# Kritická recenze: `03-dobyvani-znalosti-shrnuti.tex`

Rozsah recenze: celý dokument (704 řádků, 8 stran PDF = rozcestník + 7 otázek).
Metoda: (a) tvrzení po tvrzení srovnáno s plným textem `03-dobyvani-znalosti.tex`
(4751 řádků) — jak s výkladem, tak s oddíly „Shrnutí ke~zkoušce“; (b) nezávislý
přepočet všech číselných údajů uvedených v shrnutí (entropie 4 atributů na 12
klientech, naivní Bayes, χ², IQR, 2pq, 2p(1−p), 63,2 %); (c) kontrola oborové
správnosti proti Han–Kamber, Berka, Tan–Steinbach–Kumar, Easley–Kleinberg,
Zafarani–Abbasi–Liu; (d) kontrola doslovnosti nadpisů proti oficiálnímu znění
okruhu (WebFetch stránky MFF, plán 2025/2026, zaměření Strojové učení);
(e) kontrola invariantu „jedna otázka = jedna strana“ a sazby (NEL-safe grep logu,
`pdfinfo`); (f) vizuální kontrola zaplnění stran (`pdftoppm -r 50`) kvůli tomu, aby
každý návrh na doplnění měl na téže straně krytí.

---

## Souhrn

| Kategorie | Počet nálezů |
|---|---|
| KRITICKÉ | 1 |
| DŮLEŽITÉ | 2 |
| DROBNÉ (věcné + didaktické) | 9 (z toho 1 označeno NEJISTÉ, 2 jsou návrhy na doplnění) |
| DROBNÉ (sazba a jazyk) | 2 |
| Overfull boxy | 0 (kontrolováno NEL-safe) |

**Celkový dojem.** Shrnutí je věcně velmi čisté. Přepočítal jsem všechna čísla,
která v něm figurují — entropie příjmu 0,5747, konta 0,6667, pohlaví 0,9183
a nezaměstnanosti 0,825 na tabulce 12 klientů, naivní Bayes 0,1042 vs. 0,0416,
χ² = 42,857 > 3,84, 2pq = 8 z 18, 2p(1−p) = 49 % vs. 14 %, 63,2 % = 1 − 1/e —
a **všechna jsou správně**. Nadpisy sedmi stran jsou **doslovným** zněním sedmi
vět oficiálního okruhu (ověřeno proti stránce MFF), invariant „1 otázka =
1 strana“ platí (PDF má přesně 8 stran) a překlad je bez jediného overfull boxu.
Kondenzace je poctivá: nenašel jsem místo, kde by shrnutí zkratkou obrátilo
smysl u „velkých“ pastí okruhu (t-weight vs. d-weight, bagging vs. boosting,
uzavřenost dolů u MS-Apriori, normalizace u HITS vs. PageRank, nejmenší vlastní
čísla laplaciánu).

