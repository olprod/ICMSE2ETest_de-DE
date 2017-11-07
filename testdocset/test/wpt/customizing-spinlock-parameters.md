---
title: Anpassen von Spinlock Parameter
description: Anpassen von Spinlock-Parameter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16e6e317-659b-4797-a447-db4dcdb3c9c0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5173d4a941737a54f5b16d633f8b9f61dc775c8b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customizing-spinlock-parameters"></a>Anpassen von Spinlock Parameter


Standardmäßig protokolliert das System eine Spinlock-Ereignis für jedes 1000 nicht Konflikten Übernahmen und eine Spinlock-Ereignis für jedes Konflikten Erwerb. Datensammlung SpinLock unterstützt drei Parameter, die Sie die Datensammlung anpassen können. Spinlock-Auflistung Parameter festlegen möchten, verwenden Sie den folgenden Befehl aus.

``` syntax
xperf -setspinlocksample [spin_threshold] [acquire_sample_rate] [contention_sample_rate]
```

## <a name="parameters"></a>Parameter


<a href="" id="spin-threshold"></a>*Drehfeld\_Schwellenwert*  
Die Instrumentation Spinlock stellt eine Möglichkeit zum Verfolgen stark Sperren Konflikten bereit. Dies wird durch Festlegen eines hohen Drehfeld Schwellenwerts erreicht. Wenn eine Sperre weniger als dieser Schwellenwert dreht, wird kein Ereignis Spinlock angemeldet sein. Wenn dieser Wert 1 ist, wird beispielsweise ein Spinlock-Ereignis für jeden Versuch, eine Sperre zu erwerben erworben. Wenn dieser Wert 10 ist, wird ein Spinlock-Ereignis für jeden zehn versucht, eine Sperre zu erwerben protokolliert. Der Standardwert ist 1.

<a href="" id="acquire-sample-rate"></a>*erwerben\_Beispiel\_Rate*  
Samplingrate an welche Spinlock Ereignisse während einer Trace protokolliert werden. Wenn dieser Wert 1000 ist, wird beispielsweise eine Spinlock-Ereignis für jeden 1000 nicht Ereignis Übernahmen protokolliert. Der Standardwert ist 1000.

<a href="" id="contention-sample-rate"></a>*Konflikte\_Beispiel\_Rate*  
Rate, an welche Spinlock Ereignisse protokolliert werden, wenn Konflikte auftreten. Dieser Wert 100 ist, wird angenommen, ein Spinlock-Ereignis für jeden 100 Spinlock Kollisionen protokolliert. Der Standardwert ist 1.

## <a name="remarks"></a>Hinweise


SpinLock-Auflistung Parameter zurück auf die Standardwerte beim Neustart des Systems. Gültige Datensammlung sicherzustellen, immer Abfragen oder Spinlock Parameter vor dem Start Ereignis Datensammlung festzulegen.

## <a name="example"></a>Beispiel


Im folgenden Beispiel wird veranschaulicht, wie die aktuellen Werte abgefragt.

``` syntax
xperf -spinlock
```

Im folgenden Beispiel wird den Schwellenwert Drehfeld auf 1 fest, die Samplingrate einlesen bis 1000 und die Spinlock Konflikte Abtastrate und 100.

``` syntax
xperf -setspinlocksample 1 1000 100
```

Diese Abfrage gibt das folgende Ergebnis für die Werte aus dem vorherigen Beispiel festgelegt.

``` syntax
Current Spinlock Spin Threshold = 1
Current Spinlock Acquire Sample Rate = 1000
Current Spinlock Contention Sample Rate = 100
```

## <a name="related-topics"></a>Verwandte Themen


[SpinLock](spinlock.md)

 

 







