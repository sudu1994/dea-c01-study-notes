# DEA-C01 Cheat Sheet

> 🔰 New to data? Each tool's first mention links to a plain-English explanation in [Data Basics for Beginners](00-data-basics-for-beginners.md). Abbreviations are listed in the [glossary](00-abbreviations-glossary.md).

> One-page review for the last 48 hours before the exam.

## Keyword → answer decoder

| If the question says… | Think… |
|---|---|
| Real time, multiple consumers, replay, ordering | **[Kinesis Data Streams](00-data-basics-for-beginners.md#amazon-kinesis-data-streams)** |
| Near real time, deliver to [S3](00-data-basics-for-beginners.md#amazon-s3)/Redshift/OpenSearch, least ops | **[Amazon Data Firehose](00-data-basics-for-beginners.md#amazon-data-firehose)** |
| [Kafka](00-data-basics-for-beginners.md#apache-kafka), existing Kafka clients | **Amazon [Managed Streaming for Apache Kafka [MSK]](00-data-basics-for-beginners.md#amazon-msk)** (Serverless for no sizing) |
| Windowed aggregations / stateful stream processing | **[Managed Service for Apache Flink](00-data-basics-for-beginners.md#managed-service-for-apache-flink)** |
| Database migration, Change Data Capture (CDC) | **Amazon Web Services (AWS) [Database Migration Service [DMS]](00-data-basics-for-beginners.md#aws-dms)** (+ DMS Schema Conversion for heterogeneous) |
| Database (DB) → [Redshift](00-data-basics-for-beginners.md#amazon-redshift) with no pipeline | **[Zero-ETL](00-data-basics-for-beginners.md#zero-etl-integrations) integration** |
| Software as a Service (SaaS) source ([Salesforce](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce), Zendesk…) | **[Amazon AppFlow](00-data-basics-for-beginners.md#amazon-appflow)** |
| On-prem Network File System (NFS)/Server Message Block (SMB) to Simple Storage Service (S3) | **[AWS DataSync](00-data-basics-for-beginners.md#aws-datasync)** |
| Partners upload over SSH File Transfer Protocol (SFTP) | **[AWS Transfer Family](00-data-basics-for-beginners.md#aws-transfer-family)** |
| Petabytes offline | **[Snow Family](00-data-basics-for-beginners.md#aws-snow-family)** |
| Third-party datasets | **[AWS Data Exchange](00-data-basics-for-beginners.md#aws-data-exchange)** |
| Serverless [Spark](00-data-basics-for-beginners.md#apache-spark) Extract, Transform, Load (ETL) | **[AWS Glue](00-data-basics-for-beginners.md#aws-glue)** |
| Process only new data | **Glue job bookmarks** |
| Non-urgent job, cheaper | **Glue Flex** |
| No-code data prep for analysts | **[Glue DataBrew](00-data-basics-for-beginners.md#aws-glue-databrew)** |
| Fuzzy dedup without exact key | **Glue FindMatches** |
| Full [Hadoop](00-data-basics-for-beginners.md#apache-hadoop) ecosystem, Spot | **Amazon [Elastic MapReduce [EMR]](00-data-basics-for-beginners.md#amazon-emr)** (Spot on **task** nodes) |
| [Structured Query Language [SQL]](00-data-basics-for-beginners.md#sql) on S3, pay per query | **[Athena](00-data-basics-for-beginners.md#amazon-athena)** |
| Petabyte warehouse, Business Intelligence (BI) | **Redshift** |
| Query S3 from Redshift | **Redshift Spectrum** |
| Query live [RDS](00-data-basics-for-beginners.md#amazon-rds)/Aurora from Redshift | **Federated query** |
| Share Redshift data without copying | **Redshift data sharing** |
| Updates/deletes/time travel on S3 | **[Apache Iceberg](00-data-basics-for-beginners.md#apache-iceberg)** |
| Managed Iceberg, automatic compaction | **[Amazon S3 Tables](00-data-basics-for-beginners.md#amazon-s3-tables)** |
| Vector search with SQL/relational data | **[Aurora](00-data-basics-for-beginners.md#amazon-aurora) [PostgreSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server) + pgvector (Hierarchical Navigable Small World [HNSW])** |
| Hybrid keyword + vector search | **[OpenSearch](00-data-basics-for-beginners.md#amazon-opensearch-service)** |
| Microsecond [DynamoDB](00-data-basics-for-beginners.md#amazon-dynamodb) reads | **DynamoDB Accelerator (DAX)** |
| Durable in-memory key/value | **[MemoryDB](00-data-basics-for-beginners.md#amazon-memorydb-and-elasticache)** |
| Retrieval-Augmented Generation (RAG) data pipeline, managed | **[Bedrock](00-data-basics-for-beginners.md#amazon-bedrock) Knowledge Bases** |
| Large Language Model (LLM) over a large batch of records, cheap | **Bedrock batch inference** |
| Serverless workflow across AWS services | **[Step Functions](00-data-basics-for-beginners.md#aws-step-functions)** |
| Existing [Airflow](00-data-basics-for-beginners.md#apache-airflow) Directed Acyclic Graphs (DAGs) | **[Managed Workflows for Apache Airflow [MWAA]](00-data-basics-for-beginners.md#amazon-mwaa)** |
| Only Glue jobs and crawlers | **Glue workflows** |
| Start pipeline on file arrival | **S3 → [EventBridge](00-data-basics-for-beginners.md#amazon-eventbridge) → Step Functions** |
| Notify on failure | **EventBridge / [CloudWatch](00-data-basics-for-beginners.md#amazon-cloudwatch) alarm → [Simple Notification Service [SNS]](00-data-basics-for-beginners.md#amazon-sns)** |
| Many Lambdas overwhelm Relational Database Service (RDS) | **RDS Proxy** |
| Allowlist a fixed outbound Internet Protocol (IP) | **Network Address Translation (NAT) gateway Elastic IP** |
| Shared persistent files in [Lambda](00-data-basics-for-beginners.md#aws-lambda) | **Elastic File System (EFS) mount** |
| Package/deploy serverless pipeline | **AWS [Serverless Application Model [SAM]](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam)** |
| Infra in TypeScript/Python | **AWS Cloud Development Kit (CDK)** |
| Data quality rules in pipeline | **[Glue Data Quality](00-data-basics-for-beginners.md#aws-glue-data-quality) (Data Quality Definition Language [DQDL])** |
| Data quality without code | **DataBrew rulesets + profile jobs** |
| Unknown access pattern storage | **S3 Intelligent-Tiering** |
| Write Once, Read Many (WORM), even root can't delete | **S3 Object Lock compliance mode** |
| Auto-expire DynamoDB items | **DynamoDB Time To Live (TTL)** |
| Producer schema changes break consumers | **Glue Schema Registry** |
| Too many partitions, slow Athena | **Partition projection** |
| Athena can't see new partitions | **Metastore Consistency Check (MSCK) REPAIR / ADD PARTITION / projection** |
| Who did it? | **[CloudTrail](00-data-basics-for-beginners.md#aws-cloudtrail)** (S3 objects → **data events**) |
| What changed / compliant? | **[AWS Config](00-data-basics-for-beginners.md#aws-config)** |
| SQL over audit events, org-wide | **CloudTrail Lake** |
| Quick log search | **CloudWatch Logs Insights** |
| Rotate DB passwords automatically | **[Secrets Manager](00-data-basics-for-beginners.md#aws-secrets-manager)** |
| Table/column/row permissions on the lake | **[Lake Formation](00-data-basics-for-beginners.md#aws-lake-formation)** (data filters) |
| Scale permissions over thousands of tables | **Lake Formation tags [LF-tags] (Tag-Based Access Control [TBAC])** |
| Masked values per role in Redshift | **Dynamic data masking** |
| Find Personally Identifiable Information (PII) in S3 | **[Amazon Macie](00-data-basics-for-beginners.md#amazon-macie)** |
| Cross-account [Key Management Service [KMS]](00-data-basics-for-beginners.md#aws-kms) | **Customer managed key** + key policy |
| Enforce Hypertext Transfer Protocol Secure (HTTPS) to S3 | **`aws:SecureTransport` deny** |
| Encrypt before sending | **Client-side encryption** |
| Keep data in approved Regions | **Service Control Policy (SCP) `aws:RequestedRegion`** |
| Business catalog, request access | **[SageMaker Catalog](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)** |
| One workspace for data + Artificial Intelligence (AI) teams | **SageMaker Unified Studio** |

## Numbers to remember

| Item | Value |
|---|---|
| Kinesis Data Streams (KDS) shard write | 1 MB/s or 1,000 records/s |
| KDS shard read | 2 MB/s shared (5 GetRecords/s); 2 MB/s **per consumer** with enhanced fan-out |
| KDS retention | 24 h default → up to 365 days |
| DynamoDB Streams retention | 24 h |
| Lambda | 15 min timeout; 128 MB–10,240 MB memory; /tmp up to 10 GB; Kinesis parallelization factor up to 10 |
| Step Functions | Standard up to 1 year; Express up to 5 min; 256 KB payload |
| Firehose buffer | 1–128 MiB size / interval (zero buffering available) |
| S3 request rate | 3,500 writes & 5,500 reads per second **per prefix** |
| S3 lifecycle to Infrequent Access (IA) | ≥ 30 days in Standard |
| S3 minimum durations | IA 30 d; Glacier Instant Retrieval (Glacier IR)/Flexible 90 d; Deep Archive 180 d |
| Deep Archive retrieval | 12–48 h |
| DynamoDB item max | 400 KB |
| DynamoDB Point-In-Time Recovery (PITR) | 35 days |
| Redshift automated snapshots | 1-day default, up to 35 days |
| CloudTrail Event history | 90 days |
| Ideal analytics file size | 128 MB – 1 GB |
| Exam | 65 Qs (50 scored), 130 min, pass 720 |

## Common "least operational overhead" winners
Firehose > KDS + custom code · Glue > EMR · Athena > EMR for SQL · Redshift Serverless > provisioned for spiky use · AppFlow > custom [Application Programming Interface [API]](00-data-basics-for-beginners.md#api) code · Step Functions > custom orchestration on Elastic Compute Cloud (EC2) · S3 Tables > self-maintained Iceberg · Zero-ETL > DMS + Glue for supported sources · Managed services > self-managed on EC2.
