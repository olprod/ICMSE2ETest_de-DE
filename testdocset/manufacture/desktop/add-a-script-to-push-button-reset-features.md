---
author: Justinha
Description: "Sie können die Drucktaste zurücksetzen Erfahrung durch Konfigurieren Erweiterungspunkte anpassen. So können Sie benutzerdefinierte Skripts ausführen, installieren zusätzliche Applikationen oder zusätzliche Benutzer oder Anwendungsdaten beibehalten."
ms.assetid: 147358d0-bae5-4f48-b02d-1ccc48bdcc2e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen eines Skripts zu Drucktaste Reset-features"
ms.openlocfilehash: 33e585a4e4c115b340c84a3c8c32f4a676fc5894
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-script-to-push-button-reset-features"></a>Hinzufügen eines Skripts zu Drucktaste Reset-features


Sie können die Drucktaste zurücksetzen Benutzererlebnis Erweiterungspunkte konfigurieren. So können Sie benutzerdefinierte Skripts auszuführen, zusätzliche Applikationen installieren oder zusätzliche Benutzer oder Anwendungsdaten beibehalten.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Erweiterbarkeitspunkte konfigurieren sowie zum Anpassen der Drucktaste zurücksetzen wünschen, benötigen Sie Folgendes.

-   Eine Konfigurationsdatei mit dem Namen ResetConfig.xml
-   Skripts, die benutzerdefinierte Vorgänge unter Ausführen ausgewählt Erweiterungspunkte.
-   Zusätzlichen Dateien von den Skripts erforderlich

Jedes Skript muss die folgenden Anforderungen erfüllen:

-   Eine ausführbare Datei (.exe) oder ein Befehlsskript (cmd) sein
-   Führen Sie ohne graphical User Interface (GUI)
-   Zurückzugeben Sie entweder 0, um eine erfolgreiche Ausführung anzugeben, oder ein nicht-NULL-Wert an, dass ein Vorgang nicht erfolgreich

Diese Dateien gespeichert werden sollen, im Ordner C:\\Wiederherstellung\\OEM, und werden durch Drucktaste zurücksetzen Features automatisch erkannt. Es ist OK, um den Unterordner verwenden.

## <a name="span-idstep1creatingconfigurationfilestoprepareforrecoveryspanspan-idstep1creatingconfigurationfilestoprepareforrecoveryspanspan-idstep1creatingconfigurationfilestoprepareforrecoveryspanstep-1-creating-configuration-files-to-prepare-for-recovery"></a><span id="Step_1__Creating_Configuration_Files_to_Prepare_for_Recovery"></span><span id="step_1__creating_configuration_files_to_prepare_for_recovery"></span><span id="STEP_1__CREATING_CONFIGURATION_FILES_TO_PREPARE_FOR_RECOVERY"></span>Schritt 1: Erstellen von Konfigurationsdateien zur Vorbereitung der Wiederherstellung


**Zum Erstellen von Skripts Erweiterbarkeit**

