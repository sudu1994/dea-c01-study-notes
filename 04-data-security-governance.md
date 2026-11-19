# Domain 4: Data Security and Governance (18%)

> **About 9 of the 50 scored questions.**
>
> This domain covers who can get in (authentication), what they can do (authorization), how data is protected (encryption and masking), how activity is recorded (audit logging), and how data is governed (privacy, Personally Identifiable Information (PII), sovereignty, sharing, SageMaker Catalog). The smallest domain, but its questions are often "two answers look right," so precision matters.

## Table of contents

- [Exam tasks and skills](#exam-tasks-and-skills)
- [Task 4.1: Apply authentication mechanisms](#task-41-apply-authentication-mechanisms)
- [Task 4.2: Apply authorization mechanisms](#task-42-apply-authorization-mechanisms)
- [Task 4.3: Ensure data encryption and masking](#task-43-ensure-data-encryption-and-masking)
- [Task 4.4: Prepare logs for audit](#task-44-prepare-logs-for-audit)
- [Task 4.5: Understand data privacy and governance](#task-45-understand-data-privacy-and-governance)
- [Gotchas and exam traps](#gotchas-and-exam-traps)
- [Quick-recall summary](#quick-recall-summary)

## Exam tasks and skills

> Summarized from the official AWS Certified Data Engineer – Associate (DEA-C01) exam guide (v1.1). Exact wording: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain4.html

### Task 4.1: Apply authentication mechanisms
- **4.1.1** Update Virtual Private Cloud (VPC) security groups.
- **4.1.2** Create/update Identity and Access Management (IAM) groups, roles, endpoints, and services.
- **4.1.3** Create and rotate credentials (Secrets Manager).
- **4.1.4** Set up IAM roles for access (Lambda, Application Programming Interface (API) Gateway, Amazon Web Services (AWS) Command Line Interface (CLI), CloudFormation).
- **4.1.5** Apply IAM policies to roles, endpoints, services (Simple Storage Service (S3) Access Points, PrivateLink).
- **4.1.6** Describe managed vs unmanaged services.
- **4.1.7** 🆕 Use domains, domain units, and projects in SageMaker Unified Studio.

### Task 4.2: Apply authorization mechanisms
- **4.2.1** Write custom IAM policies when managed policies don't fit.
- **4.2.2** Store application and database credentials (Secrets Manager, Parameter Store).
- **4.2.3** Grant database users, groups, and roles access in a database (Redshift).
- **4.2.4** Manage permissions with Lake Formation (for Redshift, Elastic MapReduce (EMR), Athena, S3).
- **4.2.5** Apply role-based, tag-based, and attribute-based authorization.
- **4.2.6** Build custom least-privilege policies.

### Task 4.3: Ensure data encryption and masking
- **4.3.1** Apply masking and anonymization for compliance/policy.
- **4.3.2** Encrypt/decrypt with keys (Key Management Service (KMS)).
- **4.3.3** Configure encryption across account boundaries.
- **4.3.4** Encrypt in transit or **before** transit.

### Task 4.4: Prepare logs for audit
- **4.4.1** Track API calls with CloudTrail.
- **4.4.2** Store application logs in CloudWatch Logs.
- **4.4.3** Query centrally with CloudTrail Lake.
- **4.4.4** Analyze logs (Athena, CloudWatch Logs Insights, OpenSearch).
- **4.4.5** Integrate services for logging (e.g., EMR for large log volumes).

### Task 4.5: Understand data privacy and governance
- **4.5.1** Grant permissions for data sharing (e.g., Redshift data sharing).
- **4.5.2** Identify PII (Macie with Lake Formation).
- **4.5.3** Prevent backups/replication to disallowed Regions.
- **4.5.4** View configuration changes (AWS Config).
- **4.5.5** Maintain data sovereignty.
- **4.5.6** 🆕 Manage data access through SageMaker Catalog projects.
- **4.5.7** 🆕 Describe governance frameworks and data sharing patterns.

---

## Task 4.1: Apply authentication mechanisms

### Core concepts

- **Authentication** = proving *who* you are. **Authorization** = deciding *what* you may do.
- **Methods:**
  - **Password-based**: database users, console passwords (+ **Multi-Factor Authentication (MFA)**).
  - **Certificate-based**: X.509 certificates, mutual Transport Layer Security (TLS), IoT devices, client certificates.
  - **Role-based**: assume an **IAM role** and get **temporary credentials** from AWS Security Token Service (STS). **This is the preferred method for AWS workloads.**
- Workforce users sign in through **IAM Identity Center** (Single Sign-On (SSO), federated with Okta, Microsoft Entra ID, etc.). Avoid long-lived IAM user access keys.

### VPC security groups (skill 4.1.1)

| | Security group | Network Access Control List (ACL) |
|---|---|---|
| Level | Elastic Network Interface (ENI)/instance (Glue connection Elastic Network Interfaces (ENIs), Redshift, Relational Database Service (RDS), EMR, Lambda in VPC) | Subnet |
| State | **Stateful** (return traffic allowed automatically) | **Stateless** (allow both directions, incl. ephemeral ports) |
| Rules | **Allow only** | Allow and deny, numbered order |
| Sources | Classless Inter-Domain Routing ranges (CIDRs), prefix lists, **other security groups** | CIDRs only |

Data-engineering patterns:
- Database Security Group (SG) allows the port (5439 Redshift, 5432 PostgreSQL, 3306 MySQL) **from the application/Glue SG**, not from `0.0.0.0/0`.
- **Glue**: SG needs a **self-referencing inbound rule for all Transmission Control Protocol (TCP)**.
- **EMR**: managed security groups for primary/core/task nodes; block public access setting.
- Lambda in a VPC: outbound rules to reach databases; Network Address Translation (NAT) gateway or VPC endpoints for AWS Application Programming Interfaces (APIs).

### IAM groups, roles, endpoints, services (skills 4.1.2, 4.1.4)

- **IAM users** (avoid for apps) → **groups** (assign policies to many users) → **roles** (assumed by services, users, other accounts; temporary credentials).
- A role has a **trust policy** (who can assume it) and **permissions policies** (what it can do).

| Service | Role setup |
|---|---|
| **Lambda** | **Execution role** trusted by `lambda.amazonaws.com` (e.g., read S3, write logs) |
| **Glue** | Service role trusted by `glue.amazonaws.com` (S3 paths, catalog, KMS, CloudWatch) |
| **API Gateway** | Role for AWS service integrations (e.g., put to Kinesis); a resource-based permission on Lambda lets API Gateway invoke it; IAM authorization for callers |
| **AWS CLI** | Named profiles with `role_arn` + `source_profile` (or IAM Identity Center `sso` profiles) to assume roles |
| **CloudFormation** | **Service role** CloudFormation uses to create resources, so users only need permission to pass that role (`iam:PassRole`) |
| **Redshift** | IAM role attached to the cluster/workgroup for COPY/UNLOAD/Spectrum |
| **EC2/EMR** | **Instance profile** (role for instances); EMR also has a service role |

- **`iam:PassRole`**: required to hand a role to a service (e.g., a user creating a Glue job with role X needs `iam:PassRole` on X). It's a frequent permission-error answer.
- **VPC endpoints**: **gateway endpoints** (S3, DynamoDB; route table entry; free) and **interface endpoints** (PrivateLink ENIs for most services: Glue, Athena, KMS, Secrets Manager, STS, Kinesis…). Traffic stays on the AWS network with no internet or NAT needed.

### Credentials and rotation (skill 4.1.3)

- **AWS Secrets Manager**: stores database (DB) credentials, API keys, tokens; **automatic rotation** on a schedule using Lambda rotation functions (managed rotation for RDS, Aurora, Redshift, DocumentDB); KMS-encrypted; resource policies for **cross-account** access; versioning (`AWSCURRENT`/`AWSPREVIOUS`).
- **RDS/Aurora/Redshift managed master passwords** can live in Secrets Manager directly.
- **Redshift temporary credentials**: `GetClusterCredentials` / IAM-based auth (or Redshift Serverless `GetCredentials`) gives short-lived database credentials, with no stored passwords.
- **RDS IAM database authentication**: authenticate with an IAM token instead of a password.

### IAM policies on roles, endpoints, services (skill 4.1.5)

- **Identity-based policies** (attached to users/groups/roles) vs **resource-based policies** (attached to the resource: S3 bucket policy, KMS key policy, Simple Queue Service (SQS) queue policy, Secrets Manager resource policy, Lambda permissions).
- **S3 Access Points**: named network endpoints on a bucket, each with **its own access point policy**. They simplify managing access for many teams/apps on a shared bucket. They can be **VPC-only** (network origin = VPC). The bucket policy can delegate control to access points.
- **VPC endpoint policies**: restrict *which* resources/actions can be reached through the endpoint (e.g., only the company's buckets → data exfiltration protection).
- Bucket policy conditions: `aws:SourceVpce` (only via a specific endpoint), `aws:SourceVpc`, `aws:PrincipalOrgID` (only principals in your organization), `aws:SecureTransport`.
- **AWS PrivateLink** also lets you expose your own service (Network Load Balancer (NLB)) privately to other Virtual Private Clouds (VPCs)/accounts.

### Managed vs unmanaged services (skill 4.1.6)

| | Managed (Glue, Athena, Redshift Serverless, DynamoDB, Managed Streaming for Apache Kafka (MSK) Serverless, Firehose) | Unmanaged / self-managed (Kafka or Hadoop on Elastic Compute Cloud (EC2), DB on EC2) |
|---|---|---|
| Patching, Operating System (OS), High Availability (HA) | AWS | **You** |
| Security responsibility | You configure IAM, encryption, network; AWS secures the infrastructure | You also secure the OS, software, patches, backups |
| Flexibility | Less control | Full control of versions/configs |
| Ops overhead | Low | High |

This is the **shared responsibility model**: the more managed the service, the more AWS takes on.

### 🆕 SageMaker Unified Studio: domains, domain units, projects (skill 4.1.7)

| Concept | Meaning | Governance role |
|---|---|---|
| **Domain** | Top-level container for an organization's SageMaker Unified Studio (users, catalog, projects); usually tied to **IAM Identity Center** for sign-in | Boundary for governance, catalog, and users |
| **Domain units** | Hierarchical sub-groupings inside a domain (e.g., by business unit: Finance, Marketing) | Delegated ownership and **authorization policies** (who can create projects, publish to the catalog, use which project profiles) |
| **Projects** | Collaborative workspaces for a team: members (owners/contributors), data, compute, tools | Each project has its **own IAM role**. Members' data access is granted **to the project**, so it's the unit of access control. |
| **Project profiles / blueprints** | Templates defining which resources and tools a project gets | Standardized, approved environments |

---

## Task 4.2: Apply authorization mechanisms

### Custom IAM policies and least privilege (skills 4.2.1, 4.2.6)

- **AWS managed policies** (e.g., `AmazonS3ReadOnlyAccess`): broad, maintained by AWS, can't be edited.
- **Customer managed policies**: you write and version them; reusable; the answer when **managed policies are too broad**.
- **Inline policies**: embedded in one identity; strict 1:1 relationships.

**Least-privilege policy techniques:**
- Specific **actions** (no `s3:*`), specific **resource Amazon Resource Names (ARNs)** (bucket + prefix: `arn:aws:s3:::lake/curated/finance/*`).
- **Conditions**: `s3:prefix`, `aws:PrincipalTag`, `aws:SourceVpce`, `aws:RequestedRegion`, `kms:ViaService`, `aws:MultiFactorAuthPresent`.
- Remember that S3 needs **`s3:ListBucket` on the bucket Amazon Resource Name (ARN)** and **`s3:GetObject` on `bucket/*`**, two different resources.
- **IAM Access Analyzer**: generates least-privilege policies **from CloudTrail activity**, validates policies, and finds resources shared outside your account.
- Guardrails: **permission boundaries** (max permissions for a role/user) and **Service Control Policies (SCPs)** in AWS Organizations (max permissions for accounts). Neither grants anything. They only limit.
- Evaluation: an **explicit Deny always wins**. Otherwise, access needs an Allow (and none of SCP/boundary/session policy blocking it).

### Storing credentials (skill 4.2.2)

| | Secrets Manager | Systems Manager Parameter Store |
|---|---|---|
| Purpose | Secrets (DB passwords, API keys) | Configuration values and secrets (`SecureString` with KMS) |
| **Automatic rotation** | ✅ built in | ❌ (do it yourself) |
| Cross-account sharing | ✅ resource policy | Limited (advanced tier sharing) |
| Cost | Per secret per month + API calls | **Standard tier free** |
| Exam choice | "**Rotate automatically**", DB credentials for RDS/Redshift | Cheap config/flags, no rotation needed |

Glue connections, Lambda, EMR, Managed Workflows for Apache Airflow (MWAA), and QuickSight can all read from Secrets Manager. **Never** put credentials in code, plain environment variables, or job parameters.

### Database-level authorization in Redshift (skill 4.2.3)

- **Users** and **groups** (legacy) or **roles** (**Role-Based Access Control (RBAC)**: `CREATE ROLE analyst; GRANT SELECT ON ALL TABLES IN SCHEMA sales TO ROLE analyst; GRANT ROLE analyst TO alice;`). Roles can be nested and include system privileges.
- `GRANT`/`REVOKE` at **database, schema, table, column** levels (`GRANT SELECT (name, city) ON customers TO ROLE support;`).
- **Default privileges** (`ALTER DEFAULT PRIVILEGES`) so new tables automatically get the right grants.
- **Row-level security (RLS)** policies: `CREATE RLS POLICY … USING (region = current_user_region)` attached to tables and roles.
- **Dynamic data masking** policies (see 4.3).
- **IAM Identity Center integration**: users sign in with corporate identities, and their groups map to Redshift roles.

### Lake Formation permissions (skill 4.2.4)

**Why Lake Formation:** managing access to a data lake with S3 bucket policies + IAM gets unmanageable at table/column level. Lake Formation provides **database-style grants** on catalog resources and enforces them across engines.

**How it works:**
1. **Register S3 locations** with Lake Formation (it then vends temporary credentials to integrated engines).
2. Grant permissions on **databases, tables, columns** (`SELECT`, `INSERT`, `ALTER`, `DROP`, `DESCRIBE`, plus grantable options) to IAM principals, Identity Center users/groups, or external accounts.
3. Engines that integrate (**Athena, Redshift Spectrum, EMR, Glue Extract, Transform, Load (ETL), QuickSight via Athena**) enforce those permissions.

| Feature | Explanation |
|---|---|
| **Column-level security** | Include/exclude columns in the grant |
| **Data filters** | **Row-level** (filter expression, e.g., `country = 'US'`) and **cell-level** (rows + columns) security |
| **Lake Formation Tag-Based Access Control (LF-TBAC)** (tag-based access control) | Assign **Lake Formation tags (LF-tags)** (e.g., `classification=confidential`, `domain=sales`) to databases/tables/columns and grant on tag expressions. Scales to thousands of tables, and new tables inherit access when tagged. |
| **Cross-account sharing** | Share databases/tables with other accounts (via AWS Resource Access Manager (RAM)). The consumer creates a **resource link**. |
| **Data lake administrators** | Principals who manage permissions |
| **Hybrid access mode / IAMAllowedPrincipals** | Transition from IAM-only to Lake Formation permissions without breaking existing users |

> If Lake Formation is enabled but users still get access they shouldn't, check the default **IAMAllowedPrincipals** grant ("Use only IAM access control" settings).

### Role-, tag-, and attribute-based authorization (skill 4.2.5)

| Model | How | Best for |
|---|---|---|
| **RBAC** (role-based) | Permissions attached to roles (job functions); users assume roles | Stable teams and job functions; simple |
| **TBAC** (tag-based, e.g., **Lake Formation LF-tags**) | Resources tagged; grants written on tag values | Large, growing catalogs: grant once on `domain=sales`, new tables inherit |
| **ABAC** (attribute-based, IAM) | Policies compare **principal tags** to **resource tags** (`"aws:ResourceTag/project": "${aws:PrincipalTag/project}"`) | Many teams/projects with fewer policies; access follows attributes automatically |

---

## Task 4.3: Ensure data encryption and masking

### Masking and anonymization (skill 4.3.1)

| Technique | What it does | Reversible? |
|---|---|---|
| **Masking / redaction** | Hide all or part of a value (`***-**-1234`) | No (for the viewer) |
| **Hashing** (salted) | Replace value with a hash; joins still work | No |
| **Tokenization** | Replace with a token; the mapping is stored securely | Yes, with the vault |
| **Encryption** (deterministic or probabilistic) | Ciphertext; deterministic keeps joinability | Yes, with the key |
| **Generalization** | Reduce precision (age → age band, ZIP → first 3 digits) | No |
| **Pseudonymization** vs **anonymization** | Pseudonymized data can be re-identified with extra info (still personal data under General Data Protection Regulation (GDPR)); anonymized data cannot | — |

**AWS tools:**
- **Redshift dynamic data masking**: masking policies applied at query time based on role (analysts see masked Social Security Number (SSN); auditors see full).
- **Lake Formation**: exclude sensitive columns or use cell-level filters.
- **Glue sensitive data detection**: find PII in ETL jobs and **redact/hash/replace** it.
- **DataBrew**: masking, hashing, deterministic/probabilistic encryption, substitution transforms.
- **Amazon Comprehend**: detect and redact PII in free text.
- **QuickSight**: column-level security.
- **Macie** **finds** PII in S3 but **does not mask** it.

### Encryption with KMS (skill 4.3.2)

**KMS key types:**

| Key | Who manages | Key policy editable | Cross-account usable | Rotation |
|---|---|---|---|---|
| **AWS owned** | AWS (shared across accounts) | ❌ | ❌ | AWS |
| **AWS managed** (`aws/s3`, `aws/redshift`…) | AWS, in your account | ❌ | ❌ | Automatic (yearly) |
| **Customer managed** | You | ✅ | ✅ | Optional automatic (configurable period) or manual |

- **Envelope encryption**: KMS generates a **data key**, data is encrypted locally with the data key, and the data key is stored encrypted with the KMS key. This keeps large data out of KMS calls (KMS encrypts at most 4 KB directly).
- **Grants**: temporary, programmatic permissions to use a key (used by services like Elastic Block Store (EBS), Redshift).
- **Multi-Region keys**: same key material in several Regions (for replicated encrypted data).
- **Imported key material** / **external key store** for strict key-control requirements.

**Encryption at rest by service:**

| Service | Options |
|---|---|
| **S3** | **Server-Side Encryption with S3-managed keys (SSE-S3)** (default for all new objects), **Server-Side Encryption with KMS keys (SSE-KMS)** (audit key use in CloudTrail, key policies), **DSSE-KMS** (dual-layer), **Server-Side Encryption with Customer-provided keys (SSE-C)** (customer-provided keys), client-side. **S3 Bucket Keys** cut KMS request costs for SSE-KMS. Enforce with default encryption + bucket policy. |
| **Redshift** | KMS (or Hardware Security Module (HSM)) encryption for cluster, snapshots, backups; can encrypt an existing cluster |
| **Glue** | **Security configurations** (encrypt S3 output, CloudWatch logs, job bookmarks) + **Data Catalog encryption** (metadata and connection passwords) |
| **Athena** | Query results encryption (SSE-S3, SSE-KMS, Client-Side Encryption with KMS keys (CSE-KMS)), enforced by **workgroup** |
| **EMR** | **Security configuration**: at-rest (EBS/local disk, EMR File System (EMRFS) S3), in-transit (TLS) |
| **Kinesis / Firehose / MSK** | Server-side encryption with KMS |
| **DynamoDB, RDS, Aurora** | KMS at rest (RDS encryption must be chosen at creation; to encrypt an existing DB, snapshot → copy encrypted → restore) |

### Cross-account encryption (skill 4.3.3)

To let account B read KMS-encrypted data owned by account A:
1. Use a **customer managed key** in account A. **AWS managed keys (`aws/s3`) can't be shared**, so objects encrypted with them can't be decrypted by another account.
2. The **key policy** in account A allows account B (or a specific role) `kms:Decrypt` (and `kms:GenerateDataKey` for writes, `kms:DescribeKey`).
3. Account B's **IAM policy** allows the same KMS actions on that key ARN.
4. The **resource** (bucket policy, Secrets Manager resource policy, etc.) also allows account B.

Also: **cross-account S3 replication** of SSE-KMS objects needs the replication role to decrypt with the source key and encrypt with the destination key. **Redshift cross-Region snapshot copy** of KMS-encrypted clusters needs a **snapshot copy grant** in the destination Region.

### Encryption in transit and before transit (skill 4.3.4)

**In transit (TLS):**
- AWS service endpoints use Hypertext Transfer Protocol Secure (HTTPS)/TLS. **Enforce** it with bucket policies denying requests where **`aws:SecureTransport` = false**.
- Redshift: parameter **`require_ssl = true`**. RDS PostgreSQL: **`rds.force_ssl = 1`**. MySQL: `REQUIRE SSL` per user. Java Database Connectivity (JDBC)/Open Database Connectivity (ODBC): Secure Sockets Layer (SSL) options.
- EMR security configuration: in-transit TLS between nodes.
- Hybrid networks: Site-to-Site Virtual Private Network (VPN) (IPsec), Direct Connect (+ MACsec or VPN over Direct Connect (DX)).

**Before transit (client-side encryption):**
- Encrypt **before** data leaves the producer, so AWS only ever stores ciphertext.
- Tools: **AWS Encryption Software Development Kit (SDK)**, **Amazon S3 Encryption Client**, **AWS Database Encryption SDK** (DynamoDB attribute-level encryption), using KMS keys (CSE-KMS).
- Use when the requirement says data must be encrypted **before it is sent** or AWS must never see plaintext.

---

## Task 4.4: Prepare logs for audit

### CloudTrail (skill 4.4.1)

- **Management events** (control plane: `CreateTable`, `PutBucketPolicy`, `StartJobRun`) are recorded by default and visible for **90 days** in Event history.
- **Data events** (data plane: S3 `GetObject`/`PutObject`, Lambda `Invoke`, DynamoDB item-level, Glue/Lake Formation data access…) must be **enabled on a trail or event data store**. Use advanced event selectors to limit cost.
- **Trails**: deliver logs to S3 (and optionally CloudWatch Logs) for long-term retention; **organization trails** cover all accounts; **log file integrity validation** detects tampering; encrypt with KMS; protect the log bucket with Object Lock / restricted bucket policy.
- **Insights events**: detect unusual API call rates.
- **Lake Formation** records data access (which principal accessed which table/columns) in CloudTrail.

### CloudWatch Logs for application logs (skill 4.4.2)

- Applications and services write to **log groups**. Set **retention**, **KMS encryption**, and **resource policies**.
- Lambda, Glue, EMR (optional), MWAA, Step Functions, API Gateway, and Redshift audit logs can all send to CloudWatch Logs.
- Centralize across accounts with **subscription filters** → Firehose → S3 in a log archive account, or cross-account log sharing.

### CloudTrail Lake (skill 4.4.3)

- A **managed, immutable event data store** for CloudTrail events (also AWS Config items, audit events from outside AWS) with long retention options.
- Query with **Structured Query Language (SQL)** directly in the console or API. No S3 tables, partitions, or Athena setup required.
- Can collect from **all accounts in an organization** → centralized audit queries ("Which users called `DeleteTable` across all accounts in the last 6 months?").

### Analyzing logs (skills 4.4.4, 4.4.5)

| Need | Tool |
|---|---|
| Ad-hoc queries on CloudWatch log groups | **CloudWatch Logs Insights** |
| SQL over CloudTrail/VPC Flow/S3 access logs in S3 | **Athena** (create table from the CloudTrail console, use partition projection) |
| Real-time search, dashboards, alerting on logs | **OpenSearch Service** (ingest with Firehose or OpenSearch Ingestion) |
| SQL over CloudTrail events with no setup | **CloudTrail Lake** |
| **Very large log volumes**, complex processing | **EMR** (Spark over logs in S3) |
| Security findings correlation | Security Hub, GuardDuty (beyond core scope) |

---

## Task 4.5: Understand data privacy and governance

### Data sharing permissions (skill 4.5.1)

**Redshift data sharing:**
- The producer creates a **datashare**, adds schemas/tables/views/User-Defined Functions (UDFs), and grants it to a consumer **namespace** (same account), **AWS account** (cross-account: the producer account must **authorize** it and the consumer account must **associate** it), or Region.
- The consumer creates a **database from the datashare** and queries **live data with no copies** and no ETL. Consumer compute pays for its queries.
- Requires **RA3 or Redshift Serverless**. Can be **managed by Lake Formation** (centralized fine-grained permissions on the shared data) or shared via **AWS Data Exchange** (paid/licensed sharing).
- Multi-warehouse **writes** are supported for workload isolation.

**Other sharing mechanisms:** Lake Formation cross-account grants (via RAM), S3 bucket policies/Access Points, AWS Data Exchange (subscribe/license external data), **AWS Clean Rooms** (collaborative analysis without sharing raw data), SageMaker Catalog subscriptions.

### PII identification (skill 4.5.2)

**Amazon Macie:**
- Uses Machine Learning (ML) and pattern matching to discover sensitive data **in S3**: **managed data identifiers** (names, addresses, credit cards, passport numbers, credentials…) plus **custom data identifiers** (regex + keywords for your own formats like employee IDs).
- **Automated sensitive data discovery** (continuous sampling across buckets) or targeted **sensitive data discovery jobs** (one-time or scheduled).
- Also evaluates bucket security (public, unencrypted, shared).
- **Findings** go to EventBridge and Security Hub, which can trigger remediation.

**Macie + Lake Formation pattern:**

```
Macie job scans the S3 data lake ──► finding: PII in s3://lake/customers/ (column-level details)
   └─► EventBridge ──► Lambda ──► apply LF-tag classification=PII to the table/columns
                                     └─► Lake Formation grants: only roles with PII clearance can SELECT those columns
```

Other PII detection: **Glue sensitive data detection** (inside ETL), **Comprehend** (free text), **DataBrew** PII detection.

### Preventing backups/replication to disallowed Regions (skill 4.5.3)

- **SCPs** in AWS Organizations: deny all actions outside approved Regions using **`aws:RequestedRegion`** (exempt global services). This blocks creating resources, snapshot copies, and replicas elsewhere.
- Deny specific actions: `s3:PutReplicationConfiguration` (or limit allowed destination buckets), `rds:CopyDBSnapshot`/cross-Region read replicas, `redshift:EnableSnapshotCopy`, DynamoDB global table replica creation, `backup:StartCopyJob` to disallowed vaults.
- **AWS Backup**: organization **backup policies** that define where copies go; vault access policies.
- **AWS Control Tower** Region deny control (applies the same Service Control Policy (SCP) approach at scale).
- **KMS**: single-Region customer managed keys mean data encrypted with them can't be decrypted elsewhere.

### Viewing configuration changes with AWS Config (skill 4.5.4)

- Records **configuration items** for resources (S3 buckets, Redshift clusters, security groups, IAM, KMS keys…) and keeps a **timeline of changes**, linked to the CloudTrail event that caused each change.
- **Config rules** (managed, e.g., `s3-bucket-server-side-encryption-enabled`, `redshift-cluster-public-access-check`, or custom) evaluate compliance continuously; **conformance packs** bundle rules.
- **Remediation** via Systems Manager Automation documents.
- **Aggregators** give a multi-account, multi-Region compliance view.

> CloudTrail = **who did what (API call)**. Config = **what the resource looked like before and after, and whether it's compliant**.

### Data sovereignty (skill 4.5.5)

**Data sovereignty** = data is subject to the laws of the country where it's stored. Requirements often mean data (and sometimes keys and operators) must stay in a specific country or jurisdiction.

How to maintain it on AWS:
- Choose Regions in the required country; **restrict other Regions** with SCPs (`aws:RequestedRegion`).
- Block cross-Region replication, snapshot copy, and global tables to other jurisdictions (see 4.5.3).
- Keep **KMS keys in-Region** (or customer-controlled key stores/Hardware Security Modules (HSMs) for stricter control).
- Watch for services that move data (cross-Region inference in Bedrock, CloudFront caching, global tables) and configure them for in-country use.
- Use **AWS Local Zones / Outposts / Dedicated Local Zones** when no Region exists in the required location.
- Use AWS Config rules and Macie/CloudTrail to prove compliance.

### 🆕 Managing access through SageMaker Catalog projects (skill 4.5.6)

```
Producer project publishes asset "sales.orders" to SageMaker Catalog
        │
Consumer (member of project "Marketing Analytics") finds it via search/glossary
        │
Consumer requests a subscription (with business justification)
        │
Asset owner (or approver) approves
        │
Access is fulfilled automatically: Lake Formation grant (Glue tables) or Redshift grant (Redshift tables) to the CONSUMER PROJECT's role
        │
All members of the consumer project can query it (Athena, Redshift, notebooks); revoking the subscription removes access
```

Key points:
- Access is granted to **projects**, not to individual users, so team membership changes don't require new grants.
- Subscriptions are **auditable** (who requested, who approved, when).
- Domain units can set **policies** controlling who can publish and who can approve.

### 🆕 Governance frameworks and data sharing patterns (skill 4.5.7)

**Governance frameworks:**

| Model | How it works | Pros / cons |
|---|---|---|
| **Centralized** | One central data team owns the lake/warehouse, ingestion, and all permissions | Consistent and simple; central team becomes a bottleneck |
| **Decentralized / data mesh** | **Domain teams own their data as products** (they publish to a catalog); a **central governance** layer sets standards (catalog, policies, security) | Scales with the organization; needs strong standards and a catalog |
| **Federated / hub-and-spoke** | Central **governance/catalog account** + **producer** and **consumer** accounts; Lake Formation + RAM share tables across accounts; SageMaker Catalog for discovery and subscriptions | AWS's reference architecture for multi-account data platforms |

A governance framework covers **ownership/stewardship**, **classification** (public, internal, confidential, PII), **access policies**, **quality standards**, **lineage**, **lifecycle/retention**, and **auditing**.

**Data sharing patterns:**

| Pattern | Example | Trade-off |
|---|---|---|
| **Copy/replicate** | ETL into a consumer's bucket/warehouse, S3 replication | Independent copies; duplication, staleness, harder governance |
| **Zero-copy, in-place sharing** | Redshift data sharing, Lake Formation cross-account grants, S3 Access Points | Live data, no duplication, central control |
| **Publish/subscribe via catalog** | SageMaker Catalog subscriptions | Self-service with approval and audit |
| **Marketplace / licensed** | AWS Data Exchange | Monetize or consume third-party data |
| **Privacy-preserving collaboration** | AWS Clean Rooms | Joint analysis without exposing raw records |

---

## Gotchas and exam traps

- **Apps should use IAM roles** (temporary credentials), not IAM user access keys.
- **Glue can't connect in a VPC** → missing **self-referencing security group** rule.
- **"AccessDenied when creating a Glue job / Lambda with a role"** → missing **`iam:PassRole`**.
- **Automatic credential rotation** → **Secrets Manager** (not Parameter Store).
- **Managed policy too broad** → **customer managed policy** with specific actions, ARNs, and conditions; generate it from activity with **IAM Access Analyzer**.
- **S3 `ListBucket`** goes on the **bucket ARN**, **`GetObject`** on **`bucket/*`**.
- **SCPs and permission boundaries never grant** permissions; they only limit. **Explicit Deny wins.**
- **Table/column/row permissions across Athena, Redshift Spectrum, EMR** → **Lake Formation** (data filters for row/cell, LF-tags for scale).
- **Thousands of tables, new ones should inherit access** → **LF-TBAC (LF-tags)**.
- **Fewer IAM policies across many projects/teams** → **ABAC** with principal/resource tags.
- **Analysts see masked Social Security Numbers (SSNs), auditors see full values in Redshift** → **dynamic data masking**.
- **Macie finds PII; it doesn't mask it.**
- **Cross-account decrypt fails** → data encrypted with an **AWS managed key** (`aws/s3`) can't be shared. Use a **customer managed key** + key policy + IAM.
- **Reduce SSE-KMS request costs** → **S3 Bucket Keys**.
- **Enforce TLS to S3** → bucket policy deny on **`aws:SecureTransport` = false**. Redshift → **`require_ssl`**.
- **Encrypt before sending to AWS** → **client-side encryption** (Encryption SDK / S3 Encryption Client).
- **RDS encryption can't be turned on in place** → snapshot, copy encrypted, restore.
- **S3 object-level access auditing** → **CloudTrail data events** (not on by default).
- **Centralized SQL over CloudTrail across the org, no setup** → **CloudTrail Lake**.
- **"Who changed it?"** → CloudTrail. **"What was the configuration and is it compliant?"** → **AWS Config**.
- **Share live Redshift data with another account, no copies** → **Redshift data sharing** (RA3/Serverless; authorize + associate).
- **Block backups/replicas outside approved Regions** → **SCP with `aws:RequestedRegion`** (+ deny replication/snapshot-copy actions).
- **SageMaker Catalog access is granted to projects** via subscription approval, not individual users.
- **Domain teams own data products with central governance** → **data mesh** (federated, hub-and-spoke on AWS).

---

## Quick-recall summary

- Domain weight **18%**. Tasks: authentication (4.1), authorization (4.2), encryption/masking (4.3), audit logs (4.4), privacy/governance (4.5).
- Auth methods: password, certificate, **role-based (STS temporary credentials)**; Identity Center for workforce.
- **Security groups** stateful, allow-only, can reference Security Groups (SGs); **Network Access Control Lists (NACLs)** stateless, allow + deny.
- Roles: trust policy + permissions; Lambda execution role, Glue service role, CloudFormation service role, EC2 instance profile; **`iam:PassRole`**.
- **VPC endpoints**: gateway (S3, DynamoDB) vs interface (PrivateLink); endpoint policies; `aws:SourceVpce`.
- **S3 Access Points**: per-app policies, VPC-only option.
- **Secrets Manager** (rotation, cross-account) vs **Parameter Store** (SecureString, free, no rotation); Redshift/RDS IAM-based temporary credentials.
- Managed vs unmanaged = how much of the shared responsibility AWS carries.
- **SageMaker Unified Studio**: **domain** (top boundary, Identity Center) → **domain units** (hierarchy + policies) → **projects** (team workspace, own IAM role, unit of access).
- Policies: AWS managed vs customer managed vs inline; least privilege via actions + ARNs + conditions; **IAM Access Analyzer**; SCPs/boundaries limit only; explicit Deny wins.
- **Redshift**: RBAC roles, GRANT to column level, default privileges, **RLS**, **dynamic data masking**, Identity Center.
- **Lake Formation**: register S3, grants on db/table/column, **data filters** (row/cell), **LF-tags (TBAC)**, cross-account via RAM + resource links, IAMAllowedPrincipals.
- RBAC (roles) vs TBAC (LF-tags) vs **ABAC** (principal tag = resource tag).
- Masking/anonymization: redact, hash, tokenize, encrypt, generalize; pseudonymized ≠ anonymized; tools = Redshift Dynamic Data Masking (DDM), Lake Formation (LF), Glue sensitive data detection, DataBrew, Comprehend.
- **KMS**: AWS owned / AWS managed / **customer managed** (only Customer Managed Key (CMK) is shareable cross-account, editable policy); envelope encryption; grants; multi-Region keys.
- S3 at rest: **SSE-S3 default**, SSE-KMS (+ **Bucket Keys**), DSSE-KMS, SSE-C, client-side.
- Service encryption: Glue security configurations + catalog encryption, Athena workgroup result encryption, EMR security configurations, Redshift KMS, RDS at creation only.
- Cross-account: CMK key policy + consumer IAM + resource policy; Redshift snapshot copy grant.
- Transit: TLS, **`aws:SecureTransport`**, `require_ssl`, `rds.force_ssl`; **before transit = client-side encryption**.
- **CloudTrail**: management events default (90 days), **data events opt-in**, trails/org trails, integrity validation; **CloudTrail Lake** = SQL, central, immutable.
- **CloudWatch Logs**: retention, KMS, subscriptions to centralize.
- Log analysis: Logs Insights, Athena, OpenSearch, CloudTrail Lake, **EMR for huge volumes**.
- **Redshift data sharing**: datashare → consumer database, no copy, RA3/Serverless, cross-account authorize + associate, LF-managed or Data Exchange.
- **Macie**: managed + custom identifiers, automated discovery, findings → EventBridge → tag in **Lake Formation**.
- Region restriction: **SCP `aws:RequestedRegion`**, deny replication/snapshot copy, Backup policies, Control Tower.
- **AWS Config**: configuration timeline, rules, conformance packs, aggregators, remediation.
- Sovereignty: in-country Regions, SCPs, in-Region keys, no cross-Region replication, Local Zones/Outposts.
- **SageMaker Catalog projects**: publish → request → approve → automatic LF/Redshift grant to the project.
- Governance: centralized vs **data mesh** vs hub-and-spoke; sharing: copy vs **zero-copy** vs catalog subscribe vs Data Exchange vs Clean Rooms.
