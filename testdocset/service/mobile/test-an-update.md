---
author: kpacquer
Description: Testen Sie ein update
ms.assetid: cdeecf1c-a239-4d7a-87b8-a366e8e26f06
MSHAttr: PreferredLib:/library/windows/hardware
title: Testen Sie ein update
ms.openlocfilehash: c5fb1b50fa97cd9a196a21044305a1cce6404945
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="test-an-update"></a>Testen Sie ein update


Testen der Aktualisierung sollte bei der Entwicklung Ihrer ersten Bilds beginnen.  Testen Sie, dass der Treiber geladen apps und andere Inhalte kann über den gesamten Prozess aktualisiert werden.

Während der Phase beim Test Bilder erstellen, sollten Sie testen der lokalen des Updates, führen Sie die Kompatibilitätstests vor und nach der Aktualisierung und für die gleichen Ergebnisse suchen.  Dies ist eine beim können einfacher testen eine ganze Bandbreite von Telefonfunktionen durch Automatisierung und Zeit Update Probleme früh erkennen.  Führen Sie nicht warten Sie, bis die Fertigung und Einzelhandel Gerät testen fast ausgeschöpft ist.

Über die Air (OTA) können Updates nur auf Retail-Gerät getestet werden die schwieriger zu realisieren aufgrund der höhere Sicherheit auf einem Gerät Einzelhandel ist.  Aus diesem Grund ist es wichtig, dass Sie intensive Funktionstests auf die Bilder Test ausführen, und konzentrieren Sie sich auf Telefonen Verkaufsversion, um sicherzustellen, dass das OTA-Update durch Befolgen der Anleitung in das Netzwerk Testen der Abschnitt Updates erfolgreich angezeigt werden kann.

Die Qualität eines OEM-Updates müssen OEMs entweder vollständig testen Sie das Update vor dem Absenden an Microsoft. Als Mindestanforderung gehen OEM.

-   Stellen Sie sicher, dass die Pakete, die aktualisiert werden alle Zertifikate beim Testen einer Einzelhandel-Abbild nicht enthalten.

-   Stellen Sie sicher, dass die Revisionsnummer Firmware ordnungsgemäß geändert haben, navigieren Sie zur **Einstellungen** &gt; **System** &gt; **zu** auf dem Gerät. Weitere Informationen zu Versionsinformationen finden Sie unter [Anforderungen zu aktualisieren](update-requirements.md).

-   Stellen Sie sicher, dass das Updatepaket OEM erwartungsgemäß funktioniert.

-   Testen Sie das Update auf Gerät, die Benutzerdaten, um sicherzustellen, dass ihre Daten beibehalten werden. Es folgen einige Beispiele für Tests, die Sie ausführen können, um sicherzustellen, dass Benutzerdaten nach einer Aktualisierung nicht geändert wurde.

    -   Einstellungen für alle Benutzer sind identisch.

    -   Start-Bildschirm Kacheln haben die gleiche Position und Größe.

    -   Benutzerdaten ist weiterhin auf dem Gerät (Bilder, apps, SMS-Verlauf, Musikdateien, Videodateien usw.)

## <a name="span-idlocaltestingofupdatesspanspan-idlocaltestingofupdatesspanspan-idlocaltestingofupdatesspanlocal-testing-of-updates"></a><span id="Local_testing_of_updates"></span><span id="local_testing_of_updates"></span><span id="LOCAL_TESTING_OF_UPDATES"></span>Das lokale Testen der updates


Bevor Sie das Update übermitteln, testen Sie es lokal. Führen Sie auf einem PC, die Sie während des Tests verwenden möchten die folgenden Schritte aus:

1.  Stellen Sie die aktualisierte Test-Pakete für das Gerät. Sie können das Update Updatepakete erhalten, die bereits für das Testen mit dem [Cmdlet Get-SignedFirmwareSubmission](get-signedfirmwaresubmission-cmdlet.md)genehmigt wurde.

2.  Stellen Sie sicher, dass die Aktualisierung erfolgreich war und dass es keine unbeabsichtigten Effekte auf das Verhalten des Geräts hatte.

## <a name="span-idnetworktestingofupdatesspanspan-idnetworktestingofupdatesspanspan-idnetworktestingofupdatesspannetwork-testing-of-updates"></a><span id="Network_testing_of_updates"></span><span id="network_testing_of_updates"></span><span id="NETWORK_TESTING_OF_UPDATES"></span>Netzwerk Testen von updates


Zum Vorbereiten der ein Update von der Microsoft Update Testserver erhalten, führen Sie die folgenden Schritte aus.

1.  Ein Paket von Microsoft bereitstellen, nachdem Sie sich zum Senden von Anforderungen für die Übermittlung Firmware und Update angemeldet haben Test Update zu erhalten.

2.  Wenden Sie das Bereitstellung Paket an das Gerät mithilfe von IUTool.exe an.

3.  Stellen Sie eine Verbindung mit einem Mobiltelefon oder Wi-Fi-Netzwerk mit dem Gerät, und fügen Sie das Gerät an einen Ladegerät.

    **Hinweis**  
    Es wird empfohlen, verwenden Wi-Fi, laden Sie das Update, damit Sie nicht in Einschränkungen mit Ihrem Mobilfunkbetreiber ausführen beim Testen. Mobilfunkbetreiber können Update herunterladen größenbeschränkungen für Nachrichten angeben, wenn Sie ihre mobilfunknetzverbindung verwenden.

     

4.  Initiieren des Aktualisierungsvorgangs über **Einstellungen** &gt; **Update und Recovery** &gt; **Telefon zu aktualisieren**.

5.  Wenn die Updates angezeigt werden, befolgen Sie, und schließen Sie den Aktualisierungsvorgang.

6.  Stellen Sie sicher, dass die Aktualisierung erfolgreich war und dass es keine unbeabsichtigten Effekte auf das Verhalten des Geräts hatte.

## <a name="span-idtestcasesforfeaturesafteranupdatespanspan-idtestcasesforfeaturesafteranupdatespanspan-idtestcasesforfeaturesafteranupdatespantest-cases-for-features-after-an-update"></a><span id="Test_cases_for_features_after_an_update"></span><span id="test_cases_for_features_after_an_update"></span><span id="TEST_CASES_FOR_FEATURES_AFTER_AN_UPDATE"></span>Testfälle für Features nach einer Aktualisierung


### <a name="wi-fi"></a>Wi-Fi

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Netzwerk &amp; drahtlosen</strong> &gt; <strong>Wi-Fi</strong>.</p></li>
<li><p>Ein sicheres Drahtlosnetzwerk auswählen. Melden Sie sich mit den entsprechenden Anmeldeinformationen.</p></li>
<li><p>Stellen Sie sicher, dass der Status mit dem Netzwerk als "Verbunden." angezeigt wird</p></li>
<li><p>Sicherstellen Sie, dass das <strong>Wi-Fi</strong> -Symbol am oberen Rand des Geräts wie gewünscht angezeigt wird.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Das Symbol sollte flash, während das Gerät verbindet, und bleiben einfarbige, nachdem das Telefon angeschlossen ist. Das Symbol verschwindet wenige Sekunden, nach dem das Gerät verbunden ist. Das Symbol kann erneut durch Tippen auf der Mitte der oberen Bildschirmrand angezeigt werden.</p>
</div>
<div>
 
</div></li>
<li><p>Tippen Sie auf <strong>Start</strong>, und tippen Sie dann auf <strong>Internet Explorer</strong>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn im Browser zum ersten Mal gestartet wird, wird ein Dialogfeld pop-up aufgefordert werden, "die empfohlenen Einstellungen verwenden?" Tippen Sie auf die Schaltfläche <strong>empfohlen</strong> .</p>
</div>
<div>
 
</div></li>
<li><p>Tippen Sie auf die Adressleiste, und geben Sie einen Website-URL. Tippen Sie auf die EINGABETASTE auf der virtuellen Tastatur fahren Sie mit der Website.</p></li>
<li><p>Stellen Sie sicher, dass die Seite geladen wird.</p></li>
<li><p>Tippen Sie auf der Startseite wieder <strong>Starten</strong> , und tippen Sie dann in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Netzwerk &amp; drahtlosen</strong> &gt; <strong>Wi-Fi</strong>.</p></li>
<li><p>Wählen Sie aus, und ein nicht gesichertes drahtlosen Netzwerk verbinden.</p></li>
<li><p>Drücken Sie auf der Startseite zurückzugeben, und tippen Sie dann auf <strong>Internet Explorer</strong> <strong>zu starten</strong> .</p></li>
<li><p>Tippen Sie auf die Adressleiste, und geben Sie eine andere Website-URL.</p></li>
<li><p>Stellen Sie sicher, dass die Seite ordnungsgemäß geladen wird.</p></li>
<li><p>Tippen Sie auf <strong>Start</strong> , auf der Startseite und in der Liste App zurückzugeben, tippen Sie auf <strong>Einstellungen</strong> &gt; <strong>Netzwerk &amp; drahtlosen</strong> &gt; <strong>Wi-Fi</strong> &gt; <strong>Verwalten</strong>.</p></li>
<li><p>Stellen Sie sicher, dass beide die Netzwerknamen in der Liste der bekannten Netzwerke vorhanden sind.</p></li>
<li><p>Tippen Sie und halten Sie die <strong>Open-Netzwerk</strong>.</p></li>
<li><p>Tippen Sie auf <strong>Löschen</strong>.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät mit dem gesicherten Netzwerk automatisch aus Schritt2 eine Verbindung herstellt.</p></li>
</ol>

### <a name="maps"></a>Karten

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Maps</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Speicherort Aufforderung angezeigt, wenn wird Karten zum ersten Mal gestartet wird.</p></li>
<li><p>Tippen Sie auf <strong>Zulassen</strong> , um zur Förderung des Bekanntheitsgrads Standort zu aktivieren. Die app wird die aktuelle Position geladen.</p></li>
<li><p>Wenn Karten vollständig geladen wurde, überprüfen Sie Folgendes.</p>
<ol>
<li><p>Die Zuordnung wird vergrößert, sodass Wege im lokalen Bereich sichtbar sind.</p></li>
<li><p>Das <strong>mir</strong> -Symbol (Diamond oder Kreis geformten) wird an der Stelle Telefon platziert.</p></li>
<li><p>Der Kreis in der Mitte des Symbols <strong>mich</strong> sollte die Farbe des Designs Telefon entsprechen.</p></li>
</ol></li>
<li><p>Stellen Sie sicher, dass die Maps-app-Leiste am unteren mit den folgenden vier Schaltflächen angezeigt wird.</p>
<ol>
<li><p><strong>Scout</strong> (die Schaltfläche ist einer Reihe von Gebäude).</p></li>
<li><p><strong>Erfahren Sie, wie</strong> (die Schaltfläche ist ein Pfeil).</p></li>
<li><p><strong>Me</strong> (die Schaltfläche ist ein Kreis in einem Kreis).</p></li>
<li><p><strong>Suche</strong> (die Schaltfläche ist ein Vergrößerungsglas).</p></li>
</ol>
<div class="alert">
<strong>Hinweis</strong>  
<p>Scout ist für einige der Bilder nicht verfügbar.</p>
</div>
<div>
 
