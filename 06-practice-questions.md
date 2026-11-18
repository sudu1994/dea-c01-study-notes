# DEA-C01 Practice Questions (20)

> Answer each question first, then expand the explanation.

---

**1.** A company ingests clickstream events at 4,000 records/second, each 1.5 KB. Three applications must each read every event in real time, and the data must be reprocessable for 7 days. What is the most cost-effective design?

- A. Amazon Data Firehose delivering to S3 with three Lambda transformations
- B. Kinesis Data Streams with 6 shards, 7-day retention, and enhanced fan-out consumers
- C. Kinesis Data Streams with 4 shards and default retention
- D. Amazon SQS standard queue with three consumers

<details><summary>Answer</summary>

**B.** Ingest = 6 MB/s and 4,000 rec/s → 6 shards (the MB limit dominates). Multiple real-time consumers reading everything → enhanced fan-out. Replay for 7 days → extend retention. Firehose and SQS can't replay, and 4 shards can't absorb 6 MB/s.
</details>

---

**2.** JSON events arrive continuously and must land in S3 as Parquet, partitioned by `customer_id`, with the least operational overhead.

- A. Kinesis Data Streams + Lambda converting to Parquet
- B. Firehose with record format conversion (Glue table schema) and dynamic partitioning
- C. Glue streaming job writing CSV, then a nightly crawler
- D. MSK + MSK Connect S3 sink in JSON format

<details><summary>Answer</summary>

**B.** Firehose converts JSON to Parquet natively using a Glue Data Catalog schema, and dynamic partitioning writes `customer_id=` prefixes. No code to maintain.
</details>

---

**3.** A nightly Glue job reprocesses all files in an S3 prefix, even though only a few new files arrive each day. Costs are rising. What should the data engineer do? (Choose TWO.)

- A. Enable job bookmarks
- B. Increase the number of workers
- C. Use Flex execution for the job
- D. Switch to a Python shell job with pandas
- E. Run a crawler before each job

<details><summary>Answer</summary>

**A, C.** Bookmarks process only new files. Flex lowers cost for non-urgent jobs. More workers increases cost, and Python shell may not handle Spark-scale data.
</details>

---

**4.** A Lambda function consuming a Kinesis stream keeps failing on one malformed record, and the shard stops progressing. What fixes this while keeping other records flowing?

- A. Increase the Lambda timeout
- B. Enable bisect batch on function error, set maximum retry attempts, and configure an on-failure destination (SQS)
- C. Increase the shard count
- D. Switch the starting position to LATEST

<details><summary>Answer</summary>

**B.** Bisecting isolates the poison record, bounded retries stop the blocking, and the on-failure destination keeps the failed record's metadata for later review.
</details>

---

**5.** Analysts query a 50 TB clickstream table in Athena by date. Queries are slow and expensive. The table is stored as GZIP CSV with no partitions. Which changes give the biggest improvement? (Choose TWO.)

- A. Convert to Parquet with Snappy compression
- B. Partition by date
- C. Increase the Athena workgroup data limit
- D. Add `LIMIT 100` to queries
- E. Move the data to S3 Standard-IA

<details><summary>Answer</summary>

**A, B.** Columnar format plus partition pruning dramatically cut data scanned. `LIMIT` doesn't reduce data scanned, and storage class doesn't affect query speed.
</details>

---

**6.** A Redshift query joining a 2-billion-row `sales` fact table with a 1-billion-row `customers` table on `customer_id` shows `DS_DIST_BOTH` in the plan. What is the best fix?

- A. Set `DISTSTYLE ALL` on both tables
- B. Set `DISTKEY(customer_id)` on both tables
- C. Add an interleaved sort key
- D. Enable concurrency scaling

<details><summary>Answer</summary>

**B.** Co-locating both large tables on the join key removes redistribution. `ALL` is only for small tables.
</details>

---

**7.** A company needs to delete individual customers' records from its S3 data lake within 30 days of request (GDPR) without rewriting entire partitions manually. What should it use?

- A. S3 Lifecycle expiration rules
- B. Apache Iceberg tables with `DELETE` statements in Athena, followed by snapshot expiration
- C. S3 Object Lock governance mode
- D. DynamoDB TTL

<details><summary>Answer</summary>

**B.** Iceberg supports row-level deletes, and expiring snapshots removes the old data files. Lifecycle works on whole objects by age, and Object Lock prevents deletion.
</details>

---

**8.** An application needs semantic search over product descriptions stored alongside relational order data, with high recall and low latency. Memory is not a concern. What should the data engineer choose?

- A. Aurora PostgreSQL with pgvector and an HNSW index
- B. Aurora PostgreSQL with pgvector and an IVFFlat index trained on a small sample
- C. DynamoDB with a GSI on the embedding
- D. Athena over Parquet embeddings

<details><summary>Answer</summary>

**A.** HNSW gives high recall and fast queries at the cost of memory, which is acceptable here. pgvector keeps vectors next to relational data.
</details>

---

**9.** Athena queries on a table with daily partitions spanning 10 years are slow in the planning phase, and new partitions must appear immediately without crawlers. What is the best solution?

- A. Run `MSCK REPAIR TABLE` hourly
- B. Configure partition projection on the table
- C. Run the crawler every 5 minutes
- D. Convert the table to CSV

<details><summary>Answer</summary>

**B.** Partition projection computes partitions from table properties, removing catalog lookups and the need to register new partitions.
</details>

---

**10.** A team wants Kafka producers to stop publishing messages whose Avro schema would break existing consumers. What should be used?

