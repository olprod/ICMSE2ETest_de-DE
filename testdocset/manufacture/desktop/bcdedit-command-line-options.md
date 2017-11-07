---
author: Justinha
Description: BCDEdit ist ein Befehlszeilentool zum Verwalten von Boot Configuration Data (BCD).
ms.assetid: cf7d52f0-13fb-416d-9ec5-9e4eff4fd774
MSHAttr: PreferredLib:/library/windows/hardware
title: BCDEdit Befehlszeilenoptionen
ms.openlocfilehash: 0179c5d2aa91b43f359071be2987206ac31036e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idbcdeditcommand-lineoptionsspanbcdedit-command-line-options"></a><span id="bcdedit_command-line_options"></span>BCDEdit Befehlszeilenoptionen


BCDEdit ist ein Befehlszeilentool zum Verwalten von Boot Configuration Data (BCD).

BCD-Dateien enthalten einen Speicher, mit dem beschreiben Boot-Anwendungen und Anwendungseinstellungen zu starten.

BCDEdit für verschiedene Zwecke, einschließlich Erstellen neuer Speicher verwendet werden kann, Ändern vorhandener Speicher, Hinzufügen von Menüoptionen zu starten, und so weiter.

Sie benötigen Administratorrechte für BCDEdit verwenden, um BCD zu ändern. Starten Sie die Befehlszeile (Admin) oder verwenden Sie Windows PE.

Eine normale Herunterfahren und Neustart ist erforderlich, um sicherzustellen, dass alle geänderten BCDEdit Einstellungen geleert werden auf dem Datenträger.

BCDEdit befindet sich auf der %windir%\\-Ordner System32.

BCDEdit ist in die standard-Datentypen beschränkt und dient hauptsächlich zum Ausführen der einzelner allgemeiner Änderungen an BCD. Verwandte Ressourcen:

-   Einige allgemeine BCD Vorgänge, wie eine Partition wiederherstellen oder einen neuen PC Systempartition einrichten können leichter mithilfe von [BCDboot](bcdboot-command-line-options-techref-di.md)erreicht werden.
-   Sollten Sie für komplexe Vorgänge oder nicht standardmäßigen-Datentypen in der leistungsstarke und flexible benutzerdefinierte Tools erstellen mithilfe der BCD Windows-Verwaltungsinstrumentation (WMI) Application programming Interface (API).

## <a name="span-idbcdeditcommand-lineoptionsspanspan-idbcdeditcommand-lineoptionsspanspan-idbcdeditcommand-lineoptionsspanbcdedit-command-line-options"></a><span id="BCDEdit_Command-Line_Options"></span><span id="bcdedit_command-line_options"></span><span id="BCDEDIT_COMMAND-LINE_OPTIONS"></span>BCDEdit Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen stehen für BCDEdit.exe.

**BCDEdit/Command***\[Argument1\] \[Argument2\] ...*

### <a name="span-idhelpspanspan-idhelpspanspan-idhelpspanhelp"></a><span id="Help"></span><span id="help"></span><span id="HELP"></span>Hilfe

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/? [Befehl]</td>
<td align="left"><p>Zeigt eine Liste der BCDEdit-Befehlen.</p>
<p>Um ausführliche Hilfe für einen bestimmten Befehl anzuzeigen, führen Sie <strong>Bcdedit /? </strong><em>Befehl</em>, wobei der <em>Befehl</em> den Namen des Befehls ist Sie weitere Informationen zu durchsucht werden.</p>
<pre class="syntax" space="preserve"><code>bcdedit /? createstore</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idoperatingonastorespanspan-idoperatingonastorespanspan-idoperatingonastorespanoperating-on-a-store"></a><span id="Operating_on_a_store"></span><span id="operating_on_a_store"></span><span id="OPERATING_ON_A_STORE"></span>Betrieb von in einem Speicher

| Option       | Beschreibung                                                                                                                                                                                                                                                             |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CreateStore | Erstellt einen neue leere Boot Daten Konfigurationsspeicher. Der erstellte Speicher ist kein Systemspeicher.                                                                                                                                                                             |
| / Export      | Exportiert den Inhalt des Systems in eine Datei zu speichern. Diese Datei kann später verwendet werden, um den Status des Systemspeichers wiederherzustellen. Dieser Befehl ist nur für den Systemspeicher gültig.                                                                                            |
| / Import      | Wird den Zustand des Systemspeichers mithilfe einer Sicherungsdatei zuvor mithilfe der Option/Export generiert wiederhergestellt. Dieser Befehl löscht die Einträge im Systemspeicher, bevor der Import stattfindet. Dieser Befehl ist nur für den Systemspeicher gültig.      |
| / Store       | Diese Option kann mit den meisten BCDedit-Befehlen zum Angeben des zu verwendenden Speichers verwendet werden. Wenn diese Option nicht angegeben wird, arbeitet BCDEdit im System Store. Des Befehls Bcdedit/store allein ist gleichbedeutend mit den aktiven Bcdedit/Enum-Befehl ausführen. |
| /sysstore    | Das System Store Gerät festgelegt. Dies betrifft nur EFI-basierte Systeme. Es nicht auch nach einem Neustart bestehen, und wird nur in Fällen, in denen das System Store Gerät mehrdeutige verwendet.                                                                                            |

 

