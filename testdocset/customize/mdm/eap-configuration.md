---
title: EAP-Konfiguration
description: "Im Thema enthält eine schrittweise Anleitung zum Erstellen eines Extensible Authentication Protocol (EAP)-Konfigurations-XML für das VPN-Profil- und Zertifikatinformationen EAP-Filterung in Windows 10."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: DD3F2292-4B4C-4430-A57F-922FED2A8FAE
ms.openlocfilehash: 663be6318768bb371bf171c15282128ffbfa6fd3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eap-configuration"></a>EAP-Konfiguration


Das Thema enthält eine schrittweise Anleitung zum Erstellen eines Extensible Authentication Protocol (EAP)-Konfigurations-XML für das VPN-Profil- und Zertifikatinformationen EAP-Filterung in Windows 10.

## <a name="create-an-extensible-authentication-protocol-eap-configuration-xml-for-the-vpn-profile"></a>Erstellen eines Extensible Authentication Protocol (EAP) Konfigurations-XML für das VPN-Profil


Hier ist eine einfache Möglichkeit zum Abrufen der EAP-Konfigurations auf Ihrem Desktop mit dem Rasphone-Tool, das geliefert wird in das Feld ein.

1.  Führen Sie rasphone.exe aus.

    ![vpnv2 rasphone](images/vpnv2-csp-rasphone.png)

2.  Wenn Sie keinen derzeit VPN-Verbindungen und die folgende Meldung angezeigt wird, klicken Sie auf **OK**.

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-networkconnections.png)

3.  Wählen Sie im Assistenten **Arbeitsplatznetzwerk** aus.

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-setupnewconnection.png)

4.  Geben Sie auf der simulierte Informationen für den Internet-Adresse und Verbindung. Diese können gefälschten sein, da es nicht Authentifizierungsparameter auswirkt.

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-setupnewconnection2.png)

5.  Erstellen einer gefälschten VPN-Verbindungs. Klicken Sie in der Benutzeroberfläche der unten gezeigten auf **Eigenschaften**.

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-choosenetworkconnection.png)

6.  Klicken Sie im Dialogfeld **Eigenschaften** auf der Registerkarte **Sicherheit** .

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-testproperties.png)

7.  Wählen Sie auf der Registerkarte **Sicherheit** Optionsfeld **Verwenden Extensible Authentication Protocol (EAP)** .

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-testproperties2.png)

8.  Wählen Sie im Dropdownmenü die EAP-Methode, die Sie konfigurieren möchten. Klicken Sie dann auf **Eigenschaften** , die konfiguriert werden, je nach Bedarf.

    ![vpnv2 Eap-Konfiguration](images/vpnv2-csp-testproperties3.png)![vpnv2 Eap-Konfiguration](images/vpnv2-csp-testproperties4.png)

9.  Über PowerShell wechseln Sie und verwenden Sie die folgenden Cmdlets zum Abrufen der EAP-Konfiguration XML.

    ``` syntax
    Get-VpnConnection -Name Test
    ```

    <a href="" id="pow"></a>Es folgt eine Beispiel für die Ausgabe.

    ``` syntax
    Name                  : Test
    ServerAddress         : 1.1.1.1
    AllUserConnection     : False
    Guid                  : {EC87F6C9-8823-416C-B92B-517D592E250F}
    TunnelType            : Automatic
    AuthenticationMethod  : {Eap}
    EncryptionLevel       : Optional
    L2tpIPsecAuth         : Certificate
    UseWinlogonCredential : False
    EapConfigXmlStream    : #document
    ConnectionStatus      : Disconnected
    RememberCredential    : True
    SplitTunneling        : False
    DnsSuffix             :
    IdleDisconnectSeconds : 0
    ```

    ``` syntax
    $a = Get-VpnConnection -Name Test
    ```

    ``` syntax
    $a.EapConfigXmlStream.InnerXml
    ```

    Es folgt eine Beispiel für die Ausgabe

    ``` syntax
    <EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="http://www.microsoft.co
    m/provisioning/EapCommon">13</Type><VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorTy
    pe xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="http://www.microsoft.com/provisi
    oning/EapCommon">0</AuthorId></EapMethod><Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="h
    ttp://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="http://www.microsoft.co
    m/provisioning/EapTlsConnectionPropertiesV1"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSel
    ection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>false</DisableUserPr
    omptForServerValidation><ServerNames></ServerNames></ServerValidation><DifferentUsername>false</DifferentUsername><Perform
    ServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation>
    <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</AcceptServerName><TLSEx
    tensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.micro
    soft.com/provisioning/EapTlsConnectionPropertiesV3"><ClientAuthEKUList Enabled="true" /><AnyPurposeEKUList Enabled="true"
    /></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig>
    ```

    **Hinweis**  Sie sollten mit MDM Anbieter überprüfen, ob dieses XML-Format mit Escapezeichen übergeben werden müssen. Die XSDs für alle EAP-Methoden sind in das Feld geliefert und finden Sie unter den folgenden Speicherorten:
    -   C:\\Windows\\Schemas\\EAPHost
    -   C:\\Windows\\Schemas\\EAPMethods

     

