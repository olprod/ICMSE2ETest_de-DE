---
title: Integrierte Xperf Profile
description: Integrierte Xperf Profile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5628e0c0-5882-4b83-b8c1-058e5a125c68
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 833421904f3db858bee5e925aea0660f6cf2f1eb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-built-in-profiles"></a>Integrierte Xperf Profile


Um die integrierten Xperf Profile anzuzeigen, führen Sie den folgenden Befehl aus.

``` syntax
xperf -profiles
```

Die folgende Tabelle beschreibt die verfügbaren Profile.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Profil</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Korrektur! FileIOProfiles.InSequentialFile</p></td>
<td><p>E/a Tracing Profil in eine sequenzielle Datei.</p></td>
</tr>
<tr class="even">
<td><p>Korrektur! FileIOProfiles.InBuffer</p></td>
<td><p>Datei e/a Tracing Profil in einem Puffer an.</p></td>
</tr>
<tr class="odd">
<td><p>Korrektur! GeneralProfiles.InSequentialFile</p></td>
<td><p>Gemeinsames System Metriken Tracing Profil in eine sequenzielle Datei.</p></td>
</tr>
<tr class="even">
<td><p>Korrektur! GeneralProfiles.InBuffer</p></td>
<td><p>Gemeinsames System Metriken Tracing Profil in einem Puffer.</p></td>
</tr>
<tr class="odd">
<td><p>Korrektur! PerfCoreProfiles.InSequentialFile</p></td>
<td><p>Grundlegende systemkennzahlen tracing Profil (mit alle integrierten Profile enthalten) in eine sequenzielle Datei.</p></td>
</tr>
<tr class="even">
<td><p>Korrektur! PerfCoreProfiles.InBuffer</p></td>
<td><p>Grundlegende systemkennzahlen tracing Profil (im Lieferumfang alle integrierten Profile) in einem Puffer.</p></td>
</tr>
<tr class="odd">
<td><p>Korrektur! RegistryProfiles.InSequentialFile</p></td>
<td><p>Registrierung Tracing Profil in eine sequenzielle Datei.</p></td>
</tr>
<tr class="even">
<td><p>Korrektur! RegistryProfiles.InBuffer</p></td>
<td><p>Registrierung Tracing Profil in einem Puffer.</p></td>
</tr>
<tr class="odd">
<td><p>Korrektur! StdProfile</p></td>
<td><p>Allgemeine Definitionen in integrierten Profile (nicht wiederherzustellenden) verwendet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="examples"></a>Beispiele


In den folgenden Beispielen mehrere ETW-Sitzungen zu aktivieren und diese in einer einzigen Protokolldatei zusammenführen, je nach Bedarf.

**Arbeitsspeicher basierten Trace-Profil**

Für eine in-Memory wiederholt Momentaufnahmen Trace Profil, führen Sie den folgenden Befehl aus.

``` syntax
xperf -start perf!GeneralProfiles.InBuffer
```

Führen Sie einige Szenario, und führen Sie dann den folgenden Befehl aus.

``` syntax
xperf -save perf!GeneralProfiles.InBuffer snapshot1.etl
```

Sie können optional mit dem Speichern der zusätzlichen Snapshots fortfahren, und halten Sie dann die Trace erfassen mithilfe des folgenden Befehls.

``` syntax
xperf -cancel perf!GeneralProfiles.InBuffer
```

**Dateibasierten Trace-Profil**

Führen Sie folgenden Befehl aus, um ein Profil dateibasierten Trace zu starten.

``` syntax
xperf -start perf!RegistryProfiles.InSequentialFile
```

Führen Sie einige Szenario, und führen Sie dann den folgenden Befehl zum Beenden Trace erfassen.

``` syntax
xperf -stop perf!RegistryProfiles.InSequentialFile trace.etl
```

**Erweitern der Benutzerprofildienst-Definitionen**

Profildefinitionen erweitert werden können und über die Befehlszeile besteht. Geben Sie beispielsweise Folgendes ein, um die Korrektur ** **ReadyThread** Stapel hinzugefügt. FileIOProfiles.InSequentialFile** führen Sie den folgenden Befehl ein.

``` syntax
xperf -start perf!FileIOProfiles.InSequentialFile -stackwalk ReadyThread
```

## <a name="related-topics"></a>Verwandte Themen


[Xperf Profile](xperf-profiles.md)

 

 