**Co je naopak v pořádku a bylo ověřeno.** Fáze KDD (5) i CRISP-DM (6, pořadí
není striktní) včetně 60–80 % času na přípravu dat; čtyři škály atributů
a přípustné operace; IQR a pravidlo 1,5·IQR i konvence počítání kvartilů
(n/4, 3n/4, zaokrouhlení nahoru); rozlišení z-skóre (střední absolutní odchylka,
robustnější) a std-skóre; fuzzy diskretizace (součet charakteristických funkcí 1,
váha = ∏μ_j) i KEX (Assign/Group, χ² proti apriornímu rozdělení); PCA vs. selekce;
filtr vs. wrapper včetně bottom-up/top-down; χ² — stupně volnosti (R−1)(S−1),
podmínka r_k s_l/n ≥ 5, kritická hodnota 3,84, Fisher pro malé četnosti;
zdůvodnění normalizace ID (atributy s mnoha hodnotami, identifikátor);
support/confidence/lift a důsledek lift < 1; Apriori-Gen (spojení v k−2
kategoriích + prořezání), MS-Apriori (minimum MIS, φ, neplatnost uzavřenosti
dolů, semena L místo F₁, tailCount), CAR (jeden krok, rule-items, 101 %),
sekvence (velikost vs. délka, ⟨{3}{8}⟩ vs. ⟨{3,8}⟩), FP-Growth (2 průchody,
prefixy, podmíněné stromy, nejhorší případ); TDIDT/ID3/C4.5 (dolní mez přesnosti
s 1,96, poměrný informační zisk)/C5.0/CART (Gini, Φ = 2P_LP_R Σ|·|)/CHAID;
naivní Bayes; SVM (okraj 2/‖w‖, KKT nutné i postačující, α_i > 0 jen pro SV,
Mercer); logistická regrese; diskriminační analýza (shodné kovarianční matice →
lineární); ELM (β = H⁺T, I/C); bagging (rozptyl, 63,2 %, zkreslení nesníží),
náhodné lesy (ρσ² + (1−ρ)σ²/k, m ≈ √p), AdaBoost (zkreslení, α_t, sekvenčně,
šum); metriky včetně Mahalanobise; k-means/++/medians/medoids/PAM (k(n−k),
O(kn²d))/CLARA/CLARANS; hierarchické shlukování a CURE; LVQ (μ(k−1)/(k+1));
MAFIA a DBSCAN; AOI (O(na)), směr implikací u charakteristických (⇒, nutná
podmínka) a diskriminačních pravidel (⇐, postačující) a srovnání d-weight
s apriorním podílem třídy; matice záměn, F₁ jako harmonický průměr, ROC/AUC
(křížení křivek), lift a ekonomická úvaha; čtyři centrality včetně důvodu, proč
vlastní centralita potřebuje největší vlastní číslo; klastrovací koeficient,
modularita Q ∈ [−1,1] a práh 0,3; LTM vs. ICM; 63 % u maximalizace vlivu; testy
homofilie i korelace a shuffle test; strukturní balance včetně slabé; HITS
(nutná normalizace, ko-citační matice) vs. PageRank (normalizaci nepotřebuje);
Girvanové–Newman O(m²n), Louvain O(n log n) a Leiden; spektrální shlukování
s nejmenšími vlastními čísly vs. maximalizace modularity s největšími; Jaccard,
Adamic–Adar, Katz. Shrnutí **nepřevzalo** žádnou z chyb, které vytkla recenze
plného textu (`review-03-dm.md`) — zejména ne obrácenou interpretaci d-weight
(K2) ani záměnu „aposteriorní“ za „podmíněná“ u P(E_k|H_t) (D5).

---

## KRITICKÉ

### K1. PageRank: „všechny tři podmínky se řeší jedinou úpravou“ (str. 7, oddíl „Autority: HITS a PageRank“, ř. 604–606)

**Kde.** Strana 7 (otázka 6), poslední věta odstavce o PageRanku:

> „Markovský řetězec potřebuje matici *stochastickou, ireducibilní a~aperiodickou*
> --- webový graf nesplňuje ani jednu podmínku a~všechny se řeší *jedinou*
> úpravou (odkaz odkudkoli kamkoli s~malou pravděpodobností)."

**Co je špatně.** Augmentace „odkaz z každé stránky na každou s pravděpodobností
(1−d)/n“ řeší **jen ireducibilitu a aperiodicitu**. Stochasticitu neřeší:
visící stránka (*dangling page*) má v A řádek samých nul, po augmentaci se jeho
součet rovná (1−d), nikoli 1 — matice tedy stochastická stále není. Visící
stránky se musí ošetřit **zvlášť**: buď se během výpočtu odstraní (neovlivňují
pořadí ostatních stránek), nebo se jejich řádek nahradí A_ij = 1/n.

