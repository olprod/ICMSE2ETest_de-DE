---
title: NodeCache CSP
description: NodeCache CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b4dd2b0d-79ef-42ac-ab5b-ee07b3097876
ms.openlocfilehash: ff58a0f3bee5c0a52f95bcc586d8abc48e45ea6c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="nodecache-csp"></a>NodeCache CSP


Der Dienstanbieter für NodeCache Konfiguration wird zum Verwalten des Clientcaches verwendet. Dieses Dienstanbieters Konfiguration ist nur von Enterprise-Verwaltungsservern verwendet werden. Es bietet eine Abstraktion, die die Verwaltung der Liste der Knoten aus einem bestimmten Sicherungsspeicher trennt. Es synchronisiert Clientcache mit dem Server clientseitigen Cache. Es bietet auch eine API für die Überwachung von cacheänderungen Gerät clientseitigen.

Das folgende Diagramm zeigt den NodeCache Konfiguration-Dienstanbieter in der Strukturformat.

![Nodecache csp](images/provisioning-csp-nodecache.png)

<a href="" id="--device-vendor-msft"></a>**./Device/Vendor/MSFT**  
Erforderlich. Den Stammknoten des NodeCache-Objekts. Unterstützte Vorgang ist Get. Dieses Dienstanbieters Konfiguration wird für Gerätemanagement nur Enterprise verwendet. Dies ist eine vordefinierte MIME-Typ zum Identifizieren dieses verwalteten-Objekts in der OMA DM-Syntax. Starten Windows 10, Version 1607 des Werts ist com.microsoft/1.0/MDM/NodeCache.

<a href="" id="providerid"></a>***ProviderID***  
Optional Gruppeneinstellungen Sie pro DM-Servers. Jede Gruppe von Einstellungen wird durch des Servers-Anbieter-ID unterschieden. Es sollte dem gleichen DM Server **PROVIDER-ID-** Wert sein, die über den [w7 ANWENDUNG Konfigurationsdienstanbieter](w7-application-csp.md) XML während der Registrierung angegeben wurde. Nur ein Enterprise-Verwaltungsserver wird unterstützt. D. h., sollte nur ein *ProviderID* Knoten unter **NodeCache**vorhanden sein. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

<a href="" id="providerid-cacheversion"></a>***ProviderID*/CacheVersion**  
Optional Zeichenfolge, die durch den Server Cache Version darstellt. Bereich ist dynamisch.

Datentyp ist Zeichenfolge. Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-changednodes"></a>***ProviderID*/ChangedNodes**  
Optional Liste der Knoten, dessen Werte nicht ihre erwartete Werte gemäß überein stimmen * */*NodeID*/ExpectedValue**. Bereich ist dynamisch.

Datentyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="providerid-nodes"></a>***ProviderID*/Nodes**  
Erforderlich. Stammknoten für zwischengespeicherte Knoten. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-nodes-nodeid"></a>**/ Knoten / ***_NodeID_**  
Optional Informationen zu den einzelnen zwischengespeicherten Knoten wird unter *NodeID* gemäß dem Server gespeichert. Dieser Wert darf keine Kommas enthalten. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

<a href="" id="-nodeid-nodeuri"></a>* */*NodeID*/NodeURI**  
Erforderlich. Dieser Knoten Wert ist eine vollständige OMA DM Knoten-URI. Es kann entweder eine innere oder einen Endknoten Knoten in der Struktur des Geräts Management angeben. Bereich ist dynamisch.

Datentyp ist Zeichenfolge an. Unterstützte Vorgänge sind Get, hinzufügen und löschen.

<a href="" id="-nodeid-expectedvalue"></a>* */*NodeID*/ExpectedValue**  
Erforderlich. Dies ist der Wert, den der Server auf dem Gerät werden erwartet. Bei der Dienstanbieter für die Konfiguration eine Sitzung initiiert hat, überprüft der erwartete Wert gegen den tatsächlichen Wert des Knotens. Bereich ist dynamisch. Unterstützte Werte sind Zeichenfolgen und X-Nodemon-nicht vorhanden.

Unterstützte Vorgänge sind Get, hinzufügen und löschen.

Es folgt ein Beispiel für das Festlegen der ExpectedValue zu nicht vorhandenem ein.

``` syntax
<Add>
   <CmdID>10</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0002/ExpectedValue</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
         <Type xmlns="syncml:metinf">application/x-nodemon-nonexistent</Type>
      </Meta>
   </Item>
</Add>
```

## <a name="a-typical-dm-session-with-the-nodecache-configuration-service-provider"></a>Eine typische DM-Sitzung mit dem NodeCache Konfiguration-Dienstanbieter


1.  Herstellen einer Verbindung mit einem DM-Server.

