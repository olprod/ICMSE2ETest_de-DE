---
title: EnterpriseAssignedAccess CSP
description: EnterpriseAssignedAccess CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5F88E567-77AA-4822-A0BC-3B31100639AA
ms.openlocfilehash: 949093cf61bf59d0fb90a89aa2dbc81db29430fd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseassignedaccess-csp"></a>EnterpriseAssignedAccess CSP


Der Dienstanbieter für EnterpriseAssignedAccess Konfiguration kann IT-Administratoren Einstellungen konfigurieren, z. B. Sprache und Designs, ein Gerät sperren, und Konfigurieren von benutzerdefinierten Layouts auf einem Gerät. Beispielsweise kann der Administrator ein Gerät sperren, sodass nur die angegebenen in eine Liste der Anwendung zur Verfügung stehen. Apps nicht in der Zulassungsliste werden bleiben Sie auf dem Gerät installiert, aber ausgeblendet und verhindert, dass starten.

> **Hinweis**   EnterpriseAssignedAccess CSP ist nur in Windows 10 Mobile unterstützt.

 

Weitere Informationen zur Interaktion mit dem Sperren XML zur Laufzeit finden Sie unter [**DeviceLockdownProfile Klasse**](https://msdn.microsoft.com/library/windows/hardware/mt186983).

Das folgende Diagramm zeigt den EnterpriseAssignedAccess Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) und OMA-Clientbereitstellung verwendet.

![Enterpriseassignedaccess csp](images/provisioning-csp-enterpriseassignedaccess.png)

In der folgenden Liste sind die Merkmale und Parameter.

