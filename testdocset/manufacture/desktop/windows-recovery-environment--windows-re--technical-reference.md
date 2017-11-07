---
author: Justinha
Description: Windows Recovery Environment (Windows RE)
ms.assetid: af78b72b-9f45-4ac3-882b-411a2bafbeed
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows Recovery Environment (Windows RE)
ms.openlocfilehash: 7354f7e5c0c7b56630103236d121345cf5d84477
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-recovery-environment-windows-re"></a>Windows Recovery Environment (Windows RE)


Windows Recovery Environment (WinRE) ist eine RecoveryUmgebung, die häufige Ursachen für nicht startbaren Betriebssysteme reparieren kann. WinRE basiert auf Windows-Vorinstallation Environment (Windows PE), und kann mit zusätzlichen Treiber, Sprachen, Windows PE optionale Komponenten und andere Tools zur Problembehandlung und Diagnose angepasst werden. In der Standardeinstellung ist in der Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) und Windows Server 2016 Installationen WinRE geladen.

![Screenshot zeigt Optionen: fortgesetzt, verwenden Sie ein Gerät, Problembehandlung, oder deaktivieren Sie Ihren PC](images/dep-winre-menu.png)

## <a name="span-idwhatsnewwithwinreforwindows10spanspan-idwhatsnewwithwinreforwindows10spanspan-idwhatsnewwithwinreforwindows10spanwhats-new-with-winre-for-windows-10"></a><span id="What_s_new_with_WinRE_for_Windows_10_"></span><span id="what_s_new_with_winre_for_windows_10_"></span><span id="WHAT_S_NEW_WITH_WINRE_FOR_WINDOWS_10_"></span>Was ist neu bei WinRE für Windows 10?


-   Standardmäßig bei der Installation von Windows mithilfe von Medium aus Windows Imaging und Konfiguration Designer (ICD) erstellt erhalten eine dedizierte WinRE Tools Partition auf UEFI und BIOS-basierten Geräten befindet sich unmittelbar nach der Windows-Partition Sie. Dadurch wird Windows ersetzen und Ändern der Größe der Partition bei Bedarf. (Wenn Sie Windows mithilfe von Windows Setup installieren, Sie dasselbe Partitionslayout, das Sie in Windows 8.1 haben erhalten.)
-   Wenn Sie [ein benutzerdefiniertes Tool zum Menü Optionen Boot WinRE hinzufügen](add-a-custom-tool-to-the-windows-re-boot-options-menu.md), es nur optionale Komponenten verwenden können, die bereits in der Standardeinstellung WinRE Tools sind. Bei einer Windows 8-app, die von der optionalen Komponenten .NET abhängig, müssen Sie die app für Windows 10 umzuschreiben.
-   Wenn Sie [ein benutzerdefiniertes Tool zum Menü Optionen Boot WinRE hinzufügen](add-a-custom-tool-to-the-windows-re-boot-options-menu.md), es in platziert werden muss, die \\Quellen\\Wiederherstellung\\Tools Ordner, sodass er nach künftiger Upgrades von WinRE Arbeit fortsetzen kann.
-   Beim Hinzufügen von Sprachen zu den Tools Drucktaste zurücksetzen müssen Sie jetzt die optionale Komponente Windows PE HTA hinzufügen.

## <a name="span-idtoolsspanspan-idtoolsspanspan-idtoolsspantools"></a><span id="Tools"></span><span id="tools"></span><span id="TOOLS"></span>Tools


WinRE umfasst die folgenden Tools:

