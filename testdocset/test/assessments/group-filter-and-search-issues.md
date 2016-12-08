---
title: Gruppieren, Filtern und Suchproblemen
description: Gruppe, Filter und Suchproblemen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dfc198ee-d037-4a34-b309-ee8786026716
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: b694d9165dbfabcec6b6a19a306376041c3e1806
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="group-filter-and-search-issues"></a>Gruppe, Filter und Suchproblemen


Dieses Thema bietet eine Übersicht über die Bewertung von Suchergebnissen. Es wird auch beschrieben, wie mehrere Ergebnisse öffnen und dann gruppieren, Filtern und sortieren die Probleme, um die Informationen zu suchen, die Sie benötigen.

Ergebnisse anzeigen von Informationen über welche die Bewertung ermittelt werden, wenn es ausgeführt haben. Die Ergebnisse enthalten die Metriken, die beschreiben, was die Bewertung gemessen, Probleme, die die Bewertung gefunden auf Messungen und Empfehlungen, um mögliche Probleme zu beheben basiert. Einige Recommendations enthalten Links zu weiteren Informationen oder Links zu Windows Performance Analyzer (WPA). Diese Links können Sie die verfolgen Sie der Ursache eines Problems zurück an die Datenquelle.

Sie können einzelne Ergebnisse oder mehrere Ergebnisse aus einer Liste aller Ergebnisse öffnen. Eine Zusammenfassungsansicht steht für mehrere Ergebnisse verglichen. Aber standardmäßig beim Öffnen von Ergebnissen in der Windows-Konsole Assessment Benutzervorgänge in der Detailansicht an. Ergebnisse die Detailansicht umfasst:

-   **Führen Sie Informationen.** Die erste Tabelle in der Detailansicht enthält Informationen, ausführen. Die Laufzeit Informationen enthält Daten über den Computer, auf dem der Auftrag auf, darüber hinaus ausgeführt wurde um die Probleme insgesamt, Fehlern und Warnungen, die der Auftrag auf diesem Computer erstellt. Klicken Sie auf **Zeilen auszuwählen** , zum Hinzufügen oder Entfernen von Informationen aus der Tabelle.

-   **Assessment-Ergebnisse.** Assessment-Ergebnisse für jede Analysen, die der Auftrag ausgeführt werden nach der Tabelle mit den ausführen angezeigt. Die Bewertungsergebnisse 5 Kategorien von Informationen enthalten: Fehler, Warnungen, Probleme, Metriken und Bewertung Einstellungen. Zum Erweitern oder Reduzieren einer Zeile, klicken Sie auf den Doppelpfeil am Anfang jeder Zeile.

-   **Ein Detailbereich.** Wenn Sie eine einzelne Zelle in den Tabellen klicken, können Sie weitere Informationen im Detailbereich auf der rechten Seite angezeigt. Detailbereich standardmäßig sichtbar ist, aber Sie können reduzieren, um weitere Bildschirmbereich auf Ergebnisse zu ermöglichen.

-   **Ein Diagramm Metrik.** Jedes Assessment verfügt über ein Diagramm Symbol namentlich Bewertung. Sie können das Diagramm-Symbol, um alle Metriken Diagramm klicken. Die obersten Ebene Metriken sind auch Balkendiagrammen zugeordnet. Zum Vereinfachen oder Erweitern im Diagramm, klicken Sie auf das farbige Leiste neben das Ergebnis, das Sie zum Diagramm hinzufügen oder aus dem Diagramm entfernen möchten. Um zum ursprünglichen Diagramms zurückzukehren, klicken Sie auf der farbigen Balken neben dem Namen der Bewertung.

Probleme sind ein wichtiger Teil der Ergebnisse. Identifizieren potenzieller Probleme mit einem Computerkonfiguration oder Leistung basieren auf Messungen, Datensätze Bewertung. Der Auftrag meldet die Gesamtzahl der Probleme, die es gefunden und die Anzahl der Probleme, die sie für jede Bewertung gefunden. Wenn mehr als ein Problem auftritt, können Sie das Problem, um weitere Informationen finden Sie unter erweitern. Klicken Sie auf ein einzelnes Problem um empfohlene Remediation und weitere Analyseinformationen im Detailbereich finden Sie unter.

**So öffnen Sie Ergebnisse**

1.  In der Windows-Assessment-Konsole auf **Optionen**und klicken Sie dann auf **Open Results**. Es wird eine Liste aller Ergebnisse aus der Bibliothek Ergebnisse angezeigt.

2.  Wählen Sie einen oder mehrere Ergebnisse aus, und klicken Sie dann auf **Öffnen**.

    -   Um ein Einzelergebnis, das ausgewählt haben, wählen Sie das Kontrollkästchen in der linken Spalte aus.

    -   Um mehrere Ergebnisse auswählen, klicken Sie auf die Daten und ziehen Sie die Maus oder klicken Sie auf die Daten, und verwenden Sie die UMSCHALTTASTE oder die STRG-Taste, die Ergebnisse aus, denen Sie möchten.

