---
title: Dateiverarbeitung
description: Dateiverarbeitung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e12b8753-0c25-4dd6-8876-3b304ea69d24
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: e5d196e39159889f97a7cb16ae38ded4da886c5b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="file-handling"></a>Dateiverarbeitung


Das Dateiverarbeitung Assessment bietet eine automatisierte Möglichkeit, allgemeine Dateivorgänge Übung und Metriken erfassen. Diese Bewertung misst Dauer und Durchsatz beim Kopieren, verschieben, komprimieren, extrahieren und Löschen von Dateien und Ordnern auf Ihrem Computer. Die Ergebnisse können Sie verstehen, wie gut der Computer während diese Vorgänge ausgeführt wird. Weitere Informationen zu den Ergebnissen finden Sie unter [Ergebnisse für die Datei behandeln Bewertung](results-for-the-file-handling-assessment.md).

**Warnung**  
Das Assessment Dateiverarbeitung wird nur auf Englisch (USA) Versionen von Windows unterstützt. Diese Bewertung auf nicht Englisch (USA) Versionen von Windows ausgeführt wird möglicherweise Aufforderung Sie mit einem Fehler und die Bewertung möglicherweise nicht mehr ausgeführt.

 

Die folgende Abbildung veranschaulicht die Bewertungsprozess.

![Workflow-Grafik für die Dateibehandlung von](images/dep-win8-8-techref-fileorgassessmentflow.jpg)

In diesem Thema:

