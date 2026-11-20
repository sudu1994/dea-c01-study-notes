# Data Basics for Beginners

> <b>N</b>ew <b>t</b>o <b>da</b>ta <b>engine</b>ering? <b>Re</b>ad <b>th</b>is <b>fir</b>st. <b>I</b>t <b>expl</b>ains, <b>i</b>n <b>pla</b>in <b>Engl</b>ish, <b>eve</b>ry <b>to</b>ol, <b>fi</b>le <b>for</b>mat <b>a</b>nd <b>id</b>ea <b>t</b>he <b>oth</b>er <b>not</b>es <b>ass</b>ume <b>y</b>ou <b>alre</b>ady <b>kn</b>ow. <b>I</b>n <b>t</b>he <b>not</b>es, <b>t</b>he <b>fir</b>st <b>ment</b>ion <b>o</b>f <b>ea</b>ch <b>to</b>ol <b>lin</b>ks <b>ba</b>ck <b>he</b>re. <b>F</b>or <b>abbrevi</b>ations (JDBC, CDC, ETL…), <b>s</b>ee [00-abbreviations-glossary.md](00-abbreviations-glossary.md).

## The big picture

<b>A</b> <b>da</b>ta <b>engi</b>neer <b>bui</b>lds **pipelines**: <b>autom</b>ated <b>pat</b>hs <b>th</b>at <b>mo</b>ve <b>da</b>ta <b>fr</b>om <b>whe</b>re <b>i</b>t <b>i</b>s <b>crea</b>ted <b>t</b>o <b>whe</b>re <b>peo</b>ple <b>u</b>se <b>i</b>t.

```
 SOURCES                 INGEST              STORE                 TRANSFORM            USE
 apps, databases,  →  stream or batch  →  data lake (S3)    →  clean, join,     →  dashboards, SQL,
 sensors, SaaS,       (Kinesis, Kafka,     warehouse          reshape            ML / AI models,
 files, APIs          DMS, AppFlow…)       (Redshift)         (Glue, Spark, SQL)  other apps
                 └──────────── orchestrated (Step Functions, Airflow) + secured + monitored ────────────┘
```

<b>Mo</b>st <b>ex</b>am <b>quest</b>ions <b>a</b>sk: *<b>whi</b>ch <b>serv</b>ice <b>fi</b>ts <b>th</b>is <b>st</b>ep, <b>wi</b>th <b>t</b>he <b>lea</b>st <b>wo</b>rk, <b>co</b>st <b>o</b>r <b>ri</b>sk?*

---

## Core ideas

### Data pipeline
<b>A</b> <b>repea</b>table, <b>autom</b>ated <b>ser</b>ies <b>o</b>f <b>ste</b>ps <b>th</b>at <b>mov</b>es <b>a</b>nd <b>chan</b>ges <b>da</b>ta, <b>f</b>or <b>exam</b>ple "<b>eve</b>ry <b>nig</b>ht, <b>co</b>py <b>yester</b>day's <b>ord</b>ers <b>fr</b>om <b>t</b>he <b>data</b>base, <b>cle</b>an <b>th</b>em, <b>a</b>nd <b>lo</b>ad <b>th</b>em <b>in</b>to <b>t</b>he <b>wareh</b>ouse."

### Batch vs streaming
- **Batch**: <b>proc</b>ess <b>a</b> <b>pi</b>le <b>o</b>f <b>da</b>ta <b>o</b>n <b>a</b> <b>sche</b>dule (<b>eve</b>ry <b>ho</b>ur, <b>eve</b>ry <b>nig</b>ht). <b>Sim</b>ple <b>a</b>nd <b>che</b>ap.
- **Streaming**: <b>proc</b>ess <b>ea</b>ch <b>rec</b>ord <b>seco</b>nds <b>aft</b>er <b>i</b>t <b>i</b>s <b>crea</b>ted (<b>cli</b>cks, <b>sen</b>sor <b>read</b>ings, <b>paym</b>ents). <b>Nee</b>ded <b>f</b>or "<b>re</b>al <b>ti</b>me" <b>requir</b>ements.
- **Near real time** <b>usua</b>lly <b>mea</b>ns "<b>wit</b>hin <b>a</b> <b>min</b>ute <b>o</b>r <b>s</b>o", <b>f</b>or <b>exam</b>ple <b>Fire</b>hose <b>buffe</b>ring <b>f</b>or 60 <b>seco</b>nds <b>bef</b>ore <b>writ</b>ing.

### ETL and ELT
- **ETL (Extract, Transform, Load)**: <b>ta</b>ke <b>da</b>ta <b>o</b>ut <b>o</b>f <b>a</b> <b>sou</b>rce, <b>cle</b>an/<b>resh</b>ape <b>i</b>t, <b>th</b>en <b>lo</b>ad <b>i</b>t <b>in</b>to <b>t</b>he <b>destin</b>ation.
- **ELT (Extract, Load, Transform)**: <b>lo</b>ad <b>r</b>aw <b>da</b>ta <b>fir</b>st, <b>th</b>en <b>trans</b>form <b>i</b>t *<b>ins</b>ide* <b>t</b>he <b>destin</b>ation (<b>usua</b>lly <b>a</b> <b>wareh</b>ouse, <b>wi</b>th SQL).

### Data lake
<b>A</b> <b>b</b>ig, <b>che</b>ap <b>stor</b>age <b>ar</b>ea (<b>o</b>n AWS: **S3**) <b>hold</b>ing <b>r</b>aw <b>a</b>nd <b>proce</b>ssed <b>fil</b>es <b>o</b>f <b>a</b>ny <b>ty</b>pe: CSV, JSON, <b>Parq</b>uet, <b>ima</b>ges, <b>lo</b>gs. <b>Y</b>ou <b>dec</b>ide <b>t</b>he <b>struc</b>ture <b>wh</b>en <b>y</b>ou <b>re</b>ad <b>i</b>t (*<b>sch</b>ema-<b>o</b>n-<b>re</b>ad*).

### Data warehouse
<b>A</b> <b>data</b>base <b>bui</b>lt <b>f</b>or **analytics**: <b>fa</b>st SQL <b>ov</b>er <b>bill</b>ions <b>o</b>f <b>ro</b>ws, <b>f</b>or <b>repo</b>rts <b>a</b>nd <b>dashb</b>oards. <b>Da</b>ta <b>i</b>s <b>clea</b>ned <b>a</b>nd <b>struc</b>tured <b>bef</b>ore <b>load</b>ing (*<b>sch</b>ema-<b>o</b>n-<b>wri</b>te*). <b>O</b>n AWS: **Redshift**.

### Lakehouse
<b>Da</b>ta <b>la</b>ke <b>fil</b>es <b>pl</b>us <b>a</b> **table format** (<b>Iceb</b>erg, <b>Hu</b>di, <b>Del</b>ta <b>La</b>ke) <b>th</b>at <b>ad</b>ds <b>wareh</b>ouse <b>feat</b>ures: <b>upda</b>tes, <b>dele</b>tes, <b>transa</b>ctions, <b>ti</b>me <b>tra</b>vel. <b>Y</b>ou <b>g</b>et <b>wareh</b>ouse-<b>li</b>ke <b>tab</b>les <b>whi</b>le <b>t</b>he <b>da</b>ta <b>sta</b>ys <b>i</b>n <b>che</b>ap S3.

### OLTP vs OLAP
- **OLTP (Online Transaction Processing)**: <b>t</b>he <b>app</b>'s <b>data</b>base. <b>Ma</b>ny <b>sma</b>ll, <b>fa</b>st <b>rea</b>ds/<b>wri</b>tes ("<b>ins</b>ert <b>th</b>is <b>ord</b>er"). <b>Exam</b>ples: RDS, <b>Aur</b>ora, <b>Dyna</b>moDB.
- **OLAP (Online Analytical Processing)**: <b>b</b>ig <b>analy</b>tical <b>quer</b>ies ("<b>tot</b>al <b>sal</b>es <b>p</b>er <b>reg</b>ion <b>f</b>or 5 <b>yea</b>rs"). <b>Exam</b>ples: <b>Reds</b>hift, <b>Ath</b>ena.
<b>Y</b>ou <b>don</b>'t <b>r</b>un <b>hea</b>vy <b>analy</b>tics <b>o</b>n <b>t</b>he OLTP <b>data</b>base <b>beca</b>use <b>i</b>t <b>slo</b>ws <b>t</b>he <b>a</b>pp <b>do</b>wn; <b>y</b>ou <b>co</b>py <b>t</b>he <b>da</b>ta <b>o</b>ut <b>inst</b>ead.

