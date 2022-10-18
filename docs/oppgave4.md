### Oppgave 4: GPS-basert statistikk

I klassen `GPSComputer.java` skal dere implementere metoder som beregner statistikk (nøkkeltall) basert på de innleste og konverterte GPS data.

I forbindelse med implementasjonen bør dere tenke på om der allerede finnes metoder fra tidligere oppgaver eller denne deloppgaven som kan brukes i løsningen.

Klassen `GPSComputer.java` inneholder en tabell

```java
	private GPSPoint[] gpspoints;
```

med konvertert GPS data og metodene som dere skal implementere skal bruke data fra denne tabellen til å gjøre beregninger. Tabellen vil inneholder de GPS punktene som utgjør ruten dvs. de punktene som en har syklet igjennom.

Testklassen for denne oppgaver er `GPSComputerTester.java`.

Følgende metoder skal implementeres

#### 4a)

```java
public double totalDistance()
```

som beregner den totale distansen på ruten som GPS dataene angir. Dvs. metoden må legge sammen avstanden mellom de punktene vi har beveget oss igjennom på ruten.

#### 4b)

```java
public double totalElevation()
```

som beregner det totale antall høydemeter på ruten. Husk at vi skal kun telle høydemeter mellom to punkter om vi beveger oss oppover.

#### 4c)

```java
public int totalTime()
```

som skal beregne den totale tiden det har tatt å sykle ruten svarende til de innleste GPS data.

#### 4d)

```java
public double[] speeds()
```

som skal returnere en tabell med gjennomsnitshastigheter mellom hver av de punktene vi har beveget oss mellom. Dvs. første inngang i tabellen skal være hastigheten vi beveget oss med mellom punkt 0 og punkt 1, andre inngang hastigheten mellom punkt 1 og 2 osv. Hvis antall GPS datapunker er *N* da vil lengden av den tabellen som returneres være *N-1*.

**Hint:** kan du bruke noe fra klassen `GPSUtils.java`?

#### 4e)

```java
public double maxSpeed()
```

som returnerer den største hastigheten vi har beveget oss med mellom to punkter på ruten.

#### 4f)

```java
public double averageSpeed()
```

som returnerer gjennomsnittshastigheten vi har beveget oss med total sett for hele ruten.  

#### 4g)

```java
public double kcal(double weight, int secs, double speed)
```

som beregnerer hvor mye energi vi har forbrent gitt vekten vår og at vi beveger os med en gitt hastighet i antall sekunder.

For å kunne estimere energi-forbrenningen i kilo-kalorier (kcal) skal vi først finne *MET* (Metabolic Equivalent of Task)  som er et fysiologisk mål for hvor mange kcal vi forbrenner per kilo kroppsvekt per time ved en gitt aktivitet. MET avhenger av type aktivitet og intensitet. For sykling [ http://coachlevi.com/health/calories-burned-bicycling/ ] er den gitt i tabellen nedenfor der hastighet er angitt i miles per hour (mps):

```
Hastighet	MET
<10 mph	4.0
10-12 mph	6.0
12-14 mph	8.0
14-16 mph	10.0
16-20 mph	12.0
>20 mph	16.0
```

Hastighet i km/t kan omregnes til mph ved å gange med en faktor *0.62*. MET vil også avhenge av eks. stigningsprosent (om det går opp eller ned og hvor mye) men det skal vi se bort fra her.

#### 4h)

```java
public double totalKcal(double weight)
```

som beregner den totale energy-mengden som er forbrent på ruten.

#### 4i)

```java
public void displayStatistics()
```

som skriver ut statistikken som er beregnet av metodene i klassen. Formatet på utskriften skal være slik:

```
==============================================
Total Time     :   00:36:35
Total distance :      13.74 km
Total elevation:     210.60 m
Max speed      :      47.98 km/t
Average speed  :      22.54 km/t
Energy         :     742.80 kcal
==============================================
```

Testene vil kalle denne metoden med de fire log-filer og du kan se utskriften i konsollen i Eclipse.