**Rozpor s plným textem.** Výklad v plné verzi (ř. 3927–3945) říká přesně opak
shrnutí: nejprve vyjmenuje řešení pro visící stránky zvlášť a pak uvádí
„**Obě posledně jmenované vlastnosti** se řeší jedinou strategií“. Chyba je
převzatá z oddílu „Shrnutí ke~zkoušce“ plné verze (ř. 4531–4534: „vše se řeší
jedinou strategií“), který je tedy v rozporu s vlastním výkladem o 600 řádků výš
— **stojí za to opravit obojí**.

**Proč je to kritické.** PageRank je nejčastěji zkoušená položka celé otázky 6
a tahle věta je přesně to, na co navazuje doplňující otázka „a co stránky bez
odkazů?“. Student, který zopakuje shrnutí, odpoví špatně.

**Návrh opravy** (délkově neutrální, vejde se beze změny sazby):

```tex
Markovský řetězec potřebuje matici \emph{stochastickou, ireducibilní
a~aperiodickou} --- webový graf nesplňuje ani jednu: visící stránky (nulové
řádky) se odstraní nebo dostanou řádek $1/n$, ireducibilitu a~aperiodicitu
zajistí až tlumicí faktor (odkaz odkudkoli kamkoli).
```

---

## DŮLEŽITÉ

### D1. „Informační dávka“ — neexistující termín (str. 3, „Filtrační kritéria“, ř. 258–259)

**Kde.** Strana 3 (otázka 2):

> „vzájemná informace MI(A,C), **informační dávka** ID(A,C)=MI(A,C)/H(C) (větší = lepší)"

**Co je špatně.** Termín „informační dávka“ v oboru neexistuje a plný text jej
nepoužívá. Plná verze (ř. 794–797, shodně ve slidech NDBI023) má
**informační míra závislosti** (*information measure of dependence*, odtud
zkratka ID). „Dávka“ je zřejmě omyl při rozepisování zkratky.

**Správně.** Informační míra závislosti; vzorec i zdůvodnění normalizace jsou
ve shrnutí správně, chybný je jen název — a právě názvem se ptá zkoušející.

**Návrh opravy** (str. 3 má proti stranám 4 a 7 rezervu, přírůstek ~2 slova):

```tex
\tm{informační míra závislosti} $\mathrm{ID}(A,C)=\mathrm{MI}(A,C)/H(C)$
(\en{information measure of dependence}; větší $=$ lepší).
```

### D2. Generalizovaná relace označena za *vstup* charakterizace (str. 5, „Souvislosti“, ř. 440–441)

**Kde.** Strana 5 (otázka 4), závěrečný odstavec:

> „Charakterizace a~diskriminace jsou *deskriptivní* úlohy (otázka~1);
> **vstupem je generalizovaná relace** po přípravě dat a~diskretizaci (otázka~2)…"

**Co je špatně.** Generalizovaná (primární) relace je **výstupem** AOI, ne jeho
vstupem — plný text ji zavádí až v kroku „prezentace“ algoritmu (ř. 2533–2536)
a míry t-weight/d-weight se z ní teprve počítají (ř. 2564). Vstupem je datová
tabulka po přípravě dat plus koncepční hierarchie a dotaz vymezující cílovou
třídu.

**Správně.** Vstup = připravená a diskretizovaná tabulka + koncepční hierarchie;
výstup = generalizovaná (primární) relace, z níž se čtou obě váhy.

**Návrh opravy** (délkově neutrální):

```tex
Charakterizace a~diskriminace jsou \emph{deskriptivní} úlohy (otázka~1); vstupem
je tabulka po přípravě dat a~diskretizaci (otázka~2) plus koncepční hierarchie,
výstupem generalizovaná relace; zajímavost jako filtr nadprodukce pravidel
navazuje na asociační pravidla (otázka~3) a~na kritéria hodnocení znalostí
(otázka~5).
```

---

## DROBNÉ (věcné a didaktické)

### S1. d-weight: nedefinovaný rozsah indexu $j$ ve jmenovateli (str. 5, ř. 419–420)

