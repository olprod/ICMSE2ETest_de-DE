---
title: "Ein-/ausschalten Übergang-Leistung"
description: "Ein-/ausschalten Übergang Leistung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ad7f1448-c818-412d-9610-1e0a2f7fbd7c
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: a890dcbc19ff4ff1ea57e52b2cd0359a2e0127d0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onoff-transition-performance"></a>Ein-/ausschalten Übergang-Leistung


Die Bewertung weiter Übergang Leistung messen der Übergänge von verschiedenen Computer Status, wie:

-   Power-on Übergänge, einschließlich Boot, aus dem Standbymodus (S3) fortsetzen und Wiederaufnahme aus dem Ruhezustand (S4).

-   Schalten Sie Übergänge, einschließlich Herunterfahren nach unten, geben Sie dem Standbymodus (S3), und geben Sie den Ruhezustand (S4).

-   Die Boot-Intervall das Intervall zwischen dem Zeitpunkt, zu dem die Power-Taste gedrückt wird und die Zeit entspricht, wenn der Computer der Desktop und alle zum Starten des Tasks verarbeitet.

-   Die beim Herunterfahren Intervall wird das Intervall zwischen beim Herunterfahren initiiert wird und wenn der Computer ausgeschaltet wird.

Vier weiter Übergang Leistung Bewertung sind verfügbar. In diesem Thema werden die Start-Leistung (Fast Start), Leistung Ruhezustand und Standby-Leistung Bewertung.

Diese Grafik veranschaulicht Bewertungsprozess:

![Workflow-Grafik zur on/off Übergang Leistung](images/dep-win8-8-techref-on-off-combined.jpg)

In diesem Thema:

