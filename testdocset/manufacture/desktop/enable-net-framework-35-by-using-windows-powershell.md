---
author: Justinha
Description: Aktivieren Sie .NET Framework 3.5 mithilfe von Windows PowerShell
ms.assetid: af189974-cffa-46d9-950a-40f5e28d378f
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktivieren Sie .NET Framework 3.5 mithilfe von Windows PowerShell
ms.openlocfilehash: 47447b9e70763eb5242e29851584c458b23baf07
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-net-framework-35-by-using-windows-powershell"></a>Aktivieren Sie .NET Framework 3.5 mithilfe von Windows PowerShell


Für ein Windows Server® 2012 Core-Installation, die nicht mit dem Internet verbunden ist, Sie können mithilfe von Windows PowerShell zum Hinzufügen von .NET Framework 3.5 und gewähren Sie Zugriff auf die ** \\Quellen\\Sxs** Ordner auf dem Installationsmedium. Die ** \\Quellen\\Sxs** Ordner Netzwerkfreigabe kopiert werden kann (beispielsweise \\ \\Netzwerk\\freigeben\\Sxs) auf mehreren Computern leicht zugänglich machen. Konto auf dem Zielcomputer DOMÄNE\\SERVERNAME$ muss mindestens Zugriff auf die Netzwerkfreigabe gelesen haben.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


-   WindowsServer 2012

-   Installationsmedien

-   Systemadministratorrechte. Der aktuelle Benutzer muss ein Mitglied der lokalen Gruppe Administratoren hinzufügen oder Entfernen von Windows-Features.

-   Zielcomputern benötigen möglicherweise Netzwerkzugriff und Rechte für die Verwendung von alternativen Quellen oder dem Internet verbunden, um Windows Update zu verwenden.

## <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>Schritte


1.  Starten von Windows PowerShell durch Eingabe in das Administrator-Eingabeaufforderung:

    ``` syntax
    powershell
    ```

2.  Wenn Sie .NET Framework 3.5 vom Installationsmedium befindet sich auf einer Netzwerkfreigabe installieren, verwenden Sie den folgenden Befehl ein:

    ``` syntax
    Install-WindowsFeature Net-Framework-Core -source \\network\share\sxs
    ```

    Wobei * \\ \\Netzwerk\\freigeben\\Sxs* ist der Speicherort der Quelldateien.

    Weitere Informationen zu dem Cmdlet Install-WindowsFeature finden Sie unter [Install-WindowsFeature](http://go.microsoft.com/fwlink/p/?linkid=329977).

3.  Führen Sie den folgenden Befehl, um die Installation zu überprüfen:

    ``` syntax
    Get-WindowsFeature
    ```

    Die **Installationsstatus** Spalte sollte **Installed** für das Feature für **.NET Framework 3.5 (einschließlich .NET 2.0 und 3.0)** angezeigt werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellungsaspekte für Microsoft .NET Framework 3.5](microsoft-net-framework-35-deployment-considerations.md)

 

 






