---
author: Justinha
Description: "Drucktaste zurücksetzen"
ms.assetid: f3d01e46-2288-42b3-a662-1f9346aeb50f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Drucktaste zurücksetzen"
ms.openlocfilehash: 6f33522ea8b0d6010c8df9f2be8923d67d0cf600
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="push-button-reset"></a>Drucktaste zurücksetzen

In diesem Thema wird für Original Equipment Manufacturers (OEMs) vorgesehen, die ihre Windows 10 Desktopcomputer Fertigungsprozesse Drucktaste zurücksetzen Features hinzufügen möchten. Wenn Sie ein Benutzer sind, möchte einen Computer zurücksetzen, der 10 Windows ausgeführt wird, finden Sie unter [Wiederherstellungsoptionen in Windows 10](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options).

Drucktaste Reset ist eine Recovery-Tool, mit dem das Betriebssystem repariert Beibehaltung von Daten und wichtige Anpassungen. Es verringert bietet Benutzern so weitere Optionen und die Möglichkeit zum Reparieren von ihren eigenen PCs teilnehmen mit Confidence die Notwendigkeit für benutzerdefinierte Wiederherstellung Applications.

Drucktaste zurücksetzen ist im Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) enthalten und in Windows 8 eingeführt.

## <a name="whats-new-for-windows-10"></a>What's new for Windows 10

In Windows-Version-1607 10 wurde Drucktaste zurücksetzen aktualisiert, um die folgenden Änderungen enthalten:

-   **Verbesserte Zuverlässigkeit:** Wenn Sie Drucktaste zurücksetzen Features aus der Einstellungsapp starten, durchsucht Windows die Systemdateien im Speicher Komponente Windows ermittelten. Wenn es beschädigte Dateien findet und Ersetzungen über Windows Update herunterladen kann, wird es automatisch das Problem behoben. Obwohl dies die gesamte Wiederherstellungszeit erhöht wird, wird es die Zuverlässigkeit des PCs verbessert.
-   **Wiederherstellen von fehlgeschlagenen zurückgesetzt:** Setzen Sie in Windows 10, Version 1507 und Windows 10, Version 1511, Fehlern, die beim Auftreten dieser PC fast immer gerendert der PC nicht startbaren/nicht wiederhergestellt zurück. Dieses Feature wurde neu gestaltet, in das Update Jahrestag beschränkt Rollback zu unterstützen, wenn ein Problem auftritt, während der Computer im Windows RE befindet.
-   **Wiederherstellungsoptionen beim Start von Wiederherstellungsmedien:** Wenn der PC von Wiederherstellungsmedien gestartet wird, werden die Aktualisierung dieser PC und Zurücksetzen dieser PC-Features nicht mehr unterstützt. Das nur Drucktaste Reset-Feature ist verfügbar, wenn über Media gestartet ist bare-Metal-Recovery (d. h. von einem Laufwerk wiederherstellen).

Frühere Versionen von Windows 10 bereitgestellt, die folgenden Verbesserungen an Drucktaste zurücksetzen:

-   **Bild weniger Wiederherstellung**: Drucktaste Zurücksetzen nicht mehr benötigen oder Image-separate Wiederherstellung auf einer lokalen Partition oder auf Medien unterstützt. Dadurch erheblich möglichst wenig Speicherplatz erforderlich, damit die Features unterstützt, und Wiederherstellung möglich sogar auf Geräten mit begrenzter Speicherkapazität.
-   **In den aktualisierten Zustand wiederhergestellt**: Drucktaste zurücksetzen Features Wiederherstellen jetzt das Betriebssystem (OS) und Treiber (einschließlich Gerät Applets, die im Rahmen der INF-basierte Treiberpakete installiert sind) in den aktualisierten Zustand. Dadurch wird die Zeitdauer, die Benutzer verbringen Neuinstallieren der OS Updates und Treiber nach dem Ausführen einer Wiederherstellung müssen.

Die Benutzeroberfläche Drucktaste Zurücksetzen weiterhin Anpassung Verkaufschancen anbieten. Hersteller können benutzerdefinierte Skripts einfügen, installieren Anwendungen oder zusätzliche Daten zur Verfügung stehenden Erweiterungspunkte beibehalten.

Die folgenden Drucktaste Reset-Features sind für Benutzer mit Windows-10-PCs und Geräte verfügbar:

-   **Aktualisieren Sie Ihren PC** Behebt Softwareproblemen durch die Neuinstallation des Betriebssystems Beibehaltung der Benutzerdaten, Benutzerkonten und wichtige Einstellungen. Alle anderen vorinstallierten Anpassungen werden Factory Zustand wiederhergestellt. In Windows 10 behält dieses Feature nicht mehr Windows-apps Benutzer erworben haben.
-   **Zurücksetzen von Ihrem PC** Bereitet den PC für das recycling oder für die Übertragung von Gesamtbetriebskosten durch Neuinstallation des Betriebssystems, alle Benutzerkonten und Inhalt (z. B. Daten, Windows-desktopanwendungen und apps für universelle Windows) entfernen und Wiederherstellen von vorinstallierten Anpassungen für deren Status Factory vor.
-   **Bare-Metal-recovery** Die standardmäßigen oder vorkonfigurierte Partitionslayout auf dem Systemdatenträger wiederhergestellt und erneut installiert, das Betriebssystem und die vorinstallierten Anpassungen vom externen Medium.

![Screenshot zeigt Optionen: Meine Dateien beibehalten werden sollen, oder Alles entfernen](images/dep-winre-pbr.png)

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
<td align="left"><p><strong>Übersicht</strong></p></td>
<td align="left"><p>[Wie Drucktaste zurücksetzen Arbeit features](how-push-button-reset-features-work.md) | [Wiederherstellungsstrategie für allgemeine Anpassungen](recovery-strategy-for-common-customizations.md) | [Siloed Bereitstellen von Lösungspaketen](siloed-provisioning-packages.md) </p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Festplatte setup</strong></p></td>
<td align="left"><p>[Festplatten und Partitionen](hard-drives-and-partitions.md) | [UEFI, GPT-basierten Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md) | [BIOS/MBR-basierten Festplattenpartitionen](configure-biosmbr-based-hard-drive-partitions.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[Drucktaste zurücksetzen Features mit ScanState bereitstellen](deploy-push-button-reset-features.md) | [Bare-Metal Reset-Recovery: Aktivieren Sie Ihre Benutzer zu Wiederherstellungsmedien erstellen](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md) | [Bare-Metal Reset-Recovery: beim Bereitstellen neuer Geräte zu Wiederherstellungsmedien erstellen](create-media-to-run-push-button-reset-features-s14.md) | [Hinzufügen ein Skript zum Drucktaste zurücksetzen Features](add-a-script-to-push-button-reset-features.md) | [provisioning Paket mit Windows-desktopanwendungen erstellen](combine-provisioning-packages-into-a-new-image.md) </p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Konfigurationsdateien</strong></p></td>
<td align="left"><p>[ResetConfig XML (engl.)](resetconfig-xml-reference-s14.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Durch Zurücksetzen des Drucktaste verwendete Technologien</strong></p></td>
<td align="left"><p>[Windows-Wiederherstellungsumgebung](windows-recovery-environment--windows-re--technical-reference.md) | [Windows PE (Windows PE)](winpe-intro.md) | [ScanState](deploy-push-button-reset-features.md)</p></td>
</tr>
</tbody>
</table>

 

 

 





