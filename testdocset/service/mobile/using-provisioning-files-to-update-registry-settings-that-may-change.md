---
author: kpacquer
Description: "Mithilfe von Bereitstellung Dateien, um Registrierungseinträge zu aktualisieren, die geändert werden können"
ms.assetid: 77262c4c-69e2-456e-909b-27bd4e0d21f1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Mithilfe von Bereitstellung Dateien, um Registrierungseinträge zu aktualisieren, die geändert werden können"
ms.openlocfilehash: a0034301bdf19713b700156fbc91e8547e9b0199
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-provisioning-files-to-update-registry-settings-that-may-change"></a>Mithilfe von Bereitstellung Dateien, um Registrierungseinträge zu aktualisieren, die geändert werden können


Standard-Paket-Updates werden nicht übernommen, um Registrierungsdaten an, die geändert wurden – beispielsweise von einem Benutzer, die ein Menü wird in der Registrierung gespeicherten Einstellung. Um die Werte dieser Kategorie von Registrierungsdaten zu aktualisieren, muss die Option provisioning XML (Provxml) verwendet werden. Wenn Provxml nicht verwendet wird, um die Registrierungsdaten zu aktualisieren, die geändert wurde, seit das Gerät in der Factory aktualisiert wurde, das Update meldet Erfolg für den Benutzer, aber registrierungsänderungen im standard-Update werden nicht angewendet werden.

**Wichtige**  
Von Registrierungsupdates für Einträge, die nicht geändert werden können mithilfe der standard-Updates behandelt werden. Verwenden Sie Provxml-Dateien in Updates wird nur, wenn ein nicht zu vermeiden müssen Sie Registrierungseinträge zu aktualisieren, die geändert werden können.

 

## <a name="span-idavoidingtheneedspanspan-idavoidingtheneedspanspan-idavoidingtheneedspanregistry-update-strategies"></a><span id="AvoidingTheNeed"></span><span id="avoidingtheneed"></span><span id="AVOIDINGTHENEED"></span>Strategien für die Registrierung


Vermeiden, indem die Notwendigkeit, vorhandene Registrierungsdaten zu aktualisieren konnte Code, um die vorhandene Registrierungsdaten gelesen und migrieren es auf einen neuen Schlüssel, aktualisiert werden, sodass alle vorhandenen benutzereinstellungen beibehalten werden. Sie können auch möglicherweise Ansätze, beispielsweise das Hinzufügen einer Zahl versionsprüfung beim Starten der Anwendung (zur Bestimmung, welche Registrierungswerte verwenden) geeignet. Wenn keine dieser Vorgehensweisen möglich ist, kann Provxml verwendet werden, die vorhandenen Registrierungseinträge zu überschreiben.

## <a name="span-idupdatingregistrysettingswithprovxmlspanspan-idupdatingregistrysettingswithprovxmlspanspan-idupdatingregistrysettingswithprovxmlspanupdating-registry-settings-with-provxml"></a><span id="Updating_registry_settings_with_provxml"></span><span id="updating_registry_settings_with_provxml"></span><span id="UPDATING_REGISTRY_SETTINGS_WITH_PROVXML"></span>Aktualisieren von Einstellungen in der Registrierung mit provxml


Die meisten Updates können ohne die Notwendigkeit für die Bereitstellung von XML (Provxml) erstellt werden. Es gibt jedoch bestimmte Situationen, in dem die Verwendung von Provxml möglicherweise erforderlich. Wenn ein Registrierungswert kann, durch eine Einstellung für Benutzer oder Code, der auf dem Telefon zu einem beliebigen Zeitpunkt geändert werden vor der Installation des Updates ausgeführt wird, Standardpaket Updates berücksichtigen diese Änderungen und die vorhandenen Registrierungsdaten nicht überschreiben. In diesem Fall muss die hier beschriebenen Provxml verwendet werden.

Sie können die OMA CP bereitstellen mithilfe von Provxml verwenden.

In diesem Beispiel Provxml legt den Wert eines einzelnen Registrierungseintrags.

``` syntax
<wap-provisioningdoc>
  <characteristic type="Registry">
    <characteristic type="HKLM\Software\ExampleRegistryKey>
      <parm name="ExampleSettingName" value="0" datatype="integer"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
```

Verwenden Sie folgende Syntax für den Dateinamen Provxml:

``` syntax
mxipupdate_PackageName_n.provxml
```

Für den Wert von *n* für die erste Aktualisierung mit 001 beginnen Sie, und erhöhen Sie den Wert für jedes nachfolgende Update. Alle Provxml Updates werden in der Reihenfolge von *n*angegebenen angewendet.

``` syntax
mxipupdate_updateExample_001.provxml
```

## <a name="span-idcreatingapackagefortheprovxmlspanspan-idcreatingapackagefortheprovxmlspanspan-idcreatingapackagefortheprovxmlspancreating-a-package-for-the-provxml"></a><span id="Creating_a_package_for_the_provxml"></span><span id="creating_a_package_for_the_provxml"></span><span id="CREATING_A_PACKAGE_FOR_THE_PROVXML"></span>Erstellen eines Pakets für die provxml


