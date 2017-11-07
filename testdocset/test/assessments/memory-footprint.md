---
title: Speicherbedarf
description: Speicherbedarf
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e2e18edf-c9b2-4401-b879-c08f59ca74c7
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 3cfe7d68e39a39f2a8d17a93e216616b700844f6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="memory-footprint"></a>Speicherbedarf


Die Bewertung Speicherbedarf können Sie ein Betriebssystemabbild Baseline gegen eine andere Betriebssystemabbilds Quantitatives verglichen werden soll. Klicken Sie dann können Sie bestimmten Komponenten identifizieren, die Einfluss auf die Speicherbedarf von physischen System. Diese Komponenten können Treiber, Add-In-Programme, vorinstallierte Softwarepakete und Antivirenprogramme enthalten.

Mithilfe der Bewertung Speicherbedarf können Sie den Effekt vergleichen, den verschiedene Hardwarekonfigurationen und der zugehörigen Software auf Systemspeichers haben. Nach dem Vergleichen von zwei Systemabbilder in ein Side-by-Side lesen, Sie können festlegen, ändern Sie Treiber oder höherer Speicherbedarf Ihres Systems auf andere Weise zu optimieren.

**Hinweis**  
Diese Bewertung erstellt eine Momentaufnahme der Speicherverwendung während der eine Reihe von Assessment beim Starten des Systems und unmittelbar nach der Darstellung von Desktop in Windows 10 oder der Startseite in Windows 10 Enterprise. Es wird nicht Speicherverwendung während der normalen Computer Vorgänge ausgewertet. Weitere Informationen zu den Ergebnissen dieser Beurteilung erzeugt, finden Sie unter [Ergebnisse für die Bewertung der Speicher Bilanz](results-for-the-memory-footprint-assessment.md).

 

In der folgenden Grafik veranschaulicht den Bewertung. Wie die Grafik veranschaulicht wird, muss die Bewertung mehrere Systemneustart alle Assessment Ergebnisse zu generieren.

![Workflow für Speicher-Bilanz](images/dep-win8-8-techref-memoryfootprint.jpg)

In diesem Thema:

-   [Bevor Sie beginnen](#beforebegin)

-   [Einstellungen](#assesssettings)

## <a name="a-href-idbeforebeginabefore-you-begin"></a><a href="" id="beforebegin"></a>Bevor Sie beginnen


Diese Bewertung umfasst Systemneustart als normaler Bestandteil der Bewertungsprozess. Zum Konfigurieren des Computers zum Ausführen von Assessment Aufträge automatisch und ohne manuelle Neustarts oder System aufgefordert werden, finden Sie unter [automatisieren Neustarts, bevor Sie eine Bewertung ausführen](automate-reboots-before-you-run-an-assessment.md).

### <a name="system-requirements"></a>Systemanforderungen

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows 10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Es gibt zwei Methoden zur Ausführung dieses Assessment in Windows RT:

-   Packen Sie den Assessment Auftrag in der Windows-Assessment-Konsole und führen sie dann auf Windows RW Weitere Informationen zu dieser Option finden Sie unter. [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausführen Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>Einstellungen


Microsoft definiert die empfohlenen Einstellungen, damit Sie können die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

Sie können auch die Einstellungen für eine Bewertung, anpassen, wenn Sie möchten, zum Erfassen von Daten, die sich aus der Standarddaten unterscheidet. Beispielsweise können Sie Daten zu beschreiben, mit denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers ausführen würden.

In der folgenden Tabelle wird beschrieben, die Einstellungen für die Bewertung empfohlene Einstellungswerte und alternative Werte für jede Einstellung.

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
<td><p>Empfohlene Einstellungen verwenden</p></td>
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet wird. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Configuration</p></td>
<td><p>Gibt Optionen an, denen Sie auswählen können, um die Art des Tests Arbeitsspeicher konfigurieren, die die Bewertung durchführt. Diese Optionen sind wie folgt:</p>
<ul>
<li><p><strong>Vollständiges ausführen.</strong> Diese Option bietet mehr genaue Ergebnisse, aber es dauert länger dauern. Diese Option wird mit sechs vorbereitenden Neustarts, gefolgt von einem siebten Messen der Neustart möglichst genaue Messung der speicherauslastung durch den sichergestellt.</p></li>
<li><p><strong>Schnelles ausführen.</strong> Diese Option ist nicht mit dem System vorbereitenden Schritte der vollständigen Ausführung enthalten. Aus diesem Grund verkürzt es die Dauer der Auftrag ausgeführt wird. Die Informationen, die sie bietet ist weniger umfassend, aber dennoch geeignet.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Symbolpfad</p></td>
<td><p>Zeigt den Pfad des Servers Microsoft öffentliches Symbol für Windows. Die Bewertung wird Symbole verwendet, um sicherzustellen, dass ihre Ergebnisse als Treiber Zuweisungen anstelle von Kernel-Zuweisungen Treiber Speicher anzeigen. Ohne die Verwendung von Symbolen kann die Analyse Assessment falsch Memory Allocation Quelle identifizieren. Dadurch kann Probleme verschleiern und Treiberprobleme ausblenden. Weitere Informationen zum Symbolserver finden Sie unter [wie: Verwenden eines Servers Symbole](http://go.microsoft.com/fwlink/?LinkId=242234).</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn Sie keine Verbindung mit dem Symbolserver herstellen können, können Sie die folgenden Schritte aus, um Assessment Genauigkeit nutzen:</p>
<ul>
<li><p>Laden Sie die Symbole und kopieren Sie sie auf dem Computer, den Sie ermitteln möchten. Diese Option erfordert, dass Sie den Pfad zu der lokale Symbole bereitzustellen.</p></li>
<li><p>Führen Sie Bewertung auf einem einzigen Computer aus und Laden Sie das Ablaufverfolgungsprotokoll auf einem anderen Computer mit Zugriff auf die Symbole (, da es mit dem Internet verbunden ist oder bereits heruntergeladenen Symbole enthält). Führen Sie dann die Analyse mithilfe des Analysis-only-Modus.</p></li>
</ul>
</div>
<div>
 
</div>
<p>Weitere Informationen zu fehlenden Symbole und Bewertung Genauigkeit finden Sie unter [Häufige Depth Analysis Probleme](common-in-depth-analysis-issues.md).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Bewertung der Speicher-Bilanz](results-for-the-memory-footprint-assessment.md)

[Windows-Assessment-Toolkit](index.md)

[Bewertung](assessments.md)

[Schrittweise Anleitung für Windows-Bewertungen-Konsole](windows-assessment-console-step-by-step-guide.md)

 

 







