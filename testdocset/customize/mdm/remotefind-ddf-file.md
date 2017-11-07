---
title: RemoteFind DDF-Datei
description: "In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den RemoteFind Konfigurationsdienstanbieter. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5864CBB8-2030-459E-BCF6-9ACB69206FEA
ms.openlocfilehash: 5cf446f6de6c4dea78a14b5618818e3ea325b92e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotefind-ddf-file"></a>RemoteFind DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **RemoteFind** -Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>RemoteFind</NodeName>
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
            <NodeName>DesiredAccuracy</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                    <Replace />
                </AccessType>
                <DefaultValue>50</DefaultValue>
                <DFFormat>
                    <int />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <CaseSense>
                    <CS />
                </CaseSense>
                <DFTitle>DesiredAccuracy</DFTitle>
                <DFType>
                    <MIME>text/plain</MIME>
                </DFType>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>MaximumAge</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                    <Replace />
                </AccessType>
                <DefaultValue>60</DefaultValue>
                <DFFormat>
                    <int />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <CaseSense>
                    <CS />
                </CaseSense>
                <DFTitle>MaximumAge</DFTitle>
                <DFType>
                    <MIME>text/plain</MIME>
                </DFType>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>Timeout</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                    <Replace />
                </AccessType>
                <DefaultValue>7</DefaultValue>
                <DFFormat>
                    <int />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <CaseSense>
                    <CS />
                </CaseSense>
                <DFTitle>Timeout</DFTitle>
                <DFType>
                    <MIME>text/plain</MIME>
                </DFType>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>Location</NodeName>
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
                <CaseSense>
                    <CS />
                </CaseSense>
                <DFTitle>Location</DFTitle>
                <DFType>
                    <DDFName></DDFName>
                </DFType>
            </DFProperties>
            <Node>
                <NodeName>Latitude</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <float />
                    </DFFormat>
                    <Occurrence>
                        <One />
                    </Occurrence>
                    <Scope>
                        <Permanent />
                    </Scope>
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>Latitude</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
            <Node>
                <NodeName>Longitude</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <float />
                    </DFFormat>
                    <Occurrence>
                        <One />
                    </Occurrence>
                    <Scope>
                        <Permanent />
                    </Scope>
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>Longitude</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
            <Node>
                <NodeName>Altitude</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <float />
                    </DFFormat>
                    <Occurrence>
                        <One />
                    </Occurrence>
                    <Scope>
                        <Permanent />
                    </Scope>
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>Altitude</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
            <Node>
                <NodeName>Accuracy</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
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
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>Accuracy</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
            <Node>
                <NodeName>AltitudeAccuracy</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
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
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>AltitudeAccuracy</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
            <Node>
                <NodeName>Age</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <time />
                    </DFFormat>
                    <Occurrence>
                        <One />
                    </Occurrence>
                    <Scope>
                        <Permanent />
                    </Scope>
                    <CaseSense>
                        <CS />
                    </CaseSense>
                    <DFTitle>Age</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
        </Node>
    </Node>
</MgmtTree>
```

 

 