</div></li>
<li><p>Schwenken Weg von der Pfad für die Zuordnung, und tippen Sie dann auf die Schaltfläche " <strong>Me</strong> " auf. Stellen Sie sicher, dass die Zuordnung der Standort des tischtelefons mit <strong>mir</strong> -Symbol in der Mitte zurückgibt.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Scout</strong> . Überprüfen, ob lokale Scout innerhalb weniger Sekunden geladen wird und das Pivot <strong>Essen + Trinken</strong> wird angezeigt, mit einer Liste von Unternehmen, die Speisen und Getränke anbieten.</p>
<ol>
<li><p>Stellen Sie sicher, dass jedes Element in der Pivot <strong>Essen + Trinken</strong> die Firma und Adresse enthält.</p></li>
<li><p>Sicherstellen Sie, dass mit zwei anderen Pivot-Elemente, <strong>finden Sie unter + führen</strong> und <strong>Shop</strong>Scout geladen wird.</p></li>
</ol></li>
<li><p>Kehren Sie zur Anwendung zuordnen, und tippen Sie dann auf die Schaltfläche <strong>erfahren Sie, wie</strong> .</p>
<ol>
<li><p>Lassen Sie das Feld Start standardmäßig auf "Mein Standort".</p></li>
<li><p>Tippen Sie auf das Feld Ende, und geben Sie einen Endpunkt (Seattle). Drücken Sie die EINGABETASTE auf der Tastatur zum Abrufen der erfahren Sie, wie ein.</p></li>
<li><p>Stellen Sie sicher, dass die schrittweisen Anweisungen in Form einer Liste mit einer Zuordnung Stripe oben angezeigt werden.</p></li>
<li><p>Die Zuordnung sollte einen "A" am Anfangspunkt angezeigt werden.</p></li>
<li><p>Blättern Sie durch die Anweisungen. Stellen Sie sicher, dass die Zuordnung aktualisiert, um jede neue Richtung anzuzeigen.</p></li>
<li><p>Führen Sie einen Bildlauf bis zum Ende. Stellen Sie sicher, dass die Karte "B" am Endpunkt zeigt.</p></li>
</ol></li>
<li><p>Kehren Sie zur Anwendung zuordnen. Tippen Sie auf die Schaltfläche <strong>Suchen</strong> .</p>
<ol>
<li><p>Geben Sie den Suchbegriff "Restaurants in Seattle". Tippen Sie auf die EINGABETASTE auf der virtuellen Tastatur, um die Suche auszuführen.</p></li>
<li><p>Stellen Sie sicher, dass bis zu 10 Search Ergebnisse als Pins auf der Karte angezeigt werden, und die erste Pin wird erweitert, sodass Sie deren Namen sehen können. (Der Name kann am rechten Rand abgeschnitten werden).</p></li>
</ol></li>
</ol>

### <a name="lock-screen-testing"></a>Testen der Bildschirm sperren

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf &gt; <strong>Einstellungen</strong> &gt; <strong>Personalisierung</strong> &gt; <strong>Sperren des Bildschirms</strong>.</p></li>
<li><p>Legen Sie das Feld "Bildschirm läuft nach" auf "30 Sekunden".</p></li>
<li><p>Lassen Sie das Gerät im Leerlauf für 30 Sekunden. Nach der Bildschirm zu dem Standbymodus, drücken Sie und führen Sie eine streifbewegung dem Bildschirm wechselt, um sicherzustellen, dass das Programm reagiert nicht, und dass ist das Gerät gesperrt.</p></li>
<li><p>Drücken Sie die zum Entsperren des Geräts. Eine streifbewegung, um den Bildschirm freizugeben.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät erfolgreich aufgehoben.</p></li>
<li><p>Aktivieren Sie das Kennwort auf dem Bildschirm Sperre auf "Aktiviert".</p></li>
<li><p>Erstellen Sie ein Kennwort ein.</p></li>
<li><p>Lassen Sie das Telefon im Leerlauf für 30 Sekunden. Nach der Bildschirm wechselt in den Energiesparmodus, ist drücken Sie und führen Sie eine streifbewegung, dem Bildschirm, um zu überprüfen, dass keine passiert, und das Gerät gesperrt.</p></li>
<li><p>Drücken Sie die zum Entsperren des Geräts. Eine streifbewegung, um den Bildschirm freizugeben. Stellen Sie sicher, dass Sie aufgefordert werden, geben Sie das Kennwort angezeigt wird.</p></li>
<li><p>Geben Sie ein falsches Kennwort. Stellen Sie sicher, dass des Geräts nicht entsperren und das korrekte Kennwort eingegeben werden muss.</p></li>
<li><p>Geben Sie das korrekte Kennwort ein. Stellen Sie sicher, dass das Gerät erfolgreich entsperrt.</p></li>
</ol>

### <a name="capturing-photos-with-the-camera"></a>Erfassen von Fotos mit der Kamera

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Sperren Sie das Gerät, und lassen sie das Leerlauf, um es in den Energiesparmodus versetzt werden soll.</p></li>
<li><p>Drücken Sie und halten Sie die Kamera Hardware, um die Kamera zu starten. Vergewissern Sie sich, dass die Kamera entweder die Standard-Kamera-app oder die Kamera app startet. Tippen Sie auf <strong>Abbrechen</strong> , in der &quot;ermöglichen die Webcam an Ihren Standort verwenden&quot; Bildschirm.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn das Telefon nicht mit eine Kamera-Taste verfügt, starten Sie die Kamera-Anwendung direkt.</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Aufforderung "Ermöglichen... Speicherort" werden die vorherigen Einstellungen beherrschen und möglicherweise nicht angezeigt, wenn die Kamera zuletzt verwendet wurde.</p>
</div>
<div>
 
</div></li>
<li><p>Stellen Sie sicher, dass standardmäßig die Kamera, um festgelegt ist &quot;Bild&quot; Modus.</p></li>
<li><p>Drücken Sie mit den Fingern auf dem Bildschirm Kamera an-und Abmelden, und stellen Sie sicher, dass der Kamera-Bildschirm an-und Abmelden Zooms.</p></li>
<li><p>Wenn das Gerät einen Kamera Hardware-Schlüssel verfügt, halten sie halb und stellen Sie sicher, dass ein rechteckiges Feld, auf dem Bildschirm für das Feature automatisch den Fokus hat angezeigt wird. Sie außerdem sicher, dass ein akustisches nach Abschluss der Kamera Fokus hören.</p></li>
<li><p>Tippen Sie auf dem Bildschirm auf oder drücken Sie die Kamera-Taste, und stellen Sie sicher, dass ein akustisches hören ist nach dem Erstellen eines Bilds.</p></li>
<li><p>Überprüfen Sie das Bild, das Sie soeben ausgeführten und prüfen Sie die folgenden Links führen Sie eine streifbewegung.</p>
<ol>
<li><p>Farbe Fehler.</p></li>
<li><p>Staub unter die Kamera-Fenster. Sie sehen dies, wenn in das Foto dunkleren Bereiche vorhanden sind.</p></li>
<li><p>Verschwommene Bilder</p></li>
<li><p>Ein Bild übermäßig hell oder Matt. Dies impliziert, dass etwas mit der Kamera Sensor falsch ist.</p></li>
</ol></li>
</ol>

### <a name="recording-videos-with-the-camera"></a>Videos zur Aufzeichnung im Rahmen der Kamera

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Sperren Sie das Gerät, und lassen sie das Leerlauf, um es in den Energiesparmodus versetzt werden soll.</p></li>
<li><p>Drücken Sie und halten Sie die Kamera Hardware-Taste, um die Kamera zu starten, oder starten Sie die Anwendung direkt aus der Liste Apps. Tippen Sie auf <strong>Abbrechen</strong> , in der &quot;ermöglichen die Kamera Verwendung Ihres Standorts für Ihre&quot; Bildschirm.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn das Gerät nicht über eine Kamera-Taste verfügt, starten Sie direkt die Kamera-app.</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Aufforderung "Ermöglichen... Speicherort" wird die vorherige Einstellungen erinnern und möglicherweise nicht angezeigt, wenn die Kamera zuletzt verwendet wurde.</p>
</div>
<div>
 
</div></li>
<li><p>Ändern Sie in Videoaufnahme-Modus.</p></li>
<li><p>Drücken Sie mit dem Finger auf dem Bildschirm an-und Abmelden und überprüfen Sie, ob der Kamera Bildschirm an-und Abmelden Zooms.</p></li>
<li><p>Weist das Gerät eine Kamera-Taste, drücken sie ein Video Aufzeichnung starten.</p></li>
<li><p>Stellen Sie sicher, dass eine Warnung mit der Beep und den Indikator für die Aufzeichnung startet vorhanden ist.</p></li>
<li><p>Wenn das Gerät eine Kamera-Taste verfügt, drücken sie erneut auf Aufzeichnung beenden nach 15 Sekunden video.</p></li>
<li><p>Führen Sie die Links auf dem Bildschirm Kamera ein, und drücken Sie die Videoaufnahme <strong>wiedergegeben werden sollen</strong> .</p></li>
<li><p>Überprüfen Sie das Video wird ordnungsgemäß erfasst und 15 Sekunden lang abgespielt.</p></li>
</ol>

### <a name="front-facing-camera"></a>Front-internetbasierte Kamera

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Sperren Sie das Gerät, und lassen sie das Leerlauf, um das Telefon in den Energiesparmodus versetzt werden soll.</p></li>
<li><p>Drücken Sie und halten Sie die Kamera Hardware, um die Kamera zu starten. Tippen Sie auf <strong>Abbrechen</strong> , in der &quot;ermöglichen die Webcam an Ihren Standort verwenden&quot; Bildschirm.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn das Gerät nicht über eine Kamera-Taste verfügt, starten Sie direkt die Kamera-app.</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Aufforderung "Ermöglichen... Speicherort" werden die vorherigen Einstellungen beherrschen und möglicherweise nicht angezeigt, wenn die Kamera zuletzt verwendet wurde.</p>
</div>
<div>
 
