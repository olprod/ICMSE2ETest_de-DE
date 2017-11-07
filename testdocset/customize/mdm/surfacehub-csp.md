---
title: SurfaceHub CSP
description: "Der SurfaceHub Konfiguration-Dienstanbieter (CSP) wird verwendet, um Microsoft Surface Hub Einstellungen konfigurieren. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 36FBBC32-AD6A-41F1-86BF-B384891AA693
ms.openlocfilehash: c6c687fe8e69c3fb4ee34e99bdcd7b8808616343
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="surfacehub-csp"></a>SurfaceHub CSP


Der SurfaceHub Konfigurationsdienstanbieter (CSP) wird verwendet, um Microsoft Surface Hub Einstellungen konfigurieren. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt.

Das folgende Diagramm zeigt die SurfaceHub CSP Verwaltungsobjekte in der Strukturformat.

![Fläche Hub-Diagramm](images/provisioning-csp-surfacehub.png)

<a href="" id="--vendor-msft-surfacehub"></a>**./Vendor/MSFT/SurfaceHub**  
Der für die Oberfläche Hub Konfigurationsdienstanbieter Stammknoten.

<a href="" id="deviceaccount"></a>**DeviceAccount**  
Knoten für das Gerät Kontoinformationen festlegen. Ein Gerät Konto ist eine Microsoft Exchange, der mit Skype für Unternehmen,, wodurch Personen zur geplante Besprechungen teilnehmen verbunden ist, Skype für geschäftliche Anrufe tätigen und Freigeben von Inhalt aus dem Gerät. Finden Sie die Fläche Hub-Administratorhandbuch für Weitere Informationen zum Einrichten eines Kontos Gerät.

**Gerät-Konto von Azure Active Directory verwenden**

1.  UserPrincipalName (für Azure AD) festgelegt.
2.  Legen Sie ein gültiges Kennwort ein.
3.  Führen Sie zum Überprüfen der angegebenen Benutzernamen und das Kennwort der Kombination mit Azure AD ValidateAndCommit an.
4.  Abrufen der ErrorContext Fall, dass ein Problem bei der Validierung auftritt

> **Hinweis**  Wenn das Gerät Auto-den Exchange-Server und Session Initiation Protocol (SIP) Adresse aus diesen Informationen entdeckt werden kann, sollten Sie die ExchangeServer und "SipAddress" angeben.

 

Hier ist ein Beispiel für die SyncML aus.

``` syntax
 <SyncML xmlns="SYNCML:SYNCML1.2">
        <SyncBody>
            <Replace>
                <CmdID>1</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/UserPrincipalName</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>user@contoso.com</Data>
                </Item>
            </Replace>
            <Replace>
                <CmdID>2</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/Password</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>password</Data>
                </Item>
            </Replace>
            <Exec>
                <CmdID>3</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/ValidateAndCommit</LocURI>
                    </Target>
                </Item>
            </Exec>
            <Get>
                <CmdID>4</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/ErrorContext</LocURI>
                    </Target>
                </Item>
            </Get>
            <Final/> 
        </SyncBody>
    </SyncML>
```

**Verwendung eines Kontos Gerät aus Active Directory**

1.  Legen Sie den Domänennamen ein.
2.  Legen Sie den Benutzernamen ein.
3.  Legen Sie ein gültiges Kennwort ein.
4.  Führen Sie den Knoten ValidateAndCommit.

<a href="" id="deviceaccount-domainname"></a>**DeviceAccount/Domänenname**  
Das Gerät-Konto bei Verwendung der Active Directory-Domäne. Wenn Sie ein Konto Gerät aus Active Directory verwenden, sollten Sie für das Gerät ein Domänenname und Benutzername angeben.

Der Datentyp ist Char. Unterstützte Operation wird Get und ersetzen.

<a href="" id="deviceaccount-username"></a>**DeviceAccount/Benutzername**  
Der Benutzername des Kontos Gerät bei Verwendung von Active Directory. Wenn Sie ein Gerät Konto aus Active Directory verwenden, sollten Sie für das Gerät ein Domänenname und Benutzername angeben.

Der Datentyp ist Char. Unterstützte Operation wird Get und ersetzen.

<a href="" id="deviceaccount-userprincipalname"></a>**DeviceAccount/UserPrincipalName**  
Benutzerprinzipalname (UPN) des Kontos ein Gerät. Wenn Sie ein Gerät Konto von Azure Active Directory oder eine hybridbereitstellung verwenden, sollten Sie den UPN des Kontos ein Gerät angeben.

Der Datentyp ist Char. Unterstützte Vorgang ist Get und ersetzen.

<a href="" id="deviceaccount-sipaddress"></a>**DeviceAccount/SipAddress**  
Session Initiation Protocol (SIP)-Adresse des Geräts ein. Normalerweise versucht das Gerät SIP automatisch ermitteln. Dieses Feld ist nur erforderlich, wenn die automatische Ermittlung fällt aus.

Der Datentyp ist Char. Unterstützte Vorgang ist Get und ersetzen.

