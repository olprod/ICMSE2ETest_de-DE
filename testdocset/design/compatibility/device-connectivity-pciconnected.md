---
title: Device.Connectivity.PciConnected
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: bcb3ff8337f1a8061a8371595b9f6ac7f111f86c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.PciConnected

 - [Device.Connectivity.PciConnected](#device.connectivity.pciconnected)
-->

<a name="device.connectivity.pciconnected"></a>
##Device.Connectivity.PciConnected

### <a name="deviceconnectivitypciconnected64bitprefetchablebar"></a>Device.Connectivity.PciConnected.64BitPrefetchableBar

*PCI-X und PCI Express-Geräte, prefetchable Arbeitsspeicher Balken implementieren prefetchable 64-Bit-Speicher-Basisadresse (Balken) registriert*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Geräte, die auf dem PCI-X oder PCI Express-Bus sit und verwenden prefetchable Speicher, dass Balken 64-Bit-prefetchable Speicher Balken auf X64-basierte Systeme implementieren müssen.

*Hinweise zum Entwurf*

Finden Sie unter [Firmware Zuordnung von Ressourcen zu PCI-Gerät unter Windows](http://www.microsoft.com/whdc/system/bus/pci/PCI-rsc.mspx)

Wenn das Gerät prefetchable Speicher für 64-Bit-Balken unterstützt, versucht Windows zuweisen eine Region oberhalb von 4 GB. In einer PCI-Brücke ignoriert Windows Startkonfiguration für einen gesamten Gerätepfad ausgehen aus der Brücke im, die Bereich diese Methode definiert wird. Bridge und die Geräte, darunter eine Region oberhalb von 4 GB zugewiesen werden soll müssen alle Geräte im Pfad prefetchable 64-Bit-Balken unterstützt. Wenn dies nicht der Fall ist, wird der Rebalance Code ausgeführt, und verschiebt alle ressourcenzuordnungen unter 4 GB, da das Ziel besteht darin, wie vielen Geräten wie möglich zu starten

### <a name="deviceconnectivitypciconnectedconfigurationspacecorrectlypopulated"></a>Device.Connectivity.PciConnected.ConfigurationSpaceCorrectlyPopulated

*Konfigurationsbereich für PCI-Gerät wird ordnungsgemäß aufgefüllt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

PCI2.3 beschreibt den Konfiguration Speicherplatz, den das System verwendet zum Identifizieren und Konfigurieren jedes Gerät, die an den Bus angefügt ist. Der Konfigurationsbereich besteht aus einer Kopfzeile Region und einer Region Gerät abhängig. Jede Konfigurationsbereich muss einen 64-Byte-Header offset0 verfügen. Das Gerät registriert, dass der Netzfrequenz Gerät für Initialisierung, Konfiguration und nach einem schwerwiegenden Fehler Fehlerbehandlung verwendet alle muss in den Abstand zwischen byte64 und byte255 passen.
Alle anderen das Gerät wird, während des normalen Betriebs verwendet Register müssen in normalen e/a oder Speicher Fläche befinden. Nicht implementierte registriert oder Lesevorgänge auf reservierte Register müssen ordnungsgemäß fertig gestellt und 0 (null) zurück. Schreibt zu reservierten Register müssen ordnungsgemäß fertig gestellt, und die Daten verworfen werden müssen.
Alle Register mit das Gerät Zeitpunkt Interrupt muss im Arbeitsspeicher oder e/a-Raum.

### <a name="deviceconnectivitypciconnectedexpresscardimplementsserialnumber"></a>Device.Connectivity.PciConnected.ExpressCardImplementsSerialNumber

*Ein einzelnes ExpressCard Modul, das sowohl USB und PCI Express-Schnittstellen unterstützt implementiert eine allgemeine Seriennummer*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Ein ExpressCard Modul, das für ein einzelnes Modul USB und PCI Express-Schnittstellen unterstützt muss die allgemeine Seriennummer implementieren Sie wie in der Spezifikation für PCI ExpressCard elektromechanische beschrieben.
Dies ist die einzige Methode, die Windows verwendet wird, um die Beziehung von USB und PCI Express auf einem Modul zu bestimmen.
 

### <a name="deviceconnectivitypciconnectedinterruptdisablebit"></a>Device.Connectivity.PciConnected.InterruptDisableBit

*PCI und PCI-X-Geräte, die PCI 2.3 kompatibel sind, unterstützen das Interrupt Disable-bit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle PCI und PCI-X-Geräte, die Unterstützung für PCI lokalen Bus-Spezifikation Version 2.3 oder höher, Forderung muss das Interrupt Disable Bit unterstützen.

*Hinweise zum Entwurf*

Finden Sie unter PCI Local Bus-Spezifikation, Version 2.3, Abschnitt 6.2.2.

### <a name="deviceconnectivitypciconnectedmsiormsixsupport"></a>Device.Connectivity.PciConnected.MsiOrMsixSupport

*PCI-Gerät PCI-X-Funktion in der PCI-Konfigurationsbereich Berichte und die Interrupts generiert MSI-DATEI oder MSI-X unterstützen möglicherweise jedoch nicht dazu erforderlich ist*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Im Rahmen der konventionelle PCI-Spezifikation 2.2 oder höher, PCI-X-Addendum Abschnitt 3.2, müssen alle PCI-X-Geräten, die Interrupts generieren Nachricht signalisiert Interrupts unterstützen.
Für eine MSI-Implementierung müssen die MSI-Funktionen in der Konfigurationsbereich implementiert werden.
Für die Implementierung der MSI-X müssen die MSI-X-Funktionen in der Konfigurationsbereich implementiert werden.
Jedoch ist, da von PCI Express PCI-X ersetzt werden und viele vorhandene Implementierungen MSI-DATEI oder MSI-X nicht unterstützt, diese Anforderung gelockert wird. Jedes Gerät, das zur Unterstützung von MSI-DATEI oder MSI-X Ansprüche muss dazu oder die relevanten WDK-Tests schlägt fehl.

*Hinweise zum Entwurf*

Nachricht für PCI-X-Gerät unterbrechen signalisiert ist Industriestandard erforderlich. Siehe jedoch oben.

### <a name="deviceconnectivitypciconnectedpciandpcixdevicesarepcicompliant"></a>Device.Connectivity.PciConnected.PciAndPcixDevicesArePciCompliant

*PCI und PCI-X-Geräten mindestens sind PCI 2.1 kompatibel*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle PCI und PCI-X-Geräte müssen die PCI lokalen Bus-Spezifikation, Version 2.1 oder höher entsprechen. Dies gilt für Geräte auf X86 IA64 und X64 Systeme.

*Hinweise zum Entwurf*

Finden Sie unter PCI lokalen Bus-Spezifikation, Version 2.1 oder höher.

### <a name="deviceconnectivitypciconnectedpciexpress"></a>Device.Connectivity.PciConnected.PCIExpress

*PCI Express-Anforderung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**1. Gerätetreiber für PCI-Express-Gerät nicht VC++ Enable-Einstellungen geändert:**

Der Gerätetreiber muss das Bit "VC++ aktivieren" nicht ändern (PCI Express Base Spezifikation, Version1.0a, Section7.11.7, VC++ Ressource Steuerelement registrieren: bit 31) für des Geräts erweiterte (VC0-nicht)-Kanal oder Kanäle.

**2.** **PCI Express aktiven Zustand L1 Exit Wartezeit für die Verbindung nicht überschreitet 64 µS:**

Eine PCI Express-Verbindung zwischen komplexen Stamm und Gerät oder Bridge, dürfen keine aktiven Zustand L1 Exit Wartezeit von mehr als 64 Mikrosekunden auf Systemen besitzen, wenn die Verknüpfung ein PCI Express Kabel zugeordnet ist. d. h., kann nicht Wert 111 b in der Link Funktionen Register Feld 17:15 gemeldet werden. Finden Sie unter Base PCIe Express-Spezifikation, Version 1. 0a, Abschnitt 7.8.6.

**3.** **PCI Express hot-Plug-Port, der Firmware gesteuerte hot Plug & Play verwendet unterstützt die \_OSC steuern-Methode zum Aktivieren und Deaktivieren von**:

Alle PCI Express hot-Plug-Ports, die Firmware gesteuerte hot-Stecker unterstützen müssen unterstützen die\_OSC-Steuerelement-Methode zum Aktivieren und Deaktivieren von Firmware gesteuerte hot-Plug-in der PCI-Firmware-Spezifikation, Version 3.0 gemäß. Finden Sie unter Express Base PCI-Spezifikation, Version 1.1, 6.7.4 Abschnitt.

**4.** **PCI-Express-Komponente eine einzelnes Gerät Anzahl für die primäre Schnittstelle implementiert wird:**

Jede Komponente PCI Express (d. h., physisches Gerät) zur Implementierung von einer einzelnen Gerätenummer auf die primäre Schnittstelle (Upstream-Port) eingeschränkt ist, aber es kann bis zu acht unabhängige Funktionen innerhalb dieser Gerätenummer implementieren. Finden Sie in PCI Express Base Spezifikation Revision1.1 (oder höher) im Abschnitt 7.3.1.

**5. PCI Express-Gerät implementiert die Unterstützung für MSI-DATEI oder MSI-X:**

MSI-Unterstützung für PCI 2.1, PCI 2.2 und 2.3 PCI-Geräte optional ist, ist für PCI Express-Geräte erforderlich. Diese Funktion kann entweder als MSI-DATEI oder MSI-X implementiert werden. Siehe PCI-Express-Spezifikation, Revision1.0a, Abschnitt 6.1 basieren.

**6**. **PCI Express Stamm komplexe unterstützt den erweiterte Konfiguration der (Arbeitsspeicher zugeordnet) Speicherplatz Access Mechanismus:**

Komplexe Stamm muss den erweiterten Konfiguration Speicherplatz Access Mechanismus unterstützen, gemäß Definition in PCI Express Base-Spezifikation, Version 1.1 (oder höher), Abschnitt 7.9.

**7.** **PCI Express Gerät unterbrechen kann unterstützt das Interrupt Disable Bit:**

Wenn ein Interrupt implementiert ist, müssen PCI Express-Geräten zur Unterstützung der Interrupt deaktivieren Funktionalität in lokalen PCI-Bus Spezifikation, Revision2.3 beschrieben. Dieses Bit deaktiviert das Gerät oder von INTx Assert-Funktion. Der Wert 0 ermöglicht die Assertion von sein INTx Signal. Ein Wert von 1 wird die Assertion von sein Signal INTx deaktiviert. Dieses Bit Status nach dem Zurücksetzen ist 0

### <a name="deviceconnectivitypciconnectedsubsystemidsrequired"></a>Device.Connectivity.PciConnected.SubsystemIdsRequired

*Gerät-IDs umfassen PCI-Subsystem IDs*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die Felder SID und SVID müssen die SID-Anforderung in PCI lokalen Bus-Spezifikation 2.3 und die Implementierung Details im "PCI-Geräte Subsystem-IDs und Windows" entsprechen
AMR-Geräte und MR Geräte auf der Hauptplatine sind nicht von der Anforderung für SID und SVID ausgenommen.
SVID ist nicht erforderlich, damit PCIe PCI/PCI-X-Brücken.

*Hinweise zum Entwurf*

Unter <http://go.microsoft.com/fwlink/?LinkId=36804>finden Sie unter "PCI-Geräte Subsystem-IDs und Windows".
