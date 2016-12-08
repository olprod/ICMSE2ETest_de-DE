---
title: Device.Streaming.Camera
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cda409d9cac1228cf658f3aca8906051708e8ea3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicestreamingcamera"></a>Device.Streaming.Camera

 - [Device.Streaming.Camera.Base](#device.streaming.camera.base)
 - [Device.Streaming.Camera.Base.Sharing](#device.streaming.camera.base.sharing)
 - [Device.Streaming.Camera.UVC](#device.streaming.camera.uvc)

<a name="device.streaming.camera.base"></a>
## <a name="devicestreamingcamerabase"></a>Device.Streaming.Camera.Base

### <a name="devicestreamingcamerabaseavstreamclassinterfaceandwdm"></a>Device.Streaming.Camera.Base.AVStreamClassInterfaceAndWDM 

*Implementierung der Kamera muss auf AVStream Klasse und WDM basieren, und die Schnittstelle Anforderungen erfüllen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Kamera Implementierungen müssen auf der Schnittstelle für AVStream Klassen und Windows Driver Model (WDM) basieren, wie in der Windows-Treiberkits definiert. AVStream ist die ersatztechnologie für Stream-Klasse-Schnittstelle, die nicht mehr unterstützt wird.

Kameratreiber müssen alle erforderlichen Pins, Eigenschaften und Einstellungen gemäß Definition im Windows-Treiberkits unterstützen.

*Kamera-Profile* (Sofern implementiert) *:*

Der Treiber möglicherweise Profile ankündigen Kombinationen von Kamera Funktionen darstellen, die gleichzeitig arbeiten garantiert werden. Weitere Informationen zu Kamera-Profilen finden Sie in der WDK.

*Unabhängige Pins:*

Alle vom Kameratreiber angekündigt Pins müssen unabhängig und in Kombination gemäß der Funktionen aufgeführt, die in den Profilen angekündigt vom Gerät ausgeführt werden können. Wenn das Gerät Profile nicht unterstützt, sollte dann gleichzeitige streaming von Pins für alle zusätzliche Funktionen für alle Medientypen unterstützt werden. Wenn der Datensatz und Image Pins der Kamera nicht gleichzeitig stream können, der Treiber muss explizit ankündigen dies durch Festlegen der KSPROPERTY\_CAMERACONTROL\_BILD\_PIN\_FUNKTION\_EXKLUSIVE\_WITH\_DATENSATZ und KSPROPERTY\_CAMERACONTROL\_BILD\_PIN\_FUNKTION\_SEQUENZ\_EXKLUSIVE\_WITH\_DATENSATZ ein Flag in der INF-Treiber (finden Sie zusätzliche Dokumentation über diese Flags hier: https://msdn.microsoft.com/en-us/library/windows/hardware/jj553707.aspx. Alle anderen Kombinationen von PIN-Nummer müssen unterstützt werden.

USB-basierte Kameras müssen USB Video Class (UVC) gemäß Definition im **Device.Streaming.Camera.UVC.UVCDriver** und **Device.Streaming kompatibel sein. Camera.UVC.USBClassDriver**.

**Fehlerbedingungen**

Fehlerbedingungen enthalten (jedoch nicht auf beschränkt) ungültige Pin Verbindungen gezwungen, ungültige-Eigenschaft festgelegt wird, Puffer mit ungültigen Daten, null-Zeiger und fehlerbedingungen von Treibern oberhalb oder unterhalb auf dem Stapel

### <a name="devicestreamingcamerabasedirectshow"></a>Device.Streaming.Camera.Base.DirectShow

*RGB-Kamera Implementierung muss DirectShow unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
</td></tr></table>

**Beschreibung**

RGB-Kameras müssen Microsoft DirectShow entwickelt, um Legacyanwendungen zu unterstützen.

### <a name="devicestreamingcamerabasekscategoryvideocameraregistration"></a>Device.Streaming.Camera.Base.KSCategoryVideoCameraRegistration

*RGB-Kameras müssen unter KSCategory registrieren\_Video\_Kamera*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

RGB-Kameras müssen unter KSCategory registrieren\_Video\_Kamera für Windows zum Erkennen von der Kamera

### <a name="devicestreamingcamerabasemediafoundation"></a>Device.Streaming.Camera.Base.MediaFoundation

*Kamera-Implementierung muss Media Foundation Architektur unterstützt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Kameras müssen Microsoft Media Foundation entwickelt, zur Unterstützung der Vorversion (Win32) und Windows Store-Apps.

### <a name="devicestreamingcamerabasemultipleclientappsupport"></a>Device.Streaming.Camera.Base.MultipleClientAppSupport

*Kamera-Implementierung muss mehrere Instanzen von KS Filter und das streaming von unabhängigen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

*Mehrere Filterinstanz demselben Gerät:*

Jede Kamera muss mehrere Filterinstanzen zu erstellenden zulassen. Geräte können nur eine Filterinstanz in einem stream aktiv ermöglichen.

### <a name="devicestreamingcamerabasenonrgbcameras"></a>Device.Streaming.Camera.Base.NonRGBCameras

*Nicht-RGB-Kameras müssen unter KSCategory registrieren\_Sensor\_Kamera*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Um die Funktionalität zwischen RGB-Kameras und anderen Arten von Sensoren zu unterscheiden, Kameras, die nicht RGB Kameras Videostreaming sind unter Kategorie KSCategory registrieren müssen\_Sensor\_Kamera

### <a name="devicestreamingcamerabasepnpandpowerpolicies"></a>Device.Streaming.Camera.Base.PnPandPowerPolicies 

*Kamera-Implementierung muss Microsoft PNP und Power Richtlinien entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Microsoft PNP Kameras entsprechen und Konfigurationen Standby Power-Richtlinien und auch Unterstützung verbunden.

Weitere Informationen finden Sie unter den folgenden Link:

-   <http://go.Microsoft.com/fwlink/?LinkID=733968>

### <a name="devicestreamingcamerabasesurpriseremoval"></a>Device.Streaming.Camera.Base.SurpriseRemoval

*Laufenden Betrieb austauschbare Kameras müssen plötzlich unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Alle laufenden Betrieb austauschbare Kameras müssen ihre plötzlich aus der Host-Bus unterstützen.

### <a name="devicestreamingcamerabaseusageindicator"></a>Device.Streaming.Camera.Base.UsageIndicator

*Kameras benötigen einen optischer Indikator an, dass Verwendung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Eine Kamera benötigen einen optischer Indikator, der angibt, wenn es streaming ist. Visuelle Hinweis muss beim Gerät Streaming ist und deaktiviert, wenn das Gerät nicht streaming ist. Wenn mehrere Kameras auf das System jedoch nur ein einzelnes Symbol vorhanden sind, muss das Symbol auf werden, wenn die Geräte streaming sind.

Ein Hardware Usage Indicator (physischen LED) wird dringend empfohlen. Statt eine physische LED-Anzeige kann die folgenden Registrierungsschlüssels festgelegt werden:

<dl><dt>Path</dt><dd><p>HKLM\\SOFTWARE\\Microsoft\\OEM\\Gerät\\erfassen</p></dd><dt>Eintrag</dt><dd><p>NoPhysicalCameraLED (REG\_DWORD-WERT).</p></dd><dt>0 x 1</dt><dd><p>Aktivieren Sie das Feature (= No physischen Kamera-LED auf dem System).</p></dd><dt>0 x 0</dt><dd><p>Standard. Deaktivieren Sie das Feature (= physischen Kamera-LED auf dem System)</p></dd></dl>

Wenn dies festgelegt ist, ist das Betriebssystem werden zum Anzeigen der Benutzeroberfläche, der angibt, wenn die Kamera streaming ist können.

<a name="device.streaming.camera.base.sharing"></a>
## <a name="devicestreamingcamerabasesharing"></a>Device.Streaming.Camera.Base.Sharing

### <a name="devicestreamingcamerabasesharingcustommediasource"></a>Device.Streaming.Camera.Base.Sharing.CustomMediaSource

*Benutzerdefinierte Media-Quellen müssen die Media Foundation-Architektur und Schnittstellen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Kameras und Erweiterung benutzerdefinierte Media-Quellen, die als Kameras mit Microsoft Media Foundation arbeiten müssen, um die Windows-Clientanwendungen unterstützt fungieren. Zusätzlich zu den normalen MediaSource Schnittstellen und Attribute, die benutzerdefinierte Medienquellen-installiert werden muss als Teil eines Treiberpakets.

### <a name="devicestreamingcamerabasesharingdevicemft"></a>Device.Streaming.Camera.Base.Sharing.DeviceMFT

*DeviceMFT und MFT0 Kamera Freigabe muss außerhalb des Prozesses als Anwendung im Benutzermodus ausgeführt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Zur Unterstützung der Freigabe wünschen, Gerätetreiber und Benutzer werden aus einem anderen Prozess als der Anwendung verwenden die Aufnahme APIs Mode Modus Komponenten im Zusammenhang mit der Treiber (DeviceMFT oder MFT0) ausgeführt werden. Dies bedeutet, dass die Komponenten für den Benutzer keine Abhängigkeiten zum Ausführen von im Prozess wie die Anwendung im Benutzermodus nutzen können. Einige Beispiele dafür sind eine private Schnittstelle, der DeviceMFT aus der Anwendung oder einen Verweis auf das Objekt CaptureEngine nutzen.

### <a name="devicestreamingcamerabasesharingfaceauthmode"></a>Device.Streaming.Camera.Base.Sharing.FaceAuthMode

*Zur Unterstützung der Oberfläche Authentifizierung DDI wie unterstützt müssen Windows Hello zusätzliche Anforderungen erfüllt werden*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Weitere Windows Hello Anforderungen müssen erfüllt sein, um anzukündigen, dass Gesicht Authentifizierung von einem Gerät unterstützt wird. Minimale Auflösung und hohe Framerate beinhalten. Finden Sie in der Windows-Hardware-Anleitung der fantasievollen Gesicht Authenfizierung (v2. 0 oder höher) Dokument Weitere Details.

### <a name="devicestreamingcamerabasesharingmemoryallocation"></a>Device.Streaming.Camera.Base.Sharing.MemoryAllocation

*Zuweisung von virtuellem Speicher von Treibern muss auf 4 KB (4.096 Bytes) Seitenränder ausgerichtet werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Zuweisung von virtuellem Speicher von Treibern muss 4 k Seitenränder ausgerichtet.  Es wird empfohlen, dass der Treiber Benutzer Modus Komponente die Zuweisung MF (Media Foundation) verwenden.

### <a name="devicestreamingcamerabasesharingnonconsumabledata"></a>Device.Streaming.Camera.Base.Sharing.NonConsumableData

*Nicht vorgesehen für Benutzer Verbrauch Datenströme müssen ausgeblendet ist*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
</td></tr></table>

**Beschreibung**

Jeder Stream durch den Treiber verfügbar gemacht werden sollten in irgendeiner Weise von einer Anwendung verwendet werden. Der Datentyp für den Datenstrom wird gut verstanden ist nicht erforderlich, aber der Stream sollte in allen anderen Aspekten Streaming funktionsfähig sein. Wenn die Daten aus einem Stream können nicht von einer anderen Komponente oder einer Anwendung genutzt werden, muss dies auf die Pin markiert werden, damit Applications ausgeblendet ist.

<a name="device.streaming.camera.uvc"></a>
## <a name="devicestreamingcamerauvc"></a>Device.Streaming.Camera.UVC

, ## Device.Streaming.Camera.UVC.USBClassDriver 

*Streaming USB-Videokameras USB Video Class Spezifikationen einhalten müssen von und Arbeiten mit der Microsoft UVC-Treiber (USBVideo.sys)*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
</td></tr></table>

**Beschreibung**

Alle USB-Videokameras streaming muss mit Microsoft USB Video Class-Treiber (USBVideo.sys) kompatibel sein.

### <a name="devicestreamingcamerauvcuvcdriver"></a>Device.Streaming.Camera.UVC.UVCDriver

*USB-Videokameras streaming muss mit USB Video Class Spezifikationen entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
</td></tr></table>

**Beschreibung**

Alle USB-streaming Videokameras, einschließlich nicht direkt mit dem Microsoft USB Video Class-Treiber (USBVideo.sys), muss die Spezifikationen der USB Video Class entsprechen. Zumindest müssen alle erforderlichen Eigenschaften und Befehle implementiert werden. Alle implementierten Befehle müssen die Spezifikationen entsprechen.

*Nicht-Microsoft-Treiber (sofern implementiert)*

USB-Kamera-Implementierung, die nicht den Microsoft USB Video Class-Treiber verwenden müssen weiterhin mit USBVideo.sys (pro **Device.Streaming.Camera.UVC.USBClassDriver**) kompatibel sein.

*H264 systemeigene Unterstützung (wenn implementiert*) *

Wenn h. 264-Format von der Kamera systemintern unterstützt wird, muss die Implementierung der USB Video Class-Spezifikation kompatibel sein. Referenz finden Sie unter: <http://go.microsoft.com/fwlink/?LinkId=233063>. Darüber hinaus muss die h. 264-Bit-Stream mit Media Foundation kompatibel sein.

Bei mindestens 2 Pins müssen unterstützt werden:

1. Eine Vorschau pin auf demselben Gerät mit nicht komprimierten Ausgabetyp YUY2 und/oder NV12

2. H. 264-Format muss auf einem separaten Videoaufnahme pin

