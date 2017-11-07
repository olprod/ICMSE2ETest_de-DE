---
title: Strict Anbieter
description: Strict Anbieter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b75d08cc-eaa5-42b8-9bac-d9b6aa35f31a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 11db583e7ee8197b57e940b38881fba49247b6b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="strict-providers"></a>Strict Anbieter


Windows Performance Aufzeichnung (WPR) Aufzeichnung Profile werden in eine XML-Datei gespeichert, die Erweiterung .wprp hat. *Profildefinitionen* vereinen die Definitionen Collector und Anbieter in der Datei .wprp. Das Attribut **Strict** in Anbieter Definitionen steuert das Verhalten eines Profils Aufzeichnung der Anbieter nicht gleichzeitig gestartet wird, die die Aufzeichnung startet.

Anbieter für viele Gründen ein Fehler in der Implementierung des Anbieters oder ein falsch konfigurierten System wird möglicherweise nicht gestartet. Wenn ein Anbieter nicht gestartet, und seine **Strict** -Attribut auf "True", den Startvorgang festgelegt ist schlägt fehl und ein Rollback. Alle Kollektoren und Anbieter, die erfolgreich gestartet werden abgebrochen. Im Fehlerprotokoll enthält Informationen über den Anbieter, der nicht gestartet wurde. Wenn das **Strict** -Attribut auf "False" festgelegt ist, beliebig viele Kollektoren und Anbieter starten wie möglich ist und der Startvorgang erfolgreich beendet wird. Informationen zu Anbietern, die nicht gestartet wurde, wird als Warnungen anstelle von Fehlern angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Authoring Aufzeichnung Profile](authoring-recording-profiles.md)

[2. System- und Ereignis Anbieter-Definitionen](2-system-and-event-provider-definitions.md)

 

 







