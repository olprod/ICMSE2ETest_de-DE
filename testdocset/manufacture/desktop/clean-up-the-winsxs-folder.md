---
author: Justinha
Description: Bereinigen des Ordners WinSxS
ms.assetid: 67fe462d-cda1-4f2e-9652-62c374a6be97
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereinigen des Ordners WinSxS
ms.openlocfilehash: 26b1ec8f9fa9665af2e4f313ba6e59e4ad4db93b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clean-up-the-winsxs-folder"></a>Bereinigen des Ordners WinSxS


Eine häufig gestellte Frage ist ich den Ordner WinSxS, um Speicherplatz wieder zu übernehmen löschen können? Die Antwort ist keine. Es gibt jedoch Möglichkeiten, um die Größe des Ordners WinSxS zu reduzieren. Weitere Informationen zu den Ordner WinSxS finden Sie unter [Verwalten der Komponente Store](manage-the-component-store.md). In diesem Thema wurde zum bieten Informationen über die verschiedenen Verfahren zum Reduzieren der Größe des Ordners WinSxS auf eine ausgeführte Version von Windows 10 geschrieben.

Windows 10 und Windows Server 2016 automatisch die Größe von verringert die WinSxS ähnelt derjenigen, die in diesem Thema beschriebenen Methoden verwenden, aber diese Methoden umfassen auch interner Prozesse, wie deinstallieren und Löschen von Paketen mit Komponenten, die von anderen Komponenten durch neuere Versionen ersetzt wurden. Frühere Versionen von einige Komponenten werden auf dem System für einen Zeitraum, sodass Sie bei Bedarf zum Ausführen eines Rollbacks gespeichert. Nachdem eine bestimmte Zeitspanne werden diese Komponenten aus der Installation entfernt.

Sie können auch die Größe eines Bilds Windows Verwendung einiger der gleichen Techniken reduzieren, wie beschrieben unter [Reduce the Size des Speichers Komponente in einem Offline-Windows-Bild](reduce-the-size-of-the-component-store-in-an-offline-windows-image.md).

**Warnung**  
Löschen von Dateien aus dem Ordner WinSxS oder löschen den gesamten Ordner WinSxS beschädigen stark Ihr System sodass PC möglicherweise nicht starten und kann die aktualisieren.

 

In Windows 10 und Windows Server 2016 verfügen Sie über eine Anzahl von verwenden Sie eine Kombination von Paket löschen und Komponente Komprimierung Ordner WinSxS bereinigen Benutzeroberfläche für die Bereinigung des Speichers Komponente zu starten:

## <a name="span-idtaskschedulerspanspan-idtaskschedulerspanspan-idtaskschedulerspantask-scheduler"></a><span id="Task_Scheduler"></span><span id="task_scheduler"></span><span id="TASK_SCHEDULER"></span>Taskplaner


Die Aufgabe **StartComponentCleanup** erstellt wurde, Windows 8 regelmäßig Komponenten automatisch bereinigen, wenn das System nicht verwendet wird. Für diese Aufgabe wird automatisch ausgeführt, wenn vom Betriebssystem ausgelöst festgelegt. Wenn automatisch ausgeführt wird, wartet die Aufgabe mindestens 30 Tage nach der Installation von einer aktualisierten Komponente vor dem Deinstallieren früherer Versionen der Komponente.

Wenn Sie für diese Aufgabe ausführen, wird die Aufgabe muss einen Timeout 1 Stunde und möglicherweise nicht vollständig bereinigt alle Dateien.

**Führen Sie den Task StartComponentCleanup im Taskplaner zum Bereinigen und komprimieren Komponenten**

