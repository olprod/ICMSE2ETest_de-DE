---
author: kpacquer
Description: "Updates für vorinstallierte apps und Diensten"
ms.assetid: d3e08bae-f997-4593-9c6d-552fdd7a3d11
MSHAttr: PreferredLib:/library/windows/hardware
title: "Updates für vorinstallierte apps und Diensten"
ms.openlocfilehash: ba4bc7d278f23ef2e83affedba7dea9b5756db6c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updates-to-preloaded-apps-and-services"></a>Updates für vorinstallierte apps und Diensten


Partner-app kann in das Bild enthalten und im Benutzerspeicher wird beim ersten Start installiert werden.

Vorinstallierte apps Updates aus den OS Updates separat geliefert werden und müssen vom Benutzer initiiert werden. Aus diesem Grund muss die vorinstallierte app zum Verwalten von Kompatibilität mit den Updates Main OS und OEM-BSP entworfen werden. Darüber hinaus der Benutzer möglicherweise initiieren eine Sicherung und Wiederherstellung Sequenz oder Zurücksetzen des Geräts, entweder die aktive Version der app vorinstallierte ändern kann. Zum Testen und beheben alle möglichen Szenarien, muss eine Strategie entwickelt werden.

Vorinstallierte *Systemeinstellungen* apps zulassen OEMs benutzerdefinierte Einstellungen für die Hardwarekomponenten verfügbar machen Es sind weitere wichtige Update Aspekte für System Einstellungen apps. Weitere Informationen finden Sie unter [System Einstellungen apps und Updates](system-settings-apps-and-updates.md).

## <a name="span-idsummaryofpreloadedappscenariosspanspan-idsummaryofpreloadedappscenariosspanspan-idsummaryofpreloadedappscenariosspansummary-of-preloaded-app-scenarios"></a><span id="Summary_of_preloaded_app_scenarios"></span><span id="summary_of_preloaded_app_scenarios"></span><span id="SUMMARY_OF_PRELOADED_APP_SCENARIOS"></span>Zusammenfassung der vorinstallierte app-Szenarien


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
<td align="left"><p>Vorinstallierte app-Update konnte vom OEM erstellt werden. aktive installierte Anwendung werden nicht aktualisiert, der einen gespeicherten.</p></td>
<td align="left"><p>Aktive app wird aktualisiert. die gespeicherte app bleibt unverändert.</p></td>
<td align="left"><p>Gespeicherte app auf dem Gerät wird neu installiert. Wenn die gespeicherte Version nicht aktualisiert wurden, muss der Benutzer zum Herunterladen der aktualisierten Version aus dem Speicher.</p></td>
<td align="left"><p>Gespeicherte app auf dem Gerät wird neu installiert. Wenn die gespeicherte Version nicht aktualisiert wurden, muss der Benutzer zum Herunterladen der aktualisierten Version aus dem Speicher.</p></td>
</tr>
</tbody>
</table>

 

Diese Beispielszenarien werden zur Veranschaulichung und nicht alle möglichen Kunden Verwendungsszenarien oder die Kombinationen von Updates, die möglich sind aufzeichnen. OEMs müssen die möglichen Verwendungsszenarien identifizieren und testen die bei der Vorbereitung von Updates.

## <a name="span-idmanagingupdatestopreloadedappsspanspan-idmanagingupdatestopreloadedappsspanspan-idmanagingupdatestopreloadedappsspanmanaging-updates-to-preloaded-apps"></a><span id="Managing_updates_to_preloaded_apps"></span><span id="managing_updates_to_preloaded_apps"></span><span id="MANAGING_UPDATES_TO_PRELOADED_APPS"></span>Verwalten von Updates für apps geladen


Vorinstallierte apps werden mithilfe der Sendemethode Store aktualisiert. Wenn der Benutzer die Store-app ausgeführt wird, werden ausstehende Updates angezeigt. Diese Updates umfassen Updates für vorinstallierte apps verfügbar sind. Updates immer Upgrade auf die neueste Version die app aus einer früheren Version zu speichern.

## <a name="span-idpreloadedappotaupdatesspanspan-idpreloadedappotaupdatesspanspan-idpreloadedappotaupdatesspanpreloaded-app-ota-updates"></a><span id="Preloaded_app_OTA_updates"></span><span id="preloaded_app_ota_updates"></span><span id="PRELOADED_APP_OTA_UPDATES"></span>Vorinstallierte app OTA-updates


Damit können die neueste Version der vorinstallierte app installiert werden soll, wenn das Gerät zurückgesetzt wird, kann ein over-the (OTA)-Paket-Update für die vorinstallierte app vorbereitet werden. Dieses OTA-Update wird die aktuelle aktive Version der app auf dem Gerät nicht aktualisiert. nur aktualisiert die gespeicherte Version, die verwendet wird, wenn das Gerät zurückgesetzt wurde. Dies bedeutet, dass es kann zwei verschiedene Versionen der vorinstallierte app auf dem Gerät

Beispielsweise, wenn das Gerät im Lieferumfang eine vorinstallierte Version 1.0 des einer vorinstallierte-app, die nicht wurde aktualisiert OTA, und der Benutzer eine Version 1.1 der vorinstallierte app aus dem Speicher herunterlädt, die gespeicherten und aktiven Versionen werden sowohl auf dem Gerät vorhanden, wie in der folgenden Abbildung dargestellt.

