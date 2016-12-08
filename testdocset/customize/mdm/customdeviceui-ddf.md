---
title: CustomDeviceUI DDF
description: CustomDeviceUI DDF
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E6D6B902-C57C-48A6-9654-CCBA3898455E
ms.openlocfilehash: 989d79a10ea2c1a7f46a6d05fcd619c9a2127ee1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customdeviceui-ddf"></a>CustomDeviceUI DDF


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **CustomDeviceUI** -Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>CustomDeviceUI</NodeName>
        <Path>./Vendor/MSFT</Path>
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
                <MIME>com.microsoft/1.0/MDM/CustomDeviceUI</MIME>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>StartupAppID</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                    <Replace />
                </AccessType>
                <Description>AppID string value is the default appid/AUMID to launch during boot up </Description>
                <DFFormat>
                    <chr />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <CaseSense>
                    <CIS />
                </CaseSense>
                <DFType>
                    <MIME>text/plain</MIME>
                </DFType>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>BackgroundTasksToLaunch</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>List of package names of background tasks that needs to be launched on boot.</Description>
                <DFFormat>
                    <node />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <CaseSense>
                    <CIS />
                </CaseSense>
                <DFTitle>Background Tasks to Launch</DFTitle>
                <DFType>
                    <DDFName></DDFName>
                </DFType>
            </DFProperties>
            <Node>
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Add />
                        <Delete />
                        <Get />
                        <Replace />
                    </AccessType>
                    <Description>Package Full Name of the App that needs be launched in the background. This can contain no entry points, a single or multiple entry points</Description>
                    <DFFormat>
                        <chr />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrMore />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <CaseSense>
                        <CIS />
                    </CaseSense>
                    <DFTitle>BackgroundTaskPackageName</DFTitle>
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


[CustomDeviceUI Konfigurationsdienstanbieter](customdeviceui-csp.md)

 

 






