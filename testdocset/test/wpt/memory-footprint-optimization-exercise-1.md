---
title: "Übung 1: Identifizieren von Geschäftsprozessen mit großen Working Sets"
description: "Methodik zum Analysieren der Daten kann mehrere Ansätze und hängt davon ab, über die Umstände, unter denen die Untersuchung gestartet wurde."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F77AAF4D-2A0E-440B-8199-69FD1D5E65FE
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 832f530147d3fe02cc19ae13e1fa043d7122db9d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-1---identify-processes-with-large-working-sets"></a>Übung 1: Identifizieren von Geschäftsprozessen mit großen Working Sets


Methodik zum Analysieren der Daten kann mehrere Ansätze und unterscheidet sich abhängig von den Umständen, unter denen die Untersuchung gestartet wurde. In dieser Übung erläutert und präsentiert werden zusammen mit den verschiedenen Ansichten präsentiert von verschiedenen Spalte Modalitäten einige Beispiel-Methoden.

Die Daten als die Wohnsitz festgelegt ist die Menge von Seiten, die sich derzeit im physischen Arbeitsspeicher (RAM) befinden. Legen Sie die Berater ist eine Momentaufnahme des aktuellen Speicherzustands am Ende einer Aufzeichnung Trace mit **Windows Performance Aufzeichnung (WPR)** oder die Bewertung Assessment Toolkit Arbeitsspeicher. Es ist nicht möglich, mehrere Momentaufnahmen in einer einzigen Ablaufverfolgung zu erfassen.

Wohnsitz legt bieten eine ganzheitliche und unmittelbare Momentaufnahme der Zusammensetzung Arbeitsspeicher auf dem System. Untersuchungen in Analysis Wohnsitz festlegen erfolgt in der Regel aus den folgenden Gründen:

-   Nutzung des physischen Arbeitsspeichers, zu verstehen, insbesondere bei der Nutzung des physischen Arbeitsspeichers höher als erwartet ist.

-   Um zu verstehen, die Quellen der Prozess private Arbeitssatz, insbesondere wenn ist privaten Arbeitssatz Prozess größer als erwartet.

-   System Reaktionsfähigkeit Probleme aufgrund von Paging-Aktivität.

## <a name="step-1-collect-data-using-the-assessment-toolkit"></a>Schritt 1: Sammeln von Daten mit dem Assessment Toolkit


Das **Windows Assessment Toolkit** enthält einen Test, um nach dem Start der Arbeitsspeicherbedarf messen. Die Ergebnisse der **Speicherbedarf** Assessment können Sie um einen Basisplan der Teiler Bildsoftware zu erfassen. Viele Prozesse und Dienste sind immer verwendet und Arbeitsspeicher belegen. Diese Bewertung hilft Ihnen, finden Sie unter wie Treiber und Anwendungen (, die immer ausgeführt) des Startvorgangs beeinflussen.

1.  Öffnen Sie **Windows-Assessment-Konsole (WAC)** im Menü **Start** .

2.  Öffnen Sie das Menü **Optionen** und wählen Sie **Neuer Auftrag...**

    1.  Geben Sie **MemoryTest** als Name des Auftrags.

    2.  Wählen Sie **Erstellen eines benutzerdefiniertes Auftrags.**

3.  Klicken Sie auf **Hinzufügen Bewertung.**

    -   Fügen Sie die Bewertung **Speicherbedarf** , indem Sie auf das Symbol "+" hinzu

4.  Klicken Sie auf die neu hinzugefügte **Speicherbedarf** zur Bewertung die Testkonfiguration eingeben.

5.  **Empfohlene Verwendung** deaktivieren Sie und wählen Sie **Quick ausführen** , für die Konfiguration.

    -   **Schnelles ausführen** kann der Test in einem kürzeren Zeitraum auf Kosten der Genauigkeit der Daten abgeschlossen.

    ![Screenshot des Windows-Assessment-Konsole.](images/memoryfootprintlab1.png)

