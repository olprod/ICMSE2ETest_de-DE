---
title: Reporting DDF-Datei
description: "In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für Reporting-Konfiguration. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt. Unterstützung für die Überwachung von desktopsicherheit wurde für den Desktop in Windows 10, Version 1607 hinzugefügt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7A5B79DB-9571-4F7C-ABED-D79CD08C1E35
ms.openlocfilehash: 6271384d2e2e5c454c6d6239afacc601bbe39f59
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reporting-ddf-file"></a>Reporting DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für Reporting-Konfiguration. Dieser CSP wurde in Windows 10, Version 1511 hinzugefügt. Unterstützung für die Überwachung von desktopsicherheit wurde für den Desktop in Windows 10, Version 1607 hinzugefügt.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>Reporting</NodeName>
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
                <MIME>com.microsoft/2.0/MDM/Reporting</MIME>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>EnterpriseDataProtection</NodeName>
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
                <NodeName>RetrieveByTimeRange</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>A time range is supported by setting a start and stop time in ISO 8601 format.  If the start/stop value is not preset and a GetValue is called to RetrieveByTimeRange then the missing values will be interpreted as either the first existing or the last existing. For example, not setting a start date and setting an end date will return all known logs that exist before the end date. Setting a start date but not an end date will return all the logs that exist from the start date. Not setting a start and end date will return all logs.</Description>
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
                    <NodeName>Logs</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                        </AccessType>
                        <DFFormat>
                            <xml />
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
                    <NodeName>StartTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
                    <NodeName>StopTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
                <NodeName>RetrieveByCount</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>The count range will return the configured number of logs starting from the StartTime value.  The start time is expressed in ISO8601 formt. The caller will configure the number of desired logs by calling set on the LogCount and StartTime, then retrieve the logs by calling get on Logs node. The call will return the number of desired logs or less if the total number of logs are less than the desired number of logs. The logs are returned from StartTime forward.</Description>
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
                    <NodeName>Logs</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                        </AccessType>
                        <DFFormat>
                            <xml />
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
                    <NodeName>LogCount</NodeName>
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
                    <NodeName>StartTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
        </Node>
        <Node>
            <NodeName>SecurityAuditing</NodeName>
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
                <NodeName>RetrieveByTimeRange</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>A time range is supported by setting a start and stop time in ISO 8601 format.  If the start/stop value is not preset and a GetValue is called to RetrieveByTimeRange then the missing values will be interpreted as either the first existing or the last existing. For example, not setting a start date and setting an end date will return all known logs that exist before the end date. Setting a start date but not an end date will return all the logs that exist from the start date. Not setting a start and end date will return all logs.</Description>
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
                    <NodeName>Logs</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                        </AccessType>
                        <DFFormat>
                            <xml />
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
                    <NodeName>StartTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
                    <NodeName>StopTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
                <NodeName>RetrieveByCount</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>The count range will return the configured number of logs starting from the StartTime value.  The start time is expressed in ISO8601 formt. The caller will configure the number of desired logs by calling set on the LogCount and StartTime, then retrieve the logs by calling get on Logs node. The call will return the number of desired logs or less if the total number of logs are less than the desired number of logs. The logs are returned from StartTime forward.</Description>
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
                    <NodeName>Logs</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                        </AccessType>
                        <DFFormat>
                            <xml />
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
                    <NodeName>LogCount</NodeName>
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
                    <NodeName>StartTime</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>Use ISO 8601 format.</Description>
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
        </Node>
    </Node>
</MgmtTree>
```

 

 






