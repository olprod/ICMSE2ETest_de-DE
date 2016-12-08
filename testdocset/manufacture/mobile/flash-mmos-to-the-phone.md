---
author: kpacquer
Description: "Flash MMOS an das Gerät"
ms.assetid: 23b741e6-ba15-4a81-a78e-9545ff62c3af
MSHAttr: PreferredLib:/library/windows/hardware
title: "Flash MMOS an das Gerät"
ms.openlocfilehash: 6c98346635cef770ea338ca673e4db45153d4349
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flash-mmos-to-the-device"></a>Flash MMOS an das Gerät


Nach Abschluss die MMOS Bild Definition kann das Bild auf das Gerät aktualisiert werden

1.  Auf der Hostseite blinken erfolgt über eine Verbindung mit WinUSB, den Treiber Microsoft Universal USB-Gerät eingerichtet. Die erforderlichen Treiber sind standardmäßig in Windows 8 und Windows 10 enthalten. In Windows 7 können die erforderlichen Treiber von Windows Update installiert werden. Wählen Sie zum Konfigurieren eines Computers für Windows 7 Installieren der erforderlichen Treiber, klicken Sie auf **Start**, geben Sie "Device Installation Settings" **Ja, dies automatisch (empfohlen)**, und klicken Sie dann auf **Speichern**.

2.  Platzieren Sie das Gerät im Modus die Lautstärke Schaltfläche halten, beim Einschalten des Geräts blinken. Nachdem das Gerät im Modus blinkt ist, schließen Sie ein USB-Kabel an den Computer.

3.  Stellen Sie sicher, dass das Gerät als *WinUSB-Gerät*im Geräte-Manager erkannt wird.

4.  Um die Ffutool, anmelden und ImageSigner Tools verwenden können, fügen Sie WPDKCONTENTROOT %\\Tools\\Bin\\i386 Ihrer **Path** -Umgebungsvariablen.

5.  Vor dem blinkt der Datei FFU auf das Gerät, müssen Sie die FFU-Datei mithilfe der folgenden Syntax in der Befehlszeile anmelden. Cat-Datei wird mit der FFU generiert, wenn Sie das Tool ImgGen verwenden.

    ``` syntax
    c:\>sign <path to cat file>
    c:\>ImageSigner SIGN <path to ffu> <path to cat file>
    ```

    Beispiel:

    ``` syntax
    c:\>sign MMOS.cat
    c:\>ImageSigner SIGN MMOS.ffu MMOS.cat
    ```

6.  Befehlszeile, führen Sie den Befehl Ffutool, der die folgende Syntax verwendet:

    ``` syntax
    c:\>ffutool -flash <path to ffu image file>
    ```

    Beispiel:

    ``` syntax
    c:\>ffutool -flash C:\MMOS\MMOS.ffu
    ```

7.  Ausgabe ähnlich der folgenden sollte angezeigt werden.

    ``` syntax
    Logging to ETL file: C:\Users\Nancy\AppData\Local\Temp\ffutool8276.etl 
    Found device: 
    Name: Contoso.DCD6000 Phone.DCD6000 
    ID: 00000045-14ca-3016-8fbe-120000000000 
    Flashing: MMOS.ffu 
    [==================================================] 100.00% 
    Transferred 157.88 MB in 50.56 seconds, overall rate 3.12 MB/s.
    ```

8.  Das Gerät wird in MMOS neu gestartet. Die Anzeige auf dem Gerät wird eine kleine rotierende Grafik angezeigt.

 

 





