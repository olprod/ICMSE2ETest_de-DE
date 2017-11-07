---
title: CMPolicy CSP
description: CMPolicy CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 62623915-9747-4eb1-8027-449827b85e6b
ms.openlocfilehash: 5e2cd0a588215fbfc306ec69dfd220d2d6447e94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cmpolicy-csp"></a>CMPolicy CSP


Der Dienstanbieter für CMPolicy Konfiguration definiert Regeln, die den Verbindungs-Manager wird verwendet, um die richtige Verbindung für eine Anforderung der Verbindung zu identifizieren.

> **Hinweis**  
Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_NETWORKING\_ADMIN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Jeder Richtlinieneintrag identifiziert eine oder mehrere Anwendungen in Kombination mit einem Host-Muster. Der Richtlinieneintrag wird eine Liste der Verbindungsdetails zugewiesen, die Verbindungs-Manager wird verwendet, um die Anwendung und Host-Muster übereinstimmende Verbindungsanfragen erfüllen. CMPolicy Konfiguration-Dienstanbieter kann mehrere Richtlinien aufweisen.

**Richtlinie Sortierung**: Es gibt keine explizite Reihenfolge der Richtlinien. Allgemein gilt, dass die meisten konkreten oder bestimmte Richtlinie Zuordnungen Vorrang dauern.

**Standardrichtlinien**: Richtlinien in der Reihenfolge der ihren Bereich mit den am häufigsten Richtlinien berücksichtigt werden, bevor Sie den allgemeinen Richtlinien angewendet werden. Standardverhalten für das Telefon gilt für alle Anwendungen und alle Domänen und wird nur verwendet, wenn keine andere, spezifischeren Richtlinie verfügbar ist. Die Standardrichtlinie ist zunächst alle verfügbaren Wi-Fi-Netzwerk und klicken Sie dann auf alle verfügbaren APN.

Im folgenden Diagramm wird das CMPolicy Konfiguration Service Provider-Management-Objekt im Strukturformat von Open Mobile Allianz (OMA)-Clientbereitstellung und OMA Gerätemanagement verwendet.

![Cmpolicy Csp (dm, cp)](images/provisioning-csp-cmpolicy.png)

<a href="" id="policyname"></a>***Richtlinienname***  
Definiert den Namen der Richtlinie.

<a href="" id="sid"></a>**SID**  
Der Wert der SID, hängt von der Clienttyp.

Für app-basierte Zuordnung von universellen Windows-Plattform (UWP)-Richtlinien ist SID den Paketnamen Familie ohne geschweiften Klammern {}, nicht die Anwendung.

Für nicht UWP Anwendung-basierte Zuordnung-Richtlinien ist SID die Produkt-ID in GUID-Format. Die geschweiften Klammern {}, um die GUID sind erforderlich.

Host-basierte Zuordnung-Richtlinien SID muss festgelegt werden `*`.

<a href="" id="clienttype"></a>**Clienttyp**  
Gibt an, welche Richtlinie Zuordnung.

In der folgenden Liste werden die verfügbaren Zuordnung Richtlinientypen beschrieben:

-   Anwendung-basierte Zuordnung Richtlinien gelten für Applikationen. Um diese Zuordnung festzulegen, verwenden Sie den Wert `app`.

-   Host-basierte Zuordnung Richtlinien gelten für alle Arten von Clients, die Verbindung zum angegebenen Hosts anfordern. Um diese Zuordnung festzulegen, verwenden Sie den Wert `*`.

<a href="" id="host"></a>**Host**  
Gibt den Namen eines Musters Host. Der Hostname wird auf die Anforderung Verbindung die richtige Richtlinie verwenden auswählen verglichen.

Das Host-Muster kann zwei Platzhalter haben "\*" und "+". Das Muster der Host ist kein URL-Muster, und es gibt kein Konzept des Transport oder Pfade auf dem angegebenen Host. Beispielsweise das Muster Host möglicherweise "\*.host\_" Name.com "" Präfix an den Host abgleichen\_"Name.com" Domänen. Entspricht das Muster Host "www.host\_" Name.com "" und "mail.host\_" Name.com "", aber es stimmt nicht überein "Host\_" Name.com "".

<a href="" id="orderedconnections"></a>**OrderedConnections**  
Gibt an, ob die Liste der Verbindungen Rangfolge ist.

Der Wert "0" gibt an, dass die Verbindungen in der Rangordnung nicht aufgeführt sind. Der Wert "1" gibt an, dass die aufgeführten Verbindungen in der Rangordnung sind.

