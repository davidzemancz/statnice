# Kritická recenze: `01-multiagentni-systemy-shrnuti.tex` (8 s., 641 řádků)

Recenzent: nezávislý oponent učebních textů pro SZZ MFF UK, obor Umělá inteligence.

## Rozsah

Recenzován je **kondenzát** okruhu Multiagentní systémy (`01-multiagentni-systemy-shrnuti.tex`,
PDF 8 stran). Ověřováno proti:

* plnému textu `01-multiagentni-systemy.tex` (3070 ř.) — hledány **rozpory** a **zavádějící zkratky**;
* oficiálnímu znění okruhu (ověřeno WebFetchem 12. 8. 2026, MFF UK, studijní plány 2025/2026,
  zaměření *Inteligentní agenti*) — hledáno **pokrytí** a doslovnost nadpisů;
* vlastní znalosti oboru: Wooldridge, *An Introduction to MultiAgent Systems* (2. vyd. 2009);
  Shoham & Leyton-Brown, *Multiagent Systems* (2009); Russell & Norvig, *AIMA*;
  Cohen & Perrault (1979); Maes (1989); Brooks (1986); specifikace FIPA SC00037J/SC00061;
  Sutton & Barton, *Reinforcement Learning*; Sharon et al. (CBS).

Ověřen i **invariant rozsahu**: `pdfinfo` hlásí 8 stran (1 rozcestník + 7 otázek), tedy invariant
„jedna otázka = jedna strana“ **drží**. Log neobsahuje **žádný overfull box** (jen neškodné
`microtype Warning: Unable to apply patch 'item'`). Vizuální kontrola volného místa po stranách
(`pdftoppm`, 70 dpi): str. 2 ≈ 20 %, str. 3 ≈ 20 %, str. 4 ≈ 40 %, str. 5 ≈ 22 %, str. 7 ≈ 25 %,
str. 8 ≈ 22 % volné; **str. 6 je zaplněná téměř na 100 %** — pouze u ní vyžadují návrhy doplnění
kompenzační škrt (uveden u každého nálezu).

## Souhrn

| Severita | Počet | Kde |
|---|---|---|
| **KRITICKÉ** (fakticky špatně) | **2** | K1 str. 5 (Cohen–Perrault Request), K2 str. 2 (vyjadřovací síla architektur) |
| **DŮLEŽITÉ** (rozpor s plným textem, zavádějící zkratka, mezera v pokrytí) | **4** | D1 str. 3, D2 str. 6, D3 str. 8, D4 str. 5 |
| **DROBNÉ** (přesnost, sazba, jazyk) | **17** | S1–S17 |

**Celkové hodnocení.** Kondenzace je nadprůměrně čistá. Šrouby, na kterých se kondenzáty obvykle
lámou, drží: A\* (přípustnost vs. konzistence, správně i „v grafové verzi s reexpanzí“), STRIPS
(přípustný vs. korektní plán, `\models`), commitment strategie, parametry $\gamma/\phi$ v síti Maes,
S5 vs. KD45, 22 performativ FIPA, PPAD-úplnost, Vickrey vs. FPSB, VCG jako externalita,
off-policy vs. on-policy, CTDE. Text se nikde nedopouští chyb, které předchozí recenze našla
v plné verzi (počet polí FIPA zprávy, směr inhibice v Maesově $\pi$, sloučení Axelrodových
vlastností). Nálezy jsou proto soustředěné do **dvou míst, kde kondenzace ubrala jednu modální
vrstvu nebo jeden kvantifikátor** — a právě tam by student odpověděl špatně.

### Co je naopak v pořádku a bylo ověřeno

Přepočítal a proti literatuře prověřil jsem každý vzorec a každé číslo ve shrnutí:

* **Formalismus abstraktní architektury**: $E$, $A$, běh $r=e_0a_0e_1\dots e_n$, $R^A$/$R^E$,
  $\tau:R^A\to 2^E$ (odtud historie *i* nedeterminismus), $\mathit{Env}=\langle E,e_0,\tau\rangle$,
  $Ag:R^E\to A$, $\mathcal{R}(Ag,\mathit{Env})$, funkční ekvivalence (vzhledem k prostředí /
  prostá) — **správně a úplně**; $\tau(r)=\emptyset$ jako konec běhu též.
* **Predikátová specifikace**: $\Psi:R\to\{0,1\}$, pesimista/optimista/realista, úlohy dosažení
  ($G$) a udržení ($B$) — **správně**.
* **Optimální agent** $\arg\max_{Ag}\sum_r P(r\mid Ag,\mathit{Env})u(r)$, nekonstruktivnost,
  Tileworld $u(r)=N_f/N_a$ — **správně**; doplněná zmínka o *bounded optimality* (Russell) je
  věcně správná a v plném textu není — vhodné rozšíření, ne chyba.
* **STRIPS**: $\langle P_a,D_a,A_a\rangle$, $\langle B_0,O,G\rangle$,
  $B_i=(B_{i-1}\setminus D_{a_i})\cup A_{a_i}$, přípustný ($B_{i-1}\models P_{a_i}$) vs. korektní
  (navíc $B_n\models G$) — **správně**, včetně $B_n$ (ne $B_{i-1}$, jak mají slidy).
* **Commitment**: blind / single-minded / open-minded, bold vs. cautious, efektivita =
  dosažené/všechny záměry, pravidlo pomalé→bold / rychlé→cautious (Kinny & Georgeff) — **správně**.
* **Maes**: moduly s předpoklady a add/delete listem, následnické / předchůdcovské / konfliktní
  spoje, tři zdroje aktivace (stav světa, cíle, inhibice od chráněných cílů), výběr proveditelného
  modulu s nejvyšší aktivací nad prahem + vynulování, $\gamma/\phi$ jako osa proaktivita–reaktivita
  — **správně**, věrně Maes (1989).
