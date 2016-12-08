---
author: Justinha
Description: "Windows im Überwachungsmodus oder OOBE Boot"
ms.assetid: a928dea9-52b1-42b9-bee1-cbe9c8c0b07b
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows im Überwachungsmodus oder OOBE Boot"
ms.openlocfilehash: 16b0a5a0064abdbbd608892f1b1d257fc04fa1f8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-windows-to-audit-mode-or-oobe"></a>Windows im Überwachungsmodus oder OOBE Boot


Sie können im Überwachungsmodus Anpassen des Computers, Anwendungen und Gerätetreiber hinzufügen und Testen Sie den Computer in einer Windows-Umgebung verwenden. Starten im Überwachungsmodus startet den Computer in das integrierte Administratorkonto. Windows® entfernt dieses Konto automatisch während der Konfiguration [verallgemeinern](generalize.md) übergeben. Nachdem Sie einen Computer auf Start im Überwachungsmodus konfiguriert haben, wird der Computer weiterhin boot-Modus standardmäßig überwacht, bis Sie konfigurieren Sie den Computer zum Out-Of-Box-Experience (OOBE) starten, wenn der Computer an den Benutzer verwendet werden soll.

Wenn ein kennwortgeschützte Bildschirmschoner gestartet wird, wenn Sie im Überwachungsmodus aktiviert sind, können nicht Sie wieder an das System anmelden. Das integrierten Administratorkonto, das verwendet wird, um melden Sie sich im Überwachungsmodus wird unmittelbar nach der Anmeldung deaktiviert. Zum Deaktivieren des Bildschirmschoners entweder Power planen über die Windows-Systemsteuerung zu ändern oder konfigurieren und Bereitstellen eines benutzerdefinierten Plans. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Power planen](create-a-custom-power-plan-technicalreference.md).


## <a name="span-idbkmk1spanspan-idbkmk1spanboot-to-audit-mode-automatically-on-a-new-installation"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Automatisch in einer neuen Installation im Überwachungsmodus starten


-   Fügen Sie zum Konfigurieren von Windows für das Starten im Überwachungsmodus der **Microsoft Windows-Deployment | Reseal | Mode = Audit** Datei-Einstellung zu beantworten.

    Abschluss der Installation wird der Computer in Windows im Überwachungsmodus automatisch startet und das System Vorbereitungstool (**Sysprep**) angezeigt. Weitere Informationen zur Verwendung des Tools Sysprep im Überwachungsmodus aktiviert finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

    **Hinweis**  
    Einstellungen in einer Antwortdatei aus **der Konfigurationsphase** werden nicht im Überwachungsmodus aktiviert angezeigt. Weitere Informationen über welche Antwort dateieinstellungen beim Start Modus oder OOBE überwachen verarbeitet werden, finden Sie unter [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md).

     

## <a name="span-idbkmk2spanspan-idbkmk2spanboot-to-audit-mode-manually-on-a-new-or-existing-installation"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>(Auf einem neuen oder vorhandenen Installation) manuell im Überwachungsmodus starten


-   Drücken Sie **STRG**, auf dem Bildschirm OOBE+**UMSCHALT**+**F3**.

    Windows startet den Computer im Überwachungsmodus neu, und das System Preparation (**Sysprep**) Tool wird angezeigt.

    **Hinweis**  
    Die **STRG**+**UMSCHALT**+**F3** Tastenkombination wird nicht alle Teile des Prozesses OOBE umgangen, wie das Ausführen von Skripts und Anwenden von Antwort dateieinstellungen in der Konfiguration **OobeSystem** übergeben.

     

## <a name="span-idbkmk3spanspan-idbkmk3spanboot-to-oobe-automatically-on-a-new-installation"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>Starten Sie das OOBE automatisch in einer neuen installation


