---
title: PolicyManager CSP
description: PolicyManager CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 048427b1-6024-4660-8660-bd91c583f7f9
ms.openlocfilehash: bfb68fc6662c09daead9bf61a70b4fc62cfefb8d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="policymanager-csp"></a>PolicyManager CSP


PolicyManager Konfigurationsdienstanbieter ermöglicht das Unternehmen so konfigurieren Sie Unternehmensrichtlinien auf Windows 10 Mobile.

> **Hinweis**   Windows 10 Mobile wird PolicyManager CSP für die Abwärtskompatibilität unterstützt. Für Windows 10 Geräte sollten Sie die [Richtlinie CSP](policy-configuration-service-provider.md), verwenden das PolicyManager CSP ersetzt. Sie können weiterhin PolicyManager CSP für Windows Phone 8.1 und Windows Phone 8.1 GDR-Geräte verwenden. PolicyManager CSP werden einige Zeit in der Zukunft veraltet sein.

 

PolicyManager CSP weist die folgenden Unterkategorien:

-   *AreaName* – verarbeitet die Richtlinie Konfiguration Anforderung vom Server.

-   PolicyManager-*AreaName* – stellt einen schreibgeschützten Pfad zur Richtlinien, die auf dem Gerät erzwungen.

Die Richtlinien für den gleichen *AreaName* die Konfiguration müssen in ein unteilbare Befehl eingeschlossen werden.

Die folgende Abbildung zeigt den PolicyManager Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) und OMA-Clientbereitstellung verwendet.

![Bereitstellung\-Csp\-Policymanager](images/provisioning-csp-policymanager.png)

Die folgende Liste beschreibt die Merkmale und Parameter.

<a href="" id="--vendor-msft-policymanager"></a>**./Vendor/MSFT/PolicyManager**  
Der Stammknoten für den Dienstanbieter für PolicyManager-Konfiguration.

Unterstützte Vorgang ist Get.

<a href="" id="my"></a>**Meine**  
Knoten für Richtlinien für einen bestimmten Anbieter, der abgerufen werden können, geändert oder gelöscht werden.

Unterstützte Vorgang ist Get.

<a href="" id="my--areaname-"></a>**Meine / ***_&lt;AreaName&gt;_**  
Der Bereichsgruppe, die durch eine einzelne Technologie für einen einzelnen Anbieter konfiguriert werden kann. Nach dem Hinzufügen, können Sie den Wert nicht ändern.

Unterstützte Vorgänge sind Add, Get und löschen.

<a href="" id="my--areaname---policyname-"></a>**Meine /_&lt;AreaName&gt;_/****_&lt;PolicyName&gt; _**  
Gibt das Name/Wert-Paar in der Richtlinie verwendet. Die folgende Liste enthält einige Tipps, die Sie beim Konfigurieren von Richtlinien unterstützen:

-   Trennen Sie Mehrfachzeichenfolge Werte durch die Unicode &\#xF000; in der XML-Datei.

-   Enden mit Multistrings &\#xF000; Beispiel einer Zeichenfolge &\#xF000; zwei Zeichenfolge &\#xF000; Rot Zeichenfolge &\#xF000; Blau Zeichenfolge &\#xF000; &\#xF000;. Beachten Sie, dass eine Abfrage aus verschiedenen Anrufer einen anderen Wert bieten konnte, wenn jeder Anrufer unterschiedliche Werte für eine benannte Richtlinie haben kann.

-   Umschließen Sie diese Richtlinie mit dem Befehl unteilbare Syncml so, dass die Richtlinieneinstellungen als eine einzelne Transaktion behandelt werden.

-   Unterstützte Vorgänge sind Add, Get löschen, und ersetzen.

-   Werttyp ist Zeichenfolge.

Mögliche Bereich und Richtliniennamen finden Sie unter [unterstützte Unternehmensrichtlinien](#bkmk-supportedpolicies) unten.

<a href="" id="device"></a>**Gerät**  
Gruppiert die ausgewerteten Richtlinien von allen Anbietern, die konfiguriert werden können. Unterstützte Vorgänge ist abrufen.

<a href="" id="device--areaname-"></a>**Gerät / ***_&lt;AreaName&gt;_**  
Der Bereichsgruppe, die durch eine einzelne Technologie unabhängig von der Anbieter konfiguriert werden kann. Unterstützte Vorgang ist Get.

<a href="" id="device--areaname---policyname-"></a>**Gerät /_&lt;AreaName&gt;_/****_&lt;PolicyName&gt; _**  
Gibt das Name/Wert-Paar in der Richtlinie verwendet. Unterstützte Vorgang ist Get.

## <a name="a-href-idbkmk-supportedpoliciesalist-of-ltareanamegtltpolicynamegt"></a><a href="" id="bkmk-supportedpolicies"></a>Liste der * &lt;AreaName&gt;*/*&lt;PolicyName&gt; *


