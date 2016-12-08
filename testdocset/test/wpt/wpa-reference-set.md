---
title: Alle Referenzen
description: "Windows® Performance Analyzer (WPA) können Sie den Verweis Satz von bei einem Szenario, wodurch eine umfassendere Bewertung als Workingset Effekte eines Szenarios auf dem System verwendeter Arbeitsspeicher zu analysieren."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
author: v-gmoor
ms.assetid: 
ms.prod: W10
ms.mktglfcycl: 
ms.sitesec: msdn
ms.openlocfilehash: 8fecf48cb4093eed4aa7085ff4a5c3949a8366c0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reference-sets-and-the-system-wide-effects-on-memory-use"></a>Verweisen auf festgelegt und die systemweite Effekte bei der Verwendung von Arbeitsspeicher 

Ein *Verweis festgelegt* , wird empfohlen, die reale Effekte eines Prozesses für die Arbeitsspeicher-Verfügbarkeit des Systems als Ganzes zu verstehen.

In der Vergangenheit hat Speicherverwendung durch den *Arbeitsseiten* des Prozesses zu einem bestimmten Zeitpunkt gemessen. Das Workingset eines Prozesses ist die Menge von Seiten im virtuellen Adressraum des Prozesses, die derzeit speicherresidenten physischen sind. (Weitere Informationen zu arbeiten, finden Sie unter [Arbeiten mit](https://msdn.microsoft.com/en-us/library/windows/desktop/cc441804.aspx) auf Windows-Entwicklungscenter.)


## <a name="limitations-of-a-working-set"></a>Einschränkungen von Workingset

Workingset Informationen beschränkt, da nicht alle des Arbeitsspeichers angezeigt, die zur Unterstützung des Prozesses zwischengespeicherten Dateien und die Dienste aufgeführt, die der Prozess nutzt verwendeter Arbeitsspeicher verwendet wird.
Darüber hinaus ist Workingset stark abhängig von den Zustand des Computers, dessen Größe des Arbeitsspeichers und der Umfang der Aufgaben des Teilsystems Arbeitsspeicher erforderlich sind, um alle Vorgänge auf dem System mit den Arbeitsspeicher angeben, wenn sie anfordern (die Ebene des *genügend Arbeitsspeicher zur Verfügung*). Darüber hinaus wird Workingset erheblich durch die Einschränkung aus Sicherheitsgründen Richtlinien des Betriebssystems beeinflusst. Also Workingset wird nur eine vorübergehende Messung und Effekte außerhalb des Prozesses gezielte lässt.


## <a name="advantages-of-a-reference-set"></a>Vorteile einer Gruppe (engl.)

Dagegen ist ein Verweis ein Maß für die systemweite Menge von Arbeitsspeicherseiten, die während eines bestimmten Szenarios auf eine beliebige Prozess oder neue Aktivität auf dem System zugegriffen hat. Sie enthält alle Seiten im Namen der Komponente, die untersucht wird, unabhängig davon, welchen Prozess Zugriff auf die Seite zugegriffen.
Der Verweis Set variiert basierend auf RAM-Größe, Arbeitsspeicherdruck oder OS verkürzen Richtlinien nicht. Messen der eine Reihe von Verweis ist eine sehr präzise Möglichkeit zum Bewerten der speicherauslastung durch den gesamten System für alle Arbeitslasten, da die Seiten, die sich derzeit im des Arbeitssatzes von Prozessen oder, durch Systemprozesse oder Treibern, zugegriffen werden, in den Verweis enthalten sind. Ein Verweis ist speziell für ein Szenario, nicht mit einem bestimmten Zeitpunkt: Es ist nicht zulässig, bitten, *Was Verweis Meine Prozess zu diesem Zeitpunkt ist der?* Es ist jedoch ungültig zu Fragen, *Was Verweis das System in diesem Szenario ist der?* oder *Was Verweis Meine Prozess in diesem Szenario ist der?*

Die Vorstellung, dass hinter einem Satz Verweis ist einfach: um ein genaues Bild des Arbeitsspeichers zu erteilen, die während des Szenarios referenzierten systemweit ist, werden Seiten gezählt, wenn zugegriffen und veröffentlicht. Diese Methode bietet einen umfassenden Überblick in die Spitzen Speicherverwendung ebenso wie in was am Ende des Szenarios (d. h., *stabilen Zustand verwenden*) aussteht.

<blockquote><p><b>Hinweis</b>&nbsp;&nbsp;&nbsp;werden nur der erste Verweis in eine Seite erfasst.</p></blockquote>

Eine Reihe Verweis kann ungefähr angesehen werden, als Maßeinheit für die Menge des Arbeitsspeichers, die vor dem Rest des Systems durchgeführt werden kann, während der Ausführung des Szenarios oder Typ, die Menge des Arbeitsspeichers, die fehlerhaft und von der Festplatte, um das Szenario ausführen (wenn andere Teile des Systems zu ausgelagert werden Arbeitsspeichers verursacht haben) gelesen werden muss. Aus diesem Grund ist ein Verweis wertvolle zum Bestimmen der *Auswirkungen auf die Leistung* der Speicher verwenden.


# <a name="how-to-collect-reference-set-data"></a>Festlegen, wie Verweis sammeln Daten

Sie können zwei verschiedene Befehlszeilentools verwenden, um Referenzdaten Set sammeln: Windows Performance-Aufzeichnung (WPR) und Xperf. Sie können auch die WPR-Benutzeroberfläche verwenden.

WPR und Xperf sind Teil der Windows Performance Toolkit, das in dem Windows Assessment and Deployment Kit (ADK) enthalten ist. Sie können die ADK für Windows 10 aus den folgenden Link herunterladen: [Windows Assessment and Deployment Kit](http://go.microsoft.com/fwlink/p/?LinkId=526740). 

<blockquote><p><b>Hinweis</b>&nbsp;&nbsp;&nbsp;verwenden Sie eine Eingabeaufforderung mit erhöhten Rechten, wenn Daten erfassen Verweis festgelegt werden.</p></blockquote>


## <a name="collect-data-with-wpr"></a>Sammeln von Daten mit WPR

Erfassen von Daten mit WPR, geben Sie Folgendes ein:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Wpr-Referenceset - Filemode starten**

Führen Sie das Szenario, und halten Sie dann auf das Sammeln von Daten eingeben:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Wpr-beenden**&nbsp;<i>Dateinamen</i><b>ETL</b>


## <a name="collect-data-with-xperf"></a>Sammeln von Daten mit Xperf

Wenn Xperf Arbeitsspeicher Spuren sammeln, geben Sie dieselbe Größe für die minimale und maximale Puffer, um sicherzustellen, dass eine konsistente Menge des Systemspeichers reserviert für Event Tracing for Windows (ETW) vorhanden ist.
Die Konsistenz macht Vergleich zwischen aufgrund der verringerten Variabilität einfacher ausführen. (Diese Puffer werden automatisch auf die gleiche Größe festgelegt bei Verwendung von WPR.)

Erfassen von Daten mit Xperf, geben Sie Folgendes ein:

<blockquote>
<b>Xperf-auf Referenceset - Minbuffers 50 - MaxPuffer 50 - Puffergröße 1024 - Stackwalk PageAccess + PageRelease + PageRangeAccess + PageRangeRelease + PagefileMappedSectionCreate + VirtualFree + PagefileMappedSectionDelete-Benutzer beginnen-auf Win32HeapRanges - Minbuffers 10 - MaxPuffer 10 - Puffergröße 1024</b>
</blockquote>

Führen Sie das Szenario, und halten Sie dann auf das Sammeln von Daten eingeben:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Xperf-Stop-Benutzer-beenden – d**&nbsp;<i>Dateinamen</i><b>ETL</b>


## <a name="collect-data-with-the-wpr-desktop-app"></a>Sammeln von Daten mit WPR-desktop-app

Sie können auch Sammeln von Daten mithilfe von WPR-desktop-app wprui.exe. Wählen Sie in der Benutzeroberfläche bei **Ressource Analysis** **Analyse Verweis festlegen**aus.
(Wenn Sie diese Option nicht angezeigt werden, müssen Sie auf klicken Sie auf **Weitere Optionen**, und erweitern Sie dann auf **Ressource Analysis**).

![Starten im Dialogfeld des Windows Performance Aufzeichnung (WPR).](images/wpa-reference-set-wpr-dialog.png)

Klicken Sie zum Starten der Aufzeichnung, klicken Sie auf **Start**, und führen Sie das Szenario.

Um Aufzeichnung beenden und speichern Sie die Daten der nachrichtenablaufverfolgung, klicken Sie auf **Speichern**.

![Dialogfeld des Windows Performance Aufzeichnung (WPR) mit active Aufzeichnung.](images/wpa-reference-set-wpr-dialog-recording.png)


# <a name="how-reference-set-tracing-works"></a>Wie Verweis Tracing Works festlegen

Wenn WPR startet das Sammeln von Trace Verweis aus einem Satz, entfernt das System sofort alle Seiten im Arbeitsspeicher von Arbeitsseiten aller Prozesse, einschließlich des Systems an. Darüber hinaus werden alle Seiten, die in einem Prozess oder das System die Arbeitsseiten verbleiben-Konto für Seiten aufgezeichnet, die gesperrt oder als nicht navigierbaren markiert werden. Nach dem Klicken auf den ersten Zugriff auf eine Seite, die in der Liste standby verschoben wurde, die einen soft-Fehler in der Verfolgung des Satzes Verweis aufgezeichnet wird, wird die Seite des Arbeitssatzes über den Prozess hinzugefügt, und der Prozess weiter ausgeführt.
Nachfolgende Zugriffe auf eine Seite in den Arbeitsseiten des Prozesses oder System verursacht nicht einer anderen soft Seitenfehler, da die Seite bereits im des Arbeitssatzes befindet. Daher die Ausführung wird fortgesetzt, ohne alle zusätzlichen Zugriffe auf Seiten im Workingset Aufzeichnung, und daher die Gesamtzahl der Zugriffe auf eine Seite nicht in das Ablaufverfolgungsprotokoll aufgezeichnet.

Entsprechend wird der erste Zugriff auf eine andere Seite in demselben Prozess in der Verfolgung, einschließlich der neu zugeordnete Seiten aufgezeichnet. Seiten, die veröffentlicht werden (z. B. von **HeapFree**), und Dateien, die gelöscht werden ihre *ausstehenden Größe* nicht mehr den Verweis am Ende des Intervalls Messung festgelegt haben, aber erfolgt weiterhin angezeigt. Dateien, die geschlossen oder ausführbare Dateien, die aus dem Speicher entfernt wurden, werden nicht von der Größe des ausstehenden entfernt, da sie nicht aus dem RAM auf Schließen oder entfernen gelöscht werden. Wenn eine Seite zwischen mindestens zwei Prozessen freigegeben ist, zeichnet Trace ersten Zugriff auf diese Seite in den einzelnen Prozessen, die er berührt haben.

<blockquote><p><b>Hinweis</b>&nbsp;&nbsp;&nbsp;Aufzeichnung Trace Verweis aus einem Satz kann sich erheblich auf die Systemleistung, haben, da allen Prozessen große Anzahl von Seiten wieder in ihre Arbeitsseiten fault, nachdem ihre Arbeitsseiten geleert werden müssen.</p></blockquote>


# <a name="reference-set-visualizations"></a>Verweis festgelegt Visualisierungen

WPA bietet die folgenden Ansichten von Referenzdaten festlegen:

-  [Verweis festgelegt ausstehender Größe von Prozess](#reference-set-outstanding-size-by-process)
-  [Verweis festgelegt ausstehender Größe nach Kategorie](#reference-set-outstanding-size-by-category)
-  [Verweis festgelegt ausstehender Größe von Dynamic-Datei](#reference-set-outstanding-size-by-dynamic-file)


## <a name="reference-set-outstanding-size-by-process"></a>Verweis festgelegt ausstehender Größe von Prozess

Dieses Feld zeigt Arbeitsspeicher geteilt durch den Prozess für die Ansicht. Dies ist eine ausgezeichnete Quelle zu starten, wenn Sie die Auswirkung auf einer bestimmten Anwendung Arbeitsspeicher untersuchen.

<a href="images/wpa-reference-set-outstanding-size-by-process-01.png"><img src="images/wpa-reference-set-outstanding-size-by-process-01.png" alt="Example of the 'Outstanding Size by Process' view in Windows Performance Analyzer (WPA)."></a>

Die Bedeutung der Spalten in dieser Ansicht finden Sie unter [wichtige Definitionen](#important-column-definitions), die weiter unten in diesem Thema.


## <a name="reference-set-outstanding-by-category"></a>Legen Sie nach Kategorie ausstehender Verweis

Zeigt Seiten im Arbeitsspeicher nach Kategorie für die Ansicht.

<a href="images/wpa-reference-set-outstanding-by-category-01.png"><img src="images/wpa-reference-set-outstanding-by-category-01.png" alt="Example of the 'Reference Set Outstanding by Category' view in Windows Performance Analyzer (WPA)."></a>

Eine Erläuterung der Seitenkategorien finden Sie unter [Seite Kategorie (dynamisch)](#page-category-dynamic) und der [Seite Kategorie (Datei)](#page-category-file)weiter unten in diesem Thema.


## <a name="reference-set-outstanding-by-dynamicfile"></a>Verweis von Dynamic-Datei ausstehender festgelegt

Dieses Feld zeigt Arbeitsspeicher kategorisiert, ob es im Speicher gesicherte oder dateibasierten für die Ansicht ist.

<a href="images/wpa-reference-set-outstanding-by-dynamic-file-01.png"><img src="images/wpa-reference-set-outstanding-by-dynamic-file-01.png" alt="Example of the 'Reference Set Outstanding by Dynamic/File' view in Windows Performance Analyzer (WPA)."></a>

<blockquote><p><b>Hinweis</b>&nbsp;&nbsp;&nbsp;<i>Speicher gesicherte Seiten</i> werden gesichert, durch die Auslagerungsdatei oder im Fall von nicht ausgelagerten Pools nie ausgelagert. Speicher gesicherte Seiten enthalten Stack, Heap, VirtualAlloc und anderen Seitenkategorien, bei die eine Datei auf dem Datenträger direkt zuordnen nicht. <i>Dateibasierten Seiten</i> werden in einzelne Dateien auf dem Datenträger, beispielsweise Bild-Modul gesichert.</p></blockquote>


# <a name="understanding-reference-set-data"></a>Grundlegendes zu Verweis Einrichten von Daten

Wie bereits erwähnt, stellt der Verweis Satz den Arbeitsspeicher, der während der Ausführung der relevanten Szenario geändert wurde. In dieser Hinsicht die Referenz wird die ist-Kosten der Ausführung der Arbeitslast und der genauesten Accounting von höherer Speicherbedarf von der Arbeitslast darstellt.

Sie sind in der Regel höherer Speicherbedarf von einem bestimmten Prozess interessiert, so wird mit der Tabelle *Verweis festgelegt ausstehender Prozess* beginnen soll. Sie möchten die Stellen untersuchen, in dem die Speicherverwendung erhöht oder verringert wird, sowie, bei denen es Spitzen und stetig war.


## <a name="peak-vs-steady-state"></a>Spitzenzeiten im Vergleich zu stabilen Zustand

Da die Referenz Gruppe die Messung der Größe des Arbeitsspeichers, die während eines Szenarios verwiesen wird ist, kann es nicht intuitiv sein, dass ihre Größe je verringern kann. Beim Speicher ist freigegeben und wieder an das System für andere Zwecke verwendet werden soll, ist es subtrahiert den Verweis auf die der Tatsache überarbeitet, dass es später wiederverwendet werden kann.

Dadurch wird ein Szenario werden zwei primäre Referenz Set Metriken: *stabil* und *Höchstwerte*.

<table>
<tr><th>Metrisch</th><th>Beschreibung</th></tr>
<tr><td>Konstanter&nbsp;Zustand</td><td><p>Geplante Kosten der app oder Szenario. Dies kann durch Ausführung ein Szenario (oder mehrere Szenarien) und darauf zu warten, damit das System Leerlauf erneut zu erreichen gemessen werden. Minimieren der Anzahl der Seiten, die Ihre app über verschiedene Szenarien in einem stabilen Zustand zugreift, sehen Sie die Szenarien schneller ausgeführt werden (beispielsweise schneller fortsetzen), und geben Sie eine wünschen, die für Ihre Benutzer besser ist, da Sie den Arbeitsspeicherdruck auf dem System reduziert werden können.</p></td></tr>
<tr><td>Spitzenzeiten</td><td><p>Vorübergehende hohe Auslastung Arbeitsspeicher und mehr nützliche Informationen nicht genügend Arbeitsspeicher push können. Durch Verringern der Häufigkeit und Magnitude alle Spitzen Auslastung, werden Ihre app oder Feature eine bessere "System Bürger" durch Verringern der das Potenzial für die Auslagerung oder der Beendigung von anderen Prozessen.</p></td></tr>
</table>


## <a name="important-column-definitions"></a>Wichtige Definitionen

Wenn Sie die Verfolgung von einen Verweis in WPA untersuchen, sind die folgenden Spalten in der Tabellenansicht besonders wichtig:

-  [Auswirkung-Typ](#impact-type)
-  [Größe und Größe der Auswirkungen](#size-and-impact-size)
-  [Kategorie Klasse](#category-class)
-  [Seite Kategorie (dynamisch)](#page-category-dynamic)
-  [Seite Kategorie (Datei)](#page-category-file)
-  [Allocation-Stapel](#allocation-stack)
-  [Störenden stack](#impacting-stack)

Wenn eine der Spalten aus der Ansicht in WPA nicht vorhanden ist, können Sie es mithilfe der rechten Maustaste auf eine Spaltenüberschrift in der aktuellen Ansicht auswählen und dann auf die fehlende Spalte aus der Liste hinzufügen.

Alle drei Referenz Satz Ansichten enthalten 4 Größen des Speichers wird gezählt Bereitstellung verschiedene Spalten:

-  **Größe (Prozessansicht)**: die gesamte Menge von Seiten, die durch den angegebenen Prozess
-  **Größe (System View)**: die Gruppe von Seiten, die durch 
-  **Auswirkung Größe (Prozessansicht)**
-  **Auswirkung Größe (System View)** 

Verschiedene Ansichten anzeigen verschiedene Spalten in der Standardeinstellung, aber sie sind alle verfügbaren in allen Ansichten Refset, wenn Sie diese suchen und diese addieren Größen der gleichen Weise, unabhängig davon, welche, der Ansichten sie verwenden.


### <a name="impact-type"></a>Auswirkung-Typ

Die Spalte **Typ Auswirkungen** identifiziert den Typ des Effekt eine Zuordnung von Arbeitsspeicher auf den Speicher derzeit: **Impacting**, **vorübergehende**und **Persistent**.

<table>
<tr><th>Auswirkung&nbsp;Typ</th><th>Beschreibung</th></tr>
<tr>
<td>Beeinträchtigen</td>
<td><p>Speicher, die (A) wurde vor dem Start des Ihre Ansicht belegt und freigegeben werden, während die Ansicht (reservierte außerhalb und innerhalb) oder (B) während Ihrer Ansicht belegt und nach dem Ende der Ansicht (reservierte innerhalb und außerhalb freigegeben) freigegeben. Eine Zuweisung störenden wirkt sich auf den Speicher am Ende der Ansicht verwendet.</p></td>
</tr>
<tr>
<td>Vorübergehende</td>
<td><p>Arbeitsspeicher, die belegt und während der Ansicht (innerhalb zugewiesen und innerhalb) freigegeben wurde. Eine vorübergehende Zuordnung ist nur innerhalb der aktuellen Ansicht aktiv.
Vorübergehende Zuweisungen Beitrag normalerweise zu jeder Spitzen bei der Verwendung in einer Ansicht.</p></td>
</tr>
<tr>
<td>Persistent</td>
<td><p>Zuweisungen, die vor dem Start des Ansichtsfensters zugewiesen und nach dem Ende des (außerhalb zugewiesen ist und freigegeben außerhalb) freigegeben wurden. Während die gesamte Ansichtsfensters ist eine permanente Zuordnung aktiv.</p></td>
</tr>
</table>


### <a name="size-and-impact-size"></a>Größe und Größe der Auswirkungen

Die **Größe** -Spalte der **Verweis festlegen ausstehender Prozess** stellt die *Magnitude* Zugriffe, unabhängig von der Art der Auswirkung (siehe Abbildung in der Spalte **Typ der Auswirkungen** ), dass eine Zuweisung bewirkt, **Impacting**, **vorübergehende**oder **Persistent**sein könnte dass.
Dieser Schritt ist nicht sehr hilfreich für die Analyse, jedoch für Diagramme in WPA angefordert wird.

**Auswirkungen Größe** stellt die Auswirkung auf die Größe von der Anfangs-Zeitstempel die Endzeichenposition Zeitstempel für die aktuelle Zoomstufe. Ein Vergleich der grafisch dargestellten Werte am Anfang und Ende für das Blickfeld, einfach ausgedrückt, entspricht die Delta. Vorübergehende oder dauerhafte Zugriffe führen nicht den Wert grafisch dargestellt, für die Zoom-Fenster zu ändern, und daher nicht gezählt.

Wenn zwei separate Prozesse auf derselben Seite des physischen Arbeitsspeichers verweisen, wird die Seite für jeden Prozess in der Spalte **Größe** gezählt. Hinzufügen von zwei Werten erzeugt systemweiten insgesamt für den ein Verweis kein da nachfolgenden Zugriff nach des Arbeitssatzes die Seite hinzugefügt wird, nicht gezählt wird. Die Seite wird auch in der Spalte **Auswirkungen Größe** gezählt, nur einmal für den ersten Prozess, die auf die Seite zugreift. Hinzufügen der Werte in **Auswirkungen Größe** für einen Prozess erzeugt gültige systemweiten insgesamt für den Verweis ein, und dies geschieht ohne fehlende oder Multiplizieren die Anzahl von einer beliebigen Seite. Aus diesem Grund Werte in **Auswirkungen Größe** die tatsächliche systemweiten Effekte auf Speicher darstellt. 

Berücksichtigen Sie ein Beispiel von t\_starten in t\_beenden möchten, mit den folgenden Werten:

-   Diagramm zum t\_starten: 10 MB

-   Klicken Sie im Fenster neue (Impacting)-Zugriffe: 10 MB

-   Vorübergehende im Fenster zugegriffen: 10 MB

-   Diagramm zum t\_Ende: 10 (Persistent) + 10 (Impacting) = 20

-   Größenspalte: 10 (Persistent) + 10 (vorübergehende) + 10 (Impacting) = 30

-   Auswirkung der Spalte Größe: 10 (Impacting)

<blockquote><p><b>Hinweis</b>&nbsp;&nbsp;&nbsp;ändert die Ansicht vergrößern und verkleinern und bewirkt, dass diese Größen neu berechnet werden.</p></blockquote>


### <a name="category-class"></a>Kategorie-Klasse

Es gibt zwei Kategorien für den Zugriff auf Speicherseiten, die in der Spalte **Kategorie-Klasse** in WPA identifiziert: **dynamische** oder **Datei**.

<table>
<tr><th>Kategorie&nbsp;Klasse</th><th>Beschreibung</th></tr>
<tr><td>Dynamik</td><td><p>Hierbei handelt es sich bei Bedarf Zuweisungen Systemstatus oder Arbeitsspeicher, die mit einem Prozess verknüpft sind, die nicht über ein Herunterfahren des Systems beibehalten werden. Die Zuweisungen nicht ausgelagerten oder durch die Seitendatei gesichert werden können, und sie können <b>Heap</b> <b>VirtualAlloc</b>und usw. sein, wie in der <b>Seite Kategorie</b> -Spalte identifiziert. Freigebbare dynamischer Arbeitsspeicher wird auch als <b>PFMappedSection</b> <b>Seite</b> Kategorie identifiziert.</p></td></tr>
<tr><td>File</td><td><p>Dies sind die Dateien, die durch verarbeitet, die durch eine Datei auf dem Datenträger gesichert werden. Dateien geladen als Daten Dateien als Bilder geladen (ausführbare oder DLL-DATEI), und ordnen von Dateien.</p></td></tr>
</table>


### <a name="page-category-dynamic"></a>Seite Kategorie (dynamisch)

In der Spalte **Seite Kategorie** zeigt die Kategorie-Klasse **dynamische**, ist WPA eine oder mehrere der in der folgenden Tabelle beschriebenen Kategorien.

<table>
<thead>
<tr class="header">
<th>Seite&nbsp;Kategorie, dynamische Zuweisung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>VirtualAlloc</td>
<td>Diese Seitenkategorie enthält große dynamische Zuweisungen (größer als 512 KB oder 1 MB, je nach System) dynamische Zuweisungen von der app (oder gestellt vom Framework im Namen der app) mithilfe der virtuellen Zuweisung APIs.</td>
</tr>
<tr class="even">
<td>Heap</td>
<td>Diese Seitenkategorie enthält kleine, dynamische Zuweisungen, die durch die app (oder die app von Framework getätigter) mithilfe der Heapzuweisung APIs.</td>
</tr>
<tr class="odd">
<td>UserStack</td>
<td>Benutzermodus-Stapel eines Threads.</td>
</tr>
<tr class="even">
<td>PFMappedSection</td>
<td>Freigebbare dynamischen Arbeitsspeicher. Diese Seitenkategorie misst oft die Menge des Arbeitsspeichers für Grafiken Zuweisungen aufgewendeten. Aus der Sicht app sind dies nicht nur Bilder, Videos, andere "Media-Pipeline" Zuweisungen, dass Ihre app ist geeignet, aber außerdem die grundlegenden Bausteine der Benutzeroberfläche, beispielsweise die Flächen verwendet enthält, um eine Listenansicht gerendert.</td>
</tr>
<tr class="odd">
<td>CopyOnWriteImage</td>
<td>Kopie bei Schreibvorgang Seiten für Module, die in den Prozess geladen werden.</td>
</tr>
<tr class="even">
<td>LargePage</td>
<td></td>
</tr>
<tr class="odd">
<td>AWEPage</td>
<td>Physische Seiten, die von einem Prozess zugeordnet werden.</td>
</tr>
<tr class="even">
<td>PageTable</td>
<td></td>
</tr>
<tr class="odd">
<td>PagedPool</td>
<td>Kernel-Heap.</td>
</tr>
<tr class="even">
<td>Nicht PagedPool</td>
<td>Heap nicht navigierbaren Kernelmodus.</td>
</tr>
<tr class="odd">
<td>SessionPrivate</td>
<td></td>
</tr>
<tr class="even">
<td>KernelStack</td>
<td>Stapel für Kernel-Modus.</td>
</tr>
<tr class="odd">
<td>Treiber</td>
<td></td>
</tr>
<tr class="even">
<td>DriverLockedSystemPage</td>
<td></td>
</tr>
<tr class="odd">
<td>Seitentabelleneinträge</td>
<td></td>
</tr>
</tbody>
</table>


### <a name="page-category-file"></a>Seite Kategorie (Datei)

In der Spalte **Seite Kategorie** zeigt die Kategorie-Klasse- **Datei**ist WPA eine oder mehrere der in der folgenden Tabelle beschriebenen Kategorien.

| Seite&nbsp;Kategorie, -Datei | Beschreibung |
|-----------------------|---------------------------------------------------------------|
| Image                 | Eine Datei als ausführbare Datei, wie etwa eine DLL-DATEI geladen. |
| MapFile               | Eine Datei als Daten geladen. |
| Metadatei              | Ein Verzeichnis oder eine Systemprotokoll. |
| RegistryFile          | Eine Registrierungsdatei. |
| Prefetcher            | Informationen, die verwendet wird, um das Starten einer App beschleunigen. |
| DriverFile            | Ein Treiber, der als ausführbare Datei geladen wird. |


### <a name="allocation-stack"></a>Allocation-Stapel

Die **Zuordnung Stack** Spalte identifiziert, wo der Speicher reserviert ist.


### <a name="impacting-stack"></a>Störenden Stack

**Stack Beeinträchtigung der** Spalte wird warum der Speicher zugegriffen wird.


# <a name="recommendations-for-measuring-and-improving-performance-in-a-reference-set"></a>Empfehlungen für messen und Verbessern der Leistung in ein Verweis festgelegt

Die folgenden allgemeinen Empfehlungen sind hilfreich für einen Satz Verweis messen und zur Verbesserung der Geltungsbereich eine app oder ein Feature auf dem System. Verwenden Sie diesen Empfehlungen in der folgenden Reihenfolge:

-   [Untersuchen Sie stabilen Zustand verwenden und bei Verwendung von Arbeitsspeicher](#examine-steady-state-use-and-peak-use-of-memory)

-   [Der Prozess mit der größten Effekte zu Schwerpunktthemen](#focus-on-the-process-with-the-greatest-effects)

-   [Definieren Sie und kategorisieren Sie Seiten im Arbeitsspeicher](#characterize-and-categorize-memory-pages)

<blockquote><b>Hinweis</b>&nbsp;&nbsp;&nbsp;Tracing verwendet Arbeitsspeicher, der als nicht ausgelagerten Pool mit der Beschreibung "ETWB" für <strong>ETW-Puffer</strong>angezeigt wird.</blockquote>


## <a name="examine-steady-state-use-and-peak-use-of-memory"></a>Untersuchen Sie stabilen Zustand verwenden und bei Verwendung von Arbeitsspeicher

Es sind zwei Aspekte wichtig: (1) die Größe des Speicherverwendung, die in einer stabilen Zustand am Ende des Szenarios und (2) ist, in denen die Verwendung Spitzen im Satz Verweis auftreten und warum. Analyse sollte konzentrieren Sie sich zunächst auf die Auswirkungen stabilen Zustand des Szenarios, und klicken Sie dann alle bestimmten Spitzen in den Diagrammen des Satzes Verweis betrachten.


## <a name="focus-on-the-process-with-the-greatest-effects"></a>Der Prozess mit der größten Effekte zu Schwerpunktthemen

Konzentrieren Sie sich auf Prozesse, die die größte Auswirkung auf die Verweis festgelegt sind, einschließlich der Prozess der Zinssatz sowie andere Systemprozesse verfügen.


## <a name="characterize-and-categorize-memory-pages"></a>Definieren Sie und kategorisieren Sie Seiten im Arbeitsspeicher

Einstufung für Kategorie von Seiten im Arbeitsspeicher, dynamische Klassen und Datei werden muss und weiter in Unterkategorien unterteilt.


### <a name="examine-memory-pages-in-the-file-category"></a>Untersuchen Sie Speicherseiten in der Dateikategorie

Die beste Möglichkeit zum Untersuchen der Datei Zugriffe ist in der Regel nach Pfad Struktur gruppiert und identifizieren Sie dann auf System-bezogene Datei Zugriffe (wie DLLs) und Prozess-spezifischen Datei greift auf (wie lokale Datenbanken, Textdateien, JPEG-Bilder usw.).

Minimieren die Prozess-spezifischen Datei Zugriffe reduziert die Größe des Satzes Verweis. Verbesserte Leistung, um zu testen, bevor die Anwendung starten oder Feature getesteten geladen wird (ein *Kalt Szenario*).

Diagnose von der Dateianteil Verweis aus einem Satz erfordert im Wesentlichen wissen, welche DLLs für Ihr Szenario und warum diese geladen werden, sowie alle Dateien, die Ihre Anwendung oder ein Feature greift auf (beispielsweise Bilddateien, wenn für eine Bildschirmpräsentation mit der Decodierung) eindeutig sind.


### <a name="examine-memory-pages-in-the-dynamic-category"></a>Untersuchen Sie die Arbeitsspeicherseiten in der Kategorie dynamischen

Verwenden Sie folgende Schritte Trace Verweis aus einem Satz zu analysieren:

-   [Nach Seitenkategorie klassifizieren](#classify-by-page-category)

-   [Anwenden von Tags stack](#apply-stack-tags)

-   [Heap-spezifischen Tracing ausführen](#perform-heap-specific-tracing)

-   [Untersuchen von Zuweisungen Stapel mit hoher Auslastung](#examine-allocations-stacks-that-have-high-usage)

-   [Untersuchen Sie Systemprozesse, die erhebliche Auswirkungen haben](#examine-system-processes-that-have-significant-effects)

-   [Kategorisieren Sie zum Analysieren von Kosten und Optionen für die Verringerung der bestimmen.](#categorize-to-analyze-costs-and-identify-options-for-reduction)

<br/>

#### <a name="classify-by-page-category"></a>Nach Seitenkategorie klassifizieren

Nach Seitenkategorie in das folgende klassifizieren: **Win32Heap**, **VirtualAlloc**oder **PFMappedSection**. Die Kategorie kann direkt an den Prozess Ergebnisarray als Attribut zugewiesen werden.

Systemspezifische Kategorien können in der Regel für die Erstanalyse, ignoriert werden zwar Haupt-Beiträge (mehr als 2 bis 3 MB) aus dem ausgelagerte Pool- oder Kernelstapel in der Regel untersucht, da solche Datenträger oft eine übermäßige Verwendung von Threads oder Komponenten, beispielsweise die Registrierung angibt.


#### <a name="apply-stack-tags"></a>Anwenden von Tags stack

Anwenden von Tags zum Speicherbedarf von Stack kategorisieren Stack kann sehr hilfreich sein, identifizieren, wo Ihre Speicherverwendung stammt.


#### <a name="perform-heap-specific-tracing"></a>Heap-spezifischen Tracing ausführen

Während Stack Tags für einen Satz Verweis Sie eine allgemeine Vorstellung die Prozesse den Heap verwenden übergeben können, müssen Sie häufig Heap-spezifischen tracing verfügt Heap-Verwendung sich erheblich in Ihrem Szenario ausführen. Eine Reihe Referenz bietet nicht, dass die erforderliche Granularität den Heap aus einer Sicht Zuweisung analysieren, da nur den Verweis eingerichtet identifiziert, welche Seiten im Arbeitsspeicher verwiesen werden. Ein stark fragmentierter Heap wird möglicherweise eine große stabilen Zustand Bilanz für Heap-Verwendung, auch wenn die Heapzuweisungen selbst kleine, aber dem Heap zahllosen werden angezeigt.


#### <a name="examine-allocations-stacks-that-have-high-usage"></a>Untersuchen von Zuweisungen Stapel mit hoher Auslastung

VirtualAlloc: Untersuchen Sie bestimmte Zuweisung Stapel mit hoher Auslastung von **VirtualAlloc**. Anzeigen von **VirtualAlloc Commit Lebensdauer** in der Registerkarte **Analyse** werden Details zur Verwendung von Commit vom Prozess angezeigt.


#### <a name="examine-system-processes-that-have-significant-effects"></a>Untersuchen Sie Systemprozesse, die erhebliche Auswirkungen haben

Gibt es andere Systemprozesse, die größer als Ergebnis dieses Szenario Speicher auswirken? Beispiele für Kandidaten sind Services, app Broker und Virenscanner.


#### <a name="categorize-to-analyze-costs-and-identify-options-for-reduction"></a>Kategorisieren Sie zum Analysieren der Kosten und Optionen für die Verringerung der bestimmen

Wenn Sie über den vorstehenden Empfehlungen gearbeitet haben, verwenden Sie die folgende Schritte aus die Stapeln analysieren, die den größten wirken sich auf das System und Erforschen von Möglichkeiten zum Arbeitsspeicher Kosten zu reduzieren.

1.  Identifizieren der Stapel mit der höchsten Kosten.

2.  Führen Sie mit Anmerkungen die Stapel durch einen Namen für die welche einzelnen kategorisiert sollte.

3.  Überlegen Sie, ob die Kosten für jede Kategorie und den Stapel eine erwartete Betrag für das Szenario ist.

4.  Überlegen Sie, ob Sie die Spitzen im aktiven Szenario durch, beispielsweise beeinträchtigen können beim Zuordnen des Speichers nur bei Bedarf.

5.  Überlegen Sie, ob Sie stabilen Zustand Verwendung von Arbeitsspeicher reduzieren können. Beispielsweise können Sie Ressourcen während stabilen Zustand freigeben, die szenariospezifische und nicht erforderlich sind? Beispiele für gehören Caches und Domains. Freigeben von Ressourcen kann die stabilen Zustand Speicherbedarf verringern.
