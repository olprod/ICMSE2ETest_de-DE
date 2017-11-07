---
author: kpacquer
Description: Blinken tools
ms.assetid: ac04af30-84ef-4d09-9c6f-5b9c01f9a2a0
MSHAttr: PreferredLib:/library/windows/hardware
title: Blinken-tools
ms.openlocfilehash: 0dd3a1876cffe2c402c93998dc18812bc5c90033
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flashing-tools"></a>Blinken-tools


Jeder Hersteller hat verschiedenen Techniken und Tools, die für die Herstellung und einem Windows-10-Mobile-Gerät-service verwendet werden. Die beste technische Kenntnisse, Bezug Manufacturing in diesen sich befindet, die die OEM Manufacturing Zeile integriert. Dies bedeutet, dass der OEM Sie bestimmen, welche blinken müssen und manufacturing Prozess am besten für sie funktioniert. OEM Servicecenter möglicherweise eindeutige Anforderungen, die auch die Auswahl der Tools blinkendes beeinflussen wird. Bestimmen, wie testen und überprüfen, dass die ausgewählten Tools und Prozesse erfüllt ihre Kosten, Qualität und andere eindeutige Fertigung Ziele müssen der OEM.

Der OEM verwendet Microsoft bereitgestellten imaging Tools, um die FFU Images erstellen, die auf das Gerät aktualisiert werden.

## <a name="span-idflashingtoolscomparisonspanspan-idflashingtoolscomparisonspanspan-idflashingtoolscomparisonspanflashing-tools-comparison"></a><span id="Flashing_tools_comparison"></span><span id="flashing_tools_comparison"></span><span id="FLASHING_TOOLS_COMPARISON"></span>Vergleich der blinken


OEM müssen möglicherweise entwickeln ein benutzerdefiniertes blinkendes Tool, um die Anforderungen des Lebenszyklus des Geräts gerecht werden. Andere Optionen blinkenden haben Einschränkungen, die der OEM vertraut sein sollten, bevor Sie sich entscheiden, deren Verwendung.

In der folgenden Tabelle werden die blinkende Tooloptionen zusammengefasst.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Szenario</th>
<th align="left">Microsoft FFU Engineering-Tool</th>
<th align="left">OEM benutzerdefinierte FFU Tool</th>
<th align="left">Tool SoC blinkendes Manufacturing bereitgestellt</th>
<th align="left">Gang Programmierer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Engineering und Entwicklung</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>N/V</p></td>
</tr>
<tr class="even">
<td align="left"><p>Fertigung</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Service-Center</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>n/v</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idoemcustomflashingtoolspanspan-idoemcustomflashingtoolspanspan-idoemcustomflashingtoolspanoem-custom-flashing-tool"></a><span id="OEM_custom_flashing_tool"></span><span id="oem_custom_flashing_tool"></span><span id="OEM_CUSTOM_FLASHING_TOOL"></span>Benutzerdefinierte blinkende OEM-tool


Wenn ein blinkendes Tool für die Produktion erstellen möchten, muss der OEM eigene Tools für ihre Umgebung Fertigung und Ausrüstung angepasst entwickeln.

Je nach den Anforderungen OEMs müssen die blinkende Tools auch eine Reihe von Szenarien beschrieben, die im [Feld Service-Szenarien](field-service-scenarios.md)zu behandeln.

Weitere Informationen finden Sie unter [Developing benutzerdefinierten OEM blinkende Tools](developing-custom-oem-flashing-tools.md).

## <a name="span-idsocprovidedmanufacturingflashingtoolspanspan-idsocprovidedmanufacturingflashingtoolspanspan-idsocprovidedmanufacturingflashingtoolspansoc-provided-manufacturing-flashing-tool"></a><span id="SoC_provided_manufacturing_flashing_tool"></span><span id="soc_provided_manufacturing_flashing_tool"></span><span id="SOC_PROVIDED_MANUFACTURING_FLASHING_TOOL"></span>SoC manufacturing blinkende Tool bereitgestellt


Informationen der bereitgestellten manufacturing blinkende Tools SoC wenden Sie sich an den Anbieter SoC.

## <a name="span-idgangprogrammerspanspan-idgangprogrammerspanspan-idgangprogrammerspangang-programmer"></a><span id="Gang_programmer"></span><span id="gang_programmer"></span><span id="GANG_PROGRAMMER"></span>Gang Programmierer


Eine Reihe von Optionen stehen zur Verfügung, an den OEM binäre Abbilder blinkt. OEM können ihrer eindeutigen blinkende Tools sowie Gang Programmierer Technologien auf das Gerät herstellen, wenn sie feststellen, dass diese Optionen für ihre Umgebung besser geeignet sind.

