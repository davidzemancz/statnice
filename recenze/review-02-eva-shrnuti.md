# Kritická recenze: 02-prirodou-inspirovane-pocitani-shrnuti.tex

Rozsah: 563 řádků TeXu, 7 stran PDF (1 rozcestník + 6 otázek — invariant splněn,
`Output written … (7 pages)`). Recenzent prošel celé shrnutí větu po větě a každé
tvrzení i vzorec ověřil (a) proti plnému textu `02-prirodou-inspirovane-pocitani.tex`
(3757 řádků), (b) proti standardní literatuře (Eiben & Smith, Goldberg, Koza,
Poli–Langdon–McPhee, Hansen k CMA-ES, Storn & Price k DE, Deb k NSGA-II/III,
Wilson k ZCS/XCS, Stanley k NEAT/HyperNEAT, Axelrod k IPD) a (c) proti nálezům
starší recenze plného textu `review-02-eva.md`. Doslovné znění okruhu ověřeno
WebFetchem přímo na stránce MFF (zaměření *Inteligentní agenti*).

## Souhrn

| kategorie | počet nálezů |
|---|---|
| KRITICKÉ (fakticky špatně) | 1 |
| DŮLEŽITÉ (rozpor s plným textem / zavádějící zkratka / pokrytí okruhu) | 5 |
| DROBNÉ (nepřesnost, styl, sazba, terminologie) | 14 |

**Co je naopak v pořádku a bylo ověřeno:** Pokrytí okruhu je úplné — všech šest
vět oficiálního znění má svou stranu a **každá položka, kterou věta okruhu
výslovně jmenuje, na příslušné straně je** (GA / GP / EP; teorie schémat
i pravděpodobnostní modely; ES / DE / koevoluce / otevřená evoluce; rojové
algoritmy; memetické algoritmy / hill climbing / simulované žíhání; LCS /
neuroevoluce / kombinatorické úlohy / vícekriteriální optimalizace). Znění vět
v rozcestníku na str. 1 je doslovné a čísla stran sedí.

Všechny vzorce jsou přepsány správně: věta o schématech včetně znamének,
$d(S)/(m-1)$ i $(1-p_M)^{o(S)}\approx 1-p_M o(S)$; kombinatorika schémat
($3^m$ / $2^m$); implicitní paralelismus $n^3$; Voseho $s=\mathbf F p/\sum_j
\mathbf F_{jj}p_j$, kvadratický $\mathcal M$ i klíčová symetrie
$r(i,j,k)=r(i\oplus k,j\oplus k,0)$ (nález D2 staré recenze je zapracován);
počet stavů Markovova řetězce $\binom{n+2^l-1}{2^l-1}$; Schwefelova samoadaptace
včetně **pořadí $\sigma$ → $x$** a počtů strategických parametrů $1/n/n(n+1)/2$;
pravidlo 1/5 správným směrem a správně označené jako *adaptivní*;
DE/rand/1/bin (dárce, $I_\mathrm{rand}$, souboj s vlastním rodičem, $F\in[0,2]$,
$C\in[0,1]$, $N\approx10D$); vězňovo dilema ($T>R>P>S$, $2R>T+S$, $DD$ jako
jediné Pareto-neoptimální pole — ověřeno rozborem všech čtyř polí); PSO včetně
$w$ 0,9→0,4, $c_1=c_2=2$ a $\chi\approx0{,}729$; ACO $\tau^\alpha\eta^\beta$
a $\tau\gets(1-\rho)\tau+\sum_k Q/L_k$; Metropolis a Boltzmannovo rozdělení;
XCS $\kappa=\alpha(\epsilon/\epsilon_0)^{-\nu}$ (opravená konstanta $\alpha$
podle nálezu N5 staré recenze); crowding distance NSGA-II; hypervolume jako
jediná striktně dominance-monotónní metrika.

**Zvlášť: obě KRITICKÉ chyby staré recenze plného textu shrnutí nezdědilo.**
SAT v reálné reprezentaci je uveden **správně** (hodnoty jsou penalty ⇒
disjunkce = součin, konjunkce = součet, i s odůvodněním) a Hillisovy řadicí sítě
jsou zmíněny bez napadnutelného tvrzení „lepší než člověk“.

