---
title: Streaming Media-Leistung
description: Streaming Media-Leistung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 01a1594a-93ab-472e-941a-49bc57cbb6a9
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 3afe0862b8f93df55f34f11f1f45783f3dcebcb7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="streaming-media-performance"></a>Streaming Media-Leistung


Die Leistung für Streaming Media-Bewertung hilft Ihnen die Bewerten der Leistung einer konkreten Computerkonfiguration beim Streamen von Medien mit Internet Explorer. Sie können die Bewertungsergebnisse zu verstehen, vergleichen und Verbessern der benutzerfreundlichkeit von streaming Media verwenden.

Das Streaming Media Performance Assessment verwendet eine streaming Serveranwendung, die bereitgestellt wird, auf einem lokalen Computer oder auf einem Remoteserver. Die Bewertung startet Internet Explorer und gibt wieder die Media-Inhalten von Anfang bis Ende oder zu einem angegebenen Zeitpunkt. Klicken Sie dann, Internet Explorer wird geschlossen, und Ergebnisse werden generiert. In der folgenden Grafik veranschaulicht Bewertungsprozess an.

![Workflow-Grafik für streaming-Medien](images/dep-win8-8-techref-streamingmedia.jpg)

Der Schwerpunkt der Bewertung liegt auf Wiedergabe von Videos mithilfe von Internet Explorer. Die Bewertung imitiert wird ein Benutzer, der einen Film überwacht und meldet alle Probleme aufgeführt, die Geräte-. Die Bewertung spielt Videoinhalte aus mehreren Arbeitslasten, die zwischen niedriger Auflösung und hoher Auflösung. Wenn sie auf einem einzelnen Computer ausgeführt wird, verwendet der Prozess 5.0 HTML-Seiten, die im Ordner Inhaltspfad verfügbar sind. Diese Dateien enthalten eingebettete Medien wie 360p.html, 480p.html, 720p.html und 1080p.html-Dateien. Jede video Arbeitslast spielt für eine Minute.

Ein Fehler wird jeder erkennbare visuelle oder akustische Fehler, die Benutzeroberfläche. Die Bewertung enthält Testergebnisse für video-Fehler. Es werden Probleme für Abständen von einer Sekunde während der Ausführung der Videoinhalte gemeldet. Video Probleme sind als minor, mittleren und großen kategorisiert. Die Bewertung meldet außerdem die Platzierung der Probleme. Viewer sind mit hoher Wahrscheinlichkeit zu erkennen, wenn drei oder mehrere aufeinander folgende Frames werden gelöscht. Darüber hinaus zwar Audiodaten mit weitaus geringerer Wahrscheinlichkeit als den Videostream gestört werden, eine Reihe von aufeinander folgenden Initiale Videoframes beeinträchtigen die Viewer Arbeit, da der audio-Track kurz nicht mit dem video Track synchronisiert ist. Weitere Informationen zu den Ergebnissen und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für die Bewertung der Streaming Media-Leistung](results-for-the-streaming-media-performance-assessment.md).

**Warnung**  
Beachten Sie, dass bei der Bewertung der Streaming Media konfiguriert ist zum Streamen mit demselben Gerät, die es wiedergeben das Video (Standardeinstellungen), audio oder video Probleme aufgeführt werden, die nicht bearbeitungsfähige an. Das ideale Szenario zum Testen von streaming Media besteht darin, einem Remoteserver hier beschriebenen einzurichten: [Streaming Media-Bewertung: Einrichten von einem Remoteserver](set-up-a-remote-server-for-the-streaming-media-performance-assessment.md).

 

In diesem Thema:

-   [Bevor Sie beginnen](#beforebegin)

-   [Arbeitslasten](#bkmk-streamingworkloads)

-   [Einstellungen](#settings)

## <a name="a-href-idbeforebeginabefore-you-begin"></a><a href="" id="beforebegin"></a>Bevor Sie beginnen


Der ersten Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Bei der Ausführung dieser Bewertung auf Windows 8.1, stellen Sie sicher, dass die Einstellung **Sammeln Analysis Trace** bei der Beurteilung der erwarteten Akkulaufzeit deaktiviert ist. Wenn diese Option aktiviert ist, wird diese Option eine falsche Schätzung erstellt.

Aktivieren Sie Analyse Trace-Auflistung nur, wenn Sie weitere Informationen zum Untersuchen von anderen Probleme im Zusammenhang mit Energie benötigen.

Zur Vorbereitung der Bewertung ausführen, gehen Sie folgendermaßen vor:

1.  Beenden Sie alle geöffneten Programme.

    **Wichtige**  
    Tippen Sie die Maus noch die Tastatur nicht nach dem Starten des Auftrags zur Bewertung. Andere Anwendungen oder Aufträge zur selben Zeit wie der Bewertungssauftrag ausgeführt, kann Ihre Ergebnisse auswirken. Darüber hinaus umfasst das Streaming Media Performance Assessment keine Messung der Funktionalität durch Suchvorgänge oder anhalten. Seek oder unterbrechen Sie das Video während der Bewertung nicht.

     

2.  Führen Sie die entsprechenden Schritte zum Einrichten des Auftrags zur Bewertung auf einem einzelnen Computer oder auf zwei Computern, die über ein Netzwerk verbunden sind, wie in der folgenden Tabelle dargestellt.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Auftragstyp</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Ausführung des Auftrags auf einem einzelnen computer</p></td>
    <td><p>Zum Ausführen des Auftrags auf einem einzelnen Computer installieren Sie Windows Assessment and Deployment Kit (Windows ADK) technische Referenz und öffnen Sie Windows Assessment-Konsole zu. Führen Sie dann die Anweisungen, die in der Einführung zum Ausführen der Bewertung Streaming Media-Leistung bereitgestellt werden.</p>
    <p>Der Auftrag wird automatisch in Internet Explorer 10 oder höhere Versionen ausgeführt. Der Auftrag wird ausgeführt, in der Pipeline Internet Explorer Medien im Vollbildmodus aus. Benutzerinteraktion wird nicht empfohlen.</p>
    <div class="alert">
    <strong>Hinweis</strong>  
    <p>Eine 1080p in der Standardeinstellung ist 30fps Video für den Auftrag verfügbar. Die Bewertung wiedergegeben auf dem gesamten Bildschirm. Zusätzliche Arbeitslasten umfassen 360p mit 30 fps, 480p mit 30 fps und 720p mit 30 fps.</p>
    </div>
    <div>
     
    </div>
    <p>Wenn der Auftrag auf einem einzelnen Computer ausgeführt wird, gehören die Ergebnisse des Auftrags für die Anzahl der Video- oder Probleme, die auftreten.</p></td>
    </tr>
    <tr class="even">
    <td><p>Ausführung des Auftrags auf zwei Computern</p></td>
    <td><p>So führen Sie den Auftrag für Netzwerkcomputer zwei installieren Sie der technischen Referenz zu Windows ADK auf beiden Computern, öffnen Sie Windows Assessment-Konsole zu, wählen Sie das Streaming Media Performance Assessment und konfigurieren Sie anschließend die Einstellungen wie in [Einstellungen](#settings)dargestellt.</p>
    <p>Der lokale Computer als Stream-Inhalten in der HTTP-streaming-Server-Anwendung, die auf dem zweiten oder remote-Computer installiert ist.</p></td>
    </tr>
    </tbody>
    </table>

     

Vor Beginn der Bewertung die Streaming Media-Performance-Bewertung einige Tests vor dem auf dem System ausgeführt. Wenn diese vor dem Prüfungen ein Fehler auftritt, wird die Bewertung Fehler und Warnungen generiert. Obwohl die Bewertung Ausführung Fehler zu blockieren, blockiert Warnungen nicht die Bewertung Ausführung. Sie können die Korrekturen vornehmen, die werden empfohlen, die Warnmeldung und fahren Sie mit der Auftrag ausgeführt. In den Ergebnissen werden unaddressed Warnungen und Fehler gemeldet. Weitere Informationen zu den Ergebnissen und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für die Bewertung der Streaming Media-Leistung](results-for-the-streaming-media-performance-assessment.md#bkmk-precheck).

### <a name="system-requirements"></a>Systemanforderungen

Sie können dieses Assessment nur auf einem Computer ausführen, auf denen Windows 8 und Internet Explorer 10 ausgeführt wird.

Unterstützte Architekturen zählen X86-basierte X64-basierte Systeme und ARM-basierte Systeme.

Es gibt zwei Methoden zur Ausführung dieses Assessment in Windows RT:

-   Packen Sie den Bewertungssauftrag zur in Windows Assessment Konsole (WAC), und führen Sie ihn auf Windows RW Weitere Informationen finden Sie unter [Packen Sie einen Auftrag verwenden und es auf einem anderen Computer ausführen](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausführen Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idbkmk-streamingworkloadsaworkloads"></a><a href="" id="bkmk-streamingworkloads"></a>Arbeitslasten


Eine Arbeitslast ist ein Satz von automatischen Aufgaben, die Aktivität des Benutzers auf eine vordefinierte, wiederholbare Weise simulieren. Führen Sie die Arbeitslasten unabhängig voneinander. Das Assessment spielt Videoinhalte mehrere arbeitsauslastungen, die zwischen niedriger Auflösung und hoher Auflösung.

Sie können eine beliebige Kombination von diese Arbeitslasten während der Bewertung ausführen auswählen.

-   Arbeitslast 360p (30 f/s)

-   Arbeitslast 480p (30 f/s)

-   Arbeitslast 720p (30 f/s)

-   Arbeitslast 1080p (30 f/s)

"P" in der videoauflösung gibt progressiv Überprüfung, die im Computermonitore und digitale Fernsehgeräte verwendet wird. Ein "i" in videoauflösung gibt Interlaced-Scan in standard verbringt Formaten verwendet. Interlaced Videoinhalte wird in diese Bewertung nicht verwendet werden.

**Hinweis**  
Sie können auch die Streaming Media-Bewertung als eine Arbeitslast einer Energie Effizienz Arbeit verwenden. Weitere Informationen zu Aufträgen Energie-Effizienz finden Sie unter [Dem Standbymodus Energie-Effizienz verbunden](connected-standby-energy-efficiency.md) und [Erstellen und Ausführen einer Energie Effizienz Auftrag](create-and-run-an-energy-efficiency-job.md).

 

## <a name="settings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Von Microsoft, um sicherzustellen, dass die Ergebnisse über verschiedene Computerkonfigurationen oder über einen Zeitraum auf demselben Computer verglichen werden können, werden diese Einstellungen definiert. Beim Überprüfen der Ergebnisse enthält die führen Informationen Metadaten, die gibt an, dass die empfohlenen Einstellungen, damit Sie können auf einfache Weise Ergebnisse erkennen, die zusätzlich zu den empfohlene Einstellungen verwenden, die nicht verwendet wurden.

Sie können diese Einstellungen auch anpassen, wenn Sie andere Daten als standardmäßig Erfassung erfassen möchten. Beispielsweise können Sie Daten zu beschreiben, mit denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers führen würde.

In der folgenden Tabelle wird beschrieben, die Einstellungen für die Bewertung empfohlene Einstellungswerte und alternative Werte für jede Einstellung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Empfohlene Einstellungen verwenden</p></td>
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet wird. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Iterationen</p></td>
<td><p>Gibt die Anzahl der Versuche, die die Bewertung ausgeführt wird. Standardmäßig ist der Wert 3. Video wiedergeben wird 5 Zeiten während 3 Iterationen angezeigt werden. Die erste ist eine 15 Sekunde bis zu initialisieren von Internet Explorer, 3 video Playbacks für die Berechnung der Metriken ist und sind für die Bewertung der Ergebnisse.</p></td>
</tr>
<tr class="odd">
<td><p>Inhaltspfad</p></td>
<td><p>Gibt den Pfad der das Quellverzeichnis für das Arbeitslast-Dataset, das Medien und HTML-Dateien, die die Bewertung enthält. In der Standardeinstellung der Inhalt wird übernommen aus <code>../Content/Streaming Media</code>. Sie können eigene Wert angeben.</p></td>
</tr>
<tr class="even">
<td><p>Servername</p></td>
<td><p>Gibt den Namen des Servers auf dem lokalen Netzwerk. Obwohl das werden leer angezeigt wird, ist der Pfad des Standardserver definiert. Wenn die Einstellung nicht angegeben ist, wird die Bewertung der streaming Server auf dem lokalen Computer gestartet.</p></td>
</tr>
<tr class="odd">
<td><p>Port</p></td>
<td><p>Gibt den Port auf dem Server Anforderungen akzeptiert. Standardmäßig ist der Port auf dem Server Anforderungen akzeptiert als 80 definiert. Sie können auch einen eigenen Wert angeben.</p></td>
</tr>
<tr class="even">
<td><p>Streaming Zeit</p></td>
<td><p>Gibt die maximale Zeit in Sekunden, die die Bewertung wartet, bis ein video Arbeitslast um die Wiedergabe abzuschließen. Standardmäßig ist der Wert für diese Einstellung 65. Sie können auch einen eigenen Wert angeben.</p></td>
</tr>
<tr class="odd">
<td><p>ETW Trace-Dateiname</p></td>
<td><p>Gibt den Namen der Trace-Datei, die die Ereignisse Event Tracing for Windows (ETW) erfasst, die die Bewertung generiert. Obwohl das werden leer angezeigt wird, ist die Ablaufverfolgungsdatei zum Sammeln von Ereignissen definiert. Sie können auch einen eigenen Wert angeben.</p></td>
</tr>
<tr class="even">
<td><p>ETW-Protokollierung deaktivieren</p></td>
<td><p>ETW-Protokollierung deaktiviert. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wenn dieses Kontrollkästchen aktiviert ist, ETW-Ablaufverfolgung ist deaktiviert, und der Bewertungssauftrag generiert eine Ablaufverfolgungsdatei ETW keine.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Streaming Media-Performance-Bewertung](results-for-the-streaming-media-performance-assessment.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

 

 







