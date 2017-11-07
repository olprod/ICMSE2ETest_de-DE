---
title: Detailstufe
description: Detailstufe
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8a1de1e7-dea5-4ab2-b707-2a1ee109b0f1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f1061098643d678b3dab7a72349f27f674af2f84
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="detail-level"></a>Detailstufe


Windows Performance Aufzeichnung (WPR) Aufzeichnung Profile steuern alle Aspekte einer Aufzeichnung. Für jedes Profil WPR müssen Sie eine Detailstufe auswählen. Die verfügbaren Ebenen sind **hell** und **Verbose**. Die Detailebene **Licht** wird hauptsächlich für Timing-Aufzeichnungen verwendet. Die Detailebene **Verbose** bietet detaillierte Informationen, die Sie für die Analyse benötigen. Integrierte Profile unterstützen **Verbose** und **geringfügigen** Detail-Ebenen.

Die Ebene **Verbose** ist standardmäßig auf beide der WPR-Benutzeroberfläche (UI) und in der Befehlszeile WPR ausgewählt.

Wenn Sie benutzerdefinierte Profile erstellen haben, wird empfohlen, eine light-Version und eine ausführliche Version in derselben .wprp Datei zu definieren. Diese Dateien können bis zu vier Profildefinitionen enthalten: einen für jede Kombination aus Detailstufe und Protokollierungsmodus.

## <a name="related-topics"></a>Verwandte Themen


[WPR-Features](wpr-features.md)

[Protokollierungsmodus](logging-mode.md)

[3. Definitionen für Profil](3-profile-definitions.md)

[Ändern der Detailebene](change-the-detail-level.md)

[Authoring Aufzeichnung Profile](authoring-recording-profiles.md)

 

 







