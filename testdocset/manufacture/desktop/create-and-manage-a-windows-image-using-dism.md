---
author: Justinha
Description: Erstellen und Verwalten von einem Windows-Abbild mithilfe von DISM
ms.assetid: ef3d32c6-54f4-4347-9cbb-593c7ae7bf5e
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen und Verwalten von einem Windows-Abbild mithilfe von DISM
ms.openlocfilehash: aa064445ac66d6943ed2f19925ddc1ab618c6b0a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-and-manage-a-windows-image-using-dism"></a>Erstellen und Verwalten von einem Windows-Abbild mithilfe von DISM


Bereitstellung Bild Wartung und Verwaltung (DISM.exe) bindet ein Windows-Abbilddatei (WIM) oder die virtuelle Festplatte (VHD- oder .vhdx) für die Wartung. Sie können auch den Befehl DISM Bild Management so Listen Sie die Indexnummern Bild oder die Architektur für das Bild zu überprüfen, die Sie bereitstellen werden. Nachdem Sie das Bild aktualisieren, müssen Sie es und entweder entladen einen commit oder die Änderungen zu verwerfen.

Befehle Wartung DISM können installieren, deinstallieren, konfigurieren und Aktualisieren von Features und Paketen in offline Windows® Bilder und offline Windows Vorinstallation Environment (Windows PE) Bilder. Weitere Informationen zu gängigen DISM Szenarien finden Sie unter [Was ist DISM?](what-is-dism.md). Weitere Informationen zu DISM – Wartung Befehle finden Sie unter [Deployment Image Servicing and Management (DISM) Command-Line Options](deployment-image-servicing-and-management--dism--command-line-options.md).

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[Erfassen von Bildern mithilfe von DISM Festplatte Partitionen](capture-images-of-hard-disk-partitions-using-dism.md)</p></td>
<td align="left"><p>Verwenden Sie das Diskpart-Tool und das Tool Deployment Image Servicing and Management (DISM) zum Erfassen eines Abbilds und als WIM-Datei zu speichern.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Bereitstellen Sie und ändern Sie ein Windows-Abbild mithilfe von DISM](mount-and-modify-a-windows-image-using-dism.md)</p></td>
<td align="left"><p>Übersicht über den Inhalt einer Windows WIM-Datei in ein Verzeichnis auf das Bild service oder auf allgemeine Dateivorgänge wie hinzufügen und Löschen von Dateien führen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Anwenden von Abbildern mithilfe von DISM](apply-images-using-dism.md)</p></td>
<td align="left"><p>Verwenden Sie das Diskpart-Tool und das Tool DISM Windows-Abbilder auf einen oder mehrere Partitionen auf einem Computer für die Bereitstellung anwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Aufteilen einer Bilddatei Windows (WIM) span auf mehreren DVDs](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)</p></td>
<td align="left"><p>Teilen Sie eine große WIM-Datei in mehrere kleinere Dateien, die auf das ausgewählte Medium passen. WIM-Dateien auf die ausgewählten Medien eine Kopie als ISO-Dateien abgeleitet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Erstellen einer WIM-DATEI für mehrere Architekturtypen mithilfe von DISM](create-a-wim-for-multiple-architecture-types-using-dism.md)</p></td>
<td align="left"><p>Erstellen Sie eine einzelne WIM-Datei, die 32-Bit- und 64-Bit-Windows-Abbilder enthält.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Fügen Sie ein Volume Image an einem vorhandenen Abbild mithilfe von DISM](append-a-volume-image-to-an-existing-image-using-dism--s14.md)</p></td>
<td align="left"><p>Fügen Sie ein zweites Bild zu einer vorhandenen WIM-Datei.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Erstellen eines Datenabbilds mithilfe von DISM](create-a-data-image-using-dism.md)</p></td>
<td align="left"><p>Erstellen Sie eine WIM-Datei, die enthält nur die Dateien und Anwendungen, die Sie mithilfe einer Antwortdatei auf der Windows-Installation kopieren möchten.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

 

 






