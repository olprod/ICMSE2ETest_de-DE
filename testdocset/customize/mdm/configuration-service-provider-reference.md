---
title: Konfiguration Dienstverweis-Anbieter
description: "Eine Schnittstelle zum Lesen, festlegen, ändern oder löschen Konfigurationseinstellungen auf dem Gerät ist ein Konfiguration-Dienstanbieter (CSP)."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 71823658-951f-4163-9c40-c4d4adceaaec
ms.openlocfilehash: 04bea68be2c71dd928d378f71ada01affdb1a9cd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configuration-service-provider-reference"></a>Konfiguration Dienstverweis-Anbieter


Ein Konfigurationsdienstanbieter (CSP) ist eine Schnittstelle zum Lesen, festlegen, ändern oder Löschen von Konfigurationseinstellungen auf dem Gerät. Diese Einstellungen ordnen Sie Registrierungsschlüssel oder Dateien. Einige Konfigurationsdienstanbieter unterstützen das WAP-Format, einige Support-SyncML und einige Support beide. SyncML ist nur verwendeten Over – the-Air für Open Allianz Verwaltung mobiler Geräte (OMA DM), während WAP kann verwendeten Over – the-Air für OMA-Clientbereitstellung oder im Bild Telefon als .provxml-Datei, die während des Startvorgangs installiert wird enthalten sein.

