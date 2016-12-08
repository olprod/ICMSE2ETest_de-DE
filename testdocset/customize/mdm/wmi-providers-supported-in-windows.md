---
title: "WMI-Anbieter in Windows 10 unterstützt"
description: "WMI-Anbieter in Windows 10 unterstützt"
MS-HAID:
- p\_phdevicemgmt.wmi\_providers\_supported\_in\_windows\_10\_technical\_preview
- p\_phDeviceMgmt.wmi\_providers\_supported\_in\_windows
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7D533044-AAD7-4B8F-B71B-9D52C15A168A
ms.openlocfilehash: 1d96ae4dec3e925f5d79cfc95aa88e0ac26ac60e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wmi-providers-supported-in-windows-10"></a>WMI-Anbieter in Windows 10 unterstützt

Windows Management Infrastructure (Windows Management Instrumentation, WMI)-Anbieter (und die Klassen, die sie unterstützen) dienen zum Verwalten von Einstellungen und Anwendungen auf Geräten, die das Mobile Gerät Management (MDM) Dienst abonnieren. In den folgenden Unterabschnitten zeigt eine Liste WMI MDM Klassen, die in Windows 10 unterstützt werden.

> **Hinweis**  Applications Installation mit WMI-Klassen werden nicht entfernt, wenn das Konto MDM vom Gerät entfernt wird.

 

Die untergeordnete Knotennamen, der das Ergebnis einer Abfrage WMI durch einen Schrägstrich (/) voneinander getrennt sind, und nicht URI Escapezeichen. Es folgt eine Beispielabfrage.

Rufen Sie die Liste der Netzwerkadapter auf dem Gerät.

``` syntax
<Get>
   <Target>
      <LocURI>./cimV2/Win32_NetworkAdapter</LocURI>
   </Target>
</Get>
```

Ergebnis

``` syntax
<Item>
   <Source>
      <LocURI>./cimV2/Win32_NetworkAdapter</LocURI>
   </Source>
   <Meta>
      <Format xmlns="syncml:metinf">node</Format>
   </Meta>
      <Data>Win32_NetworkAdapter.DeviceID="0"/Win32_NetworkAdapter.DeviceID="1"/Win32_NetworkAdapter.DeviceID="2"</Data>
</Item>
```

## <a name="mdm-bridge-wmi-classes"></a>MDM Bridge WMI-Klassen


