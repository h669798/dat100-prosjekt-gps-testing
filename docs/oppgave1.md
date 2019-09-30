# Oppgave 1: Klasse for GPS punkter

I denne oppgaven skal der implementeres en klasse `GPSPoint.java` for å kunne representere GPS datapunkter. Ideen er at et GPS punkt skal representeres som et objekt av denne klassen og programmet skal ha et slikt objekt for hvert GPS punkt. For hvert GPS punkt får vi behov for å lagre tidspunkt, breddegrad, lengdegrad og høyde (elevation).

### a) Objektvariable og konstruktør

Se på start-koden for klassen `GPSPoint.java` i pakken `no.hvl.dat100ptc.oppgave1`

Skriv kode slik klassen får tre objektvariable:

-	`time` (heltall) som angir tiden i sekunder
-	`latitude` (desimaltall) som angir breddegrad
-	`longitude` (desimaltall) som angir lengdegrad
- `elevation` (desimaltall) som angir høyde i meter

som alle skal være `private` dvs. kun synlige innenfor klassen.

Videre skal klassen ha en *konstruktør*

```java
GPSPoint(int time, double latitude, double longitude, double elevation)
```

som kan gi verdi til alle objektvariable.

Test implementasjonen din ved å kjøre testene i test-klassen `GPSPointeTester.java`

### b) Hent/sett-metoder

Gjør ferdig implementasjonen av get/set metoder og test de med enhetstestene.

### c) Strengrepresentasjon

Gjør ferdig implementasjonen av `toString()`-metoden som returnerer en strengrepresentasjon av objektvariablene på formen: `1 (2.0,3.0) 5.0\n` der `1` er tiden, `(2.0,3.0)` er (breddegrad,lengdegrad) og 5.0 er høyden.

Test implementasjonen ved å bruke enhetstestene.
