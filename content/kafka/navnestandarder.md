---
title: "Navnestandarder"
bookComments: false
type: 'docs'
# date: 2022-11-19T10:46:33+01:00
# bookSearchExclude: false
---

# Navnestandard på kafka-medlinger

## Status
Besluttet sommer 2022 og alle meldinger i løsninger er ryddet opp i. 

## Bakgrunn
Stor variasjon i navngivning, der en variabel ofte har 2-3 ulike varianter. Behov for en standard løsning. 

## Alternativer
### Innføre en navnestandard 
Vi blir enige om en navnestandard, og alle apper må forholde seg til det.

### Ikke innføre en navnestandard 
Alle meldinger kan fortsette å skrives litt vilkårlig. 


## Konklusjon
Felles-nøkler er flyttet til et eget bibliotek og skal hentes derfra.  
Disse hentes i appen rapidsandrivers-extra, under StandardKeys.kt, og inkluderer
- @correlation_id
- @event_name
- @behov


For egne meldinger gjelder følgende:

- CamelCase for alle keynavn vi setter selv på toppnivå i melding (eg sakId, behandlingId)
- @ brukes bare på "system-keys", så alle egne meldinger skal ikke ha @. 


# Navnestandard på hendelser som publiseres

## Status
Besluttet 2022-06-09 i utviklersync-møte

## Bakgrunn
En del  av arkitekturen som har vokst fram i løsningen er at applikasjoner reagerer på hendelsene til hverandre.
Det kan oppleves rotete og lite intuitivt om alt om hvordan en hendelse ser ut defineres i hver app.

## Alternativer
### Innføre en navnestandard for hendelser
Vi blir enige om en navnestandard, og alle apper må forholde seg til det.
En slik navnestandard kan for eksempel utformes slik at det er enkelt å se hvor hendelsen kommer fra og hva den gjelder, uten detaljert kunskap om alle appene.

### Ikke innføre en navnestandard for hendelser
Vi lar alle apper lage sine egne navn på hendelser helt uavhengig av andre apper.

## Konklusjon
Vi vil ha en felles navnestandard på hendelsene våre.
Hendelser publiseres med navn på formatet `DOMENE:HENDELSE`. For eksempel publiserer behandling hendelsen `BEHANDLING:OPPRETTET` når en behandling er opprettet.

