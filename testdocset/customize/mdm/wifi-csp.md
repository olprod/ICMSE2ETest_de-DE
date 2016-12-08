---
title: WiFi CSP
description: WiFi CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f927cb5f-9555-4029-838b-03fb68937f06
ms.openlocfilehash: c417315b5a2b766d515357cd56c573f36f8014d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wifi-csp"></a>WiFi CSP


Der WLAN-Konfigurationsdienstanbieter bietet die Funktionalität zum Hinzufügen oder Löschen von Wi-Fi-Netzwerke auf einem Windows-Gerät. Der Konfigurationsdienstanbieter akzeptiert SyncML Eingabe und zu einem Netzwerkprofil, die auf dem Gerät installiert wird konvertiert. Dieses Profil kann das Gerät mit dem Wi-Fi-Netzwerk zu verbinden, wenn sie im Bereich befindet.

Hinweise zur Programmierung:

-   Wenn die Authentifizierungsmethode ein Zertifikat benötigt, beispielsweise EAP-TLS Clientzertifikate erfordert, müssen Sie ihn durch den Dienstanbieter für CertificateStore Konfiguration konfigurieren. Der WLAN-Konfigurationsdienstanbieter bietet keine dieser Funktionalität. Stattdessen kann das Wi-Fi-Profil Merkmale des Zertifikats an, für die Auswahl des richtigen Zertifikats für das Netzwerk verwendet werden angeben. Der Server muss das Zertifikat zunächst die Wi-Fi-Netzwerkkonfiguration vor dem Bereitstellen von erfolgreich registrieren. Beispielsweise muss der Server für ein EAP-TLS-Profil erfolgreich konfigurieren und registrieren Sie das erforderlichen Clientzertifikat vor der Bereitstellung von der Wi-Fi-Profil. Selbstsigniertes Zertifikat für EAP-TLS/PEAP-MSCHAPv2 funktioniert, aber es wird EAP-TLS nicht unterstützt.
-   Da der Windows 10 Mobile Emulator Wi-Fi nicht unterstützt, testen Sie können nicht die Wi-Fi-Konfiguration mit einem Emulator. Können Sie weiterhin eine Wi-Fi-Netzwerk mit dem WiFi CSP bereitstellen und dann die Wi-Fi-Einstellungsseite einchecken, aber Sie können nicht die Netzwerkkonnektivität im Emulator testen.
-   Schließen Sie für WEP, WPA und WPA2-basierte Netzwerke das Kennwort in der Netzwerkkonfiguration in nur-Text. Der Hauptschlüssel wird automatisch verschlüsselt, wenn sie auf dem Gerät gespeichert ist.
-   Die SSID des Wi-Fi-Netzwerk Teils des Knotens LocURI muss ein gültiger URI basierend auf RFC 2396 sein. Dies erfordert, dass alle nicht-ASCII-Zeichen mit einem Prozentzeichen geschützt werden müssen. Unicode-Zeichen ohne die erforderlichen Escapezeichen werden nicht unterstützt.
-   Die &lt;Namen&gt;*Namen\_wechselt\_hier*&lt;/name&gt;&lt;SSIDConfig&gt; muss übereinstimmen &lt;SSID&gt;&lt;Namen&gt; *Namen\_wechselt\_hier*&lt;/name&gt;&lt;/SSID&gt;.
-   Für den CSP WiFi nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.
-   Verwenden Proxyis nur in Windows 10 Mobile unterstützt. Mit dieser Konfiguration in Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) führt zu Fehler.

Die folgende Abbildung zeigt den WiFi Konfiguration-Dienstanbieter im Strukturformat dar.

![Wi-Fi Csp Diagramm](images/provisioning-csp-wifi.png)

In der folgenden Liste sind die Merkmale und Parameter.

<a href="" id="profile"></a>**Profil**  
Identifiziert die Wi-Fi-Netzwerkkonfiguration. Jede Wi-Fi-Netzwerkkonfiguration wird durch ein Profile-Objekt dargestellt. Dieses Netzwerkprofil enthält alle Informationen für das Gerät für die Verbindung mit dem Netzwerk – beispielsweise die SSID, Authentifizierung und Verschlüsselungsmethoden und Passphrase im Fall eines WAN-WEP oder WPA2 Netzwerke erforderlich.

Unterstützte Vorgang ist Get.