Wenn der OEM Gang Programmierer verwendet müssen sie entwickeln ein benutzerdefiniertes Tool, um das Bild FFU auf ein Roh binäre Bild zu konvertieren. Das Tool für die Konvertierung müssen:

1.  Öffnen Sie eine unformatierte Binärdatei in das vom Programmierer Gang erwartete Format ein.

2.  Lesen Sie in der Datei FFU und Analysieren der Dateidaten gemäß [FFU Bildformat](ffu-image-format.md).

3.  Schreibt Daten, auf die in der FFU BLOCKIEREN\_DATEN\_ENTRY-Elemente der Roh-Datei.

4.  Wenn keine weiteren Einträge vorhanden sind, schreibt alle Metadaten oder Füllzeichen für das unformatierte Format erforderlich ist, und schließen Sie dann die Rohdaten Binärdatei.

## <a name="span-idffutoolsupportlimitationsspanspan-idffutoolsupportlimitationsspanspan-idffutoolsupportlimitationsspanffutool-support-limitations"></a><span id="FFUTool_support_limitations"></span><span id="ffutool_support_limitations"></span><span id="FFUTOOL_SUPPORT_LIMITATIONS"></span>Eingeschränkte FFUTool-Unterstützung


Die Microsoft bereitgestellt FFUTool vollständige flash-Update (FFU) Technologie für engineering-Entwicklung und Testzwecke entwickelt wurde. Es ist nicht für die Verwendung in der Produktion unterstützt. Jede OEM muss ermitteln, ob die FFUTool zur Verwendung in ihrer Service Center-Umgebungen geeignet ist.

## <a name="span-idffutoolknownissuesspanspan-idffutoolknownissuesspanspan-idffutoolknownissuesspanffutool-known-issues"></a><span id="FFUTool_known_issues"></span><span id="ffutool_known_issues"></span><span id="FFUTOOL_KNOWN_ISSUES"></span>FFUTool – bekannte Probleme


Mithilfe der FFUTool hat eine Reihe von erhebliche Einschränkungen, die hier zusammengefasst werden.

### <a name="span-idusbhubactivitymaycauseflashingfailuresspanspan-idusbhubactivitymaycauseflashingfailuresspanspan-idusbhubactivitymaycauseflashingfailuresspanusb-hub-activity-may-cause-flashing-failures"></a><span id="USB_hub_activity_may_cause_flashing_failures"></span><span id="usb_hub_activity_may_cause_flashing_failures"></span><span id="USB_HUB_ACTIVITY_MAY_CAUSE_FLASHING_FAILURES"></span>USB-Hub Aktivität kann blinkende Fehler verursachen.

Einige USB-Hubs bekanntermaßen Zuverlässigkeit Problemen führen, auch wenn blinkendes Geräte in seriell aufgrund von Interferenzen mit den streaming FFU Daten Hardware.

Mehrere Geräte, die einen einzelnen USB-Hub freigeben können nicht verbunden sein und getrennt, während andere angeschlossene Geräte blinken. Dies Identifizieren einer bekannten Hardwareproblem mit einigen USB-Controller. Weitere Informationen finden Sie unter [KB908673](http://support.microsoft.com/kb/908673). Trennen Sie USB-Geräte nicht Sie Wenn Geräts blinken aktiviert wird.

### <a name="span-idusbcablelengthislimitedto3feetspanspan-idusbcablelengthislimitedto3feetspanspan-idusbcablelengthislimitedto3feetspanusb-cable-length-is-limited-to-3-feet"></a><span id="USB_cable_length_is_limited_to_3_feet"></span><span id="usb_cable_length_is_limited_to_3_feet"></span><span id="USB_CABLE_LENGTH_IS_LIMITED_TO_3_FEET"></span>Die Länge des USB-Kabels ist beschränkt auf 3 Fuß

Blinken möglicherweise unzuverlässiger, bei Verwendung von mehr als 3.91 Meter USB-Kabel, oder wenn das blinkende Setup aufeinander folgende Kabel enthält, die auf mehr als 3 Fuß insgesamt. Dies ist aufgrund von Einschränkungen der Datenübertragung in Kabel Hardware.

### <a name="span-idflashingtimeperphonespanspan-idflashingtimeperphonespanspan-idflashingtimeperphonespanflashing-time-per-phone"></a><span id="Flashing_time_per_phone"></span><span id="flashing_time_per_phone"></span><span id="FLASHING_TIME_PER_PHONE"></span>Einmal pro Phone blinken

Sie müssen ermitteln, ob die blinkende einmal pro Gerät ihre Ziele für die Fertigung Leitung erfüllt.

 

 





