---
title: "Schrittweise Anleitung für Windows Performance Analyzer"
description: "Schrittweise Anleitung für Windows Performance Analyzer"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 53b7dfe1-f39b-41b4-a7ff-6040f1ab318c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8ad0e8f038f19c047dc2a9b20939c249667ac301
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-performance-analyzer-step-by-step-guide"></a>Schrittweise Anleitung für Windows Performance Analyzer


In diesem Abschnitt finden Sie eine detaillierte Vorgehensweise der Funktionen der Windows Performance Analyzer (WPA)-Benutzeroberfläche (UI).

## <a name="step-1-opening-an-etl-file"></a>Schritt 1: Öffnen einer ETL-Datei


WPA kann Ereignis-ablaufverfolgungsprotokolldateien (ETL) öffnen, die mithilfe von Windows Performance-Aufzeichnung (WPR) oder Xperf erstellt werden.

**Zum Öffnen einer ETL-Datei in WPA**

1.  Klicken Sie im Menü **Datei** auf **Öffnen**.

2.  Wenn Sie in einem anderen Speicherort als die Standardeinstellung ETL-Datei gespeichert haben, navigieren Sie zu diesem Speicherort.

    WPR speichert standardmäßig ETL-Dateien in Ihren Dokumenten\\WPR Ordner.

3.  Wählen Sie die gewünschte Datei, und klicken Sie auf **Öffnen**.

Sie können auch WPA von der Ergebnisseite der Bewertung öffnen, die mithilfe der Assessment-Plattform erstellt werden.

**So öffnen Sie WPA über eine Bewertung**

-   Nach dem Ausführen des Auftrags klicken Sie auf den Link **WPA eingehenderen Analysen** im Bereich **Probleme** auf der Seite Ergebnisse anzeigen. Möglicherweise müssen Sie das Problem, um diesen Link finden Sie unter erweitern.

## <a name="step-2-selecting-graphs"></a>Schritt 2: Auswählen von Diagrammen


Alle verfügbaren Diagramme für eine Aufzeichnung werden im Diagramm Explorer-Fenster angezeigt. Erweitern Sie alle Knoten durch Klicken auf das kleine Dreieck. Ziehen Sie dann die Diagrammen auf der Registerkarte **Analyse** , die in voller im Diagramm und die zugehörige Datentabelle anzeigen. Doppelklicken Sie auf das Diagramm, um sie auf der Registerkarte **Analyse** zu öffnen.

Durch die Layoutsymbole auf der rechten Seite der Titelleiste Graph verwenden, Sie können auswählen, dass nur das Diagramm anzuzeigen und/oder nur die Datentabelle.

## <a name="step-3-selecting-a-time-interval"></a>Schritt 3: Ein Zeitintervall auswählen


Klicken Sie auf der Registerkarte **Analyse** können Sie ein Zeitintervall auswählen, den Zeiger über einem Abschnitt des Diagramms horizontal ziehen. Die Zeitachse am unteren Rand der Registerkarte gilt für alle Diagramme auf der Registerkarte.

## <a name="step-4-zooming-in-on-a-time-interval"></a>Schritt 4: Vergrößern ein Zeitintervall


Nachdem Sie ein Zeitintervall ausgewählt haben, können Sie vergrößern, um auf die volle Breite des der Registerkarte **Analyse** , Zeitintervall ausweiten. Zu diesem Zweck mit der rechten Maustaste in des Intervalls, und wählen Sie dann **auf ausgewählte Zeitbereich Zoomen**. Sie können diesen Schritt mehrmals wiederholen, um ein Zeitintervall für sehr kleine sehr Details finden Sie unter.

Verwenden Sie alle Diagramme auf der Registerkarte **Analyse** demselben Zeitplan. Aus diesem Grund wird durch diese Aktion das gleiche Zeitintervall für alle diese Diagramme erweitert.

## <a name="step-5-highlighting-a-selected-time-interval"></a>Schritt 5: Ein ausgewählten Zeitintervall Hervorhebung


Nachdem Sie ein Zeitintervall ausgewählt haben, können Sie auch diese Zeitintervall in alle Diagramme auf der Registerkarte **Analyse** und in das Diagramm Explorer-Fenster hervorheben. Zu diesem Zweck Maustaste auf das Intervall und wählen Sie dann die **Auswahl hervorzuheben**. Diese Aktion Einfrieren die Auswahl unabhängig davon, wo Sie klicken. Zum Deaktivieren der Markierung rechten Maustaste auf das Intervall, und wählen Sie dann auf **Auswahl löschen**.

## <a name="step-6-customizing-a-data-table"></a>Schritt 6: Anpassen einer Datentabelle


Sie können Spalten in einer beliebigen Position in der Datentabelle ziehen. Sie können die Tabellenkopfzeile über eine beliebige Spalte sortiert nach dieser Spalte klicken. Klicken Sie auf die Tabellenkopfzeile erneut aus, um die Sortierung des Reverseproxys. Wenn Sie die Datentabelle ändern, werden die Änderungen auch im Steuerelement für die **Legende** im Diagramm angezeigt. Die Legende Tabellenspalte Daten ermittelt Steuerelement für die **Legende** im Diagramm.

