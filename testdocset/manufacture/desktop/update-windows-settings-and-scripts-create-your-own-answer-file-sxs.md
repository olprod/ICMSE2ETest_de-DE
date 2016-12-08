---
author: Justinha
Description: "Übung 7: Einstellungen ändern, geben Sie die Product Keys und Ausführen von Skripts mit einer Antwortdatei (unattend.xml)"
ms.assetid: a29101dc-4922-44ee-a758-d555e6cf39fa
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 7: Einstellungen ändern, geben Sie die Product Keys und Ausführen von Skripts mit einer Antwortdatei (unattend.xml)"
ms.openlocfilehash: 22308f2a3cca63335fbd0bf8b6d11d9440e77be6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idaddsettingsspanlab-7-change-settings-enter-product-keys-and-run-scripts-with-an-answer-file-unattendxml"></a><span id="Add_settings"></span>Übung 7: Einstellungen ändern, geben Sie die Product Keys und Ausführen von Skripts mit einer Antwortdatei (unattend.xml)

Antwortdateien (oder Dateien für die unbeaufsichtigte Installation) können verwendet werden, um Windows-Einstellungen in Ihren Bildern während der Installation zu ändern. Sie können auch Einstellungen erstellen, die Skripts in Ihren Bildern, die auslösen nach der erste Benutzer ihr Konto erstellt und die Standardsprache wählt ausgeführt.

Weitere Informationen zu den Windows-Anpassungen finden Sie unter der [Windows 10, Version 1607 OEM Richtlinie Dokument (OPD)](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2017/Pages/DP-OPDRoyWin10v1607CL.aspx).

Als Beispiel fügen wir eine Einstellung, die automatisch starten einer Wartungsmodus Überwachungsmodus aufgerufen wird. In diesem Modus können Sie zusätzliche Tests ausführen, und erfassen die Änderungen. Wir verwenden in den nächsten Paar Übungseinheiten Überwachungsmodus aktiviert.

![Diagramm zum Erstellen einer neuen Antwortdatei](images/dep-win8-sxs-createanswerfile.jpg)

## <a name="span-idoverviewspanspan-idoverviewspanwindows-settings-overview"></a><span id="overview"></span><span id="OVERVIEW"></span>Windows-Einstellungen (Übersicht)

