# Státnice — SZZ Umělá inteligence (MFF UK)

## Kde jsou otázky

Oficiální znění zkušebních okruhů (= otázek) je zde:

**<https://www.mff.cuni.cz/cs/studenti/bc-a-mgr-studium/studijni-plany/2025-2026/informatika/mgr/umela-inteligence>**

Stránka je **zdroj pravdy** pro pokrytí — okruhy jsou tam členěné podle zaměření (Inteligentní agenti / Strojové učení / Robotika) a každá věta okruhu odpovídá jedné kapitole v textech níže.

## Texty

Učební texty ke třem okruhům magisterské státní závěrečné zkoušky oboru Umělá inteligence:

| Soubor | Okruh |
|---|---|
| `01-multiagentni-systemy` | Multiagentní systémy |
| `02-prirodou-inspirovane-pocitani` | Přírodou inspirované počítání |
| `03-dobyvani-znalosti` | Dobývání znalostí (+ část II: Internet a klasifikační metody, + část III: Neuronové sítě, strojové učení a náhodnost) |

Zkrácené verze k opakování (jedna otázka = jedna strana):

| Soubor | Obsah |
|---|---|
| `01-multiagentni-systemy-shrnuti` | 8 stran: rozcestník + 7 otázek okruhu |
| `02-prirodou-inspirovane-pocitani-shrnuti` | 7 stran: rozcestník (+ srovnávací tabulka algoritmů) + 6 otázek okruhu |
| `03-dobyvani-znalosti-shrnuti` | 8 stran: rozcestník + 7 otázek okruhu |

První strana každého shrnutí je rozcestník: odkaz na oficiální znění okruhu, seznam otázek s čísly stran, průřezová témata, co se chce spočítat u tabule a nejčastější chyby.

Pokrytí ověřeno proti oficiálnímu znění okruhů 2025/2026 (odkaz výše). Recenzní protokoly jsou ve složce `recenze/`.

## Kompilace

```sh
pdflatex <soubor>.tex   # 2× kvůli obsahu a referencím
```

Vyžaduje TeX Live s balíčky `babel` (czech), `tcolorbox`, `algorithm`, `algpseudocode`, `booktabs`; shrnutí navíc `multicol`, `fancyhdr`, `microtype`, `lmodern`.