-   [Systemanforderungen](#sysrqmnts)

-   [Arbeitslasten](#bkmk-fileworkloads)

-   [Einstellungen](#assesssettings)

## <a name="a-href-idsysrqmntsasystem-requirements"></a><a href="" id="sysrqmnts"></a>Systemanforderungen


Die erste Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Führen Sie diese Bewertung nur während der Desktop im Vollbildmodus ist. Diese Bewertung wird nicht ausgeführt, wenn Sie eine andere Windows Store app geöffnet Side-by-Side mit dem Desktop verfügen.

Bei der Ausführung dieser Bewertung auf Windows 8.1, stellen Sie sicher, dass die Einstellung **Sammeln Analysis Trace** bei der Beurteilung der erwarteten Akkulaufzeit deaktiviert ist. Wenn diese Option aktiviert ist, erzeugt diese Option eine falsche Schätzung.

Aktivieren Sie nur, wenn Sie weitere Informationen zum Untersuchen von anderen Probleme im Zusammenhang mit Energie benötigen Analysis Trace-Auflistung.

Sie können diese Bewertung unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows-10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme. Die Bewertung wird für die Verwendung auf virtuellen Computern nicht unterstützt.

Sie können diese Bewertung auf Windows RT in einem der folgenden Verfahren ausführen:

-   Packen des Bewertung Auftrags in der Windows-Assessment-Konsole und führen sie dann auf Windows RW Weitere Informationen finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausgeführt Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idbkmk-fileworkloadsaworkloads"></a><a href="" id="bkmk-fileworkloads"></a>Arbeitslasten


Eine Arbeitslast ist ein Satz von automatischen Aufgaben, die Aktivität des Benutzers auf eine vordefinierte, wiederholbare Weise simulieren. Diese Bewertung misst, Dauer und Durchsatz für die folgenden Arbeitslasten und es die Kriterien in der Datei mit den Suchergebnissen erfasst.

-   **Programmgesteuerte Arbeitslasten.** Diese Arbeitslasten mithilfe der API, Dateifunktionen auszuführen. Diese Arbeitslasten messen Sie die zugrunde liegende Datei Funktionalität. Dateivorgänge gehören **Copypg**, **Movepg**und **Deletepg**.

-   **Arbeitslasten in Skripte integriert.** Diese Arbeitslasten simulieren Benutzeraktivität im Datei-Explorer auf einem Computer mit Windows 8. Dateivorgänge gehören **Copyuxxs**, **Deleteuxs**, **Moveuxs**und **Zipuxs**. Skriptgesteuerte Arbeitslasten können nicht verwendet werden, wenn Sie die Bewertung auf einem Computer mit Windows 7 ausführen.

Weitere Informationen zur Auswahl einer Arbeitslast finden Sie unter [Einstellungen](#assesssettings).

**Hinweis**  
Sie können auch das Assessment Dateiverarbeitung als einer Arbeitslast in einem Auftrag Energie-Effizienz. Weitere Informationen zu Aufträgen Energie-Effizienz finden Sie unter [Erstellen und Ausführen einer Energie Effizienz Auftrag](create-and-run-an-energy-efficiency-job.md).

 

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen können. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

Wenn Sie möchten, zum Erfassen von Daten, die unterscheidet sich von was die Bewertung standardmäßig erfasst wird, können Sie auch die Einstellungen anpassen. Jedoch, wenn Sie die Quell- oder Ziel-Standardordner ändern oder Ihre eigenen Dateien bereitstellen, Vergleiche möglicherweise nicht mehr relevant.

**Hinweis**  
Nach der Ausführung der Bewertung möglicherweise alle Dateien aus dem Papierkorb dauerhaft gelöscht werden. Vor dem Ausführen der Bewertung überprüfen Sie alle Dateien aus dem Papierkorb da sie nicht verfügbar oder wiederherstellbare nachdem die Bewertung abgeschlossen wurde.

 

In der folgenden Tabelle werden die Einstellungen für die Assessment empfohlen, Werte und alternative Werte für jede Einstellung beschrieben.

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
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Iterationen</p></td>
<td><p>Gibt die Anzahl der Versuche, die die Bewertung ausgeführt wird. Standardmäßig ist der Wert 1. Bewertung mehrmals ausführen und durchschnittliche Dauer der Ergebnisse, erhöhen Sie diesen Wert.</p></td>
</tr>
<tr class="odd">
<td><p>Source</p></td>
<td><p>Gibt den Speicherort an, dem die Bewertung der Arbeitslast Dateien oder Ordner aus kopiert. Um einen Speicherort als die Standardstärke festzulegen, geben Sie einen Pfad zu dem Quellordner in das Feld ein. Die Bewertung können mehrere Computer, externe Geräte und Netzwerkadressen des Quellordners.</p>
<p>Arbeitslasten können konfiguriert werden, um Dateifunktionen im Ordner "Source" allein auszuführen, oder Sie können einen Ordner Quell- und Zielserver angeben.</p></td>
</tr>
<tr class="even">
<td><p>Ziel</p></td>
<td><p>Gibt den Speicherort an, dem die Bewertung der Arbeitslast Dateien oder Ordner kopiert. Sie benötigen Schreibzugriff auf den Zielordner. Wenn Sie einen Speicherort als die Standardstärke festzulegen, geben Sie einen Pfad in den Zielordner im Feld. Wenn Sie einen Zielordner aus verschiedenen bereitstellen, muss der Zielordner leer sein, vor der Bewertung.</p>
<p>Arbeitslasten können Informationen zum Ausführen der Dateifunktionen aus dem Quellverzeichnis allein konfiguriert werden, oder Sie können einen Ordner Quell- und Zielserver angeben. Externe Geräte und Netzwerkadressen werden unterstützt.</p></td>
</tr>
<tr class="odd">
<td><p>Aktivieren von Neustarts</p></td>
<td><p>Gibt an, dass der Computer vor jeder Dateivorgang neu gestartet wird. Standardmäßig aktiviert nicht.</p>
<p>Verwenden Sie diese Option, um ein System bereinigen Timeout jeder Vorgang sicherzustellen. Dies ist besonders nützlich für das Testen von Antivirensoftware Verhalten.</p></td>
</tr>
<tr class="even">
<td><p>Ausführung Verzögerung</p></td>
<td><p>Gibt an, die Zeit in Sekunden an, nach einem Neustart vor der Ausführung der Dateioperation warten ist. Diese Option ist nur verfügbar, bei Verwendung des Parameters "Neustarts aktivieren". Der Standardwert ist 300 Sekunden.</p>
<p>Dieser Parameter können Sie die Zeitspanne für den Computer in den rest vor dem Ausführen des Vorgangs bestimmte Datei für die Iteration steuern.</p></td>
</tr>
<tr class="odd">
<td><p>Arbeitslast</p></td>
<td><p>Gibt an, welche Arbeitslasten ausführen. Skriptgesteuerte Arbeitslasten und Programmatic zur Verfügung stehen. Standardmäßig werden nur programmgesteuerten Arbeitslasten ausgeführt.</p>
<p>Weitere Informationen zu der Datei-Funktionen von jeder Arbeitslast ausgeführt finden Sie unter [Arbeitslasten](#bkmk-fileworkloads).</p></td>
</tr>
<tr class="even">
<td><p>Datenspeicherort importieren</p></td>
<td><p>Gibt den Speicherort der Dateien, die Sie während der Bewertung verwenden möchten. Wenn ein Speicherort importieren angegeben wird, kopiert die Bewertung die Dateien aus dem <strong>Datenspeicherort importieren</strong> auf Quellordners. Während des Aktivierungsvorgangs Assessment wird der Inhalt der Quelle in den Zielordner kopiert. Aus diesem Grund müssen die Quell-und die Zielordner leer sein, wenn die Bewertung beginnt.</p></td>
</tr>
<tr class="odd">
<td><p>Minifilter Diagnosemodus aktivieren</p></td>
<td><p>Gibt an, ob die Diagnose Minifilter Option verwenden. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Minifilter Diagnosemodus aktiviert ist, generiert er Metriken, mit denen Sie die Auswirkung des Minifilter auf Dateibehandlung bewerten. Weitere Informationen zu dieser Einstellung finden Sie unter [Minifilter Diagnose](minifilter-diagnostics.md).</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die Diagnose Minifilter Option wird nur unter Windows 8 unterstützt.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Dateiverarbeitung durch den Bewertung](results-for-the-file-handling-assessment.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

[Minifilter Diagnose](minifilter-diagnostics.md)

 

 







