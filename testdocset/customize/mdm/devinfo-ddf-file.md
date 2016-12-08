---
title: DevInfo DDF-Datei
description: DevInfo DDF-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: beb07cc6-4133-4c0f-aa05-64db2b4a004f
ms.openlocfilehash: 2340132a510be836d9d5ad4447e6456d96875b33
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devinfo-ddf-file"></a>DevInfo DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **DevInfo** -Konfiguration. DDF-Dateien werden nur mit OMA DM XML-Bereitstellung verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC "-//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>DevInfo</NodeName>
        <Path>.</Path>
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
            <DFTitle>The interior node holding all devinfo objects</DFTitle>
            <DFType>
                <DDFName>urn:oma:mo:oma-dm-devinfo:1.0</DDFName>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>DevId</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>An unique device identifier. An application-specific global unique device identifier is provided in this node.</Description>
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
            <NodeName>Man</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
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
            <NodeName>Mod</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>Device model name, as specified and tracked by the mobile operator</Description>
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
            <NodeName>DmV</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>The current management client revision of the device.</Description>
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
            <NodeName>Lang</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>The current language at the device user interface.</Description>
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


[DevInfo Konfiguration-Dienstanbieter](devinfo-csp.md)

 

 






