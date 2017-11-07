---
title: EnterpriseExt DDF
description: EnterpriseExt DDF
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 71BF81D4-FBEC-4B03-BF99-F7A5EDD4F91B
ms.openlocfilehash: f41a9693a8b3cbe51ab9514e0e6612137b8fd30d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseext-ddf"></a>EnterpriseExt DDF


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **EnterpriseExt** -Konfiguration. DDF-Dateien werden nur mit OMA DM XML-Bereitstellung verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>EnterpriseExt</NodeName>
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
                <DDFName></DDFName>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>DeviceCustomData</NodeName>
            <DFProperties>
                <AccessType>
                    <Exec />
                    <Get />
                    <Replace />
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
                <NodeName>CustomID</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
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
                <NodeName>CustomString</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
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
        </Node>
        <Node>
            <NodeName>Brightness</NodeName>
            <DFProperties>
                <AccessType>
                    <Exec />
                    <Get />
                    <Replace />
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
                <NodeName>Default</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
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
                <NodeName>MaxAuto</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
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
        </Node>
        <Node>
            <NodeName>LedAlertNotification</NodeName>
            <DFProperties>
                <AccessType>
                    <Exec />
                    <Get />
                    <Replace />
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
                <NodeName>State</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
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
                <NodeName>Intensity</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
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
                <NodeName>Period</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
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
                <NodeName>DutyCycle</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
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
                <NodeName>Cyclecount</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
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
    </Node>
</MgmtTree>
```



 

 