</div></li>
<li><p>Sicherstellen, dass standardmäßig die Kamera festgelegt werden sollte &quot;Bild&quot; Modus mit der Kamera hinten gerichteten.</p></li>
<li><p>Tippen Sie auf der app-Leiste auf das Symbol <strong>Nach außen gerichtete</strong></p></li>
<li><p>Stellen Sie sicher, dass das Symbol nach außen gerichtete <strong>Kamera</strong> jetzt hervorgehoben wird.</p></li>
<li><p>Drücken Sie mit den Fingern auf dem Bildschirm Kamera an-und Abmelden, und stellen Sie sicher, dass der Kamera Bildschirm an-und Abmelden Zooms.</p></li>
<li><p>Drücken Sie Kamera Hardware ganz nach unten, oder tippen Sie auf dem Bildschirm, um ein Bild ausgeführt werden, wenn das Gerät eine Taste besitzt.</p></li>
<li><p>Stellen Sie sicher, dass ein akustisches hören nach Aufnahme des Bildes.</p></li>
<li><p>Führen Sie eine streifbewegung von überprüfen Sie das Bild, das Sie soeben ausgeführten und prüfen Sie die folgenden Links.</p>
<ol>
<li><p>Farbe Fehler.</p></li>
<li><p>Staub unter der Kamera-Fenster. Sie sehen dies, wenn in das Foto dunkleren Bereiche vorhanden sind.</p></li>
<li><p>Verschwommene Bilder.</p></li>
<li><p>Ein Bild übermäßig hell oder Matt. Dies impliziert, dass etwas mit der Kamera Sensor falsch ist.</p></li>
</ol></li>
</ol>

### <a name="calling-with-a-bluetooth-device"></a>Durch den Aufruf eines Bluetooth-Geräts

Voraussetzungen: 

<ul>
<li><p>Bluetooth-Geräts zum Herstellen einer Verbindung des Testgeräts</p></li>
<li><p>Zweite Telefon die Anruf-Funktionalität zu testen.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Geräte</strong> &gt; <strong>Bluetooth</strong>, Bluetooth auf aktivieren.</p></li>
<li><p>Verbinden Wert-Paar eines Bluetooth-Geräts mit dem Testgerät</p></li>
<li><p>Rufen Sie das Testgerät</p></li>
<li><p>Stellen Sie sicher, dass der Anruf auf dem Testgerät mit angezeigt wird ein auf dem Bildschirm beachten.</p></li>
<li><p>Stellen Sie sicher, dass der Anruf Klingelton über Bluetooth-Geräts gehört, der mit dem Testgerät verbunden ist</p></li>
<li><p>Nehmen Sie den Anruf auf dem Testgerät mithilfe des verbundenen Bluetooth-Geräts.</p></li>
<li><p>Stellen Sie sicher, das Testgerät über Bluetooth-Geräts Audiosignale vom zweiten Gerät gehört werden kann.</p></li>
<li><p>Vergewissern Sie sich, dass auf dem zweiten Gerät Audiosignale vom das Testgerät über Bluetooth-Geräts hören ist.</p></li>
<li><p>Beendet den Anruf mithilfe der Bluetooth-Geräts.</p></li>
</ol>

### <a name="bluetooth-and-nfc-tapsend"></a>Bluetooth- und NFK (Tap + senden)

Voraussetzungen: 

<ul>
<li><p>Bluetooth muss aktiviert sein.</p></li>
<li><p>Zweite Telefon überprüfen Tap + Funktionalität zu senden.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Wechseln Sie zu <strong>Fotos</strong> &gt; <strong>Alben</strong> und ein Foto auswählen.</p></li>
<li><p>Die Optionen für das Foto auswählen.</p></li>
<li><p>Teilen Sie das Foto bis NFK Tap / + senden.</p></li>
<li><p>Ein Popup-Fenster für die Übertragung wird auf das zweite Gerät angezeigt. Tippen Sie auf <strong>annehmen</strong> , und warten Sie für die Übertragung auf Fertig stellen.</p></li>
<li><p>Wechseln Sie zu <strong>Fotos</strong> &gt; <strong>Alben</strong> &gt; <strong>Bilder gespeichert</strong>.</p></li>
<li><p>Stellen Sie sicher, dass das übertragene Foto in das Album angezeigt wird.</p></li>
</ol>

### <a name="proximity-sensor"></a>Näherungssenor

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf der Startseite auf <strong>Telefon</strong>.</p></li>
<li><p>Rufen Sie das zweite Gerät</p></li>
<li><p>Halten Sie den Finger über den Earpiece Bereich. Stellen Sie sicher, dass die Anzeige deaktiviert wird.</p></li>
<li><p>Trennen Sie die Verbindung.</p></li>
</ol>

### <a name="video-streaming"></a>Videostreaming

Voraussetzungen: 

<ul>
<li><p>Das Gerät mit Wi-Fi verbunden sein oder über eine Verbindung zu den Webbrowser verwenden.</p></li>
<li><p>Ein zweites Gerät mit aufrufen.</p></li>
<li><p>Bluetooth-Geräts.</p></li>
</ul>

Testen Sie Schritte:

<ol>
<li><p>Tippen Sie auf der Startseite auf <strong>Internet Explorer</strong>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn im Browser zum ersten Mal gestartet wird, wird ein Dialogfeld pop-up aufgefordert werden, &quot;empfohlene verwenden?&quot; Tippen Sie auf die Schaltfläche <strong>empfohlen</strong> .</p>
</div>
<div>
 
</div></li>
<li><p>Tippen Sie auf die Adressleiste, und wechseln Sie zu einer Website, die Videos unterstützt.</p></li>
<li><p>Wählen Sie ein Video aus der Website ein, und tippen Sie auf <strong>Wiedergeben</strong>.</p></li>
<li><p>Stellen Sie sicher, dass das Video Pufferung und schließlich startet wiedergeben. Je nach der Netzwerk-Übertragungsrate kann es 15 bis 20 Sekunden für das Video wiederzugeben dauern.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Anhalten</strong> , auf dem Bildschirm angezeigt.</p></li>
<li><p>Stellen Sie sicher, dass das Video angehalten ist.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Wiedergeben</strong> , auf dem Bildschirm angezeigt.</p></li>
<li><p>Überprüfen Sie das Video fortgesetzt und ohne Probleme wiedergegeben wird.</p></li>
<li><p>Stellen Sie sicher, dass eine Benachrichtigung für den eingehenden Anruf über Bluetooth gehört wird und die Audiowiedergabe.</p></li>
<li><p>Erhalten Sie den eingehenden Anruf durch Drücken der Taste Bluetooth, und stellen Sie sicher, dass die Verbindung hergestellt ist.</p></li>
<li><p>Trennen Sie die Verbindung über Bluetooth, und tippen Sie auf die Schaltfläche <strong>Wiedergeben</strong> , auf dem Bildschirm angezeigt.</p></li>
<li><p>Stellen Sie sicher, dass das Video beginnt mit der Wiedergabe und die Audiodaten über Bluetooth-Geräts geroutet wird.</p></li>
<li><p>Vom zweiten Gerät senden Sie eine Textnachricht an das Testgerät aus.</p></li>
<li><p>Stellen Sie sicher, dass eine Benachrichtigung Text am Telefon und eine audio-Benachrichtigung auf die Bluetooth für die eingehende Nachricht empfangen werden. Tippen Sie auf <strong>ignorieren</strong> , wenn Sie die Textnachricht ignorieren.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Für einige Regionen Sprache wird nicht unterstützt, und eine Meldung wird angezeigt, auf dem Gerät. Tippen Sie auf <strong>Schließen</strong> , und fahren Sie fort zu testen.</p>
</div>
<div>
 
</div></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Wiedergeben</strong> , auf dem Bildschirm angezeigt.</p></li>
<li><p>Stellen Sie sicher, dass das Video beginnt mit der Wiedergabe ohne Probleme und Audiosignale über Bluetooth geleitet werden.</p></li>
</ol>

### <a name="audio-streaming"></a>Streaming Audio

Voraussetzungen: 

<ul>
<li><p>Zweites Gerät für die Unterstützung des Anrufs.</p></li>
<li><p>Ein A2DP Bluetooth-Geräts.</p></li>
<li><p>Outlook-Musik app heruntergeladen.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Melden Sie sich mit Ihrem Microsoft Account.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Geräte</strong> &gt; <strong>Bluetooth</strong>. Aktivieren Sie Bluetooth.</p></li>
<li><p>Tragen Sie einen A2DP Bluetooth-Geräts paring Modus. Wenn sie in den Suchergebnissen auf dem Gerät aufgeführt ist, tippen Sie auf. Stellen Sie sicher, dass der Status des Bluetooth-Geräts als "Verbundenen VoIP Musik." angezeigt</p></li>
<li><p>Drücken Sie die Hardware zurück- <strong>Schaltfläche</strong> um zur Liste zurückzukehren. Tippen Sie auf die app "Musik Outlook-".</p></li>
<li><p>Führen Sie eine streifbewegung von der <strong>neu</strong> Pivot und tippen Sie auf ein Album links.</p></li>
<li><p>Tippen Sie auf einen Titel für das Album.</p></li>
<li><p>Stellen Sie sicher, dass die Spur Pufferung und schließlich startet Wiedergabe über Bluetooth. Je nach der Netzwerk-Übertragungsrate kann es bis zu 15 bis 20 Sekunden die Audiodatei mit der Wiedergabe beginnt dauern.</p></li>
<li><p>Vom zweiten Gerät rufen Sie das Testgerät.</p></li>
<li><p>Stellen Sie sicher, dass eine Benachrichtigung für den eingehenden Anruf über Bluetooth gehört wird und die Audiodaten hält.</p></li>
<li><p>Erhalten Sie den eingehenden Anruf mit der Bluetooth-Schaltfläche.</p></li>
<li><p>Stellen Sie sicher, dass die Verbindung hergestellt ist.</p></li>
<li><p>Trennen Sie die Verbindung über Bluetooth-Geräts.</p></li>
<li><p>Stellen Sie sicher, dass die Spur wieder automatisch neu startet.</p></li>
<li><p>Senden Sie über das zweite Gerät eine Textnachricht, das Testgerät.</p></li>
<li><p>Stellen Sie sicher, dass eine Benachrichtigung Text auf dem Gerät angezeigt wird und eine audio-Benachrichtigung auf die Bluetooth-Geräts für die eingehende Nachricht empfangen wird.</p></li>
<li><p>Tippen Sie auf die Benachrichtigung Text und senden Sie eine Antwort zu.</p></li>
<li><p>Stellen Sie sicher, dass die Audiodaten wird ohne Probleme abgespielt.</p></li>
<li><p>Tippen Sie zweimal auf die Schaltfläche Bluetooth <strong>zurück</strong> .</p></li>
<li><p>Drücken Sie die Schaltfläche Bluetooth <strong>Weiterleiten</strong> .</p></li>
<li><p>Stellen Sie sicher, dass der nächste Titel beginnt mit der Wiedergabe.</p></li>
<li><p>Drücken Sie die Bluetooth- <strong>zurückspulen</strong> .</p></li>
<li><p>Stellen Sie sicher, dass der vorherige Titel beginnt mit der Wiedergabe.</p></li>
<li><p>Drücken Sie die Bluetooth <strong>Pause</strong> -Taste.</p></li>
<li><p>Stellen Sie sicher, dass die Spur hält.</p></li>
<li><p>Drücken Sie die Taste Bluetooth <strong>Pause</strong> erneut ein.</p></li>
<li><p>Stellen Sie sicher, dass die Spur Wiedergabe fortgesetzt.</p></li>
</ol>