<a href="" id="deviceaccount-password"></a>**DeviceAccount/Kennwort**  
Kennwort für das Gerät ein.

Der Datentyp ist Char. Unterstützte Vorgang ist Get und ersetzen. Der Vorgang Get ist zulässig, jedoch wird immer eine leere zurückgegeben.

<a href="" id="deviceaccount-validateandcommit"></a>**DeviceAccount/ValidateAndCommit**  
Diese Methode überprüft die Daten zur Verfügung gestellt, und klicken Sie dann die Änderungen werden übernommen.

Der Datentyp ist Char. Unterstützte Vorgang ist ausführen.

<a href="" id="deviceaccount-email"></a>**DeviceAccount-e**  
E-Mail-Adresse des Geräts ein.

Der Datentyp ist Char an.

<a href="" id="deviceaccount-passwordrotationperiod"></a>**DeviceAccount/PasswordRotationPeriod**  
Gibt an, ob die automatische kennwortänderung Drehung aktiviert ist. Wenn Sie eine Richtlinie für den Kennwortablauf für das Konto Gerät erzwingen, verwenden Sie diese Einstellung ermöglicht das Gerät verwalten Sie ein eigenes Kennwort von geändert wird häufig, ohne dass Sie die Kontoinformationen auch manuell zu aktualisieren, wenn das Kennwort läuft ab. Sie können jederzeit mithilfe von Active Directory (oder Azure AD) das Kennwort zurücksetzen.

Gültige Werte:

-   0 – Kennwort Drehung aktiviert
-   1 – deaktiviert

Der Datentyp ist "int" Unterstützte Vorgang ist Get und ersetzen.

