---
author: Justinha
Description: Verwenden Sie DISM in Windows PowerShell
ms.assetid: c258fead-059f-4a03-b6af-24cdc7451ca3
MSHAttr: PreferredLib:/library/windows/hardware
title: Verwenden Sie DISM in Windows PowerShell
ms.openlocfilehash: 076b603410d23827606747c645dee141056588c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-dism-in-windows-powershell"></a>Verwenden Sie DISM in Windows PowerShell


Die Cmdlets Deployment Image Servicing and Management (DISM) kann verwendet werden, um die gleichen Funktionen wie das Befehlszeilentool DISM.exe auszuführen. In vielen Fällen DISM-Cmdlet-Namen entsprechen direkt Dism.exe Optionen, und die gleichen Argumente können verwendet werden. Da es auch Fälle gibt, in dem die DISM-Cmdlet-Namen nicht direkt mit Dism.exe Optionen übereinstimmen, wird eine Tabelle, die Befehle Dism.exe DISM Cmdlets zugeordnet, hier bereitgestellt:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">DISM.exe Befehl</th>
<th align="left">DISM-cmdlet</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DISM.exe /Add-Capability</p></td>
<td align="left"><p>Hinzufügen von WindowsCapability</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Append-Image</p></td>
<td align="left"><p>Hinzufügen von WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Apply-Image</p></td>
<td align="left"><p>Erweitern Sie WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Capture-Image</p></td>
<td align="left"><p>Neue WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Cleanup-MountPoints</p></td>
<td align="left"><p>Clear-WindowsCorruptMountPoint</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Commit-Image</p></td>
<td align="left"><p>Speichern WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Export-Image</p></td>
<td align="left"><p>Export-WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Get-Capabilities</p></td>
<td align="left"><p>Get-WindowsCapability</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Get-ImageInfo</p></td>
<td align="left"><p>Get-WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Get-MountedImageInfo</p></td>
<td align="left"><p>Get-WindowsImage-bereitgestellt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Get-WimBootEntry</p></td>
<td align="left"><p>Get-WIMBootEntry</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /List-Image</p></td>
<td align="left"><p>Get-WindowsImageContent</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Mount-Image</p></td>
<td align="left"><p>Mount-WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Split-Image</p></td>
<td align="left"><p>Split-WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Remove-Capability</p></td>
<td align="left"><p>Remove-WindowsCapability</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Remove-Image</p></td>
<td align="left"><p>Remove-WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Remount-Image</p></td>
<td align="left"><p>Mount-WindowsImage-stellen Sie erneut bereit</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe /Unmount-Image</p></td>
<td align="left"><p>Dismount-WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe /Update-WimBootEntry</p></td>
<td align="left"><p>Update-WIMBootEntry</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;...&gt; / Hinzufügen-Treiber</p></td>
<td align="left"><p>Hinzufügen von WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Add-Package</p></td>
<td align="left"><p>Hinzufügen von WindowsPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Add-ProvisionedAppxPackage</p></td>
<td align="left"><p>Hinzufügen von AppxProvisionedPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Apply-Unattend</p></td>
<td align="left"><p>Anwenden von WindowsUnattend</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Cleanup-Image /CheckHealth</p></td>
<td align="left"><p>Reparatur WindowsImage - CheckHealth</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Cleanup-Image /ScanHealth</p></td>
<td align="left"><p>Reparatur WindowsImage - ScanHealth</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Cleanup-Image /RestoreHealth</p></td>
<td align="left"><p>Reparatur WindowsImage - RestoreHealth</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Disable-Feature</p></td>
<td align="left"><p>Disable-WindowsOptionalFeature</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Enable-Feature</p></td>
<td align="left"><p>Enable-WindowsOptionalFeature</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Export-Driver</p></td>
<td align="left"><p>Export-WindowsDriver</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-CurrentEdition</p></td>
<td align="left"><p>Get-WindowsEdition-aktuelle</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-Driverinfo</p></td>
<td align="left"><p>Get-WindowsDriver-Treiber</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-Drivers</p></td>
<td align="left"><p>Get-WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; FeatureInfo</p></td>
<td align="left"><p>Get-WindowsOptionalFeature - FeatureName</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-Features</p></td>
<td align="left"><p>Get-WindowsOptionalFeature</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-Packageinfo</p></td>
<td align="left"><p>Get-WindowsPackage - PackagePath | Paketname-</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-Packages</p></td>
<td align="left"><p>Get-WindowsPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-ProvisionedAppxPackages</p></td>
<td align="left"><p>Get-AppxProvisionedPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Get-TargetEditions</p></td>
<td align="left"><p>Get-WindowsEdition-Ziel</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Optimize-Image</p></td>
<td align="left"><p>Optimieren der Leistung von WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; Driver</p></td>
<td align="left"><p>Remove-WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Remove-Package</p></td>
<td align="left"><p>Remove-WindowsPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Remove-ProvisionedAppxPackage</p></td>
<td align="left"><p>Remove-AppxProvisionedPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Set-Edition</p></td>
<td align="left"><p>Set-WindowsEdition</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Set-ProductKey</p></td>
<td align="left"><p>Set-WindowsProductKey</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISM.exe/Image:&lt;... &gt; /Set-ProvisionedAppxDataFile</p></td>
<td align="left"><p>Set-AppXProvisionedDataFile</p></td>
</tr>
</tbody>
</table>

 