### <a name="smsmms-messaging"></a>SMS/MMS-Messaging

Voraussetzungen: 

<ul>
<li><p>Zwei zusätzliche Gerät, um die messaging-Dienste zu testen.</p></li>
<li><p>Haben Sie ein Foto und ein Video auf den Geräten</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Klicken Sie auf der Startseite Tippen Sie auf <strong>Messaging</strong>, und tippen Sie dann auf <strong>neu</strong>.</p></li>
<li><p>Erstellen einer neuen Textnachricht.</p></li>
<li><p>Stellen Sie sicher, dass die Karte Chat mit einer leeren Adressleiste geöffnet wird und Antworten im Feld.</p></li>
<li><p>Geben Sie im Feld "An" die Telefonnummer des zweiten Geräts.</p></li>
<li><p>Geben Sie eine kurze &quot;Hello&quot; in das Feld Antwort ein und Senden der Nachricht.</p></li>
<li><p>Überprüfen Sie, ob die gesendete Nachricht in der Karte Chat angezeigt wird.</p></li>
<li><p>Stellen Sie sicher, dass das zweite Gerät die Nachricht erfolgreich empfangen.</p></li>
<li><p>Die Karte Chat Tippen Sie auf die Schaltfläche <strong>Anlagen</strong> und wählen Sie ein Bild anfügen.</p></li>
<li><p>Wählen Sie ein Bild aus der Kamera Blogroll (engl.), und senden Sie die Nachricht.</p></li>
<li><p>Stellen Sie sicher, dass das zweite Gerät das Bild erfolgreich erhält.</p></li>
<li><p>Antworten Sie vom zweiten Gerät mit einem Bild Anlage.</p></li>
<li><p>Stellen Sie sicher, dass das Testgerät die Bild-Nachricht empfängt.</p></li>
<li><p>Antwort von das Testgerät mit einem video Anlage.</p></li>
<li><p>Stellen Sie sicher, dass das zweite Gerät empfängt und kann das Video abspielen.</p></li>
<li><p>Antworten Sie vom zweiten Gerät mit Anlage zu einer video.</p></li>
<li><p>Stellen Sie sicher, dass das Testgerät das Video empfängt und wiedergeben kann.</p></li>
<li><p>Klicken Sie auf das Testgerät drücken Sie die Hardware zurück-Schaltfläche, und erstellen Sie eine andere SMS-Nachricht.</p></li>
<li><p>Stellen Sie sicher, dass die Karte Chat geöffnet wird und verfügt über eine leere Adressleiste und Antworten im Feld.</p></li>
<li><p>Geben Sie eine Telefonnummer ein, geben Sie ein Semikolon, und geben Sie die Telefonnummer des Kontakts in das Feld "An".</p></li>
<li><p>Geben Sie eine Nachricht mit mehr als 320 Zeichen in das Feld Antwort ein, und tippen Sie auf <strong>Senden</strong>.</p></li>
<li><p>Stellen Sie sicher, dass vor der Indikator Zeichen angezeigt wird oder wenn der Zeichen Grenzwert erreicht ist.</p></li>
<li><p>Überprüfen Sie, ob die gesendete Nachricht in einer Karte Chat angezeigt wird.</p></li>
<li><p>Überprüfen, ob die mehrteilige SMS-Nachricht empfangenen erfolgreich ist, in der zweiten und dritten Geräte ist</p></li>
<li><p>Senden Sie eine SMS-Antwortnachricht aus der zweiten oder dritten Gerät an das Testgerät.</p></li>
<li><p>Klicken Sie auf das Testgerät überprüfen Sie, ob die audio-Benachrichtigung für eingehende SMS-Nachricht hören ist.</p></li>
<li><p>Stellen Sie sicher, dass die Antwort in eine Karte Chat als die aktuelle Nachricht angezeigt wird.</p></li>
</ol>

### <a name="fm-radio"></a>UKW

Voraussetzungen: 

<ul>
<li><p>Eine Reihe von Kopfhörer als eine Antenne für die UKW dienen soll.</p></li>
<li><p>Ein zweites Gerät für die Unterstützung des Anrufs.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Schließen Sie ein Paar von Kopfhörer.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>UKW</strong>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Zulassen Sie den UKW Zugriff auf Diensten, wenn angefordert</p>
</div>
<div>
 
</div></li>
<li><p>Drücken Sie <strong>Vorwärts</strong> oder <strong>Rückwärts</strong> um die Stationen durchsuchen. Stellen Sie sicher, dass der Empfänger über die Stationen entsprechend überprüft.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Anhalten</strong> und sicherzustellen Sie, dass der Sender wird angehalten. Tippen Sie auf <strong>Wiedergeben</strong> , und vergewissern Sie sich, dass Radio wiedergeben fortgesetzt.</p></li>
<li><p>Rufen Sie von einem zweiten Gerät das Testgerät.</p></li>
<li><p>Stellen Sie sicher, dass eine Benachrichtigung für den eingehenden Anruf über Bluetooth gehört wird und die Audiowiedergabe.</p></li>
<li><p>Erhalten Sie den eingehenden Anruf durch Drücken der Taste Bluetooth und stellen Sie sicher, dass der Anruf eine Verbindung herstellt.</p></li>
<li><p>Trennen Sie die Verbindung über Bluetooth, und stellen Sie sicher, dass der Sender wieder automatisch neu startet.</p></li>
<li><p>Schaltfläche <strong>Favoriten hinzufügen</strong> die aktuelle Station zu Favoriten zu speichern.</p></li>
<li><p>Blättern Sie durch den Stationen durch ein Lesegerät den Bildschirm und stellen Sie sicher, dass der Empfänger verschiedene Stationen übernehmen kann.</p></li>
<li><p>Drücken Sie die Startseite wieder <strong>Starten</strong> . Stellen Sie sicher, dass der Sender weiterhin wiedergegeben werden sollen.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Geräte</strong> &gt; <strong>Bluetooth</strong>. Deaktivieren Sie Bluetooth.</p></li>
<li><p>Drücken Sie die Hardware zurück. Flugzeug-Modus aktivieren, und stellen Sie sicher, dass der Sender Wiedergabe. Deaktivieren Sie Flugzeug-Modus.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>UKW</strong>.</p></li>
<li><p>Tippen Sie auf <strong>Favoriten</strong>. Stellen Sie sicher, dass die zuvor hinzugefügte bevorzugte Station angezeigt wird, wählen Sie diese Station, und stellen Sie sicher, dass der Sender den entsprechenden Favoriten Sender optimiert.</p></li>
<li><p>Tippen Sie auf <strong>...</strong> in der unteren rechten. Tippen Sie auf <strong>Wechseln zu Lautsprecher</strong> überprüfen, die das Audio über Lautsprecher kommt.</p></li>
<li><p>Rufen Sie von einem zweiten Gerät das Testgerät.</p></li>
<li><p>Überprüfen, ob eine Benachrichtigung für den eingehenden Anruf ist hören und die Audiowiedergabe anzuhalten.</p></li>
<li><p>Den eingehenden Anruf erhalten, und stellen Sie sicher, dass der Anruf eine Verbindung herstellt.</p></li>
<li><p>Trennen Sie die Verbindung, und stellen Sie sicher, dass der Sender wieder automatisch neu startet.</p></li>
</ol>

### <a name="rebooting-the-device"></a>Neustart des Geräts

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Drücken Sie und halten Sie die Power auf dem Gerät</p></li>
<li><p>Überprüfen Sie, ob die &quot;nach unten schieben ausschalten&quot; Bildschirm wird angezeigt, und führen Sie den Bildschirm nach unten.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät ausgeschaltet wird.</p></li>
<li><p>Drücken Sie und halten Sie die Taste erneut.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät zum Hauptbildschirm OS ohne abstürzen erfolgreich gestartet.</p></li>
<li><p>Wiederholen Sie die Schritte 1 bis 5.</p></li>
</ol>

### <a name="messagingfamily-room"></a>Messaging-Familie Raum

Voraussetzungen: 

