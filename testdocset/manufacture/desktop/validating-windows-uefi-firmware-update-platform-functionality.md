---
author: Justinha
Description: "Dieses Dokument enthält die grundlegende Validierung Szenarien, die erforderlich sind, bevor Signieren-off auf der Funktionalität Windows UEFI Firmware Update-Plattform zu übergeben. Spezifikation kann hier heruntergeladen werden."
ms.assetid: 42e7c93e-3af3-496a-8fdf-ac97b4e85970
MSHAttr: PreferredLib:/library/windows/hardware
title: "Überprüfung der Funktionalität von Windows UEFI Firmware Update-Plattform"
ms.openlocfilehash: a75a98cd9436b5b69904c86fbcb8d0b49d0765fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="validating-windows-uefi-firmware-update-platform-functionality"></a>Überprüfung der Funktionalität von Windows UEFI Firmware Update Plattform


Dieses Dokument enthält die grundlegende Validierung Szenarien, die erforderlich sind, bevor Signieren-off auf der Funktionalität Windows UEFI Firmware Update-Plattform zu übergeben. Spezifikation kann [hier](http://go.microsoft.com/fwlink/p/?linkid=523808)heruntergeladen werden.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspan-prerequisites"></a><span id="_Prerequisites"></span><span id="_prerequisites"></span><span id="_PREREQUISITES"></span>Erforderliche Komponenten


-   Für jeden Eintrag EFI System Ressource Tabelle (ESRT) benötigen Sie eine "Kapseln" für die neueste Firmware. Die Szenarios bezieht sich auf die neueste Version als X. Jeder Eintrag ESRT wird mit einer eindeutigen GUID identifiziert.
-   Für jeden ESRT Eintrag verfügbar gemacht werden, erstellen Sie ein Paket ' Kapseln ', die ihre Version wird oberhalb des Pakets, das in Schritt 1 erstellte erhöht. Diese kapseln werden als X + 1 bezeichnet werden.
-   Kapseln, die bei simulieren fehlerbedingungen wie etwa eine "Kapseln" für die Nutzlast ist nicht signiert oder mit einer ungültigen PS. signiert
-   Stellen Sie sicher, dass alle kapseln zu verwendende angemeldet sind entsprechend der OS Perspektive, Katalog signiert und der Firmware signiert, PK signiert. Es sei denn, Sie insbesondere die negativen PK Signieren Fällen testen. Siehe "Signieren des Firmware Treibers Paket" in der Spezifikation für Einzelheiten zur Anzeige ein Treiberpakets "Kapseln" oder Firmware signieren.

## <a name="span-idhowtospanspan-idhowtospanspan-idhowtospanhow-to"></a><span id="How_To"></span><span id="how_to"></span><span id="HOW_TO"></span>So wird es gemacht


**Installieren Sie eine neue "Kapseln" oder deinstallieren Sie der eine zuvor installierte "Kapseln"**

1.  Öffnen Sie den Geräte-Manager.
2.  Suchen Sie nach der Geräteknoten, der die Firmware darstellt, ist normalerweise unter "Firmware" Geräte.
3.  Klicken Sie mit der rechten Maustaste auf das Firmware-Gerät Sie aktualisieren möchten.
4.  Wählen Sie die **Treiber-Software zu aktualisieren**. Erhalten Sie ein Popup, der besagt "Update-Treiber-Software - &lt;Firmware&gt;".
5.  Wählen Sie **auf dem Computer für Treiber-Software suchen**.
6.  Wählen Sie auf das nächste Fenster **aus einer Liste von Gerätetreibern auf meinem Computer auswählen**.
7.  Wenn Sie vor der Treiber installiert wurde, wählen Sie ihn aus dem Feld **kompatible Hardware anzeigen** . Wenn es nicht vorhanden ist, wählen Sie die **Datenträger** und auf Weiter. Andernfalls klicken Sie **auf OK** und starten Sie das System neu.
8.  Wenn Sie die **Datenträger**auswählen, erhalten Sie eine **Installation von Datenträger**mit der Bezeichnung Popup.
9.  Verwenden Sie **Durchsuchen** , um zu dem Verzeichnis zu wechseln, das die "Kapseln" der Firmware verfügt, die Sie installieren möchten.
10. Wählen Sie aus der INF-Datei in diesem Verzeichnis, und drücken Sie **OK** , um die Installation.
11. Während der Installation Wenn Sie möchten ein Popup-Fenster angezeigt, dass der Treiber nicht signiert ist, fahren Sie fort und stimme diesem Treiber.
12. Das System zu einem Neustart aufgefordert.
13. Nach der Installation der "Kapseln" der Firmware müssen Sie neu starten. Wenn Sie mehrere ' Kapseln ' Pakete installieren möchten, warten Sie, bis alle kapseln installiert sind, und klicken Sie dann auf die endgültige "Kapseln" Neustart neu zu starten.

**Die Version und Status Details Abfragen:**

-   Führen Sie das Skript QueryVersionAndStatus.ps1 PowerShell (PS) die aktuelle Firmwareversion Abfragen, letzter Versuch Firmwareversion und letzter Versuch Status.

    **Ausführen des Skripts:**

    1.  PowerShell als Administrator ausführen.
    2.  `Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force`(Dies wird nur einmal ausgeführt werden.)
    3.  Zeigt die Version und den Status Details für die angegebene GUID. Beispiel:`.\QueryVersionAndStatus.ps1 6bd2efb9-23ab-4b4c-bc37-016517413e9a`
    4.  Überprüfen Sie, ob die erfolgreiche Aktualisierung der Firmware: finden Sie im Abschnitt "Überprüfen des Status von der Firmware-Aktualisierung" im Spezifikationsdokument. Stellen Sie sicher, dass der letzte Versuch Status und der aktuellen Version übereinstimmt, die erwartete Version.
    5.  Empfohlen: Überprüfen Sie, um sicherzustellen, dass die Geräte, die Sie aktualisieren möchten auch weiterhin funktionsfähig sind.
    6.  Legen Sie die Rollbackrichtlinie: Einige Szenarien erfordern möglicherweise, Rollback Firmware. Rollback ist kein Produktionsszenario. Um Rollback können, verfügt über ein Registrierungsschlüssel für die Richtlinie zu erstellenden ein. Erstellen einer REG\_DWORD-Schlüssel mit dem Namen "Richtlinie" unter dem Knoten HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Control\\FirmwareResources\\{&lt;GUID&gt;} und den Wert des Schlüssels Richtlinie auf 1 festgelegt. Beachten Sie, dass die GUID, durch die tatsächliche GUID aus der ESRT ersetzt werden soll.

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Szenarien


### <a name="span-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespanspan-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespanspan-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespans1-each-esrt-entry-is-successfully-updatable-through-capsule"></a><span id="S1__Each_ESRT_entry_is_successfully_updatable_through_capsule"></span><span id="s1__each_esrt_entry_is_successfully_updatable_through_capsule"></span><span id="S1__EACH_ESRT_ENTRY_IS_SUCCESSFULLY_UPDATABLE_THROUGH_CAPSULE"></span>S1: Jeden Eintrag ESRT kann durch "Kapseln" erfolgreich aktualisiert

Die folgenden Schritte sollten für jeden Eintrag ESRT abgeschlossen werden, die von der Plattform unterstützt wird. Oder mit anderen Worten für System-Firmware und jede Gerätefirmware, das Aktualisieren der Firmware über UpdateCapsule unterstützt.

**Schritte**

1.  Installieren Sie für jeden Eintrag ESRT der "Kapseln" für Firmwareversion X.
2.  Stellen Sie sicher, dass alle oben genannten kapseln vor dem Neustart installiert sind.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte für jeden Eintrag ESRT erfolgreich sein, die aktualisiert wurde. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X
-   Letzter Versuch Status = 0 (STATUS\_ERFOLG)

### <a name="span-ids2thelatestfirmwareversionxisalsoupdatabletox1spanspan-ids2thelatestfirmwareversionxisalsoupdatabletox1spanspan-ids2thelatestfirmwareversionxisalsoupdatabletox1spans2-the-latest-firmware-version-x-is-also-updatable-to-x1"></a><span id="S2__The_latest_firmware_version_X_is_also_updatable_to_X_1_"></span><span id="s2__the_latest_firmware_version_x_is_also_updatable_to_x_1_"></span><span id="S2__THE_LATEST_FIRMWARE_VERSION_X_IS_ALSO_UPDATABLE_TO_X_1_"></span>S2: Die aktuelle Firmwareversion X kann auch auf X + 1 aktualisiert

Die folgenden Schritte sollten für jeden Eintrag ESRT abgeschlossen werden, die von der Plattform unterstützt wird. Oder mit anderen Worten, für System-Firmware und jede Gerätefirmware, das Aktualisieren der Firmware über UpdateCapsule unterstützt.

**Schritte**

1.  Führen Sie Szenario S1 oben.
2.  Installieren Sie für jeden Eintrag ESRT der "Kapseln" für Firmwareversion X + 1.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte für jeden Eintrag ESRT erfolgreich sein, die aktualisiert wurde. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X + 1
-   Letzter Versuch Version = X + 1
-   Letzter Versuch Status = 0 (STATUS\_ERFOLG)

### <a name="span-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspanspan-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspanspan-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspans3-on-failure-firmware-update-returns-the-right-status-code-as-defined-in-the-specification"></a><span id="S3__On_failure__firmware_update_returns_the_right_status_code_as_defined_in_the_specification_"></span><span id="s3__on_failure__firmware_update_returns_the_right_status_code_as_defined_in_the_specification_"></span><span id="S3__ON_FAILURE__FIRMWARE_UPDATE_RETURNS_THE_RIGHT_STATUS_CODE_AS_DEFINED_IN_THE_SPECIFICATION_"></span>S3: Bei einem Fehler gibt Firmwareupdates den richtigen Statuscode gemäß Definition in der Spezifikation

Die Statuscodes werden in den Abschnitt mit dem Namen "UEFI System Definition: Ressourcentabelle", in der Tabelle mit dem Titel "ESRT letzter Versuch Feld Statuswerte" definiert.

### <a name="span-ids31insufficientbatteryanduefisystemfirmwareupdatespanspan-ids31insufficientbatteryanduefisystemfirmwareupdatespanspan-ids31insufficientbatteryanduefisystemfirmwareupdatespans31-insufficient-battery-and-uefi-system-firmware-update"></a><span id="S3.1_Insufficient_Battery_and_UEFI_System_Firmware_update"></span><span id="s3.1_insufficient_battery_and_uefi_system_firmware_update"></span><span id="S3.1_INSUFFICIENT_BATTERY_AND_UEFI_SYSTEM_FIRMWARE_UPDATE"></span>Nicht genügend Batterie S3.1 und UEFI System Firmware update

**Schritte**

1.  Nimmt die Gebühr Batterie auf weniger als 25 % und dann plug-in das Netzkabel ab.
2.  Installieren Sie die "Kapseln" für UEFI System Firmware Version X + 1. Nehmen wir an, dass die aktuelle Version X ist.
3.  Stellen Sie vor dem Neustart sicher, dass die Belastung Batterie weniger als 25 % ist

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte fehlschlagen. Überprüfen Sie auf ESRT-Eintrag, der Firmware System entspricht, dass:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 1
-   Letzter Versuch Status = 0xc00002de (STATUS\_UNZUREICHEND\_POWER)

### <a name="span-ids32insufficientbatteryanddevicefirmwareupdatespanspan-ids32insufficientbatteryanddevicefirmwareupdatespanspan-ids32insufficientbatteryanddevicefirmwareupdatespans32-insufficient-battery-and-device-firmware-update"></a><span id="S3.2_Insufficient_Battery_and_Device_Firmware_update_"></span><span id="s3.2_insufficient_battery_and_device_firmware_update_"></span><span id="S3.2_INSUFFICIENT_BATTERY_AND_DEVICE_FIRMWARE_UPDATE_"></span>Nicht genügend Batterie S3.2 und Gerätefirmware update

**Schritte**

1.  Nimmt die Gebühr Batterie auf weniger als 25 % und dann plug-in das Netzkabel ab.
2.  Installieren der kapseln für ALLE unterstützten Geräte im System mit Firmwareversion X + 1. Nehmen wir an, dass die aktuelle Firmwareversion für das angegebene Gerät X ist.
3.  Vor dem Neustart, stellen Sie sicher, dass die Belastung Batterie weniger als 25 %.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte fehlschlagen. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 1
-   Letzter Versuch Status = 0xc00002de (STATUS\_UNZUREICHEND\_POWER)

### <a name="span-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespanspan-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespanspan-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespans33-insufficient-battery-uefi-system-and-device-firmware-update-at-the-same-time"></a><span id="S3.3_Insufficient_Battery__UEFI_System_and_Device_Firmware_update_at_the_same_time"></span><span id="s3.3_insufficient_battery__uefi_system_and_device_firmware_update_at_the_same_time"></span><span id="S3.3_INSUFFICIENT_BATTERY__UEFI_SYSTEM_AND_DEVICE_FIRMWARE_UPDATE_AT_THE_SAME_TIME"></span>Nicht genügend Batterie S3.3, UEFI System und Gerätefirmware aktualisieren zur selben Zeit

**Schritte**

1.  Nimmt die Gebühr Batterie weniger als 25 % und dann plug-in das Netzkabel ab.
2.  Installieren Sie die kapseln für UEFI System Firmware und alle Gerätefirmware mit der Version X + 1.
3.  Vor dem Neustart, stellen Sie sicher, dass die Belastung Batterie weniger als 25 %.

**Erwartetes Ergebnis**

Für Firmware System und der Gerätefirmware aller für die das Update versucht wurde, sollte Firmwareupdates fehlschlagen. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 1
-   Letzter Versuch Status = 0xc00002de (STATUS\_UNZUREICHEND\_POWER)

### <a name="span-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspanspan-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspanspan-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspans34-firmware-update-should-fail-when-the-capsule-is-not-pk-signed"></a><span id="S3.4_Firmware_update_should_fail_when_the_capsule_is_not_PK_signed"></span><span id="s3.4_firmware_update_should_fail_when_the_capsule_is_not_pk_signed"></span><span id="S3.4_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_IS_NOT_PK_SIGNED"></span>S3.4 Firmwareupdate sollte fehlschlagen, wenn der "Kapseln" nicht PK angemeldet ist

Die folgenden Schritte sollten für jeden Eintrag ESRT abgeschlossen werden, die von der Plattform unterstützt wird. Oder mit anderen Worten für System-Firmware und jede Gerätefirmware, das Aktualisieren der Firmware über UpdateCapsule unterstützt.

**Schritte**

1.  Erstellen Sie für jeden Eintrag ESRT ein "Kapseln" X + 2, für die Nutzlast nicht angemeldet ist.
2.  Installieren Sie die kapseln X + 2. Nehmen wir an, dass die aktuelle Version X ist.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte für alle ESRT Posten fehlschlagen für die das Update versucht wurde. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 2
-   Letzter Versuch Status = 0xC0000022 (STATUS\_ACCESS\_VERWEIGERT)

### <a name="span-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespanspan-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespanspan-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespans35-firmware-update-should-fail-when-the-capsule-is-signed-with-the-wrong-pk-certificate"></a><span id="S3.5_Firmware_update_should_fail_when_the_capsule_is_signed_with_the_wrong_PK_certificate"></span><span id="s3.5_firmware_update_should_fail_when_the_capsule_is_signed_with_the_wrong_pk_certificate"></span><span id="S3.5_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_IS_SIGNED_WITH_THE_WRONG_PK_CERTIFICATE"></span>S3.5 Firmwareupdate sollten misslingen, wenn die "Kapseln" mit dem falschen PK Zertifikat signiert wurde.

Die folgenden Schritte sollten für jeden Eintrag ESRT abgeschlossen werden, die von der Plattform unterstützt wird. Oder mit anderen Worten für System-Firmware und jede Gerätefirmware, das Aktualisieren der Firmware über UpdateCapsule unterstützt.

**Schritte**

1.  Für jeden Eintrag ESRT Erstellen einer "Kapseln" X + 2, Signieren mit einem falschen Schlüssel oder (beispielsweise Verwendung einer Debug "Kapseln" auf einem Produktionsgerät signiertes) Nutzlast.
2.  Installieren Sie die kapseln X + 2. Nehmen wir an, dass die aktuelle Version X ist.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte für alle ESRT Posten fehlschlagen für die das Update versucht wurde. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 2
-   Letzter Versuch Status = 0xC0000022 (STATUS\_ACCESS\_VERWEIGERT)

### <a name="span-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspanspan-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspanspan-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspans36-firmware-update-should-fail-when-the-capsule-payload-is-tampered-with"></a><span id="S3.6_Firmware_update_should_fail_when_the_capsule_payload_is_tampered_with"></span><span id="s3.6_firmware_update_should_fail_when_the_capsule_payload_is_tampered_with"></span><span id="S3.6_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_PAYLOAD_IS_TAMPERED_WITH"></span>S3.6 Firmwareupdate sollten misslingen, wenn ' Kapseln ' Nutzlast manipuliert

Die folgenden Schritte sollten für jeden Eintrag ESRT abgeschlossen werden, die von der Plattform unterstützt wird. Oder mit anderen Worten für System-Firmware und jede Gerätefirmware, das Aktualisieren der Firmware über UpdateCapsule unterstützt.

**Schritte**

1.  Für jeden Eintrag ESRT Erstellen einer "Kapseln" X + 2, Signieren mit dem richtigen Schlüssel oder Zertifikat Nutzlast. Klicken Sie dann öffnen Sie die Firmware-Bin-Datei und kippen Sie 1 oder mehrere Bits in der Datei, und speichern Sie die Datei zurück.
2.  Generieren Sie den Katalog für die Bin-Datei und die INF-Datei erneut.
3.  Installieren Sie die kapseln X + 2. Nehmen wir an, dass die aktuelle Version X ist.

**Erwartetes Ergebnis**

Firmwareupdates sollten für alle Einträge der ESRT fehl, für die das Update versucht wurde. Überprüfen Sie für alle ESRT-Einträge für die das Update versucht wurde, aus:

-   Aktuelle Firmwareversion = X
-   Letzter Versuch Version = X + 2
-   Letzter Versuch Status = 0xC0000022 (STATUS\_ACCESS\_VERWEIGERT) oder 0xC000007B (STATUS\_UNGÜLTIGE\_BILD\_FORMAT)

### <a name="span-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspanspan-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspanspan-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspans37-firmware-does-not-allow-rollback-beyond-the-lowestsupportedfirmwareversion"></a><span id="S3.7__Firmware_does_not_allow_rollback_beyond_the_LowestSupportedFirmwareVersion_"></span><span id="s3.7__firmware_does_not_allow_rollback_beyond_the_lowestsupportedfirmwareversion_"></span><span id="S3.7__FIRMWARE_DOES_NOT_ALLOW_ROLLBACK_BEYOND_THE_LOWESTSUPPORTEDFIRMWAREVERSION_"></span>S3.7: Firmware lässt nicht Rollback hinter der LowestSupportedFirmwareVersion

Die folgenden Schritte sollten auch für andere Gerätefirmware (niedrigere Priorität) durchgeführt werden.

**Schritte**

1.  UEFI System Firmware erstellen Sie eine X + 1 "Kapseln", "LowestSupportedFirmwareVersion" in den ESRT Eintrag für das Systemfirmware auf X + 1 festgelegt ist.
2.  Installieren Sie die "Kapseln" X + 1, und stellen Sie sicher, dass die Aktualisierung erfolgreich ist.
3.  Erstellen Sie eine Aktualisierung der Firmware UEFI System kapseln, so, dass die Version in der INF-Datei X + 2 ist, aber die aktuelle Firmware Binärdatei Version X.
4.  Installieren Sie die "Kapseln" X + 2 und starten Sie das System neu.

**Erwartetes Ergebnis**

Aktualisierung der Firmware sollte fehlschlagen. Überprüfen Sie auf ESRT-Eintrag, der Firmware System entspricht, dass:

-   Aktuelle Firmwareversion = X + 1
-   Letzter Versuch Version = X + 2
-   Letzter Versuch Status = 0xC0000059 (STATUS\_REVISION\_MISMATCH)

### <a name="span-ids4seamlessrecoveryandfirmwareupdateifimplementedspanspan-ids4seamlessrecoveryandfirmwareupdateifimplementedspanspan-ids4seamlessrecoveryandfirmwareupdateifimplementedspans4-seamless-recovery-and-firmware-update-if-implemented"></a><span id="S4__Seamless_recovery_and_firmware_update__if_implemented__"></span><span id="s4__seamless_recovery_and_firmware_update__if_implemented__"></span><span id="S4__SEAMLESS_RECOVERY_AND_FIRMWARE_UPDATE__IF_IMPLEMENTED__"></span>S4: Nahtlose Recovery und Firmware zu aktualisieren (sofern implementiert)

In diesem Szenario variiert nach Plattform je nach der Implementierung der nahtlos Wiederherstellung. Je nach der Implementierung, die Überprüfung erfordern möglicherweise, dass das System in Wiederherstellung oder Unterbrechen der Stromversorgung in der Mitte ein Update oder durch andere Mittel der Wahrnehmung der Wiederherstellung Abläufe erstellen "Kapseln" fehlerhafte, erzwingt die.

**Erwartetes Ergebnis**

Das System sollte in das Betriebssystem starten und die Aktualisierung der Firmware als fehlgeschlagen markiert werden sollte. Die Version vom Gerät UEFI Firmware Ressource gemeldet sollte nicht geändert haben.

### <a name="span-ids5firmwareupdateadherestotheuserexperienceuxrequirementspanspan-ids5firmwareupdateadherestotheuserexperienceuxrequirementspanspan-ids5firmwareupdateadherestotheuserexperienceuxrequirementspans5-firmware-update-adheres-to-the-user-experience-ux-requirement"></a><span id="S5__Firmware_Update_adheres_to_the_User_Experience__UX__requirement"></span><span id="s5__firmware_update_adheres_to_the_user_experience__ux__requirement"></span><span id="S5__FIRMWARE_UPDATE_ADHERES_TO_THE_USER_EXPERIENCE__UX__REQUIREMENT"></span>S5: Firmwareupdate erfüllt die Anforderung User Experience (UX)

**Schritte**

-   In diesem Szenario kann während der Ausführung eines der oben beschriebenen Szenarien, die zu einer erfolgreichen Firmwareupdates führen überprüft werden.

**Erwartetes Ergebnis**

Der Benutzer gemäß der Spezifikation verwendet wird, finden Sie im Abschnitt auf "Benutzerinteraktion".

-   Nur Text, der auf dem Bildschirm angezeigt wird ist "Warten Sie, während wir ein Systemupdate installieren". Der Text wird an den richtigen Koordinaten auf dem Bildschirm angezeigt, wie in der Spezifikation gekennzeichnet.
-   OEM-Logo wird angezeigt, wie in der Spezifikation beschrieben wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows UEFI Firmware Update-Plattform](http://go.microsoft.com/fwlink/p/?linkid=523808)

[UEFI Validierung Option ROM Validierung Anleitungen](uefi-validation-option-rom-validation-guidance.md)

 

 






