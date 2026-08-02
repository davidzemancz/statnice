# Statnice — učební texty ke SZZ (Umělá inteligence, MFF UK)

Repozitář obsahuje generovaná skripta ke třem okruhům magisterské státní závěrečné zkoušky. Není to softwarový projekt: jsou to LaTeXové dokumenty a jejich PDF.

Repozitář je podsložkou osobního archivu `~/DEV/MFF/`, kde jsou v adresářích `4-1`, `4-2`, `5-1`, `5-2`, `6-1`, `6-2` (rok-semestr, uvnitř složka na předmět) uložené zdrojové slidy jednotlivých kurzů. Ty verzované nejsou.

### Kde jsou zdrojové slidy k okruhům

| Okruh | Zdroje (relativně k tomuto repu) |
|---|---|
| Multiagentní systémy | `../5-2/MAS/mas25-en.pdf` (NAIL106, Pilát), `../4-2/MAS/` |
| Přírodou inspirované počítání | `../5-1/EVA 1/`, `../4-2/EVO/` (EVA I/II, Neruda/Pilát) |
| Dobývání znalostí | `../5-2/Data Mining/` (NDBI023, Mrázová), `../6-1/SNA/` (Social Networks and their Analysis) |
| Internet a klasifikační metody | `../6-2/Internet a klasifikacni metody/` (NAIL105, Holeňa) |
| Neuronové sítě, strojové učení a náhodnost | `../6-2/Internet a klasifikacni metody/nmr1–nmr5.pdf` (volitelný kurz, Holeňa) |

Pozn.: `nmr1`–`nmr5` leží ve složce IKM, ale jsou to slidy jiného (volitelného) Holeňova kurzu — v metadatech PDF nesou zastaralý titul „The specificity of neural networks in extracting rules from data“.

## Dokumenty

Tři samostatné LaTeX dokumenty, česky, každý pokrývá jeden zkouškový okruh:

| Soubor | Okruh |
|---|---|
| `01-multiagentni-systemy.tex` | Multiagentní systémy |
| `02-prirodou-inspirovane-pocitani.tex` | Přírodou inspirované počítání |
| `03-dobyvani-znalosti.tex` | Dobývání znalostí + IKM (část II) + NN/ML/náhodnost (část III) |

Recenzní protokoly nezávislých kontrol jsou v `recenze/`.

Oficiální znění okruhů (zdroj pravdy pro pokrytí):
<https://www.mff.cuni.cz/cs/studenti/bc-a-mgr-studium/studijni-plany/2025-2026/informatika/mgr/umela-inteligence>
(okruhy jsou tam členěné podle zaměření — Inteligentní agenti / Strojové učení / Robotika).

### Kompilace

```sh
pdflatex -interaction=nonstopmode <soubor>.tex   # 2× kvůli obsahu a křížovým odkazům
```

Potřebné balíčky: `babel` (czech), `tcolorbox` (`most`), `algorithm`, `algpseudocode`, `booktabs`, `amsmath`, `hyperref`, `enumitem`, `parskip`.

### Konvence textů

- Sdílená preambule ve všech třech souborech; definice se sázejí do `\begin{defbox}[Název]`, pseudokód do `defbox` + `algorithmic` (ne do plovoucího `algorithm` — dokument float nepoužívá).
- Struktura: `\part` → `\section` (jedna kapitola = jedna položka okruhu) → `\subsection`. Každá kapitola končí oddílem **„Shrnutí ke zkoušce“** s odrážkami — to je hlavní opakovací vrstva, udržovat ji konzistentní s textem kapitoly.
- Na začátku dokumentu je tabulka **mapování okruhů na kapitoly**; při přidání kapitoly ji aktualizovat.
- České termíny, anglický ekvivalent kurzívou v závorce při prvním výskytu. Uvozovky `\uv{}`, nezlomitelná mezera po jednopísmenných předložkách (`v~datech`, `s~učitelem`).
- Popisky `\label{sec:...}` používat pro křížové odkazy; nové kapitoly části III mají prefix `sec:nmr-`.

### QA po úpravách

1. Přeložit **2×** a zkontrolovat `exit=0`.
2. Overfull boxy — **pozor**: log pdfTeXu má konce řádků NEL (U+0085), takže obyčejný `grep` tiše selže. Používat:
   ```sh
   LC_ALL=C tr '\205' '\n' < 03-dobyvani-znalosti.log | LC_ALL=C grep "Overfull"
   ```
   Cíl: žádný overfull box nad ~10 pt. Typický viník je dlouhý inline vzorec (v inline matematice se láme jen na relacích a binárních operátorech) nebo bold slovo se spojovníkem (`Metropolis--Hastings`) na konci řádku — řešením je přesun do `\[...\]`, `multline*`, nebo přeformulování věty.
3. Zkontrolovat, že `\ref` nehlásí `undefined`.

### Pasti

- `\cmidrule` a `\cline` se s českým babelem zacyklí — používat jen `\toprule`/`\midrule`/`\bottomrule`.
- Tabulky a `defbox` musí být `breakable` (v preambuli už nastaveno), jinak přetečou stránku.

## Práce s tímto repozitářem

- Necommitovat bez vyžádání; build artefakty (`.aux`, `.log`, `.out`, `.toc`) jsou v `.gitignore`, ale PDF se verzují.
- Při doplňování látky z nových slidů: vytáhnout text přes `pdftotext -layout`, doplnit do příslušné části a ověřit proti oficiálnímu znění okruhu, jestli jde o látku okruhu, nebo o nadstavbu (a v mapovací tabulce to tak označit).
