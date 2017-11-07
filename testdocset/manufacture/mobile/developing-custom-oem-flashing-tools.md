---
author: kpacquer
Description: Entwickeln von benutzerdefinierten OEM Tools blinken
ms.assetid: 121f6c72-5d87-4391-9b40-dbd89e57a826
MSHAttr: PreferredLib:/library/windows/hardware
title: Entwickeln von benutzerdefinierten OEM Tools blinken
ms.openlocfilehash: d5c918faf47939ba840ab07a850be4f9af4d9c83
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="developing-custom-oem-flashing-tools"></a>Entwickeln von benutzerdefinierten OEM Tools blinken


OEMs können die vollständige flash-Update (FFU) Bildformat und einfache UEFI USB-Protokolle verwenden, um benutzerdefinierte blinkende Tools erstellen. Ein benutzerdefiniertes blinkendes OEM-Tool kann Integration mit vorhandenen Systemen und einen Zellbereich in [blinkendes Tools](flashing-tools.md)beschriebenen Szenarien unterstützen.

## <a name="span-iduefiflashingapplicationspanspan-iduefiflashingapplicationspanspan-iduefiflashingapplicationspanuefi-flashing-application"></a><span id="UEFI_flashing_application"></span><span id="uefi_flashing_application"></span><span id="UEFI_FLASHING_APPLICATION"></span>Blinkende UEFI-Anwendung


Der OEM muss flash das Gerät aus einer UEFI-Anwendung, die mit einem bestimmten Bildlayout, die in [FFU Bildformat](ffu-image-format.md)erläutert wird.

Dieses Diagramm werden den Kommunikationsfluss vom PC blinkende Tool auf das Gerät mit dem UEFI einfache Windows Phone-e/a-Protokoll zusammengefasst.

![OEM\-zu\-Simpleio](images/oem-manu-simpleio.png)

