# Kritická recenze: `01-multiagentni-systemy.tex` (49 s., 3141 řádků)

Recenzent: přísný oponent učebních textů pro SZZ MFF UK, obor Umělá inteligence.
Referenční zdroje: slidy NAIL106 (Neruda, 2025, `mas25.txt`, 2150 ř. / 221 s. PDF),
`MAS_notes.md`, `MAS_pojmy.md`, Wooldridge (2009), Shoham & Leyton-Brown (2009).

**Celkové hodnocení.** Text je nadprůměrně dobrý: struktura odpovídá okruhu, formalismus
je věrný slidům, na několika místech dokonce opravuje chyby přednášky (RDF = *Resource
Description Framework*, KIF = *Knowledge Interchange Format*, $\mathcal{ALC}$ místo
překlepu „ACL“, A-Box = asertivní část, doplnění `ArmEmpty` do počátečního stavu světa
kostek, $B_n \models G$ místo slidového $B_{i-1} \models G$). Přesto obsahuje **jednu
tvrdou početní chybu**, několik definičních nepřesností proti standardní literatuře
a **chybí mu látka, kterou přednáška explicitně probírá** (IDA / global workspace,
sociologický pohled na MAS) i **klíčový početní příklad na volební systémy**, který
patří k nejčastěji zkoušeným úlohám celého okruhu.

Nálezy: **8 KRITICKÝCH**, **9 DŮLEŽITÝCH**, **11 DROBNÝCH**.

---

## A. KRITICKÉ (fakticky špatně)

### K1. Příklad běhu CBS — chybná cena optimálního řešení (ř. 1412–1419)
**Kde:** kap. 4.4, odstavec „Příklad běhu CBS“.
**Co je špatně:** Text tvrdí, že v koridoru $1-2-3$ s výklenkem $4$ napojeným na $2$
(agenti $a_1: 1\to3$, $a_2: 3\to1$) najde CBS „řešení ceny 5 --- $a_2$ uhne do $4$
a pustí $a_1$“. **Řešení ceny 5 neexistuje.** Ověřeno vyčerpávajícím prohledáním všech
bezkonfliktních dvojic cest do horizontu 7:

* cena 5 by znamenala rozdělení $2+3$; agent s cenou 2 jde přímo přes vrchol 2, druhý
  pak nutně způsobí buď vrcholový konflikt v 2, nebo *swap* konflikt na hraně $(2,3)$;
* cena 6 ($3+3$ i $2+4$) je z týchž důvodů rovněž nedosažitelná (všechny čtyři
  kombinace cest délky 3 kolidují ve vrcholu 2);
* **optimum je sum-of-costs $= 7$**: $a_1 = (1,1,2,3)$ za 3 a $a_2 = (3,2,4,2,1)$ za 4.

Navíc popis „$a_2$ uhne do 4 a pustí $a_1$“ neodpovídá tomu, že *oba* agenti musí
ustoupit od individuálně optimální cesty (jeden čeká, druhý zajíždí do výklenku).
**Jak opravit:** přepsat na cenu 7, uvést konkrétní obě trajektorie po časových krocích
a doplnit, že kořen má cenu 4, oba potomci po prvním větvení cenu 5 a teprve další
větvení (na *swap* konflikt) dá 7 — to je zároveň hezká ilustrace toho, že cena v uzlech
stromu omezení monotónně roste. Také doplnit, že bez výklenku je instance **neřešitelná**
a CBS by větvil donekonečna (základní CBS je úplný jen pro řešitelné instance).