### SQL
<b>T</b>he <b>stan</b>dard <b>lang</b>uage <b>f</b>or <b>ask</b>ing <b>quest</b>ions <b>o</b>f <b>tabu</b>lar <b>da</b>ta: `SELECT region, SUM(sales) FROM orders GROUP BY region`. <b>Us</b>ed <b>b</b>y <b>Ath</b>ena, <b>Reds</b>hift, RDS <b>a</b>nd <b>ma</b>ny <b>oth</b>er <b>serv</b>ices.

### API
<b>A</b>n **Application Programming Interface** <b>i</b>s <b>a</b> <b>defi</b>ned <b>w</b>ay <b>f</b>or <b>o</b>ne <b>prog</b>ram <b>t</b>o <b>a</b>sk <b>anot</b>her <b>f</b>or <b>da</b>ta <b>o</b>r <b>acti</b>ons, <b>usua</b>lly <b>ov</b>er <b>t</b>he <b>w</b>eb (HTTP). <b>F</b>or <b>exam</b>ple, "<b>ca</b>ll `GET /orders?date=today` <b>a</b>nd <b>rece</b>ive JSON <b>ba</b>ck." <b>Ma</b>ny <b>da</b>ta <b>sour</b>ces (SaaS <b>ap</b>ps, <b>part</b>ners) <b>a</b>re <b>re</b>ad <b>thro</b>ugh <b>the</b>ir APIs.

### JDBC and ODBC
<b>Stan</b>dard "<b>plu</b>gs" (<b>driv</b>ers) <b>th</b>at <b>l</b>et <b>a</b> <b>prog</b>ram <b>ta</b>lk <b>t</b>o <b>alm</b>ost <b>a</b>ny SQL <b>data</b>base <b>t</b>he <b>sa</b>me <b>w</b>ay. **JDBC (Java Database Connectivity)** <b>i</b>s <b>us</b>ed <b>b</b>y <b>Ja</b>va-<b>bas</b>ed <b>too</b>ls <b>su</b>ch <b>a</b>s <b>Spa</b>rk, <b>Gl</b>ue <b>a</b>nd EMR. **ODBC (Open Database Connectivity)** <b>i</b>s <b>us</b>ed <b>b</b>y <b>ma</b>ny <b>oth</b>er <b>too</b>ls, <b>su</b>ch <b>a</b>s <b>Exc</b>el, <b>Tabl</b>eau <b>a</b>nd <b>Pow</b>er BI. <b>A</b> JDBC/ODBC *<b>conne</b>ction* = <b>data</b>base <b>addr</b>ess (URL) + <b>po</b>rt + <b>user</b>name/<b>pass</b>word.

### NoSQL and key/value stores
<b>Datab</b>ases <b>th</b>at <b>don</b>'t <b>u</b>se <b>fix</b>ed <b>tab</b>les <b>a</b>nd SQL <b>joi</b>ns. <b>A</b> **key/value store** (<b>Dyna</b>moDB, <b>Red</b>is) <b>loo</b>ks <b>u</b>p <b>a</b>n <b>it</b>em <b>b</b>y <b>i</b>ts <b>k</b>ey <b>extre</b>mely <b>fa</b>st, <b>li</b>ke <b>a</b> <b>gia</b>nt <b>dicti</b>onary. <b>Gre</b>at <b>f</b>or <b>ap</b>ps, <b>po</b>or <b>f</b>or <b>a</b>d-<b>h</b>oc <b>analy</b>tics.

### Schema
<b>T</b>he <b>struc</b>ture <b>o</b>f <b>da</b>ta: <b>col</b>umn <b>nam</b>es <b>a</b>nd <b>the</b>ir <b>typ</b>es (`order_id: int, amount: decimal, created_at: timestamp`). **Schema evolution** = <b>t</b>he <b>struc</b>ture <b>chan</b>ges <b>ov</b>er <b>ti</b>me (<b>a</b> <b>n</b>ew <b>col</b>umn <b>appe</b>ars) <b>a</b>nd <b>t</b>he <b>pipe</b>line <b>mu</b>st <b>co</b>pe.

### Metadata and data catalog
**Metadata** = <b>da</b>ta <b>abo</b>ut <b>da</b>ta (<b>whe</b>re <b>fil</b>es <b>a</b>re, <b>the</b>ir <b>colu</b>mns <b>a</b>nd <b>typ</b>es, <b>parti</b>tions). <b>A</b> **data catalog** <b>sto</b>res <b>th</b>is <b>s</b>o <b>que</b>ry <b>engi</b>nes <b>c</b>an <b>tre</b>at <b>a</b> <b>fol</b>der <b>o</b>f <b>fil</b>es <b>a</b>s <b>a</b> <b>tab</b>le. <b>O</b>n AWS: <b>t</b>he **Glue Data Catalog**.

### Partitioning
<b>Split</b>ting <b>da</b>ta <b>in</b>to <b>fold</b>ers <b>b</b>y <b>a</b> <b>col</b>umn, <b>usua</b>lly <b>da</b>te: `s3://lake/orders/year=2026/month=11/day=19/`. <b>A</b> <b>que</b>ry <b>f</b>or <b>o</b>ne <b>d</b>ay <b>th</b>en <b>rea</b>ds <b>on</b>ly <b>th</b>at <b>fol</b>der <b>inst</b>ead <b>o</b>f <b>every</b>thing. <b>Th</b>at <b>mak</b>es <b>i</b>t <b>fas</b>ter <b>a</b>nd <b>chea</b>per.

### Row vs columnar storage
- **Row format** (CSV, JSON): <b>ea</b>ch <b>li</b>ne <b>hol</b>ds <b>o</b>ne <b>who</b>le <b>rec</b>ord. <b>Go</b>od <b>f</b>or <b>writ</b>ing <b>reco</b>rds <b>o</b>ne <b>b</b>y <b>o</b>ne.
- **Columnar format** (<b>Parq</b>uet, ORC): <b>val</b>ues <b>o</b>f <b>ea</b>ch <b>col</b>umn <b>a</b>re <b>sto</b>red <b>toge</b>ther. <b>A</b> <b>que</b>ry <b>read</b>ing 3 <b>o</b>f 50 <b>colu</b>mns <b>on</b>ly <b>rea</b>ds <b>tho</b>se 3, <b>a</b>nd <b>simi</b>lar <b>val</b>ues <b>comp</b>ress <b>ve</b>ry <b>we</b>ll. <b>Th</b>is <b>i</b>s <b>t</b>he <b>defa</b>ult <b>cho</b>ice <b>f</b>or <b>analy</b>tics.

### Compression and "splittable"
<b>Compre</b>ssion (<b>Sna</b>ppy, GZIP, ZSTD) <b>shri</b>nks <b>fil</b>es <b>t</b>o <b>sa</b>ve <b>stor</b>age <b>a</b>nd <b>read</b>ing <b>ti</b>me. <b>A</b> <b>fi</b>le <b>i</b>s **splittable** <b>i</b>f <b>seve</b>ral <b>work</b>ers <b>c</b>an <b>ea</b>ch <b>re</b>ad <b>a</b> <b>pa</b>rt <b>o</b>f <b>i</b>t <b>i</b>n <b>para</b>llel. <b>A</b> <b>b</b>ig `.csv.gz` <b>fi</b>le <b>i</b>s **not** <b>split</b>table (<b>o</b>ne <b>wor</b>ker <b>mu</b>st <b>re</b>ad <b>i</b>t <b>a</b>ll); <b>Parq</b>uet <b>i</b>s.