**Installieren Sie das Windows Assessment and Deployment Kit (Optional)**

-   Das Modul DISM PowerShell ist in Windows 10 und Windows Server 2016 – Technische Vorschau enthalten. Auf anderen unterstützten Betriebssystemen können Sie das Windows Assessment and Deployment Kit (ADK) einschließlich das DISM PowerShell-Modul installieren.

**Installieren Sie Windows PowerShell 5.0**

-   Windows Powershell 5.0 ist für Windows 10 und Windows Server 2016 – Technische Vorschau in der Installation enthalten. Für andere älteren unterstützten Versionen von Windows und Windows Server müssen Sie Windows Management Framework 5.0 installieren. Sie können herunterladen und Installieren von [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) aus dem Microsoft Download Center.

**So bereiten Sie die DISM PowerShell-Umgebung**

1.  PowerShell mit Administratorrechten auf dem Bildschirm **Start** öffnen Geben Sie **PowerShell**, mit der rechten Maustaste in der **Windows PowerShell** -app-Kachel und klicken Sie auf der app-Leiste auf **als Administrator ausführen**.

2.  Importieren Sie das Modul DISM PowerShell.

    Das DISM PowerShell-Modul ist in 10 für Windows und Windows Server 2016 – Technische Vorschau enthalten und muss nicht importiert werden.

    Auf anderen unterstützten Betriebssystemen können Sie das DISM-PowerShell-Modul in der Windows-ADK enthalten. Standardmäßig wird das Modul mit DISM Ordner in Windows ADK installiert * &lt;X86 oder amd64&gt;*\\DISM\\ unter dem Pfad: C:\\Program Files (x86)\\Windows Kits\\10.0\\Assessment and Deployment Kit\\Bereitstellungstools\\ in Windows 10. Geben Sie zum Importieren von diesem Modul an der Befehlszeile Folgendes ein:

    ``` syntax
    import-module <path to DISM folder>
    ```

    Verwenden beispielsweise die Windows-10-Version von Windows ADK auf einem 64-Bit-PC-Typ:

    ``` syntax
    import-module "C:\Program Files (x86)\Windows Kits\10.0\Assessment and Deployment Kit\Deployment Tools\amd64\DISM"
    ```

    **Hinweis**  
    **Import-Module** importiert ein Modul nur in der aktuellen Sitzung. Fügen Sie zum Importieren des Moduls in allen Sitzungen, einen Befehl **Import-Module** an das PowerShell-Profil. Geben Sie für Weitere Informationen zu Benutzerprofilen, `get-help about_profiles`.

     

3.  Legen Sie die `%path%` Umgebungsvariable an den Speicherort des Ordners DISM bei der Installation von Windows ADK. Geben Sie in der Befehlszeile Folgendes ein:

    ``` syntax
    $env:path = <path to DISM folder>
    ```

    Wenn Sie Umgebungsvariablen in PowerShell ändern, wirkt sich die Änderung nur die aktuelle Sitzung. Um eine beständige Änderung an eine Umgebungsvariable vornehmen, in dem die Änderung in der Registrierung gespeichert, verwenden Sie in der Systemsteuerung. Weitere Informationen finden Sie unter [Hinzufügen oder Ändern der Werte von Umgebungsvariablen](http://go.microsoft.com/fwlink/?LinkId=223710).

**So erhalten Sie Hilfe für DISM PowerShell-cmdlets**

-   Wenn Sie die Syntax mit einem Cmdlet, eine Befehlszeile verwenden möchten, geben Sie Folgendes ein:

    ``` syntax
    get-help <cmdlet name>
    ```

    Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    get-help get-WindowsImage
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM unterstützte Plattformen](dism-supported-platforms.md)

 

 






