# DEA-C01 Cheat Sheet

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> <b>O</b>ne-<b>pa</b>ge <b>rev</b>iew <b>f</b>or <b>t</b>he <b>la</b>st 48 <b>hou</b>rs <b>bef</b>ore <b>t</b>he <b>ex</b>am.

## Keyword → answer decoder

| <b>I</b>f <b>t</b>he <b>ques</b>tion <b>sa</b>ys… | <b>Thi</b>nk… |
|---|---|
| <b>Re</b>al <b>ti</b>me, <b>mult</b>iple <b>consu</b>mers, <b>rep</b>lay, <b>orde</b>ring | **[Kinesis Data Streams](00-data-basics-for-beginners.md#amazon-kinesis-data-streams)** |
| <b>Ne</b>ar <b>re</b>al <b>ti</b>me, <b>deli</b>ver <b>t</b>o [S3](00-data-basics-for-beginners.md#amazon-s3)/<b>Reds</b>hift/<b>OpenS</b>earch, <b>lea</b>st <b>o</b>ps | **[Amazon Data Firehose](00-data-basics-for-beginners.md#amazon-data-firehose)** |
| [<b>Kaf</b>ka](00-data-basics-for-beginners.md#apache-kafka), <b>exis</b>ting <b>Kaf</b>ka <b>clie</b>nts | **Amazon [Managed Streaming for Apache Kafka [MSK]](00-data-basics-for-beginners.md#amazon-msk)** (<b>Serve</b>rless <b>f</b>or <b>n</b>o <b>siz</b>ing) |
| <b>Wind</b>owed <b>aggreg</b>ations / <b>stat</b>eful <b>str</b>eam <b>proce</b>ssing | **[Managed Service for Apache Flink](00-data-basics-for-beginners.md#managed-service-for-apache-flink)** |
| <b>Data</b>base <b>migra</b>tion, <b>Cha</b>nge <b>Da</b>ta <b>Capt</b>ure (CDC) | **Amazon Web Services (AWS) [Database Migration Service [DMS]](00-data-basics-for-beginners.md#aws-dms)** (+ DMS <b>Sch</b>ema <b>Conve</b>rsion <b>f</b>or <b>heterog</b>eneous) |
| <b>Data</b>base (DB) → [<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift) <b>wi</b>th <b>n</b>o <b>pipe</b>line | **[Zero-ETL](00-data-basics-for-beginners.md#zero-etl-integrations) integration** |
| <b>Soft</b>ware <b>a</b>s <b>a</b> <b>Serv</b>ice (<b>Sa</b>aS) <b>sou</b>rce ([<b>Sales</b>force](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce), <b>Zend</b>esk…) | **[Amazon AppFlow](00-data-basics-for-beginners.md#amazon-appflow)** |
| <b>O</b>n-<b>pr</b>em <b>Netw</b>ork <b>Fi</b>le <b>Sys</b>tem (NFS)/<b>Ser</b>ver <b>Mess</b>age <b>Blo</b>ck (SMB) <b>t</b>o <b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice (S3) | **[AWS DataSync](00-data-basics-for-beginners.md#aws-datasync)** |
| <b>Part</b>ners <b>upl</b>oad <b>ov</b>er SSH <b>Fi</b>le <b>Tran</b>sfer <b>Prot</b>ocol (SFTP) | **[AWS Transfer Family](00-data-basics-for-beginners.md#aws-transfer-family)** |
| <b>Petab</b>ytes <b>offl</b>ine | **[Snow Family](00-data-basics-for-beginners.md#aws-snow-family)** |
| <b>Thi</b>rd-<b>par</b>ty <b>data</b>sets | **[AWS Data Exchange](00-data-basics-for-beginners.md#aws-data-exchange)** |
| <b>Serve</b>rless [<b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark) <b>Extr</b>act, <b>Trans</b>form, <b>Lo</b>ad (ETL) | **[AWS Glue](00-data-basics-for-beginners.md#aws-glue)** |
| <b>Proc</b>ess <b>on</b>ly <b>n</b>ew <b>da</b>ta | **Glue job bookmarks** |
| <b>N</b>on-<b>urg</b>ent <b>j</b>ob, <b>chea</b>per | **Glue Flex** |
| <b>N</b>o-<b>co</b>de <b>da</b>ta <b>pr</b>ep <b>f</b>or <b>anal</b>ysts | **[Glue DataBrew](00-data-basics-for-beginners.md#aws-glue-databrew)** |
| <b>Fuz</b>zy <b>ded</b>up <b>with</b>out <b>exa</b>ct <b>k</b>ey | **Glue FindMatches** |
| <b>Fu</b>ll [<b>Had</b>oop](00-data-basics-for-beginners.md#apache-hadoop) <b>ecosy</b>stem, <b>Sp</b>ot | **Amazon [Elastic MapReduce [EMR]](00-data-basics-for-beginners.md#amazon-emr)** (<b>Sp</b>ot <b>o</b>n **task** <b>nod</b>es) |
| [<b>Struc</b>tured <b>Que</b>ry <b>Lang</b>uage [SQL]](00-data-basics-for-beginners.md#sql) <b>o</b>n S3, <b>p</b>ay <b>p</b>er <b>que</b>ry | **[Athena](00-data-basics-for-beginners.md#amazon-athena)** |
| <b>Peta</b>byte <b>wareh</b>ouse, <b>Busi</b>ness <b>Intell</b>igence (BI) | **Redshift** |
| <b>Que</b>ry S3 <b>fr</b>om <b>Reds</b>hift | **Redshift Spectrum** |
| <b>Que</b>ry <b>li</b>ve [RDS](00-data-basics-for-beginners.md#amazon-rds)/<b>Aur</b>ora <b>fr</b>om <b>Reds</b>hift | **Federated query** |
| <b>Sha</b>re <b>Reds</b>hift <b>da</b>ta <b>with</b>out <b>copy</b>ing | **Redshift data sharing** |
| <b>Upda</b>tes/<b>dele</b>tes/<b>ti</b>me <b>tra</b>vel <b>o</b>n S3 | **[Apache Iceberg](00-data-basics-for-beginners.md#apache-iceberg)** |
| <b>Mana</b>ged <b>Iceb</b>erg, <b>autom</b>atic <b>compa</b>ction | **[Amazon S3 Tables](00-data-basics-for-beginners.md#amazon-s3-tables)** |
| <b>Vec</b>tor <b>sea</b>rch <b>wi</b>th SQL/<b>relat</b>ional <b>da</b>ta | **[Aurora](00-data-basics-for-beginners.md#amazon-aurora) [PostgreSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server) + pgvector (Hierarchical Navigable Small World [HNSW])** |
| <b>Hyb</b>rid <b>keyw</b>ord + <b>vec</b>tor <b>sea</b>rch | **[OpenSearch](00-data-basics-for-beginners.md#amazon-opensearch-service)** |
| <b>Micros</b>econd [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb) <b>rea</b>ds | **DynamoDB Accelerator (DAX)** |
| <b>Dura</b>ble <b>i</b>n-<b>mem</b>ory <b>k</b>ey/<b>val</b>ue | **[MemoryDB](00-data-basics-for-beginners.md#amazon-memorydb-and-elasticache)** |
| <b>Retri</b>eval-<b>Augme</b>nted <b>Gener</b>ation (RAG) <b>da</b>ta <b>pipe</b>line, <b>mana</b>ged | **[Bedrock](00-data-basics-for-beginners.md#amazon-bedrock) Knowledge Bases** |
| <b>Lar</b>ge <b>Lang</b>uage <b>Mod</b>el (LLM) <b>ov</b>er <b>a</b> <b>lar</b>ge <b>bat</b>ch <b>o</b>f <b>reco</b>rds, <b>che</b>ap | **Bedrock batch inference** |
| <b>Serve</b>rless <b>work</b>flow <b>acr</b>oss AWS <b>serv</b>ices | **[Step Functions](00-data-basics-for-beginners.md#aws-step-functions)** |
| <b>Exis</b>ting [<b>Airf</b>low](00-data-basics-for-beginners.md#apache-airflow) <b>Dire</b>cted <b>Acyc</b>lic <b>Gra</b>phs (DAGs) | **[Managed Workflows for Apache Airflow [MWAA]](00-data-basics-for-beginners.md#amazon-mwaa)** |
| <b>On</b>ly <b>Gl</b>ue <b>jo</b>bs <b>a</b>nd <b>craw</b>lers | **Glue workflows** |
| <b>Sta</b>rt <b>pipe</b>line <b>o</b>n <b>fi</b>le <b>arri</b>val | **S3 → [EventBridge](00-data-basics-for-beginners.md#amazon-eventbridge) → Step Functions** |
| <b>Not</b>ify <b>o</b>n <b>fail</b>ure | **EventBridge / [CloudWatch](00-data-basics-for-beginners.md#amazon-cloudwatch) alarm → [Simple Notification Service [SNS]](00-data-basics-for-beginners.md#amazon-sns)** |
| <b>Ma</b>ny <b>Lamb</b>das <b>overw</b>helm <b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice (RDS) | **RDS Proxy** |
| <b>Allow</b>list <b>a</b> <b>fix</b>ed <b>outb</b>ound <b>Inte</b>rnet <b>Prot</b>ocol (IP) | **Network Address Translation (NAT) gateway Elastic IP** |
| <b>Sha</b>red <b>persi</b>stent <b>fil</b>es <b>i</b>n [<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda) | **Elastic File System (EFS) mount** |
| <b>Pack</b>age/<b>dep</b>loy <b>serve</b>rless <b>pipe</b>line | **AWS [Serverless Application Model [SAM]](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam)** |
| <b>Inf</b>ra <b>i</b>n <b>TypeS</b>cript/<b>Pyt</b>hon | **AWS Cloud Development Kit (CDK)** |
| <b>Da</b>ta <b>qual</b>ity <b>rul</b>es <b>i</b>n <b>pipe</b>line | **[Glue Data Quality](00-data-basics-for-beginners.md#aws-glue-data-quality) (Data Quality Definition Language [DQDL])** |
| <b>Da</b>ta <b>qual</b>ity <b>with</b>out <b>co</b>de | **DataBrew rulesets + profile jobs** |
| <b>Unkn</b>own <b>acc</b>ess <b>patt</b>ern <b>stor</b>age | **S3 Intelligent-Tiering** |
| <b>Wri</b>te <b>On</b>ce, <b>Re</b>ad <b>Ma</b>ny (WORM), <b>ev</b>en <b>ro</b>ot <b>can</b>'t <b>del</b>ete | **S3 Object Lock compliance mode** |
| <b>Au</b>to-<b>exp</b>ire <b>Dyna</b>moDB <b>ite</b>ms | **DynamoDB Time To Live (TTL)** |
| <b>Prod</b>ucer <b>sch</b>ema <b>chan</b>ges <b>bre</b>ak <b>consu</b>mers | **Glue Schema Registry** |
| <b>T</b>oo <b>ma</b>ny <b>parti</b>tions, <b>sl</b>ow <b>Ath</b>ena | **Partition projection** |
| <b>Ath</b>ena <b>can</b>'t <b>s</b>ee <b>n</b>ew <b>parti</b>tions | **Metastore Consistency Check (MSCK) REPAIR / ADD PARTITION / projection** |
| <b>W</b>ho <b>d</b>id <b>i</b>t? | **[CloudTrail](00-data-basics-for-beginners.md#aws-cloudtrail)** (S3 <b>obje</b>cts → **data events**) |
| <b>Wh</b>at <b>chan</b>ged / <b>compl</b>iant? | **[AWS Config](00-data-basics-for-beginners.md#aws-config)** |
| SQL <b>ov</b>er <b>aud</b>it <b>eve</b>nts, <b>o</b>rg-<b>wi</b>de | **CloudTrail Lake** |
| <b>Qui</b>ck <b>l</b>og <b>sea</b>rch | **CloudWatch Logs Insights** |
| <b>Rot</b>ate DB <b>passw</b>ords <b>automat</b>ically | **[Secrets Manager](00-data-basics-for-beginners.md#aws-secrets-manager)** |
| <b>Tab</b>le/<b>col</b>umn/<b>r</b>ow <b>permis</b>sions <b>o</b>n <b>t</b>he <b>la</b>ke | **[Lake Formation](00-data-basics-for-beginners.md#aws-lake-formation)** (<b>da</b>ta <b>filt</b>ers) |
| <b>Sca</b>le <b>permis</b>sions <b>ov</b>er <b>thous</b>ands <b>o</b>f <b>tab</b>les | **Lake Formation tags [LF-tags] (Tag-Based Access Control [TBAC])** |
| <b>Mas</b>ked <b>val</b>ues <b>p</b>er <b>ro</b>le <b>i</b>n <b>Reds</b>hift | **Dynamic data masking** |
| <b>Fi</b>nd <b>Perso</b>nally <b>Identi</b>fiable <b>Inform</b>ation (PII) <b>i</b>n S3 | **[Amazon Macie](00-data-basics-for-beginners.md#amazon-macie)** |
| <b>Cro</b>ss-<b>acco</b>unt [<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice [KMS]](00-data-basics-for-beginners.md#aws-kms) | **Customer managed key** + <b>k</b>ey <b>pol</b>icy |
| <b>Enfo</b>rce <b>Hyper</b>text <b>Tran</b>sfer <b>Prot</b>ocol <b>Sec</b>ure (HTTPS) <b>t</b>o S3 | **`aws:SecureTransport` deny** |
| <b>Encr</b>ypt <b>bef</b>ore <b>send</b>ing | **Client-side encryption** |
| <b>Ke</b>ep <b>da</b>ta <b>i</b>n <b>appr</b>oved <b>Regi</b>ons | **Service Control Policy (SCP) `aws:RequestedRegion`** |
| <b>Busi</b>ness <b>cata</b>log, <b>requ</b>est <b>acc</b>ess | **[SageMaker Catalog](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)** |
| <b>O</b>ne <b>works</b>pace <b>f</b>or <b>da</b>ta + <b>Artif</b>icial <b>Intell</b>igence (AI) <b>tea</b>ms | **SageMaker Unified Studio** |

## Numbers to remember

| <b>It</b>em | <b>Val</b>ue |
|---|---|
| <b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams (KDS) <b>sha</b>rd <b>wri</b>te | 1 MB/<b>s</b> <b>o</b>r 1,000 <b>reco</b>rds/<b>s</b> |
| KDS <b>sha</b>rd <b>re</b>ad | 2 MB/<b>s</b> <b>sha</b>red (5 <b>GetRe</b>cords/<b>s</b>); 2 MB/<b>s</b> **per consumer** <b>wi</b>th <b>enha</b>nced <b>f</b>an-<b>o</b>ut |
| KDS <b>reten</b>tion | 24 <b>h</b> <b>defa</b>ult → <b>u</b>p <b>t</b>o 365 <b>da</b>ys |
| <b>Dyna</b>moDB <b>Stre</b>ams <b>reten</b>tion | 24 <b>h</b> |
| <b>Lam</b>bda | 15 <b>m</b>in <b>time</b>out; 128 MB–10,240 MB <b>mem</b>ory; /<b>t</b>mp <b>u</b>p <b>t</b>o 10 GB; <b>Kine</b>sis <b>parallel</b>ization <b>fac</b>tor <b>u</b>p <b>t</b>o 10 |
| <b>St</b>ep <b>Funct</b>ions | <b>Stan</b>dard <b>u</b>p <b>t</b>o 1 <b>ye</b>ar; <b>Expr</b>ess <b>u</b>p <b>t</b>o 5 <b>m</b>in; 256 KB <b>payl</b>oad |
| <b>Fire</b>hose <b>buf</b>fer | 1–128 <b>M</b>iB <b>si</b>ze / <b>inte</b>rval (<b>ze</b>ro <b>buffe</b>ring <b>avail</b>able) |
| S3 <b>requ</b>est <b>ra</b>te | 3,500 <b>wri</b>tes & 5,500 <b>rea</b>ds <b>p</b>er <b>sec</b>ond **per prefix** |
| S3 <b>lifec</b>ycle <b>t</b>o <b>Infre</b>quent <b>Acc</b>ess (IA) | ≥ 30 <b>da</b>ys <b>i</b>n <b>Stan</b>dard |
| S3 <b>mini</b>mum <b>durat</b>ions | IA 30 <b>d</b>; <b>Glac</b>ier <b>Inst</b>ant <b>Retri</b>eval (<b>Glac</b>ier IR)/<b>Flex</b>ible 90 <b>d</b>; <b>De</b>ep <b>Arch</b>ive 180 <b>d</b> |
| <b>De</b>ep <b>Arch</b>ive <b>retri</b>eval | 12–48 <b>h</b> |
| <b>Dyna</b>moDB <b>it</b>em <b>m</b>ax | 400 KB |
| <b>Dyna</b>moDB <b>Poi</b>nt-<b>I</b>n-<b>Ti</b>me <b>Reco</b>very (PITR) | 35 <b>da</b>ys |
| <b>Reds</b>hift <b>autom</b>ated <b>snaps</b>hots | 1-<b>d</b>ay <b>defa</b>ult, <b>u</b>p <b>t</b>o 35 <b>da</b>ys |
| <b>Cloud</b>Trail <b>Eve</b>nt <b>hist</b>ory | 90 <b>da</b>ys |
| <b>Ide</b>al <b>analy</b>tics <b>fi</b>le <b>si</b>ze | 128 MB – 1 GB |
| <b>Ex</b>am | 65 <b>Q</b>s (50 <b>sco</b>red), 130 <b>m</b>in, <b>pa</b>ss 720 |

## Common "least operational overhead" winners
<b>Fire</b>hose > KDS + <b>cus</b>tom <b>co</b>de · <b>Gl</b>ue > EMR · <b>Ath</b>ena > EMR <b>f</b>or SQL · <b>Reds</b>hift <b>Serve</b>rless > <b>provis</b>ioned <b>f</b>or <b>spi</b>ky <b>u</b>se · <b>AppF</b>low > <b>cus</b>tom [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>face [API]](00-data-basics-for-beginners.md#api) <b>co</b>de · <b>St</b>ep <b>Funct</b>ions > <b>cus</b>tom <b>orchest</b>ration <b>o</b>n <b>Elas</b>tic <b>Comp</b>ute <b>Clo</b>ud (EC2) · S3 <b>Tab</b>les > <b>se</b>lf-<b>maint</b>ained <b>Iceb</b>erg · <b>Ze</b>ro-ETL > DMS + <b>Gl</b>ue <b>f</b>or <b>suppo</b>rted <b>sour</b>ces · <b>Mana</b>ged <b>serv</b>ices > <b>se</b>lf-<b>mana</b>ged <b>o</b>n EC2.