### K2. Subsumpční architektura — relace inhibice je definovaná obráceně (ř. 958–961)
**Kde:** kap. 3.2, odstavec pod pseudokódem.
**Co je špatně:** „$b_1 \prec b_2$ znamená ‚$b_1$ je potlačeno $b_2$‘“. Wooldridge
(2. vyd., §5.1) definuje přesně opačně: *„$b_1 \prec b_2$ means that $b_1$ will inhibit
$b_2$: $b_1$ is lower in the subsumption hierarchy and will hence get priority over
$b_2$.“* Zkoušející čtoucí zápis $R1 \prec R2 \prec \dots$ ze slidů (a slidy tuto notaci
používají: „Priority: R1 < R6 < R7 < R4 < R8 < R5“) ho bude číst po Wooldridgeovi.
Text si sice zůstává vnitřně konzistentní (používá $\succ$), ale definici má proti
literatuře i proti přednášce převrácenou.
**Jak opravit:** definovat $b_1 \prec b_2$ = „$b_1$ inhibuje (potlačuje) $b_2$, tedy má
přednost“, a příklad průzkumníka Marsu přepsat do téže notace, jakou používají slidy.

### K3. Agent network architecture — chybný význam parametru $\pi$ (ř. 1045–1049)
**Kde:** kap. 3.3.
**Co je špatně:** „$\pi$ (práh proveditelnosti)“. V Maesově modelu (*How to do the right
thing*, 1989) je $\pi$ **průměrná úroveň aktivace v síti**, podle níž se po každém kroku
aktivace normalizuje; práh je jediný — $\theta$. Text tedy vyrábí parametr, který
neexistuje, a zároveň nevysvětlí, k čemu je normalizace (kterou o dva řádky níž zmiňuje).
**Jak opravit:** $\pi$ = průměrná (celková) úroveň aktivace udržovaná normalizací;
doplnit Maesovo pravidlo, že se $\theta$ o 10 % sníží, pokud v daném kroku není vybrán
žádný modul (jinak by síť mohla „zamrznout“).

### K4. FIPA-ACL — chybný počet polí zprávy (ř. 1744)
**Kde:** kap. 6.3, defbox FIPA-ACL.
**Co je špatně:** „Struktura zprávy (14 polí, povinné je jen `performative`)“.
Specifikace FIPA SC00061 definuje `performative` + **12 parametrů** (`sender`,
`receiver`, `reply-to`, `content`, `language`, `encoding`, `ontology`, `protocol`,
`conversation-id`, `reply-with`, `in-reply-to`, `reply-by`), tj. **13 polí** — a přesně
13 jich vyjmenovává i tabulka hned pod tím. Číslo v textu si odporuje s vlastní tabulkou.
**Jak opravit:** 13.

### K5. FPSB — vnitřní rozpor mezi „dominantní strategií“ a příkladem (ř. 2508–2513 vs. 2549)
**Kde:** kap. 10.2, tabulka čtyř aukcí + příklad 80/60/30.
**Co je špatně:** tabulka uvádí ve sloupci **„Dominantní strategie“** pro FPSB
„nabídnout méně než své ocenění“, ale příklad pak tvrdí, že $A$ zaplatí **80**, tedy
přesně své ocenění. Obojí zároveň platit nemůže. Věcně navíc platí, že **FPSB (a stejně
tak holandská aukce) dominantní strategii nemá vůbec** — optimální míra podhodnocení
závisí na přesvědčení o ostatních; sloupec je tedy pojmenován nepřesně.
**Jak opravit:** sloupec přejmenovat na „Racionální / dominantní strategie“, u FPSB
a holandské explicitně napsat, že dominantní strategie neexistuje (formulace z přednášky
„$\varepsilon$ pod svou utilitou“ je heuristika, ne dominance), a v příkladu vysvětlit,
proč vychází 80: v ideálním scénáři *bez jakékoli informace o ostatních* si $A$ nemůže
dovolit shazovat nabídku, se znalostí ocenění by nabídl $60+\varepsilon$.

