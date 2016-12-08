---
author: Justinha
Description: "Hinzufügen der Unterstützung mehrerer Sprachen zu Windows Setup"
ms.assetid: 242b963c-79fc-450b-90d7-c736965797b7
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen der Unterstützung mehrerer Sprachen zu Windows Setup"
ms.openlocfilehash: f29a6619203d76892aa3f12add2f6fe3c9ca6de0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-multilingual-support-to-windows-setup"></a>Hinzufügen der Unterstützung mehrerer Sprachen zu Windows Setup

Windows Setup mehrsprachige Unterstützung können Sie verschiedene Sprachen für Windows Setup und Windows-Installation auswählen. Dieses Szenario ermöglicht einen Techniker Windows Setup in einer Sprache ausführen, und installieren Sie Windows in einer anderen Sprache. 

In dieser exemplarischen Vorgehensweise werden die Schritte zum Erstellen von Windows-Installationsmedium mit Unterstützung mehrerer Sprachen. 

## <a name="prerequisites"></a>Voraussetzungen


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Technikercomputer, der auf dem Windows Assessment and Deployment Kit (Windows ADK) installiert ist

-   Windows-Installationsmedium für alle Sprachen, dass Sie Medien erstellen

-   Das Windows-Sprachpaket ISO


## <a name="step-1-prepare-your-environment"></a>Schritt 1. Vorbereiten der Umgebung 

Kopieren Sie Sie zuerst Windows-Installationsdateien von Medien in ein lokales Verzeichnis. Wenn Sie Medien für die Verwendung mit einer angepassten Abbilds erstellen, müssen Sie die Windows Media verwenden, die die Version des benutzerdefinierten Abbilds entspricht. Wenn Sie ein benutzerdefiniertes Windows 10 Setup Bild erstellen, müssen Sie die ursprüngliche Windows 10 Produktmedium verwenden.

-   Erstellen Sie ein neues Verzeichnis für die Windows-Verteilung und kopieren Sie die Windows Media-Inhalten in das Verzeichnis, auf dem Referenzcomputer. Beispiel:

    ``` syntax
    md C:\my_distribution
    xcopy /E D: C:\my_distribution
    md C:\mount\boot 
    md C:\mount\windows
    ```

    *D:* ist der Speicherort des Windows-Produktmedium.

## <a name="step-2-customize-languages-available-for-windows-setup"></a>Schritt 2. Anpassen von Sprachen für das Setup für Windows verfügbar
In diesem Abschnitt veranschaulicht die Sprachen anpassen, die für einen Techniker zur Verfügung stehen, wenn Sie eine Windows-Installation ausführen.

### <a name="add-windows-pe-setup-language-packs-to-the-default-boot-image"></a>Das Standardbild Boot Windows PE Setup-Sprachpaketen hinzufügen

In diesem Schritt fügen Sie auf das zweite Abbild (Index 2) in der standardmäßigen Boot.wim sprachunterstützung und optionalen Komponenten Windows Setup.

1.  Auf Ihrem PC-Techniker: Klicken Sie auf **Starten**, und geben **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Stellen Sie das zweite Abbild (Index 2) in Boot.wim auf einem lokalen Bereitstellungsverzeichnis **Dism /Mount-Image**verwenden. Beispiel:

    ``` syntax
    Dism /mount-image /imagefile:C:\my_distribution\sources\boot.wim /index:2 /mountdir:C:\Mount\boot
    ```

3.  Fügen Sie optionale Komponente Windows PE Setup und Language Packs in bereitgestellten Abbild mithilfe von **Dism/Add-Package** für jede Sprache, die Sie unterstützen möchten. Hinzufügen von *lp.cab*, *Windows PE-Setup_\<Sprache > CAB*, und *Windows PE-Setup-Client_\<Sprache > CAB* für jede Sprache, die Sie hinzufügen.

    Windows PE-Sprachpakete sind in der Windows-ADK verfügbar.

    Beispiel:

    ``` syntax
    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-Client_fr-fr.cab"
    ```

    **Wichtige**  
    Für Windows Server 2016 müssen Sie Windows PE-Setup – Server optionalen Komponenten anstelle der optionalen Komponenten Windows PE-Setup-Client verwenden.

     
4.  Für Japanisch (ja-JP), Koreanisch (Ko-KR) und Chinesisch (Zh-HK, Zh-CN, Zh-TW) müssen Sie zusätzliche Schriftart Unterstützung für das Abbild hinzuzufügen. Geben Sie beispielsweise Folgendes ein, um die Unterstützung für japanische Schriftarten hinzuzufügen:

    ``` syntax
    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-FontSupport-JA-JP.cab"
    ```


## <a name="step-3-customize-the-languages-available-in-windows"></a>Schritt 3. Anpassen der verfügbaren Sprachen in Windows

### <a name="add-language-packs-to-the-windows-image"></a>Hinzufügen von Sprachpaketen auf den Windows-Abbild

**Sie müssen die gleichen sprachunterstützung hinzufügen zu Ihrer Windows-Bilddatei install.wim, als Sie für die Datei boot.wim haben.** Der Setup-Vorgang erfordert, dass beide Bilder den gleichen Satz von Sprachpaketen enthalten. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Language Packs Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md).

