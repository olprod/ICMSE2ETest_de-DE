---
author: Justinha
Description: "Windows PE: Hinzufügen von Windows PowerShell-Unterstützung zu Windows PE"
ms.assetid: 8b653cf6-3584-4c80-be84-ca32d60aeba2
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows PE: Hinzufügen von Windows PowerShell-Unterstützung zu Windows PE"
ms.openlocfilehash: 28bdc32f0ed7b4fe614d292014263709d2058a6c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-adding-windows-powershell-support-to-windows-pe"></a>Windows PE: Hinzufügen von Windows PowerShell-Unterstützung zu Windows PE


Das folgenden Beispielskript erstellt eine Version von Windows PE mit Windows PowerShell und die zugehörigen Cmdlets DISM und Speicher, die zum Automatisieren der Bereitstellung von Windows verwendet werden kann.

**Vorbereiten einer lokalen Kopie des Windows PE-Dateien**

1.  Installieren Sie [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkID=526803), die **Bereitstellungstools** und **Windows PE** Features hinzufügen.

2.  Starten Sie **Bereitstellung und Imaging Tools Umgebung** als **Administrator**an.

3.  Erstellen Sie eine Arbeitskopie von Windows PE-Dateien. Geben Sie entweder X86, amd64 oder arm:

    ``` syntax
    copype amd64 C:\WinPE_amd64_PS
    ```

## <a name="span-idsamplescriptspanspan-idsamplescriptspanspan-idsamplescriptspansample-script"></a><span id="SampleScript"></span><span id="samplescript"></span><span id="SAMPLESCRIPT"></span>Beispielskript


Verwenden Sie das folgende Skript, stellen Sie das Windows-Abbild, fügen Sie die optionalen Windows PE-Komponenten für Windows PowerShell sowie zur Bereitstellung des Abbilds aufheben.

``` syntax
Dism /Mount-Image /ImageFile:"C:\WinPE_amd64_PS\media\sources\boot.wim" /Index:1 /MountDir:"C:\WinPE_amd64_PS\mount"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-WMI.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-NetFX.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-NetFX_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Scripting.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-PowerShell.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-PowerShell_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-StorageWMI.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-StorageWMI_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-DismCmdlets.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-DismCmdlets_en-us.cab"

Dism /Unmount-Image /MountDir:C:\WinPE_amd64_PS\mount /Commit
```

## <a name="span-idinstallthisversionofwindowspetoausbkeyspanspan-idinstallthisversionofwindowspetoausbkeyspanspan-idinstallthisversionofwindowspetoausbkeyspaninstall-this-version-of-windows-pe-to-a-usb-key"></a><span id="Install_this_version_of_Windows_PE_to_a_USB_key"></span><span id="install_this_version_of_windows_pe_to_a_usb_key"></span><span id="INSTALL_THIS_VERSION_OF_WINDOWS_PE_TO_A_USB_KEY"></span>Installieren Sie diese Version von Windows PE auf einem USB-Schlüssel


``` syntax
MakeWinPEMedia /UFD C:\WinPE_amd64_PS F:
```

## <a name="span-idstartwindowspowershellinwindowspespanspan-idstartwindowspowershellinwindowspespanspan-idstartwindowspowershellinwindowspespanstart-windows-powershell-in-windows-pe"></a><span id="Start_Windows_PowerShell_in_Windows_PE"></span><span id="start_windows_powershell_in_windows_pe"></span><span id="START_WINDOWS_POWERSHELL_IN_WINDOWS_PE"></span>Starten Sie Windows PowerShell in Windows PE


Nachdem Sie einen PC USB-Schlüssel mit Windows PE starten, starten Sie Windows PowerShell:

``` syntax
X:\Windows\system32\WindowsPowerShell\v1.0\powershell
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)](winpe-add-packages--optional-components-reference.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Erstellen einer Boot-CD, DVD, ISO oder virtuelle Festplatte](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

 

 