### K6. Axelrodovy vlastnosti — sloučení dvou různých vlastností (ř. 2206–2207)
**Kde:** kap. 8.3, defbox iterovaného PD.
**Co je špatně:** „**srozumitelnost** (*clear/non-envious*) --- buď předvídatelný,
nesnaž se soupeře porazit“. To jsou u Axelroda **dvě různé** vlastnosti: *non-envious*
(nezáviď, neusiluj o to porazit konkrétního soupeře — TFT nikdy nezískal víc bodů než
jeho protihráč) a *clarity* (buď srozumitelný a předvídatelný, aby se s tebou dalo
spolupracovat). Kanonická čtveřice z *The Evolution of Cooperation* je
nice / retaliating / forgiving / non-envious, srozumitelnost bývá uváděna jako pátá.
**Jak opravit:** rozdělit na dvě odrážky.

### K7. Condorcetův paradox vs. kámen–nůžky–papír — nepravdivé „formálně přesná analogie“ (ř. 2374–2375)
**Kde:** kap. 9.2, defbox Condorcetova paradoxu (a znovu ř. 2275).
**Co je špatně:** „**Formálně** jde o **přesnou** analogii neexistence Nashova ekvilibria
v ryzích strategiích u hry kámen--nůžky--papír.“ Žádná formální redukce mezi cyklickou
majoritní preferencí a neexistencí ryzího NE neexistuje; slidy říkají opatrně
„The **similar** situation as with Nash equilibrium for the Rock-Paper-Scissors game“.
Tvrzení v této síle je nepravdivé a u zkoušky snadno napadnutelné.
**Jak opravit:** zeslabit na „obdobná situace / stejný motiv cyklické (necyklické
uspořádatelné) struktury preferencí“.

### K8. Sémantika `inform` — neúplná feasibility precondition (ř. 1802)
**Kde:** kap. 6.3, defbox „Sémantika FIPA-ACL: FP a RE“.
**Co je špatně:** uvedeno $\text{FP: } B_i\varphi \wedge \neg B_i(\mathit{Bif}_j\varphi)$.
Specifikace FIPA má $B_i\varphi \wedge \neg B_i(\mathit{Bif}_j\varphi \vee
\mathit{Uif}_j\varphi)$ — chybí disjunkt s operátorem nejistoty $U$, přestože operátor
$U_i$ je o tři řádky výš zaveden a slovní komentář („ani zda platí, či ne“) ho už
předpokládá.
**Jak opravit:** doplnit $\vee\, \mathit{Uif}_j\varphi$.

---

## B. DŮLEŽITÉ (chybí vůči okruhu nebo vůči kurzu)

### D1. Chybí IDA a teorie globálního pracovního prostoru (slidy ř. 2093–2120)
Přednáška má samostatný blok **„Complex Agent Architectures — IDA“** (S. Franklin,
*Intelligent Distribution Agent*), inspirovaný **global workspace theory** (Baars):
mysl jako MAS mnoha jednoduchých procesů komunikujících přes sdílenou paměť typu
blackboard, dynamicky vznikající **koalice** procesů, koalice nejlépe odpovídající
vstupu se dostane do „vědomí“ a je vykonána, hierarchie kontextů. V dokumentu **není
ani zmínka**. Přitom to hezky uzavírá linii mechanismů výběru akce (je to čtvrtý typ
arbitráže vedle priority, aktivace a vrstev) a váže se na blackboard z kap. 7.
**Doplnit** jako defbox do kap. 3 (hybridní/komplexní architektury) + řádek do shrnutí
a do srovnávací tabulky architektur.

### D2. Chybí sociologický pohled na MAS a ABM (slidy ř. 124–132)
Přednáška uvádí **pět** úhlů pohledu; dokument jen čtyři (SW inženýrství, distribuované
systémy, UI, teorie her). Chybí **sociologie**: klíčovým pojmem MAS jsou agentní
společnosti, sociologie (a ekologie, ekonomie) používá agenty pro simulační modely
(**ABM**), s obvyklou výhradou „inspirace ano, nutnost ne“ (letadla vs. ptáci).
Bez toho zůstává později zmíněné NetLogo bez motivace.
**Doplnit** pátou odrážku do kap. 1.1 a odkaz na NetLogo/ABM v kap. 12.

