---
author: kpacquer
Description: "Sie können Ihr Gerät mithilfe eines Pakets Fertigung Profile hinzufügen."
ms.assetid: 9925eedf-a49e-4545-b071-72d10925f080
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen Sie ein Profil benutzerdefinierte Fertigung Paket
ms.openlocfilehash: 06ae9d331da7e0c9a40ea95536f539cd4216a4f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-manufacturing-profile-package"></a>Erstellen Sie ein Profil benutzerdefinierte Fertigung Paket


Sie können Ihr Gerät mithilfe eines Pakets Manufacturing Profile hinzufügen. Weitere Informationen zum Erstellen von Paketen finden Sie unter [Creating Pakete](https://msdn.microsoft.com/library/dn756642) . In einigen Fällen müssen Sie zum Erstellen eines benutzerdefinierten Profils. Beispielsweise vielleicht Feinabstimmung, welche Microsoft-Dienste aus Gründen der Leistung oder Funktionen ausgeführt werden soll oder vielleicht haben mehr als eine Fertigung Profil werden soll. Wenn Sie neue benutzerdefinierte Profile zu erstellen, sollten Sie zunächst bereitgestellten Standardprofil kopieren und entsprechend Ihren Anforderungen anpassen.

Wenn Sie ein neues benutzerdefiniertes Profil zu Testzwecken Factory zu erstellen, das wird eine Kopie des Standardprofils, jedoch auch Ihre Test-Zuordnungsdienst startet, könnte es beispielsweise wie folgt aussehen:

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="ManufacturingModeServices"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfileServices" Value="$(MfgMode)\CustomProfile\Services" />
    </Macros>

    <Components>
        <OSComponent>
         <!-- Overrides copied from default profile -->
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\*">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000003" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\AccountProvSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>              
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\adss">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\AudioSrv">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\BFE">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\BrokerInfrastructure">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\cellusermodeinterconnect">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\DcomLaunch">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\DHCP">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\Fusion">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\KeepWifiOnSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000003" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\LaunchAppSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\MPSSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\NETACT">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\nsi">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\Power">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\ProfSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\RpcEptMapper">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\RpcSs">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SamSs">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SecMgr">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SirepSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SystemEventsBroker">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\TestSirepSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
         <!-- Custom overrides for OEM services -->
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\OEMFactoryTestService">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
        </OSComponent>
    </Components>
</Package>
```

Sie können das Paket dann mithilfe von pkggen.exe (im Lieferumfang von Windows-Treiberkits enthalten) erstellen:

``` syntax
pkggen.exe example.pkg.xml /config:pkggen.cfg.xml
```

 

 





