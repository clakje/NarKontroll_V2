# Økt 10 · Case 6–9

Les [README.md](README.md) først. Økt 01, 05 og 07 må være gjort (knappenavn, nye titler, ID-kortet
på signer-steg).

**Kilde:** `bilder/lysbilde-26.png`, `bilder/lysbilde-27.png`, `bilder/lysbilde-31.png`,
`bilder/lysbilde-32.png`, og lysbilde 3 (titlene). Lysbilde 28–30 og 33 har ingen kommentarer.

Case 6–9 er fortsatt **utkast** (`utkast: true`). La merkelappen stå.

## Case 6 «OVERFØRING til/fra eget underlager» (`case-6`)

Fagekspertene har skrevet **«Test underlager»** ved navnet på underlageret (lysbilde 26).

- Bytt «TEST Medisintralle» med «TEST Underlager» i `kortTekst`, steg 1 og i `content/koder.js`
  (`UNDERLAGER-01`, bare `navn`, la `payload` stå til de ekte kodene kommer). Skriv TEST med store
  bokstaver, som de andre lagrene (TEST Medisinrom 1).
- Fjern `[AVKLARES: navnet på underlageret i Opplæringsmodus]`.
- Medisintrallen kan fortsatt være eksempelet i teksten: «Medisintrallen er et underlager til
  medisinrommet. I Opplæringsmodus heter underlageret **TEST Underlager**.»
- Tittelen (økt 05) sier «til/fra». I dag øver casen bare OVERFØRE. Legg til et steg 2 med
  TILBAKEFØRE (for eksempel 2 stk Oxynorm tilbake til medisinrommet), med
  `[AVKLARES: kan TILBAKEFØRE brukes i Opplæringsmodus? Knappen er blek på lysbilde 4]`.
  Tipset om TILBAKEFØRE i steg 1 kan da fjernes.

## Case 7 «KASSERE og ETTERKASSERE» (`case-7`)

Fagekspertene har skrevet ny `kortTekst` (lysbilde 27):

> «Du mister en Sobril 10 mg på gulvet. Denne må kasseres.»

- `kortTekst` som over.
- Steg 1, rad 1: «Trykk på **KASSERE** rester / endose.» (knappens tekst i appen 2.1)
- Steg 1, rad 2: `mengde: 1`. Merknaden «Desimaltall skrives med komma.» blir:
  «Mengden kan også være et desimaltall, for eksempel 0,5 stk for en halv tablett. Desimaltall skrives med komma.»
- Punktene i steg 1 (tablett på gulvet, halv tablett, skvett) kan stå.
- Steg 2 (signer, dobbeltsignering): uendret. ID-kort-tegningen er borte etter økt 07.
- **ETTERKASSERE** er nytt i tittelen. Legg til et `info`-steg før eller etter signeringen:
  tittel «Når bruker du ETTERKASSERE?», tekst
  «[AVKLARES: når brukes ETTERKASSERE, og hvor i appen? Er det kassasjon som er knyttet til en
  registrering du allerede har gjort, for eksempel resten av en ampulle etter UTTAK?]»
  (I dag står det at KASSERE brukes når kassasjonen *ikke* er knyttet til en annen registrering.)

## Case 8 «LÅN til/fra annen enhet» (`case-8`)

Steg 3 «Mottakeren får en ny signeringsoppgave», lysbilde 31:

- `tips` blir: «Signeringsoppgaven for INNLÅN lages på mottakerens lager.» Fjern AVKLARES-teksten
  der («stemmer det, eller signeres innlånet et annet sted? …»).
- Punktet «En tredje bruker dobbeltsignerer INNLÅNET … [AVKLARES: er det en kollega på
  mottakeravdelingen?]» står til det er avklart.

## Case 9 «KONTROLL av beholdning» (`case-9`)

Fagekspertenes tekst (lysbilde 32), lett språkvasket:

> Ved KONTROLL lønner det seg å skanne, fordi legemidler som er KONTROLL-signert de siste 12 timene,
> skjules fra listen. Vil du se alle legemidlene, slår du på den grønne bryteren. Da ser du alle, og de
> som allerede er kontrollert, har en grønn hake.
> Det anbefales å skanne på KONTROLL. Da går appen rett til «Skann legemiddel» etter signering.
> Velger du legemidlene manuelt fra listen, går appen tilbake til listen.
> Bruk filteret for reseptgruppene, og se til slutt over at du har fått med alle legemidlene i
> beholdningen. Står det noe igjen i listen som ikke er KONTROLL-signert de siste 12 timene?

Fordel det slik:

- Steg 1, `punkter` (venstre kolonne):
  - «Legemidler som er KONTROLL-signert de siste 12 timene, skjules fra listen. Slå på den grønne
    bryteren for å se alle. De som er kontrollert, har grønn hake.»
  - «Skann legemidlene. Da går appen rett til **Skann legemiddel** etter hver signering. Velger du fra
    listen, går appen tilbake til listen.»
- Steg 1, `rekke`: legg til en siste rad: «Bruk filteret for reseptgruppene. Se til slutt over at alle
  legemidlene i beholdningen er KONTROLL-signert de siste 12 timene.»
- Passer det ikke på én side uten rulling i 1280 × 650, flytt det siste punktet til et eget
  `info`-steg «Er alt kontrollert?».
- Kontrollspørsmålet (steg 2): ingen kommentar. `forklaring` har `[AVKLARES: fremgangsmåte ved avvik
  under KONTROLL]`. La den stå.

## Test

- `index.html?dev=1#case-6/1` til `#case-9/…`: nye tekster, ingen rulling for å nå knappen videre.
- QR-ark for Case 6–9 (Case 8 fylte to sider før, se om det fortsatt er greit).
- Utviklerpanelet, AVKLARES-registeret: de nye spørsmålene står der.

## Ferdig når

- [x] Case 6: TEST Underlager, og TILBAKEFØRE-steg med AVKLARES
- [x] Case 7: ny situasjon, KASSERE rester / endose, ETTERKASSERE-steg med AVKLARES
- [x] Case 8: INNLÅN-tipset
- [x] Case 9: fagekspertenes tekst om KONTROLL
- [x] Haket av i [README.md](README.md)

Forslag til commit: `R2: Case 6–9 etter fagekspertenes kommentarer`
