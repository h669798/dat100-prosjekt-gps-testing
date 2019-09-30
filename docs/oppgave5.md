### Oppgave 5 - Visualisering av høyde profil

I denne oppgaven skal EasyGraphics-biblioteket brukes til å visualisere høyde-kurven for ruten gitt ved GPS datapunktene. For GPS datafilen `medium.log` skal visualiseringen se ut som nedenfor der høyden på en vertikal linje svarer til høyden i GPS datapunktet.

![](assets/markdown-img-paste-20180909115303289.png)

I klassen [showProfile.java](https://github.com/dat100hib/dat100-prosjekt/blob/master/src/no/hvl/dat100/prosjekt/ShowProfile.java) finnes allerede en main-metode som setter opp et vindu som kan brukes til å tegne høydeprofilen og som ber om navn på den datafil som skal visualiseres (short, medium, long).

Klassen sørger allerede for å lese inn data fra GPS datafilen ved oppstart og lagre data i følgende tabeller som finnes i klassen

```java
private static int[] times;
private static double[] latitudes;
private static double[] longitudes;
private static double[] elevations;
```

Implementer metoden

```java
showHeightProfile(int ybase)
```

som tegner høydeprofilen der parameteren ybase angir hvor på y-aksen bunnen av en søyle skal starte.

For å gjøre oppgaven enklere kan det antas at hvert punkt (pixel) i vinduet svarer til en høyde-meter. Negative høyder skal ignoreres – dvs. behandles som om de hadde verdien 0.

**Hint:** Husk at EasyGraphics bilioteket sitt koordinatsystem har punktet (0,0) i øverste venstre hjørne og se på koden for [Oppgave 6 på programmeringslab 3](https://github.com/dat100hib/H2017/blob/master/programmering/jplab3/JP3.md#oppgave-6-søylediagram).

Dokumentasjon for metodene i EasyGraphics-bibliotekt kan finnes her

https://dbsys.info/programmering/easygraphics/javadoc/index.html

### Oppgave 6 - Visualisering av hastighet

I denne oppgaven skal EasyGraphics brukes til å visualisere hastigheten der blev kjørt med i løpet av ruten. For GPS datafilen `medium.log` skal visualiseringen se slik ut

![](assets/markdown-img-paste-20180909120055723.png)

der denne grønne linjen indikerer gjennomsnittshastigheten for hele ruten.

Ferdiggjør implementasjonen av metoden showSpeedProfile i klassen [ShowSpeed.java](https://github.com/dat100hib/dat100-prosjekt/blob/master/src/no/hvl/dat100/prosjekt/ShowSpeed.java).

Der finnes allerede en main-metode i klassen som setter opp vindu og som kaller metoden showSpeedProfile. GPS data blir automatisk lest inn i tabeller med samme navn som i oppgave 5.

### Oppgave 7 - Visualisering av sykkelruten

I denne oppgaven skal EasyGraphics brukes til å visualisere ruten på et kart og til slutt skrive ut statistikk (nøkkeltall) om sykkelturen i øverste venstre hjørne. Et eksempel er vist nedenfor for log filen `medium.log`.

![](assets/markdown-img-paste-20180909120229747.png)

Y-aksen svarer til breddegrader og x-aksen svarer til lengdegrader.

Ferdiggjør implementasjonen av følgende metoder i klassen [ShowRoute.java](https://github.com/dat100hib/dat100-prosjekt/blob/master/src/no/hvl/dat100/prosjekt/ShowRoute.java).

Der finnes allerede en main-metode i klassen som setter opp vindu og som kaller de tre metodene `ShowRouteMap`, `ShowStatistics` og `PlayRoute`.

#### 7a)

```java
public double ystep()
```

som beregner hvor mange punkter (pixels) en breddegrad skal svare til for at vi kan tegne alle GPS datapunkter innen for et tegneområde på skjermen med et antall punkter i y-retningen som er gitt ved konstanten `MAPYSIZE`.

**Hint:** se implementasjonen av metoden `xstep()`. Vi antar her at jorden er flat dvs. en lengde og en breddegrad svarer til samme avstand uansett hvor vi befinner oss. Al den stund vi ikke sykler over veldig lange avstander er det en rimelig antagelse.

#### 7b)

```java
showRouteMap(int ybase)
```

som tegner punkter i vinduet svarende til de (lengdegrad,breddegrad) posisjoner som finnes i GPS datafilen. Parameteren `ybase` angir det sted på y-aksen som skal svare til den minste breddegrad som finnes i datafilen.

#### 7c)

```java
public void showStatistics()
```

som viser statistikk fra sykkelturen i øverste venstre hjørne (se bildet først i oppgaven ovenfor).