-   Im Editor können Sie benutzerdefinierte Skripts zum Installieren und speichern oder Protokolldateien abgerufen werden, überprüfen Sie Partitionen erstellen.

    **Wichtige**  
    Ihre Skripts müssen die folgenden Anforderungen erfüllen:

    -   Die Skripts werden als ein cmd oder .exe-Dateien formatiert.
    -   Die Skripts sind nicht auf Windows PE optionale Komponenten in der Windows RE-Standardbild (winre.wim) nicht vorhanden abhängig.
    -   Die Skripts sind nicht für Binärdateien (z. B. .exe oder DLL-Dateien) nicht vorhanden ist, in der Windows RE-Standardbild (winre.wim) abhängig.
    -   Die Skripts ausführen, ohne dass graphical User Interface (GUI) angezeigt.
    -   Die Skripts führen Sie alle gewünschten Funktionen innerhalb von 5 Minuten für jeden Erweiterungspunkt.
    -   Das Skript muss die Laufwerkbuchstaben nicht geändert werden. Dies kann die Wiederherstellung zu einem Fehler beim potenziell verursachen.

    Skripts müssen eine 0 (null), wenn erfolgreich zurück. Wenn Drucktaste zurücksetzen auf einen Wert nicht 0 empfängt, geschieht Folgendes:

    -   **Wenn der Aktualisierung Ihrer PC-Funktion ausgeführt**: alle Systemveränderungen rückgängig gemacht werden. Wenn das Skript oder die ausführbare Datei aus dem Windows- **PC-Einstellungen** -Menü initiiert, startet das System in Windows neu. Wenn das Skript oder die ausführbare Datei aus Windows RE oder das Menü **Startoptionen** gestartet wurde, wird das System verbleibt im Windows RE und zeigt eine Fehlermeldung an.

    -   **Wenn dem Zurücksetzen Ihrer PC-Funktion ausgeführt**: der Fehler wird ignoriert. Das Skript oder die ausführbare Datei wird mit dem nächsten Schritt im Prozess zurücksetzen fortgesetzt, und den Fehler protokolliert.

    Die folgenden Speicherorte können für die Speicherung, bei Bedarf.

    -   **Windows PE-RAM-Laufwerk (x)**. Dieses virtuelle Laufwerk wird erstellt, indem Windows PE und während des Prozesses zum **Aktualisieren von Ihrem PCs** aktiv bleibt. Können Sie sie mit dem Feature zum **Aktualisieren von Ihrem PCs** Daten speichern, bevor die Partition aktualisiert wird und Informationen zum Wiederherstellen der Daten nach der Partition Aktualisierung abgeschlossen ist. Die Menge des Arbeitsspeichers verfügbar ist auf die Größe des Arbeitsspeichers auf dem System abzüglich der Menge an RAM benötigt für die Windows RE-Tools, wenn vollständig erweitert beschränkt. Anweisungen zum Bereitstellen von Windows RE, und Bestimmen der Dateigröße vollständig erweitert finden Sie unter [Windows RE anpassen](customize-windows-re.md).

    -   **Festgelegte OEM-Partition**. Sie können zusätzliche Raum auf eine Partition lassen. Sie können beispielsweise Platz auf der Wiederherstellung Bild Partition und Verwenden von Skripts zum vorübergehend weisen Sie einen Laufwerkbuchstaben, und speichern Sie die Dateien auf dieser Partition. Jedoch, wenn Ihre Benutzer Wiederherstellungsmedien Festplatten neu partitionieren verwendet wird, möglicherweise die Daten auf diesen Partitionen während des Wiederherstellungsvorgangs verloren.

     

    **In Beispiel 1: Speichern von Protokolldateien**

    Dieses Beispielskript Dateien, die andernfalls entfernt werden würde die Ausschnitte in einem temporären Verzeichnis im Speicher, von einem anderen Beispielskript abgerufen werden, behält **RetrieveLogFiles.cmd**.

    ``` syntax
    :rem == SaveLogFiles.cmd

    :rem == This sample script preserves files that would 
    :rem    otherwise be removed by placing them in a 
    :rem    temporary location in memory, to be retrieved by
    :rem    RetrieveLogFiles.cmd.

    :rem == 1. Use the registry to identify the location of
    :rem       the new operating system and the primary hard
    :rem       drive. For example, 
    :rem       %TARGETOS% may be defined as C:\Windows
    :rem       %TARGETOSDRIVE% may be defined as C:
    for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

    for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

    :rem == 2. Copy old logs to a temporary folder in memory
    mkdir X:\Temp
    xcopy %TARGETOS%\Logs\*.* X:\temp /cherkyi

    EXIT 0
    ```

    **Beispiel 2: Abrufen von Protokolldateien**

    Dieses Beispielskript Ruft die Dateien, die im Speicher von gespeichert wurden die `SaveLogFiles.cmd` Skript und wieder an das System hinzugefügt. Es führt auch ein System-Diagnose und sendet dann die Ausgabe auf Laufwerk C:\\Fabrikam-Ordner.

    ``` syntax
    :rem == RetrieveLogFiles.cmd

    :rem == This sample script retrieves the files that 
    :rem    were saved in memory by 
    :rem    SaveLogFiles.cmd,
    :rem    and adds them back to the system.
    :rem
    :rem    It also runs a system diagnostic, and sends the output
    :rem    to the C:\Fabrikam folder.


    :rem == 1. Use the registry to identify the location of
    :rem       the new operating system and the primary drive.
    :rem        
    :rem       %TARGETOS% is the Windows folder 
    :rem          (This later becomes C:\Windows)
    :rem       %TARGETOSDRIVE% is the Windows partition 
    :rem          (This later becomes C:)
    for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C
    for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

    :rem == 2. Copy the old logs to the new OS 
    :rem       at C:\Windows\OldLogs
    mkdir %TARGETOS%\OldLogs
    xcopy X:\Temp\*.* %TARGETOS%\OldLogs /cherkyi

    :rem == 3. Run system diagnostics using the
    :rem       DirectX Diagnostic tool, and save the 
    :rem       results to the C:\Fabrikam folders. ==

    mkdir %TARGETOSDRIVE%\Fabrikam
    %TARGETOS%\system32\dxdiag.exe /whql:off /t %TARGETOSDRIVE%\Fabrikam\DxDiag-TestLogFiles.txt

    EXIT 0
    ```

