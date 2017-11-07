---
author: Justinha
Description: Bootsect Befehlszeilenoptionen
ms.assetid: 2021a0b5-955a-4193-a6e2-9864c047d82d
MSHAttr: PreferredLib:/library/windows/hardware
title: Bootsect Befehlszeilenoptionen
ms.openlocfilehash: a1c41bb9b45853d5ab110959d9355a30e083205b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootsect-command-line-options"></a>Bootsect Befehlszeilenoptionen


Bootsect.exe aktualisiert den master Boot-Code für Festplattenpartitionen zum Wechseln zwischen Bootmgr und NT Loader (**NTLDR**). Mit diesem Tool können Sie den Boot-Sektor auf Ihrem Computer wiederherstellen. Dieses Tool ersetzt **FixFAT** und **FixNTFS**.

## <a name="span-idbootsectcommandsspanspan-idbootsectcommandsspanspan-idbootsectcommandsspanbootsect-commands"></a><span id="Bootsect_Commands"></span><span id="bootsect_commands"></span><span id="BOOTSECT_COMMANDS"></span>Bootsect-Befehle


Bootsect werden die folgenden Befehlszeilenoptionen verwendet:

**Bootsect {/ help | / nt52 | / NT60} {SYS | ALLE | &lt;DriveLetter:&gt;} \[/force\] /MBR**

Beispiel für master Bootcode anwenden, die mit NTLDR auf den Datenträger mit der Bezeichnung kompatibel ist E, verwenden Sie den folgenden Befehl ein:

**Bootsect/nt52 E:**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Befehlszeilenoptionen</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Help</strong></p></td>
<td align="left"><p>Diese Anweisungen: Einsatz angezeigt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ nt52</strong></p></td>
<td align="left"><p>Wendet den master Bootcode, der mit NTLDR <strong>SYS</strong>, <strong>ALLE</strong>, kompatibel ist oder &lt;DriveLetter&gt;. Das Betriebssystem auf <strong>SYS</strong>; <strong>ALLE</strong>, installiert oder &lt;DriveLetter&gt; muss älter als Windows Vista.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ NT60</strong></p></td>
<td align="left"><p>Wendet den master Bootcode, der auf <strong>SYS</strong>; <strong>ALLE</strong>, sodass er mit kompatibel ist oder &lt;DriveLetter&gt;. Das Betriebssystem auf <strong>SYS</strong>; <strong>ALLE</strong>, installiert oder &lt;DriveLetter&gt; muss Windows 8, Windows® 7, Windows Vista, Windows Server® 2012, Windows Server 2008 R2 oder Windows Server 2008.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SYS</strong></p></td>
<td align="left"><p>Aktualisiert den master Bootcode auf der Systempartition, die zum Starten des Windows verwendet wird.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ALL</strong></p></td>
<td align="left"><p>Aktualisiert den master Bootcode auf alle Partitionen. Die Option <strong>ALLE</strong> aktualisiert nicht notwendigerweise den Boot-Code für jedes Volume. Diese Option aktualisiert stattdessen den Boot-Code auf Volumes, die verwendet werden können, als Windows-Startvolumes, der keine dynamischen Datenträger ausschließt, die nicht mit einer zugrunde liegenden Festplattenpartition verbunden sind. Diese Einschränkung ist vorhanden, da Bootcode am Anfang des einer Festplattenpartition gefunden werden muss.</p></td>
</tr>
<tr class="even">
<td align="left"><p>&lt;DriveLetter&gt;</p></td>
<td align="left"><p>Aktualisiert den master Bootcode auf dem Datenträger diesen Laufwerkbuchstaben zugeordnet. Boot-Code werden nicht aktualisiert werden, wenn entweder:</p>
<ul>
<li><p>&lt;DriveLetter&gt; ist nicht mit einem Volume verknüpft</p></li>
<li><p>&lt;DriveLetter&gt; zugeordnet ist, ein Volume nicht mit einer zugrunde liegenden Festplattenpartition verbunden.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Force</strong></p></td>
<td align="left"><p>Zwangsweise hebt die Bereitstellung des Volumes, auf denen während der Aktualisierung der Boot-Codebeispiel. Sie müssen diese Option mit Vorsicht verwenden.</p>
<p>Wenn Bootsect.exe exklusive Volume zugreifen kann, kann das Dateisystem den Boot-Code vor dem nächsten Neustart überschreiben. Bootsect.exe versucht immer, Sperren und Aufheben der Bereitstellung der Lautstärke vor jedem Update. <strong>Wenn/force</strong> angegeben ist, eine erzwungene Dismount versucht werden soll, wenn der erste Sperrversuch ein Fehler auftritt. Eine Sperre kann beispielsweise fehl, wenn die Dateien auf dem Zieldatenträger derzeit von anderen Programmen geöffnet werden.</p>
<p>Bei erfolgreicher eine erzwungene Dismount exklusive Volume-Zugriff wird aktiviert und ein zuverlässige Boot-Code zu aktualisieren, obwohl die erste Sperre ist fehlgeschlagen. Gleichzeitig wird eine erzwungene Dismount alle geöffneten Handles für Dateien auf dem Zieldatenträger ungültig. Dies kann unerwartetes Verhalten der Programme führen, die diese Dateien geöffnet. Verwenden Sie diese Option daher mit Vorsicht.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ MBR</strong></p></td>
<td align="left"><p>Aktualisiert den master Boot Record ohne Änderung der Partitionstabelle im Sektor 0 des Datenträgers, der von <strong>SYS</strong>, <strong>ALLE</strong>, angegebene Partition enthält, oder &lt;Laufwerkbuchstaben&gt;. Bei Verwendung mit der <strong>Option/nt52</strong> ist der master Boot Record mit Betriebssystemen vor Windows Vista kompatibel. Bei Verwendung mit der <strong>Option/NT60</strong> ist der MBR kompatibel mit Windows 8, Windows 7, Windows Vista, Windows Server 2012, Windows Server 2008 R2 oder Windows Server 2008.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

 

 