**Um Probleme bei der Gruppe in der Ergebnistabelle Bewertung**

1.  Klicken Sie auf der Seite **Ergebnisse anzeigen** in der Ergebnistabelle zur Bewertung auf den Doppelpfeil neben **Probleme** , die Probleme zu erweitern.

2.  Mit der rechten Maustaste **Probleme**, und wählen Sie dann auf das Menü **Gruppieren nach** einer Kategorie nach dem gruppiert werden.

    Jedes Assessment kann unterschiedliche Gruppierung Kategorien aufweisen. Beispielsweise könnte angezeigt:

    -   **(Kein Rahmen)**. Gruppieren Sie keine Probleme.

    -   **Kategorie**. Gruppe Probleme nach Kategorie. Jede Probleme wird von der Art der Auswirkungen auf die Leistung, die die Bewertung erkannt hat kategorisiert.

    -   **Typ-ID**. Gruppe Probleme basierend auf einer-ID. Jedes Problem ist Typ-ID, die definiert eine Gruppe von ähnlichen Problemen über mehrere Kategorien zugeordnet.

    -   **Testfall**. Gruppieren Sie basierend auf welche Testfall oder Arbeitslast ausgeführt wird, wurde bei die Bewertung der Problems Probleme.

    -   **Hersteller**. Gruppe Probleme basierend auf den Hersteller, wenn in der Ausgabe des Herstellers identifiziert wird.

    -   **Prozess**. Gruppe Probleme basierend auf Prozesse, wenn sie in der Ausgabe gekennzeichnet sind.

    **Hinweis**  
    Sie können außerdem **Probleme insgesamt** in der Tabelle ausführen Gruppe Probleme in einer Tabelle mit der Maustaste.

     

**Zum Sortieren von Problemen über mehrere Aufträge**

1.  Klicken Sie auf der Seite **Ergebnisse anzeigen** in der Ergebnistabelle zur Bewertung auf den Doppelpfeil neben **Probleme** , die Probleme zu erweitern.

2.  Mit der rechten Maustaste **Probleme**, und klicken Sie dann auf **Aufsteigend sortieren** oder **Absteigend sortieren** , um die Spalten für die verschiedenen Auftragsergebnisse zu sortieren.

    **Hinweis**  
    Sie können auch **Probleme insgesamt** in der Informationstabelle ausführen zum Sortieren der Spalten für verschiedene Auftragsergebnisse basierend auf der Anzahl der insgesamt Probleme in jeder Auftrag mit der rechten Maustaste.

     

**Zur Suche nach Problemen im Detailbereich**

1.  Klicken Sie auf der Seite **Ergebnisse anzeigen** in der Ergebnistabelle Bewertung auf **Probleme**.

    Details für jedes Problem im Detailbereich auf der rechten Seite angezeigt werden.

2.  Geben Sie im Detailbereich ein beliebiges Wort in das Feld **Filtern Probleme** .

**Filtern von Problemen im Detailbereich**

1.  Klicken Sie auf der Seite **Ergebnisse anzeigen** in der Ergebnistabelle Bewertung auf **Probleme**.

    Details für jedes Problem im Detailbereich auf der rechten Seite angezeigt werden.

2.  Klicken Sie im Detailbereich auf das grünes Pluszeichen (**+**) neben dem Feld **Filter Probleme** , und wählen Sie Filterkriterien. Andere Bewertung haben verschiedene Filterkriterien.

    Neben den Filterkriterien, die Sie ausgewählt wird der standardmäßige relationale Ausdruck angezeigt.

3.  Klicken Sie auf der relationale Ausdruck aus, und wählen Sie eine, die Sie verwenden möchten.

    Je nach den Metadaten-filtern, die Sie verwenden, sind diese relationale Ausdrücke verfügbar:

    -   ist gleich

    -   ungleich

    -   kleiner als

    -   größer als

    -   kleiner oder gleich

    -   größer als oder gleich

    -   beginnt mit

    -   endet mit

    -   contains

    -   enthält nicht

    -   zwischen

    -   Regex

        **Hinweis**  
        Der Begriff *Regex* bezieht sich auf reguläre Ausdrücke. Weitere Informationen finden Sie unter [Sprachelemente für reguläre Ausdrücke](http://go.microsoft.com/fwlink/?LinkId=235292).

         

4.  Geben Sie im Feld den Metadatenwert, dem Sie filtern möchten.

    -   Wiederholen Sie diese Schritte, um die Filterkriterien hinzuzufügen.

    -   Um Filterkriterien zu entfernen, klicken Sie auf das **X** neben diese.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Konsole](windows-assessment-console.md)

[Häufige Szenarien Windows Assessment-Konsole](windows-assessment-console-common-scenarios.md)

[Vergleich der Ergebnisse](compare-results.md)

[Importergebnisse](import-results.md)

[Filtern der Ergebnisse](filter-results.md)

 

 







