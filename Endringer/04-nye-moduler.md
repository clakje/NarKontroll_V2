# Økt 04 · Nye moduler: TIPS og valgfrie moduler (del D)

Les [README.md](README.md) først.

**Kilde:** `bilder/lysbilde-03.png` (hovedmenyen med del A–D) og lysbilde 41–45 (tekst, skrevet av under).

## Mål

Modulene som hovedmenyen i økt 05 skal vise, finnes i `kurs.js`: et nytt kort «TIPS: Viktig info»
blant casene og fem valgfrie moduler i del D. Kurset regnes som fullført når del A, B og C er
fullført. Del D er valgfri.

Innholdet er utkast. Det meste må fagekspertene skrive. Lag modulene med det vi har, og merk resten
`[AVKLARES: …]` og `utkast: true`.

## Hva fagekspertene har skrevet

Ingressen på hovedmenyen (lysbilde 3) sier: «Del A, B og C omhandler grunnleggende funksjoner og er
obligatorisk for alle app-brukere. Del D er valgfri, men også anbefalt for alle.»

Del B «Caser» har et tiende kort: **TIPS** med teksten «Viktig info». Innholdet er ikke beskrevet.

Del D «Valgfrie moduler» har fem kort, i denne rekkefølgen:

| Kort | Stikkord fra lysbilde 41–45 (tolkning: lysbilde ↔ kort) |
|---|---|
| Akuttvogn | Lysbilde 42: «Etterfylle etter bruk til pasient vs. Etterfylle etter datoutløp» |
| Rette opp feil | Lysbilde 41: «Dekke over andres feil · Angiveri-perspektiv: Rapportere andres forglemmelser · Spesielt viktig at MOTTAK stemmer for riktig tall i månedsrapport · Dokumentere i sanntid vs. etterregistrere» |
| Glemmekort | Lysbilde 43: «Nullstille eget ansattkort» (resten er plassholdertekst) |
| Kjekt å vite | Lysbilde 44: bare plassholdertekst |
| Bidra til forbedring | Lysbilde 45: «narkontroll@so-hf.no direkte fra appen eller på mail» |

Koblingen mellom lysbilde og kort er en tolkning. Lysbilde 41 og 42 står i omvendt rekkefølge av
kortene. Skriv tolkningen som en kommentar i `kurs.js`.

## Endringer

### 1. Datamodellen (`content/kurs.js`, kommentaren øverst)

- Nytt felt på en modul: `valgfri: true`. Valgfrie moduler teller ikke med for at kurset er fullført.
- Nytt felt på en modul: `kortTittel`, en kortere tittel som bare brukes på kortet i hovedmenyen
  (økt 05 bruker den til «Start her!» på M0). Uten `kortTittel` brukes `tittel`.
- Grupper (`KURS.grupper`): nytt felt `del` («A», «B», «C», «D») og `valgfri: true` på del D.
  Selve visningen lages i økt 05.

### 2. Ny modul «TIPS» (`content/kurs.js`)

Legg den etter Case 9, og i gruppen «Caser» som siste kort.

```js
{
  id: "tips",
  nr: "M11b",                  // velg et nr som passer, nr brukes ikke i visningen
  eyebrow: "Tips",
  tittel: "Viktig info",
  utkast: true,
  kortTekst: "[AVKLARES: hva skal stå i TIPS? Fagekspertene har bare skrevet «Viktig info»]",
  steg: [
    { type: "info", tittel: "Viktig info", tekst: "[AVKLARES: innhold]" }
  ]
}
```

### 3. Fem valgfrie moduler (`content/kurs.js`)

Legg dem etter M13 «Avslutning», med `valgfri: true` og `utkast: true`. Én `info`-side per stikkord
holder. Eksempler:

- **Akuttvogn** (`id: "d-akuttvogn"`, eyebrow «Valgfri»): ett steg «Etterfylle akuttvognen» med to
  punkter: «Etterfylle etter bruk til pasient» og «Etterfylle etter at holdbarheten er utløpt».
  `[AVKLARES: hvilke knapper i appen brukes, og hva er forskjellen i registreringen?]`
- **Rette opp feil** (`d-rette-opp-feil`): steg «Ikke dekk over andres feil» (rapporter forglemmelser,
  det er ikke angiveri), steg «MOTTAK må stemme» (riktig tall i månedsrapporten), steg «Dokumenter i
  sanntid» (sanntid vs. etterregistrering). Hvert steg `[AVKLARES: tekst]`.
- **Glemmekort** (`d-glemmekort`): steg «Nullstille eget ansattkort». `[AVKLARES: fremgangsmåte]`
- **Kjekt å vite** (`d-kjekt-a-vite`): ett steg med `[AVKLARES: innhold]`.
- **Bidra til forbedring** (`d-forbedring`): steg «Si fra om feil og forslag» med tekst om at
  forslag sendes til **narkontroll@so-hf.no**, direkte fra appen eller på e-post.
  `[AVKLARES: hvor i appen?]`

Skriv tekstene kort og i samme stil som casene (korte setninger, aktiv form, **fet** for knappenavn).

### 4. Fullført kurs (`js/app.js`)

- `antallFerdig()` og alle steder som sammenligner med `MODULER.length` (`lagre()` for
  `lesson_status`, `fremdriftHtml()`, `navradHtml()` for «Fullfør kurset», `resultatHtml` hvis den
  fortsatt finnes): bruk antallet **obligatoriske** moduler (ikke `valgfri`).
- `erSisteModul()` brukes til «Fullfør kurset»-knappen. Den skal gjelde siste obligatoriske modul
  (M13), ikke siste modul i listen, nå som de valgfrie står etter.
- `anbefaltNeste()`: anbefal aldri en valgfri modul før alle obligatoriske er fullført.
- Fullførte valgfrie moduler lagres i `suspend_data` som de andre. Sjekk at lengden fortsatt er godt
  under 4096 tegn.

## Ikke gjør

- Ikke lag hovedmenyens nye utseende. Det er økt 05. Det holder at modulene vises i dagens meny
  (legg dem i en midlertidig gruppe hvis det trengs).

## Test

- `index.html?dev=1`: de nye modulene kan åpnes fra utviklerpanelet, og AVKLARES vises som gule merkelapper.
- Fullfør alle obligatoriske moduler (utviklerpanelet kan hoppe): `lesson_status` blir `completed`
  uten at del D er gjort.
- `suspend_data` (utviklerpanelet) med alt fullført: under 4096 tegn.

## Ferdig når

- [x] TIPS og fem valgfrie moduler finnes i `kurs.js`
- [x] Kurset er fullført uten del D
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: nye moduler TIPS og valgfri del D (utkast), del D teller ikke for fullført`
