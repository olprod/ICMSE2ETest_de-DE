---
title: ANWENDUNG Konfiguration-Dienstanbieter
description: ANWENDUNG Konfiguration-Dienstanbieter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0705b5e9-a1e7-4d70-a73d-7f758ffd8099
ms.openlocfilehash: 5e05d75fa416679b3c8240607f956c0b5f7d89d0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="application-configuration-service-provider"></a>ANWENDUNG Konfiguration-Dienstanbieter


Der ANWENDUNG Konfigurationsdienstanbieter wird verwendet, so konfigurieren Sie einen Anwendung Transport Clientbereitstellung Open Mobile Allianz (OMA) verwenden.

OMA betrachtet jeder Transport zu einer Anwendung und einen Dienstanbieter der entsprechenden ANWENDUNG Konfiguration erfordert. Die folgende Liste enthält die unterstützten Transporten.

-   W7 für bootstrapping ein Gerät mit einem Konto an OMA Gerätemanagement (OMA DM). Weitere Informationen finden Sie unter [w7 APPLICATION Configuration-Dienstanbieter](w7-application-csp.md)

-   W4, für die Konfiguration von Multimedia Messaging Service (MMS). Weitere Informationen finden Sie unter [w4 ANWENDUNG Konfiguration-Dienstanbieter](w4-application-csp.md)

Der Parameter APPID unterscheidet diese Anwendung Transporten. Jede APPID OMA registriert werden muss, und jeder ANWENDUNG Konfiguration-Dienstanbieter muss im Stamm des Dokuments Bereitstellung sein.

Für das Gerät ordnungsgemäß decodieren muss provisioning XML, das die APPLICATION-Eigenschaft enthält OMA-Clientbereitstellung Version 1.1 unterstützt.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