**Erstellen eine Konfigurationsdatei Drucktaste zurücksetzen**

1.  Erstellen Sie im Editor eine Konfigurationsdatei (ResetConfig.xml), die auf Ihre Drucktaste zurücksetzen Erweiterbarkeit Skripts verweist. Weitere Informationen zu dieser Datei finden Sie unter [ResetConfig XML-Referenz](resetconfig-xml-reference-s14.md).

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml -->
       <Reset>
          <Run Phase="BasicReset_BeforeImageApply">
             <Path>SaveLogFiles.cmd</Path>
             <Duration>4</Duration>
          </Run>      
          <Run Phase="BasicReset_AfterImageApply">
             <Path>RetrieveLogFiles.cmd</Path>
             <Duration>2</Duration>
          </Run>
          <Run Phase="FactoryReset_AfterDiskFormat">
             <Path>CheckPartitions.exe</Path>
             <Duration>2</Duration>
          </Run>
          <Run Phase="FactoryReset_AfterImageApply">
             <Path>InstallApps.cmd</Path>
             <Param>/allApps</Param>
             <Duration>2</Duration>
          </Run>
          <!-- May be combined with Recovery Media Creator
               configurations – insert SystemDisk element here -->
       </Reset>
    ```

    Wobei SaveLogFiles.cmd, RetrieveLogFiles.cmd, CheckPartitions.exe und InstallApps.cmd alle fiktive Skripts sind.

2.  Klicken Sie auf **Datei**, und klicken Sie dann auf **Speichern unter**. Im Feld **Codierung** wählen Sie **UTF-8**, und speichern Sie diese Datei unter E:\\Wiederherstellung\\RecoveryImage\\ResetConfig.xml.

    Dabei ist *E* der Laufwerkbuchstabe des einem USB-Laufwerk oder Wechselmedium. Verwenden Sie keine ANSI-Codierung.

    **Hinweis**  
    Die gleiche ResetConfig.xml-Datei können Sie um Windows zum Erstellen von Wiederherstellungsmedien zu konfigurieren. Weitere Informationen finden Sie unter [Bereitstellen von Features für Push-Button zurückgesetzt](deploy-push-button-reset-features.md).

     

## <a name="span-idbkmk4spanspan-idbkmk4spanstep-2-adding-configuration-files-and-scripts-to-the-destination-computer"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Schritt 2: Hinzufügen von Konfigurationsdateien und Skripts auf dem Zielcomputer


**So fügen Sie Ihrer Konfigurationsdateien und Skripts hinzu**

1.  Legen Sie auf dem Zielcomputer die Konfigurationsdateien USB flash-Laufwerk ein.

2.  Kopieren Sie die Konfigurationsdateien auf den Zielcomputer

    ``` syntax
    Copy E:\Recovery\RecoveryImage\* R:\RecoveryImage\*
    ```

    Dabei ist *E* der Laufwerkbuchstabe des USB flash-Laufwerk.

## <a name="span-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspanspan-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspanspan-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspansample-script-making-sure-unattendxml-layoutmodificationxml-and-oobexml-are-kept-during-a-reset"></a><span id="Sample_script__making_sure_unattend.xml__LayoutModification.xml__and_OOBE.xml_are_kept_during_a_reset"></span><span id="sample_script__making_sure_unattend.xml__layoutmodification.xml__and_oobe.xml_are_kept_during_a_reset"></span><span id="SAMPLE_SCRIPT__MAKING_SURE_UNATTEND.XML__LAYOUTMODIFICATION.XML__AND_OOBE.XML_ARE_KEPT_DURING_A_RESET"></span>Beispielskript: sicherstellen, dass unattend.xml LayoutModification.xml und OOBE.xml bleiben während einer Zurücksetzung


Einstellungen über unattend.xml Setup-Dateien erstellt wurden, noch mit LayoutModification.xml erstellt wurden, während eine systemweite Zurücksetzen noch die erste Anmeldung Info aus oobe.xml Windows-Startmenü Anpassungen nicht automatisch gespeichert. Stellen Sie sicher, dass Ihre Anpassungen gespeichert sind, die Schritte, um die unattend.xml, LayoutModification.xml und oobe.xml zu umfasst, Sichern Dateien in Place aus.

Nachfolgend finden Sie einige Beispielskripts, die zeigen, wie werden diese Einstellungen beibehalten, und setzen Sie sie wieder in die richtigen stellen.

Speichern von Kopien der unattend.xml, LayoutModification.xml, oobe.xml sowie diese zwei Textdateien, in C:\\Wiederherstellung\\OEM\\.

**ResetConfig.xml:**

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
<Reset>
  <Run Phase="BasicReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <Run Phase="FactoryReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
</Reset>
```

