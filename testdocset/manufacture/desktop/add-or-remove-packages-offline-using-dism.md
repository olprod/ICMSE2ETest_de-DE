---
author: Justinha
Description: "Hinzufügen oder Entfernen von Paketen mithilfe von DISM Offline"
ms.assetid: 32785116-e5ed-40ae-8802-9c2a67cd9938
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen oder Entfernen von Paketen mithilfe von DISM Offline"
ms.openlocfilehash: f69aa01e5dad324751a015e6f246ec41a018cbf8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-or-remove-packages-offline-using-dism"></a>Hinzufügen oder Entfernen von Paketen mithilfe von DISM Offline


Bereitstellung Bild Wartung und Verwaltung (DISM.exe) ist ein Befehlszeilentool, das zum Aktualisieren der offline Windows® Bilder verwendet wird. Es gibt zwei Methoden zum Installieren oder Deinstallieren von Paketen im Offlinemodus mit DISM. Sie können entweder eine unbeaufsichtigte Installation Antwortdatei auf offline-Abbild anwenden, Sie hinzufügen oder entfernen Sie das Paket direkt über die Befehlszeile.

Wenn Sie mehrere Pakete ein Windows-Abbild installieren und Abhängigkeit Anforderungen vorhanden sind, ist die beste Möglichkeit, um sicherzustellen, dass die richtige Reihenfolge der Installation mithilfe einer Antwortdatei. DISM können die Antwortdatei auf das Bild anwenden. Wenn Sie DISM zum Anwenden einer Antwortdatei verwenden, werden die Einstellungen für die unbeaufsichtigte Installation im Durchgang **OfflineServicing** Konfiguration auf dem Windows-Abbild angewendet.

Installieren Sie die neueste Version von Windows Assessment and Deployment Kit (Windows ADK), die alle Tools, die erforderlich sind enthält, einschließlich DISM sind.

## <a name="to-add-packages-to-an-offline-image-by-using-dism"></a>So ein offline-Abbild mithilfe von DISM Pakete hinzu

1.  Bei einer Eingabeaufforderung mit erhöhten Rechten suchen nach dem Wartung ADK Windows-Ordner, und geben Sie den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die Bilddatei festlegen.

2.  Geben Sie den folgenden Befehl zum Bereitstellen von offline-Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

3.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein bestimmtes Paket das Bild hinzugefügt. Sie können mehrere Pakete über eine Befehlszeile hinzufügen. Sie werden in der angegebenen Reihenfolge aus, in der Befehlszeile installiert werden.

    ``` syntax
    Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab
    ```

4.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, und heben Sie die Bereitstellung des Abbilds commit der Änderungen.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-remove-packages-from-an-offline-image-by-using-dism"></a>So entfernen Sie mithilfe von DISM Pakete aus ein offline-Abbild

1.  Suchen Sie an einer Eingabeaufforderung mit erhöhten Rechten den Wartung ADK Windows-Ordner, und geben Sie den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine Bilddatei angeben.

2.  Geben Sie den folgenden Befehl zum Bereitstellen der offline-Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

3.  Optional: Geben Sie den folgenden Befehl aus, um die Pakete im Abbild aufzulisten.

    ``` syntax
    Dism /Image:C:\test\offline /Get-Packages
    ```

    Sie können `>featurelist.txt` zur Umleitung von der Ausgabe des Befehls an eine Textdatei mit dem Namen Komponentenliste.

4.  Überprüfen Sie die Liste der Pakete, die im bereitgestellten Abbild verfügbar sind, und beachten Sie die Paketidentität des Pakets.

5.  Geben Sie an einer Eingabeaufforderung die Paketidentität um es aus dem Bild gelöscht. Sie können mehrere Pakete über eine Befehlszeile entfernen.

    ``` syntax
    DISM /Image:C:\test\offline /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0 /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~x86~~6.1.6801.0
    ```

    So zeigen Sie auf die ursprüngliche Quelle des Pakets oder um den Pfad zu der CAB-Datei anzugeben, verwenden Sie die **Option/PackagePath** können, oder **Sie können verwenden, das Paket mit Namen anzugeben, wie es im Bild aufgeführt ist** . Weitere Informationen finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

6.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, und heben Sie die Bereitstellung des Abbilds commit der Änderungen.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-add-or-remove-packages-offline-by-using-dism-and-an-answer-file"></a>Zum Hinzufügen oder Entfernen von Paketen im Offlinemodus mithilfe von DISM und einer Antwortdatei

1.  Windows System Image Manager zu öffnen.

2.  Um ein neues Paket hinzuzufügen, klicken Sie im Hauptmenü auf **Einfügen** , und wählen Sie **Pakete**aus. Navigieren Sie zu dem Paket, den, das Sie hinzufügen möchten, und klicken Sie dann auf **Öffnen**.

3.  Um ein vorhandenes Paket zu entfernen, wählen Sie das Paket im Bereich **Antwortdatei** , den Sie entfernen möchten. Ändern Sie im **Eigenschaftenbereich** die **Action** -Eigenschaft zu **Entfernen**.

    **Hinweis**  
    Übergeben Sie die **OfflineServicing** Konfiguration müssen die Pakete hinzugefügt werden.

4.  Überprüfen Sie, und speichern Sie die Antwortdatei.

5.  Bei einer Eingabeaufforderung mit erhöhten Rechten suchen nach dem Wartung ADK Windows-Ordner, und geben Sie den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie bereitstellen möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

6.  Geben Sie den folgenden Befehl zum Bereitstellen von offline-Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine Bilddatei angeben.

7.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl die Antwortdatei auf das Bild anwenden.

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

8.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, und heben Sie die Bereitstellung des Abbilds commit der Änderungen.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

Weitere Informationen zu Windows SIM finden Sie unter [Technische Referenz zu Windows Setup](windows-setup-technical-reference.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[DISM unbeaufsichtigtes Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

 

 






