---
title: "Ergebnisse für die Bewertung der Treiber Überprüfung"
description: "Ergebnisse für die Bewertung der Treiber Überprüfung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16514264-4581-408b-bd7a-778ca245f0bc
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 61d238f3eb74a6f8ee21e7caa7d1df642ca8352c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-driver-verification-assessment"></a>Ergebnisse für die Bewertung der Treiber Überprüfung


Die Überprüfung der Treiber Bewertung hilft Ihnen beim Überprüfen Ihrer offline-Windows-Abbild oder einem ausgeführten Windows-Betriebssystem die korrekte Liste der Treiber enthält. Die Ergebnisse können Sie Probleme wie fehlende unnötige und veraltete Treiber feststellen.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-driverresults)

-   [Probleme](#bkmk-driverissues)

Weitere Informationen zu Systemanforderungen und Bewertung Einstellungen finden Sie unter [Treiber Überprüfung](driver-verification.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für einen high-End-Desktopcomputer festgelegten oder erwartet Land/Ihrer Region möglicherweise so, dass Sie die Flexibilität, verschiedene Ziele zu definieren möchten und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Bei dem Ziel für diese Metrik ein metrischer Wert verglichen wird, ist der Status farblich in der Ansicht Ergebnis wie folgt an:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass die Benutzeroberfläche zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse, um die Verbesserungen, die das System vorgenommen werden können, finden Sie unter. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich. Möglicherweise müssen Sie erwägen Kompromissen, um eine hohe Qualität-Windows-Erfahrung zu übermitteln.

-   Keine Farbe bedeutet, dass es keine Ziele für die Metrik definiert sind.

In der Windows Assessment Toolkit für Windows 8 umfassen einige Bewertung Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools, wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows-10 können.

Sie können legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, um die benutzerdefinierten Ziele anzuwenden. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Nur eine Ziele Datei kann zu einem Zeitpunkt verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Können die Ziele-Beispieldatei, die bereitgestellt wird unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele Ihrer eigenen Ziele-Datei zu erstellen.

**Hinweis**  
Nicht in eine Datei Ziele mit einem Auftrag Pakete, jedoch können sie für andere Benutzer freigegeben gespeichert werden.

 

## <a name="a-href-idbkmk-driverresultsametrics"></a><a href="" id="bkmk-driverresults"></a>Metriken


Das Überprüfung der Treiber Assessment ausgewertet wird, die Treiber auf Ihrem Computer und Ergebnisse erzeugt, die Ihnen helfen können die installierten Treiber verwalten. In der folgenden Tabelle werden die Metriken, die zur Verfügung stehen, nachdem Sie das Assessment Treiber Überprüfung ausgeführt beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Metrisch</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Alle Geräte</p></td>
<td><p>Anzeigen aller Geräte, die das Assessment ermittelt. Sie können die Metrik zum Anzeigen einer Liste von Geräten und zum Identifizieren der Name des Aufnahmegeräts und Device-Klasse erweitern.</p></td>
</tr>
<tr class="even">
<td><p>Geräte mit anderen Probleme</p></td>
<td><p>Die Anzahl der Geräte, die andere als die aufgeführten speziell Probleme in dieser Tabelle.</p></td>
</tr>
<tr class="odd">
<td><p>Fehlende Treiber Geräte</p></td>
<td><p>Die Anzahl der Geräte, die fehlende Treiber haben. Sie können diese Metrik zum Anzeigen einer Liste der Geräte, die einen Treiber fehlen und zum Identifizieren der Gerätenamen und Geräteklassen erweitern.</p></td>
</tr>
<tr class="even">
<td><p>Geräte mit verfügbaren Treiberupdates</p></td>
<td><p>Die Anzahl der Geräte, auf denen Treiber verfügbar sind. Erweitern Sie diese Metrik zum Anzeigen einer Liste von Geräten und den Namen des Geräts, einem besseren Treiber, -Datei des Treibers, den Hersteller des Treibers und die Treiberversion zu identifizieren.</p></td>
</tr>
<tr class="odd">
<td><p>Geräte mit mehrere Treiber</p></td>
<td><p>Die Anzahl der Geräte, die mehrere Treiber haben. Sie können diese Metrik zum Anzeigen einer Liste der Geräte mit mehr als eine zugehörige Treiber und zum Identifizieren der Name des Aufnahmegeräts und Device-Klasse erweitern.</p></td>
</tr>
<tr class="even">
<td><p>Legacy-Geräte</p></td>
<td><p>Die Anzahl der Geräte, die als älteren Geräte erkannt wurden. Sie können diese Metrik sehen Sie eine Liste der älteren Geräte und zum Identifizieren der Name des Aufnahmegeräts, Geräteklasse, Beschreibung, Instanz-ID und das Gerät Hersteller erweitern.</p></td>
</tr>
<tr class="odd">
<td><p>Nicht benötigte Treiber</p></td>
<td><p>Die Anzahl der Geräte, die nicht benötigte Softwaretreiber haben, die nicht mit einem Hardwaregerät verknüpft sind. Erweitern Sie diese Metrik zum Anzeigen einer Liste der unnötige Treiber und die Treiberdatei sowie die Beschreibung Treiberhersteller und Treiberversionen zu identifizieren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idbkmk-driverissuesaissues"></a><a href="" id="bkmk-driverissues"></a>Probleme


Die Überprüfung der Treiber Bewertung identifiziert Probleme mit Treibern, enthält Informationen darüber, wie diese Probleme Einfluss auf das System und schlägt mögliche Lösungen. Die folgenden Probleme und Empfehlungen können nach dem Ausführen des Überprüfung der Treiber Assessment angezeigt werden. Problem Beschreibungen, Empfehlungen und Links zu weiteren Informationen sind auch in der Benutzeroberfläche verfügbar.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Problem</th>
<th>Beschreibung</th>
<th>Empfehlung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Fehlende Treiber</p></td>
<td><p>Es wurde kein Treiber für dieses Gerät gefunden. Das Gerät funktioniert nicht ohne den entsprechenden Treiber.</p></td>
<td><p>Wenn mit dem Internet verbunden ist, suchen Sie Windows Update nach der Treiber für dieses Gerät. Um Windows Update automatisch nach fehlenden Treibern zu suchen, führen Sie Bewertung erneut aus, während Sie mit dem Internet verbunden sind, und verwenden Sie die Standardeinstellungen. In einigen Fällen müssen Sie möglicherweise wenden Sie sich an den OEM oder den Hersteller des Geräts, um die Treiber zu erhalten.</p></td>
</tr>
<tr class="even">
<td><p>Mehrere Treiber</p></td>
<td><p>Anzeigen aller Geräte mit mehrere Treiber verfügbar.</p></td>
<td><p>Zusätzliche Treiber unnötig viel Speicherplatz und Sicherheitsrisiken, die Sicherheit des Computers gefährden enthalten kann. Es wird empfohlen, dass Sie nur die benötigten Treiber enthalten. Entfernen Sie die zusätzliche Treiber aus diesem Abbild offline mithilfe von DISM oder deinstallieren Sie die Treiber aus dem aktiven Computer mithilfe der Geräte-Manager. Weitere Informationen zur Verwendung von DISM zum Entfernen von Treibern finden Sie unter [Befehlszeilenoptionen zum Warten](http://go.microsoft.com/fwlink/?LinkId=225962).</p></td>
</tr>
<tr class="odd">
<td><p>Nicht benötigte Treiber</p></td>
<td><p>Treiber nicht für jede der verfügbaren Hardwaregeräte aufgelistet. Nicht benötigte Treiber können entweder ein Software oder Dienst Treiber handeln.</p></td>
<td><p>Wenn Sie diese Software oder der Dienst nicht verwenden, sollten Sie ihn entfernen. Zusätzliche Treiber können entfernt werden, mithilfe von offline DISM, oder mithilfe der Geräte-Manager. Finden Sie unter [Treiber Befehlszeilenoptionen zum Warten](http://go.microsoft.com/fwlink/?LinkId=225962).</p></td>
</tr>
<tr class="even">
<td><p>Aktualisierte besseren Treiber</p></td>
<td><p>Ein aktualisierter ist verfügbar.</p></td>
<td><p>Es wird empfohlen, dass Sie den Treiber für eine optimale-Funktionen zu aktualisieren. Es ist ein aktueller Treiber auf Windows Update verfügbar. Verwenden Sie den bereitgestellten Link zum Herunterladen des Treibers oder weitere Updates fordern Sie beim Hersteller des Geräts an. Informationen dazu, wie Sie mithilfe von Windows Update finden Sie unter [Windows Update Treiber veröffentlichen](http://go.microsoft.com/fwlink/?LinkId=242240) .</p></td>
</tr>
<tr class="odd">
<td><p>Legacy-Geräte</p></td>
<td><p>Listet die Geräte, die keine Plug & Play-ID.</p></td>
<td><p>Das Microsoft Gerät Zuordnung Stammenumerator Gerät verfügt nicht über eine Plug & Play-ID. Diese Geräte können nicht durch diese Bewertung ausgewertet werden. Verwenden Sie alternativer Methoden zum Überprüfen der Funktionalität von diesem Gerät.</p></td>
</tr>
</tbody>
</table>

 

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Das Assessment Berichte Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Überprüfung der Treiber](driver-verification.md)

[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