Links zu diesen Klassen finden Sie unter [**MDM Bridge WMI-Anbieter**](https://msdn.microsoft.com/library/windows/hardware/dn905224).

## <a name="mdm-wmi-classes"></a>MDM WMI-Klassen

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Klasse</th>
<th>Test für Desktop in Windows 10 abgeschlossen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>[<strong>MDM_AppInstallJob</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610368)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="even">
<td>[<strong>MDM_Application</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610369)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_ApplicationFramework</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610370)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="even">
<td>[<strong>MDM_ApplicationSetting</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610382)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_BrowserSecurityZones</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610383)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MDM_BrowserSettings</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610384)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_Certificate</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610385)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MDM_CertificateEnrollment</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610386)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_Client</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610387)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="even">
<td>[<strong>MDM_ConfigSetting</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610388)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_DeviceRegistrationInfo</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610389)</td>
<td></td>
</tr>
<tr class="even">
<td>[<strong>MDM_EASPolicy</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610390)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_MgMtAuthority</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610391)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td><strong>MDM_MsiApplication</strong></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>MDM_MsiInstallJob</strong></td>
<td></td>
</tr>
<tr class="even">
<td>[<strong>MDM_RemoteApplication</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610371)</td>
<td><p>Test nicht gestartet.</p></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_RemoteAppUseCookie</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610372)</td>
<td><p>Test nicht gestartet.</p></td>
</tr>
<tr class="even">
<td>[<strong>MDM_Restrictions</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610392)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_RestrictionsUser</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610393)</td>
<td><p>Test nicht gestartet.</p></td>
</tr>
<tr class="even">
<td>[<strong>MDM_SecurityStatus</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610394)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_SideLoader</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610395)</td>
<td></td>
</tr>
<tr class="even">
<td>[<strong>MDM_SecurityStatusUser</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn920104)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_Updates</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn920105)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MDM_VpnApplicationTrigger</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610396)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td><strong>MDM_VpnConnection</strong></td>
<td></td>
</tr>
<tr class="even">
<td>[<strong>MDM_WebApplication</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610373)</td>
<td><p>Derzeit testen.</p></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_WirelessProfile</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610397)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MDM_WirelesssProfileXML</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610398)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MDM_WNSChannel</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610399)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MDM_WNSConfiguration</strong>] (https://msdn.microsoft.com/library/windows/hardware/dn610400)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[<strong>MSFT_NetFirewallProfile</strong>] (https://msdn.microsoft.com/library/windows/hardware/jj676842)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>MSFT_VpnConnection</strong>] (https://msdn.microsoft.com/library/windows/hardware/jj206647)</td>
<td><img src="images/checkmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[<strong>SoftwareLicensingProduct</strong>] (https://msdn.microsoft.com/library/windows/hardware/cc534596)</td>
<td></td>
</tr>
<tr class="odd">
<td>[<strong>SoftwareLicensingService</strong>] (https://msdn.microsoft.com/library/windows/hardware/cc534597)</td>
<td></td>
</tr>
</tbody>
</table>

 

### <a name="parental-control-wmi-classes"></a>Altersfreigabe WMI-Klassen

| Klasse                                                                    | Test für Desktop in Windows 10 abgeschlossen |
|--------------------------------------------------------------------------|------------------------------------------|
| [**wpcappoverride**](https://msdn.microsoft.com/library/windows/hardware/ms711334)       | ![Kreuz](images/checkmark.png)      |
| [**wpcgameoverride**](https://msdn.microsoft.com/library/windows/hardware/ms711334)      | ![Kreuz](images/checkmark.png)      |
| [**wpcgamessettings**](https://msdn.microsoft.com/library/windows/hardware/ms711334)     | ![Kreuz](images/checkmark.png)      |
| [**wpcrating**](https://msdn.microsoft.com/library/windows/hardware/ms711334)            | ![Kreuz](images/checkmark.png)      |
| [**wpcRatingsDescriptor**](https://msdn.microsoft.com/library/windows/hardware/ms711334) |                                          |
| [**wpcratingssystem**](https://msdn.microsoft.com/library/windows/hardware/ms711334)     | ![Kreuz](images/checkmark.png)      |
| [**wpcsystemsettings**](https://msdn.microsoft.com/library/windows/hardware/ms711334)    | ![Kreuz](images/checkmark.png)      |
| [**wpcurloverride**](https://msdn.microsoft.com/library/windows/hardware/ms711334)       | ![Kreuz](images/checkmark.png)      |
| [**wpcusersettings**](https://msdn.microsoft.com/library/windows/hardware/ms711334)      | ![Kreuz](images/checkmark.png)      |
| [**wpcwebsettings**](https://msdn.microsoft.com/library/windows/hardware/ms711334)       | ![Kreuz](images/checkmark.png)      |

 

### <a name="win32-wmi-classes"></a>Win32-WMI-Klassen

| Klasse                                                                    | Test für Desktop in Windows 10 abgeschlossen |
|--------------------------------------------------------------------------|------------------------------------------|
[**Win32\_1394Controller**](https://msdn.microsoft.com/library/windows/hardware/aa394059) |
[**Win32\_BaseBoard**](https://msdn.microsoft.com/library/windows/hardware/aa394072)      |
[**Win32\_Batterie**](https://msdn.microsoft.com/library/windows/hardware/aa394074)        | ![Kreuz](images/checkmark.png)
[**Win32\_BIOS**](https://msdn.microsoft.com/library/windows/hardware/aa394077)           | ![Kreuz](images/checkmark.png)
[**Win32\_CDROMLaufwerk**](https://msdn.microsoft.com/library/windows/hardware/aa394081)     |
[**Win32\_ComputerSystem**](https://msdn.microsoft.com/library/windows/hardware/aa394102) | ![Kreuz](images/checkmark.png)
[**Win32\_ComputerSystemProduct**](https://msdn.microsoft.com/library/windows/hardware//aa394105) | ![Kreuz](images/checkmark.png)
[**Win32\_CurrentTime**](https://msdn.microsoft.com/library/windows/hardware/aa394114)    | ![Kreuz](images/checkmark.png)
[**Win32\_Desktop**](https://msdn.microsoft.com/library/windows/hardware/aa394121)        |
[**Win32\_DesktopMonitor**](https://msdn.microsoft.com/library/windows/hardware/aa394122) |![Kreuz](images/checkmark.png)
[**Win32\_Laufwerk**](https://msdn.microsoft.com/library/windows/hardware/aa394132)      | ![Kreuz](images/checkmark.png)
[**Win32\_Datenträgerpartition**](https://msdn.microsoft.com/library/windows/hardware/aa394135)  |
[**Win32\_DisplayConfiguration**](https://msdn.microsoft.com/library/windows/hardware/aa394137) | ![Kreuz](images/checkmark.png)
[**Win32\_DMAChannel**](https://msdn.microsoft.com/library/windows/hardware/aa394139)     | 
[**Win32\_DriverVXD**](https://msdn.microsoft.com/library/windows/hardware/aa394141)      |
[**Win32\_EncryptableVolume**](https://msdn.microsoft.com/library/windows/hardware/aa376483) |
[**Win32\_Umgebung**](https://msdn.microsoft.com/library/windows/hardware/aa394143)    |
[**Win32\_IDEController**](https://msdn.microsoft.com/library/windows/hardware/aa394155)  |
[**Win32\_InfraredDevice**](https://msdn.microsoft.com/library/windows/hardware/aa394158) |
[**Win32\_IRQResource**](https://msdn.microsoft.com/library/windows/hardware/aa394164)    |
[**Win32\_Tastatur**](https://msdn.microsoft.com/library/windows/hardware/aa394166)       |
[**Win32\_LoadOrderGroup**](https://msdn.microsoft.com/library/windows/hardware/aa394168) |
[**Win32\_Ortszeit**](https://msdn.microsoft.com/library/windows/hardware/aa394171)      | ![Kreuz](images/checkmark.png)
[**Win32\_LoggedOnUser**](https://msdn.microsoft.com/library/windows/hardware/aa394172)   |
[**Win32\_logischer Datenträger**](https://msdn.microsoft.com/library/windows/hardware/aa394173)    | ![Kreuz](images/checkmark.png)
[**Win32\_MotherboardDevice**](https://msdn.microsoft.com/library/windows/hardware/aa394204) |
[**Win32\_Netzwerkadapter**](https://msdn.microsoft.com/library/windows/hardware/aa394216) | ![Kreuz](images/checkmark.png)
[**Win32\_NetworkAdapterConfiguration**](https://msdn.microsoft.com/library/windows/hardware/aa394217) |
[**Win32\_NetworkClient**](https://msdn.microsoft.com/library/windows/hardware/aa394219)  |
[**Win32\_NetworkLoginProfile**](https://msdn.microsoft.com/library/windows/hardware/aa394221) |
[**Win32\_NetworkProtocol**](https://msdn.microsoft.com/library/windows/hardware/aa394223) |
[**Win32\_NTEventlogFile**](https://msdn.microsoft.com/library/windows/hardware/aa394225)  |
[**Win32\_OperatingSystem**](https://msdn.microsoft.com/library/windows/hardware/aa394239) | ![Kreuz](images/checkmark.png)
[**Win32\_OSRecoveryConfiguration**](https://msdn.microsoft.com/library/windows/hardware/aa394242) |
[**Win32\_PageFileSetting**](https://msdn.microsoft.com/library/windows/hardware/aa394245) |
[**Win32\_ParallelPort**](https://msdn.microsoft.com/library/windows/hardware/aa394247) |
[**Win32\_PCMCIAController**](https://msdn.microsoft.com/library/windows/hardware/aa394251) |
[**Win32\_physikalischen Medien**](https://msdn.microsoft.com/en-us/library/windows/hardware/aa394346)                                   |  
[**Win32\_PhysicalMemory**](https://msdn.microsoft.com/library/windows/hardware/aa394347)   | ![Kreuz](images/checkmark.png)
[**Win32\_PnPDevice**](https://msdn.microsoft.com/library/windows/hardware/aa394352)        |  
[**Win32\_seiner**](https://msdn.microsoft.com/library/windows/hardware/aa394353)        |  
[**Win32\_PointingDevice**](https://msdn.microsoft.com/library/windows/hardware/aa394356)   |
[**Win32\_PortableBattery**](https://msdn.microsoft.com/library/windows/hardware/aa394357)  |
[**Win32\_PortResource**](https://msdn.microsoft.com/library/windows/hardware/aa394359)     |
[**Win32\_POTSModem**](https://msdn.microsoft.com/library/windows/hardware/aa394360)        |
[**Win32\_Drucker**](https://msdn.microsoft.com/library/windows/hardware/aa394363)          |
[**Win32\_PrinterConfiguration**](https://msdn.microsoft.com/library/windows/hardware/aa394364) |
[**Win32\_Prozessor**](https://msdn.microsoft.com/library/windows/hardware/aa394373)        | ![Kreuz](images/checkmark.png)
[**Win32\_QuickFixEngineering**](https://msdn.microsoft.com/library/windows/hardware/aa394391) | ![Kreuz](images/checkmark.png)
[**Win32\_Registrierung**](https://msdn.microsoft.com/library/windows/hardware/aa394394)         |
[**Win32\_SCSIController**](https://msdn.microsoft.com/library/windows/hardware/aa394400)   |
[**Win32\_SerialPort**](https://msdn.microsoft.com/library/windows/hardware/aa394413)       |
[**Win32\_SerialPortConfiguration**](https://msdn.microsoft.com/library/windows/hardware/aa394414) |
[**Win32\_ServerFeature**](https://msdn.microsoft.com/library/windows/hardware/cc280268)    |
[**Win32\_Service**](https://msdn.microsoft.com/library/windows/hardware/aa394418)          | ![Kreuz](images/checkmark.png)
[**Win32\_freigeben**](https://msdn.microsoft.com/library/windows/hardware/aa394435)            | ![Kreuz](images/checkmark.png)
[**Win32\_SoundDevice**](https://msdn.microsoft.com/library/windows/hardware/aa394463)      |
[**Win32\_SystemAccount**](https://msdn.microsoft.com/library/windows/hardware/aa394466)    |
[**Win32\_SystemBIOS**](https://msdn.microsoft.com/library/windows/hardware/aa394467)       | ![Kreuz](images/checkmark.png)
[**Win32\_SystemDriver**](https://msdn.microsoft.com/library/windows/hardware/aa394472)     |
[**Win32\_SystemEnclosure**](https://msdn.microsoft.com/library/windows/hardware/aa394474)  | ![Kreuz](images/checkmark.png)
[**Win32\_TapeDrive**](https://msdn.microsoft.com/library/windows/hardware/aa394491)        |
[**Win32\_TimeZone**](https://msdn.microsoft.com/library/windows/hardware/aa394498)         | ![Kreuz](images/checkmark.png)
[**Win32\_UninterruptiblePowerSupply**](https://msdn.microsoft.com/library/windows/hardware/aa394503) |
[**Win32\_USB-Controller**](https://msdn.microsoft.com/library/windows/hardware/aa394504)    |
[**Win32\_UTCTime**](https://msdn.microsoft.com/library/windows/hardware/aa394510)          | ![Kreuz](images/checkmark.png)
[**Win32\_VideoController**](https://msdn.microsoft.com/library/windows/hardware/aa394505) |
**Win32\_WindowsUpdateAgentVersion**                                                        |
 

## <a name="related-topics"></a>Verwandte Themen


[Referenz zum Konfiguration Service provider](configuration-service-provider-reference.md)

 

 

10/10/2016




