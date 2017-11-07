---
author: kpacquer
Description: "Wenn Sie Modus Manufacturing testen möchten, können Sie es mithilfe der ffutool.exe oder mithilfe einer Einstellung BCD aktivieren."
ms.assetid: a5506896-0692-4256-a307-075da141ad44
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktivieren oder Deaktivieren von Manufacturing Modus
ms.openlocfilehash: 174e0af1d93a728e7789f2c2a11e1c52aa552e23
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-or-disable-manufacturing-mode"></a>Aktivieren oder Deaktivieren von Manufacturing Modus


Wenn Sie Manufacturing Modus testen möchten, können Sie es mithilfe der ffutool.exe oder mithilfe einer Einstellung BCD aktivieren.

**Hinweis**  Die empfohlene Vorgehensweise zur Unterstützung von Fertigung Modus auf Geräten ausgeliefert ist haben die Firmware-Unterstützung der Boot Modus Management UEFI-Protokoll. Weitere Informationen über dieses Protokoll finden Sie unter [Boot Modus Management UEFI-Protokoll](boot-mode-management-uefi-protocol.md).

 

## <a name="span-idenableordisablemanufacturingmodewithffutoolexespanspan-idenableordisablemanufacturingmodewithffutoolexespanenable-or-disable-manufacturing-mode-with-ffutoolexe"></a><span id="enable_or_disable_manufacturing_mode_with_ffutool.exe"></span><span id="ENABLE_OR_DISABLE_MANUFACTURING_MODE_WITH_FFUTOOL.EXE"></span>Aktivieren oder Deaktivieren von Manufacturing Modus mit ffutool.exe


Wenn das Gerät den Startmodus UEFI Protokoll unterstützt, können Sie aktivieren oder Deaktivieren von Manufacturing Modus mit ffutool.exe mithilfe des Parameters **SetBootMode** . Die Syntax lautet wie folgt:

``` syntax
ffutool.exe -setBootMode <boot mode> <profile name>
```

-   *Startmodus* – eine ganze Zahl, die den Startmodus entspricht, in dokumentiert [EFI\_BOOT\_MODUS\_INFO Enumeration](efi-boot-mode-info-enumeration.md).
-   *Name der Benutzerprofildienst* – der Name des Profils Manufacturing zu aktivieren. Dies ist erforderlich, wenn der Startmodus auf 1 festgelegt ist, und wird ignoriert, wenn der Startmodus auf 0 festgelegt ist.

Das folgende Beispiel Fertigung Modus aktiviert und ein Fertigung Profil mit dem Namen CustomProfile verwendet:

``` syntax
ffutool.exe -setBootMode 1 CustomProfile
```

Das folgende Beispiel deaktiviert Manufacturing Schreibmodus und ermöglicht das Betriebssystem ordnungsgemäß gestartet werden:

``` syntax
ffutool.exe -setBootMode 0
```

## <a name="span-idenablemanufacturingmodewithabcdsettingspanspan-idenablemanufacturingmodewithabcdsettingspanspan-idenablemanufacturingmodewithabcdsettingspanenable-manufacturing-mode-with-a-bcd-setting"></a><span id="Enable_Manufacturing_Mode_with_a_BCD_setting"></span><span id="enable_manufacturing_mode_with_a_bcd_setting"></span><span id="ENABLE_MANUFACTURING_MODE_WITH_A_BCD_SETTING"></span>Mit der Einstellung BCD Manufacturing-Modus aktivieren


Die Einstellung MfgMode BCD können Testmodus Fertigung Ihre benutzerdefinierte Manufacturing Profile. MfgMode ist ein Zeichenfolgenwert, der auf den Namen Ihres Profils benutzerdefinierte Fertigung festgelegt ist.

Beispielsweise können Sie das Gerät in der Fertigung Modus mithilfe des standardmäßigen manufacturing Profil mithilfe des folgenden Befehls auf dem Gerät beginnen:

``` syntax
bcdedit.exe /set {default} mfgmode "default"
```

Oder Sie können das Gerät beginnen, in der Fertigung-Modus unter Verwendung einer benutzerdefinierten Fertigung Profil mit dem Namen, CustomProfile, die folgenden Schritte durch:

``` syntax
bcdedit.exe /set {default} mfgmode "CustomProfile"
```

Sie können auch es auf einem Gerät offline aktivieren, die angeschlossen ist und befindet sich im Modus für USB-Massenspeichergerät. Beispiel:

``` syntax
bcdedit.exe /store "D:\EFIESP\efi\Microsoft\Boot\BCD" /set {default} mfgmode "default"
```

**Hinweis**  Wenn Sie eine ältere Version von bcdedit.exe verwenden, müssen Sie möglicherweise eine **benutzerdefinierte: 22000140** anstelle von **Mfgmode** als der Einstellungsname BCD verwenden.

 

## <a name="span-idcreateamanufacturingmodebcdpackagespanspan-idcreateamanufacturingmodebcdpackagespanspan-idcreateamanufacturingmodebcdpackagespancreate-a-manufacturing-mode-bcd-package"></a><span id="Create_a_Manufacturing_Mode_BCD_package"></span><span id="create_a_manufacturing_mode_bcd_package"></span><span id="CREATE_A_MANUFACTURING_MODE_BCD_PACKAGE"></span>Erstellen eines Pakets Manufacturing Modus BCD


Sie können ein Paket erstellen, die den Eintrag MfgMode BCD erstellt und platziert es in Ihrem benutzerdefinierten Fertigung Profil. Zu diesem Zweck müssen Sie zunächst eine XML-Datei erstellen, die den Eintrag BCD verweist:

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<BootConfigurationDatabase xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/phone/2011/10/BootConfiguration">
  <Objects>

    <!-- Global Settings Group -->
    <Object SaveKeyToRegistry="false">
      <FriendlyName>Windows Loader</FriendlyName>
      <Elements>

        <Element>
          <DataType>
            <WellKnownType>Manufacturing Mode</WellKnownType>
          </DataType>
          <ValueType>
            <StringValue>Default</StringValue>
          </ValueType>
        </Element>

      </Elements>
    </Object>

  </Objects>
</BootConfigurationDatabase>
```

Nachdem erstellt wird, können Sie es in einer XML-Paketdatei verweisen:

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="ManufacturingModeBcd"
        ReleaseType="Production"
        Partition="EFIESP"
        OwnerType="OEM">

    <Components>
        <BCDStore Source=".\exampleBcd.bcd.xml"/>
    </Components>
</Package>
```

**Hinweis**  Ist eine Partition-Attribut definieren, dass diese BCD-Einträge für die Partition EFIESP gelten müssen. Dies sollte der Partition sein befindet, in dem der BCD-Speicher für Ihr Gerät aktualisiert werden. Dies unterscheidet sich von der Partition, in dem das Hauptfenster Betriebssystem befindet, können nicht anderer Vorgänge, beispielsweise das Hinzufügen von Dateien und Registrierungsschlüssel auf die wichtigsten Betriebssystempartition aus dem gleichen Paket erfolgen.

 

Um das Paket zu erstellen, können Sie pkggen.exe (im Lieferumfang von Windows-Treiberkits enthalten):

``` syntax
pkggen.exe exampleBcd.pkg.xml /config:pkggen.cfg.xml
```

 

 





