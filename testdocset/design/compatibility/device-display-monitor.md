---
title: Device.Display.Monitor
Description: "Anforderungen für zeigt, um sicherzustellen, dass eine gute End-User Experience vorgesehen."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7f97d30e15d7cfd1c7d9a522a9c3a850e2be2f1d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Display.Monitor

 - [Device.Display.Monitor](#device.display.monitor)
-->

<a name="device.display.monitor"></a>
##Device.Display.Monitor

### <a name="devicedisplaymonitorbase"></a>Device.Display.Monitor.Base

*Base-Anforderungen für zeigt müssen eine gute Endbenutzers sicherstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Sämtliche Verbinder auf dem Bildschirm müssen ein Modus, der nicht CE Formatvorlage Overscan anwenden oder underscan standardmäßig festgelegt werden. Es ist für den Bildschirm aus, geben Sie eine Option, um dem Benutzer so konfigurieren Sie mithilfe einer lokalen Bildschirmanzeige Overscan/Underscan zu ermöglichen.

Alle video zeigt, die einen Connector HDMI bereitstellen muss das Flag ITC unterstützen gemäß Definition in der Spezifikation HDMI.

Zeigt für alle digitalen werden benötigt, um einzelne HPD Signal Umstellung von niedrig, hoch auf Gerät Verbindung und hoch haben. Periodischen Umschalten des HPD Signals nach Verbindung oder Power up ist nicht zulässig. 

Mehrere Übergang Lead Datenquelle an das Betriebssystem mehrere Gerät hinzukommen und Entfernen des Ereignisses zu benachrichtigen; verursacht unerwünschte Modus blinkt festgelegt.

### <a name="devicedisplaymonitordigitallinkprotection"></a>Device.Display.Monitor.DigitalLinkProtection

*Bildschirme, die digitale Eingaben unterstützen müssen für alle digitalen Eingaben digitale Link Schutz unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Zeigt mit digitalen Eingaben, wie Digital Visual Interface (DVI), High-Definition Multimedia Interface, (HDMI), DisplayPort, usw.... muss ein digitaler Monitor Link Schutzmechanismen wie hoher Bandbreite digitalen Content Protection (HDCP) unterstützen.

### <a name="devicedisplaymonitoredid"></a>Device.Display.Monitor.EDID

*Eine Anzeigegeräts muss die EDID-Datenstruktur implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der Monitor muss eine Struktur EDID übertragen, die alle erforderlichen Felder gemäß der Definition in VESA Enhanced erweiterte Display Identification Data Standard (E-EDID), Version A, Abschnitt 3 enthält. Diese EDID muss auch eine eindeutige Name des Herstellers, Produkt Code-ID und Seriennummer enthalten. (Die Seriennummer ist nicht für eine integrierte Bereich auf einer mobilen oder alle in einem System erforderlich.)

Für analoge CRT-Monitore muss angeben, EDID Inhalt mindestens 75 Hz oder höher für jede unterstützte Auflösung VESA-Modus.

Alle Monitore müssen E EDID unterstützen, durch die Implementierung einer EDID 1.3 oder höher Datenstruktur, die:

-   Enthält für die bevorzugten Anzeigemodus Zeiterfassungsdaten in Timing \#1.

<!-- -->

-   Für eine LCD-Anzeige oder eine andere Anzeige mit festem Format ist diese Anzeigemodus den systemeigenen, stetig überprüften Modus des Bereichs.

-   Für andere Anzeigetypen ist dies optimale, stetig überprüften Anzeigemodus, der basiert auf der Größe und die Funktionen des Geräts und muss die Anforderungen für Aktualisierungsrate oben definierten erfüllen.

<!-- -->

-   Implementiert die Bildschirmgröße oder Seitenverhältnis Felder, 0x15 und 0 x 16 pro die unterstützte EDID Version mit genaue Dimensionen Bytes.

-   Legt Byte 0 x 18, Bit 1 an, dass die bevorzugte Modus Bedeutung pro die unterstützte Version EDID fest.

-   Enthält eine eindeutige fortlaufende Zahl in mindestens einer der das Feld ID Seriennummer oder eine Zeichenfolge zur Anzeige Seriennummer des Produkts in einem Basiskalender Block 18-Byte-Deskriptor.

-   Implementiert eine Anzeige Produktname-Zeichenfolge in einen Basiskalender Block 18-Byte-Deskriptor, optional für eine integrierte Systemsteuerung. Diese Zeichenfolge muss für die Verwendung von Benutzer-Schnittstelle geeignet.

-   Implementiert eine Anzeige Bereich Grenzwerte in einem von der Basis blockieren 18-Byte-gelangen, es sei denn, das Gerät eine Anzeige nicht zusammenhängenden Häufigkeit (Multi-Modus) ist.

Mobile und anderen Systemen all-in-One müssen eine EDID-Struktur in drei verschiedene Arten übertragen:

-   LCD-Anzeige enthält, einen extern angeschlossene Monitor vergleichbar ist.

-   Wenn die LCD-Anzeige nicht zur Verfügung stellt, ist der WDDM Miniport zum Definieren und Bereitstellen des Betriebssystems verantwortlich.

-   WDDM-Treiber möglicherweise ACPI ausgeführt \_DDC-Methode für das untergeordnete Gerät zum Abrufen einer EDID aus System-BIOS dem internen Bereich zugeordnet.

Zeigt Geräte, die Features implementiert, die mit mehr als 8 Bits pro primäre Textfarbe EDID 1.4 verwenden müssen, um sicherzustellen, dass diese Funktionen das Betriebssystem und Applikationen vermittelt werden können.

*Hinweise zum Entwurf*

Die ACPI-Spezifikation definiert die Methode, um die EDID vom BIOS gleichwertige Funktionalität gemäß ACPI 2.0 b, Anhang B, erzielt erwerben oder höher.

### <a name="devicedisplaymonitormodes"></a>Device.Display.Monitor.Modes

*Anforderung für die Unterstützung der Lösung für Anzeigegeräte*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein Anzeigegeräts kann mehrere Connectors verfügen. Im folgenden werden die erforderlichen Modi, dass eine Anzeige auf jedem Connector unterstützen muss, und geben Sie an, die Unterstützung über die EDID (eine Darstellung ist kostenlos zur Unterstützung von weiteren Modi und ihn in die EDID sowie out anrufen).

HINWEIS: In Windows 10 wird keine Minimale Aktualisierungsrate benötigt. Für systemeigene Auflösung ist der empfohlene Mindestwert 60 Hz progressiv oder die engsten Häufigkeit für die Region geeignet. Niedrigere Aktualisierungsrate möglicherweise benutzerfreundlich.

**Für eine integrierte Bereich:** Die systemeigene Auflösung des Bereichs muss größer als oder gleich 1024 x 768.
 
**Für HD15, DVI, HDMI und DisplayPort Connector:**

Die systemeigene Auflösung des Bereichs muss größer als oder gleich 1024 x 768.

Die folgenden Modi müssen von der Anzeige unterstützt und in die Anzeigedauer hergestellt in der EDID aufgenommen werden:

-   640 x 480 bei 60 Hz progressiv (Byte 23h bit 5 im Hinblick auf hergestellt.)

-   800 x 600, und 60 Hz progressiv (Byte 23h bit 0 im Hinblick auf hergestellt.)

-   1024 x 768 bei 60 Hz progressiv (Byte 24h, bit 3 im Hinblick auf hergestellt.)

Diese Modi können als Vollbild unterstützt oder zentriert werden.

**Für alle anderen Connectors wie S-Video, Komponente und zusammengesetzter:** Der Connector muss den maximalen zulässigen Modus unterstützt, gemäß Definition in der Spezifikation für die Standard.

### <a name="devicedisplaymonitorstereoscopic3dmodes"></a>Device.Display.Monitor.Stereoscopic3DModes

*Eine externe Stereo 3D angezeigt oder interne mobile Systemsteuerung muss einen Stereo Modus entspricht die systemeigene oder bevorzugten Lösung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die systemeigene oder bevorzugte Auflösung der Stereo 3D Anzeige muss einen entsprechenden Stereo Modus verfügen. Die systemeigene oder bevorzugte Auflösung der Anzeige wird über seine EDID verfügbar gemacht.

Beispiel: Bei die systemeigene Auflösung der Stereo 3D Anzeige 1920 x 1200 in Mono müssen sie auch dieselbe systemeigene Auflösung im Stereo Modus unterstützen.

