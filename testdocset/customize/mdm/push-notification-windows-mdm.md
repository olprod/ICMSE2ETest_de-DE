---
title: "Push Notification-Unterstützung für die Verwaltung von Geräten"
description: "DMClient CSP unterstützt die Möglichkeit, verwaltungssitzungen Push initiierte Gerät konfigurieren."
MS-HAID:
- p\_phdevicemgmt.push\_notification\_support\_for\_device\_management
- p\_phDeviceMgmt.push\_notification\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9031C4FE-212A-4481-A1B0-4C3190B388AE
ms.openlocfilehash: b85adda303e3595e13ec71a4a4dce183b9a9f06c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="push-notification-support-for-device-management"></a>Push Notification-Unterstützung für die Verwaltung von Geräten

Die [DMClient CSP](dmclient-csp.md) unterstützt die Möglichkeit, verwaltungssitzungen Push initiierte Gerät konfigurieren. Mit der [Windows-Notification-Services (WNS)](http://go.microsoft.com/fwlink/p/?linkid=528800)kann ein Verwaltungsserver ein Geräts zum Einrichten einer Management-Sitzung mit dem Server über eine Push-Benachrichtigung anfordern. Ein Gerät ist so konfiguriert, dass Push unterstützen vom Verwaltungsserver durch das Gerät mit einer PFN für eine Anwendung bereitstellen. Nachdem das Gerät konfiguriert wurde, registriert eine permanente Verbindung mit der Cloud WNS (Batterie Sinn und Daten Sinne Conditions zulassen).

Um ein Gerät Management-Sitzung zu initiieren, muss der Verwaltungsserver zunächst mit WNS mithilfe der SID und des geheimen clientschlüssels authentifizieren. Nach der Authentifizierung, erhält der Server ein Token, das zum Initiieren einer unformatierten Pushbenachrichtigungen für alle ChannelURI verwendet werden kann. Der Verwaltungsserver möchte eine Gerät Management-Sitzung mit einem Gerät zu initiieren, kann dessen Token und das Gerät ChannelURI nutzen und beginnen mit dem Gerät kommunizieren.

Weitere Informationen dazu, wie Sie Push-Anmeldeinformationen (SID und des geheimen clientschlüssels) zu erhalten und PFN mit in WNS, finden Sie unter [erste WNS Anmeldeinformationen und PFN für MDM Pushbenachrichtigungen](#get-wns-credentials-and-pfn-for-mdm-push-notification).

Da ein Gerät immer nicht mit dem Internet verbunden werden kann, unterstützt WNS Zwischenspeichern Benachrichtigungen zur Zustellung an das Gerät, nachdem sie eine Verbindung herstellen. Um sicherzustellen, dass Ihre Benachrichtigung für die Übermittlung zwischengespeichert wird, legen Sie die X-WNS-Cache-Policy Kopfzeile auf Cache. Darüber hinaus Wenn der Server eine Zeit gebundene Roh-Push-Benachrichtigung senden möchte, kann der Server den Header X-WNS-TTL verwenden, der bereitstellen wird WNS mit einem TTL Bindung, damit die Benachrichtigung abläuft, nachdem die Zeit vergangen ist. Weitere Informationen finden Sie unter [Übersicht über die rohbenachrichtigung (Windows-Runtime-apps)](http://go.microsoft.com/fwlink/p/?LinkId=733254).

Beachten Sie die folgenden Einschränkungen im Zusammenhang mit Pushbenachrichtigungen und WNS:

-   Pushbenachrichtigungen für die Verwaltung von Geräten verwendet unformatierte Pushbenachrichtigungen. Dies bedeutet, dass diese Rohdaten Push Notifications unterstützen oder nicht nutzen Push Notification Nutzlast.
-   / Kleinschreibung des Empfangs von Pushbenachrichtigungen an den Einstellungen Batterie Bildschirmschoner und Daten sinnvoll, auf dem Gerät. Wenn die Batterie bestimmte Schwellenwerte unterschreitet, wird beispielsweise die dauerhafte Verbindung des Geräts mit WNS beendet. Darüber hinaus, wenn der Benutzer Daten sinnvoll nutzen ist und ihre monatliche Zuteilung Datengruppe überschritten hat, wird die dauerhafte Verbindung des Geräts mit WNS auch beendet.
-   Eine ChannelURI zur Verfügung gestellt, die Verwaltungsserver vom Gerät gilt nur für 30 Tage. Das Gerät erneuert das ChannelURI nach 15 Tagen automatisch und löst eine Management-Sitzung auf erfolgreiche Erneuerung von der ChannelURI aus. Es wird dringend empfohlen, dass bei jeder Sitzung Management fragt der Verwaltungsserver den ChannelURI-Wert, um sicherzustellen, dass er den letzten Wert erhalten hat. Dadurch wird sichergestellt, dass der Verwaltungsserver nicht versucht, eine ChannelURI verwenden, die abgelaufen ist.
-   Push ist kein Ersatz für die Verwendung eines Zeitplans abrufen.
-   WNS behält sich das Recht von Pushbenachrichtigungen zu Ihrer PFN blockieren, wenn ungültige Verwendung von Benachrichtigungen erkannt wird. Alle Geräte, die mit diesem PFN verwalteten verliert Push haben initiiert Gerät Management Support.
-   Unter Windows 10, Version 1511 als auch Windows 8 und 8.1 scheitern MDM Push mitunter erneuern den WNS Push-Kanal automatisch verursacht es abläuft. Es kann möglicherweise auch hängen, wenn der für den Kanal PFN festlegen.

    Um dieses Problem zu umgehen sollte dieses Problem, wenn ein 410 vom Server WNS zurückgegeben wird, bei dem Versuch, eine Push-Benachrichtigung an das Gerät die PFN senden während der nächsten Synchronisierung Sitzung festgelegt werden. Um zu verhindern, dass den Push-Kanal auf ältere Builds ablaufen, können Server die PFN zurücksetzen, Ablauf der DDE-Kanal (~ 30 Tage). Wenn sie bereits Windows 10 ausführen, sollte ein Update zur Verfügung, die sie installieren können, die das Problem zu beheben, sollte vorhanden sein.

-   Auf Windows-10, Version 1511; verwenden wir die folgende Retry-Logik für die DMClient:
    -   Wenn ExpiryTime größer als 15 Tage ist wird nach ein Zeitplan für festgelegt, wenn 15 Tage.
    -   Wenn ExpiryTime zwischen jetzt und 15 Tage eines Zeitplans für 4 +/-1 Stunde von jetzt festgelegt ist.
    -   Wenn ExpiryTime vergangen ist wird nach ein Zeitplan ab sofort für 1 Tag +/-4 Stunden festgelegt.


-   Auf Windows-10, Version 1607, überprüfen wir für Netzwerkkonnektivität bevor wiederholt wird. Wir prüfen nicht Internet-Verbindung. Wenn Netzwerkkonnektivität nicht verfügbar ist wir die Wiederholung überspringen und festlegen Zeitplans für 4 +/-1 Stunden erneut versuchen.


## <a name="get-wns-credentials-and-pfn-for-mdm-push-notification"></a>Abrufen der Anmeldeinformationen WNS und PFN für MDM Push-Benachrichtigung

Wenn Sie eine PFN und WNS Anmeldeinformationen erhalten möchten, müssen Sie eine Windows Store-app erstellen.

1.  Besuchen Sie das Windows- [Dashboard](https://dev.windows.com/en-US/dashboard) , und melden Sie sich über Ihr Entwicklerkonto.

    ![MDM Push-Benachrichtigung](images/push-notification1.png)
2.  Erstellt eine neue app an.

    ![MDM Push-Benachrichtigung](images/push-notification2.png)
3.  Reservieren Sie einen app-Namen ein.

    ![MDM Pushbenachrichtigungen](images/push-notification3.png)
4.  Klicken Sie auf **Dienste**.

    ![MDM Pushbenachrichtigungen](images/push-notification4.png)
5.  Klicken Sie auf **Pushbenachrichtigungen**.

    ![MDM Push-Benachrichtigung](images/push-notification5.png)
6.  Klicken Sie auf **Live Services-Website**. Für die **Anwendung Registrierung Portal** Seite wird ein neues Fenster geöffnet.

    ![MDM Pushbenachrichtigungen](images/push-notification6.png)
7.  Auf der Seite **Anwendung Registrierung Portal** sehen Sie die Eigenschaften für die app, die Sie, wie etwa erstellt:
    -   Id der Anwendung
    -   Anwendung Secrets
    -   Windows Store-Paket SID-Anwendungsidentität und Publisher.

    ![MDM Push-Benachrichtigung](images/push-notification7.png)
8.  Klicken Sie auf **Speichern**.
9.  Schließen Sie das Fenster **Anwendung Registrierung Portal** und Windows Dev Center Dashboard zurück.
10. Wählen Sie Ihre app aus der Liste auf der linken Seite an.
11. Vom linken Navigationsbereich erweitern Sie **App-Verwaltung** , und klicken Sie dann auf **App-Identität**.

    ![MDM Push-Benachrichtigung](images/push-notification10.png)
12. Klicken Sie auf der **App-Identität** sehen Sie die **Paket-Familienname (PFN)** Ihrer App.

 