### Small files problem
<b>Mill</b>ions <b>o</b>f <b>ti</b>ny <b>fil</b>es (<b>a</b> <b>f</b>ew KB <b>ea</b>ch) <b>ma</b>ke <b>quer</b>ies <b>sl</b>ow <b>beca</b>use <b>t</b>he <b>eng</b>ine <b>spe</b>nds <b>mo</b>re <b>ti</b>me <b>open</b>ing <b>fil</b>es <b>th</b>an <b>read</b>ing <b>da</b>ta. <b>F</b>ix: <b>comb</b>ine <b>th</b>em <b>in</b>to <b>few</b>er <b>fil</b>es <b>o</b>f <b>roug</b>hly 128 MB–1 GB (<b>cal</b>led **compaction**).

### Change Data Capture (CDC)
<b>Inst</b>ead <b>o</b>f <b>copy</b>ing <b>a</b> <b>who</b>le <b>data</b>base <b>eve</b>ry <b>nig</b>ht, <b>re</b>ad <b>i</b>ts **change log** <b>a</b>nd <b>co</b>py <b>on</b>ly <b>t</b>he <b>inse</b>rts, <b>upda</b>tes <b>a</b>nd <b>dele</b>tes <b>a</b>s <b>th</b>ey <b>hap</b>pen. DMS <b>do</b>es <b>th</b>is <b>o</b>n AWS.

### Upsert and MERGE
**Upsert** = "<b>upd</b>ate <b>t</b>he <b>r</b>ow <b>i</b>f <b>i</b>t <b>exi</b>sts, <b>ins</b>ert <b>i</b>t <b>i</b>f <b>i</b>t <b>does</b>n't." <b>I</b>n SQL <b>th</b>is <b>i</b>s <b>t</b>he `MERGE` <b>state</b>ment. <b>Nee</b>ded <b>wh</b>en <b>appl</b>ying CDC <b>chan</b>ges <b>t</b>o <b>a</b> <b>tab</b>le.

### Shard / partition (in streams)
<b>A</b> <b>str</b>eam <b>i</b>s <b>spl</b>it <b>in</b>to <b>para</b>llel <b>lan</b>es <b>cal</b>led **shards** (<b>Kine</b>sis) <b>o</b>r **partitions** (<b>Kaf</b>ka). <b>Mo</b>re <b>lan</b>es = <b>mo</b>re <b>throu</b>ghput. <b>A</b> **partition key** <b>deci</b>des <b>whi</b>ch <b>la</b>ne <b>ea</b>ch <b>rec</b>ord <b>go</b>es <b>t</b>o; <b>reco</b>rds <b>wi</b>th <b>t</b>he <b>sa</b>me <b>k</b>ey <b>st</b>ay <b>i</b>n <b>ord</b>er.

### Producer and consumer
<b>A</b> **producer** <b>wri</b>tes <b>reco</b>rds <b>in</b>to <b>a</b> <b>str</b>eam <b>o</b>r <b>que</b>ue; <b>a</b> **consumer** <b>rea</b>ds <b>th</b>em. <b>Stre</b>ams <b>l</b>et <b>ma</b>ny <b>consu</b>mers <b>re</b>ad <b>t</b>he <b>sa</b>me <b>da</b>ta <b>indepen</b>dently <b>a</b>nd **replay** <b>i</b>t <b>lat</b>er.

### Orchestration and DAG
**Orchestration** = <b>runn</b>ing <b>pipe</b>line <b>ste</b>ps <b>i</b>n <b>t</b>he <b>rig</b>ht <b>ord</b>er, <b>wi</b>th <b>retr</b>ies <b>a</b>nd <b>ale</b>rts ("<b>r</b>un <b>j</b>ob <b>B</b> <b>on</b>ly <b>aft</b>er <b>j</b>ob <b>A</b> <b>succ</b>eeds"). <b>A</b> **DAG (Directed Acyclic Graph)** <b>i</b>s <b>a</b> <b>diag</b>ram <b>o</b>f <b>ste</b>ps <b>wi</b>th <b>arr</b>ows <b>show</b>ing <b>wh</b>at <b>depe</b>nds <b>o</b>n <b>wh</b>at, <b>wi</b>th <b>n</b>o <b>loo</b>ps. <b>Airf</b>low <b>pipel</b>ines <b>a</b>re <b>writ</b>ten <b>a</b>s DAGs.

### Idempotent
<b>Runn</b>ing <b>a</b> <b>st</b>ep <b>twi</b>ce <b>giv</b>es <b>t</b>he <b>sa</b>me <b>res</b>ult <b>a</b>s <b>runn</b>ing <b>i</b>t <b>on</b>ce (<b>n</b>o <b>dupli</b>cate <b>ro</b>ws). <b>Impor</b>tant <b>beca</b>use <b>fai</b>led <b>ste</b>ps <b>g</b>et <b>retr</b>ied.

### Data skew
<b>O</b>ne <b>wor</b>ker <b>ge</b>ts <b>f</b>ar <b>mo</b>re <b>da</b>ta <b>th</b>an <b>t</b>he <b>oth</b>ers (<b>e</b>.g., 70% <b>o</b>f <b>ro</b>ws <b>ha</b>ve `country = 'US'`), <b>s</b>o <b>t</b>he <b>who</b>le <b>j</b>ob <b>wai</b>ts <b>f</b>or <b>th</b>at <b>sin</b>gle <b>sl</b>ow <b>wor</b>ker. <b>Fix</b>es <b>incl</b>ude **salting** (<b>add</b>ing <b>a</b> <b>ran</b>dom <b>num</b>ber <b>t</b>o <b>t</b>he <b>h</b>ot <b>k</b>ey <b>t</b>o <b>spr</b>ead <b>i</b>t <b>o</b>ut) <b>a</b>nd **broadcast joins**.

### Distributed computing
<b>Split</b>ting <b>o</b>ne <b>b</b>ig <b>j</b>ob <b>acr</b>oss <b>ma</b>ny <b>mach</b>ines (<b>a</b> **cluster**) <b>th</b>at <b>wo</b>rk <b>i</b>n <b>para</b>llel, <b>th</b>en <b>combi</b>ning <b>t</b>he <b>resu</b>lts. <b>Spa</b>rk, <b>Had</b>oop <b>a</b>nd <b>Reds</b>hift <b>a</b>ll <b>wo</b>rk <b>th</b>is <b>w</b>ay.

### Star schema: fact and dimension tables
<b>A</b> <b>com</b>mon <b>wareh</b>ouse <b>des</b>ign. <b>A</b> <b>cent</b>ral **fact table** <b>hol</b>ds <b>eve</b>nts <b>wi</b>th <b>numb</b>ers (<b>ea</b>ch <b>sa</b>le: <b>amo</b>unt, <b>quan</b>tity), <b>lin</b>ked <b>t</b>o **dimension tables** <b>th</b>at <b>desc</b>ribe <b>th</b>em (<b>cust</b>omer, <b>prod</b>uct, <b>da</b>te). <b>Dra</b>wn <b>o</b>ut, <b>i</b>t <b>loo</b>ks <b>li</b>ke <b>a</b> <b>st</b>ar.

### Slowly Changing Dimension (SCD)
<b>H</b>ow <b>t</b>o <b>han</b>dle <b>dimen</b>sion <b>da</b>ta <b>th</b>at <b>chan</b>ges, <b>e</b>.g., <b>a</b> <b>cust</b>omer <b>mov</b>es <b>ci</b>ty. **Type 1** <b>overw</b>rite <b>t</b>he <b>o</b>ld <b>val</b>ue; **Type 2** <b>ke</b>ep <b>hist</b>ory <b>b</b>y <b>add</b>ing <b>a</b> <b>n</b>ew <b>r</b>ow; **Type 3** <b>ke</b>ep <b>t</b>he <b>prev</b>ious <b>val</b>ue <b>i</b>n <b>a</b>n <b>ext</b>ra <b>col</b>umn.

### Serverless vs provisioned
- **Provisioned**: <b>y</b>ou <b>cho</b>ose <b>a</b>nd <b>p</b>ay <b>f</b>or <b>serv</b>ers/<b>capa</b>city, <b>whet</b>her <b>bu</b>sy <b>o</b>r <b>id</b>le.
- **Serverless**: AWS <b>hand</b>les <b>t</b>he <b>serv</b>ers <b>a</b>nd <b>scal</b>ing; <b>y</b>ou <b>p</b>ay <b>p</b>er <b>u</b>se. <b>T</b>he <b>ex</b>am <b>oft</b>en <b>pref</b>ers <b>serve</b>rless <b>f</b>or "<b>lea</b>st <b>operat</b>ional <b>over</b>head."