<a href="" id="deviceaccount-exchangeserver"></a>**DeviceAccount ExchangeServer /**  
Exchange-Server des Geräts ein. Normalerweise versucht das Gerät auf den Exchange-Server automatisch ermitteln. Dieses Feld ist nur erforderlich, wenn die automatische Ermittlung fällt aus.

Der Datentyp ist Char. Unterstützte Vorgang ist Get und ersetzen.

<a href="" id="deviceaccount-calendarsyncenabled"></a>**DeviceAccount/CalendarSyncEnabled**  
Gibt an, ob Kalender synchronisieren und anderen Exchange-Server-Dienste aktiviert ist.

Der Datentyp ist Bool. Unterstützte Vorgang ist Get und ersetzen.

<a href="" id="deviceaccount-errorcontext"></a>**DeviceAccount/ErrorContext**  
Ist ein Fehler ValidateAndCommit aufrufen, ist es zusätzlicher Kontext für diesen Fehler in diesem Knoten. Hier sind mögliche Werte:

<table>
<colgroup>
<col width="15%" />
<col width="20%" />
<col width="65%" />
</colgroup>
<thead>
<tr class="header">
<th>ErrorContext Wert</th>
<th>Phase, in dem Fehler aufgetreten ist</th>
<th>Beschreibung und Vorschläge</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Unbekannt</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Auffüllen Konto</p></td>
<td><p>Kann nicht mit dem Benutzernamen und Kennwort eingegebenen Kontodetails abrufen.</p>
<ul>
<li>Für Azure AD-Konten stellen Sie sicher, dass UserPrincipalName und das Kennwort gültig sind.</li>
<li>Für AD-Konten stellen Sie sicher, dass DomainName, UserName und Password gültig sind.</li>
<li>Stellen Sie sicher, dass das angegebene Konto ein Exchange Server-Postfach verfügt.</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Auffüllen der Exchange-Serveradresse</p></td>
<td><p>Automatische Erkennung von Ihrem Exchange Server-Adresse kann nicht ausgeführt werden. Versuchen Sie, die Adresse des Exchange-Servers unter Verwendung des Feldes ExchangeServer manuell angeben.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Überprüfen der Exchange-Serveradresse</p></td>
<td><p>Überprüfen die Adresse des Exchange-Servers kann nicht ausgeführt werden. Stellen Sie sicher, dass das Feld ExchangeServer gültig ist.</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>Speichern von Kontoinformationen</p></td>
<td><p>Speichern Kontodetails an das System nicht möglich.</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>Validieren der EAS-Richtlinien</p></td>
<td><p>Das Konto Gerät verwendet eine nicht unterstützte EAS-Richtlinie. Stellen Sie sicher, dass die EAS-Richtlinie entsprechend der Administratorhandbuch ordnungsgemäß konfiguriert ist.</p></td>
</tr>
</tbody>
</table>

 

Der Datentyp ist "int" Unterstützte Vorgang ist Get.

<a href="" id="maintenancehourssimple-hours"></a>**MaintenanceHoursSimple/Stunden**  
Knoten für Wartungszeitplan.

<a href="" id="maintenancehourssimple-hours-starttime"></a>**MaintenanceHoursSimple/Stunden/StartTime**  
Gibt die Startzeit für Wartungszeiten in Minuten aus Mitternacht. Legen Sie diesen Wert beispielsweise um eine Startzeit 2:00 Uhr festzulegen, und 120.

Der Datentyp ist "int" Unterstützte Operation wird Get und ersetzen.

<a href="" id="maintenancehourssimple-hours-duration"></a>**MaintenanceHoursSimple/Stunden/Dauer**  
Gibt die Dauer der Wartungsfenster in Minuten. Legen Sie diesen Wert auf 180 beispielsweise zum Festlegen der Dauer von 3 Stunden.

Der Datentyp ist "int" Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps"></a>**InBoxApps**  
Der Knoten für das Feld in app-Einstellungen.

<a href="" id="inboxapps-welcome"></a>**InBoxApps-Willkommensseite**  
Der Knoten für die Willkommensseite.

<a href="" id="inboxapps-welcome-autowakescreen"></a>**InBoxApps/Willkommen/AutoWakeScreen**  
Aktivieren Sie automatisch mit Bewegungssensoren auf dem Bildschirm.

Der Datentyp ist Bool. Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps-welcome-currentbackgroundpath"></a>**InBoxApps/Willkommen/CurrentBackgroundPath**  
Hintergrundbild für die Seite Willkommen. Geben Sie dies zum Festlegen eine Https-URL zu einer PNG-Datei (nur PNGs sind aus Sicherheitsgründen unterstützt).

Der Datentyp ist Zeichenfolge an. Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps-welcome-meetinginfooption"></a>**InBoxApps/Willkommen/MeetingInfoOption**  
Besprechungsinformationen, die auf der Willkommensseite angezeigt werden.

Gültige Werte:

-   0 – Organisator und nur Uhrzeit
-   1 – organisieren, Zeit und Subject. Betreff wird in privaten Besprechungen ausgeblendet.

Der Datentyp ist "int" Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps-wirelessprojection"></a>**InBoxApps/WirelessProjection**  
Knoten für die app-Einstellungen für drahtlose Projektor.

<a href="" id="inboxapps-wirelessprojection-pinrequired"></a>**InBoxApps/WirelessProjection/PINRequired**  
Benutzer müssen eine PIN Drahtlos an das Gerät bei Project eingeben.

Der Datentyp ist Bool. Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps-wirelessprojection-enabled"></a>**InBoxApps, WirelessProjection, aktiviert**  
Ermöglicht drahtlosen Projektion an dem Gerät.

Der Datentyp ist Bool. Unterstützte Operation wird Get und ersetzen.

<a href="" id="inboxapps-wirelessprojection-channel"></a>**InBoxApps/WirelessProjection/Kanal**  
Drahtlose Kanal für Miracast-Vorgang verwenden. Die unterstützten Kanäle werden durch die Wi-Fi-Allianz Wi-Fi direkte Angabe definiert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Funktioniert mit allen Miracast Absendern in allen Regionen</p></td>
<td><p>1, 3, 4, 5, 6, 7, 8, 9, 10, 11</p></td>
</tr>
<tr class="even">
<td><p>Funktioniert mit allen 5ghz Band Miracast Absender in allen Regionen</p></td>
<td><p>36, 40, 44, 48</p></td>
</tr>
<tr class="odd">
<td><p>Funktioniert mit allen 5ghz band Miracast Absender in allen Regionen außer Japan</p></td>
<td><p>149, 153, 157, 161, 165</p></td>
</tr>
</tbody>
</table>

 

Der Standardwert beträgt 255. Außerhalb von behördlichen wird empfohlen Wenn der Kanal nicht richtig konfiguriert ist der Treiber wird nicht gestartet oder auf der falsche Kanal (der Absender für gesehen wird nicht) übertragen wird.

Der Datentyp ist "int" Unterstützte Operation wird Get und ersetzen.

<a href="" id="properties"></a>**Eigenschaften**  
Knoten für die Geräteeigenschaften.

<a href="" id="properties-friendlyname"></a>**Eigenschaften/FriendlyName**  
Anzeigename des Geräts. Dies ist der Name, der Benutzern angezeigt wird, wenn sie auf das Gerät drahtlos project möchten.

Der Datentyp ist Zeichenfolge. Unterstützte Operation wird Get und ersetzen.

<a href="" id="momagent"></a>**MOMAgent**  
Der Knoten für die Microsoft Operations Management Suite.

<a href="" id="momagent-workspaceid"></a>**MOMAgent/WorkspaceID**  
GUID, die die Microsoft Operations Management Suite Workspace-ID zum Sammeln der Daten identifiziert. Legen Sie dies auf eine leere Zeichenfolge an den MOM-Agent zu deaktivieren.

Der Datentyp ist Zeichenfolge. Unterstützte Operation wird Get und ersetzen.

<a href="" id="momagent-workspacekey"></a>**MOMAgent/WorkspaceKey**  
Der Primärschlüssel für die Authentifizierung mit den Arbeitsbereich.

Der Datentyp ist Zeichenfolge an. Unterstützte Operation wird Get und ersetzen. Der Get-Vorgang ist zulässig, aber es gibt immer eine leere Zeichenfolge zurück.

 

 






