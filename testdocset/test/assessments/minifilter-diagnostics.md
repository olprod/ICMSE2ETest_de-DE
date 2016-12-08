---
title: Minifilter Diagnose
description: Minifilter Diagnose
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fc7638a8-587c-4626-b0bd-a056639441fb
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: c68131faa1eb7ee7a2c5f09e29ba5905bdc1af5e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="minifilter-diagnostics"></a>Minifilter Diagnose


Dieses Thema hilft Ihnen Interpretieren der Ergebnisse, die mit mit einem der der Minifilter diagnostic Bewertung oder Ergebnisse, die erstellt werden, werden, da die Minifilter Diagnosemodus in eine Bewertung. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die Endbenutzer Erfahrung und wahrgenommene Leistung eines Computers betreffen.

Ein Minifiltertreiber handelt es sich ein Filter, der fängt System Anfragen, die an einem Dateisystem oder einer anderen Dateisystemfilter gerichtet sind. Durch das Abfangen der Anforderung an, bevor er seine beabsichtigte Ziel erreicht, kann der Filtertreiber erweitern oder Ersetzen Sie die ursprünglichen als Ziel für die Anforderung bereitgestellten Funktionen. Beispiele für Dateisystem Filter-Treiber sind Antiviren-Filter, backup-Agenten und Verschlüsselung/Entschlüsselung Produkte. Filtertreiber werden durch ein legacy-Treiber möglich mit dem Namen Filter-Treiber.

Ein Minifilter macht Rückrufe für Pre- und Post Verarbeitung der e/a-Datei. Der Filtertreiber kommuniziert mit dem Minifilter über diese Rückrufe auf. Minifilter dienen zum Verarbeiten der standard-e/a; Sie werden nicht verwendet, wenn eine Anwendung zugeordneten Speicherzuordnungsdateien verwendet.

In diesem Thema:

