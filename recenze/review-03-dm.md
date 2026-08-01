# Kritická recenze: `03-dobyvani-znalosti.tex`

Rozsah recenze: celý dokument (5107 řádků, 153 stran), obě části.
Metoda: (a) přepočet **všech** číselných příkladů nezávisle, (b) srovnání s primárními
zdroji (slidy NDBI023 Mrázová 2024, slidy SNA 2024, `SNA_notes.md`, `IKM_sylabus.md`),
(c) kontrola pokrytí obou osnov frázi po frázi, (d) kontrola konzistence napříč částmi,
(e) NEL-safe kontrola sazby.

---

## Souhrn

| Kategorie | Počet nálezů |
|---|---|
| KRITICKÉ | 4 |
| DŮLEŽITÉ | 9 |
| DROBNÉ (věcné + didaktické) | 7 |
| DROBNÉ (sazba) | 22 overfull boxů (1 vbox + 21 hboxů) |

**Celkový dojem.** Dokument je velmi silný. Přepočítal jsem 23 číselných příkladů
(χ², Fisher, Apriori průchod + generování pravidel, lift, frekvenční tabulka, entropie
/ information gain / gain ratio na 12 klientech, MAP, naivní Bayes, Laplace, k-means
3 iterace + SSE, silueta, single/complete linkage, ROC body + AUC dvěma způsoby, lift
analýza + ekonomika, centrality na 6 uzlech + kontrola součtu mezilehlostí hran,
shlukovací koeficient 0,31, homofilie 2pq, test korelace 2p(1−p), HITS 2 iterace +
normalizace, PageRank 3 iterace + přesné řešení, modularita Girvan–Newman,
Adamic–Adar, base-rate fallacy, kvartily + IQR + želvy) — **21 z nich je zcela
správně**. Chyby jsou v **interpretačních větách** kolem správných čísel, ne
v číslech samotných. To je dobrá zpráva, ale právě takové věty student u zkoušky
zopakuje jako fakt.

Pokrytí osnov je **úplné**: všech 10 frází oficiálního okruhu i všech 6 témat sylabu
IKM (včetně jmenovitých položek typu „bayesian poisoning“, „Fisherfaces“,
„michiganský/pittsburgský přístup“, „typy náhodných lesů“, „aktivní učení náhodných
lesů“) má netriviální pokrytí. Nenašel jsem žádné téma osnovy bez zpracování.

---

## KRITICKÉ

### K1. Chybná interpretace výsledku PageRanku (ř. 3436)
> „nejvyšší PageRank má $C$, **přestože má stejný počet vstupních hran jako $A$**“

V grafu $A\to B$, $A\to C$, $B\to C$, $C\to A$ má $C$ vstupní stupeň **2** (od $A$ i od
$B$), zatímco $A$ má vstupní stupeň **1** (jen od $C$). Tvrzení je faktograficky
nepravdivé a navíc ničí pointu příkladu. Pointa je opačná: $A$ má jedinou vstupní
hranu, a přesto se svým skóre 0,3878 téměř dorovnává $C$ (0,3974), protože dostává
**celý** PageRank uzlu $C$, který je nejsilnější.

**Oprava:** přeformulovat na „$A$ má jedinou vstupní hranu, a přesto se skóre 0,3878
téměř vyrovná $C$ se dvěma vstupními hranami — protože $C$ svůj PageRank nedělí
a předává jej celý $A$.“

### K2. Chybná interpretace d-weight (ř. 2664)
> „druhý a třetí řádek mají t-weight i d-weight shodně 25 %, resp. 20 % — jsou typické,
> ale jejich rozlišovací síla je **nulová až mírně záporná**.“

Apriorní podíl cílové třídy je $200/1000 = 20\,\%$. Řádek 2 má $d$-weight $25\,\% >
20\,\%$ → rozlišovací síla je **mírně kladná**. Řádek 3 má $d$-weight $20\,\% =
20\,\%$ → **přesně nulová**. Formulace „nulová až mírně záporná“ je obrácená a mate
právě v místě, kde text vysvětluje rozdíl mezi $t$- a $d$-weight (jádro okruhu
„měření zajímavosti“).

