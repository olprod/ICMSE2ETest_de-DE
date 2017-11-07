---
author: kpacquer
Description: "OEM und Enterprise-Kunden können eine Reihe von Skripts und Tools zur app-Updates für Windows 10 IoT Core (IoT Core) Geräte senden nutzen."
ms.assetid: 010c4836-a8ad-4ab9-b5a8-45babcc8a3f3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Aktualisieren von apps auf Ihren Geräten IoT Core"
ms.openlocfilehash: 92348a061555f21b1c4d35f1723a28bc42972b4e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-apps-on-your-iot-core-devices"></a>Aktualisieren von apps auf Ihren Geräten IoT Core

**Neue für Windows 10, Version 1607**: OEMs und Unternehmenskunden realisiert werden können app-Updates für Windows 10 IoT Core Geräte indem Aktualisierungen an den Windows Store. Wenn Ihre Geräte mit dem Internet verbinden, sie regelmäßig suchen nach Updates aus dem Windows Store und Updates automatisch installieren. 

Bevor Sie Updates an den Store senden, sollten sie zuerst auf Ihren eigenen Geräten testen. 

## <a name="span-idsendupdatestothewindowsstorespansend-updates-to-the-windows-store"></a><span id="Send_updates_to_the_Windows_Store"></span>Senden von Updates an den Windows Store

Erstellen Sie Updates für Ihre apps auf die gleiche Weise, die Sie den ursprünglichen apps erstellen.

Verwenden Sie jedes Mal eine höhere Versionsnummer. (Beispielsweise--> 1.0.0.0 1.0.1.0.)

Es ist OK, um die vorhandenen Paketnamen wiederverwenden und sogar über die alte Ordnernamen und Speicherorte schreiben. Sichern der Dateien zuerst, für den Fall, dass Sie die Änderung später wiederherstellen möchten.

Es wird empfohlen, die Sie [Testen und überwachen Sie das Update](#Test_and_track_the_update) mit den Verfahren in diesem Thema.

Schließlich signieren und das app-Paket an den Windows Store zu übermitteln. 

Weitere Informationen finden Sie unter [Installing and apps auf Windows 10 IoT Core Servicing](https://developer.microsoft.com/en-us/windows/iot/docs/store)

## <a name="span-idtestandtracktheupdatespanspan-idtest-and-track-the-updatespanspan-idtest-and-track-the-upatespantest-and-track-the-update-recommended"></a><span id="Test_and_track_the_update"></span><span id="test and track the update"></span><span id="TEST AND TRACK THE UPATE"></span>Testen Sie und überwachen Sie das Update (empfohlen)

Testen Sie die Updates auf Ihren Geräten vor dem Senden an den Windows Store aus.

### <a name="span-idcreateanupdatepackagespancreate-an-update-package"></a><span id="Create_an_update_package"></span>Erstellen Sie ein Update-Paket

1.  Erstellen Sie einen Ordner für Ihre Updatepaket. 

    Verwenden Sie eine neue Versionsnummer. Diese Versionsnummer gilt für alle Pakete in Projekten.

    ``` syntax
    newupdate Update1 10.0.0.1
    ```

2.  Aktualisieren der app mit Änderungen an.

3.  Erstellen Sie die app über eine neue Versionsnummer. 
    
4.  Aktualisieren Sie das Paketinfo:

    - Erstellen Sie eine Kopie der vorhandenen Paket (beispielsweise Appx.HelloWorld) unter Update1\ Ordner, und aktualisieren Sie, klicken Sie dann mit der Versionsnummer.
    
    - Kopieren Sie die neuen Appx Dateien in das Verzeichnis.
    
    - Open C:\\Iot-Adk-Addonkit\\Quelle Arm\\Pakete\\Appx.HelloWorld\\Appx.HelloWorld.pkg.xml und die Version Nummerierung aktualisieren.
        
5.  Erstellen Sie das Updatepaket

    ``` syntax
    createupdatepkgs Update1
    ```

    Die Ausgabe wechselt zu C:\\Iot-Adk-Addonkit\\erstellen\\Arm\\Update1.

### <a name="span-idapplytheupdatedirectlytothedevicespanspan-idapplytheupdatedirectlytothedevicespanspan-idapplytheupdatedirectlytothedevicespanapply-the-update-directly-to-the-device"></a><span id="Apply_the_update_directly_to_the_device"></span><span id="apply_the_update_directly_to_the_device"></span><span id="APPLY_THE_UPDATE_DIRECTLY_TO_THE_DEVICE"></span>Wenden Sie das Update direkt auf das Gerät

1.  Die CAB-Datei auf das Gerät zu kopieren. Sie können dazu ein FTP-Tool wie [WinSCP](http://winscp.net)oder indem die Datei direkt auf das Gerät Laufwerk (beispielsweise eine Micro SD-Karte) kopiert.

2.  Verbinden Sie auf der Techniker PC auf Ihrem Gerät mit einem SSH-Client, wie beispielsweise [kitten](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe). Verwenden Sie beispielsweise IP-Adresse und Port 22, um eine Verbindung mit dem Gerät, und melden Sie sich mit dem Administratorkonto und Kennwort. (Weitere Informationen finden Sie finden Sie unter [Verwenden von SSH eine Verbindung herstellen, und konfigurieren ein Gerät, auf dem Windows IoT Core](https://developer.microsoft.com/windows/iot/docs/ssh).)

3.  Bereitstellen Sie über die Befehlszeile Gerät, das Update. Sie können diesen Schritt, um mehrere Updates Phase wiederholen.
    ``` syntax
    ApplyUpdate.exe -stage <DownloadedPackageName.cab>
    ```

4.  Commit der Änderungen an. Mit diesem Befehl löst auch der Windows Update-Vorgang anwendbare Updates installieren. 
    ``` syntax
    ApplyUpdate.exe -commit
    ```
    
    (Verwenden Sie zum Ablehnen alle Updates: `ApplyUpdate.exe -clear` stattdessen.)
    
    Problembehandlung:
    -  **Fehler: Eine Zertifikatkette konnte nicht zu einer vertrauenswürdigen Stammzertifizierungsstelle erstellt werden. (0x800B010A). signaturüberprüfung ist fehlgeschlagen.** Mögliche Ursache: Hinzufügen von Test Bilder auf ein Bild Retail signiert. Melden Sie sich das Bild, und versuchen Sie es erneut.
       
    -  **Fehler: 0x80188302.**
       Mögliche Ursache: falsche Version des Pakets. Stellen Sie sicher, dass die neue Versionsnummer höher ist als die alte Version ist, und versuchen Sie es erneut. 
    
    -  **Fehler: Update (0x8024A10F) konnte nicht gestartet werden** Mögliche Ursache: Windows Update wird gerade durchgeführt. Versuchen Sie es erneut, nachdem die aktuelle Windows-Updates abgeschlossen ist.
       

### <a name="span-idkeeptrackofversionsspankeep-track-of-versions"></a><span id="Keep_track_of_versions"></span>Nachverfolgen der Versionen

Open `UpdateVersion.txt` Beschreibungen von Paketen angezeigt. Das Tool Createupdatepkgs aktualisiert diese Datei beim Erstellen eines neuen Updates.

### <a name="span-idtestnewimagesspantest-new-images"></a><span id="Test_new_images"></span>Testen Sie neue Bilder
Erstellen Sie ein neues Paket mit demselben Verfahren wie in dargestellt [Übung 1 b: Hinzufügen einer app zu Ihr Bild](../../manufacture/iot/deploy-your-app-with-a-standard-board.md).
