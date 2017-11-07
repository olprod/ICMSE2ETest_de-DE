---
title: Device.Input.Keyboard
Description: "Anforderungen an das Logo mit ausführlichen Informationen zu den Details der Implementierung der Tastatur wichtig, Betriebssystemen von Microsoft."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 559c7879ef863dd83b80d50a57229db3d7ff1d26
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.Keyboard

 - [Device.Input.Keyboard](#device.input.keyboard)
-->

<a name="device.input.keyboard"></a>
##Device.Input.Keyboard

*Anforderungen an das Logo mit ausführlichen Informationen zu den Details der Implementierung der Tastatur wichtig, Microsoft-Betriebssysteme.*

### <a name="deviceinputkeyboardbrowsermultimediakeysusemsapis"></a>Device.Input.Keyboard.BrowserMultimediaKeysUseMSApis

*Schlüssel für Internetbrowser und multimedia müssen Microsoft-APIs verwenden.*

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

Wenn eine Tastatur oder Peripheriegeräte Multimedia oder Internet Browser Schlüssel implementiert, muss verwendet werden die Registrierungsschlüssel für den WM zugeordnet\_APPCOMMAND API auf diese Funktionen zugreifen, wie in der Windows-Treiberkits beschrieben. Registrierungsschlüssel können mithilfe der INF-Dateien spezielle Einträge als Standardwerte installieren oder über eine benutzerdefinierte Schnittstelle zur Verfügung gestellt, die Benutzer programmiert werden.

*Hinweise zum Entwurf*

Das Microsoft Platform SDK, finden Sie in "WM\_APPCOMMAND."

### <a name="deviceinputkeyboardcharmskey"></a>Device.Input.Keyboard.CharmsKey

*Wenn einen der Schlüssel der Windows Charms anzuzeigen auf Tastaturen implementiert sind, müssen sie die richtige Scan Codes und die entsprechenden Glypths implementieren.*

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

Tastaturen, die implementiert werden Schaltflächen, um die Windows-Charms anzuzeigen zu starten, müssen die richtigen Scan Codes und Symbole auf die Schaltflächen verwenden. Die Symbole, die auf den Schaltflächen wechseln Sie in der Windows-Symbole Ergänzung zu den Windows-Logo-Lizenzvertrag für Hardware verfügbar unter [definiert sind *http://go.microsoft.com/fwlink/?LinkId=279574.*](http://go.microsoft.com/fwlink/?LinkId=279574.)

Die Schaltfläche Charm muss den richtigen Scan-Code entsprechend der Charm senden. Keine anderen Glyphe kann auf die Schaltfläche verwendet werden, wenn einen Überprüfung Code verwenden, der bezieht sich auf Aufrufen eines der Windows 8 Charms anzuzeigen.

### <a name="deviceinputkeyboarddynamickeyboards"></a>Device.Input.Keyboard.DynamicKeyboards

*Dynamische Tastaturen müssen die hier aufgeführten Anforderungen erfüllt.*

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

-   Wenn ein System Security Desktop eine Tastatur Lage, ändern die Tasten entsprechend der verschiedenen Symbole angezeigt wird oder Legenden dynamisch müssen vorhanden verfügt ein Tastaturlayout entsprechend die Sprache des Benutzers im System aktiv.

-   Wenn eine Tastatur kann die Tasten ändern verwenden, um die verschiedenen Symbole oder Legenden dynamisch anzuzeigen, die Tastaturen müssen neu starten, in das System Language-Standardlayout aktiviert in der Systemsteuerung -&gt; Regions- und Sprachoptionen -&gt; Tastaturen und Sprachen.

-   Wenn Sie eine Tastatur kann die Tasten ändern mit verschiedenen Symbole oder Legenden dynamisch anzuzeigen, müssen die Tastaturen das Tastaturlayout und die Sprache von einem Benutzer auf dem Anmeldebildschirm aktiviert ändern.

-   Wenn Sie eine Tastatur kann die Tasten ändern mit verschiedenen Symbole oder Legenden dynamisch anzuzeigen, müssen die Tastaturen die aktuell ausgewählte Layout und Sprache Vorgabe wiederzugeben, wenn der Windows-Desktop den Fokus besitzt.

-   Wenn Sie eine Tastatur kann die Tasten ändern mit verschiedenen Symbole oder Legenden dynamisch anzuzeigen, kann die Tastatur für die Neupositionieren von der Windows-Taste; Dieser Schlüssel muss jedoch in allen Konfigurationen-Layouts für Benutzer sichtbar bleiben. Standardmäßig muss dieser Schlüssel in der unteren linken Ecke der Tastatur, zwischen dem Steuerelement und alternative Tastenkombination bei einer Anmeldung, Willkommen oder Kennwort Eintrag Bildschirm vorhanden sein. Nachdem der Benutzer angemeldet hat, kann die Position des Schlüssels nach Priorität sortiert Benutzer neu positioniert.

-   Wenn eine Tastatur kann die Tasten ändern verwenden, um die verschiedenen Symbole oder Legenden dynamisch anzuzeigen, müssen der angezeigten Tastaturlayout und Sprache installierte Sprache des Betriebssystems entsprechen.

-   Eine mit eigener Tastatur kann die Tasten, um die verschiedenen Symbole und Legenden dynamisch entsprechend ändern müssen für die Tastatur über einen Switch zurückgesetzt werden zulassen oder Tastenfolge, unabhängig von einer Software zurücksetzen oder ein-und Ausschalten des Geräts.

### <a name="deviceinputkeyboardhotkeyfunctionapi"></a>Device.Input.Keyboard.HotKeyFunctionAPI

*Geräte, die Hotspot-Schlüssel Funktionalität implementieren müssen die entsprechenden API Benachrichtigungen implementieren.*

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

Zeigen und zeichnen und Tastaturen implementieren, die Schaltflächen, die als Anwendung oder Funktion hot Schlüssel für die WM vorhanden\_APPCOMMAND API muss die entsprechende Benachrichtigung API implementieren. Dies umfasst, ist aber nicht nur die folgenden Funktionen:

-   Positive/negative Volume

-   Stummschalten

-   Browser zurück oder Weiter

-   Wiedergabe/pause

*Hinweise zum Entwurf*

Bewährte Methoden für die Unterstützung von Zeigegerät und drawing und Tastaturen finden Sie unter <http://msdn.microsoft.com/en-us/library/ms997498.aspx>.
API für WM\_APPCOMMAND Benachrichtigungen finden Sie unter <http://msdn.microsoft.com/en-us/library/ms646275.aspx>.
HID Usage Seite und ID-Informationen für diese Funktionen finden Sie unter <http://www.microsoft.com/whdc/archive/scancode.mspx> und <http://www.usb.org/developers/hidpage>.
 

### <a name="deviceinputkeyboardkernelmodedriversusewdfkmdf"></a>Device.Input.Keyboard.KernelModeDriversUseWdfKmdf

*Tastatur Kernelmodus-Treiber müssen die WDF-KMDF verwenden.*

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

Drittanbieter-Tastatur Kernelmodus-Treiber müssen in das Modell WDF KMDF übertragen werden.

### <a name="deviceinputkeyboardlogoflagkey"></a>Device.Input.Keyboard.LogoFlagKey

*Windows Symbolschlüssel wird auf allen Tastaturen unterstützen von mehr als 50 Schlüssel implementiert. Das Windows Symbol Design ist erforderlich, nach dem 31. Dezember<sup>St</sup>, 2013.*

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

Alle Tastaturen aus, die mehr als 50 Schlüssel unterstützen müssen die Taste Windows Symbol implementieren. Der Windows-Flag-Logo Druckversion des Entwurfs wichtige möglicherweise, dass Logo für mobile Geräte und eigenständige Tastaturen bis zum Zeitpunkt des Übergangs qualifiziert. Die Windows-Flag Marke muss deutlich Key oben entsprechend *Der Microsoft Windows Logo Key Logo-Lizenzvertrag* , und das Dokument, "Schlüssel Support, Tastatur Scan Codes und Windows" <http://go.microsoft.com/fwlink/?LinkId=116451>unterschieden werden.

### <a name="deviceinputkeyboardmultiplekeyboard"></a>Device.Input.Keyboard.MultipleKeyboard

*Keine Interferenzen zwischen mehreren Tastaturen tritt auf.*

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

Wenn das System mehrere Tastatur enthält, muss keine Konflikte vorhanden sein. Beispielsweise kann ein angedockten mobiler Computer mehr als eine Tastatur an das System angeschlossen haben. Die Tastaturports auf einem mobilen Computer und einer Dockingstation müssen möglicherweise lösen von Konflikten zwischen den zwei Ports, wenn der mobile Computer verankert ist.

### <a name="deviceinputkeyboardscancode"></a>Device.Input.Keyboard.ScanCode

*Scannen Codes Branchenstandards entsprechen.*

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

Im folgenden sind die Anforderungen für einen Entwurf der Tastatur, der Windows-Logo-Taste enthält:

-   Die Tastatur muss gemäß den technischen Anforderungen in "Schlüssel Support, Tastatur Scan Codes und Windows." entwickelt werden

-   Die Tastatur muss auf Windows virtuelle Tastencodes Ebene kompatibel sein.

-   Windows-Logotaste muss als Modifizierer (STRG, UMSCHALT oder ALT) fungieren.

-   Tastatur Hersteller müssen Consumer-Steuerelement oder herstellerspezifischen, auf oberster Ebene Auflistungen für HID Hotspot Schaltflächen verwenden.

*Hinweise zum Entwurf*

Unter <http://go.microsoft.com/fwlink/?LinkId=36767>finden Sie unter "Wichtige Unterstützung, Tastatur Scan Codes und Windows".
Zusätzliche Software oder Treiber können Software Neuzuordnen Funktionalität bereitstellen geschrieben werden.