**Oprava:** „mírně kladná (25 % vs. 20 %), resp. přesně nulová (20 % = apriorní podíl)“.

### K3. Chybný vzorec Minkowského metriky (ř. 2201)
$$L^{(z)}(\vec x_1,\vec x_2)=\sqrt[z]{\sum_j (x_{1j}-x_{2j})^z}$$
Chybí **absolutní hodnoty**. Bez nich vzorec pro $z=1$ nedává Manhattanskou vzdálenost
(dá algebraický součet rozdílů, tedy i záporná čísla), pro liché $z$ může být výraz pod
odmocninou záporný a tvrzení $d_H=L^{(1)}$, $d_C=\lim_{z\to\infty}L^{(z)}$ o řádek níž
neplatí. Slidy (`dm_dataanalysis.txt`, snímek 59) mají absolutní hodnoty — v OCR textu
se svislítka ztratila a chyba se propsala do dokumentu; svědčí o tom i to, že
u $d_H$ a $d_C$ na týchž řádcích slidu jsou bary rovněž pryč.

**Navíc interní rozpor:** táž metrika je v kap. 14 (ř. 4338) napsána **správně** jako
$\big(\sum_j|x_j-z_j|^q\big)^{1/q}$.

**Oprava:** doplnit $|\cdot|$ v ř. 2201.

### K4. Overfull \vbox 100,84 pt — obsah přetéká stránku 38
`Overfull \vbox (100.8418pt too high) has occurred while \output is active`
nastává při odstránkování strany 38, na níž je defbox
*„Příklad — indukce stromu, žádost o~úvěr“* (ř. 1244–1316). Jde o jediný nedělitelný
`tcolorbox` obsahující tabulku 12 klientů + 7 zobrazených rovnic + výpis stromu; je
vyšší než sazební zrcadlo, takže jej nelze umístit na žádnou stránku.

**Oprava** (bez zásahu do preambule, jak požaduje zadání): rozdělit defbox na dva
navazující boxy — (1/2) data + entropie kořene + všechny čtyři atributy + zisky,
(2/2) druhé a třetí větvení + výsledný strom.

---

## DŮLEŽITÉ

### D1. Nekonzistentní značení kořenové a bázové množiny u HITS (ř. 3276–3277)
Text zavede $W$ = kořenová množina, $S$ = bázová množina, ale vzorec zní
$T=S\cup\{d\mid s\to d\vee d\to s;\ s\in S\}$ — používá tedy $S$ v roli kořenové
množiny a zavádí nedefinované $T$. Správně má být
$S=W\cup\{d\mid s\to d\vee d\to s;\ s\in W\}$.

### D2. Mezilehlostní centralita: vzorec počítá uspořádané dvojice, příklad neuspořádané
Vzorec (ř. 2881) $C_B(v)=\sum_{s\neq v\neq t}\frac{\sigma_{st}(v)}{\sigma_{st}}$ při
doslovném čtení sčítá přes **uspořádané** dvojice, což by pro vrchol $C$ v příkladu
(ř. 2920) dalo 12, nikoli uváděných 6. Číslo 6 je správné pro neuspořádané dvojice.
Chybí explicitní úmluva. **Oprava:** doplnit větu, že u neorientovaných grafů se sčítá
přes neuspořádané dvojice (ekvivalentně se dělí dvěma), a zmínit normalizaci
$2/((n-1)(n-2))$.

### D3. Fisherův exaktní test — kolize indexů a nekonzistentní popis (ř. 600–604)
Vzorec sčítá $\sum_{i=0}^{a_{11}}$ s předpokladem $a_{11}=\min_{k,l}a_{kl}$, tedy pro
tabulku $D_A(5,13)$, $D_B(1,11)$ je $a_{11}=1$ a sčítanci jsou $i=0$ (pozorovaná
tabulka) a $i=1$ (extrém). Navazující výčet ale označuje $P_0=0{,}031$, což je
**extrémní** tabulka ($i=1$), a $P_1=0{,}173$, což je tabulka **pozorovaná** ($i=0$).
Čísla jsem přepočítal hypergeometricky a **všechna jsou správná**
($0{,}0313;\ 0{,}1732;\ 0{,}3401;\ 0{,}3023;\ 0{,}1276;\ 0{,}0240;\ 0{,}0016$, součet 1),
i výsledek $P=0{,}204>0{,}05$ — jde čistě o značení, které při čtení vypadá jako chyba.
**Oprava:** přeznačit na $P(0),\dots,P(6)$ = pravděpodobnost, že sledovaná buňka nabude
hodnoty $j$, a explicitně říct, že pozorovaná hodnota je 1, takže se sčítá $P(1)+P(0)$.

