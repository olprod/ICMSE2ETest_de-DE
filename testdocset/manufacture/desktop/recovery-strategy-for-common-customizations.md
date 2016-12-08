---
author: Justinha
Description: "Drucktaste zurücksetzen Features standardmäßig nur-Treiber (über INF-Pakete installiert) wiederherstellen und apps für Windows vorinstalliert."
ms.assetid: 909227f2-8969-4ab3-b296-c54977a38977
MSHAttr: PreferredLib:/library/windows/hardware
title: Recovery-Komponenten
ms.openlocfilehash: 454c842408cf7fb03a23ed1de32d44eb6e548172
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recovery-components"></a>Recovery-Komponenten


Drucktaste zurücksetzen Features standardmäßig nur-Treiber (über INF-Pakete installiert) wiederherstellen und apps für Windows vorinstalliert. Um die Funktionen zum Wiederherstellen weitere Anpassungen vor, wie beispielsweise Windows-desktopanwendungen und zu konfigurieren, müssen Sie ein oder mehrere Anpassung Pakete vorbereiten, die die Anpassungen enthalten. Diese Pakete Anpassungen werden in Form von Paketen (.ppkg) bereitstellen.

Drucktaste zurücksetzen Features gesucht und automatisch wiederhergestellt provisioning Pakete, die sich im Ordner C: befinden\\Wiederherstellung\\Anpassungen.

Um die-Pakete schützen Missbrauch oder versehentliches Löschen, die Write/Modify Berechtigungen von C:\\Wiederherstellung\\Anpassungen sollte auf die Gruppe der lokalen Administratoren Benutzer beschränkt werden.

Einige Einstellungen und Anpassungen können nicht bei der Bereitstellung Pakete enthalten sein. Stattdessen können Sie sie über eine Datei mithilfe der Drucktaste angewendet zurücksetzen Erweiterbarkeit Skripts wiederherstellen. Einstellungen, die mit den beiden provisioning-Paketen unterstützt werden und für die unbeaufsichtigte Installation, wird empfohlen, dass Sie diese mit nur einer der Mechanismen, nicht beides angeben. Weitere Informationen finden Sie Ihren geschäftlichen Sie [wie Drucktaste zurücksetzen Features](how-push-button-reset-features-work.md).

## <a name="span-idcapturingclassicwindowsapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspanspan-idcapturingwindowsdesktopapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspanspan-idcapturingwindowsdesktopapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspancapturing-windows-desktop-applications-using-windows-user-state-migration-tool-usmts-scanstate-tool"></a><span id="Capturing_Classic_Windows_applications_using_Windows_User_State_Migration_Tool__USMT__s_ScanState_tool"></span><span id="capturing_windows_desktop_applications_using_windows_user_state_migration_tool__usmt__s_scanstate_tool"></span><span id="CAPTURING_WINDOWS_DESKTOP_APPLICATIONS_USING_WINDOWS_USER_STATE_MIGRATION_TOOL__USMT__S_SCANSTATE_TOOL"></span>Erfassen von Windows-desktopanwendungen mit Windows User State Migration Tool (USMT) des ScanState tool


Die ScanState.exe Windows User State Migration Tool (USMT) wurde aktualisiert, in Windows 10, erfassen Windows desktopanwendungen-Clientanwendungen unterstützt. Diese Funktion aktiviert werden kann, durch Angeben der `/apps` Option.

Beim `/apps` ScanState verwendet eine Reihe von Anwendung Discovery Regeln, um zu bestimmen, was erfasst werden sollen, und speichert die Ausgabe als Referenz Gerät Datenabbild in einem Paket provisioning wird angegeben. Die Gerät Referenzdaten umfasst im Allgemeinen Folgendes:

-   Windows-desktopanwendungen, die mit Microsoft Windows Installer oder anderen Installer installiert
-   Alle Dateien und Ordner außerhalb des Windows-Namespaces (also außerhalb des \\Windows \\Programmdateien, \\Program Files (x86), \\Ordner "ProgramData", und \\Benutzer). Dies gilt nur für den Datenträger, auf dem Windows installiert ist.
-   Nicht aufgezeichnet: apps für Windows.
-   Nicht aufgezeichnet: Benutzer Zustandsdaten.

Sie können auch zusätzliche Regeln zum einbeziehen oder Ausschließen bestimmter Dateien, Ordner und registrierungseinstellungen angeben. Wenn Sie während der Bereitstellung von Factory ScanState verwenden, müssen Sie Fertigung-spezifischen Tools ausschließen, sodass sie nicht wiederhergestellt werden, wenn Endbenutzer Drucktaste Reset-Features verwenden. Um zusätzliche Regeln angeben, müssen Sie Erstellen einer XML-Migrations und Angeben der `/i` option, wenn ScanState.exe verwenden.

