# Oppgave 2 - GPS data innlesing og referansetabeller

I denne oppgaven skal vi se på hvordan GPS data kan leses inn fra fil og hvordan GPS punktene i filen kan representeres ved å bruke en tabell med pekere til GPSPoint-objekt.

Klassen `GPSDataRFileReader` inneholder ferdig Java-kode for å lese inn en CVS-datafil med GPS punkter i formatet forklart tidligere. Denne Java-koden er der ikke behov for endre i og vi skal først litt senere i faget lære om hvordan man leser og skrier i filer i Java.

Fokus i denne oppgavene er på å implementere metoden i klassene `GPSData.java` som skal lagre innlest GPS data i form av en tabell av `GPSPoint`-objekt og hjelpeklassen `GPSDataConverter.java` som inneholder hjelpemetoder for å konvertere det data som leses inn til `GPSPoint`-objekt.

#### 2a) GPS data konvertering

Når data leses inn fra fil vil et GPS punkt være representert som strenger. Eksempelvis vil tidsdata  for et innlest GPS punkt være representert som strengen:

```
"2017-08-13T08:52:26.000Z"
```

Gjør ferdig implementasjon av metoden

```java
public static int toSeconds(String timestr)
```

som omregner tidsdata som representert ovenfor til antall sekunder. For eksemplet ovenfor skal de 8 timer, 52 minutter og 26 sekunder regnes om til 31946 sekunder og returneres.

Implementer metoden

```java
public static GPSPoint convert(String timeStr, String latitudeStr, String longitudeStr, String elevationStr) {
```

som tar Streng-representasjoner av tid, breddegrad, lengdegrad og høyde konverterer disse og oppretter et `GPSPoint`-objekt med de lagrede data.

Hvis eksempelvis skal metoden kalles med

```java
convert("2017-08-13T08:52:26.000Z","60.385390","5.217217","61.9"
```

da skal metoden returner et GPSPoint-objekt der tid er 31946, breddegrad er 60.385390, lengdegrad er 5.217217 og høyde er 61.9.

#### 2b) Referansetabell med GPS punkt objekt

De GPS punkter som leses inn fra fil og konverteres skal representeres ved å bruke en referanasetabell dvs. en tabell der elementene som er lagret er pekere til `GPSPoint`-objekt.

Starten på implementasjonen finnes i klassen `GPSData.java`:

```java
public class GPSData {

	private GPSPoint[] gpspoints;
	protected int antall = 0;

  [...]
```

Objektvariabelen `gpspoints` skal brukes til å peke på referansetabellen av GPS punkter. Objektvariabelen `antall` skal brukes ifm. med innsettelse i tabellen til å holde kontroll på hvor (dvs. på hvilken posisjon/indeks) neste vare skal settes inn.

Variabelen `antall` vil til ethvert tidspunkt angi hvor mange GPS punkter som er satt inn i tabellen. Indeks der det ikke er satt inn noen vare vil ha verdien `null` (en null-peker).

Objektvariablen `antall` har modifikatoren `protected` for å gjøre det enklere å teste klassen. Testene for klassen finnes i klassen `GPSDataTester.java`.

Metodene som allerede er implementert i klassen GPSDatFileReader er allerede implementert og leser - linje for linje - i GPS datafilen og lagrer data i tabellen.

Gjør ferdig implementasjonen av følgende metoder:

- `public GPSData(int antall)` som er en kontruktør for klassen. Konstruktøren skal opprettet en tabell av GPS punkter med størrelse gitt ved parameteren `n` og sette `antall` lik `0` (siden første element skal inn på position 0).

- `public Vare[] getVarer()` som returnerer en referanse til tabellen `varer`

- `protected boolean insertGPS(GPSPoint gpspoint)` som setter inn GPS punktet `gpspoint` i `gpspoints`-tabellen på posisjonen angitt ved objektvariablen `antall`. Videre skal metoden inkrementere `antall` slik neste punkt kommmer inn på neste posisjon. Metoden skal kun sette inn `gpspoint` hvis der er plass i tabellen dvs. hvis `antall` er strengt mindre enn `gpspoints.length`. Metoden skal returnere `true` om punktet blev satt inn og `false` ellers.

- `public boolean insert(String time, String latitude, String longitude, String elevation)` som tar GPS punkt data i streng-representasjon og setter inn et tilsvarende `GPSPoint`-objekt i `gpspoints`-tabellen. **Hint:** Konverter data, opprette et nytt `GPSPoint-objekt` og bruk metoden ovenfor.

- `public void print()` som skal skrive ut GPS data som finnes i `gpspoints`-tabellen på følgende formen

====== Konvertert GPS Data - START ======
1 (1.0,2.0) 3.0
2 (4.0,5.0) 6.0
3 (7.0,8.0) 9.0
====== Konvertert GPS Data - SLUTT ======

**Hint**: bruk løkke og `toString`-metoden på `GPSPoint`-objekt
