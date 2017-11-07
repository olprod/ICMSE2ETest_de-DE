---
author: Justinha
Description: "Hochauflösenden und Windows 8.1"
ms.assetid: e330d659-35f0-4178-b504-1e5a3bd169ca
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hochauflösenden und Windows 8.1"
ms.openlocfilehash: f69dedf30719c3869ac5067e7abe6f034a6f5611
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="high-dpi-and-windows-81"></a>Hochauflösenden und Windows 8.1


In diesem Thema erläutert die wichtigsten Konzepte der DPI und Anzeige Skalierung und beschreibt, was ist neu in Windows 8.1.

**In diesem Thema:**

-   [Wichtige Konzepte](#key)

-   [Neuigkeiten zu DPI](#newdpi)

## <a name="span-idkeyspanspan-idkeyspankey-concepts"></a><span id="key"></span><span id="KEY"></span>Wichtige Konzepte


### <a name="span-idwhatisdpispanspan-idwhatisdpispanspan-idwhatisdpispanwhat-is-dpi"></a><span id="What_is_DPI"></span><span id="what_is_dpi"></span><span id="WHAT_IS_DPI"></span>Was ist DPI

Punkte pro Zoll (DPI)) ist die physische Messung der Anzahl der Pixel in eine lineare Zoll angezeigt. DPI ist eine Funktion der Auflösung und Größe. einer höheren Auflösung oder eine geringere Größe führt zum höherer Auflösung und eine geringere Auflösung oder vergrößert werden nach unten DPI führen. Wenn eine Darstellung einer höheren DPI aufweist, sind Pixel kleiner und näher zusammen, sodass der Benutzeroberfläche (UI) und anderen angezeigten Inhalten kleiner als vorgesehen angezeigt wird.

### <a name="span-idscalespanspan-idscalespanwhat-are-windows-scale-factors"></a><span id="scale"></span><span id="SCALE"></span>Was sind Windows Skalierungsfaktor

Windows® wird sichergestellt, dass alle Elemente auf dem Bildschirm mit einer Größe verwendbar und konsistente angezeigt wird, durch die Anweisung an ihren Inhalt durch einen Skalierungsfaktor Größe (einschließlich der Windows-desktop-Shell). Diese Nummer hängt davon ab, die Anzeige DPI als auch andere Faktoren, die der Benutzer Wahrnehmung der Anzeige auswirkt. Fast alle desktop zeigt und aktuelle Laptop zeigt liegen im Bereich von 95 110 DPI; für diese Geräte keine Skalierung ist erforderlich und Windows einen Skalierungsfaktor von 100 % festgelegt. Es gibt jedoch eine Anzahl von neuen Geräten, insbesondere in Premium Laptop und Tablet Märkte, die was höhere zeigt mit über 200 DPI haben. Für diese Geräte wird Windows höher Skalierungsfaktor um sicherzustellen, dass die Benutzeroberfläche bequem angezeigt werden.

### <a name="span-idusersspanspan-idusersspanwhy-this-matters-to-users"></a><span id="users"></span><span id="USERS"></span>Warum dies für Benutzer wichtig ist

Die Benutzer müssen in der Regel Stunden lesen und auf Windows-Geräten arbeiten, daher ist es wichtig, um sicherzustellen, dass das Gerät, das mit für ihren Komfort optimiert ist. Aus diesem Grund ist es wichtig für Windows, um den Inhalt der besten lesbar Weise darstellen, sodass die Augen Überlastung wird reduziert, und Produktivität ist nicht betroffen sind. Wie Technologie verbessert, kann dies in einer Kombination aus einer höheren DPI zeigt übermittelt und bessere Skalierung in Windows sein. Windows 8 bietet Features, die die standardmäßige Skalierung neuere, zeigt DPI zeigt besser entsprechend automatisch angepasst werden.

### <a name="span-identerprisesspanspan-identerprisesspanwhy-this-matters-to-enterprises"></a><span id="enterprises"></span><span id="ENTERPRISES"></span>Warum dies für Unternehmen wichtig ist

Windows-Geräten zu verbessern, wird hohe Dichte zeigt immer häufiger in unternehmensumgebungen. Unternehmen sind ebenfalls verschieben zu einer mehr mobile Mitarbeiter, die Laptops an Besprechungen zu verwenden, um das Projekt, Andocken Lösungen Wenn am Schreibtisch. Um eine optimale Produktivität zu gewährleisten, sollten Benutzer im Unternehmen nicht müssen wie ihre Bildschirme gesperrt, wenn sie project, oder wie ihre docking Lösungen werden ihre Arbeitsbereich angezeigt, wenn intensiv an einem Schreibtisch verwalten. Windows 8 führt dies automatisch für die meisten Benutzer, aber es verbleiben einige Edge Fällen die Hilfe IT-Experten in unternehmensumgebungen müssen möglicherweise Unterstützung. In diesem Thema wird beschrieben, wie Windows automatisch in den meisten Fällen die richtige Wahl ist und auf dem IT müssen möglicherweise Schritt und den Benutzer helfen.

## <a name="span-idnewdpispanspan-idnewdpispanwhats-new-about-dpi"></a><span id="newdpi"></span><span id="NEWDPI"></span>Neuigkeiten zu DPI


### <a name="span-iddisplayhardwaremarketchangesspanspan-iddisplayhardwaremarketchangesspanspan-iddisplayhardwaremarketchangesspandisplay-hardware-market-changes"></a><span id="Display_hardware_market_changes"></span><span id="display_hardware_market_changes"></span><span id="DISPLAY_HARDWARE_MARKET_CHANGES"></span>Hardware-marktveränderungen anzeigen

Mit der Einführung von einer höheren DPI angezeigt. Windows-Geräte, die während und nach 2013 verfügbar sind, werden regelmäßig DPI-Werte feature, die viel höher ist als was zuvor verfügbar wurde sind. Anstelle von Laptops mit 13" und von 1366 x 768 Auflösung sehen Sie bildschirmauflösungen auf 3200 x 1800 unter 13" einrichten. Für diese Laptops verwendet werden, Windows Skalierung von 100 % (13,3" 1366 x 768) auf 125 % (13,3" 1600 x 900), 150 % (10,6" 1920 x 1080) verschieben verfügt oder 200 % (13,3" 2560 x 1440). Bevor Sie Windows 8 wurden nur 100 %, 125 % und 150 % automatisch festgelegt entsprechend die Anzeige; Unterstützung von 200 % wurde in Windows 8 hinzugefügt.

### <a name="span-idwindows81changesspanspan-idwindows81changesspanspan-idwindows81changesspanwindows-81-changes"></a><span id="Windows_8.1_changes"></span><span id="windows_8.1_changes"></span><span id="WINDOWS_8.1_CHANGES"></span>Windows 8.1 Änderungen

Windows 8 enthält eine Reihe von Änderungen bei Features, die für hohe DPI spezifisch sind, wie in *Tabelle 1 Windows 8.1 DPI Änderungen*dargestellt:

**Tabelle 1 Windows 8.1 DPI Änderungen**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Windows 8</th>
<th align="left">Windows 8.1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Unterstützung für die Skalierung von 200 %</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>DPI-monitor</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Skalierung von vorhandenen DPI-fähigen Anwendung</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Unterstützende Anwendungen DPI pro monitor</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Anzeigen von Abstand integriert in standardmäßigen DPI-Berechnung</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Kostenlose DPI Abmeldung ändern</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DPI pro Monitor Beachten Sie Internet Explorer</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Auto-DPI-Konfiguration des Remotedesktop</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
</tbody>
</table>

 

Die ersten beiden oben genannten Features wirken die größte sich auf Windows 8 Verwendbarkeit. Ausführlicher:

1.  **Verbesserte Unterstützung Skalierung von 200 %:** Windows 8.1 hohe DPI Anzeigegeräte für dynamische einzeln identifiziert und systemintern unterstützt bis zu 200 % Skalierungsfaktor. Windows 8 nur beim ersten Start identifiziert eine hohe DPI-Anzeige und nur unterstützt bis zu 150 % ohne Anpassung durch die Benutzer skalieren. Dieses Feature wird sichergestellt, dass Benutzer, die Premium Laptops mit hoher DPI zeigt kaufen automatisch die 200 % Skalierung erforderlich erhält, um Inhalte auf einfache Weise sichtbar machen.

2.  **Pro Monitor DPI:** Windows 8.1 legt verschiedene Skalierungsfaktor für verschiedene Bildschirme und entsprechend Content skalieren können. Windows 8 wird nur einen einzelnen Skalierungsfaktor, der auf alle zeigt angewendet wird. Dieses Feature wird sichergestellt, dass Benutzer mit Hochauflösenden Geräten (d. h., 150 % und Laptops Skalierung von 200 %), die project oder ihren Geräten mit konventionellen 100 % Skalierung Projektoren und desktop Monitore Anzeige ordnungsgemäß Andocken Inhalte auf diese Bildschirmen angepasst.

### <a name="span-idhowthesechangesimpactenterpriseusersspanspan-idhowthesechangesimpactenterpriseusersspanspan-idhowthesechangesimpactenterpriseusersspanhow-these-changes-impact-enterprise-users"></a><span id="How_these_changes_impact_enterprise_users"></span><span id="how_these_changes_impact_enterprise_users"></span><span id="HOW_THESE_CHANGES_IMPACT_ENTERPRISE_USERS"></span>Wie diese Änderungen Unternehmensbenutzer beeinflussen

Für die Benutzer auf Laptops mit 100 % skalieren haben geänderten Features Windows 8.1 keine Auswirkung. Für Benutzer, die neue Geräte erwerben, die Hochauflösenden haben, bietet Windows 8.1 einen entscheidender Vorteil.

Es ist möglich, dass einige Benutzer erwerben Geräte, die dazwischen liegenden, fallen mit Windows Skalierung von 125 %. Der Benutzer oder die IT-Experten so konfigurieren sie ordnungsgemäß oder Update/Tweak Anwendungen zur Verbesserung der Verwendbarkeit, können diese Geräte erforderlich. Der Abschnitt zur Problembehandlung in diesem Thema kann IT-Experten, die diese Systeme, diese Anwendungen zu identifizieren und verpflichten sich die richtigen Risikominderung Taktiken helfen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hochauflösenden Unterstützung für IT-Experten](high-dpi-support-for-it-professionals.md)

 

 