ScanState des /apps Option unterstützt außerdem die folgenden optionalen Parameter:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Verwendung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><code>+/-sysdrive</code></td>
<td align="left">Gibt an, ob Applications, Dateien und Ordner außerhalb des Windows-Namespaces erfasst werden soll.
<p>Wenn <code>+sysdrive</code> angegeben ist, werden alle Inhalte auf dem Systemlaufwerk werden überprüft und gemäß den Regeln Discovery erfasst werden können.</p>
<p>Wenn <code>-sysdrive</code> angegeben ist, nur Inhalt in den Windows-Namespace überprüft und berechtigt, gemäß den Regeln Discovery erfasst werden.</p>
<p><code>+sysdrive</code> ist die Standardeinstellung.</p></td>
</tr>
<tr class="even">
<td align="left"><code>+/-oeminfo</code></td>
<td align="left">Gibt an, ob der OEM-spezifische-Hilfe und-Support Info erfasst werden sollen.
<p>Wenn <code>+oeminfo</code> angegeben ist, Unterstützung und OEM-Info werden erfasst.</p>
<p>Wenn <code>-oeminfo</code> angegeben ist, Unterstützung und OEM-Info werden nicht erfasst.</p>
<p><code>+oeminfo</code> ist die Standardeinstellung.</p></td>
</tr>
</tbody>
</table>

 

**Wichtige**  
-   Obwohl Drucktaste zurücksetzen Features mehrere provisioning Pakete wiederhergestellt werden können, kann nur eine der Pakete Verweis Gerät Datenabbild mit ScanState erfasst enthalten.
-   ScanState sollte verwendet werden, nachdem alle Anpassungen auf dem PC angewendet wurden. Es wird nicht unterstützt, weitere Änderungen an einer vorhandenen Bildtyp Daten Verweis anfügen.
-   Eine Bereitstellung Paket mit ScanState.exe erfasst kann nur mit Drucktaste Reset-Funktionen und Bereitstellung von Medien mit Windows Imaging und Konfiguration Designer (ICD) erstellt angewendet werden. Es kann nicht mit Tools wie DISM oder des USMT LoadState.exe angewendet werden.
-   Wenn Sie für die Erfassung von Anpassungen ScanState vorbereiten, sollten Sie ausschließen Windows Defender Einstellungen, um mögliche Ausfälle während der Wiederherstellung zu vermeiden, die durch die Dateikonflikte verursacht werden können. Weitere Informationen finden Sie unter Schritt 1 in [Deploy Drucktaste zurücksetzen Features](deploy-push-button-reset-features.md).

 

## <a name="span-idcreatingcustomizationpackagesusingwindowsicdspanspan-idcreatingcustomizationpackagesusingwindowsicdspanspan-idcreatingcustomizationpackagesusingwindowsicdspancreating-customization-packages-using-windows-icd"></a><span id="Creating_customization_packages_using__Windows_ICD"></span><span id="creating_customization_packages_using__windows_icd"></span><span id="CREATING_CUSTOMIZATION_PACKAGES_USING__WINDOWS_ICD"></span>Erstellen von Windows ICD Anpassung Lösungspaketen


Für Anpassungen im Zusammenhang mit Einstellungen, die für alle Editionen von Windows 10 (einschließlich Windows 10 Mobile) gelten, können Sie die Bereitstellung Pakete, die mithilfe der Windows-ICD erstellen.

In Build-zu-Stock (BTS) Szenarien Wenn Sie Ihre Windows-desktopanwendungen aus Ihrem Referenz-PC, mit dem Befehlszeilentool ScanState bereits erfasst haben können Importieren der Ausgabe provisioning-Paket in Windows ICD und geben Sie zusätzliche Einstellungen, die während der Wiederherstellung wiederhergestellt werden soll.

## <a name="span-idrestoringsettingsusingunattendxmlandextensibilityscriptsspanspan-idrestoringsettingsusingunattendxmlandextensibilityscriptsspanrestoring-settings-using-unattendxml-and-extensibility-scripts"></a><span id="restoring_settings_using_unattend.xml_and_extensibility_scripts"></span><span id="RESTORING_SETTINGS_USING_UNATTEND.XML_AND_EXTENSIBILITY_SCRIPTS"></span>Wiederherstellen von Einstellungen mithilfe von Skripts unattend.xml und Erweiterbarkeit


Die meisten Einstellungen, die konfiguriert werden mithilfe von unattend.xml und andere Konfigurationsdateien (z. B. "Oobe.xml", LayoutModification.xml) können nicht mithilfe der Bereitstellung Pakete wiederhergestellt werden. Stattdessen müssen Sie die Drucktaste zurücksetzen Erweiterungspunkte verwenden, um sie während der Wiederherstellung wiederherzustellen. Diese Erweiterbarkeitspunkte ermöglichen, dass Sie Skripts ausführen können:

-   Fügen Sie eine unattend.xml in das wiederhergestellte Betriebssystem
-   Kopieren Sie andere Konfigurationsdateien und Anlagen in das wiederhergestellte Betriebssystem

**Wichtige**  
-   Sie sollten nicht unattend.xml (oder andere Mechanismen), um die wiederhergestellte OS starten im Überwachungsmodus verwenden. Das wiederhergestellte Betriebssystem muss zum Starten OOBE konfigurierten bleiben.
-   Eine Kopie der Konfigurationsdateien und Ressourcen, die wiederhergestellt werden müssen, muss unter C: platziert werden\\Wiederherstellung\\OEM. Inhalt dieses Ordners durch Drucktaste Reset-Features nicht geändert werden und werden automatisch zu Wiederherstellungsmedien erstellt, mit dem Dienstprogramm **erstellen ein Wiederherstellungslaufwerk** gesichert. Die Konfiguration und unattend.xml Dateien/Ressourcen aus schützen Missbrauch oder versehentliches Löschen, Berechtigungen von C: Write/Modify\\Wiederherstellung\\OEM sollte auf die Gruppe der lokalen Administratoren Benutzer beschränkt werden.

 

Informationen zum Erstellen von Skripts mit Erweiterungspunkte ausgeführt werden, finden Sie unter [ein Skript zum Drucktaste zurücksetzen Features hinzufügen](add-a-script-to-push-button-reset-features.md).

Erfahren Sie, wie mit ScanState erfassen und speichern die resultierenden PPKG unter C:\\Wiederherstellung\\Anpassungen, die automatisch während PBR wiederhergestellt wird, finden Sie unter [Deploy Drucktaste Zurücksetzen von ScanState Features](deploy-push-button-reset-features.md).

## <a name="span-idrecoverystrategiesforcommoncustomizationsspanspan-idrecoverystrategiesforcommoncustomizationsspanspan-idrecoverystrategiesforcommoncustomizationsspanrecovery-strategies-for-common-customizations"></a><span id="Recovery_strategies_for_common_customizations"></span><span id="recovery_strategies_for_common_customizations"></span><span id="RECOVERY_STRATEGIES_FOR_COMMON_CUSTOMIZATIONS"></span>Strategien für allgemeine Anpassungen


