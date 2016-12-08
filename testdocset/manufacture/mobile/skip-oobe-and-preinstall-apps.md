---
author: kpacquer
Description: "Beim Starten in den Modus Fertigung können OOBE überspringen und Vorinstallieren von apps, die Fertigung Tests ausführen."
ms.assetid: e448479f-6831-40b5-bb19-7ad4c22cdf6a
MSHAttr: PreferredLib:/library/windows/hardware
title: "Erstellen Sie ein vollständige Betriebssystem manufacturing Profil"
ms.openlocfilehash: cf3a19a55b85557c8da0742e2eeca6e74427d22e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-full-operating-system-manufacturing-profile"></a>Erstellen Sie ein vollständige Betriebssystem manufacturing Profil


Beim Starten in den Modus Fertigung können OOBE überspringen und Vorinstallieren von apps, die Fertigung Tests ausführen. Springen OOBE kann das manufacturing Zeit beschleunigen.

Um dies einzurichten, fügen Sie der apps, die dem Profil Manufacturing installiert werden soll. Weitere Informationen zu Fertigung-Profilen finden Sie unter [Fertigung Modus](manufacturing-mode.md).

## <a name="span-idaddappstoacustommanufacturingprofilespanspan-idaddappstoacustommanufacturingprofilespanspan-idaddappstoacustommanufacturingprofilespanadd-apps-to-a-custom-manufacturing-profile"></a><span id="Add_apps_to_a_custom_manufacturing_profile"></span><span id="add_apps_to_a_custom_manufacturing_profile"></span><span id="ADD_APPS_TO_A_CUSTOM_MANUFACTURING_PROFILE"></span>Hinzufügen von apps zu einem benutzerdefinierten Fertigung Profil


Im Modus Fertigung Profil, müssen Sie einen neuen Registrierungsschlüssel, die die apps aufgeführt werden, die mit dem Profil Fertigung installiert werden sollen erstellen:

``` syntax
HKEY_LOCAL_MACHINE\System\ControlSet001\Control\ManufacturingMode\<Profile Name>\Apps\OobeInstall
```

Sie müssen unter dem Registrierungsschlüssel OOBEInstall Registrierungsschlüssel erstellen (mit REG\_DWORD-Typ) für die jeweilige app. Der Name des Registrierungsschlüssels muss den Dateinamen des app-Paket übereinstimmen.

Um die Einstellungsapp das Profil Fertigung hinzuzufügen, würden Sie beispielsweise einen Registrierungsschlüssel namens **Systemsettings**hinzufügen.

Hier sind einige Punkte, berücksichtigen Sie beim Hinzufügen von apps zu einem Profil Fertigung:

-   Das Profil Manufacturing muss keine Windows-Services nicht deaktivieren.
-   Der Wert des Registrierungsschlüssels ist reserviert. Nur der Name des Registrierungsschlüssels wird.
-   Die app eine erste oder zweite Partei app werden kann, aber das app-Paket muss ein Teil des Bilds.
-   Die \* Platzhalter verwenden Sie im Namen der app verwendet werden kann.
-   Soll die normale OOBE-Erfahrung (mit allen apps installiert), erstellen Sie einen einzelnen Registrierungsschlüssel mit dem Namen der **\***.

### <a name="span-idfindthenameoftheappspanspan-idfindthenameoftheappspanspan-idfindthenameoftheappspanfind-the-name-of-the-app"></a><span id="Find_the_name_of_the_app"></span><span id="find_the_name_of_the_app"></span><span id="FIND_THE_NAME_OF_THE_APP"></span>Suchen Sie den Namen der app

Der Name des Registrierungsschlüssels muss den Dateinamen des app-Paket übereinstimmen. Sie können eine Liste der apps abrufen, die auf dem Gerät sind, mithilfe des folgenden Befehls auf dem Gerät Laufwerksstamm:

``` syntax
dir /S MPAP_*.provxml
```

Dieser Befehl gibt eine Liste der Dateien, ähnlich der folgenden zurück:

``` syntax
MPAP_systemsettings_001.provxml
```

Der Teil des Dateinamens nach **MPAP\_ ** und vor der ** \_0xx.provxml** ist, was Sie für den Namen des Registrierungsschlüssels verwenden soll.

## <a name="span-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanspan-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanspan-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanadd-the-registry-keys-to-your-custom-manufacturing-profile-package"></a><span id="Add_the_registry_keys_to_your_custom_manufacturing_profile_package"></span><span id="add_the_registry_keys_to_your_custom_manufacturing_profile_package"></span><span id="ADD_THE_REGISTRY_KEYS_TO_YOUR_CUSTOM_MANUFACTURING_PROFILE_PACKAGE"></span>Hinzufügen der Registrierungsschlüssel zu Ihrer benutzerdefinierten Fertigung-Profil Paket


Sie fügen die Registrierung Schlüssel zu Ihrem benutzerdefinierten Fertigung Profil zu packen, wie jedes andere Paket verwenden. Weitere Informationen zu packen finden Sie unter [Erstellen von Telefon Pakete](https://msdn.microsoft.com/library/dn756642).

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="Manufacturing.FactoryTestSample"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfile" Value="$(MfgMode)\CustomProfile" />
    </Macros>

    <Components>
        <OSComponent>
          <RegKeys>
            <RegKey KeyName="$(CustomProfile)\"/>
            <RegKey KeyName="$(CustomProfile)\Services"/>
            <RegKey KeyName="$(CustomProfile)\Apps"/>
            <RegKey KeyName="$(CustomProfile)\Apps\OobeInstall">
                <RegValue Name="FactoryTestOEMSample" Value="0" Type="REG_DWORD"/>
                <RegValue Name="systemsettings" Value="0" Type="REG_DWORD"/>
             </RegKey>
          </RegKeys>
        </OSComponent>
    </Components>
</Package>
```

 

 





