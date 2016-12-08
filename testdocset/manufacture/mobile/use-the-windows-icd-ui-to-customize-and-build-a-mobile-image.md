---
Description: "Sie können Windows Imaging und Konfiguration Designer (ICD) Benutzeroberfläche verwenden, erstellen ein neues Windows 10 Mobile Bild und passen Sie es durch Hinzufügen von Einstellungen und einige Elemente."
ms.assetid: bf897b96-2ab4-42c0-b825-34e7979b3761
MSHAttr: PreferredLib:/library
title: "Mithilfe der Windows ICD Benutzeroberfläche anpassen und Erstellen einer mobilen Bild"
author: CelesteDG
ms.openlocfilehash: 0ac852099a0c334fc35fd4030dac9d4657b2f5ee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-windows-icd-ui-to-customize-and-build-a-mobile-image"></a>Mithilfe der Windows ICD Benutzeroberfläche anpassen und Erstellen einer mobilen Bild


Sie können Windows Imaging und Konfiguration Designer (ICD) Benutzeroberfläche zum Erstellen eines neuen Windows 10 Mobile Bilds, und passen sie durch Hinzufügen von Einstellungen und einige Ressourcen verwenden.

Diese imaging-Methode erfordert eine vorinstallierte OS Kit müssen Sie alle notwendigen Microsoft OS Pakete und Features in Ihrem standardmäßigen Manifestdateien verfügen Installationspfad. Eine Konfiguration-Datendatei (BSP.config.xml), die Informationen über die Hardware-Komponente-Pakete für Ihre Pinnwand Support-Paket (BSP) enthält, ist auch erforderlich. Für die Datei BSP.config.xml ermöglichen Folgendes:

-   Verwenden Sie die BSP.config.xml-Datei, die Sie heruntergeladen haben als Teil der BSP-Kit, oder

-   Generieren Sie Ihre eigene BSP.config.xml durch Ausführen von das BSP Kit Konfigurationstools SoC dessen Hersteller und die Komponententreiber auswählen.

## <a name="span-idtobuildamobileimageusingthewindowsicduispanspan-idtobuildamobileimageusingthewindowsicduispanbuild-a-mobile-image-using-the-windows-icd-ui"></a><span id="to_build_a_mobile_image_using_the_windows_icd_ui"></span><span id="TO_BUILD_A_MOBILE_IMAGE_USING_THE_WINDOWS_ICD_UI"></span>Erstellen einer mobilen Abbilds mithilfe der Windows-ICD-Benutzeroberfläche


In dieser exemplarischen Vorgehensweise veranschaulicht mithilfe der Windows-ICD-Benutzeroberfläche anzupassen, erstellen und einer mobilen Bild flash.

1.  Wählen Sie auf der Seite Windows ICD starten aus, **neue Windows-Abbild Anpassung**.

    Oder Sie können auch **Neues Projekt...** wählen Sie im Menü **Datei** .

2.  Geben Sie im Fenster **Projektdetails Geben Sie** einen **Namen** und **Speicherort** für das Projekt ein. Optional können Sie auch eine kurze **Beschreibung** zur Beschreibung von Ihrem Projekts eingeben.

3.  Klicken Sie auf **Weiter**.

4.  Wenn Sie auf der Startseite des Projekts erstellt haben, überspringen Sie diesen Schritt.

    Klicken Sie im Fenster **Wählen Sie Project Workflow** aus der Liste der verfügbaren Workflows wählen Sie **Imaging** , und klicken Sie dann auf **Weiter**.

5.  Klicken Sie im Fenster **Wählen Sie imaging Quellformat** wählen Sie aus **der Windows-Abbild basiert auf Microsoft-Pakete**, und klicken Sie dann auf **Weiter**.

    Sie werden aufgefordert, eine BSP.config.xml-Datei an.

