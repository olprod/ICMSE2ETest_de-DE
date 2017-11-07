---
title: "Übung 3: Nachverfolgen Treiber Speicherbedarf und dynamische Zuweisungen während des Startvorgangs"
description: "Pool ist die Ressource Arbeitsspeicher für Kernel-Modus-Komponenten, die der OS und Gerätetreiber verwenden, um ihre Datenstrukturen zu speichern."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C77947E1-D20A-4728-878C-3748B1068DEC
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0b35c618fb9637ab786a611e642c62d2664fd172
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-3---track-driver-footprint-and-dynamic-allocations-during-boot"></a>Übung 3: Nachverfolgen Treiber Speicherbedarf und dynamische Zuweisungen während des Startvorgangs


**Pool** ist die Ressource Arbeitsspeicher für Kernel-Modus-Komponenten, die der OS und Gerätetreiber verwenden, um ihre Datenstrukturen zu speichern. Pool besteht aus vier grundlegenden Zuweisung Bereiche:

1.  **Nicht ausgelagerter Pool:** Zuweisungen garantiert im physikalischen Speicher befinden.

2.  **Ausgelagerter Pool:** Zuordnung, die nicht genügend Arbeitsspeicher in die Auslagerungsdatei ausgelagert werden können.

3.  **n x nicht navigierbaren Pool:** Nicht ausgelagerter Zuweisungen, die nicht ausgeführt werden.

4.  **Sitzungspool:** Zuweisungen pro Sitzung vorgenommen. Dies sind navigierbaren.

Pool wie folgt eine erhebliche Mitwirkender für die allgemeine Verwendung von Arbeitsspeicher auf einem Computer – es ist der größte Verbraucher Arbeitsspeicher unmittelbar nach dem starten. Verringerung der Auslastung reduziert die Gesamtverwendung der Speicher des Systems über das Betriebssystem-navigierbaren Speicher wird die höchste Prioritätskategorie auf Laufwerk gesenkt werden können (für).

In dieser Übung prüfen Sie während des Startvorgangs Posteingang Microsoft Treiber Zuweisungen und ihre Bilanz (zur Initialisierungszeit).

## <a name="step-1-gather-a-pool-memory-trace-across-a-boot-transition"></a>Schritt 1: Erfassen Sie Ablaufverfolgungsdaten Arbeitsspeicher Pools über einen Boot Übergang


In diesem Schritt erfassen Sie Boot Trace mithilfe von **Windows Performance Aufzeichnung (WPR)** , die Pools und der Wohnsitz Set-Daten enthält.

1.  Öffnen Sie im Menü **Start** **WPR**

2.  Wählen Sie die richtigen Ereignisablaufverfolgungsanbieter:

    1.  **Pool-Verwendung**

    2.  **Wohnen Set**

    3.  **Erste Ebene Ursachenanalyse**

3.  Wählen Sie **Boot** **Leistung Szenario**wie.

4.  Wählen Sie die **Datei** als die **Protokollierung Modus**.

5.  Legen Sie als die **Anzahl von Iterationen**1 fest.

6.  Klicken Sie auf **Start** , und wählen Sie einen Speicherort zum Speichern der ETL-Datei.

Das System automatisch neu gestartet wird, sammelt Trace und hält nach der Desktop angezeigt wird.

![Screenshot WPR Einstellungen im Dialogfeld.](images/memoryfootprintlab25.png)

## <a name="step-2-review-pool-data-using-wpa"></a>Schritt 2: Überprüfen der Pool-Daten mithilfe von WPA


Die Daten **Pool** werden über den **Pool Diagramm** Übersicht über die in **WPA**verfügbar gemacht. Die Schlüsselspalten von Interesse sind in der folgenden Tabelle.

Sie können Spalten hinzufügen oder entfernen Sie mit der rechten Maustaste auf die Spaltenüberschriften.

| Terminologie     | Beschreibung                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------|
| Pool-Tag        | Das Tag eine Zuordnung Pool zugeordnet ist.                                                             |
| Pool-Tag-Modul | Das Modul (Treiber) einen Pool-Tag zugeordnet.                                                        |
| Stapel           | Zeigt den Codepfad in einem Thread, was zu einer Zuweisung von virtuellem Speicher.                                        |
| Paged           | Gibt an, ob die Zuweisungen in einem Pool ausgelagert oder Non-Paged Pool abgelegt wurden.              |
| Störenden Typ  | Zeigt, ob eine Zuweisung wirkt sich auf die Speicherverwendung stabilen Zustand oder eine vorübergehende Verteilung ist. |

 

1.  Öffnen Sie die erfassten Trace in Schritt 1 mit **WPA**.

