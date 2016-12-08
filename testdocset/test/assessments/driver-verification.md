---
title: "Überprüfung der Treiber"
description: "Überprüfung der Treiber"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 23dd86be-1262-4ec0-a7bb-1f411bc1ef04
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 19ee61287263201eafcbfe1cab390621a6c9ab87
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="driver-verification"></a>Überprüfung der Treiber


Das Assessment Treiber Überprüfung stellt sicher, dass ein offline-Windows-Abbild oder einem ausgeführten Windows-Betriebssystem die korrekte Liste der Treiber enthält. Die Ergebnisse enthalten Empfehlungen, um mögliche Probleme zu beheben, die die Bewertung findet. Diese Probleme können fehlende, doppelte, ältere oder unnötige Treiber enthalten. Weitere Informationen zu Ergebnisse und Problemen finden Sie unter [Ergebnisse für die Bewertung der Treiber die Überprüfung](results-for-the-driver-verification-assessment.md).

Das Assessment Treiber Überprüfung verwendet werden kann:

-   Hier finden Sie Gerät und Treiber Probleme ohne Verwendung der Geräte-Manager.

-   Fehlende Gerätetreiber entweder in einem Windows-Abbild oder einem ausgeführten Betriebssystem suchen.

-   Hier finden Sie Treiberprobleme, bevor Sie ein Bild an einem Computer bereitstellen.

-   Hier finden Sie Software Treibern, die keine Hardwaregeräte zugeordnet sind.

Die folgende Abbildung veranschaulicht die Bewertungsprozess.

![Workflow-Grafik zur Überprüfung der Treiber](images/dep-win8-8-techref-driverassessmentflow.jpg)

In diesem Thema:

-   [Systemanforderungen](#beforebegin)

-   [Einstellungen](#settings)

## <a name="a-href-idbeforebeginasystem-requirements"></a><a href="" id="beforebegin"></a>Systemanforderungen


Die erste Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Sie können diese Bewertung unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows-10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Es gibt zwei Methoden, um diese Bewertung auf Windows RT auszuführen:

-   Packen des Bewertung Auftrags in der Windows-Assessment-Konsole und führen sie dann auf Windows RW Weitere Informationen zu dieser Option finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausgeführt Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="settings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen können. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

Wenn Sie möchten, zum Erfassen von Daten, die unterscheidet sich von was die Bewertung standardmäßig erfasst wird, können Sie auch die Einstellungen anpassen. Beispielsweise können Sie Daten zu beschreiben, in denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers ausführen werden.

Die folgende Tabelle beschreibt die Einstellungen für die Bewertung Einstellungswerte und alternative Werte für jede Einstellung empfohlen.

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
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Input Pfad für Geräte</p></td>
<td><p>Gibt einen Pfad zu einer Device.xml Datei mit einer Bestandsaufnahme aller Geräte auf dem Computer an. In der Standardeinstellung kein Pfad bereitgestellt wird, und Geräteinformationen werden erfasst, auf dem Computer, auf dem die Bewertung auf ausgeführt wird. Wenn Sie einen Pfad zu einer Datei Device.xml bereitstellen, wird stattdessen die Geräteinformationen in der Datei verwendet werden.</p></td>
</tr>
<tr class="odd">
<td><p>Automatische Konsole</p></td>
<td><p>Gibt an, ob der Auftrag im automatischen Modus (ohne eine Konsole UI) ausgeführt wird. Dies ist das Standardverhalten.</p></td>
</tr>
<tr class="even">
<td><p>Schreiben von Devices.xml</p></td>
<td><p>Gibt an, ob eine Devices.xml Datei mit einer Bestandsaufnahme aller Geräte auf dem Computer generiert werden soll. Standardmäßig ist dieses Kontrollkästchen deaktiviert, und die Datei wird nicht generiert. Wenn Sie dieses Kontrollkästchen aktivieren, wird eine Devices.xml Datei auf dem lokalen Computer in den Ergebnisordner Assessment zur späteren Verwendung gespeichert.</p></td>
</tr>
<tr class="odd">
<td><p>Schreiben von Driver.xml</p></td>
<td><p>Gibt an, ob eine Drivers.xml-Datei, die Listen der Treiber, die auf dem Computer oder nicht generiert wird. Standardmäßig ist dieses Kontrollkästchen deaktiviert, und die Datei wird nicht generiert. Wenn Sie dieses Kontrollkästchen aktivieren, wird eine Drivers.xml-Datei auf dem lokalen Computer im Ordner Assessment Ergebnisse für die spätere Verwendung gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>Bereitgestellte Abbildpfad</p></td>
<td><p>Gibt den vollständigen Pfad zu einem bereitgestellten Windows-Abbild an, ob die Bewertung für Schwelle Windows offline ausgeführt werden soll. Standardmäßig dieses Feld leer ist, und die Bewertung wertet die Treiber unter dem Betriebssystem ausgeführt wird.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Bewertung der Treiber Überprüfung](results-for-the-driver-verification-assessment.md)

[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







