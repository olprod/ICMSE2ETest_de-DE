---
title: Datentabellen
description: Datentabellen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9fd6d934-d6cd-454e-9960-dacf0fe01541
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0a170e4e088d67de553be5e671cddf990dd16824
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="data-tables"></a>Datentabellen


In vielen Fällen ist ein Diagramm die beste Möglichkeit zum Anzeigen von Systemaktivitäten Leistung analysieren. In einigen Fällen ist jedoch eine tabellarische Ansicht vorzuziehen. Wenn Sie ein Diagramm auf der Registerkarte **Analyse** ziehen, wird es selbst angezeigt. Um dieselben Daten in Tabellenform mit dem Diagramm auf eine Miniaturansicht verkleinert anzuzeigen, klicken Sie auf das Symbol Layout ganz rechts auf der Titelleiste des Diagramms. Wenn Sie die Datentabelle und das Diagramm in voller Größe anzeigen möchten, klicken Sie auf das Symbol Layout der am weitesten links auf der Titelleiste des Diagramms.

Die folgende Abbildung zeigt eine Datentabelle WPA.

![WPA-Tabelle](images/wpatable.jpg)

Wenn Sie die vertikale Bildlaufleiste gold beim Öffnen Sie zuerst einer Datentabelle nicht angezeigt werden, führen Sie einen Bildlauf nach rechts.

Die Legende-Spalte auf der rechten Seite der Tabelle entspricht dem Steuerelement **Legende** links neben dem Diagramm verknüpft. Wenn Sie in der **Legende** Steuerelement ein oder mehrere Elemente auswählen, die entsprechenden Zeilen der Tabelle ausgewählt, und umgekehrt.

Die Datentabelle und dem zugehörigen Diagramm werden dynamisch synchronisiert. Wenn Sie Änderungen an der Datentabelle vornehmen, wird im Diagramm diese Änderungen widergespiegelt. Wenn Sie erweitern oder reduzieren einen Knoten im Diagramm **Legende** -Steuerelement, ist in der Datentabelle (und umgekehrt) es auch erweitert oder reduziert. Wenn Sie ein Zeitintervall im Diagramm vergrößern, zeigt die Tabelle nur Daten für den ausgewählten Zeitraum an.

Informationen zum Durchführen von Änderungen an eine Datentabelle finden Sie unter [Anpassen einer Datentabelle](customize-a-data-table.md) und [anwenden, zu erstellen, oder löschen eine voreingestellte Kombination von anzuzeigende Spalten](apply-create-or-delete-a-preset-combination-of-columns-to-display.md).

Informationen zum Suchen und Filtern von Daten finden Sie unter [Suchen oder Filtern von Daten](search-or-filter-data.md).

## <a name="data-table-layout"></a>Tabellenlayout Daten


Die Spalte ganz links ist immer die Zeilennummer Spalte, und die äußersten rechten Spalte ist immer der Legende Spalte das Steuerelement für die **Legende** im entsprechenden Diagramm entspricht. Zwischen diesen beiden äußeren Spalten sind die folgenden Bereiche, von links nach rechts:

-   Bereich

-   Datenbereich

-   Element Bereich Diagramme

### <a name="key-area"></a>Bereich

Dies ist der Bereich auf der linken Seite der Tabelle, zwischen der Zeilennummer Spalte und die vertikale Leiste gold.

Ziehen Sie eine beliebige Spalte im Datenbereich des links neben den vertikalen gold Balken zu vereinfachen ein Schlüssels.

### <a name="data-area"></a>Datenbereich

Dies ist der Bereich in der Mitte der Tabelle, zwischen den vertikalen gold Balken und die blaue vertikale Leiste.

Die Daten für Spalten, die im Datenbereich angezeigt werden, ist weder gruppiert noch im Diagramm angezeigt. Zellen in den folgenden Spalten werden (sofern eine Aggregation für die Spalte angegeben wurde) aggregiert, wenn sie rechts neben der einer Gruppe sind. Zellen in diesen Spalten anzeigen die Daten für die einzelnen Zeilen der Tabelle, die nicht erweitert werden können.

### <a name="graphing-element-area"></a>Element Bereich Diagramme

Dies ist der Bereich auf der rechten Seite der Tabelle, zwischen den vertikalen blauen Balken und der Legende-Spalte. Wenn Sie eine Spalte für diesen Bereich ziehen, generiert die Daten in dieser Spalte Linien oder Balken.

Ist das Diagramm ein Balkendiagramm (Gantt), muss jeder Spalte, die Sie in der Diagrammerstellungsfunktion Elemente verschieben Timestamp-Werte enthalten. Eine der horizontalen Balken im Balkendiagramm mit einem Häkchen stellt einen Zeitstempelwert.

## <a name="related-topics"></a>Verwandte Themen


[WPA-Features](wpa-features.md)

 

 







