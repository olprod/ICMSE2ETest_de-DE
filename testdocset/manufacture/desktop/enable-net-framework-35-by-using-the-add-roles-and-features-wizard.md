---
author: Justinha
Description: "Aktivieren Sie .NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features"
ms.assetid: 08b011c7-7f15-4fd5-9a19-c99249e4f642
MSHAttr: PreferredLib:/library/windows/hardware
title: "Aktivieren Sie .NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features"
ms.openlocfilehash: fb6f73220f86e4cd4e0891dbb98eae41de909970
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-net-framework-35-by-using-the-add-roles-and-features-wizard"></a>Aktivieren Sie .NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features


Server-Manager können Sie .NET Framework 3.5 für eine lokale oder remote-Installation von Windows Server 2012 R2 aktivieren.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


-   Windows Server 2012 R2

-   Installationsmedien

-   Systemadministratorrechte. Der aktuelle Benutzer muss ein Mitglied der lokalen Gruppe Administratoren hinzufügen oder Entfernen von Windows-Features.

-   Zielcomputern benötigen möglicherweise Netzwerkzugriff und Rechte für die Verwendung von alternativen Quellen oder dem Internet verbunden, um Windows Update zu verwenden.

## <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>Schritte


1.  Klicken Sie im Server-Manager auf **Verwalten** und wählen Sie dann **Hinzufügen von Rollen und Funktionen** zum Hinzufügen von Rollen und Funktionen-Assistenten zu starten.

2.  Wählen Sie auf dem Bildschirm **Installationsart wählen Sie** **rollenbasierte oder funktionsbasierte Installation**aus.

3.  Wählen Sie aus dem Zielserver.

4.  Auf dem Bildschirm **Features auswählen** das Kontrollkästchen Sie neben **.net Framework 3.5-Features**.

5.  Auf dem Bildschirm **Installationsauswahl bestätigen** wird eine Warnung auf Fragen angezeigt werden **müssen Sie einen Alternative Quellpfad angeben?**. Wenn der Computer keinen Zugriff auf Windows Update, klicken Sie auf den Link **Angeben einer alternativen Quellpfad** , um den Pfad zum Angeben der ** \\Quellen\\Sxs** Ordner auf dem Installationsmedium, und klicken Sie dann auf **OK**. Nachdem Sie die alternative Quelle angegeben haben, oder wenn der Zielcomputer Zugriff auf Windows Update ist, klicken Sie auf das **X** neben der Warnung, und klicken Sie dann auf **Installieren**.

    Wenn Sie Server-Manager in Windows Server 2012 zum Hinzufügen einer Rolle oder das Feature auf einem Remoteserver Computerkonto des Servers Serverdienst (DOMÄNE\\ComputerName$) benötigt Zugriff auf den Dateipfad alternative Quelle, da der Bereitstellungsvorgang im Kontext SYSTEM auf dem Zielserver ausgeführt wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellungsaspekte für Microsoft .NET Framework 3.5](microsoft-net-framework-35-deployment-considerations.md)

 

 






