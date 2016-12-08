---
author: Justinha
Description: "Windows-Setup-Szenarien und bewährte Methoden"
ms.assetid: 651cb9c3-121d-40d3-9e17-47f1a78a000f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows-Setup-Szenarien und bewährte Methoden"
ms.openlocfilehash: 02d4264091ab6962556f9d0e0b370073aa052b88
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-scenarios-and-best-practices"></a>Windows-Setup-Szenarien und bewährte Methoden


Windows® Setup installiert das Betriebssystem Microsoft Windows. Windows-Setup verwendet eine Technologie namens Abbildbasierte Installation (IBS), die ein einheitliches Verfahren bietet mit dem alle Kunden Windows installieren können. IBS führt Neuinstallationen und Upgrades von Windows und Client und Server-Installationen verwendet wird. Windows Setup können Sie zum Anpassen von Windows während der Installation mithilfe von Setup Antwort dateieinstellungen.

In diesem Thema:

-   [Allgemeine Verwendungsszenarien](#commoninstallationscenarios)

-   [Bewährte Methoden für Windows Setup](#bestpractices)

-   [Windows-Setup-Einschränkungen](#limitations)

## <a name="span-idcommoninstallationscenariosspanspan-idcommoninstallationscenariosspanspan-idcommoninstallationscenariosspancommon-usage-scenarios"></a><span id="CommonInstallationScenarios"></span><span id="commoninstallationscenarios"></span><span id="COMMONINSTALLATIONSCENARIOS"></span>Allgemeine Verwendungsszenarien


Allgemeine Installationsszenarien enthalten Neuinstallationen, Upgrades und unbeaufsichtigte Installationen durchführen.

### <a name="span-idcustominstallationsspanspan-idcustominstallationsspanspan-idcustominstallationsspancustom-installations"></a><span id="Custom_Installations"></span><span id="custom_installations"></span><span id="CUSTOM_INSTALLATIONS"></span>Benutzerdefinierte Installationen

Das am häufigsten verwendete Szenario für Windows Setup ist eine benutzerdefinierte Installation ausführen. In diesem Szenario installieren Sie Windows auf einem Computer, der verfügt nicht über ein Betriebssystem oder eine frühere Version von Windows. Dieses Szenario umfasst die folgenden Phasen:

1.  Führen Sie Setup.exe aus dem Windows-Produkt-DVD oder der Netzwerkfreigabe aus.

2.  Wählen Sie **benutzerdefinierte** Installation.

3.  Wenn Sie von einer vorherigen Installation von Windows installieren, wird Windows Setup ein lokales Startverzeichnis erstellt und kopiert alle erforderlichen Windows-Setup-Dateien in dieses Verzeichnis.

4.  Windows-Setup wird neu gestartet, installiert und konfiguriert Windows-Komponenten und, nach Abschluss der Installation wird Windows-Willkommensseite gestartet.

Benutzerdefinierte Installationen migriere keine Einstellungen oder Voreinstellungen von zuvor installierten Versionen von Windows. Dateien aus früheren Versionen von Windows werden in kopiert eine \\Verzeichnis "Windows.old". Alle Daten aus der Windows-Installation, einschließlich der Benutzer, die Programmdateien und die Windows-Verzeichnisse werden in diesem Verzeichnis gespeichert.

### <a name="span-idupgradesspanspan-idupgradesspanspan-idupgradesspanupgrades"></a><span id="Upgrades"></span><span id="upgrades"></span><span id="UPGRADES"></span>Upgrades

Windows-Setup können auch Upgrades ein unterstütztes Betriebssystem ausführen.

Dieses Szenario umfasst die folgenden Phasen:

1.  Führen Sie Setup.exe auf der vorherigen Version von Windows.

2.  Wählen Sie die Installationsart **Aktualisieren** . Windows Setup das System aktualisiert und schützt Ihre Dateien, Einstellungen und Voreinstellungen während der Installation.

3.  Windows Setup wird neu gestartet und Ihre geschützter Dateien, Einstellungen und Voreinstellungen wiederhergestellt. Windows-Setup startet dann Windows-Willkommensseite.

**Hinweis**  
Upgrades dienen zum upgrade von eines einzelnen Computers auf Windows 8. Upgrades unterstützen auch Migrieren der Benutzerdaten zu einem neuen System.

 

### <a name="span-idautomatedinstallationsspanspan-idautomatedinstallationsspanspan-idautomatedinstallationsspanautomated-installations"></a><span id="Automated_Installations"></span><span id="automated_installations"></span><span id="AUTOMATED_INSTALLATIONS"></span>Automatisierte Installationen

Automatisierte Installationen können Sie zum Anpassen einer Windows-Installation und entfernen die Notwendigkeit für einen Benutzer mit Windows Setup interagieren. Mithilfe von Windows System Image Manager (Windows SIM) oder den APIs Component Platform Interface (CPI) können Sie eine oder mehrere benutzerdefinierte Windows-Installationen erstellen, die über zahlreiche verschiedene Konfigurationen bereitgestellt werden kann.

Die automatisierte Installation, eine unbeaufsichtigte Installation die Abkürzung, Szenario umfasst die folgenden Phasen:

1.  Verwenden Sie Windows SIM oder den CPI-APIs, um eine unbeaufsichtigte Installation Antwortdatei Speichervorgangs aufgerufen Unattend.xml erstellen. Diese Antwortdatei enthält alle Einstellungen, die Sie im Windows-Abbild konfigurieren. Weitere Informationen finden Sie unter [Windows System Image Manager How-to Topics](https://msdn.microsoft.com/library/windows/hardware/dn915116).

2.  Windows PE eine frühere Version von Windows oder einem anderen Vorinstallation Umgebung führen Sie Setup.exe mit der explizite Pfad der Antwortdatei. Wenn Sie den Pfad zu der Antwortdatei nicht verwenden, wird eine gültige Antwortdatei an verschiedenen Speicherorten Setup.exe gesucht. Weitere Informationen finden Sie unter [Windows Setup Command-Line Options](windows-setup-command-line-options.md).

3.  Windows Setup dann wird das Betriebssystem installiert und alle Einstellungen, die in die Antwortdatei konfiguriert. Zusätzliche Applikationen Gerätetreibern und Updates können auch während der Installation von Windows installiert werden. Nachdem das Betriebssystem installiert ist, wird Setup Windows-Willkommensseite gestartet.

## <a name="span-idbestpracticesspanspan-idbestpracticesspanspan-idbestpracticesspan-windows-setup-best-practices"></a><span id="BestPractices"></span><span id="bestpractices"></span><span id="BESTPRACTICES"></span>Bewährte Methoden für Windows Setup


Im folgende Abschnitt werden einige bewährte Methoden zur Verwendung mit Windows Setup beschrieben.

-   **Stellen Sie sicher, dass ausreichend Speicherplatz für Windows Setup temporäre Dateien vorhanden ist.** Wenn Sie Setup aus einer früheren Version von Windows ausführen, stellen Sie sicher, dass genügend Speicherplatz auf dem Datenträger für temporäre Windows Setup-Dateien vorhanden ist. Der erforderliche Speicherplatz kann variieren, jedoch kann bis zu 500 Megabyte (MB) sein.

-   **Frühere Installationen von Windows werden in einen Ordner Windows.old verschoben.** Es empfiehlt sich sollten Sie Ihre Daten sichern, vor dem upgrade. Wenn Sie Windows über eine frühere Windows-Installation installieren, werden alle vorherigen Windows-Dateien und Verzeichnisse in einen Ordner Windows.old mit allen Benutzern, Windows und Programmdateien Verzeichnisse verschoben. Nach Abschluss der Installation von Windows können Sie Ihre Daten in den Ordner Windows.old zugreifen. Wenn Sie zusätzliche Ordner nicht in Benutzer, Programmdateien oder Windows-Ordner vorhanden sind, werden diese Ordner nicht verschoben. Angenommen, Sie haben einen Ordner mit dem Namen C:\\Treiber dieses Ordners nicht in den Ordner "Windows.old" verschoben.

-   **Überprüfen der Protokolldateien Windows Setup.** Wenn Sie während der Installation von Windows Probleme auftreten, überprüfen Sie die Protokolldateien im ORDNER %\\Panther. Identifizieren und viele Probleme zu beheben, durch die Überprüfung der Installationsprotokolldateien sein. Weitere Informationen finden Sie unter [Problembehandlung bei Bereitstellung und Protokolldateien](deployment-troubleshooting-and-log-files.md) und [Windows Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md).

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspan-windows-setup-limitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Windows Setup Einschränkungen


Den folgenden Abschnitten werden einige der die Einschränkungen der Windows-Installation. Lesen Sie diesen Abschnitt, bevor Sie Windows Setup ausführen.

-   **So installieren Sie auf einem UEFI-basierten Computer UEFI - Kompatibilitätsmodus aktivieren**. Sie können nicht auf einigen Computern UEFI Windows im BIOS-Kompatibilitätsmodus installieren. Sie müssen möglicherweise UEFI-Kompatibilitätsmodus wechseln.

-   **Applications möglicherweise eine konsistente Laufwerkbuchstabe erforderlich.** Wenn Sie benutzerdefinierte Anwendungen auf Ihrem Windows-Abbild installieren, wird empfohlen, dass Sie Windows auf den gleichen Laufwerksbuchstaben auf dem Zielcomputer installieren, da einige Anwendungen einen einheitlichen Laufwerkbuchstaben erforderlich sind. Deinstallation, warten und Reparieren Szenarien möglicherweise nicht ordnungsgemäß funktioniert, ist der Laufwerkbuchstabe des Systems nicht mit der Buchstabe des Laufwerks, in der Anwendung angegeben. Diese Beschränkung gilt für die Bereitstellung Bild Wartung und Verwaltung (DISM) Tool und den Windows Setup.

-   **Bereitstellen mehrerer Abbilder auf mehreren Partitionen.** Wenn Sie erfassen und mehrere Bilder auf mehreren Partitionen bereitstellen, müssen die folgenden Anforderungen erfüllt sein:

    -   Die Partitionsstruktur, Bus-Speicherort und Anzahl der Datenträger müssen auf den Verweis und Zielcomputern identisch sein.

    -   Die Partitionstypen (primär, erweiterte oder logischen) müssen übereinstimmen. Die aktive Partition auf dem Referenzcomputer muss mit dem Zielcomputer übereinstimmen.

-   **Installieren von benutzerdefinierten WIM-Dateien erfordert einen Beschreibungswert in der WIM-Datei.** Wenn Sie eine benutzerdefinierte WIM-Datei erstellen, erfordert Windows Setup immer ein Beschreibungswert für eingeschlossen. Wenn eine WIM-Datei nicht Beschreibungswert enthält, wird das Bild möglicherweise nicht ordnungsgemäß installiert. Mit der Option **/capture-image** den **Dism** -Befehl verwenden, können Sie einen Beschreibungswert ermöglichen. Wenn Sie eine WIM-Datei, die nicht über einen Beschreibungswert verfügt installieren, erfassen Sie das Bild, und geben Sie einen gültigen Beschreibungswert. Weitere Informationen finden Sie unter der [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

**Hinweis**  
Für Windows® Vorinstallation Environment (Windows PE), muss die Version der Startdateien die Computerarchitektur übereinstimmen. Eine X64, die nur UEFI Computer starten kann, mithilfe von Windows PE X64 Startdateien. Ein, die nur Computer starten können Sie mithilfe von Windows PE X86 X86 Dateien zu starten. Dies unterscheidet sich von legacy-BIOS. Legacy BIOS starten, ein, den Computer starten können Sie mithilfe von X86 X64 Dateien.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows Setup-Installationsvorgang](windows-setup-installation-process.md)

[Übersicht über die Automatisierung von Windows-Setup](windows-setup-automation-overview.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






