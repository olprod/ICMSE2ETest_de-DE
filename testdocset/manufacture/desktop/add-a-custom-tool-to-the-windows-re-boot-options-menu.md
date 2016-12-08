---
author: Justinha
Description: "Ein benutzerdefiniertes Tool zum Menü Optionen Boot Windows RE hinzufügen"
ms.assetid: 474958cf-91bc-4c5c-8afd-22865e9bf4a5
MSHAttr: PreferredLib:/library/windows/hardware
title: "Ein benutzerdefiniertes Tool zum Menü Optionen Boot Windows RE hinzufügen"
ms.openlocfilehash: 2de8eadb2bff460a1bf69f7a6cbf55e5d2190b2d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-custom-tool-to-the-windows-re-boot-options-menu"></a>Fügen Sie ein benutzerdefiniertes Tool auf das Menü Windows RE Boot-Optionen


Sie können eine benutzerdefinierte zur Problembehandlung oder Diagnosetool das Bild Windows Recovery Environment (WinRE) hinzufügen. Dieses Tool ist im Menü Startoptionen angezeigt.

Durch das benutzerdefinierte Tool zur Ausführung in WinRE entwickeln, die Fingereingabe kann genutzt werden, und auf dem Bildschirm Tastatur verfügbar in WinRE unterstützen.

Neu in Windows 10: Sie nicht WinRE optionale Komponenten hinzufügen, die bereits in der standardmäßigen WinRE Tools sind nicht möglich. Bei einer Windows 8-app, die von der optionalen Komponenten .NET abhängig, müssen Sie die app für Windows 10 umzuschreiben.

**So fügen Sie ein benutzerdefiniertes Tool hinzu**

1.  Extrahieren Sie und binden Sie ein Windows-Abbild (install.wim) und dem entsprechenden WinRE Bild (winre.wim):

    ``` syntax
    md c:\mount
    xcopy D:\sources\install.wim C:\mount 
    md C:\mount\windows
    Dism /mount-image /imagefile:C:\mount\install.wim /index:1 /mountdir:C:\mount\windows 
    md C:\mount\winre 
    Dism /mount-image /imagefile:c:\mount\windows\windows\system32\recovery\winre.wim /index:1 /mountdir:C:\mount\winre
    ```

    Weitere Informationen zu diesen Schritten finden Sie im Thema: [Windows RE anpassen](customize-windows-re.md).

2.  Erstellen Sie im Editor eine Konfigurationsdatei, die des benutzerdefinierten Tools Dateiname und Parameter (falls vorhanden) gibt:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- WinREConfig.xml -->
    <Recovery>
       <RecoveryTools>
          <RelativeFilePath>OEMDiagnostics.exe</RelativeFilePath>
          <CommandLineParam>/param1 /param2</CommandLineParam>
       </RecoveryTools>
    </Recovery>
    ```

    In dem *C:\\Tools\\OEMDiagnostics.exe* ist der Problembehandlung für benutzerdefinierte oder Diagnose-Tool und where */param1* und */param2* optionale Parameter verwendet, wenn dieses benutzerdefinierte Tool ausführen.

    **Hinweis**  
    Sie können nur ein benutzerdefiniertes Tool für die WinRE Boot Optionen Menüs hinzufügen.

    Speichern Sie die Datei mit UTF-8-Codierung. Verwenden Sie ANSI-nicht:

    Klicken Sie auf **Datei**, und klicken Sie dann auf **Speichern unter**. Klicken Sie im Feld **Codierung** wählen Sie **UTF-8**, und speichern Sie die Datei als `C:\mount\WinREConfig.xml`.

3.  Erstellen einer \\Quellen\\Wiederherstellung\\Ordner Tools in WinRE Ordner bereitstellen, und kopieren Sie das benutzerdefinierte Tool und eine Konfigurationsdatei in den neuen Ordner:

    ``` syntax
    md C:\mount\winre\sources\recovery\tools
    copy C:\Tools\OEMDiagnostics.exe C:\mount\winre\sources\recovery\tools
    copy C:\mount\WinREConfig.xml C:\mount\winre\sources\recovery\tools
    ```

    Benutzerdefiniertes Tool und alle zugehörigen Ordner muss in diesem Ordner, damit es nach zukünftige WinRE Upgrades Arbeit fortsetzen kann.

4.  Ihre Anpassungen Commit, und heben Sie die Bereitstellung des Abbilds WinRE:

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\winre /commit
    ```

5.  Optional: Stellen Sie eine Sicherungskopie des Bilds WinRE.

    ``` syntax
    copy C:\mount\windows\windows\system32\recovery\winre.wim C:\mount\winre_amd64_backup.wim
    ```

    Sie können dieselben Anpassungen auf mehrere Bilder oft wiederverwenden.

