---
author: kpacquer
Description: "Übung 9: Ändern von Windows (Überwachungsmodus aktiviert)"
ms.assetid: 142bc507-64db-43dd-8432-4a19af3c568c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 9: Ändern von Windows (Überwachungsmodus aktiviert)"
ms.openlocfilehash: bb505db23d2c3eaaaa2b22d0437f86f63bebf7c2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-9-make-changes-from-windows-audit-mode"></a>Übung 9: Ändern von Windows (Überwachungsmodus aktiviert)

Im Überwachungsmodus können Sie Windows mithilfe der vertrauten Windows-Umgebung anpassen. Im Überwachungsmodus aktiviert können Sie Windows-desktopanwendungen hinzufügen, Systemeinstellungen ändern, Hinzufügen von Daten und Ausführen von Skripts.  

Stellen Sie sicher, dass die Audit Modus Änderungen im Wiederherstellungsabbild enthalten sind, müssen Sie diese Änderungen in einer Bereitstellung Paket mit ScanState zu erfassen. Dieses Bild dient zum Abrufen von der Wiederherstellung Systemprogramme verwendet, um Ihre Änderungen wiederherzustellen, falls Dinge Fehler. Sie können optional Speicherplatz speichern, durch die Anwendung direkt aus den Wiederherstellungsdateien komprimierter ausführen. Dies wird als Single instancing bezeichnet.

Wenn Sie die Änderungen in einem Bild zu erfassen und andere Geräte zuweisen möchten, müssen Sie das Sysprep-Tool verwenden, um das Bild verallgemeinern.


## <a name="span-idprepareacopyofthedeploymentandimagingtoolsspanspan-idprepareacopyofthedeploymentandimaging-toolsspanspan-idprepareacopyofthedeploymentandimagingtoolsspanstep-1-prepare-a-copy-of-the-deployment-and-imaging-tools"></a><span id="Prepare_a_copy_of_the_Deployment_and_Imaging_Tools"></span><span id="prepare_a_copy_of_the_deployment_and_imaging Tools"></span><span id="PREPARE_A_COPY_OF_THE_DEPLOYMENT_AND_IMAGING_TOOLS"></span>Schritt 1: Vorbereiten der Bereitstellung und Imaging-Tools einer Kopie

Benötigen Sie die Windows-10 Version 1607 Version der Bereitstellung und Tools von ADK Imaging an. Dazu gehören das Tool ScanState und der aktuellen Version von DISM ein.

**Wichtig**   Überschreiben Sie nicht die vorhandenen DISM-Dateien auf dem Windows PE-Abbild.

1.  Kopieren Sie aus der PC-Techniker die Bereitstellung und Imaging-Tools aus dem Windows ADK in externen Speicher (beispielsweise einen Speicher USB-Schlüssel mit Laufwerkbuchstaben D:).

    ``` syntax
    CopyDandI.cmd amd64 D:\ADKTools\amd64
    ```
    
## <a name="span-idgetintoauditmodespanstep-2-get-into-audit-mode"></a><span id="Get_into_audit_mode"></span>Schritt 2: Abrufen der Überwachungsmodus

1.  Starten Sie das Gerät Verweis, wenn er noch nicht gestartet wird.

2.  Wenn das Gerät für die **Sprachen** oder dem **Wechsel zu Schnelles Abrufen** Bildschirm startet, drücken Sie **STRG + UMSCHALT + F3** Überwachungsmodus eingeben.

3.  Im Überwachungsmodus aktiviert das Gerät wird neu gestartet, auf dem Desktop, und die Systemvorbereitungstool (Sysprep) wird angezeigt. Jetzt ignorieren Sie Sysprep.

## <a name="span-idcustomizethepcspanstep-3-customize-the-pc-in-audit-mode"></a><span id="Customize_the_PC"></span>Schritt 3: Anpassen des PCs im Überwachungsmodus aktiviert.

-   Installieren Sie eine Windows-desktop-Anwendung. Ändern von Systemeinstellungen. Hinzufügen von Daten. Ausführen von Skripts.

## <a name="span-idcaptureyourchangesspanstep-4-capture-your-changes-for-the-recovery-tools"></a><span id="Capture_your_changes"></span>Schritt 4: Erfassen Sie Ihre Änderungen für die Wiederherstellungstools

1.  Verbinden Sie mit Ihrer externen Speicher (beispielsweise einen Speicher USB-Schlüssel mit dem Laufwerkbuchstaben D:)

2.  Erfassen der Änderungen in einem Paket Bereitstellung. Erstellt eine komprimierte Kopie der Faktoren, die Sie im Überwachungsmodus hinzugefügt, die von der Wiederherstellungstools verwendet werden kann und desktopanwendungen.

    ``` syntax
    D:\ADKTools\amd64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\usmt.ppkg /o /c /v:13 /l:C:\Recovery\ScanState.log
    ```

    **Hinweis**  Optional: Löschen der ScanState Logfile: `del C:\Recovery\Scanstate.log`.

## <a name="span-idprepareforimagecapturespanstep-5-prepare-for-image-capture"></a><span id="Prepare_for_image_capture"></span>Schritt 5: Vorbereiten der für die abbilderfassung

Dieser Schritt ist erforderlich, wenn Sie Bilder auf anderen PCs anwenden erfassen möchten.
    
