---
title: Device.Input.Digitizer
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 8e01ce2454bd09b575ddabdffa44b74bde6c2c34
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceinputdigitizer"></a>Device.Input.Digitizer
 
 - [Device.Input.Digitizer.Base](#device.input.digitizer.base)
 - [Device.Input.Digitizer.Pen](#device.input.digitizer.pen)
 - [Device.Input.Digitizer.PrecisionTouchpad](#device.input.digitizer.precisiontouchpad)

<a name="device.input.digitizer.base"></a>
## <a name="deviceinputdigitizerbase"></a>Device.Input.Digitizer.Base

### <a name="deviceinputdigitizerbasecontactreports"></a>Device.Input.Digitizer.Base.ContactReports

*Digitizer Zuverlässigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Device.Digitizer.Touch.NoiseSupression**bezeichnet.

Ein Digitizer darf nur Report-Daten, die von Benutzereingaben entspricht. Keine anderen Daten, die als "Objekts" oder "Ghost Kontakte" bezeichnet werden mitgeteilt. Dies gilt sowohl, wenn das System aktiv empfängt Benutzereingaben und wann keine Benutzereingaben erhält und unter AC und DC Power conditions (sofern zutreffend).

### <a name="deviceinputdigitizerbasehidcompliant"></a>Device.Input.Digitizer.Base.HIDCompliant

*HID kompatible Gerätefirmware und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Gerät bezeichnet. Digitizer.Touch.HIDCompliantFirmware**

Alle Digitalisierungsgeräte müssen Funktionsspezifikation für ihre jeweiligen Verwendung zu Bericht Eingabe für Windows und werden Eingabegeräte (HID) kompatibel.

Die Device.Input.Digitizer.Base.ThirdPartyDrivers Weitere Informationen finden Sie bei der Verwendung der Posteingang HID Mini Port Treiber Vs 3<sup>rd</sup> Partei HID Mini Port Treiber.

Weitere Informationen zur Implementierung finden Sie unter:

Die Berichten Anforderungen finden Sie unter der Themen am [ *http://msdn.microsoft.com/en-us/library/windows/hardware/jj151569.aspx* -Auflistung](http://msdn.microsoft.com/en-us/library/windows/hardware/jj151569.aspx)

HID über I2C Anforderungen finden Sie unter [ *http://msdn.microsoft.com/en-us/library/windows/hardware/Dn642101.aspx*](http://msdn.microsoft.com/en-us/library/windows/hardware/Dn642101.aspx)

HID über USB-Anforderungen, finden Sie unter [ *http://www.usb.org/developers/devclass\_Dokumente/HID1\_11. Pdf*](http://www.usb.org/developers/devclass_docs/HID1_11.pdf)

HID über Bluetooth-Anforderungen, finden Sie unter [ *http://developer.bluetooth.org/TechnologyOverview/Documents/HID\_SPEC.pdf*](http://developer.bluetooth.org/TechnologyOverview/Documents/HID_SPEC.pdf)

**Unternehmensvorgabe**

Das Gerät HID (Human Interface)-Protokoll ist der erkannten Industriestandard, die Microsoft für Eingabegeräte erforderlich sind. Dadurch wird sichergestellt, Windows-Kompatibilität und Wartungsfreundlichkeit bei jeder anderen kompatibler Treiber-Lösung.

### <a name="deviceinputdigitizerbasethirdpartydrivers"></a>Device.Input.Digitizer.Base.ThirdPartyDrivers

*Wartung und 3<sup>rd</sup> Partei Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

*Anwendungsbereich: "Windows Desktop"*

Wenn ein Windows Genauigkeit Touchpad Digitizer nutzt eine 3rd HID Mini-Port-Treiber von Drittanbietern, Teil der OEM des Protokollversands-Bild (und Wiederherstellungsabbild) und auf Windows Update verfügbar sein muss. Alle 3. HID Mini Port Treiber sind auch in Windows PE funktionsfähig sein. Es wird dringend empfohlen, dass ein Posteingang HID Mini-Port-Treiber nach Möglichkeit für Windows Genauigkeit Touchpad Implementierungen ausgelastet ist.

Hinweis: ein Touchpad nicht vermarktet werden als einem Windows Genauigkeit Touchpad, wenn alle anwendbaren Kompatibilität Anforderungen erfüllt sind.

Tippen Sie auf alle integrierten Windows und Stift Geräte festgelegt ohne die Verwendung von jedem 3. Partei HID Mini Port voll funktionsfähig sein oder Filtertreiber bereitgestellt, dass eine für den zugeordneten Bus verwendet für Konnektivität verfügbar ist. Während es wird empfohlen, dass ein Gerät geliefert werden, während der Tests, OEM einstellen, kann einen Windows-10-Treiber Mini Port kompatibel HID ausgeliefert und/oder Filtertreiber, der zusätzliche Funktionen bereitstellt, nachdem das Gerät alle erfüllt verknüpften HLK Anforderungen einschließlich **Device.Input.Digitizer.Base.ThirdPartyDrivers** , vorausgesetzt, dass alle anderen Anforderungen erfüllt sind, bei der Installation von diesem Treiber. Alle 3<sup>rd</sup> Partei HID Mini-Port-Treiber die in Instanzen verwendet wird, in dem ein Posteingang Treiber nicht für den Bus steht-Konnektivität ausgewählt, Treiber Teil der OEM des Protokollversands-Bild (und Wiederherstellungsabbild) und auf Windows Update verfügbar sein. Alle 3. HID Mini Port Treiber sind auch in Windows PE funktionsfähig sein.

*Anwendungsbereich: "Windows Mobile"*

Wenn Sie eine Windows Genauigkeit Touchpad, integrierte Touch oder integrierte Stift Digitizer nutzt so eine 3rd HID Mini-Port-Treiber von Drittanbietern, Teil des OEM Base Support Paket (BSP) für das System. Es wird dringend empfohlen, dass ein Posteingang HID Mini-Port-Treiber möglichst ausgelastet ist.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass immer Digitalisierungsgeräte für Benutzereingaben unabhängig davon warten Szenarien und oder Neuinstallationen verfügbar sind. Instanzen, in der Digitizer die einzige Quelle von Benutzereingaben für ein bestimmtes Gerät möglicherweise nicht, sind vorhanden

<a name="device.input.digitizer.pen"></a>
## <a name="deviceinputdigitizerpen"></a>Device.Input.Digitizer.Pen

### <a name="deviceinputdigitizerpenaccuracy"></a>Device.Input.Digitizer.Pen.Accuracy

*Kontakt Genauigkeit Stift*

|                |                            |
|----------------|----------------------------|
| Ziel-Funktion | Device.Input.Digitizer.Pen |

**Beschreibung**

Mit dieser Anforderung wurde die Anforderung Device.Digitizer.Pen.HoverAccuracy zusammengeführt.

Wenn Stift Tipp in Kontakt mit dem Bildschirm ist, wird das Delta zwischen den tatsächlichen Speicherort Kontakt und was meldet das Gerät sein:

-   &lt;= +/-0,5 mm (Center)

-   &lt;= +/-1 mm (innerhalb von 3,5 mm alle Ränder)

Wenn bewegt (mit Tipp nicht in Kontakt) des physischen Deltas zwischen physischen Standort und was das Gerät meldet muss &lt;= +/-1 mm (Center).

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit DirectInk und Posteingang Stift Erfahrungen; insbesondere:

-   Wenn der Stift in Kontakt mit dem Bildschirm gewährleisten, dass diese Freihandeingabe ist scheint stammen aus der Stiftspitze und gewährleisten, dass Möglichkeit zum Ziel kleine Steuerelemente.

-   Wenn der Stift bewegt wird, über den Bildschirm, um sicherzustellen, dass der Cursorposition genau vom Benutzer wahrgenommen wird

### <a name="deviceinputdigitizerpenbuffering"></a>Device.Input.Digitizer.Pen.Buffering

*Mit hoher Resume-Wartezeit Pufferung für Bus*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies ist eine Anforderung "If implementiert". Aktiven Stift Lösungen, mit denen einen Bus mit hoher Wartezeit fortsetzen, wie USB mit selektive anhalten oder Bluetooth darf einen input Bericht Puffer verarbeiten können implementieren &gt;= 100 ms Daten.

Eingabe Bericht Puffergröße (in Bytes) = Größe des Berichts Eingabe &times; (100 ms/maximal Bericht Rate)

Dies ist zwar eine Voraussetzung für Geräte, die einen Bus mit hoher Resume Wartezeit verwenden, empfiehlt es sich auch implementieren Lösungen, die anderen Bus verwenden einen Puffer input Bericht um Interrupt Verarbeitung Probleme zu vermeiden, die auftreten können.

**Unternehmensvorgabe**

Aufgrund der Hostcontroller oder Bus Resume Zeiten Energiesparmodus Staaten müssen Geräte, um sicherzustellen, dass keine Benutzerdaten Interaktion während Power Übergänge unterbrochen werden Pufferung zu implementieren.

### <a name="deviceinputdigitizerpencontactreports"></a>Device.Input.Digitizer.Pen.ContactReports

*Digitizer Zuverlässigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Device.Digitizer.Touch.NoiseSupression** bezeichnet.

Ein Digitizer darf nur Report-Daten, die von Benutzereingaben entspricht. Keine anderen Daten, die als "Objekts" oder "Ghost Kontakte" bezeichnet werden mitgeteilt. Dies gilt sowohl, wenn das System aktiv empfängt Benutzereingaben und wann keine Benutzereingaben erhält und unter AC und DC Power conditions (sofern zutreffend).

### <a name="deviceinputdigitizerpencustomgestures"></a>Device.Input.Digitizer.Pen.CustomGestures

*Benutzerdefinierte Laufzeitfehler System Gesten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Unabhängig von der Implementierung Berichte der, zusätzliche benutzerdefinierte Laufzeitfehler Stift Gesten mit Ausnahme von Remoteaktivierung Gesten nicht zulässig sind.

**Unternehmensvorgabe**

Diese Anforderung wird die Kompatibilität mit DirectInk sichergestellt.

-   Wird sichergestellt, dass keine Beeinträchtigung durch die Erfahrung Freihandeingabe Core vorhanden ist.

-   Gewährleistet Kompatibilität mit dem Posteingang Gestik-Modul.

### <a name="deviceinputdigitizerpeneraser"></a>Device.Input.Digitizer.Pen.Eraser

*Radierer Aufforderungscharakter*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Eine integrierte Windows-Stift-Lösung hat eine Aufforderungscharakter Hardware auf den Stift, die als Radierer-Funktionen kompatibel mit dem Protokoll zugeordnete bereitstellt. Die Funktionalität Erase muss standardmäßig aktiviert sein.

Microsoft ermöglicht eine Ausnahme für den aktiven Stifte, die nur eine einzigen Lauf Schaltfläche bis 01 Januar 2016 unterstützen: 

Microsoft empfiehlt, dass alle Stifte Erase Funktionalität standardmäßig unterstützen.  Integrierte Windows-Stift-Lösung, die Unterstützung für nur einen einzigen Lauf Schaltfläche enthält die, ohne ein Radierer Aufforderungscharakter bis 1 Januar 2016 liefern zulässig.  Nach Januar 1, 2016 eine integrierte Windows-Stift-Lösung hat eine Aufforderungscharakter Hardware auf der Stift, der Radierer kompatibel mit dem Protokoll zugeordnete Funktionalität und die Erase-Funktionalität standardmäßig aktiviert werden muss.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass Interaktionen mit dem Stift intuitiv und effizient sind. Auf diese Weise können Softwareentwickler für Radierer Funktionen während der verbleibenden unabhängig an die Implementierung der Radierer zu entwickeln.

Hinweis: Aktiven Stifte, die als Radierer-Funktionalität aktivieren bieten die beste Möglichkeit, digitalen Freihand gelöscht wird.  Aktive Stifte, die als Radierer-Funktionalität aktivieren frei auch den Anwendungsentwickler zum Entwickeln von Benutzeroberfläche zum Stift Kontext aus Freihandmodus wechseln zu müssen, um Modus zu löschen.  Aus diesem Grund wird empfohlen, dass alle Stifte Erase Funktionalität unterstützen in der Standardeinstellung.

### <a name="deviceinputdigitizerpenhidcompliant"></a>Device.Input.Digitizer.Pen.HIDCompliant

*Kompatible Gerätefirmware HID und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Device.Input.Digitizer.Base.HIDCompliant.

### <a name="deviceinputdigitizerpenhoverrange"></a>Device.Input.Digitizer.Pen.HoverRange

*Bereich beim Daraufzeigen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Pen.PenRange bezeichnet.

Ein Digitizer-Stift berichtet den Speicherort der Stift und dass er *im Bereich* beginnend mit dem Stift Tipp mindestens 5 mm anderen Bildschirm ist.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit DirectInk und genauer gesagt:

-   Stellt sicher, dass Benutzer auf dem Bildschirm empfangen Feedback bezüglich der Stift Speicherort und Tool Kontext in kurzer Zeit.

-   Gewährleistet Kompatibilität mit Windows Palm Ablehnung-Funktionalität.

### <a name="deviceinputdigitizerpenjitter"></a>Device.Input.Digitizer.Pen.Jitter

*Jitter und Linearität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Gemeldete Jitter aus einem integrierten Windows-Stift festgelegt sein:

-   Verschieben von Jitter

    -   &lt;= +/-0,4 mm (Center)

    -   &lt;= +/-0,6 mm (innerhalb von 3,5 mm alle Ränder)

-   Briefpapier Jitter

    -   &lt;= +/-0,3 mm (Center)

    -   &lt;+/-0,5 mm (innerhalb von 3,5 mm alle Ränder) =

-   Bewegen Sie den Mauszeiger Briefpapier Jitter &lt;= +/-0,5 mm (Center)

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit DirectInk und genauer gesagt:

-   Wenn Stift Tipp ist in Kontakt mit dem Bildschirm und verschieben, gibt Freihand exakt tatsächlichen Stiftstriche des Benutzers

-   Wenn der Stift Briefpapier (entweder wenn es sich im Kontakt mit dem Bildschirm oder hovering) gehalten wird, ist nicht Jitter wahrnehmbar für den Benutzer.

### <a name="deviceinputdigitizerpenlatency"></a>Device.Input.Digitizer.Pen.Latency

*Antwort Wartezeiten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Stift Digitalisierungsgeräte sind Antwort Wartezeiten pro Folgendes:

-   Kalt Boot Wartezeit

    -   Eine integrierte Windows-Stift wird sofort ausgeführt, sondern werden, nachdem die Anzeige aktiv ist

    -   Kalt Boot ist als den Zeitraum vom Anwendung von Power an den Controller definiert, bis der Controller HID Befehle akzeptieren kann

-   Nach-unten-Wartezeit (im Leerlauf) &lt;= 150ms (If-implementierte)

    -   Diese Anforderung ist anwendbar, wenn ein Status im Leerlauf implementiert wurde

    -   Nach unten Wartezeit (Idle) ist definiert als die Verzögerung zwischen dem Stift anfänglichen Kontaktaufnahme mit dem Bildschirm, wenn das Gerät in einen Zustand im Leerlauf ist und mit dem zugehörigen Bericht an den Host übermittelt.

-   Nach-unten-Wartezeit (aktiv) &lt;= 35ms (Center)

    -   Nach-unten-Wartezeit (aktiv) ist definiert als die Verzögerung zwischen der Stift anfänglichen Kontaktaufnahme mit dem Bildschirm, wenn das Gerät in einen aktiven Power Zustand ist und mit dem zugehörigen Bericht an den Host übermittelt.

-   Verschieben der Wartezeit &lt;= 30ms (Center)

    -   Zwar eine Info Stift in Motion (und in Kontakt mit dem Bildschirm), verschieben Latenz ist definiert als die Verzögerung zwischen dem Stift wird an einem physischen Standort und die zugeordnete müssen Bericht an den Host übermittelt.

**Unternehmensvorgabe**

Diese Bedingung stellt sicher:

-   Geräte werden nach der ein System Power Statusübergang für Benutzerinteraktionen immer leicht zugänglich sind.

-   Wenn Stift ersten Kontakt mit dem Bildschirm ernannt werden, ist Zeitabstand in visuelles Feedback nicht wahrnehmbar den meisten Benutzern.

-   Wenn Stift in Kontakt mit dem Bildschirm und zum Verschieben, End-to-End Wartezeit von Freihand und andere Interaktionen ist sind nicht für die meisten Benutzer wahrnehmbar.

### <a name="deviceinputdigitizerpenpressure"></a>Device.Input.Digitizer.Pen.Pressure

*Druck Reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Stift Digitalisierungsgeräte berichtet &gt;= 256 Ebenen der Druck.

Eine logarithmische Kurve muss die angewendete Kraft in der QuickInfo Stift Unwichtigstes verwendet werden. Wenn Stift Tipp in Kontakt mit dem Bildschirm ist, und die Aktivierung Force überschritten wurde, sollte das Gerät die Option Tipp als Set melden. Ist die maximale Aktivierung Force für eine integrierte Windows-Stift &lt;= 20g.

Die ideale Druck Kurve (bei einem Gerät mit 256 Ebenen) ist jedoch die zugeordneten HLK Tests sicherstellen, dass das Gerät innerhalb der von der Obergrenze und Untergrenze definierten Bereiche Druck Berichten in Abbildung 1 dargestellt. Für Geräte, die größere Anzahl von Ebenen Druck haben, sollte die derselben Kurve angeordnet bleibt angewendet jedoch auf die Anzahl der Ebenen logisch gemeldet skaliert.

**Abbildung 1: Ideal Druck Reporting Kurve für ein Gerät mit 256 Druck Ebenen**
![Ideal Druck Berichten Kurve für ein Gerät mit 256 Druck Ebenen](images/ideal-pressure-reporting-curve.png)



**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit DirectInk und genauer gesagt:

-   Sorgt für ausreichende Granularität und Darstellung Abweichung in Druck wie während der Freihandeingabe vom Benutzer wahrgenommen.

### <a name="deviceinputdigitizerpenreportrate"></a>Device.Input.Digitizer.Pen.ReportRate

*Bericht Rate*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Pen.100HzSampleRate bezeichnet.

Eine integrierte Windows-Stift-Digitizer hat eine Bericht Rate &gt;= 133Hz.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit DirectInk und genauer gesagt:

-   Stellt sicher, dass genügend Punkte als Stichprobe verwendet werden, um bei normalen Handschrift Geschwindigkeitsinformationen genau darstellen.

### <a name="deviceinputdigitizerpenresolution"></a>Device.Input.Digitizer.Pen.Resolution

*Input Lösung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Pen.PenResolution bezeichnet.

Ein Stift Digitizer Lösung muss Eingabe des &gt;= die systemeigene Auflösung oder 150 dpi (je größer ist).

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass jedes Pixel auf Bildschirm gezeichneten werden kann und eine reibungslose Stift bietet.

### <a name="deviceinputdigitizerpenthirdpartydrivers"></a>Device.Input.Digitizer.Pen.ThirdPartyDrivers

*Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

Finden Sie unter Device.Input.Digitizer.Base.ThirdPartyDrivers.

<a name="device.input.digitizer.precisiontouchpad"></a>
## <a name="deviceinputdigitizerprecisiontouchpad"></a>Device.Input.Digitizer.PrecisionTouchpad

### <a name="deviceinputdigitizerprecisiontouchpadaccuracy"></a>Device.Input.Digitizer.PrecisionTouchpad.Accuracy

*Genauigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Genauigkeit Touchpad berichtet die Digitizer absolute Position &lt;= 2 mm von tatsächlichen Position für alle Kontakte.

**Unternehmensvorgabe**

Anforderung wird eine genaue moussing und gesturing Fläche sichergestellt.

### <a name="deviceinputdigitizerprecisiontouchpadbuffering"></a>Device.Input.Digitizer.PrecisionTouchpad.Buffering

*Pufferung für Bus mit hoher Resume-Wartezeit.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies ist eine Anforderung "If implementiert". USB- oder Bluetooth verbunden Windows Genauigkeit Touchpad darf einen input Bericht Puffer verarbeiten können implementieren &gt;= 100 ms basierend auf die maximale Anzahl von Kontakten, die vom Gerät Eingabe Bericht Puffergröße (in Bytes) unterstützt:

= Maximale \# von Kontakten unterstützt &times; Größe des Berichts Eingaben &times; (100 ms/Maximum Bericht Rate)

Während dieser Anforderung USB und Bluetooth-Geräte angewendet, empfiehlt es sich, dass andere Geräte implementieren auch einen Puffer input Bericht um Interrupt Verarbeitung Probleme zu vermeiden, die auftreten können.

**Unternehmensvorgabe**

Aufgrund der Hostcontroller oder Bus Resume Zeiten Energiesparmodus Staaten müssen Geräte, um sicherzustellen, dass keine Benutzerdaten Interaktion während Power Übergänge unterbrochen werden Pufferung zu implementieren.

### <a name="deviceinputdigitizerprecisiontouchpadbuttons"></a>Device.Input.Digitizer.PrecisionTouchpad.Buttons

*Physische Schaltflächen und Schaltfläche reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die folgenden Anforderungen müssen diese Anforderung zusammengeführt wurden:

-   Device.Input.PrecisionTouchpad.Hardware.ClickpadPress
-   Device.Input.PrecisionTouchpad.Hardware.PressurePadPress

Wenn Windows Genauigkeit Touchpad externe Schaltflächen implementieren und sind nicht Clickpads oder Pressurepads, muss es mindestens zwei Schaltflächen zur Darstellung von links, und klicken Sie mit der rechten Maustaste auf die Schaltflächen.

Wenn mehr als eine Schaltfläche vorhanden ist, werden die Schaltflächen als ein Array von Schaltfläche Flags mitgeteilt. Behandeln von Schaltflächen hinter den ersten beiden (primäre und sekundäre Klicks) sollte die Rolle der Treiber und/oder Maus-Auflistung sein.

(Sofern implementiert) – sowohl Clickpad und nicht-Clickpad-basierten Windows Genauigkeit Touchpad berichtet eine Schaltfläche Schließen, wenn ausgeübten Druck 150 g - 180 g überschreitet.  Dies ist am 140 g - 190 g, um Fertigung Abweichung tolerieren getestet.

**Unternehmensvorgabe**

Tabellentitel Regionen sollten problemlos verwendet werden.

Externe Schaltflächen implementiert werden, muss mindestens zwei Tasten sowohl Links darstellen, und klicken Sie mit der rechten Maustaste, um sicherzustellen, dass das Gerät vollständige Maus-Funktionen verfügt.

### <a name="deviceinputdigitizerprecisiontouchpadcontactreports"></a>Device.Input.Digitizer.PrecisionTouchpad.ContactReports

*Digitizer Zuverlässigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Device.Digitizer.Touch.NoiseSupression** bezeichnet.

Ein Digitizer darf nur Report-Daten, die von Benutzereingaben entspricht. Keine anderen Daten, die als "Objekts" oder "Ghost Kontakte" bezeichnet werden mitgeteilt. Dies gilt sowohl, wenn das System aktiv empfängt Benutzereingaben und wann keine Benutzereingaben erhält und unter AC und DC Power conditions (sofern zutreffend).

### <a name="deviceinputdigitizerprecisiontouchpadcontacttipswitchheight"></a>Device.Input.Digitizer.PrecisionTouchpad.ContactTipSwitchHeight

*Kontakt Tipp Switch Höhe*

Windows Genauigkeit Touchpad berichtet Kontakte nicht &gt; 0,5 mm oberhalb der Digitizer Fläche.

**Unternehmensvorgabe**

Verhindert, dass die unbeabsichtigte Kontakte Aktivierungen auftritt, und trägt dazu bei, um während der Eingabe Palm aufgerufen Aktivierungen zu vermeiden.

### <a name="deviceinputdigitizerprecisiontouchpaddevicetypereporting"></a>Device.Input.Digitizer.PrecisionTouchpad.DeviceTypeReporting

*Gerätetyp*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Genauigkeit Touchpad müssen ihre Schaltfläche Gerätetyp (z. B. Druck Pad, klicken Sie auf Pad) über einen HID Feature Bericht melden, wenn eine Schaltfläche unter Digitizer vorhanden ist.  Ein Gerät, das nicht über einen Tabellentitel Digitizer verfügt muss dieses Feature Bericht nicht verfügbar.

Weitere Informationen zur Implementierung finden Sie unter [http://msdn.microsoft.com/en-us/library/windows/hardware/jj126202.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/jj126202%28v=vs.85%29.aspx)*.* 

**Unternehmensvorgabe**

Grundlegenden, um sicherzustellen, dass die richtigen Schaltfläche Handhabung wird vom Betriebssystem ausgeführt.

### <a name="deviceinputdigitizerprecisiontouchpaddimensions"></a>Device.Input.Digitizer.PrecisionTouchpad.Dimensions

*Dimensionen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die Anforderung **Device.Input.PrecisionTouchpad.Hardware.Length** und **Device.Input.PrecisionTouchpad.Hardware.Height** wurden mit diesem zusammengeführt.

Windows Genauigkeit Touchpad muss &gt;= 64 mm Länge (horizontale Messung der Touchpad) X &gt;= 32 mm (vertikale Wert).

**Unternehmensvorgabe**

Precision Touchpad muss eine minimale Größe, um Benutzern ordnungsgemäß Interaktion mit über weite entfernungen hinweg eine moussing und ausführen, die mit mehreren Finger Gesten verwalten.

### <a name="deviceinputdigitizerprecisiontouchpadfingerseparation"></a>Device.Input.Digitizer.PrecisionTouchpad.FingerSeparation

*Mit dem Finger voneinander getrennt zu halten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Input.PrecisionTouchpad.Performance.MinSeparation bezeichnet.

Windows Genauigkeit Touchpad darf nicht alias zwei Kontakte an eine minimale Trennung von 8mm oder weniger Edge-Edge-ausgerichtet.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, mit dem Finger Count und Position bleiben bei Interaktionen mit mehreren Finger präzise.

### <a name="deviceinputdigitizerprecisiontouchpadhidcompliant"></a>Device.Input.Digitizer.PrecisionTouchpad.HIDCompliant

*Kompatible Gerätefirmware HID und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Device.Input.Digitizer.Base.HIDCompliant.

### <a name="deviceinputdigitizerprecisiontouchpadinputresolution"></a>Device.Input.Digitizer.PrecisionTouchpad.InputResolution

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Genauigkeit Touchpad berichtet logische maximal für x linear proportional zu der Breite des Touchpads und logische maximal für y linear proportional zum die Länge des Touchpads berichtet. Die obere linke Ecke des Touchpads muss der Ursprung (0,0) sein. Alle Windows Genauigkeit Touchpad sind mindestens 300 dpi. aus diesem Grund für die Mindestgröße Windows Genauigkeit Touchpad die logische maximale x festgelegt sein &gt;= 767 und die logische maximal für y ist &gt;= 384.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass Benutzer genaue Bearbeitung und Positionieren des Cursors durchführen können.

### <a name="deviceinputdigitizerprecisiontouchpadjitter"></a>Device.Input.Digitizer.PrecisionTouchpad.Jitter

*Jitter und Linearität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Mit dieser Anforderung wurde die Anforderung Device.Input.Digitizer.PrecisionTouchpad.Linearity zusammengeführt.

Einen Kontakt

-   Windows Genauigkeit Touchpad berichtet keine Jitter, wenn ein Kontakt Briefpapier mit einfacher Genauigkeit auf der Oberfläche Digitizer ist.

Mehrere Kontakte

-   Windows Genauigkeit Touchpad berichtet Kontakte mit &lt;= 2mm von Jitter bei mehreren Kontakten Briefpapier anfänglich auf der Oberfläche Digitizer platziert werden, jedoch keine Briefpapier Jitter zulässig ist, nachdem die Kontakte werden wieder Briefpapier und verschoben haben.

Eine beliebige Anzahl von Kontakten

-   Windows Genauigkeit Touchpad unterhält Linearität 0,5 mm, für alle Kontakte, die horizontal, vertikal und diagonal über Kante zu Kante Geschäftsreisen gemeldet.

-   3,5 mm der Begrenzung unterhält Genauigkeit Touchpad Linearität 1,5 mm für alle Kontakte gemeldet.

-   Windows Genauigkeit Touchpad berichtet keine rückwärts Motion Jitter für Kontakte in Bewegung. Rückwärts Jitter wird als nachfolgende Bericht des Kontakts Speicherorts in entgegengesetzter Richtung des Kontakts Reisekosten definiert.

**Unternehmensvorgabe**

Wird sichergestellt, dass moussing Genauigkeit und Gesten ordnungsgemäß funktionieren und Anhalten während gesturing keine Steuerelemente Jitter-Wert ergibt.

### <a name="deviceinputdigitizerprecisiontouchpadlatency"></a>Device.Input.Digitizer.PrecisionTouchpad.Latency

*Antwort Wartezeiten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die folgenden Anforderungen müssen diese Anforderung zusammengeführt wurden:

-   Device.Input.PrecisionTouchpad.Performance.ActiveTouchdownLatency

-   Device.Input.PrecisionTouchpad.Performance.IdleTouchdownLatency

-   Device.Input.PrecisionTouchpad.Performance.PanLatency

Drücken der Wartezeit:

-   Aktiv:

    -   Windows Genauigkeit Touchpad hat &lt;= 35 ms Touch nach unten Wartezeit im Zustand aktiv. Touch nach unten Wartezeit ist definiert als die Zeit zwischen Kontakt mit der Digitizer und den nachfolgenden input Bericht vom Host empfangen wird.

-   Leerlauf:

    -   Windows Genauigkeit Touchpad hat &lt;= 150 ms Touch nach unten Wartezeit im Leerlauf.

    -   Touch nach unten Wartezeit ist definiert als die Zeit zwischen Kontakt mit der Digitizer und den nachfolgenden input Bericht vom Host empfangen wird.

Wartezeit zu verschieben:

-    Windows Genauigkeit Touchpad hat panning Wartezeit &lt;70 ms =. Panning Wartezeit ist definiert als der Zeitraum zwischen der Bewegung auf dem Digitizer und die nachfolgenden Änderung vom Host empfangenen Audiodaten.

Kalt Boot Wartezeit:

-    Windows Genauigkeit Touchpad muss sofort ausgeführt, sondern sein, nachdem die Anzeige auf künftige vom kalt Boot-Systemen aktiv ist. Kalt Boot ist definiert als den Zeitraum vom Anwendung von Power an den Controller, bis der Controller HID Befehle akzeptieren kann.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass Core Benutzererlebnis büroumzüge tippen moussing, gesturing sind weiterhin leistungsfähige (d. h., tippen Sie eine Schaltfläche-Steuerelement, Hyperlink, usw..).

Das Gerät Touchpad sollte immer leicht zugänglich sind für Benutzereingaben, sobald das System gestartet oder aus einem Energiesparmodus unabhängig von der Konnektivität Bus fortgesetzt wurde.

Zusätzliche UX-Studie auf die Auswirkungen der Wartezeit bei der indirekten Eingabegeräte panning Blocksatz erhöhte Verschiebemodus Wartezeit im Vergleich zum direkten Eingabegeräte gilt.

### <a name="deviceinputdigitizerprecisiontouchpadminmaxcontacts"></a>Device.Input.Digitizer.PrecisionTouchpad.MinMaxContacts

*Wenden Sie sich an count*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Genauigkeit Touchpad berichtet nicht mehr als ein Maximum von 5 eindeutige Kontakte unterstützt wird. Windows Genauigkeit Touchpad wird gemeldet wird, kann (und in der Lage sein) mindestens 3 eindeutige Kontakte zu unterstützen.

**Unternehmensvorgabe**

Precision Touchpad erfordern mindestens drei Finger Zugriff auf alle Windows Interaktionen haben. Für eine größere Anzahl von verfügbaren Interaktionen sind mindestens vier Fingern unterstützt. Multihand Interaktionen sind nicht für die Verwendung von Touchpad, sodass mehrere Kontakte die Unterstützung von 5 nicht mehr benötigte ist geeignet.

### <a name="deviceinputdigitizerprecisiontouchpadreportrate"></a>Device.Input.Digitizer.PrecisionTouchpad.ReportRate

*Bericht-Sätze*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Input.PrecisionTouchpad.Performance.ReportRate bezeichnet werden.

Windows Genauigkeit Touchpad berichtet an &gt;= 125Hz (und nicht mehr als 250Hz) Wenn ein Kontakt auf Digitizer befindet. Windows Genauigkeit Touchpad berichtet alle Kontakte bei &gt;= Anzeige Aktualisierungsrate + 10Hz (bis zu 125 Hz) wann sind mehrere Kontakte auf dem Digitizer.

**Unternehmensvorgabe**

Verwalten der Maus Erfahrung Anforderungen und hervorragende Performance bei &gt;125 Hz =. Das Gestik Leistung inline mit Touch-Anforderungen, die von den Anforderungen Erfahrung direkte Bearbeitung zur Vermeidung Korrekturen gesichert werden.

### <a name="deviceinputdigitizerprecisiontouchpadselectivereporting"></a>Device.Input.Digitizer.PrecisionTouchpad.SelectiveReporting

*Selektive reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Genauigkeit Touchpad haben die Anforderung Hosts über einen HID Feature Bericht selektiv Digitizer Kontakte und drückt die Schaltfläche Unwichtigstes zu unterstützen. Der Host kann die Empfangens von Berichten für entweder Digitizer Kontakte Tasten, weder oder beides anfordern. Windows Genauigkeit Touchpad ist ihre basierend auf der Auswahl des Stromverbrauchs optimieren.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass Precision Touchpad Digitalisierungsgeräte Konfiguration Benutzeranfragen So aktivieren oder deaktivieren Sie das Gerät ordnungsgemäß beantworten.

### <a name="deviceinputdigitizerprecisiontouchpadthirdpartydrivers"></a>Device.Input.Digitizer.PrecisionTouchpad.ThirdPartyDrivers

*Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Device.Input.Digitizer.Base.ThirdPartyDrivers.

 # <a name="deviceinputdigitizertouch"></a>Device.Input.Digitizer.Touch

### <a name="deviceinputdigitizertouchaccuracy"></a>Device.Input.Digitizer.Touch.Accuracy

*Genauigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Touch.PhysicalInputPosition bezeichnet.

Ein Berührungsdigitizer legt die Position der alle Kontakte in der folgenden Zertifikate Bericht:

-   &lt;Wenn Kontakt Speicherort größer als 3,5 mm vom Rand Digitizer ist = +/-1mm

-   &lt;Wenn Kontakt Speicherort innerhalb der Digitizer Kanten 3,5 mm ist = +/-2mm

**Unternehmensvorgabe**

Dadurch wird eine präzise und zuverlässige Touch-Interaktionen sichergestellt.

### <a name="deviceinputdigitizertouchbuffering"></a>Device.Input.Digitizer.Touch.Buffering

*Mit hoher Resume-Wartezeit Pufferung für Bus*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Dies ist eine Anforderung "If implementiert". Ein Windows touch-Lösung für die Verbindung über USB oder Bluetooth darf einen input Bericht Puffer verarbeiten können implementieren &gt;= 100 ms Daten basierend auf die maximale Anzahl von Kontakten, die vom Gerät unterstützt werden

Eingabe Bericht Puffergröße (in Bytes) (für die einzelnen Finger Hybrid Reporting): = Maximum \# des Kontakte unterstützt &times; Größe des Berichts Eingabe &times; (100 ms/maximal Bericht Rate)

Dies ist zwar eine Voraussetzung für Geräte, die einen Bus mit hoher Resume Wartezeit verwenden, empfiehlt es sich auch implementieren Lösungen, die anderen Bus verwenden einen Puffer input Bericht um Interrupt Verarbeitung Probleme zu vermeiden, die auftreten können.

**Unternehmensvorgabe**

Aufgrund der Hostcontroller oder Bus Resume Zeiten Energiesparmodus Staaten müssen Geräte, um sicherzustellen, dass keine Benutzerdaten Interaktion während Power Übergänge unterbrochen werden Pufferung zu implementieren.

### <a name="deviceinputdigitizertouchcontactreports"></a>Device.Input.Digitizer.Touch.ContactReports

*Digitizer Zuverlässigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Device.Digitizer.Touch.NoiseSupression** bezeichnet.

Ein Digitizer darf nur Report-Daten, die von Benutzereingaben entspricht. Keine anderen Daten, die als "Objekts" oder "Ghost Kontakte" bezeichnet werden mitgeteilt. Dies gilt sowohl, wenn das System aktiv empfängt Benutzereingaben und wann keine Benutzereingaben erhält und unter AC und DC Power conditions (sofern zutreffend).

### <a name="deviceinputdigitizertouchcustomgestures"></a>Device.Input.Digitizer.Touch.CustomGestures

*Benutzerdefinierte Laufzeitfehler System Gesten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Es dürfen nur sehr schwer umsetzbar entwickelt, um das System aktivieren. Benutzerdefinierte Benutzeroberflächenelemente entwickelt Gesten sind nicht zulässig.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass die Plattform eine konsistente und zuverlässige Gestik-Erfahrung auf allen Windows-Geräten verwaltet.

### <a name="deviceinputdigitizertouchfingerseparation"></a>Device.Input.Digitizer.Touch.FingerSeparation

*Mit dem Finger voneinander getrennt zu halten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Touch.InputSeparation bezeichnet.

Alle Kontakte eindeutig nachverfolgt werden muss und wann gemeldet &lt;= 8mm Abstand gemessen vom Edge-Edgeserver.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit Posteingang Gesten wie Pinch/mit mehreren Finger tippen, Zoom und parallel mit dem Finger Bearbeitung zuverlässig ausgeführt werden können.

### <a name="deviceinputdigitizertouchhidcompliant"></a>Device.Input.Digitizer.Touch.HIDCompliant

*Kompatible Gerätefirmware HID und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Device.Input.Digitizer.Base.HIDCompliant.

### <a name="deviceinputdigitizertouchjitter"></a>Device.Input.Digitizer.Touch.Jitter

*Jitter und Linearität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Touch.DigitizerJitter bezeichnet.

Ein Maximum von Briefpapier Jitter nicht überschreiten &lt;+/-außerhalb der Ränder von 0,5 mm = und &lt;+/-1 mm innerhalb der Kanten 3,5 mm =

Verschieben von Jitter darf maximal nicht überschreiten &lt;= +/-1mm Weg von der Ränder und &lt;+/-2 mm innerhalb der Kanten 3,5 mm =

Jitter ist nicht in eine beliebige Richtung gegenüber der Kontakt Geschäftsreisen für nicht-Briefpapier Kontakte zulässig.

**Unternehmensvorgabe**

Dadurch wird sichergestellt, Kompatibilität mit Posteingang Gesten, Bearbeitung und Freihand und genauer gesagt, die:

-   Tippen Sie auf Interaktionen mit kleine Steuerelemente funktionieren

-   Inhalt sollte nicht jitter, wenn nach der Bearbeitung Briefpapier gehalten wird.

-   Inhalt in der Richtung, die der Benutzer für die direkte Verwendung bearbeitet formfreies panning

-   Akzeptable sieht Finger zeichnen/Freihandeingabe

### <a name="deviceinputdigitizertouchlatency"></a>Device.Input.Digitizer.Touch.Latency

*Antwortzeit für Anfragen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Touch.ResponseLatency bezeichnet.

Ein Berührungsdigitizer sind Antwort Wartezeiten wie folgt:

<html>
    <ul>
        <li>
            <p>Nach-unten-Wartezeit (aktiv)&lt;= 35ms</p>
            <ul>
                <li><p>Aktiv nach unten Wartezeit ist definiert als der Zeitraum zwischen Kontakt mit Digitizer und die nachfolgenden input Bericht vom Host empfangenen Audiodaten.</p></li>
            </ul>
        </li>
        <li>
            <p>Nach-unten-Wartezeit (im Leerlauf) &lt;= 150ms</p>
            <ul>
                <li><p>Nach unten Wartezeit im Leerlauf ist definiert als der Zeitraum zwischen Kontakt mit der Digitizer und den nachfolgenden input Bericht vom Host empfangen wird, während der Digitizer standby verbunden ist.</p></li>
            </ul>
        </li>
        <li><p>Verschieben der Wartezeit</p>
            <table>
                <thead>
                    <tr class="header">
                        <th>Bildschirmgröße (Diagonal)</th>
                        <th>Maximale Wartezeit</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="odd">
                        <td>&lt;7"</td>
                        <td>&lt;= 35ms</td>
                    </tr>
                    <tr class="even">
                        <td>&gt;= 7"</td>
                        <td>&lt;= 25ms</td>
                    </tr>
                </tbody>
            </table>
        </li>

        <li><p>Move latency is defined as the period between a contact being at a physical position and having that position reported to the host.</p></li>

        <li>
            <p>Cold Boot Latency -</p>
            <ul>
                <li><p>Touch digitizers shall be immediately responsive once the display is active.  Cold boot is defined as the period from application of power to the controller until the controller is ready to accept HID commands.</p></li>
            </ul>
        </li>
    </ul>
    <p><strong>Business Justification</strong></p>
    <p>This requirement ensures the following:</p>
    <ul>
        <li><p>Content sticks close to the physical finger position when under manipulation.</p></li>
        <li><p>Devices are readily available for user interactions after a system power state transition.</p></li>
        <li><p>User interactions involving a tap are responsive even when in a low power state.</p></li>
    </ul>
</html>

### <a name="deviceinputdigitizertouchmincontactcount"></a>Device.Input.Digitizer.Touch.MinContactCount

*Minimale gleichzeitige betroffenen Kontakte*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als **Device.Digitizer.Touch.5TouchPointMinimum**bezeichnet.

Ein Berührungsdigitizer muss mindestens fünf gleichzeitige Touch-Kontakte unterstützen.

**Unternehmensvorgabe**

Diese Anforderung gewährleistet Kompatibilität mit Posteingang Gesten, Eingabehilfen und 3rd Party Applications.

### <a name="deviceinputdigitizertouchreportrate"></a>Device.Input.Digitizer.Touch.ReportRate

*Bericht rate*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung wurde früher als Device.Digitizer.Touch.ReportingRate bezeichnet.

Wenn in einem Zustand active Power wird die Touch Digitizer reporting Rate unter mindestens Aktualisierungsrate anzeigen und maximal 250 Hz verwaltet werden. Alle Berichte müssen eindeutig aufgenommen werden.

Beispiel:

| Anzeige Aktualisierungsrate | Tippen Sie auf Reporting Rate |
|----------------------|----------------------|
| 60Hz                 | &gt;= 60Hz           |
| 120Hz                | &gt;= 120Hz          |

**Unternehmensvorgabe**

Diese Anforderung gewährleistet als kompatible reibungslose und flimmerfreie gesturing beim Ausführen einer Schwenken und Pinch/Zoom Interaktionen mit dem Framework Windows direkte Bearbeitung.

### <a name="deviceinputdigitizertouchresolution"></a>Device.Input.Digitizer.Touch.Resolution

*Input Lösung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Mindestens die Touch Digitizer Auflösung werden die systemeigene Auflösung gleich oder größer. Jedes Pixel der Anzeige in einer integrierten Berührungsdigitizer ist erforderlich, tippen Sie auf Eingabe zugänglich sein. Jedes Pixel enthält Pixel auf die Ränder und in den Ecken des Bildschirms.
Weitere Details zur Überprüfung und Testen von dieser Anforderung finden Sie unter <http://go.microsoft.com/fwlink/?LinkID=234575>

**Unternehmensvorgabe**

Dadurch wird sichergestellt, dass jedes Pixel steht für die Fingereingabe Interaktion gewährleistet als zuverlässige und reibungslose Touch.

### <a name="deviceinputdigitizertouchthirdpartydrivers"></a>Device.Input.Digitizer.Touch.ThirdPartyDrivers

*Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Device.Input.Digitizer.Base.ThirdPartyDrivers.
