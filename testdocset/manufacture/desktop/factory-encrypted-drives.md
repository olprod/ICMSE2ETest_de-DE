---
author: Justinha
Description: "Factory verschlüsselt Laufwerke"
ms.assetid: 3469481b-f380-4585-87c8-ca8a267fe607
MSHAttr: PreferredLib:/library/windows/hardware
title: "Verschlüsselt Factory-Laufwerke"
ms.openlocfilehash: fcc0d7626018fcafe25af1e14b2f1fdd39cd1cf0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="factory-encrypted-drives"></a>Verschlüsselt Factory-Laufwerke


Sie können Windows auf Laufwerken Factory verschlüsselt, auch bekannt als verschlüsselte Festplatten (eHDD) installieren. Ein *Laufwerk Factory verschlüsselt* ist, der Verschlüsselung ganzer Festplatten kann.

In der Standardeinstellung bei der Installation von Windows auf einem Laufwerk Factory verschlüsselt Windows werden automatisch verschlüsselt das Laufwerk mithilfe der Trusted Computing Group (TCG) und IEEE 1667 Transport Verschlüsselungsstandards.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


Verwenden Sie zum Installieren von Windows auf einem Laufwerk Factory verschlüsselt Folgendes ein:

1.  Firmware: UEFI Version 2.3.1, die Verwendung des EFI Storage Security-Protokolls konfiguriert wurde.

2.  Hardware: ein Festplattenlaufwerk, der TCG und IEEE 1667 Transport Verschlüsselungsstandards verwenden kann.

## <a name="span-idusingotherencryptionstandardsspanspan-idusingotherencryptionstandardsspanspan-idusingotherencryptionstandardsspanusing-other-encryption-standards"></a><span id="Using_other_encryption_standards"></span><span id="using_other_encryption_standards"></span><span id="USING_OTHER_ENCRYPTION_STANDARDS"></span>Verwenden andere Verschlüsselung Standards (engl.)


Um eine andere Verschlüsselung verwenden müssen auf dem Laufwerk standard, Sie zuerst deaktivieren das automatische Bereitstellung, dass Windows bietet Laufwerk. Bei einer Neuinstallation Sie dazu die Einstellung für die unbeaufsichtigte Installation Microsoft-Windows-EnhancedStorage-Adm/TCGSecurityActivationDisabled auf **true**festgelegt. Weitere Informationen finden Sie in der [Referenz für unbeaufsichtigte Windows](https://msdn.microsoft.com/library/windows/hardware/dn923277).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Festplatten und Partitionen](hard-drives-and-partitions.md)

 

 






