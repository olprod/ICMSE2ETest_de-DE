---
author: Justinha
Description: Problembehandlung von Bereitstellung und Protokolldateien
ms.assetid: 6dcada17-852e-4a2a-bc22-ebf3504b9ccc
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellung Problembehandlung und Protokolldateien
ms.openlocfilehash: 4cc710f3343b3bbfe7a9936f46e2c2f7a0b5a847
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deployment-troubleshooting-and-log-files"></a>Bereitstellung Problembehandlung und Protokolldateien


Der folgende Abschnitt beschreibt die Beziehung zwischen häufige Szenarien für die Bereitstellung und die zugehörigen Protokolldateien. Windows®-Bereitstellung ist eine anpassbare Prozess, der das Potenzial für viele Fehlerquellen hat. Identifizieren von bestimmten Zeitpunkt des Fehlers aufgetreten ist, beginnt mit Grundlegendes zur Funktionsweise der zugrunde liegenden Technologies.

## <a name="span-idwindowssetupscenariospanspan-idwindowssetupscenariospanspan-idwindowssetupscenariospanwindows-setup-scenario"></a><span id="Windows_Setup_Scenario"></span><span id="windows_setup_scenario"></span><span id="WINDOWS_SETUP_SCENARIO"></span>Windows-Setup-Szenario


In diesem Szenario beginnt mit Abschluss der Installation von Windows auf einem neuen Computer, damit Sie auf dem Desktop eingehen. Dieses Szenario ist am häufigsten verwendeten, wenn Sie ein Bild Verweis erstellen. Dieser Prozess ist auch bekannt als der *erste Benutzer auftreten*.

Wie in der folgenden Abbildung gezeigt, wird der Schlüssel zum Beheben von Fehlern, wo Sie in den Installationsvorgang befinden und wenn ein Fehler auftritt, identifizieren. Da Sie eine neue Installation erstellen, die Festplatte ist nicht zunächst verfügbar, damit Windows Setup in den Arbeitsspeicher, insbesondere in einer Windows PE-Sitzung Protokolle schreibt (X:\\Windows). Nachdem die Festplatte formatiert ist, wird Setup fortgesetzt anmelden direkt an die neue Festplatte (C:\\Windows). Während der Sitzung Windows PE erstellte Protokolldateien werden temporäre.

![Windows Setup Log-Dateien](images/dep-win8-l-setup-failure-log.jpg)

Tritt ein Fehler im Windows-Setup die Einträge in der Datei Setuperr.log zuerst, klicken Sie dann die Setupact.log Datei zweiten und klicken Sie dann andere Protokolldateien überprüfen Sie je nach Bedarf.