<ul>
<li><p>Zwei anderen Microsoft-Konten.</p></li>
<li><p>Zwei andere Geräte.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Die Zahlen für das zweite und dritte Gerät das Testgerät Kontaktliste hinzufügen.</p></li>
<li><p>Tippen Sie in der Liste app auf <strong>Personen</strong> , und führen Sie eine streifbewegung von Links mit dem Pivot <strong>zusammen</strong> .</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Hinzufügen (+)</strong> und von der &quot;neu hinzufügen&quot; Bildschirm, tippen Sie auf <strong>Raum</strong>.</p></li>
<li><p>Überprüfen Sie, ob die &quot;Name Your Raum&quot; Bildschirm wird angezeigt, um einen Anzeigenamen für den Chatroom anzugeben. Tippen Sie dann auf <strong>Speichern</strong>.</p></li>
<li><p>Aus der &quot;Raum bearbeiten&quot; Bildschirm, tippen Sie auf die Schaltfläche <strong>einladen</strong> , von der app-Leiste, die in Schritt 1 erstellte Kontakte hinzufügen.</p></li>
<li><p>Nehmen Sie die Einladung auf dem anderen Gerät</p></li>
<li><p>Stellen Sie sicher, dass alle Kontakte, die Sie erstellt haben im Bildschirm Mitglieder aufgeführt sind.</p></li>
<li><p>Führen Sie Links mit dem Pivot <strong>Chat</strong> , und geben Sie Text in dem Meldungsfeld.</p></li>
<li><p>Stellen Sie sicher, dass alle Mitglieder der Gruppe Text, der Sie gesendet eingeht.</p></li>
<li><p>Reaktion auf die Post vom zweiten Gerät, und stellen Sie sicher, dass alle Gruppenmitglieder (einschließlich des Testgeräts) die Nachricht erhalten.</p></li>
<li><p>Tippen Sie in das Testgerät auf die Taste zurück und führen Sie eine streifbewegung Links erneut mit dem <strong>Kalender</strong> Pivot.</p></li>
<li><p>Tippen Sie auf das Symbol " <strong>neu</strong> " aus der app-Leiste, und erstellen Sie einen neuen Termin für die bevorstehenden Stunden.</p></li>
<li><p>Stellen Sie sicher, dass der neue Termin in die Pivot <strong>Kalender</strong> für das Testgerät als auch die anderen Telefone angezeigt wird.</p></li>
<li><p>Starten Sie das <strong>Fotos</strong> Pivot, und tippen Sie auf die Schaltfläche <strong>Hinzufügen</strong> in der app-Leiste Hinzufügen einer &quot;Fotos und Videos&quot;.</p></li>
<li><p>Stellen Sie sicher, dass der hochgeladenen Fotos und Videos in das <strong>Foto</strong> Pivot das Test-Telefon als auch die anderen Geräten dargestellt wird.</p></li>
<li><p>Führen Sie eine streifbewegung von links die <strong>Notizen</strong> Pivot und tippen Sie auf die Schaltfläche <strong>Hinzufügen</strong> in der app-Leiste, um eine Notiz hinzufügen.</p></li>
<li><p>Überprüfen Sie, ob der erstellte Hinweis auf die <strong>Notiz</strong> Pivot des Testgeräts und den anderen Geräten gespeichert wird.</p></li>
</ol>

### <a name="search"></a>Search

Voraussetzungen: 

<ul>
<li><p>Mit Wi-Fi verbunden ist.</p></li>
<li><p>Mit einem Microsoft-Konto angemeldet.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf die Suchschaltfläche am Telefon, um die Suche zu starten.</p></li>
<li><p>Tippen Sie in das Suchfeld bearbeiten auf, und geben Sie den Suchbegriff &quot;Hunde. "</p></li>
<li><p>Drücken Sie die EINGABETASTE, um zu suchen.</p></li>
<li><p>Überprüfen Sie die Suchergebnisse auf mehrere Pivot-Elemente.</p></li>
<li><p>Stellen Sie sicher, dass alle Pivots mit der relevante Ergebnisse aufgefüllt werden oder dass vorhanden ist, der angibt, dass keine Ergebnisse messaging.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>US-Bilder können die Suchergebnisse variieren. Alle Pivot-Elemente möglicherweise nicht vorhanden.</p>
</div>
<div>
</div></li>
</ol>

### <a name="alarm"></a>Alarm

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Alarmen &amp; Uhr</strong>.</p></li>
<li><p>Erstellen Sie einen neuen Alarm.</p></li>
<li><p>Speichern Sie den neuen Alarm.</p></li>
<li><p>Stellen Sie sicher, dass der Alarm durch die richtigen Informationen erstellt wird.</p></li>
<li><p>Stellen Sie sicher, dass der Alarm zum angegebenen Zeitpunkt mit der richtigen Alarm Tone und Namen klingelt.</p></li>
</ol>

### <a name="themes"></a>Designs

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Personalisierung</strong> &gt; <strong>Design</strong>.</p></li>
<li><p>Ändern Sie die Werte für <strong>Hintergrund</strong> und <strong>Akzentfarbe</strong>.</p></li>
<li><p>Drücken Sie auf der Startseite zurückzugebenden <strong>Starten</strong> .</p></li>
<li><p>Stellen Sie sicher, dass das Gerät Design geändert wurde.</p></li>
</ol>

### <a name="contacts"></a>Kontakte

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf der Startseite auf die Kachel <strong>Personen</strong> .</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Hinzufügen (+)</strong> auf der app-Leiste, aus der Pivot <strong>Kontakte</strong> .</p></li>
<li><p>Geben Sie eine Telefonnummer ein, und speichern Sie es.</p></li>
<li><p>Stellen Sie sicher, dass die neue Nummer auf der Seite Kontakte gespeichert ist.</p></li>
<li><p>Wählen Sie die gespeicherte Telefonnummer.</p></li>
<li><p>Tippen Sie auf <strong>Bearbeiten</strong> , um die ausgewählte Nummer zu ändern. Geben Sie einen Namen für den Kontakt, und speichern Sie ihn.</p></li>
<li><p>Stellen Sie sicher, dass der Kontakt korrekt geändert wird.</p></li>
<li><p>Stellen Sie sicher, dass der neue Kontakt auf der Seite "Kontakte" unter dem Namen der richtigen gespeichert ist.</p></li>
<li><p>Wählen Sie den gespeicherten Kontakt aus.</p></li>
<li><p>Tippen Sie auf <strong>Optionen</strong>.</p></li>
<li><p>Tippen Sie auf <strong>Löschen</strong>.</p></li>
<li><p>Stellen Sie sicher, dass der Kontakt aus der Kontaktliste entfernt wurde.</p></li>
</ol>

### <a name="email"></a>Email

Voraussetzungen: 

Mehrere gültige e-Mail-Konten von Anbietern kompatibel.

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf <strong>Einstellungen</strong> , klicken Sie in der Liste App &gt; <strong>Konten</strong> &gt; <strong>e &amp; Konten</strong>.</p></li>
<li><p>Tippen Sie auf <strong>Konto hinzufügen</strong> &gt; <strong>Microsoft-Konto</strong> auf Konto hinzufügen.</p></li>
<li><p>Geben Sie auf dem Bildschirm Outlook eine gültige e-Mail-Adresse und das Kennwort ein.</p></li>
<li><p>Stellen Sie sicher, dass das Konto erstellt wird und dass es von ordnungsgemäß ohne Probleme synchronisiert wird.</p></li>
<li><p>Drücken Sie <strong>Starten</strong> , und tippen Sie dann auf die Kachel <strong>E-Mail</strong> .</p></li>
<li><p>Stellen Sie sicher, dass die e-Mail-Nachricht wie gewünscht angezeigt wird.</p></li>
<li><p>Tippen Sie auf das Symbol <strong>neue e-Mail-Nachrichten</strong> (+).</p></li>
<li><p>Verfassen und Senden einer e-Mails an Ihr Konto mit Betreff, Textkörper und Microsoft Excel oder Word-Dokument zugeordnet ist.</p></li>
<li><p>Stellen Sie sicher, dass die e-Mail-Nachricht geöffnet und das Konto auf einem PC gelesen werden kann. Antworten Sie auf diese e-Mail von Ihrem PC Reaktion.</p></li>
<li><p>Stellen Sie sicher, dass das Testgerät Angabe der neue e-Mails empfängt und dass die Kachel aktualisiert, um die neue Nachricht anzuzeigen.</p></li>
<li><p>Stellen Sie sicher, dass die Nachricht geöffnet und gelesen werden.</p></li>
<li><p>Wiederholen Sie die Schritte, die die verschiedenen Typen von e-Mail-Konten verwenden.</p></li>
</ol>

### <a name="microsoft-office"></a>Microsoft Office

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Office</strong>.</p></li>
<li><p>Führen Sie eine streifbewegung von Links mit dem Pivot <strong>zuletzt verwendet</strong> .</p></li>
<li><p>Stellen Sie sicher, dass mindestens drei Beispieldokumente vorhanden sind:</p>
<ol>
<li><p>Beispieldokument.</p></li>
<li><p>Beispielpräsentation.</p></li>
<li><p>Beispiel-Kalkulationstabelle.</p></li>
</ol></li>
<li><p>Tippen Sie auf <strong>Beispieldokument</strong>.</p></li>
<li><p>Stellen Sie sicher, dass das Dokument ordnungsgemäß gerendert wird und dass Sie einen Bildlauf durch das Dokument durchführen können.</p></li>
<li><p>Drücken Sie die Schaltfläche Hardware zurück, das Dokument geschlossen.</p></li>
<li><p>Tippen Sie auf <strong>Beispiel Spreadsheet</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Tabelle ordnungsgemäß gerendert wird (d. h. Zeilen 1, 2, usw. und Spalten A, B usw. in der Ansicht angezeigt werden) und, die Sie einen Bildlauf durch das Dokument durchführen können.</p></li>
<li><p>Tippen Sie auf <strong>Beispielpräsentation</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Präsentation in die Ausrichtung des Telefons angezeigt wird, indem Sie das Telefon an/aus der Hochformat/Querformat drehen. Übergang durch Folien 2 bis 3 durch ein Lesegerät von rechts nach links und drehen Sie das Telefon.</p></li>
<li><p>Stellen Sie sicher, dass der Inhalt ordnungsgemäß gerendert wird.</p></li>
<li><p>Drücken Sie die Hardware zurück-Schaltfläche, um die Präsentation zu schließen.</p></li>
<li><p>Die <strong>zuletzt verwendet</strong> Pivot Tippen Sie auf die Schaltfläche <strong>Hinzufügen (+)</strong> , um ein neues Worddokument erstellen.</p></li>
<li><p>Öffnen Sie ein Word-Dokument, und geben Sie ein Teil des Inhalts. Tippen Sie auf <strong>mehr (...)</strong> , und tippen Sie dann auf <strong>Speichern</strong>.</p></li>
<li><p>Wählen Sie &quot;Telefon&quot; als Speicherort zum Speichern der Daten. Tippen Sie auf die Schaltfläche <strong>Speichern</strong> , um das erstellte Word-Dokument zu speichern.</p></li>
<li><p>Stellen Sie sicher, dass das Word-Dokument, das Sie erstellt in der <strong>aktuell</strong> Pivot der Office-app angezeigt wird.</p></li>
<li><p>Wiederholen Sie die Schritte 10 bis 13 für ein Excel-Dokument.</p></li>
</ol>