<a href="" id="devicelock-devicepasswordenabled"></a>**DeviceLock/DevicePasswordEnabled**  
Gibt an, ob Gerätesperre aktiviert ist.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) - aktiviert

-   1 – deaktiviert

> **Wichtige**  
>Die Einstellung DevicePasswordEnabled muss auf 0 (Gerätekennworts ist aktiviert) festgelegt werden, für die folgenden Einstellungen wirksam werden:
>
> -   AllowSimpleDevicePassword
> -   MinDevicePasswordLength
> -   AlphanumericDevicePasswordRequired
> -   MaxDevicePasswordFailedAttempts
> -   MaxInactivityTimeDeviceLock
> -   MinDevicePasswordComplexCharacters

 

Über MDM und EAS unterstützt

Name der EAS-Richtlinie – DevicePasswordEnabled

Min-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-allowsimpledevicepassword"></a>**DeviceLock/AllowSimpleDevicePassword**  
Gibt an, ob Kennwörter wie "1111" oder "1234" zulässig sind.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zulässig.

-   1 (Standard) – zulässig.

Über MDM und EAS unterstützt

Name der EAS-Richtlinie – AllowSimpleDevicePassword

Min-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-mindevicepasswordlength"></a>**DeviceLock/MinDevicePasswordLength**  
Gibt die Mindestanzahl oder Zeichen in die PIN-NUMMER erforderlich.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, in dem

    4 &lt;= X &lt;= 16.

-   0-nicht erzwungen.

-   Standard: 4.

Über MDM und EAS unterstützt

EAS-Richtlinienname - MinDevicePasswordLength

Max-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-alphanumericdevicepasswordrequired"></a>**DeviceLock/AlphanumericDevicePasswordRequired**  
Bestimmt den Typ der erforderliche Kennwort. Diese Richtlinie gilt nur, wenn DevicedPasswordEnabled Richtlinie auf 0 (erforderlich) festgelegt ist.

In der folgenden Liste sind die unterstützten Werte:

-   0 – Alphanumerisches Kennwort erforderlich.

-   1 – numerische erforderliche Kennwort.

-   2 (Standard) - Benutzer können auswählen: numerische Kennwort oder Alphanumerisches Kennwort.

Über MDM und EAS unterstützt

Name der EAS-Richtlinie – AlphanumericDevicePasswordRequired

Min-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-devicepasswordexpiration"></a>**DeviceLock/DevicePasswordExpiration**  
Gibt an, wann das Kennwort (in Tagen) abläuft.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X wobei

    0 &lt;= X &lt;= 730.

-   0 (Standard) - Kennwörter laufen nicht ab.

Über MDM und EAS unterstützt

Name der EAS-Richtlinie – DevicePasswordExpiration

Wenn alle Richtlinienwerte, die = 0 then 0; Andernfalls ist Min Richtlinienwert die sicherste Wert

<a href="" id="devicelock-devicepasswordhistory"></a>**DeviceLock/DevicePasswordHistory**  
Gibt an, wie viele Kennwörter im Verlauf gespeichert werden können, die nicht verwendet werden kann.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, in dem

    0 &lt;= X &lt;=50.

-   Standard: 0

Über MDM und EAS unterstützt

EAS-Richtlinienname - DevicePasswordHistory

Max-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-maxdevicepasswordfailedattempts"></a>**DeviceLock/MaxDevicePasswordFailedAttempts**  
Die Anzahl der Fehler bei der Authentifizierung zulässig ist, bevor das Gerät wird bereinigt werden. Der Wert 0 deaktiviert Gerät Remotegerätzurücksetzung Funktionalität.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, in dem

    0 &lt;= X &lt;= 999.

-   Standard: 0. Das Gerät wird nie bereinigt, nachdem die falsche Kennwörter eingegeben werden.

Über MDM und EAS unterstützt

EAS-Richtlinienname - MaxDevicePasswordFailedAttempts

Wenn alle Richtlinienwerte, die = 0 then 0; Andernfalls ist Richtlinienwert Min den am stärksten eingeschränkten Wert.

<a href="" id="devicelock-maxinactivitytimedevicelock"></a>**DeviceLock/MaxInactivityTimeDeviceLock**  
Gibt die Zeitdauer (in Minuten) an, nach dem das Gerät sich im Leerlauf befindet, die bewirkt, dass des Geräts Kennwort gesperrt werden.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, in dem

    0 &lt;= X &lt;= 999.

-   0 (Standard) - kein Timeout definiert ist. "0" wird der Standardwert ist Mango Parität und vom interpretiert wird, wie "kein Timeout definiert ist."

Über MDM und EAS unterstützt

Name der EAS-Richtlinie – MaxInactivityTimeDeviceLock

Min-Richtlinienwert (mit Ausnahme von "0") ist der am stärksten eingeschränkte Wert.

