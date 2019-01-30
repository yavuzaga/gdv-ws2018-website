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
author: Yavuz Azal, Arif Bozkurt, Benedikt Herbst, Vu Tuannah, Thear Aldefai 
---

## Abstract
Jeden Tag verbrauchen wir Resourcen der Erde und erzeugen Müll. Dabei vergessen wir, dass diese Resourcen der Erde endlich sind. Mittleweile verbauchen wir Menschn mehr Resourcen, als auf der Erde vorhanden sind. Diesen Verbrauch den wir erzeugen, wird als den ökologischen Fußabdruck dargestellt. Der ökologischer Fußabdruck ist eine Metrik, mit der erfasst werden kann, wie viel Biokapazität vorhanden ist und wie diese genutzt wird, um unseren Lebensstandard aufrechtzuerhalten. 

## Inhalt
1. [Einführung](#Einführung)
2. [These](#These)
3. [Daten](#Daten)
    1. [Datenquelle](#Datenquelle)
    2. [Datenerhebung](#Datenerhebung)
    3. [Datenaufbereitung](#Datenaufbereitung)
4. [Visualisierung](#Visualisierung)
    1. [Prozess](#Prozess)
    2. [Treemap](#Treemap)
    3. [Säulendiagramm](#Säulendiagramm)
    4. [Linendiagramm](#Linendiagramm)
5. [Prototyp/Ergebnisse](#Prototyp/Ergebnisse)
6. [Implementierung](#Implementierung)
7. [Fazit](#Fazit)

## Einführung
In diesem Semester wurden als Thema die Sustainable Development Goals der UN behandelt. 
Diese beinhalten 17 Ziele zur nachhaltigen Entwicklung, die von den Vereinten Nationen erreicht werden sollen. 
Die Ziele sollen bei der Sicherung einer nachhaltigen Entwicklung auf ökonomischer, sozialer sowie ökologischer Ebene behilflich sein. Im Rahmen der Lehrveranstaltung Grundlagen der Datenvisualisierung, die von Prof. Dr. Till Nagel an der Hochschule Mannheim gehalten wird, findet ein Visualisierungsprojekt statt. In diesem Projekt konzentrieren wir uns auf den ökologischen Fußabdruck, welches mehrere Sustainable Development Goals beninhaltet. Für die Visualisierung wurden die Daten der G20-Staaten herangezogen. Der ökologischer Fußabdruck ist eine Metrik, mit der erfasst werden kann, wie viel Biokapazität vorhanden ist und wie diese genutzt wird, um unseren Lebensstandard aufrechtzuerhalten. Die Differenz zwischen der Biokapazität und dem ökologischen Fußabdruck ergibt bei einem Positiven Wert eine Reserve und bei einem negativen Wert einen Defizit. 

## These
Ein hoher ökologischer Fußabdruck eines Landes besagt nicht, dass der ökologische Fußabdruck pro Kopf des jeweiligen Landes ebenfalls hoch sein muss.

## Daten
### Datenquelle
Die Global Footprint Network stellt Daten zum ökologischen Fußabdruck zur Verfügung Quelle:  <https://www.footprintnetwork.org/>. Es basiert auf einer einfachen, unkomplizierten Abrechnung. Die erhobenen Daten werden von der UN seit 1961 bis 2014 zu verfügung gestellt und sind als CSV-Datei frei verfügabar. 

### Datenerhebung
Für das Projekt wurden die G20-Staaten berücksichtigt, diese sind in der Datenbank des "Footprintnetwork" detailliert vorhanden. Es bestandt keine Herausforderung bei der Beschaffung der Daten, weil diese Freizugänglich sind. Die benötigten Daten wurden seperate heruntergeladen, weil diese nicht aggregiert vorhanden waren. Die vorhandenen Daten setzen sich aus folgenden Informationen zusammen Biokapazität (die im Ökosystem vorhandene Ressourcen die wir benötigen, um unser Lebensstand aufrecht zuhalten), ökologischen Fußabdruck (Verbrauch der natürlichen Ressourcenn im ökosystem), Built-Up-Land (benötigte Fläche für Infrastruktur), Carbon (Aufnahme von CO-Emission), Forest Products (Verbrauch Bauholz), Fishing Grounds (Fang und Verbrauch von Fisch), Cropland (Getreidekapazität) und Grazing Land (Weidevieh und Fleisch verbrauch). Die Daten sind jeweils für 
ein ganzes Land und für pro Einwohner eines Landes vorhanden.

### Datenaufbereitung
Die erhobenen Daten wurden für die Analyse aufbereitet und bereinigt. Die Informationen in der CSV-Datei, sind in eine Spalte vorhanden. Für die Weiterbearbeitung werden diese in separate Spalten aufgeteilt. Anschließend wurden diese auf Vollständigkeit überprüft und ggf. ergänzt/gelöscht. Die Zeichensezung für Komma und Punktsetzungen wurden an das jeweilige Zielformate angepasst. Die separaten Daten für die einzelnen Länder wurden in eine Excel zusammengefügt für die erste Visualisierung in Tableau. 

## Visualisierung

### Prozess
Im Visualisierungsprozess wurden die aggregierten Daten im ersten Schritt in Tableau visualisiert. Das Ziel dieses Prozesses war eine schnelle und einfache Visulisierung der Daten, um erste Erkenntnisse zu gewinnen und zu prüfen ob die ausgewählten Visualisierungstechniken die These unterstützen. Die Ergebnisse der Visualisierungen waren eindeutig, die ausgewählten Visualisierungstechniken konnten die Daten nach den Anforderungen visualisieren.

### Treemap
Für die Darstellung des ökologischen Fußabdrucks und der Biokapazität wurden zwei verschachtelte Treempas benutzt. Eine Treemap dient der Visualisierung von hierarchischen Strukturen, die hierbei durch ineinander verschachtelte Rechtecke dargestellt wird. Damit können Größenverhältnisse veranschaulicht werden, indem die Flächen der Rechtecke proportional zur Größe der darzustellenden Werte gewählt wird. Für den optischen Vergleich unter den Werten der beiden Treemaps, wurden diese dynamisch anhand der Größe angepasst. Damit lassen sich Rechtecke des oberen Treemaps mit den Rechtecken des unteren Treemaps optisch vergleichen. Dies wurde realisiert, indem das Treemap, das als Summe seiner dargestellten Werte, kleiner ist als das andere Treemap, proportional zu den Werten mit der Größe seiner Fläche angepasst wird. Diese Funktion bietet neben den optischen Vergleich unter den Treemaps auch die schnelle Übersicht darüber, ob bei den Vergleichenden Werten eine Reserve oder ein Defizit besteht. In der ersten Ebene der Treemaps werden alle G20-Staaten mit ihren absoluten Werten bzgl. Fusabdruck und Biokapazität abgebildet. Im oberen Treemap wird der ökologische Fußabdruck der G20-Staaten, entweder im Gesamtverbrauch oder als pro Kopf-Einheit dargestellt. Im unteren Treemap wird analog dazu die vorhandene Biokapazität dargestellt. Die zweite Ebene ist durh ein Klick-Event zu erreichen, welches die Zusammensetzung der Indikatoren für den Fußabdruck (im oberen Treemap) und Biokapazität (im unteren Treemap) des jeweiligen Staates im Treemap darstellt. 
Mit der Interaktion Technik „Mouseover“ wird das ausgewählte Land in alle Visualisierunge im Dashboard hervorgehoben. 

Ökologischer Fußabdruck der G20-Staaten

![](/images/footprint/TreemapTotal.PNG)


Ökologischer Fußabdruck pro Kopf G20-Staaten

![](/images/footprint/TreemapCapita.PNG)

### Säulendiagramm

Um die Länder bezüglich deren Reserve/Defizit untereinander zu vergleichen, wurde ein Säulendiagramm benutzt. Dabei wurden die Säulen nach den Werten Reserve/Defizit absteigend sortiert, damit auf einen Blick der Rang bzgl. „gutem Fußabdruck“ der Länder zu erkennen ist. Das Säulendiagramm, das sowohl positive als auch negative Werte darstellt, lässt durch die unterschiedlichen Farben der Säulen (grün für positive und rot für negative Werte) sofort erkennen, ob ein Land eine Reserve oder ein Defizit aufweist. Die Entscheidung, diese Reserven/Defizite der Länder mit dieser Visualisierungstechnik zu realisieren, wurde getroffen da sich ein Rang unter mehreren Objekten sehr gut mit einem Säulendiagramm darstellen lässt. Ob sich diese Visualisierungstechnik für das abbilden von 20 Werten (G20-Staaten) eignet, musste jedoch erst im Tableau getestet werden, da man befürchtete, dass es zu unübersichtlich werden könnte. Selbstverständlich interagiert das Säulendiagramm mit den anderen Diagrammen auf dem Dashboard auf dem sie auch vorhanden ist. Eine mögliche Interaktion ist zum Beispiel, dass ein anderes Jahr im Dashboard ausgewählt wird, woraufhin sich das Säulendiagramm direkt anpasst und die Werte des ausgewählten Jahres darstellt. Ebenfalls werden bei einem „Mouseover“ auf einem Land beim Säulendiagramm, das selbe Land auf den anderen Diagrammen des Dashboards mit einer Hervorhebung angezeigt und analog dazu andersrum

![](/images/footprint/Saulendiagramm.PNG)

### Linendiagramm
Durch die begrenzte Zeit konnte die Visualisierung des Linendiagramms nicht umgesetzt werden. Das Liniendiagramm ist als Konzept dargestellt. Für die Veranschaulichung der Zeitlichen Entwicklung des ökologischen Fußabdrucks und der Biokapazität eines Staates wurde ein Liniendiagramm verwendet. Hier ist zu erkennen, wie sich diese Werte von 1961 bis 2014 entwickelt haben. Die Farben der Linien wurden dabei, den Farben aus den Treemaps (Fußabdruck=rot & Biokapazität=grün) angepasst. Dadurch ist auf einem Blick zu erkennen, ob und zu welchem Zeitpunkt die Linie des Fußabdrucks über oder unter der Linie der Biokapazität ist, wodurch abzuleiten ist ob eine Reserve oder ein Defizit besteht. 

Bilder

## Prototyp

## Implementierung
Für die Implementierung des Prototyps haben wir uns für eine Webseite entschieden. Diese wurde mit den folgenden Technologien umgesetzt:

* Node.js
* D3.js
* jQuery
* Bootstrap

Anfangs hatten wir uns für die JavaScript-Bibliothek amCharts entschieden. Mit dieser hatten wir jedoch Probleme, unsere gewünschten Interaktionen darzustellen. Deshalb entschieden wir uns letztendlich für das Framework D3.js, da wir mit diesem unsere Interaktionen nach etwas Einarbeitungszeit besser umsetzen konnten. Für das Ausführen der Webseite wurde per Node.js ausgeführt.
Hier evtl. Bild des D3.js-Gerüsts für die Treemap
Anhand der eingespeisten JSON-Datei, die sämtliche relevanten Daten für den totalen- und den Pro-Kopf-Vergleich enthält, visualisierten wir die Werte für den ökologischen Fußabdruck so, dass diese entsprechend ihrer prozentualen Werte auf den beiden Treemap’s dargestellt wird. So wird bspw. China in der totalen Ansicht als Land mit dem größten ökologischen Fußabdruck auch das größte Rechteck in der Treemap zuteil.

### Vergleich der Framworks amcharts und D3.js
Mit der Bibliothek amCharts lässt sich anhand eines Frameworks relativ schnell eine Drill-Down-Treemap erstellen. Anschließend muss die Demo-Version mit eigenen Daten versehen werden. 


## Erkenntnisse
Unsere anfangs aufgestellte Hypothese, dass es erhebliche Unterschiede zwischen der absoluten- und der Pro-Kopf-Ansicht gibt, konnte bestätigt werden. 
Während im Jahr 2014 in der absoluten Ansicht China bei weitem den höchsten ökologischen Fußabdruck aller G20-Länder aufweist, führen bei den Pro-Kopf-Werten die Vereinigten Staaten, dicht gefolgt von Kanada. 
Bei der Biokapazität ergibt sich ebenfalls ein neues Bild. Bei Ansicht der absoluten Werte führt Brasilien vor China. Da Brasilien aber mit seinen knapp 210 Millionen Einwohnern ein sehr bevölkerungsreiches Land ist, liegt es in der Pro-Kopf-Ansicht lediglich auf dem dritten Platz. Hier führt Kanada, gefolgt von Australien auf einem zweiten Rang. Des Weiteren lässt sich außerdem festhalten, dass China als vermeintlich größter Umweltverschmutzer bei der Pro Kopf-Ansicht zwar immer noch eine negative Bilanz aufweist, allerdings weisen fünf G20-Länder eine deutlich schlechtere Bilanz auf.

## Fazit
Im Gegensatz zu allgemein üblichen Herangehensweise, lediglich die einzelnen Länder als Ganzes danach zu beurteilen, wie sehr sie zur allgemeinen Umweltverschmutzung beitragen, wollten wir herausfinden, ob sich etwas an dem Bild der größten Umweltverschmutzer ändert, wenn man die Bevölkerungsanzahl der untersuchten Länder berücksichtigt. 
Dabei war es zunächst schwierig einen einheitlichen Datensatz zu finden. Die zu Verfügung stehenden Datensätze mussten letztlich angepasst werden, um unserem Vorhaben zu entsprechen. Zudem musste unsere ursprünglich aufgestellte Hypothese dem Datensatz angepasst werden, da der dieser nicht alle Elemente für unsere Hypothese enthielt.
Durch anfängliche Schwierigkeiten bei der Suche nach einem geeigneten Datensatz, hatten wir anfangs auch Schwierigkeiten mit dem Aufstellen einer Hypothese. Dieser Prozess nahm deutlich mehr Zeit in Anspruch als ursprünglich geplant, weshalb wir auf einige Features bei der Interaktion verzichten mussten.
Ferner stellte sich das Arbeiten mit dem zuvor gewählten Framework als problematisch heraus. Mit dem anfänglich gewählten JavaScript-Framework amCharts waren wir nicht im Stande unsere zuvor geplanten Interaktionen umzusetzen. Aus diesem Grund stiegen wir auf die JavaScript-Bibliothek D3.js um. Dadurch entstand zwar ein zusätzlicher Aufwand bzgl. der Einarbeitung, allerdings konnten wir unsere geplanten Interaktionen deutlich besser umsetzen.
