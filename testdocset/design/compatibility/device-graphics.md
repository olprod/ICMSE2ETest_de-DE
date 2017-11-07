---
title: Device.Graphics
Description: "Anforderungen für die Basis Featuregruppe aller Graphic-Geräte erforderlich."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 9f31989982c9634669e612ba321fd453952615b7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicegraphics"></a>Device.Graphics

 - [Device.Graphics.AdapterBase](#device.graphics.adapterbase)
 - [Device.Graphics.AdapterRender.D3D101Core](#device.graphics.adapterrender.d3d101core)
 - [Device.Graphics.AdapterRender.D3D101WDDM11](#device.graphics.adapterrender.d3d101wddm11)
 - [Device.Graphics.AdapterRender.D3D101WDDM12](#device.graphics.adapterrender.d3d101wddm12)
 - [Device.Graphics.AdapterRender.D3D10ComputeShader](#device.graphics.adapterrender.d3d10computeshader)
 - [Device.Graphics.AdapterRender.D3D10Core](#device.graphics.adapterrender.d3d10core)
 - [Device.Graphics.AdapterRender.D3D10D3D11LogicOps](#device.graphics.adapterrender.d3d10d3d11logicops)
 - [Device.Graphics.AdapterRender.D3D10Multisampling4X](#device.graphics.adapterrender.d3d10multisampling4x)
 - [Device.Graphics.AdapterRender.D3D10Multisampling8X](#device.graphics.adapterrender.d3d10multisampling8x)
 - [Device.Graphics.AdapterRender.D3D10WDDM11](#device.graphics.adapterrender.d3d10wddm11)
 - [Device.Graphics.AdapterRender.D3D10WDDM12](#device.graphics.adapterrender.d3d10wddm12)
 - [Device.Graphics.AdapterRender.D3D111Core](#device.graphics.adapterrender.d3d111core)
 - [Device.Graphics.AdapterRender.D3D11ASTC](#device.graphics.adapterrender.d3d11astc)
 - [Device.Graphics.AdapterRender.D3D11ConservativeRasterization](#device.graphics.adapterrender.d3d11conservativerasterization)
 - [Device.Graphics.AdapterRender.D3D11Core](#device.graphics.adapterrender.d3d11core)
 - [Device.Graphics.AdapterRender.D3D11DoublePrecisionShader](#device.graphics.adapterrender.d3d11doubleprecisionshader)
 - [Device.Graphics.AdapterRender.D3D11DriverCommandLists](#device.graphics.adapterrender.d3d11drivercommandlists)
 - [Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation](#device.graphics.adapterrender.d3d11driverconcurrentobjectcreation)
 - [Device.Graphics.AdapterRender.D3D11Level9WDDM12](#device.graphics.adapterrender.d3d11level9wddm12)
 - [Device.Graphics.AdapterRender.D3D11Level9WDDM13](#device.graphics.adapterrender.d3d11level9wddm13)
 - [Device.Graphics.AdapterRender.D3D11PartialPrecision](#device.graphics.adapterrender.d3d11partialprecision)
 - [Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews](#device.graphics.adapterrender.d3d11rasterizerorderedviews)
 - [Device.Graphics.AdapterRender.D3D11StencilReference](#device.graphics.adapterrender.d3d11stencilreference)
 - [Device.Graphics.AdapterRender.D3D11TypedUAVLoads](#device.graphics.adapterrender.d3d11typeduavloads)
 - [Device.Graphics.AdapterRender.D3D11WDDM12](#device.graphics.adapterrender.d3d11wddm12)
 - [Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader](#device.graphics.adapterrender.d3d11wddm12doubleprecisionshader)
 - [Device.Graphics.AdapterRender.D3D11WDDM13](#device.graphics.adapterrender.d3d11wddm13)
 - [Device.Graphics.AdapterRender.D3D11WDDM20](#device.graphics.adapterrender.d3d11wddm20)
 - [Device.Graphics.AdapterRender.D3D11WDDM21](#device.graphics.adapterrender.d3d11wddm21)
 - [Device.Graphics.AdapterRender.D3D12ASTC](#device.graphics.adapterrender.d3d12astc)
 - [Device.Graphics.AdapterRender.D3D12ConservativeRasterization](#device.graphics.adapterrender.d3d12conservativerasterization)
 - [Device.Graphics.AdapterRender.D3D12Core](#device.graphics.adapterrender.d3d12core)
 - [Device.Graphics.AdapterRender.D3D12Multiadapter](#device.graphics.adapterrender.d3d12multiadapter)
 - [Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews](#device.graphics.adapterrender.d3d12rasterizerorderedviews)
 - [Device.Graphics.AdapterRender.D3D12StencilReference](#device.graphics.adapterrender.d3d12stencilreference)
 - [Device.Graphics.AdapterRender.D3D12TypedUAVLoads](#device.graphics.adapterrender.d3d12typeduavloads)
 - [Device.Graphics.AdapterRender.D312VolumeTiledResources](#device.graphics.adapterrender.d312volumetiledresources)
 - [Device.Graphics.IndirectDisplay.Wired](#device.graphics.indirectdisplay.wired)
 - [Device.Graphics.WDDM](#device.graphics.wddm)
 - [Device.Graphics.WDDM.Display](#device.graphics.wddm.display)
 - [Device.Graphics.WDDM.DisplayRender](#device.graphics.wddm.displayrender)
 - [Device.Graphics.WDDM.Render](#device.graphics.wddm.render)
 - [Device.Graphics.WDDM11](#device.graphics.wddm11)
 - [Device.Graphics.WDDM11.Display](#device.graphics.wddm11.display)
 - [Device.Graphics.WDDM11.DisplayRender](#device.graphics.wddm11.displayrender)
 - [Device.Graphics.WDDM11.DisplayRender.D3D9Overlay](#device.graphics.wddm11.displayrender.d3d9overlay)
 - [Device.Graphics.WDDM11.Render](#device.graphics.wddm11.render)
 - [Device.Graphics.WDDM11.Render.DXVAHD](#device.graphics.wddm11.render.dxvahd)
 - [Device.Graphics.WDDM12](#device.graphics.wddm12)
 - [Device.Graphics.WDDM12.Display](#device.graphics.wddm12.display)
 - [Device.Graphics.WDDM12.DisplayOnly](#device.graphics.wddm12.displayonly)
 - [Device.Graphics.WDDM12.DisplayRender](#device.graphics.wddm12.displayrender)
 - [Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent](#device.graphics.wddm12.displayrender.processingstereoscopicvideocontent)
 - [Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt](#device.graphics.wddm12.displayrender.runtimepowermgmt)
 - [Device.Graphics.WDDM12.Render](#device.graphics.wddm12.render)
 - [Device.Graphics.WDDM12.RenderOnly](#device.graphics.wddm12.renderonly)
 - [Device.Graphics.WDDM12.StandbyHibernateFlags](#device.graphics.wddm12.standbyhibernateflags)
 - [Device.Graphics.WDDM13](#device.graphics.wddm13)
 - [Device.Graphics.WDDM13.DisplayRender](#device.graphics.wddm13.displayrender)
 - [Device.Graphics.WDDM13.DisplayRender.CoolingInterface](#device.graphics.wddm13.displayrender.coolinginterface)
 - [Device.Graphics.WDDM13.DisplayRender.WirelessDisplay](#device.graphics.wddm13.displayrender.wirelessdisplay)
 - [Device.Graphics.WDDM13.EnhancedPowerManagement](#device.graphics.wddm13.enhancedpowermanagement)
 - [Device.Graphics.WDDM13.Render](#device.graphics.wddm13.render)
 - [Device.Graphics.WDDM20](#device.graphics.wddm20)
 - [Device.Graphics.WDDM20.Core](#device.graphics.wddm20.core)
 - [Device.Graphics.WDDM20.DisplayRender](#device.graphics.wddm20.displayrender)
 - [Device.Graphics.WDDM20.Display.VirtualModeSupport](#device.graphics.wddm20.display.virtualmodesupport)
 - [Device.Graphics.WDDM21](#device.graphics.wddm21)

<a name="device.graphics.adapterbase"></a>
## <a name="devicegraphicsadapterbase"></a>Device.Graphics.AdapterBase

*Die Basis Featuregruppe durch alle Graphic-Geräte benötigt.*

### <a name="devicegraphicsadapterbaseapplicationverifier"></a>Device.Graphics.AdapterBase.ApplicationVerifier

*Graphics-Treiberkomponenten müssen die Application Verifier Testkriterien entsprechen.*

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

Alle im Benutzermodus Module (DLL- oder .exe-Dateien), die Teil einer Graphics-Treiber sind erfüllen müssen, die Testkriterien für Application Verifier-Tests. Während des Testens des Treibers müssen Application Verifier Prozessen für die aktiviert werden, in dem die Treiber Module ausgeführt werden. Application Verifier verursacht eine Unterbrechung, wenn ein Fehler erkannt wird.

Graphics-Treiber ist AppVerifier erforderlich für kritische ausführbare Dateien (d. h., DWM.exe als Beispiel), verwendet, um die Stabilität oder die Stabilität von Graphics-Treiber zu testen.
Darüber hinaus muss Application Verifier für IHVs Control Panel ausführbare Datei im Rahmen dieser Anforderung aktiviert werden.
Diese Tests Application Verifier müssen während der Tests für die Prozesse eingeschaltet sein:

-   com
-   Ausnahmen
-   Handles
-   Heaps
-   InputOutput
-   Verlust
-   Sperren
-   Arbeitsspeicher
-   RPC
-   Threadpool
-   TLS
-   hängt

### <a name="devicegraphicsadapterbasedriverversion"></a>Device.Graphics.AdapterBase.DriverVersion

*Die Treiberdateien für eine Grafikkarte oder Chipsatz haben Dateiversionen ordnungsgemäß formatiert.*

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

Die Treiber-Informationsdatei (INF), muss Kernel-Modus-Treiber (sys), und Benutzer-Modus-Treiber (DLL) Version Dateiinformationen übereinstimmen. Darüber hinaus identifiziert Versionsinformationen für alle Dateien der \[SignatureAttributes\] Abschnitt der INF als PETrust Binärdateien übereinstimmen müssen die. inf-Datei. Es wird empfohlen, die Version Dateiinformationen für zusätzliche Binärdateien in einer Treiber Paket Übereinstimmung die. inf-Datei.

Um den vorherrschenden Datei Versioning Erfordernissen für legacy-Betriebssysteme werden, muss die Datei Version Formatierung eine automatische Telefonzentrale folgen. BB. CCCCC. DDDDD pattern Where an:

-   AA gibt an, die Treiberversion Modell der am häufigsten fähigen Geräts in der INF-aufgeführt

-   BB (WDDM 1.2 Treiber und höher)

    -   Gibt an, die höchsten verfügbaren D3D Feature der am häufigsten fähigen Geräts aufgeführt, die in der INF-

-   BB (für WDDM v1. 1-Treiber und nach unten)

    -   Gibt an die höchsten verfügbaren DDI-Version von der am häufigsten Gerät aufgeführt, die in der INF-unterstützt

-   CCCCC ist eine Zahl bis zu 5 Ziffern zwischen 0 und 65535, die vom Anbieter ausgewählt

-   DDDDD ist eine Zahl bis zu 5 Ziffern zwischen 0 und 65535, die vom Anbieter ausgewählt

Werte für AA dar:

| Driver Model | AA Wert |
|--------------|----------|
| WDDM v2.x    | 21       |
| WDDM v2. 0    | 20       |
| WDDM Version 1.3    | 10       |
| WDDM v1. 2    | 9        |
| WDDM v1. 1    | 8        |
| WDDM v1. 0    | 7        |
| XDDM         | 6        |

Werte für BB-Feld (WDDM v1. 2 und höher):

| Ebene DirectX-Funktion | BB Wert |
|-----------------------|----------|
| 12\_x                 | 21       |
| 12\_1                 | 20       |
| 12\_0                 | 19       |
| 11\_1                 | 18       |
| 11\_0                 | 17       |
| 10\_1                 | 16       |
| 10\_0                 | 15       |
| 9\_3                  | 14       |
| 9\_2                  | 14       |
| 9\_1                  | 14       |

Werte für BB Feld (WDDMv1.1 und früher):

| DDI-version                      | BB Wert |
|----------------------------------|----------|
| D3D11-DDI Feature auf 11\_0 | 17       |
| D3D11-DDI Feature auf 10    | 16       |
| D3D10 DDI                        | 15       |
| D3D9 DDI                         | 14       |

**Beispiel**:

HINWEIS: Es ist nicht erforderlich, d. h. Nummern mit vorangestellten Nullen aufzufüllen, 123 muss nicht als 00123 für die Felder CCCCC oder DDDDD dargestellt werden. In früheren Versionen des Windows-Betriebssystems wurden die letzten beiden Felder 4 Ziffern, d. h., CCCC. DDDD. In den Beispielen für Treiberversionen vor Windows 10 und WDDM v2. 0 müssen daher nur 4 Ziffern.

-   Windows Vista WDDM 1.0:

    -   D3d9 DDI Treiber können 7.14.0000.0000 auf 7.14.9999.9999 verwenden.

    -   D3D10 DDI Treiber können 7.15.0000.0000 auf 7.15.9999.9999 verwenden.

-   Windows 7 WDDM v1. 1:

    -   D3d9 DDI Treiber können 8.14.0000.0000 zu 8.14.9999.9999 verwenden.

    -   D3D10 DDI Treiber können 8.15.0000.0000 auf 8.15.9999.9999 verwenden.

    -   D3D11 DDI mit FL\_10\_0 Treiber können 8.16.0000.0000 auf 8.16.9999.9999

    -   D3D11 DDI mit FL\_11\_0 Treiber können 8.17.0000.0000 auf 8.17.9999.9999

-   Treiber für Windows 8 WDDM v1. 2:

    -   FL\_10\_0 Hardware können 9.15.0000.0000 auf 9.15.9999.9999

    -   FL\_10\_1 Hardware können 9.16.0000.0000 auf 9.16.9999.9999

    -   FL\_11\_0 Hardware können 9.17.0000.0000 auf 9.17.9999.9999

    -   FL\_11\_1 ww können 9.18.0000.0000 zu 9.18.9999.9999

-   Windows 8.1 WDDM v1. 3-Treiber:

    -   FL\_10\_0 ww können 10.15.0000.0000 zu 10.15.9999.9999

    -   FL\_10\_1 Hardware können 10.16.0000.0000 auf 10.16.9999.9999

    -   FL\_11\_0 Hardware können 10.17.0000.0000 auf 10.17.9999.9999

    -   FL\_11\_1 Hardware können 10.18.0000.0000 auf 10.18.9999.9999

-   Windows 10 WDDM v2. 0-Treiber:

    -   FL\_11\_1 Hardware 20.18.0000.0000 zu 20.18 verwenden kann. 65535.65535

    -   FL\_12\_0 Hardware können 20.19.0000.0000 auf 20.19. 65535.65535

    -   FL\_12\_1 Hardware 20.20.0000.0000 zu 20.20 verwenden kann. 65535.65535

**Wichtiger Hinweis:**

Ein obligatorische Test in der HLK Zertifizierung Wiedergabeliste für Windows 10 höher als 10586 die oben beschriebenen Regeln erzwingen wird erstellt. Der Test wird für die älteren Betriebssystemversionen optional sein. Für Windows 10 Builds nach 10586 wurde auf 2.1 WDDM-Version aktualisiert. Eine andere Möglichkeit, diese Ansicht ist, dass die obligatorische Anforderung gilt nur für Treiber, die für WDDM 2.1 oder höher integriert sind.

### <a name="devicegraphicsadapterbasepowermanagementcompliance"></a>Device.Graphics.AdapterBase.PowerManagementCompliance

*Eine Grafikkarte muss VESA ACPI Power Management Spezifikationen und dem Standbymodus System aktivieren einhalten.*

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

Zur Sicherstellung der richtigen Implementierung des Betriebssystems gesteuerte Power Management müssen auf Grafik Adapter und Gerätetreibern reagieren:

-   Erforderlich (D0 und D3) Power Gerätestatus in das WDK hervorgehoben

-   Betriebssystem Power Management für ACPI Power Zustände

-   \*VESA BIOS Power Management-Funktionen, die VGA-ROM-BIOS-Services für die Verwaltung der Stromversorgung Erweiterungen definiert. (\*Dieser Zeile gilt nicht für UEFI GOP-basierte Plattformen.)

### <a name="devicegraphicsadapterbaseregistryentries"></a>Device.Graphics.AdapterBase.RegistryEntries

*Eine Anwendung, die den Treiber für ein Grafikgerät installiert, muss die erforderlichen Registrierungseinträge erstellen.*

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

Die folgenden Registrierungseinträge müssen während Grafiktreiber-Installation erstellt werden:
 

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\InstalledDisplayDrivers: Dieser Schlüssel sollte der Name des Treibers im Benutzermodus enthalten.

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.MemorySize

Die Werte werden unter Hardwareinformationen vom WDDM-Treiber geschrieben:

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.ChipType

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.DACType

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.AdapterString

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.BiosString

-   REG\_BINARY: HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\Video\\TEIL\_GUID\\ID\\HardwareInformation.MemorySize

Die folgenden Direktiven INF-Datei müssen in der INF-Datei enthalten sein:

-   Feature Score - ist dies eine allgemeine Installation-Einstellung, die von allen WDDM-Treiber unterstützt werden muss.

-   Kopieren Sie Flags Richtlinie Support Plug & Play-beenden

-   Treiber\\Dienste Starttyp Richtlinie

-   Funktion außerkraftsetzungseinstellungen OpenGL deaktivieren

-   \[Version\] Abschnitt Direktiven

-   \[SourceDiskNames\] Abschnitt Direktiven

-   Allgemeine x 64 Direktiven

-   Allgemeine \[installieren\] Abschnitt Direktiven

Die DLL-Treiber benötigen eine korrekt formatierten Dateiversion wie in der Anforderung Device.Graphics.AdapterBase.DriverVersion definiert.

### <a name="devicegraphicsadapterbaserunfromdriverstore"></a>Device.Graphics.AdapterBase.RunFromDriverStore

*Die Treiberdateien für eine Grafikkarte oder Chipsatz werden aus dem Speicher-Treiber geladen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Treiber müssen geschrieben werden, damit ihre Komponenten (Benutzer-Modus-Treiber, Treiber für den Kernelmodus usw.) direkt aus dem Speicher Treiber ausgeführt werden können. Sie benötigen keine Abhängigkeiten in System Pfaden wie Windows\\System32. Dazu gehören auswählen die Option *Ausführen aus Driver Store* in der Treiber-Informationsdatei (INF).

Beachten Sie, dass nach dieser Änderung eindeutige Namen oder absolute Pfade verwendet werden müssen Abhängigkeiten geladen werden. Für Treiber auswählen, die zusätzliche optionale Side-by-Side-Funktion zu implementieren müssen Dienstnamen auch pro Treiberversion oder Hardware-Klasse eindeutig sein.

**Unternehmensvorgabe:**

Treiber aus dem Speicher Treiber ausführen müssen, die das Upgrade zu verbessert. Sie können damit auch Herstellern zusätzliche "Nebeneinander" Funktionen unterstützt, wenn sie also auswählen – auf diese Weise beispielsweise das Szenario mit zwei oder mehr GPUs aus anderen Familien in dem gleichen Computer ausführen anderer Treiber Version können.

Ein weiterer Vorteil besteht darin, dass der Datenträger Speicherbedarf reduziert, da der Treiber im Driver Store trotzdem vorhanden sein müssen, und eine weitere Kopie in Windows\\System32 Duplizierung erzeugt.

**Erzwingen**:

Die Einstellungen in der Treiber-Informationsdatei (INF) werden durch einen Test HLK überprüft werden, für Windows 10 höher als 10586 erstellt.

### <a name="devicegraphicsadapterbasesubsystemresettable"></a>Device.Graphics.AdapterBase.SubsystemResettable

*Ein Subsystem Grafiken muss zurücksetzbar auf eine normale Betriebsstatus sein.*

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

Wenn die GPU aus irgendeinem Grund reagiert, unabhängig von der nacheinander, die Hardware arbeitet es zurücksetzbar auf eine normale Betriebsstatus muss. Dies bedeutet im Wesentlichen, dass TDR von jeder GPU unterstützt werden muss.

Hybrid-System soll behandelt TDR genau wie nicht-Hybrid-System und Mechanismus, um einen (oder beide) zurücksetzen die GPU auf das System in einen funktionsfähigen Zustand zurück, wenn das Betriebssystem ein hängen erkennt.

*Hinweise zum Entwurf*

Die Möglichkeit zum Zurücksetzen der GPU ist unabhängig von der aktuelle Bearbeitungsstatus des Systems.

### <a name="devicegraphicsadapterbasesymbols"></a>Device.Graphics.AdapterBase.Symbols

*Symbole müssen zusammen mit der Treiber für die Zertifizierung übermittelt werden*

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

Wenn Graphics-Treiber für die Zertifizierung gesendet werden, muss die übereinstimmende Symboldateien gleichzeitig über den WHKL "Symbole hinzufügen" Workflow übermittelt werden. Microsoft setzt übereinstimmenden Symbole intern für die Fehleranalyse. Ohne die Symbole, ist es unwahrscheinlich Microsoft können sehen, Analysieren von Fehlern und Partner bei der Diagnose von Treiberproblemen unterstützen. Symbole für die folgenden Dateien müssen eingeschlossen werden:

-   SYS-Dateien

-   DLL-Dateien in den \[SignatureAttributes\] Teil der Treiber INF als "PETrust" Binärdateien

Symbole können durch "öffentlich" oder "Privat" pro [MSDN Anweisungen](https://msdn.microsoft.com/en-us/library/windows/hardware/ff550665.aspx).

<a name="devicegraphicsadapterrender"></a>Device.Graphics.AdapterRender
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*Das Feature Rendern eines Geräts Grafiken.*

### <a name="devicegraphicsadapterrenderminimumdirectxlevel"></a>Device.Graphics.AdapterRender.MinimumDirectXLevel

*Eine Grafikkarte muss die Mindestanforderungen für Hardware Acceleration Funktionen implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Das Anzeige-Subsystem ist erforderlich, um die Implementierung der DirectX 9-Hardware-Spezifikation und der Treiber ist erforderlich, um über die D3D9 UMD DDI die Funktionen von Direct3D 10 Feature Ebene 9 verfügbar gemacht\_3 wie folgt in MSDN:

-   <http://msdn.Microsoft.com/en-us/library/ff476876.aspx>

-   <http://msdn.Microsoft.com/en-us/library/ff476150.aspx>

-   <http://msdn.Microsoft.com/en-us/library/ff476149.aspx>

-   <http://msdn.Microsoft.com/en-us/library/ff471324.aspx>

HINWEIS: Für Windows Server sind Grafiktreiber optional. Anzeigen nur Grafiktreiber werden nicht gerendert, sodass sie keine DirectX Mindestanforderung verfügen. Wenn ein vollständige Grafiktreiber auf einem Server geladen wird, muss er auf die mindestens DirectX Feature entsprechen.

### <a name="devicegraphicsadapterrenderrgbframebuffer"></a>Device.Graphics.AdapterRender.RGBFrameBuffer

*Ein Anzeige Chipsatz muss die angegebene Komponente Reihenfolge und endian Darstellung einer 8-Bit pro Pixel oder größer Ganzzahl RGB-Frame Puffer Formate implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Für eine N Bit pro Komponente RGB-Puffer Rahmenformat die niedrigsten Bits N müssen die Blaukomponente enthalten, die nächsten N Bits müssen den Wert der Grünkomponente enthalten, die nächsten N Bits müssen enthalten, die Rotkomponente sowie die verbleibenden 32-(3 x N) Bits Alpha enthalten können. Der resultierende 32-Bit-Wert muss im Arbeitsspeicher in little-Endian-Format gespeichert werden.

### <a name="devicegraphicsadapterrenderyuvsupport"></a>Device.Graphics.AdapterRender.YUVSupport

*Ein Anzeigetreiber, DER YUV Strukturen unterstützt, muss Strukturen und Funktionen ordnungsgemäß verarbeitet werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn die Hardware YUV Textur Flächen unterstützt und die Funktion wird gemeldet, klicken Sie dann muss der Treiber diese Flächen ohne anspruchsvolleren Transformationen verarbeiten und ordnungsgemäß ausgeführt werden können.

<a name="device.graphics.adapterrender.d3d101core"></a>
## <a name="devicegraphicsadapterrenderd3d101core"></a>Device.Graphics.AdapterRender.D3D101Core

*Hauptfeature D3D 10.1*

### <a name="devicegraphicsadapterrenderd3d101cored3d101coreprimary"></a>Device.Graphics.AdapterRender.D3D101Core.D3D101CorePrimary

*Wenn das Grafikgerät Direct3D 10.1 unterstützt, müssen sie die Direct3D 10.1 und DXGI Spezifikationen entsprechen.*

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

Wenn die Grafikgeräte implementiert Direct3D 10.1, müssen alle in der *Spezifikation Direct3D 10.1* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 10.1 Features ermöglichen. 

Da Direct3D 10.1 eine Obermenge von Direct3D 10 ist, erfordert die Implementierung der Direct3D 10.1 auch die Unterstützung der Featuregruppe Direct3D 10.  

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber einschließlich diese Features für die Kopfzeile DXGI DDI definierten verfügbar gemacht werden. 

<a name="device.graphics.adapterrender.d3d101wddm11"></a>
## <a name="devicegraphicsadapterrenderd3d101wddm11"></a>Device.Graphics.AdapterRender.D3D101WDDM11

*D3D 10.1 Hauptfeature mit WDDM 1.1 Ergänzungen*

### <a name="devicegraphicsadapterrenderd3d101wddm11d3d101v11primary"></a>Device.Graphics.AdapterRender.D3D101WDDM11.D3D101v11Primary

*Wenn ein WDDM 1.1 Grafikgerät Direct3D 10.1 unterstützt, muss es die Direct3D 10.1 und DXGI Spezifikationen einhalten und BGRA unterstützen.*

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

Wenn die Grafikhardware Direct3D 10.1 implementiert wird, müssen alle in der *Spezifikation Direct3D 10.1* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 10.1 Features ermöglichen. 

Da Direct3D 10.1 eine Obermenge von Direct3D 10 ist, erfordert die Implementierung von Direct3D 10.1 auch Unterstützung für die Featuregruppe Direct3D 10.  Darüber hinaus stehen die folgenden Features, die ursprünglich in der D3D9 Hardware-Spezifikation definierten jetzt erforderlich:

-   BGRA

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber einschließlich diese Features für die Kopfzeile DXGI DDI definierten verfügbar gemacht werden. 

<a name="device.graphics.adapterrender.d3d101wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d101wddm12"></a>Device.Graphics.AdapterRender.D3D101WDDM12

*D3D 10.1 Hauptfeature mit WDDM 1.2 Ergänzungen*

### <a name="devicegraphicsadapterrenderd3d101wddm12d3d101v12primary"></a>Device.Graphics.AdapterRender.D3D101WDDM12.D3D101v12Primary

*Wenn ein WDDM 1.2 Grafikgerät Direct3D 10.1 unterstützt, müssen die Direct3D 10.1, DXGI und D3D10 Teil der Direct3D 11.1 Feature Spezifikationen entsprechen.*

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

Wenn die Grafikhardware Direct3D 10.1 implementiert wird, müssen sie die Anforderungen erfüllen, die in der *Spezifikation Direct3D 10.1* definiert und muss eine ausreichende Leistung Direct3D 10.1 Features ermöglichen. 

Da Direct3D 10.1 eine Obermenge von Direct3D 10 ist, erfordert die Implementierung der Direct3D 10.1 auch Unterstützung für die Featuregruppe Direct3D 10.  Darüber hinaus stehen die folgenden Features, die ursprünglich in der Spezifikation für D3D9 Hardware definiert jetzt erforderlich:

-   BGRA
-   Hälfte Genauigkeit Pixelformate (5551, 565, 4444)
-   Dieselbe Oberfläche Blts

Finden Sie in der *Direct3D 11.1 Features Spec* vollständige Details alle neuen Features erforderlich, um mit einem WDDM 1.2 Treiber für D3D10 + Hardware verfügbar gemacht werden.

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber, einschließlich diese Features für die Kopfzeile DXGI DDI definiert verfügbar gemacht werden. 

 

<a name="device.graphics.adapterrender.d3d10computeshader"></a>
## <a name="devicegraphicsadapterrenderd3d10computeshader"></a>Device.Graphics.AdapterRender.D3D10ComputeShader

*Direct3D 10 Shadermodell 4\_ \* berechnen Shader Funktionalität*

### <a name="devicegraphicsadapterrenderd3d10computeshaderd3d10corec"></a>Device.Graphics.AdapterRender.D3D10ComputeShader.D3D10CoreC

*Wenn die Grafikhardware Direct3D 10 Shader Model 4 implementiert\_ \* berechnen Shader Funktionalität muss an die Hardwarespezifikationen D3D11 entsprechen.*

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

Die Spezifikation D3D11 optional implementieren Shader Model 4 ermöglicht\_ \* Shader Compute-Funktionalität auf Direct3D 10 Hardware.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D11 Hardware*entsprechen. 

<a name="device.graphics.adapterrender.d3d10core"></a>
## <a name="devicegraphicsadapterrenderd3d10core"></a>Device.Graphics.AdapterRender.D3D10Core

*Hauptfeature D3D 10*

### <a name="devicegraphicsadapterrenderd3d10cored3d10coreprimary"></a>Device.Graphics.AdapterRender.D3D10Core.D3D10CorePrimary

*Wenn ein Grafikgerät Direct3D 10 unterstützt, müssen sie die Direct3D 10 und DXGI Spezifikationen entsprechen.*

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

Wenn die Grafikhardware Direct3D 10 implementiert wird, müssen in der *Spezifikation Direct3D 10* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 10-Features ermöglichen. 

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber, einschließlich diese Features für die Kopfzeile DXGI DDI definiert verfügbar gemacht werden. Die folgende Liste enthält einige der erforderlichen Features werden aufgerufen in der Spezifikation für Direct3D 10:

-   Geometrieshader
-   Streamausgabe
-   Integer-Befehlssatz
-   Neue komprimierte Formate
-   Rendern auf Scheitelpunkt Puffer
-   Cube-Zuordnung zu rendern
-   Rendern auf Datenträger

<a name="device.graphics.adapterrender.d3d10d3d11logicops"></a>
## <a name="devicegraphicsadapterrenderd3d10d3d11logicops"></a>Device.Graphics.AdapterRender.D3D10D3D11LogicOps

*D3D10 D3D11 Logik Vorgängen*

### <a name="devicegraphicsadapterrenderd3d10d3d11logicopsd3d10cored"></a>Device.Graphics.AdapterRender.D3D10D3D11LogicOps.D3D10CoreD

*Wenn die Grafikhardware Logik Vorgängen Funktionalität implementiert wird, muss die Hardwarespezifikationen D3D11 entsprechen.*

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

Die zulässige D3D11.1 zum Implementieren von Geschäftslogik Vorgängen Funktionalität optional auf D3D10, D3D10.1 und D3D11 Hardware.   Wenn die Hardware unterstützt und Unterstützung für diese Funktionalität macht, muss es gemäß Definition in der *Spezifikation für D3D11.1 Hardware*Spezifikationen für dieses Feature entsprechen. 

<a name="device.graphics.adapterrender.d3d10multisampling4x"></a>
## <a name="devicegraphicsadapterrenderd3d10multisampling4x"></a>Device.Graphics.AdapterRender.D3D10Multisampling4X

*D3D10 Multisampling (4 X)*

### <a name="devicegraphicsadapterrenderd3d10multisampling4xd3d10corea"></a>Device.Graphics.AdapterRender.D3D10Multisampling4X.D3D10CoreA

*Wenn die Grafikhardware D3D10 implementiert 4 x Multisampling, muss die Hardwarespezifikationen D3D10 entsprechen.*

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

Die zulässige D3D10 für die Implementierung von 4 X Multisampling optional.   Wenn die Hardware außerdem Unterstützung zählen und der Treiber diese Funktionalität verfügbar macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D10 Hardware*entsprechen. 

<a name="device.graphics.adapterrender.d3d10multisampling8x"></a>
## <a name="devicegraphicsadapterrenderd3d10multisampling8x"></a>Device.Graphics.AdapterRender.D3D10Multisampling8X

* Direct3D 10 Multisampling (8 X)

### <a name="devicegraphicsadapterrenderd3d10multisampling8xd3d10coreb"></a>Device.Graphics.AdapterRender.D3D10Multisampling8X.D3D10CoreB

*Wenn die Grafikhardware Direct3D 10 8 X Multisampling implementiert wird, muss es an die Hardwarespezifikationen Direct3D 10 entsprechen.*

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

Die zulässige D3D10 für die Implementierung von 8 X Multisampling optional.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D10 Hardware*entsprechen. 

<a name="device.graphics.adapterrender.d3d10wddm11"></a>
## <a name="devicegraphicsadapterrenderd3d10wddm11"></a>Device.Graphics.AdapterRender.D3D10WDDM11

*Hauptfeature mit WDDM 1.1 Ergänzungen D3D 10*

### <a name="devicegraphicsadapterrenderd3d10wddm11d3d10v11primary"></a>Device.Graphics.AdapterRender.D3D10WDDM11.D3D10v11Primary

*Wenn die Grafikhardware Direct3D 10 implementiert und der Treiber WDDM1.1 ist, müssen sie entsprechen den DXGI Spezifikationen und Direct3D 10 und BGRA unterstützen.*

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

Wenn die Grafik Hardware Direct3D 10 implementiert und der Treiber WDDM1.1 ist, müssen in der *Spezifikation Direct3D 10* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 10 Features ermöglichen. Darüber hinaus stehen die folgenden Features, die ursprünglich in der Spezifikation D3D9 Hardware definierten jetzt erforderlich:

-   BGRA

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber einschließlich diese Features für die Kopfzeile DXGI DDI definierten verfügbar gemacht werden. Die folgende Liste enthält einige der erforderlichen Features werden in der Spezifikation für Direct3D 10 heraus aufgerufen:

-   Geometrieshader
-   Streamausgabe
-   Integer-Befehlssatz
-   Neue komprimierte Formate
-   Rendern auf Scheitelpunkt Puffer
-   Cube-Zuordnung zu rendern
-   Rendern auf Datenträger

<a name="device.graphics.adapterrender.d3d10wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d10wddm12"></a>Device.Graphics.AdapterRender.D3D10WDDM12

*Hauptfeature mit WDDM 1.2 Ergänzungen D3D 10*

### <a name="devicegraphicsadapterrenderd3d10wddm12d3d10v12primary"></a>Device.Graphics.AdapterRender.D3D10WDDM12.D3D10v12Primary

*Wenn Grafikhardware Direct3D 10 implementiert und der Treiber WDDM1.2 ist, müssen sie den Direct3D 10, DXGI und die D3D10 Ergänzungen in den Direct3D 11.1 Feature Spezifikationen entsprechen.*

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

Wenn die Grafik Hardware Direct3D 10 implementiert und der Treiber WDDM1.2 ist, müssen in der *Spezifikation Direct3D 10* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 10 Features ermöglichen. Darüber hinaus stehen die folgenden Features, die ursprünglich in der Spezifikation D3D9 Hardware definierten jetzt erforderlich:

-   BGRA
-   Hälfte Genauigkeit Pixelformate (5551, 565, 4444)
-   Dieselbe Oberfläche Blts

 
Finden Sie in der *Direct3D 11.1 Features Spec* vollständige Details alle neuen Features erforderlich, um mit einem WDDM 1.2 Treiber für D3D10 + Hardware verfügbar gemacht werden.

Alle Features erforderlich, die für diese Spezifikation müssen vom Gerätetreiber einschließlich diese Features für die Kopfzeile DXGI DDI definierten verfügbar gemacht werden. Die folgende Liste enthält einige der erforderlichen Features werden aufgerufen in der Spezifikation für Direct3D 10:

-   Geometrieshader
-   Streamausgabe
-   Integer-Befehlssatz
-   Neue komprimierte Formate
-   Rendern auf Scheitelpunkt Puffer
-   Cube-Zuordnung zu rendern
-   Rendern auf Datenträger

### <a name="devicegraphicsadapterrenderd3d10wddm12stereoscopic3darraysupport"></a>Device.Graphics.AdapterRender.D3D10WDDM12.Stereoscopic3DArraySupport

*WDDM1.2 Treiber müssen Stereoskopisches 3D in D3D durch Hinzufügen von Unterstützung für erweiterte Arrays unterstützen.*

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

Unterstützung von WDDM 1.2 erforderlich
 

| DDI oder feature                                                                                                                                       | WDDM 1.1                    | WDDM 1.2                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|---------------------------------------------------|
| Erstellung von Backbuffers (und Grundfarben) mit D3D10DDIARG\_CREATERESOURCE & D3D11DDIARG\_CREATERESOURCE                                              | Beschränkt auf ArraySize = 1 | Allgemeiner (engl.), ArraySize = 2                      |
| UM DXGI Backbuffer DDIs (DXGI\_DDI\_ARG\_BLT, DXGI\_DDI\_ARG\_DREHEN\_RESSOURCE\_IDENTITÄTEN, DXGI\_DDI\_ARG\_VORHANDEN, DXGI\_DDI\_ARG\_SETDISPLAYMODE) | Beschränkt auf backbuffers   | Gleiche, aber einschließlich Stereo Back Puffer           |
| Präsentation im Allgemeinen (Kernel und Benutzer)                                                                                                            | Beschränkt auf backbuffers   | Gleiche, aber einschließlich Stereo Back Puffer           |
| Freigabe                                                                                                                                              | Beschränkt auf ArraySize = 1 | Allgemeiner (engl.) auf *eine beliebige* ArraySize (einschließlich &gt; 2) |
| GDI-interop                                                                                                                                          | Beschränkt auf ArraySize = 1 | Allgemeiner (engl.) auf *eine beliebige* ArraySize (einschließlich &gt; 2) |
| HLSL kein Array Demo Deklarationen                                                                                                                | Beschränkt auf ArraySize = 1 | Allgemeiner (engl.) auf *eine beliebige* ArraySize (einschließlich &gt; 2) |

 
HLSL kein Array Demo Deklarationen gibt an, zulassen bestimmter Shader dieses Beispiel aus Single-Subresource-Ressourcen derzeit, die auch Single-Subresource-Ansichten von Ressourcen mit mehreren Subresources (Beispiel).
 
Beachten Sie, dass Treiber müssen erweiterte Array für Stereo 3D APIs unterstützt, aber bei Fullscreen exklusive Stereo 3D apps zum Anzeigen der Treiber auch Stereo Scanout auf die Ausgabe unterstützen sollten.  Beispielsweise in einem System mit mehreren Adapter mit zwei WDDM 1.2 Grafikkarten Adapter herangezogen werden zum Erstellen einer Stereo *Fenstermodus* Swapchain, selbst wenn nur eine der Adapter tatsächlich Stereo Ausgabe unterstützt.

 

<a name="device.graphics.adapterrender.d3d111core"></a>
## <a name="devicegraphicsadapterrenderd3d111core"></a>Device.Graphics.AdapterRender.D3D111Core

*D3D 11.1 Hauptfeature*

### <a name="devicegraphicsadapterrenderd3d111cored3d111coreprimary"></a>Device.Graphics.AdapterRender.D3D111Core.D3D111CorePrimary

*Wenn ein Grafikgerät Direct3D 11.1 unterstützt, müssen sie den DXGI Spezifikationen und Direct3D 11.1 entsprechen.*

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

Ein Grafikgerät muss in der *Spezifikation Direct3D 11.1* definierten Anforderungen entsprechen und muss über ausreichende Leistung für Direct3D 11.1 Features bereitstellen.
 

Direct3D 11.1 ist eine Obermenge von Direct3D 11 (bei dem es sich um eine exakte Obermenge von Direct3D 10.1 und Direct3D 10 handelt); aus diesem Grund erfordert Implementierung Direct3D 11.1 auch vollständigen Unterstützung für die Features, die jeweils durch die Spezifikationen Direct3D 10, Direct3D 10.1 und Direct3D 11 definiert.

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber, einschließlich diese Features für die Kopfzeile DXGI DDI definiert verfügbar gemacht werden. 

<a name="device.graphics.adapterrender.d3d11astc"></a>
## <a name="devicegraphicsadapterrenderd3d11astc"></a>Device.Graphics.AdapterRender.D3D11ASTC

### <a name="devicegraphicsadapterrenderd3d11astccorerequirement"></a>Device.Graphics.AdapterRender.D3D11ASTC.CoreRequirement

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

D3D11-Treiber, die implementiert werden ASTC LDR-Unterstützung müssen Sampling von alle 2D ASTC Formate unterstützen. ASTC Formate sind nicht einzeln unterstützt und daher müssen alle Unterstützung für ASTC gezogen werden unterstützt. Hier wird eine Liste aller ASTC Formate, die Unterstützung für ASTC LDR unterstützen gültig sein müssen: (alle Formate aufweisen \_TYPELESS, und \_SRGB Entsprechung)

-   DXGI\_FORMAT\_4 X 4
-   DXGI\_FORMAT\_5 X 4
-   DXGI\_FORMAT\_5 X 5
-   DXGI\_FORMAT\_6 X 5
-   DXGI\_FORMAT\_6 X 6
-   DXGI\_FORMAT\_8 X 5
-   DXGI\_FORMAT\_8 X 6
-   DXGI\_FORMAT\_8 X 8
-   DXGI\_FORMAT\_10 X 5
-   DXGI\_FORMAT\_10 X 6
-   DXGI\_FORMAT\_10 X 8
-   DXGI\_FORMAT\_10 X 10
-   DXGI\_FORMAT\_12 X 10
-   DXGI\_FORMAT\_12 X 12

<a name="device.graphics.adapterrender.d3d11conservativerasterization"></a>
## <a name="devicegraphicsadapterrenderd3d11conservativerasterization"></a>Device.Graphics.AdapterRender.D3D11ConservativeRasterization

### <a name="devicegraphicsadapterrenderd3d11conservativerasterizationcorerequirement"></a>Device.Graphics.AdapterRender.D3D11ConservativeRasterization.CoreRequirement

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

Grafiktreiber für Direct3D 11 sollten DDIs im Zusammenhang mit der Rasterung vorsichtig, und Vergütung für Ebenen der Funktionalität implementieren:

 - Unsicherheit Bereich:
 - Innere Abdeckung
 - Nach dem Ausrichten fehlerhaften culling
 - Andere Interaktionen Pipeline:
   - TIR
   - MSAA
   - SampleMask mit inneren Abdeckung
   - Clip Abstand
   - Abfragen
   - oMask
   - HelperPixel Abdeckung
   - Attribut Interpolation (Extrapolation)
   - Frühe Z mit Tiefe Extrapolation

Weitere Informationen hierzu finden Sie in der Spezifikation vorsichtig Rasterung.

<a name="device.graphics.adapterrender.d3d11core"></a>
## <a name="devicegraphicsadapterrenderd3d11core"></a>Device.Graphics.AdapterRender.D3D11Core

*Hauptfeature D3D 11*

### <a name="devicegraphicsadapterrenderd3d11cored3d11coreprimary"></a>Device.Graphics.AdapterRender.D3D11Core.D3D11CorePrimary

*Wenn ein Grafikgerät Direct3D 11 implementiert wird, müssen sie den DXGI Spezifikationen und Direct3D 11 entsprechen.*

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

Wenn ein Grafikgerät Direct3D 11 implementiert wird, müssen in der *Spezifikation Direct3D 11* definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 11 Features ermöglichen.

Da Direct3D 11 eine Obermenge von Direct3D 10 ist, erfordert die Implementierung von Direct 3D 11 auch Unterstützung der Featuregruppe Direct3D 10.1 und nach der Erweiterung Direct3D 10. 

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber einschließlich diese Features für die Kopfzeile DXGI DDI definierten verfügbar gemacht werden.

<a name="device.graphics.adapterrender.d3d11doubleprecisionshader"></a>
## <a name="devicegraphicsadapterrenderd3d11doubleprecisionshader"></a>Device.Graphics.AdapterRender.D3D11DoublePrecisionShader

*Direct3D 11 Double Precision Shader Funktionalität*

### <a name="devicegraphicsadapterrenderd3d11doubleprecisionshaderd3d11corec"></a>Device.Graphics.AdapterRender.D3D11DoublePrecisionShader.D3D11CoreC

*Wenn Grafikhardware Direct3D 11 mit doppelter Genauigkeit implementiert wird, muss der Feature-Spezifikation entsprechen wie in der Spezifikation für D3D11 Hardware beschrieben.*

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

Die Spezifikation D3D11 ermöglicht optional doppelte Genauigkeit Shader Funktionalität auf Direct3D 11 Hardware implementieren.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D11 Hardware*entsprechen. 

<a name="device.graphics.adapterrender.d3d11drivercommandlists"></a>
## <a name="devicegraphicsadapterrenderd3d11drivercommandlists"></a>Device.Graphics.AdapterRender.D3D11DriverCommandLists

*Direct3D 11 Treiber Befehl Listen*

### <a name="devicegraphicsadapterrenderd3d11drivercommandlistsd3d11coreb"></a>Device.Graphics.AdapterRender.D3D11DriverCommandLists.D3D11CoreB

*Wenn die Grafikhardware die Liste Direct3D 11 Treiber Befehl implementiert wird, muss der Feature-Spezifikation gemäß Definition in der Spezifikation für D3D11 Hardware entsprechen.*

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

Die zulässige D3D11 für die Implementierung von DriverCommandListfunctionality optional auf Direct3D 11 Hardware. Wenn die Hardware außerdem Unterstützung zählen und der Treiber diese Funktionalität verfügbar macht, muss die Spezifikationen für dieses Feature gemäß Definition in der Spezifikation für D3D11 Hardware entsprechen.

<a name="device.graphics.adapterrender.d3d11driverconcurrentobjectcreation"></a>
## <a name="devicegraphicsadapterrenderd3d11driverconcurrentobjectcreation"></a>Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation

*Erstellung des Direct3D 11 Treiber gleichzeitige-Objekts*

### <a name="devicegraphicsadapterrenderd3d11driverconcurrentobjectcreationd3d11corea"></a>Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation.D3D11CoreA

*Wenn die Grafikhardware Direct3D 11 Treiber gleichzeitige Objekt Erstellung implementiert wird, muss der Feature-Spezifikation gemäß Definition in der Spezifikation für D3D11 Hardware entsprechen.*

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

Die zulässige D3D11 zum Implementieren der Funktion zum gleichzeitigen Driver-Objekt optional in Hardware Direct3D 11.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D11 Hardware*entsprechen. 

<a name="device.graphics.adapterrender.d3d11level9wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d11level9wddm12"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM12

*WDDM 1.2-Updates, UM DDI D3D9*

### <a name="devicegraphicsadapterrenderd3d11level9wddm12d3d9umddiupdate"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM12.D3D9UMDDIUpdate

*Wenn der Grafiktreiber Hardware die Spezifikation WDDM1.2 implementiert wird, muss die D3D9 Benutzer Modus DDI Ergänzungen gemäß der Spezifikation D3D11.1 API/DDI enthalten.*

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

Ein WDDM 1.2 Graphics-Treiber ist erforderlich, die gemäß Definition in der *Spezifikation D3D11.1 API/DDI* neben der DDI D3D9, durch den DirectX 9-Hardware und die Treiber Spezifikationen definierten D3D9 Adapter DDI und D3D9 DDI Ergänzungen zu implementieren.
 

<a name="device.graphics.adapterrender.d3d11level9wddm13"></a>
## <a name="devicegraphicsadapterrenderd3d11level9wddm13"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13

WDDM1.3-Updates, UM DDI D3D9

### <a name="devicegraphicsadapterrenderd3d11level9wddm13largecapturetextures"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.LargeCaptureTextures

*Direct3D große Capture Strukturen*

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

Alle 9 UMDs, unabhängig von der maximale Feature Ebene von Hardware zuzuordnen, müssen die Textur Größe Parameter an CreateResource2 übergeben wird jetzt ordnungsgemäß überprüfen.

Grafiktreiber müssen jetzt elegante (durch Zurückgeben einer E\_INVALIDARG) CAPTURE Textur erstellen Anforderungen, die die Funktionen der Hardware überschreiten.

Alle CAPTURE-Strukturen, die für die Erstellung genehmigt werden müssen Verhalten identisch mit Strukturen ERFASSEN, wie sie definiert sind.

### <a name="devicegraphicsadapterrenderd3d11level9wddm13level9instancing"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.Level9Instancing

*Ebene 9 Instancing*

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

In Windows wird das Betriebssystem Treffern zunehmende Verwendung von D3D Instancing an CPU/GPU zu verringern. Alle WDDM1.3 Treiber müssen Instancing unterstützen, gemäß dem Feature Ebene 9\_3.

### <a name="devicegraphicsadapterrenderd3d11level9wddm13nativestagingbuffers"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.NativeStagingBuffers

*Level9 systemeigene Staging Puffer Leistung Validierung*

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

Directx9 Ebene Grafikhardware, die WDDM1.3 implementieren muss die systemeigene Staging D3D9 Puffer DDI unterstützen.

### <a name="devicegraphicsadapterrenderd3d11level9wddm13nativeupdatesubresource"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.NativeUpdateSubresource

*Direct3D Level9 systemeigene UpdateSubresource*

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

Für Windows wird die Spezifikation Direct3D9 DDI systemeigene Unterstützung für die UpdateSubresource DDI berücksichtigen. Wenn D3D9-Ebene Teile dieser DDI implementieren, müssen die UpdateSubresource API-Aufrufe für eine bestimmte Menge an Arbeitsspeicher nicht langsamer als einen Kopiervorgang CPU ausgeführt werden.

### <a name="devicegraphicsadapterrenderd3d11level9wddm13timestampcountersupport"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.TimestampCounterSupport

*Direct3D Level9 Zeitstempel und Leistungsindikatoren*

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

Zeitstempel abfrageunterstützung wird für alle 9-Ebene 1.3 WDDM-Treiber, insbesondere diese Abfragetypen vorgeschrieben werden:

1.  D3DDDIQUERYTYPE\_ZEITSTEMPEL
2.  D3DDDIQUERYTYPE\_TIMESTAMPDISJOINT
3.  D3DDDIQUERYTYPE\_TIMESTAMPFREQ

Darüber hinaus muss die CheckDounter und CheckCounterInfo Direct3D11 Leistungsindikator DDIs unterstützt werden.

<a name="device.graphics.adapterrender.d3d11partialprecision"></a>
## <a name="devicegraphicsadapterrenderd3d11partialprecision"></a>Device.Graphics.AdapterRender.D3D11PartialPrecision

*Unterstützung für D3D11 teilweise Genauigkeit shader*

### <a name="devicegraphicsadapterrenderd3d11partialprecisiond3d11coree"></a>Device.Graphics.AdapterRender.D3D11PartialPrecision.D3D11CoreE

*Wenn die Grafik Hardware D3D11.1 teilweise Genauigkeit Shader Funktionalität implementiert wird, muss es in der Spezifikation für D3D11.1 Hardware gemäß der Feature-Spezifikation entsprechen.*

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

Die zulässige D3D11.1 zum Implementieren der Funktionalität teilweise Genauigkeit Shader optional in D3D9 D3D10\*, und Direct3D 11 Hardware mit einem WDDM 1.2 Treiber.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D11.1 Hardware*entsprechen.  


<a name="device.graphics.adapterrender.d3d11rasterizerorderedviews"></a>
## <a name="devicegraphicsadapterrenderd3d11rasterizerorderedviews"></a>Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews

### <a name="devicegraphicsadapterrenderd3d11rasterizerorderedviewscorerequirement"></a>Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews.CoreRequirement 

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

**Beschreibung**:

<a name="device.graphics.adapterrender.d3d11stencilreference"></a>
## <a name="devicegraphicsadapterrenderd3d11stencilreference"></a>Device.Graphics.AdapterRender.D3D11StencilReference

### <a name="devicegraphicsadapterrenderd3d11stencilreferencecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D11StencilReference.CoreRequirement (sofern implementiert)

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

Grafiktreiber für Direct3D11 sollte im Zusammenhang mit Pixel Shader Schablone Verweis DDIs implementieren:

 - Schreibt in PA\_STENCILREF-Funktion wie erwartet

Weitere Informationen finden Sie in der [PS-Specified Schablone Ref-Spezifikation](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/PS-Specified%20Stencil%20Reference%20Value%20-%20Unified%20Spec.docx?web=1).

<a name="device.graphics.adapterrender.d3d11typeduavloads"></a>
## <a name="devicegraphicsadapterrenderd3d11typeduavloads"></a>Device.Graphics.AdapterRender.D3D11TypedUAVLoads

### <a name="devicegraphicsadapterrenderd3d11typeduavloadcorerequirement"></a>Device.Graphics.AdapterRender.D3D11TypedUAVLoad.CoreRequirement

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

Grafiktreiber für Direct3D11 sollte im Zusammenhang mit eingegeben UAV Lasten DDIs implementieren:

-   Unterstützen Sie typisierte laden, sofern typisierte UAV Load-Flag festgelegt ist für alle erforderlichen UAV Formate

-   Unterstützung typisierte Last für optional deklarierte Typen

Weitere Informationen finden Sie in der [eingegebenen UAV Lasten spec](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/UAV%20Typed%20Load%20Draft%20Specification.docx?web=1)

<a name="device.graphics.adapterrender.d3d11wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm12"></a>Device.Graphics.AdapterRender.D3D11WDDM12

*Hauptfeature mit WDDM 1.2 Ergänzungen D3D 11*

### <a name="devicegraphicsadapterrenderd3d11wddm12d3d11v12primary"></a>Device.Graphics.AdapterRender.D3D11WDDM12.D3D11v12Primary

*Wenn ein WDDM 1.2 Grafikgerät Direct3D 11 implementiert wird, müssen sie das Direct3D 11, DXGI und des D3D10 Teils der Direct3D 11.1 Features Spezifikation entsprechen.*

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

Wenn ein Grafikgerät Direct3D 11 implementiert wird, müssen alle in der Spezifikation Direct3D 11 definierten Anforderungen entsprechen und muss eine ausreichende Leistung Direct3D 11 Features ermöglichen.

Da Direct3D 11 eine Obermenge von Direct3D 10 ist, erfordert die Implementierung von Direct 3D 11 auch der Featuregruppe Direct3D 10.1 und durch Erweiterung Direct3D 10 unterstützt. 

In Windows die folgenden Features, die ursprünglich in der Spezifikation D3D9 Hardware definiert sind jetzt auch erforderlich:

-   Hälfte Genauigkeit Pixelformate (5551, 565, 4444)
-   Dieselbe Oberfläche Blts

Finden Sie in der *Direct3D 11.1 Features Spec* vollständige Details alle neuen Features erforderlich, um mit einem WDDM 1.2 Treiber für D3D10 + Hardware verfügbar gemacht werden.

Alle diese Spezifikation erforderlichen Features müssen vom Gerätetreiber, einschließlich diese Features für die Kopfzeile DXGI DDI definiert verfügbar gemacht werden.

<a name="device.graphics.adapterrender.d3d11wddm12doubleprecisionshader"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm12doubleprecisionshader"></a>Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader

*Direct3D 11 doppelte Genauigkeit Shader Funktionalität durch zusätzliche Vorgängen Codes mit WDDM 1.2 eingeführt*

### <a name="devicegraphicsadapterrenderd3d11wddm12doubleprecisionshaderd3d11v12c"></a>Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader.D3D11v12C

*Wenn die Grafikhardware Direct3D 11-Funktionalität Shader doppelte Genauigkeit durch WDDM 1.2 Treiber Ergänzungen implementiert wird, muss das Feature Spezifikationen gemäß Definition in der Spezifikation für D3D11 Hardware entsprechen.*

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

Die Spezifikation D3D11 ermöglicht optional doppelte Genauigkeit Shader Funktionalität auf Direct3D 11 Hardware implementieren.   Wenn die Hardware Unterstützung für bietet der Treiber verfügbar, diese Funktionalität macht, muss die Spezifikationen für dieses Feature gemäß Definition in der *Spezifikation für D3D11 Hardware*entsprechen.   Für Windows Wenn Gerätetreiber WDDM 1.2 Grafiken doppelte Genauigkeit Shader-Funktionalität unterstützt ist es erforderlich, erweiterte mit doppelter Genauigkeit Math gemäß der *Shader Modell Verbesserungen Spezifikation*unterstützen.

<a name="device.graphics.adapterrender.d3d11wddm13"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm13"></a>Device.Graphics.AdapterRender.D3D11WDDM13

*Unterstützung von D3D11.1 nebeneinander Ressourcen*

### <a name="devicegraphicsadapterrenderd3d11wddm13mapdefault"></a>Device.Graphics.AdapterRender.D3D11WDDM13.MapDefault

*Ordnen Sie Standard*

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

Für Direct3D Feature Ebene 11\_0 und höher Teile müssen die WDDM1.3-Treiber STANDARDWERT Puffer zu erstellenden ermöglichen. Apps sind in der Lage, diese sämtliche Ressourcen anfordern, indem Sie die CPU\_Lese-/CPU\_Schreibzugriff Kennzeichen gemäß der Spezifikation WDDM1.3. Die STANDARDWERT Puffer sollte genau wie Verhalten auf vorhandene STANDARD-Puffer heute aus der Sicht API (sofern es sich nicht zugeordnet werden können). Die Zuordnung /-Zugriff auf die CPU-Leistung der STANDARDWERT Puffer sollte STAGING Puffer vergleichbar sein.

<a name="device.graphics.adapterrender.d3d11wddm20"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm20"></a>Device.Graphics.AdapterRender.D3D11WDDM20



### <a name="devicegraphicsadapterrenderd3d11wddm20corerequirement"></a>Device.Graphics.AdapterRender.D3D11WDDM20.CoreRequirement

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

<ol style="list-style-type: decimal">
<li><p><strong>Hohe Leistung Timing-Daten:</strong></p>
<p>Hinweis: Dieses Feature ist obligatorisch für einen 2.0 WDDM-Treiber D3D11 unterstützen.</p>
<p>"Hohe Leistung Timing Grafikdaten" werden Grafiken Arbeitslasten vorläufiger und sehr detaillierte Zeiterfassungsdaten bereit. Diese Daten wird durch Analysetools zum Identifizieren der Leistung oder andere Grafiken in der Windows-Anwendung, Probleme im Zusammenhang mit oder Grafiken Stapeln.</p>
<p>WDDM2.0-Treiber muss sicherstellen, dass der Grafiken Gerätetreiber stellt Folgendes bereit:</p>
<ul>
<li><p>Eine hohe Auflösung GPU-Zeitgeber</p></li>
<li><p>12,5 MHz (80ns Auflösung) oder höher.</p></li>
<li><p>Mindestens 32 Bit Timestamp-Lösung</p></li>
<li><p>Der Zeitstempel GPU kann für alle Module in einer GPU entnommen werden</p></li>
<li><p>Der Zeitstempel GPU kann am Ende der Pipeline GPU entnommen werden</p></li>
<li><p>Die Häufigkeit der GPU Timestamp kann geprüft werden.</p></li>
<li><p>Der Zeitstempel GPU unveränderlich ist und von p-Statusübergänge nicht betroffen ist.</p></li>
</ul>
<p>Zwischen den anderen Änderungen für dieses Feature wird dadurch das Hinzufügen von zwei neuen Flags in die vorhandene DdiControlEtwLogging-Schnittstelle enthalten. Wenn diese Flags so, dass die ersten Kennzeichen Wert 1 und das zweite Flag der Wert 0 ist festgelegt werden, muss der Treiber Folgendes sicherstellen:</p>
<ul>
<li><p>Alle Komponenten des Moduls müssen sicherstellen, dass sie nie Uhr oder Power abgegrenzten sind, solange das Flag aktiviert bleibt und im Allgemeinen sollten Sie nur muss in jeder Status, im Leerlauf eingeben. Die Komponenten müssen aktiv sein, um sicherzustellen, dass es keine Wartezeit aufgrund von Power Übergänge hinzugefügt.</p></li>
<li><p>Alle Komponenten des Moduls müssen sicherstellen, dass ihre Verarbeitung Frequenzen und funktionale Bus Bandbreiten an ihre maximale stabil Betrieb Werte sind. Zur Ereignisse erfordern P-Statusübergang unten sollten weiterhin statt, um Schaden an die Hardware zu vermeiden, jedoch P Staaten sollte definiert werden, damit diese außergewöhnliche Vorkommen werden, die in coole Lab Umgebungen normalerweise nicht sichtbar sind.</p></li>
<li><p>Der Stichprobe GPU Zeitstempel kann mit zuvor ausgegebenen Grafikbefehle korreliert werden</p></li>
<li><p>Generierung von Daten ist standardmäßig deaktiviert, aber Sie können ein- und ausschalten aktiviert werden, können Sie jederzeit.</p></li>
<li><p>Der Aufwand für das Erfassen von diesem Leistungsdaten ist nicht langsamer als die Verwendung der Zeitstempel Abfrage Technik, die bereits in D3D9 und D3D10 + verfügbar sind</p></li>
<li><p>Timing-Daten können in direkten Befehl Listen und fasst erfasst werden. Daten können aktiviert/für eine einzelne Liste pro Befehl deaktiviert werden.</p></li>
<li><p>Resultierenden Daten auf Grundlage Kachel zurückgestellt Rendering Hardware angezeigt wird, als wäre es auf einen sofortigen Aktualisierungsmodus Rendering-Gerät generiert wurde.</p></li>
</ul>
</li>
</ol>


<a name="device.graphics.adapterrender.d3d11wddm21"></a>
##Device.Graphics.AdapterRender.D3D11WDDM21

WDDM 2.1 ist eine optionale Versionsebene für Windows 10 eingeführt größer als 10586 basiert. Wenn ein Treiber WDDM 2.1 implementiert müssen sie alle der WDDM 2.1 Anforderungen implementieren. 2.0 WDDM-Treiber werden weiterhin auf die neuere Windows 10 Builds ausgeführt.

### <a name="devicegraphicsadapterrenderd3d11wddm21corerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D11WDDM21.CoreRequirement (sofern implementiert)

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

<ol>
<li><p>**Erweiterte NV12 / 420 Shared Textur-Unterstützung**</p>

<p>Hinweis: Dieses Feature ist obligatorisch für einen 2.1 WDDM-Treiber D3D11 unterstützen.</p>

<p>Die Freigabe von ein paar Textur Formate mit weitere Eigenschaften, um Szenarien für Frame-Server zu aktivieren, muss der Treiber unterstützen. Das Ziel ist 0 (null) Kopieren zwischen Aufnahme- und video Module.</p></li>

<li><p>**eFSE/UWP Optimierung-Unterstützung**</p>

<p>Hinweis: Dieses Feature ist obligatorisch für eine unterstützende D3D11 oder D3D9 2.1 WDDM-Treiber.</p>

<p>Der Treiber muss die neuen PfnAcquireResource/PfnReleaseResource-Methoden für die direkte Verwendung zum Aktivieren von Treiber Optimierungen für eFSE (emulierten vollständige Bildschirm ausschließlich) unterstützen / UWP (Universal Windows-Plattform) Leistung Parität mit FSE.</p></li>
</ol>

<a name="device.graphics.adapterrender.d3d12astc"></a>
##Device.Graphics.AdapterRender.D3D12ASTC

### <a name="devicegraphicsadapterrenderd3d12astccorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12ASTC.CoreRequirement (sofern implementiert)

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

Display-Treiber für Direct3D12 müssen alle Anforderungen mit ausreichend Leistung gemäß den Direct3D 12 Spezifikationen erfüllen.

D3D12 Treibern, die ASTC LDR Unterstützung implementieren müssen Sampling von alle 2D ASTC Formate unterstützen. ASTC Formate sind nicht einzeln unterstützt und daher müssen alle Unterstützung für ASTC gezogen werden unterstützt. Hier wird eine Liste aller ASTC Formate, die Unterstützung für ASTC LDR unterstützen gültig sein müssen: (alle Formate aufweisen \_TYPELESS, und \_SRGB Equilovants.)

 - DXGI\_FORMAT\_4 X 4
 - DXGI\_FORMAT\_5 X 4
 - DXGI\_FORMAT\_5 X 5
 - DXGI\_FORMAT\_6 X 5
 - DXGI\_FORMAT\_6 X 6
 - DXGI\_FORMAT\_8 X 5
 - DXGI\_FORMAT\_8 X 6
 - DXGI\_FORMAT\_8 X 8
 - DXGI\_FORMAT\_10 X 5
 - DXGI\_FORMAT\_10 X 6
 - DXGI\_FORMAT\_10 X 8
 - DXGI\_FORMAT\_10 X 10
 - DXGI\_FORMAT\_12 X 10
 - DXGI\_FORMAT\_12 X 12

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.adapterrender.d3d12conservativerasterization"></a>
## <a name="devicegraphicsadapterrenderd3d12conservativerasterization"></a>Device.Graphics.AdapterRender.D3D12ConservativeRasterization

### <a name="devicegraphicsadapterrenderd3d12conservativerasterizationcorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12ConservativeRasterization.CoreRequirement (sofern implementiert)

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

Grafiktreiber für Direct3D12 müssen im Zusammenhang mit der Rasterung vorsichtig, und Vergütung für Ebenen der Funktionalität DDIs implementieren:

 - Unsicherheit Bereich:
 - Innere Abdeckung
 - Nach dem Ausrichten fehlerhaften culling
 - Andere Interaktionen Pipeline:
 - TIR
 - MSAA
 - SampleMask mit inneren Abdeckung
 - Clip Abstand
 - Abfragen
 - oMask
 - HelperPixel Abdeckung
 - Attribut Interpolation (Extrapolation)
 - Frühe Z mit Tiefe Extrapolation

Weitere Informationen hierzu finden Sie in der [Rasterung vorsichtig Spec](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/Conservative%20Rasterization%20-%20Unified%20Spec.docx?web=1).

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.adapterrender.d3d12core"></a>
## <a name="devicegraphicsadapterrenderd3d12core"></a>Device.Graphics.AdapterRender.D3D12Core

*D3D 12 Core-Funktion*

### <a name="devicegraphicsadapterrenderd3d12corecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12Core.CoreRequirement (sofern implementiert)

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

Beschreibung:

<p>Treiber für Direct3D12 im definierten alle Anforderungen erfüllt sein müssen angezeigt werden die <strong><em>Direct3D 12 Spezifikationen</em></strong>.</p>

<ol style="list-style-type: decimal">
<li><p><strong>Benutzer-Heaps</strong></p>
<p>Die GPU muss lesen und Schreiben von Daten zu und von Seiten im Arbeitsspeicher. Wenn eine solche Seiten von der CPU zugegriffen werden kann, müssen sie als Zurückschreiben oder Write-Kombinieren der CPU gekennzeichnet werden sein.</p>
<p>Write-Combine Anforderungen effizient mit anderen Adapter und Module im System ausgeführt werden muss der Treiber berücksichtigt werden. Die anderen Seiteneigenschaften müssen vollständig orthogonal GPUs unterstützen.</p>
<p>Muss die GPU lesen und Schreiben von Pufferdaten eindimensionale &amp; Textur mehrdimensionale Daten zu und von dieser Seiten für alle GPU Vorgänge. Allerdings Einschränkungen und Verhalten vorhanden ist und in der Spezifikation erläutert wird.</p>
<p>Es ist zulässig, Ressourcen und Heaps während die GPU ist aktiv lesen oder Schreiben von solchen Seiten zugeordnet werden. Ausführliche Informationen über das Lesen von Schreibvorgängen GPU finden Sie die DDI-Spezifikation</p>

<blockquote>
<p>Der e/a-Kohärenz GPUs müssen verwenden, wenn Zurückschreiben erforderlich oder für Seiten, die sich im physischen Systemspeicher befinden ausgewählt ist.</p>

<p>Daten in der Regel im Zusammenhang mit Puffer und Datenvorgänge Tonlage linear Textur werden benötigt, um ordnungsgemäß für die Auslastung durch die GPU ausgerichtet werden. Puffer und Tonlage lineare Daten können neben miteinander und sogar Überlappung befinden.</p>
</blockquote>

<p>Zeichenbreite linear Anforderungen &amp; Einschränkungen lauten folgendermaßen:</p>

<ul>
<li><p>Nur ein einzelnes 3D Subresource ist zu einem Zeitpunkt erforderlich Tonlage linear / Zeile-Major kopieren.</p></li>
<li><p>Nur ein einzelnes 2D Subresource zu einem Zeitpunkt ist erforderlich, Schriftbreite linear / Zeile-Major Sampling Rendering.</p></li>
<li><p>Die Basisadresse / Offset Tonlage linear Textur Datengruppe muss 512 Byte ausgerichtet oder weniger.</p></li>
<li><p>Breite ein Schritt muss 128-Byte ausgerichtet, oder weniger für alle Größen von Texel--Element. Ein Schritt Breite ist 32-Bit- und kann wesentlich größer als die höchsten Schrittweite, die für einen bestimmten Texturbreite ordnungsgemäß ausgerichtet wird.</p></li>
<li><p>Beliebige Höhe, bis der maximale D3D wird orthogonal unterstützt.</p></li>
<li><p>Für Volume Strukturen ist ein Schritt Tiefe Höhe Mal Breite Schrittweite.</p></li>
<li><p>Komprimierte Renderingziele müssen möglicherweise zum Aktivieren der CPUS in Lese- / Schreibzugriff der Texel aufgelöst werden.</p></li>
</ul>
<p>Puffer Ausrichtung Einschränkungen werden nicht über D3D11 geändert:</p>
<ul>
<li><p>Konstante Daten Lesevorgänge muss ein Vielfaches von 256 Bytes vom Anfang des Heap (d. h. nur von Adressen, die 256 Byte ausgerichtet sind), oder weniger.</p></li>
<li><p>Index Daten Lesevorgänge muss ein Vielfaches von Typ der Indexgröße-Daten (d. h. nur aus Adressen, die für die Daten natürlich ausgerichtet sind), oder weniger.</p></li>
<li><p>Zeichnen Sie * indirekte Daten muss zwischen Offsets, die ein Vielfaches von 4 sind (d. h. nur von Adressen, die DWORD ausgerichtet sind), oder weniger.</p></li>
</ul>

<ul>
  <li>
    <p>Wenn die GPU standard Swizzle unterstützt, die GPU muss unterstützen alle mehrdimensionale Vorgänge orthogonal als andere Strukturen, wie Textur, zum Kopieren von auf Rendern &amp; von Re-Swizzle zu &amp; usw..</p>
    <ul>
        <li><p>Elementgröße für Dateiformate blockieren komprimiert und ASTC Formate muss die Blockgröße identisch sein.</p></li>
        <li><p>GPU muss aus allen Modulen, einschließlich Scan skalierten standard Swizzle unterstützen.</p></li>
        <li><p>Komprimierte Renderingziele müssen möglicherweise zum Aktivieren der CPUS in Lese- / Schreibzugriff der Texel aufgelöst werden.</p></li>
        <li><p>Standard Swizzle Daten müssen auf 4 KB und 64 KB Seitenränder ausgerichtet werden.</p></li>
    </ul>
  </li>
  <li>
    <p>Die GPU darf keine Textur Ausrichtung ist größer als 64 KB, mit Ausnahme von MSAA-Ressourcen mit Beispiel Count größer als 1 erfordern.</p>
  </li>
  <li>
    <p>Seite-basierte virtuelle Adressierung des physischen Arbeitsspeichers aus allen Modulen auf der GPU zu unterstützen.</p>
    <ul>
      <li>
        <p>Wenn die GPU GPU virtuelle Adressierung mit ordnungsgemäßen Sicherheitsgrenzen zum Zulassen der Änderung des Benutzer unterstützt, muss es aus alle Module aus, die die vollständige Vorteil unterstützt werden.</p>
      </li>
    </ul>
  </li>
</ul>
</li>

<li><p><strong>Resource-Bindung:</strong></p>
<p>Grafiktreiber für die Direct3D-API 12 müssen im Zusammenhang mit Deskriptoren und Deskriptor Heap-Objekts (wie folgt) DDIs und Vergütung für Ebenen der Funktionalität implementieren:</p>
<ul>
<li><p>Capability-Abfrage zum Binden von Ebenen Ressource</p></li>
<li><p>Deskriptor Heaps</p></li>
<li><p>Festlegen von Deskriptor Heaps</p></li>
<li><p>Erstellen von Deskriptoren</p></li>
<li><p>Kopieren von Deskriptoren</p></li>
<li><p>Erstellen eines Layouts der Stamm-Tabelle</p></li>
<li><p>Layout Tabelle Stamm festlegen</p></li>
<li><p>Festlegen von Deskriptor Tabellen für die Stammtabelle</p></li>
<li><p>Festlegen von Konstanten für die Stammtabelle</p></li>
<li><p>Festlegen von Deskriptoren für die Stammtabelle (Umgehung Deskriptor Heap/Tabellen)</p></li>
<li><p>Einstellung IA/VB/SO/RT/DS Deskriptoren zu einem Befehl auflisten / Verpacken</p></li>
<li><p>Zur Bearbeitung</p>
<p>Abschnitte von "Ebenen der Hardware-Unterstützung" und "DDI" in D3D12 Ressource Binding - funktionale Spec ausführliche Informationen finden Sie.</p></li>
</ul></li>

<li><p><strong>Hohe Leistung Timing-Daten:</strong></p>
<p>"Hohe Leistung Timing Grafikdaten" werden Grafiken Arbeitslasten vorläufiger und sehr detaillierte Zeiterfassungsdaten bereit. Diese Daten wird durch Analysetools zum Identifizieren der Leistung oder andere Grafiken in der Windows-Anwendung, Probleme im Zusammenhang mit oder Grafiken Stapeln.</p>

<ul>
<li><p>Ein WDDM1.3 Treiber muss sicher, dass der Grafiken Gerätetreiber Folgendes enthält:</p></li>
<li><p>Eine hohe Auflösung GPU-Zeitgeber</p></li>
<li><p>12,5 MHz (80ns Auflösung) oder höher.</p></li>
<li><p>Mindestens 32 Bit Timestamp-Lösung</p></li>
<li><p>Der Zeitstempel GPU kann für alle Module in einer GPU entnommen werden</p></li>
<li><p>Der Zeitstempel GPU kann am Ende der Pipeline GPU entnommen werden</p></li>
<li><p>Die Häufigkeit der GPU Timestamp kann geprüft werden.</p></li>
<li><p>Der Zeitstempel GPU unveränderlich ist und von p-Statusübergänge nicht betroffen ist.</p></li>
<li><p>Zwischen den anderen Änderungen für dieses Feature wird dadurch das Hinzufügen von zwei neuen Flags in die vorhandene DdiControlEtwLogging-Schnittstelle enthalten. Wenn diese Flags so, dass die ersten Kennzeichen Wert 1 und das zweite Flag der Wert 0 ist festgelegt werden, muss der Treiber Folgendes sicherstellen:</p></li>
<li><p>Alle Komponenten des Moduls müssen sicherstellen, dass sie nie Uhr oder Power abgegrenzten sind, solange das Flag aktiviert bleibt und im Allgemeinen sollten Sie nur muss in jeder Status, im Leerlauf eingeben. Die Komponenten müssen aktiv sein, um sicherzustellen, dass es keine Wartezeit aufgrund von Power Übergänge hinzugefügt.</p></li>
<li><p>Alle Komponenten des Moduls müssen sicherstellen, dass ihre Verarbeitung Frequenzen und funktionale Bus Bandbreiten an ihre maximale stabil Betrieb Werte sind. Zur Ereignisse erfordern P-Statusübergang unten sollten weiterhin statt, um Schaden an die Hardware zu vermeiden, jedoch P Staaten sollte definiert werden, damit diese außergewöhnliche Vorkommen werden, die in coole Lab Umgebungen normalerweise nicht sichtbar sind.</p></li>
<li><p>Der Stichprobe GPU Zeitstempel kann mit zuvor ausgegebenen Grafikbefehle korreliert werden</p></li>
<li><p>Ein D3D12 Treiber muss eine Anfang des Pipeline-Stempel neben ein Ende der Pipeline Timestamp sample können. Die Zeit auf den Anfang der Pipeline Timestamp muss aus die GPU nach Beginn der Ausführung eines Befehls korrelierte Grafiken auf Verarbeitungseinheiten, dass es verwendet, um den Befehl auszuführen.</p></li>
<li><p>Generierung von Daten ist standardmäßig deaktiviert, aber Sie können ein- und ausschalten aktiviert werden, können Sie jederzeit.</p></li>
<li><p>Der Mehraufwand für das Erfassen von diesem Leistungsdaten ist nicht langsamer als die Verwendung der Zeitstempel Abfrage Technik, die bereits in D3D9 und D3D10 + verfügbar ist</p></li>
<li><p>Timing-Daten können in direkten Befehl Listen und fasst erfasst werden. Timing-Daten können aktiviert/pro Liste pro Befehl deaktiviert werden.</p></li>
<li><p>Resultierenden Daten auf Grundlage Kachel zurückgestellt Rendering Hardware angezeigt wird, als wäre es auf einen sofortigen Aktualisierungsmodus Rendering-Gerät generiert wurde.</p></li>
</ul>
</li>

<li><p><strong>Zeitstempel Abfragen:</strong></p>
<ul>
<li><p>Eine einfache Zuordnung von D3D11 UAV Leistungsindikatoren, Stream-Ausgabe Leistungsindikatoren und Abfragen an den D3D12 API-Konstrukten muss Ergebnissen, die die relevanten D3D11 HLK-Tests.</p></li>
<li><p>D3D12-Treiber müssen die neue binäre verschiedenen Abfrage korrekt implementieren.</p></li>
<li><p>Seitenfehler GPU muss auftreten, wenn ein Shader einen nicht vorhandenen UAV Zähler zugreift.</p></li>
<li><p>Dynamische UAV Leistungsindikatoren Indizierung Shader muss ordnungsgemäß funktionieren.</p></li>
<li><p>Zeitstempel Abfragen müssen 3D arbeiten und Befehl Warteschlangen zu berechnen.</p></li>
<li><p>Predication muss für alle Renderingvorgänge (einschließlich denen, die in einem Paket) ordnungsgemäß funktionieren.</p></li>
<li><p>Stream-Ausgabe, UAV Leistungsindikatoren und Predication Puffer müssen alle D3D12 Heap Ressourcentypen ordnungsgemäß arbeiten.</p></li>
</ul>
</li>

<li><p><strong>Indirekte Rendering:</strong></p>
<ul>
<li><p>Ein D3D12-Treiber muss GPU Zeichnung/Versendung aus dem Puffer indirekte Agument implementieren.</p></li>
<li><p>Rendern mit einem Aribtrary indirekte Argument Puffer sollte dasselbe Ergebnis wie das entsprechende Satz von D3D12 Befehl Liste API-Aufrufe erstellen.</p></li>
<li><p>Indirekte Argument Puffer müssen in allen D3D12 Heap unterstützt werden.</p></li>
<li><p>Aribtrary Byte Fortschritte (die ein Vielfaches von 4) pro Draw-Strukturen müssen unterstützt werden.</p></li>
<li><p>Eine Liste von einzelnen Befehl die generiert eines Puffers indirekte Argument und nutzt muss ordnungsgemäß funktionieren (Treiber müssen ordnungsgemäß synchronisieren).</p></li>
<li><p>D3D12 Treiber müssen die GPU berechnet das untere Ende der MaxDrawCount an den Treiber übergeben Programm aus, und die DrawCount in einem Puffer indirekte Argument übergeben.</p></li>
</ul>
</li>

<li><p><strong>Pipeline Zustand Zwischenspeichern:</strong></p>

<ul>
<li><p>Ein D3D12 Treiber muss DDIs zum Abrufen von Hardware systemeigenen Shader Code für ein Objekt der Pipeline Zustand implementieren, und DDIs für rekonstruieren Pipeline Zustände aus diesem Cache Shader Code.</p></li>
<li><p>Muss zwischengespeichert werden, einschließlich Compute-Pipelines für jeden Pipeline Zustand, der an die API konstruiert werden kann.</p></li>
<li><p>Verwenden einen Pipeline Zustand aus zwischengespeicherten Shader Code erstellt muss identische Rendering im Vergleich zu einer, die von Bytecode HLSL kompiliert Ergebnissen.</p></li>
</ul>
</li>

</ol>


Unternehmensvorgabe:

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent.  Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.


<a name="device.graphics.adapterrender.d3d12multiadapter"></a>
## <a name="devicegraphicsadapterrenderd3d12multiadapter"></a>Device.Graphics.AdapterRender.D3D12Multiadapter

### <a name="devicegraphicsadapterrenderd3d12multiadaptercorerequirement"></a>Device.Graphics.AdapterRender.D3D12Multiadapter.CoreRequirement

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

**Beschreibung:**

Treiber für Direct3D12 mit ausreichend Leistung gemäß müssen alle Anforderungen erfüllen angezeigt den 

**Direct3D 12-Spezifikationen**.

Grafiktreiber D3D12, müssen gemäß den Direct3D-12-Spezifikationen gemeinsam genutzten Oberflächen Cross-Adapter unterstützen.

Wenn der Treiber auf Verknüpfte Grafikkarten ausgeführt wird, und klicken Sie dann die Direct3D 12 verknüpft ist Adapter Funktionalität erforderlich.

Hinweis: Dieses Feature ist obligatorisch nach einem Treiber zu D3D12-kompatibler Treiber sein.

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.adapterrender.d3d12rasterizerorderedviews"></a>
## <a name="devicegraphicsadapterrenderd3d12rasterizerorderedviews"></a>Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews

### <a name="devicegraphicsadapterrenderd3d12rasterizerorderedviewscorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews.CoreRequirement (sofern implementiert)

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

Display-Treiber für Direct3D12 müssen im Zusammenhang mit Raster Reihenfolge Ansichten DDIs implementieren:

 - Korrigieren Sie die Reihenfolge der Vorgänge für alle RasterizerOrdered\* Typen

Weitere Informationen hierzu finden Sie in der [ROV Spec](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/ROVs%20-%20Unified%20Spec.docx?web=1).

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.adapterrender.d3d12stencilreference"></a>
## <a name="devicegraphicsadapterrenderd3d12stencilreference"></a>Device.Graphics.AdapterRender.D3D12StencilReference

### <a name="devicegraphicsadapterrenderd3d12stencilreferencecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12StencilReference.CoreRequirement (sofern implementiert)

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

**Beschreibung**:

Grafiktreiber für Direct3D12 müssen im Zusammenhang mit Pixel Shader Schablone Verweis DDIs implementieren:

 - Schreibt in PA\_STENCILREF-Funktion wie erwartet

Weitere Informationen finden Sie in der [PS-Specified Schablone Ref-Spezifikation](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/PS-Specified%20Stencil%20Reference%20Value%20-%20Unified%20Spec.docx?web=1).

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.adapterrender.d3d12typeduavloads"></a>
## <a name="devicegraphicsadapterrenderd3d12typeduavloads"></a>Device.Graphics.AdapterRender.D3D12TypedUAVLoads

### <a name="devicegraphicsadapterrenderd3d12typeduavloadcorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12TypedUAVLoad.CoreRequirement (sofern implementiert)

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

Grafiktreiber für Direct3D12 müssen im Zusammenhang mit eingegeben UAV Lasten DDIs implementieren:

 - Unterstützen Sie typisierte laden, sofern typisierte UAV Load-Flag festgelegt ist für alle erforderlichen UAV Formate
 - Unterstützung typisierte Last für optional deklarierte Typen

Weitere Informationen finden Sie in der Spezifikation <a href="http://windowsteams/devx/GRFX/d3d/D3D Next Design/MQ Planning Documents/UAV Typed Load Draft Specification.docx?web=1">UAV Lasten eingegeben haben</a> .


**Unternehmensvorgabe**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent.  Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.


<a name="device.graphics.adapterrender.d312volumetiledresources"></a>
## <a name="devicegraphicsadapterrenderd312volumetiledresources"></a>Device.Graphics.AdapterRender.D312VolumeTiledResources

### <a name="devicegraphicsadapterrenderd3d12volumetiledresourcescorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12VolumeTiledResources.CoreRequirement (sofern implementiert)

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

**Beschreibung**:

Unterstützung für Volume nebeneinander Ressourcen (über das Verfügbarmachen nebeneinander Ressourcen Stufe 3) reporting Treiber müssen die Spezifikationen für dieses Feature in die D3D IHV Spezifikationen beschriebenen entsprechen. Ein Beispiel für eine interessante Spec Detailebene für Volume nebeneinander Ressourcen ist erforderlich Kachel Formen für verschiedenen Fläche Formate, wenn in einer Volume nebeneinander Ressource verwendet. Alle anderen Verhaltensweisen für dieses Feature fallen unter allgemeinen Spezifikationen für gekachelter Ressourcen im Allgemeinen sowie Volume Strukturen im Allgemeinen – wie dieses Feature die Schnittmenge der beiden ist.

**Unternehmensvorgabe:**

Alle Treiber für die Implementierung der D3D12 DDI müssen konsistent. Auf diese Weise können die D3D12-API haben ein konsistentes Verhalten auf vielen Plattformen ISVs der 3D Anwendungsentwicklung auf PC/Tablet/Telefon/XBOX Plattformen vermindert die Kosten.

<a name="device.graphics.indirectdisplay.wired"></a>
## <a name="devicegraphicsindirectdisplaywired"></a>Device.Graphics.IndirectDisplay.Wired

*Anzeigen der Feature-Anforderungen für verkabelten indirekte angezeigt.*

### <a name="devicegraphicsindirectdisplaywiredbase"></a>Device.Graphics.IndirectDisplay.Wired.Base

*Anforderungen für ein verkabeltes indirekte anzuzeigen.*

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

Eine indirekte Anzeige ist eine Anzeigegeräts (z. B. überwachen) Verbindung zu einem remote Gerät indirekte anzuzeigen, die das Bild aus einer Benutzer-Modus-Treiber nach Microsoft indirekte anzuzeigen Framework auf dem Absendersystem erhält, führt einige Verarbeitung und dann das Bild auf dem Bildschirm angezeigt.

Absender System benötigt die Vorschau CPU-Aktivität, um verarbeitet und auf das Gerät anzeigen indirekte übertragen werden. Diese Interaktion CPU möglicherweise direkte Bearbeitung des Bilds oder nur programming Hardware, die für das Abbild verarbeitet werden.

Einige Beispiele sind aber nicht beschränkt auf, universelle Dockingstation, USB-Anzeige Dongles und Monitore mit USB-Funktionen. 

**Allgemeine indirekte Anzeige DDIs**

Indirekte zeigt müssen alle erforderlichen DDI implementieren für indirekte Anzeigetreiber in das WDK aufgelistet.

**Anforderungen:**

**UMDF und DevFund Anforderungen:** Eine indirekte Grafikkartentreiber muss ein UMDF Treiber und muss alle Pertanent Gerät Fundemental Anforderungen entsprechen. Die folgenden DevFund Driver Framework UMDF Anforderungen müssen erfüllt, aber nicht beschränkt auf.

-   Device.DevFund.DriverFramework.UMDF

    -   Device.DevFund.DriverFramework.UMDF.Reliability

    -   Device.DevFund.DriverFramework.UMDF.WDFProperINF

**Grafiken Anforderung:** Indirekte Grafiktreiber müssen die Follow Grafiken Anforderungen entsprechen.

-   Device.Graphics.AdapterBase.PowerManagementCompliance - sollte dieser aus der USB-gefordertes stammen.

-   Device.Graphics.AdapterBase.Symbols

-   Device.Graphics.WDDM.Display.GammaCorrection – (optionale Anforderung)

-   Device.Graphics.WDDM.Display.I2CSupport – (optionale Anforderung)

-   Device.Graphics.WDDM.Display.Multimon

-   Device.Graphics.WDDM12.Display.ContainerIDSupport

-   Device.Graphics.WDDM12.Display.ModeEnumeration

-   Device.Graphics.WDDM.DisplayRender.OutputProtection

HDCP-Unterstützung ist optional, aber das Gerät OPM implementieren und ein entsprechendes OPM Zertifikat verfügen muss.

<a name="device.graphics.wddm"></a>
## <a name="devicegraphicswddm"></a>Device.Graphics.WDDM

*Die Basis-Featuregruppe durch Treiber unterstützt alle Versionen des WDDM implementiert.*

### <a name="devicegraphicswddmbase"></a>Device.Graphics.WDDM.Base

*Grafiktreiber müssen pro WDDM 1.0-Spezifikation implementiert werden.*

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

Wie der WDDM 1.0-Spezifikation müssen Grafiktreiber minimal D3D9 und Pixel Shader 2.0 unterstützen.

WDDM 1.0 bietet die folgenden wichtigen Anforderungen:

-   Grafikkartentreiber im Benutzermodus
-   Video-Speicher-Manager
  - (p1) Linear Speicher-Manager
  - (p1) Rechteckige Speicher-Manager
-   GPU Planer
-   Mode-Switch Architektur Bereinigung
-   Zusammengeführte Miniport und DLL
-   Wiederherstellung von Hardware hängt
-   Vereinfachte Kernelmodus-Objekte
-   Legacy DDI Konsolidierung
-   Hot-Plug-Grafikkarten, Betriebs Andocken und Unterstützung für "Klon anzeigen"

**MSDN-Dokumentationen wird basierend auf der WDDM 1.0-Spezifikation aktualisiert. Überprüfen Sie die MSDN-Dokumentation für WDDM 1.0 Anforderungen.**

### <a name="devicegraphicswddmchecklist"></a>Device.Graphics.WDDM.Checklist

*Alle Grafikgeräte müssen Basis Anforderungen Prüfliste für Grafikkarten, Chipsätze und Treiber entsprechen.*

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

Alle Grafikkarten müssen auf der folgenden Checkliste entsprechen: **Arbeitsspeicher Zuweisungen und Access** (gilt für alle Formularfaktoren)

-   Die GPU muss keine Zuweisung nach dem letzten DMA-Puffer zugreifen, die in die GPU, Zuweisung, wird als abgeschlossen gemeldet, die auf verweisen übermittelt wurde.

-   Die GPU muss nicht etwaigen zugegriffen werden, die in der Zuweisung-Liste zugeordnet ausgeführten DMA-Puffer nicht angegeben wurden.

**Karte/Chipsatzanforderungen** (gilt nicht für Server-Geräte)

-   Für eine mit mehreren Spitzen Grafikkarte empfiehlt es sich, dass der Anzeige Adapter machen alle Ressourcen über eine einzige Funktion und nicht als Multifunktionsgeräts angezeigt. Wenn eine sound-Controller oder Empfänger Teil des Geräts ist, kann das Gerät klicken Sie dann als Multifunktionsgeräts verfügbar gemacht werden.

<!-- -->

-   Wenn eine zweite Anzeige Klassenfunktion für Kompatibilität mit Vorversionen verfügbar gemacht wird, ist der Adapter muss bereits voll funktionsfähig sein ohne Verwendung der zweiten Leiter. Die zweite (oder eine zusätzliche) funktionale fasst muss:

<!-- -->

-   Haben Sie Unterklasse 80 (andere) um einen generischen verwendeten Treiber zu vermeiden.

-   Eine Erweiterung ROM keinen

-   Beschrieben Sie mehr als 1 MB insgesamt Speicherplatz Speicherressourcen nicht.

-   Die Ressourcen der Frame-Puffer nicht dupliziert.

-   Beschrieben Sie alle Ressourcen Interrupt nicht.

-   Beschrieben Sie alle e/a-Ressourcen nicht.

-   Funktionen der Basisklasse nicht anzeigen auf demselben Gerät, beispielsweise ein multimedia-Gerät-Klasse, Sub-Klasse Videogerät oder Sub-Klasse Audiogerät, unterliegen nicht diese Beschränkungen.

**WDDM-Treiber Prüfliste** (gilt nicht für nicht-WDDM-Treiber)

-   WDDM-Treiber müssen kein Zauns Übermittlung gemeldet werden als abgeschlossen, bis der Vorgang für die zugeordnete Einreichung tatsächlich abgeschlossen ist. Dies ist durch die Planung Objektmodell in WDDM erforderlich. Dass die Stabilität von Windows gefährdet ist muss das WDDM nicht die DDI in einer Weise verwenden.

-   WDDM-Treiber müssen ein paar Zauns-Interrupt für jede Zauns angefordert einfügen und dürfen nicht aus der Durchführung dieser Zauns reporting aufnehmen. Zauns muss gemeldet werden, sobald der zugehörige erforderliche Interrupt von der GPU generiert wird. Er muss beispielsweise nicht erst den Timer Interrupt oder bis der nächste VSync warten. Dies ist der DDM Details des Modells Planung erforderlich.

-   WDDM-Treiber müssen nicht warten oder blockieren während DdiSubmitCommand, der aus der Sicht von Video Planer WDDM erforderlich ist. Der Treiber muss nicht warten oder während eines Anrufs von DdiBuildPagingBuffer sowie blockieren.

-   WDDM-Treiber muss nicht mehr als einen Knoten pro physischen Engine verfügbar machen. Die Treiber und GPU kann nicht zwischen mehreren Knoten ein einzelnes physischen Modul planen.

-   WDDM-Treiber muss keine virtuelle Adresse Videospeicher zuordnen, die direkt zu einer Anwendung verfügbar gemacht wird. Dies ist unerlässlich für die Implementierung der Videospeicher Management Support in der WDDM-Treiber. WDDM-Treiber muss nicht ausblenden oder verfügbar machen Videospeicher in eine Möglichkeit, der der Videospeicher-Manager nicht bekannt ist.
    Ausnahmen sind spezifisch für die Implementierung der GPU Entwicklertools (Debugger, Profiler,...) zulässig.  Eine Ausnahme ausgelöst muss nur in einem Szenario gelten die GPU Developer-Tools zum Ausführen, auf dem virtuellen Adressraum für die Dauer der Sitzung und nur für den Prozess der Anwendung verwendeten Videospeicher zuordnen müssen.

-   WDDM-Treiber muss keine Segmente Arbeitsspeicher verfügbar machen, die für reporting zusätzliche Videospeicher als tatsächlich für die entsprechende Verwendung vorhanden ist der einzige Zweck verwendet werden. Die richtige Speichermenge, die für die Verwendung von verschiedenen Anwendungen über Windows mitzuteilen. WDDM-Treiber kann bis zu 5 % des Systemspeichers für die interne Verwendung wie Cursor Bitmaps, Ringpuffer usw. verwenden. Betrag über diese muss nicht verwendet werden, ausblenden oder machen Videospeicher in einer Weise verfügbar, sodass der Videospeicher-Manager nicht bekannt ist.

-   WDDM-Treiber muss für alle Interaktionen mit dem System-BIOS ACPI verwenden. SMI derzeit zulässig ist, aber es wird nicht von Microsoft dringend empfohlen. Finden Sie unter WinHEC 2005 Präsentation *TWAR05007.*

*Hinweise zum Entwurf*

Finden Sie für Weitere Informationen auf eines der Elemente im Abschnitt Details in der Windows-Treiberkits, und suchen Sie nach den entsprechenden Schlüsselwörtern.

### <a name="devicegraphicswddmgpufencecommands"></a>Device.Graphics.WDDM.GPUFenceCommands

*Eine GPU, das für die Verarbeitung von Befehlen in der Warteschlange Befehl Zauns kann muss einen Interrupt auf die CPU ausgelöst werden, wenn sie einen Befehl Zauns werden genutzt.*

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

Wenn die Hardware ein Zauns Befehls werden genutzt, müssen sie das Betriebssystem benachrichtigt werden, indem auslösen Interrupt auf die CPU, mit der der ISR. mitgeteilt Zauns-ID

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits

<a name="device.graphics.wddm.display"></a>
## <a name="devicegraphicswddmdisplay"></a>Device.Graphics.WDDM.Display

*Die Basis-Featuregruppe durch Treiber unterstützt alle Versionen von der WDDM Anzeige DDIs implementiert.*

### <a name="devicegraphicswddmdisplaybase"></a>Device.Graphics.WDDM.Display.Base

*Grafiktreiber müssen gemäß der Spezifikation WDDM 1.0 implementiert werden.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM.Base**
 

### <a name="devicegraphicswddmdisplaygammacorrection"></a>Device.Graphics.WDDM.Display.GammaCorrection

*Eine Grafikkarte muss Gamma-Korrektur Hardware unterstützen, ohne zusätzliche Grafiken Arbeitsspeicherbandbreite.*

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

ICM verwendet die Möglichkeit zum Ausführen von Gamma-Korrektur für die angeschlossenen Monitor und Spiel, Farbpaletten wechseln zu ermöglichen. Diese Funktion unterstützt auch Übergangseffekte in Applications. Zur Unterstützung der ICM, die Grafikkarte oder Chipsatz muss Gamma programmgesteuert veränderbaren sein.

Zum Ausführen von Gamma-Korrektur in Hardware müssen herunterladbare RAM DAC-Einträge (LUT) eingeschlossen werden.

Die LUT muss mindestens 256 Einträge pro Komponente Eingabe für 8-Bit-Farben Channel Komponenten implementieren. Hardware kann die LUT für größere Komponente Lösungen implementieren, mithilfe von Interpolation, wenn mindestens 128 Punkten verwendet werden.

Diese Fähigkeit muss unterstützt werden, ohne die Verwendung von Grafiken Arbeitsspeicherbandbreite. Diese Fähigkeit muss für RGBA8888 und RGBA1010102 Pixel unterstützt werden Formate.
 

### <a name="devicegraphicswddmdisplayhotplugdetection"></a>Device.Graphics.WDDM.Display.HotPlugDetection

*Eine Grafikkarte muss zuverlässig erkennen das Verbindung herstellen und disconnect-Ereignis von Anzeigegeräten.*

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

Windows unterstützt zwei Stufen von Anzeige Erkennung - gestört werden und Umfrage können.

-   Gestört werden wird die Groß-/Kleinschreibung definiert, in dem die Grafikkarte berechtigt ist, automatisch erkennen eine Änderung in Anzeige Konnektivität, und wenden Sie sich an Windows. Die Möglichkeit der Hardware, automatisch generieren Interrupt für die Änderung der Anzeigeoptionen Connectivity heißt Hot Plug & Play erkennen (HPD). Die HPD muss keine visual auf einer Anzeige bereits mit dem System verbundenen beschädigt werden.

-   Umfrage können wird die Groß-/Kleinschreibung definiert, in dem Windows hat, den Grafikadapter für die Abfrage für eine Änderung in der Anzeige Connectivity explizit Abfragen. In einigen Fällen kann visual Beschädigung für eine kurze Zeit angezeigt werden.

  
Alle standard digitale Connectors (DisplayPort, HDMI, DVI) unterstützen HPD, und die Grafikkarte muss diese Connectors als Arbeitsgruppenmitgliedern melden. Nachdem die Hardware den Interrupt generiert, teilt die Grafikkarte Windows über die DxgkCbIndicateChildStatus DDI finden Sie hier: <http://msdn.microsoft.com/en-us/library/ff559522.aspx>.

Analoge Connectors (HD-15, S-Video, Component, zusammengesetzte) zur Unterstützung von Arbeitsgruppenmitgliedern Anzeige Erkennung nicht erforderlich sind. Es ist jedoch möglich, dass in der Hardware HPD implementiert werden kann (z. B. Erkennung I2C laden) für solche Connectors. In diesem Fall muss die Grafikkarte dieser Connector wie Arbeitsgruppenmitgliedern als oben melden. Software Abruf kann nicht verwendet werden, HPD Funktionalität für analoge Connectors erzielt.

Für diese analoge Connectors, wobei HPD nicht in die Hardware implementiert wird, muss die Grafikkarte wie, die abgerufen werden den Connector melden. In diesem Fall die Grafikkarte muss nur ausführen Erkennung für den Connector explizite Anforderung von Windows über die D3DKMTPollDisplayChildren DDI, finden Sie hier: <http://msdn.microsoft.com/en-us/library/ff547077.aspx>.

*Hinweise zum Entwurf*

Finden Sie unter Windows-Treiberkits: <http://msdn.microsoft.com/en-us/library/ff559522.aspx> für "DxgkCbIndicateChildStatus."

Die folgenden HPD Methoden sind VESA Standards: DVI HPD fällt im VESA Plug & Play (Plug & Play-) Standard für die Anzeige/Grafiken Subsystem, Version a DisplayPort HPD wird in allen Versionen des DisplayPort Standards behandelt.

### <a name="devicegraphicswddmdisplayi2csupport"></a>Device.Graphics.WDDM.Display.I2CSupport

*Ein Gerät Grafiktreiber benötigen I2C-Unterstützung in WDDM.*

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

Dies ist der Satz von Schnittstellen, die jeder WDDM-Treiber für I2C Unterstützung implementieren erforderlich ist:

 - DxgkDdiI2CReceiveDataFromDisplay
 - DxgkDdiI2CTransmitDataToDisplay

Diese Schnittstellen sind in der WDK dokumentiert und finden Sie hier: <http://msdn.microsoft.com/en-us/library/ff567386.aspx>.


### <a name="devicegraphicswddmdisplaymultimon"></a>Device.Graphics.WDDM.Display.Multimon

*Wenn eine Grafikkarte mehr als 1 Quell- und 1 unterstützt, muss alle Konfigurationen für mehrere Monitore in Windows unterstützt werden.*

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

Graphics-Treiber kann Quellen und Ziele basierend auf seine Funktionen aufgelistet werden. Windows fragt den Treiber für die Anzahl der Quellen und Ziele durch einen Aufruf der DxgkDdiEnumVidPnCofuncModality DDI, finden Sie hier <http://msdn.microsoft.com/en-us/library/ff559649.aspx>. Windows unterstützt die folgenden Monitorkonfigurationen:

-   Konfiguration der einzelnen Monitor - nur eine physische Monitor aktiv ist und der gesamte Desktop auf es angezeigt wird.

-   Monitor erweiterte Konfiguration – mehrere Bildschirme in aktiv sind und verschiedene Teile des Desktops darauf angezeigt werden. GDI muss der Monitor Grenzen hingewiesen werden, dass Windows-Features wie maximieren, aero Snap usw. gemäß der Spezifikation arbeiten.

-   Doppelte Monitor-Konfiguration - genauen denselben Desktop, den Inhalt auf mehreren Monitoren angezeigt werden.

Die Anzahl der Ziele muss immer größer als oder gleich der Anzahl der Quellen.

Wenn der Treiber genau 1 Quell- und 1 zählt, werden keine mehrere Monitorkonfigurationen unterstützt.

Wenn der Treiber genau 1 Quell- und mehrere Ziele aufgezählt, muss der Treiber einzelnen Monitor und doppelte Monitorkonfigurationen unterstützen.

Wenn mehrere Quellen und mehrere Ziele der Treiber aufgezählt hat, muss der Treiber alle unterstützten Konfigurationen unterstützen. Darüber hinaus gilt:

-   Die Möglichkeit, jede Quelle bei Aktivierung von Itsself, im Hinblick auf die Lösung, Direct 3D, geschützten Inhalts Wiedergabe, sollten identisch sein. Die Funktionen des Ziels variiert basierend auf dem Zieltyp.

-   Das Betriebssystem muss jeder Ziel aus keinem Quellcode Laufwerk können zwar die Einschränkung des Treibers welche Ziele in Kombination gesteuert werden können.

Unterstützung für mehrere Monitore ist in Windows integriert. aus diesem Grund müssen Grafiktreiber nicht bereits in das Betriebssystem verfügbaren unterstützen keinen bestimmten Code enthalten.

Es muss ein Benutzer durch Drücken der Win + P Tastenkombination und alle Konfigurationen unterstützt mithilfe der Systemsteuerung Windows Display festgelegt sein.

<a name="device.graphics.wddm.displayrender"></a>
## <a name="devicegraphicswddmdisplayrender"></a>Device.Graphics.WDDM.DisplayRender

*Die Basis Featuregruppe von Treibern, die Unterstützung für alle Versionen des WDDM für Anzeige und Rendern DDIs implementiert.*

### <a name="devicegraphicswddmdisplayrenderbase"></a>Device.Graphics.WDDM.DisplayRender.Base

*Grafiktreiber müssen gemäß der Spezifikation WDDM 1.0 implementiert werden.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM.Base**

### <a name="devicegraphicswddmdisplayrenderdriversetupcompatible"></a>Device.Graphics.WDDM.DisplayRender.DriverSetupCompatible

*Grafiktreiber müssen gemäß der Spezifikation WDDM 1.0 implementiert werden.*

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

Alle WDDM Graphics-Treiber, die für die Bereitstellung der Windows-Update für Windows-Client-SKUs übermittelt ordnungsgemäß auf Einfügung in den Windows-Betriebssystem Bild Treiber installieren muss während des Setups OS speichern.

### <a name="devicegraphicswddmdisplayrenderoutputprotection"></a>Device.Graphics.WDDM.DisplayRender.OutputProtection

*Eine Grafikkarte muss Ausgabe Connectors mit Schutz von Inhalten Features unterstützen und bietet Kontrolle über geschützte Medienpfad Ausgabe Protection Manager (PVP OPM) und Certified Ausgabe Protection-Protokoll (COPP).*

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

Um die Wiedergabe von Videoinhalten Premium zu aktivieren, müssen digitale video Ausgaben einer digitalen Monitor Link Schutzmechanismen wie HDCP zum Abrufen von Windows 8-Client-Logo unterstützen. Dies gilt für alle vollständige Grafikgeräte zur Verfügung.

OPM API und Media Foundation PMP erfordern Grafiktreiber ordnungsgemäß implementieren der OPM DDIs um Premium-Inhalte zu behandeln. Hohe Qualität Premiuminhalt wird nicht an Grafikkartentreiber übergeben werden, es sei denn, der Grafiktreiber ein PVP OPM Zertifikat verfügt. Treiber, die OPM DDIs unterstützen, benötigen ein Zertifikat Treiber bezeugen, die Compliance-Regeln, Stabilität Regeln und PVP OPM rechtlichen zustimmen, erfüllt sind.
Grafikkartentreiber muss sowohl die COPP unterstützen\* und PVP OPM Treiber Schnittstellen für die Steuerung und Signale video Ausgabe Protection Zustand.

Ausgabe Protection Verhaltensweisen werden durch die Kompatibilitätsregeln PVP OPM festgelegt.  Das Dokument ist für Grafiken Lieferanten durch Anforderung an wmla@microsoft.com verfügbar.

WDDM-Treiber muss die erforderlichen Anzeige Modus Management DDIs implementieren und Strukturen, wie in der Windows-Treiberkits und in der Dokumentation WDDM zum Aktivieren von TV-Wiedergabe und Analog Content Protection (ACP) erläutert die Unterstützung für Media Center\*.

D3DKMDT\_VIDPN\_VORHANDEN\_PFAD\_CONTENT: Media Center werden diese Informationen verwenden, um den TV-Modus ändern (TV\_WIEDERGABE im Vergleich zu WIN\_GRAFIKEN)

D3DKMDT\_VIDPN\_VORHANDEN\_PFAD\_COPYPROTECTION\_TYP und D3DKMDT\_VIDPN\_VORHANDEN\_PFAD\_COPYPROTECTION\_UNTERSTÜTZEN: Diese Strukturen sind erforderlich, um über den Treiber LDDM ACP unterstützen.

S-Video- und zusammengesetzte video Ausgabe Schnittstellen müssen die folgenden Funktionen:

 - CGMS-A auf Zeile 20 gemäß IEC 61880
 - CGMS-A auf Zeile 21 gemäß EIA-608-B

Component (YPbPr) Ausgaben müssen folgende Funktionen werden unterstützt:

 - CGMS-A mit Redistribution Steuerelement gemäß EIA 805

Wenn TV Out-Schnittstelle aktiviert ist, muss der Grafiktreiber 720 x 480 60 Hz Anzeigemodus und/oder einen Anzeigemodus von 720 x 576 50 Hz verfügbar machen. Diese Anzeige Modi von der video-Miniport verfügbar gemacht werden und die Standardliste der Anzeigedauer für Windows-Anwendung fest, wenn ein standard Definition TV verbunden hinzugefügt werden müssen.

SDTV Modi unterstützt:<br/>
WDDM-Miniporttreiber muss dieser Parameter für die Ausgabe video SDTV Modi wie NTSC, PAL oder SECAM verfügbar machen auf TRUE festzulegen.

Cable Ready Systeme mit CableCARD Unterstützung mit digitalen video Ausgaben (beispielsweise HDMI oder DP) müssen eine CableLabs genehmigt digitaler Monitor Link Schutzmechanismen wie HDCP unterstützen.

 
*Hinweise zum Entwurf*

-   S-Video- und zusammengesetzte video Ausgabe Schnittstellen können über den gleichen Connector implementiert werden. Wenn eine proprietäre Schnittstelle verwendet wird, muss ein Adapter zur Verfügung gestellt werden mit dem System oder zu erwerben ist beim Kauf eingeschlossen. Ein System oder Gerät mit S-Video-Connectors 7-Pin ist nicht erforderlich, um einen Adapter bereitstellen, solange die ersten vier Pins für den Connector 7-Pin durch eine standard-Pin 4 S-Video-Verbindung elektrisch kompatibel sind. Microsoft empfiehlt, einschließlich SCART Ausgabe, wenn für den Bereich des Verkauf geeignet.

-   \*COPP ACP, CGMS-A, analoge TV-Ausgang und SDTV unterstützen sind auf X86 und X64 Architekturen und nur Betriebssysteme erforderlich.

### <a name="devicegraphicswddmdisplayrenderstability"></a>Device.Graphics.WDDM.DisplayRender.Stability

*Alle WDDM Graphics-Treiber müssen keine hängt oder Seitenfehler längerer Belastung generieren.*

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

Grafiktreiber ordnungsgemäß funktioniert, und nicht generiert werden alle hängt oder Fehler im Verlauf des Belastungstests gemäß dem Profil"WDDM 4 Stunden".

Um "belasten Graphics-Treiber", Marktanteilen Zuverlässigkeit Analyzer für Software und Hardware (ABSTURZ) startet und andere testanwendungen können Sie das reale Szenarios beendet.

<a name="device.graphics.wddm.render"></a>
## <a name="devicegraphicswddmrender"></a>Device.Graphics.WDDM.Render

*Die Basis-Featuregruppe durch Treiber unterstützt alle Versionen von der WDDM Rendern DDIs implementiert.*

### <a name="devicegraphicswddmrenderbase"></a>Device.Graphics.WDDM.Render.Base

*Grafiktreiber müssen gemäß der Spezifikation WDDM 1.0 implementiert werden.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM.Base**

### <a name="devicegraphicswddmrendervideodecoding"></a>Device.Graphics.WDDM.Render.VideoDecoding

*Grafiktreiber müssen die DirectX VA 2.0 Video Decoder DDI unterstützen.*

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

Anzeige WDDM-Treiber müssen folgende DXVA 2.0 Video Decoder DDI unterstützen.

WDDM-Treiber müssen die folgenden Modi DXVA unterstützen:

-   DXVA\_ModeH264\_VLD

-   DXVA2\_ModeVC1\_D ODER DXVADDI\_ModeVC1\_D2010

Wenn Hardware Acceleration für MPEG2 unterstützt, unterstützen WDDM-Treiber mindestens eine der folgenden Ressourcengruppen MPEG2 GUIDs:

-   DXVA2\_ModeMPEG2\_VLD und DXVA2\_ModeMPEG2\_iDCT

-   DXVA2\_ModeMPEG2\_VLD und DXVA2\_ModeMPEG2\_MoComp

-   DXVA2\_ModeMPEG2\_iDCT

-   DXVA2\_ModeMPEG2and1\_VLD

Wenn Hardware Acceleration für H.265 unterstützt, müssen sie HEVC/H.265 Modi unterstützen:

-   D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN

-   D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN10 (optional, wenn Hardware Main10 Profil nicht unterstützt)

Es wird empfohlen für Treiber zur Unterstützung von D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN10, als 10 Main ist sehr häufiges Format für Premium HEVC Inhalt.

Wenn Hardware Acceleration für VPx unterstützt, müssen sie VPx Modi unterstützen:

-   D3D11\_DECODER\_PROFIL\_VP8\_VLD

-   D3D11\_DECODER\_PROFIL\_VP9\_VLD\_PROFILE0

-   D3D11\_DECODER\_PROFIL\_VP9\_VLD\_PROFILE2 (optional, wenn Hardware Profil 2 nicht unterstützt)

WDDM-Treiber müssen DXGI unterstützen\_FORMAT\_420\_nicht TRANSPARENT, und DXGI\_FORMAT\_NV12 als Decoder Ausgabeformate. NV12 wird für Szenarios, in denen Shader Interop empfohlen. HEVC Main 10 müssen Treiber DXGI unterstützen\_FORMAT\_P010 als Decoder Ausgabeformat.

Wenn der Anzeige Adapter unterstützt hardwarebeschleunigte der h. 264 decodieren, müssen sie entweder die DXVA unterstützen\_ModeH264\_MoComp GUID oder den DXVA\_ModeH264\_VLD GUID.

Wenn die Anzeige Adapter Support hardwarebeschleunigte des HEVC Decodierung, muss er die DXVA unterstützen\_ModeHEVC\_VLD\_Main-GUID.

Schließlich müssen WDDM-Treiber unterstützt standardisiert AES 128 h. 264\* \* \* und MPEG2, wenn MPEGE2 Acceleration unterstützt wird.

*Hinweise zum Entwurf*

\*\*\*Unterstützung von standardisierten AES-128 ist auf X86 und X64 Architekturen und nur Betriebssysteme erforderlich.

### <a name="devicegraphicswddmrendervideoprocessing-if-implemented"></a>Device.Graphics.WDDM.Render.VideoProcessing (sofern implementiert)

*Anzeige WDDM-Treiber muss DirectX VA 2.0 Video-Prozessor-DDI unterstützen.*

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

Wenn implementiert, müssen Anzeige WDDM-Treiber unterstützt die DXVA 2.0 Video Prozessor DDI und implementieren die Unterstützung für die folgenden Video Prozessor Gerät GUIDs:

-   DXVADDI\_VideoProcProgressiveDevice
-   DXVADDI\_VideoProcBobDevice

Die folgenden DXVA2 video Prozessor Caps müssen für jede des Geräts video Prozessor GUIDs unterstützt werden:

-   DXVADDI\_VIDEOPROCESS\_YUV2RGB
-   DXVADDI\_VIDEOPROCESS\_YUV2RGBEXTENDED
-   DXVADDI\_VIDEOPROCESS\_STRETCHX
-   DXVADDI\_VIDEOPROCESS\_STRETCHY
-   DXVADDI\_VIDEOPROCESS\_SUBRECTS
-   DXVADDI\_VIDEOPROCESS\_untergeordneter DATENSTRÖME
-   DXVA2\_VideoProcess\_SubStreamsExtended
-   DXVA2\_VideoProcess\_Constriction

Darüber hinaus zur Unterstützung von DXVADDI\_VIDEOPROCESS\_YUV2RGBEXTENDED Caps, die folgenden Farbe-Parameter muss unterstützt, wenn Farbe Leerzeichen konvertieren von einer YUV Fläche in einem RGB-Oberfläche:

-   D3DDDIARG\_VIDEOPROCESSBLT. DestFormat.NominalRange

    -   DXVADDI\_NominalRange\_unbekannt (interpretiert werden soll, als 0\_255, wenn es sich bei ein komplexen Algorithmus nicht implementiert ist)
    
    -   DXVADDI\_NominalRange\_0\_255
    
    -   DXVADDI\_NominalRange\_16\_235

-   D3DDDIARG\_VIDEOPROCESSBLT.pSrcSurfaces\[\]. SampleFormat.VideoTransferMatrix

    -   DXVADDI\_VideoTransferMatrix\_unbekannt (interpretiert werden soll wie BT601, sofern die Quelloberfläche größer als 576 Höhe in diesem Fall wird als BT709 interpretiert werden soll)

    -   DXVADDI\_VideoTransferMatrix\_BT709

    -   DXVADDI\_VideoTransferMatrix\_BT601

Die folgenden Formate YUV müssen als den Videostream unterstützt werden:

-   YUY2 - 8-Bit-gepackt 4:2:2
-   NV12 - 8-Bit-Ebene 4:2:0

Wenn der video Prozessor ein 10-Bit-YUV subsampling unterstützt, muss das folgende Format für die entsprechende unterstützt werden:

-   Y210 - 10-Bit-gepackt 4:2:2
-   Y410 - 10-Bit-gepackt 4:4:4
-   P210 - 10-Bit-Ebene 4:2:2
-   P010 - 10-Bit-Ebene 4:2:0

Wenn der video Prozessor 16-Bit-YUV Formate unterstützt, müssen die folgenden Formate unterstützt:

-   Y216 - 16-Bit-gepackt 4:2:2
-   Y416 - 16-Bit-gepackt 4:4:4
-   P216 - 16-Bit-Ebene 4:2:2
-   P016 - 16-Bit-Ebene 4:2:0

Im folgende Format YUV muss als die untergeordneten Videostreams unterstützt werden:

-   AYUV - 8-Bit-gepackt 4:4:4

Für diese Formate muss Farbe konvertieren YUV-RGB-Blits führen Sie über die Funktion VideoProcessBlt mindestens BT. verwenden können 601 und BT. 709 Konvertierung Übersichten unterstützt wird. Dieser Prozess ermöglicht es, die Grafiken so wechseln Sie zwischen den YUV-RGB-Matrix-Transformationen für andere Farbenformate, um die korrekte Handhabung von Video zu gewährleisten, die andere Standardfarbe Leerzeichen wie in ITU-R Recommendations BT. stammt 601 und BT.709, ist erforderlich.

Schwellenwert für die Fehlertoleranz: 50dB Qualität Unterschiede zwischen Referenz und DXVAHD-Modi

-   Unterstützung der folgenden für Wiedergabe, Codierung und Capture Szenarien der Konvertierung Farbe:

    -   NV12 -&gt;ARGB32
    -   YUY2 -&gt;ARGB32
    -   ARGB32 -&gt;NV12 (vollständig Einsatz und Studio Einsatz)
    -   420O -&gt;NV12
    -   420O -&gt;ARGB32
    -   AYUV -&gt;NV12

-   Unterstützung für die oben genannten Konvertierungen Skalierung

-   Rotation-Unterstützung

-   Erweiterte Bereich (vollständig Einsatz) Unterstützung für Codierung und Erfassung Szenarien

Unterstützung für aktualisierte für DX9 und DX10 + Benutzermodus DDIs wie auf Verbindung mit dokumentiert: <https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=47236>.

<a name="device.graphics.wddm11"></a>
## <a name="devicegraphicswddm11"></a>Device.Graphics.WDDM11

*Die Basis-Featuregruppe durch Treiber unterstützt WDDM 1.1 implementiert.*

### <a name="devicegraphicswddm11base"></a>Device.Graphics.WDDM11.Base

*Ein Graphic-Treiber, der für eine einzelne Grafik Adapter oder ein integrierter Grafikkarte Adapter Gerät geschrieben wird, muss die Anforderungen, die in den Spezifikationen WDDM 1.1 definierten erfüllen.*

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

WDDM 1.1 werden die folgenden wichtigen Anforderungen über WDDM 1.0 eingeführt:

-   Hardware-Beschleunigung GDI-Funktionen auswählen.

-   Implementierung von DMM DDIs für das Verbinden und Konfigurieren von zeigt

-   Unterstützung für 32-Bit-BGRA Pixelformat mit GDI kompatibel. (Über DirectX10 und höher DDIs.)

-   Enthalten Sie weitere Informationen zur Unterstützung bei der VSync TDRs Debuggen.

-   Kernelmodus-Treiber müssen mit Frame Zeiger Optimierungen (FPO) deaktiviert kompiliert werden.

-   Optionale Features müssen entsprechend die Spezifikationen und WDK-Dokumentation, einschließlich AES128 standardisiert, DXVA HD, Überlagerungen und Direct3D11 Wenn implementiert, aufgenommen werden.

**MSDN-Dokumentationen wird basierend auf der WDDM 1.1-Spezifikation aktualisiert. WDDM 1.1 Anforderungen finden Sie in MSDN-Dokumentation.**

<a name="device.graphics.wddm11.display"></a>
## <a name="devicegraphicswddm11display"></a>Device.Graphics.WDDM11.Display

*Die Basis Featuregruppe durch Treiber unterstützt alle Versionen von der WDDM Anzeige DDIs implementiert.*

### <a name="devicegraphicswddm11displaybase"></a>Device.Graphics.WDDM11.Display.Base

*Eine Grafik Treibern, die für eine einzelne Grafik Adapter oder ein integrierter Grafikkarte Adapter Gerät geschrieben wird, müssen alle Anforderungen in den Spezifikationen WDDM 1.1 definierten erfüllen.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.displayrender"></a>
## <a name="devicegraphicswddm11displayrender"></a>Device.Graphics.WDDM11.DisplayRender

*Die Basis Featuregruppe von Treibern, die Unterstützung für alle Versionen des WDDM für Anzeige und Rendern DDIs implementiert.*

### <a name="devicegraphicswddm11displayrenderbase"></a>Device.Graphics.WDDM11.DisplayRender.Base

*Ein Graphic-Treiber, der für eine einzelne Grafik Adapter oder ein integrierter Grafikkarte Adapter Gerät geschrieben wird, muss die Anforderungen, die in den Spezifikationen WDDM 1.1 definierten erfüllen.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.displayrender.d3d9overlay"></a>
## <a name="devicegraphicswddm11displayrenderd3d9overlay"></a>Device.Graphics.WDDM11.DisplayRender.D3D9Overlay

*Das optionale Feature implementiert 1.1 WDDM-Treiber und höher ermöglicht es für Flächen in einer Überlagerung Hardware dargestellt werden sollen.*

### <a name="devicegraphicswddm11displayrenderd3d9overlayd3d9overlay"></a>Device.Graphics.WDDM11.DisplayRender.D3D9Overlay.D3D9Overlay

*Ein WDDM1.1 Treiber muss Direct3D 9 Überlagerungen unterstützen.*

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

Wenn der Treiber WDDM1.1 Direct3D 9 Überlagerungen unterstützt, sind wie folgt die video Überlagerung Präsentation-Anforderungen:

-   WDDM-Treiber Version 1.1 muss die D3DCAPS festgelegt\_ÜBERLAGERUNG Bit im Feld D3DCaps9.Caps.

-   WDDM-Treiber v1. 1 muss Abfragetyp D3DDDICAPS unterstützen\_CHECKOVERLAYSUPPORT zu Benutzermodus PfnGetCaps DDI anrufen.

-   WDDM-Treiber v1. 1 muss Überlagerungen unterstützen in mindestens einen gültigen Konfiguration (Displaymode, OverlayFormat, Breite und Höhe) zu DDICHECKOVERLAYSUPPORTDATA aufgerufen für unterstützten Überlagerung und die maximale Breite und Höhe des unterstützten Überlagerung muss größer als 0 (null).

<a name="device.graphics.wddm11.render"></a>
## <a name="devicegraphicswddm11render"></a>Device.Graphics.WDDM11.Render

*Die Basis-Featuregruppe durch Treiber unterstützt alle Versionen von der WDDM Rendern DDIs implementiert.*

### <a name="devicegraphicswddm11renderbase"></a>Device.Graphics.WDDM11.Render.Base

*Ein Graphic-Treiber, der für eine einzelne Grafik Adapter oder ein integrierter Grafikkarte Adapter Gerät geschrieben wird, muss die Anforderungen, die in den Spezifikationen WDDM 1.1 definierten erfüllen.*

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

Finden Sie unter Anforderung **Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.render.dxvahd"></a>
## <a name="devicegraphicswddm11renderdxvahd"></a>Device.Graphics.WDDM11.Render.DXVAHD

*Die optionale Funktion, die vom 1.1 WDDM-Treiber unterstützt die neue statusbasierte video Verarbeitung DDIs implementiert wird.*

### <a name="devicegraphicswddm11renderdxvahddxvahd"></a>Device.Graphics.WDDM11.Render.DXVAHD.DXVAHD

*WDDM1.1-Treiber unterstützt DXVA HD*

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

Wenn der Treiber WDDM1.1 DXVA HD unterstützt, klicken Sie dann die folgenden Eingaben Formate (D3DDDICAPS\_DXVAHD\_GETVPINPUTFORMATS) muss unterstützt werden:

-   YUY2
-   AYUV
-   NV12
-   X8R8G8B8
-   A8R8G8B8

Der Treiber muss auch die folgenden Ausgabeformate unterstützen (D3DDDICAPS\_DXVAHD\_GETVPOUTPUTFORMATS):

-   X8R8G8B8
-   A8R8G8B8



<a name="device.graphics.wddm12"></a>
## <a name="devicegraphicswddm12"></a>Device.Graphics.WDDM12

*Die Basis-Featuregruppe durch Unterstützung WDDM 1.2 Treiber implementiert.*

### <a name="devicegraphicswddm12base"></a>Device.Graphics.WDDM12.Base

*Grafiktreiber müssen gemäß der Spezifikation WDDM 1.2 implementiert werden.*

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

<html>
    <p>
Die WDDM v1. 2 ist eine Obermenge von WDDM 1.1 und WDDM 1.0.  <br />
Es folgt eine Zusammenfassung dieser WDDM-Versionen:    </p>
    <table>
        <thead>
            <tr class="header">
                <th>Betriebssystem</th>
                <th>Treibermodelle unterstützt</th>
                <th>D3D-Versionen unterstützt werden</th>
                <th>Aktivierte Features</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Windows Vista</td>
                <td>
WDDM 1.0<br />
XDDM auf Server und begrenzte UMPC                </td>
                <td>D3D9 D3D10</td>
                <td>Planen, für die Verwaltung von Fehlertoleranz D3D9 &amp; 10</td>
            </tr>
            <tr class="even">
                <td>Windows Vista SP1 / Windows 7-Client pack</td>
                <td>
WDDM 1.05<br />
XDDM unter Server 2008                </td>
                <td>D3D9, D3D10, D3D10.1</td>
                <td>+ Unterstützung von BGRA in D3D10 D3D 10.1</td>
            </tr>
            <tr class="odd">
                <td>Windows 7</td>
                <td>
WDDM 1.1<br />
XDDM auf Server 2008 R2                </td>
                <td>D3D9 D3D10 D3D10.1, D3D11</td>
                <td>
GDI-Hardwarebeschleunigung<br />
Herstellen einer Verbindung und Konfigurieren von zeigt DXVA HD, D3D11                </td>
            </tr>
            <tr class="even">
                <td>Windows 8</td>
                <td>WDDM 1.2</td>
                <td>D3D9, D3D10, D3D10.1, D3D11, D3D11.1</td>
                <td>
Reibungslose Drehung<br />
3D Stereo<br />
D3D11-Video<br />
GPU-Unterbrechung<br />
TDR Verbesserungen<br />
Diagnose Verbesserungen<br />
Leistung und Speicherverwendung Optimierungen<br />
Power-Verwaltung<br />
usw.
                </td>
            </tr>
        </tbody>
    </table>

    <p>WDDM v1.2 also introduces new types of graphics drivers, targeting specific scenarios and is described below:</p>
    <ul>
        <li><p>WDDM Full Graphics Driver: This is the full version of the WDDM graphics driver that supports hardware accelerated 2D &amp; 3D operations. This driver is fully capable of handling all the render, display, and video functions. WDDM 1.0 and WDDM 1.1 are full graphics drivers. All Windows 8 client systems must have a full graphics WDDM 1.2 device as the primary boot device.</p></li>
        <li><p>WDDM Display Only Driver: This driver is only supported as a WDDM 1.2 driver and enables IHVs to write a WDDM based kernel mode driver that is capable of driving display only devices. The OS handles the 2D or 3D rendering using a software simulated GPU.</p></li>
        <li><p>WDDM Render Only Driver: This driver is only supported as a WDDM 1.2 driver and enables IHVs to write a WDDM driver that supports only rendering functionality. Render only devices are not allowed as the primary graphics device on client systems.</p></li>
    </ul>
    <p>Table below explains the scenario usage for the new driver types:</p>
    <table>
        <thead>
            <tr class="header">
                <th> </th>
                <th>Client</th>
                <th>Server</th>
                <th>Client running in a Virtual Environment</th>
                <th>Server Virtual</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Full Graphics</td>
                <td>Required as boot device</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="even">
                <td>Display Only</td>
                <td>Not allowed</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="odd">
                <td>Render Only</td>
                <td>Optional as non primary adapter</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="even">
                <td>Headless</td>
                <td>Not allowed</td>
                <td>Optional</td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>WDDM v1.2 Feature caps</strong>
    </p>
    <p>The table below lists the requirements for a WDDM v1.2 driver to specify to Windows the WDDM Driver Type, version, and the feature caps (visible to dxgkrnl) that WDDM v1.2 drivers are required to set. If a driver has wrongfully claimed itself as &quot;WDDM v1.2&quot; or has implemented partial features (only some of the mandatory features), then it will fail to create an adapter and the system will fall back to the Microsoft Basic Display Driver.</p>
    <p><strong>WDDM Driver Requirements</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>WDDM driver type</th>
                <th>DDI requirements</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Full Graphics</td>
                <td>Implement all the Render-specific and the Display-specific required DDIs</td>
            </tr>
            <tr class="even">
                <td>Display-Only</td>
                <td>Implement all the Display-specific DDIs and return a null pointer for all the Render-specific DDIs</td>
            </tr>
            <tr class="odd">
                <td>Render-Only</td>
                <td>
                    Implement all the Render-specific DDIs and return a null pointer for all the Display-specific DDIs<br />
                    <strong>OR</strong><br />
                    Implement all the DDIs for a full WDDM driver but report DISPLAY_ADAPTER_INFO::NumVidPnSources = 0 and DISPLAY_ADAPTER_INFO::NumVidPnTargets = 0
                </td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>WDDM v1.2 Feature Caps</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>Feature</th>
                <th>WDDM Driver Type</th>
                <th>Feature Caps</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td> </td>
                <td> <strong>Full Graphics</strong></td>
                <td><strong>Render Only</strong></td>
            </tr>
            <tr class="even">
                <td>WDDM version</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="odd">
                <td>Bugcheck and PnP Stop support for Non VGA</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="even">
                <td>Optimized screen rotation Support</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="odd">
                <td>GPU Preemption</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>FlipOnVSyncMmIo</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="odd">
                <td>TDR Improvements</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>Optimizing the graphics stack to improve performance on sleep &amp; resume</td>
                <td><strong>O</strong></td>
                <td><strong>O</strong></td>
            </tr>
            <tr class="odd">
                <td>Stereoscopic 3D: New infrastructure to process and present stereoscopic content</td>
                <td><strong>O</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="even">
                <td>DirectFlip</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="odd">
                <td>GDI Hardware acceleration (This is a required WDDM v1.1 feature)</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>GPU power management of idle and active power</td>
                <td><strong>O</strong></td>
                <td><strong>O</strong></td>
            </tr>
        </tbody>
    </table>
</html>

<a name="device.graphics.wddm12.display"></a>
## <a name="devicegraphicswddm12display"></a>Device.Graphics.WDDM12.Display

*Anzeigen der Feature-Anforderungen für alle WDDM12-Treiber, die Anzeige unterstützen, bestimmte DDIs*

### <a name="devicegraphicswddm12displaybase"></a>Device.Graphics.WDDM12.Display.Base

*Zeigt an, für eine WDDM-Grafikkarte zur Unterstützung von Funktionen*

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

WDDM wurde erweitert, um einen WDDM-Treiber unterstützt, der nur für die Anzeige Scan-Funktionen zuständig ist. Ein solchen Treiber ist nicht zulässig, um eine beliebige Renderingfunktionen zu unterstützen.

Ein Treiber gilt nur Anzeige WDDM-Treiber, wenn sie die folgenden DDIs implementiert.
 

**Allgemeine WDDM DDIs**

Diese DDIs gelten für die allgemeine Gerät-Funktionen wie Plug & Play-Unterstützung und Unterstützung für Power. Alle WDDM-Treiber diese Funktionen erforderlich sind, und wenn nicht implementiert, der Treiber wird nicht gestartet werden von Windows. Diese DDIs befinden sich bereits [in WDK dokumentiert](http://msdn.microsoft.com/en-us/library/ff554066.aspx).

**Erforderlich:**

 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**Optional:**

 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\***DxgkDdiInterruptRoutine** -Funktion ist erforderlich, wenn das aktuelle Hardwaregerät einen Hardwareinterrupt meldet. In diesem Fall würde der Treiber diese Funktion DDI nicht angegeben wurde, das Betriebssystem die Initialisierung fehlschlagen. Wenn die aktuelle Hardware verfügt nicht über ein Hardwareinterrupt und der Treiber diese Funktion DDI anbietet, das Betriebssystem können trotzdem diesem Treiber geladen werden, und DxgkDdiInterruptRoutine wird nie aufgerufen werden.

\***DdiNotifyAcpiEvent** DDI-Funktion wird verwendet, um Grafiktreiber auf einige ACPI Ereignisse zu benachrichtigen. Es ist optional für das Rendering-Gerät. Auf normale WDDM Grafiken Geräten gibt diese Funktion DDI ein Flag an, dass dxgkrnl.sys um einige weiteren Aktionen ausgeführt werden wie Anzeigemodus zurücksetzen oder Abfragen verbundenen Monitore zurück. Für das Gerät Rendering nur diese Flags werden nicht verwendet und müssen auf 0 (null) festgelegt werden.
 

**Nur DDIs anzeigen**

Die folgenden Funktionen DDI müssen von einem Treiber nur Anzeige implementiert werden. Wenn der Treiber nicht alle diese DDIs angeben, wird Windows nicht initialisieren von diesem Treiber.

 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite
 - DxgkDdiI2CReceiveDataFromDisplay
 - DxgkDdiI2CTransmitDataFromDisplay

\***DxgkDdiSetPalette** ist eine erforderliche DDI. Wenn der Treiber eine beliebige Palettenmodus nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

\*\***DxgkDdiSetPointerPosition** und **DxgkDdiSetPointerShape** sind erforderlich DDIs. Wenn der Treiber eine beliebige Hardwarecursor nicht unterstützt werden, sollten sie weiterhin diese beiden DDIs bereitstellen.

\*\*\***DxgkDdiRecommendFunctionalVidPn** ist eine DDI erforderlich. Wenn der Treiber jedes Ereignis ACPI nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

### <a name="devicegraphicswddm12displaycontaineridsupport"></a>Device.Graphics.WDDM12.Display.ContainerIDSupport

*Eine Grafikkarte muss die DDI Container ID unterstützen.*

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

Eine Grafikkarte muss **DxgkDdiGetDeviceContainer** DDI implementieren. Windows verwenden dieser DDI, bitten Sie den Treiber für die Container-ID. Der Treiber muss testen und Container-ID aus der Anzeigehardware zu erhalten.

Für den Fall, dass Anzeigegeräts keine Container-ID bereitstellt, wird Windows automatisch eine Container-ID für die Anzeige produzieren. Die Eindeutigkeit des Container-ID erfolgt mithilfe der Herstellung ID, die Produkt-ID und die Seriennummer der Anzeige von der EDID abgerufen. Mithilfe dieser Informationen kann ein Treiber für ein anderes Gerät dieselbe Container-ID wie Anzeigegeräts generieren Sie mithilfe der RtlGenerateClass5Guid-Funktion in wdm.h enthalten.

### <a name="devicegraphicswddm12displaydisplayoutputcontrol"></a>Device.Graphics.WDDM12.Display.DisplayOutputControl

*Unterstützung für WDDM er die Kontrolle über die Ausgabe während der Ausführung des WDDM-Treibers*

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

Es besteht eine Notwendigkeit für eine nahtlose Hand anderes Steuerelement Anzeige zwischen Windows- und der WDDM Graphics-Treiber. Dies bedeutet, dass in einigen Fällen Windows die Kontrolle über die Überprüfung anzeigen, ohne Plug & Play-beenden dauern WDDM-Treiber muss.

Ein solches Szenario ist, wenn Windows muss Fehler überprüfen Sie das System und der blaue Bildschirm. Diese Sammlung von DDIs ermöglicht, übersichtlicherer Hand deaktiviert.

Die folgenden DDIs werden benötigt, um von einem vollständig und Anzeige nur WDDM 1.2 Treiber implementiert werden.

 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

Diese DDIs sind [hier auf WDK dokumentiert](http://msdn.microsoft.com/en-us/library/ff554066.aspx): <http://msdn.microsoft.com/en-us/library/ff554066.aspx>.

Im folgenden sind die Anforderungen für WDDM-Treiber während diese DDIs implementieren:

-   Wenn Windows DxgkDdiSystemDisplayEnable aufruft, muss ein Treiber alle GPU Vorgänge abbrechen oder GPU auf Leerlauf zurückgesetzt.

-   Windows stellt ein Ziel-ID als Teil des Anrufs DDI bereit. Der Treiber muss weiterhin Laufwerk die Anzeige der Ziel-ID zugeordnet ist

    -   Der Treiber muss die Konnektivität für die Anzeige auf der angegebenen Ziel-ID überprüfen. Wenn angegeben Ziel verfügt nicht über eine Darstellung verbunden ist, sollte der Treiber Fehlschlagen dieses Anrufs mit dem STATUS\_NICHT\_UNTERSTÜTZT.

    -   Der Treiber muss alle anderen zeigt auf den Adapter mit Ausnahme der Ziel-ID verbunden werden, sofern das Signal deaktivieren.

        -   Wenn dies nicht möglich ist, sollte der Treiber testen und ein leeres Bild auf allen anderen Monitoren zu platzieren.

        -   Wenn dies nicht möglich ist, muss der Treiber das letzte Bild auf dem Bildschirm bleibt unverändert lassen.

-   Für die ausgewählte Ziel-ID muss der Treiber beibehalten des aktuellen Anzeigemodus und Bereitstellen von diesen Modus zurück zu Windows als Teil des Anrufs DDI.

    -   Fall, dass der Treiber nicht auf den aktuellen Modus verwalten kann ODER Ziel-ID nicht Bestandteil der aktiven Topologie ist, der Treiber sollte versuchen und die systemeigene Auflösung der Anzeige ODER ein hochauflösende-Modus. Zumindest muss der Treiber auf einen Modus zurückgesetzt, das größer als oder gleich 640 x 480 24 Bit pro Pixel-farbenformat auf das angegebene Ziel.

    -   Es ist NICHT erforderlich, dass der Treiber linear Frame-Puffer-Modus verwendet werden soll. Der Treiber sollte den Schreibvorgang aus einer D3DDDIFMT unterstützt\_A8R8G8B8 Quelle an diesen Framepuffer.

-   Auf hoher Ebene IRQL oder das System Fehlercode wurde, kann diese Funktion aufgerufen werden. Der Treiber sollte legen Sie diese Funktion im Abschnitt nicht ausgelagerten Code und nur nicht ausgelagerten Speicher verwenden.

    -   Windows Kernelmodus-Funktionen möglicherweise NICHT verfügbar, wenn diese Funktion aufgerufen wird.

-   Sobald der Treiber Kontrolle der Anzeige an Windows übergeben wurde, wird Windows die DxgkDdiSystemDisplayWrite DDI verwenden, um die Bildschirmanzeige zu aktualisieren. Windows wird die DDI verwenden, um einen Block von Bild aus der angegebenen Quelle ein Bild auf dem Bildschirm zu schreiben, die über DxgkDdiSystemDisplayEnable Funktion zurückgesetzt wird. Diese Funktion wird der Treiber die Startadresse der Quelle ein Bild als auch die Schrittweite, Breite und Höhe übergeben. Die Quelle ein Bild-farbenformat ist immer D3DDDIFMT\_X8R8G8B8. Windows wird sichergestellt, dass das Bild Datenquelle im Arbeitsspeicher nicht ausgelagerten ist. Der Treiber muss dieses Quellbild zum aktuellen Bildschirm an (PostionX PositionY) schreiben.

-   Auf hoher Ebene IRQL oder das System Fehlercode wurde, kann diese Funktion aufgerufen werden. Der Treiber sollte legen Sie diese Funktion im Abschnitt nicht ausgelagerten Code und nur nicht ausgelagerten Speicher verwenden.

    -   Windows Kernelmodus-Funktionen möglicherweise NICHT verfügbar, wenn diese Funktion aufgerufen wird.

-   Es wird empfohlen, die CPU verwenden, um das Bild schreiben aus dem Frame Quelle möglicherweise Puffer, da der Fehlercode durch wiederholte TDR und der GPU verursacht werden möglicherweise in eine unbekannte Bedingung.

### <a name="devicegraphicswddm12displaymodeenumeration"></a>Device.Graphics.WDDM12.Display.ModeEnumeration

*Anforderungen für Modus-Aufzählung*

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

**Ziel-Modi**

-   Eine Grafikkarte muss Skalieren einer beliebigen Auflösung scannen, die größer als oder gleich 1024 x 768 progressiv unter 32 Bit pro Pixel und maximal Anzeigedauer, die von 148.5 Mhz Pixel-Clock pro die VESA und Branchenstandards und Richtlinien für Computer Anzeige Monitor Timing (DMT) November 2007 Update oder CEA-861-E-Spezifikationen. Graphics-Treiber unterstützt möglicherweise Modi, die größer oder kleiner als diese Einschränkungen sind, aber der Treiber ist dies nicht erforderlich.

-   Die Grafiktreiber ist nicht erforderlich, wenn alle interlaced Anzeigedauer, aber möglicherweise dazu entschließen.

-   Während des Anrufs DxgkDdiEnumVidPnCofuncModality DDI müssen den unterstützten Ziel Modi größer als oder gleich der Modi angeheftete Quelle mit Ausnahme von analogen TV Connectortyp oder wenn das Ziel nicht für jede zeitliche Steuerung mit einer Auflösung von 1024 x 768 oder höher unterstützt sein. Dies bedeutet, dass der Treiber für alle anderen Verwendungen nur eine vertikale Skalierung darf. Ein Treiber kann downscaling unterstützen, wenn der Benutzer diese speziell für Overscan Vergütung auf TV anfordert.

**Source-Modi**

-   Eine Grafikkarte muss die systemeigene Auflösung integrierte Systemsteuerung unterstützen.

-   Wenn die Grafikkarte genügend Bandbreite aufweist, muss die systemeigene Auflösung einer verbundenen Anzeige unterstützt werden.

-   Graphics-Treiber muss mindestens ein Source-Modus für alle erreichbaren detaillierte Anzeigedauer in der EDID der Anzeige auflisten.

-   Ist der einzige Modus von Anzeigegeräts unterstützt kleiner oder gleich 640 x 480, kann der Treiber in diesem Fall Bildbearbeitungsprogramms aus. Der Source-Modus muss jedoch mindestens 800 x 600 sein.

-   Graphics-Treiber muss nur Datenquellen Modi 32 Bit pro Pixel oder höher auflisten.

**Für den Modus Duplicate (Wenn Sie den Klon)**

-   Wenn 2 zeigt, die in doppelte Modus konfiguriert sind, muss die Grafikkarte die Einstellung der folgenden Konfiguration unterstützen:

    -   Wenn alle allgemeinen detaillierte Anzeigedauer zwischen den 2 zeigt, die kleiner oder gleich 1920 x 1080 progressiv unter 32 Bit pro Pixel sind vorhanden sind, muss die Grafikkarte wird unter dieser Timing im Modus doppelte gesteuerter unterstützen.


-   Zumindest müssen in doppelte Modus 1024 x 768 unterstützt werden.

-   Für mehr als 2 zeigt in doppelte Modus konfiguriert sind kann die Grafikkarte geeigneten Modus zur Unterstützung von wählen.

-   Mindestens ungeachtet der Anzahl der im doppelte Modus zeigt muss die Grafikkarte zur Unterstützung der ein Source-Modus von 1024 x 768 progressiv unter 32 Bit pro Pixel in den doppelten Modus können.

**Für Erweiterungsmodus**

-   Wenn 2 zeigt, die im erweiterten Modus konfiguriert sind, muss die Grafikkarte unterstützen die folgende Konfiguration festlegen:

    -   Auf Systeme mit integrierten zeigt: Native Auflösung auf integrierte Anzeige- und gleichzeitig bis zu 1920 x 1080 progressiv unter 32 Bit pro Pixel für die Anzeige nicht integrierten

    -   Bis zu 1920 x 1080 progressiv unter 32 Bit pro Pixel auf jedem Monitor nicht integriert

-   Für mehr als 2 zeigt, die im erweiterten Modus konfiguriert werden kann die Grafikkarte ein entsprechenden Satz von Modi zur Unterstützung von der verfügbaren Bandbreite Grundlage auswählen.

### <a name="devicegraphicswddm12displaypnpstopstartsupport"></a>Device.Graphics.WDDM12.Display.PnpStopStartSupport

*Unterstützung für Plug & Play-Stop in WDDM*

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

Seit der Einführung von WDDM ist jede Treiber erforderlich, wenn Plug & Play-starten und beenden. Diese Anforderung wird die Unterstützung für Plug & Play-starten und beenden in WDDM verbessert.

Sobald ein WDDM-Treiber beendet ist, muss Windows Steuerung über das Anzeige-Steuerelement und wenn der Treiber gestartet wird, Windows-Anforderungen für die Weitergabe wieder anzeigen an den Treiber.

WDDM 1.2 führt eine neue DDI Hinzufügen von Unterstützung für UEFI-basierte Systeme und der Benutzer in ein solches Szenario zu optimieren.

Die folgenden DDIs werden benötigt, um von einem vollständig und Anzeige nur WDDM 1.2 Treiber implementiert werden.

 - DxgkDdiReleasePostDisplayOwnership

Im folgenden werden die Anforderungen für den Treiber beim Implementieren dieser DDI Verknüpft.

-   Windows stellt ein Ziel-ID als Teil des Anrufs DDI bereit. Der Treiber muss weiterhin Laufwerk die Anzeige der Ziel-ID zugeordnet ist

    -   Überprüfen der der Treiber muss die Konnektivität für die Anzeige auf der angegebenen Ziel-ID Wenn angegeben, Ziel verfügt nicht über eine Darstellung verbunden ist, sollte der Treiber Fehlschlagen dieses Anrufs mit dem STATUS\_NICHT\_UNTERSTÜTZT.

    -   Der Treiber muss alle anderen zeigt auf den Adapter mit Ausnahme der Ziel-ID verbunden werden, sofern das Signal deaktivieren.

        -   Wenn dies nicht möglich ist, sollte der Treiber testen und ein leeres Bild auf allen anderen Monitoren zu platzieren.

        -   Wenn dies nicht möglich ist, muss der Treiber das letzte Bild auf dem Bildschirm bleibt unverändert lassen.

-   Befindet sich ein ACPI-ID zugeordnet ist die Ziel-ID und dann wieder an den Windows als Teil der Rückgabe-Datenstruktur PDXGK bereitgestellt werden müssen\_ANZEIGE\_INFORMATIONEN.

-   Für die ausgewählten Ziel-ID muss der Treiber des aktuellen Anzeigemodus behalten und Bereitstellen von diesen Modus zurück zu Windows als Teil des Aufrufs DDI.

    -   Fall, dass der Treiber nicht auf den aktuellen Modus verwalten kann ODER Ziel-ID nicht Bestandteil der aktiven Topologie ist, sollte der Treiber wählen Sie eine alternative active Ziel und versuchen Sie es und verwalten die aktuelle Auflösung des, abzielen. Wenn dies nicht möglich ist, der Treiber sollte versuchen und die systemeigene Auflösung der Anzeige ODER ein hochauflösende-Modus. Der Treiber muss zumindest, um einen Modus, die größer als oder gleich 800 x 600 24bpp zurückgesetzt (D3DDDIFMT\_R8G8B8) oder 32-bpp (D3DDDIFMT\_X8R8G8B8).

    -   Wenn kein Ziel aktiv ist, sollten der Treiber versuchen, um ein Ziel zu aktivieren. Vorzugsweise interner Leiste (sofern verfügbar).

-   Der Treiber muss bereinigen den aktuellen Framepuffer, deaktivieren Hardwarecursor, deaktivieren alle Überlagerungen und legen Sie auf Standard GAMMA lernen.

-   Der Treiber muss aktuellen Framepuffer linear (entweder mithilfe von Swizzle Bereich oder Swizzle Modus deaktivieren) vornehmen.

-   Der Treiber muss den aktuellen Framepuffer von CPU zugänglich machen.

-   Der Treiber muss sicherstellen, dass die Sichtbarkeit auf das angegebene Ziel "aktiviert" festgelegt ist.

### <a name="devicegraphicswddm12displayprovidelinearframebuffer"></a>Device.Graphics.WDDM12.Display.ProvideLinearFrameBuffer

*Ein Grafikgerät kann einen lineare Framepuffer verwendbar durch Windows bereitstellen.*

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

Es gibt zahlreiche Szenarien, in dem Komponenten in das Windows-Betriebssystem Lage sein müssen, um die Anzeige zu aktualisieren, wenn ein IHV-Treiber nicht geladen wird. Einige dieser Szenarien sind: Boot, Fehlercode, abgesicherten Modus, Treiber Upgrades etc.. Um sicherzustellen, dass ein Grafikgerät mit diese Szenarien Windows kompatibel ist, müssen sie folgende Schritte ausführen:

1.  Stellen Sie sicher, ohne Addition IHV/OEM-Updates auf den Framepuffer, überprüft.

2.  Software/Treiber. Geben Sie linear Frame Puffers, CPU bei Bedarf aus der IHV-Treiber zugegriffen werden.

3.  In UEFI-Systemen beim Start UEFI 2.3 GOP verwenden.

4.  Auf BIOS-Systemen VBE 3.0 Standards verwenden.

<a name="device.graphics.wddm12.displayonly"></a>
## <a name="devicegraphicswddm12displayonly"></a>Device.Graphics.WDDM12.DisplayOnly

*Die optionale Featuregruppe durch 1.2 WDDM-Treiber, nur die Anzeige unterstützen, implementiert bestimmte DDIs.*

### <a name="devicegraphicswddm12displayonlybase"></a>Device.Graphics.WDDM12.DisplayOnly.Base

*Zeigt an, für eine WDDM-Grafikkarte zur Unterstützung von Funktionen*

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

WDDM wurde erweitert, um einen WDDM-Treiber unterstützt, der nur für die Anzeige Scan-Funktionen zuständig ist. Ein solchen Treiber ist nicht zulässig, um eine beliebige Renderingfunktionen zu unterstützen.

Ein Treiber gilt nur Anzeige WDDM-Treiber, wenn nur die folgenden DDIs implementiert und wird dem Rendern DDIs nicht implementiert.
 

**Allgemeine WDDM DDIs**

Diese DDIs sind für die allgemeine Gerät Funktionen wie Plug & Play-Unterstützung und Unterstützung für Power. Alle WDDM-Treiber diese Funktionen erforderlich sind, und wenn nicht implementiert, der Treiber wird nicht gestartet werden von Windows. Diese DDIs sind bereits [in der WDK dokumentiert](http://msdn.microsoft.com/en-us/library/ff554066.aspx): <http://msdn.microsoft.com/en-us/library/ff554066.aspx>.

**Erforderlich:**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**Optional:**
 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\***DxgkDdiInterruptRoutine** -Funktion ist erforderlich, wenn das aktuelle Hardwaregerät Hardwareinterrupt meldet. In diesem Fall würde der Treiber diese Funktion DDI nicht angegeben wurde, das Betriebssystem die Initialisierung fehlschlagen. Wenn die aktuelle Hardware hat keinen Interrupt und der Treiber diese Funktion DDI anbietet, das Betriebssystem können trotzdem diesem Treiber geladen werden, und **DxgkDdiInterruptRoutine** wird nie aufgerufen werden.

\***DdiNotifyAcpiEvent** DDI-Funktion wird verwendet, um Grafiktreiber auf einige ACPI Ereignisse zu benachrichtigen. Es ist optional bei einem Gerät rendern. Auf normale WDDM Grafiken Geräten gibt diese Funktion DDI ein Flag an, dass dxgkrnl.sys um einige weiteren Aktionen ausgeführt werden wie Anzeigemodus zurücksetzen oder Abfragen verbundenen Monitore zurück. Für das Gerät Rendering nur diese Flags werden nicht verwendet und müssen auf 0 (null) festgelegt werden.
 

**Nur DDIs anzeigen**

Folgende DDI sind Funktionen von einem Treiber nur Anzeige implementiert werden. Wenn der Treiber nicht alle diese DDIs angeben, wird Windows nicht initialisieren von diesem Treiber.

 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

\***DxgkDdiSetPalette** ist eine DDI erforderlich. Wenn der Treiber eine beliebige Palettenmodus nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

\*\***DxgkDdiSetPointerPosition** und **DxgkDdiSetPointerShape** sind erforderlich DDIs. Wenn der Treiber eine beliebige Hardwarecursor nicht unterstützt werden, sollten sie weiterhin diese beiden DDIs bereitstellen.

\*\*\***DxgkDdiRecommendFunctionalVidPn** ist eine DDI erforderlich. Wenn der Treiber eine beliebige ACPI-Ereignis nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

*Entwerfen Hinweis:* Das einzige farbenformat unterstützt für die Anzeige nur Treiber ist D3DDDIFMT\_A8R8G8B8; aus diesem Grund sollten diese Treiber Quelle Kommunikationsmodi dieses Format nur auflisten.

<a name="device.graphics.wddm12.displayrender"></a>
## <a name="devicegraphicswddm12displayrender"></a>Device.Graphics.WDDM12.DisplayRender

*Die optionale Featuregruppe durch 1.2 WDDM-Treiber unterstützt sowohl implementiert anzeigen und DDIs zu rendern.*

### <a name="devicegraphicswddm12displayrenderbase"></a>Device.Graphics.WDDM12.DisplayRender.Base

*Anforderungen für eine Implementierung Rendern und anzeigen DDIs WDDM-Grafikkarte*

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

WDDM wurde erweitert, um einen WDDM-Treiber unterstützt, der nur für die Anzeige Scan-Funktionen zuständig ist. Ein solchen Treiber ist nicht zulässig, um eine beliebige Renderingfunktionen zu unterstützen.

WDDM wurde auch erweitert, um einen WDDM-Treiber unterstützt, der nur für das Rendering und berechnen DDIs verantwortlich ist. Ein solchen Treiber ist nicht zulässig, Anzeige Scan-Funktionen unterstützt.

Des Treibers metrische oder DDI des (Ansicht und Rendern) implementieren, gelten vollständige Grafikkarten.
 

**Allgemeine WDDM DDIs**

Diese DDIs sind für die allgemeine Gerät Funktionen wie Plug & Play-Unterstützung und Unterstützung für Power. Alle WDDM-Treiber diese Funktionen erforderlich sind, und wenn nicht implementiert, der Treiber wird nicht gestartet werden von Windows. Diese DDIs befinden sich bereits [in WDK dokumentiert](http://msdn.microsoft.com/en-us/library/ff554066.aspx): <http://msdn.microsoft.com/en-us/library/ff554066.aspx>.

**Erforderlich:**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**Optional:**
 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\*DxgkDdiInterruptRoutine-Funktion ist erforderlich, wenn die aktuelle Hardwaregerät Hardwareinterrupt meldet. In diesem Fall würde der Treiber diese Funktion DDI nicht angegeben wurde, das Betriebssystem die Initialisierung fehlschlagen. Wenn die aktuelle Hardware verfügt nicht über einen Interrupt und der Treiber diese Funktion DDI anbietet, das Betriebssystem können trotzdem diesem Treiber geladen werden, und DxgkDdiInterruptRoutine wird nie aufgerufen werden.
 

**Nur DDIs anzeigen**

Folgende DDI sind Funktionen von einem Treiber nur Anzeige implementiert werden. Wenn der Treiber nicht alle diese DDIs angeben, wird Windows nicht initialisieren von diesem Treiber.
 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

\***DxgkDdiSetPalette** ist eine DDI erforderlich. Wenn der Treiber eine beliebige Palettenmodus nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

\*\***DxgkDdiSetPointerPosition** und **DxgkDdiSetPointerShape** sind erforderlich DDIs. Wenn der Treiber eine beliebige Hardwarecursor nicht unterstützt werden, sollten sie weiterhin diese beiden DDIs bereitstellen.

\*\*\***DxgkDdiRecommendFunctionalVidPn** ist eine DDI erforderlich. Wenn der Treiber eine beliebige ACPI-Ereignis nicht unterstützt, sollten sie weiterhin diese DDI bereitstellen.

\***DdiNotifyAcpiEvent** DDI-Funktion wird verwendet, um Grafiktreiber auf einige ACPI Ereignisse zu benachrichtigen. Es ist optional bei einem Gerät rendern. Auf normale WDDM Grafiken Geräten gibt diese Funktion DDI ein Kennzeichen angibt dxgkrnl.sys einige weitere Aktionen wie Ausführen des Anzeigemodus zurücksetzen oder verbundenen Monitore Abfragen zurück. Für das Gerät Rendering nur diese Flags werden nicht verwendet und müssen auf 0 (null) festgelegt werden.
 

**Nur DDIs Rendern**

Diese Funktionen DDI sind für das Rendering-Funktionen.

**Erforderlich:**

 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**Optional:**

Wenn die Hardware Rendering Swizzling Ranger unterstützt, sollte der Treiber auch die beiden folgenden Funktionen zur Verfügung stellen:

 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

<a name="device.graphics.wddm12.displayrender.processingstereoscopicvideocontent"></a>
## <a name="devicegraphicswddm12displayrenderprocessingstereoscopicvideocontent"></a>Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent

*Die optionale Featuregruppe, die von WDDM 1.2 Treiber die Unterstützung Stereoskopisches video Verarbeitung implementiert.*

### <a name="devicegraphicswddm12displayrenderprocessingstereoscopicvideocontentprocessingstereoscopicvideocontent"></a>Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent.ProcessingStereoscopicVideoContent

*Wenn eine Grafikkarte Präsentation und Verarbeitung von Videoinhalten Stereoskopisches unterstützt, muss der DXGI Spezifikation für Stereo 3D entsprechen.*

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

WDDM 1.2 Treiber können optional Videodaten für Stereo kodiert verarbeitet. Wenn der Treiber veröffentlicht, dass es kann Stereo unterstützen, müssen sie die Verarbeitung von Inhalten in unterstützen, horizontal und vertikal angeordnet linken und rechten Auge Ansichten sowie separater Streams für die linken und rechten Auge Ansichten.
Darüber hinaus Wenn der Treiber veröffentlicht, dass es kann Stereo unterstützt, es kann optional auch verarbeitet die folgenden Stereo Inhaltslayouts:

-   Zeile überlappend  
-   Spalte überlappend  
-   Schachbrett  
-   Gespiegelten Konfigurationen

Schließlich kann der Treiber optional neue Stereo Verarbeitung Features unterstützen:

-   Mono offset
-   Stereo Auge Anpassung

Für alle optionalen Inhaltslayouts und Verarbeitung Features muss der Treiber veröffentlichen, die entsprechenden Cap hat, um anzugeben, ob das Feature unterstützt.

<a name="device.graphics.wddm12.displayrender.runtimepowermgmt"></a>
## <a name="devicegraphicswddm12displayrenderruntimepowermgmt"></a>Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt

*Die optionale Featuregruppe durch 1.2 WDDM-Treiber, die Unterstützung für die Laufzeit Power Management DDIs implementiert.*

### <a name="devicegraphicswddm12displayrenderruntimepowermgmtruntimepowermgmt"></a>Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt.RuntimePowerMgmt

*Wenn implementiert - müssen WDDM 1.2 Treiber neue WDDM 1.2 GPU Power Management DDI für F-Zustand und Status p Power Management verwenden.*

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

WDDM 1.2 Treiber können optional F-Zustand und Status p Power Management unterstützen.
Weitere Informationen zur Verwendung der SoC GPU Power Management WDDM v1. 2 DDI finden Sie in der Windows WDK-Dokumentation.

<a name="device.graphics.wddm12.render"></a>
## <a name="devicegraphicswddm12render"></a>Device.Graphics.WDDM12.Render

*Die Basis Featuregruppe durch 1.2 WDDM-Treiber, die Render unterstützen, implementiert bestimmte DDIs.*

### <a name="devicegraphicswddm12renderbase"></a>Device.Graphics.WDDM12.Render.Base

*Rendering-Anforderungen für eine WDDM-Grafikkarte zur Unterstützung von Funktionen*

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

WDDM wurde erweitert, um einen WDDM-Treiber unterstützt, der nur für das Rendering und berechnen DDIs verantwortlich ist. Ein solchen Treiber ist nicht zulässig, Anzeige Scan-Funktionen unterstützt.

Ein Treiber gilt nur Rendern WDDM-Treiber, wenn eine der folgenden zwei Bedingungen erfüllt ist:

-   Der Treiber implementiert alle für eine vollständige WDDM-Treiber erforderliche DDIs aber meldet 0 Quellen und 0 Ziele.

-   Treiber implementiert alle Render bestimmte DDIs und gibt einen null-Zeiger für alle Anzeigen bestimmter DDIs zurück. Die hierfür erforderliche DDIs werden unter bezeichnet.

**Allgemeine WDDM DDIs**

Diese Funktionen DDI sind für die allgemeine Gerät Funktionen wie Plug & Play-Unterstützung und Power. Alle WDDM-Treiber diese Funktionen erforderlich sind, und wenn nicht implementiert, der Treiber wird nicht gestartet werden von Windows. Diese DDIs sind bereits in WDK dokumentiert: <http://msdn.microsoft.com/en-us/library/ff554066.aspx>.

**Erforderlich:**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**Optional:**

 - DdiNotifyAcpiEvent\*

\*DdiNotifyAcpiEvent DDI-Funktion wird verwendet, um Grafiktreiber auf einige ACPI-Ereignisse zu benachrichtigen. Es ist optional bei einem Gerät rendern. Auf normale WDDM Grafiken Geräten gibt diese Funktion DDI ein Flag an, dass dxgkrnl.sys um einige weiteren Aktionen ausgeführt werden wie Anzeigemodus zurücksetzen oder Abfragen verbundenen Monitore zurück.  Für das Gerät Rendering nur diese Flags werden nicht verwendet und müssen auf 0 (null) festgelegt werden.
 

**Nur DDIs Rendern**

Diese DDI-Funktionen sind für das Rendering-Funktionen.

**Erforderlich:**
 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**Optional:** Wenn die Hardware Rendering Swizzling Ranger unterstützt, sollte der Treiber auch die beiden folgenden Funktionen bereitstellen:
 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

### <a name="devicegraphicswddm12renderd3d11videodecoding"></a>Device.Graphics.WDDM12.Render.D3D11VideoDecoding

*Ein Grafikkartentreiber muss die DirectX 11 Video Decoder DDI unterstützen.*

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

Anzeige WDDM 1.2 Treiber unterstützen die DirectX 11 Video Decoder DDI.

WDDM-Treiber müssen mindestens eine der folgenden Ressourcengruppen h. 264-GUIDs unterstützen:

-   D3D11\_DECODER\_PROFIL\_H264\_VLD\_NOFGT
-   D3D11\_DECODER\_PROFIL\_H264\_VLD\_FGT
-   D3D11\_DECODER\_PROFIL\_H264\_VLD\_WITHFMOASO\_NOFGT

WDDM-Treiber unterstützt mindestens eine der folgenden VC1 Modi:

-   D3D11\_DECODER\_PROFIL\_VC1\_VLD
-   D3D11\_DECODER\_PROFIL\_VC1\_D2010

If-implementiert: WDDM-Treiber unterstützt mindestens eines der folgenden MPEG2 Modi:

-   D3D11\_DECODER\_PROFIL\_MPEG2\_VLD und D3D11\_DECODER\_PROFIL\_MPEG2\_IDCT
-   D3D11\_DECODER\_PROFIL\_MPEG2\_VLD und D3D11\_DECODER\_PROFIL\_MPEG2\_MOCOMP
-   D3D11\_DECODER\_PROFIL\_MPEG2\_IDCT
-   D3D11\_DECODER\_PROFIL\_MPEG2AND1\_VLD

If implementiert: HEVC/H.265 Modi

-   D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN
-   D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN10

Es wird empfohlen für Treiber zur Unterstützung von D3D11\_DECODER\_PROFIL\_HEVC\_VLD\_MAIN10 als Main 10 ist ein sehr häufiges Format für Premium HEVC Inhalt.

If-implementiert: VPx Modi:

-   D3D11\_DECODER\_PROFIL\_VP8\_VLD
-   D3D11\_DECODER\_PROFIL\_VP9\_VLD\_PROFILE0
-   D3D11\_DECODER\_PROFIL\_VP9\_VLD\_PROFILE2 (optional, wenn Hardware Profil 2 nicht unterstützt)

Schließlich müssen WDDM-Treiber unterstützt DXGI\_FORMAT\_420\_nicht TRANSPARENT, und DXGI\_FORMAT\_NV12 als Decoder Ausgabeformate. HEVC Main 10 müssen Treiber DXGI unterstützen\_FORMAT\_P010 als Decoder Ausgabeformat.

WDDM-Treiber müssen für h. 264 standardisiert AES-128 (definiert in den Spezifikationen des WDDM v1. 1) unterstützen\* \* \* und MPEG2, wenn MPEGE2 Acceleration unterstützt wird.

Hinweise zum Entwurf

\*\*\*Unterstützung von standardisierten AES-128 muss auf X86 und X64 Architekturen und nur Betriebssysteme.

### <a name="devicegraphicswddm12renderd3d11videoprocessing"></a>Device.Graphics.WDDM12.Render.D3D11VideoProcessing

*Ein Grafikkartentreiber muss die entsprechende DDIs 11 DirectX video Verarbeitung unterstützen.*

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

Die folgende video Prozessor Gerät-Funktion DDIs muss unterstützt werden:

-   BOB zusammenfügen

    -   DXVAHDDDI\_PROZESSOR\_CAPS\_"Zusammenfügen"\_BOB
    -   D3D11\_1DDI\_VIDEO\_PROZESSOR\_PROZESSOR\_CAPS\_"Zusammenfügen"\_BOB 

-   Constriction

    -   DXVAHDDDI\_FEATURE\_CAPS\_CONSTRICTION
    -   D3D11\_1DDI\_VIDEO\_PROZESSOR\_FEATURE\_CAPS\_CONSTRICTION

-   Drehung

    -   DXVAHDDDI\_FEATURE\_CAPS\_DREHUNG
    -   D3D11\_1DDI\_VIDEO\_PROZESSOR\_FEATURE\_CAPS\_DREHUNG

-   Beliebige Strecken/verkleinern

-   Vollständige und nominal RGB-Bereiche müssen unterstützt werden, auf die Eingabe und Ausgabe YCbCr Daten, insbesondere:

    -   zwischen 0 und 255

        -   DXVAHDDDI\_STREAM\_ZUSTAND\_EINGABE\_FARBE\_SPEICHERPLATZ\_DATEN

RGB\_Feld Bereich auf 0 festgelegt ist:

-   DXVAHDDDI\_BLT\_ZUSTAND\_AUSGABE\_FARBE\_SPEICHERPLATZ\_DATEN RGB\_Feld Bereich auf 0 festgelegt ist

    -   D3D11\_1DDI\_VIDEO\_PROZESSOR\_FARBE\_SPEICHERPLATZ RGB\_Feld Bereich auf 0 festgelegt.

-   16 zu 235

    -   DXVAHDDDI\_STREAM\_ZUSTAND\_EINGABE\_FARBE\_SPEICHERPLATZ\_DATEN

RGB\_Feld Bereich auf 1 festgelegt ist:

-   DXVAHDDDI\_BLT\_ZUSTAND\_AUSGABE\_FARBE\_SPEICHERPLATZ\_DATEN RGB\_Feld Bereich auf 1 festgelegt ist

    -   D3D11\_1DDI\_VIDEO\_PROZESSOR\_FARBE\_SPEICHERPLATZ RGB\_Feld Bereich auf 1 festgelegt.

-   BT. 601 und BT. 709 Konvertierung Matrizen müssen unterstützt werden, auf die Eingabe und Ausgabe YCbCr Daten, insbesondere:

-   DXVAHDDDI\_STREAM\_ZUSTAND\_EINGABE\_FARBE\_SPEICHERPLATZ\_DATEN. YCbCr\_Matrix

    -   Beide Feld auf 0 (null) (BT.601) und 1 (für BT.709) festlegen, muss unterstützt werden.

-   DXVAHDDDI\_BLT\_ZUSTAND\_AUSGABE\_FARBE\_SPEICHERPLATZ\_DATEN. YCbCr\_Matrix

    -   Beide festlegen Feld auf 0 (null) (BT.601) und 1 (für BT.709) muss unterstützt werden.

-   D3D11\_1DDI\_VIDEO\_PROZESSOR\_FARBE\_SPEICHERPLATZ. YCbCr\_Matrix

    -   Beide Feld auf 0 (null) (BT.601) und 1 (für BT.709) festlegen, muss unterstützt werden.

-   Beliebige Hintergrundfarbe

-   Rechteck-stream

-   Pro-Stream Zielrechteck

-   Allgemeine Zielrechteck

-   Mindestens ein Stream-Objekt

Für die Eingabe müssen die folgenden Formate unterstützt werden:

-   D3DFMT\_420\_UNDURCHSICHTIG
-   D3DFMT\_NV12
-   D3DFMT\_YUY2
-   Alle Dateiformate, die als Ausgabe von DXVA 2.0 unterstützt decodieren oder DirectX 11 Video decodieren

Je nach der Funktion Ebene zur Verfügung gestellt vom Treiber für Direct3D (z. B. 9.1-9.3 für Direct3D 9 DDIs, 10.0 für Direct3D 10 DDIs usw.), müssen die folgenden Formate für die Ausgabe unterstützt werden:

-   9.1 9.3 Feature Ebenen

    -   D3DFMT\_A8R8G8B8
    -   D3DFMT\_NV12

-   10.0 10.1 Feature Ebenen

    -   DXGI\_FORMAT\_R16G16B16A16\_FLOAT
    -   DXGI\_FORMAT\_R8G8B8A8\_UNORM
    -   DXGI\_FORMAT\_R10G10B10A2\_UNORM
    -   DXGI\_FORMAT\_R8G8B8A8\_UNORM\_SRGB
    -   DXGI\_FORMAT\_NV12

    -   Die folgenden Formate sind auch erforderlich, wenn der Treiber diese als ein Swapchain Format unterstützt:

        -   DXGI\_FORMAT\_B8G8R8A8\_UNORM
        -   DXGI\_FORMAT\_B8G8R8A8\_UNORM\_SRGB
        -   DXGI\_FORMAT\_R10G10B10\_XR\_BIAS\_A2\_UNORM

-   11.0 feature Ebene und höher

    -   DXGI\_FORMAT\_R16G16B16A16\_FLOAT
    -   DXGI\_FORMAT\_R8G8B8A8\_UNORM
    -   DXGI\_FORMAT\_R10G10B10A2\_UNORM
    -   DXGI\_FORMAT\_R8G8B8A8\_UNORM\_SRGB
    -   DXGI\_FORMAT\_NV12, DXGI\_FORMAT\_B8G8R8A8\_UNORM
    -   DXGI\_FORMAT\_B8G8R8A8\_UNORM\_SRGB
    -   DXGI\_FORMAT\_R10G10B10\_XR\_BIAS\_A2\_UNORM

**Hinweise zum Entwurf**

MPEG-2-Unterstützung ist auf X86 und X64 Architekturen und nur Betriebssysteme erforderlich.

### <a name="devicegraphicswddm12renderdirectflip"></a>Device.Graphics.WDDM12.Render.DirectFlip

*Ein Treiber muss die DirectFlip DDI unterstützen.*

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

Der Treiber muss das Feld SupportDirectFlip veröffentlichen, als TRUE in der DXGK\_DRIVERCAPS Struktur.
WDDM 1.2 Treiber für die Direct3D 11 DDI müssen die D3D11 implementieren\_1DDI\_CHECKDIRECTFLIPSUPPORT DDI und return TRUE aus der DDI, wenn sie mit mindestens die folgenden Parameter aufgerufen wird:

-   Die app-Ressource entspricht die DWM-Ressource im Format und Pixel Dimensionen.

-   Die D3DDDI\_CHECKDIRECTFLIP\_SOFORTIGE Flag nicht festgelegt ist.

WDDM 1.2 Treiber für die Direct3D 9 DDI müssen die D3DDDIARG implementieren\_CHECKDIRECTFLIPSUPPORT DDI und return TRUE aus der DDI, wenn sie mit mindestens die folgenden Parameter aufgerufen wird:

-   Die app-Ressource entspricht die DWM-Ressource im Format und Pixel Dimensionen.

-   Die D3DDDI\_CHECKDIRECTFLIP\_SOFORTIGE Flag nicht festgelegt ist.

Der Treiber muss das Erstellen von freigegebenen primären Swapchains, speziell als mit erstellten Ressourcen identifiziert unterstützen:

-   pPrimaryDesc als ungleich NULL.

-   D3D10\_DDI\_RESSOURCE\_MISC\_SHARED im MiscFlags festgelegt.

-   D3D10\_DDI\_BINDEN\_SHADER\_RESSOURCE, D3D10\_DDI\_BINDEN\_VORHANDEN und D3D10\_DDI\_BINDEN\_RENDERN\_ZIEL in BindFlags festgelegt.

Wenn das SharedPrimaryTransition-Bit festgelegt ist, in der DXGK\_SETVIDVIDPNSOURCEADDRESS DDI, der Treiber muss:

-   Überprüfen Sie, dass die Hardware nahtlos zwischen den beiden Verfahren einsetzen kann.

-   Führen Sie einen nahtlosen Schalter, mit dem die neue primäre durch die DDI angegeben.

### <a name="devicegraphicswddm12renderfliponvsyncmmio"></a>Device.Graphics.WDDM12.Render.FlipOnVSyncMmIo

*WDDM1.2 Treiber müssen einer zugeordneten Speichers MMIO e/a-basierte kippen unterstützt, die auf die nächste vertikale Synchronisierung wirksam wird.*

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

Alle WDDM1.2 Treiber müssen Feld FlipOnVSyncMmIo als TRUE in der DXGK veröffentlichen\_FLIPCAPS Struktur, und Implementieren des Verhaltens unter FlipOnVSyncMmIo hier beschriebenen: <http://msdn.microsoft.com/en-us/library/ff561069.aspx>.
 

### <a name="devicegraphicswddm12renderofferreclaim"></a>Device.Graphics.WDDM12.Render.OfferReclaim

*WDDM 1.2 Treiber müssen das Angebot und freigeben DDI zur Reduzierung der Arbeitsspeicherbedarf verwenden.*

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

WDDM 1.2 Treiber müssen der neuen UMD bieten und DDI freizugeben verwenden, um den Aufwand für temporäre Flächen im lokalen Speicher für Video und System erstellt Speicherressourcen zu reduzieren.  Ein Beispiel ist die Verwendung der Stagingdatenbank Puffer den Prozess der Hochladen von Daten in den lokalen Speicher GPU zu beschleunigen.  Durch das Angebot diese Ressourcen, kann das Betriebssystem den Arbeitsspeicher wiederverwenden, ohne die Ausgaben für löschen und Neuerstellen von mit großer Häufigkeit riskieren.
WDDM-Treiber behalten auch oft Zuweisungen, die eine Anwendung nicht mehr verwendet wird, damit die Anwendung mit den gleichen Eigenschaften eine andere Zuordnung erstellt, es wieder der alte Datenbankserver zuweisen kann.  Dadurch wird der Leistung durch schnelle löschen und Neuerstellen von Zuweisungen ein allgemeines fehlerhafte Verhalten for Applications, jedoch kann auch ein sehr hohe Memory Kosten haben.  Diese Zuweisungen anbieten, kann der 1.2 WDDM-Treiber Großteil der Leistung beibehalten, ohne unnötig Arbeitsspeicher.
Unten finden Sie ausführliche untergeordneten Anforderungen:

-   WDDM 1.2 Treiber müssen immer "internen Puffer staging bieten" nach verwendet wurden. Diese temporären Puffer halten im allgemeinen Daten verschoben oder von einer Quelle zu einem Ziel kopiert wird. In Windows 7 und frühere Betriebssysteme diese temporären Flächen im Arbeitsspeicher verbleiben, obwohl sie nicht mehr verwendet wurden.

-   WDDM 1.2 Treiber müssen immer "die verzögerte Löschvorgänge Flächen, die wiederverwendet werden anbieten". Wenn ein Treiber beschließt, das Löschen einer Fläche verzögern, muss es mindestens an dem Manager Videospeicher anbieten.

-   WDDM 1.2 Treiber sollten nur gepackte Zuweisungen anbieten, wenn alle die einzelnen Ressourcen in der Zuweisung Angebot Ed wurden. Die Zuordnung als Ganzes sollte freigegeben werden, wenn eine beliebige einzelnen Ressourcen freigegeben wurden.

-   WDDM 1.2 Treiber müssen immer Angebot Zuweisungen verworfen, wenn sie einen eigenen umbenennen Mechanismus implementiert.

-   WDDM 1.2 Treiber sollte niemals pack Zuweisungen größer als 64 KB mit anderen Zuweisungen, Gewährleistung für Anwendung ihnen diese Angebot den erwarteten Vorteil erteilen.

Weitere Informationen zur Verwendung der Version 1.2 Angebot und WDDM freizugeben DDI finden Sie in der Dokumentation zu Windows WDK.

### <a name="devicegraphicswddm12renderpreemptiongranularity"></a>Device.Graphics.WDDM12.Render.PreemptionGranularity

*WDDM 1.2 Treiber müssen die Granularität Ebene der GPU Unterbrechung melden.*

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

1.2 WDDM-Treiber muss die GPU Unterbrechung Granularität für die Ausführung von Grafiken und Compute-Szenarien melden.
Die WDDM 1.2 muss Folgendes ausführen:

-   Legen Sie der WDDM 1.2 Treiber zunächst das Kennzeichen "PreemptionAware" und das Kennzeichen "MultiEngineAware" in der \_DXGK\_VIDSCHCAPS Struktur über die DxgkDdiQueryAdapterInfo DDI.

-   1.2 WDDM-Treiber muss die entsprechende GPU Unterbrechung Granularität über festgelegt "D3DKMDT\_UNTERBRECHUNG\_CAPS PreemptionCaps".

Es ist nicht obligatorisch erforderlich auf die aktuelle Zugriffsebene Unterbrechung für Grafiken oder Compute. Beispielsweise wenn eine GPU einer beliebigen Ebene der Mid-DMA Puffer Grafiken Unterbrechung, wie Sie auf die Grenze Dreieck oder andere nicht unterstützt werden, es kann melden dieses Endes als D3DKMDT\_GRAFIKEN\_UNTERBRECHUNG\_DMA\_PUFFER\_GRENZE. Auf ähnliche Weise, wenn keinerlei eine feinere detailliert Unterbrechung für Compute nicht unterstützt werden, es muss melden die Cap als D3DKMDT\_BERECHNEN\_UNTERBRECHUNG\_DMA\_PUFFER\_GRENZE.

Allerdings wenn die GPU Mid DMA-Puffer oder Paket Unterbrechung nicht unterstützt, muss wählen Sie dann 1.2 WDDM-Treiber die entsprechenden Cap hat, um die Vorteile durch eine feinere detailliert GPU Unterbrechung für Grafiken und/oder Compute nutzen.

Ausführliche Informationen zur Verwendung der GPU Unterbrechung WDDM v1. 2 DDI finden Sie in der Dokumentation zu Windows WDK.

### <a name="devicegraphicswddm12renderpremiumcontentplayback"></a>Device.Graphics.WDDM12.Render.PremiumContentPlayback

*Geschützte Umgebung Signatur Anforderung für WDDM1.2 Treiber*

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

Alle WDDM 1.2 Modus Graphics-Treiber binäre erforderlich für die Premium-Wiedergabe ordnungsgemäß signiert sein muss wie vom Lizenzprogramm Windows geschützten Umgebung (PE) erforderlich. Kompatibilität mit dem PE-Lizenz-Programm ist bereits im Abschnitt 3.1 des Lizenzvertrags PVP OPM erforderlich. Jede Binärdatei in der erforderlichen Gruppe muss in einer genehmigten Stamm von Windows OS Codeintegrität für PE erkannt signiert sein, insbesondere haben einen oder beide der folgenden Charakteristika signierenden:

1.  Katalog mit Signatur mit einem allgemeinen PE VERTRAUENSWÜRDIGE-Attribut, mit einem Hash-Eintrag für jede bestimmte Datei festlegen ein Feld und den Wert der PETrusted = 1.

2.  Eingebettete Signatur mit pro Seitenhashs.

Darüber hinaus den Prozess der Ermittlung, welche Signatur jedes Modul muss standardisiert ist. Jede INF-Datei enthalten muss nun einen SignatureAttributes-Abschnitt, eindeutig identifiziert, welche Art von Signatur für die zugeordnete Treiber Binärdateien anwendbar ist. Hinzufügen von vorhandenen INF-Dateien in diesem Abschnitt wird ein sehr einfacher Vorgang.

Es folgt ein Beispiel:

```
[SignatureAttributes]
NameOfFile.dll = SignatureAttributes.PETrust
[SignatureAttributes.PETrust]
PETrust=true
```

### <a name="devicegraphicswddm12rendertdrresiliency"></a>Device.Graphics.WDDM12.Render.TDRResiliency

*WDDM 1.2 Treiber für GPUs, die pro Modul zurückgesetzt unterstützen müssen der Windows-DDI für TDR Resiliency implementieren.*

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

WDDM 1.2 Treiber für eine Unterstützung pro Modul zurückgesetzt GPU muss die TDR DDI für verbesserte Zuverlässigkeit und Flexibilität implementieren.
1.2 WDDM-Treiber muss die folgenden Schritte ausführen:

-   1.2 WDDM-Treiber muss die Anforderung WDDM 1.2 GPU Unterbrechung zu erfüllen.

-   1.2 WDDM-Treiber muss die folgenden GPU Engine DDIs implementieren:

<!-- -->

-   QueryDependentEngineGroup

-   QueryEngineStatus

-   ResetEngine

<!-- -->

-   WDDM 1.2 Treiber müssen weiterhin unterstützt das Prä-Windows 8 TDR Verhalten von Adapter geltende zurücksetzen und neu starten. Semantik der diese vorhandenen DDIs bleiben gleich wie vor Windows 8.

Ausführliche Informationen zur Verwendung der GPU Unterbrechung und TDR Verbesserungen WDDM v1. 2 DDI finden Sie in der Dokumentation zu Windows WDK.

### <a name="devicegraphicswddm12renderumdlogging"></a>Device.Graphics.WDDM12.Render.UMDLogging

*WDDM 1.2 Treiber müssen im Benutzermodus WDDM-Treiber oder UMD Protokollierung zur Unterstützung der Diagnosability implementieren.*

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

1.2 WDDM-Treiber muss die Beziehung zwischen der Direct3D-Ressourcen und Videospeicher Zuweisungen verfügbar machen, durch die Implementierung der UMD Protokollierung ETW-Schnittstellen. Im folgenden sind die spezifischen Anforderungen für die Treiber:

-   UMD muss im Aufruf CreateResource angegebene Größe für die Zuordnung melden, auch wenn die Größe der Speichermenge größer ist.

-   UMD muss das MapAllocation-Ereignis für die einzelnen seine interne Reservierung melden, und geben Sie den Zweck des diese Zuordnung.

-   UMD muss das Ereignis MapAllocation für jede umbenannte Fläche melden.

-   UMD muss für jede Fläche der MapAllocation anmelden, das sie in einer vorhandenen Oberfläche packs.

-   UMD muss für jede Fläche der MapAllocation anmelden, das derzeit im Falle einer kurzer vorhanden ist.

-   UMD muss die MapAllocation als Reaktion auf CreateResource anrufen, melden Sie sich, auch wenn kein neuer Speicher zugewiesen ist.

-   UMD muss die UnmapAllocation jedes Mal anmelden, der die interne Zuordnung gelöscht wird.

-   UMD muss melden Sie sich die UnmapAllocation jedes Mal eine Anwendung eine Zuweisung löscht, auch wenn die tatsächliche arbeitsspeicherreservierung nicht gelöscht wird.

-   UMD muss die UnmapAllocation jedes Mal anmelden eine der die umbenannten Zuweisungen geschlossen wird.

-   UMD muss die UnmapAllocation für jede Fläche anmelden, das in einer größeren Verteilung gepackt ist.

Zusätzlich zum Protokollieren von Ereignissen MapAllocation und UnmapAllocation Echtzeit, muss die Grafiktreiber alle vorhandene Zuordnungen zwischen Ressourcen und Zuweisungen an einer beliebigen Stelle in der Zeit Berichten können.

Weitere Informationen zur Verwendung der v1. UMD Protokollierung WDDM 2 DDI finden Sie in der Dokumentation zu Windows WDK.

### <a name="devicegraphicswddm12renderxpsrasterizationconformance"></a>Device.Graphics.WDDM12.Render.XPSRasterizationConformance

*WDDM 1.2 Treiber müssen XPS Rasterung unterstützen.*

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

Zur Sicherstellung einer drucken Qualität unter Windows müssen die Grafiktreiber WDDM1.2 XPS Rasterung unterstützen.

<a name="device.graphics.wddm12.renderonly"></a>
## <a name="devicegraphicswddm12renderonly"></a>Device.Graphics.WDDM12.RenderOnly

*Die optionale Featuregruppe durch 1.2 WDDM-Treiber unterstützt nur die Render implementiert bestimmte DDIs.*

### <a name="devicegraphicswddm12renderonlybase"></a>Device.Graphics.WDDM12.RenderOnly.Base

*Anforderungen für eine WDDM-Grafikkarte zur Unterstützung von Rendering-Funktionen*

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

WDDM wurde erweitert, um einen WDDM-Treiber unterstützt, der nur für das Rendering und berechnen DDIs verantwortlich ist. Ein solchen Treiber ist nicht zulässig, Anzeige Scan-Funktionen unterstützt.

Ein Treiber gilt nur Rendern WDDM-Treiber, wenn eine der folgenden zwei Bedingungen erfüllt ist:

-   Der Treiber implementiert alle für eine vollständige WDDM-Treiber erforderliche DDIs aber meldet 0 Quellen und 0 Ziele.

-   Treiber implementiert alle Render bestimmte DDIs und gibt einen null-Zeiger für alle Anzeigen bestimmter DDIs zurück. Die hierfür erforderliche DDIs werden unter bezeichnet.

**Allgemeine WDDM DDIs**

Diese Funktionen DDI sind für die allgemeine Gerät Funktionen wie Plug & Play-Unterstützung und Power. Alle WDDM-Treiber diese Funktionen erforderlich sind, und wenn nicht implementiert, der Treiber wird nicht gestartet werden von Windows. Diese DDIs sind bereits in der WDK <http://msdn.microsoft.com/en-us/library/ff554066.aspx>dokumentiert.

**Erforderlich:**

 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**Optional:**

 - DdiNotifyAcpiEvent\*

\*DdiNotifyAcpiEvent DDI-Funktion wird verwendet, um Grafiktreiber auf einige ACPI Ereignisse zu benachrichtigen. Es ist optional bei einem Gerät rendern. Auf normale WDDM Grafiken Geräten gibt diese Funktion DDI ein Flag an, dass dxgkrnl.sys um einige weiteren Aktionen ausgeführt werden wie Anzeigemodus zurücksetzen oder verbundenen Monitore Abfragen zurück.  Für das Gerät Rendering nur diese Flags werden nicht verwendet und müssen auf 0 (null) festgelegt werden.
 

**Nur DDIs Rendern**

Diese Funktionen DDI sind für das Rendering-Funktionen.

**Erforderlich:**

 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**Optional:** Wenn die Hardware Rendering Swizzling Ranger unterstützt, sollte der Treiber auch die beiden folgenden Funktionen bereitstellen:

 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

<a name="device.graphics.wddm12.standbyhibernateflags"></a>
## <a name="devicegraphicswddm12standbyhibernateflags"></a>Device.Graphics.WDDM12.StandbyHibernateFlags

*Das optionale Feature von WDDM 1.2 Treiber unterstützen die neue Fuß durch Ruhezustand Flags implementiert.*

### <a name="devicegraphicswddm12standbyhibernateflagsstandbyhibernateflags"></a>Device.Graphics.WDDM12.StandbyHibernateFlags.StandbyHibernateFlags

*WDDM v1. 2 Graphics-Treiber können optional angeben, wenn sie das Windows optimiert Standby Unterstützung oder Ruhezustand Kennzeichen.*

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

Zum Verbessern der Leistung im Ruhezustand & Wiederaufnahme für Standby und Ruhezustand, kann ein 1.2 WDDM-Treiber die neue StandbyHibernateFlags (PreservedDuringStandby, PreservedDuringHibernate und PartiallyPreservedDuringHibernate) nutzen. Um dieses Feature nutzen zu können, müssen Treiber mindestens eines der StandbyHibernateFlags festgelegt, Aufzählen Segment Funktionen. Dies gibt an, dass während der Power Statusübergang für die entsprechenden Segmente Entfernung übersprungen werden soll. Überprüfung der Aufbewahrung von Arbeitsspeicher während Power Übergang wird für alle WDDM 1.2 Treiber Einrichten einer StandbyHibernateFlag überprüft werden.

<a name="device.graphics.wddm13"></a>
## <a name="devicegraphicswddm13"></a>Device.Graphics.WDDM13

*Die Basis-Featuregruppe durch Treiber unterstützt WDDM1.3 implementiert.*

### <a name="devicegraphicswddm13base"></a>Device.Graphics.WDDM13.Base

*Grafiktreiber müssen WDDM1.3 implementieren.*

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

WDDM 1.3 ist erforderlich für alle neuen Systeme, die mit Windows 10 enthalten sind.

<html>
    <table>
        <thead>
            <tr class="header">
                <th>Featurename</th>
                <th>Zutreffend DX H/W-Klasse</th>
                <th>Vollständiger Grafiken Treiber X86/X64</th>
                <th>Nur Treiber X86/X64 Rendern</th>
                <th>Vollständige Graphics-Treiber ARM/RT</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Hybrid-Grafiken (GPU Kernel)</td>
                <td>DX11 +</td>
                <td>Wenn implementiert</td>
                <td>NV</td>
                <td>NV</td>
            </tr>
            <tr class="even">
                <td>Multiplane Überlagerungen (GPU Kernel)</td>
                <td>Alles</td>
                <td>Wenn implementiert</td>
                <td>NV</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Unterstützung für drahtlose</td>
                <td>Alles</td>
                <td>Wenn implementiert</td>
                <td>NV</td>
                <td>Wenn implementiert</td>
            </tr>
            <tr class="even">
                <td>Videowiedergabe 48 Hz</td>
                <td>Alles</td>
                <td>Obligatorisch</td>
                <td>NV</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Gemeinsam genutzte Fläche Unterstützung für Weitere Formate</td>
                <td>Alles</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Vorhanden Gemeinkosten Optimierung</td>
                <td>Alles</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Kernel-Leistung: GPU Engine-Aufzählung</td>
                <td>Alles</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Power-Management – Verbesserungen: GPU p-Unterstützung</td>
                <td>Alles</td>
                <td>Wenn implementiert</td>
                <td>Wenn implementiert</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Power-Management – Verbesserungen: P-stabil</td>
                <td>Alles</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
                <td>Obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Power-Management – Verbesserungen: GPU f-Zustand Hysterese</td>
                <td>Alles</td>
                <td>Wenn*implementiert</td>
                <td>Wenn implementiert</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Power Management – Verbesserungen: Aggressive V-Synchronisierung</td>
                <td>alle</td>
                <td>Wenn implementiert</td>
                <td>NV</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Zugriff auf die Wärmeleitpaste</td>
                <td>alle</td>
                <td>Wenn implementiert</td>
                <td>Wenn implementiert</td>
                <td>Wenn implementiert</td>
            </tr>
            <tr class="odd">
                <td>Leistungssteigerungen Rendern: D3D9 Staging Puffer</td> 
                 <td>Alle</td>
                <td>
                    <p>für DX9.x Hardware obligatorisch</p>
                    <p>Optional für DX10 +</p>
                </td>
                <td>NV</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Leistungssteigerungen Rendern: systemeigene UpdateSubResource D3D9</td>
                <td>alle</td>
                <td>
                    <p>für DX9.x Hardware obligatorisch</p>
                    <p>Optional für DX10 +</p>
                </td>
                <td>NV</td>
                <td>obligatorische</td>
            </tr>
            <tr class="odd">
                <td>Leistungssteigerungen Rendern: D3D9 Zeitstempel und Leistungsindikatoren</td> 
                 <td>Alle</td>
                <td>
                    <p>für DX9.x Hardware obligatorisch</p>
                    <p>Optional für DX10 +</p>
                </td>
                <td>NV</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Leistungssteigerungen Rendern: D3D Ressource Trim</td>
                <td>alle</td>
                <td>obligatorisch</td>
                <td>obligatorisch</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Leistungssteigerungen Rendern: Feature Ebene 9 Instancing</td>
                <td>alle</td> 
                 <td>Für DX9.x Hardware obligatorisch</td>
                <td>NV</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="even">
                <td>Leistungssteigerungen Rendern: große D3D9 erfassen Strukturen</td>
                <td>alle</td>
                <td>obligatorisch</td>
                <td>NV</td>
                <td>obligatorisch</td>
            </tr>
            <tr class="odd">
                <td>Leistungssteigerungen Rendern: Zuordnen von Standard</td>
                <td>DX11 +</td>
                <td>obligatorisch</td>
                <td>NV</td>
                <td>NV</td> 
             </tr>
            <tr class="even">
                <td>Tiled Resources</td>
                <td>DX11.1</td>
                <td>If implemented</td>
                <td>If Implemented</td>
                <td>If implemented</td>
            </tr>
            <tr class="odd">
                <td>Independent Flip</td>
                <td>All</td>
                <td>Mandatory</td>
                <td>NA</td>
                <td>Mandatory</td>
            </tr>
            <tr class="even">
                <td>D3D Modification for Tools: High Performance Timing Data</td>
                <td>All</td>
                <td>Mandatory </td>
                <td>Mandatory</td>
                <td>Mandatory</td>
            </tr>
            <tr class="odd">
                <td>Full Range YUV Support</td>
                <td>DX10+</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
            </tr>
        </tbody>
    </table>
    <p></strong>Mandatory if implementing Connected Standby</p>
    <p>Es sind keine zusätzlichen Anforderungen für die Anzeige nur Treiber. Daher ist es nicht in der Tabelle aufgerufen skalieren.</p>
    <p><strong>D3D Anforderungen:</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>DirectX-Hardware</th>
                <th>KMD Anforderungen</th>
                <th>UMD Anforderungen</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>D3D9</td>
                <td>Erforderlich: WDDM v1. 3</td>
                <td>Erforderlich: D3D9 - UMD DDI</td>
            </tr>
            <tr class="even">
                <td>D3D10</td>
                <td>Erforderlich: WDDM v1. 3</td>
                <td>
                    <p>Erforderlich: D3D9 - UMD DDI</p>
                    <p>Erforderlich: D3D10 - DDI UMD</p>
                    <p>Erforderlich: D3D11.1 - UMD DDI</p>
                </td>
            </tr>
            <tr class="odd">
                <td>D3D10.1</td>
                <td>Erforderlich: WDDM v1. 3</td>
                <td>
                    <p>Erforderlich: D3D9 - UMD DDI</p>
                    <p>Erforderlich: D3D10 - DDI UMD</p>
                    <p>Erforderlich: D3D10.1 - DDI UMD</p>
                    <p>Erforderlich: D3D11.1 - UMD DDI</p>
                </td>
            </tr>
            <tr class="even">
                <td>D3D11</td>
                <td>Erforderlich: WDDM v1. 3</td>
                <td>
                    <p>Erforderlich: D3D9 - UMD DDI</p>
                    <p>Erforderlich: D3D10 - DDI UMD</p>
                    <p>Erforderlich: D3D10.1 - DDI UMD</p>
                    <p>Erforderlich: D3D11 - UMD DDI</p>
                    <p>Erforderlich: D3D11.1 - UMD DDI</p>
                </td>
            </tr>
            <tr class="odd">
                <td>D3D11.1</td>
                <td>Erforderlich: WDDM v1. 3</td>
                <td>
                    <p>Erforderlich: D3D9 - UMD DDI</p>
                    <p>Erforderlich: D3D10 - DDI UMD</p>
                    <p>Erforderlich: D3D10.1 - DDI UMD</p>
                    <p>Erforderlich: D3D11 - UMD DDI</p>
                    <p>Erforderlich: D3D11.1 - UMD DDI</p>
                </td>
            </tr>
        </tbody>
    </table>
</html>

<a name="device.graphics.wddm13.displayrender"></a>
## <a name="devicegraphicswddm13displayrender"></a>Device.Graphics.WDDM13.DisplayRender

*Dem übergeordneten Knoten von Anforderungen, die für die Anzeige auswirken und Rendern GPU Funktion.*

### <a name="devicegraphicswddm13displayrender48hzvideoplayback"></a>Device.Graphics.WDDM13.DisplayRender.48HzVideoPlayback

*WDDM1.3 Treiber müssen 48 Hz Videowiedergabe unterstützen.*

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

Implementieren von WDDM1.3 Grafiktreiber DDIs implementiert werden müssen, die:

1.  Melden Sie, ob für das gesamte System kann problemlos 48 Hz (Schnittmenge der SOC und Systemsteuerung Anzeigefunktionen) umschalten.

2.  Ist dies der Fall ist, können Sie die Aktualisierungsrate (beispielsweise 48 Hz) auf jedem bestimmten vorhanden DDI angegeben werden.

Der Test HCK wird überprüft, dass die Aktualisierungsrate mit innerhalb einer Toleranz 0,5 % der dem angeforderten Wert, vorausgesetzt erneut den Grafiktreiber-Unterstützung für die bestimmten Aktualisierungsrate Berichte. Dies wird für die Geräte *, die das unterstützen Bericht für 48 Hz oder über die Funktionen DDI 50 Hz* über einen Test HCK überprüft die im Datenblatt IHV 48 Hz ausführlich beschrieben wird.

### <a name="devicegraphicswddm13displayrenderindependentflip"></a>Device.Graphics.WDDM13.DisplayRender.IndependentFlip

*IndependentFlip-Unterstützung*

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

Alle 1.3 WDDM-Treiber MÜSSEN IndependentFlip unterstützen. Als solche MÜSSEN alle WDDM 1.3 Laufwerke UINT FlipIndependent Elements festgelegt, auf 1 in der aktualisierten DXGK\_FLIPCAPS Struktur. Finden Sie weitere Informationen zu den aktualisierten DXGK im Dokument DDI IndependentFlip\_FLIPCAPS Struktur.

<a name="device.graphics.wddm13.displayrender.coolinginterface"></a>
## <a name="devicegraphicswddm13displayrendercoolinginterface"></a>Device.Graphics.WDDM13.DisplayRender.CoolingInterface

*Feature zur Hinweise*

### <a name="devicegraphicswddm13displayrendercoolinginterfacethermalhints"></a>Device.Graphics.WDDM13.DisplayRender.CoolingInterface.ThermalHints

*Optionale Hinweise zur Unterstützung für WDDM1.3-Treiber*

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

1.3 oder höher Grafiktreiber des WDDM müssen für das neue Feld DeviceUid in der ABFRAGE hinzugefügt überprüfen\_SCHNITTSTELLE Struktur OS durch die DxgkDdiQueryInterface übergebenen Funktion und eine gültige Schnittstelle-Funktion auf dem angegebenen Gerät OS zurückzugeben.

Wenn ACPI Firmware fügt das aktuelle Graphics-Gerät ACPI ThermalZone hinzu, der IHV Miniport muss auf der GUID der DxgkDdiQueryInterface unterstützen\_ZUR\_KÜHLUNG\_SCHNITTSTELLE für das aktuelle Graphics-Gerät.

**Überprüfung:**

ACPI.sys wird nur die Thermal Kühlung Schnittstelle ist das aktuelle Gerät in einer Zone zur Abfrage. Dxgkrnl.sys können überprüfen, dass der Miniporttreiber IHV die GUID unterstützt\_ZUR\_KÜHLUNG\_SCHNITTSTELLE wenn ACPI diese Schnittstelle abfragt. In diesem Fall erhalten WHCK im Fehlerprotokoll, dass der Miniporttreiber schlägt, den Anruf DxgkDdiQueryInterface auf GUID fehl\_ZUR\_KÜHLUNG\_-SCHNITTSTELLE und die WHCK Fail zu testen.

<a name="device.graphics.wddm13.displayrender.wirelessdisplay"></a>
## <a name="devicegraphicswddm13displayrenderwirelessdisplay"></a>Device.Graphics.WDDM13.DisplayRender.WirelessDisplay

*Die optionale Featuregruppe durch 1.3 WDDM-Treiber, die zur Unterstützung der Funktionalität Miracast implementiert.*

### <a name="devicegraphicswddm13displayrenderwirelessdisplaybasicwirelessdisplay"></a>Device.Graphics.WDDM13.DisplayRender.WirelessDisplay.BasicWirelessDisplay

*Optionale Wireless Anzeige-Unterstützung für WDDM1.3-Treiber*

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

HINWEIS: In Windows 10 wurde das Framework Wireless Anzeige erheblich geändert, sodass, dass ein Großteil der Arbeit erfolgt durch das Betriebssystem. Die Anforderungen in diesem Abschnitt gelten nicht für WDDM 2.0-Treiber. Vorhandene WDDM 1.3-Treiber können jedoch weiterhin dieser Mechanismus verwenden.

-   Dies ist eine optionale Funktion für 1.3 WDDM-Treiber.

-   Miracast WDDM-Treiber für die Benutzer-Modus muss eine separate DLL.

-   Wenn ein Treiber Miracast Anzeige unterstützt, müssen sie nur eine Miracast Ziel zusammen mit anderen unterstützten Zielen auflisten.

-   Ein Treiber muss exakt den Zieltyp Windows Bericht. Jedes Mal, wenn Windows zu einem Gerät Miracast verbindet, muss der Treiber neue Zieltyp unabhängig von der Verbindung zwischen dem Endpunkt Miracast und Anzeigegeräts verwenden.

-   Ein Treiber muss nur den Empfang von einen Monitor anzugeben, nachdem die Sitzung Miracast eingerichtet ist, die Gerätefunktionen erhalten haben, HDCP Aushandlung stattgefunden hat und der Benutzer-Modus-Treiber bereit zur Anzeige auf dem Gerät Stream ist.

-   Ein Treiber muss für jede private Kommunikation zwischen UMD und KMD der neuen DDIs verwenden. Ein Treiber muss nicht Paket Zustand abrufen.

-   Ein Treiber muss für jede private Kommunikation zwischen UMD und KMD der neuen DDIs verwenden. Ein Treiber muss nicht Paket Zustand abrufen.

-   Alle Speicherzugriff mithilfe der GPU muss über DirectX APIs reserviert werden. Ein Treiber muss nicht festzulegen oder Ausblenden von Arbeitsspeicher, für die Implementierung verwendet wird.

-   Die gesamte Hardware für die Implementierung verwendeten muss präzise Power-Verwaltung aktivieren für Windows verfügbar gemacht werden.

-   Ein Treiber muss der drahtlosen zeigt V Sync melden.

-   Ein Treiber muss veröffentlichte Windows Netzwerk-APIs von Benutzermodus verwenden und privaten Schnittstellen muss nicht mit dem NW-Treiber verwenden.

-   Jedes Mal, wenn der Empfänger einen i-Frame anfordert, muss der Treiber mit Windows mithilfe einer neuen DDI melden.

-   Wenn das Gerät Miracast Audio unterstützt, muss der Treiber einen Audio-Endpunkt, vergleichbar mit der Art der Aufzählung für HDMI/Anzeige Port auflisten. Container-ID für das Audiogerät muss übereinstimmen, der die entsprechenden Miracast Gerät angezeigt.

-   Wenn Windows die Anzeige MC auf "Monitor im Leerlauf" festgelegt wird, muss der Treiber die "power speichern im Modus" gemäß der Definition in der MC standard festgelegt. Wenn der Benutzer die Eingabe von Monitor im Leerlauf wieder hochfahren vornimmt, muss die Anzeige MC wieder in leistungsstarken gemacht werden, und der Benutzer muss verwenden, ohne dass Sie erneut eine Verbindung sein.

-   Der Benutzer Modus Miracast Treiber müssen die neue DDI zum Beenden einer Sitzung Miracast innerhalb von 3 Sekunden.

-   Ein Treiber muss mit der gleichen Auflösung-Enumeration Anforderung als andere Ziel gemäß der WHCK entsprechen.

-   Es keine Anzeige physisch ist an den Empfänger Miracast verbunden klicken Sie dann der Treiber zuzulassen muss die Verbindung hergestellt werden kann aber die Anzeige muss nicht an Windows gemeldet. Nachdem die Anzeige physisch verbunden ist, muss der Treiber es Windows melden.

-   Wenn ein Benutzer die Anzeige physisch vom Empfänger Miracast Gerät getrennt wird, muss der Treiber gemeldet werden, dass die Anzeige entfernen und Windows trennen wird.

-   WDDM-Treiber muss HDCP über Miracast unterstützen.

-   Wenn ein Gerät Empfänger HDCP nicht unterstützt werden, muss der Treiber die Verbindung hergestellt werden kann zuzulassen.

-   In der Treiber die TDR Fall sollte der Treiber entsprechend die Sitzung beenden.

<a name="device.graphics.wddm13.enhancedpowermanagement"></a>
## <a name="devicegraphicswddm13enhancedpowermanagement"></a>Device.Graphics.WDDM13.EnhancedPowerManagement

*Grafiken Kernel Power Management – Verbesserungen*

### <a name="devicegraphicswddm13enhancedpowermanagementfstate"></a>Device.Graphics.WDDM13.EnhancedPowerManagement.FState

*F-Zustand Hysterese*

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

WDDM 1.3 werden einige Power Management – Verbesserungen vorgestellt. Wenn Sie dann implementiert:

WARTEZEIT TIME-VALIDIERUNG

Für einen Übergang von einer weniger Strom F-Status zu einer höheren wird davon ausgegangen, dass der Zeitaufwand für die Durchführung den Übergang nicht mehr als 10 % über der Wartezeit für den Übergang vom Treiber gemeldet werden.

### <a name="devicegraphicswddm13enhancedpowermanagementvsync"></a>Device.Graphics.WDDM13.EnhancedPowerManagement.VSYNC

*Aggressive VSYNC*

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

WDDM 1.3 werden einige Power Management – Verbesserungen vorgestellt:

IN PHASE VSYNC

Während der Vsync aktiviert ist, müssen 98 % der Vsyncs innerhalb von 500 uns von der erwartete Wert mit keine Überschreitung eine Varianz von mehr als 1,5 ms Vsyncs sein.

<a name="device.graphics.wddm13.render"></a>
## <a name="devicegraphicswddm13render"></a>Device.Graphics.WDDM13.Render

*Die Basis Featuregruppe durch 1.3 WDDM-Treiber, die dem Rendern unterstützen implementiert bestimmte DDIs.*

### <a name="devicegraphicswddm13rendercheckddiboundaries"></a>Device.Graphics.WDDM13.Render.CheckDDIBoundaries

*Hybrid-Grafiken*

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

**Grafiktreiber sollte DDI Grenzen nicht umgangen werden.**

-   Keine Systemebene oder Runtime Ebene API Standort zulässig ist – der Treiber darf keine intercept OS System oder Common Language Runtime-Aufrufe, oder ändern Sie die Argumente übergebener OS System oder Laufzeit-APIs oder Text fließt um die Objekte aus der API Entrypoints zurückgegeben.

-   Zugreifen auf und Verwenden von internen Datenstrukturen ist nicht zulässig.

-   Keine Treiber Überlagerung ist zulässig – nur eine Benutzer-Modus-Kernel-Modus-Treiber ist zulässig, die geladen werden und die Kommunikation mit der Common Language Runtime und Kernel-Binärdateien.

### <a name="devicegraphicswddm13renderdirtyrect"></a>Device.Graphics.WDDM13.Render.DirtyRect

*Optionale DirtyRect Unterstützung für WDDM1.3-Treiber*

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

WDDM1.3 erhalten Sie die Möglichkeit zur Unterstützung von DirtyRect. Wenn DirtyRect implementiert ist, muss er in der Spezifikation folgen.

### <a name="devicegraphicswddm13rendergpunode"></a>Device.Graphics.WDDM13.Render.GPUNode

*Grafiken Kernel-Leistung*

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

Wenn WDDM1.3 implementiert wird, muss der Treiber:

-   Der Treiber muss einen gültige Enum-Wert für jedes Modul pro physischen Adapter angeben.

-   Der Treiber muss angeben, ein Modul des Typs DXGK\_ENGINE\_TYPE\_3D pro physischen Adapter.

-   Für jedes Modul muss der angegebene Enum-Wert die Anforderungen erfüllen, wie in der Tabelle Engine Definitionen der DDI angegeben.

### <a name="devicegraphicswddm13renderhighperformancetimingdata"></a>Device.Graphics.WDDM13.Render.HighPerformanceTimingData

*Timing-Grafikdaten hohe Leistung*

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

"Hohe Leistung Timing Grafikdaten" bietet einfache und sehr detaillierte Zeiterfassungsdaten für Grafiken Arbeitslasten. Diese Daten wird durch Analysetools zum Identifizieren der Leistung oder andere Grafiken in der Windows-Anwendung, Probleme im Zusammenhang mit oder Grafiken Stapeln.

Ein WDDM1.3 Treiber muss sicher, dass der Grafiken Gerätetreiber Folgendes enthält:

-   Eine hohe Auflösung GPU-Zeitgeber

    -   12,5 MHz (80ns Auflösung) oder höher.

    -   Mindestens 32 Bit Timestamp Lösung.

    -   Der Zeitstempel GPU kann für alle Module in einer GPU aufgenommen werden.

    -   Der Zeitstempel GPU kann am Ende der Pipeline GPU entnommen werden.

    -   Die Häufigkeit der GPU Timestamp kann geprüft werden.

    -   Der Zeitstempel GPU unveränderlich ist und von p-Statusübergänge nicht betroffen ist.

<!-- -->

-   Zwischen den anderen Änderungen für dieses Feature wird dadurch das Hinzufügen von zwei neuen Flags in die vorhandene DdiControlEtwLogging-Schnittstelle enthalten. Wenn diese Flags so, dass die ersten Kennzeichen Wert 1 und das zweite Flag der Wert 0 ist festgelegt werden, muss der Treiber Folgendes sicherstellen:

    -   Alle Komponenten des Moduls müssen sicherstellen, dass sie nie Uhr oder Power abgegrenzten sind, solange das Flag aktiviert bleibt und im Allgemeinen sollten Sie nur muss in jeder Status, im Leerlauf eingeben. Die Komponenten müssen aktiv sein, um sicherzustellen, dass es keine Wartezeit aufgrund von Power Übergänge hinzugefügt ist.

    -   Alle Komponenten des Moduls müssen sicherstellen, dass ihre Verarbeitung Frequenzen und funktionale Bus Bandbreiten an ihre maximale stabil Betrieb Werte sind. Zur Ereignisse erfordern P-Statusübergang unten sollten weiterhin statt, um Schaden an die Hardware zu vermeiden, jedoch P Staaten sollte definiert werden, damit diese außergewöhnliche Vorkommen werden, die in coole Lab Umgebungen normalerweise nicht sichtbar sind.

<!-- -->

-   Der Stichprobe GPU Zeitstempel kann mit zuvor ausgegebenen Grafikbefehle korreliert werden.

-   Die Generierung von Daten ist standardmäßig deaktiviert, jedoch kann ein- und ausschalten aktiviert werden, zu einem beliebigen Zeitpunkt.

-   Der Aufwand für das Erfassen von diesem Leistungsdaten ist nicht langsamer als die Verwendung der Zeitstempel Abfrage Technik, die bereits in D3D9 und D3D10 + verfügbar sind.

-   Timing-Daten können über die D3D9 auf Feature Ebene 9 Hardware, und den D3D10 Treiber auf Funktion Ebene 10 + Hardware erfasst werden.

-   Die daraus resultierenden Daten auf Grundlage Kachel zurückgestellt Rendering Hardware angezeigt wird, als wäre es auf einen sofortigen Aktualisierungsmodus Rendering-Gerät generiert wurde.

### <a name="devicegraphicswddm13renderpresentoverheadoptimization"></a>Device.Graphics.WDDM13.Render.PresentOverheadOptimization

*Vorhanden Gemeinkosten Optimierung*

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

WDDM1.3 Treiber müssen die neue DDI, Present1, auf Hardware über die D3D9 DDI Feature Ebene 9 sowie auf Features 10 + Hardware über die D3D11 DDI unterstützen. WDDM1.3 Treiber auf Hardware Feature Ebene 10 + können dieses Feature durch die D3D9 DDI optional unterstützen. Diese Unterstützung sollten jedoch durch die Unterstützung für alle anderen Optional Leistung Features (z. B. Shared Fläche unterstützen) konsistent sein.

Wenn Sie die gewünschten Leistungsmerkmale sicherstellen, dass beim Present1 verwendet wird, ist Folgendes erforderlich:

-   Als Ergebnis des Aufrufs der neuen Rendern DDI muss identisch sein, das Rendering als Ergebnis der Verwendung mehrerer traditionellen Single-Present DDI Anrufe.

-   Der Treiber muss nur den vorhanden Rückruf einmal pro Aufruf der DDI (und nicht einmal pro Ressource) aufrufen.

### <a name="devicegraphicswddm13rendersharedsurfacesupport"></a>Device.Graphics.WDDM13.Render.SharedSurfaceSupport

*Unterstützung von freigegebenen Fläche*

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

WDDM1.3 Treiber müssen diese neue Dateiformate und die Funktionen für gemeinsam genutzten Oberflächen unterstützen:

-   Treiber unterstützt neue Dateiformate auf Ebene 9 Hardware,

    -   A8\_UNORM

    -   R8\_UNORM

    -   R8G8\_UNORM

-   Treiber unterstützt gemeinsam genutzten Oberflächen in neue Dateiformate (A8\_UNORM, R8G8\_UNORM, R8\_UNORM, BC1\_\*, BC2\_\*, und BC3\_\*) mit den folgenden Funktionen auf Hardware über die D3D9 DDI Feature Ebene 9 sowie auf Hardware über die D3D11 DDI Feature 10 +. WDDM1.3 Treiber auf Hardware Feature Ebene 10 + können diese Funktion über die D3D9 DDI optional unterstützen. Allerdings sollten derartige Unterstützung durch die Unterstützung für alle anderen Optional Leistung Features (z. B. vorhanden Aufwand unterstützen) konsistent sein.

    -   Freigeben von Ressourcen;

    -   Ressourcen können verwendet werden, als Ziel zu rendern.

    -   Ressourcen können gemischt werden;

    -   Ressourcen können gefiltert werden.

    -   Ressourcen können zugegriffen werden.

### <a name="devicegraphicswddm13displayrendermultiplaneoverlaysupport"></a>Device.Graphics.WDDM13.DisplayRender.MultiplaneOverlaySupport

*Mit mehreren Ebene Überlagerung-Unterstützung*

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

Alle 1.3 WDDM-Treiber müssen mit mehreren Ebene Überlagerung Funktionen der Hardware, die von der durch die Ebene mit mehreren Überlagerung Support DDI Spezifikation definierten DDI melden. 1.3 WDDM-Treiber, die zur Unterstützung von mehreren Ebene überlagert Forderung müssen der Hardware in der folgenden Kriterien erfüllen:

1.  Hardware muss nicht überlappende Ebenen unterstützen.

    -   Einer Ebene kann beschäftigen sich mit einem Bereich des Bildschirms während einer anderen Ebene zu einer anderen, sich gegenseitig ausschließender Bereich des Bildschirms decken.

    -   Ist ein Teil des Bildschirms nicht durch eine Ebene behandelt, muss die Hardware, Schwarz für diesen Bereich überprüft. Die Hardware kann davon ausgehen, dass eine virtuelle Ebene an die unterste Z-Reihenfolge, die mit Schwarz gefüllt ist vorhanden ist.

2.  Hardware muss sich überschneidenden Ebenen unterstützen. Zwischen den Ebenen mit vorab multiplizierten Alpha mischen muss unterstützt werden. Die Hardware muss auch alpha mischen für einzelne pro Ebene aktivieren/deaktivieren können.

3.  Wenn nur eine Ausgabe aktiv ist, muss die aktive Ausgabe mit mehreren Ebene Überlagerungen unterstützen. Im Fall von Clone-Modus, in dem mehrere Ausgaben gleichzeitig aktiv sind, sollte die Hardware nicht gemeldet werden, dass es mit mehreren Ebene Überlagerungen unterstützt, es sei denn, die alle aktive Ausgaben mit mehreren Ebene Überlagerungen unterstützen.

4.  Der DWM Swapchain (Ebene 0) muss zur Interaktion mit den anderen Überlagerung Ebenen möglich.

5.  Alle Ebenen muss aktiviert und deaktiviert, einschließlich Ebene 0 (der DWM Swapchain) werden können.

6.  Alle Ebenen müssen Quell- und Ziel-Clipping, einschließlich der Ebene 0 (der DWM Swapchain) unterstützen.

7.  Verkleinern und dehnen, unabhängig von der anderen Ebenen, die aktiviert werden können, muss mindestens eine Ebene unterstützen.

8.  Ebenen, die Skalierung unterstützen müssen sowohl bilineare unterstützen filtern und besser als bilineare Filterung Qualität.

9.  Es muss mindestens eine Ebene unterstützen:

    -   601 und 709 formatiert YUV Konvertierung von RGB-Matrix für YUV.

    -   Normale Bereich YUV Luminance (16-235) und vollständig YUV Luminance-Bereichen (0 – 255).

10. In der folgenden Szenarien latching registrieren muss behandelt werden:

  -   Alle pro Ebene Attribute (Pufferadresse, clipping, Skalierung, usw.) müssen auf die vertikale Rücklaufdauer automatisch veröffentlichen. Beim Register-Block zu aktualisieren, müssen sie alle automatisch gebucht, (d. h., wenn die VSYNC tritt auf, nachdem schreiben 10 20 Register für die Ebene Überlagerung keines der Projekte wird erst nach der nächsten VSYNC, da sie alle auf dem aktuellen VSYNC gebucht ist nicht möglich).

  -   Jede Ebene kann unabhängig von den anderen Ebenen aktualisiert werden. Beispielsweise wenn die Ebene 0 Register aktualisiert wurden, bevor Sie die VSYNC und wir aktualisieren die Ebene 1 registriert, wenn die VSYNC auftritt, der Ebene 1-Updates möglicherweise warten, bis der nächste VSYNC, aber die Ebene 0 Updates auf Zeit durchgeführt werden soll.

  -   Wenn mehrere Ebenen während eines Anrufs mit einzelnen vorhanden aktualisiert werden, sollte die Updates automatisch auftreten. Beispielsweise wenn einer einzigen vorhanden aufrufen ist Ebene 0 und Aktivieren von Ebene 1, die Ebene 0 aktualisieren, Register nicht auf die VSYNC buchen sollten, wenn die Ebene 1 auch Post auf der gleichen VSYNC registriert.

11.  XSL-Transformation, sollten Skalierung und mischen (in der angegebenen Reihenfolge) wie folgt auftreten:

  -   Die Quelle Zuweisung wird entsprechend der angegebenen Rechteck abgeschnitten. Das Quellrechteck wird unbedingt innerhalb der Größe der Quelle Zuweisung begrenzt werden.

  -   Wenn angefordert Bild Horizontal kippen, und klicken Sie dann auf Bild vertikal kippen angewendet werden soll.

  -   Gemäß dem Zielrechteck Skalierung anwenden, Clipping gemäß dem Cliprechteck anwenden und die entsprechenden Filtern beim Skalieren.

  -   Verbund mit Zuweisungen in anderen Schichten. Mischen sollte von oben nach unten (oder bis hit undurchsichtig Layer) in der Z-Reihenfolge ausgeführt werden. Wenn alpha mischen angefordert werden, Hardware muss die pro-Pixel-Alpha berücksichtigt und Farbwert vorab multipliziert Alpha. Pseudocode wird unterhalb dieser Vorgang über Ziel funktioniert "Source" wiederholt von oben nach unten angegeben (((Layer\[0\] über Layer\[1\]) über Layer\[2\]) über... Layer\[n\]). Außerhalb des Zielrechtecks muss jede Ebene als transparent (0,0,0,0) behandelt werden.

> Farbe Farbe =\[0\]; Ebene 0 ist ganz oben.
>
> Ist Alpha = Farbe\[0\]. Alpha;
>
> für (ich = 1; Alpha &lt; 1 & & ich &lt; LayersToBlend; i))
>
> {
>
> Farbe += ((1-Alpha) \* Farbe\[ich\]);
>
> Alpha += ((1-Alpha) \* Farbe\[ich\]. Alpha);
>
> }
>
> Ausgabefarbe;

Es ist OK, wenn Hardware unten nach oben mischt, wie das Ergebnis der Ausgabe identisch ist. In diesem Fall sollten der folgenden Blend-Algorithmus verwendet werden:

> Farbe Farbe =\[LayersToBlend-1\]; Die meisten Layer unten
>
> Ist Alpha = Farbe\[LayersToBlend-1\]. Alpha;
>
> Wenn (LayersToBlend &gt; 1)
>
> {
>
> für (ich = LayersToBlend - 2. Alpha &lt; 1 & & ich &gt;= 0; i –)
>
> {
>
> Farbe Farbe =\[ich\] + (1 – Farbe\[ich\]. Alpha) \* Farbe;
>
> Ist Alpha = Farbe\[ich\]. Alpha + (1 – Farbe\[ich\]. Alpha) \* Alpha;
>
> }
>
> }
>
> Ausgabefarbe;

-   Schwarz muss im Bereich angezeigt werden, in denen jede der Ziel-Rechtecke alle Ebenen nicht behandelt. Hardware kann davon ausgehen, dass die meisten Layer, der die Größe des Bildschirms ist eine konzeptionelle virtuellen Schwarz unten.


### <a name="devicegraphicswddm13rendertrimsupport"></a>Device.Graphics.WDDM13.Render.TrimSupport

*Direct3D Trim*

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

Die Trim-API ist neu in die WDDM1.3 Updates, UM DDI D3D9. Grafikgeräte müssen diese API unterstützen, und der Treiber muss die folgenden Schritte aus:

-   Nachdem ein Gerät Trim aufruft, muss die Graphics-Treiber Speicherverwendung nach der anfänglichen Gerät Erstellung zu innerhalb von 5 % Verwendungsmöglichkeit zurückkehren.

-   Die Reaktionszeit des Graphics-Treiber für das Rendern der Vorgänge nach dem Aufrufen der Trim muss nach der ursprünglichen Erstellung der Direct3D-Gerät des Treibers vergleichbar sein.

-   Aufrufen der Trim muss den Zustand des Direct3D-Geräts nicht ändern – alle Renderingvorgänge sollten weiterhin normalerweise ausgewertet werden soll.

<a name="device.graphics.wddm20"></a>
## <a name="devicegraphicswddm20"></a>Device.Graphics.WDDM20

### <a name="devicegraphicswddm20corerequirement-if-implemented"></a>Device.Graphics.WDDM20.CoreRequirement (sofern implementiert)  

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

<ol style="list-style-type: decimal">
<li><p>Core.MemoryResidencyModel</p>

<p>Ein 2.0 WDDM-Treiber muss die Anforderungen mit erfüllen, die in der Spezifikation für WDDM 2.0 definiert.</p>
<p>Treiber müssen das neue Modell für die Verwaltung von vor-Ort-Speicher für WDDM 2.0 gemäß Definition in der Spezifikation für Speicher vor-Ort-Modell unterstützen.</p>
<p>Treiber müssen explizit eine oder mehrere Paging Warteschlangen für jedes Gerät D3D erstellen. Synchronisierung von Vorgängen Paging Warteschlangen muss ausgeführt werden, verwenden Klammern überwacht. Asynchrone Trim Rückrufe können auftreten, das Entfernen von Ressourcen, bis die Speicherverwendung unter den angegebenen Grenzwert liegt der UMD behandeln muss.</p>
<p>Eine Liste vor-Ort-Ressourcen im Arbeitsspeicher muss durch die UMD für jedes Gerät D3D verwaltet werden. UMD muss Trim/Flush/Wait verwenden, um Fortschritte zu machen, für den Fall, dass eine Anwendung mehr als dessen reservierter Speicher verwendet.</p>
<p>Kompatibilität mit D3D11 und früheren Versionen muss die UMD vor-Ort-basierend auf binden und lösen Vorgänge verwalten.</p>
<p>UMD Angebot verarbeiten muss, und bei der Rückgewinnung fordert anders, um der Liste vor-Ort-ordnungsgemäß zu verwalten.</p>

<table>
<thead>
<tr class="header">
<th>Featurename</th>
<th>Zutreffend DX H/W-Klasse</th>
<th>Vollständige Graphics-Treiber</th>
<th>Rendern nur Treiber</th>
<th>Anzeigen nur Treiber</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>MakeResident und entfernen</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Lock2-Unterstützung</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>Überwachte Zauns-Unterstützung</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>GPU Sync Punkt</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>Trim Callback-Unterstützung</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Angebot/bei der Rückgewinnung support</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>MakeResident und entfernen</td>
<td>Alles</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
</tbody>
</table>
</li>

<li><p>Virtueller Arbeitsspeicher:</p>

<p>2.0 WDDM-Treiber muss die Anforderungen, die in der Spezifikation für WDDM 2.0 definiert erfüllen.</p>
<p>Treiber müssen das neue Modell für die Verwaltung von vor-Ort-Speicher für WDDM 2.0 unterstützen.</p>
<p>Alle Module, die GPU virtuelle Adressierung implementieren müssen in der GPU virtueller Arbeitsspeicher DDI Spezifikation einschließlich Festlegen der entsprechenden Funktionsbits definierten Funktionen unterstützen.</p>
<p>Verweise auf alle Ressourcen müssen über ihre virtuellen Adressen und die virtuellen Adressen müssen für die Lebensdauer der Ressourcen konstant bleiben.</p>
<p>Zur Unterstützung der einzelnen GPU Adressraum pro GPU logischen Adapter pro Prozess obligatorisch ist.</p>
<p>Module, dass virtuelle Adressierung unterstützen GPUMMU unterstützen muss für die virtuelle Adressierung modellieren und darf keine keine Abhängigkeit von physischen Adressierung. Unterstützung für das IOMMU Modell der virtuellen Adressierung ist optional.</p>
<p>Treiber müssen mit mehreren Ebenen Seitentabellen unterstützen und müssen eine Mischung aus 4 KB und 64 KB Seitentabellen unterstützen.</p>
<p>Anzeige und Erfassung Flächen für integrierte GPUs müssen über das Segment Blende adressiert werden.</p>
<p>Zeigen Sie Flächen in diskrete GPUs müssen zusammenhängend aus einem Segment Arbeitsspeicher zugeordnet werden.</p>

<table>
<thead>
<tr class="header">
<th>Featurename</th>
<th>Zutreffend DX H/W-Klasse</th>
<th>Vollständige Graphics-Treiber</th>
<th>Rendern nur Treiber</th>
<th>Nur anzeigen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Virtuelle Paging-Unterstützung</td>
<td>Alles</td>
<td>Wenn VA implementiert wird</td>
<td>Wenn VA implementiert wird</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Unterstützung von Seite Tabelle mit mehreren Ebenen</td>
<td>Alles</td>
<td>Wenn VA implementiert wird</td>
<td>Wenn VA implementiert wird</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>Side-by-Side 4K/64 KB Tables-Seite</td>
<td>Alles</td>
<td>Wenn VA implementiert wird</td>
<td>Wenn VA implementiert wird</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Seite-basierte Segment Speicherverwaltung</td>
<td>Alles</td>
<td>Wenn VA implementiert wird</td>
<td>Wenn VA implementiert wird</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>Gekachelter Ressourcen</td>
<td>DX11.1 +</td>
<td>Obligatorisch</td>
<td>Obligatorisch</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Programmierbare Unterstützung der CPU-Host Blende</td>
<td>Alles</td>
<td>Falls zutreffend</td>
<td>Falls zutreffend</td>
<td>n/v</td>
</tr>
<tr class="odd">
<td>LDA-Unterstützung</td>
<td>Alles</td>
<td>Falls zutreffend</td>
<td>Falls zutreffend</td>
<td></td>
</tr>
</tbody>
</table>
</li>

<li><p><strong>Ordnen Sie Standard</strong></p>

<p>Treiber für D3D11/D3D12 in definiert alle Anforderungen erfüllt sein müssen angezeigt werden die <strong><em>D3D 11/D3D12 Spezifikationen</em></strong>.</p>
<p>Wenn eine solche Seiten von der CPU zugegriffen werden kann, müssen sie als Zurückschreiben oder Write-Kombinieren der CPU gekennzeichnet werden sein.   In der Standardeinstellung verwendeter Arbeitsspeicher CPU zugänglichen Strukturen müssen als Zurückschreiben gekennzeichnet werden, wenn CPU-lesen aktiviert ist.  Wenn die CPU-Write aktiviert ist der Speicher muss als markiert sein Write-kombinieren, außer auf Cache zusammenhängendes UMA Designs.</p>
<p>Zeichenbreite linear Anforderungen &amp; Einschränkungen lauten folgendermaßen:</p>

<ul>
<li><p>Die Basisadresse / Offset des zugeordneten Ressourcen muss mindestens 16-Byte ausgerichtet.</p></li>
<li><p>Komprimierte Renderingziele müssen möglicherweise zum Aktivieren der CPUS in Lese- / Schreibzugriff der Texel aufgelöst werden.</p></li>
</ul>

<p>Arbeitsspeicheranforderungen &amp; Einschränkungen lauten wie folgt:</p>

<ul>
<li><p>Die Basisadresse / Offset des zugeordneten Ressourcen muss mindestens 16-Byte ausgerichtet.</p></li>
<li><p>Komprimierte Renderingziele müssen möglicherweise zum Aktivieren der CPUS in Lese- / Schreibzugriff der Texel aufgelöst werden.</p></li>
<li><p>Die Struktur muss im Systemarbeitsspeicher</p></li>
<li><p>Die Struktur muss nicht umbenannt oder als Ergebnis einer Zuordnung Schattenkopien</p></li>
<li><p>Swizzle Bereiche müssen nicht verwendet werden, während die Textur zugeordnet ist</p></li>
</ul>
<ul>
<li><p>Wenn die GPU standard Swizzle unterstützt, die GPU muss unterstützen alle mehrdimensionale Vorgänge orthogonal als andere Strukturen, wie Textur, zum Kopieren von auf Rendern &amp; von Re-Swizzle zu &amp; usw..</p>
<ul>
<li><p>Elementgröße für Dateiformate blockieren komprimiert und ASTC Formate muss die Blockgröße identisch sein.</p></li>
<li><p>GPU muss aus allen Modulen, einschließlich Scan skalierten standard Swizzle unterstützen.</p></li>
<li><p>Komprimierte Renderingziele müssen möglicherweise zum Aktivieren der CPUS in Lese- / Schreibzugriff der Texel aufgelöst werden.</p></li>
</ul></li>
</ul>
<p>Standard Swizzle Daten müssen auf 4 KB und 64 KB Seitenränder ausgerichtet werden.</p>
</li>
</ol>

Unternehmensvorgabe:

WDDM 2.0 führt neuen Satz von Features und DDI Änderungen, die nächste Version von Windows optimal entwickelt.


<a name="device.graphics.wddm20.core"></a>
## <a name="devicegraphicswddm20core"></a>Device.Graphics.WDDM20.Core

*Die Basis-Featuregruppe durch Treiber unterstützt WDDM2.0 implementiert.*

### <a name="devicegraphicswddm20corebase-if-implemented"></a>Device.Graphics.WDDM20.Core.Base (sofern implementiert)

WDDM2.0

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

Grafiktreiber können optional WDDM 2.0 implementieren, wenn sie keine D3D12 unterstützen. Unterstützung von D3D12 erfordert jedoch WDDM 2.0.

Windows 10 führt einen neuen Satz von Features und DDI Änderungen, die als WDDM2.0 bezeichnet werden. Die Implementierung der WDDM2.0 ist optional, obwohl es für einen Treiber, der d3d12 unterstützt, implementieren erforderlich ist. Wenn implementiert, muss die Spezifikation WDDM2.0 folgen.

**D3D Anforderungen:**

<table>
<thead>
<tr class="header">
<th>DirectX Hardware</th>
<th>KMD-Anforderungen</th>
<th>UMD Anforderungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D3D9</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="even">
<td>D3D10</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D10 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D11.1 - UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D10.1</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D10 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D10.1 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D11.1 - UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D11</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D10 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D10.1 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D11 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D11.1 - UMD DDI</td>
</tr>
<tr class="even">
<td>D3D11.1</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D10 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D10.1 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D11 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D11.1 - UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D12</td>
<td>Erforderlich: WDDM 2.0</td>
<td>Erforderlich: D3D9 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D10 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D10.1 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D11 - UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>Erforderlich: D3D11.1 - UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>Erforderlich: D3D12 - UMD DDI</td>
</tr>
</tbody>
</table>

<a name="device.graphics.wddm20.displayrender"></a>
##Device.Graphics.WDDM20.DisplayRender

*Dem übergeordneten Knoten von Anforderungen, die für die Anzeige auswirken und Rendern GPU Funktion.*

### <a name="devicegraphicswddm20displayrenderhardwarecontentprotection"></a>Device.Graphics.WDDM20.DisplayRender.HardwareContentProtection

*Eine GPU muss hardwarebasierte Schutz von Inhalten unterstützen.*

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

Der GPU-Treiber für die nächste Version von Windows muss die Grafiken – D3D11 Content Protection DDI Spezifikationen entsprechen. 

Die GPU Treiber und Hardware müssen die Tests für Microsoft Hardware Schutz von Inhalten durch übergeben. 

Erfordert, dass eine Netzwerkschnittstelle und Zugriff auf den Schutz von Inhalten PlayReady Servern testen.

<a name="device.graphics.wddm20.display.virtualmodesupport"></a>
## <a name="devicegraphicswddm20displayvirtualmodesupport"></a>Device.Graphics.WDDM20.Display.VirtualModeSupport

### <a name="devicegraphicswddm20displayvirtualmodesupportcorerequirement-if-implemented"></a>Device.Graphics.WDDM20.Display.VirtualModeSupport.CoreRequirement (sofern implementiert)

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

**Beschreibung**:

WDDM2.0 Treiber müssen Unterstützung für virtuelle Lösung Änderungen und DWMClone, über das neue VirtualModeSupport-Element in DXGK melden\_ANZEIGE\_DRIVERCAPS\_ERWEITERUNG, indem VirtualModeSupport auf 1 festlegen, wenn das Betriebssystem auf DXGKQAITYPE DxgkDdiQueryAdapterInfo aufruft\_ANZEIGE\_DRIVERCAPS\_ERWEITERUNG. 

<a name="device.graphics.wddm21"></a>
## <a name="devicegraphicswddm21"></a>Device.Graphics.WDDM21

WDDM 2.1 ist eine optionale Versionsebene für Windows 10 eingeführt größer als 10586 basiert. Wenn ein Treiber WDDM 2.1 implementiert müssen sie alle der WDDM 2.1 Anforderungen implementieren. 2.0 WDDM-Treiber werden weiterhin auf die neuere Windows 10 Builds ausgeführt.

### <a name="devicegraphicswddm21corerequirement-if-implemented"></a>Device.Graphics.WDDM21.CoreRequirement (sofern implementiert)

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

**Beschreibung**:

2.1 WDDM-Treiber muss die Anforderungen, die in der WDDM 2.1-Spezifikation definierten erfüllen. Insbesondere sollten Treiber Folgendes (je nach Hardwarefunktionen) implementieren:

1.  Anbieten / freigeben

    2.1 WDDM-Treiber müssen unterstützen die Änderungen an das Angebot / Feature freizugeben.

2.  Video geschützten Bereich

    Hardware, die einen einzelnen Bereich VPR (Video geschützten Bereich) implementiert muss die neue verschieben Paging DDIs unterstützen, damit die VPR Defragmentierung werden kann.

3.  Große Seite PTE-Codierung

    Wenn die Hardware großen Seite PTEs unterstützt, z. B. 64KB, diese werden von WDDM 2.1 unterstützt und implementiert werden soll.

4.  Pre-Beitrag vorhanden Optimierungen

    Eine neue Rückruffunktion in WDDM 2.1 (UpdateAllocationProperties) ermöglicht für Szenarien mit Optimierungen Pre/Post vorhanden. Dieser Schritt ist optional.

### <a name="devicegraphicswddm21flipqueuelatency-if-implemented"></a>Device.Graphics.WDDM21.FlipQueueLatency (sofern implementiert)

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

**Beschreibung**:

Ein WDDM2.1 Treiber muss ein 64-Bit-PresentID-Element im DXGK unterstützen\_MULTIPLANE\_ÜBERLAGERUNG\_VSYNC\_INFO2 jeder Flip-Anforderung für eine bestimmte MPO Ebene zugewiesen. Dieser Wert wird zum Zeitpunkt der Flip-Anforderung an den Treiber übergeben, und der Treiber muss wieder den derzeit bestätigten PresentId Wert in den Rückruf VSync ISR melden.

Die Möglichkeit, mehrere kippen auf VSync Anforderung auf derselben Ebene MPO in die Warteschlange muss vom MaxQueuedMultiPlaneOverlayFlipVSync Mitglied in DXGK gesteuert werden\_DRIVERCAPS.

Für Hardware, die mehr als ein Flug kippen auf VSync Anforderung unterstützen kann, muss der Treiber MaxQueuedMultiPlaneOverlayFlipVSync auf 1 festgelegt.

Wenn das Betriebssystem eine nicht Negative MaxImmediateFlipLine übergibt (Mitglied DXGK\_MULTIPLANE\_ÜBERLAGERUNG\_PLANE3) an den und die Treiber erkennt, dass die Hardware noch nicht gestartet wurde, die nicht genügend horizontale Linie überprüft &gt;= MaxImmediateFlipLine, muss der Treiber eine sofortige kippen ausführen, für die neue Oberfläche.

In dem Fall, in dem eine konvertierte sofortige kippen einer vorherigen ausstehende kippen auf VSync überschreibt, muss der Treiber gemeldet werden, dass die sofortige Konvertierung Erfolg kippen.

Der Treiber muss GPU Uhr und Häufigkeit Werte übergeben Sie den Rückruf VSync ISR (DXGKARGCB\_BENACHRICHTIGEN\_UNTERBRECHEN\_DATEN).