<a href="" id="devicelock-mindevicepasswordcomplexcharacters"></a>**DeviceLock/MinDevicePasswordComplexCharacters**  
Die Anzahl der komplexe Elementtypen (Groß-und Kleinbuchstaben, Zahlen und Interpunktion) für ein sicheres Kennwort erforderlich.

In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, in dem

    1 &lt;= X &lt;= 4.

Der Standardwert ist 1.

Über MDM und EAS unterstützt.

EAS-Richtlinienname – MinDevicePasswordComplexCharacters

Max-Richtlinienwert ist die eingeschränkte

<a href="" id="devicelock-allowidlereturnwithoutpassword"></a>**DeviceLock/AllowIdleReturnWithoutPassword**  
Erzwingen, dass des Benutzers jedes Mal, wenn das Gerät aus Leerlauf gibt das Kennwort eingegeben.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 - Benutzer kann nicht auf den Timer Kennwort Kulanzfrist festgelegt und der Wert wird als "jedes Mal." festgelegt.

    1 (Standard) - Benutzer ist den Toleranzperiode-Zeitgeber Kennwort festlegen können.

Über den MDM und EAS unterstützt.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowwifi"></a>**WiFi/AllowWiFi**  
Zulassen Sie oder verweigern Sie Wi-Fi-Verbindung. (Exchange sowie – konfigurierbar Definition konsistent mit EAS-Definition werden.)

> **Hinweis**  Die Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – Verwendung Wi-Fi-Verbindung nicht zulässig ist.

-   1 (Standard) – Verwendung Wi-Fi-Verbindung zulässig ist.

Über den MDM und EAS unterstützt.

EAS-Richtlinienname – AllowWiFi

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowinternetsharing"></a>**WiFi/AllowInternetSharing**  
Zulassen Sie oder verbieten Sie des Internet freigeben.

(Exchange sowie – konfigurierbar Definition konsistent mit EAS-Definition werden.)

In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt nicht die Verwendung von Internet Sharing.

-   1 (Standard) – zulassen der Verwendung von Internet Sharing.

Über den MDM und EAS unterstützt.

Name der EAS-Richtlinie – AllowInternetSharing

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowautoconnecttowifisensehotspots"></a>**WiFi/AllowAutoConnectToWiFiSenseHotspots**  
Zulassen Sie oder Sperren Sie des Geräts Wi-Fi-Hotspots und Friend für soziale Netzwerke automatisch eine Verbindung herstellen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowwifihotspotreporting"></a>**WiFi/AllowWiFiHotSpotReporting**  
Zulassen Sie oder verweigern Sie Wi-Fi-Hotspot Informationen an Microsoft reporting. Nachdem nicht zulässig ist, kann nicht der Benutzer aktiviert werden.

In der folgenden Liste sind die unterstützten Werte:

-   0 – ist HotSpot reporting nicht zulässig.

-   1 (Standard) – ist HotSpot reporting zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowmanualwificonfiguration"></a>**WiFi/AllowManualWiFiConfiguration**  
Zulassen oder Herstellen einer Verbindung mit Wi-Fi außerhalb MDM Server installiert Netzwerke nicht zulassen.

> **Hinweis**  Die Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – No Wi-Fi-Verbindung außerhalb MDM bereitgestellten Netzwerk zulässig ist.

-   1 (Standard) – Hinzufügen von neuen Netzwerk SSIDs außerhalb der bereits MDM bereitgestellt Schriftarten zulässig ist.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allownfc"></a>**Konnektivität/AllowNFC**  
Zulassen oder Sperren in der Nähe Feld Kommunikation (NFK) auf dem Gerät.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt nicht NFK Funktionen.

-   1 (Standard) – Funktionen NFK zulassen.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowcellulardataroaming"></a>**Konnektivität/AllowCellularDataRoaming**  
Zugelassen oder verweigert Mobilfunk-Daten auf dem Gerät roaming.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowusbconnection"></a>**Konnektivität/AllowUSBConnection**  
Ermöglicht die USB-Verbindung zwischen dem Gerät und einem Computer zum Synchronisieren von Dateien mit dem Gerät oder Entwicklertools zum Bereitstellen und Debuggen von Anwendungen verwenden. Ändern diese Richtlinie wirkt USB aufgeladen sich nicht.

Media Transfer Protocol (MTP) und IP über USB sind deaktiviert, wenn diese Richtlinie erzwungen wird.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zulässig.

-   1 (Standard) - zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowvpnovercellular"></a>**Konnektivität/AllowVPNOverCellular**  
Diese Richtlinie gibt an, welche Art von zugrunde liegenden Verbindungen mit VPN zulässig ist.

In der folgenden Liste sind die unterstützten Werte:

-   0 - VPN ist nicht über Mobiltelefone zulässig.

