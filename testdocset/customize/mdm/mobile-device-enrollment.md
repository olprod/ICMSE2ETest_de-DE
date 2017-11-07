---
title: "Mobiles Gerät Registrierung"
description: "Mobiles Gerät-Registrierung ist die erste Phase der Enterprise-Verwaltung."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 08C8B3DB-3263-414B-A368-F47B94F47A11
ms.openlocfilehash: e84903ed8e91ff6e04aa36e9896289937317f052
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-device-enrollment"></a>Registrierung des mobilen Geräts


Mobiles Gerät-Registrierung ist die erste Phase der Enterprise-Verwaltung. Das Gerät ist so konfiguriert, dass mit dem MDM Server mithilfe von Sicherheitsvorkehrungen während der Registrierungsprozess kommunizieren. Der Registrierungsdienst stellt sicher, dass nur authentifizierte und autorisierte Geräte von ihrem Unternehmen verwaltet werden können.

Der Registrierungsprozess umfasst die folgenden Schritte aus:

1.  Ermittlung des Endpunkts Registrierung

    Dieser Schritt enthält die Registrierung Konfigurationseinstellungen für den Endpunkt an.

2.  Zertifikatinstallation

    In diesem Schritt verarbeitet Benutzerauthentifizierung, Generierung des Zertifikats und Zertifikat installieren. Die installierten Zertifikate werden in der Zukunft zum Verwalten von gegenseitige Authentifizierung von Client-Server Secure Sockets Layer (SSL) verwendet werden.

3.  DM Clientbereitstellung

    Dieser Schritt wird den Gerät Management (DM) Client eine Verbindung mit einem Server Mobile Device Management (MDM) nach der Registrierung über DM SyncML über HTTPS (auch bekannt als Open Allianz Verwaltung mobiler Geräte (OMA DM) XML) konfiguriert.

## <a name="enrollment-protocol"></a>Registrierung Protokoll


