# caramelly.no: teknisk notat

Dette notatet forklarer hvordan nettsiden caramelly.no er bygget og hvordan den oppdateres. Les det før du endrer noe på siden. Sist oppdatert 23. november 2026.

## Hvor siden ligger

- **Kilde:** GitHub-repoet `snapheim8/CARAMELLY-ALL-AI`, grenen `main`. På Christians PC ligger repoet i `C:\Users\chris\OneDrive\Dokumenter\GitHub\CARAMELLY_ALL AI`.
- **Publisering:** GitHub Pages publiserer `main` automatisk til caramelly.no, vanligvis ett til to minutter etter en push. Filen `CNAME` kobler GitHub Pages til domenet. Ikke slett den.
- **Den ekte versjonen er alltid `index.html` i repoet,** ikke en kopi i en chat, en artifact eller en arbeidsmappe. Hent alltid siste versjon fra repoet før du endrer noe, fordi Christian kan ha endret filen selv.
- **Endringer fra Claude:** Claude har skrivetilgang til repoet via GitHub-koblingen (en fin-kornet nøkkel som bare gjelder dette repoet). Claude kan derfor endre tekstfiler og pushe direkte, fra hvilken som helst enhet. Bilder må fortsatt legges inn fra PC-en.
- **Endringer fra PC-en:** Christian bruker GitHub Desktop. Klikk alltid **Fetch origin** og **Pull** før du endrer noe lokalt, fordi Claude kan ha pushet endringer siden sist.

## Filer i repoet

| Fil | Hva den er |
|---|---|
| `index.html` | Hele forsiden: HTML, CSS og JavaScript i én fil, cirka 84 KB. |
| `assets/` | Bildene på siden (se «Bilder»). |
| `styrerommet.html` | Liten side som videresender til `/#styrerommet`, så gamle lenker fortsatt virker. |
| `CNAME` | Domenet `caramelly.no` for GitHub Pages. |
| `README.md` | Kort beskrivelse av repoet med henvisning til dette notatet. |
| `INNHOLD.md` | Innholdsgrunnlaget: teksten og faktaene på siden. |
| `Claude outputs/` | Gamle arbeidsfiler fra Claude. Ikke en del av siden. |

## Slik er `index.html` bygget

### Oppsett øverst i filen (må aldri fjernes)

Filen må starte med `<!DOCTYPE html>`, `<html lang="no">`, `<head>`, `<meta charset="UTF-8">` og `<meta name="viewport" content="width=device-width, initial-scale=1">`. Uten viewport-linjen viser mobiltelefoner desktop-versjonen i miniatyr. Det skjedde én gang og var vanskelig å finne.

Rett før `<style>` ligger skriptet for GoatCounter, en enkel besøksteller (`https://caramelly.goatcounter.com/count`). Ikke fjern det.

### Seksjoner i rekkefølge

| Id | Innhold |
|---|---|
| `.hero` | Toppbildet (Christian på kaia i Stavanger), overskrift, to knapper. |
| `#posisjon` | «Hvem jeg er»: sitat, bakgrunn, merkelapper. |
| `#impact` | Fire kort: Sofia, Matchforger, Nikola, AI-hackathon i India. |
| `#tilbud` | Kjernetilbudet: interim ledelse for AI-transformasjon, med portrettet. |
| `#styrerommet` | Styrerommet: rundbordssamtaler om AI, et tilbud som bestilles via kontakt. |
| `#sitater` | Sitatbibliotek fra LinkedIn-artikler, med LinkedIn-ikon og lenke. |
| `#kontakt` | E-post, telefon og Sofia-chatten i siden. |
| `#bio` | Sitatkort: «Det er som å ta lappen…». |

Etter seksjonene ligger Sofia-widgeten (den flytende chatboblen nederst til høyre).

### Norsk og engelsk (viktigst å huske)

Siden har en NO/EN-bryter. Teksten styres av JavaScript nederst i filen:

- Elementer har `data-i18n="nøkkel"` (vanlig tekst), `data-i18n-html="nøkkel"` (tekst med lenker eller `<span>`) eller `data-i18n-placeholder="nøkkel"` (plassholdertekst i felt).
- Ordboken `var I18N = { no:{...}, en:{...} }` har én verdi per nøkkel og språk.
- Funksjonen `applyLang()` skriver ordbokens verdi over HTML-teksten når siden lastes.

**Regel:** Når du endrer en tekst, må du endre den tre steder: i HTML-en, i `I18N.no` og i `I18N.en`. Endrer du bare HTML-en, blir endringen overskrevet av ordboken og vises ikke.

Unntak: overskriftene «Sofia», «Matchforger» og «Nikola» på impact-kortene og sitatene i `#sitater` har ingen nøkkel og står bare i HTML-en.

### Bilder

