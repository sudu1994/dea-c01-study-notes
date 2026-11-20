# Domain 4: Data Security and Governance (18%)

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> **About 9 of the 50 scored questions.**
>
> <b>Th</b>is <b>dom</b>ain <b>cov</b>ers <b>w</b>ho <b>c</b>an <b>g</b>et <b>i</b>n (<b>authent</b>ication), <b>wh</b>at <b>th</b>ey <b>c</b>an <b>d</b>o (<b>authori</b>zation), <b>h</b>ow <b>da</b>ta <b>i</b>s <b>prote</b>cted (<b>encry</b>ption <b>a</b>nd <b>mask</b>ing), <b>h</b>ow <b>acti</b>vity <b>i</b>s <b>reco</b>rded (<b>aud</b>it <b>logg</b>ing), <b>a</b>nd <b>h</b>ow <b>da</b>ta <b>i</b>s <b>gove</b>rned (<b>priv</b>acy, <b>Perso</b>nally <b>Identi</b>fiable <b>Inform</b>ation [PII], <b>sovere</b>ignty, <b>shar</b>ing, [<b>SageM</b>aker <b>Cata</b>log](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog)). <b>T</b>he <b>smal</b>lest <b>dom</b>ain, <b>b</b>ut <b>i</b>ts <b>quest</b>ions <b>a</b>re <b>oft</b>en "<b>t</b>wo <b>answ</b>ers <b>lo</b>ok <b>rig</b>ht," <b>s</b>o <b>preci</b>sion <b>matt</b>ers.

## Table of contents

