---
title: Anbieter
description: Anbieter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2da92ebb-055a-45ff-8da6-7a06f78a8d9e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0c4f17a2e7ae5e0ca3910b304f38ec8e23073d03
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="providers"></a>Anbieter


Anbieter sind Event Tracing for Windows (ETW) Komponenten, die Ereignisse auf Windows Performance Aufzeichnung (WPR) verfügbar machen. Sie können ein einzelnes Systemanbieter und mehrere Anbieter in einem Profil, einschließlich von einem Provider Heap Ereignisse verwenden.

## <a name="system-providers"></a>System-Anbieter


Ein Systemanbieter stellt Kernelereignisse bereit. System-Anbieter werden mithilfe des folgenden definiert:

-   Schlüsselwörter für die Ereignisse gesammelt werden.

-   Stapel aus dem Ereignisse erfasst werden sollen.

-   Pooltags an, dass die Komponente, die die Zuordnung oder die Zuordnung vorgenommen eingeben.

Eine Beschreibung der unterstützten System Schlüsselwörter finden Sie unter [Keyword (in "Systemprovider")](keyword--in-systemprovider-.md).

## <a name="event-providers"></a>Ereignisanbieter


Anbieter für bestimmte Arten von Ereignissen (berücksichtigt, die vom Anbieter unterstützt werden) bereitstellen, indem Sie ein Schlüsselwort hexadezimale Bitmaske angeben können konfiguriert werden. Da Anbieter andere Ereignisse unterstützt, sind es keine Zeichenfolgenkonstanten für diese Schlüsselwörter. Aus diesem Grund müssen diese Zeichenfolgen im Hexadezimal-Format sein.

## <a name="related-topics"></a>Verwandte Themen


[WPR-Features](wpr-features.md)

[2. System- und Ereignis Anbieter-Definitionen](2-system-and-event-provider-definitions.md)

 

 