6.  Klicken Sie auf **Durchsuchen** , um die Datei-Explorer und suchen Sie nach dem Speicherort der Datei BSP.config.xml starten, klicken Sie im Fenster **Wählen Sie Hardware-Komponententreiber** .

7.  Klicken Sie auf **Fertig stellen**.

    Dadurch wird geladen, Anpassungen, die Sie konfigurieren können basierend auf der Windows-Edition, die Sie ausgewählt haben. Nachdem alle verfügbaren Anpassungen geladen werden, können Sie die **Anpassungen Seite**angezeigt.

8.  Wählen Sie auf der **Seite Anpassungen**die Einstellungen, die Sie aus dem Bereich **Verfügbare Anpassungen** anpassen möchten.

    In dieser exemplarischen Vorgehensweise finden Sie unter [Configure Anpassungen in der Windows-ICD-Benutzeroberfläche](#configure-customizations-in-the-windows-icd-ui) für eine Liste mit den Einstellungen, die wir als Beispiele verwenden. Sobald Sie fertig sind Konfigurieren der Einstellungen, mit dem nächsten Schritt fortfahren.

9.  Zwar optional, Exportieren eines provisioning Pakets zum Kapseln der Einstellungen, die Sie soeben konfiguriert haben, und ermöglichen es Ihnen, alle oder die meisten Anpassungen nach einem anderen Projekt wiederverwenden.

    Zu diesem Zweck klicken Sie auf die Dropdownliste **Exportieren** im Hauptmenü **Provisioning-Paket**aus, fügen Sie die erforderlichen Paketinformationen hinzu.

    -   **Name** – Name, der für das Paket verwendet *Contoso\_Ppkg*.
    -   **ID** - Paket automatisch generierten GUID.
    -   **Besitzer** - Paketbesitzer. Legen Sie auf *OEM*.
    -   **Version** - Versionsinformationen. Dies ist bereits ausgefüllte mit den neuesten Paket Versionsnummer oder "1.0". Lassen Sie es auf die Standardeinstellung *1.0*, festlegen, obwohl Sie es auf eine beliebige Version festlegen können, die Sie möchten.
    -   **Rank** - Paket Rang, die einen Wert zwischen 0 und 99 (einschließlich) ist. Lassen Sie es standardmäßig auf *0*festgelegt.

    Klicken Sie auf **Weiter** , bis Sie auf dem Bildschirm **Erstellen Sie das Paket Bereitstellung** erhalten. Klicken Sie auf **Erstellen** , um das Paket zu erstellen, und klicken Sie dann auf **Fertig stellen**.

10. Wählen Sie im Hauptmenü **Erstellen** aus, und wählen Sie dann **FFU**.

11. Wählen Sie im Bildschirm **Wählen Sie Bildtyp** **Test** für den Typ des Bilds.

    Zwar andere Arten, eignet sich ein Bild Testtyp Wenn Ihr Bild noch nicht endgültige ist und Sie weiterhin verschiedenen Komponenten in Ihrem Bild testen. Das Bild wird auch nicht gesperrte und keine Bescheide Sicherheit enthalten.

12. Klicken Sie auf **Weiter**.

13. Wählen Sie im Bildschirm **beschreiben das Bild** der Sprachen, die Sie als Teil Ihres Bilds einschließen möchten.

    Wenn Sie weitergeleitet wurde [Teil 1: mobile Bereitstellung Classic](lab-1--classic-mobile-deployment.md), werden die Einstellungen in diesem Schritt ähnlich wie würden Sie die Gerät Sprachen unter [Konfigurieren der Datei OEMInput](configure-the-oeminput-file.md)festgelegt.

    -   **Sprache der Benutzeroberfläche** - Hierbei handelt es sich um die Anzeige Sprache(n) auf dem Gerät installiert.

        Wählen Sie *En-gb*, *En-us*, *es-es*, *fr-fr*und *Zh-Cn*.

    -   **Tastatursprachen** - Dies sind zusätzliche Tastatursprachen für die Textkorrektur und Vorschläge verwenden, bei der Eingabe auf dem Gerät.

        Wählen Sie *En-us*.

    -   **Die Sprachen** - Hierbei handelt es sich um die Sprache Sprachen, die auf dem Gerät installiert werden soll.

        Wählen Sie *En-us*.

14. Da wir mehrere Sprachen in der **Sprache der Benutzeroberfläche**ausgewählt haben, müssen wir die Standardsprache für die Anzeige auszuwählen, die das Gerät verwendet wird, wenn sie zuerst durch den Benutzer aktiviert ist. Zu diesem Zweck wählen Sie **Boot Sprache** , und wählen Sie die Standardsprache für das Gerät, die Sie festlegen möchten. Legen Sie dies beispielsweise auf *En-us*.

15. Wenn Land oder Region festlegen möchten, wählen Sie **Start Gebietsschema** , und wählen Sie das Gebietsschema für die Standardregion oder jedes Land. Eine beliebige Gebietsschema als regionalen Format verwendet werden kann, jedoch nur der Wert für das Land (GeoID) wird verwendet. Legen Sie dies beispielsweise auf *En-us*.

16. Klicken Sie auf **Weiter**.

17. Zum Ändern des Speicherorts, in dem die Dateien gespeichert sind, klicken Sie auf **Durchsuchen...** unter **Wählen Sie, wo die Dateien gespeichert werden**.

    Ändern des Speicherorts kann, in dem die Dateien gespeichert werden, aber in der Regel der Standardspeicherort ist kein Problem.

18. Optional Wenn Sie eine CAF Datei durch die folgenden [administrativen Anpassung konfigurieren](configure-customization-settings.md)erstellt haben, können Sie dies durch die Option unter **Anpassung Antwortdatei (optional)** **Suchen...** und zum Angeben des Speicherorts der CAF einschließen.

    Beispielsweise *C:\\Contoso\\Anpassungen\\MobileCustomizations.xml*.

19. Um am Standardspeicherort zu ändern, wo Sie das Bild speichern möchten, klicken Sie auf **Durchsuchen** , um die Datei-Explorer zu starten, und geben Sie einen neuen Speicherort.

    Klicken Sie auf **Weiter**, um am Standardspeicherort zu verwenden.

20. Klicken Sie auf **Erstellen** , um das Bild erstellen. Die Project-Informationen in der Build-Seite angezeigt wird und die Statusanzeige gibt den Status des Build an.

    Wenn Sie den Build abbrechen müssen, klicken Sie auf **Abbrechen**. Dadurch wird das aktuelle Build abgebrochen, wird der Assistent geschlossen und gelangen Sie zurück zur **Seite Anpassungen**.

21. Den Erstellungsvorgang Bild wird im Fenster Ausgabe Build viel was passiert den Erstellungsvorgang angezeigt. In diesem Fenster werden:

    -   Warnungen, die während der Erstellung des Abbilds angezeigt werden können.

    -   Nachrichten an, dass die Phasen im Image verbose Build erstellen Prozess.

    -   Fehlermeldungen wie bei die Eingabe Dateien Schema fehlerhaft sind oder wenn das Bild nicht erstellen.

    Wenn Sie der Build ein Fehler auftritt, wird eine Fehlermeldung ausgegeben. Sie können das Buildprotokoll, um das Problem zu identifizieren, indem Sie auf **Ansicht in Editor**ansehen.

    Wenn der Build erfolgreich ist, wird der Name des Bilds und seinen Speicherort angezeigt.

    -   Wenn Sie auswählen, können Sie das Bild durch einen anderen Bildtyp Entnahme, unterschiedliche Sprachen auswählen, und starten Sie einen anderen Build erneut erstellen. Zu diesem Zweck, klicken Sie auf **wieder** aktivieren, was Sie ändern möchten, und klicken Sie dann auf **Weiter** , um eine andere Build zu starten.

    -   Starten Sie das Gerät im Bild oder FFU Download-Modus. So erzwingen Sie das Telefon in Abbild oder FFU Downloadmodus manuell, drücken und halten, um Telefon neu starten, und klicken Sie dann sofort drücken und halten die Lautstärke Schaltfläche nach oben. Beachten Sie, dass diese Option verfügbar ist, nachdem eine anfängliche FFU wurde auf dem Telefon aktualisiert wurde.

        Wenn dies nicht funktioniert, überprüfen Sie, und befolgen Sie das Anweisungen des Herstellers SoC blinkendes Gerät.

    -   Wenn Sie das erstellte Bild auf Ihrem Gerät blinkt bereit sind, klicken Sie auf **Flash** , und wählen Sie das Zielgerät blinkt die FFU. Wenn Sie das Gerät in der Liste der verfügbaren Ziel Geräte nicht finden, klicken Sie auf **Aktualisieren**.

        Wenn Sie das Bild, das das Gerät später flash möchten, führen Sie die Schritte unter [Deploy eines Bilds zu einem mobilen Gerät](#deploy-an-image-to-a-mobile-device) , wenn Sie das Bild auf Ihrem Gerät blinkt bereit sind.

        Es dauert ein paar Minuten, damit das Bild vollständig auf das Gerät aktualisiert werden. Nach Abschluss der blinken Geräteinstallation durchlaufen, und stellen Sie sicher, dass die Anpassungen als Teil des Bilds angezeigt werden.

    -   Wenn Sie fertig sind, klicken Sie auf **Fertig stellen** , um den Assistenten zu schließen, und gehen Sie zurück zur **Seite Anpassungen**.

## <a name="span-idconfigurecustomizationsinthewindowsicduispanspan-idconfigurecustomizationsinthewindowsicduispanconfigure-customizations-in-the-windows-icd-ui"></a><span id="configure_customizations_in_the_windows_icd_ui"></span><span id="CONFIGURE_CUSTOMIZATIONS_IN_THE_WINDOWS_ICD_UI"></span>Konfigurieren von Anpassungen in der Windows-ICD-Benutzeroberfläche


**Hinweis**  Verwenden Sie die **Bild-Zeiteinstellungen**, verwenden Sie stattdessen die **Laufzeit Einstellungen** nicht, beim Konfigurieren von Windows ICD Anpassungen. Wenn Sie die Bild-Time-Einstellungen konfigurieren, verursacht dadurch einen Fehler aufgrund von einem Konflikt Einstellungen, wenn die Einstellung in WPAF und MCSF CAF konfiguriert ist.

 

Wenn Sie dies noch nicht getan haben müssen Sie zuerst die LayoutModification.xml Dateien erstellen, wie unter [Konfigurieren des Layouts Start](configure-the-start-layout.md) vor dem Fortfahren mit den Schritten in diesem Abschnitt dargestellt.

**So konfigurieren Sie das Start-layout**

1.  Klicken Sie im Bereich **Verfügbare Anpassungen** in Windows ICD erweitern Sie **Runtime Einstellungen**, wählen Sie **Start**aus und wählen Sie dann **StartLayout**aus.

2.  Klicken Sie im mittleren Bereich auf **Durchsuchen** , um die Datei-Explorer öffnen.

3.  Klicken Sie im Datei-Explorer navigieren Sie zu dem Speicherort LayoutModification1.xml aus Schritt 1; beispielsweise *C:\\Contoso\\Anpassungen*.

4.  Wählen Sie LayoutModification1.xml aus, und klicken Sie dann auf **Öffnen**.

    Hierdurch wird des Werts der **StartLayout** , und die Einstellung der **ausgewählte Anpassungen** Seite angezeigt werden soll.

Enterprise-Richtlinien und Einstellungen für die Registrierung sind einige der Anpassungen, die nur über die Windows-Bereitstellung zur Verfügung. Konfigurieren Sie hier, wenige diese Richtlinien als Teil des Bilds. Weitere Informationen zu anderen Richtlinien, die Sie konfigurieren können, finden Sie unter [Richtlinien](https://msdn.microsoft.com/library/windows/hardware/dn965797) (die Einstellungen für die Windows-Bereitstellung). Beachten Sie, dass die Windows-Bereitstellung Einstellungen Themen keine detaillierte Beschreibung der einzelnen Richtlinien bieten. Stattdessen verknüpft in jedem Thema mit Informationen im [Bereich CSP Richtlinie](https://msdn.microsoft.com/library/windows/hardware/dn904962).

**Zum Festlegen von Richtlinien**

1.  Klicken Sie im Bereich **Verfügbare Anpassungen** Einstellungen Sie **Runtime**-, und wählen Sie **Richtlinien**.

2.  Hier finden Sie **Richtlinien/DeviceLock** , und **MaxInactivityTimeDeviceLock** auf "15" festgelegt.

    Dies gibt an, dass nach das Gerät 15 Minuten im Leerlauf befunden hat, das Gerät PIN oder das Kennwort gesperrt wird.

3.  Hier finden Sie **Richtlinien/DeviceLock** und **ScreenTimeoutWhileLocked** auf "15" festgelegt.

    Dies gibt die Dauer in Sekunden für das Timeout für klicken Sie auf dem Sperrbildschirm an. In diesem Beispiel wird die Dauer 15 Sekunden.

## <a name="span-iddeployanimagetoamobiledevicespanspan-iddeployanimagetoamobiledevicespanspan-iddeployanimagetoamobiledevicespandeploy-an-image-to-a-mobile-device"></a><span id="Deploy_an_image_to_a_mobile_device"></span><span id="deploy_an_image_to_a_mobile_device"></span><span id="DEPLOY_AN_IMAGE_TO_A_MOBILE_DEVICE"></span>Bereitstellen eines Bilds zu einem mobilen Gerät


Gehen Sie folgendermaßen vor, wenn Sie das Bild, das das Gerät blinkt, nachdem es erstellt wurde zurückgestellt.

1.  Starten Sie das Gerät im Bild oder FFU Download-Modus. So erzwingen Sie das Telefon in Abbild oder FFU Downloadmodus manuell, drücken und halten, um Telefon neu starten, und klicken Sie dann sofort drücken und halten die Lautstärke Schaltfläche nach oben. Beachten Sie, dass diese Option verfügbar ist, nachdem eine anfängliche FFU wurde auf dem Telefon aktualisiert wurde.

    Wenn dies nicht funktioniert, überprüfen Sie, und befolgen Sie das Anweisungen des Herstellers SoC blinkendes Gerät.

2.  Verbinden Sie Ihr Telefon über ein USB-Kabel an, auf den Hostcomputer.

3.  Klicken Sie im Hauptmenü auf **Bereitstellen** , und wählen Sie zum Bereitstellen von FFU Bild auf das Gerät **zu USB-Gerät angeschlossen** .

4.  Klicken Sie im Fenster **Wählen Sie ein Bild FFU** Datei-Explorer zu starten, und wählen Sie die FFU die gewünschte auf Ihr Zielgerät flash auf **Durchsuchen...,** und klicken Sie dann auf **Weiter**.

5.  Wählen Sie das Zielgerät oder Laufwerk aus der Liste aus. Wenn Ihr Gerät oder Laufwerk nicht aufgeführt ist, klicken Sie auf **Aktualisieren**.

6.  Klicken Sie auf **Weiter**.

7.  Wählen Sie im Fenster **Deploy Gerät** **Flash** um das Bild blinkt zu starten.

8.  Klicken Sie auf **Fertig stellen,** der zum Schließen der Seite für die **Bereitstellung** .

 

 