6.  Mit **Schnellen ausführen** ausgewählt haben Sie zwei Optionen:

    1.  Den Auftrag, um einen Ordner zu erstellen, der hat alle Testressourcen und kopieren Sie sie in einer anderen Testsystem **Paket** . (Klicken Sie auf das **Paket...** Schaltfläche in der unteren rechten Ecke auf diese Option auswählen.)

    2.  **Ausführen** des Auftrags direkt auf dem System an. (Klicken Sie auf die Schaltfläche **Ausführen** , in der unteren rechten Ecke auf diese Option auswählen.)

        -   Dies startet das System, um eine Ablaufverfolgung zu erfassen.

        -   Bei diesem Test kann einige 15 bis 20 Minuten dauern.

    Die Option **Ausführen** soll.

## <a name="step-2-visualize-the-memory-footprint-assessment-results-using-wac"></a>Schritt 2: Visualisieren der Speicherbedarf-Assessment-Ergebnisse mit WAC


Nach Abschluss die Bewertung können Sie die XML-Datei mit den Suchergebnissen öffnen, die enthält eine Übersicht über die Speicherverwendung auf dem System.

### <a name="step-21-open-the-memory-report"></a>Schritt 2.1: Öffnen Sie den Bericht Arbeitsspeicher

1.  Klicken Sie in **WAC**öffnen Sie das Menü **Optionen** , und wählen Sie **Ergebnisse öffnen**

    -   Sie können auch auf der Tastatur **STRG + R** drücken.

2.  Klicken Sie auf **Durchsuchen...** Schaltfläche.

3.  Navigieren Sie zu dem Ordner, in dem Sie gespeichert haben, die Bewertung, Sie in Schritt 1 erstellt haben.

4.  Öffnen Sie die Bewertung, den, die Sie in Schritt 1 erstellt haben.

    Der Bericht enthält, um die Treiber und Prozess Beiträge zu den allgemeinen Speicherbedarf Verständnis der verschiedene Kategorien.

    Der Bericht sollte etwa folgendermaßen aussehen.

    ![Beispielbericht Windows Assessment Verwaltungskonsole Speicherverwendung angezeigt.](images/memoryfootprintlab2.png)

5.  Übernehmen Sie die Zeit, sich mit den Bericht anhand der Kategorien **Treiber** und **Prozess Private Seiten** vertraut machen.

Im vorstehenden Beispiel wird die 1487 MB Speicher nicht genügend 4 GB des physikalischen RAMS verwendet.

-   Arbeitsspeicher In Gebrauch Prozess Arbeitsseiten + nicht ausgelagerte Arbeitsspeicher = + geänderte Seiten

-   Verfügbarer Arbeitsspeicher = Standby-Speicher + freien Speicher

Im vorherigen Beispiel sind die größte Consumer der Speicherverwendung Treiber Zuweisungen mit 267 MB für nicht ausgelagerten und 613 MB für Prozess\Private (private Arbeitsseiten) Seiten.

