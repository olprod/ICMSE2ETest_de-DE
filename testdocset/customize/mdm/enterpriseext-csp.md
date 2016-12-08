---
title: EnterpriseExt CSP
description: EnterpriseExt CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ACA5CD79-BBD5-4DD1-86DA-0285B93982BD
ms.openlocfilehash: d352a7302d269e3ad6699f18d07b2130381e4136
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseext-csp"></a>EnterpriseExt CSP


Der Dienstanbieter für EnterpriseExt Konfiguration kann OEMs eigene eindeutige ID für ihren Geräten legen fest, Helligkeit Anzeigewerte, und legen Sie das LED-Verhalten.

> **Hinweis**   EnterpriseExt CSP ist nur in Windows 10 Mobile unterstützt.

 

Das folgende Diagramm zeigt den EnterpriseExt Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) und OMA-Clientbereitstellung verwendet.

![Enterpriseext csp](images/provisioning-csp-enterpriseext.png)

In der folgenden Liste sind die Merkmale und Parameter.

<a href="" id="--vendor-msft-enterpriseext"></a>**./Vendor/MSFT/EnterpriseExt**  
Der Stammknoten für den Dienstanbieter für EnterpriseExt-Konfiguration. Unterstützte Vorgänge ist abrufen.

<a href="" id="devicecustomdata"></a>**DeviceCustomData**  
Der Knoten für das Festlegen der benutzerdefinierten Geräte-ID und die Zeichenfolge.

<a href="" id="devicecustomdata-customid"></a>**DeviceCustomData/CustomID**  
Alle String-Wert wie die Geräte-ID. Dieser Wert wird in den **Einstellungen** &gt; **zu** &gt; **Info**.

Es folgt ein Beispiel für die erste benutzerdefinierter Daten.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/EnterpriseExt/DeviceCustomData/CustomID</LocURI>
                </Target>
            </Item>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/EnterpriseExt/DeviceCustomData/CustomString</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="devicecustomdata-customstring"></a>**DeviceCustomData/CustomString**  
Alle String-Wert, der mit dem Gerät verbunden ist.

Es folgt ein Beispiel zum Festlegen von benutzerdefinierter Daten.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/EnterpriseExt/DeviceCustomData/CustomID</LocURI>
                </Target>
                <Data>urn:uuid:130CCE0D-0187-5866-855A-DE7406F76046</Data> 
            </Item>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/EnterpriseExt/DeviceCustomData/CustomString</LocURI>
                </Target>
                <Data>{"firstName":"John","lastName":"Doe"}</Data> 
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="brightness"></a>**Helligkeit**  
Der Knoten für das Gerät Helligkeitswerte festlegen.

<a href="" id="brightness-default"></a>**Helligkeit/Default**  
Anzeige Helligkeit Standardwert. Sie können beispielsweise maximieren Akkulaufzeit durch Reduzierung den Standardwert oder legen es auf Mittel in eine Funktion, die im Allgemeinen dunkler.

Gültige Werte sind:

-   Automatisch – das Gerät bestimmt die Helligkeit
-   Low
-   Mittel
-   High

Die unterstützten Vorgänge sind Get und ersetzen.

Es folgt ein Beispiel zum Abrufen des aktuellen Standardwert.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/Brightness/Default</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

Es folgt ein Beispiel für das Festlegen des Standardwert auf Mittel.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/Brightness/Default</LocURI>
        </Target>
        <Data>medium</Data>
      </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="brightness-maxauto"></a>**Helligkeit/MaxAuto**  
Maximale Helligkeit Anzeigewert, wenn das Gerät zum automatischen Modus festgelegt ist. Die Helligkeit Gerät werden nie höher ist als der MaxAuto-Wert. Der Wert Werte sind:

-   Low
-   Mittel
-   High

Die unterstützten Vorgänge sind Get und ersetzen.

Es folgt ein Beispiel für das Festlegen der maximalen Auto-Helligkeit auf Mittel.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/Brightness/MaxAuto</LocURI>
        </Target>
        <Data>medium</Data>
      </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="ledalertnotification"></a>**LedAlertNotification**  
