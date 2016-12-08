---
author: Justinha
Description: "Bereitstellen von Windows, die werksseitige schneller mithilfe das Bildformat vollständige Flash Update (FFU)."
ms.assetid: af2b402f-9a5c-4c6a-8852-61039e5bec2a
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bereitstellen von Windows mithilfe der vollständigen Flash Update (FFU)"
ms.openlocfilehash: db7953b314c6da60b14fbb3cf28d6ebee47a05b5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-using-full-flash-update-ffu"></a>Bereitstellen von Windows mithilfe der vollständigen Flash Update (FFU)


Bereitstellen Sie Windows schneller werksseitige mithilfe das vollständigen Flash Update (FFU) Bildformat.

Mit FFU-Bilder können Sie ein Windows-Abbild direkt auf einem Laufwerk oder einer SD-Karte Festlegung des gesamten Laufwerks gleichzeitig, einschließlich der Partitionsinformationen anwenden.

Zum Erstellen und Anwenden von Abbildern, können Sie [Windows Imaging und Konfiguration Designer (ICD)](https://msdn.microsoft.com/library/windows/hardware/dn916112.aspx)verwenden. Sie können auch die Windows-10-Version von DISM anzuwendende FFU Bilder, die in der Windows-10-Version von Windows Vorinstallation Environment (Windows PE) enthalten ist.

Nach dem Erstellen eines Abbilds FFU werden nicht es geändert oder offline bearbeitet.

Um Compact OS mit einem Bild FFU verwenden, müssen Sie das ursprüngliche FFU Bild als komprimierten Bild vorbereiten.

FFU Bilder sind häufig zu groß auf einem standard Windows PE FAT32 formatierten USB flash-Laufwerk. Um dieses Problem umgehen können entweder einen separaten Laufwerk oder im Netzwerk Speicherort, oder Sie können das Bild in kleinere teilen. SFU-Dateien.

## <a name="span-idusingffusspanspan-idusingffusspanspan-idusingffusspanusing-ffus"></a><span id="Using___FFUs"></span><span id="using___ffus"></span><span id="USING___FFUS"></span>Verwenden von FFUs


**So erstellen Sie ein Abbild FFU**

1.  Öffnen Sie auf Ihrem PC Techniker Windows ICD und erstellen Sie das Projekt.
2.  Schließen Sie ein USB-Laufwerk, und notieren Sie den Laufwerkbuchstaben (Beispiel: D:).
3.  Klicken Sie auf **Erstellen** &gt; **Produktion Media** &gt; **FFU** &gt; **OS Dateikomprimierung aktivieren:** (**Ja** oder **Nein**)&gt; nennen Sie die Datei, z. B. D:\\install.ffu &gt; **Erstellen**.

**Zum Bereitstellen von Windows direkt auf einer SD-Karte oder Wechseldatenträger**

1.  Windows-ICD, klicken Sie auf **Deploy** &gt; (entweder **zu USB-Gerät angeschlossen** oder **Wechseldatenträger**) &gt; **Durchsuchen** &gt; suchen das Bild FFU &gt; **Weiter** &gt; wählen Sie aus der SD-Karte oder das Gerät &gt; **Weiter** &gt; **Flash**.
2.  Wenn Sie auf SD-Karten bereitstellen, dann nach dem die blinkende abgeschlossen ist, legen Sie SD-Karte in Ihr Zielgerät.

**Zum Bereitstellen von Windows aus Windows PE**

1.  Ihr Zielgerät zu einer Windows PE zu starten.
2.  Verbinden Sie einer Speicherlaufwerk oder einem Speicherort im Netzwerk, und notieren Sie der Buchstabe des Laufwerks, z. B. N.

    ``` syntax
    net use N: \\server\share
    ```

3.  Identifizieren Sie das Laufwerk, auf den Sie das Bild anwenden können. Sie können verwenden Diskpart oder [Hinzufügen von Windows PowerShell-Unterstützung zu einer Windows PE](winpe-adding-powershell-support-to-windows-pe.md) und [Get-Datenträger](https://technet.microsoft.com/library/hh848657.aspx) für Scriptability und komplexere Setupprogrammen wie ein Server mit mehreren Datenträgern. 

    ``` syntax
    diskpart 
    list disk
    exit
    ```

4.  Wenden Sie das Abbild auf einem Laufwerk. Für ein physisches Laufwerk *X:*sollte die Zeichenfolge der folgenden Form: "\\\\. \\PhysicalDrive*X*", wobei *X* der Anzahl der Datenträger, Diskpart bietet, wie \\ \\. \\PhysicalDrive0. Festplatte Seitenzahlen beginnen bei 0 (null). Weitere Informationen zu PhysicalDrive*X*finden Sie unter [CreateFile-Funktion](https://msdn.microsoft.com/library/windows/desktop/aa363858.aspx).
    
    Weitere Informationen zu /SkipPlatformCheck finden Sie unter [/Apply-Image in DISM Bild Management-Befehlszeilenoptionen](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/dism-image-management-command-line-options-s14#apply-image) 

    ``` syntax
    DISM /Apply-Image /ImageFile:N:\flash.ffu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

**Mit einem einzigen Laufwerk für Windows PE und Schwelle FFU**

1.  Das Bild FFU in kleineren Dateien aufgeteilt:

    ``` syntax
    DISM.exe /Split-Image /ImageFile:flash.ffu /SFUFile:flash.sfu /FileSize:3500
    ```

2.  Kopieren Sie die Dateien der WinPE USB-Taste.
3.  Ihr Zielgerät zu einer Windows PE zu starten.
4.  Identifizieren der Buchstabe des Laufwerks Windows PE, beispielsweise E.

    ``` syntax
    diskpart
    list volume
    ```

5.  Klicken Sie im Menü Diskpart identifizieren das Laufwerk, dem Sie werden des Abbilds, beispielsweise anwenden benötigen \\ \\. \\PhysicalDrive0.

    ``` syntax 
    list disk
    exit
    ```

6.  Wenden Sie das Abbild auf einem Laufwerk.

    ``` syntax
    DISM.exe /Apply-Image /ImageFile:E:\flash.sfu /SFUFile:flash*.sfu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

**Verwenden eine vorherige Version von Windows PE**

1.  Schließen Sie in einem WinPE USB-Schlüssel, und notieren Sie der Buchstabe des Laufwerks, beispielsweise E.
2.  Fügen Sie die Windows-10-Version von DISM mit dem Windows PE-Laufwerk ein. Finden Sie weitere Informationen finden Sie unter [DISM auf einen anderen Computer kopieren](copy-dism-to-another-computer.md).

    ``` syntax
    copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\DISM" E:\DISM_Win10 /s
    ```

3.  Starten Sie das Zielgerät mit dem Windows PE USB-Schlüssel.
4.  Identifizieren der Buchstabe des Laufwerks, auf dem die FFU gespeichert ist, beispielsweise E.

    ``` syntax
    diskpart
    list volume
    ```

5.  Klicken Sie im Menü Diskpart identifizieren das Laufwerk, auf die Sie werden des Abbilds, beispielsweise anwenden benötigen \\ \\. \\PhysicalDrive0.

    ``` syntax
    list disk
    exit
    ```

6.  Installieren Sie die Windows-10-Version von DISM.

    ``` syntax
    E:\DISM_Win10\WimMountAdkSetupAmd64.exe /Install /q
    ```

7.  Wenden Sie das Abbild auf einem Laufwerk.

    ``` syntax
    E:\DISM_Win10\DISM.exe /Apply-Image /ImageFile:E:\flash.sfu /SFUFile:E:\flash*.sfu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows Imaging und Konfiguration-Designer](https://msdn.microsoft.com/library/windows/hardware/dn916113)

[FFU Bildformat](../mobile/ffu-image-format.md)

[WIM im Vergleich zu VHD im Vergleich zu FFU: Bilddateiformate vergleichen](wim-vs-ffu-image-file-formats.md)

[Planen einer Strategie für die Multicast im Konfigurations-Manager](http://go.microsoft.com/fwlink/?LinkId=286313)

[Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[CreateFile-Funktion](https://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)

 




