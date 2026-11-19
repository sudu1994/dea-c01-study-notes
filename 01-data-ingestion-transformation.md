# Domain 1: Data Ingestion and Transformation (34%)

> **The largest domain. Roughly 17 of the 50 scored questions.**
>
> This domain tests how data gets *into* Amazon Web Services (AWS) (streaming and batch), how it gets *reshaped* (Glue, Elastic MapReduce (EMR), Lambda, Redshift, containers, Large Language Models (LLMs)), how the steps are *orchestrated* (Step Functions, Managed Workflows for Apache Airflow (MWAA), Glue workflows, EventBridge), and the *programming practices* behind it (Lambda tuning, Infrastructure as Code (IaC), Serverless Application Model (SAM), Continuous Integration / Continuous Delivery (CI/CD), distributed computing). Most questions are "pick the right service/configuration with the least operational overhead."

## Table of contents

- [Exam tasks and skills](#exam-tasks-and-skills)
- [Task 1.1: Perform data ingestion](#task-11-perform-data-ingestion)
- [Task 1.2: Transform and process data](#task-12-transform-and-process-data)
- [Task 1.3: Orchestrate data pipelines](#task-13-orchestrate-data-pipelines)
- [Task 1.4: Apply programming concepts](#task-14-apply-programming-concepts)
- [Gotchas and exam traps](#gotchas-and-exam-traps)
- [Quick-recall summary](#quick-recall-summary)

## Exam tasks and skills

> Summarized from the official AWS Certified Data Engineer – Associate (DEA-C01) exam guide (v1.1). Read the exact wording at https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain1.html

### Task 1.1: Perform data ingestion
- **1.1.1** Read from streaming sources (Kinesis, Managed Streaming for Apache Kafka (MSK), DynamoDB Streams, Database Migration Service (DMS), Glue, Redshift).
- **1.1.2** Read from batch sources (Simple Storage Service (S3), Glue, EMR, DMS, Redshift, Lambda, AppFlow).
- **1.1.3** Configure batch ingestion appropriately.
- **1.1.4** Consume data Application Programming Interfaces (APIs).
- **1.1.5** Set up schedulers (EventBridge, Airflow, time-based schedules for jobs and crawlers).
- **1.1.6** Set up event triggers (S3 Event Notifications, EventBridge).
- **1.1.7** Invoke Lambda from Kinesis.
- **1.1.8** Create Internet Protocol (IP) allowlists so connections to data sources are permitted.
- **1.1.9** Handle throttling and rate limits (DynamoDB, Relational Database Service (RDS), Kinesis).
- **1.1.10** Manage fan-in and fan-out for streaming distribution.
- **1.1.11** Describe replayability of ingestion pipelines.
- **1.1.12** Define stateful vs stateless data transactions.

### Task 1.2: Transform and process data
- **1.2.1** Optimize container usage for performance (Elastic Kubernetes Service (EKS), Elastic Container Service (ECS)).
- **1.2.2** Connect to data sources (Java Database Connectivity (JDBC), Open Database Connectivity (ODBC)).
- **1.2.3** Integrate data from multiple sources.
- **1.2.4** Optimize processing costs.
- **1.2.5** Choose transformation services by requirement (EMR, Glue, Lambda, Redshift).
- **1.2.6** Convert between formats (e.g., Comma-Separated Values (CSV) → Parquet).
- **1.2.7** Troubleshoot transformation failures and performance issues.
- **1.2.8** Create data APIs that expose data to other systems.
- **1.2.9** Define volume, velocity, and variety (structured vs unstructured).
- **1.2.10** 🆕 Integrate LLMs for data processing.

### Task 1.3: Orchestrate data pipelines
- **1.3.1** Build Extract, Transform, Load (ETL) workflows with orchestration services (Lambda, EventBridge, MWAA, Step Functions, Glue workflows).
- **1.3.2** Build pipelines for performance, availability, scalability, resiliency, fault tolerance.
- **1.3.3** Implement and maintain serverless workflows.
- **1.3.4** Send alerts with notification services (Simple Notification Service (SNS), Simple Queue Service (SQS)).

### Task 1.4: Apply programming concepts
- **1.4.1** Optimize code to reduce ingestion/transformation runtime.
- **1.4.2** Configure Lambda for concurrency and performance.
- **1.4.3** Use data engineering languages and frameworks (Python, Structured Query Language (SQL), Scala, R, Java, Bash, PowerShell).
- **1.4.4** Apply software engineering practices (version control, testing, logging, monitoring).
- **1.4.5** Deploy data engineering solutions with IaC.
- **1.4.6** Package and deploy serverless pipelines with AWS SAM.
- **1.4.7** Use and mount storage volumes in Lambda.
- **1.4.8** Use IaC (CloudFormation, Cloud Development Kit (CDK)) for repeatable deployments.
- **1.4.9** Describe CI/CD for data pipelines.
- **1.4.10** Define distributed computing.
- **1.4.11** Describe data structures and algorithms (graphs, trees).

---

## Task 1.1: Perform data ingestion

### Core concepts

**The ingestion decision tree** (mental model for "which service" questions):

1. **Is the data arriving continuously (events, clicks, IoT, logs)?** → Streaming. Otherwise batch.
2. **Streaming: do you need custom consumers, multiple consumers, ordering, or replay?** → **Kinesis Data Streams**. Do you just need to land it somewhere with no code? → **Amazon Data Firehose**. Do you need Kafka APIs or existing Kafka clients? → **Amazon MSK**.
3. **Batch: where is the source?**
   - Relational/NoSQL database → **AWS DMS** (or **zero-ETL** to Redshift if supported)
   - Software as a Service (SaaS) app (Salesforce, ServiceNow, Zendesk…) → **Amazon AppFlow**
   - On-prem file shares (NFS/Server Message Block (SMB)/HDFS) → **AWS DataSync**
   - Partners pushing files over SSH File Transfer Protocol (SFTP) → **AWS Transfer Family**
   - Petabytes, little bandwidth → **AWS Snow Family**
   - Third-party/commercial datasets → **AWS Data Exchange**
4. **How is the job started?** Schedule → EventBridge Scheduler / MWAA / Glue trigger. Event → S3 Event Notifications / EventBridge rule.
5. **Must it be reprocessable?** → keep raw data in S3 and/or use a retained stream (Kinesis Data Streams (KDS), MSK).

### Streaming sources (skill 1.1.1)

| Service | Model | Latency | Scaling | Replay | Choose when |
|---|---|---|---|---|---|
| **Kinesis Data Streams (KDS)** | Ordered shards; you write consumers | ~200 ms (~70 ms with enhanced fan-out) | Shards (provisioned) or **on-demand** | ✅ 24 h default, up to 365 days | Real time, multiple consumers, custom processing, ordering per key |
| **Amazon Data Firehose** | Managed delivery, buffered | Near real time (buffer by size/time; zero buffering option) | Automatic | ❌ | Land data in S3, Redshift, OpenSearch, Splunk, Snowflake, Hypertext Transfer Protocol (HTTP), **Iceberg tables** with no code |
| **Amazon MSK** (provisioned / Serverless) | Kafka topics & partitions | Real time | Brokers/partitions or serverless | ✅ topic retention | Kafka compatibility, existing Kafka apps, Kafka Connect (**MSK Connect**) |
| **DynamoDB Streams** | Item-level change log | Near real time | Automatic | ❌ only 24 h | React to DynamoDB inserts/updates/deletes (Change Data Capture (CDC) from DynamoDB) |
| **Kinesis Data Streams for DynamoDB** | DynamoDB changes into a KDS stream | Near real time | KDS | ✅ (KDS retention) | DynamoDB CDC with longer retention or more consumers |
| **AWS DMS (CDC)** | Reads database (DB) transaction logs | Seconds | Replication instance or DMS Serverless | ❌ (re-run task) | Ongoing replication from RDS/Aurora/Oracle/SQL Server/on-prem |
| **AWS Glue streaming ETL** | Spark Structured Streaming micro-batches from KDS/MSK | Seconds | Workers (G.025X for low volume) | via source | Transform streams with Spark, write to S3/Iceberg |
| **Redshift streaming ingestion** | Materialized view over KDS/MSK | Seconds | Redshift | via source | Get stream data into Redshift **without staging in S3** |

#### Kinesis Data Streams deep dive

**Shard limits (memorize):**
- **Write:** 1 MB/s **or** 1,000 records/s per shard (whichever comes first)
- **Read (shared):** 2 MB/s per shard, split across all standard consumers, max 5 `GetRecords` calls/s per shard
- **Read (enhanced fan-out):** 2 MB/s **per consumer** per shard, pushed via HTTP/2

**Shard calculation example:**
> 3,000 records/s × 2 KB = 6 MB/s ingest; 3 consumers each reading everything.
> - Write: max(6 MB ÷ 1, 3,000 ÷ 1,000) = **6 shards**
> - Read (shared): 3 consumers × 6 MB/s = 18 MB/s ÷ 2 = **9 shards**, or keep 6 shards and use **enhanced fan-out**.

**Partition keys:** the key is hashed to pick a shard. A **low-cardinality key** (e.g., `country`) creates a **hot shard** → `ProvisionedThroughputExceededException` even when total capacity looks fine. Fix with a high-cardinality key (device ID, user ID) or a random suffix.

**Capacity modes:**
- **Provisioned**: you set shard count; split/merge shards (resharding) to scale. Cheaper for steady, predictable traffic.
- **On-demand**: scales automatically. Best for unpredictable or spiky traffic, no capacity planning.

**Producers and consumers:**
- **KPL (Kinesis Producer Library):** aggregation + batching + retries → high throughput, adds a little latency.
- **KCL (Kinesis Client Library):** distributes shards across workers, checkpoints progress in a **DynamoDB lease table**. If the KCL app is throttled on DynamoDB, increase that table's capacity.
- **`IteratorAgeMilliseconds`** (`GetRecords.IteratorAgeMilliseconds`): how far behind consumers are. Rising iterator age = consumers can't keep up.

#### Amazon Data Firehose deep dive

- **Buffering:** delivers when either the size (1–128 MiB) or interval threshold is hit. Bigger buffers → fewer, larger S3 files (better for Athena). Smaller → lower latency.
- **Record format conversion:** JavaScript Object Notation (JSON) → **Parquet or Optimized Row Columnar (ORC)** using a schema from a **Glue Data Catalog table**. Most common "least operational effort" answer for "convert streaming JSON to Parquet".
- **Lambda transformation:** enrich/clean records in flight (blueprints available).
- **Dynamic partitioning:** writes into S3 prefixes based on record fields (e.g., `customer_id=…/year=…/`) → Athena-friendly partitions.
- **Redshift destination:** Firehose writes to S3, then issues a `COPY` into Redshift.
- **Failed records** go to an S3 error prefix. Firehose has **no replay**. If you need reprocessing, put KDS in front (KDS → Firehose) or keep the raw copy.
- **Source** can be direct PUT, KDS, MSK, CloudWatch Logs subscriptions, and others.

#### Amazon MSK deep dive

- **Provisioned**: you choose broker type/count and storage; full Kafka config control.
- **MSK Serverless**: no broker sizing; good when you want Kafka APIs without capacity management.
- **MSK Connect**: managed Kafka Connect workers (e.g., S3 sink connector, Debezium CDC source).
- Choose MSK over KDS when the scenario says **"Kafka"**, "existing Kafka producers/consumers", "open-source portability", or needs very long retention or large messages.

### Batch sources (skills 1.1.2, 1.1.3)

| Source / need | Service | Key configuration options |
|---|---|---|
| Files already in S3 | **Glue jobs / crawlers**, **Athena CREATE TABLE AS SELECT (CTAS)**, **Redshift COPY** | Partitioned prefixes, file sizing, compression, manifest files |
| Relational DB snapshot + ongoing changes | **AWS DMS** | Task type (**full load**, **full load + CDC**, **CDC only**), table mappings, transformation rules, Large Object (LOB) settings, data validation |
| Operational DB → Redshift with no pipeline | **Zero-ETL integrations** | Aurora MySQL/PostgreSQL, RDS MySQL, DynamoDB → Redshift |
| SaaS apps | **Amazon AppFlow** | Trigger: on demand / scheduled / event; field mapping, filtering, masking, validation; destinations S3, Redshift, Snowflake |
| On-prem file systems | **AWS DataSync** | Agent on-prem, scheduled tasks, bandwidth throttling, integrity verification, filters |
| Hadoop/Spark on large datasets | **Amazon EMR** | Reads from S3 (EMR File System (EMRFS)), Hadoop Distributed File System (HDFS), HBase |
| Small custom pulls | **AWS Lambda** | Scheduled with EventBridge, ≤15 min runtime |
| Data warehouse exports | **Redshift `UNLOAD`** | To S3 in Parquet, partitioned, parallel |

**DMS details the exam likes:**
- **Components:** replication instance (or DMS Serverless), source/target **endpoints**, **replication task**.
- **CDC prerequisites:** the source must expose change logs. MySQL needs **binary logging with `binlog_format=ROW`**. Oracle needs **supplemental logging**. PostgreSQL needs **logical replication**. SQL Server needs Microsoft SQL Server Change Data Capture (MS-CDC)/MS-Replication.
- **DMS does light transforms only** (rename, add/drop columns, filter rows). Heavy logic goes downstream in Glue/EMR.
- **S3 target**: can write CSV or **Parquet**; CDC files land with an operation column (`I`/`U`/`D`), which you later merge (Iceberg `MERGE` is a great fit).
- **DMS Schema Conversion** (inside DMS) converts schemas for heterogeneous migrations. The standalone AWS Schema Conversion Tool (SCT) is no longer in scope.

### Consuming data APIs (skill 1.1.4)

Pattern: **EventBridge Scheduler → Lambda (or Glue Python shell) → call REST Application Programming Interface (API) → write raw JSON to S3 → crawler/Glue job.**

Things to handle:
- **Authentication:** store API keys/OAuth secrets in **AWS Secrets Manager**, never in code or plain environment variables.
- **Pagination:** loop through pages/cursors. If it may exceed 15 minutes, use Step Functions (loop or Map) or a Glue Python shell job.
- **Rate limits:** exponential backoff with jitter, respect `Retry-After`, throttle with SQS.
- **Idempotency:** write each page to a deterministic S3 key so retries don't duplicate data.
- **SaaS with a built-in connector?** Prefer **AppFlow**. No code means less operational overhead.

### Schedulers and event triggers (skills 1.1.5, 1.1.6)

| Mechanism | Use |
|---|---|
| **EventBridge Scheduler** | Cron/rate schedules with time zones, one-time schedules, retries + Dead-Letter Queue (DLQ); can target almost any AWS API |
| **EventBridge rules (schedule)** | Older way to schedule; still valid |
| **Glue triggers** | Scheduled, on-demand, or conditional (start job B when job A succeeds) |
| **Crawler schedules** | Cron schedule on the crawler itself |
| **MWAA (Airflow)** | `schedule` on a Directed Acyclic Graph (DAG); best when the pipeline is already Airflow |
| **Redshift scheduled queries** | Run SQL on a schedule (Redshift Data API under the hood) |

**S3 Event Notifications vs EventBridge:**

| | S3 Event Notifications | S3 → EventBridge |
|---|---|---|
| Targets | Lambda, SQS, SNS | 20+ targets (Step Functions, Glue workflows via API, Kinesis, etc.) |
| Filtering | Prefix/suffix only | Rich content filtering (object size, key patterns, metadata) |
| Multiple targets for same event | Limited (overlapping prefixes not allowed) | Many rules on the same event |
| Archive & replay | ❌ | ✅ |

> Rule of thumb: one simple target → S3 Event Notification. Complex filtering, multiple consumers, or starting Step Functions directly → **EventBridge**.

**Crawler-specific trick:** instead of re-crawling a huge bucket on a schedule, use **S3 event-mode crawlers** (S3 events → SQS → crawler crawls only changed prefixes).

### Calling Lambda from Kinesis (skill 1.1.7)

Lambda reads KDS through an **event source mapping** (Lambda polls the stream; you don't write polling code).

| Setting | What it does | Exam use |
|---|---|---|
| **Batch size** | Records per invocation (up to 10,000) | Bigger = fewer invocations, more efficient |
| **Batch window** | Wait up to N seconds (≤300) to fill a batch | Reduce invocations for low-traffic streams |
| **Parallelization factor** | 1–10 concurrent batches **per shard** | Increase throughput **without adding shards** (ordering kept per partition key) |
| **Starting position** | `TRIM_HORIZON` (oldest), `LATEST`, `AT_TIMESTAMP` | Reprocess from the beginning with `TRIM_HORIZON` |
| **Bisect batch on function error** | Splits a failing batch in half to isolate a bad record | "One poison record blocks the shard" |
| **Maximum retry attempts / maximum record age** | Stop retrying old/failing records | Prevent a shard from being stuck forever |
| **On-failure destination** | Send metadata of failed batches to SQS/SNS | Keep processing, inspect failures later |
| **Tumbling windows** | Aggregate state across invocations (up to 15 min) | Simple **stateful** aggregations in Lambda |
| **Enhanced fan-out consumer** | Dedicated throughput for this Lambda | Lambda is one of several consumers |

> ⚠️ By default, a failed batch is **retried until it succeeds or the data expires**, and the shard is **blocked** meanwhile. Expect a question where the fix is bisect-on-error + max retries + on-failure destination.

### IP allowlists for data sources (skill 1.1.8)

Common scenario: an **external** database or API only accepts connections from approved IP addresses.

- AWS services in a Virtual Private Cloud (VPC) (Glue jobs, Lambda, EMR, ECS) reach the internet through a **Network Address Translation (NAT) gateway**. Give the partner the **NAT gateway's Elastic IP** to allowlist. This gives a fixed, known IP.
- Lambda/Glue **without** a VPC uses random AWS Internet Protocol addresses (IPs), which can't be reliably allowlisted.
- Inbound allowlisting to *your* resources: security groups (stateful) or network Access Control Lists (ACLs) (stateless). For AWS services that connect *to* your resources (e.g., Firehose → Redshift/Splunk, QuickSight → RDS), allow that service's **published IP ranges / Classless Inter-Domain Routing (CIDR) for the Region**.
- **Glue JDBC connections** run in your VPC subnet. The security group needs a **self-referencing inbound rule (all Transmission Control Protocol (TCP))** so Glue workers can talk to each other, and the subnet needs a route to the data source (or a NAT gateway / VPC endpoint for S3).

### Throttling and rate limits (skill 1.1.9)

| Source | Symptom | Fixes |
|---|---|---|
| **DynamoDB** | `ProvisionedThroughputExceededException`, `ThrottlingException` | On-demand mode or auto scaling, better partition key (avoid hot keys), `BatchWriteItem` with retries of `UnprocessedItems`, exponential backoff, SQS buffer in front, DynamoDB Accelerator (DAX) for read-heavy traffic |
| **RDS / Aurora** | "Too many connections" from many Lambdas | **RDS Proxy** (connection pooling), reserved concurrency to cap Lambda, read replicas for reads |
| **Kinesis** | `ProvisionedThroughputExceededException` on put or get | More shards / on-demand, high-cardinality partition key, `PutRecords` batching, KPL aggregation, enhanced fan-out for readers |
| **Any AWS API** | `ThrottlingException`, `Rate exceeded` | Software Development Kit (SDK) retries with **exponential backoff and jitter**, request quota increase |
| **External APIs** | HTTP 429 | Backoff, honor `Retry-After`, queue requests in SQS, limit concurrency |

### Fan-in and fan-out (skill 1.1.10)

- **Fan-in:** many producers → one stream (thousands of devices → one KDS stream or Firehose stream). Also many streams → one destination (several Firehose streams into one bucket with different prefixes).
- **Fan-out:** one stream → many consumers:
  - **KDS enhanced fan-out**: each consumer gets dedicated 2 MB/s per shard.
  - **SNS → multiple SQS queues** (classic pub/sub fan-out with buffering per consumer).
  - **EventBridge** rule with several targets, or several rules on the same event.
  - **MSK consumer groups**: each group reads the full topic independently.
- **Firehose** delivers to **one destination per stream**. To fan out, put KDS first and attach multiple Firehose streams.

```
              ┌──► Lambda (real-time alerts)          [enhanced fan-out]
Producers ──► KDS ──► Firehose ──► S3 (Parquet) ──► Athena
              └──► Managed Service for Apache Flink ──► OpenSearch dashboards
```

### Replayability (skill 1.1.11)

Replayability = the ability to **re-run ingestion/processing over past data** after a bug fix, a schema change, or a new consumer.

| Mechanism | Replay window |
|---|---|
| **KDS** | Retention up to 365 days. New consumer can start at `TRIM_HORIZON` or `AT_TIMESTAMP`. |
| **MSK** | Topic retention (time or size based); reset consumer group offsets |
| **S3 raw/bronze zone** | Indefinite. **Keep the immutable raw copy** and rebuild downstream tables. |
| **EventBridge archive** | Archive events, then replay to a bus |
| **Glue job bookmarks** | Reset the bookmark to reprocess everything |
| **DynamoDB Streams** | 24 h only (use KDS for DynamoDB for longer) |
| **Firehose / SQS** | ❌ no replay once delivered/deleted |

> Design principle: **land raw data unchanged first, then transform.** It's the safest replay strategy and a common correct answer.

### Stateful vs stateless (skill 1.1.12)

| | Stateless | Stateful |
|---|---|---|
| Meaning | Each record is processed independently | Processing depends on previous records or stored state |
| Examples | Filter, format conversion, field masking, per-record enrichment | Windowed aggregations (count per 5 min), deduplication, sessionization, stream joins, running totals |
| AWS tools | Lambda per record, Firehose Lambda transform | **Managed Service for Apache Flink** (checkpoints, savepoints), Glue streaming with checkpoints, **Lambda tumbling windows**, KCL with DynamoDB checkpoints |
| Scaling | Easy, any worker can process any record | Must preserve state; partition by key so related records hit the same worker |

**Transactions:** "stateful/transactional" may also mean **Atomicity, Consistency, Isolation, Durability (ACID) guarantees**: all-or-nothing writes (Redshift, Aurora, **Apache Iceberg** commits) vs eventually consistent, append-only writes (plain S3 files).

---

## Task 1.2: Transform and process data

### Choosing a transformation service (skill 1.2.5)

| Requirement | Best fit | Why |
|---|---|---|
| Serverless Spark ETL integrated with the Data Catalog, minimal ops | **AWS Glue** | No clusters; bookmarks, crawlers, Data Quality built in |
| Visual / no-code cleaning and profiling for analysts | **Glue DataBrew** | 250+ point-and-click transforms, profile jobs |
| Full Hadoop ecosystem (Spark, Hive, Presto/Trino, HBase, Hudi), custom versions, tuning, Spot | **Amazon EMR** (on Elastic Compute Cloud (EC2)) | Full control; cheapest at large scale with Spot task nodes |
| Spark without managing clusters, but EMR runtime | **EMR Serverless** | Pay per vCPU/GB-second, auto scale |
| Spark on existing Kubernetes | **EMR on EKS** | Shares EKS cluster with other apps |
| Lightweight per-event transforms (< 15 min) | **AWS Lambda** | Event-driven, no servers |
| SQL transforms on S3 data | **Athena CTAS / INSERT INTO** | Serverless SQL, no ETL code |
| SQL transforms inside the warehouse (Extract, Load, Transform (ELT)) | **Amazon Redshift** | Stored procedures, materialized views, `MERGE` |
| Real-time, stateful stream processing | **Managed Service for Apache Flink** | Windows, joins, exactly-once state |
| Long-running containerized jobs beyond Lambda limits | **ECS/EKS on Fargate**, **AWS Batch** | Any runtime, any duration |

#### AWS Glue essentials

| Feature | Explanation |
|---|---|
| **Job types** | **Spark** (large ETL), **Spark Streaming**, **Python shell** (small jobs, pandas-scale, cheap), **Ray** (distributed Python) |
| **DynamicFrame** | Glue's DataFrame that tolerates inconsistent schemas. `ResolveChoice` fixes mixed types (e.g., a column that is sometimes string, sometimes int). `Relationalize` flattens nested JSON into tables. Convert to Spark DataFrame with `toDF()` when you need Spark APIs. |
| **Job bookmarks** | Remember what was already processed → incremental loads. Needs `job.init()`/`job.commit()` and a `transformation_ctx`. |
| **Pushdown predicates** | `push_down_predicate="year='2026'"` filters **partitions before listing/reading S3** → much faster on partitioned data |
| **Worker types** | **G.1X / G.2X** standard; larger (G.4X, G.8X) for memory-heavy jobs; **G.025X** for low-volume streaming |
| **Auto Scaling** | Adds/removes workers during the run; pay only for what's used |
| **Flex execution** | Runs on spare capacity at a lower price; start time not guaranteed → **non-urgent jobs only** |
| **Glue Studio** | Visual job authoring that generates code |
| **Glue connections** | JDBC (RDS, Redshift, on-prem databases (DBs)), MongoDB, Kafka, plus marketplace/custom connectors |
| **Glue Data Quality** | Rules in Data Quality Definition Language (DQDL) (see Domain 3) |

#### Amazon EMR essentials

- **Node types:** **Primary** (coordinates; one per cluster, or 3 for High Availability (HA)), **Core** (runs tasks **and stores HDFS data**), **Task** (compute only, **no HDFS** → perfect for **Spot**).
- **Persistent vs transient:** transient clusters spin up for a job and terminate → keep data in **S3 via EMRFS**, not HDFS.
- **Instance fleets** let you mix instance types and On-Demand/Spot with allocation strategies.
- **Managed scaling** resizes the cluster automatically.
- **Graviton** instances give better price/performance.

### Containers for data processing (skill 1.2.1)

| Option | When |
|---|---|
| **ECS on Fargate** | Containerized ETL longer than 15 min, no servers to manage |
| **EKS** | Organization standard is Kubernetes; Spark operator; **EMR on EKS** |
| **AWS Batch** | Many independent batch jobs, queues, job dependencies, Spot |

Optimization levers:
- Right-size task CPU/memory (CloudWatch Container Insights shows actual usage).
- **Fargate Spot** / EC2 Spot for interruptible batch work.
- Graviton (Advanced RISC Machine (ARM)) images for cheaper compute.
- Horizontal scaling (more tasks/pods) for parallelizable work; cluster autoscaler or Karpenter for EKS nodes.
- Keep images small for faster startup.

### Connecting to data sources (skill 1.2.2)

- **JDBC** (Java Database Connectivity) and **ODBC** (Open Database Connectivity) are standard database driver APIs. Glue, EMR/Spark, and Athena federated connectors use JDBC. Business Intelligence (BI) tools (Excel, Tableau, Power BI) often use ODBC.
- **Glue connection** = JDBC Uniform Resource Locator (URL) + credentials (Secrets Manager) + VPC subnet + security group.
- Custom/newer drivers: upload the JDBC driver JAR to S3 and reference it in the job.
- **Redshift** and **Athena** provide JDBC/ODBC drivers for client tools.
- **Redshift Data API** and **Athena API** avoid drivers entirely (Hypertext Transfer Protocol Secure (HTTPS) calls, good for Lambda).

### Integrating multiple sources (skill 1.2.3)

| Pattern | Service |
|---|---|
| Join data from S3 + JDBC sources in one ETL | **Glue job** with multiple sources |
| Query across S3, DynamoDB, RDS, CloudWatch Logs in one SQL statement | **Athena Federated Query** (Lambda-based connectors) |
| Join warehouse tables with live Aurora/RDS PostgreSQL or MySQL data | **Redshift federated query** |
| Join warehouse tables with S3 data lake | **Redshift Spectrum** |
| Replicate operational DBs into the warehouse continuously | **Zero-ETL** integrations |
| Centralize everything first | Land all sources in an S3 data lake (raw → curated) |

### Optimizing processing cost (skill 1.2.4)

- **Glue:** Flex for non-urgent jobs, Auto Scaling, right worker type, Python shell instead of Spark for small data, job bookmarks (don't reprocess), pushdown predicates.
- **EMR:** transient clusters, **Spot for task nodes**, Graviton, managed scaling, EMR Serverless for intermittent jobs.
- **Lambda:** right-size memory (more memory can be *cheaper* if it shortens runtime), Graviton (arm64), batch records.
- **Athena:** columnar formats + compression + partitions = less data scanned = lower cost.
- **Redshift:** Serverless for intermittent use, pause/resume provisioned clusters, Reserved Instances for steady use, Spectrum for cold data.
- **Data layout:** convert to Parquet, compact small files, lifecycle old data to cheaper S3 classes.

### Format conversion (skill 1.2.6)

| Format | Layout | Splittable | Best for |
|---|---|---|---|
| CSV | Row, text | Yes (uncompressed or with splittable codec) | Ingestion, interchange |
| JSON | Row, text, nested | Yes, line-delimited | APIs, logs |
| **Parquet** | **Columnar**, typed, compressed | ✅ | **Analytics (Athena, Spectrum, Spark)**: read only needed columns |
| **ORC** | Columnar | ✅ | Hive-based analytics |
| **Avro** | Row, schema in file | ✅ | Streaming, Kafka, schema evolution, write-heavy |

**Compression codecs:** **Snappy** (fast, default for Parquet), **GZIP** (high compression; a gzipped CSV/JSON file is **not splittable**, so one worker per file), **Zstandard (ZSTD)** (good balance), **BZIP2** (splittable but slow), **LZO** (splittable with index).

**Ways to convert CSV/JSON → Parquet:**
1. **Firehose record format conversion** (streaming, no code)
2. **Glue job** (`write_dynamic_frame` with `format="parquet"`)
3. **Athena CTAS** (`CREATE TABLE … WITH (format='PARQUET', partitioned_by=…) AS SELECT …`)
4. **EMR/Spark** at very large scale
5. **DMS** with an S3 target in Parquet format

### Troubleshooting transformations (skill 1.2.7)

| Symptom | Likely cause | Fix |
|---|---|---|
| Glue/Spark **driver** Out Of Memory (OOM) | `collect()` to driver, or millions of small files tracked by driver | Avoid `collect`, use `groupFiles`/`groupSize` to group small files, bigger worker type |
| **Executor** OOM / one task runs forever | **Data skew**: one key has most rows | Salt the key, repartition, broadcast join the small table, larger workers |
| Job slow reading S3 | Many tiny files, no partition pruning, GZIP CSV | Compact files (128 MB–1 GB), pushdown predicates, Parquet |
| Glue job can't reach RDS | Networking | Glue connection in correct VPC/subnet, self-referencing Security Group (SG) rule, route/NAT, DB SG allows Glue SG |
| Athena `HIVE_PARTITION_SCHEMA_MISMATCH` | Partition schema differs from table schema | Update partitions / recrawl with "update all partitions from table" |
| Athena doesn't see new partitions | Partitions not registered | `MSCK REPAIR TABLE`, `ALTER TABLE ADD PARTITION`, **partition projection**, or rerun crawler |
| Redshift `COPY` fails | Bad rows, type mismatch, wrong delimiter | Check `STL_LOAD_ERRORS` / `SYS_LOAD_ERROR_DETAIL`; use `MAXERROR` carefully |
| Crawler creates many tables instead of one | Inconsistent schemas or folder structure | "Create a single schema for each S3 path" option, consistent formats, set table level |

**Where to look:** CloudWatch Logs (driver and executor logs), **Glue job metrics / job run insights**, **Spark User Interface (UI)** (Glue and EMR) for stages, skew, shuffle size, EMR step logs in S3.

### Creating data APIs (skill 1.2.8)

| Pattern | Use |
|---|---|
| **API Gateway → Lambda → DynamoDB** | Low-latency key lookups |
| **API Gateway → Lambda → Redshift Data API** | Expose warehouse queries without managing JDBC connections (async: submit, poll, fetch) |
| **API Gateway → Lambda → Athena** | Ad-hoc queries over the lake (async, results in S3) |
| **AWS AppSync** (GraphQL) | Flexible client-defined queries across multiple data sources |
| **Redshift data sharing / Data Exchange** | Share data with other teams/customers without building an API |

Add: API keys/usage plans or Cognito/Identity and Access Management (IAM) auth, caching in API Gateway, throttling limits.

### Volume, velocity, variety (skill 1.2.9)

| V | Meaning | Design impact |
|---|---|---|
| **Volume** | How much data (GB → PB) | Distributed processing (Spark/EMR/Glue), columnar storage, partitioning |
| **Velocity** | How fast it arrives (batch → real time) | Batch jobs vs streaming (KDS/MSK/Flink) |
| **Variety** | Types of data | **Structured** (tables, fixed schema: RDS/Redshift), **semi-structured** (JSON, Extensible Markup Language (XML), Avro: S3 + Glue, Redshift `SUPER`), **unstructured** (images, Portable Document Format files (PDFs), audio, free text: S3 + Artificial Intelligence (AI) services/LLMs) |

### 🆕 Integrating LLMs for data processing (skill 1.2.10)

**Why:** LLMs turn unstructured text into structured data inside a pipeline: classify support tickets, extract entities from contracts, summarize call transcripts, standardize messy addresses, translate, or detect sentiment.

**Reference architecture (batch):**

```
S3 raw documents ──► Glue / Lambda (chunk & clean, mask PII)
                         │
                         ├─ small volume / near real time ──► Bedrock InvokeModel / Converse API
                         └─ large volume / offline ─────────► Bedrock batch inference (JSONL in S3 → JSONL out)
                                                                   │
                                                  S3 curated (Parquet) ◄─ parse model output
                                                                   │
                                                     Glue Data Catalog ──► Athena / Redshift
```

**Integration options:**

| Option | When |
|---|---|
| **Lambda or Glue calling Amazon Bedrock** | Per-record enrichment in an existing pipeline |
| **Step Functions optimized Bedrock integration** | Orchestrated workflow; call a model directly from a state, no Lambda needed |
| **Bedrock batch inference** | Large datasets, not latency-sensitive → **lower cost than on-demand**, avoids throttling |
| **Redshift Machine Learning (ML) + Bedrock** (`CREATE EXTERNAL MODEL`) | Analysts call a Large Language Model (LLM) from SQL inside Redshift |
| **Amazon Comprehend** | Standard Natural Language Processing (NLP) (sentiment, entities, Personally Identifiable Information (PII), language) without prompts. Often simpler and cheaper for those specific tasks. |
| **Amazon Q** (in QuickSight / Redshift query editor) | Natural language → SQL or insights for people, not pipeline processing |

**Design considerations:**
- **Throttling/quotas:** backoff + retries, SQS buffering, or batch inference.
- **Cost:** tokens in + out × records. Use the smallest model that meets quality; batch for bulk.
- **Determinism:** low temperature, ask for **structured JSON output**, validate the schema, send invalid outputs to a retry/DLQ path.
- **Privacy:** mask PII before sending (Glue sensitive data detection / Comprehend), use **Bedrock Guardrails**, use VPC endpoints (PrivateLink). Bedrock doesn't use your prompts to train base models.

---

## Task 1.3: Orchestrate data pipelines

### Orchestration services (skill 1.3.1)

| Service | Best for | Key facts |
|---|---|---|
| **AWS Step Functions** | Serverless workflows calling many AWS services | Visual state machines (Amazon States Language (ASL) JSON); **Standard** (up to 1 year, exactly-once, full history) vs **Express** (up to 5 min, very high volume, at-least-once, cheaper); `.sync` waits for Glue/EMR/Athena/Batch jobs to finish; **Retry**/**Catch** per state; **Parallel**, **Choice**, **Wait**, **Map**; **Distributed Map** processes millions of S3 objects in parallel |
| **Amazon MWAA** | Apache Airflow Directed Acyclic Graphs (DAGs) written in Python | Pick when the team already uses Airflow, needs many third-party/open-source operators, or complex dependency scheduling. DAGs and plugins/requirements live in an S3 bucket. |
| **AWS Glue workflows** | Chains of Glue crawlers and jobs only | Triggers (scheduled, on-demand, conditional on success/failure/completion); simplest for Glue-only pipelines |
| **Amazon EventBridge** | Event-driven starts and schedules | Starts any of the above on S3 events, schedules, or custom events |
| **AWS Lambda** | Glue code between steps | Not an orchestrator by itself (15 min limit, no state) |

**Choosing:**
- Only Glue jobs and crawlers → **Glue workflows**
- Mixed AWS services, serverless, least ops → **Step Functions**
- Existing Airflow / Python DAGs / open-source portability → **MWAA**
- "Start the pipeline when a file lands" → **EventBridge rule → Step Functions**

**Reference architecture (daily batch pipeline):**

```
EventBridge (cron 02:00) ──► Step Functions (Standard)
      1. Glue crawler (raw)              [.sync]
      2. Glue job: raw → curated Parquet [.sync, Retry x3 with backoff]
      3. Glue Data Quality evaluation    [Choice: pass/fail]
      4. Parallel:
           a. Redshift COPY via Data API
           b. Athena CTAS for aggregates
      Catch (any failure) ──► SNS topic ──► email / Slack / on-call
```

### Building resilient, scalable pipelines (skill 1.3.2)

| Quality | Technique |
|---|---|
| **Fault tolerance** | Retries with exponential backoff, Catch → fallback/alert, **dead-letter queues** (SQS DLQ, Lambda on-failure destinations), checkpointing (bookmarks, KCL, Flink) |
| **Idempotency** | Re-running a step gives the same result: overwrite partitions instead of appending, use `MERGE`/upserts, deterministic output paths |
| **Availability** | Multi-AZ managed services, decouple stages with SQS/KDS so one slow stage doesn't break others |
| **Scalability** | Serverless/auto-scaling services (Glue Auto Scaling, KDS on-demand, Lambda, EMR managed scaling), partition data for parallelism |
| **Performance** | Parallel states, Distributed Map, columnar formats, right-sized compute |

### Serverless workflows (skill 1.3.3)

A fully serverless pipeline: **S3 → EventBridge → Step Functions → Lambda / Glue / Athena / Redshift Serverless → SNS**. There are no servers to patch and everything scales automatically, so it's usually the answer for "least operational overhead."

Maintenance points: version the state machine definition in Git and deploy with IaC/SAM; use CloudWatch metrics (`ExecutionsFailed`, `ExecutionsTimedOut`) and X-Ray tracing; use Step Functions versions and aliases for safe rollout.

### Notifications and alerts (skill 1.3.4)

| | Amazon SNS | Amazon SQS |
|---|---|---|
| Model | **Push**, pub/sub | **Pull**, queue |
| Use | Alerts to email/Short Message Service (SMS)/HTTP/Lambda; fan-out to many subscribers | Buffer work, decouple producers/consumers, DLQ for failures |
| Typical exam use | "Notify the team when the Glue job fails" | "Hold failed messages for later reprocessing", "smooth spikes into a database" |

Common alert wiring: **Glue job state change → EventBridge rule → SNS**; **CloudWatch alarm → SNS**; **Step Functions Catch → SNS publish**. Use **SNS First-In, First-Out (FIFO) + SQS FIFO** when order and exactly-once delivery matter.

---

## Task 1.4: Apply programming concepts

### Optimizing code (skill 1.4.1)

- **Read less:** partition pruning, column pruning (`SELECT` only needed columns), predicate pushdown, columnar formats.
- **Spark specifics:** prefer built-in functions over Python User-Defined Functions (UDFs) (UDFs are slow and block optimization); broadcast small tables in joins; `repartition`/`coalesce` to control file counts; cache only reused DataFrames; avoid `collect()`.
- **Batching:** batch API calls (`PutRecords`, `BatchWriteItem`) instead of one call per record.
- **Connection reuse:** in Lambda, create SDK clients and DB connections **outside the handler** so warm invocations reuse them.
- **SQL:** filter early, avoid `SELECT *`, use window functions instead of self-joins, use `UNION ALL` instead of `UNION` when duplicates are impossible.

### Configuring Lambda (skill 1.4.2)

| Setting | Range / behavior | Exam angle |
|---|---|---|
| **Memory** | 128 MB – 10,240 MB; **Central Processing Unit (CPU) scales with memory** | CPU-bound job slow → increase memory |
| **Timeout** | Up to **15 minutes** | Longer work → Glue, ECS/Fargate, Step Functions |
| **Ephemeral storage (/tmp)** | 512 MB – 10 GB | Temporary large files |
| **Reserved concurrency** | Guarantees **and caps** concurrency for a function | Protect a downstream DB from too many connections; ensure critical function always has capacity |
| **Provisioned concurrency** | Pre-initialized environments | Eliminate **cold starts** for latency-sensitive APIs |
| **Account concurrency** | Regional quota (1,000 default, can be raised) | Throttling across all functions |
| **Layers** | Shared libraries/dependencies | Reuse pandas/pyarrow across functions |
| **Architecture** | x86_64 or **arm64 (Graviton)** | Better price/performance |
| **VPC** | Needed to reach private resources (RDS, Elastic File System (EFS)) | Internet access then requires a NAT gateway (or VPC endpoints for AWS services) |

### Languages and frameworks (skill 1.4.3)

You need **concepts, not exact syntax**: Python (PySpark, pandas, boto3), **SQL** (most important), Scala/Java (Spark, Flink, Kafka), R (statistics), Bash/PowerShell (automation and scripts).

**SQL you should be fluent in:** `JOIN` types, `GROUP BY`/`HAVING`, window functions (`ROW_NUMBER() OVER (PARTITION BY … ORDER BY …)` for deduplication, `LAG`/`LEAD`, running totals), Common Table Expressions (CTEs) (`WITH`), `CASE`, `MERGE`/upsert, `CREATE VIEW`/materialized views.

### Software engineering best practices (skill 1.4.4)

- **Version control:** Git for all ETL code, SQL, DAGs, IaC. Branches + pull requests + code review. Know `clone`, `commit`, `push`, `pull`, `branch`, `merge`, `rebase` at a concept level.
- **Testing:** unit tests for transform functions (pytest; Glue offers a local Docker image for testing jobs), integration tests on sample data, **data quality tests** as pipeline gates.
- **Logging:** structured logs to CloudWatch Logs; Glue continuous logging; Spark event logs for the Spark UI.
- **Monitoring:** CloudWatch metrics and alarms, job run insights, dashboards (details in Domain 3).

### IaC: CloudFormation, CDK, SAM (skills 1.4.5, 1.4.6, 1.4.8)

| Tool | What it is | Choose when |
|---|---|---|
| **AWS CloudFormation** | Declarative YAML Ain't Markup Language (YAML)/JSON templates → stacks; change sets preview changes; drift detection; **StackSets** deploy across accounts/Regions | Standard repeatable infra for any AWS resource |
| **AWS CDK** | Define infra in Python/TypeScript/Java/etc. using constructs → synthesizes CloudFormation | Developers prefer real programming languages, loops, reusable components |
| **AWS SAM** | CloudFormation extension for serverless (`AWS::Serverless::Function`, `::StateMachine`, `::SimpleTable`, `::Api`); Command Line Interface (CLI): `sam build`, `sam deploy`, `sam local invoke` | **Package and deploy serverless pipelines** (Lambda + Step Functions + DynamoDB), test Lambda locally |

> Exam signal: "repeatable deployments across dev/test/prod" → IaC. "Serverless pipeline, local testing, package Lambda code" → **SAM**. "Developers want TypeScript/Python for infra" → **CDK**.

### Storage volumes in Lambda (skill 1.4.7)

| Option | Size | Persistence | Use |
|---|---|---|---|
| **/tmp (ephemeral)** | 512 MB – 10 GB | Per execution environment only; lost when it's recycled | Scratch space during an invocation |
| **Amazon EFS mount** | Elastic | **Persistent, shared** across invocations and functions | Large reference files, ML models, shared state, files > 10 GB total |
| **S3** | Unlimited | Persistent | Input/output objects (not mounted, accessed by API) |
| **Layers / container image** | Up to 250 MB unzipped / 10 GB image | Read-only | Libraries and static assets |

**EFS requirements:** the Lambda must be in the **same VPC** (subnets with mount targets), use an **EFS access point**, and the security groups must allow Network File System (NFS) (TCP 2049).

### CI/CD for data pipelines (skill 1.4.9)

```
Git push ──► CodePipeline
   ├─ Source: GitHub/GitLab/Bitbucket (via CodeConnections)
   ├─ Build: CodeBuild → lint, unit tests, package (sam build / cdk synth)
   ├─ Deploy to dev: CloudFormation/CDK/SAM
   ├─ Integration + data quality tests on sample data
   ├─ Manual approval
   └─ Deploy to prod
```

- **Continuous integration:** every commit is built and tested automatically.
- **Continuous delivery/deployment:** tested artifacts are released to environments automatically (with or without a manual approval gate).
- Keep environment-specific values in parameters (Systems Manager (SSM) Parameter Store), not in code.

### Distributed computing (skill 1.4.10)

- **Definition:** splitting work across many machines that work in parallel, then combining results.
- **Spark model:** a **driver** plans the job as a DAG of stages; **executors** on worker nodes process **partitions** of data in parallel; **shuffles** move data between nodes for joins/aggregations and are expensive; transformations are **lazy** and run when an action is called.
- **MapReduce:** map (process chunks in parallel) → shuffle/sort → reduce (aggregate).
- **Key ideas:** horizontal scaling (add nodes), data locality, partitioning, fault tolerance via re-computation or replication, data skew as the main performance killer.

### Data structures and algorithms (skill 1.4.11)

| Structure | Where it shows up in data engineering |
|---|---|
| **Graph** (nodes + edges) | Workflow DAGs (Airflow, Step Functions, Spark), data lineage, relationship data in **Amazon Neptune** |
| **Tree** | B-tree indexes in databases, nested JSON/Parquet schemas, decision logic |
| **Hash table** | Hash partitioning (Kinesis partition keys, Redshift KEY distribution), hash joins, deduplication |
| **Queue** | SQS, Kafka topics, buffering between stages |
| **Array/list** | Columnar storage, batches |

Know Big-O basics: a lookup in a hash table is O(1) on average; a sort is O(n log n); nested-loop joins are O(n×m), which is why engines prefer hash or broadcast joins.

---

## Gotchas and exam traps

- **"Near real time" + "deliver to S3/Redshift/OpenSearch" + "least operational overhead"** → **Firehose**, not KDS + custom Lambda consumers.
- **"Real time" + "multiple independent consumers" + "replay"** → **KDS** (add **enhanced fan-out** if consumers slow each other down).
- **"Kafka" anywhere in the question** → **MSK**.
- **Firehose has no replay.** If reprocessing matters, keep raw data in S3 or put KDS in front.
- **Throttling on one shard while overall throughput is low** → hot partition key, not "add more shards."
- **Lambda behind KDS needs more throughput without resharding** → raise **parallelization factor** (up to 10).
- **One bad record blocks a Kinesis shard** → **bisect batch on error** + max retries + on-failure destination.
- **"Convert streaming JSON to Parquet with no code"** → **Firehose record format conversion** (uses Glue table schema).
- **"Process only new data since the last run"** → **Glue job bookmarks**.
- **"Non-urgent nightly Glue job, cut cost"** → **Glue Flex**.
- **"Small dataset, simple Python transform"** → **Glue Python shell** or Lambda, not a Spark job.
- **"Many Lambdas exhaust RDS connections"** → **RDS Proxy** (and/or reserved concurrency).
- **"External system only allows known IPs"** → put Glue/Lambda in a VPC behind a **NAT gateway** and allowlist its **Elastic IP**.
- **Glue job can't connect to RDS in a VPC** → missing **self-referencing security group rule** or route.
- **DMS CDC from MySQL not capturing changes** → enable **binary logging with ROW format**.
- **DMS isn't a heavy ETL tool.** Land data in S3 and transform with Glue.
- **"SaaS source like Salesforce, no code"** → **AppFlow**, not a custom Lambda.
- **GZIP CSV files are not splittable** → one task per file; convert to Parquet for parallelism.
- **"Only Glue jobs/crawlers in the pipeline"** → **Glue workflows**. **"Existing Airflow DAGs"** → **MWAA**. **"Mixed AWS services, serverless"** → **Step Functions**.
- **Step Functions Express workflows max out at 5 minutes.** Long ETL needs **Standard**.
- **"Large volume of text to classify/summarize with an LLM, cost-sensitive"** → **Bedrock batch inference**, not per-record on-demand calls.
- **"Package and deploy Lambda + Step Functions + DynamoDB, test locally"** → **AWS SAM**.
- **"Shared, persistent file storage for Lambda"** → **EFS mount** (Lambda in the VPC), not /tmp.

---

## Quick-recall summary

- Domain weight **34%**. Four tasks: ingestion (1.1), transformation (1.2), orchestration (1.3), programming (1.4).
- KDS shard: **1 MB/s or 1,000 rec/s in, 2 MB/s out**; retention up to **365 days**; provisioned vs **on-demand**; **enhanced fan-out** = 2 MB/s per consumer.
- Hot shard = bad partition key. Rising **IteratorAge** = consumers behind.
- **Firehose**: buffered near real time; Parquet/ORC conversion; Lambda transform; dynamic partitioning; Redshift via S3 + COPY; Iceberg destination; **no replay**.
- **MSK** for Kafka; **MSK Connect** for connectors; **MSK Serverless** for no sizing.
- **DynamoDB Streams** = 24 h CDC. **KDS for DynamoDB** = longer retention.
- Batch: **DMS** (DB, CDC), **AppFlow** (SaaS), **DataSync** (file shares), **Transfer Family** (SFTP), **Snow** (offline), **Data Exchange** (third-party data), **zero-ETL** (DB → Redshift).
- Schedules: **EventBridge Scheduler**, Glue triggers, crawler schedules, MWAA. Events: **S3 Event Notifications** (simple) vs **EventBridge** (filtering, many targets, replay).
- Lambda + Kinesis: batch size, batch window, **parallelization factor (≤10)**, bisect on error, max retries/age, on-failure destination, tumbling windows.
- Allowlist outbound IPs with a **NAT gateway Elastic IP**.
- Throttling: backoff + jitter, better keys, on-demand capacity, batching, **RDS Proxy**, SQS buffering.
- Replay: **KDS/MSK retention, raw S3 zone, EventBridge archive, reset bookmarks**.
- Stateless = per record. Stateful = windows/dedup/joins → **Flink**, Glue streaming checkpoints, Lambda tumbling windows.
- Transform service picks: **Glue** (serverless Spark), **DataBrew** (no code), **EMR** (full control, Spot task nodes), **Lambda** (small, ≤15 min), **Athena CTAS** (SQL on S3), **Redshift** (ELT), **Flink** (streams), **ECS/EKS/Batch** (containers).
- Glue: DynamicFrame, **bookmarks**, **pushdown predicates**, worker types, Auto Scaling, **Flex**, Python shell.
- Formats: **Parquet** = default analytics answer; Avro = streaming/schema evolution; GZIP text = not splittable.
- Troubleshoot: skew → salt/broadcast; small files → group/compact; partitions missing → Metastore Consistency Check (MSCK) REPAIR / projection; COPY errors → `STL_LOAD_ERRORS`.
- Data APIs: API Gateway + Lambda + DynamoDB / **Redshift Data API** / Athena; AppSync for GraphQL.
- 3 Vs: volume, velocity, variety (structured, semi-structured, unstructured).
- LLMs: **Bedrock** via Lambda/Glue/Step Functions; **batch inference** for bulk; Redshift ML for SQL; Comprehend for standard NLP; mask PII first.
- Orchestration: **Step Functions** (Standard ≤1 yr / Express ≤5 min, Retry/Catch, Distributed Map), **MWAA** (Airflow), **Glue workflows** (Glue only), **EventBridge** (start).
- Alerts: **SNS** push; **SQS** buffer + DLQ.
- Lambda: memory 128 MB–10 GB (CPU scales), **15 min**, /tmp up to 10 GB, **reserved** (cap) vs **provisioned** (no cold start) concurrency, **EFS** for shared persistent storage.
- IaC: **CloudFormation** (templates, StackSets), **CDK** (code → CloudFormation), **SAM** (serverless + local testing).
- CI/CD: CodePipeline + CodeBuild + IaC deploy, tests and approval gates.
- Distributed computing: driver/executors, partitions, shuffles, lazy evaluation, skew.
- Data structures: graphs (DAGs, lineage, Neptune), trees (indexes, nested data), hash (partitioning, joins).