* **Hybridní**: horizontální ($m^n$ kombinací, mediátor jako úzké hrdlo) vs. vertikální
  (one-/two-pass, $n-1$ rozhraní, křehkost); TouringMachines horizontální, InteRRaP vertikální
  two-pass s vlastní KB na vrstvu — **správně**; čtyři typy arbitráže včetně IDA **správně**.
* **A\***: $f=g+h$; $h\le h^*$ ⇒ optimalita; $h(n)\le w(n,m)+h(m)$ ⇒ neklesající $f$ a nejvýš jedna
  expanze vrcholu; konzistence ⇒ přípustnost; $h\equiv0$ ⇒ Dijkstra; weighted A\* jako
  $\varepsilon$-suboptimální; manhattan/oktil/eukleid — **správně**.
* **LPA\*/D\* Lite**: $g$ a *rhs*, lokální konzistence $g=\mathit{rhs}$, prohledávání od cíle
  k agentovi, freespace assumption — **správně**.
* **MAPF**: vrcholový vs. hranový/swap konflikt, sum-of-costs vs. makespan, NP-těžkost optima;
  prioritizované plánování/Cooperative A\* s rezervační tabulkou je neúplné (příklad koridoru
  s výklenkem); CBS nízká úroveň = A\* v prostoru–čase s omezeními, vysoká = strom omezení
  s binárním větvením, optimální a úplný — **správně**. ECBS/SIPP/LNS jako suboptimální varianty
  **existují a jsou správně zařazeny** (v plném textu nejsou — rozšíření, ne rozpor).
* **Ontologie**: Gruber, tranzitivní *is-a*, „ontologie + fakta = znalostní báze“, dělení
  aplikační/doménové/horní; RDF trojice + SPARQL, RDFS (třídy, hierarchie, domain/range);
  OWL = DL = rozhodnutelný fragment FOL, OWA, T-Box/A-Box, profily Lite $\mathcal{SHIF}$,
  DL $\mathcal{SHOIN}$, Full nerozhodnutelný, OWL 2 $=\mathcal{SROIQ}$ + EL/QL/RL — **správně**.
  SUMO je legitimní příklad horní ontologie (plný text uvádí BFO/GFO/UFO — jiný, ale rovněž
  správný příklad).
* **Epistemická logika**: $K_i\varphi$ + sémantika možných světů; znalost = S5 (axiom T),
  přesvědčení = KD45 (T nahrazeno D, 4/5 introspekce); $C_G\varphi$ nevznikne nespolehlivou
  komunikací (koordinovaný útok / dva generálové) — **správně a přesně**.
* **Řečové akty**: Austin, lokuce/ilokuce/perlokuce; Searlovy **podmínky zdařilosti vyjmenované
  všech pět** (normální vstup/výstup, propoziční obsah, přípravné, upřímnost, esenciální — plný
  text má jen tři, shrnutí je zde **přesnější než zdroj**) a pět kategorií
  (asertiva/direktiva/komisiva/expresiva/deklarace) — **správně**.
* **Inform** Cohen–Perrault: pre $S$ věří $\varphi$, efekt „$H$ věří, že $S$ věří $\varphi$“
  s explicitním „nikoli že $H$ uvěří $\varphi$“ — **správně** (to je nejčastěji zkoušená pointa
  celé kapitoly).
* **FIPA-ACL**: pole zprávy (bez nesprávného počtu), **22 performativ** (souhlasí se SC00037J),
  všechna vyjmenovaná performativa jsou platná, FP/RE v jazyce SL, příjemce není povinen RE
  splnit, neverifikovatelnost jako hlavní slabina — **správně**.
* **Protokoly**: FIPA-Request (request → agree/refuse → inform/failure), FIPA-Query,
  Contract Net + iterovaný (cfp → propose/refuse → accept/reject → inform), Subscribe,
  Brokering/Recruiting, English/Dutch — **správně**; `protocol` a `conversation-id` také.
* **Teorie her**: NE jako profil vzájemně nejlepších odpovědí; $m^n$ profilů; Nashova věta
  (konečná hra ⇒ NE ve smíšených); PPAD-úplnost; Paretova optimalita; $\mathit{sw}=\sum u_i$;
  max sw ⇒ Pareto-optimální, obráceně ne; recept na smíšené NE („protihráč indiferentní“);
  vězňovo dilema $T>R>P>S$, $D$ dominantní, $(D,D)$ jediné NE i jediné ne-Pareto-optimální pole;
  stín budoucnosti a zpětná indukce při známém konečném počtu kol; Axelrodova pětice
  **rozdělená správně** na *non-envious* a *clarity*; matching pennies má skutečně jen smíšené NE
  — **správně**.
* **Sociální volba**: plurality/IRV/sekvenční/Borda/Slater, Condorcetův paradox,
  kritéria, Arrow (Pareto + IIA nad 3+ ⇒ diktatura), Gibbard–Satterthwaite — **správně**.
* **Aukce**: dominantní strategie u anglické a Vickreyovy, **neexistence** u holandské a FPSB;
  ekvivalence anglická↔Vickrey a holandská↔FPSB; věta o ekvivalenci výnosů a její tři typické
  porušení; efektivita aukce; WDP NP-těžký; VCG = alokace maximalizující sw + platba rovná
  externalitě; princip odhalení; Zeuthen (ustupuje ten, kdo riskuje méně) — **správně**.