![OEM\-vorab geladen\-app](images/oem-preloaded-app.png)

## <a name="span-idbackupandrestorescenariosspanspan-idbackupandrestorescenariosspanspan-idbackupandrestorescenariosspanbackup-and-restore-scenarios"></a><span id="Backup_and_restore_scenarios"></span><span id="backup_and_restore_scenarios"></span><span id="BACKUP_AND_RESTORE_SCENARIOS"></span>Sichern und Wiederherstellen von Szenarien


Vorinstallierte apps werden nicht aus der Cloud wiederhergestellt. Vielmehr werden vorinstallierte apps erneut mit der gespeicherten Version auf dem Gerät installiert. Wenn die gespeicherte Version der app vorinstallierte aktualisiert wurde OTA die aktualisierte Version wird installiert, wenn das Gerät wiederhergestellt wird. Wenn ein Benutzer das Gerät zurückgesetzt und führt eine Wiederherstellung und nicht die gespeicherte Version aktualisiert wurde, muss der Benutzer des Speichers für die Updates für die apps vorinstallierte überprüfen.

Dieses Verhalten unterscheidet sich von Store-apps, die auf dem Gerät nicht geladen wurden. Wenn ein Telefon gesichert ist, wird eine Liste der installierten Programme als Teil der Sicherung gespeichert. Wenn das Gerät wiederhergestellt wird, werden die aktuellen Versionen von apps aus der Cloud, mit der Liste von apps, die erstellt wurde, wenn das Telefon gesichert wurde installiert. Weitere Informationen zu diesem Feature finden Sie unter [Sichern von Meine Auswahl](http://go.microsoft.com/fwlink/p/?LinkId=331631).

## <a name="span-idresetscenariosspanspan-idresetscenariosspanspan-idresetscenariosspanreset-scenarios"></a><span id="Reset_scenarios"></span><span id="reset_scenarios"></span><span id="RESET_SCENARIOS"></span>Zurücksetzen von Szenarien


Wenn das Gerät zurückgesetzt wird, gibt eine vorinstallierte app auf die Version, die in einem app-Paket auf dem Gerät gespeichert ist; Dies kann die Version sein, die auf dem Gerät geliefert. OS Updates, die das Telefon eingegangen sind auch nach dem Zurücksetzen auf dem Gerät aktiv. Dies bedeutet, dass die ursprüngliche vorinstallierte app möglicherweise mit neuere Versionen des Betriebssystems und neueren Versionen BSP ausgeführt werden muss. Wie Updates auf apps vorinstallierte vorbereitet werden, sollten diese Abhängigkeiten und damit zusammenhängende Interaktionen berücksichtigt werden. Weitere Informationen zu das Verhalten der OS Zurücksetzen finden Sie unter [das Gerät zurückzusetzen](../../manufacture/mobile/resetting-a-phone-during-manufacturing.md).

## <a name="span-idupdatestonativeservicesandserviceagentsspanspan-idupdatestonativeservicesandserviceagentsspanspan-idupdatestonativeservicesandserviceagentsspanupdates-to-native-services-and-service-agents"></a><span id="Updates_to_native_services_and_service_agents"></span><span id="updates_to_native_services_and_service_agents"></span><span id="UPDATES_TO_NATIVE_SERVICES_AND_SERVICE_AGENTS"></span>Updates für systemeigenen Diensten und Dienst-Agenten


OEMs können systemeigenen Diensten und Dienst-Agenten in das Betriebssystem Adresse Code Szenarien fortlaufend ausgeführt. Da systemeigenen Diensten und Dienst-Agenten in das Betriebssystem enthaltenen mithilfe zwei verschiedene Methoden, Updates erstellt und verwaltet unterschiedlich.

### <a name="span-idnativeservicesspanspan-idnativeservicesspanspan-idnativeservicesspannative-services"></a><span id="Native_services"></span><span id="native_services"></span><span id="NATIVE_SERVICES"></span>Systemeigenen Diensten

Systemeigene Diensten sind in das Betriebssystem enthalten, indem Sie verwandte Code zu einem Paket, das im Bild enthalten ist. Sie werden wie jedes andere Paket im Betriebssystem aktualisiert.

### <a name="span-idserviceagentsspanspan-idserviceagentsspanspan-idserviceagentsspanservice-agents"></a><span id="Service_agents"></span><span id="service_agents"></span><span id="SERVICE_AGENTS"></span>Dienst-Agenten

Mehrere Dienst-Agenten sind in einer einzigen vorinstallierte app enthalten. Wie bei allen vorinstallierte apps werden Updates mit den Speicher zugestellt. Jede-Agent-Anwendung kann mehrere Dienst-Agenten, die darin enthaltenen ausgeführt haben. Wenn keines der Dienst-Agenten aktualisiert werden muss, muss die app, die die Dienst-Agenten enthält aktualisiert werden. Dienst-Agenten Verhalten sich im Allgemeinen wie apps Update, zurücksetzen und Wiederherstellungsszenarien geladen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Update](index.md)

[Die Einstellungen für apps System und updates](system-settings-apps-and-updates.md)

 

 


