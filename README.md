# NarKontroll opplæring · Konsept A «Veileder ved siden av»

Et guidet kurs på PC mens deltakeren bruker den ekte NarKontroll-appen på mobilen.
Kurset viser oppgaven til venstre. Til høyre, i «skannesonen», står det deltakeren skal gjøre
i appen, med kodene som skal skannes. Se `Losningsforslag.md` del 4 for idé og avgrensning.

> Alt faginnhold, alle koder og all beholdning er **dummy**. Tekst merket
> `[AVKLARES: …]` vises som gul merkelapp i kurset.

## Kom i gang

| Hva | Hvordan |
|---|---|
| Åpne kurset | Dobbeltklikk `index.html`. Kurset går i lokal testmodus og lagrer fremdriften i nettleseren |
| Utviklermodus | `index.html?dev=1`, eller <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>. Et klikk på en QR-kode tolkes som «skannet», og et klikk på ID-kortet (eller «Bruker 1»/«Bruker 2») som «tæppet». Panelet nede til venstre lar deg hoppe mellom moduler, nullstille fremdriften, merke del A–C eller alle moduler som fullført, og se registrene over skjermbilder, AVKLARES-punkter og koder |
| Slå av utviklermodus | `index.html?dev=0` |
| Introfilm | Spilles når kurset åpnes, og går rett over i hovedmenyen. `?intro=0` hopper over, `?intro=1` viser den også i utviklermodus |
| Gå rett til et steg | `index.html#case-1/3` (modul-ID / stegnummer). `index.html#meny` åpner hovedmenyen |
| Lag SCORM-pakken | `python scripts/pakk-scorm.py` gir `dist/NarKontroll-KonseptA-scorm12.zip` |

## Filer

```
index.html            startfil, ikonsett og logomerke (inline SVG)
imsmanifest.xml       SCORM 1.2. Fillisten oppdateres av pakkeskriptet
css/app.css           tokens (lys og mørk), layout, skannesone, utskrift
js/scorm.js           felles SCORM 1.2-wrapper med lokal testmodus
js/app.js             konseptets logikk
js/vendor/qrcode.js   QR-generator (Kazuhiko Arase, MIT), lagt lokalt
content/kurs.js       moduler, steg og gruppene i hovedmenyen (felles innholdsmodell)
content/koder.js      QR-register. Bytt bare `payload` når de ekte kodene kommer
content/skjermer.js   register over skjermbilder. Tomt: kurset viser ikke bilder av appen (G-04)
assets/               logo, ikon for Opplæringsmodus, skjermbilder og introfilm (video/introfilm.mp4)
scripts/pakk-scorm.py lager zip-filen
Endringer/            oppgavene fra tilbakemeldingsrunde 2, én fil per økt (kommer ikke med i pakken)
```

### Felt i `kurs.js`

Øverst i `content/kurs.js` står alle feltene. Disse kom med i runde 2:

| Felt | Hvor | Hva |
|---|---|---|
| `del` | gruppe i `KURS.grupper` | «A»–«D». Vises som nummer foran gruppenavnet i hovedmenyen |
| `valgfri` | gruppe og modul | `true` på del D og modulene der. Teller ikke med for at kurset er fullført |
| `kortTittel` | modul | kortere tittel som bare brukes på kortet i hovedmenyen (M0: «Start her!») |
| `utenKort` | steg | stegkortet viser bare stegtelleren, og tittelen leses bare av skjermleseren. Brukes når case-boksen og radene til høyre sier det kortet ville sagt (Case 1 og Case 3, steg 1) |
| `panel.tekst` | steg med `panel: { type: "idkort" }` | teksten under ID-kortet i skannesonen (Case 8) |

`KURS.hovedmeny` har tittelen, ingressen (fire korte linjer) og overskriftene over del A–C og del D.

## Innhold i denne versjonen

**Runde 1.** Kurset ble kortet ned etter de første tilbakemeldingene fra fagekspertene, fra 130 til 34 steg.

