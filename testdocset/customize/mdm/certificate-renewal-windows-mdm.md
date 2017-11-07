---
title: Erneuerung von Zertifikaten
description: "Das registrierten Clientzertifikat läuft ab nach einem bestimmten Zeitraum verwenden."
MS-HAID:
- p\_phdevicemgmt.certificate\_renewal
- p\_phDeviceMgmt.certificate\_renewal\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F910C50C-FF67-40B0-AAB0-CA7CE02A9619
ms.openlocfilehash: b75c9706cd9185df3105bd8e6424e6ebac73801e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="certificate-renewal"></a>Erneuerung von Zertifikaten


Das registrierten Clientzertifikat läuft ab nach einem bestimmten Zeitraum verwenden. Das Ablaufdatum des Zertifikats wird vom Server angegeben. Zur Sicherstellung der kontinuierlichen Zugriffs auf enterpriseanwendungen unterstützt Windows einen Benutzer ausgelöste Zertifikat Erneuerung-Prozess. Der Benutzer wird aufgefordert, das aktuelle Kennwort für das Konto im Unternehmen angeben, und der Registrierung Client Ruft ein neue Client-Zertifikat vom Server Registrierung und löscht das alte Zertifikat. Der Client ein neues privaten/öffentlichen Schlüsselpaar generiert, generiert eine PKCS\#7 Anforderung und auf Anzeichen für die PKCS\#7-Anforderung mit dem vorhandenen Zertifikat. In Windows wird die automatische MDM Client Zertifikat Erneuerung ebenfalls unterstützt.

> **Hinweis**  Stellen Sie sicher, dass die EntDMID in der Dienstanbieter für DMClient Konfiguration festgelegt ist, bevor die Erneuerung zertifikatanforderung ausgelöst wird.

 

## <a name="in-this-topic"></a>In diesem Thema


