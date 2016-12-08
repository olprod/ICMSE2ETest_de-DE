---
author: Justinha
Description: "Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern"
ms.assetid: 36eba03c-ba15-4b34-b1cb-fd83cad08d63
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern"
ms.openlocfilehash: 5e425e9f82edbd9e998b6eedc840c6d73fb13904
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-network-drivers-initializing-and-adding-drivers"></a>Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern


Der Befehl Wpeutil initialisiert die Netzwerk-Treiber Windows PE (Windows PE) als Windows PE wird gestartet. Windows PE Standardbilds bietet Unterstützung für viele häufig verwendete Netzwerkadapter und unterstützt viele der gleichen Netzwerke, der Befehle wie Windows.Windows PE umfasst eine grundlegende Reihe von Netzwerk-Treiber für viele häufig verwendete Netzwerkadapter und unterstützt viele der gleichen Netzwerke Befehle wie in Windows.

Die unterstützten Methoden zum Herstellen einer Verbindung mit einem Dateiserver sind TCP/IP und NetBIOS über TCP/IP. Windows PE unterstützt keine andere Methoden, wie das Netzwerkprotokoll-Internetwork Packet Exchange/Sequenzierte Packet Exchange (IPX/SPX).

Windows PE unterstützt namensauflösung (Distributed File System, DFS) für eigenständige Namespaces hinzu. Domänen-Namespaces werden nicht unterstützt. Eigenständigen DFS-Namespaces ermöglichen ein DFS-Namespace, der nur auf dem lokalen Computer vorhanden ist und daher nicht Active Directory®-Domänendienste (AD DS) verwenden.

Herstellen einer Verbindung mit einem IPv4-Netzwerk von Windows PE in einem Netzwerk IPv6 wird nicht unterstützt.

**Verbindung mit einem anderen PC oder freigegebenen Ordner in einem Netzwerk**

