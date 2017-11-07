---
title: Command-Line Options ResultsUtil
description: Command-Line Options ResultsUtil
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7cf8c26e-50b5-4634-9e60-80ff7d69c22d
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ca497a3c82481e2f20c1c3bc1e81bbd9dec0f4f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resultsutil-command-line-options"></a>Command-Line Options ResultsUtil


Der Befehl ResultsUtil wird verwendet, wenn Assessment Ergebnisse in einer SQL Server-Datenbank gespeichert werden soll. Standardmäßig werden die Ergebnisse auf dem Server Windows Assessment-Services in einem Ergebnisspeicher gespeichert. Der Befehl ResultsUtil wird von der Freigabe Ergebnisse so konfigurieren Sie die Windows-Assessment-Services-Server (oder ein unabhängiger Server) zum Speichern der Auftragsergebnisse verwendet, in einer SQL-Datenbank. Es wird auch verwendet, um vorhandene Ergebnisse in einer SQL-Datenbank zu importieren. Nach der Installation von Windows Assessment Services auf einem Server verwenden Sie die Befehle ResultsUtil die Datenbank auf einer SQL Server-Instanz initialisieren, bevor Sie einzelne Ergebnisse importieren oder Konfigurieren von Windows Assessment Services, um Ergebnisse an die Datenbank automatisch buchen.

**Warnung**  
Ergebnisse, die in einer SQL Server-Datenbank gespeichert sind die Assessment Plattform Darstellungsschicht nicht einschließen und nicht in der Windows-Assessment-Services - Client (Windows ASC) angezeigt werden. Eine benutzerdefinierte berichterstellungslösung ist erforderlich, um die Ergebnisse anzuzeigen.

 

## <a name="remarks"></a>Hinweise


Windows 8.1 ab, können Sie jetzt Batch importieren eine Gruppe von Ergebnissen in die Datenbank und den Batch aus der Datenbank löschen. Der Tracking-Mechanismus verwendet, um die Ergebnisse in einem Batch Import-Tags ist die Batch-ID. Importieren von Batch (/ B) können Sie auf einen Ordner mit einem Satz von Ergebnisse zeigen und mit einem einzigen Befehl zu importieren. Die Ausgabe dieses Befehls bietet eine Batch-ID, die später verwendet werden kann, Löschen des Stapels Auftreten eines Fehlers importieren – befindet sich ein Tippfehler in die Metadaten, zum Beispiel.

**Hinweis**  
Die Option /tags wird nicht mehr unterstützt.

 

**Hinweis**  
Wenn Sie eine Datenbank-Verbindungszeichenfolge, mit der Option/DB oder beim Speichern in ResultsUtil.exe.config mit der Option /FileSave verwenden, müssen Sie als die Anfangskatalog **RelaxResults** angeben. Siehe Tabelle der Optionen unter Beispiele.

 

### <a name="metadata"></a>Metadaten

Metadaten ist nützlich, wenn führt zu vergleichen oder Berichte in einer Auflistung von Ergebnissen. Es gibt drei Arten von Metadaten, die verwendet werden können, um Daten in die Datenbank importiert auszurichten. Finden Sie die entsprechenden Einträge in der vollständigen folgenden Beispiele für die Optionstabelle aus.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Typ</th>
<th>Option</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Project</strong></p></td>
<td><p>/ p</p></td>
<td><p>Eine Gruppierung, die eine Reihe von Computern darstellt.</p></td>
</tr>
<tr class="even">
<td><p><strong>Testdurchlauf</strong></p></td>
<td><p>/ t</p></td>
<td><p>Eine Gruppe von Ergebnissen, die durch einen einzelnen Testdurchlauf oder auf einen bestimmten Build erstellt wurden</p></td>
</tr>
<tr class="odd">
<td><p><strong>Führen Sie Tag</strong></p></td>
<td><p>/RT</p></td>
<td><p>Die Konfiguration, die während der Ausführung des einen Testdurchlauf verwendet wird. Beispielsweise können Sie vor und nach einer Aktualisierung der Treiber die Leistung gemessen ausführen</p></td>
</tr>
</tbody>
</table>

 