- Infoboksen «Før du starter» er borte. Kurset går rett fra introfilmen til hovedmenyen.
- M1 «Bli kjent med startmenyen» er slettet. Deltakeren lærer knappene ved å bruke dem i casene.
- M2 «Signering og dobbeltkontroll» er ikke lenger egen modul. Innholdet står i Case 1 (når dobbeltkontroll
  kreves, og å utsette), Case 2 (avvik, bruker 2, tæpp to ganger) og Case 5 (ikke overlat det til neste skift).
- Hver registrering står på én side (stegtypen `registrer`): det deltakeren gjør i appen, i appens rekkefølge,
  med QR-kodene og mengden på samme side.
- Hvor NFC-leseren sitter på telefonen, forklares første gang deltakeren signerer (Case 1). Senere ligger
  forklaringen bak lenken «Hvor sitter leseren?».
- Case 2 er ett uttak av Oxynorm, der deltakeren teller og oppdager at det mangler én (avvik).

**Runde 2.** Fagekspertene gikk gjennom kurset på nettet og skrev kommentarene i
`Tilbakemeldinger - NarKontroll (1).pptx` (47 lysbilder). Endringene er delt opp i oppgaver i `Endringer/`,
med lysbildene i `Endringer/bilder/`. `Endringer/README.md` har status for hver oppgave og listen over
spørsmål til fagekspertene. Kommentarer i koden som viser til runde 2, er merket `R2-<lysbilde>`.

- **Ord:** «apoteket» (ikke «Sykehusapoteket»), «etter lokale prosedyrer», og knappen som het OVERSIKT, heter
  **Signeringsoppgaver og nylig historikk**, som i appen 2.1. Kurset anbefaler å skanne hele veien. Manuell
  liste er bare for koder som mangler eller ikke kan skannes.
- **Hovedmenyen** har en ingress på fire linjer, og modulene er delt i del A–D (se Design).
- **M0** heter «Klargjør appen for opplæringen» og har kortet «Start her!». Den har to sider: hva du trenger,
  og hvordan appen startes i Opplæringsmodus (radene står i skannesonen, som i casene).
- **Case 1–9** er rettet etter kommentarene. Nye titler: «UTTAK med avvik», «APOTEKET: mottak og retur»,
  «OVERFØRING til/fra eget underlager» (med TILBAKEFØRE), «KASSERE og ETTERKASSERE», «LÅN til/fra annen enhet».
  Case 5 beskriver Signeringsoppgaver og nylig historikk med to faner.
- **Nye moduler:** TIPS «Viktig info» (del B), og fem valgfrie moduler i del D: Akuttvogn, Rette opp feil,
  Glemmekort, Kjekt å vite og Bidra til forbedring. Innholdet er stikkord fra fagekspertene og venter på svar.
- **M13** heter «Logg inn med ekte bruker», og steg 1 har samme tittel. Kurset viser ingen poengsum til slutt.

**Omfang nå:** 18 moduler. 13 er obligatoriske (del A–C) med til sammen 39 steg, og 5 er valgfrie (del D) med
7 steg. Kurset har 7 kontrollspørsmål. Ingen spør om ny beholdning: deltakeren sammenligner beholdningen i appen
med det de teller. Kurset viser ingen bilder av appen.

Målet er 15–20 minutter for del A–C. M0 sier ca. 20 minutter. Det må måles med en testperson.

M0 og Case 1–4 bygger på manus. Case 5–9, TIPS og del D er merket **Utkast, ikke faglig godkjent**.

## SCORM

- `lesson_status` er `incomplete` til alle **obligatoriske** moduler (del A–C) er fullført, og blir da
  `completed`. Del D teller ikke med. Siste steg i Avslutning har knappen «Fullfør kurset».
- `score.raw` er andelen kontrollspørsmål som er besvart riktig på **første forsøk** (0–100). Den settes først
  når deltakeren har svart på minst ett spørsmål. Den sendes til LMS-et, men vises ikke i kurset.
- `suspend_data` er kompakt JSON (ca. 520 tegn når del A–C og én valgfri modul er gjennomført, grensen er 4096).
  Et svar som er endret, lagres som tredje tall i svaret, så poengsummen fortsatt bygger på første valg.