### D4. Chybná formalizace disjunktnosti shluků v $k$-means (ř. 2235)
$\bigcap_{k'=1}^{K}U_{k'}=\emptyset$ je triviálně splněno pro libovolné $K\ge2$ různých
množin a nevyjadřuje to, co má — správně je **párová** disjunktnost
$U_k\cap U_l=\emptyset$ pro $k\neq l$, plus pokrytí $\bigcup_k U_k = D$.

### D5. Terminologická chyba: $P(E_k\mid H_t)$ není aposteriorní pravděpodobnost (ř. 1508)
> „nulová **aposteriorní** pravděpodobnost $P(E_k\mid H_t)$“

$P(E_k\mid H_t)$ je **podmíněná pravděpodobnost atributu při dané třídě**, tedy
věrohodnost (*likelihood*) — jak text sám správně uvádí o 40 řádků výš (ř. 1470).
Aposteriorní je $P(H\mid E)$. U zkoušky je záměna těchto dvou pojmů okamžitě
penalizovaná.

### D6. Algoritmus HITS a jeho příklad nejsou totéž (ř. 3288–3289 vs. 3329–3336)
Algoritmus iteruje $\mathbf a_k\gets L^TL\,\mathbf a_{k-1}$, příklad iteruje
$\mathbf a\gets L^T\mathbf h$, $\mathbf h\gets L\mathbf a$. Obě varianty jsou korektní
a mají stejnou limitu, ale z počátečního vektoru $(1,1,1,1)$ dávají po prvním kroku
různé hodnoty ($(0,0,4,5)$ vs. $(0,0,2,3)$), takže čtenář, který příklad počítá podle
algoritmu, dostane jiná čísla. Ověřil jsem i limitu: přesný poměr je
$a_C:a_D = 0{,}4385:0{,}5615$ (kořen $2r^2+r-2=0$), uváděné $0{,}435:0{,}565$ je
korektní hodnota **po dvou iteracích**, což ale není v textu řečeno.
**Oprava:** doplnit poznámku o ekvivalenci obou zápisů a o tom, že jde o stav po
2 iteracích.

### D7. Chybí propočítaný příklad na Gini index
Gini je definován (ř. 629–631) a figuruje ve srovnávací tabulce stromů jako kritérium
CART, ale nikde není spočítán — přitom entropie a information gain propočítané jsou.
U zkoušky je „spočtěte Gini“ typická otázka. **Doplnit** výpočet na téže tabulce
12 klientů (aby šlo porovnat s entropií).

### D8. Chybí propočítaný příklad na GUHA kvantifikátory
Sekce 16.3 zavádí čtyřpolní tabulku $(a,b,c,d)$ a šest kvantifikátorů, ale ani jeden
není vyčíslen. Přitom právě tady je nejsnazší ukázat rozdíl mezi deskriptivní
a statistickou rodinou (fundovaná implikace vs. dolní kritická implikace na týchž
datech). **Doplnit** konkrétní tabulku a spočítat všechny kvantifikátory.

### D9. Chybí propočítaný příklad na WAcc a TCR
Vzorce jsou uvedeny (ř. 4173) bez čísel, ačkoli sylabus IKM tuto míru explicitně
zmiňuje a scénáře $\lambda\in\{1,9,999\}$ jsou standardní zkouškovou otázkou.
**Doplnit** výpočet na malé matici záměn pro všechny tři hodnoty $\lambda$, aby bylo
vidět, že filtr s nenulovou FP při $\lambda=999$ TCR pod 1.

