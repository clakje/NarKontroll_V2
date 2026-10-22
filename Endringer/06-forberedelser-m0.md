# Økt 06 · Forberedelser (M0)

Les [README.md](README.md) først. Økt 02 bør være gjort (fast oppsett).

**Kilde:** `bilder/lysbilde-07.png`.

## Mål

M0 får to sider: først hva deltakeren trenger, så hvordan appen gjøres klar. Ingen av sidene må rulles
for å komme til knappen videre.

## Fagekspertenes kommentarer (lysbilde 7)

- Tittel: **Klargjør appen for opplæringen**
- «Teksten til venstre kan komme på en egen side 1 i denne modulen» (boksen «Du gjør kurset på PC og
  bruker den ekte appen på mobilen …»).
- Punkt 1: legg til **Ikke logge inn!**
- Punkt 2 (til merknaden): «I opplæringsmodus tæpper du med eget ansatt-ID-kort på mobiltelefonen både
  for signering (SIGN1) og for dobbeltsignering (SIGN2). Ekte registreringer på ekte lagre må signeres
  av to ulike brukere. Knappene i startmenyen er deaktivert fordi det ikke er angitt et lager.»
- Punkt 4: «Når det er angitt lager, får knappene farger.»
- Punkt 5 (til merknaden): «Opplæringsmodus er markert med en oransje stripe øverst i appen. Knappene
  har nå fått farge. QR-kodene i dette kurset for legemidler og pasienter er ikke ekte koder, og kan
  ikke brukes utenfor opplæringsmodus. Se på appens startmeny og oppsettet for de ulike knappene.»
- «Knappen "Fullfør modulen" ligger under "skrolling", bør komme på en side!»

## Endringer (`content/kurs.js`, modulen `m0-velkommen`)

### 1. Tittel

- `tittel: "Klargjør appen for opplæringen"`
- `kortTittel: "Start her!"` (fra økt 05, sjekk at den finnes)
- `eyebrow` er fortsatt «Forberedelser».
- Fjern `kortTekst` fra modulen (den blir side 1).

### 2. Side 1 (nytt steg, `type: "info"`)

```js
{
  type: "info",
  tittel: "Dette trenger du",
  tekst: "Du gjør kurset på PC og bruker den ekte appen på mobilen.",
  punkter: [
    "Mobilen med **NarKontroll** installert",
    "ID-kortet ditt",
    "Ca. 20 minutter"   // tiden må måles med en testperson, se README.md i prosjektroten
  ]
}
```

Høyre kolonne viser den rolige flaten (økt 02).

### 3. Side 2 (dagens steg, `type: "registrer"`)

Nye tekster i `rekke`. Bruk `merknad` for den lille teksten under punktet, som i dag.

| Punkt | `tekst` | `merknad` |
|---|---|---|
| 1 | «Start **NarKontroll**-appen på mobilen. **Ikke logg inn.**» | – |
| 2 | «Trykk på ikonet øverst til høyre for å gå til **Opplæringsmodus**. {ikon:opplaeringsmodus}» | «I Opplæringsmodus tæpper du med ditt eget ID-kort både for signering (SIGN1) og dobbeltsignering (SIGN2). Ekte registreringer på ekte lagre må signeres av to ulike brukere. Knappene i startmenyen er grå fordi du ikke har valgt lager ennå.» |
| 3 | «Spør appen om å få bruke kameraet? Trykk **Tillat**.» | «Dette skjer bare første gang du åpner appen.» |
| 4 | «Trykk på **Angi lager**, og skann lagerkoden.» (`kode: "LAGER-01"`) | «Når lageret er valgt, får knappene farger.» |
| 5 | «Nå er du i **Opplæringsmodus**. Øverst står lageret: **TEST Medisinrom 1**. Se på startmenyen og hvordan knappene er satt opp.» | «Opplæringsmodus er markert med en oransje stripe øverst i appen. QR-kodene i kurset er ikke ekte koder, og virker bare i Opplæringsmodus.» |

Teksten «I casene gjør du registreringene i appen, og kurset viser kodene du skal skanne.» kan
flyttes til side 1 som siste setning i `tekst`. «Ser du noe annet? Gjør punktene over på nytt.» kan
fjernes hvis det trengs plass.

Skrivestil: «deaktivert» er et teknisk ord. «Grå» er det deltakeren ser. Behold betydningen fra
fagekspertene.

### 4. Plass: «Fullfør modulen» uten rulling

Side 2 bruker i dag `iKortet: true` (radene i stegkortet, én kolonne, 760 px), og knappen havner
under kanten i 1280 × 650. Velg én av disse, og test:

- **a)** Fjern `iKortet`. Radene står i skannesonen til høyre som i casene (med QR-koden for lageret),
  og venstre kolonne har en kort tittel og tekst. Da får M0 samme oppsett som casene (økt 02). Anbefalt.
- **b)** Behold `iKortet`, men stram inn: mindre QR-kode (`clamp` med `vh`), merknadene tettere.

## Test

- `index.html?dev=1#m0-velkommen/1` og `/2` i 1280 × 650, 1536 × 730 og 1920 × 940:
  «Fullfør modulen» synlig uten å rulle på begge sidene.
- QR-koden for lageret er minst 120 px (kan skannes fra ca. 20 cm).
- Ikonet for Opplæringsmodus vises fortsatt i punkt 2.
- QR-arket for M0 (knappen «QR-ark») ser greit ut med to steg.

## Ferdig når

- [x] Ny tittel, to sider, nye tekster
- [x] Ingen rulling for å nå «Fullfør modulen» (valgte a: radene i skannesonen som i casene)
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: M0 «Klargjør appen for opplæringen» på to sider uten rulling`