Bildene ligger som vanlige filer i mappen `assets/` og lenkes fra `index.html` med relative stier, for eksempel `src="assets/christian-portrett.jpg"`.

| Fil | Størrelse | Brukes i |
|---|---|---|
| `assets/hero-christian-stavanger.jpg` | 1400 × 1867, 233 KB | Toppbildet (`.hero-media img`). Ansiktet ligger i øverste 30 prosent av bildet. |
| `assets/christian-portrett.jpg` | 600 × 600, 55 KB | Kjernetilbudet (`.offer-portrait`), hånd mot ansiktet, svart bakgrunn. |
| `assets/christian-portrett-liten.jpg` | 176 × 176, 5 KB | Den runde boblen ved knappen på mobil (`.offer-bubble`). |

Til og med november 2026 lå bildene inne i `index.html` som base64-tekst, og filen var 470 KB. De ble flyttet ut så filen kan redigeres via GitHub-koblingen og fra telefon. Ikke legg bilder tilbake som `data:`-tekst.

GitHub-koblingen i Claude kan ikke laste opp bildefiler. Nye bilder må derfor legges i `assets/` fra PC-en (GitHub Desktop) eller lastes opp i GitHub sitt nettgrensesnitt.

### Design

Farger er definert som variabler i `:root`:

| Variabel | Verdi | Brukes til |
|---|---|---|
| `--paper` | `#EFEAD9` | Bakgrunn |
| `--paper-hi` | `#F8F4E8` | Lys bakgrunn |
| `--card` | `#F9F5EA` | Kort |
| `--ink` | `#1C2420` | Tekst |
| `--ink-soft` | `#4A5349` | Brødtekst |
| `--line` | `#CFC6AE` | Linjer og kanter |
| `--brass` / `--brass-hi` | `#B4762C` / `#D69A45` | Aksentfarge (messing) |
| `--petrol` / `--petrol-hi` | `#1F4A46` / `#2E6360` | Kjernetilbudet, sitatkort |
| `--rust` | `#B5502E` | Hovedknapper |

Impact-kortene har egne ikonfarger: Sofia petrol, Matchforger messing, Nikola rust, India-hackathon blå (`#2D4C8C`).

Fonter fra Google Fonts: Newsreader (overskrifter, sitater), Archivo (brødtekst), IBM Plex Mono (små etiketter). Siden har mørk modus via `prefers-color-scheme: dark`.

### Bruddpunkter for mobil

| Bredde | Hva skjer |
|---|---|
| `≤ 760px` | Menyen i toppen skjules. |
| `≤ 780px` | Impact-kortene går til én kolonne og blir sammenleggbare («Les mer»). |
| `≤ 860px` | Portrettet i Kjernetilbudet byttes til en rund boble ved knappen. |
| `≥ 1201px` | Hero-bildet begrenses til 1200 px bredde og legges til høyre, slik at ansiktet alltid vises. |

### Sofia-chatten

Sofia (både i `#kontakt` og den flytende boblen) sender meldinger til en n8n-webhook på `https://herheim.app.n8n.cloud/webhook/...`. Svarene lages av n8n, ikke av siden. Hvis Sofia ikke svarer, sjekk n8n-flyten først.

## Fast arbeidsflyt for en endring

1. Hent siste `index.html` fra GitHub (grenen `main`), ikke fra en gammel kopi.
2. Gjør endringen. Ved tekst: oppdater HTML, `I18N.no` og `I18N.en`.
3. Sjekk siden i nettleser på mobilbredde (390 px), vanlig bredde (1366 px) og bred skjerm (1920 px eller mer).
4. Valgfritt: publiser en kommenterbar kopi som Claude-artifact for gjennomgang. Ta med bildene i `assets/` som egne filer i artifacten. En artifact-kopi skal ikke ha `<!DOCTYPE>`, `<html>`, `<head>` eller `<body>`, og GoatCounter fjernes der. Repo-versjonen skal alltid ha dem.
5. Commit og push til `main`, enten via GitHub-koblingen i Claude eller fra GitHub Desktop på PC-en. Skriv en kort commit-melding som sier hva som er endret.
6. Siden er oppdatert på caramelly.no etter ett til to minutter.

## Regler for innhold

- Styrerommet er et tilbud nå, og bestilles ved å ta kontakt. Ikke kall det en serie som kommer senere.
- Kristin Gabrielsen nevnes ikke i omtalen av Styrerommet. Christian og Kristin utvikler EdelT, en kandidatreise. EdelT er ikke omtalt på siden ennå; spør Christian før du legger det inn.
- ONS er over. Ikke nevn det.
- Bruk bare tall og fakta som står i `INNHOLD.md` eller som Christian har bekreftet.
- Ingen konfidensielle avtaler, kundenavn eller interne produktdetaljer.
