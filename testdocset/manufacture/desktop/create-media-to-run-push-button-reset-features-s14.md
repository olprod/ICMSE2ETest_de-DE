---
author: Justinha
Description: "Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte"
ms.assetid: 2244bddf-8f49-41db-949a-2fbe9e224003
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte"
ms.openlocfilehash: 2164c1933902642ad544299c69956b637b9e9d18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bare-metal-resetrecovery-create-recovery-media-while-deploying-new-devices"></a>Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte


Wiederherstellungsmedien (bare-Metal-Recovery) hilft bei Windows-Gerät auf den Status Factory wiederherstellen, auch wenn der Benutzer muss die Festplatte ersetzen oder vollständig das Laufwerk bereinigen.

Sie können dieses Medien für neue Geräte einschließen, dass Sie Ihren Kunden mit demselben Windows Bilder zum Rendern der Geräte bereitstellen bereitstellen.

**Hinweis**  
-   PC Firmware/BIOS muss konfiguriert sein, damit der PC-Option vom Installationsmedium (USB-Laufwerk oder DVD-Laufwerk) gestartet werden kann.
-   Der USB-Laufwerk oder DVD-Wiederherstellungsmedien benötigen genügend Platz für das Windows-Abbild.
-   Wenn die Windows größer als 32 GB oder größer Mediums Bilder (beispielsweise 4.7GB DVDs) verwenden, müssen Sie [das Windows-Abbild über mehrere DVDs erstrecken Dateiname geteilten](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md).

 

