---
author: KPacquer
Description: "Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silo provisioning Lösungspaketen (SPPs)"
ms.assetid: 142bc507-64db-43dd-8432-4a19af3c568c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silo provisioning Lösungspaketen (SPPs)"
ms.openlocfilehash: fa139116e0771746dd8c22c2a627501951eced95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-12-add-desktop-applications-and-settings-with-siloed-provisioning-packages-spps"></a>Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silo provisioning Lösungspaketen (SPPs)

Installieren Sie Windows-desktopanwendungen und Systemeinstellungen durch das Erfassen von ihnen in Silo provisioning-Pakete (SPPs).

SPPs sind eine neue Art von Bereitstellung-Paket, das für Windows 10 1607 Version verfügbar ist. In früheren Versionen von Windows 10 würde, um diese Anwendungen zu erfassen Sie zu alle Kontakte gleichzeitig in einem einzigen provisioning Paket erfassen.  

Mit SPPs können Sie einzelne Windows-desktopanwendungen, .exe-Schreibweise Treiber und Windows-Einstellungen erfassen. Sie können dann anwenden diese auf Ihren PCs, nachdem Sie das Windows-Abbild angewendet haben. Dies bietet mehr Flexibilität für den Fertigungsprozess und reduziert die erforderliche Zeit zum Erstellen von PCs, auf denen Windows ausgeführt.    

SPPs unterstützen außerdem Sammeln von Add-On-Pakete für apps, die optionale Komponenten, wie die Anwendung von Sprachpaketen enthalten.

Nachdem Sie die SPPs anwenden, werden sie automatisch in die Wiederherstellungstools enthalten sein. 

Wenn Sie SPPs für übernehmen ein Compact OS-System, die Anwendungen SPP sind Einzelinstanz-automatisch, um Speicherplatz einzusparen.

**Notizen**

*  Um diese apps im Menü Taskleiste und Startmenü hinzuzufügen, müssen Sie die LayoutModification.xml aktualisieren und TaskbarLayoutModification.xml Dateien, die Sie zuvor hinzugefügt haben [Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste Pins](add-universal-apps-sxs.md). Neue Versionen dieser Dateien können einfach in das Bild oder auf das Zielgerät direkt kopiert werden. 

## <a name="best-practices-while-capturing-applications-use-clean-installations"></a>Bewährte Methoden beim Erfassen Applications: Verwenden von Neuinstallationen

Es wird empfohlen, dass jedes Mal Sie eine neue Anwendung für Windows desktop, erfassen Sie mit einem clean, neu installiert Windows-Abbild im Überwachungsmodus beginnen.

Sie können dazu:
*  Mithilfe der Techniken, haben Sie in den Übungseinheiten schnell Bilder auf einem Gerät anwenden
*  Verwenden von virtuellen Computern (VMs). Mit Hyper-V können Sie Erstellen eines Windows-Abbilds bereinigen, neu installiert und erstellen Sie einen Prüfpunkt. Prüfpunkte können Sie schnell wieder auf den Status clean, neu installiert aufprallen. 

## <a name="span-idprepareacopyofthedeploymentandimagingtoolsspanspan-idprepareacopyofthedeploymentandimaging-toolsspanspan-idprepareacopyofthedeploymentandimagingtoolsspanstep-1-prepare-a-copy-of-the-deployment-and-imaging-tools"></a><span id="Prepare_a_copy_of_the_Deployment_and_Imaging_Tools"></span><span id="prepare_a_copy_of_the_deployment_and_imaging Tools"></span><span id="PREPARE_A_COPY_OF_THE_DEPLOYMENT_AND_IMAGING_TOOLS"></span>Schritt 1: Vorbereiten der Bereitstellung und Imaging-Tools einer Kopie

Benötigen Sie das Windows-10, Version 1607 Version der Bereitstellung und Imaging-Tools aus der ADK ein. Dazu gehören das Tool ScanState und die neueste Version von DISM.

**Wichtige**   Überschreiben Sie nicht die vorhandenen DISM Dateien auf dem Windows PE-Abbild.

1.  Starten Sie die Bereitstellung und Imaging-Tools-Umgebung als Administrator an.

2.  Kopieren Sie aus der PC-Techniker die Bereitstellung und Imaging Tools aus Windows ADK der Speicher USB-Taste.

    ``` syntax
    CopyDandI.cmd amd64 E:\ADKTools\amd64
    ```

## <a name="span-idprepareadeviceforimagecapturespanspan-idprepareadeviceforimagecapturespanspan-idprepareadeviceforimagecapturespanstep-2-prepare-a-device-for-image-capture"></a><span id="Prepare_a_device_for_image_capture"></span><span id="prepare_a_device_for_image_capture"></span><span id="PREPARE_A_DEVICE_FOR_IMAGE_CAPTURE"></span>Schritt 2: Vorbereiten eines Geräts für die abbilderfassung