---

## DROBNÉ (věcné a didaktické)

- **N1 (ř. 3378):** překlep „surfař **klika** na odkazy“ → „kliká“.
- **N2 (ř. 1421):** kritérium *twoing* je uvedeno v Dunhamově zjednodušené podobě
  $2P_LP_R\sum_j|\cdot|$ (přesně jak na slidu 50), zatímco Breimanova původní definice
  má výraz umocněný na druhou a dělený čtyřmi. Slidům to odpovídá, ale stojí za
  půlvětnou poznámku, aby student nebyl zaskočen literaturou.
- **N3 (ř. 2298):** vzorec pro $k$-means++ píše $d^2(\vec x,\vec c_l)/\sum_q
  d^2(\vec x_q,\vec c_l)$ s pevným $\vec c_l$; správně jde o vzdálenost k **nejbližšímu**
  dosud zvolenému centroidu (text to slovy říká, vzorec ne).
- **N4 (ř. 3719):** parentetická poznámka „(Vlastní čísla $A^k$ jsou $k$-té mocniny
  vlastních čísel $A$.)“ visí bez souvislosti — patří k podmínce konvergence
  $\beta<1/\lambda_{\max}$, která ale není uvedena.
- **N5:** Katzova míra nemá číselný příklad, ačkoli Adamic–Adar ano.
- **N6 (ř. 1904):** „boosting překonává náhodné lesy (ty prohledávají jen malou
  podmnožinu **dat**)“ — v prvním řádku téže tabulky je řeč o podmnožině **atributů**.
  Ověřeno: je to doslovný překlad slidu 65 (`search only a small subset of the data`),
  takže věrné přednášce; nechávám, ale hodí se poznámka.
- **N7:** ověřeno jako **správné** a shodné se slidy (žádný zásah): shlukovací koeficient
  0,31 (1 + 0,67 + 0,33 + 0,17 = 2,17; /7), Jaccard 4/9 a Adamic–Adar $3/\log 2$,
  63 % u maximalizace vlivu, hustota 5/6 a 5/12, reciprocita 2/5, Erdősovo číslo
  4,65/13, 80 % vs. 5–15 % u bezškálových sítí, twoing, C4.5 pesimistický odhad.

---

## DROBNÉ — sazba (22 overfull boxů)

Kontrolováno NEL-safe:
`LC_ALL=C tr '\205' '\n' < 03-dobyvani-znalosti.log | LC_ALL=C /usr/bin/grep -E 'Overfull'`

| pt | místo (ř. tex) | příčina | oprava |
|---|---|---|---|
| **100,84 (vbox)** | str. 38 / defbox 1244–1316 | nedělitelný box vyšší než stránka | rozdělit na dva boxy |
| 12,14 | 2443–2444 | dlouhý výčet rozšíření DBSCAN | přeformulovat |
| 11,05 | 2042 | trojitá display rovnice precision/recall/accuracy | zalomit |
| 10,94 | 4710–4711 | shrnutí s mezí VC dimenze | zkrátit |
| 7,76 | 2499–2517 | tabulka srovnání shlukování (`llllll`) | úzké sloupce |
| 7,59 / 3,92 / 2,62 | 1917 | tabulka srovnání klasifikátorů | zkrátit buňky |
| 5,02 | 979–980 | položka MS-Apriori s inline matematikou | přeformulovat |
| 4,78 | 4287–4288 | shrnutí (cenově citlivá klasifikace) | zkrátit |
| 4,69 | 3960 | display se třemi prahy spamu | zalomit |
| 3,45 | 1736 | maticová rovnice ELM | zmenšit / zalomit |
| 2,99 | 2449–2450 | odstavec o modelových metodách | přeformulovat |
| 1,94 | 502–503 | „Johnson--Lindenstrauss“ nelze dělit | dělicí body |
| 1,86 | 3667–3680 | tabulka taxonomie detekce komunit | úzké sloupce |
| 1,10 | 2722 | tabulka forem reprezentace | zkrátit |
| 6× 0,619 | 40–57, 63–75, 877–887, 934–943, 1194–1204, 1898–1908 | `p{7.6cm}p{8.6cm}` resp. `p{9.2cm}p{7.0cm}`: 16,2 cm + 2\tabcolsep = 473 pt > textwidth 472 pt | zúžit o 0,2 cm |