### D3. Chybí početní příklad na volební systémy (kap. 9)
Nejzávažnější **didaktická** mezera. Celá kapitola 9 je bez jediného preferenčního plánu
s čísly, přestože typická zkoušková úloha zní „tady je preferenční plán, kdo vyhraje
podle plurality / IRV / Bordy / Condorceta a co to říká o vlastnostech systémů“.
Text má u aukcí i u Q-learningu spočítané příklady, tady ne — hloubka je nevyvážená.
**Doplnit** jeden preferenční plán, na kterém *různé systémy dají různé vítěze*
(ideálně tak, aby Condorcetův vítěz existoval a plurality ho nezvolila), s celým výpočtem.

### D4. Chybí rámec návrhu mechanismů (*mechanism design*) — kap. 10
Okruh říká „alokace zdrojů, aukce“; text má Vickreyho, VCG i Gibbarda–Satterthwaita,
ale **nikde nedefinuje mechanismus** a jeho žádoucí vlastnosti (incentive compatibility
/ strategy-proofness, individuální racionalita, efektivita, vyrovnaný rozpočet,
výpočetní zvládnutelnost) ani **princip odhalení** (*revelation principle*), přestože
na tyto pojmy odkazuje v závěru („mechanism design“ v ose 2). Tím visí ve vzduchu, proč
je Vickrey „lepší“ než FPSB a proč je VCG „zobecnění“.
**Doplnit** kompaktní defbox před Vickreyho / před VCG.

### D5. Chybí kooperativní (koaliční) teorie her — kap. 8
Okruh explicitně jmenuje „kooperaci“ a „Nashova ekvilibria, Paretovu efektivitu“;
standardní literatura (Wooldridge kap. 13, Shoham–Leyton-Brown kap. 12) k tomu řadí
**koaliční hry**: charakteristická funkce, superaditivita, velká koalice, **jádro**
(*core*) a **Shapleyho hodnota** jako férové rozdělení zisku, výpočetní obtížnost
(reprezentace charakteristické funkce, prázdné jádro). V dokumentu není nic.
Přednáška je sice neprobírá, ale zkoušející z herně-teoretické strany se na ně ptají
a je to nejlevnější způsob, jak text zpevnit vůči formulaci okruhu „kooperace“.
**Doplnit** stručný defbox (nekooperativní vs. kooperativní hry, jádro, Shapley).

### D6. Chybí distribuované řešení omezujících podmínek (DisCSP / DCOP) — kap. 7
Kapitola „Distribuované řešení problémů“ pokrývá CDPS, CNET a blackboard, ale ne
**formální** větev distribuovaného řešení problémů: DisCSP (Yokoo: ABT — asynchronous
backtracking) a DCOP (ADOPT, DPOP, Max-Sum) — tedy typickou úlohu „agenti drží proměnné,
omezení jsou mezi agenty, hledá se globálně konzistentní/optimální přiřazení“
(rozvrhování schůzek, alokace senzorů, koordinace v MAPF). Bez toho je název kapitoly
širší než její obsah.
**Doplnit** krátký defbox.

### D7. Chybí zmínka o vzorkovacích plánovačích (RRT/PRM) — kap. 4
Kapitola „Problém hledání cesty“ je celá diskrétní/grafová. Jedna věta o spojitých
konfiguračních prostorech (PRM, RRT/RRT*, potenciálová pole a jejich lokální minima)
uzavře otázku „a co když prostředí není mřížka“, kterou zkoušející rád položí, protože
text sám v definici zmiňuje „mřížku konfiguračního prostoru robota“.

### D8. Dominance definována jen silná (ř. 2100–2103)
Slidy definují dominanci **slabě** („better **or same** result … against all strategies“),
text jen silně („striktně lepší“). Rozdíl není kosmetický: pravdomluvnost ve Vickreyově
aukci je jen **slabě** dominantní (což text o 400 řádků dál správně píše) a IESDS se
slabě dominovanými strategiemi **závisí na pořadí** odstraňování. Doplnit obě varianty
a poznámku o pořadí.