1.  Klicken Sie in Windows PE oder eine werden kann (mit einem freigegebenen Ordner mit dem Befehl [net Use](http://technet.microsoft.com/library/bb490717.aspx) zuordnen). Wenn Sie an einer Domäne gehörenden PC verbinden, werden Windows PE für Benutzername und Kennwort aufgefordert.

    ``` syntax
    net use n: \\server\share
    ```

2.  Sie können Windows PE auch mithilfe der Systemanalyse vor dem Start Execution Environment (PXE), der Teil des [Windows-Bereitstellungsdienste](http://technet.microsoft.com/library/hh831764)ist von einem Netzwerk hosten.

**Beheben von Netzwerkproblemen**

1.  Versuchen Sie einen Treiber für Ihr Netzwerkgerät hinzuzufügen.

    Es wird empfohlen [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md), insbesondere für eine beliebige Treiber, der während des Installationsvorgangs ein Neustart erforderlich ist.

    Sie können möglicherweise auch die [Drvload Command-Line Options](drvload-command-line-options.md) verwenden, um einige Treiber nicht laden, wenn Windows PE ausgeführt wird. Jedoch Aktualisierungen an der Registrierung während der Installation werden nicht beibehalten nach einem Neustart, auch wenn Windows PE, in ausgeführt wird eine [Windows PE: Installieren Sie auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md).

2.  Führen Sie [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md) das Netzwerk nicht initialisieren. In der Standardeinstellung führt Wpeinit beim Start von Windows PE.

3.  In einigen Fällen müssen Sie die Einstellungen der Firewall auf dem PC konfigurieren, die Sie für die Verbindung versuchen. Windows PE unterstützt [IPSec-Konfiguration](http://go.microsoft.com/fwlink/p/?linkid=81713).

4.  Beachten Sie Sie nicht Windows PE einer Domäne beitreten oder Windows PE als Server ausführen. Weitere Informationen finden Sie unter [Windows PE für Windows 10](winpe-intro.md).

**Verbindung mit einem verkabelten Netzwerk mit 802.1 x-Authentifizierungsprotokolle**

1.  Erstellen eines benutzerdefinierten Windows PE-Bilds, das die optionale Komponente **Windows PE Dot3Svc** enthält.

2.  Starten Sie Windows PE einen PC.

3.  Starten Sie den Dienst dot3svc.

    ``` syntax
    net start dot3svc
    ```

4.  LAN-Profil hinzufügen. Beispiel:

    ``` syntax
    netsh lan add profile="G:\EthernetLANProfile.xml"
    ```

    Beispiel-LAN-Profil:

    ``` syntax
    <?xml version="1.0"?>
    <!-- Sample LAN profile: EthernetLANProfile.xml" -->
    <LANProfile xmlns="http://www.microsoft.com/networking/LAN/profile/v1">
      <MSM>
        <security>
          <OneXEnforced>false</OneXEnforced>
          <OneXEnabled>true</OneXEnabled>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>true</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig><EapHostConfig 
              xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config 
              xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap 
              xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
            <Type>25</Type><EapType 
              xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1">
            <ServerValidation>
              <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
              <ServerNames></ServerNames>
              <TrustedRootCA>1a 2b 3c 4d 56 78 90 aa bb cc dd ee ff 1a 2b 3c 4d 5e 6f</TrustedRootCA>
              </ServerValidation><FastReconnect>true</FastReconnect>
              <InnerEapOptional>false</InnerEapOptional><Eap 
                xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
              <Type>26</Type><EapType 
                xmlns="http://www.microsoft.com/provisioning/MsChapV2ConnectionPropertiesV1">
              <UseWinLogonCredentials>false</UseWinLogonCredentials></EapType></Eap>
              <EnableQuarantineChecks>false</EnableQuarantineChecks>
              <RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions>
              <PerformServerValidation 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false
              </PerformServerValidation><AcceptServerName 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false
                </AcceptServerName><PeapExtensionsV2 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">
              <AllowPromptingWhenServerCANotFound 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV3">true
              </AllowPromptingWhenServerCANotFound></PeapExtensionsV2></PeapExtensions></EapType>
            </Eap></Config></EapHostConfig></EAPConfig>
          </OneX>
        </security>
      </MSM>
    </LANProfile>
    ```

5.  Verknüpfen Sie die Benutzerdaten EAP mit dem Profil. Beispiel:

    ``` syntax
    netsh lan set eapuserdata filename="g:\EAP_UserData.xml" alluser=yes Interface="ethernet"
    ```

    EAP-Benutzerdaten-Beispieldatei:

    ``` syntax
    <?xml version="1.0"?>
    <!-- Sample EAP user data: EAP_UserData.xml" -->
    <EapHostUserCredentials 
      xmlns="http://www.microsoft.com/provisioning/EapHostUserCredentials" 
      xmlns:eapCommon="http://www.microsoft.com/provisioning/EapCommon" 
      xmlns:baseEap="http://www.microsoft.com/provisioning/BaseEapMethodUserCredentials">
      <EapMethod>
        <eapCommon:Type>25</eapCommon:Type>
        <eapCommon:AuthorId>0</eapCommon:AuthorId>
      </EapMethod>
      <Credentials
        xmlns:eapUser="http://www.microsoft.com/provisioning/EapUserPropertiesV1" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:baseEap="http://www.microsoft.com/provisioning/BaseEapUserPropertiesV1" 
        xmlns:MsPeap="http://www.microsoft.com/provisioning/MsPeapUserPropertiesV1" 
        xmlns:MsChapV2="http://www.microsoft.com/provisioning/MsChapV2UserPropertiesV1">
        <baseEap:Eap>
          <baseEap:Type>25</baseEap:Type>
          <MsPeap:EapType>
            <MsPeap:RoutingIdentity>onex\administrator</MsPeap:RoutingIdentity>
            <baseEap:Eap>
              <baseEap:Type>26</baseEap:Type>
              <MsChapV2:EapType>
                <MsChapV2:Username>actualuser</MsChapV2:Username>
                <MsChapV2:Password>actualpassword</MsChapV2:Password>
                <MsChapV2:LogonDomain>actualdomain</MsChapV2:LogonDomain>
              </MsChapV2:EapType>
            </baseEap:Eap>
          </MsPeap:EapType>
        </baseEap:Eap>
      </Credentials>
    </EapHostUserCredentials>
    ```

6.  Weitere Informationen finden Sie unter [Aktivieren nur Computer-Authentifizierung für eine 802.1 X-basierten Netzwerk in Windows Vista, Windows Server 2008 und Windows XP Service Pack 3](http://support.microsoft.com/kb/929847).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Wpeinit und Startnet.cmd: Verwenden von Skripts zum Starten des Windows PE](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)

[DrvLoad Befehlszeilenoptionen](drvload-command-line-options.md)

 

 






