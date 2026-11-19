# Data Basics for Beginners

> New to data engineering? Read this first. It explains, in plain English, every tool, file format and idea the other notes assume you already know. In the notes, the first mention of each tool links back here. For abbreviations (JDBC, CDC, ETL…), see [00-abbreviations-glossary.md](00-abbreviations-glossary.md).

## The big picture

A data engineer builds **pipelines**: automated paths that move data from where it is created to where people use it.

```
 SOURCES                 INGEST              STORE                 TRANSFORM            USE
 apps, databases,  →  stream or batch  →  data lake (S3)    →  clean, join,     →  dashboards, SQL,
 sensors, SaaS,       (Kinesis, Kafka,     warehouse          reshape            ML / AI models,
 files, APIs          DMS, AppFlow…)       (Redshift)         (Glue, Spark, SQL)  other apps
                 └──────────── orchestrated (Step Functions, Airflow) + secured + monitored ────────────┘
```

Most exam questions ask: *which service fits this step, with the least work, cost or risk?*

---

## Core ideas

### Data pipeline
A repeatable, automated series of steps that moves and changes data, for example "every night, copy yesterday's orders from the database, clean them, and load them into the warehouse."

### Batch vs streaming
- **Batch**: process a pile of data on a schedule (every hour, every night). Simple and cheap.
- **Streaming**: process each record seconds after it is created (clicks, sensor readings, payments). Needed for "real time" requirements.
- **Near real time** usually means "within a minute or so", for example Firehose buffering for 60 seconds before writing.

### ETL and ELT
- **ETL (Extract, Transform, Load)**: take data out of a source, clean/reshape it, then load it into the destination.
- **ELT (Extract, Load, Transform)**: load raw data first, then transform it *inside* the destination (usually a warehouse, with SQL).

### Data lake
A big, cheap storage area (on AWS: **S3**) holding raw and processed files of any type: CSV, JSON, Parquet, images, logs. You decide the structure when you read it (*schema-on-read*).

### Data warehouse
A database built for **analytics**: fast SQL over billions of rows, for reports and dashboards. Data is cleaned and structured before loading (*schema-on-write*). On AWS: **Redshift**.

### Lakehouse
Data lake files plus a **table format** (Iceberg, Hudi, Delta Lake) that adds warehouse features: updates, deletes, transactions, time travel. You get warehouse-like tables while the data stays in cheap S3.

### OLTP vs OLAP
- **OLTP (Online Transaction Processing)**: the app's database. Many small, fast reads/writes ("insert this order"). Examples: RDS, Aurora, DynamoDB.
- **OLAP (Online Analytical Processing)**: big analytical queries ("total sales per region for 5 years"). Examples: Redshift, Athena.
You don't run heavy analytics on the OLTP database because it slows the app down; you copy the data out instead.

### SQL
The standard language for asking questions of tabular data: `SELECT region, SUM(sales) FROM orders GROUP BY region`. Used by Athena, Redshift, RDS and many other services.

### API
An **Application Programming Interface** is a defined way for one program to ask another for data or actions, usually over the web (HTTP). For example, "call `GET /orders?date=today` and receive JSON back." Many data sources (SaaS apps, partners) are read through their APIs.

### JDBC and ODBC
Standard "plugs" (drivers) that let a program talk to almost any SQL database the same way. **JDBC (Java Database Connectivity)** is used by Java-based tools such as Spark, Glue and EMR. **ODBC (Open Database Connectivity)** is used by many other tools, such as Excel, Tableau and Power BI. A JDBC/ODBC *connection* = database address (URL) + port + username/password.

### NoSQL and key/value stores
Databases that don't use fixed tables and SQL joins. A **key/value store** (DynamoDB, Redis) looks up an item by its key extremely fast, like a giant dictionary. Great for apps, poor for ad-hoc analytics.

### Schema
The structure of data: column names and their types (`order_id: int, amount: decimal, created_at: timestamp`). **Schema evolution** = the structure changes over time (a new column appears) and the pipeline must cope.