### <a name="calendar"></a>Kalender

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Kalender</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Kalender app gestartet wird.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Ansicht Kalender</strong> , und wählen Sie einen Monat.</p></li>
<li><p>Stellen Sie sicher, dass Sie einen Bildlauf durch die Monate im Kalender durchführen können.</p></li>
<li><p>Tippen Sie erneut auf die Schaltfläche <strong>Ansicht</strong> , und wählen Sie einen Tag aus.</p></li>
<li><p>Stellen Sie sicher, dass Sie auf dem Bildschirm Tag durchgeführt werden.</p></li>
<li><p>Tippen Sie auf eine leere Raster, in den kommenden Stunden.</p></li>
<li><p>Vergewissern Sie sich, dass eine Inline Eingabefelds und virtuelle Tastatur neu gestartet wird.</p></li>
<li><p>Geben Sie "Betreff" Text im Bearbeitungsfeld.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Speichern</strong> app-Leiste.</p></li>
<li><p>Stellen Sie sicher, dass der Termin ist gespeichert und werden mit der richtigen Betreff und die Zeit angezeigt.</p></li>
<li><p>Tippen Sie auf der Startseite wieder <strong>Starten</strong> .</p></li>
<li><p>Stellen Sie sicher, dass der Termin angezeigt wird ordnungsgemäß in die Kachel "Kalender".</p></li>
<li><p>Drücken Sie das Gerät, das Gerät zu sperren. Drücken Sie die Taste erneut, um die Sperrbildschirm anzeigen.</p></li>
<li><p>Stellen Sie sicher, dass auf dem Sperrbildschirm der Termin im Kalender angezeigt wird.</p></li>
</ol>

### <a name="internet-explorer"></a>InternetExplorer

Voraussetzungen: 

<ul>
<li><p>Bluetooth muss aktiviert sein.</p></li>
<li><p>Zweites Gerät zu Testzwecken Tap + senden.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf der Startseite auf Internet Explorer.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn im Browser zum ersten Mal gestartet wird, wird ein Dialogfeld pop-up Frage &quot;empfohlene verwenden?&quot; Tippen Sie auf die Schaltfläche <strong>empfohlen</strong> .</p>
</div>
<div>
 
</div></li>
<li><p>Stellen Sie sicher, dass Internet Explorer gestartet wird.</p></li>
<li><p>Tippen Sie auf die Adressleiste. Beginnen mit der Eingabe der Name einer Website.</p></li>
<li><p>Stellen Sie sicher, dass automatische Vorschläge angezeigt, sobald die URL eingegeben wurde.</p></li>
<li><p>Sicherstellen Sie, dass das Laden der Seite des Inhalts für die URL, die eingegeben wurde.</p></li>
<li><p>Überprüfen Sie, ob die Seite zu Favoriten hinzugefügt werden kann.</p></li>
<li><p>Drücken und gestreckt, um vergrößern oder verkleinern. Die Seite schwenken. Führen Sie einen Bildlauf nach oben und unten der Seite. Stellen Sie sicher, dass diese Gesten ordnungsgemäß funktionieren.</p></li>
<li><p>Leerlauf befunden 30-bis 60 Sekunden.</p></li>
<li><p>Stellen Sie sicher, dass es keine Probleme mit der Seite sind nach dem lassen Sie das Gerät im Leerlauf.</p></li>
<li><p>Das Gerät zu drehen.</p></li>
<li><p>Stellen Sie sicher, dass der Übergang vom Hochformat zum Querformat reibungsloses ist.</p></li>
<li><p>Sicherstellen Sie, dass der Browser in der richtigen Ausrichtung übergeht und die app-Leiste Menüs angezeigt werden.</p></li>
<li><p>Tippen Sie in der unteren rechten Seite des app-Leiste auf <strong>mehr (...)</strong> , und tippen Sie auf <strong>Favoriten</strong>.</p></li>
<li><p>Stellen Sie sicher, dass Sie zu einer Website, die in den Favoriten aufgeführten navigieren können.</p></li>
<li><p>Freigeben die Website für das zweite Telefon mit NFK / Tap + senden.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn im Browser zum ersten Mal auf dem zweiten Gerät gestartet wird, ein Dialogfeld Popup-Frage &quot;empfohlene verwenden?&quot; Tippen Sie auf <strong>empfohlen</strong>.</p>
</div>
<div>
 
</div></li>
<li><p>Stellen Sie sicher, dass die freigegebene Website im Browser des zweiten Geräts wird geöffnet.</p></li>
</ol>

### <a name="charging"></a>Erheben

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ul>
<li><p>Verbinden Sie einer Wand Ladegerät auf das Gerät, und überprüfen Sie, dass das <strong>aufgeladen</strong> Symbol angezeigt wird. Hören Sie akustische Angabe, nachdem Sie das Kabel anschließen. Trennen Sie aufgeladen.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Das Gerät hat keinen für drahtlose aufgeladen funktioniert deaktiviert werden.</p>
</div>
<div>
 
</div></li>
</ul>

### <a name="pc-companion"></a>PC Companion

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Schließen Sie das Gerät an einen Computer mit einem USB-Kabel an.</p></li>
<li><p>Überprüfen Sie, dass das Gerät aufgeladen gestartet wird.</p></li>
<li><p>Stellen Sie sicher, dass das PC Companion-Tool auf dem PC nach einigen Sekunden automatisch gestartet.</p></li>
</ol>

### <a name="ambient-light-sensor"></a>Umgebungslichtsensor

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>System</strong> &gt; <strong>Anzeigen</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Option <strong>automatisch anpassen der Helligkeit der Anzeige</strong> aktiviert ist.</p></li>
<li><p>Drücken Sie auf der Startseite zurückzugebenden <strong>Starten</strong> .</p></li>
<li><p>Scheinen Sie eine Taschenlampe/Fackel am oberen Rand des Geräts</p></li>
<li><p>Stellen Sie sicher, dass der Kontrast des Anzeige als Reaktion auf das Licht ändert.</p></li>
</ol>

### <a name="display-and-accelerometer"></a>Anzeige und Beschleunigungsmesser

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Hochformat führen Sie den Finger über den gesamten Tastatur.</p></li>
<li><p>Stellen Sie sicher, dass eine Nachricht erstellt wird, wie erwartet.</p></li>
<li><p>Drehen Sie das Gerät auf der linken und rechten Seiten.</p></li>
<li><p>Stellen Sie sicher, dass die Bildschirm Ausrichtung reibungslos ändert.</p></li>
</ol>

### <a name="download-keyboard"></a>Herunterladen der Tastatur

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste der App auf <strong>Einstellungen</strong> &gt; <strong>Geräte</strong> &gt; <strong>Tastatur</strong>.</p></li>
<li><p>Tippen Sie auf die <strong>Registerkarte Tastaturen hinzufügen</strong>.</p></li>
<li><p>Wählen Sie eine Tastatur aus.</p></li>
<li><p>Stellen Sie sicher, dass die Tastatursprache die von Ihnen gewählten als angezeigt wird &quot;vorbereiten Download...&quot;</p></li>
<li><p>Stellen Sie sicher, dass nach der Download bereit ist, der Benutzer Option zum Installieren der Tastatur erhält.</p></li>
<li><p>Installieren Sie die Tastatur.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät wird neu gestartet und die Updates installiert sind.</p></li>
<li><p>Starten Sie auf der Startseite der Messaging-app.</p></li>
<li><p>Erstellen Sie eine neue SMS-Nachricht.</p></li>
<li><p>Tippen Sie und halten Sie die <strong>ENG</strong> auf der virtuellen Tastatur. Wählen Sie die neu heruntergeladenen Sprache aus dem Menü aus.</p></li>
<li><p>Sicherstellen Sie, dass die Tastatur in der neuen Sprache Tastatur geändert wird.</p></li>
<li><p>Erstellen Sie und senden Sie eine neue SMS-Nachricht.</p></li>
<li><p>Stellen Sie sicher, dass die SMS-Nachricht erfolgreich gesendeten und in derselben Sprache auf dem zweiten Gerät empfangenen</p></li>
</ol>

### <a name="download-app-from-store"></a>Laden Sie die app aus Store

Voraussetzungen: 

Wi-Fi muss verbunden sein.

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf der Startseite auf <strong>Anmelden</strong>.</p></li>
<li><p>Überprüfen Sie, ob der Speicher wird gestartet</p></li>
<li><p>Wählen Sie eine app oder Spiel aus der Front-Seite anmelden, und installieren Sie es.</p></li>
<li><p>Stellen Sie sicher, dass Sie den Downloadstatus der app/Spiel überwachen können.</p></li>
<li><p>Stellen Sie sicher, dass der Spiele Download abgeschlossen, in weniger als 5 Minuten ist und die Statusanzeige nicht mehr vorhanden ist.</p></li>
<li><p>Stellen Sie sicher, dass das app/Spiel gestartet werden kann, nachdem sie heruntergeladen wird.</p></li>
</ol>

### <a name="skype-video-calling"></a>Skype (Video-Anrufe)

Voraussetzungen: 

<ul>
<li><p>Sie müssen mit Wi-Fi verbunden werden.</p></li>
<li><p>Bluetooth-Geräts.</p></li>
<li><p>Zweite Rufnummer</p></li>
<li><p>Zwei Microsoft-Konto (eins für jedes Gerät) Skype verwenden.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf der Startseite auf <strong>Anmelden</strong>.</p></li>
<li><p>Suchen Sie nach, und Laden Sie die Skype-app.</p></li>
<li><p>Tippen Sie auf <strong>Einstellungen</strong> , klicken Sie in der Liste app &gt; <strong>Geräte</strong> &gt; <strong>Bluetooth</strong>. Aktivieren Sie Bluetooth.</p></li>
<li><p>Tragen Sie die Bluetooth-Geräts paring Modus, und klicken Sie dann das Testgerät Bluetooth-Gerät Kopplung.</p></li>
<li><p>Skype-app zu starten.</p></li>
<li><p>Stellen Sie sicher, dass die Geschäftsbedingungen Seite eingeblendet.</p></li>
<li><p>Tippen Sie auf <strong>Übernehmen</strong>.</p></li>
<li><p>Stellen Sie sicher, dass die Anmeldeseite angezeigt wird.</p></li>
<li><p>Greifen Sie auf unten auf der Anmeldeseite und melden Sie sich mit einem Microsoft-Account.</p></li>
<li><p>Überprüfen Sie, ob "zulassen Benachrichtigung?" Nachricht wird mit den Schaltflächen <strong>Ja</strong> und <strong>Nein</strong> angezeigt.</p></li>
<li><p>Tippen Sie auf <strong>keine</strong>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Führen Sie dieselben Schritte auf dem zweiten Gerät zur Vorbereitung der Skype zu testen.</p>
</div>
<div>
 
