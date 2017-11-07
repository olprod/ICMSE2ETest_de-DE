---
author: Justinha
Description: offlineServicing
ms.assetid: 8c921c85-c986-419c-9f93-bdacd9441abb
MSHAttr: PreferredLib:/library/windows/hardware
title: offlineServicing
ms.openlocfilehash: 12f000093127dcafe144db254fd23d8b8c92e7f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="offlineservicing"></a>offlineServicing


Verwenden Sie die **OfflineServicing** Konfiguration übergeben, um unbeaufsichtigte Installation Einstellungen gelten für Schwelle Microsoft® Windows® offline. Während dieser Konfigurationsphase können Sie die offline-Abbild Sprachpakete, Updates, Gerätetreiber oder andere Pakete hinzufügen.

Übergeben Sie die **OfflineServicing** Konfiguration wird während der Installation von Windows ausgeführt werden. Setup führt dann Deployment Image Servicing and Management (Dism.exe) Tool extrahiert und das Windows-Abbild installiert. Pakete aufgelistet, die der `<servicing>` Abschnitt und Einstellungen in der `<offlineServicing>` Abschnitt der Antwortdatei auf dem Windows-Abbild offline angewendet werden.

Darüber hinaus können Sie das Tool Abbildern Bereitstellung und Verwaltung mit einer Antwortdatei verwenden, Einstellungen im Durchgang **OfflineServicing** angewendet. Weitere Informationen finden Sie unter [Service ein DISM mithilfe eines Windows Bild](service-a-windows-image-using-dism.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[Verallgemeinern](generalize.md)

[oobeSystem](oobesystem.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






