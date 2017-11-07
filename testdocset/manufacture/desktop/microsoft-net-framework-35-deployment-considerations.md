---
author: Justinha
Description: "Bereitstellungsaspekte für Microsoft .NET Framework 3.5"
ms.assetid: c231ba55-4181-47c0-bd16-f63e428f555f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bereitstellungsaspekte für Microsoft .NET Framework 3.5"
ms.openlocfilehash: 6f8e47e77ffaab1e7a869f91c6a93a48cb773a2a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="microsoft-net-framework-35-deployment-considerations"></a>Bereitstellungsaspekte für Microsoft .NET Framework 3.5


.NET Framework 3.5 ist nicht enthalten, die standardmäßig in Windows 10 oder Windows Server 2016, jedoch können Sie herunterladen und Anwendungskompatibilität bereitstellen. In diesem Abschnitt werden diese Bereitstellungsoptionen beschrieben.

**In diesem Abschnitt:**

-   [Bereitstellen von .NET Framework 3.5 mithilfe von Richtlinienfeature Gruppe auf Anforderung-Einstellung](deploy-net-framework-35-by-using-group-policy-feature-on-demand-setting.md)
-   [Bereitstellen von .NET Framework 3.5 mithilfe von Deployment Image Servicing and Management (DISM)](deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism.md)
-   [Aktivieren Sie .NET Framework 3.5 mithilfe von Windows PowerShell](enable-net-framework-35-by-using-windows-powershell.md)
-   [Aktivieren von .NET Framework 3.5 mithilfe der Systemsteuerung und Windows-Updates (nur Windows 8)](enable-net-framework-35-by-using-control-panel-and-windows-update--windows-8-only.md)
-   [Aktivieren Sie .NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features](enable-net-framework-35-by-using-the-add-roles-and-features-wizard.md)
-   [.NET Framework 3.5 Bereitstellungsfehler und Lösungsschritte](net-framework-35-deployment-errors-and-resolution-steps.md)

## <a name="span-idintroductionspanspan-idintroductionspanspan-idintroductionspanintroduction"></a><span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>Einführung in


Windows 10 oder Windows Server 2016 enthalten .NET Framework 4.6 einer Windows-Komponente ist, die unterstützt erstellen und Ausführen der nächsten Generation von ASP.NET-Webanwendungen und Webdiensten. .NET Framework stellt eine Teilmenge der verwalteten Typen, die Sie, zum Erstellen von Windows Store-apps für Windows verwenden können mithilfe von C\# oder in Visual Basic. Weitere Informationen finden Sie unter [.NET Framework](http://go.microsoft.com/fwlink/p/?linkid=329972).

Nur die Metadaten, die zum Aktivieren von .NET Framework 3.5 erforderlich ist in der Windows-Standardbild enthalten ist **(\\Quellen\\install.wim**). Die tatsächlichen Binärdateien werden nicht in das Bild. Dieses Featurestatus wird als *deaktiviert mit Nutzlast entfernt*bezeichnet.

Sie erhalten die .NET Framework 3.5 Nutzlast Dateien über Windows Update oder dem Installationsdatenträger in den ** \\Quellen\\Sxs** Ordner. Weitere Informationen finden Sie unter [Installieren von .NET Framework 3.5](http://go.microsoft.com/fwlink/p/?linkid=257556). Nachdem das .NET Framework 3.5-Feature aktiviert ist, werden die Dateien genau wie andere Dateien des Betriebssystems Windows-Updates muss.

Bei der Aktualisierung von Windows 7 (einschließlich .NET Framework 3.5.1 [standardmäßig](http://blogs.msdn.com/b/e7/archive/2009/03/06/beta-to-rc-changes-turning-windows-features-on-or-off.aspx)auf Windows 10) oder von Windows Server 2008 R2 (mit .NET Framework 3.5.1 Feature installiert) auf Windows Server 2016 wird .NET Framework 3.5 automatisch aktiviert.

Wenn Sie Feedback zu diesem Thema verfügen, besuchen Sie das Microsoft-Forum:

-   [Windows IT Pro](http://social.technet.microsoft.com/Forums/windows/home?category=w8itpro)
-   [WindowsServer](http://social.technet.microsoft.com/Forums/windowsserver/home?category=windowsserver)
-   [Windows Store-apps](http://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Optionen für die Installation von Windows Server](http://go.microsoft.com/fwlink/p/?linkid=251454)

 

 






