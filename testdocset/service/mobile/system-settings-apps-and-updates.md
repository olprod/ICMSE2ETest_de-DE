---
author: kpacquer
Description: "Die Einstellungen für apps System und updates"
ms.assetid: 28da264d-0ab9-4a16-8382-53304ee86421
MSHAttr: PreferredLib:/library/windows/hardware
title: "Die Einstellungen für apps System und updates"
ms.openlocfilehash: 3385f1226961000cf04e001f789838191f77a58c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="system-settings-apps-and-updates"></a>System Einstellungen apps und updates


Vorinstallierte System Einstellungen apps ermöglichen OEMs, um benutzerdefinierte Einstellungen für die Hardwarekomponenten verfügbar zu machen, dass sie ein Gerät zur Unterscheidung von anderen Geräten hinzufügen.

Updates Einstellungen für apps aus dem Betriebssystemupdates separat geliefert werden und müssen vom Benutzer initiiert werden. Aus diesem Grund muss die Einstellungsapp konzipiert zum Verwalten von Problemen wie Abwärtskompatibilität. Darüber hinaus der Benutzer möglicherweise initiieren eine Sicherung und Wiederherstellung Sequenz oder Zurücksetzen des Geräts, von denen entweder die aktive Version der Einstellungsapp ändern kann. Zum Testen und beheben alle möglichen Szenarien, muss eine Strategie entwickelt werden.

**Wichtige**  
Aufgrund der Komplexität der Synchronisieren von der Einstellungsapp und Gerätetreiber-Registrierung die Einstellung ändert sich für diese apps wird abgeraten. Sorgfältiges Überprüfen der Richtlinien in diesem Thema Strategien zur Vermeidung von registrierungsänderungen sowie wichtige Szenarien, die bei der Vorbereitung von Updates gelöst werden müssen.

Beispielszenarien Schwerpunktthemen Einstellungen in der Registrierung gespeichert; Wenn die app andere Speichermechanismen wie isolierten Speicher verwendet wird, ist ähnlich wie Analysis erforderlich.

 

In den folgenden Abschnitten beschreiben einiger die wichtigen Aspekte für die Verwaltung von System Einstellungen apps im Laufe getrennt werden Updates, Sicherung und Wiederherstellung Vorgänge und setzt:

-   [Verwalten von Updates auf Einstellungen für apps](#managing)

-   [Einstellungen app OTA-updates](#ota)

-   [Updateszenarien](#update)

-   [Aktualisieren von Szenarien mit Änderung der Registrierung](#registry)

-   [Sichern und Wiederherstellen von Szenarien](#backup)

-   [Zurücksetzen von Szenarien](#reset)

-   [Zusammenfassung der vorinstallierte Einstellungen app-Szenarien](#summary)

## <a name="span-idmanagingspanspan-idmanagingspanmanaging-updates-to-settings-apps"></a><span id="managing"></span><span id="MANAGING"></span>Verwalten von Updates auf Einstellungen für apps


Einstellungen für apps werden mithilfe der Sendemethode Store aktualisiert. Stellen Sie sicher, dass die Einstellungsapp auf dem aktuellen Stand ist, eine Versionsnummer auf dem Gerät verwaltet werden kann, und ein externen Webdiensts aufgerufen werden konnte, um zu überprüfen, um festzustellen, ob die neueste Version installiert ist. Wenn ein Update erforderlich ist, kann der Benutzer aufgefordert, ein Update für die Einstellungsapp zu initiieren. Andere gleichmäßig effektive Ansätze sind möglich.

Eine Versionsnummer kann angezeigt werden, in der Einstellungsapp zu Support für Kunden zu ermitteln, welche Version verwendet wird. Auch wenn der Benutzer die Store-app ausgeführt wird, werden ausstehende Updates angezeigt. Diese Updates umfassen Updates für Einstellungen apps verfügbar sind. Speichern Sie Updates immer Upgrade auf die neueste Version die app aus einer früheren Version.

## <a name="span-idotaspanspan-idotaspansettings-app-ota-updates"></a><span id="ota"></span><span id="OTA"></span>Einstellungen app OTA-updates


Damit können die neueste Version der vorinstallierte app installiert werden soll, wenn das Gerät zurückgesetzt wird, kann ein over-the (OTA)-Paket-Update für die vorinstallierte app vorbereitet werden. Dieses OTA-Update wird die aktuelle aktive Version auf dem Gerät nicht aktualisiert. Es wird nur die gespeicherte Version aktualisiert, die verwendet wird, wenn das Gerät zurückgesetzt wird. Dies bedeutet, dass es kann zwei verschiedene Versionen der Einstellungsapp auf dem Gerät

In den folgenden Abbildungen die aktive Version, der der Benutzer interagiert, wird im oberen Feld blau dargestellt, und die Version, die auf dem Gerät gespeichert ist, wird grau dargestellt. Beispielsweise das Gerät ausgeliefert eine vorinstallierte Version 1.0 des ein Einstellungsapp, die nicht wurde aktualisiert OTA, und der Benutzer herunterlädt eine Version 1.1 der Einstellungsapp aus dem Speicher, die gespeicherten und aktiven Versionen sind wie folgt dargestellt.

![OEM\-Einstellungen\-app\-Version\-1\-0](images/ooem-settings-app-version-1-0.png)

## <a name="span-idupdatespanspan-idupdatespanupdate-scenarios"></a><span id="update"></span><span id="UPDATE"></span>Updateszenarien


Wie OEMs Updates vorzubereiten, müssen sie die möglichen Verwendungsszenarien identifizieren und testen die, um die gewünschte Update und die Benutzeroberfläche der Anwendung zu erstellen. Hier werden Einstellungen app Updateszenarien zusammengefasst. Alle Szenarien beginnen Sie mit einer Version 1.0 einer Einstellungsapp und Gerätetreiber Version 1.0, dass beide Registrierung Einstellung A. verwenden Im folgenden Diagramm wird den Start-Status für diese Szenarien.

![OEM\-Einstellungen\-app\-Registrierung\-Rega\-s0\-d0](images/oem-settings-app-registry-rega-s0-d0.png)

### <a name="span-iddriverupdatespanspan-iddriverupdatespanspan-iddriverupdatespandriver-update"></a><span id="Driver_update"></span><span id="driver_update"></span><span id="DRIVER_UPDATE"></span>Treiber-update

1.  Das Gerät im Lieferumfang von Einstellungen für app-Treiber 1.0 und zugeordneten Code 1.0.

2.  Das over-the Update nicht enthalten, die die aktualisierte 1.1 app, damit die Einstellungsapp 1.0 gespeicherten und auf dem Gerät aktiv ist.

3.  Ein over-the Update auftritt, den Treibercode auf 1.1 aktualisieren.

Wenn keine aktuelle registrierungsänderungen in den 1.1 Gerät Treibercode in das Update zugestellt vorhanden sind, kann weiterhin der Benutzer die Version 1.0 der Einstellungsapp erfolgreich ausgeführt.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrya\-s0\-d1](images/oem-settings-app-registrya-s0-d1.png)

## <a name="span-idregistryspanspan-idregistryspanupdate-scenarios-with-registry-changes"></a><span id="registry"></span><span id="REGISTRY"></span>Szenarien mit registrierungsänderungen aktualisieren


Aufgrund der Komplexität der Synchronisierung von der Einstellungsapp und Gerätetreiber, Registrierung sollte die Option Einstellung ändert sich vermieden werden. Vermeiden, indem die Notwendigkeit, vorhandene Registrierungsdaten zu aktualisieren konnte Code, um die vorhandene Registrierungsdaten gelesen und auf einen neuen Unterschlüssel, migrieren, aktualisiert werden, sodass alle vorhandenen benutzereinstellungen beibehalten werden. Sie können auch möglicherweise Ansätze, wie eine Zahl Überprüfung der Version hinzufügen, wenn die Einstellungsapp gestartet wird (zur Bestimmung, welche Registrierungswerte verwenden) geeignet.

Wenn ein Update für einen Registrierungswert vorbereitet wird, die geändert werden kann, wie das Gerät verwendet wird – beispielsweise von einem Benutzer eine Einstellung in einem Menü ändern – Bereitstellung von XML (Provxml) muss verwendet werden. Weitere Informationen finden Sie unter [Verwenden von Bereitstellung Dateien um Registrierungseinträge zu aktualisieren, die sich ändern kann](using-provisioning-files-to-update-registry-settings-that-may-change.md).

Falls ein Update zu eine geänderten registrierungseinstellung Behebung vorbereitet wird, müssen OEMs identifizieren die möglichen Verwendungsszenarien und testen die, um die gewünschte Update und die Benutzeroberfläche der Anwendung zu erstellen. Eine Strategie sollten entwickelt werden, die Adresse alle Updates für die Versionen von Einstellungsapp, Betriebssystem und Gerätetreiber koordiniert werden müssen.

Das folgende Updateszenario zeigt die unerwünschte Situation, wenn eine Änderung der Einstellung Registrierung stattfindet, die von einer OEM-Gerätetreiber und einer Einstellungsapp verwendet wird. Der Einstellungsapp und Gerätetreiber verwenden denselben Registrierungsschlüssel festlegen A, anfänglich wie nachfolgend dargestellt.

![OEM\-Einstellungen\-app\-Registrierung\-Rega\-s0\-d0](images/oem-settings-app-registry-rega-s0-d0.png)

### <a name="span-iddriverupdatewithregistrychangespanspan-iddriverupdatewithregistrychangespanspan-iddriverupdatewithregistrychangespandriver-update-with-registry-change"></a><span id="Driver_update_with_registry_change"></span><span id="driver_update_with_registry_change"></span><span id="DRIVER_UPDATE_WITH_REGISTRY_CHANGE"></span>Treiberupdate mit Änderung der Registrierung

1.  Das Gerät im Lieferumfang von Einstellungen app 1.0 und zugehörige Treibercode 1.0, die Registrierung Einstellung a liest

2.  Ein over-the Update auftritt, verwendet den Treibercode auf 1.1 aktualisieren die nun neue Registrierung festlegen B.

3.  Die Einstellungsapp 1.0 wird auf dem Gerät, das die ältere Registrierung Einstellung A. verwendet

Wenn der Benutzer mit 1.0 Einstellungsapp ändert, aber der 1.1-Treibercode ist B Einstellung in der Registrierung verwenden, wird die Einstellungsapp nicht erwartungsgemäß. Beispielsweise kann ein Benutzer in der Settings-app, die nicht tatsächlich etwas ändern Änderungen vornehmen.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrierung\-regab\-s0\-d1](images/oem-settings-app-registry-regab-s0-d1.png)

Der Benutzer kann festlegen, dass sie eine neuere Version der Einstellungsapp herunterladen müssen. Wenn der Benutzer die aktualisierte Version 1.1 downloads, ist die Einstellungsapp ordnungsgemäß funktionsfähig.

## <a name="span-idbackupspanspan-idbackupspanbackup-and-restore-scenarios"></a><span id="backup"></span><span id="BACKUP"></span>Sichern und Wiederherstellen von Szenarien


Vorinstallierte apps werden nicht aus der Cloud wiederhergestellt. Vielmehr werden vorinstallierte apps neu installiert, mit der gespeicherten Version auf dem Gerät. Wenn die gespeicherte Version von den Einstellungen, die app wurde OTA aktualisiert, wird die aktualisierte Version installiert werden, wenn das Telefon wiederhergestellt wird. Wenn ein Benutzer das Gerät zurückgesetzt und führt eine Wiederherstellung und nicht die gespeicherte Version aktualisiert wurde, wird der Benutzer müssen Sie auch Updates im Speicher für die apps vorinstallierte Einstellungen überprüfen.

Dieses Verhalten unterscheidet sich von Store-apps, die auf dem Gerät nicht geladen wurden. Wenn ein Gerät gesichert ist, wird eine Liste der installierten Programme als Teil der Sicherung gespeichert. Wenn das Gerät wiederhergestellt wird, werden die aktuellen Versionen von apps mithilfe der Liste apps, die erstellt wurde, wenn das Telefon gesichert wurde installiert. Weitere Informationen zu diesem Feature finden Sie unter [verdienen sichern](http://go.microsoft.com/fwlink/p/?LinkId=331631).

Überprüfen Sie nach das Update wird übermittelt, und der Benutzer die Einstellungsapp startet, die app konnte einen Webserver und sehen, dass eine aktualisierte Version der Einstellungsapp verfügbar ist. Der Benutzer konnte das Update Herunterladen aufgefordert werden. Wenn der Benutzer die Store-Anwendung auf dem Gerät ausgeführt wird, werden ausstehende Einstellungen für apps Updates es angezeigt. Der Benutzer kann nach einer gewissen Zeitspanne die 1.1 Einstellungsapp herunterladen und können es erfolgreich.

### <a name="span-idbackupandrestoreafterupdatespanspan-idbackupandrestoreafterupdatespanspan-idbackupandrestoreafterupdatespanbackup-and-restore-after-update"></a><span id="Backup_and_restore_after_update"></span><span id="backup_and_restore_after_update"></span><span id="BACKUP_AND_RESTORE_AFTER_UPDATE"></span>Sicherung und Wiederherstellung nach Aktualisierung

1.  Das Gerät im Lieferumfang von Einstellungsapp 1.0 und Gerät Treibercode 1.0.

2.  Ein over-the Update auftritt, den Treibercode auf 1.1 aktualisieren.

3.  Der Benutzer downloads und die neuere 1.1 Einstellungsapp verwendet.

4.  Der Benutzer sichert das Gerät mithilfe des Sicherungsfeatures.

5.  Der Benutzer verwendet die Wiederherstellungsfunktion zum Wiederherstellen einer früheren Version des Betriebssystems. Während der Wiederherstellung die vorinstallierte apps neu installiert werden, und die Version 1.0 der Einstellungsapp auf dem Gerät aktiv ist.

Wie bereits erläutert, wenn keine Abhängigkeiten zwischen der Updates und der Einstellungen der Anwendung vorhanden sind, kann der Benutzer erfolgreich ausführen die ältere Version 1.0 der Einstellungsapp, bis sie eine aktualisierte Version herunterladen.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrya\-s0\-d1](images/oem-settings-app-registrya-s0-d1.png)

### <a name="span-idbackupandrestoreafterupdatewithregistrychangespanspan-idbackupandrestoreafterupdatewithregistrychangespanspan-idbackupandrestoreafterupdatewithregistrychangespanbackup-and-restore-after-update-with-registry-change"></a><span id="Backup_and_restore_after_update_with_registry_change"></span><span id="backup_and_restore_after_update_with_registry_change"></span><span id="BACKUP_AND_RESTORE_AFTER_UPDATE_WITH_REGISTRY_CHANGE"></span>Sicherung und Wiederherstellung nach Aktualisierung mit Änderung der Registrierung

1.  Das Gerät im Lieferumfang von Einstellungen app 1.0 und zugehörige Treibercode 1.0, die Registrierung Einstellung a liest

2.  Der Benutzer sichert das Gerät mithilfe des Sicherungsfeatures ab.

3.  Ein over-the Update auftritt, verwendet den Treibercode auf 1.1 aktualisieren die nun neue Registrierung festlegen B.

4.  Der Benutzer die neuere Einstellungsapp herunterlädt und die neue Registrierung festlegen b erfolgreich verwendet

5.  Der Benutzer verwendet das Feature zum Wiederherstellen eine frühere Version des Betriebssystems wiederherstellen. Während der Wiederherstellung die vorinstallierte apps neu installiert werden, und die Version 1.0 der Einstellungsapp auf dem Gerät aktiv ist

Wenn der Benutzer mit 1.0 Einstellungsapp ändert, werden die Systemeinstellungen nicht erwartungsgemäß.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrierung\-regab\-s0\-d1](images/oem-settings-app-registry-regab-s0-d1.png)

Der Benutzer kann festlegen, dass sie auf eine neuere Version der Einstellungsapp aktualisieren müssen. Wenn der Benutzer auf Version 1.1 der Einstellungsapp downloads, die app wird die neue Einstellung B in der Registrierung gelesen und ordnungsgemäß ausgeführt wird.

## <a name="span-idresetspanspan-idresetspanreset-scenarios"></a><span id="reset"></span><span id="RESET"></span>Zurücksetzen von Szenarien


Zusätzliche Szenarien vorhanden – beispielsweise wenn das Gerät vom Kunden mit **Standardeinstellungen** zurückgesetzt ist &gt; **System** &gt; **zu** &gt; **Ihr Telefon zurücksetzen**. Der Benutzer kann das Gerät, zum Beispiel, wenn es gewartet wird oder übertragen den Besitz des Geräts zurückgesetzt. Wenn das Gerät zurückgesetzt wird, gibt die Einstellungsapp auf die Version zurück, die in einer app-Paket-Datei auf dem Gerät gespeichert ist; Dies kann die Version sein, die auf dem Gerät geliefert. OS Updates, die das Gerät eingegangen sind auch nach dem Zurücksetzen auf dem Gerät aktiv. Dies bedeutet, dass die ursprünglichen Einstellungsapp möglicherweise mit neuere Versionen des Betriebssystems und alle zugehörigen Gerätetreiber neueren Versionen ausgeführt werden muss. Diese Abhängigkeiten und Interaktionen sollten als Updates auf Einstellungen für apps berücksichtigt und Gerätetreiber vorbereitet werden. Weitere Informationen über das Verhalten der OS Zurücksetzen finden Sie unter [das Gerät zurückzusetzen](../../manufacture/mobile/resetting-a-phone-during-manufacturing.md).

### <a name="span-idresetafterupdatespanspan-idresetafterupdatespanspan-idresetafterupdatespanreset-after-update"></a><span id="Reset_after_update"></span><span id="reset_after_update"></span><span id="RESET_AFTER_UPDATE"></span>Nach dem Update zurücksetzen

1.  Das Gerät im Lieferumfang von Einstellungen app 1.0 und zugehörige Gerät Treibercode 1.0.

2.  Ein over-the Update auftritt, den Treibercode auf 1.1 aktualisieren.

3.  Der Benutzer lädt die neuere 1.1 Einstellungsapp herunter.

4.  Das over-the Update nicht enthalten, die die aktualisierte 1.1 app, damit die Einstellungsapp 1.0 auf dem Gerät ist.

5.  Der Benutzer setzt das Gerät.

6.  Updates für das Gerät Treibercode beibehalten werden nach dem Zurücksetzen und Version 1.1 des Codes Treiber Gerät ist auf dem Gerät aktiv.

7.  Da die Einstellungsapp nicht Teil des Updates ist, wird es nicht automatisch in die Basis-Image Zurücksetzen des aktualisiert.

Wie in den früheren Szenarien Wenn es keine Abhängigkeiten zwischen der Updates und die Einstellungsapp sind kann der Benutzer ausführen die ältere Version 1.0 der Einstellungsapp, bis sie ein Update herunterladen.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrya\-s0\-d1](images/oem-settings-app-registrya-s0-d1.png)

### <a name="span-idresetafterupdatewithregistrychangespanspan-idresetafterupdatewithregistrychangespanspan-idresetafterupdatewithregistrychangespanreset-after-update-with-registry-change"></a><span id="Reset_after_update_with_registry_change"></span><span id="reset_after_update_with_registry_change"></span><span id="RESET_AFTER_UPDATE_WITH_REGISTRY_CHANGE"></span>Nach dem Update mit Änderung der Registrierung zurücksetzen

1.  Das Gerät im Lieferumfang von Einstellungen app 1.0 und zugehörige Treibercode 1.0, die Registrierung Einstellung a liest

2.  Ein over-the Update auftritt, verwendet den Treibercode auf 1.1 aktualisieren die nun neue Registrierung festlegen B.

3.  Der Benutzer die neuere Einstellungsapp herunterlädt und die neue Registrierung festlegen b erfolgreich verwendet

4.  Der Benutzer setzt das Gerät zurück.

5.  Updates für das Gerät Treibercode beibehalten werden nach dem Zurücksetzen und Version 1.1 des Codes Treiber Gerät ist auf dem Gerät aktiv

6.  Da die Einstellungsapp nicht Teil des Updates ist, es wird nicht automatisch aktualisiert, in die Basis-Image Zurücksetzen des und die Version 1.0 ist auf dem Gerät.

Wie im vorherigen Szenario beim Verwenden der Einstellungsapp 1.0 ändert der Benutzer funktioniert die Systemeinstellungen nicht wie vorgesehen.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrierung\-regab\-s0\-d1](images/oem-settings-app-registry-regab-s0-d1.png)

Der Benutzer kann festlegen, dass sie eine neuere Version der Einstellungsapp herunterladen müssen. Wenn der Benutzer die aktualisierte Version 1.1 downloads, ist die Einstellungsapp ordnungsgemäß funktionsfähig.

### <a name="span-idresetafterupdatewithregistrychangeandpreloadedappupdatespanspan-idresetafterupdatewithregistrychangeandpreloadedappupdatespanspan-idresetafterupdatewithregistrychangeandpreloadedappupdatespanreset-after-update-with-registry-change-and-preloaded-app-update"></a><span id="Reset_after_update_with_registry_change_and_preloaded_app_update"></span><span id="reset_after_update_with_registry_change_and_preloaded_app_update"></span><span id="RESET_AFTER_UPDATE_WITH_REGISTRY_CHANGE_AND_PRELOADED_APP_UPDATE"></span>Nach dem Update mit Änderung der Registrierung und vorinstallierte app-Update zurücksetzen

In diesem letzten Szenario wird das Gerät vom Kunden mit **Standardeinstellungen** zurückgesetzt &gt; **System** &gt; **zu** &gt; **Ihr Telefon zurücksetzen**.

1.  Das Gerät im Lieferumfang von Einstellungen app 1.0 und zugehörige Treibercode 1.0, die Registrierung Einstellung a liest

2.  Ein over-the Update auftritt, verwendet den Treibercode auf 1.1 aktualisieren die nun neue Registrierung festlegen B.

3.  Das over-the-Update enthält auch ein Update für das 1.1 Einstellungen vorab geladen app-Paket. Dieses Update bietet ein neues app-Paket, das nur verwendet wird, wenn das Gerät zurückgesetzt und der anfänglichen vorinstallierte apps installiert sind. Zu diesem Zeitpunkt wurde das Szenario der Benutzer nicht das Gerät zurückgesetzt, damit Version 1.0 der Einstellungsapp verwendet wird.

4.  Der Benutzer die neuere Einstellungsapp herunterlädt und die neue Registrierung festlegen b erfolgreich verwendet

5.  Der Benutzer setzt das Gerät zurück.

6.  Beibehalten von Updates für das Gerät Treibercode nach dem Zurücksetzen und Version 1.1 des Codes Treiber Gerät ist auf dem Gerät aktiv. Darüber hinaus, da das vorinstallierte Einstellungen app 1.1 Update OTA übermittelt wurde, wird es installiert, wenn das Gerät zurückgesetzt wird.

In diesem Szenario sowohl die Einstellungsapp 1.1 und Gerätetreiber 1.1 Einstellung B in der Registrierung verwenden, und die app ordnungsgemäß funktioniert.

Im folgenden Diagramm wird der Endzustand für dieses Szenario.

![OEM\-Einstellungen\-app\-Registrierung\-Regb\-s1\-d1](images/oem-settings-app-registry-regb-s1-d1.png)

## <a name="span-idsummaryspanspan-idsummaryspansummary-of-preloaded-settings-app-scenarios"></a><span id="summary"></span><span id="SUMMARY"></span>Zusammenfassung der vorinstallierte Einstellungen app-Szenarien


In der folgenden Tabelle werden die Szenarien vorinstallierte apps zusammengefasst.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">OTA-update</th>
<th align="left">Vom Benutzer initiierte Store update</th>
<th align="left">Sicherung und Wiederherstellung</th>
<th align="left">Reset</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Vorinstallierte Einstellungen app Update konnte vom OEM erstellt werden. aktive installierte Anwendung werden nicht aktualisiert, der einen gespeicherten.</p></td>
<td align="left"><p>Aktive app wird aktualisiert. die gespeicherte app bleibt unverändert.</p></td>
<td align="left"><p>Gespeicherte app auf dem Telefon wird neu installiert. Wenn die gespeicherte Version nicht aktualisiert wurden, muss der Benutzer zum Herunterladen der aktualisierten Version aus dem Speicher.</p></td>
<td align="left"><p>Gespeicherte app auf dem Gerät wird neu installiert. Wenn die gespeicherte Version nicht aktualisiert wurden, muss der Benutzer zum Herunterladen der aktualisierten Version aus dem Speicher.</p></td>
</tr>
</tbody>
</table>

 

Diese Beispielszenarien erläuternde sind und nicht alle möglichen Kunden Verwendungsszenarien oder die Kombinationen von möglichen Update-Releases aufzeichnen. OEMs müssen die möglichen Verwendungsszenarien identifizieren und testen die bei der Vorbereitung von Updates.

Um die Versionen des Treibers Einstellungen app und Gerät koordinieren beim Anwenden von Updates, um benutzerfreundlich zu vermeiden, sollten eine Strategie entwickelt werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Mithilfe von Bereitstellung Dateien, um Registrierungseinträge zu aktualisieren, die geändert werden können](using-provisioning-files-to-update-registry-settings-that-may-change.md)

 

 






