---
author: Justinha
Description: "Wie Drucktaste zurücksetzen Arbeit features"
ms.assetid: 86c93069-916c-4c94-8ba8-2fbf0d792a36
MSHAttr: PreferredLib:/library/windows/hardware
title: "Wie Drucktaste zurücksetzen Arbeit features"
ms.openlocfilehash: 29713ad1c7e89574edcf68b5383c2228a9d3594a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idhowpush-buttonresetfeaturesworkspanhow-push-button-reset-features-work"></a><span id="How_push-button_reset_features_work"></span>Wie Drucktaste zurücksetzen Arbeit features


## <a name="span-idrestoringtheoperatingsystemandcustomizationsspanspan-idrestoringtheoperatingsystemandcustomizationsspanspan-idrestoringtheoperatingsystemandcustomizationsspanrestoring-the-operating-system-and-customizations"></a><span id="Restoring_the_operating_system_and_customizations"></span><span id="restoring_the_operating_system_and_customizations"></span><span id="RESTORING_THE_OPERATING_SYSTEM_AND_CUSTOMIZATIONS"></span>Wiederherstellen des Betriebssystems und Anpassungen


In diesem Abschnitt werden die Mechanismen, die Drucktaste zurücksetzen Funktionen verwenden, um die Software auf dem PC wiederherzustellen.

### <a name="span-idrestoringwindowsspanspan-idrestoringwindowsspanspan-idrestoringwindowsspanrestoring-windows"></a><span id="Restoring_Windows"></span><span id="restoring_windows"></span><span id="RESTORING_WINDOWS"></span>Wiederherstellen von Windows

Drucktaste zurücksetzen Features Windows 10 wiederherstellen, indem Sie eine neue Kopie des Betriebssystems von Common Language Runtime-Systemdateien befindet sich im Windows Store-Komponente (C:\\Windows\\WinSxS). Dadurch wird die Wiederherstellung auch ohne eine Sicherungskopie aller Systemdateien mit Image-separate Wiederherstellung möglich ist.

Darüber hinaus wiederherstellen Drucktaste zurücksetzen Features Windows auf einer aktualisierten Zustand und nicht auf den Status Factory vorinstalliert. Insbesondere wird die neueste Version oder Haupt-Update installiert auf dem Computer (wie Windows 10, Version 1511) wiederhergestellt werden, während andere Updates installiert, nachdem, verworfen werden.

Dieser Ansatz bietet ein Gleichgewicht zwischen Benutzeroberfläche im Hinblick auf die Anzahl der Updates die neu installiert werden müssen, und die Features Effektivität in Beheben von Problemen mit Update. Darüber hinaus können Windows, ältere Systemdateien zu entfernen, die für die Verwendung der Common Language Runtime oder Recovery und Freigeben von Speicherplatz nicht mehr benötigt werden.

In der Standardeinstellung werden nicht wichtige Updates nicht wiederhergestellt werden. Um sicherzustellen, dass während der Herstellung vorinstalliert Updates nach der Wiederherstellung nicht verworfen werden, sollten sie als permanente gekennzeichnet werden mithilfe des Befehls /Cleanup-Image in DISM mit den Optionen /StartComponentCleanup und /ResetBase. Updates als permanente markiert werden immer während der Wiederherstellung wiederhergestellt.

### <a name="span-idrestoringlanguagepacksspanspan-idrestoringlanguagepacksspanspan-idrestoringlanguagepacksspanrestoring-language-packs"></a><span id="Restoring_language_packs"></span><span id="restoring_language_packs"></span><span id="RESTORING_LANGUAGE_PACKS"></span>Wiederherstellen von Sprachpaketen

Sprachpakete, die installiert und wird von mindestens ein Benutzerkonto verwendet werden, werden wiederhergestellt. Andere Sprachpakete werden aus der Komponente Windows Store sieben Tage nach der Out-of-Box-Experience (OOBE) entfernt. Mithilfe der Drucktaste zurücksetzen Features nach dem, der die entfernten Language Packs nicht wiederhergestellt werden sollen.

Auf PCs unter Single-Sprache-Editionen von Windows, wie beispielsweise Windows 10 Home Benutzer nicht herunterladen oder installieren Sie zusätzliche Language Packs, und sie können nicht Drucktaste Reset-Features verwenden, um Sprachen zu wechseln, wenn die vorinstallierten Language Packs entfernt wurden.

### <a name="span-idrestoringdriversspanspan-idrestoringdriversspanspan-idrestoringdriversspanrestoring-drivers"></a><span id="Restoring_drivers"></span><span id="restoring_drivers"></span><span id="RESTORING_DRIVERS"></span>Wiederherstellen der Treiber

Treiber werden auf ähnliche Weise als Betriebssystem wiederhergestellt. Anstelle von diesen Image-Wiederherstellung wiederhergestellt, werden die vorhandenen Treiber über Recovery beibehalten. Wie mit Systemdateien Treiber in dem Zustand wiederhergestellt werden waren sie bei der Installation der neuesten Version oder Haupt-Update in. Beispiel:

-   Wenn der Kunde Wiederherstellung nach dem Start eines neuen PCs vorinstalliert mit Windows 10 ausführt, werden verwendet, die während der OOBE vorhanden sind wiederhergestellt werden, auch wenn seit neuere Treiber installiert wurden.
-   Wenn der Kunde Wiederherstellung ausgeführt wird, nach der Aktualisierung von Windows 10 bis 10 für Windows, Version 1511, werden die Treiber, die während des Upgrades vorhanden sind wiederhergestellt werden, auch wenn seit neuere Treiber installiert wurden.

Gerät Applets, die außerhalb des Treiberpakets INF-Datei installiert werden, werden nicht im Rahmen dieses Prozesses wiederhergestellt. Factory Version und Status werden auf die gleiche Weise wie andere Anpassungen wie Windows-desktopanwendungen wiederhergestellt. (Siehe das Wiederherstellen von anderen Anpassungen für Weitere Informationen.) Wenn das Gerät Applet immer synchron (Version wise) mit der Treiber bleiben muss, empfiehlt es sich, dass der Treiber und das Gerät Applet über das gleiche INF-Paket installiert werden.

### <a name="span-idrestoringpreviouslyinstalledwindowsappsspanspan-idrestoringpreviouslyinstalledwindowsappsspanspan-idrestoringpreviouslyinstalledwindowsappsspanrestoring-previously-installed-windows-apps"></a><span id="Restoring_previously_installed_Windows_apps"></span><span id="restoring_previously_installed_windows_apps"></span><span id="RESTORING_PREVIOUSLY_INSTALLED_WINDOWS_APPS"></span>Wiederherstellen zuvor installierten apps für Windows

Vorinstallierten Windows-apps werden immer ihre Factory Version und der Zustand wiederhergestellt. Anstelle von diesen Image-Wiederherstellung wiederhergestellt, wird eine Kopie der Windows-apps automatisch gesichert, wenn sie während der bildanpassung und Fertigung bereitgestellt werden, und die Sicherungen werden wiederhergestellt, wenn Drucktaste zurücksetzen Features verwendet werden.

### <a name="span-idrestoringothercustomizationsspanspan-idrestoringothercustomizationsspanspan-idrestoringothercustomizationsspanrestoring-other-customizations"></a><span id="Restoring_other_customizations"></span><span id="restoring_other_customizations"></span><span id="RESTORING_OTHER_CUSTOMIZATIONS"></span>Wiederherstellen von anderen Anpassungen

In der Standardeinstellung wiederherstellen Drucktaste zurücksetzen Features nur OS Dateien, Treibern und vorinstallierten universellen Windows-apps. Unterschiedliche Mechanismen werden verwendet, um weitere Anpassungen vor, wie beispielsweise und Windows-desktopanwendungen wiederherstellen.

-   **Windows-desktopanwendungen** können mit den Migrationstools für Benutzerstatus des (USMT) erfasst werden ScanState Dienstprogramm in Verweis-Bildtyp Daten in einem Paket bereitstellen. Drucktaste zurücksetzen Features gesucht und dieses Paket Bereitstellung automatisch aus einem bekannten Speicherort wiederherstellen.
-   **Für alle Editionen von Windows 10 Allgemeine Einstellungen** (einschließlich Windows 10 Mobile) kann mit dem Windows Imaging und Konfiguration Designer (ICD) Tool festgelegt und in der Bereitstellung Pakete gespeichert werden. Drucktaste zurücksetzen Features suchen und diese Bereitstellung Pakete aus einem bekannten Speicherort automatisch wiederhergestellt. Alternativ können diese Einstellungen mit einer Kombination aus eine unbeaufsichtigte Installation Datei und Erweiterbarkeit Skripts zum Zurücksetzen des Drucktaste wiederhergestellt werden.
-   **Einstellungen für Editionen von Windows-10 für desktop-Editionen (Start, Pro, Enterprise, und Bildungseinrichtungen)** kann mit einer Kombination aus eine unbeaufsichtigte Installation Datei und Erweiterbarkeit Skripts für Drucktaste zurücksetzen wiederhergestellt werden. Beispiele für diese Einstellungen sind Supportinformationen für Gerätehersteller (engl.), Hersteller Logos und Startmenü Layout.

**Hinweis**  
Viele Einstellungen Anpassungen zugelassen oder durch den OPD erforderlich sind spezifisch für Windows 10 für Desktop und können nicht bei der Bereitstellung mithilfe von Windows ICD erstellt Pakete gespeichert werden. Für Windows 10 RTM empfiehlt sich die Verwendung von einer Datei für die unbeaufsichtigte Installation und Drucktaste zurücksetzen Erweiterbarkeit Skripts zum Wiederherstellen aller Einstellungen Anpassungen während der Wiederherstellung. Die Verwendung von Bereitstellung mithilfe von Windows ICD erstellt Pakete ist vollständig optional.

 

