# Økt 02 · Fast oppsett på stegsidene

Les [README.md](README.md) først.

**Kilde:** `bilder/lysbilde-03.png` (toppfeltet), `bilder/lysbilde-08.png` (kolonnene og «for å bla»),
`bilder/lysbilde-09.png` (case-boksen).

> Lysbilde 3: «Litt lavere topp-bar»
> Lysbilde 8: «Ønsker at bredden på disse to kolonnene er statiske, altså at de har en låst posisjon
> gjennomgående i alle case.» og «Slette "for å bla" gjennomgående»
> Lysbilde 9: Case-boksen («Case 1 · Line Danser har smerter …») på steg 2: «Står på side en, trengs ikke her?!?»

## Mål

Stegsidene ser like ut fra steg til steg, så deltakeren ikke må lete. Kolonnene står stille, toppfeltet
tar mindre plass, og det som bare trengs én gang, vises én gang.

## Endringer

### 1. Lavere toppfelt (`css/app.css`, `.toppfelt`)

Toppfeltet har `padding: 10px …` og knapper på 44 px. Gjør det ca. 25 % lavere, for eksempel
`padding: 6px …` og litt mindre logo. Trykkflatene skal fortsatt være minst 44 × 44 px (README, Design).
Juster eventuelt også regelen i `@media (min-width: 861px) and (max-height: 900px)`.

### 2. Låste kolonner i alle moduler (`css/app.css` rundt `.scene`, `js/app.js` `velgPanel`)

I dag bytter `.scene` mellom tre oppsett:

- `minmax(0, 3fr) minmax(0, 2fr)` (vanlig steg)
- `1fr 1fr` når skannesonen har en registrering (`.sone[data-rekke]`)
- én midtstilt kolonne på 760 px for kontrollspørsmål og steg uten skannesone

Nytt: **alle steg i alle moduler** (ikke hovedmenyen) har de samme to kolonnene, like brede
(`minmax(0, 1fr) minmax(0, 1fr)`), med samme `max-width` og samme start. Venstre kolonne står alltid
på samme sted, og skannesonen alltid til høyre.

- Kontrollspørsmål: spørsmålet står i venstre kolonne. Høyre kolonne viser en rolig flate
  (`stilleHtml`) med ikonet for kontrollspørsmål og teksten «Velg ett svar.» I `velgPanel` returnerer
  `sporsmal` i dag `ingen: true`. Endre det.
- Steg uten skannesone (for eksempel `info` uten panel, `instruks`): høyre kolonne viser den rolige
  flaten «Ingen skanning i dette steget.», som `info` allerede gjør.
- Unntak: steg med `iKortet` (bare M0). Det tar økt 06 stilling til. La dem være som nå.
- Fjern reglene som lager én midtstilt kolonne, og regelen for `data-rekke` hvis den ikke trengs lenger.
- Under 861 px bredde blir det én kolonne som før.

### 3. Fjern «← → for å bla» (`js/app.js`, `navradHtml`)

Fjern `<span class="tastatur-hint">…</span>`. Piltastene skal fortsatt virke. Fjern CSS for
`.tastatur-hint` hvis den ikke brukes andre steder.

### 4. Case-boksen bare på første steg (`js/app.js`, `veilederHtml`)

Boksen med casebeskrivelsen (`historie historie--case`, og `historie` for moduler uten appknapp) vises
bare på **steg 1** i modulen. På steg 2 og videre:

- Boksen vises ikke.
- Merkelappen øverst (`eyebrow-rad`) viser da `eyebrow` («Case 1») foran appmerket, slik andre moduler gjør,
  så deltakeren fortsatt ser hvilken case de er i.
- Skjermleseren får fortsatt modultittelen via `h1`.

## Ikke gjør

- Ikke endre kontrollspørsmålenes logikk (økt 03) eller tekstene i casene.
- Ikke fjern stegkortet på enkeltsteg. Det gjøres i økt 07 og 08.

## Test

- Bla gjennom hele Case 1 og Case 4 (`index.html?dev=1#case-1/1`) i 1280 × 650 og 1920 × 940.
  Venstre kolonne står på samme sted på alle steg, også på kontrollspørsmålet.
- Case-boksen vises bare på steg 1. På steg 2 står «Case 1» ved appmerket.
- «for å bla» er borte, og piltastene blar fortsatt.
- Toppfeltet er lavere, og «Hovedmeny» er fortsatt minst 44 px høy.
- Smal skjerm (under 860 px): én kolonne, ingen horisontal rulling.

## Ferdig når

- [x] Toppfeltet er lavere
- [x] Kolonnene er like og står stille på alle steg (unntatt M0, økt 06)
- [x] «for å bla» er fjernet overalt
- [x] Case-boksen vises bare på steg 1
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: lavere toppfelt, låste kolonner, case-boksen bare på steg 1`