-   1 (Standard) – VPN konnte Verbindung einschließlich Mobilfunk verwenden.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowvpnroamingovercellular"></a>**Konnektivität/AllowVPNRoamingOverCellular**  
Diese Richtlinie, wenn erzwungen, wird verhindert, dass das Gerät VPN verbinden, wenn das Gerät über Mobilfunknetze wechselt.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) - zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowbluetooth"></a>**Konnektivität/AllowBluetooth**  
Ermöglichen Sie Benutzern das Aktivieren von Bluetooth oder Einschränken des Zugriffs an.

In der folgenden Liste sind die möglichen Werte:

-   0 – Bluetooth deaktivieren.

-   1 – zulassen Sie die Konfiguration von Profilen Headset in 10 Mobile Windows für MDM und EAS deaktivieren Bluetooth nicht unterstützt, aber.

-   2 (Standard) – Bluetooth zulassen.

Über MDM und EAS unterstützt.

EAS-Richtlinienname – AllowBluetooth

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowstoragecard"></a>**System/AllowStorageCard**  
Steuert, ob der Benutzer berechtigt ist, verwenden Sie die Speicherkarte für Speicher des Geräts. Diese Einstellung verhindert nicht den programmgesteuerten Zugriff auf die Speicherkarte, es nur verhindert, dass des Benutzers über die Karte als Speicherort.

In der folgenden Liste sind die unterstützten Werte:

-   0 – SD-Karte Verwendung nicht zulässig. Dies verhindert nicht den programmgesteuerten Zugriff auf die Speicherkarte.

-   1 (Standard) – zulassen eine Speicherkarte.

Name der EAS-Richtlinie – AllowStorageCard

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowlocation"></a>**System/AllowLocation**  
Gibt an, ob einen Dienst Speicherort zulassen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowtelemetry"></a>**System/AllowTelemetry**  
Ermöglichen Sie das Gerät zum Senden von Telemetrie-Informationen (wie Software Quality Management (SQM) und Watson).

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 – zulässig, außer für sekundäre Anforderungen.

-   2 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowusertoresetphone"></a>**System/AllowUserToResetPhone**  
Gibt an, ob der Benutzer Factory des Telefons mit Control Panel und Hardware Tastenkombination zurücksetzen.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die möglichen Werte:

-   0 – nicht zulässig.

-   1 (Standard) - berechtigt, auf die werkseinstellungen zurückgesetzt.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowsaveasofofficefiles"></a>**Erfahrung/AllowSaveAsOfOfficeFiles**  
Gibt an, ob der Benutzer eine Datei auf dem Gerät als eine Office-Datei speichern.

> **Hinweis**  Diese Richtlinie wird nicht unterstützt und in Windows 10 veraltet.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowcopypaste"></a>**Erfahrung/AllowCopyPaste**  
Gibt an, ob kopieren und Einfügen ist zulässig.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowscreencapture"></a>**Erfahrung/AllowScreenCapture**  
Gibt an, ob Bildschirmaufnahme zulässig ist.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowvoicerecording"></a>**Erfahrung/AllowVoiceRecording**  
Gibt an, ob VoIP Aufzeichnung zulässig ist.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowcortana"></a>**Erfahrung/AllowCortana**  
Gibt an, ob auf dem Gerät Cortana zulässig ist.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowsyncmysettings"></a>**Erfahrung/AllowSyncMySettings**  
Ermöglicht das Unternehmen so verweigern Sie Roamingeinstellungen zwischen Geräten (in der ein Gerät). Wenn nicht erzwungen, kann unabhängig davon, ob roaming zulässig ist von anderen Faktoren abhängen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – Roaming nicht zulässig.

-   1 (Standard) – das Unternehmen erzwingt keine Einschränkungen roaming.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="-experience-allowmanualmdmunenrollment"></a>**Erfahrung/AllowManualMDMUnenrollment**  
Gibt an, ob der Benutzer das Jahrestag-Konto mithilfe der Jahrestag-Systemsteuerung löschen kann. Der MDM Server kann immer Remote das Konto löschen.

-   0 - nicht zulässig Server.

-   1 – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="-experience-allowsharingofofficefiles"></a>**Erfahrung/AllowSharingOfOfficeFiles**  
Gibt an, ob der Benutzer Office-Dateien freigeben.

In der folgenden Liste sind die unterstützten Werte:

> **Hinweis**  Diese Richtlinie wird in 10 Windows nicht unterstützt.

 

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="accounts-allowmicrosoftaccountconnection"></a>**Konten/AllowMicrosoftAccountConnection**  
Gibt an, ob Benutzer berechtigt ist, ein Konto MSA für verwandte ohne e-Mail-Verbindungsauthentifizierung und die Dienste zu verwenden.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="accounts-allowaddingnonmicrosoftaccountsmanually"></a>**Konten/AllowAddingNonMicrosoftAccountsManually**  
Gibt an, ob Benutzer berechtigt ist, nicht MSA e-Mail-Konten hinzufügen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="security-allowmanualrootcertificateinstallation"></a>**Security/AllowManualRootCertificateInstallation**  
Gibt an, ob der Benutzer manuell installieren Stamm und intermediate CAP Zertifikate berechtigt ist.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="security-requiredeviceencryption"></a>**Security/RequireDeviceEncryption**  
Ermöglicht es Unternehmen Zentralspeicher Verschlüsselung aktivieren. Beachten Sie, dass nach aktiviert, es über die Richtlinie deaktiviert werden kann.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – die Verschlüsselung ist nicht erforderlich.