1.  Das Gerät für den Endbenutzer vorbereiten: Maustaste auf **Start**, wählen Sie **die Befehlszeile (Admin)**und führen Sie über die Befehlszeile den folgenden Befehl aus:

    ``` syntax
    C:\Windows\System32\Sysprep\sysprep /oobe /generalize /shutdown
    ```

    Das Tool Sysprep versiegelt das Gerät. Dieser Vorgang kann einige Minuten dauern. Nachdem der Vorgang abgeschlossen ist, wird das Gerät automatisch beendet.

    **Warnung**: Wenn Sie [Silo provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md)verwenden, das Bild, das Starten im erneut (Sysprep/audit) Überwachungsmodus nicht festgelegt. Es ist ein bekanntes Problem in Windows 10, Version 1607, die das Bild möglicherweise nicht mehr gestartet wird, wenn Sie dies tun. Stattdessen legen Sie es, OOBE, starten und Start erneut, Überwachungsmodus [Hinzufügen eine Antwortdatei mit der Einstellung der Modus: Überwachen](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)möchten. Dieses Problem wird in zukünftigen Versionen behoben.

2.  Starten Sie das Gerät in Windows PE ein. Zu diesem Zweck müssen Sie die Taste drücken, die das Startvolumes Auswahlmenü für das Gerät (beispielsweise die **Esc** -Taste oder die Taste **Lautstärke** ) wird geöffnet.

    Wählen Sie die Option in der Firmware Menüs, die USB-Laufwerk zu starten.

    **Warnung**   Windows beginnt mit dem anstelle von Windows PE starten, müssen Sie das Gerät erneut, bevor Erfassen des Abbilds verallgemeinern: nach Windows gestartet wird, drücken Sie **STRG + UMSCHALT + F3** Überwachungsmodus eingeben. Das Gerät wird neu gestartet. Das Gerät erneut verallgemeinern: `C:\Windows\System32\Sysprep\sysprep /oobe /generalize /shutdown`.

3.  Optional: beschleunigen Sie die Optimierung und Image Capture Prozesse durch Festlegen des Power Schemas mit hoher Leistung:

    ``` syntax
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

4.  Hier finden Sie die Laufwerkbuchstaben mit DiskPart ein:

    ``` syntax
    diskpart
    DISKPART> list volume
    DISKPART> exit
    ```

    Beispielsweise die Laufwerke können werden mit einem Buchstaben gekennzeichneten wie folgt: *C* = Windows; *D* ist der Übungseinheit USB-Schlüssel, und *E* ist eine externe Festplatte.

    Beachten Sie, dass einige Partitionen möglicherweise nicht mit einen Laufwerkbuchstaben empfangen.

## <a name="span-idoptimizetheimagespanstep-6-optimize-the-image-to-take-up-less-drive-space-optional"></a><span id="Optimize_the_image"></span>Schritt 6: Optimieren Sie das Abbild beanspruchen weniger Speicherplatz (optional)

1.  Speichern Sie das Bild Single instancing Speicherplatz. Dies entfernt das Original desktop-Anwendung und fügt Zeiger Dateien hinzu, sodass diese Anwendungen ausgeführt werden können, aus die Wiederherstellung provisioning Paket, das Sie zuvor erstellt haben.

    ``` syntax
    DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Windows-Partition.

    **Warnung**  Stellen Sie nicht Anführungszeichen durch die /ImagePath:C:\\ Option.

2.  Bereinigung der Windows Dateien:

    ``` syntax
    md temp

    DISM /Cleanup-Image /Image=C:\ /StartComponentCleanup /ResetBase /ScratchDir:C:\Temp
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Windows-Partition. Beginnend mit Windows 10, Version 1607 verwenden, können Sie mit /Resetbase verzögern langer Cleanup Vorgänge auf die nächste automatische Verwaltung den /Defer-Parameter angeben. Es wird jedoch dringend empfohlen Sie **nur** als eine Option in der Factory, in denen DISM /Resetbase erfordert mehr als 30 Minuten, /Defer verwenden.

### <a name="span-idcapturetheimagespanspan-idcapturetheimagespanspan-idcapturetheimagespanstep-7-capture-the-image"></a><span id="Capture_the_image"></span><span id="capture_the_image"></span><span id="CAPTURE_THE_IMAGE"></span>Schritt 7: Erfassen Sie das Abbild

-   Erfassen Sie das Abbild der Windows-Partition.

    ``` syntax
    dism /Capture-Image /CaptureDir:C:\ /ImageFile:"C:\WindowsWithFinalChanges.wim" /Name:"Final changes"
    ```

    wobei *C* ist der Laufwerkbuchstabe der Partition Windows und *Französisch und Desktopanwendungen* den Namen des Abbilds ist.

    Das Tool DISM werden die Windows-Partition in eine neue Abbilddatei erfasst. Dieser Vorgang kann einige Minuten dauern.

    **Problembehandlung**: Wenn Sie erhalten eine: "ein Parameter ist falsch" Fehlermeldung, wenn Sie versuchen, kopieren Sie die Datei auf den USB-Schlüssel zu erfassen, die Datei ist möglicherweise zu groß für das Zieldateisystem. Kopieren Sie die Datei auf ein anderes Laufwerk, das NTFS-Dateisystem formatiert ist.

    2.  Kopieren Sie das Bild in eine Netzwerkfreigabe. Beispiel: 
    ```syntax
    net use N: \\server\share
    copy C:\WindowsWithFinalChanges.wim N:\Images\WindowsWithFinalChanges.wim
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 6: Wenden Sie das Abbild auf einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, das Windows-Abbild und die Wiederherstellungsabbild anwenden, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Verweis Gerät, um mit dem Windows PE USB-Schlüssel Windows PE starten](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Trennen Sie die Laufwerke, und klicken Sie dann neu starten (`exit`).
    
**Schritt 7: Überprüfen Sie, ob Anpassungen**

1.  Nach dem Starten des PCs-Option, entweder ein neues Benutzerkonto zu erstellen, andernfalls Drücken von STRG + UMSCHALT + F3, in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Sehen Sie, dass die im Überwachungsmodus vorgenommenen Änderungen vorhanden sind.

Nächste Schritte: [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md)