2.  Öffnen Sie das Menü **Trace** , und wählen Sie **Konfigurieren Symbole Pfad**.

    -   Geben Sie den Pfad des Caches Symbol. Weitere Informationen zu Symbolen finden Sie unter auf der [Supportseite Symbol](https://go.microsoft.com/fwlink/?linkid=623019) auf MSDN.

3.  Öffnen Sie das Menü **Trace** , und wählen Sie **Symbole laden**.

4.  Hier finden Sie im Diagramm **Pool** in der Kategorie **Speicher** des **Diagramm-Explorer**

5.  Drag & drop im **Pool** Diagramm auf der Registerkarte **Analyse** .

6.  Organisieren der Tabelle, um diese Spalten werden angezeigt:

    1.  **Pool-Tag-Modul**

    2.  **Mehrere Seiten vorhanden sind**

    3.  **Störenden Typ**

    4.  **Stack**

    5.  **Pool-tag**

    6.  **Count**

    7.  **Beeinträchtigung der Größe** und **Größe**

    **Hinweis auf Pooltags:**

    Wenn Sie ein Entwickler sind, stellen Sie sicher, dass der vom Treiber verwendeten Pooltags klare und leicht verständliche, um zu analysieren sind. Beispielsweise ist der Firmenname Fabrikam, Sie konnte hinzufügen ein Präfix "Fbk" für alle Pools Tags: FbkPool1, FbkPool2, FbkBuffer, usw..

    ![Screenshot, der zeigt, wie die neu organisierte WPA Tabelle aussehen sollte.](images/memoryfootprintlab26.png)

7.  Deaktivieren Sie alle Datenreihen im Diagramm (Rechtsklick -&gt; **Deaktivieren**  - &gt; **Gesamtes Diagramm**  - &gt; **Alle Datenreihen**)

    ![Screenshot der Menüoption in WPA deaktivieren.](images/memoryfootprintlab27.png)

8.  Sortierung nach Größe durch Klicken auf die Spaltenüberschrift **Beeinträchtigung der Größe** beeinträchtigen.

    Treiber, die die höchste Speicherverwendung stabilen Zustand angezeigt, die im oberen Bereich.

## <a name="step-3-intercept-pool-allocation-data"></a>Schritt 3: Intercept Pool Zuordnungsdaten


1.  Vergrößern Sie den ersten 30 Sekunden des Zeitplans.

2.  Wählen Sie eine Treiber (beispielsweise ACPI.sys, aber alle geschieht).

    1.  Überprüfen Sie den Speicher **nicht ausgelagert** , und erweitern Sie die Zeile.

        **Nicht ausgelagert** Arbeitsspeicher sollte den Fokus von Ihrer Untersuchungen sein, wie es in die Auslagerungsdatei verschoben werden kann, wenn ausreichender Arbeitsspeicher auf dem System vorhanden ist.

    2.  Aktivieren Sie die **Legende** für die Kategorien **Impacting** und **vorübergehende** an.

        ![Screenshot der Beispieldaten, die Speicherverwendung angezeigt.](images/memoryfootprintlab28.png)

3.  Sortieren nach **Größe Paketverlust beeinflusst** , indem Sie auf die Spaltenüberschrift.

4.  **Impacting** Speicher trägt direkt auf die allgemeine Speicherbedarf des Treibers jederzeit. Im obigen Beispiel können Sie mitteilen, dass ACPI.sys Speicherplatz nicht ausgelagerten jederzeit verwendet und, dass dies Verwendung, Stabilität zweimal erhöht (zuerst, wenn der Treiber, klicken Sie dann ein zweites Mal bei rund 3 Sekunden geladen wird).

    1.  Erweitern Sie den Stapel und zum Navigieren durch. Klicken Sie oben sollten Funktionsaufrufe angezeigt werden, die zu den größten stabilen Zustand Pool Zuweisungen führen.

    2.  Im folgenden Beispiel sehen Sie sich, dass ACPI.sys maximal 255 Pool-Zuweisungen macht insgesamt 1,2 MB unter der **ACPIInitStartACPI** -Funktion. Dies ist, wobei der vom Entwickler konzentrieren sollten, um die Speicherverwendung Treiber stabilen Zustand als diese Funktion Konten für den Großteil der Treiber Zuweisungen zu verbessern.

        ![Screenshot der Beispieldaten, die Speicherverwendung durch ACPI.sys angezeigt.](images/memoryfootprintlab29.png)

5.  Sortieren nach **Größe** , indem Sie auf die Spaltenüberschrift.

6.  Führen Sie dieselben Schritte für die **vorübergehende** Kategorie. Erweitern Sie den Stapel und zum Navigieren durch. Funktionsaufrufe zu den größten vorübergehende Pool Zuweisungen sollten Sie am Anfang angezeigt werden.

    -   Im folgenden Beispiel sehen Sie, dass die anfängliche Sammlung der vorübergehende Speicherverwendung hauptsächlich von ACPI verursacht wird ausführen DPCs von Geräten (**ACPI.sys! ACPIBuildDeviceDpc**). Die Auflistung angehängt wird, die den Code unter diesen Funktionsaufruf eingeführt summiert 455 KB.

        ![Screenshot der Beispieldaten, die Speicherverwendung durch ACPI.sys angezeigt.](images/memoryfootprintlab30.png)

## <a name="step-4-measure-the-driver-code-footprint"></a>Schritt 4: Messen der Treiber Code Speicherbedarf


1.  Hier finden Sie im Diagramm **Wohnsitz festlegen** in der Kategorie **Speicher** des **Diagramms Explorer**ein.

2.  Drag & drop im Diagramm **Wohnsitz festlegen** auf der Registerkarte Analyse.

3.  Stellen Sie sicher, dass Sie das Diagramm verkleinern (STRG + UMSCHALT + "-").

4.  Wählen Sie die **Datei gesichert Seite** Diagramm Voreinstellung.

    ![Screenshot der Datei gesichert Option Seite.](images/memoryfootprintlab31.png)

5.  Navigieren Sie über der Spalte **Pfad Struktur** zu der in Schritt 3 (beispielsweise ACPI.sys unter C:/Windows/Treiber) gewählte Treiber.

6.  Erweitern Sie die Kategorie **Treiber** und konzentrieren Sie sich auf den Seiten des **aktiven** .

    Der Wert in der Spalte **Größe** stellt die Auswirkung von der Treibercode auf höherer Speicherbedarf. Im folgenden Beispiel ist es 0,48 MB. ![Screenshot des aktiven Seiten mit Beispieldaten.](images/memoryfootprintlab32.png)

 

 