-   1 – Verschlüsselung ist erforderlich.

Über MDM und EAS unterstützt.

EAS-Richtlinienname – RequireDeviceEncryption

Die meisten eingeschränktem Wert ist 1.

<a href="" id="browser-allowbrowser"></a>**Browser/AllowBrowser**  
Gibt an, ob Internet Explorer im Gerät zulässig ist.

> **Hinweis**  In dieser Richtlinie werden nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Über MDM und EAS unterstützt.

Name der EAS-Richtlinie – AllowBrowser

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="camera-allowcamera"></a>**Kamera/AllowCamera**  
Aktiviert oder deaktiviert die Kamera.

In der folgenden Liste sind die unterstützten Werte:

-   0 – ist die Verwendung der Kamera nicht zulässig.

-   1 (Standard) – ist die Verwendung der Kamera zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowstore"></a>**ApplicationManagement/AllowStore**  
Gibt an, ob die app-Store auf dem Gerät zulässig ist.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-applicationrestrictions"></a>**ApplicationManagement/ApplicationRestrictions**  
Ein XML-BLOB-, der angibt, dass Unternehmen Einschränkungen Anwendung auf das Gerät aufnehmen möchten. Es konnte app Zulassungsliste, app disallow Liste usw. Publisher-IDs zulässig sein. Eine Anwendung, die ausgeführt wird, kann nicht sofort beendet werden.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