* **RL**: $\mathit{MDP}=\langle S,A,T,R,\gamma\rangle$, Markovská vlastnost, $G_t$,
  $V^\pi/Q^\pi$, Bellmanova rovnice optimality, value iteration jako kontrakce, policy iteration
  v konečně mnoha krocích; Q-learning (off-policy, $\max_{a'}$) vs. SARSA (on-policy, cliff
  walking a cesta dál od útesu — směr je **správný**); REINFORCE
  $\nabla_\theta J=\mathbb{E}[\nabla_\theta\ln\pi_\theta(a|s)G_t]$; actor-critic s výhodou
  $A=Q-V$; DQN (replay buffer, target network); Markovská hra; **Minimax-Q řeší LP** v každé
  aktualizaci; nestacionarita, exponenciální sdružený prostor, credit assignment; CTDE
  (MADDPG, QMIX) — **správně**.
* **Metodologie a prostředí**: Gaia (uzavřené kooperativní systémy, statická organizace;
  permissions / responsibilities s liveness ($\cdot$, $|$, $\omega$) a safety / activities /
  protocols; model interakcí; návrh = agenti + služby + známosti); Prometheus (BDI, PDT);
  Tropos (i\*/Yu, softgoals, jediný pokrývá rané požadavky); FIPA od 1996, dnes IEEE;
  AMS bílé stránky + AID + životní cyklus, DF žluté stránky, MTS/ACC; JADE (agent = vlákno,
  kooperativní plánování chování, `action` nesmí blokovat — **přesně správně**, to je oblíbená
  doplňující otázka); Jason/AgentSpeak (`spouštěč : kontext <- tělo`, cíle `!`/`?`);
  NetLogo (turtles/patches/links, Wolf–Sheep, Ants); SPADE (Python, XMPP);
  JaCaMo = Jason + CArtAgO + Moise; Mesa/MASON/GAMA — **správně**.
* **Křížové odkazy mezi stranami** („otázka 5“ u DisCSP, „otázka 6“ u RL, „otázka 2“ u
  means-ends reasoning) i **čísla stran v rozcestníku** (str. 2–8) — **souhlasí**.
* **Cesty k souborům**: `01-multiagentni-systemy.pdf` i `ENG/01-multiagent-systems.pdf`
  v repozitáři **existují**.

---

## A. KRITICKÉ

### K1. Cohen–Perraultův `Request` — chybný předpoklad a o modální vrstvu ochuzený efekt

**Kde:** str. 5 (Otázka 4), oddíl „Cohen & Perrault“, ř. 380–381 zdroje shrnutí.

**Co je špatně:** Shrnutí uvádí

> *Request*$(S,H,A)$: pre --- $S$ věří, že $H$ může $A$ vykonat a~že $A$ ještě nevykonal;
> efekt --- $H$ **ví**, že $S$ chce $A$.

Dvě chyby v jedné větě:

1. **Předpoklad „že $A$ ještě nevykonal“ v Cohen–Perraultově `Request` není.** Plný text
   (ř. 1736–1747) má korektně dvojici *cando* předpokladů
   $(S\ \mathrm{believe}\ (H\ \mathrm{cando}\ A)) \wedge (S\ \mathrm{believe}\ (H\ \mathrm{believe}\ (H\ \mathrm{cando}\ A)))$
   — tedy druhý konjunkt je „$S$ věří, že **$H$ si o sobě myslí**, že $A$ umí“, nikoli nic
   o (ne)vykonání. Shrnutí zde propašovalo cizí podmínku: „nebylo by to provedeno i bez
   požádání“ je Searlova **přípravná podmínka** (plný text ř. 1701–1702) a
   $\neg B_i I_j\mathrm{Done}(\alpha)$ je **FP FIPA-ACL** `request` (ř. 1856–1857). Student, který
   se to naučí takto, splete tři různé formalismy do jednoho.
2. **Efekt je „$H$ **věří**, že $S$ **věří**, že $S$ chce $A$“**, tj.
   $(H\ \mathrm{believe}\ (S\ \mathrm{believe}\ (S\ \mathrm{want}\ A)))$ — dvě vrstvy víry.
   Shrnutí píše „$H$ **ví**, že $S$ chce $A$“: (a) zamění *belief* za *knowledge* (a znalost podle
   S5 implikuje pravdivost — viz vlastní oddíl „Epistemická logika“ o dvě odrážky výš!),
   (b) zahodí jednu modální vrstvu. Přitom **tatáž věta** o řádek dál u `Inform` správně trvá na
   „$H$ věří, že $S$ věří $\varphi$ (nikoli že $H$ uvěří $\varphi$!)“. Zkoušející, který se ptá
   „a jaký je tedy efekt Requestu?“, dostane odpověď, která popírá celý smysl předchozí pointy.

**Správně:** pre --- $S$ věří, že $H$ může $A$ vykonat, a že si to $H$ myslí i sám o sobě;
$S$ chce, aby $A$ bylo vykonáno. Efekt --- $H$ *věří*, že $S$ *věří*, že $S$ chce $A$.

**Návrh opravy** (str. 5 má ≈ 22 % volného místa, škrtat není třeba):

```tex
\emph{Request}$(S,H,A)$: pre --- $S$ věří, že $H$ může $A$ vykonat, a~že si to $H$ myslí
i~sám o~sobě; $S$ chce, aby se $A$ vykonalo. Efekt --- \emph{$H$ věří, že $S$ věří,
že $S$ chce $A$} --- opět jen víra o~víře, žádný závazek.
\emph{Inform}$(S,H,\varphi)$: pre --- $S$ věří $\varphi$;
efekt --- \emph{$H$ věří, že $S$ věří $\varphi$} (nikoli že $H$ uvěří $\varphi$!).
```

### K2. „Stejná vyjadřovací síla“ přiřčena i čistě reaktivnímu agentovi

**Kde:** str. 2 (Otázka 1), oddíl „Dva speciální případy“, ř. 150–151 zdroje shrnutí.

**Co je špatně:**

> \tm{Čistě reaktivní agent} $Ag : E \to A$ --- \dots (striktně slabší).
> \tm{Agent s~vnitřním stavem}: \dots
> **Oba** jsou převeditelné na standardního agenta $R^E\to A$ (**stejná vyjadřovací síla**).

Závorka „stejná vyjadřovací síla“ platí **jen pro agenta s vnitřním stavem**. U čistě reaktivního
agenta je převod jednosměrný: plný text (ř. 329–330) explicitně říká „ke každému čistě reaktivnímu
agentovi existuje funkčně ekvivalentní standardní agent; **opačně to neplatí**“ — proto ta poznámka
„(striktně slabší)“ o dva řádky výš. Věta si tedy odporuje sama se sebou i se zdrojem a v této
podobě tvrdí faktickou nepravdu (že $E\to A$ a $R^E\to A$ mají stejnou vyjadřovací sílu).

**Správně:** oba jsou *podmnožinou* standardních agentů; vnitřní stav vyjadřovací sílu
**nezvyšuje** (přidává jen efektivitu a přehlednost implementace), zatímco čistě reaktivní agent
je **striktně slabší** — obrácený převod neexistuje.

**Návrh opravy** (str. 2 má ≈ 20 % volného místa; délkově neutrální):

```tex
Oba jsou zvláštní případy standardního agenta $R^E\to A$: vnitřní stav vyjadřovací sílu
\emph{nezvyšuje} (jen efektivitu), kdežto obrácený převod na čistě reaktivního agenta
obecně \emph{neexistuje} --- ten je striktně slabší.
```

(pak lze z první odrážky vypustit duplicitní „(striktně slabší)“, čímž se text ještě zkrátí)

---

## B. DŮLEŽITÉ

### D1. Směr inhibice v subsumpci — rozpor s plným textem i s Wooldridgem

**Kde:** str. 3 (Otázka 2), oddíl „Symbolické reaktivní plánování: subsumpce“, ř. 235–236.

**Co je špatně:** Shrnutí:

> uspořádaných do \tm{pevné priority}: **vyšší vrstva potlačuje** (*subsumuje*) **nižší**.

Plný text téhož repozitáře na to má **explicitní varování** (ř. 979–984):

> Pozor na směr --- u~Wooldridge i~na přednášce znamená $b_1 \prec b_2$, že **$b_1$ inhibuje
> $b_2$**, tedy $b_1$ je *níže* v~subsumpční hierarchii a~má *přednost*.

Wooldridge (2. vyd., §5.1) skutečně definuje „$b_1\prec b_2$ means that $b_1$ will inhibit $b_2$:
$b_1$ is lower in the subsumption hierarchy and will hence get priority over $b_2$“, a slidy tuto
notaci používají ($\mathrm{R1}\prec\mathrm{R6}\prec\dots$, kde R1 = „vyhni se překážce“ je vrstva
nejnižší a zároveň nejprioritnější). Shrnutí varování zahodilo a nechalo jen tu formulaci, která
vede k opačnému čtení: podle ní by v příkladu průzkumníka Marsu měla „náhodná chůze“ potlačovat
„vyhni se překážce“.

*Nuance, kterou je fér přiznat:* Brooksův původní článek popisuje, že „higher level layers subsume
the roles of lower levels“ a mohou potlačit vstupy / inhibovat výstupy nižších vrstev, takže
formulace shrnutí má v literatuře oporu. **Jistý je ale rozpor s plným textem a s notací
přednášky**, a právě podle té bude zkoušející číst zápis $\prec$.

**Správně:** relace inhibice $b_1\prec b_2$ = „$b_1$ potlačuje $b_2$“; $b_1$ je *níže*
v hierarchii a má *přednost*. Bezpečnostní chování (vyhýbání překážkám) je nejnižší a nejprioritnější.

**Návrh opravy** (str. 3 má ≈ 20 % volného místa):

```tex
Množina jednoduchých \tm{chování} \emph{situace $\to$ akce} (symbolická pravidla, ale bez
dedukce), běžících \emph{paralelně}, uspořádaných \tm{pevnou prioritou}: relace inhibice
$b_1\prec b_2$ znamená \uv{$b_1$ potlačuje $b_2$}, tedy $b_1$ je \emph{níže} v~hierarchii
a~má \emph{přednost} (nejnižší, nejprioritnější vrstva je bezpečnostní --- vyhýbání překážkám).
```

### D2. Dominance jen v jedné (nerozlišené) verzi — a přesto „Vickrey má dominantní strategii“

**Kde:** str. 6 (Otázka 5), oddíly „Sobecký agent a hra v normální formě“ (ř. 455–456)
a „Aukce jako alokace zdrojů“ (ř. 485–488).

**Co je špatně:** Shrnutí definuje dominanci jediným, navíc vágním způsobem:

> \tm{dominance} (strategie je **lepší** při každé volbě ostatních)

„lepší“ nerozlišuje **silnou** (striktně lepší proti všem) a **slabou** dominanci (nikdy horší,
aspoň jednou striktně lepší). Plný text tento rozdíl **má** (ř. 2168–2183, doplněn po předchozí
recenzi) a hned dodává, proč není akademický:

* pravdomluvnost ve Vickreyově aukci je jen **slabě** dominantní (plný text ř. 2467:
  „Tedy $b = v$ je (slabě) dominantní strategie“) — shrnutí přitom na téže straně tvrdí bez
  přívlastku, že anglická a Vickreyova „mají \tm{dominantní strategii}“;
* IESDS se **slabě** dominovanými strategiemi **závisí na pořadí** odstraňování a lze přijít
  o ekvilibria — shrnutí uvádí „iterované odstraňování dominovaných“ bez této výhrady.

Kondenzát tím **regresoval** proti plné verzi. Otázka „je pravdomluvnost ve Vickreyovi silně, nebo
slabě dominantní?“ je klasická past (odpověď: slabě — při $b>p$ i $b'>p$ je zisk týž).

**Správně:** rozlišit silnou a slabou dominanci; u Vickreyho uvést „(slabě) dominantní“;
u IESDS uvést závislost na pořadí při slabé dominanci.

**Návrh opravy.** Str. 6 je zaplněná téměř na 100 %, takže **s kompenzací**:

*Nahradit* (ř. 455–456):

```tex
\tm{dominance} \emph{silná} (striktně lepší proti všem volbám ostatních) vs.\ \emph{slabá}
(nikdy horší, aspoň jednou lepší); \tm{IESDS} --- u~slabé záleží na pořadí odstraňování.
```

*Vložit* jediné slovo na ř. 486: `mají \tm{(slabě) dominantní strategii}`.

*Kompenzační škrty na téže straně* (dohromady ≈ 2 řádky, tedy více, než přidání zabere):

* ř. 443: vypustit `(Užito i~v~IDA.)` — vazba na IDA je už na str. 3;
* ř. 492: vypustit vsuvku `(porovnat nadhodnocení a~podhodnocení oproti pravdě)` — postup
  důkazu student stejně musí umět z plného textu, samotné „umět důkaz“ stačí;
* případně ř. 421 `Koordinace je prostředek, koherence cíl.` (mnemotechnika, ne fakt).

### D3. Chybí agentově orientované programování (Shoham, AGENT-0, Concurrent MetateM)

**Kde:** str. 8 (Otázka 7), oddíl „Jazyky a prostředí“.

**Co je špatně:** Věta okruhu explicitně jmenuje **„jazyky … multiagentních systémů“**. Shrnutí
uvádí jen *implementační platformy* (JADE, Jason, NetLogo, SPADE, JaCaMo, Mesa…), ale vynechává
**paradigma**, ze kterého agentní jazyky vzešly a které plný text má (ř. 2974–2980):
**agentově orientované programování** (Shoham 1993) — stav programu tvoří *mentální kategorie*
(přesvědčení, závazky, schopnosti), program je množina *pravidel závazků*; první jazyk
**AGENT-0**; jinou cestou **Concurrent MetateM**, kde je agent *přímo spustitelná specifikace*
v temporální logice. Bez toho zůstává na straně jen výčet nástrojů bez pojmového rámce a chybí
i pěkná vazba zpět na deduktivní agenty z otázky 2.

**Správně:** doplnit jednu odrážku o AOP.

**Návrh opravy** (str. 8 má ≈ 22 % volného místa, škrtat není třeba — vložit jako **první**
odrážku oddílu „Jazyky a prostředí“):

```tex
\item \tm{AOP} (\en{agent-oriented programming}, Shoham 1993) --- stav programu tvoří
  \emph{mentální kategorie} (přesvědčení, závazky, schopnosti), program je množina
  \emph{pravidel závazků}; první jazyk \tm{AGENT-0}. \tm{Concurrent MetateM}: agent je přímo
  \emph{spustitelná specifikace} v~temporální logice. Oba navazují na deduktivního agenta
  (otázka~2); prakticky zvítězila linie AgentSpeak/Jason.
```

### D4. `inform`: efekt podle Cohen–Perraulta vs. RE podle FIPA — student je splete

**Kde:** str. 1 (rozcestník, „Drobnosti, na které se často ptají“, ř. 101) + str. 5, oddíl
„KQML a FIPA-ACL“ (ř. 395–397).

**Co je špatně:** Rozcestník vypichuje jako klíčovou drobnost:

> Proč efektem `inform` *není*, že příjemce uvěří (jen že věří, že mluvčí věří).

To je pravda **o Cohen–Perraultově** `Inform`. U **FIPA-ACL** je ale
$\mathrm{RE}(\mathrm{inform}(j,\varphi)) = B_j\varphi$, tedy **právě** „$j$ uvěří $\varphi$“ —
jen s tím, že příjemce RE *není povinen* naplnit. Plný text obojí uvádí vedle sebe a rozdíl je
z něj zřejmý (ř. 1846–1854 vs. 1751–1753). Shrnutí uvádí FP/RE **bez hodnot** a rozcestník staví
generickou tezi „efektem inform není, že příjemce uvěří“. Student pak na otázku „jaký je racionální
efekt FIPA `inform`?“ odpoví „že $H$ věří, že $S$ věří $\varphi$“ — **špatně**. Přesně typ
zavádějící zkratky vzniklé kondenzací.

**Správně:** Cohen–Perrault: efekt $=B_H B_S\varphi$. FIPA-ACL: $\mathrm{RE}=B_j\varphi$,
$\mathrm{FP}=B_i\varphi\wedge\neg B_i(\mathit{Bif}_j\varphi\vee \mathit{Uif}_j\varphi)$;
rozdíl není v obsahu RE, ale v tom, že RE **nezavazuje** příjemce.

**Návrh opravy** (str. 5 má ≈ 22 % volného místa). Za „příjemce \emph{není povinen} RE splnit“
(ř. 397) doplnit:

```tex
Např.\ \texttt{inform}: FP $=B_i\varphi\wedge\neg B_i(\mathit{Bif}_j\varphi\vee
\mathit{Uif}_j\varphi)$, RE $=B_j\varphi$ --- pozor, u~FIPA RE \emph{je} \uv{$j$ uvěří
$\varphi$}, jen není vynutitelné; Cohen--Perraultův \emph{efekt} je slabší ($B_H B_S\varphi$).
```

a na str. 1 (ř. 101) zpřesnit odrážku:

```tex
\item Proč efektem \texttt{inform} \emph{u~Cohen--Perraulta} \emph{není}, že příjemce uvěří
  (jen že věří, že mluvčí věří) --- a~čím se to liší od FIPA \en{rational effect}.
```

---

## C. DROBNÉ

### S1. Nadpis strany 5 není doslovný
**Kde:** str. 5, `\qpage{4}{...}`.
**Co je špatně:** `Komunikace a~znalosti v~MAS, ontologie, ...` — oficiální znění má
„Komunikace a znalosti **v multiagentních systémech**, ontologie, …“. Rozcestník na str. 1
(ř. 74) přitom cituje správně, takže dokument si odporuje sám se sebou. Ostatních šest nadpisů je
doslovných. (Drobnost navrch: oficiální věty končí tečkou, nadpisy stran ji nemají — v rozcestníku
tečky jsou.)
**Správně:** `\qpage{4}{Komunikace a~znalosti v~multiagentních systémech, ontologie, řečové akty, FIPA-ACL, protokoly}`
**Návrh opravy:** nadpis se do dvou řádků `qbox` vejde (str. 7 to dělá se stejně dlouhou větou);
pokud by přetékal, zkrátit lze `\qpage` sazbou na `\normalsize` místo `\large`.

### S2. Chybějící nezlomitelné mezery v mezititulcích `\hh{}`
**Kde:** 16 nadpisů, ř. 115, 260, 278, 327, 384, 418, 423, 429, 440, 445, 451 (dvakrát), 458, 512, 595, 605, 616.
**Co je špatně:** proti konvenci repozitáře (`CLAUDE.md`: „nezlomitelná mezera po jednopísmenných
předložkách“) je v tělech odstavců `~` použita důsledně, ale v `\hh{}` nadpisech systematicky chybí:
`Agent a MAS`, `IDA a globální pracovní prostor`, `Formulace a zařazení`,
`Souvislosti s ostatními otázkami`, `KQML a FIPA-ACL`, `Koherence a koordinace`,
`Sdílení úloh a výsledků`, `Systémy s tabulí (BBS)`, `DisCSP a DCOP`,
`Sobecký agent a hra v normální formě`, `Nash a Pareto`, `Proč a jak se agenti učí`,
`Prometheus a Tropos`, `Standard FIPA a architektura platformy`, `Jazyky a prostředí`.
Navíc `\hh{CDPS vs. PPS vs. MAS}` (ř. 423) má `vs.` bez `\ `, takže TeX sází mezivětnou mezeru
(v ostatních 8 výskytech je správně `vs.\`).
**Správně / Návrh opravy:** doplnit `~` (`Agent a~MAS`, `Systémy s~tabulí (BBS)`,
`Sobecký agent a~hra v~normální formě`, …) a `\hh{CDPS vs.\ PPS vs.\ MAS}`. Jednorázový
`sed` per nadpis; nadpisy se nelámou, takže riziko je nulové, ale konzistence se hlídat má.

### S3. Překlep „čísti“
**Kde:** str. 8, oddíl „Gaia“, ř. 588.
**Co je špatně:** `\en{permissions} (co role smí čísti/měnit)` — archaický/nesprávný infinitiv
(navíc podle „Pastí“ v `CLAUDE.md` je i tvar `čísti/měnit` kandidát na zlom před lomítkem).
**Správně:** „co role smí číst a měnit“.
**Návrh opravy:** `\en{permissions} (co role smí číst a~měnit)`.

### S4. Definice konzistence bez podmínky $h(\text{cíl})=0$
**Kde:** str. 4, oddíl „A\*“, ř. 291–293.
**Co je špatně:** `\tm{Konzistence} ...: $h(n)\le w(n,m)+h(m)$ ... Konzistence $\Rightarrow$ přípustnost.`
Bez podmínky $h(g_{\mathrm{cíl}})=0$ implikace **neplatí** (konstanta $h\equiv c>0$ trojúhelníkovou
nerovnost splňuje, ale přípustná není). Plný text ji v definici má (ř. 1364).
**Správně:** $h(n)\le w(n,m)+h(m)$ **a** $h(\text{cíl})=0$.
**Návrh opravy** (str. 4 má ≈ 40 % volného místa):
`$h(n)\le w(n,m)+h(m)$ a~$h(\text{cíl})=0$ $\Rightarrow$ \dots`

### S5. Ohodnocení hran $\mathbb{R}^+$ místo $\mathbb{R}_0^+$
**Kde:** str. 4, oddíl „Formulace a zařazení“, ř. 279–280.
**Co je špatně:** `$w:E\to\mathbb{R}^+$`; plný text má `$w : E \to \mathbb{R}_0^+$` (nezáporné).
Pro A\* je podstatná právě nezápornost, nulové hrany jsou přípustné.
**Návrh opravy:** `$w:E\to\mathbb{R}_0^+$`.

### S6. „$(C,C)$ maximalizuje sw“ bez podmínky $2R>T+S$
**Kde:** str. 6, oddíl „Klasické hry“, ř. 468–469.
**Co je špatně:** Shrnutí uvádí jen `$T>R>P>S$` a pak `$(C,C)$ maximalizuje sw`. Z $T>R>P>S$
to **neplyne**: pro $T=5,R=2,P=1,S=0$ je $sw(C,D)=5>4=sw(C,C)$. Potřebná je druhá podmínka
$2R>T+S$, kterou plný text má (ř. 2245: „a~často navíc $2R > T + S$“). Naopak „$(D,D)$ jediné
ne-Pareto-optimální pole“ z $T>R>P>S$ **plyne** a je uvedeno správně.
**Návrh opravy** (délkově neutrální): `\tm{Vězňovo dilema} $T>R>P>S$ (a~$2R>T{+}S$): ...`

### S7. „Reálná prostředí jsou vždy v té těžší variantě“
**Kde:** str. 2, oddíl „Vlastnosti prostředí (4 dichotomie)“, ř. 134–135.
**Co je špatně:** `vždy` je nepravda a snadno napadnutelná — šachy, Sokoban či svět kostek jsou
diskrétní, deterministické, statické a plně pozorovatelné. Plný text (ř. 239) je opatrný:
„**většina** zajímavých prostředí (reálný svět, internet)“.
**Návrh opravy:** `Většina zajímavých prostředí (reálný svět, internet) je v~té těžší variantě;`

### S8. Rozcestník oslabuje pointu o $(D,D)$ na „ekvilibrium“
**Kde:** str. 1, „Drobnosti“, ř. 102.
**Co je špatně:** `Proč je $(D,D)$ jediné \emph{ne}-Pareto-optimální ekvilibrium vězňova dilematu.`
Protože $(D,D)$ je **jediné** ekvilibrium vůbec, je tvrzení triviálně pravdivé a pointa se ztrácí.
Plný text (ř. 2251) i str. 6 shrnutí říkají silnější a zajímavé: $(D,D)$ je jediné
ne-Pareto-optimální **pole hry**.
**Návrh opravy:** `Proč je $(D,D)$ jediné \emph{ne}-Pareto-optimální \emph{pole} vězňova dilematu.`

### S9. Výčet klasických her se rozešel s plným textem
**Kde:** str. 6, oddíl „Klasické hry“, ř. 472–473.
**Co je špatně:** `Dále \emph{stag hunt}, \emph{chicken}, \emph{matching pennies} (jen smíšené NE).`
Ověřeno grepem: **stag hunt ani matching pennies v plném textu nejsou** (ten má vězňovo dilema,
**koordinační hru / Battle of the Sexes** a Chicken). Zmizela přitom právě koordinační hra, na
které plný text jako na **jediné** předvádí výpočet smíšeného NE ($q=2-2q\Rightarrow q=2/3$)
a kterou v „Shrnutí ke zkoušce“ výslovně žádá umět spočítat. Shrnutí tak jmenuje hry, které
student v plné verzi nenajde, a vynechává tu, kterou má umět propočítat.
**Návrh opravy** (délkově neutrální):
`Dále \emph{koordinační hra} / \en{Battle of the Sexes} (smíšené NE $q=2/3$), \emph{chicken} ($p=1/2$), \emph{matching pennies} (jen smíšené NE).`

### S10. JADE: `SimpleBehaviour` jako příklad
**Kde:** str. 8, `\tm{JADE}`, ř. 618–619.
**Co je špatně:** `\texttt{Behaviour} (\texttt{Simple}/\texttt{Cyclic}/\texttt{FSM})`.
`SimpleBehaviour` existuje, ale je to **abstraktní báze**; kanonickými příklady, které uvádí i plný
text (ř. 2990–2991), jsou `OneShotBehaviour`, `CyclicBehaviour`, `TickerBehaviour`,
`SequentialBehaviour`, `FSMBehaviour`.
**Návrh opravy:** `\texttt{Behaviour} (\texttt{OneShot}/\texttt{Cyclic}/\texttt{Ticker}/\texttt{FSM})`.

### S11. Nash-Q: „NE podhry“ + chybí výhrada o konvergenci
**Kde:** str. 7, oddíl „Multiagentní RL“, ř. 559.
**Co je špatně:** `\tm{Nash-Q} (obecný součet, potřebuje NE podhry)`. Nash-Q počítá NE
**jednorázové maticové hry v daném stavu** (*stage game* $Q(s',\cdot,\cdot)$) — „podhra“ je pojem
z her v extenzivní formě a mate. Navíc plný text (ř. 2862–2863) přidává podstatnou výhradu
„ale konverguje jen za silných předpokladů“, kterou shrnutí zahodilo.
**Návrh opravy:** `\tm{Nash-Q} (obecný součet: NE maticové hry $Q(s',\cdot,\cdot)$ v~daném stavu; konverguje jen za silných předpokladů)` — str. 7 má ≈ 25 % volného místa.

### S12. „Bold agent nepřehodnocuje“
**Kde:** str. 3, oddíl „Odhodlání“, ř. 219–220.
**Co je špatně:** Odvážný agent přehodnocuje záměry — jen **až po dokončení celého plánu**
(plný text ř. 831–832). „Nepřehodnocuje“ je nepřesné a splývá se slepým odhodláním, které je
o dva řádky výš jiný pojem.
**Návrh opravy:** `\tm{Bold} agent přehodnocuje až po dokončení plánu, \tm{cautious} po každém kroku;`

### S13. Škála formalizace ontologií se rozešla s plným textem
**Kde:** str. 5, oddíl „Ontologie“, ř. 346–347.
**Co je špatně:** `řízený slovník $\to$ taxonomie $\to$ tezaurus $\to$ rámce $\to$ logická omezení`.
Plný text (ř. 1521–1526) má jinou posloupnost: slovník → **glosář** → tezaurus →
**neformální hierarchie** → **formální *is-a* hierarchie** → **třídy s vlastnostmi** →
**omezení hodnot** → libovolná logická omezení. „Rámce“ jsou v plném textu samostatný
*jazyk* (Minsky), ne stupeň škály. Věcně to obhajitelné je, ale kondenzát se nemá se zdrojem
rozcházet ve výčtu, který se u tabule odříkává.
**Návrh opravy** (délkově neutrální):
`řízený slovník $\to$ glosář $\to$ tezaurus $\to$ neformální hierarchie $\to$ formální \emph{is-a} $\to$ třídy s~vlastnostmi $\to$ logická omezení.`

### S14. „Ekvivalence“ bez rozlišení jejího druhu
**Kde:** str. 6, oddíl „Aukce jako alokace zdrojů“, ř. 489.
**Co je špatně:** `Ekvivalence: anglická $\leftrightarrow$ Vickrey, holandská $\leftrightarrow$ FPSB.`
Nejsou to ekvivalence stejného druhu: holandská–FPSB je **strategická ekvivalence** (týž
rozhodovací problém), anglická–Vickrey platí **za soukromých hodnot** (výsledková ekvivalence,
padá při společných hodnotách, kde anglická odhaluje informaci). Plný text rozdíl má
(ř. 2447 vs. 2452) a shrnutí ho o tři řádky dál samo potřebuje (prokletí vítěze).
**Návrh opravy** (délkově neutrální):
`Ekvivalence: holandská $\leftrightarrow$ FPSB (\emph{strategicky}), anglická $\leftrightarrow$ Vickrey (\emph{za soukromých hodnot}).`

### S15. Dlouhé názvy souborů v `\texttt{}` místo `\path{}`
**Kde:** str. 1, ř. 66.
**Co je špatně:** `\texttt{01-multiagentni-systemy.pdf}` a `\texttt{ENG/01-multiagent-systems.pdf}`
— `CLAUDE.md` výslovně říká: „Dlouhé názvy souborů sázet `\path{…}`, ne `\texttt{…}` — `\texttt`
se nezlomí a přeteče sloupec.“ Dnes to projde (text je přes celou šířku, log je bez overfull boxu),
ale je to nastražená past pro každou budoucí editaci prvního odstavce.
**Návrh opravy:** obalit oba názvy `\path{...}` (balíček `url` už je přes `hyperref` k dispozici).

### S16. „Nekonstruktivní definice (optimální agent, Nashova věta, Arrowova věta)“
**Kde:** str. 1, „Čtyři osy“, ř. 92–93 (týž problém má i plný text, ř. 3060).
**Co je špatně:** Nashova a Arrowova věta nejsou *definice*, a Arrowova věta není
*nekonstruktivní* — je to **negativní/nemožnostní** výsledek (a její důkazy jsou konstruktivní).
**Návrh opravy:** `nekonstruktivní a~nemožnostní výsledky (optimální agent, Nashova věta, Arrowova věta) versus použitelné algoritmy`

### S17. „Problém transdukce (jak dostat svět do symbolů **včas**)“
**Kde:** str. 3, oddíl „Deduktivní agent“, ř. 200–201.
**Co je špatně:** Transdukce je o **převodu** světa do symbolické reprezentace (vidění, NLP);
časová tíseň („než se výpočet dokončí, svět se změní“) je obsahem **vypočitatelné racionality**,
kterou tatáž věta zmiňuje hned za tím. Slovo „včas“ dvě různé slabiny slévá.
**Návrh opravy:** `\tm{problém transdukce} (jak převést svět do symbolů) a~\tm{vypočitatelná racionalita} (než se důkaz dokončí, svět se změní).`

---

## D. Poznámky bez nálezu (pro úplnost, nic neopravovat)

* **Rozsah drží s rezervou.** Jediná strana bez rezervy je str. 6 (Otázka 5) — nejobsáhlejší věta
  okruhu. Str. 4 (hledání cesty) má naopak ≈ 40 % volné plochy; kdyby vznikla potřeba text kdekoli
  zkrátit, tady je naopak místo, kam se ještě vejde např. rozdíl „rozhodnout **řešitelnost** MAPF
  je polynomiální (Kornhauser a kol. 1984), zatímco najít **optimum** je NP-těžké“ nebo jedna věta
  o spojitých plánovačích (PRM/RRT). Do plného textu to předchozí recenze doporučila (D7) a zatím
  tam není — do shrnutí to tedy patřit nemusí.
* Str. 4 poznámka „*Ve slidech NAIL106 tato kapitola není — okruh ji ale jmenuje.*“ je v kondenzátu
  na místě a odpovídá značce `\mimoq{celá kapitola}` v plné verzi. Analogická poznámka u otázky 6
  (učení agentů, ve slidech také není) na str. 7 chybí — pro symetrii by se hodila, ale prostor
  by si vzala; ponechávám jako věc vkusu, ne nález.
* Doplňky, které v plné verzi nejsou a jsou přitom **věcně správné**: *bounded optimality* (str. 2),
  všech pět Searlových podmínek zdařilosti (str. 5), SUMO (str. 5), ECBS/SIPP/LNS (str. 4),
  `DummyAgent`, `Mesa`, PDT (str. 8). Kondenzát je tedy místy přesnější než zdroj — to je v pořádku,
  jen pozor, aby se zpětně nerozešel s plnou verzí při jejích dalších úpravách.


---

## Zapracováno (12. 8. 2026)

Opraveno ve `01-multiagentni-systemy-shrnuti.tex`, PDF přeloženo znovu (8 stran, 0 overfull):

| nález | jak |
|---|---|
| K1 | Request má nyní předpoklad *S věří, že H umí A, a S věří, že H věří, že umí A* a efekt *H věří, že S věří, že S chce A* (podle tabulky v plném textu, ř. 1738–1747) |
| K2 | „stejná vyjadřovací síla“ → „obráceně to pro čistě reaktivního agenta neplatí“ |
| D1 | subsumpce: doplněna relace $\prec$ v notaci plného textu (ř. 980–983), přednost mají nižší vrstvy |
| D2 | Vickrey/anglická aukce: „slabě dominantní strategii“ |
| D3 | doplněna odrážka AOP (Shoham 1993), AGENT-0, Concurrent MetateM |
| D4 | doplněno RE `inform` $=B_j\varphi$ a kontrast s Cohen–Perraultovým efektem |
| S1 | nadpis str. 5 doslovně („v multiagentních systémech“) |
| S3 | „čísti/měnit“ → „číst a měnit“ |
| S4 | „konzistence $+$ $h(\text{cíl})=0$ $\Rightarrow$ přípustnost“ |
| S7 | „reálná prostředí jsou **typicky** v těžší variantě“ |
| S12 | „bold agent přehodnocuje teprve po dokončení plánu“ |
| S15 | dlouhé názvy souborů v `\path{}` |
| S2 | nezlomitelné mezery v 16 `\hh{}` nadpisech |

**Nezapracováno** (posouzeno jako sporné nebo pod rozlišovací schopnost jednostránkového
kondenzátu): S5, S6, S8, S9, S10, S11, S13, S14, S16, S17. Nálezy zůstávají v protokolu
jako podklad pro případnou další revizi.