### Data quality
<b>Autom</b>ated <b>che</b>cks <b>th</b>at <b>da</b>ta <b>i</b>s <b>corr</b>ect <b>bef</b>ore <b>it</b>'s <b>us</b>ed: <b>n</b>o <b>miss</b>ing IDs, <b>val</b>ues <b>i</b>n <b>ran</b>ge, <b>n</b>o <b>dupli</b>cates.

### Data lineage
<b>A</b> <b>rec</b>ord <b>o</b>f <b>whe</b>re <b>da</b>ta <b>ca</b>me <b>fr</b>om <b>a</b>nd <b>whi</b>ch <b>ste</b>ps <b>chan</b>ged <b>i</b>t ("<b>th</b>is <b>dashb</b>oard <b>num</b>ber <b>ca</b>me <b>fr</b>om <b>tab</b>le <b>X</b>, <b>bui</b>lt <b>b</b>y <b>j</b>ob <b>Y</b> <b>fr</b>om <b>sou</b>rce <b>Z</b>"). <b>I</b>t <b>hel</b>ps <b>wi</b>th <b>debug</b>ging <b>a</b>nd <b>aud</b>its.

### Data governance
<b>T</b>he <b>rul</b>es <b>a</b>nd <b>too</b>ls <b>f</b>or <b>w</b>ho <b>m</b>ay <b>s</b>ee <b>wh</b>at <b>da</b>ta, <b>h</b>ow <b>sensi</b>tive <b>da</b>ta <b>i</b>s <b>prote</b>cted, <b>a</b>nd <b>h</b>ow <b>da</b>ta <b>i</b>s <b>docum</b>ented <b>a</b>nd <b>audi</b>ted.

### PII, masking and encryption
- **PII (Personally Identifiable Information)**: <b>da</b>ta <b>th</b>at <b>ident</b>ifies <b>a</b> <b>per</b>son: <b>na</b>me, <b>ema</b>il, <b>pho</b>ne, ID <b>num</b>ber.
- **Masking**: <b>hid</b>ing <b>pa</b>rt <b>o</b>f <b>a</b> <b>val</b>ue (`****-1234`) <b>fr</b>om <b>peo</b>ple <b>w</b>ho <b>don</b>'t <b>ne</b>ed <b>i</b>t.
- **Encryption at rest**: <b>da</b>ta <b>i</b>s <b>scram</b>bled <b>whi</b>le <b>sto</b>red <b>o</b>n <b>di</b>sk. **In transit**: <b>scram</b>bled <b>whi</b>le <b>mov</b>ing <b>ov</b>er <b>t</b>he <b>netw</b>ork (TLS/HTTPS). <b>On</b>ly <b>hold</b>ers <b>o</b>f <b>t</b>he <b>k</b>ey <b>c</b>an <b>re</b>ad <b>i</b>t.

### Vectors and embeddings
<b>A</b>n **embedding** <b>i</b>s <b>a</b> <b>li</b>st <b>o</b>f <b>numb</b>ers <b>repres</b>enting <b>t</b>he *<b>mean</b>ing* <b>o</b>f <b>te</b>xt <b>o</b>r <b>a</b>n <b>ima</b>ge, <b>prod</b>uced <b>b</b>y <b>a</b>n AI <b>mod</b>el. <b>Simi</b>lar <b>mean</b>ings <b>gi</b>ve <b>nea</b>rby <b>vect</b>ors. <b>A</b> **vector database/index** <b>fin</b>ds <b>t</b>he <b>mo</b>st <b>simi</b>lar <b>ite</b>ms <b>quic</b>kly. <b>Th</b>is <b>i</b>s <b>us</b>ed <b>i</b>n RAG, <b>whe</b>re <b>a</b>n AI <b>loo</b>ks <b>u</b>p <b>rele</b>vant <b>docum</b>ents <b>bef</b>ore <b>answe</b>ring.

---

## File formats

### CSV
<b>Pla</b>in <b>te</b>xt, <b>o</b>ne <b>r</b>ow <b>p</b>er <b>li</b>ne, <b>com</b>mas <b>betw</b>een <b>val</b>ues. <b>Hum</b>an-<b>read</b>able <b>a</b>nd <b>unive</b>rsal, <b>b</b>ut <b>sl</b>ow <b>a</b>nd <b>b</b>ig <b>f</b>or <b>analy</b>tics, <b>wi</b>th <b>n</b>o <b>typ</b>es.

### JSON
<b>Te</b>xt <b>for</b>mat <b>o</b>f <b>nes</b>ted `{"key": "value"}` <b>obje</b>cts. <b>Ve</b>ry <b>com</b>mon <b>f</b>or APIs <b>a</b>nd <b>eve</b>nts. **JSON Lines (JSONL)** = <b>o</b>ne JSON <b>obj</b>ect <b>p</b>er <b>li</b>ne.

### Parquet
<b>Colu</b>mnar, <b>compr</b>essed, <b>wi</b>th <b>a</b> <b>sch</b>ema <b>sto</b>red <b>i</b>n <b>t</b>he <b>fi</b>le. **The default analytics format** <b>o</b>n AWS: <b>smal</b>ler <b>a</b>nd <b>mu</b>ch <b>fas</b>ter <b>t</b>o <b>que</b>ry <b>th</b>an CSV/JSON.

### ORC
<b>Anot</b>her <b>colu</b>mnar <b>for</b>mat (<b>fr</b>om <b>t</b>he <b>Hi</b>ve <b>wor</b>ld), <b>simi</b>lar <b>t</b>o <b>Parq</b>uet.

### Avro
<b>R</b>ow-<b>bas</b>ed <b>bin</b>ary <b>for</b>mat <b>wi</b>th <b>a</b> <b>sch</b>ema <b>sto</b>red <b>along</b>side. <b>Com</b>mon <b>i</b>n <b>Kaf</b>ka <b>strea</b>ming <b>beca</b>use <b>ea</b>ch <b>rec</b>ord <b>i</b>s <b>comp</b>act <b>a</b>nd <b>t</b>he <b>sch</b>ema <b>c</b>an <b>evo</b>lve.

---

## Open-source tools

### Apache Hadoop
<b>T</b>he <b>orig</b>inal <b>op</b>en-<b>sou</b>rce <b>sys</b>tem (<b>aro</b>und 2006) <b>f</b>or <b>stor</b>ing <b>a</b>nd <b>proce</b>ssing <b>hu</b>ge <b>da</b>ta <b>acr</b>oss <b>ma</b>ny <b>che</b>ap <b>mach</b>ines. <b>Mos</b>tly <b>repl</b>aced <b>b</b>y <b>Spa</b>rk + S3, <b>b</b>ut EMR <b>sti</b>ll <b>ru</b>ns <b>i</b>t.

### HDFS
**Hadoop Distributed File System**: <b>Hado</b>op's <b>stor</b>age, <b>spr</b>ead <b>acr</b>oss <b>t</b>he <b>dis</b>ks <b>o</b>f <b>t</b>he <b>clust</b>er's <b>mach</b>ines. <b>Da</b>ta <b>disap</b>pears <b>wi</b>th <b>t</b>he <b>clus</b>ter, <b>whi</b>ch <b>i</b>s <b>w</b>hy AWS <b>desi</b>gns <b>sto</b>re <b>da</b>ta <b>i</b>n S3 <b>inst</b>ead.

### YARN
<b>Hado</b>op's <b>reso</b>urce <b>mana</b>ger: <b>deci</b>des <b>whi</b>ch <b>j</b>ob <b>ge</b>ts <b>whi</b>ch CPU <b>a</b>nd <b>mem</b>ory <b>o</b>n <b>t</b>he <b>clus</b>ter.

