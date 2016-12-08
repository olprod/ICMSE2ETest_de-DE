---
author: Justinha
Description: "Deployment Image Servicing and Management (DISM) bewährte Methoden"
ms.assetid: b9629ef4-9b4f-47c4-8eca-d2469cfcbd9b
MSHAttr: PreferredLib:/library/windows/hardware
title: "Deployment Image Servicing and Management (DISM) bewährte Methoden"
ms.openlocfilehash: a4013207c60781e56f55ec0144617b55d11c7e22
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deployment-image-servicing-and-management-dism-best-practices"></a>Deployment Image Servicing and Management (DISM) bewährte Methoden


In diesem Abschnitt werden einige bewährten Methoden im Zusammenhang mit Warten eines Abbilds Windows® beschrieben. Es wird empfohlen, dass Sie diese Methoden nach Möglichkeit implementieren.

In diesem Thema:

[Berechtigungsebenen Sie für Befehlszeilentools](#bkmk-elevate)

[Deaktivieren von Antivirus-Tools](#bkmk-av)

[Warten eines Abbilds](#bkmk-servicing)

[Ändern der internationale Einstellungen](#bkmk-intl)

[Verwenden von Protokolldateien](#bkmk-log)

[Paket-Speicherorte](#bkmk-pkg)

[Speichern von Dateien auf einer Netzwerkfreigabe](#netshare)

[Warten eines Windows-Abbilds von Windows PE](#bkmk-pe)

[Suchen nach einer Beschädigung und überprüfen Sie die Integrität der Systemdateien](#bkmk-verify)

[Verbessern der Sicherheit für Windows-Bilder](#security)

## <a name="span-idbkmkelevatespanspan-idbkmkelevatespanspan-idbkmkelevatespanelevate-permissions-for-command-line-tools"></a><span id="BKMK_elevate"></span><span id="bkmk_elevate"></span><span id="BKMK_ELEVATE"></span>Erhöhen der Berechtigungen für Befehlszeilentools


Viele Bereitstellung-Befehlszeilentools, einschließlich Deployment Image Servicing and Management (DISM) sind mit erhöhten Berechtigungen erforderlich.

Stellen Sie sicher, dass Sie Berechtigungen erweiterte. Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

Dies muss erfolgen, auch wenn Sie als Administrator angemeldet sind.

## <a name="span-idbkmkavspanspan-idbkmkavspanspan-idbkmkavspandisable-antivirus-tools"></a><span id="BKMK_av"></span><span id="bkmk_av"></span><span id="BKMK_AV"></span>Deaktivieren von Antivirus-Tools


Einige DISM-Befehle können durch Antivirus oder Modul Tools blockiert werden. Deaktivieren Sie vor der Wartung Schwelle, Antivirus oder Modul-Tools auf dem Referenzcomputer.

## <a name="span-idbkmkservicingspanspan-idbkmkservicingspanspan-idbkmkservicingspanservicing-an-image"></a><span id="BKMK_servicing"></span><span id="bkmk_servicing"></span><span id="BKMK_SERVICING"></span>Warten eines Abbilds


Die beste Möglichkeit, eine Windows-Abbild ist mit dem Tool DISM offline. DISM kann verwendet werden, zu installieren, deinstallieren, konfigurieren und Aktualisieren von Treibern, Features und Paketen in Windows-Abbildern und Abbildern Windows Vorinstallation Environment (Windows PE) ohne das Abbild zu starten. Weitere Informationen finden Sie unter [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

Die Option **/Commit-Image** können zu einem beliebigen Zeitpunkt während der Wartung um die Änderungen zu speichern, die Sie bisher vorgenommen haben. Wenn Sie Ihre Änderungen häufig ausgeführt haben, können Sie eine beschädigte Abbild leichter mit der Option **/Cleanup-Image /RestoreHealth** wiederherstellen.

Sie können bereitstellen und mehrere Bilder auf einem einzelnen Computer ändern. Jedoch beeinträchtigen Leistung auf einige Funktionen, wie **/Unmount-Image**, je nach den Arbeitsspeicher auf dem Computer verfügbar. Es empfiehlt sich sollten Sie nicht mehr als 20 Bilder zur selben Zeit bereitstellen.

**Hinweis**  
Wenn Sie eine WIM-Datei in kleinere Dateien aufteilen und auf mehrere Medien geteilt haben, wird Sie nicht das Bild für die Wartung bereitstellen.

 

## <a name="span-idbkmkintlspanspan-idbkmkintlspanspan-idbkmkintlspanchanging-international-settings"></a><span id="BKMK_intl"></span><span id="bkmk_intl"></span><span id="BKMK_INTL"></span>Ändern der internationale Einstellungen


Um die internationalen Einstellungen in Windows 10, Windows 8.1, Windows 8, Windows Server 2016 – Technische Vorschau, Windows Server 2012 R2, Windows Server 2012, Windows 7 und Windows Server 2008 R2 Bilder zu ändern, müssen Sie DISM verwenden. Weitere Informationen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

## <a name="span-idbkmklogspanspan-idbkmklogspanspan-idbkmklogspanuse-log-files"></a><span id="BKMK_log"></span><span id="bkmk_log"></span><span id="BKMK_LOG"></span>Verwenden von Protokolldateien


DISM protokolliert ausführliche Informationen zu %windir%\\Protokolle\\Dism\\Dism.log standardmäßig. Sie können auch einen Namen und Speicherort Ihrer Wahl für die Protokolldatei angeben und **/loglevel** Parameter festlegen, sodass nur die Informationen, die, der Sie interessiert sind, angemeldet ist. Wenn ein Fehler auftritt, wird die Konsole den Fehlercode, Fehlermeldung und den Speicherort der Protokolldatei angezeigt.

**Wichtige**  
Wenn Sie einen Protokollpfad auf einer Netzwerkfreigabe auf einem Computer, die nicht Mitglied einer Domäne ist angeben, verwenden Sie Net-Verwendung mit Anmeldeinformationen für die Domäne, um Zugriffsberechtigungen festzulegen, bevor Sie den Protokollpfad für das DISM-Protokoll festlegen.

 

Die Protokolldatei wird automatisch archiviert werden. Mit bak an den Dateinamen angefügt wird die archivierte Protokolldatei gespeichert werden, und eine neue Protokolldatei generiert werden. Jedes Mal, wenn die Protokolldatei archiviert wird, wird die BAK-Datei überschrieben.

Die Protokolldatei können Sie den Verlauf von die Vorgänge durchgeführt, die Behandlung von Problemen kann.

## <a name="span-idbkmkpkgspanspan-idbkmkpkgspanspan-idbkmkpkgspanpackage-locations"></a><span id="BKMK_pkg"></span><span id="bkmk_pkg"></span><span id="BKMK_PKG"></span>Paket-Speicherorte


Stellen Sie kein Paket, das Sie direkt am Stamm einer Partition auf einem Windows-Installation installieren möchten.

## <a name="span-idnetsharespanspan-idnetsharespanspan-idnetsharespanstoring-files-on-a-network-share"></a><span id="NetShare"></span><span id="netshare"></span><span id="NETSHARE"></span>Speichern von Dateien auf einer Netzwerkfreigabe


Obwohl DISM Netzwerkpfade für Bilder und Paketen unterstützt, werden die meisten Vorgänge schneller für Dateien ausführen, die auf die lokale Festplatte kopiert werden.

## <a name="span-idbkmkpespanspan-idbkmkpespanservicing-a-windows-image-from-winpe"></a><span id="BKMK_PE"></span><span id="bkmk_pe"></span>Warten eines Windows-Abbilds von Windows PE


Sie können Windows Bilder aus Windows PE-service. Sie müssen jedoch bestimmte Faktoren berücksichtigen, während der Planung Ihrer Strategie für die Wartung. Überprüfen Sie die folgenden Anforderungen zum Warten eines Abbilds von Windows PE.

### <a name="span-idbootingwinpefromaharddrivespanspan-idbootingwinpefromaharddrivespanspan-idbootingwinpefromaharddrivespanbooting-winpe-from-a-hard-drive"></a><span id="Booting_WinPE_from_a_Hard_Drive"></span><span id="booting_winpe_from_a_hard_drive"></span><span id="BOOTING_WINPE_FROM_A_HARD_DRIVE"></span>Starten Windows PE von einer Festplatte

Für eine bessere Leistung können Sie zusätzlichen Arbeitsspeicher zuweisen, wenn Sie von einem Festplattenlaufwerk mit Windows PE starten. Sie können auch die temporären Ordner zum Speichern der Updatedateien um umfangreiche Updates erstellen.

### <a name="span-idaddpage-filesupporttoyourwinpeimagespanspan-idaddpage-filesupporttoyourwinpeimagespanspan-idaddpage-filesupporttoyourwinpeimagespanadd-page-file-support-to-your-winpe-image"></a><span id="Add_Page-File_Support_to_Your_WinPE_Image"></span><span id="add_page-file_support_to_your_winpe_image"></span><span id="ADD_PAGE-FILE_SUPPORT_TO_YOUR_WINPE_IMAGE"></span>Auslagerungsdatei Unterstützung zum Windows PE-Abbild hinzufügen

Stellen Sie sicher, dass Sie genügend Speicher zum Laden und Ausführen von Ihr benutzerdefiniertes Windows PE-Abbild verfügen. Zusätzlich zu der Größe des Bilds benötigen Sie mindestens 256 MB Arbeitsspeicher verfügbar. Arbeitsspeicher zur Verfügung steht, definieren Sie eine Auslagerungsdatei (Pagefile.sys), um die Speicherverwaltung zu verbessern. Weitere Informationen zum Implementieren einer Auslagerungsdatei finden Sie unter [Wpeutil Command-Line Options](wpeutil-command-line-options.md).

### <a name="span-idcreateatemporarydirectoryinwhichtostoreupdatefilesspanspan-idcreateatemporarydirectoryinwhichtostoreupdatefilesspanspan-idcreateatemporarydirectoryinwhichtostoreupdatefilesspancreate-a-temporary-directory-in-which-to-store-update-files"></a><span id="Create_a_Temporary_Directory_in_Which_to_Store_Update_Files"></span><span id="create_a_temporary_directory_in_which_to_store_update_files"></span><span id="CREATE_A_TEMPORARY_DIRECTORY_IN_WHICH_TO_STORE_UPDATE_FILES"></span>Erstellen Sie ein temporäres Verzeichnis, in dem die Aktualisierungsdateien gespeichert

Verwenden die **Option/ScratchDir** sollte Sie mit DISM erstellen Sie ein temporäres Verzeichnis auf ein anderes Laufwerk beim Erstellen oder ein Windows-Abbild-Dienst. Ein temporäres Verzeichnis wird für das Aufzeichnen eines Abbilds, Installieren von Language Packs, Installieren von Updates, oder installieren oder Entfernen von Windows-Features in einem Windows-Abbild einschließlich viele DISM-Vorgänge verwendet. Einige Dateien werden in diesem temporären Verzeichnis erweitert, bevor sie auf einem Windows-Abbild angewendet werden.

In der Partition für umfangreiche Updates muss ausreichend Speicherplatz vorhanden sein. Die bestimmte Größe der freie Speicherplatz, die erforderlich ist, hängt von der Größe der Updates, die Sie installieren möchten. Beim Hinzufügen eines Sprachpakets muss das Scratch Verzeichnis mindestens 1 GB Speicherplatz für temporäre Dateien enthalten.

Wenn Sie einen temporäres Verzeichnispfad mit der **Option/ScratchDir** nicht festlegen, wird Windows PE ein temporäres Verzeichnis 32 MB standardmäßig erstellt. Sie können zusätzlichen temporären Speicher verwendet, um diese mit der Option **DISM/Set-ScratchSpace** Standardspeicherort zuweisen. Gültige Größen sind 32, 64, 128, 256 und 512 MB. Dieses Feature ist nur offline verfügbar, und Sie können diese Einstellung während eine Windows PE-Sitzung läuft nicht anpassen. Es empfiehlt sich sollten Sie die **Option/ScratchDir** verwenden, Sie stattdessen ein Verzeichnis auf einer anderen Partition angeben, ausreichend Speicherplatz zur Unterstützung von alle Image-Verwaltung und Wartungsvorgänge an, die ausgeführt werden.

Nach Abschluss der Installation wird der Inhalt des Verzeichnisses werden nicht mehr benötigt und können gelöscht werden. Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

### <a name="span-idbootingwinpefromacd-romdvdspanspan-idbootingwinpefromacd-romdvdspanspan-idbootingwinpefromacd-romdvdspanbooting-winpe-from-a-cd-romdvd"></a><span id="Booting_WinPE_from_a_CD-ROM_DVD"></span><span id="booting_winpe_from_a_cd-rom_dvd"></span><span id="BOOTING_WINPE_FROM_A_CD-ROM_DVD"></span>Starten Windows PE von einer CD-ROM/DVD

Warten eines Windows-Abbilds ist zusätzlicher temporärer Speicherplatz erforderlich. Für Windows PE RAM-Datenträger möglicherweise mehr Arbeitsspeicher erforderlich. Zusätzlich zu den erforderlichen Arbeitsspeicher Windows PE-Abbild ist zusätzlicher RAM benötigt, um die Prozess-Updates. Der Menge an RAM, die erforderlich ist, hängt von der Größe der Updates, die Sie anwenden möchten. Stellen Sie sicher, dass Ihr Computer über ausreichend RAM verfügt.

## <a name="span-idbkmkverifyspanspan-idbkmkverifyspanspan-idbkmkverifyspanscan-for-corruption-and-verify-the-integrity-of-system-files"></a><span id="BKMK_verify"></span><span id="bkmk_verify"></span><span id="BKMK_VERIFY"></span>Suchen nach einer Beschädigung und überprüfen Sie die Integrität der Systemdateien


Bevor Sie einen Computer an Endbenutzer übermitteln, sollten Sie die Integrität der Windows-Systemdateien überprüfen. Die Option **/Cleanup-Image** können Sie eine Beschädigung der Datei zu identifizieren, und führen Sie Reparaturen auf das Bild. Weitere Informationen zur Option **/Cleanup-Image** DISM finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

Sie können auch auf ein Bild online oder offline Verweis Systemdatei (Sfc.exe) verwenden. Systemdatei wird mit allen Versionen von freigegeben Windows.System Datei Checker erhöhte Berechtigungen benötigt, und Sie müssen ein Administrator für die Ausführung. Alle geschützte Dateien, um zu überprüfen, die Dateiversionen gescannt. Führen Sie die Option **sfc.exe/VERIFYONLY** , um nur die Integrität der Windows-Systemdateien zu überprüfen. Geben Sie für vollständige Befehlszeilensyntax an einer Eingabeaufforderung mit erhöhten Rechten **sfc.exe /?**.

Ausführen von Sfc.exe, kann sehr viel Zeit dauern. Das erwartete Ergebnis ist, dass kein System Integrität Verstöße vorhanden sind. Wenn Probleme mit der Windows-Systemdateien vorhanden sind, sollten Sie die Probleme untersuchen. Nicht empfohlen, dass Sie die Sfc.exe Scan-Optionen verwenden, um die Windows-Systemdateien nicht automatisch korrigiert.

## <a name="span-idsecurityspanspan-idsecurityspanspan-idsecurityspanimproving-security-for-windows-images"></a><span id="Security"></span><span id="security"></span><span id="SECURITY"></span>Verbessern der Sicherheit für Windows-Bilder


Ihre Windows-Abbilder enthalten benutzerdefinierten Konfigurationsdaten, benutzerdefinierte Anwendungen und anderem geistigen Eigentum. Sie haben verschiedene Möglichkeiten zur Verbesserung der Sicherheit Ihrer Windows-Bilder, online und offline.

-   **Einschränken des Zugriffs auf Windows-Abbilder**. Je nach Ihrer Umgebung können Sie die Zugriffssteuerungslisten (ACLs) oder die Berechtigungen für eine Datei bearbeiten. Nur genehmigte Konten haben Zugriff auf Windows-Abbilder.

-   **Aktualisieren Sie Ihre Windows-Abbilder mit der neuesten Patches und Softwareupdates**. Es gibt viele Methoden können Sie ein Windows-Abbild service. Prüfen Sie nach der Warten des Windows-Abbilds die Gültigkeit und Stabilität des Computers.

-   **Konfigurieren Sie den Computer aus, um das automatische Herunterladen und Installieren von Windows-Updates während der Windows-Installation**. Dies erweitert Installationsdauer, aber es wird sichergestellt, dass das Windows-Abbild, das Sie installieren die neuesten Updates enthält. Weitere Informationen finden Sie unter der `DynamicUpdate` festlegen in der Microsoft-Windows-Setup-Komponente in der **Referenz für unbeaufsichtigte Windows**.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

 

 