<a href="" id="-vendor-msft-enterpriseassignedaccess-"></a>**. Hersteller/MSFT/EnterpriseAssignedAccess /**  
Der Stammknoten für den EnterpriseAssignedAccess Konfigurationsdienstanbieter. Unterstützte Vorgänge sind hinzufügen, löschen, Get und ersetzen.

<a href="" id="assignedaccess-"></a>**AssignedAccess /**  
Der übergeordnete Knoten der zugewiesenen Zugriffsrechten XML.

<a href="" id="assignedaccess-assignedaccessxml"></a>**AssignedAccess/AssignedAccessXml**  
Der XML-Code, der die zugewiesenen zugriffseinstellungen steuert, die auf das Gerät angewendet werden.

Unterstützte Vorgänge sind hinzufügen, löschen, Get und ersetzen.

In den Abschnitten Apps und -Einstellungen der Sperrung XML bilden eine Zulassungsliste. Jede Anwendung oder Einstellung, die nicht im AssignedAccessXML angegeben ist ist auf dem Gerät für Benutzer nicht verfügbar. In der folgenden Tabelle werden die Einträge der Sperrung XML beschrieben.

> **Wichtige**  
Wenn Sie die AssignedAccessXml im EnterpriseAssignedAccess CSP über eine MDM verwenden, der XML-CODE muss verwenden Escapezeichen, wie &lt; anstelle von &lt; , da es in einem XML-eingebettet ist. In den Beispielen finden Sie im Thema werden zur besseren Lesbarkeit formatiert.

Wenn Sie die AssignedAccessXml in einer Bereitstellung Paket mit dem Tool Windows Imaging und Konfiguration Designer (ICD) verwenden, verwenden Sie Escapezeichen nicht.

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Eintrag</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>ActionCenter</p></td>
<td><p>Sie können aktivieren oder deaktivieren die Action-Center (vormals Benachrichtigung Center) auf dem Gerät. Legen Sie auf "true" Action-Center aktivieren oder deaktivieren Sie die Action-Center auf False festgelegt.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;ActionCenter enabled=&quot;true&quot;&gt;&lt;/ActionCenter&gt;</code></pre>
<p>In Windows 10 Wenn die Aktion Center deaktiviert ist, werden über Lock-Benachrichtigungen und Popups auch deaktiviert. Wenn die Aktion Center aktiviert ist, werden auch die folgenden Richtlinien aktiviert:</p>
<ul>
<li>AboveLock/AllowActionCenterNotifications</li>
<li>AboveLock/AllowToasts</li>
</ul>
<p>Weitere Informationen zu diesen Richtlinien finden Sie unter [Richtlinie CSP](policy-configuration-service-provider.md)</p>
<p>Sie können auch das ActionCenter-Element, das das Standardverhalten außer Kraft setzen die folgenden optionalen Attribute hinzufügen:</p>
<ul>
<li>aboveLockToastEnabled</li>
<li>actionCenterNotificationEnabled</li>
</ul>
<p>Gültige Werte sind 0 (Richtlinie deaktiviert), 1 (Richtlinie aktiviert) und 1 (nicht festlegen, Richtlinie aktiviert ist).</p>
<p>In diesem Beispiel wird die Aktion Center ist aktiviert, und beide Richtlinien sind deaktiviert.</p>
<pre class="syntax" space="preserve"><code>&lt;ActionCenter enabled=&quot;true&quot; aboveLockToastEnabled=&quot;0&quot; actionCenterNotificationEnabled=&quot;0&quot;/&gt;</code></pre>
<p>Diese optionale Attribute werden unabhängig voneinander.</p>
<p>In diesem Beispiel Action Center ist aktiviert, die Benachrichtigungen Richtlinie deaktiviert ist und die Richtlinie Toast ist standardmäßig aktiviert, da sie nicht festgelegt ist.</p>
<pre class="syntax" space="preserve"><code>&lt;ActionCenter enabled=&quot;true&quot; actionCenterNotificationEnabled=&quot;0&quot;/&gt;</code></pre></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>StartScreenSize</p></td>
<td><p>Angeben der Größe des im Menü Start. Zusätzlich zu den Spalten 4/6 können Sie auch 4/6/8 je nach bildschirmauflösungen.</p>
<p>Gültige Werte:</p>
<ul>
<li><strong>Kleine</strong> wird die Breite auf 4 Spalten auf Computern mit kurzen Achse &lt;400epx oder 6 Spalten auf Geräten mit kurze Achse &gt;= 400epx.</li>
<li><strong>Große</strong> wird die Breite auf 6 Spalten auf Geräten mit kurzen Achse &lt;400epx oder 8 Spalten auf Geräten mit kurze Achse &gt;= 400epx.</li>
</ul>
<p>Wenn Sie vorhandene Sperrfunktionen XML haben, müssen Sie diese aktualisieren, wenn das Gerät hat &gt;= 400epx seine kurzen Achse, sodass Kacheln Start alle 8 Spalten ausfüllen können, wenn Sie verwenden möchten, verwenden Sie alle 8 Spalten anstelle von 6 oder 6 Spalten anstelle von 4.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;StartScreenSize&gt;Large&lt;/StartScreenSize&gt;</code></pre></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Anwendung	</p></td>
<td><p>Enthalten Sie die Produkt-ID für die jeweilige app, die auf dem Gerät verfügbar ist.</p>
<p>Sie können die Produkt-ID für eine lokal entwickelte app in der Datei AppManifest.XML der app suchen. Die Liste der Produkt-ID und AUMID finden Sie unter [ProductIDs in Windows 10 Mobile](#productid).</p>
<p>Um die Benachrichtigung für eine Windows-app zu aktivieren, müssen Sie die Anwendung AUMID in die Sperrung XML einbeziehen. Allerdings kann der Benutzer die Einstellung können Sie jederzeit aus der Benutzeroberfläche ändern.</p>
<pre class="syntax" space="preserve"><code>&lt;Application productId=&quot;{A558FEBA-85D7-4665-B5D8-A2FF9C19799B}&quot; aumid=&quot;microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.mail&quot;/&gt;</code></pre>
<img src="images/enterpriseassignedaccess-csp.png" alt="modern app notification" />
<p>Enthalten Sie zum Anzeigen einer app auf der Startseite PinToStart. Identifizieren Sie für apps, die auf dem Bildschirm Start fixiert eine Kachelgröße (kleinen, mittleren oder großen) und einen Speicherort. Die Größe des eine kleine Kachel ist 1 X 1 Spaltenzeile und eine große Kachel 4 x 2 ist eine mittlere Kachel ist 2 x 2.</p>
<p>Speicherort für die Kachel der erste Wert gibt an, der Spalte und der zweite Wert gibt der Zeile an. Der Wert <strong>0</strong> gibt die erste Spalte an, der Wert <strong>1</strong> gibt an, die zweite Spalte usw..</p>
<p>Schließen Sie AutoRun als ein Attribut so konfigurieren Sie die Anwendung automatisch ausgeführt.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;Application productId=&quot;{2A4E62D8-8809-4787-89F8-69D0F01654FB}&quot; autoRun=&quot;true&quot;&gt;
   &lt;PinToStart&gt;
      &lt;Size&gt;Large&lt;/Size&gt;
      &lt;Location&gt;
         &lt;LocationX&gt;0&lt;/LocationX&gt;
         &lt;LocationY&gt;2&lt;/LocationY&gt;
      &lt;/Location&gt;
   &lt;/PinToStart&gt;
&lt;/Application&gt;</code></pre>
<p>Mehrere App-Pakete Aktivieren von mehreren apps im gleichen Paket vorhanden sein. Da ProductIds-Paketen und nicht Applications identifiziert haben, reicht angeben einer ProductID-Wert nicht zum unterscheiden zwischen einzelnen apps in mehreren app-Paket. Versucht, aus einem mehrere app-Paket mit nur einer ProductId Anwendung enthalten kann unerwartetes Verhalten führen.</p>
<p>Verwenden Sie zum Anheften Clientanwendungen in mehreren app-Paketen unterstützt, eine AUMID-Parameter in Sperrfunktionen XML. Die Liste der Produkt-ID und AUMID finden Sie unter [ProductIDs in Windows 10 Mobile](#productid). Im folgende Beispiel veranschaulicht das so heften Sie Outlook-Mail und Outlook-Kalender an.</p>
<pre class="syntax" space="preserve"><code>&lt;Apps&gt;
    &lt;!-- Outlook Calendar --&gt;
    &lt;Application productId=&quot;{A558FEBA-85D7-4665-B5D8-A2FF9C19799B}&quot; 
aumid=&quot;microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.calendar&quot;&gt;
        &lt;PinToStart&gt;
            &lt;Size&gt;Large&lt;/Size&gt;
            &lt;Location&gt;
                &lt;LocationX&gt;1&lt;/LocationX&gt;
                &lt;LocationY&gt;4&lt;/LocationY&gt;
            &lt;/Location&gt;
        &lt;/PinToStart&gt;
    &lt;/Application&gt;
    &lt;!-- Outlook Mail--&gt;
    &lt;Application productId=&quot;{A558FEBA-85D7-4665-B5D8-A2FF9C19799B}&quot; 
aumid=&quot;microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.mail&quot;&gt;
        &lt;PinToStart&gt;
            &lt;Size&gt;Large&lt;/Size&gt;
            &lt;Location&gt;
                &lt;LocationX&gt;1&lt;/LocationX&gt;
                &lt;LocationY&gt;6&lt;/LocationY&gt;
            &lt;/Location&gt;
        &lt;/PinToStart&gt;
    &lt;/Application&gt;
&lt;/Apps&gt;</code></pre></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Folder</p></td>
<td><p>Ein Ordner in enthalten sein sollte &lt;Applications /&gt; Knoten zwischen mit anderen &lt;Anwendung /&gt; Knoten, gemeinsam die meisten Grammatik mit den Anwendungsknoten <strong>FolderId</strong> ist obligatorisch, <strong>FolderName</strong> ist optional, die den Namen des Ordners auf Start angezeigt wird. <strong>FolderId</strong> ist eine eindeutige Ganzzahl ohne Vorzeichen für jeden Ordner an.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;Application folderId=&quot;4&quot; folderName=&quot;foldername&quot;&gt;
    &lt;PinToStart&gt;
        &lt;Size&gt;Large&lt;/Size&gt;
        &lt;Location&gt;
            &lt;LocationX&gt;0&lt;/LocationX&gt;
            &lt;LocationY&gt;2&lt;/LocationY&gt;
        &lt;/Location&gt;
    &lt;/PinToStart&gt;
&lt;/Application&gt;</code></pre>
<p>Eine Anwendung, die im Ordner gehört würde ein optionales Attribut <strong>ParentFolderId</strong>, hinzufügen, die <strong>FolderId</strong> des Ordners zugeordnet ist. In diesem Fall wird der Speicherort dieser Anwendung innerhalb der Ordner befinden.</p>
<pre class="syntax" space="preserve"><code>&lt;Application productId=&quot;{2A4E62D8-8809-4787-89F8-69D0F01654FB}&quot;&gt;
    &lt;PinToStart&gt;
        &lt;Size&gt;Medium&lt;/Size&gt;
        &lt;Location&gt;
            &lt;LocationX&gt;0&lt;/LocationX&gt;
            &lt;LocationY&gt;0&lt;/LocationY&gt;
        &lt;/Location&gt;
        &lt;ParentFolderId&gt;2&lt;/ParentFolderId&gt;
    &lt;/PinToStart&gt;
&lt;/Application&gt;</code></pre></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Einstellungen</p></td>
<td><p><strong>Seiten mit</strong></p>
<p>Starten im Windows-10, Version 1511, können Sie die folgenden Einstellungen für Seiten in der Sperrung XML-Datei angeben.</p>
<div class="alert">
<strong>Wichtig</strong>  Geben Sie einen Group-Eintrag ohne einen Eintrag für die Seite nicht an, da dies ein Verhalten führt.
</div>
<div>
 
</div>
<ul>
<li>System (Hauptmenü) - SettingsPageGroupPCSystem
<ul>
<li>Anzeige - SettingsPageDisplay</li>
<li>Benachrichtigungen &amp; Aktionen - SettingsPageAppsNotifications</li>
<li>Telefon - SettingsPageCalls</li>
<li>Messaging - SettingsPageMessaging</li>
<li>Batterie Bildschirmschoner - SettingsPageBatterySaver</li>
<li>Speicher - SettingsPageStorageSenseStorageOverview</li>
<li>Gesteuerte Modus - SettingsPageDrivingMode</li>
<li>Offline-Karten - SettingsPageMaps</li>
<li>Informationen zum - SettingsPagePCSystemInfo</li>
<li>Apps für Websites - SettingsPageAppsForWebsites</li>
</ul></li>
<li>Geräte (Hauptmenü) - SettingsPageGroupDevices
<ul>
<li>Standardkamera - SettingsPagePhotos</li>
<li>Bluetooth - SettingsPagePCSystemBluetooth</li>
<li>NFK - SettingsPagePhoneNFC</li>
<li>Maus - SettingsPageMouseTouchpad</li>
<li>USB - SettingsPageUsb</li>
</ul></li>
<li>Netzwerk- und Wireless (Hauptmenü) - SettingsPageGroupNetwork
<ul>
<li>Mobiltelefone und SIM - SettingsPageNetworkCellular</li>
<li>Wi-Fi - SettingsPageNetworkWiFi</li>
<li>Flugzeug-Modus - SettingsPageNetworkAirplaneMode</li>
<li>Datennutzungs-- SettingsPageDataSenseOverview</li>
<li>Mobile Hotspot - SettingsPageNetworkMobileHotspot</li>
<li>VPN - SettingsPageNetworkVPN</li>
<li></li>
</ul></li>
<li>Personalisierung (Hauptmenü) - SettingsPageGroupPersonalization
<ul>
<li>Start - SettingsPageBackGround</li>
<li>Farben - SettingsPageColors</li>
<li>Sounds - SettingsPageSounds</li>
<li>Sperren des Bildschirms - SettingsPageLockscreen</li>
<li>Blick - SettingsPageGlance</li>
<li>Navigationsleiste - SettingsNavigationBar</li>
</ul></li>
<li>Konten (Hauptmenü) - SettingsPageGroupAccounts
<ul>
<li>Ihr Konto - SettingsPageAccountsPicture</li>
<li>Anmeldeoptionen - SettingsPageAccountsSignInOptions</li>
<li>Access – SettingsPageWorkAccess arbeiten</li>
<li>Synchronisieren Sie Ihre Einstellungen - SettingsPageAccountsSync</li>
<li>Apps Ecke * - SettingsPageAppsCorner</li>
<li>E-Mail - SettingsPageAccountsEmailApp</li>
</ul></li>
<li>Zeit- und Sprache (Hauptmenü) - SettingsPageGroupTimeRegion
<ul>
<li>Datum und Uhrzeit - SettingsPageTimeRegionDateTime</li>
<li>Language - SettingsPageTimeLanguage</li>
<li>Region - SettingsPageRegion</li>
<li>Tastatur - SettingsPageKeyboard</li>
<li>Speech - SettingsPageSpeech</li>
</ul></li>
<li>Einfacher Zugriff (Hauptmenü) - SettingsPageGroupEaseOfAccess
<ul>
<li>Die Sprachausgabe - SettingsPageEaseOfAccessNarrator</li>
<li>Bildschirmlupe - SettingsPageEaseOfAccessMagnifier</li>
<li>Hoher Kontrast - SettingsPageEaseOfAccessHighContrast</li>
<li>Untertitel - SettingsPageEaseOfAccessClosedCaptioning</li>
<li>Weitere Optionen - SettingsPageEaseOfAccessMoreOptions</li>
</ul></li>
<li>Datenschutz (Hauptmenü) - SettingsPageGroupPrivacy
<ul>
<li>Standort - SettingsPagePrivacyLocation</li>
<li>Kamera - SettingsPagePrivacyWebcam</li>
<li>Mikrofon - SettingsPagePrivacyMicrophone</li>
<li>Motion - SettingsPagePrivacyMotionData</li>
<li>Speech Freihand und eingeben - SettingsPagePrivacyPersonalization</li>
<li>Kontoinformationen - SettingsPagePrivacyAccountInfo</li>
<li>Kontakte - SettingsPagePrivacyContacts</li>
<li>Kalender - SettingsPagePrivacyCalendar</li>
<li>Messaging - SettingsPagePrivacyMessaging</li>
<li>Sender - SettingsPagePrivacyRadios</li>
<li>Hintergrund-apps – SettingsPagePrivacyBackgroundApps</li>
<li>Zubehör apps – SettingsPageAccessories</li>
<li>ID der Werbung - SettingsPagePrivacyAdvertisingId</li>
<li>Andere Geräte - SettingsPagePrivacyCustomPeripherals</li>
<li>Feedback &amp; Diagnose - SettingsPagePrivacySIUFSettings</li>
<li>Die Anrufliste... - SettingsPagePrivacyCallHistory</li>
<li>E-Mail - SettingsPagePrivacyEmail</li>
<li>Telefonanruf - SettingsPagePrivacyPhoneCall</li>
<li>Benachrichtigungen - SettingsPagePrivacyNotifications</li>
<li>Für Parts für Benutzerdefinierte - SettingsPagePrivacyCDP</li>
</ul></li>
<li>Update- und Sicherheit (Hauptmenü) - SettingsPageGroupRestore
<ul>
<li>Update - SettingsPageRestoreMusUpdate Telefon</li>
<li>Backup - SettingsPageRestoreOneBackup</li>
<li>Hier finden Sie Mein Telefon - SettingsPageFindMyDevice</li>
<li>Für Entwickler – SettingsPageSystemDeveloperOptions</li>
<li>Windows-Insider Programm - SettingsPageFlights</li>
<li>Geräteverschlüsselung - SettingsPageGroupPCSystemDeviceEncryption</li>
</ul></li>
<li>OEM (Hauptmenü) - SettingsPageGroupExtensibility
<ul>
<li>Erweiterbarkeit - SettingsPageExtensibility</li>
</ul></li>
</ul>
<p><strong>Einstellungen für schnelles Aktion</strong></p>
<p>Starten im Windows-10, Version 1511, können Sie die folgenden Einstellungen für schnelles-Aktion in der Sperrung-XML-Datei angeben. Der folgenden Liste werden die Einstellungen für schnelles Aktion und Seite mit den servereinstellungen Abhängigkeiten (Seite und Gruppe). Die Gruppe abhängigen Einstellungen und Seiten werden automatisch hinzugefügt, wenn das schnelle Action-Element im XML der Sperrung angegeben ist.</p>
<ul>
<li><p>SystemSettings_System_Display_QuickAction_Brightness</p>
<p>Abhängigkeiten - SettingsPageSystemDisplay, SettingsPageDisplay</p></li>
<li><p>SystemSettings_System_Display_Internal_Rotation</p>
<p>Abhängigkeiten - SettingsPageSystemDisplay, SettingsPageDisplay</p></li>
<li><p>SystemSettings_QuickAction_WiFi</p>
<p>Abhängigkeiten - SettingsPageGroupNetwork, SettingsPageNetworkWiFi</p></li>
<li><p>SystemSettings_QuickAction_InternetSharing</p>
<p>Abhängigkeiten - SettingsPageGroupNetwork, SettingsPageInternetSharing</p></li>
<li><p>SystemSettings_QuickAction_CellularData</p>
<p>Abhängigkeiten - SettingsPageGroupNetwork, SettingsPageNetworkCellular</p></li>
<li><p>SystemSettings_QuickAction_AirplaneMode</p>
<p>Abhängigkeiten - SettingsPageGroupNetwork, SettingsPageNetworkAirplaneMode</p></li>
<li><p>SystemSettings_Privacy_LocationEnabledUserPhone</p>
<p>Abhängigkeiten - SettingsGroupPrivacyLocationGlobals, SettingsPagePrivacyLocation</p></li>
<li><p>SystemSettings_Network_VPN_QuickAction</p>
<p>Abhängigkeiten - SettingsPageGroupNetwork, SettingsPageNetworkVPN</p></li>
<li><p>SystemSettings_Launcher_QuickNote</p>
<p>Abhängigkeiten - keine</p></li>
<li><p>SystemSettings_Flashlight_Toggle</p>
<p>Abhängigkeiten - keine</p></li>
<li><p>SystemSettings_Device_BluetoothQuickAction</p>
<p>Abhängigkeiten - SettingsPageGroupDevices, SettingsPagePCSystemBluetooth</p></li>
<li><p>SystemSettings_BatterySaver_LandingPage_OverrideControl</p>
<p>Abhängigkeiten - BatterySaver_LandingPage_SettingsConfiguration, SettingsPageBatterySaver</p></li>
<li><p>QuickActions_Launcher_DeviceDiscovery</p>
<p>Abhängigkeiten - keine</p></li>
<li><p>QuickActions_Launcher_AllSettings</p>
<p>Abhängigkeiten - keine</p></li>
<li><p>SystemSettings_QuickAction_QuietHours</p>
<p>Abhängigkeiten - keine</p></li>
<li><p>SystemSettings_QuickAction_Camera</p>
<p>Abhängigkeiten - keine</p></li>
</ul>
<p>In diesem Beispiel werden alle Einstellungsseiten und Einstellungen für schnelles Aktion zulässig. Ein leeres &lt;Einstellungen&gt; Knoten gibt an, dass keine der Einstellungen blockiert werden.</p>
<pre class="syntax" space="preserve"><code>&lt;Settings&gt;
&lt;/Settings&gt;</code></pre>
<p>In diesem Beispiel werden alle System Einstellung Seiten aktiviert. Beachten Sie, dass die Gruppe der System-Seite und alle von der Unterseite Systemnamen hinzugefügt wird.</p>
<pre class="syntax" space="preserve"><code>&lt;Settings&gt; 
  &lt;System name=&quot;SettingsPageGroupPCSystem&quot; /&gt; 
  &lt;System name=&quot;SettingsPageDisplay&quot; /&gt; 
  &lt;System name=&quot;SettingsPageAppsNotifications&quot; /&gt;
  &lt;System name=&quot;SettingsPageCalls&quot; /&gt;
  &lt;System name=&quot;SettingsPageMessaging&quot; /&gt; 
  &lt;System name=&quot;SettingsPageBatterySaver&quot; /&gt; 
  &lt;System name=&quot;SettingsPageStorageSenseStorageOverview&quot; /&gt;
  &lt;System name=&quot;SettingsPageGroupPCSystemDeviceEncryption&quot; /&gt; 
  &lt;System name=&quot;SettingsPageDrivingMode&quot; /&gt; 
  &lt;System name=&quot;SettingsPagePCSystemInfo&quot; /&gt; 
 &lt;/Settings&gt;</code></pre>
<p>Um den Zugriff auf alle Einstellungen im System zu entfernen, wird die Anwendung nicht einfach in der app-Liste für eine bestimmte Rolle aufgelistet.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Schaltflächen</p></td>
<td><p>In der folgenden Liste identifiziert die Tasten auf dem Gerät, das in <strong>ButtonLockdownList</strong>sperren können. Wenn ein Benutzer eine Schaltfläche, die in der Liste der Sperrung ist tippt, passiert nichts.</p>
<ul>
<li><p>Start</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Sperren der Schaltfläche Start verhindert, dass nur das Drücken und halten-Ereignis.</p>
</div>
<div>
 
</div></li>
<li><p>Zurück</p></li>
<li><p>Search</p></li>
<li><p>Kamera</p></li>
<li><p>Custom1</p></li>
<li><p>Custom2</p></li>
<li><p>Custom3</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Benutzerdefinierte Schaltflächen sind Hardware-Schaltflächen, die Geräte von OEMs hinzugefügt werden können.</p>
</div>
<div>
 
</div></li>
</ul>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;Buttons&gt;
   &lt;ButtonLockdownList&gt;
      &lt;!-- Lockdown all buttons --&gt;
         &lt;Button name=&quot;Search&quot;&gt;
         &lt;/Button&gt;
         &lt;Button name=&quot;Camera&quot;&gt;
         &lt;/Button&gt;
         &lt;Button name=&quot;Custom1&quot;&gt;
         &lt;/Button&gt;
         &lt;Button name=&quot;Custom2&quot;&gt;
         &lt;/Button&gt;
         &lt;Button name=&quot;Custom3&quot;&gt;
         &lt;/Button&gt;
   &lt;/ButtonLockdownList&gt;</code></pre>
<p>Die Such- und benutzerdefinierten Schaltflächen <em>neu zugeordnet</em> werden können, oder so konfiguriert, dass um eine bestimmte Anwendung zu öffnen. Schaltfläche Neuzuordnen wirkt sich auf das Gerät und gilt für alle Benutzer.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Sperrung Einstellungen für eine Schaltfläche, pro Benutzerrolle, werden unabhängig von der Schaltfläche Zuordnung angewendet.</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>Warnung</strong>  
<p>Neuzuordnen Schaltfläche können einen Benutzer zum Öffnen einer Anwendung, die nicht in der Zulassungsliste enthalten ist. Verwenden Sie Schaltfläche Sperre nach unten, um Anwendungszugriff für eine Benutzerrolle zu verhindern.</p>
</div>
<div>
 
</div>
<p>Um eine Schaltfläche im Sperrfunktionen XML zuordnen möchten, geben Sie den Namen der Schaltfläche, die Schaltflächenereignis (in der Regel &quot;drücken&quot;), und die Produkt-ID für die Anwendung die Schaltfläche wird geöffnet.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;ButtonRemapList&gt;
   &lt;Button name=&quot;Search&quot;&gt;
      &lt;ButtonEvent name=&quot;Press&quot;&gt;
         &lt;!-- Alarms --&gt;
         &lt;Application productId=&quot;{08179793-ED2E-45EA-BA12-BDE3EE9C3CE3}&quot; parameters=&quot;&quot; /&gt;
          &lt;/ButtonEvent&gt;
   &lt;/Button&gt;
&lt;/ButtonRemapList&gt;</code></pre>
<p><strong>Deaktivieren der Navigationsschaltflächen</strong></p>
<p>Um in Sperrfunktionen XML Navigationsschaltflächen (z. B. Heim- oder Back) deaktivieren Sie geben den Namen (beispielsweise Start) und die Schaltflächenereignis (in der Regel &quot;drücken&quot;).</p>
<p>Der folgende Abschnitt enthält eine Sperrung XML-Beispieldatei, die zeigt, wie Sie Navigationsschaltflächen deaktivieren.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;HandheldLockdown version=&quot;1.0&quot; &gt;
    &lt;Default&gt;
        &lt;ActionCenter enabled=&quot;false&quot; /&gt;
        &lt;Apps&gt;
            &lt;!-- Settings --&gt;
            &lt;Application productId=&quot;{2A4E62D8-8809-4787-89F8-69D0F01654FB}&quot;&gt;
                &lt;PinToStart&gt;
                    &lt;Size&gt;Large&lt;/Size&gt;
                    &lt;Location&gt;
                        &lt;LocationX&gt;0&lt;/LocationX&gt;
                        &lt;LocationY&gt;0&lt;/LocationY&gt;
                    &lt;/Location&gt;
                &lt;/PinToStart&gt;
            &lt;/Application&gt;

            &lt;!-- Phone Apps --&gt;
            &lt;Application productId=&quot;{F41B5D0E-EE94-4F47-9CFE-3D3934C5A2C7}&quot;&gt;
                &lt;PinToStart&gt;
                    &lt;Size&gt;Small&lt;/Size&gt;
                    &lt;Location&gt;
                        &lt;LocationX&gt;2&lt;/LocationX&gt;
                        &lt;LocationY&gt;2&lt;/LocationY&gt;
                    &lt;/Location&gt;
                &lt;/PinToStart&gt;
            &lt;/Application&gt;
        &lt;/Apps&gt;
        &lt;Buttons&gt;
            &lt;ButtonLockdownList&gt;
                &lt;Button name=&quot;Start&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Back&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Search&quot;&gt;
                    &lt;ButtonEvent name=&quot;All&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Camera&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom1&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom2&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom3&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
            &lt;/ButtonLockdownList&gt;
            &lt;ButtonRemapList /&gt;
        &lt;/Buttons&gt;
        &lt;MenuItems&gt;
            &lt;DisableMenuItems/&gt;
        &lt;/MenuItems&gt;
        &lt;Settings&gt;
        &lt;/Settings&gt;
        &lt;Tiles&gt;
            &lt;EnableTileManipulation/&gt;
        &lt;/Tiles&gt;
        &lt;StartScreenSize&gt;Small&lt;/StartScreenSize&gt;
    &lt;/Default&gt;
&lt;/HandheldLockdown&gt;</code></pre></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>MenuItems</p></td>
<td><p>Verwenden Sie <strong>DisableMenuItems</strong> , um die Verwendung des Kontextmenüs, zu verhindern, die angezeigt wird, wenn ein Benutzer drückt und verfügt über eine Anwendung in der Liste alle Programme. Sie können diesen Eintrag einschließen, in dem Standardprofil und alle zusätzlichen Rolle Benutzerprofile, die Sie erstellen.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;MenuItems&gt;
   &lt;DisableMenuItems/&gt;
&lt;/MenuItems&gt;</code></pre>
<div class="alert">
<strong>Wichtige</strong>  
<p>Wenn <strong>DisableMenuItems</strong> nicht in einem Profil enthalten ist, können Benutzer des Profils apps deinstallieren.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Kacheln</p></td>
<td><p><strong>Drehen Single Sign-On Kachel Bearbeitung</strong></p>
<p>Standardmäßig unter Zugriff zugewiesen Kachel Manipulation ist deaktiviert (blockiert), und nur verfügbar, wenn im Profil des Benutzers aktiviert.</p>
<p>Wenn Kachel Manipulation im Profil des Benutzers aktiviert ist, können sie Pin/lösen, verschieben und Größe basierte auf ihren Vorlieben Kacheln. Wenn mehrere Benutzer ein Gerät verwenden, und Sie Kachel Manipulation für mehrere Benutzer aktivieren möchten, müssen Sie es für jeden Benutzer in ihrem Benutzerprofil aktivieren.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Wenn ein Gerät aus und dann wieder auf die Kacheln zurücksetzen auf die vordefinierten das Layout aktiviert ist. Wenn ein Gerät nur ein Profil hat, ist die einzige Möglichkeit, die Kacheln Zurücksetzen deaktivieren und aktivieren Sie dann auf dem Gerät. Wenn ein Gerät mehrere Profile verfügt, setzt das Gerät die Kacheln auf das vordefinierte Layout basierend auf dem Profil des angemeldeten Benutzers.</p>
</div>
<div>
 
</div>
<p>Die folgende Beispieldatei enthält Konfiguration für Kachel Bearbeitung aktivieren.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Kachel Manipulation ist deaktiviert, wenn Ihnen keine <code>&lt;Tiles&gt;</code> Knoten in Sperrfunktionen XML, oder wenn Sie eine <code>&lt;Tiles&gt;</code> Knoten jedoch nicht die <code>&lt;EnableTileManipulation/&gt;</code> Knoten.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;HandheldLockdown version=&quot;1.0&quot; &gt;
    &lt;Default&gt;
        &lt;ActionCenter enabled=&quot;false&quot; /&gt;
        &lt;Apps&gt;
            &lt;!-- Settings --&gt;
            &lt;Application productId=&quot;{2A4E62D8-8809-4787-89F8-69D0F01654FB}&quot;&gt;
                &lt;PinToStart&gt;
                    &lt;Size&gt;Large&lt;/Size&gt;
                    &lt;Location&gt;
                        &lt;LocationX&gt;0&lt;/LocationX&gt;
                        &lt;LocationY&gt;0&lt;/LocationY&gt;
                    &lt;/Location&gt;
                &lt;/PinToStart&gt;
            &lt;/Application&gt;

            &lt;!-- Phone Apps --&gt;
            &lt;Application productId=&quot;{F41B5D0E-EE94-4F47-9CFE-3D3934C5A2C7}&quot;&gt;
                &lt;PinToStart&gt;
                    &lt;Size&gt;Small&lt;/Size&gt;
                    &lt;Location&gt;
                        &lt;LocationX&gt;2&lt;/LocationX&gt;
                        &lt;LocationY&gt;2&lt;/LocationY&gt;
                    &lt;/Location&gt;
                &lt;/PinToStart&gt;
            &lt;/Application&gt;
        &lt;/Apps&gt;
        &lt;Buttons&gt;
            &lt;ButtonLockdownList&gt;
                &lt;Button name=&quot;Start&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Back&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Search&quot;&gt;
                    &lt;ButtonEvent name=&quot;All&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Camera&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom1&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom2&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
                &lt;Button name=&quot;Custom3&quot;&gt;
                    &lt;ButtonEvent name=&quot;Press&quot; /&gt;
                    &lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;
                &lt;/Button&gt;
            &lt;/ButtonLockdownList&gt;
            &lt;ButtonRemapList /&gt;
        &lt;/Buttons&gt;
        &lt;MenuItems&gt;
            &lt;DisableMenuItems/&gt;
        &lt;/MenuItems&gt;
        &lt;Settings&gt;
        &lt;/Settings&gt;
        &lt;Tiles&gt;
            &lt;EnableTileManipulation/&gt;
        &lt;/Tiles&gt;
        &lt;StartScreenSize&gt;Small&lt;/StartScreenSize&gt;
    &lt;/Default&gt;
&lt;/HandheldLockdown&gt;</code></pre></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>CSP Testprogramm</p></td>
<td><p>Kryptografiedienstanbieter auf dem Gerät pro Benutzerrolle ausgeführt werden können. Sie können mithilfe dieser Rolle bestimmte Richtlinien, wie das Farbschema ändern, wenn ein Administrator auf dem Gerät anmeldet implementieren oder Konfigurationen pro Rolle festlegen.</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="lockscreenwallpaper-"></a>**LockscreenWallpaper /**  
Der übergeordnete Knoten der Sperre Bildschirm bezogene Parameter, die Administratoren Abfrage lassen und das Bild des Sperre auf Geräten verwalten. Unterstützte Vorgänge sind hinzufügen, löschen, Get und ersetzen.

<a href="" id="lockscreenwallpaper-bgfilename"></a>**LockscreenWallpaper/BGFileName**  
Der Dateiname des Bildschirms sperren. Die Bilddatei für das Blockieren des Bildschirms kann im JPG oder PNG-Format sein und darf nicht mehr als 2 MB. Der Dateiname kann auch in diesem Format (UNC = Universal Naming Convention) sein, in dem Fall das Gerät aus dem freigegebenen Netzwerk übertragen und dann als die Sperre Bildschirm Hintergrundbild werden festgelegt.

Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="theme-"></a>**Design /**  
Der übergeordnete Knoten des Design-bezogenen Parameter.

Unterstützte Vorgänge sind hinzufügen, löschen, Get und ersetzen.

<a href="" id="theme-themebackground"></a>**Theme/ThemeBackground**  
Gibt an, ob die Hintergrundfarbe hell oder dunkel ist. Legen Sie auf **0** für Licht. Dunkel **1** festgelegt.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="theme-themeaccentcolorid"></a>**Design/ThemeAccentColorID**  
Die Akzentfarbe, die als Vordergrundfarbe für Kacheln, Steuerelemente und andere visuelle Elemente auf dem Gerät angewendet. In der folgenden Tabelle sind die möglichen Werte.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>0</strong></p></td>
<td><p>Gelbgrün</p></td>
</tr>
<tr class="even">
<td><p><strong>1</strong></p></td>
<td><p>Grün</p></td>
</tr>
<tr class="odd">
<td><p><strong>2</strong></p></td>
<td><p>Smaragdgrün</p></td>
</tr>
<tr class="even">
<td><p><strong>3</strong></p></td>
<td><p>Blaugrün (Viridian)</p></td>
</tr>
<tr class="odd">
<td><p><strong>4</strong></p></td>
<td><p>Cyan (Blau)</p></td>
</tr>
<tr class="even">
<td><p><strong>5</strong></p></td>
<td><p>Cobalt</p></td>
</tr>
<tr class="odd">
<td><p><strong>6</strong></p></td>
<td><p>Indigoblau</p></td>
</tr>
<tr class="even">
<td><p><strong>7</strong></p></td>
<td><p>Violett (Violett)</p></td>
</tr>
<tr class="odd">
<td><p><strong>8</strong></p></td>
<td><p>Rosa</p></td>
</tr>
<tr class="even">
<td><p><strong>9</strong></p></td>
<td><p>Magenta</p></td>
</tr>
<tr class="odd">
<td><p><strong>10</strong></p></td>
<td><p>Karmesinrot</p></td>
</tr>
<tr class="even">
<td><p><strong>11</strong></p></td>
<td><p>Rot</p></td>
</tr>
<tr class="odd">
<td><p><strong>12</strong></p></td>
<td><p>Orange (Mango)</p></td>
</tr>
<tr class="even">
<td><p><strong>13</strong></p></td>
<td><p>Orange</p></td>
</tr>
<tr class="odd">
<td><p><strong>14</strong></p></td>
<td><p>Gelb</p></td>
</tr>
<tr class="even">
<td><p><strong>15</strong></p></td>
<td><p>Braun</p></td>
</tr>
<tr class="odd">
<td><p><strong>16</strong></p></td>
<td><p>Ocker</p></td>
</tr>
<tr class="even">
<td><p><strong>17</strong></p></td>
<td><p>Stahlblau</p></td>
</tr>
<tr class="odd">
<td><p><strong>18</strong></p></td>
<td><p>Mauve</p></td>
</tr>
<tr class="even">
<td><p><strong>19</strong></p></td>
<td><p>Siena</p></td>
</tr>
<tr class="odd">
<td><p><strong>101</strong> über <strong>104</strong></p></td>
<td><p>Optionale Farben, gemäß der Definition durch den OEM</p></td>
</tr>
<tr class="even">
<td><p><strong>151</strong></p></td>
<td><p>Benutzerdefinierte Akzentfarbe für Unternehmen</p></td>
</tr>
</tbody>
</table>

 

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="theme-themeaccentcolorvalue"></a>**Design/ThemeAccentColorValue**  
Eine Zeichenfolge mit 6 Zeichen für die Akzentfarbe für Steuerelemente und andere visuelle Elemente gelten.

Geben Sie die Verwendung einer benutzerdefinierten Akzentfarbe für Enterprise **151** für *ThemeAccentColorID* vor *ThemeAccentColorValue* in Sperrfunktionen XML. *ThemeAccentColorValue* konfiguriert die benutzerdefinierten Akzentfarbe Hexadezimalwerte für Red, Green und Blue, RRGGBB-Format verwenden. Geben Sie beispielsweise FF0000 für Rot.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="persistdata"></a>**PersistData**  
In Windows 10 unterstützt nicht.

Der übergeordnete Knoten an, ob die Daten zu speichern, die auf dem Gerät bereitgestellt wurde.

<a href="" id="persistdata-persistprovisioneddata"></a>**PersistData/PersistProvisionedData**  
In Windows 10 unterstützt nicht. Verwenden Sie stattdessen DoWipePersistProvisionedData im [Bereich CSP RemoteWipe](remotewipe-csp.md) .

<a href="" id="clock-timezone-"></a>**Uhr/TimeZone /**  
Eine ganze Zahl, die die Zeitzone des Geräts angibt. In der folgenden Tabelle sind die möglichen Werte.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Zeitzone</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>0</strong></p></td>
<td><p>UTC-12 Internationale Datumsgrenze</p></td>
</tr>
<tr class="even">
<td><p><strong>100</strong></p></td>
<td><p>UTC + 13 Samoa</p></td>
</tr>
<tr class="odd">
<td><p><strong>110</strong></p></td>
<td><p>UTC-11 koordinierte Weltzeit-11</p></td>
</tr>
<tr class="even">
<td><p><strong>200</strong></p></td>
<td><p>UTC-10 Hawaii</p></td>
</tr>
<tr class="odd">
<td><p><strong>300</strong></p></td>
<td><p>UTC-09 Alaska</p></td>
</tr>
<tr class="even">
<td><p><strong>400</strong></p></td>
<td><p>UTC-08 Pacific Zeit (USA &amp; Kanada)</p></td>
</tr>
<tr class="odd">
<td><p><strong>410</strong></p></td>
<td><p>UTC-08-Niederkalifornien</p></td>
</tr>
<tr class="even">
<td><p><strong>500</strong></p></td>
<td><p>UTC-07 Mountain Standard Time (US &amp; Kanada)</p></td>
</tr>
<tr class="odd">
<td><p><strong>510</strong></p></td>
<td><p>UTC-07 Chihuahua, La Paz, Mazatlan</p></td>
</tr>
<tr class="even">
<td><p><strong>520</strong></p></td>
<td><p>UTC-07 Arizona</p></td>
</tr>
<tr class="odd">
<td><p><strong>600</strong></p></td>
<td><p>UTC-06 Saskatchewan</p></td>
</tr>
<tr class="even">
<td><p><strong>610</strong></p></td>
<td><p>UTC-06 Mittelamerika</p></td>
</tr>
<tr class="odd">
<td><p><strong>620</strong></p></td>
<td><p>UTC-06 Central Zeit (USA &amp; Kanada)</p></td>
</tr>
<tr class="even">
<td><p><strong>630</strong></p></td>
<td><p>UTC-06 Guadalajara, Mexico-Stadt, Monterrey</p></td>
</tr>
<tr class="odd">
<td><p><strong>700</strong></p></td>
<td><p>UTC-05 Eastern Zeit (USA &amp; Kanada)</p></td>
</tr>
<tr class="even">
<td><p><strong>710</strong></p></td>
<td><p>UTC-05 Bogotá, Lima, Quito</p></td>
</tr>
<tr class="odd">
<td><p><strong>720</strong></p></td>
<td><p>UTC-05 Indiana (OST)</p></td>
</tr>
<tr class="even">
<td><p><strong>800</strong></p></td>
<td><p>UTC-04 Atlantic (Kanada)</p></td>
</tr>
<tr class="odd">
<td><p><strong>810</strong></p></td>
<td><p>UTC-04 Cuiaba</p></td>
</tr>
<tr class="even">
<td><p><strong>820</strong></p></td>
<td><p>UTC-04 Santiago</p></td>
</tr>
<tr class="odd">
<td><p><strong>830</strong></p></td>
<td><p>UTC-04 Georgetown, La Paz, Manaus, San Juan</p></td>
</tr>
<tr class="even">
<td><p><strong>840</strong></p></td>
<td><p>UTC-04 Caracas</p></td>
</tr>
<tr class="odd">
<td><p><strong>850</strong></p></td>
<td><p>UTC-04 Asuncion</p></td>
</tr>
<tr class="even">
<td><p><strong>900</strong></p></td>
<td><p>UTC-03:30 Neufundland</p></td>
</tr>
<tr class="odd">
<td><p><strong>910</strong></p></td>
<td><p>UTC-03 Brasília</p></td>
</tr>
<tr class="even">
<td><p><strong>920</strong></p></td>
<td><p>UTC-03 Grönland</p></td>
</tr>
<tr class="odd">
<td><p><strong>930</strong></p></td>
<td><p>UTC-03 Montevideo</p></td>
</tr>
<tr class="even">
<td><p><strong>940</strong></p></td>
<td><p>UTC-03 Cayenne, Fortaleza</p></td>
</tr>
<tr class="odd">
<td><p><strong>950</strong></p></td>
<td><p>UTC-03 Buenos Aires</p></td>
</tr>
<tr class="even">
<td><p><strong>960</strong></p></td>
<td><p>UTC-03 Salvador</p></td>
</tr>
<tr class="odd">
<td><p><strong>1000</strong></p></td>
<td><p>UTC-02 Mittelatlantik</p></td>
</tr>
<tr class="even">
<td><p><strong>1010</strong></p></td>
<td><p>UTC-02 koordinierte Weltzeit-02</p></td>
</tr>
<tr class="odd">
<td><p><strong>1100</strong></p></td>
<td><p>UTC-01 Azoren</p></td>
</tr>
<tr class="even">
<td><p><strong>1110</strong></p></td>
<td><p>UTC-01 Cabo Verde</p></td>
</tr>
<tr class="odd">
<td><p><strong>1200</strong></p></td>
<td><p>UTC Dublin, Edinburgh, Lissabon, London</p></td>
</tr>
<tr class="even">
<td><p><strong>1210</strong></p></td>
<td><p>UTC Monrovia, Reykjavik</p></td>
</tr>
<tr class="odd">
<td><p><strong>1220</strong></p></td>
<td><p>UTC Casablanca</p></td>
</tr>
<tr class="even">
<td><p><strong>1230</strong></p></td>
<td><p>UTC koordinierte Weltzeit</p></td>
</tr>
<tr class="odd">
<td><p><strong>1300</strong></p></td>
<td><p>UTC + 01 Belgrad, Bratislava, Budapest, Ljubljana, Prag</p></td>
</tr>
<tr class="even">
<td><p><strong>1310</strong></p></td>
<td><p>UTC + 01 Sarajevo, Skopje, Warschau, Zagreb</p></td>
</tr>
<tr class="odd">
<td><p><strong>1320</strong></p></td>
<td><p>UTC + 01 Brüssel, Kopenhagen, Madrid, Paris</p></td>
</tr>
<tr class="even">
<td><p><strong>1330</strong></p></td>
<td><p>UTC + 01 West-Zentralafrika</p></td>
</tr>
<tr class="odd">
<td><p><strong>1340</strong></p></td>
<td><p>UTC + 01 Amsterdam, Berlin, Bern, ROM, Stockholm, Wien</p></td>
</tr>
<tr class="even">
<td><p><strong>1350</strong></p></td>
<td><p>UTC + 01 Windhuk</p></td>
</tr>
<tr class="odd">
<td><p><strong>1360</strong></p></td>
<td><p>UTC + 01 Tripoli</p></td>
</tr>
<tr class="even">
<td><p><strong>1400</strong></p></td>
<td><p>UTC + 02 E. Europa</p></td>
</tr>
<tr class="odd">
<td><p><strong>1410</strong></p></td>
<td><p>UTC + 02 Kairo</p></td>
</tr>
<tr class="even">
<td><p><strong>1420</strong></p></td>
<td><p>UTC + 02 Helsinki, Kiew, Riga, Sofia, Tallinn, Wilna</p></td>
</tr>
<tr class="odd">
<td><p><strong>1430</strong></p></td>
<td><p>UTC + 02 Athen, Bukarest</p></td>
</tr>
<tr class="even">
<td><p><strong>1440</strong></p></td>
<td><p>UTC + 02 Jerusalem</p></td>
</tr>
<tr class="odd">
<td><p><strong>1450</strong></p></td>
<td><p>UTC + 02 Amman</p></td>
</tr>
<tr class="even">
<td><p><strong>1460</strong></p></td>
<td><p>UTC + 02 Beirut</p></td>
</tr>
<tr class="odd">
<td><p><strong>1470</strong></p></td>
<td><p>UTC + 02 Harare, Pretoria</p></td>
</tr>
<tr class="even">
<td><p><strong>1480</strong></p></td>
<td><p>UTC + 02 Damaskus</p></td>
</tr>
<tr class="odd">
<td><p><strong>1490</strong></p></td>
<td><p>UTC + 02 Istanbul</p></td>
</tr>
<tr class="even">
<td><p><strong>1500</strong></p></td>
<td><p>UTC + 03 Kuwait, Riad</p></td>
</tr>
<tr class="odd">
<td><p><strong>1510</strong></p></td>
<td><p>UTC + 03 Bagdad</p></td>
</tr>
<tr class="even">
<td><p><strong>1520</strong></p></td>
<td><p>UTC + 03 Nairobi</p></td>
</tr>
<tr class="odd">
<td><p><strong>1530</strong></p></td>
<td><p>UTC + 03 Kaliningrad, Minsk</p></td>
</tr>
<tr class="even">
<td><p><strong>1540</strong></p></td>
<td><p>UTC + 04 Moskau, St. Petersburg, Wolgograd</p></td>
</tr>
<tr class="odd">
<td><p><strong>1550</strong></p></td>
<td><p>UTC + 03 Teheran</p></td>
</tr>
<tr class="even">
<td><p><strong>1600</strong></p></td>
<td><p>UTC + 04 Abu Dhabi, Muskat</p></td>
</tr>
<tr class="odd">
<td><p><strong>1610</strong></p></td>
<td><p>UTC + 04 Baku</p></td>
</tr>
<tr class="even">
<td><p><strong>1620</strong></p></td>
<td><p>UTC + 04 Eriwan</p></td>
</tr>
<tr class="odd">
<td><p><strong>1630</strong></p></td>
<td><p>UTC + 04 Kabul</p></td>
</tr>
<tr class="even">
<td><p><strong>1640</strong></p></td>
<td><p>UTC + 04 Tiflis</p></td>
</tr>
<tr class="odd">
<td><p><strong>1650</strong></p></td>
<td><p>UTC + 04 Port Louis</p></td>
</tr>
<tr class="even">
<td><p><strong>1700</strong></p></td>
<td><p>UTC + 06 Jekaterinburg</p></td>
</tr>
<tr class="odd">
<td><p><strong>1710</strong></p></td>
<td><p>UTC + 05 Taschkent</p></td>
</tr>
<tr class="even">
<td><p><strong>1720</strong></p></td>
<td><p>UTC + 05 Chennai, Kolkata, Mumbai, Neu-Delhi</p></td>
</tr>
<tr class="odd">
<td><p><strong>1730</strong></p></td>
<td><p>UTC + 05 Sri Jayawardenepura</p></td>
</tr>
<tr class="even">
<td><p><strong>1740</strong></p></td>
<td><p>UTC + 05 Katmandu</p></td>
</tr>
<tr class="odd">
<td><p><strong>1750</strong></p></td>
<td><p>UTC + 05 Islamabad, Karatschi</p></td>
</tr>
<tr class="even">
<td><p><strong>1800</strong></p></td>
<td><p>UTC + 06 Astana</p></td>
</tr>
<tr class="odd">
<td><p><strong>1810</strong></p></td>
<td><p>UTC + 07 Nowosibirsk</p></td>
</tr>
<tr class="even">
<td><p><strong>1820</strong></p></td>
<td><p>UTC + 06 Yangon (Rangun)</p></td>
</tr>
<tr class="odd">
<td><p><strong>1830</strong></p></td>
<td><p>UTC + 06 Dakka</p></td>
</tr>
<tr class="even">
<td><p><strong>1900</strong></p></td>
<td><p>UTC + 08 Krasnojarsk</p></td>
</tr>
<tr class="odd">
<td><p><strong>1910</strong></p></td>
<td><p>UTC + 07 Bangkok, Hanoi, Jakarta</p></td>
</tr>
<tr class="even">
<td><p><strong>1900</strong></p></td>
<td><p>UTC + 08 Krasnojarsk</p></td>
</tr>
<tr class="odd">
<td><p><strong>2000</strong></p></td>
<td><p>UTC + 08 Peking, Chongqing, Hongkong SAR, Ürümqi</p></td>
</tr>
<tr class="even">
<td><p><strong>2010</strong></p></td>
<td><p>UTC + 09 Irkutsk</p></td>
</tr>
<tr class="odd">
<td><p><strong>2020</strong></p></td>
<td><p>UTC + 08 Kuala Lumpur, Singapur</p></td>
</tr>
<tr class="even">
<td><p><strong>2030</strong></p></td>
<td><p>UTC + 08 Taipeh</p></td>
</tr>
<tr class="odd">
<td><p><strong>2040</strong></p></td>
<td><p>UTC + 08 Perth</p></td>
</tr>
<tr class="even">
<td><p><strong>2050</strong></p></td>
<td><p>UTC + 08 Ulan-Bator</p></td>
</tr>
<tr class="odd">
<td><p><strong>2100</strong></p></td>
<td><p>UTC + 09 Seoul</p></td>
</tr>
<tr class="even">
<td><p><strong>2110</strong></p></td>
<td><p>UTC + 09 Osaka, Sapporo, Tokio</p></td>
</tr>
<tr class="odd">
<td><p><strong>2120</strong></p></td>
<td><p>UTC + 10 Jakutsk</p></td>
</tr>
<tr class="even">
<td><p><strong>2130</strong></p></td>
<td><p>UTC + 09 Darwin</p></td>
</tr>
<tr class="odd">
<td><p><strong>2140</strong></p></td>
<td><p>UTC + 09 Adelaide</p></td>
</tr>
<tr class="even">
<td><p><strong>2200</strong></p></td>
<td><p>UTC + 10 Canberra, Melbourne, australische</p></td>
</tr>
<tr class="odd">
<td><p><strong>2210</strong></p></td>
<td><p>UTC + 10 Brisbane</p></td>
</tr>
<tr class="even">
<td><p><strong>2220</strong></p></td>
<td><p>UTC + 10 Hobart</p></td>
</tr>
<tr class="odd">
<td><p><strong>2230</strong></p></td>
<td><p>UTC + 11 Wladiwostok</p></td>
</tr>
<tr class="even">
<td><p><strong>2240</strong></p></td>
<td><p>UTC + 10 Guam, Port Moresby</p></td>
</tr>
<tr class="odd">
<td><p><strong>2300</strong></p></td>
<td><p>UTC + 11 Solomon Inseln, Neukaledonien</p></td>
</tr>
<tr class="even">
<td><p><strong>2310</strong></p></td>
<td><p>UTC + 12 Magadan</p></td>
</tr>
<tr class="odd">
<td><p><strong>2400</strong></p></td>
<td><p>UTC + 12 Fidschi</p></td>
</tr>
<tr class="even">
<td><p><strong>2410</strong></p></td>
<td><p>UTC + 12 Auckland, Wellington</p></td>
</tr>
<tr class="odd">
<td><p><strong>2420</strong></p></td>
<td><p>UTC + 12 Petropawlowsk-Kamtschatski</p></td>
</tr>
<tr class="even">
<td><p><strong>2430</strong></p></td>
<td><p>UTC + 12 koordinierte Weltzeit + 12</p></td>
</tr>
<tr class="odd">
<td><p><strong>2500</strong></p></td>
<td><p>UTC + 13 Nuku'alofa</p></td>
</tr>
</tbody>
</table>

 

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="locale-language-"></a>**Gebietsschema/Sprache /**  
Der Code, der die Sprache für die Anzeige auf einem Gerät identifiziert, und gibt die Formatierung von Zahlen, Währung, Uhrzeit und Datumsangaben. Language-Werte finden Sie unter [Von Microsoft zugewiesene Gebietsschema-](http://go.microsoft.com/fwlink/p/?LinkID=189567).

Die Spracheinstellung wird in der Standard-Benutzerprofil nur konfiguriert.

> **Hinweis**  Wenden Sie die Gebietsschema-ID, nachdem die entsprechenden Language Packs integriert und unterstützte für das Betriebssystemabbild auf dem Gerät ausgeführt werden. Möglicherweise ist ein Neustart erforderlich, und die angegebene Sprache als Telefon Sprache angewendet werden.

 

Unterstützte Vorgänge sind Get und ersetzen.

## <a name="oma-client-provisioning-examples"></a>Beispiele für die Bereitstellung OMA-client


XML-Beispielen in diesem Abschnitt zeigen, wie verschiedene Aufgaben mithilfe von OMA-Client-Bereitstellung.

> **Hinweis**  In diesen Beispielen werden XML Snippets und enthalten nicht alle Abschnitte, die für eine vollständige Sperrung XML-Datei benötigt werden.

 

### <a name="assigned-access-settings"></a>Zugewiesene zugriffseinstellungen

Im folgenden Beispiel wird gezeigt, wie eine neue Richtlinie hinzugefügt.

``` syntax
<wap-provisioningdoc> 
  <characteristic type="EnterpriseAssignedAccess"> 
    <characteristic type="AssignedAccess"> 
      <parm name=" AssignedAccessXml" datatype="string" 
            value="&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&lt;HandheldLockdown version=&quot;1.0&quot;&gt;&lt;Default&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5615}&quot; pinToStart=&quot;1&quot;/&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5612}&quot; pinToStart=&quot;0&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;System name=&quot;Microsoft.About&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;ButtonLockdownList&gt;&lt;Button name=&quot;Start&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;Button name=&quot;Camera&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;Button name=&quot;Search&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;/ButtonLockdownList&gt;&lt;ButtonRemapList/&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Default&gt;&lt;RoleList&gt;&lt;Role guid=&quot;{76C01983-A872-4C4E-B4C6-321EAC709CEA}&quot; name=&quot;Associate&quot;&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5615}&quot; pinToStart=&quot;1&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;System name=&quot;Microsoft.About&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;ButtonLockdownList&gt;&lt;Button name=&quot;Start&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;Button name=&quot;Camera&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;/ButtonLockdownList&gt;&lt;ButtonRemapList/&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Role&gt;&lt;Role guid=&quot;{8ABB8A10-4418-4467-9E18-99D11FA54E30}&quot; name=&quot;Manager&quot;&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5612}&quot; pinToStart=&quot;1&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;ButtonLockdownList&gt;&lt;Button name=&quot;Start&quot;&gt;&lt;ButtonEvent name=&quot;Press&quot; /&gt;&lt;ButtonEvent name=&quot;PressAndHold&quot; /&gt;&lt;/Button&gt;&lt;/ButtonLockdownList&gt;&lt;ButtonRemapList/&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Role&gt;&lt;/RoleList&gt;&lt;/HandheldLockdown&gt;"/> 
    </characteristic> 
  </characteristic> 
</wap-provisioningdoc> 
```

### <a name="language"></a>Sprache

Im folgenden Beispiel wird das Angeben der Sprache für die Anzeige auf dem Gerät veranschaulicht.

``` syntax
<wap-provisioningdoc> 
   <characteristic type="EnterpriseAssignedAccess"> 
  <characteristic type="Language"> 
      <parm name="Language" datatype="string" 
   <parm name="Language" value="1033" />
   </characteristic> 
</wap-provisioningdoc> 
```

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Diese XML-Beispielen veranschaulicht verschiedene Aufgaben mit OMA DM ausführen.

### <a name="assigned-access-settings"></a>Zugewiesene zugriffseinstellungen

Im folgenden Beispiel wird gezeigt, wie zum Sperren von einem Gerät.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Add> 
         <CmdID>2</CmdID> 
         <Item> 
            <Target> 
               <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/AssignedAccess/AssignedAccessXml</LocURI> 
            </Target> 
            <Data>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&lt;HandheldLockdown version=&quot;1.0&quot;&gt;&lt;Default&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5615}&quot; pinToStart=&quot;1&quot;/&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5612}&quot; pinToStart=&quot;2&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;System name=&quot;Microsoft.About&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;Button name=&quot;Start&quot; disableEvents=&quot;PressAndHold&quot; /&gt;&lt;Button name=&quot;Camera&quot; disableEvents=&quot;All&quot; /&gt;&lt;Button name=&quot;Search&quot; disableEvents=&quot;All&quot; /&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Default&gt;&lt;RoleList&gt;&lt;Role guid=&quot;{76C01983-A872-4C4E-B4C6-321EAC709CEA}&quot; name=&quot;Associate&quot;&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5615}&quot; pinToStart=&quot;1&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;System name=&quot;Microsoft.About&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;Button name=&quot;Start&quot; disableEvents=&quot;PressAndHold&quot; /&gt;&lt;Button name=&quot;Camera&quot; disableEvents=&quot;All&quot; /&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Role&gt;&lt;Role guid=&quot;{8ABB8A10-4418-4467-9E18-99D11FA54E30}&quot; name=&quot;Manager&quot;&gt;&lt;Apps&gt;&lt;Application productId=&quot;{5B04B775-356B-4AA0-AAF8-6491FFEA5612}&quot; pinToStart=&quot;1&quot;/&gt;&lt;/Apps&gt;&lt;Settings&gt;&lt;System name=&quot;Microsoft.Themes&quot; /&gt;&lt;/Settings&gt;&lt;Buttons&gt;&lt;Button name=&quot;Start&quot; disableEvents=&quot;PressAndHold&quot; /&gt;&lt;/Buttons&gt;&lt;MenuItems&gt;&lt;DisableMenuItems/&gt;&lt;/MenuItems&gt;&lt;/Role&gt;&lt;/RoleList&gt;&lt;/HandheldLockdown&gt;</Data> 
         </Item> 
      </Add> 
      <Final/> 
   </SyncBody> 
</SyncML> 
```

### <a name="theme"></a>Design

Im folgenden Beispiel wird veranschaulicht, wie die Akzentfarbe eines Standardfarben ändern.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Replace> 
         <CmdID>1</CmdID> 
         <Item> 
            <Target> 
             <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Theme/ThemeAccentColorID</LocURI> 
            </Target> 
            <Meta> 
               <Format xmlns="syncml:metinf">int</Format> 
            </Meta> 
            <!-- zero based index of available theme colors --> 
            <Data>7</Data> 
         </Item> 
      </Replace> 
      <Final/> 
   </SyncBody> 
</SyncML>
```

Im folgenden Beispiel wird gezeigt, wie das Design ändern.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
       <Replace> 
           <CmdID>1</CmdID> 
           <Item> 
               <Target> 
                   <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Theme/ThemeBackground</LocURI> 
               </Target> 
               <Meta> 
                   <Format xmlns="syncml:metinf">int</Format> 
               </Meta> 
               <!-- 0 for "light", 1 for "dark" --> 
               <Data>1</Data> 
           </Item> 
       </Replace> 
       <Final/> 
   </SyncBody> 
</SyncML> 
```

Im folgenden Beispiel wird veranschaulicht, wie ein benutzerdefiniertes Design Akzentfarbe für die Enterprise-Umgebung festlegen.

``` syntax
<SyncBody> 
   <Replace> 
      <CmdID>1</CmdID> 
      <Item> 
         <Target> 
             <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Theme/ThemeAccentColorID</LocURI> 
         </Target> 
         <Meta> 
            <Format xmlns="syncml:metinf">int</Format> 
         </Meta> 
         <!—set to Enterprise custom --> 
         <Data>151</Data> 
      </Item> 
   </Replace> 
   <Replace>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Theme/ThemeAccentColorValue</LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
         </Meta>
         <!—sets custom accent color of red -->
         <Data>FF0000</Data>
      </Item>
   </Replace>
   <Final/> 
</SyncBody> 
```

### <a name="lock-screen"></a>Sperrbildschirm

Verwenden Sie die Beispiele in diesem Abschnitt, um einen neuen Sperrbildschirm festlegen und Verwalten der die Sperre Bildschirmfeatures. Wenn Sie einen UNC-Pfad zu verwenden, formatieren Sie die LocURI als \\ \\Host\\freigeben\\image.jpg.

``` syntax
<Add> 
  <CmdID>2</CmdID> 
  <Item> 
    <Target> 
      <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/LockScreenWallpaper/BGFileName</LocURI> 
    <Meta> 
      <Format xmlns="syncml:metinf">chr</Format> 
      <Type xmlns="syncml:metinf">text/plain</Type> 
    </Meta> 
    <Data>c:\windows\system32\lockscreen\480x800\Wallpaper_015.jpg </Data> 
    </Target> 
  </Item> 
</Add> 
```

Im folgenden Beispiel wird gezeigt, wie das Gerät für die Datei als dem Sperrbildschirm verwendete Abfragen.

``` syntax
<Get> 
  <CmdID>2</CmdID> 
  <Item> 
    <Target> 
      <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/LockScreenWallpaper/BGFileName</LocURI> 
    </Target> 
  </Item> 
</Get> 
```

Im folgende Beispiel veranschaulicht das Bild des vorhandenen Sperre auf eine Ihrer Wahl zu ändern.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Replace> 
         <CmdID>2</CmdID> 
         <Item> 
            <Target> 
               <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/LockScreenWallpaper/BGFileName</LocURI> 
            </Target> 
            <Meta> 
               <Format xmlns="syncml:metinf">chr</Format> 
               <Type xmlns="syncml:metinf">text/plain</Type> 
            </Meta> 
            <Data>c:\windows\system32\lockscreen\480x800\Wallpaper_015.jpg</Data> 
         </Item> 
      </Replace> 
      <Final/> 
   </SyncBody> 
</SyncML> 
```

### <a name="time-zone"></a>Zeitzone

Im folgenden Beispiel wird veranschaulicht, wie die Zeitzone zu UTC-07 Mountain Zeit (USA und Kanada) festgelegt.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Replace> 
         <CmdID>2</CmdID> 
         <Item> 
            <Target> 
               <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Clock/TimeZone</LocURI> 
            </Target> 
            <Meta> 
               <Format xmlns="syncml:metinf">int</Format> 
            </Meta> 
            <Data>500</Data> 
         </Item> 
      </Replace> 
      <Final/> 
   </SyncBody> 
</SyncML> 
```

Im folgenden Beispiel wird veranschaulicht, wie festzulegen, der die Zeitzone Pacific Standard Time (UTC-08:00) ohne beobachten Sommerzeit (UTC + 01:00).

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Replace> 
         <CmdID>2</CmdID> 
         <Item> 
            <Target> 
               <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Clock/TimeZone</LocURI> 
            </Target> 
            <Meta> 
               <Format xmlns="syncml:metinf">int</Format> 
            </Meta> 
            <Data>400 </Data> 
         </Item> 
      </Replace> 
      <Final/> 
   </SyncBody> 
</SyncML> 
```

### <a name="language"></a>Sprache

Im folgende Beispiel veranschaulicht die Sprache festgelegt.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2"> 
   <SyncBody> 
      <Replace> 
         <CmdID>1</CmdID> 
         <Item> 
            <Target> 
               <LocURI>./Vendor/MSFT/EnterpriseAssignedAccess/Locale/Language</LocURI> 
            </Target> 
            <Meta> 
               <Format xmlns="syncml:metinf">int</Format> 
            </Meta> 
            <Data>1033</Data> 
         </Item> 
      </Replace> 
      <Final/> 
   </SyncBody> 
</SyncML> 
```

## <a name="a-href-idproductidaproduct-ids-in-windows-10-mobile"></a><a href="" id="productid"></a>Produkt-IDs in 10 Windows Mobile


Die folgende Tabelle enthält die Produkt-ID und AUMID für die jeweilige app, die in Windows 10 Mobile enthalten ist.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>App</th>
<th>Produkt-ID</th>
<th>AUMID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alarmen und Uhr</td>
<td>44F7D2B4-553D-4BEC-A8B7-634CE897ED5F</td>
<td>Microsoft.WindowsAlarms_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Rechner</td>
<td>B58171C6-C70C-4266-A2E8-8F9C994F4456</td>
<td>Microsoft.WindowsCalculator_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Kamera</td>
<td>F0D8FEFD-31CD-43A1-A45A-D0276DB069F1</td>
<td>Microsoft.WindowsCamera_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Kontaktieren des Supports</td>
<td>0DB5FCFF-4544-458A-B320-E352DFD9CA2B</td>
<td>Windows.ContactSupport_cw5n1h2txyewy! App</td>
</tr>
<tr class="odd">
<td>Cortana</td>
<td>FD68DCF4-166F-4C55-A4CA-348020F71B94</td>
<td>Microsoft.Windows.Cortana_cw5n1h2txyewy! CortanaUI</td>
</tr>
<tr class="even">
<td>Excel</td>
<td>EAD3E7C0-FAE6-4603-8699-6A448138F4DC</td>
<td>Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel</td>
</tr>
<tr class="odd">
<td>Facebook</td>
<td>82A23635-5BD9-DF11-A844-00237DE2DB9E</td>
<td>Microsoft.MSFacebook_8wekyb3d8bbwe!x82a236355bd9df11a84400237de2db9e</td>
</tr>
<tr class="even">
<td>Datei-Explorer</td>
<td>C5E2524A-EA46-4F67-841F-6A9465D9D515</td>
<td>c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy! App</td>
</tr>
<tr class="odd">
<td>UKW</td>
<td>F725010E-455D-4C09-AC48-BCDEF0D4B626</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Erste Schritte</td>
<td>B3726308-3D74-4A14-A84C-867C8C735C3C</td>
<td>Microsoft.Getstarted_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Groove-Musik</td>
<td>D2B6A184-DA39-4C9A-9E0A-8B589B03DEC0</td>
<td>Microsoft.ZuneMusic_8wekyb3d8bbwe! Microsoft.ZuneMusic</td>
</tr>
<tr class="even">
<td>Karten</td>
<td>ED27A07E-AF57-416B-BC0C-2596B622EF7D</td>
<td>Microsoft.WindowsMaps_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Messaging</td>
<td>27E26F40-E031-48A6-B130-D1F20388991A</td>
<td>Microsoft.Messaging_8wekyb3d8bbwe!x27e26f40ye031y48a6yb130yd1f20388991ax</td>
</tr>
<tr class="even">
<td>Microsoft-Edge</td>
<td>395589FB-5884-4709-B9DF-F7D558663FFD</td>
<td>Microsoft.MicrosoftEdge_8wekyb3d8bbwe! MicrosoftEdge</td>
</tr>
<tr class="odd">
<td>Money</td>
<td>1E0440F1-7ABF-4B9A-863D-177970EEFB5E</td>
<td>Microsoft.BingFinance_8wekyb3d8bbwe! AppexFinance</td>
</tr>
<tr class="even">
<td>Filme und TV</td>
<td>6AFFE59E-0467-4701-851F-7AC026E21665</td>
<td>Microsoft.ZuneVideo_8wekyb3d8bbwe! Microsoft.ZuneVideo</td>
</tr>
<tr class="odd">
<td>Neuigkeiten</td>
<td>9C3E8CAD-6702-4842-8F61-B8B33CC9CAF1</td>
<td>Microsoft.BingNews_8wekyb3d8bbwe! AppexNews</td>
</tr>
<tr class="even">
<td>OneDrive</td>
<td>AD543082-80EC-45BB-AA02-FFE7F4182BA8</td>
<td>Microsoft.MicrosoftSkydrive_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>OneNote</td>
<td>CA05B3AB-F157-450C-8C49-A1F127F5E71D</td>
<td>Microsoft.Office.OneNote_8wekyb3d8bbwe!microsoft.onenoteim</td>
</tr>
<tr class="even">
<td>Outlook-Kalender</td>
<td><p>A558FEBA-85D7-4665-B5D8-A2FF9C19799B</p></td>
<td><p>Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe! Microsoft.WindowsLive.Calendar</p></td>
</tr>
<tr class="odd">
<td>Outlook-Mail</td>
<td><p>A558FEBA-85D7-4665-B5D8-A2FF9C19799B</p></td>
<td><p>Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe! Microsoft.WindowsLive.Mail</p></td>
</tr>
<tr class="even">
<td>Kontakte</td>
<td>60BE1FB8-3291-4B21-BD39-2221AB166481</td>
<td>Microsoft.People_8wekyb3d8bbwe!xb94d6231y84ddy49a8yace3ybc955e769e85x</td>
</tr>
<tr class="odd">
<td>Telefon (Wählhilfe)</td>
<td>F41B5D0E-EE94-4F47-9CFE-3D3934C5A2C7</td>
<td>Microsoft.CommsPhone_8wekyb3d8bbwe!App</td>
</tr>
<tr class="even">
<td>Fotos</td>
<td>FCA55E1B-B9A4-4289-882F-084EF4145005</td>
<td>Microsoft.Windows.Photos_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Podcasts (engl.)</td>
<td>C3215724-B279-4206-8C3E-61D1A9D63ED3</td>
<td>Microsoft.MSPodcast_8wekyb3d8bbwe!xc3215724yb279y4206y8c3ey61d1a9d63ed3x</td>
</tr>
<tr class="even">
<td>PowerPoint</td>
<td>B50483C4-8046-4E1B-81BA-590B24935798</td>
<td>Microsoft.Office.PowerPoint_8wekyb3d8bbwe!microsoft.pptim</td>
</tr>
<tr class="odd">
<td>Einstellungen</td>
<td>2A4E62D8-8809-4787-89F8-69D0F01654FB</td>
<td>2a4e62d8-8809-4787-89f8-69d0f01654fb_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Skype</td>
<td>C3F8E570-68B3-4D6A-BDBB-C0A3F4360A51</td>
<td>Microsoft.SkypeApp_kzf8qxf38zg5c! Skype.AppId</td>
</tr>
<tr class="odd">
<td>Skype-Video</td>
<td>27E26F40-E031-48A6-B130-D1F20388991A</td>
<td>Microsoft.Messaging_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Sportliga</td>
<td>0F4C8C7E-7114-4E1E-A84C-50664DB13B17</td>
<td>Microsoft.BingSports_8wekyb3d8bbwe! AppexSports</td>
</tr>
<tr class="odd">
<td>Storage</td>
<td>5B04B775-356B-4AA0-AAF8-6491FFEA564D</td>
<td>n/v</td>
</tr>
<tr class="even">
<td>Store</td>
<td>7D47D89A-7900-47C5-93F2-46EB6D94C159</td>
<td>Microsoft.WindowsStore_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>VoIP-Aufzeichnung</td>
<td>7311B9C5-A4E9-4C74-BC3C-55B06BA95AD0</td>
<td>Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Wallet</td>
<td>587A4577-7868-4745-A29E-F996203F1462</td>
<td>Microsoft.MicrosoftWallet_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Wetterbericht</td>
<td>63C2A117-8604-44E7-8CEF-DF10BE3A57C8</td>
<td>Microsoft.BingWeather_8wekyb3d8bbwe! App</td>
</tr>
<tr class="even">
<td>Windows-Feedback</td>
<td>7604089D-D13F-4A2D-9998-33FC02B63CE3</td>
<td>Microsoft.WindowsFeedback_8wekyb3d8bbwe! App</td>
</tr>
<tr class="odd">
<td>Wort</td>
<td>258F115C-48F4-4ADB-9A68-1387E634459B</td>
<td>Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word</td>
</tr>
<tr class="even">
<td>Xbox</td>
<td>B806836F-EEBE-41C9-8669-19E243B81B83</td>
<td>Microsoft.XboxApp_8wekyb3d8bbwe! Microsoft.XboxApp</td>
</tr>
</tbody>
</table>

 

 

 






