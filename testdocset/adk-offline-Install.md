# <a name="install-the-windows-adk-offline"></a>Installieren von Windows ADK offline

Um die Windows ADK auf einem PC zu installieren, die keinen Zugriff auf das Internet, zuerst herunterladen Sie die Installationsdateien auf einem PC mit Internetzugriff. Kopieren Sie im nächsten Schritt die Installer-Dateien an einen Speicherort, der für die Offlinecomputer zugänglich ist. Führen Sie dann mithilfe der Benutzeroberfläche oder der Befehlszeile ADKSetup.exe aus.

## <a name="to-install-the-windows-adk-on-an-offline-computer-using-the-gui"></a>So installieren Sie Windows ADK auf einem Offlinecomputer mit der Benutzeroberfläche
1. Führen Sie auf einem PC mit Internetzugriff, Windows ADK Setup aus dieser [Microsoft-Website](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit).
2. Wählen Sie **dem Assessment and Deployment Kit für die Installation auf einem separaten Computer herunterladen.**
3. Geben Sie in das Feld **Pfad herunterladen** den Speicherort, wo Sie die Dateien herunterladen möchten, und klicken Sie dann auf **Weiter**.
4. Wählen Sie aus, ob Sie im Customer Experience Improvement-Programm (CEIP) teilnehmen, und klicken Sie auf **herunterladen**möchten. 
5. Nachdem der Download abgeschlossen ist, klicken Sie auf **Schließen**.
6. Kopieren der heruntergeladenen Dateien an einem Speicherort, den den offline Computer zugreifen können.
    Kopieren Sie beispielsweise die Dateien auf Wechseldatenträger oder auf einem Dateiserver, den auf der Computer zugreifen kann.

7. Ändern Sie auf dem Offlinecomputer Verzeichnis zum Speicherort der kopierten Dateien.
8. Führen Sie ADKSetup.exe, und wählen Sie dann die Windows ADK-Features, die Sie installieren möchten.

## <a name="to-install-the-windows-adk-on-an-offline-computer-using-the-command-line"></a>So installieren Sie Windows ADK auf einem Offlinecomputer über die Befehlszeile
1. Auf einem PC mit Internetzugriff, speichern Sie eine Kopie der Adksetup.exe.
2. Öffnen Sie ein Eingabeaufforderungsfenster als Administrator.
3. Wechseln Sie zum Verzeichnis, in dem die Adksetup.exe Datei gespeichert.
        
    ```
    cd %userprofile%\downloads
    ```

4. Führen Sie adksetup.exe. Verwenden Sie/quiet, um das Installationsprogramm im Hintergrund ausgeführt. Verwenden/Layout an, auf denen die offline Dateien installieren, wird in kopiert werden.

    ```
    adksetup /quiet /layout c:\temp\ADKoffline
    ```

5. Kopieren der heruntergeladenen Dateien an einem Speicherort, den den offline Computer zugreifen können.
    Kopieren Sie die Dateien beispielsweise Wechseldatenträger oder auf einem Dateiserver, den die Offlinecomputer zugreifen kann.
6. Öffnen Sie ein Eingabeaufforderungsfenster als Administrator, auf dem Computer mit offline.
7. Wechseln Sie zum Verzeichnis, das adksetup.exe enthält.
8. Führen Sie adksetup.exe. Verwenden Sie/quiet für eine automatische Installation, /installpath, um anzugeben, wo die ADK und /features zum Angeben von Features zu installieren. Beispielsweise Bereitstellungstools und Windows PE zum c:\ADK automatische Installation: 

    ```
    adksetup.exe /quiet /installpath c:\ADK /features OptionId.DeploymentTools OptionId.WindowsPreinstallationEnvironment
    ```
    
[ADKSetup Command-Line Syntax](https://technet.microsoft.com/en-us/library/dn621910.aspx).