Vzorec `d-weight = count(q_a ∈ C_target) / Σ_j count(q_a ∈ C_j)` je Han–Kamberův
a je správný **jen** tehdy, běží-li $j$ přes *všechny* třídy (včetně cílové).
Plný text ovšem zavádí $C_1,\dots,C_m$ výslovně jako **kontrastní** třídy
(ř. 2572–2575) a cílovou třídu přičítá ve jmenovateli zvlášť. Kdo si u tabule
vybaví tuhle definici a použije vzorec ze shrnutí, dostane pro první řádek
příkladu 90/10 = 900 % místo 90 %. **Oprava:** doplnit tři slova —
`$\sum_j \mathrm{count}(q_a\in C_j)$ přes \emph{všechny} třídy`.

### S2. Chybný příklad u „operační“ koncepční hierarchie (str. 5, ř. 411)

Shrnutí uvádí „*operační* (výpočtem, např. intervaly věku)“. Intervaly věku jsou
v plném textu (ř. 2500–2503) i u Han–Kambera příkladem hierarchie
**seskupovací** ({20--29} ≺ mladý); operační je odvozená operací nad hodnotou
(e-mail → doména, URL → server). Takto to působí, že jde o dva názvy téhož.
**Oprava:** `\tm{operační} (výpočtem z~hodnoty --- e-mail $\to$ doména)`.

### S3. Katzova míra: skalár položený rovno matici (str. 7, ř. 634–635)

> „\tm{Katzova míra} $\sum_t \beta^t W^{(t)}_{ij}=(I-\beta A)^{-1}-I$"

Levá strana je číslo (prvek $ij$), pravá matice $n\times n$. Plný text
(ř. 4408–4412) obojí správně odděluje. Navíc chybí podmínka konvergence
(dostatečně malé β; přesněji β < 1/λ_max). **Oprava** s krytím délky —
zkrátit u společných sousedů `(ignoruje stupně)`:

```tex
\emph{Společní sousedé} $|S_i\cap S_j|$, \emph{Jaccard} …
\tm{Katzova míra} $\mathrm{Katz}(i,j)=\sum_t\beta^tW^{(t)}_{ij}$, maticově
$K=(I-\beta A)^{-1}-I$ (malé $\beta$, jinak řada diverguje) --- pro \emph{řídké}
sítě s~málo společnými sousedy.
```

### S4. „(ne slepé podvzorkování)“ jde proti zdroji (str. 3, ř. 241–242)

Plný text (ř. 661–664) uvádí jako řešení nevyvážených tříd explicitně
„převzorkování minority, podvzorkování majority“ vedle vah chyb. Parentetické
„ne slepé podvzorkování“ může studenta svést k tvrzení, že podvzorkování je
chyba. **Oprava:** `(váhy chyb, převzorkování minority či podvzorkování majority)`.

### S5. Prahy AOI jen anglicky (str. 5, ř. 406–407)

`\emph{attribute threshold}` a `\emph{generalized relation threshold}` porušují
konvenci „český termín + anglický ekvivalent kurzívou“ (obojí má v plné verzi
český název, ř. 2551–2553). Strana 5 je nejméně zaplněná ze všech, vejde se
i typická velikost prahů. **Oprava:**
`Prahy: \emph{prah generalizace atributu} $T_i$ (\en{attribute threshold}; typicky 2--8) a~\emph{prah velikosti relace} $T$ (10--30).`

### S6. „primárně min ⟨w·w⟩/2“ (str. 4, ř. 331)

Míněno „**primární úloha** je min ⟨w·w⟩/2“ (tak to má plný text, ř. 2395–2396);
„primárně“ čtenář přečte jako „především“. **Oprava:** `primární úloha
$\min\frac{\langle w\cdot w\rangle}{2}$ za podmínek …`.

### S7. Chybí měkký okraj SVM (str. 4) — s návrhem, co škrtnout

Shrnutí u SVM končí u separabilního případu; proměnné vůle ξ_i a parametr C
(plný text ř. 1819–1822) chybí. Je to nejčastější doplňující otázka
(„a co když data lineárně separabilní nejsou?“). Strana 4 je plná, takže
**nutná protiváha** — obojí na téže straně:

* ř. 362: škrtnout `, LocalSearch++` (exotická položka, u zkoušky nepadne);
* ř. 366–367: `\tm{CLARA} vzorkuje (riziko špatného vzorku)` → `\tm{CLARA} vzorkuje`;

uvolní ~2 řádky, do nichž se vejde:
`Neseparabilní data: proměnné vůle $\xi_i$, $\min\frac{\langle w\cdot w\rangle}{2}+C\sum_i\xi_i$ ($C$ řídí kompromis okraj/chyby).`

### S8. Nevyužité místo na stranách 3 a 5 — chybí právě ty výpočty, které slibuje rozcestník

**Zjištění z vizuální kontroly** (`pdftoppm -r 50`, strany 2–8): strany otázek 3
a 6 jsou zaplněné do posledního řádku (jakékoli doplnění tam vyžaduje škrt, viz
S3 a S7), ale **strana 5 (otázka 4) a strana 3 (otázka 2) mají shodně ~40 %
volného místa** v dolní části obou sloupců. Přitom rozcestník na str. 1 slibuje
v oddílu „Co se chce spočítat u~tabule“ mimo jiné *„t-weight a d-weight
z tabulky generalizovaných záznamů“* a *„kvartily, IQR a mez odlehlosti“* —
a ani jedno z toho na příslušné straně žádné číslo nemá, zatímco strany otázek 2
(χ²) a 3 (entropie, Bayes) propočítané příklady citují. Doplnění bez jakéhokoli
škrtu:

* **str. 5** — miniaturní tabulka z plného textu (ř. 2600–2648): cíl 200 /
  kontrast 800; řádek „30--40, vysoký příjem, Praha“ 90:10 $\Rightarrow$
  $t=90/200=45\,\%$, $d=90/100=90\,\%$; řádek „20--30, nízký, mimo Prahu“ 20:480
  $\Rightarrow$ $t=10\,\%$, $d=4\,\%$ — tedy \emph{pod} apriorními 20~\%, profil
  hypotéku spíše vylučuje. Dvě čísla navíc udělají z abstraktní strany
  použitelnou přípravu k tabuli.
* **str. 5** — formální schéma všech tří pravidel (plný text ř. 2581–2597):
  `target_class(X) ⇒ cond₁[t:w₁] ∨ …`, `target_class(X) ⇐ cond[d:w]`,
  `⇔ [t:w, d:w′]`. Shrnutí směry implikací popisuje slovy, ale zápis, který se
  píše na tabuli, neuvádí.
* **str. 5** — lift u pravidel: mezi objektivními mírami je `lift` jen
  vyjmenován, plný text (ř. 2666) má vzorec
  `\tm{lift} $=\text{d-weight}/P(C_{\mathit{target}})$ --- kolikrát profil zvýší šanci na cílovou třídu.`
* **str. 3** — propočítaný příklad kvartilů (plný text ř. 502–518): $n=30$,
  $Q_1=3{,}2$, $Q_2=3{,}8$, $Q_3=4{,}0$, $\mathrm{IQR}=0{,}8$, meze 2,0 a 5,2,
  odlehlá 5,5.

### S9. NEJISTÉ — interpretace Rockdale County (str. 8, ř. 677–678)

> „*Epidemiologie* (Rockdale County 1996) --- struktura kontaktní sítě vysvětlí
> šíření lépe než počet kontaktů."

Plný text (ř. 4659–4662) u tohoto případu uvádí jen popis tří skupin a počty
diagnóz, žádný takový závěr. Tvrzení je v souladu s tím, jak se případ v SNA
literatuře čte, ale **v podkladech pro tento okruh oporu nemá** — nechávám jako
nejisté; buď doplnit oporu do plného textu, nebo formulovat opatrněji
(„ukázka, že o šíření rozhoduje struktura kontaktní sítě“).

---

## DROBNÉ (sazba a jazyk)

