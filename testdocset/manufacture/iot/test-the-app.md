---
author: kpacquer
Description: "Testen Sie eine Datei Appx auf einem Gerät IoT."
ms.assetid: ae043bb0-656e-4439-bdbe-a8d370629ab7
MSHAttr: PreferredLib:/library
title: "Testen Sie eine Appx-Datei auf einem Gerät IoT"
ms.openlocfilehash: 103dec18becb969dcf16705c701bc33cb5d2c5e8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idtestanappxfileonaniotdevicespantest-an-appx-file-on-an-iot-device"></a><span id="TEST_AN_APPX_FILE_ON_AN_IOT_DEVICE"></span>Testen Sie eine Datei Appx auf einem Gerät IoT

Verbinden Sie mit dem Gerät aus einer anderen PC **

1.  Ein Netzwerkkabel anschließen.

2.  Beachten Sie die IP-Adresse, die auf dem Gerät wird angezeigt.

3.  Öffnen Sie auf Ihrem PC-Technikers, Internet Explorer, und geben Sie in der Adresse mit einem Präfix http:// und: 8080 Suffix:

    ``` syntax
    http://100.100.0.100:8080
    ```

    Das [Windows-Gerät Portal](https://developer.microsoft.com/windows/iot/docs/deviceportal)wird geöffnet. Von hier aus können Sie app-Pakete hochladen, finden Sie unter welche apps installiert sind, und zwischen ihnen wechseln.

4.  Wenn Sie das IOT_ENABLE_ADMIN-Feature in dem Paket hinzugefügt haben, melden Sie sich mit Administrator/p@ssw0rd. , die Wenn Sie einen benutzerdefinierten Benutzernamen und ein Kennwort erstellt haben, nun verwenden. Finden Sie weitere Informationen finden Sie unter [Übung 1 b: Hinzufügen einer app zu Ihr Bild](deploy-your-app-with-a-standard-board.md).

Testen der app durch Installieren von It **

1.  Klicken Sie auf **Apps**.

2.  Klicken Sie unter **app installieren**, klicken Sie unter **App-Paket**klicken Sie auf **Durchsuchen**, und wählen Sie die Datei .appx.
    **Hinweis**  Wenn Sie Ihre app als ein Paket erstellt haben, müssen Sie einem Tool wie 7-Zip verwenden, um diese Dateien aus dem Paket zu extrahieren.

3.  Fügen Sie Ihrer app- **Zertifikat** die gleiche Weise hinzu.

4.  Klicken Sie auf **Abhängigkeit hinzufügen** , und fügen Sie alle Dateien aus Ihrer app Abhängigkeit.

5.  Klicken Sie unter **Deploy**klicken Sie auf **OK**. Die app installiert.

6.  Klicken Sie unter **Installed apps**auf das Dropdown-Feld, und wählen Sie Ihre app. Ihre app muss auf dem Gerät starten.

Umfangreiche, funktioniert die app! Jetzt wir packen, damit Sie Ihre app auch nach Ihren Kunden übermittelt wird beibehalten können.
