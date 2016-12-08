---
title: WindowsAdvancedThreatProtection DDF-Datei
description: WindowsAdvancedThreatProtection DDF-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0C62A790-4351-48AF-89FD-7D46C42D13E0
ms.openlocfilehash: 9fc539b3df828cde3f052499f70262fe76d027c2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowsadvancedthreatprotection-ddf-file"></a>WindowsAdvancedThreatProtection DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den **WindowsAdvancedThreatProtection** Konfigurationsdienstanbieter. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>WindowsAdvancedThreatProtection</NodeName>
        <Path>./Device/Vendor/MSFT</Path>
        <DFProperties>
          <AccessType>
            <Get />
          </AccessType>
          <Description>Windows Defender Advanced Threat Protection</Description>
          <DFFormat>
            <node />
          </DFFormat>
          <Occurrence>
            <One />
          </Occurrence>
          <Scope>
            <Permanent />
          </Scope>
          <DFType>
            <MIME>com.microsoft/1.0/MDM/WindowsAdvancedThreatProtection</MIME>
          </DFType>
        </DFProperties>
        <Node>
          <NodeName>Onboarding</NodeName>
          <DFProperties>
            <AccessType>
              <Replace />
              <Get />
            </AccessType>
            <Description>Set Windows Defender Advanced Threat Protection Onboarding blob and initiate onboarding to Windows Defender Advanced Threat Protection</Description>
            <DFFormat>
              <chr />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
        <Node>
          <NodeName>HealthState</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <Description>Represents Windows Defender Advanced Threat Protection Health State</Description>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>LastConnected</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <Description>The last successful connection.</Description>
              <DFFormat>
                <time />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>SenseIsRunning</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <DefaultValue>false</DefaultValue>
              <Description>Return Windows Defender Advanced Threat Protection service running state</Description>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>OnboardingState</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <DefaultValue>0</DefaultValue>
              <Description>Return Windows Defender Advanced Threat Protection onboarding state: 0 – not onboarded; 1 - onboarded</Description>
              <DFFormat>
                <int />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>OrgId</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <Description>Onboarded Org ID.</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>Configuration</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <Description>Represents Windows Defender Advanced Threat Protection Configuration</Description>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>SampleSharing</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
                <Replace />
              </AccessType>
              <DefaultValue>1</DefaultValue>
              <Description>Return or set Windows Defender Advanced Threat Protection Sample Sharing configuration parameter: 0 - none, 1 - All</Description>
              <DFFormat>
                <int />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>Offboarding</NodeName>
          <DFProperties>
            <AccessType>
              <Replace />
              <Get />
            </AccessType>
            <Description>Set Windows Defender Advanced Threat Protection Offboarding blob and initiate offboarding</Description>
            <DFFormat>
              <chr />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
      </Node>
</MgmtTree>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