1.   Stellen Sie das Windows-Abbild mithilfe von DISM

        ``` syntax
        Dism /mount-image /imagefile:C:\my_distribution\sources\install.wim /index:1 /mountdir:C:\mount\windows    
        ```
        Dabei ist *1* der Index des Bilds, das Sie bereitstellen möchten.

2.   Fügen Sie einen oder mehrere Sprachpakete auf dem Windows-Abbild.

        ``` syntax
        Dism /image:C:\mount\windows /add-package /packagepath:F:\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
        ```

        Dabei steht *F:* den Speicherort des ISO-Sprachpakets.

Der gleiche Satz von Sprachen muss auch auf das Bild Windows Recovery Environment (winre.wim) hinzugefügt werden. Weitere Informationen finden Sie unter [Windows RE anpassen](customize-windows-re.md).

## <a name="step-4-add-localized-windows-setup-resources-to-the-windows-distribution"></a>Schritt 4: Hinzufügen von lokalisierten Windows Setupressourcen für die Windows-Verteilung


In diesem Schritt kopieren Sie die Liste der sprachspezifischen Setupressourcen von jeder Sprache bestimmtes Windows-Verteilung in den Ordner Datenquellen in die Windows-Verteilung. Beispielsweise legen Sie die Windows-DVD für Fr-FR in das DVD-Laufwerk (e), und kopieren Sie Quellordners Fr-FR in die Windows-Verteilung.

-   Kopieren Sie die lokalisierten Windows Setup-Dateien in die Windows-Verteilung.

    ``` syntax
    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    ```

    Dabei ist *E:* den Speicherort des Windows-Installationsmedium, die Sie Windows-Setup die lokalisierten Ressourcen enthält.

## <a name="step-5-recreate-the-langini"></a>Schritt 5: Erstellen der Lang.ini neu.

In diesem Schritt erstellen Sie die Lang.ini-Datei erneut und die Standardeinstellungen für die Sprache angeben.

1.  Erstellen Sie die *Dism/Gen-LangINI*mit zusätzlichen Sprachen aktualisiert die Lang.ini-Datei erneut.

    ``` syntax
    Dism /image:C:\mount\windows /gen-langINI /distribution:C:\my_distribution
    ```

2.  Ändern Sie die Standardsprache Windows Setup mit DISM. Beispiel:

    ``` syntax
    Dism /image:C:\mount\windows /Set-SetupUILang:fr-FR /distribution:C:\my_distribution
    ```

    Weitere Informationen zum Angeben der verschiedenen internationalen Einstellungen für das Gebietsschema und andere Elemente finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

3.  Kopieren Sie die lang.ini-Datei in der Windows-Verteilung der Datei boot.wim.

    ``` syntax
    Xcopy C:\my_distribution\sources\lang.ini C:\mount\boot\sources\lang.ini
    ```

## <a name="step-6-commit-the-changes-to-the-windows-images"></a>Schritt 6: Commit der Änderungen an der Windows-Bilder


In diesem Schritt übernehmen Sie die Änderungen auf alle Bilder, die Sie aktualisiert haben

-   Mithilfe von DISM heben Sie die Bereitstellung und die Änderungen in der Windows- und Boot Bilder zu übernehmen.

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\boot /commit 
    Dism /unmount-image /mountdir:C:\mount\windows /commit
    ```

## <a name="step-7-create-a-boot-order-file-optional"></a>Schritt 7: Erstellen einer Datei für die Startreihenfolge (Optional)


In diesem Schritt erstellen Sie eine Datei für die Startreihenfolge. Aufgrund der Größe des Bilds müssen Sie dies tun, bevor Sie eine ISO-Datei erstellen.

-   Erstellen Sie eine Datei für die Startreihenfolge (bootorder.txt). Beispiel:

    ``` syntax
    Oscdimg -m -n -yo C:\temp\bootOrder.txt -bC:\winpe_amd64\Efisys.bin C:\winpe_amd64\winpeamd64.iso
    ```

    Bootorder.txt enthält, in der folgenden Liste der Dateien:

    ``` syntax
    boot\bcd
    boot\boot.sdi
    boot\bootfix.bin
    boot\bootsect.exe
    boot\etfsboot.com
    boot\memtest.efi
    boot\memtest.exe
    boot\en-us\bootsect.exe.mui
    boot\fonts\chs_boot.ttf
    boot\fonts\cht_boot.ttf
    boot\fonts\jpn_boot.ttf
    boot\fonts\kor_boot.ttf
    boot\fonts\wgl4_boot.ttf
    sources\boot.wim
    ```

## <a name="next-steps"></a>Nächste Schritte


Das multilingual Bild können jetzt erstellen Medien für die Verteilung. Startbare Medien erstellen wie ein USB-Laufwerk, finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md). Sie können auch eine startbare CD oder DVD erstellen. Allerdings müssen aufgrund der Größe eines mehrsprachigen Bilds, Sie zuerst eine Datei für die Startreihenfolge erstellen vor der Erstellung einer Datei startbaren Abbild (ISO) auf CD oder DVD. Weitere Informationen finden Sie unter [Oscdimg Command-Line Options](oscdimg-command-line-options.md).

## <a name="related-topics"></a>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md)

[Oscdimg Befehlszeilenoptionen](oscdimg-command-line-options.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

 

 






