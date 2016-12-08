---
title: DeviceInstanceService CSP
description: DeviceInstanceService CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f113b6bb-6ce1-45ad-b725-1b6610721e2d
ms.openlocfilehash: f67a3f66b9d48fe065fce98a3f44a598468bd325
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceinstanceservice-csp"></a>DeviceInstanceService CSP


Der Dienstanbieter für DeviceInstanceService Konfiguration bietet einige Gerät Inventar nützliche Informationen für ein Unternehmen konnte. Darüber hinaus werden diese CSP Abfragen zwei unterschiedliche Telefonnummern im Fall von zwei SIM unterstützt. Die URIs für SIM 1 und 2 SIM sind ./Vendor/MSFT/DeviceInstanceService/Identity/Identity1 und ./Vendor/MSFT/DeviceInstanceService/Identity/Identity2.

> **Hinweis**  
Nicht mehr DeviceInstanceService CSP verwenden und der aktualisierten [DeviceStatus CSP](devicestatus-csp.md) verwenden.

DeviceInstance CSP ist nur in Windows 10 Mobile unterstützt.

 

Das folgende Diagramm zeigt den DeviceInstanceService Konfiguration-Dienstanbieter in der Strukturformat.

![Bereitstellung\-Csp\-Deviceinstanceservice](images/provisioning-csp-deviceinstanceservice.png)

<a href="" id="roaming"></a>**Roaming**  
Ein boolescher Wert, der den roaming Status des Geräts angibt. In Dualmodus SIM entspricht das Gerät zwei unterschiedliche Telefonnummern unterstützt Abfragen SIM 1 explizit mit ./Vendor/MSFT/DeviceInstanceService/Identify1/Roaming funktional ./Vendor/MSFT/DeviceInstanceService/Roaming verwenden.

Unterstützte Vorgang ist **Abrufen**.

Gibt **true,** Wenn das Gerät roaming ist; andernfalls **False**.

<a href="" id="phonenumber"></a>**"PhoneNumber"**  
Eine Zeichenfolge, die Telefonnummer des Geräts, darstellt. Im Fall eines WAN-Dualmodus SIM, wenn das Gerät zwei unterschiedliche Telefonnummern unterstützt entspricht Abfragen SIM 1 explizit mit ./Vendor/MSFT/DeviceInstanceService/Identify1/PhoneNumber funktional Verwendung ./Vendor/MSFT/DeviceInstanceService/PhoneNumber.

Werttyp ist chr.

Unterstützte Vorgang ist **Abrufen**.

<a href="" id="imei"></a>**IMEI**  
Eine Zeichenfolge darstellt International Mobile Station (IMEI Equipment Identity) des Geräts. Im Fall eines WAN-Dualmodus SIM, wenn das Gerät zwei unterschiedliche Telefonnummern unterstützt entspricht Abfragen SIM 1 explizit mit ./Vendor/MSFT/DeviceInstanceService/Identify1/IMEI funktional ./Vendor/MSFT/DeviceInstanceService/IMEI verwenden.

Werttyp ist chr.

Unterstützte Vorgang ist **Abrufen**.

<a href="" id="imsi"></a>**IMSI**  
Eine Zeichenfolge, die ersten sechs Ziffern IMSI Gerätenummer (Mobile Länder-/Regionscode, Mobile Netzwerkcode) des Geräts darstellt. Im Fall eines WAN-Dualmodus SIM entspricht das Gerät zwei unterschiedliche Telefonnummern unterstützt Abfragen SIM 1 explizit mit ./Vendor/MSFT/DeviceInstanceService/Identify1/IMSI funktional ./Vendor/MSFT/DeviceInstanceService/IMSI verwenden.

Werttyp ist chr.

Unterstützte Vorgang ist **Abrufen**.

<a href="" id="identity"></a>**Identität**  
Der übergeordnete Knoten Gruppe pro SIM bestimmte Informationen im Fall eines WAN-Dualmodus SIM.

<a href="" id="identity1"></a>**Identity1**  
Der übergeordnete Knoten SIM1 bestimmte Informationen im Fall eines WAN-Dualmodus SIM gruppiert.

<a href="" id="identity2"></a>**Identity2**  
Der übergeordnete Knoten SIM2 bestimmte Informationen im Fall eines WAN-Dualmodus SIM gruppiert.

## <a name="examples"></a>Beispiele


Im folgende Beispiel gezeigt, wie zum Abfragen von servergespeicherten Status und Telefonnummer auf dem Gerät.

``` syntax
<Get>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/DeviceInstanceService/Roaming</LocURI>
        </Target>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/DeviceInstanceService/PhoneNumber</LocURI>
        </Target>
      </Item>
</Get>
```

Antwort über das Telefon.

``` syntax
<Results>
   <CmdID>3</CmdID>
   <MsgRef>1</MsgRef>
   <CmdRef>2</CmdRef>
   <Item>
      <Source><LocURI>./Vendor/MSFT/DeviceInstanceService/Roaming</LocURI></Source>
      <Meta><Format xmlns="syncml:metinf">bool</Format></Meta>
      <Data>false</Data>
   </Item>
   <Item>
      <Source><LocURI>./Vendor/MSFT/DeviceInstanceService/PhoneNumber</LocURI></Source>
      <Data>+14254458055</Data>
   </Item>
</Results>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






