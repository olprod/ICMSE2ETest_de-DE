---
author: kpacquer
Description: Bereitstellen von Windows mithilfe eines Skripts
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 2: Bereitstellen von Windows mithilfe eines Skripts"
ms.openlocfilehash: 034275b0e580e24296b5cc6704bcd975a78405da
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-2-deploy-windows-using-a-script"></a>Übung 2: Bereitstellen von Windows mithilfe eines Skripts

Skripts können Sie ein Windows-Abbild übernehmen und schnelle Bereitstellung von Windows auf neuen PCs. Sie können diese Skripts zum Ändern der Größe der Laufwerkspartitionen oder vollständig automatisieren der Bereitstellung ändern. 

## <a name="spand-idgettheimagespanstep-1-mount-the-image"></a>< Spand Id = "Get_the_image ></span>Schritt 1: Stellen Sie das Abbild

Ihres PC-Technikers und mit der rechten Maustaste der Bilddatei für Windows 10, Version 1607-Startseite (X21 08790), und wählen Sie bereitstellen. Dadurch werden die Dateien in einem temporären Laufwerkbuchstaben (beispielsweise D:) geladen. 

## <a name="span-idcopythebaseimagespanstep-2-copy-the-base-windows-image-file-to-the-storage-usb-drive"></a><span id="Copy_the_base_image"></span>Schritt 2: Kopieren Sie Basis Windows Bilddatei an in das Speicher USB-Laufwerk

1.  Kopieren Sie die Windows-Bilddatei an Ihr USB-Speicherlaufwerk:

    ``` syntax
    md E:\images
    copy D:\sources\install.wim file E:\images\install.wim.
    ```
    
    D: ist das Laufwerk aus dem Windows-ISO und E: ist die USB-Speicherlaufwerk. 

2.  Kopieren Sie den [Beispielskripts](windows-deployment-sample-scripts-sxs.md) in den Stamm des Laufwerks USB-Speicher.

## <a name="span-idapplytheimagespanstep-3-apply-the-windows-image-using-a-script"></a><span id="Apply_the_image"></span>Schritt 3: Wenden Sie das Windows-Abbild mithilfe eines Skripts

Verwenden Sie Bereitstellungsskripts, um das Abbild auf einem Testgerät anzuwenden. Diese Skripts richten Sie die Festplattenpartitionen und fügen Sie die Dateien aus dem Windows-Abbild auf die Partitionen.

