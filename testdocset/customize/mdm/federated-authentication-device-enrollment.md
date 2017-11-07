---
title: "Verbundauthentifizierung Gerät Registrierung"
description: "Dieser Abschnitt enthält ein Beispiel für das mobile Gerät Registrierung Protokoll Verbundauthentifizierung Richtlinie verwenden."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 049ECA6E-1AF5-4CB2-8F1C-A5F22D722DAA
ms.openlocfilehash: 230f54c834822f6f2232b94b433a87c8bafc0e47
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="federated-authentication-device-enrollment"></a>Verbundauthentifizierung Gerät Registrierung


Dieser Abschnitt enthält ein Beispiel für das Mobilgerät Registrierung Protokoll Verbundauthentifizierung Richtlinie verwenden. Wenn die Authentifizierungsrichtlinie auf Federated festgelegt ist, wird der Web-Authentifizierungsbroker vom Client Registrierung ein Sicherheitstoken abgerufen genutzt. Der Registrierung Client Ruft den Web-Authentifizierungsbroker API innerhalb der Antwortnachricht zum Starten des Prozesses. Der Server sollte im Web erstellen Authentifizierung Broker Seiten dem Bildschirm gestreckt und sollte mit der vorhandenen Registrierung Benutzeroberfläche konsistent sein. Das undurchsichtig Sicherheitstoken, das aus der Broker zurückgegeben wird, eine Endseite als das Gerät Sicherheit Geheimnis während des Aufrufs von Client-Zertifikat-Anforderung vom Client Registrierung verwendet wird.

Die &lt;AuthenticationServiceURL&gt; -Element der Discovery-Antwortnachricht gibt Web Authentifizierung Broker Seite Start-URL an.

Ausführliche Informationen zu Microsoft Mobilgerät Registrierungs-Protokoll für Windows 10, finden Sie unter [ \[MS-MDE2\]: Mobile Device Registrierung Protocol Version 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347).

## <a name="in-this-topic"></a>In diesem Thema


