---
title: RemoteLock DDF-Datei
description: RemoteLock DDF-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A301AE26-1BF1-4328-99AB-1ABBA4960797
ms.openlocfilehash: 34d86c7bd44c8e79eb7bccc79f2b9640b8159713
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotelock-ddf-file"></a>RemoteLock DDF-Datei


In diesem Thema wird das OMA DM Gerät Beschreibung Framework (DDF) für den **RemoteLock** Konfigurationsdienstanbieter. DDF-Dateien werden nur mit OMA DM Bereitstellung von XML verwendet.

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC "-//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [
  <?oma-dm-ddf-ver supported-versions="1.2"?>
]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
  <Node>
    <NodeName>RemoteLock</NodeName>
    <Path>./Vendor/MSFT</Path>
    <DFProperties>
      <AccessType />
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
      <NodeName>Lock</NodeName>
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
        <DFType>
          <MIME>text/plain</MIME>
        </DFType>
      </DFProperties>
    </Node>
    <Node>
      <NodeName>LockAndResetPIN</NodeName>
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
        <DFType>
          <MIME>text/plain</MIME>
        </DFType>
      </DFProperties>
    </Node>
    <Node>
      <NodeName>NewPINValue</NodeName>
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
  </Node>
</MgmtTree>
```

## <a name="related-topics"></a>Verwandte Themen


[RemoteLock Konfiguration-Dienstanbieter](remotelock-csp.md)

 

 