Zum Erstellen eines startbaren USB-Laufwerks für die Wiederherstellung für eine persönliche Gerät finden Sie unter [Erstellen einer Wiederherstellung USB-Laufwerk](http://go.microsoft.com/fwlink/p/?linkid=296450).

## <a name="span-idcreatemediaspanspan-idcreatemediaspanspan-idcreatemediaspancreate-a-bootable-windows-re-image"></a><span id="CreateMedia"></span><span id="createmedia"></span><span id="CREATEMEDIA"></span>Erstellen eines startbaren Windows RE-Abbilds


Zum Erstellen der, die Sie hinzufügen können Wiederherstellungsmedien mit dem PC müssen Sie über Folgendes verfügen:

-   Ein Windows-Abbild (Install.wim). Sie können entweder das Windows-Abbild Basis oder Image-benutzerdefinierte Wiederherstellung verwenden.
-   Ein Windows RE-Tools-Abbild (Winre.wim). Sie können entweder die Basis Windows RE-Tools Image vom Windows-Abbild extrahieren oder Verwenden einer [benutzerdefinierten Windows RE-Abbild](customize-windows-re.md).

**Schritt 1: Öffnen der Bereitstellung und Imaging Tools-Umgebung**

1.  Herunterladen und Installieren von [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803).
2.  Auf Ihrem PC-Techniker: Klicken Sie auf **Starten**, und geben **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

**Schritt 2: Extrahieren Sie das Windows RE-Abbild vom Windows-Abbild**

1.  Stellen Sie das Windows-Abbild:

    ``` syntax
    md c:\mount\Windows

    Dism /Mount-Image /ImageFile:D:\sources\install.wim /Index:1 /MountDir:C:\mount
    ```

2.  Kopieren Sie das Windows RE-Abbild.

    ``` syntax
    md C:\Images

    xcopy C:\mount\Windows\System32\Recovery\winre.wim C:\Images\winre.wim /h
    ```

3.  Heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\winre /Discard
    ```

**Schritt 3: Erstellen Sie einen Ordner für Windows RE-Dateien**

1.  Erstellen Sie eine Ordnerstruktur für Windows RE, in dem Windows PE basiert:

    ``` syntax
    copype amd64 C:\resetmedia_amd64
    ```

    wobei *amd64* die Architektur des Systems ist erstellen Sie Medien für.

2.  Ersetzen der standardmäßigen Windows PE Boot-Abbild (Boot.wim) mit einer Windows RE-Tools Bild.

    ``` syntax
    xcopy C:\MyImages\winre.wim C:\resetmedia_amd64\media\sources\boot.wim /h
    ```

**Schritt 4: Hinzufügen des Windows-Abbilds**

-   Kopieren Sie das Windows-Abbild in den Arbeitsordner.

    ``` syntax
    copy D:\sources\install.wim C:\resetmedia_amd64\media\sources\install.wim
    ```

    wobei *D:\\Quellen\\install.wim* ist die Basis Windows-Abbild oder Image-Wiederherstellung angepassten Drucktaste zurücksetzen.

**Schritt 5: Optional: Hinzufügen von bare-Metal Recovery Konfiguration-Skripts**

-   Wenn Sie eine angepasste Partitionslayout verwenden, Hinzufügen von bare-Metal-Recovery Konfigurationsskripts in den Arbeitsordner unter \\Quellen. Weitere Informationen finden Sie unter [Bare-Metal zurücksetzen/Recovery: ermöglichen Sie Ihren Benutzern auf Medien erstellen](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md).

    ``` syntax
    copy E:\Recovery\RecoveryImage\ResetConfig.xml C:\resetmedia_amd64\media\sources\ResetConfig.xml

    copy E:\Recovery\RecoveryImage\ResetPartitions-UEFI.txt C:\resetmedia_amd64\media\sources\ResetPartitions-UEFI.txt
    ```

## <a name="span-idcreatebootablemediaspanspan-idcreatebootablemediaspanspan-idcreatebootablemediaspancreate-bootable-media"></a><span id="Create_bootable_media"></span><span id="create_bootable_media"></span><span id="CREATE_BOOTABLE_MEDIA"></span>Erstellen eines startbaren Mediums


**So erstellen Sie ein startbares USB-Flashlaufwerk**

1.  Installieren von Windows RE auf einem USB-Laufwerk:

    ``` syntax
    Makewinpemedia /ufd C:\resetmedia_amd64 F:
    ```

    wobei *F* der Laufwerkbuchstabe des USB flash-Laufwerk ist.

2.  Beschriftung USB flash-Laufwerk mit einen beschreibenden Namen ein:

    Klicken Sie im Datei-Explorer mit der rechten Maustaste in des Laufwerks, und wählen Sie **Umbenennen**aus, und geben Sie **Full-PC-Wiederherstellung**.

**So erstellen Sie eine startbare DVD:**

1.  Erstellen einer Bilddatei DVD:

    ``` syntax
    Makewinpemedia /iso C:\resetmedia_amd64 C:\resetmedia_amd64\RecoveryImage.iso
    ```

2.  Legen Sie eine DVD.
3.  Navigieren Sie im Datei-Explorer zu `C:\resetmedia_amd64`, mit der rechten Maustaste `RecoveryImage.iso`, und klicken Sie dann auf **CD-Abbild brennen**.

## <a name="span-idtestthebaremetalrecoveryfeaturesspanspan-idtestthebaremetalrecoveryfeaturesspanspan-idtestthebaremetalrecoveryfeaturesspantest-the-bare-metal-recovery-features"></a><span id="Test_the_bare_metal_recovery_features"></span><span id="test_the_bare_metal_recovery_features"></span><span id="TEST_THE_BARE_METAL_RECOVERY_FEATURES"></span>Testen der bare-Metal-Recovery-Funktionen


1.  Legen Sie auf einem PC mit einer leeren Festplatte die neuen Wiederherstellungsmedien.
2.  Starten des PCs, drücken Sie die Firmware Boot Menüs öffnen, und wählen Sie dann das entsprechende Boot-Gerät.
3.  Wählen Sie ein Tastaturlayout, beispielsweise **UNS**an die Menüs **Windows RE-Tools** aus.
4.  Klicken Sie auf **Problembehandlung** &gt; **Zurücksetzen von Ihrem PC** &gt; **Weiter**

    **Hinweis**  
    Wenn Sie auf einem PC testen und Sie nicht die Festplatte gereinigt haben, können Sie aufgefordert, ein Laufwerk auszuwählen. Wählen Sie Windows 10.

     

    Wählen Sie **die Laufwerke, auf Ja, Partitionieren** &gt; **nur meine Dateien entfernen** &gt; **zurückgesetzt**.

    Windows setzt den Computer mithilfe des Wiederherstellungsabbilds in den ursprünglichen Zustand zurück.

## <a name="span-idlarge-scaledeploymentspanspan-idlarge-scaledeploymentspanspan-idlarge-scaledeploymentspanlarge-scale-deployment"></a><span id="Large-Scale_Deployment"></span><span id="large-scale_deployment"></span><span id="LARGE-SCALE_DEPLOYMENT"></span>Bereitstellung im großen Umfang


Wenn Sie mit Ihrem Computer USB-Schlüssel bereitstellen, können Sie eine grundlegende Kopie der Wiederherstellungsmedien Windows auf USB erstellen, mithilfe der oben genannten Schritte. Nachdem Sie die endgültige Anpassung des Bilds durchgeführt haben, können Sie starten Sie den Computer zu Windows PE und das Bild install.wim auf Wiederherstellungsmedien USB aktualisieren.

Sie können potenziell Fertigung Zeit sparen, durch Anfügen des Windows-Abbilds auf die USB-Laufwerk, statt das gesamte Windows-Abbild Neuaufnahme. Wenn Sie dies tun, müssen Sie auch ResetConfig.xml Configuration-Elements Datei aktualisieren: `RestoreFromIndex` auf die entsprechende Indexnummer. Weitere Informationen finden Sie unter [Append ein Volume Image an eine vorhandene Bild mithilfe von DISM](append-a-volume-image-to-an-existing-image-using-dism--s14.md) und [ResetConfig XML (engl.)](resetconfig-xml-reference-s14.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bare-Metal zurücksetzen /-Recovery: Aktivieren Sie Ihre Benutzer zum Erstellen von Medien](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md)

[Übersicht über die Drucktaste zurücksetzen](push-button-reset-overview.md)

[ResetConfig XML (engl.)](resetconfig-xml-reference-s14.md)

[Befehlszeilenoptionen für REAgentC](reagentc-command-line-options.md)

 

 