> **Hinweis**  Liste bekannter Probleme:
-   Beim upgrade von Windows Phone 8.1 Geräte auf Windows 10 Mobile mit einer Liste der zulässigen apps verursacht unerwartetes Verhalten einiger Windows Posteingang apps blockiert. Um dieses Problem zu umgehen, müssen Sie den [Posteingang apps](applocker-csp.md#inboxappsandcomponents) einschließen, die Sie Ihrer Liste der zulässigen apps benötigen.

    Nachfolgend finden Sie zusätzliche Hinweise zum des Upgradeprozesses:

    -   Verwenden Sie Windows 10 Produkt-IDs für die apps im [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt.
    -   Verwenden Sie den neuen Namen der Microsoft Publisher (PublisherName = "CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S Washington, C = = US") und Publisher = "CN = Microsoft Windows, O = Microsoft Corporation, L = Redmond, S Washington, C = = US" Wenn Sie die Publisher-Richtlinie verwenden. Windows Phone 8.1 Herausgeber kann nicht entfernt werden, wenn Sie es verwenden.
    -   In der SyncML müssen Sie Kleinbuchstaben Produkt-ID verwenden.
    -   Führen Sie eine Product ID nicht doppelt Messaging und Skype Videofunktionen verwenden die gleichen Produkt-ID Duplikate führt zu einer Fehlermeldung.

    Ein Beispiel SyncML finden Sie [Beispiele](#examples).

-   Sie können nicht deaktivieren oder aktivieren **Kontakt Support** und **Feedback Windows** -apps mithilfe der ApplicationManagement/ApplicationRestrictions-Richtlinie, obwohl diese im [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt sind.
-   Wenn ApplicationManagement/ApplicationRestrictions Richtlinie für Windows 10 Mobile bereitgestellt wird, Installation und Aktualisierung von apps abhängig von der Microsoft-Frameworks möglicherweise mit Fehler 0x80073CF9 blockiert werden. Dieses Problem zu umgehen, müssen Sie die Microsoft-Framework-Id Ihrer Liste der zulässigen apps einbeziehen.

    ``` syntax
    <App ProductId="{00000000-0000-0000-0000-000000000000}" PublisherName="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" />
    ```

 

Werttyp ist chr.

Wert Evaluation - Regel, die Informationen für PolicyManager ist nicht transparent. Es ist keine am stärksten eingeschränkten Wert Bewertung. Sobald eine Änderung des Werts vorhanden ist, wird das Gerät analysiert den Knotenwert und erzwingt angegebene Richtlinien.

<a href="" id="applicationmanagement-allowdeveloperunlock"></a>**ApplicationManagement/AllowDeveloperUnlock**  
Gibt an, ob Developer entsperren am Gerät zulässig ist.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-allowsearchtouselocation"></a>**Suchen/AllowSearchToUseLocation**  
Gibt an, ob Standortinformationen Search genutzt werden kann.

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-safesearchpermissions"></a>**Suchen/SafeSearchPermissions**  
Gibt an, welche sicheres Suchen (Filterung Versender nicht jugendfreier Inhalte) erforderlich ist.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – Strict, höchsten Filterung anhand der Versender nicht jugendfreier Inhalte.

-   1 (Standard) – mäßig Filtern anhand der Versender nicht jugendfreier Inhalte (gültige Suchergebnisse werden nicht gefiltert.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-allowstoringimagesfromvisionsearch"></a>**Suchen/AllowStoringImagesFromVisionSearch**  
Gibt an, ob Bing Vision zum Speichern der Inhalt der Bilder erfasst bei Vision Bing-Suche zu ermöglichen.

> **Hinweis**  Diese Richtlinie wird in 10 Windows nicht unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

<a href="" id="abovelock-allowactioncenternotifications"></a>**AboveLock/AllowActionCenterNotifications**  
Gibt an, ob die Aktion Center-Benachrichtigungen über die Geräte Sperrbildschirm zulassen.

> **Hinweis**  Mit dieser Richtlinie wird nur in Windows 10 Mobile unterstützt.

 

In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.

-   1 (Standard) – zulässig.

Am stärksten eingeschränkten Wert ist 0.

## <a name="examples"></a>Beispiele


Es folgt ein Beispiel für ApplicationRestrictions SyncML zum Hinzufügen von allen Posteingang apps im [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt.

``` syntax
<SyncML>
  <SyncBody>
    <Atomic>
      <CmdID>144-0</CmdID>
      <Replace>
        <CmdID>144-1</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/PolicyManager/My/ApplicationManagement/ApplicationRestrictions</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
            <Type xmlns="syncml:metinf">text/plain</Type>
          </Meta>
          <Data>
&lt;AppPolicy Version=&quot;1&quot; xmlns=&quot;http://schemas.microsoft.com/phone/2013/policy&quot;&gt;
&lt;Allow&gt;

            &lt;!-- Alarms and clock --&gt;
            &lt;App ProductId=&quot;{44f7d2b4-553d-4bec-a8b7-634ce897ed5f}&quot; /&gt;
            &lt;!--Calculator --&gt;
            &lt;App ProductId=&quot;{b58171c6-c70c-4266-a2e8-8f9c994f4456}&quot; /&gt;
            &lt;!--Camera --&gt;
            &lt;App ProductId=&quot;{f0d8fefd-31cd-43a1-a45a-d0276db069f1}&quot; /&gt;
           
            &lt;App ProductId=&quot;{0db5fcff-4544-458a-b320-e352dfd9ca2b}&quot; /&gt;
            &lt;!--Cortana --&gt;
            &lt;App ProductId=&quot;{fd68dcf4-166f-4c55-a4ca-348020f71b94}&quot; /&gt;
            &lt;!--Excel --&gt;
            &lt;App ProductId=&quot;{ead3e7c0-fae6-4603-8699-6a448138f4dc}&quot; /&gt;
            &lt;!--Facebook --&gt;
            &lt;App ProductId=&quot;{82a23635-5bd9-df11-a844-00237de2db9e}&quot; /&gt;
            &lt;!--File Explorer --&gt;
            &lt;App ProductId=&quot;{c5e2524a-ea46-4f67-841f-6a9465d9d515}&quot; /&gt;
            &lt;!--FM Radio --&gt;
            &lt;App ProductId=&quot;{f725010e-455d-4c09-ac48-bcdef0d4b626}&quot; /&gt;
            &lt;!--Get Started --&gt;
            &lt;App ProductId=&quot;{b3726308-3d74-4a14-a84c-867c8c735c3c}&quot; /&gt;
            &lt;!--Groove Music --&gt;
            &lt;App ProductId=&quot;{d2b6a184-da39-4c9a-9e0a-8b589b03dec0}&quot; /&gt;
            &lt;!--Maps --&gt;
            &lt;App ProductId=&quot;{ed27a07e-af57-416b-bc0c-2596b622ef7d}&quot; /&gt;

            &lt;!--Messaging --&gt;
            &lt;App ProductId=&quot;{27e26f40-e031-48a6-b130-d1f20388991a}&quot; /&gt;
            &lt;!--Microsoft Edge --&gt;
            &lt;App ProductId=&quot;{395589fb-5884-4709-b9df-f7d558663ffd}&quot; /&gt;
            &lt;!--Money --&gt;
            &lt;App ProductId=&quot;{1e0440f1-7abf-4b9a-863d-177970eefb5e}&quot; /&gt;
            &lt;!--Movies and TV --&gt;
            &lt;App ProductId=&quot;{6affe59e-0467-4701-851f-7ac026e21665}&quot; /&gt;
            &lt;!--News --&gt;
            &lt;App ProductId=&quot;{9c3e8cad-6702-4842-8f61-b8b33cc9caf1}&quot; /&gt;
            &lt;!--OneDrive --&gt;
            &lt;App ProductId=&quot;{ad543082-80ec-45bb-aa02-ffe7f4182ba8}&quot; /&gt;
            &lt;!--OneNote --&gt;
            &lt;App ProductId=&quot;{ca05b3ab-f157-450c-8c49-a1f127f5e71d}&quot; /&gt;
            &lt;!--Outlook Mail Calendar --&gt;
            &lt;App ProductId=&quot;{a558feba-85d7-4665-b5d8-a2ff9c19799b}&quot; /&gt;
            &lt;!--People --&gt;
            &lt;App ProductId=&quot;{60be1fb8-3291-4b21-bd39-2221ab166481}&quot; /&gt;
            &lt;!--Phone (dialer) --&gt;
            &lt;App ProductId=&quot;{f41b5d0e-ee94-4f47-9cfe-3d3934c5a2c7}&quot; /&gt;
            &lt;!--Photos --&gt;
            &lt;App ProductId=&quot;{fca55e1b-b9a4-4289-882f-084ef4145005}&quot; /&gt;
            
            &lt;!--Podcasts --&gt;
            &lt;App ProductId=&quot;{c3215724-b279-4206-8c3e-61d1a9d63ed3}&quot; /&gt;
            &lt;!--Powerpoint --&gt;
            &lt;App ProductId=&quot;{b50483c4-8046-4e1b-81ba-590b24935798}&quot; /&gt;
            &lt;!--Settings --&gt;
            &lt;App ProductId=&quot;{2a4e62d8-8809-4787-89f8-69d0f01654fb}&quot; /&gt;
            &lt;!--Skype --&gt;
            &lt;App ProductId=&quot;{c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51}&quot; /&gt;
            &lt;!--Skype Video GUID is same as Messaging --&gt;
            &lt;!--Sports --&gt;
            &lt;App ProductId=&quot;{0f4c8c7e-7114-4e1e-a84c-50664db13b17}&quot; /&gt;
            &lt;!--Storage --&gt;
            &lt;App ProductId=&quot;{5b04b775-356b-4aa0-aaf8-6491ffea564d}&quot; /&gt;
            &lt;!--Store --&gt;
            &lt;App ProductId=&quot;{7d47d89a-7900-47c5-93f2-46eb6d94c159}&quot; /&gt;

            &lt;!--Voice recorder --&gt;
            &lt;App ProductId=&quot;{7311b9c5-a4e9-4c74-bc3c-55b06ba95ad0}&quot; /&gt;
            &lt;!--Wallet --&gt;
            &lt;App ProductId=&quot;{587a4577-7868-4745-a29e-f996203f1462}&quot; /&gt;
            &lt;!--Weather --&gt;
            &lt;App ProductId=&quot;{63c2a117-8604-44e7-8cef-df10be3a57c8}&quot; /&gt;
         
            &lt;App ProductId=&quot;{7604089d-d13f-4a2d-9998-33fc02b63ce3}&quot; /&gt;
            &lt;!--Word --&gt;
            &lt;App ProductId=&quot;{258f115c-48f4-4adb-9a68-1387e634459b}&quot; /&gt;
            &lt;!--Xbox --&gt;
            &lt;App ProductId=&quot;{b806836f-eebe-41c9-8669-19e243b81b83}&quot; /&gt;

            &lt;!-- CloudExperienceHost --&gt;
            &lt;App ProductId=&quot;{3a4fae89-7b7e-44b4-867b-f7e2772b8253}&quot; /&gt;
            &lt;!-- AAD BrokerPlugin --&gt;
            &lt;App ProductId=&quot;{e5f8b2c4-75ae-45ee-9be8-212e34f77747}&quot; /&gt;
            &lt;!-- Ringtone --&gt;
            &lt;App ProductId=&quot;{3e962450-486b-406b-abb5-d38b4ee7e6fe}&quot; /&gt;
            &lt;!-- Advanced Info --&gt;
            &lt;App ProductId=&quot;{b6e3e590-9fa5-40c0-86ac-ef475de98e88}&quot; /&gt;
            &lt;!-- Glance --&gt;
            &lt;App ProductId=&quot;{106e0a97-8b19-42cf-8879-a8ed2598fcbb}&quot; /&gt;
            &lt;!-- Connect --&gt;
            &lt;App ProductId=&quot;{af7d2801-56c0-4eb1-824b-dd91cdf7ece5}&quot; /&gt;
            &lt;!-- Miracast View --&gt;
            &lt;App ProductId=&quot;{906beeda-b7e6-4ddc-ba8d-ad5031223ef9}&quot; /&gt;
            &lt;!-- PrintDialog --&gt;
            &lt;App ProductId=&quot;{0d32eeb1-32f0-40da-8558-cea6fcbec4a4}&quot; /&gt;

            &lt;!-- Music downloads--&gt;
            &lt;App ProductId=&quot;{3da8a0c1-f7e5-47c0-a680-be8fd013f747}&quot; /&gt;
            &lt;!-- App downloads--&gt;
            &lt;App ProductId=&quot;{20bf77a0-19c7-4daa-8db5-bc3dfdfa44ac}&quot; /&gt;
            &lt;!-- Podcast downloads--&gt;
            &lt;App ProductId=&quot;{063773e7-f26f-4a92-81f0-aa71a1161e30}&quot; /&gt;
            &lt;!-- Email and accounts--&gt;
            &lt;App ProductId=&quot;{39cf127b-8c67-c149-539a-c02271d07060}&quot; /&gt;
            &lt;!-- Assigned Access Lock app--&gt;
            &lt;App ProductId=&quot;{b84f4722-313e-4f85-8f41-cf5417c9c5cb}&quot; /&gt;
            &lt;!-- Windows Hello Setup--&gt;
            &lt;App ProductId=&quot;{01293c37-72ec-3c8b-0eb3-1de4f7d0cdc4}&quot; /&gt;
            &lt;!-- Purchase Dialog--&gt;
            &lt;App ProductId=&quot;{c60e79ca-063b-4e5d-9177-1309357b2c3f}&quot; /&gt;
            &lt;!-- Xbox Identity Provider--&gt;
            &lt;App ProductId=&quot;{ba88225b-059a-45a2-a8eb-d3580283e49d}&quot; /&gt;
            &lt;!-- Block and Filter--&gt;
            &lt;App ProductId=&quot;{59553c14-5701-49a2-9909-264d034deb3d}&quot; /&gt;
            &lt;!-- Sharing--&gt;
            &lt;App ProductId=&quot;{b0894dfd-4671-4bb9-bc17-a8b39947ffb6}&quot; /&gt;
            &lt;!-- Setup wizard--&gt;
            &lt;App ProductId=&quot;{07d87655-e4f0-474b-895a-773790ad4a32}&quot; /&gt;
            &lt;!-- Phone Reset Dialog--&gt;
            &lt;App ProductId=&quot;{2864278d-09b5-46f7-b502-1c24139ecbdd}&quot; /&gt;
            &lt;!-- SaveRingtone--&gt;
            &lt;App ProductId=&quot;{d8cf8ec7-ec6d-4892-aab9-1e3a4b5fa24b}&quot; /&gt;
            &lt;!-- HAP Update Background Worker--&gt;
            &lt;App ProductId=&quot;{73c73cdd-4dea-462c-bd83-fa983056a4ef}&quot; /&gt;
            &lt;!-- Windows Default Lock Screen--&gt;
            &lt;App ProductId=&quot;{cdd63e31-9307-4ccb-ab62-1ffa5721b503}&quot; /&gt;
            &lt;!-- navigation bar--&gt;
            &lt;App ProductId=&quot;{2cd23676-8f68-4d07-8dd2-e693d4b01279}&quot; /&gt;
            &lt;!-- SSMHost--&gt;
            &lt;App ProductId=&quot;{e232aa77-2b6d-442c-b0c3-f3bb9788af2a}&quot; /&gt;
            &lt;!-- Bing lock images--&gt;
            &lt;App ProductId=&quot;{5f28c179-2780-41df-b966-27807b8de02c}&quot; /&gt;
            &lt;!-- CertInstaller--&gt;
            &lt;App ProductId=&quot;{4c4ad968-7100-49de-8cd1-402e198d869e}&quot; /&gt;
            &lt;!-- Age Out Worker--&gt;
            &lt;App ProductId=&quot;{09296e27-c9f3-4ab9-aa76-ecc4497d94bb}&quot; /&gt;
            &lt;!-- EnterpriseInstall App--&gt;
            &lt;App ProductId=&quot;{da52fa01-ac0f-479d-957f-bfe4595941cb}&quot; /&gt;
            &lt;!-- Hands-Free Activation--&gt;
            &lt;App ProductId=&quot;{df6c9621-e873-4e86-bb56-93e9f21b1d6f}&quot; /&gt;
            &lt;!-- Hands-Free Activation--&gt;
            &lt;App ProductId=&quot;{72803bd5-4f36-41a4-a349-e83e027c4722}&quot; /&gt;


            &lt;!--Field Medic --&gt;
            &lt;App ProductId=&quot;{73c58570-d5a7-46f8-b1b2-2a90024fc29c}&quot; /&gt;
            &lt;!--Windows Insider --&gt;
            &lt;App ProductId=&quot;{ed2b1421-6414-4544-bd8d-06d58ee402a5}&quot; /&gt;

            &lt;!-- Microsoft Frameworks --&gt;
            &lt;App ProductId=&quot;{00000000-0000-0000-0000-000000000000}&quot; PublisherName=&quot;CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US&quot; /&gt;

            &lt;/Allow&gt;
&lt;/AppPolicy&gt;

          </Data>
        </Item>
      </Replace>
    </Atomic>
    <Final />
  </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Referenz zum Konfiguration Service provider](configuration-service-provider-reference.md)

 

 






