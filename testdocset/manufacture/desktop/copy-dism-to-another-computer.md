---
author: Justinha
Description: "Installieren von Windows 10 mit einer früheren Version von Windows PE"
ms.assetid: 8abda3c5-0689-4a61-ae3e-7fa51c7e2028
MSHAttr: PreferredLib:/library/windows/hardware
title: "Installieren von Windows 10 mit einer früheren Version von Windows PE"
ms.openlocfilehash: 8c8eaea4a71a1979259c25b926f292f7a189a232
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="install-windows-10-using-a-previous-version-of-windows-pe"></a>Installieren von Windows 10 mit einer früheren Version von Windows PE


Einige Features von Windows 10 wie Compact OS Installation benötigen Sie die Windows-10-Version von DISM.

Sie können die neueste Version DISM im Bild Windows Vorinstallation Environment (Windows PE) enthalten oder aus einem anderen Speicherort, beispielsweise auf einen Wechseldatenträger ausführen. Wenn Sie mit Windows PE enthalten, wird er die Größe des Bilds DISM ungefähr 4 MB hinzugefügt.

Sie müssen zum Installieren und konfigurieren die Treiber für DISM, einschließlich der Treiber wimmount.sys und wofadk.sys jedes Mal Sie Windows PE starten benötigt.

**Hinzufügen von DISM in Windows PE-Abbild**

1.  Installieren Sie auf Ihrem PC-Technikers und Windows ADK für Windows 10.
2.  Mount Windows PE. Für Windows PE 3.x, binden Sie die Datei: \\Quellen\\wird. Für Windows PE 4.x und 5.x, binden Sie die Datei: \\Quellen\\boot.wim.

    ``` syntax
    md "C:\WinPE_amd64\mount"

    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

3.  Kopieren Sie den Ordner DISM von der Windows-ADK, in einen neuen Ordner im bereitgestellten Windows PE-Abbild.

    ``` syntax
    md C:\WinPE_amd64\mount\DISM

    robocopy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\DISM" C:\WinPE_amd64\mount\DISM
    ```

    **Wichtig**   Überschreiben Sie nicht die vorhandenen DISM-Dateien aus dem Ordner **system32** im Windows PE-Abbild. Stattdessen erstellen Sie einen neuen Ordner auf dem Hostcomputer zum Kopieren von Dateien in Windows ADK.

     

4.  Heben Sie die Bereitstellung einer Windows PE.

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

5.  Erstellen Sie startbare Windows PE-Medien oder Ersetzen Sie auf dem vorhandenen Wechselmedium Windows PE Bilddatei an.

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

**Installieren und Verwenden von Windows PE DISM**

1.  Ihr Zielgerät zu einer Windows PE zu starten.
2.  Installieren Sie und konfigurieren Sie DISMs erforderliche Treiber mit **WimMountAdkSetupAmd64.exe/install** oder **WimMountAdkSetupX86.exe/install**.

    ``` syntax
    X:\DISM\WimMountAdkSetupAmd64.exe /Install /q
    ```

    Für die standardmäßige (RAMDisk) Version von Windows PE müssen Sie führen Sie diesen Befehl jedes Mal Sie Windows PE starten. Informationen zum Ausführen dieses Befehls automatisch beim Start von Windows PE, finden Sie unter [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

3.  Stellen Sie sicher, dass die Windows-10-Version von DISM installiert ist.

    ``` syntax
    X:\DISM\Dism.exe /?
    ```

    Die Ausgabe zeigt die Buildnummer an, beispielsweise:

    ``` syntax
    Deployment Image Servicing and Management tool
    Version: 10.0.10122.0
    ```

4.  Führen Sie DISM-Befehlen aus den neuen Ordner.

    ``` syntax
    X:\DISM\Dism.exe /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:W: /Compact
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM unterstützte Plattformen](dism-supported-platforms.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

 

 