### Metadata and data catalog
**Metadata** = data about data (where files are, their columns and types, partitions). A **data catalog** stores this so query engines can treat a folder of files as a table. On AWS: the **Glue Data Catalog**.

### Partitioning
Splitting data into folders by a column, usually date: `s3://lake/orders/year=2026/month=11/day=19/`. A query for one day then reads only that folder instead of everything. That makes it faster and cheaper.

### Row vs columnar storage
- **Row format** (CSV, JSON): each line holds one whole record. Good for writing records one by one.
- **Columnar format** (Parquet, ORC): values of each column are stored together. A query reading 3 of 50 columns only reads those 3, and similar values compress very well. This is the default choice for analytics.

### Compression and "splittable"
Compression (Snappy, GZIP, ZSTD) shrinks files to save storage and reading time. A file is **splittable** if several workers can each read a part of it in parallel. A big `.csv.gz` file is **not** splittable (one worker must read it all); Parquet is.

### Small files problem
Millions of tiny files (a few KB each) make queries slow because the engine spends more time opening files than reading data. Fix: combine them into fewer files of roughly 128 MB–1 GB (called **compaction**).

### Change Data Capture (CDC)
Instead of copying a whole database every night, read its **change log** and copy only the inserts, updates and deletes as they happen. DMS does this on AWS.

### Upsert and MERGE
**Upsert** = "update the row if it exists, insert it if it doesn't." In SQL this is the `MERGE` statement. Needed when applying CDC changes to a table.

### Shard / partition (in streams)
A stream is split into parallel lanes called **shards** (Kinesis) or **partitions** (Kafka). More lanes = more throughput. A **partition key** decides which lane each record goes to; records with the same key stay in order.

### Producer and consumer
A **producer** writes records into a stream or queue; a **consumer** reads them. Streams let many consumers read the same data independently and **replay** it later.

### Orchestration and DAG
**Orchestration** = running pipeline steps in the right order, with retries and alerts ("run job B only after job A succeeds"). A **DAG (Directed Acyclic Graph)** is a diagram of steps with arrows showing what depends on what, with no loops. Airflow pipelines are written as DAGs.

### Idempotent
Running a step twice gives the same result as running it once (no duplicate rows). Important because failed steps get retried.

### Data skew
One worker gets far more data than the others (e.g., 70% of rows have `country = 'US'`), so the whole job waits for that single slow worker. Fixes include **salting** (adding a random number to the hot key to spread it out) and **broadcast joins**.

### Distributed computing
Splitting one big job across many machines (a **cluster**) that work in parallel, then combining the results. Spark, Hadoop and Redshift all work this way.

### Star schema: fact and dimension tables
A common warehouse design. A central **fact table** holds events with numbers (each sale: amount, quantity), linked to **dimension tables** that describe them (customer, product, date). Drawn out, it looks like a star.

### Slowly Changing Dimension (SCD)
How to handle dimension data that changes, e.g., a customer moves city. **Type 1** overwrite the old value; **Type 2** keep history by adding a new row; **Type 3** keep the previous value in an extra column.

### Serverless vs provisioned
- **Provisioned**: you choose and pay for servers/capacity, whether busy or idle.
- **Serverless**: AWS handles the servers and scaling; you pay per use. The exam often prefers serverless for "least operational overhead."

### Data quality
Automated checks that data is correct before it's used: no missing IDs, values in range, no duplicates.

### Data lineage
A record of where data came from and which steps changed it ("this dashboard number came from table X, built by job Y from source Z"). It helps with debugging and audits.

### Data governance
The rules and tools for who may see what data, how sensitive data is protected, and how data is documented and audited.

### PII, masking and encryption
- **PII (Personally Identifiable Information)**: data that identifies a person: name, email, phone, ID number.
- **Masking**: hiding part of a value (`****-1234`) from people who don't need it.
- **Encryption at rest**: data is scrambled while stored on disk. **In transit**: scrambled while moving over the network (TLS/HTTPS). Only holders of the key can read it.

