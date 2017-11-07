---
author: Justinha
Description: "Informationen zum Windows-desktopanwendungen und andere Daten hinzufügen, indem Sie im Überwachungsmodus."
ms.assetid: 61e94d42-5d12-4c54-9efc-1e38ea94f750
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen einer Bereitstellung Paket mit Windows-desktopanwendungen
ms.openlocfilehash: 0ebbf9b83919bd4ce0a81f805f6dd1db8fae2acf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-provisioning-package-with-windows-desktop-applications"></a>Erstellen einer Bereitstellung Paket mit Windows-desktopanwendungen


Nachfolgend finden Sie zum Hinzufügen von Windows-desktopanwendungen und andere Daten mithilfe von Überwachungsmodus aktiviert. Mithilfe des Tools ScanState benötigen Sie diese Windows-desktop-Anwendungen und Daten in einem Paket provisioning erfassen. Als neuen Builds von Windows freigegeben werden und wie Sie für die verschiedenen Märkten vorbereiten, können Sie kombinieren und die Windows-Abbilder und Bereitstellung Pakete, statt neu erstellen und Anpassen der Bilder jedes Mal übereinstimmen.

Nachdem Sie das Bereitstellung Paket aufgenommen haben, können Sie es mithilfe von Windows ICD für das Abbild hinzufügen.

Die Wiederherstellungstools verwenden dieses provisioning Paket. Wenn Ihre Benutzer das Gerät (im Fall eines WAN-Gerät häufig verwendet) aktualisieren oder des Geräts zurücksetzen (häufig verwendet, um ein Gerät für einen neuen Benutzer zu bereinigen), behält das Gerät ihre installierten Windows-Updates sowie die Updates in dieser Bereitstellung Paket.

## <a name="span-idstep1prepareacopyofscanstatespanspan-idstep1prepareacopyofscanstatespanspan-idstep1prepareacopyofscanstatespanstep-1-prepare-a-copy-of-scanstate"></a><span id="Step_1__Prepare_a_copy_of_ScanState"></span><span id="step_1__prepare_a_copy_of_scanstate"></span><span id="STEP_1__PREPARE_A_COPY_OF_SCANSTATE"></span>Schritt 1: Eine Kopie der ScanState vorbereiten


1.  Schließen Sie auf Ihrem PC-Technikers und in ein anderes USB-Schlüssel oder Laufwerk.
2.  Im Datei-Explorer, erstellen Sie einen neuen Ordner auf dem USB-Schlüssel, zum Beispiel: **D:\\ScanState X64**.
3.  Kopieren Sie die Dateien aus **"C:\\Program Files (x86)\\Windows Kits\\10\\Assessment and Deployment Kit\\Migrationstool für den Benutzerstatus\\amd64"** in **D:\\ScanState X64**. Sie müssen nicht die Unterordner zu kopieren.
4.  Kopieren Sie die Dateien aus **"C:\\Program Files (x86)\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Setup\\amd64\\Quellen"** in **D:\\ScanState X64**. Duplizierte Dateien werden, kopieren diese Dateien überspringen soll. Sie müssen nicht die Unterordner zu kopieren.

## <a name="span-idinstalldesktopappspanspan-idinstalldesktopappspanspan-idinstalldesktopappspanstep-2-install-a-windows-desktop-application-in-audit-mode"></a><span id="installDesktopApp"></span><span id="installdesktopapp"></span><span id="INSTALLDESKTOPAPP"></span>Schritt 2: Installieren von Windows-desktop-Anwendung im Überwachungsmodus aktiviert


Verwenden Sie diese Methode zum Installieren von Windows-desktopanwendungen und die Treiber, die erfordern Installation (im Gegensatz zur INF-Schreibweise Treiber.)