**Im Überwachungsmodus abrufen**

1.  Starten Sie den Verweis-Gerät (oder VM) ein, wenn er noch nicht gestartet wird.

2.  Wenn das Gerät auf die **Sprachen** oder dem **Wechsel zu fast abrufen** Bildschirm startet, drücken Sie **STRG + UMSCHALT + F3** , geben Sie im Überwachungsmodus.

3.  Im Überwachungsmodus aktiviert das Gerät wird neu gestartet, auf dem Desktop, und die Systemvorbereitungstool (Sysprep) wird angezeigt. Ignorieren Sie Sysprep jetzt.

4.  Erstellen Sie für virtuelle Computer einen Prüfpunkt für dieses Bild, Windows clean, neu installiert.

## <a name="span-idcaptureasettingspanspan-idcaptureasettingspanstep-3-capture-a-setting-windows-store-id"></a><span id="Capture_a_setting"></span><span id="capture_a_setting"></span>Schritt 3: Erfassen einer Einstellung (Windows Store-ID)

Über den Windows-Informationsspeicher müssen Sie enorme Chancen für Marke und Gerät Differenzierung, Umsatz Erstellung und Kundenzugriffs an. 

Windows Store-apps sind in der Mitte der Windows-10-Erfahrung. Als OEM können Sie ein ansprechenden Kundenzufriedenheit bereitstellen und Erhöhen der Marke können durch die Bereitstellung von Software und Dienste, die Ihre PCs Wert hinzu, denen Sie erstellen.

Finden Sie weitere Informationen finden Sie im [Windows Store 2016 Programmliste](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/DP-WindowsStoreOEMProgramGuide2016FinalCL.aspx) und [Apps und Store Windows Engineering Guide (WEG)](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/DP-WinEngnrngGdAppsStore.aspx).

1.  Fügen Sie eine Einstellung hinzu. Fügen Sie beispielsweise Ihre Windows Store-Programm-ID in der Windows-Registrierung:

    ein.  'Regedit' zu starten.

    b.  Navigieren Sie zu 'HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Store'.

    c.  Klicken Sie auf **Bearbeiten > Neu > Zeichenfolgenwert**.

    d.  Geben Sie je nach Typ des Vertrags, `OEMID` oder `StoreContentModifier`.

    e.  Doppelklicken Sie auf OEMID oder StoreContentModifier ein, und geben Sie im Feld **Wert**Ihrer Windows Store-Programm-ID.

2.  Erfassen Sie die Änderungen in das Silo provisioning Paket, und speichern Sie sie auf der Festplatte:

    ``` syntax
    E:\ADKTools\amd64\ScanState.exe /config:E:\ADKTools\amd64\Config_SettingsOnly.xml /o /v:13 /ppkg e:\SPPs\store.spp
    ```

    Dabei ist *E* der Laufwerkbuchstabe des USB-Laufwerk mit ScanState.

    **Optional**: Löschen der ScanState Logfile: `del C:\Scanstate.log`.

## <a name="span-idinstallandcaptureawindowsdesktopapplicationspanspan-idinstallandcaptureawindowsdesktopapplicationspanspan-idinstallandcaptureawindowsdesktopapplicationspanstep-3-install-and-capture-a-windows-desktop-application-microsoft-office"></a><span id="Install_and_capture_a_Windows_desktop_application"></span><span id="install_and_capture_a_windows_desktop_application"></span><span id="INSTALL_AND_CAPTURE_A_WINDOWS_DESKTOP_APPLICATION"></span>Schritt 3: Installieren und zum Erfassen einer Windows-desktop-Anwendung (Microsoft Office)

1.  Installieren Sie eine Windows-desktop-Anwendung. Wenn Sie beispielsweise Office 2016 installieren.

    ein.  Binden Sie auf Ihrem PC-Technikers ISO für das Bereitstellungstool von "Office v16.2 Deployment Tool for OPK\Software OEM - DVD\X21 05495 SW DVD5 Office 2016 v16.2 Deployment Tool For OEM\X21-05495.img X21 05453"

    b.  Kopieren von Dateien vom Laufwerk mit bereitgestellten USB-b (wobei E:\ ist Laufwerkbuchstaben für USB-B) E:\OfficeV16.2
    
    c.  Klicken Sie mit der Doppelklicken auf e:\Officev16.2\officedeploymenttool.exe


2.  Starten Sie eine Eingabeaufforderung.