### <a name="span-idoperatingonentriesinastorespanspan-idoperatingonentriesinastorespanspan-idoperatingonentriesinastorespanoperating-on-entries-in-a-store"></a><span id="Operating_on_entries_in_a_store"></span><span id="operating_on_entries_in_a_store"></span><span id="OPERATING_ON_ENTRIES_IN_A_STORE"></span>Betrieb von Einträgen in einem Speicher

| Option  | Beschreibung                                                                                                                                                                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / Copy   | Es wird eine Kopie einer angegebenen Boot-Eintrag im gleichen Systemspeicher.                                                                                                                                                                                                                                  |
| / Erstellen | Erstellt einen neuen Eintrag im Datenspeicher Boot-Konfiguration. Wenn ein bekannter Bezeichner ist angegeben, klicken Sie dann den Parameter/Application, / erben, Device Optionen können nicht angegeben werden. Wenn ein Bezeichner ist nicht angegebenen oder nicht gut bekannten ein Parameter/Application, / erben, oder Device Option angegeben werden muss. |
| / Delete | Löscht ein Element aus der angegebenen Eintrags.                                                                                                                                                                                                                                                        |
| / Mirror | Spiegelung der Einträge erstellt im Informationsspeicher.                                                                                                                                                                                                                                                           |

 

### <a name="span-idchangingentryoptionsspanspan-idchangingentryoptionsspanspan-idchangingentryoptionsspanchanging-entry-options"></a><span id="Changing_entry_options"></span><span id="changing_entry_options"></span><span id="CHANGING_ENTRY_OPTIONS"></span>Ändern der Optionen für die Einträge

| Option       | Beschreibung                                    |
|--------------|------------------------------------------------|
| / deletevalue | Löscht ein angegebenes Element aus einer Boot-Eintrag. |
| / Set         | Legt einen Eintrag Optionswert fest.                    |

Mit diesem Befehl aktivieren beispielsweise das System als vertrauenswürdig, dass Windows-Insider Preview erstellt, die mit Zertifikaten signiert sind, die standardmäßig nicht als vertrauenswürdig eingestuft werden:

``` syntax
Bcdedit /set {bootmgr} flightsigning on
Bcdedit /set flightsigning on
```
Nach Ausführung des Befehls neu starten. Flightsigning zu deaktivieren:

``` syntax
Bcdedit /set {bootmgr} flightsigning off
Bcdedit /set flightsigning off
``` 

### <a name="span-idcontrollingoutputspanspan-idcontrollingoutputspanspan-idcontrollingoutputspancontrolling-output"></a><span id="Controlling_output"></span><span id="controlling_output"></span><span id="CONTROLLING_OUTPUT"></span>Steuern der Ausgabe

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/ Enum</td>
<td align="left">Listen Einträge in einem Speicher. Die Option/enum ist der Standardwert für BCEdit, damit den Bcdedit-Befehl ohne Optionen Ausführen des Befehls Bcdedit/Enum active entspricht.</td>
</tr>
<tr class="even">
<td align="left">/ v</td>
<td align="left">Ausführlichen Modus. In der Regel werden alle bekannten-Eintragsbezeichner durch ihre benutzerfreundliche Kurzform dargestellt. Angeben von als Befehlszeilenoption/v werden alle Bezeichner vollständig angezeigt.
<p>Des Befehls Bcdedit/v allein entspricht den Bcdedit/Enum active/v-Befehl ausführen.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idcontrollingthebootmanagerspanspan-idcontrollingthebootmanagerspanspan-idcontrollingthebootmanagerspancontrolling-the-boot-manager"></a><span id="Controlling_the_boot_manager"></span><span id="controlling_the_boot_manager"></span><span id="CONTROLLING_THE_BOOT_MANAGER"></span>Steuern des Start-Managers