### Apache Hive
<b>Le</b>ts <b>y</b>ou <b>que</b>ry <b>fil</b>es <b>i</b>n <b>Had</b>oop/S3 <b>wi</b>th SQL <b>a</b>s <b>i</b>f <b>th</b>ey <b>we</b>re <b>tab</b>les. <b>I</b>ts **Hive Metastore** (<b>t</b>he <b>li</b>st <b>o</b>f <b>tab</b>les, <b>colu</b>mns <b>a</b>nd <b>parti</b>tions) <b>i</b>s <b>t</b>he <b>id</b>ea <b>t</b>he <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log <b>cop</b>ies.

### Apache Spark
<b>T</b>he <b>mo</b>st <b>popu</b>lar <b>eng</b>ine <b>f</b>or <b>proce</b>ssing <b>b</b>ig <b>da</b>ta, <b>i</b>n <b>mem</b>ory, <b>acr</b>oss <b>a</b> <b>clus</b>ter. <b>Y</b>ou <b>wri</b>te <b>co</b>de <b>i</b>n <b>Pyt</b>hon (**PySpark**), <b>Sca</b>la, <b>Ja</b>va <b>o</b>r SQL. <b>Gl</b>ue <b>a</b>nd EMR <b>r</b>un <b>Spa</b>rk. <b>K</b>ey <b>par</b>ts: <b>a</b> **driver** (<b>pla</b>ns <b>t</b>he <b>wo</b>rk) <b>a</b>nd **executors** (<b>d</b>o <b>t</b>he <b>wo</b>rk).

### Apache Kafka
<b>A</b>n <b>op</b>en-<b>sou</b>rce **event streaming platform**: <b>produ</b>cers <b>wri</b>te <b>mess</b>ages <b>t</b>o **topics** (<b>spl</b>it <b>in</b>to <b>parti</b>tions); <b>consu</b>mers <b>re</b>ad <b>th</b>em; <b>mess</b>ages <b>a</b>re <b>ke</b>pt <b>f</b>or <b>da</b>ys <b>s</b>o <b>th</b>ey <b>c</b>an <b>b</b>e <b>repl</b>ayed. <b>Us</b>ed <b>a</b>s <b>t</b>he <b>cent</b>ral "<b>pi</b>pe" <b>betw</b>een <b>syst</b>ems. <b>O</b>n AWS: **Amazon MSK**. **Kafka Connect** <b>i</b>s <b>i</b>ts <b>a</b>dd-<b>o</b>n <b>f</b>or <b>mov</b>ing <b>da</b>ta <b>betw</b>een <b>Kaf</b>ka <b>a</b>nd <b>oth</b>er <b>syst</b>ems <b>with</b>out <b>co</b>de.

### Apache Flink
<b>A</b> <b>str</b>eam-<b>proce</b>ssing <b>eng</b>ine <b>f</b>or **stateful** <b>wo</b>rk <b>o</b>n <b>li</b>ve <b>da</b>ta: <b>wind</b>owed <b>aggreg</b>ations ("<b>cou</b>nt <b>cli</b>cks <b>p</b>er <b>us</b>er <b>eve</b>ry 5 <b>minu</b>tes"), <b>joi</b>ns <b>o</b>f <b>stre</b>ams, <b>detec</b>ting <b>patt</b>erns. <b>O</b>n AWS: **Managed Service for Apache Flink**.

### Apache Airflow
<b>A</b> <b>to</b>ol <b>t</b>o <b>sche</b>dule <b>a</b>nd <b>orches</b>trate <b>pipel</b>ines <b>writ</b>ten <b>a</b>s <b>Pyt</b>hon **DAGs**, <b>wi</b>th <b>a</b> <b>w</b>eb UI <b>show</b>ing <b>ru</b>ns, <b>fail</b>ures <b>a</b>nd <b>retr</b>ies. <b>O</b>n AWS: **MWAA**.

### Apache Iceberg
<b>A</b>n <b>op</b>en **table format** <b>th</b>at <b>tur</b>ns <b>a</b> <b>fol</b>der <b>o</b>f <b>Parq</b>uet <b>fil</b>es <b>i</b>n S3 <b>in</b>to <b>a</b> <b>re</b>al <b>tab</b>le <b>suppo</b>rting <b>upda</b>tes, <b>dele</b>tes, `MERGE`, <b>sch</b>ema <b>chan</b>ges <b>a</b>nd **time travel** (<b>que</b>ry <b>t</b>he <b>tab</b>le <b>a</b>s <b>i</b>t <b>w</b>as <b>yeste</b>rday). AWS's <b>ma</b>in <b>lakeh</b>ouse <b>tab</b>le <b>for</b>mat.

### Apache Hudi
<b>Anot</b>her <b>tab</b>le <b>for</b>mat <b>li</b>ke <b>Iceb</b>erg, <b>focu</b>sed <b>o</b>n <b>fa</b>st <b>upse</b>rts <b>a</b>nd <b>increm</b>ental <b>proce</b>ssing.

### Delta Lake
<b>A</b> <b>thi</b>rd <b>tab</b>le <b>for</b>mat <b>li</b>ke <b>Iceb</b>erg, <b>crea</b>ted <b>b</b>y <b>Datab</b>ricks.

### Presto and Trino
<b>Fa</b>st <b>distri</b>buted SQL <b>engi</b>nes <b>th</b>at <b>que</b>ry <b>da</b>ta <b>whe</b>re <b>i</b>t <b>si</b>ts (S3, <b>datab</b>ases) <b>with</b>out <b>load</b>ing <b>i</b>t <b>fir</b>st. <b>Ath</b>ena <b>i</b>s <b>bui</b>lt <b>o</b>n <b>Tri</b>no/<b>Pre</b>sto.

### Apache HBase
<b>A</b> NoSQL <b>data</b>base <b>o</b>n <b>t</b>op <b>o</b>f <b>Had</b>oop <b>f</b>or <b>fa</b>st <b>ran</b>dom <b>rea</b>ds/<b>wri</b>tes <b>o</b>n <b>hu</b>ge <b>tab</b>les. <b>Ru</b>ns <b>o</b>n EMR.

### Redis and Valkey
<b>I</b>n-<b>mem</b>ory <b>k</b>ey/<b>val</b>ue <b>sto</b>res: <b>extre</b>mely <b>fa</b>st, <b>oft</b>en <b>us</b>ed <b>a</b>s <b>a</b> <b>cac</b>he. <b>Val</b>key <b>i</b>s <b>t</b>he <b>op</b>en-<b>sou</b>rce <b>fo</b>rk <b>o</b>f <b>Red</b>is. AWS <b>ru</b>ns <b>th</b>em <b>a</b>s <b>Elasti</b>Cache <b>a</b>nd <b>Memo</b>ryDB.

### Kubernetes
<b>Soft</b>ware <b>th</b>at <b>ru</b>ns <b>a</b>nd <b>mana</b>ges **containers** (<b>pack</b>aged <b>ap</b>ps) <b>acr</b>oss <b>ma</b>ny <b>mach</b>ines. <b>O</b>n AWS: **EKS**.

### Docker and containers
<b>A</b> **container** <b>pack</b>ages <b>a</b>n <b>a</b>pp <b>wi</b>th <b>every</b>thing <b>i</b>t <b>nee</b>ds <b>s</b>o <b>i</b>t <b>ru</b>ns <b>t</b>he <b>sa</b>me <b>every</b>where. <b>Doc</b>ker <b>i</b>s <b>t</b>he <b>com</b>mon <b>to</b>ol <b>f</b>or <b>buil</b>ding <b>th</b>em.

### PostgreSQL, MySQL, Oracle and SQL Server
<b>Popu</b>lar **relational databases** (<b>tab</b>les, SQL, <b>transa</b>ctions). <b>Postg</b>reSQL <b>a</b>nd MySQL <b>a</b>re <b>op</b>en <b>sou</b>rce; <b>Ora</b>cle <b>a</b>nd SQL <b>Ser</b>ver <b>a</b>re <b>comme</b>rcial. RDS <b>a</b>nd <b>Aur</b>ora <b>r</b>un <b>th</b>em <b>f</b>or <b>y</b>ou. **pgvector** <b>i</b>s <b>a</b> <b>Postg</b>reSQL <b>exten</b>sion <b>f</b>or <b>stor</b>ing <b>a</b>nd <b>searc</b>hing <b>vect</b>ors.

