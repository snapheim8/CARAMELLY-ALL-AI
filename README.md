# caramelly.no

Kildekoden til caramelly.no, Christian Herheims side om AI, interim ledelse og Styrerommet. Siden publiseres automatisk av GitHub Pages fra grenen `main`.

## Filer

| Fil | Hva den er |
|---|---|
| `index.html` | Hele forsiden (HTML, CSS og JavaScript), med norsk og engelsk tekst. |
| `styrerommet.html` | Videresender til Styrerommet-delen av forsiden. Beholdt så gamle lenker fortsatt virker. |
| `assets/` | Bildene på siden. |
| `CNAME` | Kobler GitHub Pages til domenet caramelly.no. Ikke slett den. |
| `CLAUDE.md` | Teknisk notat: hvordan siden er bygget og hvordan den oppdateres. Les dette før du endrer noe. |
| `INNHOLD.md` | Innholdsgrunnlag: teksten og faktaene som står på siden. |

## Slik oppdaterer du siden

1. Endre `index.html`. Ved tekstendringer må HTML-en og begge språkene i `I18N` oppdateres. Se `CLAUDE.md`.
2. Commit og push til `main`.
3. GitHub Pages publiserer endringen på caramelly.no etter ett til to minutter.