### <a name="span-idwindowssetup-relatedlogfilesspanspan-idwindowssetup-relatedlogfilesspanspan-idwindowssetup-relatedlogfilesspanwindows-setup-related-log-files"></a><span id="Windows_Setup-Related_Log_Files"></span><span id="windows_setup-related_log_files"></span><span id="WINDOWS_SETUP-RELATED_LOG_FILES"></span>Windows-Setup-bezogene Protokolldateien

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Protokolldatei</th>
<th align="left">Beschreibung</th>
<th align="left">Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Setupact.log</p></td>
<td align="left"><p>Primäre Protokolldatei für die meisten Fehler, die während der Installation von Windows auftreten. Es gibt mehrere Instanzen der Datei Setupact.log, je nachdem, was in den Installationsvorgang zu verweisen, die der Fehler auftritt. Es ist wichtig wissen, welche Version der Datei Setupact.log betrachten, basierend auf der Phase, in der Sie sich befinden.</p></td>
<td align="left"><p><strong>Setup (specialize):</strong> X:\Windows\panther</p>
<p><strong>Setup (OOBE), Anmeldebenutzeroberfläche, OEM ersten Textlauf:</strong>%windir%\panther</p>
<p><strong>Out-Of-Box-Experience (OOBE):</strong> %windir%\panther\unattendGC</p></td>
</tr>
<tr class="even">
<td align="left"><p>Setuperr.log</p></td>
<td align="left"><p>Allgemeine Liste der Fehler während der Phase <strong>specialize</strong> der Installation. Die Datei Setuperr.log stellt keine bestimmte Details bereit.</p></td>
<td align="left"><p><strong>Setup (specialize):</strong> %windir%\panther</p>
<p><strong>Setup (specialize):</strong> %windir%\panther</p>
<p><strong>Setup (OOBE), Anmeldebenutzeroberfläche, OEM ersten Textlauf:</strong> %windir%\panther</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Setupapi.offline.log</p></td>
<td align="left"><p>Treiber Fehler während der Phase der Komponente Spezialisierung Unterwebsites der Setup <strong>specialize</strong> Phase.</p></td>
<td align="left"><p>%windir%\Inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>Cbs_unattend.log</p></td>
<td align="left"><p>Wartung Unattended-Setup-Fehler.</p></td>
<td align="left"><p>%WINDIR%\Panther</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Setupapi.dev.log</p></td>
<td align="left"><p>Treiber Fehlern während der Phase der <strong>Oobe</strong> von Setup.</p></td>
<td align="left"><p>%windir%\Inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sessions.Xml</p></td>
<td align="left"><p>Eine XML-basierte Transaktionsprotokolldatei alle nachverfolgt werden, die Wartung Aktivität, basierend auf Id für eine Sitzung, Client, Status, Aufgaben und Aktionen. Falls erforderlich, wird die Datei Sessions.log Weitere Informationen zu den DISM.log und CBS.log zeigen.</p></td>
<td align="left"><p>%windir%\servicing\sessions</p></td>
</tr>
<tr class="odd">
<td align="left"><p>CBS.log</p></td>
<td align="left"><p>Wartung Protokolldatei, die bietet ausführliche Informationen zu offline zum Warten von Fehlern.</p></td>
<td align="left"><p>%WINDIR%\Panther</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idofflineservicingscenariospanspan-idofflineservicingscenariospanspan-idofflineservicingscenariospanoffline-servicing-scenario"></a><span id="Offline_Servicing_Scenario"></span><span id="offline_servicing_scenario"></span><span id="OFFLINE_SERVICING_SCENARIO"></span>– Wartung offline Szenario


In diesem Szenario umfasst das Hinzufügen und Entfernen von Updates, Treiber und Language Packs und andere Einstellungen konfigurieren, ohne Starten von Windows. Eine offline ist eine effiziente Möglichkeit zum Verwalten von vorhandenen Bilder, die auf einem Server gespeichert werden, da es Neuerstellen aktualisierte Bilder überflüssig. Führen Sie offline zum Warten auf ein Bild, das bereitgestellt oder auf einem Laufwerk oder Verzeichnis angewendet wird.

![– Wartung offline Fehleranalyse](images/adk-win8-l-di-offlineservicingfailureanalysis.jpg)

Das Tool Deployment Image Servicing and Management (DISM) ist das wichtigste Tool für alle Vorgänge auf offline – Wartung. DISM über eine Befehlszeile aus Windows PE oder einem ausgeführten Windows-Betriebssystem ausgeführt wird. Wenn ein Fehler auftritt, beim Ausführen eines Befehls DISM, das Tool sofortige eine Antwort bereitstellen, und melden Sie sich das Problem in der Datei DISM.log. Die Datei Session.xml ist eine Transaktionsprotokoll-Datei, die alle zum Warten Aktivitäten auf dem Betriebssystem erfasst. Die Datei Session.xml kann in Verbindung mit der Datei DISM.log Punkt der Fehler und die erforderliche Wartung Aktivität bestimmen verwendet werden.

Tritt ein Fehler in eine offline, betrachten Sie die Datei DISM.log zunächst für bestimmte Fehler. Wenn die Datei DISM.log keine Fehler enthält, überprüfen Sie das Protokoll Sessions.xml Datei und anschließend die Datei "CBS.log".

### <a name="span-idofflineservicingrelatedlogfilesspanspan-idofflineservicingrelatedlogfilesspanspan-idofflineservicingrelatedlogfilesspanoffline-servicing-related-log-files"></a><span id="Offline_Servicing_Related_Log_Files"></span><span id="offline_servicing_related_log_files"></span><span id="OFFLINE_SERVICING_RELATED_LOG_FILES"></span>– Wartung offline zugehörigen Protokolldateien

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Protokolldatei</th>
<th align="left">Beschreibung</th>
<th align="left">Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DISM.log</p></td>
<td align="left"><p>Primäre Protokolldatei für alle mithilfe von DISM offline Aktionen.</p></td>
<td align="left"><p>%windir%\logs\dism</p>
<p>Sie können auch an einem anderen Speicherort die Protokolldatei DISM erstellen, mit der <strong>Option/LogPath</strong> . Die Ebene der Daten in die Protokolldatei geschrieben kann auch mithilfe der Option <strong>/LogLevel</strong> gesteuert werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sessions.Xml</p></td>
<td align="left"><p>Ein XML-basierte Transaktionsprotokoll, das alle Aktivitäten zum Warten, basierend auf dem Client, Id für eine Sitzung, Status, Aufgaben und Aktionen nachverfolgt werden. Falls erforderlich, wird die Datei Sessions.log Weitere Informationen zu den DISM.log und CBS.log zeigen.</p></td>
<td align="left"><p>%windir%\servicing\sessions</p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen zu offline – Wartung finden Sie unter [Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md).