### S10. Chybějící nezlomitelné mezery v mezititulcích `\hh{}`

Řádky 170, 263, 289, 326, 476, 483, 491, 553, 596: „Dělení úloh a metod“,
„$\chi^2$ test a regrese“, „Apriori a varianty“, „Další metody učení s učitelem“,
„Matice záměn a míry“, „ROC a AUC“, „Skórování a lift“, „Koheze a vlastnosti
reálných sítí“, „Autority: HITS a PageRank“. V celém těle dokumentu se `a~`,
`s~`, `v~` důsledně používá, v nadpisech nikoli. Aktuálně se žádný z nich neláme
(sazba je bez overfull boxů), takže jde čistě o konzistenci — ale při jakékoli
budoucí úpravě textu se mezititulek zlomit může. **Oprava:** doplnit `~`.

### S11. „matice sousednosti (u orientovaných grafů nesymetrická)“ (str. 7, ř. 527–528)

Přesněji **nemusí být** symetrická (plný text ř. 3119–3120: „nemusí být
symetrická“); orientovaný graf se vzájemnými hranami symetrickou matici má.
Jednoslovná oprava, nulový nárůst délky.

### S12. Stav sazby — bez nálezu

Kontrolováno NEL-safe postupem
(`LC_ALL=C tr '\205' '\n' < 03-dobyvani-znalosti-shrnuti.log | grep Overfull`):
**0 overfull i underfull boxů**. `pdfinfo` hlásí **8 stran**, tedy přesně
1 + 7 otázek — invariant „jedna otázka = jedna strana“ platí. Desetinné čárky
jsou v matematice psány `{,}` (`42{,}857`, `0{,}85`, `1{,}5`, `63{,}2`), zbylé
výskyty `X,Y` uvnitř `$…$` jsou souřadnice a intervaly (`$[0,1]$`, `$(0,0)$`,
`$Q\in[-1,1]$`, `$\{3,8\}$`) — správně. `\uv{}`, `\path{}`, `str.~N`,
`\raggedcolumns` i jednotné `\footnotesize` na všech stranách odpovídají
konvencím z `CLAUDE.md`.

---

## Pokrytí okruhu — ověřeno proti oficiálnímu znění

Znění okruhu **Dobývání znalostí** (studijní plán 2025/2026, Informatika Mgr.,
Umělá inteligence, zaměření Strojové učení) má sedm vět a všech sedm je
nadpisem právě jedné strany, **doslova** včetně středníků a interpunkce
(„Metody pro extrakci charakteristických diskriminačních pravidel…“ je bez
čárky mezi adjektivy — shrnutí to má správně). Rozcestník na str. 1 uvádí
správná čísla stran 2–8.

Prošel jsem větu po větě, co která explicitně jmenuje:

| Věta okruhu | Jmenuje | Stav ve shrnutí |
|---|---|---|
| 1 | paradigmata | KDD, 5 fází, kořeny, typy úloh, škály, SEMMA/CRISP-DM/ASUM-DM — úplné |
| 2 | příprava dat; výběr atributů; analýza relevance | chybějící hodnoty, outliery, standardizace, diskretizace, redukce, filtry/wrappery, χ²/H/MI/ID, regrese — úplné |
| 3 | asociační pravidla; učení s učitelem; klastrová analýza | všechny tři bloky; jediná mezera = měkký okraj SVM (S7) |
| 4 | charakteristická diskriminační pravidla; měření zajímavosti | AOI, hierarchie, t/d-weight, objektivní i subjektivní míry — úplné (a strana má rezervu, viz S8) |
| 5 | reprezentace; vyhodnocování; vizualizace | všechny tři části včetně tří rovin vyhodnocování — úplné |
| 6 | modely SNA; míry centrality; detekce komunit | modely (vlastnosti reálných sítí, LTM/ICM, homofilie, balance, HITS/PageRank), 4 centrality, detekce komunit ve všech 4 kategoriích + predikce vazeb — úplné |
| 7 | praktické využití obojího | 8 aplikací DM + 7 SNA + provozní/etické aspekty — úplné |

