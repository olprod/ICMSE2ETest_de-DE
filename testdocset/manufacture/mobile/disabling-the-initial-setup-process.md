---
author: kpacquer
Description: "Deaktivieren des anfänglichen Setup-Prozess"
ms.assetid: e0aa36a7-5524-42de-855d-1a9b7e03e250
MSHAttr: PreferredLib:/library/windows/hardware
title: "Deaktivieren den ursprünglichen Setup-Vorgang"
ms.openlocfilehash: b94974de01d6072b3aaa5d1039f531f7373c9176
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disabling-the-initial-setup-process"></a>Deaktivieren den ursprünglichen Setup-Vorgang


Um das Gerät ersteinrichtung Prozess (manchmal auch als die *Out-of-Box-Experience* oder *OOBE*bezeichnet) in einem Test, Status oder die Produktion Abbild deaktivieren, die während der Fertigung verwendet wird, die SKIPOOBE-imaging-Funktion enthält, in der OEMnput.xml-Datei, die verwendet wird, um das Bild zu erstellen.

Das Feature SKIPOOBE setzt den Registrierungswert **OobeHeadless** (einem REG\_DWORD-Wert unter der HKEY\_LOKALE\_COMPUTER\\Software\\Microsoft\\Shell\\Eintrag OOBE) 1. Alternativ können Sie diesen Registrierungswert direkt in einem eigenen Pakete konfigurieren. Im folgenden Beispiel wird eine Paket-XML-Datei, die diesen Registrierungswert festlegt.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  Owner="Contoso"
  Component="Shell"
  SubComponent="DisableOOBE"
  OwnerType="OEM"
  ReleaseType="Production" xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00">

  <Macros>
    <Macro Id="hklm.shell" Value="$(hklm.microsoft)\Shell"/>
  </Macros>

  <Components>
    <OSComponent>
      <RegKeys>
        <RegKey KeyName="$(hklm.shell)\OOBE">
          <RegValue Name="OobeHeadless" Type="REG_DWORD" Value="00000001" />
        </RegKey>
      </RegKeys>
    </OSComponent>
  </Components>
</Package>
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Angeben von Dateien und Registrierungseinträge in einer Project-Paketdatei](https://msdn.microsoft.com/library/dn789219)

 

 