Während Sie viele Windows-Einstellungen im Überwachungsmodus festlegen können, können einige Einstellungen nur mithilfe einer Antwortdatei oder Windows Imaging und Konfiguration Designer (ICD), beispielsweise das Hinzufügen des Herstellers Supportinformationen festgelegt werden. Eine vollständige Liste der Antwort Datei Settings (auch bekannt als Einstellungen für die unbeaufsichtigte Installation) ist in der [Referenz für unbeaufsichtigte Windows](https://msdn.microsoft.com/library/windows/hardware/dn923277).

Unternehmen können andere Einstellungen mithilfe von Gruppenrichtlinien steuern. Weitere Informationen finden Sie unter [Group Policy](http://go.microsoft.com/fwlink/p/?linkid=268543).

Sie können angeben, welche Konfiguration Durchlauf zum Hinzufügen von neuer Einstellungen:

-   **1 WindowsPE**: Diese Einstellungen werden vom Installationsprogramm Windows Setup verwendet. Wenn Sie vorhandene Bilder ändern möchten, können Sie diese Einstellungen in der Regel ignorieren.
-   **4 specialize**: die meisten Einstellungen hier hinzugefügt werden soll. Diese Einstellungen werden sowohl am Anfang des Überwachungsmodus und am Anfang des OOBE ausgelöst. Wenn Sie mehrere Updates oder Einstellungen zu testen, verallgemeinern das Gerät erneut und einen neuen Batch Einstellungen im Durchgang Specialize Konfiguration hinzufügen müssen.
-   **6 AuditUser**: ausgeführt wird, sobald Sie starten im Überwachungsmodus.

    Hierbei handelt es sich um eine umfangreiche Zeit zum Ausführen eines Testskripts System - wir fügen [Microsoft Windows-Deployment\\RunAsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915797) als unserem Beispiel. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md).

-   **7 OobeSystem**: sparsame verwenden. Die meisten dieser Einstellungen führen Sie nach der Benutzer OOBE abgeschlossen ist. Die Ausnahme ist die Microsoft-Windows-Deployment\\Reseal\\[Mode](https://msdn.microsoft.com/library/windows/hardware/dn923110) = Audit Einstellung ab, die wir verwenden zu umgehen OOBE, und starten Sie den PC im Überwachungsmodus aktiviert.

    Wenn Ihr Skript zu wissen, welche Sprache, die der Benutzer während der OOBE auswählt nutzt, würden Sie die Pass OobeSystem hinzufügen.

-   Informationen zu den anderen Konfigurationsphasen finden Sie unter [Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md).

**Hinweis**  Diese Einstellungen konnte verloren, wenn der Benutzer ihre PC mit der integrierten Wiederherstellungstools zurückgesetzt. Gewusst wie: sicherstellen, dass diese Einstellungen auf dem Gerät während einer Zurücksetzung bleiben, finden Sie unter [Beispielskripts](windows-deployment-sample-scripts-sxs.md): nachhaltiger Schutz von Windows-Einstellungen über eine Wiederherstellung.

## <a name="span-idcreateanswerspanspan-idcreateanswerspancreate-and-modify-an-answer-file"></a><span id="createanswer"></span><span id="CREATEANSWER"></span>Erstellen und Ändern einer Antwortdatei

**Schritt 1: Erstellen einer Katalogdatei**

1.  Starten Sie **Windows System Image Manager**.

2.  Klicken Sie auf **Datei** > **Windows-Abbild auswählen**.

3.  Navigieren Sie in der **Windows-Abbild auswählen**zu, und wählen Sie die Bilddatei (D:\install.wim). Im nächsten Schritt wählen Sie eine Version von Windows, beispielsweise Windows 10 Pro, und klicken Sie auf **OK**. Klicken Sie auf **Ja** , um die Katalogdatei zu erstellen. Windows SIM erstellt die Datei auf die Bilddatei basiert, und speichert ihn im gleichen Ordner wie die Bilddatei. Dieser Vorgang kann einige Minuten dauern.

    Die Katalogdatei im **Windows-Abbild** wird angezeigt. Windows SIM Listet die konfigurierbaren Komponenten und Pakete in diesem Bild.

    **Problembehandlung:** Wenn Windows SIM die Katalogdatei nicht erstellt wird, führen Sie die folgenden Schritte aus:

    -   Um eine Katalogdatei für 32-Bit- oder ARM-basierte Geräte zu erstellen, verwenden Sie ein 32-Bit-Gerät.

    -   Stellen Sie sicher, dass Windows Base-Bilddatei **(\\Quellen\\Install.wim**) ist in einem Ordner, das über Lese-und Schreibzugriff verfügt, wie ein USB-Laufwerk oder auf der Festplatte.

**Schritt 2: Erstellen einer Antwortdatei**

-   Klicken Sie auf **Datei** > **neue Antwortdatei**.

    Die neue Antwortdatei wird im Bereich **Antwortdatei** angezeigt.

    **Hinweis**   Wenn Sie eine vorhandene Antwortdatei öffnen, werden Sie möglicherweise aufgefordert die Antwortdatei mit dem Bild zuordnen. Klicken Sie auf **Ja**.

**Schritt 3: Fügen Sie neuer Antwort dateieinstellungen hinzu**

1.  OEM-Info hinzufügen:

    Erweitern Sie im **Windows-Abbild** **Komponenten**der rechten Maustaste auf **amd64\_Microsoft-Windows-Shell-Setup\_(Version)**, und wählen Sie dann die **Einstellung hinzufügen, um Pass 4 specialize**.

    Wählen Sie im Bereich **Antwortdatei** **Komponenten\\4 specialize\\amd64\_Microsoft-Windows-Shell-Setup\_neutrale\\OEMInformation**.

    Wählen Sie im Bereich **OEMInformation Eigenschaften** im Abschnitt **Einstellungen** :
    
    -   Hersteller =`Fabrikam`
    -   Modell =`Notebook Model 1`
    -   Logo =`C:\Fabrikam\Fabrikam.bmp`
        
    Erstellen Sie eine 32-Bit-Farbe mit einer maximalen Größe von 120 x 120 Pixel, speichern Sie diese als C:\\AnswerFiles\\Fabrikam.bmp Datei auf Ihrem lokalen PC oder verwenden Sie das Beispiel aus der USB-B-Schlüssel: `C:\USB-B\ConfigSet\$OEM$\$$\System32\OEM\Fabrikam.bmp`. 
    
    Wir werden das Logo in das Windows-Abbild in einigen Schritten kopieren.

2.  Legen Sie das Gerät auf automatisch [Starten im Überwachungsmodus](https://msdn.microsoft.com/library/windows/hardware/dn923110.aspx):

    Klicken Sie im **Windows-Abbild** **-Komponenten**der rechten Maustaste auf **amd64\_Microsoft-Windows-Deployment\_(Version)**, und wählen Sie dann die **Einstellung zu Pass 7 OobeSystem hinzufügen**.

    Die **Antwortdatei** wählen Sie im Bereich **Komponenten\\7 OobeSystem\\amd64\_Microsoft Windows-Deployment\_neutrale\\Reseal**.

    Wählen Sie im Bereich **Reseal Eigenschaften** im Abschnitt **Einstellungen** Mode =`Audit`.

3.  Bereiten Sie ein [Skript](https://msdn.microsoft.com/library/windows/hardware/dn915797.aspx) zum Ausführen, nachdem im Überwachungsmodus beginnt.

    Klicken Sie im **Windows-Abbild** mit der rechten Maustaste **amd64\_ Microsoft-Windows-Deployment\_(Version)** und klicken Sie dann auf **Die Einstellung zu Pass 6 AuditUser hinzufügen**.

    Erweitern Sie im Bereich **Antwortdatei** **Komponenten\\6 AuditUser\\amd64\_Microsoft Windows-Deployment\_neutrale\\RunAsynchronous**. Mit der rechten Maustaste **RunAsynchronousCommand Eigenschaften** , und klicken Sie auf **Neue AsynchronousCommand einfügen**.

    Fügen Sie im Eigenschaftenbereich **AsynchronousCommand** , im Abschnitt **Einstellungen für** die folgenden Werte hinzu:

    `Path = C:\Fabrikam\SampleCommand.cmd`

    `Description = Sample command to run a system diagnostic check.`

    `Order = 1`

Häufiger Einstellungen: 

*  Windows ohne OEM Activation 3.0 (OA3.0) aktivieren, indem Sie [einen Product Key](https://msdn.microsoft.com/library/windows/hardware/dn915735.aspx): `Microsoft-Windows-Shell-Setup\ProductKey`. Für Unternehmen kann dies einen Volume License Product Key sein.

*  Beschleunigen der ersten Start durch [Treiberkonfigurationen, wenn das Erfassen eines Abbilds verwalten](maintain-driver-configurations-when-capturing-a-windows-image.md): `Microsoft-Windows-PnpSysprep/DoNotCleanUpNonPresentDevices`, `Microsoft-Windows-PnpSysprep/PersistAllDeviceInstalls`.

**Schritt 4: Speichern Sie die Antwortdatei**

-   Speichern Sie die Antwortdatei, zum Beispiel: **C:\\AnswerFiles\\BootToAudit x64.xml**.

    **Hinweis**   Windows SIM lässt nicht zu, dass Sie die Antwortdatei in die bereitgestellten Abbild-Ordner speichern.
     
**Schritt 5: Erstellen eines Skripts**

-   Kopieren Sie das folgende Beispielskript in Notepad ein, und speichern Sie es als **C:\\AnswerFiles\\SampleCommand.cmd**.

    ``` syntax
    @rem Scan the integrity of system files 
    @rem (Required after removing the base English language from an image)
    sfc.exe /scannow

    @rem Check to see if your drivers are digitally signed, and send output to a log file.
    md C:\Fabrikam
    C:\Windows\System32\dxdiag /t C:\Fabrikam\DxDiag-TestLogFiles.txt
    ```

## <a name="span-idaddtheanswerfileandscripttotheimagespanspan-idaddtheanswerfileandscripttotheimagespanspan-idaddtheanswerfileandscripttotheimagespanadd-the-answer-file-and-script-to-the-image"></a><span id="Add_the_answer_file_and_script_to_the_image"></span><span id="add_the_answer_file_and_script_to_the_image"></span><span id="ADD_THE_ANSWER_FILE_AND_SCRIPT_TO_THE_IMAGE"></span>Die Antwortdatei und das Skript zum Bild hinzufügen

### <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>Stellen Sie das Abbild

**Schritt 6: Bereitstellen der Bilder**

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) zum Bereitstellen des Abbilds. Die Kurzversion:

1.  Öffnen Sie als Administrator der Befehlszeile (**Starten** > geben **Bereitstellung** > Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

### <a name="span-idaddtheanswerfilespanadd-the-answer-file"></a><span id="Add_the_answer_file"></span>Fügen Sie die Antwortdatei hinzu
**Schritt 7: Hinzufügen der Antwortdatei**
2.  Kopieren Sie die Antwortdatei in das Bild in die \\Windows\\Panther-Ordner, und nennen Sie sie unattend.xml. Erstellen Sie den Ordner aus, wenn er nicht vorhanden ist. Wenn eine vorhandene Antwortdatei vorhanden ist, ersetzen Sie ihn oder Windows System Image Manager Sie bearbeiten/Einstellungen bei Bedarf kombinieren.

    ``` syntax
    MkDir c:\mount\windows\Windows\Panther
    Copy C:\AnswerFiles\BootToAudit-x64.xml  C:\mount\windows\Windows\Panther\unattend.xml
    MkDir c:\mount\windows\Fabrikam
    Copy C:\AnswerFiles\Fabrikam.bmp    C:\mount\windows\Fabrikam\Fabrikam.bmp
    Copy C:\AnswerFiles\SampleCommand.cmd    C:\mount\windows\Fabrikam\SampleCommand.cmd
    ```
## <a name="span-idunmounttheimagesspan-unmount-the-images"></a><span id="Unmount_the_images"></span>Heben Sie die Bereitstellung der Bilder

**Schritt 8: Heben Sie die Bereitstellung der Bilder**

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 9: Wenden Sie das Abbild auf einen neuen PC** Verwenden Sie die Schritte auf [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, das Windows-Abbild und die Wiederherstellungsabbild anwenden, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Boot Verweis Gerät, um Windows PE mit Windows PE USB-Taste](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Die Laufwerke, auf Trennen und dann neu starten (`exit`).
    
**Schritt 10: Überprüfen Sie, Einstellungen und Skripts**

Wenn die Einstellung für Ihre Audit gearbeitet haben, sollte der PC im automatisch Überwachungsmodus starten.  Beim Überwachen gestartet wird, das Skript sollte automatisch starten.

1.  Überprüfen, wenn im Datei-Explorer die Datei: **C:\\Fabrikam\\DxDiag TestLogFiles.txt** ist vorhanden. Wenn dies der Fall ist, werden Ihre Beispielskript ordnungsgemäß ausgeführt.

Lassen Sie den PC gestartet im Überwachungsmodus mit der folgenden Übungseinheit fortfahren:

Nächste Schritte: [Übung 9: Ändern von Windows (Überwachungsmodus)](prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md)