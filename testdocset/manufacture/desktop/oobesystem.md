---
author: Justinha
Description: oobeSystem
ms.assetid: afe6d754-0ca6-4252-87c7-bfc234a2cc6a
MSHAttr: PreferredLib:/library/windows/hardware
title: oobeSystem
ms.openlocfilehash: cb540a144351a11fa65523b6d11351c79eb4a3f0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oobesystem"></a>oobeSystem


**Die Konfigurationsphase** konfiguriert Einstellungen, die während der ersten Neustarts Endbenutzer auch genannt Out-Of-Box auftreten (OOBE) angewendet werden. Die Konfigurationseinstellungen Pass **OobeSystem** werden vor einem ersten Anmeldung Windows® verarbeitet.

Out-of-Box-Experience (OOBE) führt der ersten der Benutzer einen neu konfigurierten Computer startet. OOBE wird vor der Windows-Shell oder zusätzliche Software ausgeführt wird und eine kleine Gruppe von Aufgaben, die erforderlich sind, konfigurieren und Ausführen von Windows ausgeführt werden.

Im folgende Diagramm veranschaulicht den Prozess, der tritt auf, wenn ein Endbenutzer einen neu konfigurierten Computer zuerst gestartet wird. Das Ergebnis ist OOBE oder eines Benutzers ersten Starten zu.

![Windows-Willkommensseite Konfigurationsphasen](images/dep-win8-l-windowswelcomeconfigpass.jpg)

Sie können Windows starten mithilfe des **Sysprep** -Befehls mithilfe der **Option/Oobe** OOBE konfigurieren. Nach Abschluss von Setup Windows startet standardmäßig OOBE.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[Verallgemeinern](generalize.md)

[offlineServicing](offlineservicing.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






