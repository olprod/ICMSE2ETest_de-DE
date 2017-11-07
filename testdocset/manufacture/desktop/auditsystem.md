---
author: Justinha
Description: auditSystem
ms.assetid: 86d77a1f-2244-4600-80cd-65930a2cee3d
MSHAttr: PreferredLib:/library/windows/hardware
title: auditSystem
ms.openlocfilehash: 7598b94e9b291a55f6de8d48ab89b9f05cdc11ec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="auditsystem"></a>auditSystem


Übergeben Sie die **AuditSystem** Konfiguration verarbeitet unbeaufsichtigte Windows® Setup Einstellungen im Kontext des System im Überwachungsmodus aktiviert. Übergeben Sie die **AuditSystem** Konfiguration unmittelbar vor dem zum Anwenden von Einstellungen im Benutzerkontext [AuditUser](audituser.md) -Durchgang Konfiguration ausgeführt wird. Bei Windows-Start-Modus, übergeben Sie die **AuditSystem** Konfiguration und der unbeaufsichtigten AuditUser überwacht werden Windows Setup Einstellungen verarbeitet.

Überwachungsmodus ermöglicht OEMs und Unternehmen zu einem Master-Shape Windows-Abbild zusätzliche Gerätetreiber, Anwendungen und andere Updates installieren. Weniger Bilder mithilfe von Überwachungsmodus aktiviert, kann beibehalten werden, da Sie einen Verweis Bild mit einem minimalen Satz von Treibern und Anwendungen erstellen können. Das Referenzabbild kann dann mit zusätzlichen Treiber im Überwachungsmodus aktualisiert werden. Darüber hinaus können Sie testen, klicken Sie dann und Auflösen Probleme mit fehlerhaft oder falsch verbunden Geräte auf das Windows-Abbild installiert vor der Lieferung des Computers an einen Kunden. Überwachungsmodus ist optional.

Im folgenden Diagramm wird, wenn der **AuditSystem** Konfigurationsdurchlauf im Überwachungsmodus verarbeitet wird.

![übergeben Sie Auditmode Konfiguration](images/dep-win8-l-auditmode.jpg)

Übergeben Sie die **AuditSystem** Konfiguration führt nur, wenn Sie Windows-Setup zu starten im Überwachungsmodus konfigurieren. Sie können im Überwachungsmodus starten mithilfe des **Sysprep** -Befehls mit der Option **Überwachen** , oder der Befehl **Sysprep** mit den Optionen **verallgemeinern** und **Überwachen** , oder Sie können die Einstellung **Reseal** angeben, in der Microsoft Windows-Deployment-Komponente. Weitere Informationen finden Sie unter [Übersicht über Audit-Modus](audit-mode-overview.md) und [Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditUser](audituser.md)

[Verallgemeinern](generalize.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