### D9. Chybí Dennettova pointa o intencionalitě (slidy ř. 304–312)
Slidy končí blok o intencionálních systémech otázkou, zda intencionalita existuje sama
o sobě, nebo vzniká až interpretací — a Dennettovou odpovědí, že **bez interpretace
intencionalita neexistuje**. Text má Dennetta i tři postoje, ale tuhle pointu ne;
je to přesně ten typ „drobnosti“, na kterou se u ústní zkoušky dá narazit.

---

## C. DROBNÉ (styl, přesnost, sazba)

* **C1 (ř. 945–956).** Pseudokód výběru akce v subsumpci je tautologický: iteruje se
  „v pořadí od nejvyšší priority“ a uvnitř se testuje „neexistuje $b'$ s vyšší
  prioritou“. Buď iterovat neuspořádaně a testovat, nebo iterovat uspořádaně a vrátit
  první. Zjednodušit.
* **C2 (ř. 1010–1023).** Slidy uvádějí *activation threshold* jako vlastnost **modulu**,
  Maes (a text) jako **globální** práh. Rozdíl stojí za jednu poznámku, aby student
  nebyl u zkoušky překvapen formulací přednášejícího.
* **C3 (ř. 2264–2276).** Nadpis „**Přehled:** hra bez ryzího NE“ — má být spíš
  „Doplněk / Příklad“; „Přehled“ svádí k očekávání tabulky.
* **C4 (ř. 2259).** U hry Chicken se píše „Existuje i symetrické smíšené NE“ bez hodnoty.
  Doplnit $p = 1/2$ (výpočtem $1+4p = 6p$) — text jinde slibuje „umět spočítat smíšené
  NE pro $2\times2$“, tak ať je ukázka i na antikoordinační hře.
* **C5 (ř. 1471).** Motivační příklad ontologie („7777, SRPR“) je převzat doslova ze
  slidů, ale bez uvedení, že jde o dialog Anny a Borise — drobná ztráta srozumitelnosti.
* **C6.** Kap. 12 (metodologie, JADE, Jason, NetLogo, SPADE, FIPA platforma) je psaná
  z obecných znalostí — v extrahovaných slidech `mas25.txt` tato část chybí (deck končí
  u LLM agentů), byť ji sylabus přednášky jmenuje. Fakticky jsem neshledal chybu
  (AMS/DF/MTS/ACC, Gaia role model, Prometheus, Tropos i JADE `Behaviour` sedí), ale je
  vhodné to nechat tak, jak je — jen doplnit, že NetLogo/ABM navazuje na sociologický
  pohled z kap. 1 (viz D2).
* **C7 — sazba: overfull box 127 pt (ř. 1528–1532).** Inline XML příklad
  `\texttt{<product typ='CD'>...</product>}` výrazně přetéká do okraje. Rozlomit do
  `quote` bloku.
* **C8 — sazba: overfull box 88 pt (ř. 1214–1218).** Displej s $g(n)$, $h(n)$, $f(n)$
  na jediném řádku. Rozdělit.
* **C9 — sazba: overfull box 53 pt (ř. 2749–2753).** Bellmanova rovnice optimality —
  dvě rovnice ($V^*$ a $Q^*$) na jednom řádku. Dát pod sebe.
* **C10 — sazba: overfull box 52 pt (ř. 705–709)** (ověření plánu ve světě kostek)
  **a 39 pt (ř. 2016–2020)** (příklad BBWar) — přeformulovat/rozlomit.
* **C11 — sazba: overfull box 35 pt (ř. 626)** — `align*` funkcí deliberace s dlouhým
  komentářem u `options`. Zkrátit komentář.