<a href="" id="connxxx"></a>**Conn ***_XXX_**  
Listet die Verbindungen mit der Richtlinie verknüpft ist. Elementnamen beginnen mit "Conn", gefolgt von drei Ziffern, welche Schrittweite beginnend mit "000". Beispielsweise würde eine Richtlinie, die auf fünf Verbindungen angewendet Element-Einträge, die mit dem Namen "Conn000", "Conn001", "Conn002", "Conn003" und "Conn004" haben.

<a href="" id="connectionid"></a>**ConnectionID**  
Gibt einen eindeutigen Bezeichner für eine Verbindung in einer Gruppe von Verbindungen an. Der genaue Wert basiert auf der Type-Parameter.

Für `CMST_CONNECTION_NAME`, geben Sie den Verbindungsnamen. Wenn Sie eine Verbindung mithilfe der CM konfiguriert haben beispielsweise\_CellularEntries Konfiguration-Dienstanbieter der Verbindungsname den Namen der Verbindung werden konnte. Wenn Sie eine NAP mit der NAPID legen Sie auf "GPRS1" konfiguriert haben, kann der Name der Verbindung handeln.“GPRS1@WAP”.

Für `CMST_CONNECTION_TYPE`, geben Sie den GUID für den gewünschten Verbindungstyp. Die geschweiften Klammern {}, um die GUID sind erforderlich. Die folgenden Verbindungstypen sind verfügbar:

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Verbindungstyp</th>
<th>GUID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>G/M2</p></td>
<td><p>{A05DC613-E393-40ad-AA89-CCCE04277CD9}</p></td>
</tr>
<tr class="even">
<td><p>CDMA</p></td>
<td><p>{274AD55A-4A70-4E35-93B3-AE2D2E6727FC}</p></td>
</tr>
<tr class="odd">
<td><p>Legacy 3GPP</p></td>
<td><p>{6DE4C04B-B74E-47FA-99E5-8F2097C06A92}</p></td>
</tr>
<tr class="even">
<td><p>LZF</p></td>
<td><p>{2378E547-8312-46A5-905E-5C581E92693B}</p></td>
</tr>
<tr class="odd">
<td><p>Wi-Fi</p></td>
<td><p>{8568B401-858E-4B7B-B3DF-0FD4927F131B}</p></td>
</tr>
<tr class="even">
<td><p>Wi-Fi-hotspot</p></td>
<td><p>{072FC7DC-1D93-40D1-9BB0-2114D7D73434}</p></td>
</tr>
</tbody>
</table>

 

Für `CMST_CONNECTION_NETWORK_TYPE`, geben Sie die GUID für den gewünschten Netzwerktyp. Die geschweiften Klammern {}, um die GUID, sind erforderlich. Die folgenden Typen sind verfügbar:

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Netzwerktyp</th>
<th>GUID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>GPRS</p></td>
<td><p>{AFB7D659-FC1F-4EA5-BDD0-0FDA62676D96}</p></td>
</tr>
<tr class="even">
<td><p>1XRTT</p></td>
<td><p>{B1E700AE-A62F-49FF-9BBE-B880C995F27D}</p></td>
</tr>
<tr class="odd">
<td><p>EDGE</p></td>
<td><p>{C347F8EC-7095-423D-B838-7C7A7F38CD03}</p></td>
</tr>
<tr class="even">
<td><p>WCDMA UMTS</p></td>
<td><p>{A72F04C6-9BE6-4151-B5EF-15A53E12C482}</p></td>
</tr>
<tr class="odd">
<td><p>WCDMA FOMA</p></td>
<td><p>{B8326098-F845-42F3-804E-8CC3FF7B50B4}</p></td>
</tr>
<tr class="even">
<td><p>1XEVDO</p></td>
<td><p>{DD42DF39-EBDF-407C-8146-1685416401B2}</p></td>
</tr>
<tr class="odd">
<td><p>1XEVDV</p></td>
<td><p>{61BF1BFD-5218-4CD4-949C-241CA3F326F6}</p></td>
</tr>
<tr class="even">
<td><p>HSPA HSDPA</p></td>
<td><p>{047F7282-BABD-4893-AA77-B8B312657F8C}</p></td>
</tr>
<tr class="odd">
<td><p>HSPA HSUPA</p></td>
<td><p>{1536A1C6-A4AF-423C-8884-6BDDA3656F84}</p></td>
</tr>
<tr class="even">
<td><p>LZF</p></td>
<td><p>{B41CBF43-6994-46FF-9C2F-D6CA6D45889B}</p></td>
</tr>
<tr class="odd">
<td><p>EHRPD</p></td>
<td><p>{7CFA04A5-0F3F-445C-88A4-C86ED2AD94EA}</p></td>
</tr>
<tr class="even">
<td><p>Ethernet 10 Mbit/s</p></td>
<td><p>{97D3D1B3-854A-4C32-BD1C-C13069078370}</p></td>
</tr>
<tr class="odd">
<td><p>100 Mbit/s Ethernet</p></td>
<td><p>{A8F4FE66-8D04-43F5-9DD2-2A85BD21029B}</p></td>
</tr>
<tr class="even">
<td><p>Gbit/s Ethernet-</p></td>
<td><p>{556C1E6B-B8D4-448E-836D-9451BA4CCE75}</p></td>
</tr>
</tbody>
</table>

 