- A. Glue crawler with schema change policy "update the table definition"
- B. AWS Glue Schema Registry with BACKWARD compatibility
- C. Lake Formation LF-tags
- D. DMS Schema Conversion

<details><summary>Answer</summary>

**B.** Schema Registry validates new schema versions against the compatibility mode before producers can use them.
</details>

---

**11.** A Step Functions Express workflow fails intermittently, but the console shows no execution history. What should the engineer do first?

- A. Convert to a Standard workflow permanently
- B. Enable CloudWatch Logs (level ALL or ERROR) for the state machine
- C. Enable CloudTrail data events
- D. Increase the payload size limit

<details><summary>Answer</summary>

**B.** Express workflows record execution details only in CloudWatch Logs when logging is enabled.
</details>

---

**12.** A Glue ETL job must stop loading data into Redshift when more than 5% of `email` values are null, and route bad rows to a quarantine prefix otherwise. What should be used?

- A. A DataBrew profile job run weekly
- B. Glue Data Quality's Evaluate Data Quality transform with DQDL rules inside the job
- C. Athena queries scheduled by EventBridge
- D. Macie sensitive data discovery

<details><summary>Answer</summary>

**B.** In-job DQDL rules (e.g., `Completeness "email" > 0.95`) can fail the job or route failing records during processing.
</details>

---

**13.** A Spark job on EMR has one task running 40 minutes while others finish in 2 minutes. The join key `country` has 70% of rows with value `US`. Which mechanisms reduce the problem? (Choose TWO.)

- A. Salt the `country` key and aggregate in two stages
- B. Broadcast the smaller table in the join
- C. Add more core nodes
- D. Store the data as CSV
- E. Disable Adaptive Query Execution

<details><summary>Answer</summary>

**A, B.** Salting spreads the hot key, and broadcasting avoids shuffling the skewed side. More nodes don't help a single overloaded task.
</details>

---

**14.** The security team must find out who deleted objects from a production S3 bucket last week. What must already have been enabled?

- A. AWS Config for S3
- B. CloudTrail data events for the bucket (or S3 server access logs)
- C. CloudWatch Logs Insights
- D. Macie automated discovery

<details><summary>Answer</summary>

**B.** Object-level API calls like `DeleteObject` are data events, which aren't recorded by default. Server access logs also capture requests.
</details>

---

**15.** Account B's Athena users can't read S3 objects in account A, even though the bucket policy grants account B access. Objects are encrypted with the `aws/s3` key. What is the fix?

- A. Add account B to the `aws/s3` key policy
- B. Re-encrypt the objects with a customer managed KMS key whose key policy allows account B, and grant `kms:Decrypt` in account B's IAM policies
- C. Enable S3 Bucket Keys
- D. Switch to SSE-C

<details><summary>Answer</summary>

**B.** AWS managed keys can't be shared cross-account. A customer managed key with a key policy plus consumer IAM permissions is required.
</details>

---

**16.** Analysts across 300 Glue tables should see columns tagged `confidential` only if they belong to the finance team, and new tables must follow the rule automatically. What is the most scalable approach?

- A. IAM policies per table
- B. S3 bucket policies per prefix
- C. Lake Formation LF-tags (tag-based access control)
- D. Redshift dynamic data masking

<details><summary>Answer</summary>

**C.** LF-TBAC grants on tag expressions, and newly tagged tables and columns inherit the access rules.
</details>

---

**17.** A company must ensure no backups or replicas of its data are ever created outside eu-central-1 in any account. What should it implement?

- A. AWS Config rule reporting non-compliant buckets
- B. Service control policy denying actions where `aws:RequestedRegion` is not eu-central-1 (with exemptions for global services)
- C. Macie jobs in every Region
- D. S3 Object Lock

<details><summary>Answer</summary>

**B.** An SCP **prevents** the actions. Config only detects them after the fact.
</details>

---

**18.** A finance team needs live, read-only access to tables in the sales team's Redshift Serverless workgroup in another account, without copying data. What should be used?

- A. UNLOAD to S3 and COPY into the finance warehouse nightly
- B. Redshift data sharing (producer authorizes, consumer account associates the datashare)
- C. DMS replication between warehouses
- D. Redshift federated query

<details><summary>Answer</summary>

**B.** Data sharing gives live, zero-copy access across accounts. Federated query targets RDS/Aurora, not other Redshift warehouses.
</details>

---

**19.** Business users must search for datasets by business terms, request access, and get approval from data owners, with access granted automatically to their team. What should be used?

- A. AWS Glue Data Catalog with crawlers
- B. Amazon SageMaker Catalog with projects and subscription requests
- C. AWS Data Exchange
- D. IAM Identity Center permission sets

<details><summary>Answer</summary>

**B.** SageMaker Catalog provides the business glossary, search, and publish/subscribe workflow, and grants access to the requesting project once approved.
</details>

---

**20.** A pipeline must classify 20 million archived support tickets by topic with an LLM. Results are needed within 2 days, and cost must be minimized. What is the best approach?

- A. Lambda invoking Bedrock on-demand for each ticket via S3 events
- B. Prepare JSONL input in S3 and run an Amazon Bedrock batch inference job, then load the output with Glue
- C. Host an open-source model on EC2 GPU instances
- D. Use Amazon Q in QuickSight

<details><summary>Answer</summary>

**B.** Batch inference is designed for large asynchronous workloads at lower cost than on-demand calls, and avoids throttling.
</details>