### Vectors and embeddings
An **embedding** is a list of numbers representing the *meaning* of text or an image, produced by an AI model. Similar meanings give nearby vectors. A **vector database/index** finds the most similar items quickly. This is used in RAG, where an AI looks up relevant documents before answering.

---

## File formats

### CSV
Plain text, one row per line, commas between values. Human-readable and universal, but slow and big for analytics, with no types.

### JSON
Text format of nested `{"key": "value"}` objects. Very common for APIs and events. **JSON Lines (JSONL)** = one JSON object per line.

### Parquet
Columnar, compressed, with a schema stored in the file. **The default analytics format** on AWS: smaller and much faster to query than CSV/JSON.

### ORC
Another columnar format (from the Hive world), similar to Parquet.

### Avro
Row-based binary format with a schema stored alongside. Common in Kafka streaming because each record is compact and the schema can evolve.

---

## Open-source tools

### Apache Hadoop
The original open-source system (around 2006) for storing and processing huge data across many cheap machines. Mostly replaced by Spark + S3, but EMR still runs it.

### HDFS
**Hadoop Distributed File System**: Hadoop's storage, spread across the disks of the cluster's machines. Data disappears with the cluster, which is why AWS designs store data in S3 instead.

### YARN
Hadoop's resource manager: decides which job gets which CPU and memory on the cluster.

### Apache Hive
Lets you query files in Hadoop/S3 with SQL as if they were tables. Its **Hive Metastore** (the list of tables, columns and partitions) is the idea the Glue Data Catalog copies.

### Apache Spark
The most popular engine for processing big data, in memory, across a cluster. You write code in Python (**PySpark**), Scala, Java or SQL. Glue and EMR run Spark. Key parts: a **driver** (plans the work) and **executors** (do the work).

### Apache Kafka
An open-source **event streaming platform**: producers write messages to **topics** (split into partitions); consumers read them; messages are kept for days so they can be replayed. Used as the central "pipe" between systems. On AWS: **Amazon MSK**. **Kafka Connect** is its add-on for moving data between Kafka and other systems without code.

### Apache Flink
A stream-processing engine for **stateful** work on live data: windowed aggregations ("count clicks per user every 5 minutes"), joins of streams, detecting patterns. On AWS: **Managed Service for Apache Flink**.

### Apache Airflow
A tool to schedule and orchestrate pipelines written as Python **DAGs**, with a web UI showing runs, failures and retries. On AWS: **MWAA**.

### Apache Iceberg
An open **table format** that turns a folder of Parquet files in S3 into a real table supporting updates, deletes, `MERGE`, schema changes and **time travel** (query the table as it was yesterday). AWS's main lakehouse table format.

### Apache Hudi
Another table format like Iceberg, focused on fast upserts and incremental processing.

### Delta Lake
A third table format like Iceberg, created by Databricks.

### Presto and Trino
Fast distributed SQL engines that query data where it sits (S3, databases) without loading it first. Athena is built on Trino/Presto.

### Apache HBase
A NoSQL database on top of Hadoop for fast random reads/writes on huge tables. Runs on EMR.

### Redis and Valkey
In-memory key/value stores: extremely fast, often used as a cache. Valkey is the open-source fork of Redis. AWS runs them as ElastiCache and MemoryDB.

### Kubernetes
Software that runs and manages **containers** (packaged apps) across many machines. On AWS: **EKS**.

### Docker and containers
A **container** packages an app with everything it needs so it runs the same everywhere. Docker is the common tool for building them.

### PostgreSQL, MySQL, Oracle and SQL Server
Popular **relational databases** (tables, SQL, transactions). PostgreSQL and MySQL are open source; Oracle and SQL Server are commercial. RDS and Aurora run them for you. **pgvector** is a PostgreSQL extension for storing and searching vectors.

### MongoDB
A popular NoSQL **document database** storing JSON-like documents. AWS's compatible service is DocumentDB.

