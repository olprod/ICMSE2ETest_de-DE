---
author: kpacquer
Description: "Es kann beispielsweise sein, einen Dienst automatisch ausgeführt, wenn das Gerät im Modus Manufacturing ist aber normalerweise deaktiviert werden sollen."
ms.assetid: 5504bade-5342-4006-9631-7321acd983ac
MSHAttr: PreferredLib:/library/windows/hardware
title: "Legen Sie einen Dienst, der nur im Modus Manufacturing ausgeführt wird"
ms.openlocfilehash: 314009721cdcbe0f78c1612c276ed7b1849e87d3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="define-a-service-that-only-runs-in-manufacturing-mode"></a>Legen Sie einen Dienst, der nur im Modus Manufacturing ausgeführt wird


Möglicherweise Anfragen an einen Dienst automatisch ausgeführt, wenn das Gerät im Modus Manufacturing ist aber normalerweise deaktiviert. Beispielsweise würde die Factory Testsammlung wahrscheinlich in dieser Konfiguration ausgeführt. Würden Sie Ihre Service Starttyp auf deaktiviert festgelegt und fügen Sie ein Profil Manufacturing außer Kraft setzen, die den Dienst automatisch gestartet werden, wenn die entsprechende verwenden durchführt manufacturing Modus Profil.

Hier ist ein Beispiel für manufacturing Profil:

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="FactoryTest"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfileServices" Value="$(MfgMode)\CustomProfile\Services" />
    </Macros>

    <Components>
      <!-- Definition for the service -->
      <Service
        Name="FactoryService"
        Start="Disabled"
        Type="Win32OwnProcess"
        ErrorControl="Ignore"
        DisplayName="OEMFactoryTestService"
        Description="A Sample OEM Factory Test Service">

        <Executable Source="$(BINARY_ROOT)\bin\factory\oem_factory_test_service.exe" />

        <!-- Failure actions should reset once per day, for security reasons -->
        <FailureActions ResetPeriod="86400">
          <Action Type="RestartService" Delay="1000"/>
          <Action Type="RestartService" Delay="1000"/>
          <Action Type="RestartService" Delay="1000"/>
          <!-- if it fails to start three times, services should just stop -->
          <Action Type="None" Delay="0"/>
        </FailureActions>

        <RequiredCapabilities>
          <!-- Needed to access and create RPC endpoints -->
          <RequiredCapability CapId="ID_CAP_INTEROPSERVICES" />
        </RequiredCapabilities>

      </Service>

      <OSComponent>
        <!-- Set the factory test service to auto-start when the device is in Manufacturing Mode -->
        <RegKeys>
          <RegKey KeyName="$(CustomProfileServices)\OEMFactoryTestService">
            <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
          </RegKey>
        </RegKeys>
      </OSComponent>

    </Components>
</Package>
```

 

 





