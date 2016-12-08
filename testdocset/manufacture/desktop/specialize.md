---
author: Justinha
Description: specialize
ms.assetid: 9873c2be-c80c-47d7-a188-84e27200f2f8
MSHAttr: PreferredLib:/library/windows/hardware
title: specialize
ms.openlocfilehash: 934adb7d8b8e5c87976d8dfd6b0e5d84377890b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="specialize"></a>specialize


Computer-spezifische Informationen für das Bild wird während des **specialize** Konfiguration Schritts von Windows® Setup angewendet. Beispielsweise können Sie die Netzwerkeinstellungen, internationalen Einstellungen und Informationen zur Domäne konfigurieren.

Die Konfiguration **specialize** Pass wird zusammen mit der [verallgemeinern](generalize.md) Konfiguration Pass verwendet werden. Übergeben Sie den verallgemeinern wird verwendet, um ein Windows-Abbild Verweis zu erstellen, die in der gesamten Organisation verwendet werden kann. Dieses grundlegende Windows Verweis Bild können Sie zusätzliche erforderliche Anpassungen vor hinzufügen, die auf verschiedenen Abteilungen in einer Organisation oder auf verschiedenen Installationen von Windows gelten. Jede Methode verschieben oder Kopieren eines Windows-Abbilds zu einem neuen Computer muss mit vorbereitet werden die **Sysprep / verallgemeinern** Befehl. Weitere Informationen finden Sie unter [Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md) und [Sysprep Command-Line Options](sysprep-command-line-options.md).

Im folgende Diagramm veranschaulicht die Verwendung der **specialize** Konfigurationsdurchlauf ist diese bestimmten Anpassungen anwenden.

![specialize Konfigurationsphasen](images/dep-win8-l-specializeconfigpass.jpg)

Beispielsweise können während des Schritts **specialize** Konfiguration Sie verschiedenen Homepages im Internet Explorer® für Zweigniederlassungen oder anderen Abteilungen in Ihrem Unternehmen angeben. Diese Einstellung überschreibt die standardmäßige Startseite.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[Verallgemeinern](generalize.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[windowsPE](windowspe.md)

 

 






