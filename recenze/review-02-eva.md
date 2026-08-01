# Kritická recenze: 02-prirodou-inspirovane-pocitani.tex

Rozsah: 3697 řádků TeXu, 55 stran PDF. Recenzent prošel celý dokument, přepočítal
všechny číselné příklady a porovnal obsah se slidy EVA I (`eva1.txt`) a EVA II
(`eva2.txt`) a se studentskými poznámkami.

## Souhrn

| kategorie | počet nálezů |
|---|---|
| KRITICKÉ (fakticky špatně) | 2 |
| DŮLEŽITÉ (chybí vůči okruhu / kurzu, nebo nepřesné) | 12 |
| DROBNÉ (styl, sazba, terminologie) | 9 |

**Co je naopak v pořádku a bylo ověřeno výpočtem:** ruletová selekce
(Goldbergův příklad 01101/11000/01000/10011, všechna $p_i$ i očekávané počty),
lineární škálování ($a=0{,}516$, $b=141{,}6$, podíl 49,2 % → 37,5 %),
číselný příklad k větě o schématech (všechny tři řádky tabulky včetně
$F(S)$, $o(S)$, $d(S)$, pravděpodobností přežití a $\mathbb{E}[C]$),
PMX / OX / CX **krok za krokem na obou potomcích** (přepočítáno nezávisle,
souhlasí i s výsledky ve slidech), seznamy sousedů pro ER (všech 9 měst),
průběh ER až k `145678239`, ordinální kódování TSP `112141311`,
sousednostní kódování `(248397156)`, DE krok (donor $(3{,}6;-2{,}6;-1{,}1)$,
$f(\vec u)=23{,}17$), PSO krok ($\vec v'=(-2{,}65;-0{,}95)$),
constriction $\chi = 0{,}7298$ pro $\varphi=4{,}1$, ACO pravidlo přechodu
($p=0{,}216/0{,}108/0{,}676$) i update feromonu (1,09), Metropolis
(0,135 / 0,018 / 0,67), crowding distance ($d_B = 1{,}05$, $d_C = 1{,}48$),
hypervolume (42 — ověřeno i integrací po pruzích), počet stavů Markovova
řetězce ($n=l=8 \Rightarrow N \approx 5{,}1\cdot10^{14}$, $|\mathbf Q| \approx
2{,}6\cdot 10^{29}$, tedy „řádově $10^{29}$" sedí), $\chi$, $\tau'$/$\tau$
u Schwefelovy samoadaptace, kovarianční matice $c_{ij}$, NEAT $\delta$.
**Sazba je čistá: log neobsahuje ani jeden overfull/underfull box, žádné
varování, žádné nerozřešené reference.**

---

## KRITICKÉ

### K1. SAT — reálná reprezentace má prohozenou konjunkci a disjunkci
**Kde:** kap. „Kombinatorické úlohy", odst. *SAT / Reprezentace*, druhá odrážka
(řádek ~3245).

**Co:** Text říká „konjunkce jako součin, disjunkce jako součet" při kódování
$x \mapsto (1-y)^2$, $\neg x \mapsto (1+y)^2$, pravda $=1$, nepravda $=-1$
a minimalizaci. To je matematicky obráceně (dokument zde věrně přebírá překlep
ze slidu `eva1.txt`, „Conjunction is \*, disjunction is +").

**Proč je to špatně:** členy jsou *penalty* — splněný literál dává 0.
Klauzule (disjunkce) je splněna, stačí-li jeden literál → penalta musí být
**součin** (nula, je-li aspoň jeden činitel nula). Formule (konjunkce klauzulí)
je splněna, jsou-li splněny všechny → **součet**. Kontrola na $(x_1 \vee x_2)$
s $y_1=1$, $y_2=-1$: součin $=0\cdot 4 = 0$ ✓; součet $=0+4=4 \ne 0$ ✗.

**Jak opravit:** prohodit a přidat jednořádkové zdůvodnění, aby si student
mohl pravidlo kdykoli odvodit sám.

### K2. Hillisovy řadicí sítě — nepravdivé tvrzení o překonání člověka
**Kde:** kap. „Koevoluce", odst. *Klasický příklad: Hillisovy řadicí sítě*
(řádek ~2023).

**Co:** „Hillis takto nalezl síť pro 16 prvků s 61 komparátory --- lepší než
tehdy nejlepší lidský návrh."

**Proč je to špatně:** Hillis (1990) našel síť s 61 komparátory; nejlepší známý
*lidský* návrh (Green, 1969) měl **60** komparátorů. Skutečný obsah výsledku je
srovnání koevoluce s obyčejným GA: bez parazitů týž algoritmus dosáhl jen 65
komparátorů. Tvrzení „lepší než člověk" je při zkoušce snadno napadnutelné.

**Jak opravit:** uvést 61 vs. 65 (bez koevoluce) vs. 60 (Green).

---

## DŮLEŽITÉ

### D1. EDA (algoritmy odhadu rozdělení) jsou jen jednou odrážkou
Kurz je uvádí na dvou místech (BBO zoo v EVA II, „linkage learning"), a okruh
explicitně zmiňuje *pravděpodobnostní modely jednoduchého GA* — EDA jsou
přirozený most od Voseho modelu k praxi. Dokument jim věnuje 4 řádky
(kap. `sec:vose`, „Další teoretické nástroje"). **Doplnit samostatný odstavec:**
obecné schéma (vzorkuj → vyber → přepočti model), PBIL (aktualizace vektoru
pravděpodobností $p \gets (1-\alpha)p + \alpha x_{\text{best}}$), UMDA
(marginály), cGA, MIMIC/BMDA (závislosti), BOA (Bayesovská síť) a vztah k CMA-ES.

### D2. Voseho model — chybí klíčová symetrie míchacího operátoru
Text říká jen „$r$ je invariantní vůči *posunu* XOR" a že stačí znát $r(i,j,0)$.
Neuvádí konkrétní vztah, který to umožňuje:
$r(i,j,k) = r(i\oplus k,\; j\oplus k,\; 0)$.
To je jádro celé Voseho konstrukce (mixing matrix + permutace $\sigma_k$).
Doplnit explicitně, včetně věty, jak se z toho $\mathcal M$ sestaví.

### D3. Voseho model — část $\mathcal F$ je odvozena příliš zkratkovitě
Krok „$\mathbb{E}[p(t+1)] = s(t)$, a~tedy $\mathbb{E}[s(t+1)] \propto \mathbf F s(t)$"
je pro čtenáře skok. Chybí i drobný konkrétní příklad (co je $\mathbf F$ a $s$
pro $l=2$), který by celý formalismus zpřístupnil. Doplnit dvě věty odvození
+ mini-příklad se čtyřmi řetězci.

### D4. Otevřená evoluce je nejtenčí pasáž vůči okruhu
Okruh jmenuje „otevřenou evoluci" jako samostatnou položku; dokument jí věnuje
jeden defbox + tři řádky výčtu systémů, zbytek podkapitoly je novelty search.
Doplnit: kritéria/hallmarky OEE (trvalý růst složitosti, nepřestávající produkce
novosti, evoluce evolvability, vznik nových tříd entit), proč se modely
„zasekávají", major transitions jako inspirace, a zmínit generativní
reprezentace, které kurz jmenuje (**L-systémy, celulární automaty,
morfogeneze**, ECHO, Polyworld) — ty v dokumentu zcela chybí.

### D5. Chybí interaktivní evoluce
Kurz na ni odkazuje přes Picbreeder/EndlessForms (EVA II, HyperNEAT). Dokument
je zmiňuje jen jako „ukázky estetického potenciálu CPPN", ale samotný pojem
*interaktivní evoluce* (člověk jako fitness funkce) nikde nedefinuje. Doplnit
krátký odstavec včetně omezení (únava uživatele, malé populace).

### D6. ES — chybí varianta s $2n$ strategickými parametry
Slide `eva1.txt` uvádí $k \in \{1,\ n,\ 2n,\ n(n{+}1)/2\}$; tabulka v dokumentu
má jen 1, $n$, $n(n{+}1)/2$. Doplnit řádek $2n$ (odchylky + hlavní úhly natočení,
tj. částečně korelované mutace).

### D7. Tabulka disruptivity křížení je vágní u dvoubodového křížení
Řádek „dvoubodové | mírně nižší pro krajní pozice" nedává vzorec. Přitom je
jednoduchý a při zkoušce se hodí: chápeme-li řetězec jako kruh o $m$ mezerách,
je pravděpodobnost rozbití schématu $2d(m-d)/\big(m(m-1)\big)$ — pro schéma
přes celý řetězec ($d=m-1$) klesne z 1 na $2/m$, což přesně vysvětluje
„odstranění okrajového biasu". Doplnit.

### D8. Bloat — jediná teorie vysvětlení
Dokument uvádí jen „hitchhiking / replication accuracy". Standardně se uvádějí
minimálně tři konkurenční teorie: *replication accuracy*, *removal bias*
a *crossover bias* (distribuce velikostí podstromů). Doplnit.

### D9. Lokální prohledávání — chybí Nelder–Mead (downhill simplex)
Slide EVA II jej v „BBO how-to zoo" vyjmenovává mezi lokálními heuristikami
vedle SA a hill climbingu; v dokumentu není. Doplnit jednu odrážku.

### D10. Paralelní modely EA jsou jen implicitní
Ostrovní model je zmíněn v kapitole o diverzitě, ale chybí systematické
rozlišení master–slave / ostrovní (hrubozrnný) / buněčný (jemnozrnný, mřížka)
model, které kurz naznačuje („island model of GA – usually sub-populations
on different machines", „individuals on a 2D (3D) mesh"). Doplnit krátký odstavec.

### D11. LCS — chybí celkový obrázek běhu systému a moderní varianty
Kapitola jde rovnou k ZCS/XCS. Chybí (a) explicitní popis architektury
Hollandova LCS jako smyčky *detektory → buffer zpráv → match set → efektory →
odměna → bucket brigade + GA* (slide „Bucket brigade algorithm"), (b) zmínka
o UCS (varianta XCS pro učení s učitelem) a o tom, že populace jako celek
**je** ten expertní systém. Doplnit.

### D12. Scatter search — chybí varianty aktualizace referenční množiny
Slide uvádí tři způsoby (inkrementálně / kompletní obnova / tvorba ve vnitřním
cyklu). Dokument popisuje jen obecně. Doplnit jednu větu.

---

## DROBNÉ

### N1. Překlepy
- ř. 979: `vícerruký` → `víceruký`
- ř. 1757: `náhradí` → `nahradí`
- ř. 2288: `jednoduší` → `jednodušší`

### N2. Nekonzistentní indexování v selekci
V turnajové selekci je $i=1$ **nejlepší** jedinec, o odstavec dál v pořadové
selekci je $i=1$ **nejhorší**. Obojí je vnitřně správně, ale čtenář si toho
nemusí všimnout. Doplnit explicitní poznámku k turnajovému vzorci.

### N3. „Relace dominance je částečné uspořádání (ireflexivní, tranzitivní)"
Ireflexivní + tranzitivní = **ostré (striktní)** částečné uspořádání;
„částečné uspořádání" se v češtině obvykle míní reflexivní. Upřesnit.

### N4. ER — počty sousedů se počítají před odebráním navštíveného města
V příkladu „kandidáti 9 (4 sousedi), 2 (3), 4 (3)" jsou počty včetně města 1,
které už je na cestě. Po korektním odebrání jsou počty 3, 2, 2 — pořadí i závěr
jsou stejné, ale postup je třeba zmínit, jinak si student zapamatuje chybný
algoritmus. Doplnit závorku.

### N5. XCS — nestandardní název konstanty
Vzorec přesnosti je psán $\kappa = \eta(\epsilon/\epsilon_0)^{-\nu}$; ve
standardní literatuře (Wilson, Butz–Wilson) je konstanta $\alpha$, zatímco
$\eta$/$\beta$ bývá učicí rychlost. Přejmenovat na $\alpha$.

### N6. `\pageref{sec:uvod}` odkazuje na začátek kapitoly, ne na tabulku
V číselném příkladu k větě o schématech: „Vezměme populaci ze str.
\pageref{sec:uvod}". Label `sec:uvod` je u nadpisu kapitoly, tabulka je o stránku
dál. Zavést vlastní label u tabulky a odkazovat na něj.

### N7. NEAT — definice $E$ a $D$ je zkratkovitá
„$E$, $D$ jsou počty přebývajících a nesouhlasných genů" nerozliší, že *excess*
jsou geny za koncem kratšího genomu a *disjoint* geny chybějící uvnitř
společného rozsahu. Upřesnit.

### N8. Chybí Michalewicz v seznamu literatury
Úvodní odstavec jmenuje Eiben & Smith a Mitchella; kurz na obou přednáškách
uvádí i Michalewicze (*Genetic Algorithms + Data Structures = Evolution
Programs*), z něhož pochází právě reprezentace SAT a kombinatorické kapitoly.

### N9. Drobná doplnění z kurzu
- „Tragedy of the commons" u vězňova dilematu (slide to explicitně jmenuje).
- Flegrova „zamrzlá evoluce" jako poznámka u ztráty diverzity (slide EVA II).
- Poznámka o „efektivnější než ukládat celá řešení" u tabu listu — už tam je ✓.

---

## Poznámky k didaktice (bez nutnosti zásahu)

- Rozložení hloubky je vyvážené; každá kapitola má „Shrnutí k~zkoušce".
- Číselné příklady jsou na správných místech (ruleta, škálování, TST, PMX/OX/CX/ER,
  DE, PSO, ACO ×2, SA, crowding distance, hypervolume) — to je hlavní přednost textu.
- Duplicity: pravidlo 1/5 je vysvětleno v kap. ES i v kap. „Ladění a řízení
  parametrů"; to je ale funkční křížový odkaz, ne redundance.
- Mapovací tabulka okruh → kapitola na začátku je výborný nápad.
