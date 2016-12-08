---
author: Justinha
Description: DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten
ms.assetid: 698c8ad3-e292-45b2-9f74-d0e8885a7971
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten
ms.openlocfilehash: 3277792aff652a3fb73bf215259ced6b7d033b8e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-unattended-servicing-command-line-options"></a>DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten


Wenn Sie mehrere Pakete auf ein Bild Windows® installieren, verwenden Sie DISM eine Antwortdatei auf das Bild anwenden. Einige Pakete müssen andere Pakete zuerst installiert sein. Wenn die Anforderung einer Abhängigkeit vorhanden ist, ist die beste Möglichkeit zum Sicherstellen der richtigen Reihenfolge der Installation mithilfe einer Antwortdatei. Wenn Sie DISM verwenden, um eine Antwortdatei auf ein Bild angewendet wird, werden die unbeaufsichtigten Einstellungen im Durchgang **OfflineServicing** Konfiguration auf dem Windows-Abbild angewendet.

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_ Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Die folgenden Optionen stehen zur Verfügung, um eine Antwortdatei auf ein offline-Windows-Abbild anzuwenden:

**DISM.exe/Image:**&lt;*Pfad\_auf\_ Bild\_Verzeichnis* &gt; **/Apply-unattend:**&lt;*Pfad\_auf\_unattend.xml*&gt;

Die folgenden Optionen sind verfügbar, eine Antwortdatei auf einem ausgeführten Betriebssystem anwenden:

**DISM.exe / Online** **/Apply-unattend:** &lt; *Pfad\_auf\_unattend.xml*&gt;

Die folgende Tabelle enthält eine Beschreibung der wie eine unbeaufsichtigte Wartungsoptionen verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

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
<td align="left"><p><strong>/ Get-Help</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>Beim unmittelbar nach einer unbeaufsichtigten Wartung Befehlszeilenoption verwendet wird, werden Informationen zur Option und zu den Argumenten angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild angegeben wird.</p>
<p>Beispiele für die:</p>
<p><strong>DISM / online/Apply-Unattend /?</strong></p>
<p><strong>/ Apply DISM-/image:C:\test\offline Unattend /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Anwenden-unbeaufsichtigten:</strong>&lt;<em>Pfad_zu_unattend.XML</em>&gt;</p></td>
<td align="left"><p>Wendet eine Unattend.xml-Datei zu einem Bild.</p>
<p>Wenn Sie Gerätetreibern mithilfe einer Antwortdatei aktualisieren, müssen Sie die Antwortdatei auf ein offline-Abbild anwenden und angeben, dass die Einstellungen in die Konfiguration <strong>OfflineServicing</strong> übergeben.</p>
<p>Wenn Sie Pakete oder anderen Einstellungen, die mithilfe einer Antwortdatei aktualisieren, können Sie zu einem Bild offline- oder Onlinemodus die Antwortdatei anwenden. Geben Sie die Einstellungen im Durchgang <strong>OfflineServicing</strong> Konfiguration.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml</strong></p>
<p><strong>DISM / online /Apply-Unattend:C:\test\answerfiles\myunattend.xml</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


-   Sie können nicht in der gleichen Befehlszeile mit unbeaufsichtigten Wartung Befehlen anderer Befehle zum Warten verwenden.

-   In einer Befehlszeile kann nur eine einzelne Antwortdatei angegeben werden.

-   Wenn Sie ein Bild mit einer Antwortdatei Pakete hinzufügen, wird die Verfügbarkeit des Pakets nicht überprüft werden soll. Die Antwortdatei angewendet wird, und der Vorgang wird abgeschlossen, auch wenn es in die Antwortdatei angegebenen Pakete nicht auf das Bild anwenden. Wenn Sie die Verfügbarkeit eines Pakets überprüfen, wenn Sie es zu einem Bild hinzufügen müssen, verwenden Sie den Befehl **DISM** zusammen mit der **Option/Add-Package** , ohne die **Option/IgnoreCheck** . Weitere Informationen finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

-   Wenn Sie mithilfe einer Antwortdatei Gerätetreiber aktualisieren, müssen Sie die Antwortdatei auf ein offline-Abbild anwenden.

-   Wenn Sie eine Antwortdatei auf einem ausgeführten Betriebssystem anwenden DISM.exe verwenden, sollte die Antwortdatei nur Elemente im **OfflineServicing** Konfiguration Durchgang enthalten. Dies ist, da einige Einstellungen in der Spezialisierungskonfigurationsdurchlauf für das Betriebssystem angewendet werden können. Es wird empfohlen, dass die Antwortdatei, die mit DISM verwendet, nur Einstellungen im **OfflineServicing** Konfiguration Durchgang enthalten.

-   Die empfohlene Option zum Antwortdateien ist in Windows System Image Manager (Windows SIM) erstellt. Wenn Sie eine manuell erstellte Antwortdatei verwenden, müssen Sie jedoch überprüfen die Antwortdatei in Windows SIM, um sicherzustellen, dass es funktioniert. Weitere Informationen finden Sie unter [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073).

-   Wenn Sie eine Antwortdatei mithilfe von DISM anwenden, wird die Antwortdatei nicht auf dem Zielcomputer zwischengespeichert.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[DISM Windows Edition zum Warten von Befehlszeilenoptionen](dism-windows-edition-servicing-command-line-options.md)

[Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)

 

 






