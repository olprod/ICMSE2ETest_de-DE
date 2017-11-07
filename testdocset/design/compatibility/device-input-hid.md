---
title: Device.Input.HID
Description: "Alle HID-Geräte über I2C verbundene müssen Microsoft HID I2C Protokoll Spezifikation entsprechen."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 193cc5b46d0229e1a4b85f520c6081014ee30184
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.HID

 - [Device.Input.HID](#device.input.hid)
-->

<a name="device.input.hid"></a>
##Device.Input.HID

### <a name="deviceinputhidi2cprotocolspeccompliant"></a>Device.Input.HID.I2CProtocolSpecCompliant

*Microsoft HID I2C Protokoll Spezifikation müssen alle HID-Geräte über I2C verbundene entsprechen.*

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

Alle HID über I2C kompatible Geräte einhalten müssen mit der Microsoft Dokumentation für die Angabe der HID I2C Protokoll veröffentlicht.

*Hinweise zum Entwurf*

Veröffentlichte HID I2C Protocol-Spezifikation (Hyperlink noch nicht bereitgestellt) von Microsoft finden Sie unter

Ausnahmen: Dieser Anforderung ist nur für Geräte HID I2C erzwungen und nicht allgemeiner für SP b (engl.).

### <a name="deviceinputhidusbspecificationcompliant"></a>Device.Input.HID.UsbSpecificationCompliant

*Alle HID-Geräte, die über USB verbunden sind entsprechen der USB-HID-Spezifikation (v1. 1 oder höher).*

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

Version 5: WMC AQ Anforderungen definiert

-   Für WMC AQ ist dieser Anforderung:

    -   ERFORDERLICH für desktop-Systeme

    -   ERFORDERLICH für Notebook-Systeme Wenn Laptopsystem Remote und Empfänger enthält.

-   Nicht AQ Systeme ist dieser Anforderung:

    -   ERFORDERLICH, wenn das System (Desktop- oder Laptopcomputer) Remote und Empfänger enthält.<br/><br/>

-   Infrarot-Empfänger (nur Eingabe) und Infrarot-Infrarottransceiver (Eingabe und Ausgabe von Infrarot-/ Learning) Schnittstelle mit dem Windows Media Center Klasse-Treiber. In einem System mit einer TV-Empfänger muss Infrarot-Infrarottransceiver verwendet werden, die alle Funktionen des Dokuments *Remote-Steuerung und Empfänger-Transceiver Spezifikationen und Anforderungen für Windows Media Center in Windows-Betriebssystemen* unterstützen.

-   Tunerless Systeme mit einem Infrarot-Empfänger sind nur Infrarot-Eingabe und Aktivierung Funktionen erforderlich. Die Infrarot-Lern- und Ausgeben von Funktionen sind optional.

-   Digitaltext Lösungen sind zur Unterstützung von erlernen und Ausgeben von nicht erforderlich. Diese Funktionen sind optional.

-   In Gebietsschemas, die keine Set-Top-Boxen verwenden, sind die Lern- und Ausgeben von Funktionen optional.

-   In diesen Regionen, die eine sekundäre 10 Fuß-Anwendung zu unterstützen, müssen die Infrarot-Empfänger/Infrarottransceiver nicht die Infrarot-Learning-Anforderung erfüllen.

-   In diesen Regionen, die DVB-S unterstützen, empfiehlt Microsoft die Verwendung von Infrarot-Infrarottransceiver (Eingabe und Ausgabe von Infrarot-/ Learning).

-   Wenn ein Laptopsystem ausgeliefert, ist Infrarot-Learning und Infrarot-ausgeben optional.

-   Für Infrarot-Empfänger (nur Eingabe), für die Verwendung von Microsoft Infrarot-Protokolle und alle Infrarot-Transceiver (Eingabe- und Emissionen Funktionen) autorisiert wird das Gerät Umschlägen Wellenform Infrarot-Software für die Software des Infrarot-Signals Decodierung zurückgeben. Ein Infrarot-Signal kann nicht in der Hardware decodiert werden. Die einzige Ausnahme ist die "Aktivierung von Remote" Power-Taste.

-   Einem Infrarot-Empfänger (nur Eingabe) ist zulässig, Hardware Decodierung des einer Infrarot-Signal ausführen. Diese Infrarot-Empfänger (nur Eingabe) müssen nicht empfangen und reagieren auf eine derzeit Microsoft IR Protocol autorisiert. Infrarot-Empfänger, die Hardware Decodierung, der ein Infrarot-Signal verwenden müssen auch zur Unterstützung der Funktionalität "Aktivierung von Remote". Diese Geräte müssen mit dem Remote *-Steuerelement und Empfänger-Transceiver Spezifikationen und Anforderungen für Windows Media Center in Windows-Betriebssystemen* Dokument erfüllen.

*Hinweise zum Entwurf*

Microsoft empfiehlt, Infrarot-Kabel mit der Bezeichnung und für Endbenutzer dokumentiert werden. Zeigt ein kleines Diagramm des Kabels Infrarot-Steuerelement und wie es stellt eine zur digitalen Kabels Verbindung oder Satellitenempfänger konnte verhindern, dass Anrufe beim Support verursachen einfügen.