### MongoDB
<b>A</b> <b>popu</b>lar NoSQL **document database** <b>stor</b>ing JSON-<b>li</b>ke <b>docum</b>ents. AWS's <b>compa</b>tible <b>serv</b>ice <b>i</b>s <b>Docum</b>entDB.

### Jupyter
<b>Noteb</b>ooks <b>i</b>n <b>t</b>he <b>brow</b>ser <b>whe</b>re <b>y</b>ou <b>m</b>ix <b>co</b>de, <b>resu</b>lts <b>a</b>nd <b>not</b>es, <b>ce</b>ll <b>b</b>y <b>ce</b>ll. <b>Com</b>mon <b>f</b>or <b>da</b>ta <b>explor</b>ation.

### Snowflake, Splunk and Salesforce
<b>Thi</b>rd-<b>par</b>ty <b>prod</b>ucts <b>th</b>at <b>app</b>ear <b>a</b>s <b>sour</b>ces <b>o</b>r <b>destin</b>ations: **Snowflake** <b>i</b>s <b>a</b> <b>clo</b>ud <b>da</b>ta <b>wareh</b>ouse, **Splunk** <b>a</b> <b>l</b>og <b>sea</b>rch/<b>analy</b>tics <b>to</b>ol, **Salesforce** <b>a</b> <b>cust</b>omer-<b>relati</b>onship (CRM) SaaS <b>a</b>pp.

---

## AWS services in one line each

### Storage and databases

#### Amazon S3
<b>Obj</b>ect <b>stor</b>age: <b>unlim</b>ited <b>fil</b>es ("<b>obje</b>cts") <b>i</b>n "<b>buck</b>ets," <b>ve</b>ry <b>che</b>ap <b>a</b>nd <b>dura</b>ble. <b>T</b>he <b>ba</b>se <b>o</b>f <b>eve</b>ry AWS <b>da</b>ta <b>la</b>ke. <b>H</b>as **storage classes** (<b>Stan</b>dard, <b>Infre</b>quent <b>Acc</b>ess, <b>Glac</b>ier) <b>th</b>at <b>tra</b>de <b>retri</b>eval <b>spe</b>ed <b>f</b>or <b>low</b>er <b>pri</b>ce.

#### Amazon S3 Tables
S3 <b>buck</b>ets <b>bui</b>lt <b>specif</b>ically <b>f</b>or <b>Iceb</b>erg <b>tab</b>les, <b>wi</b>th <b>autom</b>atic <b>mainte</b>nance (<b>compa</b>ction, <b>clea</b>nup).

#### Amazon Redshift
AWS's <b>da</b>ta <b>wareh</b>ouse <b>f</b>or <b>fa</b>st SQL <b>analy</b>tics <b>a</b>t <b>peta</b>byte <b>sca</b>le. **Redshift Spectrum** <b>le</b>ts <b>i</b>t <b>que</b>ry <b>fil</b>es <b>i</b>n S3 <b>dire</b>ctly; **Redshift Serverless** <b>remo</b>ves <b>clus</b>ter <b>manag</b>ement.

#### Amazon RDS
<b>Mana</b>ged <b>relat</b>ional <b>datab</b>ases (<b>Postg</b>reSQL, MySQL, <b>Ora</b>cle, SQL <b>Ser</b>ver…): AWS <b>hand</b>les <b>back</b>ups, <b>patc</b>hing <b>a</b>nd <b>fail</b>over.

#### Amazon Aurora
AWS's <b>o</b>wn <b>hi</b>gh-<b>perfor</b>mance MySQL/<b>Postg</b>reSQL-<b>compa</b>tible <b>data</b>base, <b>pa</b>rt <b>o</b>f RDS.

#### Amazon DynamoDB
<b>Serve</b>rless NoSQL <b>k</b>ey/<b>val</b>ue <b>data</b>base <b>wi</b>th <b>sin</b>gle-<b>dig</b>it-<b>millis</b>econd <b>spe</b>ed <b>a</b>t <b>a</b>ny <b>sca</b>le. <b>Desi</b>gned <b>aro</b>und <b>kno</b>wn <b>acc</b>ess <b>patt</b>erns, <b>n</b>ot <b>a</b>d-<b>h</b>oc <b>quer</b>ies.

#### Amazon OpenSearch Service
<b>Sea</b>rch <b>a</b>nd <b>l</b>og-<b>analy</b>tics <b>eng</b>ine (<b>op</b>en-<b>sou</b>rce <b>fo</b>rk <b>o</b>f <b>Elastic</b>search): <b>fu</b>ll-<b>te</b>xt <b>sea</b>rch, <b>l</b>og <b>dashb</b>oards, <b>vec</b>tor <b>sea</b>rch.

#### Amazon Neptune
<b>Gra</b>ph <b>data</b>base <b>f</b>or <b>hig</b>hly <b>conne</b>cted <b>da</b>ta (<b>soc</b>ial <b>netw</b>orks, <b>fra</b>ud <b>rin</b>gs).

#### Amazon MemoryDB and ElastiCache
<b>I</b>n-<b>mem</b>ory <b>Red</b>is/<b>Val</b>key-<b>compa</b>tible <b>sto</b>res. **ElastiCache** <b>i</b>s <b>a</b> <b>cac</b>he; **MemoryDB** <b>i</b>s <b>dura</b>ble <b>eno</b>ugh <b>t</b>o <b>b</b>e <b>a</b> <b>prim</b>ary <b>data</b>base.

### Moving data in (ingestion)

#### Amazon Kinesis Data Streams
AWS's <b>strea</b>ming <b>serv</b>ice, <b>li</b>ke <b>Kaf</b>ka: <b>produ</b>cers <b>wri</b>te <b>reco</b>rds <b>in</b>to <b>sha</b>rds, <b>ma</b>ny <b>consu</b>mers <b>re</b>ad <b>th</b>em, <b>da</b>ta <b>i</b>s <b>ke</b>pt <b>f</b>or <b>rep</b>lay.

#### Amazon Data Firehose
<b>T</b>he <b>easi</b>est <b>w</b>ay <b>t</b>o *<b>deli</b>ver* <b>strea</b>ming <b>da</b>ta: <b>i</b>t <b>buff</b>ers <b>reco</b>rds <b>a</b>nd <b>wri</b>tes <b>th</b>em <b>t</b>o S3, <b>Reds</b>hift, <b>OpenS</b>earch, <b>Spl</b>unk <b>a</b>nd <b>oth</b>ers, <b>wi</b>th <b>n</b>o <b>co</b>de. <b>C</b>an <b>conv</b>ert JSON <b>t</b>o <b>Parq</b>uet <b>o</b>n <b>t</b>he <b>w</b>ay. (<b>Form</b>erly "<b>Kine</b>sis <b>Da</b>ta <b>Fire</b>hose".)

#### Amazon MSK
<b>Mana</b>ged <b>Apa</b>che <b>Kaf</b>ka. <b>Cho</b>ose <b>i</b>t <b>wh</b>en <b>t</b>he <b>te</b>am <b>alre</b>ady <b>us</b>es <b>Kaf</b>ka.

#### Managed Service for Apache Flink
<b>Ru</b>ns <b>Fli</b>nk <b>f</b>or <b>re</b>al-<b>ti</b>me <b>str</b>eam <b>proce</b>ssing (<b>wind</b>owed <b>aggreg</b>ations, <b>joi</b>ns). (<b>Form</b>erly "<b>Kine</b>sis <b>Da</b>ta <b>Analy</b>tics".)

#### AWS DMS
<b>Data</b>base <b>Migra</b>tion <b>Serv</b>ice: <b>cop</b>ies <b>datab</b>ases <b>t</b>o AWS (<b>o</b>ne-<b>ti</b>me **full load**) <b>a</b>nd <b>kee</b>ps <b>copy</b>ing <b>chan</b>ges (**CDC**).

#### Zero-ETL integrations
AWS-<b>mana</b>ged <b>autom</b>atic <b>replic</b>ation <b>fr</b>om <b>Aur</b>ora/RDS/<b>Dyna</b>moDB <b>in</b>to <b>Reds</b>hift, <b>wi</b>th <b>n</b>o <b>pipe</b>line <b>t</b>o <b>bui</b>ld.