3.  Erfassen Sie die Änderungen in das Silo provisioning-Paket, und speichern Sie sie auf der Festplatte:

    ``` syntax
    E:\ADKTools\amd64\ScanState.exe /apps:-sysdrive /o /v:13 /config:E:\ADKTools\amd64\Config_AppsOnly.xml /ppkg e:\SPPs\office16_base.spp
    ```

    Dabei ist *E* der Laufwerkbuchstabe des USB-Laufwerk mit ScanState.

    **Optional**: Löschen der ScanState Logfile: `del C:\Scanstate.log`.

4.  Wiederholen Sie den Vorgang, um ein Add-On-Paket zu erfassen. 
    Beispiel: Hinzufügen von Sprachpaketen für Office 2016. Rufen Sie diese aus dem Update für Office OPK Bild aus der Website Office OPK verbinden.
    
    1.  Installieren Sie das Sprachpaket für fr-fr.
    
    2.  Erfassen der kombinierten Dateien als ein Add-On.
        ``` syntax
        E:\ADKTools\amd64\ScanState.exe /apps:-sysdrive /o /v:13 /config:E:\ADKTools\amd64\Config_AppsOnly.xml /diff:e:\SPPs\office16_base.spp /ppkg E:\SPPs\office16_fr-fr.spp
        ```

        Das Tool Sysprep versiegelt das Gerät. Dieser Vorgang kann einige Minuten dauern. Nachdem der Vorgang abgeschlossen ist, wird das Gerät automatisch beendet.
    
    3. Weitere Add-Ons erfasst:
       -  Installieren Sie Windows und Office-app-Basis und erfassen Sie das nächste Add-on Pack.
          oder
       -  Für virtuelle Computer auf dem Prüfpunkt zurückgesetzt, das base-Paket anwenden und dann erfassen Sie das nächste Add-on Pack.

5.  Weitere apps erfasst:
    -  Installieren Sie Windows neu und dann erfassen die nächste app oder
    -  Für virtuelle Computer auf dem Prüfpunkt zurückgesetzt und dann erfasst die nächste app.

## <a name="span-idtryitoutspanspan-idtryitoutspanspan-idtryitoutspanstep-4-try-it-out"></a><span id="Try_it_out"></span><span id="try_it_out"></span><span id="TRY_IT_OUT"></span>Schritt 4: Probieren Sie es aus
    
**Wenden Sie das Abbild**

Die Schritte von [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, wenden Sie das Abbild, und starten. 

Die Kurzversion:

1.  Starten Sie den Verweis PC auf Windows PE.

2.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).

3.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install-updated.wim`.

**Anwenden der SPPs**

1.  Kopieren Sie den ADK Tools zu einem nicht entfernbar Dateispeicherort wie beispielsweise die primäre Festplatte, die nach dem Befehl ApplyImage W zugewiesen ist. 
    Kopieren die Datei an einen Speicherort nicht entfernbar vermeidet Fehler zugeordnet DISM über Wechseldatenträger installieren.
    ``` syntax
    xcopy D:\ADKTools\ W:\ADKTools\ /s
    ```

2.  Installieren Sie die Tools ADK mithilfe von **WimMountAdkSetupAmd64.exe/install/q /** **oder/q/Install WimMountAdkSetupX86.exe**.

    ``` syntax
    W:\ADKTools\amd64\WimMountAdkSetupAmd64.exe /Install /q
    ```

3.  Die SPPs gelten. In diesem Beispiel wird der Office-Basis Pack sowie zwei Language Packs: fr-fr und de-de.
    
    ```syntax
    W:\ADKTools\amd64\DISM.exe /Apply-SiloedPackage /ImagePath:W:\ /PackagePath:"e:\SPPs\store.spp" /PackagePath:"D:\SPPs\office16_base.spp" /PackagePath:"D:\SPPs\office16_fr-fr.spp" /PackagePath:"D:\SPPs\office16_de-de.spp"
    ```

    Finden Sie weitere Informationen finden Sie unter [Siloed provisioning Pakete](siloed-provisioning-packages.md). Informationen zur Syntax finden Sie unter [DISM Bild Management Command-Line Options](dism-image-management-command-line-options-s14.md). 

**Wenden Sie das Wiederherstellungsabbild**
1.  Wenden Sie das Wiederherstellungsabbild, nach dem Anwenden der SPPs:`D:\ApplyRecovery.bat`

2.  Die Laufwerke, auf Trennen und dann neu starten (`exit`).
    
**Überprüfen von apps**

1.  Nach dem Starten des PCs-Option, entweder erstellen Sie ein neues Benutzerkonto zu, andernfalls drücken Sie STRG + UMSCHALT + F3 in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

2.  Sehen Sie, wenn der Windows-desktopanwendungen und -Add-Ons installiert sind.

