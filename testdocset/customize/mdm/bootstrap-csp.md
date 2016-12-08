---
title: BOOTSTRAP CSP
description: BOOTSTRAP CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b8acbddc-347f-4543-a45b-ad2ffae3ffd0
ms.openlocfilehash: 53ea409c6f2c2437ab402f3b7be4982786e5f016
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootstrap-csp"></a>BOOTSTRAP CSP


Der Konfiguration BOOTSTRAP Dienstanbieter legt vertrauenswürdige Bereitstellung Server (TPS) für das Gerät fest.

> **Hinweis**  BOOTSTRAP CSP ist nur in Windows 10 Mobile unterstützt.

 

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_ADMIN-Funktionen aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Die folgende Abbildung zeigt den Konfiguration BOOTSTRAP Dienstanbieter im Strukturformat von Open Mobile Allianz (OMA)-Clientbereitstellung verwendet. Das Protokoll OMA Gerätemanagement wird mit dieser Konfigurationsdienstanbieter nicht unterstützt.

![Bootstrap Csp (cp)](images/provisioning-csp-bootstrap-cp.png)

<a href="" id="context-allow"></a>**KONTEXT ZULASSEN**  
Optional Gibt einen Kontext für die TPS an. Nur ein Kontext wird unterstützt, sodass dieser Parameter wird ignoriert, und wird für den Wert "0" angenommen.

<a href="" id="provurl"></a>**PROVURL**  
Erforderlich. Gibt den Speicherort von einem vertrauenswürdigen Provisioning Server (TPS). Der PROVURL-Wert muss eine vollständige URL-Zeichenfolge mit einer maximalen Länge von 256 Zeichen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






