---
Autor: KPacquer Beschreibung: Übung 11: Reduzieren Sie die Bildgröße MSHAttr: ' PreferredLib: / Bibliothek/Windows/Hardware ' Titel: Übung 11: Reduzieren Sie die Bildgröße
---

# <a name="lab-11-shrink-your-image-size"></a>Übung 11: Verkleinern Sie die Bildgröße

Optimieren des Windows-Abbilds, um Speicherplatz zu sparen, auf dem PC, einen Übertragungen auf neue Geräte zu beschleunigen und speichern zu vereinfachen.

Dazu verwenden wir überprüfen DISM-Tools nach doppelten Dateien. Wir werden die Dateien für die Entfernung markiert. Diese Dateien werden nicht entfernt werden, bis das Bild zu exportieren. 

   ![Bild: Stellen Sie das Abbild, duplizierte Dateien zum Entfernen zu kennzeichnen, heben Sie die Bereitstellung des Abbilds und dann exportieren Sie das Abbild.](images/dism-shrink-image.jpg)


Wir werden das Bild WinRE optimieren, die innerhalb der Windows-10 und Windows Server 2016 Bilder enthalten ist, und schließlich in der Windows RE-Tools-Partition auf dem Ziel-PC oder ein Gerät kopiert. Um sie zu ändern, müssen Sie stellen Sie das Windows-Abbild und dann stellen Sie das Abbild WinRE darin. Stellen Sie die Änderungen, heben Sie die Bereitstellung des WinRE Bilds, und heben Sie die Bereitstellung des Windows-Abbilds. 

   ![Bild: Stellen Sie das Windows-Abbild, und stellen Sie das Wiederherstellungsabbild darin. Nehmen Sie Änderungen vor, und klicken Sie dann heben Sie die Bereitstellung der Wiederherstellungsabbild und schließlich auf dem Windows-Abbild](images/customize-recovery-image.jpg)

## <a name="span-idmounttheimagesspanmount-the-images"></a><span id="Mount_the_images"></span>Binden Sie die Bilder

**Schritt 1: Stellen Sie das Windows-Abbild**

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) , das Windows-Abbild bereitzustellen. Die Kurzversion:

1.  Öffnen Sie als Administrator der Befehlszeile (**Starten** > geben **Bereitstellung** > Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)



## <a name="span-idoptimizingtheimagepart1spanspan-idoptimizingtheimagepart1spanspan-idoptimizingtheimagepart1spanstep-2-optimizing-the-image-part-1-optional"></a><span id="Optimizing_the_image_part_1"></span><span id="optimizing_the_image_part_1"></span><span id="OPTIMIZING_THE_IMAGE_PART_1"></span>Schritt 2: Optimieren das Bild, Teil 1 (optional)

Nach dem Hinzufügen eine Sprache oder ein Windows-Updatepaket, können Sie die Größe von Bildgröße reduzieren, indem duplizierten Dateien gesucht und markiert die älteren Versionen als abgelöst.

1.  Optimieren Sie das Bild:

    ``` syntax
    Dism /Image:c:\mount\windows /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

2.  Später exportieren Sie das Bild, um die ersetzten Dateien zu entfernen.

## <a name="span-idbkmksaveimagespanspan-idbkmksaveimagespanspan-idbkmksaveimagespanstep-3-unmount-the-windows-image"></a><span id="BKMK_SaveImage"></span><span id="bkmk_saveimage"></span><span id="BKMK_SAVEIMAGE"></span>Schritt 3: Aufheben des Windows-Abbilds


-   Heben Sie die Bereitstellung, und speichern Sie das Bild:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

## <a name="span-idoptimizingtheimagepart2spanspan-idoptimizingtheimagepart2spanspan-idoptimizingtheimagepart2spanstep-4-optimizing-the-image-part-2-optional"></a><span id="Optimizing_the_image_part_2"></span><span id="optimizing_the_image_part_2"></span><span id="OPTIMIZING_THE_IMAGE_PART_2"></span>Schritt 4: Optimieren das Bild, Teil 2 (optional)

Wenn Sie das Bild optimiert haben, müssen Sie das Bild zu exportieren, um eine Änderung der Dateigröße zu sehen. Während des Exportvorgangs entfernt DISM Dateien, die ersetzt wurden.

1.  Exportieren Sie das Windows-Abbild in eine neue Abbilddatei aus.

    ``` syntax
    Dism /Export-Image /SourceImageFile:"C:\Images\Win10_x64\sources\install.wim" /SourceIndex:1 /DestinationImageFile:"C:\Images\Win10_x64\sources\install-optimized.wim"
    ```

Nächster Schritt: [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md)