---
layout: page
title:  "Der Ökologischer Fußabdruck der G20-Staaten"
header: no
show_meta: false
categories:
    - projects
image:
    title: footprint\Poster.jpg
    caption: Teaser
author: Yavuz Azal, Arif Bozkurt, Benedikt Herbst, Vu Tuananh, Thaer Aldefai 
---

## Abstract
Jeden Tag verbrauchen wir Resourcen der Erde und erzeugen Müll. Dabei vergessen wir, dass diese Resourcen der Erde endlich sind. Mittleweile verbauchen wir Menschn mehr Resourcen, als auf der Erde vorhanden sind. Dieser Verbrauch wird auch als ökologischer Fußabdruck bezeichnet. Der ökologischer Fußabdruck ist eine Metrik, mit der erfasst werden kann, wie viel Biokapazität vorhanden ist und wie diese genutzt wird, um unseren Lebensstandard aufrechtzuerhalten. 

## Inhalt
1. [Einführung](#Einführung)
2. [These](#These)
3. [Daten](#Daten)
    1. [Datenquelle](#Datenquelle)
    2. [Datenerhebung](#Datenerhebung)
    3. [Datenaufbereitung](#Datenaufbereitung)
4. [Prozess](#Prozess)
5. [Prototypen](#Prototypen)
    1. [Visualisierung mit D3.js](#Visualisierung)
        1. [Treemap](#Treemap)
        2. [Säulendiagramm](#Säulendiagramm)
        3. [Linendiagramm](#Linendiagramm)
        4. [Linendiagramm](#Linendiagramm)
    2. [Visualisierung mit amChart](#Visualisierung)
        1. [Library](#Library)
        2. [container](#container)
        3. [Treemap](#Treemap)
            1. [Biokapazität Treemap](#Biocapacity)
            2. [Ökologischer Fußabdruck](#Ökologischer Fußabdruck)
            3. [Treemap Text](#Treemap Text)
            4. [Treemap hover methoden](#Treemap hover methoden)
        4. [XYChart](#XYChart)
            1. [series](#series)
            2. [Legende](#Legende)
        5. [Events](#Events)
        6. [Interaction](#Interaction)
 
6. [Vergleich der Framworks amCharts und D3.js](#Vergleich der Framworks amCharts und D3.js)
6. [Erkenntnisse](#Erkenntnisse)
7. [Fazit](#Fazit)

## Einführung
In diesem Semester wurden als Thema die Sustainable Development Goals der UN behandelt. 
Diese beinhalten 17 Ziele zur nachhaltigen Entwicklung, die von den Vereinten Nationen erreicht werden sollen. 
Die Ziele sollen bei der Sicherung einer nachhaltigen Entwicklung auf ökonomischer, sozialer sowie ökologischer Ebene behilflich sein. Im Rahmen der Lehrveranstaltung Grundlagen der Datenvisualisierung, die von Prof. Dr. Till Nagel an der Hochschule Mannheim gehalten wurde, fand ein Visualisierungsprojekt statt. In diesem Projekt konzentrierten wir uns auf den ökologischen Fußabdruck, welches mehrere Sustainable Development Goals beninhaltete. Für die Visualisierung wurden die Daten der G20-Staaten herangezogen. Der ökologischer Fußabdruck ist eine Metrik, mit der erfasst werden kann, wie viel Biokapazität vorhanden ist und wie diese genutzt wird, um unseren Lebensstandard aufrechtzuerhalten. Die Differenz zwischen der Biokapazität und dem ökologischen Fußabdruck ergibt bei einem positiven Wert eine Reserve und bei einem negativen Wert ein Defizit. 

## These
Ein hoher ökologischer Fußabdruck eines Landes besagt nicht, dass der ökologische Fußabdruck pro Kopf des jeweiligen Landes ebenfalls hoch sein muss.

## Daten
### Datenquelle
Das Global Footprint Network stellt Daten zum ökologischen Fußabdruck zur Verfügung (  <https://www.footprintnetwork.org/>). Es basiert auf einer einfachen, unkomplizierten Abrechnung. Die erhobenen Daten werden von der UN von 1961 bis 2014 zur verfügung gestellt und sind als CSV-Datei frei verfügabar. 

### Datenerhebung
Für das Projekt wurden die G20-Staaten berücksichtigt. Diese sind in der Datenbank des "Footprintnetwork" detailliert vorhanden. Es bestand keine Herausforderung bei der Beschaffung der Daten, weil diese frei zugänglich sind. Die benötigten Daten wurden seperat heruntergeladen, weil diese nicht aggregiert vorhanden waren. Die vorhandenen Daten setzen sich aus folgenden Informationen zusammen: Biokapazität (die im Ökosystem vorhandene Ressourcen, die wir benötigen, um unser Lebensstand aufrecht zu erhalten), ökologischen Fußabdruck (Verbrauch der natürlichen Ressourcenn im ökosystem), Built-Up-Land (benötigte Fläche für Infrastruktur), Carbon (Aufnahme von CO-Emission), Forest Products (Verbrauch Bauholz), Fishing Grounds (Fang und Verbrauch von Fisch), Cropland (Getreidekapazität) und Grazing Land (Weidevieh- und Fleischverbrauch). Die Daten sind jeweils für ein ganzes Land und für Einwohner eines Landes vorhanden.

### Datenaufbereitung
Die erhobenen Daten wurden für die Analyse aufbereitet und bereinigt. Die Informationen in der CSV-Datei sind in einer Spalte vorhanden. Für die Weiterbearbeitung werden diese in separate Spalten aufgeteilt. Anschließend wurden diese auf Vollständigkeit überprüft und ggf. ergänzt/gelöscht. Die Zeichensezung für Komma- und Punktsetzungen wurden an das jeweilige Zielformat angepasst. Die separaten Daten für die einzelnen Länder wurden für die erste Visualisierung in Tableau in eine Excel-Datei zusammengefügt.

### Prozess
Im Visualisierungsprozess wurden die aggregierten Daten im ersten Schritt in Tableau visualisiert. Das Ziel dieses Prozesses war eine schnelle und einfache Visulisierung der Daten, um erste Erkenntnisse zu gewinnen und zu prüfen, ob die ausgewählten Visualisierungstechniken die These unterstützen. Die Ergebnisse der Visualisierungen waren eindeutig, die ausgewählten Visualisierungstechniken konnten die Daten nach den Anforderungen visualisieren.

## Prototypen

### Visualisierung mit D3.js

Für die Implementierung des Prototyps haben wir uns für eine Webseite entschieden. Diese wurde mit den folgenden Technologien umgesetzt:

* Node.js
* D3.js
* jQuery
* Bootstrap

Anfangs hatten wir uns für die JavaScript-Bibliothek amCharts entschieden. Mit dieser hatten wir jedoch Probleme, unsere gewünschten Interaktionen darzustellen. Deshalb entschieden wir uns letztendlich für das Framework D3.js, da wir mit diesem unsere Interaktionen nach etwas Einarbeitungszeit besser umsetzen konnten. Das Ausführen der Webseite wurde mit Hilfe von Node.js durchgeführt.<br>
Anhand der eingespeisten JSON-Datei, die sämtliche relevanten Daten für den totalen Vergleich und den Pro-Kopf-Vergleich enthält, visualisierten wir die Werte für den ökologischen Fußabdruck so, dass diese entsprechend ihrer prozentualen Werte auf den beiden Treemaps dargestellt wurden. So wird bspw. China in der totalen Ansicht als Land mit dem größten ökologischen Fußabdruck auch das größte Rechteck in der Treemap zuteil.

#### Treemap
Für die Darstellung des ökologischen Fußabdrucks und der Biokapazität wurden zwei verschachtelte Treemaps benutzt. Eine Treemap dient der Visualisierung von hierarchischen Strukturen, die hierbei durch ineinander verschachtelte Rechtecke dargestellt werden. Damit können Größenverhältnisse veranschaulicht werden, indem die Flächen der Rechtecke proportional zur Größe der darzustellenden Werte gewählt werden. Für den optischen Vergleich unter den Werten der beiden Treemaps wurden diese dynamisch anhand der Größe angepasst. Damit lassen sich Rechtecke der oberen Treemap mit den Rechtecken der unteren Treemap optisch vergleichen. Dies wurde realisiert, indem die Treemap, die als Summe seiner dargestellten Werte kleiner ist als die andere Treemap, proportional zu den Werten mit der Größe seiner Fläche angepasst wird. Diese Funktion bietet neben dem optischen Vergleich unter den Treemaps auch die schnelle Übersicht darüber, ob bei den vergleichenden Werten eine Reserve oder ein Defizit besteht. In den ersten Ebenen der Treemaps werden alle G20-Staaten mit ihren absoluten Werten bzgl. Fußabdruck und Biokapazität abgebildet. In der oberen Treemap wird der ökologische Fußabdruck der G20-Staaten, entweder im Gesamtverbrauch oder als Pro-Kopf-Einheit dargestellt. In der unteren Treemap wird analog dazu die vorhandene Biokapazität dargestellt. Die zweite Ebene ist durch ein Klick-Event zu erreichen, welches die Zusammensetzung der Indikatoren für den Fußabdruck (in der oberen Treemap) und der Biokapazität (in der unteren Treemap) des jeweiligen Staates in der Treemap darstellt. 
Mit der Interaktiontechnik „Mouseover“ wird das ausgewählte Land in alle Visualisierungen im Dashboard hervorgehoben. 

**Ökologischer Fußabdruck der G20-Staaten**

![](/images/footprint/TreemapperTotal.PNG)

**Ökologischer Fußabdruck pro Kopf G20-Staaten**

![](/images/footprint/TreemapCapita.PNG)

Das folgende Code-Fragment beschreibt grob, wie eine Treemap in D3.js generiert wird.

```javascript
function makeBioChart(path, year){
  document.getElementById("chart").insertBefore(bioSvg.node().parentNode, document.getElementById("mainCard"));

  d3.json(path, function (rawdata) {
	.
	.
	.
  }
```


Nachfolgend findet per `nest()`-Methode eine Verschachtelung innerhalb der Treemap statt.
```javascript
    var data = d3.nest()
      .key(function(d) { return d['year']})
      .key(function(d) { return d['Country Name']})
      .rollup(function(d) { return [
        {name: "Built-Up Land", count: parseFloat((""+d[0]["Built-up Land"]).replace(",", ".")).toFixed(2)},
        {name: "Carbon", count: parseFloat((""+d[0]["Carbon"]).replace(",", ".")).toFixed(2)},
        {name: "Cropland", count: parseFloat(( "" + d[0]["Cropland"]).replace(",", ".")).toFixed(2)},
        {name: "Fishing Grounds", count: parseFloat((""+d[0]["Fishing Grounds"]).replace(",", ".")).toFixed(2)},
        {name: "Forest Products", count: parseFloat((""+d[0]["Forest Products"]).replace(",", ".")).toFixed(2)},
        {name: "Grazing Land", count: parseFloat((""+d[0]["Grazing Land"]).replace(",", ".")).toFixed(2)},
      ]
      })
      .entries(rawdata);
    
```

#### Säulendiagramm

Um die Länder bezüglich deren Reserve/Defizit untereinander zu vergleichen, wurde ein Säulendiagramm benutzt. Dabei wurden die Säulen nach den Werten Reserve/Defizit absteigend sortiert, damit auf einen Blick der Rang bzgl. „gutem Fußabdruck“ der Länder zu erkennen ist. Das Säulendiagramm, das sowohl positive als auch negative Werte darstellt, lässt durch die unterschiedlichen Farben der Säulen (grün für positive und rot für negative Werte) sofort erkennen, ob ein Land eine Reserve oder ein Defizit aufweist. Die Entscheidung, diese Reserven/Defizite der Länder mit dieser Visualisierungstechnik zu realisieren wurde getroffen, da sich ein Rang unter mehreren Objekten sehr gut mit einem Säulendiagramm darstellen lässt. Ob sich diese Visualisierungstechnik für das Abbilden von 20 Werten (G20-Staaten) eignet, musste jedoch erst in Tableau getestet werden, da man befürchtete, dass es zu unübersichtlich werden könnte. Selbstverständlich interagiert das Säulendiagramm mit den anderen Diagrammen auf dem Dashboard, auf dem sie auch vorhanden ist. Eine mögliche Interaktion ist zum Beispiel, dass ein anderes Jahr im Dashboard ausgewählt wird, woraufhin sich das Säulendiagramm direkt anpasst und die Werte des ausgewählten Jahres darstellt. Ebenfalls werden bei einem „Mouseover“ auf einem Land beim Säulendiagramm dasselbe Land auf den anderen Diagrammen des Dashboards mit einer Hervorhebung angezeigt. Dies gilt analog auch im umgekehrten Sinne.

![](/images/footprint/Saulendiagramm.PNG)

Anbei kann man sehen, wie anhand der `makeBarChart`-Methode das Säulendiagramm aufgebaut ist.

```javascript
function makeBarChart(path, capitaDef, year){
  document.getElementById("chart").insertBefore(barSvg.node().parentNode, document.getElementById("mainCard"));

  d3.json("./data/Defizit.json", function(error, rawdata) {
    if (error) throw error;
  
    // format the data
    var data = []
    for(var i in rawdata){
      if(rawdata[i].year == year){
          data.push({name: rawdata[i]["Country Name"], value: rawdata[i][capitaDef]})
          }
      }
  
    data = data.sort(function(a, b){return parseFloat(b.value) - parseFloat(a.value)});
.
.
.
}
```

#### Linendiagramm
Durch die begrenzte Zeit konnte die Visualisierung des Linendiagramms nicht umgesetzt werden. Das Liniendiagramm ist als Konzept dargestellt. Für die Veranschaulichung der zeitlichen Entwicklung des ökologischen Fußabdrucks und der Biokapazität eines Staates wurde ein Liniendiagramm verwendet. Hier ist zu erkennen, wie sich diese Werte von 1961 bis 2014 entwickelt haben. Die Farben der Linien wurden dabei den Farben aus den Treemaps (Fußabdruck=rot & Biokapazität=grün) angepasst. Dadurch ist auf einem Blick zu erkennen, ob und zu welchem Zeitpunkt die Linie des Fußabdrucks über oder unter der Linie der Biokapazität ist, wodurch abzuleiten ist, ob eine Reserve oder ein Defizit besteht. 

### Visualisierung mit amChart
[Amcharts V4](https://www.amcharts.com/docs/v4/) ist die aktuellste Version von amChart. Diese Version unterstütz die Interaktionen zwischen den Charts. Mit Hilfe der Dokumentationen hat man ein Überblick über die Möglichkeiten, um die Charts zu bauen, verändern oder anzupassen. Auch die Demos und die Beispiele auf der Webseite von amChart waren sehr hilfreich um unser Dashboard zu bauen. Da Version 4 von amChart relativ neu und nicht so bekannt ist und sich deutlich von den vorherigen Versionen unterscheidet, haben wir uns dafür entschieden, die einzelnen Elemente der Webseite genauer per Code-Fragmente zu erläutern. Zudem werden die Charakteristika des Frameworks amChart untersucht und per Ampel-Prinzip bewertet.

- <span style="color:green">Kostenlos solange man es nicht kommerziell verwendet</span>
- <span style="color:green ">Design ist schön und dynamisch</span>
- <span style="color:green ">TypeScript Unterstützung</span>
- <span style="color:green ">Code ist verständlich</span>
- <span style="color:green">Dynamik braucht kein extra code</span>
- <span style="color:green">Dokumentation ist OK</span>
- <span style="color:GoldenRod">Treemap hat wenige Methoden</span>
- <span style="color:red ">Internet Community, weil die Version 4 sehr aktuell und noch unbekannt ist</span>



![amChart](/images/footprint/amChart.gif)

#### Library
Das Dashboard wurde mit [`JavaScript`](https://www.javascript.com) geschrieben und basiert auf der JavaScript-Laufzeitumgebung [`NodeJS`](https://nodejs.org). Zusätzlich nutzten wir das Framework [`ExpressJS`](https://expressjs.com), um eine statische Website zu erstellen.<br>
Alle Daten waren in ein JSON-Objekt namens data.json gespeichert. Problematisch war es, dieses JSON-Objekt anzubinden bzw. zu filtern. Es war zeitaufwendig herauszufinden, wie man die data.json filtert, um diese an den Charts anzubinden, da die data.json sehr groß und komplex war.<br>
Die Library [`lodash`](https://lodash.com) bietet einige Hilfsfunktionen, um die data.json zu filtern. Es war am Ende mehr Filter-Code (<span style="color:gray">260 Liniecode</span>) als Dashboard-Code (<span style="color:gray">180 Liniecode</span>). Es wäre einfacher, für jedes Chart eine separate JSON-Datei mit den jeweiligen Daten zu haben.

#### [container](https://www.amcharts.com/docs/v4/concepts/svg-engine/containers/)
Es empfehlt sich ein amChart-Container zu erstellen, um alle Charts zu erstellen und eine Dashboard-Sicht zu generieren, damit eine bessere Übersicht für die Interaktion zwischen den Charts dargestellt werden kann. Änderungen in HTML oder CSS, um das Dashboard anzupassen bzw. zu ändern, sind nicht mehr notwendig. <br>
Die Treemaps sind unterschiedlich groß, weil diese sich an den Zahlen sich orientieren. Je größer die Zahlen, desto größer die Treemap.


```javascript
var container = am4core.create("chartdiv", am4core.Container); 
container.width = am4core.percent(100);
container.height = am4core.percent(100);
```

#### [Treemap](https://www.amcharts.com/docs/v4/chart-types/treemap/)
Wir haben zuerst zwei Treemaps erstellt, wie auf der amchart-Webseite vorgeschrieben, und diese an den Container positioniert.

##### Biocapacity Treemap (treemapGreen)
In dieser Treemap haben wir einen sogenannten Simple-Treemap erstellt, um die Biokapazität und den Key zu definieren, um diese später an das data.json zu verknüpfen.

```javascript
var treemapGreen = container.createChild(am4charts.TreeMap);
    treemapGreen.hiddenState.properties.opacity = 0;
    treemapGreen.align = "right";
    treemapGreen.minGridDistance = 100;
    treemapGreen.width = am4core.percent(50);
    treemapGreen.height = am4core.percent(50);
    // keys
    treemapGreen.homeText = "Biocapacity";
    treemapGreen.dataFields.color = "color";
    treemapGreen.dataFields.value = "value";
    treemapGreen.dataFields.name = "name";
```
<img src="/images/footprint/treemapGreen.png" alt="" width="300" height="500" />




##### Ecological Footprint Treemap (treemapRed)
Hier würde eine Drill-Down-Treemap erstellt. Damit kann man auf ein Land klicken, um die dazugehörigen Children-Daten anzugzeigen. Die Children-Daten stellen hier die spezifischen Daten eines Landes dar. Beim Klicken auf ein Land werden die spezifischen Daten dargestellt.

```javascript
var treemapRed = container.createChild(am4charts.TreeMap);
    treemapRed.hiddenState.properties.opacity = 0;
    treemapRed.width = am4core.percent(50);
    treemapRed.height = am4core.percent(50);
    treemapRed.align = "left";
    treemapRed.padding(0, 0, 0, 0);
    treemapRed.data = processData(data);
    treemapRed.maxLevels = 1;
    treemapRed.dataFields.value = "value";
    treemapRed.dataFields.name = "name";
    treemapRed.dataFields.color = "color";
    //Children Data
    treemapRed.dataFields.children = "children";
    treemapRed.homeText = "Ecological Footprint";
```
<img src="/images/footprint/treemapWorld.png" alt="" width="300" height="500" />
<img src="/images/footprint/treemapChina.png" alt="" width="300" height="500" />


##### Treemap Text 
Dieser Code ist für die Treemaps, um die einzelnen Ebenen mit Text und Mausverhalten darzustellen.
Bsp. <br/>
Erste  ebene  = var level0SeriesTemplate<br/>
Zweite ebene  = var level1SeriesTemplate

```javascript
treemap.navigationBar = new am4charts.NavigationBar();

    var level0SeriesTemplate = treemap.seriesTemplates.create("0");
    level0SeriesTemplate.strokeWidth = 2;
    var bullet0 = level0SeriesTemplate.bullets.push(
        new am4charts.LabelBullet()
    );
    bullet0.locationX = 0.5;
    bullet0.locationY = 0.5;
    bullet0.label.text = "{name}";
    bullet0.label.fill = am4core.color("#ffffff");
```
#####  Treemap hover methoden
Dieser Code ist für den Schwebeeffekt über die Treemaps zuständig. Hier war es aus zeitlichen Gründen nicht möglich, dass sich das Verhalten bei beiden Treemaps gleich ist. Geplant war, dass wenn man auf der Treemap auf ein Land mit den Mauszeiger druber schwebt, dass das jeweilige Land auf der anderen Treemap gleichesmaßen hervorgeboen wird.
```javascript
    // ein hover erstellen
    var hoverState = level0SeriesTemplate.columns.template.states.create("hover");
    // beim drauf havern dimmen
    hoverState.adapter.add("fill", (fill, target) => {
        return am4core.color(am4core.colors.brighten(fill.rgb, -0.2));
    });
```
#### [XYChart](https://www.amcharts.com/docs/v4/chart-types/xy-chart/)
Dieser Chart ist etwas übersichtlicher als das Treemap und ist besser dokumentiert.
```javascript
    var chart = container.createChild(am4charts.XYChart);
    chart.height = am4core.percent(50);
    chart.valign = "bottom";
    chart.hiddenState.properties.opacity = 0;

    var dateAxis = chart.xAxes.push(new am4charts.DateAxis());
    var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.tooltip.disabled = true;
```
##### [series](https://www.amcharts.com/docs/v4/concepts/series/)
Hier wird das Verlauf der Zeitlinie erstellt.<br>
<br>
Biocapacity linie
```javascript
    var series = chart.series.push(new am4charts.LineSeries());
    series.dataFields.dateX = "date";
    series.dataFields.valueY = "Bio";
```

 Ecological linie
```javascript
    var series = chart.series.push(new am4charts.LineSeries());
    series.dataFields.dateX = "date";
    series.dataFields.valueY = "Eco";
```
![axes](/images/footprint/selectAxesZoomSelect.png)

Darstellung und Feature anpassung.
```javascript
//farbfläche und die anzeige info gesetzt
    series.fill = am4core.color("#DC143C");
    series.fillOpacity = 0.3;
    series.sequencedInterpolation = true;
    series.defaultState.transitionDuration = 1500;
    series.stroke = "#228B22";
    series.tensionX = 0.8;

// info text setzten
    series.tooltipText = "Bio: {valueY.value}";

// farbe 
    series.fill = am4core.color("#228B22");
    series.fillOpacity = 0.3;

// maus Curser und zoom auswahl
    chart.cursor = new am4charts.XYCursor();
    chart.cursor.xAxis = dateAxis;
    chart.scrollbarX = new am4core.Scrollbar();
```
![axes](/images/footprint/zoom.png)
![axes](/images/footprint/selectAxesZoom.png)


##### [Legende](https://www.amcharts.com/docs/v4/concepts/legend/)
Die Legende funktioniert nur bei Simple-Treemap und XYChart. Bei der Drill-Down Treemap kam es zu einigen UI-Fehlern. Es wurde nur in dem XYChart verwendet, da es in der Treemap nicht notwendig ist.
```javascript
//zeige legende
chart.legend = new am4charts.Legend();
chart.legend.useDefaultMarker = true;

// form der legende
var marker = chart.legend.markers.template.children.getIndex(0);
    marker.cornerRadius(12, 12, 12, 12);
    marker.strokeWidth = 2;
    marker.strokeOpacity = 1;
    marker.stroke = am4core.color("#ccc");
```
Ein schöner Effekt bei Legenden, dass man es auch als Filter benutzen kann.<br>
<img src="/images/footprint/axesfilter.png" alt="" width="300" height="500" />



#### [Events](https://www.amcharts.com/docs/v4/concepts/event-listeners/)
Wir haben leider sehr wenige interaktive Funktionen für unseren Treemaps gefunden. In Chrome-Debugger haben wir eine Methode gefunden, die den Namen des Zustandes liefert, welche momentan anzeigt wird.

```
treemapRed.currentlyZoomed.name
```

Nach einer sehr langen Suche in der amchart-Doku und Testen im Chrome-Debugger sind wir auf diese Funktion als Lösung für die Interaktionen gekommen.<br>
Wir verwenden treemapRed als Navigation Chart.
```javascript
//event methode für treemapRed mausklick
treemapRed.events.on("hit", function (ev) {
// zeigt name wo die Drilldown Treemap sich befindet
treemapRed.currentlyZoomed.name
}, this);
```
#### Interaction
Wichtig zu erwähnen ist es hier, dass zuerst die Charts erstellt und mit Daten geladen werden müssen, um eine Startseite anzuzeigen. Ansonsten startet man eine leere Seite und man kann auf nichts klicken. Hier wird mit allen Daten der G20-Ländern gestartet.<br>

![start](/images/footprint/start.png)

In der Interaktion stößt man auf das Problem, dass die Klicks entweder zu spät oder zu früh reagieren. Wir haben die `setTimeout()`-Methode verwendet, um das Klickverhalten zu verbessern, weil die dynamische Visualisierung Zeit braucht. Der Name des aktuellen Zustands wird an die Methode für die Daten-Filterung übergeben.


```javascript
treemapRed.events.on("hit", function (ev) {
  setTimeout(() => {
    // zeigt die G20 länder oder ein land verlaufs daten
    axisChart.data = processTime(data, treemapRed.currentlyZoomed.name);
    // zeigt spätzlefische länder daten oder zeigt die länder sicht
    treemapGreen.data = processBio(data, treemapRed.currentlyZoomed.name);
  }, 500);
}, this);
```

### Vergleich der Framworks amCharts und D3.js
Beim Arbeiten mit den beiden Frameworks fiel uns auf, dass sich mit amCharts deutlich leichter unterschiedliche Charts erstellen lassen. Zwar ist die Auswahl an Charts in amChart deutlich bschränkter als in D3.js, für unsere Zwecke hätte es allerdings gereicht. Allerdings war es uns nicht möglich, unsere Vorstellungen bzgl. der Interaktion der Treemaps, wie z.B. komplexeres Hovern einzelner Elemente, umzusetzen. Zudem gestaltete es sich als schwierig, die proportionalen Unterschiede zwischen den Treemaps deutlicher darzustellen. Dieses Problem hatten wir mit D3.js nicht. Allgemein lässt sich festhalten, dass mit D3.js deutlich besser Visualisierungen umsetzen lassen, jedoch bedarf es einiges an Einarbeitungszeit sich mit dem Framework vertraut zu machen.


## Erkenntnisse
Unsere anfangs aufgestellte Hypothese, dass es erhebliche Unterschiede zwischen der absoluten- und der Pro-Kopf-Ansicht gibt, konnte bestätigt werden. 
Während im Jahr 2014 in der absoluten Ansicht China bei weitem den höchsten ökologischen Fußabdruck aller G20-Staaten aufweist, führen bei den Pro-Kopf-Werten die Vereinigten Staaten, dicht gefolgt von Kanada. 
Bei der Biokapazität ergibt sich ebenfalls ein neues Bild. Bei Ansicht der absoluten Werte führt Brasilien vor China. Da Brasilien aber mit seinen knapp 210 Millionen Einwohnern ein sehr bevölkerungsreiches Land ist, liegt es in der Pro-Kopf-Ansicht lediglich auf dem dritten Platz. Hier führt Kanada, gefolgt von Australien auf einem zweiten Rang. Des Weiteren lässt sich außerdem festhalten, dass China als vermeintlich größter Umweltverschmutzer bei der Pro Kopf-Ansicht zwar immer noch eine negative Bilanz aufweist, allerdings weisen fünf G20-Länder eine deutlich schlechtere Bilanz auf.

## Fazit
Im Gegensatz zu allgemein üblichen Herangehensweise, lediglich die einzelnen Länder als Ganzes danach zu beurteilen, wie sehr sie zur allgemeinen Umweltverschmutzung beitragen, wollten wir herausfinden, ob sich etwas an dem Bild der größten Umweltverschmutzer ändert, wenn man die Bevölkerungsanzahl der untersuchten Länder berücksichtigt. 
Dabei war es zunächst schwierig einen einheitlichen Datensatz zu finden. Die zu Verfügung stehenden Datensätze mussten letztlich angepasst werden, um unserem Vorhaben zu entsprechen. Zudem musste unsere ursprünglich aufgestellte Hypothese dem Datensatz angepasst werden, da der dieser nicht alle Elemente für unsere Hypothese enthielt.
Durch anfängliche Schwierigkeiten bei der Suche nach einem geeigneten Datensatz, hatten wir anfangs auch Schwierigkeiten mit dem Aufstellen einer Hypothese. Dieser Prozess nahm deutlich mehr Zeit in Anspruch als ursprünglich geplant, weshalb wir auf einige Features bei der Interaktion verzichten mussten.
Ferner stellte sich das Arbeiten mit dem zuvor gewählten Framework als problematisch heraus. Mit dem anfänglich gewählten JavaScript-Framework amCharts waren wir nicht im Stande unsere zuvor geplanten Interaktionen umzusetzen. Aus diesem Grund stiegen wir auf die JavaScript-Bibliothek D3.js um. Dadurch entstand zwar ein zusätzlicher Aufwand bzgl. der Einarbeitung, allerdings konnten wir unsere geplanten Interaktionen deutlich besser umsetzen.
