---
author: Justinha
Description: "Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup"
ms.assetid: a22c2f2f-c297-4027-9712-d747b08f7476
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup"
ms.openlocfilehash: d78a352e8d2e8817c755377e0acfca7067d2ebd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-custom-script-to-windows-setup"></a>Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup


**Windows-Setup-Skripts**: **Setupcomplete.cmd** und **ErrorHandler.cmd** benutzerdefinierte Skripts, während oder nach der Installation von Windows ausgeführt, werden. Sie können so installieren Anwendungen oder andere Aufgaben ausführen, mithilfe von **Cscript/Wscript** Skripts verwendet werden.

-   **%Windir%\\Setup\\Skripts\\SetupComplete.cmd**: Dieses Skript wird ausgeführt, unmittelbar nachdem der Benutzer den Desktop erhält. Diese Einstellung wird bei der Verwendung von OEM-Produktschlüssel deaktiviert. Es wird mit der Berechtigung lokales System ausgeführt.
-   **%Windir%\\Setup\\Skripts\\ErrorHandler.cmd**: mit diesem Skript wird automatisch ausgeführt, wenn Setup ein schwerwiegender Fehler auftritt. Es wird mit der Berechtigung lokales System ausgeführt.

**Skripts für die unbeaufsichtigte Installation Windows**: Erstellen Sie eine Unattend.xml-Datei mit einem dieser Einstellungen, die während des Installationsvorgangs von Windows ausgeführt. Dies kann mit OEM Product Keys verwendet werden.

Führen Sie Dienste oder Befehle, die zur selben Zeit starten können mit RunAsynchronousCommands. Um Befehle auszuführen, die vor anderen Befehle Fertig stellen müssen können starten, RunSynchronousCommands verwenden.

**Hinweis**  Ab Windows 10 [Microsoft-Fenster-Shell-Setup\\LogonCommands\\AsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915476) jetzt funktioniert wie LogonCommands\\AsynchronousCommand: alle Befehle, die mit diesen Einstellungen unbeaufsichtigten jetzt zur selben Zeit gestartet wurden, und warten Sie nicht mehr für den vorherigen Befehl auf Fertig stellen.

 

Einige dieser Einstellungen im Kontext Benutzers ausgeführt, andere im System-Kontext je nach der Konfiguration Durchgang werden ausgeführt.

