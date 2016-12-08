---
author: kpacquer
Description: "Die folgenden Features können mit Geräte, auf denen im Modus Manufacturing verwendet werden."
ms.assetid: 6f675ace-3f76-4421-8109-16fdf9e469fd
MSHAttr: PreferredLib:/library/windows/hardware
title: "Optionale Features für Manufacturing-Modus"
ms.openlocfilehash: 51da87396efc2459291e971054d3b698f5416722
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="optional-features-for-manufacturing-mode"></a>Optionale Features für Manufacturing-Modus


Die folgenden Features können mit Geräte, auf denen im Modus Manufacturing verwendet werden.

**Hinweis**  Alle optionale Funktionen mit Windows 10 Mobile enthalten können, zu verwendet werden. Weitere Informationen zu den anderen optionalen Features finden Sie unter [optionale Features zum Erstellen von Bildern](https://msdn.microsoft.com/library/windows/hardware/dn756780).

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>BCDEDIT</p></td>
<td align="left"><p>Das Bild für Entwicklung hinzugefügt bcdedit.exe. Dies sollte nicht im endgültigen Bilder enthalten.</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGMODEBCD</p></td>
<td align="left"><p>Fügt den BCD-Eintrag in der vollständigen Betriebssystemabbild Manufacturing Modus aktivieren. Sie sollten diese entfernen, bevor das Gerät werksseitige verlässt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGSTARTUP</p></td>
<td align="left"><p>Das Bild Manufacturing Modus startup.bsc-Datei hinzugefügt und ist erforderlich, wenn das Feature MOBILECOREBOOTSH verwendet wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGDEVTOOLS</p></td>
<td align="left"><p>Der Modus Manufacturing Bilds, beispielsweise tlist.exe, sc.exe, shutdown.exe hinzugefügt eine Sammlung von Entwicklertools nützlich. Dies sollte nicht in das endgültige Manufacturing Modus Image aufgenommen werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGTELNETFTP</p></td>
<td align="left"><p>Das Bild Manufacturing Modus hinzugefügt Telnet und TFTP-Server. Lassen sie in das endgültige Image für die Wartung, da diese nur ausgeführt, wenn das Gerät im Modus Manufacturing ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGTSHELL</p></td>
<td align="left"><p>Das Bild Manufacturing Modus hinzugefügt TShell Funktion. Lassen sie in das endgültige Image zum Warten, da sie nur ausgeführt wird, wenn das Gerät im Modus Manufacturing ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MOBILECOREBOOTSH</p></td>
<td align="left"><p>Aktiviert den Bootsh-Dienst (Bootshscv), damit Features in startup.bsc, wie Telnet und ftp, verwendet werden können. Dies ist erforderlich, wenn die MFGTELNETFTP angegeben ist. Lassen sie im Bild zur Wartung, da sie nur ausgeführt wird, wenn das Gerät im Modus Manufacturing ist.</p></td>
</tr>
</tbody>
</table>

 

 

 





