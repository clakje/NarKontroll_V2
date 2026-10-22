# Økt 08 · Case 3 og Case 4

Les [README.md](README.md) først. Økt 07 må være gjort (feltet `utenKort`).

**Kilde:** `bilder/lysbilde-15.png`, `bilder/lysbilde-17.png`, `bilder/lysbilde-18.png`,
`bilder/lysbilde-19.png`. Lysbilde 16, 20 og 21 har ingen kommentarer.

## Case 3 (`case-3` i `content/kurs.js`)

### Steg 1 «Legg tilbake fentanylplasteret» (lysbilde 15)

«Denne boksen kan tas bort.» Sett `utenKort: true` på steget. Behold `tittel` (for skjermleseren og
QR-arket).

Les teksten som forsvinner: «Neste dose var allerede klargjort og tatt ut av narkotikaregnskapet. Den
skal legges tilbake.» Står ikke dette tydelig nok i case-boksen (`kortTekst`), skriv det inn der med
én kort setning. Case-boksen vises bare på steg 1 (økt 02), og det er nettopp dette steget.

Tipset «Følg appen på mobilen. Her i kurset trenger du bare kodene.» forsvinner også. Det er greit.

### Steg 2 «En løs tablett i medisintrallen»

Ingen kommentarer. Ingen endring.

## Case 4 (`case-4`)

### Steg 1 «Registrer mottaket» (lysbilde 17)

I `rekke`:

- **Slett** rad 2 («Slå på bryteren **Nytt mottak på samme lager**. Da kan du registrere flere
  legemidler etter hverandre.»).
- Rad 3 (Sobril 15 mg, 50 stk) får ny tekst etter fagekspertene:
  «Skann, og skriv inn mengden. Før du signerer, slår du på bryteren **Nytt mottak på samme lager**,
  fordi du skal registrere flere mottak etter hverandre.»
- Rad 4 (Cosylan) er uendret: «Skann, skriv inn mengden, og signer og lagre.»

Bryteren slås altså på i oppsummeringen før signering, ikke før skanning.

### Steg 2 «Registrer resten av mottaket» (lysbilde 18)

- Metadon Nordic Drugs mikst: `enhet: "ml"` (fagekspertene har skrevet «ml» over AVKLARES-merkelappen).
- Mengden står som `2`. Med ml som enhet er 2 ml lite for en miksturflaske. Sett
  `merknad: "Flytende, registreres i ml. [AVKLARES: mengde i ml, for eksempel 2 flasker × 100 ml]"`
  og la `mengde` stå til fagekspertene svarer. Spørsmålet står allerede i README («Spørsmål til fagekspertene»).
- Merknaden «Metadon kan være et unntak fra hovedregelen. Sjekk enheten i appen.» fjernes, fordi
  enheten nå er kjent og følger hovedregelen.

### Steg 3 «To tabletter har gått ut på dato» (lysbilde 19)

«Sykehusapoteket» og «prosedyre» ble rettet i økt 01. Sjekk at tipset nå sier «RETUR til apoteket
… etter lokale prosedyrer».

### Steg 4 og 5, kontrollspørsmålene

Ingen kommentarer. Les forklaringene etter økt 03-endringen (vises også etter feil svar).

## Test

- `index.html?dev=1#case-3/1`: ingen beskrivelsesboks, case-boksen gir nok informasjon.
- `#case-4/1`: tre rader, bryteren nevnt i rad 2 (tidligere rad 3).
- `#case-4/2`: Metadon i ml, AVKLARES om mengde.
- QR-ark for Case 3 og Case 4.

## Ferdig når

- [x] Case 3 steg 1 uten boks
- [x] Case 4: bryteren slås på før signering, Metadon i ml
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: Case 3 uten beskrivelsesboks, Case 4 med bryteren før signering og Metadon i ml`
