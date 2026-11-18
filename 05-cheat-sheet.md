# DEA-C01 Cheat Sheet

> One-page review for the last 48 hours before the exam.

## Keyword → answer decoder

| If the question says… | Think… |
|---|---|
| Real time, multiple consumers, replay, ordering | **Kinesis Data Streams** |
| Near real time, deliver to S3/Redshift/OpenSearch, least ops | **Amazon Data Firehose** |
| Kafka, existing Kafka clients | **Amazon MSK** (Serverless for no sizing) |
| Windowed aggregations / stateful stream processing | **Managed Service for Apache Flink** |
| Database migration, CDC | **AWS DMS** (+ DMS Schema Conversion for heterogeneous) |
| DB → Redshift with no pipeline | **Zero-ETL integration** |
| SaaS source (Salesforce, Zendesk…) | **Amazon AppFlow** |
| On-prem NFS/SMB to S3 | **AWS DataSync** |
| Partners upload over SFTP | **AWS Transfer Family** |
| Petabytes offline | **Snow Family** |
| Third-party datasets | **AWS Data Exchange** |
| Serverless Spark ETL | **AWS Glue** |
| Process only new data | **Glue job bookmarks** |
| Non-urgent job, cheaper | **Glue Flex** |
| No-code data prep for analysts | **Glue DataBrew** |
| Fuzzy dedup without exact key | **Glue FindMatches** |
| Full Hadoop ecosystem, Spot | **Amazon EMR** (Spot on **task** nodes) |
| SQL on S3, pay per query | **Athena** |
| Petabyte warehouse, BI | **Redshift** |
| Query S3 from Redshift | **Redshift Spectrum** |
| Query live RDS/Aurora from Redshift | **Federated query** |
| Share Redshift data without copying | **Redshift data sharing** |
| Updates/deletes/time travel on S3 | **Apache Iceberg** |
| Managed Iceberg, automatic compaction | **Amazon S3 Tables** |
| Vector search with SQL/relational data | **Aurora PostgreSQL + pgvector (HNSW)** |
| Hybrid keyword + vector search | **OpenSearch** |
| Microsecond DynamoDB reads | **DAX** |
| Durable in-memory key/value | **MemoryDB** |
| RAG data pipeline, managed | **Bedrock Knowledge Bases** |
| LLM over a large batch of records, cheap | **Bedrock batch inference** |
| Serverless workflow across AWS services | **Step Functions** |
| Existing Airflow DAGs | **MWAA** |
| Only Glue jobs and crawlers | **Glue workflows** |
| Start pipeline on file arrival | **S3 → EventBridge → Step Functions** |
| Notify on failure | **EventBridge / CloudWatch alarm → SNS** |
| Many Lambdas overwhelm RDS | **RDS Proxy** |
| Allowlist a fixed outbound IP | **NAT gateway Elastic IP** |
| Shared persistent files in Lambda | **EFS mount** |
| Package/deploy serverless pipeline | **AWS SAM** |
| Infra in TypeScript/Python | **AWS CDK** |
| Data quality rules in pipeline | **Glue Data Quality (DQDL)** |
| Data quality without code | **DataBrew rulesets + profile jobs** |
| Unknown access pattern storage | **S3 Intelligent-Tiering** |
| WORM, even root can't delete | **S3 Object Lock compliance mode** |
| Auto-expire DynamoDB items | **DynamoDB TTL** |
| Producer schema changes break consumers | **Glue Schema Registry** |
| Too many partitions, slow Athena | **Partition projection** |
| Athena can't see new partitions | **MSCK REPAIR / ADD PARTITION / projection** |
| Who did it? | **CloudTrail** (S3 objects → **data events**) |
| What changed / compliant? | **AWS Config** |
| SQL over audit events, org-wide | **CloudTrail Lake** |
| Quick log search | **CloudWatch Logs Insights** |
| Rotate DB passwords automatically | **Secrets Manager** |
| Table/column/row permissions on the lake | **Lake Formation** (data filters) |
| Scale permissions over thousands of tables | **LF-tags (TBAC)** |
| Masked values per role in Redshift | **Dynamic data masking** |
| Find PII in S3 | **Amazon Macie** |
| Cross-account KMS | **Customer managed key** + key policy |
| Enforce HTTPS to S3 | **`aws:SecureTransport` deny** |
| Encrypt before sending | **Client-side encryption** |
| Keep data in approved Regions | **SCP `aws:RequestedRegion`** |
| Business catalog, request access | **SageMaker Catalog** |
| One workspace for data + AI teams | **SageMaker Unified Studio** |

## Numbers to remember

| Item | Value |
|---|---|
| KDS shard write | 1 MB/s or 1,000 records/s |
| KDS shard read | 2 MB/s shared (5 GetRecords/s); 2 MB/s **per consumer** with enhanced fan-out |
| KDS retention | 24 h default → up to 365 days |
| DynamoDB Streams retention | 24 h |
| Lambda | 15 min timeout; 128 MB–10,240 MB memory; /tmp up to 10 GB; Kinesis parallelization factor up to 10 |
| Step Functions | Standard up to 1 year; Express up to 5 min; 256 KB payload |
| Firehose buffer | 1–128 MiB size / interval (zero buffering available) |
| S3 request rate | 3,500 writes & 5,500 reads per second **per prefix** |
| S3 lifecycle to IA | ≥ 30 days in Standard |
| S3 minimum durations | IA 30 d; Glacier IR/Flexible 90 d; Deep Archive 180 d |
| Deep Archive retrieval | 12–48 h |
| DynamoDB item max | 400 KB |
| DynamoDB PITR | 35 days |
| Redshift automated snapshots | 1-day default, up to 35 days |
| CloudTrail Event history | 90 days |
| Ideal analytics file size | 128 MB – 1 GB |
| Exam | 65 Qs (50 scored), 130 min, pass 720 |

## Common "least operational overhead" winners
Firehose > KDS + custom code · Glue > EMR · Athena > EMR for SQL · Redshift Serverless > provisioned for spiky use · AppFlow > custom API code · Step Functions > custom orchestration on EC2 · S3 Tables > self-maintained Iceberg · Zero-ETL > DMS + Glue for supported sources · Managed services > self-managed on EC2.