- `lesson_location` er `<modul-id>:<steg>`. Kurset fortsetter der deltakeren slapp.
- Ny kursversjon (`KURS.versjon`) nullstiller lagrede stegnummer og svar, men fullførte moduler står seg.
- Manifestet har ingen `masteryscore`, fordi kravet til bestått ikke er avklart.

Test i SCORM Cloud før opplasting til sykehusets LMS.

## Design

Designet er laget med skillen `apple-design` (HIG som grunnlag, WCAG 2.1 AA som krav).

- **Oppgaven på hver skjerm:** si hva deltakeren skal gjøre nå, og vise det som skal skannes.
  Venstre kolonne har stegkortet. Høyre kolonne viser bare det steget trenger. På et registrer-steg er det
  hele registreringen som nummererte rader.
- **Låste kolonner:** alle steg i alle moduler har to like brede kolonner med samme plassering, så venstre
  kolonne aldri flytter seg. Steg uten noe å skanne (info, kontrollspørsmål, obs) har en rolig flate til høyre
  («Ingen skanning i dette steget», «Velg ett svar»). Case-boksen med situasjonen vises bare på steg 1. Senere
  står «Case 1» ved appmerket øverst.
- **Toppfeltet** er lavere enn før. Knappene er fortsatt minst 44 px høye.
- **Ingen «← → for å bla».** Piltastene blar fortsatt.
- **PC først:** de fleste tar kurset på PC. På lave skjermer (16" bærbar, 650–900 px høyde) strammes
  avstandene, og QR-kodene i et registrer-steg skaleres med høyden, så steget får plass. Testet i økt 11:
  alle steg i del A–C og én valgfri modul, og hovedmenyen etter hver fullførte modul. Hovedmenyen også i
  mørk modus.

  | Størrelse | Hovedmenyen | Stegene |
  |---|---|---|
  | 1920 × 940 | ingen rulling | ingen rulling |
  | 1536 × 730 | ingen rulling | ingen rulling |
  | 1280 × 650 | ingen rulling | knappen videre synes på alle steg. Steg 1 i Case 2, 5 og 8 ruller 1–17 px, slik at statuslinjen under knappen kommer frem |

- **Kontrollspørsmål:** deltakeren får svar med en gang («Riktig» med forklaring, eller «Ikke riktig. Prøv et
  annet svar.»). Fasiten vises ikke etter et feil svar. Svaret kan endres, og knappen **Fortsett** virker så
  snart et svar er valgt. Kurset viser ingen summering eller poengsum.
- **Navigasjon:** kurset åpner i **hovedmenyen**. Øverst står tittelen og en ingress på fire linjer. Under
  overskriften **Obligatoriske moduler** står del A «Kom i gang» (M0, kortet «Start her!»), del B «Caser»
  (Case 1–9 og TIPS) og del C «Til slutt» (Gode råd og Avslutning). Under **Valgfrie moduler** står del D
  «Fordypning» med fem moduler. Fra 1000 px bredde står gruppenavnet med bokstav og «x av y» til venstre for
  kortene. Casekortene har appknappens farge øverst. En fullført modul får **grønt kort med hake**
  (Alternativ 1 på lysbilde 4). Anbefalt neste modul har ramme, og en valgfri modul anbefales først når del
  A–C er fullført. Nederst er en smal fremdriftslinje som teller bare obligatoriske moduler, med én knapp videre
  («Start kurset», «Fortsett: …» eller «Neste: …»). Etter hver modul kommer deltakeren tilbake til hovedmenyen.
  Knappen «Hovedmeny» står alltid i toppfeltet, og på første steg i en modul. Rekkefølgen og gruppene står i
  `KURS.grupper` i `kurs.js`.
- **To utforminger av hovedmenyen:** bryteren **Kort | Liste** ved siden av tittelen bytter mellom dem. Valget
  huskes i nettleseren (`localStorage`, `nk-menyutforming`), og «Kort» er standard. «Kort» er menyen over.
  «Liste» har del A–C som lister i hvert sitt kort (statusmerke, casenummer, tittel og «Fullført» eller
  «x av y steg»), og anbefalt neste rad er fremhevet med «Fortsett» eller «Start». Fremdriften med knappen videre
  står øverst til høyre, og del D står i en smal kolonne under den (`listeTekst` på gruppen). Listemenyen ruller
  på lave skjermer. Under 1000 px står alt i én kolonne.
- **Signaturelementet** er skannesonen: en rolig mintflate med QR-kodene, som kamerarammen i appen.
  Resten av siden er stille.
- **Farger** fra logoen: teal `#186F7B` (5,8:1 på hvitt) og mint `#79E3E0` (flater og markering).
  Appens knappefarger er merkefarger, og der hvit tekst ga for lav kontrast, er de mørknet:
  APOTEKET `#1388FF` → `#0A6FD6` (4,9:1), KASSERE/LÅN `#FF383D` → `#D42A2F` (5,0:1),
  OVERFØRE `#AE7F60` → `#8A5E40` (5,6:1). Knappens navn står alltid ved siden av fargen.
- **Lys og mørk modus** følger systeminnstillingen. Kurset har ingen egen bryter (HIG `dark-mode.md`).
  QR-kodene ligger alltid på hvitt, slik at de kan skannes.
- **Tilgjengelighet:** systemfont, 17 px brødtekst, trykkflater på minst 44 × 44 px, synlig fokus,
  «Hopp til innholdet», fokus flyttes til nytt steg, og endringer leses opp. Piltastene blar.
  Kurset tar hensyn til redusert bevegelse, redusert gjennomsiktighet og Windows' høykontrastmodus.
- **Introfilm:** `assets/video/introfilm.mp4` (4 s, uten lyd, H.264 Main med «faststart», så den kan starte
  før hele filen er lastet) spilles over hovedmenyen hver gang kurset åpnes. Etterpå kommer hovedmenyen.
  Den har lys flate også i mørk modus, slik som filmen. «Hopp over», <kbd>Esc</kbd> eller klikk ved
  siden av filmen lukker den, og fokus går til hovedmenyen. Står filmen stille i 3 sekunder (starter ikke,
  eller henger på første bilde, slik den gjorde i Arbeidsflate), lukkes den. Filmen vises også når Windows
  har slått av animasjoner (redusert bevegelse), fordi fagekspertene vil ha den på PC. Den vises ikke i
  utviklermodus.
- **Smal skjerm:** én kolonne, og kurset forklarer at det gjøres best på PC, med knapp til QR-arket.
- **QR-ark (case-ark):** knappen «QR-ark» skriver ut ett A4-ark per modul med koder, satt opp som en tegneserie
  for dem som gjør kurset sammen. Øverst står situasjonen med appknappen i appens farge. Deretter kommer hvert steg
  i en egen rute («Steg 1», «Steg 2» …), tre i bredden. Rutene har QR-koden, mengden eller en enkel tegning
  (appknappen, ID-kortet eller telefonen). Kontrollspørsmålene blir ruter med «Snakk sammen» og avkrysningsbokser,
  og fasiten står opp ned nederst på arket. Den siste ruta i en ufullstendig rad strekkes ut, med bildet til venstre.
  Alt hentes fra `kurs.js` (`arkHtml()` i `app.js`), også tekst som ikke vises på skjermen (for eksempel på steg
  med `utenKort`). De lengste casene fyller to sider.

## Åpne punkter som påvirker dette konseptet

- Beholdningen i appens Opplæringsmodus må stemme med kurset, og vi må vite når den nullstilles.
- De ekte QR-kodene (`koder.js`) fra apputvikler, også lagerkoden `LAGER-01` i M0.
- Spørsmålene fra runde 2 står i «Spørsmål til fagekspertene» i `Endringer/README.md`. Den listen kan sendes
  til fagekspertene.
- Hele listen over AVKLARES finner du i utviklermodus under **AVKLARES**.
