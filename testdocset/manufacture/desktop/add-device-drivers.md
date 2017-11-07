---
author: KPacquer
Description: "Hinzufügen von Gerätetreibern"
ms.assetid: 9a8f525c-bb8f-492c-a555-0b512e44bcd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 3: Hinzufügen von Gerätetreibern"
ms.openlocfilehash: a93bcfce576f633c174905777869d8cfc716b7fc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-3-add-device-drivers"></a>Übung 3: Hinzufügen von Gerätetreibern 

Hinzufügen von Gerätetreibern zu Ihren Bildern, um Ihre Hardware zu unterstützen. Einige haben Verfahren bei der Installation:

-  **INF-Schreibweise Treiber**: viele Treiber enthalten eine Informationsdatei (mit der Erweiterung INF) unterstützen den Treiber zu installieren. Diese können mithilfe der in diesem Thema beschriebenen Tools installiert werden.    
-  **.exe-Schreibweise Treiber**: Treiber ohne oft eine INF-Datei müssen wie herkömmlichen Windows-desktop-Anwendungen installiert sein. Zeigen wir Ihnen das Hinzufügen in [Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md).
-  **Wichtige Faktoren**: Grafiken und Speicher Treiber müssen in einigen Fällen, das Windows-Abbild (wie in diesem Thema dargestellt) sowie das Windows PE-Abbild hinzugefügt werden soll (siehe weiter oben in [Übung 1: Installieren von Windows PE](install-windows-pe-sxs.md)), und im Windows Recovery-Abbild. Zeigen wir Ihnen zum Aktualisieren des Wiederherstellungsabbilds später in [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md).

## <a name="span-idprepareandmounttheimagespanprepare-and-mount-the-image"></a><span id="Prepare_and_mount_the_image"></span>Vorbereiten Sie und stellen Sie das Abbild
Um die Änderungen an ein Windows-Abbild vornehmen, Sie den Bildinhalt in einen temporären Ordner bereitstellen, und verwenden Tools wie DISM, um die Änderungen vornehmen. Heben Sie die Bereitstellung der Bilder, um die Änderungen zu speichern, und die Bereitstellungsskripts verwenden, um die Bilder zu testen. 

![Bild: Bereitstellen eines Abbilds, Änderungen vornehmen und Aufheben der Bereitstellung des Abbilds](images/dep-win8-sxs-createmodelspecificfiles.jpg)

**Schritt 1: Sichern Sie Ihrer Windows-Bilddatei (beim Testen des neuen Designs empfohlen)**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Erstellen Sie eine Sicherungskopie der Bilddatei an:
``` syntax
copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim
```

**Schritt2: Binden Sie die Windows-Bilddatei** Erstellen Sie einen temporären Ordner, um die Dateien bereitstellen, und stellen Sie das Abbild hinein: 
``` syntax
md C:\mount\windows
Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize
```
/ Index: 1, wobei das Bild bezeichnet, die Sie bereitstellen möchten. Verwenden Sie für die Edition Windows 10 Home/Pro/Index: 2, die Home Edition auszuwählen.

Dieser Schritt kann einige Minuten dauern.

**Problembehandlung:**

-   Bilder zu geschützten Ordnern an, wie Ihre Benutzer nicht bereitstellen\\-Dokumentordner.

-   Wenn DISM Prozesse unterbrochen werden, können Sie vorübergehend aus dem öffentlichen Netzwerk trennen und Virenschutz deaktivieren.
    
-   Wenn Sie ein Bild in den Ordner, bevor Sie bereitgestellt haben, versuchen Sie, bereinigen die bereitgestellten Abbild zugeordneten Ressourcen:

    ``` syntax
    Dism /Cleanup-Mountpoints
    ```

-   Für einige DISM-Befehle müssen Sie sicherstellen, dass Sie die **Bereitstellung und Imaging Tools Umgebung** statt der standard-Eingabeaufforderung.

