---
author: Justinha
Description: DrvLoad Befehlszeilenoptionen
ms.assetid: d4e6f566-2763-4774-876e-24357f223a52
MSHAttr: PreferredLib:/library/windows/hardware
title: DrvLoad Befehlszeilenoptionen
ms.openlocfilehash: 32563a0b5adb184293b81dda0c4b8d87e3f0a029
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="drvload-command-line-options"></a>DrvLoad Befehlszeilenoptionen


Das Tool Drvload hinzugefügt einen gestarteten Windows Vorinstallation Environment (Windows PE) Abbild Out-of-Box-Treiber. Es hat eine oder mehrere Treiber INF-Dateien als Eingabe. Verwenden Sie das Tool Abbildern Bereitstellung und Verwaltung (DISM), um einen Treiber ein offline Windows PE-Abbild hinzuzufügen. Weitere Informationen finden Sie unter [Hinzufügen und entfernen Treiber eine Offline-Windows-Abbild](add-and-remove-drivers-to-an-offline-windows-image.md).

Wenn die INF-Datei ein Neustart erforderlich ist, wird Windows PE die Anforderung ignoriert. Wenn die Treiber sys-Datei ein Neustart erforderlich ist, kann der Treiber mit Drvload hinzugefügt werden. Weitere Informationen finden Sie unter [Gerätetreibern und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md) und [DISM Befehlszeilenoptionen zum Warten](dism-driver-servicing-command-line-options-s14.md).

Als bevorzugter Treiber für dieses Gerät sind Treiber hinzugefügt werden mit dem Tool Drvload gekennzeichnet. Wenn Sie während der Installation von Windows einen aktualisierten Treiber hinzufügen, hat der, den Sie mit Drvload hinzugefügt Treiber Vorrang.

## <a name="span-iddrvloadcommand-lineoptionsspanspan-iddrvloadcommand-lineoptionsspanspan-iddrvloadcommand-lineoptionsspandrvload-command-line-options"></a><span id="Drvload_Command-Line_Options"></span><span id="drvload_command-line_options"></span><span id="DRVLOAD_COMMAND-LINE_OPTIONS"></span>DrvLoad Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen stehen für Drvload zur Verfügung.

**Drvload** *inf\_Pfad* \[,*inf\_path* \[... \]\] \[**/?**\]

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/?</strong></p></td>
<td align="left"><p>Zeigt Informationen zur Verwendung.</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>inf_path</em></p></td>
<td align="left"><p>Gibt den Pfad zu der INF-Datei. Der Pfad kann Umgebungsvariablen enthalten.</p></td>
</tr>
</tbody>
</table>

 

Wenn keine Treiber installiert wurden, gibt Drvload Status ungleich Null (% ERRORLEVEL%) zurück.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

 

 






