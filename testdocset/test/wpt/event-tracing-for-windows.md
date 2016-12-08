---
title: Event Tracing for Windows
description: Event Tracing for Windows
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5130d144-de4d-4b6e-bfe9-e17aaddff7d0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80c1487927a74b014f3fff4b08c6c848bba32207
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="event-tracing-for-windows"></a>Event Tracing for Windows


Die Infrastruktur Event Tracing for Windows (ETW) bietet die Grundlage für Windows Performance Toolkit. Diese Tools bieten eine Reihe von Programmen, die die Komplexität der arbeiten direkt mit dem ETW-Anwendungsprogrammierschnittstellen (APIs) ausblenden.

Dieser Artikel enthält eine allgemeine Einführung in ETW. Weitere Informationen zu ETW finden Sie unter [Event Tracing](http://go.microsoft.com/fwlink/p/?linkid=213103).

ETW aktiviert das Aufzeichnen konsistente, einfache und Kernel Anwendungsereignissen. Sie können aktivieren oder Deaktivieren von Ereignis Capture können Sie jederzeit ohne Neustart des Systems oder Prozess. Windows Performance Analyzer (WPA) stellt die Informationen, die in einem leicht verständliche Satz von Diagrammen und Tabellen ETW gesammelt werden.

Sie können erfassen und präsentieren ausgewählten Ereignisse nicht invasiven identifizieren und diagnostizieren System- und Leistungsprobleme. Sie können aktivieren oder deaktivieren dynamisch tracing Ereignis. Windows Performance Aufzeichnung (WPR) verwendet ETW sammeln und Organisieren wichtige Systeminformationen an. WPR fungiert als Controller Sitzung starten und beenden die Sitzung und welche ETW-Ereignisse aufgezeichnet auswählen.

WPA verbraucht Ereignis (ETL) Ablaufverfolgungsprotokolldatei, die alle Ereignisanbieter für in einer ETW-Sitzung zu erzeugen. Kernel und Anwendungsereignissen bietet umfassende Details zu dem Vorgang des Systems. Fast alle Kernel-Ereignis, das die Systemleistung wirkt sich auf ist definiert ist und auf WPA verfügbar.

## <a name="related-topics"></a>Verwandte Themen


[Windows Performance Toolkit](index.md)

 

 







