---
author: kpacquer
Description: "Eine Reihe von wichtigen Szenarien behandelt das Gerät zurückzusetzen: ein Benutzer ein Gerät, um es in einem anderen Besitzer übertragen zurücksetzen möchten."
ms.assetid: 2db677f1-edf6-421d-8482-770ee5f16140
MSHAttr: PreferredLib:/library/windows/hardware
title: "Zurücksetzen eines mobilen Geräts"
ms.openlocfilehash: ada132c1d114158c59f856d4380a97a6126883ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resetting-a-mobile-device"></a>Zurücksetzen eines mobilen Geräts


Zurücksetzen des Geräts werden eine Reihe von wichtigen Szenarien ausgeräumt:

-   Ein Benutzer kann möglicherweise Zurücksetzen eines Geräts, um es in einem anderen Besitzer zu übertragen.
-   Das Gerät verlorenen oder gestohlenen wurde und der Besitzer möchte Remote Zurücksetzen des Geräts
-   Das Gerät gehört zu einer Organisation, und die Organisation möchte das Gerät Remote zurückgesetzt. Beispielsweise wenn ein Mitarbeiter das Unternehmen verlässt.
-   Das Gerät hat nicht funktionierenden und möchte, dass des Benutzers das Gerät zurückzusetzen.
-   OEM Factory Anwendungstests abgeschlossen sind und möchte das Gerät (optional vorinstallierte Zuordnungsdaten beibehalten) zurückgesetzt.

**Wichtige**  
Wenn Sie ein Gerät zurückgesetzt, gibt es keine in den Originalzustand Factory zurück. Zum Beispiel bleiben alle Pakete, die hinzugefügt oder während einer Aktualisierung geändert wurden. Um das Gerät in den Originalzustand Factory zurückzugeben, müssen mit dem ursprünglichen Factory Bild flash.

 

## <a name="span-idwaystoresetamobiledevicespanspan-idwaystoresetamobiledevicespanspan-idwaystoresetamobiledevicespanways-to-reset-a-mobile-device"></a><span id="Ways_to_reset_a_mobile_device"></span><span id="ways_to_reset_a_mobile_device"></span><span id="WAYS_TO_RESET_A_MOBILE_DEVICE"></span>Methoden zum Zurücksetzen eines mobilen Geräts


Die folgenden Optionen für das Zurücksetzen stehen verschiedene Arten von Benutzern zur Verfügung.

### <a name="span-idendusersspanspan-idendusersspanspan-idendusersspanend-users"></a><span id="End_users"></span><span id="end_users"></span><span id="END_USERS"></span>Endbenutzer

Endbenutzer können ein zurücksetzen aufrufen, durch die folgenden Optionen:

