---
title: WPA-Abfragesyntax
description: WPA-Abfragesyntax
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b62dfcb3-1900-438f-84ac-9e6113de67bb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ac56b3c766489016e37bb0aa6336f212609b60a7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpa-query-syntax"></a>WPA-Abfragesyntax


Die Syntax der Suche und Filtern von Komponenten der Windows Performance Analyzer (WPA) sind eine Erweiterung für Windows-Abfragesyntax. Weitere Informationen finden Sie unter [Erweiterte-Abfragesyntax](http://go.microsoft.com/fwlink/p/?linkid=229849).

## <a name="available-extensions"></a>Verfügbare Erweiterungen


Die folgende Tabelle beschreibt die verfügbaren Erweiterungen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Beispiele</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Eigenschaftennamen können Leerzeichen und andere nicht alphanumerische Zeichen enthalten, wenn die Leerzeichen oder Buchstaben in Klammern eingeschlossen sind.</p></td>
<td><p><code>[All Count]:&gt;0</code></p>
<p><code>[% Weight]:= 5.6</code></p></td>
</tr>
<tr class="even">
<td><p>Das Sternchen <strong>RegEx</strong> -Operator (*) ist für die Zeichenfolgentypen zulässig.</p></td>
<td><p>Die folgende Abfrage stimmt mit sowohl <em>Iexplore</em> und <em>Explorer</em>, aber nicht <em>Myexplorer</em>:</p>
<p><code>ProcessName:* '.?explore.*'</code></p></td>
</tr>
<tr class="odd">
<td><p>Arbeitsspeicher Größe-Suffixe (KB, MB, GB) und Zeiteinheiten (s, ms, USA, ns) Double und Ganzzahl Literale unterstützt werden. Diese Suffixe Groß-/Kleinschreibung nicht beachtet.</p></td>
<td><p><code>Size :&gt; 20MB AND Size :&lt; 0.5GB</code></p>
<p><code>Duration :&gt; 5ms OR Duration :&lt; 1us</code></p></td>
</tr>
<tr class="even">
<td><p>Flexible Genauigkeit auf Float Literale für Gleichheit Vorgänge wird unterstützt. Precision basiert auf der Anzahl von Dezimalstellen, der die Abfrage enthält.</p></td>
<td><p><code>Duration := 4.5ms</code> können potenziell ein Ergebnis größer als <code>Duration :=4.50ms</code>.</p></td>
</tr>
</tbody>
</table>

 

Sie möchten einen Suchbereich auf eine Teilmenge von Zeilen nach Datenreihennamen einschränkt. Der Name der Datenreihe ist der Name der Spalte nicht leeren ganz rechts auf der linken Seite des Balkens gold. *In der folgenden Tabelle versteht der Datenreihennamen für Zeilen 1 bis 6.* Für alle anderen Zeilen ist der Name der Datenreihe *Modul*.

![WPA-Suche](images/wpasearch.jpg)

Bei einer Abfrage für `Process:~='iexplore'`, 6 bis 13 Zeilen ausgewählt sind.

Bei einer Abfrage für `Process:~='iexplore' AND [Series Name] := 'Process'`, nur in Zeile 6 ausgewählt ist.

Bei einer Abfrage für `Process:~'iexplore' AND [Series Name] := 'Module'`, Zeilen 7 bis 13 ausgewählt sind.

## <a name="related-topics"></a>Verwandte Themen


[WPA-Features](wpa-features.md)

 

 







