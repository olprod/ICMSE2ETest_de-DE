---
title: "Nicht genügend Box-Experience"
description: "Nicht genügend Box-Experience"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D97B30B5-A604-483F-821C-9831218F2AA7
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: beaec02cb8475e66e1725326faad92a15bebd41b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="out-of-box-experience"></a>Nicht genügend Box-Experience


Betrifft: Windows 8.1 Windows 10

Diese Bewertung misst die Dauer der wichtigsten Aspekte der ersten Start Experience (OOBE), die normalerweise von Bild Anpassungen und Software Add-ons, die auf das Windows Retail Bild angewendet betroffen sind. Leistung Spuren Event Tracing for Windows (ETW) beim ersten Starten einer Windows-10-System mit gesammelt werden die Maße abgerufen. Die Bewertung misst die Dauer der ersten Anmeldung als auch bestimmte Aspekte wie Active Setup und Installieren der App bereitgestellt.

In diesem Thema:

-   [Bevor Sie beginnen](#beforebegin)

-   [Manuelle Ausführung der Bewertung](#bkmk-streamingworkloads)

-   [Einstellungen](#settings)

## <a name="a-href-idbeforebeginabefore-you-begin"></a><a href="" id="beforebegin"></a>Bevor Sie beginnen


**Warnung**  Diese Bewertung wird nicht automatisch ausgeführt.

 

**Warnung**  Das Bild wird getestet werden muss in einem Zustand nie wurde-gestartete in Reihenfolge für Maßeinheiten erfolgreich gesammelt werden. Versucht bewerteten Schwelle wieder auf den Pre-OOBE Status zurücksetzen, wird nicht Rendite vergleichbare Ergebnisse und wird nicht unterstützt.

 

## <a name="a-href-idbkmk-streamingworkloadsamanual-execution-of-assessment"></a><a href="" id="bkmk-streamingworkloads"></a>Manuelle Ausführung der Bewertung


Diese Bewertung erfordert manuelle Ausführung um die Daten erforderlich sind, um die Ergebnisse zu erfassen. Führen Sie die folgenden Anweisungen.

1.  Erstellen eines neuen Auftrags Paket mit nur die OOBE Bewertung.
    1.  Wählen Sie in der Windows-Konsole zur Bewertung der Registerkarte Fertigung und Bereitstellung. Wenn die Registerkarte nicht geöffnet ist, klicken Sie auf der Homepage, und doppelklicken Sie dann auf den Auftrag, um ihn zu öffnen.
    2.  Klicken Sie auf Paket.
    3.  Geben Sie im Paket einen Auftrag zum Ausführen auf einem anderen Computer Dialogfeld Notizen, mit die Hilfe Sie diesen Auftrag zu identifizieren, wenn Sie die Ergebnisse zu öffnen und anzeigen, wie Manufacturing gepackt und Bereitstellungsauftrag auswählen.
    4.  Geben Sie im Feld Pfad Paket den Speicherort, in der Sie das Paket Auftrag speichern möchten. In dieser Übung sollte der Speicherort auf einem Wechselmedium sein, wie ein USB-Laufwerk.
    5.  Geben Sie im Feld Pfad Ergebnisse des Speicherorts, in der Sie die Ergebnisse speichern möchten. Standardmäßig ist dies der relative Pfad des ein. \\Ergebnisordner am selben Speicherort, in dem der Auftrag ausgeführt wird.
    6.  Klicken Sie auf OK. Wenn der Auftrag verpackt wurde, wird der Speicherort des Auftrags geöffnet.
    7.  Das USB-Laufwerk ausschließen.

2.  Vorbereiten eines Computers durch Installieren des Windows-Bilds, das bewertet wird.
3.  Kopieren Sie das Paket auf diesem Computer (idealerweise auf einem anderen Datenträger und Partition) ein.
4.  Starten Sie den Computer.
5.  Bei die erste Aufforderung angezeigt wird, drücken Sie "UMSCHALT + F10" zu einer Admin-Eingabeaufforderungsfenster zu öffnen.
6.  Navigieren Sie zu Ihrem ADK-Paket. Führen Sie "cd Assessment1\\% PROCESSOR\_ARCHITEKTUR %" und führen Sie dann "hinzufügen\_autologger.reg". Vergewissern Sie sich, dass die registrierungseinstellungen erfolgreich importiert wurden.
7.  Führen Sie "Herunterfahren/r/t 0" in der Befehlszeile. Der Computer startet neu.
8.  Geben Sie nach dem Neustart die erforderlichen Daten, wenn Sie den Computer über OOBE fortgesetzt werden. Verwenden Sie ein lokaler oder je nach Szenario live-Konto an, die Sie testen möchten...
9.  Navigieren Sie beim Erreichen des Desktops zu Ihrer ADK-Paket. Führen Sie "cd Assessment1\\% PROCESSOR\_ARCHITEKTUR %" und führen Sie "Beenden\_autologger.cmd". Dies wird den ETW Trace sammeln, der mit der Autologger und andere relevante Protokolle gestartet wurde. Der Ordner mit dem Namen "Assessment1\\% PROCESSOR\_ARCHITEKTUR %\\&lt;Datum-Uhrzeit-&gt;\_&lt;Username&gt;\_&lt;Machinename&gt;" ist, in dem Ergebnisse erstellt werden.
10. Kopieren Sie diesen Inhalt an einen Computer mit der ADK installiert haben, um die Ergebnisse zu analysieren.

## <a name="settings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Diese Einstellungen werden von Microsoft, um sicherzustellen, dass die Ergebnisse können über verschiedene Computerkonfigurationen oder über einen Zeitraum auf demselben Computer verglichen werden definiert. Wenn Sie die Ergebnisse zu überprüfen, enthält die Laufzeit Informationen Metadaten, der angibt, dass die empfohlenen Einstellungen, damit Sie problemlos Ergebnisse erkennen können, die zusätzlich zu den empfohlene Einstellungen verwenden, die nicht verwendet wurden.

Sie können auch diese Einstellungen anpassen, wenn Sie andere Daten als was standardmäßig erfasst wird erfassen möchten. Beispielsweise können Sie bestimmte Daten identifizieren, mit denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers führen würde.

Die folgende Tabelle beschreibt die Einstellungen für die Bewertung Einstellungswerte und alternative Werte für jede Einstellung empfohlen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Manuell erfasste OOBE-Protokolle</p></td>
<td><p>Dies ist der vollständige Pfad zu dem Ordner, der die Trace und Protokolle durch die manuelle Ausführung von OOBE enthält.</p>
<p>Dies ist ein erforderlicher Parameter für die Analyse.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die außerhalb der Box-Experience Bewertung](results-for-the-out-of-box-experience-assessment.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







