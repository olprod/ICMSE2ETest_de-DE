---
title: Reporting CSP
description: "Der Dienstanbieter für Reporting Konfiguration wird verwendet, um Windows Information Protection (vormals Enterprise Data Protection) und Sicherheit Überwachungsprotokolle abzurufen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 148441A6-D9E1-43D8-ADEE-FB62E85A39F7
ms.openlocfilehash: c27a119b35b3dfffc18efe147dfda81449120068
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reporting-csp"></a>Reporting CSP


Der Dienstanbieter für Reporting Konfiguration wird verwendet, um Windows Information Protection (vormals Enterprise Data Protection) und Sicherheit Überwachungsprotokolle abzurufen. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt. Unterstützung für die Überwachung von desktopsicherheit wurde für den Desktop in Windows 10, Version 1607 hinzugefügt.

Das folgende Diagramm zeigt den Reporting Konfiguration-Dienstanbieter in der Strukturformat.

![Reporting Csp-Diagramm](images/provisioning-csp-reporting.png)

<a href="" id="reporting"></a>**Reporting**  
Stammknoten.

<a href="" id="reporting-enterprisedataprotection"></a>**Reporting/EnterpriseDataProtection**  
Inneren Knoten zum Abrufen von der Windows-Information Protection (vormals Enterprise Data Protection) protokolliert.

<a href="" id="reporting-securityauditing--for-mobile-only-"></a>**Reporting/SecurityAuditing** (für Mobile)  
Interior-Knoten für die Sicherheit Überwachungsprotokolle abrufen. Dieser Knoten ist nur für mobile Geräte.

<a href="" id="retrievebytimerange"></a>**RetrieveByTimeRange**  
Gibt die Protokolle, die innerhalb der Werte von StartTime und StopTime vorhanden sind. Die Werte von StartTime und StopTime werden im ISO 8601-Format angegeben. Wenn die Werte von StartTime und StopTime nicht angegeben wurden, werden die Werte als zuerst vorhandenen oder letzten vorhandenen Zeit interpretiert.

Es folgen die anderen möglichen Szenarien:

-   Wenn die Werte von StartTime und StopTime nicht angegeben wurden, wird alle vorhandenen Protokolle zurückgegeben.
-   Wenn der StopTime wird angegeben, aber der Werte von StartTime nicht angegeben, werden alle Protokolle, die vorhanden sein, bevor die StopTime zurückgegeben.
-   Wenn die Werte von StartTime angegeben ist, jedoch die StopTime nicht ist, angegeben und klicken Sie dann alle, die protokolliert, die aus der Werte von StartTime vorhanden werden zurückgegeben.

<a href="" id="retrievebycount"></a>**RetrieveByCount**  
Interior-Knoten zum Abrufen von einer angegebenen Anzahl von Protokolle aus der Werte von StartTime. Die Werte von StartTime wird im ISO 8601-Format angegeben. Sie können die Anzahl der erforderlichen festlegen LogCount und StartTime Protokolle festlegen. Wenn die gesamte Nummer Protokolle ist kleiner als LogCount zurückgegeben die angegebene Anzahl von Protokoll oder weniger.

<a href="" id="logs"></a>**Protokolle**  
Enthält die reporting-Protokolle.

Werttyp ist XML.

Unterstützte Vorgänge ist abrufen.

<a href="" id="starttime"></a>**StartTime**  
Gibt die Startzeit für das Abrufen von Protokollen.

Werttyp ist Zeichenfolge. Verwenden Sie ISO 8601-Format.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="stoptime"></a>**StopTime**  
Gibt die Endzeit für das Abrufen von Protokollen.

Werttyp ist Zeichenfolge. Verwenden Sie ISO 8601-Format.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="logcount"></a>**LogCount**  
Gibt die Anzahl der Protokolle zum Abrufen aus der Werte von StartTime an.

Werttyp ist int.

Unterstützte Vorgänge sind Get und ersetzen.

## <a name="examples"></a>Beispiele


Rufen Sie aller verfügbaren Windows Information Protection (vormals Enterprise Data Protection) Protokolle aus der angegebenen StartTime starten ab.

``` syntax
<SyncML>
    <SyncBody>
        <Replace>
            <CmdID>3</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/PolicyManager/My/DataProtection/EnterpriseProtectedDomainNames</LocURI></Target>
                <Data>microsoft.com|office.com|xbox.com</Data>
            </Item>
        </Replace>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/Reporting/EnterpriseDataProtection/RetrieveByTimeRange/StartTime</LocURI></Target>
                <Data>2012-11-30T01:48:14.233Z</Data>
            </Item>
        </Replace>
        <Get>
            <CmdID>4</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/Reporting/EnterpriseDataProtection/RetrieveByTimeRange/Logs</LocURI></Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

Rufen Sie eine bestimmte Anzahl von Sicherheit, beginnend mit dem angegebenen StartTime Überwachungsprotokolle ab.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/LogCount
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>10</Data>
      </Item>
    </Replace>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/StartTime
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>2015-08-12T08:15:30:27</Data>
      </Item>
    </Replace>
    <Get>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/Logs
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Final/> 
  </SyncBody>
</SyncML>
```

 

 