## <a name="system-requirements"></a>Systemanforderungen


Im folgenden sind die Systemanforderungen für den ResultsUtil-Befehl ausführen:

-   Windows-Assessment-Services

-   Windows Server 2008 R2, WindowsServer 2012 oder Windows Server 2012 R2

-   Eine vollständige Version von SQL Server 2008 R2 oder höher

## <a name="configuration-overview"></a>Übersicht über die Konfiguration


ResultsUtil verwendet eine Konfigurationsdatei, die im gleichen Verzeichnis befindet wie die ausführbare Datei gespeichert ist. In den folgenden Abschnitten werden die einzelnen Konfigurationsoptionen beschrieben. Abschnitte der Konfigurationsdatei, die unten nicht aufgeführt sind sind spezifisch für SQLServer und sollte nur vom Administrator erfahrene bearbeitet werden.

## <a name="resultsutilexe-command-line-options"></a>Command-Line Options ResultsUtil.exe


Verwenden Sie die folgende Syntax, um die Datenbank zu initialisieren:

**ResultsUtil /InitializeDatabase \[/DB &lt;Datenbank-Verbindungszeichenfolge&gt; \] \[/User &lt;Datenbankbenutzername&gt; \] \[/FileSave\]**

Verwenden Sie die folgende Syntax, um Ergebnisse zu importieren:

**ResultsUtil.exe/i \[/s &lt;Dateipfad&gt; \] \[/b &lt;Ordnerpfad&gt; \] \[/a\] \[/DB &lt;Datenbank-Verbindungszeichenfolge&gt; \] \[/User &lt;Datenbankbenutzername&gt; \] \[/p &lt;Projektnamen&gt; \] \[/t &lt;Durchlauf Testname&gt; \] \[/rt &lt;Tag ausführen&gt; \] \[/tags &lt;benutzerdefinierte Tags&gt;\]**

Um einen Batch der Ergebnisse zu löschen, die in die Datenbank importiert wurden, verwenden Sie folgende Syntax:

**ResultsUtil/d /BID &lt;führen Stapel ID&gt; \[DB &lt;Datenbank-Verbindungszeichenfolge&gt; \] \[/User &lt;Datenbankbenutzername&gt;\]**

