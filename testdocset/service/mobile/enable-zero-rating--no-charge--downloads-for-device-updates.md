---
author: kpacquer
Description: "Aktivieren Sie zero-rating (kostenlos) Downloads für Geräteupdates"
ms.assetid: defe3e29-03b2-448e-acf7-9009b45283d3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Aktivieren Sie zero-rating (kostenlos) Downloads für Geräteupdates"
ms.openlocfilehash: 2777583d37f03285878a4c53d5db9035ded93452
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-zero-rating-no-charge-downloads-for-device-updates"></a>Aktivieren Sie zero-rating (kostenlos) Downloads für Geräteupdates


Mobilfunkbetreiber (MOs) können Geräte Updates zu erhalten, ohne für datennutzungs-belastet wird, durch den Windows Update-Servern zu ihrer Liste erklärt Websites hinzufügen aktivieren.

Diese Methode ermöglicht nur Updates von den Servern Windows Update erklärt werden. Andere Netzwerkdatenverkehr, wie Store Updates oder Updates für Geräte mit der Freigabe (ICS) werden nicht erklärt.

## <a name="span-idenablingzero-ratingspanspan-idenablingzero-ratingspanspan-idenablingzero-ratingspanenabling-zero-rating"></a><span id="Enabling_zero-rating"></span><span id="enabling_zero-rating"></span><span id="ENABLING_ZERO-RATING"></span>Zero-rating aktivieren


Fügen Sie die folgenden beiden URLs in Ihr Netzwerk als erklärt Websites hinzu:

-   http://wp.Download.windowsupdate.com

-   http://wp.DS.Download.windowsupdate.com

Nachdem diese URLs erklärt werden, sind keine weiteren Aktionen durchführen, um die erste NULL Bewertung vorhanden. Für Alldevices (Variant Operator und Markt-Geräte) wirksam werden.

## <a name="span-idtestingzero-ratingspanspan-idtestingzero-ratingspanspan-idtestingzero-ratingspantesting-zero-rating"></a><span id="Testing_zero-rating"></span><span id="testing_zero-rating"></span><span id="TESTING_ZERO-RATING"></span>Zero-rating testen


Um NULL Bewertung zu testen, müssen Sie ein Update über Mobilfunk auslösen, die unter den Grenzwert von Ihrer Monat definierten bleiben klein genug ist Beispielsweise kann ein MO zero-rating Downloads auf 100 MB oder weniger beschränken.

1.  Beginnen Sie mit einer Retail Gerät, das für ein Update bereit ist.

2.  Entfernen Sie die SIM-Karte (sofern vorhanden). Überprüfen Sie wie viele Daten sie es für den aktuellen Zeitraum zugeordnet ist. Wenden Sie sich die MO für spezifische Anweisungen an.

3.  Deaktivieren Sie alle Wi-Fi-Optionen:

    1.  In der Einstellung: **Wi-Fi**:

        Ändern Sie **Wi-Fi-Netzwerke** zu **Deaktivieren**.

        Ändern Sie auf **manuell** **Wi-Fi aktivieren auf Sichern** .

        Tippen Sie auf Wi-Fi sinnvoll, und ändern Sie **mit Wi-Fi-Hotspots verbinden** zu **Deaktivieren**.

    2.  In den **Einstellungen** &gt; **Update und Recovery** &gt; **Telefon aktualisieren**, deaktivieren Sie das Kontrollkästchen **automatisch heruntergeladen Updates, wenn die Einstellungen für meine Daten zulassen** .

4.  Erzwingen Sie das Update über die Mobilfunk Verbindung:

    1.  Können Sie das Gerät zum Starten.

    2.  Deaktivieren Sie das Gerät, und fügen Sie dann eine SIM-Karte eines Plans Daten zugeordnet.

    3.  Schließen Sie das Gerät erneut zu schalten, starten und melden Sie sich mit Ihrem Konto.

    4.  Suchen Sie nach dem Update: **Einstellungen** &gt; **Update und Recovery** &gt; **Telefon zu aktualisieren**. Sie sollten so erzwingen Sie das Update über die Mobilfunk Verbindung können.

        Beachten Sie, sehen Sie möglicherweise eine Warnung besagt, dass Sie für den Download berechnet werden können:

        ![Screenshot: bereit zum Herunterladen von mobile Daten](images/oem-update-.png)

    5.  Nachdem der Download abgeschlossen ist, überprüfen Sie die Daten Plan um festzustellen, ob das Gerät für die Aktualisierung berechnet wurde.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Update](index.md)

 

 