## <a name="eap-certificate-filtering"></a>Filtern von EAP Zertifikat


In Ihrer Bereitstellung Wenn Sie mehrere Zertifikate auf dem Gerät bereitgestellt haben und das Wi-Fi-Profil bereitgestellt verfügt nicht über eine exakte Filterkriterien sehen Verbindungsfehler Sie Wi-Fi-Verbindung. Die Lösung besteht darin, sicherzustellen, dass das Wi-Fi-Profil bereitgestellt strict Filterkriterien verfügt, so, dass sie nur ein Zertifikat entspricht.

Unternehmen bereitstellen Zertifikat von der formularbasierten Authentifizierung EAP für VPN/Wi-Fi der Vorderseite nach einer Situation können, in denen es sind mehrere Zertifikate, die die Kriterien für die Authentifizierung zu erfüllen. Dies kann beispielsweise zu Problemen führen:

-   Der Benutzer möglicherweise aufgefordert, das Zertifikat auszuwählen.
-   Das falsche Zertifikat möglicherweise erhalten automatisch ausgewählt und ein Authentifizierungsfehlers verursachen.

Eine Bereitstellung in der Produktion bereit benötigen die geeigneten Zertifikatdetails als Teil des Profils bereitgestellt wird. Die folgende Informationen erläutert das Erstellen oder aktualisieren eine EAP-Konfigurations-XML, dass die zusätzlichen Zertifikate gefiltert werden, und das entsprechende Zertifikat für die Authentifizierung verwendet werden kann.

EAP XML muss mit der relevante Informationen für Ihre Umgebung dies manuell durch Bearbeiten des XML-Beispiels unten oder mithilfe der Benutzeroberfläche Leitfaden erfolgen kann aktualisiert werden. Nachdem die EAP XML aktualisiert wird, finden Sie in Anweisungen aus Ihrer MDM zum Bereitstellen von aktualisierten Konfigurations wie folgt:

-   Wi-Fi, suchen Sie nach der &lt;EAPConfig&gt; Abschnitt Ihrer aktuellen WLAN-Profil-XML-Daten (dieser Schritt ist, was Sie für den Knoten WLanXml im Wi-Fi CSP angeben). Innerhalb dieser Tags finden Sie die gesamte EAP-Konfiguration. Ersetzen Sie den Abschnitt unter &lt;EAPConfig&gt; Ihre aktualisierten XML- und Ihr Wi-Fi-Profil zu aktualisieren. Sie müssen möglicherweise auf Ihre MDM Anleitungen zum Bereitstellen eines neuen Wi-Fi-Profils zu verweisen.
-   Für VPN ist EAP-Konfiguration ein separates Feld in der MDM-Konfiguration. Arbeiten Sie mit Ihrem Anbieter MDM identifizieren und das entsprechende Feld aktualisieren.

Informationen zu EAP-Einstellungen finden Sie unter <https://technet.microsoft.com/library/hh945104.aspx#BKMK_Cfg_cert_Selct>

Informationen zum Generieren eines EAP XML finden Sie unter EAP-Konfiguration

Weitere Informationen zu erweiterten Enhanced Key Usage finden Sie unter <http://tools.ietf.org/html/rfc5280#section-4.2.1.12>

Informationen zum Hinzufügen von Erweiterte Schlüsselverwendung (EKU) an ein Zertifikat finden Sie unter <https://technet.microsoft.com/library/cc731792.aspx>

Die folgende Liste beschreibt die erforderlichen Komponenten für ein Zertifikat mit EAP verwendet werden:

-   Das Zertifikat muss mindestens eine der folgenden EKU (Erweiterte Schlüsselverwendung) Eigenschaften aufweisen:

    -   Clientauthentifizierung
    -   Gemäß RFC 5280, ist dies ein eindeutig definierter OID mit Wert 1.3.6.1.5.5.7.3.2
    -   Einen beliebigen Zweck
    -   Die EKU definiert und von Microsoft veröffentlicht, ist ein eindeutig definierter OID mit 1.3.6.1.4.1.311.10.12.1-Wert. Die Aufnahme der diese OID impliziert, dass das Zertifikat für einen beliebigen Zweck verwendet werden kann. Der Vorteil eines EKU gegenüber der alle Zweck EKU ist, dass zusätzliche nicht kritischen oder benutzerdefinierte EKU weiterhin das Zertifikat für eine effektive Filtern hinzugefügt werden können.
    -   Alle Zwecke
    -   Gemäß RFC 5280, wenn eine Zertifizierungsstelle erweiterte Schlüsselverwendung umfasst um einige Anwendung benötigt, möchte jedoch nicht zum Einschränken der Verwendung des Schlüssels zu erfüllen, kann die Zertifizierungsstelle einen erweiterten Key Usage-Wert von 0 hinzufügen. Ein Zertifikat mit solchen EKU kann für alle Zwecke verwendet werden.
-   Der Benutzer oder das Computerzertifikat auf dem Client Lieferketten zu einer vertrauenswürdigen Stammzertifizierungsstelle
-   Der Benutzer oder das Computerzertifikat fehlschlagen nicht eine der Prüfungen, die von den Zertifikatspeicher CryptoAPI ausgeführt werden, und das Zertifikat übergibt Anforderungen RAS-Richtlinie.
-   Der Benutzer oder das Computerzertifikat kein Fehler eine der Zertifikat-Objekt-ID Prüfungen, die in der (Internetauthentifizierungsdienst) angegeben sind auf / Radius-Server.
-   Die Erweiterung alternativen Antragstellernamen (SubjectAltName) im Zertifikat enthält den Benutzerprinzipalnamen (UPN) des Benutzers an.

Im folgende XML-Beispiel erläutert, die Eigenschaften für das EAP TLS XML, einschließlich Zertifikat zu filtern.

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

1.  Führen Sie die Schritte 1 bis 7 im Thema EAP-Konfiguration.
2.  Wählen Sie im Dialogfeld Eigenschaften von Microsoft VPN davon **Microsoft: Smartcard oder andere Zertifikat** aus der Dropdownliste (diese markiert EAP TLS)

    ![VPN selbst hosten Eigenschaftenfenster](images/certfiltering1.png)

    **Hinweis**  Wählen Sie für PEAP oder TTLS die entsprechende Methode aus, und folgen Sie diesem Verfahren fortgesetzt.

     

3.  Klicken Sie auf die Schaltfläche " **Eigenschaften** " unterhalb der Dropdown-Menü.
4.  Klicken Sie im Menü **Smartcard oder andere Zertifikateigenschaften** wählen Sie die Schaltfläche **Erweitert** .

    ![Smartcard oder andere Eigenschaftenfenster Zertifikat](images/certfiltering2.png)

5.  Klicken Sie im Menü **Konfigurieren Zertifikatauswahl** passen Sie die Filter nach Bedarf.

    ![Zertifikatsfenster konfigurieren](images/certfiltering3.png)

6.  Klicken Sie auf **OK** , um die Fenster zu im Dialogfeld für die wichtigsten rasphone.exe zurückzukehren zu schließen.
7.  Schließen Sie das Dialogfeld Rasphone.
8.  Führen Sie die folgenden das Verfahren im Thema EAP-Konfiguration aus Schritt 9, um ein EAP TLS Profil mit dem entsprechenden Filter zu erhalten.

> **Hinweis**  Sie können auch alle anderen zutreffend EAP Eigenschaften mithilfe dieser Benutzeroberfläche sowie festlegen. Leitfaden für die Bedeutung dieser Eigenschaften kann im Thema [Extensible Authentication Protocol (EAP) Einstellungen für den Netzwerkzugriff](https://technet.microsoft.com/library/hh945104.aspx) gefunden werden.

 

 

 






