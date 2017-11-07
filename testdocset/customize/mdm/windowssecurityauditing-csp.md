---
title: WindowsSecurityAuditing CSP
description: "Der WindowsSecurityAuditing Konfiguration-Dienstanbieter (CSP) wird verwendet, um die Protokollierung von Sicherheitsüberwachungsereignisse aktivieren. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 611DF7FF-21CE-476C-AAB5-3D09C1CDF08A
ms.openlocfilehash: d8f7eb655bcd3299e44b483f66a82ddc9d145a0a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowssecurityauditing-csp"></a>WindowsSecurityAuditing CSP


Der WindowsSecurityAuditing Konfiguration-Dienstanbieter (CSP) wird verwendet, um die Protokollierung von Sicherheitsüberwachungsereignisse aktivieren. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt.

Das folgende Diagramm zeigt den WindowsSecurityAuditing Konfigurationsdienstanbieter in der Strukturformat.

![Windowssecurityauditing Csp Diagramm](images/provisioning-csp-windowssecurityauditing.png)

<a href="" id="windowssecurityauditing"></a>**WindowsSecurityAuditing**  
Stammknoten.

<a href="" id="configurationsettings"></a>**ConfigurationSettings**  
Interior-Knoten für die Verarbeitung von alle Audit-Konfigurationseinstellungen. Verwenden Sie Get-Operation nicht in diesem Knoten. Es wird nur verwendet, Konfigurationseinstellungen zu gruppieren.

<a href="" id="configurationsettings-enablesecurityauditing"></a>**ConfigurationSettings/EnableSecurityAuditing**  
Gibt an, ob zum Aktivieren oder Deaktivieren der Überwachung für das Gerät.

Werttyp ist boolean. Bei true wird ein Standardsatz von Ereignissen in eine Protokolldatei für den Upload erfasst. Bei "false" Überwachung deaktiviert ist, und Ereignisse werden nicht protokolliert. Standardwert ist false.

Unterstützte Vorgänge sind Get und ersetzen.

## <a name="examples"></a>Beispiele


Aktivieren Sie Protokollieren von Ereignissen.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/WindowsSecurityAuditing/ConfigurationSettings/EnableSecurityAuditing
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">bool</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>true</Data>
      </Item>
    </Replace>
    <Final/> 
  </SyncBody>
</SyncML>
```

Weitere Informationen zu Windows-Sicherheit, Überwachung finden Sie unter [Was ist neu in die Überwachung](https://technet.microsoft.com/itpro/windows/whats-new/security-auditing).

 

 