[Suchdienst](#discovery-service)  
[Registrierung-Webdienst](#enrollment-policy-web-service)  
[Registrierungs-Webdienst](#enrollment-web-service)  

Die Liste der Registrierung Szenarien in Windows 10 nicht unterstützt finden Sie unter [Registrierung Szenarien nicht unterstützt](mobile-device-enrollment.md#enrollment-scenarios-not-supported).

## <a name="discovery-service"></a>Suchdienst


Der Discovery-Webdienst bietet die Konfigurationsinformationen für einen Benutzer zum Registrieren von ein Telefon mit einem Verwaltungsdienst erforderlich. Der Dienst ist ein Rest-Webdienst über HTTPS (gilt nur für Serverauthentifizierung).

> **Hinweis**  Der Administrator von der Discovery-Dienst muss einen Host mit der Adresse Enterpriseenrollment erstellen. *Domäne\_Namen*. com.

 

Der automatische Ermittlung Ablauf des Geräts verwendet den Domänennamen der e-Mail-Adresse, die bei der Anmeldung an dem Bildschirm Jahrestag Einstellungen übermittelt wurde. Das System für die automatische Ermittlung erstellt einen URI, der dieser Hostname durch Anfügen der Unterdomäne "Enterpriseenrollment" auf die Domäne der e-Mail-Adresse und den durch den Pfad anhängen verwendet "/ EnrollmentServer/Discovery.svc". Wenn die e-Mail-Adresse ist beispielsweise “sample@contoso.com”, der resultierende URI für den ersten Get-Anforderung wäre: http:<span></span>//enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc

Die erste Anforderung ist ein standard-HTTP GET-Anforderung.

Das folgende Beispiel zeigt eine über HTTP GET-Anforderung an den angegebenen Discovery-Server user@contoso.com als die e-Mail-Adresse.

```
Request Full Url: http://EnterpriseEnrollment.contoso.com/EnrollmentServer/Discovery.svc
Content Type: unknown
Header Byte Count: 153
Body Byte Count: 0
```

```
GET /EnrollmentServer/Discovery.svc HTTP/1.1
User-Agent: Windows Phone 8 Enrollment Client
Host: EnterpriseEnrollment.contoso.com
Pragma: no-cache
```

```
Request Full Url: http://EnterpriseEnrollment.contoso.com/EnrollmentServer/Discovery.svc
Content Type: text/html
Header Byte Count: 248
Body Byte Count: 0
```

```
HTTP/1.1 200 OK
Connection: Keep-Alive
Pragma: no-cache
Cache-Control: no-cache
Content-Type: text/html
Content-Length: 0
```

Nachdem das Gerät eine Antwort vom Server erhält, sendet das Gerät eine POST-Anforderung an Enterpriseenrollment. *Domäne\_Namen*/EnrollmentServer/Discovery.svc. Nachdem sie eine weitere Antwort vom Server ruft (die das Gerät angeben sollten, wo ist der Registrierung Server), werden die nächste Nachricht vom Gerät gesendet Enterpriseenrollment. *Domäne\_Namen* an den Server für die Registrierung.

Die folgenden Logik angewendet wird:

1.  Das Gerät versucht zuerst HTTPS. Wenn das Server-Zertifikat vom Gerät nicht vertrauenswürdig ist, schlägt die HTTPS.
2.  Wenn dies nicht funktioniert, versucht das Gerät HTTP, um festzustellen, ob es umgeleitet wird:
    -   Wenn das Gerät nicht umgeleitet wird, werden den Benutzer die Adresse des Servers aufgefordert.
    -   Wenn das Gerät umgeleitet wird, es der Benutzer aufgefordert, die Umleitung zu ermöglichen.

Im folgenden Beispiel wird eine Anforderung über eine HTTP POST-Befehl des Webdiensts Discovery angegebenen user@contoso.com als die e-Mail-Adresse

```
https://EnterpriseEnrollment.Contoso.com/EnrollmentServer/Discovery.svc
```

Das folgende Beispiel zeigt die Discovery-Service-Anforderung.

``` syntax
    <?xml version="1.0"?>
    <s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
       xmlns:s="http://www.w3.org/2003/05/soap-envelope">
      <s:Header>
        <a:Action s:mustUnderstand="1">
          http://schemas.microsoft.com/windows/management/2012/01/enrollment/IDiscoveryService/Discover
        </a:Action>
        <a:MessageID>urn:uuid: 748132ec-a575-4329-b01b-6171a9cf8478</a:MessageID>
        <a:ReplyTo>
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
        </a:ReplyTo>
        <a:To s:mustUnderstand="1">
          https://ENROLLTEST.CONTOSO.COM/EnrollmentServer/Discovery.svc
        </a:To>
      </s:Header>
      <s:Body>
        <Discover xmlns="http://schemas.microsoft.com/windows/management/2012/01/enrollment/">
          <request xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <EmailAddress>user@contoso.com</EmailAddress>
            <OSEdition>3</OSEdition> <!--New -->
            <RequestVersion>3.0</RequestVersion> <!-- Updated -->
            <DeviceType>WindowsPhone</DeviceType> <!--Updated -->
            <ApplicationVersion>10.0.0.0</ApplicationVersion>
            <AuthPolicies>
                <AuthPolicy>OnPremise</AuthPolicy>
                <AuthPolicy>Federated</AuthPolicy>
            </AuthPolicies>
          </request>
        </Discover>
      </s:Body>
```

Die Antwort Discovery ist im XML-Format und enthält die folgenden Felder:

-   Registrierung Dienst-URL (EnrollmentServiceUrl) – gibt die URL des Endpunkts Registrierung, die von der Verwaltungsdienst verfügbar gemacht wird. Das Gerät sollte diese URL aufrufen, nachdem der Benutzer authentifiziert wurde. Dieses Feld ist erforderlich.
-   Authentifizierungsrichtlinie (AuthPolicy) – gibt an, welche Art der Authentifizierung erforderlich ist. Für den Server MDM ist lokale Verwaltungs den unterstützten Wert, was bedeutet, dass der Benutzer beim Aufrufen der Verzeichnisverwaltungsdienst-URL authentifiziert werden. Dieses Feld ist erforderlich.
-   In Windows wird Federated als einen anderen unterstützten Wert hinzugefügt. Dadurch kann der Server Nutzen der Web-Authentifizierungsbroker zum Ausführen der benutzerdefinierten Authentifizierung, und der Nutzung Annahme Ausdruckssätzen.

> **Hinweis**  Die HTTP-Antwort vom Server muss nicht chunked werden; Es muss als eine Nachricht gesendet werden.

 

Wenn Authentifizierungsrichtlinie festgelegt ist, werden wird Federated, Web-Authentifizierung Broker (WAB) vom Client Registrierung ein Sicherheitstoken abgerufen genutzt werden. Das WAB-Startseite, die URL durch den Discovery-Dienst in der Antwortnachricht bereitgestellt wird. Der Registrierung-Client wird die API WAB innerhalb der Antwortnachricht zum Starten des Prozesses WAB aufrufen. WAB Seiten sind Webseiten Server gehostet. Der Server sollte diesen Seiten, um dem Bildschirm gut passt und so konsistent wie möglich zu anderen Builds in der Registrierung MDM Benutzeroberfläche erstellt werden. Das undurchsichtig Sicherheitstoken von WAB zurückgegeben wird, da ein Endpage vom Client Registrierung als das Gerät Sicherheit Geheimnis während des Aufrufs der Client Zertifikat Registrierungs-Anforderung verwendet wird.

> **Hinweis**  Verwenden Sie anstelle der vertrauenden Seite auf die Benutzer-Agent-Zeichenfolge, die während der Authentifizierung zum Abrufen von Informationen, wie die Betriebssystemversion übergeben wird die folgende Hinweise:
> -   Analysieren Sie die Version des Betriebssystems aus den Daten, die während der Discovery-Anforderung gesendet.
> -   Fügen Sie der Version des Betriebssystems als Parameter in der AuthenticationServiceURL.
> -   Wenn das Betriebssystem für die Authentifizierung sendet die Version des Betriebssystems aus der AuthenticiationServiceURL analysiert.

 

Neues XML-Tag AuthenticationServiceUrl, wird in der DiscoveryResponse von XML in der Server WAB Seite Start-URL angeben kann eingeführt. Für die Authentifizierung Federated muss dieses XML-Tag vorhanden sein.

> **Hinweis**  Der Registrierung Client ist unabhängig im Hinblick auf die Abläufe Protokoll für die Authentifizierung und das Sicherheitstoken zurückgeben. Während der Server möglicherweise Aufforderung zur Eingabe der Anmeldeinformationen des Benutzers direkt oder in einer verbundprotokoll mit einem anderen Server und dem Verzeichnis-Dienst eingeben, wird die Registrierung-Client auf all dies unabhängig. Um unabhängig bleiben, werden alle Protokoll Datenflüsse zur Authentifizierung betreffen, an denen den Registrierung Client beteiligt passiv, der Browser implementiert ist.

 

Im folgenden werden die expliziten Anforderungen für den Server.

-   Die &lt;DiscoveryResponse&gt;&lt;AuthenticationServiceUrl&gt; Element muss HTTPS unterstützen.
-   Der Authentifizierungsserver muss ein vertrauenswürdigen Stammzertifikats Gerät verwenden. Andernfalls wird der Anruf WAP fehl.
-   WP unterstützt Fenster integrierte Authentifizierung (WIA) für ADFS während der WAB Authentifizierung keine. ADFS 2012 R2, wenn muss kein Versuch WIA für Windows-Gerät konfiguriert werden.

Der Registrierung-Client sendet eine HTTPS-Anforderung wie folgt:

```
AuthenticationServiceUrl?appru=<appid>&amp;login_hint=<User Principal Name>
```

-   &lt;AppID&gt; wird von der Form ms-App://string
-   &lt;Benutzerprinzipalname&gt; ist der Name des Benutzers eingeschrieben, beispielsweise user@constoso.com als Eingabe durch den Benutzer in einer Registrierung anmelden-Seite. Der Wert dieses Attributs dient als einen Hinweis, der als Teil der Authentifizierung durch den Authentifizierungsserver verwendet werden kann.

Nach der Authentifizierung abgeschlossen ist, sollte der Authentifizierungsserver ein HTML-Formulardokument mit einer Aktion NACH der Methode der Appid identifiziert, in dem Abfragezeichenfolgen-Parameter zurückgegeben.

```
HTTP/1.1 200 OK 
Content-Type: text/html; charset=UTF-8
Vary: Accept-Encoding
Content-Length: 556

<!DOCTYPE>
<html>
   <head>
      <title>Working...</title>
      <script>
         function formSubmit() {
            document.forms[0].submit();
         }
           window.onload=formSubmit;
      </script>
   </head>
   <body>
    <!-- appid below in post command must be same as appid in previous client https request. -->
      <form method="post" action="ms-app://appid">
         <p><input type="hidden" name="wresult" value="token value"/></p>
         <input type="submit"/>
      </form>
   </body>
</html>
```

Der Server verfügt über eine POST-ANFORDERUNG an eine umleitungs-URL des dem Formular ms-App://string (das URL-Schema ist ms-app) senden, wie in der Aktion NACH der Methode angegeben. Der Security token-Wert ist die base64-codierte Zeichenfolge "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd\#base64binary" enthalten, der &lt;Wsse:BinarySecurityToken&gt; EncodingType-Attribut. Windows wird die Binärdatei codieren, wenn er es wieder auf Registrierungs-Server, in der Form es einfach HTML sendet ist-codiert. Diese Zeichenfolge ist undurchsichtig an den Client Registrierung; der Client kann nicht die Zeichenfolge interpretieren.

Das folgende Beispiel zeigt eine Antwort erhalten vom Web Discovery-Dienst, der Authentifizierung über WAB erforderlich sind.

``` syntax
    <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
       xmlns:a="http://www.w3.org/2005/08/addressing">
      <s:Header>
        <a:Action s:mustUnderstand="1">
          http://schemas.microsoft.com/windows/management/2012/01/enrollment/IDiscoveryService/DiscoverResponse
        </a:Action>
        <ActivityId>
          d9eb2fdd-e38a-46ee-bd93-aea9dc86a3b8
        </ActivityId>
        <a:RelatesTo>urn:uuid: 748132ec-a575-4329-b01b-6171a9cf8478</a:RelatesTo>
      </s:Header>
      <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <DiscoverResponse
           xmlns="http://schemas.microsoft.com/windows/management/2012/01/enrollment">
          <DiscoverResult>
            <AuthPolicy>Federated</AuthPolicy>
            <EnrollmentVersion>3.0</EnrollmentVersion>
            <EnrollmentPolicyServiceUrl>
              https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentPolicyServiceUrl>
            <EnrollmentServiceUrl>
              https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentServiceUrl>
            <AuthenticationServiceUrl>
              https://portal.manage.contoso.com/LoginRedirect.aspx
            </AuthenticationServiceUrl>
          </DiscoverResult>
        </DiscoverResponse>
      </s:Body>
    </s:Envelope>
```

## <a name="enrollment-policy-web-service"></a>Registrierung-Webdienst


Dienst für die Informationsverwaltungsrichtlinie ist optional. Standardmäßig werden keine Richtlinien angegeben, die minimale Schlüssellänge ist 2k und der Hashalgorithmus ist SHA-1.

Dieser Webdienst implementiert die x. 509-Zertifikat-Registrierung Richtlinie Protocol (MS-XCEP)-Spezifikation, die Möglichkeit zum Anpassen der Registrierung von Zertifikaten zu unterschiedlichen Zeiten unterschiedliche sicherheitsanforderungen Unternehmen entsprechend (kryptografische Flexibilität). Der Dienst verarbeitet die Nachricht GetPolicies vom Client, authentifiziert den Client und übereinstimmenden Registrierungsrichtlinien für in der Nachricht GetPoliciesResponse zurückgegeben.

Für Federated Authentifizierungsrichtlinie, wird die Sicherheitsanmeldeinformationen token in einer Nachricht mit Anforderung bereitgestellt der &lt;Wsse:BinarySecurityToken&gt; Element \[WSS\]. Das Sicherheitstoken wird abgerufen, wie im Abschnitt Antwort Discovery beschrieben. Die Authentifizierungsinformationen lautet wie folgt:

-   Security: der Registrierung Client implementiert die &lt;Security&gt; Element im definierten \[WSS\] Abschnitt 5. Die &lt;Security&gt; -Element muss ein untergeordnetes Element des werden die &lt;S:Header&gt; Element.
-   Wsse:BinarySecurityToken: der Registrierung Client implementiert die &lt;Wsse:BinarySecurityToken&gt; Element im definierten \[WSS\] Abschnitt 6.3. Die &lt;Wsse:BinarySecurityToken&gt; Element als untergeordnetes Element des enthalten darf die &lt;Security&gt; Element im SOAP-Header.

Wie in der Antwort Discovery beschrieben wurde Abschnitt die Aufnahme der &lt;Wsse:BinarySecurityToken&gt; Element nicht transparent an den Client Registrierung und der Client kann nicht die Zeichenfolge interpretieren ist und die Aufnahme des Elements wird vom Server Tokenauthentifizierung Sicherheit vereinbart (siehe die &lt;AuthenticationServiceUrl&gt; Element des &lt;DiscoveryResponse&gt; und Enterprise-Server.

Die &lt;Wsse:BinarySecurityToken&gt; Element enthält eine base64-codierte Zeichenfolge. Der Registrierung-Client verwendet das Sicherheitstoken empfangen aus dem Authentifizierungsserver und base64-codiert das Token zum Auffüllen der &lt;Wsse:BinarySecurityToken&gt; Element. Wsse:BinarySecurityToken/Attribute/Werttyp: die &lt;Wsse:BinarySecurityToken&gt; Werttyp-Attribut muss "http:<span></span>/ / schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken".

Wsse:BinarySecurityToken/Attribute/EncodingType: die &lt;Wsse:BinarySecurityToken&gt; EncodingType-Attribut muss "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd\#base64binary".

Folgendes ist ein Beispiel für Registrierung Richtlinie-Anforderung mit einer empfangenen Sicherheitstoken als Clientanmeldeinformationen ein.

``` syntax
    <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
       xmlns:a="http://www.w3.org/2005/08/addressing"
       xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
       xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
       xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"
       xmlns:ac="http://schemas.xmlsoap.org/ws/2006/12/authorization">
      <s:Header>
        <a:Action s:mustUnderstand="1">
          http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy/IPolicy/GetPolicies
        </a:Action>
        <a:MessageID>urn:uuid:72048B64-0F19-448F-8C2E-B4C661860AA0</a:MessageID>
        <a:ReplyTo>
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
        </a:ReplyTo>
        <a:To s:mustUnderstand="1">
          https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
        </a:To>
        <wsse:Security s:mustUnderstand="1">
          <wsse:BinarySecurityToken  ValueType= 
    "http: //schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken"
          EncodingType=
          "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
          xmlns=
          "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          B64EncodedSampleBinarySecurityToken
          </wsse:BinarySecurityToken>
        </wsse:Security>
      </s:Header>
      <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <GetPolicies
           xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy">
          <client>
            <lastUpdate xsi:nil="true"/>
            <preferredLanguage xsi:nil="true"/>
          </client>
          <requestFilter xsi:nil="true"/>
        </GetPolicies>
      </s:Body>
    </s:Envelope>
```

Nachdem der Benutzer authentifiziert ist, ruft der Webdienst die Zertifikatvorlage, dass der Benutzer mit registrieren sollte und Registrierungsrichtlinien basierend auf den Eigenschaften der Vorlage erstellt. Ein Beispiel für die Antwort finden Sie auf MSDN.

MS-XCEP unterstützt sehr flexibel Registrierungsrichtlinien mithilfe von verschiedenen komplexe Typen und Attribute. Für Windows-Gerät unterstützen wir zunächst den MinimalKeyLength, der HashAlgorithmOIDReference Richtlinien und der CryptoProviders. Die HashAlgorithmOIDReference hat OID und OIDReferenceID und PolicySchema in der GetPolicesResponse miteinander verknüpft. Die PolicySchema bezieht sich auf die Version der Formularvorlage Zertifikat. MS-XCEP-Version 3 unterstützt Hashalgorithmen an.

> **Hinweis**  Die HTTP-Antwort vom Server muss nicht chunked werden; Es muss als eine Nachricht gesendet werden.

 

Der folgende Codeausschnitt zeigt die Richtlinie Webdienstantwort.

``` syntax
      <s:Envelope
         xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
         xmlns:s="http://www.w3.org/2003/05/soap-envelope"
         xmlns:a="http://www.w3.org/2005/08/addressing">
        <s:Header>
          <a:Action s:mustUnderstand="1">
            http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy/IPolicy/GetPoliciesResponse
          </a:Action>
          <a:RelatesTo>urn:uuid: 69960163-adad-4a72-82d2-bb0e5cff5598</a:RelatesTo>
        </s:Header>
        <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xmlns:xsd="http://www.w3.org/2001/XMLSchema">
          <GetPoliciesResponse
             xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy">
            <response>
            <policyID />
              <policyFriendlyName xsi:nil="true"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
              <nextUpdateHours xsi:nil="true"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
              <policiesNotChanged xsi:nil="true"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
              <policies>
                <policy>
                  <policyOIDReference>0</policyOIDReference>
                  <cAs xsi:nil="true" />
                  <attributes>
                    <commonName>CEPUnitTest</commonName>
                    <policySchema>3</policySchema>
                    <certificateValidity>
                      <validityPeriodSeconds>1209600</validityPeriodSeconds>
                      <renewalPeriodSeconds>172800</renewalPeriodSeconds>
                    </certificateValidity>
                    <permission>
                      <enroll>true</enroll>
                      <autoEnroll>false</autoEnroll>
                    </permission>
                    <privateKeyAttributes>
                      <minimalKeyLength>2048</minimalKeyLength>
                      <keySpec xsi:nil="true" />
                      <keyUsageProperty xsi:nil="true" />
                      <permissions xsi:nil="true" />
                      <algorithmOIDReference xsi:nil="true" />
                      <cryptoProviders xsi:nil="true" />
                    </privateKeyAttributes>
                    <revision>
                      <majorRevision>101</majorRevision>
                      <minorRevision>0</minorRevision>
                    </revision>
                    <supersededPolicies xsi:nil="true" />
                    <privateKeyFlags xsi:nil="true" />
                    <subjectNameFlags xsi:nil="true" />
                    <enrollmentFlags xsi:nil="true" />
                    <generalFlags xsi:nil="true" />
                    <hashAlgorithmOIDReference>0</hashAlgorithmOIDReference>
                    <rARequirements xsi:nil="true" />
                    <keyArchivalAttributes xsi:nil="true" />
                    <extensions xsi:nil="true" />
                  </attributes>
                </policy>
              </policies>
            </response>
            <cAs xsi:nil="true" />
            <oIDs>
              <oID>
                <value>1.3.14.3.2.29</value>
                <group>1</group>
                <oIDReferenceID>0</oIDReferenceID>
                <defaultName>szOID_OIWSEC_sha1RSASign</defaultName>
              </oID>
            </oIDs>
          </GetPoliciesResponse>
        </s:Body>
      </s:Envelope>
```

## <a name="enrollment-web-service"></a>Registrierungs-Webdienst


Dieser Webdienst implementiert das MS-WSTEP-Protokoll. Verarbeitet die Nachricht RequestSecurityToken (RST) vom Client, der Client authentifiziert, fordert das Zertifikat von der Zertifizierungsstelle und wird in die RequestSecurityTokenResponse (RST-ANTWORT) an dem Client zurückgegeben. Neben den ausgestellte Zertifikat enthält die Antwort auch Konfigurationen erforderlich, um den Client DM bereitstellen.

RequestSecurityToken (RST) müssen die Anmeldeinformationen des Benutzers und eine zertifikatanforderung verfügen. Die Anmeldeinformationen des Benutzers in einem RST SOAP-Umschlag ist identisch mit GetPolicies und kann variieren, je nachdem, ob die Authentifizierungsrichtlinie lokalen oder Verbundpartner ist. Das BinarySecurityToken ein RST SOAP-Textkörper enthält eine Base64-codierte PKCS\#10 zertifikatanforderung, die vom Client basierend auf der Registrierungsrichtlinien generiert wird. Der Client konnte ein Registrierungsrichtlinien mithilfe MS-XCEP vor dem Anfordern eines Zertifikats mit MS-WSTEP angefordert haben. Wenn die PKCS\#10 zertifikatanforderung wird akzeptiert, von der Zertifizierungsstelle (CA) (Schlüssellänge, Hashalgorithmus und die Zertifikatvorlage übereinstimmen usw.) und der Client erfolgreich registrieren kann.

Beachten Sie, dass das RequestSecurityToken eine benutzerdefinierte "TokenType" verwendet werden soll (http:<span></span>/ / schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken), da unsere Registrierung Token mehr als ein x. 509 Version 3-Zertifikat ist. Weitere Informationen finden Sie im Abschnitt Antwort.

RST kann auch eine Anzahl von AdditionalContext Elemente wie DeviceType und Version angeben. Basierend auf diesen Werten, kann beispielsweise der Webdienst gerätespezifischen und versionsspezifischen DM Konfiguration zurück.

> **Hinweis**  Dienst für den Richtlinien und der Registrierungsdienst müssen auf dem gleichen Server sein. d. h., müssen sie den gleichen Hostnamen haben.

 

Das folgende Beispiel zeigt die Registrierung Web Service-Anforderung für Verbundauthentifizierung.

``` syntax
    <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
       xmlns:a="http://www.w3.org/2005/08/addressing"
       xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
       xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
       xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"
       xmlns:ac="http://schemas.xmlsoap.org/ws/2006/12/authorization">
      <s:Header>
        <a:Action s:mustUnderstand="1">
          http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RST/wstep
        </a:Action>
        <a:MessageID>urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:MessageID>
        <a:ReplyTo>
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
        </a:ReplyTo>
        <a:To s:mustUnderstand="1">
          https://enrolltest.contoso.com:443/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
        </a:To>
        <wsse:Security s:mustUnderstand="1">
          <wsse:BinarySecurityToken  wsse:ValueType= 
    "http:"//schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken
          wsse:EncodingType=
          http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
          
    >
          B64EncodedSampleBinarySecurityToken
          </wsse:BinarySecurityToken>
        </wsse:Security>
      </s:Header>
      <s:Body>
        <wst:RequestSecurityToken>
          <wst:TokenType>
            http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
          </wst:TokenType>
          <wst:RequestType>
            http://docs.oasis-open.org/ws-sx/ws-trust/200512/Issue
          </wst:RequestType>
          <wsse:BinarySecurityToken
             ValueType="http://schemas.microsoft.com/windows/pki/2009/01/enrollment#PKCS10"
             EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary">
            DER format PKCS#10 certificate request in Base64 encoding Insterted Here
          </wsse:BinarySecurityToken>
          <ac:AdditionalContext xmlns="http://schemas.xmlsoap.org/ws/2006/12/authorization">
               <ac:ContextItem Name="OSEdition">
                   <ac:Value> 4</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="OSVersion">
                   <ac:Value>10.0.9999.0</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceName">
                   <ac:Value>MY_WINDOWS_DEVICE</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="MAC">
                   <ac:Value>FF:FF:FF:FF:FF:FF</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="MAC">
                   <ac:Value>CC:CC:CC:CC:CC:CC</ac:Value>
                <ac:ContextItem Name="IMEI">
                   <ac:Value>49015420323756</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="IMEI">
                   <ac:Value>30215420323756</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="EnrollmentType">
                   <ac:Value>Full</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceType">
                   <ac:Value>CIMClient_Windows</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="ApplicationVersion">
                   <ac:Value>10.0.9999.0</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceID">
                   <ac:Value>7BA748C8-703E-4DF2-A74A-92984117346A</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="TargetedUserLoggedIn">
                   <ac:Value>True</ac:Value>
                </ac:ContextItem>
             </ac:AdditionalContext>
        </wst:RequestSecurityToken>
      </s:Body>
```

Nach der Überprüfung der Anforderung, der Webdienst sucht die zugewiesenen Zertifikatvorlage für den Client, aktualisieren sie bei Bedarf, sendet die PKCS\#10 an die Zertifizierungsstelle anfordert, verarbeitet die Antwort von der Zertifizierungsstelle, OMA Client Provisioning XML-Format erstellt und wird in die RequestSecurityTokenResponse (RST-ANTWORT) zurückgegeben.

> **Hinweis**  Die HTTP-Antwort vom Server muss nicht chunked werden; Es muss als eine Nachricht gesendet werden.

 

Ähnelt der "TokenType" in die RST und die RST-ANTWORT wird in verwenden, eine benutzerdefinierte Werttyp BinarySecurityToken (http:<span></span>/ / schemas.microsoft.com/ConfigurationManager/Enrollment/DeviceEnrollmentProvisionDoc), da das Token mehr als ein x. 509 Version 3-Zertifikat ist.

Die XML-Bereitstellungsdatei enthält:

-   Der angeforderten Zertifikate (erforderlich)
-   DM-Client-Konfiguration (erforderlich)

Der Client wird das Clientzertifikat, das Stammzertifikat für Unternehmen und intermediate Zertifizierungsstellen-Zertifikat installieren, sofern vorhanden. Die DM Konfiguration umfasst den Namen und die Adresse des Servers DM, welche Clientzertifikat zu verwenden und Zeitpläne, wenn der Client DM zurück an den Server aufruft.

Bereitstellung von XML Registrierung sollten maximal ein Stammzertifikat und eine anspruchsvollere Zertifizierungsstellen-Zertifikat, das benötigt werden, um das Clientzertifikat MDM zu verketten enthalten. Zusätzliche Stamm- und Zwischenzertifizierungsstellen konnte während einer Sitzung OMA DM bereitgestellt werden.

Beim Bereitstellen von Stamm- und Zwischenzertifizierungsstellen der unterstützte CSP Knotenpfad ist: CertificateStore/Root/System für Stammzertifikat provisioning CertificateStore/My/Benutzer für die Bereitstellung von anspruchsvolleren CA Zertifikat.

Es folgt eine Beispiel-RST-ANTWORT-Nachricht und ein Beispiel für die Bereitstellung von XML in RST-ANTWORT OMA-Client. Weitere Informationen über die Konfiguration-Dienstanbieter (CSP) in die Bereitstellung von XML verwendet finden Sie unter Enterprise-Einstellungen, Richtlinien und im Abschnitt app-Verwaltung.

Das folgende Beispiel zeigt die Registrierung Webdienstantwort an.

``` syntax
    <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" 
       xmlns:a="http://www.w3.org/2005/08/addressing" 
       xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
       <s:Header>
          <a:Action s:mustUnderstand="1" >
             http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RSTRC/wstep
          </a:Action>
          <a:RelatesTo>urn:uuid:81a5419a-496b-474f-a627-5cdd33eed8ab</a:RelatesTo>
          <o:Security s:mustUnderstand="1" xmlns:o=
             "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
             <u:Timestamp u:Id="_0">
                <u:Created>2012-08-02T00:32:59.420Z</u:Created>
                <u:Expires>2012-08-02T00:37:59.420Z</u:Expires>
             </u:Timestamp>
          </o:Security>
       </s:Header>
       <s:Body>
          <RequestSecurityTokenResponseCollection 
             xmlns="http://docs.oasis-open.org/ws-sx/ws-trust/200512">
             <RequestSecurityTokenResponse>
                <TokenType>
        http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
                </TokenType>
                 <DispositionMessage xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment"/>           <RequestedSecurityToken>
                   <BinarySecurityToken 
                      ValueType=
    "http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentProvisionDoc"
                      EncodingType=
       "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
                      xmlns=
              "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
                      B64EncodedSampleBinarySecurityToken
                   </BinarySecurityToken>
                </RequestedSecurityToken>
                <RequestID xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment">0
                </RequestID>
             </RequestSecurityTokenResponse>
          </RequestSecurityTokenResponseCollection>
       </s:Body>
    </s:Envelope>
```

Der folgende Code zeigt Beispiel-XML-Bereitstellungsdatei (im obigen Paket als ein Sicherheitstoken dargestellt):

```
<wap-provisioningdoc version="1.1">
   <characteristic type="CertificateStore">
      <characteristic type="Root">
         <characteristic type="System">
            <characteristic type="031336C933CC7E228B88880D78824FB2909A0A2F">
               <parm name="EncodedCertificate" value="B64 encoded cert insert here" />
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="CertificateStore">
      <characteristic type="My" >      
         <characteristic type="User">
            <characteristic type="F9A4F20FC50D990FDD0E3DB9AFCBF401818D5462">
               <parm name="EncodedCertificate" value="B64EncodedCertInsertedHere" />
            </characteristic>
            <characteristic type="PrivateKeyContainer"/> 
            <!-- This tag must be present for XML syntax correctness. -->            
         </characteristic>
         <characteristic type="WSTEP">
            <characteristic type="Renew">
             <!—If the datatype for ROBOSupport, RenewPeriod, and RetryInterval tags exist, they must be set explicitly. -->
               <parm name="ROBOSupport" value="true" datatype="boolean"/>
               <parm name="RenewPeriod" value="60" datatype="integer"/>
               <parm name="RetryInterval" value="4" datatype="integer"/>
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="APPLICATION">
      <parm name="APPID" value="w7"/>
      <parm name="PROVIDER-ID" value="TestMDMServer"/>
      <parm name="NAME" value="Microsoft"/>
      <parm name="ADDR" value="https://DM.contoso.com:443/omadm/Windows.ashx"/>
      <parm name="CONNRETRYFREQ" value="6" />
      <parm name="INITIALBACKOFFTIME" value="30000" />
      <parm name="MAXBACKOFFTIME" value="120000" />
      <parm name="BACKCOMPATRETRYDISABLED" />
      <parm name="DEFAULTENCODING" value="application/vnd.syncml.dm+wbxml" />
      <parm name="SSLCLIENTCERTSEARCHCRITERIA" value=
  "Subject=DC%3dcom%2cDC%3dmicrosoft%2cCN%3dUsers%2cCN%3dAdministrator&amp;amp;Stores=My%5CUser"/>
      <characteristic type="APPAUTH">
         <parm name="AAUTHLEVEL" value="CLIENT"/>
         <parm name="AAUTHTYPE" value="DIGEST"/>
         <parm name="AAUTHSECRET" value="password1"/>
         <parm name="AAUTHDATA" value="B64encodedBinaryNonceInsertedHere"/>
      </characteristic>
      <characteristic type="APPAUTH">
         <parm name="AAUTHLEVEL" value="APPSRV"/>
         <parm name="AAUTHTYPE" value="BASIC"/>
         <parm name="AAUTHNAME" value="testclient"/>
         <parm name="AAUTHSECRET" value="password2"/>
      </characteristic>
   </characteristic>
   <characteristic type="DMClient"> <!-- In Windows 10, an enrollment server should use DMClient CSP XML to configure DM polling schedules. -->
      <characteristic type="Provider">
<!-- ProviderID in DMClient CSP must match to PROVIDER-ID in w7 APPLICATION characteristics -->
    <characteristic type="TestMDMServer">
          <parm name="UPN" value="UserPrincipalName@contoso.com" datatype="string" /> 
             <characteristic type="Poll">
                <parm name="NumberOfFirstRetries" value="8" datatype="integer" />
                <parm name="IntervalForFirstSetOfRetries" value="15" datatype="integer" />
                <parm name="NumberOfSecondRetries" value="5" datatype="integer" />
                <parm name="IntervalForSecondSetOfRetries" value="3" datatype="integer" />
                <parm name="NumberOfRemainingScheduledRetries" value="0" datatype="integer" />
<!-- Windows 10 supports MDM push for real-time communication. The DM client long term polling schedule’s retry waiting interval should be more than 24 hours (1440) to reduce the impact to data consumption and battery life. Refer to the DMClient Configuration Service Provider section for information about polling schedule parameters.-->
         <parm name="IntervalForRemainingScheduledRetries" value="1560" datatype="integer" />
         <parm name="PollOnLogin" value="true" datatype="boolean" />
 </characteristic>
        <parm name="EntDeviceName" value="Administrator_Windows" datatype="string" />
</characteristic>
      </characteristic>
   </characteristic>
   <!-- For Windows 10, we removed EnterpriseAppManagement from the enrollment 
        protocol. -->
</wap-provisioningdoc>
```

**Notizen**

-   &lt;Parameternamen&gt; und &lt;charakteristische Type =&gt; Elemente in w7 APPLICATION CSP XML Groß-/Kleinschreibung und muss vollständig in Großbuchstaben.
-   In w7 ANWENDUNG Merkmal sollten sowohl CLIENT-als auch APPSRV Anmeldeinformationen in XML bereitgestellt werden.
-   Eine ausführliche Beschreibung der diese Einstellungen befinden sich in diesem Dokument im Abschnitt [Enterprise-Einstellungen, Richtlinien und app-Verwaltung](windows-mdm-enterprise-settings.md) .
-   Die **PrivateKeyContainer** -Eigenschaft ist erforderlich und muss in der Registrierung XML webbereitstellung, indem Sie die Registrierung vorhanden sein. Andere wichtigen Einstellungen werden den **ANBIETER-ID**, **NAME**und **ADRESSE** Parameter Elementen, die die eindeutige ID und den NAMEN Ihres Anbieters DM enthalten müssen, und die Adresse, in dem das Gerät für die Bereitstellung von Konfiguration verbinden kann. Die ID und NAME kann beliebigen Werten entsprechen, aber sie müssen eindeutig sein.
-   Wichtig ist auch SSLCLIENTCERTSEARCHCRITERIA, das verwendet wird, zum Auswählen des Zertifikats für die Clientauthentifizierung verwendet werden. Die Suche basiert auf dem Betreff-Attribut für das signierte Benutzerzertifikat ab.
-   CertificateStore/WSTEP ermöglicht Erneuerung von Zertifikaten. Falls der Server nicht unterstützt, legen Sie sie nicht.

 






