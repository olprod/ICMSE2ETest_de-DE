---
author: kpacquer
Description: "Reset-Schutz können Sie die ein Gerät für den Fall, dass es Diebstahl zu sichern. Es muss auf dem Gerät während der Zeit manufacturing aktiviert sein."
ms.assetid: d9cd4f83-fb29-47cb-b26f-e82eb4d3bee8
MSHAttr: PreferredLib:/library/windows/hardware
title: Reset-Schutz
ms.openlocfilehash: 822cf411e43c1fd13c24761964ddee68463fb685
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reset-protection"></a>Reset-Schutz


Zurücksetzen Schutz können Sie ein Gerät für den Fall, dass es Diebstahl secure. Es muss auf dem Gerät während der Zeit manufacturing aktiviert sein.

Zurücksetzen Schutz besteht aus den folgenden Teilen:

-   **Zurücksetzen und zur Reaktivierung Protection** – gestohlenen Geräts kann nicht durch Zurücksetzen oder des Geräts blinken wiederverwendet werden. Wenn ein Benutzer eine Factory zurücksetzen auf dem Gerät ausgeführt wird, werden sie aufgefordert, die Microsoft Account Anmeldeinformationen eingeben, die diesem Gerät zugeordnet sind. Darüber hinaus wird, wenn das Gerät mit dem neuen Bild blinkt und Zurücksetzen Schutz aktiviert ist, die Microsoft Account-Anmeldeinformationen, die zugeordnet wurden dieses Gerät erforderlich, um vollständig OOBE und verwenden Sie das Gerät.
-   **Anti-Rollback Protection** – Wenn zurücksetzen Schutz aktiviert ist, gestohlenen Geräts kann nicht in einer früheren Version des Betriebssystems, die nicht zurücksetzen Schutz aktualisiert werden.

Zum Zurücksetzen von Schutz aktivieren möchten, müssen Sie zwei Variablen für sichere UEFI konfigurieren:

-   **ANTI\_DIEBSTAHL\_AKTIVIERT** – diese Variable muss mit einem Wert festgelegt werden, die von Microsoft bereitgestellt werden und gibt an, dass das Gerät zurücksetzen Schutz unterstützen können. Das Betriebssystem ermöglicht den Schutz zurücksetzen auf dem Gerät auf Grundlage dieser Einstellung. Diese Variable wird in den 1A597235-6378-4910-9F8B-720FEE9357A3-Namespace.
-   **DBX** - diese Variable muss die Hashes Bild der Builds enthalten, zu dem das Gerät rückgängig gemacht werden kann. Diese Bild Hashes werden von Microsoft bereitgestellt. Diese Variable wird in der EFI\_BILD\_SECURITY\_DATENBANK\_GUID-Namespace.

## <a name="span-idturnonresetprotectioninyourimagesspanspan-idturnonresetprotectioninyourimagesspanspan-idturnonresetprotectioninyourimagesspanturn-on-reset-protection-in-your-images"></a><span id="Turn_on_Reset_Protection_in_your_images"></span><span id="turn_on_reset_protection_in_your_images"></span><span id="TURN_ON_RESET_PROTECTION_IN_YOUR_IMAGES"></span>Einschalten des Schutzes zurücksetzen in Bildern


Es gibt zwei Methoden, um die Reset-Schutz in Ihren Bildern zu aktivieren:

**Option 1: Aktivieren sie mithilfe von oeminput.xml**

