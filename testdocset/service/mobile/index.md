---
author: kpacquer
Description: To update your devices, you'll submit an update to Microsoft.
ms.assetid: 529f841c-abd2-4b33-93c6-509e3dfcbff7
MSHAttr: PreferredLib:/library/windows/hardware
title: Mobile update
ms.openlocfilehash: 4f7c688443f88801616586790a8a7684e9d13b2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-update"></a>Mobile update

##<a name="updating-a-device"></a>Aktualisieren eines Geräts
Um Ihre Geräte zu aktualisieren, werden Sie ein Update an Microsoft übermitteln. Mobilfunkbetreiber (MO) kann helfen Ihnen, die Updates zu testen. Wenn genehmigt, geht das Update auf den Update Produktionsserver, wobei können Kunden Telefone herunterladen und die Updates über ein Mobiltelefon oder eine Wi-Fi-Verbindung empfangen. Das Gerät mit Zustimmung Benutzer mit den meisten Update-Prozessen zu arbeiten im Hintergrund automatisch aktualisiert.

### <a name="span-idbeforeyoubeginspanspan-idbeforeyoubeginspanspan-idbeforeyoubeginspanbefore-you-begin"></a><span id="Before_you_begin"></span><span id="before_you_begin"></span><span id="BEFORE_YOU_BEGIN"></span>Bevor Sie beginnen


Führen Sie vor dem Senden von Updates, die folgenden Aufgaben aus:

1.  Registrieren Sie sich zum Übermitteln der Firmware Übermittlung und Aktualisieren von Anfragen an. Weitere Informationen finden Sie im Abschnitt "Melden Sie sich für Retail-Paket signieren und Update Übermittlungen" [Aufnahme](ingestion-client-for-windows-phone.md)-Client.

2.  Überprüfen Sie die Updateszenarien, die Sie im [Update-Szenarien](update-scenarios.md)liegen.

3.  Überprüfen Sie die Update-Anforderungen, die Sie in der [Aktualisierung von](update-requirements.md)liegen.

4.  Abrufen der Übermittlung erfolgreich signierte Firmware Ticket-IDs für die Firmware, der Geräte aus aktualisieren werden und der Firmware, der Geräte aktualisiert werden. Informationen dazu, wie Sie zum Ausführen dieser Aufgabe überprüfen Sie [Submit-Binärdateien Retail werden signiert](https://msdn.microsoft.com/library/windows/hardware/dn789223).

### <a name="span-idtypesofupdatesspanspan-idtypesofupdatesspanspan-idtypesofupdatesspantypes-of-updates"></a><span id="Types_of_updates"></span><span id="types_of_updates"></span><span id="TYPES_OF_UPDATES"></span>Typen von updates


-   **Microsoft-Updates**. Diese Updates Ziel ein Microsoft-Code in das Bild, einschließlich der Microsoft-Pakete in der ESP (EFI-Systempartition) und die Main OS Partitionen und Microsoft-Pakete für das System Ladeprogramme.

-   **OEM-Updates**. Diese werden auch als Updates Board Support Paket (BSP) bezeichnet. OEMs können Pakete für ihre Komponenten reserviert Regionen und die Partitionen, denen Verwaltungsberichte-Pakete für, einschließlich der Main OS und MMOS Partitionen entwickeln. Die Benutzerdaten und SD-Karten können nicht aktualisiert werden. Alle Benutzerdaten und Einstellungen müssen beibehalten werden, wenn diese Updates installiert sind.

Diese Arten von Updates können nur einzeln gesendet werden.

 

##<a name="refurbishing-a-device"></a>Prüfen ein Gerät
Verwenden Sie in den Themen in diesem Abschnitt erfahren Sie mehr über ein mobiles Gerät mit Windows 10 Mobile prüfen.


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[Zurücksetzen eines mobilen Geräts](resetting-the-phone.md)</p></td>
<td align="left"><p>Zurücksetzen des Geräts werden eine Reihe von wichtigen Szenarien ausgeräumt:</p>
<ul>
<li>Ein Benutzer kann möglicherweise Zurücksetzen eines Geräts, um es in einem anderen Besitzer zu übertragen.</li>
<li>Das Gerät verlorenen oder gestohlenen wurde und der Besitzer möchte Remote Zurücksetzen des Geräts</li>
<li>Das Gerät gehört zu einer Organisation, und die Organisation möchte das Gerät Remote zurückgesetzt. Beispielsweise wenn ein Mitarbeiter das Unternehmen verlässt.</li>
<li>Das Gerät hat nicht funktionierenden und möchte, dass des Benutzers das Gerät zurückzusetzen.</li>
<li>OEM Factory Anwendungstests abgeschlossen sind und möchte das Gerät (optional vorinstallierte Zuordnungsdaten beibehalten) zurückgesetzt.</li>
</ul></td>
</tr>
</tbody>
</table>

 

 


 





