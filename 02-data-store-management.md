# Domain 2: Data Store Management (26%)

> 🔰 New to data? Each tool's first mention links to a plain-English explanation in [Data Basics for Beginners](00-data-basics-for-beginners.md). Abbreviations are listed in the [glossary](00-abbreviations-glossary.md).

> **About 13 of the 50 scored questions.**
>
> This domain tests whether you can pick the right store for a cost/performance/access-pattern requirement, catalog the data so others can find and query it, manage its lifecycle (load/unload, tiering, expiry, deletion, resiliency), and model it well (schemas, schema evolution, [lineage](00-data-basics-for-beginners.md#data-lineage), partitioning, vectors). Expect lots of [Redshift](00-data-basics-for-beginners.md#amazon-redshift), [Simple Storage Service [S3]](00-data-basics-for-beginners.md#amazon-s3), [Athena](00-data-basics-for-beginners.md#amazon-athena), [DynamoDB](00-data-basics-for-beginners.md#amazon-dynamodb), [Glue](00-data-basics-for-beginners.md#aws-glue) Data Catalog, and, new in v1.1, **[Apache Iceberg](00-data-basics-for-beginners.md#apache-iceberg), vector indexes, and [SageMaker Catalog](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)**.

## Table of contents

- [Exam tasks and skills](#exam-tasks-and-skills)
- [Task 2.1: Choose a data store](#task-21-choose-a-data-store)
- [Task 2.2: Understand data cataloging systems](#task-22-understand-data-cataloging-systems)
- [Task 2.3: Manage the lifecycle of data](#task-23-manage-the-lifecycle-of-data)
- [Task 2.4: Design data models and schema evolution](#task-24-design-data-models-and-schema-evolution)
- [Gotchas and exam traps](#gotchas-and-exam-traps)
- [Quick-recall summary](#quick-recall-summary)

## Exam tasks and skills

> Summarized from the official AWS Certified Data Engineer – Associate (DEA-C01) exam guide (v1.1). Exact wording: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain2.html

### Task 2.1: Choose a data store
- **2.1.1** Pick storage services that meet cost and performance needs (Redshift, [Elastic MapReduce [EMR]](00-data-basics-for-beginners.md#amazon-emr), [Lake Formation](00-data-basics-for-beginners.md#aws-lake-formation), [Relational Database Service [RDS]](00-data-basics-for-beginners.md#amazon-rds), DynamoDB, [Kinesis Data Streams [KDS]](00-data-basics-for-beginners.md#amazon-kinesis-data-streams), [Managed Streaming for Apache Kafka [MSK]](00-data-basics-for-beginners.md#amazon-msk)).
- **2.1.2** Configure storage for specific access patterns.
- **2.1.3** Match storage to use cases (e.g., **Hierarchical Navigable Small World [HNSW] indexes on [Aurora](00-data-basics-for-beginners.md#amazon-aurora) [PostgreSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server)**, **[MemoryDB](00-data-basics-for-beginners.md#amazon-memorydb-and-elasticache)** for fast key/value).
- **2.1.4** Integrate migration tools (e.g., [Transfer Family](00-data-basics-for-beginners.md#aws-transfer-family)).
- **2.1.5** Use migration/remote-access methods (Redshift federated queries, materialized views, Spectrum).
- **2.1.6** Manage locks (Redshift, RDS).
- **2.1.7** 🆕 Manage open table formats (Apache Iceberg).
- **2.1.8** 🆕 Describe vector index types (HNSW, Inverted File index [IVF]).

### Task 2.2: Understand data cataloging systems
- **2.2.1** Use catalogs to consume data from its source.
- **2.2.2** Build and reference a technical catalog (Glue Data Catalog, [Hive](00-data-basics-for-beginners.md#apache-hive) metastore).
- **2.2.3** Discover schemas with Glue crawlers.
- **2.2.4** Keep partitions in sync with the catalog.
- **2.2.5** Create source/target connections for cataloging.
- **2.2.6** 🆕 Create and manage business data catalogs (SageMaker Catalog).

### Task 2.3: Manage the lifecycle of data
- **2.3.1** Load and unload between S3 and Redshift.
- **2.3.2** Use S3 Lifecycle to change storage tiers.
- **2.3.3** Use S3 Lifecycle to expire data by age.
- **2.3.4** Manage S3 versioning and DynamoDB Time To Live (TTL).
- **2.3.5** Delete data for business and legal requirements.
- **2.3.6** Protect data with appropriate resiliency and availability.

### Task 2.4: Design data models and schema evolution
- **2.4.1** Design schemas for Redshift, DynamoDB, Lake Formation.
- **2.4.2** Handle changes in data characteristics.
- **2.4.3** Convert schemas (Amazon Web Services [AWS] Schema Conversion Tool [SCT], [Database Migration Service [DMS]](00-data-basics-for-beginners.md#aws-dms) Schema Conversion).
- **2.4.4** Establish lineage (SageMaker Machine Learning [ML] Lineage Tracking, SageMaker Catalog).
- **2.4.5** Apply indexing, partitioning, compression, and other optimizations.
- **2.4.6** 🆕 Describe vectorization (e.g., [Bedrock](00-data-basics-for-beginners.md#amazon-bedrock) Knowledge Bases).

---

## Task 2.1: Choose a data store

### Core concepts

Every store question is answered by four questions:
1. **Access pattern:** key lookups? scans/aggregations? full-text? similarity search? graph traversal?
2. **Latency:** microseconds, milliseconds, seconds, minutes?
3. **Structure:** relational, semi-structured, unstructured, vectors?
4. **Cost model:** pay per query, per hour, per GB stored, per request?

### Data store decision table (skills 2.1.1, 2.1.2, 2.1.3)

| Requirement | Store | Why |
|---|---|---|
| Cheap, durable storage for any format; [data lake](00-data-basics-for-beginners.md#data-lake) | **Amazon S3** | 11 nines durability, storage classes, decoupled from compute |
| Lake tables with Atomicity, Consistency, Isolation, Durability (ACID), updates/deletes, time travel | **Apache Iceberg** on S3 / **[Amazon S3 Tables](00-data-basics-for-beginners.md#amazon-s3-tables)** | Open table format; S3 Tables adds automatic maintenance |
| PB-scale [Structured Query Language [SQL]](00-data-basics-for-beginners.md#sql) analytics, Business Intelligence (BI) dashboards, complex joins | **Amazon Redshift** | Columnar Massively Parallel Processing (MPP) warehouse |
| Ad-hoc SQL on S3, infrequent queries, no infrastructure | **Amazon Athena** | Serverless, pay per TB scanned |
| Single-digit ms key/value or document at any scale | **Amazon DynamoDB** | Serverless NoSQL, predictable latency |
| **Microsecond** reads in front of DynamoDB | **DynamoDB Accelerator (DAX)** | Write-through in-memory cache for DynamoDB |
| **Durable** in-memory key/value as a primary database | **Amazon MemoryDB** | [Redis](00-data-basics-for-beginners.md#redis-and-valkey)/Valkey [Application Programming Interface [API]](00-data-basics-for-beginners.md#api) + Multi-AZ transaction log (data survives node failure) |
| In-memory cache (data can be rebuilt) | **Amazon ElastiCache** | Lower cost cache, not a durable system of record |
| Relational Online Transaction Processing (OLTP) with transactions | **Amazon RDS / Aurora** | ACID, joins, constraints |
| Vector similarity search next to relational data | **Aurora PostgreSQL + pgvector** (HNSW / IVFFlat) | Keep [embeddings](00-data-basics-for-beginners.md#vectors-and-embeddings) with business data, use SQL |
| Full-text search, log analytics, vector search at scale | **[Amazon OpenSearch Service](00-data-basics-for-beginners.md#amazon-opensearch-service) / Serverless** | Inverted index + k-Nearest Neighbors (k-NN) engine |
| Highly connected data (fraud rings, recommendations) | **[Amazon Neptune](00-data-basics-for-beginners.md#amazon-neptune)** | Graph database [DB] (Gremlin, openCypher, SPARQL) |
| Big data processing with [HDFS](00-data-basics-for-beginners.md#hdfs)/HBase | **Amazon EMR** | [Hadoop](00-data-basics-for-beginners.md#apache-hadoop) ecosystem storage and compute |
| Data retained as a stream (hours to a year) | **Kinesis Data Streams / MSK** | Streams are storage too: ordered, replayable |
| Governed data lake permissions | **AWS Lake Formation** (over S3 + Glue Catalog) | Fine-grained access, not a storage engine itself |

### Amazon S3 essentials

**Storage classes:**

| Class | Access | Min duration | Use |
|---|---|---|---|
| **Standard** | ms | — | Hot data |
| **Intelligent-Tiering** | ms (archive tiers optional) | — | **Unknown or changing access patterns**; auto-moves objects, small monitoring fee |
| **Standard-Infrequent Access (Standard-IA)** | ms | 30 days | Infrequent access, multi-AZ |
| **One Zone-Infrequent Access (One Zone-IA)** | ms | 30 days | Re-creatable infrequent data, one Availability Zone (AZ) |
| **Glacier Instant Retrieval** | ms | 90 days | Archive accessed about once a quarter |
| **Glacier Flexible Retrieval** | minutes–hours (expedited 1–5 min, standard 3–5 h, bulk 5–12 h) | 90 days | Backups, archives |
| **Glacier Deep Archive** | 12–48 h | 180 days | Compliance archives, cheapest |
| **Express One Zone** | single-digit ms | — | Very high request rates, latency-sensitive analytics/ML in one AZ |

**Performance:** 3,500 write and 5,500 read requests per second **per prefix**. Spread hot data across prefixes, use multipart upload for large objects, and byte-range fetches for parallel reads.

### Amazon Redshift essentials

**Architecture:** leader node (parses, plans, aggregates) + compute nodes, each split into **slices** that work in parallel. **RA3** nodes separate compute from **Redshift Managed Storage** (S3-backed). **Redshift Serverless** bills by Redshift Processing Unit hours (RPU-hours) with no clusters to manage. Use it for unpredictable or intermittent workloads.

**Distribution styles:**

| Style | How rows are placed | Use when |
|---|---|---|
| **AUTO** | Redshift chooses and adjusts | Default, unsure |
| **KEY** | Same key value → same slice | Large fact tables joined on that column (e.g., `customer_id`). **Co-located joins** avoid data movement. Watch for **skew** if the key has few distinct values. |
| **ALL** | Full copy on every node | Small, rarely updated dimension tables |
| **EVEN** | Round-robin | No dominant join; tables not joined |

**Sort keys:**
- **Compound** (default): ordered by column 1, then 2… Best when queries filter on the **leading column** (usually a date/timestamp) and for range filters, merge joins, `GROUP BY`/`ORDER BY`.
- **Interleaved**: equal weight to each column; helps when different queries filter on different columns. Expensive `VACUUM REINDEX`, so rarely the best answer.
- Sort keys enable **zone maps** (min/max per block), so Redshift skips blocks that can't match.

**Compression (column encoding):** `AZ64` (numbers/dates), `ZSTD` (strings), `LZO`; `ENCODE AUTO` lets Redshift choose. Don't compress the first sort key column heavily (it hurts range-restricted scans).

**Scaling and workload features:**

| Feature | What it solves |
|---|---|
| **Concurrency scaling** | Bursts of many concurrent queries → transient extra clusters |
| **Elastic resize** | Change node count in minutes |
| **Workload Management [WLM] (automatic)** | Query queues, priorities, **Short Query Acceleration** |
| **Materialized views** | Precompute expensive joins/aggregations; incremental and auto refresh |
| **Data sharing** | Live read (and write) access across clusters/workgroups/accounts/Regions **with no copies** |
| **Redshift Spectrum** | Query S3 (Glue Catalog external tables) from Redshift |
| **Federated query** | Query live RDS/Aurora PostgreSQL & MySQL |
| **[Zero-ETL](00-data-basics-for-beginners.md#zero-etl-integrations)** | Near-real-time replication from Aurora/RDS/DynamoDB |
| **SUPER type + PartiQL** | Store and query semi-structured [JavaScript Object Notation [JSON]](00-data-basics-for-beginners.md#json) |

### Amazon DynamoDB essentials

- **Primary key:** partition key only, or partition key + sort key. Choose a **high-cardinality** partition key with evenly spread traffic.
- **Indexes:** **Global Secondary Index [GSI]** (different partition/sort key, add anytime, eventually consistent, own capacity) vs **Local Secondary Index [LSI]** (same partition key, different sort key, **only at table creation**, supports strongly consistent reads, 10 GB per partition key value limit).
- **Capacity:** **on-demand** (spiky/unknown traffic) vs **provisioned + auto scaling** (steady traffic, cheaper). Read Capacity Unit (RCU) = 1 strongly consistent read/s of up to 4 KB (or 2 eventually consistent); Write Capacity Unit (WCU) = 1 write/s of up to 1 KB.
- **Item limit:** 400 KB. Store larger payloads in S3 and keep a pointer.
- **Streams, TTL, Point-In-Time Recovery (PITR), global tables, export to S3, zero-ETL** are covered under lifecycle and ingestion.

### Migration tools (skill 2.1.4)

| Tool | Moves |
|---|---|
| **AWS Transfer Family** | Files via **SFTP/File Transfer Protocol Secure (FTPS)/File Transfer Protocol (FTP)/Applicability Statement 2 (AS2)** into S3/Elastic File System (EFS). Partners keep using their existing SSH File Transfer Protocol (SFTP) clients; managed workflows can post-process files. |
| **[AWS DataSync](00-data-basics-for-beginners.md#aws-datasync)** | Large online file transfers (Network File System [NFS]/Server Message Block [SMB]/HDFS/object) with scheduling and verification |
| **[AWS Snow Family](00-data-basics-for-beginners.md#aws-snow-family)** | Offline bulk transfer |
| **AWS DMS** | Databases (homogeneous and heterogeneous), full load + Change Data Capture (CDC) |
| **S3 Batch Operations** | Bulk actions on billions of existing objects (copy, tag, restore, invoke [Lambda](00-data-basics-for-beginners.md#aws-lambda)) |

### Remote access instead of copying (skill 2.1.5)

| Method | What it does | When |
|---|---|---|
| **Redshift Spectrum** | External tables over S3 via Glue Catalog; Spectrum layer scans S3 in parallel | Join warehouse data with **cold/large lake data** without loading it |
| **Redshift federated query** | Pushes queries down to **live** Aurora/RDS PostgreSQL or MySQL | Join operational data with warehouse data without Extract, Transform, Load (ETL) |
| **Redshift materialized views** | Store the result of a query (can include Spectrum/federated sources) | Speed up repeated expensive queries; refresh on schedule or automatically |
| **Athena federated query** | Lambda connectors to DynamoDB, RDS, [CloudWatch](00-data-basics-for-beginners.md#amazon-cloudwatch), others | SQL across many sources from Athena |

### Managing locks (skill 2.1.6)

**Redshift lock types:**

| Lock | Taken by | Blocks |
|---|---|---|
| **AccessShareLock** | `SELECT` | Only AccessExclusiveLock |
| **ShareRowExclusiveLock** | `INSERT`, `UPDATE`, `DELETE`, `COPY` | Other writes on the same table (and exclusive locks) |
| **AccessExclusiveLock** | Data Definition Language (DDL): `ALTER TABLE`, `DROP`, `TRUNCATE`, some `VACUUM` | **Everything**, including reads |

- Find blockers: `STV_LOCKS`, `SVV_TRANSACTIONS`, `STV_RECENTS`; end the session with `PG_TERMINATE_BACKEND(pid)`.
- Use the explicit `LOCK table_name;` command to serialize concurrent writers (avoids serializable isolation errors).
- Long-running open transactions hold locks. Commit promptly, and schedule DDL outside busy windows.

**RDS / Aurora:**
- Row-level locking in InnoDB/PostgreSQL; `SELECT … FOR UPDATE` locks rows for a transaction.
- **Deadlocks**: the engine kills one transaction. Fix with consistent lock ordering and shorter transactions.
- Inspect with `pg_locks` / `pg_stat_activity` (PostgreSQL) or `SHOW ENGINE INNODB STATUS` / `performance_schema` (MySQL). **Performance Insights** shows lock waits visually.

### 🆕 Open table formats: Apache Iceberg (skill 2.1.7)

**Why table formats exist:** plain [Parquet](00-data-basics-for-beginners.md#parquet) files in S3 have no transactions. Two writers can corrupt a table, readers can see half-written data, and updating/deleting a row means rewriting partitions. Open table formats add a **metadata layer** over files to give database-like behavior.

**How Iceberg works:**

```
Catalog (Glue Data Catalog / S3 Tables) ──► current metadata.json
                                               └─► snapshot → manifest list
                                                              └─► manifest files
                                                                      └─► data files (Parquet) + delete files
```

Each commit creates a **new snapshot** atomically, so readers always see a consistent version.

**Key features (memorize):**

| Feature | Meaning |
|---|---|
| **ACID transactions** | Concurrent readers/writers safe; atomic commits |
| **Row-level `UPDATE` / `DELETE` / `MERGE INTO`** | [Upserts](00-data-basics-for-beginners.md#upsert-and-merge) and CDC merges, General Data Protection Regulation (GDPR) deletes |
| **Schema evolution** | Add, drop, rename, reorder columns **without rewriting data** (column IDs, not names) |
| **Hidden partitioning** | Partition by transforms (e.g., `day(ts)`), so queries don't need to reference partition columns |
| **Partition evolution** | Change partitioning scheme without rewriting old data |
| **Time travel** | Query a past snapshot/time; roll back bad writes |
| **Copy-on-write vs merge-on-read** | CoW rewrites files on update (faster reads); MoR writes delete files (faster writes, compaction needed) |

**Maintenance (exam favorite):**
- **Compaction**: rewrite many [small files](00-data-basics-for-beginners.md#small-files-problem) into fewer large files. In Athena: `OPTIMIZE table REWRITE DATA USING BIN_PACK`.
- **Expire snapshots / remove orphan files**: reclaim storage from old versions. In Athena: `VACUUM table`.
- **Glue Data Catalog table optimizers** can run compaction, snapshot retention, and orphan file deletion **automatically** for Iceberg tables.

**Amazon S3 Tables:** **table buckets** that store Iceberg tables as a managed resource, with **automatic compaction, snapshot management, and unreferenced file removal**, plus higher performance for tabular data. Query from Athena, Redshift, EMR, Glue, and [Firehose](00-data-basics-for-beginners.md#amazon-data-firehose) can deliver into them. → "Managed Iceberg with least maintenance" = **S3 Tables**.

**Other formats you may see as distractors:** **[Apache Hudi](00-data-basics-for-beginners.md#apache-hudi)** (upserts/incremental pulls, CoW/MoR, strong on EMR) and **[Delta Lake](00-data-basics-for-beginners.md#delta-lake)** (Databricks-origin). AWS analytics services support all three, but Iceberg is the one the exam guide names.

**Engines that work with Iceberg on AWS:** Athena (read/write, Data Manipulation Language [DML], time travel), Glue ETL, EMR ([Spark](00-data-basics-for-beginners.md#apache-spark), [Trino](00-data-basics-for-beginners.md#presto-and-trino), [Flink](00-data-basics-for-beginners.md#apache-flink)), Redshift (read), Firehose (write), [Managed Service for Apache Flink](00-data-basics-for-beginners.md#managed-service-for-apache-flink).

### 🆕 Vector index types (skills 2.1.3, 2.1.8)

**Background:** An **embedding** is a list of numbers (a vector, e.g., 1,024 dimensions) representing meaning. Similar items have nearby vectors. **Similarity search** finds the nearest vectors using a distance metric: **cosine similarity**, **Euclidean (L2)**, or **dot product**. Exact search compares against every vector (slow at scale), so stores use **approximate nearest neighbor (ANN)** indexes.

| | **HNSW** (Hierarchical Navigable Small World) | **IVF** (Inverted File index) |
|---|---|---|
| Structure | Multi-layer **graph**; upper layers are sparse "highways," the bottom layer has all vectors | Vectors **clustered** around centroids (k-means); each cluster is a list |
| Search | Greedy walk from the top layer down to the nearest neighbors | Find the nearest centroids, search only those clusters (`nprobe`/`lists`) |
| Recall / speed | **High recall, very fast queries** | Good; recall depends on how many clusters are probed |
| Memory | **High** (graph edges) | **Lower** |
| Build | Slower to build, no training step, handles inserts incrementally | Faster build but needs a **training** step on representative data; heavy data drift can require rebuilding |
| Tuning knobs | `m` (connections per node), `ef_construction`, `ef_search` | number of lists/clusters, number of probes |
| Choose when | Low latency + high accuracy, memory is OK | Very large datasets, memory/cost constrained |

**Where vectors live on AWS:**

| Store | Notes |
|---|---|
| **Aurora PostgreSQL / RDS PostgreSQL + pgvector** | `CREATE INDEX … USING hnsw` or `ivfflat`; vectors next to relational data; SQL filtering |
| **OpenSearch Service / Serverless** | k-NN plugin (HNSW, IVF via Facebook AI Similarity Search [FAISS]/Lucene engines); hybrid keyword + vector search; default store for Bedrock Knowledge Bases quick create |
| **MemoryDB** | In-memory vector search with very low latency (and durable) |
| **Neptune Analytics, DocumentDB** | Vector search alongside graph/document data |

---

## Task 2.2: Understand data cataloging systems

### Core concepts

A **data catalog** stores **metadata**: table names, columns and types, partition locations, file formats, owners, descriptions. Engines read the catalog to know *how* to read files. Without it, a bucket of Parquet files is just a bucket of files.

- **Technical catalog** → schemas, partitions, locations (for engines). Example: **AWS Glue Data Catalog**, **Hive metastore**.
- **Business catalog** → business meaning, ownership, glossary terms, data products, access requests (for people). Example: **Amazon SageMaker Catalog**.

### Technical catalogs (skills 2.2.1, 2.2.2)

**AWS Glue Data Catalog:**
- One per account per Region. Organized as **databases → tables → partitions**.
- **Hive-metastore compatible**, used by **Athena, Redshift Spectrum, EMR, Glue ETL, Lake Formation, [QuickSight](00-data-basics-for-beginners.md#amazon-quicksight) (via Athena)**.
- Supports Iceberg, Hudi, and Delta table metadata; **partition indexes** speed up queries on tables with many partitions; **column statistics** help query planning.
- EMR can use the Glue Data Catalog **as its Hive metastore** (recommended for shared, persistent metadata) instead of a cluster-local or RDS-hosted Hive metastore.
- Can be encrypted (catalog encryption settings with [Key Management Service [KMS]](00-data-basics-for-beginners.md#aws-kms)) and governed by Lake Formation.

**Consuming data through the catalog:** once a table is cataloged, Athena runs `SELECT * FROM db.table`, Redshift creates `CREATE EXTERNAL SCHEMA … FROM DATA CATALOG`, and Glue jobs use `from_catalog(database, table_name)`. You get one definition shared by many engines.

### Glue crawlers (skill 2.2.3)

A **crawler** connects to a data store, uses **classifiers** to infer schema, and creates/updates tables and partitions.

| Setting | Explanation |
|---|---|
| **Data sources** | S3, [Java Database Connectivity [JDBC]](00-data-basics-for-beginners.md#jdbc-and-odbc) (RDS, Redshift, on-prem), DynamoDB, [MongoDB](00-data-basics-for-beginners.md#mongodb)/DocumentDB, Delta/Iceberg/Hudi tables |
| **Classifiers** | Built-in ([Comma-Separated Values [CSV]](00-data-basics-for-beginners.md#csv), JSON, Parquet, [Avro](00-data-basics-for-beginners.md#avro), [Optimized Row Columnar [ORC]](00-data-basics-for-beginners.md#orc), Extensible Markup Language [XML]…) + **custom** (Grok, XML, JSON path, CSV) for unusual formats; first classifier that matches with certainty wins |
| **Include/exclude patterns** | Skip folders/files (e.g., `_temporary`, `*.metadata`) |
| **Schema change policy** | Update table definition / add new columns only / ignore changes and log; deleted objects → delete, mark deprecated, or ignore |
| **Recrawl policy** | Crawl all folders, **crawl new folders only** (incremental), or **S3 event mode** (crawl only changed objects from [Simple Queue Service [SQS]](00-data-basics-for-beginners.md#amazon-sqs) events) |
| **Grouping** | "Create a single schema for each S3 path" avoids one table per folder when schemas are compatible |
| **Schedule** | On demand, cron, or as part of a Glue workflow |

**When not to use a crawler:** the schema is known and stable (define the table with DDL / [CloudFormation](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam) instead), or partitions follow a predictable pattern (**partition projection**).

### Synchronizing partitions (skill 2.2.4)

New partition folders in S3 (e.g., `year=2026/month=11/day=19/`) are invisible to Athena until the catalog knows about them.

| Method | Notes |
|---|---|
| **Re-run crawler** (incremental) | Easy, but scheduled and costs crawler time |
| **`MSCK REPAIR TABLE`** | Scans S3 and adds Hive-style partitions; slow on huge tables |
| **`ALTER TABLE ADD PARTITION`** | Explicit and fast; works for non-Hive layouts too |
| **Glue job writes with catalog update** | `enableUpdateCatalog=True` + `partitionKeys` adds partitions as the job writes |
| **Athena partition projection** | Partitions **computed from table properties** (ranges, dates, enums); no catalog lookups. Best for **highly partitioned tables** and predictable paths. |
| **Iceberg tables** | Partitions tracked in table metadata automatically |

### Connections for cataloging (skill 2.2.5)

A **Glue connection** holds what a crawler or job needs to reach a source/target: type (**JDBC**, MongoDB, [Kafka](00-data-basics-for-beginners.md#apache-kafka), **Network**, marketplace/custom connectors), endpoint Uniform Resource Locator (URL), credentials (preferably **[Secrets Manager](00-data-basics-for-beginners.md#aws-secrets-manager)**), and **[Virtual Private Cloud [VPC]](00-data-basics-for-beginners.md#amazon-vpc), subnet, security group**. Remember the self-referencing security group rule and a route to the source (Network Address Translation [NAT] gateway for the internet, **S3 gateway endpoint** for S3 from a private subnet).

### 🆕 Business data catalogs: Amazon SageMaker Catalog (skill 2.2.6)

**SageMaker Catalog** (built on Amazon DataZone, part of **SageMaker Unified Studio**) is where people **find, understand, request, and govern** data and Artificial Intelligence (AI) assets.

| Concept | Meaning |
|---|---|
| **Assets** | Tables (Glue/Redshift), S3 data, models, dashboards registered in the catalog |
| **Business metadata** | Descriptions, **business glossary** terms, **metadata forms** (custom required fields like owner, sensitivity) |
| **AI-generated descriptions** | Generative AI suggests business names/descriptions for assets and columns |
| **Publishing** | Producers publish assets (or bundles as **data products**) so others can discover them |
| **Subscription workflow** | Consumers **request access** for their project → owner **approves** → access is **granted automatically** (e.g., Lake Formation or Redshift grants) |
| **Data quality & lineage** | Quality scores and **lineage graphs** shown on assets |

> Technical vs business catalog in one line: **Glue Data Catalog tells Athena how to read the table; SageMaker Catalog tells an analyst what the table means, who owns it, and how to get access.**

---

## Task 2.3: Manage the lifecycle of data

### Load and unload between S3 and Redshift (skill 2.3.1)

**COPY (load):**
- Loads in **parallel**, with each slice reading files. **Split data into multiple files** (ideally a multiple of the number of slices), similar sizes (1 MB–1 GB compressed), compressed (GZIP, Zstandard [ZSTD], BZIP2, LZOP) or columnar (Parquet/ORC).
- Use a **manifest file** to load an exact list of files (avoids loading partial or wrong files).
- Authorize with an **[Identity and Access Management [IAM]](00-data-basics-for-beginners.md#aws-iam) role** attached to the cluster (`IAM_ROLE 'arn:…'`), not access keys.
- Useful options: `FORMAT AS PARQUET|JSON|CSV`, `COMPUPDATE`, `STATUPDATE`, `MAXERROR`, `REGION`, `TIMEFORMAT`.
- **Errors** → `STL_LOAD_ERRORS` / `SYS_LOAD_ERROR_DETAIL`.
- **Upserts:** COPY into a **staging table**, then `MERGE` (or delete + insert) into the target in one transaction.
- **Auto-copy**: `COPY JOB` can watch an S3 prefix and load new files automatically.

**UNLOAD (export):**
- `UNLOAD ('select …') TO 's3://…' IAM_ROLE '…' FORMAT AS PARQUET PARTITION BY (col)`. Writes in parallel (multiple files) by default; `PARALLEL OFF` for a single file (slower).
- Can encrypt with KMS (`KMS_KEY_ID`) and set `MAXFILESIZE`.
- Typical use: archive old warehouse data to S3 and query it with Spectrum (hot data in Redshift, cold data in S3).

### S3 Lifecycle: tiering and expiration (skills 2.3.2, 2.3.3)

A **lifecycle configuration** is a set of rules scoped by **prefix and/or object tags**:
- **Transition actions:** move objects to cheaper classes after N days (e.g., Standard → Standard-IA at 30 days → Glacier Flexible Retrieval at 90 days → Deep Archive at 365 days).
- **Expiration actions:** delete objects after N days.
- **Noncurrent version actions:** transition/expire **old versions** in versioned buckets (e.g., keep 3 noncurrent versions for 30 days).
- **Abort incomplete multipart uploads** after N days (hidden storage cost).
- **Expired object delete markers** cleanup.

Rules to remember:
- Objects must stay **30 days** in Standard before transitioning to Standard-IA/One Zone-IA via lifecycle.
- Minimum storage duration charges apply (Infrequent Access [IA] 30, Glacier Instant Retrieval [Glacier IR]/Flexible 90, Deep Archive 180 days). Deleting early still bills the minimum.
- Lifecycle runs asynchronously (not at an exact minute).
- **Unknown access pattern** → use Intelligent-Tiering instead of guessing transition days.

### S3 versioning and DynamoDB TTL (skill 2.3.4)

**S3 versioning:**
- Keeps every version of an object; protects against accidental overwrite/delete.
- A delete without a version ID adds a **delete marker** (the object "disappears" but old versions remain). Deleting the marker restores it.
- Once enabled, it can only be **suspended**, never fully disabled.
- Required for **replication** and **Object Lock**. Combine with **Multi-Factor Authentication (MFA) Delete** for extra protection.
- Control cost with noncurrent-version lifecycle rules.

**DynamoDB TTL:**
- You choose an attribute holding an **epoch timestamp in seconds**. After that time, DynamoDB deletes the item **automatically at no cost** (no WCU consumed).
- Deletion is **not immediate**. It typically happens within a few days, so filter expired items in queries if exactness matters.
- TTL deletes appear in **DynamoDB Streams** (marked as system deletes), so you can archive expired items to S3 via Lambda/Firehose.

### Deleting data for business and legal requirements (skill 2.3.5)

| Requirement | Approach |
|---|---|
| Delete after retention period | S3 Lifecycle expiration, DynamoDB TTL, Redshift scheduled `DELETE`/`TRUNCATE`, CloudWatch Logs retention settings |
| **Right to be forgotten** (GDPR) on a data lake | Use **Iceberg** (`DELETE FROM … WHERE user_id = …` in Athena/Glue) instead of rewriting Parquet partitions by hand; then expire snapshots so old files are removed |
| Find where personal data lives first | **[Amazon Macie](00-data-basics-for-beginners.md#amazon-macie)** (S3), catalog tags, lineage |
| **Must not be deleted** for N years (Write Once, Read Many [WORM]) | **S3 Object Lock**: **compliance mode** (no one, including root, can delete or shorten retention) vs **governance mode** (privileged users with special permission can override); **legal hold** (indefinite until removed). Glacier **Vault Lock** for vaults. |
| Prove deletion | [CloudTrail](00-data-basics-for-beginners.md#aws-cloudtrail) data events, S3 server access logs |

> ⚠️ With versioning on, "deleting" an object only adds a delete marker. Truly removing data requires deleting **all versions** (or a lifecycle rule for noncurrent versions).

### Resiliency and availability (skill 2.3.6)

| Service | Protection options |
|---|---|
| **S3** | Multi-AZ by default (except One Zone classes); **Cross-Region / Same-Region Replication** (versioning required; **Replication Time Control** = 99.99% of objects in 15 min); AWS Backup for S3 |
| **DynamoDB** | **PITR** (restore to any second in the last 35 days), on-demand backups, **global tables** (multi-Region active-active) |
| **Redshift** | **Automated snapshots** (default 1-day retention, up to 35 days), manual snapshots (kept until deleted), **cross-Region snapshot copy**, **Multi-AZ** deployments (RA3), relocation to another AZ |
| **RDS / Aurora** | **Multi-AZ** (failover), read replicas (scale reads, cross-Region Disaster Recovery [DR]), automated backups + snapshots, **Aurora Global Database** (cross-Region, <1 s lag) |
| **KDS / MSK** | Data replicated across 3 Availability Zones [AZs] (KDS); MSK multi-AZ brokers, MSK Replicator for cross-cluster/Region |
| **EMR** | Store data in **S3, not Hadoop Distributed File System (HDFS)**, so cluster loss doesn't lose data; multi-primary nodes for High Availability (HA) |
| **Centralized** | **AWS Backup** policies across services and accounts; backup vault lock for immutability |

Know the difference: **high availability** (survive an AZ failure with no or brief interruption: Multi-AZ) vs **disaster recovery** (recover in another Region: replication, snapshot copy, global tables), measured by **Recovery Point Objective [RPO]** (how much data you can lose) and **Recovery Time Objective [RTO]** (how long recovery takes).

---

## Task 2.4: Design data models and schema evolution

### Designing schemas (skill 2.4.1)

**Redshift (dimensional modeling):**
- **Star schema**: central **fact table** (events/measures: sales, clicks) + **dimension tables** (who/what/where/when: customer, product, date). **[Snowflake](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce) schema** normalizes dimensions further (more joins).
- Fact: `DISTKEY` on the most common large join column, `SORTKEY` on the date column. Small dimensions: `DISTSTYLE ALL`.
- Moderate **denormalization** is fine in a columnar warehouse. It reduces joins.
- Primary/foreign keys are **informational only** in Redshift (not enforced) but help the optimizer. You must deduplicate yourself.
- **Slowly changing dimensions (SCD):** **Type 1** overwrite (no history), **Type 2** add a new row with effective/expiry dates and a current flag (full history), **Type 3** add a "previous value" column (limited history).

**DynamoDB (access-pattern-first modeling):**
- List **access patterns first**, then design keys. There are no joins, so you design for queries, not normalization.
- **Composite sort keys** (e.g., `ORDER#2026-11-19#123`) enable `begins_with` and range queries.
- **Single-table design**: several entity types in one table with generic `PK`/`SK` (e.g., `CUSTOMER#1` / `ORDER#…`) for efficient one-query fetches of related items.
- **Global Secondary Indexes (GSIs)** for alternate access patterns; **sparse indexes** (only items with the attribute appear) for efficient filtering.
- Avoid hot keys: add a random/calculated suffix (**write sharding**) when one key gets too much traffic.

**Lake Formation / data lake:**
- Organize S3 into zones: **raw (bronze)** → **cleaned (silver)** → **curated (gold)**, each as Glue databases.
- Partition by query filters (usually date), use Parquet/Iceberg, consistent naming.
- Design for permissions: separate sensitive columns or use **Lake Formation tags (LF-tags)** and **data filters** (Domain 4).

### Handling changing data characteristics: schema evolution (skill 2.4.2)

| Situation | Tool / approach |
|---|---|
| New columns appear in source files | Crawler schema change policy (add new columns); Parquet schema merging; **Iceberg** add column (no rewrite) |
| Column renamed or type widened | **Iceberg** handles rename/reorder/type promotion safely; plain Hive tables don't |
| Streaming producers change message format | **AWS Glue Schema Registry** (Avro, JSON Schema, Protobuf) with **compatibility modes**: **BACKWARD** (default: new schema can read old data), **FORWARD**, **FULL**, **NONE**, plus transitive variants. Rejects incompatible schema versions before they break consumers. |
| Mixed types in a column (string/int) | Glue **`ResolveChoice`** (cast, make_struct, project) |
| Changing volume/velocity | Move from batch to streaming, resize/scale stores, repartition |
| Redshift table change | `ALTER TABLE ADD COLUMN`; deep copy for structure changes; **late-binding views** so views don't break when underlying tables change |

### Schema conversion (skill 2.4.3)

- **Homogeneous** migrations (Oracle → RDS Oracle, MySQL → Aurora MySQL): no conversion needed. Use native tools or DMS.
- **Heterogeneous** migrations (Oracle/SQL Server → Aurora PostgreSQL or Redshift): convert schema objects first.
  - **DMS Schema Conversion**: managed, inside the DMS console; generates assessment reports and converts schemas and code objects.
  - **AWS SCT**: downloadable desktop tool that does the same (still named in the skill, though removed from the in-scope service list in v1.1).
  - Then **DMS** moves the data (full load + CDC).
- Items that can't convert automatically are flagged in an **assessment report** for manual work.

### Data lineage (skill 2.4.4)

**Lineage** = where data came from, which transformations touched it, and where it goes. It's used for impact analysis ("what breaks if I change this column?"), debugging, trust, and compliance.

| Tool | Scope |
|---|---|
| **Amazon SageMaker Catalog lineage** | Captures lineage (OpenLineage-compatible) from sources like Glue, Redshift, and EMR, and visualizes it on catalog assets |
| **SageMaker ML Lineage Tracking** | ML workflow lineage: datasets → processing jobs → training jobs → models → endpoints |
| **Amazon Neptune** | Build custom lineage graphs (graph data structure) |
| **Glue job metadata / CloudTrail** | Raw evidence of what ran and when |

### Indexing, partitioning, compression, optimization (skill 2.4.5)

**Partitioning (S3/Athena/Glue):**
- Partition by columns used in `WHERE` filters, usually **date/time** (`year=/month=/day=`) and maybe a low-cardinality dimension (region).
- **Avoid over-partitioning**: too many tiny partitions → many small files and slow planning. Aim for partitions of hundreds of MB+.
- **Never** partition on high-cardinality columns like `user_id`. Use **bucketing** (`bucketed_by`, hash into N files) for those instead.
- **Partition projection** for very many partitions.

**File layout:**
- Target **128 MB–1 GB** files; compact small files.
- **Columnar** (Parquet/ORC) + **compression** (Snappy/ZSTD) → less I/O.
- Sorting within files (or Iceberg sort orders) makes min/max statistics more effective at skipping row groups.

**Indexing:**
- **RDS/Aurora**: B-tree indexes on filter/join columns; avoid over-indexing write-heavy tables.
- **DynamoDB**: GSIs/Local Secondary Indexes [LSIs] (indexes cost extra writes and storage).
- **Redshift**: no traditional indexes. **Sort keys + zone maps** play that role.
- **OpenSearch**: inverted index (text) and k-NN index (vectors).

**Compression:** columnar codecs (Snappy for speed, ZSTD/GZIP for ratio); Redshift `ENCODE AUTO` / AZ64 / ZSTD.

### 🆕 Vectorization concepts (skill 2.4.6)

**Vectorization** = converting content (text, images) into embeddings so it can be searched by meaning. It's the data side of **RAG** (retrieval-augmented generation).

**Pipeline (Amazon Bedrock Knowledge Bases does this end to end):**

```
Data source (S3, web crawler, Confluence, SharePoint, Salesforce…)
   └─► Parsing (text, tables; optional advanced parsing for PDFs)
        └─► Chunking (fixed-size, semantic, hierarchical, or no chunking)
             └─► Embedding model (e.g., Amazon Titan Text Embeddings, Cohere Embed)
                  └─► Vector store (OpenSearch Serverless, Aurora PostgreSQL, MemoryDB, Neptune Analytics, Pinecone, MongoDB Atlas, Redis…)
                       └─► Retrieval: Retrieve API (chunks) or RetrieveAndGenerate API (answer + citations)
```

Key concepts:
- **Chunk size and overlap**: too large → noisy matches and more tokens; too small → lost context. Overlap preserves context across chunk boundaries.
- **Embedding dimensions**: more dimensions capture more nuance but cost more storage and compute. The **same embedding model** must be used for documents and queries.
- **Metadata filtering**: store attributes (department, date) with vectors to filter results.
- **Sync**: re-run knowledge base ingestion when source data changes (only changed documents are re-embedded).
- **Hybrid search**: combine keyword (Best Matching 25 [BM25]) and vector similarity for better relevance (supported with OpenSearch).

---

## Gotchas and exam traps

- **"Microsecond latency for DynamoDB reads"** → **DAX**. **"Durable in-memory primary database"** → **MemoryDB**, not ElastiCache.
- **"Vectors with relational data, SQL"** → **Aurora PostgreSQL + pgvector (HNSW)**. **"Full-text + vector hybrid search"** → **OpenSearch**.
- **HNSW** = graph, high recall, high memory. **IVF** = clusters, less memory, needs training.
- **"Updates/deletes/time travel on S3 data"** → **Iceberg**. **"…with automatic compaction and no maintenance"** → **S3 Tables**.
- Many small Iceberg files → **compaction** (`OPTIMIZE`), old snapshots bloating storage → **expire snapshots** (`VACUUM`).
- **Query S3 from Redshift without loading** → **Spectrum**. **Live Aurora/RDS data from Redshift** → **federated query**.
- **Share Redshift data across accounts without copying** → **data sharing** (RA3/Serverless).
- **DDL blocked or blocking reads in Redshift** → `AccessExclusiveLock`; find with `STV_LOCKS`, end with `PG_TERMINATE_BACKEND`.
- **KEY distribution on a low-cardinality column** → skew. Use `AUTO`/`EVEN` or a better key.
- **Small dimension table** → `DISTSTYLE ALL`.
- **COPY slow** → one big file. Split into multiple files (multiple of slices), compress.
- **Athena doesn't see new partitions** → `MSCK REPAIR TABLE` / `ADD PARTITION` / **partition projection** / crawler.
- **Thousands of partitions, slow Athena planning** → **partition projection** (or partition indexes).
- **Crawler created hundreds of tables** → enable "single schema per S3 path" / fix folder layout.
- **Unknown access pattern, minimize cost** → **Intelligent-Tiering**.
- **Lifecycle to Standard-IA** needs **30 days** in Standard first.
- **Delete in a versioned bucket** only adds a delete marker.
- **WORM, nobody can delete, not even root** → **Object Lock compliance mode**.
- **DynamoDB TTL** isn't immediate and doesn't consume Write Capacity Units (WCUs). Expired items flow to Streams.
- **LSI** can only be created **at table creation**.
- **Producers changing Avro/JSON schemas break consumers** → **Glue Schema Registry** with compatibility mode.
- **Heterogeneous DB migration** → **DMS Schema Conversion / SCT**, then DMS.
- **"What does this table mean, who owns it, request access"** → **SageMaker Catalog** (business catalog), not Glue Data Catalog.
- **Partition on `user_id`** → wrong; partition on date, **bucket** on high-cardinality columns.

---

## Quick-recall summary

- Domain weight **26%**. Tasks: choose store (2.1), catalogs (2.2), lifecycle (2.3), modeling and evolution (2.4).
- **S3** for the lake; storage classes by access frequency; 3,500 writes / 5,500 reads per second **per prefix**.
- **Redshift**: leader + compute slices; RA3 / Serverless; dist styles **AUTO/KEY/ALL/EVEN**; compound sort keys + zone maps; COPY in parallel; Spectrum, federated query, Materialized Views (MVs), data sharing, concurrency scaling, zero-ETL.
- **Athena**: serverless SQL; partitions, Parquet, compression, file sizing, **partition projection**; supports Iceberg DML.
- **DynamoDB**: high-cardinality partition key; GSI anytime / LSI at creation; on-demand vs provisioned; 400 KB items; DAX for microseconds.
- **MemoryDB** = durable in-memory; **ElastiCache** = cache.
- **Iceberg**: ACID, row-level DML, schema & partition evolution, hidden partitioning, time travel; maintain with compaction + snapshot expiry; **S3 Tables** = managed Iceberg with automatic maintenance.
- **Vectors**: embeddings + distance (cosine, L2, dot); **HNSW** (graph, fast, memory-heavy) vs **IVF** (clusters, lighter, needs training); stores = pgvector, OpenSearch, MemoryDB.
- **Locks**: Redshift AccessShare / ShareRowExclusive / AccessExclusive; `STV_LOCKS`; RDS deadlocks and `FOR UPDATE`.
- **Transfer Family** = SFTP into S3.
- **Glue Data Catalog** = technical metastore (Hive compatible) for Athena/Spectrum/EMR/Glue; **crawlers** with classifiers, schema change and recrawl policies.
- Partition sync: crawler, `MSCK REPAIR`, `ADD PARTITION`, Glue job catalog update, **partition projection**.
- **SageMaker Catalog** = business catalog: glossary, metadata forms, publish/subscribe with approval, AI descriptions, lineage.
- **COPY/UNLOAD**: multiple compressed files, IAM role, manifest, staging + MERGE for upserts, UNLOAD to Parquet.
- **S3 Lifecycle**: transitions, expirations, noncurrent versions, abort multipart; 30-day IA rule; minimum durations.
- **Versioning**: delete markers; suspend not disable; needed for replication and Object Lock.
- **TTL**: epoch seconds, free, delayed deletes, shows in Streams.
- **Legal**: Iceberg deletes for GDPR; **Object Lock** compliance/governance/legal hold for retention.
- **Resiliency**: S3 replication (+Replication Time Control [RTC]), DynamoDB PITR/global tables, Redshift snapshots + cross-Region copy + Multi-AZ, RDS Multi-AZ/replicas, Aurora Global Database, AWS Backup.
- **Modeling**: [star schema](00-data-basics-for-beginners.md#star-schema-fact-and-dimension-tables), SCD types 1/2/3; DynamoDB access-pattern-first and single-table design; lake zones raw/clean/curated.
- **Schema evolution**: crawler policies, **Glue Schema Registry** (BACKWARD default), Iceberg, `ResolveChoice`, late-binding views.
- **Schema conversion**: DMS Schema Conversion / SCT → DMS data move.
- **Lineage**: SageMaker Catalog (data), SageMaker ML Lineage Tracking (ML).
- **Optimization**: partition by filter columns (date), bucket high-cardinality, 128 MB–1 GB files, columnar + compression, indexes/sort keys.
- **Vectorization/RAG**: parse → chunk → embed → store → retrieve; Bedrock Knowledge Bases automates it.
