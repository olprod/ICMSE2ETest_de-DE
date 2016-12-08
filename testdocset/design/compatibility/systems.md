---
title: "Spezifikation für die Hardware für Filter für Windows 10, Version 1607"
Description: "In diesem Abschnitt der Dokumentation sind die Spezifikationen für Hardware-Kompatibilität für Windows 10, Version 1607-Systeme."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: ccba79fc717fc59d7b508f388b3b6cd71538c44c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hardware-compatibility-specification-for-systems-for-windows-10-version-1607"></a>Spezifikation für die Hardware für Systeme für Windows 10, Version 1607

Dieser Abschnitt der Dokumentation enthält Spezifikationen für die Hardwarekompatibilität für Systeme mit Windows 10, Version 1607.

 - [System.Client.BluetoothController.Base](#system-client-bluetoothcontroller-base)
 - [System.Client.BluetoothController.NonUSB](#system-client-bluetoothcontroller-nonusb)
 - [System.Client.BluetoothController.USB](#system-client-bluetoothcontroller-usb)
 - [System.Client.BrightnessControls](#system-client-brightnesscontrols)
 - [System.Client.Buttons](#system-client-buttons)
 - [System.Client.Camera](#system-client-camera)
 - [System.Client.Digitizer](#system-client-digitizer)
 - [System.Client.Digitizer.Pen](#system-client-digitizer-pen)
 - [System.Client.Digitizer.PrecisionTouchpad](#system-client-digitizer-precisiontouchpad)
 - [System.Client.Digitizer.Touch](#system-client-digitizer-touch)
 - [System.Client.Firmware.UEFI.GOP](#system-client-firmware-uefi-gop)
 - [System.Client.Graphics](#system-client-graphics)
 - [System.Client.MobileBroadBand](#system-client-mobilebroadband)
 - [System.Client.PCContainer](#system-client-pccontainer)
 - [System.Client.RadioManagement](#system-client-radiomanagement)
 - [System.Client.RadioManagement.ConnectedStandby](#system-client-radiomanagement-connectedstandby)
 - [System.Client.SystemConfiguration](#system-client-systemconfiguration)
 - [System.Client.SystemImage](#system-client-systemimage)
 - [System.Client.SystemPartition](#system-client-systempartition)
 - [System.Client.ScreenRotation](#system-client-screenrotation)
 - [System.Client.Tablet.Graphics](#system-client-tablet-graphics)
 - [System.Client.WLAN.BasicConnectivity](#system-client-wlan-basicconnectivity)
 - [System.Client.WLAN.HangDetectionAndRecovery](#system-client-wlan-hangdetectionandrecovery)
 - [System.Client.WLAN.HostedNetwork](#system-client-wlan-hostednetwork)
 - [System.Client.WLAN.WiFiDirect](#system-client-wlan-wifidirect)
 - [System.Client.WLAN.Miracast](#system-client-wlan-miracast)
 - [System.Fundamentals.DebugPort](#system-fundamentals-debugport)
 - [System.Fundamentals.DebugPort.USB](#system-fundamentals-debugport-usb)
 - [System.Fundamentals.EnergyEstimation](#system-fundamentals-energyestimation)
 - [System.Fundamentals.Firmware](#system-fundamentals-firmware)
 - [System.Fundamentals.Firmware.Boot](#system-fundamentals-firmware-boot)
 - [System.Fundamentals.Firmware.CS](#system-fundamentals-firmware-cs)
 - [System.Fundamentals.Firmware.TPR](#system-fundamentals-firmware-tpr)
 - [System.Fundamentals.Graphics](#system-fundamentals-graphics)
 - [System.Fundamentals.Graphics.DisplayRender](#system-fundamentals-graphics-displayrender)
 - [System.Fundamentals.Graphics.HybridGraphics](#system-fundamentals-graphics-hybridgraphics)
 - [System.Fundamentals.Graphics.InternalDisplay](#system-fundamentals-graphics-internaldisplay)
 - [System.Fundamentals.Graphics.MultipleDevice](#system-fundamentals-graphics-multipledevice)
 - [System.Fundamentals.Graphics.RenderOnly](#system-fundamentals-graphics-renderonly)
 - [System.Fundamentals.HAL](#system-fundamentals-hal)
 - [System.Fundamentals.Input](#system-fundamentals-input)
 - [System.Fundamentals.MarkerFile](#system-fundamentals-markerfile)
 - [System.Fundamentals.Network](#system-fundamentals-network)
 - [System.Fundamentals.NX](#system-fundamentals-nx)
 - [System.Fundamentals.PowerManagement](#system-fundamentals-powermanagement)
 - [System.Fundamentals.PowerManagement.CS](#system-fundamentals-powermanagement-cs)
 - [System.Fundamentals.PXE](#system-fundamentals-pxe)
 - [System.Fundamentals.Reliability](#system-fundamentals-reliability)
 - [System.Fundamentals.Security](#system-fundamentals-security)
 - [System.Fundamentals.ServerNano](#system-fundamentals-servernano)
 - [System.Fundamentals.SignedDrivers](#system-fundamentals-signeddrivers)
 - [System.Fundamentals.SMBIOS](#system-fundamentals-smbios)
 - [System.Fundamentals.StorageAndBoot](#system-fundamentals-storageandboot)
 - [System.Fundamentals.StorageClassMemory](#system-fundamentals-storageclassmemory)
 - [System.Fundamentals.SystemAudio](#system-fundamentals-systemaudio)
 - [System.Fundamentals.SystemPCIController](#system-fundamentals-systempcicontroller)
 - [System.Fundamentals.SystemUSB](#system-fundamentals-systemusb)
 - [System.Fundamentals.TPM20](#system-fundamentals-tpm20)
 - [System.Fundamentals.TrustedPlatformModule](#system-fundamentals-trustedplatformmodule)
 - [System.Fundamentals.USBBoot](#system-fundamentals-usbboot)
 - [System.Fundamentals.USBDevice](#system-fundamentals-usbdevice)
 - [System.Fundamentals.WatchDogTimer](#system-fundamentals-watchdogtimer)
 - [System.Server.Assurance](#system-server-assurance)
 - [System.Server.AzureStack](#system-server-azurestack)
 - [System.Server.AzureStack.Storage](#system-server-azurestack-storage)
 - [System.Server.AzureStack.Networking](#system-server-azurestack-networking)
 - [System.Server.AzureStack.Firmware](#system-server-azurestack-firmware)
 - [System.Server.AzureStack.Security](#system-server-azurestack-security)
 - [System.Server.AzureStack.Security.Base](#system-server-azurestack-security-base)
 - [System.Server.AzureStack.BMC](#system-server-azurestack-bmc)
 - [System.Server.AzureStack.BMC.Base](#system-server-azurestack-bmc-base)
 - [System.Server.Base](#system-server-base)
 - [System.Server.BMC](#system-server-bmc)
 - [System.Server.DynamicPartitioning](#system-server-dynamicpartitioning)
 - [System.Server.FaultTolerant](#system-server-faulttolerant)
 - [System.Server.Firmware.UEFI.GOP](#system-server-firmware-uefi-gop)
 - [System.Server.Firmware.VBE](#system-server-firmware-vbe)
 - [System.Server.Graphics](#system-server-graphics)
 - [System.Server.Manageability.Redfish](#system-server-manageability-redfish)
 - [System.Server.PowerManageable](#system-server-powermanageable)
 - [System.Server.RemoteFX](#system-server-remotefx)
 - [System.Server.SMBIOS](#system-server-smbios)
 - [System.Server.StorageManageability.Smapi](#system-server-storagemanageability-smapi)
 - [System.Server.StorageManageability.Smapi.BlockStorage](#system-server-storagemanageability-smapi-blockStorage)
 - [System.Server.StorageManageability.Smapi.BlockStorage.RemoteReplication](#system-server-storagemanageability-smapi-blockStorage-remotereplication)
 - [System.Server.StorageManageability.Smapi.FileStorage](#system-server-storagemanageability-smapi-filestorage)
 - [System.Server.StorageManageability.Smapi.Smi](#system-server-storagemanageability-smapi-smi)
 - [System.Server.SVVP](#system-server-svvp)
 - [System.Server.SystemStress](#system-server-systemstress)
 - [System.Server.Virtualization](#system-server-virtualization)
 - [System.Server.WHEA](#system-server-whea)
 - [System.Solutions.AzureStack](#system-solutions-azurestack)
 - [System.Solutions.StorageSpacesDirect](#system.solutions-storagespacesdirect)

## <a name="systemclientbluetoothcontrollerbase"></a>System.Client.BluetoothController.Base

*Diese Anforderungen gelten für Systeme, die generische Bluetooth-Domänencontroller verwenden.*


### <a name="systemclientbluetoothcontrollerbase4lespecification"></a>System.Client.BluetoothController.Base.4LeSpecification

*Wenn ein System einen Bluetooth-fähigen Controller enthält, muss die Anforderungen der Bluetooth-4.0-Spezifikation unterstützt werden.*

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

Der Bluetooth-aktivierte Controller muss mit den grundlegenden Rate (Brasilien) und niedriger Energie (LE) kombiniert zentrale Konfiguration Controller Teile und Host-Controller-Schnittstelle (HCI) Kernkonfiguration Anforderungen beschrieben, die in den Spezifikationen Compliance Bluetooth-Version 4.0 entsprechen.


### <a name="systemclientbluetoothcontrollerbasecs"></a>System.Client.BluetoothController.Base.CS

*Systeme, die Standbymodus verbunden mit Bluetooth-fähigen Controller unterstützen müssen im Lieferumfang von Microsoft Posteingang Bluetooth-Stapel.*

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

Systeme, die Standbymodus verbunden unterstützen, die im Lieferumfang von Bluetooth Controller aktiviert müssen im Lieferumfang von Microsoft Posteingang Bluetooth-Stapel. 


### <a name="systemclientbluetoothcontrollerbasehciextensions-if-implemented"></a>System.Client.BluetoothController.Base.HciExtensions (sofern implementiert)

*MSFT definiert HCI Extensions Unterstützung für Hardware Verschiebung der Werbung und Überwachung von RSSI.*                                                                                                                                                       

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

 Sender an, die Microsoft-OSG definierten Bluetooth HCI Extensions unterstützen müssen der Spezifikation entsprechen und die zugehörigen HLKWLK Tests übergeben. Die Details der Spezifikationen werden zu einem späteren Zeitpunkt freigegeben werden. Partner werden über Connect benachrichtigt.


### <a name="systemclientbluetoothcontrollerbaselestatecombinations"></a>System.Client.BluetoothController.Base.LEStateCombinations

*Systeme mit Bluetooth-fähigen Controller müssen einen minimalen Satz von LE Zustand Kombinationen unterstützen.*

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

Der Bluetooth-fähigen Controller muss die Spec LE Zustand Kombinationen zulassen (wie im Abschnitt zulässig \[Lautstärke 6\] Teil B, Abschnitt 1.1.1 der Bluetooth-Spezifikation Version 4.0).


### <a name="systemclientbluetoothcontrollerbaselewhitelist"></a>System.Client.BluetoothController.Base.LEWhiteList

*Systeme mit Bluetooth-fähigen Controller müssen mindestens LE Listengröße von 25 Einträgen aus der zulassen unterstützen.*

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

Der Bluetooth-fähigen Controller auf dem System muss mindestens 25 Einträge im unterstützen der Zulassungsliste für remote niedrig Energie (LE) Geräte.


### <a name="systemclientbluetoothcontrollerbasenobluetoothlefilterdriver"></a>System.Client.BluetoothController.Base.NoBluetoothLEFilterDriver

*Bluetooth LE Filtertreiber dürfen nicht auf BTHLEENUM geladen werden. SYS.*

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

Um eine einheitliche Erfahrung über Windows Store-Apps mithilfe der Bluetooth-LE (GATT) WinRT-API zu gewährleisten, müssen Filtertreiber nicht auf BTHLEENUM geladen werden. SYS.


### <a name="systemclientbluetoothcontrollerbaseonoffstatecontrollableviasoftware"></a>System.Client.BluetoothController.Base.OnOffStateControllableViaSoftware

*Bluetooth-fähigen-Controller ein-/ausschalten Zustand muss über Software gesteuert.*

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

Wenn den Sender ausschalten, unterstützt Bluetooth aktivierten Controller nach unten zu der niedrigsten genommen werden Power Zustand und keine Übertragung/Empfang erfolgt. Windows wird durch Entladen der Protokolltreiber Posteingang und ihre untergeordneten Elemente, die HCI einreichen Bluetooth-Aktivität beendet\_Befehl in der Controller, und klicken Sie dann auf den Status D3 logischen Stromversorgung, Bustreiber Herunterfahren, den Sender entsprechend zulassen festlegen des Controllers zurückzusetzen. Vollständig kann der Sender ausgeschaltet werden, wenn eine Methode Bus unterstützt den Sender wieder aktivieren verfügbar ist. Keine zusätzliche Hersteller Steuerelement Softwarekomponenten werden unterstützt.

Klicken Sie auf den Sender wieder einschalten, wird der Bluetooth-Stack für Windows das Gerät D0, sodass Bustreiber für das Gerät neu starten fortsetzen. Der Windows Bluetooth-Stack wird dann die Bluetooth-fähigen Komponenten des Controllers neu initialisieren.

Bluetooth-Radio Management wird nur für interne Bluetooth 4.0 aktiviert Controller aktiviert sein.

Der Status ein-/Ausschalten der Controller Bluetooth-fähigen wird über Software gemäß Bluetooth-Software-Sender-Schalter gesteuert. Im Status ist mindestens als die Antenne Komponente des Moduls Bluetooth-fähigen deaktivieren, sodass keine Übertragung/Empfang definiert. Es müssen keine Hardware-only Wechsel in den Stromversorgung Bluetooth-fähigen Radio steuern vorhanden sein.

Der Sender muss über dem Standbymodus ein-/ausschalten Zustand verwalten und neu starten.


### <a name="systemclientbluetoothcontrollerbasesimultaneousbredrandletraffic"></a>System.Client.BluetoothController.Base.SimultaneousBrEdrAndLeTraffic

*Bluetooth-fähigen Domänencontroller müssen gleichzeitige BR/EDR und LE Datenverkehr unterstützen.*

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

Bluetooth-fähigen Domänencontroller müssen die gleichzeitige Verwendung von grundlegenden Rate BR/Enhanced Data Rate (EDR) und wenig Energie (LE) Sender zulassen.


### <a name="systemclientbluetoothcontrollerbasewidebandspeech"></a>System.Client.BluetoothController.Base.WidebandSpeech

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Breitband Speech ermöglicht Sprachqualität high-Definition (Audio wird gemessen, mit 16 KHz, im Gegensatz zu nur 8 KHz) für Telefonie Audio auf Windows-Geräten, wenn der Benutzer über eine Bluetooth peripherer kommuniziert, die auch Breitband Sprache unterstützt.

Dies bedeutet, dass Bluetooth-Sender Breitband Speech unterstützen müssen, in der Hardware gemäß Definition durch die Bluetooth SIG [Headset Profil (HFP) 1.6-Spezifikation](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=238193) und [Core Spezifikation Addendum (CSA) 2](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=245127) in der [Version 4.1 Core](https://www.bluetooth.org/DocMan/handlers/DownloadDoc.ashx?doc_id=282159) Bluetooth-Spezifikation enthalten ist. Mindestens muss mindestens ein Bluetooth SIG definierten Breitband Speech Codec (derzeit mSBC) verwendet werden.

**Unternehmensvorgabe:**

Wir möchten, dass Benutzer die beste mögliche Audioqualität bei Verwendung von Bluetooth-Peripheriegeräte unter Windows Umgebung zu bieten. Breitband-Sprache ist ein Standard für Peripheriegeräte immer, die das Profil HFP unterstützen. Konkurrenz bereits unterstützt.


### <a name="systemclientbluetoothcontrollerbasewlanbtcoexistence"></a>System.Client.BluetoothController.Base.WLANBTCoexistence

*Windows-Systeme, WLAN- und Bluetooth unterstützen, müssen WLAN-BT Koexistenz Anforderungen erfüllen.*

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

Windows-Systemen, die WLAN- und Bluetooth unterstützen müssen WLAN-BT Koexistenz erfüllen die Anforderungen unten aufgeführten. Die Anforderung ist für alle Arten von Bus für alle WLAN-Geräte.

 - Wenn Bluetooth für neue Geräte überprüft wird, müssen Sie die Verbindung mit der WLAN-AP nicht löschen.

 - Muss gleichzeitig für WLAN- und Bluetooth-Netzwerke überprüfen können.


## <a name="systemclientbluetoothcontrollernonusb"></a>System.Client.BluetoothController.NonUSB

*Diese Anforderungen gelten für Systeme, die nicht - USB-Bluetooth-fähigen-Domänencontroller verwenden.*


### <a name="systemclientbluetoothcontrollernonusbnonusbusesmicrosoftsstack"></a>System.Client.BluetoothController.NonUSB.NonUsbUsesMicrosoftsStack

*Jeder Plattform mit nicht-USB-verbunden Bluetooth-fähigen Controller muss im Lieferumfang von Microsoft Posteingang Bluetooth-Stapel.*

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

Jeder Plattform mit nicht-USB-verbunden Bluetooth-fähigen Controller muss im Lieferumfang von *Microsoft Posteingang Bluetooth-* Stapel. 


### <a name="systemclientbluetoothcontrollernonusbscosupport"></a>System.Client.BluetoothController.NonUSB.ScoSupport

*Jede beliebige Plattform mit einem nicht-USB-verbunden Bluetooth-fähigen Domänencontroller muss einen Kanal Sideband für SCO verwenden.*

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

Jeder mit nicht-USB-Plattform verbunden Bluetooth-fähigen Controller muss Sideband Channel für SCO (beispielsweise SCO über eine Schnittstelle I2S/PCM) verwenden.


## <a name="systemclientbluetoothcontrollerusb"></a>System.Client.BluetoothController.USB

*Diese Anforderungen gelten für Systeme, die USB-Bluetooth-fähigen-Domänencontroller verwenden.*


### <a name="systemclientbluetoothcontrollerusbscodatatransportlayer"></a>System.Client.BluetoothController.USB.ScoDataTransportLayer

*Bluetooth-fähigen Hostcontroller unterstützen die SCO Daten Transportschicht wie angegeben im Bluetooth 2.1 + EDR Spezifikationen.*

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

Ein System mit einem Bluetooth-fähigen Domänencontroller muss mit der synchronen Verbindung orientierten (SCO) entsprechen-USB-Anforderungen, die in der Spezifikation des Bluetooth-System, Version 2.1 + Enhanced Data Rate (EDR), Teil A beschriebenen Abschnitt 3.5.


## <a name="systemclientbrightnesscontrols"></a>System.Client.BrightnessControls 

*Dieser Abschnitt beschreibt die Anforderungen für Systeme mit Brightness-Steuerelemente.*


### <a name="systemclientbrightnesscontrolsbacklightoptimization"></a>System.Client.BrightnessControls.BacklightOptimization

Windows Display Driver Model (*WDDM) 1.2 Treiber müssen basierendes Szenario Beleuchtung Power Optimierung zur Reduzierung der Ebene der Beleuchtung durch integrierte Bereich aktivieren.*

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

 - Wenn WDDM-Treiber basierendes Szenario Beleuchtung Power Optimierung unterstützt, müssen sie die Unterstützung angeben, durch die Implementierung der DXGK\_HELLIGKEIT\_INTERFACE2-Schnittstelle.

 - Wenn Windows das aktuelle Szenario mithilfe der Funktion DxgkDdiSetBacklightOptimization festlegt, ist WDDM-Treiber wie folgt berücksichtigt die Absicht des Szenarios erforderlich:

     - DxgkBacklightOptimizationDisable: Treiber ist erforderlich, um alle Beleuchtung Optimierung vollständig zu deaktivieren.

     - DxgkBacklightOptimizationDesktop: Treiber ist erforderlich, um die Beleuchtung Optimierung auf einer niedrigeren Gründlichkeit aktiviert werden kann. Treiber muss für Szenarien wie Foto anzeigen, Browser und Office-Dokumenten zu optimieren.

     - DxgkBacklightOptimizationDynamic: Treiber ist erforderlich, um die Beleuchtung Optimierung auf einer höheren Ebene Gründlichkeit aktiviert werden kann. Treiber muss für Szenarien wie Videowiedergabe und Spiele optimieren.

     -  DxgkBacklightOptimizationDimmed: Treiber ist erforderlich, um die Optimierung auf einer höheren Ebene Gründlichkeit Beleuchtung aktivieren. Treiber muss sicherstellen, dass die Inhalte auf dem Bildschirm angezeigt wird, aber nicht leicht lesbaren zwingend erforderlich.

 - Treiber ist zulässig, die Gründlichkeit Ebene basierend auf dem Inhalt auf dem Bildschirm dynamisch zu ändern.

 - Treiber ist erforderlich, um Windows-Anforderungen für Änderung Helligkeit Ebene (basierend auf Benutzer Eingabe- oder umgebende Lichtsensors) Beibehaltung Beleuchtung Optimierung aktiviert zu behandeln.

 - Treiber ist erforderlich, um schrittweise Übergang zwischen den Ebenen Gründlichkeit ausführen:

     - Dies ist wichtig, in dem Fall, wenn Benutzer kurz Wiedergabesteuerelemente aufruft. Zu diesem Zeitpunkt wird Windows Szenario aus DxgkBacklightOptimizationDynamic DxgkBacklightOptimizationDesktop zurückgesetzt. Der Übergang muss sich nicht auf einen Schritt jedoch muss schrittweise.<br/><br/>

 - WDDM-Treiber ist erforderlich, um genaue Informationen bereitzustellen, wenn Windows DxgkDdiGetBacklightReduction abfragt.

 - Zusätzliche Anzeige an das System anschließen muss keinen Einfluss auf die Möglichkeit, Beleuchtung Optimierung für den integrierten Bereich des Systems ausgeführt.

 

### <a name="systemclientbrightnesscontrolsbrightnesscontrolbuttons"></a>System.Client.BrightnessControls.BrightnessControlButtons

*Systeme, die physischen Helligkeit Steuerelement Funktionstasten-Einstellungen verwenden Standardereignisse ACPI und Steuerung der LCD-hintergrundbeleuchtung Helligkeit über ACPI-Methoden in der Systemfirmware zu unterstützen.*

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

Windows bietet Benutzern eine LCD-Helligkeit-Steuerelement-Benutzeroberfläche. Wenn das System Schlüssel, die für das Betriebssystem nicht sichtbar sind implementiert, müssen diese Schlüssel Advanced Configuration and Power Interface (ACPI) Methoden verwenden. Diese Schlüssel müssen die Helligkeit nicht direkt nach dem Bit 2 von Steuern der \_DOS-Methode festgelegt wurde. Dies erfordert die Implementierung der ACPI Helligkeitsmethoden in der Systemfirmware.

Die folgenden Methoden sind erforderlich:

 - \_BCL
 - \_BCM

Bit 2 von der \_DOS-Methode muss, damit die Systemfirmware automatisch die Helligkeit Ebenen ändern kann nicht deaktiviert werden.

Die folgenden Methoden sind optional:

Unterstützung für die \_BQC-Methode wird dringend empfohlen, jedoch nicht erforderlich. Systeme müssen die folgenden ACPI Benachrichtigungswerte Schlüssel zuordnen:

 - ACPI\_BENACHRICHTIGEN\_CYCLE\_HELLIGKEIT\_HOTKEY 0x85

 - ACPI\_BENACHRICHTIGEN\_INC\_HELLIGKEIT\_HOTKEY 0x86

 - ACPI\_BENACHRICHTIGEN\_Dez\_HELLIGKEIT\_HOTKEY 0x87

 - ACPI\_BENACHRICHTIGEN\_0 (null)\_HELLIGKEIT\_HOTKEY 0 x 88

 
*Hinweise zum Entwurf:*

Die \_BCL und \_BCM-Methoden in der Firmware aktivieren Sie das Betriebssystem die Helligkeitsbereich und Werte abzufragen und zu neuen Werte festgelegt. Finden Sie in der Spezifikation ACPI 3.0 für weitere Details.


### <a name="systemclientbrightnesscontrolssmoothbrightness"></a>System.Client.BrightnessControls.SmoothBrightness

*Treiber muss einen reibungslosen Übergang als Antwort auf alle Helligkeit Change Anfragen Windows unterstützen.*

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

1.  Allen Windows-Systemen, die Helligkeit-Steuerelement unterstützt werden zur Unterstützung von reibungsloses Helligkeit-Steuerelement erforderlich

2.  Alle Windows-Systeme sind Windows 101 Helligkeit Ebenen Unwichtigstes erforderlich. Helligkeit wird als % gemeldet, damit dies bedeutet, dass 0 bis 100 Level, einschließlich 0 und 100. Intern kann der Treiber genauere Steuerung des Helligkeit unterstützen.

3.  Dadurch wird sichergestellt, dass Windows die Möglichkeit, die Helligkeit des Bildschirms einwandfrei detailliert ändern verfügt. Der Helligkeitsschieberegler Benutzeroberfläche kann weniger Ebenen über den Schieberegler jedoch verfügbar machen möglicherweise ist es schwierig für den Benutzer so viele Ebenen anpassen.

4.  WDDM-Treiber ist erforderlich, um reibungslosen Helligkeit Steuerelement in der Treiber ohne je nach der eingebettete Controller (EG) für die Glättung implementieren.

5.  WDDM-Treiber ist erforderlich, um anzugeben, Unterstützung für reibungslose Helligkeit-Steuerelement mit der Funktion Bit in der DXGK definierten\_HELLIGKEIT\_INTERFACE2-Schnittstelle.

6.  WDDM-Treiber muss aktivieren/reibungslose Helligkeit Steuerelement basierend auf Status mit DxgkDdiSetBrightnessState festgelegt deaktivieren.

7.  Wenn Windows eine Änderung Helligkeit anfordert, ist Treiber schrittweise die Helligkeit Ebene über einen Zeitraum zu ändern, damit die Änderung nicht um einen Schritt ist erforderlich.

8.  Wählen Sie einen entsprechenden Steigung für den Umstieg von ist WDDM-Treiber zulässig. Der Übergang muss jedoch in weniger als 2 s abgeschlossen.

9.  WDDM-Treiber ist zulässig, die Steigung basierend auf Systemsteuerung Merkmalen, um sicherzustellen, dass Glättung Helligkeit Steuerelements ändern.

10. WDDM-Treiber ist erforderlich, um sofort reagieren auf neue Helligkeit Ebene Anfragen zu starten. Dies muss berücksichtigt werden, selbst wenn das System bereits gerade einen vorhandenen Übergang ist. Zu einem Zeitpunkt muss das System den vorhandenen Übergang auf der aktuellen Ebene beenden und starten den neuen Übergang von der aktuellen Position. Dadurch wird sichergestellt, dass bei ein Benutzer den Schieberegler manuell die Helligkeit verwendet, das Steuerelement Helligkeit weiterhin schnell und nicht gering ist.

11. WDDM-Treiber ist erforderlich, um den Vorgang fortzusetzen, dass reibungslos Brightness-Steuerelement auch unterstützt, wenn Inhalte adaptive Helligkeit Optimierung basierend aktuell in Kraft ist.

12. Wenn WDDM-Treiber Plug & Play-gestartet wird, muss er erkennen die Helligkeit Ebene angewendet, indem Sie die Firmware und reibungslos Übergang von dieser Ebene mit der Windows-Ebene.

13. Zusätzliche Anzeige an das System anschließen muss nicht die Möglichkeit, Helligkeit-Steuerelement auf die integrierte Systemsteuerung des Systems smooth beeinträchtigen.

14. Helligkeit werden als % in Windows dargestellt. Daher ist keine absolute Zuordnung zwischen Helligkeit % Ebene und physischen Helligkeit Ebene. Für Windows 8 lautet wie folgt die Anweisungen.


<table>
<thead>
<tr class="header">
<th>Prozent dargestellt wird Windows</th>
<th>Benutzeroberfläche</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0 %</td>
<td>Helligkeit der Ebene, dass der Inhalt des Bildschirms kaum für den Benutzer sichtbar ist</td>
</tr>
<tr class="even">
<td>100 %</td>
<td>Max Helligkeit von Systemsteuerung unterstützt</td>
</tr>
</tbody>
</table>



## <a name="systemclientbuttons"></a>System.Client.Buttons

<!--There is no content provided here in the original Word file.-->

### <a name="systemclientbuttonshardwarebuttons"></a>System.Client.Buttons.HardwareButtons

*Hardware-Schaltflächen sind ordnungsgemäß implementiert.*

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

Dies ist derzeit optional und wird nicht erzwungen, bis 2017.

Tasten müssen gemäß den Anweisungen auf der nächsten Seite implementiert werden: <https://msdn.microsoft.com/en-us/library/windows/hardware/dn957423(v=vs.85).aspx>

GPIO Schaltflächen müssen mit der standardisierten ACPI Standardschaltfläche-Gerät (ACPI0011) angegeben werden: <https://msdn.microsoft.com/en-us/library/windows/hardware/dn957422(v=vs.85).aspx>

In dem Fall, in dem Schaltflächen nicht über GPIO Interrupts verbunden sind, müssen Windows Schaltflächen als HID Sammlungen gemeldet werden. Deskriptoren müssen befolgen, die auf der folgenden Seite angegebenen Bericht Deskriptoren HID Schaltfläche Bericht: <https://msdn.microsoft.com/en-us/library/windows/hardware/dn457881(v=vs.85).aspx>


## <a name="systemclientcamera"></a>System.Client.Camera

<!--No content was provided here in the original Word file.-->

### <a name="systemclientcameradevice"></a>System.Client.Camera.Device

*Systeme mit integrierten Kameras müssen Kamera Gerät Anforderungen erfüllen.*

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

Jede integrierte Kamera auf einem System **Device.Streaming.Camera.Base** entsprechen, und alle zugehörigen Anforderungen. Wenn die integrierte Kamera einer USB-Kamera ist, müssen sie auch **Device.Streaming.Camera.UVC** für das System suchen Zertifikat entsprechen.

Hinweis: mit zwar auf '**Device.Streaming.Camera.Base.UsageIndicator'** Wenn ein System mehrere Kameras, und klicken Sie dann auf einem physischen Indikator verfügt (z. B. GEHALTENE) ist akzeptabel, solange es gibt an, Verwendung, wenn eine oder mehrere Kameras verwendet werden. Systeme ohne Bildschirmanzeige müssen einen physischen Indikator haben.


### <a name="systemclientcameraphysicallocation"></a>System.Client.Camera.PhysicalLocation

*Systeme mit integrierten Kameras müssen den physischen Standort der einzelnen Kameras melden.*

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

Die Firmware muss angeben, für alle Kamera-Geräte, die in den Rahmen des Systems basiert und mechanische Richtung fest, die \_PLD-Methode, und legen Sie das Feld Bereich (Bits \[69:67\]) auf den entsprechenden Wert für den Bereich, auf dem die Kamera bereitgestellt wird. "Vordergrund" gibt beispielsweise an, dass die Kamera während "zurück" gibt an, dass die Kamera entfernt vom Endbenutzer zeigt den Benutzer, weist.

Darüber hinaus bit 143:128 (vertikalen Offset) und Bits 159:144 (horizontalen Offset) müssen die relative Position der Kamera im Hinblick auf die Anzeige angeben. Diese Origin ist relativ zu der systemeigenen Pixeladressierung in der Komponente angezeigt. Stammt aus der unteren linken Ecke der Anzeige, in denen besitzen positive horizontalen und vertikalen Offset-Werte nach rechts und oben, jeweils. Weitere Informationen finden Sie unter der ACPI Version 5.0 Abschnitt 6.1.8 "Gerätekonfiguration \_PLD (physischen Gerät Standort)."

Ausrichtung Kamera im Hinblick auf die Standardeinstellung System die Ausrichtung der Anzeige (auch bekannt als systemeigene System Anzeige Ausrichtung) muss angegeben werden, dem \_PLD Drehung dar (Bits 115 118). Wenn die Pixel aus der Kamera Sensor abgelesen kann ordnungsgemäß angezeigt werden ohne Drehung, und klicken Sie dann auf des Kamera Sensors \_PLD Drehungswert auf 0 festgelegt werden. Wenn die Kamera Sensor abgelesen Pixel müssen gedreht um 90 Grad im Uhrzeigersinn, um ordnungsgemäß angezeigt werden, und klicken Sie dann des Kamera Sensors \_PLD Drehungswert usw. auf 2 festgelegt werden.

Alle Felder in der \_PLD sind optional.


### <a name="systemclientcameravideocaptureandcameracontrols"></a>System.Client.Camera.VideoCaptureAndCameraControls

*Systeme mit integrierten Kameras erfüllen und die Windows-Infrastruktur erfassen unterstützen.*

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

*Arbeitsspeicher:*

Systemspeichers muss unterstützt werden.

*Unabhängige Streaming:*

Alle integrierten Kameras müssen unterstützen unabhängigen streaming zwischen unterschiedlichen Pins und verschiedene Filter (Kameras) gemäß der Funktionen, die in die vom Gerät angekündigt Profile aufgelistet. Wenn die Kamera Profile nicht unterstützt werden, ist dann gleichzeitiger streaming für *Alle* System Kameras optional.

*Spiegelung:*

Der Standardzustand für die Spiegelung muss "nicht gespiegelt werden."

*Kamera-Steuerelemente (*Wenn implementiert) *:*

Jeder der folgenden Kamera-Steuerelemente sind optional.

 - Interessenbereich (ROI)

 - Fokus

 - Belichtung

 - Weißabgleich

 - Zoomen

 - Kamera-Flash

 - Szene Modus

 - Optimierung Hinweise

 - Optische Bild Stabilisierung

 - Hintergrund

 - Brightness

 - Contrast

 - Belichtung Korrektur

 - Farbton

 - PAN

 - Kippen

 - Blogroll (engl.)

 - Video Stabilisierung

 - Variable Framerate

 - Das Standardsymbol zurück Erkennung

 - Video HDR

 - Histogramm

 - Erweiterte Foto

Wenn ein beliebiges einzelnes Steuerelement in der Kameratreiber implementiert wird, muss die Steuerelementspezifikation in das WDK entsprechen.

*Foto-Sequenz (*Falls implementiert) *:*

Foto Sequenz erfasst eine Sequenz von Fotos als Antwort auf ein einzelnes Foto klicken. Capture-Pipeline würde Puffer an der Kameratreiber ständig zum Erfassen von Fotos nacheinander senden. In diesem Modus können auch Erfassen von Fotos von dem Zeitpunkt vor dem "Benutzer klicken Sie dann auf" wodurch Benutzer nicht für einen Moment gehen verloren.

Wenn Kamera ww Foto Sequenz unterstützt, müssen sie verfügbar machen diese Funktion über die Photo Mode-Eigenschaft und die leistungsanforderungen entsprechen.

Foto Sequenz muss vom Gerät und Treiber aktiviert sein:

 - Die gleichen Lösungen, die verfügbar gemacht werden im normalen Modus unterstützt

 - Melden Sie anhand von der aktuellen light Bedingungen die aktuellen Frame Sätze im Foto Sequenz Modus möglich. Gerät muss berücksichtigt und nicht mehr als die maximale Framerate durch die Anwendung festgelegt.

 - Unterstützung mit mindestens 4fps gemessen am kleiner als der maximale Auflösung von der Bild-Pin oder 8MP verfügbar gemacht werden.

 - Bereitstellen von mindestens 4 Frames in der Vergangenheit an kleiner als der maximale Auflösung von der Bild-Pin oder 8MP verfügbar gemacht werden.

 - Foto Sequenz sollte Preview ausgeführten unabhängig voneinander, unabhängig davon, on/off.

 - Frames ständig im Foto Sequenz Mode auf bieten kleiner als der maximale Auflösung von der Bild-Pin oder 8MP verfügbar gemacht werden.

 - Wenn der Treiber JPEG-Format für Foto Sequenz gibt müssen auch Miniaturansichten, auf Anfrage, bei 1/2 X, 1/4 X, 1/8 X und 1/16 X Anteil der Breite und Höhe des ursprünglichen Auflösung unterstützt werden.

 - Das von der Kamera generierte JPEG-Bild kann optional EXIF-Metadaten, die angibt, der Informationen "Flash ausgelöst" verfügen. EXIF-Informationen umfassen personenbezogene Informationen wie Position eindeutigen Ids, u. a. nicht.

*Variable Foto-Sequenz (*Falls implementiert) *:*

Variable Foto Sequenz zeichnet eine begrenzte Anzahl von Bildern und unterstützt die Möglichkeit, die Capture Parameter für jeden der erfasste Bilder variieren. In Kamera-Treiber implementiert sollte der Treiber die angeforderte Anzahl von Bildern in der Reihenfolge, jeweils mit unterschiedlichen Capture-Parameter, wie von der Anwendung angewiesen zurückgeben sein. Der Treiber wird möglicherweise im Voraus programmiert werden der Anzahl der Frames benötigt und unabhängige Capture-Parameter für jeden Frame festlegen, bevor Capture initiiert wird.

Es wird empfohlen, dass die Variable Foto Sequenz die Anwendung die folgenden Parameter für jeden Frame angeben kann, aber mindestens eine der folgenden implementiert werden muss, wenn VPS unterstützt wird:

 - Belichtung

 - ISO

 - Belichtung Korrektur in EV

 - Fokus position

 - Flash

Wenn ein der Parameter nicht festgelegt ist folgt in pro Frame Einstellungen der Treiber die globalen Einstellungen und 3A sperren. Beispielsweise wenn EV Belichtungsreihe verwendet wird, der Treiber sorgen dafür, dass Belichtung weiterführende Parameter wie Gewinn- und Belichtung entsprechend der EV Belichtungsreihe Einstellungen festgelegt werden.  Der Treiber variieren automatische Weißabgleich Einstellungen für Bild frames, es sei denn, die pro Frame Einstellungen verwenden Sie manuelle Weißabgleich Einstellungen oder im Falle der Anwendung verwendet Weißabgleich sperren. Nicht empfohlen, Lens Position (es sei denn, die von der Anwendung manuell angegeben) automatisch zwischen den Frames VPS geändert wird.


## <a name="systemclientdigitizer"></a>System.Client.Digitizer

<!--No content was provided here in the original Word file.-->

### <a name="systemclientdigitizerbasesystemdigitizerbase"></a>System.Client.Digitizer.Base.SystemDigitizerBase

*System Digitizer Base*

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

Die folgenden Digitizer Base Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Lesen Sie die folgenden **Device.Input.Digitizer.Base** -Anforderungen für vollständige Anforderung Details:

 - Device.Input.Digitizer.Base.ContactReports
 - Device.Input.Digitizer.Base.HIDCompliant
 - Device.Input.Digitizer.Base.ThirdPartyDrivers


### <a name="systemclientdigitizersystempen"></a>System.Client.Digitizer.SystemPen

*System Stift*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden Anforderungen **Device.Input.Digitizer.Pen** ausführliche vollständige Anforderung:

 - Device.Input.Digitizer.Pen.Accuracy
 - Device.Input.Digitizer.Pen.Buffering
 - Device.Input.Digitizer.Pen.CustomGestures
 - Device.Input.Digitizer.Pen.Eraser
 - Device.Input.Digitizer.Pen.HoverRange
 - Device.Input.Digitizer.Pen.Jitter
 - Device.Input.Digitizer.Pen.Latency
 - Device.Input.Digitizer.Pen.Pressure
 - Device.Input.Digitizer.Pen.ReportRate
 - Device.Input.Digitizer.Pen.Resolution


### <a name="systemclientdigitizersystemtouch"></a>System.Client.Digitizer.SystemTouch

*System-Touch*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Lesen Sie die folgenden **Device.Input.Digitizer.Touch** -Anforderungen für vollständige Anforderung Details:

 - Device.Input.Digitizer.Touch.Accuracy
 - Device.Input.Digitizer.Touch.Buffering
 - Device.Input.Digitizer.Touch.CustomGestures
 - Device.Input.Digitizer.Touch.FingerSeparation
 - Device.Input.Digitizer.Touch.Jitter
 - Device.Input.Digitizer.Touch.Latency
 - Device.Input.Digitizer.Touch.MinContactCount
 - Device.Input.Digitizer.Touch.ReportRate
 - Device.Input.Digitizer.Touch.Resolution

Microsoft empfiehlt, melden können 5 oder mehr gleichzeitige Kontaktpunkte Touch-Lösungen.  Dadurch wird sichergestellt, dass die Plattform mit Drittanbieter Applications kompatibel ist, die nach Fingereingabe abhängig sind und Endbenutzer können alle von Windows bereitgestellten System Gesten aufrufen.

Microsoft ist bekannt, dass extenuating Umständen vorhanden, bei denen eine erweiterte Gestik wünschen nicht erforderlich ist.  Um diese sehr begrenzten Satz von Systemen zu unterstützen, stellen wir die folgenden Zertifikate:

Systeme, die verkauft werden, wie erstellen, um benutzerdefinierte Enterprise-Bildern konfigurieren oder sich für spezifischen Enterprise vertikalen Märkten eignen, haben die Möglichkeit, einem Touchscreen melden können nur eine einzige Anlaufstelle liefern.  Beispiele sind Systeme für das Gesundheitswesen Militär Applications und der Verkauf Punkt.

Für alle Systeme, die Unterstützung für mehr als eine einzelne Anlaufstelle werden alle Gesten System als generische Maus Verhalten aufrufen möglich. 

Ein System abhängig, Tastatur und Maus als die primäre input Modalität, ohne die Möglichkeit zum Umwandeln in einen Modus Tablet-Gerät können eine unterstützt mindestens 2 gleichzeitige Kontaktpunkte Touch-Lösung zu integrieren.  Beispiele für: externe anzeigt, All-In-One-desktop-Systeme. 

Für alle Systeme, die Unterstützung für mehr als 2 gleichzeitige Kontaktpunkte wird 4 Finger Eingabehilfen Gesten Aufrufen möglich.
Alle anderen Systemen müssen mindestens 5 gleichzeitige Kontaktpunkte unterstützen.


### <a name="systemclientdigitizersystemprecisiontouchpad"></a>System.Client.Digitizer.SystemPrecisionTouchpad

*Precision Touchpad*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Lesen Sie die folgenden **Device.Input.Digitizer.PrecisionTouchpad** -Anforderungen für vollständige Anforderung Details:

 - Device.Input.Digitizer.PrecisionTouchpad.Accuracy
 - Device.Input.Digitizer.PrecisionTouchpad.Buffering
 - Device.Input.Digitizer.PrecisionTouchpad.Buttons
 - Device.Input.Digitizer.PrecisionTouchpad.ContactTipSwitchHeight
 - Device.Input.Digitizer.PrecisionTouchpad.DeviceTypeReporting
 - Device.Input.Digitizer.PrecisionTouchpad.Dimensions
 - Device.Input.Digitizer.PrecisionTouchpad.FingerSeparation
 - Device.Input.Digitizer.PrecisionTouchpad.Jitter
 - Device.Input.Digitizer.PrecisionTouchpad.Latency
 - Device.Input.Digitizer.PrecisionTouchpad.MinMaxContacts
 - Device.Input.PrecisionTouchpad.Precision.InputResolution
 - Device.Input.Digitizer.PrecisionTouchpad.SelectiveReporting
 
Ein Touchpad kann nicht vermarktet werden, wie ein Touchpad Genauigkeit, wenn das Gerät ein 3<sup>rd</sup> -Treibers eines Drittanbieters muss installiert sein, um als eine Genauigkeit Touchpad melden.


## <a name="systemclientdigitizerpen"></a>System.Client.Digitizer.Pen

<!--No content was provided here in the original Word file.-->

### <a name="systemclientdigitizerpenaccuracy"></a>System.Client.Digitizer.Pen.Accuracy

*System Stift Kontakt Genauigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Accuracy** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenbuffering"></a>System.Client.Digitizer.Pen.Buffering

*System Stift Pufferung für Bus mit hoher Resume-Wartezeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Buffering** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpencontactreports"></a>System.Client.Digitizer.Pen.ContactReports

*Um die Systemstabilität Stift Digitizer*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.ContactReports** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpencustomgestures"></a>System.Client.Digitizer.Pen.CustomGestures

*System Stift benutzerdefinierten Laufzeitfehler System Gesten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.CustomGestures** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpeneraser"></a>System.Client.Digitizer.Pen.Eraser

*System Stift Radierer Aufforderungscharakter*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Eraser** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenhidcompliant"></a>System.Client.Digitizer.Pen.HIDCompliant

*System Stift HID-kompatible Gerätefirmware und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.HIDCompliant** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenhoverrange"></a>System.Client.Digitizer.Pen.HoverRange

*System Stift beim Daraufzeigen Bereich*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.HoverRange** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenjitter"></a>System.Client.Digitizer.Pen.Jitter

*System Stift Jitter und Linearität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Jitter** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenlatency"></a>System.Client.Digitizer.Pen.Latency

*System Stift Antwort Wartezeiten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Latency** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenpressure"></a>System.Client.Digitizer.Pen.Pressure

*System Stift Druck Reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Pressure** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenreportrate"></a>System.Client.Digitizer.Pen.ReportRate

*System Stift Bericht Rate*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.ReportRate** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenresolution"></a>System.Client.Digitizer.Pen.Resolution

*System Stift Input-Lösung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.Resolution** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerpenthirdpartydrivers"></a>System.Client.Digitizer.Pen.ThirdPartyDrivers

*System Stift Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Stift Gerät Level-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.Pen.ThirdPartyDrivers** ausführliche vollständige Anforderung.


## <a name="systemclientdigitizerprecisiontouchpad"></a>System.Client.Digitizer.PrecisionTouchpad

<!--No content was provided here in the original Word file.-->

### <a name="systemclientdigitizerprecisiontouchpadaccuracy"></a>System.Client.Digitizer.PrecisionTouchpad.Accuracy

*System Precision Touchpad Genauigkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Accuracy** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadbuffering"></a>System.Client.Digitizer.PrecisionTouchpad.Buffering

*System Precision Touchpad Pufferung für Bus mit hoher Resume-Wartezeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät geforderte muss erfüllt sein und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Buffering** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadbuttons"></a>System.Client.Digitizer.PrecisionTouchpad.Buttons

*System Precision Touchpad physischen Schaltflächen- und Reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Folgende Genauigkeit Touchpad Gerät Ebene Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Buttons** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadcontactreports"></a>System.Client.Digitizer.PrecisionTouchpad.ContactReports

*Um die Systemstabilität Precision Touchpad Digitizer*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Folgende Genauigkeit Touchpad Gerät Ebene Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.ContactReports** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadcontacttipswitchheight"></a>System.Client.Digitizer.PrecisionTouchpad.ContactTipSwitchHeight

*System Precision Touchpad Kontakt Tipp Switch Höhe*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Folgende Genauigkeit Touchpad Gerät Ebene Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.ContactTipSwitchHeight** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpaddevicetypereporting"></a>System.Client.Digitizer.PrecisionTouchpad.DeviceTypeReporting

*Systemtyp Precision Touchpad-Gerät*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.DeviceTypeReporting** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpaddimensions"></a>System.Client.Digitizer.PrecisionTouchpad.Dimensions

*System Precision Touchpad Dimensionen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Dimensions** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadfingerseparation"></a>System.Client.Digitizer.PrecisionTouchpad.FingerSeparation

*System Precision Touchpad Finger voneinander getrennt zu halten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.FingerSeparation** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadhidcompliant"></a>System.Client.Digitizer.PrecisionTouchpad.HIDCompliant

*System Precision Touchpad HID-kompatible Gerätefirmware und/oder HID Mini-Port-Treiber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.HIDCompliant** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadinputresolution"></a>System.Client.Digitizer.PrecisionTouchpad.InputResolution

*System Precision Touchpad Input-Lösung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Input Lösung** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadjitter"></a>System.Client.Digitizer.PrecisionTouchpad.Jitter

*System Precision Touchpad Jitter und Linearität*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Folgende Genauigkeit Touchpad Gerät Ebene Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Jitter** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadlatency"></a>System.Client.Digitizer.PrecisionTouchpad.Latency

*System Precision Touchpad Antwort Wartezeiten*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.Latency** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadminmaxcontacts"></a>System.Client.Digitizer.PrecisionTouchpad.MinMaxContacts

*System Precision Touchpad Kontakt Count*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der Anforderung **Device.Input.Digitizer.PrecisionTouchpad.MinMaxContacts** ausführliche vollständige Anforderung.


### <a name="systemclientdigitizerprecisiontouchpadreportrate"></a>System.Client.Digitizer.PrecisionTouchpad.ReportRate

*System Precision Touchpad Bericht Sätze*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der **Device.Input.Digitizer.PrecisionTouchpad.ReportRate** -Anforderungen für vollständige Anforderung Details.


### <a name="systemclientdigitizerprecisiontouchpadselectivereporting"></a>System.Client.Digitizer.PrecisionTouchpad.SelectiveReporting

*System Precision Touchpad selektive Reporting*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in der **Device.Input.Digitizer.PrecisionTouchpad.SelectiveReporting** -Anforderungen für vollständige Anforderung Details.


### <a name="systemclientdigitizerprecisiontouchpadthirdpartydrivers"></a>System.Client.Digitizer.PrecisionTouchpad.ThirdPartyDrivers

*System Precision Touchpad Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung**

Die folgenden Genauigkeit Touchpad Gerät Ebene-Anforderung muss erfüllt und bei der Integration in einem System überprüft werden. Finden Sie in den **Device.Input.Digitizer.PrecisionTouchpad.ThirdPartyDrivers** Anforderungen für vollständige Anforderung Details.


## <a name="systemclientdigitizertouch"></a>System.Client.Digitizer.Touch

<!--No content was provided here in the original Word file.-->

### <a name="systemclientdigitizertouchaccuracy"></a>System.Client.Digitizer.Touch.Accuracy

*System Touch Genauigkeit*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Näheres folgende **Device.Input.Digitizer.Touch.Accuracv** Anforderung ausführliche vollständige Anforderung.


### <a name="systemclientdigitizertouchbuffering"></a>System.Client.Digitizer.Touch.Buffering

*System Touch Pufferung für Bus mit hoher Resume-Wartezeit*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.Buffering** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchcontactreports"></a>System.Client.Digitizer.Touch.ContactReports

*Um die Systemstabilität Touch Digitizer*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Näheres folgende **Device.Input.Digitizer.Touch.ContactReports** Anforderung ausführliche vollständige Anforderung.


### <a name="systemclientdigitizertouchcustomgestures"></a>System.Client.Digitizer.Touch.CustomGestures

*System nur benutzerdefinierte Laufzeitfehler System sehr schwer umsetzbar*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.CustomGestures** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchfingerseparation"></a>System.Client.Digitizer.Touch.FingerSeparation

*System Touch Finger voneinander getrennt zu halten*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.FingerSeparation** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchhidcompliant"></a>System.Client.Digitizer.Touch.HIDCompliant

*System Touch HID-kompatible Gerätefirmware und/oder HID Mini-Port-Treiber*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.HIDCompliant** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchjitter"></a>System.Client.Digitizer.Touch.Jitter

*System Touch Jitter und Linearität*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Näheres folgende **Device.Input.Digitizer.Touch.Jitter** Anforderung ausführliche vollständige Anforderung.


### <a name="systemclientdigitizertouchlatency"></a>System.Client.Digitizer.Touch.Latency

*System Touch Antwortzeit für Anfragen*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt sein und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.Latency** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchmincontactcount"></a>System.Client.Digitizer.Touch.MinContactCount

*System Touch minimale gleichzeitige betroffenen Kontakte*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.MinContactCount** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchreportrate"></a>System.Client.Digitizer.Touch.ReportRate

*System Touch Bericht Rate*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.ReportRate** -Anforderung für vollständige Anforderung Details.


### <a name="systemclientdigitizertouchresolution"></a>System.Client.Digitizer.Touch.Resolution

*Input System Touch-Lösung*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Näheres folgende **Device.Input.Digitizer.Touch.Resolution** Anforderung ausführliche vollständige Anforderung.


### <a name="systemclientdigitizertouchthirdpartydrivers"></a>System.Client.Digitizer.Touch.ThirdPartyDrivers

*System Touch Wartung und 3<sup>rd</sup> Teilnehmern Treiber Verfügbarkeit*

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

Die folgenden Touch Gerät Ebenen Anforderungen müssen erfüllt und bei der Integration in einem System überprüft werden. Finden Sie die folgenden **Device.Input.Digitizer.Touch.ThirdPartyDrivers** -Anforderung für vollständige Anforderung Details.


## <a name="systemclientfirmwareuefigop"></a>System.Client.Firmware.UEFI.GOP

<!--No content was provided here in the original Word file.-->

### <a name="systemclientfirmwareuefigopdisplay"></a>System.Client.Firmware.UEFI.GOP.Display

*System-Firmware muss Grafiken Ausgabe Protocol (GOP) unterstützen, und zeigt Windows Anforderungen an.*

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

Gemäß Definition im UEFI 2.3.1, muss jeder Firmware auf einem Clientcomputer Windows GOP unterstützen. Die Anzeige wird vom System UEFI gesteuert, vor der Grafiktreiber WDDM übernimmt. GOP muss verfügbar sein, wenn Windows EFI Boot-Manager geladen wird.  VBIOS wird nicht unterstützt. Er ist auch erforderlich für die vorherige Benutzeroberfläche wie OEM-Logo, Firmware-Setup oder Kennwort Prompt Bildschirme GOP zu aktivieren. Während dieser Zeit, wenn die Firmware im Steuerelement ist, sind die folgenden Anforderungen.

**Auswahl der Topologie**

 - UEFI muss zuverlässig alle zeigt erkennen, die mit der POST-Adapter verbunden sind. Der Bildschirm grafikbasierten kann nur auf einem Monitor mit der POST-Adapter verbunden angezeigt werden.

 - Für den Fall, dass mehrere Monitore festgestellt werden, muss UEFI grafikbasierten Bildschirms auf der Grundlage der folgenden Logik anzeigen:

     - System mit einer integrierten Display (Laptop, alle In einem Tablet): UEFI muss der Bildschirm grafikbasierten nur auf die integrierte Anzeige.

     - System **ohne** eine integrierte Anzeige (integrierte Anzeige ist Herunterfahren oder desktop System): UEFI muss der Bildschirm grafikbasierten einen Bildschirm. UEFI muss die Anzeige von Priorisierung wird basierend auf den Verbindungstyp auswählen. Die Priorisierung ist wie folgt: DisplayPort, HDMI, DVI, HD15, Component, S-Video. Wenn mehrere Bildschirme mit dem gleichen Connectortyp verbunden sind, kann die Firmware welche davon verwenden soll.

**Die Auswahl**

 - Nachdem die Anzeige auf aktiviert, um den Bildschirm grafikbasierten UEFI ermittelt, müssen sie den Modus basierend auf der folgenden Logik anwenden auswählen.

     - System mit einer integrierten Display (Laptop, alle In einem Tablet): die Anzeige muss immer auf die systemeigene Auflösung und systemeigene Timing festgelegt werden.

     - System **ohne** eine integrierte Anzeige (Desktop):

         - UEFI muss Versuch, die systemeigene Auflösung und die zeitliche Steuerung der Anzeige durch beschaffen es aus der EDID.

         - Wenn die nicht unterstützt wird, muss UEFI einen alternativen Modus auswählen, der das gleiche Seitenverhältnis als die systemeigene Auflösung der Anzeige übereinstimmt.

         - Zumindest muss UEFI einen Modus von 1024 x 768 festlegen.

         - Wenn Anzeigegeräts ein EDID nicht bereitstellt, muss UEFI einen Modus von 1024 x 768 festlegen.

     - Firmware muss immer eine 32-Bit-linear Frame-Puffer verwenden, um den Bildschirm grafikbasierten anzuzeigen.

     - PixelsPerScanLine muss die HorizontalResolution entsprechen.

     - PixelFormat muss PixelBlueGreenRedReserved8BitPerColor sein. Beachten Sie, dass ein physikalischer Rahmenpuffer erforderlich ist. PixelBltOnly wird nicht unterstützt.  

**Modus zum Löschen des Archivs**

 - UEFI muss löschen die Liste der verfügbaren Modi nach den Vorgaben in EFI genannten\_GRAFIKEN\_AUSGABE\_PROTOKOLL. QueryMode() (gemäß der Spezifikation, Version 2.1 UEFI)

**Bereitstellen der EDID**

 - Sobald die UEFI einen Modus auf die entsprechende Anzeige (basierend auf der Auswahl der Topologie) festgelegt, UEFI erhalten die EDID der Anzeige und an den Windows übergeben, wenn Windows EFI verwendet muss\_EDID\_ERMITTELTE\_PROTOCOL (gemäß der Spezifikation, Version 2.1 UEFI) zum Abfragen von der EDID:

     - Es ist möglich, dass einige integrierte Fenster ein EDID im Bereich Anzeige selbst möglicherweise nicht.  In diesem Fall muss UEFI die EDID produzieren. Die EDID muss genau die systemeigene Timing und die physischen Dimensionen der der integrierte Systemsteuerung angeben.

     - Wenn die Anzeige nicht integriert ist, und verfügt nicht über ein EDID, klicken Sie dann muss die UEFI nicht Herstellung einer EDID.


## <a name="systemclientgraphics"></a>System.Client.Graphics

<!--No content was provided here in the original Word file.-->

### <a name="systemclientgraphicsfullgpu"></a>System.Client.Graphics.FullGPU

*Ein Windows-Client-System muss ein Grafikgerät "Full" und das Gerät muss die Post-Gerät.*

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

WDDM 1.3 stellt mehrere Treiber-Gerät: vollständige, nur Rendern und nur anzeigen. Eine detaillierte Beschreibung der einzelnen finden Sie in der WDDM 1.3 im Anforderung **Device.Graphics.WDDM13.Base**.
Jeder dieser Treiber-Gerät Typen eignen sich für bestimmte Szenarien und Nutzung Groß-/Kleinschreibung. Alle Clientszenarien erwarten ein Grafikgerät "full. Viele Clientanwendungen wird auch davon ausgegangen, dass das Gerät Post ist die "beste" Grafikgeräte dieses Gerät exklusiv verwenden. Aus diesem Grund benötigen ein Windows-Client-System eine "full" Graphics Treiber, der Anzeige, Rendering und Video kann.


### <a name="systemclientgraphicsnomorethanoneinternalmonitor"></a>System.Client.Graphics.NoMoreThanOneInternalMonitor

*Graphics-Treiber muss nicht mehr als einem Monitor als intern aufgelistet werden.*

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

Der Grafiktreiber muss nicht mehr als eine als Anzeigeziel für die D3DKMDT auflisten\_VOT\_INTERNAL Geben Sie für jeden beliebigen Adapter.
*Design Notes:* Weitere Informationen finden Sie im Handbuch der Grafiken für Windows 7 unter [http://go.microsoft.com/fwlink/?LinkId=237084](http://www.microsoft.com/whdc/device/display/graphicsguidewin7.mspx). 


### <a name="systemclientgraphicswddm"></a>System.Client.Graphics.WDDM

*Alle Windows Graphics-Treiber müssen Windows Display Driver Model (WDDM) sein.*

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

Die WDDM-Architektur bietet Funktionen zum Aktivieren von Features wie desktop Zusammensetzung, erweiterte Fehlertoleranz Fehlertoleranz, Videospeichermanager, Planer, schneidet Prozessfreigabe von D3D Flächen und so weiter. WDDM wurde speziell für Grafikgeräte modernen, die mindestens Direct3D 10 Feature Ebene 9 sind\_3 mit PixelShader 2.0 oder besser und verfügen über alle erforderlichen Hardwarefunktionen zur Unterstützung der Funktion WDDM Arbeitsspeicher Verwaltung, Planung und Fehlertoleranz.

Alle Systeme, die im Lieferumfang von Windows 10 ist WDDMv1.3 erforderlich.

Der folgenden Tabelle wird die Verwendung Szenario für die Grafiktreiber Typen erläutert:


<table>
<thead>
<tr class="header">
<th>Modus</th>
<th>Client</th>
<th>Server</th>
<th>Client Ausführung in einer virtuellen Umgebung</th>
<th>Virtuelle Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Vollständige Grafiken</td>
<td>Erforderliche Gerät buchen</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
</tr>
<tr class="even">
<td>Nur anzeigen</td>
<td>Nicht zulässig</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
</tr>
<tr class="odd">
<td>Nur rendern</td>
<td>Optional als nicht primären adapter</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
</tr>
<tr class="even">
<td>Headless</td>
<td>Nicht zulässig</td>
<td>Optional</td>
<td>n/v</td>
<td>n/v</td>
</tr>
</tbody>
</table>



### <a name="systemclientgraphicswddmsupportrotatedmodes"></a>System.Client.Graphics.WDDMSupportRotatedModes

*Wenn Beschleunigungsmesser vorhanden ist, muss Windows Display Driver Model (WDDM)-Treiber alle gedrehte Modi unterstützen.*

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

Auf einem System mit Beschleunigungsmesser ist WDDM-Treiber erforderlich, um alle gedrehte Modi für jede Lösung für den Bereich integrierte aufgezählt unterstützen:
 

 - WDDM-Treiber ist erforderlich, die Quelle Modi für die integrierte Anzeige aufgelistet werden. WDDM-Treiber muss für jede Modus gedrehte Modi (0, 90, 180 und 270) unterstützen, die sie für die integrierte Systemsteuerung aufgezählt werden.

 - Die Drehung ist erforderlich, die unterstützt werden, selbst wenn der integrierte Bereich in einer doppelten oder erweiterte Topologie mit einer anderen Anzeigegeräts ist. Doppelte Modus ist es akzeptabel, drehen alle Ziele mit der gedrehte Datenquelle verbunden. Pro Pfad ist Drehung zulässig, aber nicht erforderlich.

Sowohl die oben genannten Anforderungen sind optional in Stereo 3D fähig Lösungen.


### <a name="systemclientgraphicswirelessusbdisplay"></a>System.Client.Graphics.WirelessUSBDisplay

*System-Einschränkungen für drahtlose und USB-verbunden zeigt.*

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

 - Von Anzeigegeräten (Monitor, LCD-Anzeige, TV, Projektoren) werden an den Windows nur über die WDDM Graphics-Treiber aufgezählt. Eine indirekte Anzeige ist WDDM-Treiber für die Zwecke dieses Dokuments

 - Es muss mindestens ein Anzeigegeräts physisch verbunden, um eine vollständige WDDM Grafikhardware, die mindestens unterstützt DX 9\_1 in der Hardware.

 - Windows unterstützt nur einen festen Satz von Anzeige Connectors gemäß Definition in WDDM als Teil der [D3DKMDT\_VIDEO\_AUSGABE\_TECHNOLOGIE](http://msdn.microsoft.com/en-us/library/windows/hardware/ff546605%28v=vs.85%29.aspx) Enumeration.

 - Der Treiber WDDM (oder indirekte anzuzeigen) ist erforderlich, um die Verbindung mittelgroße hergestellt Anzeigegeräts an das System meldet genau.

 - Windows unterstützt drahtlose zeigt über Miracast Verbindung oder indirekte anzuzeigen, über WDDM1.3 oder WDDM2.0 Grafiktreiber.

 - Systeme möglicherweise eine Anzeige in der alternativen USB-Typ C-Modus für DisplayPort verbinden, und diese Anzeige als normale DisplayPort Verbindung aufgezählt werden sollte.

 - Systeme möglicherweise einen Treiber indirekte anzeigen verwenden, um ein USB-Anzeige zu verbinden.


## <a name="systemclientmobilebroadband"></a>System.Client.MobileBroadBand

*Dies sind die Anforderungen für Breitband Mobile Geräte in den Systemen integriert.*


### <a name="systemclientmobilebroadbandclassdriver"></a>System.Client.MobileBroadBand.ClassDriver

*USB-Schnittstelle-basierte g/M2 und CDMA Klasse des Mobile Breitband Gerätefirmware entsprechen USB-des IF Mobile Breitband-Schnittstelle Modell Spezifikation.*

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

USB-Schnittstelle-basierte g/M2 und CDMA Klasse Breitband Mobile Gerät Firmware Implementierung entsprechen den USB-Spezifikation für die IF Mobile Breitband Schnittstelle Modell (MBIM). Keine zusätzliche IHV-Treiber für die Funktionalität des Geräts benötigt werden, und das Gerät mit Microsoft Mobile-Broadband(MB) Klasse Treiber Implementierung arbeiten muss. Beachten Sie, dass Microsoft generische Klassentreiber-USB-Schnittstelle Geräte nicht unterstützt. Nicht-USB-Geräte erfordern des Geräteherstellers Gerätetreiber mit MB Driver Model Specification kompatibel.

Weitere Details: 
 - [Mobile Breitband-Schnittstelle Modell-Spezifikation](http://www.usb.org/developers/devclass_docs/MBIM10.zip)
 - [Mobile Breitband-Treiber Modell-Spezifikation](http://msdn.microsoft.com/en-us/library/windows/hardware/ff560543.aspx)

Ausnahme: 

 - Gerätemodelle, die als Ende der Lebensdauer (EOL) seit Dezember 2011 angekündigt.
 - Gerätemodelle, die nicht mehr in der Produktion Zeile sind. 

Beachten Sie, dass oberhalb Ausnahmen zutreffend nur, wenn:

 - Geräte werden in Windows 8-Client X86 und Windows 8-Client X64 verwendet.
 - Geräte sind vorab zertifizierten für mehrere Operatoren (mindestens 20).


### <a name="systemclientmobilebroadbandconcurrentradiousage"></a>System.Client.MobileBroadBand.ConcurrentRadioUsage

*System-Builder müssen sicherstellen, dass die RF-Leistung für mobiles Breitband, Wi-Fi und Bluetooth-fähigen Sender zur selben Zeit ausführen optimiert wird.*

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

System-Builder müssen sicherstellen, dass die RF-Leistung für mobiles Breitband, Wi-Fi und Bluetooth-fähigen Sender zur selben Zeit ausführen optimiert wird. Systeme, mit denen Internet-ICS-(tethering), Multi-Homing, und wechseln alle erfordern mehrere Sender gleichzeitig aktiv sein. Systeme sollten hohen Durchsatz, Zuverlässigkeit, eine optimale Leistungseffizienz und minimale RF Störungen unter diesen Umständen unabhängig von den Formularfaktor System sicherstellen.


### <a name="systemclientmobilebroadbandmobilebroadband"></a>System.Client.MobileBroadBand.MobileBroadBand

*Systeme, die Breitband unterstützt erfüllen Windows.*

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

Firmware-Anforderungen

USB-Geräte für GSM und CDMA Technologien (3GPP 3GPP2/Standards basierte) müssen Firmware mit der Mobile Breitband-Schnittstelle Modell Specification kompatibel sein. Diese Geräte müssen vom USB-Forum für die Einhaltung der zertifiziert werden (Wenn sie für MB Geräte verfügbar sind).

Neben den oben genannten Firmware die unten aufgeführten Features unterstützen muss durch NDIS angegeben wird.


<table>
<thead>
<tr class="header">
<th>Firmware-Funktion</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Keine Pause auf Anhalten</td>
<td>Erforderlich</td>
</tr>
<tr class="even">
<td>Selektive USB anhalten</td>
<td>Erforderlich – wenn USB basiert</td>
</tr>
<tr class="odd">
<td>Verwaltung des Senders</td>
<td>Erforderlich</td>
</tr>
<tr class="even">
<td>Mobiles Breitband Remoteaktivierung</td>
<td>Erforderlich</td>
</tr>
<tr class="odd">
<td>Fast Ruhephase</td>
<td>Erforderlich</td>
</tr>
</tbody>
</table>


Keine zusätzliche Software für den Verbindungs-Manager ist für den Betrieb von Mobilgeräten Breitband erforderlich.
Mehrwert Mobile Breitband Verbindungs-Manager, wenn implementiert, implementiert werden muss die Mobile Breitband-API (<http://msdn.microsoft.com/en-us/library/dd323271 (VS.85).aspx)>.

Microsoft empfiehlt Bus USB-basierte Schnittstellen wie analoge USB, HSIC (falls zutreffend) und SSIC (sofern verfügbar). Mobile Breitband-Stapel in Windows 8 soll nur USB-Protokoll Bus Schnittstellen unterstützen. In der folgenden Tabelle sind die erforderlichen Features auf mobilen Breitband zusammengefasst.


<table>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Bus</td>
<td>USB-HSCI (empfohlen) oder USB</td>
</tr>
</tbody>
</table>

<ul>
<li><p>Geräte MÜSSEN 16 Bitmap Remoteaktivierung Muster von 128 Byte unterstützen.</p></li>
<li><p>Geräte MÜSSEN das System registrieren Zustand ändern Sie auf aktivieren.</p></li>
<li><p>Geräte MÜSSEN aktiviert das System auf Medien verbinden.</p></li>
<li><p>Geräte MÜSSEN das System auf Medien trennen aktivieren.</p></li>
<li><p>G/M2 und CDMA-Klasse von Geräten MUSS aktiviert werden, das System auf eine eingehende SMS-Nachricht empfangen.</p></li>
<li><p>Geräte, die USSD MUSS unterstützen aktiviert das System auf USSD Nachricht empfangen.</p></li>
<li><p>Geräte MÜSSEN Remoteaktivierung Paket Angabe unterstützen. NIC sollte das Paket, wodurch die Aktivierung auf Hardware und übergeben, wenn das Betriebssystem für bereit ist es empfängt, cache.</p></li>
<li><p>Mobile Breitband-Klasse von Geräten muss die Aktivierung auf Mobile Breitband unterstützen. Es sollte das System oben erwähnten Ereignisse auf aktivieren. Hinweis Diese Remoteaktivierung über USSD ist nur erforderlich, wenn das Gerät meldet, dass es USSD unterstützt. Else ist optional. Finden Sie unter den folgenden MSDN-Dokumentationen für Weitere Informationen am SMS und registrieren Sie Zustand Remoteaktivierung Ereignisse.</p>
<ul>
<li><p>NDIS_STATUS_WWAN_REGISTER_STATE</p></li>
<li><p>NDIS_STATUS_WWAN_SMS_RECEIVE</p></li>
</ul>
</li>
</ul>



## <a name="systemclientpccontainer"></a>System.Client.PCContainer

*Windows wird auf einem Gerät centric Präsentation von Computern und Geräten bewegt.  Elemente des Windows-Benutzeroberfläche (UI), beispielsweise den Ordner Geräte und Drucker werden angezeigt, der Computer und alle Geräte, die an den Computer angeschlossen sind.  Die Anforderungen in diesem Abschnitt beschreiben, was erforderlich ist, auf dem PC werden als ein einzelnes Objekt in der Windows-Benutzeroberfläche angezeigt.*


### <a name="systemclientpccontainerpcappearsassingleobject"></a>System.Client.PCContainer.PCAppearsAsSingleObject

*Computer müssen als ein einzelnes Objekt im Ordner "Geräte und Drucker" angezeigt werden.*

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

Computer müssen als ein einzelnes Objekt im Ordner "Geräte und Drucker" angezeigt werden. Windows verfügt über eine Plattformebene die gruppiert alle Funktionen, die von dem Computer zu einem einzigen Objekt verfügbar gemacht werden. Dieses Objekt wird als Container Gerät Computer bezeichnet. Der Container Computer Gerät muss das Gerät funktioniert enthalten, die sich physisch in Chassis des Computers befinden. Dies umfasst, ist aber nicht beschränkt auf Tastaturen Touch-Pads; Steuern von Medien/Medien transport-Schlüssel, drahtlosen Sender, Speichergeräten und Audiogeräte. Der Container Computer Gerät wird in der Windows-Plattform verwendet und ist sichtbar für den Benutzer in der Benutzeroberfläche Geräte und Drucker verfügbar gemacht. Diese Anforderung wird eine konsistente und qualitativ hochwertige benutzererfahrung durch Erzwingen der Regel "ein Objekt pro physisches Gerät" im Ordner "Geräte und Drucker" sichergestellt.

Der Computer muss als einzelnes Gerätecontainer im Ordner "Geräte und Drucker" angezeigt, aus folgendem Grund: Geräte und Drucker können keine logische und verständlich Darstellung des Computers für dem Benutzer bereitzustellen. Genaue Informationen, welche Geräte physisch mit dem Computer integriert werden, muss, bereitgestellten Unterstützung und abhängige Windows-Features.

*Hinweise zum Entwurf:*

Windows wird auf einem Gerät centric Präsentation von Computern und Geräten bewegt. Der Geräte und Drucker Ordner wird angezeigt, der Computer und alle Geräte, die an den Computer angeschlossen sind. In Geräte und Drucker wird der Computer durch ein einzelnes Symbol dargestellt. Alle Funktionen, die von dem Computer verfügbar gemacht werden über einzelnes Symbol-Objekt, bietet einen zentralen Speicherort für Benutzer entdecken Sie Geräte mit dem Computer integriert und Ausführen bestimmte Aktionen auf die integrierten Geräte verfügbar sein. Um dies zu aktivieren, muss der Computer sein können erkennen und Gruppe alle integriert Computergeräte (alle Geräte physisch innerhalb der PC). Dies erfordert eine diesem Computer integrierten Geräte ordnungsgemäß identifizieren sich selbst als integrierte Komponenten. Dies kann durch zurück, der angibt, dass das Gerät nicht vom Computer entfernt werden kann, ordnungsgemäß konfigurieren von ACPI für den Port, mit dem das Gerät verbunden ist, oder erstellen eine Registrierung DeviceOverride-Eintrag für das Gerät erreicht werden. (Hinweis: für jeden Bus unterschiedliche Mechanismen zum Identifizieren der austauschbaren Beziehungs für Geräte, die diesem Bus angeschlossen sind.

Um die Funktionalität von dem Computer verfügbar gemacht werden in ein einzelnes Gerätecontainer zu gruppieren, verwendet Windows Informationen in der Geräte, Bus-Treiber und System UEFI oder BIOS und Windows-Registrierung verfügbar sind. Der Bus-Typ, mit dem ein bestimmtes Gerät verbunden ist, bestimmt, dass die heuristische Windows angewendet wird, um das Gerät zu gruppieren.  Im Whitepaper mit dem Titel "Multifunktions Gerät Support und Gerät Container Gruppen in Windows 7" unter <http://www.microsoft.com/whdc/Device/DeviceExperience/ContainerIDs.mspx>gefunden werden kann, wird die Heuristik für viele Bustypen, einschließlich erläutert:
 

 - Universal Serial Bus (USB)
 - Bluetooth
 - IP angeschlossene Geräte mithilfe von Plug & Play-Erweiterungen (PnP-X)
 - 1394
 - eSATA
 - PCI Express (PCIe)

Der einzelnen Computerobjekt Anzeige Test (ComputerSingleDDOTest.exe) muss ausgeführt werden, auf dem System, überprüfen Sie, ob diese Bedingung erfüllt ist. Das Tool ist im Windows-Lab Kit enthalten.


## <a name="systemclientradiomanagement"></a>System.Client.RadioManagement

*Dieses Feature enthält für Schaltflächen, die steuern, die Verwaltung von jeder Sender in einem Laptop oder Tablet PC zurück/konvertiert werden kann. Es enthält auch Anforderungen für GPS-Sender in Ihrer Nähe Feld Nähe zu radios und Bluetooth-fähigen Sender an, die nicht den systemeigenen Windows-Bluetooth-Stapel verwenden.*


### <a name="systemclientradiomanagementhardwarebutton"></a>System.Client.RadioManagement.HardwareButton

*Wenn ein PC verfügt über die Schaltfläche physischen (Hardware) auf einem PC zu wechseln, mit der drahtlosen Sender ein- und ausgeschaltet wird, muss es Software gesteuert werden und mit der Verwaltungsoberfläche Radio entsprechend interagieren.*

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

Es muss keine Taste für drahtlose Sender auf Windows 10 Laptops oder Tablet PCs zurück/konvertiert werden kann sein. Eine drahtlose Taste ist eine der folgenden:

 - Umschaltfläche (Notebooks und Tablets)
 - Umschaltfläche LED (nicht verbundene Standby unterstützt Notebooks und Tablets)
 - A / B Schieberegler Switch (Notebooks und Tablets)
 - A / B Schieberegler Switch mit LED (nicht verbundene Standby unterstützt Notebooks und Tablets)

Eine Taste für drahtlosen Sender ist, wenn es nicht muss mehr als ein, und die auf dem Computer vorhanden Sender gesteuert werden muss. Eine LED an, dass der Zustand des Switches ist optional. Beachten Sie, dass eine LED, der angibt, drahtlosen Status für Systeme, die verbundenen Standby unterstützen, nicht zulässig ist. Wenn eine LED zusammen mit der Schaltfläche vorhanden ist, verhält es sich wie hier definiert:

 - Es muss nur eine LED drahtlosen Status angeben (es nicht muss eine LED für Bluetooth-Funktionalität und eine für Wi-Fi usw..) vorhanden sein.
 - Wenn der globale drahtlosen Status aktiviert ist, muss die LED leuchtet.
 - Wenn der globale drahtlosen Zustand DEAKTIVIERT ist, muss die LED nicht leuchtet.
 - Wenn die Schaltfläche gedrückt ist oder Switch gekippt wird, müssen sie eine HID-Nachricht senden, die von der Sender-Verwaltungs-API genutzt werden können.
 - Wenn Radio-Verwaltungs-API eine HID-Nachricht sendet, muss die Schaltfläche oder den Schalter die Meldung und ändern den Status der LED-entsprechend.


### <a name="systemclientradiomanagementradiomaintainsstate"></a>System.Client.RadioManagement.RadioMaintainsState

*Radio verwaltet über dem Standbymodus und Neustart Power-Zyklen ein-/ausschalten Zustand.*

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

Der Status des drahtlosen Senders muss über dem Standbymodus beibehalten, neu starten, Benutzer abmelden Wechsel zwischen Benutzern und Ruhezustand.


### <a name="systemclientradiomanagementradiomanagementapihid"></a>System.Client.RadioManagement.RadioManagementAPIHID

*Drahtlose Taste muss die Änderung des Status der Radio Management-API mit HID kommunizieren.*

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

Wenn der Status der drahtlosen Sender wechseln Änderungen, ob es sich um einen Schieberegler A / B-Switch (mit oder ohne LED) oder Umschaltfläche (mit oder ohne LED) ist, muss diese HID-kompatible Hardware Schalter/Schaltfläche die HID Auflistungen von der Sender Management-API verbraucht werden verfügbar machen. Umschaltfläche dürfen nicht direkt den Zustand des Senders Gerät ändern. A / B-Switch können direkt an die Sender verkabelt werden und deren Status ändern, solange es die Änderung des Status der Radio Management-API mit dem HID-Treiber kommuniziert und den Zustand in alle Sender in dem PC vorhanden sind ändert. Die HID Usage-IDs werden: 


<table>
<thead>
<tr class="header">
<th>Verwendung-ID</th>
<th>Name der Verwendungsanalyse</th>
<th>Verwendungstyp</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0x0c</td>
<td>Drahtlose Optionsfeld-Steuerelemente</td>
<td>Bayern</td>
</tr>
<tr class="even">
<td>0xC6</td>
<td>Drahtlosen Optionsfeld</td>
<td>OOC</td>
</tr>
<tr class="odd">
<td>0xC7</td>
<td>Drahtlosen Sender LED</td>
<td>OOC</td>
</tr>
<tr class="even">
<td>0xC8</td>
<td>Drahtlosen Sender Schieberegler Switch</td>
<td>OOC</td>
</tr>
</tbody>
</table>


In den folgenden Tabellen sind die Auflistungen dargestellt.
<!--These tables, which were simple lists in the original Word document, seem like they should and could be unified. 
However, based on the text in the first columns, they aren't ready to simply have their columns of values packed into
the same table. Creating a table that accommodates the differences is beyond the scope of this conversion to Markdown.-->

**In Tabelle 1. Schaltfläche ohne LED (statusfreie Schaltfläche) – für Notebooks, Tablets und Convertible**

<table border="2">
<tr>
<td>VERWENDUNG\_SEITE (generischer Desktop)</td>
<td>05 01</td>
</tr>
<tr>
<td>VERWENDUNG (Wireless Optionsfeld-Steuerelemente)</td>
<td>09 0C</td>
</tr>
<tr>
<td>SAMMLUNG (Anwendung)</td>
<td>A1 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MINIMUM (0)</td>
<td>15 00</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MAXIMUM (1)</td>
<td>25 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (Wireless Optionsfeld)</td>
<td>09 C6</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_COUNT (1)</td>
<td>95 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Rel Var, Daten)</td>
<td>81 06</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Cnst Var, Abs)</td>
<td>81 03</td>
</tr>
<tr>
<td>END\_AUFLISTUNG</td>
<td>C0</td>
</tr>
</table>


**In Tabelle 2. Schaltfläche mit LED – für Laptops, Tablets und Convertible, die NICHT verbundenen Standby unterstützen**

<table border="2" cellpadding="0" cellspacing="0" width="0">
<tr>
<td>VERWENDUNG\_SEITE (generischer Desktop)</td>
<td>05 01</td>
</tr>
<tr>
<td>VERWENDUNG (Wireless Optionsfeld-Steuerelemente)</td>
<td>09 0C</td>
</tr>
<tr>
<td>SAMMLUNG (Anwendung)</td>
<td>A1 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MINIMUM (0)</td>
<td>15 00</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MAXIMUM (1)</td>
<td>25 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (Wireless Optionsfeld)</td>
<td>09 C6</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_COUNT (1)</td>
<td>95 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Rel Var, Daten)</td>
<td>81 06</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Cnst Var, Abs)</td>
<td>81 03</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (drahtlosen Sender LED)</td>
<td>09 C7</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Rel Var, Daten)</td>
<td>91 02</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Cnst Var, Abs)</td>
<td>91 03</td>
</tr>
<tr>
<td>END\_AUFLISTUNG</td>
<td>C0</td>
</tr>
</table>
                                   

**Tabelle 3. Schieberegler Schalter (ohne LED) - Laptops, Tablets und Convertible**

<table border="2" cellpadding="0" cellspacing="0" width="0">
<tr>
<td>VERWENDUNG\_SEITE (generischer Desktop)</td>
<td>05 01</td>
</tr>
<tr>
<td>VERWENDUNG (Wireless Optionsfeld-Steuerelemente)</td>
<td>09 0C</td>
</tr>
<tr>
<td>SAMMLUNG (Anwendung)</td>
<td>A1 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MINIMUM (0)</td>
<td>15 00</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MAXIMUM (1)</td>
<td>25 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (drahtlosen Sender Schieberegler Switch)</td>
<td>09 C8</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_COUNT (1)</td>
<td>95 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Daten, Var, Abs)</td>
<td>81 02</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Cnst Var, Abs)</td>
<td>81 03</td>
</tr>
<tr>
<td>END\_AUFLISTUNG</td>
<td>C0,</td>
</tr>
</table>                                      
 

**In Tabelle 4. Schieberegler Switch mit LED - Laptops, Tablets und Convertible, die NICHT verbundenen Standby unterstützen**

<table border="2" cellpadding="0" cellspacing="0" width="0">
<tr>
<td>VERWENDUNG\_SEITE (generischer Desktop)</td>
<td>05 01</td>
</tr>
<tr>
<td>VERWENDUNG (Wireless Optionsfeld-Steuerelemente)</td>
<td>09 0C</td>
</tr>
<tr>
<td>SAMMLUNG (Anwendung)</td>
<td>A1 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MINIMUM (0)</td>
<td>15 00</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MAXIMUM (1)</td>
<td>25 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (drahtlosen Sender Schieberegler Switch)</td>
<td>09 C8</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_COUNT (1)</td>
<td>95 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Daten, Var, Abs)</td>
<td>81 02</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;EINGABE (Cnst Var, Abs)</td>
<td>81 03</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (drahtlosen Sender LED)</td>
<td>09 C7</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Rel Var, Daten)</td>
<td>91 02</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Cnst Var, Abs)</td>
<td>91 03</td>
</tr>
<tr>
<td>END\_AUFLISTUNG</td>
<td>C0</td>
</tr>
</table>
                                                       

**Tabelle 5. LED-nur (keine Schaltfläche oder Schieberegler) - Laptops, Tablets und Convertible, die KEINE Unterstützung für standby verbunden**

<table border="2" cellpadding="0" cellspacing="0" width="0">
<tr>
<td>VERWENDUNG\_SEITE (generischer Desktop)</td>
<td>05 01</td>
</tr>
<tr>
<td>VERWENDUNG (Wireless Optionsfeld-Steuerelemente)</td>
<td>09 0C</td>
</tr>
<tr>
<td>SAMMLUNG (Anwendung)</td>
<td>A1 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MINIMUM (0)</td>
<td>15 00</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;LOGISCHE\_MAXIMUM (1)</td>
<td>25 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;VERWENDUNG (drahtlosen Sender LED)</td>
<td>09 C7</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_COUNT (1)</td>
<td>95 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (1)</td>
<td>75 01</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Rel Var, Daten)</td>
<td>91 02</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;BERICHT\_GRÖßE (7)</td>
<td>75 07</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;AUSGABE (Cnst Var, Abs)</td>
<td>91 03</td>
</tr>
<tr>
<td>END\_AUFLISTUNG</td>
<td>C0</td>
</tr>
</table> 


 
Drahtlosen Sender LED benötigen einen HID-kompatiblen Treiber um den Zustand des Switches Modus Flugzeug befindet sich in der Benutzeroberfläche widerzuspiegeln.  Drahtlosen Sender LED verwendet HID nur für die Ausgabe (keine Eingaben, da die Schaltfläche nicht vorhanden ist). 

Radio-Verwaltungs-API HID sendet eine Nachricht, da der globale drahtlosen Zustand (Flugzeug Modus) geändert hat, muss die Option Diese Nachricht verarbeiten und ein-/ausschalten den Zustand.

Für einen A / B-Switch muss proprietäre eingebetteten Controller des Herstellers melden den richtigen Zustand des Switches jederzeit durch Senden einer Nachricht HID an HID-Treiber, einschließlich jedes Mal, wenn der PC-Option auf Rückseite aktiviert ist. Reporting den Zustand des Switches A / B aus, wenn der Computer wieder eingeschaltet ist besonders wichtig, in dem Fall, dass die Option Status der PC-Option in Staaten S3/S4/S5 wurde geändert.
 

## <a name="systemclientradiomanagementconnectedstandby"></a>System.Client.RadioManagement.ConnectedStandby

*Dieses Feature enthält für Schaltflächen, die steuern, die Verwaltung von jeder Sender in einem Laptop oder Tablet PC zurück/konvertiert werden kann. Die Sender an, denen für diese Anforderung gilt sind GPS.*


### <a name="systemclientradiomanagementconnectedstandbynoradiostatusindicatorlights"></a>System.Client.RadioManagement.ConnectedStandby.NoRadioStatusIndicatorLights

*Systeme, die Standbymodus verbunden unterstützen müssen ein Licht, der den Status des die Sender im System nicht enthalten.*

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

Systeme, die verbundenen Standby unterstützen können keine, um Energie zu sparen, eine Statusanzeige zurück, der angibt, ob die Sender auf sind enthalten. 


## <a name="systemclientsystemconfiguration"></a>System.Client.SystemConfiguration


### <a name="systemclientsystemconfigurationwindows10requiredcomponents"></a>System.Client.SystemConfiguration.Windows10RequiredComponents

*Windows-10-Systeme müssen bestimmte Geräte enthalten.*

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

Für alle anderen Windows-10-Systeme sind in der folgenden Tabelle die minimalen erforderlichen Komponenten in einem System in Reihenfolge für Windows 10 kompatibel ist dafür vorhanden sind. Alle Komponenten müssen die Kompatibilität erfüllen und Gerät Kompatibilitätstests für Windows 10 übergeben.
<!--This table was also broken in the original Word document.-->


<table>
<thead>
<tr class="header">
<th><strong> </strong></th>
<th><strong> </strong></th>
<th><strong> </strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong> </strong></td>
<td>Speichertyp</td>
<td>Microsoft Windows Storage Mindestanforderungen erfüllen</td>
</tr>
<tr class="even">
<td><strong>System-firmware</strong></td>
<td> </td>
<td>UEFI gemäß Definition im System.Fundamentals.Firmware Anforderungen</td>
</tr>
<tr class="odd">
<td><strong>Netzwerke</strong></td>
<td>/ S Ethernet oder Wi-Fi</td>
<td>Muss entweder ein zertifizierter Ethernet oder Wi-Fi-adapter</td>
</tr>
<tr class="even">
<td><strong>Grafiken</strong></td>
<td>GPU</td>
<td>Mindestens Direct3D 10 Feature Ebene 9_3 und finden Sie unter System.Fundamentals.Graphics.WDDM</td>
</tr>
</tbody>
</table>



## <a name="systemclientsystemimage"></a>System.Client.SystemImage

*Die Anforderungen in diesem Abschnitt wird beschrieben, die Qualität zweiter Ebene Hardware SW + OEM Bild*


### <a name="systemclientsystemimagesystemrecoveryenvironment"></a>System.Client.SystemImage.SystemRecoveryEnvironment

*System umfasst Windows Recovery-Umgebung auf einer separaten Partition.*

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

Ein System muss eine separate Partition mit einem startbaren Windows Recovery Environment Bilddatei (winre.wim) enthalten. Die GPT-Partition sollte vom Typ PARTITION\_MSFT\_WIEDERHERSTELLUNG\_GUID, enthält die GPT\_ATTRIBUT\_PLATTFORM\_ERFORDERLICH und GPT-\_BASIC\_DATEN\_ATTRIBUT\_NO\_LAUFWERK\_BUCHSTABE Attribute und mindestens 50 Megabyte (MB) freien Speicherplatz enthält, nachdem die Bilddatei Windows Recovery Environment es kopiert wurde.


## <a name="systemclientsystempartition"></a>System.Client.SystemPartition

*Die Anforderungen in diesem Abschnitt werden die PC System Partition konfigurationsanforderungen beschrieben.*


### <a name="systemclientsystempartitiondiskpartitioning"></a>System.Client.SystemPartition.DiskPartitioning

*Systeme, die im Lieferumfang von Windows-Betriebssystems müssen Partitionierung Anforderungen erfüllen.*

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

Eine active Directory-Partition zusätzlich zu den Vorgang Systempartition (konfiguriert als Boot, Seitendatei, Dump abstürzen usw.). müssen im Lieferumfang von Windows-Systemen. In active Directory-Partition muss mindestens 250 MB freiem Speicherplatz seinem die Leerzeichen von erforderlichen Dateien verwendet haben. Windows Recovery-Umgebung (RE) und OEM-Tools (vom OEM bereitgestellte) gehostet, solange die Partition weiterhin die 250 MB freiem Speicherplatz Anforderung erfüllt, kann diese zusätzliche Systempartition verwendet werden.

Die Implementierung dieser Partition ermöglicht die Unterstützung von aktuellen und zukünftigen Windows-Features wie BitLocker und vereinfacht die Konfiguration und Bereitstellung.
Tools und Dokumentation zur Implementierung von Split-Ladeprogramm Konfiguration finden Sie unter **Windows OEM-Vorinstallation Kit/Automated Installation Kit (OPK/AIK).**


### <a name="systemclientsystempartitionoempartition"></a>System.Client.SystemPartition.OEMPartition

*Windows-Systeme mit Recovery & OEM-Partitionen müssen Partitionierung Anforderungen erfüllen.*

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

Wenn ein System einer separaten Partition zu Wiederherstellungszwecken oder OEM-Partitionen zu anderen Zwecken enthält, muss diese separaten Partition mit einem GPT identifiziert werden\_ATTRIBUT\_PLATTFORM\_REQUIRED-Attribut. Dieses Attribut definiert ist, als Teil der [PARTITION\_INFORMATIONEN\_GPT](http://msdn.microsoft.com/en-us/library/aa365449.aspx) Struktur.
Beispiel:

 - Wenn diese separaten Partition eine startbare Windows Recovery Environment Bilddatei enthält, muss die GPT-Partition vom Typ PARTITION\_MSFT\_WIEDERHERSTELLUNG\_GUID und umfassen die GPT\_ATTRIBUT\_PLATTFORM\_REQUIRED-Attribut.

Partitionen, die mit der GPT identifiziert werden\_ATTRIBUT\_PLATTFORM\_REQUIRED-Attribut darf nicht zum Speichern von Benutzerdaten verwendet werden (z. B. über Daten sichern, beispielsweise).


## <a name="systemclientscreenrotation"></a>System.Client.ScreenRotation

<!--No content was provided here in the original Word file.-->

### <a name="systemclientscreenrotationsmoothrotation"></a>System.Client.ScreenRotation.SmoothRotation

*Systeme mit Beschleunigungsaufnehmern führen Drehung des Bildschirms in 300 Millisekunden und ohne video Probleme aufgeführt.*

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

Alle Windows-Systeme mit Beschleunigungsmesser benötigt ausreichende Grafiken Leistung, Leistung Drehung des Bildschirms erfüllen: 

 - WDDM-Treiber ist erforderlich, die Quelle Modi für die integrierte Anzeige aufgelistet werden. WDDM-Treiber muss für jede Modus gedrehte Modi (0, 90, 180 und 270) unterstützen, die sie für die integrierte Systemsteuerung aufgezählt werden.

 - Die Drehung ist erforderlich, die unterstützt werden, selbst wenn der integrierte Bereich in einer doppelten oder erweiterte Topologie mit einer anderen Anzeigegeräts ist. Doppelte Modus ist es akzeptabel, drehen alle Ziele mit der gedrehte Datenquelle verbunden. Pro Pfad ist Drehung zulässig, aber nicht erforderlich.

Sowohl die oben genannten Anforderungen sind optional in Stereo 3D fähig Lösungen.


## <a name="systemclienttabletgraphics"></a>System.Client.Tablet.Graphics

<!--No content was provided here in the original Word file.-->

### <a name="systemclienttabletgraphicssupportallmodeorientations"></a>System.Client.Tablet.Graphics.SupportAllModeOrientations

*Grafiktreiber auf Tablet-Systemen müssen alle Modus Ausrichtung unterstützen.*

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

Grafiktreiber auf Tablet-Systemen müssen alle Modus Leitlinien für jede Lösung für den Bereich integrierte aufgezählt unterstützen:
 

 - Graphics-Treiber ist zum Aufzählen der Quelle Modi für die integrierte Anzeige erforderlich. Für jede Quellmodus aufgelistet ist der Grafiktreiber erforderlich, um jede Orientierung (0, 90, 180 und 270) unterstützen.

 - Jede Orientierung ist erforderlich, auch wenn der integrierte Bereich in einer doppelten oder erweiterte Topologie mit einer anderen Anzeigegeräts ist. Doppelte Modus ist es akzeptabel, drehen alle Ziele mit der gedrehte Datenquelle verbunden. Pro Pfad ist Drehung zulässig, aber nicht erforderlich.

Sowohl die oben genannten Anforderungen sind optional in Stereo 3D fähig Lösungen.


## <a name="systemclientwlanbasicconnectivity"></a>System.Client.WLAN.BasicConnectivity

<!--No content was provided here in the original Word file.-->

### <a name="systemclientwlanbasicconnectivitywlanbasicconnectivity"></a>System.Client.WLAN.BasicConnectivity.WlanBasicConnectivity

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

Wenn vorhanden WLAN für den ungebundenen Konnektivität zu Netzwerken für eine Vielzahl von Szenarien wie Browsen im Web oder streaming Videoinhalte ermöglichen kann. Wenn dieser Parameter angegeben wurde das WLAN-Gerät muss unterstützen, mindestens eine Verbindung mit einer WPA2-Psk AES ap und alle zugehörigen Aktionen, die diese Verbindung bisher zu aktivieren. Dies umfasst Folgendes:

 - Suchen nach verfügbaren Netzwerken
 - Gerät-Aufzählung
 - Kontrollkästchen Funktionen
 - Sender ein- / ausschalten
 - Abfragen von Eigenschaften-Schnittstelle
 - Herstellen einer Verbindung mit einer WPA2 PSK AES-ap in der angegebenen Zeit wie in der Windows-10 WLAN-Anforderungen
 
Zeitangaben für die oben genannten Aktionen finden Sie in der Windows 10 WLAN-Gerät Anforderungen.


## <a name="systemclientwlanhangdetectionandrecovery"></a>System.Client.WLAN.HangDetectionAndRecovery

<!--No content was provided here in the original Word file.-->

### <a name="systemclientwlanhangdetectionandrecoverywlanhangdetectionandrecovery-if-implemented-wdi-drivers-only"></a>System.Client.WLAN.HangDetectionAndRecovery.WlanHangDetectionAndRecovery (If-implementierte) **(nur WDI-Treiber)**

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

Wi-Fi Gerätefirmware ist bekannt, dass hängen und / oder in einem unterbrochene Zustand erhalten möchten. Wenn in diesem Fall würde der untere Rand Treiber entweder Absturz verursacht eine 9F (blauer Bildschirm) oder das Wi-Fi-Subsystem ruft in einen Zustand erfordert einen Neustart des Systems für das Gerät erneut funktionsfähig sein. In beiden Fällen wird der Benutzer in ihrer Konnektivität einen negativen Umgang mit konfrontiert, und ihre allgemeine Systemverwendung unterbrochen ist. Als Bestandteil des WDI wir einen Mechanismus, um zu erkennen, wann die Firmware in dieser Zustände ruft entworfen haben und das Gerät nahtlos wiederherstellen. Dadurch wird sichergestellt, dass der Benutzer einen Geschäftsablauf im Dienst angezeigt, indem sichergestellt wird, dass Gerätestapel Wi-FI wiederhergestellt und Verbindung mit dem Netzwerk ohne das System benötigen einen Neustart fortgesetzt. Geräte müssen Unterstützung bei der Erkennung hängen und Wiederherstellung in WDI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN. Finden Sie in der Spezifikation WDI Implementierungsdetails.

Anforderung – Hardware / Firmware

System ACPI Firmware: Bereitstellen des Systems ACPI Methoden zum PDLR auf das Gerät an einen Bus oder auf Device-Ebene.

System-Hardware: ist für eine PDLR (vollständige Gerät Ebene Reset) zulässig. Alle Systeme müssen PDLR unterstützen.

System: Im System wird die Unterstützung für die Unterstützung von PDLR angezeigt.

Gerät: Der untere Rand Treiber speichert mit 25 ms und Größe von 250 Kb sammeln werden können

System: Das System müssen innerhalb von 10 Sekunden zurücksetzen.


## <a name="systemclientwlanhostednetwork"></a>System.Client.WLAN.HostedNetwork

<!--No content was provided here in the original Word file.-->

### <a name="systemclientwlanhostednetworkwlanhostednetwork-if-implemented"></a>System.Client.WLAN.HostedNetwork.WlanHostedNetwork (If-implementierte)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


**Beschreibung** Mit diesem Feature kann ein Windows-Computer einen einzelnen physischen drahtlosen Adapter für die Verbindung als Client für einen Hardware Access Point (AP), während gleichzeitig die fungiert als Softwareupdate AP andere WLAN-fähigen Geräte zulassen zum Herstellen der Verbindung verwenden.


## <a name="systemclientwlanwifidirect"></a>System.Client.WLAN.WiFiDirect

<!--No content was provided here in the original Word file.-->

### <a name="systemclientwlanwifidirectwlanwifidirect-if-implemented"></a>System.Client.WLAN.WiFiDirect.WlanWiFiDirect (If-implementierte)

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

Unterstützung für direkte Wi-Fi vom Wi-Fi-Treiber Miracast, öffentlichen APIs für Wi-Fi direkt zu ermöglichen, eine Kopplung mit & vom PC, annehmen und Herstellen einer Verbindung mit anderen direkte Wi-Fi-Gerät für UNTERWEGS & der Client-Rolle zu aktivieren. Hierzu zählen außerdem Unterstützung für gleichzeitige Vorgang über direkte Wi-Fi & Station.


## <a name="systemclientwlanmiracast"></a>System.Client.WLAN.Miracast

<!--No content was provided here in the original Word file.-->

### <a name="systemclientwlanmiracastwlanmiracast-if-implemented"></a>System.Client.WLAN.Miracast.WlanMiracast (If-implementierte)

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

Miracast erfordert WiFiDirect Support in der WLAN-Adapter und Support in der Graphics-Treiber. Miracast ermöglicht es dem Benutzer, deren Anzeige zu einem Miracast unterstützt Sync-Gerät erweitern.


## <a name="systemfundamentalsdebugport"></a>System.Fundamentals.DebugPort

*Die Möglichkeit zum Debuggen des Systems ist für die Unterstützung von Kunden in das Feld und die Stamm-verursacht Verhalten in den Kernel entscheidend.  Anforderungen in diesem Bereich unterstützt das von Kernel Debuggen ein Windows-Systems.*


### <a name="systemfundamentalsdebugportsystemexposesdebuginterface"></a>System.Fundamentals.DebugPort.SystemExposesDebugInterface

*System macht Debug-Schnittstelle, die mit Debuggen Port Spezifikation kompatibel.*

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

Windows-10 unterstützt mehrere verschiedene Debug Transporten. Sie können in der Implementierung der bevorzugte Reihenfolge sind unten aufgeführt.
**Debuggen von Transporten Hardware** 

 - Ethernet-Network Interface Card, aus der Liste der unterstützten: <http://msdn.microsoft.com/en-us/library/windows/hardware/hh830880>

 - USB 3.0 – xHCI Controller xHCI Debug-Spezifikation kompatibel.

 - 1394 OHCI konform Firewire Domänencontroller.

 - Dieser Transport aus Windows 10 bis 2016 ENTFERNT wurde, und ist nicht gültig für Anforderungen in zukünftigen Versionen von Windows 10.

 - USB2 OTG (auf unterstützten Hardware für Windows XHCI Debuggen stattdessen empfohlen).

 - USB 2.0-EHCI Debug (der Debuggen aktiviert Port muss für Benutzer zugänglich sein).

 - Legacy seriell (16550 kompatibel programming Interface).

 
**ZUSÄTZLICHE ANFORDERUNGEN** FÜR ALLE DER OBEN GENANNTEN IMPLEMENTIERUNGEN MUSS FOLGENDES GELTEN:
 

 - Es muss mindestens ein Benutzer zugänglich Debugport auf dem Computer. Es ist akzeptabel auf Systeme, die nicht verfügbar machen einen USB-Anschluss oder einem anderen akzeptable Port aus der Liste aus, um stattdessen erfordern eine separate debugging Pinnwand oder Geräte, die bietet die Möglichkeit zum Debuggen über (oder mehrere) der oben genannten angezeigt. Dieses Gerät/Pinnwand müssen in der gleichen standardmäßigen Port beendet werden für den Transport verwendet wird, wenn es sich um "integrierte" des Computers. Wenn dieses Gerät erforderlich ist müssen sie in die Systemspezifikationen dokumentiert werden, Benutzer gewartet werden, werden Benutzer auf dem Computer installiert, und für den Verkauf vom Hersteller des Computers verfügbar sein.

 - Auf PC-Plattformen Verkaufsversion wird dringend empfohlen, dass Computer 2 Benutzer zugänglich Debug-Ports aus der obigen Liste verfügen. Der sekundären Debugport ist erforderlich, um Szenarien zu debuggen, auf dem ersten Debug Ports als Teil des Szenarios wird. Microsoft ist nicht für das Debuggen oder bei der Wartung von Problemen, die auf der Plattform Retail gedebuggt oder auf Entwicklungsplattformen reproduziert werden können nicht verantwortlich.

 - SoC Entwicklungs- oder Prototyp Plattformen bereitgestellt an Microsoft zur Evaluierung benötigen einen dedizierten Debugport für das debugging verfügbar. Wenn der Debugport für alle Szenarien, die verwendet wird, die auch auf Verkaufsversion des Protokollversands Geräten verwendet werden soll, in diesem Fall muss vorhanden sein ein sekundären Debug-Ports für das debugging verfügbar. Dadurch wird sichergestellt, dass SoC Entwicklungsplattformen zum Testen und Debuggen von allen Szenarien für alle verfügbaren Transporten, einschließlich USB-Hostcontroller und -Funktion verwendet werden können.

 - Alle Debug Gerät Register müssen Arbeitsspeicher oder e/a zugeordnet sein. Beispielsweise muss das Debuggerät nicht hinter einem freigegebenen Bus wie SPI oder I2C verbunden werden. Dadurch wird verhindert, dass andere Geräte auf dem gleichen Bus gedebuggt wird.

 - Bei Aktivierung wird das Debuggen Gerät eingeschaltet und eingestempelt von der Firmware UEFI während Systemanalyse vor dem Start, vor dem Übergeben der Steuerung an den Bootblock.  

Weitere Informationen finden Sie unter <http://go.microsoft.com/fwlink/?LinkId=237141>


## <a name="systemfundamentalsdebugportusb"></a>System.Fundamentals.DebugPort.USB

*Die Möglichkeit zum Debuggen des Systems USB3 ist entscheidend zur Unterstützung von Kunden in das Feld und Verhalten in den Kernel Root verursacht.  Anforderungen in dieser Bereich Unterstützung der debugging-Funktion für den xHCI Controller-basierte Systeme über eine Debug registriert. Jedes System, bei dem xHCI Controller und USB3 externer Port über diesen Port unterstützen soll.*


### <a name="systemfundamentalsdebugportusbsystemexposesdebuginterfaceusb"></a>System.Fundamentals.DebugPort.USB.SystemExposesDebugInterfaceUsb

*USB-3-System macht Debug-Schnittstelle, die mit Debuggen Port Spezifikation kompatibel.*

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

Systeme, die USB-3 unterstützen müssen xHCI Controllern xHCI Debug Spezifikation konform verfügen. Die Controllern xHCI müssen Speicher zugeordnet sein.

Es muss mindestens ein Benutzer zugänglich USB 3.0 Debugport auf dem Computer.

Alle 3.0 USB-Anschlüsse müssen einen kurzen am VBus Pin Schutz so, dass ein anderes USB-Hostcontroller verbunden ist, die USB-Kreis nicht beschädigt ist.

3.0 USB-Hubs müssen nicht in der SoC oder PCH/Southbridge integriert werden.

Weitere Informationen finden Sie unter <http://go.microsoft.com/fwlink/?LinkId=58376>.


## <a name="systemfundamentalsenergyestimation"></a>System.Fundamentals.EnergyEstimation

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>


### <a name="systemfundamentalsenergyestimationdiscretional"></a>System.Fundamentals.EnergyEstimation.Discretional

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

In den primären Speicher, Netzwerk und primäre Anzeige einschließlich HLK sind derzeit drei Energie Micro-Benchmarktests vorhanden. Führen Sie auf einem beliebigen Batterie-basiertes Gerät sind diese Benchmarks geplant. Bei der Ausführung emulieren die Benchmarks für eine Reihe von stabilen Zustand Arbeitslasten einer bestimmten Komponente. Gleichzeitig Beachten sie auch die Batterie abzuleiten aus.

<ol style="list-style-type: decimal">
<li><p>Die Batterie muss nahezu vollständig vor der Ausführung einer Vergleichstest geladen werden. Eine Richtlinie hat in der Regel mehrere Analysen. Die Vergleichstest wird die erwartete Laufzeit schätzen Sie vor Beginn der Bewertung. Die verbleibende Dauer der Batterie Lebensdauer kleiner als die geschätzte Zeit für das Ausführen des gesamten Assessment erforderlich ist, wird die Ausführung sofort mit einer Fehlermeldung beendet.</p></li>
<li><p>Beachten Sie außerdem, dass einige Geräte keine Batterie Bericht abzuleiten ordnungsgemäß, wenn es 100 % ausgelastet ist. Stellen Sie sicher, dass sie vor der Ausführung einer Vergleichstest kleiner oder gleich 99 % Energie Kapazität ist.</p></li>
<li><p>Anzeige benchmarkanforderungen:</p>
<p>Zeigen Sie Benchmarktests die Batterie abzuleiten, während andere Helligkeit Einstellungen an. Aus diesem Grund muss das Gerät zugreifen können, um die Helligkeit Ebene über Software Steuerelement anzupassen.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Öffnen Sie ein Eingabeaufforderungsfenster als administrator</p></li>
<li><p>Führen Sie die folgenden Befehle aus, um festzustellen, ob die Helligkeit geändert wird:</p>
<code>
<p>powercfg /setacvalueindex scheme_current sub_video aded5e82-b909-4619-9949-f5d71dac0bcb 10</p>
<p>powercfg /setdcvalueindex scheme_current sub_video aded5e82-b909-4619-9949-f5d71dac0bcb 10</p>
<p>powercfg /setactive scheme_current</p>
</code></li>
<li><p>Wenn die Helligkeit nicht geändert wird, ist das Gerät nicht für diese Vergleichstest geeignet.</p></li>
</ol></li>
<li><p>Netzwerk-benchmarkanforderungen: keine</p></li>
<li><p>Speicher benchmarkanforderungen:<br />
Einrichten einen gefälschten Laufwerk Get die Leistungsfähigkeit Baseline muss Vergleichstest zur Speicherung.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Dieser Schritt braucht des Systems mit Testsigning auf und WTT Dienst aktiviert. Nachdem Sie der Testcomputer über HLK Controller eingerichtet haben, sollten diese automatisch eingerichtet werden.</p></li>
<li><p>Öffnen Sie ein Eingabeaufforderungsfenster als Administrator und e3hlk\storhba-cd in den Ordner. Der Ordner Storhba finden Sie auch im <em> &lt;-Name des Domänencontrollers&gt;\Tests\&Lt; Prozessorarchitektur&gt;\e3hlk.</em></p></li>
<li><p>Cscript Scripts\Install_Storhba.wsf /storhba:1 /TestParameter:6 /LogicalUnitDiskSizeInMB:4096 /PhysicalLuns:1</p></li>
<li><p>Diskmgmt.msc (um datenträgerverwaltung öffnen).</p></li>
<li><p>Hier finden Sie den neuen Datenträger mit einer Größe von 4GB.</p></li>
<li><p>Initialisieren Sie den Datenträger mit MBR Partitionsstil.</p>
![Initialisieren Sie im Dialogfeld Datenträger](images/initialize-disk-dialog-box.png)
</li>
<li><p>Klicken Sie mit der rechten Maustaste darauf, wählen Sie "Neues einfaches Volume" aus. Führen Sie die Benutzeroberfläche, die ein Volume mit 4GB Speicherplatz erstellen und formatieren Sie ihn in NTFS aus.</p></li>
<li><p>Beachten Sie die zugewiesenen Laufwerkbuchstabe des neuen Datenträger aus, und schließen Sie Datenträger-Manager.</p></li>
<li><p><em>Set\storapp_set.exe /flag – zurücksetzen</em></p></li>
<li><p>Einmal Fertig stellen den Test, können Sie das falsche Laufwerk durch Ausführen von entfernen</p>
<p><em>Cscript Scripts\Install_Storhba.wsf /storhba:0</em></p>
<p>Es kann einige Problem entfernt werden, das Fake Treiber nach dem Zurücksetzen. Dieses Problem, zu umgehen können zuerst erstellen Sie ein anderes Laufwerk gefälschtes durch Ausführen von "<em>Scripts\Install_Storhba.wsf /storhba:1 /TestParameter:6 /LogicalUnitDiskSizeInMB:4096 /PhysicalLuns:1" erneut, gefolgt von "Scripts\Install_Storhba.wsf /storhba:0".</em></p></li>
</ol></li>
</ol>


## <a name="systemfundamentalsfirmware"></a>System.Fundamentals.Firmware

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsfirmwareacpi"></a>System.Fundamentals.Firmware.ACPI

*ACPI-Systemanforderungen*

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

Alle Systeme müssen die folgenden ACPI Tabelle Anforderungen erfüllen.

| Anforderungen für ACPI-Tabelle                                  |
|----------------------------------------------------------|
| Stamm-System Beschreibung Zeiger (RSDP)                   |
| Stamm- oder erweiterten System Description-Tabelle (RSDT oder XSDT) |
| Feste ACPI Description-Tabelle (FADT)                      |
| Mehrere APIC Description-Tabelle (MADT)                   |
| Core System Ressourcen Beschreibung (CSRT)                 |
| Debug-Port-Tabelle (DBGP)                                  |
| Differenzierten System Description-Tabelle (DSDT)           |

 
**DSDT-Anforderungen**

Alle Geräte im ACPI-Namespace müssen gemäß den Anweisungen in ACPI 4. 0a enthalten:
 
 - Der Hersteller zugewiesene, ACPI-kompatible Hardware-ID (\_HID-Objekt).

 - Eine Reihe von Ressourcen verbraucht (\_CRS-Objekt).

Darüber hinaus gelten die folgenden bedingten Anforderungen:

 - Wenn alle Geräte im Namespace die gleiche Hardware-ID gemeinsam, und klicken Sie dann jeweils erforderlich ist, wenn unterschiedliche eindeutigen Bezeichner (\_UID Objekt).

 - Wenn ein Gerät im Namespace von seinem übergeordneten Bus (Plug & Play-Bus), aufgezählt wird die Adresse des Geräts auf seinem übergeordneten Bus (\_ADR-Objekt) ist erforderlich.

 - Wenn ein Gerät im Namespace mit einem Microsoft bereitgestellten Treiber, kompatible ID kompatibel ist (\_CID-Objekt) definierten für dieses Gerät Typs erforderlich ist.

**Allgemeine Eingabe/Ausgabe (GPIO) für ein System, mit dem Standbymodus unterstützt verbunden**

GPIO Controller für Pins von Windows-Treiber oder ASL Steuerelementmethoden müssen als Geräte im ACPI-Namespace verwendet werden.

Geräte in den Namespace, die mit GPIO Pins auf einem Controllergerät enumerierten verbunden werden müssen:

 - Einschließen GPIO e/a-Verbindung Ressource Deskriptoren in ihren \_CRS Stifte GPIO e/a verbunden.  Einschließen GPIO Interrupt Verbindung Ressource Deskriptoren in ihren \_GPIO Interrupt Stifte CRS-Objekt verbunden.

**Einfache peripherer Bus (SP b) für ein System, das Standbymodus verbunden unterstützt**

SP b Controller für Verbindungen von Windows-Treiber oder ASL Steuerelementmethoden müssen als Geräte im ACPI-Namespace verwendet werden.

Geräte in den Namespace, der mit einer enumerierten SP b Controller-Gerät (UART I2C, SPI) verbunden werden müssen SP b Verbindung Ressource Deskriptoren in enthalten ihre \_CRS auf den SP b Verbindung(en) verwendet wird.

**Power-Schaltfläche**

Die Leistungsfähigkeit Schaltfläche, ob als Schaltfläche Power-Methode ein ACPI oder als Teil des Windows-kompatiblen Schaltfläche Arrays muss implementiert:

 - Können Sie sehen, dass das System Hochfahren bei Bedarf.

 - Generieren der Power Schaltfläche außer Kraft setzen-Ereignis (im Abschnitt 4.7.2.2.1.3 ACPI 4. 0a Specification) beim 4 Sekunden gedrückt.

**Schaltfläche Power-Methode**

Systeme integrierten abhängig (oder verbundene) Tastaturen/Maus für die Eingabe muss die ACPI Power-Methode Schaltfläche entsprechen (im Abschnitt 4.7.2.2.1.2 ACPI 4. 0a Specification).  Darüber hinaus müssen Systeme, die Unterstützung standby verbunden:

 - Implementieren Sie die Schaltfläche ACPI Steuerung-Methode Power (im Abschnitt 4.7.2.2.1.2 ACPI 4. 0a Spezifikation) mit einem dedizierten GPIO Interrupt Pin auf Signal Schaltflächenereignisse drücken.

 - Konfigurieren Sie die Power-Schaltfläche GPIO Interrupt Pin als ein nicht freigegeben, Aktivierung-fähige (ExclusiveAndWake) GPIO unterbrechen Verbindungsressource.

 - Listen Sie die Power-Schaltfläche GPIO Interrupt Verbindungsressource in die Ereignisinformationen ACPI (\_AEI-Objekt) des GPIO Controller Geräts mit dem es verbunden ist.

 - Geben Sie die Ereignismethode (\_Lxx oder \_Exx-Objekt) für das Ereignis des Power-Schaltfläche unter dem GPIO Controller-Gerät im ACPI-Namespace.

HINWEIS: Systeme, die einen separaten Treiber zum Verarbeiten von Power Tasten erfordern, ist es akzeptabel, Treiber eine Control-Methode ausgewertet werden soll, die ein Notify() auf dem Gerät Schaltfläche Power-Methode statt der oben genannten GPIO basierende Lösung ausgeführt wird.

**Array-basierte Power Schaltfläche**

Touch-First (Tastatur kleiner) Systeme müssen:

 - Implementieren des Windows-kompatiblen Schaltfläche Array-Geräts.

 - Verbinden Sie die Schaltfläche Power eine dedizierte GPIO Interrupt PIN.

 - Konfigurieren Sie die Power-Schaltfläche GPIO Interrupt Pin als ein nicht freigegeben, Aktivierung-fähige (ExclusiveAndWake) Rand ausgelöst (Edge) GPIO unterbrechen Verbindungsressource auf beide Ränder (ActiveBoth) unterbrochen werden können.

 - Die Power-Schaltfläche GPIO unterbrechen Verbindungsressource zunächst in des Schaltfläche Array Geräts Liste \_CRS-Objekt.

HINWEIS: Systeme, die einen separaten Treiber zum Verarbeiten von Power Tasten erfordern, ist es akzeptabel, diesen Aufrufen der 5-Tasten-Array Treiber Power Schaltfläche Ereignisschnittstelle statt der oben genannten GPIO basierende Lösung Treiber haben.

**Zeit- und Alarmgerät**

Alle Batterie-basiertes Systeme, die nicht unterstützen Standby verbunden sind, sind zum Implementieren der Alarm Funktionen des ACPI Zeit- und Alarm Steuerelement-Methode Geräts erforderlich.

Für alle Systeme, die verbunden Standby unterstützt, die die "CMOS RTC nicht vorhanden" festlegt bit in der IAPC\_BOOT\_BOGEN Flags dar, der die FADT muss die Funktionen des Geräts Zeit implementieren.


### <a name="systemfundamentalsfirmwarefirmwaresupportsbootingfromdvddevice"></a>System.Fundamentals.Firmware.FirmwareSupportsBootingFromDVDDevice

*System-Firmware unterstützt das Starten von DVD-Laufwerk gemäß der Spezifikation El Torito*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

System-Firmware muss System DVD gestartet, wenn das System eine DVD umfasst unterstützen. Die Option ROM oder System-Firmware muss den No Emulationsmodus für die Installation von Windows® von optischen Medien, wie beispielsweise startbaren DVD-Medien in der "El Torito" startbaren CD-ROM-Format-Spezifikation, Version 1.0, unterstützen. Primäre optische Laufwerk muss startbare. Dies gilt für den primären optischen Speicher und die primäre Bus mit dem das Gerät verbunden ist.


### <a name="systemfundamentalsfirmwarefirmwaresupportsusbdevices"></a>System.Fundamentals.Firmware.FirmwareSupportsUSBDevices

*System-Firmware bietet USB-Boot-Unterstützung für USB-Tastaturen, Maus und hubs*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Wenn das System bietet Unterstützung für USB-Tastaturen und zeigt Geräte, müssen die Systemfirmware: unterstützen USB-Tastaturen und zeigt Geräte beim Systemstart aus Ruhezustand und Betriebssystem-Setup und die Installation fortsetzen.

Unterstützung für USB Eingabegeräte mindestens drei Ebenen der physischen Hubs unter den Hostcontroller.

Wie in HID definiert ist, wird durch das Protokoll Boot unterstützen Sie zusammengesetzte Eingabegeräte.

Für Windows Server-Systeme ist akzeptabel, Aufzählen, jedoch nicht auf allen Geräten zu initialisieren. Wenn das Gerät zugegriffen wird, muss es vor dem Fortfahren vollständig initialisiert werden.

Die USB-Controller und USB-Geräten muss vollständig wann aufgelistet:

 - Alles außer den Windows-Start-Manager ist am oberen Rand der Startreihenfolge system
 - Eine nächste Boot-Variable wurde auf einen anderen Wert als Windows-Start-Manager starten festgelegt
 - Auf einem System, auf dem der Windows-Start-Manager am oberen Rand der Liste ist, hat ein Fehler Fall so, dass die Firmware aus den Windows-Start-Manager zum nächsten Element in der Liste ein Failover erreicht wurde,
 - Fortsetzen aus dem Ruhezustand, wenn das System Ruhezustand versetzt wurde, wenn von USB gestartet
 - Firmware-Setups wird zugegriffen.
 
### <a name="systemfundamentalsfirmwarehardwarememoryreservation"></a>System.Fundamentals.Firmware.HardwareMemoryReservation

*System.Fundamentals.Firmware.HardwareMemoryReservation*

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

Diese Anforderung begrenzt die Menge des Arbeitsspeichers, die von der Hardware (einschließlich Treiber oder Firmware) reserviert und nicht für das Betriebssystem oder Benutzer Clientanwendungen auf einem System verfügbar ist. Berücksichtigung der erforderlichen Änderungen an der diese Anforderung erfüllen, wird es stufenweise eingeführt werden. &lt;= 2GB Systeme – max 3 % + 25MB 2GB (86.5 MB)

 - 2-3GB Systeme – max 3 % von 3 GB + 25 MB (117,2 MB)

 - Für alle anderen Systeme, maximal 120MB

 - Wenn die Auflösung von 1366 x 768 überschreitet, die zusätzliche 8 Byte pro Pixel zulässig. Hinweis: Die oben genannten Budgets soll die 2 Vollbild Videospeicher Reservierungen für Grafiktreiber mit 1366 x 768 32 Bytes pro Pixel – 8 MB erfassen. Die oben genannten Anpassung dauert in Erwägung Maschinen mit einer höheren Auflösung.

| RAM-Größe | Bildschirmauflösung | Schwellenwert     |
|----------|-------------------|---------------|
| 1GB      | 1366 x 768          | 86.5 MB        |
| 2GB      | 1366 x 768          | 86.5 MB        |
| 2GB      | 1920 x 1080         | 86.5 MB + 8 MB  |
| / 3GB      | 1366 x 768          | 117,2 MB       |
| / 3GB      | 1920 x 1080         | 117.2 MB + 8 MB |
| 4GB      | Jede               | 120MB         |

Gilt für Windows-Clientbetriebssystem SKUs

**Hinweise zum Entwurf:**

 - Arbeitsspeicher, dass die Reservierung als die Differenz zwischen den physischen Speicher berechnet wird, der als für das Windows-Betriebssystem (mit Ausnahme von allen Gerätefirmware/Reservierungen) sichtbar zugeordnet ist, im Vergleich zu installierten RAM auf dem Computer.

Installierter Speicher wird über Abfrage [GetPhysicallyInstalledSystemMemory](http://msdn.microsoft.com/en-us/library/windows/desktop/cc300158.aspx) abgefragt und OS sichtbaren Speichers über [GlobalMemoryStatusEx](http://msdn.microsoft.com/en-us/library/aa366589.aspx) – UllTotalPhys abgefragt wird.


### <a name="systemfundamentalsfirmwarenoexternaldmaonboot"></a>System.Fundamentals.Firmware.NoExternalDMAOnBoot

*Alle externen DMA Ports müssen standardmäßig deaktiviert sein, bis das Betriebssystem sie explizit über verwandte Controllern schaltet.*

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

Die Firmware muss physischen Arbeitsspeicher von nicht autorisierten internen DMA (z. B. GPU beim Zugriff auf Speicher außerhalb von Video-spezifischen Speicher) und alle nicht autorisierten DMA-fähigen externen Ports vorherige während des Startvorgangs und solange der OS fährt DMA Ports über verwandte Controller Brücke zu starten, zu schützen. Wenn das Gerät ein Energiesparmodus eingibt, muss DMA Port Gerätekontext gespeichert und bei der Rückkehr zum aktiven Zustand wiederhergestellt werden.

Wenn Sie die Firmware verfügt über die Option aktivieren und deaktivieren diesen Schutz, darf die Konfiguration des Protokollversands mit Schutz sein aktiviert, und Aktivieren der Schutz deaktiviert, beispielsweise mit Plattform Authentifizierung über BIOS-Kennwort geschützt werden muss.

Beachten Sie, dass diese Anforderung die Verwendung von Speichermedien als Startmedien ausschließt, wenn nur über einen externen DMA-fähigen Port zugegriffen werden.


### <a name="systemfundamentalsfirmwareuefibitlocker"></a>System.Fundamentals.Firmware.UEFIBitLocker

*Ein System mit TPM, die in grafikbasierten verkabeltes LAN unterstützt EFI UEFI 2.3.1 unterstützen muss\_DHCP4\_PROTOKOLL Protokoll und UEFI 2.3.1 EFI\_DHCP6\_-PROTOKOLL (und die entsprechenden Service Bindung Protokolle).*

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

Unterstützung von Systemen die TPM und verkabelten LAN-Netzwerk unterstützen müssen EFI\_DHCP4\_EFI-Protokoll\_DHCP4\_SERVICE\_BINDEN\_PROTOKOLL, EFI\_DHCP6\_Protokoll und EFI\_DHCP6\_SERVICE\_BINDEN\_-PROTOKOLL für verkabelten LAN gemäß Definition im UEFI 2.3.1.

Beim vor dem Start muss BitLocker erkennen dessen Netzwerk entsperren Anbieter auf einem Windows Server (Deployment WDS) über DHCP, und des Betriebssystem-Volumes nach dem Abrufen eines geheimen Schlüssels aus WDS entsperren.

**Details** Alle UEFI Systeme mit TPM vorhanden und einem verkabelten LAN-Anschluss müssen BitLocker Netzwerk entsperren unterstützen. Dies erfordert vollständige DHCP-Unterstützung für verkabelten LAN während der Systemanalyse vor dem Start über einen UEFI DHCP-Treiber. Insbesondere muss vorhanden sein UEFI-Treiber Implementierungen für EFI\_DHCP4\_EFI-Protokoll\_DHCP4\_SERVICE\_BINDEN\_PROTOCOL, EFI\_DHCP6\_Protokoll und EFI\_DHCP6\_SERVICE\_BINDEN\_-PROTOKOLL für verkabelten LAN, wie in UEFI 2.3.1 definiert.

Diese Anforderung ist "Wenn implementiert" für Server-Systeme und gilt nur, wenn ein Server-System UEFI-fähig ist


### <a name="systemfundamentalsfirmwareuefibootentries"></a>System.Fundamentals.Firmware.UEFIBootEntries

*UEFI-Firmware berücksichtigt Softwarekontrolle über die Optionsvariablen laden.*

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

UEFI-Systemen müssen das Betriebssystem generische und Gerät bestimmte Starteinträge Messaging Gerät Pfad, insbesondere USB-Klasse Gerät (UEFI Version 2.3 Hauptfenster Spezifikation Abschnitt 9.3.5.9) So erstellen Sie mit zulassen. Die Firmware muss berücksichtigen diese Einstellungen und diese nicht ändern, nachdem das Betriebssystem geändert hat. Darüber hinaus muss die Firmware genau die Start-Einträge für das Betriebssystem melden.

**Funktionale Hinweise:**

Wenn das Gerät entsprechend der Boot-Eintrag nicht gefunden wird, empfiehlt es sich für das System, fahren Sie fort mit dem nächsten Boot-Eintrag im automatischen Modus (ohne eine Fehlermeldung Freigabe- oder Benutzereingriff).

Wenn das System von einem internen USB-Gerät gestartet wird und ein USB-Klasseneintrag am oberen Rand der Startreihenfolge vorhanden ist, versucht das System sollte zunächst, von externen USB-Geräten zu starten, bevor Sie versuchen, interne USB-Boot-Geräte.

**Hinweise zum Entwurf:**

Die UEFI-Spezifikation erfordert, dass der Software Bootmanager berechtigt, führen Sie die Startreihenfolge programming (UEFI V. 2,3 Abschnitt 3.1.1 "Start-Manager Programming").
Die Firmware sollte interpretieren Optionen laden und Gerätepfade wie angegeben in Abschnitt 9 "Protokolle - Gerät Path Protocol."

UEFI-Spezifikation beschreibt die Variablen, die zur Laufzeit in Abschnitt 3.2 Tabelle 10 geändert werden müssen.

Die Spezifikation UEFI ist unter <http://www.UEFI.org>verfügbar. Diese Anforderung ist "Wenn implementiert" für Server-Systeme und gilt nur, wenn ein Server-System UEFI Lage ist.


### <a name="systemfundamentalsfirmwareueficompatibility"></a>System.Fundamentals.Firmware.UEFICompatibility

*System-Firmware muss Windows-Kompatibilität Anforderungen erfüllen.*

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

Alle Systeme, die mit einer UEFI-kompatiblen OS ausgeliefert muss kompatibel mit den folgenden Abschnitten der UEFI 2.3.1 Spezifikation: 2.3, 3.1, 4.3 6.1 ~ 6.5, 7.1 ~ 7.5, 8.1, 8.2, 9.1, 9.5, 11.2 ~ 11.4 11,8, 11.9, 12.4, 12.7, 12,8, 12,9, 18.5, 21.1, 21.3:, 21,5, 27.1 ~ 27,8.

Weitere Anleitungen in aufgeführten "UEFI Support and Requirements: Microsoft Windows Server 2008" Dokument (verfügbar unter <http://www.microsoft.com/whdc/system/platform/firmware/uefireg.mspx>), sofern zutreffend, auch ist gehalten.

Alle Windows 8-Systeme müssen im UEFI Modus standardmäßig starten. Sonstige Anforderungen möglicherweise zusätzliche Abschnitte der Kompatibilität zu dieser Liste hinzufügen, jedoch Dies ist der Grundlinie.

Alle Systeme, mit Ausnahme von Servern, müssen im UEFI Modus ohne Aktivierung CSM zertifiziert sein. Wenn ein System mit 32-Bit- und/oder 64-Bit-UEFI verfügbar ist, müssen für die Zertifizierung für beide Konfigurationen getestet werden. Für Server, Zertifizierung im UEFI-Modus ist nur erforderlich, wenn UEFI implementiert wird.

OEMs können mit CSM-Modus aktiviert und das Unternehmen oder Behörden Auswahl des Kunden lizenzierte OS bei Bedarf.


### <a name="systemfundamentalsfirmwareuefidefaultboot"></a>System.Fundamentals.Firmware.UEFIDefaultBoot

*Alle Clientsysteme müssen in UEFI Startmodus gestartet werden, und versuchen Sie in diesem Modus standardmäßig starten.*

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

System-Firmware muss UEFI Startmodus standardmäßig zu erreichen können.  Einem solchen System unterstützt möglicherweise auch Fallback zu legacy BIOS-Startmodus für die Bereitstellung von OS Bilder, die keine für UEFI Unterstützung, wenn der Benutzer explizit auf die entsprechende Option im Menü UEFI BIOS vor dem Start auswählt.

Dies ist "Wenn implementiert" für Server-Systeme.


### <a name="systemfundamentalsfirmwareuefilegacyfallback"></a>System.Fundamentals.Firmware.UEFILegacyFallback

*System-Firmware muss auf BIOS-Legacymodus ohne explizite Benutzer-Aktion nicht zurückgreifen.*

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

Wenn das System mit einer UEFI-kompatiblen OS verwendet werden soll, muss System-Firmware implementiert werden wie UEFI und es UEFI Startmodus zu erreichen können, müssen in der Standardeinstellung.  Einem solchen System unterstützen möglicherweise auch Fallback zum Starten der Vorversion BIOS auf Systeme mit OS die UEFI, nicht unterstützen, aber nur wenn der Benutzer die Option in einer vor dem Start Firmware-Benutzeroberfläche wählt. Legacy Option ROM kann auch nicht standardmäßig geladen werden.

"Explizite Benutzeraktion" bedeutet, dass dieser Endbenutzer (oder im Fall eines WAN-Enterprise "Kunde", die für IT-Experten) müssen manuell Zugriff auf dem Bildschirm vor dem Start Firmware Konfiguration und ändern Sie die Einstellung. Es kann nicht im BIOS-Modus standardmäßig ausgeliefert und programmatische Methoden, die von Malware Angriff werden können, sind nicht zulässig.

Alle Systeme mit Klasse 2 UEFI darf keine auf BIOS-Legacymodus zurückgreifen oder laden legacy Option ROM ohne explizite Benutzer-Aktion innerhalb der vor dem Start UEFI Konfigurationsbenutzeroberfläche."
OEM möglicherweise keine 64-Bit-System gehören, die standardmäßig-legacy-BIOS oder legacy Option ROM geladen wird, wenn das System eine UEFI-kompatiblen OS Lieferumfang.

Wenn Secure Boot aktiviert ist, müssen die Kompatibilität Support Module (CSM) NICHT geladen werden. Kompatibilität unterstützen Module werden immer auf Systeme nicht zulässig, die verbundenen Standby unterstützen. 

Diese Anforderung ist "Wenn implementiert" für Server-Systeme und gilt nur, wenn ein Server-System UEFI Lage ist.


### <a name="systemfundamentalsfirmwareuefisecureboot"></a>System.Fundamentals.Firmware.UEFISecureBoot

*Alle Clientsysteme müssen UEFI Secure Boot unterstützen.*

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

Hinweis: Diese Anforderungen für Server-Systeme werden "Wenn implementiert" und gilt nur, wenn ein Server-System UEFI Secure Boot unterstützt.


<ol style="list-style-type: decimal">
<li><p>Sichere Boot muss mit minimalen UEFI 2.3.1 Fehlerverzeichnis c aktiviert liefern.</p></li>
<li><p>Für die Zwecke UEFI Secure Boot, die Plattform dürfen zur Verfügung stellen einer Schnittstelle zum Secure starten, bei dem die System-Firmware kompatibel mit den folgenden Abschnitten und Unterabschnitten der UEFI Version 2.3.1 ist Fehlerverzeichnis C:</p>
<ol style="list-style-type: lower-alpha">
<li><p>7.1</p></li>
<li><p>7.2</p></li>
<li><p>7.2.1</p></li>
<li><p>27.2</p></li>
<li><p>27,5-27,8 (wie weiter unten Profil).</p></li>
</ol>
</li>

<li><p>UEFI Version 2.3.1 Fehlerverzeichnis C Variablen müssen festgelegt werden, um SecureBoot = 1 und SetupMode = 0 mit einer Signatur-Datenbank (EFI_IMAGE_SECURITY_DATABASE) erforderlich, starten Sie den Computer sicher vorab bereitgestellt, und schließen Sie PS, die festgelegt ist und eine gültige KEK-Datenbank. Das System diese Datenbank verwendet, um sicherzustellen, dass nur vertrauenswürdigen Code (z. B.: vertrauenswürdigen signierten des Startladeprogramms) initialisiert wird, und, dass eine nicht signierte Bild oder ein Bild, die von einem nicht autorisierten Herausgeber signiert ist, wird nicht ausgeführt. Der Inhalt der Signaturdatenbank ergeben sich die OEM basierend auf die erforderlichen systemeigenen und Drittanbieter-UEFI-Treiber, jeweiligen wiederherstellungsanforderungen und den OS des Startladeprogramms auf dem Computer installiert. Die folgende Signatur von Microsoft bereitgestellten EFI_CERT_X509 aufzunehmenden in der Signaturdatenbank: &quot;CN = Microsoft Windows Produktion PCA 2011&quot; und &quot;Cert Hash(SHA1):: 58 0a 6f 4c c4 e4 b6 69 b9 Eb dc 1 b 2 b 3e 08 7 b 80 d0 67 8 d&quot; dem so verwenden Sie die folgenden SignatureOwner GUID: {77fa9abd-0359-4 d 32-bd60-28f4e78f784b}, muss auch in Form einer EFI_CERT_X509_GUID oder EFI_CERT_RSA2048_GUID enthalten sein :</p>


<ol style="list-style-type: lower-alpha">
<li><p>Hinweis: Muss das folgende Zertifikat NICHT enthalten: &quot;CN = Microsoft Windows PCA 2010&quot; und &quot;Cert Hash(SHA1):: c0 13 86 a9 07 49 64 04 f2 76 c3 c1 85 3a bf 4a 52 74 af 88&quot;</p></li>
<li><p>Hinweis II: WindowsServer-Systeme können im Lieferumfang von Secure Boot deaktiviert, aber alle anderen Vorschriften dieser untergeordnete Anforderung erfüllt sein müssen</p></li>
</ol></li>
<li><p>Wenn Secure Boot aktiviert ist, müssen die Kompatibilität Support Module (CSM) NICHT geladen werden.</p></li>
<li><p>Die anfänglichen UEFI Signatur Datenbanken (Db) müssen mit dem EFI_VARIABLE_TIME_BASED_AUTHENTICATED_WRITE_ACCESS-Attribut in der Firmware flash gespeichert erstellt werden und können nur mit einer Aktualisierung Firmware OEM-signiert oder über UEFI authentifizierten Variable Write aktualisiert werden.</p></li>
<li><p>Unterstützung für die UEFI &quot;verboten&quot; Signaturdatenbank (EFI_IMAGE_SECURITY_DATABASE1) implementiert werden muss.</p></li>
<li><p>Die Plattform ist im Lieferumfang von einer &quot;verboten&quot; Signaturdatenbank (EFI_IMAGE_SECURITY_DATABASE1) mit dem Attribut EFI_VARIABLE_TIME_BASED_AUTHENTICATED_ACCESS erstellt. Wenn die Signaturdatenbank verbotene beim Neustarten eine Signatur hinzugefügt wird muss beliebiges Bild mit dieser Signatur zertifiziert nicht Initialize/ausführen dürfen.</p></li>
<li><p>Sichere Boot muss in einem öffentlichen Schlüssel geschützten oder ROM-basierten Stamm haben. Sichere Boot muss in einer öffentlichen RSA-Schlüssel mit einer Modulogröße von mindestens 2048 Bit zurückgehen werden und entweder in unveränderlich ROM produktbasiert oder andernfalls geschützt werden vor Änderung von einem sicheren Firmware Update-Prozess wie nachstehend definiert.</p></li>
<li><p>Die Aktualisierung Firmware zu sichern. Wenn die Plattform Firmware ist, die gewartet werden, muss es einen sicheren Aktualisierungsvorgang folgen. Um sicherzustellen, dass der untersten Ebene Code Schicht nicht beeinträchtigt wird, muss die Plattform die Aktualisierung einer sicheren Firmware zu unterstützen, die wird sichergestellt, dass nur signierte Firmware-Komponenten, die mit der Signaturdatenbank überprüft werden können (und nicht von der Signaturdatenbank verbotene für ungültig erklärt) installiert werden können. UEFI Boot Services Variablen müssen Hardware geschützt und alle Updates flash beibehalten werden. Die Flash-ROM, die den UEFI BIOS-Code speichert müssen geschützt werden. Flash, das in der Regel an (auf authentifizierte Firmwareupdates zulassen) zurücksetzen geöffnet ist muss vor dem Ausführen nicht autorisierten Codes anschließend gesperrt werden. Aktualisierung der Firmware zu muss auch gegen Rollback auf unsichere oder nicht in der Produktion Versionen, die möglicherweise Secure Boot deaktivieren oder nicht in der Produktion Schlüssel schützen. Ein physisch Benutzer kann jedoch den Rollback Schutz manuell außer Kraft setzen. In diesem Fall (wo des Schutzes Rollback außer Kraft gesetzt ist) muss das TPM deaktiviert werden. Darüber hinaus wird empfohlen, dass Hersteller BIOS Code schreiben entsprechen den NIST Leitlinien in SP NIST 800-147 (http://csrc.nist.gov/publications/nistpubs/800-147/NIST-SP800-147-April2011.pdf), BIOS Protection-Richtlinien, die bietet Richtlinien zum Erstellen von Features in das BIOS, mit deren Hilfe sie geändert oder beschädigt, indem Angreifer zu schützen. Beispielsweise aktualisiert mithilfe von kryptografischen digitalen Signaturen zum Authentifizieren BIOS.</p></li>
<li><p>Überprüfung der Firmware Code Integrität angemeldet. Firmware, die vom OEM installiert ist und ist schreibgeschützt oder durch die Aktualisierung einer sicheren Firmware zu, wie oben, definiert erwogen werden geschützt. Systeme prüft, dass alle Komponenten ungeschützte Firmware, UEFI-Treiber und UEFI Applications SHA-256 mit minimalen RSA-2048 angemeldet sind (MD5 und SHA-1 sind nicht zulässig), und stellen Sie sicher, dass UEFI-Anwendungen und Treiber, gemäß den Anweisungen in diesen Anforderungen nicht signiert sind, ein Fehler auftritt, ausführen (Dies ist die Standardrichtlinie für gültigen Signaturalgorithmen). Wenn eine Signatur Bilder nicht in der autorisierten Datenbank gefunden wird oder in der unzulässige Datenbank gefunden wird, das Bild muss nicht gestartet werden, und stattdessen Informationen sind in der Tabelle mit den Bild Ausführung platziert werden.</p></li>
<li><p>UEFI Firmware und Treiber Implementierungen muss gegen böswillige Eingaben von nicht vertrauenswürdigen Quellen. Unvollständige eingabevalidierung möglicherweise Pufferüberläufe, überschreibt Integer und Zeiger Beschädigung, Arbeitsspeicher und andere Sicherheitslücken, beeinträchtigen die Laufzeit Integrität der authentifiziert UEFI Komponenten.</p></li>
<li><p>Überprüfen Sie Signatur aller Boot Apps und Boot Ladeprogramme. Beim Einschalten die Plattform Boot Firmware Ausführung beginnt und öffentlichem Schlüssel gemäß der Richtlinie Algorithmus zum Überprüfen der Signaturen aller Bilder in den Boot Sequenz bis zur und einschließlich des Start-Managers von Windows verwenden.</p></li>
<li><p>Microsoft Schlüssel Encryption Key (KEK) bereitgestellt ist eine gültige Microsoft bereitgestellten KEK ist in der Datenbank KEK enthalten. Microsoft bietet die KEK in Form von entweder eine EFI_CERT_X509_GUID oder EFI_CERT_RSA2048_GUID Typsignatur. Die Microsoft KEK Signatur verwendet die folgenden SignatureOwner GUID: {77fa9abd-0359-4d32-bd60-28f4e78f784b}.</p></li>
<li><p>PKpub Überprüfung. Der Schlüssel PKpub ist Besitz des OEMs und im Firmware flash gespeichert. Das Private Schlüssel Gegenstück zur PKpub ist PKpriv, der Richtlinie auf alle OEM hergestellten Geräten Secure Boot steuert, und den Schutz und zur Nutzung müssen vor nicht autorisiertem Verwendung oder Offenlegung gesichert werden. PKpub muss vorhanden sein und muss das Betriebssystem lesen den Wert, und stellen Sie sicher, dass sie mit der richtigen Schlüssellänge vorhanden ist.</p></li>
<li><p>Keine Inline-Mechanismus wird vorausgesetzt, bei dem ein Benutzer Secure Boot-Fehlern umgehen und trotzdem starten kann, Signatur Überprüfung außer Kraft setzen während des Startvorgangs bei aktiviertem Secure Boot nicht zulässig ist. Eine physisch Benutzer Überschreibung darf nicht für UEFI Bilder, die beim Starten von signaturüberprüfung fehlschlagen. Wenn ein Benutzer ein Bild zu starten, die Überprüfung der Signatur nicht erfolgreich ausgeführt wird möchte, müssen sie auf dem Zielsystem explizit Secure Boot deaktivieren.</p></li>
<li><p>UEFI nutzt und zugehörige Applikationen. UEFI Module, die nicht erforderlich sind, um die Plattform zu starten müssen nicht von Kehrmatrix Produktion Zertifikaten signiert werden &quot;Db&quot;wie UEFI Applications setzen Sie die Sicherheit des Secure Boot herab können. Beispielsweise Dies umfasst und ist nicht auf UEFI nutzt sowie Fertigung beschränkt, zu testen, Debuggen RMA &amp; Außerbetriebnahme Tools. Mit diesen Tools und nutzt muss erfordern, dass ein Plattformadministrator Secure Boot deaktiviert.</p></li>
<li><p>Sichere Boot Variable. Die Firmware wird die Variable SecureBoot implementieren, wie im Abschnitt 3.2 dokumentiert &quot;global definierten Variablen UEFI-Spezifikationsversion 2.3.1 Fehlerverzeichnis c&quot;</p></li>
<li><p>Geräte zum immer mit einer bestimmten Secure Startkonfiguration boot vorgesehen sind, sind die beiden folgenden Anforderungen zur Unterstützung von benutzerdefinierten Modus und die Möglichkeit, Secure Boot deaktivieren optional.</p></li>
<li><p>Auf nicht-ARM-Systemen, die Plattform MUSS die Möglichkeit physisch Benutzer wählen Sie zwischen zwei Secure Boot Modi während des Setups von Firmware implementieren: &quot;benutzerdefinierte&quot; und &quot;Standard&quot;. Benutzerdefinierter Modus ermöglicht mehr Flexibilität gemäß der folgenden:</p>
<ol style="list-style-type: upper-alpha">
<li><p>Es muss ein physisch Benutzer die Option benutzerdefinierte Modus Firmware Setup verwenden Sie zum Ändern des Inhalts der Secure Boot Signatur Datenbanken und die PS. möglich sein. Dies kann implementiert werden, indem Sie einfach die Option zum Löschen aller Secure Boot-Datenbanken (PK, KEK, Db, Dbx), die das System in den Installationsmodus versetzt.</p></li>
<li><p>Wenn der Benutzer dann Löschen der PK beim Beenden des benutzerdefinierten Modus Firmware-Setups beendet ist das Betriebssystem im Setup-Modus mit SecureBoot deaktiviert.</p></li>
<li><p>Der Firmware-Setups vermerkt, wenn Secure Boot eingeschaltet ist und sie als Standard Edition oder benutzerdefinierten Modus ausgeführt wird. Der Firmware-Setups muss eine Option, um benutzerdefinierte auf den Standardmodus zurückgeben, die wiederhergestellt, die Standardwerte für das bereitstellen. Für ein System ARM ist es verboten benutzerdefinierte Modus aktivieren. Standard-Modus aktiviert werden kann.</p></li>
</ol></li>
<li><p>Sichere Boot aktivieren/deaktivieren. Ein Benutzer physisch dürfen Secure Boot über Firmware Setup ohne Besitz eines PKpriv deaktivieren. Deaktivieren eines Servers Windows möglicherweise auch Secure Boot Remote über einen authentifizierten (vorzugsweise öffentlichen Schlüssel basierend) Out-of-Band-Management-Verbindung, beispielsweise auf einem Baseboard Management Controller oder Service-Prozessor. Programmgesteuerte Deaktivierung des Secure Boot während Boot-Dienste oder nach dem Beenden des EFI Boot-Dienste MÜSSEN NICHT möglich. Deaktivieren von Secure Boot muss nicht auf ARM-Systemen möglich sein.</p></li>
<li><p>Wenn die Firmware auf die Standardwerte zurücksetzen, und klicken Sie dann auf alle benutzerdefinierten Secure Boot-Variablen wird werden auch Factory zurückgesetzt. Wenn die Einstellungen der Firmware auf die Standardwerte zurückgesetzt werden, alle benutzerdefinierten-Set-Variablen werden gelöscht, und der OEM-PKpub zusammen mit der ursprünglichen, die vom Hersteller bereitgestellte Signatur Datenbanken wiederhergestellt werden.</p></li>
<li><p>OEM-Mechanismus zum Warten von fehlerhafte EFI Boot Komponenten bis zum, einschließlich den Windows-Betriebssystem Loader ("Bootmgr.EFI") vorhanden ist. Bilder im Pfad Boot EFI, die nicht von signaturüberprüfung Secure Boot MÜSSEN nicht ausgeführt werden, und der Eintrag EFI_IMAGE_EXECUTION_INFO_TABLE für diese Komponente wird mit den Grund für den Fehler aktualisiert werden. Der Start-Manager für UEFI leitet Wiederherstellung nach einem OEM-spezifische Strategie für alle Komponenten bis zum und einschließlich Windows "Bootmgr.EFI".</p></li>
<li><p>Eine funktionsfähige Windows RE-Abbild darf vorhanden auf alle Fenster sein Clientsysteme sein muss, die Wiederherstellung der Windows-Bild im Bild Factory auf jedem Secure Boot-fähige System darstellen. Zur Unterstützung von automatisierte Wiederherstellung, und geben Sie einen positiven Eindruck auf Secure Boot-Systemen, muss das Windows RE-Abbild vorhanden und standardmäßig aktiviert. Im Rahmen der Arbeit Windows vertrauenswürdige Boot Verbesserungen Windows RE wurden, optimierte Wiederherstellung aus Signatur Überprüfung mit Fehlern in Secure Boot zuzulassen. OEMs müssen Windows RE als Teil ihres Bilds Factory auf allen Windows-Client-Systemen enthalten.</p></li>
<li><p>Firmware-basierte Sicherung und Wiederherstellung. Wenn der OEM einen Mechanismus zum backup kritische Startdateien bietet (zum Beispiel: EFI-Treiber und Starten von Clientanwendungen), an einem sicheren Ort nur zugänglich und von der Firmware gewartet werden muss. Der OEM kann die Kapazität über Firmware oder andere backup zu speichern Sicherungskopien der kritischen Startdateien und Wiederherstellungstools enthalten. Wenn solche ein Speicher implementiert wird, muss die Lösung auch die Möglichkeit zum Wiederherstellen der Zieldatei auf dem System ohne die Notwendigkeit für externe Medien oder Benutzereingriffe verfügen. Dies ist ein Unterscheidungsmerkmal für OEM im Failover-Schutz verwendet, wenn das Windows-Betriebssystem-Ladeprogramm ("Bootmgr.EFI") oder andere wichtige Komponenten Boot ausfallen, verhindern, dass Windows systemeigene Recovery Solutions ausführen.</p></li>
<li><p>Firmware-basierte backup-Synchronisierung. Sicherungskopien der wichtigen Komponenten Boot (zum Beispiel: EFI-Treiber, und starten Sie Applikationen) Kehrmatrix Firmware muss mit Updates auf dieselben Dateien auf dem System, wenn das System die Möglichkeit zum Speichern von einer Sicherungskopie der Ladeprogramm des Windows-Betriebssystem ("Bootmgr.EFI"), und potenziell andere wichtige Boot Komponenten, und klicken Sie dann auf die Dateien auf dem gleichen Zeitplan wie die entsprechenden auf live-System verwendeten bedient werden müssen synchronisiert bedient werden. Wenn das Windows-Betriebssystem Ladeprogramm von Windows Update aktualisiert wird, muss die Sicherungskopie in der Firmware gespeichert "Bootmgr.EFI" beim nächsten Start aktualisiert werden.</p></li>
<li><p>Alle Windows-Clientsysteme müssen eine sekundäre Startpfad unterstützen. Für alle Windows-Systeme für Secure Boot konfiguriert sind muss eine alternative Boot-Pfad-Option, die von der Firmware des Telefonfestnetzes verwendet wird, wenn das primäre Windows-Betriebssystem Ladeprogramm vorhanden sein. Der zweite Startpfad möglicherweise zeigen Sie entweder auf die Standard-Schattenkopie von Windows installiert ist, im System backup-Speicher (&lt;EFI Systemvolume&gt;\EFI\Boot\boot&lt;Plattform&gt;.efi), oder um eine Kopie von der Firmware-basierte OEM-Mechanismus gespeichert. Diese alternative Pfad einer Datei in ausführbaren Speicher sein, oder, zeigen Sie auf ein Firmware-basierte Remediation-Prozess, der eine Kopie außerhalb der OEM setzt vordefiniert backup-Speicher.</p></li>
<li><p>Alle Windows-Clientsysteme müssen ein USB-Startpfad zu Wiederherstellungszwecken unterstützen. Für alle Windows-Systemen für Secure Boot konfiguriert ist Notfall von USB aus gestartet.</p></li>
<li><p>Unterstützung für GetVariable() für die EFI_IMAGE_SECURITY_DATABASE (autorisiert und verboten Signaturdatenbank) und die SecureBoot-Variable.</p></li>
<li><p>Unterstützende SetVariable() für den EFI_IMAGE_SECURITY_DATABASE (autorisiert und verboten Signaturdatenbank), einen autorisierten KEK zur Authentifizierung mit.</p></li>
<li><p>Reservierter Speicher für Windows sicheren Boot UEFI Variablen. Insgesamt mindestens 64 KB unveränderliche NVRAM-Speicher für NV UEFI (authentifizierten und nicht authentifizierten, BS und RT) verwendeten Variablen von UEFI Secure Boot und Windows reserviert werden muss, und die maximale Größe des unterstützte Variable muss mindestens 32kB sein. Es ist keine maximale NVRAM Speichergrenzwert aus.</p></li>
<li><p>Während der normalen Firmware müssen die folgenden Updates beibehalten werden:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Status des Starts Secure &amp; Konfiguration (PS, KEK, Db, Dbx, SetupMode, SecureBoot)</p></li>
<li><p>Alle UEFI Variablen mit VendorGuid {77fa9abd-0359-4d32-bd60-28f4e78f784b}</p></li>
<li><p>Ein physisch vorhandene Benutzer der Firmware authentifiziert möglicherweise ändern, zurücksetzen oder löschen Sie diese Werte</p></li>
</ol></li>
<li><p>Die Plattform muss EFI Variablen unterstützen, die sind:</p>
<ol style="list-style-type: lower-alpha">
<li><p>nur während der Boot-Dienste verfügbar oder auch in der Phase der Common Language Runtime zugänglich;</p></li>
<li><p>unveränderliche; und</p></li>
<li><p>Möglich, nur nach ordnungsgemäße Autorisierung zu aktualisieren ordnungsgemäß signiert wird.</p></li>
</ol></li>
<li><p>Die Plattform muss EFI Variablen mit eine beliebige gültige Kombination der folgenden UEFI 2.3.1 unterstützen Variable Attribute festgelegt:</p>
<blockquote>
<p>Kopie</p>
<p>EFI_VARIABLE_NON_VOLATILE</p>
<p>EFI_VARIABLE_BOOTSERVICE_ACCESS</p>
<p>EFI_VARIABLE_RUNTIME_ACCESS</p>
<p>EFI_VARIABLE_AUTHENTICATED_WRITE_ACCESS</p>
<p>EFI_VARIABLE_APPEND_WRITE</p>
<p>EFI_VARIABLE_TIME_BASED_AUTHENTICATED_WRITE_ACCESS</p>
</blockquote>
</li>
<li><p>Microsoft UEFI CA-Schlüssel MUSS in SecureBoot DB enthalten sein, es sei denn, die Plattform konzipiert, alle die 3<sup>rd</sup> Partei UEFI-Erweiterungen blockiert.</p></li>
<li><p>Auf dem neuesten Stand DBX Content Out-of-the-Box müssen im Lieferumfang von allen Windows-Client-Systemen.</p></li>
<li><p>Plattform verfügbar machen DbDefault, DbxDefault, KEKDefault, &amp; PKDefault für das Lesen vom Betriebssystem zugegriffen werden.</p></li>
<li><p>[Wenn implementiert] Wenn Plattform mit Unterstützung für den sicheren Bereitstellung des angepassten Start (Revision 1263, Abschnitt 30.3) mit UEFI 2.5 enthalten ist, MUSS das Gerät im Modus bereitgestellten liefern. Geräte können vom Unternehmenskunden, die im Benutzermodus für benutzerdefinierte Orders geliefert werden.</p></li>
<li><p>[Wenn implementiert] Wenn Plattform mit UEFI 2.5 mit Unterstützung für HTTP-Boot (Revision 1214, Abschnitt 23.7) enthalten ist, muss die Clientverbindung mit dem Server auf einen starken Serverauthentifizierung basieren. Im Fall eines WAN-HTTP muss es HTTPS mit minimalen EV SSL-Authentifizierung oder die einer ähnlichen Gruppe sein.</p></li>
<li><p>[Wenn implementiert] Wenn Plattform mit UEFI 2.5 mit Unterstützung für die Plattform Wiederherstellung (Revision 1227, Abschnitt 23.7) enthalten ist, MUSS Plattform auch HTTP-Boot unterstützen wie bereits erwähnt.</p></li>
<li><p>[Wenn implementiert] Wenn UEFI 2.5 Plattform Lieferumfang bereitstellen MUSS der Plattform konsistente Secure Boot Workflows wie im Dokument "Windows konsistente Secure Boot Workflows" (in diesem Dokument steht auf CONNECT) angegeben.</p></li>
</ol>



### <a name="systemfundamentalsfirmwareuefitimingclass"></a>System.Fundamentals.Firmware.UEFITimingClass

*System-Firmware muss Timing und Klasse Informationen verfügbar machen.*

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

 - Während des POST wird Firmware eine eigene Timing messen und die Dauer des Beitrags, gerundet auf das nächstliegende MS aufzeichnen.

 - Diese Anzeigedauer gemessen werden in der Regel Reset-Sequenz (notiert haben am Anfang der BIOS-Initialisierung – normalerweise unter zurücksetzen Vektor Timer-Wert) Übergabe an OS Loader.


### <a name="systemfundamentalsfirmwareupdate"></a>System.Fundamentals.Firmware.Update

*System-Firmware muss die Anforderungen in der Reihenfolge, um die Unterstützung der vom System und/oder Gerät Firmwareupdates mit Firmware Treiberpakets erfüllen.*

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

Diese Anforderungen müssen von einem System erfüllt sein, mit die System und/oder Gerät Firmware mithilfe des Windows-Firmware Treiber Paket Mechanismus aktualisiert.

 - Die Tabelle ESRT muss mindestens eine Ressource der Firmware (ESRE) in der Ressourcenliste definieren die Firmware Systemressource enthalten muss.

 - Nur ein einziges System Firmware Ressource kann in der ESRT definiert werden.
 
 - Keine zwei Ressourcen in der Tabelle ESRT dürfen die gleiche Firmware-Klasse GUID haben.
 
 - ESRE muss entsprechenden Statuscode einschließlich Erfolg oder Fehler bei der Firmware Update Versuch, auf die nachfolgenden Boot, an das Betriebssystem.
 
 - Für jede Ressource, die von den ESRT definierten Firmware muss erweiterbar auf eine neuere version
 
 - Firmware-Version für eine bestimmte Ressource muss Kompatibilität mit Firmwareversionen von anderen Ressourcen nicht aufgehoben werden.
 
 - Firmware muss die niedrigste unterstützten Firmwareversion über das Feld "LowestSupportedFirmwareVersion" in der Tabelle ESRE bereitstellen. Firmware darf keine Rollback auf eine beliebige Version niedriger als die niedrigste unterstützte Version zulassen. Wenn ein Wertpapier, dass die Aktualisierung erfolgreich durchgeführt wurde verbunden, muss dieses Feld entsprechend das Feld "FirmwareVersion" die ESRE aktualisiert werden. Wenn die niedrigste Firmwareversion nicht die aktuelle Firmwareversion übereinstimmt, muss Firmware Rollbacks auf eine beliebige Version zwischen der aktuellen Version und die niedrigste unterstützte Version, der (einschließlich) gestatten.

 - Firmware muss nahtlos von Updatefehlern Versuche wiederhergestellt, falls noch nicht an das Betriebssystem Steuerelement übertragen, nachdem ein Update angewendet wird.


## <a name="systemfundamentalsfirmwareboot"></a>System.Fundamentals.Firmware.Boot

*In diesem Abschnitt wird beschrieben, Boot-Anforderungen für alle Clientsysteme.*


### <a name="systemfundamentalsfirmwarebooteithergraphicsadapter"></a>System.Fundamentals.Firmware.Boot.EitherGraphicsAdapter

*System-Firmware muss ein System mit Grafiken integriert und mit mehreren Grafikkarten gestartet sein.*

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

Systeme mit GPUs auf der Hauptplatine und mobile Systeme, die eine Dockingstation mit PCI-Steckplätze verwenden können müssen im System Firmware-Setup-Dienstprogramm integrierten Grafik verwenden zum Starten des Systems Verzuges werden können. Diese Funktion ist erforderlich, damit das Gerät integrierten Grafik in einer Konfiguration mit mehreren Monitoren und für hot Trennvorgang ein mobiles System verwendet werden kann.
Wenn das System PCI, AGP- oder PCI Express-Steckplätze umfasst, muss die Systemfirmware ein System mit mehreren Grafikkarten gestartet sein.  System-BIOS müssen legen Sie ein Gerät als VGA-Gerät und VGA auf allen anderen Adaptern deaktivieren.  Ein System mit einer integrierten Grafik-Chipsatz und einen oder mehrere separate Grafikkarten muss möglicherweise den Grafikchipsatz integrierte deaktivieren, wenn der integrierte Grafikchipsatz als einen Chipsatz-VGA-Funktion kann nicht.


### <a name="systemfundamentalsfirmwarebootsystemwithbootdevicegreaterthan"></a>System.Fundamentals.Firmware.Boot.SystemWithBootDeviceGreaterThan

*Systeme mit einem Boot-Gerät mit einer Kapazität größer als 2,2 TB müssen Anforderungen entsprechen.*

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

Systeme mit einem Boot-Gerät mit einer Kapazität größer als 2,2 TB müssen die folgenden Anforderungen erfüllen:

 - Das System muss die 64-Bit-Version.

 - Das System muss die UEFI Anforderungen in den Abschnitt system.fundamentals.firmware entsprechen.

 - Erweiterte Konfiguration und Power Interface (ACPI) Spezifikation Version 4.0 muss das System einhalten. Insbesondere muss das System veraltete oder Betriebssystem veranlasst Konfigurations- und Power Management (OSPM) unterstützen / ACPI-Modus.


## <a name="systemfundamentalsfirmwarecs"></a>System.Fundamentals.Firmware.CS

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsfirmwarecscryptocapabilities"></a>System.Fundamentals.Firmware.CS.CryptoCapabilities

*System, die Standbymodus verbunden unterstützen muss Verschlüsselungsfunktionen Kunden erwarten auf Plattform Geschwindigkeit und Leistung erfüllen enthalten.*

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

Da alle Komponenten in der Startpfad ebenso wie viele wichtige Leistung OS Subsysteme kryptografische Funktionen aufruft, ist die Leistung dieser Funktionen zur Laufzeit wichtig. Die folgenden Anforderungen haben entworfen wurde, um sicherzustellen, dass ausreichend Verschlüsselungsfunktionen Kunden erwarten auf Plattform Geschwindigkeit und Leistung erfüllt sind:

<ol style="list-style-type: decimal">
<li><p>Die Plattform muss kryptografische leistungsanforderungen erfüllen, wie in Tabelle 1 angegeben. Die Plattform kann durch eine beliebige Kombination von Hardware- oder diesen Anforderungen entsprechen. Die folgenden allgemeinen Anmerkungen gelten für alle-Algorithmen sind in der folgenden Tabelle:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Ziel-Leistung muss in einem Multithreaded Test erzielt werden. Die Anzahl der Threads richtet sich nach der Eigenschaft mit dem Namen L Abfragen&quot;HardwareThreads&quot; auf dem BCrypt Anbieter über die BCryptGetProperty CNG-Schnittstelle. Der Anbieter ist erforderlich, um einen DWORD-Wert in der Antwort zurückzugeben. Wenn der Anbieter diese Eigenschaft nicht unterstützt, wird der Test Einzel-Thread ausgeführt.</p></li>
<li><p>Wenn kryptografische Acceleration Module verwendet werden: aufgrund der Aufwand beim Verteilen Anforderungen an Hardware Acceleration Module, wird empfohlen, dass kleine Anfragen in Software verarbeitet werden. Es wird auf ähnliche Weise empfohlen, Lieferanten erwogen werden CPU-basierte Kryptografie zur Verbesserung des Datendurchsatzes, wenn alle kryptografischen Acceleration Module werden genutzt, im Leerlauf Kapazität auf die CPU steht und das Gerät in einen Modus für hohe Leistung wird (beispielsweise wenn an Stromversorgung angeschlossen).</p></li>
</ol></li>
<li><p>ARM-basierte Plattformen müssen die EFI_HASH_PROTOCOL aus der Branche UEFI, Unified Extensible Firmware Interface Specification Version 2.3.1 Fehlerverzeichnis b implementieren. Die Implementierung EFI_HASH_PROTOCOL muss aus der Windows-Betriebssysteme vor dem Systemcode (d. h. in der Phase Boot Services Plattform Starts) zugreifen können. Sowohl die UEFI Hash-Protokolle EFI_HASH_ALGORITHM_SHA1_NOPAD_GUID und EFI_HASH_ALGORITHM_SHA256_NOPAD_GUID müssen unterstützt werden und muss die Implementierung unterstützen, übergeben einen langen Nachricht mindestens 10 MB (Hinweis: ohne Abstand zu einem beliebigen Zeitpunkt auf die eingegebenen Daten angewendet werden muss). </p></li>
<li><p>Entropie Generation Funktionen auf Windows-Betriebssysteme vor dem Systemcode zur Verfügung zu stellen, wird die Plattform die EFI_RNG_PROTOCOL für die Überprüfung vor dem Operating System Lesen von mindestens 256 Bits Entropie in einem einzigen Aufruf (d. h. 256 Bits des vollständigen Entropie aus einer Datenquelle mit Sicherheitsstärke von mindestens 256 Bits) unterstützen. Die Protokolldefinition finden Sie im Microsoft Corporation, &quot;UEFI Entropie zum Erfassen von-Protokoll&quot;<sup>2</sup>.</p></li>
<li><p>Alle Verschlüsselungsfunktionen gemäß Tabelle 1 sind die Laufzeit OS im Kernelmodus, über die Schnittstelle im Microsoft Corporation, angegebene zugegriffen werden kann &quot;BCrypt Profil für SoC-Beschleunigern&quot; <sup>2</sup> .</p></li>
<li><p><strong>OPTIONAL.</strong> Es wird empfohlen, dass die Plattform Verschlüsselungsfunktionen auch von der Laufzeit OS im Benutzermodus, über die Schnittstelle, die zuvor in der Anforderung 4 verwiesen zugegriffen werden kann.</p></li>
<li><p>Die OS Interface-Bibliothek wird in einer Weise durchgeführt, wenn ein Prozess, der nicht privilegierten auf einem bestimmten Schlüssel in einem bestimmten Kontext ausgeführt wird, es nicht möglich ist das Schlüsselmaterial zugreifen oder anderen Kontexten zugeordnete wichtige Vorgänge ausführen.</p></li>
<li><p><strong>OPTIONALE</strong>. Es wird dringend empfohlen, dass die RNG-Funktion der Plattform verfügbar gemacht werden, über eine OS Entropie Datenquelle über die Schnittstelle im Microsoft Corporation, angegebenen &quot;BCrypt Profil für SoC-Beschleunigern&quot; zuvor in 4 Anforderung verwiesen wird.</p></li>
<li><p><strong>OPTIONAL.</strong>  (Gilt, wenn ein Modul kryptografische Acceleration verwendet wird) Es sollte zu verwalten, und führen kryptografische Vorgänge auf mindestens drei unterschiedlichen symmetrische Schlüssel oder zwei symmetrische Schlüssel und einen asymmetrischen Schlüssel gleichzeitig in das Modul Acceleration möglich sein. </p></li>
</ol>

**Tabelle: Algorithmus-spezifischen Anforderungen. Die Spalte "Kategorie" klassifiziert Algorithmen als obligatorisch-Support unter der Softwareschnittstelle je nach Bedarf 4 (M) oder optional (O). Beachten Sie, dass alle Algorithmen an, die in Hardware beschleunigt werden auch über die Benutzeroberfläche verfügbar gemacht werden müssen.**

<table>
<thead>
<tr class="header">
<th>Algorithmus</th>
<th>Kategorie</th>
<th>Modi</th>
<th>Obligatorisch unterstützt Key der Größe</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>3-DES</td>
<td>O</td>
<td>ECB CBC, CFB8</td>
<td>112, 168</td>
<td> </td>
</tr>
<tr class="even">
<td>AES</td>
<td>M</td>
<td>ECB CBC CFB8 CFB128 CCM CMAC GCM, GMAC</td>
<td>128, 192, 256</td>
<td>Leistung &gt;= 60 MB/s für AES-128-CBC und AES-128-ECB-Verschlüsselung und Entschlüsselung gemessen an der CNG-Kernelmodus BCrypt-Schnittstelle bei der Verarbeitung von 32 Bildspeicher-Blöcke.</td>
</tr>
<tr class="odd">
<td></td>
<td>O</td>
<td>STRG XTS, IAPM</td>
<td>128, 192, 256</td>
<td> </td>
</tr>
<tr class="even">
<td>RSA</td>
<td>O</td>
<td>PKCS #1 v1. 5, PSS, OAEP</td>
<td>512 auf 16384 in 8-Byte-Schritten angegeben wird</td>
<td>Öffentliche Leistungskennzahlen für 2.048 Bit Schlüssel (und öffentlichen Exponenten F4 (0x10001)) beim Überprüfen der PKCS #1v1.5 Signaturen, gemessen an der Kernel-Modus BCrypt Schnittstelle aufgefüllt &lt;= 0,6 ms/Überprüfung.</td>
</tr>
<tr class="odd">
<td>ECC</td>
<td>O</td>
<td>ECDSA ECDH</td>
<td>256</td>
<td>Wenn implementiert, muss Ellipsenkurven P-256 National Institute for Standards and Technology gemäß unterstützen &quot;Digital Signature Standard,&quot; <a href="http://www.nist.gov/customcf/get_pdf.cfm?pub_id=903873">FIPS 186-3</a>, Juni 2009.</td>
</tr>
<tr class="even">
<td>SHA-1</td>
<td>O</td>
<td> </td>
<td> </td>
<td>Leistung<br />
&gt;60 MB/s gemessen an der CNG im Kernelmodus BCrypt Schnittstelle bei der Verarbeitung von 4kByte blockiert.</td>
</tr>
<tr class="odd">
<td>HMAC-SHA1</td>
<td>O</td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td>SHA-256</td>
<td>O</td>
<td> </td>
<td> </td>
<td>Leistung<br />
&gt;60 MB/s gemessen an der CNG im Kernelmodus BCrypt Schnittstelle bei der Verarbeitung von 4kByte blockiert.</td>
</tr>
<tr class="odd">
<td>HMAC SHA-256</td>
<td>O</td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td>RNG</td>
<td>M</td>
<td>Entropie Quelle mit optionalen FIPS 800-90-basierte DRBG</td>
<td> </td>
<td>Sicherheitsstärke muss mindestens 256 Bits<sup>1</sup>sein. Beachten Sie, dass diese Funktionalität durch das Protokoll zum Erfassen von UEFI Entropie Verfügbarmachen erforderlich ist (Siehe gefordertes 3) und Verfügbarmachen als eine OS Entropie Datenquelle wird (Siehe gefordertes 7) empfohlen.</td>
</tr>
</tbody>
</table>


<sup>1</sup> die verbunden Standby Hersteller übermitteln Dokumentation zurück, der angibt, und ermöglicht es Microsoft schätzen Sie, die Qualität der Quelle Entropie. Die Entropie muss mithilfe der min-Entropie-Methode von Anhang C des National Institute for Standards and Technology "Empfehlung für zufällige Generierung deterministisch Random-Bit-Generatoren von" [FIPS 800 90](http://www.nist.gov/customcf/get_pdf.cfm?pub_id=50814), März 2007 bewertet und überschreiten oder gleich 256 Bits werden, bevor die Laufzeit OS startet.

<sup>2</sup> diese Spezifikation muss explizit von Microsoft angefordert werden. Um die aktuelle Version anzufordern, wenden Sie sich an den [http://go.microsoft.com/fwlink/?LinkId=237130](http://go.microsoft.com/fwlink/?LinkId=237130 "http://go.microsoft.com/fwlink/?LinkId=237130").
<p></p>


### <a name="systemfundamentalsfirmwarecsuefisecurebootconnectedstandby"></a>System.Fundamentals.Firmware.CS.UEFISecureBoot.ConnectedStandby

*Alle Clientsysteme, die Standbymodus verbunden unterstützen müssen UEFI Secure Boot unterstützen.*

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

1.  Verbundener standby-Systeme müssen alle der in diesem Abschnitt und Abschnitt System.Fundamentals.Firmware.Uefisecureboot genannten Anforderungen erfüllen. Darüber hinaus MUSS die folgende Anforderung erfüllen.

2.  Boot-Integrität. Plattform verwendet integrierter ROM oder einmalig programmierbare (OTP) Arbeitsspeicher zum Speichern von Code beim ersten Start und anfänglichen öffentlichen Schlüssel (oder Hash des ersten öffentlichen Schlüssels) verwendet, um Boot Integrität bereitzustellen und Power-on zurücksetzen Logik zum Ausführen von integrierter ROM oder secure integrierter SRAM enthält.

3.  Sichere Boot Start von Windows 8 BootMgr darf keine erfordern die Verwendung eines Eintrags DB zulässig, außer Microsoft bereitgestellten EFI\_CERT\_X509 Signatur mit "CN = Microsoft Windows Produktion PCA 2011" und "Cert Hash(SHA1):: 58 0a 6f 4 c c4 e4 b6 69 b9 Eb dc 1 b 2 b 3e 08 7 b 80 d0 67 8 d.

4.  Auf ARM, die Datenbank UEFI zulässig ("Db") darf keine enthalten einen beliebigen anderen Eintrag als Microsoft - EFI bereitgestellten\_CERT\_X509 Signatur mit "CN = Microsoft Windows Produktion PCA 2011" und "Cert Hash(SHA1):: 58 0a 6f 4 c c4 e4 b6 69 b9 Eb dc 1 b 2 b 3e 08 7 b 80 d0 67 8 d.

5.  Die Richtlinien für akzeptable Signatur-Algorithmen (und Textabstand Schemas) muss so aktualisieren Sie möglich sein. Die genaue-Methode zum Aktualisieren der Richtlinie ergibt sich jede Behörde (zum Beispiel: Microsoft bestimmt Richtlinien für Binärdateien verantwortlich für das ist; SOC Anbieter Firmwareupdates). Es wird erkannt, dass der anfängliche ROM-Code keine Möglichkeit, das Schema der ursprünglichen Signatur aktualisieren muss.

6.  Die Plattform muss verwalten und erzwingen Sie eine Richtlinie im Hinblick auf Signatur Behörden Firmware und vor dem Betriebssystemkomponenten; die Richtlinie (und somit auch den Satz von Behörden) ist möglich, zu aktualisieren. Das Update muss entweder als Ergebnis einer Aktionen durch einen physisch autorisierten Benutzer oder durch die Bereitstellung von einer vorhandenen Zertifizierungsstelle für diese Aufgabe autorisiert angemeldet Aktualisierung erfolgen. Auf ARM-Plattformen ist die Anwesenheit einer Person allein nicht ausreichend. Signatur Autorität (Db oder KEK) Updates müssen auf ARM-Plattformen authentifiziert werden.

7.  Beim Einschalten die Plattform schreibgeschützt Boot gespeicherte Firmware auf Die Ausführung beginnt und öffentlichem Schlüssel gemäß der Richtlinie Algorithmus zum Überprüfen der Signaturen aller Bilder in der Boot Sequence nach-oben-an der Windows-Start-Manager verwenden.

8.  Schutz des physischen Arbeitsspeichers von nicht autorisierten internen DMA (zum Beispiel: GPU den Zugriff auf Speicher außerhalb von Video-spezifischen Speicher) und keine nicht authentifizierten DMA Zugriff auf die SOC. Die Firmware muss dieser Schutz so früh wie möglich, vorzugsweise innerhalb der Firmware beim ersten Start ermöglichen.

9.  Optional: Der Arbeitsspeicher, die beim ersten Start Firmware (Ausführen in SRAM) enthält kann nicht zugegriffen werden beim Springen zur nächsten Stufe der Startsequenz überprüfte gestellt werden. Beim ersten Start Firmware kann nicht zugegriffen werden bleiben, bis Power auf Zurücksetzen ausgelöst wird.

10. Die Plattform muss Richtlinien bezüglich der Ersatz der Firmware Komponenten erzwingen. Die Richtlinie muss Schutz gegen Rollback enthalten. Ist es von der Plattform-Hersteller, um die genauen-Methode für die Erzwingung von Gruppenrichtlinien definieren links, aber die Überprüfung der Signatur aller Firmware Updates muss übergeben und das Update muss in einem solchen identifiziert werden eine Art und Weise, die eine höhere Version einer Komponente nicht, ohne ordnungsgemäße Autorisierung möglich (zum Beispiel: Anwesenheit), von einer früheren Version der Komponente ersetzt werden, in denen frühere und später möglicherweise durch eine Versionsnummer (signierte) definiert , zum Beispiel.

11. Optional: Die Plattform muss mindestens 112 logische eFuse Bits zur Unterstützung der Plattform Firmware Versionskontrolle gemäß der oben genannten Anforderung bieten.

12. Physische Sicherheit Requirements. Im Einzelhandel Teile nachdem die Plattform für Produktionsmodus versetzen, konfiguriert wurde muss die Hardware alle externen Hardware Debug-Schnittstellen wie JTAG deaktivieren, die zum Ändern der Plattform Sicherheitsstatus, und deaktivieren alle Hardware Test Modi sowie alle Scan Lieferketten verwendet werden können. Die Deaktivierung muss permanente es sei denn, die erneute Aktivierung uneingeschränkt alle verwalteten Gerät Schlüssel verursacht, die sicheren Boot TPM und Speicher Sicherheit gerendert werden auswirkt, dauerhaft gelöscht.

13. Auf ARM-Plattformen ist Secure benutzerdefinierte Startmodus nicht zulässig.

14. Ein physisch vom Benutzer nicht authentifiziert Secure Boot Variablen überschrieben (z. B.: PK, KEK, Db, Dbx).

15. Plattformen müssen UEFI-Klasse drei (Siehe UEFI Branche, auswerten UEFI mit dem Markt verfügbaren Plattformen und Lösungen, Version 0.3 für eine Definition) mit keine Kompatibilität Supportmodul installierbares oder installiert sein. BIOS Emulation und legacy PC / BEIM Start muss deaktiviert sein.

16. Jedes Gerät ist erforderlich, bereitgestellt mit alle kryptografischen Basis und Schlüssel, die erforderlich sind, um zu verhindern, dass Angriffe auf des Geräts sicheren Boot, TPM und sichere Speicherung Implementierungen sind Fertigung lassen. Basis und symmetrische Schlüssel festgelegt sein, unveränderlich, pro-Gerät-eindeutig und nicht-vorhersehbare (mit ausreichend Länge vollständige standhält zufällige suchen; finden Sie unter NIST 800 31A akzeptable wichtige Größen).

17. Die Plattform ist erforderlich zum Implementieren von Hardware Test-Schnittstelle und die Freigabe Dokumentation zu Sicherheit und Tools wie im Dokument "Hardware Sicherheit testen Schnittstellenspezifikation" angegeben. Diese Anforderung ist IF für Server IMPLEMENTIERT.


## <a name="systemfundamentalsfirmwaretpr"></a>System.Fundamentals.Firmware.TPR

*Dieses Feature umfasst Anweisungen für System-Firmware mit EDer-Unterstützung.*


### <a name="systemfundamentalsfirmwaretpruefiencryptedhdd"></a>System.Fundamentals.Firmware.TPR.UEFIEncryptedHDD

*Systeme, die mit einer sich selbst verschlüsseln Festplatte zu liefern, gemäß einem Speichergerät UEFI 2.3.1 EFI unterstützen muss\_SPEICHER\_SECURITY\_BEFEHL\_PROTOKOLL Protokolle und enthält eine BS-Partition, die zum Speichern von WinRE verwendet werden können.*

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

Wenn Self verschlüsselten Laufwerk Unterstützung implementiert ist es muss ein UEFI-kompatiblen Betriebssystem und enthalten Systemfirmware in System.Fundamentals.Firmware, die Anforderungen an das System Firmware Logo als beide entsprechen definiert und enthalten auch eine separate WINRE Partition.

BitLocker muss sich selbst verschlüsseln Treiber unterstützen, die die EDer Gerät Richtlinien auf WHDC unter http://msdn.microsoft.com/en-us/library/windows/hardware/br259095 verfügbar entsprechen

UEFI – Anzahl 616 oder UEFI 2.3.1 vertrauenswürdige Befehl Unterstützung in UEFI 2.3 + UEFI Mantis ändern

Standard 2.3 + fehlerverzeichnis Bv2 www.uefi.org

Mantis Änderung Anzahl 616 www.uefi.org (Dies ist nicht Teil der 2.3)

Alle erforderliche Partitionen erstellt, verwaltete einzeln vor/Post-Verschlüsselung werden müssen. Die WINRE Partition muss immer separate und außerhalb der Partition OS-Verschlüsselung.

Wenn WinRE auf der Systempartition ist, ist die Größe 350 MB. Wenn sie nicht die Systempartition ist, ist es 300MB. Dies wird von MBR-Layout vorausgesetzt. (Für GPT ist WinRE immer unabhängig von der ESP, daher 300 MB.)

Diese Anforderung ist "Wenn implementiert" für Server-Systeme und gilt nur, wenn ein Serversystem UEFI Lage ist.


## <a name="systemfundamentalsgraphics"></a>System.Fundamentals.Graphics

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsgraphicsfirmwaresupportslargeaperture"></a>System.Fundamentals.Graphics.FirmwareSupportsLargeAperture

*32-Bit- und 64-Bit-System-Firmware unterstützt große Blende Graphic-Adapter.*

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

System-Firmware (BIOS-/ UEFI) muss große Blende Grafikkarten unterstützen. Die 32-Bit-System-Firmware (BIOS/UEFI) muss Support mindestens 256 MB Blende können. Auf 64-Bit-Systemen muss mindestens 1 GB Blende unterstützen die Firmware (BIOS/UEFI).
Ein System, mehrere Grafikkarten unterstützt, muss für jeden Adapter über genügend Ressourcen sicherstellen. Auf einem 32-Bit-System mit 4 Grafikkarten, muss jeder Adapter beispielsweise mindestens 256 MB Speicherressourcen jedes im PCI-Bus erhalten.


### <a name="systemfundamentalsgraphicsmicrosoftbasicdisplaydriver"></a>System.Fundamentals.Graphics.MicrosoftBasicDisplayDriver

*System ist kompatibel mit den grundlegenden Grafiktreiber von Microsoft.*

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

Das System muss in einen Modus gestartet wird, in dem der vom Treiber Standardanzeige Microsoft verwendete Framepuffer angezeigt, wenn Microsoft Grafikkartentreiber auf der Framepuffer schreibt. Kein anderer Treiber ist zum Ausführen dieser Ausgabe beteiligt. Der Framepuffer muss linear und im BGRA-Format dar.


### <a name="systemfundamentalsgraphicsnorebootupgrade"></a>System.Fundamentals.Graphics.NoRebootUpgrade

*Grafiktreiber müssen ohne einen Neustart des Systems aktualisierbar sein.*

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

WDDM-Treiber-Modell wurde seit Windows Vista ohne Reboot Upgrade unterstützt.  Für Windows müssen alle Systeme die Aktualisierung des Treiberpakets Grafiken unterstützen, ohne dass das System neu gestartet.
Beispielsweise enthält das Graphics-Treiberpaket Graphics-Treiber, und alle zugehörigen Dienstprogramme und Dienste.


## <a name="systemfundamentalsgraphicsdisplayrender"></a>System.Fundamentals.Graphics.DisplayRender

*Die Anforderungen in diesem Abschnitt durchgesetzt Grafiken Gerät anzeigen implementieren und Rendern Teil der WDDM.*


### <a name="systemfundamentalsgraphicsdisplayrenderstableandfunctional"></a>System.Fundamentals.Graphics.DisplayRender.StableAndFunctional

*Anzeigegeräts ordnungsgemäß funktioniert und löst keine längerer Belastung hängt oder Fehler.*

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

Das System muss unter längerer Stress ausgeführt, ohne hängt oder Fehler generieren.


## <a name="systemfundamentalsgraphicshybridgraphics"></a>System.Fundamentals.Graphics.HybridGraphics

*Hybride Graphics-Funktion*


### <a name="systemfundamentalsgraphicshybridgraphicsmultigpu"></a>System.Fundamentals.Graphics.HybridGraphics.MultiGPU

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

Neue Systeme in Windows 10 ausgeliefert, die erwartungsgemäß Hybrid-fähig sein müssen die folgenden Anforderungen erfüllen:

 - Ein Hybrid-System von Microsoft unterstützten kann nur erstellt werden, wie eine GPU (iGPU) und einer separaten GPU (dGPU) integriert.

 - Mehr als zwei GPUs nicht möglich

 - Beide GPU muss DX11.0 oder höher

 - Beide GPU Treiber muss WDDM 2.0 oder höher sein.

 - Sowohl GPUs müssen implementieren den standardmäßigen Zuordnung Typ der KM hinzugefügt und zugehörigen UM DDIs um Cross Adapter shared Flächen zu unterstützen.

 - Verfügt jede GPU separate standard-Treiber, müssen sie unabhängig von einander und unabhängig voneinander aktualisiert werden, ohne dass hybridfunktionen kann sein

 - Die dGPU muss dieselbe oder eine höhere Leistung als das iGPU sein.

 - Der dGPU Adapter ist diejenige, die die einzelne Hybrid Cap festgelegt

Alle anderen Multi-GPU Konfigurationen erhalte nicht Hybrid Support von Microsoft. Sie werden die gleiche Weise behandelt werden, wie durch die Anforderung "System.Fundamentals.Graphics.MultipleOperatingMode" definiert.

**D-List-Anforderungen**

Dies ist die Liste der Anwendungen, die für die Auswahl einer GPU für eine app im Hybridmodus ausgeführt werden sollen oder nicht von der dGPU IHV verwaltet:

 - Die D-List-DLL kann in einen Prozess geladen und höchstens einmal während der Initialisierung D3D abgefragt werden

 - Die Größe der DLL-DATEI muss unter 200 KB sein.

 - Die DLL muss sich GPU Auswahl Auswahlmöglichkeit im 4ms zurückgeben können.

**Power Anforderungen für das Projektmanagement**

Es folgen die Power Management-Anforderungen für die Teilnahme an einer hybridkonfiguration separaten GPU:

<ul>
  <li>
    <p>Der Treiber ist erforderlich, um für die Verwaltung der Common Language Runtime Stromversorgung registrieren.</p>
  </li>
  <li>
    <p>Der Treiber muss bestimmte basierten auf den folgenden Szenarien Power-Komponenten zu registrieren.</p>
    <table>
      <tr>
        <th>Gerät ist kein D3 Übergänge erforderlich.</th>
        <td>
          <p>DXGK\_POWER\_KOMPONENTE\_ENGINE-Komponente für jedes Modul GPU (Knoten)</p>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_D3\_ÜBERGANG Komponente mit einem F-Zustand</p>
        </td>
      </tr>
      <tr>
        <th>Gerät erfordert D3 Übergänge und hat kein Speicher Self aktualisieren</th>
        <td>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_D3\_besagt ÜBERGANG Komponente mit zwei F</p>
          <p>DXGK\_POWER\_KOMPONENTE\_ENGINE-Komponente für jedes Modul GPU (Knoten)</p>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_ARBEITSSPEICHER Komponente für jedes Segment Arbeitsspeicher.</p>
          <p>Wenn TransitionalLatency dieser Komponente ist &gt; 200us, Komponente müssen außerdem DXGK\_POWER\_KOMPONENTE\_FLAGS::DriverCompletesFStateTransition-Kennzeichens</p>
        </td>
      </tr>
      <tr>
        <th>Gerät erfordert, D3 Übergänge und hat Arbeitsspeicher Self aktualisieren</th>
        <td>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_D3\_besagt ÜBERGANG Komponente mit zwei F</p>
          <p>DXGK\_POWER\_KOMPONENTE\_ENGINE-Komponente für jedes Modul GPU (Knoten)</p>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_SPEICHER-Komponente für jedes Segment Arbeitsspeicher und mit der DXGK\_POWER\_KOMPONENTE\_FLAGS::ActiveInD3 festgelegt.</p>
          <p>Diese Komponente muss melden, 2 F Staaten und TransitionalLatency von F1 Zustand müssen 0 sein.</p>
          <p>Ein DXGK\_POWER\_KOMPONENTE\_SPEICHER\_REFRESH Komponente für den Adapter. Außerdem muss der Treiber in Abhängigkeit Array für alle Gerät Module Platz</p>
        </td>
      </tr>
    </table>
  </li>
  <li>
    <p>Übergangs-Wartezeit für jede Komponente gemeldet darf nicht größer als Max sein.  Latenztoleranz für diese Komponente wird in der folgenden Tabelle angegeben.</p>
  </li>
</ul>

<table border="2">
  <tr>
    <th colspan="2"> </th>
    <th>Wartezeit Toleranzen</th>
  </tr>
  <tr>
    <th rowspan="3">Modul (Monitor ON)</th>
    <td>Anfangszustand</td>
    <td>0,08 ms</td>
  </tr>
  <tr>
    <td>Nach der Leerlaufzeit bis 200 ms</td>
    <td>15 ms</td>
  </tr>
  <tr>
    <td>Kein Kontext auf das Modul</td>
    <td>30 ms</td>
  </tr>
  <tr>
    <th rowspan="3">Modul (Monitor)</th>
    <td>Anfangszustand</td>
    <td>2 ms</td>
  </tr>
  <tr>
    <td>Nach der Leerlaufzeit bis 200 ms</td>
    <td>50 ms</td>
  </tr>
  <tr>
    <td>Kein Kontext für das Modul</td>
    <td>100 ms</td>
  </tr>
  <tr>
    <th rowspan="2">Arbeitsspeicher</th>
    <td>Aktiven Kontext vorhanden ist.</td>
    <td>15 ms</td>
  </tr>
  <tr>
    <td>Keine aktiven Kontext vorhanden ist.</td>
    <td>30 ms</td>
  </tr>
  <tr>
    <th rowspan="3">Aktualisieren von Arbeitsspeicher</th>
    <td>Anfangszustand</td>
    <td>0,08 ms</td>
  </tr>
  <tr>
    <td>Keine aktiven Kontext vorhanden ist.</td>
    <td>30 ms</td>
  </tr>
  <tr>
    <td>Überwachen deaktivieren und keine aktiven Kontext vorhanden ist.</td>
    <td>80 ms</td>
  </tr>
  <tr>
    <th rowspan="4">D3 Übergang</th>
    <td>Anfangszustand</td>
    <td>0,08 ms</td>
  </tr>
  <tr>
    <td>Nach 10 s der Leerlaufzeit für alle Module</td>
    <td>15 ms</td>
  </tr>
  <tr>
    <td>Keine aktiven Kontext</td>
    <td>200 ms</td>
  </tr>
  <tr>
    <td>Deaktiviert überwachen und (keine aktiven Kontext oder alle Module im Leerlauf für 60 s)</td>
    <td>250 ms</td>
  </tr>
</table>

## <a name="systemfundamentalsgraphicsinternaldisplay"></a>System.Fundamentals.Graphics.InternalDisplay

*Basis für Grafiken auf Systeme*


### <a name="systemfundamentalsgraphicsinternaldisplaynativeresolution"></a>System.Fundamentals.Graphics.InternalDisplay.NativeResolution

*Systeme mit integrierten zeigt müssen native Auflösung in der Standardeinstellung verwenden.*

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

Ein System mit einer integrierten Display muss unterstützen die systemeigene Auflösung der Anzeige und native Auflösung als Standard verwenden.

Eine "integrierte" Anzeige ist einer Anzeige, die in das System integriert ist. Ein Laptop Abdeckung ist ein Beispiel für eine integrierte anzeigt.

Windows soll in systemeigenen Lösung am besten geeignet.
Dies gilt für Systeme, die UEFI oder BIOS verwenden. 


## <a name="systemfundamentalsgraphicsmultipledevice"></a>System.Fundamentals.Graphics.MultipleDevice

*Anforderungen, die für Systeme mit mehr als ein Grafikgerät gelten.*


### <a name="systemfundamentalsgraphicsmultipledeviceconfigure"></a>System.Fundamentals.Graphics.MultipleDevice.Configure

*Auf einem System mit mehreren Grafikkarten kann Systemfirmware den Benutzer so konfigurieren Sie die Verwendung der Adapter ansetzt.*

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

Auf einem System mit mehreren Grafikkarten muss die Systemfirmware (BIOS, UEFI usw.) den Benutzer die Möglichkeit zum Ändern der folgenden Einstellungen angeben:
 

 - Jeder Adapter aktivieren/deaktivieren:

     - Die Firmware muss dem Benutzer bieten die Möglichkeit zum auswählen, welcher Adapter aktiviert oder deaktiviert ist

     - Zu einem bestimmten Zeitpunkt muss mindestens ein Adapter, die POST unterstützt, aktiviert werden

     - Wenn der Benutzer einen Adapter kann, und das System nur einen aktiven Adapter zu einem Zeitpunkt unterstützt, müssen Sie dann alle anderen Adapter deaktiviert werden

     - Wenn nur aktiviert Adapter nicht erkannt, wird die Firmware, greift auf den integrierten Adapter. Wenn Adapter vorhanden, keine integrierte, klicken Sie dann auf den ersten Adapter gefunden auf dem ersten Bus fallback ist

 - Wählen Sie den Adapter als POST-Gerät verwendet werden soll

     - Firmware muss nur den Benutzer einen Adapter als POST Gerät auswählen können.

     - Ein System mit einer integrierten Adapter ist POST nur an einem Adapter zulässig, die nicht physisch aus dem System entfernt werden

     - Zu einem bestimmten Zeitpunkt muss mindestens ein Adapter, die POST unterstützt, aktiviert werden

     - Wenn mehrere Adapter, die POST unterstützen aktiviert sind, muss die Firmware dem Benutzer bieten eine Option auswählen, welche für Post-ANFORDERUNG verwendet werden soll


### <a name="systemfundamentalsgraphicsmultipledevicesubsystemdeviceid"></a>System.Fundamentals.Graphics.MultipleDevice.SubsystemDeviceID

*Hybrid/Switchable Graphics-Systeme, die mehrere separate Grafikkarten oder Chipsatz Kombination unterstützen müssen verwenden der gleichen Subsystem ID.*

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

Mehrere GPU Graphics-Konfigurationen, die mehrere separate Grafikkarten oder Chipsatz Kombination unterstützen müssen für jedes Gerät in der Konfiguration der gleichen Subsystem-ID verwenden.
Mehrere GPU Grafiken Systeme heterogenen Grafiken Lösungen unter bestimmten Umständen, wodurch andere ANBIETER-IDs haben dürfen.
Die GPUS von anderen Anbietern Kombinieren mehrerer GPU Konfigurationen benötigen die gleichen SUBSYS-ID an, dass die Treiberpakete ein mehrere GPU System gerichtet sind.  Sollte dasselbe Gerät verwendet werden als einzelnes Gerät in einem anderen System, muss diese Instanz des Geräts eine andere eindeutige 4teilig verwenden-PnP-Kennung.

Dies gilt nicht für Systeme, die Microsoft-Hybrid-Lösung implementieren, wird erwartet, dass diese Lösung distinct HWID haben.
Beispiele für die:

1. Der integrierte GPU und separaten GPU möglicherweise unterschiedliche ANBIETER--ID sowie DEV, jedoch dieselbe SSID benötigen. Beispiel:
<code><br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Display Devices<br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Card name: InField GFX<br/>
Manufacturer: OutStanding<br/>
Chip type: RUOK Family<br/>
DAC type: Integrated RAMDAC<br/>
Device Key: Enum\\PCI\\VEN\_AAAA&DEV\_EEEE&SUBSYS\_9025104D&REV\_A1<br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Display Devices<br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Card name: Rocking Fast GFX<br/>
Manufacturer: Awesome Chips<br/>
Chip type: 10Q Family<br/>
DAC type: Internal<br/>
Device Key: Enum\\PCI\\VEN\_BBBB&DEV\_DDDD&SUBSYS\_9025104D&REV\_07<br/>
</code>

2. Die GPUs, die auf einem Computer ein umschaltbares verwendet wird, müssen eine andere SSID verwenden, wenn auch in einem-ein umschaltbares Computer verwendet. Beispiel:
<code><br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Display Devices<br/>
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-<br/>
Card name: InField GFX<br/>
Manufacturer: OutStanding<br/>
Chip type: RUOK Family<br/>
DAC type: Integrated RAMDAC<br/>
Device Key: Enum\\PCI\\VEN\_AAAA&DEV\_EEEE&SUBSYS\_9999104D&REV\_A1<br/>
</code>

Beachten Sie, dass die ausstehenden InField globalen Soundeffekts in \#1. Ist identisch mit dem in angegeben \#2; Obwohl sie die gleiche Hardware sind, müssen sie eine andere SSID aufweisen.


## <a name="systemfundamentalsgraphicsrenderonly"></a>System.Fundamentals.Graphics.RenderOnly

*Anforderungen für die zu einem Grafikgerät gelten nur WDDM Rendern DDI implementieren.*


### <a name="systemfundamentalsgraphicsrenderonlyminimumdirectxlevel"></a>System.Fundamentals.Graphics.RenderOnly.MinimumDirectXLevel

*Darstellungsgerät nur auf Client oder Serversystem muss Direct3D 10 Lage oder höher sein.*

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

Wenn ein Client oder Server-System eine einzige darstellungsgerät enthält, muss das Gerät Direct3D 10 Lage oder höher sein.   Dieses Gerät kann nur von einem WDDMv1.2 Rendern nur Treiber unterstützt werden. Rendern nur Geräte sind als primäre Grafikgerät auf Client-Systemen nicht zulässig.  Allen Windows-Client-Systemen benötigen eine vollständigen Grafiken WDDM v1. 3 Gerät als primäre Boot-Gerät.


## <a name="systemfundamentalshal"></a>System.Fundamentals.HAL

*Dieses Feature Hardwareabstraktionsschicht (HAL) Erfordernisse für Systeme definiert werden.*


### <a name="systemfundamentalshalifcsrtpresent"></a>System.Fundamentals.HAL.IfCSRTPresent

*Signierte HAL-Erweiterungen für Zeitgeber erforderlich sind, und DMA-Controller, die nicht im Feld unterstützt*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>10 Windows Mobile ARM</p>
</td></tr></table>


**Beschreibung**

Für Plattformen, mit die den ARM implementiert keine generischen Intervall Timer (GIT) definiert, sollte die Plattform CSRT Tabelle mit Ressourcengruppen, die die Timer-Ressourcen zu beschreiben. Darüber hinaus muss das Betriebssystemabbild auf der Plattform Microsoft enthalten signierte HAL-Erweiterungen, die ordnungsgemäß mit den Einträgen in der CSRT und diese HAL Extensions verknüpft sind, müssen die folgenden Windows erforderlichen minimale Timer-Ressourcen registrieren:

 - eines Zeitgebers (minimale Auflösung von 1 Millisekunde)

 - ein Indikator (mindestens Lösung 1 Mikrosekunden)

 -  ein immer auf Timer (muss auch registriert werden mit einer Auflösung von mindestens 1 Millisekunde), und

 -  ein immer auf Counter (mit einer Auflösung von einer least 1 Millisekunde registriert)

Wenn die Plattform DMA-Controller (freigegebene) System enthält, muss der CSRT die Einträge zur Beschreibung dieser Controller enthalten. Darüber hinaus muss das Betriebssystemabbild auf der Plattform Microsoft signierte HAL-Erweiterungen, die ordnungsgemäß an diesen Einträgen in der CSRT und diese HAL Extensions verknüpft sind, müssen Windows erforderlichen Ressourcen DMA registrieren enthalten: mindestens ein DMA-Controller und alle DMA-Kanäle für jeden registrierten DMA-Controller.  

**Weitere Informationen**

|                        |                                                                                            |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unternehmensvorgabe | Die Informationen in den Tabellen können Windows die HAL Erweiterung Module zu identifizieren, die zur Unterstützung der Hardware für die Plattform implementiert geladen werden müssen. Die Erweiterung HAL aus diesen Tabellen auf wie die Systemressourcen Core implementiert und auf dieser Plattform, um alle Unterschiede zwischen den verschiedenen Plattformen aufzunehmen konfiguriert werden abgerufen. |
|                        |      |                                                                                      |


### <a name="systemfundamentalshalhpetrequired"></a>System.Fundamentals.HAL.HPETRequired

*System bietet einen hohe Genauigkeit-Ereignis-Zeitgeber*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Systeme müssen eine hohe Genauigkeit Ereignis Timer (HPET) implementieren, die mit den folgenden Punkten des Intel entspricht

Architektonische privaten Computer (IA-PC) HPET Daten:

 - Die wichtigsten Leistungsindikator Häufigkeit muss größer als oder gleich 10 MHz und kleiner oder gleich 500-MHz
 - Der wichtigste Leistungsindikator muss monoton erhöhen, außer auf ein Roll Over-Ereignis.
 - Die wichtigsten Leistungsindikator und könnten muss mindestens 32 Bit.
 - Der wichtigste Leistungsindikator benötigen mindestens drei könnten.
 - Alle von der könnten muss aperiodic, "einmalige" Interrupts ausgelöst werden können.
 - Mindestens eines der könnten muss periodische Interrupts ausgelöst werden können.
 - Jede Vergleichsoperator muss einen eindeutigen und unabhängigen Interrupt ausgelöst werden können.
 - HPET muss Edge auslösen Interrupts unterstützen.
 - Zeitgeber-Interrupts müssen im LegacyIRQRouting Modus nicht freigegeben werden.
 
 
## <a name="systemfundamentalsinput"></a>System.Fundamentals.Input

*Anforderungen in diesem Abschnitt gelten für HID-Geräte, die im System integriert sind.*


### <a name="systemfundamentalsinputi2cdeviceuniquehwid"></a>System.Fundamentals.Input.I2CDeviceUniqueHWID

*I2C angeschlossenen HID Geräte, eine Unique HWID zusammen mit einer kompatiblen HID benötigen-ID.*

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

Alle I2C verbundenen HID-Geräte benötigen, eine eindeutige HWID und eine kompatible HID-ID, die zulassen WU Identifizieren des Geräts (falls erforderlich) und Treiber von WU geladen werden können.

*Hinweise zum Entwurf*:

Finden Sie in Microsoft HID I2C Protokollspezifikation veröffentlicht.


### <a name="systemfundamentalsinputps2uniquehwid"></a>System.Fundamentals.Input.PS2UniqueHWID

*Alle verbunden PS/2-Geräte (wie internen Tastaturen) müssen eine eindeutige Hardware-ID verfügen.*

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

Alle PS/2 angeschlossene Geräte (wie Touchpad und Tastaturen) eine eindeutige Hardware-ID verfügen müssen, die im Lieferumfang von WU den Drittanbieter-Treiber ermöglicht.

*Hinweise zum Entwurf*:

Finden Sie unter [Hardware-IDs für Eingabegeräte auf Laptops PS/2](http://www.microsoft.com/whdc/device/input/mobileHW-IDs.mspx), ein entsprechendes Whitepaper.


## <a name="systemfundamentalsmarkerfile"></a>System.Fundamentals.MarkerFile

*Eine Markierung-Datei wird verwendet, zu bestimmten Computer-Modellen WER Daten zugeordnet werden.  Anforderungen in diesem Abschnitt beschreiben die Syntax für die Datei"Markierung.*


### <a name="systemfundamentalsmarkerfilesystemincludesmarkerfile"></a>System.Fundamentals.MarkerFile.SystemIncludesMarkerFile

*System enthält Markerdatei*

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

Die Markierung Datei bietet zusätzliche Informationen über den Ersteller des Systems PC und Modell. Diese Informationen werden zum Erfassen und verteilen Online abstürzen Analyseinformationen verwendet. Die Markierung-Datei ist eine Textdatei mit der Erweiterung .mrk an. Die. MRK Filename muss unter 256 Zeichen lang, einschließlich des Pfads. Die Zeichen müssen Buchstaben, Zahlen, Punkte, Bindestriche, Kommata und Klammern sein.

Das Format der Markierung ist: 

Für Unternehmen mit PCI-Hersteller-IDs:

&nbsp;&nbsp;&nbsp;*Anbieter-ID*\_*CompanyName*\_*Division*\_*Marketing Modellname*\_*Weitere Infos*. MRK

Für Unternehmen ohne PCI-Anbieter-ID:

&nbsp;&nbsp;&nbsp;*CompanyName*\_*Division*\_*Marketing Modellname*\_*Weitere Infos*. MRK

Jeder Spalte wird durch den Unterstrich getrennt '\_' Zeichen. Die Werte in jeder Spalte werden:

 - *Anbieter-ID* = die PCI-Anbieter-ID für den PC-Hersteller.

 - *CompanyName* = Name des Unternehmens Ort. Dies sollte für jede Markerdatei konsistent sein.

 - *Division* = dieser stellt die Abteilung innerhalb des Unternehmens. Wenn Ihr Unternehmen nicht Abteilungen versetzen "NV". besitzt

 - *Marketing-Modellname* = Produktname das System ausgeliefert werden wird. Dies sollte der Zeitpunkt der Übermittlung Logo eingegebene marketing Name identisch sein.

 - *Weitere Infos* = optional Ad durch werden die Websitemigration Weitere Unterstriche hinzugefügt werden kann. Die zusätzlichen Felder können verwendet werden, für andere wichtige Informationen über das System zu identifizieren.

Optional können Sie die \_ich Feld als Zahl, die verwendet werden kann, der marketing Modellname zu verknüpfenden Teil verwendet werden können. 

*Design Notes:* Die Markierung-Datei wird in das Laufwerk c:\\Windows\\system32\\Treiberordner.


## <a name="systemfundamentalsnetwork"></a>System.Fundamentals.Network

*Dies sind Ebene Systemanforderungen, die die Integration in einem Netzwerk Gerätetyp auswirkt*.


### <a name="systemfundamentalsnetworknetworklistoffloads"></a>System.Fundamentals.Network.NetworkListOffloads

*Drahtloses Netzwerke LAN-Gerät auf Systeme, die Standbymodus verbunden unterstützen muss NDIS 6.30 unterstützen und verlagert unterstützen.*

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

Die folgenden Anforderungen gelten für drahtlosen LAN-Geräten.  WLAN-Geräte müssen die folgenden Features unterstützen.

| Feature               | Anforderung            |
|-----------------------|------------------------|
| Keine Pause auf Anhalten   | Erforderlich               |
| D0-Offloading            | Erforderlich               |
| Selektive USB anhalten | Required-wenn USB basiert |
| Abladung von Netzwerkliste  | Erforderlich               |
| Wi-Fi PSM             | Erforderlich               |
| Wi-Fi Direct          | Erforderlich               |
| Verwaltung des Senders      | Erforderlich               |
| WPS 2.0               | Erforderlich               |
| WoWLAN                | Erforderlich               |


Systeme, die Standbymodus verbunden unterstützen erfordern die Verwendung eines NDIS 6.30 Ethernet-Treibers. Das Gerät muss die unten aufgeführten Features unterstützen.

| Feature                                             | Erforderlich |
|-----------------------------------------------------|----------|
| Remoteaktivierung über LAN                                       | Ja      |
| D0 & D3 Protokoll verlagert (Protokolle 26 Uhr angezeigt 2013) | Ja      |
| Unterbrechen Moderation                                | Ja      |
| Paketfiltern von OS programmierbare                    | Ja      |


### <a name="systemfundamentalsnetworkpowerrequirements"></a>System.Fundamentals.Network.PowerRequirements

*Alle physischen Netzwerkgeräte in einem System (einschließlich Dockingstation) müssen Gerät Zertifizierung Kriterien für Power Management Anforderungen erfüllen.*

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

Unterstützung für dieses Feature ist erforderlich. Alle physischen Netzwerkgeräte in einem System (einschließlich Dockingstation) müssen auf Device-Ebene Management Energiebedarf für dieses Typs bestimmtes Gerät erfüllen. Beispiel: Wenn einem Ethernet-Gerät ist ein fähiges verbunden Standby-System eingeschlossen oder verknüpfte docken Sie an, Ethernet Gerät Management Energiebedarf für verbundene Standby unabhängig davon, ob die Zertifizierung einzelne Gerät erreicht wurde, wenn auf ein fähiges System Standby verbunden oder nicht getestet erfüllt sein müssen.


## <a name="systemfundamentalsnx"></a>System.Fundamentals.NX

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsnxsystemincludesnxprocessor"></a>System.Fundamentals.NX.SystemIncludesNXProcessor

*Systeme müssen mit Prozessoren liefern, die n x unterstützen und Treiber, die normalerweise funktionsfähig, wenn n x aktiviert ist*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Um die korrekte Gerät und Treiber Verhalten in Systemen sicherzustellen müssen alle Treiber normalerweise mit Schutz der Datenausführung betrieben werden. Insbesondere müssen Treiber Code aus dem Stack, ausgelagerte Pool- und Sitzungspool nicht ausführen. Darüber hinaus müssen Treiber nicht nicht laden, wenn die physische Adresse Extension (PAE)-Modus aktiviert ist, eine Voraussetzung für den Betrieb von n x. Darüber hinaus die System-Firmware benötigen n x auf und die Daten Ausführungsrichtlinie Datenausführungsverhinderung (DEP) muss nicht festgelegt werden, auf "immer off."


## <a name="systemfundamentalspowermanagement"></a>System.Fundamentals.PowerManagement

*Verwaltung der Stromversorgung ist ein Feature, das den PC ausgeschaltet oder in einen Zustand mit niedrigerer wird aktiviert. In diesem Abschnitt beschreibt Anforderungen um Power Management.*


### <a name="systemfundamentalspowermanagementdockundock"></a>System.Fundamentals.PowerManagement.DockUndock

*System unterstützt Andocken und über einen Übergang Ruhezustand Trennvorgang.*

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

Für Systemen, die im Lieferumfang von einer Dockingstation, das System muss möglicherweise Ruhezustand und beim Ändern von der angedockten fortsetzen abgedockt oder nicht angedockte auf den Status verankert. Dies ist nicht auf beschränkt, jedoch sollten verwenden, dass die Arbeitsspeicher-Zuordnung nicht geändert werden sollten, wenn andocken oder Entfernen des Systems.


### <a name="systemfundamentalspowermanagementmultiphaseresume"></a>System.Fundamentals.PowerManagement.MultiPhaseResume

*Speichersubsystem unterstützt mehrere Phasen fortsetzen aus dem Ruhezustand*

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

Die Treiber und Hardware-Subsysteme für das Speichergerät Boot müssen mit mehreren Phase fortsetzen aus dem Ruhezustand unterstützen. Hierzu muss das System die Fähigkeit des Systems definitiv identifiziert den gesamten Arbeitsspeicher erforderlich auf Resume verwalten können. Dies ist nicht auf beschränkt, aber sollte enthalten:
 

 - Speicherabbild Filter/Minifilter, die unterstützen müssen Lesen
 - Es werden keine WHEA Pshed-Plug-Ins installiert.
 - Hypervisor ist nicht aktiviert.


### <a name="systemfundamentalspowermanagementpcsupportslowpowerstates"></a>System.Fundamentals.PowerManagement.PCSupportsLowPowerStates

*Unterstützung von Systemen S4 und S5 und entweder S0 niedrig Power im Leerlauf oder a3, Zustände.*

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

Ein desktop oder mobilen System mit einem Clientbetriebssystem installiert muss die S4 unterstützen (Ruhezustand) und S5 (vorläufig off) Staaten und entweder S0 niedrig Power im Leerlauf oder S3 (den Energiesparmodus versetzt wird). Systeme, die Standbymodus verbunden unterstützen müssen auch unterstützen, S4 (Ruhezustand). Jedes System muss die Aktivierung über alle implementierten Standbymodus Zustände unterstützen. Aktivierung über S5 ist nur erforderlich, über die Power-Schaltfläche.

Systeme die S0 Energiesparmodus im Leerlauf unterstützen müssen dieses Verhalten durch Festlegen der folgenden Bits in den Flags FACP melden.

| FACP - Feld                  | Len-Bit. | Bit Offset | Beschreibung                                                                                |
|-------------------------------|----------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NIEDRIG\_POWER\_S0\_im LEERLAUF\_GEEIGNET | 1        | 21         | Dieses Kennzeichen gibt an, ob das System im Zustand ACPI S0 Energiesparmodus im Leerlauf Staaten unterstützt.                 Der Wert 1 (1) gibt an, dass die Plattform so gering, S0 im Leerlauf unterstützt, sodass Übergänge auf den Status S3 nicht erforderlich sind.  OSPM interpretieren eine in einer Weise, dass er verlassen der Plattform im Zustand S0 mit vielen Geräten ausgeschaltet über den Status S3 bevorzugt, wenn der Benutzer nicht mehr mit der Plattform interagiert.  |
| *Reserviert*                    | 10       | 22         | *Für künftige Zwecke vorbehalten.*|
|   |   |   |   |   |

Wenn Sie ein USB-Hostcontroller im System implementiert wird, muss mindestens ein externer Port auf dem Domänencontroller Reaktivierung-Funktionen von S3 unterstützen. Wenn das System über mehrere USB-Hostcontroller enthält, müssen alle Hostcontroller integriert auf der Hauptplatine (d. h., nicht Add-on-Karten) Reaktivierung von S3 unterstützen. USB-Hostcontroller sind nicht erforderlich, Reaktivierung unterstützt, wenn ein mobiles System auf Batterie ausgeführt wird.

Server-Systeme sind nicht erforderlich, implementiert S0 im Leerlauf, a3, S4 oder S5 aufweisen. Wenn ein Server-System eine der folgenden Verhaltensweisen implementiert wird, müssen sie ordnungsgemäß funktionieren.

Verwaltung der Stromversorgung ist ein wichtiger Aspekt Benutzeroberfläche ist eine gute. Das System sollte steuern, welche Geräte in dem Ruhezustand versetzt wird, wenn nicht verwendet werden können. Alle Geräte müssen die Anforderung aus dem System in dem Zustand und nicht die Anforderung, wodurch eine zusätzliche ausgleichen an, auf der Stromquelle unterbinden einhalten.



### <a name="systemfundamentalspowermanagementpowerprofile"></a>System.Fundamentals.PowerManagement.PowerProfile

*System muss über Power Management Profil Formfaktor melden.*

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

Die bevorzugte\_PM\_Profil in der Tabelle FADT muss auf einen der Werte basierend auf der Formfaktor des Systems gemäß der Spezifikation, Version 5.0 ACPI festgelegt werden.  Dieser Wert darf nicht nicht festgelegt (0) sein. 
***Design Notes:*** Weitere Informationen finden Sie auf der Seite 119 ACPI-Spezifikation, Version 5.0.


## <a name="systemfundamentalspowermanagementcs"></a>System.Fundamentals.PowerManagement.CS

*Verwaltung der Stromversorgung ist ein Feature, das den PC ausgeschaltet oder in einen Zustand mit niedrigerer wird aktiviert.  In diesem Abschnitt beschreibt Anforderungen, um die Verwaltung der Stromversorgung für Systeme, die verbundenen Standby unterstützen.*


### <a name="systemfundamentalspowermanagementcscsquality"></a>System.Fundamentals.PowerManagement.CS.CSQuality

*Systeme, S0 Energiesparmodus im Leerlauf unterstützen, müssen Zuverlässigkeit Standards für Runtime Power Management erfüllen.*

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

Systeme, die Standbymodus verbunden unterstützen müssen die minimale Zuverlässigkeit Standards während der Tests für diese Anforderung erfüllen. Mit dieser Anforderung verbundenen Tests werden alle installierten Power-Engine-Plug-in (PEP), installierten Gerätetreiber und Plattform Firmware berücksichtigt.
***Design Notes:*** Um der Zuverlässigkeit des Systems sicherzustellen, dass unterstützt die mit dem Standbymodus verbunden sind, wird das System die folgenden Tests unterzogen werden:
 

 - Standby Stress im Zusammenhang mit e/a

 - Common Language Runtime Power praxisorientierte Stress, e/a

Diese Tests werden ausgeführt, während das Treiber Verifier mit den Standardeinstellungen aktiviert ist.
Diese Tests werden mit der Einstellung Testen der Treiber Verifier Parallelität auch separat ausgeführt.
Wenn ein Gerät PEP im ACPI Namespace aufgezählt und das System verfügt nicht über eine PEP geladen, wird der Test nicht erfolgreich.


## <a name="systemfundamentalspxe"></a>System.Fundamentals.PXE

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalspxepxeboot"></a>System.Fundamentals.PXE.PXEBoot

*Remote Boot-Unterstützung für PXE einhält BIOS Boot Spezifikation 1,01 oder EFI-Start-manager*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Systeme müssen PXE-fähig sein. Das System muss über das Netzwerk gestartet wurde gemäß Definition in BIOS-Spezifikation, Version 1,01, Anhang C oder als vom EFI Bootmanager gesteuert unterstützen. Diese Anforderung ist ausgenommen für Systeme, die nur mit drahtlosen LAN konfiguriert sind.

Systeme, die mit einem UEFI kompatiblen Betriebssystem ausgeliefert und den unterstützenden PXE starten müssen PXE IPV4 und IPV6 PXE-Starts gemäß Definition im UEFI 2.3.1 unterstützen.

UNDI muss Folgendes unterstützen:

 - eine DUID-UUID pro IEFT Entwurf (http://tools.ietf.org/html/draft-narten-dhc-duid-uuid-01)
 - DHCP6 DUID-UUID, IPv4-IPv6-multicast
 
Hinweise zum Entwurf:

Microsoft empfiehlt, die Implementierung der Zugriff auf PXE konsistent mit BIOS-Spezifikation, Version 1,01 und Anhang C.


## <a name="systemfundamentalsreliability"></a>System.Fundamentals.Reliability

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsreliabilitysystemreliability"></a>System.Fundamentals.Reliability.SystemReliability

*Treiber in einem System müssen zuverlässig ist.*

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

Alle Treiber in einem System müssen alle Anforderungen unter **Device.DevFund.Reliability**übergeben.  Alle Systeme müssen häufiges Szenario Stress übergeben:

1.  Aktivieren/Deaktivieren mit e/a vor und nach

2.  Dem Standbymodus Stress, e/a vor und nach


## <a name="systemfundamentalssecurity"></a>System.Fundamentals.Security

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalssecuritycredentialguard-if-implemented"></a>System.Fundamentals.Security.CredentialGuard (If-implementierte)

*Dieses Feature überprüft Credential Guard.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

Beschreibung:

In der folgenden Tabelle zeigt die Firmware, Hardware und Software-Anforderungen für Anmeldeinformationen Guard.

 - MÜSSEN die Gerät Guard-Anforderungen erfüllen, wie in [System.Fundamentals.Security.DeviceGuard](#_System.Fundamentals.Security.Device)beschrieben.

 - MUSS die zusätzlichen Anforderungen erfüllen, wie in der folgenden Tabelle beschrieben:

| **Anforderung**                                                                                                                           | **Beschreibung**                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Vertrauenswürdige Plattform Modul (TPM), Version 1.2 oder 2.0                                                                                          | TPM 1.2 und 2.0 bietet Schutz für Verschlüsselungsschlüssel, die in der Firmware gespeichert sind. Entweder diskrete oder Firmware TPMs ist ausreichend.       |
| [Firmware Sicherheitspatch für Secure m oder Implementierung](https://msdn.microsoft.com/en-us/library/windows/hardware/mt270973.aspx) | Sichere m ODER Bit verhindert, dass bestimmte Angriffe Arbeitsspeicher und für Anmeldeinformationen Guard erforderlich ist. Dadurch wird der Anmeldeinformationen Guard Sicherheit zu erhöhen. |


### <a name="systemfundamentalssecuritydeviceencryption"></a>System.Fundamentals.Security.DeviceEncryption

*Systeme, die Unterstützung standby verbunden müssen geräteverschlüsselung unterstützen.*

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

Systeme, die Unterstützung standby verbunden müssen die sicherheitsanforderungen zur Unterstützung der Aktivierung des Geräteverschlüsselung erfüllen. OEMs müssen die Aktivierung der Verschlüsselung Gerät nicht blockieren, wenn die Images bereitstellen, es sei denn, das Gerät mit einem Drittanbieter-Datenträger Verschlüsselung Lösung bereits bereitgestellt wird. Geräteverschlüsselung wird auf diesen Systemen aktiviert werden, um sicherzustellen, dass Benutzerdaten geschützt ist. Als Voraussetzungen für die Verschlüsselung des Geräts müssen verbundene standby-Systemen Anforderungen für TPM und Secure Boot erfüllen, wie in System.Fundamentals.TPM20 und System.Fundamentals.Firmware.CS.UEFISecureBoot.ConnectedStandby beschrieben.


### <a name="systemfundamentalssecuritydeviceguard-if-implemented"></a>System.Fundamentals.Security.DeviceGuard (If-implementierte)

*Gerät Guard-Anforderung für Systeme*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Windows-10 ist eine optionale Funktion aufgerufen [Gerät Guard](http://blogs.msdn.com/b/windows_hardware_certification/archive/2015/05/22/driver-compatibility-with-device-guard-in-windows-10.aspx) , die Organisationen bietet die Möglichkeit zum Sperren von Geräten in eine Möglichkeit, die erweiterte Schadsoftware Schutz vor neuen und unbekannten Schadsoftware Varianten bietet sowie erweiterte Persistent Bedrohungen (APTs). Die folgende Tabelle zeigt erforderlichen Hardware, Firmware und Software für die Guard-Gerät.

 - MÜSSEN die [HVCI kompatiblen](http://go.microsoft.com/fwlink/p/?LinkId=627463) Treiber-Anforderungen erfüllen, wie in "Filter.Driver.DeviceGuard.DriverCompatibility" beschrieben.

 - MUSS die zusätzlichen Anforderungen erfüllen, wie in der folgenden Tabelle beschrieben:


<table>
<thead>
<tr class="header">
<th><strong>Anforderung</strong></th>
<th><strong>Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Windows 10 Enterprise</td>
<td>Der PC muss Windows 10 Enterprise ausgeführt werden.</td>
</tr>
<tr class="even">
<td>X64 Architektur</td>
<td>Die Features, die Virtualisierung basierende Sicherheit verwendet, in dem Windows Hypervisor nur auf einem 64-Bit-PC ausgeführt werden können.</td>
</tr>
<tr class="odd">
<td>UEFI Firmwareversion 2.3.1 oder höher mit UEFI Secure Boot und Plattform Secure Boot</td>
<td><p>UEFI Secure Boot wird sichergestellt, dass das Gerät nur autorisierten Code gestartet wird. Darüber hinaus muss die Spezifikation für die Hardware-Anforderung für Systeme für Windows 10 nach Boot Integrität (auch bekannt als Plattform Secure Boot) unterstützt werden:</p>
<p><a href="https://msdn.microsoft.com/en-us/library/windows/hardware/dn932805(v=vs.85).aspx#system_fundamentals_firmware_uefisecureboot">System.Fundamentals.Firmware.UEFISecureBoot</a></p>
<p><a href="https://msdn.microsoft.com/en-us/library/windows/hardware/dn932807(v=vs.85).aspx#system_fundamentals_firmware_cs_uefisecureboot_connectedstandby">System.Fundamentals.Firmware.CS.UEFISecureBoot.ConnectedStandby</a> (einschließlich Hardware Security Test-Schnittstelle)</p></td>
</tr>
<tr class="even">
<td>Sichern der Aktualisierungsvorgang</td>
<td><p>System-Firmware muss Feld Updates über Windows Update unterstützen.</p>
<p>UEFI-Firmware muss secure Firmwareupdates unterstützen, wie in <a href="http://msdn.microsoft.com/library/windows/hardware/dn932805(v=vs.85).aspx#system_fundamentals_firmware_uefisecureboot">System.Fundamentals.Firmware.UEFISecureBoot</a>beschrieben.</p></td>
</tr>
<tr class="odd">
<td>Firmware BIOS-Sperrung</td>
<td><p>BIOS-Funktionen erforderlich:</p>
<p>BIOS-Kennwort oder stärkere Authentifizierung wird unterstützt, um sicherzustellen, die nur Plattform BIOS-Administrator authentifizierte kann BIOS-Einstellungen ändern.</p>
<p>OEM unterstützt die Möglichkeit, OEM oder Enterprise-Zertifikat in Secure Boot DB am manufacturing Zeit zu hinzu.</p>
<p>So konfigurieren Sie die Liste der zulässigen Bootgeräte und Gerät Startreihenfolge BOOTORDER Änderung durch OS (z. B. Boot nur von internen Festplatte) überschreibt die geschützte BIOS-Option.</p>
<p>Erforderlichen Konfigurationen:</p>
<p>Microsoft UEFI Zertifizierungsstelle muss aus Secure Boot DB entfernt werden. Unterstützung für 3rd Party UEFI Module zulässig, jedoch sollten bereitgestellten ISV Zertifikate für die bestimmte UEFI Software (z. B. Software-Paket "Foo" Zertifikat) nutzen.</p>
<p>BIOS-Optionen im Zusammenhang mit Sicherheits-und starten müssen, zu verhindern, dass andere Betriebssysteme starten und Änderungen an den BIOS-Einstellungen zu gesichert werden.</p>
<p>BIOS-Authentifizierung muss festgelegt sein (z. B. BIOS-Kennwort muss festgelegt werden)</p></td>
</tr>
<tr class="even">
<td>Virtualisierungserweiterungen</td>
<td><p>Die folgenden Virtualisierungserweiterungen sind zur Unterstützung der Virtualisierung-basierte Sicherheit erforderlich:</p>
<ul>
<li><p>Intel VT-X oder AMD-V</p></li>
<li><p>Zweite Ebene Netzwerkadressübersetzung (Intel Extended Seitentabellen, AMD schnelle Virtualisierung Indizierung)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>VT D oder AMD‑Vi IOMMU (Eingabe/Ausgabe Arbeitsspeicher Management Einheit)</td>
<td>In Windows 10 verbessert ein IOMMU System Resiliency vor Angriffen Arbeitsspeicher.</td>
</tr>
<tr class="even">
<td>Sichern von Geräten</td>
<td><p><strong>Wenn implementiert:</strong> zur Unterstützung von sicherer Geräten (angegeben durch das Vorhandensein der ACPI SDEV Tabelle, auch bekannt als VTIO Tabelle) müssen Virtualisierungserweiterungen UND alle System IOMMUs aktivieren. Alle Systemkomponenten müssen hinter einer IOMMU sein.</p>
<ol style="list-style-type: decimal">
<li><p>SMM wird für alle synchronen SMI-Handler überprüfen Sie, ob MMIO für sichere Geräte Ranges und VT d Einheiten nicht zugegriffen wird.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td>Signiert Prozessor Microcode-updates</td>
<td>Wenn der Prozessor Microcode-Updates unterstützt muss jedoch signierten Microcode-Updates erforderlich.</td>
</tr>
<tr class="even">
<td>UEFI n x Schutzebenen</td>
<td><ol style="list-style-type: decimal">
<li><p>Muss 2,6 UEFI-Spezifikation EFI_MEMORY_ATTRIBUTES_TABLE implementieren. Die gesamte UEFI-Laufzeitkomponente muss von dieser Tabelle beschrieben werden.</p></li>
<li><p>Alle Einträge müssen enthalten EFI_MEMORY_RO und/oder EFI_MEMORY_XP-Attribute</p></li>
<li><p>Mit keines der oben genannten-Attribut, dass Speicher, die ausführbare Datei und nicht schreibgeschützt ist, darf keine Einträge gelassen werden. Speicher MUSS entweder lesbar und ausführbare ODER schreibbare und nicht ausführbar sein.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td>SMM Protection Firmware-Unterstützung</td>
<td><p>SMM Kommunikation Puffer Protection verhindert, dass bestimmte daher für Gerät Guard erforderlichen Arbeitsspeicher-Angriffe. Dadurch wird der VSM (virtuelle sicherer Modus) Sicherheit zu erhöhen.</p>
<ol style="list-style-type: decimal">
<li><p>System MUSS "Windows SMM Sicherheitsmaßnahme Table" Dokument implementieren. Gibt an, dass dokumentierten Gegenmaßnahmen implementiert werden MUSS alle nicht reservierten WSMT Schutz Flags Feld festgelegt werden.</p></li>
<li><p>SMM muss Code nicht aus dem Speicher ausgeführt, die durch das Betriebssystem nicht schreibgeschützt ist.</p></li>
</ol></td>
</tr>
</tbody>
</table>

<br/>


### <a name="systemfundamentalssecuritynotdifilterandlsp"></a>System.Fundamentals.Security.NoTDIFilterAndLSP

*Keine Filter TDI oder LSPs werden während der Installation oder Verwendung durch den Treiber oder zugeordneten Softwarepakete installiert.*

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

Keine Verwendung von TDI-filtern oder LSPs durch Kernel-Modus Software oder Treiber oder Benutzersoftware Modus oder Treiber können vorhanden sein.


### <a name="systemfundamentalssecurityplayreadymodule"></a>System.Fundamentals.Security.PlayReadyModule 

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

PlayReadyModule, aktiviert, wenn auf einem Gerät in sicheren Firmware in Verbindung mit einer kompatiblen Grafiktreiber verfügbar hardwarebasierte Schutz von Inhalten für Medien. Wenn implementiert, bietet in diesem Modul Hardware-Stamm Schutz Gerät Schlüssel, Schlüsseln und Media-Inhalte/Beispiele, die über eine Medienpipeline übertragen. Sie ermöglicht das Gerät den Zugriff auf high-Definition (1080p und höher) Premium-Inhalte. OEMs shipping auf Chipsätze/SoCs, die ein PlayReadyModule (in Form eines sicheren Firmware vom Hersteller Chipsatz verfügbar) zur Verfügung haben müssen auf Geräten mit-Auflösung 1080p oder höher PlayReadyModule enthalten.


## <a name="systemfundamentalsservernano"></a>System.Fundamentals.ServerNano

Mindestanforderungen für Windows Server Nano.


### <a name="systemfundamentalsservernanodeployment"></a>System.Fundamentals.ServerNano.Deployment

Alle Treiber für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Treiber für die Verwendung auf Windows Server Nano vorgesehen müssen die folgenden Anforderungen für die Bereitstellung erfüllen:

 - Treiber müssen nicht als eine MSI-DATEI gepackt werden. Alle Treiberdateien (beispielsweise inf und sys-Dateien) müssen als eine Reihe von Dateien verfügbar sein, die in einen Ordner für die Verwendung mit Deployment Image Servicing and Management (DISM) kopieren.

 - Treiber installiert werden müssen mithilfe von DISM offline.

Alle Tools, Dienstprogramme oder Agents auf Nano Server installiert sein müssen als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt werden.


### <a name="systemfundamentalsservernanodiagnostics"></a>System.Fundamentals.ServerNano.Diagnostics

Alle diagnostic Dienstprogramme für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Diagnosetools und Dienstprogramme zur Verwendung in einer Microsoft Azure-Stapel-Lösung müssen Management mithilfe einer der folgenden Methoden unterstützt:

 - Verwenden von Remote Windows PowerShell oder Windows-Verwaltungsinstrumentation (WMI).

 - Ein Befehlszeilentool verwenden, das ein Administrator auf dem Nano Server ausgeführt kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH.

Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.

Zusätzlich zu den obigen Systemen muss mit Windows Server Nano unterstützen Nano Server Recovery Console-Funktionen überprüfen Sie, dass alle entsprechenden Features in Nano Server verwendete Treiber ordnungsgemäß arbeiten.


### <a name="systemfundamentalsservernanofirmwareupdate"></a>System.Fundamentals.ServerNano.FirmwareUpdate

Alle diagnostic Dienstprogramme für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Firmware Update-Tools und Dienstprogramme für die Verwendung auf Windows Server Nano vorgesehen müssen Installation mithilfe einer der folgenden Methoden unterstützt:

 - Remote-Installation von Windows PowerShell oder WMI

 - Lokale Installation von ein Befehlszeilentool, das ein Administrator auf Nano Server ausführen kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH

Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.


### <a name="systemfundamentalsservernanomonitoringandtelemetry"></a>System.Fundamentals.ServerNano.MonitoringAndTelemetry

Alle diagnostic Dienstprogramme für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle monitoring Tools, Dienstprogramme und Agents müssen Installation mithilfe einer der folgenden Methoden unterstützt:

 - Remote-Installation von Windows PowerShell oder WMI
 
 - Lokale Installation von ein Befehlszeilentool, das ein Administrator auf Nano Server ausführen kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH
 
Wenn das Tool, Dienstprogramm oder Agent auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.

Microsoft Azure-Stapel insbesondere muss alle Überwachung ohne Agents sein und Agents auf den Hosts nicht zulässig. Siehe auch "if implementiert" Goldbarsch Anforderung unter System.Server.Manageability.Redfish.


### <a name="systemfundamentalsservernanooperateinservernano"></a>System.Fundamentals.ServerNano.OperateInServerNano

Alle diagnostic Dienstprogramme für die Verwendung mit Windows Server Nano vorgesehen müssen folgenden Anforderungen erfüllen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Der auf dem Windows Server Betriebssysteme bereitgestellten Hardwareplattform haben erheblich in den vergangenen zehn Jahren entwickelt. Sobald diese Grafik kleiner sind Systementwürfe für Kosten und Effizienz der Bereitstellung, die Kunden erwarten vollständig setup, bereitstellen, konfigurieren und verwalten diese mithilfe der minimale Befehlszeilenschnittstelle und automatisierte scripting von Windows Server Nano Hardware-Plattformen. Windows Server-Gerät, den Treiber in ähnlicher Weise wie für den Kunden diese Vorgänge ungehinderte unterschiedliche ermöglichen weiterentwickelt werden müssen.

Gerätetreiber muss veranschaulichen die Fähigkeit zum Installieren, konfigurieren Sie bedient werden und das Vorhandensein Abhängigkeit von der GUI nicht verwendet.

Hinweise zum Entwurf:

Alle Gerätetreiber, die diese Anforderung nicht erfüllt wird nicht auf Windows Server Nano-Systemen verwendet werden.


### <a name="systemfundamentalsservernanopatchandupdate"></a>System.Fundamentals.ServerNano.PatchAndUpdate

Patchen von Anforderungen für Windows Server Nano.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Patches und Updates können offline installieren, muss im Rahmen der Erstellung des Image oder online.


## <a name="systemfundamentalssigneddrivers"></a>System.Fundamentals.SignedDrivers

*Dieses Feature überprüft, ob signierte Treiber.*


### <a name="systemfundamentalssigneddriversbootdriverembeddedsignature"></a>System.Fundamentals.SignedDrivers.BootDriverEmbeddedSignature

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
 
*Design Notes:* Weitere Informationen dazu, wie Sie eingebettete Anmelden ein Boot-Start-Treiber, finden Sie unter "Schritt 6: Version Anmelden ein Treiber Bild Datei nach mithilfe einer eingebetteten Signatur" auf der folgenden Website:     <http://www.microsoft.com/whdc/winlogo/drvsign/kmcs_walkthrough.mspx>

Nachdem die Datei eingebettet angemeldet ist, verwenden Sie zum Überprüfen der Signatur SignTool. Überprüfen Sie die Ergebnisse, um sicherzustellen, dass der Stamm der SPC-Zertifikatkette für Kernel-Richtlinie "Microsoft Code Überprüfung Root." ist Der in der folgenden Befehlszeile wird die Signatur in der Datei toaster.sys überprüft:
```
    Signtool verify /kp /v amd64\\toaster.sys
    Verifying: toaster.sys
    SHA1 hash of file: 2C830C20CF15FCF0AC0A4A04337736987C8ACBE3
    Signing Certificate Chain:
    Issued to: Microsoft Code Verification Root
    Issued by: Microsoft Code Verification Root
    Expires: 11/1/2025 5:54:03 AM
    SHA1 hash: 8FBE4D070EF8AB1BCCAF2A9D5CCAE7282A2C66B3
    ...
    Successfully verified: toaster.sys
    Number of files successfully Verified: 1
    Number of warnings: 0
    Number of errors: 0
```

Im Windows Hardware Lab Kit wird dieser Anforderung mithilfe der eingebetteten Signatur Überprüfungstest getestet werden soll.


### <a name="systemfundamentalssigneddriversdigitalsignature"></a>System.Fundamentals.SignedDrivers.DigitalSignature

*System muss kompatible qualifizierte Geräte enthalten.*

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

Jeden Bus, Geräte und andere Komponenten in einem System müssen ihre jeweiligen Windows kompatibel Hardwareanforderungen erfüllen und Treibern, die entweder mit dem Windows-Betriebssystem-Installationsmedium enthalten sind, oder von Microsoft über das Windows Hardware Compatibility Programm digital signiert werden, die die Windows-Betriebssystem für übermittelt und des Versands mit entsprechen verwenden.

Beispielsweise wenn ein Logo qualifizieren ein System für Windows 10, klicken Sie dann alle Treiber für das System von Microsoft für Windows 10 signiert werden müssen oder Treiber, die auf dem Windows-10-Datenträger enthalten sein.  Alle Geräte im System muss auch Logo qualifiziert oder zertifiziert für Windows 10 sein.  Dies gilt für alle Versionen von Microsoft Windows.

Alle Geräte und Treiber müssen vollständig installiert werden, und enthält keine Problem Codes. 


## <a name="systemfundamentalssmbios"></a>System.Fundamentals.SMBIOS

*System Management BIOS SMBIOS-Anforderungen definiert Datenstrukturen in der Systemfirmware, die kann einen Benutzer oder eine Anwendung zum Speichern und Abrufen von Informationen zu dem Computer an.*


### <a name="systemfundamentalssmbiossmbiosspecification"></a>System.Fundamentals.SMBIOS.SMBIOSSpecification

*System-Firmware-Unterstützung für SMBIOS entspricht der SMBIOS-Spezifikation.*

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

System-Firmware muss Unterstützung für mit System Management BIOS Reference Specification Version 2.4 oder höher entspricht SMBIOS implementieren. Die Implementierung SMBIOS muss alle Konventionen und enthalten alle erforderlichen Strukturen und Felder wie angegeben in der SMBIOS-Spezifikation, Abschnitt 3.2, und befolgen Sie alle Konformität Anforderungen wie in Abschnitt 4 angegeben. Bit 2 im Feld BIOS Merkmale Erweiterung Byte 2 muss (Abschnitt 3.3.1.2.2 der Spezifikation) festgelegt werden. Die Länge der Tabelle type1 (Systeminformationen) muss mindestens 1Bh Bytes (einschließlich SKU-Nummer und Freunde Felder aus der Spezifikation Version 2.4).

Darüber hinaus müssen die folgenden Felder Werte ungleich Null sein, in denen das Computersystem oder Systemkomponente Computer genau beschrieben:

 - (Tabelle 0, offset 04h) BIOS-Anbieter

 - (Tabelle 0, offset 08h) Datum der BIOS-Freigabe

 - (0 Tabelle, offset 14h) BIOS-Version Hauptversion<sup>1</sup>

 - (Tabelle 0, offset 15h) BIOS Nebenversion Version Version<sup>1</sup>

 - (Tabelle 1 offset 04h) System Hersteller<sup>2</sup>

 - (Tabelle 1 offset 05h) System Produktname<sup>2</sup>

 - (Tabelle 1 offset 08h) Universelle eindeutige ID-Nummer

 - (Tabelle 1 offset 19h) System SKU Zahl<sup>2</sup>

Microsoft empfiehlt die folgenden Felder nicht-Null-Werte haben, in denen das Computersystem oder Systemkomponente Computer genau beschrieben:

 - (Tabelle 0, offset 05h) BIOS-Version

 - (Tabelle 0, offset 16h) Eingebettete Controller Version Hauptversion<sup>3</sup>

 - (0 Tabelle, Abstand 17h) Eingebettete Controller Nebenversion Version<sup>3</sup>

 - (Tabelle 1 offset 06h) Systemversion

 - (Tabelle 1, Offset 1Bh) System-Produktfamilie<sup>2</sup>

 - (Tabelle 2, offset 04h) Hauptplatine Hersteller

 - (Tabelle 2, offset 05h) Hauptplatine Produkt

 - (Tabelle 2, offset 06h) Hauptplatine Version

<sup>1</sup> diese Felder darf keine Werte gleich 0FFh haben.

<sup>2</sup> diese Felder erhalten Hervorhebung als Felder, die zur Identifizierung von Konfigurationen für Telemetrie und Wartung eindeutige System verwendet wird. Der Hersteller, Produktname, SKU-Nummer und -Produktfamilie Felder darf nicht länger als 64 Zeichen lang sein. Vermeiden Sie führende oder nachfolgende Leerzeichen oder andere nicht sichtbaren Zeichen.

<sup>3</sup> , verfügt das System ein Feld erweiterbaren Controller-Firmware eingebettet. Diese Werte sollten nicht 0FFh gleich sein.

Hinweise zum Entwurf: SKU-Nummer wurde an ein erforderliches Feld verschoben, um Telemetrie reporting zu verbessern. Wir empfehlen OEM Seien Sie vorsichtig Hersteller konsistent ausfüllen und SKU-Nummer mit einem Wert eingeben, die identifizieren können, was eine eindeutige Systemkonfiguration für Telemetrie und Wartung der OEM betrachtet.


## <a name="systemfundamentalsstorageandboot"></a>System.Fundamentals.StorageAndBoot

*In diesem Abschnitt werden die Anforderungen für Speicher und Boot-Geräte.*


### <a name="systemfundamentalsstorageandbootbootperformance"></a>System.Fundamentals.StorageAndBoot.BootPerformance

*Bootgeräte in Systemen, die verbunden Standby unterstützen müssen folgenden Anforderungen erfüllen.*

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

Die folgenden Anforderungen gelten für Boot-Geräte in Systemen, die verbunden Standby unterstützen.

Zusätzlich zu SATA und USB-basierten Windows-Plattform unterstützt SD und eMMC Speicher. Ein Gerät eMMC kann entweder ein (Boot) Systemdatenträger oder als einen Datenträger verwendet werden, aber ein SD-Device kann nur als einen Datenträger verwendet werden.

| Flash-Typ    | Boot | Datenträger |
|---------------|------|-----------|
| eMMC 4.5 +     | Ja  | Ja       |
| SD 2.0 oder 3.0 | Nein   | Ja       |

ACPI Schnittstellen müssen angeben, ob das Speichergerät intern oder extern ist und ob es austauschbaren oder fest ist.

\_RMV muss definiert werden, im ACPI-Namespace für alle eingebetteten Geräte zu einer SD-Hostcontroller, wobei 0 als nicht entfernbar definiert wird. \_RMV kann optional für externe Slots als 1 definiert werden.

Die folgenden Parameter müssen innerhalb der "Speicher Klasse-spezifische Informationen" von der ACPI zurückgegeben werden soll definiert sein \_DSM-Methode für ein Speichercontroller SD/eMMC:

 - Anzahl der Sockets

 - Socketadressen

Unterstützung von SD/eMMC Speichercontroller GPIO Karte Erkennung.

Wenn eMMC als primäre Boot-Gerät zu verwenden, muss der Speicher eMMC Hardware partitioniert so, dass der Boot kritische Teil der EFI-Firmware in einem Bereich des Geräts gespeichert, die nicht zugegriffen werden von Windows sein.

Die CPU-Hersteller und/oder Firmware Anbieter müssen die Software-Tools zum Verwalten und aktualisieren Sie die Firmware erforderlich sind.

Die folgenden Anforderungen gelten für Boot Speichermedien und werden mit der kleinere der 2 % getestet oder 1GB freier Speicherplatz.


<table>
<thead>
<tr class="header">
<th>Feature</th>
<th>Span-Größe</th>
<th>Spezifikation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Potenz</td>
</tr>
<tr class="even">
<td>Max im Leerlauf</td>
<td>-</td>
<td>&lt;= 5 mW</td>
</tr>
<tr class="odd">
<td>Zufällige Leistung</td>
</tr>
<tr class="even">
<td>4KB Schreib-IOPs</td>
<td>1 GB</td>
<td>&gt;= 200</td>
</tr>
<tr class="odd">
<td></td>
<td>* 5 GB</td>
<td>&gt;= 50</td>
</tr>
<tr class="even">
<td></td>
<td>†10 GB</td>
<td>&gt;= 50</td>
</tr>
<tr class="odd">
<td>64KB Schreib-IOPs</td>
<td>1 GB</td>
<td>&gt;= 25</td>
</tr>
<tr class="even">
<td>4KB lesen IOPs</td>
<td>* 5 GB</td>
<td>&gt;= 2000</td>
</tr>
<tr class="odd">
<td></td>
<td>†10 GB</td>
<td>&gt;= 2000</td>
</tr>
<tr class="even">
<td>4KB 2:1 Lese-/Schreibvorgänge IOPs</td>
<td>1 GB</td>
<td>&gt;= 500</td>
</tr>
<tr class="odd">
<td></td>
<td>*5GB</td>
<td>&gt;= 140</td>
</tr>
<tr class="even">
<td></td>
<td>†10 GB</td>
<td>&gt;= 140</td>
</tr>
<tr class="odd">
<td>Sequentielle Leistung</td>
</tr>
<tr class="even">
<td>Schreiben Sie Geschwindigkeit (64 KB e/a)</td>
<td>* 5 GB</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="odd">
<td></td>
<td>†10 GB</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="even">
<td>Schreiben Sie Geschwindigkeit (1 MB e/a)</td>
<td>* 5 GB</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="odd">
<td></td>
<td>†10 GB</td>
<td>&gt;= 40 MB/s</td>
</tr>
<tr class="even">
<td>Lesen Sie Geschwindigkeit (64 KB e/a)</td>
<td>* 5 GB</td>
<td>&gt;60 MB/s =</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>‡&gt;= (120 MB/s)</td>
</tr>
<tr class="even">
<td></td>
<td>†10GB</td>
<td>&gt;60 MB/s =</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>‡&gt;= (120 MB/s)</td>
</tr>
<tr class="even">
<td>Gerät e/a-Wartezeit</td>
</tr>
<tr class="odd">
<td>Maximale Wartezeit</td>
<td>-</td>
<td>&lt;500 Millisekunden</td>
</tr>
</tbody>
</table>


\*Gilt nur für Geräte mit 16 GB oder weniger Zentralspeicher.

† Gilt nur für Geräte mit mehr als 16 GB Zentralspeicher.

‡ Gilt nur, wenn das Gerät HS200 Lage ist.

Zusätzliche Wartezeit e/a-Anforderung:

Maximal **20 Sekunden** -Gesamtsumme der Benutzer wahrnehmbar e/a-Wartezeiten über einen beliebigen Zeitraum **1 Stunde** einer Benutzer-Vertreter Arbeitslast, wobei eine Benutzer-wahrnehmbar e/a definiert ist, dass eine Wartezeit von mindestens 100 Millisekunden.


### <a name="systemfundamentalsstorageandbootencrypteddrive"></a>System.Fundamentals.StorageAndBoot.EncryptedDrive

*Systeme, die im Lieferumfang von einem verschlüsselte Laufwerk als einem Speichergerät Boot müssen Sicherheitsprotokolle-Befehl, um sicherzustellen, dass die Daten im Ruhezustand immer geschützt sind unterstützen.*

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

Wenn verschlüsselte Laufwerk (**System.Fundamentals.StorageAndBoot.EncryptedDrive**) Unterstützung für einen UEFI-basierten Client-System oder Serversysteme implementiert wird, gelten die folgenden Anforderungen:

1.  Das System benötigen ein TPM 1.2 oder TPM 2.0.

2.  Das System MUSS die EFI implementieren\_SPEICHER\_SICHERHEIT\_BEFEHL\_PROTOKOLL entweder aus:

    ein.  Unterstützung von vertrauenswürdigen Befehl in UEFI 2.3 + UEFI Mantis Änderungsnummer 616 oder

    b.  UEFI 2.3.1 (ENGL.)

3.  Die Implementierung von vertrauenswürdigen Netzwerke Gruppe Plattform zurücksetzen Angriff Risikominderung Spezifikation (<http://www.trustedcomputinggroup.org/resources/pc_client_work_group_platform_reset_attack_mitigation_specification_version_10>) MUSS *uneingeschränkt* dieses Problem TPer zurücksetzen (OPAL v2. 0 in Abschnitt 3.2.3) für alle Szenarien bei jedem Speicher deaktiviert ist.

4.  EFI\_SPEICHER\_SECURITY\_BEFEHL\_PROTOKOLL und den Befehl TPer zurücksetzen MÜSSEN im Basiskalender UEFI Bild (nicht in einem separaten Bild eines Treibers UEFI) enthalten sein.

5.  Das System MUSS alle verschlüsselt Laufwerke auflisten und TPer zurücksetzen MUSS vor dem Ausführen von Firmware-Code nicht des Herstellers Plattform im Basiskalender UEFI Bild ausgestellt werden.

6.  TPer zurücksetzen MÜSSEN werden unabhängig davon, ob das TPM Besitz übernommen oder nicht wurde ausgestellt.

 Hinweis: Die Aktion des Zurücksetzens TPer treten weiter unten in den Startvorgang als die Arbeitsspeicher-clear-Aktion, da es eine Abhängigkeit EFI verfügt\_SPEICHER\_SECURITY\_BEFEHL\_PROTOKOLL.


### <a name="systemfundamentalsstorageandbootsatabootstorage"></a>System.Fundamentals.StorageAndBoot.SATABootStorage

*System mit SATA-Boot Speicher muss die Anforderungen erfüllen.*

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

Verwenden von Windows auf Boot-Unterstützung AHCI-Hostcontroller muss mit AHCI kompatibel sein.

| Host Controller-Schnittstelle | Bearbeitung      |
|---------------------------|---------------|
| AHCI                      | 1.1, 1.2, 1.3 |

System mit SATA-Controller muss Unterstützung für AHCI-Modus aktivieren.

Extern verbundenen SATA-Geräte (eSATA) werden nicht für Boot-Speicher unterstützt.

Wenn SATA als primäre Boot-Gerät verwendet wird, muss zum Sicherstellen der Zuverlässigkeit und verhindern unbeabsichtigten Löschens der Firmware, die das Gerät nicht funktioniert, wird möglicherweise der Boot kritische Teil der Firmware UEFI auf einem separaten Speichergerät befinden, die nicht vom Host Betriebssystem zugegriffen werden. Die CPU-Hersteller und/oder Firmware Anbieter müssen die Software-Tools zum Verwalten und aktualisieren Sie die Firmware erforderlich sind.

Bei Verwendung in Systemen, die verbundenen Standby unterstützen muss das SATA-Gerät im Abschnitt für **System.Fundamentals.StorageAndBoot.BootPerformance**erwähnt Energiebedarf erfüllen.


## <a name="systemfundamentalsstorageclassmemory"></a>System.Fundamentals.StorageClassMemory

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalsstorageclassmemory"></a>System.Fundamentals.StorageClassMemory

*System.Fundamentals.StorageClassMemory*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

 - Plattformen unterstützt die Verwendung von Klasse Speicher Geräten müssen die NFIT-Tabelle von ACPI 6.1 definierten implementieren.

 - Firmware keine Geräte Speicher-Klasse die Adresse 0xFFFF00000000 im System-Adressraum beginnend 4 GB Region zugeordnet.


### <a name="systemfundamentalsstorageclassmemorynvdimm-ndsmcompliance"></a>System.Fundamentals.StorageClassMemory.NVDIMM N.DSMCompliance

*System.Fundamentals.StorageClassMemory.NVDIMM N.DSMCompliance*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung:**

Plattformen unterstützt die Verwendung von NVDIMM-N-Geräte verfügen, zur Einhaltung der *Microsoft \_DSM für JEDEC Byte-Addressable Energy-Backed Schnittstelle NVDIMMs* -Spezifikation, befindet sich hier:

 - <http://go.Microsoft.com/fwlink/?LinkId=620289>

Hinweis: NVDIMM-N-Geräte werden durch die Firmware NFIT Tabelle gemäß Definition im ACPI 6.1 identifiziert.


### <a name="systemfundamentalsstorageclassmemorynvdimm-npersistence"></a>System.Fundamentals.StorageClassMemory.NVDIMM N.Persistence

*System.Fundamentals.StorageClassMemory.NVDIMM N.Persistence*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

NVDIMM-N-Geräte unterstützen entsprechend auslösen müssen Plattformen speichern / Wiederherstellungsvorgängen für geplante und ungeplante Power-Zyklen des Systems. Es wird erwartet, dass Daten nach Stromausfall, beibehalten werden, sofern das Gerät zum bewaffneten und bereit zum Zeitpunkt der Stromausfall eine Sicherung werden angezeigt.

Hinweis: Es wird dringend empfohlen, dass durch die Implementierung von ADR Support in der Plattform Persistenz erreicht wird.


### <a name="systemfundamentalsstorageclassmemorynvdimm-nhealthnotificationsupport"></a>System.Fundamentals.StorageClassMemory.NVDIMM N.HealthNotificationSupport

*System.Fundamentals.StorageClassMemory.NVDIMM N.HealthNotificationSupport*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Plattformen unterstützen NVDIMM-N-Geräten müssen NFIT Health Ereignisbenachrichtigung Support implementieren, gemäß ACPI 6.1 und durch die folgenden \_DSM-Funktion:

 - Feld "-Ereignis Benachrichtigung unterstützt" Register-FUNKTIONEN ist 1, von dem Feld "Funktionen" von "Get NVDIMM N Kennung" (1) zurückgegeben

 - EREIGNIS registrieren\_BENACHRICHTIGUNG\_UNTERSTÜTZUNG muss anzugeben, dass alle Benachrichtigungen unterstützt werden von der Option "Benachrichtigungsereignisse unterstützt" zurückgegeben "Abrufen NVDIMM N Identifizierung" (1),


## <a name="systemfundamentalssystemaudio"></a>System.Fundamentals.SystemAudio

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalssystemaudioaudio"></a>System.Fundamentals.SystemAudio.Audio

*Systeme enthalten Audiogeräte, die Anforderungen an das Windows-Logo entsprechen.*

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

Systeme müssen alle **Device.Audio** Anforderungen entsprechen.


### <a name="systemfundamentalssystemaudiomicrophonelocation"></a>System.Fundamentals.SystemAudio.MicrophoneLocation

*Mikrofon Speicherort Reporting-Anforderung*

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

1.  Alle aktiven integrierte-Position einzelnes Element Mikrofonen und integrierte-Position Mikrofon Arrays (mehrere kombinierten Elementen) auf einem System müssen für unabhängige Capture verfügbar sein.

2.  Systeme mit keine integrierte-Position Mikrofon Arrays, aber mit mehreren integrierten-Position Mikrofonen (z. B. vorne/hinten), UND hat keine kombinierte Mikrofon genau mit GeoLocation = "Vorne" (die als das standardmäßige Mikrofon auf dem System festgelegt werden).

3.  Systeme mit mehreren integrierten-Position Mikrofon Arrays benötigen genau eine Vorlage mit GeoLocation = "Vorne".

4.  Mikrofon Arrays mit "n" Elementen müssen ROH Audio an das System übermitteln. ROH-Format benötigen "n" Kanäle und die Daten direkt in die Mikrofon-Elemente frei von Signal Processing stammen müssen.

5.  Wenn ein Mikrofon und eine Kamera physisch am selben Standort sind muss integrierte dann erwähnt Standortinformationen für jede übereinstimmen.

6.  Bei Geräten mit mehreren Mikrofonen für integrierte-Position oder mehrere Arrays sollte die Namen der Endpunkte im System eindeutig sein. An einen eindeutigen Namen, stehen einige verschiedene Methoden mit KSPROPERTY\_PIN\_NAME, IPinName und INF anheften Beschreibung namensregistrierung GUID.


### <a name="systemfundamentalssystemaudiosystemuseshdaudiopinconfigs"></a>System.Fundamentals.SystemAudio.SystemUsesHDAudioPinConfigs

*System verwendet die HD Audio Gerät Pin Konfiguration Register logische von der Klasse Windows LF HD Audiotreiber unterstützten Geräte verfügbar machen.*

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

Wenn der Plug & Play-ID eine HD-Audiogerät als kompatibel mit einer der vom audio-Klasse Treiber mit Windows gepackt entspricht, muss das Gerät beim dieser Treiber mit grundlegenden Funktionen für alle Endpunkte angeben. Audiogerät muss führen Sie Microsoft HD Audio Pin programming Konfigurationsrichtlinien und Verfügbarmachen von Geräten in basierend auf Audiogerät Funktionalität Hardwareressourcen Bereiche unterteilt.

Finden Sie die Pin Konfigurationsrichtlinien für High Definition Audiogeräte Whitepaper unter <http://go.microsoft.com/fwlink/?LinkId=58572>.


## <a name="systemfundamentalssystempcicontroller"></a>System.Fundamentals.SystemPCIController

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalssystempcicontrollerpcirequirements"></a>System.Fundamentals.SystemPCIController.PCIRequirements

*Systemgeräte und Firmware erfüllen PCI-Anforderungen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

PCI Express-Geräten müssen mit PCI-Base Express Spezifikation 1.1 oder höher entsprechen, sofern nicht anders angegeben unten.

Umgekehrte Bridge Implementierungen gemäß Definition in Anhang A von der PCI-Express PCI/PCI-X-Brücke.
Spezifikation werden in Windows nicht unterstützt.
Reverse-Brücke, die die Richtlinien und Empfehlungen in Anhang A von der PCI-Express PCI/PCI-X Bridge-Spezifikation, Version 1.0 gemäß entspricht, wird nicht unterstützt.

System-Firmware deaktiviert die erweiterten (VC0-nicht) virtuellen Kanäle in PCI Express-Geräten.
System-Firmware setzt das VC++ Enable-Bit (PCI Express Base-Spezifikation, Version 1. 0a, Abschnitt 7.11.7, "VC++ Ressource Steuerelement registrieren: bit 31") auf 0 für alle erweitert (nicht VC0) virtuelle Kanäle in allen PCI Express-Geräten. Dies gilt nicht für PCI Express High Definition Audio-Controller die Code 04-Klasse und Unterklasse Code 03. verwendet werden, weil erweiterte Unterstützung für VC++ Hardware ist optional, dieser Anforderung das Szenario-Adressen in dem inkompatible VC++ Hardware Implementierungen Zuverlässigkeit des Systems, Stabilität und Leistungsprobleme verursachen könnten. Hardwareanbieter werden empfohlen, Microsoft definieren die Zukunft von erweiterten virtuellen Kanal Support entwickelt.

System-Firmware für PCI-X Modus 2-fähig und PCI Express-Systeme implementiert MCFG-Tabelle für den Zugriff auf die Speicherplatz. PCI-X-Modus 2-fähige und PCI Express-Systemen müssen die MCFG ACPI-Tabelle in PCI-Firmware implementieren. Spezifikation, Revision 3.0.The Konfigurationsbereich Modus 2 PCI-X und PCI Express-Geräten muss über die Konfiguration Speicher zugeordnete Speicherplatz Region in dieser Tabelle definiert zugegriffen werden.

PCI-PCI-Brücken einhalten PCI-PCI-Brücke-Architektur-Spezifikation

PCI-PCI-Brücke Architektur-Spezifikation, Version 1.2 müssen alle PCI-PCI-Brücken entsprechen.

Virtuelle Brücken, die mit PCI Express erfüllen, auch PCI-PCI-Brücke Architektur-Spezifikation, Version 1.1 einzuhalten. Darüber hinaus VGA 16-Bit-decodieren (Abschnitt 3.2.5.18, "Bridge Steuerelement registrieren, bit 4") und SSID und SSVID (Abschnitt 3.2.5.13) von PCI-PCI-Brücke-Architektur-Spezifikation, Version 1.2, muss auch unterstützt werden.
Unterstützung von SSID und SSVID ist nicht erforderlich, bis zum 1. Januar 2011. Wenn implementiert, erfüllen SSID und SSVID die Spezifikation. SSVID ist nicht erforderlich, damit PCIe PCI/PCI-X Brücken.

X64-basierten System bietet 64-Bit-Unterstützung im PCI-Teilsystem. X64-basierte Systeme alle PCI-Brücken auf der Hauptplatine müssen für den eingehenden Zugriff Dual-Access-Zyklus (DAC) unterstützen und DAC-fähigen Geräte müssen nicht verbunden unter nicht-DAC-fähigen Brücken, wie beispielsweise auf Netzwerkadapter mit.

Alle 64-Bit-Adapter müssen DAC-fähig sein. Diese DAC Anforderung gilt nicht für ausgehende Zugriffe auf PCI-Geräte. Jedoch muss die System-Firmware für Systeme in denen DAC auf ausgehende Zugriffe auf PCI-Geräte nicht unterstützt wird, nicht Forderung das, dass die Bus Blende oberhalb der 4-GB-Grenze platziert werden kann.


## <a name="systemfundamentalssystemusb"></a>System.Fundamentals.SystemUSB

*Dieser Abschnitt enthält die Anforderungen für Systeme mit USB-Hostcontroller.*


### <a name="systemfundamentalssystemusbexternalusboncsisehciorxhci"></a>System.Fundamentals.SystemUSB.ExternalUSBonCSisEHCIorXHCI

*Externer USB-Anschlüsse auf System, die verbundenen Standby unterstützen müssen EHCI oder XHCI sein.*

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

USB-Hostcontroller auf Systeme, die Standbymodus verbunden unterstützen müssen xHCI (eXtensible Host Controller Interface) oder EHCI (Enhanced Host Controller Interface) implementieren.  Legacy-Companion-Controller (UHCI/OHCI) werden nicht unterstützt. 

Alle verfügbar gemachten Ports müssen alle kumulativ langsamer als die maximale Geschwindigkeit der Hostcontroller, zum Aktivieren der Unterstützung von älteren Geräte, einschließlich Tastatur und Maus unterstützen.

| Erforderliche Geschwindigkeit-Unterstützung | EHCI Port (USB 2.0) | XHCI Port (USB 3.x) |
|------------------------|---------------------|---------------------|
| Niedrige Geschwindigkeit              | Ja                 | Ja                 |
| Full-Geschwindigkeit             | Ja                 | Ja                 |
| Hochgeschwindigkeits-               | Ja                 | Ja                 |
| Super Geschwindigkeit            | Nein                  | Ja                 |

Transaktion Übersetzer (TTs), mit dem EHCI-Hostcontroller integriert sind nicht standardisiert, aber der Windows-EHCI-Treiber unterstützt mehrere Implementierungen von einer TT Controller-integriert. Die unterstützte integrierte TT Implementierung muss in ACPI identifiziert werden mithilfe der \_HRV Revisionsnummer der Hardware für den USB-Controller. Wenden Sie sich an das Team USB zu bestimmen, ob die Implementierung unterstützt wird und Weitere Informationen dazu, welche \_HRV Wert berichtet werden soll.

Wenn USB-EHCI-Controller keine integrierte TT Funktion müssen über einen eingebetteten Rate übereinstimmenden Hub extern verfügbar gemachten Ports weitergeleitet werden.

USB-Hostcontroller auf Systemen, Standby verbunden unterstützen, werden empfohlen für verbesserte Leistungseffizienz und Leistung, mindestens USB-3.x kompatibel mit einem XHCI Domänencontroller in der SoC oder Chipsatz integriert. Das Betriebssystem unterstützt standard EHCI und XHCI Controller einschließlich Debug registriert.

| USB-Host Controller-Schnittstelle     | Empfehlung            |
|-----------------------------------|---------------------------|
| UHCI/OHCI Companion-Controller   | Nicht unterstützte             |
| EHCI                              | Unterstützt                 |
| XHCI (einschließlich Debug-Funktion) | Unterstützt und empfohlen |

 

### <a name="systemfundamentalssystemusbsuperspeedcapableconnectorrequirements"></a>System.Fundamentals.SystemUSB.SuperSpeedCapableConnectorRequirements

*Jeder verfügbar gemachte SuperSpeed Connector Lage SuperSpeed, hoch, vollständig unterstützt und niedrig Geschwindigkeit USB-Geräte über einen xHCI Controller weitergeleitet.*

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

xHCI Controller sind vollständige abwärtskompatibel mit SuperSpeed, hoch, und geringe Geschwindigkeit USB-Geräte. Abwärtskompatibilität ist kompatible definiert, wie alle USB-Geräte auflisten und mit ihren vorgesehenen Geschwindigkeit fungieren. Mehr als einen xHCI Controller kann auf einem System vorhanden sein, solange die SuperSpeed-fähigen Anschlüsse ordnungsgemäß weitergeleitet werden. EHCI-Controller möglicherweise auch auf dem System vorhanden sein. SuperSpeed-fähigen Anschlüsse müssen jedoch nicht über diese weitergeleitet werden.



### <a name="systemfundamentalssystemusbsystemexposesusbport"></a>System.Fundamentals.SystemUSB.SystemExposesUSBPort

*Systeme werden empfohlen, um mindestens ein Benutzer zugänglichen USB-Anschluss verfügbar zu machen.*

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

Systeme werden empfohlen, um mindestens einen externen USB-hostPort verfügbar zu machen. Wenn ein System solche Ports verfügbar macht, gilt die folgende Anforderung.

USB-Anschlüsse *Mus*t ordnungsgemäß in ACPI mit beschrieben werden die \_UPC (USB-Anschluss Funktionen) Paket Type-Parameter gemäß Definition in der Spezifikation ACPI 6.1 Abschnitt 9.14 zeigt. Anhand dieser Informationen können Sie Windows, um zu bestimmen, wann ein USB-C Port verfügbar gemacht wird, oder wenn ein Micro-A/B-Port verfügbar gemacht wird (d. h., ID Pin Erkennung erforderlich ist).

Ist das System Formfaktor zu dünn, um einen A USB-Anschluss verfügbar zu machen, ist es empfohlen, einen Typ C Port verfügbar zu machen und zulässige Micro-A/B-Port verfügbar machen.  Finden Sie in der folgenden Tabelle für die vollständige Liste der Optionen. 

Während USB 2.0-fähige Controller zulässig sind, werden die 3.1 XHCI USB-Hostcontroller bevorzugt. Die USB-Anschlüsse müssen vollständig der USB-3.1 oder USB 2.0-Spezifikation entsprechen. USB-3.1 Verbinder müssen ordnungsgemäß 900mA 3.1 USB-Geräte und 500 mA USB 2.0- und 1.1-Geräte unterstützen. USB 2.0-Anschlüsse müssen 500 mA USB 2.0- und 1.1-Geräte ordnungsgemäß unterstützen.

Es ist einen Adapter enthalten, der den Port von Micro USB oder USB-Typ-C in USB A. konvertiert optional Wenn Sie einen Adapter gebündelt werden, müssen die Adapter-Funktionen, die der verfügbar gemachte Verbindung über USB-Hostcontroller übereinstimmen.

| Externe USB-Ports                                                | Empfehlung |
|-------------------------------------------------------------------|----------------|
| Standard-USB-eine Ports                                            | Empfohlen    |
| USB-Typ-C-Ports                                                | Empfohlen    |
| Standard-USB-ein Ports + USB-Typ-C-Ports                       | Empfohlen    |
| Micro-USB-A / B-Port + 1 oder mehrere Standard USB A Port                | Unterstützt      |
| Micro-USB-A / B (Host + Funktion Debuggen) Port                        | Unterstützt      |
| USB-Micro B Port + 1 oder mehrere Standard USB A Port                  | Unterstützt      |
| Proprietäre Docking Anschluss mit USB-Hostcontroller und/oder Debug-Funktionalität | Unterstützt      |
| Mini-USB-A, A / B oder B Port                                         | Nicht unterstützt  |
| Proprietäre USB-hostPort                                         | Nicht unterstützt  |

 

Ein Standard-A-zu-A-Kabel definierten gemäß der Spezifikation USB 3.1 kann verwendet werden, um XHCI Host Debug Transport aus einen USB-A-Anschluss verfügbar zu machen. Diese Ports müssen tolerieren wird Back-basiertes, und es wird dringend empfohlen, dass der standard A USB-Anschluss auf dem VBus Linie. integrierten Schutz gegen einen kurzen aufweisen kann auftreten, wenn der USB-Anschluss an einen anderen Host verbunden ist, wenn im Debugmodus nicht ordnungsgemäß konfiguriert ist. Typ-C-Ports, die XHCI Host Debuggen verfügbar machen können denselben Mechanismus als Standard-A-Ports verwenden, indem Sie zuerst eine Verbindung einen Adapter C A-nimmt an den Anschluss Typ-C.

Wenn ein System mehrere duale Rolle-fähigen Anschlüsse verfügbar macht, sollten nur einen Port zu einem bestimmten Zeitpunkt im Funktionsmodus. Falls der Micro-USB-B Port keine Funktionalität zusätzlich zu debuggen, *er im Batteriefach oder hinter einem leicht austauschbaren Abdeckung ausgeblendet muss*bereitstellt. Um die Einhaltung der USB-WENN Anforderungen an die VBUS nicht auf den Port Micro / A/B bis der Widerstand auf Grund des Drehbezugspunkts ID des USB-Micro A bestätigt werden müssen / B Port weniger als 10 Ohm ist. Dadurch wird verhindert, dass ein zu umgehen, wenn ein Benutzer eine Verbindung B Micro-USB-Kabel an einen anderen USB-Host, beispielsweise eines Desktops herstellt. Alternativ kann der Port kurzen Protection Kreis für VBus implementieren.


### <a name="systemfundamentalssystemusbtestedusingmicrosoftusbstack"></a>System.Fundamentals.SystemUSB.TestedUsingMicrosoftUsbStack

*Systeme mit xHCI Controller müssen bei Microsoft xHCI getestet werden, den, die Stack installiert.*

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

Systeme mit Domänencontrollern Extensible Host Controller Interface (xHCI) müssen mit Microsoft xHCI getestet werden, die Stack installiert und aktiviert.


### <a name="systemfundamentalssystemusbusbdevicesandhostcontrollersworkafterpowercycle"></a>System.Fundamentals.SystemUSB.USBDevicesandHostControllersWorkAfterPowerCycle

*Alle USB-Geräte und Hostcontroller beim Fortsetzen aus dem Standbymodus, im Ruhezustand ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene Zurücksetzen des USB-Hostcontroller.*

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

Alle USB-Geräte und Hostcontroller beim Fortsetzen aus dem Standbymodus, im Ruhezustand ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene Zurücksetzen des USB-Hostcontroller.

*Hinweise zum Entwurf:*

Registrierungsschlüssel, die die unten aufgeführten KB ForceHCResetOnResume dokumentiert ist nicht für die Geräte ordnungsgemäß nach Resume in Windows 7 oder höher. 
<http://support.Microsoft.com/kb/928631> 

Beachten Sie, dass eine bekannte Gruppe von vorhandene Geräten derzeit führen erfordern eine erzwungene zurücksetzen auf fortsetzen, sollten diese Geräte in einer Liste, die durch das Betriebssystem, wodurch diese Geräte bei Resume zurückgesetzt wird gehalten behandelt werden. Das Ziel dieser Anforderung ist, um sicherzustellen, dass diese Liste der Geräte die benötigen ein zurücksetzen nach Resume nicht wächst angezeigt wird und dass Geräte ohne zurückzusetzende dem Standbymodus Statusübergänge ordnungsgemäß verarbeiten können.

Ein Zurücksetzen der gesamte USB-Hostcontroller Ergebnisse in deutlich mehr Zeit, die für alle USB-Geräte verfügbar wird nach dem System fortsetzen, da es möglicherweise nur ein Gerät bei Adresse 0 zu einem Zeitpunkt, hat diese Enumeration für alle USB-Geräte auf dem Bus serialisiert werden soll. Wir haben auch gesehen zurücksetzen den Hostcontroller einen ungültigen SE1 Signal Status auf einige Hostcontroller dazu führen, dass kann die einige USB-Geräte hängen oder drop aus dem Bus wiederum verursachen. Darüber hinaus können nicht Geräte alle privaten Status über dem Standbymodus fortsetzen verwalten, wie diesen Status auf Zurücksetzen verloren.


### <a name="systemfundamentalssystemusbusbtypeccharging"></a>System.Fundamentals.SystemUSB.USBTypeCCharging

*USB-Typ-C aufgeladen Fällen werden unterstützt.*

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

Wenn ein System ein USB-Typ-C-Ports, das zum Berechnen des Systems verwendet werden kann enthält, muss dieser Port die folgenden Anforderungen zusätzlich zu den USB-Typ-C und PD Spezifikationsdialogfeld unterstützen:

 - Das System kann über den Typ C aus eine deaktivierte Batterie (mit aufgeladen, die im Lieferumfang des Systems / wird mit dem System verkauft) berechnen

 - Für mehrere USB-Typ-C-Systemen empfiehlt es sich, dass alle USB-Typ-C-Ports auf dem System verwendet werden können, belasten des Systems Benutzer Verwechslungen zu vermeiden.


### <a name="systemfundamentalssystemusbusbtypeccertifiedcables"></a>System.Fundamentals.SystemUSB.USBTypeCCertifiedCables

*Lieferumfang USB-Typ-C-Systeme und Geräte, die zum gehören mit Kabel zertifizierten Kabel*

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

Wenn ein System oder Gerät USB-Typ-C ist und müssen ein USB-Typ-C Kabel oder ein Adapter, das Kabel und/oder Adapter im Lieferumfang von USB-WENN zertifiziert.

Darüber hinaus, wenn die USB-Typ-C Kabel oder Adapter für eine alternative Modus Standard- und der Branche, die besitzt, dass eine entsprechende Zertifizierung-Standard besitzt die verwendet wird, muss das Kabel oder Adapter diese Zertifizierung abgerufen werden.


### <a name="systemfundamentalssystemusbusbtypecucm"></a>System.Fundamentals.SystemUSB.USBTypeCUCM

*USB-Typ-C Systeme müssen UCM unterstützen.*

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

Systeme mit lokalen USB-C-Ports (z. B. direkt auf dem System im Vergleich zu auf einem Gerät entfernbar oder separat oder Andocken, die nicht UCSI implementieren) müssen mit einem 3rd Party UCMCx Clienttreiber liefern. 3rd Party UCMCx Clienttreiber müssen gemäß den Anweisungen in der folgenden MSDN-Dokumentation implementiert werden:

 - <https://msdn.Microsoft.com/en-us/library/Windows/Hardware/mt188011 (v=vs.85).aspx>

Der Client-Treiber UCMCx ist erforderlich, um die folgenden APIs implementieren:

 - UcmInitializeDevice

 - UcmConnectorCreate

 - UcmConnectorTypeCAttach

 - UcmConnectorTypeCDetach

 - UcmConnectorTypeCCurrentAdChanged

 - UcmConnectorChargingStateChanged

Wenn das System oder Controller Stromversorgung unterstützt, gelten die folgenden zusätzlichen Anforderungen:

 - UcmConnectorPowerDirectionChanged

 - UcmConnectorPdSourceCaps

 - UcmConnectorPdPartnerSourceCaps

 - UcmConnectorPdConnectionStateChanged

Wenn das System oder Controller dual Rolle Ports verfügbar macht, gelten die folgenden zusätzlichen Anforderungen:

 - UcmConnectorDataDirectionChanged


### <a name="systemfundamentalssystemusbusbtypecucsi"></a>System.Fundamentals.SystemUSB.USBTypeCUCSI

*USB-Typ-C Systeme, UCSI unterstützen, muss USCI ordnungsgemäß implementieren.*

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

Wenn ein USB-Typ-C-System verfügt über lokale USB-C-Ports (z. B. direkt auf dem System im Vergleich zu auf einem Gerät entfernbar oder separat oder verankern) und seine PD/USB-Typ-C Zustandsautomat in einem eingebetteten Controller implementiert, implementieren UCSI v1. 0 (oder höher). Darüber hinaus müssen sie die folgenden optionalen Features aus der Spezifikation UCSI implementieren.

*Befehle*

 - ERSTE\_ALTERNATIVE\_MODI

 - ERSTE\_CAM\_UNTERSTÜTZTE

 - ERSTE\_g.

 - LEGEN Sie\_BENACHRICHTIGUNG\_AKTIVIEREN

     - Das System oder Controller muss die folgenden Benachrichtigungen innerhalb dieses Befehls unterstützen:

         - Unterstützte Anbieter Funktionen ändern

         - Ausgehandelte Power Änderung

 - ERSTE\_CONNECTOR\_STATUS

     - Das System oder Controller muss die folgenden Connector Statusänderungen innerhalb dieses Befehls unterstützen:

         - Unterstützte Anbieter Funktionen ändern

         - Ausgehandelte Power Änderung


 - Die System- oder Controller muss folgende Feld in GET unterstützen\_CONNECTOR\_STATUS Status Struktur

     - Grund der Anbieter Funktionen begrenzt


### <a name="systemfundamentalssystemusbxhcibioshandofffollowsspec"></a>System.Fundamentals.SystemUSB.XhciBiosHandoffFollowsSpec

*xHCI BIOS Übergabe folgt-Spezifikation*

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

Für alle xHCI Controller für das Betriebssystem verfügbar gemacht muss die Systemfirmware das BIOS Übergabe Verfahren im Abschnitt 4.2.2.1 der XHCI-Spezifikation definierten folgen.


### <a name="systemfundamentalssystemusbxhcicontrollersmusthaveembeddedinfo"></a>System.Fundamentals.SystemUSB.XHCIControllersMustHaveEmbeddedInfo

*Systeme mit xHCI Controller müssen ACPI-Informationen für das routing von Port eingebettet haben.*

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

Verweisen Sie bitte ACPI-Spezifikation, Version 4.0.

Die Geräte-Hierarchie von Windows-Betriebssystem aufgelistet übereinstimmen ACPI-Namespace-Hierarchie für USB-Geräte genau. 

Alle verbindbaren USB-Ports sind erforderlich, um haben eine \_PLD-Objekt. Darüber hinaus zwei Felder in der \_PLD-Objekt: Gruppe Token (86:79 Bit) und Gruppe Position (Bit 94:87) sollte ordnungsgemäß für alle USB-Verbindungspunkte, einschließlich derer, die nicht extern sichtbar sind definiert werden (dem durch Festlegen angegeben sein sollte 64-bit auf NULL festgelegt).

Keine zwei USB-Verbindungspunkte sollte identische Kombination von Gruppe Token und Gruppe Position verfügen. Wenn zwei Ports einen Verbindungspunkt freigeben, sollten sie identische besitzen \_PLD-Objekten.

Mithilfe dieser Informationen können die Zuordnung der USB-Anschlüsse an Verbindungspunkte eindeutig identifizierbare definieren.  Der USB-Windows 3.x-Stapel wird diese Informationen nutzen, um zu bestimmen, welche Ports an denselben Verbindungspunkten gebunden sind. Einen USB-Anschluss, die keiner \_PLD-Objekt wird angenommen, nicht verbindbaren und nicht sichtbar sein (d. h. er wird nicht verwendet überhaupt).  Die Definition von verbindungsfähigen Port gemäß den Anweisungen in ACPI 4.0-Spezifikation (Abschnitt 9.13:) ist ein Port auf dem entweder ein Benutzer ein Gerät eine Verbindung herstellen kann, ODER es ist ein integriertes Gerät verbunden.

Finden Sie Hinweise zum Entwurf für Weitere Informationen zum Implementieren dieser Anforderung.

*Design Notes:* Beispiel basiert, in diesem Beispiel wird auf xHCI Spec (Version.95) Anhang D. Die Hardwarekonfiguration entspricht genau wie in diesem Anhang. Die Darstellung ACPI diese Hardwarekonfiguration unterscheidet sich in diesem Beispiel wird. Es werden die Unterschiede hervorgehoben.
Es folgt ein Beispiel für die ACPI-Objekte für eine xHCI, die eine schnelle implementiert und SuperSpeed Bus Instanz definiert, die jeweils USB2 und USB3 Protokoll Root Hub-Anschlüsse zugeordnet sind. Die xHCI unterstützt außerdem einen integrierten Hochgeschwindigkeits-Hub um niedrig und Full Speed-Funktionalität zu ermöglichen. Die externe Ports durch die Implementierung xHC definierten bieten einen USB2 Datenbus (d. h. ein D / D-Signal-Paar) oder eine SuperSpeed (oder zukünftigen USB-Geschwindigkeit) Datenbus (d. h. SSRx / SSRx- und SSTx / SSTx-Signal-Paare).
Dabei gilt Folgendes: 

<ul>
<li><p>Die Hauptplatine werden 5 Benutzer sichtbar Connectors C1 - C5 dargestellt:</p>
<ul>
<li><p>Hauptplatine Connectors C1 und C2 unterstützen USB2 (LS/FS/HS) Geräte.</p></li>
<li><p>Hauptplatine Connectors C3, C4 und C5 unterstützen USB3 (LS/FS/HS/SS) Geräte.</p></li>
</ul></li>
<li><p>Die xHCI implementiert eine Speed-Bus-Instanz zugeordnet USB2 Protokoll Root-Hub-Ports, z. B. HCP1 und HCP2 werden Hochgeschwindigkeits nur, d. h. bieten keine Unterstützung für Low-Full Speed.</p></li>
<li><p>Die xHCI stellt 7 externe Ports (P1 - 7):</p>
<ul>
<li><p>Externe Ports 1 (P1) ist HS nur und ist nicht sichtbar oder verbindbaren.</p></li>
<li><p>Externe Ports 2 bis 5 (P2 - P5) unterstützen LS/FS/HS Geräte:</p>
<ul>
<li><p>P2 wird Hauptplatine USB2 Connector C1 angefügt.</p></li>
<li><p>P3 ist Hauptplatine USB2 Connector C2 zugeordnet.</p></li>
<li><p>P4 ist logische USB 2.0-Hub des eingebetteten USB3 Hubs auf der Hauptplatine zugeordnet. Logische USB 2.0-Hub unterstützt die LS/FS/HS Verbindungen für 2 Ports (EP1 - EP2)</p></li>
<li><p>USB 2.0-Verbindungen von Hauptplatine Hub-Ports EP1 und EP2 sind jeweils an Hauptplatine Connectors C3 und C4 angefügt LS/FS/HS Unterstützung für die USB3 Connectors.</p></li>
</ul></li>
<li><p>P5 als Anlage für Hauptplatine Connector C5, vorausgesetzt, der Hauptplatine USB3 Connector C5 LS/FS/HS unterstützen.</p></li>
<li><p>Externe Ports 6 (P6) wird an den logischen SuperSpeed Hub des eingebetteten USB3 Hubs auf der Hauptplatine angefügt. Der logische SuperSpeed Hub unterstützt die SS Verbindungen von 2 Ports (EP1 - EP2).</p></li>
<li><p>Die SuperSpeed Verbindungen von Hauptplatine Hub-Ports EP1 und EP2 sind jeweils an Hauptplatine Connectors C3 und C4 angefügt stellen die SS-Unterstützung für die USB3 Connectors.</p></li>
<li><p>Externe Ports 7 (7) stellen die SS-Unterstützung für den Connector USB3 Hauptplatine Connectors C5, gehört.</p></li>
</ul></li>

<li><p>Die xHCI implementiert 4 interne HS Root-Hub-Ports (HCP1 - HCP4), 2 Hochgeschwindigkeits und 2 SuperSpeed:</p>
<ul>
<li><p>Interner Port 1 (HCP1) direkt externe Port 1 (P1) zugeordnet.</p></li>
<li><p>Interner Port 2 (HCP2) ist ein integrierter Hub HS zugeordnet. Die integrierte Hub unterstützt 4-Ports (IP1 - IP4):</p>
<ul>
<li><p>Ports 1 bis 4 (IP1-IP4) der integrierten Hub Verbinden mit externen Ports 2 auf 5 (P2-P5) jeweils.</p></li>
</ul></li>
<li><p>Interne Ports 3 und 4 (HCP3, HCP4) Anfügen an externen Ports 6 und 7 (P6, 7).</p></li>
</ul></li>
<ul>
<li><p>Alle Verbindungen sind befindet sich auf der Rückseite und die gleiche Gruppe zugewiesen.</p></li>
<li><p>Connectors C1 und C2 USB2 kompatibel sind und deren Farbe nicht angegeben ist. Connectors C3 in C5 USB3 kompatibel sind, und deren Farbe wird angegeben.</p></li>
<li><p>Externe Ports P1 - P5 präsentieren einen USB2 Datenbus (d. h. ein D / D-Signal-Paar). Externe Ports P6 und 7 präsentieren Sie einen SuperSpeed Datenbus (d. h. SSRx / SSRx- und SSTx / SSTx-Signal-Paare).</p></li>
</ul>


```
Scope( \_SB ) {<br />
<br />
                Device( PCI0 ) {<br />
<br />
// Host controller ( xHCI )<br />
Device( USB0 ) {<br />
// PCI device#/Function# for this HC. Encoded as specified in the ACPI<br />
// specification<br />
Name( _ADR, 0xyyyyzzzz )<br />
// Root hub device for this HC #1.<br />
Device( RHUB ) {<br />
Name( _ADR, 0x00000000 ) // must be zero for USB root hub<br />
// Root Hub port 1 ( HCP1 )<br />
Device( HCP1 ) {// USB0.RHUB.HCP1<br />
Name( _ADR, 0x00000001 )<br />
// USB port configuration object. This object returns the system<br />
// specific USB port configuration information for port number 1<br />
Name( _UPC, Package() {<br />
0x01,// Port is connectable but not visible<br />
0xFF,// Connector type (N/A for non-visible ports)<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
} // Device( HCP1 )<br />
// Root Hub port 2 ( HCP2 )<br />
Device( HCP2 ) {// USB0.RHUB.HCP2<br />
Name( _ADR, 0x00000002 )<br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x00,// Connector type - (N/A for non-visible ports)<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// Even an internal connection point should have a _PLD and<br />
// provide a valid Group Token and Position<br />
Name( _PLD, Buffer( 0x10) {<br />
0x00000081,// Revision 1,<br />
// color width height ignored for non-visible connector<br />
0x00000000,// connector type ignored for non-visible connector<br />
0x00808000,// Not User visible, Panel, position shape ignored,<br />
// Group Token = 1, Group Position = 1<br />
// This is the group of all internal connectors.<br />
// Each connector should have a unique position in this<br />
// group<br />
0x00000000} )// Ignored for non-visible connectors <br />
//<br />
// There is no separate node for the integrated hub itself<br />
//<br />
// Integrated hub port 1 ( IP1 )<br />
Device( IP1 ) {// USB0.RHUB.HCP2.IP1<br />
// Address object for the port. Because the port is<br />
// implemented on integrated hub port #1, this value must be 1<br />
Name( _ADR, 0x00000001 )<br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x00,// Connector type - Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x00000081,// Revision 1, Ignore color<br />
// Color (ignored), width and height not<br />
0x00000000,// required as this is a standard USB 'A' type<br />
// connector<br />
0x00800c69,// User visible, Back panel, Center, left,<br />
// shape = vert. rect, Group Token = 0,<br />
// Group Position 1 (i.e. Connector C1)<br />
0x00000003} )// ejectable, requires OPSM eject assistance<br />
} // Device( IP1 )<br />
// Integrated Hub port 2 ( IP2 )<br />
Device( IP2 ) {// USB0.RHUB.HCP2.IP2<br />
// Address object for the port. Because the port is<br />
// implemented on integrated hub port #2, this value must be 2<br />
Name( _ADR, 0x00000002 )<br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x00,// Connector type - Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x00000081,// Revision 1, Ignore color<br />
// Color (ignored), width and height not<br />
0x00000000,// required as this is a standard USB 'A' type<br />
// connector<br />
0x01000c69,// User visible, Back panel, Center, Left,<br />
// Shape = vert. rect, Group Token = 0,<br />
// Group Position 2 (i.e. Connector C2)<br />
0x00000003} )// ejectable, requires OPSM eject assistance<br />
} // Device( IP2 )<br />
// Integrated Hub port 3 ( IP3 )<br />
Device( IP3 ) { // USB0.RHUB.HCP2.IP3<br />
// Address object for the port. Because the port is implemented<br />
// on integrated hub port #3, this value must be 3<br />
Name( _ADR, 0x00000003 )<br />
<strong>// Must match the _UPC declaration for</strong> USB0.RHUB.HCP3 <strong>as</strong><br />
<strong>// this port shares the connection point</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is not connectable<br />
0x00,// Connector type - (N/A for non-visible ports)<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// Even an internal connection point should have a _PLD and<br />
// provide a valid Group Token and Position.<br />
<strong>// Must match the _PLD declaration for</strong> USB0.RHUB.HCP3 <strong>as</strong><br />
<strong>// this port shares the connection point</strong><br />
Name( _PLD, Buffer( 0x10) {<br />
0x00000081,// Revision 1,<br />
// color width height ignored for non-visible connector<br />
0x00000000,// connector type ignored for non-visible connector<br />
0x01008000,// Not User visible, Panel, position shape ignored,<br />
// Group Token = 1, Group Position = 2<br />
// This is the group of all internal connectors.<br />
// Each connector should have a unique position in this<br />
// group<br />
0x00000000} )// Ignored for non-visible connectors <br />
//<br />
// There is no separate node for the embedded hub itself<br />
//<br />
               <br />
// Motherboard Embedded Hub 2.0 Logical Hub port 1 ( EP1 )<br />
Device( EP1 ) {// USB0.RHUB.HCP2.IP3.EP1<br />
Name( _ADR, 0x00000001 )<br />
<strong>// Must match the _UPC declaration for</strong><br />
<strong>//</strong> USB0.RHUB.HCP3.EP1 <strong>as this port provides</strong><br />
<strong>// the LS/FS/HS connection for C3</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB<br />
// 'A' type connector<br />
0x01800c69,// User visible, Back panel, Center,<br />
// Left, shape = vert.<br />
// rect, Group Token = 0,<br />
// Group Position 3<br />
//(i.e. Connector C3)<br />
0x00000003} )// ejectable, requires OPSM eject<br />
// assistance<br />
} // Device(EP1)<br />
// Motherboard Embedded Hub 2.0 Logical Hub port 2 ( EP2 )<br />
Device( EP2 ) {// USB0.RHUB.HCP2.IP3.EP2<br />
Name( _ADR, 0x00000002 )<br />
<strong>// Must match the _UPC declaration for</strong><br />
<strong>//</strong> USB0.RHUB.HCP3.EHUB.EP2 <strong>as this port provides</strong><br />
<strong>// the LS/FS/HS connection for C4</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB<br />
// 'A' type connector<br />
0x02000c69,// User visible, Back panel, Center,<br />
// Left, Shape = vert.<br />
// rect, Group Token = 0,<br />
// Group Position 4 (i.e. Connector C4)<br />
0x00000003} )// ejectable, requires OPSM eject<br />
//assistance<br />
} // Device( EP2 )<br />
} // Device( IP3 )</p>
<p>// Integrated hub port 4 ( IP4 )<br />
Device( IP4 ) { // USB0.RHUB.HCP2.IP4<br />
Name(_ADR, 0x00000004)<br />
<strong>// Must match the _UPC declaration for USB0.RHUB.HCP4 as</strong><br />
<strong>// this port provides the LS/FS/HS connection for C5</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer(0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB 'A' type<br />
// connector<br />
0x02800c69,// User visible, Back panel, Center, Left,<br />
// Shape = vert. rectangle, Group Token = 0,<br />
// Group Position 5 (i.e. Connector C5)<br />
0x00000003} )// ejectable, requires OPSM eject assistance<br />
} // Device( IP4 )<br />
} // Device( HCP2 )</p>
<p>// Root Hub port 3 ( HCP3 )<br />
Device( HCP3 ) {<br />
Name( _ADR, 0x00000003 )<br />
<strong>// Must match the _UPC declaration for</strong> USB0.RHUB.HCP2.IP3 <strong>as</strong><br />
<strong>// this port shares the connection point</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x00,// Connector type - (N/A for non-visible ports)<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// Even an internal connection point should have a _PLD and<br />
// provide a valid Group Token and Position.<br />
<strong>// Must match the _PLD declaration for</strong> USB0.RHUB.HCP2.IP3 <strong>as</strong><br />
<strong>// this port shares the connection point</strong><br />
Name( _PLD, Buffer( 0x10) {<br />
0x00000081,// Revision 1,<br />
// color width height ignored for non-visible connector<br />
0x00000000,// connector type ignored for non-visible connector<br />
0x01008000,// Not User visible, Panel, position shape ignored,<br />
// Group Token = 1, Group Position = 2<br />
// This is the group of all internal connectors.<br />
// Each connector should have a unique position in this<br />
// group<br />
0x00000000} )// Ignored for non-visible connectors <br />
//<br />
// There is no separate node for the embedded hub itself<br />
//                                                                           <br />
// Motherboard Embedded Hub SS Logical Hub port 1 ( EP1 )<br />
Device( EP1 ) {// USB0.RHUB.HCP3.EP1<br />
Name( _ADR, 0x00000001 )<br />
<strong>// Must match the _UPC declaration for</strong><br />
<strong>//</strong> USB0.RHUB.HCP2.IHUB.IP3.EHUB.EP1 <strong>as this port</strong><br />
<strong>// provides the SS connection for C3</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB<br />
// 'A' type connector<br />
0x01800c69,// User visible, Back panel, Center,<br />
// Left, shape = vert.<br />
// rect, Group Token = 0,<br />
// Group Position 3<br />
//(i.e. Connector C3)<br />
0x00000003} )// ejectable, requires OPSM eject<br />
// assistance<br />
} // Device(EP1)<br />
// Motherboard Embedded Hub SS Logical Hub port 2 ( EP2 )<br />
Device( EP2 ) {// USB0.RHUB.HCP2.EP2<br />
Name( _ADR, 0x00000002 )<br />
<strong>// Must match the _UPC declaration for</strong><br />
<strong>//</strong> USB0.RHUB.HCP3.IP3.EP2 <strong>as this port</strong><br />
<strong>// provides the SS connection for C4</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB<br />
// 'A' type connector<br />
0x02000c69,// User visible, Back panel, Center,<br />
// Left, Shape = vert.<br />
// rect, Group Token = 0,<br />
// Group Position 4 (i.e. Connector C4)<br />
0x00000003} )// ejectable, requires OPSM eject<br />
// assistance<br />
} // Device( EP2 )<br />
} // Device( HCP3 )<br />
// Root Hub port 4 ( HCP4 )<br />
Device( HCP4 ) {// USB0.RHUB.HCP4<br />
Name( _ADR, 0x00000004 )<br />
<strong>// Must match the _UPC declaration for</strong> USB0.RHUB.HCP2.IP4 <strong>as</strong><br />
<strong>// this port provides the SS connection for C5</strong><br />
Name( _UPC, Package() {<br />
0xFF,// Port is connectable<br />
0x03,// Connector type - USB 3 Type 'A'<br />
0x00000000,// Reserved 0 - must be zero<br />
0x00000000} )// Reserved 1 - must be zero<br />
// provide physical connector location info<br />
Name( _PLD, Buffer( 0x10) {<br />
0x0072C601,// Revision 1, Color valid<br />
// Color (0072C6h), width and height not<br />
0x00000000,// required as this is a standard USB 'A' type<br />
// connector<br />
0x02800c69,// User visible, Back panel, Center, Left,<br />
// Shape = vert. rect, Group Token = 0,<br />
// Group Position 5 (i.e. Connector C5)<br />
0x00000003} )// ejectable, requires OPSM eject assistance<br />
} // Device( HCP4 )<br />
} // Device( RHUB )<br />
<br />
} // Device( USB0 )<br />
//<br />
// Define other control methods, etc.<br />
<br />
} // Device( PCIO )<br />
<br />
} // Scope( \_SB )
```




### <a name="systemfundamentalssystemusbxhcisupportsminimum31streams"></a>System.Fundamentals.SystemUSB.XhciSupportsMinimum31Streams

*xHCI Controller muss mindestens 31 primären Datenströme pro Endpunkt unterstützen.*

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

Finden Sie in der eXtensible Host Controller Interface-Spezifikation, Abschnitt 4.12.2.

Dies ist für die MaxPSASize in der HCCPARAMS mit mindestens 4 festgelegt werden soll, ultimate Datenübertragungsrate mit UAS-Geräte zu aktivieren.

Basierend auf USB-Attached SCSI-Protokoll (UASP) Speichergeräten nutzt Streams um schnellere Datenübertragungsrate, wie Sie Daten zu erreichen. Um die beste Erfahrung mit diesen Geräten zu aktivieren, müssen alle xHCI Controller mindestens 31 primären Streams unterstützen.


## <a name="systemfundamentalstpm20"></a>System.Fundamentals.TPM20

<!--No content was provided here in the original Word file.-->

### <a name="systemfundamentalstpm20ekcerts"></a>System.Fundamentals.TPM20.EKCerts 

*Systeme mit TPM 2.0 ausgeliefert müssen ein Zertifikat für vollständige Vermerk Schlüssel enthalten.*

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

Alle TPMs müssen ein vollständiger Vermerk Schlüssel (EK) Zertifikat im RAM NV TPM gespeichert, wie beschrieben in der TCG PC Client bestimmte Implementierung Spezifikation für konventionelle BIOS Abschnitt 7.4.5 enthalten: TCG\_VOLLSTÄNDIGE\_CERT, oder vom Gerät während der ersten Boot-Erfahrung abgerufenen Daten aneinander.

| TPM-Artefakten   | NV Index   | Erforderlich                                                                                                                                          |
|----------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| EK Zertifikat | 0x01c00002 | Ja. Dies muss ein Zertifikat mit einem RSA 2048 Bit Schlüssel sein.                                                                              |
| EK nonce       | 0x01c00003 | Optional, ist nur erforderlich, wenn nicht standardmäßigen Werte verwendet werden. **Es wird empfohlen, dieses Feld nicht verwenden. Stattdessen bieten Sie eine angepasste Vorlage bei Bedarf.**  |
| EK-Vorlage    | 0x01c00004 | Optional, ist nur erforderlich, wenn nicht standardmäßigen Werte verwendet werden. Es wird empfohlen, anstelle einer Nonce mit der eindeutigen Feld der Vorlage.                  |
| EK Zertifikat | 0x01c0000a | Optional Wenn dieser Parameter angegeben wurde, muss dies ein Zertifikat mit einem TPM\_ECC\_NIST\_P256-Taste.                                                     |
| EK nonce       | 0x01c0000b | Optional, ist nur erforderlich, wenn nicht standardmäßigen Werte verwendet werden. **Es wird empfohlen, dieses Feld nicht verwenden. Geben Sie eine benutzerdefinierte Vorlage stattdessen bei Bedarf.** |
| EK-Vorlage    | 0x01c0000c | Optional, ist nur erforderlich, wenn nicht standardmäßigen Werte verwendet werden. Es wird empfohlen, anstelle einer Nonce mit der eindeutigen Feld der Vorlage.                  |

Das Zertifikat ECC P256 EK ist die Übermittlung wirksamer erforderlich 28 Juli 2017. AT muss immer mindestens eine, die mit einem Schlüssel RSA 2.048 Bit EK Zertifikat zugeordnet eingeschlossen werden.

Alle Zertifikate EK neben den in 0x01c00002 und 0x01c0000a gespeicherten müssen an NV Indizes beginnend am 0x01c00012 gespeichert werden. Jeder sogar Index kann eine EK Zertifikatspeicher. Der nachfolgende ungerade Speicherort wird die zugeordnete Vorlage speichern, falls erforderlich. Ein Nonce darf nicht in einem separaten NV Index vorhanden sein und stattdessen muss werden in der Vorlage enthaltenen bei Bedarf. Wenn eine benutzerdefinierte Vorlage zum Generieren des zugehörigen EK erforderlich ist, aufgeführt sein ganz im zugeordneten Index so, dass die Vorlage an TPM2 übergeben werden möglicherweise\_CreatePrimary.

**Behandlung von Windows 10 EK Zertifikat nonces**

Wenn eine Nonce in 0x01c00003 vorhanden ist, wird sie an den Anfang des Felds in der Vorlage unique.rsa.buffer kopiert werden. Das Feld wird die Länge des Schlüssels die Modulus entsprechend aufgefüllt werden. Das Feld unique.rsa.size wird entsprechend entsprechend festgelegt werden. Die resultierende Vorlage wird an die TPM2 übergeben\_CreatePrimary Befehl. Beliebige vorhanden Nonce und Vorlage müssen, wenn mithilfe dieses Verfahrens verarbeitet den EK EK Zertifikat für die Nonce und die Vorlage zugeordnet generieren.

Wenn eine Nonce in 0x01c0000b vorhanden ist, wird es in den Anfang des Felds in der Vorlage unique.ecc.x.buffer kopiert werden. Das Feld unique.ecc.x.size wird entsprechend entsprechend festgelegt werden. Die resultierende Vorlage wird an die TPM2 übergeben\_CreatePrimary Befehl. Beliebige vorhanden Nonce und Vorlage müssen, wenn mithilfe dieses Verfahrens generiert den EK EK Zertifikat zugeordnet sind, für die Nonce und die Vorlage generieren.

Das Zertifikat EK muss Daten aneinander des TPM NVRAM so die Löschen des TPM-Aktion nicht durch das Zertifikat EK gelöscht geschrieben wird.

Das Zertifikat muss die EKU angegeben haben, die angibt, dass es tatsächlich ein EK-Zertifikat ist. Der Objektbezeichner für diesen Zweck verwendet wird "2.23.133.8.1".

Das Zertifikat EK kann auch mit ECDSA signiert werden. Die unterstützten ECC gekrümmter für diesen Zweck sind NIST 256, 384 und 521.

Das Zertifikat EK muss AIA-Erweiterung enthalten, die die URL für das Zertifikat der ausstellenden Zertifizierungsstelle in der Zertifikatskette enthält.

AIA-Erweiterung muss auch vorhanden sein, in jeder nicht-Stammzertifikats in der Kette mit URLs, die Einstellung der ausstellenden Zertifizierungsstelle (alle intermediate Zertifikate der Zertifizierungsstelle und das Zertifikat der Stammzertifizierungsstelle) – sichtbar und abrufbar über beim Starten der nur mit einer einzelnen EK Cert iterative abruft. Weitere Informationen zu AIA-Erweiterung finden Sie unter http://go.microsoft.com/fwlink/?LinkId=717890.


### <a name="systemfundamentalstpm20tpm20"></a>System.Fundamentals.TPM20.TPM20

*Anforderungen für alle Systeme, die die Spezifikation TPM 2.0 implementieren*

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

**Obligatorisch:** Alle Systeme müssen ein TPM 2.0 enthalten, und des TPM 2.0 muss im System verfügbar und in der Konfiguration des Protokollversands aktiviert. Die TPM-2.0 und Plattform müssen die Anforderungen in diesem Abschnitt sowie alle anwendbaren Vorschriften außer wie folgt entsprechen

 - Dies ist **Optional** für Server X64. Wenn ein TPM 2.0 auf einer Serverplattform X64 vorhanden ist, muss diese Plattform mit aller Anforderungen in System.Fundamentals.TPM20 und alle untergeordneten Anforderungen entsprechen.

**Obligatorisch:** Ein System, das ein Trusted Platform Module implementiert muss ein TPM enthalten, die entspricht TCG vertrauenswürdige Plattform Modul Library-Spezifikation, Familie "2.0", Stufe 00, Revision-1.16 oder höher empfohlen.

**Obligatorisch:** Systeme mit TPM 2.0 müssen die folgenden Anforderungen erfüllen:


<ol>
<li>
  <p>Die Plattform muss alle "Required" Features in der folgenden Tabelle implementieren.</p>
  <table>
    <thead>
      <tr class="header">
        <th>Integrität-Funktion</th>
        <th>SOC Hardware-Funktionen</th>
        <th>Anforderung</th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>Vertrauenswürdige Ausführung Umgebung</td>
        <td>
          <p>
            <em>
              <strong>Isolierten Speicher</strong>
            </em>
          </p>
          <p>Verfügbarkeit von Speicher zum Speichern von langfristig geheime Schlüssel. Diesen Speicher darf nicht möglich, durch das Betriebssystem ohne Erkennung zu ändern, indem Sie vor dem Betrieb Systemkomponenten sein.</p>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="even">
        <td>Sicherer Speicher</td>
        <td>
          <p>Sichere (isoliert von Common Language Runtime OS) Speicherung von:</p>
          <ul>
            <li>
              <p>Werte (beispielsweise ein Vermerk primären Seed), die vollständige Plattform Power off überstehen sowie Firmwareupdates</p>
            </li>
            <li>
              <p>Werte (beispielsweise eine NV-Indikatoren), die vollständige Plattform Power off überstehen jedoch nicht unbedingt überstehen Firmwareupdates (in diesem Fall, diese Werte auf einen zufällig ausgewählten Wert zurückgesetzt werden müssen)</p>
            </li>
            <li>
              <p>Werte (beispielsweise die Plattform Konfiguration registriert), die Plattform Herunterfahren, der die Entsprechung ACPI S3 überstehen, wenn TPM2_Shutdown (TPM_SU_STATE) aufgerufen wird jedoch möglicherweise auf Weitere Herunterfahren verloren.</p>
            </li>
          </ul>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="odd">
        <td>Plattform Bescheinigung</td>
        <td>
          <blockquote>
            <p>Boot Maßangaben in die Plattform Konfiguration registriert für alle Firmware-Code aufgezeichnet geladen, nachdem die Einrichtung der Core Stamm der Vertrauensstellung für die Messung.</p>
          </blockquote>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="even">
        <td/>
        <td>
          <blockquote>
            <p>Implementierung der PCRs 0 bis 23 für SHA-256, in der gleichen Boot Maßangaben als TPM 1.2 dediziert.</p>
          </blockquote>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="odd">
        <td/>
        <td/>
        <td/>
      </tr>
      <tr class="even">
        <td/>
        <td>
          <blockquote>
            <p>Stabilität Angriffen Seite Channel einschließlich differenzielle Power Analyse (DPA) und elektromagnetische Abstrahlung (langen)</p>
          </blockquote>
        </td>
        <td>
          <strong>Empfohlen</strong>
        </td>
      </tr>
      <tr class="odd">
        <td>Anwesenheit-Schnittstelle</td>
        <td>
          <p>Mobile-SKUs: NoPPIClear muss auf TRUE festgelegt sein.</p>
          <p>Server-SKUs: NoPPIClear muss auf TRUE festgelegt sein.</p>
          <p>IoT SKUs: NoPPIClear muss auf TRUE festgelegt sein.</p>
          <p>Client-SKUs: NoPPIClear muss auf FALSE festgelegt sein.</p>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
    </tbody>
  </table>
</li>
<li>
  <p><strong>Müssen</strong> TPM bieten Unterstützung für Folgendes:</p>
  <table>
    <thead>
      <tr class="header">
        <th>TPM-Funktion</th>
        <th>Beschreibung</th>
        <th>Empfohlen</th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>Befehle</td>
        <td>
          <p><strong>Erforderlich:</strong> der Befehl TPM2_HMAC muss unterstützt werden.</p>
          <p><strong>Optional:</strong> TPM2_EncryptDecrypt unterstützt.</p>
          <p><strong>Erforderlich:</strong> TPM2_PolicyTicket muss unterstützt werden.</p>
          <p><strong>Erforderlich:</strong> TPM2_PolicySigned muss unterstützt werden.</p>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="even">
        <td>Algorithmen</td>
        <td>
          <p><strong>Erforderlich:</strong> Unterstützung für die folgenden Algorithmen: TPM_ALG_RSA TPM_ALG_SHA1 TPM_ALG_AES TPM_ALG_HMAC TPM_ALG_SHA256 TPM_ALG_RSAES TPM_ALG_RSAPSS, TPM_ALG_OAEP.</p>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="odd">
        <td>ECC</td>
        <td>
          <p><strong>Obligatorische</strong>:</p>
          <ul>
            <li>Unterstützung für die Kurve TPM_ECC_NIST_P256 gemäß Tabelle 8 der TPM-Bibliothek Spezifikation Teil 2 für die oben genannten Algorithmen.</li>
          </ul>
          <p><strong>Erforderlich:</strong> die folgenden Befehle sind erforderlich. Einzelheiten zu diesen Befehlen finden Sie im TCG TPM-Bibliothek Spezifikation Teil 3</p>
          <ul>
            <li>
              <p>TPM2_ECDH_KeyGen</p>
            </li>
            <li>
              <p>TPM2_ECDH_ZGen</p>
            </li>
            <li>
              <p>TPM2_ECC_Parameters</p>
            </li>
            <li>
              <p>TPM2_Commit</p>
            </li>
          </ul>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="even">
        <td>PCR Banken</td>
        <td>
          <p><strong>Erforderlich:</strong> mit TPM 2.0 ist aktiviert, SHA-256 PCR Banken werden benötigt, um standardmäßig aktiviert sein.</p>
          <ul>
            <li>
              <p>Das System muss in der Konfiguration des Protokollversands PCR Maßangaben nach Bedarf in diese SHA 256 Banken stellen.</p>
            </li>
            <li>
              <p>Es ist akzeptabel, TPMs mit einer einzelnen ein umschaltbares PCR Bank liefern, die für die SHA-1 und SHA-256 Maße genutzt werden können.</p>
            </li>
          </ul>
        </td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
      <tr class="odd">
        <td>Ereignisprotokolle</td>
        <td><strong>Obligatorische</strong>: Kryptografie Agile Ereignisprotokolle muss unterstützt werden, wie in TCG EFI Protokollspezifikation für TPM-Produktfamilie 2.0 Revision Version 1.0 9 angegeben</td>
        <td>
          <strong>Obligatorisch</strong>
        </td>
      </tr>
    </tbody>
  </table>
</li>
<li>
  <p><strong>Obligatorische</strong>: The TPM hat die folgenden leistungsanforderungen einzuhalten. Diese Anforderungen gelten für den Zeitpunkt, zu dem der Befehl ausgeführt wird an das TPM im Betriebssystem oder UEFI, bis das Ergebnis zurückgegeben wird. Wiederholungen angegeben ist, als den Mittelwert einer finden Sie unter dem Mittelwert von 100 oder mehrere Vorgänge in direkter Folge abgeschlossen. Für Vorgänge auf Schlüssel als importieren möglicherweise die Vorgänge auf abzuschließenden (intern) Schlüssel importiert vorgegeben werden.</p>
  <ol style="list-style-type: lower-alpha">
    <li>
      <p><strong>Zwischenspeichern von</strong>: für TPM\_Vorgänge erstellen, wenn ein TPM 10 des angegebenen erstellen kann Schlüsseltyp innerhalb 1 s jeweils in direkter Folge, starten nach dem ersten Startvorgang vom Endbenutzer 5s, beim möglicherweise anders generiert Schlüsseln in 3 x der vorgesehenen Zeit unten.</p>
    </li>
    <li>
      <p><strong>Geschützte Import</strong>: Importieren geschützt ist definiert als ein Importvorgang auf einen Schlüssel, wo EncryptedDuplication im duplizierte-Objekt festgelegt wurde.</p>
    </li>
  </ol>
  <table>
    <thead>
      <tr class="header">
        <th>Befehl</th>
        <th>Metrik und Beschreibung</th>
        <th>Erforderlich</th>
        <th>Empfohlen</th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>PCR erweitern</td>
        <td><strong>Erforderlich:</strong> TPM auszufüllen Operations (TPM_Extend) innerhalb von 20 ms erweitern.</td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>RSA</td>
        <td>
          <p><strong>Erforderlich:</strong> die Verteilung von RSA 2048 bit Generierung Mal benötigen den Mittelwert einen 25s oder weniger.</p>
          <p><strong>Obligatorische</strong>: RSA 2048 Bit Schlüssel müssen innerhalb von 1000 MS ungeschützte Import abgeschlossen.</p>
          <p><strong>Obligatorische</strong>: Schlüssel momentan geschützte importieren, auf dem sie durch einen RSA-Schlüssel 2048 Bit geschützt wurden, ist innerhalb von 1600ms abgeschlossen importieren geschützt.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>RSA: Signieren</td>
        <td>
          <p><strong>Erforderlich:</strong> TPM muss Vorzeichen (TPM2_SIGN) Vorgänge mit 2048 Bit RSA-Schlüssel innerhalb von 600ms abgeschlossen.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>RSA: Verschlüsselung</td>
        <td>
          <p><strong>Erforderlich:</strong> TPM PKCS15 Verschlüsselungsvorgänge innerhalb von 120ms abgeschlossen ist.</p>
          <p><strong>Erforderlich:</strong> TPM Entschlüsselungsvorgänge PKCS15 innerhalb von 600ms abgeschlossen ist.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>ECC</td>
        <td>
          <p><strong>Obligatorische</strong>: The TPM Anmelde-Vorgänge mit der Kurve P256 ECC (TPM_ECC_NIST_256) innerhalb von 250ms abgeschlossen ist.</p>
          <p><strong>Erforderlich:</strong> TPM_ECC_NIST_256 Schlüssel muss mit einem Mittelwert Zeitabstand von 400ms generierten oder weniger.</p>
          <p><strong>Obligatorische</strong>: ECDH_ZGen müssen innerhalb eines Zeitraums Mittelwert von 250ms oder weniger.</p>
          <p><strong>Obligatorische</strong>: Keys momentan geschützt importieren, in dem die Taste wurde, durch eine ECDH ECC P256 geschützt Bit-Schlüssel auszufüllen geschützte Import innerhalb 450ms.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>HMAC</td>
        <td>
          <p><strong>Obligatorische</strong>: HMAC erstellen Vorgänge innerhalb von 320ms abgeschlossen ist.</p>
          <p><strong>Obligatorische</strong>: HMAC Vorgänge innerhalb von 125ms abgeschlossen ist.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>Symmetrische ver-/entschlüsseln: AES</td>
        <td>
          <p><strong>Obligatorische</strong>: AES erstellen Vorgänge innerhalb von 320ms abgeschlossen ist.</p>
          <p><strong>Obligatorische</strong>: AES ungeschützte Importvorgänge innerhalb von 250ms abgeschlossen ist.</p>
          <p><strong>Obligatorische</strong>: AES ver-/entschlüsseln Vorgänge mit 1 KB an Daten innerhalb von 250ms abgeschlossen ist.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
    </tbody>
  </table>
</li>
<li>
  <p>Die folgenden leistungsanforderungen ersetzen jene Element 3, in denen Konflikte zwischen nach wirksam werden. Die unten aufgeführten leistungsanforderungen stammen an 28 Juli 2018 in Kraft.</p>
  <table>
    <thead>
      <tr class="header">
        <th>Befehl</th>
        <th>Metrik und Beschreibung</th>
        <th>Erforderlich</th>
        <th>Empfohlen</th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>Wichtige Generation</td>
        <td>
          <p><strong>Erforderlich:</strong> einer Zeit Mittelwert 5s RSA 2048 Bit-Schlüssel generiert werden müssen.</p>
          <p><strong>Erforderlich:</strong> ECC P256 (TPM_ECC_NIST_256 und TPM_ECC_BN_256 Varianten) einer maximale Zeit 150ms generiert werden müssen.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>Signieren</td>
        <td>
          <p><strong>Erforderlich:</strong> TPM wird Anmeldung Vorgänge mit 2048 Bit RSA-Schlüssel innerhalb von 250ms abgeschlossen.</p>
          <p><strong>Obligatorische</strong>: The TPM Anmelde-Vorgänge mit der Kurve P256 ECC innerhalb von 150ms abgeschlossen ist.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>Import</td>
        <td>
          <p><strong>Obligatorische</strong>: The TPM muss geschützte Importvorgänge mit 2048 Bit RSA geschützte Schlüsseln innerhalb von 250ms abgeschlossen.</p>
          <p><strong>Obligatorische</strong>: The TPM wird geschützte Importvorgänge mit ECC P256 geschützte Schlüsseln innerhalb von 150ms abgeschlossen.</p>
        </td>
        <td>X</td>
        <td/>
      </tr>
    </tbody>
  </table>
</li>
<li>
  <p>Die folgenden Anforderungen ersetzen jene Elemente 3 und 4, in denen Konflikte zwischen. Die unten aufgeführten leistungsanforderungen stammen an 28 Juli 2019 in Kraft.</p>
  <table>
    <thead>
      <tr class="header">
        <th>Befehl</th>
        <th>Metrik und Beschreibung</th>
        <th>Erforderlich</th>
        <th>Empfohlen</th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>Wichtige Generation</td>
        <td><strong>Obligatorische</strong>: einer Zeit Mittelwert 50 ms ECC P256 Schlüssel generiert werden müssen.</td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>Signieren</td>
        <td><strong>Obligatorische</strong>: The TPM Anmelde-Vorgänge mit der Kurve P256 ECC innerhalb von 100 ms abgeschlossen ist.</td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>Import</td>
        <td><strong>Obligatorische</strong>: The TPM muss geschützte Importvorgänge mit ECC P256 geschützte Schlüsseln innerhalb von 100 ms abgeschlossen.</td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="even">
        <td>Verschlüsselung</td>
        <td><strong>Obligatorische</strong>: AES ver-/entschlüsseln Vorgänge mit 1kB an Daten innerhalb von 50 ms abgeschlossen ist.</td>
        <td>X</td>
        <td/>
      </tr>
      <tr class="odd">
        <td>Algorithmen</td>
        <td><strong>Obligatorische</strong>: AES 256 ist erforderlich.</td>
        <td>X</td>
        <td/>
      </tr>
    </tbody>
  </table>
</li>
<li>
  <p>Eine Plattform, die eine Separate wird nicht unterstützt und über die wichtigsten CPUs isoliert, kryptografische Verarbeitungseinheit muss eine vertrauenswürdige Ausführungsmodus unterstützen. Die vertrauenswürdige Ausführungsmodus benötigen eine höhere Berechtigungsebene als den Ausführungsmodus Normal, die es den Zugriff auf Daten und Code für den Ausführungsmodus Normal nicht verfügbar sind.</p>
</li>
<li>
  <p>Während der Startsequenz wird die Boot-Firmware/Software messen, alle Firmware und alle Softwarekomponenten, die es lädt, nachdem der Kern-Stamm der Vertrauensstellung für die Messung eingerichtet ist. Die Maße werden werden protokolliert als auch auf Plattform Konfiguration Register in Übereinstimmung mit den folgenden Anforderungen erweitert.</p>
</li>
<li>
  <p>So, dass sie zuverlässig und überprüfbar ein Drittanbieter entweder identifizieren Sie alle Komponenten des Startvorgangs Ereignisprotokolle bis zum Zeitpunkt die Boot nach Abschluss des Vorgangs erfolgreich ermöglichen oder wenn Software mit einer Sicherheitslücke ausnutzen (z. B., wenn die dritte Komponente geladen umfasst eine Anfälligkeit ausnutzen, und klicken Sie dann Werte für das erste, zweite, und dritten Komponente im Protokoll vertrauenswürdigen Boot widerspiegeln ordnungsgemäß der Software, die geladen, aber keine Werte nach, die möglicherweise Verlusts) geladen wurde, müssen die Maße implementiert werden. Um dies zu erreichen, muss die vertrauenswürdige Umgebung einen Mechanismus, um die Werte der Register vertrauenswürdigen Boot zum Signieren bereitstellen. Die Schnittstelle der Mechanismus Signatur ("Bescheinigung") hat die Anforderungen in der Microsoft Corporation, definiert einzuhalten "vertrauenswürdige Ausführung Umgebung ACPI Profil 1.0 vom 2. März 2012 behoben.</p>
</li>
<li>
  <p>Das System muss eine vertrauenswürdige Ausführung Umgebung unterstützen der Definition in der Microsoft Corporation, Befehlssatz umfassen "TPM v2. 0 Befehl und Signatur Profil 1.0 vom 2, März 2012.</p>
</li>
<li>
  <p>Das System wird in der Microsoft Corporation, angegebene Schnittstelle unterstützen "vertrauenswürdige Ausführung Umgebung ACPI Profil 1.0 vom 2. März 2012 behoben.</p>
</li>
<li>
  <p>Das System ist erforderlich, um Daten in PCR messen \[7\] gemäß den Angaben in TCG PC Client-Plattform Firmware Profilspezifikation für TPM-Produktfamilie 2.0 Ebene 00 Revision 00.21 27 August 2015 behoben.</p>
</li>
<li>
  <p>Aktualisierungsvorgang UEFI muss auch gegen Rollback auf unsichere Firmware oder nicht in der Produktion Versionen, die sichere Boot deaktivieren oder nicht in der Produktion Schlüssel schützen. Ein physisch Benutzer kann jedoch den Rollback Schutz manuell außer Kraft setzen. In diesem Fall (wo des Schutzes Rollback außer Kraft gesetzt ist) muss das TPM deaktiviert werden.</p>
</li>
<li>
  <p>Plattform-Firmware muss Unveränderlichkeit von der PCRs 0, 2 und 4 über Power Zyklen keine Änderungen an der Plattform statische Core vertrauenswürdige Stammzertifizierungsstelle für Maßeinheiten (SRTM) sicher. Plattform-Firmware muss Unveränderlichkeit von der PCR sicherstellen\[7\] gemäß TCG EFI Protocol-Spezifikation TPM-Produktfamilie 2.0 Revision 1.0 Version 9, über die Power-Zyklen keine Änderungen an der Plattform statische core SRTM. Anfügen einer (nicht startbaren) USB an der Plattform oder Anfügen von der Plattform mit einer Dockingstation darf nicht Änderungen auf den SRTM verursachen.</p>
</li>
<li>
  <p>Ausführung des Befehls TPM 2.0 TPM2\_NV\_Schrittweite muss einen geöffnetes Objekt Steckplatz nicht erforderlich.</p>
</li>
<li>
  <p>Die Plattform muss der vertrauenswürdige Netzwerke Gruppe physische Anwesenheit Schnittstelle Spezifikation Version 1.30 entsprechen.</p>
</li>
<li>
  <p>Die Plattform ist in jeder Zustand, beispielsweise einen Modus Fertigung debug-Modus oder eines anderen Zustands der PCR versetzt\[7\] Objekte gefährdet gebunden, Arbeitsspeicher speichert ermöglicht, ist für die direkte Verwendung zum Debuggen, Fertigung verwenden oder engineering Verwendung von Geräten, die Plattform sich PCR erstreckt\[7\] solchen Status entsprechend.</p>
</li>
<li>
  <p>Die Plattform muss TCG EFI Protokollspezifikation für TPM-Produktfamilie 2.0 Revision 1.0 Version 9 entsprechen.</p>
</li>
</ol>



## <a name="systemfundamentalstrustedplatformmodule"></a>System.Fundamentals.TrustedPlatformModule

*Ein Modul TPM (Trusted Platform) ist ein Mikrochip, bieten grundlegenden Sicherheit verwandte Funktionen.  Anforderungen in diesem Bereich geben die erforderliche TPM-Version und die Kompatibilität mit Windows Bitlocker wieder.*


### <a name="systemfundamentalstrustedplatformmoduletpmcomplieswithtcgtpmmainspecification"></a>System.Fundamentals.TrustedPlatformModule.TPMComplieswithTCGTPMMainSpecification

*Ein System, das ein Modul TPM (Trusted Platform) 1.2 implementiert muss ein TPM enthalten, die TCG TPM Main-Spezifikation, Version 1.2, Revision 103 (oder eine höhere Version), 1, 2 und 3 Teile entspricht.*

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

Ein System, das ein Modul TPM (Trusted Platform) 1.2 implementiert muss ein TPM enthalten, die TCG TPM Main-Spezifikation, Version 1.2, Revision 103 (oder eine höhere Version), 1, 2 und 3 Teile entspricht. 

(<http://www.trustedcomputinggroup.org/resources/tpm_main_specification>) Das TPM muss die folgenden zusätzlichen Anforderungen erfüllen:

 - Den Zeitaufwand für das TPM zum Ausführen aller der Self Tests, die das TPM\_ContinueSelfTest Befehl muss kleiner als 1 Sekunde.

 - Wenn das TPM einen Befehl nach Erhalt des TPM empfängt\_ContinueSelfTest-Befehl, jedoch vor dem Abschluss des TPM\_ContinueSelfTest Selbsttest Aktionen, muss es nicht TPM zurückgeben\_MUSS\_SELBSTTEST.

 - Das TPM monotonen Leistungsindikator muss mindestens zweimal pro eine Plattform Bootzyklus erhöhen konzipiert.

 - Das TPM muss das TPM implementieren\_CAP\_DA\_Funktion der LOGIK für das TPM\_GetCapability Befehl.

 - Standardmäßig die TPM Dictionary-Angriff Logik muss mindestens 9 Autorisierungsfehler in ermöglichen eine einem 24-Stunden-Zeitraum vor die erste Ebene der mehrstufigen eingeben.  Kleine Dauer der Sperrung weniger als fünf Sekunden sind innerhalb von 24 Stunden mit 9 Autorisierungsfehler zulässig, wenn TPM Sperrung Status automatisch bewirkt, dass nach fünf Sekunden verstreichen.  Alternativ muss das System Standardbild nicht standardmäßigen Software Anti-hammering Einstellungen enthalten die TPM-Standardverhalten entsprechen.  (Unter Windows 8 OS können die Einstellungen von ausgeführt gpedit.msc ein, und klicken Sie dann die folgenden in der linken Strukturansicht erweitern angezeigt werden: Richtlinien für Lokaler Computer\\Computerkonfiguration\\Administrative Vorlagen\\System\\TPM-Dienste. So passen Sie die Werte sind: Dauer der Sperrung von Standard Benutzer, Benutzer einzelne Sperrung Standardschwellenwert und Standard Benutzer insgesamt Sperrungsschwellenwert.) 

 - Die Logik TPM Dictionary-Angriff muss nicht mehr als 5000 Autorisierungsfehler pro Jahr zulassen.

 - Plattform Hersteller als der eines Neustarts fast wie möglich, die ein kürzerer TPM zu erreichen Hilfe\_ContinueSelfTest Ausführungszeit besser.

 - Es wird empfohlen, dass die Plattform Hersteller Informationen über das TPM Dictionary-Angriff Logik Verhalten in der Dokumentation des Kunden bereitstellen, die umfasst explizite Schritte zur Wiederherstellung nach TPM in einen gesperrten Zustand wechselt.

 - Es wird empfohlen, der TPM-Status der Lieferung möglich und aktiviert ist.

**Hinweis**: Windows Windows Zertifizierung Tests für das TPM umfangreichere sind weitere TPM-Funktion als in früheren Versionen verwendet. 


### <a name="systemfundamentalstrustedplatformmoduletpmenablesfullusethroughsystemfirmware"></a>System.Fundamentals.TrustedPlatformModule.TPMEnablesFullUseThroughSystemFirmware

*Systeme mit Trusted Platform Module aktivieren Sie das System Firmware Verbesserungen einschließlich TPM in vollem Umfang verwendet.*

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

Ein System, das ein Modul 1.2 TPM (Trusted Platform) implementiert wird, muss bestimmte System Firmware Verbesserungen unterstützen. Der System-Firmware-Code muss eine gemessene Vertrauenskette teilnehmen, die bei jedem ausschalten für die Überprüfung vor dem operating System Boot-Umgebung eingerichtet ist.  System-Firmware-Code muss geschützten Funktionen von der TPM v1. 2 unterstützen und muss die Vertrauenskette SRTM verwalten.
Für ein System, das ein Modul TPM (Trusted Platform) 1.2 implementiert wird, muss die Plattform die folgenden Spezifikationen entsprechen:

 - Die [TCG Plattform zurücksetzen Angriff Risikominderung Spezifikation](http://www.trustedcomputinggroup.org/resources/pc_client_work_group_platform_reset_attack_mitigation_specification_version_10) , Version 1.00 Revision.92 oder höher.  Revision 1.00 starkem wird empfohlen, einschließlich der Implementierung der Ermittlung ein ordnungsgemäßes Herunterfahren des Betriebssystems[(http://www.trustedcomputinggroup.org/resources/pc\_Client\_arbeiten\_Gruppe\_Plattform\_zurücksetzen\_Angriff\_Risikominderung\_Spezifikation\_Version\_10](http://www.trustedcomputinggroup.org/resources/pc_client_work_group_platform_reset_attack_mitigation_specification_version_10)).

 - Der [TCG physische Anwesenheit Interface Specification](http://www.trustedcomputinggroup.org/resources/tcg_physical_presence_interface_specification) Version 1.0 Revision 1.00 oder höher (<http://www.trustedcomputinggroup.org/resources/tcg_physical_presence_interface_specification>).

 - Die [TCG PC Client Arbeit Gruppe PC Client bestimmte TPM Interface Specification](http://www.trustedcomputinggroup.org/resources/pc_client_work_group_pc_client_specific_tpm_interface_specification_tis) (GEKOMMEN) Version 1.20 Version 1.00 oder höher.  Es wird dringend empfohlen, Version 1.21 oder höher implementieren.  Das TPM muss den in der Spezifikation beschrieben zugeordnet Speicherplatz implementieren.  (<http://www.trustedcomputinggroup.org/resources/pc_client_work_group_pc_client_specific_tpm_interface_specification_tis>)

 - Wenn die Plattform UEFI-Firmware implementiert wird, muss er implementieren:

     - Die [TCG EFI Plattform-Spezifikation](http://www.trustedcomputinggroup.org/resources/tcg_efi_platform_specification_version_120_revision_10) , Version 1.20, Revision 1.00 oder höher, [(http://www.trustedcomputinggroup.org/resources/tcg\_Efi\_Plattform\_Spezifikation\_Version\_120\_Revision\_10](http://www.trustedcomputinggroup.org/resources/tcg_efi_platform_specification_version_120_revision_10)).

     - Die [TCG EFI](http://www.trustedcomputinggroup.org/resources/tcg_efi_protocol_version_120_revision_10) Protokollversion 1.20, Revision 1.00 oder höher, <http://www.trustedcomputinggroup.org/resources/tcg_efi_protocol_version_120_revision_10>.

<!-- -->

 - Die Plattform konventionellen BIOS implementiert wird, muss der PC Client Arbeitsgruppe bestimmte Implementierung Spezifikation für konventionelle BIOS, Version 1.20, Revision 1.00 oder höher implementieren. Hinweis: Implementieren der fehlerverzeichnis Version 1.21 wird dringend empfohlen. (<http://www.trustedcomputinggroup.org/resources/pc_client_work_group_specific_implementation_specification_for_conventional_bios_specification_version_12>)

 - Die [Allgemeine TCG ACPI-Spezifikation](http://www.trustedcomputinggroup.org/resources/server_work_group_acpi_general_specification_version_10) Version 1.00, Revision 1.00 (<http://www.trustedcomputinggroup.org/resources/server_work_group_acpi_general_specification_version_10>).

 - Die Windows Vista BitLocker Anforderungen an die Clientplattform, vom 16. Mai 2006 oder höher, verfügbar unter <http://go.microsoft.com/fwlink/?LinkId=70763>.  Ein System möglicherweise anstelle der PCR Maßangaben in Windows Vista BitLocker Client Platform Requirements aufgeführten herkömmlichen BIOS-Systemen die PCR Maße in der TCG PC Client Arbeitsgruppe bestimmte Implementierung Spezifikation für konventionelle BIOS, Version 1.21, Revision 1.00 definierten implementieren.

*Design Notes:* Das TPM enthält eine vertrauenswürdige Stammzertifizierungsstelle Hardware für Plattform Integrität Bewertung und Berichte. Das TPM außerdem Betriebssystem unabhängige Schutz von vertraulichen Informationen und Verschlüsselung Schlüsseln.


### <a name="systemfundamentalstrustedplatformmoduletpmrequirements"></a>System.Fundamentals.TrustedPlatformModule.TPMRequirements

*Implementieren von TPM 1.2 System muss die Anforderungen erfüllen.*

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

Für ein System, das ein Modul TPM (Trusted Platform) 1.2 implementiert wird, muss die Plattform die folgenden Spezifikationen entsprechen:


<ol style="list-style-type: decimal" start="0">
<li><p>Der PC-Client Arbeit Gruppe Plattform zurücksetzen Angriff Risikominderung-Spezifikation, Version 1.0 Version 1.00 Revision 1.00 oder höher, http://www.trustedcomputinggroup.org/resources/pc_client_work_group_platform_reset_attack_mitigation_specification_version_10.</p></li>
<li><p>TCG Anwesenheit Schnittstelle Spezifikation, Version 1.2, Revision 1.00, http://www.trustedcomputinggroup.org/resources/tcg_physical_presence_interface_specification.</p></li>
<li><p>Der TCG PC Client Arbeit Gruppe PC Client bestimmte TPM Schnittstelle Spezifikation (GEKOMMEN) Version 1.21 Revision 1.00 oder höher (http://www.trustedcomputinggroup.org/resources/pc_client_work_group_pc_client_specific_tpm_interface_specification_tis).</p></li>
<li>
<p>Wenn die Plattform UEFI-Firmware implementiert wird, muss sie implementieren.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Die TCG EFI Plattform Spezifikation Version 1.20, Version 1.0 oder höher, http://www.trustedcomputinggroup.org/resources/tcg_efi_platform_specification_version_120_revision_10.</p></li>
<li><p>Die TCG EFI Protocol Version 1.20, Revision 1.00 oder höher, http://www.trustedcomputinggroup.org/resources/tcg_efi_protocol_version_120_revision_10.</p></li>
</ol>
</li>
<li><p>Die Plattform konventionellen BIOS implementiert wird, muss der PC Client Arbeitsgruppe bestimmte Implementierung Spezifikation für konventionelle BIOS, Version 1.20, Revision 1.00 oder höher implementieren. Hinweis: Die Version fehlerverzeichnis 1.21 wird stattdessen dringend empfohlen. (http://www.trustedcomputinggroup.org/resources/pc_client_work_group_specific_implementation_specification_for_conventional_bios_specification_version_12).</p></li>
<li><p>TCG ACPI allgemeine Spezifikationsversion 1.00, Revision 1.00, http://www.trustedcomputinggroup.org/resources/server_work_group_acpi_general_specification_version_10.</p></li>
<li><p>Windows Vista BitLocker Anforderungen an die Clientplattform, vom 16. Mai 2006 oder höher (http://go.microsoft.com/fwlink/p/?LinkId=70763). Ein System möglicherweise anstelle der PCR Maßangaben in Windows Vista BitLocker Client Platform Requirements aufgeführten herkömmlichen BIOS-Systemen die PCR Maße in der TCG PC Client Arbeitsgruppe bestimmte Implementierung Spezifikation für konventionelle BIOS, Version 1.21, Revision 1.00 definierten implementieren.</p></li>
</ol>

    
Und das System die folgenden zusätzlichen Anforderungen erfüllen:


<ol style="list-style-type: decimal">
<li><p>Plattform-Firmware muss Unveränderlichkeit von der PCRs 0, 2 und 4 und auch PCR 7 Wenn gemäß Anhang A der Microsoft Corporation, implementiert sicherstellen &quot;vertrauenswürdige Ausführung Umgebung EFI Protokoll 1.00 behoben 2. März 2012&quot; Dokument über Power Zyklen keine Änderungen in der Plattform statische Stamm des Vertrauens Maße (SRTM). Anfügen einer (nicht startbaren) USB an der Plattform oder Anfügen von der Plattform mit einer Dockingstation darf nicht Änderungen auf den SRTM verursachen.</p></li>
<li><p>Wenn die Plattform einer Serverplattform ist, müssen PCRs 8 bis 15 für OS reserviert werden. (Hinweis: die gleiche-Anforderung gilt für Client-Plattformen.)</p></li>
<li><p>Die Plattform muss den zugeordnete Speicherplatz für die TPM-Schnittstelle implementieren (beispielsweise e/a legacy Port basierend reicht nicht).</p></li>
<li><p>System-Firmware muss physikalische Anwesenheitsschnittstelle Operationen die Plattform neu gestartet wird. Es wird dringend empfohlen, Protokollierungstyp Systemfirmware physische Anwesenheitsschnittstelle Vorgänge auch nach Beenden. (Insbesondere die physische Anwesenheit Schnittstelle Spezifikation Version 1.2, Abschnitt 2.1.4: Get plattformspezifische-Aktion für den Übergang zu grafikbasierten-Umgebung muss den Wert 2 zurückgeben: Neustart.) (Dieser Anforderung kann remote-Administratoren für physische Operationen Anwesenheit ohne physisch vorhanden sein, um die Plattform wieder zu aktivieren.)</p></li>
<li><p>Die Standardkonfiguration für das System benötigen, das gemäß der Spezifikation Schnittstelle physische Anwesenheit TCG NoPPIProvision Flag Abschnitt 2: physikalische Anwesenheit-Schnittstelle auf TRUE festgelegt.</p></li>
<li><p>Die Standardkonfiguration für System Firmware muss das Betriebssystem Anwesenheit Vorgänge 6, 7, 10 und 15 anfordern zulassen. Hinweis: Die Vorgänge werden in Tabelle 2 des der TCG physische Anwesenheit Schnittstelle Spezifikation Version 1.2, Revision 1.00 beschrieben.</p></li>
<li><p>Wenn das System implementiert wird, sollte gemäß TCG physische Anwesenheit Interface Specification diese NoPPIClear-Flag, Abschnitt 2: physikalische Anwesenheit-Schnittstelle. Die Plattform sollte entweder eine festlegen, ändern Sie das Flag oder implementieren Anwesenheit Vorgänge 17 und 18 Firmware Systemkonfiguration darstellen. Hinweis: Die Vorgänge und das Flag NoPPIClear werden in Tabelle 2 des der TCG physische Anwesenheit Schnittstelle Spezifikation Version 1.2 Revision 1.00 beschrieben. (Dieses Flag implementieren hilft automatisierte Tests über die Anwesenheit einer Person-Schnittstelle in den Tests für Windows Zertifizierung vereinfachen und ermöglicht verwaltete Umgebungen vollständig TPM-Verwaltung aus dem Betriebssystem ohne Anwesenheit automatisieren, wenn ein Unternehmen möchte das Flag NoPPIClear festgelegt.)</p></li>
<li><p>System-Firmware muss die _DSM Query-Methode (Funktion Index 0) zusätzlich zu der physischen Anwesenheit Schnittstellenmethoden in der TCG physische Anwesenheit Schnittstellenspezifikation definierten, Abschnitt 2 implementieren: ACPI-Funktionen. (Näheres Advanced Configuration and Power Interface Spezifikation, Revision 5.0 für ein Implementierungsbeispiel der _DSM Query-Methode.)</p></li>
<li><p>System-Firmware muss _DSM Query-Methode (Funktion Index 0) zusätzlich zu der Speicher löschen Interface-Methode in der TCG Plattform zurücksetzen Angriff Risikominderung Spezifikation definierten, Abschnitt 6 implementieren: ACPI _DSM Funktion. (Näheres Advanced Configuration and Power Interface Spezifikation, Revision 5.0 für ein Beispiel für die Implementierung der Query-Methode _DSM.)</p></li>
<li><p>System-Firmware muss die automatische Erkennung von clean Herunterfahren des Betriebssystems implementieren und deaktivieren das Speicher überschreiben Bit gemäß Definition in der TCG Plattform zurücksetzen Angriff Risikominderung-Spezifikation, Abschnitt 2.3: automatische Erkennung der Clean statische RTM Herunterfahren des Betriebssystems. Ausnahme: Wenn das System uneingeschränkt Speicher während des Startvorgangs ohne einer steigenden Startzeit deaktivieren kann, kann das System nicht implementieren die automatische Erkennung (jedoch die vor dem Start und ACPI schnittstellenimplementierungen weiterhin erforderlich sind).</p></li>
<li><p>Wenn das System an Endkunden übermittelt werden, muss das dauerhafte TPM-Flag TPM_PF_NV_LOCKED auf TRUE festgelegt sein. (Dies ist für Systeme. Für Motherboards, die das Flag auf "false" Wenn an der Plattform Hersteller übermittelt festgelegt werden kann, müssen jedoch Anweisungen-Tools Plattform-Hersteller, um das Flag auf TRUE festzulegen, vor der Zustellung an Endkunden mitteilen.)</p></li>
<li><p>Wenn das System an Endkunden übermittelt werden, muss der permanente TPM-Flag TPM_PF_NV_ PHYSICALPRESENCELIFETIMELOCK auf "true" festgelegt werden. (Dieser Anforderung ist für Systeme. Für Motherboards, die das Flag auf "false" Wenn an der Plattform Hersteller übermittelt festgelegt werden kann, müssen jedoch Anweisungen-Tools Plattform-Hersteller, um das Flag auf TRUE festzulegen, vor der Zustellung an Endkunden mitteilen.)</p></li>
<li><p>Das System muss ein vollständiger Vermerk Schlüssel (EK) Zertifikat gespeichert im RAM NV TPM gemäß der TCG PC Client bestimmte Implementierung Spezifikation für konventionelle BIOS Abschnitt 7.4.5 enthalten: TCG_FULL_CERT. Der NV RAM Index für das Speichern des Zertifikats EK muss der vordefinierten und reserviert Index TPM_NV_INDEX_EKCert gemäß den Abschnitt TPM Main-Spezifikation, Teil 2 19.1.2: reserviert Indexwerte. Wie in der TCG PC Client bestimmte Implementierung Spezifikation für konventionelle BIOS empfohlen, Abschnitt 4.2.1: TPM Main Spezifikation reserviert Indizes das D-Bit-Attribut muss für den Index festgelegt werden. (Hinweis: das Zertifikat kann von der TPM-Hersteller oder Plattform erstellt werden.) Ausnahme: Wenn das System die Generierung von einer neuen EK unterstützt es ist nicht erforderlich (aber wird weiterhin dringend empfohlen) ein Zertifikat EK haben.</p></li>
<li><p>System-Firmware muss im Lieferumfang von TPMS standardmäßig aufgelistet. (Dies bedeutet, dass das Objekt für das TPM ACPI standardmäßig in den System ACPI-Tabellen vorhanden sein muss.)</p></li>
<li><p>System-Firmware muss das Löschen des TPM aus in einem setupmenü unterstützen.</p></li>
<li><p>Muss mindestens 256 Bytes TPM NVRAM reserviert (und verfügbar) für OS verwenden.</p></li>
<li>
<p>Firmware muss die TPM_ContinueSelfTest während des Startvorgangs ausgestellt werden, dass der Selbsttest abgeschlossen ist, bevor das Betriebssystem-Ladeprogramm gestartet wird.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Wenn das TPM-Gerät den Selbsttest synchron ausgeführt wird, sollte der Firmware TPM-Treiber den Startvorgang, um fortzufahren, ohne warten auf das Ergebnis des Befehls TPM_ContinueSelfTest erlauben jedoch Geben Sie den Befehl auf dem Gerät optimiert werden. Wenn der Firmware TPM-Treiber einen weiteren Befehl empfängt, sollten sie den folgenden Befehl Verzögerung, bis die TPM_ContinueSelfTest Befehls abgeschlossen ist, anstatt den Befehl TPM_ContinueSelfTest abzubrechen.)</p></li>
<li><p>Empfehlung werden gestartet soll die Self testen, bevor eine Aktion die benötigt mindestens eine Sekunde jedoch verfügt nicht über eine Abhängigkeit für das TPM.</p></li>
</ol>
</li>
<li><p>Die Plattform kann oder können nicht von S3 erteilen, die TPM_ContinueSelfTest beim Fortsetzen (Energiesparmodus).</p></li>
<li><p>Der Speicherort des ACPI-Namespace für das TPM-Objekt muss nur auf dem System Bus ISA oder PCI-Bus-Treiber von Microsoft bereitgestellten hängen ab. Das System Bus verfügt nicht über eine ID, jedoch wird als identifiziert \_SB. ISA-Bus-Gerät IDs möglicherweise PNP0A00 oder PCI\CC_0601. PCI-Bus-Gerät IDs möglicherweise PNP0A03 oder PCI\CC_0604. Darüber hinaus das TPM-Objekt kann auch hängen diese generischen Brücken, Containern oder Module: PNP0A05, PNP0A06 und ACPI0004. Keine anderen Gerät Abhängigkeiten dürfen für den Speicherort der ACPI-Namespace für das TPM-Objekt.</p></li>
<li><p>Optional Die Plattform wird empfohlen, um Maßangaben in PCR [7] als angegebenen in Anhang A der Microsoft Corporation, unterstützen &quot;Trusted_Execution_Environment_EFI_Protocol, 1.00 behoben 2 März 2012&quot; -Spezifikation Aktualisierungsvorgang UEFI muss auch Schutz vor Rollback auf unsichere Firmware-Versionen oder nicht in der Produktion Versionen, die deaktivieren können secure Boot oder nicht in der Produktion Schlüssel enthalten. Ein physisch Benutzer kann jedoch den Rollback Schutz manuell außer Kraft setzen. In diesem Fall (wo des Schutzes Rollback außer Kraft gesetzt ist) muss das TPM deaktiviert werden.</p></li>
</ol>


Hinweis: Bitlocker nutzt PCR7 für eine bessere benutzerumgebung und höhere PCR unzulänglichen. Wenn Secure Boot Starten des Windows-BootMgr Verwendung eines Eintrags DB zulässig, außer Microsoft bereitgestellten EFI erfordert\_CERT\_X509 Signatur mit "CN = Microsoft Windows Produktion PCA 2011" und "Cert Hash(SHA1):: 58 0a 6f 4 c c4 e4 b6 69 b9 Eb dc 1 b 2 b 3e 08 7 b 80 d0 67 8 d, Bitlocker wird dann nicht möglich, PCR7 nutzen. Es wird empfohlen, dass der einzige zulässige DB-Eintrag für Secure Boot sind Microsoft bereitgestellten EFI\_CERT\_X509 Signatur mit "CN = Microsoft Windows Produktion PCA 2011" und "Cert Hash(SHA1):: 58 0a 6f 4 c c4 e4 b6 69 b9 Eb dc 1 b 2 b 3e 08 7 b 80 d0 67 8 d.

"Vertrauenswürdige Ausführung Umgebung EFI Protokoll 1.00 Benutzer 2 März 2012" Spezifikation muss explizit von Microsoft angefordert werden. Um die aktuelle Version zu erhalten, suchen Sie zunächst nach dessen Verfügbarkeit auf der Microsoft Connect-Website. Wenn es nicht verfügbar ist, wenden Sie sich an den http://go.microsoft.com/fwlink/?LinkId=237130.


## <a name="systemfundamentalsusbboot"></a>System.Fundamentals.USBBoot

*Die Features und Anforderungen werden von einem USB-Gerät gestartet wird.*


### <a name="systemfundamentalsusbbootbootfromusb"></a>System.Fundamentals.USBBoot.BootFromUSB

*System-Firmware unterstützt das Starten von alle verfügbar gemachten USB-1.x, 2.x und 3.x-ports*

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

System-BIOS oder UEFI Firmware muss standardmäßig: 

 - Starten über USB unterstützen 1.x auf OHCI Domänencontrollern

 - Starten über USB unterstützen 2.x auf EHCI-Controller

 - Unterstützen Sie Starten über USB 1.x, 2.x und 3.x auf Domänencontrollern XHCI.

 - Unterstützt diese auf alle verfügbar gemachten USB-Anschlüsse bis zu einer Tiefe Hub von 3.

Das System muss auch Boot Windows PE-Abbilder von einem USB 2.0-Gerät unterstützen, mithilfe von erweiterten INT 13 oder UEFI systemeigene Schnittstelle in weniger als 90 Sekunden.

*Design Notes:* Sie sollten OEMs, die Boot-Funktionalität testen, indem Sie ein startbaren USB-Laufwerk mit Windows PE erstellen. Finden Sie im OPK Details. Lieferanten möglicherweise Windows PE (kostenlos) lizenzieren. Informationen, senden Sie eine E-mail an <licwinpe@microsoft.com>.


### <a name="systemfundamentalsusbbootsupportsecurestartupinpreos"></a>System.Fundamentals.USBBoot.SupportSecureStartUpInPreOS

*Unterstützung von Systemen sicheren Start durch System Firmware Unterstützung zum Schreiben in und Lesen aus USB flash-Geräte in der Umgebung vor.*

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

Klicken Sie auf alle UEFI-Systeme und alle Systeme, die ein TPM implementieren, muss das System BitLocker-Wiederherstellung und die strenge Authentifizierungsszenarien unterstützen. Dies geschieht durch Aktivieren der Enumeration und schnellen Lesen / Schreiben von Daten (beispielsweise wichtige Informationen für Sicherung und Wiederherstellung) aus, und ein USB-Massenspeichergerät und UEFI-Firmware wird eine Instanz des Blocks e/a-Protokoll für den Zugriff auf diese USB-Geräte bieten.

*Design Notes:* Finden Sie die USB-Masse-Klasse Bulk-Only Speichertransport und der Spezifikationen UFI-Befehl der USB-Masse Speicher-Klasse, die zum Herunterladen von <http://go.microsoft.com/fwlink/?LinkId=58382>.


## <a name="systemfundamentalsusbdevice"></a>System.Fundamentals.USBDevice

*Diese Anforderungen gelten für USB-Geräte, die in einem System integriert werden.*


### <a name="systemfundamentalsusbdeviceselectivesuspend"></a>System.Fundamentals.USBDevice.SelectiveSuspend

*Alle intern verbundenen USB-Geräte müssen selektive unterstützen standardmäßig anhalten.*

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

Selektive anhalten ist ein wichtiger Power Feature von USB-Geräten zu speichern. Selektive Aussetzung des USB-Geräte ist besonders hilfreich bei tragbaren Computern, da es hilft Ihnen, Strom sparen.

Wenn ein USB-Gerät intern verbunden ist, muss der Gerätetreiber selektive aktivieren standardmäßig anhalten. Alle USB-Gerätetreiber muss das Gerät in selektive platzieren innerhalb von 60 Sekunden ohne Benutzeraktivität anhalten. Dieses Timeout sollten möglichst kurzen werden, während eine gute Benutzeroberfläche zur Verfügung. Die selektive Suspend-Unterstützung überprüft werden kann, durch die Überprüfung des Berichts durch die **Powercfg-Energie** Befehl.

**Hinweise zur Implementierung:** Wenn Geräte selektive eingeben Standby-Modus, sind beschränkt, in einen USB-Zeichnung Spezifikation 2.5mA des aktuellen aus dem USB-Anschluss definiert. Es ist wichtig, um sicherzustellen, dass Geräte aus selektive schnell fortsetzen können aussetzen, wenn sie aktiv sein sollen erforderlich sind.

Beispielsweise beim selektiv angehalten, ein USB-Touchpad muss erkannt Erkennen eines Benutzers Berührung und Signal fortzusetzen, ohne dass des Benutzers eine Taste drücken. Einige Geräte können verlieren die Möglichkeit, eine Aktivierungsereignis beim beschränkt auf die selektive aussetzen aktuelle erkennen, 500 Microamps pro Einheit zu laden, 2.5mA übersteigt. Diese Geräte, wie ein USB-Bluetooth-Modul aktiviert, müssen nicht mehr nur auf den USB-Bus für Power Self versorgt werden. Zeichnen Sie Power aus einer anderen Quelle, erkennt das Gerät Remoteaktivierung Ereignisse

Weitere Informationen zum Aktivieren der selektiven anhalten für HID-Geräte, finden Sie in diesem MSDN-Artikel <http://msdn.microsoft.com/en-us/library/ff538662(VS.85).aspx>

Weitere Informationen zum Implementieren von selektive in einem Treiber anhalten, finden Sie in diesem Whitepaper: <http://www.microsoft.com/whdc/driver/wdf/USB_select-susp.mspx>

 Einen Port angeben, die intern ist (nicht sichtbar für Benutzer) und ein integriertes Gerät, die Eigenschaften ACPI hergestellt werden kann \_UPC. PortIsConnectable Byte muss auf 0xFF festgelegt werden und die \_PLD NICHT. UserVisible Bit muss auf 0 festgelegt werden. Weitere Details stehen auf [MSDN](http://msdn.microsoft.com/en-us/library/ff553550(v=VS.85).aspx).


## <a name="systemfundamentalswatchdogtimer"></a>System.Fundamentals.WatchDogTimer

*Ein Watchdog-Zeitgeber ist ein Gerät, das grundlegende Watchdog für ein Hardwarezeitgeber, die von der Microsoft Hardware Watchdog-Zeitgeber Ressourcentabelle verfügbar gemacht werden unterstützt.*


### <a name="systemfundamentalswatchdogtimerifwatchdogtimerimplemented"></a>System.Fundamentals.WatchDogTimer.IfWatchDogTimerImplemented

*Wenn ein Watch-Zeitgeber Dog implementiert und durch eine WDRT (unterstützt für Versionen vor Windows 8) oder WDAT (erforderlich für Windows 8 und höher) verfügbar gemacht werden, müssen sie Windows-Kompatibilität und Funktionalität Anforderungen erfüllen.*

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

Hardware Watchdog-Zeitgeber überwacht das Betriebssystem und startet den Computer neu, wenn das Betriebssystem ein Fehler auftritt, der Watchdog zurücksetzen. Die Watchdog muss die Anforderungen erfüllen und der Spezifikation in <http://MSDN.microsoft.com/en-us/windows/hardware/gg463320.aspx>einhalten.



## <a name="systemserverassurance"></a>System.Server.Assurance

Dieses Feature zeigt die Anforderungen, die von einem Server zum Abrufen der Hardware Assurance AQ. erfüllt sein müssen


### <a name="systemserverassuranceenhancedplatformintegrityprotection"></a>System.Server.Assurance.EnhancedPlatformIntegrityProtection 

Server unterstützt Hardware und Firmware-basierte erweiterten Schutz der Plattform Integrität.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Dies ist ein *If-implementiert*, optional System-Anforderung für ein System Bereitstellen von erweiterten Sicherheit für Windows Server.  Die Server-Plattform muss unterstützen:


<ul>
    <li>
      <p>UEFI 2.3.1c oder höher gemäß der Definition in der folgenden Anforderungen und getestete durch die entsprechenden Tests;</p>
      <ul>
        <li>
          <p>System.Fundamentals.Firmware.TPR.UEFIEncryptedHDD</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFIBitLocker</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFIBootEntries</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFICompatibility</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFIDefaultBoot</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFILegacyFallback</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.Update</p>
        </li>
      </ul>
    </li>
    <li>
      <p>SecureBoot als in der folgenden Anforderungen definiert und durch die entsprechenden Tests getestet;</p>
      <ul>
        <li>
          <p>System.Fundamentals.Firmware.UEFILegacyFallback</p>
        </li>
        <li>
          <p>System.Fundamentals.Firmware.UEFISecureBoot</p>
        </li>
      </ul>
    </li>
    <li>
      <p>Die Prozessoren im System sind in der Lage, der IOMMU, gemäß Definition in der folgenden Anforderungen oder durch die entsprechenden Tests getestet;</p>
      <ul>
        <li>
          <p>System.Server.Virtualization.ProcessorVirtualizationAssist</p>
        </li>
      </ul>
    </li>
    <li>
      <p>Wenn der Prozessor Microcode-Updates unterstützt muss es signierten Microcode-Updates benötigen, gemäß Definition in der folgenden Anforderung durch die entsprechenden Tests überprüft.</p>
      <ul>
        <li>
          <p>System.Fundamentals.Security.DeviceGuard</p>
        </li>
      </ul>
    </li>
    <li>
      <p>Das System unterstützt TPM 2.0, wie in der folgenden Anforderungen definiert und durch die entsprechenden Tests getestet;</p>
      <ul>
        <li>
          <p>System.Fundamentals.TPM20.EKCerts</p>
        </li>
        <li>
          <p>System.Fundamentals.TPM20.TPM20</p>
        </li>
      </ul>
    </li>
</ul>
<p>Die Plattform ist erforderlich, implementieren Sie Hardware-Test-Schnittstelle und Freigabe Dokumentation und Tools wie im Dokument Hardware Sicherheit testen Interface Specification an folgendem Speicherort <a href="https://msdn.microsoft.com/en-us/library/windows/hardware/dn879006.aspx">https://msdn.microsoft.com/en-us/library/windows/hardware/dn879006.aspx</a>angegeben. Diese Anforderung ist IF IMPLEMENTIERT für Server, jedoch für die Hardware Assurance zusätzliche Qualifikation ERFORDERLICH.</p>
<p>Alle Komponenten in das System, wie Speicher, Netzwerk- oder Grafikkarten oder Kreis, oder anderer Komponenten, die die Standardkonfiguration des Systems sind oder Komponenten, die ein Kunde aus der Anbieter mit dem System bestellen kann müssen Secure Boot unterstützen. Beispielsweise Secure Boot einhalten müssen alle Treiber signiert sein, und die Netzwerkkarte muss PXE-Start unterstützen, wenn das System für Secure Start konfiguriert ist.</p>
<p>Für Systeme und die Sicherstellung AQ vergeben werden müssen das Flag UEFI NoPPIClear standardmäßig auf TRUE festgelegt werden. Darüber hinaus muss das Flag NoPPIProvision standardmäßig auf TRUE festgelegt. Es muss ein Mechanismus in UEFI, bestätigen die Einstellungen dieser Variablen, und ändern. Diese Anforderung ist vorhanden, um insgesamt Remoteverwaltung von TPMs sofort einsetzbar ohne zusätzliche Konfiguration zu ermöglichen.</p>
<p>Für Systeme und die Assurance AQ vergeben werden muss die UEFI-Implementierung mit den Bedürfnissen der Integrität des Codes kompatibel sein. Insbesondere;</p>
<ul>
    <li>
      <p>Datenseiten müssen getrennt von Codepages aufgeführt werden.</p>
    </li>
    <li>
      <p>Code und Datenseiten finden Sie auf der Seite Ebene Granularität für die Ausrichtung.</p>
    </li>
    <li>
      <p>Die gleiche Seite <em>wird nicht</em> enthalten Daten [lesen und schreiben] und ausführbaren Code.</p>
    </li>
    <li>
      <p>Arbeitsspeicher Zuordnungen für welche Seiten Code und die Daten sind Richtigkeit d. h., es ist nicht der Fall, die das gesamte Bild als Daten oder Code markiert ist.</p>
    </li>
</ul>
<p>Dies wird mit den richtigen Buildoptionen für die Erstellung der Binärdateien UEFI erreicht werden. Das System muss die GUID enthalten Firmware festgelegt werden kann, um die Einhaltung dieser Anforderung beanspruchen.</p>

## <a name="systemserverazurestack"></a>System.Server.AzureStack

<!--No content was provided here in the original Word file.-->

### <a name="systemserverazurestackbase"></a>System.Server.AzureStack.Base

*Grundlegende Anforderungen, die von einem beliebigen Server in einer Microsoft Azure-Stapel-Lösung verwendet unterstützt werden sollten.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

In der folgenden Tabelle werden die Anforderungen für einen Server in einer Microsoft Azure-Stapel-Lösung verwendet erfasst.


<table>
<thead>
<tr class="header">
<th>Feature</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td rowspan="8">System.Fundamentals.Firmware</td>
<td>System.Fundamentals.Firmware.FirmwareSupportsUSBDevices</td>
</tr>
<tr class="even">
<td>System.Fundamentals.Firmware.UEFIBitLocker</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.Firmware.UEFIBootEntries</td>
</tr>
<tr class="even">
<td>System.Fundamentals.Firmware.UEFICompatibility</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.Firmware.UEFIDefaultBoot</td>
</tr>
<tr class="even">
<td>System.Fundamentals.Firmware.UEFILegacyFallback</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.Firmware.UEFISecureBoot</td>
</tr>
<tr class="even">
<td>System.Fundamentals.Firmware.Update</td>
</tr>
<tr class="odd">
<td>System.Server.Virtualization</td>
<td>System.Server.Virtualization.ProcessorVirtualizationAssist</td>
</tr>
<tr class="even">
<td rowspan="6">System.Fundamentals.ServerNano</td>
<td>System.Fundamentals.ServerNano.Deployment</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.ServerNano.Diagnostics</td>
</tr>
<tr class="even">
<td>System.Fundamentals.ServerNano.FirmwareUpdate</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.ServerNano.MonitoringAndTelemetry</td>
</tr>
<tr class="even">
<td>System.Fundamentals.ServerNano.OperateInServerNano</td>
</tr>
<tr class="odd">
<td>System.Fundamentals.ServerNano.PatchAndUpdate</td>
</tr>
</tbody>
</table>


Zusätzlich zu den oben genannten muss der Server verfügen:

1.  CPU, durch die eine duale Socket System mit Intel® Xeon® Prozessor E5 v3 Familie oder besser ist

2.  Mindestens 128 GB RAM


## <a name="systemserverazurestacksecurity"></a>System.Server.AzureStack.Security

*Sicherheitsanforderungen für Server in einer Azure-Stapel-Lösung verwendet.*


### <a name="systemserverazurestackassurance"></a>System.Server.AzureStack.Assurance

*Assurance-hardwareanforderungen für Server in einer Azure-Stapel-Lösung verwendet.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

In einer Azure-Stapel-Lösungen verwendeten Server sollte die Anforderungen von der Hardware Assurance AQ. erfüllen.

| Feature | Anforderungen |
|---------|--------------|
|System.Server.Assurance | System.Server.Assurance.EnhancedPlatformIntegrityProtection |


### <a name="systemserverazurestacksecurebootuefioverpxe"></a>System.Server.AzureStack.SecureBootUEFIOverPXE

*PXE-Boot-Anforderungen für die Bereitstellung von Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

In Microsoft Azure-Stapel-Lösungen verwendeten Server sollte erfolgreich über PXE im Modus UEFI mit SecureBoot aktiviert starten können.


## <a name="systemserverazurestackbmc"></a>System.Server.AzureStack.BMC

<!--No content provided in the Word file for this section.-->

### <a name="systemserverazurestackbmcbase"></a>System.Server.AzureStack.BMC.Base

*Baseboard Management Controller-Anforderungen für die Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

In der folgenden Tabelle wird die BMC Feature-Anforderung für eine Lösung Microsoft Azure-Stapel erfasst.

| Feature | Anforderung | Azure-Stapel-Zertifizierung |
|---------|-------------|---------------------------|
| System.Server.BMC | System.Server.BMC.OutOfBandRemoteManageability | Erforderlich |
| System.Server.Manageability.Redfish | System.Server.Manageability.Redfish.Basic | Wenn implementiert |


### <a name="systemserverazurestackbmcbasereliability"></a>System.Server.AzureStack.BMC.Base.Reliability

*Baseboard Management Controller Zuverlässigkeit Requirements for Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Die IPMI-Funktionalität unten wird aus Sicht der Zuverlässigkeit getestet werden soll, da es für eine erfolgreiche Bereitstellung und kontinuierlichen Zugriff auf eine Lösung Azure-Stapel von entscheidender Bedeutung ist. Die folgenden Powershell-Cmdlets wird mit dem Parameter **- ManagementProtocol IPMI** zum IPMI-Funktionen in einer Umgebung Stress verwendet werden. 

 - **Get-PcsvDevice**
 - **Get-PcsvDeviecLog**
 - **Neustart-PcsvDevice**
 - **Set-PcsvDeviceBootConfiguration**
 - **Set-PcsvDeviceNetworkConfiguration**
 - **Set-PcsvDeviceUserPassword**
 - **Start-PcsvDevice**
 - **Stop-PcsvDevice**
 - **Clear-PcsvDeviceLog**



## <a name="systemserverbase"></a>System.Server.Base

*Mindestanforderungen für Server-Systeme*


### <a name="systemserverbase64bit"></a>System.Server.Base.64Bit

*Ein Server-System kann eine systemeigene 64-Bit-Version von Windows Server ausführen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein Server-System muss möglicherweise systemintern unterstützt, und führen eine 64-Bit-Windows Server-Betriebssystem.
Geräte in einem Serversystem benötigen auch 64-Bit-Treiber für 64-Bit-Vorgang zur Verfügung.


### <a name="systemserverbasebmc"></a>System.Server.Base.BMC

*Baseboard Management Controller-Lösung muss die Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Baseboard Management Controller (BMC) Hardware, die die Microsoft verwendet bereitgestellt IPMI-Treiber und Dienstanbieter muss einhalten Intelligent Platform Management Interface (IPMI)-Spezifikation, Version 1.5-Dokument (Version 1.1, 20. Februar 2002, 6/1/04 MARKUP) oder höher.

Der BMC muss auf das System über eine Schnittstelle Tastatur Controller Formatvorlage (KCS) verbunden sein. Der BMC und seine KCS Schnittstelle müssen über ACPI, erkannt werden, wie in Anhang C3 der Spezifikation IPMI 1.5 vorgeschrieben.

Unterstützung für Interrupt ist optional für den BMC. Wenn Interrupt unterstützt wird, die BMC:

 - Dürfen nicht mit anderen Hardwaregeräten freigegeben werden.

 - Der Befehl Globale Flags festlegen müssen unterstützt werden.

Der Treiber BMC muss Plug & Play- und Leistung Management gemäß den Mindestanforderungen Gerät grundlegenden Anforderungen in die Windows-Logo-Programm Anforderungen definiert unterstützen.

Der Treiber muss an die Kernelmodus-Treiber (KMDF) Framework-Komponente von Windows Treiber Framework (WDF) für Microsoft Windows-Familie der Betriebssysteme kompatibel sein. Ein legacy-Treiber aus Gründen der Abwärtskompatibilität muss Windows Driver Model (WDM) kompatibel sein.

Der Treiber muss bereitstellen eine WMI-Schnittstelle, einschließlich der Konfiguration der Timeout über RequestResponseEx() die in der Datei ipmidrv.mof die WMI-Schnittstelle definiert ist.
Der Treiber benötigt Unterstützung für ACPI-Steuerelement:

 - HARDWARE-ID - IPI0001

 - KOMPATIBLE ID - IPI0001 optional

 - \_SRV - IPMI 1.5 oder 2.0

 - \_CRS /\_PRS - Format von Ressourcen: ein einzelnes 2-Byte oder zwei 1-Byte jedes e/a-Port oder da beim Arbeitsspeicher zugeordnete e/a

Der Treiber muss den Windows-ACPI-Treiber zum Abrufen der oben aufgeführten ACPI Daten aufrufen.

Unterstützung für Interrupt ist in der Treiber optional, wenn den IPMI-Treiber unterstützt müssen:
 

 - Nur ein Interrupt zugewiesen

 - Interrupts nicht freigeben

 - Deaktivieren von nicht-Kommunikation Interrupts, die der Treiber nicht vollständig durch den Befehl Globale Flags festgelegt unterstützt zu behandeln.

 - Kommunikation und nicht Kommunikation Interrupts verarbeiten kann sein.

*Design Notes:* Um zu verhindern, Interrupt-Ansturm der Treiber ermöglicht BMC Interrupt beim Starten und deaktiviert die BMC Interrupt unterstützt, wenn mithilfe des Befehls "Festlegen BMC globale ermöglicht" IPMI beendet. Das Feld muss festgelegt ist, das Bit \[0\] -Interrupt Nachrichtenwarteschlange empfangen. Jedoch ist dieses Bit für KCS Kommunikation Interrupt und KCS nicht-Kommunikation freigegeben, damit der Treiber sowohl Interrupts ordnungsgemäß verarbeiten können muss.

Ein KCS Kommunikation Interrupt wird als OBF generierte Interrupt definiert, das auftritt, während der Verarbeitung der BMC Anforderung Nachrichten senden und Empfangen der entsprechenden Antwort. Auftritt auch im Verlauf der Verarbeitung eines GET\_Code STATUS/ABBRUCH des Steuerelements.

Ein KCS nicht Kommunikation Interrupt ist definiert als ein Interrupt OBF generiert, das auftritt, wenn der BMC nicht während der Übertragung von Meldungsdaten oder erste Fehlerstatus ist. Dies ist in der Regel wird eine Unterbrechung, das auftritt, während die Schnittstelle der im LEERLAUF ist\_ZUSTAND\].
 

### <a name="systemserverbasebmcdiscovery"></a>System.Server.Base.BMCDiscovery

*BMC ist sichtbar und aufzählbare.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein System, einen Baseboard Management Controller (BMC) vorhanden ist, müssen sie für das Auffinden und Enumeration von Windows über Plug & Play (Plug & Play-) Methoden für die Geräteschnittstelle verfügbar machen. Wenn der BMC auf das System über kein PnP legacy Link wie die Tastatur Controller-Oberfläche (KCS) verbunden ist, müssen seine Ressourcen über SMBIOS oder ACPI für Discovery und -Enumeration von Windows bereitgestellt werden.


### <a name="systemserverbasecompliance"></a>System.Server.Base.Compliance

*Server-System enthält Komponenten und Treibern, die mit Windows Hardware Zertifizierungsprogramm erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Jeden Bus, Geräte und andere Komponenten in einem System ihre jeweiligen Windows Hardware Zertifizierungsprogramm Anforderungen erfüllen und Treiber verwenden, die entweder sind enthalten mit dem Windows Betriebssystem-Installationsmedien oder, dass Microsoft Digital wurde signiert.


### <a name="systemserverbasedevicepciexpress"></a>System.Server.Base.DevicePCIExpress

*Server-System enthält Speicher- und Lösungen, mit denen PCI-Express-Architektur*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein Serversystem muss PCI Express-Konnektivität für alle Speicher- und Geräte, die auf dem System installierte verwenden.

Die Geräte können entweder Adaptern in PCI Express-Steckplätze oder Chip unten werden direkt mit der Hauptplatine verbunden ist. Dies gilt nicht für integrierte Geräte, die Teil der Chipsatz sind.


### <a name="systemserverbaseecc"></a>System.Server.Base.ECC

*Systemspeichers verwendet ECC oder andere Technologie, um zu verhindern, dass Einzel-Bit-Fehler verursacht Systemfehler.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server-Systeme müssen unterstützen Fehlerkorrektur-Code, Arbeitsspeicher Spiegelung oder einer anderen Technologie, die zu erkennen und korrigieren Sie mindestens ein Einzel-Bit-Speicherfehler kann. Der Systemspeicher und der Cache geschützt werden müssen mit ECC) oder anderen Speicherschutz. Alle ECC oder anderweitig geschützt RAM, sichtbar für das Betriebssystem muss zwischengespeichert werden. Die Lösung muss mindestens einen Double-Bit-Fehler in ein Wort zu erkennen und in ein Einzel-Bit-Fehler in einem Wort, korrigieren gibt an, in dem die Breite in Bits des Teilsystems Arbeitsspeicher "Word". Ein ermittelte Fehler, der nicht behoben werden kann, muss in einem Systemfehler führen.


### <a name="systemserverbasehotplugecn"></a>System.Server.Base.HotPlugECN

*Serversystem, das systemeigene Hot-Plug-Funktionalität unterstützt erfüllt Anforderungen Hot-Plug ECN Nr. 31 definiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein Server-System muss Anforderungen definiert im Feld PCI-Hot-Plug-ECN. erfüllen. 31 Wenn hot-Plug-PCI Express-Geräten oder Adapter unterstützt. beispielsweise als eine Verhaltensweise von einer dynamisch Hardware-partitionierbarer entwerfen oder in Form von Express Modul oder eine vergleichbare hot-Plug-PCI Express e/a-option entwerfen.


### <a name="systemserverbasenopata"></a>System.Server.Base.NoPATA

*Persistent Speichergeräten auf Servern, die als Festplattenlaufwerke klassifiziert darf kein PATA sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Persistent Speichergeräten klassifiziert als Festplatten, entweder eine feste oder Wechseldatenträger müssen nicht durch einen der folgenden gesteuert werden: Parallel Advanced Technology Attachment (auch bekannt als Parallel ATA-GERÄTS, PATA, IDE, e-IDE oder ATAPI) Domänencontroller, auf RAID-Versionen dieser Geräte enthalten. PATA Controller jeglicher Art können nur auf CD, DVD oder andere nicht als Festplattenlaufwerke klassifiziert Speichergeräten verbunden werden.

Parallel Advanced Technology Attachment (auch bekannt als Parallel ATA-GERÄTS, PATA, IDE, e-IDE oder ATAPI) Domänencontroller, auf RAID-Versionen dieser Geräte umfassen die Möglichkeit zum Betrieb eine Festplatte aus dem System entfernt sollte ein Festplattenlaufwerk fehlschlagen und müssen ausgetauscht werden nicht unterstützt. Dies erzwingt, dass das System für einen längeren Zeitraum nicht verfügbar ist.

Parallel Advanced Technology Attachment (auch bekannt als Parallel ATA-GERÄTS, PATA, IDE, e-IDE oder ATAPI) Domänencontroller, auf RAID-Versionen dieser Geräte enthalten die Möglichkeit zum Betrieb eine Festplatte aus dem System entfernt sollte ein Festplattenlaufwerk fehlschlagen und müssen ausgetauscht werden nicht unterstützt. Dies erzwingt, dass das System für einen längeren Zeitraum nicht verfügbar ist.
 

### <a name="systemserverbaseosinstall"></a>System.Server.Base.OSInstall

*Server-System enthält eine Methode zum Installieren des Betriebssystems für den Notfall Wiederherstellung oder Reparatur.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Das Serversystem muss eine Methode zum Installieren des Betriebssystems für den Notfall Reparatur-Unterstützung bieten. Es folgen Beispiele für mögliche Lösungen:

 - PXE-Unterstützung

 -  Intern oder extern angefügte, startbaren, wieder DVD.


### <a name="systemserverbasepciaer"></a>System.Server.Base.PCIAER

*Windows Server-Systeme können Microsoft Application (erweiterte Fehlerberichterstattung) implementieren, wie von der Plattform bereitgestellt und in PCI Express Base Spezifikation, Version 2.1 ACPI Spezifikation 3.0 b angegeben wird*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

System-Serverhersteller welche um das erweiterte Error Reporting (Microsoft Application) Bit (0 x 3) in der PCI- \_OSC-Tabelle in

das System-BIOS müssen Folgendes implementieren:

 - Die \_HID-Wert auf dem Stamm Bus des Systems muss PNP0A08, sodass das Betriebssystem finden kann, die Geräte sind, PCI Express und unterstützen von Microsoft Application.

 - PCI AER mit Windows verwenden, muss das System möglicherweise Berichten \_OSC-Steuerelement in das Gerät und die \_in ACPI SB/PC10-Objekten. Die folgenden Bits müssen aktiviert sein:

   - 0 x 0 – PCI Express Native Hot Plug
   - 0 x 1 - hot-Plug-Steuerelement
   - 0 x 3 - erweiterte Fehlerberichterstattung (Microsoft Application)
   - 0 x 4 – PCI Express Zuverlässigkeit Struktur-Steuerelement<br/><br/>

 - MCFG ACPI-Tabelle in PCI-Firmware-Spezifikation, Version 3.0, b, damit das Betriebssystem Microsoft Application Funktion Register in der erweiterten Konfiguration Speicherplatz PCIe zugreifen können.

Hinweise zum Entwurf:

Dies ist eine Anforderung implementiert für Server System-Anbieter. Besteht keine Notwendigkeit Windows Server 8 zum Bereitstellen von Microsoft Application\_OSC auf Steuerung übergeben möchten, um das Betriebssystem und die Systeme Implementieren einer "Firmware ersten" Fehler Richtlinie.


### <a name="systemserverbaseremotemanagement"></a>System.Server.Base.RemoteManagement

*Server-System unterstützt remote, headless, nicht genügend Band Management-Funktionen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server-Systeme müssen bieten die Möglichkeit verwaltet werden, ohne das Betriebssystem vorhanden sind, oder wenn das Betriebssystem nicht vollständig funktionsfähig ist.
Das System muss die folgenden Remote, headless, nicht genügend Band Management-Funktionen bieten:

 - Schalten Sie die server
 - Schaltet den server
 - Zurücksetzen des Servers
 - Bereitstellen von Zugriff auf Windows Server Emergency Management Services auf dem server
 - Zeigen Sie auf dem Server System-Abbruchfehler

Im folgenden sind nicht erforderlich, wenn das System ist ein Sockel/Standalone-System mit 8GB oder weniger Max, den RAM, auf dem Logo wurde für Windows Server 2003 vor dem 31. Dezember 2007 würde:

 - Ändern Sie die BIOS-Einstellung des Servers
 - Wählen Sie welches Betriebssystem auf dem Server zu starten.

Die oben genannten Funktionen können mit einer beliebigen Kombination der folgenden Methoden bereitgestellt werden:

 - Seriellen Anschluss konsolenumleitung
 - Service-Prozessor
 - BIOS-Umleitung
 - BMC
 - Verwaltung von Geräten

Diese Anforderung behandelt die minimalen Funktionen für die serverunterstützung von headless-erforderlich.
Hinweise zum Entwurf:

Umleitung der Konsole kann mit einer Setup-Befehlszeilenoption erzwungen werden,
```
[/emsport:{com1|com2|usebiossettings|off}
/emsbaudrate:*baudrate*]
```
Zur Abstimmung Setup, SPCR und EFI- oder BIOS-umleitungseinstellungen können pro die Informationen finden Sie unter <http://msdn2.microsoft.com/en-us/library/ms791506.aspx>konfiguriert werden.

Finden Sie die Microsoft Headless-Server und Emergency Services Entwurfsspezifikationen und den IPMI-Spezifikation unter [http://go.microsoft.com/fwlink/?linkid=36699](http://www.microsoft.com/whdc/system/platform/server/default.mspx).

Finden Sie Prozessor-Konsole Umleitung Dienstdetails unter [http://go.microsoft.com/fwlink/?LinkId=58372](http://technet2.microsoft.com/WindowsServer/en/Library/04aa0d33-f24a-4f63-8977-bfab15706c8a1033.mspx). 


### <a name="systemserverbaseresourcerebalance"></a>System.Server.Base.ResourceRebalance

*Server-Gerätetreibern müssen Ressource neu auszugleichen Anforderungen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein System breit Ressource Rebalance kann unter Windows Server ausgeführt werden. Einen Fall, in dem in diesem Fall, ist, wenn ein Gerät an einen Server dynamisch hinzugefügt wird. Gerätetreiber müssen berücksichtigt werden, der Ressource Rebalance Ablauf und die Plug & Play-Anforderungen, die als Teil des Datenflusses verteilt werden. Gerätetreiber müssen alle e/a-Anforderungen während des Vorgangs der Ressource Rebalance Warteschlange.


### <a name="systemserverbaseserverrequiredcomponents"></a>System.Server.Base.ServerRequiredComponents

*Server-System muss erforderlichen Geräte und Funktionen enthalten.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server-Systeme müssen die folgenden Geräte oder Funktionen enthalten.


<table>
<thead>
<tr class="header">
<th>Gerät oder Funktionen</th>
<th>Anforderung</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>E/a-Bus und Geräte</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>System.Fundamentals.SystemPCIController.PCIRequirements</td>
<td>Verschiedene PCI-Spezifikation reqts</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>System.Server.Base.HotPlugECN</td>
<td>Hot-Plug-ECN #31</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Arbeitsspeicher</td>
<td>2008 – 1 TB, 2008 R2 - 2TB, 2012-4 TB, Server weiter - 4TB (abhängig von der Korrektur am RTM)</td>
<td>Höchstzahl an unterstützten Speicher</td>
</tr>
<tr class="even">
<td></td>
<td>512 MB</td>
<td>Unterstützte Mindestarbeitsspeicher</td>
</tr>
<tr class="odd">
<td></td>
<td>System.Server.Base.ECC</td>
<td>ECC</td>
</tr>
<tr class="even">
<td>Prozessor</td>
<td>System.Server.Virtualization.ProcessorVirtualizationAssist</td>
<td>Unterstützung für Hyper-V</td>
</tr>
<tr class="odd">
<td></td>
<td>1.4 GHz und 64-Bit-Version</td>
<td>Minimal unterstützte prozessorgeschwindigkeit</td>
</tr>
<tr class="even">
<td></td>
<td>2008 – 64, 2008 R2 - 256, 2012-640, zum nächsten Server - 640 logischen Prozessoren (Dies ist noch an RTM)</td>
<td>Anzahl der maximal unterstützten Prozessor</td>
</tr>
<tr class="odd">
<td>Storage</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>System.Server.Base.NoPATA</td>
<td>E-IDE,-IDE ATAPI, Parallel ATA-GERÄTS nicht zulässig</td>
</tr>
<tr class="odd">
<td></td>
<td>System.Fundamentals.Firmware.Boot.SystemWithBootDeviceGreaterThan</td>
<td>No 2.2 TB Boot HD-Unterstützung für BIOS-basierte Systeme</td>
</tr>
<tr class="even">
<td>Netzwerk</td>
<td>Device.Network.LAN.Base</td>
<td>1GigE). und mindestens-Server Anforderung</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Wiederherstellung</td>
<td>System.Server.Base.OSInstall</td>
<td>Beispiel: DVD, PXE</td>
</tr>
<tr class="even">
<td>Debuggen</td>
<td>System.Fundamentals.DebugPort.SystemExposesDebugInterface</td>
<td>Beispiel: COM, USB, 1394</td>
</tr>
<tr class="odd">
<td>Remote &amp; OOB-Mngmt</td>
<td>System.Server.Base.RemoteManagement</td>
<td>Beispiel: BMC Service-Prozessor-Adapter</td>
</tr>
<tr class="even">
<td>Hohe Precision-Zeitgeber</td>
<td>System.Fundamentals.HAL.HPETRequired</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>SMBIOS</td>
<td>System.Fundamentals.SMBIOS.SMBIOSSpecification</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>System.Server.SMBIOS.SMBIOS</td>
<td></td>
</tr>
<tr class="even">
<td>Video</td>
<td>System.Server.Graphics.WDDM</td>
<td>Treiber bereitgestellten MS verwenden, oder geben Sie entweder Anzeige nur oder vollständige WDDM-Treiber</td>
</tr>
<tr class="odd">
<td></td>
<td>System.Fundamentals.Graphics.MicrosoftBasicDisplayDriver</td>
<td>Video Minimalwerte, 1024 x 768 x 32 Bit pro Pixel, VESA Timing und compliance</td>
</tr>
<tr class="even">
<td>RemoteFX</td>
<td>System.Fundamentals.Firmware.SystemCanBootWithEitherGraphicsAdapter</td>
<td>BIOS-Unterstützung für mehrere Adapter</td>
</tr>
<tr class="odd">
<td></td>
<td>System.Fundamentals.Graphics.MultipleOperatingMode</td>
<td>Funktionalität von mehreren GPUs Anforderung</td>
</tr>
<tr class="even">
<td>Markerdatei</td>
<td>System.Fundamentals.MarkerFile.SystemIncludesMarkerFile</td>
<td>Datei für OCA Markierung</td>
</tr>
<tr class="odd">
<td>Einzelnen container</td>
<td>System.Client.PCContainer.PCAppearsAsSingleObject</td>
<td>Computer wird als einzelnen Objekts in Geräte und Drucker Ordner angezeigt.</td>
</tr>
</tbody>
</table>


Die folgenden Geräte oder Funktionen sind nicht erforderlich für Server-Systeme:

<ol style="list-style-type: decimal">
<li><p>Bus-Controller &amp; Ports:</p>
<ol style="list-style-type: lower-alpha">
<li><p>HD-Audio</p></li>
<li><p>CardBus &amp; PCMCIA</p></li>
<li><p>IEEE 1394</p></li>
<li><p>Secure Digital</p></li>
</ol></li>
<li><p>Konnektivität:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Bluetooth</p></li>
<li><p>CardBus &amp; PCMCIA</p></li>
<li><p>ExpressCard</p></li>
<li><p>IEEE 1394</p></li>
<li><p>Infrarot</p></li>
<li><p>Parallel [Sysfund-0221] &amp; seriellen</p></li>
<li><p>Drahtlose USB</p></li>
</ol></li>
<li><p>Netzwerk:</p>
<ol style="list-style-type: lower-alpha">
<li><p>ISDN</p></li>
<li><p>TCP Chimney NIC</p></li>
</ol></li>
<li><p>Anzeigen:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Zusätzliche</p></li>
</ol></li>
<li><p>Eingabe:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Smartcard-Leser</p></li>
</ol></li>
<li><p>Streaming Media &amp; übertragen:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Empfänger senden</p></li>
<li><p>Decoder</p></li>
<li><p>Encoder</p></li>
<li><p>Videoaufnahme</p></li>
</ol></li>
<li><p>TPM:</p>
<ol style="list-style-type: lower-alpha">
<li><p>TPM. Wenn implementiert, müssen Anforderungen erfüllen.</p></li>
<li><p>USB-Schreibberechtigung für BitLocker-Wiederherstellung</p></li>
</ol></li>
<li><p>Watchdog-Zeitgeber (WDT)</p></li>
<li><p>Baseboard Management Controller (BMC)</p></li>
<li><p>Erweiterte Power Management zusätzliche Qualifikation</p></li>
<li><p>Dynamische Partitionierung zusätzliche Qualifikation</p></li>
<li><p>Fehlertoleranz Toleranz zusätzliche Qualifikation</p></li>
<li><p>Hohe Verfügbarkeit zusätzliche Qualifikation</p></li>
<li><p>Power-Verwaltung über S3, besagt S4 und S5 System support</p></li>
</ol>


### <a name="systemserverbasesystempciexpress"></a>System.Server.Base.SystemPCIExpress

*Server-System unterstützt systemintern PCI Express*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server-Systemen ist erforderlich, wenn einen PCI Express-Stamm komplexer als eine Verbindung von e/a-System für die CPU und Arbeitsspeicher die Anforderungen in der PCI-Express definierten 1. 0a (oder 1.1) entsprechen muss Base-Spezifikation und PCI-lokalen Bus-Spezifikation, Version 2.3 oder höher. Wenn Diskrepanzen vorhanden ist, hat der PCI-Express Base Spezifikation Vorrang.


## <a name="systemserverbmc"></a>System.Server.BMC

<!--No content was provided here in the original Word file.-->

### <a name="systemserverbmcoutofbandremotemanageability"></a>System.Server.BMC.OutOfBandRemoteManageability

*Server unterstützt Out-of-Band-remote Management-Funktionen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Serverhardware unterstützt Out-of-Band-remote Management-Funktionen, die mit IPMI 2.0 über ein LAN und/oder seriellen Schnittstellen sowie in-Band-Verwaltung über die Schnittstelle System KCS über den IPMI-Treiber.

Es ist nicht erforderlich, dass der Server die vollständige IPMI 2.0-Spezifikation unterstützt, da nur eine Teilmenge der Funktionalität für Out-of-Band-Remoteverwaltung erforderlich ist.

Erzwingung

Dies ist eine optionale System "If-implementierte" Anforderung für einen Server zu Remote außerhalb des Bereichs mit den IPMI Industriestandard verwaltbar sein. Diese Anforderung wird also tatsächlich bei der Freigabe von Windows Server 2016.

Unternehmensvorgabe

Out-of-Band-remote-Verwaltung über den IPMI 2.0 ermöglichen Modelle Server-Systeme, Windows Server 2016 für eine effiziente Funktionsweise in einem Datacenter Software definiert ausgeführt und daher Senkung der Betriebskosten für den Kunden und anderen macht, in der heterogenen Hardware-Plattformen bereitgestellt werden. Um dieses Ziel zu erreichen, müssen Systeme diese Funktionalität Remote verfügbar machen. Ein Server mit einer dedizierten NIC BMC kann dadurch über den IPMI über LAN verfügbar. Ein Server BMC, das nur die IPMI-Funktionalität über eine Serial-Schnittstelle verfügbar macht müssen Teil von einem Chassis oder einer Anlage, die folgenden Verwaltungsvorgänge für einen remote-Operator im Netzwerk (beispielsweise über eine Chassis-Manager) übersetzen kann sein.


## <a name="systemserverdynamicpartitioning"></a>System.Server.DynamicPartitioning

*Dieses Feature definiert dynamische Partitionierung Anforderungen von Server-Systemen. Dieses Feature ist nicht von allen Serversystemen erforderlich.*


### <a name="systemserverdynamicpartitioningapplication"></a>System.Server.DynamicPartitioning.Application

*Server, die Partitionierung der Hardware unterstützen müssen als Windows-Anwendung, die auf einem Windows-Betriebssystem ausgeführt Partition-Verwaltungssoftware bereitstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server, dass Support Partitionierung der Hardware Partition Managersoftware bereitstellen muss die der Benutzer Schnittstelle Administratoren bereitstellt werden so konfigurieren Sie Hardware-Partitionen verwenden. Diese Software muss als Windows-Anwendung, die auf einem Windows-Betriebssystem ausgeführt angeboten werden.


### <a name="systemserverdynamicpartitioningapplicationinterface"></a>System.Server.DynamicPartitioning.ApplicationInterface

*Server, die Partitionierung der Hardware unterstützen müssen Partition-Verwaltungssoftware angeben, das eine Benutzeroberfläche und eine Skriptfunktionen für Partition Management bereitstellt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server, die Partitionierung der Hardware unterstützen müssen Verwaltungssoftware Partition angeben, die auch eine grafische Benutzeroberfläche zur Verwaltung der manuellen Anwendungsverzeichnispartition und eine Skriptfunktionen für die Verwaltung von Remote- oder automatisierte Partition.
 

### <a name="systemserverdynamicpartitioningconfigurationpersist"></a>System.Server.DynamicPartitioning.ConfigurationPersist

*Server, die Partitionierung der Hardware unterstützen müssen über einen Neustart und Power-Zyklus Persistenz der Partition Hardwarekonfiguration unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Die Hardware-Partition-Konfiguration auf einem Server, auf dem Ruhezustand unterstützt Partitionierung der Hardware einem Neustart beibehalten werden muss, fortsetzen und Ausschalten der Partition oder dem Server. Diese Anforderung wird vorausgesetzt, dass keine Änderung Partition initiiert wurde, während die Partition verfügbar war.


### <a name="systemserverdynamicpartitioningcore"></a>System.Server.DynamicPartitioning.Core

*Systeme, die dynamische Hardwarepartitionierung unterstützen müssen die Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Systeme müssen die unten aufgeführten Anforderungen entsprechen und übergeben den Test mit dynamischen Partitionierung der Hardware im Windows Hardware Lab Kit, um in Windows Server-Katalog als unterstützende dynamische Partitionierung aufgeführt werden:

 - System.Server.DynamicPartitioning.Application

 - System.Server.DynamicPartitioning.ApplicationInterface

 - System.Server.DynamicPartitioning.ConfigurationPersist

 - System.Server.DynamicPartitioning.ErrorEffect

 - System.Server.DynamicPartitioning.Firmware

 - System.Server.DynamicPartitioning.HotAddLocal

 - System.Server.DynamicPartitioning.HotAddReplace

 - System.Server.DynamicPartitioning.HotAddVisual

 - System.Server.DynamicPartitioning.HotReplacePU

 - System.Server.DynamicPartitioning.PartialHotAdd

 - System.Server.DynamicPartitioning.SoftwareStatus

 - System.Server.DynamicPartitioning.Subsystem 


### <a name="systemserverdynamicpartitioningerroreffect"></a>System.Server.DynamicPartitioning.ErrorEffect

*Fehler in eine Partition Hardwaregerät auf Servern, die Hardware Partitionierung Ursache unterstützen keine Betriebssystem auffindbaren Effekte auf anderen Partitionen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Softwarefehler, die innerhalb der Grenzen einer Hardware-Partition auf einem Server auftreten, die unterstützt Partitionierung der Hardware oder Hardware (einschließlich Firmware) müssen keinen Einfluss auf die Betriebssystem in anderen Hardware-Partitionen.


### <a name="systemserverdynamicpartitioningfirmware"></a>System.Server.DynamicPartitioning.Firmware

*Server, die Partitionierung der Hardware unterstützen müssen serverbeschreibung und Partitionierung Abläufe in der Firmware entsprechen, die mit der dynamischen Hardware Partitionierung Anforderungsspezifikation angeben.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

System-Firmware auf einem Server, der Partitionierung der Hardware unterstützt, bietet die ACPI serverbeschreibung Handshake während der Partitionierung Ereignisse und Initialisierung von Hardware zuzuordnen, die in eine Partition hinzugefügt werden soll und muss unter Einhaltung der Hot ersetzen Flow sowie Anforderungen und Hot Flow hinzufügen und Anforderungen Spezifikationen bereitgestellt werden.

Für den Zugriff auf diese Spezifikationen, senden Sie E-mail an <DPFB@Microsoft.com>.


### <a name="systemserverdynamicpartitioninghotaddlocal"></a>System.Server.DynamicPartitioning.HotAddLocal

*Hardware-Komponenten auf einem Server, den eine Partition unterstützt, Hardware, die Partitionierung in eine Einheit, die hot wird, hinzugefügt können nicht aus anderen Partitionen Hardware zugegriffen werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Prozessoren, Arbeitsspeicher und e/a-Komponenten in eine beliebige Einheit hot hinzugefügt, um eine vorhandene Hardware-Partition auf einem Server, der Partitionierung der Hardware unterstützt, müssen nicht direkt von Software in einer anderen Hardware Partition mit zugegriffen werden.


### <a name="systemserverdynamicpartitioninghotaddreplace"></a>System.Server.DynamicPartitioning.HotAddReplace

*Server, dass hot hinzufügen Prozessoren, Arbeitsspeicher und e/a unterstützt und hot muss Support Partitionierung der Hardware ersetzen Subsysteme Prozessor und Speicher.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server, die Partitionierung der Hardware unterstützen müssen hinzufügen und hot Ersatz für alle unterstützte Betriebssystem Komponententypen unterstützen. PU unterstützt Komponententypen Hot-add-sind Prozessoren, Arbeitsspeicher und e/a. Komponententypen Hot ersetzen-unterstützt werden, Prozessoren und Arbeitsspeicher Subsysteme.
 

### <a name="systemserverdynamicpartitioninghotaddvisual"></a>System.Server.DynamicPartitioning.HotAddVisual

*Server, die Partitionierung der Hardware unterstützen müssen visuelle Benutzer Anzeige des Status von bereitstellen hot-add-Ereignisse, wenn keine Benachrichtigung softwarebasierte bereitgestellt wird.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server, die Unterstützung für eine oder mehrere hot-Hinzufügen von Komponenten-Features visuell den Status der einzelnen bereitstellen müssen hinzufügen hot-Ereignis wenn keine Partition-Verwaltungssoftware bereitgestellt wird.
 

### <a name="systemserverdynamicpartitioninghotreplacepu"></a>System.Server.DynamicPartitioning.HotReplacePU

*In Servern, die dynamische Partitionierung unterstützen, hot Replacement PUs benötigen, gleich und kompatibel Hardwareressourcen für die PU ersetzt werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein Prozessor oder Speicher PU als Ersatz auf einem Server, der dynamische Partitionierung unterstützt benötigen, gleich und kompatibel Hardwareressourcen für die zu ersetzende PU verwendet; d. h., den gleichen Prozessortyp und schrittweise durchlaufen und die gleiche Speicherkonfiguration.


### <a name="systemserverdynamicpartitioningpartialhotadd"></a>System.Server.DynamicPartitioning.PartialHotAdd

*Teilweise Erfolg der eine hot-add-Aktion auf einem Server, die dynamische Partitionierung unterstützt wirkt sich nicht auf die Stabilität der Partition oder des Servers.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Komponenten im Zusammenhang mit einer hot-add-Aktion auf einem Server, die dynamische Partitionierung unterstützt, die nicht gestartet (Geparkte Komponente) darf keine sich nachteilig auf die anderen Komponenten in der PU, Partition oder Server.


### <a name="systemserverdynamicpartitioningsoftwarestatus"></a>System.Server.DynamicPartitioning.SoftwareStatus

*Server, die Partitionierung der Hardware unterstützen müssen Partition-Verwaltungssoftware angeben, der den Benutzer mit dem Status für jeden Hot-add oder hot-ersetzen-Ereignis enthält.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server, die Partitionierung der Hardware unterstützen müssen Partition-Verwaltungssoftware angeben. Status eines Ereignisses Hot-add oder hot ersetzen wird durch das Windows-Betriebssystem in der betroffenen Partition zur Verfügung gestellt. Die Software PM muss visuell von dieser Status wird an den Administrator PM angeben.


### <a name="systemserverdynamicpartitioningsubsystem"></a>System.Server.DynamicPartitioning.Subsystem

*Auf Servern, die dynamische Partitionierung unterstützen, werden in eine andere Partition Einheit Prozessoren und Arbeitsspeicher Subsysteme e/a-Subsysteme bereitgestellt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Um Erfolg des hot ersetzen Features zu aktivieren, müssen e/a-Subsysteme implementiert werden, in einer anderen PU Prozessoren und Arbeitsspeicher-Subsysteme auf Servern, die dynamische Partitionierung unterstützen.


## <a name="systemserverfaulttolerant"></a>System.Server.FaultTolerant

*Dieses Feature definiert Fehlertoleranz fehlertolerante Anforderungen für Server-Systeme.*


### <a name="systemserverfaulttolerantcore"></a>System.Server.FaultTolerant.Core

*Zur Unterstützung von Fehlertoleranz Vorgänge müssen die Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Systeme müssen die unten aufgeführten Anforderungen entsprechen und übergeben Sie den Test mit Fehlertoleranz Windows Hardware Zertifizierung Kit, um in Windows Server-Katalog mit Fehlertoleranz aufgelistet werden.

Eine fehlertolerante Reihe \[FT Set\] Systeme ist eine Gruppierung von Systemen, die Redundanz für jede Hardwarekomponente in einem einzelnen System von den FT festgelegt und kann alle Hardwarefehler maskieren, sodass vernetzten Clients nicht durch den Verlust der Verbindung aufgrund Netzwerktimeouts an die FT aufgrund der Hostname Festlegen von der Hardwarefehler wie betroffen sind , Domänennamen, MAC-Adresse oder IP-Adresse und die Dienste oder der Anwendung auf die FT festgelegt sind, sind somit nicht verfügbar, auf diejenigen Netzwerk verbundenen Clients. Darüber hinaus wird eine Menge FT vernetzten Clients als ein einziges System mit einem einzelnen Hostnamen, Domänennamen, MAC-Adresse oder IP-Adresse und eindeutige Instanzen von Diensten oder Anwendungen angezeigt.

Eine Menge FT muss enthalten Systemuhrzeit, die Ausführung im tatsächlichen Gleichschritt, d. h., ist nur eine Uhr-Domäne für die FT Set oder virtuellen Gleichschritt, d. h., die Uhren in den Systemen, die den Satz FT umfassen in regelmäßigen Abständen von weniger als einer Sekunde synchronisiert werden. Dadurch wird die FT Set immer Reaktion auf genau die gleiche Interrupts gleichzeitig genau, und daher genau die gleichen Schritte ausgeführt werden und haben denselben Status jederzeit, womit die erforderliche Redundanz.

Eine Menge FT ist berechtigt, synchronisieren, d. h., stellen identisch, Betriebssystem-Images nach einem Hardwarefehler in einem System des Satzes FT korrigiert, sodass vernetzten Clients nicht von Verlust der Verbindung aufgrund Netzwerktimeouts an die FT-Satz aufgrund der Hostname, Domänenname, MAC-Adresse oder IP-Adresse durch die erneute Synchronisierung wie betroffen sind , und die Dienste oder eine Anwendung auf die FT festgelegt sind, sind somit nicht verfügbar, mit denen Netzwerk verbundenen Clients. Die Korrektur des Problems möglicherweise durch Austausch oder der Reparatur der fehlerhafte Hardware-Komponente, oder wenn die Hardwarefehler vorübergehende, ist möglicherweise gelöscht werden, indem ein Systemneustart, dass erzwingt die erneute Initialisierung aller Geräte im System, das Bestandteil der FT ist festgelegt.

FT Systeme möglicherweise deaktivieren oder nicht enthalten Geräte, die asynchrone Interrupts eintritt, dass ein einziges System in den FT redundante auf einen Interrupt reagieren, die andere Systeme des Satzes FT nicht Erfahrung musste verursachen können. Beispiele für solche Geräte Geräte monitoring werden würde \[Thermal, Spannung usw.\], oder externen Geräten, die einen Benutzer versehentlich unterbrechen oder nur ein einziges System in einem Satz FT, beispielsweise eine CD/DVD-Laufwerk, Tastatur, Maus usw. Zugriff zulassen würden.
 

## <a name="systemserverfirmwareuefigop"></a>System.Server.Firmware.UEFI.GOP

*In diesem Abschnitt werden die Anforderungen für Systeme implementieren UEFI-Firmware beschrieben.*


### <a name="systemserverfirmwareuefigopdisplay"></a>System.Server.Firmware.UEFI.GOP.Display

*System-Firmware muss GOP unterstützen, und zeigt Windows Anforderungen an.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Wenn die System-Firmware UEFI unterstützt, können es darüber hinaus Grafiken Ausgabe Protocol (GOP) unterstützen. Wenn Grafiken Ausgabe Protocol (GOP) unterstützt wird, ist muss, wie in UEFI 2.3.1 definiert.

Während dieser Zeit, wenn die Firmware im Steuerelement ist, sind die folgenden Anforderungen:

**Auswahl der Topologie**

 - UEFI muss zuverlässig alle zeigt erkennen, die mit der POST-Adapter verbunden sind. Der Bildschirm grafikbasierten kann nur auf einem Monitor mit der POST-Adapter verbunden angezeigt werden.

 - Für den Fall, dass mehrere Monitore festgestellt werden, muss UEFI grafikbasierten Bildschirms auf der Grundlage der folgenden Logik anzeigen:

     - System mit einer integrierten Display (Laptop, alle In einem Tablet): UEFI muss der Bildschirm grafikbasierten nur auf die integrierte Anzeige

     - System **ohne** eine integrierte Anzeige (integrierte Anzeige ist Herunterfahren oder desktop System): UEFI muss der Bildschirm grafikbasierten einen Bildschirm. UEFI muss die Anzeige von Priorisierung wird basierend auf den Verbindungstyp auswählen. Die Priorisierung ist wie folgt: DisplayPort, HDMI, DVI, HD15, Component, S-Video. Wenn mehrere Bildschirme mit dem gleichen Connectortyp verbunden sind, kann die Firmware welche davon verwenden soll.

 
**Die Auswahl**

 - Nachdem die Anzeige auf aktiviert, um den Bildschirm grafikbasierten UEFI ermittelt, müssen sie den Modus basierend auf der folgenden Logik anwenden auszuwählen:

     - System mit einer integrierten Display (Laptop, alle In einem Tablet): die Anzeige muss immer auf die systemeigene Auflösung und systemeigene Timing festgelegt werden

     - System **ohne** eine integrierte Anzeige (Desktop):

         - UEFI muss Versuch, die systemeigene Auflösung und die zeitliche Steuerung der Anzeige durch beschaffen es aus der EDID.

         - Wenn die nicht unterstützt wird, muss UEFI einen alternativen Modus auswählen, der das gleiche Seitenverhältnis als die systemeigene Auflösung der Anzeige übereinstimmt.

         - Zumindest muss UEFI einen Modus von 1024 x 768 festlegen.

         - Wenn Anzeigegeräts keine EDID bereitstellt, muss einen Modus von 1024 x 768 UEDI festgelegt werden.

     - Die Firmware muss immer eine 32-Bit-Puffer linear Frame verwenden, um den grafikbasierten-Bildschirm

     - PixelsPerScanLine muss die HorizontalResolution entsprechen.

     - PixelFormat muss PixelBlueGreenRedReserved8BitPerColor sein. Beachten Sie, dass ein physikalischer Rahmenpuffer erforderlich ist. PixelBltOnly wird nicht unterstützt.

**Modus zum Löschen des Archivs**

 - UEFI muss löschen die Liste der verfügbaren Modi nach den Vorgaben in EFI genannten\_GRAFIKEN\_AUSGABE\_PROTOKOLL. QueryMode() (gemäß der Spezifikation, Version 2.1 UEFI).

**Bereitstellen der EDID**

 - Sobald die UEFI einen Modus auf die entsprechende Anzeige (basierend auf der Auswahl der Topologie) festgelegt, UEFI erhalten die EDID der Anzeige und Windows übergeben, wenn Windows EFI verwendet muss\_EDID\_ERMITTELTE\_PROTOKOLL (gemäß der Spezifikation, Version 2.1 UEFI) zum Abfragen von der EDID.

 - Es ist möglich, dass einige integrierte Fenster ein EDID im Bereich Anzeige selbst möglicherweise nicht.  In diesem Fall muss UEFI die EDID produzieren. Die EDID muss genau die systemeigene Timing und die physischen Dimensionen der der integrierte Systemsteuerung angeben.

 - Wenn die Anzeige nicht integriert ist, und verfügt nicht über ein EDID, klicken Sie dann muss die UEFI nicht Herstellung einer EDID.


## <a name="systemserverfirmwarevbe"></a>System.Server.Firmware.VBE

*Die Anforderungen in diesem Abschnitt werden auf jedem Grafikgerät mit Unterstützung von VBE Firmware erzwungen und Treiber Anzeigebereich des WDDM implementiert wird.*


### <a name="systemserverfirmwarevbedisplay"></a>System.Server.Firmware.VBE.Display

*System-Firmware, die VBE unterstützt muss die Windows Display Anforderungen entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Wenn eine System-Firmware VBE für Anzeige-Steuerelement unterstützt, und klicken Sie dann muss es die folgenden Anforderungen erfüllen: die Anzeige von der Firmware Videogerät bevor der Grafiktreiber WDDM übernimmt gesteuert wird. Während dieser Zeit, wenn die Firmware im Steuerelement ist, sind die folgenden Anforderungen:

**Auswahl der Topologie**

 - Video Gerätefirmware muss zuverlässig alle zeigt erkennen, die mit der POST-Adapter verbunden sind. Der Bildschirm grafikbasierten kann nur auf einem Monitor mit der POST-Adapter verbunden angezeigt werden. 

 - Für den Fall, dass mehrere Monitore festgestellt werden, muss Videogerät Firmware grafikbasierten Bildschirms auf der Grundlage der folgenden Logik anzeigen:

     - System mit einer integrierten Display (Laptop, alle In einem Tablet/konvertiert werden kann): Video Gerätefirmware muss der Bildschirm grafikbasierten nur auf die integrierte Anzeige

     - System **ohne** eine integrierte Anzeige (integrierte Anzeige ist Herunterfahren oder desktop System): Video Gerätefirmware muss der Bildschirm grafikbasierten einen Bildschirm. Videogerät Firmware muss die Anzeige von Priorisierung der zeigt, basierend auf Verbindungstyp auswählen. Die Priorisierung ist wie folgt: DisplayPort, HDMI, DVI, HD15, Component, S-Video. Wenn mehrere Bildschirme mit dem gleichen Connectortyp verbunden sind, kann die Firmware welche davon verwenden soll.

**Die Auswahl**

 - Nachdem die Anzeige auf aktiviert, um den Bildschirm grafikbasierten Videogerät Firmware ermittelt, müssen sie den Modus basierend auf der folgenden Logik anwenden auszuwählen:

     - System mit einer integrierten Display (Laptop, alle In einem Tablet/konvertiert werden kann): die Anzeige muss immer auf die systemeigene Auflösung und systemeigene Timing festgelegt werden

     - System **ohne** eine integrierte Anzeige (Desktop):

         - Videogerät Firmware muss versuchen, die systemeigene Auflösung und die zeitliche Steuerung der Anzeige festzulegen, indem Sie es aus der EDID abrufen

         - Wenn, nicht unterstützt wird, muss die Firmware Videogerät einen alternativen Modus auswählen, der das gleiche Seitenverhältnis als die systemeigene Auflösung der Anzeige übereinstimmt.

         - In jedem Fall muss die Firmware Videogerät einen Modus von 1024 x 768 festgelegt.

         - Wenn Anzeigegeräts keine EDID bereitstellt, muss einen Modus von 1024 x 768 UEDI festgelegt werden.

     - Videogerät Firmware muss immer eine 32-Bit linear Framepuffer verwenden, um den Bildschirm grafikbasierten

     - PixelsPerScanLine muss die HorizontalResolution entsprechen.

     - PixelFormat muss PixelBlueGreenRedReserved8BitPerColor sein. Beachten Sie, dass ein physikalischer Rahmenpuffer erforderlich ist. PixelBltOnly wird nicht unterstützt.

**Modus zum Löschen des Archivs**

 - Die Videogerät Firmware muss beim Windows die Funktion 01 h (VBE-Modus Informationen zurückgeben) gemäß der VESA BIOS-Erweiterung Core Funktionen Standard Version 3.0 verwendet eine Liste der Modi Windows angeben.

 - Die Videogerät Firmware muss die Modi entsprechend gelöscht. Es sollte nur die Modi auflisten, die in der Anzeige der EDID unterstützt werden, die derzeit aktiv ist. Es ist nicht erforderlich, zur Unterstützung der Lösungen, die für die in der EDID unterstützt.

 - Die Firmware Videogerät muss 800 x 600 und 1024 x 768 unterstützen.

 - Alle Modi müssen Fortschritt 60 Hz sein.

 
**Bereitstellen der EDID**

 - Sobald einen Modus Videogerät Firmware auf die entsprechende Anzeige (basierend auf der Auswahl der Topologie) festgelegt, muss Videogerät Firmware erhalten die EDID der Anzeige und an den Windows übergeben, wenn Windows Befehl 15 h (Display Data Channel) gemäß der VESA BIOS-Erweiterung Core Funktionen Standard Version 3.0 verwendet:

     - Es ist möglich, dass einige integrierte Fenster ein EDID im Bereich Anzeige selbst möglicherweise nicht.  In diesem Fall muss Videogerät Firmware die EDID produzieren. Die EDID muss exakt die systemeigene Timing und die physischen Dimensionen der der integrierte Systemsteuerung angeben.

     - Wenn die Anzeige nicht integriert ist, verfügt nicht über ein EDID muss Videogerät Firmware nicht Herstellung einer EDID


## <a name="systemservergraphics"></a>System.Server.Graphics

*Basis für Grafiken auf Serversystemen.*


### <a name="systemservergraphicswddm"></a>System.Server.Graphics.WDDM

*Alle Windows Graphics-Treiber muss WDDM.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Die WDDM-Architektur bietet Funktionen zum Aktivieren von Features wie desktop Zusammensetzung, erweiterte Fehlertoleranz Fehlertoleranz, Videospeichermanager, Planer, schneidet Prozessfreigabe von D3D Flächen und so weiter. WDDM wurde speziell für Grafikgeräte modernen, die mindestens Direct3D 10 Feature Ebene 9 sind\_3 mit PixelShader 2.0 oder besser und verfügen über alle erforderlichen Hardwarefunktionen zur Unterstützung der Funktion WDDM Arbeitsspeicher Verwaltung, Planung und Fehlertoleranz. Alle Systeme, die im Lieferumfang von Windows 10 ist WDDMv1.3 erforderlich.

Der folgenden Tabelle wird die Verwendung der Szenario für die Grafiktreiber Typen erläutert.

|      &nbsp;         | Client                          | Server   | Client Ausführung in einer virtuellen Umgebung | Virtuelle Server |
|---------------|---------------------------------|----------|-----------------------------------------|----------------|
| Vollständige Grafiken | Erforderliche Gerät buchen         | Optional | Optional                                | Optional       |
| Nur anzeigen  | Nicht zulässig                     | Optional | Optional                                | Optional       |
| Nur rendern   | Optional als nicht-primäre adapter | Optional | Optional                                | Optional       |
| Headless      | Nicht zulässig                     | Optional | n/v                                     | n/v            |

 
## <a name="systemservermanageabilityredfish"></a>System.Server.Manageability.Redfish

<!--No content provided here in the original Word file.-->


### <a name="systemservermanageabilityredfishbasic"></a>System.Server.Manageability.Redfish.Basic

Server Baseboard Management Controller (BMC) Geräte können Out-of-Band-Management-Funktionen, die basierend auf dem Standard DMTF Goldbarsch unterstützen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

BMC Geräte möglicherweise Server Hardware Out-of-Band-Management-Funktion unter Verwendung des DMTF Goldbarsch DSP0266 v1.0.1-Spezifikation und zugehörige Goldbarsch Schemadefinitionen (DSP8010) zu unterstützen. Wenn Goldbarsch implementiert ist, sind die folgenden Anforderungen zwingend erforderlich.

Es ist nicht erforderlich, dass der BMC die vollständige Goldbarsch Spezifikation implementiert, da nur eine Teilmenge der Funktionalität für Out-of-Band-Verwaltung erforderlich ist. Der BMC muss die folgenden Funktionen unterstützen und Goldbarsch Schema definiert:


<ol style="list-style-type: decimal">
<li>
<p>Sicherheit</p>
<ol style="list-style-type: lower-alpha">
<li><p>Unterstützung der Sitzung Verbindungen über HTTPS (TLS).</p></li>
<li><p>Unterstützung für LDAP und Radius der formularbasierten Authentifizierung.</p></li>
<li><p>BMC darf kein Benutzerkonto für anonyme Benutzer standardmäßig konfiguriert haben. Wenn dieses Konto vorhanden ist, muss es deaktiviert werden.</p></li>
<li><p>Der BMC ermöglicht die Verwaltung von remote-Anmeldeinformationen. Der BMC muss seine Administratorkennwort geändert wird, über das Schema AccountService unterstützen.</p></li>
</ol>
</li>
<li>
<p>Die Hardware-Ereignisprotokolle können über die Verwendung des Schemas die LogService BMC verwaltet werden.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Die Hardware-Ereignisprotokolleinträge können gelesen werden.</p></li>
<li><p>Die Hardware-Ereignisprotokolleinträge können gelöscht werden.</p></li>
<li><p>Die Hardware-Ereignisprotokollzeit des Servers.</p></li>
<li><p>Die Hardware-Ereignisprotokoll Kapazitätsinformationen.</p></li>
</ol>
</li>
<li>
<p>Der Status des Systems Power kann über die Verwendung des Schemas ComputerSystem BMC verwaltet werden.</p>
<ol style="list-style-type: lower-alpha">
<li>
<p>BMC muss die folgenden Server Systeminformationen verfügbar machen:</p>
<ol style="list-style-type: lower-roman">
<li><p>Aktuelle Power Zustand des Servers.</p></li>
</ol>
</li>
<li>
<p>Der BMC muss die folgenden Vorgänge durchgeführt werden, auf dem Server unterstützen.</p>
<ol style="list-style-type: lower-roman">
<li><p>Power außerhalb des physischen Servers über die BMC,</p></li>
<li><p>Schalten Sie des physischen Servers über die BMC.</p></li>
<li><p>Schalten Sie einen physischen Server über die BMC</p></li>
</ol>
</li>
</ol>
</li>
<li>
<p>Das System Boot-Quelle kann durch den BMC konfiguriert werden. Diese Funktionalität wird über das ComputerSystem Schema implementiert.</p>
<ol style="list-style-type: lower-alpha">
<li><p>Der Server kann zum nächsten Starten von der PXE-Server konfiguriert werden Zeit wird zurückgesetzt</p></li>
<li><p>Der Server kann von der Festplatte des nächsten Starten konfiguriert werden Zeit wird zurückgesetzt</p></li>
<li><p>Der Server kann so konfiguriert werden, um immer vom PXE-Server zu starten</p></li>
<li><p>Der Server kann so konfiguriert werden, dass immer von der Festplatte zu starten</p></li>
</ol>
</li>
<li>
<p>Des Systems BMC Firmware und BIOS-Version, dass Informationen über Goldbarsch verfügbar gemacht wird.</p>
<ol style="list-style-type: lower-alpha">
<li>
<p>Der BMC muss die Versionsinformationen für die folgenden Komponenten verfügbar machen:</p>
<ol style="list-style-type: lower-roman">
<li><p>BIOS/UEFI (ComputerSystem-Schema).</p></li>
<li><p>BMC Management Firmware (Manager-Schema).</p></li>
</ol>
</li>
</ol>
</li>
<li>
<p>Die OOB Management LAN-Konfiguration kann durch den BMC aktualisiert werden. Dies gilt nur für Systeme, die Konfiguration der Verwaltung von LAN OOB über die Benutzeroberfläche Goldbarsch verfügbar machen.</p>
<ol style="list-style-type: lower-alpha">
<li><p>BMC muss die folgende Informationen zu den BMC LAN-Konfiguration verfügbar zu machen: IP-Adresse, Subnetzmaske, das Standardgateway und ein Indikator, ob mit einer statischen IP-Adresse der BMC konfiguriert ist oder wenn eine wird von DHCP (BMCs EthernetInterface Schema) zugewiesen.</p></li>
</ol>
</li>
<li>
<p>Das System-Lösungsentwickler wird durch den BMC verfügbar gemacht. BMC muss die folgenden Server Systeminformationen über das ComputerSystem Schema verfügbar machen:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Hersteller der Serverhardware</p></li>
<li><p>Modell der Serverhardware</p></li>
<li><p>Server SMBIOS GUID</p></li>
<li><p>Asset-Tag des Servers</p></li>
<li><p>Seriennummer des Servers</p></li>
</ol>
</li>
<li>
<p>Hardware-Überwachung des Systems muss über die Schemas Chassis, Thermal und Power unterstützt werden:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Abrufen von physischen Lüfter Integrität</p></li>
<li><p>Abrufen von Power Kooperation Integrität</p></li>
<li><p>Einen Sensor Benachrichtigungen der CPU</p></li>
<li><p>Abrufen von integrierten Netzwerkadapter integritätsbenachrichtigungen, wenn unterstützt</p></li>
<li><p>Abrufen von integritätsbenachrichtigungen HBA-Controller, wenn unterstützt</p></li>
<li><p>Abrufen von integritätsbenachrichtigungen Speicher, wenn unterstützt</p></li>
</ol>
</li>
</ol>


**Erzwingung**

Dies ist ein *If-implementierte* optional Gerät Anforderung. Dies ist eine erforderliche Gerät Voraussetzung für Server zu Out-of-Band-verwaltbaren den DMTF Goldbarsch Standard verwendet werden. Diese Anforderung wird also tatsächlich bei der Freigabe von Windows Server vNext.

**Unternehmensvorgabe**

Server-Bereitstellungen sind in Rest-Infrastrukturen verschoben, die angezeigt werden, dass sie extrem skalierbar sind. Skalierbare Bereitstellungen immer häufiger vertrauter wird, basiert wie umstellen von einem IPMI Out-of-Band-Management-Schnittstelle auf eine Schnittstelle Goldbarsch RESTful Methoden mit gemeinsamen OData-Konventionen ist ein entscheidender Faktor, moderne Data Center Sicherheit und einem festen Maßstab für die Unterstützung bereitstellen.




## <a name="systemserverpowermanageable"></a>System.Server.PowerManageable

*Dieses Feature definiert verwaltbaren Energiebedarf Server-Systeme.*


### <a name="systemserverpowermanageableacpipowerinterface"></a>System.Server.PowerManageable.ACPIPowerInterface

*Power verwaltbaren Server unterstützt die Leistungsfähigkeit Messung und Budgetierung ACPI-Schnittstelle.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server bietet Unterstützung für Ebene Stromverbrauchs lesen und lesen und schreiben das System Power Budget für den Server mit der 'Stromversorgung, Messung und Budgetierung Schnittstelle' in der ACPI 4.0-Spezifikation. Das System Power Budget bietet einen unterstützten Bereichs, dass das Budget, in dem sich der minimale Budgetwert niedriger als der maximale Budgetwert festgelegt werden kann. Die Power-Anzeige unterstützt einen Bereich von Mittelwert Intervallen so, dass mindestens Mittelwert Intervall 1 Sekunde ist oder die unter- und die maximale Mittelwert Intervall beträgt fünf Minuten oder höher. Um mit der Spezifikation auszurichten, muss das Samplingintervall für den Statusanzeiger Power Mittelwert Intervall mindestens kleiner oder gleich.
 

### <a name="systemserverpowermanageableperformancestates"></a>System.Server.PowerManageable.PerformanceStates

*Wenn Prozessors in einem Serversystem Performance Status zu unterstützen, stellt der Server Mechanismen, wird dieser Zustände für Windows verfügbar.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Wenn die Prozessoren auf dem Server Performance Status zu unterstützen, stellt dem Server Firmware Mechanismen, um die Steuerung des Prozessors Leistung Staaten Windows übergeben. Dieser Mechanismus muss auf dem Server in der Standardeinstellung aktiviert sein.


### <a name="systemserverpowermanageableremotepowercontrol"></a>System.Server.PowerManageable.RemotePowerControl

*Power verwaltbarer Server bietet eine standardisierte remote Out-of-Band-Schnittstelle zum Abfragen und steuern die Leistungsfähigkeit des Systems.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Power verwaltbarer Server bietet nicht genügend Band remote Management-Schnittstelle aus dem Server Baseboard Management Controller (BMC), die mit den IPMI DCMI, oder SMASH (über WS-MAN) kompatibles ist "Power State Management Profil" zum Abfragen des Zustand Power power aktiviert oder deaktiviert (off vorläufig) dem Server Remote.
Dies ist eine Voraussetzung für die Power verwaltbaren zusätzliche Qualifikation für Windows Server.

Weitere Details im Profil SMASH finden Sie auf der Distributed Management Task Force-Website unter - <http://www.dmtf.org/standards/published_documents/DSP1027.pdf>.


## <a name="systemserverremotefx"></a>System.Server.RemoteFX

*Dieses Feature definiert RemoteFX Anforderungen für Server-Systeme.*


### <a name="systemserverremotefxremotefx"></a>System.Server.RemoteFX.RemoteFX

*Server zur Unterstützung von RemoteFX müssen die Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server müssen die folgenden Anforderungen erfüllen:

 - CPU SLAT - CPU muss SLAT unterstützen. Diese Anforderung wird die Leistung in den RemoteFX Virtualisierung Szenarien unterstützen.

 - GPU Anforderungen - muss WDDM GPUs, die Direct3D11 unterstützen. Diese Anforderungen gelten für nur die GPUs RemoteFX Arbeitslasten zu unterstützen.

 - Homogene GPUs für RemoteFX-Arbeitslasten - muss die GPUs, die zum Ausführen von RemoteFX Arbeitslasten gedacht sind die gleichen GPU den gleichen Treiber ausgeführt.


## <a name="systemserversmbios"></a>System.Server.SMBIOS

*Dieses Feature definiert SMBIOS Anforderungen für Server-Systeme*


### <a name="systemserversmbiossmbios"></a>System.Server.SMBIOS.SMBIOS

*System-Firmware muss vollständig und entsprechend SMBIOS Strukturen vom Typ 16 und vom Typ 17 zu implementieren*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

System-Firmware muss vollständig und entsprechend SMBIOS Strukturen vom Typ 16 (Beschreibung des physischen Arbeitsspeichers Arrays) implementieren und vom Typ 17 (Beschreibung der Speichergeräte), durch die SMBIOS-Spezifikation erlaubt. Implementierung von anderen SMBIOS Arbeitsspeicher Beschreibung Strukturen - Typen 19, 20 und 37 - sind optional.

Ein JEDEC kompatible DRAM DIMM unterstützt Serial Presence Detect (SPD). Über dieses Mechanismus und definierten Standards kann das Modul im Hinblick auf deren Hersteller, Seriennummer und andere nützliche Informationen identifiziert werden. Die JEDEC Standards erfordern bestimmte Daten in den unteren 128 Bytes ein EEPROM, die sich nicht auf das Speichermodul befinden. Programmierung von diesem EEPROM erfolgt normalerweise von Anbietern von DRAM DIMMs an ihren Ursprung der Herstellung und kann optional wiederholt danach um Spezifikationen ihre OEMs oder Einzelhandelsunternehmen Anforderungen für das branding Zwecke beim durchgehen Vertriebskanäle erfüllen.

Die Systemfirmware (BIOS oder UEFI) Prüfpunkte und extrahiert diese Informationen aus dem DIMM über seine SMBus-Schnittstelle. System-Firmware anhand dieser Informationen die Speichercontroller konfigurieren. System-Firmware, das unterstützt SMBIOS v2. 4 oder höher übermittelt die oben genannten DIMM-spezifische Informationen zu den Betriebssystemen und Programme über eine Reihe von SMBIOS Strukturen ("Tabellen") Arbeitsspeicher Beschreibungen. Diese SMBIOS Strukturen werden auch die Systemtopologie Arbeitsspeicher sowie die Geometrie und Merkmale beschrieben. Die kurz hier zu Referenzzwecken beschrieben und finden Sie in der aktuellen SMBIOS v2. 5-Spezifikation (5 September 2006):

 - Physischen Arbeitsspeicher Array (Typ 16) mit Informationen zu den Standort, Verwendung und Korrektur Fehlertypen. Seiten 51-52.

 - Arbeitsspeicher Array zugeordnete Adresse (Typ 19) mit der Adresszuordnung für einen physischen Arbeitsspeicher Array (eine Struktur für jede zusammenhängenden Adressbereich beschrieben vorhanden ist); Seite 56.

 - Speichergerät (Typ 17) mit Informationen zu Formfaktor, Typ und Details; Seiten 52 54

 - Arbeitsspeicher Gerät zugeordnete Adresse (Typ 20) mit der Adresszuordnung zu einer Granularität auf Device-Ebene (eine Struktur für jede zusammenhängenden Adressbereich beschrieben vorhanden ist); Seite 56.

 - Arbeitsspeicher Channel (Typ 37) mit Korrelation zwischen einem Kanal Speicher und seine zugeordnete Arbeitsspeicher-Geräte (jedes Gerät stellt eine oder mehrere Lasten auf den DDE-Kanal); Seite 68. Diese Unterstützung in der Systemfirmware wird:

     - Können Sie die Kunden ihre Server Speicherkomponenten als bereitgestellte IT-Ressourcen verwalten, und ein umfassendes Verständnis des Investment dieser Ressourcen im Hinblick auf RAS-Fähigkeiten und Cost of Ownership verwalten.

     - Ermöglichen Sie Server und jedem Rechenzentrum-Management-Lösungen, um diese Informationen in ihrer Diagnose-Tools und Methoden für eine bessere RAS-Funktionen nutzen.

     - Aktivieren Sie bestimmte Klassen der ISV-Produkte (RAM-Datenträger, usw.) nutzen diese Informationen für eine bessere Leistung und Funktionen auf Windows-Plattformen.



## <a name="systemserverstoragemanageabilitysmapi"></a>System.Server.StorageManageability.Smapi

*Dieses Feature definiert Anforderungen für die Verwaltung von Server verbundene Speichergerät. Einem Speichergerät gilt bei Verwendung mit einem Windows Server System über eine Fabric-Schnittstelle verbunden. Diese Art von Storage-Schnittstelle enthält FibreChannel FibreChannel over Ethernet (FCoE), iSCSI und kleine und mittelständische Betriebe3.*

*Diese Verwaltbarkeit von einem verbundenen Speichergerät bedeutet, dass der Benutzer einen End-to-End-Speicher-Workflow verwenden eine einheitliche Benutzeroberfläche wie WMI, PowerShell, oder die Datei und Storage Services in einer Server-Verwaltungstools ausführen kann. Diesen Workflow darf, auch vor dem betriebsbereite-Ziel erreichbar sein Windows Server OS in der Umgebung bereitgestellt wird. Das verbundenen Speichergerät muss verwaltbar von Windows Server, über die Speicher-Management-API (SMAPI) sein. Die Integration in SMAPI mit SNIA Storage Management Interface Specification (SMI-S) oder eine Storage Management-Anbieter (SMP). Implementieren von SMI-S und SMP ist nicht erforderlich.*

**Unternehmensvorgabe**

Verwaltbaren verbundenen Speichergeräten ermöglichen eine effiziente Bereitstellung und Verwendung des Server-Systeme, Windows Server in einem Rechenzentrum Software definiert ausgeführt und daher Senkung der Betriebskosten für den Kunden, in der heterogenen Hardware-Plattformen bereitgestellt werden.


## <a name="systemserverstoragemanageabilitysmapiblockstorage"></a>System.Server.StorageManageability.Smapi.BlockStorage

<!--No content provided here in the original Word file.-->

### <a name="systemserverstoragemanageabilitysmapiblockstoragebasicfunction"></a>System.Server.StorageManageability.Smapi.BlockStorage.BasicFunction

*Einem Speichergerät verbundenen Block muss durch Windows über seine Speicher-Management-API (SMAPI) verwaltbar sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

SMAPI unterstützt FC, FcoE, iSCSI und SAS-Block Speichergeräten an.
Speichergeräten über SMAPI verbundenen Block müssen die folgenden Verwaltungsvorgänge unterstützen:

-   Ermittlung von Speicherpool, Speichervolumes (auch bekannt ALS LUN), Speichermedien, Initiator-Ports, Zielports, Ansichten, Konsistenz, Replikationsgruppen Maskierung

-   Bereitstellung des neuen Speichervolumes, Speicher Volume löschen, Speichervolumes Maske/Zeichen nicht maskiert

-   Erstellen und Löschen von lokalen Speicher Volume Momentaufnahmen, Klonen oder Spiegel

-   Erstellen, ändern, Löschen der (Konsistenzgruppen ALIAS Replikation)

-   Geplante/ungeplante Failover und reverse Replikation der von Konsistenzgruppen

-   Momentaufnahme und Klons von Konsistenzgruppen

-   Life cycle Angaben und alter Angaben

**Erzwingung**

Dies ist eine Voraussetzung für die obligatorische Gerät.


## <a name="systemserverstoragemanageabilitysmapiblockstorageremotereplication"></a>System.Server.StorageManageability.Smapi.BlockStorage.RemoteReplication

<!--No content provided here in the original Word file.-->

### <a name="systemserverstoragemanageabilitysmapiblockstorageremotereplicationbasicfunction"></a>System.Server.StorageManageability.Smapi.BlockStorage.RemoteReplication.BasicFunction

*Eine verbundener Block Storage Gerät remote-Replikation muss von Windows über seine Speicher-Management-API (SMAPI) verwaltbar sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

SMAPI unterstützt FC, FcoE, iSCSI und SAS-Block Speichergeräten an.
Speichergeräten über SMAPI verbundenen Block müssen die folgenden Verwaltungsvorgänge unterstützen:

-   Ermittlung von Konsistenz, Replikationsgruppen

-   Erstellen und Löschen von lokalen oder Remotecomputer Speicher Volume Momentaufnahmen, Klonen oder Spiegel

-   Erstellen, ändern, Löschen der (Konsistenzgruppen ALIAS Replikation)

-   Geplante/ungeplante Failover und reverse Replikation der von Konsistenzgruppen

-   Momentaufnahme und Klons von Konsistenzgruppen

-   Life cycle Angaben und alter Angaben

**Erzwingung**

Dies ist eine Voraussetzung für die obligatorische Gerät.


## <a name="systemserverstoragemanageabilitysmapifilestorage"></a>System.Server.StorageManageability.Smapi.FileStorage

<!--No content provided here in the original Word file.-->

### <a name="systemserverstoragemanageabilitysmapifilestoragebasicfunction"></a>System.Server.StorageManageability.Smapi.FileStorage.BasicFunction

*Ein verbundener Dateispeichergerät muss von Windows über seine Speicher-Management-API (SMAPI) verwaltbar sein.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

SMAPI unterstützt Speichergeräten für kleine und mittelständische Betriebe3-Datei. Verbundenen Datei Speichergeräten über SMAPI müssen die folgenden Verwaltungsvorgänge unterstützen:

-   Ermittlung des Dateisystems
-   Dateisystem-Datenträger erstellen/löschen
-   Erstellen/Löschen von Dateifreigabe
-   Ändern der Berechtigungen Dateifreigaben
-   Life cycle Angaben und alter Angaben

**Erzwingung**

Dies ist eine Voraussetzung für die obligatorische Gerät.


## <a name="systemserverstoragemanageabilitysmapismi"></a>System.Server.StorageManageability.Smapi.Smi

<!--No content provided here in the original Word file.-->

### <a name="systemserverstoragemanageabilitysmapismictp"></a>System.Server.StorageManageability.Smapi.Smi.Ctp

*Ein Industriestandard Speichergerät verbunden, das über die systemeigene SMI-S v1.6.1 Anbieterschnittstelle verwaltbaren ist veranschaulicht solche Konformität über einen erfolgreichen CTP Testdurchlauf.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Ein verbundener Speichergerät gilt Industriestandard, wenn es Verwaltbarkeit aus Gründen der Storage Networking Industry Association (SNIA) Storage Management Initiative Specification (SMI-S) v1.6.1 unterstützt. In der verbundenen Speichergerät ohne Hilfe eines externen Begleit-Anbieters Betrieb in einer separaten Gerät Anlage muss diese SMI-S v1.6.1 Anbieter-Schnittstelle implementiert werden. Dies sollte solche Konformität durch einen Test erfolgreich Durchlauf [SNIA SMI-S die Konformität testen Programm (CTP)](http://snia.org/ctp/)führen, und das Testergebnis von dem SNIA SMI Lab Konformität befürwortet werden muss.

**Erzwingung**

Dies ist eine obligatorische Gerät-Anforderung für ein verbundener Speichergerät zu Industriestandard und mithilfe von einem Windows Server System Smapi über Smi verwaltbar sein.

Hierzu und alle zugehörigen untergeordneten Anforderungen an werden jedoch für ein verbundener Speichergerät zu Industriestandard und von einem Windows Server System einfach zu verwaltende werden obligatorisch. Verbundenen Speichergeräten, die SMI-S unterstützen müssen die Anforderungen bei den hier angegebenen unterstützen: <https://msdn.microsoft.com/en-us/library/windows/hardware/dn265461(v=vs.85).aspx>


## <a name="systemserversvvp"></a>System.Server.SVVP

*Dieses Feature definiert Anforderungen für das SVVP Programm.*


### <a name="systemserversvvpsvvp"></a>System.Server.SVVP.SVVP

*Teilnahme an der Server Virtualization Validation Program Produkte müssen die Anforderungen erfüllen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Teilnahme an der Server Virtualization Validation Program Serverplattformen die hier genannten Anforderungen erfüllen: <http://www.windowsservercatalog.com/svvp.aspx>.


## <a name="systemserversystemstress"></a>System.Server.SystemStress

*Dieses Feature definiert Stress Systemanforderungen der Server-Systeme.*


### <a name="systemserversystemstressserverstress"></a>System.Server.SystemStress.ServerStress

*Server-System muss unter Stress einwandfrei funktionsfähig.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server-System muss ordnungsgemäß langer-Transport, nicht deterministisch hohe Belastung ausgeführt werden.  Die Hardware und Software Komponenten des Server-Systems müssen nicht dazu führen, dass Beschädigung der Daten, hängen, Speicherverluste, Fragmentierung des Speichers Ressource, Abstürze oder haben Auswirkungen auf andere Komponenten des Systems.  Server-Systeme müssen möglicherweise zuverlässig Herunterfahren und neu starten, klicken Sie unter Stress, unnötige und nicht geplante Ausfallzeiten zu verhindern.
Dies wird mit Stress-Tools, mit die emulieren lädt die auf einem Windows Server System werden möglicherweise getestet werden.


## <a name="systemservervirtualization"></a>System.Server.Virtualization

*Dieses Feature definiert Anforderungen für die Virtualisierung von Server-Systeme.*


### <a name="systemservervirtualizationprocessorvirtualizationassist"></a>System.Server.Virtualization.ProcessorVirtualizationAssist

*Prozessoren in die Unterstützung Virtualisierung Serverhardware unterstützt.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Alle Prozessoren auf dem Server müssen eine der folgenden Prozessor Virtualisierung Hardware Assist-Technologien unterstützen:

 - Intel VT-Technologie
 - AMD-V-Technologie

Informationen zu spezifischen Anforderungen für jede dieser Technologien stehen im Dokument Anforderungen für die Virtualisierung von Windows Server 2008.
Für den Zugriff auf das Dokument Anforderungen für die Virtualisierung von Windows Server 2008, senden Sie E-mail an <lhvrtreq@microsoft.com>.


## <a name="systemserverwhea"></a>System.Server.WHEA

<!--No content was provided here in the original Word file.-->

### <a name="systemserverwheacore"></a>System.Server.WHEA.Core

*Server ermöglicht die Erstellung von Fehlerberichten, System Hardware für das Betriebssystem.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Server sind erforderlich, um bereitzustellen Mechanismen zum Aktivieren von reporting oder Kommunikation korrigiert und nicht korrigierte System Hardwarefehler, die auf dem Server für das Betriebssystem verfügbar sind. Die Plattform möglicherweise Schwellenwert der korrigierten Fehler führen.

Der minimale Satz von Fehler Quellen sind:

* IA64 - Kontrollkästchen Ausnahme Computer, Computer-Kontrollkästchen korrigiert Plattform Fehler; INIT, PCI-Express Microsoft Application korrigiert

* X86-64 - Computer überprüfen Ausnahme, korrigiert Computer überprüfen, nicht Maskable Interrupt, PCI-Express Microsoft Application, Fehler beim STARTEN.

Eine Schnittstelle muss auf dem Server zur Erleichterung der Beibehaltung von Datensätzen Fehler bereitgestellt werden. Die Schnittstelle muss die Fehlerdatensätze über einen Neustart des Servers beibehalten und ein- und ausschalten. Zumindest muss die Plattform genügend freier Speicherplatz für einen nicht korrigierbaren Fehlerdatensatz angeben. Optionen für die Implementierung dieser Schnittstelle werden in der WHEA Plattform Design Guide beschrieben.

Windows Server bietet einen OSC-Mechanismus, um das Vorhandensein von WHEA im Betriebssystem anzugeben. Der Server muss diese Mechanismen berücksichtigt und WHEA fließt aktivieren, wenn die OSC erkannt wird. Optionale Mechanismen dienen zum Aktivieren der Firmware zum Verarbeiten von Ereignissen Fehler aus Quellen Fehler vor der Übergabe Steuerelement WHEA und kommunizieren dieses Verhalten für das Betriebssystem angegeben. Dadurch werden Konflikte Software Handhabung von Hardwareereignisse Fehler zu vermeiden.
Diese Mechanismen werden in der WHEA Plattform Design Guide beschrieben.

Server müssen für das Einfügen von Software einer Teilmenge der Hardware fehlerbedingungen in die Plattform die WHEA Validierung aktiviert WHEA definierten Schnittstellen unterstützen. Der Einfügung Mechanismus muss die Einfügung eines schwerwiegenden unterstützen nicht korrigierte und eine berichtigte Fehler; jedes um injizierbare Fehler ist eingefügten mithilfe einer der Fehler Quellen für die Plattform und mithilfe des Signalisierung Mechanismus für diese Fehlerquelle angegeben. Optionen, um diese Schnittstelle bereitzustellen, werden in der WHEA Plattform Design Guide beschrieben.

Für den Zugriff auf die WHEA Plattform Design Guide, senden Sie E-mail an <WHEAFB@Microsoft.com>.


## <a name="systemsolutionsazurestack"></a>System.Solutions.AzureStack

Microsoft Azure Stapel (MAS) wird ein neues Microsoft anbietet, dass eine einheitliche Gruppe von Azure-Cloud-Dienste lokal abgibt. Zwar die genauen Zusammensetzung der Microsoft Azure-Stapel noch in der Diskussion, können die Komponenten, die zum Erstellen einer Lösung "Cloud-Design-Infrastruktur" sollte im Allgemeinen gibt es die folgenden Kategorien aufgeteilt werden soll.


<table>
<thead>
<tr>
<th>Berechnen</th>
<td>Komponenten im Computecluster der Microsoft Azure-Stapel Lösung – in der Regel alle Teile, die in die Vereinfachung von eines einzelnen Servers (CPU, Arbeitsspeicher, eine Hauptplatine, ein Startdatenträger, eine Grafikkarte, ein BIOS usw.) wechseln.</td>
</tr>
<tr class="odd">
<th>Netzwerk</th>
<td>Komponenten, die für die Microsoft Azure-Stapel Lösung Netzwerke Fabric bereitstellen – Netzwerkschnittstellenkarten (NICs) (bei einer veränderlichen Anzahl von Ports und Gesamtstrukturfunktionsebenen), Switches, Hardware und Software-basierte Systeme zum Lastenausgleich und So weiter.</td>
</tr>
<tr class="even">
<th>Storage</th>
<td>Komponenten, die permanente Speichermedien für die Microsoft Azure-Stapel Lösung bereitstellen – physischen Datenträgern (Festplatten und SSDs) HBAs (mit anderen Verbindungen: FC, SAS, ISCSI, SATA usw.), RAID-Adapter, Speicher-Anlagen und so weiter.</td>
</tr>
<tr class="odd">
<th>Sicherheit</th>
<td>TPM-basierte Komponenten erforderlich, um die Plattform Sicherheit und Integrität zu gewährleisten – in der Regel von Komponenten wie BitLocker, Microsoft-Assurance verwendet und VMs geschützt.</td>
</tr>
<tr class="even">
<th>Sonderzeichen</th>
<td>Komponenten, die erforderlich sind, um spezielle Szenarien für eine Lösung Microsoft Azure-Stapel wie Skype für Unternehmen zu ermöglichen.</td>
</tr>
</table>


Die Ziel dieses Features besteht darin, produktanforderungen für Partner zu definieren, die basierend auf dem Microsoft Azure-Stapel private Cloudlösungen zu erstellen.

OEMs und Systemintegratoren Lösung, die Microsoft Azure-Stapel Lösungen erstellen müssen Komponenten integrieren, die das zugehörige Microsoft Azure-Stapel-Logo Anforderungen Tests, einschließlich des Private Cloud Simulation (PCS) Tests bestanden haben. Die vollständig zusammengefassten Lösungen müssen die minimale und maximale Skalierung unterstützten Konfigurationen PCS Tests übergeben.


### <a name="systemsolutionsazurestackcloudstress"></a>System.Solutions.AzureStack.CloudStress

*Microsoft Azure-Stapel Lösungen müssen diese Spezifikation in den Mindest- und Konfigurationen entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen.

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud.

Um diese Spezifikation entsprechen, muss die Lösung den PCS Testlauf mit den "Azure-Stapel - Lösungen' übergeben Profil in die **minimale** und **maximale** Konfigurationen. Beispielsweise wenn eine Lösung mit einer 4-Knoten niedrigste Konfiguration und einer höchste 16-Knoten Konfiguration, PCS geliefert wird Azure-Stapel erforderlich auf 4-Knoten und 16-Knoten-Konfigurationen, jedoch nicht für ist fortgeschrittene alle Konfigurationen (auch bekannt als 8 oder 12-Knoten)


### <a name="systemsolutionsazurestacknano"></a>System.Solutions.AzureStack.Nano

*Anforderungen für Nano Server Core unterstützen Microsoft Azure-Stapel-Lösungen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Systeme (Virtualisierungshosts ALIAS), die in einer Microsoft Azure-Stapel Lösung sollten Windows Server Nano als Host OS ausführen.

Daher alle Treiber, Software-Dienstprogramme, Diagnosetools, Patchen und Firmware aktualisieren Mechanismen soll, führen Sie auf der Host sollte das Device.DevFund.Server.Nano Feature und dessen bestimmte Anforderungen unterstützen.

Neben den oben genannten für vollständige Microsoft Azure-Stapel-Lösungen gelten die folgenden Anforderungen:


<ol style="list-style-type: decimal">
<li>
<p><strong>In Nano Server ausgeführt werden</strong></p>
<p>Alle Systeme müssen möglicherweise installieren, konfigurierbaren, gewartet werden und in Windows Server Nano funktionsfähig sein.</p>
</li>

<li>
<p><strong>Diagnose</strong></p>
<p>Alle Diagnosetools und Dienstprogramme zur Verwendung in einer Microsoft Azure-Stapel-Lösung müssen Management mithilfe einer der folgenden Methoden unterstützt:</p>
<ul>
<li>
<p>Verwenden von Remote Windows PowerShell oder Windows-Verwaltungsinstrumentation (WMI).</p>
</li>
<li>
<p>Ein Befehlszeilentool verwenden, das ein Administrator auf dem Nano Server ausgeführt kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH.</p>
</li>
</ul>
<p>Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.</p>
<p>Zusätzlich zu den obigen Systemen muss mit Windows Server Nano unterstützen Nano Server Recovery Console-Funktionen überprüfen Sie, dass alle entsprechenden Features in Nano Server verwendete Treiber ordnungsgemäß arbeiten.</p>
</li>

<li>
<p><strong>Bereitstellung</strong></p>
<p>Alle Treiber für die Verwendung in einer Microsoft Azure-Stapel-Lösung müssen die folgenden bereitstellungsanforderungen erfüllen:</p>
<ul>
<li>
<p>Treiber müssen für die Verwendung mit Windows Server 2016 zertifiziert und haben das Windows Server 2016-logo</p>
</li>
<li>
<p>Treiber müssen Device.DevFund.Server.Nano unterstützen.</p>
</li>
<li>
<p>Treiber müssen nicht als eine MSI-DATEI gepackt werden. Alle Treiberdateien (beispielsweise inf und sys-Dateien) müssen als eine Reihe von Dateien verfügbar sein, die in einen Ordner für die Verwendung mit Deployment Image Servicing and Management (DISM) kopieren.</p>
</li>
<li>
<p>Treiber installiert werden müssen mithilfe von DISM offline.</p>
</li>
</ul>
<p>Alle Tools, Dienstprogramme oder Agents auf Nano Server installiert sein müssen als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt werden.</p>
</li>

<li>
<p><strong>Patch und Update (engl.)</strong></p>
<p>Alle Patches und Updates muss offline installieren können (als Teil des Image-Erstellung) oder online.</p>
</li>

<li>
<p><strong>Überwachung und Telemetrie</strong></p>
<p>Microsoft Azure Stapel muss alle Überwachung ohne Agents sein und Agents auf den Hosts nicht zulässig. Daher müssen alle monitoring Tools, Dienstprogramme und Agents Installation durch die folgende Methode unterstützt:</p>
<ul>
<li>
<p>Remote-Installation von Windows PowerShell oder WMI</p>
</li>
</ul>
<p>Siehe auch: Goldbarsch Anforderung in System.Server.Manageability.Redfish</p>
</li>

<li>
<p><strong>Firmware-Aktualisierung</strong></p>
<p>Alle Firmware Update Tools und Dienstprogramme zur Verwendung in einer Microsoft Azure-Stapel Lösung müssen Installation mithilfe einer der folgenden Methoden unterstützt:</p>
<ul>
<li>
<p>Remote-Installation von Windows PowerShell oder WMI</p>
</li>
<li>
<p>Lokale Installation von ein Befehlszeilentool, das ein Administrator auf Nano Server ausführen kann, indem es eine Verbindung zu einer Instanz Nano Server über eine remote Windows PowerShell-Sitzung oder SSH</p>
</li>
</ul>
<p>Wenn das Tool oder Dienstprogramm auf Nano Server lokal ausgeführt wird, müssen sie als Windows-Server-Anwendung (WSA) Installer-Paket zur Verfügung gestellt.</p>
</li>
</ol>



### <a name="systemsolutionsazurestacknetwork"></a>System.Solutions.AzureStack.Network

*Kernnetzwerks Anforderungen für die Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Azure-Stapel-Lösungen müssen Netzwerkkomponenten verwenden, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente | Unterstützung von Azure-Stapel |
|-----------|-----------------------------|
| LAN (Card, NIC) | Device.Network.LAN.AzureStack |
| Switch | Device.Network.Switch.AzureStack |


**Drittanbieter Hyper-V-Switch-Erweiterungen**

Drittanbieter extensible wechselt für Hyper-V, Unterstützung erfassen, filtern oder Weiterleitung des Datenverkehrs im Netzwerk werden in Microsoft Azure-Stapel Lösungen nicht unterstützt.


### <a name="systemsolutionsazurestackserver"></a>System.Solutions.AzureStack.Server

*Server-Systemanforderungen für Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Azure Stack Lösungen müssen die Server-Systeme verwenden, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente | Unterstützung von Azure-Stapel |
|-----------|-----------------------------|
| Serverobjektmodell    | System.Server.AzureStack |


### <a name="systemsolutionsazurestackstorage"></a>System.Solutions.AzureStack.Storage

*Core-speicheranforderungen für Microsoft Azure-Stapel.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Azure-Stapel-Lösungen müssen Speicherkomponenten verwenden, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente | Unterstützung von Azure-Stapel |
|-----------|-----------------------------|
| Controller (HBA) | Device.Storage.Controller.AzureStack |
| Anlage        | Device.Storage.Enclosure.AzureStack |
| Laufwerk            | Device.Storage.Hd.AzureStack |


**Speicher-Lösungen basierend auf 'Speicher Leerzeichen direkte'**

Microsoft Azure-Stapel-speicheranforderungen für die anfängliche Produktversion sind identisch mit der hardwareanforderungen für **Speicher Leerzeichen direkte**. Zukünftige Microsoft Azure-Stapel Iterationen möglicherweise zusätzliche Speichertypen unterstützt.


## <a name="systemsolutionsstoragespacesdirect"></a>System.Solutions.StorageSpacesDirect

Windows Server 2016 führt 'Speicher Leerzeichen direkte', wodurch Erstellen von Systemen mit hoher Verfügbarkeit (HA) Speicher mit lokalen Speicher. Dies ist vereinfacht die Bereitstellung und Verwaltung von SDS Systeme und Verwendung der neuen Klassen von Festplatten wie SATA und NVMe Datenträger-Geräte, die mit gruppierten Speicherplätze freigegebene Datenträger zuvor nicht möglich waren auch entsperrt einen wichtigen Schritt vorwärts Software definiert Microsoft Windows Server-Speicher (SDS).

OEMs und Systemintegratoren Lösung, die Speicherung Leerzeichen direkte Lösungen erstellen müssen Komponenten integrieren, die zugeordneten Microsoft Azure-Stapel Logo Anforderung Versuche, einschließlich des Private Cloud Simulation (PCS) Tests bestanden haben.

Die folgenden Funktionen werden von Storage Leerzeichen direkte Lösungen in Windows Server 2016 nicht unterstützt:

-   RAID-Controller (RAID oder JBOD-Modus) werden nicht unterstützt.
-   FC/iSCSI verbunden Geräte werden nicht unterstützt.
-   MPIO oder Datenträger über mehrere Pfade physisch verbinden wird nicht unterstützt.


### <a name="systemsolutionsstoragespacesdirectbvtandstress"></a>System.Solutions.StorageSpacesDirect.BVTandStress

*Speicher Leerzeichen direkte Lösungen müssen diese Spezifikation in den Mindest- und Konfigurationen entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Diese Anforderung beschreibt die Buildüberprüfungstests und Stress Szenarien, die Speicher Leerzeichen direkte Lösungen in einem Szenario nicht virtualisierten unterstützen.

Des Buildüberprüfungstests werden zwei Arten von Tests ausgeführt: 

 - Verschieben der Cluster Shared Volume (CSV) auf der Basis Speicher Leerzeichen direkte zwischen Knoten beim Ausführen des zufällige schreiben Sie e/a und sicherstellen Sie, dass die e/a ist ohne Unterbrechung und CSV wird kein Fehler auf. 

 - Deaktivierung eines Knotens durch Beenden der Clusterdienst, Cluster-Dienst zu beenden Knoten, ordnungsgemäßes Computer neu starten und nicht ordnungsgemäß Computer neu starten (mit jeder Aktion für einen zufällig ausgewählten Knoten). Test auch führt zufällige Schreibvorgänge e/a Zielgruppenadressierung die entsprechende CSV während Knotenfehler und stellt sicher, dass die e/a nicht fehlschlägt.

Die Belastungstests Knoten wiederholte und zufällige Fehler verursachen (nach Beenden oder Cluster-Dienst zu beenden), potenziell verursacht mehrere Knoten fehlschlagen, wenn von der angegebenen Konfiguration vorgenommen. Während der mit Knotenfehlern führt der Test mehrere e/a-Streams aus mehreren Knoten Zielgruppenadressierung die entsprechenden Cluster Shared Lautstärke (mit jedem Stream sequenzielle/zufälliger Lese-/Schreibzugriff mit gelesenen Daten-Überprüfung ausführen). Der Test kann für eine vom Benutzer angegebener Zeit, bis auf 24 Stunden ausgeführt.

Um diese Spezifikation entsprechen, muss die Lösung die **minimale** und **maximale** Konfigurationen diese Tests übergeben. Beispielsweise wenn ein Speicher Leerzeichen direkte Lösung im Lieferumfang von einer 4-Knoten niedrigste Konfiguration und einer höchste 16-Knoten Konfiguration, diese Tests erforderlich auf 4-Knoten und 16-Knoten-Konfigurationen, jedoch nicht auf sind bis Fortgeschrittene alle Konfigurationen (auch bekannt als 8 oder 12-Knoten).


### <a name="systemsolutionsstoragespacesdirectcloudstress"></a>System.Solutions.StorageSpacesDirect.CloudStress

*Speicher Leerzeichen direkte Lösungen müssen diese Spezifikation in den Mindest- und Konfigurationen entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Private Cloudlösungen umfassen eng integrierte Software und Hardwarekomponenten für Zweigstellenstandorte mit hoher Leistung bieten. Probleme bei der in den Komponenten (Software, Hardware, Treibern, Firmware usw.) können gefährden die Lösung und beeinträchtigt alle Versprechen bezüglich Service Level Agreement (SLA) für die private Cloud vorgenommen.

Viele dieser Probleme sind nur unter eine hohe Stress, private Cloud Simulation verfügbar gemacht. Private Cloud Simulator (PCS) können Sie zum Überprüfen der Komponente in einem cloudszenario mit und Probleme zu identifizieren. Es simuliert eine live Datacenter/Private Cloud durch VM-Arbeitslasten zu erstellen, Planen von administrative Vorgänge (Lastenausgleich, Wartung von Software/Hardware) und Einfügen von Fehlern (ungeplante Hard-und Software mit Fehlern) auf die private Cloud.

Die Lösung muss zur Einhaltung dieser Spezifikation den mit der 'Speicher Leerzeichen Direct - Lösungen"Testlauf PCS übergeben Profil in die **minimale** und **maximale** Konfigurationen. Beispielsweise bei einer Speicher Leerzeichen einer 4-Knoten niedrigste Konfiguration und einer höchste 16-Knoten Konfiguration, PCS Lösung Lieferumfang erforderlich auf 4-Knoten und 16-Knoten-Konfigurationen, jedoch nicht auf direktverbindung bis Fortgeschrittene alle Konfigurationen (auch bekannt als 8 oder 12-Knoten).


### <a name="systemsolutionsstoragespacesdirectnano"></a>System.Solutions.StorageSpacesDirect.Nano

*Anforderungen für Nano Server Core Unterstützung von Lösungen basierend auf Speicher Leerzeichen direkte.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Nano Support-Anforderungen für Speicher Leerzeichen direkte Lösungen sind identisch mit denen für die erste Version von Microsoft Azure-Stapel.
Speicher Leerzeichen direkte Lösungen müssen daher die nachfolgenden Anforderung unterstützen.

| Bereich                        | Azure-Stapel-Anforderung |
|-----------------------------|-------------------------|
| Windows Server Nano-Unterstützung | System.Solutions.Azurestack.Nano |



### <a name="systemsolutionsstoragespacesdirectnetwork"></a>System.Solutions.StorageSpacesDirect.Network

*Core netzwerkanforderungen für Lösungen basierend auf 'Speicher Leerzeichen direkte'*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Gerät-Anforderungen für Speicher Leerzeichen direkte Lösungen sind identisch mit denen für die erste Version von Microsoft Azure-Stapel. Daher müssen Speicher Leerzeichen direkte Lösungen Netzwerkkomponenten verwenden, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente      | Unterstützung von Azure-Stapel |
|----------------|-----------------------------|
| LAN (Card, NIC) | Device.Network.LAN.AzureStack |
| Switch         | Device.Network.Switch.AzureStack |


Für optimale Leistung und Dichte werden RDMA-fähig Netzwerkschnittstellenkarten (NICs) empfohlen. Das verwendete Protokoll RDMA muss einer der folgenden sein: iWARP oder RoCE (RoCE Version 1 oder RoCE Version 2). Routingfähige RDMA-Protokolle werden bevorzugt, sobald Sie verfügbar sind (z. B. iWARP oder RoCEv2) für größte Flexibilität zur Unterstützung von skalierbaren Lösungen. Wenn RDMA-fähig Netzwerkschnittstellenkarten (NICs) verwendet werden, müssen die an die Netzwerkkarten angeschlossen Netzwerkswitches die relevanten Funktionen zur Unterstützung des RDMA-Protokolls (z. B., aber nicht beschränkt, um die Unterstützung von Protokollen zur Unterstützung der RoCE Data Center Bridging wechseln) angeben.


### <a name="systemsolutionsstoragespacesdirectserver"></a>System.Solutions.StorageSpacesDirect.Server

*Server-Systemanforderungen für Speicher Leerzeichen direkte.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Speicher Leerzeichen direkte Lösungen Server-Systeme verwenden müssen, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente | Unterstützung von Azure-Stapel |
|-----------|-----------------------------|
| Serverobjektmodell    | System.Server.AzureStack |


Serverkonfiguration sollte homogene sein. Windows Server 2016 unterstützt mindestens 3 und bis zu 16 Server in einer zentralen Lösung. Windows Server 2016 unterstützt maximal 20 Datenträger Geräten pro Server.


### <a name="systemsolutionsstoragespacesdirectstorage"></a>System.Solutions.StorageSpacesDirect.Storage

*Core Speicherbedarf für Lösungen basierend auf 'Speicher Leerzeichen direkte'*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>


**Beschreibung**

Gerät-Anforderungen für Speicher Leerzeichen direkte Lösungen sind identisch mit denen für die erste Version von Microsoft Azure-Stapel. Daher müssen Speicher Leerzeichen direkte Lösungen Speicherkomponenten verwenden, die:

1.  Sind für Windows Server 2016 zertifiziert

2.  Azure-Stapel Supportfunktionen und somit die entsprechende Gerät Anforderungen entsprechen für dieses feature

Die Feature-Support-Tabelle ist als unter:

| Komponente        | Unterstützung von Azure-Stapel |
|------------------|-----------------------------|
| Controller (HBA) | Device.Storage.Controller.AzureStack |
| Anlage        | Device.Storage.Enclosure.AzureStack |
| Laufwerk            | Device.Storage.Hd.AzureStack |