Sie können die [Beispielskripts](windows-deployment-sample-scripts-sxs.md) für verschiedene Firmware Gerätetypen (die neuere UEFI-basierten, oder der Vorversion BIOS) verwenden. Einige UEFI-basierte Geräte beinhalten Unterstützung für das ältere legacy-BIOS. Weitere Informationen finden Sie unter [UEFI Firmware](http://go.microsoft.com/fwlink/?LinkId=526945).

![Abbildung zeigt, um eine Referenz-Computer mit Anpassungen erstellen, einen neuen PC und einer Bilddatei ein Bereitstellungsskript benötigen.](images/dep-win8-sxs-createdeploymentscript.jpg)

1.  [Verweis Gerät, um mit dem Windows PE USB-Schlüssel Windows PE starten](install-windows-pe-sxs.md).

2.  Nehmen Sie die Windows PE USB-Taste, und platzieren Sie in den Speicher USB-Schlüssel.
    
3.  Hier finden Sie die Laufwerkbuchstaben des USB-Schlüssels mithilfe von Diskpart:

    ``` syntax
    diskpart
    DISKPART> list volume
    DISKPART> exit
    ```

    Beispielsweise die Laufwerke können werden mit einem Buchstaben gekennzeichneten wie folgt: C = Windows; D = USB-Speicherlaufwerk.

4.  Formatieren Sie die primäre Festplatte, erstellen Sie die Partitionen, und wenden Sie das Abbild mithilfe der vorbereiteten [Beispielskripts](windows-deployment-sample-scripts-sxs.md). 

Das Skript **ApplyImage.bat** verwendet der Diskpart-Skripts: CreatePartitions UEFI.txt und CreatePartitions BIOS.txt zum Erstellen von Partitionen und definieren das Partitionslayout. Diese Skripts müssen im selben Ordner platziert werden. Sie können diese Skripts zum Ändern der Partitionsgröße aktualisieren.

    ``` syntax
    D:
    D:\ApplyImage.bat D:\Images\install.wim
    ```

    When prompted by the script: 
    
    1.  Drücken Sie Y ein, um das Laufwerk zu formatieren.
    2.  Drücken Sie Y ein, um Compact OS oder N wählen Sie ein Betriebssystem nicht komprimiert auswählen:
        -   **Y**: das Bild mit Compact OS gilt. Dies ist am besten für Geräte mit Solid-State und Laufwerke mit beschränktem freien Speicherplatz. Verwenden Sie dies für Hardwarekonfiguration 1 und 2 aus.
        -   **N**: das Bild als Bild vollständig dekomprimiert gilt. Dies ist am besten für High Performance Geräte oder Geräte, die herkömmliche Festplatten mit Rotation Media verwenden. Verwenden Sie dies für Hardwarekonfiguration 3.
    3.  Drücken Sie N, um anzugeben, dass das Bild enthält keinen erweiterten Attribute (EA).

    Die Skripts, wenden Sie das Abbild auf das Laufwerk und dann beendet.

    
## <a name="span-idapplydesktopapplicationsspanstep-4-apply-desktop-applications"></a><span id="Apply_desktop_applications"></span>Schritt 4: Wenden Sie desktopanwendungen

**Überspringen Sie diesen Schritt** , bis Sie abgeschlossen haben [Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md). Dieser Schritt fügt Windows-desktopanwendungen zu Ihren Bildern. Dies muss vor dem Hinzufügen des Wiederherstellungsabbilds erfolgen.

1.  Gelten Sie desktopanwendungen.
    ```syntax
    D:\ADKTools\amd64\WimMountAdkSetupAmd64.exe /Install /q
    D:\ADKTools\amd64\DISM.exe /ImagePath:C:\ /Apply-SiloedPackage /PackagePath:E:\SPPs\office16_base.spp /PackagePath:E:\SPPs\office16_fr-fr.spp /PackagePath:E:\SPPs\office16_de-de.spp
    ```

## <a name="span-idapplytherecoveryimagespanstep-5-set-up-the-system-recovery-tools"></a><span id="Apply_the_recovery_image"></span>Schritt 5: Einrichten der Wiederherstellung Systemprogramme

**Optional: überspringen Sie diesen Schritt** , bis Sie abgeschlossen haben [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md). 

Image-Wiederherstellung für die endgültige Bilder enthalten, aber es ist nicht für diese frühe Tests Schritte erforderlich. 

1.  Wenden Sie das Abbild Windows Recovery Environment (Windows RE). Diese Tools unterstützen häufige Ursachen für nicht startbaren Betriebssysteme repariert. Das Bild wird in einem separaten Laufwerkpartition gespeichert. Verwendet das Skript **ApplyRecovery.bat** Diskpart-Skripts: HidePartitions UEFI.txt und HidePartitions-BIOS.txt, um diese Partition einzurichten. Diese Skripts müssen im selben Ordner wie ApplyRecovery.bat platziert werden.

    ```syntax
    D:\ApplyRecovery.bat
    ```

## <a name="span-idrebootspanstep-6-reboot"></a><span id="Reboot"></span>Schritt 6: Neustart

Trennen Sie die Laufwerke, und klicken Sie dann neu starten (`exit`).

Der PC-Option sollte in Windows neu starten. Während der Vorbereitungsphase für die Durchführung warten Sie zurück zu Ihrem PC-Techniker, und fahren Sie mit dem Labor.

**Problembehandlung**: Wenn das Gerät nicht gestartet wird, aktivieren Sie das Gerät, und drücken Sie den Schlüssel, der das Auswahlmenü Startvolumes (beispielsweise die **Esc** -Taste) wird geöffnet. Wählen Sie die Festplatte als Boot-Gerät aus, und fortfahren.

**Optional: Testen Sie das Wiederherstellungsabbild**
1.  Führen Sie den ersten Anmeldevorgang wie ein normaler Benutzer aus.
2.  Wählen Sie **Start** &gt; **Einstellungen** &gt; **Security & aktualisieren** &gt; **Wiederherstellung** &gt; unter **diesem PC zurückzusetzen**, klicken Sie auf **die ersten Schritte beim** > **Alles entfernen**  >  ** Meine Dateien entfernen** > **Weiter**.
3.  Nach Abschluss des Zurücksetzens Windows sollten Windows als wäre es kein Benutzerkonto auf dem Gerät wieder an den ursprünglichen Willkommen wechseln.

## <a name="span-idwhatsnextspanwhats-next"></a><span id="Whats_next"></span>Was kommt dann

[Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) (einschließlich Grundlagen zum Bereitstellen von Bilder)