-   Tippen Sie auf **Einstellungen** , wenn Einstellungen kann zugegriffen werden, &gt; **System** &gt; **zur** &gt; **Ihr Telefon zurücksetzen**.

    **Hinweis**  
    Wenn das Gerät nicht erreichbar ist, sollte der Benutzer zuerst versuchen gestartet wird; finden Sie weiter unten in diesem Thema [einen Neustart des Betriebssystems](#restarting) .

     

-   Wenn die Einstellungen kann nicht zugegriffen werden, führen Sie die folgenden Schritte aus:

    1.  Deaktivieren Sie das Gerät aus.

    2.  Aktivieren Sie auf dem Gerät, halten Sie die Lautstärke gedrückt, bis das Ausrufezeichen auf dem Bildschirm angezeigt wird.

    3.  Drücken Sie die folgenden vier Schaltflächen in der angegebenen Reihenfolge: Lautstärke nach oben, Lautstärke nach unten, Strom, Lautstärke nach unten.

-   Verwenden Sie die Erase-Funktion auf der Website WindowsPhone.com Remote Zurücksetzen eines Geräts. Weitere Informationen finden Sie unter [Suchen Sie nach einem verlorenen Telefon](http://www.windowsphone.com/how-to/wp8/basics/find-a-lost-phone).

### <a name="span-idpartnersspanspan-idpartnersspanspan-idpartnersspanpartners"></a><span id="Partners"></span><span id="partners"></span><span id="PARTNERS"></span>Partner (engl.)

Zusätzlich zu die Optionen aufgeführt im vorherigen Abschnitt Partner wie OEMs und Mobilfunkbetreiber weisen die folgenden zusätzlichen Optionen zum Aufrufen einer zurücksetzen:

-   Ein zurücksetzen kann programmgesteuert beim manufacturing Szenarien durch Aufrufen der ResetPhone oder ResetPhoneEx-Funktion aufgerufen werden.

-   In nicht-Retail-Bildern (d. h., Bilder, in dem das **ReleaseType** -Element in der Datei OEMInput auf **Test**festgelegt ist), kann ein Zurücksetzen über das Startmenü Developer aufgerufen werden.

**Hinweis**  Der Endbenutzer Factory Reset-Prozess ist nicht für die Verwendung der Fabrik ausgelegt. Es wird empfohlen, das Telefon programmgesteuert Factory oder Reparaturservice Einstellungen zurücksetzen. Dies ist schneller als das Telefon mithilfe von **Einstellungen** zurücksetzen &gt; **System** &gt; **zu** &gt; **Ihr Telefon zurücksetzen**.

 

Sie können sicherstellen, dass alle Daten mithilfe von GetResetLogs.exe erfolgreich entfernt wurde. Die Protokolldateien erfahren Sie alle Dateien, die nach dem Zurücksetzen des Geräts nicht entfernt wurden.

### <a name="span-identerprisesspanspan-identerprisesspanspan-identerprisesspanenterprises"></a><span id="Enterprises"></span><span id="enterprises"></span><span id="ENTERPRISES"></span>Unternehmen

In Enterprise-Szenarien, in denen mobile Geräten mit Gerät Managementsoftware verwaltet werden, ein zurücksetzen kann aufgerufen werden, Remote mit den folgenden Optionen:

-   Ein zurücksetzen kann mithilfe der Einstellung der RemoteWipe mit Exchange ActiveSync aufgerufen werden. Weitere Informationen finden Sie unter [Übersicht über Windows Phone Exchange ActiveSync](http://go.microsoft.com/fwlink/?LinkId=270085) -Whitepaper im Microsoft Download Center.

-   Ein zurücksetzen kann mithilfe der OMA DM aufgerufen werden. Weitere Informationen finden Sie unter [RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418).

## <a name="span-idoperationsperformedbyphoneresetspanspan-idoperationsperformedbyphoneresetspanspan-idoperationsperformedbyphoneresetspanoperations-performed-by-phone-reset"></a><span id="Operations_performed_by_phone_reset"></span><span id="operations_performed_by_phone_reset"></span><span id="OPERATIONS_PERFORMED_BY_PHONE_RESET"></span>Operationen Telefon zurücksetzen


Ein Zurücksetzen führt die folgenden Vorgänge aus:

-   Es wird das Programm Chkdsk verwendet, um das Hauptfenster Betriebssystem für Probleme mit einer beschädigten Scannen und versucht wird, automatisch die Probleme zu beheben, sofern vorhanden. Wenn der Reset-Vorgang gestartet wird, mithilfe der ResetPhoneEx-Funktion mit der **ZURÜCKSETZEN\_BEIBEHALTEN\_BENUTZER\_STORE\_DATEN** Flag des Vorgangs überprüft auch die Partition der Benutzerdaten.

-   QuickFormat der Benutzer Datenpartition wird ausgeführt. Alle vorab aufgefüllte Daten (beispielsweise Zuordnungsdaten) auf der Benutzer Datenpartition gelöscht und müssen erneut geladen werden.

-   Entfernt alle Benutzer installiert Store-apps. Der Benutzer kann verwenden Sie die Sicherung und Features zum Wiederherstellen der installierten apps wiederherstellen.

-   Von der Partition OS entfernt alle Dateien, die nicht von Paketen beschrieben sind. Da Updates in Paketen beschrieben werden, werden Updates nach dem Zurücksetzen vorhanden sein.

-   Es wird die Registrierung mithilfe einer gespeicherten Kopie, die beim ersten Start gespeichert wurde, zu dem alle registrierungsänderungen hinzugefügt, die in Update-Pakete empfangen wurden neu erstellt.

-   Wenn vor der Operation zurücksetzen geräteverschlüsselung aktiviert ist, den Verschlüsselungsschlüssel Gerät aktiv dauerhaft gelöscht. Geräteverschlüsselung jedoch weiterhin mit einem anderen Schlüssel nach dem Zurücksetzen Vorgang aktiviert werden soll.

-   Wenn das Gerät auf eine SD-Karte verfügt, wird in einigen Szenarien SD-Karte auch neu formatiert. Weitere Informationen finden Sie weiter unten in diesem Thema [die SD-Karte formatieren](#sdcard) .

Die folgenden Elemente dauerhaft über ein Zurücksetzen auf:

-   Pakete, die an das Gerät übermittelt und vom Benutzer installiert wurden.

-   Registrierungsänderungen, die in Updates zugestellt wurden.

-   Alle Daten in der Partition DPP wie diesem Bereich beschäftigten.

-   Den Inhalt von Main Betriebssystem und Benutzer Datenpartitionen werden zurückgesetzt, wie oben beschrieben. In den anderen OS Partitionen gespeicherten beibehalten.

-   Statische kalt-Boot XML-Bereitstellungsdatei.

-   Wenn der Reset-Vorgang mithilfe der Funktion ResetPhoneEx initiiert, bestimmte Daten im Benutzerspeicher optional erhalten bleiben können durch Angeben von **ZURÜCKSETZEN\_BEIBEHALTEN\_BENUTZER\_SPEICHERN\_DATEN** im Parameter *DwFlags* . Derzeit ist die einzige Store Benutzerdaten, die beibehalten werden vorinstallierte Zuordnungsdaten.

### <a name="span-idsdcardspanspan-idsdcardspanreformatting-the-sd-card"></a><span id="sdcard"></span><span id="SDCARD"></span>Formatieren der SD-Karte

Wenn das Gerät auf eine SD-Karte enthält, kann in den folgenden Szenarien Zurücksetzen die SD-Karte formatiert werden:

-   Der Benutzer versucht, einen Reset-Vorgang im Abschnitt Systemeinstellungen, und der Benutzer wählt die Option zum Formatieren der SD-Karte zusammen mit das Gerät zurückzusetzen.

-   Der Benutzer initiiert einen Reset-Vorgang Remote von der WindowsPhone.com-Website. In diesem Szenario formatiert der Reset-Vorgang automatisch die SD-Karte; Es gibt keine Option für die SD-Karteninhalt beibehalten.

-   Der Reset-Vorgang wird Remote auf einem verwalteten Gerät mithilfe von Exchange ActiveSync oder mit OMA DM und Konfigurationsdienstanbieter RemoteWipe initiiert. In diesem Szenario formatiert der Reset-Vorgang automatisch die SD-Karte; Es gibt keine Option für die SD-Karteninhalt beibehalten. Weitere Informationen finden Sie unter [RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418).

-   Der Reset-Vorgang wird programmgesteuert von einer partneranwendung initiiert, die die Funktion ResetPhone oder ResetPhoneEx auf folgende Weise verwendet:

    -   ResetPhone: Übergeben Sie **TRUE** an den *bWipeStorageCard* -Parameter.

    -   ResetPhoneEx: Übergeben Sie **ZURÜCKSETZEN\_WISCHEN\_SD** an den *DwFlags* -Parameter.

Das Betriebssystem versucht in jedem dieser Szenarien QuickFormat SD-Karte ausführen. Wenn der Versuch, die SD-Karte neu zu formatieren nicht erfolgreich ist, wird der Vorgang mit dem Rest des Prozesses zum Zurücksetzen.

## <a name="span-idomaprovisioningandresettingthedevicespanspan-idomaprovisioningandresettingthedevicespanspan-idomaprovisioningandresettingthedevicespanoma-provisioning-and-resetting-the-device"></a><span id="OMA_provisioning_and_resetting_the_device"></span><span id="oma_provisioning_and_resetting_the_device"></span><span id="OMA_PROVISIONING_AND_RESETTING_THE_DEVICE"></span>Bereitstellung und das Gerät zurückzusetzen OMA


Einstellungen für OMA-Clientbereitstellung und OMA Gerät Management (DM), die in das Modem gespeichert sind werden beibehalten, wenn das Gerät zurückgesetzt wird. Registrierungseinträge, die über eine Bereitstellung geändert werden werden nicht beibehalten, wenn das Gerät zurückgesetzt wird. Weitere Informationen finden Sie unter [RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418).

## <a name="span-idpersistingprovisionedcontentfromtheworkplacespanspan-idpersistingprovisionedcontentfromtheworkplacespanspan-idpersistingprovisionedcontentfromtheworkplacespanpersisting-provisioned-content-from-the-workplace"></a><span id="Persisting_provisioned_content_from_the_workplace"></span><span id="persisting_provisioned_content_from_the_workplace"></span><span id="PERSISTING_PROVISIONED_CONTENT_FROM_THE_WORKPLACE"></span>Speichern von bereitgestellten Inhalt aus am Arbeitsplatz


Wenn das Gerät mit der Bereitstellung Pakete angewendet wurde, oder die Organisation EnterpriseExtFileSystem Konfigurationsdienstanbieter verwendet nach unten bereitgestellten Inhalte an einem persistenten Speicherort übertragen, kann mit einer Zurücksetzung folgendermaßen verwenden der bereitgestellte Inhalt beibehalten werden:

-   Der Benutzer initiiert einen Reset-Vorgang in Systemeinstellungen, und der Benutzer wählt die Option aus, um die bereitgestellten Inhalte aus den Arbeitsbereich beibehalten werden.
-   Der Reset-Vorgang ist Remote mit OMA DM und dem RemoteWipe Konfiguration-Dienstanbieter (DoWipePersistProvisionedData Knoten) auf einem verwalteten Gerät gestartet.

Weitere Informationen zu den RemoteWipe Konfiguration-Dienstanbieter und EnterpriseExtFileSystem Konfiguration-Dienstanbieter finden Sie unter [RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418).

## <a name="span-idrestartingspanspan-idrestartingspanspan-idrestartingspanrestarting-the-os"></a><span id="Restarting"></span><span id="restarting"></span><span id="RESTARTING"></span>Neustarten des Betriebssystems


Wenn das Gerät nicht schnell an die Prozedur normalen Herunterfahren oder die Power-Schaltfläche allein ist, kann das Gerät neu starten, indem Sie mit einer Kombination von Schaltflächen erzwungen werden. In diesem Verfahren wird das Gerät nicht zurückgesetzt; Stattdessen bietet es eine alternative Möglichkeit, ein nicht reagiert Gerät neu zu starten.

Wenn Sie das Gerät neu starten, halten Sie die Lautstärke gedrückt und die Schaltfläche Power für 10 Sekunden.

 

 





