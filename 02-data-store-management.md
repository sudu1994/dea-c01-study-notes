# Domain 2: Data Store Management (26%)

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> **About 13 of the 50 scored questions.**
>
> <b>Th</b>is <b>dom</b>ain <b>tes</b>ts <b>whet</b>her <b>y</b>ou <b>c</b>an <b>pi</b>ck <b>t</b>he <b>rig</b>ht <b>sto</b>re <b>f</b>or <b>a</b> <b>co</b>st/<b>perfor</b>mance/<b>acc</b>ess-<b>patt</b>ern <b>requir</b>ement, <b>cata</b>log <b>t</b>he <b>da</b>ta <b>s</b>o <b>oth</b>ers <b>c</b>an <b>fi</b>nd <b>a</b>nd <b>que</b>ry <b>i</b>t, <b>man</b>age <b>i</b>ts <b>lifec</b>ycle (<b>lo</b>ad/<b>unl</b>oad, <b>tier</b>ing, <b>exp</b>iry, <b>dele</b>tion, <b>resil</b>iency), <b>a</b>nd <b>mod</b>el <b>i</b>t <b>we</b>ll (<b>sche</b>mas, <b>sch</b>ema <b>evolu</b>tion, [<b>line</b>age](00-data-basics-for-beginners.md#data-lineage), <b>partit</b>ioning, <b>vect</b>ors). <b>Exp</b>ect <b>lo</b>ts <b>o</b>f [<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift), [<b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice [S3]](00-data-basics-for-beginners.md#amazon-s3), [<b>Ath</b>ena](00-data-basics-for-beginners.md#amazon-athena), [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb), [<b>Gl</b>ue](00-data-basics-for-beginners.md#aws-glue) <b>Da</b>ta <b>Cata</b>log, <b>a</b>nd, <b>n</b>ew <b>i</b>n v1.1, **[Apache Iceberg](00-data-basics-for-beginners.md#apache-iceberg), vector indexes, and [SageMaker Catalog](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)**.

## Table of contents

- [<b>Ex</b>am <b>tas</b>ks <b>a</b>nd <b>ski</b>lls](#exam-tasks-and-skills)
- [<b>Ta</b>sk 2.1: <b>Cho</b>ose <b>a</b> <b>da</b>ta <b>sto</b>re](#task-21-choose-a-data-store)
- [<b>Ta</b>sk 2.2: <b>Under</b>stand <b>da</b>ta <b>catal</b>oging <b>syst</b>ems](#task-22-understand-data-cataloging-systems)
- [<b>Ta</b>sk 2.3: <b>Man</b>age <b>t</b>he <b>lifec</b>ycle <b>o</b>f <b>da</b>ta](#task-23-manage-the-lifecycle-of-data)
- [<b>Ta</b>sk 2.4: <b>Des</b>ign <b>da</b>ta <b>mod</b>els <b>a</b>nd <b>sch</b>ema <b>evolu</b>tion](#task-24-design-data-models-and-schema-evolution)
- [<b>Gotc</b>has <b>a</b>nd <b>ex</b>am <b>tra</b>ps](#gotchas-and-exam-traps)
- [<b>Qui</b>ck-<b>rec</b>all <b>summ</b>ary](#quick-recall-summary)

## Exam tasks and skills

> <b>Summa</b>rized <b>fr</b>om <b>t</b>he <b>offi</b>cial AWS <b>Certi</b>fied <b>Da</b>ta <b>Engi</b>neer – <b>Assoc</b>iate (DEA-C01) <b>ex</b>am <b>gui</b>de (v1.1). <b>Exa</b>ct <b>word</b>ing: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain2.html

### Task 2.1: Choose a data store
- **2.1.1** <b>Pi</b>ck <b>stor</b>age <b>serv</b>ices <b>th</b>at <b>me</b>et <b>co</b>st <b>a</b>nd <b>perfor</b>mance <b>nee</b>ds (<b>Reds</b>hift, [<b>Elas</b>tic <b>MapRe</b>duce [EMR]](00-data-basics-for-beginners.md#amazon-emr), [<b>La</b>ke <b>Forma</b>tion](00-data-basics-for-beginners.md#aws-lake-formation), [<b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice [RDS]](00-data-basics-for-beginners.md#amazon-rds), <b>Dyna</b>moDB, [<b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams [KDS]](00-data-basics-for-beginners.md#amazon-kinesis-data-streams), [<b>Mana</b>ged <b>Strea</b>ming <b>f</b>or <b>Apa</b>che <b>Kaf</b>ka [MSK]](00-data-basics-for-beginners.md#amazon-msk)).
- **2.1.2** <b>Confi</b>gure <b>stor</b>age <b>f</b>or <b>spec</b>ific <b>acc</b>ess <b>patt</b>erns.
- **2.1.3** <b>Mat</b>ch <b>stor</b>age <b>t</b>o <b>u</b>se <b>cas</b>es (<b>e</b>.g., **Hierarchical Navigable Small World [HNSW] indexes on [Aurora](00-data-basics-for-beginners.md#amazon-aurora) [PostgreSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server)**, **[MemoryDB](00-data-basics-for-beginners.md#amazon-memorydb-and-elasticache)** <b>f</b>or <b>fa</b>st <b>k</b>ey/<b>val</b>ue).
- **2.1.4** <b>Integ</b>rate <b>migra</b>tion <b>too</b>ls (<b>e</b>.g., [<b>Tran</b>sfer <b>Fam</b>ily](00-data-basics-for-beginners.md#aws-transfer-family)).
- **2.1.5** <b>U</b>se <b>migra</b>tion/<b>rem</b>ote-<b>acc</b>ess <b>meth</b>ods (<b>Reds</b>hift <b>feder</b>ated <b>quer</b>ies, <b>materi</b>alized <b>vie</b>ws, <b>Spec</b>trum).
- **2.1.6** <b>Man</b>age <b>loc</b>ks (<b>Reds</b>hift, RDS).
- **2.1.7** 🆕 <b>Man</b>age <b>op</b>en <b>tab</b>le <b>form</b>ats (<b>Apa</b>che <b>Iceb</b>erg).
- **2.1.8** 🆕 <b>Desc</b>ribe <b>vec</b>tor <b>ind</b>ex <b>typ</b>es (HNSW, <b>Inve</b>rted <b>Fi</b>le <b>ind</b>ex [IVF]).

### Task 2.2: Understand data cataloging systems
- **2.2.1** <b>U</b>se <b>cata</b>logs <b>t</b>o <b>cons</b>ume <b>da</b>ta <b>fr</b>om <b>i</b>ts <b>sou</b>rce.
- **2.2.2** <b>Bui</b>ld <b>a</b>nd <b>refer</b>ence <b>a</b> <b>techn</b>ical <b>cata</b>log (<b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log, [<b>Hi</b>ve](00-data-basics-for-beginners.md#apache-hive) <b>metas</b>tore).
- **2.2.3** <b>Disc</b>over <b>sche</b>mas <b>wi</b>th <b>Gl</b>ue <b>craw</b>lers.
- **2.2.4** <b>Ke</b>ep <b>parti</b>tions <b>i</b>n <b>sy</b>nc <b>wi</b>th <b>t</b>he <b>cata</b>log.
- **2.2.5** <b>Cre</b>ate <b>sou</b>rce/<b>tar</b>get <b>connec</b>tions <b>f</b>or <b>catal</b>oging.
- **2.2.6** 🆕 <b>Cre</b>ate <b>a</b>nd <b>man</b>age <b>busi</b>ness <b>da</b>ta <b>cata</b>logs (<b>SageM</b>aker <b>Cata</b>log).

### Task 2.3: Manage the lifecycle of data
- **2.3.1** <b>Lo</b>ad <b>a</b>nd <b>unl</b>oad <b>betw</b>een S3 <b>a</b>nd <b>Reds</b>hift.
- **2.3.2** <b>U</b>se S3 <b>Lifec</b>ycle <b>t</b>o <b>cha</b>nge <b>stor</b>age <b>tie</b>rs.
- **2.3.3** <b>U</b>se S3 <b>Lifec</b>ycle <b>t</b>o <b>exp</b>ire <b>da</b>ta <b>b</b>y <b>a</b>ge.
- **2.3.4** <b>Man</b>age S3 <b>versi</b>oning <b>a</b>nd <b>Dyna</b>moDB <b>Ti</b>me <b>T</b>o <b>Li</b>ve (TTL).
- **2.3.5** <b>Del</b>ete <b>da</b>ta <b>f</b>or <b>busi</b>ness <b>a</b>nd <b>leg</b>al <b>requir</b>ements.
- **2.3.6** <b>Prot</b>ect <b>da</b>ta <b>wi</b>th <b>approp</b>riate <b>resil</b>iency <b>a</b>nd <b>availa</b>bility.

### Task 2.4: Design data models and schema evolution
- **2.4.1** <b>Des</b>ign <b>sche</b>mas <b>f</b>or <b>Reds</b>hift, <b>Dyna</b>moDB, <b>La</b>ke <b>Forma</b>tion.
- **2.4.2** <b>Han</b>dle <b>chan</b>ges <b>i</b>n <b>da</b>ta <b>characte</b>ristics.
- **2.4.3** <b>Conv</b>ert <b>sche</b>mas (<b>Ama</b>zon <b>W</b>eb <b>Serv</b>ices [AWS] <b>Sch</b>ema <b>Conve</b>rsion <b>To</b>ol [SCT], [<b>Data</b>base <b>Migra</b>tion <b>Serv</b>ice [DMS]](00-data-basics-for-beginners.md#aws-dms) <b>Sch</b>ema <b>Conve</b>rsion).
- **2.4.4** <b>Estab</b>lish <b>line</b>age (<b>SageM</b>aker <b>Mach</b>ine <b>Lear</b>ning [ML] <b>Line</b>age <b>Trac</b>king, <b>SageM</b>aker <b>Cata</b>log).
- **2.4.5** <b>App</b>ly <b>inde</b>xing, <b>partit</b>ioning, <b>compre</b>ssion, <b>a</b>nd <b>oth</b>er <b>optimiz</b>ations.
- **2.4.6** 🆕 <b>Desc</b>ribe <b>vectori</b>zation (<b>e</b>.g., [<b>Bedr</b>ock](00-data-basics-for-beginners.md#amazon-bedrock) <b>Knowl</b>edge <b>Bas</b>es).

---

## Task 2.1: Choose a data store

### Core concepts

<b>Eve</b>ry <b>sto</b>re <b>ques</b>tion <b>i</b>s <b>answ</b>ered <b>b</b>y <b>fo</b>ur <b>quest</b>ions:
1. **Access pattern:** <b>k</b>ey <b>look</b>ups? <b>sca</b>ns/<b>aggreg</b>ations? <b>fu</b>ll-<b>te</b>xt? <b>simil</b>arity <b>sea</b>rch? <b>gra</b>ph <b>trave</b>rsal?
2. **Latency:** <b>micros</b>econds, <b>millis</b>econds, <b>seco</b>nds, <b>minu</b>tes?
3. **Structure:** <b>relat</b>ional, <b>se</b>mi-<b>struc</b>tured, <b>unstru</b>ctured, <b>vect</b>ors?
4. **Cost model:** <b>p</b>ay <b>p</b>er <b>que</b>ry, <b>p</b>er <b>ho</b>ur, <b>p</b>er GB <b>sto</b>red, <b>p</b>er <b>requ</b>est?

### Data store decision table (skills 2.1.1, 2.1.2, 2.1.3)

| <b>Requir</b>ement | <b>Sto</b>re | <b>W</b>hy |
|---|---|---|
| <b>Che</b>ap, <b>dura</b>ble <b>stor</b>age <b>f</b>or <b>a</b>ny <b>for</b>mat; [<b>da</b>ta <b>la</b>ke](00-data-basics-for-beginners.md#data-lake) | **Amazon S3** | 11 <b>nin</b>es <b>durab</b>ility, <b>stor</b>age <b>clas</b>ses, <b>decou</b>pled <b>fr</b>om <b>comp</b>ute |
| <b>La</b>ke <b>tab</b>les <b>wi</b>th <b>Atomi</b>city, <b>Consis</b>tency, <b>Isola</b>tion, <b>Durab</b>ility (ACID), <b>upda</b>tes/<b>dele</b>tes, <b>ti</b>me <b>tra</b>vel | **Apache Iceberg** <b>o</b>n S3 / **[Amazon S3 Tables](00-data-basics-for-beginners.md#amazon-s3-tables)** | <b>Op</b>en <b>tab</b>le <b>for</b>mat; S3 <b>Tab</b>les <b>ad</b>ds <b>autom</b>atic <b>mainte</b>nance |
| PB-<b>sca</b>le [<b>Struc</b>tured <b>Que</b>ry <b>Lang</b>uage [SQL]](00-data-basics-for-beginners.md#sql) <b>analy</b>tics, <b>Busi</b>ness <b>Intell</b>igence (BI) <b>dashb</b>oards, <b>comp</b>lex <b>joi</b>ns | **Amazon Redshift** | <b>Colu</b>mnar <b>Massi</b>vely <b>Para</b>llel <b>Proce</b>ssing (MPP) <b>wareh</b>ouse |
| <b>A</b>d-<b>h</b>oc SQL <b>o</b>n S3, <b>infre</b>quent <b>quer</b>ies, <b>n</b>o <b>infrast</b>ructure | **Amazon Athena** | <b>Serve</b>rless, <b>p</b>ay <b>p</b>er TB <b>scan</b>ned |
| <b>Sin</b>gle-<b>dig</b>it <b>m</b>s <b>k</b>ey/<b>val</b>ue <b>o</b>r <b>docu</b>ment <b>a</b>t <b>a</b>ny <b>sca</b>le | **Amazon DynamoDB** | <b>Serve</b>rless <b>NoS</b>QL, <b>predic</b>table <b>late</b>ncy |
| **Microsecond** <b>rea</b>ds <b>i</b>n <b>fro</b>nt <b>o</b>f <b>Dyna</b>moDB | **DynamoDB Accelerator (DAX)** | <b>Wri</b>te-<b>thro</b>ugh <b>i</b>n-<b>mem</b>ory <b>cac</b>he <b>f</b>or <b>Dyna</b>moDB |
| **Durable** <b>i</b>n-<b>mem</b>ory <b>k</b>ey/<b>val</b>ue <b>a</b>s <b>a</b> <b>prim</b>ary <b>data</b>base | **Amazon MemoryDB** | [<b>Red</b>is](00-data-basics-for-beginners.md#redis-and-valkey)/<b>Val</b>key [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>face [API]](00-data-basics-for-beginners.md#api) + <b>Mul</b>ti-AZ <b>transa</b>ction <b>l</b>og (<b>da</b>ta <b>surv</b>ives <b>no</b>de <b>fail</b>ure) |
| <b>I</b>n-<b>mem</b>ory <b>cac</b>he (<b>da</b>ta <b>c</b>an <b>b</b>e <b>rebu</b>ilt) | **Amazon ElastiCache** | <b>Low</b>er <b>co</b>st <b>cac</b>he, <b>n</b>ot <b>a</b> <b>dura</b>ble <b>sys</b>tem <b>o</b>f <b>rec</b>ord |
| <b>Relat</b>ional <b>Onl</b>ine <b>Transa</b>ction <b>Proce</b>ssing (OLTP) <b>wi</b>th <b>transa</b>ctions | **Amazon RDS / Aurora** | ACID, <b>joi</b>ns, <b>constr</b>aints |
| <b>Vec</b>tor <b>simil</b>arity <b>sea</b>rch <b>ne</b>xt <b>t</b>o <b>relat</b>ional <b>da</b>ta | **Aurora PostgreSQL + pgvector** (HNSW / <b>IVFF</b>lat) | <b>Ke</b>ep [<b>embed</b>dings](00-data-basics-for-beginners.md#vectors-and-embeddings) <b>wi</b>th <b>busi</b>ness <b>da</b>ta, <b>u</b>se SQL |
| <b>Fu</b>ll-<b>te</b>xt <b>sea</b>rch, <b>l</b>og <b>analy</b>tics, <b>vec</b>tor <b>sea</b>rch <b>a</b>t <b>sca</b>le | **[Amazon OpenSearch Service](00-data-basics-for-beginners.md#amazon-opensearch-service) / Serverless** | <b>Inve</b>rted <b>ind</b>ex + <b>k</b>-<b>Near</b>est <b>Neigh</b>bors (<b>k</b>-NN) <b>eng</b>ine |
| <b>Hig</b>hly <b>conne</b>cted <b>da</b>ta (<b>fra</b>ud <b>rin</b>gs, <b>recommen</b>dations) | **[Amazon Neptune](00-data-basics-for-beginners.md#amazon-neptune)** | <b>Gra</b>ph <b>data</b>base [DB] (<b>Grem</b>lin, <b>openC</b>ypher, SPARQL) |
| <b>B</b>ig <b>da</b>ta <b>proce</b>ssing <b>wi</b>th [HDFS](00-data-basics-for-beginners.md#hdfs)/<b>HBa</b>se | **Amazon EMR** | [<b>Had</b>oop](00-data-basics-for-beginners.md#apache-hadoop) <b>ecosy</b>stem <b>stor</b>age <b>a</b>nd <b>comp</b>ute |
| <b>Da</b>ta <b>reta</b>ined <b>a</b>s <b>a</b> <b>str</b>eam (<b>hou</b>rs <b>t</b>o <b>a</b> <b>ye</b>ar) | **Kinesis Data Streams / MSK** | <b>Stre</b>ams <b>a</b>re <b>stor</b>age <b>t</b>oo: <b>orde</b>red, <b>repla</b>yable |
| <b>Gove</b>rned <b>da</b>ta <b>la</b>ke <b>permis</b>sions | **AWS Lake Formation** (<b>ov</b>er S3 + <b>Gl</b>ue <b>Cata</b>log) | <b>Fi</b>ne-<b>grai</b>ned <b>acc</b>ess, <b>n</b>ot <b>a</b> <b>stor</b>age <b>eng</b>ine <b>its</b>elf |

### Amazon S3 essentials

**Storage classes:**

| <b>Cla</b>ss | <b>Acc</b>ess | <b>M</b>in <b>dura</b>tion | <b>U</b>se |
|---|---|---|---|
| **Standard** | <b>m</b>s | — | <b>H</b>ot <b>da</b>ta |
| **Intelligent-Tiering** | <b>m</b>s (<b>arch</b>ive <b>tie</b>rs <b>opti</b>onal) | — | **Unknown or changing access patterns**; <b>au</b>to-<b>mov</b>es <b>obje</b>cts, <b>sma</b>ll <b>monit</b>oring <b>f</b>ee |
| **Standard-Infrequent Access (Standard-IA)** | <b>m</b>s | 30 <b>da</b>ys | <b>Infre</b>quent <b>acc</b>ess, <b>mul</b>ti-AZ |
| **One Zone-Infrequent Access (One Zone-IA)** | <b>m</b>s | 30 <b>da</b>ys | <b>R</b>e-<b>creat</b>able <b>infre</b>quent <b>da</b>ta, <b>o</b>ne <b>Availa</b>bility <b>Zo</b>ne (AZ) |
| **Glacier Instant Retrieval** | <b>m</b>s | 90 <b>da</b>ys | <b>Arch</b>ive <b>acce</b>ssed <b>abo</b>ut <b>on</b>ce <b>a</b> <b>quar</b>ter |
| **Glacier Flexible Retrieval** | <b>minu</b>tes–<b>hou</b>rs (<b>exped</b>ited 1–5 <b>m</b>in, <b>stan</b>dard 3–5 <b>h</b>, <b>bu</b>lk 5–12 <b>h</b>) | 90 <b>da</b>ys | <b>Back</b>ups, <b>arch</b>ives |
| **Glacier Deep Archive** | 12–48 <b>h</b> | 180 <b>da</b>ys | <b>Compl</b>iance <b>arch</b>ives, <b>chea</b>pest |
| **Express One Zone** | <b>sin</b>gle-<b>dig</b>it <b>m</b>s | — | <b>Ve</b>ry <b>hi</b>gh <b>requ</b>est <b>rat</b>es, <b>late</b>ncy-<b>sensi</b>tive <b>analy</b>tics/ML <b>i</b>n <b>o</b>ne AZ |

**Performance:** 3,500 <b>wri</b>te <b>a</b>nd 5,500 <b>re</b>ad <b>requ</b>ests <b>p</b>er <b>sec</b>ond **per prefix**. <b>Spr</b>ead <b>h</b>ot <b>da</b>ta <b>acr</b>oss <b>pref</b>ixes, <b>u</b>se <b>multi</b>part <b>upl</b>oad <b>f</b>or <b>lar</b>ge <b>obje</b>cts, <b>a</b>nd <b>by</b>te-<b>ran</b>ge <b>fetc</b>hes <b>f</b>or <b>para</b>llel <b>rea</b>ds.

### Amazon Redshift essentials

**Architecture:** <b>lea</b>der <b>no</b>de (<b>par</b>ses, <b>pla</b>ns, <b>aggre</b>gates) + <b>comp</b>ute <b>nod</b>es, <b>ea</b>ch <b>spl</b>it <b>in</b>to **slices** <b>th</b>at <b>wo</b>rk <b>i</b>n <b>para</b>llel. **RA3** <b>nod</b>es <b>sepa</b>rate <b>comp</b>ute <b>fr</b>om **Redshift Managed Storage** (S3-<b>bac</b>ked). **Redshift Serverless** <b>bil</b>ls <b>b</b>y <b>Reds</b>hift <b>Proce</b>ssing <b>Un</b>it <b>hou</b>rs (RPU-<b>hou</b>rs) <b>wi</b>th <b>n</b>o <b>clus</b>ters <b>t</b>o <b>man</b>age. <b>U</b>se <b>i</b>t <b>f</b>or <b>unpredi</b>ctable <b>o</b>r <b>interm</b>ittent <b>workl</b>oads.

**Distribution styles:**

| <b>Sty</b>le | <b>H</b>ow <b>ro</b>ws <b>a</b>re <b>pla</b>ced | <b>U</b>se <b>wh</b>en |
|---|---|---|
| **AUTO** | <b>Reds</b>hift <b>choo</b>ses <b>a</b>nd <b>adju</b>sts | <b>Defa</b>ult, <b>uns</b>ure |
| **KEY** | <b>Sa</b>me <b>k</b>ey <b>val</b>ue → <b>sa</b>me <b>sli</b>ce | <b>Lar</b>ge <b>fa</b>ct <b>tab</b>les <b>joi</b>ned <b>o</b>n <b>th</b>at <b>col</b>umn (<b>e</b>.g., `customer_id`). **Co-located joins** <b>avo</b>id <b>da</b>ta <b>move</b>ment. <b>Wat</b>ch <b>f</b>or **skew** <b>i</b>f <b>t</b>he <b>k</b>ey <b>h</b>as <b>f</b>ew <b>dist</b>inct <b>val</b>ues. |
| **ALL** | <b>Fu</b>ll <b>co</b>py <b>o</b>n <b>eve</b>ry <b>no</b>de | <b>Sma</b>ll, <b>rar</b>ely <b>upda</b>ted <b>dimen</b>sion <b>tab</b>les |
| **EVEN** | <b>Rou</b>nd-<b>rob</b>in | <b>N</b>o <b>domi</b>nant <b>jo</b>in; <b>tab</b>les <b>n</b>ot <b>joi</b>ned |

**Sort keys:**
- **Compound** (<b>defa</b>ult): <b>orde</b>red <b>b</b>y <b>col</b>umn 1, <b>th</b>en 2… <b>Be</b>st <b>wh</b>en <b>quer</b>ies <b>fil</b>ter <b>o</b>n <b>t</b>he **leading column** (<b>usua</b>lly <b>a</b> <b>da</b>te/<b>times</b>tamp) <b>a</b>nd <b>f</b>or <b>ran</b>ge <b>filt</b>ers, <b>mer</b>ge <b>joi</b>ns, `GROUP BY`/`ORDER BY`.
- **Interleaved**: <b>equ</b>al <b>wei</b>ght <b>t</b>o <b>ea</b>ch <b>col</b>umn; <b>hel</b>ps <b>wh</b>en <b>diffe</b>rent <b>quer</b>ies <b>fil</b>ter <b>o</b>n <b>diffe</b>rent <b>colu</b>mns. <b>Expen</b>sive `VACUUM REINDEX`, <b>s</b>o <b>rar</b>ely <b>t</b>he <b>be</b>st <b>ans</b>wer.
- <b>So</b>rt <b>ke</b>ys <b>ena</b>ble **zone maps** (<b>m</b>in/<b>m</b>ax <b>p</b>er <b>blo</b>ck), <b>s</b>o <b>Reds</b>hift <b>ski</b>ps <b>blo</b>cks <b>th</b>at <b>can</b>'t <b>mat</b>ch.

**Compression (column encoding):** `AZ64` (<b>numb</b>ers/<b>dat</b>es), `ZSTD` (<b>stri</b>ngs), `LZO`; `ENCODE AUTO` <b>le</b>ts <b>Reds</b>hift <b>cho</b>ose. <b>Don</b>'t <b>comp</b>ress <b>t</b>he <b>fir</b>st <b>so</b>rt <b>k</b>ey <b>col</b>umn <b>heav</b>ily (<b>i</b>t <b>hur</b>ts <b>ran</b>ge-<b>restr</b>icted <b>sca</b>ns).

**Scaling and workload features:**

| <b>Feat</b>ure | <b>Wh</b>at <b>i</b>t <b>sol</b>ves |
|---|---|
| **Concurrency scaling** | <b>Bur</b>sts <b>o</b>f <b>ma</b>ny <b>concu</b>rrent <b>quer</b>ies → <b>trans</b>ient <b>ext</b>ra <b>clus</b>ters |
| **Elastic resize** | <b>Cha</b>nge <b>no</b>de <b>cou</b>nt <b>i</b>n <b>minu</b>tes |
| **Workload Management [WLM] (automatic)** | <b>Que</b>ry <b>que</b>ues, <b>prior</b>ities, **Short Query Acceleration** |
| **Materialized views** | <b>Preco</b>mpute <b>expen</b>sive <b>joi</b>ns/<b>aggreg</b>ations; <b>increm</b>ental <b>a</b>nd <b>au</b>to <b>refr</b>esh |
| **Data sharing** | <b>Li</b>ve <b>re</b>ad (<b>a</b>nd <b>wri</b>te) <b>acc</b>ess <b>acr</b>oss <b>clus</b>ters/<b>workg</b>roups/<b>acco</b>unts/<b>Regi</b>ons **with no copies** |
| **Redshift Spectrum** | <b>Que</b>ry S3 (<b>Gl</b>ue <b>Cata</b>log <b>exte</b>rnal <b>tab</b>les) <b>fr</b>om <b>Reds</b>hift |
| **Federated query** | <b>Que</b>ry <b>li</b>ve RDS/<b>Aur</b>ora <b>Postg</b>reSQL & <b>MyS</b>QL |
| **[Zero-ETL](00-data-basics-for-beginners.md#zero-etl-integrations)** | <b>Ne</b>ar-<b>re</b>al-<b>ti</b>me <b>replic</b>ation <b>fr</b>om <b>Aur</b>ora/RDS/<b>Dyna</b>moDB |
| **SUPER type + PartiQL** | <b>Sto</b>re <b>a</b>nd <b>que</b>ry <b>se</b>mi-<b>struc</b>tured [<b>JavaS</b>cript <b>Obj</b>ect <b>Nota</b>tion [JSON]](00-data-basics-for-beginners.md#json) |

### Amazon DynamoDB essentials

- **Primary key:** <b>parti</b>tion <b>k</b>ey <b>on</b>ly, <b>o</b>r <b>parti</b>tion <b>k</b>ey + <b>so</b>rt <b>k</b>ey. <b>Cho</b>ose <b>a</b> **high-cardinality** <b>parti</b>tion <b>k</b>ey <b>wi</b>th <b>eve</b>nly <b>spr</b>ead <b>traf</b>fic.
- **Indexes:** **Global Secondary Index [GSI]** (<b>diffe</b>rent <b>parti</b>tion/<b>so</b>rt <b>k</b>ey, <b>a</b>dd <b>anyt</b>ime, <b>event</b>ually <b>consi</b>stent, <b>o</b>wn <b>capa</b>city) <b>v</b>s **Local Secondary Index [LSI]** (<b>sa</b>me <b>parti</b>tion <b>k</b>ey, <b>diffe</b>rent <b>so</b>rt <b>k</b>ey, **only at table creation**, <b>supp</b>orts <b>stro</b>ngly <b>consi</b>stent <b>rea</b>ds, 10 GB <b>p</b>er <b>parti</b>tion <b>k</b>ey <b>val</b>ue <b>lim</b>it).
- **Capacity:** **on-demand** (<b>spi</b>ky/<b>unkn</b>own <b>traf</b>fic) <b>v</b>s **provisioned + auto scaling** (<b>ste</b>ady <b>traf</b>fic, <b>chea</b>per). <b>Re</b>ad <b>Capa</b>city <b>Un</b>it (RCU) = 1 <b>stro</b>ngly <b>consi</b>stent <b>re</b>ad/<b>s</b> <b>o</b>f <b>u</b>p <b>t</b>o 4 KB (<b>o</b>r 2 <b>event</b>ually <b>consi</b>stent); <b>Wri</b>te <b>Capa</b>city <b>Un</b>it (WCU) = 1 <b>wri</b>te/<b>s</b> <b>o</b>f <b>u</b>p <b>t</b>o 1 KB.
- **Item limit:** 400 KB. <b>Sto</b>re <b>lar</b>ger <b>payl</b>oads <b>i</b>n S3 <b>a</b>nd <b>ke</b>ep <b>a</b> <b>poin</b>ter.
- **Streams, TTL, Point-In-Time Recovery (PITR), global tables, export to S3, zero-ETL** <b>a</b>re <b>cove</b>red <b>und</b>er <b>lifec</b>ycle <b>a</b>nd <b>inges</b>tion.

### Migration tools (skill 2.1.4)

| <b>To</b>ol | <b>Mov</b>es |
|---|---|
| **AWS Transfer Family** | <b>Fil</b>es <b>v</b>ia **SFTP/File Transfer Protocol Secure (FTPS)/File Transfer Protocol (FTP)/Applicability Statement 2 (AS2)** <b>in</b>to S3/<b>Elas</b>tic <b>Fi</b>le <b>Sys</b>tem (EFS). <b>Part</b>ners <b>ke</b>ep <b>usi</b>ng <b>the</b>ir <b>exis</b>ting SSH <b>Fi</b>le <b>Tran</b>sfer <b>Prot</b>ocol (SFTP) <b>clie</b>nts; <b>mana</b>ged <b>workf</b>lows <b>c</b>an <b>po</b>st-<b>proc</b>ess <b>fil</b>es. |
| **[AWS DataSync](00-data-basics-for-beginners.md#aws-datasync)** | <b>Lar</b>ge <b>onl</b>ine <b>fi</b>le <b>trans</b>fers (<b>Netw</b>ork <b>Fi</b>le <b>Sys</b>tem [NFS]/<b>Ser</b>ver <b>Mess</b>age <b>Blo</b>ck [SMB]/HDFS/<b>obj</b>ect) <b>wi</b>th <b>sched</b>uling <b>a</b>nd <b>verifi</b>cation |
| **[AWS Snow Family](00-data-basics-for-beginners.md#aws-snow-family)** | <b>Offl</b>ine <b>bu</b>lk <b>tran</b>sfer |
| **AWS DMS** | <b>Datab</b>ases (<b>homoge</b>neous <b>a</b>nd <b>heterog</b>eneous), <b>fu</b>ll <b>lo</b>ad + <b>Cha</b>nge <b>Da</b>ta <b>Capt</b>ure (CDC) |
| **S3 Batch Operations** | <b>Bu</b>lk <b>acti</b>ons <b>o</b>n <b>bill</b>ions <b>o</b>f <b>exis</b>ting <b>obje</b>cts (<b>co</b>py, <b>t</b>ag, <b>rest</b>ore, <b>inv</b>oke [<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda)) |

### Remote access instead of copying (skill 2.1.5)

| <b>Met</b>hod | <b>Wh</b>at <b>i</b>t <b>do</b>es | <b>Wh</b>en |
|---|---|---|
| **Redshift Spectrum** | <b>Exte</b>rnal <b>tab</b>les <b>ov</b>er S3 <b>v</b>ia <b>Gl</b>ue <b>Cata</b>log; <b>Spec</b>trum <b>lay</b>er <b>sca</b>ns S3 <b>i</b>n <b>para</b>llel | <b>Jo</b>in <b>wareh</b>ouse <b>da</b>ta <b>wi</b>th **cold/large lake data** <b>with</b>out <b>load</b>ing <b>i</b>t |
| **Redshift federated query** | <b>Pus</b>hes <b>quer</b>ies <b>do</b>wn <b>t</b>o **live** <b>Aur</b>ora/RDS <b>Postg</b>reSQL <b>o</b>r <b>MyS</b>QL | <b>Jo</b>in <b>operat</b>ional <b>da</b>ta <b>wi</b>th <b>wareh</b>ouse <b>da</b>ta <b>with</b>out <b>Extr</b>act, <b>Trans</b>form, <b>Lo</b>ad (ETL) |
| **Redshift materialized views** | <b>Sto</b>re <b>t</b>he <b>res</b>ult <b>o</b>f <b>a</b> <b>que</b>ry (<b>c</b>an <b>incl</b>ude <b>Spec</b>trum/<b>feder</b>ated <b>sour</b>ces) | <b>Spe</b>ed <b>u</b>p <b>repe</b>ated <b>expen</b>sive <b>quer</b>ies; <b>refr</b>esh <b>o</b>n <b>sche</b>dule <b>o</b>r <b>automat</b>ically |
| **Athena federated query** | <b>Lam</b>bda <b>conne</b>ctors <b>t</b>o <b>Dyna</b>moDB, RDS, [<b>Cloud</b>Watch](00-data-basics-for-beginners.md#amazon-cloudwatch), <b>oth</b>ers | SQL <b>acr</b>oss <b>ma</b>ny <b>sour</b>ces <b>fr</b>om <b>Ath</b>ena |

### Managing locks (skill 2.1.6)

**Redshift lock types:**

| <b>Lo</b>ck | <b>Tak</b>en <b>b</b>y | <b>Blo</b>cks |
|---|---|---|
| **AccessShareLock** | `SELECT` | <b>On</b>ly <b>AccessExcl</b>usiveLock |
| **ShareRowExclusiveLock** | `INSERT`, `UPDATE`, `DELETE`, `COPY` | <b>Oth</b>er <b>wri</b>tes <b>o</b>n <b>t</b>he <b>sa</b>me <b>tab</b>le (<b>a</b>nd <b>exclu</b>sive <b>loc</b>ks) |
| **AccessExclusiveLock** | <b>Da</b>ta <b>Defin</b>ition <b>Lang</b>uage (DDL): `ALTER TABLE`, `DROP`, `TRUNCATE`, <b>so</b>me `VACUUM` | **Everything**, <b>inclu</b>ding <b>rea</b>ds |

- <b>Fi</b>nd <b>bloc</b>kers: `STV_LOCKS`, `SVV_TRANSACTIONS`, `STV_RECENTS`; <b>e</b>nd <b>t</b>he <b>sess</b>ion <b>wi</b>th `PG_TERMINATE_BACKEND(pid)`.
- <b>U</b>se <b>t</b>he <b>expl</b>icit `LOCK table_name;` <b>comm</b>and <b>t</b>o <b>seria</b>lize <b>concu</b>rrent <b>writ</b>ers (<b>avo</b>ids <b>serial</b>izable <b>isola</b>tion <b>err</b>ors).
- <b>Lo</b>ng-<b>runn</b>ing <b>op</b>en <b>transa</b>ctions <b>ho</b>ld <b>loc</b>ks. <b>Com</b>mit <b>prom</b>ptly, <b>a</b>nd <b>sche</b>dule DDL <b>outs</b>ide <b>bu</b>sy <b>wind</b>ows.

**RDS / Aurora:**
- <b>R</b>ow-<b>lev</b>el <b>lock</b>ing <b>i</b>n <b>Inn</b>oDB/<b>Postg</b>reSQL; `SELECT … FOR UPDATE` <b>loc</b>ks <b>ro</b>ws <b>f</b>or <b>a</b> <b>transa</b>ction.
- **Deadlocks**: <b>t</b>he <b>eng</b>ine <b>kil</b>ls <b>o</b>ne <b>transa</b>ction. <b>F</b>ix <b>wi</b>th <b>consi</b>stent <b>lo</b>ck <b>orde</b>ring <b>a</b>nd <b>shor</b>ter <b>transa</b>ctions.
- <b>Insp</b>ect <b>wi</b>th `pg_locks` / `pg_stat_activity` (<b>Postg</b>reSQL) <b>o</b>r `SHOW ENGINE INNODB STATUS` / `performance_schema` (<b>MyS</b>QL). **Performance Insights** <b>sho</b>ws <b>lo</b>ck <b>wai</b>ts <b>visu</b>ally.

### 🆕 Open table formats: Apache Iceberg (skill 2.1.7)

**Why table formats exist:** <b>pla</b>in [<b>Parq</b>uet](00-data-basics-for-beginners.md#parquet) <b>fil</b>es <b>i</b>n S3 <b>ha</b>ve <b>n</b>o <b>transa</b>ctions. <b>T</b>wo <b>writ</b>ers <b>c</b>an <b>corr</b>upt <b>a</b> <b>tab</b>le, <b>read</b>ers <b>c</b>an <b>s</b>ee <b>ha</b>lf-<b>writ</b>ten <b>da</b>ta, <b>a</b>nd <b>upda</b>ting/<b>dele</b>ting <b>a</b> <b>r</b>ow <b>mea</b>ns <b>rewri</b>ting <b>parti</b>tions. <b>Op</b>en <b>tab</b>le <b>form</b>ats <b>a</b>dd <b>a</b> **metadata layer** <b>ov</b>er <b>fil</b>es <b>t</b>o <b>gi</b>ve <b>data</b>base-<b>li</b>ke <b>beha</b>vior.

**How Iceberg works:**

```
Catalog (Glue Data Catalog / S3 Tables) ──► current metadata.json
                                               └─► snapshot → manifest list
                                                              └─► manifest files
                                                                      └─► data files (Parquet) + delete files
```

<b>Ea</b>ch <b>com</b>mit <b>crea</b>tes <b>a</b> **new snapshot** <b>atomi</b>cally, <b>s</b>o <b>read</b>ers <b>alw</b>ays <b>s</b>ee <b>a</b> <b>consi</b>stent <b>vers</b>ion.

**Key features (memorize):**

| <b>Feat</b>ure | <b>Mean</b>ing |
|---|---|
| **ACID transactions** | <b>Concu</b>rrent <b>read</b>ers/<b>writ</b>ers <b>sa</b>fe; <b>ato</b>mic <b>comm</b>its |
| **Row-level `UPDATE` / `DELETE` / `MERGE INTO`** | [<b>Upse</b>rts](00-data-basics-for-beginners.md#upsert-and-merge) <b>a</b>nd CDC <b>mer</b>ges, <b>Gene</b>ral <b>Da</b>ta <b>Prote</b>ction <b>Regul</b>ation (GDPR) <b>dele</b>tes |
| **Schema evolution** | <b>A</b>dd, <b>dr</b>op, <b>ren</b>ame, <b>reor</b>der <b>colu</b>mns **without rewriting data** (<b>col</b>umn IDs, <b>n</b>ot <b>nam</b>es) |
| **Hidden partitioning** | <b>Parti</b>tion <b>b</b>y <b>trans</b>forms (<b>e</b>.g., `day(ts)`), <b>s</b>o <b>quer</b>ies <b>don</b>'t <b>ne</b>ed <b>t</b>o <b>refer</b>ence <b>parti</b>tion <b>colu</b>mns |
| **Partition evolution** | <b>Cha</b>nge <b>partit</b>ioning <b>sch</b>eme <b>with</b>out <b>rewri</b>ting <b>o</b>ld <b>da</b>ta |
| **Time travel** | <b>Que</b>ry <b>a</b> <b>pa</b>st <b>snap</b>shot/<b>ti</b>me; <b>ro</b>ll <b>ba</b>ck <b>b</b>ad <b>wri</b>tes |
| **Copy-on-write vs merge-on-read** | <b>C</b>oW <b>rewr</b>ites <b>fil</b>es <b>o</b>n <b>upd</b>ate (<b>fas</b>ter <b>rea</b>ds); <b>M</b>oR <b>wri</b>tes <b>del</b>ete <b>fil</b>es (<b>fas</b>ter <b>wri</b>tes, <b>compa</b>ction <b>nee</b>ded) |

**Maintenance (exam favorite):**
- **Compaction**: <b>rewr</b>ite <b>ma</b>ny [<b>sma</b>ll <b>fil</b>es](00-data-basics-for-beginners.md#small-files-problem) <b>in</b>to <b>few</b>er <b>lar</b>ge <b>fil</b>es. <b>I</b>n <b>Ath</b>ena: `OPTIMIZE table REWRITE DATA USING BIN_PACK`.
- **Expire snapshots / remove orphan files**: <b>recl</b>aim <b>stor</b>age <b>fr</b>om <b>o</b>ld <b>vers</b>ions. <b>I</b>n <b>Ath</b>ena: `VACUUM table`.
- **Glue Data Catalog table optimizers** <b>c</b>an <b>r</b>un <b>compa</b>ction, <b>snap</b>shot <b>reten</b>tion, <b>a</b>nd <b>orp</b>han <b>fi</b>le <b>dele</b>tion **automatically** <b>f</b>or <b>Iceb</b>erg <b>tab</b>les.

**Amazon S3 Tables:** **table buckets** <b>th</b>at <b>sto</b>re <b>Iceb</b>erg <b>tab</b>les <b>a</b>s <b>a</b> <b>mana</b>ged <b>reso</b>urce, <b>wi</b>th **automatic compaction, snapshot management, and unreferenced file removal**, <b>pl</b>us <b>hig</b>her <b>perfor</b>mance <b>f</b>or <b>tabu</b>lar <b>da</b>ta. <b>Que</b>ry <b>fr</b>om <b>Ath</b>ena, <b>Reds</b>hift, EMR, <b>Gl</b>ue, <b>a</b>nd [<b>Fire</b>hose](00-data-basics-for-beginners.md#amazon-data-firehose) <b>c</b>an <b>deli</b>ver <b>in</b>to <b>th</b>em. → "<b>Mana</b>ged <b>Iceb</b>erg <b>wi</b>th <b>lea</b>st <b>mainte</b>nance" = **S3 Tables**.

**Other formats you may see as distractors:** **[Apache Hudi](00-data-basics-for-beginners.md#apache-hudi)** (<b>upse</b>rts/<b>increm</b>ental <b>pul</b>ls, <b>C</b>oW/<b>M</b>oR, <b>str</b>ong <b>o</b>n EMR) <b>a</b>nd **[Delta Lake](00-data-basics-for-beginners.md#delta-lake)** (<b>Datab</b>ricks-<b>ori</b>gin). AWS <b>analy</b>tics <b>serv</b>ices <b>supp</b>ort <b>a</b>ll <b>thr</b>ee, <b>b</b>ut <b>Iceb</b>erg <b>i</b>s <b>t</b>he <b>o</b>ne <b>t</b>he <b>ex</b>am <b>gui</b>de <b>nam</b>es.

**Engines that work with Iceberg on AWS:** <b>Ath</b>ena (<b>re</b>ad/<b>wri</b>te, <b>Da</b>ta <b>Manipu</b>lation <b>Lang</b>uage [DML], <b>ti</b>me <b>tra</b>vel), <b>Gl</b>ue ETL, EMR ([<b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark), [<b>Tri</b>no](00-data-basics-for-beginners.md#presto-and-trino), [<b>Fli</b>nk](00-data-basics-for-beginners.md#apache-flink)), <b>Reds</b>hift (<b>re</b>ad), <b>Fire</b>hose (<b>wri</b>te), [<b>Mana</b>ged <b>Serv</b>ice <b>f</b>or <b>Apa</b>che <b>Fli</b>nk](00-data-basics-for-beginners.md#managed-service-for-apache-flink).

### 🆕 Vector index types (skills 2.1.3, 2.1.8)

**Background:** <b>A</b>n **embedding** <b>i</b>s <b>a</b> <b>li</b>st <b>o</b>f <b>numb</b>ers (<b>a</b> <b>vec</b>tor, <b>e</b>.g., 1,024 <b>dimen</b>sions) <b>repres</b>enting <b>mean</b>ing. <b>Simi</b>lar <b>ite</b>ms <b>ha</b>ve <b>nea</b>rby <b>vect</b>ors. **Similarity search** <b>fin</b>ds <b>t</b>he <b>near</b>est <b>vect</b>ors <b>usi</b>ng <b>a</b> <b>dist</b>ance <b>met</b>ric: **cosine similarity**, **Euclidean (L2)**, <b>o</b>r **dot product**. <b>Exa</b>ct <b>sea</b>rch <b>comp</b>ares <b>agai</b>nst <b>eve</b>ry <b>vec</b>tor (<b>sl</b>ow <b>a</b>t <b>sca</b>le), <b>s</b>o <b>sto</b>res <b>u</b>se **approximate nearest neighbor (ANN)** <b>inde</b>xes.

| | **HNSW** (<b>Hierar</b>chical <b>Navig</b>able <b>Sma</b>ll <b>Wor</b>ld) | **IVF** (<b>Inve</b>rted <b>Fi</b>le <b>ind</b>ex) |
|---|---|---|
| <b>Struc</b>ture | <b>Mul</b>ti-<b>lay</b>er **graph**; <b>upp</b>er <b>lay</b>ers <b>a</b>re <b>spa</b>rse "<b>high</b>ways," <b>t</b>he <b>bot</b>tom <b>lay</b>er <b>h</b>as <b>a</b>ll <b>vect</b>ors | <b>Vect</b>ors **clustered** <b>aro</b>und <b>centr</b>oids (<b>k</b>-<b>mea</b>ns); <b>ea</b>ch <b>clus</b>ter <b>i</b>s <b>a</b> <b>li</b>st |
| <b>Sea</b>rch | <b>Gre</b>edy <b>wa</b>lk <b>fr</b>om <b>t</b>he <b>t</b>op <b>lay</b>er <b>do</b>wn <b>t</b>o <b>t</b>he <b>near</b>est <b>neigh</b>bors | <b>Fi</b>nd <b>t</b>he <b>near</b>est <b>centr</b>oids, <b>sea</b>rch <b>on</b>ly <b>tho</b>se <b>clus</b>ters (`nprobe`/`lists`) |
| <b>Rec</b>all / <b>spe</b>ed | **High recall, very fast queries** | <b>Go</b>od; <b>rec</b>all <b>depe</b>nds <b>o</b>n <b>h</b>ow <b>ma</b>ny <b>clus</b>ters <b>a</b>re <b>pro</b>bed |
| <b>Mem</b>ory | **High** (<b>gra</b>ph <b>edg</b>es) | **Lower** |
| <b>Bui</b>ld | <b>Slo</b>wer <b>t</b>o <b>bui</b>ld, <b>n</b>o <b>trai</b>ning <b>st</b>ep, <b>hand</b>les <b>inse</b>rts <b>increme</b>ntally | <b>Fas</b>ter <b>bui</b>ld <b>b</b>ut <b>nee</b>ds <b>a</b> **training** <b>st</b>ep <b>o</b>n <b>represe</b>ntative <b>da</b>ta; <b>hea</b>vy <b>da</b>ta <b>dri</b>ft <b>c</b>an <b>requ</b>ire <b>rebui</b>lding |
| <b>Tun</b>ing <b>kno</b>bs | `m` (<b>connec</b>tions <b>p</b>er <b>no</b>de), `ef_construction`, `ef_search` | <b>num</b>ber <b>o</b>f <b>lis</b>ts/<b>clus</b>ters, <b>num</b>ber <b>o</b>f <b>pro</b>bes |
| <b>Cho</b>ose <b>wh</b>en | <b>L</b>ow <b>late</b>ncy + <b>hi</b>gh <b>accu</b>racy, <b>mem</b>ory <b>i</b>s OK | <b>Ve</b>ry <b>lar</b>ge <b>data</b>sets, <b>mem</b>ory/<b>co</b>st <b>constr</b>ained |

**Where vectors live on AWS:**

| <b>Sto</b>re | <b>Not</b>es |
|---|---|
| **Aurora PostgreSQL / RDS PostgreSQL + pgvector** | `CREATE INDEX … USING hnsw` <b>o</b>r `ivfflat`; <b>vect</b>ors <b>ne</b>xt <b>t</b>o <b>relat</b>ional <b>da</b>ta; SQL <b>filte</b>ring |
| **OpenSearch Service / Serverless** | <b>k</b>-NN <b>plu</b>gin (HNSW, IVF <b>v</b>ia <b>Face</b>book AI <b>Simil</b>arity <b>Sea</b>rch [FAISS]/<b>Luc</b>ene <b>engi</b>nes); <b>hyb</b>rid <b>keyw</b>ord + <b>vec</b>tor <b>sea</b>rch; <b>defa</b>ult <b>sto</b>re <b>f</b>or <b>Bedr</b>ock <b>Knowl</b>edge <b>Bas</b>es <b>qui</b>ck <b>cre</b>ate |
| **MemoryDB** | <b>I</b>n-<b>mem</b>ory <b>vec</b>tor <b>sea</b>rch <b>wi</b>th <b>ve</b>ry <b>l</b>ow <b>late</b>ncy (<b>a</b>nd <b>dura</b>ble) |
| **Neptune Analytics, DocumentDB** | <b>Vec</b>tor <b>sea</b>rch <b>along</b>side <b>gra</b>ph/<b>docu</b>ment <b>da</b>ta |

---

## Task 2.2: Understand data cataloging systems

### Core concepts

<b>A</b> **data catalog** <b>sto</b>res **metadata**: <b>tab</b>le <b>nam</b>es, <b>colu</b>mns <b>a</b>nd <b>typ</b>es, <b>parti</b>tion <b>locat</b>ions, <b>fi</b>le <b>form</b>ats, <b>own</b>ers, <b>descri</b>ptions. <b>Engi</b>nes <b>re</b>ad <b>t</b>he <b>cata</b>log <b>t</b>o <b>kn</b>ow *<b>h</b>ow* <b>t</b>o <b>re</b>ad <b>fil</b>es. <b>With</b>out <b>i</b>t, <b>a</b> <b>buc</b>ket <b>o</b>f <b>Parq</b>uet <b>fil</b>es <b>i</b>s <b>ju</b>st <b>a</b> <b>buc</b>ket <b>o</b>f <b>fil</b>es.

- **Technical catalog** → <b>sche</b>mas, <b>parti</b>tions, <b>locat</b>ions (<b>f</b>or <b>engi</b>nes). <b>Exam</b>ple: **AWS Glue Data Catalog**, **Hive metastore**.
- **Business catalog** → <b>busi</b>ness <b>mean</b>ing, <b>owner</b>ship, <b>glos</b>sary <b>ter</b>ms, <b>da</b>ta <b>prod</b>ucts, <b>acc</b>ess <b>requ</b>ests (<b>f</b>or <b>peo</b>ple). <b>Exam</b>ple: **Amazon SageMaker Catalog**.

### Technical catalogs (skills 2.2.1, 2.2.2)

**AWS Glue Data Catalog:**
- <b>O</b>ne <b>p</b>er <b>acco</b>unt <b>p</b>er <b>Reg</b>ion. <b>Organ</b>ized <b>a</b>s **databases → tables → partitions**.
- **Hive-metastore compatible**, <b>us</b>ed <b>b</b>y **Athena, Redshift Spectrum, EMR, Glue ETL, Lake Formation, [QuickSight](00-data-basics-for-beginners.md#amazon-quicksight) (via Athena)**.
- <b>Supp</b>orts <b>Iceb</b>erg, <b>Hu</b>di, <b>a</b>nd <b>Del</b>ta <b>tab</b>le <b>meta</b>data; **partition indexes** <b>spe</b>ed <b>u</b>p <b>quer</b>ies <b>o</b>n <b>tab</b>les <b>wi</b>th <b>ma</b>ny <b>parti</b>tions; **column statistics** <b>he</b>lp <b>que</b>ry <b>plan</b>ning.
- EMR <b>c</b>an <b>u</b>se <b>t</b>he <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log **as its Hive metastore** (<b>recomm</b>ended <b>f</b>or <b>sha</b>red, <b>persi</b>stent <b>meta</b>data) <b>inst</b>ead <b>o</b>f <b>a</b> <b>clus</b>ter-<b>loc</b>al <b>o</b>r RDS-<b>hos</b>ted <b>Hi</b>ve <b>metas</b>tore.
- <b>C</b>an <b>b</b>e <b>encry</b>pted (<b>cata</b>log <b>encry</b>ption <b>sett</b>ings <b>wi</b>th [<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice [KMS]](00-data-basics-for-beginners.md#aws-kms)) <b>a</b>nd <b>gove</b>rned <b>b</b>y <b>La</b>ke <b>Forma</b>tion.

**Consuming data through the catalog:** <b>on</b>ce <b>a</b> <b>tab</b>le <b>i</b>s <b>catal</b>oged, <b>Ath</b>ena <b>ru</b>ns `SELECT * FROM db.table`, <b>Reds</b>hift <b>crea</b>tes `CREATE EXTERNAL SCHEMA … FROM DATA CATALOG`, <b>a</b>nd <b>Gl</b>ue <b>jo</b>bs <b>u</b>se `from_catalog(database, table_name)`. <b>Y</b>ou <b>g</b>et <b>o</b>ne <b>defin</b>ition <b>sha</b>red <b>b</b>y <b>ma</b>ny <b>engi</b>nes.

### Glue crawlers (skill 2.2.3)

<b>A</b> **crawler** <b>conn</b>ects <b>t</b>o <b>a</b> <b>da</b>ta <b>sto</b>re, <b>us</b>es **classifiers** <b>t</b>o <b>inf</b>er <b>sch</b>ema, <b>a</b>nd <b>crea</b>tes/<b>upda</b>tes <b>tab</b>les <b>a</b>nd <b>parti</b>tions.

| <b>Sett</b>ing | <b>Explan</b>ation |
|---|---|
| **Data sources** | S3, [<b>Ja</b>va <b>Data</b>base <b>Connec</b>tivity [JDBC]](00-data-basics-for-beginners.md#jdbc-and-odbc) (RDS, <b>Reds</b>hift, <b>o</b>n-<b>pr</b>em), <b>Dyna</b>moDB, [<b>Mong</b>oDB](00-data-basics-for-beginners.md#mongodb)/<b>Docum</b>entDB, <b>Del</b>ta/<b>Iceb</b>erg/<b>Hu</b>di <b>tab</b>les |
| **Classifiers** | <b>Bui</b>lt-<b>i</b>n ([<b>Com</b>ma-<b>Separ</b>ated <b>Val</b>ues [CSV]](00-data-basics-for-beginners.md#csv), JSON, <b>Parq</b>uet, [<b>Av</b>ro](00-data-basics-for-beginners.md#avro), [<b>Optim</b>ized <b>R</b>ow <b>Colu</b>mnar [ORC]](00-data-basics-for-beginners.md#orc), <b>Exten</b>sible <b>Mar</b>kup <b>Lang</b>uage [XML]…) + **custom** (<b>Gr</b>ok, XML, JSON <b>pa</b>th, CSV) <b>f</b>or <b>unus</b>ual <b>form</b>ats; <b>fir</b>st <b>class</b>ifier <b>th</b>at <b>matc</b>hes <b>wi</b>th <b>certa</b>inty <b>wi</b>ns |
| **Include/exclude patterns** | <b>Sk</b>ip <b>fold</b>ers/<b>fil</b>es (<b>e</b>.g., `_temporary`, `*.metadata`) |
| **Schema change policy** | <b>Upd</b>ate <b>tab</b>le <b>defin</b>ition / <b>a</b>dd <b>n</b>ew <b>colu</b>mns <b>on</b>ly / <b>ign</b>ore <b>chan</b>ges <b>a</b>nd <b>l</b>og; <b>dele</b>ted <b>obje</b>cts → <b>del</b>ete, <b>ma</b>rk <b>depre</b>cated, <b>o</b>r <b>ign</b>ore |
| **Recrawl policy** | <b>Cra</b>wl <b>a</b>ll <b>fold</b>ers, **crawl new folders only** (<b>increm</b>ental), <b>o</b>r **S3 event mode** (<b>cra</b>wl <b>on</b>ly <b>chan</b>ged <b>obje</b>cts <b>fr</b>om [<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice [SQS]](00-data-basics-for-beginners.md#amazon-sqs) <b>eve</b>nts) |
| **Grouping** | "<b>Cre</b>ate <b>a</b> <b>sin</b>gle <b>sch</b>ema <b>f</b>or <b>ea</b>ch S3 <b>pa</b>th" <b>avo</b>ids <b>o</b>ne <b>tab</b>le <b>p</b>er <b>fol</b>der <b>wh</b>en <b>sche</b>mas <b>a</b>re <b>compa</b>tible |
| **Schedule** | <b>O</b>n <b>dem</b>and, <b>cr</b>on, <b>o</b>r <b>a</b>s <b>pa</b>rt <b>o</b>f <b>a</b> <b>Gl</b>ue <b>work</b>flow |

**When not to use a crawler:** <b>t</b>he <b>sch</b>ema <b>i</b>s <b>kno</b>wn <b>a</b>nd <b>sta</b>ble (<b>def</b>ine <b>t</b>he <b>tab</b>le <b>wi</b>th DDL / [<b>CloudFo</b>rmation](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam) <b>inst</b>ead), <b>o</b>r <b>parti</b>tions <b>fol</b>low <b>a</b> <b>predic</b>table <b>patt</b>ern (**partition projection**).

### Synchronizing partitions (skill 2.2.4)

<b>N</b>ew <b>parti</b>tion <b>fold</b>ers <b>i</b>n S3 (<b>e</b>.g., `year=2026/month=11/day=19/`) <b>a</b>re <b>invis</b>ible <b>t</b>o <b>Ath</b>ena <b>unt</b>il <b>t</b>he <b>cata</b>log <b>kno</b>ws <b>abo</b>ut <b>th</b>em.

| <b>Met</b>hod | <b>Not</b>es |
|---|---|
| **Re-run crawler** (<b>increm</b>ental) | <b>Ea</b>sy, <b>b</b>ut <b>sched</b>uled <b>a</b>nd <b>cos</b>ts <b>craw</b>ler <b>ti</b>me |
| **`MSCK REPAIR TABLE`** | <b>Sca</b>ns S3 <b>a</b>nd <b>ad</b>ds <b>Hi</b>ve-<b>sty</b>le <b>parti</b>tions; <b>sl</b>ow <b>o</b>n <b>hu</b>ge <b>tab</b>les |
| **`ALTER TABLE ADD PARTITION`** | <b>Expl</b>icit <b>a</b>nd <b>fa</b>st; <b>wor</b>ks <b>f</b>or <b>n</b>on-<b>Hi</b>ve <b>layo</b>uts <b>t</b>oo |
| **Glue job writes with catalog update** | `enableUpdateCatalog=True` + `partitionKeys` <b>ad</b>ds <b>parti</b>tions <b>a</b>s <b>t</b>he <b>j</b>ob <b>wri</b>tes |
| **Athena partition projection** | <b>Parti</b>tions **computed from table properties** (<b>ran</b>ges, <b>dat</b>es, <b>enu</b>ms); <b>n</b>o <b>cata</b>log <b>look</b>ups. <b>Be</b>st <b>f</b>or **highly partitioned tables** <b>a</b>nd <b>predic</b>table <b>pat</b>hs. |
| **Iceberg tables** | <b>Parti</b>tions <b>trac</b>ked <b>i</b>n <b>tab</b>le <b>meta</b>data <b>automat</b>ically |

### Connections for cataloging (skill 2.2.5)

<b>A</b> **Glue connection** <b>hol</b>ds <b>wh</b>at <b>a</b> <b>craw</b>ler <b>o</b>r <b>j</b>ob <b>nee</b>ds <b>t</b>o <b>rea</b>ch <b>a</b> <b>sou</b>rce/<b>tar</b>get: <b>ty</b>pe (**JDBC**, <b>Mong</b>oDB, [<b>Kaf</b>ka](00-data-basics-for-beginners.md#apache-kafka), **Network**, <b>market</b>place/<b>cus</b>tom <b>conne</b>ctors), <b>endp</b>oint <b>Unif</b>orm <b>Reso</b>urce <b>Loca</b>tor (URL), <b>creden</b>tials (<b>prefe</b>rably **[Secrets Manager](00-data-basics-for-beginners.md#aws-secrets-manager)**), <b>a</b>nd **[Virtual Private Cloud [VPC]](00-data-basics-for-beginners.md#amazon-vpc), subnet, security group**. <b>Reme</b>mber <b>t</b>he <b>se</b>lf-<b>refere</b>ncing <b>secu</b>rity <b>gro</b>up <b>ru</b>le <b>a</b>nd <b>a</b> <b>rou</b>te <b>t</b>o <b>t</b>he <b>sou</b>rce (<b>Netw</b>ork <b>Addr</b>ess <b>Transl</b>ation [NAT] <b>gate</b>way <b>f</b>or <b>t</b>he <b>inte</b>rnet, **S3 gateway endpoint** <b>f</b>or S3 <b>fr</b>om <b>a</b> <b>priv</b>ate <b>sub</b>net).

### 🆕 Business data catalogs: Amazon SageMaker Catalog (skill 2.2.6)

**SageMaker Catalog** (<b>bui</b>lt <b>o</b>n <b>Ama</b>zon <b>Data</b>Zone, <b>pa</b>rt <b>o</b>f **SageMaker Unified Studio**) <b>i</b>s <b>whe</b>re <b>peo</b>ple **find, understand, request, and govern** <b>da</b>ta <b>a</b>nd <b>Artif</b>icial <b>Intell</b>igence (AI) <b>ass</b>ets.

| <b>Conc</b>ept | <b>Mean</b>ing |
|---|---|
| **Assets** | <b>Tab</b>les (<b>Gl</b>ue/<b>Reds</b>hift), S3 <b>da</b>ta, <b>mod</b>els, <b>dashb</b>oards <b>regis</b>tered <b>i</b>n <b>t</b>he <b>cata</b>log |
| **Business metadata** | <b>Descri</b>ptions, **business glossary** <b>ter</b>ms, **metadata forms** (<b>cus</b>tom <b>requ</b>ired <b>fie</b>lds <b>li</b>ke <b>own</b>er, <b>sensit</b>ivity) |
| **AI-generated descriptions** | <b>Gener</b>ative AI <b>sugg</b>ests <b>busi</b>ness <b>nam</b>es/<b>descri</b>ptions <b>f</b>or <b>ass</b>ets <b>a</b>nd <b>colu</b>mns |
| **Publishing** | <b>Produ</b>cers <b>publ</b>ish <b>ass</b>ets (<b>o</b>r <b>bund</b>les <b>a</b>s **data products**) <b>s</b>o <b>oth</b>ers <b>c</b>an <b>disc</b>over <b>th</b>em |
| **Subscription workflow** | <b>Consu</b>mers **request access** <b>f</b>or <b>the</b>ir <b>proj</b>ect → <b>own</b>er **approves** → <b>acc</b>ess <b>i</b>s **granted automatically** (<b>e</b>.g., <b>La</b>ke <b>Forma</b>tion <b>o</b>r <b>Reds</b>hift <b>gra</b>nts) |
| **Data quality & lineage** | <b>Qual</b>ity <b>sco</b>res <b>a</b>nd **lineage graphs** <b>sho</b>wn <b>o</b>n <b>ass</b>ets |

> <b>Techn</b>ical <b>v</b>s <b>busi</b>ness <b>cata</b>log <b>i</b>n <b>o</b>ne <b>li</b>ne: **Glue Data Catalog tells Athena how to read the table; SageMaker Catalog tells an analyst what the table means, who owns it, and how to get access.**

---

## Task 2.3: Manage the lifecycle of data

### Load and unload between S3 and Redshift (skill 2.3.1)

**COPY (load):**
- <b>Loa</b>ds <b>i</b>n **parallel**, <b>wi</b>th <b>ea</b>ch <b>sli</b>ce <b>read</b>ing <b>fil</b>es. **Split data into multiple files** (<b>idea</b>lly <b>a</b> <b>mult</b>iple <b>o</b>f <b>t</b>he <b>num</b>ber <b>o</b>f <b>sli</b>ces), <b>simi</b>lar <b>siz</b>es (1 MB–1 GB <b>compr</b>essed), <b>compr</b>essed (GZIP, <b>Zstan</b>dard [ZSTD], BZIP2, LZOP) <b>o</b>r <b>colu</b>mnar (<b>Parq</b>uet/ORC).
- <b>U</b>se <b>a</b> **manifest file** <b>t</b>o <b>lo</b>ad <b>a</b>n <b>exa</b>ct <b>li</b>st <b>o</b>f <b>fil</b>es (<b>avo</b>ids <b>load</b>ing <b>part</b>ial <b>o</b>r <b>wro</b>ng <b>fil</b>es).
- <b>Autho</b>rize <b>wi</b>th <b>a</b>n **[Identity and Access Management [IAM]](00-data-basics-for-beginners.md#aws-iam) role** <b>atta</b>ched <b>t</b>o <b>t</b>he <b>clus</b>ter (`IAM_ROLE 'arn:…'`), <b>n</b>ot <b>acc</b>ess <b>ke</b>ys.
- <b>Use</b>ful <b>opti</b>ons: `FORMAT AS PARQUET|JSON|CSV`, `COMPUPDATE`, `STATUPDATE`, `MAXERROR`, `REGION`, `TIMEFORMAT`.
- **Errors** → `STL_LOAD_ERRORS` / `SYS_LOAD_ERROR_DETAIL`.
- **Upserts:** COPY <b>in</b>to <b>a</b> **staging table**, <b>th</b>en `MERGE` (<b>o</b>r <b>del</b>ete + <b>ins</b>ert) <b>in</b>to <b>t</b>he <b>tar</b>get <b>i</b>n <b>o</b>ne <b>transa</b>ction.
- **Auto-copy**: `COPY JOB` <b>c</b>an <b>wat</b>ch <b>a</b>n S3 <b>pre</b>fix <b>a</b>nd <b>lo</b>ad <b>n</b>ew <b>fil</b>es <b>automat</b>ically.

**UNLOAD (export):**
- `UNLOAD ('select …') TO 's3://…' IAM_ROLE '…' FORMAT AS PARQUET PARTITION BY (col)`. <b>Wri</b>tes <b>i</b>n <b>para</b>llel (<b>mult</b>iple <b>fil</b>es) <b>b</b>y <b>defa</b>ult; `PARALLEL OFF` <b>f</b>or <b>a</b> <b>sin</b>gle <b>fi</b>le (<b>slo</b>wer).
- <b>C</b>an <b>encr</b>ypt <b>wi</b>th KMS (`KMS_KEY_ID`) <b>a</b>nd <b>s</b>et `MAXFILESIZE`.
- <b>Typi</b>cal <b>u</b>se: <b>arch</b>ive <b>o</b>ld <b>wareh</b>ouse <b>da</b>ta <b>t</b>o S3 <b>a</b>nd <b>que</b>ry <b>i</b>t <b>wi</b>th <b>Spec</b>trum (<b>h</b>ot <b>da</b>ta <b>i</b>n <b>Reds</b>hift, <b>co</b>ld <b>da</b>ta <b>i</b>n S3).

### S3 Lifecycle: tiering and expiration (skills 2.3.2, 2.3.3)

<b>A</b> **lifecycle configuration** <b>i</b>s <b>a</b> <b>s</b>et <b>o</b>f <b>rul</b>es <b>sco</b>ped <b>b</b>y **prefix and/or object tags**:
- **Transition actions:** <b>mo</b>ve <b>obje</b>cts <b>t</b>o <b>chea</b>per <b>clas</b>ses <b>aft</b>er <b>N</b> <b>da</b>ys (<b>e</b>.g., <b>Stan</b>dard → <b>Stan</b>dard-IA <b>a</b>t 30 <b>da</b>ys → <b>Glac</b>ier <b>Flex</b>ible <b>Retri</b>eval <b>a</b>t 90 <b>da</b>ys → <b>De</b>ep <b>Arch</b>ive <b>a</b>t 365 <b>da</b>ys).
- **Expiration actions:** <b>del</b>ete <b>obje</b>cts <b>aft</b>er <b>N</b> <b>da</b>ys.
- **Noncurrent version actions:** <b>trans</b>ition/<b>exp</b>ire **old versions** <b>i</b>n <b>versi</b>oned <b>buck</b>ets (<b>e</b>.g., <b>ke</b>ep 3 <b>noncu</b>rrent <b>vers</b>ions <b>f</b>or 30 <b>da</b>ys).
- **Abort incomplete multipart uploads** <b>aft</b>er <b>N</b> <b>da</b>ys (<b>hid</b>den <b>stor</b>age <b>co</b>st).
- **Expired object delete markers** <b>clea</b>nup.

<b>Rul</b>es <b>t</b>o <b>reme</b>mber:
- <b>Obje</b>cts <b>mu</b>st <b>st</b>ay **30 days** <b>i</b>n <b>Stan</b>dard <b>bef</b>ore <b>transit</b>ioning <b>t</b>o <b>Stan</b>dard-IA/<b>O</b>ne <b>Zo</b>ne-IA <b>v</b>ia <b>lifec</b>ycle.
- <b>Mini</b>mum <b>stor</b>age <b>dura</b>tion <b>char</b>ges <b>app</b>ly (<b>Infre</b>quent <b>Acc</b>ess [IA] 30, <b>Glac</b>ier <b>Inst</b>ant <b>Retri</b>eval [<b>Glac</b>ier IR]/<b>Flex</b>ible 90, <b>De</b>ep <b>Arch</b>ive 180 <b>da</b>ys). <b>Dele</b>ting <b>ear</b>ly <b>sti</b>ll <b>bil</b>ls <b>t</b>he <b>mini</b>mum.
- <b>Lifec</b>ycle <b>ru</b>ns <b>asynchr</b>onously (<b>n</b>ot <b>a</b>t <b>a</b>n <b>exa</b>ct <b>min</b>ute).
- **Unknown access pattern** → <b>u</b>se <b>Intell</b>igent-<b>Tier</b>ing <b>inst</b>ead <b>o</b>f <b>gues</b>sing <b>trans</b>ition <b>da</b>ys.

### S3 versioning and DynamoDB TTL (skill 2.3.4)

**S3 versioning:**
- <b>Kee</b>ps <b>eve</b>ry <b>vers</b>ion <b>o</b>f <b>a</b>n <b>obj</b>ect; <b>prot</b>ects <b>agai</b>nst <b>accid</b>ental <b>overw</b>rite/<b>del</b>ete.
- <b>A</b> <b>del</b>ete <b>with</b>out <b>a</b> <b>vers</b>ion ID <b>ad</b>ds <b>a</b> **delete marker** (<b>t</b>he <b>obj</b>ect "<b>disap</b>pears" <b>b</b>ut <b>o</b>ld <b>vers</b>ions <b>rem</b>ain). <b>Dele</b>ting <b>t</b>he <b>mar</b>ker <b>rest</b>ores <b>i</b>t.
- <b>On</b>ce <b>enab</b>led, <b>i</b>t <b>c</b>an <b>on</b>ly <b>b</b>e **suspended**, <b>nev</b>er <b>ful</b>ly <b>disa</b>bled.
- <b>Requ</b>ired <b>f</b>or **replication** <b>a</b>nd **Object Lock**. <b>Comb</b>ine <b>wi</b>th **Multi-Factor Authentication (MFA) Delete** <b>f</b>or <b>ext</b>ra <b>prote</b>ction.
- <b>Cont</b>rol <b>co</b>st <b>wi</b>th <b>noncu</b>rrent-<b>vers</b>ion <b>lifec</b>ycle <b>rul</b>es.

**DynamoDB TTL:**
- <b>Y</b>ou <b>cho</b>ose <b>a</b>n <b>attri</b>bute <b>hold</b>ing <b>a</b>n **epoch timestamp in seconds**. <b>Aft</b>er <b>th</b>at <b>ti</b>me, <b>Dyna</b>moDB <b>dele</b>tes <b>t</b>he <b>it</b>em **automatically at no cost** (<b>n</b>o WCU <b>cons</b>umed).
- <b>Dele</b>tion <b>i</b>s **not immediate**. <b>I</b>t <b>typic</b>ally <b>happ</b>ens <b>wit</b>hin <b>a</b> <b>f</b>ew <b>da</b>ys, <b>s</b>o <b>fil</b>ter <b>expi</b>red <b>ite</b>ms <b>i</b>n <b>quer</b>ies <b>i</b>f <b>exact</b>ness <b>matt</b>ers.
- TTL <b>dele</b>tes <b>app</b>ear <b>i</b>n **DynamoDB Streams** (<b>mar</b>ked <b>a</b>s <b>sys</b>tem <b>dele</b>tes), <b>s</b>o <b>y</b>ou <b>c</b>an <b>arch</b>ive <b>expi</b>red <b>ite</b>ms <b>t</b>o S3 <b>v</b>ia <b>Lam</b>bda/<b>Fire</b>hose.

### Deleting data for business and legal requirements (skill 2.3.5)

| <b>Requir</b>ement | <b>Appr</b>oach |
|---|---|
| <b>Del</b>ete <b>aft</b>er <b>reten</b>tion <b>per</b>iod | S3 <b>Lifec</b>ycle <b>expir</b>ation, <b>Dyna</b>moDB TTL, <b>Reds</b>hift <b>sched</b>uled `DELETE`/`TRUNCATE`, <b>Cloud</b>Watch <b>Lo</b>gs <b>reten</b>tion <b>sett</b>ings |
| **Right to be forgotten** (GDPR) <b>o</b>n <b>a</b> <b>da</b>ta <b>la</b>ke | <b>U</b>se **Iceberg** (`DELETE FROM … WHERE user_id = …` <b>i</b>n <b>Ath</b>ena/<b>Gl</b>ue) <b>inst</b>ead <b>o</b>f <b>rewri</b>ting <b>Parq</b>uet <b>parti</b>tions <b>b</b>y <b>ha</b>nd; <b>th</b>en <b>exp</b>ire <b>snaps</b>hots <b>s</b>o <b>o</b>ld <b>fil</b>es <b>a</b>re <b>remo</b>ved |
| <b>Fi</b>nd <b>whe</b>re <b>pers</b>onal <b>da</b>ta <b>liv</b>es <b>fir</b>st | **[Amazon Macie](00-data-basics-for-beginners.md#amazon-macie)** (S3), <b>cata</b>log <b>ta</b>gs, <b>line</b>age |
| **Must not be deleted** <b>f</b>or <b>N</b> <b>yea</b>rs (<b>Wri</b>te <b>On</b>ce, <b>Re</b>ad <b>Ma</b>ny [WORM]) | **S3 Object Lock**: **compliance mode** (<b>n</b>o <b>o</b>ne, <b>inclu</b>ding <b>ro</b>ot, <b>c</b>an <b>del</b>ete <b>o</b>r <b>shor</b>ten <b>reten</b>tion) <b>v</b>s **governance mode** (<b>privi</b>leged <b>use</b>rs <b>wi</b>th <b>spec</b>ial <b>permi</b>ssion <b>c</b>an <b>over</b>ride); **legal hold** (<b>indef</b>inite <b>unt</b>il <b>remo</b>ved). <b>Glac</b>ier **Vault Lock** <b>f</b>or <b>vau</b>lts. |
| <b>Pro</b>ve <b>dele</b>tion | [<b>Cloud</b>Trail](00-data-basics-for-beginners.md#aws-cloudtrail) <b>da</b>ta <b>eve</b>nts, S3 <b>ser</b>ver <b>acc</b>ess <b>lo</b>gs |

> ⚠️ <b>Wi</b>th <b>versi</b>oning <b>o</b>n, "<b>dele</b>ting" <b>a</b>n <b>obj</b>ect <b>on</b>ly <b>ad</b>ds <b>a</b> <b>del</b>ete <b>mar</b>ker. <b>Tru</b>ly <b>remo</b>ving <b>da</b>ta <b>requ</b>ires <b>dele</b>ting **all versions** (<b>o</b>r <b>a</b> <b>lifec</b>ycle <b>ru</b>le <b>f</b>or <b>noncu</b>rrent <b>vers</b>ions).

### Resiliency and availability (skill 2.3.6)

| <b>Serv</b>ice | <b>Prote</b>ction <b>opti</b>ons |
|---|---|
| **S3** | <b>Mul</b>ti-AZ <b>b</b>y <b>defa</b>ult (<b>exc</b>ept <b>O</b>ne <b>Zo</b>ne <b>clas</b>ses); **Cross-Region / Same-Region Replication** (<b>versi</b>oning <b>requ</b>ired; **Replication Time Control** = 99.99% <b>o</b>f <b>obje</b>cts <b>i</b>n 15 <b>m</b>in); AWS <b>Bac</b>kup <b>f</b>or S3 |
| **DynamoDB** | **PITR** (<b>rest</b>ore <b>t</b>o <b>a</b>ny <b>sec</b>ond <b>i</b>n <b>t</b>he <b>la</b>st 35 <b>da</b>ys), <b>o</b>n-<b>dem</b>and <b>back</b>ups, **global tables** (<b>mul</b>ti-<b>Reg</b>ion <b>act</b>ive-<b>act</b>ive) |
| **Redshift** | **Automated snapshots** (<b>defa</b>ult 1-<b>d</b>ay <b>reten</b>tion, <b>u</b>p <b>t</b>o 35 <b>da</b>ys), <b>man</b>ual <b>snaps</b>hots (<b>ke</b>pt <b>unt</b>il <b>dele</b>ted), **cross-Region snapshot copy**, **Multi-AZ** <b>deploy</b>ments (RA3), <b>reloc</b>ation <b>t</b>o <b>anot</b>her AZ |
| **RDS / Aurora** | **Multi-AZ** (<b>fail</b>over), <b>re</b>ad <b>repl</b>icas (<b>sca</b>le <b>rea</b>ds, <b>cro</b>ss-<b>Reg</b>ion <b>Disa</b>ster <b>Reco</b>very [DR]), <b>autom</b>ated <b>back</b>ups + <b>snaps</b>hots, **Aurora Global Database** (<b>cro</b>ss-<b>Reg</b>ion, <1 <b>s</b> <b>l</b>ag) |
| **KDS / MSK** | <b>Da</b>ta <b>repli</b>cated <b>acr</b>oss 3 <b>Availa</b>bility <b>Zon</b>es [AZs] (KDS); MSK <b>mul</b>ti-AZ <b>brok</b>ers, MSK <b>Repli</b>cator <b>f</b>or <b>cro</b>ss-<b>clus</b>ter/<b>Reg</b>ion |
| **EMR** | <b>Sto</b>re <b>da</b>ta <b>i</b>n **S3, not Hadoop Distributed File System (HDFS)**, <b>s</b>o <b>clus</b>ter <b>lo</b>ss <b>does</b>n't <b>lo</b>se <b>da</b>ta; <b>mul</b>ti-<b>prim</b>ary <b>nod</b>es <b>f</b>or <b>Hi</b>gh <b>Availa</b>bility (HA) |
| **Centralized** | **AWS Backup** <b>poli</b>cies <b>acr</b>oss <b>serv</b>ices <b>a</b>nd <b>acco</b>unts; <b>bac</b>kup <b>vau</b>lt <b>lo</b>ck <b>f</b>or <b>immuta</b>bility |

<b>Kn</b>ow <b>t</b>he <b>diffe</b>rence: **high availability** (<b>surv</b>ive <b>a</b>n AZ <b>fail</b>ure <b>wi</b>th <b>n</b>o <b>o</b>r <b>bri</b>ef <b>interr</b>uption: <b>Mul</b>ti-AZ) <b>v</b>s **disaster recovery** (<b>reco</b>ver <b>i</b>n <b>anot</b>her <b>Reg</b>ion: <b>replic</b>ation, <b>snap</b>shot <b>co</b>py, <b>glo</b>bal <b>tab</b>les), <b>meas</b>ured <b>b</b>y **Recovery Point Objective [RPO]** (<b>h</b>ow <b>mu</b>ch <b>da</b>ta <b>y</b>ou <b>c</b>an <b>lo</b>se) <b>a</b>nd **Recovery Time Objective [RTO]** (<b>h</b>ow <b>lo</b>ng <b>reco</b>very <b>tak</b>es).

---

## Task 2.4: Design data models and schema evolution

### Designing schemas (skill 2.4.1)

**Redshift (dimensional modeling):**
- **Star schema**: <b>cent</b>ral **fact table** (<b>eve</b>nts/<b>meas</b>ures: <b>sal</b>es, <b>cli</b>cks) + **dimension tables** (<b>w</b>ho/<b>wh</b>at/<b>whe</b>re/<b>wh</b>en: <b>cust</b>omer, <b>prod</b>uct, <b>da</b>te). **[Snowflake](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce) schema** <b>norma</b>lizes <b>dimen</b>sions <b>furt</b>her (<b>mo</b>re <b>joi</b>ns).
- <b>Fa</b>ct: `DISTKEY` <b>o</b>n <b>t</b>he <b>mo</b>st <b>com</b>mon <b>lar</b>ge <b>jo</b>in <b>col</b>umn, `SORTKEY` <b>o</b>n <b>t</b>he <b>da</b>te <b>col</b>umn. <b>Sma</b>ll <b>dimen</b>sions: `DISTSTYLE ALL`.
- <b>Mode</b>rate **denormalization** <b>i</b>s <b>fi</b>ne <b>i</b>n <b>a</b> <b>colu</b>mnar <b>wareh</b>ouse. <b>I</b>t <b>redu</b>ces <b>joi</b>ns.
- <b>Prim</b>ary/<b>fore</b>ign <b>ke</b>ys <b>a</b>re **informational only** <b>i</b>n <b>Reds</b>hift (<b>n</b>ot <b>enfo</b>rced) <b>b</b>ut <b>he</b>lp <b>t</b>he <b>optim</b>izer. <b>Y</b>ou <b>mu</b>st <b>dedupl</b>icate <b>your</b>self.
- **Slowly changing dimensions (SCD):** **Type 1** <b>overw</b>rite (<b>n</b>o <b>hist</b>ory), **Type 2** <b>a</b>dd <b>a</b> <b>n</b>ew <b>r</b>ow <b>wi</b>th <b>effec</b>tive/<b>exp</b>iry <b>dat</b>es <b>a</b>nd <b>a</b> <b>curr</b>ent <b>fl</b>ag (<b>fu</b>ll <b>hist</b>ory), **Type 3** <b>a</b>dd <b>a</b> "<b>prev</b>ious <b>val</b>ue" <b>col</b>umn (<b>limi</b>ted <b>hist</b>ory).

**DynamoDB (access-pattern-first modeling):**
- <b>Li</b>st **access patterns first**, <b>th</b>en <b>des</b>ign <b>ke</b>ys. <b>The</b>re <b>a</b>re <b>n</b>o <b>joi</b>ns, <b>s</b>o <b>y</b>ou <b>des</b>ign <b>f</b>or <b>quer</b>ies, <b>n</b>ot <b>normali</b>zation.
- **Composite sort keys** (<b>e</b>.g., `ORDER#2026-11-19#123`) <b>ena</b>ble `begins_with` <b>a</b>nd <b>ran</b>ge <b>quer</b>ies.
- **Single-table design**: <b>seve</b>ral <b>ent</b>ity <b>typ</b>es <b>i</b>n <b>o</b>ne <b>tab</b>le <b>wi</b>th <b>gene</b>ric `PK`/`SK` (<b>e</b>.g., `CUSTOMER#1` / `ORDER#…`) <b>f</b>or <b>effic</b>ient <b>o</b>ne-<b>que</b>ry <b>fetc</b>hes <b>o</b>f <b>rela</b>ted <b>ite</b>ms.
- **Global Secondary Indexes (GSIs)** <b>f</b>or <b>alter</b>nate <b>acc</b>ess <b>patt</b>erns; **sparse indexes** (<b>on</b>ly <b>ite</b>ms <b>wi</b>th <b>t</b>he <b>attri</b>bute <b>app</b>ear) <b>f</b>or <b>effic</b>ient <b>filte</b>ring.
- <b>Avo</b>id <b>h</b>ot <b>ke</b>ys: <b>a</b>dd <b>a</b> <b>ran</b>dom/<b>calcu</b>lated <b>suf</b>fix (**write sharding**) <b>wh</b>en <b>o</b>ne <b>k</b>ey <b>ge</b>ts <b>t</b>oo <b>mu</b>ch <b>traf</b>fic.

**Lake Formation / data lake:**
- <b>Orga</b>nize S3 <b>in</b>to <b>zon</b>es: **raw (bronze)** → **cleaned (silver)** → **curated (gold)**, <b>ea</b>ch <b>a</b>s <b>Gl</b>ue <b>datab</b>ases.
- <b>Parti</b>tion <b>b</b>y <b>que</b>ry <b>filt</b>ers (<b>usua</b>lly <b>da</b>te), <b>u</b>se <b>Parq</b>uet/<b>Iceb</b>erg, <b>consi</b>stent <b>nam</b>ing.
- <b>Des</b>ign <b>f</b>or <b>permis</b>sions: <b>sepa</b>rate <b>sensi</b>tive <b>colu</b>mns <b>o</b>r <b>u</b>se **Lake Formation tags (LF-tags)** <b>a</b>nd **data filters** (<b>Dom</b>ain 4).

### Handling changing data characteristics: schema evolution (skill 2.4.2)

| <b>Situa</b>tion | <b>To</b>ol / <b>appr</b>oach |
|---|---|
| <b>N</b>ew <b>colu</b>mns <b>app</b>ear <b>i</b>n <b>sou</b>rce <b>fil</b>es | <b>Craw</b>ler <b>sch</b>ema <b>cha</b>nge <b>pol</b>icy (<b>a</b>dd <b>n</b>ew <b>colu</b>mns); <b>Parq</b>uet <b>sch</b>ema <b>merg</b>ing; **Iceberg** <b>a</b>dd <b>col</b>umn (<b>n</b>o <b>rewr</b>ite) |
| <b>Col</b>umn <b>rena</b>med <b>o</b>r <b>ty</b>pe <b>wide</b>ned | **Iceberg** <b>hand</b>les <b>ren</b>ame/<b>reor</b>der/<b>ty</b>pe <b>promo</b>tion <b>saf</b>ely; <b>pla</b>in <b>Hi</b>ve <b>tab</b>les <b>don</b>'t |
| <b>Strea</b>ming <b>produ</b>cers <b>cha</b>nge <b>mess</b>age <b>for</b>mat | **AWS Glue Schema Registry** (<b>Av</b>ro, JSON <b>Sch</b>ema, <b>Prot</b>obuf) <b>wi</b>th **compatibility modes**: **BACKWARD** (<b>defa</b>ult: <b>n</b>ew <b>sch</b>ema <b>c</b>an <b>re</b>ad <b>o</b>ld <b>da</b>ta), **FORWARD**, **FULL**, **NONE**, <b>pl</b>us <b>trans</b>itive <b>vari</b>ants. <b>Reje</b>cts <b>incomp</b>atible <b>sch</b>ema <b>vers</b>ions <b>bef</b>ore <b>th</b>ey <b>bre</b>ak <b>consu</b>mers. |
| <b>Mix</b>ed <b>typ</b>es <b>i</b>n <b>a</b> <b>col</b>umn (<b>str</b>ing/<b>i</b>nt) | <b>Gl</b>ue **`ResolveChoice`** (<b>ca</b>st, <b>ma</b>ke_struct, <b>proj</b>ect) |
| <b>Chan</b>ging <b>vol</b>ume/<b>velo</b>city | <b>Mo</b>ve <b>fr</b>om <b>bat</b>ch <b>t</b>o <b>strea</b>ming, <b>res</b>ize/<b>sca</b>le <b>sto</b>res, <b>repart</b>ition |
| <b>Reds</b>hift <b>tab</b>le <b>cha</b>nge | `ALTER TABLE ADD COLUMN`; <b>de</b>ep <b>co</b>py <b>f</b>or <b>struc</b>ture <b>chan</b>ges; **late-binding views** <b>s</b>o <b>vie</b>ws <b>don</b>'t <b>bre</b>ak <b>wh</b>en <b>under</b>lying <b>tab</b>les <b>cha</b>nge |

### Schema conversion (skill 2.4.3)

- **Homogeneous** <b>migra</b>tions (<b>Ora</b>cle → RDS <b>Ora</b>cle, <b>MyS</b>QL → <b>Aur</b>ora <b>MyS</b>QL): <b>n</b>o <b>conve</b>rsion <b>nee</b>ded. <b>U</b>se <b>nat</b>ive <b>too</b>ls <b>o</b>r DMS.
- **Heterogeneous** <b>migra</b>tions (<b>Ora</b>cle/SQL <b>Ser</b>ver → <b>Aur</b>ora <b>Postg</b>reSQL <b>o</b>r <b>Reds</b>hift): <b>conv</b>ert <b>sch</b>ema <b>obje</b>cts <b>fir</b>st.
  - **DMS Schema Conversion**: <b>mana</b>ged, <b>ins</b>ide <b>t</b>he DMS <b>cons</b>ole; <b>gener</b>ates <b>asses</b>sment <b>repo</b>rts <b>a</b>nd <b>conv</b>erts <b>sche</b>mas <b>a</b>nd <b>co</b>de <b>obje</b>cts.
  - **AWS SCT**: <b>downlo</b>adable <b>desk</b>top <b>to</b>ol <b>th</b>at <b>do</b>es <b>t</b>he <b>sa</b>me (<b>sti</b>ll <b>nam</b>ed <b>i</b>n <b>t</b>he <b>ski</b>ll, <b>tho</b>ugh <b>remo</b>ved <b>fr</b>om <b>t</b>he <b>i</b>n-<b>sco</b>pe <b>serv</b>ice <b>li</b>st <b>i</b>n v1.1).
  - <b>Th</b>en **DMS** <b>mov</b>es <b>t</b>he <b>da</b>ta (<b>fu</b>ll <b>lo</b>ad + CDC).
- <b>Ite</b>ms <b>th</b>at <b>can</b>'t <b>conv</b>ert <b>automat</b>ically <b>a</b>re <b>flag</b>ged <b>i</b>n <b>a</b>n **assessment report** <b>f</b>or <b>man</b>ual <b>wo</b>rk.

### Data lineage (skill 2.4.4)

**Lineage** = <b>whe</b>re <b>da</b>ta <b>ca</b>me <b>fr</b>om, <b>whi</b>ch <b>transfor</b>mations <b>touc</b>hed <b>i</b>t, <b>a</b>nd <b>whe</b>re <b>i</b>t <b>go</b>es. <b>It</b>'s <b>us</b>ed <b>f</b>or <b>imp</b>act <b>anal</b>ysis ("<b>wh</b>at <b>bre</b>aks <b>i</b>f <b>I</b> <b>cha</b>nge <b>th</b>is <b>col</b>umn?"), <b>debug</b>ging, <b>tru</b>st, <b>a</b>nd <b>compl</b>iance.

| <b>To</b>ol | <b>Sco</b>pe |
|---|---|
| **Amazon SageMaker Catalog lineage** | <b>Capt</b>ures <b>line</b>age (<b>OpenLi</b>neage-<b>compa</b>tible) <b>fr</b>om <b>sour</b>ces <b>li</b>ke <b>Gl</b>ue, <b>Reds</b>hift, <b>a</b>nd EMR, <b>a</b>nd <b>visua</b>lizes <b>i</b>t <b>o</b>n <b>cata</b>log <b>ass</b>ets |
| **SageMaker ML Lineage Tracking** | ML <b>work</b>flow <b>line</b>age: <b>data</b>sets → <b>proce</b>ssing <b>jo</b>bs → <b>trai</b>ning <b>jo</b>bs → <b>mod</b>els → <b>endpo</b>ints |
| **Amazon Neptune** | <b>Bui</b>ld <b>cus</b>tom <b>line</b>age <b>gra</b>phs (<b>gra</b>ph <b>da</b>ta <b>struc</b>ture) |
| **Glue job metadata / CloudTrail** | <b>R</b>aw <b>evid</b>ence <b>o</b>f <b>wh</b>at <b>r</b>an <b>a</b>nd <b>wh</b>en |

### Indexing, partitioning, compression, optimization (skill 2.4.5)

**Partitioning (S3/Athena/Glue):**
- <b>Parti</b>tion <b>b</b>y <b>colu</b>mns <b>us</b>ed <b>i</b>n `WHERE` <b>filt</b>ers, <b>usua</b>lly **date/time** (`year=/month=/day=`) <b>a</b>nd <b>may</b>be <b>a</b> <b>l</b>ow-<b>cardin</b>ality <b>dimen</b>sion (<b>reg</b>ion).
- **Avoid over-partitioning**: <b>t</b>oo <b>ma</b>ny <b>ti</b>ny <b>parti</b>tions → <b>ma</b>ny <b>sma</b>ll <b>fil</b>es <b>a</b>nd <b>sl</b>ow <b>plan</b>ning. <b>A</b>im <b>f</b>or <b>parti</b>tions <b>o</b>f <b>hund</b>reds <b>o</b>f MB+.
- **Never** <b>parti</b>tion <b>o</b>n <b>hi</b>gh-<b>cardin</b>ality <b>colu</b>mns <b>li</b>ke `user_id`. <b>U</b>se **bucketing** (`bucketed_by`, <b>ha</b>sh <b>in</b>to <b>N</b> <b>fil</b>es) <b>f</b>or <b>tho</b>se <b>inst</b>ead.
- **Partition projection** <b>f</b>or <b>ve</b>ry <b>ma</b>ny <b>parti</b>tions.

**File layout:**
- <b>Tar</b>get **128 MB–1 GB** <b>fil</b>es; <b>comp</b>act <b>sma</b>ll <b>fil</b>es.
- **Columnar** (<b>Parq</b>uet/ORC) + **compression** (<b>Sna</b>ppy/ZSTD) → <b>le</b>ss <b>I</b>/<b>O</b>.
- <b>Sort</b>ing <b>wit</b>hin <b>fil</b>es (<b>o</b>r <b>Iceb</b>erg <b>so</b>rt <b>ord</b>ers) <b>mak</b>es <b>m</b>in/<b>m</b>ax <b>stati</b>stics <b>mo</b>re <b>effec</b>tive <b>a</b>t <b>skip</b>ping <b>r</b>ow <b>gro</b>ups.

**Indexing:**
- **RDS/Aurora**: <b>B</b>-<b>tr</b>ee <b>inde</b>xes <b>o</b>n <b>fil</b>ter/<b>jo</b>in <b>colu</b>mns; <b>avo</b>id <b>ov</b>er-<b>inde</b>xing <b>wri</b>te-<b>hea</b>vy <b>tab</b>les.
- **DynamoDB**: GSIs/<b>Loc</b>al <b>Secon</b>dary <b>Inde</b>xes [LSIs] (<b>inde</b>xes <b>co</b>st <b>ext</b>ra <b>wri</b>tes <b>a</b>nd <b>stor</b>age).
- **Redshift**: <b>n</b>o <b>tradit</b>ional <b>inde</b>xes. **Sort keys + zone maps** <b>pl</b>ay <b>th</b>at <b>ro</b>le.
- **OpenSearch**: <b>inve</b>rted <b>ind</b>ex (<b>te</b>xt) <b>a</b>nd <b>k</b>-NN <b>ind</b>ex (<b>vect</b>ors).

**Compression:** <b>colu</b>mnar <b>cod</b>ecs (<b>Sna</b>ppy <b>f</b>or <b>spe</b>ed, ZSTD/GZIP <b>f</b>or <b>rat</b>io); <b>Reds</b>hift `ENCODE AUTO` / AZ64 / ZSTD.

### 🆕 Vectorization concepts (skill 2.4.6)

**Vectorization** = <b>conve</b>rting <b>cont</b>ent (<b>te</b>xt, <b>ima</b>ges) <b>in</b>to <b>embed</b>dings <b>s</b>o <b>i</b>t <b>c</b>an <b>b</b>e <b>sear</b>ched <b>b</b>y <b>mean</b>ing. <b>It</b>'s <b>t</b>he <b>da</b>ta <b>si</b>de <b>o</b>f **RAG** (<b>retri</b>eval-<b>augme</b>nted <b>gener</b>ation).

**Pipeline (Amazon Bedrock Knowledge Bases does this end to end):**

```
Data source (S3, web crawler, Confluence, SharePoint, Salesforce…)
   └─► Parsing (text, tables; optional advanced parsing for PDFs)
        └─► Chunking (fixed-size, semantic, hierarchical, or no chunking)
             └─► Embedding model (e.g., Amazon Titan Text Embeddings, Cohere Embed)
                  └─► Vector store (OpenSearch Serverless, Aurora PostgreSQL, MemoryDB, Neptune Analytics, Pinecone, MongoDB Atlas, Redis…)
                       └─► Retrieval: Retrieve API (chunks) or RetrieveAndGenerate API (answer + citations)
```

<b>K</b>ey <b>conc</b>epts:
- **Chunk size and overlap**: <b>t</b>oo <b>lar</b>ge → <b>noi</b>sy <b>matc</b>hes <b>a</b>nd <b>mo</b>re <b>tok</b>ens; <b>t</b>oo <b>sma</b>ll → <b>lo</b>st <b>cont</b>ext. <b>Over</b>lap <b>prese</b>rves <b>cont</b>ext <b>acr</b>oss <b>chu</b>nk <b>bound</b>aries.
- **Embedding dimensions**: <b>mo</b>re <b>dimen</b>sions <b>capt</b>ure <b>mo</b>re <b>nua</b>nce <b>b</b>ut <b>co</b>st <b>mo</b>re <b>stor</b>age <b>a</b>nd <b>comp</b>ute. <b>T</b>he **same embedding model** <b>mu</b>st <b>b</b>e <b>us</b>ed <b>f</b>or <b>docum</b>ents <b>a</b>nd <b>quer</b>ies.
- **Metadata filtering**: <b>sto</b>re <b>attri</b>butes (<b>depar</b>tment, <b>da</b>te) <b>wi</b>th <b>vect</b>ors <b>t</b>o <b>fil</b>ter <b>resu</b>lts.
- **Sync**: <b>r</b>e-<b>r</b>un <b>knowl</b>edge <b>ba</b>se <b>inges</b>tion <b>wh</b>en <b>sou</b>rce <b>da</b>ta <b>chan</b>ges (<b>on</b>ly <b>chan</b>ged <b>docum</b>ents <b>a</b>re <b>r</b>e-<b>embe</b>dded).
- **Hybrid search**: <b>comb</b>ine <b>keyw</b>ord (<b>Be</b>st <b>Matc</b>hing 25 [BM25]) <b>a</b>nd <b>vec</b>tor <b>simil</b>arity <b>f</b>or <b>bet</b>ter <b>relev</b>ance (<b>suppo</b>rted <b>wi</b>th <b>OpenS</b>earch).

---

## Gotchas and exam traps

- **"Microsecond latency for DynamoDB reads"** → **DAX**. **"Durable in-memory primary database"** → **MemoryDB**, <b>n</b>ot <b>Elasti</b>Cache.
- **"Vectors with relational data, SQL"** → **Aurora PostgreSQL + pgvector (HNSW)**. **"Full-text + vector hybrid search"** → **OpenSearch**.
- **HNSW** = <b>gra</b>ph, <b>hi</b>gh <b>rec</b>all, <b>hi</b>gh <b>mem</b>ory. **IVF** = <b>clus</b>ters, <b>le</b>ss <b>mem</b>ory, <b>nee</b>ds <b>trai</b>ning.
- **"Updates/deletes/time travel on S3 data"** → **Iceberg**. **"…with automatic compaction and no maintenance"** → **S3 Tables**.
- <b>Ma</b>ny <b>sma</b>ll <b>Iceb</b>erg <b>fil</b>es → **compaction** (`OPTIMIZE`), <b>o</b>ld <b>snaps</b>hots <b>bloa</b>ting <b>stor</b>age → **expire snapshots** (`VACUUM`).
- **Query S3 from Redshift without loading** → **Spectrum**. **Live Aurora/RDS data from Redshift** → **federated query**.
- **Share Redshift data across accounts without copying** → **data sharing** (RA3/<b>Serve</b>rless).
- **DDL blocked or blocking reads in Redshift** → `AccessExclusiveLock`; <b>fi</b>nd <b>wi</b>th `STV_LOCKS`, <b>e</b>nd <b>wi</b>th `PG_TERMINATE_BACKEND`.
- **KEY distribution on a low-cardinality column** → <b>sk</b>ew. <b>U</b>se `AUTO`/`EVEN` <b>o</b>r <b>a</b> <b>bet</b>ter <b>k</b>ey.
- **Small dimension table** → `DISTSTYLE ALL`.
- **COPY slow** → <b>o</b>ne <b>b</b>ig <b>fi</b>le. <b>Spl</b>it <b>in</b>to <b>mult</b>iple <b>fil</b>es (<b>mult</b>iple <b>o</b>f <b>sli</b>ces), <b>comp</b>ress.
- **Athena doesn't see new partitions** → `MSCK REPAIR TABLE` / `ADD PARTITION` / **partition projection** / <b>craw</b>ler.
- **Thousands of partitions, slow Athena planning** → **partition projection** (<b>o</b>r <b>parti</b>tion <b>inde</b>xes).
- **Crawler created hundreds of tables** → <b>ena</b>ble "<b>sin</b>gle <b>sch</b>ema <b>p</b>er S3 <b>pa</b>th" / <b>f</b>ix <b>fol</b>der <b>lay</b>out.
- **Unknown access pattern, minimize cost** → **Intelligent-Tiering**.
- **Lifecycle to Standard-IA** <b>nee</b>ds **30 days** <b>i</b>n <b>Stan</b>dard <b>fir</b>st.
- **Delete in a versioned bucket** <b>on</b>ly <b>ad</b>ds <b>a</b> <b>del</b>ete <b>mar</b>ker.
- **WORM, nobody can delete, not even root** → **Object Lock compliance mode**.
- **DynamoDB TTL** <b>isn</b>'t <b>immed</b>iate <b>a</b>nd <b>does</b>n't <b>cons</b>ume <b>Wri</b>te <b>Capa</b>city <b>Uni</b>ts (WCUs). <b>Expi</b>red <b>ite</b>ms <b>fl</b>ow <b>t</b>o <b>Stre</b>ams.
- **LSI** <b>c</b>an <b>on</b>ly <b>b</b>e <b>crea</b>ted **at table creation**.
- **Producers changing Avro/JSON schemas break consumers** → **Glue Schema Registry** <b>wi</b>th <b>compati</b>bility <b>mo</b>de.
- **Heterogeneous DB migration** → **DMS Schema Conversion / SCT**, <b>th</b>en DMS.
- **"What does this table mean, who owns it, request access"** → **SageMaker Catalog** (<b>busi</b>ness <b>cata</b>log), <b>n</b>ot <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log.
- **Partition on `user_id`** → <b>wro</b>ng; <b>parti</b>tion <b>o</b>n <b>da</b>te, **bucket** <b>o</b>n <b>hi</b>gh-<b>cardin</b>ality <b>colu</b>mns.

---

## Quick-recall summary

- <b>Dom</b>ain <b>wei</b>ght **26%**. <b>Tas</b>ks: <b>cho</b>ose <b>sto</b>re (2.1), <b>cata</b>logs (2.2), <b>lifec</b>ycle (2.3), <b>mode</b>ling <b>a</b>nd <b>evolu</b>tion (2.4).
- **S3** <b>f</b>or <b>t</b>he <b>la</b>ke; <b>stor</b>age <b>clas</b>ses <b>b</b>y <b>acc</b>ess <b>frequ</b>ency; 3,500 <b>wri</b>tes / 5,500 <b>rea</b>ds <b>p</b>er <b>sec</b>ond **per prefix**.
- **Redshift**: <b>lea</b>der + <b>comp</b>ute <b>sli</b>ces; RA3 / <b>Serve</b>rless; <b>di</b>st <b>sty</b>les **AUTO/KEY/ALL/EVEN**; <b>comp</b>ound <b>so</b>rt <b>ke</b>ys + <b>zo</b>ne <b>ma</b>ps; COPY <b>i</b>n <b>para</b>llel; <b>Spec</b>trum, <b>feder</b>ated <b>que</b>ry, <b>Materi</b>alized <b>Vie</b>ws (MVs), <b>da</b>ta <b>shar</b>ing, <b>concur</b>rency <b>scal</b>ing, <b>ze</b>ro-ETL.
- **Athena**: <b>serve</b>rless SQL; <b>parti</b>tions, <b>Parq</b>uet, <b>compre</b>ssion, <b>fi</b>le <b>siz</b>ing, **partition projection**; <b>supp</b>orts <b>Iceb</b>erg DML.
- **DynamoDB**: <b>hi</b>gh-<b>cardin</b>ality <b>parti</b>tion <b>k</b>ey; GSI <b>anyt</b>ime / LSI <b>a</b>t <b>crea</b>tion; <b>o</b>n-<b>dem</b>and <b>v</b>s <b>provis</b>ioned; 400 KB <b>ite</b>ms; DAX <b>f</b>or <b>micros</b>econds.
- **MemoryDB** = <b>dura</b>ble <b>i</b>n-<b>mem</b>ory; **ElastiCache** = <b>cac</b>he.
- **Iceberg**: ACID, <b>r</b>ow-<b>lev</b>el DML, <b>sch</b>ema & <b>parti</b>tion <b>evolu</b>tion, <b>hid</b>den <b>partit</b>ioning, <b>ti</b>me <b>tra</b>vel; <b>main</b>tain <b>wi</b>th <b>compa</b>ction + <b>snap</b>shot <b>exp</b>iry; **S3 Tables** = <b>mana</b>ged <b>Iceb</b>erg <b>wi</b>th <b>autom</b>atic <b>mainte</b>nance.
- **Vectors**: <b>embed</b>dings + <b>dist</b>ance (<b>cos</b>ine, L2, <b>d</b>ot); **HNSW** (<b>gra</b>ph, <b>fa</b>st, <b>mem</b>ory-<b>hea</b>vy) <b>v</b>s **IVF** (<b>clus</b>ters, <b>ligh</b>ter, <b>nee</b>ds <b>trai</b>ning); <b>sto</b>res = <b>pgve</b>ctor, <b>OpenS</b>earch, <b>Memo</b>ryDB.
- **Locks**: <b>Reds</b>hift <b>Access</b>Share / <b>ShareRowE</b>xclusive / <b>AccessEx</b>clusive; `STV_LOCKS`; RDS <b>deadl</b>ocks <b>a</b>nd `FOR UPDATE`.
- **Transfer Family** = SFTP <b>in</b>to S3.
- **Glue Data Catalog** = <b>techn</b>ical <b>metas</b>tore (<b>Hi</b>ve <b>compa</b>tible) <b>f</b>or <b>Ath</b>ena/<b>Spec</b>trum/EMR/<b>Gl</b>ue; **crawlers** <b>wi</b>th <b>classi</b>fiers, <b>sch</b>ema <b>cha</b>nge <b>a</b>nd <b>recr</b>awl <b>poli</b>cies.
- <b>Parti</b>tion <b>sy</b>nc: <b>craw</b>ler, `MSCK REPAIR`, `ADD PARTITION`, <b>Gl</b>ue <b>j</b>ob <b>cata</b>log <b>upd</b>ate, **partition projection**.
- **SageMaker Catalog** = <b>busi</b>ness <b>cata</b>log: <b>glos</b>sary, <b>meta</b>data <b>for</b>ms, <b>publ</b>ish/<b>subsc</b>ribe <b>wi</b>th <b>appr</b>oval, AI <b>descri</b>ptions, <b>line</b>age.
- **COPY/UNLOAD**: <b>mult</b>iple <b>compr</b>essed <b>fil</b>es, IAM <b>ro</b>le, <b>mani</b>fest, <b>stag</b>ing + MERGE <b>f</b>or <b>upse</b>rts, UNLOAD <b>t</b>o <b>Parq</b>uet.
- **S3 Lifecycle**: <b>transi</b>tions, <b>expira</b>tions, <b>noncu</b>rrent <b>vers</b>ions, <b>abo</b>rt <b>multi</b>part; 30-<b>d</b>ay IA <b>ru</b>le; <b>mini</b>mum <b>durat</b>ions.
- **Versioning**: <b>del</b>ete <b>mark</b>ers; <b>susp</b>end <b>n</b>ot <b>disa</b>ble; <b>nee</b>ded <b>f</b>or <b>replic</b>ation <b>a</b>nd <b>Obj</b>ect <b>Lo</b>ck.
- **TTL**: <b>epo</b>ch <b>seco</b>nds, <b>fr</b>ee, <b>dela</b>yed <b>dele</b>tes, <b>sho</b>ws <b>i</b>n <b>Stre</b>ams.
- **Legal**: <b>Iceb</b>erg <b>dele</b>tes <b>f</b>or GDPR; **Object Lock** <b>compl</b>iance/<b>gover</b>nance/<b>leg</b>al <b>ho</b>ld <b>f</b>or <b>reten</b>tion.
- **Resiliency**: S3 <b>replic</b>ation (+<b>Replic</b>ation <b>Ti</b>me <b>Cont</b>rol [RTC]), <b>Dyna</b>moDB PITR/<b>glo</b>bal <b>tab</b>les, <b>Reds</b>hift <b>snaps</b>hots + <b>cro</b>ss-<b>Reg</b>ion <b>co</b>py + <b>Mul</b>ti-AZ, RDS <b>Mul</b>ti-AZ/<b>repl</b>icas, <b>Aur</b>ora <b>Glo</b>bal <b>Data</b>base, AWS <b>Bac</b>kup.
- **Modeling**: [<b>st</b>ar <b>sch</b>ema](00-data-basics-for-beginners.md#star-schema-fact-and-dimension-tables), SCD <b>typ</b>es 1/2/3; <b>Dyna</b>moDB <b>acc</b>ess-<b>patt</b>ern-<b>fir</b>st <b>a</b>nd <b>sin</b>gle-<b>tab</b>le <b>des</b>ign; <b>la</b>ke <b>zon</b>es <b>r</b>aw/<b>cle</b>an/<b>cura</b>ted.
- **Schema evolution**: <b>craw</b>ler <b>poli</b>cies, **Glue Schema Registry** (BACKWARD <b>defa</b>ult), <b>Iceb</b>erg, `ResolveChoice`, <b>la</b>te-<b>bind</b>ing <b>vie</b>ws.
- **Schema conversion**: DMS <b>Sch</b>ema <b>Conve</b>rsion / SCT → DMS <b>da</b>ta <b>mo</b>ve.
- **Lineage**: <b>SageM</b>aker <b>Cata</b>log (<b>da</b>ta), <b>SageM</b>aker ML <b>Line</b>age <b>Trac</b>king (ML).
- **Optimization**: <b>parti</b>tion <b>b</b>y <b>fil</b>ter <b>colu</b>mns (<b>da</b>te), <b>buc</b>ket <b>hi</b>gh-<b>cardin</b>ality, 128 MB–1 GB <b>fil</b>es, <b>colu</b>mnar + <b>compre</b>ssion, <b>inde</b>xes/<b>so</b>rt <b>ke</b>ys.
- **Vectorization/RAG**: <b>par</b>se → <b>chu</b>nk → <b>emb</b>ed → <b>sto</b>re → <b>retr</b>ieve; <b>Bedr</b>ock <b>Knowl</b>edge <b>Bas</b>es <b>autom</b>ates <b>i</b>t.
