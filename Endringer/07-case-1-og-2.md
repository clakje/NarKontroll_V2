# Økt 07 · Case 1 og Case 2

Les [README.md](README.md) først. Økt 01–03 bør være gjort.

**Kilde:** `bilder/lysbilde-08.png`, `bilder/lysbilde-09.png`, `bilder/lysbilde-11.png`,
`bilder/lysbilde-13.png`. Lysbilde 10, 12 og 14 har ingen kommentarer.

## Mål

Det som gjentar case-boksen eller sier det samme to ganger, fjernes. Deltakeren ser casen, kodene og
knappen videre.

## Case 1 (`case-1` i `content/kurs.js`)

### Steg 1 «Registrer uttaket i appen»: slett boksen (lysbilde 8)

Fagekspertene vil fjerne stegkortet med «BESKRIVELSE · Registrer uttaket i appen · Gjør registreringen
på mobilen …» og tipset om mengde. Case-boksen over sier allerede hva som skal gjøres, og radene til
høyre viser hvordan.

Lag dette som en generell mulighet, for Case 3 trenger det samme (økt 08):

- Nytt felt på et steg: `utenKort: true`. Da viser `veilederHtml` ikke `stegtype`, tittel, tekst,
  punkter eller tips. Stegtelleren («Steg 1 av 4» og strekene) står fortsatt, i et lavt kort eller
  rett over navigasjonsraden, så deltakeren ser hvor langt de har kommet.
- Skjermleseren må fortsatt få en overskrift for steget. Behold `tittel` i `kurs.js` og vis den som
  `.sr`, slik `iKortet` gjør i dag.
- Beskriv feltet i kommentaren øverst i `kurs.js`.
- QR-arket (`arkHtml`) bruker tittel og tekst. Sjekk at ruten for steget fortsatt gir mening.

Tipset om mengde («Mengden kan være et desimaltall … ml for store miksturflasker …») forsvinner med
boksen. Desimaltall øves i Case 7, og enheter i Case 4.

### Steg 2 «Dobbeltkontroll: med en gang eller senere?» (lysbilde 9)

Case-boksen på dette steget er fjernet i økt 02. Legg til fagekspertenes tekst i faktapanelet, i
raden «Kan utsettes»:

> «For eksempel UTTAK til pasient uten avvik. Utsetter du dobbeltsigneringen, får andre brukere som er
> innlogget på samme lager, et varsel.»

### Steg 4, kontrollspørsmålet

Teksten ble endret i økt 01 (Signeringsoppgaver og nylig historikk). Les forklaringen på nytt etter
økt 03: den vises nå med en gang, også etter feil svar. Røper den fasiten, se økt 03.

## Case 2 (`case-2`)

### Steg 2 «Dobbeltsigner avviket med en gang» (lysbilde 13)

- Slett linjen «Tæpp ID-kortet to ganger: først som bruker 1, så som bruker 2.» (`tekst`). Steget
  har fortsatt tittel og de tre punktene.
- «Trenger vi denne infoen her??» står på ID-kortet i skannesonen. Tolkning: tegningen av ID-kortet
  trengs ikke når deltakeren har signert før (Case 1 viste den, med hvor leseren sitter).
  På signer-steg **uten** `forklar` viser skannesonen bare:
  - «Tæpp kortet mot baksiden av telefonen, to ganger.» (eller «… telefonen.» når `antall` er 1)
  - indikatorene «Bruker 1» og «Bruker 2»
  - lenken «Hvor sitter leseren?»

  Gjelder også Case 7 steg 2. I utviklermodus er det i dag et klikk på ID-kortet som simulerer
  tæpp (`simulerTaepp`). Gjør indikatorene «Bruker 1»/«Bruker 2» klikkbare i utviklermodus i stedet.
  Case 8 steg 1 bruker `panel: { type: "idkort" }` (kontroller kollegaens kort) og skal beholde kortet.

## Test

- `index.html?dev=1#case-1/1`: ingen beskrivelsesboks. Stegtelleren synes. Radene og QR-kodene til høyre.
  Skjermleseren leser «Registrer uttaket i appen».
- `#case-1/2`: teksten om varsel står i «Kan utsettes».
- `#case-2/2`: ingen linje om bruker 1 og 2, ingen ID-kort-tegning, og tæpp kan simuleres.
- `#case-1/3`: ID-kortet og telefonene vises fortsatt (første signering, `forklar`).
- QR-ark for Case 1 og 2 ser greit ut.

## Ferdig når

- [x] `utenKort` finnes og brukes på Case 1 steg 1
- [x] Varsel om utsatt dobbeltsignering i Case 1 steg 2
- [x] Case 2 steg 2 uten den ekstra linjen og ID-kort-tegningen
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: Case 1 og 2 uten gjentakelser, varsel ved utsatt dobbeltsignering`