Auf Geräten Retail Sie Protection Zurücksetzen aktivieren, indem Sie das ZURÜCKSETZEN\_PROTECTION-Feature in der Datei OEMInput.xml. Wenn Sie dieses Feature einschließen, werden das Gerät UEFI sicheren Boot-Schlüsseln für Schutz zurücksetzen als geplante Aufgabe bereitgestellt, die wird einmal in Hauptfenster Betriebssystem beim ersten Start ausgeführt und wird nicht erneut ausgeführt. Weitere Informationen zu den optionalen Features, die verfügbar sind, finden Sie unter O[optionale Features zum Erstellen von Bildern](https://msdn.microsoft.com/library/windows/hardware/dn756780).

**Hinweis**  Wenn Sie ein Testbild erstellen, verwenden Sie ZURÜCKSETZEN\_SCHUTZ\_INTERNAL stattdessen.

 

**Option 2: Aktivieren Sie beim Bereitstellen von sicheren Boot-Schlüssel**

Zurücksetzen Schutz provisioning UEFI sicheren Boot-Schlüssel auf einem Gerät aktiviert ist und umfasst zwei Schritte:

1.  **Anti-Rollback Bereitstellung** – die DBX-Variable muss aktualisiert werden, um die Hashes für die Builds enthalten, die nicht Schutz zurückgesetzt unterstützte. Insbesondere werden Beispielskripts, die Variablen PK, KEK, DB und DBX erstellen geändert werden, um in der Variablen DBX die Liste des von Microsoft bereitgestellten weiteren hinzuzufügen. Die Liste des weiteren wird von Microsoft in einer Datei namens angegeben werden **OEM\_RollbackHashes.bin**. Die DBX-Variable muss mit dem OEM-Zertifikat signiert werden.

    Im folgenden Auszug enthält die Änderungen an das Skript, das die Variable DBX erstellt:

    ``` syntax
    write-progress -activity "Making secure boot variables" -status "Creating DBX"
# add SHA256 hashes from the supplied file to the DBX variable
    $hashes = Get-Content .\OEM_RollbackHashes.bin
    format-sb-hashes "dbx" $ownerGuid $hashes
    ```

2.  **Zurücksetzen und Reaktivierung Protection provisioning** – nach dem Einrichten der Variablen DBX müssen Sie auch festlegen ANTI\_DIEBSTAHL\_authentifizierten Variable AKTIVIERT. Der Inhalt der Variablen erhalten Sie von Microsoft in der **OEM\_ResetProtection\_aktivieren\_Resource.bin** Datei. Der Name der Variablen ist ANTI\_DIEBSTAHL\_AKTIVIERT und die Namespace-GUID 1A597235-6378-4910-9F8B-720FEE9357A3 ist. Sie können dies auf die gleiche Weise wie die sicheren Boot-Schlüssel festlegen.

## <a name="span-idhowdoiupdatearetailimagewithresetprotectionspanspan-idhowdoiupdatearetailimagewithresetprotectionspanspan-idhowdoiupdatearetailimagewithresetprotectionspanhow-do-i-update-a-retail-image-with-reset-protection"></a><span id="How_do_I_update_a_retail_image_with_Reset_Protection_"></span><span id="how_do_i_update_a_retail_image_with_reset_protection_"></span><span id="HOW_DO_I_UPDATE_A_RETAIL_IMAGE_WITH_RESET_PROTECTION_"></span>Wie aktualisiere ich ein Bild Retail mit Protection zurücksetzen?


Wenn Sie ein Update übermitteln, sollte zurücksetzen Schutz kein Bestandteil des Updates sein. Wenn Sie Bild erstellen, sollten Protection zurücksetzen in der Datei oeminput.xml enthalten sein. Es wird empfohlen, die folgenden Schritte zur ein Abbild Retail mit aktiviertem zurücksetzen Schutz aktualisieren:

1.  Beim Entwickeln eines Bilds, das ZURÜCKSETZEN\_PROTECTION optionale Funktion in der Datei oeminput.xml eingeschlossen sein soll.
2.  Bevor Sie die Pakete für die Signierung senden, sollten Sie das ZURÜCKSETZEN entfernen\_PROTECTION optionale Funktion aus der Datei oeminput.xml.
3.  Nachdem Sie die Pakete, die von Microsoft signiert erhalten haben, müssen Sie das ZURÜCKSETZEN hinzufügen\_PROTECTION optionale Funktion wieder auf Ihre oeminput.xml-Datei.

## <a name="span-idbootablewimfilesandmmosspanspan-idbootablewimfilesandmmosspanspan-idbootablewimfilesandmmosspanbootable-wim-files-and-mmos"></a><span id="Bootable_WIM_files_and_MMOS"></span><span id="bootable_wim_files_and_mmos"></span><span id="BOOTABLE_WIM_FILES_AND_MMOS"></span>Startbaren WIM-Dateien und MMOS


Wenn Sie Schutz zurücksetzen auf einem Gerät zu verwenden, müssen die MMOS oder startbaren WIM-Dateien, die dieses Gerät unterstützen werden unter einer Version der Tools erstellt, die Schutz Zurücksetzen nicht unterstützt. Es wird empfohlen, die die Version des Geräts und die Version der MMOS Übereinstimmung.

## <a name="span-idreverselogisticsspanspan-idreverselogisticsspanspan-idreverselogisticsspanreverse-logistics"></a><span id="Reverse_logistics"></span><span id="reverse_logistics"></span><span id="REVERSE_LOGISTICS"></span>Reverse Logistik


Sie können mit reverse Logistik Abrufen von Informationen über den Status des Schutzes zurücksetzen auf einem Gerät, wie das Gerät IMEI, oder Überprüfen Sie, ob zurücksetzen Protection derzeit auf dem Gerät aktiviert ist. Sie können auch dies verwenden, Zurücksetzen Schutz entfernen, wenn Sie den entsprechenden Recovery-Schlüssel für das Gerät haben. Reverse Logistik kann Ihnen in Reparaturservice Szenarien zurücksetzen Schutz ist aktiviert, wobei ein Ihnen nicht die Microsoft Account-Anmeldeinformationen, die um es auszuschalten die erforderlich sind. Wir haben zum Verwenden von reverse Logistik in der [Tragbaren Geräte COM-API-Beispiel](https://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d)Beispielcode bereitgestellt.

### <a name="span-idhowtogetstartedusingreverselogisticsspanspan-idhowtogetstartedusingreverselogisticsspanspan-idhowtogetstartedusingreverselogisticsspanhow-to-get-started-using-reverse-logistics"></a><span id="How_to_get_started_using_reverse_logistics"></span><span id="how_to_get_started_using_reverse_logistics"></span><span id="HOW_TO_GET_STARTED_USING_REVERSE_LOGISTICS"></span>Erste Schritte mit reverse Logistik

Unternehmen müssen, um Microsofts automatisierte reverse Logistik-Programm verwenden, melden Sie sich für ein Konto mit der [Microsoft-Dashboard](https://sysdev.microsoft.com/) , und führen Sie die folgenden Aufgaben:

-   Erwerben Sie eine Authenticode-Signaturzertifikat.
-   Installieren Sie das Zertifikat auf allen Computern, die zum Senden von Anforderungen verwendet werden.
-   Zuweisen einer Administratoren zum Verwalten des Programms.
-   Fügen Sie für jeden Benutzer in Ihrem Unternehmen, die Übermittlungen an das Dashboard berücksichtigt wird das Microsoft-Konto für den Benutzer, und erteilen Sie jeder Benutzer die **Logistische Reverse** -Berechtigung. Zum Erteilen von Berechtigungen, klicken Sie auf **Ihr Profil** , und klicken Sie dann auf **Berechtigungen.**

### <a name="span-idregisteryourcompanyspanspan-idregisteryourcompanyspanspan-idregisteryourcompanyspanregister-your-company"></a><span id="Register_your_company"></span><span id="register_your_company"></span><span id="REGISTER_YOUR_COMPANY"></span>Registrieren Sie Ihr Unternehmen

Ihr Unternehmen bereits ein Konto mit der Microsoft-Dashboard. In diesem Fall müssen Sie den Administrator Ihres Kontos mit dem Dashboard. Wenn den Administrator suchen möchten, klicken Sie auf **Verwaltung** , und klicken Sie dann auf **Meine Administratoren**. Es wird empfohlen, einen reverse Logistik Manager als zusätzliche Administrator hinzufügen, daher es einfacher ist, reverse Logistik Abfragen von Benutzern zu genehmigen. Die Administratoren Aufgaben zählen Genehmigen von Anfragen zur Teilnahme an des Unternehmens, Genehmigen der Anforderung für Berechtigungen und Entfernen von Benutzern aus, nachdem sie das Unternehmen verlassen. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Berechtigungen](https://msdn.microsoft.com/library/windows/hardware/br230781.aspx).

Wenn Ihr Unternehmen noch nicht über ein Konto mit dann Dashboard verfügt, ist erste Schritte:

-   [Abrufen einer Codesignierungszertifikat an](https://msdn.microsoft.com/library/windows/hardware/hh801887.aspx)
    -   Um Revers Logistik verwenden, Sie **müssen** erwerben, ein standard-Klasse 3-Zertifikat ein EV-Zertifikat.
    -   Stellen Sie sicher, dass Sie Ihr Unternehmen mit dem gleichen Namen eingerichtet haben, die Sie verwendet, um das Zertifikat zu erwerben. Dies ist der Name, der für Benutzer verfügbar gemacht wird.
-   [Einrichten eines Unternehmens](https://msdn.microsoft.com/library/windows/hardware/br230795.aspx)

Stellen Sie sicher, dass Sie dieses Zertifikat speichern und ihn zugegriffen werden. Sie müssen auf mehreren Computern weiter unten in diesem Abschnitt zu installieren. Es wird empfohlen, dass Sie eine Kopie des Zertifikats auf einem Laufwerk Ziehpunkt oder etwas leicht zugänglich speichern.

### <a name="span-idaddusersforyourcompanyspanspan-idaddusersforyourcompanyspanspan-idaddusersforyourcompanyspanadd-users-for-your-company"></a><span id="Add_users_for_your_company"></span><span id="add_users_for_your_company"></span><span id="ADD_USERS_FOR_YOUR_COMPANY"></span>Hinzufügen von Benutzern für Ihr Unternehmen

Nachdem Sie Ihr Unternehmen registrieren, fügen Sie andere Benutzer, die Berechtigung Logistik des Reverseproxys müssen:

-   Die erste Person, die ein Unternehmen registrieren wird ein Administrator für dieses Unternehmenskonto.
-   Nachfolgende Benutzer müssen mit einem Microsoft-Konto registrieren. Klicken Sie auf der oberen rechten Ecke des [Dashboards](https://sysdev.microsoft.com/), **Registrieren** Sie sich selbst zu Ihrem Unternehmen hinzufügen, und fordern die Berechtigung **Des Reverseproxys Logistik** , klicken Sie unter **Zusätzliche Berechtigungen anfordern**.
-   Der Administrator erhält eine Benachrichtigung und genehmigt die Anforderung.

Weitere Informationen zum Anmelden an das Dashboard finden Sie unter [vor der Anmeldung](https://msdn.microsoft.com/library/windows/hardware/br230782.aspx).

### <a name="span-idsetupyourworkstationforreverselogisticsspanspan-idsetupyourworkstationforreverselogisticsspanspan-idsetupyourworkstationforreverselogisticsspanset-up-your-workstation-for-reverse-logistics"></a><span id="Set_up_your_workstation_for_reverse_logistics"></span><span id="set_up_your_workstation_for_reverse_logistics"></span><span id="SET_UP_YOUR_WORKSTATION_FOR_REVERSE_LOGISTICS"></span>Einrichten der Arbeitsstation für reverse Logistik

### <a name="span-idprerequistesspanspan-idprerequistesspanspan-idprerequistesspanprerequistes"></a><span id="Prerequistes"></span><span id="prerequistes"></span><span id="PREREQUISTES"></span>Prerequistes

-   Sie benötigen eine Arbeitsstation, die Windows 7 oder höher ausgeführt wird und der Browserzugriff auf das Internet hat.
-   Jeden Absender reverse Logistik benötigen ein eigenes Microsoft-Konto; Kontoanmeldeinformationen sollte nicht von mehreren Personen gemeinsam genutzt werden.
-   Nur Computer, die das Zertifikat lokal installiert sein werden reverse Logistik ausführen können.

### <a name="span-idprocessspanspan-idprocessspanspan-idprocessspanprocess"></a><span id="Process"></span><span id="process"></span><span id="PROCESS"></span>Prozess

1.  Schließen Sie das Bildlauffeld Laufwerk, das das Zertifikat enthält, das Sie erworben haben.
2.  Melden Sie auf jedem Computer, auf dem Sie reverse Logistik Anforderungen übermitteln möchten sich als lokaler Administrator und installieren Sie das Codesignierungszertifikat:
    1.  Öffnen Sie ein Eingabeaufforderungsfenster.
    2.  Typ `mmc` und drücken Sie die EINGABETASTE.
    3.  Klicken Sie im Menü **Datei** auf **Snap-In hinzufügen/entfernen**.
    4.  Klicken Sie auf **Hinzufügen**.
    5.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** die Option **Zertifikate**aus.
    6.  Klicken Sie auf **Hinzufügen**.
    7.  Klicken Sie im Dialogfeld **Zertifikat-Snap-in** **auf** Computerkonto, und klicken Sie auf **nächsten.**
    8.  Klicken Sie im Dialogfeld **Computer auswählen** auf **Fertig stellen**.
    9.  Klicken Sie im Dialogfeld **Snap-In hinzufügen/entfernen** auf **OK**.
    10. Klicken Sie auf **Zertifikate (lokaler Computer)** , um die Zertifikatspeicher für den Computer anzuzeigen, klicken Sie im Fenster **Konsolenstamm** .
    11. Wählen Sie im Bereich **Aktionen** unter Zertifikate ** **Weitere Aktionen**, und klicken Sie dann alle Aufgaben**, und klicken Sie dann **Importieren**:![Zertifikat importieren](images/import-cert.png)
    12. Klicken Sie auf **Durchsuchen** , und suchen Sie das Zertifikat, das Sie erworben haben.
    13. Klicken Sie auf **OK**. Das Zertifikat sollte in Ihrer **persönlichen** Zertifikatspeicher installiert werden.

### <a name="span-idauthenticationandusespanspan-idauthenticationandusespanspan-idauthenticationandusespanauthentication-and-use"></a><span id="Authentication_and_Use"></span><span id="authentication_and_use"></span><span id="AUTHENTICATION_AND_USE"></span>Authentifizierung und Verwendung

Im nächste Schritt ist die Erstellung ein Clienttools auf einer Arbeitsstation bereitgestellten reverse Logistik Anforderungen übermitteln. Sie müssen eine Drittanbieter-app mit Microsoft-Kontos zu erstellen. Die app wird auf einen anderen Browser verwenden, um einen Benutzer zur Eingabe der Anmeldeinformationen, die über eine Microsoft-Konto-Website zu ermöglichen. Gewährt, die Zugriff auf die Wahl des geeigneten Tools zum Aufrufen der umgekehrte Logistik API den entsprechenden-Token abzurufen. Weitere Informationen dazu, wie Sie die app zu erstellen, finden Sie unter [Mobile und Windows-desktop-apps](https://msdn.microsoft.com/library/hh826529.aspx), und verwenden Sie "dds.reverse\_Logistik" Bereich (anstelle von "wl.basic"), um den entsprechenden Token abzurufen.

Nachdem das Tool, das das Token verfügt, kann die logistische Reverse-API mit Token, das Clientzertifikat und das Ziel des Vorgangs IMEI, um die Wiederherstellungsschlüssel für das Zielgerät abrufen aufgerufen werden.

![Reverse Logistocs-Authentifizierungsprozess](images/rlauthnprocess.png)

### <a name="span-idapispecificationspanspan-idapispecificationspanspan-idapispecificationspanapi-specification"></a><span id="API_specification"></span><span id="api_specification"></span><span id="API_SPECIFICATION"></span>API-Spezifikation

### <a name="span-idrequestspanspan-idrequestspanspan-idrequestspanrequest"></a><span id="Request"></span><span id="request"></span><span id="REQUEST"></span>Anforderung

Reverseproxy-Endpunkt Logistik-API:

<Https://cs.dds.microsoft.com/Command/ExternalClientCert/AdministrativeUnprotect/%7BPartnerName%7D/%7BDeviceId%7D> BUCHEN

{PartnerName} sollte mit einer Endbenutzer lesbare Zeichenfolge ersetzt werden, die in einer e-Mail an den Benutzer, deren Microsoft-Konto des Telefons schützt, einbezogen werden.

{Geräte-ID} sollte durch eine Zeichenfolge in einem der folgenden Formate (die eckigen Klammern verlassen und ersetzen den Text innerhalb und einschließlich der geschweiften Klammern) ersetzt werden:

-   ImeiOrMeid\[{IMEI oder MEID des Geräts}\]
-   DUID\[{DUID des Geräts}\]

Das Microsoft-Konto Benutzertoken der "Authorization" Kopfzeile der Anforderung einschließen.

Das Zertifikat bereitgestellt wird, mit dem Dashboard für Ihre Organisation muss als das Clientzertifikat für mutual HTTPS verwendet werden.

### <a name="span-idresponsespanspan-idresponsespanspan-idresponsespanresponse"></a><span id="Response"></span><span id="response"></span><span id="RESPONSE"></span>Antwort

```
{
  "UnprotectResult": "{UnprotectResult}"
  "RecoveryKey": "{RecoveryKey}"
}

UnprotectResult will be a string value of the enum specified below:

    /// <summary>
    /// Result of the unprotect operation
    /// </summary>
    public enum UnprotectResult
    {
        /// <summary>
        /// Device was not found in DDS
        /// </summary>
        DeviceNotFound,

        /// <summary>
        /// Device was already unprotected
        /// </summary>
        DeviceAlreadyUnprotected,

        /// <summary>
        /// Device has been unprotected
        /// </summary>
        DeviceUnprotected,

        /// <summary>
        /// IF we find more than 1 device, we don&#39;t currently have a way to resolve the conflict. So, we don&#39;t unprotect.
        /// </summary>
        MultipleDevicesFound,
    }
```

Antwortcodes:

-   200: Erfolg.
-   400: die Anforderung ist ungültig.
-   401: die Anforderung ist nicht autorisiert. Ihrer Organisation möglicherweise nicht ordnungsgemäß bereitgestellt werden, der Benutzer kann nicht mit der Organisation bereitgestellt werden oder ein Problem oder Konflikt mit das Clientzertifikat oder Benutzertokens Microsoft Konto vorhanden sein kann. Die Antwort kann Text, wenn Sie einen Grund für das Problem Autorisierung für enthalten.
-   404: der API-Pfad oder Gerät angegeben wurde nicht gefunden.
-   500: ein unerwarteter Fehler. Wenn dieses Problem weiterhin auftritt, wenden Sie sich an Microsoft für die Lösung des Problems.
-   503: Speicherfehler. Wenn dieses Problem weiterhin auftritt, wenden Sie sich an Microsoft für die Lösung des Problems.

 

 





