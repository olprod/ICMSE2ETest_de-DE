---
author: kpacquer
Description: Feld Service-Szenarien
ms.assetid: 064509f8-902d-4ac8-85d9-7a405512d762
MSHAttr: PreferredLib:/library/windows/hardware
title: Feld Service-Szenarien
ms.openlocfilehash: b0d4e51602e55b4939c3b8597277e3c20b209674
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="field-service-scenarios"></a>Feld Service-Szenarien


Szenarien, damit um Sicherheitslücken im Feld Service-Prozesse zu erkennen. Jedes Szenario sollte überprüft werden, um sicherzustellen, dass eine sichere Lösung vom OEM implementiert wurde.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Prüfen des Geräts</p></td>
<td align="left"><p>Mobilfunkanbieter und OEMs können Geräte refurbish mithilfe verschiedener Methoden. Das erste Szenario Reparaturservice tritt auf, wenn Kunden Telefone an den Mobilfunkbetreiber aus irgendeinem Grund zurückzugeben. In diesem Fall werden die Geräte in der Regel an regionalen OEM Servicecenter geliefert, in dem sie mit dem aktuellen OEM-Bild reflashed werden.</p>
<p>Das zweite Reparaturservice Szenario tritt auf, wenn Kunden Probleme mit der Vorgang des Geräts vorliegen. Der Kunde setzt das Gerät wieder an den Mobilfunkbetreiber Speicher und die Store zuordnen führt einfache Diagnose aus. Die zuordnen kann das Telefon auf die herstellereinstellung zurückgesetzt oder einen reflash das Gerät OS mithilfe blinkende Tools von Microsoft (FFU) oder der OEM versuchen. Wenn dies nicht funktioniert, kann die Store zuordnen, senden das Gerät an eine OEM-Service-Center entscheiden. Bevor das Gerät bewirkt, die Kontrolle über den Mobilfunkbetreiber dass und den OEM zurückgegeben wird, wird ein Mechanismus verwendet, um die Kundendaten zu entfernen.</p>
<p>Die Erneuerung des Geräts in der Mitte der OEM-Dienst ist die dritte Reparaturservice Szenario. Das Gerät kann mit beliebigen Tools OEM Servicecenter mit ausgestattet ist reflashed sein. Einige OEMs verwenden auf Betriebssystemebene blinkende Technologie, was bedeutet, dass sie das Gerät einen reflash ist nicht möglich, wenn die Software oder der Modem Ebene des Startladeprogramms unterbrochen ist. Andere Benutzer werden können die Modem- und OS Partitionen einen reflash.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Problembehandlung von Telefon</p></td>
<td align="left"><p>Feld Test- und Diagnose-apps können verwendet werden, durch die Mobile Operator Store, Mobilfunkbetreiber Servicecenter und OEM service Center zum Durchführen der bestimmten Tests auf einem Telefon in zwei verschiedenen Szenarien.</p>
<p>Das erste Szenario für die Problembehandlung ist, wenn der Kunde mit dem Gerät Probleme ist und ein Diagnosetest ausgeführt wird, um das Problem gemeldet erfassen.</p>
<p>Das zweite Szenario ist, wenn der Mobilfunkbetreiber oder OEM Servicecenter seek Qualitätsstatus eines Geräts herstellen. In diesem Szenario ist die allgemeine Form der vorherigen Szenario für die Problembehandlung. Dies ist, da es sich möglicherweise weitere Gründe als Kunden Probleme, die die Notwendigkeit für Diagnose und Tests für den Einzelhandel Telefone auslösen würde. Beispielsweise konnte Feld Qualität Measures ausgeführt werden, der Test initiiert werden Informationen zum Ausführen der Stichprobe Tests.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Engineering blinken</p></td>
<td align="left"><p>Die technischen Mitarbeiter Halbleiterhersteller und OEMs benötigen Zugriff auf Technologien während der Entwicklung von Hardware und Software für die Telefone blinken. In diesem Szenario wird in der Regel von Low-Level-Technologien wie JTAG, blinken UEFI-basierten oder OEM-spezifische blinkende Technologien unterstützt. Welche Technologie ausgewählt ist, hängt von Problemen, die bearbeitet, Entwicklungsprozesse und unterstützende Tools. Die Granularität blinkende Optionen variiert. Low-Level-Tools haben mehr Flexibilität bei der Auswahl die Partitionen zugeordnet werden können.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Engineering-Diagnose</p></td>
<td align="left"><p>Die technischen Mitarbeiter von Halbleiterhersteller und OEMs benötigen Zugriff auf Diagnose Technologien während der Entwicklung von Hardware und Software für die Telefone. Diese Szenarien werden in der Regel von Technologien von der bereitgestellten PA oder OEM an, die auf Geräten Retail deaktiviert wird unterstützt. Einige der PA Technologien bieten einer breiten Palette von Funktionen – einschließlich Funktionen zur Unterstützung von lesen und Schreiben in den Arbeitsspeicher flash –, die deaktiviert werden müssen, bevor das Gerät ausgeliefert wird.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Mobilfunkbetreiber Testversionen (engl.)</p></td>
<td align="left"><p>Es muss möglicherweise eine blinkt OS Bilder an das Gerät zum Mobilfunkbetreiber Versuche unterstützen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Produktion Fertigung</p></td>
<td align="left"><p>Der Prozess der Telefone während der Herstellung blinkendes variiert je nach OEM. Einige OEMs verwenden Gang Programmierer, die eine Anzahl von Einheiten zu einem Zeitpunkt flash können; andere Benutzer verwenden die blinkende Technologie, die in dieser Dokumentation beschrieben. Nähere Informationen zu den blinkende Prozess finden Sie unter [Tools blinken](flashing-tools.md).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Gestalten Sie Fertigung</p></td>
<td align="left"><p>Einige OEMs haben einen Prozess direkten überarbeiten Telefone, die Fertigung Qualitätskontrolle fehlschlagen. Da das Gerät vollständig zusammengestellt wird, es möglich, ein Gang Programmierer möglicherweise nicht; Diese Überarbeitung kann mithilfe von erfolgen blinkendes Technologien ähnelt dem Szenario für die Rückgabe Reparaturservice angeschlossen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Remanufacturing</p></td>
<td align="left"><p>Es können vorhandene telefonbestand für eine andere Region oder Mobilfunkbetreiber Ändern eines Befehls durch Ersetzen der vorhandenen OS mit einem für den neuen Markt angepasst werden muss vorhanden sein.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Fertigung](index.md)

 

 






