---
author: Justinha
Description: "DISM unterstützte Plattformen"
ms.assetid: c52337e1-19a0-46d9-aa17-c5b704ea1949
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM unterstützte Plattformen"
ms.openlocfilehash: bdaa8da3b21d6da869b374fc0b35258194fe65aa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-supported-platforms"></a>DISM unterstützte Plattformen


Die Windows-10-Version von Abbildern Bereitstellung und Verwaltung (DISM) steht in Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), Windows Server 2016 – Technische Vorschau und Windows-Vorinstallation Environment (Windows PE) für Windows 10.

Um Windows 10 Bilder zu warten, benötigen Sie die Windows-10-Version von DISM, andernfalls, die das Bild beschädigt werden kann.

Um die Windows-10-Version von DISM auf einer früheren Version von Windows verwenden, installieren Sie das Windows Assessment and Deployment Kit (ADK) [von dieser Website](http://go.microsoft.com/fwlink/p/?LinkId=526803), und installieren Sie die **Bereitstellungstools**. Starten Sie dann die **Bereitstellung und Imaging Tools Umgebung** zum DISM-Befehle ausführen.

Um den Windows-10-Version von DISM mit einer früheren Version von Windows PE verwenden, finden Sie unter [Windows 10 installieren eine vorherige Version von Windows PE verwenden](copy-dism-to-another-computer.md).

Beachten Sie, dass neuere DISM Features immer funktionieren nicht, wenn Bilder von früheren Versionen von Windows – Wartung. Finden Sie weitere Informationen finden Sie [DISM Verweis](dism-reference--deployment-image-servicing-and-management.md)aus.

## <a name="span-iddtspdismspanspan-iddtspdismspansupported-platforms"></a><span id="DTSP_DISM"></span><span id="dtsp_dism"></span>Unterstützte Plattformen


Der Host-bereitstellungsumgebung ist das Betriebssystem dem DISM ausgeführt wird. Das Zielbild ist das Bild, das Wartungsarbeiten durchgeführt werden.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Host-bereitstellungsumgebung</th>
<th align="left">Bild: Windows 10, 10 Windows oder Windows PE als Ziel für Windows 10</th>
<th align="left">Zielbild:, Windows 8.1, Windows Server 2016 – Technische Vorschau anzuzeigen, Windows Server 2012 R2 oder Windows PE 5.0 (X86 oder X64)</th>
<th align="left">Zielbild: Windows 8, WindowsServer 2012 oder Windows PE 4.0 (X86 oder X64)</th>
<th align="left">Zielbild: Windows 7, Windows Server 2008 R2 oder Windows PE 3.0 (X86 oder X64)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows-10 (X86 oder X64)</p></td>
<td align="left">Unterstützt</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2016 – Technische Vorschau (X86 oder X64)</p></td>
<td align="left">Unterstützt</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8.1 (X86 oder X64)</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012 R2 (x 86 oder X64)</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8 (X86 oder X64)</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td align="left"><p>WindowsServer 2012 (X86 oder X64)</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7 (X86 oder X64)</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt, mit der Windows 8-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2008 R2 (x 86 oder X64)</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt, mit der Windows 8-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows Server 2008 SP2 (x 86 oder X64)</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt mit der Windows 8-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PE für Windows 10 X86</p></td>
<td align="left">Unterstützt</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PE für Windows 10 X64</p></td>
<td align="left">Unterstützt: X64 Ziel nur Symbol</td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PE 5.0 x86</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PE 5.0 x64</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM: X64 Ziel nur Symbol</td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PE 4.0 x86</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PE 4.0 x64</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM: X64 Ziel nur Symbol</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: Adressieren X64 nur Bild</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PE 3.0 x86</p></td>
<td align="left">Unterstützt, mithilfe der Windows-10-Version von DISM</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt, mit der Windows 8-Version von DISM oder höher</p></td>
<td align="left"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PE 3.0 x64</p></td>
<td align="left">Unterstützt, mit der Windows-10-Version von DISM: X64 Ziel nur Symbol</td>
<td align="left"><p>Unterstützt, mit der Windows 8.1-Version von DISM oder höher: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt, mit der Windows 8-Version von DISM oder höher: X64 Ziel nur Symbol</p></td>
<td align="left"><p>Unterstützt: X64 Ziel nur Symbol</p></td>
</tr>
</tbody>
</table>

 

Ausfallsichere File System (REFS) wird nicht unterstützt.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Installieren von Windows 10 Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803)

[DISM Verweis (Deployment Image Servicing and Management)](dism-reference--deployment-image-servicing-and-management.md)

[Installieren von Windows 10 mit einer früheren Version von Windows PE](copy-dism-to-another-computer.md)

 

 