2.  Der Server fragt die Version **NodeCache** durch Ausstellen einer Get-Operation für ./Vendor/MSFT/NodeCache/*ProviderID*CacheVersion LocURI

3.  Wenn sich das Gerät **CacheVersion** und die serverseitige Cache (aufgrund eines Geräts Absturz oder Serverausfalls) unterscheiden, der Server kann den serverseitigen Cache löschen und gehen Sie zu Schritt 5.

4.  Der Server aktualisiert den Cache serverseitige:

    1.  Sendet eine Get-Operation für ./Vendor/MSFT/NodeCache/*ProviderID*ChangedNodes LocURI

    2.  Antwort ist eine Liste der geänderten Knoten-IDs. Jede-ID in der Liste entspricht einem Knoten unter ./Vendor/MSFT/NodeCache/*ProviderID*/Nodes Stamm

    3.  Für jeden Knoten in der Liste Ungültiger Knoten, sendet der Server eine `GET` Befehl aus, um den tatsächlichen Wert des Knotens abzurufen. Beispielsweise `GET <NodeURI>`, wobei `NodeURI` ist ein vollständiger Gerät LocURI, die den Cache ungültig Knoten entspricht.

    4.  Knoten im Cache serverseitige werden mit der tatsächlichen Werte vom Gerät empfangen aktualisiert.

    5.  Für jede aktualisierte Knoten einer `REPLACE` Befehl wird an das Gerät gesendet, auf den Gerät clientseitigen Cache aktualisieren:

        `REPLACE ./Vendor/MSFT/NodeCache/ProviderID/Nodes/NodeID/ExpectedValue => ActualValue`

    6.  Eine neue Version der Cache wird erstellt und an das Gerät gesendet:

        `REPLACE ./Vendor/MSFT/NodeCache/ProviderID/CacheVersion => new_version`

        Die `new_version` Wert wird vom Server gespeichert.

5.  Der Verwaltungsserver Ruft den entsprechenden Wert aus dem Cache serverseitige ab:

    1.  Ein Wert bereits im Cache serverseitige vorhanden, rufen Sie den Wert aus dem Cache serverseitige anstelle des Geräts an.

    2.  Wenn Sie ein Wert im Cache serverseitigen nicht vorhanden ist, führen Sie folgende Schritte aus:

        1.  Erstellen Sie einen neuen Eintrag mit einer eindeutigen *NodeID* in den Cache serverseitigen an.

        2.  Abzufragen Sie das Gerät zum Abrufen des tatsächlichen Werts, der den URI.

        3.  Erstellen Sie einen neuen Knoten unter ./Vendor/MSFT/NodeCache/*ProviderID*/Nodes *NodeID* -Wert.

        4.  **Ist daher nicht möglich** und **ExpectedValue** des Knotens ./Vendor/MSFT/NodeCache/*ProviderID*/Nodes/*NodeID* einrichten.

        5.  Aktualisieren Sie die Version **CachedNodes** .

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Einstellungen für das Zwischenspeichern der Knoten erstellen:

``` syntax
<Add>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
      </Meta>
   </Item>
</Add>
<Add>
   <CmdID>4</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
      </Meta>
   </Item>
</Add>
<Add>
   <CmdID>5</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001/NodeURI</LocURI>
      </Target>
      <Data>./Vendor/MSFT/DeviceLock/Provider/MDMSRV1/DevicePasswordEnabled</Data>
   </Item>
</Add>
<Add>
   <CmdID>6</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001/ExpectedValue</LocURI>
      </Target>
      <Data>0</Data>
   </Item>
</Add>
<Add>
   <CmdID>8</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0002</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
      </Meta>
   </Item>
</Add>
<Add>
   <CmdID>9</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0002/NodeURI</LocURI>
      </Target>
      <Data>
         ./Vendor/MSFT/DeviceLock/Provider/MDMSRV1/AlphanumericDevicePasswordRequired
      </Data>
   </Item>
</Add>
<Add>
   <CmdID>10</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0002/ExpectedValue</LocURI>
      </Target>
      <Data>0</Data>
   </Item>
</Add>
```

Erste Knoten unter Provider ID MDMSRV1, Cache Version, geänderten Knoten, Knoten, erwartete Wert:

``` syntax
<Get>
   <CmdID>18</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1</LocURI>
      </Target>
   </Item>
</Get>
<Get>
   <CmdID>19</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/CacheVersion</LocURI>
      </Target>
   </Item>
</Get>
<Get>
   <CmdID>20</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/ChangedNodes</LocURI>
      </Target>
   </Item>
</Get>
<Get>
   <CmdID>21</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001</LocURI>
      </Target>
   </Item>
</Get>
<Get>
   <CmdID>22</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001/ExpectedValue</LocURI>
      </Target>
   </Item>
</Get>
```

Ersetzen den Cache Version, die Knoten-URI und die erwartete Wert:

``` syntax
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/CacheVersion</LocURI>
      </Target>
      <Data>SCCM0001@!Replace</Data>
   </Item>
</Replace>
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001/NodeURI</LocURI>
      </Target>
      <Data>./Vendor/MSFT/DeviceLock/DeviceValue/AllowSimpleDevicePassword</Data>
    </Item>
</Replace>
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/NodeCache/MDMSRV1/Nodes/Node_0001/ExpectedValue</LocURI>
      </Target>
      <Data>2</Data>
   </Item>
</Replace>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






