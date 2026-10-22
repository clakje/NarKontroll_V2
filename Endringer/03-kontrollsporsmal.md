# Økt 03 · Kontrollspørsmål med umiddelbar respons

Les [README.md](README.md) først. Økt 02 bør være gjort (spørsmålet står da i venstre kolonne).

**Kilde:** `bilder/lysbilde-11.png`, `bilder/lysbilde-40.png`.

> Lysbilde 11: «På alle kontrollspørsmål ønskes umiddelbar svarrespons, og at bruker kan endre sitt
> svar og få ny umiddelbar svarrespons. Ikke "Sjekk svar", men "Fortsett". Ikke nødvendig med
> summering og resultat til slutt.»
> Lysbilde 40: resultatpanelet i Avslutning (11/12 moduler fullført, 6/7 riktige på første forsøk).

## Mål

Deltakeren får svar med en gang de velger et alternativ, kan prøve et annet, og går videre med
«Fortsett». Kurset teller ikke poeng foran deltakeren.

## Endringer

### 1. Respons med en gang (`js/app.js`: `sporsmalHtml`, `sjekkSvar`, hendelsen for radioknappene)

I dag: deltakeren velger (`valgtSvar`), trykker «Sjekk svar», og svaret låses (`data-laast`,
`disabled`). Nytt:

- Når deltakeren velger et alternativ, vises tilbakemeldingen med en gang (riktig/feil og `forklaring`)
  under alternativene. Bruk den eksisterende `.tilbakemelding` og `data-resultat` på alternativet.
- Alternativene låses **ikke**. Velger deltakeren et annet, oppdateres tilbakemeldingen.
- Ved feil svar: vis «Ikke helt.» og forklaringen, men **ikke** hvilket svar som er riktig, så det er
  noe å prøve igjen. Ved riktig svar: «Riktig.» og forklaringen. Sjekk at hver `forklaring` i
  `kurs.js` ikke røper fasiten når den vises etter et feil svar. Gjør den det, vis forklaringen bare
  ved riktig svar, og en kort hjelpetekst («Prøv et annet svar.») ved feil.
- Tilbakemeldingen leses opp (`role="status"`), men fokus blir på radioknappen, så piltastene
  fortsatt bytter alternativ. I dag flyttes fokus til `#tilbakemelding`. Fjern det.
- Piltastene blar mellom steg ellers. Sjekk at venstre/høyre-pil i en radiogruppe ikke både bytter
  svar og blar til neste steg.

### 2. «Fortsett» i stedet for «Sjekk svar» (`navradHtml`, `neste`)

- Knappen heter «Fortsett» (eller «Fullfør casen»/«Fullfør modulen» hvis det er siste steg).
- Den er deaktivert til deltakeren har valgt et svar. Den krever **ikke** riktig svar.
- `neste()` skal ikke lenger kalle `sjekkSvar()`.

### 3. Lagring og poeng (`tilstand.svar`, `poeng`, `lagre`)

- Lagre fortsatt **første** valg per spørsmål (`[valg, riktig]`), så SCORM-poengsummen
  (`cmi.core.score.raw`) betyr det samme som før. Senere valg endrer ikke den lagrede verdien.
  Poengsummen vises ikke i kurset, men LMS-et får den.
- Lagre også siste valg, så spørsmålet vises med siste svar og tilbakemelding når deltakeren kommer
  tilbake. Hold `suspend_data` kort (README, SCORM: grensen er 4096 tegn).

### 4. Ingen summering til slutt

- M13 «Avslutning», steg 2: fjern `panel: { type: "resultat" }` i `kurs.js`. Steget får den rolige
  flaten i høyre kolonne. Fjern `resultatHtml()` og CSS for `.resultat` hvis de ikke brukes lenger.
- Hovedmenyen, `fremdriftHtml()`: fjern «… X av Y kontrollspørsmål riktig på første forsøk».
- Utviklerpanelet kan fortsatt vise score.

## Ikke gjør

- Ikke endre selve spørsmålene eller svaralternativene. Det gjøres case for case i senere økter.

## Test

- `index.html?dev=1#case-1/4`: velg feil svar, så riktig. Tilbakemeldingen bytter med en gang.
  «Fortsett» virker uten riktig svar.
- Gå tilbake og frem: siste svar og tilbakemelding står der fortsatt.
- Tøm fremdriften i utviklerpanelet. Svar feil først, så riktig, på alle 7 spørsmålene. Score i
  utviklerpanelet er 0.
- Skjermleser/tastatur: Tab til alternativene, piltast bytter svar, tilbakemeldingen leses opp.
- Avslutning steg 2 og hovedmenyen etter fullført kurs viser ingen poengsum.

## Ferdig når

- [x] Tilbakemelding med en gang, og svaret kan endres
- [x] «Fortsett» i stedet for «Sjekk svar»
- [x] Ingen resultat/summering i kurset
- [x] SCORM-score bygger fortsatt på første forsøk
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: kontrollspørsmål med umiddelbar respons og «Fortsett», uten summering til slutt`
