---
title: Neustart DDF-Datei
description: "In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Neustart Konfiguration-Dienstanbieter. DDF-Dateien werden nur mit OMA DM XML-Bereitstellung verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ABBD850C-E744-462C-88E7-CA3F43D80DB1
ms.openlocfilehash: ac910e3bee982a64cc8c555abd68383d4ea6d181
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reboot-ddf-file"></a>Neustart DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Konfigurationsdienstanbieter **neu gestartet** . DDF-Dateien werden nur mit OMA DM XML-Bereitstellung verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>Reboot</NodeName>
        <Path>./Device/Vendor/MSFT</Path>
        <DFProperties>
          <AccessType>
            <Get />
          </AccessType>
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
          <NodeName>RebootNow</NodeName>
          <DFProperties>
            <AccessType>
              <Exec />
            </AccessType>
            <DFFormat>
              <null />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFTitle>RebootNow</DFTitle>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
        <Node>
          <NodeName>Schedule</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
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
            <NodeName>Single</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
                <Replace />
              </AccessType>
              <Description>Value in ISO8601, both the date and time are required. A reboot will be scheduled at the configured date time. Setting a null (empty) date will delete the existing schedule.</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFTitle>Single</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>DailyRecurrent</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
                <Replace />
              </AccessType>
              <Description>Value in ISO8601, time is required. A reboot will be scheduled each day at the configured time starting at the date and time. Setting a null (empty) date will delete the existing schedule.</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFTitle>DailyRecurrent</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
      </Node>
</MgmtTree>
```

## <a name="related-topics"></a>Verwandte Themen


[Neustart Konfiguration-Dienstanbieter](reboot-csp.md)

 

 






