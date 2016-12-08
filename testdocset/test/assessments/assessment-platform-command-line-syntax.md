---
title: Assessment Plattform Befehlszeilensyntax
description: Assessment Plattform Befehlszeilensyntax
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 34286b79-1867-4d0d-8b65-6a0c6a7e5df8
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 6c74f6ae01ced36cdb45c952ae784f8582a00478
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="assessment-platform-command-line-syntax"></a>Assessment Plattform Befehlszeilensyntax


**AXE.exe** ist ein Befehlszeilentool, das zusammen mit dem Windows Assessment Toolkit installiert wird. In diesem Satz von Befehlszeilenoptionen können Sie Aufträge aus einem Skript automatisieren und Ressource: Einsatz zu minimieren. Ein Auftrag ist eine oder mehrere Analysen gleichzeitig auf einem Computer ausgeführt. Die Befehlszeilenoptionen können Sie einen Auftrag zum Verfassen. Sie sollten erstellen ändern und einen Auftrag mithilfe der Windows-Assessment-Verwaltungskonsole zu speichern. Aufträge werden standardmäßig auf "UserProfile" % gespeichert\\Dokumente\\Windows Assessment-Konsole\\Aufträge Ordner.

Standardmäßig wird auf AXE.exe installiert:

ProgramFiles%\\Windows Kits\\10\\ Assessment and Deployment Kit\\Windows Assessment Toolkit\\*&lt;Architektur&gt; *

Wobei * &lt;Architektur&gt; * X86 oder amd64 ist.

## <a name="command-line-options"></a>Befehlszeilenoptionen


Die grundlegende Syntax für die Verwendung der Assessment-Plattform, über die Befehlszeile ist:

``` syntax
AXE.exe jobfile [AXE_options]
```

In der folgenden Tabelle enthält eine Beschreibung für die Verwendung jeder Option. Diese Optionen nicht beachtet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Hilfe</strong> oder <strong>/?</strong></p></td>
<td><p>Zeigt Informationen zu verfügbaren <strong>AXE.exe</strong> Command-Line Options.</p></td>
</tr>
<tr class="even">
<td><p><strong>JobFile</strong></p></td>
<td><p>Gibt die Job-Datei, die Sie ausführen möchten.</p>
<p>Der Pfad der Auftragsdatei kann ein relativer Pfad sein. Kein Pfad ist erforderlich, wenn der Auftrag im Verzeichnis, die Sie <strong>AXE.exe</strong> aus arbeiten ist. In der Standardeinstellung beim Erstellen eines Auftrags in der Windows-Assessment-Konsole, wird im Ordner Assessment Console\Jobs %USERPROFILE%\Documents\Windows gespeichert.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Diese Option ist erforderlich, wenn keine anderen Parameter, der eine Aktion ausführt angegeben ist.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\MyJobs\Job1.jobx</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ Timeout</strong><em>&lt;Sekunden&gt;</em></p></td>
<td><p>Gibt die Zeitspanne in Sekunden, die der Auftrag gewartet, ein anderer Auftrag bis wird auf Fertig stellen, bevor sie mit einem Fehler beendet wird. Der Standardwert ist 0 (null), was bedeutet, dass der Auftrag sofort beendet wird, wenn ein anderer Auftrag bereits ausgeführt wird. Dies ist ein optionaler Parameter.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /Timeout 30</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ NoPublish</strong></p></td>
<td><p>Gibt an, nicht die Datei mit den Suchergebnissen auf den Speicherort zu veröffentlichen, die in der Job-Datei angegeben wird. Wenn Sie diese Option verwenden, werden die Ergebnisse in den Standardspeicherort, % LOCALAPPDATA%\Microsoft\Axe\Results gespeichert.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /NoPublish</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ PublishPath</strong><em>&lt;Directory&gt;</em></p></td>
<td><p>Gibt den Pfad eines Ordners, der die Datei mit den Suchergebnissen zu veröffentlichen. Dies überschreibt den Pfad Publikation &lt;ResultsPublishPath&gt;, die in der Job-Datei angegeben wird. Dieser Parameter wird ignoriert, wenn es mit <strong>/NoPublish</strong>kombiniert ist.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /PublishPath C:\Assessments\myResults</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ RemoveRestart</strong></p></td>
<td><p>Gibt an, dass alle vorhandenen ausstehenden Job-Neustart Aufgabe sollte entfernt werden.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Option <strong>/JobFile</strong> ist nicht erforderlich, wenn Sie diese Option verwenden.</p>
</div>
<div>
 
