### Oppgave 3 - GPS hjelpemetoder

Nå kan vi lese inn GPS data og konvertere det det tall som vi kan gjøre beregninger på. I første omgang skal vi implementere noen hjelpe-metoder i klassen [GPSUtils.java](https://github.com/dat100hib/dat100-prosjekt/blob/master/src/no/hvl/dat100/prosjekt/GPSUtils.java) som vi skal bruke seinere i prosjektet.


Gjør ferdig implementasjonen av følgende metoder i klassen og bruk enhetstestene i klassen `GPSUtils.java` til løpende å teste koden.

#### 3a)

```java
double findMin(double[] da)
```

som finner minste tall i en tabell med flyttall. **Hint:** se på implementasjonen av metoden findMax i klassen.

#### 3b)

```java
double distance(double latitude1, double longitude1,
          double latitude2, double longitude2)
```

som bruker Math-klassen: https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html

til å beregne avstanden *d* i meter mellom to punkter på jordkloden ved bruk av Haversine-formlen

![](assets/markdown-img-paste-20180909113408842.png)

der *R = 6371000* meter er jordens gjennomsnittsradius.

```java
double speed(int secs,
             double latitude1, double longitude1,        
             double latitude2, double longitude2)
```

som beregninger gjennomsnittshastighet i km/t om man beveger seg fra punktet gitt ved (latitude1,longitude1) til punktet (latitude2,longitude2) på det antall sekunder som er gitt med parameteren secs.

#### 3c)

```java
String printDouble(double d)
```

som runder av et flyttall til to desimaler, setter resultat inn i en streng og fyller på med mellomrom foran i strengen slik at lengden på strengen blir 10 (se eksempel i koden).

#### 3d)

```java
public static String printTime(int secs)
```

som returnerer en streng der tiden i sekunder fra midnatt gitt av parameteren secs på formatet `hh:mm:ss` der `hh` er antall timer, `mm` er antall minutter og `ss` er antall sekunder.
