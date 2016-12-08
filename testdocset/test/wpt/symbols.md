---
title: Symbole
description: Symbole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7d34c86b-3b0c-40b1-a71d-b23978f97edf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b196f9f5790621af998ae6e7d36bab50345bef9a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="symbols"></a>Symbole


Aktiviert und Symbol Decodierung Unterstützung konfiguriert.

``` syntax
xperf -i <trace file>… [-o output] -symbols [cacheonly] [verbose] [dbghelplog]
```

## <a name="parameters"></a>Parameter


<a href="" id="cacheonly"></a>*CacheOnly*  
Verwenden Sie SymCache, aber nicht DbgHelp. Diese Option wird das Symbol für ablaufverfolgungen mit viele binary Bilder, dass Ungenügende Symboldateien erst, nachdem alle interessante Symboldateien transcodiert wurden Decodierung beschleunigt.

<a href="" id="verbose"></a>*"ausführlich"*  
Ausführlichen Modus. Druckt symbol für Pfade und Versionsinformationen. Weitere Informationen finden Sie unter [Symbole laden](loading-symbols.md).

<a href="" id="dbghelplog"></a>*dbghelplog*  
Debug-Protokoll zu **Stderr**DbgHelp zu aktivieren.

Symbol Decodierung Support verwendet die Umgebungsvariablen in der folgenden Tabelle für eine zusätzliche Konfiguration von DbgHelp und SymCache.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>_NT_SYMBOL_PATH</p></td>
<td><p>Gibt der Pfad DbgHelp bei der Suche suchen Dateien (mit der Erweiterung der PDB) Symbole in der Verfolgung verwendet, die binäre Abbilder Dateien entsprechen. Finden Sie unten im Hinweis bezüglich diese Variable ein.</p></td>
</tr>
<tr class="even">
<td><p>_NT_SYMCACHE_PATH</p></td>
<td><p>Gibt den Pfad in das lokale Verzeichnis SymCache. Standardmäßig wird \SymCache verwendet.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Für die Decodierung von Symbol Trace muss ein Kernel Trace (oder ein Benutzer Trace in Verbindung mit einer Ablaufverfolgung für Kernel verarbeitet), auf dem die PROC\_THREAD + LADEPROGRAMM Kernel Flags aktiviert und, beendet und mit zusammengeführt wurde `-d` oder mit `-merge` auf dem Computer, auf dem sie ausgeführt wurde. Xperf führt eine spezielle Kennung Abbilds während seiner benutzerdefinierte Trace zusammenführen, mit dem Symbol Decodierung kann.

 

## <a name="remarks"></a>Hinweise


Wenn diese Aktion nicht in der Befehlszeile angegeben wird, ist das Symbol Decodierung deaktiviert.

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

[Laden von Symbolen](loading-symbols.md)

[Häufige Probleme von eingehenderen Analysen](../assessments/common-in-depth-analysis-issues.md)

 

 