**Srovnávací tabulka na str. 1** (reprezentace / variace / selekce u 12
algoritmů) je věcně správná a shodná s tabulkou v plném textu; jediná drobnost
je řádek NSGA-II, kde „libovolná“ reprezentace nesedí k SBX + polynomiální
mutaci (obojí jsou reálné operátory) — ale tak je to i v plném textu a jako
zkratka je to obhajitelné.

**Sazba:** log neobsahuje ani jeden **Overfull** box, žádné varování, žádné
nerozřešené reference. Desetinné čárky jsou všude `0{,}` a nezlomitelné mezery
v běžném textu jsou důsledné — jediné výjimky jsou uvnitř `\hh{}` nadpisů
(viz S11).

---

## KRITICKÉ

### K1. Efekt Červené královny je popsán obráceně

**Kde:** str. 4 (Otázka 3), oddíl „Koevoluce“, výčet patologií (ř. 339–340).

**Co je špatně:**

> „efekt *Červené královny* (**relativní zlepšení bez absolutního**)“

Plný text (`sec:koevoluce`, ř. 2058–2061) tvrdí pravý opak:

> „**Efekt Červené královny** (*Red Queen effect*): **všichni se zlepšují, ale
> relativní fitness zůstává konstantní** — z naměřených hodnot nepoznáme, zda je
> pokrok skutečný.“

**Správně:** Metafora z Carrollovy Alenky („musíš běžet ze všech sil, abys
zůstala na místě“) znamená *absolutní* zlepšení bez *relativního* zisku:
populace se objektivně zlepšují, ale protože se zlepšují všechny současně,
naměřená (kontextová) fitness se nehne. Formulace ve shrnutí navíc dělá
z Červené královny nerozlišitelný duplikát „cyklení“ a „průměrných stabilních
stavů“ — student by u zkoušky nedokázal ty tři patologie odlišit.

**Návrh opravy** (délkově neutrální, jen se prohodí dvě slova):

```tex
efekt \emph{Červené královny} (všichni se zlepšují, relativní fitness stojí),
```

---

## DŮLEŽITÉ

### D1. Nadpis 6. otázky není doslovné znění věty okruhu

**Kde:** str. 7, `\qpage{6}{…}` (ř. 486–487).

**Co je špatně:** Nadpis zní

> „Aplikace evolučních algoritmů: **expertní systémy**, neuroevoluce,
> **kombinatorické úlohy**, vícekriteriální optimalizace“

Oficiální znění (ověřeno WebFetchem) je

> „Aplikace evolučních algoritmů (**evoluce expertních systémů**, neuroevoluce,
> **řešení kombinatorických úloh**, vícekriteriální optimalizace).“

Zajímavé je, že v rozcestníku na str. 1 (ř. 77–78) je věta uvedena **doslovně
a správně** — rozchází se tedy jen nadpis strany. Ostatních pět nadpisů je
doslovných.

**Správně:** Invariant dokumentu (i `CLAUDE.md`) říká, že nadpis strany = doslovné
znění věty okruhu. Vypadlo slovo „evoluce“ (což mění smysl: neevolvují se
expertní systémy jako aplikace EA obecně, ale *evoluce* expertních systémů je ta
zkoušená položka) a slovo „řešení“; závorka byla nahrazena dvojtečkou.

**Návrh opravy:**

```tex
\qpage{6}{Aplikace evolučních algoritmů (evoluce expertních systémů, neuroevoluce,
řešení kombinatorických úloh, vícekriteriální optimalizace)}
```

Nadpis je už dnes dvouřádkový; +14 znaků se do druhého řádku vejde. Kdyby se
přece jen přelil, zkrátit na téže straně poslední větu oddílu „Kombinatorické
úlohy“ („Obecné pravidlo: rozhoduje kódování a operátory…“), která doslova
duplikuje oddíl „Souvislosti“ na str. 6.

### D2. HyperNEAT — „substrát“ je zaměněn za CPPN

**Kde:** str. 7, oddíl „Neuroevoluce“ (ř. 518–520).

**Co je špatně:**

> „**HyperNEAT**: **substrát** $S:\mathbb{R}^4\to\mathbb{R}$ generuje váhy ze
> souřadnic neuronů, **je reprezentován CPPN** (DAG s různými aktivačními
> funkcemi) evolvovaným pomocí NEAT“