## <a name="span-idonlineservicingscenariospanspan-idonlineservicingscenariospanspan-idonlineservicingscenariospanonline-servicing-scenario"></a><span id="Online_Servicing_Scenario"></span><span id="online_servicing_scenario"></span><span id="ONLINE_SERVICING_SCENARIO"></span>Online-Szenario – Wartung


In diesem Szenario bedient ein Betriebssystem ausgeführt wird. In diesem Szenario umfasst das Starten des Computers zum Überwachungsmodus Treiber, Anwendungen und andere Pakete hinzuzufügen. Online – Wartung ist ideal für Treiber, wenn die Treiberpakete gemeinsame Installer oder Anwendung Abhängigkeiten haben. Es ist auch effizient bei haben die meisten-Pakete für die Wartung Installer, die Updates in der MSI-Datei oder KB.exe Dateiformate sind oder die Anwendungen auf Windows installierte Dienste und Technologien (wie die .NET Framework oder die vollständige Plug & Play-Unterstützung basieren).

![Fehler bei Analyse Wartung Online](images/adk-win8-l-di-onlineservicingfailureanalysis.jpg)

Wie Wartung offline, werden alle Protokollierung in den Dateien DISM.log CBS.log und Sessions.xml erfasst. Wenn ein Fehler auftritt, beim Ausführen eines Befehls DISM, wird das Tool bieten sofort eine Antwort als auch das Problem in der Datei DISM.log melden. Session.xml-Datei ist eine Transaktionsprotokolldatei, die alle zum Warten Aktivitäten auf dem Betriebssystem erfasst. Die Datei Session.xml in Verbindung mit der Datei DISM.log verwendbar Punkt der Fehler und die erforderlichen Service-Aktivitäten zu bestimmen

Tritt ein Fehler in eine offline, sehen Sie sich die Datei DISM.log für bestimmte Fehler. Wenn die Datei DISM.log keine Fehler enthält, überprüfen Sie die Protokolldatei Sessions.xml und dann die CBS.log-Datei aus.

### <a name="span-idonlineservicing-relatedlogfilesspanspan-idonlineservicing-relatedlogfilesspanspan-idonlineservicing-relatedlogfilesspanonline-servicing-related-log-files"></a><span id="Online_Servicing-Related_Log_Files"></span><span id="online_servicing-related_log_files"></span><span id="ONLINE_SERVICING-RELATED_LOG_FILES"></span>Online – Wartung-bezogene Protokolldateien.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Protokolldatei</th>
<th align="left">Beschreibung</th>
<th align="left">Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DISM.log</p></td>
<td align="left"><p>Primäre Protokolldatei für alle mithilfe von DISM online Aktionen. Bei Bedarf zeigen DISM.log auf CBS.log Einzelheiten.</p></td>
<td align="left"><p>%windir%\logs\dism</p>
<p>Sie können auch Punkt DISM Protokolldatei an einem anderen Speicherort mit der Befehlszeilenoption/LogPath. Die Protokolldaten können auch mithilfe der Option /LogLevel Befehl gesteuert werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>CBS.log</p></td>
<td align="left"><p>Sekundäre Protokolldatei, die weitere Details zu einer online Wartung Fehler bereitstellt. DISM.log verweist CBS.log Einzelheiten.</p></td>
<td align="left"><p>%windir%\Logs\CBS</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sessions.Xml</p></td>
<td align="left"><p>Eine Xml basierte Transaktionsprotokoll an, die alle zum Warten Aktivitäten basierend auf Id für eine Sitzung, Client, Status, Aufgaben und Aktionen nachverfolgt werden. Falls erforderlich, zeigen Sessions.log auf DISM.log und CBS.log für weitere Details.</p></td>
<td align="left"><p>%windir%\servicing\sessions</p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen zu offline – Wartung finden Sie unter [Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md).

 

 