<a href="" id="-ssid-"></a>***&lt;SSID&gt;***  
Gibt den Namen des Netzwerks Wi-Fi (maximal 32 Bytes) zu erstellen, konfigurieren, Abfragen oder löschen. Der Name wird die Groß-/Kleinschreibung beachtet, und kann in ASCII dargestellt werden. Die SSID wird hinzugefügt, wenn der WlanXML Knoten hinzugefügt wird. Wenn der SSID Knoten gelöscht wird, werden auch alle untergeordneten Knoten gelöscht.

SSID ist der Name des Netzwerks, Verbindung werden zwar Profilname den Namen des Profils, die WiFi Einstellungsinformationen enthält. Wenn der Name der Benutzerprofildienst rechten nicht festgelegt ist in der SyncML MDM gemäß den Anweisungen in der Informationen in den Einstellungen WiFi XML, kann es zu unerwartete Fehler führen. Beispielsweise &lt;LocURI&gt;./Vendor/MSFT/WiFi/Profile/&lt;*MÜSSEN WERDEN NAMEN DES PROFILS AS PRO WIFI XML*&gt;/WlanXml&lt;/LocURI&gt;.

Die unterstützten Vorgänge sind hinzufügen, abrufen, löschen, und Ersetzen Sie.

<a href="" id="wlanxml"></a>**WlanXML**  
Der XML-CODE, der beschreibt der Netzwerkkonfiguration und folgt der [WLAN\_profile Schema](http://go.microsoft.com/fwlink/p/?LinkId=325608) auf MSDN.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

Werttyp ist chr.

Das XML-Profil muss Escapezeichen umgewandelt werden, wie in den folgenden Beispielen gezeigt.

Wenn sie in den Blob vorhanden ist, müssen die **Schlüsseltyp** und **geschützte** Elemente vor **KeyMaterial**, stehen, wie im Beispiel in [WPA2-Persönlich Profil Beispiel](http://go.microsoft.com/fwlink/p/?LinkId=523870)dargestellt.

> **Hinweis**  Wenn Sie müssen angeben Sonstiges erweiterte angeben von Kriterien für Zertifikate, die von der Wi-Fi-Profil verwendet werden können möchten, dies über den EapHostConfig Teil der WlanXML angeben. Weitere Informationen finden Sie unter [EAP-Konfiguration](http://go.microsoft.com/fwlink/p/?LinkId=618963).

 

Die unterstützten Vorgänge sind hinzufügen, abrufen, löschen, und Ersetzen Sie.

<a href="" id="proxy"></a>**Proxy**  
Optional Gibt die Konfiguration des Netzwerk-Proxy. Pro Verbindung für Windows 10 Mobile können einen Proxy-Server-Host und Port angegeben werden. Diese Proxy-Konfiguration ist nur in Windows 10 Mobile unterstützt. Verwenden diese Konfiguration in Windows 10 für desktop Edition führt zu Fehler.

Das Format ist *Host: Port ein*, auf dem Host Folgendes möglich:

-   Ein registrierte Hostname, wie Servername, FQDN oder einzelne Bezeichnung, beispielsweise MeinWeb anstelle von myweb.contoso.com.
-   IPv4-Adresse
-   / IPvFuture IPv6-Adresse.

Wenn es eine IPvFuture-Adresse ist, muss als eine IP-Adresse als literal angegeben werden "\[" (IP-V6-Adresse / IPvFuture) "\]", z. B. "\[2441:4880:28:3:204:76ff:f43f:6eb\]: 8080".

Unterstützte Vorgänge sind Get, hinzufügen, löschen und ersetzen.

<a href="" id="disableinternetconnectivitychecks"></a>**DisableInternetConnectivityChecks**  
In Windows 10, Version 1511.Optional hinzugefügt. Deaktivieren Sie das Kontrollkästchen Internet Connectivity für das Profil.

Werttyp ist chr.

-   True - ist Internet Connectivity Kontrollkästchen deaktiviert.
-   False – ist Internet Connectivity Kontrollkästchen aktiviert.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="proxypacurl"></a>**ProxyPacUrl**  
In Windows 10, Version 1607 hinzugefügt. Optional Gibt den Wert der URL zum Speicherort Proxy AutoConfig (PAC) Datei. Diese Proxy-Konfiguration ist nur in Windows 10 Mobile unterstützt.

Werttyp ist chr, z. B. http://www.contoso.com/wpad.dat an.

<a href="" id="proxywpad"></a>**ProxyWPAD**  
In Windows 10, Version 1607 hinzugefügt. Optional Bei Festlegung auf true fest, es Web Proxy Auto-Discovery-Protokoll (WPAD) zum Nachschlagen von Proxy aktiviert. Diese Proxy-Konfiguration ist nur in Windows 10 Mobile unterstützt.

Werttyp ist Bool.

## <a name="examples"></a>Beispiele


Diese XML-Beispielen gezeigt, wie verschiedene Aufgaben mit OMA DM.

### <a name="add-a-network"></a>Hinzufügen eines Netzwerks

Im folgenden Beispiel wird gezeigt, wie PEAP-MSCHAPv2 Netzwerk mit SSID 'MyNetwork', eine Proxy-URL 'Testproxy,' hinzufügen und port 80.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Atomic>
      <CmdID>301</CmdID>
      <Add>
        <CmdID>302</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
          </Meta>
          <Data>&lt;?xml version=&quot;1.0&quot;?&gt;&lt;WLANProfile xmlns=&quot;http://contoso.com/networking/WLAN/profile/v1&quot;&gt;&lt;name&gt;MyNetwork&lt;/name&gt;&lt;SSIDConfig&gt;&lt;SSID&gt;&lt;hex&gt;412D4D534654574C414E&lt;/hex&gt;&lt;name&gt;MyNetwork&lt;/name&gt;&lt;/SSID&gt;&lt;nonBroadcast&gt;false&lt;/nonBroadcast&gt;&lt;/SSIDConfig&gt;&lt;connectionType&gt;ESS&lt;/connectionType&gt;&lt;connectionMode&gt;manual&lt;/connectionMode&gt;&lt;MSM&gt;&lt;security&gt;&lt;authEncryption&gt;&lt;authentication&gt;WPA2&lt;/authentication&gt;&lt;encryption&gt;AES&lt;/encryption&gt;&lt;useOneX&gt;true&lt;/useOneX&gt;&lt;/authEncryption&gt;&lt;OneX xmlns=&quot;http://contoso.com/networking/OneX/v1&quot;&gt;&lt;authMode&gt;user&lt;/authMode&gt;&lt;EAPConfig&gt;&lt;EapHostConfig xmlns=&quot;http://contoso.com/provisioning/EapHostConfig&quot;&gt;&lt;EapMethod&gt;&lt;Type xmlns=&quot;http://contoso.com/provisioning/EapCommon&quot;&gt;25&lt;/Type&gt;&lt;VendorId xmlns=&quot;http://contoso.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns=&quot;http://contoso.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns=&quot;http://contoso.com/provisioning/EapCommon&quot;&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns=&quot;http://contoso.com/provisioning/EapHostConfig&quot;&gt;&lt;Eap xmlns=&quot;http://contoso.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt;&lt;Type&gt;25&lt;/Type&gt;&lt;EapType xmlns=&quot;http://contoso.com/provisioning/MsPeapConnectionPropertiesV1&quot;&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;true&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;FastReconnect&gt;true&lt;/FastReconnect&gt;&lt;InnerEapOptional&gt;false&lt;/InnerEapOptional&gt;&lt;Eap xmlns=&quot;http://contoso.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt;&lt;Type&gt;26&lt;/Type&gt;&lt;EapType xmlns=&quot;http://contoso.com/provisioning/MsChapV2ConnectionPropertiesV1&quot;&gt;&lt;UseWinLogonCredentials&gt;false&lt;/UseWinLogonCredentials&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;EnableQuarantineChecks&gt;false&lt;/EnableQuarantineChecks&gt;&lt;RequireCryptoBinding&gt;false&lt;/RequireCryptoBinding&gt;&lt;PeapExtensions&gt;&lt;PerformServerValidation xmlns=&quot;http://contoso.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns=&quot;http://contoso.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;false&lt;/AcceptServerName&gt;&lt;/PeapExtensions&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;&lt;/EAPConfig&gt;&lt;/OneX&gt;&lt;/security&gt;&lt;/MSM&gt;&lt;/WLANProfile&gt; </Data>
        </Item>
      </Add>
      <Add>
        <CmdID>$CmdID$</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/Proxy</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
          </Meta>
          <Data>testproxy:80</Data>
        </Item>
      </Add>
    </Atomic>
    <Final/>
  </SyncBody>
</SyncML>
```

### <a name="query-network-profiles"></a>Abfrage Netzwerkprofile

Im folgenden Beispiel wird gezeigt, wie Wi-Fi-Profile installiert auf einem Server MDM Abfragen.

``` syntax
<Get> 
   <CmdID>301</CmdID> 
   <Item> 
      <Target> 
         <LocURI>./Vendor/MSFT/WiFi/Profile</LocURI> 
      </Target> 
   </Item> 
</Get>
```

Das folgende Beispiel zeigt die Antwort.

``` syntax
<Results> 
   <CmdID>3</CmdID> 
   <MsgRef>1</MsgRef> 
   <CmdRef>301</CmdRef>
   <Item> 
      <Source><LocURI>./Vendor/MSFT/WiFi/Profile</LocURI></Source> 
      <Meta><Format xmlns="syncml:metinf">node</Format></Meta> 
      <Data>TestWLAN1/TestWLAN2</Data> 
   </Item> 
</Results>
```

### <a name="remove-a-network"></a>Entfernen eines Netzwerks

Im folgenden Beispiel wird veranschaulicht, wie ein Netzwerk mit 'MyNetwork' SSID und kein Proxy zu entfernen. Entfernen alle Netzwerk Authentifizierungstypen erfolgt in diese Art und Weise.

``` syntax
<Atomic>
      <CmdID>300</CmdID>
      <Delete>
        <CmdID>301</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
          </Target>
        </Item>
      </Delete>
</Atomic>
```

### <a name="add-a-network-and-certification-authority-for-a-server-certificate"></a>Hinzufügen einer Zertifizierungsstelle Netzwerk- und Zertifizierung für ein Serverzertifikat

Das folgende Beispiel veranschaulicht das Hinzufügen von PEAP-MSCHAPv2 Netzwerk mit 'MyNetwork' SSID und Root CA Validierung Serverzertifikat.

``` syntax
<Atomic>
      <CmdID>300</CmdID>
      <Add>
        <CmdID>301</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
          </Meta>
          <Data>&lt;?xml version=&quot;1.0&quot;?&gt;&lt;WLANProfile xmlns=&quot;http://www.microsoft.com/networking/WLAN/profile/v1&quot;&gt;&lt;name&gt;MyNetwork&lt;/name&gt;&lt;SSIDConfig&gt;&lt;SSID&gt;&lt;name&gt;MyNetwork&lt;/name&gt;&lt;/SSID&gt;&lt;nonBroadcast&gt;false&lt;/nonBroadcast&gt;&lt;/SSIDConfig&gt;&lt;connectionType&gt;ESS&lt;/connectionType&gt;&lt;connectionMode&gt;manual&lt;/connectionMode&gt;&lt;MSM&gt;&lt;security&gt;&lt;authEncryption&gt;&lt;authentication&gt;WPA2&lt;/authentication&gt;&lt;encryption&gt;AES&lt;/encryption&gt;&lt;useOneX&gt;true&lt;/useOneX&gt;&lt;/authEncryption&gt;&lt;OneX xmlns=&quot;http://www.microsoft.com/networking/OneX/v1&quot;&gt;&lt;authMode&gt;user&lt;/authMode&gt;&lt;EAPConfig&gt;&lt;EapHostConfig xmlns=&quot;http://www.microsoft.com/provisioning/EapHostConfig&quot;&gt;&lt;EapMethod&gt;&lt;Type xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;25&lt;/Type&gt;&lt;VendorId xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns=&quot;http://www.microsoft.com/provisioning/EapCommon&quot;&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns=&quot;http://www.microsoft.com/provisioning/EapHostConfig&quot;&gt;&lt;Eap xmlns=&quot;http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt;&lt;Type&gt;25&lt;/Type&gt;&lt;EapType xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1&quot;&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;true&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;TrustedRootCA&gt; InsertCertThumbPrintHere &lt;/TrustedRootCA&gt;&lt;/ServerValidation&gt;&lt;FastReconnect&gt;true&lt;/FastReconnect&gt;&lt;InnerEapOptional&gt;false&lt;/InnerEapOptional&gt;&lt;Eap xmlns=&quot;http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1&quot;&gt;&lt;Type&gt;26&lt;/Type&gt;&lt;EapType xmlns=&quot;http://www.microsoft.com/provisioning/MsChapV2ConnectionPropertiesV1&quot;&gt;&lt;UseWinLogonCredentials&gt;false&lt;/UseWinLogonCredentials&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;EnableQuarantineChecks&gt;false&lt;/EnableQuarantineChecks&gt;&lt;RequireCryptoBinding&gt;false&lt;/RequireCryptoBinding&gt;&lt;PeapExtensions&gt;&lt;PerformServerValidation xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;true&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns=&quot;http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2&quot;&gt;false&lt;/AcceptServerName&gt;&lt;/PeapExtensions&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;&lt;/EAPConfig&gt;&lt;/OneX&gt;&lt;/security&gt;&lt;/MSM&gt;&lt;/WLANProfile&gt; </Data>
        </Item>
      </Add>
</Atomic>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






