---
author: Justinha
Description: Konfigurieren von Windows Server-Rollen
ms.assetid: c7ad0ffa-30a5-4fb3-9e69-b70fed86b694
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren von Windows Server-Rollen
ms.openlocfilehash: dd62bd2ceb8cb33b90bf0cdd90d6eaefd2134a9b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-server-roles"></a>Konfigurieren von Windows Server-Rollen


Um eine oder mehrere Serverrollen bei einer unbeaufsichtigten Installation konfigurieren möchten, können Sie das Befehlszeilentool PowerShell oder Server-Manager verwenden. Weitere Informationen zu Serverrollen finden Sie unter diese [Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=140100).

Sie können erstellen `FirstLogonCommands` in die Antwortdatei, die die erforderlichen Parameter für die Serverrolle gibt an, die Sie konfigurieren möchten. Die `FirstLogonCommands` Einstellung in [der Konfigurationsphase](oobesystem.md) konfiguriert ist. Die `FirstLogonCommands` Einstellung wird ausgeführt, unmittelbar nachdem ein Benutzer anmeldet, auf dem Computer und vor der Desktop angezeigt wird.

**Hinweis**  
Sie müssen über ein Konto mit Administratorrechten PowerShell und Server-Manager-Befehle ausführen.

 

Weitere Informationen zum Hinzufügen von den `FirstLogonCommands` festgelegt wird, finden Sie unter [Hinzufügen eines benutzerdefinierten Befehls zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915058).

Im folgenden Beispiel wird veranschaulicht, die PowerShell.exe Syntax für das Modul "Servermanager" und die Rollen DHCP, FAX-, DNS und Datei-Services installieren.

``` syntax
<FirstLogonCommands>
   <SynchronousCommand wcm:action="add">
      <Order>1</Order>
      <CommandLine> Powershell.exe –command Import-Module ServerManager; Install-WindowsFeature DHCP,FAX,DNS,File-Services</CommandLine>
      <Description>Configure Server Role</Description>
   </SynchronousCommand>
</FirstLogonCommands>
```

**Hinweis**  
Nicht alle Serverrollen unterstützen Sysprep. Sie müssen nach dem Imaging und Bereitstellung einige Serverrollen konfigurieren. Weitere Informationen finden Sie unter [Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md).

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

 

 






