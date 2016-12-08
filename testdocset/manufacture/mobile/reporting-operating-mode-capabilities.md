---
author: kpacquer
Description: Berichtsfunktionen funktionieren Modus
ms.assetid: 1beda5a7-63d7-4519-955c-cc240733fc49
MSHAttr: PreferredLib:/library/windows/hardware
title: Berichtsfunktionen funktionieren Modus
ms.openlocfilehash: c30f90714aaa4f933bb109ac10b8f064ff4d96f7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reporting-operating-mode-capabilities"></a>Berichtsfunktionen funktionieren Modus


Wenn ein Wi-Fi-Treiber im Modus Fertigung ausgeführt wird unterstützt, sollten sie die Liste der unterstützten Funktionen Fertigung Modus hinzufügen. Sie können die Funktionen der unterstützten Vorgang-Modus mithilfe von Abfragen die **OID\_DOT11\_VORGANG\_MODUS\_FUNKTION** Befehl, der Informationen auf der vom Treiber unterstützt Betriebsmodi zurückgegeben wird. Weitere Informationen zum **OID\_DOT11\_VORGANG\_MODUS\_FUNKTION**, finden Sie unter [Unterstützung OID Verhalten in manufacturing Modus aktualisiert](supporting-updated-oid-behavior-in-manufacturing-mode.md).

Der Treiber Vorgang Modus Fertigung Modus verwenden, um die **OID\_DOT11\_AKTUELLEN\_VORGANG\_MODUS** aus, um sicherzustellen, dass Fertigung Tests nicht mit der Treiber Verhalten in einem beliebigen anderen zugehörigen Modus Konflikt wird. Weitere Informationen zum **OID\_DOT11\_AKTUELLEN\_VORGANG\_MODUS**, finden Sie unter [Unterstützung OID Verhalten in manufacturing Modus aktualisiert](supporting-updated-oid-behavior-in-manufacturing-mode.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






