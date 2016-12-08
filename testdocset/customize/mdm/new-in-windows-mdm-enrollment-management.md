---
title: Was ist neu in MDM Registrierung und Verwaltung
description: "Dieses Thema enthält Informationen zu den neue und wichtige Änderungen in Windows 10 Mobilgerät Management (MDM) Registrierung und Verwaltung auf allen Windows-10-Geräten auftreten."
MS-HAID:
- p\_phdevicemgmt.mdm\_enrollment\_and\_management\_overview
- p\_phDeviceMgmt.new\_in\_windows\_mdm\_enrollment\_management
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9C42064F-091C-4901-BC73-9ABE79EE4224
ms.openlocfilehash: 37efb76bbad6f9e2223f4aaa9ee7baf55d93ff1e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-mdm-enrollment-and-management"></a>Was ist neu in MDM Registrierung und Verwaltung


Dieses Thema enthält Informationen zu den neuen und wichtige Änderungen in Windows 10 Mobilgerät Management (MDM) Registrierung und Verwaltung auf allen Windows-10-Geräten auftreten.

Ausführliche Informationen zu Microsoft Mobilgerät Management Protokolle für Windows 10 finden Sie unter [ \[MS-MDM\]: Mobile Gerät Management Protocol](http://go.microsoft.com/fwlink/p/?LinkId=619346) und [ \[MS-MDE2\]: Mobile Device Registrierung Protocol Version 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347).

## <a name="in-this-section"></a>In diesem Abschnitt


-   [Was ist neu in Windows 10, Version 1511](#whatsnew)
-   [Was ist neu in Windows 10, Version 1607](#whatsnew1607)
-   [Wichtige Änderungen und bekannte Probleme](#breaking-changes-and-known-issues)
    -   [GET-Befehl innerhalb einer unteilbare Befehl wird nicht unterstützt.](#getcommand)
    -   [Benachrichtigung Channel-URI, die während des Upgrades von Windows 8.1 für Windows 10 nicht beibehalten](#notification)
    -   [Apps, die Installation mit WMI-Klassen werden nicht entfernt.](#appsnotremoved)
    -   [CDATA SyncML übergeben funktioniert nicht](#cdata)
    -   [Einstellungen für SSL in IIS-Server für SCEP müssen auf "Ignorieren" festgelegt werden](#sslsettings)
    -   [MDM Registrierung auf dem mobilen Gerät schlägt fehl, wenn Datenverkehr über Proxy geht](#enrollmentviaproxy)
    -   [Server initiierte Anmeldung kündigen Fehler](#unenrollment)
    -   [Verursacht Probleme mit Wi-Fi und VPN-Zertifikate](#certissues)
    -   [Versionsinformationen für mobile Geräte](#versioninformation)
    -   [Aktualisieren von Windows Phone 8.1 Geräte mit dem app mithilfe von ApplicationRestriction Richtlinie hat Probleme](#whitelist)
    -   [Abhängig von der Microsoft-Frameworks Apps möglicherweise blockiert werden](#frameworks)
    -   [Mehrere Zertifikate Ursachen in Windows 10 Mobile Wi-Fi-Verbindung installiert haben.](#wificertissue)
    -   [Remote PIN zurücksetzen in Azure Active Directory nicht unterstützt beigetreten mobile Geräten](#remote)
    -   [MDM Client wird sofort mit dem MDM Server Einchecken nachdem Client WNS Channel-URI erneuert.](#renewwns)
    -   [Benutzer Bereitstellungsfehler in Azure Active Directory verbunden Windows 10 PC](#userprovisioning)
    -   [Anforderungen beachten für VPN-Zertifikate auch für die Kerberos-Authentifizierung verwendet](#kerberos)
    -   [Gerät Verwaltungs-Agent für die Drucktaste zurücksetzen ist nicht funktionsfähig.](#pushbuttonreset)
-   [Änderungsprotokoll in MDM-Dokumentation](#change-history-in-mdm-documentation)
-   [Häufig gestellte Fragen](#faq)

## <a name="a-href-idwhatsnewawhats-new-in-windows-10-version-1511"></a><a href="" id="whatsnew"></a>Was ist neu in Windows 10, Version 1511

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Neue Konfiguration-Dienstanbieter hinzugefügt in Windows 10, Version 1511</p></td>
<td style="vertical-align:top"><ul>
<li>[AllJoynManagement CSP](alljoynmanagement-csp.md)</li>
<li>[Maps CSP](maps-csp.md)</li>
<li>[Reporting CSP](reporting-csp.md)</li>
<li>[SurfaceHub CSP](surfacehub-csp.md)</li>
<li>[WindowsSecurityAuditing CSP](windowssecurityauditing-csp.md)</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neue und aktualisierte Richtlinien im Bereich CSP Richtlinie</p></td>
<td style="vertical-align:top"><p>Die folgenden Richtlinien wurden die [Richtlinie CSP](policy-configuration-service-provider.md)hinzugefügt:</p>
<ul>
<li>Konten/DomainNamesForEmailSync</li>
<li>ApplicationManagement/AllowWindowsBridgeForAndroidAppsExecution</li>
<li>Bluetooth/ServicesAllowedList</li>
<li>DataProtection/AllowAzureRMSForEDP</li>
<li>DataProtection/RevokeOnUnenroll</li>
<li>DeviceLock/DevicePasswordExpiration</li>
<li>DeviceLock/DevicePasswordHistory</li>
<li>TextInput/AllowInputPanel</li>
<li>Update/PauseDeferrals</li>
<li>Update/RequireDeferUpdate</li>
<li>Update/RequireUpdateApproval</li>
</ul>
<p>Die folgenden Richtlinien wurden in der Richtlinie CSP aktualisiert:</p>
<ul>
<li>System/AllowLocation</li>
<li>Update/RequireDeferUpgrade</li>
</ul>
<p>Die folgenden Richtlinien sind in der Richtlinie CSP veraltet:</p>
<ul>
<li>TextInput/AllowKoreanExtendedHanja</li>
<li>WiFi/AllowWiFiHotSpotReporting</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Verwaltungstool für den Windows Store for Business</p></td>
<td style="vertical-align:top"><p>Neue Themen. Des Speichers für die Business hat einen neuen Webdienst für das Unternehmen zu erwerben, verwalten und Verteilen von Anwendungen in einer Sammeloperation entwickelt. Sie können verschiedene Funktionen, die für das Unternehmen zum Verwalten des Lebenszyklus von Anwendungen aus Erwerb zu aktualisierende erforderlich sind.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Benutzerdefinierte Kopfzeile für generische Warnung</p></td>
<td style="vertical-align:top"><p>Die MDM-GenericAlert ist ein neuer benutzerdefinierter Header, der einen oder mehrere alert Informationen in der HTTP-Nachrichten an den Server während einer Sitzung OMA DM vom Gerät gesendet gehostet wird. Die generische Benachrichtigung wird gesendet, wenn die Sitzung vom Gerät aufgrund von mindestens einen kritischen oder schwerwiegenden Warnungen ausgelöst wird. Hier ist alert Format:</p>
<code>MDM-GenericAlert: &lt;AlertType1&gt;&lt;AlertType2&gt;</code>
<p>Falls vorhanden, wird die MDM-GenericAlert angezeigt, jeder der ausgehenden MDM Nachricht in der gleichen OMA DM-Sitzung. Weitere Informationen zu generischen Warnungen finden Sie im Abschnitt 8.7 in OMA Gerät Management Protocol, genehmigt, Version 1.2.1 (engl.) auf dieser [Website OMA](http://go.microsoft.com/fwlink/p/?LinkId=267526).</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Benachrichtigung an für langsame Client Antwort</p></td>
<td style="vertical-align:top"><p>Wenn der MDM Server eine Konfiguration Anforderung sendet, manchmal benötigt wird, des alle Informationen zusammen länger als das Zeitlimit für HTTP-Clients, und klicken Sie dann am Ende der Sitzung unerwartet aufgrund eines Timeouts. Standardmäßig werden MDM Client keine Benachrichtigung gesendet, dass eine Anforderung DM aussteht.</p>
<p>Das Timeout zu umgehen, können Sie EnableOmaDmKeepAliveMessage-Einstellung die Sitzung durch Senden von Heartbeat-Nachrichten an den Server zurückgesendet beibehalten werden soll. Dies ist eine SyncML Nachricht mit einem bestimmten Gerät alert-Element im Text senden, bis der Client wieder auf dem Server mit den angeforderten Informationen reagieren kann. Weitere Informationen hierzu finden Sie unter EnableOmaDmKeepAliveMessage Knoten im [DMClient CSP](dmclient-csp.md).</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neuen Knoten in DMClient CSP</p></td>
<td style="vertical-align:top"><p>Einen neuen Knoten EnableOmaDmKeepAliveMessage [DMClient CSP](dmclient-csp.md) hinzugefügt, und aktualisiert die ManagementServerAddress, um darauf hinzuweisen, dass sie eine Liste mit URLs enthalten kann.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Neuen Knoten im EnterpriseModernAppManagement CSP</p></td>
<td style="vertical-align:top"><p>Die folgenden Knoten, [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md)hinzugefügt wurde:</p>
<ul>
<li>AppManagement/GetInventoryQuery</li>
<li>AppManagement/GetInventoryResults</li>
<li>... /<em>PackageFamilyName</em>/AppSettingPolicy/<em>SettingValue</em></li>
<li>AppLicenses/StoreLicenses-/<em>LicenseID</em>/LicenseCategory</li>
<li><em>AppLicenses/StoreLicenses/LicenseID</em>/LicenseUsage</li>
<li><em>AppLicenses/StoreLicenses/LicenseID</em>/RequesterID</li>
<li><em>AppLicenses/StoreLicenses/LicenseID</em>/GetLicenseFromStore</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neue Knoten in EnterpriseExt CSP</p></td>
<td style="vertical-align:top"><p>Die folgenden Knoten, der [EnterpriseExt CSP](enterpriseext-csp.md)hinzugefügt wurde:</p>
<ul>
<li>DeviceCustomData (CustomID, CustomeString)</li>
<li>Helligkeit (Standard, MaxAuto)</li>
<li>LedAlertNotification (Zustand, Intensität, Zeitraum, DutyCycle, Cyclecount)</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Neuen Knoten in EnterpriseExtFileSystem CSP</p></td>
<td style="vertical-align:top"><p>OemProfile-Knoten auf [EnterpriseExtFileSystem Kryptografiedienstanbieter](enterpriseextfilessystem-csp.md)hinzugefügt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neue Knoten in PassportForWork CSP</p></td>
<td style="vertical-align:top"><p>Die folgenden Knoten hinzugefügt [PassportForWork CSP](passportforwork-csp.md):</p>
<ul>
<li>TenantId/Richtlinien/PINComplexity/Verlauf</li>
<li>TenantId/Richtlinien/PINComplexity/Ablauf</li>
<li>TenantId/Richtlinien/Remote/UseRemotePassport (nur für ./Device/Vendor/MSFT)</li>
<li>Biometrik/UseBiometrics (nur für ./Device/Vendor/MSFT)</li>
<li>Biometrik/FacialFeaturesUseEnhancedAntiSpoofing (nur für ./Device/Vendor/MSFT)</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Aktualisierte EnterpriseAssignedAccess CSP</p></td>
<td style="vertical-align:top"><p>Hier sind die Änderungen an der [EnterpriseAssignedAccess CSP](enterpriseassignedaccess-csp.md)aus:</p>
<ul>
<li>In AssignedAccessXML hinzugefügt neue seiteneinstellungen und Einstellungen für schnelles Aktion Knoten.</li>
<li>In AssignedAccessXML hinzugefügt Knoten ein Beispiel dazu, wie Sie für Pin-Clientanwendungen in mehreren app-Paketen mithilfe der AUMID.</li>
<li>Das Thema [EnterpriseAssignedAccess XSD-](enterpriseassignedaccess-xsd.md) aktualisiert.</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neue Knoten im DevDetail CSP</p></td>
<td style="vertical-align:top"><p>Hier sind die Änderungen an der [DevDetail Kryptografiedienstanbieter](devdetail-csp.md):</p>
<ul>
<li>TotalStore und TotalRAM Einstellungen hinzugefügt.</li>
<li>Unterstützung für den Befehl "ersetzen" für die Einstellung DeviceName hinzugefügt.</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Behandeln von großer Objekte</p></td>
<td style="vertical-align:top"><p>Unterstützung für den Client zum Behandeln von Hochladen großer Objekte auf dem Server hinzugefügt.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idwhatsnew1607awhats-new-in-windows-10-version-1607"></a><a href="" id="whatsnew1607"></a>Was ist neu in Windows 10, Version 1607


<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Sideloading von apps</p></td>
<td style="vertical-align:top"><p>In Windows 10, Version 1607 beginnend, ist Sideloading Apps nur über [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md)zulässig. Produktschlüssel (5 x 5) werden nicht mehr unterstützt werden, um Sideloading auf Windows 10, Version 1607 Geräte zu aktivieren.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Neue Wert für [NodeCache CSP](nodecache-csp.md)</p></td>
<td style="vertical-align:top"><p>In [NodeCache CSP](nodecache-csp.md), den Wert der NodeCache Stammknoten starten im Windows-10 wird 1607 com.microsoft/1.0/MDM/NodeCache.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[EnterpriseDataProtection CSP](enterprisedataprotection-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP aus.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Entfernt die folgenden Richtlinien:</p>
<ul>
<li>DataProtection/AllowAzureRMSForEDP - verschoben diese Richtlinie in [EnterpriseDataProtection CSP](enterprisedataprotection-csp.md) .</li>
<li>DataProtection/AllowUserDecryption - verschoben diese Richtlinie in [EnterpriseDataProtection CSP](enterprisedataprotection-csp.md) .</li>
<li>DataProtection/EDPEnforcementLevel - verschoben diese Richtlinie in [EnterpriseDataProtection CSP](enterprisedataprotection-csp.md) .</li>
<li>DataProtection/RequireProtectionUnderLockConfig - verschoben diese Richtlinie in [EnterpriseDataProtection CSP](enterprisedataprotection-csp.md) .</li>
<li>DataProtection/RevokeOnUnenroll - verschoben diese Richtlinie in [EnterpriseDataProtection CSP](enterprisedataprotection-csp.md) .</li>
<li>DataProtection/EnterpriseCloudResources - verschoben diese Richtlinie in NetworkIsolation Richtlinie.</li>
<li>DataProtection/EnterpriseInternalProxyServers - verschoben diese Richtlinie in NetworkIsolation Richtlinie.</li>
<li>DataProtection/EnterpriseIPRange - verschoben diese Richtlinie in NetworkIsolation Richtlinie.</li>
<li>DataProtection/EnterpriseNetworkDomainNames - verschoben diese Richtlinie in NetworkIsolation Richtlinie.</li>
<li>DataProtection/EnterpriseProxyServers - verschoben diese Richtlinie in NetworkIsolation Richtlinie.</li>
<li>Security/AllowAutomaticDeviceEncryptionForAzureADJoinedDevices - diese Richtlinie ist veraltet.</li>
</ul>
<p><strong>WiFi/AllowManualWiFiConfiguration</strong> <strong>und/AllowWiFi WLAN</strong> -Richtlinien hinzugefügt für Windows 10, Version 1607:</p>
<ul>
<li>Windows 10 Pro</li>
<li>Windows 10 Enterprise</li>
<li>Windows 10 Bildungseinrichtungen</li>
</ul>
<p>Die folgenden neuen Richtlinien hinzugefügt:</p>
<ul>
<li>AboveLock/AllowCortanaAboveLock</li>
<li>ApplicationManagement/DisableStoreOriginatedApps</li>
<li>Authentifizierung/AllowSecondaryAuthenticationDevice</li>
<li>Bluetooth/AllowPrepairing</li>
<li>Browser/AllowExtensions</li>
<li>Browser/PreventAccessToAboutFlagsInMicrosoftEdge</li>
<li>Browser/ShowMessageWhenOpeningSitesInInternetExplorer</li>
<li>DeliveryOptimization/DOAbsoluteMaxCacheSize</li>
<li>DeliveryOptimization/DOMaxDownloadBandwidth</li>
<li>DeliveryOptimization/DOMinBackgroundQoS</li>
<li>DeliveryOptimization/DOModifyCacheDrive</li>
<li>DeliveryOptimization/DOMonthlyUploadDataCap</li>
<li>DeliveryOptimization/DOPercentageMaxDownloadBandwidth</li>
<li>DeviceLock/EnforceLockScreenAndLogonImage</li>
<li>DeviceLock/EnforceLockScreenProvider</li>
<li>Defender/PUAProtection</li>
<li>Erfahrung/AllowThirdPartySuggestionsInWindowsSpotlight</li>
<li>Erfahrung/AllowWindowsSpotlight</li>
<li>Erfahrung/ConfigureWindowsSpotlightOnLockScreen</li>
<li>Erfahrung/DoNotShowFeedbackNotifications</li>
<li>Lizenzierung/AllowWindowsEntitlementActivation</li>
<li>Lizenzierung/DisallowKMSClientOnlineAVSValidation</li>
<li>Sperren/AllowEdgeSwipe</li>
<li>Karten/EnableOfflineMapsAutoUpdate</li>
<li>Karten/AllowOfflineMapsDownloadOverMeteredConnection</li>
<li>Messaging/AllowMessageSync</li>
<li>NetworkIsolation/EnterpriseCloudResources</li>
<li>NetworkIsolation/EnterpriseInternalProxyServers</li>
<li>NetworkIsolation/EnterpriseIPRange</li>
<li>NetworkIsolation/EnterpriseIPRangesAreAuthoritative</li>
<li>NetworkIsolation/EnterpriseNetworkDomainNames</li>
<li>NetworkIsolation/EnterpriseProxyServers</li>
<li>NetworkIsolation/EnterpriseProxyServersAreAuthoritative</li>
<li>NetworkIsolation/NeutralResources</li>
<li>Benachrichtigungen/DisallowNotificationMirroring</li>
<li>Datenschutz/DisableAdvertisingId</li>
<li>Datenschutz/LetAppsAccessAccountInfo</li>
<li>Datenschutz/LetAppsAccessAccountInfo_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessAccountInfo_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessAccountInfo_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessCalendar</li>
<li>Datenschutz/LetAppsAccessCalendar_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessCalendar_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessCalendar_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessCallHistory</li>
<li>Datenschutz/LetAppsAccessCallHistory_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessCallHistory_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessCallHistory_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessCamera</li>
<li>Datenschutz/LetAppsAccessCamera_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessCamera_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessCamera_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessContacts</li>
<li>Datenschutz/LetAppsAccessContacts_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessContacts_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessContacts_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessEmail</li>
<li>Datenschutz/LetAppsAccessEmail_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessEmail_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessEmail_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessLocation</li>
<li>Datenschutz/LetAppsAccessLocation_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessLocation_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessLocation_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessMessaging</li>
<li>Datenschutz/LetAppsAccessMessaging_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessMessaging_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessMessaging_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessMicrophone</li>
<li>Datenschutz/LetAppsAccessMicrophone_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessMicrophone_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessMicrophone_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessMotion</li>
<li>Datenschutz/LetAppsAccessMotion_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessMotion_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessMotion_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessNotifications</li>
<li>Datenschutz/LetAppsAccessNotifications_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessNotifications_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessNotifications_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessPhone</li>
<li>Datenschutz/LetAppsAccessPhone_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessPhone_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessPhone_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessRadios</li>
<li>Datenschutz/LetAppsAccessRadios_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessRadios_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessRadios_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsAccessTrustedDevices</li>
<li>Datenschutz/LetAppsAccessTrustedDevices_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsAccessTrustedDevices_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsAccessTrustedDevices_UserInControlOfTheseApps</li>
<li>Datenschutz/LetAppsSyncWithDevices</li>
<li>Datenschutz/LetAppsSyncWithDevices_ForceAllowTheseApps</li>
<li>Datenschutz/LetAppsSyncWithDevices_ForceDenyTheseApps</li>
<li>Datenschutz/LetAppsSyncWithDevices_UserInControlOfTheseApps</li>
<li>Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices</li>
<li>Einstellungen/AllowEditDeviceName</li>
<li>Spracherkennung/AllowSpeechModelUpdate</li>
<li>System/TelemetryProxy</li>
<li>Update/ActiveHoursStart</li>
<li>Update/ActiveHoursEnd</li>
<li>Update/AllowMUUpdateService</li>
<li>Update/BranchReadinessLevel</li>
<li>Update/DeferFeatureUpdatesPeriodInDays</li>
<li>Update/DeferQualityUpdatesPeriodInDays</li>
<li>Update/ExcludeWUDriversInQualityUpdate</li>
<li>Update/PauseFeatureUpdates</li>
<li>Update/PauseQualityUpdates</li>
<li>WindowsInkWorkspace/AllowWindowsInkWorkspace</li>
<li>WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace</li>
<li>WirelessDisplay/AllowProjectionToPC</li>
<li>WirelessDisplay/RequirePinForPairing</li>
</ul>
<p>Aktualisiert die <strong>Datenschutz/AllowAutoAcceptPairingAndPrivacyConsentPrompts</strong> Beschreibung ein, um die veraltete Informationen zu entfernen.</p>
<p>Aktualisierte DeliveryOptimization/DODownloadMode neue Werte hinzufügen.</p>
<p>Aktualisierte Erfahrung/AllowCortana Beschreibung zur Klärung welche jeden unterstützten Werts ist.</p>
<p>Aktualisierte Security/AntiTheftMode Beschreibung zur Klärung welche jeden unterstützten Werts ist.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[DMClient CSP](dmclient-csp.md)</td>
<td style="vertical-align:top"><p>Die folgenden Einstellungen hinzugefügt:</p>
<ul>
<li>ManagementServerAddressList</li>
<li>AADDeviceID</li>
<li>EnrollmentType</li>
<li>HWDevID</li>
<li>CommercialID</li>
</ul>
<p>Die Einstellung EnrollmentID entfernt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Reporting CSP](reporting-csp.md)</td>
<td style="vertical-align:top"><p>Unterstützung für <strong>SecurityAuditing</strong> -Einstellungen für den Desktop hinzugefügt.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[DeviceManageability CSP](devicemanageability-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP aus.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[DeviceStatus CSP](devicestatus-csp.md)</td>
<td style="vertical-align:top"><p>Die folgenden neuen Einstellungen hinzugefügt:</p>
<ul>
<li>DeviceStatus/TPM/SpecificationVersion</li>
<li>DeviceStatus/OS/Edition</li>
<li>DeviceStatus/Antivirus/SignatureStatus</li>
<li>DeviceStatus/Antivirus/Status</li>
<li>DeviceStatus/Antispyware/SignatureStatus</li>
<li>DeviceStatus/Antispyware/Status</li>
<li>DeviceStatus/Firewall/Status</li>
<li>DeviceStatus/UAC/Status</li>
<li>DeviceStatus/Batterie/Status</li>
<li>DeviceStatus/Batterie/EstimatedChargeRemaining</li>
<li>DeviceStatus/Batterie/EstimatedRuntime</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[AssignedAccess CSP](assignedaccess-csp.md)</td>
<td style="vertical-align:top"><p>SyncML Beispiele hinzugefügt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[EnterpriseAssignedAccess CSP](enterpriseassignedaccess-csp.md)</td>
<td style="vertical-align:top"><ul>
<li>Einen neuen Tabelle Ordnereintrag hinzugefügt in die AssignedAccess/AssignedAccessXml Beschreibung.</li>
<li>In den Abschnitten für DDF und XSD-Datei aktualisiert.</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[SecureAssessment CSP](secureassessment-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, Version 1607</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[DiagnosticLog CSP](diagnosticlog-csp.md)
<p>[DiagnosticLog DDF](diagnosticlog-ddf.md)</p></td>
<td style="vertical-align:top"><p>Hinzugefügte Version 1.3 CSP mit zwei neuen Einstellungen. Die neue Version 1.3 der DDF hinzugefügt. Die folgenden neuen Einstellungen hinzugefügt in Windows 10, Version 1607.</p>
<ul>
<li>DeviceStateData</li>
<li>DeviceStateData/MdmConfiguration</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[Neustart CSP](reboot-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, Version 1607</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[CMPolicyEnterprise CSP](cmpolicyenterprise-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, Version 1607</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[VPNv2 CSP](vpnv2-csp.md)</td>
<td style="vertical-align:top"><p>Die folgenden Einstellungen für Windows 10, Version 1607 hinzugefügt</p>
<ul>
<li><em>Profilname</em>/RouteList/routeRowId/ExclusionRoute</li>
<li><em>Profilname</em>/DomainNameInformationList/<em>DniRowId</em>/AutoTrigger</li>
<li><em>Profilname</em>/DomainNameInformationList/dniRowId/Persistent</li>
<li><em>Profilname</em>/ProfileXML</li>
<li><em>Profilname</em>/DeviceCompliance/aktiviert</li>
<li><em>Profilname</em>/DeviceCompliance/Sso</li>
<li><em>Profilname</em>/DeviceCompliance/Sso/Enabled</li>
<li><em>Profilname</em>/DeviceCompliance/Sso/IssuerHash</li>
<li><em>Profilname</em>/DeviceCompliance/Sso/Eku</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/AuthenticationTransformConstants</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/CipherTransformConstants</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/EncryptionMethod</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/IntegrityCheckMethod</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/DHGroup</li>
<li><em>Profilname</em>/NativeProfile/CryptographySuite/PfsGroup</li>
<li><em>Profilname</em>/NativeProfile/L2tpPsk</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Win32AppInventory CSP](win32appinventory-csp.md)
<p>[Win32AppInventory DDF](win32appinventory-ddf-file.md)</p></td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, Version 1607.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[SharedPC CSP](sharedpc-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, 1607 Version.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[WindowsAdvancedThreatProtection CSP](windowsadvancedthreatprotection-csp.md)</td>
<td style="vertical-align:top"><p>Neue CSP für Windows 10, Version 1607.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[MDM Bridge WMI-Anbieter](https://msdn.microsoft.com/library/windows/hardware/dn905224)</td>
<td style="vertical-align:top"><p>Neue Klassen für Windows 10, Version 1607 hinzugefügt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[MDM Registrierung von Windows-Geräten](mdm-enrollment-of-windows-devices.md)</td>
<td style="vertical-align:top"><p>Thema von umbenannt &quot;Registrierung Benutzeroberfläche&quot;.</p>
<p>Registrierung Prozeduren und Screenshots vollständig aktualisiert.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[UnifiedWriteFilter CSP](unifiedwritefilter-csp.md)
<p>[UnifiedWriteFilter DDF-Datei](unifiedwritefilter-ddf.md)</p></td>
<td style="vertical-align:top"><p>Die folgenden neue Einstellung für Windows 10, Version 1607 hinzugefügt:</p>
<ul>
<li>NextSession/HORMEnabled</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[CertificateStore CSP](certificatestore-csp.md)
<p>[CertificateStore DDF-Datei](certificatestore-ddf-file.md)</p></td>
<td style="vertical-align:top"><p>Die folgenden neuen Einstellungen hinzugefügt in Windows 10, Version 1607:</p>
<ul>
<li>Meine/WSTEP/erneuern/LastRenewalAttemptTime</li>
<li>Meine/WSTEP/erneuern/RenewNow</li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="breaking-changes-and-known-issues"></a>Wichtige Änderungen und bekannte Probleme


### <a name="a-href-idgetcommandaget-command-inside-an-atomic-command-is-not-supported"></a><a href="" id="getcommand"></a>GET-Befehl innerhalb einer unteilbare Befehl wird nicht unterstützt.

In Windows 10 wird innerhalb einer unteilbare Befehl Get-Befehl nicht unterstützt. Dies wurde in Windows Phone 8 und Windows Phone 8.1 zulässig ist.

### <a name="a-href-idnotificationanotification-channel-uri-not-preserved-during-upgrade-from-windows-81-to-windows-10"></a><a href="" id="notification"></a>Benachrichtigung Channel-URI, die während des Upgrades von Windows 8.1 für Windows 10 nicht beibehalten

Bei einem Upgrade von Windows 8.1 auf Windows 10 wird der Benachrichtigung DDE-Kanal-URI-Informationen nicht beibehalten. Darüber hinaus verliert der Client MDM PFN, AppID und den geheimen Clientschlüssel.

Rufen Sie nach dem Upgrade auf Windows 10, MDM\_WNSConfiguration-Klasse zum erneuten Erstellen den Benachrichtigung Channel-URI.

### <a name="a-href-idappsnotremovedaapps-installed-using-wmi-classes-are-not-removed"></a><a href="" id="appsnotremoved"></a>Apps, die Installation mit WMI-Klassen werden nicht entfernt.

Applications Installation mit WMI-Klassen werden nicht entfernt, wenn das Konto MDM vom Gerät entfernt wird.

### <a name="a-href-idcdataapassing-cdata-in-syncml-does-not-work"></a><a href="" id="cdata"></a>CDATA SyncML übergeben funktioniert nicht

Daten in SyncML ConfigManager und Kryptografiedienstanbieter CDATA übergeben funktioniert nicht in Windows 10. Es funktioniert in Windows Phone 8.

### <a name="a-href-idsslsettingsassl-settings-in-iis-server-for-scep-must-be-set-to-ignore"></a><a href="" id="sslsettings"></a>Einstellungen für SSL in IIS-Server für SCEP müssen auf "Ignorieren" festgelegt werden

Das Zertifikat unter "Einstellungen für SSL" in der IIS-Server SCEP muss auf "Ignorieren" in Windows 10 festgelegt werden. In Windows Phone 8.1 Wenn Sie festlegen, dass das Clientzertifikat auf "Accept", funktioniert es.

![Einstellungen für SSL](images/ssl-settings.png)

### <a name="a-href-idenrollmentviaproxyamdm-enrollment-fails-on-the-mobile-device-when-traffic-is-going-through-proxy"></a><a href="" id="enrollmentviaproxy"></a>MDM Registrierung auf dem mobilen Gerät schlägt fehl, wenn Datenverkehr über Proxy geht

Wenn das mobile Gerät konfiguriert ist, um einen Proxy verwenden, der Authentifizierung erfordert, schlägt die Registrierung fehl. Um dieses Problem zu umgehen, kann der Benutzer einen Proxy verwenden, der keine Authentifizierung und entfernen die Proxyeinstellung aus dem Netzwerk verbunden.

### <a name="a-href-idunenrollmentaserver-initiated-unenrollment-failure"></a><a href="" id="unenrollment"></a>Ausfall der Server initiierte unenrollment

Server initiierte Unenrollment für ein Gerät durch Hinzufügen eines Kontos für die Arbeit im Hintergrund registriert schlägt fehl, das Konto MDM aktiven verlassen. MDM Richtlinien und Ressourcen noch gültig sind und der Client kann weiterhin mit dem Server synchronisieren.

Remoteserver Unenrollment ist für mobile Geräte über Azure Active Directory beitreten registriert deaktiviert. Es wird eine Fehlermeldung an den Server zurückgegeben. Durch das Gerät Remote verlorener ist die einzige Möglichkeit zum Registrierung für ein mobiles Gerät zu entfernen, die Azure AD verbunden ist.

### <a name="a-href-idcertissuesacertificates-causing-issues-with-wi-fi-and-vpn"></a><a href="" id="certissues"></a>Verursacht Probleme mit Wi-Fi und VPN-Zertifikate

Derzeit Windows 10, Version 1511, bei Verwendung der ClientCertificateInstall-Zertifikate auf dem Gerätespeicher und der Benutzerspeicher und beide Zertifikate installiert werden gesendet, um das Gerät in der gleichen MDM Nutzlast im Benutzerspeicher auch das Zertifikat für die direkte Verwendung für den Gerätespeicher installiert wird. Dies kann zu Problemen bei der Auswahl des richtigen Zertifikats zum Herstellen einer Verbindung mit Wi-Fi oder VPN-führen. Wir arbeiten, um dieses Problem zu beheben.

### <a name="a-href-idversioninformationaversion-information-for-mobile-devices"></a><a href="" id="versioninformation"></a>Versionsinformationen für mobile Geräte

Die Softwareversionsinformationen **DevDetail/SwV** stimmt nicht mit die Version in den **Einstellungen** unter **System/zu**überein.

### <a name="a-href-idwhitelistaupgrading-windows-phone-81-devices-with-app-whitelisting-using-applicationrestriction-policy-has-issues"></a><a href="" id="whitelist"></a>Aktualisieren von Windows Phone 8.1 Geräte mit dem app mithilfe von ApplicationRestriction Richtlinie hat Probleme

-   Während der Aktualisierung von Windows Phone 8.1 Geräte Windows 10 Mobile eine Liste der zulässigen apps ApplicationRestrictions mit verursacht unerwartetes Verhalten einiger Windows Posteingang apps blockiert. Um dieses Problem zu umgehen, müssen Sie den [Posteingang apps](applocker-csp.md#inboxappsandcomponents) einschließen, die Sie Ihrer Liste der zulässigen apps müssen.

    Hier finden zusätzliche Richtlinien für den Upgradevorgang:

    -   Verwenden Sie Windows-10-Produkt-IDs für die apps in [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt.
    -   Verwenden Sie den neuen Namen der Microsoft Publisher (PublisherName = "CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S Washington, C = = US") und Publisher = "CN = Microsoft Windows, O = Microsoft Corporation, L = Redmond, S Washington, C = = US" Wenn Sie die Publisher-Richtlinie verwenden. Entfernen Sie die Windows Phone 8.1 Publisher Regel nicht, wenn Sie es verwenden.
    -   In der SyncML müssen Sie Kleinbuchstaben Produkt-ID verwenden.
    -   Führen Sie eine Product ID nicht doppelt Messaging und Skype Videofunktionen verwenden die gleichen Produkt-ID Duplikate führt zu einer Fehlermeldung.

    Weitere Informationen hierzu finden Sie unter [ApplicationRestrictions im Bereich CSP PolicyManager](policymanager-csp.md#applicationmanagement-applicationrestrictions).

-   Silverlight kann möglicherweise nicht installiert, auch wenn Publisherrichtlinie mithilfe von Windows Phone 8.1 Publisher Regel angegeben ist. Beispielsweise Silverlight-Anwendung "Level" nicht installiert werden, kann selbst wenn Sie angegeben &lt;Publisher PublisherName = "Microsoft Corporation" /&gt;.

    Zum Umgehen dieses Problems entfernen Sie die Windows Phone 8.1 Publisher Regel, und fügen Sie die bestimmten Produkt-ID für die jeweilige Silverlight-app, die Sie zur Liste zulässigen app zulassen möchten.

-   Einige apps (insbesondere solche, die im Windows Store als AppX fasst veröffentlicht werden) werden blockiert, vom installieren, auch wenn sie in der Liste enthalten sind.

    Nicht umgangen werden zu diesem Zeitpunkt. Ein OS Update zur Behebung dieses Problems wird in Kürze bereitgestellt.

### <a name="a-href-idframeworksaapps-dependent-on-microsoft-frameworks-may-get-blocked-in-phones-prior-to-build-10586218"></a><a href="" id="frameworks"></a>Apps, die abhängig von der Microsoft-Frameworks können in Telefone vor Build 10586.218 blockiert abrufen

Gilt nur für Telefon vor Build 10586.218: Wenn ApplicationManagement/ApplicationRestrictions Richtlinie wird Windows 10 Mobile Installation bereitgestellt, und Aktualisieren von apps abhängig von der Microsoft-Frameworks möglicherweise mit Fehler 0x80073CF9 blockiert. Dieses Problem zu umgehen, müssen Sie die Microsoft-Framework-Id Ihrer Liste der zulässigen apps einbeziehen.

``` syntax
<App ProductId="{00000000-0000-0000-0000-000000000000}" PublisherName="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"/>
```

### <a name="a-href-idwificertissueamultiple-certificates-might-cause-wi-fi-connection-instabilities-in-windows-10-mobile"></a><a href="" id="wificertissue"></a>Mehrere Zertifikate Ursachen in Windows 10 Mobile Wi-Fi-Verbindung installiert haben.

In der Bereitstellung Wenn Sie mehrere Zertifikate auf dem Gerät bereitgestellt haben und das bereitgestellte Wi-Fi-Profil verfügt nicht über eine exakte Filterkriterien sehen Verbindungsfehler Sie beim Verbinden mit Wi-Fi. Die Lösung besteht darin, sicherzustellen, dass das Wi-Fi-Profil bereitgestellt strict Filterkriterien verfügt, so, dass sie nur ein Zertifikat entspricht.

Unternehmen bereitstellen Zertifikats basierend EAP-Authentifizierung für VPN/Wi-Fi der Vorderseite nach einer Situation kann, in denen es sind mehrere Zertifikate, die die Kriterien für die Authentifizierung zu erfüllen. Dies kann zu Problemen wie führen:

-   Der Benutzer kann aufgefordert werden, können Sie das Zertifikat auswählen.
-   Das falsche Zertifikat möglicherweise erhalten automatisch ausgewählt und ein Authentifizierungsfehlers verursachen.

Eine Bereitstellung in der Produktion bereit benötigen die entsprechenden Zertifikatdetails als Teil des Profils bereitgestellt wird. Die folgende Informationen erläutert das Erstellen oder aktualisieren eine EAP-Konfigurations-XML so, dass die zusätzlichen Zertifikate gefiltert werden, und das entsprechende Zertifikat für die Authentifizierung verwendet werden kann.

EAP XML muss mit der relevante Informationen für Ihre Umgebung, dass dies manuell durch Bearbeiten des XML-Beispiels unten oder mithilfe der Benutzeroberfläche Leitfaden erfolgen kann aktualisiert werden. Nachdem das EAP XML aktualisiert wird, finden Sie in Anweisungen aus Ihrer MDM zum Bereitstellen von aktualisierten Konfigurations wie folgt:

-   Wi-Fi, suchen Sie nach der &lt;EAPConfig&gt; Abschnitt Ihrer aktuellen WLAN-Profil-XML-Daten (dieser Schritt ist, was Sie für den Knoten WLanXml im Wi-Fi CSP angeben). Innerhalb dieser Tags finden Sie die gesamte EAP-Konfiguration. Ersetzen Sie den Abschnitt unter &lt;EAPConfig&gt; Ihrer aktualisierten XML- und Ihr Wi-Fi-Profil zu aktualisieren. Sie müssen möglicherweise auf Ihre MDM Anleitungen zum Bereitstellen eines neuen Wi-Fi-Profils zu verweisen.
-   Für VPN ist EAP-Konfiguration ein separates Feld in der MDM-Konfiguration. Arbeiten Sie mit Ihrem Anbieter MDM identifizieren und das entsprechende Feld aktualisieren.

Informationen zu EAP-Einstellungen finden Sie unter <https://technet.microsoft.com/library/hh945104.aspx#BKMK_Cfg_cert_Selct>

Informationen zum Generieren eines EAP XML finden Sie unter [EAP-Konfiguration](eap-configuration.md)

Weitere Informationen zu erweiterten Enhanced Key Usage finden Sie unter <http://tools.ietf.org/html/rfc5280#section-4.2.1.12>

Informationen zum Hinzufügen von Erweiterte Schlüsselverwendung (EKU) an ein Zertifikat finden Sie unter <https://technet.microsoft.com/library/cc731792.aspx>

Die folgende Liste beschreibt die erforderlichen Komponenten für ein Zertifikat mit EAP verwendet werden:

-   Das Zertifikat muss mindestens eine der folgenden EKU (Erweiterte Schlüsselverwendung) Eigenschaften aufweisen:

    -   Clientauthentifizierung
    -   Gemäß RFC 5280, ist dies ein eindeutig definierter OID mit Wert 1.3.6.1.5.5.7.3.2
    -   Einen beliebigen Zweck
    -   Die EKU definiert und von Microsoft veröffentlicht, ist ein eindeutig definierter OID mit 1.3.6.1.4.1.311.10.12.1-Wert. Die Aufnahme dieser OID impliziert, dass das Zertifikat für einen beliebigen Zweck verwendet werden kann. Der Vorteil eines EKU gegenüber der alle Zweck EKU ist, dass zusätzliche nicht kritischen oder benutzerdefinierte EKU weiterhin das Zertifikat für eine effektive Filterung hinzugefügt werden können.
    -   Alle Zwecke
    -   Gemäß RFC 5280, wenn eine Zertifizierungsstelle erweiterte Schlüsselverwendung umfasst um einige Anwendung benötigt, möchte jedoch nicht zum Einschränken der Verwendung des Schlüssels zu erfüllen, kann die Zertifizierungsstelle einen erweiterten Key Usage-Wert von 0 hinzufügen. Ein Zertifikat mit einer solchen EKU kann für alle Zwecke verwendet werden.
-   Der Benutzer oder das Computerzertifikat auf dem Client Lieferketten zu einer vertrauenswürdigen Stammzertifizierungsstelle
-   Der Benutzer oder das Computerzertifikat fehlschlagen nicht eine der Prüfungen, die von den Zertifikatspeicher CryptoAPI ausgeführt werden, und das Zertifikat übergibt Anforderungen RAS-Richtlinie.
-   Der Benutzer oder das Computerzertifikat kein Fehler eine der Zertifikat-Objekt-ID Prüfungen, die in der (Internetauthentifizierungsdienst) angegeben sind auf / Radius-Server.
-   Erweiterung für den alternativen Antragstellernamen (SubjectAltName) im Zertifikat enthält den Benutzerprinzipalnamen (UPN) des Benutzers an.

Im folgende XML-Beispiel wird die Eigenschaften für das Zertifikat Filtern einschließlich EAP TLS-XML erläutert.

> **Hinweis**  Der EAP-TLS-XML-CODE ist für PEAP oder TTLS Profile in PEAP oder TTLS bestimmte Elemente eingebettet.

 
``` syntax
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
 <EapMethod>
  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
  <!--The above property defines the Method type for EAP, 13 means EAP TLS -->

  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
  <!--The 3 properties above define the method publishers, this is seen primarily in 3rd party Vendor methods.-->
  <!-- For Microsoft EAP TLS the value of the above fields will always be 0 --> 
 </EapMethod>
 <!-- Now that the EAP Method is Defined we will go into the Configuration --> 
 <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
   <Type>13</Type>
   <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
    <CredentialsSource>
     <!-- Credential Source can be either CertificateStore or SmartCard --> 
     <CertificateStore>
      <SimpleCertSelection>true</SimpleCertSelection>
      <!--SimpleCertSelection automatically selects a cert if there are mutiple identical (Same UPN, Issuer, etc.) certs.-->
      <!--It uses a combination of rules to select the right cert-->
     </CertificateStore>
    </CredentialsSource>
    <ServerValidation>
     <!-- ServerValidation fields allow for checks on whether the server being connected to and the server cert being used are trusted -->
     <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
     <ServerNames/>
    </ServerValidation>
    <DifferentUsername>false</DifferentUsername>
    <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
    <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
     <!-- For filtering the relevant information is below -->
     <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
      <CAHashList Enabled="true">
       <!-- The above implies that you want to filter by Issuer Hash -->
       <IssuerHash>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
        <!-- Issuing certs thumbprint goes here-->
       </IssuerHash>
       <!-- You can add multiple entries and it will find the list of certs that have at least one of these certs in its chain--> 
      </CAHashList>
      <EKUMapping>
       <!-- This section defines Custom EKUs that you may be adding-->
       <!-- You do not need this section if you do not have custom EKUs -->
       <!-- You can have multiple EKUs defined here and then referenced below as shown -->
       <EKUMap>
        <EKUName>
         <!--Add a friendly Name for an EKU here for example -->ContostoITEKU</EKUName> 
        <EKUOID>
         <!--Add the OID Value your CA adds to the certificate here, for example -->1.3.6.1.4.1.311.42.1.15</EKUOID> 
       </EKUMap>
        <!-- All the EKU Names referenced in the example below must first be defined here
       <EKUMap>
        <EKUName>Example1</EKUName>
        <EKUOID>2.23.133.8.3</EKUOID>
      
       </EKUMap>
       <EKUMap>
        <EKUName>Example2</EKUName>
        <EKUOID>1.3.6.1.4.1.311.20.2.1</EKUOID>
       </EKUMap>
       -->
      </EKUMapping>
      <ClientAuthEKUList Enabled="true">
       <!-- The above implies that you want certs with Client Authentication EKU to be used for authentication -->
       <EKUMapInList>
        <!-- This section implies that the certificate should have the following custom EKUs in addition to the Client Authentication EKU -->
        <EKUName>
         <!--Use the name from the EKUMap Field above-->ContostoITEKU</EKUName> 
       </EKUMapInList>
       <!-- You can have multiple Custom EKUs mapped here, Each additional EKU will be processed with an AND operand -->
       <!-- For example, Client Auth EKU AND ContosoITEKU AND Example1 etc. -->
       <EKUMapInList>
        <EKUName>Example1</EKUName>
       </EKUMapInList>
      </ClientAuthEKUList>
      <AllPurposeEnabled>true</AllPurposeEnabled>
      <!-- Implies that a certificate with the EKU field = 0 will be selected --> 
      <AnyPurposeEKUList Enabled="true"/>
      <!-- Implies that a certificate with the EKU oid Value of 1.3.6.1.4.1.311.10.12.1 will be selected --> 
      <!-- Like for Client Auth you can also add Custom EKU properties with AnyPurposeEKUList (but not with AllPurposeEnabled) -->
      <!-- So here is what the above policy implies. 
      The certificate selected will have
      Issuer Thumbprint = ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
      AND
      ((Client Authentication EKU AND ContosoITEKU) OR (AnyPurposeEKU) OR AllPurpose Certificate)
      
      Any certificate(s) that match these criteria will be utilised for authentication
      -->
     </FilteringInfo>
    </TLSExtensions>
   </EapType>
  </Eap>
 </Config>
</EapHostConfig>
```

> **Hinweis**  Der EAP-TLS-XSD befindet sich unter **Systemlaufwerk %\\Windows\\Schemas\\EAPMethods\\eaptlsconnectionpropertiesv3.xsd**

 

Alternativ können Sie das folgende Verfahren verwenden, erstellen Sie eine EAP-Konfigurations-XML.

1.  Führen Sie die Schritte 1 bis 7 im Thema [EAP-Konfiguration](eap-configuration.md) .
2.  Wählen Sie im Dialogfeld Eigenschaften von Microsoft VPN davon **Microsoft: Smartcard oder andere Zertifikat** aus der Dropdownliste (diese markiert EAP TLS)

    ![VPN-davon Eigenschaftenfenster](images/certfiltering1.png)

    > **Hinweis**  Wählen Sie für PEAP oder TTLS die entsprechende Methode aus, und folgen Sie diesem Verfahren fortgesetzt.

3.  Klicken Sie auf die Schaltfläche " **Eigenschaften** " unterhalb der Dropdown-Menü.
4.  Klicken Sie im Menü **Smartcard oder andere Zertifikateigenschaften** wählen Sie die Schaltfläche **Erweitert** .

    ![Smartcard oder andere Eigenschaftenfenster Zertifikat](images/certfiltering2.png)
5.  Klicken Sie im Menü **Konfigurieren Zertifikatauswahl** passen Sie die Filter nach Bedarf.

    ![Konfigurieren Sie Fenster zur Auswahl des Zertifikats](images/certfiltering3.png)
6.  Klicken Sie auf **OK** , um die Fenster zu im Dialogfeld für die wichtigsten rasphone.exe zurückzukehren zu schließen.
7.  Schließen Sie das Dialogfeld Rasphone.
8.  Führen Sie die folgenden das Verfahren im Thema [EAP-Konfiguration](eap-configuration.md) aus Schritt 9, um ein EAP TLS Profil mit dem entsprechenden Filter zu erhalten.

> **Hinweis**  Sie können auch alle anderen zutreffend EAP Eigenschaften mithilfe dieser Benutzeroberfläche sowie festlegen. Leitfaden für die Bedeutung dieser Eigenschaften kann im Thema [Extensible Authentication Protocol (EAP) Einstellungen für den Netzwerkzugriff](https://technet.microsoft.com/library/hh945104.aspx) gefunden werden.


### <a name="a-href-idremotearemote-pin-reset-not-supported-in-azure-active-directory-joined-mobile-devices"></a><a href="" id="remote"></a>Remote PIN zurücksetzen in Azure Active Directory nicht unterstützt beigetreten mobile Geräten

In Windows 10 Mobile remote PIN zurücksetzen in Azure AD verbunden Geräte werden nicht unterstützt. Geräte werden endgültig gelöscht, wenn Sie einen remote PIN zurücksetzen-Befehl mit dem RemoteLock CSP ausgeben.

### <a name="a-href-idrenewwnsamdm-client-will-immediately-check-in-with-the-mdm-server-after-client-renews-wns-channel-uri"></a><a href="" id="renewwns"></a>MDM Client wird sofort mit dem MDM Server Einchecken nachdem Client WNS Channel-URI erneuert.

Starten im Windows 10, nachdem der Client MDM automatisch den WNS Channel-URI erneuert, MDM-Client wird sofort mit dem MDM Server einchecken. Nun sollte für jede MDM Client einchecken, MDM sendet der Server eine GET-Anforderung für "ProviderID/Push/ChannelURI" So rufen Sie den neuesten Channel-URI und vergleichen Sie ihn mit den vorhandenen Kanal-URI; So aktualisieren Sie dann den Channel-URI bei Bedarf.

### <a name="a-href-iduserprovisioningauser-provisioning-failure-in-azure-active-directory-joined-windows-10-pc"></a><a href="" id="userprovisioning"></a>Benutzer Bereitstellungsfehler in Azure Active Directory verbunden Windows 10 PC

In Azure AD verknüpft Windows 10 PC-Bereitstellung /. User-Ressourcen schlägt fehl, wenn der Benutzer als Azure AD-Benutzer nicht angemeldet ist. Wenn Sie versuchen, Azure AD aus **Einstellungen** teilnehmen &gt; **System** &gt; **über** die Benutzeroberfläche, vergewissern Sie sich abmelden, und melden Sie sich mit Azure AD-Anmeldeinformationen für Ihre Organisationskonfiguration aus Ihrem MDM Server abzurufen. Dieses Verhalten ist entwurfsbedingt.

### <a name="a-href-idkerberosarequirements-to-note-for-vpn-certificates-also-used-for-kerberos-authentication"></a><a href="" id="kerberos"></a>Anforderungen beachten für VPN-Zertifikate auch für die Kerberos-Authentifizierung verwendet

Wenn verwenden Sie das Zertifikat für die VPN-Authentifizierung auch für die Kerberos-Authentifizierung (erforderlich, wenn Sie Zugriff benötigen auf lokale Ressourcen mit NTLM oder Kerberos) verwendet werden soll, muss das Zertifikat des Benutzers die Anforderungen für Smartcard-Zertifikat erfüllen, deren Feld Betreff sollte das DNS enthalten Domänennamen in der DN oder SAN sollte einen vollqualifizierten UPN enthalten, damit der DC aus der DNS-Registrierungen gefunden werden kann. Wenn Zertifikate, die nicht diesen Anforderungen entsprechen für VPN verwendet werden, können der Benutzer auf Ressourcen zugreifen, die Kerberos-Authentifizierung erfordern fehlschlagen. Dieses Problem wirkt sich hauptsächlich auf Windows Phone aus.

### <a name="a-href-idpushbuttonresetadevice-management-agent-for-the-push-button-reset-is-not-working"></a><a href="" id="pushbuttonreset"></a>Gerät Verwaltungs-Agent für die Drucktaste zurücksetzen ist nicht funktionsfähig.

Der Agent DM für [Drucktaste zurücksetzen](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/push-button-reset-overview) behält die registrierungseinstellungen für OMA DM-Sitzungen, aber löscht Zeitpläne für Aufgaben. Die Client-Registrierung wird beibehalten, aber es nie mit den MDM Dienst synchronisiert wird.


## <a name="change-history-in-mdm-documentation"></a>Änderungsprotokoll in MDM-Dokumentation

### <a name="november-2016"></a>November 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[EnterpriseAPN CSP](enterpriseapn-csp.md)</td>
<td style="vertical-align:top"><p>Der EnterpriseAPN Konfiguration-Dienstanbieter (CSP) wird im Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), Versionen 1511 und 1607 nicht unterstützt.</p>
</td>
</tr><tr class="even">
<td style="vertical-align:top">[Defender CSP](defender-csp.md)</td>
<td style="vertical-align:top"><p>Die folgenden Werte für Defender-Scan Einstellung hinzugefügt:</p>
<ul>
<li>1 – schnell-scan</li>
<li>2 - vollständige Überprüfung</li>
</ul>
</td>
</tr><tr class="odd">
<td style="vertical-align:top">[EnterpriseDataProtection CSP](enterprisedataprotection-csp.md)</td>
<td style="vertical-align:top"><p>Daten Recovery-Agent (DRA) Informationen zu Einstellungen/DataRecoveryCertificate hinzugefügt.</p>
</td>
</tr><tr class="even">
<td style="vertical-align:top">[Trennen die Verwaltungsinfrastruktur (Unenrollment)](disconnecting-from-mdm-unenrollment.md)</td>
<td style="vertical-align:top"><p>Informationen zu Unenrollment von Azure Active Directory beitreten hinzugefügt.</p>
</td>
</tr><tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die Beschreibung der folgenden Richtlinien.<ul>
<li>[Browser/Homepages](policy-configuration-service-provider#browser-homepages)</li>
<li>[DeviceLock/MaxInactivityTimeDeviceLock](policy-configuration-service-provider#devicelock-maxinactivitytimedevicelock)</li>
</ul></p>
</td>
</tr>
</tbody>
</table>

### <a name="october-27-2016"></a>27 Oktober 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[CM_ProxyEntries CSP](cm-proxyentries-csp.md)</td>
<td style="vertical-align:top"><p>Unterstützung für OMA DM wurde in Windows 10, Version 1607 hinzugefügt.</p>
</td></tr>
<tr class="even">
<td style="vertical-align:top">[AppLocker CSP](applocker-csp.md)</td>
<td style="vertical-align:top"><p> [Empfohlene verweigern Liste für Windows Information Protection](applocker-csp.md#recommended-deny-list-for-windows-information-protection) - Beispiel für Windows 10, Version 1607, die verweigert bezeichnet unenlightened Microsoft-apps auf Enterprise-Daten als eine zulässige app zugreifen. Dadurch wird sichergestellt, ein Administrator nicht versehentlich stellen diese apps, die Windows Information Protection zulässig, und Kompatibilität bekannte Probleme im Zusammenhang mit der automatischen Datei-Verschlüsselung mit diese Anwendungen vermeiden. 
</p>
</td>
</tr>
</tbody>
</table>

### <a name="october-21-2016"></a>21 Oktober 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die am stärksten eingeschränkte Werte für die folgenden Richtlinien:</p>
<ul>
<li>Browser/AllowDoNotTrack</li>
<li>Browser/AllowPasswordManager</li>
<li>Browser/AllowPopups</li>
<li>Browser/AllowSmartScreen</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="october-6-2016"></a>6 Oktober 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>WindowsTeam CSP</p></td>
<td style="vertical-align:top"><p>Das Thema WindowsTeam CSP gelöscht. Verwenden Sie stattdessen [SurfaceHub](surfacehub-csp.md) .</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Die folgenden Richtlinien hinzugefügt:</p>
<ul>
<li>Suchen/DisableBackoff</li>
<li>Suchen/DisableRemovableDriveIndexing</li>
<li>Suchen/PreventIndexingLowDiskSpaceMB</li>
<li>Suchen/PreventRemoteQueries</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="september-29-2016"></a>29 September 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die folgenden Richtlinien:</p>
<ul>
<li>System/AllowBuildPreview - unterstützt Windows 10 Mobile und Windows 10 Mobile Enterprise</li>
<li>Erfahrung/AllowThirdPartySuggestionsInWindowsSpotlight - in Windows 10 Pro unterstützt.</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="september-22-2016"></a>22 September 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[AppLocker CSP](applocker-csp.md)</td>
<td style="vertical-align:top"><p>Der folgende Hinweis hinzugefügt die die Liste der [Posteingang apps und Komponenten](applocker-csp.md#inboxappsandcomponents):</p>
<div class="alert">
<strong>Hinweis</strong> Diese Liste gibt System-apps, die als Teil des Windows geliefert, die Sie Ihre Richtlinie AppLocker, um sicherzustellen, dass ordnungsgemäße Funktion des Betriebssystems hinzufügen können. Wenn Sie beschließen, diese apps zu blockieren, wird empfohlen, eine sorgfältige Tests vor der Bereitstellung in Ihrer produktionsumgebung. Anderenfalls kann unerwartete Fehler und die Benutzeroberfläche erheblich beeinträchtigen kann.
</div>
</td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>[ComputerName](https://msdn.microsoft.com/library/windows/hardware/mt188590) im Windows-Bereitstellung (Referenz)</p></td>
<td style="vertical-align:top"><p>ComputerName Sternchen (*) wird nicht unterstützt und leere Zeichenfolge wird nicht unterstützt.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die unterstützten Werte für [Update/BranchReadinessLevel](policy-configuration-service-provider.md#update-branchreadinesslevel)</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Verwaltung der geräteaktualisierung](device-update-management.md)</td>
<td style="vertical-align:top"><p>Im folgenden Abschnitt aktualisiert:</p>
<ul>
<li>[Erste Update-Metadaten, die unter Verwendung des Server-zu-Server-Sync-Protokolls](device-update-management.md#gettingupdatemetadata)</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="september-12-2016"></a>12 September 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Die folgende Anweisung hinzugefügt Update/DeferUpdatePeriod Richtlinie:</p>
<p>In Windows 10 Mobile Enterprise-Version 1511 Geräte legen Sie auf automatische Updates, für DeferUpdatePeriod funktioniert müssen Sie Folgendes festlegen:</p>
<ul>
<li>/ RequireDeferUpgrade Update muss auf 1 festgelegt werden</li>
<li>System/AllowTelemetry muss mindestens auf 1 festgelegt werden</li>
</ul>
<p>Neue Richtlinie Erfahrung/AllowThirdPartySuggestionsInWindowsSpotlight hinzugefügt in Windows 10, Version 1607.</p></td>
</tr>
</tbody>
</table>

 

### <a name="september-8-2016"></a>8 September 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die Namen für die folgenden Einstellungen:</p>
<ul>
<li>AppInventoryQuery</li>
<li>AppInventoryResults</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)</td>
<td style="vertical-align:top"><p>Die folgenden richtlinienbeschreibung aktualisiert:</p>
<p></p>
<dl>
<dt><strong>System/AllowTelemetry</strong></dt>
<dd><p>Zulassen Sie das Gerät zum Senden von Diagnose- und Verwendungsanalyse Telemetriedaten wie Watson.</p>
<p>Die folgenden Listen werden die unterstützten Werte beschrieben:</p>
<p><strong>Windows 8.1 Werte</strong></p>
<ul>
<li>0 – nicht zulässig</li>
<li>1 – zulässig, außer für sekundäre Anforderungen.</li>
<li>2 (Standard) – zulässig.</li>
</ul>
<p><strong>Windows-10-Werte</strong></p>
<ul>
<li>0 – Sicherheit. Angaben sind, die zur Windows Sicherheit beitragen, einschließlich der Daten über die Einstellungen der Benutzerinteraktion verbunden und Telemetrie-Komponente, die böswilligen Tool zum Entfernen der Software und Windows Defender verwenden.
<div class="alert">
<strong>Hinweis</strong>  Dieser Wert gilt nur für Windows 10 Enterprise, Windows 10 Education, Windows 10 Mobile Enterprise, Windows 10 IoT Core (IoT Core) und Windows Server 2016. Mit dieser Einstellung auf anderen Geräten entspricht dem Festlegen des Werts von 1.
</div>
</li>
<li>1 – grundlegende. Grundlegende Device Info, einschließlich: Daten im Zusammenhang mit Qualität, app-Kompatibilität, app-Verwendungsdaten und Daten aus der Sicherheitsstufe.</li>
<li>2 – erweitert. Zusätzliche Hinweise, einschließlich: wie Windows, Windows Server, System Center und apps verwendet werden, die Leistung, erweiterte Zuverlässigkeit Daten und Daten aus der Basic und die Sicherheitsstufen.</li>
<li>3 – vollständige. Alle Daten erforderlich, und beheben Sie Probleme beheben, sowie Daten aus den Ebenen Sicherheit, Basic und erweitert.</li>
</ul>
<div class="alert">
<strong>Wichtige</strong>  Wenn Sie Windows 8.1 MDM Server verwenden, und legen Sie den Wert 0 mithilfe der Richtlinie der Vorversionen AllowTelemetry auf einem Windows 10 Mobile Gerät, der Wert wird nicht berücksichtigt, und die Telemetrie-Ebene im Hintergrund auf der Ebene 1 festgelegt ist.
</div>
<p>Am stärksten eingeschränkten Wert ist 0.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[Unterstützung des Protokolls für OMA DM](oma-dm-protocol-support.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die in der folgenden Beschreibung:</p>
<ul>
<li>LocURI - gibt die Adresse des Speicherorts Ziel oder die Quelle. Wenn die Adresse ein nicht alphanumerische Zeichen enthält, müssen sie entsprechend der URL-Codierung ordnungsgemäß geschützt.</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[VPNv2 CSP](vpnv2-csp.md)</td>
<td style="vertical-align:top"><p>Aktualisiert die in der folgenden Beschreibung:</p>
<ul>
<li><p>VPNv2/Profilname - alpha numerische Kennung für das Profil. Name des Profils darf keinen Schrägstrich (/) enthalten.</p>
<p>Unterstützte Vorgänge einschließen Get, hinzufügen und löschen.</p>
<div class="alert">
<strong>Hinweis</strong>  Weist den Namen des Profils ein Leerzeichen oder andere nicht alphanumerische Zeichen, müssen sie entsprechend der URL-Codierung ordnungsgemäß geschützt.
</div>
</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[MDM Bridge WMI-Anbieter](https://msdn.microsoft.com/library/windows/hardware/dn905224)</td>
<td style="vertical-align:top"><p>Die Beschreibungen für jede Klassenmember ersetzt mit Links zu den entsprechenden Knoten im Thema CSP. Die CSP-Themen enthalten die aktuellste Informationen.</p></td>
</tr>
</tbody>
</table>

 

### <a name="september-2-2016"></a>2 September 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)
<p>[PolicyManager CSP](policymanager-csp.md)</p></td>
<td style="vertical-align:top"><p>Der folgende Hinweis hinzugefügt:</p>
<ul>
<li>Nicht deaktivieren oder aktivieren <strong>Kontakt Support</strong> und <strong>Feedback von Windows</strong> -apps, die mithilfe der ApplicationManagement/ApplicationRestrictions-Richtlinie, obwohl diese im [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt sind.</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[PassportForWork CSP](passportforwork-csp.md)</td>
<td style="vertical-align:top"><p>Der folgende Hinweis hinzugefügt:</p>
<div class="alert">
<strong>Wichtige</strong>  Beginnend mit Windows 10, Version 1607, dass alle Geräte nur eine zugeordnete PIN Windows Hello für Unternehmen. Dies bedeutet, dass PIN auf einem Gerät gelten die Richtlinien in PassportForWork CSP angegeben werden. Die angegebenen Werte haben Vorrang vor jeder Komplexitätsregeln über Exchange ActiveSync (EAS) oder die DeviceLock CSP festgelegt.
</div>
</td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[XSD-profileXML gespeichert](vpnv2-profile-xsd.md)</td>
<td style="vertical-align:top"><p>Das [systemeigene Profilbeispiel](vpnv2-profile-xsd.md#native-profile-example) Beispiel aktualisiert.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Richtlinie CSP](policy-configuration-service-provider.md)
<p>[Verwaltung der geräteaktualisierung](device-update-management.md)</p></td>
<td style="vertical-align:top"><p>Die folgenden Richtlinien werden in Windows 10 Mobile Enterprise nicht unterstützt:</p>
<ul>
<li>DeferUpgradePeriod</li>
<li>DeferFeatureUpdatesPeriodInDays</li>
<li>PauseFeatureUpdates</li>
<li>ExcludeWUDrivers</li>
</ul>
<div class="alert">
<strong>Hinweis</strong>  Da diese Richtlinien nicht gesperrt sind, erhalten Sie bei ihrer Verwendung so konfigurieren Sie eine Windows 10 Mobile Enterprise-Gerät keine Fehlermeldung angezeigt. Die Richtlinien werden jedoch nicht wirksam wird.
</div>
<p>Weitere Informationen zum Aktualisieren von Richtlinien für Windows Update for Business in [Windows 10, Version 1607 für aktualisieren Management](device-update-management.md#windows10version1607forupdatemanagement)unterstützt hinzugefügt.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[DevDetail CSP](devdetail-csp.md)</td>
<td style="vertical-align:top"><p>Klicken Sie im Knoten Microsoft/Ext/DeviceName ersetzen-Vorgang nur in Windows 10 Mobile unterstützt und in den Desktop nicht unterstützt.</p></td>
</tr>
</tbody>
</table>

 

### <a name="august-25-2016"></a>25 August 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Richtlinie DDF-Datei](policy-ddf-file.md)</td>
<td style="vertical-align:top"><p>Aktualisierte Version für Windows 10, Version 1607</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[MDM Registrierung von Windows-Geräten](mdm-enrollment-of-windows-devices.md)</td>
<td style="vertical-align:top"><p>Im Abschnitt zum Registrieren von auf einem Desktop in MDM aktualisiert. Zum Registrieren von in MDM auf einem Telefon einen neuen Abschnitt hinzugefügt.</p></td>
</tr>
</tbody>
</table>

 

### <a name="august-18-2016"></a>18 August 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[CertificateStore CSP](certificatestore-csp.md)
<p>[CertificateStore DDF-Datei](certificatestore-ddf-file.md)</p></td>
<td style="vertical-align:top"><p>Die folgenden neuen Einstellungen hinzugefügt in Windows 10, Version 1607:</p>
<ul>
<li>Meine/WSTEP/erneuern/LastRenewalAttemptTime</li>
<li>Meine/WSTEP/erneuern/RenewNow</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="august-11-2016"></a>11 August 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Massen-Registrierung](bulk-enrollment-using-windows-provisioning-tool.md)</td>
<td style="vertical-align:top"><p>Neuen Abschnitt hinzugefügt:</p>
<ul>
<li>[Wiederholen Sie die Logik bei einem Ausfall](bulk-enrollment-using-windows-provisioning-tool.md#retry-logic-in-case-of-a-failure)</li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Azure Active Directory-Integration mit MDM](azure-active-directory-integration-with-mdm.md)</td>
<td style="vertical-align:top"><p>Link hinzugefügt zu MDM Registrierung Vorlagen und CSS-Dateien:</p>
<ul>
<li>[Laden Sie die Windows-10-Vorlagen und CSS-Dateien](http://download.microsoft.com/download/3/E/5/3E535D52-6432-47F6-B460-4E685C5D543A/MDM-ISV_1.1.3.zip)</li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="august-2-2016"></a>2 August 2016

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Neue oder aktualisierte Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">[Unterstützung des Protokolls für OMA DM](oma-dm-protocol-support.md)</td>
<td style="vertical-align:top"><p>Eine Tabelle mit gemeinsamen SyncML Antwortcodes, die während der OMA DM Sitzungen auftreten hinzugefügt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Mobiles Gerät Registrierung](mobile-device-enrollment.md)</td>
<td style="vertical-align:top"><p>Im folgenden Abschnitt aktualisiert:</p>
<ul>
<li>[Registrierung-Fehlermeldungen](mobile-device-enrollment.md#enrollment-error-messages)</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[SUPL CSP](supl-csp.md)</td>
<td style="vertical-align:top"><p>LocMasterSwitchDependencyNII Einstellung ist nicht veraltet. Entfernt die Beachten Sie, dass es in Windows 10 als veraltet markiert ist.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Push Notification-Unterstützung für die Verwaltung von Geräten](push-notification-windows-mdm.md)</td>
<td style="vertical-align:top"><p>Der folgende Abschnitt hinzugefügt:</p>
<ul>
<li>[Rufen Sie WNS Anmeldeinformationen und PFN für Pushbenachrichtigungen MDM](push-notification-windows-mdm.md#get-wns-credentials-and-pfn-for-mdm-push-notification)</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">[RemoteWipe CSP](remotewipe-csp.md)</td>
<td style="vertical-align:top"><p>Aktualisierte [The Remote Wischen Process](remotewipe-csp.md#the-remote-wipe-process) -Abschnitt. Der folgende Hinweis hinzugefügt:</p>
<div class="alert">
<strong>Hinweis</strong>  Auf dem Desktop führt die Remotezurücksetzung effektiv Herstellerstandard zurücksetzen und PC nicht keine Informationen über den Befehl beibehalten, wenn der Löschvorgang abgeschlossen ist. Antwort vom Gerät zu den tatsächlichen Status oder das Ergebnis des Befehls möglicherweise inkonsistente und unzuverlässige, da die MDM Informationen entfernt wurde.
</div>
</td>
</tr>
<tr class="even">
<td style="vertical-align:top">[Massen-Registrierung](bulk-enrollment-using-windows-provisioning-tool.md)</td>
<td style="vertical-align:top"><p>Hinzugefügte neue Anleitung zum Erstellen und Anwenden von provisioning Pakete.</p></td>
</tr>
</tbody>
</table>

 

## <a name="faq"></a>FAQ


<a href="" id="can-there-be-more-than-1-mdm-server-to-enroll-and-manage-devices-in--"></a>**Sein mehr als 1 MDM Server zum Registrieren und Verwalten von Geräten in Windows 10 kann es?**  
Nein. Nur ein MDM ist zulässig.

<a href="" id="how-do-i-set-the-maximum-number-of-azure-active-directory-joined-devices-per-user-"></a>**Wie richte ich die maximale Anzahl von Azure Active Directory verbunden Geräte pro Benutzer?**  
1.  Melden Sie sich als Administrator das Portal: https://manage.windowsazure.com.
2.  Klicken Sie im linken Bereich auf Active Directory.
3.  Wählen Sie Ihre Mandanten.
4.  Klicken Sie auf **Konfigurieren**.
5.  Kontingent auf unlimited festgelegt.

    ![AAD maximale Anzahl der verknüpften Geräte](images/faq-max-devices.png)

 

 





