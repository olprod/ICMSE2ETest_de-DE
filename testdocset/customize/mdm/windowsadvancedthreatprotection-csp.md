---
title: WindowsAdvancedThreatProtection CSP
description: WindowsAdvancedThreatProtection CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6C3054CA-9890-4C08-9DB6-FBEEB74699A8
ms.openlocfilehash: a69f7277913d31fe44b1977425548ffc7f8ec99f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowsadvancedthreatprotection-csp"></a>WindowsAdvancedThreatProtection CSP


Der Windows Defender erweiterte Threat Protection (WDATP) Konfiguration-Dienstanbieter (CSP) ermöglicht es IT-Administratoren, integrierte, Konfiguration und Integritätsstatus und externe Endpunkte ermitteln Sie für WDATP.

Das folgende Diagramm zeigt den WDATP Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) verwendet.

![Windowsadvancedthreatprotection Csp Diagramm](images/provisioning-csp-watp.png)

Die folgende Liste beschreibt die Merkmale und Parameter.

<a href="" id="--device-vendor-msft-windowsadvancedthreatprotection"></a>**./Device/Vendor/MSFT/WindowsAdvancedThreatProtection**  
Der Stammknoten für den Dienstanbieter für Windows Defender erweiterte Threat Protection-Konfiguration.

Unterstützte Vorgang ist Get.

<a href="" id="onboarding"></a>**Onboarding**  
Windows Defender erweiterte Threat Protection Onboarding Blob festgelegt und Onboarding zu Windows Defender erweiterte Bedrohungsschutz initiiert.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="healthstate"></a>**HealthState**  
Knoten, den Integritätsstatus Windows Defender erweiterte Threat Protection darstellt.

<a href="" id="healthstate-lastconnected"></a>**HealthState/LastConnected**  
Enthält den Zeitstempel der letzten erfolgreichen Verbindung.

Unterstützte Vorgang ist Get.

<a href="" id="healthstate-senseisrunning"></a>**HealthState/SenseIsRunning**  
Boolescher Wert, der die Windows Defender erweiterte Threat Protection Sinne Zustand "aktiv" bezeichnet.

Der Standardwert ist false.

Unterstützte Vorgang ist Get.

<a href="" id="healthstate-onboardingstate"></a>**HealthState/OnboardingState**  
Stellt den Onboarding-Zustand.

Unterstützte Vorgang ist Get.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht Onboarded.
-   1 – Onboarded

<a href="" id="healthstate-orgid"></a>**HealthState/Organisations-ID**  
Zeichenfolge, die Organisations-ID darstellt.

Unterstützte Vorgang ist Get.

<a href="" id="configuration"></a>**Konfiguration**  
Stellt die Konfiguration für den Schutz von Windows Defender erweiterte Bedrohung dar.

<a href="" id="configuration-samplesharing"></a>**Konfiguration/SampleSharing**  
Zurückgeben oder Festlegen des Parameters Konfiguration Windows Defender erweiterte Threat Protection Beispiel Freigabe: 0 – keine, 1 - alle

In der folgenden Liste sind die unterstützten Werte:

-   0 – keine
-   1 (Standard) – alle

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="offboarding"></a>**Offboarding**  
Legt den Blob Windows Defender erweiterte Threat Protection Offboarding und Offboarding zu Windows Defender erweiterte Bedrohungsschutz initiiert.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get und ersetzen.

## <a name="examples"></a>Beispiele


``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>11</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Onboarding
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Get>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/LastConnected
          </LocURI>
        </Target>
      </Item>
    </Get>
        <Get>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/OnBoardingState
          </LocURI>
        </Target>
      </Item>
    </Get>
            <Get>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/SenseIsRunning
          </LocURI>
        </Target>
      </Item>
    </Get>
            <Get>
      <CmdID>4</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/OrgId
          </LocURI>
        </Target>
      </Item>
    </Get>

            <Get>
      <CmdID>5</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Configuration/SampleSharing
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Get>
      <CmdID>99</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Final/> 
  </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






