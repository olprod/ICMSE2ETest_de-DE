---
title: CMPolicyEnterprise DDF-Datei
description: CMPolicyEnterprise DDF-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 065EF07A-0CF3-4EE5-B620-3464A75B7EED
ms.openlocfilehash: 34259bbe29d14cdfa77eac4b46b9b6685f5d9dc5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cmpolicyenterprise-ddf-file"></a>CMPolicyEnterprise DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **CMPolicyEnterprise** -Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>CMPolicyEnterprise</NodeName>
        <!-- NOTE: from here below, CMPolicy and CMPolicyEnterprise should be identical -->
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
            <MIME>com.microsoft/1.0/MDM/CMPolicyEnterprise</MIME>
          </DFType>
        </DFProperties>
        <Node>
          <NodeName></NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Delete />
              <Get />
            </AccessType>
            <Description>The name of the policy</Description>
            <DFFormat>
              <node />
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
            <DFTitle>PolicyName</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>SID</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <Description>The value of SID depends on the ClienType</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>SID</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>ClientType</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <Description>Specifies the mapping policy type</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>ClientType</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>Host</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <Description>Specifies the name of a host pattern</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Host</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>OrderedConnections</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <Description>Specifies whether the list of connections is in preference order</Description>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>OrderedConnection</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>Connections</NodeName>
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
              <DFTitle>Connections</DFTitle>
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
                </AccessType>
                <Description>Connection associated with the policy</Description>
                <DFFormat>
                  <node />
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
                <DFTitle>ConnXXX</DFTitle>
                <DFType>
                  <DDFName></DDFName>
                </DFType>
              </DFProperties>
              <Node>
                <NodeName>ConnectionID</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <Description>A unique identifier for a connection within a group of connections</Description>
                  <DFFormat>
                    <chr />
                  </DFFormat>
                  <Occurrence>
                    <ZeroOrOne />
                  </Occurrence>
                  <Scope>
                    <Dynamic />
                  </Scope>
                  <CaseSense>
                    <CIS />
                  </CaseSense>
                  <DFTitle>ConnectionID</DFTitle>
                  <DFType>
                    <MIME>text/plain</MIME>
                  </DFType>
                </DFProperties>
              </Node>
              <Node>
                <NodeName>Type</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <Description>The type of connection being referenced</Description>
                  <DFFormat>
                    <chr />
                  </DFFormat>
                  <Occurrence>
                    <ZeroOrOne />
                  </Occurrence>
                  <Scope>
                    <Dynamic />
                  </Scope>
                  <CaseSense>
                    <CIS />
                  </CaseSense>
                  <DFTitle>Type</DFTitle>
                  <DFType>
                    <MIME>text/plain</MIME>
                  </DFType>
                </DFProperties>
              </Node>
            </Node>
          </Node>
        </Node>
      </Node>
</MgmtTree>
```

## <a name="related-topics"></a>Verwandte Themen


[CMPolicyEnterprise Konfiguration-Dienstanbieter](cmpolicyenterprise-csp.md)

 

 






