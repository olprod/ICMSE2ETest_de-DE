---
author: Justinha
Description: "Verwenden Sie DISM zum Arbeiten mit Dateien Provisioning-Pakete (.ppkg). Beispielsweise können Sie Einstellungen und Windows-desktopanwendungen auf Windows 10 hinzufügen oder verringern Sie die Größe der Windows-Installation."
ms.assetid: 205d296e-fced-429a-9e74-c445743ed7e9
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Provisioning Befehlszeilenoptionen Paket (.ppkg)
ms.openlocfilehash: 33ae13d4232b9ef4a1242d0522302fa1f2330039
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-iddismprovisioningpackagecommand-lineoptionsspandism-provisioning-package-ppkg-command-line-options"></a><span id="dism_provisioning_package_command-line_options"></span>DISM Provisioning Befehlszeilenoptionen Paket (.ppkg)


Verwenden Sie DISM zum Arbeiten mit Dateien Provisioning-Pakete (.ppkg). Beispielsweise können Sie Einstellungen und Windows-desktopanwendungen auf Windows 10 hinzufügen oder verringern Sie die Größe der Windows-Installation.

## <a name="span-idadd-provisioningpackagespanspan-idadd-provisioningpackagespanspan-idadd-provisioningpackagespanadd-provisioningpackage"></a><span id="_Add-ProvisioningPackage"></span><span id="_add-provisioningpackage"></span><span id="_ADD-PROVISIONINGPACKAGE"></span>**/ Add-ProvisioningPackage**

Fügt zutreffend Nutzlast provisioning-Paket für das angegebene Bild hinzu.

Syntax:

``` syntax
DISM.exe /Add-ProvisioningPackage /PackagePath:<package_path> [/CatalogPath:<path>]
```

Beispiel:

``` syntax
DISM.exe /Image=C:\ /Add-ProvisioningPackage /PackagePath:C:\oem.ppkg
```

## <a name="span-idget-provisioningpackageinfospanspan-idget-provisioningpackageinfospanspan-idget-provisioningpackageinfospanget-provisioningpackageinfo"></a><span id="_Get-ProvisioningPackageInfo"></span><span id="_get-provisioningpackageinfo"></span><span id="_GET-PROVISIONINGPACKAGEINFO"></span>**/ Get-ProvisioningPackageInfo**

Rufen Sie die Informationen des Paket-Bereitstellung an.

Syntax:

``` syntax
DISM.exe /Get-ProvisioningPackageInfo /PackagePath:<package_path>
```

Beispiel:

``` syntax
DISM.exe /Image=C:\ /Get-ProvisioningPackageInfo /PackagePath:C:\oem.ppkg
```

## <a name="span-idapply-customdataimagespanspan-idapply-customdataimagespanspan-idapply-customdataimagespanapply-customdataimage"></a><span id="_Apply-CustomDataImage"></span><span id="_apply-customdataimage"></span><span id="_APPLY-CUSTOMDATAIMAGE"></span>**/ Anwenden-CustomDataImage**

Pausieren Dateien in das Bild benutzerdefinierte Daten, um Speicherplatz einzusparen. Dieses Paket wird für Clienteditionen von die Drucktaste Wiederherstellungstools verwendet.

Syntax:

``` syntax
/Apply-CustomDataImage /CustomDataImage:<path_to_image_file> /ImagePath:<target_drive> /SingleInstance
```


|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
|   / CustomDataImage | Gibt an, in dem das provisioning-Paket gespeichert ist. |
| / Image | Gibt das Laufwerk, das Windows-Abbild enthält. DISM scannt dieses Laufwerk für alle nicht-Systemdateien auf dem Laufwerk und die Bereitstellung Paket integriert. |
| / SingleInstance | Nach DISM die kein Systemlaufwerk-Dateien in einem komprimierten provisioning Paket erfasst, DISM Zeiger auf dem Laufwerk in das neue komprimierte provisioning Paket hinzugefügt und entfernt die ursprünglichen Dateien. Daher die Dateien bleiben jedoch weiterhin an das System aber weniger Speicherplatz auf dem Laufwerk.|


Beispiel:

``` syntax
DISM.exe /Apply-CustomDataImage /CustomDataImage:C:\oem.ppkg /ImagePath:C:\ /SingleInstance
```

Betrifft: Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) nur.

 