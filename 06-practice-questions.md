# DEA-C01 Practice Questions (20)

> 🔰 <b>N</b>ew <b>t</b>o <b>da</b>ta? <b>Ea</b>ch <b>too</b>l's <b>fir</b>st <b>ment</b>ion <b>lin</b>ks <b>t</b>o <b>a</b> <b>pla</b>in-<b>Engl</b>ish <b>explan</b>ation <b>i</b>n [<b>Da</b>ta <b>Bas</b>ics <b>f</b>or <b>Begin</b>ners](00-data-basics-for-beginners.md). <b>Abbrevi</b>ations <b>a</b>re <b>lis</b>ted <b>i</b>n <b>t</b>he [<b>glos</b>sary](00-abbreviations-glossary.md).

> <b>Ans</b>wer <b>ea</b>ch <b>ques</b>tion <b>fir</b>st, <b>th</b>en <b>exp</b>and <b>t</b>he <b>explan</b>ation.

---

**1.** <b>A</b> <b>comp</b>any <b>inge</b>sts <b>clicks</b>tream <b>eve</b>nts <b>a</b>t 4,000 <b>reco</b>rds/<b>sec</b>ond, <b>ea</b>ch 1.5 KB. <b>Thr</b>ee <b>applic</b>ations <b>mu</b>st <b>ea</b>ch <b>re</b>ad <b>eve</b>ry <b>eve</b>nt <b>i</b>n <b>re</b>al <b>ti</b>me, <b>a</b>nd <b>t</b>he <b>da</b>ta <b>mu</b>st <b>b</b>e <b>reproce</b>ssable <b>f</b>or 7 <b>da</b>ys. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>mo</b>st <b>co</b>st-<b>effec</b>tive <b>des</b>ign?