Informationen zu den Bridge WMI-Anbieterklassen, die diese Kryptografiedienstanbieter zugeordnet sind, finden Sie unter [MDM Bridge WMI-Anbieter](https://msdn.microsoft.com/library/windows/hardware/dn905224). Die Liste der neuen Kryptografiedienstanbieter in Windows 10 hinzugefügt finden Sie unter [neue Kryptografiedienstanbieter in Windows 10, Version 1511 hinzugefügt](#newcsps). Finden Sie in der [Liste der Kryptografiedienstanbieter in Windows Hologramm unterstützt](#hololens) und die [Liste der Kryptografiedienstanbieter in Microsoft Surface Hub unterstützt](#surfacehubcspsupport) Weitere Informationen.

In der folgenden Tabelle zeigen die Konfiguration-Dienstanbieter in Windows 10 unterstützt.  

> **Wichtige**  Um die Tabelle horizontal zu navigieren, klicken Sie auf die Tabelle und verwenden Sie die linken und rechten Scroll-Taste auf der Tastatur oder mithilfe der Bildlaufleiste am unteren Rand der Tabelle.

<table>
<colgroup>
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
</colgroup>
<thead>
<tr class="header">
<th>Konfiguration-Dienstanbieter</th>
<th>Unterstützt in Windows 10 Pro</th>
<th>Unterstützt in Windows 10 Enterprise</th>
<th>In Windows 10 Education unterstützt</th>
<th>Unterstützt in Windows 10-Startseite</th>
<th>Unterstützt in 10 Windows Mobile</th>
<th>Unterstützt in 10 Windows Mobile Enterprise</th>
<th>Unterstützt in Windows 10 IoT Core (IoT Core)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>[ActiveSync CSP](activesync-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[AllJoynManagement CSP](alljoynmanagement-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[ANWENDUNG CSP](application-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[AppLocker CSP](applocker-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[AssignedAccess CSP](assignedaccess-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[BOOTSTRAP CSP](bootstrap-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[BrowserFavorite CSP](browserfavorite-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CellularSettings CSP](cellularsettings-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CertificateStore CSP](certificatestore-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[ClientCertificateInstall CSP](clientcertificateinstall-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[CM_CellularEntries CSP](cm-cellularentries-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CM_ProxyEntries CSP](cm-proxyentries-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CMPolicy CSP](cmpolicy-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CMPolicyEnterprise CSP](cmpolicyenterprise-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CustomDeviceUI CSP](customdeviceui-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[Defender CSP](defender-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DevDetail CSP](devdetail-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[DeviceInstanceService CSP](deviceinstanceservice-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DeviceLock CSP](devicelock-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[DeviceManageability CSP](devicemanageability-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DeviceStatus CSP](devicestatus-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[DevInfo CSP](devinfo-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[DiagnosticLog CSP](diagnosticlog-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[DMAcc CSP](dmacc-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[DMClient CSP](dmclient-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[EMAIL2 CSP](email2-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseAPN CSP](enterpriseapn-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />nur Version 1507</td>
<td><img src="images/checkmark.png" alt="check mark" />nur Version 1507</td>
<td><img src="images/checkmark.png" alt="check mark" />nur Version 1507</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseAppManagement CSP](enterpriseappmanagement-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseAssignedAccess CSP](enterpriseassignedaccess-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseDataProtection CSP](enterprisedataprotection-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseDesktopAppManagement CSP](enterprisedesktopappmanagement-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseExt CSP](enterpriseext-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseExtFileSystem CSP](enterpriseextfilessystem-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[FileSystem CSP](filesystem-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[HealthAttestation CSP](healthattestation-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[HotSpot CSP](hotspot-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[Maps CSP](maps-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[NAP-CSP](nap-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[NAPDEF CSP](napdef-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[NodeCache CSP](nodecache-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[PassportForWork CSP](passportforwork-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[PolicyManager CSP](policymanager-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[Provisioning CSP](provisioning-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>(Nur Bereitstellung)</p></td>
</tr>
<tr class="even">
<td>[PROXY-CSP](proxy-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[PXLOGICAL CSP](pxlogical-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[Neustart CSP](reboot-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[Registrierung CSP](registry-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[RemoteFind CSP](remotefind-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RemoteLock](remotelock-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[RemoteRing CSP](remotering-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RemoteWipe CSP](remotewipe-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[Reporting CSP](reporting-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RootCATrustedCertificates CSP](rootcacertificates-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[SecureAssessment CSP](secureassessment-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[SecurityPolicy CSP](securitypolicy-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[SharedPC CSP](sharedpc-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[Speicher CSP](storage-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[SUPL CSP](supl-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[SurfaceHub](surfacehub-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>[UnifiedWriteFilter CSP](unifiedwritefilter-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[Update CSP](update-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[VPN-CSP](vpn-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[VPNv2 CSP](vpnv2-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[W4 ANWENDUNG CSP](w4-application-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[W7 ANWENDUNG CSP](w7-application-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[Wi-Fi CSP](wifi-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[Win32AppInventory CSP](win32appinventory-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[WindowsAdvancedThreatProtection CSP](windowsadvancedthreatprotection-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[WindowsLicensing CSP](windowslicensing-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[WindowsSecurityAuditing CSP](windowssecurityauditing-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idhololensacsps-supported-in-windows-holographic"></a><a href="" id="hololens"></a>Unterstützt in Windows Hologramm Kryptografiedienstanbieter


In der folgenden Liste wird die Konfiguration-Dienstanbieter in Windows Hologramm Editionen unterstützt.

| Konfiguration-Dienstanbieter                                                                        | Windows-Hologramm edition      | Windows Hologramm Enterprise edition |
|-------------------------------------------------------------------------------------------------------|-------------------------------------|-------------------------------------------|
| [Anwendung csp](application-csp.md)                                     | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [AppLocker csp](applocker-csp.md)                                         | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [CertificateStore csp](certificatestore-csp.md)                           | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [Clientcertificateinstall csp](clientcertificateinstall-csp.md)           | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Devdetail csp](devdetail-csp.md)                                         | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [Devicestatus csp](devicestatus-csp.md)                                                              | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Devinfo csp](devinfo-csp.md)                                             | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [Diagnosticlog csp](diagnosticlog-csp.md)                                 | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Dmacc csp](dmacc-csp.md)                                                 | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [DMClient csp](dmclient-csp.md)                                           | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [Enterprisemodernappmanagement csp](enterprisemodernappmanagement-csp.md) | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Nodecache csp](nodecache-csp.md)                                         | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |
| [Richtlinie csp](policy-configuration-service-provider.md)                                               | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Rootcatrustedcertificates csp](rootcacertificates-csp.md)                | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Update csp](update-csp.md)                                               | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [vpnv2 csp](vpnv2-csp.md)                                                 | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Wi-Fi csp](wifi-csp.md)                                                  | ![Kreuz](images/crossmark.png) | ![Häkchen](images/checkmark.png)       |
| [Windowslicensing csp](windowslicensing-csp.md)                           | ![Häkchen](images/checkmark.png) | ![Häkchen](images/checkmark.png)       |


## <a name="a-href-idnewcspsanew-csps-added-in-windows-10-version-1511"></a><a href="" id="newcsps"></a>Neue Kryptografiedienstanbieter in Windows 10, Version 1511 hinzugefügt

-   [AllJoynManagement CSP](alljoynmanagement-csp.md)
-   [Maps CSP](maps-csp.md)
-   [Reporting CSP](reporting-csp.md)
-   [SurfaceHub CSP](surfacehub-csp.md)
-   [WindowsSecurityAuditing CSP](windowssecurityauditing-csp.md)

## <a name="a-href-idsurfacehubcspsupportacsps-supported-in-microsoft-surface-hub"></a><a href="" id="surfacehubcspsupport"></a>Unterstützt in Microsoft Surface Hub Kryptografiedienstanbieter

-   [ANWENDUNG CSP](application-csp.md)
-   [CertificateStore CSP](certificatestore-csp.md)
-   [ClientCertificateInstall CSP](clientcertificateinstall-csp.md)
-   [Defender CSP](defender-csp.md)
-   [DevDetail CSP](devdetail-csp.md)
-   [DeviceManageability CSP](devicemanageability-csp.md)
-   [DeviceStatus CSP](devicestatus-csp.md)
-   [DevInfo CSP](devinfo-csp.md)
-   [DiagnosticLog CSP](diagnosticlog-csp.md)
-   [DMAcc CSP](dmacc-csp.md)
-   [DMClient CSP](dmclient-csp.md)
-   [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md)
-   [HealthAttestation CSP](healthattestation-csp.md)
-   [NodeCache CSP](nodecache-csp.md)
-   [PassportForWork CSP](passportforwork-csp.md)
-   [Richtlinie CSP](policy-configuration-service-provider.md)
-   [Neustart CSP](reboot-csp.md)
-   [RemoteWipe CSP](remotewipe-csp.md)
-   [Reporting CSP](reporting-csp.md)
-   [RootCATrustedCertificates CSP](rootcacertificates-csp.md)
-   [SurfaceHub CSP](surfacehub-csp.md)
-   [WindowsAdvancedThreatProtection CSP](windowsadvancedthreatprotection-csp.md)




