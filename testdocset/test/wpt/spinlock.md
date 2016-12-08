---
title: SpinLock
description: SpinLock
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5ca2ee5f-ad3f-42ec-91e4-a044ce982650
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9813421e0d18947e83b791d952b99b655dd38726
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="spinlock"></a>SpinLock


Diese Aktion wird eine Textdatei mit Informationen im Zusammenhang mit Spinlock Aktivität erzeugt.

``` syntax
-a spinlock [-summary] [-counts [n]]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-Zusammenfassung**  
Enthält eine Zusammenfassung Spinlock Ereignisinformationen in einem Format Tabstopp-getrennt.

<a href="" id="-count-n-"></a>**-Count***\[n\]*  
Maximale Anzahl von Dateien angezeigt.

## <a name="remarks"></a>Hinweise


Xperf Spinlock Analyse ist für 64-Bit-Architekturen verfügbar. SpinLock Instrumentation wird beginnend mit Windows 7, Windows Server 2008 R2 und neuere Versionen des Betriebssystems unterstützt. Xperf unterstützt normalen Drehfeld sperren und Drehfeld Sperren in der Warteschlange. Weitere Informationen zu Drehfeld Sperren finden Sie unter [Drehfeld Sperren](http://go.microsoft.com/fwlink/p/?linkid=213937). Um Aufwand zu verringern, ist ETW Spinlock Instrumentation Sample-basiert. Die Sampling-Häufigkeit kann mit optimiert werden `-setspinlocksample`. Weitere Informationen zum Starten von Spinlock Sampling finden Sie unter [Starten](start.md).

Gute Kenntnisse im Umgang mit WPA Symbole wird empfohlen, um sinnvolle Analyse durchzuführen. Informationen zu Symbole finden Sie unter [Symbol Unterstützung](symbol-support.md).

Wenn Ihr Testszenario bereits ausgeführt wird, ist es nicht erforderlich, das Szenario zum Sammeln von Ereignissen Spinlock zu beenden. Sie können Spinlock Ereignissammlung starten, während Sie der Code von Interesse ist aktiv ausgeführt wird. Noch ist es erforderlich, Ihr Szenario aussetzen, wenn Spinlock Ereignisdaten gesammelt wurden.

**Hinweis**  
Große Anzahl von Spinlock Ereignisse möglicherweise die Trace-Puffer überladen und verursachen Ereignisse verloren. Beim Zusammenführen von, und laden die Ablaufverfolgung in diesem Fall wird eine Meldung angezeigt. Weitere Informationen zum Ereignis Datenverlust zu vermeiden finden Sie unter [Verloren Ereignissen zu vermeiden](avoid-lost-events.md).

Weitere Informationen zur Aktivität **Spinlock** finden Sie unter [Anpassen von Spinlock-Parameters](customizing-spinlock-parameters.md).

 

## <a name="example"></a>Beispiel


Das folgende Befehlsbeispiel veranschaulicht eine Verfolgung mit Spinlock Daten zu starten.

``` syntax
xperf -on PROC_THREAD+LOADER+SPINLOCK
```

SpinLock Ereignisdaten können auch gesammelt werden nur die Option "SPINLOCK" verwenden, das wie in das folgende Befehlsbeispiel dargestellt ist.

``` syntax
xperf -on SPINLOCK
```

Jedoch, wenn die "PROC\_THREAD + LADEPROGRAMM" Optionen nicht angegeben werden, Symbolinformationen sind nicht verfügbar für die Decodierung. Weitere Informationen zu Symbolen finden Sie unter [Unterstützung Symbol](symbol-support.md).

Nachdem Daten in einer ETL-Datei erfasst wurden, Verarbeiten der ETL-Datei das folgende Befehlsbeispiel Siehe

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock
```

Dies führt zu einen Spinlock Bericht. Informationen zu diesem Bericht finden Sie unter [Auswerten Spinlock Daten](evaluating-spinlock-data.md).

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







