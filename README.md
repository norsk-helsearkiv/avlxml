AVLXML

XML-skjema for digital avleveringsliste til Norsk helsearkiv.

Faglig referanse (standarden dekker både fysiske og elektroniske avleveringer):

- Fysiske pasientarkiver:
	https://www.nasjonalarkivet.no/besok-informasjon/norsk-helsearkiv/avleveringer-helsearkiv/avlevering-fysiske-arkiv-etter-helseforskriften/
- Elektronisk pasientmateriale:
	https://www.nasjonalarkivet.no/besok-informasjon/norsk-helsearkiv/avleveringer-helsearkiv/avlevering-av-elektronisk-pasientmateriale/

## Innhold i repo

Mappen `Schemas/` inneholder:

- `Schemas/avlxml.xsd`: Hovedskjema for grunnleggende avleveringsliste (AVLXML).
- `Schemas/avlxml-mdk.xsd`: Metadatatyper brukt av `avlxml.xsd`.
- `Schemas/avlsup.xsd`: Hovedskjema for supplerende opplysninger (AVLSUP).
- `Schemas/avlsup-mdk.xsd`: Metadatatyper brukt av `avlsup.xsd`.

Mappen `_local_docs/` brukes til lokale arbeidsdokumenter (for eksempel høringsutkast).
Denne mappen er lokalt arbeidsområde og er bevisst ignorert av git.

## Validering

Eksempel med `xmllint` for AVLXML:

```bash
xmllint --noout --schema Schemas/avlxml.xsd sti/til/avlxml-fil.xml
```

Eksempel med `xmllint` for AVLSUP:

```bash
xmllint --noout --schema Schemas/avlsup.xsd sti/til/avlsup-fil.xml
```

## Viktige føringer i gjeldende skjema

- `A-01 avlxmlversjon` er låst til `2.16.578.1.39.100.5.2.4` i `Schemas/avlxml-mdk.xsd`.
- `P-11 sikkermors` er modellert som indikator `0` eller `1`.
- Feltrekkefølge i `virksomhet` og `pasientjournal` er bevisst beholdt i tråd med eksisterende v3-baserte implementasjoner.
- I `Schemas/avlsup.xsd` støttes både `Organisasjon` (legacy) og `organisasjon` (foretrukket) i overgangsperiode.

## Endringslogg (kort)

- 2026-03-12
	- Låst `A-01 avlxmlversjon` til fast v4-OID `2.16.578.1.39.100.5.2.4`.
	- Endret `sikkermors` til streng indikator (`0`/`1`).
	- Lagt til overgangsstøtte for både `Organisasjon` og `organisasjon` i AVLSUP.
- 2022-05-09
	- AVLXML v4 draft publisert.
	- Store endringer i AVLSUP: supplerende opplysninger beskriver dokumentnivå.
- 2020-12-08
	- AVLXML v3 publisert.
	- `P-13` og `P-14` gjort obligatoriske.
	- `P-03` lagt til på pasientjournal.
	- `A-04` lagt til på avlevering.
- 2018-10-04
	- Første opprettelse av skjemaene.
