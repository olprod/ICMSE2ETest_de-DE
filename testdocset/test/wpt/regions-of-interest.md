---
title: Interessante Bereiche
description: Interessante Bereiche
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 46062275-1d15-4361-81c6-be4a2f15938d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 907beeb68c849adeb8cae25b9c36ded4bcadbc0c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="regions-of-interest"></a>Interessante Bereiche


Bereiche von Interesse ist eine neue Funktion in WPA, mit dem die Anwendung von benutzerfreundlichen Beschriftungen auf Teile der Trace kann. Ereignisse, die das Starten und Beenden von einer bestimmten Region definieren Sie herausfinden, werden diese Etiketten angewendet. Die Regionen und die zugehörigen Ereignisse sind in einer Regionen XML-Datei enthalten. Microsoft stellt einige Dateien Regionen für die Analyse der app ein, und Sie können auch Ihre eigenen Dateien Regionen für Ihre Szenarien oder Anwendungen definieren. Diese Funktion können Sie schnell und einfach komplexe Bereiche identifizieren und erhöht die Geschwindigkeit und Effizienz von Performance-Analyse.

Als Beispiel wird davon ausgegangen Sie Szenarios, in dem mehrere Loading-Zeichenfolgen enthält jeweils durch ein Ereignis: A, gefolgt von einem anderen Ereignis, b definiert ist Regionen Interesse können Sie eine benutzerfreundliche "Loading" Beschriftung an alle diese Zeitspannen A / B anwenden. Nun, anstatt diese Ereignis Sequenzen manuell identifizieren, WPA automatisch angewendet Bezeichnungsfelds "Loading" ermöglicht es Ihnen, schnell visualisieren, in denen diese Ereignisse auftreten.

Als weiteres Beispiel muss ein Benutzer die Leistung einer bestimmten Windows Store-App zu analysieren. Anwendungslebenszyklus kann in mehreren Phasen, wie starten, anhalten/fortsetzen und Herunterfahren, von denen jedes eine entsprechende Region Definition hätte unterteilt werden. Mit dieser Region Definitionen konnte jeder Benutzer auf einfache Weise identifizieren, wo diese Lebenszyklusereignisse auftreten.

Um Bereiche von Interesse mit WPA verwenden, müssen Sie über Folgendes verfügen:

-   Eine ETW Trace (ETL)-Datei, die während der relevanten Szenario gesammelt wurden

-   Eine Definitionsdatei Regionen interessante (.xml)

## <a name="creating-a-regions-of-interest-file"></a>Erstellen einer Datei Regionen von Interesse


Informationen zum Erstellen einer Datei Regionen von Interesse finden Sie unter [Erstellen einer Regionen Zinsen Datei](creating-a-regions-of-interest-file.md)

## <a name="supporting-regex-in-a-regions-of-interest-file"></a>Unterstützung von Regex in eine Datei von Interesse Regionen


Ein Regionen Interesse Datei unterstützt reguläre Ausdrücke (Regex). Informationen zu Regex und erstellen neue Zeilen in einer Datei Regionen der Zinssatz finden Sie unter [Erstellen einer Regionen Zinsen Datei](creating-a-regions-of-interest-file.md)

## <a name="applying-a-regions-of-interest-file-to-an-open-trace"></a>Anwenden einer Datei Regionen von Interesse auf ein Trace öffnen


Eine interessante Regionen Datei können Sie zusätzliche Markup eines open Trace in WPA gilt:

-   Wählen Sie im Menü **Trace**, **Trace-Eigenschaften**.

-   Wählen Sie im Bereich **Trace Eigenschaften** **Hinzufügen**.

-   Navigieren Sie zum Auswählen der gewünschten Bereiche von Interesse-Manifestdatei (XML) und wählen Sie **Öffnen**.

-   Die Datei wird jetzt das ListBox-Steuerelement **Regionen von Interesse Definitionen** hinzugefügt. Wechseln Sie zu dem Bereich **Analysis** durch Auswahl der Registerkarte **Analyse** im oberen Bereich des Fensters.

-   Erweitern Sie im **Diagramm Explorer** **Systemaktivitäten** .

-   Wenn Ihre Trace Regionen, die durch die Manifestdatei definiert wurden enthält, wird das Diagramm **Regionen von Interesse** als im letzten Diagramm unter **Systemaktivitäten** (unmittelbar vor der **Berechnung** Kategorie) im **Graph-Explorer** angezeigt. Ziehen Sie im Diagramm auf die **Analysis** -Bereich.

    Wenn Trace keinen Bereiche von Interesse ist, wird ein Diagramm **Regions interessante** nicht angezeigt.

**Hinweis**  
Regionen mit Interesse Definitionen zur CPU-Auslastung an verschiedene Aktivitäten-Attribut nutzt die CPU-Auslastung Ergebnisarray als Attribut zugewiesen-Tabelle. Wenn Sie mehrere Regionen Dateien verwenden, können unterschiedliche Regionen von Interesse überlappen und in Konflikt stehen. Wenn diese Konflikte auftreten, kann WPA nicht genau eine einzelne Aktivität an einen bestimmten Thread in einem bestimmten Zeitraum Attribut.

Um diese mögliche Konflikte zu vermeiden, verwenden Sie nur eine Region-Definitionsdatei zu einem Zeitpunkt.

 

## <a name="related-topics"></a>Verwandte Themen


[Erstellen einer Bereiche der Zinsen-Datei](creating-a-regions-of-interest-file.md)

[WPA-Features](wpa-features.md)

 

 







