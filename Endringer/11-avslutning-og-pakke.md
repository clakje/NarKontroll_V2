# Økt 11 · Avslutning, README og SCORM-pakke

Les [README.md](README.md) først. Alle de andre øktene må være gjort.

**Kilde:** `bilder/lysbilde-39.png`, `bilder/lysbilde-40.png`. Lysbilde 34–38 (Gode råd) har ingen
kommentarer.

## Mål

Siste modul er rettet, hele kurset er testet fra start til slutt, dokumentasjonen stemmer, og det
finnes en ny SCORM-pakke.

## Endringer

### 1. M13 «Avslutning» (`m13-avslutning` i `content/kurs.js`)

- Steg 1: fagekspertene har skrevet «Logg inn med ekte bruker» over stegkortet (lysbilde 39).
  Bytt stegtittelen «Sjekk tilgangen din» med **«Logg inn med ekte bruker»**. Teksten er uendret.
- Steg 2: sjekk at resultatpanelet er borte (økt 03).

### 2. Gjennomgang av hele kurset

Tøm fremdriften (utviklerpanelet) og gå gjennom hele kurset i `index.html?dev=1`, i 1536 × 730:

- Hovedmenyen → M0 → Case 1–9 → TIPS → Gode råd → Avslutning → én valgfri modul.
- På hvert steg: kolonnene står stille, knappen videre synes uten å rulle, ingen «for å bla», ingen
  «OVERSIKT», «Sykehusapotek» eller «prosedyre» uten «lokale».
- Etter Avslutning: `lesson_status` er `completed` selv om del D ikke er gjort.
- `suspend_data` er godt under 4096 tegn.
- Gjenta hovedmenyen i 1280 × 650 og 1920 × 940, lys og mørk modus.

Skriv ned feil du finner, og rett dem. Er de store, lag en ny økt-fil (12-…) i stedet.

### 3. `README.md` i prosjektroten

Oppdater beskrivelsen så den stemmer med kurset nå:

- «Innhold i denne versjonen»: legg til et avsnitt om runde 2 (lysbildene i
  `Tilbakemeldinger - NarKontroll (1).pptx`, oppgavene i `Endringer/`). Antall steg og moduler.
  Erstatt henvisningen til mappen `Tilbakemeldinger/` (den er slettet).
- «Design»: hovedmenyen med del A–D, «Obligatoriske moduler» og «Valgfrie moduler», fullført = grønt
  kort med hake (Alternativ 1), låste kolonner på alle steg, lavere toppfelt, ingen «for å bla».
  Oppdater også hva som er testet for plass (fra økt 05 og 06).
- Kontrollspørsmål: umiddelbar respons, svaret kan endres, «Fortsett», ingen summering.
- «SCORM»: `completed` når alle obligatoriske moduler (del A–C) er fullført. `score.raw` bygger
  fortsatt på første forsøk, men vises ikke i kurset.
- Nye felt i `kurs.js`: `utenKort`, `kortTittel`, `valgfri`, `del`.

### 4. Spørsmål til fagekspertene

Gå gjennom AVKLARES-registeret i utviklerpanelet. Sjekk at alle nye AVKLARES fra denne runden står
i listen «Spørsmål til fagekspertene» i [README.md](README.md), med case og steg. Den listen kan
sendes til fagekspertene.

### 5. SCORM-pakken

```
python scripts/pakk-scorm.py
```

Sjekk at `dist/NarKontroll-KonseptA-scorm12.zip` er oppdatert, og at mappen `Endringer/` ikke er med
i pakken (skriptet tar bare `css`, `js`, `content`, `assets` og `index.html`).

## Funn i gjennomgangen

Gått gjennom med et skript i Chrome (uten hodet): hele kurset fra tom fremdrift, M0 → Avslutning → Akuttvogn,
i 1536 × 730, 1280 × 650 og 1920 × 940, med og uten utviklermodus. Hovedmenyen målt etter hver fullførte
modul, i lys og mørk modus.

I orden: kolonnene står på samme sted på alle 40 stegene, ingen «for å bla», «OVERSIKT», «Sykehusapotek» eller
«prosedyre» uten «lokale», `lesson_status` blir `completed` etter Avslutning uten del D, og `suspend_data` er
516 tegn til slutt. M13 steg 2 har ikke noe resultatpanel.

Feil som er rettet:

| Feil | Rettet |
|---|---|
| Case 5 steg 1: «Ferdig, neste» under kanten i 1536 × 730 (og 1280 × 650) | Siste setning i teksten («Gå inn i Signeringsoppgaver …») er fjernet, fordi rad 1 sier det samme. Tipset om å dobbeltsignere andres registreringer er flyttet til steg 3 («Ikke overlat det til neste skift») |
| Case 8 steg 1: «Neste» under kanten i 1280 × 650 | Tipset «Kontroller ID-kortet til den som skal låne …» står nå under ID-kortet i skannesonen (`panel.tekst`). QR-arket tar det med |
| Stegene i 1280 × 650: mange ruller 5–48 px | Den strammeste regelen for lave skjermer gjelder nå til 680 px høyde (var 640 px) |
| Hovedmenyen ruller 8 px i 1536 × 730 | Mindre avstand mellom gruppene (`.meny` gap 6 px, 4 px under 680 px høyde) |
| Hovedmenyen i 1280 × 650: fremdriftslinjen brytes i to når neste modul har langt navn (rullet opptil 82 px) | Sporet krymper først (`.fremdrift-spor` flex-basis 60 px) |
| Hovedmenyen ble høyere for hver rad med fullførte kort (haken var høyere enn raden) | Haken har negativ marg |

Resultat: hovedmenyen ruller ikke i noen av de tre størrelsene. Stegene ruller ikke i 1536 × 730 og 1920 × 940.
I 1280 × 650 synes knappen videre på alle steg. Steg 1 i Case 2, 5 og 8 ruller 1–17 px for å vise statuslinjen
under knappen.

## Ferdig når

- [x] M13 steg 1 heter «Logg inn med ekte bruker»
- [x] Hele kurset er gått gjennom uten feil
- [x] README.md stemmer
- [x] Spørsmålene til fagekspertene er samlet
- [x] Ny SCORM-pakke
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: Avslutning, oppdatert README og ny SCORM-pakke`
