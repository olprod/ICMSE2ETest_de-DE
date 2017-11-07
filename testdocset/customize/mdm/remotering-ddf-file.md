---
title: RemoteRing DDF-Datei
description: "In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für RemoteRing-Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6815267F-212B-4370-8B72-A457E8000F7B
ms.openlocfilehash: 7dd5d64fafb376b5973ea2cb1828eca7fe6c453e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotering-ddf-file"></a>RemoteRing DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den Dienstanbieter für **RemoteRing** -Konfiguration. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>RemoteRing</NodeName>
        <Path>./User/Vendor/MSFT</Path>
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
          <NodeName>Ring</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <Description>Required. The node accepts requests to ring the device. The supported operation is Exec</Description>
            <DFFormat>
              <null />
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
        <NodeName>Root</NodeName>
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
      </Node>
</MgmtTree>
```

 

 