Für `CMST_CONNECTION_DEVICE_TYPE`; Geben Sie den GUID für den gewünschten Gerätetyp. Die geschweiften Klammern {}, um die GUID sind erforderlich. Die folgenden Medienarten stehen zur Verfügung:

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Gerätetyp</th>
<th>GUID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mobiltelefon</p></td>
<td><p>{F9A53167-4016-4198-9B41-86D9522DC019}</p></td>
</tr>
<tr class="even">
<td><p>Ethernet</p></td>
<td><p>{97844272-00C7-4572-B20A-D8D861C095F2}</p></td>
</tr>
<tr class="odd">
<td><p>Bluetooth</p></td>
<td><p>{1D793123-701A-4fd0-B6AE-9C3C57E99C2C}</p></td>
</tr>
<tr class="even">
<td><p>Virtuelle</p></td>
<td><p>{EAA02CE5-9C70-4E87-97FE-55C9DEC847D4}</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="type"></a>**Typ**  
Gibt den Typ der Verbindung, auf die verwiesen wird. Die folgende Liste beschreibt die verfügbaren Verbindungstypen:

-   `CMST_CONNECTION_NAME`– Eine Verbindung, die durch Name angegebenen.

-   `CMST_CONNECTION_TYPE`– Eine beliebige Verbindung eines angegebenen Typs.

-   `CMST_CONNECTION_NETWORK_TYPE`– Eine beliebige Verbindung eines angegebenen Typs.

-   `CMST_CONNECTION_DEVICE_TYPE`– Eine beliebige Verbindung von der angegebenen Gerätetyp.

## <a name="oma-client-provisioning-examples"></a>Beispiele für die Bereitstellung OMA-client


Hinzufügen einer Richtlinie Anwendung-basierte Zuordnung. In diesem Beispiel wird die ConnectionId für Type CMST\_VERBINDUNG\_NAME festgelegt ist, auf den Namen der Verbindung ("GPRSConn1") an, der mit der Verbindungs-Manager konfiguriert ist\_CellularEntries Konfigurationsdienstanbieter.

``` syntax
<wap-provisioningdoc>

   <characteristic type="CM_CellularEntries">
       <characteristic type="GPRSConn1">
          <parm name="ConnectionType" value="gprs" />
             <characteristic type="DevSpecificCellular">
                <parm name="GPRSInfoAccessPointName" value="apn.adatum.com" />
         </characteristic>
          <parm name="AlwaysOn" value="0" />
          <parm name="Enabled" value="1" />
       </characteristic>
    </characteristic>

   <characteristic type="CMPolicy">
      <characteristic type="Policy1">
       <parm name="SID" value="{A05D1234-F393-9385-AA89-CD3E049367D2}" />
       <parm name="ClientType" value="app" />
       <parm name="Host" value="*.+" />
       <parm name="OrderedConnections" value="1" />
       <characteristic type="Connections">
           <characteristic type="Conn000">
               <parm name="Type" value="CMST_CONNECTION_DEVICE_TYPE" /> 
               <parm name="ConnectionId" value="{F9A53167-4016-4198-9B41-86D9522DC019}" /> 
           </characteristic>
           <characteristic type="Conn001">
               <parm name="Type" value="CMST_CONNECTION_NETWORK_TYPE" /> 
               <parm name="ConnectionId" value="{AFB7D659-FC1F-4EA5-BDD0-0FDA62676D96}" /> 
           </characteristic>
           <characteristic type="Conn002">
               <parm name="Type" value="CMST_CONNECTION_NAME" /> 
               <parm name="ConnectionId" value="GPRSConn1" /> 
           </characteristic>
           <characteristic type="Conn003">
              <parm name="Type" value="CMST_CONNECTION_TYPE" /> 
              <parm name="ConnectionId" value="{072FC7DC-1D93-40d1-9BB0-2114D7D73434}" /> 
           </characteristic>
       </characteristic>
      </characteristic>
    </characteristic>
</wap-provisioningdoc>
```

