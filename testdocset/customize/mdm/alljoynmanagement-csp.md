---
title: AllJoynManagement CSP
description: "Im AllJoynManagement Konfiguration-Dienstanbieter (CSP) kann IT-Administrator die Geräte AllJoyn auflisten, die mit der AllJoyn verbunden sind."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 468E0EE5-EED3-48FF-91C0-89F9D159AA8C
ms.openlocfilehash: b02080872c467a1b5fcf98e0672c6f1957a19264
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="alljoynmanagement-csp"></a>AllJoynManagement CSP


Der AllJoynManagement Konfiguration-Dienstanbieter (CSP) kann IT-Administratoren zum Aufzählen der AllJoyn Geräte, die mit dem AllJoyn Bus verbunden sind. Die Geräten müssen die Microsoft AllJoyn Configuration-Schnittstelle (com.microsoft.alljoynmanagement.config) unterstützen. Sie können auch auf die gleichen Geräte Konfigurationsdateien drücken. Füllen Sie die verschiedenen Knoten beim Festlegen der neuen Konfigurations wird empfohlen, dass Sie eine Abfrage zuerst tun, um der tatsächlichen Werte für alle Knoten in allen angeschlossene Geräte erhalten. Die Informationen aus der Abfrage können dann den Knotenwerte festgelegt, wenn die neue Konfiguration pushen.

> **Hinweis**  
Der AllJoynManagement Konfigurationsdienstanbieter (CSP) ist nur in Windows 10 IoT Core (IoT Core) unterstützt.

Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt.

 

