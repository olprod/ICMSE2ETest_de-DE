---
author: Justinha
Description: 'Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)'
ms.assetid: f4495adf-63db-4fdc-ae56-70166eed930c
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)'
ms.openlocfilehash: 74fd03850a62fd1e9ab40f218f8e317bb017926d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-install-on-a-hard-drive-flat-boot-or-non-ram"></a>Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)


Windows-Vorinstallation Environment (Windows PE) ist ein minimales Betriebssystem, auf dem Sie für die Installation, Bereitstellung und Wartung von Windows einen PC vorbereiten. Nachfolgend finden Sie zum Herunterladen und installieren es auf einer internen oder externen Festplatte.

Diese Anleitung wird gezeigt, wie eine Standardinstallation von Windows PE einrichten, die vom Laufwerk ausgeführt wird. Dies manchmal erhalten Sie eine bessere Leistung als das Starten aus dem Speicher und helfen Ihnen bei Windows PE auf PCs oder virtuellen Umgebungen mit wenig Arbeitsspeicher ausgeführt werden. Dieses Verfahren ist auch bekannt als ein *nicht-RAMDISK-Start*oder einer *flachen Boot*.

**Hinweis**  
Wenn vom Laufwerk mit Windows PE ausgeführt wird, müssen Sie den PC deaktivieren, vor dem Trennen des Laufwerks, um Datenverlust zu vermeiden.

 
## <a name="span-idinstallthewindowsadkspan-install-the-windows-adk"></a><span id="Install_the_Windows_ADK"></span>Installieren von Windows ADK

-   Rufen Sie das [Windows Assessment and Deployment Kit (Windows ADK) technische Referenz](http://go.microsoft.com/fwlink/p/?LinkId=526803), einschließlich des Windows PE-Features.

**Erstellen einer Gruppe von entweder 32-Bit oder 64-Bit-Windows PE-Dateien**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Kopieren Sie in der **Bereitstellung und Imaging Tools Environment**Windows PE-Dateien für die PCs Sie starten möchten.

    Die 64-Bit-Version von Windows PE kann UEFI 64-Bit- und 64-Bit-BIOS PCs starten:

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

    Die 32-Bit-Version von Windows PE kann UEFI 32-Bit, BIOS-32-Bit- und 64-Bit-BIOS PCs starten:

    ``` syntax
    copype x86 C:\WinPE_x86
    ```

## <a name="span-idcreateaworkingdirectoryspan-create-a-working-directory-for-windows-pe-files"></a><span id="Create_a_Working_Directory"></span>Erstellen Sie eine funktionsfähige Verzeichnis für Windows PE-Dateien

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Erstellen Sie über die **Bereitstellung und Imaging Tools Umgebung**einem Arbeitsverzeichnis für Windows PE-Dateien.

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

## <a name="span-idinstallwindowspespan-install-windows-pe-to-the-media"></a><span id="Install_Windows_PE"></span>Installieren von Windows PE auf den Datenträger

1.  Verwenden Sie DiskPart, um die Partitionen vorzubereiten.

    **Hinweis**  
    Die folgenden Befehle vorbereiten eine USB-Festplatte, die gestartet werden kann auf einem BIOS-basierten oder UEFI-basierten PC.

    Auf UEFI-basierten PCs erfordert Windows PE FAT32 File Format formatierte, die einzige Datei unterstützt bis zu 4 GB Größe eine Boot-Partition. Es wird empfohlen, das Erstellen einer separaten Partition auf dem Laufwerk, mit NTFS, formatiert, sodass Windows Bilder und anderen großen Dateien gespeichert werden können. Weitere Informationen finden Sie unter [Windows PE: Identifizieren Laufwerkbuchstaben mit einem Skript](winpe-identify-drive-letters.md). 

    ``` syntax
    diskpart
    list disk
    select <disk number>
    clean
    rem === Create the Windows PE partition. ===
    create partition primary size=2000
    format quick fs=fat32 label="Windows PE"
    assign letter=P
    active
    rem === Create a partition for images ===
    create partition primary
    format fs=ntfs quick label="Images"
    assign letter=I
    list vol
    exit
    ```

    wobei * &lt;Anzahl Datenträger&gt; * ist die aufgelistete Anzahl von externen USB-Festplatte.

2.  Wenden Sie das Windows PE-Abbild auf der Festplatte.

    ``` syntax
    dism /Apply-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /Index:1 /ApplyDir:P:\
    ```

3.  Richten Sie die Startdateien.

    ``` syntax
    BCDboot P:\Windows /s P: /f ALL
    ```

    **Hinweis**  
    Ignorieren Sie alle Warnhinweise, die sagen Sie "Warnung: Fortsetzen der Anwendung nicht gefunden."

     

## <a name="span-idboottowindowspespan-boot-to-windows-pe"></a><span id="Boot_to_Windows_PE"></span>Starten Sie Windows PE

1.  Schließen Sie das Gerät (interne oder externe USB-Festplatte) an den PC, die Sie bearbeiten möchten.

2.  Aktivieren Sie auf dem PC, und verwenden Sie die Boot-Menüs, das Windows PE Laufwerk auszuwählen. Dies erfordert in der Regel durch Drücken einer Taste oder einen Schlüssel, wie die Esc-Taste.

    **Hinweis**  
    Für UEFI-basierte PCs, müssen Sie möglicherweise suchen eine Option, um die UEFI Startdateien, beispielsweise manuell auswählen USBDrive01\\EFI\\BOOT\\BOOTX64. EFI.

    Windows PE wird automatisch gestartet. Nachdem Sie im Befehlsfenster angezeigt wird, wird automatisch der Wpeinit-Befehl ausgeführt. Dies kann einige Minuten dauern.

    
## <a name="span-idtroubleshootingspano-troubleshooting"></a><span id="Troubleshooting"></span>o Problembehandlung

1.  Wenn der PC nicht gestartet, die folgenden Schritte nacheinander, und versuchen Sie nach jedem Schritt den PC starten:

    1.  Versuchen Sie für externe USB-Laufwerke, das Laufwerk in einen anderen USB-Anschluss. Vermeiden der Verwendung von USB-Hubs oder Kabel, da sie möglicherweise nicht während der Startsequenz erkannt werden. Vermeiden Sie enthält die Firmware keine systemeigene Unterstützung für USB-3.0 3.0 USB-Anschlüsse.

    2.  Benötigt der PC Treibern wie Treiber oder die Grafiktreiber, starten oder Ihre Treiber Änderungen an der Registrierung erforderlich ist, fügen Sie das Windows PE-Abbild der Treiber hinzu. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

    3.  Aktualisieren Sie auf die neueste Version der Firmware des PCs.

2.  Tipps zum Herstellen einer Verbindung mit einem Netzwerk finden Sie unter [Windows PE Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).

**Ausführen von Windows Setup über Windows PE**

-   Tipps zur Installation von Windows auf UEFI-PCs, die UEFI und legacy BIOS-Firmware Modi unterstützen und für die Verwendung der 32-Bit (x 86) Version von Windows PE zum Installieren einer 64-Bit-Version von Windows, finden Sie unter [Windows Setup unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md) .

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>Verwandte Themen

[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Identifizieren Sie Laufwerkbuchstaben mithilfe eines Skripts](winpe-identify-drive-letters.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