6.  Heben Sie die Bereitstellung, und speichern Sie die Änderungen aus dem Basiskalender Windows Bild:

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\windows /commit
    ```

**Zum Bereitstellen des Abbilds**

1.  Erstellen Sie im Editor eine Konfigurationsdatei, die die benutzerdefinierten Tools im Menü Optionen Boot beschreibt. Fügen Sie eine Beschreibung für jede Sprache, die Sie unterstützt. Dieses Beispiel gibt an, auf Englisch und Französisch Sprachversionen von Toolname und Beschreibung:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- AddDiagnosticsToolToBootMenu.xml -->
    <BootShell>
       <WinRETool locale="en-us">
             <Name>Fabrikam Utility</Name>
             <Description>Troubleshoot your Fabrikam PC</Description>
       </WinRETool>
       <WinRETool locale="fr-fr">
          <Name>Utilité de Fabrikam</Name>
          <Description>Dépannez votre PC de Fabrikam</Description>
       </WinRETool>
    </BootShell>
    ```

    **Warnung**  
    Grenzwert für die `<Name>` und `<Description>` Werte auf ungefähr 30 Zeichen oder weniger dafür sorgen, dass sie ordnungsgemäß im Startmenü Optionen angezeigt werden.

    Speichern Sie die Datei mit UTF-8-Codierung:

    Klicken Sie auf **Datei**, und klicken Sie dann auf **Speichern unter**. Klicken Sie im Feld **Codierung** wählen Sie **UTF-8**, und speichern Sie die Datei als `E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml`.

    Wobei *E:\\ * ist der Laufwerkbuchstabe des einen austauschbaren Laufwerk oder im Netzwerk-Speicherort.

2.  Auf dem Zielcomputer, während der Bereitstellung von Bild, aber nach dem Registrieren Sie des benutzerdefinierten WinRE Boot Bilds und die Windows-Betriebssystem, müssen Sie die Beschreibung des benutzerdefinierten Tools registrieren:

    ``` syntax
    Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
    ```

    Wenn das benutzerdefinierte Tool ordnungsgemäß registriert ist, wird die Ausgabe dieses Befehls werden: `<OEM Tool =  1>`.

    **Hinweis**  
    Weitere Informationen zum Bereitstellen von Windows finden Sie unter dem Thema [Bereitstellen von Windows RE](deploy-windows-re.md) .

**So überprüfen Sie das benutzerdefinierte Tool angezeigt wird, klicken Sie im Menü Startoptionen beim Start von Windows**

1.  Starten Sie den Zielcomputer neu, und führen Sie OOBE als Ihrer Benutzer.

    **Hinweis**  
    Wenn Sie einen Product Key aufgefordert werden, klicken Sie auf **Überspringen**.   

2.  Klicken Sie auf **Start** &gt; **PC-Einstellungen**, und wählen Sie dann **Allgemein**.

3.  Wählen Sie im Abschnitt **erweiterten Startoptionen** **jetzt neu starten**.

    Das Windows- **Startoptionen** Menü wird angezeigt.

4.  Klicken Sie im Menü **Startoptionen** wählen Sie **Troubleshoot aus**, und klicken Sie dann auf den Link **Fabrikam-Dienstprogramm** .

    Neustart des Computers in WinRE und das Tool, das in angegeben ist die * &lt;RecoveryTools&gt; * Abschnitt der Datei "WinREConfig.xml" wird angezeigt.

5.  Vergewissern Sie sich, dass das benutzerdefinierte Tool ordnungsgemäß funktioniert, und schließen Sie das Tool.

    Wenn das benutzerdefinierte Tool nicht auf das Menü Startoptionen angezeigt wird, können Sie Folgendes versuchen:

    -   Überprüfen Sie die "WinREConfig.xml" und der AddDiagnosticsToolToBootMenu.xml Dateien mit UTF-8-Codierung-Format gespeichert werden.

    -   Deaktivieren Sie WinRE und anschließend aktivieren Sie WinRE registrieren Sie des benutzerdefinierten Tools erneut. Beispiel:

        ``` syntax
        Reagentc /disable 
        Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
        Reagentc /enable
        ```
**So überprüfen Sie das benutzerdefinierte Tool angezeigt wird, klicken Sie im Menü WinRE Wiederherstellung**

1.  Klicken Sie im Menü Wiederherstellung wählen Sie **Troubleshoot aus**, und klicken Sie dann auf den Link **Fabrikam-Dienstprogramm** aus.

2.  Bestätigen Sie, dass das benutzerdefinierte Tool ordnungsgemäß funktioniert, und schließen Sie das Tool.

3.  Klicken Sie auf **Weiter**.

    Der PC wird in das Betriebssystem neu gestartet.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)

[Anpassen von Windows RE](customize-windows-re.md)

[Bereitstellen von Windows RE](deploy-windows-re.md)

[Windows RE-Problembehandlung von Features](windows-re-troubleshooting-features.md)

 

 