-   Fügen Sie zum Konfigurieren von Windows für das OOBE Starten der **Microsoft-Windows-Deployment | Reseal |** **Modus** **= Oobe** Antwort Datei Einstellung.

    Wenn Sie das Windows-Abbild OOBE Starten konfiguriert haben, aber dann Sie weitere Konfigurationen für das Abbild im Überwachungsmodus aktiviert müssen, finden Sie unter [Ändern einer vorhandenen Bild, d. h., die zum Starten OOBE konfiguriert](#bkmk-4).

## <a name="span-idbkmk4spanspan-idbkmk4spanmodify-an-existing-image-that-is-configured-to-boot-to-oobe"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Ändern eines vorhandenes Abbilds konfiguriert ist, die zum Starten OOBE


-   Wenn Sie das Windows-Abbild um OOBE starten, jedoch dann müssen Sie für das Abbild weitere Konfigurationen im Überwachungsmodus konfiguriert haben, können Sie einen der folgenden Möglichkeiten:

    1.  Verwenden Sie die **STRG**+**UMSCHALT**+**F3** Tastenkombination zugeordnet. Der Computer wird im Überwachungsmodus neu gestartet.

        Diese Option kann eine beliebige Skripts ausgelöst werden, die Sie konfiguriert haben, um in OOBE zu starten.

        \endash oder \endash

    2.  Stellen Sie das Abbild, hinzufügen eine Antwortdatei mit der Einstellung **Überwachen** , und speichern sie als **C:\\testen\\offline\\Windows\\Panther\\unbeaufsichtigte Installation\\Unattend.xml**. Dies erfordert möglicherweise Überschreiben einer vorhandenen Antwortdatei an folgendem Speicherort.

        Nächsten Starten wird Windows direkt im Überwachungsmodus gestartet.

## <a name="span-idbkmk5spanspan-idbkmk5spanboot-to-audit-mode-automatically-from-an-existing-image"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>Automatisch aus einem vorhandenen Bild im Überwachungsmodus starten


1.  Erstellen einer neuen Antwortdatei, und fügen Sie die Microsoft Windows-Deployment **| Reseal | Mode = Audit** Einstellung. Speichern Sie die Antwortdatei als **Unattend.xml**.

2.  Binden Sie an einer Eingabeaufforderung mit erhöhten Rechten das Windows-Abbild. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /index:<image_index> /MountDir:C:\test\offline
    ```

    dabei * &lt;Bild\_Index&gt; * ist die Anzahl der das ausgewählte Bild auf der WIM-Datei.

3.  Kopieren Sie die neue Antwortdatei auf dem **C:\\testen\\offline\\Windows\\Panther\\Ordner für die unbeaufsichtigte Installation**.

4.  Commit der Änderungen, und klicken Sie dann das Bild entladen. Beispiel:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /commit
    ```

    Wenn das Bild auf den Zielcomputer und Windows angewendet wird gestartet wird, startet der Computer im Überwachungsmodus automatisch, und das **Sysprep** -Tool wird angezeigt. Beispiel finden Sie unter Schritt 1: übertragen ein Abbilds auf einen anderen Computer und Schritt2: Vorbereiten den Computer für einen Kunden in [Bereitstellungsbeispiele](#bkmk-6).

Optionen zum Anwenden der Schwelle zählen auch die Verwendung der Antwort dateieinstellungen wie das Abbild zu installieren und die Konfigurationen vornehmen auf dem Zielcomputer angeben. Weitere Informationen finden Sie im [Unbeaufsichtigten Windows Setup-Referenzhandbuch](http://go.microsoft.com/fwlink/?linkid=206281).

## <a name="span-idbkmk6spanspan-idbkmk6spandeployment-examples"></a><span id="bkmk_6"></span><span id="BKMK_6"></span>Bereitstellungsbeispiele


Um ein Bild auf einem anderen Computer zu übertragen, müssen Sie die computerspezifische Informationen vom konfigurierten Computer zuerst Verallgemeinern des Image mit dem **Sysprep** -Tool entfernen. Sie müssen zum Vorbereiten eines Computers für den Kunden Verallgemeinern des Computers und legen Sie es OOBE beim Kunden des Computers zum ersten Mal starten starten. In den folgenden Beispielen erstellen wir und übertragen ein Bild Verweis auf einen anderen Computer, und erstellen Sie ein Modell-spezifisches Bild, die an einen Kunden ausgeliefert wird.

**Schritt 1: Übertragen eines Bilds auf einem anderen computer**

1.  Installieren Sie Windows auf einem Referenzcomputer.

2.  Nachdem die Installation abgeschlossen ist, starten Sie den Computer, und installieren Sie keine zusätzlichen Treiber oder Applications.

3.  Nach dem Aktualisieren der Windows-Installations, führen Sie **Sysprep aus**:

    -   Führen Sie an der Befehlszeile die **Sysprep / / Shutdown verallgemeinern** Befehl.

        \endash oder \endash

    -   Aktivieren Sie im Fenster Systemvorbereitungstool das Kontrollkästchen **verallgemeinern** unter dem Feld **Systembereinigungsaktion** auf das Feld **Optionen für Herunterfahren** , wählen Sie **Herunterfahren,**und klicken Sie dann auf **OK**.

    **Sysprep** entfernt-spezifische Daten aus der Windows-Installation. System-spezifische Informationen enthält Ereignisprotokolle eindeutige Sicherheits-IDs (SIDs) und andere individuellen Informationen. Nachdem **Sysprep** die eindeutigen Systeminformationen entfernt, wird der Computer heruntergefahren.

4.  Nach dem Herunterfahren des Computers, legen Sie das Windows PE USB flash-Laufwerk oder anderen startbaren Medium, und starten Sie in Windows PE.

5.  Erfassen Sie das Bild Verweis in der Windows PE-Sitzung mithilfe des Befehls **Dism /capture-image** .

6.  Fahren Sie fort mit dem nächsten Schritt zum Erstellen eines Abbilds Modell-spezifisches Reference.

**Schritt 2: Vorbereiten des Computers für einen Kunden**

1.  Installieren Sie den Verweis-Bilddatei, den Sie in Schritt 1 erstellt haben, die für Ihren Kunden bestimmt ist.

2.  Nach dem Aktualisieren der Windows-Installations, an der Befehlszeile Ausführen der **Sysprep/überwachen / / Shutdown verallgemeinern** Befehl zum Konfigurieren von Windows zum Starten des Computers im Überwachungsmodus. Dann können Sie das Windows-Abbild auf eine andere Partition starten oder mithilfe von Windows PE erfassen.

3.  Verwenden Sie das neue Modell-spezifisches Referenzabbild zum Installieren von Windows auf einem neuen Computer. Das Windows-Abbild auf dem Computer installiert ist, und Windows im Überwachungsmodus gestartet wird.

4.  (Optional) Sie können zusätzliche Applikationen und andere Updates basierend auf einem Kunden Reihenfolge installieren. Sie können auch testen Sie den Computer, um sicherzustellen, dass alle Komponenten ordnungsgemäß konfiguriert sind.

5.  Nachdem Sie die Windows-Installation aktualisiert haben, führen Sie den **Sysprep/OOBE/Shutdown-Befehl**.

    **Hinweis**  
    Wenn Sie mithilfe von Windows-Abbilder Installieren der **Sysprep / / OOBE verallgemeinern** Befehl wird die Benutzeroberfläche nicht ideal sein. Beim nächsten Neustart nach dem Ausführen der **Sysprep / / OOBE verallgemeinern** Befehl Windows ausgeführt wird, übergeben Sie die Konfiguration **specialize** Plug & Play und andere Setupaufgaben vor dem Start von Windows OOBE. Dieser Prozess kann zusätzliche Zeit in Anspruch nehmen und erste Anmeldung eines Kunden verzögern kann.

     

6.  Packen Sie und liefern Sie den Computer für den Kunden.

    Wenn der Kunde den Computer gestartet wird, wird OOBE ausgeführt.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Hinzufügen eines Treibers Online im Überwachungsmodus](add-a-driver-online-in-audit-mode.md)

[Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos](enable-and-disable-the-built-in-administrator-account.md)

[Starten Sie von einer DVD](boot-from-a-dvd.md)

[Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

[Bereitstellen eines benutzerdefinierten Abbilds](deploy-a-custom-image.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md)

 

 






