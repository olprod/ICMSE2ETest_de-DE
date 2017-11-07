---
title: Diagramme
description: Diagramme
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 44ccfef7-aaee-4194-a26d-5285e41eb683
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e6ceee999a29d0d663820e908a2bf7b32d5580d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="graphs"></a>Diagramme

Windows Performance Analyzer (WPA) bietet die folgenden Arten von Diagrammen:

-   [Liniendiagramme](#line_stacked_bar)
-   [Gestapelte Liniendiagramme](#line_stacked_bar)
-   [Gestapelte Balkendiagramme](#line_stacked_bar)
-   [Flamme Diagramme](#flame_graphs)
-   [Gültigkeitsdauer für Diagramme](#lifetime_graphs)
-   [Aktivität Typ Diagramme](#activity_type_graphs)
-   Sequenzielle Ressource Prüflisten
-   [Generische Ereignisse Diagramme](#generic_events_graphs)

<a name="line_stacked_bar"></a>
## <a name="line-stacked-line-and-stacked-bar-graphs"></a>Zeile, Gestapelte Linie und gestapelte Balken-Diagrammen

Wenn Sie eine Zeile, Gestapelte Linie oder gestapelte Balken Diagramm aus dem **Diagramm Explorer** -Fenster auf der Registerkarte **Analyse** ziehen, wird sie als Liniendiagramm, wie in der folgenden Abbildung dargestellt.

![Liniendiagramm](images/wpaline.jpg)

Ändern der Darstellung des Diagramms, klicken Sie auf den Dropdownpfeil ganz rechts auf der Titelleiste des Diagramms, und wählen Sie **Zeilen gestapelt** oder **Gestapelte Balken**.

Die folgende Abbildung zeigt das gleiche Diagramm als Diagramm Gestapelte Linie.

![Gestapelte Liniendiagramm](images/wpastackedline.jpg)

Die folgende Abbildung zeigt das gleiche Diagramm als ein gestapeltes Balkendiagramm.

![Gestapeltes Balkendiagramm](images/wpastackedbar.jpg)

Sie können 4 bis 100 Intervalle für ein gestapeltes Balkendiagramm angeben.

<a name="flame_graphs"></a>
## <a name="flame-graphs"></a>Flamme Diagramme

*Flamme Diagramm* ist eine Diagrammerstellungsfunktion Modus, in dem Sie Datenwerte aus der Tabelle schnell vergleichen kann. Die Breite jeder *Gruppe Flamme* wird durch die Weight-Wert in der Ansicht bestimmt. Beispielsweise wird die Gewichtung der einzelnen Frame mit CPU-Stapel durch seine Breite angezeigt. Dieser Modus eignet sich am besten, wenn Sie Daten für eine bestimmte gefiltert haben.

Zum Wechseln zur Flamme Diagramm, stellen Sie sicher, dass die Tabelle mit Spalten auf der linken Seite des Balkens gold und einer einzelnen numerischen Spalte rechts neben die blaue Leiste mit Summenaggregation konfiguriert ist, und wählen Sie dann aus dem Menü Diagramm am oberen Rand des Diagramms **Flamme** aus. Verwenden Sie alternativ der integrierten **Prozess Stack Flammen** Vorgaben im Diagramm mit **CPU-Auslastung (abgetastete)** .

<img src="images\wpa-select-chart-type-menu.png" alt="Chart menu in WPA." height="170"><br/>

In der folgenden Abbildung ist ein Beispiel der Stichprobe CPU und die Stapel nach unten zu Notepad.exe gefiltert. Im Diagramm **comctl32.dll! TV_DrawTree** ist der größte Frame in die aktuelle gefilterte Ansicht. Von hier aus können Sie den Stapel damit ermittelt wird, in dem die optimale Arbeitsumfang durchgeführt wird durchlaufen.

![Beispiel für Sampling CPU und die Stapel einer kleineren Gruppe gefiltert.](images/wpa-graph-flame-example-CPU-sampled.jpg)

Die Namen der Flamme Gruppen werden angezeigt, wenn der Text eine minimale Höhe gelesen werden. Um eine QuickInfo mit den Daten anzuzeigen, bewegen Sie den Mauszeiger über ein Element im Diagramm Flamme ein. Um die entsprechend Daten in der Tabelle auszuwählen, klicken Sie auf eine Flamme Gruppe um ihn in der Tabelle zu erweitern oder zu filtern, die in Tabelle mit der rechten Maustaste und klicken Sie dann auf **Filter auf Flamme** in der Datenansicht. 

Flamme Diagramme können mit einer beliebigen Reihenfolge der Gruppierungsspalten auf der linken Seite des Balkens Gold konfiguriert werden. Die folgende Abbildung zeigt die Gruppierung von Datenträgerverwendung und Servicezeit. Die QuickInfo für **Normal**, zeigt den Namen und Werte der Gruppe Flamme, unter dem Mauszeiger.

![Flammen Sie Diagramm Beispiel Datenträgerverwendung und Servicezeit mit einer QuickInfo, die angezeigt der Name wird und Wert, der unter dem Mauszeiger Flamme Gruppe an.](images/wpa-graph-flame-example-disk-usage.jpg)

<a name="lifetime_graphs"></a>
## <a name="lifetime-graphs"></a>Gültigkeitsdauer für Diagramme

Lebensdauer Diagramme zeigen einzelne Kategorien, z. B. Prozesse, die als horizontale Balken, die die Lebensdauer der Kategorie definieren.

Die folgende Abbildung zeigt ein Prozess Lebensdauer Diagramm.

![Prozess Lebensdauer Diagramm](images/processlifetime.jpg)

<a name="activity_type_graphs"></a>
## <a name="activity-type-graphs"></a>Aktivität Typ Diagramme

Aktivität Typ Diagramme verwenden horizontale Balken Typen von Aktivität anzeigen. Auf jede Leiste ist die Zeit der Aktivität grau schattiert dargestellt. Wenn Sie über ausreichende Details auf diese Art von Grafik, Sie sehen können vergrößern, benötigte wie lange auf jedem Datenträger lesen oder Schreiben beispielsweise.

Die folgende Abbildung zeigt die Eingabe- und Ausgabeparameter vom Typ.

![WPA e/a vom Prozess](images/wpaio.jpg)

<a name="generic_events_graphs"></a>
## <a name="generic-events-graphs"></a>Generische Ereignisse-Diagrammen

Allgemeines Ereignis Diagramme werden alle Crimson Ereignisse in der Aufzeichnung anzeigen.

In der folgenden Abbildung ist ein Beispiel für eine generische Ereignisse Grafik.

![WPA generische Ereignisse Diagramm](images/wpagenericevents.jpg)


## <a name="related-topics"></a>Verwandte Themen

[WPA-Features](wpa-features.md)

 

 







