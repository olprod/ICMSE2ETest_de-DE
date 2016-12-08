---
author: Justinha
Description: Reparieren eines Windows-Abbilds
ms.assetid: 4ca60b08-6801-4af4-a504-3e88ec0c8fb8
MSHAttr: PreferredLib:/library/windows/hardware
title: Reparieren eines Windows-Abbilds
ms.openlocfilehash: 52018e0c3885bdbaa78e35246300e093d54297f4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="repair-a-windows-image"></a>Reparieren eines Windows-Abbilds


Ein Windows-Abbild mithilfe von DISM zu reparieren. Sie können offline-Windows-Abbild in einer WIM oder VHD-Datei oder ein online Windows Bild reparieren. Schwelle Windows online versucht ebenfalls zu reparieren, wenn diese nicht verarbeitbare wird. Die Quelle reparieren für diesen Vorgang ist die dieselbe Datenquelle, die für Features bei Bedarf verwendet wird und hängt von Gruppenrichtlinien. Weitere Informationen finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md). Wenn Sie das Tool DISM zum Reparieren eines Abbilds online oder offline verwenden, können Sie das *Argument/Source* mit dem Argument */RestoreHealth* verwenden, zum Angeben von zusätzlichen Reparatur Source Speicherorten zu verwenden, um nach der erforderlichen Dateien zu suchen.

Für eine schnelle Überprüfung der Schwelle online, können Sie möglicherweise den Befehl verwenden: `sfc /scannow` zum Scannen und Reparieren von Dateien.

Verwenden Sie für eine umfangreichere Überprüfung, die Probleme mit dem Informationsspeicher reparieren kann, `DISM /Cleanup-Image`.

**Überprüft, ob ein Bild repariert werden kann.**

1.  Das Bild, das prüfen, ob eine Beschädigung überprüft. Diesem Vorgang wird einige Minuten dauern. Geben Sie beispielsweise den folgenden Befehl an einer Eingabeaufforderung ein:

    ``` syntax
    Dism /Online /Cleanup-Image /ScanHealth
    ```

2.  Überprüfen Sie das Bild, um festzustellen, ob Schäden erkannt wurde. Beispielsweise an einer Eingabeaufforderung, geben Sie Folgendes ein:

    ``` syntax
    Dism /Online /Cleanup-Image /CheckHealth
    ```

Wenn Sie das */CheckHealth* sfc-Argument verwenden, meldet das Tool DISM, ob das Bild fehlerfrei, repariert werden oder nicht repariert wird. Wenn das Bild nicht repariert werden, sollten Sie das Bild verwerfen und erneut starten. Wenn das Bild repariert werden kann, können Sie das Argument */RestoreHealth* verwenden, um das Bild zu reparieren.

**Zum Reparieren eines Bilds**

-   Verwenden Sie das Argument */RestoreHealth* , um das Bild zu reparieren. Geben Sie beispielsweise den folgenden Befehl zum Reparieren einer offline-Abbild mit einem bereitgestellten Abbild als Quelle reparieren, an einer Eingabeaufforderung ein:

    ``` syntax
    Dism /Image:C:\offline /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows
    ```

    Oder geben Sie zum Reparieren von Schwelle online Verwendung einiger Ihrer eigenen Datenquellen anstelle von Windows Update:

    ``` syntax
    Dism /Online /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows /LimitAccess
    ```

    Wenn Sie eine */source/Source* für die Dateien Reparatur nicht angeben, wird der Standardspeicherort für Features bei Bedarf verwendet. Weitere Informationen finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md). Wenn Sie mehrere */source/Source*angeben, werden die Dateien aus dem ersten Speicherort kopiert, auf dem sie sind vorhanden und der Rest der Speicherorte werden ignoriert. */LimitAccess* können Sie verhindern, dass das Tool DISM mithilfe von Windows Update als Quelle reparieren oder als Quelle backup Reparatur online von Bildern.

## <a name="span-idrepairingimagesduringservicingspanspan-idrepairingimagesduringservicingspanspan-idrepairingimagesduringservicingspanrepairing-images-during-servicing"></a><span id="Repairing_images_during_servicing"></span><span id="repairing_images_during_servicing"></span><span id="REPAIRING_IMAGES_DURING_SERVICING"></span>Reparieren von Bildern während der Wartung


In einigen Fällen kann ein Bild beim ändern es mit DISM beschädigt werden. Verwenden Sie */Cleanup-MountPoints* um zu reparieren. Mit diesem Befehl wird nicht deaktiviert werden Bilder, die bereits bereitgestellt werden, noch werden Bilder, die mithilfe des Befehls /Remount-Image wiederhergestellt werden können gelöscht werden.

``` syntax
Dism /Cleanup-Mountpoints
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Verwenden Sie das Tool Systemdatei zur Reparatur fehlt oder ist beschädigt](http://go.microsoft.com/fwlink/p/?LinkId=717888)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[Konfigurieren einer Windows-Reparatur-Quelle](configure-a-windows-repair-source.md)

 

 






