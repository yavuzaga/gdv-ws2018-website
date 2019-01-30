[Amcharts V4](https://www.amcharts.com/docs/v4/) ist die aktuellste Version vom Amcharts um Charts zu bauen. Diese Version unterstütz die Interaktionen zwischen den Charts. Mit Hilfe der Dokumentationen hat man ein Überblick über die Möglichkeiten, um die Charts zu bauen, verändern oder anzupassen. Auch die Demos und die Beispiele auf der Hauptwebsite von amChart waren sehr hilfreich um unser Dashboard zu bauen.


- <span style="color:green">Kostenlos solange man es nicht kommerziell verwendet</span>
- <span style="color:green ">Design ist schön und dynamisch</span>
- <span style="color:green ">TypeScript Unterstützung</span>
- <span style="color:green ">Code ist verständlich</span>
- <span style="color:green">Dynamik braucht kein extra code</span>
- <span style="color:green">Dokumentation ist OK</span>
- <span style="color:GoldenRod">Treemap hat wenige Methoden</span>
- <span style="color:red ">Internet Community, weil die Version 4 sehr aktuell und noch unbekannt ist</span>



![amChart](/images/footprint/amChart.gif)

### Library
Das Dashboard wurde mit [`JavaScript`](https://www.javascript.com) geschrieben und basiert auf der JavaScript Laufzeitumgebung [`NodeJS`](https://nodejs.org). Zusätzlich nutzten wir die Framework [`ExpressJS`](https://expressjs.com), um eine statische Website zu erstellen.<br>
Alle daten waren gespeichert in eine JSON-Objekt im einem file namens data.js. Problematisch war es dieses JSON-Objekt anzubinden bzw. zu filtern. Es war Zeit aufwendig um heraus zu finden wie man die data.json filtert um diese an den Charts anzubinden, da die data.json sehr gross und komplex war.<br>
Die Library [`lodash`](https://lodash.com) bietet einige Hilfsfunktionen, um die data.json zu filtern. Es war am Ende mehr Filter Code (<span style="color:gray">260 Liniecode</span>) als Dashboard Code (<span style="color:gray">180 Liniecode</span>). Es wäre einfacher, dass man für jede Chart eine JSON Datei mit den jeweiligen Daten hätte, die man dazu braucht.

#### [container](https://www.amcharts.com/docs/v4/concepts/svg-engine/containers/)
Es empfehlt sich ein amchart Container zu erstellen, um alle Charts hinein zu bauen und eine Dashboard Sicht zu erstellen, damit eine bessere Übersicht für die Interaktion zwischen den Charts dargestellt werden. Änderung in HTML oder CSS um das Dashboard anzupassen bzw. zu ändern ist nicht mehr notwendig. <br>
Die Treemaps sind unterschiedlich groß, weil ihre Größe sich an die zahlen sich orientieren. Desto größer die zahlen desto größer das Treemap.


```javascript
var container = am4core.create("chartdiv", am4core.Container); 
container.width = am4core.percent(100);
container.height = am4core.percent(100);
```

#### [Treemap](https://www.amcharts.com/docs/v4/chart-types/treemap/)
Wir haben zuerst zwei Treemaps erstellt, die auf der amchart Webseite vorgeschrieben werden und auch an das countainer positioniert sind.

##### Biocapacity Treemap (treemapGreen)
In diesem Treemap haben wir ein sogenannten Simple-treemap erstellt um die Biocapacity und die key definiert um die später an das data.json zu verknüpfen.

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
Hier würde ein Drill-down Treemap erstellt. Damit kann man auf ein Land klicken um die dazugehörige Children Daten anzugzeigen. Die Children Daten stellen hier die spezifische Daten eines Landes dar. Beim Klicken auf einen Land, werden die spezifischen Daten dargestellt.

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
Dieser Code ist für die Treemaps, um die einzelne Ebenen mit Text und Mausverhalten darzustellen.
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
Dieser Code ist für das Schwebe Effekt über die Treemaps zuständig. Hier war es aus zeitlichen Gründen nicht möglich, dass sich das Verhalten bei beiden Treemaps gleich ist. Geplant war, dass wenn man auf ein Treemap auf ein Land mit den Mauszeiger drauf schwebt und auf das andere Treemap gleiches Land gleiche schwebe verhalten anzuzeigen.
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
Die Legende funktioniert nur bei Simple-treemap und XYChart. Bei Drill-down Treemap kam es zu einigen UI Fehlern. Es würde nur in XYChart verwendet, da es in Treemap nicht notwendig ist.
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
Wir haben leider sehr wenige interaktive Funktionen für unseren Treemaps gefunden. In Chrome debugger haben wir eine Methode gefunden, die den Namen des Zustandes liefert, das momentan anzeigt wird.

```
treemapRed.currentlyZoomed.name
```

Nach sehr lange suche in der amchart Doku und testen in Chrome-Debugger, sind wir auf dieser Funktion als Lösung für die Interaktionen gekommen.<br>
Wir verwenden treemapRed als Navigation Chart.
```javascript
//event methode für treemapRed mausklick
treemapRed.events.on("hit", function (ev) {
// zeigt name wo die Drilldown Treemap sich befindet
treemapRed.currentlyZoomed.name
}, this);
```
#### Interaction
Wichtig hier, bevor die Interaktionen funktionieren, müssen zuerst die Charts erstellt und mit Daten geladen werden, um eine Startseite anzuzeigen. Ansonsten startet man eine leere Seite und man kann auf nichts klicken. Hier wird mit alle G20 Länder Daten gestartet.<br>

![start](/images/footprint/start.png)

In der Interaktion stößt man auf das Problem, das die Klicks entweder zu spät oder zu früh reagieren. Wir haben die `setTimeout()` Methode verwendet um das Klickverhalten zu verbessern, weil die dynamische Visualisierung Zeit braucht. Name des aktuellen Zustands wird an die Methode für Daten Filterung übergeben.


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
