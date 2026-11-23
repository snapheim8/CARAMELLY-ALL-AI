Dette prosjektet bygger og vedlikeholder nettsiden caramelly.no for Christian Herheim (Caramelly AS).

Hvor siden ligger
- Den ekte versjonen er GitHub-repoet snapheim8/CARAMELLY-ALL-AI, grenen main. GitHub Pages publiserer main til caramelly.no.
- På Christians PC ligger repoet i C:\Users\chris\OneDrive\Dokumenter\GitHub\CARAMELLY_ALL AI.
- Prosjektfilene CLAUDE.md (teknisk notat) og INNHOLD.md (tekst og fakta på siden) er kopier. Hvis de avviker fra repoet, er det repoet som gjelder.

Før du endrer noe
- Les CLAUDE.md og INNHOLD.md.
- Hent siste versjon av filen fra GitHub, ikke fra en gammel kopi eller en tidligere chat.

Regler
- Tekst må endres tre steder: i HTML-en, i I18N.no og i I18N.en.
- Fjern aldri DOCTYPE, viewport-linjen eller GoatCounter-skriptet øverst i index.html.
- Bilder ligger i assets/ som egne filer. Legg dem aldri inn i HTML-en som base64-tekst.
- Når fakta endres (tjenester, tall, kontaktinfo, titler), oppdater også JSON-LD i head, meta description og llms.txt.
- Følg GEO- og SEO-sjekklisten i prosjektfilen geo-sjekkliste.md når den finnes.
- Ikke nevn samarbeidspartnere, kunder eller produkter i utvikling som ikke allerede står på siden, uten at Christian har godkjent det. ONS er over og skal ikke nevnes.
- Repoet er offentlig. Ikke skriv noe konfidensielt i filer som legges der.

Slik publiseres endringer
- Små tekstfiler (llms.txt, robots.txt, sitemap.xml, notater) kan pushes direkte med GitHub-koblingen.
- index.html er for stor til GitHub-koblingen. Skriv den til PC-mappen via koblingen til Christians PC, så pusher Christian i GitHub Desktop.
- Bilder må alltid legges inn fra PC-en.
- Sjekk endringer på mobil (390 px), laptop (1366 px) og bred skjerm (1920 px) før de publiseres.

Svar til Christian på norsk, kort og konkret, uten tankestreker. Si alltid hva han selv må gjøre (for eksempel pushe), og hva som er gjort.
