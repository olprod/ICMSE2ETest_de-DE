---
title: CustomDeviceUI CSP
description: CustomDeviceUI CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 20ED1867-7B9E-4455-B397-53B8B15C95A3
ms.openlocfilehash: 4beccdf1e2b71431904f91f257798e66e01482ca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customdeviceui-csp"></a>CustomDeviceUI CSP

Der Dienstanbieter für CustomDeviceUI Konfiguration kann OEMs implementieren Programmversionen benutzerdefinierte Vordergrund als auch die Hintergrundaufgaben auf einer IoT-Gerät ausgeführt IoT Core ausgeführt. Pro Gerät wird nur eine Vordergrund-Anwendung unterstützt. Mehrere Hintergrundaufgaben werden unterstützt.
Das folgende Diagramm zeigt den CustomDeviceUI Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) und OMA-Clientbereitstellung verwendet.

> **Hinweis**  Dieses Dienstanbieters Konfiguration gilt nur für Windows 10 IoT Core (IoT Core).

![Customdeviceui csp](images/provisioning-csp-customdeviceui.png)

<a href="" id="./Vendor/MSFT/CustomDeviceUI"></a>**./Vendor/MSFT/CustomDeviceUI**  
Der Stammknoten für den Dienstanbieter für CustomDeviceUI-Konfiguration. Der unterstützte Vorgang ist Get.

<a href="" id="StartupAppID"></a>**StartupAppID**  
AppID String-Wert ist die standardmäßige Appid/AUMID während des Starts zu starten. Die unterstützten Vorgänge sind Get und ersetzen.

<a href="" id="BackgroundTasksToLaunch"></a>**BackgroundTasksToLaunch**  
Liste der Namen der Lösungspakete Hintergrund Aufgaben, die auf Gerät Systemstart gestartet werden müssen. Der unterstützte Vorgang ist Get.

<a href="" id="BackgroundTasksToLaunch/BackgroundTaskPackageName"></a>**BackgroundTasksToLaunch / ***_BackgroundTaskPackageName_**  
Paket vollständigen Namen der App, die im Hintergrund gestartet werden muss. Dies kann keine Einstiegspunkte, einen Einstiegspunkt für einzelne oder mehrere Einstiegspunkte enthalten. Die unterstützten Vorgänge sind Add, Delete, Get, und Ersetzen Sie.

## <a name="syncml-examples"></a>Beispiele für SyncML


**StartupAppID festlegen**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>      
        <Replace>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>./Vendor/MSFT/CustomDeviceUI/StartupAppID</LocURI>
            </Target>       
             <Meta>
                <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>DefaultApp_cw5n1h2txyewy!App</Data>
        </Item>
        </Replace>        
     <Final/>
  </SyncBody>
</SyncML>
```

**Abrufen Sie aller Hintergrundaufgaben**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>      
        <Get>
          <CmdID>1</CmdID>
          <Item>
            <Target>
                <LocURI>./Vendor/MSFT/CustomDeviceUI/BackgroundTaskstoLaunch?list=Struct</LocURI>
            </Target>
          </Item>
        </Get>        
     <Final/>
  </SyncBody>
</SyncML>
```

**Hintergrundaufgabe hinzufügen**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>      
        <Add>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>./Vendor/MSFT/CustomDeviceUI/BackgroundTaskstoLaunch/BackgroundService1_1.3.0.1_neutral__8wekyb3d8bbwe</LocURI>
            </Target>
            <Meta>
                <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>0</Data>
          </Item>
        </Add>        
     <Final/>
  </SyncBody>
</SyncML>
```

 

 