Weitere Informationen zu den Metriken finden Sie die [Ergebnisse für die Bewertung der Speicher Bilanz](https://go.microsoft.com/fwlink/?linkid=619204) auf MSDN.

### <a name="step-22-review-driver-non-paged-allocations"></a>Schritt 2.2: Überprüfen der Treiber nicht ausgelagerten Zuweisungen

Diese Metrik ist die ausgelagerten Zuweisungen ähnlich, außer dass diese Zuweisungen physischen Speicher verwenden, der nicht ausgelagert werden können. Dies gilt für physischen Speicher, der durch andere Prozesse und Dienste angeheftete und daher für ausgelagerten Arbeitsspeicher oder die Verwendung nicht verfügbar ist. Erwerb zu viel Speicher nicht ausgelagerten reduziert die Größe des Arbeitsspeichers, die gesichert kann Arbeitsspeicher zu verwenden.

1.  Erweitern Sie die Kategorie **Driver Non-Paged Zuweisungen** , indem Sie auf den Pfeil auf der linken Seite.

2.  Erweitern Sie die **DriverLockedSystemPages** Kategorie.

    -   Hierbei handelt es sich um Arbeitsspeicher aus ausgelagerten Arbeitsspeicher geladen, und klicken Sie dann vom Treiber gesperrt, bis es nicht mehr benötigt werden.

3.  Identifizieren Sie, indem Sie die größte Speicherverwendung des Treibers.

    ![Beispielbericht Windows Assessment Verwaltungskonsole Treiber nicht ausgelagerten Zuweisung Verwendung anzeigen.](images/memoryfootprintlab3.png)

Sie können diese Metrik durch Auslagerung Hardware- oder Treiber, niedrigere Arbeitsspeicherbedarf beeinflussen.

Hersteller des Treibers hat die meisten Einfluss auf diese Metrik die Art und Weise wie den der Treiber vorgesehen ist. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in **WAC**dargestellt. Darüber hinaus können die Treiber Herstellern Leistung Spuren (im gleichen Verzeichnis befindet wie die Bewertungsergebnisse gespeichert und können mit **WPA**analysiert werden) zugewiesen werden dieser Beurteilung Bereiche der Zuweisung von virtuellem Speicher extra fette suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind.

### <a name="step-23-review-process-private-working-sets"></a>Schritt 2.3: Überprüfung Prozess private Arbeitsseiten

Apps, die möglicherweise im Hintergrund ohne das Wissen des Benutzers immer ausgeführt werden, sind die größten Benutzer von der allgemeinen Arbeitsspeicherbedarf. Um die Menge des Arbeitsspeichers anzuzeigen, die verarbeitet verwenden, können Sie die Kategorie **Prozess Private Seiten** im Bericht.

1.  Erweitern Sie die Kategorie **Prozess Private Seiten** , indem Sie auf den Pfeil auf der linken Seite.

2.  Erweitern Sie die **aktiven** Kategorie. Die Liste zeigt die Binärdateien und ihre Verwendung von aktiven Speicher.

    Ihre Ansicht sollte etwa folgendermaßen aussehen:

    ![Beispielbericht aus Windows Assessment-Konsole zeigt von speicherauslastung durch den Prozess.](images/memoryfootprintlab4.png)

3.  Identifizieren Sie den Prozess, der die die meisten Speicher verwendet.

Sie können diese Metrik durch Verringern der Anzahl der "immer ausführen" Applications, in den Registrierungsschlüssel **Ausführen** oder Ordner **Autostart sind** beeinflussen. Analysieren der Auswirkungen der apps hinzugefügt.

Treiber und Softwarehersteller haben die meisten Einfluss auf diese Metrik durch die Möglichkeit, den, die entsprechenden Code entwickelt wurde. Suchen Sie nach großer Arbeitsspeicher Zuweisungen in den Ergebnissen in den **WAC**dargestellt. Darüber hinaus können Softwarehersteller erhalten Leistung Spuren (gespeichert im gleichen Verzeichnis befindet wie die Ergebnisse Assessment) dieser Beurteilung Bereiche der extra fette Arbeitsspeicher Zuweisungen suchen, die für die Untersuchungen in Reduzieren der Speicherverwendung geeignet sind. Sorgfältige Analysen der Zuweisungen, selbst bei kleinen Datenbanken, unterstützt Sie dabei den Entwickler, Zuweisungen suchen, die Sie hinzufügen.

## <a name="a-href-idstep-3--collect-resident-set-data-using-wpr-astep-3-collect-resident-set-data-using-wpr"></a><a href="" id="step-3--collect-resident-set-data-using-wpr-"></a>Schritt 3: Datenerfassung Wohnsitz Festlegen von WPR


In den Schritten 1 und 2 haben Sie wie Arbeitsspeicher Spuren mithilfe der **Assessment Toolkit Speicherbedarf** Bewertung zu erfassen. Diese Bewertung kann ausschließlich eine Verfolgung für das Szenario Boot erfassen. Sie können ablaufverfolgungen für jedes Szenario (app-Start, Web browsing, usw.) erfassen mithilfe der **Windows-Leistung-Aufzeichnung (WPR)**

Führen Sie diese Schritte zum Sammeln von einer Ablaufverfolgungs für mit Daten Wohnsitz festgelegt.

1.  Öffnen Sie **Windows Performance Aufzeichnung** im Menü **Start** .

2.  Wählen Sie die **"erste Ebene Ursachenanalyse"** und **"Wohnen Set-Analyse"** Aufzeichnung Profile, doch lassen Sie die Standardwerte für die anderen Optionen.

3.  Klicken Sie auf **Start** , und warten Sie einige Sekunden.

    ![Screenshot des Windows-Assessment-Konsole.](images/memoryfootprintlab5.png)

4.  Klicken Sie auf **Speichern** , und speichern Sie die **ETL** -Ablaufverfolgung auf dem Datenträger.

Sie haben nun eine Momentaufnahme der Zusammensetzung der System-Speicher.

## <a name="step-4-interpret-resident-set-data-using-wpa"></a>Schritt 4: Interpretieren Sie Wohnsitz festlegen Daten mit WPA


Gehen Sie folgendermaßen vor:

1.  Starten Sie **Windows Performance Analyzer** im Menü **Start** .

2.  Öffnen Sie den **ETL** -Trace Sie gerade (Menü**Datei** , **Open...**) gesammelt.

3.  Erweitern Sie den **Speicher** im **Diagramm Explorer**festgelegt.

    ![Screenshot der WPA Diagramm Explorer-Ansicht.](images/memoryfootprintlab7.png)

4.  Drag & drop im Diagramm **Wohnsitz festlegen** in der Registerkarte Analyse.

Ihre Ansicht sollte etwa folgendermaßen aussehen:

![Screenshot der WPA Analysis Registerkartenansicht angezeigt.](images/memoryfootprintlab8.png)

Überprüfen Sie, wie die Daten präsentiert werden. Es folgen einige Definitionen der Spalten für die oberste Ebene Analyse besonders nützlichen:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Spalte</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>MMList</strong></td>
<td><p>Die Liste der Speicher-Management, die die Seiten enthält.</p>
<p></p>
<ul>
<li><p><strong>Aktive</strong> – derzeit innerhalb eines privaten Arbeitssatz Prozesses oder Kernel Arbeitssatzes Seiten.</p></li>
<li><p><strong>Standby</strong> – Seiten auf der standby-Liste nicht geändert. Sie sind Teil der verfügbare Arbeitsspeicher.</p></li>
<li><p><strong>Geänderte</strong> – private verarbeiten oder gesicherte Seiten, die seit der letzten Änderung der Datei dauerhaft beibehalten wird.</p></li>
<li><p><strong>ModifiedNoWrite</strong> – Seiten, die geändert wurden, jedoch nicht dauerhaft beibehalten werden.</p></li>
<li><p><strong>Übergang</strong> – Seiten in den Übergang zwischen Listen.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Prozessfarben</strong></td>
<td><p>Der Name des Prozesses, der Besitzer der Seiten ist. Diese Informationen sind nur für Prozess private Seiten verfügbar. Auch wenn nicht gemeinsam verwendet werden, sind alle freigebbare Seiten des Prozesses "Unknown" (-1) zugeordnet.</p></td>
</tr>
<tr class="odd">
<td><strong>Beschreibung</strong></td>
<td><p>Der Wert dargestellt variiert je nach der Seitenkategorie. Beispiel:</p>
<p></p>
<ul>
<li><p>Für Bilder, Treibern, Dateien usw. den vollständigen Pfad und den Namen angezeigt.</p></li>
<li><p>Für den <strong>Pool</strong> zeigt es den Poolnamen Tag Treiber.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Seite Kategorie</strong></td>
<td><p>Der Typ der Daten in der Seite wie nachstehend definiert. Einige der möglichen Kategorien sind:</p>
<p></p>
<ul>
<li><p><strong>CopyOnWriteImage</strong> – Prozess private Seiten von der Patchen einer ausführbaren Abbildern Import Adresse Tabelle erstellt oder Neuzuordnen von einer ausführbaren Datei.</p></li>
<li><p><strong>Treiber</strong> – Codepages für einen Treiber.</p></li>
<li><p><strong>DriverFile</strong> – Codepages an, die aus der Treiber ausführbaren Datei gelesen und als Daten zugeordnet wurden.</p></li>
<li><p><strong>DriverLockedSystemPage</strong> – Kernel-Modus-Seiten, die gesperrt oder im Arbeitsspeicher, in der Regel durch Treiber oder den Kernel fixiert sind.</p></li>
<li><p><strong>Bild</strong> – Seiten aus DLL und .exe-Dateien als ausführbare Datei Bilder geladen.</p></li>
<li><p><strong>MapFile</strong> – Seiten von Datendateien oder Bildern als Daten geladen.</p></li>
<li><p><strong>Des nicht ausgelagerten Pools</strong> – Seiten, die Daten für den Systempool-navigierbaren enthalten.</p></li>
<li><p><strong>PagedPool</strong> – Seiten, die Daten für den Systempool navigierbaren enthalten.</p></li>
<li><p><strong>PFMappedSection</strong> – Seiten der Speicher abgebildete Abschnitte der Auslagerungsdatei gesichert.</p></li>
<li><p><strong>SystemPage</strong> – Arbeitsspeicher Deskriptor Listen und Seiten, die Seitentabelleneinträgen enthalten verwendet, um Systemseiten wie e/a-Speicherplatz, Kernelstapel zuzuordnen.</p></li>
<li><p><strong>UserStack</strong> – Seiten, die die Modus Benutzerdaten für jeden Thread enthalten.</p></li>
<li><p><strong>VirtualAlloc</strong> – Seiten, die durch die VirtualAlloc APIs zugeordnet.</p></li>
<li><p><strong>Win32Heap</strong> – Heap Seiten.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Größe (MB)</strong></td>
<td><p>Die Gesamtgröße der Seiten aggregiert in jeder Kategorie.</p></td>
</tr>
</tbody>
</table>

 

## <a name="step-6-identify-process-working-sets-that-impact-the-memory-footprint"></a>Schritt 6: Identifizieren der Prozess Arbeitsseiten, die den Arbeitsspeicherbedarf beeinflussen


Daten Wohnsitz festlegen können auf viele verschiedene Arten basierend auf die Modalitäten Spalte in der zusammenfassenden Tabelle angezeigt werden. Übersicht über die hat mehrere Modalitäten vordefinierte Spalte, die Sie als Ausgangspunkt für eine Untersuchung verwenden können.

1.  Wählen Sie die **Prozess privater Arbeitssatz** Vorgabe.

    ![Screenshot der WPA Prozess Private Arbeitsseiten Dropdown-Liste.](images/memoryfootprintlab9.png)

2.  Erweitern Sie den **Aktiven MMList** .

    1.  Konzentrieren Sie sich auf die **aktive** Kategorie, unverändert was derzeit Speicherverwendung beeinträchtigt wird.

    2.  **Standby** -Seiten konnte unter Arbeitsspeicherdruck freigegeben werden.

    3.  **Geänderte** Seiten möglicherweise auf den Datenträger geschrieben und freigegebenen.

3.  Sortieren nach Größe, indem Sie auf die Spaltenüberschrift **Größe (MB)** .

4.  Identifizieren der Prozesse, mit der größten Usage. Als Prozessnamen möglicherweise **nicht verfügbar** und **"Unknown (-1)"** angezeigt werden.

    -   **Nicht zutreffend** enthält Seiten, die alle Prozesse wie Speicher-Treiber Pool nicht zugeordnet sind.

    -   **"Unknown (-1)"** enthält freigebbare Seiten.

5.  Erweitern Sie die Prozesse auf der **Seite Kategorie**betrachten.

    1.  Sie können jetzt die Zusammensetzung des Prozesses Arbeitssatz in der folgenden Abbildung sehen.

    2.  Top-Kategorien sollte VirtualAlloc oder Win32Heap, dem analysieren wir in Übung 2 sein.

    3.  Im folgenden Beispiel verwendet **SearchIndexer.exe** 21,7 MB Arbeitsspeicher über **Heap** Zuweisungen und 12.4 MB über **VirtualAlloc** -API-aufrufen.

    ![Tabelle mit Prozess Verwendungsbeispiel.](images/memoryfootprintlab10.png)

Konzentration auf die 3rd Party Prozesse, und ermitteln, ob sie als Teil der vorinstallierte Software beim Systemstart gestartet werden müssen. Als Entwickler sollten Sie die dynamischen Zuweisungen analysieren, die macht Upgradevorgangs zu verstehen, in dem Optimierungen hergestellt werden kann.

 

 






