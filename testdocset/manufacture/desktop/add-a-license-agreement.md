---
author: KPacquer
Description: "Übung 8: Hinzufügen eines OEM-Lizenzvertrags"
ms.assetid: a29101dc-4922-44ee-a758-d555e6cf39fa
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 8: Hinzufügen eines Lizenzvertrags"
ms.openlocfilehash: 77cf27ac6dc75a59fad4307579a5fc00f4bee061
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-an-oem-license-agreement"></a>Hinzufügen eines OEM-Lizenzvertrags

Sie können Ihre eigenen OEM-Lizenzbedingungen Windows hinzufügen. 

Für Bilder mit mehreren Region oder in mehreren Sprachen können Sie bestimmte Lizenzbedingungen Region erstellen. Diese Anzeigen der Benutzer während der ersten Anmeldung wünschen, basierend auf dem Region oder Sprache, die sie auswählen. 

Hinweis: Wenn die Lizenzbedingungen enthalten sind, muss der OEM eine Version, die Lizenzbedingungen jede Sprache enthalten, die auf dem PC vorinstalliert ist. Ein Lizenz Begriff Text muss ein. **RTF** -Datei als gespeichert. **RTF** -Format.

Verwenden Sie in den Beispielen im [USB-B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip) Schlüssel.

## <a name="span-idcreatelicensefilesspancreate-license-files"></a><span id="Create_license_files"></span>Erstellen von Lizenzdateien

1.  Erstellen von Ordnern unter Arbeitsordner, beispielsweise C:\oobe. 

2.  Nennen Sie jeden Ordner C:\oobe\info\default\ im Verzeichnis als **Decimal Sprach-ID** die Sprache entspricht. Wiederholen Sie diesen Schritt für jedes Sprachpaket, das Windows-Abbild hinzugefügt wurde.

    Die vollständige Liste der Sprache Dezimal entsprechenden Sprachen-IDs finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).

    Beispielsweise wenn En-us und de-de Sprachpakete auf der Windows-Abbild hinzugefügt fügen einen Ordner namens "1033" (En darstellt-uns Sprache) unter C:\mount\windows\Windows\System32\oobe\info\default\. fügen Sie einen Ordner namens "1031" (Ereignisobjekten de-de Language) unter demselben Verzeichnis.

    ```syntax
    md c:\oobe\info\default\1033
    md c:\oobe\info\default\1031
    ```

1.  Erstellen Sie die Lizenz Begriff Dokument für jede Sprache angegeben. Verschieben Sie jede Lizenz Begriff Dokument auf den entsprechenden Sprachordner.

    Verschieben der agreement.rtf **in Englisch** , beispielsweise die Datei:  
    
    ```syntax
    C:\oobe\info\default\\**1033**\  
    ```

    Verschieben der agreement.rtf Datei **in Deutsch** an: 
    
    ```syntax
    C:\oobe\info\default\\**1031**\ 
    Copy C:\USB-B\resources\agreement.rtf c:\oobe\info\default\1033
    ```

1.  Erstellen Sie eine Datei **oobe.xml** , um den Dateipfad agreement.rtf anzugeben. In der folgenden Abbildung sehen Sie ein Beispiel oobe.xml sich auf dem Zielserver mit **USB-B**\ConfigSet\oobe.xml befindet.

    ![Beispiel OOBE](images/sample-oobe.png)

2.  Kopieren Sie **Datei oobe.xml** in jeder Sprachordner.

    Kopieren Sie beispielsweise oobe.xml in C:\oobe\info\default\\**1033**\, in denen die agreement.rtf in Englisch gültig ist und C:\oobe\info\default\\**1031**\ Verzeichnis, in dem die agreement.rtf auf Deutsch gültig ist.

    ```syntax
    Copy C:\USB-B\configset\oobe.xml c:\oobe\info\default\1033
    ```

1.  Schließlich muss jede Sprachordner eine Datei **oobe.xml** und eine agreement.rtf-Datei in die entsprechende Sprache enthalten.

    ![Vereinbarung und OOBE Dateien](images/agreement-and-oobe-files.png)


### <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>Stellen Sie das Abbild

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) zum Bereitstellen des Abbilds. Die Kurzversion:

1.  Öffnen Sie als Administrator der Befehlszeile (**Starten** > geben **Bereitstellung** > Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

### <a name="span-idaddthelicense-filesspanadd-the-license-files"></a><span id="Add_the_license files"></span>Fügen Sie die Lizenzdateien

1.  Kopieren Sie in das Bild in die Antwortdatei der \\Windows\\System32\\Oobe\\ Ordner. Erstellen Sie den Ordner aus, wenn er nicht vorhanden ist.

    ``` syntax
    MkDir c:\mount\windows\windows\system32\oobe
    xcopy C:\oobe \c:\mount\windows\windows\system32\oobe /s
    ```

## <a name="span-idunmounttheimagesspan-unmount-the-images"></a><span id="Unmount_the_images"></span>Heben Sie die Bereitstellung der Bilder

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Übernehmen Sie das Bild, das einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, das Windows-Abbild und die Wiederherstellungsabbild anwenden, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Boot Verweis Gerät, um Windows PE mit Windows PE USB-Taste](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Die Laufwerke, auf Trennen und dann neu starten (`exit`).
    
**Überprüfen Sie die Lizenzbedingungen**

Melden Sie sich das System, als wären Sie einen neuen Benutzer. Wählen Sie Ihre Sprache oder die Region des erforderlich. Während dieser ersten Anmeldung Erfahrung sollten die richtige Lizenzbedingungen angezeigt.

Nächste Schritte: [Übung 9: Ändern von Windows (Überwachungsmodus)](prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md)