Die folgende Tabelle enthält die Wiederherstellungsstrategie für allgemeine Anpassungen, die in der User Experience Windows Engineering Guide (UX WEG) als auch in der OEM-Richtlinie-Dokument (OPD) behandelt beschrieben sind. Auf dem neuesten Stand Detailinformationen für diese Anpassungen finden Sie in der neuesten Version des UX WEG und OPD.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Anpassung</th>
<th align="left">Wie konfiguriert</th>
<th align="left">Wie sie während der PBR wiederhergestellt werden kann</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">OOBE – HID Kopplung mit.</td>
<td align="left">Einstellungen in der <code>&lt;hidSetup&gt;</code> Abschnitt OOBE.xml und Bildern (z. B. PNG-Dateien)</td>
<td align="left">Verwenden Sie PBR Erweiterbarkeit Skript OOBE.xml und Bilder aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">OOBE – OEM-EULA</td>
<td align="left"><code>&lt;Eulafilename&gt;</code> Einstellung in OOBE.xml und Lizenz Begriffe unter %WINDIR%\System32\Oobe\Info gespeichert RTF-Dateien</td>
<td align="left">Verwenden Sie PBR Erweiterbarkeit Skript OOBE.xml und RTF-Dateien aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">OOBE – Preconfigured Sprache und Zeitzone</td>
<td align="left">Einstellungen in der <code>&lt;defaults&gt;</code> im Abschnitt "Oobe.xml"</td>
<td align="left">Verwenden Sie PBR Erweiterbarkeit Skript OOBE.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">OOBE – mobile Breitband Seite ausblenden</td>
<td align="left">Microsoft-Windows-WwanUI | Einstellung in unattend.xml NotInOOBE</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">OOBE – OEM Registrierungsseite</td>
<td align="left">Einstellungen in der &lt;Registrierung&gt; Abschnitt der OOBE.xml und HTML-Dateien für Compliance-Links</td>
<td align="left">Verwenden Sie PBR Erweiterbarkeit Skript OOBE.xml und HTML-Dateien aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">Start – Pinned Kacheln und Gruppen</td>
<td align="left">LayoutModification.xml gespeichert unter %SYSTEMDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell oder Einstellungen unter Microsoft-Windows-Shell-Setup | StartTiles in unattend.xml</td>
<td align="left">Verwenden Sie PBR Erweiterbarkeit Skripts LayoutModification.xml oder unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">Start – Prepopulated am häufigsten Verwendeten Liste</td>
<td align="left">LayoutModification.xml unter %SYSTEMDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell gespeichert</td>
<td align="left">Mithilfe von PBR Erweiterbarkeit Skripts LayoutModification.xml aus C:\Recovery\OEM wiederhergestellt werden.</td>
</tr>
<tr class="even">
<td align="left">Kontinuierliche – Formfaktor</td>
<td align="left">Einstellungen in unattend.xml:
<p>• Microsoft-Windows-Deployment | DeviceForm</p>
<p>• Microsoft-Windows-GPIOButtons | ConvertibleSlateMode</p></td>
<td align="left">Mithilfe von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederhergestellt werden.</td>
</tr>
<tr class="odd">
<td align="left">Kontinuierliche – Standardmodus</td>
<td align="left">Microsoft-Windows-Shell-Setup | SignInMode Einstellung in unattend.xml</td>
<td align="left">Mithilfe von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederhergestellt werden.</td>
</tr>
<tr class="even">
<td align="left">Desktop – Standard und zusätzliche Akzentfarben</td>
<td align="left">Befehl RunSynchronous in unattend.xml die der AGRB hexadezimalen RGB-Werte in der Registrierung unter HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Accents hinzufügt</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">Desktop-Hintergrundbild</td>
<td align="left">Microsoft-Windows-Shell-Setup | Designs | DesktopBackground-Einstellung in unattend.xml und Abbild (z. B..jpg/.png/.bmp-Datei)</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml und Hintergrund Bilddatei aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">Desktop – Pinned Taskleistenelemente</td>
<td align="left">Einstellungen unter Microsoft-Windows-Shell-Setup | TaskbarLinks in unattend.xml und Verknüpfung (.lnk)-Dateien, die in einem Ordner unter %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml und .lnk-Dateien aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">Desktop – Taskleiste Symbole</td>
<td align="left">Einstellungen unter Microsoft-Windows-Shell-Setup | NotificationArea in unattend.xml</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">Mobiles Breitband – umbenennen "WiFi" auf "WLAN" im Netzwerkliste</td>
<td align="left">Microsoft-Windows-SystemSettings | WiFiToWlan Einstellung in unattend.xml</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">Mobile Breitband-Netzwerk Auswahlsteuerelement aktivieren in den Einstellungen</td>
<td align="left">Microsoft-Windows-SystemSettings | Einstellung in unattend.xml DisplayNetworkSelection</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">PC-Einstellungen – vorinstallierten Einstellungen apps</td>
<td align="left">Einstellungen für apps auf die gleiche Weise wie alle anderen app vorinstalliert sind und in den Einstellungen automatisch angezeigt. Funktion im app-Manifest deklariert bestimmt, ob es eine Einstellungsapp oder nicht ist.</td>
<td align="left">Automatisch wiederhergestellt, zusammen mit anderen vorinstallierten apps</td>
</tr>
<tr class="odd">
<td align="left">Standard-Browser und Handler von Protokollen</td>
<td align="left">Anwendung Zuordnung Einstellungen XML-Datei importiert, mit dem Befehl /Import-DefaultAppAssociations in DISM Standard</td>
<td align="left">Erneutes Importieren den XML-CODE aus C:\Recovery\OEM mithilfe von DISM mithilfe von PBR Erweiterbarkeit Skripts</td>
</tr>
<tr class="even">
<td align="left">Supportinformationen im Kontakt Support-app</td>
<td align="left">Einstellungen unter Microsoft-Windows-Shell-Setup | In der Datei unattend.xml und logo.bmp OEMInformation</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml und BMP-Datei von C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="odd">
<td align="left">Store Content Modifizierer</td>
<td align="left">Microsoft-Windows-Store-Client-Benutzeroberfläche | Einstellung in unattend.xml StoreContentModifier</td>
<td align="left">Verwenden von PBR Erweiterbarkeit Skripts unattend.xml aus C:\Recovery\OEM wiederherstellen</td>
</tr>
<tr class="even">
<td align="left">Windows-desktop-Clientanwendungen (einschließlich Treiber Applets über setup.exe installiert)</td>
<td align="left">MSI oder benutzerdefinierte Installer</td>
<td align="left">Verwenden Sie ScanState zum Erfassen und speichern die resultierende PPKG unter C:\Recovery\Customizations, die während der PBR automatisch wiederhergestellt wird.</td>
</tr>
<tr class="odd">
<td align="left">RDX Inhalt</td>
<td align="left">Einzelheiten finden Sie unter UX WEG</td>
<td align="left">Soll während PBR nicht wiederhergestellt werden</td>
</tr>
</tbody>
</table>

 

 

 





