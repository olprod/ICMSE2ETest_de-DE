---
author: Justinha
Description: Windows-Setup-Protokolldateien und Ereignisprotokolle
ms.assetid: f3f32c6c-c1f9-4b85-ba0f-1e2a0b07c50f
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows-Setup-Protokolldateien und Ereignisprotokolle
ms.openlocfilehash: e0c24f990683c7a85412759b959ff3e48cba2e69
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-log-files-and-event-logs"></a>Windows-Setup-Protokolldateien und Ereignisprotokolle


Windows® Setup erstellt Protokolldateien für alle Aktionen, die während der Installation auftreten. Wenn Sie beim Installieren von Windows Probleme auftreten, finden Sie in die Protokolldateien, um die Installation zu behandeln.

Windows-Setup-Protokolldateien sind in den folgenden Verzeichnissen verfügbar:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Speicherort der Protokolldatei</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>$windows.~bt\Sources\Panther</p></td>
<td align="left"><p>Protokollspeicherort vor dem Setup kann auf das Laufwerk zugreifen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>$windows.~bt\Sources\Rollback</p></td>
<td align="left"><p>Protokollieren Sie Speicherort aus, wenn Setup im Fall eines schwerwiegenden Fehlers Rollback.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\Panther</p></td>
<td align="left"><p>Melden Sie sich den Speicherort der Setup-Aktionen nach der Datenträgerkonfiguration.</p></td>
</tr>
<tr class="even">
<td align="left"><p>%WINDIR%\Inf\Setupapi*.log</p></td>
<td align="left"><p>Plug & Play-Geräteinstallationen Anmeldung verwendet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\Memory.dmp</p></td>
<td align="left"><p>Speicherort der Speicherabbild über Fehler überprüft.</p></td>
</tr>
<tr class="even">
<td align="left"><p>%WINDIR%\Minidump\*.dmp</p></td>
<td align="left"><p>Speicherort der Protokolldateien Minidumps Fehler überprüft.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\System32\Sysprep\Panther</p></td>
<td align="left"><p>Speicherort der Sysprep-Protokolle.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idwindowssetupeventlogsspanspan-idwindowssetupeventlogsspanspan-idwindowssetupeventlogsspanwindows-setup-event-logs"></a><span id="Windows_Setup_Event_Logs"></span><span id="windows_setup_event_logs"></span><span id="WINDOWS_SETUP_EVENT_LOGS"></span>Setup Windows-Ereignisprotokollen


Windows-Setup bietet die Möglichkeit, überprüfen Sie die Windows-Setup-Leistung-Ereignisse im Windows-Ereignisprotokoll-Viewer. So können Sie die Aktionen leichter zu überprüfen, die beim Windows Setup und die Leistungsstatistiken für unterschiedliche Teile der Windows-Installation zu überprüfen. Sie können das Protokoll um nur relevante Elemente anzuzeigen, denen Sie interessiert sind, filtern. Das Windows-Setup-Leistung-Ereignisse werden in einer Protokolldatei mit dem Namen Namen, die in der %windir% verfügbar ist gespeichert\\Panther Directory aller Installationen. Zum Anzeigen der Protokolle müssen Sie verwenden der Ereignisanzeige Lieferumfang von Windows Media, die der Version des angepassten Abbilds entspricht, die Sie erstellen.

Zum Anzeigen der Protokolle auf einem Computer, die nicht in das entsprechende Kit enthalten ist, müssen Sie ein Skript im Stammverzeichnis des Mediums ausführen, die den Anbieter Event Trace for Windows (ETW) installiert. Geben Sie an der Befehlszeile Folgendes ein:

``` syntax
Cscript D:\sources\etwproviders\etwproviderinstall.vbs install D:\sources\etwproviders
```

wobei *D* der Laufwerkbuchstabe des Windows-DVD Mediums ist.

### <a name="span-idtoviewthewindowssetupeventlogsspanspan-idtoviewthewindowssetupeventlogsspanspan-idtoviewthewindowssetupeventlogsspanto-view-the-windows-setup-event-logs"></a><span id="To_view_the_Windows_Setup_event_logs"></span><span id="to_view_the_windows_setup_event_logs"></span><span id="TO_VIEW_THE_WINDOWS_SETUP_EVENT_LOGS"></span>So zeigen Sie die Ereignisprotokolle Windows Setup an

1.  Starten Sie die Ereignisanzeige, erweitern Sie den Knoten Windows-Protokolle, und klicken Sie dann auf **System**.

2.  Klicken Sie im **Aktionsbereich** klicken Sie auf **Gespeichertes Protokoll öffnen** , und suchen Sie die Datei Namen. Standardmäßig ist diese Datei in der %windir% verfügbar\\Panther Directory.

3.  Der Inhalt der Protokolldatei werden in der Ereignisanzeige angezeigt.

### <a name="span-idtoexportthelogtoafilespanspan-idtoexportthelogtoafilespanspan-idtoexportthelogtoafilespanto-export-the-log-to-a-file"></a><span id="To_Export_the_log_to_a_file"></span><span id="to_export_the_log_to_a_file"></span><span id="TO_EXPORT_THE_LOG_TO_A_FILE"></span>Das Protokoll in eine Datei exportieren

Verwenden Sie über die Befehlszeile die **Wevtutil** oder **Tracerpt** Befehle, um das Protokoll in eine XML- oder Text-Datei zu speichern. Informationen zur Verwendung dieser Tools finden Sie unter der Befehlszeilenhilfe. Die folgenden Befehle zeigen Beispiele dafür, wie Sie die Tools verwenden:

``` syntax
Wevtutil qe /lf C:\windows\panther\setup.etl 
```

\endash oder \endash

``` syntax
Tracerpt /l C:\windows\panther\setup.etl
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows Setup-Befehlszeilenoptionen](windows-setup-command-line-options.md)

[Windows-Setup-Status](windows-setup-states.md)

[Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

 

 






