---
title: "Verwenden von PowerShell-Skripts mit dem WMI-Anbieter-Brücke"
description: "In diesem Thema wird die Verwendung von Cmdlets für PowerShell-Skripts zum Konfigurieren von pro Benutzer und pro Gerät Richtlinieneinstellungen sowie zum Aufrufen von Methoden über die WMI-Brücke Anbieter wie behandelt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 238D45AD-3FD8-46F9-B7FB-6AEE42BE4C08
ms.openlocfilehash: be158e286d454e9958933ed4892568dafa0d6187
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-powershell-scripting-with-the-wmi-bridge-provider"></a>Verwenden von PowerShell-Skripts mit dem WMI-Anbieter-Brücke

In diesem Thema werden mithilfe von PowerShell-Cmdlets Skripts so konfigurieren Sie pro Benutzer und pro Gerät Richtlinieneinstellungen sowie zum Aufrufen von Methoden über den [WMI-Anbieter für Bridge](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx).


## <a name="configuring-per-device-policy-settings"></a>Konfigurieren von Richtlinieneinstellungen pro Gerät

Dieser Abschnitt enthält eines PowerShell-Cmdlets Beispielskript zum Konfigurieren der Einstellungen über die [WMI-Brücke Anbieter](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx)pro Gerät. Wenn Sie eine Klasse für Geräte unterstützt, muss Klasse Ebene Qualifizierer für InPartition("local-system") definiert sein.

Für alle geräteeinstellungen muss der WMI-Brücke Client unter Benutzer lokales System ausgeführt werden. Klicken Sie dazu das Tool Psexec aus <https://technet.microsoft.com/sysinternals/bb897553.aspx> laden, und führen Sie `psexec.exe -i -s cmd.exe` aus einer Eingabeaufforderung mit erhöhten Rechten Admin.

