---
title: Anzeigen des Aufzeichnungsstatus einer
description: Anzeigen des Aufzeichnungsstatus einer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a0df113f-d0be-4560-9f6a-3df9ae93bdd4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4d89a23a0160551f08ea4830bff1122158df5a91
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="view-a-recording-status"></a>Anzeigen des Aufzeichnungsstatus einer


Nachdem Sie eine Aufzeichnung in Windows Performance Aufzeichnung (WPR) gestartet haben, können Sie den Status der Aufzeichnung folgen, wie es herausstellt. Dieser Artikel beschreibt den Aufzeichnungsstatus.

## <a href="" id="viewstat"></a>


Wenn Sie eine Aufzeichnung mithilfe der WPR-Benutzeroberfläche (UI) starten, werden der Aufzeichnungsstatus unmittelbar auf dem Bildschirm WPR angezeigt. Wenn Sie mithilfe der WPR-Befehlszeilenschnittstelle eine Aufzeichnung starten, können Sie den Aufzeichnungsstatus anzeigen, mithilfe einer der folgenden Methoden:

-   Geben Sie in das Eingabeaufforderungsfenster `wpr –status`. Weitere Informationen zu diesem Befehl finden Sie unter [WPR Command-Line Options](wpr-command-line-options.md#status).

-   Die Benutzeroberfläche WPR zu öffnen. Der Status der Aufzeichnung, die Sie über die Befehlszeile WPR gestartet wird angezeigt.

Weitere Informationen zur Verwendung dieser Methoden zum Starten einer Aufzeichnung WPR verwendet finden Sie unter [Starten eine Aufzeichnung](start-a-recording.md) und [WPR Command-Line Options](wpr-command-line-options.md).

**Hinweis**  
WPR kann nur eine Aufzeichnung Status anzeigen, wenn die Aufzeichnung von WPR gestartet wurde. Aufzeichnungsstatus für Aufzeichnungen nicht angezeigt, die von Xperf oder einer anderen Anwendung gestartet werden.

 

Der Aufzeichnungsstatus zeigt die folgenden Informationen:

-   **Aufzeichnung Zeit**: Dies ist die Zeitdauer, die die Aufzeichnung ausgeführt wurde.

-   **Puffer**: Dies ist die Größe des Puffers, das die Aufzeichnung verwendet wird. Es wird in MB und Prozentsatz verfügbarer Arbeitsspeicher im Pool angezeigt.

-   **Ereignisse verworfen**: die Anzahl der verloren gegangene Ereignisse seit dem Start der aufzeichnungs. Weitere Informationen zu diesem Problem finden Sie unter [Verloren Ereignissen zu vermeiden](avoid-lost-events.md).

## <a name="related-topics"></a>Verwandte Themen


[Sitzungen](sessions.md)

 

 