Es gibt eine Reihe von Änderungen an der Registrierung Protokoll besser unterstützen eine Vielzahl von Szenarien für alle Plattformen. Ausführliche Informationen zu dem mobilen Gerät Registrierung Protokoll, finden Sie unter [ \[MS-MDM\]: Mobile Gerät Management Protocol](http://go.microsoft.com/fwlink/p/?LinkId=619346) und [ \[MS-MDE2\]: Mobile Device Registrierung Protocol Version 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347).

Die Registrierung umfasst die folgenden Schritte aus:

**Ermittlungsanfragen**  
   Die Discovery-Anforderung ist ein einfacher HTTP Post-Aufruf, der über HTTP XML zurückgibt. Der zurückgegebene XML-CODE enthält die URL für die Authentifizierung, die Management-URL und der Benutzer Anmeldeinformationstyp.

**Registrierungsrichtlinien Zertifikat**  
Konfiguration der Zertifikat-Registrierung ist eine Implementierung der das MS-XCEP-Protokoll, das in beschriebene \[MS-XCEP\]: x. 509-Zertifikat-Registrierung Richtlinie Protokollspezifikation. Abschnitt 4 der Spezifikation enthält ein Beispiel der Richtlinie Anforderung und Antwort. Das x. 509-Zertifikat-Registrierung Richtlinie-Protokoll ist ein minimaler messaging-Protokoll, das einen einzelnen Client-Besprechungsanfrage (GetPolicies) enthält mit einem übereinstimmenden Server Antwortnachricht (GetPoliciesResponse). Weitere Informationen finden Sie unter [ \[MS-XCEP\]: x. 509-Zertifikat Registrierung Richtlinie Protokoll](http://go.microsoft.com/fwlink/p/?LinkId=619345)

**Registrierung von Zertifikaten**  
Die Registrierung von Zertifikaten ist eine Implementierung des MS-WSTEP-Protokolls.

**Konfiguration der Verwaltung**  
Der Server sendet die Bereitstellung von XML, das ein Serverzertifikat (für die SSL-Serverauthentifizierung) enthält ein Clientzertifikat einstufen der Zertifizierungsstelle des Unternehmens, DM Client bootstrap Informationen (für den Client zur Kommunikation mit dem Verwaltungsserver), einem Enterprise-Anwendung Token (für den Benutzer zum Enterprise installieren) und den Link zum Herunterladen der Unternehmen Hub-Anwendung.

Die folgenden Themen beschreiben die End-to-End-Registrierungsprozess mit verschiedenen Authentifizierungsmethoden:

-   [Verbundauthentifizierung Gerät Registrierung](federated-authentication-device-enrollment.md)
-   [Registrierung von Zertifikaten Authentifizierung Gerät](certificate-authentication-device-enrollment.md)
-   [Authentifizierung Gerät Registrierung am Standort](on-premise-authentication-device-enrollment.md)

> **Hinweis**  Es empfiehlt sich verwenden Sie keine hartcodierten serverseitige Prüfungen auf Werten wie etwa:
> -   Zeichenfolge des Benutzer-agent
> -   Feste URIs, die während der Registrierung übergeben werden
> -   Bestimmte Formatierung eines Wertes, sofern nicht anders angegeben, wie das Format der Geräte-ID.

 

## <a name="prevent-mdm-enrollments"></a>Verhindern der Registrierung für die MDM


Starten in Windows 10, Version 1607 verwenden, um MDM wichtige für PCs Domäne zu verhindern können Sie folgende Gruppenrichtlinie festlegen:

Schlüssel: \\SOFTWARE\\Richtlinien\\Microsoft\\Windows\\CurrentVersion\\MDM

Wert: DisableRegistration

Mit dem GP-Editor, der Pfad ist Computerkonfiguration &gt; Administrative Vorlagen &gt; Windows-Komponenten &gt; MDM &gt; MDM-Registrierung zu deaktivieren.

## <a name="enrollment-scenarios-not-supported"></a>Registrierung Szenarien nicht unterstützt


MDM Registrierung für die zulassen folgenden Szenarien nicht:

-   Vordefinierte Administratorkonten auf Windows-Desktop können nicht in MDM registrieren.
-   Standard-Benutzer auf Windows-Desktop können nicht über die Arbeit Datenzugriffsseite in den **Einstellungen**in MDM registrieren. Um einen standard-Benutzer in MDM zu registrieren, es wird empfohlen, mithilfe einer provisioning-Pakets oder teilnehmen an das Gerät Azure AD aus **Einstellungen**  - &gt; **System**  - &gt; **zu**.
-   Windows 8.1-Geräte in MDM über registrieren-im Auftrag von (EOBO) registriert Windows 10 aktualisieren können, aber die Registrierung wird nicht unterstützt. Es wird empfohlen, Ausführen ein Servers initiiert Anmeldung kündigen, um diese Registrierung zurück, und klicken Sie dann nach Abschluss die Aktualisierung auf Windows 10 zu entfernen.

## <a name="enrollment-migration"></a>Migration der Registrierung


**Desktop:** Nach der MDM Client Aktualisierung von Windows 8.1 für Windows 10 gestartet wird an die erste Client initiierte Synchronisierung mit dem Dienst MDM Registrierung-Migration. Die Anfangszeit der Registrierung Migration hängt von der Konfiguration des MDM ab. Für Intune führt es beispielsweise alle 6 Stunden.

Erst nach Abschluss die Migration der Registrierung die Benutzeroberfläche keine Registrierung zeigt und das Serverpush funktioniert nicht.

Um die Migration der Registrierung manuell auslösen, können Sie MDMMaintenenceTask ausführen.

**Mobilen Geräten:** Nach der MDM Client Aktualisierung von Windows Phone 8.1 Windows 10 Mobile wird die Registrierung Migration beim ersten Start nach dem Upgrade ausgeführt.

## <a name="enrollment-error-messages"></a>Registrierung-Fehlermeldungen


Der Registrierung Server kann mithilfe des SOAP-Fehlers das Registrierung Nachrichten ablehnen. Fehler erstellt können wie folgt gesendet werden:

``` syntax
<s:envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">
    <s:header>
        <a:action s:mustunderstand="1">http://schemas.microsoft.com/windows/pki/2009/01/enrollment/rstrc/wstep</a:action>
        <activityid correlationid="2493ee37-beeb-4cb9-833c-cadde9067645" xmlns="http://schemas.microsoft.com/2004/09/servicemodel/diagnostics">2493ee37-beeb-4cb9-833c-cadde9067645</activityid>
        <a:relatesto>urn:uuid:urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:relatesto>
    </s:header>
    <s:body>
        <s:fault>
            <s:code>
                <s:value>s:receiver</s:value>
                <s:subcode>
                    <s:value>s:authorization</s:value>
                </s:subcode>
            </s:code>
            <s:reason>
                <s:text xml:lang="en-us">This User is not authorized to enroll</s:text>
            </s:reason>
        </s:fault>
    </s:body>
</s:envelope>
```

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Namespace</th>
<th>Subcode</th>
<th>Fehler</th>
<th>Beschreibung</th>
<th>HRESULT</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>MessageFormat</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_MESSAGE_FORMAT_ERROR</p></td>
<td style="vertical-align:top"><p>Nachrichtenformat ist ungültig</p></td>
<td style="vertical-align:top"><p>80180001</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>Authentifizierung</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_AUTHENTICATION_ERROR</p></td>
<td style="vertical-align:top"><p>Benutzer, die nicht erkannt</p></td>
<td style="vertical-align:top"><p>80180002</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>Autorisierung</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_AUTHORIZATION_ERROR</p></td>
<td style="vertical-align:top"><p>Benutzer nicht berechtigt, registrieren</p></td>
<td style="vertical-align:top"><p>80180003</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>CertificateRequest</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_CERTIFCATEREQUEST_ERROR</p></td>
<td style="vertical-align:top"><p>Fehler beim Abrufen des Zertifikats</p></td>
<td style="vertical-align:top"><p>80180004</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>EnrollmentServer</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_CONFIGMGRSERVER_ERROR</p></td>
<td style="vertical-align:top"></td>
<td style="vertical-align:top"><p>80180005</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>a:</p></td>
<td style="vertical-align:top"><p>InternalServiceFault</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_INTERNALSERVICE_ERROR</p></td>
<td style="vertical-align:top"><p>Der Server erreicht ein unerwarteter Problem</p></td>
<td style="vertical-align:top"><p>80180006</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>a:</p></td>
<td style="vertical-align:top"><p>InvalidSecurity</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_INVALIDSECURITY_ERROR</p></td>
<td style="vertical-align:top"><p>Die Kopfzeile Sicherheit kann nicht analysiert werden.</p></td>
<td style="vertical-align:top"><p>80180007</p></td>
</tr>
</tbody>
</table>

 

In Windows-10, Version 1507, haben wir das Deviceenrollmentserviceerror-Element hinzugefügt. Es folgt ein Beispiel:

``` syntax
<s:envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">
    <s:header>
        <a:action s:mustunderstand="1">http://schemas.microsoft.com/windows/pki/2009/01/enrollment/rstrc/wstep</a:action>
        <activityid correlationid="2493ee37-beeb-4cb9-833c-cadde9067645" xmlns="http://schemas.microsoft.com/2004/09/servicemodel/diagnostics">2493ee37-beeb-4cb9-833c-cadde9067645</activityid>
        <a:relatesto>urn:uuid:urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:relatesto>
    </s:header>
    <s:body>
        <s:fault>
            <s:code>
                <s:value>s:receiver</s:value>
                <s:subcode>
                    <s:value>s:authorization</s:value>
                </s:subcode>
            </s:code>
            <s:reason>
                <s:text xml:lang="en-us">device cap reached</s:text>
            </s:reason>
            <s:detail>
                <deviceenrollmentserviceerror xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment">
                    <errortype>devicecapreached</errortype>
                    <message>device cap reached</message>
                    <traceid>2493ee37-beeb-4cb9-833c-cadde9067645</traceid>
                </deviceenrollmentserviceerror>
            </s:detail>
        </s:fault>
    </s:body>
</s:envelope>
```

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Subcode</th>
<th>Fehler</th>
<th>Beschreibung</th>
<th>HRESULT</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>DeviceCapReached</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICECAPREACHED</p></td>
<td style="vertical-align:top"><p>Benutzer, die bereits für zu viele Geräte registriert. Anmeldung kündigen Sie alten Behebung des Fehlers oder zu löschen. Der Benutzer kann dies ohne Admin Hilfe zu beheben.</p></td>
<td style="vertical-align:top"><p>80180013</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DeviceNotSupported</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICENOTSUPPORTED</p></td>
<td style="vertical-align:top"><p>Spezifische Plattform (z. B. Windows) oder Version wird nicht unterstützt. Es ist keine Punkt wiederholen oder aufrufen Admin. Benutzer konnte Gerät zu aktualisieren.</p></td>
<td style="vertical-align:top"><p>80180014</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>NotSupported</p></td>
<td style="vertical-align:top"><p>MENROLL_E_NOTSUPPORTED</p></td>
<td style="vertical-align:top"><p>Verwaltung mobiler Geräte, die im Allgemeinen nicht unterstützt (spart einen Anruf Admin)</p></td>
<td style="vertical-align:top"><p>80180015</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>NotEligibleToRenew</p></td>
<td style="vertical-align:top"><p>MENROLL_E_NOTELIGIBLETORENEW</p></td>
<td style="vertical-align:top"><p>Gerät erneuern versucht, aber Server werden die Anforderung abgelehnt. Client möglicherweise Benachrichtigung für diesen angezeigt, wenn Robo fehlschlägt. Überprüfen Sie die Zeit auf Gerät. Der Benutzer kann es durch erneutes Registrieren behoben.</p></td>
<td style="vertical-align:top"><p>80180016</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>InMaintenance</p></td>
<td style="vertical-align:top"><p>MENROLL_E_INMAINTENANCE</p></td>
<td style="vertical-align:top"><p>Konto ist in der Wartung später wiederholen. Der Benutzer kann sich später erneut versuchen, aber sie müssen der Administrator wenden Sie sich an, da sie nicht erkennen können, wenn das Problem gelöst wurde.</p></td>
<td style="vertical-align:top"><p>80180017</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>UserLicense</p></td>
<td style="vertical-align:top"><p>MENROLL_E_USERLICENSE</p></td>
<td style="vertical-align:top"><p>Lizenz des Benutzers befindet sich in beschädigten Zustand und sperrende Korrelation der Registrierungs. Der Benutzer muss zum Aufrufen der Admin.</p></td>
<td style="vertical-align:top"><p>80180018</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>InvalidEnrollmentData</p></td>
<td style="vertical-align:top"><p>MENROLL_E_ENROLLMENTDATAINVALID</p></td>
<td style="vertical-align:top"><p>Der Server akzeptiert die Registrierung Daten. Der Server ist nicht ordnungsgemäß konfiguriert werden.</p></td>
<td style="vertical-align:top"><p>80180019</p></td>
</tr>
</tbody>
</table>

 

TraceID ist eine Freihandform Textknoten dem angemeldet ist. Sie sollten den Server Seite Status für diese Registrierung Versuch identifizieren. Diese Informationen möglicherweise unterstützen die um zu suchende, warum der Server für die Registrierung abgelehnt verwendet werden.

## <a name="related-topics"></a>Verwandte Themen


-   [Registrierung von Windows-basierten Geräten MDM](mdm-enrollment-of-windows-devices.md)
-   [Verbundauthentifizierung Gerät Registrierung](federated-authentication-device-enrollment.md)
-   [Registrierung von Zertifikaten Authentifizierung Gerät](certificate-authentication-device-enrollment.md)
-   [Authentifizierung Gerät Registrierung am Standort](on-premise-authentication-device-enrollment.md)