1.  Installieren Sie das Bild, das in Übungseinheit 1a erstellt wurde, auf dem Gerät Verweis. Wenn das Bild bereits installiert ist, starten Sie das Gerät Verweis. Die **Sprachen** oder dem **Hi es** Bildschirm wird angezeigt.
2.  Drücken Sie **STRG + UMSCHALT + F3** Überwachungsmodus eingeben. Das Gerät wird neu gestartet, auf dem Desktop und das Systemvorbereitungstool (Sysprep) angezeigt. Sie können Sysprep schließen.
3.  Stellen Sie sicher, dass die Anpassungen aus [Lab 1a](install-windows-automatically-from-a-usb-drive-sxs.md) verfügbar sind. Dazu in den **Einstellungen** unter **System &gt; zu**, sollte angezeigt werden die technischen Support-Informationen, die Sie zuvor eingegeben werden angezeigt (Firmenname, Unterstützung Rufnummer und Support-Website).

4.  Installieren einer Windows-desktop-Anwendung-Anwendung. Beispielsweise zum Installieren von Office 2013 halten in einen USB-Schlüssel mit dem Office-Installationsprogramm, öffnen Sie die Datei-Explorer und navigieren Sie zu `oemsetup.en-us.com`. Laden Sie weitere Informationen finden Sie das Update für Office OPK Bild aus der Website Office OPK verbinden.

## <a name="span-idsavewithusmtspanspan-idsavewithusmtspanspan-idsavewithusmtspanstep-3-save-your-updates-to-a-provisioning-package"></a><span id="saveWithUSMT"></span><span id="savewithusmt"></span><span id="SAVEWITHUSMT"></span>Schritt 3: Speichern der Updates zu einem Paket Bereitstellung


**Erfassen Sie Ihre Updates in einem Paket Bereitstellung**

Schließen Sie den USB-Schlüssel mit ScanState zunächst an das Verweis-Gerät.

-   **Wenn Sie eine Kopie des Pakets für diese Bereitstellung und zu anderen Geräten bereitstellen möchten**, speichern Sie die Datei auf ein USB-Laufwerk.

    Erfassen Sie die Änderungen in der Bereitstellung Paket, und speichern Sie es auf den USB-Schlüssel.

    ``` syntax
    D:\ScanState_x64\scanstate.exe /apps /ppkg D:\Provisioning\ClassicApps.ppkg /o /c /v:13 /l:D:\ScanState.log
    ```

    *D* ist, auf dem der Buchstabe des Laufwerks mit ScanState.

   
-   **Für Build-zu-eins-Geräte**, können Sie diese Änderungen bei der Zusammenfassung und das Gerät für die sofortige Übermittlung vorbereiten. Die Änderungen provisioning Paket erfassen und speichern Sie sie als C:\\Wiederherstellung\\Anpassungen\\usmt.ppkg:

    ``` syntax
    D:\ScanState_x64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\usmt.ppkg /o /c /v:13 /l:D:\ScanState.log
    ```

## <a name="span-idstep4preparethedeviceforanenduserspanspan-idstep4preparethedeviceforanenduserspanspan-idstep4preparethedeviceforanenduserspanstep-4-prepare-the-device-for-an-end-user"></a><span id="Step_4__Prepare_the_device_for_an_end_user"></span><span id="step_4__prepare_the_device_for_an_end_user"></span><span id="STEP_4__PREPARE_THE_DEVICE_FOR_AN_END_USER"></span>Schritt 4: Vorbereiten des Geräts für Endbenutzer


-   **Für Build-zu-eins-Geräte**, das Gerät für den Endbenutzer vorbereiten: Maustaste auf **Start**, wählen Sie **das Eingabeaufforderungsfenster (Admin)**und führen Sie den folgenden Befehl:

    ``` syntax
     
    C:\Windows\System32\Sysprep\sysprep /oobe /shutdown
    ```

    Das Tool Sysprep versiegelt das Gerät. Dieser Vorgang kann einige Minuten dauern. Nachdem der Vorgang abgeschlossen ist, wird das Gerät automatisch beendet. Sie können jetzt das Gerät an den Kunden senden.

 

 





