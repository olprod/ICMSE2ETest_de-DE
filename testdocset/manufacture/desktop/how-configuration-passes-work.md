---
author: Justinha
Description: Funktionsweise von Konfigurationsphasen
ms.assetid: 11b434f9-b8a1-4159-ba8b-cf79ae47a995
MSHAttr: PreferredLib:/library/windows/hardware
title: Funktionsweise von Konfigurationsphasen
ms.openlocfilehash: a8d53174bbc338107a80b79006872101295e733e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="how-configuration-passes-work"></a>Funktionsweise von Konfigurationsphasen


Konfigurationsphasen sind die Phasen einer Windows®-Installation, in dem Sie ein Bild anpassen können. Einstellungen für die unbeaufsichtigte Installation von Windows können in eine oder mehrere Konfigurationsphasen, abhängig von der Einstellung angewendet werden, den, die Sie verwenden. Verstehen, wie und wann Konfigurationsphasen ausgeführt ist sehr wichtig, bei der Entwicklung von einer Windows-Bereitstellungsstrategie.

In diesem Thema:

-   [Grundlegendes zu Konfigurationsphasen](#understand)

-   [Konfigurieren von Gerätetreibern](#configdevice)

-   [Konfigurieren von internationalen Einstellungen](#configintsettings)

-   [Beispiele für](#examples)

## <a name="span-idunderstandspanspan-idunderstandspanunderstanding-configuration-passes"></a><span id="understand"></span><span id="UNDERSTAND"></span>Grundlegendes zu Konfigurationsphasen


In der folgenden Abbildung gezeigt, dass die Beziehung zwischen den relativ zu der verschiedenen Bereitstellungstools übergibt.

![Konfigurationsphasen (Übersicht)](images/dep-win8-l-configpassesandexes.jpg)

Nicht alle Konfigurationsphasen führen Sie in einer bestimmten Installation von Windows. Einige Konfigurationsphasen, wie **AuditSystem** und **AuditUser**, nur ausgeführt, wenn Sie den Computer im Überwachungsmodus zu starten. Die meisten unbeaufsichtigte Installation Windows Einstellungen der **specialize** oder **der Konfigurationsphase** hinzugefügt werden können. Die anderen Konfigurationsphasen können auch in bestimmten Situationen nützlich sein. In der folgenden Tabelle werden die Konfigurationsphasen beschrieben.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Konfigurationsphasen</th>
<th align="left">Beschreibung</th>
<th align="left">Übergeben Sie Konfiguration wird ausgeführt, wenn</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>windowsPE</strong></p></td>
<td align="left"><p>Zahlreiche Aspekte der Installation können während der Konfiguration <strong>WindowsPE</strong> -Durchgang automatisiert werden. In dieser Phase können Sie Folgendes konfigurieren:</p>
<ul>
<li><p>Windows PE-Optionen</p>
<p>Diese Optionen können die Angabe des Speicherorts der Protokolldatei Windows PE, wodurch Netzwerk- oder einer Windows PE-Auslagerungsdatei umfassen.</p></li>
<li><p>Windows-Setup-Optionen</p>
<p>Angeben des Windows-Abbilds installieren und Konfigurieren eines Datenträgers auf dem Zielcomputer, können zu diesen Optionen gehören.</p></li>
</ul>
<p>Während dieser Konfigurationsphase werden die Fenster Bild auf den Zielcomputer kopiert werden, nachdem die Einstellungen in der Konfiguration <strong>WindowsPE</strong> übergeben verarbeitet.</p>
<p>Wenn Ihre Installation von Windows PE erforderliche Treiber Zugriff auf das lokale Festplattenlaufwerk oder ein Netzwerk erforderlich sind, verwenden Sie übergeben Sie diese Konfiguration, Treiber zu Windows PE Driver Store hinzufügen und die erforderlichen Treiber erforderliche entsprechend</p></td>
<td align="left"><p>Einer der folgenden Aktionen:</p>
<ul>
<li><p>Starten die Windows-setupmedien</p></li>
<li><p>Starten von Windows Setup von einer vorherigen Windows-installation</p></li>
</ul>
<p>Die Windows PE-Optionen sind nur angewendet, wenn Sie Windows Setup von einer Windows PE-Umgebung ausgeführt werden. Die Windows-Setup-Optionen werden angewendet, wenn sie Windows PE oder eine frühere Windows-Installation ausgeführt wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>offlineServicing</strong></p></td>
<td align="left"><p>Übergeben Sie diese Konfiguration wird verwendet, um Updates, Treiber oder Sprachpakete auf einem Windows-Abbild anwenden.</p>
<p>Während der Installation von Windows das Windows-Abbild auf einer Festplatte angewendet wird und alle Einstellungen im Abschnitt <strong>OfflineServicing</strong> einer Antwortdatei klicken Sie dann auf das Bild vor dem Neustart des Computers angewendet werden.</p>
<p>Während dieser Konfigurationsphase können Sie ein Windows-Abbild Treiber hinzufügen, bevor das Abbild gestartet wird. So können Sie zum Installieren und Verarbeiten von Out-of-Box-Gerätetreibern während der Installation von Windows.</p>
<p>Übergeben Sie diese Konfiguration wird auch zum Anwenden von Updates auf einem Windows-Abbild während der Wartung Szenarien verwendet.</p></td>
<td align="left"><ul>
<li><p>Automatisch nach der <strong>WindowsPE</strong> Konfigurationsdurchlauf und vor dem Neustart des Computers.</p></li>
<li><p>Während der Wartung Szenarien, wenn Sie eine Antwortdatei angeben, mit der Bereitstellung Bild – Wartung und Verwaltung-tool (Dism.exe).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>specialize</strong></p></td>
<td align="left"><p>Übergeben Sie diese Konfiguration wird verwendet, um das Erstellen und Konfigurieren von Informationen im Windows-Abbild und sind spezifisch für die Hardware, der das Windows-Abbild installiert wird.</p>
<p>Nach das Windows-Abbild zum ersten Mal startet, wird die Konfiguration <strong>specialize</strong> Pass ausgeführt. Während dieser Phase werden eindeutige Sicherheits-IDs (SIDs) erstellt. Darüber hinaus können Sie viele Windows-Features, einschließlich Netzwerkeinstellungen, internationalen Einstellungen und Domäneninformationen konfigurieren.</p>
<p>Die Antwort dateieinstellungen für den <strong>specialize</strong> Lauf im Überwachungsmodus angezeigt werden. Beim Starten eines Computers mit um zu überwachenden Modus, der <strong>AuditSystem</strong> Durchlauf ausgeführt wird und der Computer verarbeitet die AuditUser-Einstellungen.</p></td>
<td align="left"><ul>
<li><p>Automatisch bei das Windows-Abbild zum ersten Mal startet.</p></li>
<li><p>Führen Sie auf der nächsten Starten, nachdem Sie den Befehl <strong>Sysprep</strong> mit der Option <strong>/ verallgemeinern</strong> .</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Verallgemeinern</strong></p></td>
<td align="left"><p>Während dieser Konfigurationsphase wird computerspezifische Informationen aus der Windows-Installation aktivieren Sie erfassen und Anwenden von Windows-Abbild auf anderen Computern entfernt. Beispielsweise werden während dieser Phase die eindeutige Sicherheits-ID (SID), eindeutigen Gerätetreiber und andere Hardware-spezifischen Einstellungen aus dem Bild entfernt.</p>
<p>Übergeben Sie diese Konfiguration können Sie minimal konfigurieren die <strong>Sysprep / verallgemeinern</strong> Command, zusätzlich zu anderen Windows-Einstellungen, die beibehalten werden, müssen auf dem master Bild konfigurieren.</p>
<p>Nachdem die <strong>verallgemeinern</strong> übergeben, das nächste Mal abgeschlossen wurde, die Windows-Abbilds wird die Konfiguration <strong>specialize</strong> Durchlauf ausgeführt. Wenn die eindeutigen Gerätetreiber beibehalten, die an der Windows-Installation installiert werden soll, können Sie die Microsoft Windows-PnpSysprep | <code>PersistAllDeviceInstalls</code> Einstellung. Wenn diese Einstellung konfiguriert ist, werden die eindeutigen Gerätetreiber nicht aus der Installation entfernt.</p></td>
<td align="left"><ul>
<li><p>Die folgende Einstellung konfiguriert ist: Microsoft-Windows-Deployment | <code>Generalize</code>.</p></li>
</ul>
<p>-oder -</p>
<ul>
<li><p>Führen Sie die <strong>Sysprep / verallgemeinern</strong> Befehl.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>auditSystem</strong></p></td>
<td align="left"><p>Während dieser Konfigurationsphase werden Einstellungen verarbeitet, wenn Windows im System-Kontext, bevor ein Benutzer meldet sich der Computer im Aaudit Modus ausgeführt wird.</p>
<p>Diese Phase ist in der Regel zum Installieren von Gerätetreibern Out-of-Box-Installation weitere Konfigurationen vornehmen verwendet.</p>
<p>In dieser Phase ausgeführt wird, nur, wenn ein Computer konfiguriert ist, starten im Überwachungsmodus.</p></td>
<td align="left"><ul>
<li><p>Die folgende Einstellung der unbeaufsichtigten Installation konfiguriert wird: Microsoft-Windows-Deployment | Reseal | <code> Mode</code>=<strong>Audit</strong>.</p></li>
</ul>
<p>-oder -</p>
<ul>
<li><p>Führen Sie den Befehl <strong>Sysprep</strong> mit der <strong>Option/audit</strong> .</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><strong>auditUser</strong></p></td>
<td align="left"><p>In dieser Phase verarbeitet Einstellungen für die unbeaufsichtigte Installation, nachdem der Computer im Überwachungsmodus ein Benutzer anmeldet.</p>
<p>Diese Phase wird in der Regel verwendet, um benutzerdefinierte Befehle auszuführen oder Konfigurieren von Optionen für die Windows-Shell.</p>
<p>In dieser Phase ausgeführt wird, nur, wenn ein Computer konfiguriert ist, starten im Überwachungsmodus.</p></td>
<td align="left"><ul>
<li><p>Die folgenden unbeaufsichtigte Installation konfiguriert ist: Microsoft Windows-Deployment | Reseal | <code> Mode</code>=<strong>Audit</strong>.</p></li>
</ul>
<p>-oder -</p>
<ul>
<li><p>Führen Sie den Befehl <strong>Sysprep</strong> mit der <strong>Option/audit</strong> .</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Während dieser Phase Configuration Settings Windows gelten für vor dem Start der Windows-Willkommensseite.</p>
<p>Diese Phase ist in der Regel zum Konfigurieren von Optionen für Windows-Shell-Benutzerkonten erstellen und Angeben von Sprachen und Gebietsschemas Einstellungen verwendet.</p>
<p>Die Antwort dateieinstellungen für den <strong>OobeSystem</strong> Lauf in der Windows-Willkommensseite, auch bekannt als OOBE angezeigt werden. Diese Einstellungen werden nicht im Überwachungsmodus aktiviert angezeigt.</p></td>
<td align="left"><ul>
<li><p>Die folgende Einstellung konfiguriert ist: Microsoft-Windows-Deployment | <code>Reseal</code> | <code>Mode</code>=<strong>OOBE</strong></p></li>
</ul>
<p>-oder -</p>
<ul>
<li><p>Führen Sie den Befehl <strong>Sysprep</strong> mit der <strong>Option/Oobe</strong> .</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

Weitere Informationen zu Windows-Komponenten und Einstellungen, die eine Antwortdatei hinzugefügt werden können, finden Sie unter unbeaufsichtigte Windows Setup (engl.). Weitere Informationen zur Protokollierung finden Sie unter [Problembehandlung bei Bereitstellung und Protokolldateien](deployment-troubleshooting-and-log-files.md) und [Windows-Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md).

## <a name="span-idconfigdevicespanspan-idconfigdevicespanspan-idconfigdevicespanconfiguring-device-drivers"></a><span id="configDevice"></span><span id="configdevice"></span><span id="CONFIGDEVICE"></span>Konfigurieren von Gerätetreibern


Um Out-of-Box, wichtige Faktoren bei einer unbeaufsichtigten Installation hinzuzufügen, müssen Sie sicherstellen, dass der Treiber erforderliche Vorinstallation Media verfügbar ist. Treiber erforderliche sollte der in der **WindowsPE** Konfigurationsphase hinzugefügt werden. Alle Treiber im Driver Store bereitgestellt werden, jedoch nur erforderliche Treiber widergespiegelt oder im Offlinemodus Windows-Abbild zusätzlich zu den Windows PE-Abbild installiert werden. Übergeben Sie den **OfflineServicing** Konfiguration können nicht Boot-erforderliche Treiber hinzugefügt werden. Dadurch wird sichergestellt, dass Treiber erforderliche verfügbar sind und beim Start des Computers des Treibers laden.

Weitere Informationen finden Sie unter [Gerätetreiber und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md).

## <a name="span-idconfigintsettingsspanspan-idconfigintsettingsspanspan-idconfigintsettingsspanconfiguring-international-settings"></a><span id="configIntSettings"></span><span id="configintsettings"></span><span id="CONFIGINTSETTINGS"></span>Konfigurieren von internationalen Einstellungen


Internationale Einstellungen sind verfügbar in mehreren Konfigurationsphasen, aktivieren Sie das Windows-Abbild basierend auf Kunden Anforderungen und verschiedene Bereitstellungsszenarien anpassen.

Wenn Sie einen Computer in den Vereinigten Staaten erstellen (Dies wäre eine internationale Einstellung En-US), sollten Sie alle Tests in Englisch durchführen. Jedoch wenn Sie beabsichtigen, liefern Sie den Computer nach Frankreich und Windows für das Starten in Französisch benötigen, können Sie das Sprachpaket fr-FR hinzufügen, wenn das Language Pack noch nicht installiert ist, und konfigurieren Sie die Microsoft-Windows-International-Core-Komponente, um während der Konfiguration **specialize** Durchlauf fr-FR Einstellungen anwenden. Wenn der Computer startet, wird die Installation englische Text angezeigt. Nachdem die Konfiguration Specialize übergeben wurde, wird jedoch französischen Text angezeigt.

DISM können Sie die Sprache des Windows-Abbild (online oder offline) konfigurieren. Weitere Informationen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

Standardmäßig zeigt Windows-Willkommensseite Seite eine Regionaleinstellungen der Benutzeroberfläche (UI) für den Endbenutzer Standardsprache, Gebietsschema und Tastenbelegungen aus. Vorkonfigurieren, die Einstellungen auf dieser Seite Benutzeroberfläche durch Angeben von Sprache und Gebietsschema in der Konfiguration **OobeSystem** übergeben, in der Microsoft-Windows-International-Core-Komponente. Wenn die Einstellungen in **OobeSystem** Konfiguration festgelegt sind übergeben Sie, den Regionaleinstellungen Seite übersprungen wird. Wenn spracheinstellungen während Specialize konfiguriert sind, wird die Regionaleinstellungen-Seite angezeigt werden.

Weitere Informationen finden Sie unter [Hinzufügen von Language Packs auf Windows](add-language-packs-to-windows.md).

## <a name="span-idexamplesspanspan-idexamplesspanspan-idexamplesspanexamples"></a><span id="Examples"></span><span id="examples"></span><span id="EXAMPLES"></span>Beispiele für


In den folgenden Abschnitten werden Beispiele für Bereitstellungsszenarien beschrieben und wird beschrieben, wann Konfigurationsphasen ausgeführt.

### <a name="span-idtorunwindowssetupspanspan-idtorunwindowssetupspanspan-idtorunwindowssetupspanto-run-windows-setup"></a><span id="To_run_Windows_Setup"></span><span id="to_run_windows_setup"></span><span id="TO_RUN_WINDOWS_SETUP"></span>Zum Ausführen von Setup für Windows

In diesem Szenario wird Windows zu einem neuen Computer installiert. Beginnen Sie mit dem Windows-Produktmedium und einer Antwortdatei.

1.  Führen Sie Setup aus, und geben Sie eine Antwortdatei. Windows-Setup wird gestartet.

2.  Übergeben Sie die **WindowsPE** -Konfiguration ausgeführt wird. Einstellungen in der `<settings pass="windowsPE">` Abschnitt einer Antwortdatei verarbeitet werden. Es gibt zwei verschiedene Arten von Einstellungen, die Sie während der Konfiguration **WindowsPE** -Durchgang konfigurieren können: Einstellungen, die die Windows PE-Umgebung, wie beispielsweise die Anzeige Auflösung und Protokolldateien Dateispeicherorte für Windows PE liegen. Sie können auch Einstellungen angeben, die für die Windows-Installation wie Datenträgerpartitionen konfigurieren oder dynamische Updates aktivieren gelten.

    -   Die Windows PE-spezifische Einstellungen in einer Antwortdatei werden nur angewendet, wenn Sie Windows Setup von einer Windows PE-Umgebung ausgeführt werden.

    -   Die Windows-Setup, die Optionen in der Konfiguration **WindowsPE** übergeben werden angewendet, bei der Ausführung von Windows PE oder eine frühere Windows-Installation.

3.  Nachdem das Windows-Abbild auf der Festplatte kopiert wurde, führt der **OfflineServicing** Konfiguration übergeben. Alle Einstellungen in der `<servicing>` und `<settings pass="offlineServicing">` Abschnitt einer Antwortdatei auf dem Windows-Abbild angewendet werden. In der Regel die Aktionen in dieser Konfigurationsphase installieren oder Entfernen von Paketen, Sprachpakete oder Gerätetreiber.

4.  Neustart des Systems wird und Windows Setup wird ausgeführt, die Konfiguration **specialize** übergeben. Zu diesem Zeitpunkt Einstellungen in der `<settings pass="specialize">` Abschnitt der Antwortdatei verarbeitet werden.

5.  Nach Abschluss der Installation von Windows startet den Computer neu. Übergeben Sie dann die **OobeSystem** -Konfiguration ausgeführt wird und die Einstellungen in der `<settings pass="oobeSystem>` Abschnitt einer Antwortdatei verarbeitet werden.

    **Hinweis**  
    Sie können eine separate Inhaltsdatei aufgerufen, die können Sie die Windows-Willkommensseite, erste Schritte, anpassen und ISP-Anmeldung Oobe.xml erstellen. Mithilfe von "Oobe.xml" eignet sich für diese Anpassungen organisieren, da es können Sie eine einzelne Datei zu verwalten, die alle branding, Lizenzbedingungen und Anmeldung Verkaufschancen für mehrere Länder/Regionen, Bereiche und/oder Sprachen aufgelistet sind. Weitere Informationen finden Sie unter [Konfigurieren von "Oobe.xml"](configure-oobexml.md). Im Allgemeinen wird Oobe.xml von OEMs und System-Builder verwendet. Einige Aspekte des Oobe.xml können jedoch auch Bereitstellungsszenarien in Unternehmen profitieren.

     

6.  Windows-Willkommensseite wird gestartet, und Sie können mit dem Computer.

### <a name="span-idtorunthesysprepgeneralizeshutdowncommandspanspan-idtorunthesysprepgeneralizeshutdowncommandspanspan-idtorunthesysprepgeneralizeshutdowncommandspanto-run-the-sysprep-generalize-shutdown-command"></a><span id="To_run_the_Sysprep__generalize__shutdown_command"></span><span id="to_run_the_sysprep__generalize__shutdown_command"></span><span id="TO_RUN_THE_SYSPREP__GENERALIZE__SHUTDOWN_COMMAND"></span>Führen Sie den Sysprep / verallgemeinern Shutdown-Befehl

In diesem Szenario erstellen Sie einen Verweis Windows Bild zur Darstellung der in der Umgebung verwenden. Beginnen Sie mit einer benutzerdefinierten Windows-Installation.

1.  Führen Sie den Befehl **Sysprep** mit **/ shutdown/oobe verallgemeinern** konfigurieren Optionen zum Erstellen eines master-Abbilds des Computers starten Sie Windows-Willkommensseite, und klicken Sie dann auf den Computer herunterzufahren.

2.  Die Einstellungen in der `<settings pass="generalize">` Abschnitt einer Antwortdatei angewendet werden.

    -   Wenn Sie nicht mit dem Befehl **Sysprep** eine Antwortdatei angegeben haben, wird die auf dem Computer zwischengespeicherte Antwortdatei verwendet werden. Weitere Informationen zur Verwendung von Antwortdateien finden Sie unter [Übersicht über die Automatisierung von Windows Setup](windows-setup-automation-overview.md).

    -   Wenn Sie eine Antwortdatei mit dem Befehl **Sysprep** angegeben, wird die Antwortdatei zwischengespeichert, um die der %windir%\\Panther Verzeichnis der Windows-Installation und für nachfolgende Konfigurationsphasen verwendet werden.

3.  Herunterfahren des Computers, sodass Sie starten Sie Windows PE oder ein anderes Betriebssystem und erfassen Sie das Abbild. Zeit der Windows-Abbilds ausgeführt, übergeben Sie die Konfiguration **specialize** ausgeführt wird und nächsten Windows startet den Computer mit der Windows-Willkommensseite.

### <a name="span-idusingascripttodeployawindowsimagespanspan-idusingascripttodeployawindowsimagespanspan-idusingascripttodeployawindowsimagespanusing-a-script-to-deploy-a-windows-image"></a><span id="Using_a_Script_to_Deploy_a_Windows_Image"></span><span id="using_a_script_to_deploy_a_windows_image"></span><span id="USING_A_SCRIPT_TO_DEPLOY_A_WINDOWS_IMAGE"></span>Verwenden eines Skripts zum Bereitstellen eines Windows-Abbilds

In diesem Szenario, starten Sie den Computer mit einem master-Bild, auf dem die **Sysprep / shutdown/oobe verallgemeinern** Befehl ausgeführt wurde, und das Abbild aufgezeichnet wurde. Sie beginnen mit einem Master-Shape, Bild, Windows PE und das Tool DISM.

1.  Anwenden des master-Abbilds auf einem Computer mit dem **Dism** -Befehl mit der Option **/apply-image** .

2.  Starten Sie den Computer mit der master-Abbild. Windows wird gestartet.

3.  Übergeben Sie die Konfiguration **specialize** ausgeführt wird. Einstellungen in der `<settings pass="specialize">` Abschnitt der Antwortdatei verarbeitet werden.

4.  Neustart des Computers.

5.  **Die Konfigurationsphase** ausgeführt wird. Einstellungen in der `<settings pass="oobeSystem">` Abschnitt der Antwortdatei verarbeitet werden.

6.  Windows-Willkommensseite wird gestartet, und Sie können mit Ihrem Computer.

### <a name="span-idtobootwindowstoauditmodespanspan-idtobootwindowstoauditmodespanspan-idtobootwindowstoauditmodespanto-boot-windows-to-audit-mode"></a><span id="To_boot_Windows_to_audit_mode"></span><span id="to_boot_windows_to_audit_mode"></span><span id="TO_BOOT_WINDOWS_TO_AUDIT_MODE"></span>So starten Sie Windows im Überwachungsmodus

In diesem Szenario starten Sie eine Windows-Bild, das im Überwachungsmodus start konfiguriert ist. Überwachungsmodus eignet sich für das Hinzufügen von benutzerdefinierten Anwendungen, Treiber und andere Updates zu einem master-Abbild. Sie können ein Windows-Abbild zum Starten des Computers im Überwachungsmodus durch Konfigurieren der folgenden Einstellung in einer Antwortdatei konfigurieren: Microsoft Windows-Deployment | Reseal | `Mode` = **Überwachen** oder Ausführen der **Sysprep** -Befehl mit der **Option/Überwachen** .

1.  Konfigurieren Sie das Windows-Abbild zum Starten des Computers im Überwachungsmodus. Führen Sie in diesem Szenario den Befehl **Sysprep** mit den **Optionen/audit/reboot** .

2.  Windows startet den Computer neu.

3.  Übergeben Sie den **AuditSystem** Konfiguration ausgeführt wird. Einstellungen in der `<settings pass="auditSystem">` Abschnitt der Antwortdatei verarbeitet werden.

4.  Das integrierte Administratorkonto ist aktiviert.

5.  Übergeben Sie den **AuditUser** Konfiguration ausgeführt wird. Einstellungen in der `<settings pass="auditUser">` Abschnitt der Antwortdatei verarbeitet werden.

6.  Der Desktop angezeigt wird.

Das nächste Mal an, dass Sie den Computer neu starten, wird es im erneut Überwachungsmodus starten.

Zum Konfigurieren des Computers, Windows-Willkommensseite zu starten müssen Sie verwenden Sie den Befehl **Sysprep** mit der **Option/Oobe** oder konfigurieren Sie die Microsoft-Windows-Deployment | Reseal | `Mode` **Oobe** in einer Antwortdatei festlegen.

### <a name="span-idtorundismagainstanofflinewindowsimagespanspan-idtorundismagainstanofflinewindowsimagespanspan-idtorundismagainstanofflinewindowsimagespanto-run-dism-against-an-offline-windows-image"></a><span id="To_run_DISM_against_an_offline_Windows_image"></span><span id="to_run_dism_against_an_offline_windows_image"></span><span id="TO_RUN_DISM_AGAINST_AN_OFFLINE_WINDOWS_IMAGE"></span>Zum Ausführen von DISM in ein offline-Windows-Abbild

In diesem Szenario führen Sie DISM für Schwelle Windows offline.

1.  Schwelle Windows offline führen Sie DISM-Tool aus, und geben Sie eine Antwortdatei. Verwenden Sie beispielsweise zum Auflisten des Pakets in ein offline-Windows-Abbild den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-Packages
    ```

2.  Einstellungen in der `<servicing>` und `<settings pass="offlineServicing">` Abschnitten einer Antwortdatei auf dem Windows-Abbild angewendet werden. Beim nächsten Starten des Computers werden die Pakete und Einstellungen verarbeitet.

Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

### <a name="span-idtousedismonarunningwindowsimagespanspan-idtousedismonarunningwindowsimagespanspan-idtousedismonarunningwindowsimagespanto-use-dism-on-a-running-windows-image"></a><span id="To_use_DISM_on_a_running_Windows_image"></span><span id="to_use_dism_on_a_running_windows_image"></span><span id="TO_USE_DISM_ON_A_RUNNING_WINDOWS_IMAGE"></span>Mit DISM für eine ausgeführte Windows-Abbild

In diesem Szenario führen Sie das Tool DISM für eine ausgeführte Windows-Installation.

-   Schwelle Windows online DISM ausführen und eine Antwortdatei angeben. Verwenden Sie beispielsweise, um Informationen in einem Windows-Abbild Treiber den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-Drivers
    ```

    **Wichtige**  
    Wenn Sie mit einer Antwortdatei für ein Windows-Installation online DISM verwenden, sollte die Antwortdatei nur die Elemente im **OfflineServicing** Konfiguration Durchgang enthalten. Dies ist, da einige Einstellungen im Durchgang Konfiguration **specialize** zur online Windows-Installation angewendet werden können.

     

In einigen Fällen müssen Sie möglicherweise den Computer neu starten. Wenn Sie Ihre Windows-Installation ein Sprachpaket hinzugefügt haben, müssen Sie den Computer beispielsweise neu starten.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[Verallgemeinern](generalize.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