Poznámka: `\cmidrule`/`\cline` se v tomto dokumentu nepoužívají (ověřeno), takže
známý problém se zacyklením s czech babel nehrozí; opravy jsou navrženy tak, aby
je nezaváděly.

---

## Co je naopak výborné (aby recenze nebyla jednostranná)

- Průběžné číslování kapitol napříč `\part` funguje, křížové odkazy z části II do
  části I (`sec:supervised`, `sec:eval`, `sec:ensemble`, `sec:aoi`, `sec:sna`,
  `sec:priprava`, `sec:vyber`, `sec:clustering`) jsou věcné a nezavádějí duplicity —
  část II opravdu jen odkazuje a přidává aplikační pohled.
- Notace je napříč dokumentem konzistentní (jediná výjimka: Minkowski, viz K3).
- Důkaz věty o balanci je korektní a úplný, včetně všech tří případů.
- Odvození prahu $c_{FP}/(c_{FP}+c_{FN})$ je správné (ověřeno derivací z očekávané ceny).
- Mez $\min\{R^2/\gamma^2,m\}+1$, nulový model $1-(1-p)^k$, test homofilie $2pq$,
  base-rate fallacy $\approx0{,}0099$ — vše ověřeno a správně.

---

# FÁZE 2 — stav zapracování

Vše zapracováno do `03-dobyvani-znalosti.tex`. Preambule beze změny; styl (defboxy,
„Shrnutí k~zkoušce", česky s anglickými termíny kurzívou, průběžné číslování napříč
`\part`) zachován.

| ID | Stav | Poznámka |
|---|---|---|
| K1 PageRank | opraveno | přepsaná interpretace: rozhoduje prestiž zdrojů a jejich výstupní stupeň |
| K2 d-weight | opraveno | „mírně kladná / přesně nulová“ |
| K3 Minkowski | opraveno | doplněny $\|\cdot\|$ + věta, proč jsou nutné |
| K4 vbox 100,8 pt | opraveno | defbox rozdělen na (1/2) a (2/2) |
| D1 HITS root/base | opraveno | $S=W\cup\{\dots\}$ + poznámka o omezení počtu vstupních odkazů |
| D2 betweenness | opraveno | úmluva o neuspořádaných dvojicích + normalizace |
| D3 Fisher | opraveno | přeznačeno na $P(j)$, doplněn hypergeometrický zápis |
| D4 $k$-means | opraveno | párová disjunktnost + pokrytí |
| D5 „aposteriorní“ | opraveno | podmíněná / věrohodnost |
| D6 HITS iterace | opraveno | poznámka o půlkroku + přesná limita $0{,}4385:0{,}5615$ |
| D7 Gini příklad | doplněno | nový defbox vč. binárních dělení CART |
| D8 GUHA příklad | doplněno | nový defbox, 7 kvantifikátorů vyčísleno |
| D9 WAcc/TCR | doplněno | nový defbox, 3 scénáře $\lambda$ |
| N1 překlep | opraveno | „kliká“ |
| N2 twoing | doplněno | poznámka o Breimanově původním tvaru |
| N3 $k$-means++ | opraveno | $D(\vec x)=\min_{\vec c\in C}d(\vec x,\vec c)$ |
| N4 Katz | opraveno | podmínka $\beta<1/\lambda_{\max}$ dána do souvislosti |
| N5 Katz příklad | doplněno | Alice/Bob/Jim, $\beta=0{,}1$ |
| N6 boosting vs. RF | ponecháno | doslovně dle slidu 65 |
| sazba | opraveno | 22 → **0** overfull boxů |

**Kompilace:** 2× `pdflatex -interaction=nonstopmode`, bez chyb, bez nedefinovaných
referencí. **156 stran** (původně 153). Kontrola NEL-safe postupem: **0 overfull boxů**
(dříve 22, z toho 1 vbox 100,84 pt).