Nenašel jsem téma, které by věta okruhu jmenovala a shrnutí je vynechalo.
U nejobjemnějších stran (3 a 6) jsem srovnával položku po položce s oddíly
„Shrnutí ke~zkoušce“ plné verze (ř. 2341–2455 a 4457–4575): shrnutí je jejich
věrným kondenzátem, vypouští jen čísla složitosti CLARA, `$O(n^5)$`/Karger
u minimálního řezu, `$t=200$` u HITS a detaily bipartitních jader — nic z toho
není nosné.

---

## Poznámka mimo rozsah (týká se plného textu, ne shrnutí)

Při ověřování jsem narazil na tři místa, která `review-03-dm.md` označuje
v tabulce „FÁZE 2“ za **opravená**, ale v aktuálním `03-dobyvani-znalosti.tex`
opravena nejsou:

* **D5** (ř. 1704): stále „nulová **aposteriorní** pravděpodobnost $P(E_k\mid H_t)$“
  — má být podmíněná pravděpodobnost / věrohodnost.
* **D3** (ř. 771–779): Fisherův test má stále značení $P_0$, $P_1$ a sumu
  $\sum_{i=0}^{m}$ přes *všechny* tabulky (ta by dala P = 1), zatímco příklad
  správně sčítá jen tabulky alespoň tak extrémní jako pozorovaná.
* **N3** (ř. 2146): vzorec $k$-means++ má stále pevné $c$ ve jmenovateli
  i čitateli, ne $D(x)=\min_{c\in C}d(x,c)$.

Shrnutí ani jednu z těchto chyb nepřevzalo — všechna tři místa jsou v něm
formulována správně, resp. vynechána.


---

## Zapracováno (12. 8. 2026)

Opraveno ve `03-dobyvani-znalosti-shrnuti.tex`, PDF přeloženo znovu (8 stran, 0 overfull):

| nález | jak |
|---|---|
| K1 | PageRank: stochasticitu kazí visící stránky a řeší se zvlášť (odstranit, nebo řádek $1/n$); tlumicí faktor spraví jen ireducibilitu a aperiodicitu — podle plného textu ř. 3943 |
| D1 | „informační dávka“ → **informační míra závislosti** (termín z plného textu ř. 784) |
| D2 | AOI: generalizovaná relace je **výstup**, vstupem je tabulka po přípravě dat + koncepční hierarchie |
| S1 | u d-weight doplněno, že jmenovatel je součet přes **všechny** třídy včetně cílové |
| S2 | operační hierarchie: „e-mail → doména“ místo intervalů věku (ř. 2502) |
| S3 | Katz: rozděleno na prvek $K_{ij}$ a maticové $K=(I-\beta A)^{-1}-I$ s podmínkou malého $\beta$ |
| S4 | „(ne slepé podvzorkování)“ → „převzorkování minority, resp. podvzorkování majority“ |
| S6 | „primárně“ → „primární úloha“ |
| S7 | doplněn měkký okraj SVM ($\xi_i$, penalizace $C\sum_i\xi_i$) — bez potřeby škrtu, strana měla rezervu |
| S11 | matice sousednosti „nemusí být symetrická“ |
| S10 | nezlomitelné mezery v 11 `\hh{}` nadpisech |

**Nezapracováno**: S5, S8 (dopsání konkrétních propočtů t/d-weight a kvartilů — čísla
nejsou v plném textu doložená v použitelné podobě, nechci je do opakovací pomůcky
vymýšlet), S9 (Rockdale County — zmírněno by vyžadovalo externí zdroj).

Pozn.: nálezy „mimo rozsah“ (tři body, které `review-03-dm.md` vede jako opravené,
ale v `03-dobyvani-znalosti.tex` opravené nejsou — D5 aposteriorní pravděpodobnost,
D3 Fisherův test, N3 k-means++) se týkají **plného textu** a zůstávají otevřené.