Der Knoten für die Einstellung LED-Verhalten des Geräts.

<a href="" id="ledalertnotification-state"></a>**LedAlertNotification/Status**  
FÜHRTEN Zustand. Gültige Werte sind:

-   0 – deaktiviert
-   1 – auf
-   2 - blinken

Beispiel: LED-auf

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/Intensity</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>100</Data>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/State</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>1</Data>
      </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

Beispiel: LED aus

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/State</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>0</Data>
      </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="ledalertnotification-intensity"></a>**LedAlertNotification/Intensität**  
Die LED-Helligkeit Intensität. Sie können den Wert zwischen 1 und 100 festlegen.

Beispiel: GEHALTENE blinken

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/Period</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>500</Data>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/Dutycycle</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>70</Data>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/Intensity</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>100</Data>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/Cyclecount</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>543210</Data>
      </Item>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseExt/LedAlertNotification/State</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
        </Meta>        
        <Data>2</Data>
      </Item>
    </Replace>
    <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="ledalertnotification-period"></a>**LedAlertNotification/Zeitraum**  
Dauer der einzelnen blinken, also die Zeit des ON + DEAKTIVIERT. Der Wert wird in Millisekunden. Dies gilt nur für blinken.

<a href="" id="ledalertnotification-dutycycle"></a>**LedAlertNotification/DutyCycle**  
DAUER, während eine blinken Cycle FÜHRTE. Sie können den Wert zwischen 1 und 100 festgelegt. Dies gilt nur für blinken.

<a href="" id="ledalertnotification-cyclecount"></a>**LedAlertNotification/Cyclecount**  
Anzahl der blinken durchläuft. Der Datentyp ist eine 4-Byte-Ganzzahl mit Vorzeichen. Alle negativen Wert oder 0 (null) erzeugt einen Fehler. Dieser Knoten ist nur gültig für blinken.

<a href="" id="devicereboot"></a>**DeviceReboot**  
In Windows 10 entfernt.

<a href="" id="devicereboot-waittime"></a>**DeviceReboot/Wartezeit**  
In 10 Windows entfernt.

<a href="" id="maintenancewindow"></a>**MaintenanceWindow**  
In 10 Windows entfernt.

<a href="" id="maintenancewindow-maintenanceallowed"></a>**MaintenanceWindow/MaintenanceAllowed**  
In Windows 10 entfernt.

<a href="" id="maintenancewindow-mwmandatory"></a>**MaintenanceWindow/MWMandatory**  
In 10 Windows entfernt.

<a href="" id="maintenancewindow-schedulexml"></a>**MaintenanceWindow/ScheduleXML**  
In 10 Windows entfernt.

<a href="" id="maintenancewindow-mwnotificationduration"></a>**MaintenanceWindow/MWNotificationDuration**  
In Windows 10 entfernt.

<a href="" id="maintenancewindow-mwminimumduration"></a>**MaintenanceWindow/MWminimumDuration**  
Im Windows-10 entfernt.

<a href="" id="deviceupdate"></a>**DeviceUpdate**  
Im Windows-10 entfernt.

<a href="" id="deviceupdate-datetimestamp"></a>**DeviceUpdate/DateTimeStamp**  
Im Windows-10 entfernt.

<a href="" id="deviceupdate-updateresultxml"></a>**DeviceUpdate/UpdateResultXml**  
Im Windows-10 entfernt.

<a href="" id="mdm"></a>**MDM**  
In Windows 10 entfernt.

<a href="" id="mdm-server"></a>**MDM/Server**  
Im Windows-10 entfernt.

<a href="" id="mdm-username"></a>**MDM/Benutzername**  
In 10 Windows entfernt.

<a href="" id="mdm-password"></a>**MDM/Kennwort**  
Im Windows-10 entfernt.

<a href="" id="mdm-enabledeviceenrollment"></a>**MDM/EnableDeviceEnrollment**  
In 10 Windows entfernt.

<a href="" id="pfx"></a>**PFX**  
In 10 Windows entfernt.

<a href="" id="disableenterprisevalidation"></a>**DisableEnterpriseValidation**  
In Windows 10 entfernt.

 

 

10/10/2016




