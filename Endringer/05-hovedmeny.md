# Økt 05 · Hovedmenyen med del A–D (Alternativ 1)

Les [README.md](README.md) først. Økt 01 og 04 må være gjort (nye knappenavn, nye moduler,
feltene `kortTittel`, `valgfri` og `del`).

**Kilde:** `bilder/lysbilde-03.png` (fagekspertenes forslag), `bilder/lysbilde-04.png` (Alternativ 1:
kortet for en fullført case).

## Mål

Hovedmenyen viser kurset i fire deler. A, B og C er obligatoriske, D er valgfri. Case-kortene står i
et eget rutenett (Alternativ 1), og en fullført case er tydelig grønn.

## Endringer

### 1. Tittel og ingress (`content/kurs.js`, `hovedmeny`)

Tittelen er uendret: «Kurs i NarKontroll-appen». Ny ingress, fire korte linjer (fra lysbilde 3):

```
NarKontroll® er en elektronisk løsning for regnskap og kontroll med A- og B-preparater.
Dette kurset guider deg gjennom appens funksjoner så du skal bli trygg på å bruke appen på riktig måte.
Del A, B og C omhandler grunnleggende funksjoner og er obligatorisk for alle app-brukere.
Del D er valgfri, men også anbefalt for alle.
```

Det kan være fire `<p>` eller to avsnitt. Hold linjeavstanden tett, så menyen får plass.

### 2. Delene (`content/kurs.js`, `grupper`, og `js/app.js`, `menyHtml`)

| Del | Gruppe | Moduler |
|---|---|---|
| A | Kom i gang | `m0-velkommen` |
| B | Caser | `case-1` … `case-9`, `tips` |
| C | Til slutt | `m12-gode-rad`, `m13-avslutning` |
| D | Valgfrie moduler | `d-akuttvogn`, `d-rette-opp-feil`, `d-glemmekort`, `d-kjekt-a-vite`, `d-forbedring` |

- Over del A står overskriften **Obligatoriske moduler** (gjelder A–C). Over del D står
  **Valgfrie moduler**. Lag dem som små overskrifter (`h2`) over gruppene, og gjør gruppetitlene til `h3`.
- Tallet foran gruppetittelen (`gruppe-nr`, i dag 1, 2, 3) blir bokstaven: A, B, C, D.
- Gruppeteksten («Gjør denne først …») og telleren «0 av 9 fullført» kan bli stående for A–C.
  For D holder det med teksten «Anbefalt for alle.» og telleren.

### 3. Kortene (`modulkortHtml`, CSS `.modulkort`)

- Kortet viser `kortTittel` hvis den finnes, ellers `tittel`.
- M0: `kortTittel: "Start her!"` (lysbilde 3). Merkelappen er fortsatt «FORBEREDELSER».
- Nye titler fra lysbilde 3 (sett `tittel` i `kurs.js`, så toppfeltet viser det samme):
  - Case 6: «OVERFØRING til/fra eget underlager» (fagekspertene skrev «Overføring til/fra eget lagre».
    Appen sier «eget underlager». Se spørsmålene i README.)
  - Case 7: «KASSERE og ETTERKASSERE»
  - Case 8: «LÅN til/fra annen enhet»
  - Case 5 fikk ny tittel i økt 01.
- TIPS-kortet har ingen appfarge øverst.
- Kortene i del D kan være like lave som de andre. Fem kort på én rad på bred skjerm.

### 4. Fullført case (Alternativ 1, lysbilde 4)

En fullført modul får:

- **lys grønn bakgrunn** på hele kortet, og
- en **grønn hake i en sirkel** øverst til høyre (som på lysbilde 4), i stedet for dagens hake og tekst.

Lag nye fargetokener på `:root`, for eksempel `--ferdig` (hake) og `--ferdig-flate` (bakgrunn), med
egne verdier i mørk modus. Teksten på kortet skal ha minst 4,5:1 kontrast mot den grønne flaten.
Appfargen øverst på case-kortet blir stående. Skjermleseren får fortsatt «fullført» (`.sr`-teksten).

Påbegynt modul beholder statusringen. Anbefalt neste beholder rammen.

### 5. Fremdriftslinjen nederst (`fremdriftHtml`)

- «X av N moduler fullført» teller bare obligatoriske moduler.
- Sporet (strekene) viser bare obligatoriske moduler.
- Knappen «Neste: …» foreslår aldri en valgfri modul før A–C er fullført (dette ble gjort i økt 04,
  sjekk det).

### 6. Plass

Tidligere krav (H-04): hele menyen skal få plass uten å rulle. Nå er det én del og én rad mer.
Prioriter slik:

1. Ingen rulling i 1920 × 940 og 1536 × 730.
2. I 1280 × 650 er litt rulling greit hvis det ikke går ellers. Stram heller inn avstander og
   kortenes høyde enn å gjøre teksten mindre enn 15 px.

Skriv i svaret hva som ble resultatet i hver størrelse.

## Ikke gjør

- Ikke legg inn bilde av appens startmeny på hovedmenyen (Alternativ 2 og 3 er valgt bort).
- Ikke endre innholdet i casene.

## Test

- `index.html?dev=1#meny` i 1920 × 940, 1536 × 730 og 1280 × 650, lys og mørk modus.
- Fullfør Case 1 (utviklerpanelet). Kortet blir grønt med hake. Hovedmenyen foreslår Case 2.
- Tastatur: Tab går gjennom kortene i rekkefølge A → D, og fokus er synlig på grønne kort.
- Windows høykontrast (`forced-colors`): fullført er fortsatt synlig (haken).

## Ferdig når

- [x] Ingress og del A–D med overskriftene «Obligatoriske moduler» og «Valgfrie moduler»
- [x] «Start her!», nye case-titler og TIPS-kort
- [x] Fullført = grønt kort med hake
- [x] Fremdriften teller bare obligatoriske moduler
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: hovedmeny med del A–D, obligatoriske og valgfrie moduler, grønne fullførte kort`
