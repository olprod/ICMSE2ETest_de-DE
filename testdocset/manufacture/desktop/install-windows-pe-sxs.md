---
author: KPacquer
Description: Installieren von Windows PE
ms.assetid: e6e571df-8b4f-43f8-9a8c-cb5f25969a5d
MSHAttr: PreferredLib:/library/windows/hardware
title: Installieren von Windows PE
ms.openlocfilehash: ebe012dfb0c9389ff71930e377edeba6c3c22654
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1-install-windows-pe"></a>Übung 1: Installieren von Windows PE


Windows-Vorinstallation Environment (Windows PE) ist ein kleines, Command-Line je Betriebssystem. Verwenden sie zum Erfassen, aktualisieren und Optimieren der Leistung von Windows-Abbildern, was in den nachfolgenden Abschnitten werden. In diesem Abschnitt Sie Vorbereiten eines einfaches Windows PE-Abbilds auf einem startbaren USB-Laufwerk und probieren Sie es aus.

Windows PE USB muss mindestens 512 MB und höchstens 32 GB. Es sollte kein Windows-to-Go-Taste oder einen Schlüssel als nicht Wechseldatenträger gekennzeichnet sein.

## <a name="span-idpreparethewinpefilesspanprepare-the-winpe-files"></a><span id="Prepare_the_WinPE_files"></span>Vorbereiten der Windows PE-Dateien

1.  Starten Sie auf Ihre Techniker PC, **Bereitstellung und Imaging Tools Umgebung** als Administrator ein:
    -  Klicken Sie auf **Starten**, geben Sie **Bereitstellung und Imaging Tools Umgebung**. Maustaste auf **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie **als Administrator ausführen**.

2.  Kopieren Sie die Basis Windows PE-Dateien in einen neuen Ordner:

    ``` syntax
    copype amd64 C:\winpe_amd64
    ```

    Wiederholen Sie, wenn Sie auch X86 bereitstellen Geräte:

    ``` syntax
    copype x86 C:\winpe_x86
    ```

   **Problembehandlung**: Wenn dies nicht funktioniert, achten Sie in der Bereitstellung Imaging Tools Umgebung und nicht die standard Befehlszeile. 
    
## <a name="span-idaddtowinpespanadd-to-winpe-usually-not-needed"></a><span id="Add_to_WinPE"></span>Fügen Sie zu einer Windows PE (normalerweise nicht erforderlich hinzu)

Häufige Szenarien:

* **Hinzufügen eines Videos oder vorliegen**. (Windows PE enthält generische Video und Netzwerk-Treiber, aber in einigen Fällen sind zusätzliche Treiber erforderlich, damit den Bildschirm anzeigen oder Verbinden mit dem Netzwerk.)

* **Hinzufügen von PowerShell-Skripts Support**. Weitere Informationen finden Sie unter [Windows PE: Hinzufügen von Windows PowerShell-Unterstützung zu Windows PE](winpe-adding-powershell-support-to-windows-pe.md). PowerShell-Skripts sind in dieser Übungseinheit nicht enthalten.

Beachten Sie, wenn Sie Windows PE weitere Pakete hinzufügen, wird Windows PE Leistung und erhöhte Zeit beeinträchtigt. Fügen Sie nur bei Bedarf weitere Pakete.  

Bei Geräten mit eingeschränkten RAM und Speicher (beispielsweise 1GB RAM / 16GB Speicher): nach dem Hinzufügen der Treiber oder weitere Anpassungen vor Windows PE finden Sie unter [Windows PE: Optimieren der Leistung und das Bild reduzieren](winpe-optimize.md) zur Reduzierung die Startzeit.

1.  Stellen Sie das Windows PE-Abbild. Bereitstellen eines Abbilds ordnet dem Inhalt einer Datei an einen Speicherort, in dem Sie anzeigen und ändern können.

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

2.  Treiber hinzufügen.

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

3.  Heben Sie die Bereitstellung des Windows PE-Bilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

## <a name="span-idcreateabootabledrivespancreate-a-bootable-drive"></a><span id="Create_a_bootable_drive"></span>Erstellen eines startbaren Laufwerks

1.  Schließen Sie ein USB-Schlüssel, den Sie Formatierung nicht stört. Beachten Sie der Laufwerkbuchstabe, die es verwendet werden, beispielsweise D.

2.  Windows PE zu einem leeren USB-Laufwerk zu installieren:

    ``` syntax
    MakeWinPEMedia /UFD C:\winpe_amd64 D:
    ```

    Wenn Sie aufgefordert werden, drücken Sie **Y** ein, um das Laufwerk formatieren, und installieren Windows PE.

    Wiederholen Sie bei Bedarf einen separaten USB-Schlüssel für die Verwendung bei der Bereitstellung von X86 anschließen Geräte:

    ``` syntax
    MakeWinPEMedia /UFD C:\winpe_x86 E:
    ```

    Wenn Sie aufgefordert werden, drücken Sie **Y** ein, um das Laufwerk formatieren, und installieren Windows PE.

3.  Klicken Sie im Datei-Explorer mit der rechten Maustaste in des Laufwerks, und wählen Sie **Auswerfen**.

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

1.  Schließen Sie das WinPE USB-Laufwerk auf Ihrem Gerät Verweis.

2.  Deaktivieren Sie das Gerät, und klicken Sie dann auf die USB-Laufwerk starten. Sie dazu in der Regel das Gerät eingeschaltet und schnell Drücken einer Taste (beispielsweise die **Esc** -Taste oder die **Lautstärke nach oben** -Taste).

    **Hinweis**   Auf einige Geräte müssen Sie möglicherweise in den Menüs Boot das USB-Laufwerk auswählen zu wechseln. Wenn Sie die Wahl zwischen Starten im UEFI oder BIOS-Modus angegeben wurde, wählen Sie UEFI-Modus. Finden Sie weitere Informationen finden Sie unter [Starten UEFI oder Legacy-BIOS-Modus](http://go.microsoft.com/fwlink/?LinkId=526943).
    Wenn das Gerät nicht aus dem USB-Laufwerk startet, finden Sie unter die Tipps zur Problembehandlung in [Windows PE: Erstellen startbaren USB-Laufwerk](http://go.microsoft.com/fwlink/?LinkId=526944).

    Windows PE an der Befehlszeile startet und führt **Wpeinit** So richten Sie das System ein. Dies kann einige Minuten dauern.

Lassen Sie dieser PC jetzt Windows PE gestartet. 

Nächster Schritt: [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md)
 