-   Hinzufügen von [Microsoft-Windows-Setup\\RunAsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915798) oder [RunSynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915802) das Ausführen eines Skripts, Windows Setup zu starten. Dies kann zum Festlegen von Festplattenpartitionen hilfreich sein.
-   Hinzufügen von [Microsoft-Windows-Deployment\\RunAsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915797) oder [RunSynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915801) übergeben Sie die **AuditUser** Konfiguration das Ausführen eines Skripts, das ausgeführt wird, wenn der PC-Option Überwachungsmodus eingibt. Dies kann für Aufgaben wie automatisierte app-Installation oder testen hilfreich sein.
-   Hinzufügen von [Microsoft-Windows-Shell-Setup\\LogonCommands\\AsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915476) oder [FirstLogonCommands\\SynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn922797) ausführen nach der Out of Feld Experience (OOBE), aber bevor der Benutzer den Desktop erhält. Dies kann insbesondere dann hilfreich sprachspezifische apps oder Inhalte einrichten, nachdem der Benutzer ihrer Sprache bereits ausgewählt hat sein.

    Verwenden Sie diese Skripts sparsame, da langen Skripts, dass Benutzer können die Startseite schnell erreicht. Für Verkaufsversionen von Windows gelten zusätzliche Einschränkungen für diese Skripts. Info finden Sie unter der Anleitung Lizenzierung und Richtlinien für das [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358).

    **Hinweis**   Wenn Sie ein Skript mit FirstLogonCommands hinzufügen, wird auf der nächsten Neustart ausgelöst werden, auch wenn Sie starten im Überwachungsmodus mit STRG + UMSCHALT + F3. Fügen Sie zum Start im Überwachungsmodus ohne diese Skripts auslösen, die Einstellung: Microsoft-Windows-Deployment\\Reseal\\[Mode](https://msdn.microsoft.com/library/windows/hardware/dn923110) = Audit.

     

## <a name="span-idrunascriptaftersetupiscompletesetupcompletecmdspanspan-idrunascriptaftersetupiscompletesetupcompletecmdspanrun-a-script-after-setup-is-complete-setupcompletecmd"></a><span id="run_a_script_after_setup_is_complete__setupcomplete.cmd_"></span><span id="RUN_A_SCRIPT_AFTER_SETUP_IS_COMPLETE__SETUPCOMPLETE.CMD_"></span>Führen Sie ein Skript nach Abschluss von Setup abgeschlossen (SetupComplete.cmd)


**Reihenfolge der Vorgänge**

1.  Nachdem Windows installiert ist, jedoch bevor der Anmeldebildschirm angezeigt wird, Windows Setup nach der **SetupComplete.cmd** -Datei in sucht der **%windir%\\Setup\\Skripts\\ Directory**.
2.  Wenn eine Datei **SetupComplete.cmd** gefunden wird, wird Windows Setup das Skript ausgeführt. Windows Setup protokolliert die Aktion in der **C:\\Windows\\Panther\\UnattendGC\\Setupact.log** Datei.

    Setup überprüft alle Exitcodes oder Fehlerebenen im Skript nach der Ausführung **SetupComplete.cmd**nicht zu.

    **Warnung**  Sie können nicht das System neu starten und fortsetzen **SetupComplete.cmd**ausgeführt. Sie sollten das System nicht durch Hinzufügen eines Befehls wie **Herunterfahren-r**neu starten. Dadurch wird das System in einem beschädigten Zustand versetzt.

     

3.  Wenn der Computer während der Installation einer Domäne beitritt, wird die Gruppenrichtlinie, die in der Domäne definiert ist auf dem Computer bis zum Abschluss **Setupcomplete.cmd** nicht angewendet. Dies ist, um sicherzustellen, dass die Gruppenrichtlinie Konfigurationsvorgang nicht mit dem Skript beeinträchtigt.

## <a name="span-idrunascriptifwindowssetupencountersafatalerrorerrorhandlercmdspanspan-idrunascriptifwindowssetupencountersafatalerrorerrorhandlercmdspanrun-a-script-if-windows-setup-encounters-a-fatal-error-errorhandlercmd"></a><span id="run_a_script_if_windows_setup_encounters_a_fatal_error__errorhandler.cmd_"></span><span id="RUN_A_SCRIPT_IF_WINDOWS_SETUP_ENCOUNTERS_A_FATAL_ERROR__ERRORHANDLER.CMD_"></span>Führen Sie ein Skript aus, wenn Windows Setup einen schwerwiegenden Fehler (ErrorHandler.cmd) erkennt.


Dieses Skript ist nützlich, wenn Sie viele Systeme zur selben Zeit installieren. Dadurch können Sie erkennen, wann ein Fehler, während der Installation von Windows auftritt. Wenn dies der Fall ist, führt Setup automatisch ein Skript, das benutzerdefinierte Befehle oder Aktionen, um die Ursache des Fehlers enthalten kann.

Wenn Windows Setup einen schwerwiegenden Fehler feststellt und Abschluss der Installation wird verhindert, sucht Setup Windows ein Befehlsskript in folgendem Verzeichnis: **%windir%\\Setup\\Skripts\\ErrorHandler.cmd**. Eine von zwei Aktionen tritt auf, je nachdem, ob das Skript gefunden wird.

-   Wenn das Skript nicht gefunden wird, wird ein Dialogfeld mit der Fehlermeldung angezeigt. Ein Benutzer muss das Dialogfeld schließen, bevor Windows Setup beendet wird.
-   Wenn das Skript gefunden wird, führt das Skript synchron. Kein Dialogfeld Feld oder Fehler Text wird angezeigt. Nachdem das Skript **ErrorHandler.cmd** ausgeführt wurde, wird Windows Setup beendet.

Je nach der Phase der Windows-Installation wird der Computer in der Umgebung zurück aus dem Windows-Setup, beispielsweise einer früheren Version des Betriebssystems oder Windows Vorinstallation Environment (Windows PE), zum Beispiel ausgeführt wurde.

Unter Umständen beim Windows Setup mehr als ein Fehler auftritt, und das Skript ErrorHandler.cmd nur einmal ausgeführt. Bei der Entwicklung mit dem Code für **ErrorHandler.cmd**stellen Sie sicher, dass dieses Skript mehrmals ausgeführt werden kann.


**ErrorHandler.cmd verwenden**, können Sie eine der folgenden Aktionen ausführen:

-   Stellen Sie das Abbild, und fügen Sie es auf das Bild **%windir%\\Setup\\Skripts\\ErrorHandler.cmd**. Hängen Sie das Bild aus.

    \endash oder \endash

-   Fügen Sie eine temporäre Dateispeicherort **ErrorHandler.cmd** (beispielsweise C:\\Temp\\ErrorHandler.cmd), und führen Sie dann Windows Setup mit der **Option/m** .
    ``` syntax
    Setup /m:C:\Temp
    ```

    Weitere Informationen finden Sie unter [Windows Setup Command-Line Options](windows-setup-command-line-options.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Starten Sie von einer DVD](boot-from-a-dvd.md)

[Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

[Bereitstellen eines benutzerdefinierten Abbilds](deploy-a-custom-image.md)

[Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

 

 