## <a name="span-idaddcustomizationstotheimagespanadd-customizations-to-the-image"></a><span id="Add_customizations_to_the_image"></span>Hinzufügen von Anpassungen auf das Bild
Dies sind nur Beispiele – Sie müssen nicht alle diese hinzufügen.

**Schritt 3: Hinzufügen von Treibern**

1.  Hinzufügen eines einzelnen Treibers, das eine INF-Datei enthält:

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf"
    ```

    wobei "C:\\Treiber\\PnP.Media.V1\\media1.inf" ist die Basis INF-Datei in das Treiberpaket.

    **Problembehandlung**: für viele DISM-Befehle können Sie ausführliche Informationen zu dem Fehler durch die Option/LogPath hinzufügen. Beispiel:

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

2.  Installieren Sie eine Gruppe von Treibern mithilfe der Option/recurse. Dadurch werden alle Treiber durch eine INF-Datei in diesem Ordner und alle Unterordner hinzugefügt.

    **Warnung**: / recurse können nützlich sein, es ist einfach, Ihr Bild zu Aufblasen. Einige Treiberpakete enthalten mehrere INF-Treiberpakete, die häufig Nutzlast Dateien im gleichen Ordner gemeinsam nutzen. Während der Installation wird jede INF-Paket in einen gesonderten Ordner, jeweils mit einer Kopie der Dateien Nutzlast erweitert. Wir haben Fällen gesehen, in denen ein beliebter Treiber in einem Ordner 900MB 10 GB Bilder, wenn mit der Option/recurse hinzugefügt hinzugefügt.

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:c:\drivers /Recurse 
    ```
    
3.  Stellen Sie sicher, dass der Treiber Teil des Bilds sind:

    ``` syntax
    Dism /Get-Drivers /Image:"C:\mount\windows"
    ```

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste den Treiber enthält.


## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>Heben Sie die Bereitstellung des Abbilds
    
**Schritt 4: Heben Sie die Bereitstellung der Bilder**

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:
    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 5: Wenden Sie das Abbild auf einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, wenden Sie das Abbild, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Verweis Gerät, um mit dem Windows PE USB-Schlüssel Windows PE starten](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Trennen Sie die Laufwerke, und klicken Sie dann neu starten (`exit`).

**Schritt 6: Überprüfen Sie, ob Treiber**
1.  Nach dem Starten des PCs-Option, entweder ein neues Benutzerkonto zu erstellen, andernfalls Drücken von STRG + UMSCHALT + F3, in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Klicken Sie mit der rechten Maustaste auf **Start** , und wählen Sie **die Befehlszeile (Admin)**.

3.  Stellen Sie sicher, dass die Treiber ordnungsgemäß angezeigt werden:

    ``` syntax
    Dism /Get-Drivers /Online
    ```

    Überprüfen Sie die resultierende Liste der Treiber. Beispiel:

    ``` syntax
    Deployment Image Servicing and Management tool
    Version: 10.0.14393.0

    Image Version: 10.0.14393.0

    Obtaining list of 3rd party drivers from the driver store...

    Driver packages listing:

    Published Name : oem0.inf
    Original File Name : contoso.graphicsdriver.inf
    Inbox : No
    Class Name : Graphics
    Provider Name : Contoso
    Date : 10/19/2016
    Version : 10.0.0.1

    The operation completed successfully.
    ```

## <a name="span-idlearnmorespanlearn-more"></a><span id="Learn_more"></span>Weitere Informationen

* Beim Erstellen von mehreren Geräten mit den identische Hardwarekonfiguration können Sie Installationszeit und ersten Systemstart durch [Verwalten von Windows-Abbildern Treiberkonfigurationen](maintain-driver-configurations-when-capturing-a-windows-image.md)beschleunigen. 


Nächster Schritt: [Übung 4: Updates hinzufügen und aktualisieren Sie die Version](servicing-the-image-with-windows-updates-sxs.md)