</div></li>
<li><p>Auf der zweiten Telefon zugeordnet führen Sie eine streifbewegung an die <strong>Personen</strong> Pivot, und wählen die Skype berücksichtigt, d. h. das Testgerät</p></li>
<li><p>Stellen Sie einen Audioanruf auf das Testgerät mit dem zweiten Gerät.</p></li>
<li><p>Das Testgerät sicher, dass eine Klingeltons für den eingehenden Anruf hören.</p></li>
<li><p>Nehmen Sie den Anruf mithilfe der Bluetooth-Geräts.</p></li>
<li><p>Stellen Sie sicher, dass das Audio auf beide Gerät (Audiosignale auf das Testgerät sollte über Bluetooth-Geräts weitergeleitet werden) hören sein.</p></li>
<li><p>Stellen Sie sicher, dass die stummschaltung und die Funktionalität des Telefons Test- und Sekunde funktioniert.</p></li>
<li><p>Trennen Sie den Anruf mithilfe der Bluetooth-Geräts.</p></li>
<li><p>Stellen Sie sicher, dass kein Audio hören ist, nachdem der Anruf beendet ist.</p></li>
<li><p>Bluetooth deaktivieren.</p></li>
<li><p>Führen Sie auf dem Testgerät Links mit dem Pivot <strong>Personen</strong> , und wählen Sie das Skype-Konto des zweiten Geräts.</p></li>
<li><p>Tätigen eines ausgehenden video Anrufs auf das zweite Gerät.</p></li>
<li><p>Stellen Sie sicher, dass die Benachrichtigung über ausgehende Anrufe über den Lautsprecher des Testgeräts hören</p></li>
<li><p>Empfangen von eingehenden Videoanruf auf dem zweiten Gerät.</p></li>
<li><p>Stellen Sie sicher, dass die Verbindung hergestellt ist.</p></li>
<li><p>Stellen Sie sicher, dass sowohl der Geräte Video und Audio funktionieren.</p></li>
<li><p>Überprüfen Sie, ob die stummschaltung und die Funktionalität auf beiden Geräten funktioniert.</p></li>
<li><p>Trennen Sie das Testgerät mit den Anruf.</p></li>
<li><p>Stellen Sie sicher, dass kein Audio hören ist, nachdem der Anruf beendet wird.</p></li>
</ol>

### <a name="play-a-game"></a>Ein Spiel

Voraussetzungen: 

Angry Vögel Spiel von im app Store heruntergeladen.

Testen Sie die Schritte aus:

<ol>
<li><p>Starten Sie in der Liste App das Spiel Angry Vögel...</p></li>
<li><p>Stellen Sie sicher, dass das Spiel 15 bis 20 Sekunden lang vollständig geladen.</p></li>
<li><p>Stellen Sie sicher, dass im Hauptmenü Hintergrundmusik wiedergegeben wird.</p></li>
<li><p>Stellen Sie sicher, dass die Musik stumm geschaltet und stummgeschaltet werden kann.</p></li>
<li><p>Drücken Sie die Schaltfläche <strong>Wiedergeben</strong> platziert in der Mitte des Bildschirms.</p></li>
<li><p>Stellen Sie sicher, dass das Spiel auf eine Ebene wiedergegeben wird geladen.</p></li>
<li><p>Auf dieser Ebene wiedergeben.</p></li>
<li><p>Überprüfen Sie, ob das Spiel visuelle Objekte und Audio reibungslos sind.</p></li>
<li><p>Stellen Sie sicher, dass das Spiel nicht abstürzen ist.</p></li>
<li><p>Stellen Sie sicher, dass Sie unterbrechen und angehaltenen Status das Spiel aufzuheben können.</p></li>
</ol>

### <a name="backup-and-restore-content"></a>Sichern und Wiederherstellen von Inhalten

Voraussetzungen: 

<ul>
<li><p>Mit Wi-Fi verbunden ist.</p></li>
<li><p>Apps, die an das Gerät heruntergeladen</p></li>
<li><p>Microsoft-Konto.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie auf <strong>Einstellungen</strong> , klicken Sie in der Liste App &gt; <strong>Personalisierung</strong> &gt; <strong>Design</strong>.</p></li>
<li><p>Ändern der Aolor Hintergrund und Markierungsleiste.</p></li>
<li><p>Tippen Sie auf <strong>Einstellungen</strong> , klicken Sie in der Liste App &gt; <strong>Konten</strong> &gt; <strong>e &amp; Konten</strong>.</p></li>
<li><p>Melden Sie sich mit Ihrem Microsoft-Konto.</p></li>
<li><p>Starten Sie InternetExplorer.</p></li>
<li><p>Wechseln Sie zu einer Website und zu Favoriten hinzufügen.</p></li>
<li><p>Wechseln Sie zu einer zweiten Website und zu Favoriten hinzufügen.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Update &amp; Wiederherstellung</strong> &gt; <strong>Sicherung</strong>.</p></li>
<li><p>Schalten Sie Sicherung.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>System</strong> &gt; <strong>zu</strong> &gt; <strong>Ihr Telefon zurücksetzen</strong>.</p></li>
<li><p>Ein &quot;Warnung!&quot; Popup-Meldung wird zweimal angezeigt. Tippen Sie auf &quot;Ja&quot; beide Male zum Zurücksetzen des Geräts</p></li>
<li><p>Stellen Sie sicher, dass das Gerät zurückgesetzt wird, und klicken Sie dann OOBE durchlaufen.</p></li>
<li><p>Während der OOBE Sie bei entsprechender Aufforderung mit einem Wi-Fi-Netzwerk verbinden.</p></li>
<li><p>Geben Sie bei Aufforderung während OOBE das Microsoft-Konto, das Sie verwendet haben.</p></li>
<li><p>Wählen Sie während OOBE Sie bei entsprechender Aufforderung die Sicherung wiederhergestellt, die soeben erstellt wurde.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Diese Sicherung sollte der Markierung am Anfang der Liste der Sicherung sein. Überprüfen Sie das Datum und Uhrzeit, um zu überprüfen, und wählen Sie dann die Sicherung.</p>
</div>
<div>
 
</div></li>
<li><p>Führen Sie den Rest des Prozesses OOBE.</p></li>
<li><p>Auf dem Bildschirm Start stellen Sie sicher, dass die Farbe Hintergrund und die Änderungen aus Schritt2 übereinstimmen.</p></li>
<li><p>Starten Sie Internet Explorer, und öffnen Sie Ihre Favoriten.</p></li>
<li><p>Stellen Sie sicher, dass die Websites, die Sie in den vorherigen Schritten hinzugefügt Favoriten aufgeführt sind.</p></li>
<li><p>In der Liste der von Apps stellen Sie sicher, dass Ihre heruntergeladenen apps immer noch aufgelistet sind.</p></li>
<li><p>Tippen Sie in der Liste app auf <strong>Einstellungen</strong> &gt; <strong>Konten</strong> &gt; <strong>E-Mail &amp; Konten</strong>. Tippen Sie auf das Konto angemeldet, und geben Sie das Kennwort ein.</p></li>
<li><p>Stellen Sie sicher, dass Ihr e-Mail-Konto synchronisiert wird.</p></li>
</ol>

### <a name="kids-corner"></a>Kinderecke

Voraussetzungen: 

Spiele aus dem Speicher auf dem Gerät installiert.

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>des Kind Ecke</strong>.</p></li>
<li><p>Stellen Sie sicher, dass der Willkommensseite für Kinderecke gestartet wird.</p></li>
<li><p>Fügen Sie die Kind Ecke eines Spiels hinzu.</p></li>
<li><p>Fügen Sie eine Reihe von apps die Kind Ecke hinzu.</p></li>
<li><p>Tippen Sie auf <strong>Weiter</strong>.</p></li>
<li><p>Stellen Sie sicher, dass im Dialogfeld Kennwort eingeblendet.</p></li>
<li><p>Erstellen Sie ein Kennwort ein.</p></li>
<li><p>Tippen Sie auf <strong>Fertig stellen</strong>.</p></li>
<li><p>Stellen Sie sicher, dass Kinderecke gestartet wird.</p></li>
<li><p>Führen Sie eine streifbewegung oben auf dem Bildschirm. Geben Sie das Kennwort ein, wenn Sie aufgefordert werden.</p></li>
<li><p>Stellen Sie sicher, dass die Startseite für Kinderecke wird gestartet, und nur die Anwendungen und den Spielen, die überprüft wurden, während die Kind Ecke einrichten auf dem Bildschirm vorhanden sind.</p></li>
<li><p>Sperren Sie und entsperren Sie des Geräts.</p></li>
<li><p>Stellen Sie sicher, dass das Kennwort ein Dialogfeld eingeblendet. Geben Sie das Kennwort ein, und das Gerät entsperrt.</p></li>
<li><p>Stellen Sie sicher, dass der Startseite angezeigt wird.</p></li>
</ol>

### <a name="nfc-tag-reading"></a>Lesen der NFK-Tag

Voraussetzungen: 

<ul>
<li><p>Ein Element mit einem Tag QR/NFK/URL, die überprüft werden soll.</p></li>
<li><p>Mit Wi-Fi, folgen Sie den Tagpfad verbunden ist.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Lassen Sie das Gerät im Leerlauf, damit es in den Energiesparmodus wechselt. Drücken Sie das Gerät, um die Sperrbildschirm aufzurufen.</p></li>
<li><p>Halten Sie die <strong>Kamera</strong> (während auf Sperrbildschirm), um die Kamera aufzurufen.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn das Telefon eine Kamera Schaltfläche nicht vorhanden ist, starten Sie die Kamera-Anwendung direkt.</p>
</div>
<div>
 