-   [Automatische Erneuerung zertifikatanforderung](#automatic-certificate-renewal-request)
-   [Konfigurieren von Zertifikaten Erneuerung Zeitplan](#certificate-renewal-schedule-configuration)
-   [Zertifikat Erneuerung Antwort](#certificate-renewal-response)
-   [Unterstützt bei der Registrierung und Zertifikat Erneuerung von MDM Konfiguration-Dienstanbieter](#configuration-service-providers-supported-during-mdm-enrollment-and-certificate-renewal)

<a href="" id="automatic-certificate-renewal"></a>
## <a name="automatic-certificate-renewal-request"></a>Automatische Erneuerung zertifikatanforderung


Zusätzlich zur manuellen Zertifikat-Erneuerung unterstützt Windows automatische zertifikatsanforderung Verlängerung, auch bekannt als erneuern im Auftrag von (ROBO), die keine Eingriffe des Benutzers erforderlich ist. Für die automatische Verlängerung verwendet der Registrierung-Client das vorhandene MDM Clientzertifikat Client Transport Layer Security (TLS) ausführen. Das Sicherheitstoken für den Benutzer ist im SOAP-Header nicht erforderlich. Daher ist der Registrierung MDM Zertifikatserver zur Unterstützung von Clients TLS für die basierender Client Zertifikatauthentifizierung für automatische Zertifikat Erneuerung erforderlich.

> **Hinweis**  Erneuerung des Zertifikats Registrierung über ROBO Zertifikat wird nur mit PKI von Microsoft unterstützt.

 

Automatische Zertifikat Verlängerung ist die einzige MDM Client Zertifikat Erneuerung-Methode für das Gerät unterstützt, die mithilfe der WAB-Authentifizierung (d. h., die die AuthPolicy auf Federated festgelegt ist) registriert ist. Dies bedeutet auch, ob der Server WAB Authentifizierung unterstützt, der Registrierung MDM Zertifikatserver auch Client TLS unterstützen MUSS, um das Clientzertifikat MDM erneuern.

Für das Gerät an, das mit der lokale Verwaltungs-Authentifizierungsmethode für die Abwärtskompatibilität registriert ist ist die Standardmethode für die Erneuerung Benutzer manuell Zertifikat Erneuerung. Jedoch konnte für Windows-Geräte während der Phase der MDM Client Zertifikat Registrierung oder bei MDM Management Abschnitt, den Registrierungs-Server oder MDM Server das Gerät zur Unterstützung der automatischen MDM Client Zertifikat Erneuerung über CertificateStore CSPs ROBOSupport Knoten unter CertificateStore/Meine/WSTEP/erneuern-URL konfiguriert werden. Weitere Informationen zum Erneuern verwandte Konfigurationseinstellungen, finden Sie in der CertificateStore Konfiguration-Dienstanbieter.

Im Gegensatz zum manuellen Zertifikat Erneuerung ist eine zusätzliche b64 Codierung für PKCS\#7 Nachricht mit automatische Erneuerung der PKCS\#7 Nachrichteninhalt b64 separat kodiert nicht zur Verfügung.

Während der automatischen Erneuerung Wenn das Stammzertifikat vom Gerät, vertrauenswürdig ist nicht fehl die Authentifizierung. Vergewissern Sie sich mit einer der Gerät vorinstalliert Stammzertifikate oder Erbringung der Stammzertifikats über eine Sitzung DM über CertificateStore Konfiguration-Dienstanbieter.

Während das automatische Zertifikat zu erneuern Prozess, das Gerät wird verweigert-HTTP-Anforderung vom Server umleiten, es sei denn, es ist die gleiche umleitungs-URL, die der Benutzer explizit während der anfänglichen MDM Registrierungsprozess akzeptiert.

Das folgende Beispiel zeigt die Details einer automatischen Erneuerung-Anforderung.

```
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing" xmlns:u=
   "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
   <s:Header>
      <a:Action s:mustUnderstand="1">
         http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RST/wstep</a:Action>
      <a:MessageID>urn:uuid:61a17f2c-42e9-4a45-9c85-f15c1c8baee8</a:MessageID>
      <a:ReplyTo>
         <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
      </a:ReplyTo>
      <a:To s:mustUnderstand="1">
         https://dm.contoso.com/EnrollmentService/DeviceEnrollmentService.svc</a:To>
      <o:Security s:mustUnderstand="1" xmlns:o=
         "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <u:Timestamp u:Id="_0">
            <u:Created>2011-07-11T19:49:08.579Z</u:Created>
            <u:Expires>2011-07-11T19:54:08.579Z</u:Expires>
         </u:Timestamp>
         <o:UsernameToken u:Id="uuid-2a734df6-b227-4e60-82a8-ed53c574b718-5">
            <o:Username>user@contoso.com</o:Username>
            <o:Password o:Type=
               "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText">                
            </o:Password>
         </o:UsernameToken>
      </o:Security>
   </s:Header>
   <s:Body>
      <RequestSecurityToken xmlns="http://docs.oasis-open.org/ws-sx/ws-trust/200512">
         <TokenType>
    http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
         </TokenType>
         <RequestType>http://docs.oasis-open.org/ws-sx/ws-trust/200512/Renew</RequestType>
         <BinarySecurityToken 
            ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#PKCS7" 
            EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary" 
            xmlns="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
            BinarySecurityTokenInsertedHere
         </BinarySecurityToken>
         <AdditionalContext xmlns="http://schemas.xmlsoap.org/ws/2006/12/authorization">
            <ContextItem Name="DeviceType">
               <Value>WindowsPhone</Value>
            </ContextItem>
            <ContextItem Name="ApplicationVersion">
               <Value>5.0.7616.0</Value>
            </ContextItem>
         </AdditionalContext>
      </RequestSecurityToken>
   </s:Body>
</s:Envelope>
```


<a href="" id="certificate-renewal-schedule"></a>
## <a name="certificate-renewal-schedule-configuration"></a>Konfigurieren von Zertifikaten Erneuerung Zeitplan

In Windows kann die Erneuerung Periode nur während der Phase der Registrierung MDM festgelegt werden. Windows unterstützt ein Zertifikat Erneuerung Punkt und Erneuerung Ausfall wiederholen, um vom sowohl MDM Registrierung Server konfiguriert und höher vom Verwaltungsserver MDM mithilfe des CertificateStore CSP werden RenewPeriod und RenewInterval Knoten. Das Gerät konnte automatischen Erneuerung mehrmals wiederholen, bis das Zertifikat abläuft. Für die manuelle Zertifikats Erneuerung anstelle einer Erinnerung nur einmal des Benutzers, erinnert das Gerät Windows den Benutzer mit einem Dialogfeld zu jeder Erneuerung wiederholen, bis das Zertifikat ist abgelaufen.

Weitere Informationen zu den Parametern finden Sie unter der CertificateStore Konfiguration-Dienstanbieter.

Im Gegensatz zum manuellen Zertifikat Erneuerung führt das Gerät keine automatische MDM Client Zertifikat Verlängerung, wenn das Zertifikat bereits abgelaufen ist. Um sicherzustellen, dass das Gerät über genügend Zeit zum Ausführen einer automatischen Verlängerung, es wird empfohlen, dass Sie einen Erneuerungszeitraum festlegen, Wiederholungsintervall einige Monate (40 bis 60 Tage), bevor das Zertifikat abläuft, und legen Sie die Erneuerung, um alle paar Tage wie alle 4 und 5 Tage alle 7 Tage (wöchentlich) werden, um erhöhen die Wahrscheinlichkeit, dass das Gerät wird eine Konnektivität an verschiedenen Tage die Woche.

> **Hinweis**  Erneuerung wird für das Zertifikat für die Registrierung ausgelöst werden, für PCs, die in MDM in Windows 8.1 zuvor registriert und klicken Sie dann auf Windows 10 aktualisiert wurden. Danach wird in der konfigurierten ROBO Intervall Erneuerung vorkommen.
> Erneuerung für Windows Phone 8.1 Geräte auf Windows 10 Mobile aktualisiert wurden an den konfigurierten internen ROBO geschieht. Dies entspricht der Erwartung und Verhalten ist erwünscht.

 

## <a name="certificate-renewal-response"></a>Zertifikat Erneuerung Antwort

Wenn RequestType erneuern festgelegt ist, wird der Webdienst (zusätzlich zu den ersten in der Registrierung im) Folgendes überprüft:

-   Die Signatur des der PKCS\#7 BinarySecurityToken korrekt ist.
-   Das Zertifikat des Clients befindet sich in der Erneuerungszeitraum
-   Das Zertifikat wurde von der Registrierungsdienst ausgestellt.
-   Die anfordernde Person ist dieselbe wie die anfordernde Person für die anfängliche Registrierung
-   Für standard Clientanforderung noch nicht der Client blockiert wurden

Nach Abschluss der Überprüfung ruft der Webdienst der PKCS\#Inhalte aus der PKCS 10\#7 BinarySecurityToken. Der Rest ist identisch mit der anfänglichen Registrierung abgesehen davon, dass die XML-Bereitstellung nur auf das neue Zertifikat von der Zertifizierungsstelle ausgestellt wurden muss.

> **Hinweis**  Die HTTP-Antwort vom Server muss nicht chunked werden; Es muss als eine Nachricht gesendet werden.


Das folgende Beispiel zeigt die Details einer Zertifikat Erneuerung Antwort.

```
<wap-provisioningdoc version="1.1">
   <characteristic type="CertificateStore">
<!-- Root certificate provision is only needed here if it is not in the device already -->      <characteristic type="Root">
         <characteristic type="System">
            <characteristic type="EncodedRootCertHashInsertedHere ">
               <parm name="EncodedCertificate" value="EncodedCertInsertedHere" />
            </characteristic>
         </characteristic>
      </characteristic>
      <characteristic type="My" >
         <characteristic type="User">
            <characteristic type="EncodedClientCertHashInsertedHere">
               <parm name="EncodedCertificate" value="EncodedCertInsertedHere" />
               <characteristic type="PrivateKeyContainer"/>
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="APPLICATION">
      <parm name="PROVIDER-ID" value="TestMDMServer"/>
   </characteristic>
</wap-provisioningdoc>
```

> **Hinweis**  Der Client empfängt ein neues Zertifikat, anstatt das anfängliche Zertifikat zu erneuern. Der Administrator steuert, welche Zertifikatvorlage der Client verwendet werden soll. Die Vorlagen können zu jedem als die anfängliche Registrierung Zeit zum Zeitpunkt der Erneuerung anders lauten.

 

<a href="" id="csp-support-during-enrollment-and-renewal"></a>
## <a name="configuration-service-providers-supported-during-mdm-enrollment-and-certificate-renewal"></a>Unterstützt bei der Registrierung und Zertifikat Erneuerung von MDM Konfiguration-Dienstanbieter


Die folgende Konfiguration-Dienstanbieter werden während der Registrierung MDM und Erneuerung Zertifikat unterstützt. Finden Sie unter Konfiguration Anbieter Dienstverweis für jede Konfigurationsdienstanbieter ausführlich beschrieben.

-   CertificateStore
-   ANWENDUNG W7
-   DMClient
-   EnterpriseAppManagement

 