### Jupyter
Notebooks in the browser where you mix code, results and notes, cell by cell. Common for data exploration.

### Snowflake, Splunk and Salesforce
Third-party products that appear as sources or destinations: **Snowflake** is a cloud data warehouse, **Splunk** a log search/analytics tool, **Salesforce** a customer-relationship (CRM) SaaS app.

---

## AWS services in one line each

### Storage and databases

#### Amazon S3
Object storage: unlimited files ("objects") in "buckets," very cheap and durable. The base of every AWS data lake. Has **storage classes** (Standard, Infrequent Access, Glacier) that trade retrieval speed for lower price.

#### Amazon S3 Tables
S3 buckets built specifically for Iceberg tables, with automatic maintenance (compaction, cleanup).

#### Amazon Redshift
AWS's data warehouse for fast SQL analytics at petabyte scale. **Redshift Spectrum** lets it query files in S3 directly; **Redshift Serverless** removes cluster management.

#### Amazon RDS
Managed relational databases (PostgreSQL, MySQL, Oracle, SQL Server…): AWS handles backups, patching and failover.

#### Amazon Aurora
AWS's own high-performance MySQL/PostgreSQL-compatible database, part of RDS.

#### Amazon DynamoDB
Serverless NoSQL key/value database with single-digit-millisecond speed at any scale. Designed around known access patterns, not ad-hoc queries.

#### Amazon OpenSearch Service
Search and log-analytics engine (open-source fork of Elasticsearch): full-text search, log dashboards, vector search.

#### Amazon Neptune
Graph database for highly connected data (social networks, fraud rings).

#### Amazon MemoryDB and ElastiCache
In-memory Redis/Valkey-compatible stores. **ElastiCache** is a cache; **MemoryDB** is durable enough to be a primary database.

### Moving data in (ingestion)

#### Amazon Kinesis Data Streams
AWS's streaming service, like Kafka: producers write records into shards, many consumers read them, data is kept for replay.

#### Amazon Data Firehose
The easiest way to *deliver* streaming data: it buffers records and writes them to S3, Redshift, OpenSearch, Splunk and others, with no code. Can convert JSON to Parquet on the way. (Formerly "Kinesis Data Firehose".)

#### Amazon MSK
Managed Apache Kafka. Choose it when the team already uses Kafka.

#### Managed Service for Apache Flink
Runs Flink for real-time stream processing (windowed aggregations, joins). (Formerly "Kinesis Data Analytics".)

#### AWS DMS
Database Migration Service: copies databases to AWS (one-time **full load**) and keeps copying changes (**CDC**).

#### Zero-ETL integrations
AWS-managed automatic replication from Aurora/RDS/DynamoDB into Redshift, with no pipeline to build.

#### AWS DataSync
Moves large amounts of files from on-premises file servers (NFS/SMB/HDFS) to S3/EFS online.

#### AWS Transfer Family
Managed SFTP/FTP servers that save uploads straight into S3, so partners keep their existing file-transfer tools.

#### Amazon AppFlow
No-code transfers from SaaS apps (Salesforce, Zendesk, ServiceNow…) into S3/Redshift.

#### AWS Snow Family
Physical devices AWS ships to you; you load petabytes onto them and ship them back. Used when the network is too slow.

#### AWS Data Exchange
A marketplace for buying/subscribing to third-party datasets.

### Processing and querying

#### AWS Glue
Serverless data integration: **Glue jobs** run Spark/Python ETL without servers; the **Glue Data Catalog** stores table definitions; **crawlers** scan S3 and create those table definitions automatically; **job bookmarks** remember what's already processed.

#### AWS Glue DataBrew
A visual, no-code tool for cleaning and preparing data (fix formats, remove duplicates, mask PII) with 250+ ready-made transforms.

#### AWS Glue Data Quality
Data-quality rules (written in DQDL) that run inside Glue jobs or against catalog tables.

#### Amazon EMR
Managed big-data clusters running Spark, Hadoop, Hive, Presto, HBase, Flink… More control and tuning than Glue; cheapest at very large scale (especially with **Spot** instances, discounted spare capacity that can be taken back).