#### AWS DataSync
<b>Mov</b>es <b>lar</b>ge <b>amou</b>nts <b>o</b>f <b>fil</b>es <b>fr</b>om <b>o</b>n-<b>prem</b>ises <b>fi</b>le <b>serv</b>ers (NFS/SMB/HDFS) <b>t</b>o S3/EFS <b>onl</b>ine.

#### AWS Transfer Family
<b>Mana</b>ged SFTP/FTP <b>serv</b>ers <b>th</b>at <b>sa</b>ve <b>uplo</b>ads <b>stra</b>ight <b>in</b>to S3, <b>s</b>o <b>part</b>ners <b>ke</b>ep <b>the</b>ir <b>exis</b>ting <b>fi</b>le-<b>tran</b>sfer <b>too</b>ls.

#### Amazon AppFlow
<b>N</b>o-<b>co</b>de <b>trans</b>fers <b>fr</b>om SaaS <b>ap</b>ps (<b>Sales</b>force, <b>Zend</b>esk, <b>Servi</b>ceNow…) <b>in</b>to S3/<b>Reds</b>hift.

#### AWS Snow Family
<b>Phys</b>ical <b>devi</b>ces AWS <b>shi</b>ps <b>t</b>o <b>y</b>ou; <b>y</b>ou <b>lo</b>ad <b>petab</b>ytes <b>on</b>to <b>th</b>em <b>a</b>nd <b>sh</b>ip <b>th</b>em <b>ba</b>ck. <b>Us</b>ed <b>wh</b>en <b>t</b>he <b>netw</b>ork <b>i</b>s <b>t</b>oo <b>sl</b>ow.

#### AWS Data Exchange
<b>A</b> <b>market</b>place <b>f</b>or <b>buy</b>ing/<b>subscr</b>ibing <b>t</b>o <b>thi</b>rd-<b>par</b>ty <b>data</b>sets.

### Processing and querying

#### AWS Glue
<b>Serve</b>rless <b>da</b>ta <b>integr</b>ation: **Glue jobs** <b>r</b>un <b>Spa</b>rk/<b>Pyt</b>hon ETL <b>with</b>out <b>serv</b>ers; <b>t</b>he **Glue Data Catalog** <b>sto</b>res <b>tab</b>le <b>defini</b>tions; **crawlers** <b>sc</b>an S3 <b>a</b>nd <b>cre</b>ate <b>tho</b>se <b>tab</b>le <b>defini</b>tions <b>automat</b>ically; **job bookmarks** <b>reme</b>mber <b>wha</b>t's <b>alre</b>ady <b>proce</b>ssed.

#### AWS Glue DataBrew
<b>A</b> <b>vis</b>ual, <b>n</b>o-<b>co</b>de <b>to</b>ol <b>f</b>or <b>clea</b>ning <b>a</b>nd <b>prepa</b>ring <b>da</b>ta (<b>f</b>ix <b>form</b>ats, <b>rem</b>ove <b>dupli</b>cates, <b>ma</b>sk PII) <b>wi</b>th 250+ <b>rea</b>dy-<b>ma</b>de <b>trans</b>forms.

#### AWS Glue Data Quality
<b>Da</b>ta-<b>qual</b>ity <b>rul</b>es (<b>writ</b>ten <b>i</b>n DQDL) <b>th</b>at <b>r</b>un <b>ins</b>ide <b>Gl</b>ue <b>jo</b>bs <b>o</b>r <b>agai</b>nst <b>cata</b>log <b>tab</b>les.

#### Amazon EMR
<b>Mana</b>ged <b>b</b>ig-<b>da</b>ta <b>clus</b>ters <b>runn</b>ing <b>Spa</b>rk, <b>Had</b>oop, <b>Hi</b>ve, <b>Pre</b>sto, <b>HBa</b>se, <b>Fli</b>nk… <b>Mo</b>re <b>cont</b>rol <b>a</b>nd <b>tun</b>ing <b>th</b>an <b>Gl</b>ue; <b>chea</b>pest <b>a</b>t <b>ve</b>ry <b>lar</b>ge <b>sca</b>le (<b>espec</b>ially <b>wi</b>th **Spot** <b>insta</b>nces, <b>disco</b>unted <b>spa</b>re <b>capa</b>city <b>th</b>at <b>c</b>an <b>b</b>e <b>tak</b>en <b>ba</b>ck).

#### Amazon Athena
<b>Serve</b>rless SQL <b>dire</b>ctly <b>o</b>n <b>fil</b>es <b>i</b>n S3. <b>N</b>o <b>serv</b>ers <b>o</b>r <b>load</b>ing; <b>y</b>ou <b>p</b>ay <b>p</b>er <b>da</b>ta <b>scan</b>ned. <b>Th</b>is <b>i</b>s <b>w</b>hy <b>Parq</b>uet <b>a</b>nd <b>partit</b>ioning <b>sa</b>ve <b>mon</b>ey.

#### AWS Lambda
<b>Ru</b>ns <b>sma</b>ll <b>pie</b>ces <b>o</b>f <b>co</b>de <b>i</b>n <b>resp</b>onse <b>t</b>o <b>eve</b>nts (<b>a</b> <b>fi</b>le <b>arri</b>ves, <b>a</b>n API <b>i</b>s <b>cal</b>led), <b>u</b>p <b>t</b>o 15 <b>minu</b>tes, <b>n</b>o <b>serv</b>ers. <b>P</b>ay <b>p</b>er <b>r</b>un.

#### Amazon ECS, EKS and Fargate
<b>Wa</b>ys <b>t</b>o <b>r</b>un <b>conta</b>iners: **ECS** <b>i</b>s AWS's <b>o</b>wn <b>conta</b>iner <b>serv</b>ice, **EKS** <b>i</b>s <b>mana</b>ged <b>Kuber</b>netes, <b>a</b>nd **Fargate** <b>ru</b>ns <b>conta</b>iners <b>f</b>or <b>eit</b>her <b>with</b>out <b>mana</b>ging <b>serv</b>ers.

#### AWS Batch
<b>Ru</b>ns <b>lar</b>ge <b>numb</b>ers <b>o</b>f <b>bat</b>ch <b>compu</b>ting <b>jo</b>bs (<b>conta</b>iners) <b>a</b>nd <b>mana</b>ges <b>t</b>he <b>comp</b>ute <b>f</b>or <b>y</b>ou.

### Orchestration and events

#### AWS Step Functions
<b>Serve</b>rless <b>workf</b>lows <b>dra</b>wn <b>a</b>s **state machines**: <b>r</b>un <b>Gl</b>ue → <b>Lam</b>bda → <b>Ath</b>ena <b>i</b>n <b>ord</b>er, <b>wi</b>th <b>retr</b>ies, <b>err</b>or <b>hand</b>ling, <b>para</b>llel <b>bran</b>ches <b>a</b>nd <b>wai</b>ts.

#### Amazon MWAA
<b>Mana</b>ged <b>Workf</b>lows <b>f</b>or <b>Apa</b>che <b>Airf</b>low: AWS <b>ru</b>ns <b>Airf</b>low <b>f</b>or <b>y</b>ou.

#### Amazon EventBridge
<b>A</b>n <b>eve</b>nt <b>b</b>us: <b>rou</b>tes <b>eve</b>nts ("<b>Gl</b>ue <b>j</b>ob <b>fai</b>led," "<b>fi</b>le <b>uplo</b>aded") <b>t</b>o <b>targ</b>ets (<b>Lam</b>bda, <b>St</b>ep <b>Funct</b>ions, SNS) <b>bas</b>ed <b>o</b>n <b>rul</b>es. **EventBridge Scheduler** <b>ru</b>ns <b>thi</b>ngs <b>o</b>n <b>a</b> <b>sche</b>dule (<b>cr</b>on).

#### Amazon SNS
<b>Sim</b>ple <b>Notifi</b>cation <b>Serv</b>ice: **push** <b>a</b> <b>mess</b>age <b>t</b>o <b>ma</b>ny <b>subscr</b>ibers <b>a</b>t <b>on</b>ce (<b>ema</b>il, SMS, <b>Lam</b>bda, SQS). <b>Us</b>ed <b>f</b>or <b>ale</b>rts <b>a</b>nd <b>f</b>an-<b>o</b>ut.