1.  Wenn **Taskplaner** nicht geöffnet ist, starten Sie den **Taskplaner**. Weitere Informationen finden Sie unter [Taskplaner starten](http://technet.microsoft.com/library/cc721931.aspx).

2.  Erweitern Sie die Konsolenstruktur, und navigieren Sie zu **Aufgabenplanungsbibliothek\\Microsoft\\Windows\\Servicing\\StartComponentCleanup**.

3.  Klicken Sie auf **Ausführen** , klicken Sie unter **Selected Item**

**Hinweis**  
Die Aufgabe StartComponentCleanup kann auch über die Befehlszeile gestartet werden:

**SCHTASKS.exe/Run/TN "\\Microsoft\\Windows\\– Wartung\\StartComponentCleanup"**

 

## <a name="span-iddismexespanspan-iddismexespandismexe"></a><span id="dism.exe"></span><span id="DISM.EXE"></span>DISM.exe


Bereitstellung Image Servicing and Management (DISM) ist ein Befehlszeilentool, das Sie installieren, deinstallieren, konfigurieren und Aktualisieren von Windows-Features, Pakete, Treiber und internationalen Einstellungen ermöglicht. Der Parameter **/Cleanup-Image** der **Dism.exe** bietet erfahrenen Benutzern weitere Optionen, um die Größe des Ordners WinSxS weiter zu verringern. Weitere Informationen finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

**Verwenden Sie den Parameter /StartComponentCleanup**

-   Mit dem **/StartComponentCleanup** -Parameter des Dism.exe auf einer ausgeführten Version von Windows 10 gibt Ihnen ähnliche Ergebnisse für die Ausführung von der **StartComponentCleanup** Aufgabe in **Taskplaner**, mit Ausnahme von früheren Versionen von aktualisierten Komponenten werden sofort gelöscht (ohne eine 30-Tage-Nachfrist) und eine Einschränkung 1 Stunde Timeout wird nicht angezeigt.

    Geben Sie von einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    Dism.exe /online /Cleanup-Image /StartComponentCleanup
    ```

**Verwenden Sie die Option /ResetBase mit dem /StartComponentCleanup-parameter**

-   Verwenden die **/ResetBase** entfernt Switch mit dem Parameter **/StartComponentCleanup** DISM.exe auf einer ausgeführten Version von Windows 10 alle ersetzte Versionen jeder Komponente im Komponentenspeicher.

    Geben Sie von einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

    **Warnung**  
    Alle vorhandenen Servicepacks und Updates können nicht deinstalliert werden, nachdem dieser Befehl abgeschlossen ist. Dadurch wird die Deinstallation von zukünftigen Servicepacks oder Updates nicht blockiert.

     

**Verwenden Sie den Parameter /SPSuperseded**

-   Um von einem Service Pack verwendeten Speicherplatz zu reduzieren, verwenden Sie den **/SPSuperseded** -Parameter der Dism.exe auf einer ausgeführten Version von Windows 10, um alle backup-Komponenten für die Deinstallation des Servicepacks benötigt zu entfernen. Ein Servicepack ist eine Auflistung von kumulativen Updates für eine bestimmte Version von Windows.

    Geben Sie von einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    Dism.exe /online /Cleanup-Image /SPSuperseded
    ```

    **Warnung**  
    Servicepack kann nicht deinstalliert werden, nachdem dieser Befehl abgeschlossen ist.

     

## <a name="span-iddiskcleanupspanspan-iddiskcleanupspanspan-iddiskcleanupspandisk-cleanup"></a><span id="Disk_Cleanup"></span><span id="disk_cleanup"></span><span id="DISK_CLEANUP"></span>Bereinigen des Datenträgers


Datenträgerbereinigung können zum Verringern der Anzahl nicht benötigte Dateien auf den Laufwerken, das Ihren PC schneller ausgeführt werden, kann hilfreich sein. Löschen der temporären Dateien und Systemdateien können, den Papierkorb leeren und verschiedene andere Elemente, die Sie möglicherweise nicht mehr benötigen entfernen. Die Option zum Aufräumen aktualisiert hilft reduziert die Größe des Speichers Komponente.

**Ausführen des Dienstprogramms Datenträgerbereinigung, um Systemdateien löschen**

-   Zum Löschen von System ausführen Dateien wie in [-Dateien mithilfe des Dienstprogramms Datenträgerbereinigung löschen](http://go.microsoft.com/fwlink/p/?LinkId=698648).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Verwalten der Komponente Store](manage-the-component-store.md)

[Bestimmen der tatsächlichen Größe des Ordners WinSxS](determine-the-actual-size-of-the-winsxs-folder.md)

[Verringern Sie die Größe des Speichers Komponente in einem Offline-Windows-Bild](reduce-the-size-of-the-component-store-in-an-offline-windows-image.md)

[Deinstallieren von-WindowsFeature](http://technet.microsoft.com/library/jj205471.aspx)

[Wie reduziert die Größe des Verzeichnisses Winsxs und freier Speicherplatz auf Windows Server 2012 mithilfe von Features bei Bedarf](http://blogs.technet.com/b/askpfeplat/archive/2013/02/24/how-to-reduce-the-size-of-the-winsxs-directory-and-free-up-disk-space-on-windows-server-2012-using-features-on-demand.aspx)

[Wie Speicherplatz zu behandeln, die durch ein große Store (WinSxS) Verzeichnis für die Windows-Komponente verursacht werden](http://support.microsoft.com/kb/2795190)

 

 






