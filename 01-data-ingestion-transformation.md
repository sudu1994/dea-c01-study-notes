# Domain 1: Data Ingestion and Transformation (34%)

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> **The largest domain. Roughly 17 of the 50 scored questions.**
>
> <b>Th</b>is <b>dom</b>ain <b>tes</b>ts <b>h</b>ow <b>da</b>ta <b>ge</b>ts *<b>in</b>to* <b>Ama</b>zon <b>W</b>eb <b>Serv</b>ices [AWS] (<b>strea</b>ming <b>a</b>nd <b>bat</b>ch), <b>h</b>ow <b>i</b>t <b>ge</b>ts *<b>resh</b>aped* ([<b>Gl</b>ue](00-data-basics-for-beginners.md#aws-glue), [<b>Elas</b>tic <b>MapRe</b>duce [EMR]](00-data-basics-for-beginners.md#amazon-emr), [<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda), [<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift), <b>conta</b>iners, <b>Lar</b>ge <b>Lang</b>uage <b>Mod</b>els [LLMs]), <b>h</b>ow <b>t</b>he <b>ste</b>ps <b>a</b>re *<b>orches</b>trated* ([<b>St</b>ep <b>Funct</b>ions](00-data-basics-for-beginners.md#aws-step-functions), [<b>Mana</b>ged <b>Workf</b>lows <b>f</b>or <b>Apa</b>che <b>Airf</b>low [MWAA]](00-data-basics-for-beginners.md#amazon-mwaa), <b>Gl</b>ue <b>workf</b>lows, [<b>EventB</b>ridge](00-data-basics-for-beginners.md#amazon-eventbridge)), <b>a</b>nd <b>t</b>he *<b>progra</b>mming <b>pract</b>ices* <b>beh</b>ind <b>i</b>t (<b>Lam</b>bda <b>tun</b>ing, <b>Infrast</b>ructure <b>a</b>s <b>Co</b>de [<b>I</b>aC], [<b>Serve</b>rless <b>Applic</b>ation <b>Mod</b>el [SAM]](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam), <b>Conti</b>nuous <b>Integr</b>ation / <b>Conti</b>nuous <b>Deli</b>very [CI/CD], <b>distri</b>buted <b>compu</b>ting). <b>Mo</b>st <b>quest</b>ions <b>a</b>re "<b>pi</b>ck <b>t</b>he <b>rig</b>ht <b>serv</b>ice/<b>configu</b>ration <b>wi</b>th <b>t</b>he <b>lea</b>st <b>operat</b>ional <b>over</b>head."

## Table of contents

- [<b>Ex</b>am <b>tas</b>ks <b>a</b>nd <b>ski</b>lls](#exam-tasks-and-skills)
- [<b>Ta</b>sk 1.1: <b>Perf</b>orm <b>da</b>ta <b>inges</b>tion](#task-11-perform-data-ingestion)
- [<b>Ta</b>sk 1.2: <b>Trans</b>form <b>a</b>nd <b>proc</b>ess <b>da</b>ta](#task-12-transform-and-process-data)
- [<b>Ta</b>sk 1.3: <b>Orches</b>trate <b>da</b>ta <b>pipel</b>ines](#task-13-orchestrate-data-pipelines)
- [<b>Ta</b>sk 1.4: <b>App</b>ly <b>progra</b>mming <b>conc</b>epts](#task-14-apply-programming-concepts)
- [<b>Gotc</b>has <b>a</b>nd <b>ex</b>am <b>tra</b>ps](#gotchas-and-exam-traps)
- [<b>Qui</b>ck-<b>rec</b>all <b>summ</b>ary](#quick-recall-summary)

## Exam tasks and skills

> <b>Summa</b>rized <b>fr</b>om <b>t</b>he <b>offi</b>cial AWS <b>Certi</b>fied <b>Da</b>ta <b>Engi</b>neer – <b>Assoc</b>iate (DEA-C01) <b>ex</b>am <b>gui</b>de (v1.1). <b>Re</b>ad <b>t</b>he <b>exa</b>ct <b>word</b>ing <b>a</b>t https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain1.html

### Task 1.1: Perform data ingestion
- **1.1.1** <b>Re</b>ad <b>fr</b>om <b>strea</b>ming <b>sour</b>ces ([<b>Kine</b>sis](00-data-basics-for-beginners.md#amazon-kinesis-data-streams), [<b>Mana</b>ged <b>Strea</b>ming <b>f</b>or <b>Apa</b>che <b>Kaf</b>ka [MSK]](00-data-basics-for-beginners.md#amazon-msk), [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb) <b>Stre</b>ams, [<b>Data</b>base <b>Migra</b>tion <b>Serv</b>ice [DMS]](00-data-basics-for-beginners.md#aws-dms), <b>Gl</b>ue, <b>Reds</b>hift).
- **1.1.2** <b>Re</b>ad <b>fr</b>om <b>bat</b>ch <b>sour</b>ces ([<b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice [S3]](00-data-basics-for-beginners.md#amazon-s3), <b>Gl</b>ue, EMR, DMS, <b>Reds</b>hift, <b>Lam</b>bda, [<b>AppF</b>low](00-data-basics-for-beginners.md#amazon-appflow)).
- **1.1.3** <b>Confi</b>gure <b>bat</b>ch <b>inges</b>tion <b>appropr</b>iately.
- **1.1.4** <b>Cons</b>ume <b>da</b>ta [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>faces [APIs]](00-data-basics-for-beginners.md#api).
- **1.1.5** <b>S</b>et <b>u</b>p <b>sched</b>ulers (<b>EventB</b>ridge, [<b>Airf</b>low](00-data-basics-for-beginners.md#apache-airflow), <b>ti</b>me-<b>bas</b>ed <b>sched</b>ules <b>f</b>or <b>jo</b>bs <b>a</b>nd <b>craw</b>lers).
- **1.1.6** <b>S</b>et <b>u</b>p <b>eve</b>nt <b>trig</b>gers (S3 <b>Eve</b>nt <b>Notific</b>ations, <b>EventB</b>ridge).
- **1.1.7** <b>Inv</b>oke <b>Lam</b>bda <b>fr</b>om <b>Kine</b>sis.
- **1.1.8** <b>Cre</b>ate <b>Inte</b>rnet <b>Prot</b>ocol (IP) <b>allow</b>lists <b>s</b>o <b>connec</b>tions <b>t</b>o <b>da</b>ta <b>sour</b>ces <b>a</b>re <b>permi</b>tted.
- **1.1.9** <b>Han</b>dle <b>throt</b>tling <b>a</b>nd <b>ra</b>te <b>lim</b>its (<b>Dyna</b>moDB, [<b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice [RDS]](00-data-basics-for-beginners.md#amazon-rds), <b>Kine</b>sis).
- **1.1.10** <b>Man</b>age <b>f</b>an-<b>i</b>n <b>a</b>nd <b>f</b>an-<b>o</b>ut <b>f</b>or <b>strea</b>ming <b>distri</b>bution.
- **1.1.11** <b>Desc</b>ribe <b>replaya</b>bility <b>o</b>f <b>inges</b>tion <b>pipel</b>ines.
- **1.1.12** <b>Def</b>ine <b>stat</b>eful <b>v</b>s <b>state</b>less <b>da</b>ta <b>transa</b>ctions.

### Task 1.2: Transform and process data
- **1.2.1** <b>Opti</b>mize <b>conta</b>iner <b>usa</b>ge <b>f</b>or <b>perfor</b>mance (<b>Elas</b>tic <b>Kuber</b>netes <b>Serv</b>ice [EKS], [<b>Elas</b>tic <b>Conta</b>iner <b>Serv</b>ice [ECS]](00-data-basics-for-beginners.md#amazon-ecs-eks-and-fargate)).
- **1.2.2** <b>Conn</b>ect <b>t</b>o <b>da</b>ta <b>sour</b>ces (<b>Ja</b>va <b>Data</b>base <b>Connec</b>tivity [JDBC], [<b>Op</b>en <b>Data</b>base <b>Connec</b>tivity [ODBC]](00-data-basics-for-beginners.md#jdbc-and-odbc)).
- **1.2.3** <b>Integ</b>rate <b>da</b>ta <b>fr</b>om <b>mult</b>iple <b>sour</b>ces.
- **1.2.4** <b>Opti</b>mize <b>proce</b>ssing <b>cos</b>ts.
- **1.2.5** <b>Cho</b>ose <b>transfo</b>rmation <b>serv</b>ices <b>b</b>y <b>requir</b>ement (EMR, <b>Gl</b>ue, <b>Lam</b>bda, <b>Reds</b>hift).
- **1.2.6** <b>Conv</b>ert <b>betw</b>een <b>form</b>ats (<b>e</b>.g., [<b>Com</b>ma-<b>Separ</b>ated <b>Val</b>ues [CSV]](00-data-basics-for-beginners.md#csv) → [<b>Parq</b>uet](00-data-basics-for-beginners.md#parquet)).
- **1.2.7** <b>Troubl</b>eshoot <b>transfo</b>rmation <b>fail</b>ures <b>a</b>nd <b>perfor</b>mance <b>iss</b>ues.
- **1.2.8** <b>Cre</b>ate <b>da</b>ta APIs <b>th</b>at <b>exp</b>ose <b>da</b>ta <b>t</b>o <b>oth</b>er <b>syst</b>ems.
- **1.2.9** <b>Def</b>ine <b>vol</b>ume, <b>velo</b>city, <b>a</b>nd <b>vari</b>ety (<b>struc</b>tured <b>v</b>s <b>unstru</b>ctured).
- **1.2.10** 🆕 <b>Integ</b>rate LLMs <b>f</b>or <b>da</b>ta <b>proce</b>ssing.

### Task 1.3: Orchestrate data pipelines
- **1.3.1** <b>Bui</b>ld <b>Extr</b>act, <b>Trans</b>form, <b>Lo</b>ad (ETL) <b>workf</b>lows <b>wi</b>th <b>orchest</b>ration <b>serv</b>ices (<b>Lam</b>bda, <b>EventB</b>ridge, MWAA, <b>St</b>ep <b>Funct</b>ions, <b>Gl</b>ue <b>workf</b>lows).
- **1.3.2** <b>Bui</b>ld <b>pipel</b>ines <b>f</b>or <b>perfor</b>mance, <b>availa</b>bility, <b>scalab</b>ility, <b>resil</b>iency, <b>fau</b>lt <b>toler</b>ance.
- **1.3.3** <b>Imple</b>ment <b>a</b>nd <b>main</b>tain <b>serve</b>rless <b>workf</b>lows.
- **1.3.4** <b>Se</b>nd <b>ale</b>rts <b>wi</b>th <b>notifi</b>cation <b>serv</b>ices ([<b>Sim</b>ple <b>Notifi</b>cation <b>Serv</b>ice [SNS]](00-data-basics-for-beginners.md#amazon-sns), [<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice [SQS]](00-data-basics-for-beginners.md#amazon-sqs)).

### Task 1.4: Apply programming concepts
- **1.4.1** <b>Opti</b>mize <b>co</b>de <b>t</b>o <b>red</b>uce <b>inges</b>tion/<b>transfo</b>rmation <b>runt</b>ime.
- **1.4.2** <b>Confi</b>gure <b>Lam</b>bda <b>f</b>or <b>concur</b>rency <b>a</b>nd <b>perfor</b>mance.
- **1.4.3** <b>U</b>se <b>da</b>ta <b>engine</b>ering <b>langu</b>ages <b>a</b>nd <b>frame</b>works (<b>Pyt</b>hon, [<b>Struc</b>tured <b>Que</b>ry <b>Lang</b>uage [SQL]](00-data-basics-for-beginners.md#sql), <b>Sca</b>la, <b>R</b>, <b>Ja</b>va, <b>Ba</b>sh, <b>Power</b>Shell).
- **1.4.4** <b>App</b>ly <b>soft</b>ware <b>engine</b>ering <b>pract</b>ices (<b>vers</b>ion <b>cont</b>rol, <b>test</b>ing, <b>logg</b>ing, <b>monit</b>oring).
- **1.4.5** <b>Dep</b>loy <b>da</b>ta <b>engine</b>ering <b>solut</b>ions <b>wi</b>th <b>I</b>aC.
- **1.4.6** <b>Pack</b>age <b>a</b>nd <b>dep</b>loy <b>serve</b>rless <b>pipel</b>ines <b>wi</b>th AWS SAM.
- **1.4.7** <b>U</b>se <b>a</b>nd <b>mou</b>nt <b>stor</b>age <b>volu</b>mes <b>i</b>n <b>Lam</b>bda.
- **1.4.8** <b>U</b>se <b>I</b>aC (<b>CloudFo</b>rmation, <b>Clo</b>ud <b>Develo</b>pment <b>K</b>it [CDK]) <b>f</b>or <b>repea</b>table <b>deploy</b>ments.
- **1.4.9** <b>Desc</b>ribe CI/CD <b>f</b>or <b>da</b>ta <b>pipel</b>ines.
- **1.4.10** <b>Def</b>ine <b>distri</b>buted <b>compu</b>ting.
- **1.4.11** <b>Desc</b>ribe <b>da</b>ta <b>struc</b>tures <b>a</b>nd <b>algor</b>ithms (<b>gra</b>phs, <b>tre</b>es).

---

## Task 1.1: Perform data ingestion

### Core concepts

**The ingestion decision tree** (<b>men</b>tal <b>mod</b>el <b>f</b>or "<b>whi</b>ch <b>serv</b>ice" <b>quest</b>ions):

1. **Is the data arriving continuously (events, clicks, IoT, logs)?** → <b>Strea</b>ming. <b>Other</b>wise <b>bat</b>ch.
2. **Streaming: do you need custom consumers, multiple consumers, ordering, or replay?** → **Kinesis Data Streams**. <b>D</b>o <b>y</b>ou <b>ju</b>st <b>ne</b>ed <b>t</b>o <b>la</b>nd <b>i</b>t <b>somew</b>here <b>wi</b>th <b>n</b>o <b>co</b>de? → **[Amazon Data Firehose](00-data-basics-for-beginners.md#amazon-data-firehose)**. <b>D</b>o <b>y</b>ou <b>ne</b>ed [<b>Kaf</b>ka](00-data-basics-for-beginners.md#apache-kafka) APIs <b>o</b>r <b>exis</b>ting <b>Kaf</b>ka <b>clie</b>nts? → **Amazon MSK**.
3. **Batch: where is the source?**
   - <b>Relat</b>ional/<b>NoS</b>QL <b>data</b>base → **AWS DMS** (<b>o</b>r **zero-ETL** <b>t</b>o <b>Reds</b>hift <b>i</b>f <b>suppo</b>rted)
   - <b>Soft</b>ware <b>a</b>s <b>a</b> <b>Serv</b>ice (<b>Sa</b>aS) <b>a</b>pp ([<b>Sales</b>force](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce), <b>Servi</b>ceNow, <b>Zend</b>esk…) → **Amazon AppFlow**
   - <b>O</b>n-<b>pr</b>em <b>fi</b>le <b>sha</b>res (NFS/<b>Ser</b>ver <b>Mess</b>age <b>Blo</b>ck [SMB]/HDFS) → **[AWS DataSync](00-data-basics-for-beginners.md#aws-datasync)**
   - <b>Part</b>ners <b>push</b>ing <b>fil</b>es <b>ov</b>er SSH <b>Fi</b>le <b>Tran</b>sfer <b>Prot</b>ocol (SFTP) → **[AWS Transfer Family](00-data-basics-for-beginners.md#aws-transfer-family)**
   - <b>Petab</b>ytes, <b>lit</b>tle <b>bandw</b>idth → **[AWS Snow Family](00-data-basics-for-beginners.md#aws-snow-family)**
   - <b>Thi</b>rd-<b>par</b>ty/<b>comme</b>rcial <b>data</b>sets → **[AWS Data Exchange](00-data-basics-for-beginners.md#aws-data-exchange)**
4. **How is the job started?** <b>Sche</b>dule → <b>EventB</b>ridge <b>Sched</b>uler / MWAA / <b>Gl</b>ue <b>trig</b>ger. <b>Eve</b>nt → S3 <b>Eve</b>nt <b>Notific</b>ations / <b>EventB</b>ridge <b>ru</b>le.
5. **Must it be reprocessable?** → <b>ke</b>ep <b>r</b>aw <b>da</b>ta <b>i</b>n S3 <b>a</b>nd/<b>o</b>r <b>u</b>se <b>a</b> <b>reta</b>ined <b>str</b>eam (<b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams [KDS], MSK).

### Streaming sources (skill 1.1.1)

| <b>Serv</b>ice | <b>Mod</b>el | <b>Late</b>ncy | <b>Scal</b>ing | <b>Rep</b>lay | <b>Cho</b>ose <b>wh</b>en |
|---|---|---|---|---|---|
| **Kinesis Data Streams (KDS)** | <b>Orde</b>red <b>sha</b>rds; <b>y</b>ou <b>wri</b>te <b>consu</b>mers | ~200 <b>m</b>s (~70 <b>m</b>s <b>wi</b>th <b>enha</b>nced <b>f</b>an-<b>o</b>ut) | <b>Sha</b>rds (<b>provis</b>ioned) <b>o</b>r **on-demand** | ✅ 24 <b>h</b> <b>defa</b>ult, <b>u</b>p <b>t</b>o 365 <b>da</b>ys | <b>Re</b>al <b>ti</b>me, <b>mult</b>iple <b>consu</b>mers, <b>cus</b>tom <b>proce</b>ssing, <b>orde</b>ring <b>p</b>er <b>k</b>ey |
| **Amazon Data Firehose** | <b>Mana</b>ged <b>deli</b>very, <b>buff</b>ered | <b>Ne</b>ar <b>re</b>al <b>ti</b>me (<b>buf</b>fer <b>b</b>y <b>si</b>ze/<b>ti</b>me; <b>ze</b>ro <b>buffe</b>ring <b>opt</b>ion) | <b>Autom</b>atic | ❌ | <b>La</b>nd <b>da</b>ta <b>i</b>n S3, <b>Reds</b>hift, [<b>OpenS</b>earch](00-data-basics-for-beginners.md#amazon-opensearch-service), <b>Spl</b>unk, <b>Snowf</b>lake, <b>Hyper</b>text <b>Tran</b>sfer <b>Prot</b>ocol (HTTP), **[Iceberg](00-data-basics-for-beginners.md#apache-iceberg) tables** <b>wi</b>th <b>n</b>o <b>co</b>de |
| **Amazon MSK** (<b>provis</b>ioned / <b>Serve</b>rless) | <b>Kaf</b>ka <b>top</b>ics & <b>parti</b>tions | <b>Re</b>al <b>ti</b>me | <b>Brok</b>ers/<b>parti</b>tions <b>o</b>r <b>serve</b>rless | ✅ <b>top</b>ic <b>reten</b>tion | <b>Kaf</b>ka <b>compati</b>bility, <b>exis</b>ting <b>Kaf</b>ka <b>ap</b>ps, <b>Kaf</b>ka <b>Conn</b>ect (**MSK Connect**) |
| **DynamoDB Streams** | <b>It</b>em-<b>lev</b>el <b>cha</b>nge <b>l</b>og | <b>Ne</b>ar <b>re</b>al <b>ti</b>me | <b>Autom</b>atic | ❌ <b>on</b>ly 24 <b>h</b> | <b>Rea</b>ct <b>t</b>o <b>Dyna</b>moDB <b>inse</b>rts/<b>upda</b>tes/<b>dele</b>tes (<b>Cha</b>nge <b>Da</b>ta <b>Capt</b>ure [CDC] <b>fr</b>om <b>Dyna</b>moDB) |
| **Kinesis Data Streams for DynamoDB** | <b>Dyna</b>moDB <b>chan</b>ges <b>in</b>to <b>a</b> KDS <b>str</b>eam | <b>Ne</b>ar <b>re</b>al <b>ti</b>me | KDS | ✅ (KDS <b>reten</b>tion) | <b>Dyna</b>moDB CDC <b>wi</b>th <b>lon</b>ger <b>reten</b>tion <b>o</b>r <b>mo</b>re <b>consu</b>mers |
| **AWS DMS (CDC)** | <b>Rea</b>ds <b>data</b>base (DB) <b>transa</b>ction <b>lo</b>gs | <b>Seco</b>nds | <b>Replic</b>ation <b>inst</b>ance <b>o</b>r DMS <b>Serve</b>rless | ❌ (<b>r</b>e-<b>r</b>un <b>ta</b>sk) | <b>Ongo</b>ing <b>replic</b>ation <b>fr</b>om RDS/<b>Aur</b>ora/<b>Ora</b>cle/SQL <b>Ser</b>ver/<b>o</b>n-<b>pr</b>em |
| **AWS Glue streaming ETL** | [<b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark) <b>Struc</b>tured <b>Strea</b>ming <b>mic</b>ro-<b>batc</b>hes <b>fr</b>om KDS/MSK | <b>Seco</b>nds | <b>Work</b>ers (<b>G</b>.025X <b>f</b>or <b>l</b>ow <b>vol</b>ume) | <b>v</b>ia <b>sou</b>rce | <b>Trans</b>form <b>stre</b>ams <b>wi</b>th <b>Spa</b>rk, <b>wri</b>te <b>t</b>o S3/<b>Iceb</b>erg |
| **Redshift streaming ingestion** | <b>Materi</b>alized <b>vi</b>ew <b>ov</b>er KDS/MSK | <b>Seco</b>nds | <b>Reds</b>hift | <b>v</b>ia <b>sou</b>rce | <b>G</b>et <b>str</b>eam <b>da</b>ta <b>in</b>to <b>Reds</b>hift **without staging in S3** |

#### Kinesis Data Streams deep dive

**Shard limits (memorize):**
- **Write:** 1 MB/<b>s</b> **or** 1,000 <b>reco</b>rds/<b>s</b> <b>p</b>er <b>sha</b>rd (<b>which</b>ever <b>com</b>es <b>fir</b>st)
- **Read (shared):** 2 MB/<b>s</b> <b>p</b>er <b>sha</b>rd, <b>spl</b>it <b>acr</b>oss <b>a</b>ll <b>stan</b>dard <b>consu</b>mers, <b>m</b>ax 5 `GetRecords` <b>cal</b>ls/<b>s</b> <b>p</b>er <b>sha</b>rd
- **Read (enhanced fan-out):** 2 MB/<b>s</b> **per consumer** <b>p</b>er <b>sha</b>rd, <b>pus</b>hed <b>v</b>ia HTTP/2

**Shard calculation example:**
> 3,000 <b>reco</b>rds/<b>s</b> <b>×</b> 2 KB = 6 MB/<b>s</b> <b>ing</b>est; 3 <b>consu</b>mers <b>ea</b>ch <b>read</b>ing <b>every</b>thing.
> - <b>Wri</b>te: <b>m</b>ax(6 MB <b>÷</b> 1, 3,000 <b>÷</b> 1,000) = **6 shards**
> - <b>Re</b>ad (<b>sha</b>red): 3 <b>consu</b>mers <b>×</b> 6 MB/<b>s</b> = 18 MB/<b>s</b> <b>÷</b> 2 = **9 shards**, <b>o</b>r <b>ke</b>ep 6 <b>sha</b>rds <b>a</b>nd <b>u</b>se **enhanced fan-out**.

**Partition keys:** <b>t</b>he <b>k</b>ey <b>i</b>s <b>has</b>hed <b>t</b>o <b>pi</b>ck <b>a</b> <b>sha</b>rd. <b>A</b> **low-cardinality key** (<b>e</b>.g., `country`) <b>crea</b>tes <b>a</b> **hot shard** → `ProvisionedThroughputExceededException` <b>ev</b>en <b>wh</b>en <b>tot</b>al <b>capa</b>city <b>loo</b>ks <b>fi</b>ne. <b>F</b>ix <b>wi</b>th <b>a</b> <b>hi</b>gh-<b>cardin</b>ality <b>k</b>ey (<b>dev</b>ice ID, <b>us</b>er ID) <b>o</b>r <b>a</b> <b>ran</b>dom <b>suf</b>fix.

**Capacity modes:**
- **Provisioned**: <b>y</b>ou <b>s</b>et <b>sha</b>rd <b>cou</b>nt; <b>spl</b>it/<b>mer</b>ge <b>sha</b>rds (<b>resha</b>rding) <b>t</b>o <b>sca</b>le. <b>Chea</b>per <b>f</b>or <b>ste</b>ady, <b>predic</b>table <b>traf</b>fic.
- **On-demand**: <b>sca</b>les <b>automat</b>ically. <b>Be</b>st <b>f</b>or <b>unpredi</b>ctable <b>o</b>r <b>spi</b>ky <b>traf</b>fic, <b>n</b>o <b>capa</b>city <b>plan</b>ning.

**Producers and consumers:**
- **KPL (Kinesis Producer Library):** <b>aggreg</b>ation + <b>batc</b>hing + <b>retr</b>ies → <b>hi</b>gh <b>throu</b>ghput, <b>ad</b>ds <b>a</b> <b>lit</b>tle <b>late</b>ncy.
- **KCL (Kinesis Client Library):** <b>distri</b>butes <b>sha</b>rds <b>acr</b>oss <b>work</b>ers, <b>checkp</b>oints <b>prog</b>ress <b>i</b>n <b>a</b> **DynamoDB lease table**. <b>I</b>f <b>t</b>he KCL <b>a</b>pp <b>i</b>s <b>throt</b>tled <b>o</b>n <b>Dyna</b>moDB, <b>incr</b>ease <b>th</b>at <b>tabl</b>e's <b>capa</b>city.
- **`IteratorAgeMilliseconds`** (`GetRecords.IteratorAgeMilliseconds`): <b>h</b>ow <b>f</b>ar <b>beh</b>ind <b>consu</b>mers <b>a</b>re. <b>Ris</b>ing <b>iter</b>ator <b>a</b>ge = <b>consu</b>mers <b>can</b>'t <b>ke</b>ep <b>u</b>p.

#### Amazon Data Firehose deep dive

- **Buffering:** <b>deli</b>vers <b>wh</b>en <b>eit</b>her <b>t</b>he <b>si</b>ze (1–128 <b>M</b>iB) <b>o</b>r <b>inte</b>rval <b>thres</b>hold <b>i</b>s <b>h</b>it. <b>Big</b>ger <b>buff</b>ers → <b>few</b>er, <b>lar</b>ger S3 <b>fil</b>es (<b>bet</b>ter <b>f</b>or [<b>Ath</b>ena](00-data-basics-for-beginners.md#amazon-athena)). <b>Smal</b>ler → <b>low</b>er <b>late</b>ncy.
- **Record format conversion:** [<b>JavaS</b>cript <b>Obj</b>ect <b>Nota</b>tion [JSON]](00-data-basics-for-beginners.md#json) → **Parquet or [Optimized Row Columnar [ORC]](00-data-basics-for-beginners.md#orc)** <b>usi</b>ng <b>a</b> <b>sch</b>ema <b>fr</b>om <b>a</b> **Glue Data Catalog table**. <b>Mo</b>st <b>com</b>mon "<b>lea</b>st <b>operat</b>ional <b>eff</b>ort" <b>ans</b>wer <b>f</b>or "<b>conv</b>ert <b>strea</b>ming JSON <b>t</b>o <b>Parq</b>uet".
- **Lambda transformation:** <b>enr</b>ich/<b>cle</b>an <b>reco</b>rds <b>i</b>n <b>fli</b>ght (<b>bluep</b>rints <b>avail</b>able).
- **Dynamic partitioning:** <b>wri</b>tes <b>in</b>to S3 <b>pref</b>ixes <b>bas</b>ed <b>o</b>n <b>rec</b>ord <b>fie</b>lds (<b>e</b>.g., `customer_id=…/year=…/`) → <b>Ath</b>ena-<b>frie</b>ndly <b>parti</b>tions.
- **Redshift destination:** <b>Fire</b>hose <b>wri</b>tes <b>t</b>o S3, <b>th</b>en <b>iss</b>ues <b>a</b> `COPY` <b>in</b>to <b>Reds</b>hift.
- **Failed records** <b>g</b>o <b>t</b>o <b>a</b>n S3 <b>err</b>or <b>pre</b>fix. <b>Fire</b>hose <b>h</b>as **no replay**. <b>I</b>f <b>y</b>ou <b>ne</b>ed <b>reproc</b>essing, <b>p</b>ut KDS <b>i</b>n <b>fro</b>nt (KDS → <b>Fire</b>hose) <b>o</b>r <b>ke</b>ep <b>t</b>he <b>r</b>aw <b>co</b>py.
- **Source** <b>c</b>an <b>b</b>e <b>dir</b>ect PUT, KDS, MSK, [<b>Cloud</b>Watch](00-data-basics-for-beginners.md#amazon-cloudwatch) <b>Lo</b>gs <b>subscri</b>ptions, <b>a</b>nd <b>oth</b>ers.

#### Amazon MSK deep dive

- **Provisioned**: <b>y</b>ou <b>cho</b>ose <b>bro</b>ker <b>ty</b>pe/<b>cou</b>nt <b>a</b>nd <b>stor</b>age; <b>fu</b>ll <b>Kaf</b>ka <b>con</b>fig <b>cont</b>rol.
- **MSK Serverless**: <b>n</b>o <b>bro</b>ker <b>siz</b>ing; <b>go</b>od <b>wh</b>en <b>y</b>ou <b>wa</b>nt <b>Kaf</b>ka APIs <b>with</b>out <b>capa</b>city <b>manag</b>ement.
- **MSK Connect**: <b>mana</b>ged <b>Kaf</b>ka <b>Conn</b>ect <b>work</b>ers (<b>e</b>.g., S3 <b>si</b>nk <b>conne</b>ctor, <b>Debe</b>zium CDC <b>sou</b>rce).
- <b>Cho</b>ose MSK <b>ov</b>er KDS <b>wh</b>en <b>t</b>he <b>scen</b>ario <b>sa</b>ys **"Kafka"**, "<b>exis</b>ting <b>Kaf</b>ka <b>produ</b>cers/<b>consu</b>mers", "<b>op</b>en-<b>sou</b>rce <b>portab</b>ility", <b>o</b>r <b>nee</b>ds <b>ve</b>ry <b>lo</b>ng <b>reten</b>tion <b>o</b>r <b>lar</b>ge <b>mess</b>ages.

### Batch sources (skills 1.1.2, 1.1.3)

| <b>Sou</b>rce / <b>ne</b>ed | <b>Serv</b>ice | <b>K</b>ey <b>configu</b>ration <b>opti</b>ons |
|---|---|---|
| <b>Fil</b>es <b>alre</b>ady <b>i</b>n S3 | **Glue jobs / crawlers**, **Athena CREATE TABLE AS SELECT (CTAS)**, **Redshift COPY** | <b>Partit</b>ioned <b>pref</b>ixes, <b>fi</b>le <b>siz</b>ing, <b>compre</b>ssion, <b>mani</b>fest <b>fil</b>es |
| <b>Relat</b>ional DB <b>snap</b>shot + <b>ongo</b>ing <b>chan</b>ges | **AWS DMS** | <b>Ta</b>sk <b>ty</b>pe (**full load**, **full load + CDC**, **CDC only**), <b>tab</b>le <b>mapp</b>ings, <b>transfo</b>rmation <b>rul</b>es, <b>Lar</b>ge <b>Obj</b>ect (LOB) <b>sett</b>ings, <b>da</b>ta <b>valid</b>ation |
| <b>Operat</b>ional DB → <b>Reds</b>hift <b>wi</b>th <b>n</b>o <b>pipe</b>line | **[Zero-ETL](00-data-basics-for-beginners.md#zero-etl-integrations) integrations** | [<b>Aur</b>ora](00-data-basics-for-beginners.md#amazon-aurora) [<b>MyS</b>QL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server)/<b>Postg</b>reSQL, RDS <b>MyS</b>QL, <b>Dyna</b>moDB → <b>Reds</b>hift |
| <b>Sa</b>aS <b>ap</b>ps | **Amazon AppFlow** | <b>Trig</b>ger: <b>o</b>n <b>dem</b>and / <b>sched</b>uled / <b>eve</b>nt; <b>fie</b>ld <b>mapp</b>ing, <b>filte</b>ring, <b>mask</b>ing, <b>valid</b>ation; <b>destin</b>ations S3, <b>Reds</b>hift, <b>Snowf</b>lake |
| <b>O</b>n-<b>pr</b>em <b>fi</b>le <b>syst</b>ems | **AWS DataSync** | <b>Age</b>nt <b>o</b>n-<b>pr</b>em, <b>sched</b>uled <b>tas</b>ks, <b>bandw</b>idth <b>throt</b>tling, <b>integ</b>rity <b>verifi</b>cation, <b>filt</b>ers |
| [<b>Had</b>oop](00-data-basics-for-beginners.md#apache-hadoop)/<b>Spa</b>rk <b>o</b>n <b>lar</b>ge <b>data</b>sets | **Amazon EMR** | <b>Rea</b>ds <b>fr</b>om S3 (EMR <b>Fi</b>le <b>Sys</b>tem [EMRFS]), [<b>Had</b>oop <b>Distri</b>buted <b>Fi</b>le <b>Sys</b>tem [HDFS]](00-data-basics-for-beginners.md#hdfs), [<b>HBa</b>se](00-data-basics-for-beginners.md#apache-hbase) |
| <b>Sma</b>ll <b>cus</b>tom <b>pul</b>ls | **AWS Lambda** | <b>Sched</b>uled <b>wi</b>th <b>EventB</b>ridge, ≤15 <b>m</b>in <b>runt</b>ime |
| <b>Da</b>ta <b>wareh</b>ouse <b>expo</b>rts | **Redshift `UNLOAD`** | <b>T</b>o S3 <b>i</b>n <b>Parq</b>uet, <b>partit</b>ioned, <b>para</b>llel |

**DMS details the exam likes:**
- **Components:** <b>replic</b>ation <b>inst</b>ance (<b>o</b>r DMS <b>Serve</b>rless), <b>sou</b>rce/<b>tar</b>get **endpoints**, **replication task**.
- **CDC prerequisites:** <b>t</b>he <b>sou</b>rce <b>mu</b>st <b>exp</b>ose <b>cha</b>nge <b>lo</b>gs. <b>MyS</b>QL <b>nee</b>ds **binary logging with `binlog_format=ROW`**. <b>Ora</b>cle <b>nee</b>ds **supplemental logging**. <b>Postg</b>reSQL <b>nee</b>ds **logical replication**. SQL <b>Ser</b>ver <b>nee</b>ds <b>Micro</b>soft SQL <b>Ser</b>ver <b>Cha</b>nge <b>Da</b>ta <b>Capt</b>ure (MS-CDC)/MS-<b>Replic</b>ation.
- **DMS does light transforms only** (<b>ren</b>ame, <b>a</b>dd/<b>dr</b>op <b>colu</b>mns, <b>fil</b>ter <b>ro</b>ws). <b>Hea</b>vy <b>log</b>ic <b>go</b>es <b>downs</b>tream <b>i</b>n <b>Gl</b>ue/EMR.
- **S3 target**: <b>c</b>an <b>wri</b>te CSV <b>o</b>r **Parquet**; CDC <b>fil</b>es <b>la</b>nd <b>wi</b>th <b>a</b>n <b>opera</b>tion <b>col</b>umn (`I`/`U`/`D`), <b>whi</b>ch <b>y</b>ou <b>lat</b>er <b>mer</b>ge (<b>Iceb</b>erg `MERGE` <b>i</b>s <b>a</b> <b>gre</b>at <b>f</b>it).
- **DMS Schema Conversion** (<b>ins</b>ide DMS) <b>conv</b>erts <b>sche</b>mas <b>f</b>or <b>heterog</b>eneous <b>migra</b>tions. <b>T</b>he <b>stand</b>alone AWS <b>Sch</b>ema <b>Conve</b>rsion <b>To</b>ol (SCT) <b>i</b>s <b>n</b>o <b>lon</b>ger <b>i</b>n <b>sco</b>pe.

### Consuming data APIs (skill 1.1.4)

<b>Patt</b>ern: **EventBridge Scheduler → Lambda (or Glue Python shell) → call REST Application Programming Interface (API) → write raw JSON to S3 → crawler/Glue job.**

<b>Thi</b>ngs <b>t</b>o <b>han</b>dle:
- **Authentication:** <b>sto</b>re API <b>ke</b>ys/<b>OAu</b>th <b>secr</b>ets <b>i</b>n **[AWS Secrets Manager](00-data-basics-for-beginners.md#aws-secrets-manager)**, <b>nev</b>er <b>i</b>n <b>co</b>de <b>o</b>r <b>pla</b>in <b>enviro</b>nment <b>varia</b>bles.
- **Pagination:** <b>lo</b>op <b>thro</b>ugh <b>pag</b>es/<b>curs</b>ors. <b>I</b>f <b>i</b>t <b>m</b>ay <b>exc</b>eed 15 <b>minu</b>tes, <b>u</b>se <b>St</b>ep <b>Funct</b>ions (<b>lo</b>op <b>o</b>r <b>M</b>ap) <b>o</b>r <b>a</b> <b>Gl</b>ue <b>Pyt</b>hon <b>she</b>ll <b>j</b>ob.
- **Rate limits:** <b>expone</b>ntial <b>back</b>off <b>wi</b>th <b>jit</b>ter, <b>resp</b>ect `Retry-After`, <b>thro</b>ttle <b>wi</b>th SQS.
- **Idempotency:** <b>wri</b>te <b>ea</b>ch <b>pa</b>ge <b>t</b>o <b>a</b> <b>determi</b>nistic S3 <b>k</b>ey <b>s</b>o <b>retr</b>ies <b>don</b>'t <b>dupli</b>cate <b>da</b>ta.
- **SaaS with a built-in connector?** <b>Pre</b>fer **AppFlow**. <b>N</b>o <b>co</b>de <b>mea</b>ns <b>le</b>ss <b>operat</b>ional <b>over</b>head.

### Schedulers and event triggers (skills 1.1.5, 1.1.6)

| <b>Mecha</b>nism | <b>U</b>se |
|---|---|
| **EventBridge Scheduler** | <b>Cr</b>on/<b>ra</b>te <b>sched</b>ules <b>wi</b>th <b>ti</b>me <b>zon</b>es, <b>o</b>ne-<b>ti</b>me <b>sched</b>ules, <b>retr</b>ies + <b>De</b>ad-<b>Let</b>ter <b>Que</b>ue (DLQ); <b>c</b>an <b>tar</b>get <b>alm</b>ost <b>a</b>ny AWS API |
| **EventBridge rules (schedule)** | <b>Old</b>er <b>w</b>ay <b>t</b>o <b>sche</b>dule; <b>sti</b>ll <b>val</b>id |
| **Glue triggers** | <b>Sched</b>uled, <b>o</b>n-<b>dem</b>and, <b>o</b>r <b>condit</b>ional (<b>sta</b>rt <b>j</b>ob <b>B</b> <b>wh</b>en <b>j</b>ob <b>A</b> <b>succ</b>eeds) |
| **Crawler schedules** | <b>Cr</b>on <b>sche</b>dule <b>o</b>n <b>t</b>he <b>craw</b>ler <b>its</b>elf |
| **MWAA (Airflow)** | `schedule` <b>o</b>n <b>a</b> <b>Dire</b>cted <b>Acyc</b>lic <b>Gra</b>ph (DAG); <b>be</b>st <b>wh</b>en <b>t</b>he <b>pipe</b>line <b>i</b>s <b>alre</b>ady <b>Airf</b>low |
| **Redshift scheduled queries** | <b>R</b>un SQL <b>o</b>n <b>a</b> <b>sche</b>dule (<b>Reds</b>hift <b>Da</b>ta API <b>und</b>er <b>t</b>he <b>ho</b>od) |

**S3 Event Notifications vs EventBridge:**

| | S3 <b>Eve</b>nt <b>Notific</b>ations | S3 → <b>EventB</b>ridge |
|---|---|---|
| <b>Targ</b>ets | <b>Lam</b>bda, SQS, SNS | 20+ <b>targ</b>ets (<b>St</b>ep <b>Funct</b>ions, <b>Gl</b>ue <b>workf</b>lows <b>v</b>ia API, <b>Kine</b>sis, <b>e</b>tc.) |
| <b>Filte</b>ring | <b>Pre</b>fix/<b>suf</b>fix <b>on</b>ly | <b>Ri</b>ch <b>cont</b>ent <b>filte</b>ring (<b>obj</b>ect <b>si</b>ze, <b>k</b>ey <b>patt</b>erns, <b>meta</b>data) |
| <b>Mult</b>iple <b>targ</b>ets <b>f</b>or <b>sa</b>me <b>eve</b>nt | <b>Limi</b>ted (<b>overla</b>pping <b>pref</b>ixes <b>n</b>ot <b>allo</b>wed) | <b>Ma</b>ny <b>rul</b>es <b>o</b>n <b>t</b>he <b>sa</b>me <b>eve</b>nt |
| <b>Arch</b>ive & <b>rep</b>lay | ❌ | ✅ |

> <b>Ru</b>le <b>o</b>f <b>thu</b>mb: <b>o</b>ne <b>sim</b>ple <b>tar</b>get → S3 <b>Eve</b>nt <b>Notifi</b>cation. <b>Comp</b>lex <b>filte</b>ring, <b>mult</b>iple <b>consu</b>mers, <b>o</b>r <b>star</b>ting <b>St</b>ep <b>Funct</b>ions <b>dire</b>ctly → **EventBridge**.

**Crawler-specific trick:** <b>inst</b>ead <b>o</b>f <b>r</b>e-<b>craw</b>ling <b>a</b> <b>hu</b>ge <b>buc</b>ket <b>o</b>n <b>a</b> <b>sche</b>dule, <b>u</b>se **S3 event-mode crawlers** (S3 <b>eve</b>nts → SQS → <b>craw</b>ler <b>cra</b>wls <b>on</b>ly <b>chan</b>ged <b>pref</b>ixes).

### Calling Lambda from Kinesis (skill 1.1.7)

<b>Lam</b>bda <b>rea</b>ds KDS <b>thro</b>ugh <b>a</b>n **event source mapping** (<b>Lam</b>bda <b>pol</b>ls <b>t</b>he <b>str</b>eam; <b>y</b>ou <b>don</b>'t <b>wri</b>te <b>poll</b>ing <b>co</b>de).

| <b>Sett</b>ing | <b>Wh</b>at <b>i</b>t <b>do</b>es | <b>Ex</b>am <b>u</b>se |
|---|---|---|
| **Batch size** | <b>Reco</b>rds <b>p</b>er <b>invoc</b>ation (<b>u</b>p <b>t</b>o 10,000) | <b>Big</b>ger = <b>few</b>er <b>invoca</b>tions, <b>mo</b>re <b>effic</b>ient |
| **Batch window** | <b>Wa</b>it <b>u</b>p <b>t</b>o <b>N</b> <b>seco</b>nds (≤300) <b>t</b>o <b>fi</b>ll <b>a</b> <b>bat</b>ch | <b>Red</b>uce <b>invoca</b>tions <b>f</b>or <b>l</b>ow-<b>traf</b>fic <b>stre</b>ams |
| **Parallelization factor** | 1–10 <b>concu</b>rrent <b>batc</b>hes **per shard** | <b>Incr</b>ease <b>throu</b>ghput **without adding shards** (<b>orde</b>ring <b>ke</b>pt <b>p</b>er <b>parti</b>tion <b>k</b>ey) |
| **Starting position** | `TRIM_HORIZON` (<b>old</b>est), `LATEST`, `AT_TIMESTAMP` | <b>Repro</b>cess <b>fr</b>om <b>t</b>he <b>begin</b>ning <b>wi</b>th `TRIM_HORIZON` |
| **Bisect batch on function error** | <b>Spl</b>its <b>a</b> <b>fail</b>ing <b>bat</b>ch <b>i</b>n <b>ha</b>lf <b>t</b>o <b>isol</b>ate <b>a</b> <b>b</b>ad <b>rec</b>ord | "<b>O</b>ne <b>poi</b>son <b>rec</b>ord <b>blo</b>cks <b>t</b>he <b>sha</b>rd" |
| **Maximum retry attempts / maximum record age** | <b>St</b>op <b>retr</b>ying <b>o</b>ld/<b>fail</b>ing <b>reco</b>rds | <b>Prev</b>ent <b>a</b> <b>sha</b>rd <b>fr</b>om <b>bei</b>ng <b>stu</b>ck <b>fore</b>ver |
| **On-failure destination** | <b>Se</b>nd <b>meta</b>data <b>o</b>f <b>fai</b>led <b>batc</b>hes <b>t</b>o SQS/SNS | <b>Ke</b>ep <b>proce</b>ssing, <b>insp</b>ect <b>fail</b>ures <b>lat</b>er |
| **Tumbling windows** | <b>Aggre</b>gate <b>sta</b>te <b>acr</b>oss <b>invoca</b>tions (<b>u</b>p <b>t</b>o 15 <b>m</b>in) | <b>Sim</b>ple **stateful** <b>aggreg</b>ations <b>i</b>n <b>Lam</b>bda |
| **Enhanced fan-out consumer** | <b>Dedic</b>ated <b>throu</b>ghput <b>f</b>or <b>th</b>is <b>Lam</b>bda | <b>Lam</b>bda <b>i</b>s <b>o</b>ne <b>o</b>f <b>seve</b>ral <b>consu</b>mers |

> ⚠️ <b>B</b>y <b>defa</b>ult, <b>a</b> <b>fai</b>led <b>bat</b>ch <b>i</b>s **retried until it succeeds or the data expires**, <b>a</b>nd <b>t</b>he <b>sha</b>rd <b>i</b>s **blocked** <b>meanw</b>hile. <b>Exp</b>ect <b>a</b> <b>ques</b>tion <b>whe</b>re <b>t</b>he <b>f</b>ix <b>i</b>s <b>bis</b>ect-<b>o</b>n-<b>err</b>or + <b>m</b>ax <b>retr</b>ies + <b>o</b>n-<b>fail</b>ure <b>destin</b>ation.

### IP allowlists for data sources (skill 1.1.8)

<b>Com</b>mon <b>scen</b>ario: <b>a</b>n **external** <b>data</b>base <b>o</b>r API <b>on</b>ly <b>acce</b>pts <b>connec</b>tions <b>fr</b>om <b>appr</b>oved IP <b>addre</b>sses.

- AWS <b>serv</b>ices <b>i</b>n <b>a</b> [<b>Virt</b>ual <b>Priv</b>ate <b>Clo</b>ud [VPC]](00-data-basics-for-beginners.md#amazon-vpc) (<b>Gl</b>ue <b>jo</b>bs, <b>Lam</b>bda, EMR, ECS) <b>rea</b>ch <b>t</b>he <b>inte</b>rnet <b>thro</b>ugh <b>a</b> **Network Address Translation (NAT) gateway**. <b>Gi</b>ve <b>t</b>he <b>part</b>ner <b>t</b>he **NAT gateway's Elastic IP** <b>t</b>o <b>allow</b>list. <b>Th</b>is <b>giv</b>es <b>a</b> <b>fix</b>ed, <b>kno</b>wn IP.
- <b>Lam</b>bda/<b>Gl</b>ue **without** <b>a</b> VPC <b>us</b>es <b>ran</b>dom AWS <b>Inte</b>rnet <b>Prot</b>ocol <b>addre</b>sses (IPs), <b>whi</b>ch <b>can</b>'t <b>b</b>e <b>reli</b>ably <b>allowl</b>isted.
- <b>Inbo</b>und <b>allowl</b>isting <b>t</b>o *<b>yo</b>ur* <b>resou</b>rces: <b>secu</b>rity <b>gro</b>ups (<b>stat</b>eful) <b>o</b>r <b>netw</b>ork <b>Acc</b>ess <b>Cont</b>rol <b>Lis</b>ts [ACLs] (<b>state</b>less). <b>F</b>or AWS <b>serv</b>ices <b>th</b>at <b>conn</b>ect *<b>t</b>o* <b>yo</b>ur <b>resou</b>rces (<b>e</b>.g., <b>Fire</b>hose → <b>Reds</b>hift/<b>Spl</b>unk, [<b>Quick</b>Sight](00-data-basics-for-beginners.md#amazon-quicksight) → RDS), <b>all</b>ow <b>th</b>at <b>servi</b>ce's **published IP ranges / Classless Inter-Domain Routing (CIDR) for the Region**.
- **Glue JDBC connections** <b>r</b>un <b>i</b>n <b>yo</b>ur VPC <b>sub</b>net. <b>T</b>he <b>secu</b>rity <b>gro</b>up <b>nee</b>ds <b>a</b> **self-referencing inbound rule (all Transmission Control Protocol [TCP])** <b>s</b>o <b>Gl</b>ue <b>work</b>ers <b>c</b>an <b>ta</b>lk <b>t</b>o <b>ea</b>ch <b>oth</b>er, <b>a</b>nd <b>t</b>he <b>sub</b>net <b>nee</b>ds <b>a</b> <b>rou</b>te <b>t</b>o <b>t</b>he <b>da</b>ta <b>sou</b>rce (<b>o</b>r <b>a</b> NAT <b>gate</b>way / VPC <b>endp</b>oint <b>f</b>or S3).

### Throttling and rate limits (skill 1.1.9)

| <b>Sou</b>rce | <b>Symp</b>tom | <b>Fix</b>es |
|---|---|---|
| **DynamoDB** | `ProvisionedThroughputExceededException`, `ThrottlingException` | <b>O</b>n-<b>dem</b>and <b>mo</b>de <b>o</b>r <b>au</b>to <b>scal</b>ing, <b>bet</b>ter <b>parti</b>tion <b>k</b>ey (<b>avo</b>id <b>h</b>ot <b>ke</b>ys), `BatchWriteItem` <b>wi</b>th <b>retr</b>ies <b>o</b>f `UnprocessedItems`, <b>expone</b>ntial <b>back</b>off, SQS <b>buf</b>fer <b>i</b>n <b>fro</b>nt, <b>Dyna</b>moDB <b>Accele</b>rator (DAX) <b>f</b>or <b>re</b>ad-<b>hea</b>vy <b>traf</b>fic |
| **RDS / Aurora** | "<b>T</b>oo <b>ma</b>ny <b>connec</b>tions" <b>fr</b>om <b>ma</b>ny <b>Lamb</b>das | **RDS Proxy** (<b>conne</b>ction <b>pool</b>ing), <b>rese</b>rved <b>concur</b>rency <b>t</b>o <b>c</b>ap <b>Lam</b>bda, <b>re</b>ad <b>repl</b>icas <b>f</b>or <b>rea</b>ds |
| **Kinesis** | `ProvisionedThroughputExceededException` <b>o</b>n <b>p</b>ut <b>o</b>r <b>g</b>et | <b>Mo</b>re <b>sha</b>rds / <b>o</b>n-<b>dem</b>and, <b>hi</b>gh-<b>cardin</b>ality <b>parti</b>tion <b>k</b>ey, `PutRecords` <b>batc</b>hing, KPL <b>aggreg</b>ation, <b>enha</b>nced <b>f</b>an-<b>o</b>ut <b>f</b>or <b>read</b>ers |
| **Any AWS API** | `ThrottlingException`, `Rate exceeded` | <b>Soft</b>ware <b>Develo</b>pment <b>K</b>it (SDK) <b>retr</b>ies <b>wi</b>th **exponential backoff and jitter**, <b>requ</b>est <b>quo</b>ta <b>incr</b>ease |
| **External APIs** | HTTP 429 | <b>Back</b>off, <b>hon</b>or `Retry-After`, <b>que</b>ue <b>requ</b>ests <b>i</b>n SQS, <b>lim</b>it <b>concur</b>rency |

### Fan-in and fan-out (skill 1.1.10)

- **Fan-in:** <b>ma</b>ny <b>produ</b>cers → <b>o</b>ne <b>str</b>eam (<b>thous</b>ands <b>o</b>f <b>devi</b>ces → <b>o</b>ne KDS <b>str</b>eam <b>o</b>r <b>Fire</b>hose <b>str</b>eam). <b>Al</b>so <b>ma</b>ny <b>stre</b>ams → <b>o</b>ne <b>destin</b>ation (<b>seve</b>ral <b>Fire</b>hose <b>stre</b>ams <b>in</b>to <b>o</b>ne <b>buc</b>ket <b>wi</b>th <b>diffe</b>rent <b>pref</b>ixes).
- **Fan-out:** <b>o</b>ne <b>str</b>eam → <b>ma</b>ny <b>consu</b>mers:
  - **KDS enhanced fan-out**: <b>ea</b>ch <b>cons</b>umer <b>ge</b>ts <b>dedic</b>ated 2 MB/<b>s</b> <b>p</b>er <b>sha</b>rd.
  - **SNS → multiple SQS queues** (<b>clas</b>sic <b>p</b>ub/<b>s</b>ub <b>f</b>an-<b>o</b>ut <b>wi</b>th <b>buffe</b>ring <b>p</b>er <b>cons</b>umer).
  - **EventBridge** <b>ru</b>le <b>wi</b>th <b>seve</b>ral <b>targ</b>ets, <b>o</b>r <b>seve</b>ral <b>rul</b>es <b>o</b>n <b>t</b>he <b>sa</b>me <b>eve</b>nt.
  - **MSK consumer groups**: <b>ea</b>ch <b>gro</b>up <b>rea</b>ds <b>t</b>he <b>fu</b>ll <b>top</b>ic <b>indepen</b>dently.
- **Firehose** <b>deli</b>vers <b>t</b>o **one destination per stream**. <b>T</b>o <b>f</b>an <b>o</b>ut, <b>p</b>ut KDS <b>fir</b>st <b>a</b>nd <b>att</b>ach <b>mult</b>iple <b>Fire</b>hose <b>stre</b>ams.

```
              ┌──► Lambda (real-time alerts)          [enhanced fan-out]
Producers ──► KDS ──► Firehose ──► S3 (Parquet) ──► Athena
              └──► Managed Service for Apache Flink ──► OpenSearch dashboards
```

### Replayability (skill 1.1.11)

<b>Replaya</b>bility = <b>t</b>he <b>abil</b>ity <b>t</b>o **re-run ingestion/processing over past data** <b>aft</b>er <b>a</b> <b>b</b>ug <b>f</b>ix, <b>a</b> <b>sch</b>ema <b>cha</b>nge, <b>o</b>r <b>a</b> <b>n</b>ew <b>cons</b>umer.

| <b>Mecha</b>nism | <b>Rep</b>lay <b>win</b>dow |
|---|---|
| **KDS** | <b>Reten</b>tion <b>u</b>p <b>t</b>o 365 <b>da</b>ys. <b>N</b>ew <b>cons</b>umer <b>c</b>an <b>sta</b>rt <b>a</b>t `TRIM_HORIZON` <b>o</b>r `AT_TIMESTAMP`. |
| **MSK** | <b>Top</b>ic <b>reten</b>tion (<b>ti</b>me <b>o</b>r <b>si</b>ze <b>bas</b>ed); <b>res</b>et <b>cons</b>umer <b>gro</b>up <b>offs</b>ets |
| **S3 raw/bronze zone** | <b>Indef</b>inite. **Keep the immutable raw copy** <b>a</b>nd <b>rebu</b>ild <b>downs</b>tream <b>tab</b>les. |
| **EventBridge archive** | <b>Arch</b>ive <b>eve</b>nts, <b>th</b>en <b>rep</b>lay <b>t</b>o <b>a</b> <b>b</b>us |
| **Glue job bookmarks** | <b>Res</b>et <b>t</b>he <b>book</b>mark <b>t</b>o <b>repro</b>cess <b>every</b>thing |
| **DynamoDB Streams** | 24 <b>h</b> <b>on</b>ly (<b>u</b>se KDS <b>f</b>or <b>Dyna</b>moDB <b>f</b>or <b>lon</b>ger) |
| **Firehose / SQS** | ❌ <b>n</b>o <b>rep</b>lay <b>on</b>ce <b>deliv</b>ered/<b>dele</b>ted |

> <b>Des</b>ign <b>princ</b>iple: **land raw data unchanged first, then transform.** <b>It</b>'s <b>t</b>he <b>saf</b>est <b>rep</b>lay <b>stra</b>tegy <b>a</b>nd <b>a</b> <b>com</b>mon <b>corr</b>ect <b>ans</b>wer.

### Stateful vs stateless (skill 1.1.12)

| | <b>State</b>less | <b>Stat</b>eful |
|---|---|---|
| <b>Mean</b>ing | <b>Ea</b>ch <b>rec</b>ord <b>i</b>s <b>proce</b>ssed <b>indepen</b>dently | <b>Proce</b>ssing <b>depe</b>nds <b>o</b>n <b>prev</b>ious <b>reco</b>rds <b>o</b>r <b>sto</b>red <b>sta</b>te |
| <b>Exam</b>ples | <b>Fil</b>ter, <b>for</b>mat <b>conve</b>rsion, <b>fie</b>ld <b>mask</b>ing, <b>p</b>er-<b>rec</b>ord <b>enric</b>hment | <b>Wind</b>owed <b>aggreg</b>ations (<b>cou</b>nt <b>p</b>er 5 <b>m</b>in), <b>dedupli</b>cation, <b>session</b>ization, <b>str</b>eam <b>joi</b>ns, <b>runn</b>ing <b>tot</b>als |
| AWS <b>too</b>ls | <b>Lam</b>bda <b>p</b>er <b>rec</b>ord, <b>Fire</b>hose <b>Lam</b>bda <b>trans</b>form | **[Managed Service for Apache Flink](00-data-basics-for-beginners.md#managed-service-for-apache-flink)** (<b>checkp</b>oints, <b>savep</b>oints), <b>Gl</b>ue <b>strea</b>ming <b>wi</b>th <b>checkp</b>oints, **Lambda tumbling windows**, KCL <b>wi</b>th <b>Dyna</b>moDB <b>checkp</b>oints |
| <b>Scal</b>ing | <b>Ea</b>sy, <b>a</b>ny <b>wor</b>ker <b>c</b>an <b>proc</b>ess <b>a</b>ny <b>rec</b>ord | <b>Mu</b>st <b>pres</b>erve <b>sta</b>te; <b>parti</b>tion <b>b</b>y <b>k</b>ey <b>s</b>o <b>rela</b>ted <b>reco</b>rds <b>h</b>it <b>t</b>he <b>sa</b>me <b>wor</b>ker |

**Transactions:** "<b>stat</b>eful/<b>transac</b>tional" <b>m</b>ay <b>al</b>so <b>me</b>an **Atomicity, Consistency, Isolation, Durability (ACID) guarantees**: <b>a</b>ll-<b>o</b>r-<b>noth</b>ing <b>wri</b>tes (<b>Reds</b>hift, <b>Aur</b>ora, **Apache Iceberg** <b>comm</b>its) <b>v</b>s <b>event</b>ually <b>consi</b>stent, <b>app</b>end-<b>on</b>ly <b>wri</b>tes (<b>pla</b>in S3 <b>fil</b>es).

---

## Task 1.2: Transform and process data

### Choosing a transformation service (skill 1.2.5)

| <b>Requir</b>ement | <b>Be</b>st <b>f</b>it | <b>W</b>hy |
|---|---|---|
| <b>Serve</b>rless <b>Spa</b>rk ETL <b>integ</b>rated <b>wi</b>th <b>t</b>he <b>Da</b>ta <b>Cata</b>log, <b>mini</b>mal <b>o</b>ps | **AWS Glue** | <b>N</b>o <b>clus</b>ters; <b>bookm</b>arks, <b>craw</b>lers, <b>Da</b>ta <b>Qual</b>ity <b>bui</b>lt <b>i</b>n |
| <b>Vis</b>ual / <b>n</b>o-<b>co</b>de <b>clea</b>ning <b>a</b>nd <b>profi</b>ling <b>f</b>or <b>anal</b>ysts | **[Glue DataBrew](00-data-basics-for-beginners.md#aws-glue-databrew)** | 250+ <b>poi</b>nt-<b>a</b>nd-<b>cli</b>ck <b>trans</b>forms, <b>prof</b>ile <b>jo</b>bs |
| <b>Fu</b>ll <b>Had</b>oop <b>ecosy</b>stem (<b>Spa</b>rk, [<b>Hi</b>ve](00-data-basics-for-beginners.md#apache-hive), [<b>Pre</b>sto](00-data-basics-for-beginners.md#presto-and-trino)/<b>Tri</b>no, <b>HBa</b>se, [<b>Hu</b>di](00-data-basics-for-beginners.md#apache-hudi)), <b>cus</b>tom <b>vers</b>ions, <b>tun</b>ing, <b>Sp</b>ot | **Amazon EMR** (<b>o</b>n <b>Elas</b>tic <b>Comp</b>ute <b>Clo</b>ud [EC2]) | <b>Fu</b>ll <b>cont</b>rol; <b>chea</b>pest <b>a</b>t <b>lar</b>ge <b>sca</b>le <b>wi</b>th <b>Sp</b>ot <b>ta</b>sk <b>nod</b>es |
| <b>Spa</b>rk <b>with</b>out <b>mana</b>ging <b>clus</b>ters, <b>b</b>ut EMR <b>runt</b>ime | **EMR Serverless** | <b>P</b>ay <b>p</b>er <b>vC</b>PU/GB-<b>sec</b>ond, <b>au</b>to <b>sca</b>le |
| <b>Spa</b>rk <b>o</b>n <b>exis</b>ting [<b>Kuber</b>netes](00-data-basics-for-beginners.md#kubernetes) | **EMR on EKS** | <b>Sha</b>res EKS <b>clus</b>ter <b>wi</b>th <b>oth</b>er <b>ap</b>ps |
| <b>Lightw</b>eight <b>p</b>er-<b>eve</b>nt <b>trans</b>forms (< 15 <b>m</b>in) | **AWS Lambda** | <b>Eve</b>nt-<b>dri</b>ven, <b>n</b>o <b>serv</b>ers |
| SQL <b>trans</b>forms <b>o</b>n S3 <b>da</b>ta | **Athena CTAS / INSERT INTO** | <b>Serve</b>rless SQL, <b>n</b>o ETL <b>co</b>de |
| SQL <b>trans</b>forms <b>ins</b>ide <b>t</b>he <b>wareh</b>ouse (<b>Extr</b>act, <b>Lo</b>ad, <b>Trans</b>form [ELT]) | **Amazon Redshift** | <b>Sto</b>red <b>proce</b>dures, <b>materi</b>alized <b>vie</b>ws, `MERGE` |
| <b>Re</b>al-<b>ti</b>me, <b>stat</b>eful <b>str</b>eam <b>proce</b>ssing | **Managed Service for [Apache Flink](00-data-basics-for-beginners.md#apache-flink)** | <b>Wind</b>ows, <b>joi</b>ns, <b>exac</b>tly-<b>on</b>ce <b>sta</b>te |
| <b>Lo</b>ng-<b>runn</b>ing <b>contain</b>erized <b>jo</b>bs <b>bey</b>ond <b>Lam</b>bda <b>lim</b>its | **ECS/EKS on Fargate**, **[AWS Batch](00-data-basics-for-beginners.md#aws-batch)** | <b>A</b>ny <b>runt</b>ime, <b>a</b>ny <b>dura</b>tion |

#### AWS Glue essentials

| <b>Feat</b>ure | <b>Explan</b>ation |
|---|---|
| **Job types** | **Spark** (<b>lar</b>ge ETL), **Spark Streaming**, **Python shell** (<b>sma</b>ll <b>jo</b>bs, <b>pan</b>das-<b>sca</b>le, <b>che</b>ap), **Ray** (<b>distri</b>buted <b>Pyt</b>hon) |
| **DynamicFrame** | <b>Glu</b>e's <b>DataF</b>rame <b>th</b>at <b>toler</b>ates <b>incons</b>istent <b>sche</b>mas. `ResolveChoice` <b>fix</b>es <b>mix</b>ed <b>typ</b>es (<b>e</b>.g., <b>a</b> <b>col</b>umn <b>th</b>at <b>i</b>s <b>somet</b>imes <b>str</b>ing, <b>somet</b>imes <b>i</b>nt). `Relationalize` <b>flat</b>tens <b>nes</b>ted JSON <b>in</b>to <b>tab</b>les. <b>Conv</b>ert <b>t</b>o <b>Spa</b>rk <b>DataF</b>rame <b>wi</b>th `toDF()` <b>wh</b>en <b>y</b>ou <b>ne</b>ed <b>Spa</b>rk APIs. |
| **Job bookmarks** | <b>Reme</b>mber <b>wh</b>at <b>w</b>as <b>alre</b>ady <b>proce</b>ssed → <b>increm</b>ental <b>loa</b>ds. <b>Nee</b>ds `job.init()`/`job.commit()` <b>a</b>nd <b>a</b> `transformation_ctx`. |
| **Pushdown predicates** | `push_down_predicate="year='2026'"` <b>filt</b>ers **partitions before listing/reading S3** → <b>mu</b>ch <b>fas</b>ter <b>o</b>n <b>partit</b>ioned <b>da</b>ta |
| **Worker types** | **G.1X / G.2X** <b>stan</b>dard; <b>lar</b>ger (<b>G</b>.4X, <b>G</b>.8X) <b>f</b>or <b>mem</b>ory-<b>hea</b>vy <b>jo</b>bs; **G.025X** <b>f</b>or <b>l</b>ow-<b>vol</b>ume <b>strea</b>ming |
| **Auto Scaling** | <b>Ad</b>ds/<b>remo</b>ves <b>work</b>ers <b>dur</b>ing <b>t</b>he <b>r</b>un; <b>p</b>ay <b>on</b>ly <b>f</b>or <b>wha</b>t's <b>us</b>ed |
| **Flex execution** | <b>Ru</b>ns <b>o</b>n <b>spa</b>re <b>capa</b>city <b>a</b>t <b>a</b> <b>low</b>er <b>pri</b>ce; <b>sta</b>rt <b>ti</b>me <b>n</b>ot <b>guara</b>nteed → **non-urgent jobs only** |
| **Glue Studio** | <b>Vis</b>ual <b>j</b>ob <b>autho</b>ring <b>th</b>at <b>gener</b>ates <b>co</b>de |
| **Glue connections** | JDBC (RDS, <b>Reds</b>hift, <b>o</b>n-<b>pr</b>em <b>datab</b>ases [DBs]), [<b>Mong</b>oDB](00-data-basics-for-beginners.md#mongodb), <b>Kaf</b>ka, <b>pl</b>us <b>market</b>place/<b>cus</b>tom <b>conne</b>ctors |
| **[Glue Data Quality](00-data-basics-for-beginners.md#aws-glue-data-quality)** | <b>Rul</b>es <b>i</b>n <b>Da</b>ta <b>Qual</b>ity <b>Defin</b>ition <b>Lang</b>uage [DQDL] (<b>s</b>ee <b>Dom</b>ain 3) |

#### Amazon EMR essentials

- **Node types:** **Primary** (<b>coordi</b>nates; <b>o</b>ne <b>p</b>er <b>clus</b>ter, <b>o</b>r 3 <b>f</b>or <b>Hi</b>gh <b>Availa</b>bility [HA]), **Core** (<b>ru</b>ns <b>tas</b>ks **and stores HDFS data**), **Task** (<b>comp</b>ute <b>on</b>ly, **no HDFS** → <b>perf</b>ect <b>f</b>or **Spot**).
- **Persistent vs transient:** <b>trans</b>ient <b>clus</b>ters <b>sp</b>in <b>u</b>p <b>f</b>or <b>a</b> <b>j</b>ob <b>a</b>nd <b>termi</b>nate → <b>ke</b>ep <b>da</b>ta <b>i</b>n **S3 via EMRFS**, <b>n</b>ot HDFS.
- **Instance fleets** <b>l</b>et <b>y</b>ou <b>m</b>ix <b>inst</b>ance <b>typ</b>es <b>a</b>nd <b>O</b>n-<b>Dem</b>and/<b>Sp</b>ot <b>wi</b>th <b>alloc</b>ation <b>strat</b>egies.
- **Managed scaling** <b>resi</b>zes <b>t</b>he <b>clus</b>ter <b>automat</b>ically.
- **Graviton** <b>insta</b>nces <b>gi</b>ve <b>bet</b>ter <b>pri</b>ce/<b>perfor</b>mance.

### Containers for data processing (skill 1.2.1)

| <b>Opt</b>ion | <b>Wh</b>en |
|---|---|
| **ECS on Fargate** | <b>Contain</b>erized ETL <b>lon</b>ger <b>th</b>an 15 <b>m</b>in, <b>n</b>o <b>serv</b>ers <b>t</b>o <b>man</b>age |
| **EKS** | <b>Organi</b>zation <b>stan</b>dard <b>i</b>s <b>Kuber</b>netes; <b>Spa</b>rk <b>oper</b>ator; **EMR on EKS** |
| **AWS Batch** | <b>Ma</b>ny <b>indepe</b>ndent <b>bat</b>ch <b>jo</b>bs, <b>que</b>ues, <b>j</b>ob <b>depend</b>encies, <b>Sp</b>ot |

<b>Optimi</b>zation <b>lev</b>ers:
- <b>Rig</b>ht-<b>si</b>ze <b>ta</b>sk CPU/<b>mem</b>ory (<b>Cloud</b>Watch <b>Conta</b>iner <b>Insi</b>ghts <b>sho</b>ws <b>act</b>ual <b>usa</b>ge).
- **Fargate Spot** / EC2 <b>Sp</b>ot <b>f</b>or <b>interru</b>ptible <b>bat</b>ch <b>wo</b>rk.
- <b>Grav</b>iton (<b>Adva</b>nced RISC <b>Mach</b>ine [ARM]) <b>ima</b>ges <b>f</b>or <b>chea</b>per <b>comp</b>ute.
- <b>Horiz</b>ontal <b>scal</b>ing (<b>mo</b>re <b>tas</b>ks/<b>po</b>ds) <b>f</b>or <b>paralle</b>lizable <b>wo</b>rk; <b>clus</b>ter <b>autos</b>caler <b>o</b>r <b>Karpe</b>nter <b>f</b>or EKS <b>nod</b>es.
- <b>Ke</b>ep <b>ima</b>ges <b>sma</b>ll <b>f</b>or <b>fas</b>ter <b>star</b>tup.

### Connecting to data sources (skill 1.2.2)

- **JDBC** (<b>Ja</b>va <b>Data</b>base <b>Connec</b>tivity) <b>a</b>nd **ODBC** (<b>Op</b>en <b>Data</b>base <b>Connec</b>tivity) <b>a</b>re <b>stan</b>dard <b>data</b>base <b>dri</b>ver APIs. <b>Gl</b>ue, EMR/<b>Spa</b>rk, <b>a</b>nd <b>Ath</b>ena <b>feder</b>ated <b>conne</b>ctors <b>u</b>se JDBC. <b>Busi</b>ness <b>Intell</b>igence (BI) <b>too</b>ls (<b>Exc</b>el, <b>Tabl</b>eau, <b>Pow</b>er BI) <b>oft</b>en <b>u</b>se ODBC.
- **Glue connection** = JDBC <b>Unif</b>orm <b>Reso</b>urce <b>Loca</b>tor (URL) + <b>creden</b>tials (<b>Secr</b>ets <b>Mana</b>ger) + VPC <b>sub</b>net + <b>secu</b>rity <b>gro</b>up.
- <b>Cus</b>tom/<b>new</b>er <b>driv</b>ers: <b>upl</b>oad <b>t</b>he JDBC <b>dri</b>ver JAR <b>t</b>o S3 <b>a</b>nd <b>refer</b>ence <b>i</b>t <b>i</b>n <b>t</b>he <b>j</b>ob.
- **Redshift** <b>a</b>nd **Athena** <b>prov</b>ide JDBC/ODBC <b>driv</b>ers <b>f</b>or <b>cli</b>ent <b>too</b>ls.
- **Redshift Data API** <b>a</b>nd **Athena API** <b>avo</b>id <b>driv</b>ers <b>enti</b>rely (<b>Hyper</b>text <b>Tran</b>sfer <b>Prot</b>ocol <b>Sec</b>ure [HTTPS] <b>cal</b>ls, <b>go</b>od <b>f</b>or <b>Lam</b>bda).

### Integrating multiple sources (skill 1.2.3)

| <b>Patt</b>ern | <b>Serv</b>ice |
|---|---|
| <b>Jo</b>in <b>da</b>ta <b>fr</b>om S3 + JDBC <b>sour</b>ces <b>i</b>n <b>o</b>ne ETL | **Glue job** <b>wi</b>th <b>mult</b>iple <b>sour</b>ces |
| <b>Que</b>ry <b>acr</b>oss S3, <b>Dyna</b>moDB, RDS, <b>Cloud</b>Watch <b>Lo</b>gs <b>i</b>n <b>o</b>ne SQL <b>state</b>ment | **Athena Federated Query** (<b>Lam</b>bda-<b>bas</b>ed <b>conne</b>ctors) |
| <b>Jo</b>in <b>wareh</b>ouse <b>tab</b>les <b>wi</b>th <b>li</b>ve <b>Aur</b>ora/RDS <b>Postg</b>reSQL <b>o</b>r <b>MyS</b>QL <b>da</b>ta | **Redshift federated query** |
| <b>Jo</b>in <b>wareh</b>ouse <b>tab</b>les <b>wi</b>th S3 [<b>da</b>ta <b>la</b>ke](00-data-basics-for-beginners.md#data-lake) | **Redshift Spectrum** |
| <b>Repli</b>cate <b>operat</b>ional DBs <b>in</b>to <b>t</b>he <b>wareh</b>ouse <b>contin</b>uously | **Zero-ETL** <b>integr</b>ations |
| <b>Centr</b>alize <b>every</b>thing <b>fir</b>st | <b>La</b>nd <b>a</b>ll <b>sour</b>ces <b>i</b>n <b>a</b>n S3 <b>da</b>ta <b>la</b>ke (<b>r</b>aw → <b>cura</b>ted) |

### Optimizing processing cost (skill 1.2.4)

- **Glue:** <b>Fl</b>ex <b>f</b>or <b>n</b>on-<b>urg</b>ent <b>jo</b>bs, <b>Au</b>to <b>Scal</b>ing, <b>rig</b>ht <b>wor</b>ker <b>ty</b>pe, <b>Pyt</b>hon <b>she</b>ll <b>inst</b>ead <b>o</b>f <b>Spa</b>rk <b>f</b>or <b>sma</b>ll <b>da</b>ta, <b>j</b>ob <b>bookm</b>arks (<b>don</b>'t <b>repro</b>cess), <b>push</b>down <b>predi</b>cates.
- **EMR:** <b>trans</b>ient <b>clus</b>ters, **Spot for task nodes**, <b>Grav</b>iton, <b>mana</b>ged <b>scal</b>ing, EMR <b>Serve</b>rless <b>f</b>or <b>interm</b>ittent <b>jo</b>bs.
- **Lambda:** <b>rig</b>ht-<b>si</b>ze <b>mem</b>ory (<b>mo</b>re <b>mem</b>ory <b>c</b>an <b>b</b>e *<b>chea</b>per* <b>i</b>f <b>i</b>t <b>shor</b>tens <b>runt</b>ime), <b>Grav</b>iton (arm64), <b>bat</b>ch <b>reco</b>rds.
- **Athena:** <b>colu</b>mnar <b>form</b>ats + <b>compre</b>ssion + <b>parti</b>tions = <b>le</b>ss <b>da</b>ta <b>scan</b>ned = <b>low</b>er <b>co</b>st.
- **Redshift:** <b>Serve</b>rless <b>f</b>or <b>interm</b>ittent <b>u</b>se, <b>pau</b>se/<b>res</b>ume <b>provis</b>ioned <b>clus</b>ters, <b>Rese</b>rved <b>Insta</b>nces <b>f</b>or <b>ste</b>ady <b>u</b>se, <b>Spec</b>trum <b>f</b>or <b>co</b>ld <b>da</b>ta.
- **Data layout:** <b>conv</b>ert <b>t</b>o <b>Parq</b>uet, <b>comp</b>act [<b>sma</b>ll <b>fil</b>es](00-data-basics-for-beginners.md#small-files-problem), <b>lifec</b>ycle <b>o</b>ld <b>da</b>ta <b>t</b>o <b>chea</b>per S3 <b>clas</b>ses.

### Format conversion (skill 1.2.6)

| <b>For</b>mat | <b>Lay</b>out | <b>Split</b>table | <b>Be</b>st <b>f</b>or |
|---|---|---|---|
| CSV | <b>R</b>ow, <b>te</b>xt | <b>Y</b>es (<b>uncomp</b>ressed <b>o</b>r <b>wi</b>th [<b>split</b>table](00-data-basics-for-beginners.md#compression-and-splittable) <b>cod</b>ec) | <b>Inges</b>tion, <b>interc</b>hange |
| JSON | <b>R</b>ow, <b>te</b>xt, <b>nes</b>ted | <b>Y</b>es, <b>li</b>ne-<b>delim</b>ited | APIs, <b>lo</b>gs |
| **Parquet** | **Columnar**, <b>typ</b>ed, <b>compr</b>essed | ✅ | **Analytics (Athena, Spectrum, Spark)**: <b>re</b>ad <b>on</b>ly <b>nee</b>ded <b>colu</b>mns |
| **ORC** | <b>Colu</b>mnar | ✅ | <b>Hi</b>ve-<b>bas</b>ed <b>analy</b>tics |
| **[Avro](00-data-basics-for-beginners.md#avro)** | <b>R</b>ow, <b>sch</b>ema <b>i</b>n <b>fi</b>le | ✅ | <b>Strea</b>ming, <b>Kaf</b>ka, <b>sch</b>ema <b>evolu</b>tion, <b>wri</b>te-<b>hea</b>vy |

**Compression codecs:** **Snappy** (<b>fa</b>st, <b>defa</b>ult <b>f</b>or <b>Parq</b>uet), **GZIP** (<b>hi</b>gh <b>compre</b>ssion; <b>a</b> <b>gzip</b>ped CSV/JSON <b>fi</b>le <b>i</b>s **not splittable**, <b>s</b>o <b>o</b>ne <b>wor</b>ker <b>p</b>er <b>fi</b>le), **Zstandard [ZSTD]** (<b>go</b>od <b>bala</b>nce), **BZIP2** (<b>split</b>table <b>b</b>ut <b>sl</b>ow), **LZO** (<b>split</b>table <b>wi</b>th <b>ind</b>ex).

**Ways to convert CSV/JSON → Parquet:**
1. **Firehose record format conversion** (<b>strea</b>ming, <b>n</b>o <b>co</b>de)
2. **Glue job** (`write_dynamic_frame` <b>wi</b>th `format="parquet"`)
3. **Athena CTAS** (`CREATE TABLE … WITH (format='PARQUET', partitioned_by=…) AS SELECT …`)
4. **EMR/Spark** <b>a</b>t <b>ve</b>ry <b>lar</b>ge <b>sca</b>le
5. **DMS** <b>wi</b>th <b>a</b>n S3 <b>tar</b>get <b>i</b>n <b>Parq</b>uet <b>for</b>mat

### Troubleshooting transformations (skill 1.2.7)

| <b>Symp</b>tom | <b>Lik</b>ely <b>cau</b>se | <b>F</b>ix |
|---|---|---|
| <b>Gl</b>ue/<b>Spa</b>rk **driver** <b>O</b>ut <b>O</b>f <b>Mem</b>ory (OOM) | `collect()` <b>t</b>o <b>dri</b>ver, <b>o</b>r <b>mill</b>ions <b>o</b>f <b>sma</b>ll <b>fil</b>es <b>trac</b>ked <b>b</b>y <b>dri</b>ver | <b>Avo</b>id `collect`, <b>u</b>se `groupFiles`/`groupSize` <b>t</b>o <b>gro</b>up <b>sma</b>ll <b>fil</b>es, <b>big</b>ger <b>wor</b>ker <b>ty</b>pe |
| **Executor** OOM / <b>o</b>ne <b>ta</b>sk <b>ru</b>ns <b>fore</b>ver | **Data skew**: <b>o</b>ne <b>k</b>ey <b>h</b>as <b>mo</b>st <b>ro</b>ws | <b>Sa</b>lt <b>t</b>he <b>k</b>ey, <b>repart</b>ition, <b>broad</b>cast <b>jo</b>in <b>t</b>he <b>sma</b>ll <b>tab</b>le, <b>lar</b>ger <b>work</b>ers |
| <b>J</b>ob <b>sl</b>ow <b>read</b>ing S3 | <b>Ma</b>ny <b>ti</b>ny <b>fil</b>es, <b>n</b>o <b>parti</b>tion <b>prun</b>ing, GZIP CSV | <b>Comp</b>act <b>fil</b>es (128 MB–1 GB), <b>push</b>down <b>predi</b>cates, <b>Parq</b>uet |
| <b>Gl</b>ue <b>j</b>ob <b>can</b>'t <b>rea</b>ch RDS | <b>Netwo</b>rking | <b>Gl</b>ue <b>conne</b>ction <b>i</b>n <b>corr</b>ect VPC/<b>sub</b>net, <b>se</b>lf-<b>refere</b>ncing <b>Secu</b>rity <b>Gro</b>up (SG) <b>ru</b>le, <b>rou</b>te/NAT, DB SG <b>all</b>ows <b>Gl</b>ue SG |
| <b>Ath</b>ena `HIVE_PARTITION_SCHEMA_MISMATCH` | <b>Parti</b>tion <b>sch</b>ema <b>diff</b>ers <b>fr</b>om <b>tab</b>le <b>sch</b>ema | <b>Upd</b>ate <b>parti</b>tions / <b>recr</b>awl <b>wi</b>th "<b>upd</b>ate <b>a</b>ll <b>parti</b>tions <b>fr</b>om <b>tab</b>le" |
| <b>Ath</b>ena <b>does</b>n't <b>s</b>ee <b>n</b>ew <b>parti</b>tions | <b>Parti</b>tions <b>n</b>ot <b>regis</b>tered | `MSCK REPAIR TABLE`, `ALTER TABLE ADD PARTITION`, **partition projection**, <b>o</b>r <b>rer</b>un <b>craw</b>ler |
| <b>Reds</b>hift `COPY` <b>fai</b>ls | <b>B</b>ad <b>ro</b>ws, <b>ty</b>pe <b>mism</b>atch, <b>wro</b>ng <b>delim</b>iter | <b>Che</b>ck `STL_LOAD_ERRORS` / `SYS_LOAD_ERROR_DETAIL`; <b>u</b>se `MAXERROR` <b>caref</b>ully |
| <b>Craw</b>ler <b>crea</b>tes <b>ma</b>ny <b>tab</b>les <b>inst</b>ead <b>o</b>f <b>o</b>ne | <b>Incons</b>istent <b>sche</b>mas <b>o</b>r <b>fol</b>der <b>struc</b>ture | "<b>Cre</b>ate <b>a</b> <b>sin</b>gle <b>sch</b>ema <b>f</b>or <b>ea</b>ch S3 <b>pa</b>th" <b>opt</b>ion, <b>consi</b>stent <b>form</b>ats, <b>s</b>et <b>tab</b>le <b>lev</b>el |

**Where to look:** <b>Cloud</b>Watch <b>Lo</b>gs (<b>dri</b>ver <b>a</b>nd <b>exec</b>utor <b>lo</b>gs), **Glue job metrics / job run insights**, **Spark User Interface [UI]** (<b>Gl</b>ue <b>a</b>nd EMR) <b>f</b>or <b>sta</b>ges, <b>sk</b>ew, <b>shuf</b>fle <b>si</b>ze, EMR <b>st</b>ep <b>lo</b>gs <b>i</b>n S3.

### Creating data APIs (skill 1.2.8)

| <b>Patt</b>ern | <b>U</b>se |
|---|---|
| **API Gateway → Lambda → DynamoDB** | <b>L</b>ow-<b>late</b>ncy <b>k</b>ey <b>look</b>ups |
| **API Gateway → Lambda → Redshift Data API** | <b>Exp</b>ose <b>wareh</b>ouse <b>quer</b>ies <b>with</b>out <b>mana</b>ging JDBC <b>connec</b>tions (<b>asy</b>nc: <b>sub</b>mit, <b>po</b>ll, <b>fet</b>ch) |
| **API Gateway → Lambda → Athena** | <b>A</b>d-<b>h</b>oc <b>quer</b>ies <b>ov</b>er <b>t</b>he <b>la</b>ke (<b>asy</b>nc, <b>resu</b>lts <b>i</b>n S3) |
| **AWS AppSync** (<b>Grap</b>hQL) | <b>Flex</b>ible <b>cli</b>ent-<b>defi</b>ned <b>quer</b>ies <b>acr</b>oss <b>mult</b>iple <b>da</b>ta <b>sour</b>ces |
| **Redshift data sharing / Data Exchange** | <b>Sha</b>re <b>da</b>ta <b>wi</b>th <b>oth</b>er <b>tea</b>ms/<b>custo</b>mers <b>with</b>out <b>buil</b>ding <b>a</b>n API |

<b>A</b>dd: API <b>ke</b>ys/<b>usa</b>ge <b>pla</b>ns <b>o</b>r <b>Cogn</b>ito/[<b>Iden</b>tity <b>a</b>nd <b>Acc</b>ess <b>Manag</b>ement [IAM]](00-data-basics-for-beginners.md#aws-iam) <b>au</b>th, <b>cach</b>ing <b>i</b>n API <b>Gate</b>way, <b>throt</b>tling <b>lim</b>its.

### Volume, velocity, variety (skill 1.2.9)

| <b>V</b> | <b>Mean</b>ing | <b>Des</b>ign <b>imp</b>act |
|---|---|---|
| **Volume** | <b>H</b>ow <b>mu</b>ch <b>da</b>ta (GB → PB) | <b>Distri</b>buted <b>proce</b>ssing (<b>Spa</b>rk/EMR/<b>Gl</b>ue), <b>colu</b>mnar <b>stor</b>age, <b>partit</b>ioning |
| **Velocity** | <b>H</b>ow <b>fa</b>st <b>i</b>t <b>arri</b>ves (<b>bat</b>ch → <b>re</b>al <b>ti</b>me) | <b>Bat</b>ch <b>jo</b>bs <b>v</b>s <b>strea</b>ming (KDS/MSK/<b>Fli</b>nk) |
| **Variety** | <b>Typ</b>es <b>o</b>f <b>da</b>ta | **Structured** (<b>tab</b>les, <b>fix</b>ed <b>sch</b>ema: RDS/<b>Reds</b>hift), **semi-structured** (JSON, <b>Exten</b>sible <b>Mar</b>kup <b>Lang</b>uage [XML], <b>Av</b>ro: S3 + <b>Gl</b>ue, <b>Reds</b>hift `SUPER`), **unstructured** (<b>ima</b>ges, <b>Port</b>able <b>Docu</b>ment <b>For</b>mat <b>fil</b>es [PDFs], <b>aud</b>io, <b>fr</b>ee <b>te</b>xt: S3 + <b>Artif</b>icial <b>Intell</b>igence [AI] <b>serv</b>ices/LLMs) |

### 🆕 Integrating LLMs for data processing (skill 1.2.10)

**Why:** LLMs <b>tu</b>rn <b>unstru</b>ctured <b>te</b>xt <b>in</b>to <b>struc</b>tured <b>da</b>ta <b>ins</b>ide <b>a</b> <b>pipe</b>line: <b>clas</b>sify <b>supp</b>ort <b>tick</b>ets, <b>extr</b>act <b>enti</b>ties <b>fr</b>om <b>contr</b>acts, <b>summa</b>rize <b>ca</b>ll <b>transc</b>ripts, <b>standa</b>rdize <b>mes</b>sy <b>addre</b>sses, <b>trans</b>late, <b>o</b>r <b>det</b>ect <b>senti</b>ment.

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

| <b>Opt</b>ion | <b>Wh</b>en |
|---|---|
| **Lambda or Glue calling [Amazon Bedrock](00-data-basics-for-beginners.md#amazon-bedrock)** | <b>P</b>er-<b>rec</b>ord <b>enric</b>hment <b>i</b>n <b>a</b>n <b>exis</b>ting <b>pipe</b>line |
| **Step Functions optimized Bedrock integration** | <b>Orches</b>trated <b>work</b>flow; <b>ca</b>ll <b>a</b> <b>mod</b>el <b>dire</b>ctly <b>fr</b>om <b>a</b> <b>sta</b>te, <b>n</b>o <b>Lam</b>bda <b>nee</b>ded |
| **Bedrock batch inference** | <b>Lar</b>ge <b>data</b>sets, <b>n</b>ot <b>late</b>ncy-<b>sensi</b>tive → **lower cost than on-demand**, <b>avo</b>ids <b>throt</b>tling |
| **Redshift Machine Learning (ML) + Bedrock** (`CREATE EXTERNAL MODEL`) | <b>Anal</b>ysts <b>ca</b>ll <b>a</b> <b>Lar</b>ge <b>Lang</b>uage <b>Mod</b>el (LLM) <b>fr</b>om SQL <b>ins</b>ide <b>Reds</b>hift |
| **[Amazon Comprehend](00-data-basics-for-beginners.md#amazon-comprehend)** | <b>Stan</b>dard <b>Natu</b>ral <b>Lang</b>uage <b>Proce</b>ssing [NLP] (<b>senti</b>ment, <b>enti</b>ties, <b>Perso</b>nally <b>Identi</b>fiable <b>Inform</b>ation [PII], <b>lang</b>uage) <b>with</b>out <b>prom</b>pts. <b>Oft</b>en <b>simp</b>ler <b>a</b>nd <b>chea</b>per <b>f</b>or <b>tho</b>se <b>spec</b>ific <b>tas</b>ks. |
| **Amazon Q** (<b>i</b>n <b>Quick</b>Sight / <b>Reds</b>hift <b>que</b>ry <b>edi</b>tor) | <b>Natu</b>ral <b>lang</b>uage → SQL <b>o</b>r <b>insi</b>ghts <b>f</b>or <b>peo</b>ple, <b>n</b>ot <b>pipe</b>line <b>proce</b>ssing |

**Design considerations:**
- **Throttling/quotas:** <b>back</b>off + <b>retr</b>ies, SQS <b>buffe</b>ring, <b>o</b>r <b>bat</b>ch <b>infer</b>ence.
- **Cost:** <b>tok</b>ens <b>i</b>n + <b>o</b>ut <b>×</b> <b>reco</b>rds. <b>U</b>se <b>t</b>he <b>smal</b>lest <b>mod</b>el <b>th</b>at <b>mee</b>ts <b>qual</b>ity; <b>bat</b>ch <b>f</b>or <b>bu</b>lk.
- **Determinism:** <b>l</b>ow <b>temper</b>ature, <b>a</b>sk <b>f</b>or **structured JSON output**, <b>vali</b>date <b>t</b>he <b>sch</b>ema, <b>se</b>nd <b>inva</b>lid <b>outp</b>uts <b>t</b>o <b>a</b> <b>ret</b>ry/DLQ <b>pa</b>th.
- **Privacy:** <b>ma</b>sk PII <b>bef</b>ore <b>send</b>ing (<b>Gl</b>ue <b>sensi</b>tive <b>da</b>ta <b>detec</b>tion / <b>Compr</b>ehend), <b>u</b>se **Bedrock Guardrails**, <b>u</b>se VPC <b>endpo</b>ints (<b>Privat</b>eLink). <b>Bedr</b>ock <b>does</b>n't <b>u</b>se <b>yo</b>ur <b>prom</b>pts <b>t</b>o <b>tra</b>in <b>ba</b>se <b>mod</b>els.

---

## Task 1.3: Orchestrate data pipelines

### Orchestration services (skill 1.3.1)

| <b>Serv</b>ice | <b>Be</b>st <b>f</b>or | <b>K</b>ey <b>fac</b>ts |
|---|---|---|
| **AWS Step Functions** | <b>Serve</b>rless <b>workf</b>lows <b>call</b>ing <b>ma</b>ny AWS <b>serv</b>ices | <b>Vis</b>ual <b>sta</b>te <b>mach</b>ines (<b>Ama</b>zon <b>Sta</b>tes <b>Lang</b>uage [ASL] JSON); **Standard** (<b>u</b>p <b>t</b>o 1 <b>ye</b>ar, <b>exac</b>tly-<b>on</b>ce, <b>fu</b>ll <b>hist</b>ory) <b>v</b>s **Express** (<b>u</b>p <b>t</b>o 5 <b>m</b>in, <b>ve</b>ry <b>hi</b>gh <b>vol</b>ume, <b>a</b>t-<b>lea</b>st-<b>on</b>ce, <b>chea</b>per); `.sync` <b>wai</b>ts <b>f</b>or <b>Gl</b>ue/EMR/<b>Ath</b>ena/<b>Bat</b>ch <b>jo</b>bs <b>t</b>o <b>fin</b>ish; **Retry**/**Catch** <b>p</b>er <b>sta</b>te; **Parallel**, **Choice**, **Wait**, **Map**; **Distributed Map** <b>proce</b>sses <b>mill</b>ions <b>o</b>f S3 <b>obje</b>cts <b>i</b>n <b>para</b>llel |
| **Amazon MWAA** | <b>Apa</b>che <b>Airf</b>low <b>Dire</b>cted <b>Acyc</b>lic <b>Gra</b>phs (DAGs) <b>writ</b>ten <b>i</b>n <b>Pyt</b>hon | <b>Pi</b>ck <b>wh</b>en <b>t</b>he <b>te</b>am <b>alre</b>ady <b>us</b>es <b>Airf</b>low, <b>nee</b>ds <b>ma</b>ny <b>thi</b>rd-<b>par</b>ty/<b>op</b>en-<b>sou</b>rce <b>opera</b>tors, <b>o</b>r <b>comp</b>lex <b>depen</b>dency <b>sched</b>uling. DAGs <b>a</b>nd <b>plug</b>ins/<b>requir</b>ements <b>li</b>ve <b>i</b>n <b>a</b>n S3 <b>buc</b>ket. |
| **AWS Glue workflows** | <b>Cha</b>ins <b>o</b>f <b>Gl</b>ue <b>craw</b>lers <b>a</b>nd <b>jo</b>bs <b>on</b>ly | <b>Trig</b>gers (<b>sched</b>uled, <b>o</b>n-<b>dem</b>and, <b>condit</b>ional <b>o</b>n <b>succ</b>ess/<b>fail</b>ure/<b>compl</b>etion); <b>simp</b>lest <b>f</b>or <b>Gl</b>ue-<b>on</b>ly <b>pipel</b>ines |
| **Amazon EventBridge** | <b>Eve</b>nt-<b>dri</b>ven <b>sta</b>rts <b>a</b>nd <b>sched</b>ules | <b>Sta</b>rts <b>a</b>ny <b>o</b>f <b>t</b>he <b>abo</b>ve <b>o</b>n S3 <b>eve</b>nts, <b>sched</b>ules, <b>o</b>r <b>cus</b>tom <b>eve</b>nts |
| **AWS Lambda** | <b>Gl</b>ue <b>co</b>de <b>betw</b>een <b>ste</b>ps | <b>N</b>ot <b>a</b>n <b>orches</b>trator <b>b</b>y <b>its</b>elf (15 <b>m</b>in <b>lim</b>it, <b>n</b>o <b>sta</b>te) |

**Choosing:**
- <b>On</b>ly <b>Gl</b>ue <b>jo</b>bs <b>a</b>nd <b>craw</b>lers → **Glue workflows**
- <b>Mix</b>ed AWS <b>serv</b>ices, <b>serve</b>rless, <b>lea</b>st <b>o</b>ps → **Step Functions**
- <b>Exis</b>ting <b>Airf</b>low / <b>Pyt</b>hon DAGs / <b>op</b>en-<b>sou</b>rce <b>portab</b>ility → **MWAA**
- "<b>Sta</b>rt <b>t</b>he <b>pipe</b>line <b>wh</b>en <b>a</b> <b>fi</b>le <b>lan</b>ds" → **EventBridge rule → Step Functions**

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

| <b>Qual</b>ity | <b>Techn</b>ique |
|---|---|
| **Fault tolerance** | <b>Retr</b>ies <b>wi</b>th <b>expone</b>ntial <b>back</b>off, <b>Cat</b>ch → <b>fall</b>back/<b>ale</b>rt, **dead-letter queues** (SQS DLQ, <b>Lam</b>bda <b>o</b>n-<b>fail</b>ure <b>destin</b>ations), <b>checkpo</b>inting (<b>bookm</b>arks, KCL, <b>Fli</b>nk) |
| **Idempotency** | <b>R</b>e-<b>runn</b>ing <b>a</b> <b>st</b>ep <b>giv</b>es <b>t</b>he <b>sa</b>me <b>res</b>ult: <b>overw</b>rite <b>parti</b>tions <b>inst</b>ead <b>o</b>f <b>appen</b>ding, <b>u</b>se `MERGE`/<b>upse</b>rts, <b>determi</b>nistic <b>out</b>put <b>pat</b>hs |
| **Availability** | <b>Mul</b>ti-AZ <b>mana</b>ged <b>serv</b>ices, <b>deco</b>uple <b>sta</b>ges <b>wi</b>th SQS/KDS <b>s</b>o <b>o</b>ne <b>sl</b>ow <b>sta</b>ge <b>does</b>n't <b>bre</b>ak <b>oth</b>ers |
| **Scalability** | <b>Serve</b>rless/<b>au</b>to-<b>scal</b>ing <b>serv</b>ices (<b>Gl</b>ue <b>Au</b>to <b>Scal</b>ing, KDS <b>o</b>n-<b>dem</b>and, <b>Lam</b>bda, EMR <b>mana</b>ged <b>scal</b>ing), <b>parti</b>tion <b>da</b>ta <b>f</b>or <b>parall</b>elism |
| **Performance** | <b>Para</b>llel <b>sta</b>tes, <b>Distri</b>buted <b>M</b>ap, <b>colu</b>mnar <b>form</b>ats, <b>rig</b>ht-<b>siz</b>ed <b>comp</b>ute |

### Serverless workflows (skill 1.3.3)

<b>A</b> <b>ful</b>ly <b>serve</b>rless <b>pipe</b>line: **S3 → EventBridge → Step Functions → Lambda / Glue / Athena / Redshift Serverless → SNS**. <b>The</b>re <b>a</b>re <b>n</b>o <b>serv</b>ers <b>t</b>o <b>pat</b>ch <b>a</b>nd <b>every</b>thing <b>sca</b>les <b>automat</b>ically, <b>s</b>o <b>it</b>'s <b>usua</b>lly <b>t</b>he <b>ans</b>wer <b>f</b>or "<b>lea</b>st <b>operat</b>ional <b>over</b>head."

<b>Mainte</b>nance <b>poi</b>nts: <b>vers</b>ion <b>t</b>he <b>sta</b>te <b>mach</b>ine <b>defin</b>ition <b>i</b>n <b>G</b>it <b>a</b>nd <b>dep</b>loy <b>wi</b>th <b>I</b>aC/SAM; <b>u</b>se <b>Cloud</b>Watch <b>metr</b>ics (`ExecutionsFailed`, `ExecutionsTimedOut`) <b>a</b>nd <b>X</b>-<b>R</b>ay <b>trac</b>ing; <b>u</b>se <b>St</b>ep <b>Funct</b>ions <b>vers</b>ions <b>a</b>nd <b>alia</b>ses <b>f</b>or <b>sa</b>fe <b>roll</b>out.

### Notifications and alerts (skill 1.3.4)

| | <b>Ama</b>zon SNS | <b>Ama</b>zon SQS |
|---|---|---|
| <b>Mod</b>el | **Push**, <b>p</b>ub/<b>s</b>ub | **Pull**, <b>que</b>ue |
| <b>U</b>se | <b>Ale</b>rts <b>t</b>o <b>ema</b>il/<b>Sho</b>rt <b>Mess</b>age <b>Serv</b>ice (SMS)/HTTP/<b>Lam</b>bda; <b>f</b>an-<b>o</b>ut <b>t</b>o <b>ma</b>ny <b>subscr</b>ibers | <b>Buf</b>fer <b>wo</b>rk, <b>deco</b>uple <b>produ</b>cers/<b>consu</b>mers, DLQ <b>f</b>or <b>fail</b>ures |
| <b>Typi</b>cal <b>ex</b>am <b>u</b>se | "<b>Not</b>ify <b>t</b>he <b>te</b>am <b>wh</b>en <b>t</b>he <b>Gl</b>ue <b>j</b>ob <b>fai</b>ls" | "<b>Ho</b>ld <b>fai</b>led <b>mess</b>ages <b>f</b>or <b>lat</b>er <b>reproc</b>essing", "<b>smo</b>oth <b>spi</b>kes <b>in</b>to <b>a</b> <b>data</b>base" |

<b>Com</b>mon <b>ale</b>rt <b>wir</b>ing: **Glue job state change → EventBridge rule → SNS**; **CloudWatch alarm → SNS**; **Step Functions Catch → SNS publish**. <b>U</b>se **SNS First-In, First-Out (FIFO) + SQS FIFO** <b>wh</b>en <b>ord</b>er <b>a</b>nd <b>exac</b>tly-<b>on</b>ce <b>deli</b>very <b>mat</b>ter.

---

## Task 1.4: Apply programming concepts

### Optimizing code (skill 1.4.1)

- **Read less:** <b>parti</b>tion <b>prun</b>ing, <b>col</b>umn <b>prun</b>ing (`SELECT` <b>on</b>ly <b>nee</b>ded <b>colu</b>mns), <b>predi</b>cate <b>push</b>down, <b>colu</b>mnar <b>form</b>ats.
- **Spark specifics:** <b>pre</b>fer <b>bui</b>lt-<b>i</b>n <b>funct</b>ions <b>ov</b>er <b>Pyt</b>hon <b>Us</b>er-<b>Defi</b>ned <b>Funct</b>ions [UDFs] (UDFs <b>a</b>re <b>sl</b>ow <b>a</b>nd <b>blo</b>ck <b>optimi</b>zation); <b>broad</b>cast <b>sma</b>ll <b>tab</b>les <b>i</b>n <b>joi</b>ns; `repartition`/`coalesce` <b>t</b>o <b>cont</b>rol <b>fi</b>le <b>cou</b>nts; <b>cac</b>he <b>on</b>ly <b>reu</b>sed <b>DataF</b>rames; <b>avo</b>id `collect()`.
- **Batching:** <b>bat</b>ch API <b>cal</b>ls (`PutRecords`, `BatchWriteItem`) <b>inst</b>ead <b>o</b>f <b>o</b>ne <b>ca</b>ll <b>p</b>er <b>rec</b>ord.
- **Connection reuse:** <b>i</b>n <b>Lam</b>bda, <b>cre</b>ate SDK <b>clie</b>nts <b>a</b>nd DB <b>connec</b>tions **outside the handler** <b>s</b>o <b>wa</b>rm <b>invoca</b>tions <b>reu</b>se <b>th</b>em.
- **SQL:** <b>fil</b>ter <b>ear</b>ly, <b>avo</b>id `SELECT *`, <b>u</b>se <b>win</b>dow <b>funct</b>ions <b>inst</b>ead <b>o</b>f <b>se</b>lf-<b>joi</b>ns, <b>u</b>se `UNION ALL` <b>inst</b>ead <b>o</b>f `UNION` <b>wh</b>en <b>dupli</b>cates <b>a</b>re <b>impos</b>sible.

### Configuring Lambda (skill 1.4.2)

| <b>Sett</b>ing | <b>Ran</b>ge / <b>beha</b>vior | <b>Ex</b>am <b>ang</b>le |
|---|---|---|
| **Memory** | 128 MB – 10,240 MB; **Central Processing Unit (CPU) scales with memory** | CPU-<b>bou</b>nd <b>j</b>ob <b>sl</b>ow → <b>incr</b>ease <b>mem</b>ory |
| **Timeout** | <b>U</b>p <b>t</b>o **15 minutes** | <b>Lon</b>ger <b>wo</b>rk → <b>Gl</b>ue, ECS/<b>Farg</b>ate, <b>St</b>ep <b>Funct</b>ions |
| **Ephemeral storage (/tmp)** | 512 MB – 10 GB | <b>Tempo</b>rary <b>lar</b>ge <b>fil</b>es |
| **Reserved concurrency** | <b>Guara</b>ntees **and caps** <b>concur</b>rency <b>f</b>or <b>a</b> <b>func</b>tion | <b>Prot</b>ect <b>a</b> <b>downs</b>tream DB <b>fr</b>om <b>t</b>oo <b>ma</b>ny <b>connec</b>tions; <b>ens</b>ure <b>crit</b>ical <b>func</b>tion <b>alw</b>ays <b>h</b>as <b>capa</b>city |
| **Provisioned concurrency** | <b>P</b>re-<b>initia</b>lized <b>enviro</b>nments | <b>Elimi</b>nate **cold starts** <b>f</b>or <b>late</b>ncy-<b>sensi</b>tive APIs |
| **Account concurrency** | <b>Regi</b>onal <b>quo</b>ta (1,000 <b>defa</b>ult, <b>c</b>an <b>b</b>e <b>rai</b>sed) | <b>Throt</b>tling <b>acr</b>oss <b>a</b>ll <b>funct</b>ions |
| **Layers** | <b>Sha</b>red <b>libra</b>ries/<b>depend</b>encies | <b>Reu</b>se <b>pan</b>das/<b>pyar</b>row <b>acr</b>oss <b>funct</b>ions |
| **Architecture** | x86_64 <b>o</b>r **arm64 (Graviton)** | <b>Bet</b>ter <b>pri</b>ce/<b>perfor</b>mance |
| **VPC** | <b>Nee</b>ded <b>t</b>o <b>rea</b>ch <b>priv</b>ate <b>resou</b>rces (RDS, <b>Elas</b>tic <b>Fi</b>le <b>Sys</b>tem [EFS]) | <b>Inte</b>rnet <b>acc</b>ess <b>th</b>en <b>requ</b>ires <b>a</b> NAT <b>gate</b>way (<b>o</b>r VPC <b>endpo</b>ints <b>f</b>or AWS <b>serv</b>ices) |

### Languages and frameworks (skill 1.4.3)

<b>Y</b>ou <b>ne</b>ed **concepts, not exact syntax**: <b>Pyt</b>hon (<b>PySp</b>ark, <b>pan</b>das, boto3), **SQL** (<b>mo</b>st <b>impor</b>tant), <b>Sca</b>la/<b>Ja</b>va (<b>Spa</b>rk, <b>Fli</b>nk, <b>Kaf</b>ka), <b>R</b> (<b>stati</b>stics), <b>Ba</b>sh/<b>Power</b>Shell (<b>autom</b>ation <b>a</b>nd <b>scri</b>pts).

**SQL you should be fluent in:** `JOIN` <b>typ</b>es, `GROUP BY`/`HAVING`, <b>win</b>dow <b>funct</b>ions (`ROW_NUMBER() OVER (PARTITION BY … ORDER BY …)` <b>f</b>or <b>dedupli</b>cation, `LAG`/`LEAD`, <b>runn</b>ing <b>tot</b>als), <b>Com</b>mon <b>Tab</b>le <b>Expres</b>sions [CTEs] (`WITH`), `CASE`, `MERGE`/<b>ups</b>ert, `CREATE VIEW`/<b>materi</b>alized <b>vie</b>ws.

### Software engineering best practices (skill 1.4.4)

- **Version control:** <b>G</b>it <b>f</b>or <b>a</b>ll ETL <b>co</b>de, SQL, DAGs, <b>I</b>aC. <b>Bran</b>ches + <b>pu</b>ll <b>requ</b>ests + <b>co</b>de <b>rev</b>iew. <b>Kn</b>ow `clone`, `commit`, `push`, `pull`, `branch`, `merge`, `rebase` <b>a</b>t <b>a</b> <b>conc</b>ept <b>lev</b>el.
- **Testing:** <b>un</b>it <b>tes</b>ts <b>f</b>or <b>trans</b>form <b>funct</b>ions (<b>pyt</b>est; <b>Gl</b>ue <b>off</b>ers <b>a</b> <b>loc</b>al [<b>Doc</b>ker](00-data-basics-for-beginners.md#docker-and-containers) <b>ima</b>ge <b>f</b>or <b>test</b>ing <b>jo</b>bs), <b>integr</b>ation <b>tes</b>ts <b>o</b>n <b>sam</b>ple <b>da</b>ta, **data quality tests** <b>a</b>s <b>pipe</b>line <b>gat</b>es.
- **Logging:** <b>struc</b>tured <b>lo</b>gs <b>t</b>o <b>Cloud</b>Watch <b>Lo</b>gs; <b>Gl</b>ue <b>conti</b>nuous <b>logg</b>ing; <b>Spa</b>rk <b>eve</b>nt <b>lo</b>gs <b>f</b>or <b>t</b>he <b>Spa</b>rk UI.
- **Monitoring:** <b>Cloud</b>Watch <b>metr</b>ics <b>a</b>nd <b>ala</b>rms, <b>j</b>ob <b>r</b>un <b>insi</b>ghts, <b>dashb</b>oards (<b>deta</b>ils <b>i</b>n <b>Dom</b>ain 3).

### IaC: CloudFormation, CDK, SAM (skills 1.4.5, 1.4.6, 1.4.8)

| <b>To</b>ol | <b>Wh</b>at <b>i</b>t <b>i</b>s | <b>Cho</b>ose <b>wh</b>en |
|---|---|---|
| **AWS CloudFormation** | <b>Declar</b>ative YAML <b>Ain</b>'t <b>Mar</b>kup <b>Lang</b>uage (YAML)/JSON <b>templ</b>ates → <b>sta</b>cks; <b>cha</b>nge <b>se</b>ts <b>prev</b>iew <b>chan</b>ges; <b>dri</b>ft <b>detec</b>tion; **StackSets** <b>dep</b>loy <b>acr</b>oss <b>acco</b>unts/<b>Regi</b>ons | <b>Stan</b>dard <b>repea</b>table <b>inf</b>ra <b>f</b>or <b>a</b>ny AWS <b>reso</b>urce |
| **AWS CDK** | <b>Def</b>ine <b>inf</b>ra <b>i</b>n <b>Pyt</b>hon/<b>TypeS</b>cript/<b>Ja</b>va/<b>e</b>tc. <b>usi</b>ng <b>const</b>ructs → <b>synthe</b>sizes <b>CloudFo</b>rmation | <b>Devel</b>opers <b>pre</b>fer <b>re</b>al <b>progra</b>mming <b>langu</b>ages, <b>loo</b>ps, <b>reus</b>able <b>compo</b>nents |
| **AWS SAM** | <b>CloudFo</b>rmation <b>exten</b>sion <b>f</b>or <b>serve</b>rless (`AWS::Serverless::Function`, `::StateMachine`, `::SimpleTable`, `::Api`); <b>Comm</b>and <b>Li</b>ne <b>Inter</b>face (CLI): `sam build`, `sam deploy`, `sam local invoke` | **Package and deploy serverless pipelines** (<b>Lam</b>bda + <b>St</b>ep <b>Funct</b>ions + <b>Dyna</b>moDB), <b>te</b>st <b>Lam</b>bda <b>loca</b>lly |

> <b>Ex</b>am <b>sig</b>nal: "<b>repea</b>table <b>deploy</b>ments <b>acr</b>oss <b>d</b>ev/<b>te</b>st/<b>pr</b>od" → <b>I</b>aC. "<b>Serve</b>rless <b>pipe</b>line, <b>loc</b>al <b>test</b>ing, <b>pack</b>age <b>Lam</b>bda <b>co</b>de" → **SAM**. "<b>Devel</b>opers <b>wa</b>nt <b>TypeS</b>cript/<b>Pyt</b>hon <b>f</b>or <b>inf</b>ra" → **CDK**.

### Storage volumes in Lambda (skill 1.4.7)

| <b>Opt</b>ion | <b>Si</b>ze | <b>Persis</b>tence | <b>U</b>se |
|---|---|---|---|
| **/tmp (ephemeral)** | 512 MB – 10 GB | <b>P</b>er <b>execu</b>tion <b>enviro</b>nment <b>on</b>ly; <b>lo</b>st <b>wh</b>en <b>it</b>'s <b>recy</b>cled | <b>Scra</b>tch <b>spa</b>ce <b>dur</b>ing <b>a</b>n <b>invoc</b>ation |
| **Amazon EFS mount** | <b>Elas</b>tic | **Persistent, shared** <b>acr</b>oss <b>invoca</b>tions <b>a</b>nd <b>funct</b>ions | <b>Lar</b>ge <b>refer</b>ence <b>fil</b>es, ML <b>mod</b>els, <b>sha</b>red <b>sta</b>te, <b>fil</b>es > 10 GB <b>tot</b>al |
| **S3** | <b>Unlim</b>ited | <b>Persi</b>stent | <b>Inp</b>ut/<b>out</b>put <b>obje</b>cts (<b>n</b>ot <b>moun</b>ted, <b>acce</b>ssed <b>b</b>y API) |
| **Layers / container image** | <b>U</b>p <b>t</b>o 250 MB <b>unzi</b>pped / 10 GB <b>ima</b>ge | <b>Re</b>ad-<b>on</b>ly | <b>Libra</b>ries <b>a</b>nd <b>sta</b>tic <b>ass</b>ets |

**EFS requirements:** <b>t</b>he <b>Lam</b>bda <b>mu</b>st <b>b</b>e <b>i</b>n <b>t</b>he **same VPC** (<b>subn</b>ets <b>wi</b>th <b>mou</b>nt <b>targ</b>ets), <b>u</b>se <b>a</b>n **EFS access point**, <b>a</b>nd <b>t</b>he <b>secu</b>rity <b>gro</b>ups <b>mu</b>st <b>all</b>ow <b>Netw</b>ork <b>Fi</b>le <b>Sys</b>tem [NFS] (TCP 2049).

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

- **Continuous integration:** <b>eve</b>ry <b>com</b>mit <b>i</b>s <b>bui</b>lt <b>a</b>nd <b>tes</b>ted <b>automat</b>ically.
- **Continuous delivery/deployment:** <b>tes</b>ted <b>artif</b>acts <b>a</b>re <b>rele</b>ased <b>t</b>o <b>enviro</b>nments <b>automat</b>ically (<b>wi</b>th <b>o</b>r <b>with</b>out <b>a</b> <b>man</b>ual <b>appr</b>oval <b>ga</b>te).
- <b>Ke</b>ep <b>enviro</b>nment-<b>spec</b>ific <b>val</b>ues <b>i</b>n <b>param</b>eters (<b>Syst</b>ems <b>Mana</b>ger [SSM] <b>Param</b>eter <b>Sto</b>re), <b>n</b>ot <b>i</b>n <b>co</b>de.

### Distributed computing (skill 1.4.10)

- **Definition:** <b>split</b>ting <b>wo</b>rk <b>acr</b>oss <b>ma</b>ny <b>mach</b>ines <b>th</b>at <b>wo</b>rk <b>i</b>n <b>para</b>llel, <b>th</b>en <b>combi</b>ning <b>resu</b>lts.
- **Spark model:** <b>a</b> **driver** <b>pla</b>ns <b>t</b>he <b>j</b>ob <b>a</b>s <b>a</b> DAG <b>o</b>f <b>sta</b>ges; **executors** <b>o</b>n <b>wor</b>ker <b>nod</b>es <b>proc</b>ess **partitions** <b>o</b>f <b>da</b>ta <b>i</b>n <b>para</b>llel; **shuffles** <b>mo</b>ve <b>da</b>ta <b>betw</b>een <b>nod</b>es <b>f</b>or <b>joi</b>ns/<b>aggreg</b>ations <b>a</b>nd <b>a</b>re <b>expen</b>sive; <b>transfor</b>mations <b>a</b>re **lazy** <b>a</b>nd <b>r</b>un <b>wh</b>en <b>a</b>n <b>act</b>ion <b>i</b>s <b>cal</b>led.
- **MapReduce:** <b>m</b>ap (<b>proc</b>ess <b>chu</b>nks <b>i</b>n <b>para</b>llel) → <b>shuf</b>fle/<b>so</b>rt → <b>red</b>uce (<b>aggre</b>gate).
- **Key ideas:** <b>horiz</b>ontal <b>scal</b>ing (<b>a</b>dd <b>nod</b>es), <b>da</b>ta <b>loca</b>lity, <b>partit</b>ioning, <b>fau</b>lt <b>toler</b>ance <b>v</b>ia <b>r</b>e-<b>comput</b>ation <b>o</b>r <b>replic</b>ation, [<b>da</b>ta <b>sk</b>ew](00-data-basics-for-beginners.md#data-skew) <b>a</b>s <b>t</b>he <b>ma</b>in <b>perfor</b>mance <b>kil</b>ler.

### Data structures and algorithms (skill 1.4.11)

| <b>Struc</b>ture | <b>Whe</b>re <b>i</b>t <b>sho</b>ws <b>u</b>p <b>i</b>n <b>da</b>ta <b>engine</b>ering |
|---|---|
| **Graph** (<b>nod</b>es + <b>edg</b>es) | <b>Work</b>flow DAGs (<b>Airf</b>low, <b>St</b>ep <b>Funct</b>ions, <b>Spa</b>rk), [<b>da</b>ta <b>line</b>age](00-data-basics-for-beginners.md#data-lineage), <b>relati</b>onship <b>da</b>ta <b>i</b>n **[Amazon Neptune](00-data-basics-for-beginners.md#amazon-neptune)** |
| **Tree** | <b>B</b>-<b>tr</b>ee <b>inde</b>xes <b>i</b>n <b>datab</b>ases, <b>nes</b>ted JSON/<b>Parq</b>uet <b>sche</b>mas, <b>deci</b>sion <b>log</b>ic |
| **Hash table** | <b>Ha</b>sh <b>partit</b>ioning (<b>Kine</b>sis <b>parti</b>tion <b>ke</b>ys, <b>Reds</b>hift KEY <b>distri</b>bution), <b>ha</b>sh <b>joi</b>ns, <b>dedupli</b>cation |
| **Queue** | SQS, <b>Kaf</b>ka <b>top</b>ics, <b>buffe</b>ring <b>betw</b>een <b>sta</b>ges |
| **Array/list** | <b>Colu</b>mnar <b>stor</b>age, <b>batc</b>hes |

<b>Kn</b>ow <b>B</b>ig-<b>O</b> <b>bas</b>ics: <b>a</b> <b>loo</b>kup <b>i</b>n <b>a</b> <b>ha</b>sh <b>tab</b>le <b>i</b>s <b>O</b>(1) <b>o</b>n <b>aver</b>age; <b>a</b> <b>so</b>rt <b>i</b>s <b>O</b>(<b>n</b> <b>l</b>og <b>n</b>); <b>nes</b>ted-<b>lo</b>op <b>joi</b>ns <b>a</b>re <b>O</b>(<b>n</b>×m), <b>whi</b>ch <b>i</b>s <b>w</b>hy <b>engi</b>nes <b>pre</b>fer <b>ha</b>sh <b>o</b>r <b>broad</b>cast <b>joi</b>ns.

---

## Gotchas and exam traps

- **"Near real time" + "deliver to S3/Redshift/OpenSearch" + "least operational overhead"** → **Firehose**, <b>n</b>ot KDS + <b>cus</b>tom <b>Lam</b>bda <b>consu</b>mers.
- **"Real time" + "multiple independent consumers" + "replay"** → **KDS** (<b>a</b>dd **enhanced fan-out** <b>i</b>f <b>consu</b>mers <b>sl</b>ow <b>ea</b>ch <b>oth</b>er <b>do</b>wn).
- **"Kafka" anywhere in the question** → **MSK**.
- **Firehose has no replay.** <b>I</b>f <b>reproc</b>essing <b>matt</b>ers, <b>ke</b>ep <b>r</b>aw <b>da</b>ta <b>i</b>n S3 <b>o</b>r <b>p</b>ut KDS <b>i</b>n <b>fro</b>nt.
- **Throttling on one shard while overall throughput is low** → <b>h</b>ot <b>parti</b>tion <b>k</b>ey, <b>n</b>ot "<b>a</b>dd <b>mo</b>re <b>sha</b>rds."
- **Lambda behind KDS needs more throughput without resharding** → <b>rai</b>se **parallelization factor** (<b>u</b>p <b>t</b>o 10).
- **One bad record blocks a Kinesis shard** → **bisect batch on error** + <b>m</b>ax <b>retr</b>ies + <b>o</b>n-<b>fail</b>ure <b>destin</b>ation.
- **"Convert streaming JSON to Parquet with no code"** → **Firehose record format conversion** (<b>us</b>es <b>Gl</b>ue <b>tab</b>le <b>sch</b>ema).
- **"Process only new data since the last run"** → **Glue job bookmarks**.
- **"Non-urgent nightly Glue job, cut cost"** → **Glue Flex**.
- **"Small dataset, simple Python transform"** → **Glue Python shell** <b>o</b>r <b>Lam</b>bda, <b>n</b>ot <b>a</b> <b>Spa</b>rk <b>j</b>ob.
- **"Many Lambdas exhaust RDS connections"** → **RDS Proxy** (<b>a</b>nd/<b>o</b>r <b>rese</b>rved <b>concur</b>rency).
- **"External system only allows known IPs"** → <b>p</b>ut <b>Gl</b>ue/<b>Lam</b>bda <b>i</b>n <b>a</b> VPC <b>beh</b>ind <b>a</b> **NAT gateway** <b>a</b>nd <b>allow</b>list <b>i</b>ts **Elastic IP**.
- **Glue job can't connect to RDS in a VPC** → <b>miss</b>ing **self-referencing security group rule** <b>o</b>r <b>rou</b>te.
- **DMS CDC from MySQL not capturing changes** → <b>ena</b>ble **binary logging with ROW format**.
- **DMS isn't a heavy ETL tool.** <b>La</b>nd <b>da</b>ta <b>i</b>n S3 <b>a</b>nd <b>trans</b>form <b>wi</b>th <b>Gl</b>ue.
- **"SaaS source like Salesforce, no code"** → **AppFlow**, <b>n</b>ot <b>a</b> <b>cus</b>tom <b>Lam</b>bda.
- **GZIP CSV files are not splittable** → <b>o</b>ne <b>ta</b>sk <b>p</b>er <b>fi</b>le; <b>conv</b>ert <b>t</b>o <b>Parq</b>uet <b>f</b>or <b>parall</b>elism.
- **"Only Glue jobs/crawlers in the pipeline"** → **Glue workflows**. **"Existing Airflow DAGs"** → **MWAA**. **"Mixed AWS services, serverless"** → **Step Functions**.
- **Step Functions Express workflows max out at 5 minutes.** <b>Lo</b>ng ETL <b>nee</b>ds **Standard**.
- **"Large volume of text to classify/summarize with an LLM, cost-sensitive"** → **Bedrock batch inference**, <b>n</b>ot <b>p</b>er-<b>rec</b>ord <b>o</b>n-<b>dem</b>and <b>cal</b>ls.
- **"Package and deploy Lambda + Step Functions + DynamoDB, test locally"** → **AWS SAM**.
- **"Shared, persistent file storage for Lambda"** → **EFS mount** (<b>Lam</b>bda <b>i</b>n <b>t</b>he VPC), <b>n</b>ot /<b>t</b>mp.

---

## Quick-recall summary

- <b>Dom</b>ain <b>wei</b>ght **34%**. <b>Fo</b>ur <b>tas</b>ks: <b>inges</b>tion (1.1), <b>transfo</b>rmation (1.2), <b>orchest</b>ration (1.3), <b>progra</b>mming (1.4).
- KDS <b>sha</b>rd: **1 MB/s or 1,000 rec/s in, 2 MB/s out**; <b>reten</b>tion <b>u</b>p <b>t</b>o **365 days**; <b>provis</b>ioned <b>v</b>s **on-demand**; **enhanced fan-out** = 2 MB/<b>s</b> <b>p</b>er <b>cons</b>umer.
- <b>H</b>ot <b>sha</b>rd = <b>b</b>ad <b>parti</b>tion <b>k</b>ey. <b>Ris</b>ing **IteratorAge** = <b>consu</b>mers <b>beh</b>ind.
- **Firehose**: <b>buff</b>ered <b>ne</b>ar <b>re</b>al <b>ti</b>me; <b>Parq</b>uet/ORC <b>conve</b>rsion; <b>Lam</b>bda <b>trans</b>form; <b>dyna</b>mic <b>partit</b>ioning; <b>Reds</b>hift <b>v</b>ia S3 + COPY; <b>Iceb</b>erg <b>destin</b>ation; **no replay**.
- **MSK** <b>f</b>or <b>Kaf</b>ka; **MSK Connect** <b>f</b>or <b>conne</b>ctors; **MSK Serverless** <b>f</b>or <b>n</b>o <b>siz</b>ing.
- **DynamoDB Streams** = 24 <b>h</b> CDC. **KDS for DynamoDB** = <b>lon</b>ger <b>reten</b>tion.
- <b>Bat</b>ch: **DMS** (DB, CDC), **AppFlow** (<b>Sa</b>aS), **DataSync** (<b>fi</b>le <b>sha</b>res), **Transfer Family** (SFTP), **Snow** (<b>offl</b>ine), **Data Exchange** (<b>thi</b>rd-<b>par</b>ty <b>da</b>ta), **zero-ETL** (DB → <b>Reds</b>hift).
- <b>Sched</b>ules: **EventBridge Scheduler**, <b>Gl</b>ue <b>trig</b>gers, <b>craw</b>ler <b>sched</b>ules, MWAA. <b>Eve</b>nts: **S3 Event Notifications** (<b>sim</b>ple) <b>v</b>s **EventBridge** (<b>filte</b>ring, <b>ma</b>ny <b>targ</b>ets, <b>rep</b>lay).
- <b>Lam</b>bda + <b>Kine</b>sis: <b>bat</b>ch <b>si</b>ze, <b>bat</b>ch <b>win</b>dow, **parallelization factor (≤10)**, <b>bis</b>ect <b>o</b>n <b>err</b>or, <b>m</b>ax <b>retr</b>ies/<b>a</b>ge, <b>o</b>n-<b>fail</b>ure <b>destin</b>ation, <b>tumb</b>ling <b>wind</b>ows.
- <b>Allow</b>list <b>outb</b>ound IPs <b>wi</b>th <b>a</b> **NAT gateway Elastic IP**.
- <b>Throt</b>tling: <b>back</b>off + <b>jit</b>ter, <b>bet</b>ter <b>ke</b>ys, <b>o</b>n-<b>dem</b>and <b>capa</b>city, <b>batc</b>hing, **RDS Proxy**, SQS <b>buffe</b>ring.
- <b>Rep</b>lay: **KDS/MSK retention, raw S3 zone, EventBridge archive, reset bookmarks**.
- <b>State</b>less = <b>p</b>er <b>rec</b>ord. <b>Stat</b>eful = <b>wind</b>ows/<b>ded</b>up/<b>joi</b>ns → **Flink**, <b>Gl</b>ue <b>strea</b>ming <b>checkp</b>oints, <b>Lam</b>bda <b>tumb</b>ling <b>wind</b>ows.
- <b>Trans</b>form <b>serv</b>ice <b>pic</b>ks: **Glue** (<b>serve</b>rless <b>Spa</b>rk), **DataBrew** (<b>n</b>o <b>co</b>de), **EMR** (<b>fu</b>ll <b>cont</b>rol, <b>Sp</b>ot <b>ta</b>sk <b>nod</b>es), **Lambda** (<b>sma</b>ll, ≤15 <b>m</b>in), **Athena CTAS** (SQL <b>o</b>n S3), **Redshift** (ELT), **Flink** (<b>stre</b>ams), **ECS/EKS/Batch** (<b>conta</b>iners).
- <b>Gl</b>ue: <b>Dynami</b>cFrame, **bookmarks**, **pushdown predicates**, <b>wor</b>ker <b>typ</b>es, <b>Au</b>to <b>Scal</b>ing, **Flex**, <b>Pyt</b>hon <b>she</b>ll.
- <b>Form</b>ats: **Parquet** = <b>defa</b>ult <b>analy</b>tics <b>ans</b>wer; <b>Av</b>ro = <b>strea</b>ming/<b>sch</b>ema <b>evolu</b>tion; GZIP <b>te</b>xt = <b>n</b>ot <b>split</b>table.
- <b>Troubl</b>eshoot: <b>sk</b>ew → <b>sa</b>lt/<b>broad</b>cast; <b>sma</b>ll <b>fil</b>es → <b>gro</b>up/<b>comp</b>act; <b>parti</b>tions <b>miss</b>ing → <b>Metas</b>tore <b>Consis</b>tency <b>Che</b>ck (MSCK) REPAIR / <b>proje</b>ction; COPY <b>err</b>ors → `STL_LOAD_ERRORS`.
- <b>Da</b>ta APIs: API <b>Gate</b>way + <b>Lam</b>bda + <b>Dyna</b>moDB / **Redshift Data API** / <b>Ath</b>ena; <b>AppS</b>ync <b>f</b>or <b>Grap</b>hQL.
- 3 <b>V</b>s: <b>vol</b>ume, <b>velo</b>city, <b>vari</b>ety (<b>struc</b>tured, <b>se</b>mi-<b>struc</b>tured, <b>unstru</b>ctured).
- LLMs: **Bedrock** <b>v</b>ia <b>Lam</b>bda/<b>Gl</b>ue/<b>St</b>ep <b>Funct</b>ions; **batch inference** <b>f</b>or <b>bu</b>lk; <b>Reds</b>hift ML <b>f</b>or SQL; <b>Compr</b>ehend <b>f</b>or <b>stan</b>dard NLP; <b>ma</b>sk PII <b>fir</b>st.
- <b>Orchest</b>ration: **Step Functions** (<b>Stan</b>dard ≤1 <b>y</b>r / <b>Expr</b>ess ≤5 <b>m</b>in, <b>Ret</b>ry/<b>Cat</b>ch, <b>Distri</b>buted <b>M</b>ap), **MWAA** (<b>Airf</b>low), **Glue workflows** (<b>Gl</b>ue <b>on</b>ly), **EventBridge** (<b>sta</b>rt).
- <b>Ale</b>rts: **SNS** <b>pu</b>sh; **SQS** <b>buf</b>fer + DLQ.
- <b>Lam</b>bda: <b>mem</b>ory 128 MB–10 GB (CPU <b>sca</b>les), **15 min**, /<b>t</b>mp <b>u</b>p <b>t</b>o 10 GB, **reserved** (<b>c</b>ap) <b>v</b>s **provisioned** (<b>n</b>o <b>co</b>ld <b>sta</b>rt) <b>concur</b>rency, **EFS** <b>f</b>or <b>sha</b>red <b>persi</b>stent <b>stor</b>age.
- <b>I</b>aC: **CloudFormation** (<b>templ</b>ates, <b>Stack</b>Sets), **CDK** (<b>co</b>de → <b>CloudFo</b>rmation), **SAM** (<b>serve</b>rless + <b>loc</b>al <b>test</b>ing).
- CI/CD: <b>CodePi</b>peline + <b>CodeB</b>uild + <b>I</b>aC <b>dep</b>loy, <b>tes</b>ts <b>a</b>nd <b>appr</b>oval <b>gat</b>es.
- <b>Distri</b>buted <b>compu</b>ting: <b>dri</b>ver/<b>execu</b>tors, <b>parti</b>tions, <b>shuf</b>fles, <b>la</b>zy <b>evalu</b>ation, <b>sk</b>ew.
- <b>Da</b>ta <b>struc</b>tures: <b>gra</b>phs (DAGs, <b>line</b>age, <b>Nept</b>une), <b>tre</b>es (<b>inde</b>xes, <b>nes</b>ted <b>da</b>ta), <b>ha</b>sh (<b>partit</b>ioning, <b>joi</b>ns).
