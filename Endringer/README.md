# Endringer etter tilbakemeldingsrunde 2

Fagekspertene har gått gjennom kurset på https://clakje.github.io/NarKontroll/ og skrevet
tilbakemeldingene i `Tilbakemeldinger - NarKontroll (1).pptx` (47 lysbilder). Endringene er delt opp
i små økter. **Én økt = én ny chat.** Hver fil er skrevet slik at du kan gjøre den ferdig uten at
kontekstvinduet blir fullt.

## Slik gjør du en økt

1. Start en ny chat og skriv for eksempel: *«Gjør Endringer/03-kontrollsporsmal.md»*.
2. Claude leser denne README-en og økt-filen, og ser på bildene i `Endringer/bilder/` som filen viser til.
3. Claude gjør endringene, tester dem i nettleseren (helst `index.html?dev=1`) og haker av i
   statuslisten under.
4. Du ser over endringene og committer (eller ber Claude committe).

Ta øktene i rekkefølge. Senere økter bygger på de tidligere, særlig 01–05.

## Status

- [x] [01 Gjennomgående tekst og appknapper](01-gjennomgaende-tekst.md) (lysbilde 2, 3, 4, 22, 27)
- [x] [02 Fast oppsett på stegsidene](02-fast-oppsett.md) (lysbilde 3, 8, 9)
- [x] [03 Kontrollspørsmål med umiddelbar respons](03-kontrollsporsmal.md) (lysbilde 11, 40)
- [x] [04 Nye moduler: TIPS og valgfrie moduler (del D)](04-nye-moduler.md) (lysbilde 3, 41–45)
- [x] [05 Hovedmenyen med del A–D (Alternativ 1)](05-hovedmeny.md) (lysbilde 3, 4)
- [x] [06 Forberedelser (M0)](06-forberedelser-m0.md) (lysbilde 3, 7)
- [x] [07 Case 1 og Case 2](07-case-1-og-2.md) (lysbilde 8–14)
- [x] [08 Case 3 og Case 4](08-case-3-og-4.md) (lysbilde 15–21)
- [x] [09 Case 5: Signeringsoppgaver og nylig historikk](09-case-5-signeringsoppgaver.md) (lysbilde 22–25)
- [x] [10 Case 6–9](10-case-6-til-9.md) (lysbilde 26–33)
- [x] [11 Avslutning, README og SCORM-pakke](11-avslutning-og-pakke.md) (lysbilde 34–40)

## Valg som er tatt

- **Hovedmenyen bruker Alternativ 1** (lysbilde 4): case-kortene står i et eget rutenett, ikke oppå
  eller ved siden av et bilde av appens startmeny. En fullført case får grønn hake og lys grønn
  bakgrunn. Hovedmenyen viser ikke noe bilde av startmenyen. Alternativ 2 (tall ved siden av
  knappene) og 3 (tall på knappene) er valgt bort.
- **Ingen bilder av appen** i kurset, som før.
- Alt faginnhold er fortsatt **dummy**. Det vi ikke vet, merkes `[AVKLARES: …]`, som før.

## Fast for alle øktene

**Ord og navn (lysbilde 2):**

| Ikke skriv | Skriv |
|---|---|
| Sykehusapoteket, sykehusapotek | apoteket, apotek |
| prosedyre, etter prosedyre | lokale prosedyrer, etter lokale prosedyrer |
| OVERSIKT (knappen) | **Signeringsoppgaver og nylig historikk** (det heter knappen i appen nå, se lysbilde 4) |

Fagekspertene anbefaler å **skanne preparatene hele veien**. Da er man sikker på å få riktig preparat.
Manuell liste skal bare brukes når koden mangler eller ikke kan skannes. Ingen tekst i kurset skal
gi inntrykk av at manuell liste er like bra.

**Appens startmeny i versjon 2.1** (lysbilde 4), ovenfra og ned:

| Knapp | Undertekst | Farge |
|---|---|---|
| Signeringsoppgaver og nylig historikk | «10 hendelser venter på signatur», rødt tall | grønn, hel bredde |
| UTTAK | til pasient | mørk grå |
| TILBAKELEGGE | fra pasient | mørk grå |
| OVERFØRE til | eget underlager | brun |
| TILBAKEFØRE fra | eget underlager | blek (deaktivert) |
| APOTEKET | Mottak fra / Retur til | blå, hel bredde |
| KASSERE | rester / endose | rød |
| LÅN | til/fra annen enhet | rød |
| KONTROLL | av beholdning | gul, hel bredde |

**Merking i koden:** Kommentarer som viser til denne runden, skrives som `R2-<lysbilde>`, for eksempel
`// R2-11: umiddelbar svarrespons`. Tidligere runde brukte H-xx, C1-xx osv.

