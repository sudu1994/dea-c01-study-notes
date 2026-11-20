# Domain 3: Data Operations and Support (22%)

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> **About 11 of the 50 scored questions.**
>
> <b>Th</b>is <b>dom</b>ain <b>i</b>s <b>abo</b>ut <b>runn</b>ing <b>pipel</b>ines <b>i</b>n <b>produ</b>ction: <b>autom</b>ating <b>proce</b>ssing <b>wi</b>th <b>Ama</b>zon <b>W</b>eb <b>Serv</b>ices (AWS) <b>serv</b>ices <b>a</b>nd <b>Soft</b>ware <b>Develo</b>pment <b>Ki</b>ts (SDKs), <b>analy</b>zing <b>da</b>ta <b>wi</b>th [<b>Struc</b>tured <b>Que</b>ry <b>Lang</b>uage [SQL]](00-data-basics-for-beginners.md#sql) <b>a</b>nd <b>visuali</b>zation <b>too</b>ls, <b>monit</b>oring/<b>logg</b>ing/<b>troubles</b>hooting <b>pipel</b>ines, <b>a</b>nd <b>mak</b>ing <b>su</b>re <b>t</b>he <b>da</b>ta <b>i</b>s <b>corr</b>ect (<b>da</b>ta <b>qual</b>ity, <b>consis</b>tency, <b>samp</b>ling, <b>sk</b>ew).

## Table of contents

- [<b>Ex</b>am <b>tas</b>ks <b>a</b>nd <b>ski</b>lls](#exam-tasks-and-skills)
- [<b>Ta</b>sk 3.1: <b>Auto</b>mate <b>da</b>ta <b>proce</b>ssing <b>b</b>y <b>usi</b>ng AWS <b>serv</b>ices](#task-31-automate-data-processing-by-using-aws-services)
- [<b>Ta</b>sk 3.2: <b>Anal</b>yze <b>da</b>ta <b>b</b>y <b>usi</b>ng AWS <b>serv</b>ices](#task-32-analyze-data-by-using-aws-services)
- [<b>Ta</b>sk 3.3: <b>Main</b>tain <b>a</b>nd <b>moni</b>tor <b>da</b>ta <b>pipel</b>ines](#task-33-maintain-and-monitor-data-pipelines)
- [<b>Ta</b>sk 3.4: <b>Ens</b>ure <b>da</b>ta <b>qual</b>ity](#task-34-ensure-data-quality)
- [<b>Gotc</b>has <b>a</b>nd <b>ex</b>am <b>tra</b>ps](#gotchas-and-exam-traps)
- [<b>Qui</b>ck-<b>rec</b>all <b>summ</b>ary](#quick-recall-summary)

## Exam tasks and skills

> <b>Summa</b>rized <b>fr</b>om <b>t</b>he <b>offi</b>cial AWS <b>Certi</b>fied <b>Da</b>ta <b>Engi</b>neer – <b>Assoc</b>iate (DEA-C01) <b>ex</b>am <b>gui</b>de (v1.1). <b>Exa</b>ct <b>word</b>ing: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain3.html

### Task 3.1: Automate data processing by using AWS services
- **3.1.1** <b>Orches</b>trate <b>pipel</b>ines ([<b>Mana</b>ged <b>Workf</b>lows <b>f</b>or <b>Apa</b>che <b>Airf</b>low [MWAA]](00-data-basics-for-beginners.md#amazon-mwaa), [<b>St</b>ep <b>Funct</b>ions](00-data-basics-for-beginners.md#aws-step-functions)).
- **3.1.2** <b>Troubl</b>eshoot <b>Ama</b>zon <b>mana</b>ged <b>workf</b>lows.
- **3.1.3** <b>Ca</b>ll SDKs <b>t</b>o <b>u</b>se AWS <b>feat</b>ures <b>fr</b>om <b>co</b>de.
- **3.1.4** <b>U</b>se <b>serv</b>ice <b>feat</b>ures <b>t</b>o <b>proc</b>ess <b>da</b>ta ([<b>Elas</b>tic <b>MapRe</b>duce [EMR]](00-data-basics-for-beginners.md#amazon-emr), [<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift), [<b>Gl</b>ue](00-data-basics-for-beginners.md#aws-glue)).
- **3.1.5** <b>Cons</b>ume <b>a</b>nd <b>main</b>tain <b>da</b>ta [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>faces [APIs]](00-data-basics-for-beginners.md#api).
- **3.1.6** <b>Prep</b>are <b>da</b>ta <b>f</b>or <b>transfo</b>rmation ([<b>Gl</b>ue <b>Data</b>Brew](00-data-basics-for-beginners.md#aws-glue-databrew), 🆕 [<b>SageM</b>aker <b>Unif</b>ied <b>Stu</b>dio](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)).
- **3.1.7** <b>Que</b>ry <b>da</b>ta ([<b>Ath</b>ena](00-data-basics-for-beginners.md#amazon-athena)).
- **3.1.8** <b>Auto</b>mate <b>proce</b>ssing <b>wi</b>th [<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda).
- **3.1.9** <b>Man</b>age <b>eve</b>nts <b>a</b>nd <b>sched</b>ulers ([<b>EventB</b>ridge](00-data-basics-for-beginners.md#amazon-eventbridge)).

### Task 3.2: Analyze data by using AWS services
- **3.2.1** <b>Visua</b>lize <b>da</b>ta (<b>Data</b>Brew, [<b>Quick</b>Sight](00-data-basics-for-beginners.md#amazon-quicksight)).
- **3.2.2** <b>Ver</b>ify <b>a</b>nd <b>cle</b>an <b>da</b>ta (<b>Lam</b>bda, <b>Ath</b>ena, <b>Quick</b>Sight, [<b>Jupy</b>ter](00-data-basics-for-beginners.md#jupyter), <b>SageM</b>aker <b>Da</b>ta <b>Wran</b>gler).
- **3.2.3** <b>U</b>se SQL <b>i</b>n **Redshift and Athena** <b>t</b>o <b>que</b>ry <b>a</b>nd <b>cre</b>ate <b>vie</b>ws.
- **3.2.4** <b>Expl</b>ore <b>da</b>ta <b>wi</b>th <b>Ath</b>ena <b>noteb</b>ooks <b>o</b>n [<b>Apa</b>che <b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark).
- **3.2.5** <b>Desc</b>ribe <b>provis</b>ioned <b>v</b>s <b>serve</b>rless <b>tra</b>de-<b>of</b>fs.
- **3.2.6** <b>Def</b>ine <b>aggreg</b>ation, <b>roll</b>ing <b>aver</b>ages, <b>grou</b>ping, <b>pivo</b>ting.

### Task 3.3: Maintain and monitor data pipelines
- **3.3.1** <b>Extr</b>act <b>lo</b>gs <b>f</b>or <b>aud</b>its.
- **3.3.2** <b>Dep</b>loy <b>logg</b>ing/<b>monit</b>oring <b>f</b>or <b>audi</b>ting <b>a</b>nd <b>tracea</b>bility.
- **3.3.3** <b>Se</b>nd <b>ale</b>rts <b>fr</b>om <b>monit</b>oring.
- **3.3.4** <b>Troubl</b>eshoot <b>perfor</b>mance <b>iss</b>ues.
- **3.3.5** <b>Tra</b>ck <b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>face (API) <b>cal</b>ls <b>wi</b>th [<b>Cloud</b>Trail](00-data-basics-for-beginners.md#aws-cloudtrail).
- **3.3.6** <b>Troubl</b>eshoot <b>a</b>nd <b>main</b>tain <b>pipel</b>ines (<b>Gl</b>ue, EMR).
- **3.3.7** <b>L</b>og <b>applic</b>ation <b>da</b>ta <b>wi</b>th [<b>Cloud</b>Watch](00-data-basics-for-beginners.md#amazon-cloudwatch) <b>Lo</b>gs (<b>configu</b>ration <b>a</b>nd <b>autom</b>ation).
- **3.3.8** <b>Anal</b>yze <b>lo</b>gs (<b>Ath</b>ena, EMR, [<b>OpenS</b>earch](00-data-basics-for-beginners.md#amazon-opensearch-service), <b>Cloud</b>Watch <b>Lo</b>gs <b>Insi</b>ghts, <b>b</b>ig <b>da</b>ta <b>a</b>pp <b>lo</b>gs).

### Task 3.4: Ensure data quality
- **3.4.1** <b>R</b>un <b>qual</b>ity <b>che</b>cks <b>dur</b>ing <b>proce</b>ssing (<b>e</b>.g., <b>emp</b>ty <b>fie</b>lds).
- **3.4.2** <b>Def</b>ine <b>da</b>ta <b>qual</b>ity <b>rul</b>es (<b>Data</b>Brew).
- **3.4.3** <b>Invest</b>igate <b>da</b>ta <b>consis</b>tency (<b>Data</b>Brew).
- **3.4.4** <b>Desc</b>ribe <b>da</b>ta <b>samp</b>ling <b>techn</b>iques.
- **3.4.5** <b>Imple</b>ment <b>mecha</b>nisms <b>f</b>or [<b>da</b>ta <b>sk</b>ew](00-data-basics-for-beginners.md#data-skew).

---

## Task 3.1: Automate data processing by using AWS services

### Orchestration in operations (skill 3.1.1)

<b>Dom</b>ain 1 <b>cov</b>ers *<b>choo</b>sing* <b>a</b>n <b>orches</b>trator. <b>He</b>re <b>t</b>he <b>foc</b>us <b>i</b>s *<b>runn</b>ing* <b>th</b>em.

| | <b>St</b>ep <b>Funct</b>ions | <b>Ama</b>zon MWAA |
|---|---|---|
| <b>Defin</b>ition | [<b>JavaS</b>cript <b>Obj</b>ect <b>Nota</b>tion [JSON]](00-data-basics-for-beginners.md#json)/YAML <b>Ain</b>'t <b>Mar</b>kup <b>Lang</b>uage [YAML] (<b>Ama</b>zon <b>Sta</b>tes <b>Lang</b>uage), <b>vis</b>ual <b>Work</b>flow <b>Stu</b>dio | <b>Pyt</b>hon <b>Dire</b>cted <b>Acyc</b>lic <b>Gra</b>ph (DAG) <b>fil</b>es <b>i</b>n [<b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice [S3]](00-data-basics-for-beginners.md#amazon-s3) |
| <b>Wait</b>ing <b>f</b>or <b>jo</b>bs | `.sync` <b>integr</b>ation (<b>e</b>.g., `glue:startJobRun.sync`) | <b>Opera</b>tors/<b>sens</b>ors (<b>GlueJobO</b>perator, S3KeySensor) |
| <b>Err</b>or <b>hand</b>ling | `Retry` (<b>inte</b>rval, <b>back</b>off <b>ra</b>te, <b>m</b>ax <b>atte</b>mpts) <b>a</b>nd `Catch` <b>p</b>er <b>sta</b>te | <b>Ta</b>sk `retries`, `retry_delay`, `on_failure_callback` |
| <b>Scal</b>ing | <b>Autom</b>atic | <b>Enviro</b>nment <b>cla</b>ss + <b>m</b>in/<b>m</b>ax <b>work</b>ers (<b>au</b>to <b>sca</b>les <b>work</b>ers) |
| <b>Pric</b>ing | <b>P</b>er <b>sta</b>te <b>trans</b>ition (<b>Stan</b>dard) <b>o</b>r <b>p</b>er <b>requ</b>est/<b>dura</b>tion (<b>Expr</b>ess) | <b>P</b>er <b>enviro</b>nment-<b>ho</b>ur + <b>work</b>ers |
| <b>Pi</b>ck <b>f</b>or | AWS-<b>nat</b>ive, <b>serve</b>rless, <b>l</b>ow <b>o</b>ps | <b>Exis</b>ting [<b>Airf</b>low](00-data-basics-for-beginners.md#apache-airflow) <b>co</b>de, <b>comp</b>lex <b>depend</b>encies, <b>op</b>en-<b>sou</b>rce <b>opera</b>tors |

### Troubleshooting managed workflows (skill 3.1.2)

**Step Functions:**
- **Execution history** <b>i</b>n <b>t</b>he <b>cons</b>ole <b>sho</b>ws <b>eve</b>ry <b>stat</b>e's <b>inp</b>ut, <b>out</b>put, <b>a</b>nd <b>err</b>or (<b>e</b>.g., `States.TaskFailed`, `States.Timeout`, `States.Permissions`).
- <b>Ena</b>ble **CloudWatch Logs** <b>f</b>or <b>t</b>he <b>sta</b>te <b>mach</b>ine (`ALL`, `ERROR`, <b>o</b>r `FATAL`). **Express workflows only keep history in CloudWatch Logs**, <b>s</b>o <b>y</b>ou <b>mu</b>st <b>ena</b>ble <b>logg</b>ing <b>t</b>o <b>deb</b>ug <b>th</b>em.
- **X-Ray** <b>trac</b>ing <b>sho</b>ws <b>late</b>ncy <b>acr</b>oss <b>serv</b>ices.
- <b>Com</b>mon <b>fix</b>es: <b>miss</b>ing [<b>Iden</b>tity <b>a</b>nd <b>Acc</b>ess <b>Manag</b>ement [IAM]](00-data-basics-for-beginners.md#aws-iam) <b>permis</b>sions <b>o</b>n <b>t</b>he <b>sta</b>te <b>mach</b>ine <b>ro</b>le, `TimeoutSeconds`/`HeartbeatSeconds` <b>t</b>oo <b>l</b>ow, <b>payl</b>oad <b>ov</b>er <b>t</b>he 256 KB <b>lim</b>it (<b>pa</b>ss S3 <b>refer</b>ences <b>inst</b>ead), <b>n</b>o `Retry` <b>f</b>or <b>trans</b>ient <b>err</b>ors.

**MWAA:**
- <b>Lo</b>gs <b>i</b>n <b>Cloud</b>Watch: **DAG processing, scheduler, web server, worker, task** <b>lo</b>gs. <b>Tu</b>rn <b>o</b>n <b>t</b>he <b>lev</b>els <b>y</b>ou <b>ne</b>ed.
- **DAG doesn't appear** → <b>Pyt</b>hon <b>imp</b>ort <b>err</b>or (<b>che</b>ck DAG <b>proce</b>ssing <b>lo</b>gs), <b>wro</b>ng S3 <b>pa</b>th, <b>o</b>r <b>a</b> `requirements.txt` <b>depen</b>dency <b>th</b>at <b>fai</b>led <b>t</b>o <b>inst</b>all (<b>che</b>ck <b>t</b>he <b>environ</b>ment's <b>requir</b>ements <b>inst</b>all <b>l</b>og).
- **Tasks queued but not running** → <b>t</b>oo <b>f</b>ew <b>work</b>ers / <b>enviro</b>nment <b>cla</b>ss <b>t</b>oo <b>sma</b>ll, <b>o</b>r <b>po</b>ol/<b>concur</b>rency <b>lim</b>its.
- **Can't reach AWS services** → <b>execu</b>tion <b>ro</b>le <b>permis</b>sions, <b>o</b>r <b>a</b> <b>priv</b>ate <b>netw</b>ork <b>wi</b>th <b>n</b>o <b>Netw</b>ork <b>Addr</b>ess <b>Transl</b>ation (NAT)/VPC <b>endpo</b>ints.
- <b>Upd</b>ate <b>requir</b>ements/<b>plug</b>ins <b>b</b>y <b>uploa</b>ding <b>n</b>ew <b>vers</b>ions <b>t</b>o S3 <b>a</b>nd <b>upda</b>ting <b>t</b>he <b>enviro</b>nment.

### Calling SDKs (skill 3.1.3)

- **AWS SDKs** (boto3 <b>f</b>or <b>Pyt</b>hon, SDKs <b>f</b>or <b>Ja</b>va, <b>JavaS</b>cript, <b>G</b>o…) <b>ca</b>ll AWS APIs <b>fr</b>om <b>co</b>de (<b>Lam</b>bda, <b>Gl</b>ue, <b>conta</b>iners, <b>noteb</b>ooks).
- **Credentials** <b>co</b>me <b>fr</b>om <b>t</b>he **IAM role** <b>o</b>f <b>t</b>he <b>comp</b>ute (<b>Lam</b>bda <b>execu</b>tion <b>ro</b>le, <b>Gl</b>ue <b>j</b>ob <b>ro</b>le, <b>Elas</b>tic <b>Comp</b>ute <b>Clo</b>ud [EC2] <b>inst</b>ance <b>prof</b>ile). <b>Nev</b>er <b>hard</b>code <b>ke</b>ys.
- **Paginators** <b>f</b>or <b>li</b>st <b>opera</b>tions <b>th</b>at <b>ret</b>urn <b>pag</b>es (`list_objects_v2`, `get_query_results`).
- **Waiters** <b>t</b>o <b>wa</b>it <b>f</b>or <b>a</b> <b>sta</b>te (<b>e</b>.g., <b>wa</b>it <b>unt</b>il <b>a</b> <b>Reds</b>hift <b>clus</b>ter <b>i</b>s <b>avail</b>able).
- **Retries**: SDKs <b>ret</b>ry <b>throt</b>tling <b>err</b>ors <b>automat</b>ically. <b>Confi</b>gure `standard` <b>o</b>r `adaptive` <b>ret</b>ry <b>mo</b>de <b>a</b>nd <b>m</b>ax <b>atte</b>mpts.
- **Asynchronous APIs** <b>y</b>ou <b>mu</b>st <b>po</b>ll: <b>Ath</b>ena (`start_query_execution` → `get_query_execution` → `get_query_results`), **Redshift Data API** (`execute_statement` → `describe_statement` → `get_statement_result`), <b>Gl</b>ue (`start_job_run` → `get_job_run`).

### Using service features to process data (skill 3.1.4)

| <b>Serv</b>ice | <b>Proce</b>ssing <b>feat</b>ures <b>wor</b>th <b>know</b>ing |
|---|---|
| **Glue** | <b>Bui</b>lt-<b>i</b>n <b>trans</b>forms (<b>ApplyM</b>apping, <b>Fil</b>ter, <b>Jo</b>in, <b>DropNul</b>lFields, <b>Relatio</b>nalize), **FindMatches Machine Learning (ML) transform** (<b>fuz</b>zy <b>dedupli</b>cation/<b>rec</b>ord <b>matc</b>hing <b>with</b>out <b>exa</b>ct <b>ke</b>ys), <b>sensi</b>tive <b>da</b>ta <b>detec</b>tion, <b>Da</b>ta <b>Qual</b>ity, <b>j</b>ob <b>bookm</b>arks |
| **EMR** | **Steps** (<b>sub</b>mit <b>Spa</b>rk/<b>Hi</b>ve <b>jo</b>bs <b>t</b>o <b>a</b> <b>clus</b>ter), <b>boots</b>trap <b>acti</b>ons, EMR <b>Serve</b>rless <b>applic</b>ations, EMR <b>Stu</b>dio <b>noteb</b>ooks |
| **Redshift** | <b>Sto</b>red <b>proce</b>dures, <b>materi</b>alized <b>vie</b>ws, `MERGE`, <b>sched</b>uled <b>quer</b>ies, <b>Reds</b>hift ML (`CREATE MODEL`), <b>strea</b>ming <b>inges</b>tion, <b>us</b>er-<b>defi</b>ned <b>funct</b>ions (SQL/<b>Lam</b>bda) |

### Consuming and maintaining data APIs (skill 3.1.5)

<b>Mainta</b>ining <b>da</b>ta APIs <b>mea</b>ns <b>opera</b>ting <b>th</b>em, <b>n</b>ot <b>ju</b>st <b>crea</b>ting <b>th</b>em:
- **Versioning** (`/v1/`, `/v2/` <b>pat</b>hs <b>o</b>r API <b>Gate</b>way <b>sta</b>ges) <b>s</b>o <b>chan</b>ges <b>don</b>'t <b>bre</b>ak <b>consu</b>mers.
- **Throttling and quotas** (API <b>Gate</b>way <b>usa</b>ge <b>pla</b>ns <b>a</b>nd API <b>ke</b>ys).
- **Caching** (API <b>Gate</b>way <b>cac</b>he) <b>f</b>or <b>repe</b>ated <b>quer</b>ies.
- **Monitoring**: API <b>Gate</b>way <b>Cloud</b>Watch <b>metr</b>ics (`4XXError`, `5XXError`, `Latency`, `Count`), <b>acc</b>ess <b>lo</b>gs, <b>X</b>-<b>R</b>ay.
- **Security**: IAM, <b>Cogn</b>ito, <b>o</b>r <b>Lam</b>bda <b>author</b>izers.
- **Pagination** <b>a</b>nd <b>consi</b>stent <b>resp</b>onse <b>form</b>ats.

### Preparing data for transformation (skill 3.1.6)

**AWS Glue DataBrew** (<b>n</b>o-<b>co</b>de <b>da</b>ta <b>pr</b>ep):
- **Datasets** (S3, <b>Gl</b>ue <b>Cata</b>log, <b>Reds</b>hift, [<b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice [RDS]](00-data-basics-for-beginners.md#amazon-rds), [<b>Snowf</b>lake](00-data-basics-for-beginners.md#snowflake-splunk-and-salesforce)…) → **projects** (<b>intera</b>ctive <b>sess</b>ion <b>o</b>n <b>a</b> <b>sam</b>ple) → **recipes** (<b>sav</b>ed <b>li</b>st <b>o</b>f <b>trans</b>form <b>ste</b>ps) → **recipe jobs** (<b>r</b>un <b>t</b>he <b>rec</b>ipe <b>o</b>n <b>t</b>he <b>fu</b>ll <b>data</b>set, <b>out</b>put <b>t</b>o S3) <b>a</b>nd **profile jobs** (<b>stati</b>stics <b>a</b>nd <b>qual</b>ity).
- 250+ <b>trans</b>forms: <b>rem</b>ove <b>dupli</b>cates, <b>fi</b>ll/<b>fl</b>ag <b>miss</b>ing <b>val</b>ues, <b>spl</b>it/<b>mer</b>ge <b>colu</b>mns, <b>standa</b>rdize <b>form</b>ats, <b>piv</b>ot/<b>unpi</b>vot, <b>ma</b>sk/<b>red</b>act/<b>encr</b>ypt <b>Perso</b>nally <b>Identi</b>fiable <b>Inform</b>ation (PII), <b>jo</b>in <b>data</b>sets.
- <b>Be</b>st <b>f</b>or **analysts or data stewards who don't write code**.

🆕 **Amazon SageMaker Unified Studio**:
- <b>A</b> **single web environment** <b>f</b>or <b>da</b>ta <b>a</b>nd <b>Artif</b>icial <b>Intell</b>igence (AI) <b>wo</b>rk: SQL <b>que</b>ry <b>edi</b>tor (<b>Ath</b>ena <b>a</b>nd <b>Reds</b>hift), <b>Jupy</b>ter <b>noteb</b>ooks (<b>Spa</b>rk, <b>Pyt</b>hon), **visual Extract, Transform, Load [ETL]** (<b>Gl</b>ue), <b>da</b>ta <b>pr</b>ep, <b>mod</b>el <b>buil</b>ding, <b>gener</b>ative AI <b>a</b>pp <b>buil</b>ding <b>wi</b>th [<b>Bedr</b>ock](00-data-basics-for-beginners.md#amazon-bedrock), <b>pl</b>us <b>t</b>he **SageMaker Catalog**.
- <b>Organ</b>ized <b>b</b>y **domains → domain units → projects** (<b>Dom</b>ain 4 <b>cov</b>ers <b>th</b>is). <b>A</b> <b>proj</b>ect <b>giv</b>es <b>a</b> <b>te</b>am <b>sha</b>red <b>da</b>ta, <b>comp</b>ute, <b>a</b>nd <b>permis</b>sions.
- <b>Cho</b>ose <b>i</b>t <b>wh</b>en <b>t</b>he <b>scen</b>ario <b>wan</b>ts **one governed workspace** <b>whe</b>re <b>engin</b>eers, <b>anal</b>ysts, <b>a</b>nd <b>da</b>ta <b>scien</b>tists <b>collab</b>orate <b>o</b>n <b>t</b>he <b>sa</b>me <b>da</b>ta.

### Querying data with Athena (skill 3.1.7)

- <b>Stan</b>dard SQL ([<b>Tri</b>no](00-data-basics-for-beginners.md#presto-and-trino) <b>eng</b>ine) <b>ov</b>er <b>t</b>he <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log; <b>resu</b>lts <b>writ</b>ten <b>t</b>o <b>a</b>n S3 <b>loca</b>tion (<b>s</b>et <b>p</b>er **workgroup**).
- **Workgroups**: <b>sepa</b>rate <b>tea</b>ms/<b>ap</b>ps, <b>enfo</b>rce <b>res</b>ult <b>loca</b>tion <b>a</b>nd <b>encry</b>ption, **per-query and per-workgroup data scan limits**, <b>co</b>st <b>trac</b>king <b>wi</b>th <b>ta</b>gs.
- **Saved queries**, **prepared statements** (<b>paramet</b>erized <b>quer</b>ies; <b>al</b>so <b>he</b>lp <b>prev</b>ent SQL <b>injec</b>tion), **views**.
- **CREATE TABLE AS SELECT (CTAS)** <b>a</b>nd `INSERT INTO` <b>t</b>o <b>cre</b>ate <b>transf</b>ormed <b>a</b>nd <b>partit</b>ioned <b>tab</b>les.
- **Query result reuse** <b>avo</b>ids <b>resca</b>nning <b>f</b>or <b>repe</b>ated <b>ident</b>ical <b>quer</b>ies.
- **Provisioned capacity** (<b>rese</b>rved <b>Da</b>ta <b>Proce</b>ssing <b>Uni</b>ts [DPUs]) <b>f</b>or <b>predic</b>table <b>concur</b>rency <b>inst</b>ead <b>o</b>f <b>p</b>er-TB <b>pric</b>ing.

### Automating with Lambda (skill 3.1.8)

<b>Typi</b>cal <b>autom</b>ation <b>patt</b>erns:
- **S3 object created → Lambda**: <b>vali</b>date <b>t</b>he <b>fi</b>le, <b>conv</b>ert [<b>sma</b>ll <b>fil</b>es](00-data-basics-for-beginners.md#small-files-problem), <b>sta</b>rt <b>a</b> <b>Gl</b>ue <b>j</b>ob / <b>St</b>ep <b>Funct</b>ions <b>execu</b>tion.
- **Scheduled Lambda** (<b>EventB</b>ridge <b>Sched</b>uler): <b>ca</b>ll <b>a</b>n API, <b>r</b>un <b>housek</b>eeping (<b>e</b>.g., <b>refr</b>esh <b>a</b> <b>materi</b>alized <b>vi</b>ew <b>thro</b>ugh <b>t</b>he <b>Reds</b>hift <b>Da</b>ta API).
- **Stream processing**: [KDS](00-data-basics-for-beginners.md#amazon-kinesis-data-streams)/<b>Dyna</b>moDB <b>Stre</b>ams/SQS → <b>Lam</b>bda (<b>s</b>ee <b>t</b>he <b>eve</b>nt <b>sou</b>rce <b>mapp</b>ing <b>sett</b>ings <b>i</b>n <b>Dom</b>ain 1).
- **Glue between steps** <b>ins</b>ide <b>St</b>ep <b>Funct</b>ions.
- <b>Ke</b>ep <b>funct</b>ions <b>sma</b>ll, [<b>idemp</b>otent](00-data-basics-for-beginners.md#idempotent), <b>wi</b>th <b>De</b>ad-<b>Let</b>ter <b>Que</b>ues (DLQs)/<b>o</b>n-<b>fail</b>ure <b>destin</b>ations <b>a</b>nd <b>struc</b>tured <b>logg</b>ing.

### Managing events and schedulers (skill 3.1.9)

**Amazon EventBridge building blocks:**

| <b>Compo</b>nent | <b>Purp</b>ose |
|---|---|
| **Event buses** | <b>Defa</b>ult <b>b</b>us (AWS <b>serv</b>ice <b>eve</b>nts), <b>cus</b>tom <b>bus</b>es (<b>yo</b>ur <b>ap</b>ps), <b>part</b>ner <b>bus</b>es (<b>Soft</b>ware <b>a</b>s <b>a</b> <b>Serv</b>ice [<b>Sa</b>aS]) |
| **Rules** | <b>Mat</b>ch <b>eve</b>nts <b>b</b>y **event pattern** (<b>sou</b>rce, <b>det</b>ail-<b>ty</b>pe, <b>fie</b>lds) → <b>u</b>p <b>t</b>o 5 <b>targ</b>ets <b>p</b>er <b>ru</b>le |
| **Targets** | <b>Lam</b>bda, <b>St</b>ep <b>Funct</b>ions, <b>Gl</b>ue <b>workf</b>lows, <b>Kine</b>sis, [<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice [SQS]](00-data-basics-for-beginners.md#amazon-sqs), [<b>Sim</b>ple <b>Notifi</b>cation <b>Serv</b>ice [SNS]](00-data-basics-for-beginners.md#amazon-sns), [<b>Elas</b>tic <b>Conta</b>iner <b>Serv</b>ice [ECS]](00-data-basics-for-beginners.md#amazon-ecs-eks-and-fargate) <b>tas</b>ks, API <b>destin</b>ations… |
| **Scheduler** | <b>Cr</b>on/<b>ra</b>te/<b>o</b>ne-<b>ti</b>me <b>sched</b>ules <b>a</b>t <b>lar</b>ge <b>sca</b>le, <b>wi</b>th <b>ti</b>me <b>zon</b>es, <b>flex</b>ible <b>wind</b>ows, <b>retr</b>ies, <b>De</b>ad-<b>Let</b>ter <b>Que</b>ue (DLQ) |
| **Archive & replay** | <b>Sto</b>re <b>eve</b>nts <b>a</b>nd <b>rep</b>lay <b>th</b>em <b>lat</b>er |
| **Cross-account** | <b>Se</b>nd <b>eve</b>nts <b>t</b>o <b>a</b> <b>b</b>us <b>i</b>n <b>anot</b>her <b>acco</b>unt (<b>cent</b>ral <b>monit</b>oring) |
| **Input transformer** | <b>Resh</b>ape <b>t</b>he <b>eve</b>nt <b>bef</b>ore <b>send</b>ing <b>i</b>t <b>t</b>o <b>t</b>he <b>tar</b>get |

<b>Da</b>ta-<b>pipe</b>line <b>eve</b>nts <b>you</b>'ll <b>s</b>ee: **Glue Job State Change**, **Glue Crawler State Change**, **[Glue Data Quality](00-data-basics-for-beginners.md#aws-glue-data-quality) evaluation results**, **EMR step status change**, **Step Functions execution status change**, **S3 Object Created**, **Redshift Data API statement status**.

---

## Task 3.2: Analyze data by using AWS services

### Visualizing data (skill 3.2.1)

**Amazon QuickSight:**
- <b>Serve</b>rless <b>Busi</b>ness <b>Intell</b>igence (BI): <b>dashb</b>oards, <b>anal</b>yses, <b>pagin</b>ated <b>repo</b>rts, **embedded dashboards** <b>i</b>n <b>ap</b>ps.
- **Super-fast, Parallel, In-memory Calculation Engine (SPICE)**: <b>i</b>n-<b>mem</b>ory <b>eng</b>ine. <b>Imp</b>ort <b>da</b>ta <b>f</b>or <b>fa</b>st, <b>scal</b>able <b>dashb</b>oards; <b>sche</b>dule <b>fu</b>ll <b>o</b>r **incremental refreshes**. **Direct query** <b>hi</b>ts <b>t</b>he <b>sou</b>rce <b>li</b>ve (<b>alw</b>ays <b>fre</b>sh, <b>slo</b>wer, <b>loa</b>ds <b>t</b>he <b>sou</b>rce).
- <b>Da</b>ta <b>sour</b>ces: <b>Ath</b>ena, <b>Reds</b>hift, RDS/<b>Aur</b>ora, S3, <b>OpenS</b>earch, <b>Snowf</b>lake, <b>Sa</b>aS…
- **Row-level security (RLS)** <b>a</b>nd <b>col</b>umn-<b>lev</b>el <b>secu</b>rity <b>p</b>er <b>us</b>er/<b>gro</b>up.
- **Amazon Q in QuickSight**: <b>a</b>sk <b>quest</b>ions <b>i</b>n <b>natu</b>ral <b>lang</b>uage, <b>bui</b>ld <b>visu</b>als <b>a</b>nd <b>da</b>ta <b>stor</b>ies.
- <b>Licen</b>sing <b>b</b>y <b>auth</b>ors <b>a</b>nd <b>read</b>ers.

**DataBrew visuals:** <b>prof</b>ile <b>resu</b>lts <b>sh</b>ow <b>col</b>umn <b>distrib</b>utions, <b>miss</b>ing <b>val</b>ues, <b>outl</b>iers, <b>correl</b>ations, <b>whi</b>ch <b>i</b>s <b>qui</b>ck <b>vis</b>ual <b>da</b>ta <b>explor</b>ation <b>bef</b>ore <b>transfo</b>rmation.

### Verifying and cleaning data (skill 3.2.2)

| <b>To</b>ol | <b>U</b>se |
|---|---|
| **Athena SQL** | <b>Cou</b>nt <b>nul</b>ls, <b>dupli</b>cates (`GROUP BY … HAVING COUNT(*) > 1`), <b>o</b>ut-<b>o</b>f-<b>ran</b>ge <b>val</b>ues, <b>comp</b>are <b>r</b>ow <b>cou</b>nts |
| **Lambda** | <b>Vali</b>date <b>ea</b>ch <b>inco</b>ming <b>fi</b>le/<b>rec</b>ord (<b>sch</b>ema, <b>requ</b>ired <b>fie</b>lds) <b>a</b>nd <b>quara</b>ntine <b>b</b>ad <b>on</b>es |
| **QuickSight** | <b>Sp</b>ot <b>anoma</b>lies <b>visu</b>ally (<b>spi</b>kes, <b>ga</b>ps) |
| **Jupyter notebooks** (<b>SageM</b>aker, EMR <b>Stu</b>dio, <b>Ath</b>ena <b>Spa</b>rk, <b>Unif</b>ied <b>Stu</b>dio) | <b>Intera</b>ctive <b>explor</b>ation <b>wi</b>th <b>pan</b>das/<b>PySp</b>ark |
| **SageMaker Data Wrangler** (<b>i</b>n <b>SageM</b>aker <b>Can</b>vas) | <b>Vis</b>ual <b>da</b>ta <b>pr</b>ep <b>f</b>or ML: 300+ <b>trans</b>forms, <b>da</b>ta <b>qual</b>ity <b>a</b>nd <b>insi</b>ghts <b>rep</b>ort, <b>exp</b>ort <b>t</b>o <b>pipel</b>ines |
| **DataBrew / Glue Data Quality** | <b>Ru</b>le-<b>bas</b>ed <b>profi</b>ling <b>a</b>nd <b>valid</b>ation (<b>Ta</b>sk 3.4) |

### SQL in Redshift and Athena (skill 3.2.3)

- <b>Bo</b>th <b>a</b>re <b>Amer</b>ican <b>Nati</b>onal <b>Stand</b>ards <b>Insti</b>tute (ANSI) SQL <b>engi</b>nes: <b>joi</b>ns, <b>Com</b>mon <b>Tab</b>le <b>Expres</b>sions (CTEs), <b>win</b>dow <b>funct</b>ions, `CASE`, <b>aggre</b>gate <b>funct</b>ions.
- **Views**: <b>sav</b>ed <b>quer</b>ies, <b>n</b>o <b>sto</b>red <b>da</b>ta, <b>alw</b>ays <b>curr</b>ent.
- **Materialized views**: <b>sto</b>re <b>resu</b>lts <b>f</b>or <b>spe</b>ed (<b>Reds</b>hift; <b>Ath</b>ena <b>does</b>n't <b>ha</b>ve <b>clas</b>sic <b>materi</b>alized <b>vie</b>ws <b>ov</b>er <b>Gl</b>ue <b>tab</b>les, <b>s</b>o <b>u</b>se CTAS <b>f</b>or <b>th</b>at).
- **Redshift late-binding views** (`CREATE VIEW … WITH NO SCHEMA BINDING`): <b>n</b>ot <b>bou</b>nd <b>t</b>o <b>under</b>lying <b>obje</b>cts, <b>s</b>o <b>y</b>ou <b>c</b>an <b>dr</b>op/<b>recr</b>eate <b>tab</b>les <b>with</b>out <b>brea</b>king <b>t</b>he <b>vi</b>ew. **Required for views that reference Spectrum external tables.**
- **Athena views** <b>a</b>re <b>sto</b>red <b>i</b>n <b>t</b>he <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log <b>a</b>nd <b>c</b>an <b>b</b>e <b>quer</b>ied <b>b</b>y <b>oth</b>er <b>Ath</b>ena <b>use</b>rs.
- <b>Kn</b>ow `CREATE TABLE AS` <b>i</b>n <b>bo</b>th, `UNLOAD` <b>i</b>n <b>bo</b>th (<b>Ath</b>ena <b>al</b>so <b>h</b>as `UNLOAD` <b>t</b>o <b>wri</b>te <b>que</b>ry <b>resu</b>lts <b>i</b>n [<b>Parq</b>uet](00-data-basics-for-beginners.md#parquet)/[<b>Optim</b>ized <b>R</b>ow <b>Colu</b>mnar [ORC]](00-data-basics-for-beginners.md#orc)/JSON).

### Athena notebooks with Apache Spark (skill 3.2.4)

- **Amazon Athena for Apache Spark**: <b>intera</b>ctive **Jupyter-compatible notebooks** <b>i</b>n <b>t</b>he <b>Ath</b>ena <b>cons</b>ole; <b>a</b> <b>Spa</b>rk <b>sess</b>ion <b>sta</b>rts <b>i</b>n <b>abo</b>ut <b>a</b> <b>sec</b>ond, <b>wi</b>th <b>n</b>o <b>clus</b>ters <b>t</b>o <b>confi</b>gure.
- <b>Us</b>es <b>a</b> **Spark-enabled workgroup**; <b>bil</b>led <b>b</b>y **Data Processing Unit hour (DPU-hour)** <b>o</b>f <b>sess</b>ion <b>u</b>se.
- <b>U</b>se <b>f</b>or <b>explor</b>atory <b>PySp</b>ark <b>o</b>n <b>la</b>ke <b>da</b>ta (<b>comp</b>lex <b>transfor</b>mations, <b>Pyt</b>hon <b>libra</b>ries) <b>wh</b>en SQL <b>alo</b>ne <b>isn</b>'t <b>eno</b>ugh.

### Provisioned vs serverless trade-offs (skill 3.2.5)

| | <b>Provis</b>ioned (<b>Reds</b>hift RA3 <b>clus</b>ter, EMR <b>o</b>n EC2, [<b>Mana</b>ged <b>Strea</b>ming <b>f</b>or <b>Apa</b>che <b>Kaf</b>ka [MSK]](00-data-basics-for-beginners.md#amazon-msk) <b>provis</b>ioned, [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb) <b>provis</b>ioned, <b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams [KDS] <b>provis</b>ioned) | <b>Serve</b>rless (<b>Reds</b>hift <b>Serve</b>rless, <b>Ath</b>ena, EMR <b>Serve</b>rless, <b>Gl</b>ue, MSK <b>Serve</b>rless, <b>Dyna</b>moDB <b>o</b>n-<b>dem</b>and, KDS <b>o</b>n-<b>dem</b>and, <b>Lam</b>bda) |
|---|---|---|
| <b>Co</b>st <b>mod</b>el | <b>P</b>ay <b>f</b>or <b>capa</b>city <b>whet</b>her <b>us</b>ed <b>o</b>r <b>n</b>ot; **cheaper at steady, high utilization** (<b>a</b>nd <b>wi</b>th <b>reserv</b>ations) | <b>P</b>ay <b>p</b>er <b>u</b>se; **cheaper for spiky, intermittent, unpredictable** <b>workl</b>oads |
| <b>Opera</b>tions | <b>Y</b>ou <b>si</b>ze, <b>sca</b>le, <b>somet</b>imes <b>pat</b>ch | <b>N</b>o <b>capa</b>city <b>plan</b>ning |
| <b>Perfor</b>mance <b>cont</b>rol | <b>Fu</b>ll <b>tun</b>ing (<b>inst</b>ance <b>typ</b>es, <b>conf</b>igs) | <b>Few</b>er <b>kno</b>bs; <b>poss</b>ible <b>co</b>ld <b>sta</b>rts / <b>scal</b>ing <b>ra</b>mp |
| <b>Predict</b>ability | <b>Predic</b>table <b>co</b>st <b>a</b>nd <b>perfor</b>mance | <b>Co</b>st <b>var</b>ies <b>wi</b>th <b>usa</b>ge |

> <b>Ru</b>le: **steady 24/7 load** → <b>provis</b>ioned (+ <b>Rese</b>rved <b>Insta</b>nces/<b>Savi</b>ngs <b>Pla</b>ns). **Unpredictable or occasional load, least ops** → <b>serve</b>rless.

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

| <b>Te</b>rm | <b>Mean</b>ing |
|---|---|
| **Aggregation** | <b>Summar</b>izing <b>ma</b>ny <b>ro</b>ws <b>in</b>to <b>o</b>ne <b>val</b>ue (SUM, AVG, COUNT, MIN, MAX) |
| **Grouping** | <b>Aggreg</b>ating <b>p</b>er <b>cate</b>gory (`GROUP BY`), <b>filte</b>ring <b>gro</b>ups <b>wi</b>th `HAVING` |
| **Rolling average** | <b>Aver</b>age <b>ov</b>er <b>a</b> <b>mov</b>ing <b>win</b>dow <b>o</b>f <b>ro</b>ws/<b>ti</b>me, <b>whi</b>ch <b>smoo</b>ths <b>fluctu</b>ations |
| **Pivoting** | <b>Turn</b>ing <b>r</b>ow <b>val</b>ues <b>in</b>to <b>colu</b>mns (<b>unpi</b>vot <b>do</b>es <b>t</b>he <b>reve</b>rse) |

---

## Task 3.3: Maintain and monitor data pipelines

### Logging and monitoring building blocks (skills 3.3.1, 3.3.2, 3.3.5, 3.3.7)

| <b>Serv</b>ice | <b>Wh</b>at <b>i</b>t <b>reco</b>rds | <b>Ex</b>am <b>u</b>se |
|---|---|---|
| **AWS CloudTrail** | **API calls**: <b>w</b>ho, <b>wh</b>at, <b>wh</b>en, <b>fr</b>om <b>whe</b>re. **Management events** <b>o</b>n <b>b</b>y <b>defa</b>ult (90-<b>d</b>ay <b>eve</b>nt <b>hist</b>ory); **data events** (S3 <b>obj</b>ect-<b>lev</b>el, <b>Lam</b>bda <b>invo</b>kes, <b>Dyna</b>moDB <b>ite</b>ms…) <b>mu</b>st <b>b</b>e <b>enab</b>led <b>a</b>nd <b>co</b>st <b>ext</b>ra | <b>Aud</b>its: "<b>w</b>ho <b>dele</b>ted <b>t</b>he <b>tab</b>le / <b>chan</b>ged <b>t</b>he <b>buc</b>ket <b>pol</b>icy / <b>r</b>an <b>t</b>he <b>Gl</b>ue <b>j</b>ob?" <b>U</b>se **trails** <b>t</b>o S3 <b>f</b>or <b>lo</b>ng-<b>te</b>rm <b>reten</b>tion, <b>a</b>n **organization trail** <b>f</b>or <b>a</b>ll <b>acco</b>unts, **log file integrity validation** <b>t</b>o <b>pro</b>ve <b>lo</b>gs <b>were</b>n't <b>alte</b>red |
| **CloudTrail Lake** | <b>Mana</b>ged <b>eve</b>nt <b>da</b>ta <b>sto</b>re <b>wi</b>th SQL <b>quer</b>ies <b>ov</b>er <b>Cloud</b>Trail (<b>a</b>nd <b>oth</b>er) <b>eve</b>nts, <b>lo</b>ng <b>reten</b>tion | <b>Centra</b>lized <b>aud</b>it <b>quer</b>ies <b>with</b>out <b>buil</b>ding <b>Ath</b>ena <b>tab</b>les |
| **Amazon CloudWatch Logs** | <b>Applic</b>ation <b>a</b>nd <b>serv</b>ice <b>lo</b>gs (<b>Lam</b>bda, <b>Gl</b>ue, EMR, MWAA, <b>St</b>ep <b>Funct</b>ions, API <b>Gate</b>way, [<b>Virt</b>ual <b>Priv</b>ate <b>Clo</b>ud [VPC]](00-data-basics-for-beginners.md#amazon-vpc) <b>Fl</b>ow <b>Lo</b>gs) | <b>Debug</b>ging, <b>met</b>ric <b>filt</b>ers, <b>subscri</b>ptions |
| **Amazon CloudWatch metrics + alarms** | <b>Nume</b>ric <b>ti</b>me <b>ser</b>ies (<b>Gl</b>ue <b>j</b>ob <b>metr</b>ics, KDS <b>Iterat</b>orAge, <b>Reds</b>hift <b>Cent</b>ral <b>Proce</b>ssing <b>Un</b>it [CPU], <b>Dyna</b>moDB <b>throt</b>tles) | <b>Ale</b>rts <b>a</b>nd <b>dashb</b>oards |
| **[AWS Config](00-data-basics-for-beginners.md#aws-config)** | <b>Reso</b>urce <b>configu</b>ration <b>hist</b>ory <b>a</b>nd <b>compl</b>iance | "<b>Wh</b>at <b>chan</b>ged <b>o</b>n <b>th</b>is <b>buc</b>ket/<b>clus</b>ter?" (<b>Dom</b>ain 4) |
| **Redshift audit logging** | **Connection log**, **user log**, **user activity log** (<b>eve</b>ry <b>que</b>ry) <b>t</b>o S3 <b>o</b>r <b>Cloud</b>Watch <b>Lo</b>gs | <b>Data</b>base-<b>lev</b>el <b>aud</b>it |
| **S3 server access logs** | <b>Requ</b>ests <b>t</b>o <b>a</b> <b>buc</b>ket (<b>be</b>st <b>eff</b>ort) | <b>Acc</b>ess <b>anal</b>ysis, <b>chea</b>per <b>th</b>an <b>da</b>ta <b>eve</b>nts <b>f</b>or <b>hi</b>gh <b>vol</b>ume |
| **EMR logs** | <b>St</b>ep, <b>applic</b>ation ([<b>Y</b>et <b>Anot</b>her <b>Reso</b>urce <b>Negot</b>iator [YARN]](00-data-basics-for-beginners.md#yarn), <b>Spa</b>rk) <b>a</b>nd <b>no</b>de <b>lo</b>gs <b>arch</b>ived <b>t</b>o S3 | <b>Debug</b>ging <b>clus</b>ter <b>jo</b>bs |

**CloudWatch Logs configuration and automation (skill 3.3.7):**
- **Log groups** (<b>p</b>er <b>a</b>pp/<b>j</b>ob) <b>a</b>nd **log streams**; <b>s</b>et **retention** <b>p</b>er <b>l</b>og <b>gro</b>up (<b>nev</b>er <b>exp</b>ire <b>b</b>y <b>defa</b>ult, <b>whi</b>ch <b>cos</b>ts <b>mon</b>ey).
- **Metric filters**: <b>tu</b>rn <b>l</b>og <b>patt</b>erns (<b>e</b>.g., `"ERROR"`) <b>in</b>to <b>metr</b>ics → <b>ala</b>rms.
- **Subscription filters**: <b>str</b>eam <b>lo</b>gs <b>i</b>n <b>re</b>al <b>ti</b>me <b>t</b>o <b>Lam</b>bda, **[Firehose](00-data-basics-for-beginners.md#amazon-data-firehose)** (→ S3/<b>OpenS</b>earch), <b>Kine</b>sis, <b>o</b>r <b>OpenS</b>earch.
- **Export** <b>t</b>o S3 <b>f</b>or <b>arch</b>ive <b>a</b>nd <b>Ath</b>ena <b>anal</b>ysis.
- **CloudWatch agent** <b>f</b>or EC2/<b>o</b>n-<b>pr</b>em <b>l</b>og <b>colle</b>ction; <b>embe</b>dded <b>met</b>ric <b>for</b>mat <b>f</b>or <b>cus</b>tom <b>metr</b>ics <b>fr</b>om <b>lo</b>gs.
- **Glue continuous logging** <b>stre</b>ams <b>dri</b>ver/<b>exec</b>utor <b>lo</b>gs <b>i</b>n <b>re</b>al <b>ti</b>me <b>dur</b>ing <b>a</b> <b>r</b>un.
- <b>Encr</b>ypt <b>l</b>og <b>gro</b>ups <b>wi</b>th [<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice [KMS]](00-data-basics-for-beginners.md#aws-kms). <b>Auto</b>mate <b>l</b>og <b>gro</b>up <b>crea</b>tion <b>a</b>nd <b>reten</b>tion <b>wi</b>th <b>Infrast</b>ructure <b>a</b>s <b>Co</b>de (<b>I</b>aC).

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
- **Job run insights**: <b>poi</b>nts <b>t</b>o <b>t</b>he <b>fail</b>ing <b>li</b>ne <b>a</b>nd <b>sugg</b>ests <b>cau</b>ses.
- **Glue metrics / observability metrics** <b>i</b>n <b>Cloud</b>Watch: <b>wor</b>ker <b>utiliz</b>ation, <b>mem</b>ory, <b>shuf</b>fle, <b>sk</b>ew. <b>Lo</b>ok <b>f</b>or <b>id</b>le <b>execu</b>tors (<b>ov</b>er-<b>provis</b>ioned) <b>o</b>r <b>mem</b>ory <b>ne</b>ar <b>lim</b>it.
- **Spark User Interface [UI]** (<b>ena</b>ble <b>eve</b>nt <b>lo</b>gs <b>t</b>o S3): <b>sta</b>ges, <b>tas</b>ks, <b>sk</b>ew (<b>o</b>ne <b>ta</b>sk <b>f</b>ar <b>lon</b>ger <b>th</b>an <b>t</b>he <b>re</b>st), <b>shuf</b>fle <b>spi</b>ll.
- <b>Typi</b>cal <b>fix</b>es: <b>big</b>ger <b>wor</b>ker <b>typ</b>es, <b>Au</b>to <b>Scal</b>ing, <b>repart</b>ition/<b>salt</b>ing, <b>push</b>down <b>predi</b>cates, <b>fi</b>le <b>grou</b>ping, <b>bookm</b>arks, <b>few</b>er <b>Us</b>er-<b>Defi</b>ned <b>Funct</b>ions (UDFs).

**Amazon EMR:**
- <b>Lo</b>gs <b>i</b>n S3 (<b>ena</b>ble <b>a</b>t <b>clus</b>ter <b>crea</b>tion), <b>Spa</b>rk <b>Hist</b>ory <b>Ser</b>ver, YARN <b>Resource</b>Manager UI, <b>Cloud</b>Watch EMR <b>metr</b>ics (`YARNMemoryAvailablePercentage`, `ContainerPending`, `HDFSUtilization`).
- <b>Fix</b>es: <b>mana</b>ged <b>scal</b>ing, <b>mo</b>re/<b>lar</b>ger <b>ta</b>sk <b>nod</b>es, <b>tu</b>ne <b>execu</b>tors/<b>parti</b>tions, <b>mo</b>ve <b>da</b>ta <b>t</b>o S3 <b>t</b>o <b>deco</b>uple.
- <b>Sp</b>ot <b>interru</b>ptions: <b>u</b>se <b>Sp</b>ot <b>on</b>ly <b>f</b>or <b>ta</b>sk <b>nod</b>es; <b>inst</b>ance <b>fle</b>ets <b>wi</b>th <b>divers</b>ified <b>typ</b>es.

**Amazon Redshift:**
- **`EXPLAIN`** <b>pl</b>an: <b>wat</b>ch <b>f</b>or `DS_BCAST_INNER` / `DS_DIST_BOTH` (<b>da</b>ta <b>redistr</b>ibution → <b>po</b>or <b>di</b>st <b>ke</b>ys), <b>nes</b>ted <b>lo</b>op <b>joi</b>ns (<b>miss</b>ing <b>jo</b>in <b>condi</b>tion).
- <b>Sys</b>tem <b>vie</b>ws: `SYS_QUERY_HISTORY`, `STL_ALERT_EVENT_LOG` (<b>miss</b>ing <b>sta</b>ts, <b>nes</b>ted <b>loo</b>ps), `SVL_QUERY_SUMMARY` (<b>di</b>sk-<b>bas</b>ed <b>ste</b>ps = <b>n</b>ot <b>eno</b>ugh <b>mem</b>ory), `SVV_TABLE_INFO` (<b>sk</b>ew, <b>unso</b>rted %, <b>sta</b>ts_off).
- <b>Fix</b>es: <b>bet</b>ter <b>di</b>st/<b>so</b>rt <b>ke</b>ys, `ANALYZE` (<b>sta</b>ts), `VACUUM` (<b>so</b>rt/<b>recl</b>aim), <b>Work</b>load <b>Manag</b>ement (WLM) <b>que</b>ues/<b>prior</b>ities, <b>concur</b>rency <b>scal</b>ing, <b>materi</b>alized <b>vie</b>ws, <b>Advi</b>sor <b>recommen</b>dations.

**Amazon Athena:**
- <b>U</b>se <b>que</b>ry <b>sta</b>ts (<b>da</b>ta <b>scan</b>ned, <b>plan</b>ning <b>v</b>s <b>execu</b>tion <b>ti</b>me) <b>a</b>nd `EXPLAIN ANALYZE`.
- <b>Fix</b>es: <b>parti</b>tions/<b>proje</b>ction, <b>Parq</b>uet + <b>compre</b>ssion, <b>few</b>er <b>a</b>nd <b>lar</b>ger <b>fil</b>es, <b>sel</b>ect <b>on</b>ly <b>nee</b>ded <b>colu</b>mns, <b>p</b>ut <b>t</b>he **larger table on the left side of a JOIN**, <b>avo</b>id <b>hu</b>ge `ORDER BY` <b>with</b>out `LIMIT`, <b>u</b>se <b>approx</b>imate <b>funct</b>ions (`approx_distinct`).

**Kinesis / Lambda:** <b>ris</b>ing `IteratorAge` → <b>consu</b>mers <b>sl</b>ow (<b>incr</b>ease <b>parallel</b>ization <b>fac</b>tor, <b>sha</b>rds, <b>enha</b>nced <b>f</b>an-<b>o</b>ut, <b>bat</b>ch <b>si</b>ze). `ThrottledRecords` → <b>h</b>ot <b>sha</b>rds.

### Analyzing logs (skill 3.3.8)

| <b>To</b>ol | <b>Be</b>st <b>f</b>or |
|---|---|
| **CloudWatch Logs Insights** | <b>Fa</b>st <b>intera</b>ctive <b>quer</b>ies <b>o</b>n <b>Cloud</b>Watch <b>l</b>og <b>gro</b>ups (`fields`, `filter`, `stats`, `sort`); <b>n</b>o <b>set</b>up |
| **Athena** | SQL <b>o</b>n <b>lo</b>gs <b>i</b>n S3 (<b>Cloud</b>Trail, VPC <b>Fl</b>ow <b>Lo</b>gs, <b>Applic</b>ation <b>Lo</b>ad <b>Bala</b>ncer [ALB], S3 <b>acc</b>ess <b>lo</b>gs). <b>U</b>se <b>parti</b>tion <b>proje</b>ction <b>f</b>or <b>da</b>te-<b>partit</b>ioned <b>lo</b>gs. <b>Che</b>ap <b>a</b>t <b>sca</b>le. |
| **Amazon OpenSearch Service** | <b>Ne</b>ar-<b>re</b>al-<b>ti</b>me <b>l</b>og <b>analy</b>tics, <b>fu</b>ll-<b>te</b>xt <b>sea</b>rch, <b>dashb</b>oards (<b>OpenS</b>earch <b>Dashb</b>oards); <b>fe</b>ed <b>v</b>ia <b>Fire</b>hose <b>o</b>r <b>subscr</b>iption <b>filt</b>ers |
| **Amazon EMR** | **Very large volumes** <b>o</b>f <b>lo</b>gs <b>need</b>ing <b>cus</b>tom <b>Spa</b>rk <b>proce</b>ssing |
| **CloudTrail Lake** | SQL <b>ov</b>er <b>Cloud</b>Trail <b>eve</b>nts <b>with</b>out <b>mana</b>ging <b>tab</b>les |

---

## Task 3.4: Ensure data quality

### Data quality dimensions

| <b>Dimen</b>sion | <b>Ques</b>tion | <b>Exam</b>ple <b>che</b>ck |
|---|---|---|
| **Completeness** | <b>I</b>s <b>anyt</b>hing <b>miss</b>ing? | `email` <b>n</b>ot <b>nu</b>ll <b>f</b>or 99% <b>o</b>f <b>ro</b>ws |
| **Accuracy/validity** | <b>D</b>o <b>val</b>ues <b>fol</b>low <b>rul</b>es? | `age` <b>betw</b>een 0 <b>a</b>nd 120; <b>ema</b>il <b>matc</b>hes <b>a</b> <b>reg</b>ex |
| **Consistency** | <b>D</b>o <b>rela</b>ted <b>data</b>sets <b>agr</b>ee? | <b>R</b>ow <b>cou</b>nts <b>sou</b>rce <b>v</b>s <b>tar</b>get; <b>tot</b>als <b>mat</b>ch |
| **Uniqueness** | <b>A</b>re <b>the</b>re <b>dupli</b>cates? | `order_id` <b>i</b>s <b>uni</b>que |
| **Timeliness/freshness** | <b>I</b>s <b>t</b>he <b>da</b>ta <b>rec</b>ent <b>eno</b>ugh? | <b>Lat</b>est <b>parti</b>tion <b>i</b>s <b>le</b>ss <b>th</b>an 1 <b>d</b>ay <b>o</b>ld |
| **Integrity** | <b>D</b>o <b>refer</b>ences <b>reso</b>lve? | <b>Eve</b>ry `order.customer_id` <b>exi</b>sts <b>i</b>n `customers` |

### Quality checks during processing (skills 3.4.1, 3.4.2)

**AWS Glue Data Quality** (<b>bui</b>lt <b>o</b>n <b>t</b>he <b>op</b>en-<b>sou</b>rce **Deequ** <b>libr</b>ary):
- <b>Rul</b>es <b>writ</b>ten <b>i</b>n **DQDL (Data Quality Definition Language)**:

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

- **Rule recommendations**: <b>Gl</b>ue <b>prof</b>iles <b>t</b>he <b>da</b>ta <b>a</b>nd <b>sugg</b>ests <b>rul</b>es.
- <b>T</b>wo <b>pla</b>ces <b>t</b>o <b>r</b>un <b>i</b>t: **on Data Catalog tables** (<b>da</b>ta <b>a</b>t <b>re</b>st, <b>sched</b>uled) <b>o</b>r **inside Glue ETL jobs** <b>wi</b>th <b>t</b>he <b>Eval</b>uate <b>Da</b>ta <b>Qual</b>ity <b>trans</b>form (<b>da</b>ta <b>i</b>n <b>tran</b>sit).
- **Actions**: <b>fa</b>il <b>t</b>he <b>j</b>ob, <b>o</b>r **route bad records** <b>t</b>o <b>a</b> <b>quara</b>ntine <b>loca</b>tion <b>whi</b>le <b>go</b>od <b>reco</b>rds <b>cont</b>inue; <b>publ</b>ish <b>resu</b>lts <b>t</b>o **CloudWatch** <b>a</b>nd **EventBridge**.
- **Anomaly detection**: <b>lea</b>rns <b>nor</b>mal <b>patt</b>erns (<b>e</b>.g., <b>r</b>ow <b>cou</b>nts) <b>a</b>nd <b>fla</b>gs <b>unus</b>ual <b>val</b>ues.

**AWS Glue DataBrew data quality:**
- **Data quality rulesets** <b>atta</b>ched <b>t</b>o <b>a</b> <b>data</b>set (<b>e</b>.g., "<b>n</b>o <b>mo</b>re <b>th</b>an 5% <b>miss</b>ing <b>val</b>ues <b>i</b>n `email`", "`price` > 0", <b>dupli</b>cate <b>r</b>ow <b>che</b>cks).
- <b>Rul</b>es <b>a</b>re <b>evalu</b>ated <b>dur</b>ing **profile jobs**. <b>Resu</b>lts <b>sh</b>ow <b>pa</b>ss/<b>fa</b>il <b>p</b>er <b>ru</b>le; <b>not</b>ify <b>thro</b>ugh <b>EventB</b>ridge.
- <b>Bet</b>ter <b>f</b>or <b>anal</b>ysts <b>a</b>nd <b>n</b>o-<b>co</b>de <b>tea</b>ms. <b>Gl</b>ue <b>Da</b>ta <b>Qual</b>ity <b>i</b>s <b>bet</b>ter <b>f</b>or <b>cod</b>ed <b>pipel</b>ines.

**Other options:** <b>cus</b>tom <b>che</b>cks <b>i</b>n <b>Lam</b>bda <b>o</b>r <b>Spa</b>rk (<b>e</b>.g., `df.filter(col("x").isNull()).count()`), <b>Ath</b>ena <b>valid</b>ation <b>quer</b>ies <b>i</b>n <b>a</b> <b>St</b>ep <b>Funct</b>ions <b>st</b>ep, **[Database Migration Service [DMS]](00-data-basics-for-beginners.md#aws-dms) data validation** <b>f</b>or <b>migra</b>tions.

### Investigating data consistency (skill 3.4.3)

- **DataBrew profile jobs**: <b>p</b>er-<b>col</b>umn <b>stati</b>stics (<b>dist</b>inct <b>val</b>ues, <b>miss</b>ing %, <b>m</b>in/<b>m</b>ax/<b>me</b>an, <b>outl</b>iers, <b>val</b>ue <b>distri</b>bution, <b>correl</b>ations) <b>a</b>nd <b>dupli</b>cate <b>ro</b>ws. <b>Compa</b>ring <b>prof</b>iles <b>betw</b>een <b>ru</b>ns <b>o</b>r <b>sour</b>ces <b>sho</b>ws <b>dri</b>ft <b>a</b>nd <b>inconsis</b>tencies.
- <b>Recon</b>cile **row counts and checksums/aggregates** <b>betw</b>een <b>sou</b>rce <b>a</b>nd <b>tar</b>get <b>aft</b>er <b>ea</b>ch <b>lo</b>ad.
- <b>Che</b>ck **referential integrity** <b>acr</b>oss <b>tab</b>les.
- <b>Lo</b>ok <b>f</b>or **format inconsistencies** (<b>da</b>te <b>form</b>ats, <b>uni</b>ts, <b>cas</b>ing, <b>encod</b>ings) <b>a</b>nd <b>standa</b>rdize <b>th</b>em <b>i</b>n <b>reci</b>pes <b>o</b>r ETL.
- **Glue FindMatches** <b>fin</b>ds <b>dupli</b>cates <b>th</b>at <b>don</b>'t <b>sha</b>re <b>a</b>n <b>exa</b>ct <b>k</b>ey ("<b>J</b>on <b>Smi</b>th" <b>v</b>s "<b>Jo</b>hn <b>Smi</b>th").

### Data sampling techniques (skill 3.4.4)

<b>Samp</b>ling = <b>chec</b>king <b>o</b>r <b>explo</b>ring <b>a</b> <b>sub</b>set <b>inst</b>ead <b>o</b>f <b>a</b>ll <b>da</b>ta (<b>fas</b>ter, <b>chea</b>per).

| <b>Techn</b>ique | <b>H</b>ow | <b>Wh</b>en |
|---|---|---|
| **Simple random** | <b>Eve</b>ry <b>r</b>ow <b>h</b>as <b>equ</b>al <b>cha</b>nce | <b>Gene</b>ral <b>profi</b>ling |
| **Systematic** | <b>Eve</b>ry <b>k</b>-<b>t</b>h <b>r</b>ow | <b>Orde</b>red <b>da</b>ta <b>wi</b>th <b>n</b>o <b>peri</b>odic <b>patt</b>ern |
| **Stratified** | <b>Ran</b>dom <b>sam</b>ple **within each group** <b>propor</b>tional <b>t</b>o <b>i</b>ts <b>si</b>ze | <b>Ke</b>ep <b>represe</b>ntation <b>o</b>f <b>sma</b>ll <b>gro</b>ups (<b>regi</b>ons, <b>clas</b>ses) |
| **Cluster** | <b>Rand</b>omly <b>pi</b>ck <b>who</b>le <b>gro</b>ups (<b>e</b>.g., <b>so</b>me <b>parti</b>tions/<b>fil</b>es) | <b>Da</b>ta <b>natur</b>ally <b>spl</b>it <b>in</b>to <b>parti</b>tions |
| **Reservoir** | <b>Fix</b>ed-<b>si</b>ze <b>ran</b>dom <b>sam</b>ple <b>fr</b>om <b>a</b> <b>str</b>eam <b>o</b>f <b>unkn</b>own <b>len</b>gth | <b>Strea</b>ming <b>da</b>ta |
| **First N rows** | <b>Ta</b>ke <b>t</b>he <b>t</b>op <b>o</b>f <b>t</b>he <b>data</b>set | <b>Qui</b>ck <b>lo</b>ok, <b>n</b>ot <b>represe</b>ntative (<b>Data</b>Brew <b>defa</b>ult <b>sam</b>ple) |

AWS <b>exam</b>ples: <b>Data</b>Brew <b>proj</b>ect <b>sam</b>ple <b>sett</b>ings (<b>fir</b>st <b>N</b>, <b>ran</b>dom <b>N</b>, <b>la</b>st <b>N</b>), <b>Ath</b>ena `TABLESAMPLE BERNOULLI (10)` <b>o</b>r `SYSTEM`, <b>Spa</b>rk `df.sample(fraction=0.1)`, <b>Spa</b>rk `sampleBy` <b>f</b>or <b>strat</b>ified <b>samp</b>ling.

### Handling data skew (skill 3.4.5)

**Skew** = <b>da</b>ta <b>i</b>s <b>unev</b>enly <b>distri</b>buted, <b>s</b>o <b>o</b>ne <b>parti</b>tion/<b>sha</b>rd/<b>sli</b>ce/<b>wor</b>ker <b>do</b>es <b>mo</b>st <b>o</b>f <b>t</b>he <b>wo</b>rk <b>whi</b>le <b>oth</b>ers <b>s</b>it <b>id</b>le.

| <b>Whe</b>re | <b>Symp</b>tom | <b>Mecha</b>nism |
|---|---|---|
| **Spark (Glue/EMR)** | <b>O</b>ne <b>ta</b>sk <b>ru</b>ns <b>mu</b>ch <b>lon</b>ger; <b>exec</b>utor <b>O</b>ut <b>O</b>f <b>Mem</b>ory (OOM) | **Salting** (<b>app</b>end <b>a</b> <b>ran</b>dom <b>num</b>ber <b>t</b>o <b>h</b>ot <b>ke</b>ys, <b>aggre</b>gate <b>twi</b>ce), **repartition** <b>o</b>n <b>a</b> <b>bet</b>ter <b>k</b>ey, **broadcast join** <b>sma</b>ll <b>tab</b>les, **Adaptive Query Execution** <b>sk</b>ew-<b>jo</b>in <b>hand</b>ling (<b>Spa</b>rk 3), <b>fil</b>ter <b>o</b>ut <b>nu</b>ll/<b>defa</b>ult <b>ke</b>ys <b>bef</b>ore <b>joi</b>ns |
| **Redshift** | <b>Sli</b>ces <b>wi</b>th <b>f</b>ar <b>mo</b>re <b>ro</b>ws (`SVV_TABLE_INFO.skew_rows`) | <b>Cho</b>ose <b>a</b> <b>hi</b>gh-<b>cardin</b>ality `DISTKEY`, <b>o</b>r `EVEN`/`AUTO` |
| **Kinesis / DynamoDB** | <b>H</b>ot <b>sha</b>rd/<b>parti</b>tion, <b>throt</b>tling | <b>Hi</b>gh-<b>cardin</b>ality <b>parti</b>tion <b>k</b>ey, <b>ran</b>dom <b>suff</b>ixes (<b>wri</b>te <b>shar</b>ding) |
| **S3 partitions** | <b>O</b>ne <b>parti</b>tion <b>mu</b>ch <b>big</b>ger <b>th</b>an <b>oth</b>ers | <b>Reth</b>ink <b>parti</b>tion <b>colu</b>mns; <b>a</b>dd <b>bucke</b>ting |

---

## Gotchas and exam traps

- **Express Step Functions** <b>ha</b>ve <b>n</b>o <b>execu</b>tion <b>hist</b>ory <b>i</b>n <b>t</b>he <b>cons</b>ole. **Enable CloudWatch Logs** <b>t</b>o <b>deb</b>ug.
- **MWAA DAG not showing** → <b>imp</b>ort <b>err</b>or <b>o</b>r <b>fai</b>led `requirements.txt` <b>inst</b>all. <b>Che</b>ck <b>t</b>he DAG <b>proce</b>ssing/<b>requir</b>ements <b>lo</b>gs.
- **Async APIs**: <b>Ath</b>ena <b>a</b>nd <b>Reds</b>hift <b>Da</b>ta API <b>mu</b>st <b>b</b>e **polled** <b>f</b>or <b>compl</b>etion.
- **Fuzzy deduplication without a common key** → **Glue FindMatches**.
- **No-code data prep for analysts** → **DataBrew**. **One governed workspace for data + AI teams** → **SageMaker Unified Studio**.
- **Limit how much data a team's Athena queries can scan** → **workgroup data usage controls**.
- **Dashboards slow and hammering the database** → <b>Quick</b>Sight **SPICE** <b>wi</b>th <b>sched</b>uled/<b>increm</b>ental <b>refr</b>esh.
- **Restrict dashboard rows per user** → <b>Quick</b>Sight **row-level security**.
- **Redshift view over Spectrum tables** <b>mu</b>st <b>b</b>e <b>a</b> **late-binding view**.
- **Interactive PySpark exploration without clusters** → **Athena for Apache Spark** <b>noteb</b>ooks.
- **Steady 24/7 workload** → <b>provis</b>ioned + <b>reserv</b>ations. **Spiky/occasional** → <b>serve</b>rless.
- **"Who deleted/changed X?"** → **CloudTrail** (S3 <b>obj</b>ect-<b>lev</b>el <b>nee</b>ds **data events**). **"What did the config look like before?"** → **AWS Config**.
- **Query CloudTrail events with SQL, no table setup** → **CloudTrail Lake**. **Logs already in S3** → **Athena**.
- **Quick ad-hoc search in Lambda/Glue logs** → **CloudWatch Logs Insights**.
- **Near-real-time log search + dashboards** → **OpenSearch** (<b>v</b>ia <b>Fire</b>hose <b>o</b>r <b>subscr</b>iption <b>fil</b>ter).
- **Huge log volumes needing custom processing** → **EMR**.
- **Turn "ERROR" log lines into an alert** → **metric filter + alarm + SNS**.
- **Glue job failure notification** → **EventBridge rule (Glue Job State Change) → SNS**.
- **Log groups never expire by default** → <b>s</b>et <b>reten</b>tion.
- **Redshift `DS_BCAST_INNER` / `DS_DIST_BOTH` in EXPLAIN** → <b>b</b>ad <b>distri</b>bution <b>ke</b>ys.
- **Fail the job or quarantine bad rows based on rules in a Glue pipeline** → **Glue Data Quality** (<b>Eval</b>uate <b>Da</b>ta <b>Qual</b>ity <b>trans</b>form).
- **One Spark task takes forever** → <b>sk</b>ew → **salting / broadcast join / Adaptive Query Execution (AQE)**.
- **Representative sample that keeps small groups** → **stratified sampling**.

---

## Quick-recall summary

- <b>Dom</b>ain <b>wei</b>ght **22%**. <b>Tas</b>ks: <b>auto</b>mate (3.1), <b>anal</b>yze (3.2), <b>main</b>tain/<b>moni</b>tor (3.3), <b>da</b>ta <b>qual</b>ity (3.4).
- <b>St</b>ep <b>Funct</b>ions: `.sync`, <b>Ret</b>ry/<b>Cat</b>ch, <b>execu</b>tion <b>hist</b>ory, **CloudWatch Logs required for Express**, <b>X</b>-<b>R</b>ay. MWAA: <b>Dire</b>cted <b>Acyc</b>lic <b>Gra</b>phs (DAGs) + <b>requir</b>ements <b>i</b>n S3, <b>Cloud</b>Watch <b>lo</b>gs <b>p</b>er <b>compo</b>nent, <b>wor</b>ker <b>scal</b>ing.
- SDKs: <b>ro</b>le-<b>bas</b>ed <b>creden</b>tials, <b>pagin</b>ators, <b>wait</b>ers, <b>ret</b>ry <b>mod</b>es; **poll** <b>Ath</b>ena/<b>Reds</b>hift <b>Da</b>ta API/<b>Gl</b>ue <b>ru</b>ns.
- <b>Serv</b>ice <b>feat</b>ures: <b>Gl</b>ue <b>trans</b>forms + **FindMatches**; EMR <b>ste</b>ps; <b>Reds</b>hift <b>sto</b>red <b>proce</b>dures, <b>Materi</b>alized <b>Vie</b>ws (MVs), MERGE, <b>sched</b>uled <b>quer</b>ies.
- <b>Da</b>ta APIs: <b>vers</b>ion, <b>thro</b>ttle, <b>cac</b>he, <b>moni</b>tor, <b>sec</b>ure.
- <b>Pr</b>ep: **DataBrew** (<b>reci</b>pes, <b>prof</b>ile <b>jo</b>bs, <b>n</b>o <b>co</b>de), **SageMaker Unified Studio** (<b>o</b>ne <b>works</b>pace: SQL, <b>noteb</b>ooks, <b>vis</b>ual ETL, <b>cata</b>log).
- **Athena**: <b>workg</b>roups (<b>sc</b>an <b>lim</b>its, <b>res</b>ult <b>encry</b>ption), <b>prep</b>ared <b>state</b>ments, <b>vie</b>ws, CTAS, UNLOAD, <b>res</b>ult <b>reu</b>se, <b>provis</b>ioned <b>capa</b>city; **Athena for Spark** <b>noteb</b>ooks (<b>Da</b>ta <b>Proce</b>ssing <b>Un</b>it <b>hou</b>rs [DPU-<b>hou</b>rs]).
- **EventBridge**: <b>bus</b>es, <b>rul</b>es/<b>patt</b>erns, <b>targ</b>ets, **Scheduler**, <b>arch</b>ive/<b>rep</b>lay, <b>cro</b>ss-<b>acco</b>unt; <b>Gl</b>ue/EMR/<b>St</b>ep <b>Funct</b>ions <b>sta</b>te-<b>cha</b>nge <b>eve</b>nts.
- **QuickSight**: SPICE <b>v</b>s <b>dir</b>ect <b>que</b>ry, RLS, <b>embe</b>dded <b>dashb</b>oards, <b>Ama</b>zon <b>Q</b>.
- <b>Cle</b>an/<b>ver</b>ify: <b>Ath</b>ena SQL, <b>Lam</b>bda, <b>noteb</b>ooks, **Data Wrangler**, <b>Data</b>Brew.
- SQL: <b>vie</b>ws, <b>materi</b>alized <b>vie</b>ws, **late-binding views** (<b>requ</b>ired <b>wi</b>th <b>Spec</b>trum), ROLLUP/CUBE, <b>win</b>dow <b>funct</b>ions (<b>roll</b>ing <b>aver</b>age), <b>piv</b>ot <b>v</b>ia CASE <b>o</b>r PIVOT, `ROW_NUMBER` <b>ded</b>up.
- <b>Provis</b>ioned = <b>ste</b>ady <b>a</b>nd <b>chea</b>per <b>a</b>t <b>sca</b>le. <b>Serve</b>rless = <b>spi</b>ky, <b>lea</b>st <b>o</b>ps.
- <b>Aud</b>it: **CloudTrail** (<b>manag</b>ement <b>o</b>n <b>b</b>y <b>defa</b>ult, <b>da</b>ta <b>eve</b>nts <b>o</b>pt-<b>i</b>n, 90-<b>d</b>ay <b>hist</b>ory, <b>tra</b>ils, <b>o</b>rg <b>tra</b>ils, <b>integ</b>rity <b>valid</b>ation), **CloudTrail Lake** (SQL), <b>Reds</b>hift <b>aud</b>it <b>lo</b>gs, S3 <b>acc</b>ess <b>lo</b>gs.
- **CloudWatch Logs**: <b>reten</b>tion, **metric filters**, **subscription filters** (→ <b>Fire</b>hose/<b>Lam</b>bda/<b>OpenS</b>earch), <b>exp</b>ort <b>t</b>o S3, <b>Lo</b>gs <b>Insi</b>ghts.
- <b>Ale</b>rts: <b>EventB</b>ridge/<b>ala</b>rms → **SNS**.
- <b>Perfor</b>mance: <b>Gl</b>ue <b>j</b>ob <b>r</b>un <b>insi</b>ghts + <b>Spa</b>rk UI; EMR <b>lo</b>gs + YARN <b>metr</b>ics; <b>Reds</b>hift EXPLAIN + <b>sys</b>tem <b>vie</b>ws + ANALYZE/VACUUM; <b>Ath</b>ena <b>parti</b>tions/<b>colu</b>mnar/<b>jo</b>in <b>ord</b>er.
- <b>L</b>og <b>analy</b>tics: **Logs Insights** (<b>qui</b>ck), **Athena** (S3, <b>che</b>ap), **OpenSearch** (<b>re</b>al-<b>ti</b>me <b>sea</b>rch), **EMR** (<b>hu</b>ge <b>vol</b>ume).
- <b>Da</b>ta <b>qual</b>ity <b>dimen</b>sions: <b>comple</b>teness, <b>vali</b>dity, <b>consis</b>tency, <b>uniqu</b>eness, <b>fresh</b>ness, <b>integ</b>rity.
- **Glue Data Quality**: DQDL <b>rul</b>es, <b>recommen</b>dations, <b>cata</b>log <b>o</b>r <b>i</b>n-<b>j</b>ob, <b>fa</b>il <b>o</b>r <b>quara</b>ntine, <b>Cloud</b>Watch/<b>EventB</b>ridge, <b>anom</b>aly <b>detec</b>tion. **DataBrew**: <b>rule</b>sets + <b>prof</b>ile <b>jo</b>bs.
- <b>Samp</b>ling: <b>ran</b>dom, <b>syste</b>matic, **stratified**, <b>clus</b>ter, <b>reser</b>voir; <b>Ath</b>ena `TABLESAMPLE`.
- <b>Sk</b>ew: **salting**, <b>repart</b>ition, **broadcast joins**, AQE, <b>bet</b>ter <b>di</b>st/<b>parti</b>tion <b>ke</b>ys.
