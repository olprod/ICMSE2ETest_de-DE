---
title: Speicher CSP
description: Speicher CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b19bdb54-53ed-42ce-a5a1-269379013f57
ms.openlocfilehash: 064c287b271a4085b212b616e1df86add499d4f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="storage-csp"></a>Speicher CSP


Enterprise-Konfiguration Service Speicheranbieter wird verwendet, um die Karte speichereinstellungen konfigurieren. Derzeit ist die einzige Einstellung, die zu konfigurierende zum Aktivieren oder Deaktivieren von Speicherkarten.

> **Hinweis**  Der Speicher CSP ist in Windows 10 veraltet, und es wird nur in Windows 10 Mobile unterstützt, für die Abwärtskompatibilität. Verwenden Sie stattdessen System/AllowStorageCard im [Bereich CSP Richtlinie](policy-configuration-service-provider.md) .

 

Das folgende Diagramm zeigt den Speicher Konfigurationsdienstanbieter in der Strukturformat.

![Bereitstellung\-Csp\-Speicher](images/provisioning-csp-storage.png)

<a href="" id="disable"></a>**Deaktivieren**  
Erforderlich. Ein boolescher Wert, der angibt, ob zum Aktivieren oder Deaktivieren einer Speicherkarte. Der Wert **True** wird die Speicherkarte deaktiviert. Der Wert **"false"** ermöglicht die Speicherkarte. Der Standardwert ist **False**. Der Wert wird Groß-/Kleinschreibung beachtet.

Die unterstützten Vorgänge sind Get und ersetzen.

> **Hinweis**   Wenn das Gerät einen Fehler 404 Code zurückgibt, wenn der Server den Befehl Get nach ./Vendor/MSFT/Storage/deaktivieren anwendet, bedeutet dies, dass das Gerät keine SD-Karte.

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






