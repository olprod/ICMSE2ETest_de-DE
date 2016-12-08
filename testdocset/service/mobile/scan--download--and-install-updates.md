---
author: kpacquer
Description: "Geräte können automatisch Updates suchen, herunterladen und der Benutzer aufgefordert, den sie zu einem Zeitpunkt installieren, die für sie geeignet ist. Sie können auch Updates identifizieren, die zu wichtig ist, übergeben, indem Sie sind."
ms.assetid: 5ed8aad7-7aa9-4c81-844c-2e529d75f0b5
MSHAttr: PreferredLib:/library/windows/hardware
title: Scannen, herunterladen und Installieren von updates
ms.openlocfilehash: 7873cb473a03242e6b36d065c644c7526aa9d416
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="scan-download-and-install-updates"></a>Scannen, herunterladen und Installieren von updates


Geräte können automatisch Updates suchen, herunterladen und der Benutzer aufgefordert, den sie zu einem Zeitpunkt installieren, die für sie die richtige Wahl ist. Sie können auch Updates identifizieren, die für die Übergabe von zu wichtig sind.

## <a name="span-idnormalstronglysuggestedandmandatoryupdatesspanspan-idnormalstronglysuggestedandmandatoryupdatesspanspan-idnormalstronglysuggestedandmandatoryupdatesspannormal-strongly-suggested-and-mandatory-updates"></a><span id="Normal__strongly_suggested__and_mandatory_updates"></span><span id="normal__strongly_suggested__and_mandatory_updates"></span><span id="NORMAL__STRONGLY_SUGGESTED__AND_MANDATORY_UPDATES"></span>Normalansicht, ausdrücklich empfohlen, und verbindliche updates


Einige Benutzer möchten nicht gestört von Updates zu werden. Wenn sie nicht wissen, wenn sie wichtig sind, können sie diese auf unbestimmte Zeit verschieben.

Um wichtige Updates zu identifizieren, kennzeichnen Sie sie als empfohlene Updates (SSU) oder verbindliche Updates durch Öffnen einer Team Foundation Server (TFS) updateanforderung und markieren diese Notes.

Wir können dies auf dem Windows Update-Server einrichten.

## <a name="span-iddetectingupdatesspanspan-iddetectingupdatesspanspan-iddetectingupdatesspandetecting-updates"></a><span id="Detecting_updates"></span><span id="detecting_updates"></span><span id="DETECTING_UPDATES"></span>Ermitteln von updates


Das Gerät wird standardmäßig für Updates regelmäßig überprüft. Dieser Prozess wird im Hintergrund und die Verwendung des Geräts nicht unterbrochen.

Die automatische Überprüfung tritt nach dem folgenden Zeitplan:

-   Alle 6.2 Tage Gründe für eine Verbindung mit Mobilfunk. Dadurch wird oben auf einen Tag zuvor ausgelöst, wenn eine Wi-Fi-Verbindung verfügbar ist.

-   Täglich, wenn das Gerät ist eingeschaltet und der Benutzer das Gerät nicht aktiv verwendet wird.

-   Jedes Mal, wenn das Gerät neu gestartet wird, beginnt die Überprüfung 60 Minuten nach dem Start abgeschlossen ist.

Die automatische Überprüfung verwendet eine Wi-Fi oder ein Mobiltelefon Verbindung:

1.  Für die erste Überprüfung scannt das Gerät, wenn eine Wi-Fi oder ein Mobiltelefon Verbindung verfügbar ist.

2.  Für die erste Überprüfung nach einer erfolgreichen Aktualisierung scannt das Gerät, wenn eine Wi-Fi oder ein Mobiltelefon Verbindung verfügbar ist.

3.  Wenn seit früheren Überprüfung 6.2 Tage ist, wird das Telefon nur überprüft, wenn eine Wi-Fi-Verbindung verfügbar ist.

4.  Wenn Zeit seit früheren Überprüfung 6.2 Tage ist oder mehr, das Telefon überprüft wird, wenn eine Wi-Fi oder ein Mobiltelefon Verbindung verfügbar ist.

5.  Wenn eine Aktualisierung abgeschlossen ist, das Gerät wird neu gestartet und führt ein anderes sofortigen Scan für Updates.