#### Amazon Athena
Serverless SQL directly on files in S3. No servers or loading; you pay per data scanned. This is why Parquet and partitioning save money.

#### AWS Lambda
Runs small pieces of code in response to events (a file arrives, an API is called), up to 15 minutes, no servers. Pay per run.

#### Amazon ECS, EKS and Fargate
Ways to run containers: **ECS** is AWS's own container service, **EKS** is managed Kubernetes, and **Fargate** runs containers for either without managing servers.

#### AWS Batch
Runs large numbers of batch computing jobs (containers) and manages the compute for you.

### Orchestration and events

#### AWS Step Functions
Serverless workflows drawn as **state machines**: run Glue → Lambda → Athena in order, with retries, error handling, parallel branches and waits.

#### Amazon MWAA
Managed Workflows for Apache Airflow: AWS runs Airflow for you.

#### Amazon EventBridge
An event bus: routes events ("Glue job failed," "file uploaded") to targets (Lambda, Step Functions, SNS) based on rules. **EventBridge Scheduler** runs things on a schedule (cron).

#### Amazon SNS
Simple Notification Service: **push** a message to many subscribers at once (email, SMS, Lambda, SQS). Used for alerts and fan-out.

#### Amazon SQS
Simple Queue Service: a **queue** that holds messages until a worker pulls and processes them. Decouples fast producers from slower consumers. A **dead-letter queue (DLQ)** catches messages that keep failing.

### Analytics, BI and AI

#### Amazon QuickSight
AWS's BI (business intelligence) dashboard tool. **SPICE** is its in-memory engine for fast dashboards.

#### Amazon SageMaker Unified Studio and SageMaker Catalog
One workspace for data and AI work (SQL, notebooks, ETL, models). **SageMaker Catalog** is where people search for datasets, request access and see lineage (built on Amazon DataZone).

#### Amazon Bedrock
Access to generative-AI models (LLMs) through an API. **Knowledge Bases** handle RAG; **batch inference** runs a model over many records cheaply.

#### Amazon Comprehend
Ready-made language AI: sentiment, entities, PII detection, language detection, without writing prompts.

### Security and governance

#### AWS IAM
Identity and Access Management: users, **roles** and **policies** (JSON documents) controlling who can do what on which resource. **IAM Identity Center** gives people single sign-on.

#### AWS Lake Formation
Central permissions for a data lake: grant access to databases, tables, columns and rows (and via **LF-tags**) once, and Athena, Redshift Spectrum, EMR and Glue all enforce it.

#### AWS KMS
Key Management Service: creates and controls the encryption keys used by S3, Redshift, etc., and logs every key use.

#### AWS Secrets Manager
Stores passwords and API keys securely, and can rotate them automatically, so they never sit in code.

#### Amazon Macie
Scans S3 and finds sensitive data (PII, credit cards, credentials) automatically.

#### AWS CloudTrail
Logs every API call made in your account (who did what, when, from where). The audit trail. **CloudTrail Lake** lets you query those logs with SQL.

#### Amazon CloudWatch
Monitoring: **metrics** (numbers over time), **alarms** (alert when a metric crosses a line) and **Logs** (application/service logs, searchable with Logs Insights).

#### AWS Config
Records how your resources are configured over time and checks them against rules (e.g., "all buckets must be encrypted").

#### Amazon VPC
Virtual Private Cloud: your own private network inside AWS. **Security groups** are firewalls around resources; **subnets** divide the network; a **NAT gateway** lets private resources reach the internet; **VPC endpoints** reach AWS services without the internet.

### Building and deploying

#### AWS CloudFormation, CDK and SAM
Infrastructure as Code: describe your resources in files, and AWS creates them the same way every time. **CloudFormation** uses YAML/JSON templates; **CDK** lets you write them in Python/TypeScript; **SAM** is a shortcut for serverless apps (Lambda, Step Functions).