Zbylé overfull boxy (0,4 / 2,2 / 2,3 / 6,2 / 10,2 / 12,8 pt) jsou pod hranicí
viditelnosti, neřeším. Kompilace jinak proběhne bez chyb, všechny reference se rozřeší
ve druhém průchodu, `algorithmic` mimo `algorithm` prostředí funguje.

---

## D. Co je naopak ověřeno jako správné (výběr)

Přepočítal jsem všechny číselné příklady a formalizace:

* výplatní matice a závěry pro **vězňovo dilema** ($T>R>P>S$, $2R>T+S$, $(D,D)$ jediné NE
  i jediné ne-Pareto-optimální, $(C,C)$ maximalizuje $sw = 6$) — **správně**;
* **smíšené NE koordinační hry**: $q = 2-2q \Rightarrow q = 2/3$, hráč $j$ hraje Balet
  s $2/3$, hráč $i$ Zápas s $2/3$, očekávaná utilita $2/3$ — **správně** (přepočítáno
  i z druhé strany: $2p = 1-p \Rightarrow p = 1/3$);
* **Chicken**: $(C,D)$ a $(D,C)$ jsou NE, $sw$-maximum $(C,C) = 10$ není NE — **správně**;
* **matching pennies**: bez ryzího NE, smíšené $(1/2,1/2)$, hodnota 0 — **správně**;
* **Vickrey**: důkaz slabé dominance pravdomluvnosti (rozbor $b>v$ a $b<v$) —
  **správně a úplně**;
* **VCG příklad** ($\{x\}\!\to\!5$, $\{y\}\!\to\!4$, $\{x,y\}\!\to\!8$): alokace $5+4=9$,
  $p_1 = 8-4 = 4$, $p_2 = 8-5 = 3$, výnos 7 < 8 — **správně**;
* **aukční příklad 80/60/30** (61 / 80 / 80 / 60) — **shodný se slidy**;
* **Q-learning krok** ($\alpha=0{,}5$, $\gamma=0{,}9$, $r=10$, $\max = 8$):
  cíl 17,2, chyba 13,2, nové $Q = 10{,}6$ — **správně**;
* **Bellmanovy rovnice**, value/policy iteration, SARSA, REINFORCE, Minimax-Q LP,
  advantage $A = Q - V$ — **správně**, v souladu se slidy;
* **A\*** ($f=4$ podél celé optimální cesty v $3\times3$ s překážkou na $(1,1)$),
  přípustnost/konzistence, $h\equiv0 \Rightarrow$ Dijkstra, oktilová heuristika,
  weighted A\* — **správně**;
* **MAPF**: NP-těžkost optima pro obě účelové funkce vs. polynomiální rozhodnutí
  řešitelnosti (Kornhauser a kol. 1984) — **správně**;
* **STRIPS** svět kostek: $\pi = (\mathit{UnStack}(A,B), \mathit{PutDown}(A))$ včetně
  posloupnosti $B_i$ — **správně** (a text správně doplnil `ArmEmpty`, který ve slidech
  v počátečním stavu chybí);
* **volební vlastnosti** (Pareto: majority + Borda ano, sekvenční ne; Condorcetův vítěz:
  sekvenční + Bordovy kombinace ano, plurality a samotná Borda ne; IIA prakticky nikdo),
  **Arrowova věta** i její jednodušší verze, **Gibbard–Satterthwaite** — **správně**;
* **Contract Net** (4 fáze), **CDPS/PPS/MAS**, **BBS** (tabule/experti/arbitr),
  **řečové akty** (lokuce/ilokuce/perlokuce, 5 Searlových kategorií, Cohen–Perrault
  Request/Inform včetně pointy, že efektem Inform není víra v $\varphi$) — **správně**;
* **ontologie** (Gruber, škála formalizace, RDF/RDFS/OWL/DL, T-Box/A-Box, profily
  $\mathcal{SHIF}$/$\mathcal{SHOIN}$/$\mathcal{SROIQ}$, OWA) — **správně**, na několika
  místech přesnější než slidy.