-   [Informationen zu Minifilter Diagnosemodus](#bkmk-minifilterabout)

-   [Metriken](#bkmk-minifiltermetrics)

## <a name="a-href-idbkmk-minifilteraboutaabout-minifilter-diagnostic-mode"></a><a href="" id="bkmk-minifilterabout"></a>Informationen zu Minifilter Diagnosemodus


Minifilter wurden entwickelt, damit abgefangen Datei-e/a einfacher, als es andere Profiler-Software verwenden werden. Ohne Minifilter müssen Entwickler legacy-Treiber schreiben, die eine Herausforderung und fehleranfällig sein kann.

Da Minifilter Code für die meisten Datei e/a ausführen, kann ihre Leistung Applications und durch den Endbenutzer erheblich beeinträchtigen. Ein schlecht implementierter Minifilter kann dazu führen, dass wahrgenommene langsame des Computers. Minifilter Diagnosemodus dient zum Identifizieren der derartige Treiber durch Ausführen von drei e/a-intensive Aufgaben, die Folgendes umfassen:

-   Standard-Dateisystemvorgänge wie verschieben, kopieren und Löschen einer Datei.

-   Laden Sie eine Anwendung, und Überwachen der e/a erforderlich, um alle abhängigen zu laden.

-   Starten Sie den Computer und Überwachen von e/a zur Unterstützung bei der Suche nach Minifilter, die möglicherweise eine negative Auswirkung auf die Leistung beim Starten und beenden.

Es gibt drei Analysen, die eine Assessment-Einstellung für die **Diagnose Minifilter-Modus aktivieren** enthalten, während die Bewertung ausgeführt wird. In der Standardeinstellung ist für diese Bewertung Minifilter Diagnosemodus deaktiviert:

-   Dateiverarbeitung

-   Internet Explorer zum Starten des Leistung

-   Start-Leistung (Fast Start)

Diese drei Bewertung stehen ebenfalls zur Verfügung, wenn Minifilter Diagnose standardmäßig aktiviert ist. Sie sind mit anderen verfügbaren Bewertung als aufgelistet:

-   Minifilter Diagnose: Die Dateibehandlung

-   Minifilter Diagnose: InternetExplorer

-   Minifilter Diagnose: Start-Leistung (Fast Start)

Alle drei Bewertung (mit Minifilter Diagnose aktiviert), betreiben, bietet einen umfassenden Überblick über die wie Minifilter des Systems auswirken. Jedes Assessment wird ein bestimmtes Szenario ausgeführt und Sammeln von Daten auf das Verhalten der auf dem System installierte Minifilter. Diese Daten können mithilfe der Windows Assessment Konsole, die Windows-Assessment-Services - Client (Windows ASC) oder Windows Performance Analyzer (WPA) analysiert werden. Die Gruppe Assessment Tools die Daten in eine andere Weise als WPA ist, aber diese Tools können Sie ein Drilldown finden Sie unter den Effekt der Minifilter.

**Minifilter Diagnose: Assessment Dateiverarbeitung**

Die Diagnose Minifilter: Dateiverarbeitung Assessment führt Aktionen wie verschieben, kopieren und Löschen von Dateien im Dateisystem des Dateisystems. Diese Bewertung misst Wand Systemzeit und Durchsatz für jede dieser Arten von e/a. Weitere Informationen zu dieser Bewertung finden Sie unter [Behandeln von Datei](file-handling.md).

Die Diagnose Minifilter: Dateiverarbeitung Assessment sammelt Daten wie die Wand Systemzeit erforderlich, um das Kopieren, verschieben oder Löschen einer Datei im Dateisystem, zusätzlich zu den Durchsatz, sofern zutreffend. Wenn Sie einen Drilldown auf alle wichtigen Minifilter Callback-Routinen finden Sie unter, finden Sie, dass jeweils die Zeit für die Durchführung der Anrufe und die durchschnittlichen und maximalen Zeiten aufgerufen wurde, wie oft.

**Minifilter Diagnose: InternetExplorer**

Die Diagnose Minifilter: InternetExplorer Assessment wird eine einzelne Registerkarte mit einfachem Inhalt in einem neuen Internet Explorer-Fenster geöffnet. Internet Explorer befindet sich eine mittlere bis große Anwendung, die eine lange Liste von abhängige DLLs hat. Die Bewertung dient als Proxy für eine beliebige Anwendung starten und dann überwachen wie gut die installierten Minifilter Verhalten. Weitere Informationen zu dieser Bewertung finden Sie unter [Start Leistung im Internet Explorer](internet-explorer-startup-performance.md).

Die Diagnose Minifilter: InternetExplorer Assessment bietet Daten beispielsweise die Zeit, die einen Frame erstellen, erstellen Sie eine Registerkarte, und Starten der Anwendung. Wenn Sie einen Drilldown alle wichtigen Mini Filter Callback-Routinen sehen, finden wie oft Sie, dass jeweils die Zeit für die Durchführung der Anrufe und die durchschnittlichen und maximalen Zeiten aufgerufen wurde.

**Minifilter Diagnose: Start-Leistung (Fast Start)**

Die Diagnose Minifilter: Start-Leistung (Fast Start) Bewertung startet das System und e/a-Aktivität in diesem Zeitraum kritische überwacht. Die Ergebnisdaten ist nach der Phase der Datei Boot organisiert. 17 Phasen des Startvorgangs sind vorhanden. Ein bestimmten Mini Filter kann die Boot in mehreren Phasen auswirken. Weitere Informationen zu dieser Bewertung finden Sie unter [Weiter Übergang Leistung](onoff-transition-performance.md).

Wenn Sie einen Drilldown auf alle wichtigen Mini Filter Callback-Routinen finden Sie unter, finden Sie die Anzahl der Häufigkeit, mit die jeweils aufgerufen wurde, die Zeit, die bis zum Abschließen der Aufrufe und die durchschnittlichen und maximalen Zeiten.

Weitere Informationen zum Ergebnis speziell für jede Bewertung finden Sie unter:

-   [Ergebnisse für die Dateiverarbeitung durch den Bewertung](results-for-the-file-handling-assessment.md)

-   [Ergebnisse für die Internet Explorer zum Starten des Performance-Bewertung](results-for-the-internet-explorer-startup-performance-assessment.md)

-   [Ergebnisse für die Bewertung ein-/ausschalten](results-for-the-onoff-assessments.md)

Es gibt zwei Arten von Problemen, die durch Bewertung generiert. Es sind vor Konfigurationsprobleme, die Sie steuern können, indem Sie reagieren auf die Fehler und Warnungen, die angezeigt werden, bevor die Bewertung beginnt. Wenn Sie diese vor dem Starten des Assessment nicht behoben werden Probleme generiert und die Ergebnisse Assessment hinzugefügt. Art des Problems wird generiert, wenn das Ziel für diese Metrik ein metrischer Wert verglichen wird. Beginn häufig Analyse mit diesen Problemen. Einige Probleme erfordern eine Neukonfiguration des Computers und die Bewertung erneut ausführen, und andere sind während der Bewertung durchgeführte Messungen, die potenzielle Problemen anzuzeigen.

Durch Ausführen dieser drei Bewertung sehen Sie beeinflussen, die Minifilter auf Start und häufige Verwendung des Computers haben. Markieren Sie die Ergebnisse möglicherweise Probleme, die speziell für das Szenario Assessment, aber die Ergebnisse können auch Minifilter Probleme zu identifizieren und Vergleichen der Ergebnisse verwendet werden. Beispielsweise können Sie beeinflussen vergleichen, die verschiedene Virenschutz (a/v) Pakete im System durch Ausführen der Bewertung auf zwei identische Systeme, die nur aufgrund der a/v-Software zu unterscheiden, die installiert ist. Sie können auch zwei verschiedene Computern vergleichen, die die gleiche a/v-Software installiert sein. Alternativ können Sie nur einen Computer verwenden und führen Sie die Bewertung mit einem a/v-Programm installiert haben, und klicken Sie dann deinstallieren und installieren ein anderes a/v-Programm, bevor Sie die drei Bewertung erneut ausführen. In beiden Fällen können Sie alle Ergebnisse für einen Vergleich der Side-by-Side öffnen und Analyse beginnen.

## <a name="a-href-idbkmk-minifiltermetricsametrics"></a><a href="" id="bkmk-minifiltermetrics"></a>Metriken


Dieser Abschnitt beschreibt die wichtigsten Minifilter-Metriken, allgemeine schlechte Ergebnisse für diese Metriken und allgemeine Behebung für Probleme, führt. In diesem Abschnitt versucht auch die Benutzergruppe mit identifiziert den größten Einfluss auf jede dieser Metriken.

In diesem Abschnitt:

-   [Minifilter metrischen Hierarchie](#bkmk-minifiltermetrichierarchy)

-   [Längste Verzögerung](#bkmk-minifiltermetriclongest)

-   [Minifilter Verzögerung](#bkmk-minifiltermetricdelay)

-   [Durchschnittliche Anrufdauer](#bkmk-minifiltermetricavgcall)

-   [Minifilter Rückrufe](#bkmk-minifiltermetriccallback)

### <a name="a-href-idbkmk-minifiltermetrichierarchyaminifilter-metric-hierarchy"></a><a href="" id="bkmk-minifiltermetrichierarchy"></a>Minifilter metrischen Hierarchie

Minifilter Diagnosemodus ergibt Dauer Metriken. Beispielsweise wenn die Diagnose Minifilter für die Bewertung Dateiverarbeitung aktiviert ist, wird die Dauer für die Kopie Arbeitslast, zusätzlich zu den untergeordneten Metriken gruppiert nach Minifilter oder gruppiert nach Rückruftyp angezeigt. Im folgenden Diagramm wird die Hierarchie der Metriken Minifilter angezeigt:

![Zeigt Ebenen der Ergebnisse für Minifilter](images/dep-win8-8-techref-minifilterdrilldown.jpg)

Minifilter metrischen Werte werden unter logischen Gruppen tief geschachtelt. Diese Hierarchie von Ergebnissen können Sie die Details eines Assessment Arbeitslast oder der Phase, die die Ergebnisse generiert, denen Sie interessiert sind anzeigen. Sobald Sie die Ergebnisse für eine Arbeitslast erweitern, sehen die Liste der Minifilter und die Ergebnisse, die sie jeweils bereitstellen, die auf der Ebene der Arbeitslast aggregiert werden. Wählen Sie einen bestimmten Minifilter aus der Liste aus, und sehen Sie die Liste der Anrufe anhand dieser Minifilter. Wählen Sie einen interessanten Anruf aus, und überprüfen Sie den vor- oder nach der Vorgänge, die die Ergebnisse generiert, die Sie interessant sind. Es folgt ein Beispiel:

**Hinweis**  
Bei der Bewertung Datei behandeln Performance wird die Detailebene für die erste Ebene der *Arbeitslast* aufgerufen. In Start Leistung Bewertung oder bei der Bewertung der Leistung von Internet Explorer zum Starten des wird die erste Detailebene der *Phase* Ebene bezeichnet.

 

![Beispielergebnisse für Minifilter Drilldown](images/dep-win8-8-techref-minifilterdrilldown-sample.jpg)

In diesem Szenario hatte die Arbeitslast CopyPG 14.494 Wert. Wenn Sie das Ergebnis erweitern, finden Sie, dass der Treiber minifilter1.sys war, der einen Wert von 11.541 auf den Wert der CopyPG Arbeitslast beitragen. Wenn Sie das Ergebnis minifilter1.sys erweitern, sehen Sie, dass die Bereinigung Rückruf an die Quelle des Werts des 11.541 war. Wenn Sie den Typ der Cleanup-Rückruf erweitern, finden Sie, dass der Vorgang MiniFilterPreOpComp war, der bei einem Wert von 11.541 gemessen wurde.

Mithilfe dieser Methode können Sie genau die Operation, die Rückruftyp, die Minifilter einrichten oder Arbeitslast-Phase bestimmte Ergebnisse erzeugt. Darüber hinaus zeigt jede **Gruppe von** Dropdown-Schaltfläche andere Metriken, die nicht standardmäßig sichtbar sind. Wählen Sie beliebige dieser zusätzlichen Kategorien, um weitere Metriken zur Analyse anzuzeigen.

### <a name="a-href-idbkmk-minifiltermetriclongestalongest-delay"></a><a href="" id="bkmk-minifiltermetriclongest"></a>Längste Verzögerung

Die längste Verzögerung Metrik ist die längste Verzögerung in der Verfolgung gefunden wird, während die Bewertung ausgeführt wurde. Diese Metrik ist für alle wichtigen e/a-Vorgänge wie etwa die Sperre Vorgänge erstellen, Steuerelement, Bereinigung, Informationen, lesen, schreiben und Einlesen verfügbar. Große Werte für diese Metrik können wahrnehmbar Stellplätze angeben, beim Ausführen einer Dateivorgänge, starten und zum Starten des Internet Explorer.

**Am besten:** Minifilter Vendors, ISVs haben den größten direkten Einfluss auf diese Metrik die Art und Weise, wie sie die Minifilter implementieren. Endbenutzer und OEMs haben indirekte Einfluss auf diese Metrik basierend auf der Minifilter Produkte, die sie installieren.

**Typische Schlüsselfaktoren Faktoren**

In dieser Metrik große Werte werden in der Regel durch Hintergrund Aktivitätsprotokolls auf dem System verursacht, während die Bewertung wird ausgeführt, jedoch Sie auch eine falsche Minifilter entwurfsbedingt verursacht werden können. Für bestimmte kann Arbeitslasten (beispielsweise Kopieren), die Größe der Dateien auch diese Metrik beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Wenn Minifilter Ergebnisse um Regressionen in einer einzelnen Softwarekomponente zu identifizieren, ist die zutreffenden zum Vergleichen von Ergebnis durch Ausführen der Bewertung für zwei Versionen derselben Komponente erstellt oder um die Ergebnisse aus verschiedenen Anwendungsentwickler zwei ähnlicher Produkte vergleichen.

Der erste Schritt besteht, die längste Verzögerung zu erhalten. Erweitern Sie die Minifilter Details dazu mit der rechten Maustaste in der Spalte längsten Verzögerung und wählen Sie nach absteigend sortieren.

Um die Qualität der Ergebnisdaten sicherzustellen:

-   Schließen Sie alle Anwendungen, die im Hintergrund ausgeführt werden.

-   Nachdem die wichtigste Komponente identifiziert wurde, sollten Sie Isolieren von die Auswirkungen durch andere optional Dienste beenden und die Bewertung für den Vergleich erneut ausführen.

-   Stellen Sie sicher, dass das System nicht überlastet ist, alle Speicher ist bei der Ausführung dieser Bewertung.

-   Führen Sie die Bewertung mehrmals um zu bestätigen, dass der metrische Wert nicht durch eine temporäre Datei Systemereignis (beispielsweise einen Cache leeren) erstellt wurde.

-   Beheben von Problemen, die aufgrund der Bewertung auftreten, sodass sie nicht mehr angezeigt werden und alle Warnungen.

-   Minifilter sind oft einen Dienst zugeordnet.

Wenn diese Schritte das Problem nicht lösen, erwägen Sie das Ersetzen des Minifilter Produkts mit einem anderen Programm, das eine ähnliche Funktionalität bietet oder eine andere Version der Minifilter testen.

Anwendungsentwickler möchte, die Ursache des Problems zu erhalten können Sie eine tiefere Analyse, öffnen die Ablaufverfolgung in WPA ausführen. Die Analyseansicht von Minifilter Verzögerungen bei WPA ist ein guter Ausgangspunkt für Tiefe Analyse. Werden mehrere ETL-Dateien, wenn Sie alle drei Bewertung, FileOrg.etl, IELaunch ausführen\_Warm\_1, IELaunch\_Warm\_2, IELaunch\_Warm\_3, IELaunch\_kalt\_1 und mehrere ETL-Dateien für die Boot-Bewertung mit dem Namen FastStartup\_Analysis -\*. Diese ETL-Dateien können von jedem Benutzer verwendet werden, die WPA versteht.

### <a name="a-href-idbkmk-minifiltermetricdelayaminifilter-delay"></a><a href="" id="bkmk-minifiltermetricdelay"></a>Minifilter Verzögerung

Minifilter Verzögerung ist das Maß für die kumulative Dauer der Zeit, die Minifilter. Diese Metrik zeigt, wie viel Zeit durch die Minifilter verwendet wird und wie viel Zeit durch andere Aktivitäten genutzt wird, die während der Bewertung ausgeführt wurde. Große Werte in dieser Metrik können der Benutzer beim Ausführen einer Dateivorgänge schlechter Reaktionsgeschwindigkeit auftreten kann hinweisen.

**Am besten:** Minifilter ISVs haben den größten direkten Einfluss auf diese Metrik die Art und Weise, wie sie die Minifilter implementieren. Endbenutzer und OEMs haben indirekte Einfluss auf diese Metrik basierend auf der Minifilter Produkte, die sie installieren.

**Typische Schlüsselfaktoren Faktoren**

Große Werte in dieser Metrik werden in der Regel durch einen Entwurf für eine weniger effektiv Minifilter verursacht. Für bestimmte können Arbeitslasten (beispielsweise Kopieren), Größe, Anzahl und Typ der Dateien auch diese Metrik beeinflussen. Beispielsweise den Unterschied zwischen einer Mediendatei und eine Textdatei.

**Analyse und Schritte zur Wiederherstellung**

Um sicherzustellen, dass die Qualität der Ergebnisdaten

-   Schließen Sie alle Anwendungen, die im Hintergrund ausgeführt werden.

-   Nachdem die wichtigste Komponente identifiziert wurde, sollten Sie Isolieren von der Auswirkungen durch andere optional Dienste beenden und die Bewertung für den Vergleich erneut ausführen.

-   Stellen Sie sicher, dass das System keine Speicher überlastet ist, bei der Ausführung dieses Assessment.

-   Führen Sie die Bewertung mehrmals um zu bestätigen, dass der metrische Wert nicht durch eine temporäre Datei Systemereignis (beispielsweise einen Cache leeren) erstellt wurde.

-   Beheben von Problemen, die aufgrund der Bewertung auftreten, sodass sie nicht mehr angezeigt werden und alle Warnungen.

-   Suchen Sie nach dem Muster in der oberen verzögert.

Wenn Sie diese Schritte das Problem nicht lösen, erwägen Sie das Ersetzen des Minifilter Produkts mit einem anderen Programm, das eine ähnliche Funktionalität bietet oder für eine andere Version von der Minifilter testen.

Der Versuch, die Ursache des Problems ermitteln Anwendungsentwickler kann eine tiefere Analyse öffnen in das Ablaufverfolgungsprotokoll in WPA ausführen. Die Minisymbolleiste Filter Verzögerungen Analysis-Ansicht ist ein guter Ausgangspunkt für die Analyse tiefer. Werden mehrere ETL-Dateien, wenn Sie alle drei Bewertung, FileOrg.etl, IELaunch ausführen\_Warm\_1, IELaunch\_Warm\_2, IELaunch\_Warm\_3, IELaunch\_kalt\_1 und eine Vielzahl von ETL-Dateien für die Boot-Bewertung mit dem Namen FastStartup\_Analysis -\* diese ETL-Dateien können von jeder Person, die WPA versteht verwendet werden.

### <a name="a-href-idbkmk-minifiltermetricavgcallaaverage-call-length"></a><a href="" id="bkmk-minifiltermetricavgcall"></a>Durchschnittliche Anrufdauer

Diese Metrik ist die durchschnittliche Zeit, die in jeder Rückruf aufgewendet wird. Große Werte in dieser Metrik können wahrnehmbar Verzögerungen angeben, beim Ausführen von Vorgängen Datei. In der die längste Verzögerung Metrik eines bestimmten Problems oder Ursache angeben kann, ist der Durchschnitt als Maßstab für die allgemeine Verhalten der Minifilter an. Jedoch kann nur mit den Mittelwert Extreme wie eine große Anzahl von identische anrufen oder eine sehr große verzögern übersehen verursachen.

**Am besten:** Minifilter ISVs haben den größten direkten Einfluss auf diese Metrik durch die Möglichkeit, dass sie die Minifilter implementieren. Endbenutzer und OEMs haben indirekte Einfluss auf diese Metrik basierend auf der Minifilter Produkte, die sie installieren.

**Typische Schlüsselfaktoren Faktoren**

Große Werte in dieser Metrik können eine falsche Minifilter entwurfsbedingt verursacht werden. Für bestimmte kann Arbeitslasten (Kopie), die Größe der verwendeten Dateien auch diese Metrik beeinflussen.

**Analyse und Schritte zur Wiederherstellung**

Wenn Minifilter Metriken um Regressionen in einer einzelnen Softwarekomponente zu identifizieren, ist die zutreffenden zum Erstellen und vergleichen Sie die Ergebnisse, die aus zwei Versionen derselben Komponente erstellt werden, und suchen Sie nach Regressionen oder um die Ergebnisse aus verschiedenen Anwendungsentwickler zwei ähnlicher Produkte vergleichen.

Durchschnittliche Anrufdauer bietet objektive Kontextinformationen um Perspektive für das in der Metrik Minifilter Verzögerung zurückgegebene Ergebnis zu übernehmen. Beim Vergleichen von Ergebnisse zurück, wenn die Verzögerung Minifilter Metrik erhöht und den Mittelwert nicht erhöht, gibt dann die Anhebung der Minifilter Verzögerung Metrik nicht in der Regel ein Problem an. Wenn trend Minifilter Verzögerung und durchschnittliche Länge der Aufrufen in derselben Richtung, gibt die Anhebung der Minifilter Verzögerung Metrik im Allgemeinen eine Änderung der Leistung.

Um die Ursache für diese Art von Problem ermittelt wird, suchen Sie nach Muster in der oberen verzögert.

Wenn diese Schritte das Problem nicht lösen, erwägen Sie das Ersetzen des Produkts Minifilter mit einem anderen Programm, das eine ähnliche Funktionalität bietet oder für eine andere Version von der Minifilter testen.

### <a name="a-href-idbkmk-minifiltermetriccallbackaminifilter-callbacks"></a><a href="" id="bkmk-minifiltermetriccallback"></a>Minifilter Rückrufe

Diese Metrik ist die Anzahl der Minifilter bezeichnet wird, durch das Betriebssystem oder andere Anwendungen und Dienste, die auf dem System ausgeführt werden. Sie können einen Drilldown auf diese Nummer für die verschiedenen Typen von Rückrufen finden Sie unter.

**Am besten:** Endbenutzer und OEMs haben indirekte Einfluss auf diese Metrik basierend auf der Minifilter Produkte, die sie installieren und die Möglichkeit, Dienste und Anwendungen, die Einfluss auf diese Metrik zu deinstallieren.

Es gibt keine Wiederherstellungsschritte wie diese Metrik nur die Anwendungen abhängig ist, die auf dem System installiert sind.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Ein-/ausschalten Übergang-Leistung](onoff-transition-performance.md)

 

 