Benutzer können aktivieren oder deaktivieren Sie automatische Überprüfung im Menü **Telefon Update** : **wann Aktualisierungen für mein Telefon zur Verfügung stehen?**. Standardmäßig ist diese Einstellung nicht sichtbar, und die Standardeinstellung aktiviert ist. OEMs können ändern, ob die Einstellung sichtbar ist, und ändern die Standardeinstellung. Benutzer können das Telefon-Menü aktualisieren manuell auf Updates überprüfen und Überwachen des Status von Updates.

## <a name="span-iddownloadingupdatesspanspan-iddownloadingupdatesspanspan-iddownloadingupdatesspandownloading-updates"></a><span id="Downloading_updates"></span><span id="downloading_updates"></span><span id="DOWNLOADING_UPDATES"></span>Herunterladen von updates


Standardmäßig Wenn das Gerät eine Wi-Fi-Verbindung verwenden, ist heruntergeladen das Update automatisch. Wenn automatische Herunterladen ist nicht aktiviert oder ist das Gerät für eine Mobilfunk Verbindung, klicken Sie dann das Gerät kann der Benutzer aufgefordert, laden Sie das Update:

-   Für mobilverbindungen, wenn das Gerät prüft, ob die Größe des Updates ist kleiner als das Größenlimit Update. Die Standardgröße beträgt 100 MB konfigurierbar durch den Monat

-   Wenn das Gerät unter der Grenzwert ist, werden sie mit der Option, laden Sie das Update über ihre Mobiltelefone Verbindung aufgefordert.

    Wenn der Benutzer entscheidet, laden Sie das Update über ihre Mobiltelefone Verbindung, kann der Benutzer für diese Daten je nach einen Plan für die Daten mit ihren Monat belastet Die MO kann Updates zur kostenfrei für den Benutzer konfigurieren. Finden Sie weitere Informationen finden Sie unter [zero-rating (kostenlos) Downloads für Geräteupdates zu aktivieren](enable-zero-rating--no-charge--downloads-for-device-updates.md).

Wenn sie den Download zu verschieben, werden sie später aufgefordert:

-   **Normale Updates**: alle 27 Stunden aufgefordert.

-   **Updates ausdrücklich empfohlen**: alle 27 Stunden für 3 Wiederholungsversuche aufgefordert. Danach werden alle vier Stunden aufgefordert.

-   **Verbindliche Updates**: aufgefordert, alle vier Stunden.

Ist es Fehlerberichte während des Downloads (beispielsweise nicht genügend Speicherplatz), behält das Update wiederholen. Schwerwiegende Fehler die Update-Phase wechselt zurück zum Suchen nach Updates und wird neu gestartet.

Benutzer können aktivieren oder Deaktivieren des automatischen Downloads im Menü **Telefon aktualisieren** : **automatisch heruntergeladen Updates, wenn die Einstellungen für meine Daten zulassen**. Die Standardeinstellung ist aktiviert. Den Standardwert können nicht OEMs geändert werden.

Nachdem das Update die Aktualisierung erfolgreich heruntergeladen wurde, wird das Gerät überprüft es und Stufen es für die Installation.

## <a name="span-iddealingwithmultipleupdatesatoncespanspan-iddealingwithmultipleupdatesatoncespanspan-iddealingwithmultipleupdatesatoncespandealing-with-multiple-updates-at-once"></a><span id="Dealing_with_multiple_updates_at_once"></span><span id="dealing_with_multiple_updates_at_once"></span><span id="DEALING_WITH_MULTIPLE_UPDATES_AT_ONCE"></span>Umgang mit mehreren Updates gleichzeitig


Alle vorherigen Updates, die ein vollständigen (hard Stop) Neustart des Geräts erforderlich ist, behandelt zunächst mit diesen Updates.

Wenn es mehr als eine aktualisieren offen, und wenn diese Updates stark werden Updates vorgeschlagen, und wenn keines dieser Updates einen Neustart des Computers erforderlich, wird sie alle als behandelt eine große Update, damit der Benutzer sie alle gleichzeitig akzeptieren kann.

## <a name="span-idinstallinganupdatespanspan-idinstallinganupdatespanspan-idinstallinganupdatespaninstalling-an-update"></a><span id="Installing_an_update"></span><span id="installing_an_update"></span><span id="INSTALLING_AN_UPDATE"></span>Installieren ein update


