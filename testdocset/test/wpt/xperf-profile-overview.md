---
title: "Übersicht über die Xperf Profil"
description: "Übersicht über die Xperf Profil"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2de4bf4a-eb88-4dd9-a91d-2b049ce9cd49
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e25ef2c0445cfa51ea15a69ac95810c1070c143
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-profile-overview"></a>Übersicht über die Xperf Profil


Ein Profil Trace ist eine Auflistung von Einstellungen für einen bestimmten Objekttyp Trace. Diese Profile sind nicht kompatibel mit Windows Performance Recorder-(WPR) aufzeichnen. Sie können erfassen und diese Einstellungen mit einem einzigen Befehl pro Vorgang steuern. Die meisten Profile sind eine der beiden folgenden Typen: Speicher- oder dateibasierten. Wählen Sie das Profil, das den Mechanismus entspricht, die Sie für die Protokollierung verwenden: Schreiben auf einen Puffer im Arbeitsspeicher oder Schreiben in eine Datei.

In der folgenden Tabelle wird beschrieben, die Typen von Sitzungen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Sitzungstyp</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>InSequentialFile Sitzungen</p></td>
<td><p>Diese Sitzungen werden sequenziell, in einer Datei gespeichert, bis eine voreingestellte maximale Dateigröße erreicht wurde erweitert. Dieses Verhalten ordnet den sequenziellen ETW-Modus.</p></td>
</tr>
<tr class="even">
<td><p>"InBuffer" Sitzungen</p></td>
<td><p>Diese Sitzungen speichern Daten im Speicher, und die ältesten Daten mit den neuesten Daten überschreiben, wenn der Puffer voll ist. Snapshot-Datei für die Analyse müssen diese Sitzungen gespeichert werden. Dieses Verhalten ordnet den Pufferung ETW-Modus.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Die Dateimodi können nicht kombiniert werden.

 

## <a name="related-topics"></a>Verwandte Themen


[Xperf Profile](xperf-profiles.md)

[Sitzungen](sessions.md)

[Anbieter](providers.md)

 

 