**Test:** Åpne `index.html?dev=1`. I utviklermodus tolkes et klikk på en QR-kode som «skannet» og et
klikk på ID-kortet (eller på «Bruker 1»/«Bruker 2» når kortet ikke er tegnet) som «tæppet». `index.html#case-1/2` går rett til et steg. Sjekk både lys og mørk
modus, og at hovedmenyen og stegene får plass uten å rulle i 1280 × 650 og 1920 × 940
(nettleserens utviklerverktøy, enhetsmodus).

## Filer i kurset

```
content/kurs.js     alt innhold: moduler, steg, grupper i hovedmenyen
content/koder.js    QR-register
js/app.js           logikk og HTML (APPKNAPPER øverst, veilederHtml, navradHtml, sporsmalHtml,
                    menyHtml, modulkortHtml, fremdriftHtml, lagre)
css/app.css         utseende (.scene, .toppfelt, .meny-gruppe, .kortgrid, .modulkort …)
README.md           beskrivelse av kurset. Oppdateres i økt 11
```

## Spørsmål til fagekspertene

Dette er tolket eller mangler i tilbakemeldingene. Kurset viser det som `[AVKLARES: …]` til det er
avklart. Legg til nye spørsmål her når en økt finner dem.

Listen er sjekket mot AVKLARES-registeret i utviklerpanelet i økt 11. Alle AVKLARES som er nye i runde 2,
står her. Steg er stegnummeret i kurset (`index.html#case-5/2` er Case 5, steg 2), og «rad» er den
nummererte raden i skannesonen. AVKLARES fra runde 1 (for eksempel startbeholdningen i Case 1) står bare i
registeret i utviklerpanelet.

| # | Hvor | Spørsmål | Økt |
|---|---|---|---|
| 1 | Hovedmeny, del B: TIPS, kortet og steg 1 | Hva skal stå i kortet **TIPS: Viktig info**? | 04 |
| 2 | Del D, alle fem modulene | Stemmer koblingen mellom lysbilde 41–45 og kortene? Og innholdet:<br>– **Akuttvogn**, steg 1: hvilke knapper i appen brukes når akuttvognen etterfylles etter bruk til pasient, og når holdbarheten er utløpt? Hva er forskjellen i registreringen?<br>– **Rette opp feil**, steg 1–3: teksten om å ikke dekke over andres feil, om at MOTTAK må stemme, og om sanntid og etterregistrering.<br>– **Glemmekort**, kortet og steg 1: når brukes glemmekort, og hvordan nullstiller man eget ansattkort?<br>– **Kjekt å vite**, kortet og steg 1: innholdet (lysbilde 44 har bare plassholdertekst).<br>– **Bidra til forbedring**, steg 1: hvor i appen sender man feil og forslag? | 04 |
| 3 | Case 6, tittelen | Fagekspertene skrev «Overføring til/fra eget lagre». Vi bruker «OVERFØRING til/fra eget underlager», som i appen. Riktig? | 05 |
| 4 | Case 4, steg 2, rad 2 | Metadon Nordic Drugs mikst registreres i ml. Hvor mange ml skal mottaket være? | 08 |
| 5 | Case 5, steg 1 rad 2, og steg 2 rad 1 | Hva heter de to fanene i Signeringsoppgaver og nylig historikk, og hva viser de? Finnes Avvik og Siste 14 dager fortsatt? | 09 |
| 6 | Case 5, steg 2 | Betyr «Etterkommentarer» og «Dobbeltsignering» typene signeringsoppgaver som ligger der? | 09 |
| 7 | Case 5, steg 4 | Kontrollspørsmålet om hvem som kan lese avvikskommentarer: beholde det? Foreløpig beholdt (valg a): punktet om at avvikskommentarer er skjult, står nå som tips på steg 2, så deltakeren har lest svaret. | 09 |
| 8 | Case 6, steg 2 | Kan TILBAKEFØRE brukes i Opplæringsmodus? | 10 |
| 9 | Case 7, steg 3 | Når brukes ETTERKASSERE, og hvordan gjøres det i appen? | 10 |
| 10 | Hovedmeny, del D | Del D står under overskriften «Valgfrie moduler», så gruppen fikk tittelen «Fordypning» for ikke å gjenta overskriften. Passer det, eller ønsker dere et annet navn? | 05 |

## Lysbildene

Bildene i `bilder/` er lysbildene med fagekspertenes kommentarer i rødt. Lysbilder som bare har
«Abc 1 2 3» i margen, har ingen kommentarer og er ikke tatt med (10, 12, 14, 16, 20, 21, 24, 25,
28–30, 33–38). Lysbilde 41–45 er bare tekst og er skrevet av i [04-nye-moduler.md](04-nye-moduler.md).