-   **Automatische Reparatur und andere Tools zur Problembehandlung**. Weitere Informationen finden Sie unter [Problembehandlung bei Windows RE-Features](windows-re-troubleshooting-features.md).
-   **Drucktaste zurücksetzen** (Windows-10 für desktop-Editionen, Windows 8.1 und nur Windows 8). Dieses Tool ermöglicht es Benutzern ihrer eigenen PCs schnell repariert Beibehaltung von Daten und wichtige Anpassungen ohne zum Sichern von Daten im voraus. Weitere Informationen finden Sie unter [Übersicht über die Push-Button zurückgesetzt](push-button-reset-overview.md).
-   **Wiederherstellung des Systems Bild** (WindowsServer 2016, Windows Server 2012 R2 und WindowsServer 2012 nur). Dieses Tool stellt die gesamte Festplatte wieder her. Weitere Informationen finden Sie unter [Wiederherstellen, das Betriebssystem oder den vollständigen Server](http://go.microsoft.com/fwlink/p/?LinkID=225039).

Darüber hinaus können Sie eigene benutzerdefinierte Lösung mithilfe der [Windows-Imaging-API](http://go.microsoft.com/fwlink/p/?LinkId=245837)oder mithilfe der [Deployment Image Servicing and Management (DISM) API](http://go.microsoft.com/fwlink/p/?LinkID=245836)erstellen.

## <a name="span-identrypointsintowinrespanspan-identrypointsintowinrespanspan-identrypointsintowinrespanentry-points-into-winre"></a><span id="Entry_points_into_WinRE"></span><span id="entry_points_into_winre"></span><span id="ENTRY_POINTS_INTO_WINRE"></span>Einstiegspunkte WinRE


Ihre Benutzer können WinRE Features mithilfe **der Startoptionen** zugreifen, die von Windows auf unterschiedliche Weise ein paar gestartet werden können:

-   Im Anmeldebildschirm auf Herunterfahren, und halten Sie die UMSCHALTTASTE gedrückt und wählen **neu starten**.
-   Wählen Sie im Windows-10, **Starten Sie** &gt; **Einstellungen** &gt; **Update & Sicherheit** &gt; **Wiederherstellung** &gt; unter **Erweiterte Start**, klicken Sie auf **jetzt neu starten**.
-   Zu Wiederherstellungsmedien starten.
-   Verwenden Sie eine [Recovery-Taste (oder Tastenkombination)](add-a-hardware-recovery-button-to-start-windows-re.md) vom OEM konfiguriert.

Nachdem Sie eine der folgenden Aktionen wird ausgeführt, benutzersitzungen für alle deaktiviert angemeldet sind und **der Startoptionen** wird angezeigt. Wenn Ihre Benutzer-wählen Sie ein Feature WinRE über dieses Menü der PC-Option in WinRE und des ausgewählten Features Neustart gestartet werden.

WinRE beginnt automatisch nach erkennt die folgenden Probleme:

-   Zwei aufeinander folgende Fehler Versuche, Windows zu starten.
-   Zwei aufeinander folgende unerwartetes Herunterfahren, die innerhalb von zwei Minuten der Fertigstellung Boot auftreten.
-   Eine Secure Boot-Fehler (mit Ausnahme von Problemen im Zusammenhang mit "Bootmgr.EFI").
-   Ein BitLocker-Fehler auf reinen Geräten.

### <a name="span-idbootoptionsmenuspanspan-idbootoptionsmenuspanspan-idbootoptionsmenuspanboot-options-menu"></a><span id="Boot_options_menu"></span><span id="boot_options_menu"></span><span id="BOOT_OPTIONS_MENU"></span>Startmenü-Optionen

Dieses Menü ermöglicht Ihren Benutzern diese Aktionen ausführen:

-   Starten Sie die Wiederherstellung, Problembehandlung und Diagnosetools.
-   Starten von einem Gerät (nur UEFI) ein.
-   Greifen Sie auf das Menü **Firmware** (nur UEFI).
-   Wählen Sie zum Starten des Betriebssystems aus, wenn mehrere Betriebssysteme auf dem Computer installiert sind.

**Hinweis**  
Sie können ein benutzerdefiniertes Tool für **die Startoptionen** hinzufügen. Andernfalls können nicht weiter diese Menüs angepasst werden. Weitere Informationen finden Sie unter [Hinzufügen ein benutzerdefiniertes Tool zum Menü Windows RE Boot Optionen](add-a-custom-tool-to-the-windows-re-boot-options-menu.md).

 

## <a name="span-idsecurityconsiderationsspanspan-idsecurityconsiderationsspanspan-idsecurityconsiderationsspansecurity-considerations"></a><span id="Security_considerations"></span><span id="security_considerations"></span><span id="SECURITY_CONSIDERATIONS"></span>Hinweise zur Sicherheit


Bei der Arbeit mit WinRE Beachten Sie sollten diese Sicherheitsaspekte:

-   Wenn Benutzer öffnen das Menü **Startoptionen** aus und wählen Sie ein Tool WinRE, müssen sie den Benutzernamen und das Kennwort für ein lokales Benutzerkonto mit Administratorrechten angeben.
-   Standardmäßig ist die Netzwerke in WinRE deaktiviert. Sie können auf das Netzwerk bei Bedarf aktivieren. Jedoch wird empfohlen, Netzwerk, wenn Sie nicht die Konnektivität benötigen zu deaktivieren.

## <a name="span-idcustomizingwinrespanspan-idcustomizingwinrespanspan-idcustomizingwinrespancustomizing-winre"></a><span id="Customizing_WinRE"></span><span id="customizing_winre"></span><span id="CUSTOMIZING_WINRE"></span>WinRE anpassen


Sie können durch Hinzufügen von Lösungspaketen (Windows PE optionale Komponenten), Sprachen, Treibern und benutzerdefinierte Tools von Diagnose- und Problembehandlungsinformationen WinRE anpassen. Die Basis WinRE-Image umfasst diese Windows PE optionale Komponenten:

-   Microsoft Windows Foundation-Paket
-   Windows PE-EnhancedStorage
-   Windows PE-Rejuv
-   Windows PE für das Skripting
-   Windows PE-SecureStartup
-   Windows PE-Setup
-   Windows PE SRT
-   Windows PE-WDS-Tools
-   Windows PE WMI
-   Windows PE-StorageWMI-Paket (auf der Basis Bild in Windows 8.1 und Windows Server 2012 R2 hinzugefügt)
-   Windows PE-HTA (die Basis-Image in Windows 10 hinzugefügt)

**Hinweis**  
Die Anzahl der Pakete, Sprachen und Treiber wird durch die Menge des Arbeitsspeichers zur Verfügung, auf dem Computer begrenzt. Aus Leistungsgründen wird empfohlen, dass Sie minimieren die Anzahl der Sprachen, Treiber und Tools, das das Bild hinzugefügt.

 

## <a name="span-idharddrivepartitionsspanspan-idharddrivepartitionsspanspan-idharddrivepartitionsspanhard-drive-partitions"></a><span id="Hard_drive_partitions"></span><span id="hard_drive_partitions"></span><span id="HARD_DRIVE_PARTITIONS"></span>Partitionen


Wenn Sie Windows mithilfe von Windows Setup installieren, wird die WinRE wie folgt konfiguriert:

1.  Während der Installation von Windows bereitet Windows die Festplattenpartitionen WinRE unterstützen.
2.  Windows platziert die Bilddatei WinRE (winre.wim) in der Windows-Partition zunächst in die \\Windows\\System32\\Datenwiederherstellung (Ordner).

    Vor der Bereitstellung von der PC-Option für Ihre Kunden, können Sie ändern oder ersetzen WinRE Bilddatei an, um zusätzliche Sprachen, Treiber oder Pakete enthalten.

3.  Während des Konfigurationsdurchgangs wird die Bilddatei WinRE in die Wiederherstellung Tools Partition kopiert, damit das Gerät auf die Wiederherstellungstools gestartet werden kann, selbst wenn ein Problem mit der Windows-Partition vorhanden ist.

Bei der Bereitstellung von Windows durch Bilder anwenden, müssen Sie die Festplattenpartitionen manuell konfigurieren. Bei der Installation von WinRE auf einer Festplatte muss die Partition NTFS-Dateisystem formatiert.

Fügen Sie das geplante WinRE Tools Bild (winre.wim) von Partitionen Windows- und Daten in einer separaten Partition. Dies ermöglicht es Benutzern WinRE verwenden, auch wenn die Windows-Partition mit Windows BitLocker Drive Encryption verschlüsselt sind. Es wird verhindert, dass Ihre Benutzer versehentlich ändern oder Entfernen der WinRE-Tools.

Es wird empfohlen, die Wiederherstellungstools in einer dedizierten Partition, direkt nach der Windows-Partition zu speichern.

Finden Sie weitere Informationen zum Konfigurieren von Partitionen [Configure UEFI/GPT-Based Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md) oder [Configure BIOS/MBR-Based Festplattenpartitionen](configure-biosmbr-based-hard-drive-partitions.md)aus.

## <a name="span-idmemoryrequirementsspanspan-idmemoryrequirementsspanspan-idmemoryrequirementsspanmemory-requirements"></a><span id="Memory_requirements"></span><span id="memory_requirements"></span><span id="MEMORY_REQUIREMENTS"></span>Speicherbedarf


Um Windows RE direkt aus dem Speicher (auch bekannt als RAM Datenträger Boot) starten, muss ein zusammenhängender Teil des physischen Arbeitsspeicher (RAM) kann das gesamte Windows RE-Abbild (winre.wim) enthalten verfügbar sein. Zum Optimieren der Speicherverwendung sollten Hersteller sicherstellen, dass ihre Firmware Speicherorte am Anfang oder am Ende des physischen Arbeitsspeichers-Adressraums reserviert.

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>Siehe auch


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Inhaltstyp</th>
<th align="left">Verweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Bereitstellung</strong></p></td>
<td align="left"><p>[Anpassen von Windows RE](customize-windows-re.md) | [Bereitstellen von Windows RE](deploy-windows-re.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[REAgentC Befehlszeilenoptionen](reagentc-command-line-options.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Problembehandlung</strong></p></td>
<td align="left"><p>[Windows RE-Problembehandlung von Features](windows-re-troubleshooting-features.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Add-On-tools</strong></p></td>
<td align="left"><p>[Fügen Sie ein benutzerdefiniertes Tool an den Windows RE-Optionen Startmenü](add-a-custom-tool-to-the-windows-re-boot-options-menu.md) | [Hinzufügen eine Recovery-Taste zum Starten des Windows RE](add-a-hardware-recovery-button-to-start-windows-re.md) | [Drucktaste zurücksetzen (Übersicht)](push-button-reset-overview.md)</p></td>
</tr>
</tbody>
</table>

 
