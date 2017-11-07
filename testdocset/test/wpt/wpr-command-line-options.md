---
title: Command-Line Options WPR
description: Command-Line Options WPR
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3c69c8df-6ce3-49a0-b17f-e2b60016b72a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a7f90d462ad753a23e1d69b2ce847eaf0fd1cb56
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpr-command-line-options"></a>Command-Line Options WPR


Windows Performance Aufzeichnung (WPR) bietet eine einfache Befehlszeilenoberfläche. Die gesamte Komplexität des WPR ist in die Aufzeichnung Profile eingebettet.

WPR erfordert Windows 7 oder höhere Version des Betriebssystems.

**Syntax:**

**wpr** {**-profiles** \[*&lt;path&gt;* \[ … \] \]  |  **-Starten** * &lt;Argumente&gt;* | **-Beenden** * &lt;Argumente&gt;* | **-Abbrechen** | **-Status** * &lt;Argumente&gt;* | **-Protokoll** * &lt;Argument&gt;* | **- Purgecache** | **-Hilfe** * &lt;Argumente&gt;* | **- Profiledetails** | **- Disablepagingexecutive**}

Die folgenden Abschnitte beschreiben die Befehlszeilenoptionen:

-   [Profile](#profiles)

-   [Starten](#start)

-   [Beenden](#stop)

-   [Abbrechen](#cancel)

-   [Status](#status)

-   [Profiledetails](#prodet)

-   [Anbieter](#prodet)

-   [DisablePagingExecutive](#disablepagingexec)

-   [Melden Sie sich](#log)

-   [PURGECACHE](#purge)

-   [Hinweise](#rem)

**Hinweis**  
Wenn Sie über die Befehlszeile WPR starten, während einer anderen Anwendung (wie Xperf oder eine Anwendung, die NT Kernel-Protokollierung, wie Logman oder PerfTrace verwendet) aufzeichnet, WPR Aufzeichnung starten und folgender Fehler zurückgegeben:

`The event collector was already running.`

In diesem Fall müssen Sie den anderen Aufzeichnung bevor Sie eine neue Aufzeichnung können mithilfe von WPR Abbrechen.

 

## <a name="profiles"></a>Profile


Verwenden Sie diese Option, um die Profile WPR aufzulisten, die Aufzeichnung verwendet.

**Syntax:**

**wpr** **-Profile** \[*&lt;path&gt;*\]

In der folgenden Tabelle sind die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;Pfad&gt;</em></p></td>
<td><p>Um herauszufinden, integrierten Profile, ausgelassen werden Sie, das Argument.</p>
<p>Um die Profile aufzulisten, die in einer Benutzerprofildienst-Definitionsdatei definiert sind, geben Sie den Pfad und Namen der Datei.</p>
<p>Beispiel:</p>
<p><code>wpr -profiles</code></p>
<p><code>wpr -profiles “c:\Users\User1\Documents\WPR Files\Custom Profiles\CustomProfile1.wprp”</code></p></td>
</tr>
</tbody>
</table>

 

## <a name="start"></a>Start


Verwenden Sie diese Option auf eine Aufzeichnung starten mithilfe von ein oder mehrere Profile.

**Syntax:**

**Wpr-starten** * &lt;Profil&gt; * \] ** \[-starten** &lt; *Profilen* &gt; \] \[ **- Filemode** \] \[ **- Recordtempto** &lt; *temp Ordnerpfad*&gt;\]\[**- Onoffscenario** &lt; */Ausschalten Übergangstyp* &gt; \] \[ **- Onoffresultspath** &lt; *Pfad, in dem die Ablaufverfolgungsdateien gespeichert werden*&gt;\]\[**- Onoffproblemdescription** &lt; *Beschreibung des Szenarios* &gt; \] \[ **- Numiterations** &lt; *Anzahl von Iterationen für Tracing/ausschalten*&gt;\]

In der folgenden Tabelle sind die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;Profil&gt; </em> oder <em> &lt;Profilen&gt;</em></p></td>
<td><p>Gibt an, ein integriertes Profil oder den Pfad zu einem benutzerdefinierten Profil.</p>
<p>Sie können bis zu 64 Profile auf einer einzelnen Befehlszeile angeben. Jedes Profil wird wie folgt angegeben:</p>
<pre class="syntax" space="preserve"><code>&lt;profile&gt; :=&lt;profile_name&gt;[.{light|verbose}] </code></pre></td>
</tr>
<tr class="even">
<td><p><em>&lt;Profilname&gt;</em></p></td>
<td><p>Jedes Profil kann entweder hell oder verbose oder beide Versionen definieren. Wenn keine dieser Optionen angegeben ist, wird die ausführliche Version verwendet, es sei denn, das Profil nur eine light-Version umfasst. Informationen zur richtigen Syntax finden Sie im vorhergehenden Codebeispiel für <em> &lt;Profil&gt; </em> oder <em> &lt;Profilen&gt;</em>.</p></td>
</tr>
<tr class="odd">
<td><p><em>-filemode</em></p></td>
<td><p>Gibt an, dass im Dateimodus Aufzeichnung durchgeführt wird. (Der Standardmodus ist Arbeitsspeicher.)</p>
<p>Mithilfe dieser Option werden die Daten in eine Datei ungebundene aufgezeichnet, die bis Datenträger belegt zunehmen kann.</p></td>
</tr>
<tr class="even">
<td><p><em>-onoffresultspath</em></p></td>
<td><p>Pfad zu dem die Ablaufverfolgungsdateien gespeichert werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>-onoffproblemdescription</em></p></td>
<td><p>Die Beschreibung des Szenarios.</p></td>
</tr>
<tr class="even">
<td><p><em>-onoffscenario</em></p></td>
<td><p>Gibt einen des Übergangs ein-/ausschalten Typen. Dies sind: Boot, FastStartup, Herunterfahren, RebootCycle, Standby oder Ruhezustand.</p></td>
</tr>
<tr class="odd">
<td><p><em>-numiterations</em></p></td>
<td><p>Legt die Anzahl von Iterationen für <em>Aufzeichnung/Ausschalten</em> . Standardmäßig werden die Einstellungen aus der integrierten oder benutzerdefinierten Profildatei standardmäßig verwendet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="stop"></a>Stopp


Verwenden Sie diese Option, um die aktuelle Aufzeichnung beenden und speichern sie Sie der Datei, die durch das Argument angegeben ist.

**Syntax:**

**wpr** **-Beenden** *&lt;file&gt;* * &lt;Beschreibung des Problems*&gt;

In der folgenden Tabelle sind die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;Datei&gt;</em></p></td>
<td><p>Gibt die Ereignis (ETL) Ablaufverfolgungsprotokolldatei in die WPR Aufzeichnung speichert. Dieses Argument ist erforderlich.</p></td>
</tr>
<tr class="even">
<td><p><em>&lt;Beschreibung des Problems&gt;</em></p></td>
<td><p>Gibt die Beschreibung des Problems an. Dieses Argument ist, zwar optional wird empfohlen, dass Sie es verwenden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="cancel"></a>Cancel


Verwenden Sie diese Option, um die aktuelle Aufzeichnung abzubrechen, ohne die erfassten Daten speichern. Wenn keine Instanz derzeit aktiv ist, wird ein Fehler zurückgegeben.

**Syntax:**

**wpr** **-Abbrechen**

Diese Option enthält keine Argumente.

## <a name="status"></a>Status


Verwenden Sie diese Option, um Statusinformationen über die aktuelle WPR Aufzeichnung anzuzeigen.

**Syntax:**

**wpr** **-Status** \[ *Profile* \] \[ *Kollektoren* \[ *Details*\]\]

Wenn keine Aufzeichnung derzeit aktiv ist, wird eine Meldung an, dass WPR nicht aufgezeichnet wird. Wenn Sie eine Aufzeichnung derzeit aktiv ist, und es werden keine Argumente verwendet, wird die folgenden Statusinformationen angezeigt:

`WPR recording is in progress...`

`Time since start        : 00:04:27`

`Dropped event           : 0`

`Logging mode            : Memory`

Wenn Sie zusammen mit Argumente angeben der **– Status** option, die Informationen, die genannten zeigt zusammen mit Daten, die für diese Option spezifisch sind. In der folgenden Tabelle sind die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung und Beispielausgabe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Profile</em></p></td>
<td><p>Dieses Argument enthält jedes Profil, die in der aktuellen WPR verwendet wird aufzeichnen.</p>
<p><strong>Beispiel:</strong></p>
<p><code>Recording system activity using the following set of profiles:</code></p>
<p><code>Profile                 : CPU.Verbose.Memory</code></p></td>
</tr>
<tr class="even">
<td><p><em>Kollektoren</em></p></td>
<td><p>Informationen zu Zugriffssteuerungslisten-Sammlung. Wenn Puffer verloren gegangen, werden diese Puffer aufgelistet.</p>
<p><strong>Beispiel:</strong></p>
<pre class="syntax" space="preserve"><code>Actively recording collectors:

Collector Name          : NT Kernel Logger
Buffer Size (KB)        : 1024
Events Lost             : 0
System Keywords
        CSwitch
        ProcessThread
        SampledProfile
System Stacks
        CSwitch
        SampledProfile

Collector Name          : WPR_initiated_WPR Event Collector
Buffer Size (KB)        : 1024
Events Lost             : 0
Providers
        Microsoft-Windows-Shell-Core: 0x1000000000000: 0x04
        Microsoft-Windows-Win32k: 0x1000000402000: 0xff : Stack
CaptureState Providers on Save
        Microsoft-Windows-Win32k: 0x80000: 0xff</code></pre></td>
</tr>
<tr class="odd">
<td><p><em></em>Details</p></td>
<td><p>Gibt zusätzliche Informationen zu jedem Collector.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idprodetaprofiledetails"></a><a href="" id="prodet"></a>Profiledetails


Verwenden Sie diese Option, um ausführliche Informationen zu einem Profil oder ein Satz von Profilen anzuzeigen. Verwenden Sie die folgende Syntax, um mehrere Profile angeben, wobei `profile` *n* verweist auf den Namen der einzelnen Profile.

**Syntax:**

`wpr -profiledetails profile1+profile2..+profilen [-filemode] -onoffscenario <OnOff Transition Type>`

## <a name="providers"></a>Anbieter


Verwenden Sie diese Option, um ausführliche Informationen zu Anbietern anzuzeigen. Anbieter finden Sie unter Event Tracing for Windows (ETW) Komponenten, die Ereignisse auf Windows Performance Aufzeichnung (WPR) verfügbar zu machen. Um Informationen zu Anbietern anzeigen möchten, verwenden Sie folgende Syntax, in dem `providers`** bezieht sich auf alle Anbieter für/bekannten installiert und registriert.

**Syntax:**

`wpr -providers`

## <a name="a-href-iddisablepagingexecadisablepagingexecutive"></a><a href="" id="disablepagingexec"></a>DisablePagingExecutive


Verwenden Sie diese Option, um anzugeben, ob der Treiber und Kernelmodus-Systemcode ausgelagert werden können auf dem Datenträger. Diese Einstellung auf *aktiviert* und verhindert, dass Paging.
Diese Option wird den Wert der [DisablePagingExecutive](https://technet.microsoft.com/en-us/library/cc959492.aspx) in der Registrierung.

**Syntax:**

`wpr -disablepagingexecutive <on/off>`

**Hinweis**  
Zum Ereignis Stapel auf 64-Bit-Systemen, auf denen Windows 7 ausgeführt werden ordnungsgemäß zu erfassen, *Disablepagingexecutive* auf *aktiviert*festgelegt werden sollte, und das System muss neu gestartet werden, vor Beginn der Aufzeichnung Leistung. Für 32-Bit-Systeme, auf denen Windows 7 ausgeführt werden und für alle Systeme, die Windows 8 oder höher ausgeführt werden, können Sie die Leistung Aufzeichnung ohne *Disablepagingexecutive* auf *aktiviert*festlegen bedienen.

 

## <a name="log"></a>Log


Verwenden Sie diese Option zum Anfügen und Konfigurieren von Debug-Protokollierung in das Ereignisprotokoll.

**Syntax:**

**wpr** **-Protokoll** {*aktiviert*|*deaktiviert*|*Entfernen*}

In der folgenden Tabelle sind die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>enabled</em></p></td>
<td><p>Ermöglicht debug-Protokollierung in das Ereignisprotokoll.</p></td>
</tr>
<tr class="even">
<td><p><em>deaktiviert</em></p></td>
<td><p>Deaktiviert die debug-Protokollierung in das Ereignisprotokoll.</p></td>
</tr>
<tr class="odd">
<td><p><em>Entfernen</em></p></td>
<td><p>Deinstalliert das WPR Debug-Protokollierung Anbietermanifest aus dem System.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idpurgeapurgecache"></a><a href="" id="purge"></a>PURGECACHE


Verwenden Sie diese Option, um verwaltete Symbolcache zu leeren.

**Syntax:**

**wpr** **Purgecache-**

Diese Option enthält keine Argumente.

## <a name="help"></a>Hilfe


Verwenden Sie diese Option zum Anzeigen der Online-Hilfe in das Eingabeaufforderungsfenster.

**wpr** **-Hilfe** \[{*Log*|*Profile*|*Profiledetails*\\*Disablepagingexecutive*\\*Starten*|*Status*|*Beenden*}\]

Die folgende Tabelle beschreibt die verfügbaren Argumente, die Sie auf diese Option anwenden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Abbrechen</em></p></td>
<td><p>Beschreibt <code>–cancel</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [abzubrechen](#cancel).</p></td>
</tr>
<tr class="even">
<td><p><em>DisablePagingExecutive</em></p></td>
<td><p>Befehlszeilenargument <em>Disablepagingexecutive –</em> beschreibt. Weitere Informationen finden Sie unter [Disablepagingexecutive](#disablepagingexec).</p></td>
</tr>
<tr class="odd">
<td><p><em>Melden Sie sich</em></p></td>
<td><p>Beschreibt <code>-log</code> Befehlszeilenargumente. Weitere Informationen finden Sie im [Protokoll](#log).</p></td>
</tr>
<tr class="even">
<td><p><em>profiledetails</em></p></td>
<td><p>Beschreibt die <em>– Profiledetails</em> Befehlszeilenargument. Weitere Informationen finden Sie unter [Profiledetails](#prodet).</p></td>
</tr>
<tr class="odd">
<td><p><em>Profile</em></p></td>
<td><p>Beschreibt <code>-profiles</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Profile](#profiles).</p></td>
</tr>
<tr class="even">
<td><p><em>Anbieter</em></p></td>
<td><p>Beschreibt <code>-providers</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Anbieter](#providers).</p></td>
</tr>
<tr class="odd">
<td><p><em>PURGECACHE</em></p></td>
<td><p>Beschreibt <code>–purgecache</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Purgecache](#purge).</p></td>
</tr>
<tr class="even">
<td><p><em>Starten</em></p></td>
<td><p>Zeigt eine Beschreibung der <code>-start</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Starten](#start).</p></td>
</tr>
<tr class="odd">
<td><p><em>status</em></p></td>
<td><p>Zeigt eine Beschreibung der <code>-status</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Status](#status).</p></td>
</tr>
<tr class="even">
<td><p><em>Beenden</em></p></td>
<td><p>Beschreibt <code>-stop</code> Befehlszeilenargumente. Weitere Informationen finden Sie unter [Beenden](#stop)</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idremaremarks"></a><a href="" id="rem"></a>Hinweise


Bei jedem WPR eine Verfolgung speichert, die aufgezeichnet wurde, wenn verwaltete Anwendungen auf dem System ausgeführt wurden speichert WPR verwaltete Symbole neben der Trace-Datei. Mit diesem Feature können Performance-Analyse von verwalteten Anwendungen.

Generieren von verwalteten Symbole ist eine Ressource und einmalig zeitaufwändigen Vorgang. WPR erstellt automatisch einen verwalteten Symbolcache, um die Generierung von verwalteten Symbole zu beschleunigen. Wenn WPR verwaltete Symbole benötigt, wird dieser Cache überprüft es zuerst an und verwendet alle verfügbaren und entsprechenden Symbole anstatt neu erstellt werden.

Der Speicherort des standardmäßigen verwalteten Symbol Arbeitsmappencaches ist C:\\Ordner "ProgramData"\\WindowsPerformanceRecorder\\NGenPdbs\_Cache.

## <a name="related-topics"></a>Verwandte Themen


[WPR-Referenz](wpr-reference.md)

 

 







