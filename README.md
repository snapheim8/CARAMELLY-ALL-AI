# caramelly.no

To sider, ferdig til å publiseres på domenet ditt:

- `index.html` — "All things AI", din personlige kontaktside for ONS.
- `styrerommet.html` — rundbordsinvitasjonen du og Kristin lager sammen. Lenket fra forsiden.
- `CNAME` — trengs kun hvis du bruker GitHub Pages (se alternativ A under).

Begge er selvstendige HTML-filer (all CSS/JS/bilder er bygget inn i filene selv) — ingen build-steg, ingen avhengigheter. Bare last dem opp et sted som kan servere statiske filer.

## Besøkstelling (valgfritt)

Øverst i `index.html` ligger en utkommentert GoatCounter-snutt. Opprett en gratis konto på goatcounter.com, bytt inn din site-kode, og fjern kommentar-tagene rundt `<script>`-linjen — da begynner den å telle besøk på ekte, på tvers av alle besøkende.

## Alternativ A — GitHub Pages (gratis, enkelt)

1. Opprett et nytt repo på github.com (offentlig eller privat — begge fungerer med Pages).
2. Last opp `index.html`, `styrerommet.html` og `CNAME` til repoet (dra-og-slipp i GitHub sitt web-grensesnitt fungerer fint, eller `git push` hvis du har git lokalt).
3. I repoet: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, velg `main`-branchen og `/ (root)`-mappen.
4. Under **Settings → Pages → Custom domain**, skriv inn `caramelly.no` og lagre. GitHub gir deg da to-fire IP-adresser (A-records) du skal peke domenet ditt til.
5. Hos domeneregistraren din (der du kjøpte caramelly.no, sannsynligvis Domeneshop eller lignende): legg inn de A-recordene GitHub oppga for `@` (roten av domenet), og en CNAME-record for `www` som peker til `dittbrukernavn.github.io`.
6. Det tar typisk 10 minutter til noen timer før DNS-endringen slår ut. GitHub Pages ordner HTTPS-sertifikat automatisk når det er verifisert.

## Alternativ B — enklere: last opp direkte til webhotellet ditt

Hvis caramelly.no allerede har et webhotell (Domeneshop, One.com og lignende har ofte dette inkludert i domeneabonnementet), er dette raskeste vei:

1. Logg inn i kontrollpanelet hos hotellleverandøren din.
2. Finn filbehandleren for nettstedet (ofte under "Filer" / "File Manager" / FTP).
3. Last opp `index.html` og `styrerommet.html` til rotmappen (`public_html` eller tilsvarende). `CNAME`-filen trengs IKKE her — den er bare for GitHub Pages.
4. Ferdig — ingen DNS-endring nødvendig, siden filene havner rett på domenet som allerede peker dit.

## Hva jeg kan hjelpe med herfra

Jeg kan ikke logge inn på GitHub- eller domeneregistrar-kontoen din selv (det krever passord jeg ikke skal håndtere). Men hvis du:

- **har en datamaskin koblet til denne samtalen** med git/GitHub allerede satt opp, kan jeg skrive filene rett inn i mappen din og kjøre `git add`/`commit`/`push`-kommandoene for deg — du er allerede innlogget lokalt, jeg trenger ikke se noe passord.
- **vil ha hjelp til å navigere GitHub eller registrarens nettside** mens du selv er innlogget i din egen nettleser, kan jeg lose deg gjennom det steg for steg.

Si fra hvilken vei du vil gå.
