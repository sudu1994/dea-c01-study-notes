# Domain 3: Data Operations and Support (22%)

> **About 11 of the 50 scored questions.**
>
> This domain is about running pipelines in production: automating processing with Amazon Web Services (AWS) services and Software Development Kits (SDKs), analyzing data with Structured Query Language (SQL) and visualization tools, monitoring/logging/troubleshooting pipelines, and making sure the data is correct (data quality, consistency, sampling, skew).

## Table of contents

- [Exam tasks and skills](#exam-tasks-and-skills)
- [Task 3.1: Automate data processing by using AWS services](#task-31-automate-data-processing-by-using-aws-services)
- [Task 3.2: Analyze data by using AWS services](#task-32-analyze-data-by-using-aws-services)
- [Task 3.3: Maintain and monitor data pipelines](#task-33-maintain-and-monitor-data-pipelines)
- [Task 3.4: Ensure data quality](#task-34-ensure-data-quality)
- [Gotchas and exam traps](#gotchas-and-exam-traps)
- [Quick-recall summary](#quick-recall-summary)

## Exam tasks and skills

> Summarized from the official AWS Certified Data Engineer – Associate (DEA-C01) exam guide (v1.1). Exact wording: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain3.html

### Task 3.1: Automate data processing by using AWS services
- **3.1.1** Orchestrate pipelines (Managed Workflows for Apache Airflow (MWAA), Step Functions).
- **3.1.2** Troubleshoot Amazon managed workflows.
- **3.1.3** Call SDKs to use AWS features from code.
- **3.1.4** Use service features to process data (Elastic MapReduce (EMR), Redshift, Glue).
- **3.1.5** Consume and maintain data Application Programming Interfaces (APIs).
- **3.1.6** Prepare data for transformation (Glue DataBrew, 🆕 SageMaker Unified Studio).
- **3.1.7** Query data (Athena).
- **3.1.8** Automate processing with Lambda.
- **3.1.9** Manage events and schedulers (EventBridge).

### Task 3.2: Analyze data by using AWS services
- **3.2.1** Visualize data (DataBrew, QuickSight).
- **3.2.2** Verify and clean data (Lambda, Athena, QuickSight, Jupyter, SageMaker Data Wrangler).
- **3.2.3** Use SQL in **Redshift and Athena** to query and create views.
- **3.2.4** Explore data with Athena notebooks on Apache Spark.
- **3.2.5** Describe provisioned vs serverless trade-offs.
- **3.2.6** Define aggregation, rolling averages, grouping, pivoting.

### Task 3.3: Maintain and monitor data pipelines
- **3.3.1** Extract logs for audits.
- **3.3.2** Deploy logging/monitoring for auditing and traceability.
- **3.3.3** Send alerts from monitoring.
- **3.3.4** Troubleshoot performance issues.
- **3.3.5** Track Application Programming Interface (API) calls with CloudTrail.
- **3.3.6** Troubleshoot and maintain pipelines (Glue, EMR).
- **3.3.7** Log application data with CloudWatch Logs (configuration and automation).
- **3.3.8** Analyze logs (Athena, EMR, OpenSearch, CloudWatch Logs Insights, big data app logs).

### Task 3.4: Ensure data quality
- **3.4.1** Run quality checks during processing (e.g., empty fields).
- **3.4.2** Define data quality rules (DataBrew).
- **3.4.3** Investigate data consistency (DataBrew).
- **3.4.4** Describe data sampling techniques.
- **3.4.5** Implement mechanisms for data skew.

---

## Task 3.1: Automate data processing by using AWS services

### Orchestration in operations (skill 3.1.1)

Domain 1 covers *choosing* an orchestrator. Here the focus is *running* them.

| | Step Functions | Amazon MWAA |
|---|---|---|
| Definition | JavaScript Object Notation (JSON)/YAML Ain't Markup Language (YAML) (Amazon States Language), visual Workflow Studio | Python Directed Acyclic Graph (DAG) files in Simple Storage Service (S3) |
| Waiting for jobs | `.sync` integration (e.g., `glue:startJobRun.sync`) | Operators/sensors (GlueJobOperator, S3KeySensor) |
| Error handling | `Retry` (interval, backoff rate, max attempts) and `Catch` per state | Task `retries`, `retry_delay`, `on_failure_callback` |
| Scaling | Automatic | Environment class + min/max workers (auto scales workers) |
| Pricing | Per state transition (Standard) or per request/duration (Express) | Per environment-hour + workers |
| Pick for | AWS-native, serverless, low ops | Existing Airflow code, complex dependencies, open-source operators |

### Troubleshooting managed workflows (skill 3.1.2)

**Step Functions:**
- **Execution history** in the console shows every state's input, output, and error (e.g., `States.TaskFailed`, `States.Timeout`, `States.Permissions`).
- Enable **CloudWatch Logs** for the state machine (`ALL`, `ERROR`, or `FATAL`). **Express workflows only keep history in CloudWatch Logs**, so you must enable logging to debug them.
- **X-Ray** tracing shows latency across services.
- Common fixes: missing Identity and Access Management (IAM) permissions on the state machine role, `TimeoutSeconds`/`HeartbeatSeconds` too low, payload over the 256 KB limit (pass S3 references instead), no `Retry` for transient errors.

**MWAA:**
- Logs in CloudWatch: **DAG processing, scheduler, web server, worker, task** logs. Turn on the levels you need.
- **DAG doesn't appear** → Python import error (check DAG processing logs), wrong S3 path, or a `requirements.txt` dependency that failed to install (check the environment's requirements install log).
- **Tasks queued but not running** → too few workers / environment class too small, or pool/concurrency limits.
- **Can't reach AWS services** → execution role permissions, or a private network with no Network Address Translation (NAT)/VPC endpoints.
- Update requirements/plugins by uploading new versions to S3 and updating the environment.

### Calling SDKs (skill 3.1.3)

- **AWS SDKs** (boto3 for Python, SDKs for Java, JavaScript, Go…) call AWS APIs from code (Lambda, Glue, containers, notebooks).
- **Credentials** come from the **IAM role** of the compute (Lambda execution role, Glue job role, Elastic Compute Cloud (EC2) instance profile). Never hardcode keys.
- **Paginators** for list operations that return pages (`list_objects_v2`, `get_query_results`).
- **Waiters** to wait for a state (e.g., wait until a Redshift cluster is available).
- **Retries**: SDKs retry throttling errors automatically. Configure `standard` or `adaptive` retry mode and max attempts.
- **Asynchronous APIs** you must poll: Athena (`start_query_execution` → `get_query_execution` → `get_query_results`), **Redshift Data API** (`execute_statement` → `describe_statement` → `get_statement_result`), Glue (`start_job_run` → `get_job_run`).

### Using service features to process data (skill 3.1.4)

| Service | Processing features worth knowing |
|---|---|
| **Glue** | Built-in transforms (ApplyMapping, Filter, Join, DropNullFields, Relationalize), **FindMatches Machine Learning (ML) transform** (fuzzy deduplication/record matching without exact keys), sensitive data detection, Data Quality, job bookmarks |
| **EMR** | **Steps** (submit Spark/Hive jobs to a cluster), bootstrap actions, EMR Serverless applications, EMR Studio notebooks |
| **Redshift** | Stored procedures, materialized views, `MERGE`, scheduled queries, Redshift ML (`CREATE MODEL`), streaming ingestion, user-defined functions (SQL/Lambda) |

### Consuming and maintaining data APIs (skill 3.1.5)

Maintaining data APIs means operating them, not just creating them:
- **Versioning** (`/v1/`, `/v2/` paths or API Gateway stages) so changes don't break consumers.
- **Throttling and quotas** (API Gateway usage plans and API keys).
- **Caching** (API Gateway cache) for repeated queries.
- **Monitoring**: API Gateway CloudWatch metrics (`4XXError`, `5XXError`, `Latency`, `Count`), access logs, X-Ray.
- **Security**: IAM, Cognito, or Lambda authorizers.
- **Pagination** and consistent response formats.

### Preparing data for transformation (skill 3.1.6)

**AWS Glue DataBrew** (no-code data prep):
- **Datasets** (S3, Glue Catalog, Redshift, Relational Database Service (RDS), Snowflake…) → **projects** (interactive session on a sample) → **recipes** (saved list of transform steps) → **recipe jobs** (run the recipe on the full dataset, output to S3) and **profile jobs** (statistics and quality).
- 250+ transforms: remove duplicates, fill/flag missing values, split/merge columns, standardize formats, pivot/unpivot, mask/redact/encrypt Personally Identifiable Information (PII), join datasets.
- Best for **analysts or data stewards who don't write code**.

🆕 **Amazon SageMaker Unified Studio**:
- A **single web environment** for data and Artificial Intelligence (AI) work: SQL query editor (Athena and Redshift), Jupyter notebooks (Spark, Python), **visual Extract, Transform, Load (ETL)** (Glue), data prep, model building, generative AI app building with Bedrock, plus the **SageMaker Catalog**.
- Organized by **domains → domain units → projects** (Domain 4 covers this). A project gives a team shared data, compute, and permissions.
- Choose it when the scenario wants **one governed workspace** where engineers, analysts, and data scientists collaborate on the same data.

### Querying data with Athena (skill 3.1.7)

- Standard SQL (Trino engine) over the Glue Data Catalog; results written to an S3 location (set per **workgroup**).
- **Workgroups**: separate teams/apps, enforce result location and encryption, **per-query and per-workgroup data scan limits**, cost tracking with tags.
- **Saved queries**, **prepared statements** (parameterized queries; also help prevent SQL injection), **views**.
- **CREATE TABLE AS SELECT (CTAS)** and `INSERT INTO` to create transformed and partitioned tables.
- **Query result reuse** avoids rescanning for repeated identical queries.
- **Provisioned capacity** (reserved Data Processing Units (DPUs)) for predictable concurrency instead of per-TB pricing.

### Automating with Lambda (skill 3.1.8)

Typical automation patterns:
- **S3 object created → Lambda**: validate the file, convert small files, start a Glue job / Step Functions execution.
- **Scheduled Lambda** (EventBridge Scheduler): call an API, run housekeeping (e.g., refresh a materialized view through the Redshift Data API).
- **Stream processing**: KDS/DynamoDB Streams/SQS → Lambda (see the event source mapping settings in Domain 1).
- **Glue between steps** inside Step Functions.
- Keep functions small, idempotent, with Dead-Letter Queues (DLQs)/on-failure destinations and structured logging.

### Managing events and schedulers (skill 3.1.9)

**Amazon EventBridge building blocks:**

| Component | Purpose |
|---|---|
| **Event buses** | Default bus (AWS service events), custom buses (your apps), partner buses (Software as a Service (SaaS)) |
| **Rules** | Match events by **event pattern** (source, detail-type, fields) → up to 5 targets per rule |
| **Targets** | Lambda, Step Functions, Glue workflows, Kinesis, Simple Queue Service (SQS), Simple Notification Service (SNS), Elastic Container Service (ECS) tasks, API destinations… |
| **Scheduler** | Cron/rate/one-time schedules at large scale, with time zones, flexible windows, retries, Dead-Letter Queue (DLQ) |
| **Archive & replay** | Store events and replay them later |
| **Cross-account** | Send events to a bus in another account (central monitoring) |
| **Input transformer** | Reshape the event before sending it to the target |

Data-pipeline events you'll see: **Glue Job State Change**, **Glue Crawler State Change**, **Glue Data Quality evaluation results**, **EMR step status change**, **Step Functions execution status change**, **S3 Object Created**, **Redshift Data API statement status**.

---

## Task 3.2: Analyze data by using AWS services

### Visualizing data (skill 3.2.1)

**Amazon QuickSight:**
- Serverless Business Intelligence (BI): dashboards, analyses, paginated reports, **embedded dashboards** in apps.
- **Super-fast, Parallel, In-memory Calculation Engine (SPICE)**: in-memory engine. Import data for fast, scalable dashboards; schedule full or **incremental refreshes**. **Direct query** hits the source live (always fresh, slower, loads the source).
- Data sources: Athena, Redshift, RDS/Aurora, S3, OpenSearch, Snowflake, SaaS…
- **Row-level security (RLS)** and column-level security per user/group.
- **Amazon Q in QuickSight**: ask questions in natural language, build visuals and data stories.
- Licensing by authors and readers.

**DataBrew visuals:** profile results show column distributions, missing values, outliers, correlations, which is quick visual data exploration before transformation.

### Verifying and cleaning data (skill 3.2.2)

| Tool | Use |
|---|---|
| **Athena SQL** | Count nulls, duplicates (`GROUP BY … HAVING COUNT(*) > 1`), out-of-range values, compare row counts |
| **Lambda** | Validate each incoming file/record (schema, required fields) and quarantine bad ones |
| **QuickSight** | Spot anomalies visually (spikes, gaps) |
| **Jupyter notebooks** (SageMaker, EMR Studio, Athena Spark, Unified Studio) | Interactive exploration with pandas/PySpark |
| **SageMaker Data Wrangler** (in SageMaker Canvas) | Visual data prep for ML: 300+ transforms, data quality and insights report, export to pipelines |
| **DataBrew / Glue Data Quality** | Rule-based profiling and validation (Task 3.4) |

### SQL in Redshift and Athena (skill 3.2.3)

- Both are American National Standards Institute (ANSI) SQL engines: joins, Common Table Expressions (CTEs), window functions, `CASE`, aggregate functions.
- **Views**: saved queries, no stored data, always current.
- **Materialized views**: store results for speed (Redshift; Athena doesn't have classic materialized views over Glue tables, so use CTAS for that).
- **Redshift late-binding views** (`CREATE VIEW … WITH NO SCHEMA BINDING`): not bound to underlying objects, so you can drop/recreate tables without breaking the view. **Required for views that reference Spectrum external tables.**
- **Athena views** are stored in the Glue Data Catalog and can be queried by other Athena users.
- Know `CREATE TABLE AS` in both, `UNLOAD` in both (Athena also has `UNLOAD` to write query results in Parquet/Optimized Row Columnar (ORC)/JSON).

### Athena notebooks with Apache Spark (skill 3.2.4)

- **Amazon Athena for Apache Spark**: interactive **Jupyter-compatible notebooks** in the Athena console; a Spark session starts in about a second, with no clusters to configure.
- Uses a **Spark-enabled workgroup**; billed by **Data Processing Unit hour (DPU-hour)** of session use.
- Use for exploratory PySpark on lake data (complex transformations, Python libraries) when SQL alone isn't enough.

### Provisioned vs serverless trade-offs (skill 3.2.5)

| | Provisioned (Redshift RA3 cluster, EMR on EC2, Managed Streaming for Apache Kafka (MSK) provisioned, DynamoDB provisioned, Kinesis Data Streams (KDS) provisioned) | Serverless (Redshift Serverless, Athena, EMR Serverless, Glue, MSK Serverless, DynamoDB on-demand, KDS on-demand, Lambda) |
|---|---|---|
| Cost model | Pay for capacity whether used or not; **cheaper at steady, high utilization** (and with reservations) | Pay per use; **cheaper for spiky, intermittent, unpredictable** workloads |
| Operations | You size, scale, sometimes patch | No capacity planning |
| Performance control | Full tuning (instance types, configs) | Fewer knobs; possible cold starts / scaling ramp |
| Predictability | Predictable cost and performance | Cost varies with usage |

> Rule: **steady 24/7 load** → provisioned (+ Reserved Instances/Savings Plans). **Unpredictable or occasional load, least ops** → serverless.

### Aggregation, rolling averages, grouping, pivoting (skill 3.2.6)

```sql
-- Aggregation + grouping
SELECT region, product, SUM(sales) AS total_sales, COUNT(*) AS orders
FROM sales
GROUP BY region, product
HAVING SUM(sales) > 10000;

-- Subtotals and grand totals in one query
SELECT region, product, SUM(sales)
FROM sales
GROUP BY ROLLUP (region, product);   -- also CUBE, GROUPING SETS

-- 7-day rolling (moving) average with a window function
SELECT sale_date,
       daily_sales,
       AVG(daily_sales) OVER (ORDER BY sale_date
                              ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS avg_7d
FROM daily_totals;

-- Pivot rows into columns (portable CASE method)
SELECT product,
       SUM(CASE WHEN quarter = 'Q1' THEN sales END) AS q1,
       SUM(CASE WHEN quarter = 'Q2' THEN sales END) AS q2
FROM sales
GROUP BY product;
-- Redshift also supports PIVOT / UNPIVOT syntax.

-- Deduplicate: keep the latest row per key
SELECT * FROM (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY order_id ORDER BY updated_at DESC) AS rn
  FROM orders) t
WHERE rn = 1;
```

| Term | Meaning |
|---|---|
| **Aggregation** | Summarizing many rows into one value (SUM, AVG, COUNT, MIN, MAX) |
| **Grouping** | Aggregating per category (`GROUP BY`), filtering groups with `HAVING` |
| **Rolling average** | Average over a moving window of rows/time, which smooths fluctuations |
| **Pivoting** | Turning row values into columns (unpivot does the reverse) |

---

## Task 3.3: Maintain and monitor data pipelines

### Logging and monitoring building blocks (skills 3.3.1, 3.3.2, 3.3.5, 3.3.7)

| Service | What it records | Exam use |
|---|---|---|
| **AWS CloudTrail** | **API calls**: who, what, when, from where. **Management events** on by default (90-day event history); **data events** (S3 object-level, Lambda invokes, DynamoDB items…) must be enabled and cost extra | Audits: "who deleted the table / changed the bucket policy / ran the Glue job?" Use **trails** to S3 for long-term retention, an **organization trail** for all accounts, **log file integrity validation** to prove logs weren't altered |
| **CloudTrail Lake** | Managed event data store with SQL queries over CloudTrail (and other) events, long retention | Centralized audit queries without building Athena tables |
| **Amazon CloudWatch Logs** | Application and service logs (Lambda, Glue, EMR, MWAA, Step Functions, API Gateway, Virtual Private Cloud (VPC) Flow Logs) | Debugging, metric filters, subscriptions |
| **Amazon CloudWatch metrics + alarms** | Numeric time series (Glue job metrics, KDS IteratorAge, Redshift Central Processing Unit (CPU), DynamoDB throttles) | Alerts and dashboards |
| **AWS Config** | Resource configuration history and compliance | "What changed on this bucket/cluster?" (Domain 4) |
| **Redshift audit logging** | **Connection log**, **user log**, **user activity log** (every query) to S3 or CloudWatch Logs | Database-level audit |
| **S3 server access logs** | Requests to a bucket (best effort) | Access analysis, cheaper than data events for high volume |
| **EMR logs** | Step, application (Yet Another Resource Negotiator (YARN), Spark) and node logs archived to S3 | Debugging cluster jobs |

**CloudWatch Logs configuration and automation (skill 3.3.7):**
- **Log groups** (per app/job) and **log streams**; set **retention** per log group (never expire by default, which costs money).
- **Metric filters**: turn log patterns (e.g., `"ERROR"`) into metrics → alarms.
- **Subscription filters**: stream logs in real time to Lambda, **Firehose** (→ S3/OpenSearch), Kinesis, or OpenSearch.
- **Export** to S3 for archive and Athena analysis.
- **CloudWatch agent** for EC2/on-prem log collection; embedded metric format for custom metrics from logs.
- **Glue continuous logging** streams driver/executor logs in real time during a run.
- Encrypt log groups with Key Management Service (KMS). Automate log group creation and retention with Infrastructure as Code (IaC).

### Alerts (skill 3.3.3)

```
Glue job FAILED ──► EventBridge rule (Glue Job State Change, state=FAILED) ──► SNS topic ──► email / chat / on-call
KDS IteratorAge > 60s ──► CloudWatch alarm ──► SNS
Log pattern "OutOfMemoryError" ──► metric filter ──► alarm ──► SNS
Step Functions Catch ──► SNS publish task
Glue Data Quality score < threshold ──► EventBridge ──► SNS / Lambda (quarantine data)
```

### Troubleshooting performance (skills 3.3.4, 3.3.6)

**AWS Glue:**
- **Job run insights**: points to the failing line and suggests causes.
- **Glue metrics / observability metrics** in CloudWatch: worker utilization, memory, shuffle, skew. Look for idle executors (over-provisioned) or memory near limit.
- **Spark User Interface (UI)** (enable event logs to S3): stages, tasks, skew (one task far longer than the rest), shuffle spill.
- Typical fixes: bigger worker types, Auto Scaling, repartition/salting, pushdown predicates, file grouping, bookmarks, fewer User-Defined Functions (UDFs).

**Amazon EMR:**
- Logs in S3 (enable at cluster creation), Spark History Server, YARN ResourceManager UI, CloudWatch EMR metrics (`YARNMemoryAvailablePercentage`, `ContainerPending`, `HDFSUtilization`).
- Fixes: managed scaling, more/larger task nodes, tune executors/partitions, move data to S3 to decouple.
- Spot interruptions: use Spot only for task nodes; instance fleets with diversified types.

**Amazon Redshift:**
- **`EXPLAIN`** plan: watch for `DS_BCAST_INNER` / `DS_DIST_BOTH` (data redistribution → poor dist keys), nested loop joins (missing join condition).
- System views: `SYS_QUERY_HISTORY`, `STL_ALERT_EVENT_LOG` (missing stats, nested loops), `SVL_QUERY_SUMMARY` (disk-based steps = not enough memory), `SVV_TABLE_INFO` (skew, unsorted %, stats_off).
- Fixes: better dist/sort keys, `ANALYZE` (stats), `VACUUM` (sort/reclaim), Workload Management (WLM) queues/priorities, concurrency scaling, materialized views, Advisor recommendations.

**Amazon Athena:**
- Use query stats (data scanned, planning vs execution time) and `EXPLAIN ANALYZE`.
- Fixes: partitions/projection, Parquet + compression, fewer and larger files, select only needed columns, put the **larger table on the left side of a JOIN**, avoid huge `ORDER BY` without `LIMIT`, use approximate functions (`approx_distinct`).

**Kinesis / Lambda:** rising `IteratorAge` → consumers slow (increase parallelization factor, shards, enhanced fan-out, batch size). `ThrottledRecords` → hot shards.

### Analyzing logs (skill 3.3.8)

| Tool | Best for |
|---|---|
| **CloudWatch Logs Insights** | Fast interactive queries on CloudWatch log groups (`fields`, `filter`, `stats`, `sort`); no setup |
| **Athena** | SQL on logs in S3 (CloudTrail, VPC Flow Logs, Application Load Balancer (ALB), S3 access logs). Use partition projection for date-partitioned logs. Cheap at scale. |
| **Amazon OpenSearch Service** | Near-real-time log analytics, full-text search, dashboards (OpenSearch Dashboards); feed via Firehose or subscription filters |
| **Amazon EMR** | **Very large volumes** of logs needing custom Spark processing |
| **CloudTrail Lake** | SQL over CloudTrail events without managing tables |

---

## Task 3.4: Ensure data quality

### Data quality dimensions

| Dimension | Question | Example check |
|---|---|---|
| **Completeness** | Is anything missing? | `email` not null for 99% of rows |
| **Accuracy/validity** | Do values follow rules? | `age` between 0 and 120; email matches a regex |
| **Consistency** | Do related datasets agree? | Row counts source vs target; totals match |
| **Uniqueness** | Are there duplicates? | `order_id` is unique |
| **Timeliness/freshness** | Is the data recent enough? | Latest partition is less than 1 day old |
| **Integrity** | Do references resolve? | Every `order.customer_id` exists in `customers` |

### Quality checks during processing (skills 3.4.1, 3.4.2)

**AWS Glue Data Quality** (built on the open-source **Deequ** library):
- Rules written in **DQDL (Data Quality Definition Language)**:

```
Rules = [
    IsComplete "customer_id",
    IsUnique "order_id",
    Completeness "email" > 0.95,
    ColumnValues "age" between 0 and 120,
    ColumnValues "status" in ["NEW", "SHIPPED", "CANCELLED"],
    RowCount > 1000,
    DataFreshness "order_date" <= 24 hours,
    ReferentialIntegrity "customer_id" "customers.id" = 1.0
]
```

- **Rule recommendations**: Glue profiles the data and suggests rules.
- Two places to run it: **on Data Catalog tables** (data at rest, scheduled) or **inside Glue ETL jobs** with the Evaluate Data Quality transform (data in transit).
- **Actions**: fail the job, or **route bad records** to a quarantine location while good records continue; publish results to **CloudWatch** and **EventBridge**.
- **Anomaly detection**: learns normal patterns (e.g., row counts) and flags unusual values.

**AWS Glue DataBrew data quality:**
- **Data quality rulesets** attached to a dataset (e.g., "no more than 5% missing values in `email`", "`price` > 0", duplicate row checks).
- Rules are evaluated during **profile jobs**. Results show pass/fail per rule; notify through EventBridge.
- Better for analysts and no-code teams. Glue Data Quality is better for coded pipelines.

**Other options:** custom checks in Lambda or Spark (e.g., `df.filter(col("x").isNull()).count()`), Athena validation queries in a Step Functions step, **Database Migration Service (DMS) data validation** for migrations.

### Investigating data consistency (skill 3.4.3)

- **DataBrew profile jobs**: per-column statistics (distinct values, missing %, min/max/mean, outliers, value distribution, correlations) and duplicate rows. Comparing profiles between runs or sources shows drift and inconsistencies.
- Reconcile **row counts and checksums/aggregates** between source and target after each load.
- Check **referential integrity** across tables.
- Look for **format inconsistencies** (date formats, units, casing, encodings) and standardize them in recipes or ETL.
- **Glue FindMatches** finds duplicates that don't share an exact key ("Jon Smith" vs "John Smith").

### Data sampling techniques (skill 3.4.4)

Sampling = checking or exploring a subset instead of all data (faster, cheaper).

| Technique | How | When |
|---|---|---|
| **Simple random** | Every row has equal chance | General profiling |
| **Systematic** | Every k-th row | Ordered data with no periodic pattern |
| **Stratified** | Random sample **within each group** proportional to its size | Keep representation of small groups (regions, classes) |
| **Cluster** | Randomly pick whole groups (e.g., some partitions/files) | Data naturally split into partitions |
| **Reservoir** | Fixed-size random sample from a stream of unknown length | Streaming data |
| **First N rows** | Take the top of the dataset | Quick look, not representative (DataBrew default sample) |

AWS examples: DataBrew project sample settings (first N, random N, last N), Athena `TABLESAMPLE BERNOULLI (10)` or `SYSTEM`, Spark `df.sample(fraction=0.1)`, Spark `sampleBy` for stratified sampling.

### Handling data skew (skill 3.4.5)

**Skew** = data is unevenly distributed, so one partition/shard/slice/worker does most of the work while others sit idle.

| Where | Symptom | Mechanism |
|---|---|---|
| **Spark (Glue/EMR)** | One task runs much longer; executor Out Of Memory (OOM) | **Salting** (append a random number to hot keys, aggregate twice), **repartition** on a better key, **broadcast join** small tables, **Adaptive Query Execution** skew-join handling (Spark 3), filter out null/default keys before joins |
| **Redshift** | Slices with far more rows (`SVV_TABLE_INFO.skew_rows`) | Choose a high-cardinality `DISTKEY`, or `EVEN`/`AUTO` |
| **Kinesis / DynamoDB** | Hot shard/partition, throttling | High-cardinality partition key, random suffixes (write sharding) |
| **S3 partitions** | One partition much bigger than others | Rethink partition columns; add bucketing |

---

## Gotchas and exam traps

- **Express Step Functions** have no execution history in the console. **Enable CloudWatch Logs** to debug.
- **MWAA DAG not showing** → import error or failed `requirements.txt` install. Check the DAG processing/requirements logs.
- **Async APIs**: Athena and Redshift Data API must be **polled** for completion.
- **Fuzzy deduplication without a common key** → **Glue FindMatches**.
- **No-code data prep for analysts** → **DataBrew**. **One governed workspace for data + AI teams** → **SageMaker Unified Studio**.
- **Limit how much data a team's Athena queries can scan** → **workgroup data usage controls**.
- **Dashboards slow and hammering the database** → QuickSight **SPICE** with scheduled/incremental refresh.
- **Restrict dashboard rows per user** → QuickSight **row-level security**.
- **Redshift view over Spectrum tables** must be a **late-binding view**.
- **Interactive PySpark exploration without clusters** → **Athena for Apache Spark** notebooks.
- **Steady 24/7 workload** → provisioned + reservations. **Spiky/occasional** → serverless.
- **"Who deleted/changed X?"** → **CloudTrail** (S3 object-level needs **data events**). **"What did the config look like before?"** → **AWS Config**.
- **Query CloudTrail events with SQL, no table setup** → **CloudTrail Lake**. **Logs already in S3** → **Athena**.
- **Quick ad-hoc search in Lambda/Glue logs** → **CloudWatch Logs Insights**.
- **Near-real-time log search + dashboards** → **OpenSearch** (via Firehose or subscription filter).
- **Huge log volumes needing custom processing** → **EMR**.
- **Turn "ERROR" log lines into an alert** → **metric filter + alarm + SNS**.
- **Glue job failure notification** → **EventBridge rule (Glue Job State Change) → SNS**.
- **Log groups never expire by default** → set retention.
- **Redshift `DS_BCAST_INNER` / `DS_DIST_BOTH` in EXPLAIN** → bad distribution keys.
- **Fail the job or quarantine bad rows based on rules in a Glue pipeline** → **Glue Data Quality** (Evaluate Data Quality transform).
- **One Spark task takes forever** → skew → **salting / broadcast join / Adaptive Query Execution (AQE)**.
- **Representative sample that keeps small groups** → **stratified sampling**.

---

## Quick-recall summary

- Domain weight **22%**. Tasks: automate (3.1), analyze (3.2), maintain/monitor (3.3), data quality (3.4).
- Step Functions: `.sync`, Retry/Catch, execution history, **CloudWatch Logs required for Express**, X-Ray. MWAA: Directed Acyclic Graphs (DAGs) + requirements in S3, CloudWatch logs per component, worker scaling.
- SDKs: role-based credentials, paginators, waiters, retry modes; **poll** Athena/Redshift Data API/Glue runs.
- Service features: Glue transforms + **FindMatches**; EMR steps; Redshift stored procedures, Materialized Views (MVs), MERGE, scheduled queries.
- Data APIs: version, throttle, cache, monitor, secure.
- Prep: **DataBrew** (recipes, profile jobs, no code), **SageMaker Unified Studio** (one workspace: SQL, notebooks, visual ETL, catalog).
- **Athena**: workgroups (scan limits, result encryption), prepared statements, views, CTAS, UNLOAD, result reuse, provisioned capacity; **Athena for Spark** notebooks (Data Processing Unit hours (DPU-hours)).
- **EventBridge**: buses, rules/patterns, targets, **Scheduler**, archive/replay, cross-account; Glue/EMR/Step Functions state-change events.
- **QuickSight**: SPICE vs direct query, RLS, embedded dashboards, Amazon Q.
- Clean/verify: Athena SQL, Lambda, notebooks, **Data Wrangler**, DataBrew.
- SQL: views, materialized views, **late-binding views** (required with Spectrum), ROLLUP/CUBE, window functions (rolling average), pivot via CASE or PIVOT, `ROW_NUMBER` dedup.
- Provisioned = steady and cheaper at scale. Serverless = spiky, least ops.
- Audit: **CloudTrail** (management on by default, data events opt-in, 90-day history, trails, org trails, integrity validation), **CloudTrail Lake** (SQL), Redshift audit logs, S3 access logs.
- **CloudWatch Logs**: retention, **metric filters**, **subscription filters** (→ Firehose/Lambda/OpenSearch), export to S3, Logs Insights.
- Alerts: EventBridge/alarms → **SNS**.
- Performance: Glue job run insights + Spark UI; EMR logs + YARN metrics; Redshift EXPLAIN + system views + ANALYZE/VACUUM; Athena partitions/columnar/join order.
- Log analytics: **Logs Insights** (quick), **Athena** (S3, cheap), **OpenSearch** (real-time search), **EMR** (huge volume).
- Data quality dimensions: completeness, validity, consistency, uniqueness, freshness, integrity.
- **Glue Data Quality**: DQDL rules, recommendations, catalog or in-job, fail or quarantine, CloudWatch/EventBridge, anomaly detection. **DataBrew**: rulesets + profile jobs.
- Sampling: random, systematic, **stratified**, cluster, reservoir; Athena `TABLESAMPLE`.
- Skew: **salting**, repartition, **broadcast joins**, AQE, better dist/partition keys.