Weitere Informationen zu verfügbaren USB-APIs finden Sie unter [UEFI blinkendes Protokolle](https://msdn.microsoft.com/windows/hardware/dn917884.aspx).

## <a name="span-idpcflashingapplicationspanspan-idpcflashingapplicationspanspan-idpcflashingapplicationspanpc-flashing-application"></a><span id="PC_flashing_application"></span><span id="pc_flashing_application"></span><span id="PC_FLASHING_APPLICATION"></span>Blinkende PC-Anwendung


Das Bild wird an das Gerät weitergeleitet, die die blinkende UEFI-Anwendung mit einem einfachen PC Seite Client-Programm ausgeführt wird. PC-Anwendung wird eine USB-Verbindung mit dem Gerät und schreibt die Daten über diese Verbindung. Die Überprüfung und Überprüfung des Bilds tritt auf, in der blinkende UEFI-Anwendung auf dem Gerät ausgeführt.

Im folgende Diagramm sind die OEM benutzerdefinierte blinkende PC Anwendung und die Anwendung UEFI den Projektfluss zusammengefasst.

![OEM\-zu\-pc\-blinken](images/oem-manu-pc-flashing.png)

**Hinweis**  
Dieses Diagramm veranschaulicht eine mögliche Lösung. OEM wird empfohlen, um diese Vorgehensweise zum Erstellen einer optimalen Lösung, die am besten geeigneten zu ändern.

 

## <a name="span-idcheckingsmbiosvaluesbeforeflashingspanspan-idcheckingsmbiosvaluesbeforeflashingspanspan-idcheckingsmbiosvaluesbeforeflashingspanchecking-smbios-values-before-flashing"></a><span id="Checking_SMBIOS_values_before_flashing"></span><span id="checking_smbios_values_before_flashing"></span><span id="CHECKING_SMBIOS_VALUES_BEFORE_FLASHING"></span>Überprüfen von SMBIOS Werten vor blinken


Um sicherzustellen, dass das richtige Bild auf das richtige Gerät aktualisiert wird, muss OEM SMBIOS System Informationen Strukturwerte auf dem Gerät überprüfen. Das Kontrollkästchen muss Vergewissern Sie sich, dass die Geräte-Plattform ID-Werte in der Abbildung SMBIOS System Informationen Strukturwerte auf dem Telefon übereinstimmt. Manufacturer.Family.ProductName.Version oder Manufacturer.Family.ProductName von SMBIOS muss den Wert in das Bild übereinstimmen, bevor blinken fortfahren kann.

Nachfolgend finden Sie die Gerät Plattform ID-Zeichenfolge.

**Manufacturer.Family.ProductName.Version**

### <a name="span-idengineeringdevicesandblankdeviceidsspanspan-idengineeringdevicesandblankdeviceidsspanspan-idengineeringdevicesandblankdeviceidsspanengineering-devices-and-blank-device-ids"></a><span id="Engineering_devices_and_blank_device_IDs"></span><span id="engineering_devices_and_blank_device_ids"></span><span id="ENGINEERING_DEVICES_AND_BLANK_DEVICE_IDS"></span>Engineering-Geräte und leere Geräte-IDs

Mit einem neuen engineering-Gerät können OEM SMBIOS Werte zu ermitteln, ob ein Bild blinkt, die Test enthält akzeptabel ist signierte Zertifikate. OEM kann bestimmen, dass der Test signierten Bilder möglicherweise leer System Informationen Strukturwerte aufweisen, in dem signierte Produktion Bilder benötigen SMBIOS System Informationen Strukturwerte, die aufgefüllt wurden.

## <a name="span-idimplementingsignedimagevalidationspanspan-idimplementingsignedimagevalidationspanspan-idimplementingsignedimagevalidationspanimplementing-signed-image-validation"></a><span id="Implementing_signed_image_validation"></span><span id="implementing_signed_image_validation"></span><span id="IMPLEMENTING_SIGNED_IMAGE_VALIDATION"></span>Implementieren von signierten Bild Validierung


FFU Bilder enthalten Elemente wie Hashes, Signaturen und Katalogen, die verwendet werden müssen, um das Bild zu überprüfen. Weitere Informationen finden Sie unter [Implementing Bild Integrität Validierung in benutzerdefinierten blinkende Tools](implementing-image-integrity-validation-in-custom-flashing-tools.md).

## <a name="span-iduefiflashingprotocolsspanspan-iduefiflashingprotocolsspanspan-iduefiflashingprotocolsspanuefi-flashing-protocols"></a><span id="UEFI_flashing_protocols"></span><span id="uefi_flashing_protocols"></span><span id="UEFI_FLASHING_PROTOCOLS"></span>Blinkende UEFI-Protokolle


<span id="UEFI_USB_function_protocol"></span><span id="uefi_usb_function_protocol"></span><span id="UEFI_USB_FUNCTION_PROTOCOL"></span>[Protokoll für UEFI USB-Funktion](https://msdn.microsoft.com/library/windows/hardware/dn789231)  
Beschreibt die **EFI\_USBFN\_e/a\_PROTOKOLL**.

<span id="UEFI_simple_I_O_protocol"></span><span id="uefi_simple_i_o_protocol"></span><span id="UEFI_SIMPLE_I_O_PROTOCOL"></span>[UEFI SMTP-e/a](https://msdn.microsoft.com/library/windows/hardware/dn772121)  
Beschreibt die **EFI\_EINFACHE\_WINPHONE\_e/a\_PROTOKOLL**.

<span id="UEFI_check_signature_protocol"></span><span id="uefi_check_signature_protocol"></span><span id="UEFI_CHECK_SIGNATURE_PROTOCOL"></span>[UEFI Kontrollkästchen Signatur Protokoll](https://msdn.microsoft.com/library/windows/hardware/dn772115)  
Beschreibt die **EFI\_CHECKSIG\_PROTOKOLL**.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Blinken tools](flashing-tools.md)

[Fertigung](index.md)

 

 