Das Skriptbeispiel in diesem Abschnitt wird die Klasse [MDM\_Richtlinie\_Config01\_WiFi02](https://msdn.microsoft.com/library/windows/desktop/dn905246.aspx):

```ManagedCPlusPlus
[dynamic, provider("DMWmiBridgeProv"), InPartition("local-system")]
class MDM_Policy_Config01_WiFi02
{
  string InstanceID;
  string ParentID;
  sint32 AllowInternetSharing;
  sint32 AllowAutoConnectToWiFiSenseHotspots;
  sint32 WLANScanMode;
};
```

Das folgende Skript beschreibt das Erstellen, Aufzählen, Abfragen, ändern und Löschen von Instanzen.

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_Policy_Config01_WiFi02"

# Create a new instance for MDM_Policy_Config01_WiFi02 
New-CimInstance -Namespace $namespaceName -ClassName $className -Property @{ParentID="./Vendor/MSFT/Policy/Config";InstanceID="WiFi";AllowInternetSharing=1;AllowAutoConnectToWiFiSenseHotspots=0;WLANScanMode=100}

# Enumerate all instances available for MDM_Policy_Config01_WiFi02
Get-CimInstance -Namespace $namespaceName -ClassName $className

# Query instances with matching properties
Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"

# Modify existing instance
$obj = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"
$obj.WLANScanMode=500
Set-CimInstance -CimInstance $obj

# Delete existing instance
try
{
    $obj = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"
    Remove-CimInstance -CimInstance $obj
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="configuring-per-user-settings"></a>Konfigurieren von benutzerspezifischen Einstellungen

Dieser Abschnitt enthält ein PowerShell-Cmdlet Beispielskript zum Konfigurieren von benutzerspezifischen Einstellungen über die WMI-Brücke. Wenn eine Klasse benutzereinstellungen unterstützt, es muss Klasse Ebene Qualifizierer für InPartition("local-user") definiert.

Für das Skriptbeispiel in diesem Abschnitt verwendet die Klasse [MDM\_Richtlinie\_Benutzer\_Config01\_Authentication02](https://msdn.microsoft.com/library/windows/desktop/mt146854.aspx):

```ManagedCPlusPlus
[dynamic, provider("DMWmiBridgeProv"), InPartition("local-user")]
class MDM_Policy_User_Config01_Authentication02
{
  string InstanceID;
  string ParentID;
  sint32 AllowEAPCertSSO;
};
```

> **Hinweis**  Wenn derzeit angemeldeten Benutzers benutzereinstellungen für sich selbst zu zuzugreifen versucht, ist es viel einfacher, das pro Gerät Einstellungen Skript aus dem vorherigen Abschnitt verwenden. Klicken Sie unter eine Eingabeaufforderung mit erhöhten Rechten Admin muss alle PowerShell-Cmdlets ausgeführt werden.

 

Zugreifen auf oder Ändern von Einstellungen für einen anderen Benutzer wird Klicken Sie dann das PowerShell-Skript komplizierter, da die WMI-Brücke erwartet, dass die Benutzer-SID kontextabhängig Custom MI festgelegt werden soll, die nicht in systemeigenen PowerShell Cmdlets unterstützt wird.

> **Hinweis**   Alle Befehle müssen unter Lokales System ausgeführt.

 

Ein Benutzer SID kann, durch die Windows-Befehl abgerufen werden `wmic useraccount get name, sid`. Im folgenden Skriptbeispiel wird davon ausgegangen, dass die Benutzer-SID S-1-5-21-4017247134-4237859428-3008104844-1001 ist.

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_Policy_User_Config01_Authentication02"

# Configure CIM operation options with target user info
$options = New-Object Microsoft.Management.Infrastructure.Options.CimOperationOptions
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Type", "PolicyPlatform_UserContext", $false)
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Id", "S-1-5-21-4017247134-4237859428-3008104844-1001", $false)

# Construct session used for all operations
$session = New-CimSession

##########################################################################
# Create a new instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("AllowEAPCertSSO", 1, "Sint32", "Property")
$newInstance.CimInstanceProperties.Add($property)
try
{
    $session.CreateInstance($namespaceName, $newInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Enumerate all instances for MDM_Policy_User_Config01_Authentication02
##########################################################################
$session.EnumerateInstances($namespaceName, $className, $options)

##########################################################################
# Query instance for MDM_Policy_User_Config01_Authentication02
# with matching properties
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $session.GetInstance($namespaceName, $getInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Modify existing instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $updateInstance = $session.GetInstance($namespaceName, $getInstance, $options)[0]
    $updateInstance.AllowEAPCertSSO = 0
    $session.ModifyInstance($namespaceName, $updateInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Delete existing instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $deleteInstance = $session.GetInstance($namespaceName, $getInstance, $options)[0]
    $session.DeleteInstance($namespaceName, $deleteInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="invoking-methods"></a>Aufrufen von Methoden

Dieser Abschnitt enthält ein PowerShell-Cmdlet Beispielskript, um eine WMI-Brücke Objektmethode aufzurufen. Das folgende Skript muss unter Benutzer lokales System ausgeführt werden. Klicken Sie dazu das Tool Psexec aus <https://technet.microsoft.com/sysinternals/bb897553.aspx> laden, und führen Sie `psexec.exe -i -s cmd.exe` aus einer Eingabeaufforderung mit erhöhten Rechten Admin.

Für das Skriptbeispiel in diesem Abschnitt wird die [UpgradeEditionWithProductKeyMethod](https://msdn.microsoft.com/library/windows/desktop/mt599805.aspx) -Methode der der [MDM\_WindowsLicensing](https://msdn.microsoft.com/library/windows/desktop/dn948453.aspx) Klasse.

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_WindowsLicensing"
$methodName = "UpgradeEditionWithProductKeyMethod"
$fakeProductKey = "7f1a3659-3fa7-4c70-93ce-0d354e8e158e"

$session = New-CimSession

$params = New-Object Microsoft.Management.Infrastructure.CimMethodParametersCollection
$param = [Microsoft.Management.Infrastructure.CimMethodParameter]::Create("param", $fakeProductKey, "String", "In")
$params.Add($param)

try
{
    $instance = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT&#39; and InstanceID=&#39;WindowsLicensing&#39;"
    $session.InvokeMethod($namespaceName, $instance, $methodName, $params)
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="related-topics"></a>Verwandte Themen

[Brücke WMI-Anbieter](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx)

 





