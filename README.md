# Státnice — SZZ Umělá inteligence (MFF UK)

Učební texty ke třem okruhům magisterské státní závěrečné zkoušky oboru Umělá inteligence:

| Soubor | Okruh |
|---|---|
| `01-multiagentni-systemy` | Multiagentní systémy |
| `02-prirodou-inspirovane-pocitani` | Přírodou inspirované počítání |
| `03-dobyvani-znalosti` | Dobývání znalostí (+ část II: Internet a klasifikační metody, + část III: Neuronové sítě, strojové učení a náhodnost) |

Pokrytí ověřeno proti [oficiálnímu znění okruhů 2025/2026](https://www.mff.cuni.cz/cs/studenti/bc-a-mgr-studium/studijni-plany/2025-2026/informatika/mgr/umela-inteligence). Recenzní protokoly jsou ve složce `recenze/`.

## Kompilace

```sh
pdflatex <soubor>.tex   # 2× kvůli obsahu a referencím
```

Vyžaduje TeX Live s balíčky `babel` (czech), `tcolorbox`, `algorithm`, `algpseudocode`, `booktabs`.