## <a name="span-idrefreshyourpcspanspan-idrefreshyourpcspanspan-idrefreshyourpcspanrefresh-your-pc"></a><span id="Refresh_your_PC"></span><span id="refresh_your_pc"></span><span id="REFRESH_YOUR_PC"></span>Aktualisieren von Ihrem PC


**Die Aktualisierung Ihrer PC-Funktion kann in den folgenden Schritten zusammengefasst werden:**

1.  PC-Start in der Windows Recovery Environment (Windows RE).
2.  **ERWEITERBARKEIT der PUNKT eine**: OEMs können optional ein Skript hier hinzufügen. (Siehe [Erweiterungspunkte](#extensibility-points) weiter unten in diesem Thema).
3.  Benutzerkonten, Einstellungen und Daten werden erfasst und an einen temporären Speicherort verschoben.
4.  Eine neue Kopie des Betriebssystems wird erstellt, in einem temporären Verzeichnis mit Dateien aus der Komponente Windows Store.
5.  Anpassungen, die bei der Bereitstellung Pakete unter C: gespeichert\\Wiederherstellung\\Anpassungen auf das neue Betriebssystem angewendet werden.
6.  Treiber werden vom vorhandenen Betriebssystem kopiert und in das neue Betriebssystem eingefügt.
7.  Vorinstallierten Windows-apps werden von ihrem backup Speicherort wiederhergestellt.
8.  System-kritische Einstellungen gelten für das neue Betriebssystem.
9.  Vorhandene OS wurde verschoben zu C:\\Windows.old.
10. Neue Betriebssystem wird in den Stamm des OS Datenträgers verschoben.
11. **ERWEITERBARKEIT PUNKT B**: OEMs können optional ein Skript hier hinzufügen. (Siehe [Erweiterungspunkte](#extensibility-points) weiter unten in diesem Thema).
12. PC wird auf das neue Betriebssystem neu gestartet.
13. Beim ersten Start werden Benutzerdaten und Einstellungen erneut angewendet.

### <a name="span-idpreservedsettingsspanspan-idpreservedsettingsspanspan-idpreservedsettingsspanpreserved-settings"></a><span id="Preserved_settings"></span><span id="preserved_settings"></span><span id="PRESERVED_SETTINGS"></span>Beibehaltenen Einstellungen

**Aktualisieren von Ihrem PC** erhalten eine Reihe von System- und Benutzerinformationen, damit das System ausgeführt und reduzieren Sie gleichzeitig die Notwendigkeit für Benutzer so konfigurieren Sie ihren PCs teilnehmen neu nicht die erforderlich sind.

Beibehaltene Einstellungen können sich grob in eine der folgenden Kategorien unterteilt werden:

-   Sind erforderlich für Benutzer, um ihren PCs teilnehmen melden Sie sich nach dem Ausführen der **Aktualisierung Ihrer PC** -Funktion.
-   Beeinflussen Sie, wie Benutzer auf ihre Dokumente und persönliche Dateien zugreifen.
-   Sind für die meisten Benutzer neu erstellen.
-   System Sicherheits- oder Benutzer Privacy auswirken.
-   Personalisieren des PCs-Option.

Die beibehaltenen Einstellungen sind wie folgt zusammengefasst:

-   Benutzerkonten (lokal, Domäne, Microsoft-Kontos) und Gruppenmitgliedschaften
-   Domäneneinstellungen
-   Windows Update-Einstellungen
-   In der Formularbibliothek
-   Sperren Hintergrund
-   Desktop zusammenhängen
-   Internationalen Einstellungen
-   Drahtlosnetzwerk-Profile
-   Windows-Willkommensseite konfigurierte Einstellungen

### <a name="span-iduserdataspanspan-iduserdataspanspan-iduserdataspanuser-data"></a><span id="User_data"></span><span id="user_data"></span><span id="USER_DATA"></span>Benutzerdaten

Da Benutzerdaten in vielen Orten gespeichert werden können, behält das Feature **Ihrem PC aktualisieren** die meisten Ordner und Dateien, die nicht Teil der Standardinstallation von Windows sind. Das Feature **PC aktualisieren** aktualisiert die in der folgenden Systemspeicherorte und der Inhalt wird nicht beibehalten.

-   \\Windows
-   \\Programmdateien
-   \\Programme\Microsoft Files(x86)
-   \\Ordner "ProgramData"
-   \\Benutzer\\&lt;Benutzernamen&gt;\\Anwendungsdaten (in jedem Benutzerprofil)

**Hinweis**  Einige Anwendungen werden Benutzerdaten in die \\Anwendungsdaten-Ordner in Benutzerprofilen. Die \\Anwendungsdaten Ordner stehen in C:\\Windows.old nach der Verwendung des Features **PC aktualisieren** .

 

Das **Aktualisieren von Ihrem PCs** Feature umgeht die folgenden Speicherorten und behält den Inhalt:

-   Datei Verlauf Versionsdaten
-   Alle Dateien und Ordner auf BS-Partitionen

### <a name="span-idwindowsapplicationsspanspan-idwindowsapplicationsspanspan-idwindowsapplicationsspanwindows-applications"></a><span id="Windows_Applications"></span><span id="windows_applications"></span><span id="WINDOWS_APPLICATIONS"></span>Windows-Anwendungen

Die Aktualisierung behandelt Ihrem PC-Feature Anwendungstypen anders, um sicherzustellen, dass der PC in einen zuverlässigen Zustand wiederhergestellt werden kann. Anwendungen werden folgendermaßen behandelt:

-   Windows-apps aus dem Windows Store Benutzer erworben werden nicht beibehalten. Benutzer müssen zum Neuinstallieren von Windows Store. Dies ist eine Änderung von Windows 8/8.1.
-   Vorinstallierten Windows-apps werden ihre Version Factory und Zustand wiederhergestellt. Updates für diese apps heruntergeladen und erneut automatisch angewendet, wenn die Verbindung zum Internet verfügbar ist.
-   Windows-desktopanwendungen Benutzer erworben werden nicht beibehalten. Benutzer müssen manuell neu zu installieren.
-   Windows-desktopanwendungen, selbst wenn der Benutzer zuvor deinstalliert haben in die Anpassungen, die Bereitstellung Paket in dem Zustand Factory wiederhergestellt werden erfasst vorinstalliert.

Das **Aktualisieren von Ihrem PCs** -Feature wird nicht beibehalten Benutzer installiert Windows desktopanwendungen standardmäßig und Speicherorte, die häufig verwendet werden, zum Speichern von Anwendungseinstellungen (\\Anwendungsdaten und \\Ordner "ProgramData") gelöscht werden. Hersteller können die Erweiterungspunkte Drucktaste zurücksetzen, um zu speichern und zu einem späteren Zeitpunkt wiederherstellen anwendungsspezifische Einstellungen und Daten, nutzen Sie bei Bedarf.

## <a name="span-idresetyourpcspanspan-idresetyourpcspanspan-idresetyourpcspanreset-your-pc"></a><span id="Reset_your_PC"></span><span id="reset_your_pc"></span><span id="RESET_YOUR_PC"></span>Zurücksetzen von Ihrem PC


**Zurücksetzen der PC-Funktion kann in den folgenden Schritten zusammengefasst werden:**

1.  PC startet Windows Recovery Environment (Windows RE).
2.  Benutzerkonten, Daten und installierten apps für Windows und Windows-desktop-Anwendung aus dem Volume OS entfernt werden.
3.  (Wenn vom Benutzer angefordert wird), werden für Inhaltsdaten formatiert.
4.  Löschen von Daten wird (wenn vom Benutzer angefordert) Betriebssystem und Daten Volumes durchgeführt.
5.  **ERWEITERBARKEIT PUNKT C**: OEMs können optional ein Skript hier hinzufügen. (Siehe [Erweiterungspunkte](#extensibility-points) weiter unten in diesem Thema).
6.  Eine neue Kopie des Betriebssystems wird erstellt, in einem temporären Verzeichnis mit Dateien aus der Komponente Windows Store.
7.  Anpassungen, die bei der Bereitstellung Pakete unter C: gespeichert\\Wiederherstellung\\Anpassungen auf das neue Betriebssystem angewendet werden.
8.  Treiber werden vom vorhandenen Betriebssystem kopiert und in das neue Betriebssystem eingefügt.
9.  Vorinstalliertes universellen Windows-apps werden von deren Sicherungsspeicherort wiederhergestellt.
10. Vorhandene OS wurde entfernt.
11. Neue Betriebssystem wird in den Stamm des OS Datenträgers verschoben.
12. **ERWEITERBARKEIT PUNKT D**: OEMs können optional ein Skript hier hinzufügen. (Siehe [Erweiterungspunkte](#extensibility-points) weiter unten in diesem Thema).
13. PC wird auf das neue Betriebssystem neu gestartet.
14. OOBE beginnt.

### <a name="span-iddataremovaloptionsspanspan-iddataremovaloptionsspanspan-iddataremovaloptionsspandata-removal-options"></a><span id="Data_removal_options"></span><span id="data_removal_options"></span><span id="DATA_REMOVAL_OPTIONS"></span>Optionen für Daten zum Entfernen

Wenn der Benutzer das **Zurücksetzen von Ihrem PCs** -Feature verwenden, werden sie mit den Optionen angezeigt, die beeinflussen, wie, dass ihre Daten vom Computer entfernt werden.

-   Weist der PC mehrere Benutzer zugänglichen Festplatte Volumes, können Benutzer Daten aus allen Volumes oder das Windows-Volume zu entfernen.

    Das Windows-Volume ist als die Dateien erforderlich, um das Betriebssystem neu erstellen nie formatiert. Stattdessen werden Benutzerdatendateien einzeln gelöscht werden.

    Wenn Benutzer entscheidet, die Daten aus allen Datenträgern zu entfernen, werden die Datenvolumes formatiert.
    
-   Benutzer können auswählen, um ihre Dateien einfach zu löschen oder auch Löschen von Daten auf den Laufwerken durchführen, sodass die Wiederherstellung der Daten von einer anderen Person schwieriger ist.

Hersteller müssen konfigurieren benutzerdefinierte Dienstprogrammpartitionen wie folgt, um sicherzustellen, dass diese Partitionen von der Reset-Prozess nicht betroffen sind.

-   Dienstprogrammpartitionen auf Datenträgern, GUID-Partitionstabelle (GPT) sollte für UEFI-basierte PCs, die GPT\_ATTRIBUT\_PLATTFORM\_Attributsatz ERFORDERLICH. Finden Sie unter [PARTITION\_INFORMATIONEN\_GPT-Struktur](http://go.microsoft.com/fwlink/?LinkId=617162) Partitionieren Sie weitere Informationen zu GPT Attribute.
-   Für BIOS-basierte PCs müssen vom Typ 0 x 7, 0x0c, 0x0b, 0x0e, 0 x 06 und 0 x 42 Dienstprogrammpartitionen auf Datenträgern, Master Boot Record (MBR) sein.

Die Zeit, die zum Löschen von Daten ausführen, hängt von Laufwerk Geschwindigkeit, Größe der Partition, und gibt an, ob das Laufwerk mit Windows BitLocker Drive Encryption verschlüsselt ist. Die Daten Löschung Funktionalität richtet sich an Consumer und Behörden und Löschung von Branchenstandards-Daten nicht entspricht.

Wenn [Compact OS](compact-os.md) auf das Betriebssystem, bevor Sie das Zurücksetzen aktiviert ist, bleibt Compact OS aktiviert, nach dem Zurücksetzen von des PCs. 

## <a name="span-idbaremetalrecoveryspanspan-idbaremetalrecoveryspanspan-idbaremetalrecoveryspanbare-metal-recovery"></a><span id="Bare_metal_recovery"></span><span id="bare_metal_recovery"></span><span id="BARE_METAL_RECOVERY"></span>Bare-Metal-recovery


Wenn der Benutzer muss tauschen Sie ihre Festplatte oder vollständig formatieren Sie ihn, können sie startbaren Wiederherstellungsmedien bare-Metal-Recovery ausführen verwenden. Bare-Metal-Recovery entfernt alle vorhandene Partitionen auf dem Systemdatenträger und erstellt alle Partitionen vor dem Wiederherstellen der Software auf dem Computer neu. Zwei Arten von Wiederherstellungsmedien werden unterstützt:

-   **Von Benutzern erstellte Wiederherstellungsmedien** mit dem Dienstprogramm **Erstellen einer Wiederherstellungslaufwerk** in Windows 10. Dies sichert die Dateien zum Wiederherstellen des PCs-Option in einem ursprünglichen Zustand.
-   **Hersteller erstellt Wiederherstellungsmedien** für Support- und Szenarien prüfen, indem Sie ein Image-Wiederherstellung auf einem Blatt startbare Windows RE-Medien.

**Wenn von Benutzern erstellte Wiederherstellungsmedien verwendet werden, können Sie das Feature bare-Metal-Recovery in den folgenden Schritten zusammengefasst:**

1.  Der Systemdatenträger wird identifiziert.
2.  Alle Partitionen aus dem Systemdatenträger werden entfernt.
3.  Löschen von Daten erfolgt auf dem Systemdatenträger (Falls vom Benutzer angefordert).
4.  Factory oder Default Partitionslayout wird auf dem Systemdatenträger neu erstellt.
5.  Alle Partitionen formatiert werden.
6.  AutoWiederherstellen-Dateien von Wiederherstellungsmedien werden in der Lautstärke OS kopiert.
7.  Eine neue Kopie des Betriebssystems wird im Stammverzeichnis des Datenträgers OS erstellt.
8.  Anpassungen, die bei der Bereitstellung Pakete gespeichert werden angewendet.
9.  Treiber werden in das neue Betriebssystem eingefügt.
10. Vorinstallierten Windows-apps werden wiederhergestellt.
11. Startdateien werden auf der Systempartition konfiguriert.
12. PC wird auf das neue Betriebssystem neu gestartet.
13. OOBE wird gestartet.

### <a name="span-iddataremovaloptionsspanspan-iddataremovaloptionsspanspan-iddataremovaloptionsspandata-removal-options"></a><span id="Data_removal_options"></span><span id="data_removal_options"></span><span id="DATA_REMOVAL_OPTIONS"></span>Optionen zum Entfernen von Daten

Wenn Benutzer das bare-Metal-Recovery-Feature verwenden, können sie auswählen, Löschen von Daten auf dem Datenträger für die gesamte System ausführen, bevor das Factory Partitionslayout erneut angewendet wird. Diese Daten Löschvorgang erfolgt auf den meisten PCs in Software, zufälligen Muster einmal für die gesamte LBA Bereich den Systemdatenträger schreiben.

Auf bestimmten Hardwarekonfigurationen wird jedoch Löschens von Daten vom Hardware-Controller das Speichergerät ausgeführt. Dies häufig weniger Zeit für die Durchführung und ist in der Regel ausführlichere in Rest-Daten entfernt. Löschen von Daten hardwarebasierte wird von PCs mit Speichergeräten unterstützt, die die folgenden Kriterien erfüllen:

-   eMMC
-   Unterstützt die Befehle Secure Zuschneiden und Sanitize

### <a name="span-idsystemdiskselectionspanspan-idsystemdiskselectionspanspan-idsystemdiskselectionspansystem-disk-selection"></a><span id="System_disk_selection"></span><span id="system_disk_selection"></span><span id="SYSTEM_DISK_SELECTION"></span>System auswählen

Bare-Metal-Recovery erkennt automatisch den Systemdatenträger mithilfe der folgenden Methoden:

-   Pfad zum Speicherort Grafikkarte und GUID des Systemdatenträgers werden einer Variablen UEFI während OOBE geschrieben.
    -   Nur ausgeführt, wenn das System und die Windows-Partitionen auf dem Systemdatenträger sind.

    -   Die Variable wird bei Bedarf aktualisiert, wenn Windows RE ruft deaktiviert, und klicken Sie dann erneut aktiviert.

-   Wenn mehrere interne Datenträger erkannt werden, wird der Systemdatenträger während bare-Metal-Recovery in der angegebenen Reihenfolge durchsucht:
    -   Datenträger mit der GUID, die mit dem Wert in der Variablen UEFI gespeicherte übereinstimmen.
    -   Datenträger mit Pfad zum Speicherort der dem Wert in der Firmware gespeichert.
    -   Datenträger mit einer vorhandenen ESP.
        -   Wenn mehrere Datenträger mit ESP gefunden werden, wird bare-Metal-Recovery nicht fortgesetzt werden.
    -   Nicht initialisiert (unformatiert) Datenträger.
        -   Wenn mehrere nicht initialisierte Datenträger gefunden werden, wird nicht bare-Metal-Recovery fortgesetzt.
-   Der BIOS gemeldete Systemdatenträger wird auf legacy BIOS/MBR-Systemen verwendet.

### <a name="span-iduser-createdrecoverymediaspanspan-iduser-createdrecoverymediaspanspan-iduser-createdrecoverymediaspanuser-created-recovery-media"></a><span id="User-created_recovery_media"></span><span id="user-created_recovery_media"></span><span id="USER-CREATED_RECOVERY_MEDIA"></span>Von Benutzern erstellte Wiederherstellungsmedien

Wenn Benutzer USB Wiederherstellungsmedien erstellen mithilfe einer Wiederherstellung Laufwerk-Dienstprogramm erstellen enthalten die resultierenden Medien immer eine startbare Windows RE-Kopie. Dies ermöglicht Benutzern den Zugriff auf Tools für Problembehandlung und Wiederherstellung beim Starten von Wiederherstellungsmedien.

Benutzer können Dateien, die zum Durchführen von bare-Metal-Recovery benötigt optional sichern. Wenn die Option ausgewählt ist, werden die folgenden USB-Wiederherstellungsmedien sowie kopiert:

-   Windows-Komponente Store
-   Installierten Treiber
-   Sicherung der vorinstallierten Windows-apps
-   Pakete mit vorinstallierten Anpassungen Provisioning (unter C:\\Wiederherstellung\\Anpassungen)
-   Drucktaste Reset-Konfigurations-XML und Skripts (unter C:\\Wiederherstellung\\OEM)

### <a name="span-idmanufacturer-createdrecoverymediaspanspan-idmanufacturer-createdrecoverymediaspanspan-idmanufacturer-createdrecoverymediaspanmanufacturer-created-recovery-media"></a><span id="Manufacturer-created_recovery_media"></span><span id="manufacturer-created_recovery_media"></span><span id="MANUFACTURER-CREATED_RECOVERY_MEDIA"></span>Hersteller erstellt Wiederherstellungsmedien

Bare-Metal-Recovery unterstützt die Verwendung von WIM-Image-Wiederherstellung, wenn das Medium Hersteller vorbereitet werden. Diese Art von Medien wird hauptsächlich in Support- und prüfen Szenarien verwendet.

Hersteller erstellt Medien müssen Folgendes enthalten:

1.  Eine startbare Windows RE-Abbild.
2.  Drucktaste Reset-kompatiblen Image-Wiederherstellung (install.wim).
3.  Eine Drucktaste zurücksetzen Konfigurationsdatei (Resetconfig.xml) die Datenträger Partitionierung Informationen angibt.
4.  Ein DISKPART-Skript zum Ausführen der Partitionierung der Festplatte.

### <a name="span-idextensibilitypointsspanspan-idextensibilitypointsspanextensibility-points-for-push-button-reset-features"></a><span id="extensibility_points"></span><span id="EXTENSIBILITY_POINTS"></span>Erweiterungspunkte für Drucktaste Reset-features

Drucktaste zurücksetzen bietet Erweiterbarkeitspunkte der Hersteller benutzerdefinierte Vorgänge einfügen können, wenn ein Benutzer auf **Ihrem PC aktualisieren** und **Zurücksetzen der PC** -Features ausführt.

Finden Sie in den Abschnitten oben, um zu sehen, die benutzerdefinierte Vorgänge, die für diese Funktionen ausgeführt werden können, in dem angezeigt.

In der folgenden Tabelle sind die Erweiterungspunkte für **Ihren PC Refresh** zusammengefasst:

|            |                                                                                                                            |                                                                                                                                                   |
|------------|----------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Erw. Punkt | Systemstatus                                                                                                               | Verwendungsbeispiel                                                                                                                                     |
| Ein          | Einstellungen und Daten werden migriert wurden an einen temporären Speicherort verschoben                                                   | Kopieren von Dateien, Treiber oder Einstellungen, die standardmäßig nicht migriert werden, wenn der Benutzer der Aktualisierung Ihrer PC-Funktion ausgeführt wird.                                 |
| B          | Das Betriebssystem wurde neu erstellt. Treiber und Anpassungen haben erneut angewendet wurde. Nur wichtige Systemeinstellungen wurden migriert. | Wiederherstellen von Setupanpassungsdateien (z. B. unattend.xml, layoutmodification.xml) oder Dateien und Einstellungen, die Sie möglicherweise auf Erweiterbarkeit Abschnitt a gesichert haben |

 

In der folgenden Tabelle sind die Erweiterungspunkte für **Ihren PC zurücksetzen** zusammengefasst:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Erw. Punkt</td>
<td align="left">Systemstatus</td>
<td align="left">Verwendungsbeispiel</td>
</tr>
<tr class="even">
<td align="left">C</td>
<td align="left">Alle Benutzerdaten aus der Windows-Partition entfernt wurden und Datenpartitionen haben (optional) formatiert wurde.</td>
<td align="left">Konfigurieren Sie Datenpartitionen bei Bedarf neu.
<div class="alert">
<strong>Wichtig</strong>  Ändern Sie die Windows-Partition nicht.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left">D</td>
<td align="left">Das Betriebssystem wurde neu erstellt. Treiber und Anpassungen haben erneut angewendet wurde.</td>
<td align="left">Wiederherstellen von Anpassungsdateien (z. B. unattend.xml, layoutmodification.xml), oder wenden Sie zusätzliche erforderliche Anpassungen vor.</td>
</tr>
</tbody>
</table>

 

## <a name="span-idcompactosspanspan-idcompactosspanspan-idcompactosspancompact-os"></a><span id="Compact_OS"></span><span id="compact_os"></span><span id="COMPACT_OS"></span>Compact OS


Compact OS ist eine Auflistung von Technologien die ermöglichen Windows 10 mit so niedrig wie 16 Gigabyte (GB) die Speicherkapazität auf PCs bereitgestellt werden. Die folgenden beiden Technologien arbeiten insbesondere in Verbindung mit den Änderungen Drucktaste zurücksetzen zur Reduzierung der Windows Datenträger Bilanz auf:

-   Pro Datei Komprimierung beim Anwenden einer Bilddatei Verweis (WIM) auf einem PC der Dateien auf den Datenträger geschrieben kann einzeln über die XPRESS Huffman-Codec komprimiert werden. Dies ist mit dem gleichen Codec durch die WIMBoot-Technologie in Windows 8.1. Wenn Drucktaste zurücksetzen Features neu erstellt, wird das Betriebssystem, bleiben die Systemdateien Runtime komprimiert.
-   Single instancing von installierten Anpassungen nach die installierten Anpassungen (z. B. Windows desktopanwendungen) erfasst wurden (über ScanState) in eine Referenz Bildtyp Daten gespeichert in einem Paket provisioning, können zwei Kopien der Anpassungen Datenträger Bilanz Auswirkungen reduzieren singled-Variante sein. Dies geschieht durch die installierten Anpassungen konvertieren (z. B. C:\\Program Files\\"Foo"\\Foo.exe) in der Datei Zeiger auf den Inhalt des Bilds Verweis Gerät Daten verknüpft.

Das folgende Diagramm veranschaulicht die allgemeine Inhaltslayout von PCs mit Compact OS aktiviert:

![Das Diagramm zeigt die Partitionsstruktur. Die OS Partition enthält die Laufzeit OS und Bereitstellung Pakete, die im C:\Recovery\Customizations sind. Das Betriebssystem Common Language Runtime wird komprimiert. Desktop-apps werden bei der Bereitstellung der Pakete, im Ordner C:\Recovery\Customizations, und diese Bereitstellung Pakete komprimiert werden. Führen Sie den desktop-apps verwendet die Laufzeit OS Datei Zeiger, die zur Bereitstellung Paket zu wechseln.](images/dep-winre-compactos.png)

Beide Technologien sind optional und können während der Bereitstellung konfiguriert werden.

## <a name="span-idupdatingtheon-diskwindowsrecoveryenvironmentspanspan-idupdatingtheon-diskwindowsrecoveryenvironmentspanspan-idupdatingtheon-diskwindowsrecoveryenvironmentspanupdating-the-on-disk-windows-recovery-environment"></a><span id="Updating_the_on-disk_Windows_Recovery_Environment"></span><span id="updating_the_on-disk_windows_recovery_environment"></span><span id="UPDATING_THE_ON-DISK_WINDOWS_RECOVERY_ENVIRONMENT"></span>Aktualisieren die auf dem Datenträger Windows Recovery-Umgebung


Im Windows-10 kann die Kopie auf dem Datenträger von Windows RE als Teil des Rollupupdates für das Betriebssystem verarbeitet werden. Nicht alle Rollupupdates werden Windows RE-service.

Windows RE nicht nicht direkt bedient Updates im Gegensatz zu den normalen OS Update-Prozess (winre.wim) für die Windows RE-Abbild auf dem Datenträger. Stattdessen ersetzt eine neuere Version des Windows RE-Abbilds den vorhandenen, durch den folgenden Inhalt eingefügt oder in das neue Bild migriert werden:

-   Wichtige starten, und das neue Windows RE-Abbild Treiber aus der vollständigen OS Umgebung hinzugefügt werden.
-   Windows RE Anpassungen unter \\Quellen\\Wiederherstellung von der bereitgestellten winre.wim auf das neue Bild migriert.

Der folgende Inhalt aus der vorhandenen Windows RE-Abbild werden nicht in das neue Bild migriert:

-   Die in der vorhandenen Windows RE-Abbild jedoch nicht in der vollständigen OS Umgebung sind Treiber
-   Windows PE optionale Komponenten, die nicht Teil der Windows RE Standardbild sind
-   Language Packs für Windows PE und optionalen Komponenten

Der Aktualisierungsprozess Windows RE intensiv an die vorhandene Windows RE-Partition ohne Änderung wiederverwenden. In einigen seltenen Fällen, in dem das neue Windows RE-Bild (zusammen mit der migriert/eingefügten Inhalt) nicht in der vorhandenen Windows RE-Partition passt, wird der Aktualisierungsprozess jedoch wie folgt Verhalten:

-   Wenn die vorhandene Windows RE-Partition unmittelbar nach der Windows-Partition befindet, wird die Windows-Partition verkleinert, und Speicherplatz wird Windows RE-Partition hinzugefügt werden. Das neue Windows RE-Bild wird auf die erweiterten Windows RE-Partition installiert werden.
-   Wenn die vorhandene Windows RE-Partition unmittelbar nach der Windows-Partition nicht gefunden wird, wird die Windows-Partition verkleinert, und eine neue Windows RE-Partition erstellt werden. Das neue Windows RE-Bild wird auf diese neuen Windows RE-Partition installiert werden. Die vorhandene Windows RE-Partition werden verwaist.
-   Wenn die vorhandene Windows RE-Partition kann nicht wiederverwendet werden und die Windows-Partition kann nicht erfolgreich verkleinert werden, wird das neue Windows RE-Bild auf der Windows-Partition installiert werden. Die vorhandene Windows RE-Partition werden verwaist.

**Wichtig**  Um sicherzustellen, dass Ihre Anpassungen weiterhin ausgeführt werden, nachdem Windows RE aktualisiert wurde, müssen sie nicht hängen von Funktionen von Windows PE optionale Komponenten, die nicht in der Windows RE-Standardbild (z. B. Windows PE-NetFX) sind bereitgestellt. Um die Entwicklung von Windows RE Anpassungen zu erleichtern, wurde das Standardbild Windows RE in Windows 10 die optionale Komponente Windows PE HTA hinzugefügt.

 

**Hinweis**  Das neue Windows RE-Bild als Teil des Updates Rollup bereitgestellt enthält Sprachressourcen nur für die Standardsprache des Systems, auch wenn das vorhandene Windows RE-Abbild Ressourcen für mehrere Sprachen enthält. Auf den meisten PCs ist die Standardsprache des Systems die Sprache, die zum Zeitpunkt der OOBE ausgewählt.

 

 

 





