---
author: kpacquer
Description: Arbeiten mit WIM MMOS Bilder
ms.assetid: c995e207-1b89-4d49-ad46-1ccc750737ec
MSHAttr: PreferredLib:/library/windows/hardware
title: Arbeiten mit Bildern WIM MMOS
ms.openlocfilehash: 1c10013a0543a8345308b166f48bb28d433ef2a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="working-with-wim-mmos-images"></a>Arbeiten mit Bildern WIM MMOS


Sie können ein Bild WIM (Windows Imaging) über vorübergehend zu einem Gerät und starten Sie das Bild im Arbeitsspeicher veränderliche ausgeführt klicken Sie dann kopieren. Diese Funktion kann verwendet werden, auf das Gerät mit MMOS-service. Weitere Informationen zu MMOS finden Sie unter [Microsoft Manufacturing OS](microsoft-manufacturing-os.md). Mit diesem Ansatz für die Wartung der Vorteil ist, müssen Sie nicht Reservieren von Speicherplatz auf der Retail OS für Code, die nur in – Wartung verwendet wird. Minimieren des Speicherplatzes, der vom Betriebssystem genutzt wird ist ein wichtiger Aspekt beim kostengünstig Geräte.

**Wichtige**  
Nur MMOS Test Bilder werden derzeit unterstützt. Retail signieren wird derzeit nicht unterstützt.

 

## <a name="span-idcreatingawimimagespanspan-idcreatingawimimagespanspan-idcreatingawimimagespancreating-a-wim-image"></a><span id="Creating_a_WIM_Image"></span><span id="creating_a_wim_image"></span><span id="CREATING_A_WIM_IMAGE"></span>Ein WIM-Abbild erstellen


Bevor Sie ein WIM-Abbild erstellt haben, müssen Sie die in den folgenden Themen beschriebenen Schritte ausführen:

[Definition der MMOS-Bild](mmos-image-definition.md)

Darüber hinaus führen Sie die folgenden Richtlinien, um ein Abbild vorbereiten, damit es ordnungsgemäß funktioniert, bei der Konvertierung in ein WIM-Abbild.

-   Das folgende XML-CODE zeigt ein Beispiel für die Microsoft-Features, die verwendet werden können in einem Test WIM-Abbild.

    ``` syntax
    <Microsoft>
      <Feature>MOBILECOREBOOTSH</Feature>
      <Feature>ENABLE_BOOT_KEYS_TEST</Feature>
      <Feature>ENABLE_IP_OVER_USB</Feature>
    </Microsoft>
    ```

    Sie können zusätzliche Features wie etwa Batterie lädt hinzufügen möchten (AKTIVIEREN\_MMOS\_LADEFEHLER) je nach Ihren Anforderungen. Zusätzliche Informationen zu den Features MMOS finden Sie unter [MMOS Bild Definition](mmos-image-definition.md).

-   Schließen Sie Pakete ein, die Zugriff auf andere Partitionen auf dem Gerät nicht. Da WIM geladen und im RAM ausgeführt wird, ist nicht auf andere Partitionen zugreifen, und das Betriebssystem keine Pakete, die anderen Partitionen verweisen enthalten.

Nachdem Sie die Schritte in den vorherigen Themen abgeschlossen haben, mithilfe des Befehls **ImgToWIM** um signierte FFU Bilds in ein WIM-Abbild zu konvertieren. Die ImgToWim ausführbare Datei befindet sich im WPDKCONTENTROOT %\\Tools\\Bin\\i386. Hier wird die Verwendung zusammengefasst.

``` syntax
ImgToWIM <FFUFileName> <WIMFileName> 
```

Bei der Eingabe des Befehls **ImgToWim** sollten Ausgabe angezeigt werden, die der folgenden ähnelt.

``` syntax
C:\TestWIM>ImgToWim MMOS.ffu MMOSWim.wim
Reading the image file: MMOS.ffu
ETW Log Path: C:\Users\USER1\AppData\Local\Temp\storage_session_1210.etl
OS Version: Microsoft Windows NT 6.2.9200.0
OpenDiskInternal: Creating empty virtual disk.
No mounted WP disks found.
Storage Service: Created a new image in 0.7 seconds.
AddAccessPath: Mount point for volume MainOS: C:\Users\USER1\AppData\Local\Temp
\oji20cvi.mq5.mnt\.

Creating WIM at 'C:\TestWIM\MMOSWim.wim' ...

Capturing 'MainOS'...
WIM creation complete.
DismountFullFlashImage:[2.87] Cleaning up temporary paths.
CleanupTemporaryPaths: Cleaning up temporary path C:\Users\USER1\AppData\Local\
Temp\oji20cvi.mq5.mnt\.
Storage Service: Dismounting the image in 2.9 seconds.
```

## <a name="span-idbootingfromawimimagespanspan-idbootingfromawimimagespanspan-idbootingfromawimimagespanbooting-from-a-wim-image"></a><span id="Booting_from_a_WIM_Image"></span><span id="booting_from_a_wim_image"></span><span id="BOOTING_FROM_A_WIM_IMAGE"></span>Starten von einer WIM-Abbild


Verwenden Sie das FFUTool **WIM** option zum Starten von einem WIM-Abbild. Hier wird die Verwendung zusammengefasst.

``` syntax
ffutool -WIM <WIMFileName.wim>
```

Gehen Sie folgendermaßen vor, um das Gerät aus ein WIM-Abbild starten.

1.  Richten Sie Seiten PC Tools blinken.

2.  Platzieren Sie das Gerät im Modus die Lautstärke Schaltfläche halten, beim Einschalten des Geräts blinken. Nachdem das Gerät im Modus blinkt ist, schließen Sie ein USB-Kabel an den Computer.

3.  Mithilfe des **FFUTool** Befehls mit der Option **WIM -** ein Gerät von einem WIM-Abbild starten. Befindet sich im WPDKCONTENTROOT %\\Tools\\Bin\\i386. Beim Eingeben der **FFUTool WIM -** Befehl sollte Ausgabe ähnlich dem folgenden angezeigt.

    ``` syntax
    C:\> ffutool -wim MMOSWim.wim
    Found device:
    Name:   Contoso.MSM8960.JD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-000000000000
    Booting WIM: MMOSWim.wim
    WIM transfer completed in 26.550073 seconds.
    ```

Der Ffutool sendet ein WIM-Opcode an das Gerät, zusammen mit Informationen über die Größe des Bilds. Weiter, die ein Puffer RAM zugewiesen wird, das Bild enthalten wird. Der Ffutool überträgt das WIM-Abbild klicken Sie dann auf das Gerät. Nachdem sie vollständig übertragen werden, startet das Gerät in der WIM-Abbild im Arbeitsspeicher.

**Hinweis**  
Die aktuellen MMOS WIM Bilder möglicherweise nicht rotierenden Disc-Grafik angezeigt, aber MMOS weiterhin funktionsfähig ist.

 

 

 