**EnableCustomizationsAfterRecovery.cmd:**

``` syntax
rem EnableCustomizationsAfterRecovery.cmd

rem Define %TARGETOS% as the Windows folder (This later becomes C:\Windows) 
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Define %TARGETOSDRIVE% as the Windows partition (This later becomes C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256
```

Bei mehrsprachigen Bereitstellungen verwendet OOBE.xml eine komplexere Ordnerstruktur. Es ist einfach den gesamten Ordner C: kopiert\\Wiederherstellung\\OEM und ändern Sie das Skript aus, um den gesamten Ordner kopieren:

``` syntax
xcopy "%ScriptFolder%\Info\" "%TargetOSDrive%\System32\Info\" /s
```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Nun, da Sie die Erfahrung Drucktaste zurücksetzen angepasst haben, können Sie auf die Wiederherstellung Bild Partition das Wiederherstellungsabbild für Drucktaste zurücksetzen (Install.wim) bereitstellen.

Befolgen Sie die Anweisungen im Thema [Zurücksetzen Push-Button-Features bereitstellen](deploy-push-button-reset-features.md) , um Diskpart-Skript, die Datei ResetConfig.xml und das Drucktaste zurücksetzen Recovery-Bild (install.wim) auf die Wiederherstellung Bild Partition des Ziels PC zu kopieren.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Drucktaste zurücksetzen](push-button-reset-overview.md)

[Erstellen von Medien zum Ausführen von Drucktaste Reset-Features](create-media-to-run-push-button-reset-features-s14.md)

[Bereitstellen von Drucktaste Reset-Features](deploy-push-button-reset-features.md)

[REAgentC Befehlszeilenoptionen](reagentc-command-line-options.md)

[ResetConfig XML (engl.)](resetconfig-xml-reference-s14.md)

 

 