</div>
<p>Wenn Sie einen Auftrag ausführen, erstellt das Assessment eine Aufgabe aus, um den Auftrag neu gestartet, wenn ein Systemfehler auftritt, wie ein Verlust der Power vorhanden ist. Wenn Sie diese Option verwenden, wird die Aufgabe aus dem Taskplaner entfernt. Wenn kein Auftrag-Neustart-Vorgang aussteht, wird die Bewertung zu informieren, wenn die Aufgabe nicht vorhanden ist ein Fehler zurückgegeben.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE /RemoveRestart</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ NoWarnings</strong></p></td>
<td><p>Unterdrückt die Warnung Nachrichten. Dies ist ein optionaler Parameter.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /NoWarnings</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ Anhalten</strong></p></td>
<td><p>Hält AXE.exe nach Abschluss des Auftrags warten Sie, eine Taste zu drücken. Sie sehen dann alle Fehler oder andere Informationen in der Konsole vor dem AXE.exe beendet und die Konsole geschlossen wird.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /Pause</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ JobParameter Param =</strong><em>&lt;Wert&gt;</em></p></td>
<td><p>Gibt einen Wert, um einen Auftragsparameter überschreiben möchten, der möglicherweise im Auftrag Manifest vorhanden ist. Dies ist ein optionaler Parameter. Es können bis zu 100 Mal Sie mehrere Job-Parameter angeben. Wenn doppelte Auftrag Parameternamen angezeigt werden, verwendet die Bewertung als letzte Datenreihe. Die Option <strong>/PublishPath</strong> hat Vorrang vor der Einstellung der &lt;ResultsPublishPath&gt; Auftragsparameter mit dieser Option.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /JobParameter iterations=1</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ DisplayLog</strong><em>&lt;Path_to_AXE_ETL_log_file&gt;</em></p></td>
<td><p>Zeigt den Inhalt der Event Trace Log (ETL) Dateien, die <strong>AXE.exe</strong> für die Anmeldung verwendet. Geben Sie den Pfad der <strong>AXE.exe</strong> ETL-Dateien ein. Der Speicherort der Protokolldateien wird in der Konsole angezeigt, wenn ein Auftrag ausgeführt wird. Der Dateiname kann Platzhalterzeichen enthalten.</p>
<p>Der Standardspeicherort der Protokolldatei ist %LOCALAPPDATA%\Microsoft\Axe\Logs\<em>&lt;GUID&gt;</em>, wobei <em> &lt;GUID&gt; </em> ist die GUID, die für jeden neuen Auftrag zufällig generiert wird. Der Auftrag Ergebnisdatei der &lt;SessionLogFiles&gt; Knoten enthält auch den vollständigen Speicherort. Dieser Knoten gibt alle die Protokolldateien.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Alle ETL-Dateien werden automatisch in einer einzigen Datei AxeLog.txt konvertiert, die im Ergebnisverzeichnis gespeichert wird. Sie können diese Datei mit dem Editor öffnen.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>AXE /DisplayLog &lt;path_to_file&gt;</code></pre></td>
</tr>
</tbody>
</table>

 

**Vorteile:**

-   Ausführen eines Auftrags in der Befehlszeile weniger Ressourcen verwendet und wirkt sich weniger auf Leistungsmetrik.

-   Command-Line Options können Sie um einen Auftrag zu automatisieren.

-   Command-Line Options Geben Sie zusätzliche Parameter, die nicht in der Windows-Assessment-Konsole verfügbar sind.

**Einschränkungen:**

-   Der Auftrag, den Sie ausführen kann nicht eine der vordefinierten Aufträge oder eines der einzelnen Bewertungsfragen, die das Windows Assessment Toolkit bietet sein.

-   Sie können nicht erstellen oder ändern einen Auftrag mithilfe von **AXE.exe**. Sie müssen die Windows-Assessment-Konsole verwenden.

## <a name="related-topics"></a>Verwandte Themen


[Windows Assessment-Konsole (Übersicht)](windows-assessment-console-overview.md)

 

 







