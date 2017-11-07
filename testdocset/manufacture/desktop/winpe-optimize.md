---
Autor: KPacquer Beschreibung: "Windows PE: Optimieren der Leistung und das Bild zu reduzieren ' ms.assetid: 5d5c13e8-8754-4fff-afd1-dcc3fb757bb9 MSHAttr: ' PreferredLib: / Bibliothek/Windows/Hardware ' Titel:" Windows PE: Optimieren der Leistung und das Bild zu reduzieren
---

# <a name="winpe-optimize-and-shrink-the-image"></a>Windows PE: Optimieren der Leistung und das Bild zu reduzieren

Startzeit Windows Vorinstallation Environment (Windows PE) um das Bild nach dem Hinzufügen von Treibern, Sprachen oder Pakete bereinigen beschleunigen.

## <a name="span-idmountthewindowspebootimagespanmount-the-windows-pe-boot-image"></a><span id="Mount_the_Windows_PE_boot_image"></span>Stellen Sie das Windows PE Boot-Abbild

``` syntax
Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
```

## <a name="span-idaddcustomizationsspanspan-idaddcustomizationsspanspan-idaddcustomizationsspanadd-customizations"></a><span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>Hinzufügen von Anpassungen

Fügen Sie [Treiber](winpe-add-drivers.md), [Pakete (optionalen Komponenten Verweis)](winpe-add-packages--optional-components-reference.md)und/oder [weitere Anpassungen vor](winpe-mount-and-customize.md).

Jedoch nicht das Bild noch aufheben.

## <a name="span-idpreparetocleantheimagespanprepare-to-clean-the-image"></a><span id="Prepare_to_clean_the_image"></span>Vorbereiten Sie auf das Bild zu bereinigen

In diesem Prozess markiert Dateien, die während des Exportvorgangs können entfernt werden. 

``` syntax
DISM /Cleanup-Image /Image="C:\WinPE_amd64\mount" /StartComponentCleanup /ResetBase 
```

## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>Heben Sie die Bereitstellung des Abbilds
    
Commit der Änderungen, und heben Sie die Bereitstellung des Windows PE-Bilds:
``` syntax
Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /Commit
```

## <a name="span-idexportandthenreplacetheimagespanexport-and-then-replace-the-image"></a><span id="Export_and_then_replace_the_image"></span>Exportieren Sie und Ersetzen Sie das Bild

Das exportierte Bild sollte kleiner als das alte Bild sein. Ersetzen Sie das ursprüngliche Bild durch den neuen. 

``` syntax
Dism /Export-Image /SourceImageFile:"c:\winpe_amd64\media\sources\boot.wim" /SourceIndex:1 /DestinationImageFile:"c:\winpe_amd64\mount\boot2.wim"
Del "C:\WinPE_amd64\media\sources\boot.wim"
Copy "C:\WinPE_amd64\mount\boot2.wim" "c:\winpe_amd64\media\sources\boot.wim"
```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

1.  Erstellen von startbaren Medien, wie ein USB-Laufwerk.

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

2.  Die Medien zu starten. Windows PE wird automatisch gestartet. Nachdem das Windows PE-Fenster angezeigt wird, wird der Befehl Wpeinit automatisch ausgeführt. Dies kann einige Minuten dauern. Überprüfen Sie die Anpassungen aus.


## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)](winpe-add-packages--optional-components-reference.md)

 

 