Sie können Datentabellen anpassen, indem Sie die anzuzeigenden Spalten auswählen. Öffnen das **Spaltenauswahl** , mit der Maustaste Tabellenüberschrift. Sie können dann Spalten einzeln auswählen oder erstellen oder vordefinierten Tastenkombinationen der anzuzeigenden Spalten.

Datentabellen werden Pivottabellen. Die Spalten der gold vertikale Leiste links sind Schlüssel. Zwischen den vertikalen gold Balken und die blaue vertikale Leiste der Datenspalten sind. Wenn Sie nicht die gold vertikale Leiste angezeigt wird, führen Sie einen Bildlauf nach rechts.

Sie können eine beliebige Spalte links neben den vertikalen gold Balken zu vereinfachen ein Schlüssels ziehen. Sie können auch einige Spalten rechts neben der vertikalen blauen Leiste Sie Diagrammerstellungsfunktion Elemente ziehen.

Sie können eine kleine Auswahl von Spalten mit der rechten Maustaste, um vertikale grau Einfrieren Balken anzeigen fixieren. Klicken Sie dann, führt einen Bildlauf die Bildlaufleiste nur zwischen den Spalten zwischen den Balken fixieren. Sie können die Einfrieren-Balken, um eine beliebige Anzahl von Spalten enthalten ziehen.

## <a name="step-7-opening-a-new-analysis-tab"></a>Schritt 7: Öffnen einer neuen Registerkarte Analyse


Alle Diagramme und Tabellen auf einer Registerkarte **Analyse** demselben Zeitplan freigeben und an-und Abmelden zusammen Zoomen festgelegt werden. Wenn Sie einige Diagramme in einem anderen Zeitplan anzeigen möchten, können Sie eine zusätzliche **Analyse** Registerkarte öffnen. Zu diesem Zweck klicken Sie im Menü **Fenster** auf **Neue Analysis-Ansicht** , und ziehen Sie dann die gewünschte Diagramme in der neuen Registerkarte.

## <a name="step-8-opening-or-closing-windows"></a>Schritt 8: Öffnen oder Schließen von Fenstern


Wählen Sie im **Fenster** auf die Windows, die Sie zum Öffnen oder schließen möchten.

## <a name="step-9-creating-and-applying-a-view-profile"></a>Schritt 9: Erstellen und Anwenden von einem Profil anzeigen


Nachdem Sie dem Layout wie festgelegt haben, dass Sie möchten, können ein Profil anzeigen, die das aktuelle Layout entweder jedes Mal reproduziert, WPA zu öffnen oder nur für bestimmte Arten von Aufzeichnungen. Klicken Sie auf **Exportieren** , um ein Profil anzeigen erstellen, klicken Sie auf **Übernehmen** , um ein Profil Ansicht anwenden, die Sie zuvor erstellt haben, oder klicken Sie auf **Start-Profil zu speichern** , um die aktuelle Ansicht jedes Mal finden Sie unter, WPA zu öffnen, klicken Sie im Menü **Profile** .

## <a name="step-10-searching-and-filtering"></a>Schritt 10: Suchen und Filtern


Sie können die Daten in einem Diagramm und die zugehörige Datentabelle durch das Diagramm **Legend** -Steuerelement mit der rechten Maustaste, und aktivieren oder deaktivieren die gewünschten Elemente filtern. Nur die ausgewählte Zeile oder Zeilen anzuzeigen, mit der rechten Maustaste der Datentabelle, und klicken Sie dann auf **Filter zur Auswahl**.

Um Spalten in der Datentabelle anzeigen auszuwählen, mit der rechten Maustaste in der Tabellenkopfzeile, und aktivieren oder Deaktivieren der Spalten im Feld **Spaltenauswahl** .

Um den Text in der Datentabelle zu suchen, mit der rechten Maustaste in der Tabelle, und wählen Sie dann auf **Suchen**, **Weitersuchen**oder **Vorheriges suchen**.

## <a name="step-11-setting-user-preferences"></a>Schritt 11: Festlegen von Benutzereinstellungen


Derzeit können Sie WPA Symbole laden festlegen, und Sie können Symbolpfade festlegen. Diese Optionen sind im Menü **Trace** verfügbar.

## <a name="step-12-using-the-diagnostic-console"></a>Schritt 12: Verwenden der Diagnose-Konsole


In diesem Fenster aufgelistet Ausnahmen, die im Workflow Analyse aufgetreten sind. Sie können Probleme aus diese Konsole Decodierung Symbol diagnostizieren.

## <a name="step-13-viewing-assessment-analysis-and-issue-details"></a>Schritt 13: Anzeigen der Assessment Analyse und Problemdetails


Beim Öffnen von WPA einer Bewertung, die in der Konsole Assessment ausgeführt wurde, und bietet zusätzliche Analyse, werden die Probleme, die die Bewertung identifiziert im **Problemfenster** angezeigt. Wenn Sie eines dieser Probleme klicken Sie auf, werden Details und empfohlene Lösung in der Registerkarte **Analyse** unter **Problemdetails**angezeigt.

Sie können auch die Liste der Probleme mithilfe der Optionen zur Suche im oberen Bereich des Fensters Probleme suchen. Weitere Informationen zu dieser Funktionalität steht im [Fenster Probleme](issues-window.md).

## <a name="related-topics"></a>Verwandte Themen


[WPA Quick Start-Handbuch](wpa-quick-start-guide.md)

 

 