Erstellen Sie eine Package-Datei, die diese Dateien in das richtige Update-Verzeichnis, siehe platziert. Geben Sie einen entsprechenden Besitzerwert. Weitere Informationen finden Sie unter [primäre Elemente und Attribute einer Projektdatei Paket](https://msdn.microsoft.com/library/dn756796).

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
    Owner="Contoso"
    OwnerType="OEM"
    Platform="" 
    Component="Update"
    SubComponent="PROVXML"
    ReleaseType="Production"
>
  <Components>
    <OSComponent>
      <Files>
        <File Source="mxipupdate_updateExample_001.provxml" 
          DestinationDir="$(runtime.updateProvxmlOEM)" />
      </Files>
    </OSComponent>
  </Components>
</Package>
```

Generieren Sie das Paket, und fügen Sie dann das provisioning-Paket im Betriebssystemabbild, mit der Aktualisierungen an Microsoft zu übermitteln. Weitere Informationen finden Sie unter [Creating Pakete](https://msdn.microsoft.com/library/dn756642) und [Senden Sie ein Update](submit-an-update.md).

## <a name="span-idresettingthephoneandprovxmlregistryupdatesspanspan-idresettingthephoneandprovxmlregistryupdatesspanspan-idresettingthephoneandprovxmlregistryupdatesspanresetting-the-phone-and-provxml-registry-updates"></a><span id="Resetting_the_phone_and_provxml_registry_updates"></span><span id="resetting_the_phone_and_provxml_registry_updates"></span><span id="RESETTING_THE_PHONE_AND_PROVXML_REGISTRY_UPDATES"></span>Die Telefon- und Provxml Registrierungsupdates zurücksetzen


Provxml Updatedateien werden verarbeitet, nachdem ein Update auf dem Gerät angewendet wurde. Wenn das Update angewendet wird, werden die Registrierungseinträge in Basis Betriebssystemabbild und der aktuellen, aktiven Registrierung gespeichert. Dies bedeutet, dass beim Zurücksetzen des Geräts, die registrierungsänderungen, die in einem Update ausgeliefert wurden vorhanden sind, jedoch Updates zugeordneten Store-apps, die diese Registrierungseinträge zu verwenden, darf nicht auf dem Gerät vorhanden sein. Wie OEMs Updates vorzubereiten, müssen sie mögliche Verwendungsszenarien, wie das Telefon zurückgesetzt, identifizieren und testen die zum Erstellen der gewünschten Benutzer wünschen.

## <a name="span-idtestingprovisioningfileinupdatesspanspan-idtestingprovisioningfileinupdatesspanspan-idtestingprovisioningfileinupdatesspantesting-provisioning-file-in-updates"></a><span id="Testing_provisioning_file_in_updates"></span><span id="testing_provisioning_file_in_updates"></span><span id="TESTING_PROVISIONING_FILE_IN_UPDATES"></span>Testen von Bereitstellungsdatei im updates


Zwei Szenarien müssen getestet werden, wenn Sie um ein Update Bereitstellungsdatei zu überprüfen:

-   Aktualisieren – das Update mit einer Basis-Image anwenden. Stellen Sie sicher, dass die Änderungen in der Provxml angewendet wurden.

-   Zurücksetzen – Test nach der Aktualisierung des Telefons mit **Einstellungen für die** &gt; **System** &gt; **zu** &gt; **Ihr Telefon zurücksetzen**. Stellen Sie sicher, dass die Update-Änderungen in der Provxml angewendet wurden.

Es ist wichtig, um sicherzustellen, dass das Update ordnungsgemäß funktioniert, wenn der Benutzer die Einstellungen geändert wurde, die das Update abzielt. Darüber hinaus muss die Erzielung von Updates zu Testzwecken folgen. Weitere Informationen finden Sie unter [Test ein Update](test-an-update.md).

## <a name="span-idprovxmlupdateerrorhandlingspanspan-idprovxmlupdateerrorhandlingspanspan-idprovxmlupdateerrorhandlingspanprovxml-update-error-handling"></a><span id="Provxml_update_error_handling"></span><span id="provxml_update_error_handling"></span><span id="PROVXML_UPDATE_ERROR_HANDLING"></span>Provxml Updates Fehlerbehandlung


Während einer Aktualisierung werden Provxml Dateien für einzelne Best-Effort verarbeitet. Wenn eine Datei Provxml aufgrund von Formatierungsproblemen Fehler oder Berechtigungen verarbeitet werden kann, die Datei wird übersprungen, und die Verarbeitung nachfolgender Provxmls wird. In der Entwicklung von der Prvoxml, überprüfen Sie den Status, der in der Registrierung unter gespeichert wird **HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\DataMigrationFramework\\ProvisioningStatus\\Microsoft**. Ein Eintrag in der Registrierung wird für jede Provxml-Datei, die verarbeitet wird erstellt, und das HRESULT aus Verarbeiten der Datei ist als der Wert des gespeichert.

 

 