1.  Nachdem das Update heruntergeladen und bereitgestellt wird, überprüft das Gerät, um festzustellen, ob es sich um eine gute Zeit zum Installieren des Updates ist. Nicht-SD-Karte Updates muss die Batterie mehr als 30 % aufgeladen wird. SD-Updates muss die Batterie mehr als 60 % aufgeladen wird.
2.  Im nächsten Schritt fordert den Benutzer, sollten Sie jetzt das Update installiert ist. Nachfolgend finden sie sehen:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Normale updates</p></td>
    <td align="left"><p>Empfohlene updates</p></td>
    <td align="left"><p>Verbindliche updates</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Sie schreiben die Benachrichtigung beim Senden des Updates an. Kleine Updates empfehlen wir eine einfache, fördern Beschreibung, wie folgt:</p>
    <p><strong>&quot;Dieses Update kann das Gerät besser helfen.&quot;</strong></p></td>
    <td align="left"><img src="images/oem-update-notification-criticalupdate.png" alt="Screenshot of a notification: &quot;Install critical update: A critical update is available and you should install it as soon as possible.&quot;" /></td>
    <td align="left"><img src="images/oem-update-notification-mandatoryupdate.png" alt="Screenshot of a notification: &quot;Install critical update: A critical update is ready to install. Your phone will update automatically if you don&#39;t install the update by tomorrow at 3:00 a.m.&quot;" /></td>
    </tr>
    </tbody>
    </table>

     

    Wenn während der Installation ein Fehler aufgetreten ist, wird die Update-Phase wechselt zurück zum Suchen nach Updates und startet erneut.

3.  Wenn der Benutzer beschließt, die Updates zu installieren, wird das Gerät neu gestartet wird, in das Update Betriebssystem und schließt den Installationsprozess.

4.  Während der Installation werden sich drehenden Fanggeräte an, dass Fortschritt angezeigt, durch die Update-Betriebssystem.

5.  Manifestdateien, die Informationen über das installierte Betriebssystem enthalten, werden aktualisiert, um den Inhalt der Updatepakete wiederzugeben. Dies ermöglicht die Verwendung beim Zurücksetzen des Geräts. Weitere Informationen zum Zurücksetzen des Geräts finden Sie unter [Updates und das Telefon zurücksetzen](updates-and-resetting-the-phone.md).

6.  Nachdem das Update OS in das Hauptfenster Betriebssystem neu gestartet wird, die Daten des Benutzers werden migriert, und eine Statusanzeige wird angezeigt. Nach die Migration abgeschlossen ist, wird eine Benachrichtigung an, die angibt, ob die Aktualisierung erfolgreich war oder nicht angezeigt.

![Diagramm des Aktualisierungsvorgangs](images/oem-update-overview.png)

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


-   Wenn ein Fehler auftritt, während ein Update staging, planen, das Gerät wird nicht installieren.

-   Wenn ein Fehler auftritt, während ein Betriebssystemupdate (Benutzer dies dreht Zahnräder) und das Update nicht erfolgreich ist, wird das Gerät eine Nachricht "Vollständige Aktualisierung" nicht angezeigt. Das Gerät wieder für das Hauptfenster Betriebssystem startet und startet den Vorgang erneut, beginnend mit Suchen nach Updates.

-   Wenn eine Installation geplant ist, überspringen die Installation und plant für den nächsten Tag in den folgenden Situationen neu:

    -   Der Benutzer ist das Gerät verwenden 5 Minuten vor dem Installieren von der bevorzugte Zeit.

    -   Es gibt ein ein- oder Ausgehender Anruf in Aktion zum Zeitpunkt der bevorzugten Install ein.

    -   Der Benutzer hat keine Benachrichtigung erhalten, die ein Update installiert werden kann. Wir senden Sie diese Erinnerung 8 Stunden hingegen und Vorgang wird wiederholt, bis eine Stunde vor dem Installieren von der bevorzugte Zeit beibehalten. Der Benutzer erhält nur einmal die Benachrichtigung an. Sie können dieser Benachrichtigung möglicherweise nicht angezeigt, wenn das Gerät deaktiviert ist.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Senden Sie ein update](submit-an-update.md)

[Ein Update genehmigen](approve-an-update.md)

 

 