Beachten Sie für die Firewalleinstellungen, dass PublicProfile und PrivateProfile schließen sich gegenseitig aus. Die Private Profil muss festgelegt werden, auf die direkt auf dem Gerät selbst und der einzige unterstützte Vorgang ist Get. Für PublicProfile hinzufügen und Get unterstützt. Diese CSP in Verbindung mit der Brücke AllJoyn Gerät System verwendet werden soll, und ein Überblick über die Brücke hilft beim wann und wie Sie mit diesen Kryptografiedienstanbieter bestimmen. Weitere Informationen finden Sie unter [Project SBG (Gerät System Bridge, Angenommene)](http://go.microsoft.com/fwlink/p/?LinkId=615876) und [AllJoyn Gerät System Bridge](http://go.microsoft.com/fwlink/p/?LinkId=615877).

Die folgende Abbildung zeigt den AllJoynManagement Konfigurationsdienstanbieter im Strukturformat

![Alljoynmanagement Csp Diagramm](images/provisioning-csp-alljoynmanagement.png)

Die folgende Liste beschreibt die Merkmale und Parameter.

<a href="" id="--vendor-msft-alljoynmanagement"></a>**./Vendor/MSFT/AllJoynManagement**  
Der Stammknoten für den Dienstanbieter für AllJoynManagement-Konfiguration.

<a href="" id="services"></a>**Dienste**  
Liste aller AllJoyn-Objekte, die auf dem Bus AllJoyn ermittelt werden. Dazu gehören alle AllJoyn-Objekte, die die "com.microsoft.alljoynmanagement.config" verfügbar machen.

<a href="" id="services-node-name"></a>**Services / ***_Knotenname_**  
Die eindeutige AllJoyn Geräte-ID (GUID), die mindestens eine konfigurierbare Objekte gehostet wird.

<a href="" id="services-node-name-port"></a>* *Services /*Knotenname*/Port**  
Der Satz von Ports, die das AllJoyn-Objekt verwendet, um Konfigurationseinstellungen zu kommunizieren. In der Regel nur einen Port für die Kommunikation verwendet wird, aber es ist möglich, geben Sie zusätzliche Ports.

<a href="" id="services-node-name-port-node-name"></a>* *Services /*Knotenname*/Port / ***_Knotenname_**  
Portnummer für die Kommunikation verwendet. Dies ist durch das konfigurierbare AllJoyn Objekt angegeben und hier übernommen.

<a href="" id="services-node-name-port-node-name-cfgobject"></a>**Services /* Knotenname*/Port/ /CfgObject***Knotenname*  
Der Satz von konfigurierbar Schnittstellen, die für den Port des AllJoyn-Objekts verfügbar sind.

<a href="" id="services-node-name-port-node-name-cfgobject-node-name"></a>**Services /* Knotenname*/Port/**Knotenname/CfgObject / ***_Knotenname_**  
Der Rest dieses URI ist ein Escapezeichen Pfad auf das konfigurierbare AllJoyn-Objekt, das von der übergeordneten ServiceID gehostet und vom übergeordneten Element PortNum zugegriffen werden.

Beispielsweise eine AllJoyn Brücke mit Microsoft AllJoyn Konfigurationsschnittstelle "\\FabrikamService\\BridgeConfig" würde den URI als angegeben werden: % 2FFabrikamService % 2FBridgeConfig.

<a href="" id="credentials"></a>**Anmeldeinformationen**  
Dies ist die Speicherung von Anmeldeinformationen. Ein Administrator kann Anmeldeinformationen für jedes Gerät AllJoyn festlegen, die an diesem Knoten Authentifizierung erfordert.

Wenn eine Anforderung SyncML im CSP ersetzen oder Abfragen ein Konfigurationselement für ein AllJoyn-Objekt, die Authentifizierung erfordert eingeht, verwendet der CSP die hier während der Authentifizierungsphase gespeicherten Anmeldeinformationen.

<a href="" id="credentials-node-name"></a>**Anmeldeinformationen / ***_Knotenname_**  
Dies ist der gleiche Dienst-ID angegeben wird, in \\AllJoynManagement\\Services\\ServiceID-URI. Es ist in der Regel als GUID implementiert.

<a href="" id="credentials-node-name-key"></a>* *Anmeldeinformationen /*Knotenname*/Key**  
Eine alphanumerische Schlüsselwert, die die Authentifizierung AllJoyn SRP KEYX standard entspricht.

<a href="" id="firewall"></a>**Firewall**  
Firewall-Einstellung für den Dienst AllJoyn.

<a href="" id="firewall-publicprofile"></a>**Firewall/PublicProfile**  
Boolescher Wert zum Aktivieren oder Deaktivieren des AllJoyn Router-Diensts (AJRouter.dll) für öffentliches Netzwerk-Profil.

<a href="" id="firewall-privateprofile"></a>**Firewall/PrivateProfile**  
Boolescher Wert, der angibt, ob für privaten Netzwerkprofil AllJoyn-Router-Dienst (AJRouter.dll) aktiviert ist.

## <a name="examples"></a>Beispiele


Set-Adapterkonfiguration

``` syntax
<?xml version="1.0" encoding="utf-8"?>
SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/AllJoynManagement/Services/_ALLJOYN_DEVICE_ID_/Port/27/Configuration/%2FDSBService%2FAdapterConfig</LocURI>
        </Target>
       <Meta>
          <Format xmlns="syncml:metinf">b64</Format>
        </Meta>       <Data>PAA/AHgAbQBsACAAdgBlAHIAcwBpAG8AbgA9ACIAMQAuADAAIgA/AD4ADQAKADwAQgBhAGMATgBlAHQAQwBmAGcAPgANAAoACQA8AEIAQgBNAEQAUwBlAHIAdgBlAHIAPgANAAoACQAJADwASQBQAEEAZABkAHIAZQBzAHMAPgAxADIANwAuADAALgAwAC4AMQA8AC8ASQBQAEEAZABkAHIAZQBzAHMAPgANAAoACQAJADwAUABvAHIAdAA+ADQANwA4ADAAOAA8AC8AUABvAHIAdAA+AA0ACgAJADwALwBCAEIATQBEAFMAZQByAHYAZQByAD4ADQAKADwALwBCAGEAYwBOAGUAdABDAGYAZwA+AA0ACgAAAA==</Data>
       </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

Ersetzen Sie \_ALLJOYN\_GERÄT\_ID\_ mit einer ID tatsächlichen Gerät Beachten Sie, dass die Daten Base64-codierte Darstellung der Konfigurationsdatei, die Sie festlegen.

Abrufen von PIN-Daten

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/AllJoynManagement/Credentials?list=StructData</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

Abrufen der Firewalls PrivateProfile

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>         
              <Get>
                <CmdID>1</CmdID>
                <Item>
                     <Target>
                       <LocURI>./Vendor/MSFT/AllJoynManagement/Firewall/PrivateProfile</LocURI>
                     </Target>
                </Item>
              </Get>        
     <Final/>
  </SyncBody>
</SyncML>
```

 

 






