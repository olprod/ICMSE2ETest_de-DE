---
title: Streaming Media-Bewertung Einrichten von einem Remoteserver
description: Streaming Media-Bewertung Einrichten von einem Remoteserver
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7cc47476-f2c3-4f82-8430-731fc035266a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 98cef8245d64209e79c7b535eb4ff9203dcd5ca5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="streaming-media-assessment-set-up-a-remote-server"></a>Streaming Media-Bewertung: Einrichten von einem Remoteserver


Das Streaming Media Performance Assessment enthält eine Option, um die Bewertung auf 2 Computern ausgeführt werden. In diesem Szenario gibt eine streaming-Server-Anwendung, die auf einem zweiten oder remote-Computer installiert ist HTTP Inhalt auf dem Computer mit der Bewertung. In diesem Thema wird beschrieben, wie den streaming-Server einrichten.

**Hinweis**  
Alle Computer, auf dem Windows Assessment Toolkit installiert ist als streaming-Server fungieren und bieten die Mediendateien, die über das Windows-Assessment-Toolkit für jeden anfordernden Client installiert wurden. Für diese Bewertung ist eine Arbeitslast eine MP4-Datei und eine entsprechende HTML-Datei, die die Bewertung zusammen als streaming Media verwendet. 720p.mp4 und 720p.html zusammen bilden beispielsweise eine 720p Arbeitslast. Gehen Sie folgendermaßen vor, um diese Arbeitslasten Media in Ihrem Szenario 2-Computer zur Bewertung zu verwenden.

 

**So richten Sie einen Server für die Bewertung Streaming Media-Leistung ein**

1.  Installieren Sie auf dem Remoteserver das Windows Assessment Toolkit. Anweisungen finden Sie unter [schrittweise Anleitung für Windows-Assessment-Konsole](windows-assessment-console-step-by-step-guide.md) oder [schrittweise Anleitung für Windows Assessment Services](windows-assessment-services-step-by-step-guide-was.md).

2.  Öffnen Sie ein Eingabeaufforderungsfenster.

3.  Je nach den Computertyp wechseln Sie zur Datei StreamingMediaAssessmentServer.exe:

    **Hinweis**  
    Die vorstehenden Pfade wird davon ausgegangen, dass Sie das Windows Assessment Toolkit in ihrem Standardspeicherort installiert haben.

     

    -   Geben Sie bei einem Computer mit X86 Folgendes aus:

        ``` syntax
        C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content Based Assessments\x86
        ```

    -   Geben Sie bei einem Computer mit X64 Folgendes aus:

        ``` syntax
        C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content Based Assessments\amd64
        ```

4.  Geben Sie an der Befehlszeile Folgendes aus:

    ``` syntax
    StreamingMediaAssessmentServer.exe -ContentPath <path_to_streaming_content>  [-PopulateCache <file_name_list>] [-Port <number>]
    ```

    In der folgenden Tabelle werden die Parameter in der vorstehenden Command-Line Text beschrieben.

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
    <td><p><em>ContentPath&lt;Path_to_streaming_content&gt;</em></p></td>
    <td><p>Geben Sie den Pfad, der enthält die Medien und die entsprechenden HTML-Seiten, die der Server stream wird. Standardmäßig ist dieser Pfad:</p>
    <pre class="syntax" space="preserve"><code>%PROGRAMFILES%\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content based Assessments\Content\Streaming Media Assessment</code></pre>
    <p>Sie können einen absoluten Pfad für die Medien und die entsprechenden HTML-Seiten angeben.</p></td>
    </tr>
    <tr class="even">
    <td><p><em>PopulateCache&lt;File_name_list&gt;</em></p></td>
    <td><p>Geben Sie die Dateinamen, die der Server zwischengespeichert werden in den Arbeitsspeicher. Listen Sie alle Dateien, durch Kommas getrennt. In diesem Beispiel enthält die Mediendateien, die standardmäßig die Bewertung verwendet:</p>
    <pre class="syntax" space="preserve"><code>-populatecache 360p.mp4,360p.html,480p.mp4,480p.html,720p.mp4,720p.html,1080p.mp4,1080p.html,1080p60.mp4,1080p60.html</code></pre>
    <p>Die Bewertung für diese Dateinamen im Pfad durchsucht, die <code>ContentPath</code> Einstellung angegeben wurde. Wenn die Dateien nicht vorhanden sind, die Bewertung protokolliert ein Ereignis <em>Datei fehlt</em> , aber die Bewertung wird weiterhin ausgeführt, den normalen Prozess mithilfe von Dateien, die im Pfad gefunden.</p></td>
    </tr>
    <tr class="odd">
    <td><p><em>Port&lt;Anzahl&gt;</em></p></td>
    <td><p>Geben Sie einen Port, wenn kein Port 80 wird den Standardwert verwendet werden soll. Der Standardport kann oder kann nicht auf dem Client angegeben werden. Wenn Sie eine andere Portnummer verwenden müssen, stellen Sie sicher, dass Sie es auf den Remoteserver und dem Client angeben.</p>
    <div class="alert">
    <strong>Wichtige</strong>  
    <p>Vor der Angabe welcher Port verwenden, stellen Sie sicher, dass Windows-Firewall Kommunikation nicht blockiert. Weitere Informationen finden Sie unter [Windows-Firewall von Anfang bis Ende](http://go.microsoft.com/fwlink/?LinkId=246551).</p>
    </div>
    <div>
     
    </div></td>
    </tr>
    </tbody>
    </table>

     

Die *PopulateCache* -Liste der zuvor aufgeführten Dateien ist die Standardgruppe von Dateien, die die Bewertung als Arbeitslasten verwendet wird. Der lokale Computer, auf dem Sie das Streaming Media Performance Assessment ausführen, fordert diese Dateien vom Remoteserver während der Bestandsaufnahme. Der Remoteserver speichert alle Dateien, dass der *PopulateCache* -Parameter angegeben wurde und diese auf dem lokalen Computer für die Messung der Leistung bietet.

## <a name="related-topics"></a>Verwandte Themen


[Streaming Media-Leistung](streaming-media-performance.md)

[Bewertung](assessments.md)

[Windows-Assessment-Konsole](windows-assessment-console.md)

 

 







