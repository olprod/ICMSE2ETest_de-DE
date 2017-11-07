---
author: Justinha
Description: auditUser
ms.assetid: 34da792a-51fa-4a4d-a67e-6390cb5be2a1
MSHAttr: PreferredLib:/library/windows/hardware
title: auditUser
ms.openlocfilehash: b86cfceac044182629c96d1614a2b1af11c01c21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="audituser"></a>auditUser


Übergeben Sie die **AuditUser** Konfiguration verarbeitet unbeaufsichtigte Windows® Setup Einstellungen im Kontext des Benutzers im Überwachungsmodus aktiviert. Übergeben Sie die **AuditUser** Konfiguration wird immer nach der [AuditSystem](auditsystem.md) Durchlauf dient zum Anwenden von Einstellungen im Systemkontext ausgeführt. In der Regel wird die **AuditUser** Konfiguration Pass **RunSynchronous** oder **RunAsynchronous** Befehle ausführen. Diese Befehle dienen zum Ausführen von Skripts, Webanwendungen oder andere ausführbare Dateien im Überwachungsmodus. Wenn Windows im Überwachungsmodus gestartet wird, werden die AuditSystem und **AuditUser** Einstellungen für die unbeaufsichtigte Installation von Windows verarbeitet.

Überwachungsmodus ermöglicht OEMs und Unternehmen auf ein Master-Shape Windows® Bild zusätzliche Gerätetreiber, Anwendungen und andere Updates installieren. Weniger Bilder mithilfe von Überwachungsmodus aktiviert, kann beibehalten werden, da Sie einen Verweis Bild mit einem minimalen Satz von Treibern und Anwendungen erstellen können. Das Referenzabbild kann dann mit zusätzlichen Treiber im Überwachungsmodus aktualisiert werden. Darüber hinaus können Sie testen und Auflösen Probleme mit fehlerhaft oder falsch verbunden Geräte auf das Windows-Abbild installiert vor der Lieferung des Computers an einen Kunden. Überwachungsmodus ist optional.

Im folgende Diagramm ist dargestellt, bei der Verarbeitung des **AuditUser** Konfigurationsdurchlauf im Überwachungsmodus aktiviert.

![übergeben Sie Auditmode Konfiguration](images/dep-win8-l-auditmode.jpg)

Übergeben Sie die **AuditUser** Konfiguration führt nur, wenn Sie Windows-Setup zu starten im Überwachungsmodus zu konfigurieren. Sie können im Überwachungsmodus starten mithilfe der **Sysprep/audit** oder **Sysprep / / audit verallgemeinern** Befehle oder Sie können die Einstellung **Reseal** angeben, in der Microsoft-Windows-Deployment-Komponente. Weitere Informationen zum Überwachungsmodus finden Sie unter [Überwachen Modus Übersichts-](audit-mode-overview.md) und [Boot Windows Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[Verallgemeinern](generalize.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