</div></li>
<li><p>Wählen Sie die Schaltfläche <strong>Lens</strong> aus.</p></li>
<li><p>Wählen Sie <strong>Bing Vision</strong>aus.</p></li>
<li><p>Halten Sie die Kamera zu einem Tag QR, um zu überprüfen.</p></li>
<li><p>Wählen Sie den im Feld Bild/Hyperlink, der nach der Überprüfung wird angezeigt.</p></li>
<li><p>Stellen Sie sicher, dass Sie zur entsprechenden Seite überprüft die-Tag zugeordnet durchgeführt werden.</p></li>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>Personalisierung</strong> &gt; <strong>Sperren des Bildschirms</strong>.</p></li>
<li><p>Aktivieren Sie "Auf" Kennwort und erstellen Sie Kennwort.</p></li>
<li><p>Lassen Sie das Gerät im Leerlauf, damit es in den Energiesparmodus wechselt. Drücken Sie das Gerät, um die Sperrbildschirm aufzurufen.</p></li>
<li><p>Halten Sie die Kamera (auf dem Sperrbildschirm), um die Kamera aufzurufen.</p></li>
<li><p>Verwenden der Schaltfläche <strong>Lens</strong> .</p></li>
<li><p>Wählen Sie <strong>Bing Vision</strong>aus.</p></li>
<li><p>Stellen Sie sicher, dass der Benutzer vor dem Zugriff auf Bing Vision ein Kennwort eingeben muss.</p></li>
</ol>

### <a name="lens-picker"></a>Lens Personenauswahl

Voraussetzungen: 

<ul>
<li><p>Sie müssen sich mit einem Microsoft-Konto angemeldet sein, objektive installieren.</p></li>
<li><p>Bluetooth muss aktiviert sein NFK Freigabe verwenden.</p></li>
<li><p>Zweites Gerät für NFK Funktionalität.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Halten Sie die Kamera Hardware-Taste, um die Kamera app starten (oder starten Sie die Anwendung direkt, wenn das Gerät eine Kamera Schaltfläche nicht vorhanden ist), und tippen Sie auf <strong>Abbrechen</strong> , in der &quot;zulassen die Webcam an Ihren Standort verwenden&quot; Bildschirm.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Aufforderung "Ermöglichen... Speicherort" wird die vorherige Einstellungen beherrschen und möglicherweise nicht angezeigt, wenn die Kamera zuletzt verwendet wurde.</p>
</div>
<div>
 
</div></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Lens</strong> .</p></li>
<li><p>Stellen Sie sicher, dass die Lens Überlagerung mit der <strong>Bing Vision</strong> und für alle installierten objektive-Symbol angezeigt wird.</p></li>
<li><p>Wählen Sie eine von den installierten objektive. Wenn keine Lens Programme installiert haben, müssen Sie eine herunterladen.</p>
<ol>
<li><p>Klicken Sie auf "Weitere objektive suchen"</p></li>
<li><p>Wählen Sie aus, und installieren Sie eine Anwendung aus der Liste.</p></li>
</ol></li>
<li><p>Stellen Sie sicher, dass Sie ein Bild verwenden der Anwendung installierten Lens nutzen können.</p></li>
<li><p>Stellen Sie sicher, dass das Bild angezeigt wird und dass Sie zwischen letzte Bilder und die Kamera blättern können.</p></li>
<li><p>Zuletzt verwendete Grafik auswählen.</p></li>
<li><p>Stellen Sie sicher, dass Sie das Foto mit NFK freigeben können / Tap + freigeben.</p></li>
</ol>

### <a name="local-scout-load-time"></a>Lokale Scout des Ladens

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Starten Sie <strong>lokale Scout</strong>.</p></li>
<li><p>Wenn Sie lokale Scout zum ersten Mal starten, ermöglichen Sie Zugriff auf Ihren aktuellen Standort.</p></li>
<li><p>Stellen Sie sicher, dass Sie verschiedene Registerkarten für unterschiedliche Arten von lokalen betrieben zu sehen sind.</p></li>
<li><p>Wählen Sie ein Restaurant aus.</p></li>
<li><p>Stellen Sie sicher, dass die entsprechende Informationen für ein Restaurant bereitgestellt wird.</p></li>
<li><p>Wählen Sie die Anweisungen aus.</p></li>
<li><p>Sicherstellen Sie, dass die Karte mit erfahren Sie, wie auf das Restaurant geladen wird.</p></li>
<li><p>Sicherstellen Sie, dass lokalen Scout Speicherorte/Ergebnisse in einer akzeptablen Zeit geladen wird.</p></li>
</ol>

### <a name="download-maps"></a>Herunterladen von Karten

Voraussetzungen: 

Mit Wi-Fi Maps herunterladen verbunden ist.

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Karten</strong> &gt; <strong>mehr (...)</strong> &gt; <strong>Settings</strong>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn die Anwendung zum ersten Mal gestartet wird, wird die app für die Berechtigung zum Zugriff auf den Standort des tischtelefons lassen. Gewähren Sie Speicherort Zugriff.</p>
</div>
<div>
 
</div></li>
<li><p>Wählen Sie <strong>Karten herunterladen</strong>.</p></li>
<li><p>Tippen Sie auf die Schaltfläche <strong>Hinzufügen (+)</strong> .</p></li>
<li><p>Wählen Sie <strong>North und Mittelamerika</strong> &gt; <strong>USA</strong> &gt; <strong>Indiana</strong>.</p></li>
<li><p>Warten Sie auf das Feld zuzuordnender Download abgeschlossen.</p></li>
<li><p>Drücken Sie auf der Startseite zurückzugebenden <strong>Starten</strong> .</p></li>
<li><p>Tippen Sie auf <strong>Einstellungen</strong> , klicken Sie in der Liste App &gt; <strong>Flugzeug Modus</strong> &gt; <strong>Einschalten</strong>.</p></li>
<li><p>Drücken Sie <strong>Starten</strong>, und tippen Sie in der Liste App auf <strong>Maps</strong>.</p></li>
<li><p>Tippen Sie auf <strong>Search</strong> (Vergrößerungsglas) und suchen Sie nach "Butte, Montana".</p></li>
<li><p>Stellen Sie sicher, dass in den heruntergeladenen Maps Butte, Montana nicht gefunden werden kann.</p></li>
<li><p>Suchen nach "Indianapolis, Indiana".</p></li>
<li><p>Stellen Sie sicher, dass die Zuordnung die heruntergeladene Zuordnung von Indianapolis, Indiana geladen wird.</p></li>
</ol>

### <a name="visual-voicemail"></a>Visual-Voicemail

Voraussetzungen: 

Sie benötigen ein zweites Gerät.

Testen Sie die Schritte aus:

<ol>
<li><p>Schalten Sie das Testgerät</p></li>
<li><p>Rufen Sie das Testgerät mit dem zweiten Gerät.</p></li>
<li><p>Stellen Sie sicher, dass der Anruf an die Voicemail weitergeleitet wird. Lassen Sie eine Voicemail.</p></li>
<li><p>Schalten Sie das Testgerät.</p></li>
<li><p>Tippen Sie auf <strong>Telefon</strong>.</p></li>
<li><p>Tippen Sie auf das Symbol " <strong>Voicemail</strong> ".</p></li>
<li><p>Akzeptieren Sie die Clientinstallation Visual Voicemail.</p></li>
<li><p>Stellen Sie sicher, dass nach der Installation die Voicemail heruntergeladen wird und Sie an die Voicemail überwachen können.</p></li>
<li><p>Rufen Sie das Testgerät aus dem zweiten Gerät erneut. Beantworten Sie es nicht.</p></li>
<li><p>Stellen Sie sicher, dass der Anruf an die Voicemail weitergeleitet wird. Lassen Sie eine Nachricht ein.</p></li>
<li><p>Stellen Sie sicher, dass Sie eine SMS-Nachricht, die besagt angezeigt, dass eine Voicemail verfügbar ist. Stellen Sie sicher, dass die neue Voicemail aufgelistet ist und dass Sie die Voicemail abspielen können.</p></li>
<li><p>Wiederholen Sie Schritte 9 bis 10, und hinterlassen Sie eine zweite Sprachnachricht zu.</p></li>
<li><p>Stellen Sie sicher, ob zwei Voicemails aufgeführten ein Symbol angezeigt wird.</p></li>
<li><p>Sollen Sie die Voicemails wiedergegeben werden.</p></li>
<li><p>Löschen Sie die Voicemails.</p></li>
</ol>

### <a name="internet-sharing"></a>Gemeinsame Nutzung der Internetverbindung

Voraussetzungen: 

<ul>
<li><p>Plan für Daten, die Freigabe hinweg ermöglicht.</p></li>
<li><p>Alle Wi-Fi-basiertes Gerät unter.</p></li>
</ul>

Testen Sie die Schritte aus:

<ol>
<li><p>Internetfreigabe aktivieren.</p></li>
<li><p>Verbinden der freigegebenen Wi-Fi mit ein zweites Gerät, mit den Namen und das Kennwort auf dem Gerät.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Das zweite Gerät sollte eine eigene Wi-Fi-aktiviert haben.</p>
</div>
<div>
 
</div></li>
<li><p>Stellen Sie sicher, dass das zweite Gerät auf das Internet zugreifen kann.</p></li>
<li><p>Stellen Sie sicher, dass das Gerät zeigt die Anzahl von Gästen an (zweites Gerät) mit freigegebenen Wi-Fi verbunden ist.</p></li>
</ol>

### <a name="storage-manager"></a>Speichermanager

Voraussetzungen: keine

Testen Sie die Schritte aus:

<ol>
<li><p>Tippen Sie in der Liste App auf <strong>Einstellungen</strong> &gt; <strong>System</strong> &gt; <strong>Speicher Sinne</strong>.</p></li>
<li><p>Tippen Sie auf dem Gerät.</p></li>
<li><p>Stellen Sie sicher, dass Usage Datenbalken Folgendes angezeigt werden:</p>
<ol>
<li><p>Apps + Spiele</p></li>
<li><p>Ordnet</p></li>
<li><p>temporäre Dateien</p></li>
<li><p>Fotos</p></li>
<li><p>Musik</p></li>
<li><p>Videos</p></li>
<li><p>Dokumente</p></li>
<li><p>e-Mail- und messaging</p></li>
<li><p>System</p></li>
<li><p>andere</p></li>
</ol></li>
<li><p>Tippen Sie auf den Eintrag.</p></li>
<li><p>Stellen Sie sicher, dass Sie einen Bildlauf durch die app-Detailseite durchführen können.</p></li>
<li><p>Überprüfen Sie, ob die Menge an Speicherplatz pro app angezeigt wird.</p></li>
</ol> 
 
 