- [<b>Ex</b>am <b>tas</b>ks <b>a</b>nd <b>ski</b>lls](#exam-tasks-and-skills)
- [<b>Ta</b>sk 4.1: <b>App</b>ly <b>authent</b>ication <b>mecha</b>nisms](#task-41-apply-authentication-mechanisms)
- [<b>Ta</b>sk 4.2: <b>App</b>ly <b>authori</b>zation <b>mecha</b>nisms](#task-42-apply-authorization-mechanisms)
- [<b>Ta</b>sk 4.3: <b>Ens</b>ure <b>da</b>ta <b>encry</b>ption <b>a</b>nd <b>mask</b>ing](#task-43-ensure-data-encryption-and-masking)
- [<b>Ta</b>sk 4.4: <b>Prep</b>are <b>lo</b>gs <b>f</b>or <b>aud</b>it](#task-44-prepare-logs-for-audit)
- [<b>Ta</b>sk 4.5: <b>Under</b>stand <b>da</b>ta <b>priv</b>acy <b>a</b>nd <b>gover</b>nance](#task-45-understand-data-privacy-and-governance)
- [<b>Gotc</b>has <b>a</b>nd <b>ex</b>am <b>tra</b>ps](#gotchas-and-exam-traps)
- [<b>Qui</b>ck-<b>rec</b>all <b>summ</b>ary](#quick-recall-summary)

## Exam tasks and skills

> <b>Summa</b>rized <b>fr</b>om <b>t</b>he <b>offi</b>cial AWS <b>Certi</b>fied <b>Da</b>ta <b>Engi</b>neer – <b>Assoc</b>iate (DEA-C01) <b>ex</b>am <b>gui</b>de (v1.1). <b>Exa</b>ct <b>word</b>ing: https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01-domain4.html

### Task 4.1: Apply authentication mechanisms
- **4.1.1** <b>Upd</b>ate [<b>Virt</b>ual <b>Priv</b>ate <b>Clo</b>ud [VPC]](00-data-basics-for-beginners.md#amazon-vpc) <b>secu</b>rity <b>gro</b>ups.
- **4.1.2** <b>Cre</b>ate/<b>upd</b>ate [<b>Iden</b>tity <b>a</b>nd <b>Acc</b>ess <b>Manag</b>ement [IAM]](00-data-basics-for-beginners.md#aws-iam) <b>gro</b>ups, <b>rol</b>es, <b>endpo</b>ints, <b>a</b>nd <b>serv</b>ices.
- **4.1.3** <b>Cre</b>ate <b>a</b>nd <b>rot</b>ate <b>creden</b>tials ([<b>Secr</b>ets <b>Mana</b>ger](00-data-basics-for-beginners.md#aws-secrets-manager)).
- **4.1.4** <b>S</b>et <b>u</b>p IAM <b>rol</b>es <b>f</b>or <b>acc</b>ess ([<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda), [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>face [API]](00-data-basics-for-beginners.md#api) <b>Gate</b>way, <b>Ama</b>zon <b>W</b>eb <b>Serv</b>ices [AWS] <b>Comm</b>and <b>Li</b>ne <b>Inter</b>face [CLI], [<b>CloudFo</b>rmation](00-data-basics-for-beginners.md#aws-cloudformation-cdk-and-sam)).
- **4.1.5** <b>App</b>ly IAM <b>poli</b>cies <b>t</b>o <b>rol</b>es, <b>endpo</b>ints, <b>serv</b>ices ([<b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice [S3]](00-data-basics-for-beginners.md#amazon-s3) <b>Acc</b>ess <b>Poi</b>nts, <b>Privat</b>eLink).
- **4.1.6** <b>Desc</b>ribe <b>mana</b>ged <b>v</b>s <b>unman</b>aged <b>serv</b>ices.
- **4.1.7** 🆕 <b>U</b>se <b>doma</b>ins, <b>dom</b>ain <b>uni</b>ts, <b>a</b>nd <b>proj</b>ects <b>i</b>n <b>SageM</b>aker <b>Unif</b>ied <b>Stu</b>dio.

### Task 4.2: Apply authorization mechanisms
- **4.2.1** <b>Wri</b>te <b>cus</b>tom IAM <b>poli</b>cies <b>wh</b>en <b>mana</b>ged <b>poli</b>cies <b>don</b>'t <b>f</b>it.
- **4.2.2** <b>Sto</b>re <b>applic</b>ation <b>a</b>nd <b>data</b>base <b>creden</b>tials (<b>Secr</b>ets <b>Mana</b>ger, <b>Param</b>eter <b>Sto</b>re).
- **4.2.3** <b>Gra</b>nt <b>data</b>base <b>use</b>rs, <b>gro</b>ups, <b>a</b>nd <b>rol</b>es <b>acc</b>ess <b>i</b>n <b>a</b> <b>data</b>base ([<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift)).
- **4.2.4** <b>Man</b>age <b>permis</b>sions <b>wi</b>th [<b>La</b>ke <b>Forma</b>tion](00-data-basics-for-beginners.md#aws-lake-formation) (<b>f</b>or <b>Reds</b>hift, [<b>Elas</b>tic <b>MapRe</b>duce [EMR]](00-data-basics-for-beginners.md#amazon-emr), [<b>Ath</b>ena](00-data-basics-for-beginners.md#amazon-athena), S3).
- **4.2.5** <b>App</b>ly <b>ro</b>le-<b>bas</b>ed, <b>t</b>ag-<b>bas</b>ed, <b>a</b>nd <b>attri</b>bute-<b>bas</b>ed <b>authori</b>zation.
- **4.2.6** <b>Bui</b>ld <b>cus</b>tom <b>lea</b>st-<b>privi</b>lege <b>poli</b>cies.

### Task 4.3: Ensure data encryption and masking
- **4.3.1** <b>App</b>ly <b>mask</b>ing <b>a</b>nd <b>anonymi</b>zation <b>f</b>or <b>compl</b>iance/<b>pol</b>icy.
- **4.3.2** <b>Encr</b>ypt/<b>decr</b>ypt <b>wi</b>th <b>ke</b>ys ([<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice [KMS]](00-data-basics-for-beginners.md#aws-kms)).
- **4.3.3** <b>Confi</b>gure <b>encry</b>ption <b>acr</b>oss <b>acco</b>unt <b>bound</b>aries.
- **4.3.4** <b>Encr</b>ypt <b>i</b>n <b>tran</b>sit <b>o</b>r **before** <b>tran</b>sit.

### Task 4.4: Prepare logs for audit
- **4.4.1** <b>Tra</b>ck API <b>cal</b>ls <b>wi</b>th [<b>Cloud</b>Trail](00-data-basics-for-beginners.md#aws-cloudtrail).
- **4.4.2** <b>Sto</b>re <b>applic</b>ation <b>lo</b>gs <b>i</b>n [<b>Cloud</b>Watch](00-data-basics-for-beginners.md#amazon-cloudwatch) <b>Lo</b>gs.
- **4.4.3** <b>Que</b>ry <b>centr</b>ally <b>wi</b>th <b>Cloud</b>Trail <b>La</b>ke.
- **4.4.4** <b>Anal</b>yze <b>lo</b>gs (<b>Ath</b>ena, <b>Cloud</b>Watch <b>Lo</b>gs <b>Insi</b>ghts, [<b>OpenS</b>earch](00-data-basics-for-beginners.md#amazon-opensearch-service)).
- **4.4.5** <b>Integ</b>rate <b>serv</b>ices <b>f</b>or <b>logg</b>ing (<b>e</b>.g., EMR <b>f</b>or <b>lar</b>ge <b>l</b>og <b>volu</b>mes).

### Task 4.5: Understand data privacy and governance
- **4.5.1** <b>Gra</b>nt <b>permis</b>sions <b>f</b>or <b>da</b>ta <b>shar</b>ing (<b>e</b>.g., <b>Reds</b>hift <b>da</b>ta <b>shar</b>ing).
- **4.5.2** <b>Iden</b>tify PII ([<b>Mac</b>ie](00-data-basics-for-beginners.md#amazon-macie) <b>wi</b>th <b>La</b>ke <b>Forma</b>tion).
- **4.5.3** <b>Prev</b>ent <b>back</b>ups/<b>replic</b>ation <b>t</b>o <b>disal</b>lowed <b>Regi</b>ons.
- **4.5.4** <b>Vi</b>ew <b>configu</b>ration <b>chan</b>ges ([AWS <b>Con</b>fig](00-data-basics-for-beginners.md#aws-config)).
- **4.5.5** <b>Main</b>tain <b>da</b>ta <b>sovere</b>ignty.
- **4.5.6** 🆕 <b>Man</b>age <b>da</b>ta <b>acc</b>ess <b>thro</b>ugh <b>SageM</b>aker <b>Cata</b>log <b>proj</b>ects.
- **4.5.7** 🆕 <b>Desc</b>ribe <b>gover</b>nance <b>frame</b>works <b>a</b>nd <b>da</b>ta <b>shar</b>ing <b>patt</b>erns.

---

## Task 4.1: Apply authentication mechanisms

### Core concepts

- **Authentication** = <b>prov</b>ing *<b>w</b>ho* <b>y</b>ou <b>a</b>re. **Authorization** = <b>deci</b>ding *<b>wh</b>at* <b>y</b>ou <b>m</b>ay <b>d</b>o.
- **Methods:**
  - **Password-based**: <b>data</b>base <b>use</b>rs, <b>cons</b>ole <b>passw</b>ords (+ **Multi-Factor Authentication [MFA]**).
  - **Certificate-based**: <b>X</b>.509 <b>certif</b>icates, <b>mut</b>ual <b>Trans</b>port <b>Lay</b>er <b>Secu</b>rity (TLS), IoT <b>devi</b>ces, <b>cli</b>ent <b>certif</b>icates.
  - **Role-based**: <b>ass</b>ume <b>a</b>n **IAM role** <b>a</b>nd <b>g</b>et **temporary credentials** <b>fr</b>om AWS <b>Secu</b>rity <b>Tok</b>en <b>Serv</b>ice (STS). **This is the preferred method for AWS workloads.**
- <b>Workf</b>orce <b>use</b>rs <b>si</b>gn <b>i</b>n <b>thro</b>ugh **IAM Identity Center** (<b>Sin</b>gle <b>Si</b>gn-<b>O</b>n [SSO], <b>feder</b>ated <b>wi</b>th <b>Ok</b>ta, <b>Micro</b>soft <b>Ent</b>ra ID, <b>e</b>tc.). <b>Avo</b>id <b>lo</b>ng-<b>liv</b>ed IAM <b>us</b>er <b>acc</b>ess <b>ke</b>ys.

### VPC security groups (skill 4.1.1)

| | <b>Secu</b>rity <b>gro</b>up | <b>Netw</b>ork <b>Acc</b>ess <b>Cont</b>rol <b>Li</b>st (ACL) |
|---|---|---|
| <b>Lev</b>el | <b>Elas</b>tic <b>Netw</b>ork <b>Inter</b>face (ENI)/<b>inst</b>ance ([<b>Gl</b>ue](00-data-basics-for-beginners.md#aws-glue) <b>conne</b>ction <b>Elas</b>tic <b>Netw</b>ork <b>Inter</b>faces [ENIs], <b>Reds</b>hift, [<b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice [RDS]](00-data-basics-for-beginners.md#amazon-rds), EMR, <b>Lam</b>bda <b>i</b>n VPC) | <b>Sub</b>net |
| <b>Sta</b>te | **Stateful** (<b>ret</b>urn <b>traf</b>fic <b>allo</b>wed <b>automat</b>ically) | **Stateless** (<b>all</b>ow <b>bo</b>th <b>direc</b>tions, <b>in</b>cl. <b>ephem</b>eral <b>por</b>ts) |
| <b>Rul</b>es | **Allow only** | <b>All</b>ow <b>a</b>nd <b>de</b>ny, <b>numb</b>ered <b>ord</b>er |
| <b>Sour</b>ces | <b>Class</b>less <b>Int</b>er-<b>Dom</b>ain <b>Rout</b>ing <b>ran</b>ges (CIDRs), <b>pre</b>fix <b>lis</b>ts, **other security groups** | CIDRs <b>on</b>ly |

<b>Da</b>ta-<b>engine</b>ering <b>patt</b>erns:
- <b>Data</b>base <b>Secu</b>rity <b>Gro</b>up (SG) <b>all</b>ows <b>t</b>he <b>po</b>rt (5439 <b>Reds</b>hift, 5432 [<b>Postg</b>reSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server), 3306 MySQL) **from the application/Glue SG**, <b>n</b>ot <b>fr</b>om `0.0.0.0/0`.
- **Glue**: SG <b>nee</b>ds <b>a</b> **self-referencing inbound rule for all Transmission Control Protocol (TCP)**.
- **EMR**: <b>mana</b>ged <b>secu</b>rity <b>gro</b>ups <b>f</b>or <b>prim</b>ary/<b>co</b>re/<b>ta</b>sk <b>nod</b>es; <b>blo</b>ck <b>pub</b>lic <b>acc</b>ess <b>sett</b>ing.
- <b>Lam</b>bda <b>i</b>n <b>a</b> VPC: <b>outb</b>ound <b>rul</b>es <b>t</b>o <b>rea</b>ch <b>datab</b>ases; <b>Netw</b>ork <b>Addr</b>ess <b>Transl</b>ation (NAT) <b>gate</b>way <b>o</b>r VPC <b>endpo</b>ints <b>f</b>or AWS <b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>faces (APIs).

### IAM groups, roles, endpoints, services (skills 4.1.2, 4.1.4)

- **IAM users** (<b>avo</b>id <b>f</b>or <b>ap</b>ps) → **groups** (<b>ass</b>ign <b>poli</b>cies <b>t</b>o <b>ma</b>ny <b>use</b>rs) → **roles** (<b>assu</b>med <b>b</b>y <b>serv</b>ices, <b>use</b>rs, <b>oth</b>er <b>acco</b>unts; <b>tempo</b>rary <b>creden</b>tials).
- <b>A</b> <b>ro</b>le <b>h</b>as <b>a</b> **trust policy** (<b>w</b>ho <b>c</b>an <b>ass</b>ume <b>i</b>t) <b>a</b>nd **permissions policies** (<b>wh</b>at <b>i</b>t <b>c</b>an <b>d</b>o).

| <b>Serv</b>ice | <b>Ro</b>le <b>set</b>up |
|---|---|
| **Lambda** | **Execution role** <b>trus</b>ted <b>b</b>y `lambda.amazonaws.com` (<b>e</b>.g., <b>re</b>ad S3, <b>wri</b>te <b>lo</b>gs) |
| **Glue** | <b>Serv</b>ice <b>ro</b>le <b>trus</b>ted <b>b</b>y `glue.amazonaws.com` (S3 <b>pat</b>hs, <b>cata</b>log, KMS, <b>Cloud</b>Watch) |
| **API Gateway** | <b>Ro</b>le <b>f</b>or AWS <b>serv</b>ice <b>integr</b>ations (<b>e</b>.g., <b>p</b>ut <b>t</b>o [<b>Kine</b>sis](00-data-basics-for-beginners.md#amazon-kinesis-data-streams)); <b>a</b> <b>reso</b>urce-<b>bas</b>ed <b>permi</b>ssion <b>o</b>n <b>Lam</b>bda <b>le</b>ts API <b>Gate</b>way <b>inv</b>oke <b>i</b>t; IAM <b>authori</b>zation <b>f</b>or <b>call</b>ers |
| **AWS CLI** | <b>Nam</b>ed <b>prof</b>iles <b>wi</b>th `role_arn` + `source_profile` (<b>o</b>r IAM <b>Iden</b>tity <b>Cen</b>ter `sso` <b>prof</b>iles) <b>t</b>o <b>ass</b>ume <b>rol</b>es |
| **CloudFormation** | **Service role** <b>CloudFo</b>rmation <b>us</b>es <b>t</b>o <b>cre</b>ate <b>resou</b>rces, <b>s</b>o <b>use</b>rs <b>on</b>ly <b>ne</b>ed <b>permi</b>ssion <b>t</b>o <b>pa</b>ss <b>th</b>at <b>ro</b>le (`iam:PassRole`) |
| **Redshift** | IAM <b>ro</b>le <b>atta</b>ched <b>t</b>o <b>t</b>he <b>clus</b>ter/<b>workg</b>roup <b>f</b>or COPY/UNLOAD/<b>Spec</b>trum |
| **EC2/EMR** | **Instance profile** (<b>ro</b>le <b>f</b>or <b>insta</b>nces); EMR <b>al</b>so <b>h</b>as <b>a</b> <b>serv</b>ice <b>ro</b>le |

- **`iam:PassRole`**: <b>requ</b>ired <b>t</b>o <b>ha</b>nd <b>a</b> <b>ro</b>le <b>t</b>o <b>a</b> <b>serv</b>ice (<b>e</b>.g., <b>a</b> <b>us</b>er <b>crea</b>ting <b>a</b> <b>Gl</b>ue <b>j</b>ob <b>wi</b>th <b>ro</b>le <b>X</b> <b>nee</b>ds `iam:PassRole` <b>o</b>n <b>X</b>). <b>It</b>'s <b>a</b> <b>freq</b>uent <b>permi</b>ssion-<b>err</b>or <b>ans</b>wer.
- **VPC endpoints**: **gateway endpoints** (S3, [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb); <b>rou</b>te <b>tab</b>le <b>ent</b>ry; <b>fr</b>ee) <b>a</b>nd **interface endpoints** (<b>Privat</b>eLink ENIs <b>f</b>or <b>mo</b>st <b>serv</b>ices: <b>Gl</b>ue, <b>Ath</b>ena, KMS, <b>Secr</b>ets <b>Mana</b>ger, STS, <b>Kine</b>sis…). <b>Traf</b>fic <b>sta</b>ys <b>o</b>n <b>t</b>he AWS <b>netw</b>ork <b>wi</b>th <b>n</b>o <b>inte</b>rnet <b>o</b>r NAT <b>nee</b>ded.

### Credentials and rotation (skill 4.1.3)

- **AWS Secrets Manager**: <b>sto</b>res <b>data</b>base (DB) <b>creden</b>tials, API <b>ke</b>ys, <b>tok</b>ens; **automatic rotation** <b>o</b>n <b>a</b> <b>sche</b>dule <b>usi</b>ng <b>Lam</b>bda <b>rota</b>tion <b>funct</b>ions (<b>mana</b>ged <b>rota</b>tion <b>f</b>or RDS, [<b>Aur</b>ora](00-data-basics-for-beginners.md#amazon-aurora), <b>Reds</b>hift, <b>Docum</b>entDB); KMS-<b>encry</b>pted; <b>reso</b>urce <b>poli</b>cies <b>f</b>or **cross-account** <b>acc</b>ess; <b>versi</b>oning (`AWSCURRENT`/`AWSPREVIOUS`).
- **RDS/Aurora/Redshift managed master passwords** <b>c</b>an <b>li</b>ve <b>i</b>n <b>Secr</b>ets <b>Mana</b>ger <b>dire</b>ctly.
- **Redshift temporary credentials**: `GetClusterCredentials` / IAM-<b>bas</b>ed <b>au</b>th (<b>o</b>r <b>Reds</b>hift <b>Serve</b>rless `GetCredentials`) <b>giv</b>es <b>sho</b>rt-<b>liv</b>ed <b>data</b>base <b>creden</b>tials, <b>wi</b>th <b>n</b>o <b>sto</b>red <b>passw</b>ords.
- **RDS IAM database authentication**: <b>authen</b>ticate <b>wi</b>th <b>a</b>n IAM <b>tok</b>en <b>inst</b>ead <b>o</b>f <b>a</b> <b>pass</b>word.

### IAM policies on roles, endpoints, services (skill 4.1.5)

- **Identity-based policies** (<b>atta</b>ched <b>t</b>o <b>use</b>rs/<b>gro</b>ups/<b>rol</b>es) <b>v</b>s **resource-based policies** (<b>atta</b>ched <b>t</b>o <b>t</b>he <b>reso</b>urce: S3 <b>buc</b>ket <b>pol</b>icy, KMS <b>k</b>ey <b>pol</b>icy, [<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice [SQS]](00-data-basics-for-beginners.md#amazon-sqs) <b>que</b>ue <b>pol</b>icy, <b>Secr</b>ets <b>Mana</b>ger <b>reso</b>urce <b>pol</b>icy, <b>Lam</b>bda <b>permis</b>sions).
- **S3 Access Points**: <b>nam</b>ed <b>netw</b>ork <b>endpo</b>ints <b>o</b>n <b>a</b> <b>buc</b>ket, <b>ea</b>ch <b>wi</b>th **its own access point policy**. <b>Th</b>ey <b>simp</b>lify <b>mana</b>ging <b>acc</b>ess <b>f</b>or <b>ma</b>ny <b>tea</b>ms/<b>ap</b>ps <b>o</b>n <b>a</b> <b>sha</b>red <b>buc</b>ket. <b>Th</b>ey <b>c</b>an <b>b</b>e **VPC-only** (<b>netw</b>ork <b>ori</b>gin = VPC). <b>T</b>he <b>buc</b>ket <b>pol</b>icy <b>c</b>an <b>dele</b>gate <b>cont</b>rol <b>t</b>o <b>acc</b>ess <b>poi</b>nts.
- **VPC endpoint policies**: <b>rest</b>rict *<b>whi</b>ch* <b>resou</b>rces/<b>acti</b>ons <b>c</b>an <b>b</b>e <b>reac</b>hed <b>thro</b>ugh <b>t</b>he <b>endp</b>oint (<b>e</b>.g., <b>on</b>ly <b>t</b>he <b>compa</b>ny's <b>buck</b>ets → <b>da</b>ta <b>exfilt</b>ration <b>prote</b>ction).
- <b>Buc</b>ket <b>pol</b>icy <b>condi</b>tions: `aws:SourceVpce` (<b>on</b>ly <b>v</b>ia <b>a</b> <b>spec</b>ific <b>endp</b>oint), `aws:SourceVpc`, `aws:PrincipalOrgID` (<b>on</b>ly <b>princ</b>ipals <b>i</b>n <b>yo</b>ur <b>organi</b>zation), `aws:SecureTransport`.
- **AWS PrivateLink** <b>al</b>so <b>le</b>ts <b>y</b>ou <b>exp</b>ose <b>yo</b>ur <b>o</b>wn <b>serv</b>ice (<b>Netw</b>ork <b>Lo</b>ad <b>Bala</b>ncer [NLB]) <b>priva</b>tely <b>t</b>o <b>oth</b>er <b>Virt</b>ual <b>Priv</b>ate <b>Clo</b>uds (VPCs)/<b>acco</b>unts.

### Managed vs unmanaged services (skill 4.1.6)

| | <b>Mana</b>ged (<b>Gl</b>ue, <b>Ath</b>ena, <b>Reds</b>hift <b>Serve</b>rless, <b>Dyna</b>moDB, [<b>Mana</b>ged <b>Strea</b>ming <b>f</b>or <b>Apa</b>che <b>Kaf</b>ka [MSK]](00-data-basics-for-beginners.md#amazon-msk) <b>Serve</b>rless, [<b>Fire</b>hose](00-data-basics-for-beginners.md#amazon-data-firehose)) | <b>Unman</b>aged / <b>se</b>lf-<b>mana</b>ged ([<b>Kaf</b>ka](00-data-basics-for-beginners.md#apache-kafka) <b>o</b>r [<b>Had</b>oop](00-data-basics-for-beginners.md#apache-hadoop) <b>o</b>n <b>Elas</b>tic <b>Comp</b>ute <b>Clo</b>ud [EC2], DB <b>o</b>n EC2) |
|---|---|---|
| <b>Patc</b>hing, <b>Opera</b>ting <b>Sys</b>tem (OS), <b>Hi</b>gh <b>Availa</b>bility (HA) | AWS | **You** |
| <b>Secu</b>rity <b>respons</b>ibility | <b>Y</b>ou <b>confi</b>gure IAM, <b>encry</b>ption, <b>netw</b>ork; AWS <b>secu</b>res <b>t</b>he <b>infrast</b>ructure | <b>Y</b>ou <b>al</b>so <b>sec</b>ure <b>t</b>he OS, <b>soft</b>ware, <b>patc</b>hes, <b>back</b>ups |
| <b>Flexib</b>ility | <b>Le</b>ss <b>cont</b>rol | <b>Fu</b>ll <b>cont</b>rol <b>o</b>f <b>vers</b>ions/<b>conf</b>igs |
| <b>O</b>ps <b>over</b>head | <b>L</b>ow | <b>Hi</b>gh |

<b>Th</b>is <b>i</b>s <b>t</b>he **shared responsibility model**: <b>t</b>he <b>mo</b>re <b>mana</b>ged <b>t</b>he <b>serv</b>ice, <b>t</b>he <b>mo</b>re AWS <b>tak</b>es <b>o</b>n.

### 🆕 SageMaker Unified Studio: domains, domain units, projects (skill 4.1.7)

| <b>Conc</b>ept | <b>Mean</b>ing | <b>Gover</b>nance <b>ro</b>le |
|---|---|---|
| **Domain** | <b>T</b>op-<b>lev</b>el <b>conta</b>iner <b>f</b>or <b>a</b>n <b>organiz</b>ation's <b>SageM</b>aker <b>Unif</b>ied <b>Stu</b>dio (<b>use</b>rs, <b>cata</b>log, <b>proj</b>ects); <b>usua</b>lly <b>ti</b>ed <b>t</b>o **IAM Identity Center** <b>f</b>or <b>si</b>gn-<b>i</b>n | <b>Boun</b>dary <b>f</b>or <b>gover</b>nance, <b>cata</b>log, <b>a</b>nd <b>use</b>rs |
| **Domain units** | <b>Hierar</b>chical <b>s</b>ub-<b>group</b>ings <b>ins</b>ide <b>a</b> <b>dom</b>ain (<b>e</b>.g., <b>b</b>y <b>busi</b>ness <b>un</b>it: <b>Fina</b>nce, <b>Marke</b>ting) | <b>Deleg</b>ated <b>owner</b>ship <b>a</b>nd **authorization policies** (<b>w</b>ho <b>c</b>an <b>cre</b>ate <b>proj</b>ects, <b>publ</b>ish <b>t</b>o <b>t</b>he <b>cata</b>log, <b>u</b>se <b>whi</b>ch <b>proj</b>ect <b>prof</b>iles) |
| **Projects** | <b>Collabo</b>rative <b>works</b>paces <b>f</b>or <b>a</b> <b>te</b>am: <b>memb</b>ers (<b>own</b>ers/<b>contri</b>butors), <b>da</b>ta, <b>comp</b>ute, <b>too</b>ls | <b>Ea</b>ch <b>proj</b>ect <b>h</b>as <b>i</b>ts **own IAM role**. <b>Memb</b>ers' <b>da</b>ta <b>acc</b>ess <b>i</b>s <b>gran</b>ted **to the project**, <b>s</b>o <b>it</b>'s <b>t</b>he <b>un</b>it <b>o</b>f <b>acc</b>ess <b>cont</b>rol. |
| **Project profiles / blueprints** | <b>Templ</b>ates <b>defi</b>ning <b>whi</b>ch <b>resou</b>rces <b>a</b>nd <b>too</b>ls <b>a</b> <b>proj</b>ect <b>ge</b>ts | <b>Standa</b>rdized, <b>appr</b>oved <b>enviro</b>nments |

---

## Task 4.2: Apply authorization mechanisms

### Custom IAM policies and least privilege (skills 4.2.1, 4.2.6)

- **AWS managed policies** (<b>e</b>.g., `AmazonS3ReadOnlyAccess`): <b>bro</b>ad, <b>maint</b>ained <b>b</b>y AWS, <b>can</b>'t <b>b</b>e <b>edi</b>ted.
- **Customer managed policies**: <b>y</b>ou <b>wri</b>te <b>a</b>nd <b>vers</b>ion <b>th</b>em; <b>reus</b>able; <b>t</b>he <b>ans</b>wer <b>wh</b>en **managed policies are too broad**.
- **Inline policies**: <b>embe</b>dded <b>i</b>n <b>o</b>ne <b>iden</b>tity; <b>str</b>ict 1:1 <b>relatio</b>nships.

**Least-privilege policy techniques:**
- <b>Spec</b>ific **actions** (<b>n</b>o `s3:*`), <b>spec</b>ific **resource Amazon Resource Names [ARNs]** (<b>buc</b>ket + <b>pre</b>fix: `arn:aws:s3:::lake/curated/finance/*`).
- **Conditions**: `s3:prefix`, `aws:PrincipalTag`, `aws:SourceVpce`, `aws:RequestedRegion`, `kms:ViaService`, `aws:MultiFactorAuthPresent`.
- <b>Reme</b>mber <b>th</b>at S3 <b>nee</b>ds **`s3:ListBucket` on the bucket Amazon Resource Name (ARN)** <b>a</b>nd **`s3:GetObject` on `bucket/*`**, <b>t</b>wo <b>diffe</b>rent <b>resou</b>rces.
- **IAM Access Analyzer**: <b>gener</b>ates <b>lea</b>st-<b>privi</b>lege <b>poli</b>cies **from CloudTrail activity**, <b>valid</b>ates <b>poli</b>cies, <b>a</b>nd <b>fin</b>ds <b>resou</b>rces <b>sha</b>red <b>outs</b>ide <b>yo</b>ur <b>acco</b>unt.
- <b>Guard</b>rails: **permission boundaries** (<b>m</b>ax <b>permis</b>sions <b>f</b>or <b>a</b> <b>ro</b>le/<b>us</b>er) <b>a</b>nd **Service Control Policies (SCPs)** <b>i</b>n AWS <b>Organiz</b>ations (<b>m</b>ax <b>permis</b>sions <b>f</b>or <b>acco</b>unts). <b>Neit</b>her <b>gra</b>nts <b>anyt</b>hing. <b>Th</b>ey <b>on</b>ly <b>lim</b>it.
- <b>Evalu</b>ation: <b>a</b>n **explicit Deny always wins**. <b>Other</b>wise, <b>acc</b>ess <b>nee</b>ds <b>a</b>n <b>All</b>ow (<b>a</b>nd <b>no</b>ne <b>o</b>f SCP/<b>boun</b>dary/<b>sess</b>ion <b>pol</b>icy <b>bloc</b>king <b>i</b>t).

### Storing credentials (skill 4.2.2)

| | <b>Secr</b>ets <b>Mana</b>ger | <b>Syst</b>ems <b>Mana</b>ger <b>Param</b>eter <b>Sto</b>re |
|---|---|---|
| <b>Purp</b>ose | <b>Secr</b>ets (DB <b>passw</b>ords, API <b>ke</b>ys) | <b>Configu</b>ration <b>val</b>ues <b>a</b>nd <b>secr</b>ets (`SecureString` <b>wi</b>th KMS) |
| **Automatic rotation** | ✅ <b>bui</b>lt <b>i</b>n | ❌ (<b>d</b>o <b>i</b>t <b>your</b>self) |
| <b>Cro</b>ss-<b>acco</b>unt <b>shar</b>ing | ✅ <b>reso</b>urce <b>pol</b>icy | <b>Limi</b>ted (<b>adva</b>nced <b>ti</b>er <b>shar</b>ing) |
| <b>Co</b>st | <b>P</b>er <b>sec</b>ret <b>p</b>er <b>mon</b>th + API <b>cal</b>ls | **Standard tier free** |
| <b>Ex</b>am <b>cho</b>ice | "**Rotate automatically**", DB <b>creden</b>tials <b>f</b>or RDS/<b>Reds</b>hift | <b>Che</b>ap <b>con</b>fig/<b>fla</b>gs, <b>n</b>o <b>rota</b>tion <b>nee</b>ded |

<b>Gl</b>ue <b>connec</b>tions, <b>Lam</b>bda, EMR, [<b>Mana</b>ged <b>Workf</b>lows <b>f</b>or <b>Apa</b>che <b>Airf</b>low [MWAA]](00-data-basics-for-beginners.md#amazon-mwaa), <b>a</b>nd [<b>Quick</b>Sight](00-data-basics-for-beginners.md#amazon-quicksight) <b>c</b>an <b>a</b>ll <b>re</b>ad <b>fr</b>om <b>Secr</b>ets <b>Mana</b>ger. **Never** <b>p</b>ut <b>creden</b>tials <b>i</b>n <b>co</b>de, <b>pla</b>in <b>enviro</b>nment <b>varia</b>bles, <b>o</b>r <b>j</b>ob <b>param</b>eters.

### Database-level authorization in Redshift (skill 4.2.3)

- **Users** <b>a</b>nd **groups** (<b>leg</b>acy) <b>o</b>r **roles** (**Role-Based Access Control [RBAC]**: `CREATE ROLE analyst; GRANT SELECT ON ALL TABLES IN SCHEMA sales TO ROLE analyst; GRANT ROLE analyst TO alice;`). <b>Rol</b>es <b>c</b>an <b>b</b>e <b>nes</b>ted <b>a</b>nd <b>incl</b>ude <b>sys</b>tem <b>privi</b>leges.
- `GRANT`/`REVOKE` <b>a</b>t **database, schema, table, column** <b>lev</b>els (`GRANT SELECT (name, city) ON customers TO ROLE support;`).
- **Default privileges** (`ALTER DEFAULT PRIVILEGES`) <b>s</b>o <b>n</b>ew <b>tab</b>les <b>automat</b>ically <b>g</b>et <b>t</b>he <b>rig</b>ht <b>gra</b>nts.
- **Row-level security (RLS)** <b>poli</b>cies: `CREATE RLS POLICY … USING (region = current_user_region)` <b>atta</b>ched <b>t</b>o <b>tab</b>les <b>a</b>nd <b>rol</b>es.
- **Dynamic data masking** <b>poli</b>cies (<b>s</b>ee 4.3).
- **IAM Identity Center integration**: <b>use</b>rs <b>si</b>gn <b>i</b>n <b>wi</b>th <b>corpo</b>rate <b>ident</b>ities, <b>a</b>nd <b>the</b>ir <b>gro</b>ups <b>m</b>ap <b>t</b>o <b>Reds</b>hift <b>rol</b>es.

### Lake Formation permissions (skill 4.2.4)

**Why Lake Formation:** <b>mana</b>ging <b>acc</b>ess <b>t</b>o <b>a</b> [<b>da</b>ta <b>la</b>ke](00-data-basics-for-beginners.md#data-lake) <b>wi</b>th S3 <b>buc</b>ket <b>poli</b>cies + IAM <b>ge</b>ts <b>unmana</b>geable <b>a</b>t <b>tab</b>le/<b>col</b>umn <b>lev</b>el. <b>La</b>ke <b>Forma</b>tion <b>prov</b>ides **database-style grants** <b>o</b>n <b>cata</b>log <b>resou</b>rces <b>a</b>nd <b>enfo</b>rces <b>th</b>em <b>acr</b>oss <b>engi</b>nes.

**How it works:**
1. **Register S3 locations** <b>wi</b>th <b>La</b>ke <b>Forma</b>tion (<b>i</b>t <b>th</b>en <b>ven</b>ds <b>tempo</b>rary <b>creden</b>tials <b>t</b>o <b>integ</b>rated <b>engi</b>nes).
2. <b>Gra</b>nt <b>permis</b>sions <b>o</b>n **databases, tables, columns** (`SELECT`, `INSERT`, `ALTER`, `DROP`, `DESCRIBE`, <b>pl</b>us <b>grant</b>able <b>opti</b>ons) <b>t</b>o IAM <b>princ</b>ipals, <b>Iden</b>tity <b>Cen</b>ter <b>use</b>rs/<b>gro</b>ups, <b>o</b>r <b>exte</b>rnal <b>acco</b>unts.
3. <b>Engi</b>nes <b>th</b>at <b>integ</b>rate (**Athena, Redshift Spectrum, EMR, Glue Extract, Transform, Load [ETL], QuickSight via Athena**) <b>enfo</b>rce <b>tho</b>se <b>permis</b>sions.

| <b>Feat</b>ure | <b>Explan</b>ation |
|---|---|
| **Column-level security** | <b>Incl</b>ude/<b>excl</b>ude <b>colu</b>mns <b>i</b>n <b>t</b>he <b>gra</b>nt |
| **Data filters** | **Row-level** (<b>fil</b>ter <b>expre</b>ssion, <b>e</b>.g., `country = 'US'`) <b>a</b>nd **cell-level** (<b>ro</b>ws + <b>colu</b>mns) <b>secu</b>rity |
| **Lake Formation Tag-Based Access Control (LF-TBAC)** | <b>Ass</b>ign **Lake Formation tags [LF-tags]** (<b>e</b>.g., `classification=confidential`, `domain=sales`) <b>t</b>o <b>datab</b>ases/<b>tab</b>les/<b>colu</b>mns <b>a</b>nd <b>gra</b>nt <b>o</b>n <b>t</b>ag <b>expres</b>sions. <b>Sca</b>les <b>t</b>o <b>thous</b>ands <b>o</b>f <b>tab</b>les, <b>a</b>nd <b>n</b>ew <b>tab</b>les <b>inhe</b>rit <b>acc</b>ess <b>wh</b>en <b>tag</b>ged. |
| **Cross-account sharing** | <b>Sha</b>re <b>datab</b>ases/<b>tab</b>les <b>wi</b>th <b>oth</b>er <b>acco</b>unts (<b>v</b>ia AWS <b>Reso</b>urce <b>Acc</b>ess <b>Mana</b>ger [RAM]). <b>T</b>he <b>cons</b>umer <b>crea</b>tes <b>a</b> **resource link**. |
| **Data lake administrators** | <b>Princ</b>ipals <b>w</b>ho <b>man</b>age <b>permis</b>sions |
| **Hybrid access mode / IAMAllowedPrincipals** | <b>Trans</b>ition <b>fr</b>om IAM-<b>on</b>ly <b>t</b>o <b>La</b>ke <b>Forma</b>tion <b>permis</b>sions <b>with</b>out <b>brea</b>king <b>exis</b>ting <b>use</b>rs |

> <b>I</b>f <b>La</b>ke <b>Forma</b>tion <b>i</b>s <b>enab</b>led <b>b</b>ut <b>use</b>rs <b>sti</b>ll <b>g</b>et <b>acc</b>ess <b>th</b>ey <b>shoul</b>dn't, <b>che</b>ck <b>t</b>he <b>defa</b>ult **IAMAllowedPrincipals** <b>gra</b>nt ("<b>U</b>se <b>on</b>ly IAM <b>acc</b>ess <b>cont</b>rol" <b>sett</b>ings).

### Role-, tag-, and attribute-based authorization (skill 4.2.5)

| <b>Mod</b>el | <b>H</b>ow | <b>Be</b>st <b>f</b>or |
|---|---|---|
| **RBAC** (<b>ro</b>le-<b>bas</b>ed) | <b>Permis</b>sions <b>atta</b>ched <b>t</b>o <b>rol</b>es (<b>j</b>ob <b>funct</b>ions); <b>use</b>rs <b>ass</b>ume <b>rol</b>es | <b>Sta</b>ble <b>tea</b>ms <b>a</b>nd <b>j</b>ob <b>funct</b>ions; <b>sim</b>ple |
| **TBAC** (<b>t</b>ag-<b>bas</b>ed, <b>e</b>.g., **Lake Formation LF-tags**) | <b>Resou</b>rces <b>tag</b>ged; <b>gra</b>nts <b>writ</b>ten <b>o</b>n <b>t</b>ag <b>val</b>ues | <b>Lar</b>ge, <b>grow</b>ing <b>cata</b>logs: <b>gra</b>nt <b>on</b>ce <b>o</b>n `domain=sales`, <b>n</b>ew <b>tab</b>les <b>inhe</b>rit |
| **ABAC** (<b>attri</b>bute-<b>bas</b>ed, IAM) | <b>Poli</b>cies <b>comp</b>are **principal tags** <b>t</b>o **resource tags** (`"aws:ResourceTag/project": "${aws:PrincipalTag/project}"`) | <b>Ma</b>ny <b>tea</b>ms/<b>proj</b>ects <b>wi</b>th <b>few</b>er <b>poli</b>cies; <b>acc</b>ess <b>foll</b>ows <b>attri</b>butes <b>automat</b>ically |

---

## Task 4.3: Ensure data encryption and masking

### Masking and anonymization (skill 4.3.1)

| <b>Techn</b>ique | <b>Wh</b>at <b>i</b>t <b>do</b>es | <b>Rever</b>sible? |
|---|---|---|
| **Masking / redaction** | <b>Hi</b>de <b>a</b>ll <b>o</b>r <b>pa</b>rt <b>o</b>f <b>a</b> <b>val</b>ue (`***-**-1234`) | <b>N</b>o (<b>f</b>or <b>t</b>he <b>vie</b>wer) |
| **Hashing** (<b>sal</b>ted) | <b>Repl</b>ace <b>val</b>ue <b>wi</b>th <b>a</b> <b>ha</b>sh; <b>joi</b>ns <b>sti</b>ll <b>wo</b>rk | <b>N</b>o |
| **Tokenization** | <b>Repl</b>ace <b>wi</b>th <b>a</b> <b>tok</b>en; <b>t</b>he <b>mapp</b>ing <b>i</b>s <b>sto</b>red <b>secu</b>rely | <b>Y</b>es, <b>wi</b>th <b>t</b>he <b>vau</b>lt |
| **Encryption** (<b>determi</b>nistic <b>o</b>r <b>probabi</b>listic) | <b>Ciphe</b>rtext; <b>determi</b>nistic <b>kee</b>ps <b>joinab</b>ility | <b>Y</b>es, <b>wi</b>th <b>t</b>he <b>k</b>ey |
| **Generalization** | <b>Red</b>uce <b>preci</b>sion (<b>a</b>ge → <b>a</b>ge <b>ba</b>nd, ZIP → <b>fir</b>st 3 <b>dig</b>its) | <b>N</b>o |
| **Pseudonymization** <b>v</b>s **anonymization** | <b>Pseudon</b>ymized <b>da</b>ta <b>c</b>an <b>b</b>e <b>r</b>e-<b>ident</b>ified <b>wi</b>th <b>ext</b>ra <b>in</b>fo (<b>sti</b>ll <b>pers</b>onal <b>da</b>ta <b>und</b>er <b>Gene</b>ral <b>Da</b>ta <b>Prote</b>ction <b>Regul</b>ation [GDPR]); <b>anony</b>mized <b>da</b>ta <b>can</b>not | — |

**AWS tools:**
- **Redshift dynamic data masking**: <b>mask</b>ing <b>poli</b>cies <b>appl</b>ied <b>a</b>t <b>que</b>ry <b>ti</b>me <b>bas</b>ed <b>o</b>n <b>ro</b>le (<b>anal</b>ysts <b>s</b>ee <b>mas</b>ked <b>Soc</b>ial <b>Secu</b>rity <b>Num</b>ber [SSN]; <b>audi</b>tors <b>s</b>ee <b>fu</b>ll).
- **Lake Formation**: <b>excl</b>ude <b>sensi</b>tive <b>colu</b>mns <b>o</b>r <b>u</b>se <b>ce</b>ll-<b>lev</b>el <b>filt</b>ers.
- **Glue sensitive data detection**: <b>fi</b>nd PII <b>i</b>n ETL <b>jo</b>bs <b>a</b>nd **redact/hash/replace** <b>i</b>t.
- **[DataBrew](00-data-basics-for-beginners.md#aws-glue-databrew)**: <b>mask</b>ing, <b>hash</b>ing, <b>determi</b>nistic/<b>probabi</b>listic <b>encry</b>ption, <b>substi</b>tution <b>trans</b>forms.
- **[Amazon Comprehend](00-data-basics-for-beginners.md#amazon-comprehend)**: <b>det</b>ect <b>a</b>nd <b>red</b>act PII <b>i</b>n <b>fr</b>ee <b>te</b>xt.
- **QuickSight**: <b>col</b>umn-<b>lev</b>el <b>secu</b>rity.
- **Macie** **finds** PII <b>i</b>n S3 <b>b</b>ut **does not mask** <b>i</b>t.

### Encryption with KMS (skill 4.3.2)

**KMS key types:**

| <b>K</b>ey | <b>W</b>ho <b>mana</b>ges | <b>K</b>ey <b>pol</b>icy <b>edit</b>able | <b>Cro</b>ss-<b>acco</b>unt <b>usa</b>ble | <b>Rota</b>tion |
|---|---|---|---|---|
| **AWS owned** | AWS (<b>sha</b>red <b>acr</b>oss <b>acco</b>unts) | ❌ | ❌ | AWS |
| **AWS managed** (`aws/s3`, `aws/redshift`…) | AWS, <b>i</b>n <b>yo</b>ur <b>acco</b>unt | ❌ | ❌ | <b>Autom</b>atic (<b>yea</b>rly) |
| **Customer managed** | <b>Y</b>ou | ✅ | ✅ | <b>Opti</b>onal <b>autom</b>atic (<b>config</b>urable <b>per</b>iod) <b>o</b>r <b>man</b>ual |

- **Envelope encryption**: KMS <b>gener</b>ates <b>a</b> **data key**, <b>da</b>ta <b>i</b>s <b>encry</b>pted <b>loca</b>lly <b>wi</b>th <b>t</b>he <b>da</b>ta <b>k</b>ey, <b>a</b>nd <b>t</b>he <b>da</b>ta <b>k</b>ey <b>i</b>s <b>sto</b>red <b>encry</b>pted <b>wi</b>th <b>t</b>he KMS <b>k</b>ey. <b>Th</b>is <b>kee</b>ps <b>lar</b>ge <b>da</b>ta <b>o</b>ut <b>o</b>f KMS <b>cal</b>ls (KMS <b>encr</b>ypts <b>a</b>t <b>mo</b>st 4 KB <b>dire</b>ctly).
- **Grants**: <b>tempo</b>rary, <b>progra</b>mmatic <b>permis</b>sions <b>t</b>o <b>u</b>se <b>a</b> <b>k</b>ey (<b>us</b>ed <b>b</b>y <b>serv</b>ices <b>li</b>ke <b>Elas</b>tic <b>Blo</b>ck <b>Sto</b>re [EBS], <b>Reds</b>hift).
- **Multi-Region keys**: <b>sa</b>me <b>k</b>ey <b>mate</b>rial <b>i</b>n <b>seve</b>ral <b>Regi</b>ons (<b>f</b>or <b>repli</b>cated <b>encry</b>pted <b>da</b>ta).
- **Imported key material** / **external key store** <b>f</b>or <b>str</b>ict <b>k</b>ey-<b>cont</b>rol <b>requir</b>ements.

**Encryption at rest by service:**

| <b>Serv</b>ice | <b>Opti</b>ons |
|---|---|
| **S3** | **Server-Side Encryption with S3-managed keys [SSE-S3]** (<b>defa</b>ult <b>f</b>or <b>a</b>ll <b>n</b>ew <b>obje</b>cts), **Server-Side Encryption with KMS keys [SSE-KMS]** (<b>aud</b>it <b>k</b>ey <b>u</b>se <b>i</b>n <b>Cloud</b>Trail, <b>k</b>ey <b>poli</b>cies), **DSSE-KMS** (<b>du</b>al-<b>lay</b>er), **Server-Side Encryption with Customer-provided keys (SSE-C)**, <b>cli</b>ent-<b>si</b>de. **S3 Bucket Keys** <b>c</b>ut KMS <b>requ</b>est <b>cos</b>ts <b>f</b>or SSE-KMS. <b>Enfo</b>rce <b>wi</b>th <b>defa</b>ult <b>encry</b>ption + <b>buc</b>ket <b>pol</b>icy. |
| **Redshift** | KMS (<b>o</b>r <b>Hard</b>ware <b>Secu</b>rity <b>Mod</b>ule [HSM]) <b>encry</b>ption <b>f</b>or <b>clus</b>ter, <b>snaps</b>hots, <b>back</b>ups; <b>c</b>an <b>encr</b>ypt <b>a</b>n <b>exis</b>ting <b>clus</b>ter |
| **Glue** | **Security configurations** (<b>encr</b>ypt S3 <b>out</b>put, <b>Cloud</b>Watch <b>lo</b>gs, <b>j</b>ob <b>bookm</b>arks) + **Data Catalog encryption** (<b>meta</b>data <b>a</b>nd <b>conne</b>ction <b>passw</b>ords) |
| **Athena** | <b>Que</b>ry <b>resu</b>lts <b>encry</b>ption (SSE-S3, SSE-KMS, <b>Cli</b>ent-<b>Si</b>de <b>Encry</b>ption <b>wi</b>th KMS <b>ke</b>ys [CSE-KMS]), <b>enfo</b>rced <b>b</b>y **workgroup** |
| **EMR** | **Security configuration**: <b>a</b>t-<b>re</b>st (EBS/<b>loc</b>al <b>di</b>sk, EMR <b>Fi</b>le <b>Sys</b>tem [EMRFS] S3), <b>i</b>n-<b>tran</b>sit (TLS) |
| **Kinesis / Firehose / MSK** | <b>Ser</b>ver-<b>si</b>de <b>encry</b>ption <b>wi</b>th KMS |
| **DynamoDB, RDS, Aurora** | KMS <b>a</b>t <b>re</b>st (RDS <b>encry</b>ption <b>mu</b>st <b>b</b>e <b>cho</b>sen <b>a</b>t <b>crea</b>tion; <b>t</b>o <b>encr</b>ypt <b>a</b>n <b>exis</b>ting DB, <b>snap</b>shot → <b>co</b>py <b>encry</b>pted → <b>rest</b>ore) |

### Cross-account encryption (skill 4.3.3)

<b>T</b>o <b>l</b>et <b>acco</b>unt <b>B</b> <b>re</b>ad KMS-<b>encry</b>pted <b>da</b>ta <b>own</b>ed <b>b</b>y <b>acco</b>unt <b>A</b>:
1. <b>U</b>se <b>a</b> **customer managed key** <b>i</b>n <b>acco</b>unt <b>A</b>. **AWS managed keys (`aws/s3`) can't be shared**, <b>s</b>o <b>obje</b>cts <b>encry</b>pted <b>wi</b>th <b>th</b>em <b>can</b>'t <b>b</b>e <b>decry</b>pted <b>b</b>y <b>anot</b>her <b>acco</b>unt.
2. <b>T</b>he **key policy** <b>i</b>n <b>acco</b>unt <b>A</b> <b>all</b>ows <b>acco</b>unt <b>B</b> (<b>o</b>r <b>a</b> <b>spec</b>ific <b>ro</b>le) `kms:Decrypt` (<b>a</b>nd `kms:GenerateDataKey` <b>f</b>or <b>wri</b>tes, `kms:DescribeKey`).
3. <b>Acco</b>unt <b>B</b>'s **IAM policy** <b>all</b>ows <b>t</b>he <b>sa</b>me KMS <b>acti</b>ons <b>o</b>n <b>th</b>at <b>k</b>ey ARN.
4. <b>T</b>he **resource** (<b>buc</b>ket <b>pol</b>icy, <b>Secr</b>ets <b>Mana</b>ger <b>reso</b>urce <b>pol</b>icy, <b>e</b>tc.) <b>al</b>so <b>all</b>ows <b>acco</b>unt <b>B</b>.

<b>Al</b>so: **cross-account S3 replication** <b>o</b>f SSE-KMS <b>obje</b>cts <b>nee</b>ds <b>t</b>he <b>replic</b>ation <b>ro</b>le <b>t</b>o <b>decr</b>ypt <b>wi</b>th <b>t</b>he <b>sou</b>rce <b>k</b>ey <b>a</b>nd <b>encr</b>ypt <b>wi</b>th <b>t</b>he <b>destin</b>ation <b>k</b>ey. **Redshift cross-Region snapshot copy** <b>o</b>f KMS-<b>encry</b>pted <b>clus</b>ters <b>nee</b>ds <b>a</b> **snapshot copy grant** <b>i</b>n <b>t</b>he <b>destin</b>ation <b>Reg</b>ion.

### Encryption in transit and before transit (skill 4.3.4)

**In transit (TLS):**
- AWS <b>serv</b>ice <b>endpo</b>ints <b>u</b>se <b>Hyper</b>text <b>Tran</b>sfer <b>Prot</b>ocol <b>Sec</b>ure (HTTPS)/TLS. **Enforce** <b>i</b>t <b>wi</b>th <b>buc</b>ket <b>poli</b>cies <b>deny</b>ing <b>requ</b>ests <b>whe</b>re **`aws:SecureTransport` = false**.
- <b>Reds</b>hift: <b>param</b>eter **`require_ssl = true`**. RDS <b>Postg</b>reSQL: **`rds.force_ssl = 1`**. MySQL: `REQUIRE SSL` <b>p</b>er <b>us</b>er. <b>Ja</b>va <b>Data</b>base <b>Connec</b>tivity (JDBC)/[<b>Op</b>en <b>Data</b>base <b>Connec</b>tivity [ODBC]](00-data-basics-for-beginners.md#jdbc-and-odbc): <b>Sec</b>ure <b>Sock</b>ets <b>Lay</b>er (SSL) <b>opti</b>ons.
- EMR <b>secu</b>rity <b>configu</b>ration: <b>i</b>n-<b>tran</b>sit TLS <b>betw</b>een <b>nod</b>es.
- <b>Hyb</b>rid <b>netw</b>orks: <b>Si</b>te-<b>t</b>o-<b>Si</b>te <b>Virt</b>ual <b>Priv</b>ate <b>Netw</b>ork [VPN] (<b>IPs</b>ec), <b>Dir</b>ect <b>Conn</b>ect (+ MACsec <b>o</b>r VPN <b>ov</b>er <b>Dir</b>ect <b>Conn</b>ect [DX]).

**Before transit (client-side encryption):**
- <b>Encr</b>ypt **before** <b>da</b>ta <b>lea</b>ves <b>t</b>he <b>prod</b>ucer, <b>s</b>o AWS <b>on</b>ly <b>ev</b>er <b>sto</b>res <b>ciphe</b>rtext.
- <b>Too</b>ls: **AWS Encryption Software Development Kit (SDK)**, **Amazon S3 Encryption Client**, **AWS Database Encryption SDK** (<b>Dyna</b>moDB <b>attri</b>bute-<b>lev</b>el <b>encry</b>ption), <b>usi</b>ng KMS <b>ke</b>ys (CSE-KMS).
- <b>U</b>se <b>wh</b>en <b>t</b>he <b>requir</b>ement <b>sa</b>ys <b>da</b>ta <b>mu</b>st <b>b</b>e <b>encry</b>pted **before it is sent** <b>o</b>r AWS <b>mu</b>st <b>nev</b>er <b>s</b>ee <b>plain</b>text.

---

## Task 4.4: Prepare logs for audit

### CloudTrail (skill 4.4.1)

- **Management events** (<b>cont</b>rol <b>pla</b>ne: `CreateTable`, `PutBucketPolicy`, `StartJobRun`) <b>a</b>re <b>reco</b>rded <b>b</b>y <b>defa</b>ult <b>a</b>nd <b>visi</b>ble <b>f</b>or **90 days** <b>i</b>n <b>Eve</b>nt <b>hist</b>ory.
- **Data events** (<b>da</b>ta <b>pla</b>ne: S3 `GetObject`/`PutObject`, <b>Lam</b>bda `Invoke`, <b>Dyna</b>moDB <b>it</b>em-<b>lev</b>el, <b>Gl</b>ue/<b>La</b>ke <b>Forma</b>tion <b>da</b>ta <b>acc</b>ess…) <b>mu</b>st <b>b</b>e **enabled on a trail or event data store**. <b>U</b>se <b>adva</b>nced <b>eve</b>nt <b>selec</b>tors <b>t</b>o <b>lim</b>it <b>co</b>st.
- **Trails**: <b>deli</b>ver <b>lo</b>gs <b>t</b>o S3 (<b>a</b>nd <b>optio</b>nally <b>Cloud</b>Watch <b>Lo</b>gs) <b>f</b>or <b>lo</b>ng-<b>te</b>rm <b>reten</b>tion; **organization trails** <b>cov</b>er <b>a</b>ll <b>acco</b>unts; **log file integrity validation** <b>dete</b>cts <b>tampe</b>ring; <b>encr</b>ypt <b>wi</b>th KMS; <b>prot</b>ect <b>t</b>he <b>l</b>og <b>buc</b>ket <b>wi</b>th <b>Obj</b>ect <b>Lo</b>ck / <b>restr</b>icted <b>buc</b>ket <b>pol</b>icy.
- **Insights events**: <b>det</b>ect <b>unus</b>ual API <b>ca</b>ll <b>rat</b>es.
- **Lake Formation** <b>reco</b>rds <b>da</b>ta <b>acc</b>ess (<b>whi</b>ch <b>princ</b>ipal <b>acce</b>ssed <b>whi</b>ch <b>tab</b>le/<b>colu</b>mns) <b>i</b>n <b>Cloud</b>Trail.

### CloudWatch Logs for application logs (skill 4.4.2)

- <b>Applic</b>ations <b>a</b>nd <b>serv</b>ices <b>wri</b>te <b>t</b>o **log groups**. <b>S</b>et **retention**, **KMS encryption**, <b>a</b>nd **resource policies**.
- <b>Lam</b>bda, <b>Gl</b>ue, EMR (<b>opti</b>onal), MWAA, [<b>St</b>ep <b>Funct</b>ions](00-data-basics-for-beginners.md#aws-step-functions), API <b>Gate</b>way, <b>a</b>nd <b>Reds</b>hift <b>aud</b>it <b>lo</b>gs <b>c</b>an <b>a</b>ll <b>se</b>nd <b>t</b>o <b>Cloud</b>Watch <b>Lo</b>gs.
- <b>Centr</b>alize <b>acr</b>oss <b>acco</b>unts <b>wi</b>th **subscription filters** → <b>Fire</b>hose → S3 <b>i</b>n <b>a</b> <b>l</b>og <b>arch</b>ive <b>acco</b>unt, <b>o</b>r <b>cro</b>ss-<b>acco</b>unt <b>l</b>og <b>shar</b>ing.

### CloudTrail Lake (skill 4.4.3)

- <b>A</b> **managed, immutable event data store** <b>f</b>or <b>Cloud</b>Trail <b>eve</b>nts (<b>al</b>so AWS <b>Con</b>fig <b>ite</b>ms, <b>aud</b>it <b>eve</b>nts <b>fr</b>om <b>outs</b>ide AWS) <b>wi</b>th <b>lo</b>ng <b>reten</b>tion <b>opti</b>ons.
- <b>Que</b>ry <b>wi</b>th **[Structured Query Language [SQL]](00-data-basics-for-beginners.md#sql)** <b>dire</b>ctly <b>i</b>n <b>t</b>he <b>cons</b>ole <b>o</b>r API. <b>N</b>o S3 <b>tab</b>les, <b>parti</b>tions, <b>o</b>r <b>Ath</b>ena <b>set</b>up <b>requ</b>ired.
- <b>C</b>an <b>coll</b>ect <b>fr</b>om **all accounts in an organization** → <b>centra</b>lized <b>aud</b>it <b>quer</b>ies ("<b>Whi</b>ch <b>use</b>rs <b>cal</b>led `DeleteTable` <b>acr</b>oss <b>a</b>ll <b>acco</b>unts <b>i</b>n <b>t</b>he <b>la</b>st 6 <b>mon</b>ths?").

### Analyzing logs (skills 4.4.4, 4.4.5)

| <b>Ne</b>ed | <b>To</b>ol |
|---|---|
| <b>A</b>d-<b>h</b>oc <b>quer</b>ies <b>o</b>n <b>Cloud</b>Watch <b>l</b>og <b>gro</b>ups | **CloudWatch Logs Insights** |
| SQL <b>ov</b>er <b>Cloud</b>Trail/VPC <b>Fl</b>ow/S3 <b>acc</b>ess <b>lo</b>gs <b>i</b>n S3 | **Athena** (<b>cre</b>ate <b>tab</b>le <b>fr</b>om <b>t</b>he <b>Cloud</b>Trail <b>cons</b>ole, <b>u</b>se <b>parti</b>tion <b>proje</b>ction) |
| <b>Re</b>al-<b>ti</b>me <b>sea</b>rch, <b>dashb</b>oards, <b>aler</b>ting <b>o</b>n <b>lo</b>gs | **OpenSearch Service** (<b>ing</b>est <b>wi</b>th <b>Fire</b>hose <b>o</b>r <b>OpenS</b>earch <b>Inges</b>tion) |
| SQL <b>ov</b>er <b>Cloud</b>Trail <b>eve</b>nts <b>wi</b>th <b>n</b>o <b>set</b>up | **CloudTrail Lake** |
| **Very large log volumes**, <b>comp</b>lex <b>proce</b>ssing | **EMR** ([<b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark) <b>ov</b>er <b>lo</b>gs <b>i</b>n S3) |
| <b>Secu</b>rity <b>find</b>ings <b>correl</b>ation | <b>Secu</b>rity <b>H</b>ub, <b>Guard</b>Duty (<b>bey</b>ond <b>co</b>re <b>sco</b>pe) |

---

## Task 4.5: Understand data privacy and governance

### Data sharing permissions (skill 4.5.1)

**Redshift data sharing:**
- <b>T</b>he <b>prod</b>ucer <b>crea</b>tes <b>a</b> **datashare**, <b>ad</b>ds <b>sche</b>mas/<b>tab</b>les/<b>vie</b>ws/<b>Us</b>er-<b>Defi</b>ned <b>Funct</b>ions (UDFs), <b>a</b>nd <b>gra</b>nts <b>i</b>t <b>t</b>o <b>a</b> <b>cons</b>umer **namespace** (<b>sa</b>me <b>acco</b>unt), **AWS account** (<b>cro</b>ss-<b>acco</b>unt: <b>t</b>he <b>prod</b>ucer <b>acco</b>unt <b>mu</b>st **authorize** <b>i</b>t <b>a</b>nd <b>t</b>he <b>cons</b>umer <b>acco</b>unt <b>mu</b>st **associate** <b>i</b>t), <b>o</b>r <b>Reg</b>ion.
- <b>T</b>he <b>cons</b>umer <b>crea</b>tes <b>a</b> **database from the datashare** <b>a</b>nd <b>quer</b>ies **live data with no copies** <b>a</b>nd <b>n</b>o ETL. <b>Cons</b>umer <b>comp</b>ute <b>pa</b>ys <b>f</b>or <b>i</b>ts <b>quer</b>ies.
- <b>Requ</b>ires **RA3 or Redshift Serverless**. <b>C</b>an <b>b</b>e **managed by Lake Formation** (<b>centra</b>lized <b>fi</b>ne-<b>grai</b>ned <b>permis</b>sions <b>o</b>n <b>t</b>he <b>sha</b>red <b>da</b>ta) <b>o</b>r <b>sha</b>red <b>v</b>ia **[AWS Data Exchange](00-data-basics-for-beginners.md#aws-data-exchange)** (<b>pa</b>id/<b>lice</b>nsed <b>shar</b>ing).
- <b>Mul</b>ti-<b>wareh</b>ouse **writes** <b>a</b>re <b>suppo</b>rted <b>f</b>or <b>work</b>load <b>isola</b>tion.

**Other sharing mechanisms:** <b>La</b>ke <b>Forma</b>tion <b>cro</b>ss-<b>acco</b>unt <b>gra</b>nts (<b>v</b>ia RAM), S3 <b>buc</b>ket <b>poli</b>cies/<b>Acc</b>ess <b>Poi</b>nts, AWS <b>Da</b>ta <b>Exch</b>ange (<b>subsc</b>ribe/<b>lice</b>nse <b>exte</b>rnal <b>da</b>ta), **AWS Clean Rooms** (<b>collabo</b>rative <b>anal</b>ysis <b>with</b>out <b>shar</b>ing <b>r</b>aw <b>da</b>ta), <b>SageM</b>aker <b>Cata</b>log <b>subscri</b>ptions.

### PII identification (skill 4.5.2)

**Amazon Macie:**
- <b>Us</b>es <b>Mach</b>ine <b>Lear</b>ning (ML) <b>a</b>nd <b>patt</b>ern <b>matc</b>hing <b>t</b>o <b>disc</b>over <b>sensi</b>tive <b>da</b>ta **in S3**: **managed data identifiers** (<b>nam</b>es, <b>addre</b>sses, <b>cre</b>dit <b>car</b>ds, <b>pass</b>port <b>numb</b>ers, <b>creden</b>tials…) <b>pl</b>us **custom data identifiers** (<b>reg</b>ex + <b>keyw</b>ords <b>f</b>or <b>yo</b>ur <b>o</b>wn <b>form</b>ats <b>li</b>ke <b>empl</b>oyee IDs).
- **Automated sensitive data discovery** (<b>conti</b>nuous <b>samp</b>ling <b>acr</b>oss <b>buck</b>ets) <b>o</b>r <b>targ</b>eted **sensitive data discovery jobs** (<b>o</b>ne-<b>ti</b>me <b>o</b>r <b>sched</b>uled).
- <b>Al</b>so <b>evalu</b>ates <b>buc</b>ket <b>secu</b>rity (<b>pub</b>lic, <b>unencr</b>ypted, <b>sha</b>red).
- **Findings** <b>g</b>o <b>t</b>o [<b>EventB</b>ridge](00-data-basics-for-beginners.md#amazon-eventbridge) <b>a</b>nd <b>Secu</b>rity <b>H</b>ub, <b>whi</b>ch <b>c</b>an <b>trig</b>ger <b>remedi</b>ation.

**Macie + Lake Formation pattern:**

```
Macie job scans the S3 data lake ──► finding: PII in s3://lake/customers/ (column-level details)
   └─► EventBridge ──► Lambda ──► apply LF-tag classification=PII to the table/columns
                                     └─► Lake Formation grants: only roles with PII clearance can SELECT those columns
```

<b>Oth</b>er PII <b>detec</b>tion: **Glue sensitive data detection** (<b>ins</b>ide ETL), **Comprehend** (<b>fr</b>ee <b>te</b>xt), **DataBrew** PII <b>detec</b>tion.

### Preventing backups/replication to disallowed Regions (skill 4.5.3)

- **SCPs** <b>i</b>n AWS <b>Organiz</b>ations: <b>de</b>ny <b>a</b>ll <b>acti</b>ons <b>outs</b>ide <b>appr</b>oved <b>Regi</b>ons <b>usi</b>ng **`aws:RequestedRegion`** (<b>exe</b>mpt <b>glo</b>bal <b>serv</b>ices). <b>Th</b>is <b>blo</b>cks <b>crea</b>ting <b>resou</b>rces, <b>snap</b>shot <b>cop</b>ies, <b>a</b>nd <b>repl</b>icas <b>elsew</b>here.
- <b>De</b>ny <b>spec</b>ific <b>acti</b>ons: `s3:PutReplicationConfiguration` (<b>o</b>r <b>lim</b>it <b>allo</b>wed <b>destin</b>ation <b>buck</b>ets), `rds:CopyDBSnapshot`/<b>cro</b>ss-<b>Reg</b>ion <b>re</b>ad <b>repl</b>icas, `redshift:EnableSnapshotCopy`, <b>Dyna</b>moDB <b>glo</b>bal <b>tab</b>le <b>repl</b>ica <b>crea</b>tion, `backup:StartCopyJob` <b>t</b>o <b>disal</b>lowed <b>vau</b>lts.
- **AWS Backup**: <b>organi</b>zation **backup policies** <b>th</b>at <b>def</b>ine <b>whe</b>re <b>cop</b>ies <b>g</b>o; <b>vau</b>lt <b>acc</b>ess <b>poli</b>cies.
- **AWS Control Tower** <b>Reg</b>ion <b>de</b>ny <b>cont</b>rol (<b>appl</b>ies <b>t</b>he <b>sa</b>me <b>Serv</b>ice <b>Cont</b>rol <b>Pol</b>icy [SCP] <b>appr</b>oach <b>a</b>t <b>sca</b>le).
- **KMS**: <b>sin</b>gle-<b>Reg</b>ion <b>cust</b>omer <b>mana</b>ged <b>ke</b>ys <b>me</b>an <b>da</b>ta <b>encry</b>pted <b>wi</b>th <b>th</b>em <b>can</b>'t <b>b</b>e <b>decry</b>pted <b>elsew</b>here.

### Viewing configuration changes with AWS Config (skill 4.5.4)

- <b>Reco</b>rds **configuration items** <b>f</b>or <b>resou</b>rces (S3 <b>buck</b>ets, <b>Reds</b>hift <b>clus</b>ters, <b>secu</b>rity <b>gro</b>ups, IAM, KMS <b>ke</b>ys…) <b>a</b>nd <b>kee</b>ps <b>a</b> **timeline of changes**, <b>lin</b>ked <b>t</b>o <b>t</b>he <b>Cloud</b>Trail <b>eve</b>nt <b>th</b>at <b>cau</b>sed <b>ea</b>ch <b>cha</b>nge.
- **Config rules** (<b>mana</b>ged, <b>e</b>.g., `s3-bucket-server-side-encryption-enabled`, `redshift-cluster-public-access-check`, <b>o</b>r <b>cus</b>tom) <b>eval</b>uate <b>compl</b>iance <b>contin</b>uously; **conformance packs** <b>bun</b>dle <b>rul</b>es.
- **Remediation** <b>v</b>ia <b>Syst</b>ems <b>Mana</b>ger <b>Autom</b>ation <b>docum</b>ents.
- **Aggregators** <b>gi</b>ve <b>a</b> <b>mul</b>ti-<b>acco</b>unt, <b>mul</b>ti-<b>Reg</b>ion <b>compl</b>iance <b>vi</b>ew.

> <b>Cloud</b>Trail = **who did what (API call)**. <b>Con</b>fig = **what the resource looked like before and after, and whether it's compliant**.

### Data sovereignty (skill 4.5.5)

**Data sovereignty** = <b>da</b>ta <b>i</b>s <b>subj</b>ect <b>t</b>o <b>t</b>he <b>la</b>ws <b>o</b>f <b>t</b>he <b>coun</b>try <b>whe</b>re <b>it</b>'s <b>sto</b>red. <b>Requir</b>ements <b>oft</b>en <b>me</b>an <b>da</b>ta (<b>a</b>nd <b>somet</b>imes <b>ke</b>ys <b>a</b>nd <b>opera</b>tors) <b>mu</b>st <b>st</b>ay <b>i</b>n <b>a</b> <b>spec</b>ific <b>coun</b>try <b>o</b>r <b>jurisd</b>iction.

<b>H</b>ow <b>t</b>o <b>main</b>tain <b>i</b>t <b>o</b>n AWS:
- <b>Cho</b>ose <b>Regi</b>ons <b>i</b>n <b>t</b>he <b>requ</b>ired <b>coun</b>try; **restrict other Regions** <b>wi</b>th SCPs (`aws:RequestedRegion`).
- <b>Blo</b>ck <b>cro</b>ss-<b>Reg</b>ion <b>replic</b>ation, <b>snap</b>shot <b>co</b>py, <b>a</b>nd <b>glo</b>bal <b>tab</b>les <b>t</b>o <b>oth</b>er <b>jurisdi</b>ctions (<b>s</b>ee 4.5.3).
- <b>Ke</b>ep **KMS keys in-Region** (<b>o</b>r <b>cust</b>omer-<b>contr</b>olled <b>k</b>ey <b>sto</b>res/<b>Hard</b>ware <b>Secu</b>rity <b>Modu</b>les [HSMs] <b>f</b>or <b>stri</b>cter <b>cont</b>rol).
- <b>Wat</b>ch <b>f</b>or <b>serv</b>ices <b>th</b>at <b>mo</b>ve <b>da</b>ta (<b>cro</b>ss-<b>Reg</b>ion <b>infer</b>ence <b>i</b>n [<b>Bedr</b>ock](00-data-basics-for-beginners.md#amazon-bedrock), <b>Cloud</b>Front <b>cach</b>ing, <b>glo</b>bal <b>tab</b>les) <b>a</b>nd <b>confi</b>gure <b>th</b>em <b>f</b>or <b>i</b>n-<b>coun</b>try <b>u</b>se.
- <b>U</b>se **AWS Local Zones / Outposts / Dedicated Local Zones** <b>wh</b>en <b>n</b>o <b>Reg</b>ion <b>exi</b>sts <b>i</b>n <b>t</b>he <b>requ</b>ired <b>loca</b>tion.
- <b>U</b>se AWS <b>Con</b>fig <b>rul</b>es <b>a</b>nd <b>Mac</b>ie/<b>Cloud</b>Trail <b>t</b>o <b>pro</b>ve <b>compl</b>iance.

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

<b>K</b>ey <b>poi</b>nts:
- <b>Acc</b>ess <b>i</b>s <b>gran</b>ted <b>t</b>o **projects**, <b>n</b>ot <b>t</b>o <b>indiv</b>idual <b>use</b>rs, <b>s</b>o <b>te</b>am <b>membe</b>rship <b>chan</b>ges <b>don</b>'t <b>requ</b>ire <b>n</b>ew <b>gra</b>nts.
- <b>Subscri</b>ptions <b>a</b>re **auditable** (<b>w</b>ho <b>reque</b>sted, <b>w</b>ho <b>appr</b>oved, <b>wh</b>en).
- <b>Dom</b>ain <b>uni</b>ts <b>c</b>an <b>s</b>et **policies** <b>contro</b>lling <b>w</b>ho <b>c</b>an <b>publ</b>ish <b>a</b>nd <b>w</b>ho <b>c</b>an <b>appr</b>ove.

### 🆕 Governance frameworks and data sharing patterns (skill 4.5.7)

**Governance frameworks:**

| <b>Mod</b>el | <b>H</b>ow <b>i</b>t <b>wor</b>ks | <b>Pr</b>os / <b>co</b>ns |
|---|---|---|
| **Centralized** | <b>O</b>ne <b>cent</b>ral <b>da</b>ta <b>te</b>am <b>ow</b>ns <b>t</b>he <b>la</b>ke/<b>wareh</b>ouse, <b>inges</b>tion, <b>a</b>nd <b>a</b>ll <b>permis</b>sions | <b>Consi</b>stent <b>a</b>nd <b>sim</b>ple; <b>cent</b>ral <b>te</b>am <b>beco</b>mes <b>a</b> <b>bottl</b>eneck |
| **Decentralized / data mesh** | **Domain teams own their data as products** (<b>th</b>ey <b>publ</b>ish <b>t</b>o <b>a</b> <b>cata</b>log); <b>a</b> **central governance** <b>lay</b>er <b>se</b>ts <b>stand</b>ards (<b>cata</b>log, <b>poli</b>cies, <b>secu</b>rity) | <b>Sca</b>les <b>wi</b>th <b>t</b>he <b>organi</b>zation; <b>nee</b>ds <b>str</b>ong <b>stand</b>ards <b>a</b>nd <b>a</b> <b>cata</b>log |
| **Federated / hub-and-spoke** | <b>Cent</b>ral **governance/catalog account** + **producer** <b>a</b>nd **consumer** <b>acco</b>unts; <b>La</b>ke <b>Forma</b>tion + RAM <b>sha</b>re <b>tab</b>les <b>acr</b>oss <b>acco</b>unts; <b>SageM</b>aker <b>Cata</b>log <b>f</b>or <b>disco</b>very <b>a</b>nd <b>subscri</b>ptions | AWS's <b>refer</b>ence <b>archit</b>ecture <b>f</b>or <b>mul</b>ti-<b>acco</b>unt <b>da</b>ta <b>platf</b>orms |

<b>A</b> <b>gover</b>nance <b>frame</b>work <b>cov</b>ers **ownership/stewardship**, **classification** (<b>pub</b>lic, <b>inte</b>rnal, <b>confid</b>ential, PII), **access policies**, **quality standards**, **[lineage](00-data-basics-for-beginners.md#data-lineage)**, **lifecycle/retention**, <b>a</b>nd **auditing**.

**Data sharing patterns:**

| <b>Patt</b>ern | <b>Exam</b>ple | <b>Tra</b>de-<b>o</b>ff |
|---|---|---|
| **Copy/replicate** | ETL <b>in</b>to <b>a</b> <b>consu</b>mer's <b>buc</b>ket/<b>wareh</b>ouse, S3 <b>replic</b>ation | <b>Indepe</b>ndent <b>cop</b>ies; <b>duplic</b>ation, <b>stale</b>ness, <b>har</b>der <b>gover</b>nance |
| **Zero-copy, in-place sharing** | <b>Reds</b>hift <b>da</b>ta <b>shar</b>ing, <b>La</b>ke <b>Forma</b>tion <b>cro</b>ss-<b>acco</b>unt <b>gra</b>nts, S3 <b>Acc</b>ess <b>Poi</b>nts | <b>Li</b>ve <b>da</b>ta, <b>n</b>o <b>duplic</b>ation, <b>cent</b>ral <b>cont</b>rol |
| **Publish/subscribe via catalog** | <b>SageM</b>aker <b>Cata</b>log <b>subscri</b>ptions | <b>Se</b>lf-<b>serv</b>ice <b>wi</b>th <b>appr</b>oval <b>a</b>nd <b>aud</b>it |
| **Marketplace / licensed** | AWS <b>Da</b>ta <b>Exch</b>ange | <b>Mone</b>tize <b>o</b>r <b>cons</b>ume <b>thi</b>rd-<b>par</b>ty <b>da</b>ta |
| **Privacy-preserving collaboration** | AWS <b>Cle</b>an <b>Roo</b>ms | <b>Joi</b>nt <b>anal</b>ysis <b>with</b>out <b>expo</b>sing <b>r</b>aw <b>reco</b>rds |

---

## Gotchas and exam traps

- **Apps should use IAM roles** (<b>tempo</b>rary <b>creden</b>tials), <b>n</b>ot IAM <b>us</b>er <b>acc</b>ess <b>ke</b>ys.
- **Glue can't connect in a VPC** → <b>miss</b>ing **self-referencing security group** <b>ru</b>le.
- **"AccessDenied when creating a Glue job / Lambda with a role"** → <b>miss</b>ing **`iam:PassRole`**.
- **Automatic credential rotation** → **Secrets Manager** (<b>n</b>ot <b>Param</b>eter <b>Sto</b>re).
- **Managed policy too broad** → **customer managed policy** <b>wi</b>th <b>spec</b>ific <b>acti</b>ons, ARNs, <b>a</b>nd <b>condi</b>tions; <b>gene</b>rate <b>i</b>t <b>fr</b>om <b>acti</b>vity <b>wi</b>th **IAM Access Analyzer**.
- **S3 `ListBucket`** <b>go</b>es <b>o</b>n <b>t</b>he **bucket ARN**, **`GetObject`** <b>o</b>n **`bucket/*`**.
- **SCPs and permission boundaries never grant** <b>permis</b>sions; <b>th</b>ey <b>on</b>ly <b>lim</b>it. **Explicit Deny wins.**
- **Table/column/row permissions across Athena, Redshift Spectrum, EMR** → **Lake Formation** (<b>da</b>ta <b>filt</b>ers <b>f</b>or <b>r</b>ow/<b>ce</b>ll, LF-<b>ta</b>gs <b>f</b>or <b>sca</b>le).
- **Thousands of tables, new ones should inherit access** → **LF-TBAC (LF-tags)**.
- **Fewer IAM policies across many projects/teams** → **ABAC** <b>wi</b>th <b>princ</b>ipal/<b>reso</b>urce <b>ta</b>gs.
- **Analysts see masked Social Security Numbers (SSNs), auditors see full values in Redshift** → **dynamic data masking**.
- **Macie finds PII; it doesn't mask it.**
- **Cross-account decrypt fails** → <b>da</b>ta <b>encry</b>pted <b>wi</b>th <b>a</b>n **AWS managed key** (`aws/s3`) <b>can</b>'t <b>b</b>e <b>sha</b>red. <b>U</b>se <b>a</b> **customer managed key** + <b>k</b>ey <b>pol</b>icy + IAM.
- **Reduce SSE-KMS request costs** → **S3 Bucket Keys**.
- **Enforce TLS to S3** → <b>buc</b>ket <b>pol</b>icy <b>de</b>ny <b>o</b>n **`aws:SecureTransport` = false**. <b>Reds</b>hift → **`require_ssl`**.
- **Encrypt before sending to AWS** → **client-side encryption** (<b>Encry</b>ption SDK / S3 <b>Encry</b>ption <b>Cli</b>ent).
- **RDS encryption can't be turned on in place** → <b>snap</b>shot, <b>co</b>py <b>encry</b>pted, <b>rest</b>ore.
- **S3 object-level access auditing** → **CloudTrail data events** (<b>n</b>ot <b>o</b>n <b>b</b>y <b>defa</b>ult).
- **Centralized SQL over CloudTrail across the org, no setup** → **CloudTrail Lake**.
- **"Who changed it?"** → <b>Cloud</b>Trail. **"What was the configuration and is it compliant?"** → **AWS Config**.
- **Share live Redshift data with another account, no copies** → **Redshift data sharing** (RA3/<b>Serve</b>rless; <b>autho</b>rize + <b>assoc</b>iate).
- **Block backups/replicas outside approved Regions** → **SCP with `aws:RequestedRegion`** (+ <b>de</b>ny <b>replic</b>ation/<b>snap</b>shot-<b>co</b>py <b>acti</b>ons).
- **SageMaker Catalog access is granted to projects** <b>v</b>ia <b>subscr</b>iption <b>appr</b>oval, <b>n</b>ot <b>indiv</b>idual <b>use</b>rs.
- **Domain teams own data products with central governance** → **data mesh** (<b>feder</b>ated, <b>h</b>ub-<b>a</b>nd-<b>spo</b>ke <b>o</b>n AWS).

---

## Quick-recall summary

- <b>Dom</b>ain <b>wei</b>ght **18%**. <b>Tas</b>ks: <b>authent</b>ication (4.1), <b>authori</b>zation (4.2), <b>encry</b>ption/<b>mask</b>ing (4.3), <b>aud</b>it <b>lo</b>gs (4.4), <b>priv</b>acy/<b>gover</b>nance (4.5).
- <b>Au</b>th <b>meth</b>ods: <b>pass</b>word, <b>certif</b>icate, **role-based (STS temporary credentials)**; <b>Iden</b>tity <b>Cen</b>ter <b>f</b>or <b>workf</b>orce.
- **Security groups** <b>stat</b>eful, <b>all</b>ow-<b>on</b>ly, <b>c</b>an <b>refer</b>ence <b>Secu</b>rity <b>Gro</b>ups (SGs); **Network Access Control Lists (NACLs)** <b>state</b>less, <b>all</b>ow + <b>de</b>ny.
- <b>Rol</b>es: <b>tru</b>st <b>pol</b>icy + <b>permis</b>sions; <b>Lam</b>bda <b>execu</b>tion <b>ro</b>le, <b>Gl</b>ue <b>serv</b>ice <b>ro</b>le, <b>CloudFo</b>rmation <b>serv</b>ice <b>ro</b>le, EC2 <b>inst</b>ance <b>prof</b>ile; **`iam:PassRole`**.
- **VPC endpoints**: <b>gate</b>way (S3, <b>Dyna</b>moDB) <b>v</b>s <b>inter</b>face (<b>Privat</b>eLink); <b>endp</b>oint <b>poli</b>cies; `aws:SourceVpce`.
- **S3 Access Points**: <b>p</b>er-<b>a</b>pp <b>poli</b>cies, VPC-<b>on</b>ly <b>opt</b>ion.
- **Secrets Manager** (<b>rota</b>tion, <b>cro</b>ss-<b>acco</b>unt) <b>v</b>s **Parameter Store** (<b>Secure</b>String, <b>fr</b>ee, <b>n</b>o <b>rota</b>tion); <b>Reds</b>hift/RDS IAM-<b>bas</b>ed <b>tempo</b>rary <b>creden</b>tials.
- <b>Mana</b>ged <b>v</b>s <b>unman</b>aged = <b>h</b>ow <b>mu</b>ch <b>o</b>f <b>t</b>he <b>sha</b>red <b>respons</b>ibility AWS <b>carr</b>ies.
- **SageMaker Unified Studio**: **domain** (<b>t</b>op <b>boun</b>dary, <b>Iden</b>tity <b>Cen</b>ter) → **domain units** (<b>hiera</b>rchy + <b>poli</b>cies) → **projects** (<b>te</b>am <b>works</b>pace, <b>o</b>wn IAM <b>ro</b>le, <b>un</b>it <b>o</b>f <b>acc</b>ess).
- <b>Poli</b>cies: AWS <b>mana</b>ged <b>v</b>s <b>cust</b>omer <b>mana</b>ged <b>v</b>s <b>inl</b>ine; <b>lea</b>st <b>privi</b>lege <b>v</b>ia <b>acti</b>ons + ARNs + <b>condi</b>tions; **IAM Access Analyzer**; SCPs/<b>bound</b>aries <b>lim</b>it <b>on</b>ly; <b>expl</b>icit <b>De</b>ny <b>wi</b>ns.
- **Redshift**: RBAC <b>rol</b>es, GRANT <b>t</b>o <b>col</b>umn <b>lev</b>el, <b>defa</b>ult <b>privi</b>leges, **RLS**, **dynamic data masking**, <b>Iden</b>tity <b>Cen</b>ter.
- **Lake Formation**: <b>regi</b>ster S3, <b>gra</b>nts <b>o</b>n <b>d</b>b/<b>tab</b>le/<b>col</b>umn, **data filters** (<b>r</b>ow/<b>ce</b>ll), **LF-tags (TBAC)**, <b>cro</b>ss-<b>acco</b>unt <b>v</b>ia RAM + <b>reso</b>urce <b>lin</b>ks, <b>IAMAllowed</b>Principals.
- RBAC (<b>rol</b>es) <b>v</b>s TBAC (LF-<b>ta</b>gs) <b>v</b>s **ABAC** (<b>princ</b>ipal <b>t</b>ag = <b>reso</b>urce <b>t</b>ag).
- <b>Mask</b>ing/<b>anonymi</b>zation: <b>red</b>act, <b>ha</b>sh, <b>toke</b>nize, <b>encr</b>ypt, <b>gener</b>alize; <b>pseudon</b>ymized ≠ <b>anony</b>mized; <b>too</b>ls = <b>Reds</b>hift <b>Dyna</b>mic <b>Da</b>ta <b>Mask</b>ing (DDM), <b>La</b>ke <b>Forma</b>tion (LF), <b>Gl</b>ue <b>sensi</b>tive <b>da</b>ta <b>detec</b>tion, <b>Data</b>Brew, <b>Compr</b>ehend.
- **KMS**: AWS <b>own</b>ed / AWS <b>mana</b>ged / **customer managed** (<b>on</b>ly <b>Cust</b>omer <b>Mana</b>ged <b>K</b>ey [CMK] <b>i</b>s <b>share</b>able <b>cro</b>ss-<b>acco</b>unt, <b>edit</b>able <b>pol</b>icy); <b>enve</b>lope <b>encry</b>ption; <b>gra</b>nts; <b>mul</b>ti-<b>Reg</b>ion <b>ke</b>ys.
- S3 <b>a</b>t <b>re</b>st: **SSE-S3 default**, SSE-KMS (+ **Bucket Keys**), DSSE-KMS, SSE-<b>C</b>, <b>cli</b>ent-<b>si</b>de.
- <b>Serv</b>ice <b>encry</b>ption: <b>Gl</b>ue <b>secu</b>rity <b>configu</b>rations + <b>cata</b>log <b>encry</b>ption, <b>Ath</b>ena <b>workg</b>roup <b>res</b>ult <b>encry</b>ption, EMR <b>secu</b>rity <b>configu</b>rations, <b>Reds</b>hift KMS, RDS <b>a</b>t <b>crea</b>tion <b>on</b>ly.
- <b>Cro</b>ss-<b>acco</b>unt: CMK <b>k</b>ey <b>pol</b>icy + <b>cons</b>umer IAM + <b>reso</b>urce <b>pol</b>icy; <b>Reds</b>hift <b>snap</b>shot <b>co</b>py <b>gra</b>nt.
- <b>Tran</b>sit: TLS, **`aws:SecureTransport`**, `require_ssl`, `rds.force_ssl`; **before transit = client-side encryption**.
- **CloudTrail**: <b>manag</b>ement <b>eve</b>nts <b>defa</b>ult (90 <b>da</b>ys), **data events opt-in**, <b>tra</b>ils/<b>o</b>rg <b>tra</b>ils, <b>integ</b>rity <b>valid</b>ation; **CloudTrail Lake** = SQL, <b>cent</b>ral, <b>immut</b>able.
- **CloudWatch Logs**: <b>reten</b>tion, KMS, <b>subscri</b>ptions <b>t</b>o <b>centr</b>alize.
- <b>L</b>og <b>anal</b>ysis: <b>Lo</b>gs <b>Insi</b>ghts, <b>Ath</b>ena, <b>OpenS</b>earch, <b>Cloud</b>Trail <b>La</b>ke, **EMR for huge volumes**.
- **Redshift data sharing**: <b>datas</b>hare → <b>cons</b>umer <b>data</b>base, <b>n</b>o <b>co</b>py, RA3/<b>Serve</b>rless, <b>cro</b>ss-<b>acco</b>unt <b>autho</b>rize + <b>assoc</b>iate, LF-<b>mana</b>ged <b>o</b>r <b>Da</b>ta <b>Exch</b>ange.
- **Macie**: <b>mana</b>ged + <b>cus</b>tom <b>identi</b>fiers, <b>autom</b>ated <b>disco</b>very, <b>find</b>ings → <b>EventB</b>ridge → <b>t</b>ag <b>i</b>n **Lake Formation**.
- <b>Reg</b>ion <b>restri</b>ction: **SCP `aws:RequestedRegion`**, <b>de</b>ny <b>replic</b>ation/<b>snap</b>shot <b>co</b>py, <b>Bac</b>kup <b>poli</b>cies, <b>Cont</b>rol <b>Tow</b>er.
- **AWS Config**: <b>configu</b>ration <b>time</b>line, <b>rul</b>es, <b>confor</b>mance <b>pac</b>ks, <b>aggreg</b>ators, <b>remedi</b>ation.
- <b>Sovere</b>ignty: <b>i</b>n-<b>coun</b>try <b>Regi</b>ons, SCPs, <b>i</b>n-<b>Reg</b>ion <b>ke</b>ys, <b>n</b>o <b>cro</b>ss-<b>Reg</b>ion <b>replic</b>ation, <b>Loc</b>al <b>Zon</b>es/<b>Outp</b>osts.
- **SageMaker Catalog projects**: <b>publ</b>ish → <b>requ</b>est → <b>appr</b>ove → <b>autom</b>atic LF/<b>Reds</b>hift <b>gra</b>nt <b>t</b>o <b>t</b>he <b>proj</b>ect.
- <b>Gover</b>nance: <b>centra</b>lized <b>v</b>s **data mesh** <b>v</b>s <b>h</b>ub-<b>a</b>nd-<b>spo</b>ke; <b>shar</b>ing: <b>co</b>py <b>v</b>s **zero-copy** <b>v</b>s <b>cata</b>log <b>subsc</b>ribe <b>v</b>s <b>Da</b>ta <b>Exch</b>ange <b>v</b>s <b>Cle</b>an <b>Roo</b>ms.