#### Amazon SQS
<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice: <b>a</b> **queue** <b>th</b>at <b>hol</b>ds <b>mess</b>ages <b>unt</b>il <b>a</b> <b>wor</b>ker <b>pul</b>ls <b>a</b>nd <b>proce</b>sses <b>th</b>em. <b>Decou</b>ples <b>fa</b>st <b>produ</b>cers <b>fr</b>om <b>slo</b>wer <b>consu</b>mers. <b>A</b> **dead-letter queue (DLQ)** <b>catc</b>hes <b>mess</b>ages <b>th</b>at <b>ke</b>ep <b>fail</b>ing.

### Analytics, BI and AI

#### Amazon QuickSight
AWS's BI (<b>busi</b>ness <b>intell</b>igence) <b>dashb</b>oard <b>to</b>ol. **SPICE** <b>i</b>s <b>i</b>ts <b>i</b>n-<b>mem</b>ory <b>eng</b>ine <b>f</b>or <b>fa</b>st <b>dashb</b>oards.

#### Amazon SageMaker Unified Studio and SageMaker Catalog
<b>O</b>ne <b>works</b>pace <b>f</b>or <b>da</b>ta <b>a</b>nd AI <b>wo</b>rk (SQL, <b>noteb</b>ooks, ETL, <b>mod</b>els). **SageMaker Catalog** <b>i</b>s <b>whe</b>re <b>peo</b>ple <b>sea</b>rch <b>f</b>or <b>data</b>sets, <b>requ</b>est <b>acc</b>ess <b>a</b>nd <b>s</b>ee <b>line</b>age (<b>bui</b>lt <b>o</b>n <b>Ama</b>zon <b>Data</b>Zone).

#### Amazon Bedrock
<b>Acc</b>ess <b>t</b>o <b>gener</b>ative-AI <b>mod</b>els (LLMs) <b>thro</b>ugh <b>a</b>n API. **Knowledge Bases** <b>han</b>dle RAG; **batch inference** <b>ru</b>ns <b>a</b> <b>mod</b>el <b>ov</b>er <b>ma</b>ny <b>reco</b>rds <b>chea</b>ply.

#### Amazon Comprehend
<b>Rea</b>dy-<b>ma</b>de <b>lang</b>uage AI: <b>senti</b>ment, <b>enti</b>ties, PII <b>detec</b>tion, <b>lang</b>uage <b>detec</b>tion, <b>with</b>out <b>writ</b>ing <b>prom</b>pts.

### Security and governance

#### AWS IAM
<b>Iden</b>tity <b>a</b>nd <b>Acc</b>ess <b>Manag</b>ement: <b>use</b>rs, **roles** <b>a</b>nd **policies** (JSON <b>docum</b>ents) <b>contro</b>lling <b>w</b>ho <b>c</b>an <b>d</b>o <b>wh</b>at <b>o</b>n <b>whi</b>ch <b>reso</b>urce. **IAM Identity Center** <b>giv</b>es <b>peo</b>ple <b>sin</b>gle <b>si</b>gn-<b>o</b>n.

#### AWS Lake Formation
<b>Cent</b>ral <b>permis</b>sions <b>f</b>or <b>a</b> <b>da</b>ta <b>la</b>ke: <b>gra</b>nt <b>acc</b>ess <b>t</b>o <b>datab</b>ases, <b>tab</b>les, <b>colu</b>mns <b>a</b>nd <b>ro</b>ws (<b>a</b>nd <b>v</b>ia **LF-tags**) <b>on</b>ce, <b>a</b>nd <b>Ath</b>ena, <b>Reds</b>hift <b>Spec</b>trum, EMR <b>a</b>nd <b>Gl</b>ue <b>a</b>ll <b>enfo</b>rce <b>i</b>t.

#### AWS KMS
<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice: <b>crea</b>tes <b>a</b>nd <b>cont</b>rols <b>t</b>he <b>encry</b>ption <b>ke</b>ys <b>us</b>ed <b>b</b>y S3, <b>Reds</b>hift, <b>e</b>tc., <b>a</b>nd <b>lo</b>gs <b>eve</b>ry <b>k</b>ey <b>u</b>se.

#### AWS Secrets Manager
<b>Sto</b>res <b>passw</b>ords <b>a</b>nd API <b>ke</b>ys <b>secu</b>rely, <b>a</b>nd <b>c</b>an <b>rot</b>ate <b>th</b>em <b>automat</b>ically, <b>s</b>o <b>th</b>ey <b>nev</b>er <b>s</b>it <b>i</b>n <b>co</b>de.

#### Amazon Macie
<b>Sca</b>ns S3 <b>a</b>nd <b>fin</b>ds <b>sensi</b>tive <b>da</b>ta (PII, <b>cre</b>dit <b>car</b>ds, <b>creden</b>tials) <b>automat</b>ically.

#### AWS CloudTrail
<b>Lo</b>gs <b>eve</b>ry API <b>ca</b>ll <b>ma</b>de <b>i</b>n <b>yo</b>ur <b>acco</b>unt (<b>w</b>ho <b>d</b>id <b>wh</b>at, <b>wh</b>en, <b>fr</b>om <b>whe</b>re). <b>T</b>he <b>aud</b>it <b>tra</b>il. **CloudTrail Lake** <b>le</b>ts <b>y</b>ou <b>que</b>ry <b>tho</b>se <b>lo</b>gs <b>wi</b>th SQL.

#### Amazon CloudWatch
<b>Monit</b>oring: **metrics** (<b>numb</b>ers <b>ov</b>er <b>ti</b>me), **alarms** (<b>ale</b>rt <b>wh</b>en <b>a</b> <b>met</b>ric <b>cros</b>ses <b>a</b> <b>li</b>ne) <b>a</b>nd **Logs** (<b>applic</b>ation/<b>serv</b>ice <b>lo</b>gs, <b>searc</b>hable <b>wi</b>th <b>Lo</b>gs <b>Insi</b>ghts).

#### AWS Config
<b>Reco</b>rds <b>h</b>ow <b>yo</b>ur <b>resou</b>rces <b>a</b>re <b>confi</b>gured <b>ov</b>er <b>ti</b>me <b>a</b>nd <b>che</b>cks <b>th</b>em <b>agai</b>nst <b>rul</b>es (<b>e</b>.g., "<b>a</b>ll <b>buck</b>ets <b>mu</b>st <b>b</b>e <b>encry</b>pted").

#### Amazon VPC
<b>Virt</b>ual <b>Priv</b>ate <b>Clo</b>ud: <b>yo</b>ur <b>o</b>wn <b>priv</b>ate <b>netw</b>ork <b>ins</b>ide AWS. **Security groups** <b>a</b>re <b>firew</b>alls <b>aro</b>und <b>resou</b>rces; **subnets** <b>div</b>ide <b>t</b>he <b>netw</b>ork; <b>a</b> **NAT gateway** <b>le</b>ts <b>priv</b>ate <b>resou</b>rces <b>rea</b>ch <b>t</b>he <b>inte</b>rnet; **VPC endpoints** <b>rea</b>ch AWS <b>serv</b>ices <b>with</b>out <b>t</b>he <b>inte</b>rnet.

### Building and deploying

#### AWS CloudFormation, CDK and SAM
<b>Infrast</b>ructure <b>a</b>s <b>Co</b>de: <b>desc</b>ribe <b>yo</b>ur <b>resou</b>rces <b>i</b>n <b>fil</b>es, <b>a</b>nd AWS <b>crea</b>tes <b>th</b>em <b>t</b>he <b>sa</b>me <b>w</b>ay <b>eve</b>ry <b>ti</b>me. **CloudFormation** <b>us</b>es YAML/JSON <b>templ</b>ates; **CDK** <b>le</b>ts <b>y</b>ou <b>wri</b>te <b>th</b>em <b>i</b>n <b>Pyt</b>hon/<b>TypeS</b>cript; **SAM** <b>i</b>s <b>a</b> <b>shor</b>tcut <b>f</b>or <b>serve</b>rless <b>ap</b>ps (<b>Lam</b>bda, <b>St</b>ep <b>Funct</b>ions).