-   [Informationen zum ein-/ausschalten Übergang Leistung Bewertung](#bkmk-aboutonoff)

-   [Bevor Sie beginnen](#beforeyoubegin)

-   [Einstellungen](#settings)

-   [Suchergebnisse](#results)

-   [Probleme](#bkmk-issues)

Weitere Informationen zum Analysieren der Ergebnisse für die Bewertung Boot (Fast Start) finden Sie unter [Ergebnisse für die Bewertung ein/aus](results-for-the-onoff-assessments.md).

## <a name="a-href-idbkmk-aboutonoffaabout-onoff-transition-performance-assessments"></a><a href="" id="bkmk-aboutonoff"></a>Informationen zum ein-/ausschalten Übergang Performance-Bewertung


Jede weiter Übergang Performance Assessment wertet einer dieser Übergänge:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Übergang</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Boot (fast Start)</p></td>
<td><p>Das Assessment Start-Leistung (Fast Start) wird die Leistung eines neuen Fast-zum Starten des Übergangs gemessen. Windows-8introduces a Boot verarbeitet das ermöglicht schnellere Starten des Computers in der Regel an. Des Herunterfahrens wurde aktualisiert, um das Schreiben von Daten auf dem Datenträger, auf eine Weise, die ähnelt enthalten wie Ruhezustand funktioniert. Initiieren Sie diesen Prozess, indem Herunterfahren des Computers. Wenn Sie die Taste drücken, wird der Computer aktiviert, und Windows wird mithilfe des fast Startvorgangs gestartet.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn schneller Start in den <strong>Energieoptionen</strong>deaktiviert ist, tritt auf als vollständige Neustarts Herunterfahren und neu starten.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>Standby</p></td>
<td><p>Sie identifizieren Sie die Komponenten, die die größte Auswirkung auf den Übergang zwischen den lokalen Systemzuständen und Anhalten Standby-Leistung Bewertung hilft. Anhalten dem Ruhezustand in der der Computer eingibt Energiesparmodus (S3) und eine sehr geringe Menge Energie verbraucht wird. Standby ist das in den Suspend-Zustand. Der Übergang vom Standby-dem Standbymodus wieder in Standby-Resume wird das Intervall zwischen dem Zeitpunkt, wenn der Computer Reaktivierung initiiert, und die Uhrzeit des Computers verwendbar und schnell ist. Hierbei handelt es sich um die Zeit, wenn der Benutzer drückt die Power Schaltfläche oder ein USB-Gerät (wenn der Computer für Aktivierung auf USB konfiguriert ist), die irgendwann wird nach der Desktop angezeigt wird.</p></td>
</tr>
<tr class="odd">
<td><p>Ruhezustand</p></td>
<td><p>Sie identifizieren Sie die Komponenten, die die meisten wirken sich auf den Übergang zwischen den Systemzuständen Ruhezustand und fortsetzen Ruhezustand Leistung Bewertung hilft. Ruhezustand wird dem Ruhezustand in dem System und die Benutzer Daten in einem Hiberfile auf den Datenträger geschrieben werden. Klicken Sie dann, gibt das System die niedrigste Ruhezustand (S4), und die Leistungsfähigkeit ausgeschnitten wird. Der Übergang vom Ruhezustand wieder aus dem Ruhezustand Reaktivierung ist das Intervall zwischen dem Zeitpunkt, wenn der Benutzer initiiert Reaktivierung aus dem Ruhezustand (durch Drücken die Schaltfläche Power oder ein USB-Gerät, wenn der Computer konfiguriert ist für die Aktivierung-auf-USB-) und die Uhrzeit des Computers ist verwendbar und schnell (irgendwann nach der Desktop angezeigt wird).</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Eine Hiberfile (Hiberfil.sys) ist eine Datei, die das Betriebssystem erstellt, wenn der Computer wechselt Ruhezustand befindet. Der Computer eingeschaltet ist, verwendet Windows diese Datei zurückzugebenden das System seine vor dem Ruhezustand Zustand.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

### <a name="effect-of-fast-startup-on-boot-performance"></a>Auswirkung der schneller Start auf Boot-Leistung

Das Standardszenario Herunterfahren und Neustart wurde in Windows 8 geändert. Prozess des Herunterfahrens enthält nun das Schreiben von Daten auf dem Datenträger in eine Möglichkeit, die Funktionsweise von des Ruhezustand ähnelt. Eine wesentliche Unterschiede zwischen dem Herunterfahren und Neustart des Windows 8 und Herunterfahren und Neustart des vorherigen Windows-Versionen ist, dass alle benutzersitzungen normalerweise abgemeldet und die verbleibende Informationen werden in einer Hiberfile geschrieben. Anmeldung bleibt gleich, wie in den früheren Versionen von Windows war. Der neue Startvorgang in Windows 8 ist in der Regel viel schneller, wie hier gezeigt:

![Vergleich der vorherigen Startvorgang für Windows 8](images/dep-win8-8-techref-comparebootperf(windevprev).jpg) herkömmliche Windows-Startvorgang lädt das Betriebssystem Kernel, Gerätetreibern, und anderer Komponenten Dateien in den Arbeitsspeicher und lädt den Anmeldebildschirm und Desktop. Schneller Start bietet durch Vermeidung von Teil der Arbeit, die bisher beim Start erforderlich ist. Die Vorteile von diesem neuen Herunterfahren-Boot Übergang werden sofort.

Es sind noch mehrere Bereiche, in dem Gerätetreiber, Dienste, Anwendungen und andere Features in diesem Szenario beeinträchtigen können. Das Assessment Start-Leistung (Fast Start) ermöglicht es Ihnen, die Dauer jeder Phase im Szenario zu messen, bietet einen Einblick in was während der einzelnen Unterphase ausgeführt wird, identifiziert potenzielle Probleme und bietet Hilfestellung für Ökosystempartner, um ihre Produkte zu verbessern Remediation.

**Hinweis**  
Traditionelle Windows-Start ist weiterhin manchmal auf einem Computer erforderlich, auf denen Windows 8 ausgeführt wird. Sie können es durch Drücken von STRG + Alt + Entf, das Power Symbol und wählen Sie dann auf **neu starten**initiieren. Beim Neustart des Computers verwendet traditionellen Startvorgang.

 

## <a name="a-href-idbeforeyoubeginabefore-you-begin"></a><a href="" id="beforeyoubegin"></a>Bevor Sie beginnen


Die erste Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Richten Sie ein und bereiten Sie das System durch diese Aktionen, um die genaue und reproduzierbaren Ergebnisse dieser Bewertung zu erhalten:

**Hinweis**  
Vor der Bewertung weiter Übergang Leistung ausgeführt werden soll, überprüfen sie, dass die unterstützten Standbymodus Status verfügbar sind. Wenn eine Precheck bestätigt, dass es sich bei dem erforderlichen Ruhezustand nicht aktiviert ist, werden die Bewertung nicht ausgeführt.

 

-   Da dieser Bewertung mehrere Neustarts durchgeführt werden, wird empfohlen, dass Sie Ihr System zum Automatisieren des Anmeldevorgangs einrichten. Hierzu finden Sie unter [automatisieren Neustarts, bevor Sie eine Bewertung ausführen](automate-reboots-before-you-run-an-assessment.md).

    **Warnung**  
    Keine Interaktion mit dem Computer während die Bewertung ausgeführt wird. Dies kann sich negativ auf die Ergebnisse auswirken. Automatisieren des Anmeldevorgangs können Sie unerwünschte Interaktion verhindern.

     

-   Stellen Sie sicher, dass alle Gerätetreiber ordnungsgemäß installiert sind. Ergebnisse können deutlich variieren, wenn Ihr Computer mit fehlenden oder falschen Treiber verfügt. Die [Überprüfung der Treiber](driver-verification.md) Bewertung können Sie um Treiberprobleme auf dem Computer zu identifizieren, die Sie ermitteln möchten.

-   Stellen Sie sicher, dass die richtige Videokarte und die Treiber installiert sind. Wenn Sie nur die Microsoft® grundlegende Grafikkarte installiert haben, kann nicht das Standby Performance Assessment ausgeführt werden.

-   Bestimmen Sie, ob Ihr System-BIOS vom Netzwerk starten, eine CD/DVD-Laufwerk BitLocker aktiviert, eingefügt oder ein Szenario mit mehreren Boot konfiguriert wurde. Diese Konfigurationen können Verzögerungen in der Startpfad und sind, die sich negativ auf die Ergebnisse beeinflussen.

-   Wenn Ihr System eine mit mehreren Startkonfiguration verfügt, wird ein Menü zum Auswählen eines Betriebssystems beim Start angezeigt. Das Vorhandensein von diesem Menü wirkt sich auf die Auftragsergebnisse.

### <a name="system-requirements"></a>Systemanforderungen

Sie können die Bewertung unter folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows-10

Unterstützte Architekturen enthalten X86 und X64-basierte Systeme.

## <a name="settings"></a>Einstellungen


Bei Ihrer Bewertung verwenden standardmäßig die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen können. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

Wenn Sie möchten, zum Erfassen von Daten, die von der Standarddaten abweicht, können Sie auch die Einstellungen für eine Bewertung anpassen. Beispielsweise können Sie Daten zu beschreiben, mit denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers ausführen würden.

Die folgende Tabelle beschreibt die Bewertung Einstellungen, die für diese Bewertung, zusätzlich zur empfohlenen Werte und alternative Werte für jede Einstellung verfügbar sind.

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
<td><p>Gibt an, ob das Assessment ausgeführt wird, indem Sie unter Verwendung der Standardwerte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Anzahl von Iterationen</p></td>
<td><p>Gibt die Anzahl der Male, dass die Bewertung Neustarts zum Zeitpunkt, zu des Herunterfahren starten und Prozess ausgeführt wird. Standardmäßig ist der Wert 3.</p></td>
</tr>
<tr class="odd">
<td><p>Führen Sie einen Neustart der anfänglichen</p></td>
<td><p>Gibt an, ob das System neu starten, bevor die Bewertung ausgeführt wird. Diese Einstellung wird in der Leistung Ruhezustand und dem Standbymodus Bewertungsfragen verwenden, jedoch nicht bei der Bewertung Start-Leistung (Fast Start) verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Alternative WPR Profil verwenden</p></td>
<td><p>Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wählen Sie sie aus, wenn Sie ein Windows Performance Aufzeichnung (WPR) Profil als Standard verwenden möchten. Wenn dieses Kontrollkästchen aktiviert ist, geben Sie den Pfad zu einer anderen WPR Profil.</p></td>
</tr>
<tr class="odd">
<td><p>Pfad zur alternativen Trace-Profil (.wprp)</p></td>
<td><p>Stellt den Pfad zu einer alternativen WPR Profil. Um einen alternativen Pfad anzugeben, aktivieren Sie das Kontrollkästchen <strong>Alternative WPR Profil verwenden</strong> , und geben Sie den Pfad im Feld <strong>Pfad alternative Trace-Profil</strong> .</p></td>
</tr>
<tr class="even">
<td><p>Minifilter Diagnosemodus aktivieren</p></td>
<td><p>Gibt an, ob die Diagnose Minifilter Option verwenden. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wenn Minifilter Diagnosemodus aktiviert ist, generiert er Metriken, die Ihnen helfen Bewerten der Auswirkungen der Minifilter Boot-Leistung. Weitere Informationen zu dieser Einstellung finden Sie unter [Minifilter Diagnose](minifilter-diagnostics.md). Diese Einstellung ist nur in der Bewertung der Start-Leistung (Fast Start) verfügbar.</p></td>
</tr>
<tr class="odd">
<td><p>Sammeln von e/a-Ablaufverfolgungsdatei</p></td>
<td><p>Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wählen Sie sie aus, wenn Sie einen Speicher e/a-Trace zusätzlich zum Standard CPU Trace erfassen möchten. Diese Einstellung ist nur in der Bewertung der Start-Leistung (Fast Start) verfügbar.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Die Minifilter Ergebnisse werden nur, wenn Sie das Kontrollkästchen **Aktivieren Minifilter Diagnosemodus** vor dem Ausführen der Bewertung auswählen.

 

## <a name="results"></a>Ergebnisse


Die Ergebnisse anzeigen Metriken für den Startvorgang standby und Ruhezustand Leistung des Computers. Einige der Metriken haben zusätzliche Informationen, die Sie anzeigen können, indem sie erweitern.

Die Bewertungsfragen weiter Übergang führen eine Reihe von ein-/ausschalten Übergänge während die Bewertung ausgeführt wird. Eine einzelne Datenreihe der Übergänge, die von einer Bewertung durchgeführt wird als Iteration bezeichnet. Es gibt drei verschiedene Typen von Iterationen: Timing, Analyse und e/a-Analyse.

-   **Timing Iterationen.** Diese Iterationen dienen als Grundlage für die metrischen Werte für alle Herunterfahren starten und Metriken, die erfasst werden. Jedes ein-/ausschalten Übergang zur Bewertung führt drei Timing Iterationen standardmäßig und drei Timing ETL-Ablaufverfolgungsprotokollen erfasst. Die metrischen Werte dargestellt sind die durchschnittliche zwischen allen Timing Iterationen. Um die Werte für einzelne Iterationen, in der Ansicht Ergebnisse finden Sie unter mit der rechten Maustaste der Spaltenüberschrift Ergebnisse, und anschließend auf **Anzeigen Iterationen**.

-   **Analyse Iteration.** Diese Iteration werden Informationen gesammelt, während das Assessment ausgeführt wird und als Grundlage für die Probleme, die durch die Bewertung generiert dient. Aufgrund der Aufwand zusätzliche Tracing dauert länger als in einer allgemeinen Fall verwenden die Vorgänge in dieser Iteration. Lassen Sie diese Abweichung (Metriken haftbar gemacht werden, aus dem Timing Iterationen und Probleme haftbar gemacht werden, von der Analyse Iteration) Beachten Sie beim selektieren und Analysieren von Ergebnissen der Bewertung.

-   **E/a-Analyse Iteration.** Diese Iteration sammelt Trace sehr ausführliche Informationen zu den e/a-Subsystem und Registrierung Zugriffe: Dieser Protokollierungstyp werden nicht standardmäßig erfasst, zum Aktivieren sie die **Ablaufverfolgungsdatei sammeln e/a** -Assessment-Einstellungen vor dem Ausführen der Bewertung auszuwählen. Die Bewertung führen 3 Neustarts, standardmäßig an die tatsächliche Timing Dauer für jede Iteration über den Prozess Herunterfahren starten und erfassen.

Die folgende Tabelle enthält eine kurze Beschreibung der Metriken, die ein/aus Übergang Leistung-Bewertungen zu erfassen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Metrisch</th>
<th>Beschreibung</th>
<th>Bewertung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dauer der BIOS-Initialisierung</p></td>
<td><p>Die Zeit in Sekunden, die BIOS, einschließlich der vor dem Start Execution Environment (PXE) nicht initialisiert werden.</p></td>
<td><p>Start-Leistung, Standby Leistung Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Explorer Initialisierung Dauer</p></td>
<td><p>Die Zeit, Internet Explorer zu initialisieren. Enthält Details, um die gesamte CPU-Verwendung in Millisekunden, und in Kilobyte Datenträger insgesamt verwendet werden sollen. Außerdem werden Details zu allen Prozessen für die Initialisierung von Internet Explorer ein.</p></td>
<td><p>Start Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Leeren Speicher Volumes Dauer</p></td>
<td><p>Die Zeit in Sekunden, um alle dirty-Daten und ein beständiger Speicher zu leeren.</p></td>
<td><p>Start-Leistung, Standby Leistung Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Hiberfile Initialize Dauer</p></td>
<td><p>Die Zeit in Sekunden, die Hiberfile nicht initialisiert werden.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Dauer der Hiberfile lesen</p></td>
<td><p>Die Zeit in Millisekunden an, die das Betriebssystem zum Lesen der Hiberfile ausgeführt wurden.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Dauer der Hiberfile schreiben</p></td>
<td><p>Die gesamte Zeit in Millisekunden an, die das Betriebssystem zum Schreiben der Hiberfile ausgeführt wurden.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Hauptfenster Pfad Boot Dauer</p></td>
<td><p>Für die Bewertung Start Leistung ist dies die Zeit in Sekunden, die vom Ende des BIOS Initialisierung fortsetzen, bis Windows initialisiert wird. Dies schließt nicht die Post weiter metrische Dauer.</p>
<p>Für Standby und Ruhezustand Leistung Bewertung ist dies die Zeit in Sekunden, die vom Ende des BIOS Initialisierung fortsetzen, bis Windows nicht eingeschlossen ist die Post weiter metrische Zeitdauer fortgesetzt wird.</p></td>
<td><p>Start-Leistung, Standby Performance Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Hauptfenster Pfad Resume Dauer</p></td>
<td><p>Die Zeit in Sekunden, die vom Ende der BIOS auf einer initialisierten Windows Desktop fortzusetzen.</p></td>
<td><p>Start-Leistung, Standby Leistung Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>On/Off Dauer buchen</p></td>
<td><p>Die Zeit in Millisekunden an, die Windows unternommen haben, um alle Startaufgaben ausführen, nachdem der Desktop angezeigt wurde.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Dauer der Abfrage-Geräte</p></td>
<td><p>Die Zeit in Sekunden, die alle Geräte für einen Suspend Power Übergang Abfragen.</p></td>
<td><p>Start-Leistung, Standby Leistung Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Dauer der Resume-Geräte</p></td>
<td><p>Die Zeit in Sekunden, die das Betriebssystem benötigte Geräte während des Aktivierungsvorgangs fortsetzen Geräte fortsetzen.</p></td>
<td><p>Start-Leistung, Standby Performance Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Vorbereiten der SuperFetch Arbeitsspeicher Dauer</p></td>
<td><p>Die Zeit in Sekunden, die für eine optimierte Resume wünschen Systemspeichers vorbereiten.</p></td>
<td><p>Start-Leistung, Standby Leistung Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Geräte Dauer anhalten</p></td>
<td><p>Die Zeit in Sekunden, die alle Geräte angehalten werden soll.</p></td>
<td><p>Start-Leistung, Standby Performance Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>Prozesse Dauer anhalten</p></td>
<td><p>Die Zeit in Millisekunden an, die das Betriebssystem anhalten Prozesse während der Bewertung von ausgeführt wurden. Falls verfügbar, erweitern Sie darauf, um weitere Informationen zu den Prozessen für die Suspend-Phase finden Sie unter. Dazu zählen Informationen zu Unterphase Dauer, CPU-Verwendung und Datenträger verwenden.</p></td>
<td><p>Start-Leistung, Standby Performance Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Services Dauer anhalten</p></td>
<td><p>Die Zeit in Millisekunden an, die das Betriebssystem konferenzbeitritt benötigten Dienste während der Bewertung anhalten. Falls verfügbar, erweitern Sie darauf, um weitere Informationen über die Zeit anzuzeigen, die jede Unterphase ausgeführt wurden.</p></td>
<td><p>Start-Leistung, Standby Performance Ruhezustand Leistung</p></td>
</tr>
<tr class="even">
<td><p>System Sitzungsdauer Herunterfahren Prozesse</p></td>
<td><p>Die Zeit in Sekunden, die die Prozesse in der Sitzung System Herunterfahren.</p></td>
<td><p>Boot-Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Insgesamt Boot [ausschließlich BIOS] Dauer</p></td>
<td><p>Die gesamte Zeit in Sekunden, die das System, einschließlich Beitrag weiter zu starten.</p></td>
<td><p>Start Leistung</p></td>
</tr>
<tr class="even">
<td><p>Dauer der insgesamt Resume [ausschließlich BIOS.]</p></td>
<td><p>Die gesamte Zeit in Sekunden, die das System, einschließlich Beitrag weiter fortsetzen.</p></td>
<td><p>Starten von Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Benutzer Sitzungsdauer Herunterfahren Prozesse</p></td>
<td><p>Die Zeit in Sekunden, die Prozesse in der die Sitzung beendet.</p></td>
<td><p>Start Leistung</p></td>
</tr>
<tr class="even">
<td><p>WinLogon Resume Dauer</p></td>
<td><p>Die Zeit in Sekunden, die das Betriebssystem unternommen haben, um den Vorgang fortsetzen Winlogon fortsetzen.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
<tr class="odd">
<td><p>Winlogon Dauer anhalten</p></td>
<td><p>Die Zeit in Sekunden, die der Benutzer, einschließlich der Abmeldung Benachrichtigungen Verarbeitung und Benachrichtigen der Winlogon-Abonnenten abgemeldet wie Gruppenrichtlinien.</p></td>
<td><p>Starten Sie die Leistung, Ruhezustand Leistung</p></td>
</tr>
</tbody>
</table>

 

Wenn Sie die Einstellung **Diagnostic Minifilter-Modus aktivieren** aktiviert haben, werden die Bewertungsergebnisse Minifilter Metriken enthalten. Weitere Informationen zu Minifilter Metriken und Ergebnisse finden Sie unter [Minifilter Diagnose](minifilter-diagnostics.md).

Weitere Informationen zum Analysieren der Ergebnisse für die Bewertung Boot (Fast Start) finden Sie unter [Ergebnisse für die Bewertung ein/aus](results-for-the-onoff-assessments.md).

## <a name="a-href-idbkmk-issuesaissues"></a><a href="" id="bkmk-issues"></a>Probleme


Die Bewertungsfragen weiter Übergang Performance erweiterte Problem Analysen durchführen und Links zu Windows® Performance Analyzer (WPA) zu den Problemen, die die Bewertungsfragen identifiziert haben. Wenn WPA geöffnet wird, möglicherweise zusätzliche Informationen zu dem Datenträger oder CPU Aktivität verfügbar, je nach Art des Problems. Weitere Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Depth Analysis Probleme](common-in-depth-analysis-issues.md).

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Bewertung ein-/ausschalten](results-for-the-onoff-assessments.md)

[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







