---
author: Justinha
ms.assetid: 0fbb2a9b-d3ce-4d7f-b68a-af641ceec96d
MSHAttr: PreferredLib:/library/windows/hardware
title: 'WIM im Vergleich zu VHD im Vergleich zu FFU: Bilddateiformate vergleichen'
ms.openlocfilehash: 6c3135aa2366fe3bf51f03837d8c432a1e0ca32e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wim-vs-vhd-vs-ffu-comparing-image-file-formats"></a>WIM im Vergleich zu VHD im Vergleich zu FFU: Bilddateiformate vergleichen


Vergleichen. WIM. VIRTUELLE FESTPLATTE /. VHDX, und. FFU: Diese Dateiformate alle dienen zum Bereitstellen von Windows für neue Geräte. Nachfolgend finden sie zum Vergleich:

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">Windows-Abbild (. WIM)</td>
<td align="left">Virtuelle Festplatte (. VHD/VHDX)</td>
<td align="left">Vollständige Flash Update (. FFU)</td>
</tr>
<tr class="even">
<td align="left">Häufige Verwendungsmöglichkeiten</td>
<td align="left"><p>Am schnellsten zum Testen und Windows-Abbilder ändern.</p>
<p>Schnelles Bereitstellen, und Ändern von Bildern.</p></td>
<td align="left"><p>Am einfachsten für die Bereitstellung von Windows in virtueller PCs.</p>
<p>Sie können ein neues Gerät direkt aus einer einzelnen Datei VHD/VHDX starten.</p></td>
<td align="left"><p>Am schnellsten zum Erfassen und Bereitstellen von Windows in einer Fabrik.</p>
<p>Integrierten Sicherheit, um zu überprüfen, signierten Bilder enthält.</p></td>
</tr>
<tr class="odd">
<td align="left">Imaging-Formatvorlage</td>
<td align="left">Dateibasierten</td>
<td align="left">Sektor-basierte</td>
<td align="left">Sektor-basierte</td>
</tr>
<tr class="even">
<td align="left">Komprimierung</td>
<td align="left">Unterstützt mehrere Typen von Komprimierung</td>
<td align="left">Keine</td>
<td align="left">Keine</td>
</tr>
<tr class="odd">
<td align="left">Was erfasst es?</td>
<td align="left"><p>Eine Reihe von Dateien, bis zu einer gesamten Partition.</p></td>
<td align="left"><p>Erfasst die umfassende Auswahl an Laufwerksinformationen, einschließlich Partitionen.</p></td>
<td align="left"><p>Erfasst die umfassende Auswahl an Laufwerksinformationen, einschließlich Partitionen.</p></td>
</tr>
<tr class="even">
<td align="left">Wenn das Abbild angewendet wird, was passiert?</td>
<td align="left"><p>Fügt die Dateien und Ordner auf die Partition.</p>
<p>Wenn bereits vorhanden sind Dateien und Ordner mit den gleichen Namen, sind sie ersetzt. Andernfalls werden die vorhandenen Dateien gespeichert.</p></td>
<td align="left"><p>Bereinigt das gesamte Laufwerk.</p></td>
<td align="left"><p>Bereinigt das gesamte Laufwerk.</p></td>
</tr>
<tr class="odd">
<td align="left">Kann ich auf verschiedene Größen der Festplatten bereitstellen?</td>
<td align="left"><p>Ja.</p></td>
<td align="left"><p>Ja, obwohl das neue Laufwerk die gleich oder größer als die ursprüngliche Größe sein muss.</p></td>
<td align="left"><p>Ja, obwohl das neue Laufwerk die gleich oder größer als die ursprüngliche Größe sein muss.</p></td>
</tr>
<tr class="even">
<td align="left">Kann ich die Bilder ändern?</td>
<td align="left"><p>Ja. Mit Tools wie DISM können Sie bereitstellen, ändern und das Bild entladen.</p></td>
<td align="left"><p>Ja, können Sie Bereitstellen einer virtuellen Festplatte/VHDX, als wäre es Wechselmedium, und die Dateien zu ändern.</p></td>
<td align="left"><p>Ja, obwohl es beschränkt ist Hinzufügen von Paketen.</p></td>
</tr>
<tr class="odd">
<td align="left">Sicherheit</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>Enthält eine Kopfzeile für Sicherheit und Headers zum Identifizieren einer gesicherten Bilds.</p>
<p>Enthält eine Tabelle Katalog und Hash, um eine Signatur vorab, bevor Sie es auf einem Gerät zu überprüfen.</p></td>
</tr>
</tbody>
</table>

 

Finden Sie weitere Informationen finden Sie unter **/Apply-Image** in [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


**DISM**
[Deployment Image Servicing and Management (DISM) Command-Line Options](deployment-image-servicing-and-management--dism--command-line-options.md)

**Virtuelle Festplatte/VHDX**
[Boot Festplatte (systemeigenen Start): Hinzufügen einer virtuellen Festplatte zum Startmenü](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)](deploy-windows-on-a-vhd--native-boot.md)

**FFU**
[Bereitstellen von Windows verwenden vollständige Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[FFU Bildformat](../mobile/ffu-image-format.md)

 