| Option             | Beschreibung                                                                                                                                                                                                                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /BOOTSEQUENCE      | Gibt eine einmalige Anzeigereihenfolge für den nächsten Start verwendet werden soll. Dieser Befehl ist ähnlich der Option /displayorder, außer dass sie nur das nächste Mal verwendet wird, wenn der Computer gestartet wird. Anschließend wird der Computer auf die ursprüngliche Anzeigereihenfolge zurückgesetzt. |
| / default           | Gibt den Standardeintrag, den der Start-Manager auswählt, wenn das Timeout abläuft.                                                                                                                                                                  |
| /DISPLAYORDER      | Gibt die Anzeigereihenfolge, die der Start-Manager bei der Anzeige von Startoptionen für einen Benutzer verwendet.                                                                                                                                                       |
| / Timeout           | Gibt die Wartezeit in Sekunden an, bevor der Start-Manager den Standardeintrag auswählt.                                                                                                                                                           |
| /TOOLSDISPLAYORDER | Gibt die Anzeigereihenfolge für die Start-Manager zu verwenden, wenn Sie im Menü Extras anzeigen.                                                                                                                                                              |

 

### <a name="span-idemergencymanagementservicesoptionsspanspan-idemergencymanagementservicesoptionsspanspan-idemergencymanagementservicesoptionsspanemergency-management-services-options"></a><span id="Emergency_Management_Services_options"></span><span id="emergency_management_services_options"></span><span id="EMERGENCY_MANAGEMENT_SERVICES_OPTIONS"></span>Notruf Rights Management Services-Optionen

| Option       | Beschreibung                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------|
| / bootems     | Aktiviert oder deaktiviert (Emergency Management Services, EMS) für den angegebenen Eintrag.                                          |
| / EMS         | Aktiviert oder deaktiviert zur Abstimmung für den angegebenen Betriebssystem Boot-Eintrag.                                                    |
| /Emssettings | Legt die globalen Einstellungen zur Abstimmung für den Computer an. /Emssettings nicht aktivieren oder deaktivieren zur Abstimmung für einen bestimmten Boot-Eintrag. |

 

### <a name="span-iddebuggingspanspan-iddebuggingspanspan-iddebuggingspandebugging"></a><span id="Debugging"></span><span id="debugging"></span><span id="DEBUGGING"></span>Debuggen

| Option              | Beschreibung                                                                                                                                                                                                                                                               |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / bootdebug          | Aktiviert oder deaktiviert den Startdebugger für einen angegebenen Boot-Eintrag. Mit diesem Befehl für jede Boot-Eintrag funktioniert, es ist zwar nur für Boot Applikationen.                                                                                                             |
| /dbgsettings        | Gibt an, oder zeigt die globale Debuggereinstellungen für das System. Mit diesem Befehl aktivieren oder deaktivieren den Kernel-Debugger nicht; Verwenden der Option/Debug zu diesem Zweck. Um eine einzelne globale Debugger-Einstellung festgelegt, verwenden Sie den Befehl Bcdedit /setdbgsettings Type-Wert. |
| / Debug              | Aktiviert oder deaktiviert den Kernel-Debugger für einen angegebenen Boot-Eintrag.                                                                                                                                                                                                       |
| /hypervisorsettings | Legt den Hypervisor-Parameter.                                                                                                                                                                                                                                           |

 

Um eine neue Installation zu beheben, aktivieren Sie Debug-Modus durch Ändern der Boot-Konfigurationsdatei (BCD). Verwenden Sie beispielsweise die folgende Syntax, um Kernel- oder Start-Debuggen aktivieren.

``` syntax
bcdedit /set <id> debug on
```

\endash oder \endash

``` syntax
bcdedit /set <id> bootdebug on
```

in dem &lt;Id&gt; ist die GUID des Loader-Objekts, die zum Laden des Betriebssystems verwendet wird. "Default" kann verwendet werden, wenn das Betriebssystem die Standardoption im Menü Start-Manager ist.

Beispiele von BCDEdit finden Sie unter [Start-Konfigurationsdaten in Windows Vista](http://go.microsoft.com/fwlink/?LinkId=69448).

### <a name="span-idremoteeventloggingspanspan-idremoteeventloggingspanspan-idremoteeventloggingspanremote-event-logging"></a><span id="Remote_event_logging"></span><span id="remote_event_logging"></span><span id="REMOTE_EVENT_LOGGING"></span>Remote-ereignisprotokollierung

| Option         | Beschreibung                                                             |
|----------------|-------------------------------------------------------------------------|
| /eventsettings | Legt die globalen remote-Ereignis Protokollierungsparameter fest.                        |
| / Event         | Aktiviert oder deaktiviert die ereignisprotokollierung von remote-für ein Betriebssystem-Eintrag. |

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot](bcdboot-command-line-options-techref-di.md)

[Einstellungen für UEFI Startkonfigurationsdaten System](bcd-system-store-settings-for-uefi.md)

[BCDEdit-Befehlen für Boot-Umgebung](https://msdn.microsoft.com/library/windows/hardware/dn653986)

[Optimieren von 4 GB: BCDEdit und Boot.ini](https://msdn.microsoft.com/library/windows/desktop/bb613473.aspx)

[Boot-Konfigurationsdaten in Windows Vista](http://go.microsoft.com/fwlink/?LinkId=69448)

 

 




