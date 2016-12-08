---
title: Device.DevFund
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 67d234ecc15fb386f3719de6f0b8a2d29f3c46b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicedevfund"></a>Device.DevFund

 - [Device.DevFund.CDA](#device.devfund.cda)
 - [Device.DevFund.DeviceGuard](#device.devfund.deviceguard)
 - [Device.DevFund.DriverFramework.KMDF](#device.devfund.driverframework.kmdf)
 - [Device.DevFund.DriverFramework.UMDF](#device.devfund.driverframework.umdf)
 - [Device.DevFund.Firmware](#device.devfund.firmware)
 - [Device.DevFund.HALExtension](#device.devfund.halextension)
 - [Device.DevFund.INF](#device.devfund.inf)
 - [Device.DevFund.Memory](#device.devfund.memory)
 - [Device.DevFund.Reliability](#device.devfund.reliability)
 - [Device.DevFund.Reliability.3rdParty](#device.devfund.reliability.3rdparty)
 - [Device.DevFund.Reliability.Interrupts](#device.devfund.reliability.interrupts)
 - [Device.DevFund.ReliabilityDisk](#device.devfund.reliabilitydisk)
 - [Device.DevFund.Rollback](#device.devfund.rollback)
 - [Device.DevFund.Security](#device.devfund.security)
 - [Device.DevFund.Server](#device.devfund.server)
 - [Device.DevFund.Server.Nano](#device.devfund.nano)
 - [Device.DevFund.Server.PCI](#device.devfund.server.pci)
 - [Device.DevFund.StaticTools](#device.devfund.statictools)

<a name="device.devfund.cda"></a>
## <a name="devicedevfundcda"></a>Device.DevFund.CDA

*Benutzerdefinierte Treiber den Zugriff für privilegierten Anwendungsverwendung.*

### <a name="devicedevfundcdaapplication"></a>Device.DevFund.CDA.Application

*Benutzerdefinierte Treiber Zugriff*

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

Wenn Gerätetreiber eine benutzerdefinierte Treiber Access ausführen privilegierte app unterstützt, müssen sie eine eingeschränkte Schnittstelle nicht deklarieren. 

Durch eine eingeschränkte Schnittstelle deklarieren, müssen die folgenden Anforderungen erfüllt sein:
 

-   Bestätigen Sie, dass die vom Treiber bereitgestellten Gerät e/a-Steuerelementschnittstellen gedacht sind möglich, indem eine privilegierten app in einem app-Container, die Hardwarefunktionen mit CreateDeviceAccessInstance() und IDeviceIoControl() auf Windows 10 greift auf ausführen.   

<!-- -->

-   Die eingeschränkte Schnittstelle kann nicht direkt von einer app-Containers geöffnet werden.

Gerätetreiber deklariert eine Schnittstelle wird durch Festlegen der DEVPKEY eingeschränkt\_DeviceInterface\_die Eigenschaft auf True für diese Schnittstelle.  

<a name="device.devfund.deviceguard"></a>
## <a name="devicedevfunddeviceguard"></a>Device.DevFund.DeviceGuard

*Alle Kernel-Treiber müssen erstellt werden, um mit <http://aka.ms/DeviceGuard> kompatibel ist.*

### <a name="devicedevfunddeviceguarddrivercompatibility"></a>Device.DevFund.DeviceGuard.DriverCompatibility

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows-10 verfügt über ein neues Feature namens [Gerät Guard](http://aka.ms/DeviceGuard) , die Organisationen bietet die Möglichkeit zum Sperren von Geräten in eine Möglichkeit, die erweiterte Schadsoftware Schutz vor neuen und unbekannten Schadsoftware Varianten bietet sowie erweiterte Persistent Bedrohungen (APTs). Gerät Guard können Hardware-Technologie und Virtualisierung Sie um die Funktion der Code Integrität (CI) Entscheidung vom Rest des Windows-Betriebssystems zu isolieren. Bei der Virtualisierung basierende Sicherheit verwenden, um die Integrität des Codes zu isolieren, ist die einzige Möglichkeit, den Kernel-Speicher ausführbare werden kann durch eine Überprüfung der Integrität des Codes. Dies bedeutet, dass Seiten im Kernelmodus Arbeitsspeicher können nie Schreibzugriff und ausführbare Datei (W + X) und ausführbarer Code kann nicht direkt geändert werden.

Details sind in der [Windows-Hardware-Zertifizierung Blog](http://go.microsoft.com/fwlink/p/?LinkId=627463)verfügbar.

Die folgenden Attribute müssen auf die Datei Sys festgelegt werden

| CompanyName             | Name des Unternehmens                           |
|-------------------------|----------------------------------------|
| FileDescription         | Datei-Produkt Beschreibung des Treibers |
| Den Eintrag OriginalFilename        | Ursprünglicher Dateiname                     |
| ProductName             | Produktname                           |
| VS\_FIXEDFILEINFO:      | &nbsp; |
| &nbsp;&nbsp;&nbsp;"Filever"                 | Versionsnummer der Datei                    |
| &nbsp;&nbsp;&nbsp;ProdVer                 | Versionsnummer des Produkts                 |

Weitere Informationen finden Sie auf der [Ressource VERSIONINFO auf MSDN](https://msdn.microsoft.com/en-us/library/windows/desktop/aa381058.aspx).

<a name="device.devfund.driverframework.kmdf"></a>
## <a name="devicedevfunddriverframeworkkmdf"></a>Device.DevFund.DriverFramework.KMDF

*Treiber Framework Anforderungen für KMDF*

### <a name="devicedevfunddriverframeworkkmdfreliability"></a>Device.DevFund.DriverFramework.KMDF.Reliability

*Kernel Modus Treiber Framework (KMDF) Treiber zum Maximieren der Zuverlässigkeit und Stabilität entworfen werden müssen, und führen Sie "Verbreitung" Ressourcen wie Arbeitsspeicher und KMDF-Objekte.*

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

Kernelmodus-Treiber Framework (KMDF) Treiber müssen verantwortlich Speicher-Pool verwenden. Behandelt, die die Treiber an Gerätetreiberschnittstellen (DDIs) übergeben müssen das Muster des Parameters entsprechen. Der Status der Treiber muss bei der Verwendung von **WDFREQUEST** -Objekten und **WDFQUEUE** Objekten konsistent sein.
Ereignis Callback-Funktionen, die der Treiber registriert müssen Anforderung Ebene (IRQL) Einschränkungen unterbrechen entsprechen.

*Hinweise zum Entwurf*

Weitere Informationen zum Entwickeln von Treibern, die diese Anforderung erfüllen, finden Sie auf den folgenden Websites: <http://msdn.microsoft.com/en-us/library/aa973499.aspx>
<http://www.microsoft.com/whdc/driver/wdf/KMDF.mspx> die folgenden Tools aktiviert werden können, um diese Anforderung für alle KMDF Treiber zu überprüfen:

-   Überprüfung der Windows® Gerätetreiber Foundation (WDF).

-   Tracking zu behandeln. Nachverfolgen der Handle wird für alle Objekte, die KMDF aktiviert werden.

-   Erweiterte Überprüfung für Framework 1,9 KMDF Treiber. Erweiterte Verifier ist neu in Framework 1,9. Dieses Tool kann mithilfe des Registrierungswerts EnhancedVerifierOptions aktiviert werden. Um erweiterte Verifier aktivieren möchten, legen Sie die folgenden Registrierungswerte für Parameter des Treibers\\Wdf Schlüssel:

```
HKLM\\System\\CurrentControlSet\\Services\\\\Parameters\\Wdf
EnhancedVerifierOptions   REG\_DWORD  1
VerifierOn                REG\_DWORD  1
TrackHandles              MULTI\_SZ        \*
```

-   Überprüfung der Gerätetreiber. Verwenden Sie den folgenden Befehl, um die Treiber-Überprüfung zu aktivieren:

<blockquote>
<b>Verifier/Flags 0xfb/Driver</b>
</blockquote>

Mit diesem Befehl wird den Treiber KMDF unter Treiber Verifier mit alle Flags außer das Flag niedrig Ressource Simulation ausgeführt. Weitere Informationen zur Überprüfung der Gerätetreiber, finden Sie auf der folgenden Website: http://msdn.microsoft.com/en-us/library/ff545448.aspx In der Windows-Logo Kit, den Test mit WDF können ausgeführt werden, um diese Anforderung zu überprüfen.

### <a name="devicedevfunddriverframeworkkmdfwdfproperinf"></a>Device.DevFund.DriverFramework.KMDF.WDFProperINF

*Windows-Treiber-Framework (WDF) Treiber-INF-Dateien müssen ordnungsgemäß strukturiert sein.*

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

<ul>
<li><p>Alle Informationsdateien (INF-Datei) in Windows Treiber Foundation (WDF) Treiberpaketen müssen ordnungsgemäß WDF Abschnitten aufrufen. Strukturierte INF-Abschnitte zur ordnungsgemäß stellen Sie sicher, dass der Treiber ordnungsgemäß installiert werden. Jedoch auch, wenn ein Treiber installiert ist, kann ein Abschnitt schlecht oder falsch konfigurierter unvorhersehbare Probleme während des Vorgangs der Treiber oder Gerät verursachen. Aufgrund dieser Probleme können verhindert werden, anhand der Richtlinien für WDF INF-Einstellungen.<br />
Um diese Anforderung erfüllt werden, müssen alle WDF INF-Dateien über Folgendes verfügen:</p></li>
<li><p>Ein Abschnitt Coinstaller wie folgt:</p></li>
<code>[DDInstall.Coinstallers]<br />
CopyFiles=<br />
AddReg=<br />
 </code></li>

<li><p>Ein Abschnitt WDF wie folgt:</p>

<p>Für Treiber Kernelmodus-Treiber Framework (KMDF):</p>
<code>[DDInstall.Wdf]<br />
KmdfService= &lt;ServiceName&gt;, &lt;Kmdf\_Install&gt;<br />
[Kmdf\_Install]<br />
KmdfLibraryVersion=
<br />
</code>

<p>Für User-Mode Driver Framework (UMDF) Treiber:</p>
<code>[DDInstall.Wdf]<br />
UmdfService=&lt;ServiceName&gt;,&lt;Umdf\_Install&gt;<br />
UmdfServiceOrder=<br />
UmdfDispatcher [Only for USB Drivers and Drivers with file handle I/O targets]=<br />
UmdfImpersonationLevel[optional]=<br/><br/>
[Umdf\_Install]<br/>
UmdfLibraryVersion=<br />
DriverCLSID=<br />
ServiceBinary=<br />
<br />
 </code>
</li>

<li><p>Alle UMDF INF-Dateien benötigen einen Abschnitt WUDFRD Service Installation wie folgt:</p>

<code>[WUDFRD\_ServiceInstall]<br />
DisplayName = &quot;Windows Driver Foundation - User-mode Driver Framework<br />
Reflector&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WUDFRd.sys<br />
LoadOrderGroup = Base<br />
<br />
 </code>
</li>

<li><p>Alle WDF-Treiber, mit denen einen WinUSB-Treiber benötigen die folgenden Einstellungen Installation:</p>

<code>[WinUsb\_ServiceInstall]<br />
DisplayName = &quot;WinUSB Driver&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WinUSB.sys<br />
<br />
 </code>
</li>

<li><p>Dienstnamen, Hardware-IDs (HWIDs), Anzeigen von Namen und UMDF Klassenbezeichner (CLSID) können nicht aus WDF Beispiele eingefügt werden.</p></li>
</ul>

<p><em>Hinweise zum Entwurf:</em><br />
Weitere Informationen zu WDF-spezifische INF-Einstellungen finden Sie auf den folgenden Websites:<br />
<a href="http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx" class="uri">http://www.Microsoft.com/whdc/Driver/WDF/wdfbook.mspx</a><br />
http://msdn.Microsoft.com/en-us/library/ff560526.aspx<br />
http://msdn.Microsoft.com/en-us/library/ff560526.aspx</p>


<a name="device.devfund.driverframework.umdf"></a>
##Device.DevFund.DriverFramework.UMDF

*Treiber Framework Anforderungen für UMDF*

### <a name="devicedevfunddriverframeworkumdfreliability"></a>Device.DevFund.DriverFramework.UMDF.Reliability

*Benutzer Mode Driver Framework (UMDF) Treiber müssen secure, stabile und zuverlässige und keine Probleme mit der Anwendungskompatibilität haben.*

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

Um sicherzustellen, dass alle Benutzermodus Driver Framework (UMDF) Treiber Sicherheitsstandards entsprechen, stabil und zuverlässig sind und keine Probleme mit der Anwendungskompatibilität, Treiber darf keines Objekt zu Speicherverlusten.
Objekt Speicherverluste können durch Aktivieren der Verfolgung Objekt untersucht werden. Wenn eines Speicherlecks setzen Sie die Verweis Count Tracking-Einstellung auf "On" Diese Einstellung meldet den Verlauf von "Referenz hinzufügen", und zählt "Version der Referenz".

Diese Features können auf "Aktiviert" mithilfe der folgenden Werte festgelegt werden:
```
HKLM\\Software\\Microsoft\\WindowsNT\\CurrentVersion\\WUDF\\Services\\{193a1820-d9ac-4997-8c55-be817523f6aa}
TrackObjects REG\_DWORD 1
TrackRefCounts REG\_DWORD 1
```

UMDF Treiber müssen auch die folgenden Anforderungen erfüllen:

-   Die Treiber dürfen nicht versuchen, ungültige Handles verwenden.

-   Die Treiber müssen ordnungsgemäß kritische Abschnitte und Dateisperren verwenden. Der primäre Zweck des Tests Sperren ist, um sicherzustellen, dass die Anwendung ordnungsgemäß kritische Abschnitte verwendet.

-   Der Treiber müssen nicht Arbeitsspeicher Heapbeschädigung verursachen.

-   Die Treiber müssen virtuelle Adresse Speicherplatz Manipulation Funktionen, wie **VirtualAlloc**und **VirtualFree** **MapViewOfFile**ordnungsgemäß verwenden.

-   Die Treiber müssen Zugriff Verstöße nicht mithilfe von strukturierten Ausnahmebehandlung ausblenden.

-   Die Treiber müssen ordnungsgemäß Thread lokalen Speicherfunktionen verwenden.

-   Die Treiber müssen ordnungsgemäß COM verwenden.

Partner können überprüfen, ob die Treiber von Microsoft® Application Verifier Handles, sperren, heaps aktivieren, Speicher, Ausnahmen und Transport Layer Security (TLS) Einstellungen für die UMDF Hostprozesse (d. h., WUDFHost.exe) diese Anforderung erfüllen der Treiber Entwicklungs-, Test-.
Weitere Informationen finden Sie unter *Entwickeln von Treibern mit Windows Foundation Treiber* dieses Buch auf der folgenden Website: <http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx>.

*Hinweise zum Entwurf*

Application Verifier helfen UMDF Treiber intensiv genutzt, um sicherzustellen, dass Treiber stabil und zuverlässig überprüfen.
Für alle UMDF Treiber wird Application Verifier aktiviert werden, wenn Treiber Zuverlässigkeitstests ausgeführt werden.

Application Verifier kann in der folgenden Microsoft-Website heruntergeladen werden: http://www.microsoft.com/downloads/en/details.aspx?FamilyID=c4a25ab9-649d-4a1b-b4a7-c9d8b095df18.

Um Application Verifier für WUDFHost.exe aktivieren möchten, führen Sie den folgenden Befehl: Appverif-aktivieren Sie die Ziehpunkte Sperren Heaps Arbeitsspeicher COM Ausnahmen TLS-für WUDFHost.exe.

Weitere Informationen zu UMDF, finden Sie auf der folgenden Website: <http://www.microsoft.com/whdc/driver/wdf/UMDF.mspx>.

### <a name="devicedevfunddriverframeworkumdfwdfproperinf"></a>Device.DevFund.DriverFramework.UMDF.WDFProperINF

*Windows-Treiber-Framework (WDF) Treiber-INF-Dateien müssen ordnungsgemäß strukturiert sein.*

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

Alle Informationsdateien (INF-Datei) in Windows Treiber Foundation (WDF) Treiberpaketen müssen ordnungsgemäß WDF Abschnitten aufrufen. Strukturierte INF-Abschnitte helfen ordnungsgemäß stellen Sie sicher, dass der Treiber ordnungsgemäß installiert werden. Jedoch auch, wenn ein Treiber installiert ist, kann ein Abschnitt schlecht oder falsch konfigurierter unvorhersehbare Probleme während des Vorgangs der Treiber oder Gerät verursachen. Aufgrund dieser Probleme können verhindert werden, anhand der Richtlinien für WDF INF-Einstellungen.

Um diese Anforderung erfüllt werden, müssen alle WDF INF-Dateien über Folgendes verfügen:

<ul>
<li><p>Ein Abschnitt Coinstaller wie folgt:</p></li>
<li><code>[DDInstall.Coinstallers]<br />
CopyFiles=<br />
AddReg=<br />
<br />
 </code></li>

<li><p>Ein Abschnitt WDF wie folgt:</p>

<p>Für Treiber Kernelmodus-Treiber Framework (KMDF):</p>
<code>[DDInstall.Wdf]<br />
KmdfService= &lt;ServiceName&gt;, &lt;Kmdf\_Install&gt;<br />
[Kmdf\_Install]<br />
KmdfLibraryVersion=</code>
<p>Für User-Mode Driver Framework (UMDF) Treiber:</p>
<code>[DDInstall.Wdf]<br />
UmdfService=&lt;ServiceName&gt;,&lt;Umdf\_Install&gt;<br />
UmdfServiceOrder=<br />
UmdfDispatcher [Only for USB Drivers and Drivers with file handle I/O targets]=<br />
UmdfImpersonationLevel[optional]=<br /><br />
[Umdf\_Install]<br />
UmdfLibraryVersion=<br />
DriverCLSID=<br />
ServiceBinary=<br />
 </code>
</li>

<li><p>Alle UMDF INF-Dateien benötigen einen Abschnitt WUDFRD Service Installation wie folgt:</p></li>
<li><code>[WUDFRD\_ServiceInstall]<br />
DisplayName = &quot;Windows Driver Foundation - User-mode Driver Framework<br />
Reflector&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WUDFRd.sys<br />
LoadOrderGroup = Base<br />
<br />
 </code></li>

<li><p>Alle WDF-Treiber, mit denen einen WinUSB-Treiber benötigen die folgenden Einstellungen Installation:</p>

<code>[WinUsb\_ServiceInstall]<br />
DisplayName = &quot;WinUSB Driver&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WinUSB.sys<br />
<br />
 </code>
</li>

<li><p>Dienstnamen, Hardware-IDs (HWIDs), Anzeigen von Namen und UMDF Klassenbezeichner (CLSID) können nicht aus WDF Beispiele eingefügt werden.</p></li>
</ul>

<p><em>Hinweise zum Entwurf</em><br />
Weitere Informationen zu WDF-spezifische INF-Einstellungen finden Sie auf den folgenden Websites:<br />
<a href="http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx" class="uri">http://www.Microsoft.com/whdc/Driver/WDF/wdfbook.mspx</a><br />
http://msdn.Microsoft.com/en-us/library/ff560526.aspx<br />
http://msdn.Microsoft.com/en-us/library/ff560526.aspx</p>


<a name="device.devfund.firmware"></a>
##Device.DevFund.Firmware

*Treiber-Paket-Anforderungen für Firmware-Updatepaket*

### <a name="devicedevfundfirmwareupdatedriverpackage"></a>Device.DevFund.Firmware.UpdateDriverPackage

*Diese Anforderungen gelten für alle Firmware Treiber Updatepaket, das für die Genehmigung und Signieren an Microsoft gesendet wird.*

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

Zusätzlich zu den Anforderungen für den standard-Treiber Firmware-Updatepaket Treiber gelten die folgenden Anforderungen:

-   Ein Firmwarepaket muss Nutzlast das Update für nur eine Ressource.

-   Ein Firmwarepaket muss konfigurierbar (Siehe Device.DevFund.INF.\* Weitere Informationen).

-   Nach einem erfolgreichen Firmware-Upgrade der Firmware-Version in der. INF-Datei des Treiberpakets, der Ressourcenversion (in ESRT) und die letzte versuchte Version (in ESRT) für diese Ressource muss übereinstimmen.

-   Der Name der Binärdatei im Firmwarepaket muss mit einem der vorherigen Firmwareversionen nicht in Konflikt.

-   Erfolgreiche Firmware-Aktualisierung muss nicht reduzieren oder die Funktionalität der Geräte im System auszuschließen.

<a name="device.devfund.halextension"></a>
## <a name="devicedevfundhalextension"></a>Device.DevFund.HALExtension

### <a name="devicedevfundhalextensionhal"></a>Device.DevFund.HALExtension.HAL

*Diese Anforderungen gelten für HAL-Erweiterungen, die für die Genehmigung und Signieren an MS übermittelt wird.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
</td></tr></table>

**Beschreibung**

Zusätzlich zum standard-Treiber-Anforderungen gelten die folgenden Anforderungen zu HAL

-   HAL Erweiterung sollte nahtlos System HAL entwickelt.

-   HAL Erweiterung sollte ordnungsgemäß signiert werden.

<a name="device.devfund.inf"></a>
## <a name="devicedevfundinf"></a>Device.DevFund.INF

*INF-Datei restictions*

### <a name="devicedevfundinfaddreg"></a>Device.DevFund.INF.AddReg

*Wenn Sie eine Richtlinie AddReg verwenden, muss jeden Eintrag AddReg HKR als Registrierungsstamm angeben.*

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

HKR (Bedeutung "relative Root") ist die einzige Registrierung Stamm-ID, die in einem Abschnitt AddReg in einer INF-Datei verwiesen werden kann. Andere Stamm-IDs, einschließlich HKCR, HKCU, HKLM und HKU, werden von der Verwendung in einem Abschnitt AddReg beschränkt. Die Richtlinie AddReg soll Gerät Installation und Konfiguration nur Zwecken verwendet werden.

*Hinweise zum Entwurf*

Alle Registrierungsschlüssel, die in einem Abschnitt AddReg einer INF-Datei deklarierten müssen die relative Stamm-ID (HKR) als den Registrierungswert Stamm verwenden, wenn eine explizite Ausnahme vorhanden ist, gemäß dieser Anforderung.

Das folgende Beispiel zeigt die Registrierung eines using-Direktiven AddReg COM-Objekts. Building auf in diesem Beispiel wird, ist es möglich, alle Parameter für das Objekt anpassen:
```
\[COMobj.AddReg\]
HKCR,CLSID\\{&lt;CLSID&gt;},,,"&lt;MFT DLL description&gt;"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,,%REG\_EXPAND\_SZ%,"%%SystemRoot%%\\System32\\mftxyz.dll"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,ThreadingModel,,"Both"
```

Eine vollständige Liste der COM-Registrierungseinträge mit Details zu ihrer Verwendung finden Sie in der MSDN-WEBSITE unter: http://msdn.microsoft.com/en-us/library/ms694355.aspx.

Das folgende Beispiel zeigt die Registrierung eines using-Direktiven AddReg MFT-Filters:
```
\[MFT.AddReg\]
HKCR,CLSID\\{&lt;CLSID&gt;},,,"&lt;MFT DLL description&gt;"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,,%REG\_EXPAND\_SZ%,"%%SystemRoot%%\\System32\\mftxyz.dll"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,ThreadingModel,,"Both"
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,InputTypes,%REG\_BINARY%,76,45,87,2d,5e,23,...
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,OutputTypes,%REG\_BINARY%,22,5e,23,46,43,10,...
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,,%REG\_SZ%,"MFT Friendly Name"
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,MFTFlags,%REG\_DWORD%, 0x00000004
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,Attributes,REG\_BINARY%, 41,46,4d,
HKCR,MediaFoundation\\Transforms\\Categories\\&lt;MFTCategoryGUID&gt;\\&lt;CLSID&gt;
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\ByteStreamHandlers\\audio/xyz,&lt;CLSID&gt;,,"XYZ Stream Handler"
```

Darüber hinaus muss beim Registrieren einer ENTSCHLÜSSELN oder HMFT CODIEREN, eine der folgenden Registrierungsschlüssel auch festgelegt werden:

```
DECODE HMFT
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\HardwareMFT,EnableDecoders, %REG\_DWORD%, 1
```

```
ENCODE HMFT
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\HardwareMFT,EnableEncoders, %REG\_DWORD%, 1
```

Weitere Informationen zu MFTs finden Sie in der MSDN-WEBSITE unter: <http://msdn.microsoft.com/en-us/library/windows/desktop/ms703138.aspx>.

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich. Beachten Sie, dass es einige Ausnahmen zu dieser Anforderung gibt an die Registrierung von Component Object Model (COM)-Objekten und Media Foundation transformiert (MFT) mithilfe der Richtlinie AddReg angepasst. Finden Sie im Abschnitt Hinweise zum Entwurf von dieser Anforderung für zusätzliche Details.</p>
</tr>
</table>


### <a name="devicedevfundinfaddservice"></a>Device.DevFund.INF.AddService

*INF-Dateien können nur Treiber-Dienste installieren.*

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

Eine Richtlinie INF AddService kann nur Services verweisen, die Treiber zusammenhängen. Nicht Dienste Treiber verbunden, beispielsweise ein Microsoft Win32-Dienst können nicht referenziert werden oder mit einer INF-Datei installiert.

*Hinweise zum Entwurf*

Ein INF AddService Richtlinie Service-Install-Abschnitt kann nur einem ServiceType Typcode der folgenden angegeben werden:

-   DIENST\_TREIBER

-   SERVICE\_KERNEL\_TREIBER

-   DIENST\_DATEI\_SYSTEM\_TREIBER

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</tr>
</table>


### <a name="devicedevfundinfclassinstall32"></a>Device.DevFund.INF.ClassInstall32

*INF-Dateien müssen nicht auf eine benutzerdefinierte Klasse Installer innerhalb eines Abschnitts ClassInstall32 definieren.*

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

Eine INF-Datei kann eine benutzerdefinierte Klasse Installer innerhalb eines Abschnitts ClassInstall32 nicht angeben. Aus diesem Grund kann kein Treiberpakets eine benutzerdefinierte Klasse Installer während der Geräteinstallation ausgeführt werden.

*Hinweise zum Entwurf*

Entwickler sollten eine der vorhandenen Posteingang Gerät Setupklassen für ihr Gerät verwenden. Sie bei Bedarf eine neue Gerät Setup-Klasse definiert, kann nicht die neue Setupklasse eine Klasse Installer als Teil des Installationsvorgangs Gerät verwenden. Das folgende Beispiel zeigt einen INF-ClassInstall32 der Abschnitt, der eine benutzerdefinierte Klasse Installer definiert und daher schlägt dieser Anforderung.

```
\[ClassInstall32.ntx86\]            ; Declare a ClassInstall32 section for the x86
                                                ; architecture.
AddReg=SetupClassAddReg    ; Reference to the ClassInstall32 AddReg section.

; Place additional class specific directives here

\[SetupClassAddReg\]                ; Declare a class specific AddReg section.

; Device class specific AddReg entries appear here.

; The next line defines the class installer that will be executed when
; installing devices of this device-class type. Defining a registry entry
; of this type is no longer supported and the driver package fails to meet
; this device fundamental requirement.
**\[HKR,,Installer32,,"class-installer.dll,class-entry-point"\] **
```

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86) empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</tr>
</table>



### <a name="devicedevfundinfcomplexdevicematching"></a>Device.DevFund.INF.ComplexDeviceMatching

*INF-Datei Direktiven im Zusammenhang mit komplexen Gerät übereinstimmenden Logik werden nicht unterstützt.*

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

INF-Dateien werden komplexe Logik übereinstimmenden Gerät nicht unterstützt. Insbesondere wird die Möglichkeit zum Angeben einer Geräte-ID für ein Gerät, die nicht installiert werden sollen, wenn ein passendes HardwareID oder CompatibleID, mit im Abschnitt DDInstall vorhanden ist nicht unterstützt.

*Hinweise zum Entwurf*

Die folgende INF-Direktive darf nicht in einer INF-Datei verwiesen werden:

-   ExcludeID

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86) empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</tr>
</table>


### <a name="devicedevfundinfddinstallcoinstallers"></a>Device.DevFund.INF.DDInstall.CoInstallers

*INF-Dateien müssen keine Co Installer innerhalb eines Abschnitts DDInstall.CoInstallers verweisen.*

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

Eine INF-Datei darf keine Co Installer innerhalb eines Bereichs DDInstall.CoInstallers verweisen. Aus diesem Grund kann kein Treiberpakets alle CO Installer während der Geräteinstallation ausgeführt.

*Hinweise zum Entwurf*

Ausführung der gemeinsame Installer ist während der Geräteinstallation unzulässig. Die folgenden Beispiele zeigen die Registrierung einer gerätespezifischen Co-Installer und ein Gerät Klasse Co-Installationsprogramm. Beide Arten von Co Installer dürfen nicht in einer INF-Datei und Aufnahme führt die Anforderung erfüllt.
Gerätespezifische Co-Installationsprogramm-Beispiel:

```
; Registering one or more device-specific co-installers requires adding
; adding a REG\_MULTI\_SZ value using an AddReg directive. The following
; shows the general form for registering a device-specific co-installer.
;  :
;  :
\[DestinationDirs\]         ; Destination dir for the co-installer dll
XxxCopyFilesSection = 11           ; DIRID\_for %WINDIR%\\System32 dir
                                   ; Xxx = driver or device prefix
;  :
;  :
\[XxxInstall.OS-platform.CoInstallers\]       ; Define co-installers section
CopyFiles = XxxCopyFilesSection             ; Copy files directive
AddReg = Xxx.OS-platform.CoInstallers\_AddReg        ; Add registry directive

\[XxxCopyFilesSection\]              ; Define the co-installer copy files
XxxCoInstall.dll                   ; section

\[Xxx.OS-platform.CoInstallers\_AddReg\]       ; Define the co-installer AddReg
                                            ; section

; The next line defines the co-installer that will be executed when
; installing this device. Defining a registry entry of this type is no
; longer supported and the driver package fails to meet this device
; fundamental requirement.
**HKR,,CoInstallers32,0x00010000,"XxxCoInstall.dll, \\**
**  XxxCoInstallEntryPoint"**
Device-class co-installer example:
\[Xxx.OS-platform.CoInstallers\_AddReg\]       ; Define the co-installer AddReg
                                            ; section

; Similar format to the device-specific co-installer example, except the
; registry location is under HKLM. The next line defines the co-installer
; executed after any installation operations complete for the given device
; setup class GUID. Defining a registry entry of this type is no
; longer supported and the driver package fails to meet this device
; fundamental requirement.
**HKLM,System\\CurrentControlSet\\Control\\CoDeviceInstallers, \\**
**{SetupClassGUID}, 0x00010008,"DevClssCoInst.dll\[,DevClssEntryPoint\]"**
```

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</tr>
</table>



### <a name="devicedevfundinfdeviceconfigonly"></a>Device.DevFund.INF.DeviceConfigOnly

*INF-Dateien können nicht INF-Datei Direktiven verweisen, die nicht direkt für die Konfiguration von einem Gerät verknüpft sind.*

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

INF-Datei Direktiven, die Funktionalität zum Konfiguration über das Konfigurieren von Gerätehardware werden nicht mehr unterstützt. Die INF-Datei und alle unterstützenden Dateien in das Paket müssen nur für Device-Installation und Konfiguration verwendet werden.

*Hinweise zum Entwurf*

Die folgenden Direktiven INF-Datei können nicht in einer INF-Datei verwiesen werden:

1.  RegisterDlls
2.  UnregisterDlls
3.  ProfileItems
4.  "UpdateInis"
5.  UpdateIniFields
6.  Ini2Reg

Beachten Sie, dass während die Richtlinie RegisterDlls nicht mehr in einer INF-Datei deklariert werden kann, weiterhin die Möglichkeit, Component Object Model (COM) und Media Foundation transformieren (MFT) Objekte aus einer INF-Datei mit der AddReg-Direktive registriert ist. Die Richtlinie AddReg ermöglicht die Deklaration von COM/MFT-Registrierungsschlüssel unter der Registrierungsstruktur HKLM. Informationen zur Verwendung der Richtlinie für diesen Zweck AddReg finden Sie in der Anforderung Device.DevFund.INF.AddReg Windows Hardwarezertifizierung.

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
<td>
</tr>
</table>


 

### <a name="devicedevfundinfdeviceresourceconfig"></a>Device.DevFund.INF.DeviceResourceConfig

*INF-basierte Gerätekonfiguration Ressource und kein PnP Konfiguration kann nicht innerhalb einer INF-Datei ausgeführt werden.*

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

INF-Dateien können nicht verwendet werden, Gerätekonfiguration Ressource oder kein PnP verwandte Konfigurationsaufgaben ausführen. Unterschiedliche INF-Richtlinien und Abschnitte werden nicht mehr unterstützt.

*Hinweise zum Entwurf*

Die folgenden Abschnitte INF-Datei und Direktiven können nicht in einer INF-Datei verwiesen werden:

-   \[DDInstall.LogConfigOverride\] Abschnitt

-   Von LogConfig

-   \[DDInstall.FactDef\] Abschnitt

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</td>
</tr>
</table>



### <a name="devicedevfundinffilecopyrestriction"></a>Device.DevFund.INF.FileCopyRestriction

*INF-basierte Datei kopieren Einschränkungen*

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

Zielspeicherorte kopieren können nur verhindern, dass Treiberpakete installieren der Treiber in ungeeigneten Speicherorten auf dem System.

*Hinweise zum Entwurf*

Wenn Sie die Richtlinie CopyFiles verwenden, muss das Zielverzeichnis gibt für eine Datei einen der folgenden Werte DIRID:

-   11 (entspricht der %windir%\\Ordner System32) 

-   12 (entspricht der %windir%\\System32\\Treiber Directory)

Nur diese Zielverzeichnisse als die entsprechenden DIRID ausgedrückt werden einen Dateispeicherort gültige Kopie.

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p>
</td>
</tr>
</table>



### <a name="devicedevfundinffileorregistrymodification"></a>Device.DevFund.INF.FileOrRegistryModification

*Löschen oder Ändern von vorhandenen Dateien, Registrierungseinträge und/oder Services ist nicht innerhalb einer INF-Datei zulässig.*

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

INF-Datei Direktiven, die löschen oder Ändern von Registrierungseinträgen, Diensten und Dateien werden nicht mehr unterstützt.

*Hinweise zum Entwurf*

Die folgenden Direktiven INF-Datei können nicht in einer INF-Datei verwiesen werden:

-   DelReg
-   DelService
-   DelPropertry
-   BitReg
-   DelFiles
-   RenFiles

<table>
<tr>
<th>Ausnahmen</th>
<td><p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p></td>
</tr></table>

### <a name="devicedevfundinfinstallmanagement"></a>Device.DevFund.INF.InstallManagement

*Verwaltung von Dateien mit einer INF-Datei installiert ist auf dem System beschränkt.*

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

Alle Dateien, die auf dem System mit einer INF-Datei installiert sind, werden ausschließlich vom Windows verwaltet. Plug & Play (Plug & Play-) verhindert, dass Applikationen direkt ändern der Dateien, die in der INF-Datei verwiesen werden.

*Hinweise zum Entwurf*

Eine INF-Datei muss keine PnpLockDown-Direktive legen Sie auf den Wert 1 in der \[Version\] Abschnitt. Dies wird in der INF-Datei wie folgt aussehen:

```
\[Version\]
; Other Version section directives here.
PnpLockDown=1
```

<table>
<tr>
<th>Ausnahmen</th>
<td><p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p></td>
</tr></table>

### <a name="devicedevfundinflegacysyntax"></a>Device.DevFund.INF.LegacySyntax

*Legacy-Dienstkonfiguration kann nicht in einer INF-Datei ausgeführt werden.*

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

Konfiguration mit älteren INF-Syntax wird nicht mehr unterstützt.

*Hinweise zum Entwurf*

Die folgenden INF-Dienst installieren im Abschnitt Richtlinie kann nicht in einer INF-Datei verwiesen werden:

-   LoadOrderGroup

<table>
<tr>
<th>Ausnahmen</th>
<td><p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p></td>
</tr></table>

### <a name="devicedevfundinftargetosversion"></a>Device.DevFund.INF.TargetOSVersion

*Die TargetOSVersion Verzierung in einer INF-Datei kann keiner ProductType oder SuiteMask Flag enthalten.*

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

Innerhalb der \[Hersteller\] Abschnitt einer INF-Datei, eine TargetOSVersion Verzierung verwendet wird, um das Ziel OS des Treiberpakets zu identifizieren. Die Ergänzung TargetOSVersion darf keine ProductType oder SuiteMask Flag enthalten.

*Hinweise zum Entwurf*

In Windows 7 und früher OS die Verzierung TargetOSVersion das folgende Format:

```
nt[Architecture].[OSMajorVersion][.[OSMinorVersion][.[ProductType][ \
  .[SuiteMask]]]]
```

Beginnend mit Windows 8, sind die ProductType SuiteMask Felder und nicht mehr gültigen Felder in die TargetOSVersion Verzierung.

<table>
<tr>
<th>Ausnahmen</th>
<td><p>Dies ist eine Voraussetzung für Windows 10 Mobile (ARM, ARM64, X86), empfohlen aber für Windows 10 für desktop Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) (x 64 x 86) und WindowsServer 2016 – Technische Vorschau X64. Es wird in der Zukunft für diese Architekturen erforderlich sein.</p></td>
</tr></table>

<a name="device.devfund.memory"></a>
##Device.DevFund.Memory

*Anforderungen in Bezug auf Speicher-Profil*

### <a name="devicedevfundmemorydriverfootprint"></a>Device.DevFund.Memory.DriverFootprint

*Treiber müssen einen begrenzte Speicherbedarf belegen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Treiber müssen kleiner oder gleich der folgende Größe des nicht ausgelagerten Codepages im Arbeitsspeicher belegt werden:

-   Nicht ausgelagerter Codepages

| Treibertyp | Graphics-Treiber | Alle anderen Treibertypen |
|-------------|------------------|------------------------|
| X86/ARM     | &lt;= 10 MB      | &lt;= 1,66 MB          |
| x64         | &lt;= 10 MB      | &lt;= 5,45 MB          |

-   **Treiber gesperrt Zuweisungen** (einschließlich MDL Zuweisungen und zusammenhängender Arbeitsspeicher Zuweisungen)

    -   12 MB für alle Treibertypen von für beide Architekturen

-   **Nicht ausgelagerte Pool** - für Windows 10-Treiber müssen kleiner oder gleich der folgenden Größe des nicht ausgelagerten Pools im Arbeitsspeicher belegt werden:

| Treibertyp | Graphics-Treiber | Alle anderen Treibertypen |
|-------------|------------------|------------------------|
| X86/ARM     | 6 MB             | 4 MB                   |
| x64         | 10 MB            | 7 MB                   |

-   Schwellenwerte in Telemetrie basieren: X86/ARM – 4 MB behandelt 80. Quantil, X64 – 7 MB behandelt 76th Quantil von Pool Allocation-Beispiele

*Hinweise zum Entwurf*

Der entsprechende Test überprüft die Größe der Treiber nicht ausgelagerten Codepages in MB.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td><p>Treiber nicht ausgelagerten Speicherverwendung bildet eine feste Kosten im Hinblick auf die RAM-Auslastung für die gesamte Lebensdauer eines Systems. Wesentlich in Richtung der insgesamt OS Arbeitsspeicherbedarf beitragen, und die meisten Treiber immer im Arbeitsspeicher vorhanden sind. Optimieren der Treiber Arbeitsspeicher stellt eine verbesserte Benutzeroberfläche und bessere allgemeine Reaktionsfähigkeit des Systems aufgrund größere Verfügbarkeit des Arbeitsspeichers für Applikationen für Benutzer bereit.</p>
<p>Verringerung der-navigierbaren Treiber Bilanz verbessert direkt die geplante Speicherbedarf des Betriebssystems, wodurch sich Skalierbarkeit erhöht. Aktuelle WHCK Tests für Windows 8 beschäftigen sich mit Treiber Locked Zuweisungen (MDL/benachbart Arbeitsspeicher Zuweisungen) und nicht ausgelagerten Treibercode. Nicht Paged Pool Nutzung ist der Treiber nur nicht navigierbaren Bilanz Aspekt, der nicht von vorhandenen Tests abgedeckt wird.</p></td>
</tr>
</table>

### <a name="devicedevfundmemorynxpool"></a>Device.DevFund.Memory.NXPool

*Alle Treiber Pool Zuweisungen müssen in n x Pool befinden.*

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

Treiber Pool Zuweisungen müssen im Pool nicht ausführbar (n x) vorgenommen werden.

*Hinweise zum Entwurf*

Eine neue Art von nicht ausgelagerten Pool ist eine nicht ausführbar (n x) Pool wurde eingeführt. Da es nicht ausführbar ist, es ist sichererer im Vergleich zu ausführbare nicht ausgelagerten (NP) Pool und bietet verbesserten Schutz vor Angriffen Überlauf.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td><p>Verschieben von Zuweisungen in den Pool nicht ausführbar, die Fläche eines Angriffs für ein nicht autorisierter binär ausführbaren Code ist minimiert.</p></td>
</tr>
</table>


<a name="device.devfund.reliability"></a>
##Device.DevFund.Reliability

*Zuverlässigkeitstests mit dem Inhalt der bisherigen DEVFUND Tests.*

### <a name="devicedevfundreliabilitybasicreliabilityandperformance"></a>Device.DevFund.Reliability.BasicReliabilityAndPerformance

*Faktoren sind so konzipiert, dass die Zuverlässigkeit und Stabilität maximieren und führen Sie "Verbreitung" Ressourcen wie den Arbeitsspeicher.*

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

Treiberkomponenten müssen nicht das System zum Absturz oder Verlust Ressourcen verursachen. Diese Ressourcen enthalten sind aber nicht auf die folgenden beschränkt:

-   Arbeitsspeicher
-   Graphics Device Interface (GDI) oder User-Objekte
-   Kernelobjekte wie Dateien, Mutex, Semaphore und Gerät handles
-   Kritische Abschnitte
-   Speicherplatz
-   Printer-handles

*Hinweise zum Entwurf*

Zur Verbesserung der Zuverlässigkeit und Stabilität der Windows-Treiber, werden alle Treiber eine Reihe von generischen Treiber Qualitätstests unterzogen werden. Diese Tests umfassen Folgendes:

<dl>
<dt>Eingebettete Signatur Überprüfungstest</dt>
<dd><p>Es wird überprüft, dass Boot Starttreiber signierte eingebettet sind.</p></dd>

<dt>Überprüfen der Datei Systemkonsistenz Gerät zu installieren</dt>
<dd><p>Es wird überprüft, dass keine Systemressourcen während der Verarbeitung einer Gerätetreiber/Install überschrieben wurde.</p></dd>

<dt>Geräteinstallation Kontrollkästchen anderen Gerät Stabilität</dt>
<dd><p>Diesem Test wird überprüft, dass kein Gerät oder Treiber, mit Ausnahme des Geräts unter Test, durch die Geräte betroffen wurde / Treiber installieren oder Prozess zusammen installiert.</p></dd>

<dt>PCI-Stamm Port plötzlich entfernen Test</dt>
<dd><p>Bei diesem Test entfernt den PCI-Stamm Port für das Gerät (falls zutreffend).</p></dd>

<dt>PNP (deaktivieren und aktivieren) mit e/a vor und nach</dt>
<dd><p>Bei diesem Test führt die grundlegenden e/a und grundlegende PNP aktivieren/deaktivieren auf die Geräte testen.</p></dd>

<dt>Installieren Sie mit e/a vor und nach</dt>
<dd><p>Diesem Test deinstalliert und erneut installiert die Treiber für Test-Geräte und e/a auf diese Geräte ausgeführt wird.</p></dd>

<dt>Mit PNP (deaktivieren und aktivieren) mit e/a vor und nach dem Standbymodus</dt>
<dd><p>Bei diesem Test durchläuft das System über verschiedene Standbymodus Zustände und e/a und grundlegende PNP (aktivieren/deaktivieren) auf Test Geräte durchführt, vor und nach dem Standbymodus Zustand Zyklus.</p></dd>

<dt>Den Energiesparmodus versetzt wird mit e/a an, vor und nach</dt>
<dd><p>Dieser Test durchläuft das System über verschiedene dem Standbymodus Zustände und Geräte vor und nach dem Standbymodus Zustand Zyklus e/a führt.</p></dd>

<dt>Mit e/a während Energiesparmodus</dt>
<dd><p>Dieser Test durchläuft das System über die verschiedenen Standbymodus Status und führt e/a für Geräte während jeder Standbymodus Zustand Zyklus.</p></dd>

<dt>Plug & Play-Treiber Test</dt>
<dd><p>Bei diesem Test führt PnP-bezogene Codepfade im Treiber unter Test.</p></dd>

<dt>Device Path Exerciser Test</dt>
<dd><p>Dies umfasst eine Reihe von Tests, jede welche konzentriert sich auf einen anderen Eintrag zeigen oder e/a-Schnittstelle. Diese Tests dienen zum Bewerten der Stabilität eines Treibers, nicht seine Funktionalität.</p></dd>

<dt>CHAOS-Test</dt>
<dd><p>In diesem Test die Plug & Play-Tests ausgeführt wird, (aktivieren/deaktivieren, Rebalance, entfernen/neu starten, plötzlichen Entfernen und DIF entfernen) und die Treiber mit zufälligen Daten auf dem Testgerät parallel beim Durchlaufen des Testsystems an-oder allen unterstützten dem Standbymodus Zuständen (S1, S2, S3, S4 und dem Standbymodus verbunden) gleichzeitig getestet.</p></dd>
</dl>

Alle diese Tests werden mit Treiber Verifier mit den Standardeinstellungen aktiviert ausgeführt.

Darüber hinaus wird alle anwendbaren Kit Tests Treiber Verifier aktiviert sein.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td><p>Management/Stromverbrauchs, Plug & Play-Fehler sowie e/a-bezogene Fehler Beitrag zu Ende benutzerfreundlich und möglicherweise häufig System Abstürze, und Fehlern. Diese Tests helfen, um einige allgemeine Treiberprobleme zu identifizieren.</p></td>
</tr>
</table>


### <a name="devicedevfundreliabilitybasicsecurity"></a>Device.DevFund.Reliability.BasicSecurity

*Gerätetreiber muss verschiedenen Benutzermodus sowie Kernelmodus zu Kernel e/a-Anforderungen (DEVFUND 0004) ordnungsgemäß verarbeiten.*

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

Treiber Zuverlässigkeit und Sicherheit verbunden sind. Zuverlässige Treiber helfen, das System vor böswilligen Angriffen zu schützen.
Einhaltung von Bestimmungen wird durch Ausführen des Tests Device Path Exerciser für den Gerätetreiber überprüft. Device Path Exerciser umfasst eine Reihe von Tests, jede welche konzentriert sich auf einen anderen Eintrag zeigen oder e/a-Schnittstelle. Diese Tests wurden entwickelt, die Stabilität eines Treibers, nicht seine Funktionalität bewerten.

Während eines Tests sendet Device Path Exerciser Hunderte oder Tausende von ähnlichen Aufrufe an den Treiber in der Regel in eine schnelle Folge. Die Anrufe umfassen unterschiedliche Datenzugriffsmethoden, gültige und ungültige Puffer Längen und Adressen und Variationsmöglichkeit bestehen soll der Funktionsparameter, einschließlich Leerzeichen, Zeichenfolgen und Zeichen, die durch einen fehlerhaften Analyse oder Fehlerbehandlungsroutine falsch interpretiert werden können.

Der Gerätetreiber muss die Zuverlässigkeit Richtlinien entsprechen, die in der Windows-Treiberkits definiert sind. Alle Benutzer Modus e/a-Anforderungen und Kernel-Kernel-e/a-Anforderungen müssen ordnungsgemäß behandelt werden, um sichere Geräte und Treiber sicherzustellen.

Hinweise zum Entwurf:

Potenzielle Sicherheitsrisiken enthalten den Fehler zu prüfen, ob ein Pufferüberlauf der fehlenden falsche Daten vom Benutzermodus, verarbeitet, und der Behandlung von unerwartete Eintrag in den Treiber verweist. Wenn eine solche Sicherheitsrisiken nicht identifizierte und nicht korrigierte hinterlassen wurden, konnte bösartige Programme potenziell Problem Denial-of-Service-Angriffe oder andernfalls Sicherheit des Systems zu umgehen.

Weitere Informationen finden Sie in der Windows-Treiberkits "Erstellen von zuverlässige und Secure" und "Erstellen von zuverlässige Kernelmodus-Treiber".

### <a name="devicedevfundreliabilitybootdriverembeddedsignature"></a>Device.DevFund.Reliability.BootDriverEmbeddedSignature

*-Treiber müssen mit einer eingebetteten Signatur selbstsignierte sein.*

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

Alle Boot Starttreiber müssen eingebettet-signiert werden mithilfe einer Software Publisher Certificate (SPC) kommerziellen Zertifikat von einer Zertifizierungsstelle. Der SPC muss für Kernel-Module gültig sein. Treiber müssen über Self vor der Übermittlung Treiber signieren eingebettet-angemeldet sein.

*Hinweise zum Entwurf*

Weitere Informationen zum eingebettet Anmelden ein Boot Start-Treiber, finden Sie unter Schritt 6: einer Bilddatei Treibers mithilfe einer eingebetteten Signatur Version anmelden "auf der folgenden Website: <http://go.microsoft.com/fwlink/?LinkId=237093>

Nachdem die Datei eingebettet angemeldet ist, verwenden Sie zum Überprüfen der Signatur SignTool. Überprüfen Sie die Ergebnisse, um sicherzustellen, dass der Stamm der SPC-Zertifikatkette für Kernel-Richtlinie "Microsoft Code Überprüfung Root." ist Der in der folgenden Befehlszeile wird die Signatur in der Datei toaster.sys überprüft:

<blockquote>
<b>SignTool überprüfen /kp/v amd64\\toaster.sys</b>
</blockquote>

```
Verifying: toaster.sys

SHA1 hash of file: 2C830C20CF15FCF0AC0A4A04337736987C8ACBE3

Signing Certificate Chain:

Issued to: Microsoft Code Verification Root

Issued by: Microsoft Code Verification Root

Expires: 11/1/2025 5:54:03 AM

SHA1 hash: 8FBE4D070EF8AB1BCCAF2A9D5CCAE7282A2C66B3

Successfully verified: toaster.sys

Number of files successfully Verified: 1

Number of warnings: 0

Number of errors: 0
```

In der Windows-Logo-Kit wird dieser Anforderung mithilfe der eingebetteten Signatur Überprüfungstest getestet werden soll.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Boot Treiber müssen eingebettet-signiert sein, um den Startvorgang ordnungsgemäß funktioniert.</p>
</tr>
</table>


### <a name="devicedevfundreliabilitydriverinstalluninstallreinstall"></a>Device.DevFund.Reliability.DriverInstallUninstallReinstall

*Gerät und Treiber Installation/Deinstallation-Installation/zugeführt-installation muss abgeschlossen werden, ohne dass ein Fehler. Dazu gehören Treiber für eine Multifunktionsgeräten Funktion.*

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

Gerät und Treiber Installation, Deinstallation oder Neuinstallation muss nicht in jedem Fall fehl.

Installation des Treibers darf keine das System nicht mehr ausgeführt oder ohne Benutzereingriff, neu zu bewirken, es sei denn, das Betriebssystem ein Neustart erforderlich ist.

Für Funktion mit mehreren Geräte mit separaten Treibern, die separate Funktionen zu aktivieren, muss jeder Treiber installieren und deinstallieren unabhängig voneinander mit keine Startreihenfolge oder ausgeblendete Abhängigkeiten Lage sein. Ein Multifunktionsgeräten ist ein einzelnes Gerät, das mehrere Funktionen unterstützt.

Geräte, die für den Betrieb Posteingang Treiber verwenden müssen auch diese Anforderung erfüllen. Dies gilt nicht für Geräte Internet Small Computer System Interface (iSCSI).

*Hinweise zum Entwurf*

Im Fall von Geräten mit mehreren Funktion funktioniert ein generelle Treiber, der verschiedene Treiber für einzelne Funktionen lädt nicht gut mit Windows®. Insbesondere wird Treiber unterstützt wahrscheinlich deshalb verloren gehen, nachdem eine Neuinstallation des Betriebssystems oder ein Upgrade oder wenn neue Treiber über Windows Update verteilt werden. Aus diesem Grund sollten derartige generelle Treiber vermieden werden.

Diese Anforderung wird mithilfe des Tests "Installieren mit e/a" getestet.

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies gilt nicht für Geräte Internet Small Computer System Interface (iSCSI). PEP und HAL Extensions werden für die Ausnahme von dieser Anforderung berücksichtigt.</p>
</tr>
</table>


### <a name="devicedevfundreliabilitydriveruninstallinstallotherdevicestability"></a>Device.DevFund.Reliability.DriverUninstallInstallOtherDeviceStability

*Installieren oder Deinstallieren von des Treibers muss nicht reduzieren oder Funktionen von anderen Geräten oder anderen funktionalen Teilen dasselbe Gerät auf dem System installierte auszuschließen.*

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

Installieren oder Deinstallieren von Gerätetreiber muss nicht reduzieren oder eliminieren Funktionalität von anderen Geräten, die auf dem System installiert sind.

Diese Bedingung gilt auch in einer Multifunktionsgeräten funktionalen Einheiten, ob dieser funktionale Einheit auf der Multifunktionsgeräten oder im System als Ganzes ist.

*Hinweise zum Entwurf*

Gerät installieren Einchecken für andere Gerät Stabilität Test werden die Schritte zum Testen dieser Anforderung beschrieben: <http://msdn.microsoft.com/en-us/library/ff561407.aspx>.
 

### <a name="devicedevfundreliabilitynoreplacingsyscomponents"></a>Device.DevFund.Reliability.NoReplacingSysComponents

*Vom Hersteller bereitgestellte Treiber oder Software muss nicht Systemkomponenten ersetzen.*

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

Treiber oder Softwareinstallation muss geschützte Systemdateien nicht überschrieben werden. Hierzu zählen Dateien, die von Microsoft nicht erstellt werden, jedoch als Teil des Betriebssystems enthalten sind.

Wenn des Herstellers Informationsdatei (INF-Datei) alle Dateien, die das Betriebssystem bereitstellt kopiert, muss die INF-Datei diese Dateien aus dem Produktdatenträger Windows® oder vorinstallierten Quelldateien, kopieren, wenn die Komponente eine lizenzierte redistributable Komponente ist.

Faktoren, die nicht vom Betriebssystem bereitgestellt werden dürfen nicht nach einem Betriebssystem bereitgestellte Treiber heißen.

### <a name="devicedevfundreliabilitynormalopwithdep"></a>Device.DevFund.Reliability.NormalOpWithDEP

*Alle Treiber müssen normalerweise arbeiten, und führen Sie ohne Fehler mit Datenausführungsverhinderung (DEP) aktiviert.*

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

Zur Sicherstellung der richtigen Gerät und Treiber Verhalten und zur Verbesserung der Sicherheit von Windows® Systemen gegen Viren und andere Sicherheitsrisiken, müssen alle Treiber normal arbeiten, wenn (Data Execution Prevention, DEP) aktiviert ist. Datenausführungsverhinderung überwacht Programme, um sicherzustellen, dass die Programme die sichere des Systemspeichers Verwendung. Datenausführungsverhinderung schützt das System auch durch jedes Programm, das versucht, zum Ausführen von Code aus dem Speicher auf unzulässige Weise zu schließen.

Um diese Anforderung erfüllen, müssen Treiber nicht Code von Datenseiten wie Heap Standardseiten, verschiedene Stack-Seiten und Seiten im Arbeitsspeicher Pool ausgeführt werden.

Die Datenausführungsverhinderung ist ein Satz von Hardware und Software-Technologien, die zusätzliche überprüft auf Arbeitsspeicher, um zu verhindern, dass bösartigen Code, die auf einem System ausgeführt werden soll. Der Hauptvorteil der Datenausführungsverhinderung ist zum Ausführen des Codes von Datenseiten zu verhindern. In der Regel wird Code nicht aus dem Heap Default und dem Stapel ausgeführt. Hardwaregestützte Datenausführungsverhinderung erkennt Code, der den Speicherorten ausgeführt wird und löst eine Ausnahme aus, bei der Ausführung. Durch Software erzwungene Datenausführungsverhinderung kann verhindern bösartigen Code Nutzen der Vorteile der Ausnahme behandeln Mechanismen in Windows.

*Hinweise zum Entwurf*

Für Weitere Informationen zur Datenausführungsverhinderung, zum Aktivieren der Datenausführungsverhinderung, einschließlich auf dieser Website: <http://support.microsoft.com/kb/875352>.

Der Test für die Datenausführungsverhinderung ist derzeit Teil der Kategorie Test Systeme in Windows Hardware Zertifizierung Kit (WHCK). Eine Geräteversion von diesem Test werden eingeführt werden, bevor diese Anforderung für Logos erzwungen wird.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Datenausführungsverhinderung kann Verbesserung die Sicherheit von Systemen, die Windows-Betriebssystemen ausgeführt werden. Datenausführungsverhinderung bietet auch Schutz vor böswilligen Code, Viren und anderen Sicherheitsrisiken. Diese Anforderung für Geräte grundlegende tätigen helfen stellen Sie sicher, dass alle Treiber, die über die Hardware-Logoprogramm signiert sind geschützt sind und die Treiber verhindern, dass Malware signiert wird.</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypnpids"></a>Device.DevFund.Reliability.PnPIDs

*Plug & Play-IDs in Hardwaregeräte, einschließlich jedes funktionale Einheit ein Multifunktionsgeräten eingebettete müssen zur Unterstützung von Plug & Play-Geräte-ID verfügen.*

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

Jedes Gerät, das mit einer Erweiterungsbus verbunden ist muss eine eigene Geräte-ID bereitstellen können. Jede Funktion oder auf einem Gerät mit mehreren Funktion Add-on, die einzeln aufgelistet wird-Gerät muss auch Geräte-ID für den Bus bieten, die der Funktion oder Gerät verwendet wird.

Im folgenden sind die spezifischen Anforderungen für Plug & Play-Geräte-IDs:

-   Jede separate Funktion oder ein Gerät in der Hauptplatine muss separat aufgelistet werden. Aus diesem Grund jede Funktion oder Gerät muss bereitstellen eine Geräte-ID für den Bus, der verwendet wird, wie in der aktuellen Plug & Play-Spezifikation erforderlich.

-   Wenn ein Gerät auf einer Visitenkarte Erweiterung aufgezählt wird, müssen das Gerät eine eindeutige ID und eine eigene Ressourcen gemäß den aktuellen Anforderungen der Geräte-ID für den Bus, mit dem die Karte verbunden ist. Diese Anforderung gilt für Geräte, die separat auf mehreren Funktion Karten oder mit mehreren Funktion aufgelistet werden Chips.

-   Plug & Play-ID kann mit anderen Geräten, die den gleichen Modellnamen, haben freigegeben werden, wie in der gerätespezifischen Plug & Play-Spezifikation definiert.

-   Jede logische Funktion des Geräts muss eine unterschiedliche Plug & Play-ID.

-   Abschnitt installieren (INF-Datei) muss deaktiviert nur die genauesten ID gemäß den Plug & Play-Richtlinien in Windows®-Treiberkits eingegeben werden.

-   Definieren Sie älteren Geräte wie etwa seriell, parallel und Infrarot-Ports die ältere Plug & Play-Richtlinien Anforderungen und Clarifications für automatische Gerätekonfiguration, Ressource: Zuteilung und dynamische Disable-Funktionen.

Hinweis: Geräte, die vollständig unsichtbar für das Betriebssystem, wie etwa Out-of-Band-Systems Management-Geräte sind oder intelligenten Eingabe/Ausgabe (I2O) ausgeblendet Geräten, weiterhin müssen verwenden Advanced Configuration and Power Interface (ACPI) Methoden ordnungsgemäß Reservieren von Ressourcen und vermeiden Konflikte.

Im folgenden sind die Ausnahmen für die einzelnen Gerät-ID-Anforderung für Geräte mit mehreren Funktion:
 
-   Mehrere Geräte derselben Gerät-Klasse, wie etwa multiline serielle Geräte, erforderlich einzelne Geräte-ID nicht.

-   Geräte, die von einem Accelerator oder Hilfs-Prozessor generiert werden und, die keine independent Hardware e/a, erforderlich einzelner Geräte-ID nicht. Dieser Prozessor benötigen eine ID und die Datei MF.sys muss verwendet werden, um die abhängigen Geräte aufgelistet werden.

Wenn OEM einen Mechanismus proprietären Hardware Anlage oder die Seriennummer zuweisen verwendet wird, muss diese Informationen für das Betriebssystem über Windows Hardware Instrumentation Technologie verfügbar sein.

*Hinweise zum Entwurf*

Finden Sie unter Windows Hardware Instrumentation Implementierung Richtlinien (WHIIG), Version1. 0, auf der folgenden Website: <http://go.microsoft.com/fwlink/?LinkId=237095>*.*

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Eine eindeutige Plug & Play-ID bietet eine gute Endbenutzers für Geräte.  Da eine eindeutige Gerät jeden Gerätetreiber installiert wird, verhindert, dass diese Anforderung die Probleme, die in Windows Update auftreten. Diese Anforderung jetzt enthält auch alle Aspekte der Plug & Play, die sind relevant für Geräte mit mehreren-Funktion, um eine gute Plug & Play-Oberfläche aktivieren, wenn das Gerät mit Windows verwendet wird. Diese Anforderung verbessert Kompatibilität und Zuverlässigkeit beim Windows mit zertifizierte Geräte verwendet wird.</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypnpirps"></a>Device.DevFund.Reliability.PnPIRPs

*Treiber müssen alle Plug & Play-IRPs unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Treiber müssen alle Plug & Play e/a-Anforderungspakete (IRPs) gemäß den Anforderungen auf der folgenden Website unterstützen:

<http://msdn.Microsoft.com/en-us/library/ff558807.aspx> Die folgenden IRPs sind häufig die Ursache der Treiberprobleme. Besonders sollte ihre Implementierung erteilt werden:

- Zum Entfernen

  - IRP\_MN\_ABFRAGE\_ENTFERNEN\_GERÄT

  - IRP\_MN\_ABBRECHEN\_ENTFERNEN\_GERÄT

  - IRP\_MN\_ENTFERNEN\_GERÄT

- Lastausgleich

  - IRP\_MN\_ABFRAGE\_BEENDEN\_GERÄT

  - IRP\_MN\_ABFRAGE\_RESSOURCE\_ANFORDERUNGEN

  - IRP\_MN\_FILTER\_RESSOURCE\_ANFORDERUNGEN

  - IRP\_MN\_ABBRECHEN\_BEENDEN\_GERÄT

  - IRP\_MN\_BEENDEN\_GERÄT

  - IRP\_MN\_STARTEN\_GERÄT

  - IRP\_MN\_ENTFERNEN

- Plötzlich

  - IRP\_MN\_PLÖTZLICH\_ENTFERNEN

 

### <a name="devicedevfundreliabilityproperinf"></a>Device.DevFund.Reliability.ProperINF

*Gerätetreiber benötigen eine korrekt formatierten INF-Datei für ihre Geräteklasse (DEVFUND-0001).*

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

Treiberinstallation und Deinstallation müssen Windows®-basierte Methoden verwenden. Aus diesem Grund Datei nur Informationen (INF-Datei)-Basis Installationsroutinen sind zulässig. Gerätetreiber benötigen eine korrekt formatierten INF-Datei für das Gerät aus, wie in der Windows Driver Kit (WDK) Thema "Erstellen einer INF-Datei" beschrieben.

*Hinweise zum Entwurf*

Der Test "INFTest gegen eine einzelne INF-Datei" in Windows Hardware Zertifizierung Kit (WHCK) überprüft dieser Anforderung. Weitere Informationen zu diesem Test finden Sie unter der Hilfedokumentation des Testkit.

Hinweis: Wenn das Gerät bietet keine INF-Datei (d. h., das Gerät verwendet nur den Posteingang Treiber und die INF-Datei), wird dieser Anforderung nicht angewendet.

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Wenn das Gerät bietet keine INF-Datei (d. h., das Gerät verwendet nur den Treiber Posteingang und die INF-Datei), wird dieser Anforderung nicht angewendet.</p>
</tr>
</table>



### <a name="devicedevfundreliabilityremotedesktopservices"></a>Device.DevFund.Reliability.RemoteDesktopServices

*Client- und Geräte müssen vor, während und nach dem Zurückwechseln oder einer Sitzung Microsoft Remote Desktop Services (DEVFUND 0009) ordnungsgemäß funktionieren.*

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

Geräte müssen ohne Datenverlust vor, während oder nach der Sitzungen Fast Benutzer wechseln (FUS) und Remote Desktop Services unterstützen. Benutzeroberfläche (UI) für das Gerät muss in der Sitzung angezeigt werden, auf den die Benutzeroberfläche angewendet wird. Device-Nutzung darf nicht auf unbestimmte Zeit in alternativen benutzersitzungen blockiert werden.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>FUS und Remote Desktop Services sind Windows® Funktionen. Um eine gute und einheitliche benutzererfahrung zu ermöglichen, muss jedem Gerät ordnungsgemäß mit diesen Diensten.</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypcsupportslowpowerstates"></a>Device.DevFund.Reliability.PCSupportsLowPowerStates

*Alle Geräte und Treiber S4 und S5 unterstützen* *und Energiesparmodus S0 im Leerlauf oder S3 Zustände des Systems den Energiesparmodus versetzt wird diese auf integriert oder mit verbunden.*

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

Alle Geräte und Treiber für Systeme, die S4 eingeben, werden die folgenden Anforderungen erfüllen müssen (Ruhezustand) und S5 (vorläufig off) und entweder S0 niedrig Power im Leerlauf oder S3 (Energiesparmodus):
 

-   Alle Geräte und Treiber müssen ordnungsgemäß unterstützen die Anforderung eines Systems, der in S0, a3, S4 oder S5 aufweisen.

-   Geräte und Treiber unterbinden, müssen nicht die Anforderung aus dem System.

-   Die Geräte müssen sowohl der S0 S3, S4 und S5 Status zu unterstützen.

-   Alle Geräte müssen Daten aneinander aus S0, a3, S4 fortgesetzt wird, und dem Standbymodus S5 Status meldet und nach dem Reaktivieren voll funktionsfähig sein.

-   Das Gerät und seine funktionalen Einheiten (im Fall von Geräten mit mehreren Funktion) müssen entsprechend aufgelistet werden, nachdem das Gerät fortgesetzt.

-   Alle Geräte und Treiber müssen ordnungsgemäß auf Ereignisse reagieren, Plug & Play, IOCtl-Aufrufe und e/a fordert, dass ein, die gleichzeitig mit dem Standbymodus Statusübergänge ausgegeben werden.

Dadurch wird sichergestellt, dass alle zertifizierten und signierten Geräte die S0, S3, S4 und S5 Standbymodus Zustände unterstützen werden, wenn die Geräte als Teil eines Systems verwendet werden oder extern mit einem System verbunden sind. Diese Anforderung helfen der Systeme und Energie gespart, wenn das System nicht verwendet wird. Verwaltung der Stromversorgung ist ein wichtiger Aspekt eine gute Benutzeroberfläche zur Verfügung. Das System sollte möglicherweise steuern, welche Geräte in dem Zustand abgelegt werden, wenn ein Gerät nicht verwendet werden. Alle Geräte müssen die Anforderung aus dem System in dem Zustand und nicht die Anforderung, wodurch eine zusätzliche ausgleichen an, auf der Stromquelle unterbinden einhalten.

*Hinweise zum Entwurf*

Diese Anforderung wird mithilfe der Test "Energiesparmodus Stress mit e/a" und der Test "Mit parallele e/a parallel mit DevPathExer PnPDTest" in Windows Hardware Lab Kit (HLK) getestet werden soll.

Das System, das zu Testzwecken verwendet wird, muss S0, S3, S4 und S5 unterstützen.

Beachten Sie, dass Systeme, die Standbymodus verbunden unterstützen a3, werden nicht unterstützt und können oder S4 möglicherweise nicht unterstützt. Geräte in solchen Systemen müssen dem Standbymodus verbunden und S4 Anforderungen dieses Systems (falls zutreffend) unterstützen.

### <a name="devicedevfundreliabilitysignable"></a>Device.DevFund.Reliability.Signable

*Gerätetreiber müssen von Microsoft signiert werden können.*

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

Alle Geräte müssen ist code signierte Treiber. Faktoren, die gesendet werden, für die Zertifizierung Windows® Code signiert werden können muss und die Microsoft®-Richtlinien, die in der Windows-Treiberkits definiert sind erfüllen Thema "WHQL digitale Signaturen". Alle Boot Start-Treiber muss eingebettet signierte mithilfe eines Zertifikats, das für Kernel-Module gültig ist. Geräte müssen über Self Anmeldung, bevor die Geräte an Microsoft, für die Zertifizierung gesendet werden eingebettet-angemeldet sein. Es wird empfohlen, die alle Treiber sind eingebettet signierte über Self Anmeldung, bevor die Treiber an Microsoft gesendet werden, obwohl dies nur für erforderlich ist Start Treiber zu starten.

*Hinweise zum Entwurf*

Anforderungen für digitale Signaturen finden Sie unter dem Thema "Driver Signierung/Datei Protection" auf der folgenden Website: <http://go.microsoft.com/fwlink/?LinkId=36678>.

Das INF2CAT Signability Überprüfung Tool wird der ersten, die Sie auf der Microsoft-Website eine Übermittlung erstellen automatisch installiert. Weitere Informationen über das Tool INF2CAT, finden Sie auf der folgenden Website: <http://go.microsoft.com/fwlink/?LinkId=109929>.

**Weitere Informationen**

<table>
<tr>
<th>Ausnahmen</th>
<td>
<p>Dies gilt nicht für Geräte, die den Posteingang Treiber des Betriebssystems verwenden.</p>
</td>
</tr>
</table>


### <a name="devicedevfundreliabilityswdeviceinstallsusepnpapis"></a>Device.DevFund.Reliability.SWDeviceInstallsUsePnPAPIs

*Gerät-Installationen Software initiierte müssen Plug & Play-APIs verwenden, um Gerätetreiber zu installieren.*

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

Gerät-Installers, die direkt Plug & Play-Ressourcen bearbeiten beitragen zur Systemstabilität. Aus diesem Grund werden direkte Bearbeitung von Plug & Play-Ressourcen in späteren Versionen von Windows® blockiert. Um Hilfe zur Sicherstellung der Kompatibilität mit Windows-Versionen, muss standard Plug & Play Application programming Interfaces, (APIs) Gerätetreiber installieren verwendet werden.

*Hinweise zum Entwurf*

In Windows Vista® und spätere Betriebssysteme, provisorische standard Plug & Play-Aufrufe, wie der Aufruf **von SetupCopyOEMInf** alle erforderliche Dateien für die Geräteinstallation auf dem System automatisch. Vor dem Staging der Treiberpakete wird Treiber Paketmigration während ein Systemupgrade auf Windows Vista oder höher Windows-Betriebssystemen erleichtern. Wir empfehlen die Verwendung der Tools Treiber installieren Framework Logo Anforderung entsprechen. Die Verwendung von DIFxAPI, DIFxAPP oder DPInst DIFx Tools erfüllt diese Anforderung.

<a name="device.devfund.reliability.3rdparty"></a>
## <a name="devicedevfundreliability3rdparty"></a>Device.DevFund.Reliability.3rdParty

*Zuverlässigkeitstests, die Inhalte der bisherigen DEVFUND Tests enthält.*

### <a name="devicedevfundreliability3rdpartyformertests"></a>Device.DevFund.Reliability.3rdParty.FormerTests

*Frühere Tests zuordnen der Anforderung*

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

Das Feature Device.DevFund.Reliability.3rdParty und diese Anforderung sind Platzhalter für die Zuordnung der bisherigen DevFund-Tests, die in den anderen Anforderungen nicht gefunden werden.

**Weitere Informationen**

| Ausnahmen | Dies gilt nicht für Geräte, die den Posteingang Treiber des Betriebssystems verwenden. |
|------------|------------------------------------------------------------------------------------------------|

<a name="device.devfund.reliability.interrupts"></a>
## <a name="devicedevfundreliabilityinterrupts"></a>Device.DevFund.Reliability.Interrupts

*Zuverlässigkeit in Bezug auf Gerät unterbrochen wird.*

### <a name="devicedevfundreliabilityinterruptsbasicreliabilityandperformance"></a>Device.DevFund.Reliability.Interrupts.BasicReliabilityAndPerformance

*Treiber darf nicht die maximale Anzahl von Interrupts enthalten und müssen Ressource Vermittlung nach unten zu einer Mindeststufe für unterstützen, gemäß vom Betriebssystem*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der Treiber muss Lastenausgleich System erneut gewählt vom Betriebssystem ohne Fehler, einschließlich der theoretischen mindestens eine Zeile basierend Interrupt Alternative Interrupt Ressourcen tolerieren können.

Interrupt Vermittlung erfordern möglicherweise mehrere Iterationen. Treiber müssen auf Fälle tolerieren, wo ihre anfänglichen Interrupt Anforderung zurückgewiesen wird, vorbereitet werden. Um optimale und rechtzeitige Interrupt Vermittlung zu unterstützen, sollten mehrere alternativen am nacheinander reduzierten Interrupt Count bereitgestellt. Treiber sollten fordert mehrere Interrupt pro Kern Wenn möglich. Jede Anforderung für mehr als 2048 Interrupts pro Gerätefunktion pro des PCIe 3.0 zurückgewiesen werden definiert MSI-X Tabelle Eintrag Grenzwert von 2048 pro Gerät.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Fordert mehrere Interrupt pro Kern kann dazu führen, dass IDT Erschöpfung in den Einstellungen, in dem vielen Geräten vorhanden sind. Gesamtanzahl Interrupts basierend auf der Anzahl der Prozessorkerne häufig anfordern führt zu Speicherprobleme Zuteilung.</p>
</tr>
</table>


<a name="device.devfund.reliabilitydisk"></a>
##Device.DevFund.ReliabilityDisk

*Zuverlässigkeitstests für Datenträgergeräte*

### <a name="devicedevfundreliabilitydiskiocompletioncancellation"></a>Device.DevFund.ReliabilityDisk.IOCompletionCancellation

*Ein Gerätetreiber muss die Designdetails in die e/a-Abschluss/Abbruch-Richtlinien (DEVFUND-0013) folgen.*

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

E/a-Abschluss und Abbruch von Richtlinien für Treiber bieten einen verbindlichen Anforderungen, um sicherzustellen, dass Gerätetreiber Beenden nicht mehr reagiert und vollständig abgebrochen werden können. Diese Anforderungen vorschlagen auch bewährte Methoden, die Treiber folgen können, um die Leistung zu verbessern.

Gemäß der Richtlinie, müssen alle Gerätetreiber die folgenden Anforderungen erfüllen:

-   Alle e/a-Anforderungspakete (IRPs), die abgebrochen werden, müssen innerhalb von 5 Sekunden in einer Umgebung ausgeführt werden, die keine Ressource eingeschränkt ist. Keine Abbruch sollte ausgelassen werden, obwohl die Abbruch Anforderungen an jeden beliebigen Zeitpunkt eingehen, bevor ein Treiber Versendung Routine die IRP erhält.

-   Alle Ressourcen, die ein abgebrochen IRP reserviert müssen jederzeit IRP Abbruch konnten Systemleistung bei Abbruch hohe Auslastung hindert freigegeben werden. Alle e/a-intensiver Vorgang sollte der Abbruch der IRP Herunterfahren.

Darüber hinaus wird dringend empfohlen, dass Treiber keine zusätzliche Zuweisung von Ressourcen während Abbruch abhängig sind.

*Hinweise zum Entwurf*

Das Windows® e/a-Manager enthält Verbesserungen zur Unterstützung der Abbruch des der MJ\_IRP\_Prozess ERSTELLEN. Die Win32-Anwendungsprogrammierschnittstellen (APIs) umfassen Verbesserungen zur Unterstützung des Abbruchs des synchrone Vorgänge, wie etwa CreateFile. Diese Verbesserungen zulassen e/a-Abbruch weitere Umgebungen als in vorherigen Versionen des Betriebssystems Weitere Informationen finden Sie im Whitepaper "E/a Abschluss/Kündigung Guidelines" auf der folgenden Website: <http://www.microsoft.com/whdc/driver/kernel/default.mspx>.

Weitere Informationen zum Entwerfen von Abschluss und Abbruch Logik für Treiber finden Sie unter den folgenden Themen in der Windows Development Kit (WDK):

Fertigstellen des IRPs IRPs, die Cancel-Safe IRP Warteschlangen mit dem System Abbrechen Drehfeld Lock stornieren

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Die primäre Begründung für diese Anforderung wird verhindert, dass Treiber verursacht Applikationen nicht mehr reagiert. Darüber hinaus können Benutzer nicht beenden oder starten Sie die Anwendung neu. Treiber Programme reagiert, eine erhebliche Ursache für die Unzufriedenheit.  Eine sekundäre Begründung für diese Anforderung wird zur Verbesserung der Kundenzufriedenheit Anwesenheitsebene e/a-Abbruch treten auf Anforderung von einem Benutzer, durch die Verwendung von Elemente der Benutzeroberfläche (UI) wie eine Schaltfläche universelle beenden oder Abbrechen Schaltflächen. Diese Anforderung wurde in Windows Vista eingeführt. Die Anforderung vorhandenen Treiber Abbruchlogik optimierte hinzugefügt und fügt die Anforderung, dass Treiber Abbrechen erstellen-Anfragen zu unterstützen. Treiber, die nicht mehr reagiert können zu manchmal zufällige Anwendung und Betriebssystem Ausfälle führen, die in verlorene Kundenproduktivität, verloren Kundendaten und die Notwendigkeit, den Computer neu starten. Abgesehen von diesen sehr schwerwiegenden Problemen verhindert, dass nicht vorhandene oder niedrige e/a Abbruch unterstützen Applikationen erfolgreich Vorgänge beenden, ohne die Anwendung neu.</p>
</tr>
</table>


<a name="device.devfund.rollback"></a>
##Device.DevFund.Rollback

*Zurücksetzen des Treibers*

### <a name="devicedevfundrollbackdriver"></a>Device.DevFund.Rollback.Driver

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Sichern Sie in der Reihenfolge für Endbenutzer werden sollen, führen Sie einen Treiber (d. h., installieren Sie den zuvor installierten Treiber), Gerätetreiber können deinstalliert und ohne Fehler neu installiert werden muss.

<a name="device.devfund.security"></a>
## <a name="devicedevfundsecurity"></a>Device.DevFund.Security

*Zusätzliche TDI-Filtertreiber und LSP Anforderungen in Bezug auf Sicherheit.*

### <a name="devicedevfundsecuritynotdifilterandlsp"></a>Device.DevFund.Security.NoTDIFilterAndLSP

*Keine Filter TDI oder LSPs werden während der Installation oder Verwendung durch den Treiber oder zugeordneten Softwarepakete installiert.*

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

Keine Verwendung von TDI-filtern oder LSPs durch Kernel-Modus Software oder Treiber oder Benutzersoftware Modus oder Treiber können vorhanden sein.

**Weitere Informationen**

<table>
<tr>
<th>Unternehmensvorgabe</th>
<td>
<p>Verwendung der TDI filtert und LSPs Angriffsfläche erhöhen und werden daher nicht mehr unterstützt für zukünftige OS frei.</p>
</tr>
</table>


<a name="device.devfund.server"></a>
##Device.DevFund.Server

### <a name="devicedevfundservercommandlineconfigurable"></a>Device.DevFund.Server.CommandLineConfigurable

*Windows Server-Gerätetreibern die konfigurierbare Einstellungen haben bieten Befehlszeilen-Dienstprogramms oder Funktion für das Gerät und Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Server®-Gerätetreibern, die konfiguriert werden müssen ein WMI oder PowerShell basierende, remoteable Funktionalität für das Gerät und Treiber angeben. Dazu gehören die folgenden Gerätekategorien:

 - Netzwerk, einschließlich teaming und Infiniband
 - Speicher, einschließlich Multipfad-e/a (MPIO)
 - Bus
 - Anderen Treibern, die möglicherweise konfigurierbare Einstellungen

Hinweis: Geräte, wie Drucker, Scanner, net Switches und Speicher-Arrays, die von einem BELIEBIGEN System (andere Server, Clientsysteme usw.) im Netzwerk konfiguriert werden können müssen nicht auf diese Anforderung erfüllen.

Die spezifischen Anforderungen sind folgende:

 - Die Funktionalität Dienstprogramm oder Tool möglicherweise PowerShell oder Windows-Verwaltungsinstrumentation (WMI) Funktionen verwenden, die Windows Server Core-Installationsoption zu unterstützen.

 - Das Dienstprogramm oder Funktionen muss ausgeführt werden, über die Befehlszeile oder werden eine WMI-Objekt und einen Anbieter, der mit dem Tool Windows Management Instrumentation Command-Line (WMIC) kompatibel ist.

 - Das Dienstprogramm muss als Teil des Treiberpakets bereitgestellt werden und werden standardmäßig auf dem System mit der Treiber installiert.

 - Das Dienstprogramm muss möglicherweise korrekt Abfragen, anzeigen und ändern alle Werte, die für den Treiber geändert werden können.

 - Das Dienstprogramm muss nicht fälschlicherweise erstellen oder Festlegen von Optionen, die für ein bestimmtes Gerät oder Treiber nicht vorhanden sind. Das Dienstprogramm muss kann eine beliebige Einstellung ändern, wenn das Betriebssystem nicht die Möglichkeit zum Ändern dieser Einstellung über die Befehlszeile bietet.

 - Geänderte Werte oder Bereichen, die die Benutzereingaben automatisch sein müssen überprüft, um sicherzustellen, dass die Benutzereingabe gültig ist.

 - Änderungen, die das Dienstprogramm macht müssen ein Netzwerk- oder Speicher Stack neu gestartet oder System wird neu gestartet, es sei denn, ein Boot, System oder -Pagingverhalten oder Speicherort geändert wird keine erforderlich.

 - Änderungen, die das Dienstprogramm aufruft, sind auch nach einem Neustart dauerhaft.

 - Hilfe über die Verwendung des Dienstprogramms und Optionen ist lokal im System verfügbar ist. Beispielsweise muss das Dienstprogramm bieten eine "/?" Befehlszeilenoption oder die WMI-Optionen für das Produkt müssen über standardmäßige WMIC Befehle bereitgestellt werden.

 - Das Dienstprogramm sollte nicht von der Informationsdatei (INF-Datei) installiert werden.

 - Das Dienstprogramm sollte standardmäßig installiert werden. Dies kann mithilfe einen gemeinsamen Installer erfolgen.

Dies gilt nicht für Speicherarrays, Speicher Gewebe, Switches, Drucker oder andere Geräte externen Server-System und von den Systemen, der an die Ethernet, Fibre Channel oder andere Netzwerk angefügt ist verwaltet werden kann.

Dies gilt nicht für jedes Gerät, die konfigurierbare Einstellungen nicht vorhanden ist. Beispielsweise in einem System, die die grafische Benutzeroberfläche verwendet, es sind keine "Erweitert", "Power Management" oder andere zusätzlichen Registerkarten in der Benutzeroberfläche der Geräte-Manager noch Dienstprogramme vom Hersteller, die die gleiche Wirkung erzielen verfügbar sind.

Diese Anforderung gilt für alle physisches Gerät oder ein Gerät, das eine PCI-ID hat, die einen Treiber hat. alle Treiber, die in dem Netzwerk, Speicher, Dateisystem oder anderen Stapel ist; und an einem beliebigen Gerät oder Treiber, die andernfalls wird während des Modus für Kernel oder Benutzer in der Instanz Betriebssystem auf dem Server.

Hinweise zum Entwurf:

Alle Gerätetreiber, die diese Anforderung nicht erfüllt wird nicht auf Nano-Server-Systemen verwendet werden.

Erzwingungsdatum: Februar 2016

### <a name="devicedevfundservermultipleprocessorgroups"></a>Device.DevFund.Server.MultipleProcessorGroups

*Treiber müssen auf Servern, die Prozessoren in mehrere Prozessorgruppen konfiguriert haben, ordnungsgemäß funktioniert*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows® Server verwendet das Konzept der KGROUPs so erweitern Sie die Anzahl der Prozessoren, die eine einzelne Instanz des Betriebssystems für mehr als 64 unterstützen kann. Beide Wandlung und unenlightened Gerätetreiber müssen in Konfigurationen mit mehreren KGROUP ordnungsgemäß.

Hinweise zum Entwurf:

Weitere Informationen finden Sie unter "Unterstützung von Systemen, dass haben mehr als 64 Prozessoren: Richtlinien für Entwickler," ein Whitepaper, auf der folgenden Website: http://www.microsoft.com/whdc/system/Sysinternals/MoreThan64proc.mspx

Dies ist für alle Server Gerätekategorien getestet. Der Test verwendet BCDEdit Funktionalität so ändern Sie die Boot-Konfigurationsdatenbank (BCD) des Betriebssystems, also die Größe der Prozessorgruppen ( **Groupsize** Einstellung) geändert, sodass mehrere Prozessor Gerätegruppen erstellt werden. Der Test verwendet auch BCDEdit-Funktionen, um die Einstellung **Groupaware** in der BCD hinzuzufügen. Dadurch wird das Verhalten von mehreren jetzt Legacy Application programming Interfaces (APIs) geändert, so, dass der Test mehr Codefehler feststellt.

Das Betriebssystem wird nicht mit einer der folgenden Einstellungen geliefert. Diese Einstellungen werden nur zu Testzwecken und werden in der Produktion nicht mehr unterstützt. Um das System für normale Vorgänge neu konfigurieren möchten, müssen diese Einstellungen aus der BCD entfernt werden und das System neu gestartet werden muss. Das System, das zu Testzwecken verwendet wird, muss mindestens vier Prozessorkerne enthalten.

Lieferanten möglicherweise das System konfigurieren, sodass es ähnelt dem Windows-Logo Kit (WLK) und dem Gerät Test Manager (DTM) System ist. Lieferanten können ihre eigenen Tests wie folgt in einer Konfiguration für mehrere Prozessor Gruppe ausführen.

Die Befehlszeilen hinzufügen der gruppeneinstellungen, und starten Sie den Computer sind folgende:

> bcdedit.exe/2 Groupsize festlegen
>
> bcdedit.exe/Groupaware für festgelegt.
>
> Shutdown.exe - R -t 0 -f

Dies sind die Befehlszeilen, um die gruppeneinstellungen zu entfernen und den Computer neu starten:

> bcdedit.exe/deletevalue groupsize
>
> bcdedit.exe/deletevalue groupaware
>
> Shutdown.exe - R -t 0 -f

### <a name="devicedevfundserveroperateinservercore"></a>Device.DevFund.Server.OperateInServerCore

*Gerätetreiber müssen installieren, konfigurieren, bedient werden und in Windows Server Core verwenden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der auf dem Windows Server Betriebssysteme bereitgestellten Hardwareplattform haben erheblich in den vergangenen zehn Jahren entwickelt. Wie diese Grafik weniger werden Kosten für Systementwürfe und Effizienz der Bereitstellung, die Kunden erwarten vollständig setup, bereitstellen, konfigurieren und verwalten diese mithilfe der minimale Befehlszeilenschnittstelle und automatisierte scripting von Windows Server Core Hardware-Plattformen. Windows Server-Gerät, den Treiber in ähnlicher Weise wie für den Kunden diese Vorgänge ungehinderte unterschiedliche ermöglichen weiterentwickelt werden müssen.

Gerätetreiber muss veranschaulichen die Fähigkeit zum Installieren, konfigurieren Sie bedient werden und das Vorhandensein Abhängigkeit von der GUI nicht verwendet.

Hinweise zum Entwurf:

Alle Gerätetreiber, die diese Anforderung nicht erfüllt wird nicht auf Windows Server Core-Systemen verwendet werden.

Erzwingungsdatum: Februar 2016

### <a name="devicedevfundserverserverpowermanagement"></a>Device.DevFund.Server.ServerPowerManagement

*Treiber für Windows Server müssen Abfrage Power und legen Sie Power Management Anfragen unterstützen.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Beim Übergang in den Ruhezustand (S4) System Energiesparmodus versetzt empfangen Gerätetreiber Power Anfragen aus dem Betriebssystem. Gerätetreiber müssen berücksichtigt und müssen ordnungsgemäß verarbeiten die Abfrage Power und legen Sie Power Power Management Anforderungen. Gerätetreiber sollte niemals eine Abfrage Power Anforderung ablehnen. Wenn Gerätetreiber eine S4 festlegen Power Power Management-Anforderung empfängt, muss der Treiber die Geräte in einem D3 Power Gerätestatus Übergang und beenden Sie alle e/a-Vorgänge. Dazu gehören direkte (Transfers DMA Memory Access), die derzeit ausgeführt werden. Während der Treiber Geräte in einem Energiesparmodus befinden, Interrupts sind deaktiviert, und alle laufenden e/a-Vorgänge werden angehalten.

Der Status D3 möglicherweise entweder D3 "Hot", um Geräte zu unterstützen, die auf externe Reize oder D3 reagieren müssen "Kalt".

Gerätetreiber muss sich selbst an eine eindeutig identifizierbare Instanz der System-Hardware, wie beispielsweise einen bestimmten Prozessor nicht binden.

*Hinweise zum Entwurf*

Weitere Informationen finden Sie im Whitepaper "Treiber Kompatibilität für dynamische Partitionierung der Hardware" auf der folgenden Website: http://www.microsoft.com/whdc/system/platform/server/dhp.mspx

<a name="device.devfund.server.nano"></a>
## <a name="devicedevfundservernano"></a>Device.DevFund.Server.Nano

*Mindestanforderungen für Windows Server Nano*

### <a name="devicedevfundservernanodeployment"></a>Device.DevFund.Server.Nano.Deployment

*Alle Treiber für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Alle Treiber für die Verwendung auf Windows Server Nano vorgesehen müssen die folgenden Anforderungen für die Bereitstellung erfüllen:

- Treiber müssen nicht als eine MSI-DATEI gepackt werden. Alle Treiberdateien (beispielsweise inf und sys-Dateien) müssen als eine Reihe von Dateien verfügbar sein, die in einen Ordner für die Verwendung mit Deployment Image Servicing and Management (DISM) kopieren.
- Treiber installiert werden müssen mithilfe von DISM offline.

Alle Tools, Dienstprogramme oder Agents auf Nano Server installiert sein müssen als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt werden.

### <a name="devicedevfundservernanodiagnostics"></a>Device.DevFund.Server.Nano.Diagnostics

*Alle diagnostic Dienstprogramme für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Alle Diagnosetools und Dienstprogramme zur Verwendung in einer Microsoft Azure-Stapel-Lösung müssen Management mithilfe einer der folgenden Methoden unterstützt:

- Verwenden von Remote Windows PowerShell oder Windows-Verwaltungsinstrumentation (WMI).
- Ein Befehlszeilentool verwenden, das ein Administrator auf dem Nano Server ausgeführt kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH.

Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.

Zusätzlich zu den obigen Systemen muss mit Windows Server Nano unterstützen Nano Server Recovery Console-Funktionen überprüfen Sie, dass alle entsprechenden Features in Nano Server verwendete Treiber ordnungsgemäß arbeiten.

### <a name="devicedevfundservernanofirmwareupdate"></a>Device.DevFund.Server.Nano.FirmwareUpdate

*Firmware Update Anforderungen für Server Nano*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

Alle Firmware Update-Tools und Dienstprogramme für die Verwendung auf Windows Server Nano vorgesehen müssen Installation mithilfe einer der folgenden Methoden unterstützt:

- Remote-Installation von Windows PowerShell oder WMI
- Lokale Installation von ein Befehlszeilentool, das ein Administrator auf Nano Server ausführen kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH

Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.

### <a name="devicedevfundservernanomonitoringandtelemetry"></a>Device.DevFund.Server.Nano.MonitoringAndTelemetry

*Anforderungen für Windows Server Nano Monitoring.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

Alle monitoring Tools, Dienstprogramme und Agents müssen Installation mithilfe einer der folgenden Methoden unterstützt:

- Remote-Installation von Windows PowerShell oder WMI
- Lokale Installation von ein Befehlszeilentool, das ein Administrator auf Nano Server ausführen kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH

Wenn das Tool, Dienstprogramm oder Agent auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.

Microsoft Azure-Stapel insbesondere muss alle Überwachung ohne Agents sein und Agents auf den Hosts nicht zulässig. Siehe auch "if implementiert' Goldbarsch Anforderung in der System.Server.Manageability.Redfish

### <a name="devicedevfundservernanooperateinservernano"></a>Device.DevFund.Server.Nano.OperateInServerNano

*Gerätetreiber müssen installieren, konfigurieren, bedient werden und in Windows Server Nano verwenden.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

**Beschreibung**

Der auf dem Windows Server Betriebssysteme bereitgestellten Hardwareplattform haben erheblich in den vergangenen zehn Jahren entwickelt. Sobald diese Grafik kleiner sind Systementwürfe für Kosten und Effizienz der Bereitstellung, die Kunden erwarten vollständig setup, bereitstellen, konfigurieren und verwalten diese mithilfe der minimale Befehlszeilenschnittstelle und automatisierte scripting von Windows Server Nano Hardware-Plattformen. Windows Server-Gerät, den Treiber in ähnlicher Weise wie für den Kunden diese Vorgänge ungehinderte unterschiedliche ermöglichen weiterentwickelt werden müssen.

Gerätetreiber muss veranschaulichen die Fähigkeit zum Installieren, konfigurieren Sie bedient werden und das Vorhandensein Abhängigkeit von der GUI nicht verwendet.

Hinweise zum Entwurf:

Alle Gerätetreiber, die diese Anforderung nicht erfüllt wird nicht auf Windows Server Nano-Systemen verwendet werden.

### <a name="devicedevfundservernanopatchandupdate"></a>Device.DevFund.Server.Nano.PatchAndUpdate

*Patchen von Anforderungen für Windows Server Nano.*

<table><tr><th>Gilt für</th><td><p>Windows Server 2016 X64</p></td></tr></table>

Alle Patches und Updates können offline installieren, muss im Rahmen der Erstellung des Image oder online.


<a name="device.devfund.server.pci"></a>
## <a name="devicedevfundserverpci"></a>Device.DevFund.Server.PCI

*PCI*

### <a name="devicedevfundserverpcipciaer"></a>Device.DevFund.Server.PCI.PCIAER

*Windows Server PCI Express-Geräten sind erforderlich, um erweiterte Fehlerberichterstattung unterstützen \[Microsoft Application\] wie in PCI Express Base Spezifikation Version 2.1 definiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Finden Sie unter Tabellen 6-2, 6-3, 6-4 und 6 bis 5 der PCI-Spezifikation unter wie Fehler in der Hardware erkannt werden, den standardmäßigen Schweregrad des Fehlers, und die erwartete Aktion der Agent erkennt den Fehler im Hinblick auf Fehler berichterstellung und Protokollierung.

Alle drei Methoden der Fehlerberichterstattung; Abschlussstatus, Fehlermeldungen, Fehler Weiterleitung\\Daten Missbrauch.

Abschlussstatus kann an einer bestimmten Anforderung einen Fehler zuordnen.

Fehlermeldungen Geben Sie an, wenn das Problem behebbaren oder nicht ist, und schwerwiegend oder nicht

Fehler-Weiterleitung\\Daten Missbrauch helfen zu bestimmen, ob ein bestimmter Schalter entlang des Pfads der TLP sozusagen

Die folgende Tabelle enthält die Fehler im Abschnitt 6.2 meldende erforderlich sind:

| Art von Fehlern                      | Erforderlich? | Aktion                                                         |
|-------------------------------------|-----------|----------------------------------------------------------------|
| ERR\_COR (behebbaren)              | Nein        | Keine Aktion, die nicht in der Ereignisanzeige protokolliert System führt keine Aktion aus. |
| ERR\_SCHWERWIEGEND ("schwerwiegend", nicht korrigieren) | Ja       | WHEA behandelt, und in der Ereignisanzeige protokolliert                       |
| ERR\_kein schwerwiegender FEHLER                       | Ja       | Keine                                                           |

<a name="device.devfund.statictools"></a>
## <a name="devicedevfundstatictools"></a>Device.DevFund.StaticTools

### <a name="devicedevfundstatictoolscaandsdv"></a>Device.DevFund.StaticTools.CAandSDV

*Entwicklung für enthält statische Analyse zur Verbesserung der Zuverlässigkeit mithilfe von Code Analysis (CA) und statische Treiber Verifier (SDV).*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Netzwerk- und Speicher Treiber Übermittlungen müssen Protokolldateien für statische Treiber Verifier (SDV) und Code-Analyse für Treiber (CA) enthalten.

**Hinweise zum Entwurf**

Statische Analysetools von Microsoft, nämlich Code Analysis für Treiber (CA) und statische Treiber Verifier (SDV) wurden gefunden werden sehr effektiv bei der Verbesserung der Zuverlässigkeit Treiber durch das Identifizieren von Codeprobleme, die andernfalls schwer zu finden sind würde.

-   **Nur Server:** Probleme bei der Zertifizierungsstelle und SDV ermittelt "Server: müssen beheben" sind müssen im Treibercode für die Kompatibilität Übermittlung korrigiert werden. Andere Probleme ermittelt werden in einem statischen Tools Protokoll gemeldet werden, aber es ist nicht erforderlich, diese Probleme zu beheben.

-   **Client nur:** Probleme durch Zertifizierungsstelle und SDV werden in eine Protokolldatei für statische aber nicht erforderlich, diese Probleme zu beheben ausgegeben werden.

Die resultierende DVL DateiAusgabe von statische Analysetools wird von der Hardware Lab-Kit für die Einbeziehung in das Gerät zum Absenden Paket erfasst werden.

**Gewusst wie: Erstellen**

-   [Code Analysis-Protokolle](http://go.microsoft.com/fwlink/p/?LinkId=723117)

-   [SDV-Protokolle](http://go.microsoft.com/fwlink/p/?LinkId=723119)

-   [Datei mit den Suchergebnissen DVL](http://go.microsoft.com/fwlink/p/?LinkId=723120)

**Hinweis:** Obwohl empfohlen, sind keine Anforderungen, die festlegen, dass die gesendeten und anschließend verteilten Treiber Binärdatei werden mit Microsoft Windows Device Kit oder andere Microsoft-Tool kompiliert.

**Hinweis:** Microsoft behält sich das Recht, die Anforderung in Zukunft frei die statische Analysetools anderen Gerätekategorien hinzufügen.

