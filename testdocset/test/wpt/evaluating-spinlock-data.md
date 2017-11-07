---
title: Evaluierung Spinlock Daten
description: Evaluierung Spinlock Daten
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9e5e4ffa-5fb7-401e-bfc3-760cbb7955d9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a4e1663b0a13d76a35d0657fdb5b29011b687909
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="evaluating-spinlock-data"></a>Evaluierung Spinlock Daten


Der Bericht Spinlock stellt die folgende Informationen zu übernommene:

-   Samplingrate zu erwerben.

-   Samplingrate Konflikt.

-   Drehfeld-Schwellenwert.

-   Anzahl der CPUs.

-   CPU-Geschwindigkeit in MHz.

-   Verfolgen Sie Länge in Nanosekunden.

-   Länge in Zyklen zu verfolgen.

In den nächsten Abschnitten des Berichts-Auslastung der Spinlock während das Profil Zeitraum an. Jede Sperre Drehfeld ist separat dargestellt. Drehfeld Sperren werden mit der "neuesten" Drehfeld Sperren zuerst angezeigt sortiert. Häufig ist es möglich, den Spinlock Engpass Identifizieren der oberen wenige Drehfeld Sperren verfolgen.

Die folgende Informationen werden für jede Sperre Drehfeld dargestellt:

-   Typ der Sperrung.

-   Kerneladresse des sperren.

-   Symbol für die Sperre. Übernommene dynamisch erstellt haben keine Symbole.

Ein Zusammenfassungsbericht folgt mit den Informationen gehen Sie folgendermaßen vor:

-   Der Prozentsatz der CPU-Zeit für auf Sperre.

-   Prozentsatz der CPU-Zeit für auf Sperrenkonflikte.

-   Anforderungsrate.

-   Konflikt Rate.

-   Drehfeld Rate.

-   Konfliktrate, beide aufgenommen und normalisiert.

Die letzten zwei Abschnitte des Berichts werden die Ereignisse, die aufgrund von Interrupts und die Version-Funktion übersprungen.

Interrupts können auftreten, während Drehfeld sperren. In diesem Fall der Interrupt Bearbeitungszeit befindet sich auf den Spinlock Zeit und die Spinlock Zeit angezeigt übermäßig lange. Xperf enthält keinen Spinlock Ereignisse, die gehalten werden, während ein Interrupt behandelt wird, bei der Berechnung Spinlock Zeiten aufbewahren. Die Zeile "-Ereignis übersprungen aufgrund von Interrupts" zeigt die Anzahl der Ereignisse, die in der Berechnung nicht enthalten waren. Diese Nummer wird normalerweise sehr klein.

Eine Sperre Drehfeld kann erworben oder aus anderen Codepfaden freigegeben werden. Eine Liste der Freigabefunktionen der Sperre Drehfeld wird am Ende des Berichts angezeigt. Die Liste ist nach Spinlock Zeit sortiert. Weitere Informationen zu einer bestimmten Freigabefunktion wie Erwerb oder Konflikte wird auch angezeigt.

## <a name="example"></a>Beispiel


Im folgenden Beispiel wird gezeigt, wie eine Zusammenfassung der Spinlock Daten abgerufen.

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock -summary
```

Im folgenden Beispiel wird veranschaulicht, wie zur Begrenzung der Anzahl der zurückgegebenen Datensätze auf die fünf aktivsten Drehfeld sperren.

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock -summary -counts 5
```

## <a name="related-topics"></a>Verwandte Themen


[SpinLock](spinlock.md)

 

 