Eine Richtlinie-basierte Zuordnung hinzufügen. In diesem Beispiel wird die ConnectionId für Type CMST\_VERBINDUNG\_NAME festgelegt ist, auf den Namen der Verbindung ("GPRSConn1") an, der mit der Verbindungs-Manager konfiguriert ist\_CellularEntries Konfigurationsdienstanbieter.

``` syntax
<wap-provisioningdoc>

   <characteristic type="CM_CellularEntries">
       <characteristic type="GPRSConn1">
          <parm name="ConnectionType" value="gprs" />
             <characteristic type="DevSpecificCellular">
                <parm name="GPRSInfoAccessPointName" value="apn.adatum.com" />
         </characteristic>
          <parm name="AlwaysOn" value="0" />
          <parm name="Enabled" value="1" />
       </characteristic>
    </characteristic>

   <characteristic type="CMPolicy">
      <characteristic type="Policy3">
       <parm name="SID" value="*" />
       <parm name="ClientType" value="*" />
       <parm name="Host" value="*.contoso.com" />
       <parm name="OrderedConnections" value="1" />
       <characteristic type="Connections">
           <characteristic type="Conn000">
               <parm name="Type" value="CMST_CONNECTION_DEVICE_TYPE" /> 
               <parm name="ConnectionId" value="{F9A53167-4016-4198-9B41-86D9522DC019}" /> 
           </characteristic>
           <characteristic type="Conn001">
               <parm name="Type" value="CMST_CONNECTION_NETWORK_TYPE" /> 
               <parm name="ConnectionId" value="{AFB7D659-FC1F-4EA5-BDD0-0FDA62676D96}" /> 
           </characteristic>
           <characteristic type="Conn002">
               <parm name="Type" value="CMST_CONNECTION_NAME" /> 
               <parm name="ConnectionId" value="GPRSConn1" /> 
           </characteristic>
           <characteristic type="Conn003">
               <parm name="Type" value="CMST_CONNECTION_TYPE" /> 
               <parm name="ConnectionId" value="{072FC7DC-1D93-40d1-9BB0-2114D7D73434}" /> 
           </characteristic>
       </characteristic>
      </characteristic>
    </characteristic>

</wap-provisioningdoc>
```

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Hinzufügen einer Application-basierte Zuordnung Richtlinie:

``` syntax
<SyncML>
    <SyncBody>
        <Atomic>
    <CmdID>8000</CmdID>
    <Add>
        <CmdID>8051</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/SID</LocURI>
            </Target>
            <Data>{A05D1234-F393-9385-AA89-CD3E049367D2}</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8052</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/ClientType</LocURI>
            </Target>
            <Data>app</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8053</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/Host</LocURI>
            </Target>
            <Data>*.+</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8054</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/OrderedConnections</LocURI>
            </Target>
            <Data>1</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8055</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/Connections/Conn000/ConnectionId</LocURI>
            </Target>
            <Data>{A05DC613-E393-40AD-AA89-CCCE04277CD9}</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8056</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy4/Connections/Conn000/Type</LocURI>
            </Target>
            <Data>CMST_CONNECTION_DEVICE_TYPE</Data>
        </Item>
    </Add>
        </Atomic> 
        <Final/>
    </SyncBody>
</SyncML>
```

Hinzufügen einer Richtlinie-basierte Zuordnung:

``` syntax
<SyncML>
    <SyncBody>
        <Atomic>
    <CmdID>8000</CmdID>
    <Add>
        <CmdID>8049</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/SID</LocURI>
            </Target>
            <Data>*</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8050</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/ClientType</LocURI>
            </Target>
            <Data>*</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8051</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/Host</LocURI>
            </Target>
            <Data>*.contoso.com</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8052</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/OrderedConnections</LocURI>
            </Target>
            <Data>1</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8053</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/Connections/Conn000/ConnectionId</LocURI>
            </Target>
            <Data>{AFB7D659-FC1F-4EA5-BDD0-0FDA62676D96}</Data>
        </Item>
    </Add>
    <Add>
        <CmdID>8054</CmdID>
        <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CMPolicy/BTHPolicy6/Connections/Conn000/Type</LocURI>
            </Target>
            <Data>CMST_CONNECTION_NETWORK_TYPE</Data>
        </Item>
    </Add>
        </Atomic>
        <Final/>
    </SyncBody>
</SyncML>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p>
<p>Rekursive Abfrage: Ja</p>
<p>Abfragen auf oberster Ebene Ebene: Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






