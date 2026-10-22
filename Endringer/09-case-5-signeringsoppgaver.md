# Økt 09 · Case 5: Signeringsoppgaver og nylig historikk

Les [README.md](README.md) først. Økt 01 må være gjort (knappenavnet og tittelen).

**Kilde:** `bilder/lysbilde-22.png`, `bilder/lysbilde-23.png`, og lysbilde 4 (appens startmeny 2.1).
Lysbilde 24 og 25 har bare det nye navnet på merkelappen.

## Bakgrunn

Knappen som het **OVERSIKT**, heter nå **Signeringsoppgaver og nylig historikk** i appen. Den er
grønn, står øverst i hel bredde og viser «10 hendelser venter på signatur» med et rødt tall
(lysbilde 4). Fagekspertene skriver (lysbilde 23):

> «Signeringsoppgaver og nylig historikk har to faner. Du kan søke og filtrere i begge.»
> – Etterkommentarer
> – Dobbeltsignering

Disse to linjene erstatter punktene om avvik («Kommentarer om avvik er skjult», «Medisinromsansvarlig
og/eller leder kan se kommentarene …»). Hva fanene heter, og hvor Avvik og Siste 14 dager er nå, er
ikke sagt.

## Mål

Case 5 beskriver den nye skjermen slik fagekspertene har skrevet den, og merker det vi ikke vet.

## Endringer (`case-5` i `content/kurs.js`)

### Steg 1 «Nå er du bruker 2»

- `tekst`: «… Gå inn i **Signeringsoppgaver og nylig historikk** i appen, og gjør dobbeltkontrollen.»
- Rad 1: «Trykk på **Signeringsoppgaver og nylig historikk**, den grønne knappen øverst med det røde tallet.»
- Rad 2: «Finn uttaket fra Case 1 i listen over registreringer som venter på dobbeltsignering.
  [AVKLARES: navnet på fanen]»
- Rad 5: «Gå tilbake til startmenyen. Det røde tallet er borte når alle dobbeltsigneringer er gjort.»
- Resten uendret.

### Steg 2 «Se gjennom fanene»

- `tekst`: «Signeringsoppgaver og nylig historikk har to faner. Du kan søke og filtrere i begge.»
- `punkter`: tolkning av fagekspertenes liste, som signeringsoppgavene du finner her:
  - «**Etterkommentarer**: registreringer som venter på en kommentar.» [AVKLARES: stemmer det?]
  - «**Dobbeltsignering**: registreringer som venter på signatur nummer to.»
- `rekke` (høyre kolonne), skrives om:
  1. «Åpne den andre fanen. [AVKLARES: navnet på fanen, og hva den viser (nylig historikk? hvor langt tilbake?)]»
  2. Behold skanne-søket (`kode: "PROD-SOBRIL-10"`): «Søk ved å skanne produktkoden mens du står i en av fanene.»
     Merknad: «Du kan også skrive navnet i søkefeltet, men skanning er tryggest.»
  3. Behold etterkommentaren: «Du kan skrive en etterkommentar på alle registreringer. Langtrykk på en
     registrering, og skriv kommentaren.» [AVKLARES: navnet på menyvalget] (står der fra før)
- Fjern radene om fanene **Avvik** og **Siste**.

### Steg 3 «Ikke overlat det til neste skift» (obs)

Bytt «det røde varselet i startmenyen» med «det røde tallet på **Signeringsoppgaver og nylig
historikk**». Ellers uendret.

### Steg 4, kontrollspørsmålet «Hvem kan lese kommentarene på et avvik?»

Ingen kommentar på lysbilde 25, men punktet om at avvikskommentarer er skjult, er fjernet fra steg 2.
Deltakeren har da ikke lest svaret. Velg én:

- **a)** Behold spørsmålet, og legg punktet om avvikskommentarer tilbake som `tips` på steg 2:
  «Kommentarer på avvik er skjult. Medisinromsansvarlig og/eller leder kan se dem og saksbehandler
  avvikene.» Anbefalt.
- **b)** Bytt til et spørsmål om de to fanene, når fanenavnene er avklart.

Spørsmålet står i README («Spørsmål til fagekspertene»). Skriv der hva du valgte.

### Andre steder

Grep etter `OVERSIKT` i `content/` igjen. Det skal ikke stå igjen noe (Case 8 ble rettet i økt 01,
og innholdet i Case 8 ses over i økt 10).

## Test

- `index.html?dev=1#case-5/1` til `/4`: merkelappen viser «Signeringsoppgaver og nylig historikk»,
  tekstene bruker det nye navnet, AVKLARES vises der vi ikke vet.
- QR-arket for Case 5.

## Ferdig når

- [ ] Ingen «OVERSIKT» i kurset
- [ ] To faner, Etterkommentarer og Dobbeltsignering
- [ ] Kontrollspørsmålet har grunnlag i teksten
- [ ] Haket av i [README.md](README.md)

Forslag til commit: `R2: Case 5 skrevet om til Signeringsoppgaver og nylig historikk`
