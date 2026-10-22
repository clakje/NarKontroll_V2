# Økt 01 · Gjennomgående tekst og appknapper

Les [README.md](README.md) først.

**Kilde:** lysbilde 2 (tekst under), 4 (`bilder/lysbilde-04.png`), 22 og 27.

> Lysbilde 2 «Gjennomgående»:
> - Det skal stå apotek og ikke sykehusapotek.
> - Der det står prosedyrer, må det stå lokale prosedyrer.
> - Det anbefales å skanne preparatene hele veien. Da er man sikker på at man får rett preparat.
>   Å velge fra manuell liste skal bare benyttes hvis koden mangler eller ikke er skannbar.

## Mål

Ordbruken og appknappene stemmer med appen og med fagekspertene i hele kurset, før de andre øktene
endrer innholdet case for case.

## Endringer

### 1. Apotek og lokale prosedyrer (`content/kurs.js`)

Søk etter `ykehusapotek` og `prosedyre` i `content/` og `js/`. `Losningsforslag.md` endres ikke.
Kjente steder:

| Hvor | Nå | Nytt |
|---|---|---|
| Case 4, steg 3, `tips` | «RETUR til Sykehusapoteket er ofte … Returen leveres etter prosedyre.» | «RETUR til apoteket er ofte … Returen leveres etter lokale prosedyrer.» |
| Case 7, steg 2, `tips` | «… skal de returneres til Sykehusapoteket, ikke kasseres lokalt.» | «… skal de returneres til apoteket, ikke kasseres lokalt.» |

### 2. Anbefal skanning (`content/kurs.js`)

- M12 «Gode råd», steg 1 «Skann det du sikter på»: legg til et første punkt:
  «Skann preparatet hele veien. Da er du sikker på at du får riktig preparat. Velg fra manuell liste
  bare hvis koden mangler eller ikke kan skannes.»
- Case 5, steg 2, rad med søk: merknaden «Du kan også skrive navnet på legemidlet i søkefeltet.»
  kan bli stående, men legg til «Skanning er tryggest.» (Case 5 skrives uansett om i økt 09.)

### 3. Appknappene (`js/app.js`, `APPKNAPPER` og `MENYREKKEFOLGE` øverst i filen)

Oppdater til appen versjon 2.1 (tabellen i README):

- `oversikt`: `merke` og `navn` blir «Signeringsoppgaver og nylig historikk», `under` blir
  «hendelser venter på signatur». Behold nøkkelen `oversikt`, så lagret fremdrift og `kurs.js` virker.
- `kassere`: `merke` «KASSERE», `under` «rester / endose». (Tittelen på Case 7 endres i økt 05.)
- `lan`: `merke` «LÅN til/fra annen enhet» (uendret, sjekk bare).
- `MENYREKKEFOLGE`: `oversikt` først (den står øverst i appen nå).
- `startmenyHtml()` (skjematisk startmeny) brukes ikke av noe steg nå. Sjekk med Grep etter `meny:` i
  `kurs.js`. Er den ubrukt, trenger du ikke oppdatere tegningen. Men `sm-oversikt` må ikke krasje
  med lang tekst hvis den brukes i QR-arket (`appknappHtml`). Skriv ut et QR-ark for Case 5 og se.

### 4. «OVERSIKT» i teksten (`content/kurs.js`)

Erstatt knappenavnet OVERSIKT med **Signeringsoppgaver og nylig historikk** der det står i Case 1
(kontrollspørsmålet) og Case 8 (`tips` i steg 3). Case 5 skrives om i økt 09, så la den være nå,
bortsett fra `tittel` (se under).

| Hvor | Nytt |
|---|---|
| Case 1, steg 4, `tekst` | «Se på startmenyen i appen. **Signeringsoppgaver og nylig historikk** har fått et rødt tall. Hva betyr det?» |
| Case 5, `tittel` | «Signeringsoppgaver og nylig historikk» (lysbilde 3 og 22) |

## Ikke gjør

- Ikke endre layout eller kontrollspørsmålenes oppførsel. Det er økt 02 og 03.
- Ikke skriv om Case 5 utover tittelen.

## Test

- Grep etter `ykehusapotek`, `prosedyre` og `OVERSIKT` i `content/` og `js/`. Det som står igjen,
  skal være kommentarer, nøkler (`oversikt`) eller Case 5-tekst som økt 09 tar.
- `index.html?dev=1#case-5/1`: merkelappen øverst viser det nye navnet med grønn farge, og det
  brytes pent på to linjer om nødvendig.
- QR-ark (knappen «QR-ark») for Case 5 og Case 7: appknappen ser riktig ut.

## Ferdig når

- [x] Ingen «Sykehusapotek» eller «prosedyre» uten «lokale» i kurset
- [x] Skanning anbefales i M12
- [x] `APPKNAPPER` stemmer med appen 2.1
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: apotek, lokale prosedyrer, anbefal skanning og nye knappenavn fra appen 2.1`
