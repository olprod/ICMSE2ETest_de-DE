---
title: DeviceLock DDF-Datei
description: DeviceLock DDF-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 46a691b9-6350-4987-bfc7-f8b1eece3ad9
ms.openlocfilehash: 42bfa6fc87f986db525f7babec7a485cccda780e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicelock-ddf-file"></a>DeviceLock DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **DeviceLock** -Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC "-//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree>
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>DeviceLock</NodeName>
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
                <DDFName>com.microsoft/1.0/WindowsPhone/DeviceLock </DDFName>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>Provider</NodeName>
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
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Add />
                        <Get />
                        <Delete />
                    </AccessType>
                    <DFFormat>
                        <node />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <DFType>
                        <DDFName></DDFName>
                    </DFType>
                </DFProperties>
                <Node>
                  <NodeName>DevicePasswordEnabled</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>1</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
                </Node>
                <Node>
                  <NodeName>AllowSimpleDevicePassword</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>1</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
               </Node>
               <Node>
                  <NodeName>MinDevicePasswordLength</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>4</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
              </Node>
              <Node>
                  <NodeName>AlphanumericDevicePasswordRequired</NodeName>
                  <DFProperties>
                      <AccessType>
                        <Add />
                        <Get />
                        <Replace />
                      </AccessType>
                      <DefaultValue>2</DefaultValue>
                      <DFFormat>
                        <int />
                      </DFFormat>
                      <Occurrence>
                        <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                        <Dynamic />
                      </Scope>
                      <DFType>
                        <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
              </Node>
              <Node>
                  <NodeName>DevicePasswordExpiration</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>0</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
              </Node>
              <Node>
                  <NodeName>DevicePasswordHistory</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>0</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
             </Node>
             <Node>
                  <NodeName>MaxDevicePasswordFailedAttempts</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>0</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
             </Node>
             <Node>
                  <NodeName>MaxInactivityTimeDeviceLock</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>0</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
             </Node>
             <Node>
                  <NodeName>MinDevicePasswordComplexCharacters</NodeName>
                  <DFProperties>
                      <AccessType>
                          <Add />
                          <Get />
                          <Replace />
                      </AccessType>
                      <DefaultValue>1</DefaultValue>
                      <DFFormat>
                          <int />
                      </DFFormat>
                      <Occurrence>
                          <ZeroOrOne />
                      </Occurrence>
                      <Scope>
                          <Dynamic />
                      </Scope>
                      <DFType>
                          <MIME>text/plain</MIME>
                      </DFType>
                  </DFProperties>
             </Node>
         </Node>
      </Node>
      <Node>
            <NodeName>DeviceValue</NodeName>
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
                <NodeName>DevicePasswordEnabled</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>AllowSimpleDevicePassword</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>MinDevicePasswordLength</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>AlphanumericDevicePasswordRequired</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>DevicePasswordExpiration</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>DevicePasswordHistory</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>MaxDevicePasswordFailedAttempts</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>MaxInactivityTimeDeviceLock</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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
                <NodeName>MinDevicePasswordComplexCharacters</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <DFFormat>
                        <int />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrOne />
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

## <a name="related-topics"></a>Verwandte Themen


[DeviceLock Konfigurationsdienstanbieter](devicelock-csp.md)

 

 