Die folgende Tabelle enthält eine Beschreibung des wie jede Option verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

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
<td><p>/ InitializeDatabase</p></td>
<td><p>Installiert die Ergebnisdatenbank in der angegebenen Instanz von SQL Server.</p>
<p>Verbindungszeichenfolgen können zum Konfigurieren von Verbindungen mit der Datenbank verwendet werden. Wenn keine Befehlszeilenoptionen angegeben werden, verwendet den Befehl /InitializeDatabase, was in der Konfigurationsdatei ist.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die beiden Konfigurationen in der Standarddatei werden nicht verwendet und können entfernt werden.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>ResultsUtil /InitializeDatabase/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName /filesave</strong></p></td>
</tr>
<tr class="even">
<td><p>/ ImportResults</p>
<p>/ I</p></td>
<td><p>Importiert die angegebene Ergebnis-Datei in der Datenbank.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName/Project MyProject /testpass Milestone1 /runtag Run1 /tags M1Results</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ ConfigureWASserver</p>
<p>/ C</p></td>
<td><p>Konfiguriert die angegebene Instanz von Windows Assessment Services zum Speichern der Ergebnisse an die angegebene Ergebnis-Datenbank.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ConfigureWASserver/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName /WasServer Http://WASserver:8000/entspannen/Service</strong></p></td>
</tr>
<tr class="even">
<td><p>/ Eingabedatei <em> &lt;Dateiname&gt;</em></p>
<p>/ S</p></td>
<td><p>Identifiziert eine Datei mit den Suchergebnissen in der Datenbank importiert werden sollen. Der vollständige Pfad zu der Datei mit den Suchergebnissen muss angegeben werden.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ B</p></td>
<td><p>BULK Import führt Dateien aus einem Ordner. Batch-ID kann später verwendet werden, diese Daten aus der Datenbank zu löschen.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults/b C:\WAS\Results\/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName/Project MyProject /testpass Milestone1 /runtag Run1 /tags M1Results</strong></p></td>
</tr>
<tr class="even">
<td><p>/ DB <em> &lt;Database_connection_string&gt;</em></p></td>
<td><p>Eine Verbindungszeichenfolge, die die Instanz von SQL Server und die Datenbank erstellt werden soll.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /InitializeDatabase/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName /filesave</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ Benutzer <em> &lt;Benutzername&gt;</em></p></td>
<td><p>Ein Benutzername für die SQL Server-Verbindung.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName</strong></p></td>
</tr>
<tr class="even">
<td><p>/ Project <em> &lt;Projektname&gt;</em></p>
<p>/ P</p></td>
<td><p>Ordnet einen Projektnamen mit den zu importierenden Daten oder eine bereits vorhandene überschrieben. Assessment Ergebnisse importiert aus einem Auftrag, der in der Windows-Assessment-Konsole auf einem lokalen Computer ausgeführt wurde, ist der Projektname nicht vorhanden. Wenn die Ergebnisse aus einem Auftrag, die in einer laborumgebung ausgeführt wurde, die Windows Assessment Services verwendet generiert wurden, ist der Projektname bereits vorhanden.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/Project Project1</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ TestPass <em> &lt;Test_pass_name&gt;</em></p>
<p>/ T</p></td>
<td><p>Erstellt ein Test Durchlauf Metadatentag oder überschreibt bereits vorhanden. Die Test Durchlauf Metadaten können Sie Ergebnisse für einen bestimmten Meilenstein "oder" Test-Zyklus organisieren.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/Project Project1 /testpass Milestone1</strong></p></td>
</tr>
<tr class="even">
<td><p>/ RunTag <em> &lt;Run_tag_name&gt;</em></p>
<p>/RT</p></td>
<td><p>Erstellt Metadaten ausführen Tag oder eine bereits vorhandene überschrieben. Führen Sie Tag Metadaten hilft Geben Sie an eine bestimmten ausführen Auftragsinstanz bei der Suche nach Ergebnisse.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/Project MyProject /testpass Milestone1 /runtag Run1</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ BIETEN &lt;Result_batch_ID&gt;</p></td>
<td><p>Gibt die ID Batch der Ergebnisse, den, die Sie löschen möchten.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil/d /BID &lt;führen Batch-ID&gt;</strong></p></td>
</tr>
<tr class="even">
<td><p>/-Archiv</p>
<p>/ A</p></td>
<td><p>Archivieren Sie Ergebnisse vor dem Importieren.</p>
<p>Der Archivpfad wird angegeben, mithilfe der <code>archivePath</code> Knoten in der Konfigurationsdatei. Sie müssen den Pfad zum Archivieren von Dateien konfigurieren.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName/Project MyProject /testpass Milestone1 /runtag Run1 /tags M1Results/Archivierung</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ D</p></td>
<td><p>Löschen eines Batches von Ergebnissen in die Datenbank importiert.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil/d /BID &lt;führen Batch-ID&gt;</strong></p></td>
</tr>
<tr class="even">
<td><p>/ DateiSpeichern</p></td>
<td><p>Speichert die Datenbank-Konfigurationsdatei resultsutil.exe.config, an den gleichen Speicherort wie die ResultsUtil an. Die Konfigurationsdatei für die Datenbank wird mit die Datenbank Verbindungen Zeichenfolge und den Namen vorausgefüllt, damit Sie nicht jedes Mal eingeben, dass Sie Ergebnisse importieren.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Es gibt nur eine Datenbankdatei Konfiguration. Wenn Sie mehrere Ergebnisse Datenbanken verfügen Vorrang die Befehlszeilenoptionen der Konfigurationsdatei.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>ResultsUtil /InitializeDatabase/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName /filesave</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ Quiet</p></td>
<td><p>Statusnachrichten unterdrückt.</p>
<p>Beispiel:</p>
<p><strong>ResultsUtil /ConfigureWASserver/DB &quot;Data Source = Localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; Integrated Security = True&quot; /User MyName /WasServer Http://MyServer:8000/entspannen/Service/quiet</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

 

 