- <b>A</b>. [<b>Ama</b>zon <b>Da</b>ta <b>Fire</b>hose](00-data-basics-for-beginners.md#amazon-data-firehose) <b>deliv</b>ering <b>t</b>o [<b>Sim</b>ple <b>Stor</b>age <b>Serv</b>ice [S3]](00-data-basics-for-beginners.md#amazon-s3) <b>wi</b>th <b>thr</b>ee [<b>Lam</b>bda](00-data-basics-for-beginners.md#aws-lambda) <b>transfor</b>mations
- <b>B</b>. [<b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams](00-data-basics-for-beginners.md#amazon-kinesis-data-streams) <b>wi</b>th 6 <b>sha</b>rds, 7-<b>d</b>ay <b>reten</b>tion, <b>a</b>nd <b>enha</b>nced <b>f</b>an-<b>o</b>ut <b>consu</b>mers
- <b>C</b>. <b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams <b>wi</b>th 4 <b>sha</b>rds <b>a</b>nd <b>defa</b>ult <b>reten</b>tion
- <b>D</b>. <b>Ama</b>zon [<b>Sim</b>ple <b>Que</b>ue <b>Serv</b>ice [SQS]](00-data-basics-for-beginners.md#amazon-sqs) <b>stan</b>dard <b>que</b>ue <b>wi</b>th <b>thr</b>ee <b>consu</b>mers

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Ing</b>est = 6 MB/<b>s</b> <b>a</b>nd 4,000 <b>r</b>ec/<b>s</b> → 6 <b>sha</b>rds (<b>t</b>he MB <b>lim</b>it <b>domin</b>ates). <b>Mult</b>iple <b>re</b>al-<b>ti</b>me <b>consu</b>mers <b>read</b>ing <b>every</b>thing → <b>enha</b>nced <b>f</b>an-<b>o</b>ut. <b>Rep</b>lay <b>f</b>or 7 <b>da</b>ys → <b>ext</b>end <b>reten</b>tion. <b>Fire</b>hose <b>a</b>nd SQS <b>can</b>'t <b>rep</b>lay, <b>a</b>nd 4 <b>sha</b>rds <b>can</b>'t <b>abs</b>orb 6 MB/<b>s</b>.
</details>

---

**2.** [<b>JavaS</b>cript <b>Obj</b>ect <b>Nota</b>tion [JSON]](00-data-basics-for-beginners.md#json) <b>eve</b>nts <b>arr</b>ive <b>contin</b>uously <b>a</b>nd <b>mu</b>st <b>la</b>nd <b>i</b>n S3 <b>a</b>s [<b>Parq</b>uet](00-data-basics-for-beginners.md#parquet), <b>partit</b>ioned <b>b</b>y `customer_id`, <b>wi</b>th <b>t</b>he <b>lea</b>st <b>operat</b>ional <b>over</b>head.

- <b>A</b>. <b>Kine</b>sis <b>Da</b>ta <b>Stre</b>ams + <b>Lam</b>bda <b>conve</b>rting <b>t</b>o <b>Parq</b>uet
- <b>B</b>. <b>Fire</b>hose <b>wi</b>th <b>rec</b>ord <b>for</b>mat <b>conve</b>rsion ([<b>Gl</b>ue](00-data-basics-for-beginners.md#aws-glue) <b>tab</b>le <b>sch</b>ema) <b>a</b>nd <b>dyna</b>mic <b>partit</b>ioning
- <b>C</b>. <b>Gl</b>ue <b>strea</b>ming <b>j</b>ob <b>writ</b>ing [<b>Com</b>ma-<b>Separ</b>ated <b>Val</b>ues [CSV]](00-data-basics-for-beginners.md#csv), <b>th</b>en <b>a</b> <b>nigh</b>tly <b>craw</b>ler
- <b>D</b>. [<b>Mana</b>ged <b>Strea</b>ming <b>f</b>or <b>Apa</b>che <b>Kaf</b>ka [MSK]](00-data-basics-for-beginners.md#amazon-msk) + MSK <b>Conn</b>ect S3 <b>si</b>nk <b>i</b>n JSON <b>for</b>mat

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Fire</b>hose <b>conv</b>erts JSON <b>t</b>o <b>Parq</b>uet <b>nati</b>vely <b>usi</b>ng <b>a</b> <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log <b>sch</b>ema, <b>a</b>nd <b>dyna</b>mic <b>partit</b>ioning <b>wri</b>tes `customer_id=` <b>pref</b>ixes. <b>N</b>o <b>co</b>de <b>t</b>o <b>main</b>tain.
</details>

---

**3.** <b>A</b> <b>nigh</b>tly <b>Gl</b>ue <b>j</b>ob <b>reproc</b>esses <b>a</b>ll <b>fil</b>es <b>i</b>n <b>a</b>n S3 <b>pre</b>fix, <b>ev</b>en <b>tho</b>ugh <b>on</b>ly <b>a</b> <b>f</b>ew <b>n</b>ew <b>fil</b>es <b>arr</b>ive <b>ea</b>ch <b>d</b>ay. <b>Cos</b>ts <b>a</b>re <b>ris</b>ing. <b>Wh</b>at <b>sho</b>uld <b>t</b>he <b>da</b>ta <b>engi</b>neer <b>d</b>o? (<b>Cho</b>ose TWO.)

- <b>A</b>. <b>Ena</b>ble <b>j</b>ob <b>bookm</b>arks
- <b>B</b>. <b>Incr</b>ease <b>t</b>he <b>num</b>ber <b>o</b>f <b>work</b>ers
- <b>C</b>. <b>U</b>se <b>Fl</b>ex <b>execu</b>tion <b>f</b>or <b>t</b>he <b>j</b>ob
- <b>D</b>. <b>Swi</b>tch <b>t</b>o <b>a</b> <b>Pyt</b>hon <b>she</b>ll <b>j</b>ob <b>wi</b>th <b>pan</b>das
- <b>E</b>. <b>R</b>un <b>a</b> <b>craw</b>ler <b>bef</b>ore <b>ea</b>ch <b>j</b>ob

<details><summary><b>Ans</b>wer</summary>

**A, C.** <b>Bookm</b>arks <b>proc</b>ess <b>on</b>ly <b>n</b>ew <b>fil</b>es. <b>Fl</b>ex <b>low</b>ers <b>co</b>st <b>f</b>or <b>n</b>on-<b>urg</b>ent <b>jo</b>bs. <b>Mo</b>re <b>work</b>ers <b>incre</b>ases <b>co</b>st, <b>a</b>nd <b>Pyt</b>hon <b>she</b>ll <b>m</b>ay <b>n</b>ot <b>han</b>dle <b>Spa</b>rk-<b>sca</b>le <b>da</b>ta.
</details>

---

**4.** <b>A</b> <b>Lam</b>bda <b>func</b>tion <b>consu</b>ming <b>a</b> <b>Kine</b>sis <b>str</b>eam <b>kee</b>ps <b>fail</b>ing <b>o</b>n <b>o</b>ne <b>malfo</b>rmed <b>rec</b>ord, <b>a</b>nd <b>t</b>he <b>sha</b>rd <b>sto</b>ps <b>progre</b>ssing. <b>Wh</b>at <b>fix</b>es <b>th</b>is <b>whi</b>le <b>keep</b>ing <b>oth</b>er <b>reco</b>rds <b>flow</b>ing?

- <b>A</b>. <b>Incr</b>ease <b>t</b>he <b>Lam</b>bda <b>time</b>out
- <b>B</b>. <b>Ena</b>ble <b>bis</b>ect <b>bat</b>ch <b>o</b>n <b>func</b>tion <b>err</b>or, <b>s</b>et <b>maxi</b>mum <b>ret</b>ry <b>atte</b>mpts, <b>a</b>nd <b>confi</b>gure <b>a</b>n <b>o</b>n-<b>fail</b>ure <b>destin</b>ation (SQS)
- <b>C</b>. <b>Incr</b>ease <b>t</b>he <b>sha</b>rd <b>cou</b>nt
- <b>D</b>. <b>Swi</b>tch <b>t</b>he <b>star</b>ting <b>posi</b>tion <b>t</b>o LATEST

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Bisec</b>ting <b>isol</b>ates <b>t</b>he <b>poi</b>son <b>rec</b>ord, <b>boun</b>ded <b>retr</b>ies <b>st</b>op <b>t</b>he <b>bloc</b>king, <b>a</b>nd <b>t</b>he <b>o</b>n-<b>fail</b>ure <b>destin</b>ation <b>kee</b>ps <b>t</b>he <b>fai</b>led <b>reco</b>rd's <b>meta</b>data <b>f</b>or <b>lat</b>er <b>rev</b>iew.
</details>

---

**5.** <b>Anal</b>ysts <b>que</b>ry <b>a</b> 50 TB <b>clicks</b>tream <b>tab</b>le <b>i</b>n [<b>Ath</b>ena](00-data-basics-for-beginners.md#amazon-athena) <b>b</b>y <b>da</b>te. <b>Quer</b>ies <b>a</b>re <b>sl</b>ow <b>a</b>nd <b>expen</b>sive. <b>T</b>he <b>tab</b>le <b>i</b>s <b>sto</b>red <b>a</b>s GZIP CSV <b>wi</b>th <b>n</b>o <b>parti</b>tions. <b>Whi</b>ch <b>chan</b>ges <b>gi</b>ve <b>t</b>he <b>bigg</b>est <b>improv</b>ement? (<b>Cho</b>ose TWO.)

- <b>A</b>. <b>Conv</b>ert <b>t</b>o <b>Parq</b>uet <b>wi</b>th <b>Sna</b>ppy <b>compre</b>ssion
- <b>B</b>. <b>Parti</b>tion <b>b</b>y <b>da</b>te
- <b>C</b>. <b>Incr</b>ease <b>t</b>he <b>Ath</b>ena <b>workg</b>roup <b>da</b>ta <b>lim</b>it
- <b>D</b>. <b>A</b>dd `LIMIT 100` <b>t</b>o <b>quer</b>ies
- <b>E</b>. <b>Mo</b>ve <b>t</b>he <b>da</b>ta <b>t</b>o S3 <b>Stan</b>dard-<b>Infre</b>quent <b>Acc</b>ess (<b>Stan</b>dard-IA)

<details><summary><b>Ans</b>wer</summary>

**A, B.** <b>Colu</b>mnar <b>for</b>mat <b>pl</b>us <b>parti</b>tion <b>prun</b>ing <b>dramat</b>ically <b>c</b>ut <b>da</b>ta <b>scan</b>ned. `LIMIT` <b>does</b>n't <b>red</b>uce <b>da</b>ta <b>scan</b>ned, <b>a</b>nd <b>stor</b>age <b>cla</b>ss <b>does</b>n't <b>aff</b>ect <b>que</b>ry <b>spe</b>ed.
</details>

---

**6.** <b>A</b> [<b>Reds</b>hift](00-data-basics-for-beginners.md#amazon-redshift) <b>que</b>ry <b>join</b>ing <b>a</b> 2-<b>bill</b>ion-<b>r</b>ow `sales` <b>fa</b>ct <b>tab</b>le <b>wi</b>th <b>a</b> 1-<b>bill</b>ion-<b>r</b>ow `customers` <b>tab</b>le <b>o</b>n `customer_id` <b>sho</b>ws `DS_DIST_BOTH` <b>i</b>n <b>t</b>he <b>pl</b>an. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>be</b>st <b>f</b>ix?

- <b>A</b>. <b>S</b>et `DISTSTYLE ALL` <b>o</b>n <b>bo</b>th <b>tab</b>les
- <b>B</b>. <b>S</b>et `DISTKEY(customer_id)` <b>o</b>n <b>bo</b>th <b>tab</b>les
- <b>C</b>. <b>A</b>dd <b>a</b>n <b>interl</b>eaved <b>so</b>rt <b>k</b>ey
- <b>D</b>. <b>Ena</b>ble <b>concur</b>rency <b>scal</b>ing

<details><summary><b>Ans</b>wer</summary>

**B.** <b>C</b>o-<b>loca</b>ting <b>bo</b>th <b>lar</b>ge <b>tab</b>les <b>o</b>n <b>t</b>he <b>jo</b>in <b>k</b>ey <b>remo</b>ves <b>redistr</b>ibution. `ALL` <b>i</b>s <b>on</b>ly <b>f</b>or <b>sma</b>ll <b>tab</b>les.
</details>

---

**7.** <b>A</b> <b>comp</b>any <b>nee</b>ds <b>t</b>o <b>del</b>ete <b>indiv</b>idual <b>custo</b>mers' <b>reco</b>rds <b>fr</b>om <b>i</b>ts S3 [<b>da</b>ta <b>la</b>ke](00-data-basics-for-beginners.md#data-lake) <b>wit</b>hin 30 <b>da</b>ys <b>o</b>f <b>requ</b>est (<b>Gene</b>ral <b>Da</b>ta <b>Prote</b>ction <b>Regul</b>ation [GDPR]) <b>with</b>out <b>rewri</b>ting <b>ent</b>ire <b>parti</b>tions <b>manu</b>ally. <b>Wh</b>at <b>sho</b>uld <b>i</b>t <b>u</b>se?

- <b>A</b>. S3 <b>Lifec</b>ycle <b>expir</b>ation <b>rul</b>es
- <b>B</b>. [<b>Apa</b>che <b>Iceb</b>erg](00-data-basics-for-beginners.md#apache-iceberg) <b>tab</b>les <b>wi</b>th `DELETE` <b>state</b>ments <b>i</b>n <b>Ath</b>ena, <b>foll</b>owed <b>b</b>y <b>snap</b>shot <b>expir</b>ation
- <b>C</b>. S3 <b>Obj</b>ect <b>Lo</b>ck <b>gover</b>nance <b>mo</b>de
- <b>D</b>. [<b>Dyna</b>moDB](00-data-basics-for-beginners.md#amazon-dynamodb) <b>Ti</b>me <b>T</b>o <b>Li</b>ve (TTL)

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Iceb</b>erg <b>supp</b>orts <b>r</b>ow-<b>lev</b>el <b>dele</b>tes, <b>a</b>nd <b>expi</b>ring <b>snaps</b>hots <b>remo</b>ves <b>t</b>he <b>o</b>ld <b>da</b>ta <b>fil</b>es. <b>Lifec</b>ycle <b>wor</b>ks <b>o</b>n <b>who</b>le <b>obje</b>cts <b>b</b>y <b>a</b>ge, <b>a</b>nd <b>Obj</b>ect <b>Lo</b>ck <b>prev</b>ents <b>dele</b>tion.
</details>

---

**8.** <b>A</b>n <b>applic</b>ation <b>nee</b>ds <b>sema</b>ntic <b>sea</b>rch <b>ov</b>er <b>prod</b>uct <b>descri</b>ptions <b>sto</b>red <b>along</b>side <b>relat</b>ional <b>ord</b>er <b>da</b>ta, <b>wi</b>th <b>hi</b>gh <b>rec</b>all <b>a</b>nd <b>l</b>ow <b>late</b>ncy. <b>Mem</b>ory <b>i</b>s <b>n</b>ot <b>a</b> <b>conc</b>ern. <b>Wh</b>at <b>sho</b>uld <b>t</b>he <b>da</b>ta <b>engi</b>neer <b>cho</b>ose?

- <b>A</b>. [<b>Aur</b>ora](00-data-basics-for-beginners.md#amazon-aurora) [<b>Postg</b>reSQL](00-data-basics-for-beginners.md#postgresql-mysql-oracle-and-sql-server) <b>wi</b>th <b>pgve</b>ctor <b>a</b>nd <b>a</b> <b>Hierar</b>chical <b>Navig</b>able <b>Sma</b>ll <b>Wor</b>ld (HNSW) <b>ind</b>ex
- <b>B</b>. <b>Aur</b>ora <b>Postg</b>reSQL <b>wi</b>th <b>pgve</b>ctor <b>a</b>nd <b>a</b>n IVFFlat <b>ind</b>ex <b>trai</b>ned <b>o</b>n <b>a</b> <b>sma</b>ll <b>sam</b>ple
- <b>C</b>. <b>Dyna</b>moDB <b>wi</b>th <b>a</b> <b>Glo</b>bal <b>Secon</b>dary <b>Ind</b>ex (GSI) <b>o</b>n <b>t</b>he <b>embed</b>ding
- <b>D</b>. <b>Ath</b>ena <b>ov</b>er <b>Parq</b>uet [<b>embed</b>dings](00-data-basics-for-beginners.md#vectors-and-embeddings)

<details><summary><b>Ans</b>wer</summary>

**A.** HNSW <b>giv</b>es <b>hi</b>gh <b>rec</b>all <b>a</b>nd <b>fa</b>st <b>quer</b>ies <b>a</b>t <b>t</b>he <b>co</b>st <b>o</b>f <b>mem</b>ory, <b>whi</b>ch <b>i</b>s <b>accep</b>table <b>he</b>re. <b>pgve</b>ctor <b>kee</b>ps <b>vect</b>ors <b>ne</b>xt <b>t</b>o <b>relat</b>ional <b>da</b>ta.
</details>

---

**9.** <b>Ath</b>ena <b>quer</b>ies <b>o</b>n <b>a</b> <b>tab</b>le <b>wi</b>th <b>dai</b>ly <b>parti</b>tions <b>span</b>ning 10 <b>yea</b>rs <b>a</b>re <b>sl</b>ow <b>i</b>n <b>t</b>he <b>plan</b>ning <b>pha</b>se, <b>a</b>nd <b>n</b>ew <b>parti</b>tions <b>mu</b>st <b>app</b>ear <b>immedi</b>ately <b>with</b>out <b>craw</b>lers. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>be</b>st <b>solu</b>tion?

- <b>A</b>. <b>R</b>un `MSCK REPAIR TABLE` <b>hou</b>rly
- <b>B</b>. <b>Confi</b>gure <b>parti</b>tion <b>proje</b>ction <b>o</b>n <b>t</b>he <b>tab</b>le
- <b>C</b>. <b>R</b>un <b>t</b>he <b>craw</b>ler <b>eve</b>ry 5 <b>minu</b>tes
- <b>D</b>. <b>Conv</b>ert <b>t</b>he <b>tab</b>le <b>t</b>o CSV

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Parti</b>tion <b>proje</b>ction <b>comp</b>utes <b>parti</b>tions <b>fr</b>om <b>tab</b>le <b>prope</b>rties, <b>remo</b>ving <b>cata</b>log <b>look</b>ups <b>a</b>nd <b>t</b>he <b>ne</b>ed <b>t</b>o <b>regi</b>ster <b>n</b>ew <b>parti</b>tions.
</details>

---

**10.** <b>A</b> <b>te</b>am <b>wan</b>ts [<b>Kaf</b>ka](00-data-basics-for-beginners.md#apache-kafka) <b>produ</b>cers <b>t</b>o <b>st</b>op <b>publi</b>shing <b>mess</b>ages <b>who</b>se [<b>Av</b>ro](00-data-basics-for-beginners.md#avro) <b>sch</b>ema <b>wou</b>ld <b>bre</b>ak <b>exis</b>ting <b>consu</b>mers. <b>Wh</b>at <b>sho</b>uld <b>b</b>e <b>us</b>ed?

- <b>A</b>. <b>Gl</b>ue <b>craw</b>ler <b>wi</b>th <b>sch</b>ema <b>cha</b>nge <b>pol</b>icy "<b>upd</b>ate <b>t</b>he <b>tab</b>le <b>defin</b>ition"
- <b>B</b>. <b>Ama</b>zon <b>W</b>eb <b>Serv</b>ices (AWS) <b>Gl</b>ue <b>Sch</b>ema <b>Regi</b>stry <b>wi</b>th BACKWARD <b>compati</b>bility
- <b>C</b>. <b>La</b>ke <b>Forma</b>tion <b>ta</b>gs (LF-<b>ta</b>gs)
- <b>D</b>. [<b>Data</b>base <b>Migra</b>tion <b>Serv</b>ice [DMS]](00-data-basics-for-beginners.md#aws-dms) <b>Sch</b>ema <b>Conve</b>rsion

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Sch</b>ema <b>Regi</b>stry <b>valid</b>ates <b>n</b>ew <b>sch</b>ema <b>vers</b>ions <b>agai</b>nst <b>t</b>he <b>compati</b>bility <b>mo</b>de <b>bef</b>ore <b>produ</b>cers <b>c</b>an <b>u</b>se <b>th</b>em.
</details>

---

**11.** <b>A</b> [<b>St</b>ep <b>Funct</b>ions](00-data-basics-for-beginners.md#aws-step-functions) <b>Expr</b>ess <b>work</b>flow <b>fai</b>ls <b>intermi</b>ttently, <b>b</b>ut <b>t</b>he <b>cons</b>ole <b>sho</b>ws <b>n</b>o <b>execu</b>tion <b>hist</b>ory. <b>Wh</b>at <b>sho</b>uld <b>t</b>he <b>engi</b>neer <b>d</b>o <b>fir</b>st?

- <b>A</b>. <b>Conv</b>ert <b>t</b>o <b>a</b> <b>Stan</b>dard <b>work</b>flow <b>perman</b>ently
- <b>B</b>. <b>Ena</b>ble [<b>Cloud</b>Watch](00-data-basics-for-beginners.md#amazon-cloudwatch) <b>Lo</b>gs (<b>lev</b>el ALL <b>o</b>r ERROR) <b>f</b>or <b>t</b>he <b>sta</b>te <b>mach</b>ine
- <b>C</b>. <b>Ena</b>ble [<b>Cloud</b>Trail](00-data-basics-for-beginners.md#aws-cloudtrail) <b>da</b>ta <b>eve</b>nts
- <b>D</b>. <b>Incr</b>ease <b>t</b>he <b>payl</b>oad <b>si</b>ze <b>lim</b>it

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Expr</b>ess <b>workf</b>lows <b>rec</b>ord <b>execu</b>tion <b>deta</b>ils <b>on</b>ly <b>i</b>n <b>Cloud</b>Watch <b>Lo</b>gs <b>wh</b>en <b>logg</b>ing <b>i</b>s <b>enab</b>led.
</details>

---

**12.** <b>A</b> <b>Gl</b>ue <b>Extr</b>act, <b>Trans</b>form, <b>Lo</b>ad (ETL) <b>j</b>ob <b>mu</b>st <b>st</b>op <b>load</b>ing <b>da</b>ta <b>in</b>to <b>Reds</b>hift <b>wh</b>en <b>mo</b>re <b>th</b>an 5% <b>o</b>f `email` <b>val</b>ues <b>a</b>re <b>nu</b>ll, <b>a</b>nd <b>rou</b>te <b>b</b>ad <b>ro</b>ws <b>t</b>o <b>a</b> <b>quara</b>ntine <b>pre</b>fix <b>other</b>wise. <b>Wh</b>at <b>sho</b>uld <b>b</b>e <b>us</b>ed?

- <b>A</b>. <b>A</b> [<b>Data</b>Brew](00-data-basics-for-beginners.md#aws-glue-databrew) <b>prof</b>ile <b>j</b>ob <b>r</b>un <b>wee</b>kly
- <b>B</b>. [<b>Gl</b>ue <b>Da</b>ta <b>Qual</b>ity](00-data-basics-for-beginners.md#aws-glue-data-quality)'<b>s</b> <b>Eval</b>uate <b>Da</b>ta <b>Qual</b>ity <b>trans</b>form <b>wi</b>th <b>Da</b>ta <b>Qual</b>ity <b>Defin</b>ition <b>Lang</b>uage (DQDL) <b>rul</b>es <b>ins</b>ide <b>t</b>he <b>j</b>ob
- <b>C</b>. <b>Ath</b>ena <b>quer</b>ies <b>sched</b>uled <b>b</b>y [<b>EventB</b>ridge](00-data-basics-for-beginners.md#amazon-eventbridge)
- <b>D</b>. [<b>Mac</b>ie](00-data-basics-for-beginners.md#amazon-macie) <b>sensi</b>tive <b>da</b>ta <b>disco</b>very

<details><summary><b>Ans</b>wer</summary>

**B.** <b>I</b>n-<b>j</b>ob DQDL <b>rul</b>es (<b>e</b>.g., `Completeness "email" > 0.95`) <b>c</b>an <b>fa</b>il <b>t</b>he <b>j</b>ob <b>o</b>r <b>rou</b>te <b>fail</b>ing <b>reco</b>rds <b>dur</b>ing <b>proce</b>ssing.
</details>

---

**13.** <b>A</b> [<b>Spa</b>rk](00-data-basics-for-beginners.md#apache-spark) <b>j</b>ob <b>o</b>n [<b>Elas</b>tic <b>MapRe</b>duce [EMR]](00-data-basics-for-beginners.md#amazon-emr) <b>h</b>as <b>o</b>ne <b>ta</b>sk <b>runn</b>ing 40 <b>minu</b>tes <b>whi</b>le <b>oth</b>ers <b>fin</b>ish <b>i</b>n 2 <b>minu</b>tes. <b>T</b>he <b>jo</b>in <b>k</b>ey `country` <b>h</b>as 70% <b>o</b>f <b>ro</b>ws <b>wi</b>th <b>val</b>ue `US`. <b>Whi</b>ch <b>mecha</b>nisms <b>red</b>uce <b>t</b>he <b>prob</b>lem? (<b>Cho</b>ose TWO.)

- <b>A</b>. <b>Sa</b>lt <b>t</b>he `country` <b>k</b>ey <b>a</b>nd <b>aggre</b>gate <b>i</b>n <b>t</b>wo <b>sta</b>ges
- <b>B</b>. <b>Broad</b>cast <b>t</b>he <b>smal</b>ler <b>tab</b>le <b>i</b>n <b>t</b>he <b>jo</b>in
- <b>C</b>. <b>A</b>dd <b>mo</b>re <b>co</b>re <b>nod</b>es
- <b>D</b>. <b>Sto</b>re <b>t</b>he <b>da</b>ta <b>a</b>s CSV
- <b>E</b>. <b>Disa</b>ble <b>Adap</b>tive <b>Que</b>ry <b>Execu</b>tion

<details><summary><b>Ans</b>wer</summary>

**A, B.** <b>Salt</b>ing <b>spre</b>ads <b>t</b>he <b>h</b>ot <b>k</b>ey, <b>a</b>nd <b>broadc</b>asting <b>avo</b>ids <b>shuff</b>ling <b>t</b>he <b>ske</b>wed <b>si</b>de. <b>Mo</b>re <b>nod</b>es <b>don</b>'t <b>he</b>lp <b>a</b> <b>sin</b>gle <b>overl</b>oaded <b>ta</b>sk.
</details>

---

**14.** <b>T</b>he <b>secu</b>rity <b>te</b>am <b>mu</b>st <b>fi</b>nd <b>o</b>ut <b>w</b>ho <b>dele</b>ted <b>obje</b>cts <b>fr</b>om <b>a</b> <b>produ</b>ction S3 <b>buc</b>ket <b>la</b>st <b>we</b>ek. <b>Wh</b>at <b>mu</b>st <b>alre</b>ady <b>ha</b>ve <b>be</b>en <b>enab</b>led?

- <b>A</b>. [AWS <b>Con</b>fig](00-data-basics-for-beginners.md#aws-config) <b>f</b>or S3
- <b>B</b>. <b>Cloud</b>Trail <b>da</b>ta <b>eve</b>nts <b>f</b>or <b>t</b>he <b>buc</b>ket (<b>o</b>r S3 <b>ser</b>ver <b>acc</b>ess <b>lo</b>gs)
- <b>C</b>. <b>Cloud</b>Watch <b>Lo</b>gs <b>Insi</b>ghts
- <b>D</b>. <b>Mac</b>ie <b>autom</b>ated <b>disco</b>very

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Obj</b>ect-<b>lev</b>el [<b>Applic</b>ation <b>Progra</b>mming <b>Inter</b>face [API]](00-data-basics-for-beginners.md#api) <b>cal</b>ls <b>li</b>ke `DeleteObject` <b>a</b>re <b>da</b>ta <b>eve</b>nts, <b>whi</b>ch <b>are</b>n't <b>reco</b>rded <b>b</b>y <b>defa</b>ult. <b>Ser</b>ver <b>acc</b>ess <b>lo</b>gs <b>al</b>so <b>capt</b>ure <b>requ</b>ests.
</details>

---

**15.** <b>Acco</b>unt <b>B</b>'s <b>Ath</b>ena <b>use</b>rs <b>can</b>'t <b>re</b>ad S3 <b>obje</b>cts <b>i</b>n <b>acco</b>unt <b>A</b>, <b>ev</b>en <b>tho</b>ugh <b>t</b>he <b>buc</b>ket <b>pol</b>icy <b>gra</b>nts <b>acco</b>unt <b>B</b> <b>acc</b>ess. <b>Obje</b>cts <b>a</b>re <b>encry</b>pted <b>wi</b>th <b>t</b>he `aws/s3` <b>k</b>ey. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>f</b>ix?

- <b>A</b>. <b>A</b>dd <b>acco</b>unt <b>B</b> <b>t</b>o <b>t</b>he `aws/s3` <b>k</b>ey <b>pol</b>icy
- <b>B</b>. <b>R</b>e-<b>encr</b>ypt <b>t</b>he <b>obje</b>cts <b>wi</b>th <b>a</b> <b>cust</b>omer <b>mana</b>ged [<b>K</b>ey <b>Manag</b>ement <b>Serv</b>ice [KMS]](00-data-basics-for-beginners.md#aws-kms) <b>k</b>ey <b>who</b>se <b>k</b>ey <b>pol</b>icy <b>all</b>ows <b>acco</b>unt <b>B</b>, <b>a</b>nd <b>gra</b>nt `kms:Decrypt` <b>i</b>n <b>acco</b>unt <b>B</b>'s [<b>Iden</b>tity <b>a</b>nd <b>Acc</b>ess <b>Manag</b>ement [IAM]](00-data-basics-for-beginners.md#aws-iam) <b>poli</b>cies
- <b>C</b>. <b>Ena</b>ble S3 <b>Buc</b>ket <b>Ke</b>ys
- <b>D</b>. <b>Swi</b>tch <b>t</b>o <b>Ser</b>ver-<b>Si</b>de <b>Encry</b>ption <b>wi</b>th <b>Cust</b>omer-<b>prov</b>ided <b>ke</b>ys (SSE-<b>C</b>)

<details><summary><b>Ans</b>wer</summary>

**B.** AWS <b>mana</b>ged <b>ke</b>ys <b>can</b>'t <b>b</b>e <b>sha</b>red <b>cro</b>ss-<b>acco</b>unt. <b>A</b> <b>cust</b>omer <b>mana</b>ged <b>k</b>ey <b>wi</b>th <b>a</b> <b>k</b>ey <b>pol</b>icy <b>pl</b>us <b>cons</b>umer IAM <b>permis</b>sions <b>i</b>s <b>requ</b>ired.
</details>

---

**16.** <b>Anal</b>ysts <b>acr</b>oss 300 <b>Gl</b>ue <b>tab</b>les <b>sho</b>uld <b>s</b>ee <b>colu</b>mns <b>tag</b>ged `confidential` <b>on</b>ly <b>i</b>f <b>th</b>ey <b>bel</b>ong <b>t</b>o <b>t</b>he <b>fina</b>nce <b>te</b>am, <b>a</b>nd <b>n</b>ew <b>tab</b>les <b>mu</b>st <b>fol</b>low <b>t</b>he <b>ru</b>le <b>automat</b>ically. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>mo</b>st <b>scal</b>able <b>appr</b>oach?

- <b>A</b>. IAM <b>poli</b>cies <b>p</b>er <b>tab</b>le
- <b>B</b>. S3 <b>buc</b>ket <b>poli</b>cies <b>p</b>er <b>pre</b>fix
- <b>C</b>. [<b>La</b>ke <b>Forma</b>tion](00-data-basics-for-beginners.md#aws-lake-formation) LF-<b>ta</b>gs (<b>t</b>ag-<b>bas</b>ed <b>acc</b>ess <b>cont</b>rol)
- <b>D</b>. <b>Reds</b>hift <b>dyna</b>mic <b>da</b>ta <b>mask</b>ing

<details><summary><b>Ans</b>wer</summary>

**C.** <b>La</b>ke <b>Forma</b>tion <b>T</b>ag-<b>Bas</b>ed <b>Acc</b>ess <b>Cont</b>rol (LF-TBAC) <b>gra</b>nts <b>o</b>n <b>t</b>ag <b>expres</b>sions, <b>a</b>nd <b>new</b>ly <b>tag</b>ged <b>tab</b>les <b>a</b>nd <b>colu</b>mns <b>inhe</b>rit <b>t</b>he <b>acc</b>ess <b>rul</b>es.
</details>

---

**17.** <b>A</b> <b>comp</b>any <b>mu</b>st <b>ens</b>ure <b>n</b>o <b>back</b>ups <b>o</b>r <b>repl</b>icas <b>o</b>f <b>i</b>ts <b>da</b>ta <b>a</b>re <b>ev</b>er <b>crea</b>ted <b>outs</b>ide <b>e</b>u-<b>cent</b>ral-1 <b>i</b>n <b>a</b>ny <b>acco</b>unt. <b>Wh</b>at <b>sho</b>uld <b>i</b>t <b>imple</b>ment?

- <b>A</b>. AWS <b>Con</b>fig <b>ru</b>le <b>repor</b>ting <b>n</b>on-<b>compl</b>iant <b>buck</b>ets
- <b>B</b>. <b>Serv</b>ice <b>cont</b>rol <b>pol</b>icy <b>deny</b>ing <b>acti</b>ons <b>whe</b>re `aws:RequestedRegion` <b>i</b>s <b>n</b>ot <b>e</b>u-<b>cent</b>ral-1 (<b>wi</b>th <b>exemp</b>tions <b>f</b>or <b>glo</b>bal <b>serv</b>ices)
- <b>C</b>. <b>Mac</b>ie <b>jo</b>bs <b>i</b>n <b>eve</b>ry <b>Reg</b>ion
- <b>D</b>. S3 <b>Obj</b>ect <b>Lo</b>ck

<details><summary><b>Ans</b>wer</summary>

**B.** <b>A</b> <b>Serv</b>ice <b>Cont</b>rol <b>Pol</b>icy (SCP) **prevents** <b>t</b>he <b>acti</b>ons. <b>Con</b>fig <b>on</b>ly <b>dete</b>cts <b>th</b>em <b>aft</b>er <b>t</b>he <b>fa</b>ct.
</details>

---

**18.** <b>A</b> <b>fina</b>nce <b>te</b>am <b>nee</b>ds <b>li</b>ve, <b>re</b>ad-<b>on</b>ly <b>acc</b>ess <b>t</b>o <b>tab</b>les <b>i</b>n <b>t</b>he <b>sal</b>es <b>tea</b>m's <b>Reds</b>hift <b>Serve</b>rless <b>workg</b>roup <b>i</b>n <b>anot</b>her <b>acco</b>unt, <b>with</b>out <b>copy</b>ing <b>da</b>ta. <b>Wh</b>at <b>sho</b>uld <b>b</b>e <b>us</b>ed?

- <b>A</b>. UNLOAD <b>t</b>o S3 <b>a</b>nd COPY <b>in</b>to <b>t</b>he <b>fina</b>nce <b>wareh</b>ouse <b>nigh</b>tly
- <b>B</b>. <b>Reds</b>hift <b>da</b>ta <b>shar</b>ing (<b>prod</b>ucer <b>autho</b>rizes, <b>cons</b>umer <b>acco</b>unt <b>assoc</b>iates <b>t</b>he <b>datas</b>hare)
- <b>C</b>. DMS <b>replic</b>ation <b>betw</b>een <b>wareh</b>ouses
- <b>D</b>. <b>Reds</b>hift <b>feder</b>ated <b>que</b>ry

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Da</b>ta <b>shar</b>ing <b>giv</b>es <b>li</b>ve, <b>ze</b>ro-<b>co</b>py <b>acc</b>ess <b>acr</b>oss <b>acco</b>unts. <b>Feder</b>ated <b>que</b>ry <b>targ</b>ets [<b>Relat</b>ional <b>Data</b>base <b>Serv</b>ice [RDS]](00-data-basics-for-beginners.md#amazon-rds)/<b>Aur</b>ora, <b>n</b>ot <b>oth</b>er <b>Reds</b>hift <b>wareh</b>ouses.
</details>

---

**19.** <b>Busi</b>ness <b>use</b>rs <b>mu</b>st <b>sea</b>rch <b>f</b>or <b>data</b>sets <b>b</b>y <b>busi</b>ness <b>ter</b>ms, <b>requ</b>est <b>acc</b>ess, <b>a</b>nd <b>g</b>et <b>appr</b>oval <b>fr</b>om <b>da</b>ta <b>own</b>ers, <b>wi</b>th <b>acc</b>ess <b>gran</b>ted <b>automat</b>ically <b>t</b>o <b>the</b>ir <b>te</b>am. <b>Wh</b>at <b>sho</b>uld <b>b</b>e <b>us</b>ed?

- <b>A</b>. AWS <b>Gl</b>ue <b>Da</b>ta <b>Cata</b>log <b>wi</b>th <b>craw</b>lers
- <b>B</b>. [<b>Ama</b>zon <b>SageM</b>aker <b>Cata</b>log](00-data-basics-for-beginners.md#amazon-sagemaker-unified-studio-and-sagemaker-catalog) <b>wi</b>th <b>proj</b>ects <b>a</b>nd <b>subscr</b>iption <b>requ</b>ests
- <b>C</b>. [AWS <b>Da</b>ta <b>Exch</b>ange](00-data-basics-for-beginners.md#aws-data-exchange)
- <b>D</b>. IAM <b>Iden</b>tity <b>Cen</b>ter <b>permi</b>ssion <b>se</b>ts

<details><summary><b>Ans</b>wer</summary>

**B.** <b>SageM</b>aker <b>Cata</b>log <b>prov</b>ides <b>t</b>he <b>busi</b>ness <b>glos</b>sary, <b>sea</b>rch, <b>a</b>nd <b>publ</b>ish/<b>subsc</b>ribe <b>work</b>flow, <b>a</b>nd <b>gra</b>nts <b>acc</b>ess <b>t</b>o <b>t</b>he <b>reque</b>sting <b>proj</b>ect <b>on</b>ce <b>appr</b>oved.
</details>

---

**20.** <b>A</b> <b>pipe</b>line <b>mu</b>st <b>clas</b>sify 20 <b>mill</b>ion <b>arch</b>ived <b>supp</b>ort <b>tick</b>ets <b>b</b>y <b>top</b>ic <b>wi</b>th <b>a</b> <b>Lar</b>ge <b>Lang</b>uage <b>Mod</b>el (LLM). <b>Resu</b>lts <b>a</b>re <b>nee</b>ded <b>wit</b>hin 2 <b>da</b>ys, <b>a</b>nd <b>co</b>st <b>mu</b>st <b>b</b>e <b>minim</b>ized. <b>Wh</b>at <b>i</b>s <b>t</b>he <b>be</b>st <b>appr</b>oach?

- <b>A</b>. <b>Lam</b>bda <b>invo</b>king [<b>Bedr</b>ock](00-data-basics-for-beginners.md#amazon-bedrock) <b>o</b>n-<b>dem</b>and <b>f</b>or <b>ea</b>ch <b>tic</b>ket <b>v</b>ia S3 <b>eve</b>nts
- <b>B</b>. <b>Prep</b>are JSON <b>Lin</b>es (JSONL) <b>inp</b>ut <b>i</b>n S3 <b>a</b>nd <b>r</b>un <b>a</b>n <b>Ama</b>zon <b>Bedr</b>ock <b>bat</b>ch <b>infer</b>ence <b>j</b>ob, <b>th</b>en <b>lo</b>ad <b>t</b>he <b>out</b>put <b>wi</b>th <b>Gl</b>ue
- <b>C</b>. <b>Ho</b>st <b>a</b>n <b>op</b>en-<b>sou</b>rce <b>mod</b>el <b>o</b>n <b>Elas</b>tic <b>Comp</b>ute <b>Clo</b>ud (EC2) <b>Grap</b>hics <b>Proce</b>ssing <b>Un</b>it (GPU) <b>insta</b>nces
- <b>D</b>. <b>U</b>se <b>Ama</b>zon <b>Q</b> <b>i</b>n [<b>Quick</b>Sight](00-data-basics-for-beginners.md#amazon-quicksight)

<details><summary><b>Ans</b>wer</summary>

**B.** <b>Bat</b>ch <b>infer</b>ence <b>i</b>s <b>desi</b>gned <b>f</b>or <b>lar</b>ge <b>asynch</b>ronous <b>workl</b>oads <b>a</b>t <b>low</b>er <b>co</b>st <b>th</b>an <b>o</b>n-<b>dem</b>and <b>cal</b>ls, <b>a</b>nd <b>avo</b>ids <b>throt</b>tling.
</details>