**Správně:** *Substrát* je v HyperNEAT **geometrické rozmístění neuronů**
(mřížka/rovina se souřadnicemi), nikoli funkce. Funkce $\mathbb{R}^4\to\mathbb{R}$,
která ze souřadnic dvou neuronů vrátí váhu jejich spoje, **je** CPPN — není
„reprezentována“ CPPN, je to ona sama (Stanley, D'Ambrosio & Gauci 2009).
Věta ve shrnutí říká, že substrát je funkce a že tato funkce je reprezentována
CPPN, tedy dvakrát mimo. Chyba je zděděná z „Shrnutí ke zkoušce“ plného textu
(ř. 3573–3575) — stará recenze ji nezachytila, opravit je proto potřeba na
obou místech.

**Návrh opravy** (délkově prakticky neutrální):

```tex
\tm{HyperNEAT}: neurony leží na \tm{substrátu} (mřížka se souřadnicemi); váhu
spoje generuje \tm{CPPN} --- funkce $\mathbb{R}^4\to\mathbb{R}$ ze souřadnic obou
neuronů, reprezentovaná DAG s~různými aktivačními funkcemi a~evolvovaná NEATem
--- proto umí zachytit symetrie a~regularity.
```

### D3. Kritika teorie schémat: „předpokládá nekonečnou populaci“ je nepřesné

**Kde:** str. 3 (Otázka 2), oddíl „Kritika teorie schémat“ (ř. 256–257).

**Co je špatně:**

> „**předpokládá nekonečnou populaci**, kdežto konečné trpí driftem“

Plný text (ř. 1403–1404) formuluje tutéž slabinu jinak a přesněji:

> „Populace jsou **konečné a malé** ⇒ výběrové chyby; **exponenciální růst je jen
> střední hodnota**.“

**Správně:** Věta o schématech je nerovnost pro **střední hodnotu** $\mathbb{E}[C(S,t{+}1)]$
a jako taková platí i pro konečnou populaci — žádný předpoklad nekonečné populace
v jejím odvození není (Goldbergovo odvození naopak pracuje s konkrétním $n$
a $\bar f$ konečné populace). Nekonečnou populaci předpokládá až *Voseho*
model o dva odstavce dál — tvrzení ve shrnutí tak navíc smazává rozdíl mezi
oběma teoriemi, který je pointou celé strany. Slabina je v tom, že realizace se
od střední hodnoty v malé populaci liší (výběrová chyba, genetický drift).

**Návrh opravy:**

```tex
platí jen pro \emph{střední hodnotu} --- v~malé populaci ji rozbíjí výběrová chyba
a~drift;
```

### D4. Turnajová selekce: chybí slovo „monotónním“

**Kde:** str. 2 (Otázka 1), oddíl „Selekce“ (ř. 172–173).

**Co je špatně:**

> „**turnaj** (tlak řídí velikost $k$, **invariantní k transformacím fitness**,
> nepotřebuje explicitní fitness — stačí porovnání)“

Plný text (ř. 323–324): „je invariantní vůči **monotónním** transformacím fitness“.

**Správně:** Turnaj je invariantní pouze vůči **rostoucím (pořadí zachovávajícím)**
transformacím. Vůči obecné transformaci invariantní není (triviálně $f\mapsto -f$
obrátí výsledek každého turnaje). Věta „turnajová selekce je invariantní vůči
transformacím fitness“ je u tabule okamžitě napadnutelná a typy selekce
a jejich vlastnosti jsou u této otázky nejčastější dotaz.

**Návrh opravy:** doplnit jedno slovo — `invariantní k~\emph{monotónním}
transformacím fitness`. Místo se najde vypuštěním věty „Historické větve
\tm{GA / ES / EP / GP} a~jejich charakteristické volby umět vyjmenovat.“
(ř. 221), která jen odkazuje na tabulku na str. 1.

### D5. V kritice teorie schémat chybí Royal Road / hitchhiking

**Kde:** str. 3, oddíl „Kritika teorie schémat“ (ř. 255–260).

**Co je špatně:** Výčet slabin je jinak úplný (jednokrokovost, konečné populace,
deceptivní úlohy, kolaterální konvergence, rozptyl uvnitř schématu, ignorování
konstruktivních efektů, závislost schémat), ale úplně vypadl **hlavní empirický
protipříklad k BBH**: Royal Road funkce (Mitchell, Forrest, Holland), tedy
krajina ušitá BBH na míru, na které jednoduchý GA **prohrál** s náhodně mutujícím
horolezcem (RMHC) kvůli **hitchhikingu**. Plný text tomu věnuje samostatný
odstavec (ř. 1364–1372); do „Shrnutí ke zkoušce“ plného textu se ale nedostal,
takže shrnutí tuto mezeru jen zdědilo. Deceptivní úlohy jsou „kdy GA selže
teoreticky“, Royal Road je „kdy selže i tam, kde by měl excelovat“ — to je jiný
a u zkoušky velmi vděčný argument.

**Správně / návrh opravy:** doplnit na konec výčtu jednu položku:

```tex
\tm{Royal Road} --- krajina ušitá BBH na míru, přesto na ní SGA prohrál
s~horolezcem (RMHC) kvůli \emph{hitchhikingu} (s~dobrým blokem se šíří i~parazitní
bity);
```

**Co na téže straně škrtnout:** poslední odstavec oddílu „Konečné populace:
Markovův řetězec“ (ř. 282–283), tj. větu „Shrnutí: nekonečné populace $=$
deterministický model (exaktní, nepraktický), konečné $=$ stochastický
(realistický, nezvládnutelný); limitní přechod je spojuje.“ Je to meta-rekapitulace
dvou bezprostředně předcházejících bloků a uvolní přesně 3 řádky.

---

## DROBNÉ

### S1. „osmiprvkovém příkladu“ — příklady PMX/OX/CX/ER jsou devítiprvkové

**Kde:** str. 1, „Co se chce spočítat u tabule“ (ř. 137) a str. 2, závěr oddílu
„Reprezentace a operátory“ (ř. 197).

**Co je špatně:** „PMX a OX na **osmiprvkovém** příkladu.“ Všechny permutační
příklady v plném textu pracují s devíti městy: $P_1=(123|4567|89)$ má
$3+4+2=9$ pozic, $P_2=(452|1876|93)$ rovněž, ER pracuje se seznamy sousedů
pro všech 9 měst.

**Správně:** *devítiprvkovém*. Chyba je zděděná z „Shrnutí ke zkoušce“ plného
textu (ř. 1121) — opravit na obou místech ve shrnutí i v plném textu.

### S2. $F(S)$ „závislá na populaci, ne na úloze“

**Kde:** str. 3, oddíl „Schéma“ (ř. 236–237).

**Co je špatně:** „(tedy veličina závislá na populaci, **ne na úloze**)“.
$F(S)$ je průměr $f$ přes reprezentanty v populaci, na úloze tedy závisí zcela
zásadně.

**Správně:** plný text (ř. 1183–1184) říká přesně: „závisí na aktuální populaci,
**nikoli jen** na $S$ a $f$“.

**Návrh opravy:** `(veličina závislá na populaci, nikoli jen na~$S$ a~$f$)`.

### S3. Pevné body $\mathcal{F}$ — chybí „z počáteční populace“

**Kde:** str. 3, oddíl „Voseho model“ (ř. 273).

**Co je špatně:** „$\mathcal{F}$ — populace kopií nejlepšího jedince“.

**Správně:** plný text (ř. 1477–1478, 1524–1525): „nejlepšího jedince
**přítomného v počáteční populaci**“. Vynechání je věcně důležité — pointa je,
že selekce sama nic nového nevytvoří, jen zaostří na to, co v populaci už je.

**Návrh opravy:** `$\mathcal{F}$ --- kopie nejlepšího jedince \emph{z~počáteční
populace} (selekce nic nového nevytvoří)`.

### S4. Markovův řetězec — chybí kontrast „bez elitismu nekonverguje“

**Kde:** str. 3, oddíl „Konečné populace: Markovův řetězec“ (ř. 280–281).

**Co je špatně:** Ze shrnutí plyne řetězec „$p_M>0$ ⇒ ireducibilní ⇒ elitistický
GA konverguje“, ale chybí právě to, co ten výsledek dělá zajímavým: **bez**
elitismu GA optimum navštíví nekonečně mnohokrát, ale **nekonverguje** k němu
(optimum se objeví a zase zmizí) — plný text ř. 1573–1575.

**Návrh opravy** (+7 slov, vejde se do uvolněného místa po škrtu z D5):

```tex
\tm{ireducibilní}; bez elitismu GA optimum navštíví, ale neudrží
$\Rightarrow$ \tm{elitistický GA konverguje k~optimu s~pravděpodobností 1}.
```

### S5. EDA — vzorec patří PBIL, nikoli UMDA

**Kde:** str. 3, oddíl „EDA“ (ř. 289).

**Co je špatně:** „**UMDA/PBIL** — nezávislé marginály
($p_i \gets (1-\alpha)p_i+\alpha x_i^{\mathrm{best}}$)“ — inkrementální posun
vektoru pravděpodobností je definiční rys **PBIL**. **UMDA** marginály v každé
generaci prostě **přepočítá jako relativní četnosti** ve vybrané podpopulaci
(žádné $\alpha$, žádná paměť předchozího modelu). Plný text obě metody odděluje
(ř. 1594–1597 i ř. 1643–1646: „PBIL: $p_i \gets \dots$“).

**Návrh opravy:** `\tm{UMDA} --- marginály z~vybrané podpopulace, \tm{PBIL} ---
inkrementálně ($p_i \gets (1-\alpha)p_i+\alpha x_i^{\mathrm{best}}$)`.

### S6. Varianty ACO — dvě chybějící slova

**Kde:** str. 5, oddíl „Varianty ACO“ (ř. 401–405).

**Co je špatně:** (a) „**ACS** … navíc *lokální* update při průchodu hranou“ —
neříká se **kterým směrem**; student si přirozeně domyslí posílení, přitom
lokální update feromon **snižuje** ($\tau\gets(1-\xi)\tau+\xi\tau_0$), aby další
mravenci hranu tolik neopakovali. (b) U **MAX–MIN** jsou uvedeny jen meze
$[\tau_{\min},\tau_{\max}]$, ale ne to, že **aktualizuje jen nejlepší mravenec**
(a inicializuje se na $\tau_{\max}$).

**Návrh opravy:** `\emph{lokální} update \emph{snižující} feromon při průchodu
hranou` a `\tm{MAX--MIN} (aktualizuje jen nejlepší, meze $\tau_{\min},\tau_{\max}$
proti předčasné konvergenci)`. Místo uvolní zkrácení první věty oddílu
„Východiska rojové inteligence“, která je z poloviny duplicitní s následujícím
výčtem klíčových slov.

### S7. XCS — chybí, že fitness je *relativní* přesnost, a podmínka $\epsilon\le\epsilon_0$

**Kde:** str. 7, oddíl „LCS: dva přístupy“, odrážka XCS (ř. 501–503).

**Co je špatně:** Vzorec $\kappa=\alpha(\epsilon/\epsilon_0)^{-\nu}$ je uveden
bez podmínky (platí pro $\epsilon>\epsilon_0$, jinak $\kappa=1$) a bez toho, že
fitness není $\kappa$ samo, ale **relativní přesnost v rámci action setu**
(plný text ř. 3027–3029). Právě ta relativizace je mechanismus, který dělá
nikový GA funkčním.

**Návrh opravy:** `$\kappa=\alpha(\epsilon/\epsilon_0)^{-\nu}$ (pro
$\epsilon\le\epsilon_0$ je $\kappa=1$), fitness $=$ \emph{relativní} $\kappa$
v~action setu`.

### S8. SPEA2 — „$\sigma$-tý soused“

**Kde:** str. 7, oddíl „Vícekriteriální optimalizace“ (ř. 553).

**Co je špatně:** „hustota přes **$\sigma$-tého souseda**“. V SPEA2 je
$\sigma_i^k$ **vzdálenost** k **$k$-tému** nejbližšímu sousedovi; $\sigma$ není
pořadové číslo. Chyba je zděděná z plného textu (ř. 3500).

**Návrh opravy:** `hustota z~vzdálenosti ke $k$-tému nejbližšímu sousedovi`.

### S9. CMA-ES — invariance vůči lineárním transformacím prostoru

**Kde:** str. 4, oddíl „CMA-ES“ (ř. 321–322).

**Co je špatně:** „Invariantní vůči monotónním transformacím fitness
a **lineárním transformacím prostoru**.“ Podle Hansena je CMA-ES bezpodmínečně
invariantní vůči **posunu a rotaci** (rigidním, úhel zachovávajícím
transformacím) prohledávaného prostoru; invariance vůči *obecné* lineární
transformaci platí jen tehdy, transformuje-li se odpovídajícím způsobem
i počáteční $\mathbf C$ (a počáteční bod). Zděděno z plného textu (ř. 2347–2348).

**Návrh opravy:** `invariantní vůči monotónním transformacím fitness
a~vůči posunu i~rotaci prostoru`. (Délkově kratší než původní.)

### S10. „akce démona v ACS“

**Kde:** str. 6, oddíl „Souvislosti“ (ř. 478–479).

**Co je špatně:** „…jako lokální krok (memetické algoritmy, **akce démona
v ACS**, 2-opt v TSP, WalkSAT v SAT)“. *Daemon actions* jsou složkou obecného
schématu **ACO** (plný text ř. 2529–2535), nikoli specifikem ACS; na str. 5 jsou
správně zařazeny pod obecné varianty.

**Návrh opravy:** `akce démona v~ACO`.

### S11. Chybějící nezlomitelné mezery a `vs.\ ` v `\hh{}` nadpisech

**Kde:** ř. 181, 190, 211, 218, 240, 248, 347 (chybí `~`) a ř. 388, 468
(chybí `\ ` po „vs.“).

**Co je špatně:** Běžný text je po této stránce vzorný (grep nenašel jedinou
jednopísmennou předložku bez `~`), ale uvnitř `\hh{}` konvence dodržena není:
`SGA a binární kódování`, `Reprezentace a operátory`, `Varianty GP a gramatická
evoluce`, `Evoluční programování a poučení`, `Věta o schématech (TST)`,
`BBH a implicitní paralelismus`, `Diverzita a dynamické krajiny`; a dále
`PSO vs. GA`, `Ladění vs. řízení parametrů`, kde tečka po „vs“ způsobí
mezivětnou (příliš širokou) mezeru.

**Návrh opravy:** `SGA a~binární kódování`, `Věta o~schématech (TST)`,
`PSO vs.\ GA`, `Ladění vs.\ řízení parametrů` atd. — čistě mechanická oprava,
délku nemění.

### S12. Anglické termíny v `\tm{}` místo `\en{}`, chybějící české ekvivalenty

**Kde:** str. 6 ř. 429–431 (`\tm{steepest ascent}`, `\tm{first improvement}`,
`\tm{stochastic}`), ř. 445 (`\tm{tenure}`), ř. 465 (`\tm{Memetic computing}`),
str. 5 ř. 384 (`\tm{constriction}`), ř. 411 (`\tm{Firefly}`), str. 2 ř. 212
(`\tm{Cartesian GP}`), ř. 204 (`\en{introny}`).

**Co je špatně:** Dokument má na to dvě makra (`\tm{}` český termín tučně,
`\en{}` anglický ekvivalent kurzívou) a jinde je používá vzorně
(`\tm{ABC} (\en{artificial bee colony})`, `\tm{Ladění} (\en{tuning})`).
V uvedených místech je anglický termín vysázen jako český (tučně) a chybí
český překlad, který plný text má: *nejstrmější stoupání*, *první zlepšení*,
*kartézské GP*, *memetické počítání*, *konstrikční faktor*, *světluška*.
`\en{introny}` je opačná chyba — „introny“ je česky, kurzivou má být buď nic,
nebo `\en{introns}`.

**Návrh opravy:** `\tm{nejstrmější stoupání} (\en{steepest ascent})`,
`\tm{první zlepšení} (\en{first improvement})`, `\tm{Kartézské GP}`,
`\tm{Memetické počítání} (\en{memetic computing})` atd. Kde by to bylo příliš
dlouhé (str. 6 je hustá), stačí přepnout `\tm{}` na `\en{}` bez překladu — sazba
pak aspoň nelže o tom, že jde o anglický termín.

### S13. Diverzita — doplnit paralelní modely (master–slave / buněčný)

**Kde:** str. 4, oddíl „Diverzita a dynamické krajiny“ (ř. 348).

**Co je špatně:** Uveden je jen „ostrovní model“. Plný text mezitím (nález D10
staré recenze) doplnil systematické rozlišení **master–slave / ostrovní
(hrubozrnný) / buněčný (jemnozrnný, mřížka)** včetně poznámky, že ostrovní
a buněčný model mění samotnou dynamiku algoritmu (ř. 2210–2227). Shrnutí ten
doplněk nereflektuje.

**Návrh opravy** (+4 slova, žádný škrt není potřeba, řádek není plný):

```tex
Diverzita: fitness sharing, crowding, speciace, nenáhodné páření, paralelní
modely (master--slave / ostrovní / buněčný na mřížce).
```

### S14. Dva `Underfull \hbox` v tabulce na str. 1

**Kde:** log, ř. 1076 a 1081 → `.tex` ř. 92 („náhodní rodiče,“) a ř. 97
(„turnaj rodiče $+$ potomci“) — buňky sloupce *selekce* u řádků ES a EP.

**Co je špatně:** Nic vážného; `p{}` sloupec text zarovnává do bloku, takže
krátký poslední řádek hlásí badness 10000. Vizuálně se to projeví mírně
rozházeným mezislovím v těch dvou buňkách.

**Návrh opravy:** do preambule tabulky přidat `\raggedright` pro tyto sloupce
(např. přes `>{\raggedright\arraybackslash}p{3.0cm}`, jak to dělá plný text),
nebo prostě ignorovat — Overfull box tam žádný není.

---

## Poznámky bez nutnosti zásahu

- **Ostatní nálezy staré recenze plného textu jsou ve shrnutí zapracovány
  správně:** EDA má vlastní blok (D1), Voseho symetrie je uvedena explicitně
  (D2), otevřená evoluce má znaky i generativní reprezentace (D4), interaktivní
  evoluce je přítomna (D5), bloat má všechny tři teorie (D8), UCS je zmíněno
  (D11), XCS používá konstantu $\alpha$ (N5).
- **Nález D6 staré recenze (varianta s $2n$ strategickými parametry) zatím není
  ani v plném textu, ani ve shrnutí.** Doplní-li se do plného textu, je třeba
  doplnit i řádek na str. 4 shrnutí — vejde se, stačí `1 / $n$ / $2n$ /
  $n(n+1)/2$`.
- **Hillisovy sítě:** shrnutí čísla neuvádí vůbec, což je bezpečné. Zvažte přesto
  doplnit „61 komparátorů vs. 65 bez koevoluce (Green 1969: 60)“ — je to
  memorovatelný a u zkoušky vděčný fakt. Protiváha na str. 4: zkrátit řádek
  „Diverzita: fitness sharing, crowding, …“, který doslova duplikuje odrážku
  „Udržení diverzity“ z rozcestníku na str. 1.
- **Dvoubodové křížení:** shrnutí uvádí jen „bez okrajového biasu“. Vzorec
  $2d(m-d)/(m(m-1))$, který plný text po nálezu D7 doplnil, by se na str. 2 vešel
  místo vypuštěné věty o historických větvích (viz D4) — ale není nutný.
- **Didaktika:** rozvržení stran je vyvážené, „Nejčastější chyby“ na str. 1 jsou
  všech pět věcně správné a trefné (zejména pořadí $\sigma$ → $x$ a to, že věta
  o schématech není důkaz konvergence), a blok „Co se chce spočítat u tabule“
  přesně odpovídá číselným příkladům, které plný text nabízí.


---

## Zapracováno (12. 8. 2026)

Opraveno ve `02-prirodou-inspirovane-pocitani-shrnuti.tex`, PDF přeloženo znovu
(7 stran, 0 overfull):

| nález | jak |
|---|---|
| K1 | efekt Červené královny přepsán podle plného textu (ř. 2058–2061): všichni se zlepšují, ale relativní fitness zůstává konstantní |
| D1 | nadpis str. 7 doslovně, včetně „evoluce expertních systémů“ a „řešení kombinatorických úloh“ |
| D2 | HyperNEAT: substrát = geometrické rozmístění neuronů, váhy generuje CPPN jako funkce $\mathbb{R}^4\to\mathbb{R}$ |
| D3 | kritika TST: „tvrzení o střední hodnotě; v konečné a malé populaci výběrové chyby (drift)“ místo „předpokládá nekonečnou populaci“ |
| D4 | turnaj: „invariantní k **monotónním** transformacím fitness“ |
| S1 | „osmiprvkovém“ → „devítiprvkovém“ příkladu (PMX/OX pracují s 9 městy — ověřeno na ř. 707) |
| S5 | rozděleno: UMDA (marginály z vybrané podpopulace) vs. PBIL (inkrementální vzorec) |
| S6 | u ACS doplněno, že lokální update feromon snižuje |
| S7 | XCS: doplněno $\epsilon\le\epsilon_0\Rightarrow\kappa=1$ a relativní přesnost v action setu |
| S8 | SPEA2: „$k$-tého nejbližšího souseda“ |
| S11 | nezlomitelné mezery v 9 `\hh{}` nadpisech |

**Nezapracováno**: D5 (Royal Road / hitchhiking), S2, S3, S4, S9, S10, S12, S13, S14.

Pozn.: D2 a S1 jsou zděděné z plného textu — tam opraveny **nejsou**, shrnutí je teď
v obou bodech přesnější než zdroj.
