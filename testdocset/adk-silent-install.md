# <a name="windows-adk-silent-install"></a>Installieren von Windows ADK im Hintergrund

Wenn Sie ein Szenario, in dem Sie für eine unbeaufsichtigte Installation von Windows ADK müssen, verfügen, können Sie über die Befehlszeile installieren.

Stellen Sie sicher, dass während des Setups ADK ausgeführt wird, bleibt PC mit dem Internet verbunden. Während der Ausführung-downloads ADK Setup Installationspakete aus dem Internet. 

## <a name="install-the-windows-adk-by-using-the-command-line"></a>Installieren von Windows ADK mithilfe der Befehlszeile
1. Adksetup.exe von dieses [Microsoft-Website](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) an den PC herunterladen.
2. Öffnen Sie ein Eingabeaufforderungsfenster als Administrator an.
3. Ändern Sie im Eingabeaufforderungsfenster zu dem Verzeichnis, das adksetup.exe enthält.

        
```
    cd %userprofile%\downloads
```

4. Installieren der ADK. Verwenden Sie für die automatische Installation/quiet. Verwenden Sie /features, um Features anzugeben. Beispielsweise Bereitstellungstools und Windows PE automatische Installation:


```
    adksetup.exe /quiet /features OptionId.DeploymentTools OptionId.WindowsPreinstallationEnvironment
```

[ADKSetup Command-Line Syntax](https://technet.microsoft.com/en-us/library/dn621910.aspx).