---
title: "Schrittweise Anleitung für Windows-Assessment-Konsole"
description: "Schrittweise Anleitung für Windows-Assessment-Konsole"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
Search.SourceType: Video
ms.assetid: 9541de45-d6ad-4a5f-9441-01fb1d8f9b2f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 8f9b07f7e284e1abaa9f01297242173d54d2754c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-console-step-by-step-guide"></a>Schrittweise Anleitung für Windows-Assessment-Konsole


Dieses Handbuch enthält schrittweise Anleitungen für das Windows Assessment Toolkit installieren und Verwenden der Windows-Konsole Assessment bewerten die Qualität von einem lokalen Computer, und überprüfen Sie die Ergebnisse an.

Die erste Bewertung in diesem Handbuch verwendeten hilft Ihnen, die Leistung Qualität für die neue Windows-Benutzeroberfläche zu überprüfen. Klicken Sie dann erstellen Sie einen Auftrag mithilfe einer Vorlage mit zwei Treiber-Analysen, die Treiber für die gezielte Hardware und Windows-Zertifizierung zu überprüfen. Anschließend erstellen Sie eine dritte Bewertung, die den ersten Boot Eindruck ausgewertet wird. In der letzten Übung in diesem Handbuch einen Auftrag zu packen und auf einem anderen Computer ausführen, damit Sie die Ergebnisse der beiden Aufträge vergleichen können.

## <a name="objectives"></a>Ziele


Die Übungen in diesem Handbuch können Sie Folgendes:

-   Erfahren Sie, wie die Bewertung zu verwenden, die im Assessment Toolkit enthalten sind.

-   Erfahren Sie, wie in der Windows-Assessment-Konsole navigieren.

In diesem Thema:

-   [Erforderliche Komponenten](#wac-sxs-prereq)

-   [Übung 1: Ausführen ein Auftrags mit empfohlene Einstellungen](#wac-sxs-ex1)

-   [Übung 2: Erstellen eines neuen Auftrags mit benutzerdefinierten Einstellungen](#wac-sxs-ex2)

-   [Übung 3: Führen Sie einen Auftrag auf einem anderen Computer, und vergleichen Sie die Ergebnisse](#wac-sxs-ex3)

Geschätzte Zeit bis zum Abschließen späteren: **60 Minuten**.

Jede Übung enthält außerdem eine Demo 3 – 5 Minuten.

## <a name="a-href-idwac-sxs-prereqaprerequisites"></a><a href="" id="wac-sxs-prereq"></a>Erforderliche Komponenten


Um die in diesem Handbuch beschriebenen Schritte ausgeführt haben, müssen Sie das Windows Assessment Toolkit aus dem Windows Assessment and Deployment Kit (Windows ADK) auf einem Testcomputer installieren, auf denen Windows 8 oder Windows 10 ausgeführt wird.

### <a name="install-the-windows-assessment-toolkit"></a>Installieren Sie das Windows-Assessment-Toolkit

1.  Doppelklicken Sie auf das Windows ADK-Installationsprogramm, ADKSetup.exe.

2.  Stellen Sie sicher, dass die Option **dem Assessment and Deployment Kit auf diesem Computer installieren** ausgewählt ist, und klicken Sie dann auf **Weiter**.

3.  Akzeptieren Sie den Lizenzvertrag.

4.  Für diese Übungen müssen Sie nur das **Assessment Toolkit** und das **Windows Performance Toolkit**installieren. Stellen Sie sicher, dass sie ausgewählt werden.

5.  Klicken Sie auf **Installieren**.

    Wenn das Fenster **Benutzerkontensteuerung** geöffnet wird, klicken Sie auf **Ja**.

Wenn die Installation abgeschlossen ist, kann die Windows-Assessment-Konsole im Menü **Start** geöffnet werden.

## <a name="a-href-idwac-sxs-ex1aexercise-1-run-a-job-with-recommended-settings"></a><a href="" id="wac-sxs-ex1"></a>Übung 1: Ausführen ein Auftrags mit empfohlene Einstellungen


Die Windows-Konsole Assessment wird verwendet, um entdecken, erstellen, bearbeiten und Anzeigen der Ergebnisse, die ein Auftrag erzeugt. Ein Auftrag ist eine Auflistung von mindestens Analysen und deren Einstellungen, die als Gruppe auf einem einzelnen Computer ausgeführt werden. Wenn die Windows-Assessment-Konsole geöffnet wird, bietet die Registerkarte **Start** einfachen Zugriff auf einige vordefinierte Aufträge und einzelne Analysen, die Sie sofort ohne alle Konfigurationsschritte ausführen können. Wenn Sie einen neuen Auftrag erstellen, sind darüber hinaus vordefinierte Aufträge als Vorlagen verfügbar. Ein Auftrag, der aus einer Vorlage erstellt wird, kann auch ohne Änderung oder zusätzliche Konfigurationsschritte ausgeführt werden.

Es gibt zwei Methoden, um einen Auftrag mit empfohlenen Einstellungen ausgeführt werden:

-   [Führen Sie eine einzelne Bewertung mit empfohlenen Einstellungen](#bkmk-runsingle)

-   [Verwenden Sie eine Vorlage mit empfohlenen Einstellungen](#bkmk-usetemplate)

### <a name="a-href-idbkmk-runsinglearun-a-single-assessment-with-recommended-settings"></a><a href="" id="bkmk-runsingle"></a>Führen Sie eine einzelne Bewertung mit empfohlenen Einstellungen

Ausführen einer Bewertung mit den empfohlenen Einstellungen ist schnell und einfach. Von Microsoft, um sicherzustellen, dass die Ergebnisse über verschiedene Computerkonfigurationen oder über einen Zeitraum auf demselben Computer verglichen werden können, werden die Einstellungen definiert. In dieser Übung führen Sie eine einzelne Bewertung mithilfe des vordefinierten Einstellungen empfohlen.

Sehen Sie sich die video Demo:

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/3f889614-b65c-4066-84ea-c523fdaabc39/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

**Zum Ausführen einer einzelnen Assessment mit den empfohlenen Einstellungen**

1.  Klicken Sie auf **Start**, Typ "Assessment Konsole", und klicken Sie dann auf **Windows-Assessment-Konsole**.

    Die Windows-Konsole Assessment wird geöffnet.

2.  Klicken Sie auf **der Startseite** auf **Einzelne Bewertung ausführen**. Klicken Sie im Detailbereich auf der rechten Seite klicken Sie auf der **Benutzeroberfläche von Windows Performance** -Bewertung, und klicken Sie dann in der unteren rechten Ecke auf **Ausführen**.

    Wenn das Fenster Benutzerkontensteuerung geöffnet wird, klicken Sie auf **Ja**.

3.  Vor dem Start des Auftrags überprüft des Auftrags der Computerkonfiguration, um sicherzustellen, dass die Bewertung erfolgreich ausgeführt werden kann. Der Auftrag generiert Fehlermeldungen, Warnungen und informative Nachrichten basierend auf der Computerkonfiguration als auch die Anforderungen der Bewertung. Die Benachrichtigungen werden im Dialogfeld Assessment Startprogrammdienst wie folgt angezeigt:

    -   Fehler blockieren den Anfang des Auftrags. Wenn der Auftrag ein Problem mit der Konfiguration, die behoben werden muss, bevor der Auftrag fortgesetzt werden kann oder Computerhardware findet, werden Fehlermeldungen angezeigt. Die Schaltfläche **Start** ist nicht verfügbar im Dialogfeld auf, wenn eine Fehlermeldung angezeigt wird. Nachdem Sie blockierenden Fehler behoben haben, können Sie **zu aktualisieren** , um erneut überprüfen Sie den Computer und weiterhin den Auftrag klicken.

    -   Warnungen angezeigt werden, wenn der Auftrag ein Problem gefunden, die Ausführung des Auftrags wird nicht blockiert werden, aber die Ergebnisse beeinträchtigen. Überprüfen Sie die Warnungen und Aktionen durchführen, oder ignorieren Sie die Warnung, und klicken Sie auf **Start**.

    -   Informative Nachrichten bieten zusätzliche Anweisungen oder Informationen zu Aktionen, die ausgeführt wird, wenn der Auftrag ausgeführt wird. Nachdem Sie die Informationen gelesen haben, klicken Sie auf **Starten** , um das Projekt zu beginnen.

    **Wichtige**  
    Interagieren Sie sich nicht mit dem Computer, während der Ausführung des Auftrags. Aktivitäten werden angezeigt, während der Ausführung des Auftrags. Wenn der Auftrag abgeschlossen ist, werden in der Windows-Konsole zur Bewertung der Ergebnisse angezeigt.

     

Die Ergebnisse dieser Beurteilung zeigen Rendering und erhöhen die Reaktionsgeschwindigkeit Metriken. Suche Leistungsmetriken enthalten die erforderliche Zeit für verschiedene Aspekte der Suche abgeschlossen und angezeigt werden. Leistungsmetriken für den Umstieg von zählen Verzögerungen, hohe Framerate und Probleme aufgeführt. Reaktionsfähigkeit Ergebnisse werden in Millisekunden gemessen. Niedrige Zahlen bedeuten, dass der Computer schneller und besser ist. Für das Rendern enthalten die Ergebnisse die Framerate und die Anzahl der Fehler, die auftreten. Eine gute benutzererfahrung verfügt über hohe hohe Framerate sowie einige Probleme.

Probleme und Empfehlungen basieren auf diese Metriken. Klicken Sie auf **Probleme**, und erweitern Sie die Informationen, die im **Detailbereich auf der rechten Seite zu verstehen, das Problem und die Empfehlungen** angezeigt wird. In den meisten Fällen können Sie auch den Link **WPA eingehenderen Analysen** , um ein Problem weiter zu analysieren klicken.

### <a name="a-href-idbkmk-usetemplateause-a-template-with-recommended-settings"></a><a href="" id="bkmk-usetemplate"></a>Verwenden Sie eine Vorlage mit empfohlenen Einstellungen

Die Registerkarte **Start** bietet einfachen Zugriff auf einige vordefinierte Aufträge, die Sie sofort, ohne alle Konfigurationsschritte ausführen können und zusätzliche vordefinierte Aufträge sind als Vorlagen verfügbar, wenn Sie einen neuen Auftrag erstellen. In dieser Übung erstellen Sie einen neuen Auftrag mithilfe der Vorlage Fertigung und Bereitstellung.

Schauen Sie sich die video Demo:

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/99837a2d-f949-4a80-8250-53898ea4d57d/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

**Um eine andere Vorlage mit empfohlene Einstellungen verwenden**

1.  Wenn die Windows-Assessment-Konsole nicht geöffnet ist, klicken Sie auf **Start**, Typ "Assessment Konsole", und klicken Sie dann auf **Windows-Assessment-Konsole**.

2.  Klicken Sie in der Windows-Assessment-Konsole auf **Optionen**, und klicken Sie dann auf **Neuer Auftrag**.

3.  Wählen Sie im Dialogfeld **Neuer Auftrag** **erstellen einen Auftrag aus einer Vorlage**aus.

4.  Wählen Sie aus der Liste der verfügbaren Vorlagen **Fertigung und Bereitstellung**, und klicken Sie dann auf **OK**.

5.  In der neuen Registerkarte in der Windows-Assessment-Konsole sind die Einstellungen eines Auftrags für standardmäßig aktiviert. Ändern Sie den Namen in **Fertigung und Bereitstellung**, geben Sie als Beschreibung ein **identifizieren Probleme mit Treibern und beim ersten Starten** . Hinzufügen von Text in das Feld **Notizen** zur einfacheren des Auftrags und die Ergebnisse zu identifizieren. Die folgenden Einstellungen stehen ebenfalls zur Verfügung, aber ändern Sie sie nicht für jetzt.

    -   **Beenden Sie diesen Auftrag, wenn ein Fehler auftritt**. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Aktivieren Sie dieses Kontrollkästchen So beenden Sie den Auftrag nicht abgeschlossen werden, wenn ein Fehler auftritt. Diese Einstellung ist nützlich, wenn ein Auftrags für einen längeren Zeitraum ausgeführt wird. Wenn ein Fehler auftritt, und dieses Kontrollkästchen aktiviert ist, kann diese Einstellung verhindert, dass lange Wartezeiten. Kürzere Aufträge ist es im Allgemeinen nicht notwendig, den Auftrag zu beenden, wenn ein Fehler auftritt.

    -   **Alle von Bewertungen erstellte temporäre Dateien beibehalten**. In der Standardeinstellung ist dieses Kontrollkästchen deaktiviert. Aktivieren Sie dieses Kontrollkästchen, wenn Sie die Dateien später zu überprüfen, die die Bewertung erstellt, während der Ausführung der Bewertung möchten.

6.  Klicken Sie auf die Bewertung **Treiber Überprüfung** , um die Bewertung Einstellungen finden Sie unter. Stellen Sie sicher, dass die **Empfohlene Einstellungen verwenden** aktiviert ist.

    Assessment Einstellungen sind für jeden Bewertung. Die anderen beiden Bewertung in diesen Auftrag, den **Treiber Zertifizierung Prevalidation** Bewertung und die Bewertung **Leistung zuerst gestartet** haben nicht konfigurierbar Assessment-Einstellungen.

7.  Um diesen Auftrag ausgeführt werden soll, klicken Sie in der unteren rechten Ecke auf **Ausführen** .

    Wenn das Fenster **Benutzerkontensteuerung** geöffnet wird, klicken Sie auf **Ja**.

8.  Wenn das Microsoft Assessment-Start-Fenster angezeigt wird, klicken Sie auf **Details** , um den Status des Auftrags zu überwachen.

    **Wichtige**  
    Es ist kein Problem zum Überwachen des Auftrags im Fenster Assessment Launcher Fortschritt, aber interagieren nicht mit dem Computer auf andere Weise, während der Ausführung des Auftrags. Sie können auch finden Sie unter einem Konsolenfenster angezeigt werden, während der Ausführung des Auftrags.

     

    Führen Sie die Bewertung in der Reihenfolge aus, die sie in den Auftrag aufgeführt sind. Zuerst die Treiber Überprüfung Bewertung überprüft, ob Ihr Computer die korrekte Liste der Treiber enthält. Klicken Sie dann überprüft die Treiber Zertifizierung Prevalidation Bewertung installierten Treiber für das Windows-Zertifizierungsprogramm ausgestellt werden kann. Zum Ausführen das letzte Assessment ist der erste Start Leistung zur Bewertung, die untersucht die Event Trace Log (ETL)-Dateien erstellt, die während der Windows-Setup und OOBE zur Erkennung von Problemen, die die Zeit betreffen, die zum Starten von Windows und zum Anzeigen der Startseite beim ersten Start der Endbenutzer Starten des Computers erforderlich ist. Wenn alle drei Bewertung abgeschlossen sind, öffnen Sie die Ergebnisse in der Konsole zur Bewertung.

9.  Die **Ergebnisse anzeigen** -Seite enthält eine Tabelle mit ausführen, zur Bewertung Ergebnisse Tabellen, einem Detailbereich rechts und einem metrischen Diagramm am oberen Rand der Seite. Die folgende Informationen helfen Ihnen die finden weitere Informationen auf der Seite **Ergebnisse anzeigen** .

    -   Klicken Sie auf **Select Zeilen** um ausführen Informationen wie **Dateipfad**, hinzuzufügen, die den Pfad der Datei mit den Suchergebnissen angezeigt wird, den Sie überprüfen, in der Tabellenüberschrift **Informationen ausführen** .

    -   Klicken Sie in der Ergebnistabelle **Treiber Überprüfung** auf den Doppelpfeil (&gt;) neben **Probleme** , die Liste der auf dem Computer gefundenen Probleme zu erweitern. Befinden sich viele Probleme mit der rechten Maustaste **Probleme**auf **Gruppieren nach**, und wählen Sie eine Kategorie zum Gruppieren von Problemen.

    -   Klicken Sie in der Ergebnistabelle **Treiber Zertifizierung Prevalidation** auf den Doppelpfeil neben der jeweiligen Problems, um die Liste zu erweitern. Klicken Sie auf eine der Probleme in der Liste, um weitere Informationen im Detailbereich anzuzeigen. Im Detailbereich erweitern Sie ein Problem und überprüfen Sie die Empfehlungen und Links für Weitere Informationen.

    -   Klicken Sie in der Ergebnistabelle **zuerst gestartet Leistung** auf den Doppelpfeil neben **Zeit beginnen** , um zusätzliche metrische Daten generiert, die für die Bewertung finden Sie unter.

    -   Klicken Sie in der Ergebnistabelle **zuerst gestartet Leistung** auf **Probleme** , um alle Probleme finden Sie unter gefunden, indem der Bewertung im Detailbereich auf der rechten Seite angezeigt. Erweitern Sie eine der Probleme im Detailbereich Recommendations und Links zu weiteren Informationen und zusätzliche Analyse angezeigt.

### <a name="next-steps"></a>Nächste Schritte

Im nächsten Schritt erstellen Sie in Übung 2 einen angepassten Auftrag, der enthält mehrere Analysen und Bewertung Einstellungen angepasst.

## <a name="a-href-idwac-sxs-ex2aexercise-2-create-a-new-job-with-custom-settings"></a><a href="" id="wac-sxs-ex2"></a>Übung 2: Erstellen eines neuen Auftrags mit benutzerdefinierten Einstellungen


Windows-Konsole Assessment können beim Erstellen eines neuen Auftrags eigener Entwurf. Dadurch können Sie zum Definieren der Bewertung, die Sie ausführen möchten und die Metriken, die Sie überprüfen möchten. Sie können durch Auswahl einen Auftragstyp im Dialogfeld Neuer Auftrag oder durch Auswahl einer erfolgreichen oder einzelne Bewertung auf der Startseite starten. In beiden Fällen können Sie auswählen, welche Bewertung des Auftrags enthalten sind, und Sie können die Einstellungen für Ihre Bedürfnisse ändern. In dieser Übung erstellen einen neuen Auftrag, Bewertung hinzufügen und ändern Sie die Bewertung.

Sehen Sie sich die video Demo:

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/a8e78967-8469-4646-9a69-bab2a033d1df/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

**So erstellen Sie eine neue benutzerdefinierte Auftrag**

1.  Wenn die Windows-Assessment-Konsole nicht geöffnet ist, klicken Sie auf **Start**, Typ "Assessment Konsole", und klicken Sie dann auf **Windows-Assessment-Konsole**.

2.  Klicken Sie auf der Registerkarte Start Doppelklicken Sie auf **Such- und Windows-UI-Erfahrung** , um das Projekt zu öffnen.

3.  Klicken Sie auf **Optionen**, und klicken Sie dann auf **Speichern und Windows Benutzeroberfläche Erfahrung als**.

4.  Navigieren Sie im Dialogfeld **Auftrag speichern** die \\Windows Assessment-Konsole\\Aufträge Ordner, benennen Sie den Auftrag **Meine durchsuchen Erfahrung Auftrag**, und klicken Sie dann auf **Speichern**.

    **Wichtige**  
    Der Standardspeicherort für das Speichern von Aufträgen ist "UserProfile" %\\Dokumente\\Windows Assessment Konsole\\Aufträge. Wenn Sie einen Auftrag an diesem Speicherort speichern, wird der Auftrag auf der Windows-Assessment-Konsole Homepage für den einfachen Zugriff angezeigt.

     

5.  **Übersicht**zum Ändern der **Beschreibung** auf **Measure Browserumgebung**, klicken Sie in der Windows-Assessment-Konsole, klicken Sie unter **Einstellungen eines Auftrags für**die neue Registerkarte auf und ändern Sie die **Notizen** in **Measure Browserumgebung und Auswirkungen auf die der Treiber Minifilter**.

6.  Bewegen Sie unter **Bewertung**den Mauszeiger über die **Windows-Benutzeroberfläche Leistung** , und klicken Sie dann auf das rote **X** , um die Bewertung zu entfernen. Führen Sie dieselben Schritte für die **Minifilter Diagnose: Internet Explorer** Bewertung.

7.  Wählen Sie die **Leistung von Internet Explorer zum Starten des** Bewertung die Bewertung Einstellungen auf der rechten Seite angezeigt.

8.  Klicken Sie unter **Einstellungen**deaktivieren Sie das Kontrollkästchen **Use empfohlene Einstellungen** und **Diagnose Minifilter-Modus aktivieren** das Kontrollkästchen.

    Diese Einstellung identifiziert Leistungsproblemen mit Minifilter Treiber beim Start von Internet Explorer.

9.  Wählen Sie die **Browser Internet Explorer-Leistung** Bewertung die Bewertung Einstellungen auf der rechten Seite angezeigt.

10. Klicken Sie unter **Einstellungen**deaktivieren Sie das Kontrollkästchen **Verwendung empfohlen Einstellungen** , und ändern Sie der **Internet Explorer-Ansicht** in **Internet Explorer auf dem Desktop**.

    Diese Einstellung können Sie den Browsen InternetExplorer-Leistung bewerten, wenn es ausgeführt wird, auf dem Desktop anstelle des in der neuen Windows-Benutzeroberfläche.

11. Klicken Sie in der unteren rechten Ecke auf **Ausführen** .

    Wenn das Fenster **Benutzerkontensteuerung** geöffnet wird, klicken Sie auf **Ja**.

12. Vor dem Start des Auftrags überprüft des Auftrags der Computerkonfiguration, um sicherzustellen, dass die Bewertung erfolgreich ausgeführt werden können. Der Auftrag generiert Fehlermeldungen, Warnungen und informative Nachrichten basierend auf der Konfiguration des Computers. Die Benachrichtigungen werden im Dialogfeld Assessment Startprogrammdienst angezeigt. Die drei Typen von Nachrichten umfassen:

    1.  Fehler blockieren den Anfang des Auftrags. Wenn der Auftrag ein Problem mit der Konfiguration, die behoben werden muss, bevor der Auftrag fortgesetzt werden kann oder Computerhardware findet, werden Fehlermeldungen angezeigt. Die Schaltfläche **Start** ist nicht verfügbar im Dialogfeld auf, wenn eine Fehlermeldung angezeigt wird.

    2.  Warnungen angezeigt werden, wenn der Auftrag ein Problem gefunden, die Ausführung des Auftrags wird nicht blockiert werden, aber die Ergebnisse beeinträchtigen. Sie können die Warnungen überprüfen, beheben Sie Probleme, und klicken Sie dann auf **Aktualisieren**, oder die Warnungen ignorieren und klicken Sie dann auf **Starten**.

    3.  Informative Nachrichten bieten zusätzliche Anweisungen oder Informationen zu Aktionen, die ausgeführt wird, wenn der Auftrag ausgeführt wird. Nachdem Sie die Informationen gelesen haben, klicken Sie auf **Starten** , um das Projekt zu beginnen.

    Klicken Sie auf den Doppelpfeil, um zusätzliche Informationen zu jeder Nachricht anzuzeigen, die in das Microsoft Assessment Startprogramm-Fenster angezeigt wird.

13. Im nächste Dialogfeld dient. Klicken Sie nach Überprüfung der Informationen auf **Starten** .

    **Wichtige**  
    Führen Sie nicht interagieren Sie mit Ihrem Computer während der Ausführung des Auftrags. Internet Explorer-Aktivität möglicherweise während der Ausführung des Auftrags auf dem Desktop angezeigt wird. Wenn der Auftrag abgeschlossen ist, werden in der Windows-Konsole zur Bewertung der Ergebnisse angezeigt.

     

### <a name="next-steps"></a>Nächste Schritte

In Übung 3 Packen Sie im nächsten Schritt einen Auftrag und auf einem USB-Laufwerk speichern, damit Sie es auf einem anderen Computer ausführen und die Ergebnisse verglichen werden können.

## <a name="a-href-idwac-sxs-ex3aexercise-3-run-a-job-on-another-computer-and-compare-the-results"></a><a href="" id="wac-sxs-ex3"></a>Übung 3: Führen Sie einen Auftrag auf einem anderen Computer, und vergleichen Sie die Ergebnisse


Wenn Sie einen Auftrag zu Sie auf einem anderen Computer ausführen möchten erstellen, müssen Sie keinen das Toolkit zur Bewertung auf diesem Computer dazu installiert. Windows-Assessment-Konsole bietet die Möglichkeit zu dieser Auftrag Paket zusammenzufassen, sodass es umfasst alle erforderlichen Dateien und Tools, die zum Ausführen des Auftrags auf einem anderen Computer erforderlich sind. In dieser Übung Verpacken einen Auftrag, es auf einem anderen Computer ausführen und dann die Ergebnisse vergleichen.

Sehen Sie sich die video Demo:

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/5a58137e-3afb-4e54-bb14-eaaf56bb44f6/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

**Wichtige**  
Sie sollten Übung 1 abschließen, bevor Sie fortfahren können.

Dieser Schritt erfordert eine austauschbare USB flash-Laufwerk zum Speichern des Auftrags und zum Ausführen des Auftrags auf einem separaten Computer.

 

**Schritt 1: Packen Sie den Auftrag**

1.  Wählen Sie in der Windows-Konsole zur Bewertung der Registerkarte **Fertigung und Bereitstellung** . Wenn die Registerkarte nicht geöffnet ist, klicken Sie auf **der Startseite** , und doppelklicken Sie dann auf den Auftrag, um ihn zu öffnen.

2.  Klicken Sie auf **Paket**.

3.  Geben Sie im Dialogfeld **Paket einen Auftrag zum Ausführen auf einem anderen Computer** Notizen, mit die Hilfe Sie diesen Auftrag zu identifizieren, wenn Sie die Ergebnisse zu öffnen und anzeigen, wie **Manufacturing gepackt und Bereitstellungsauftrag**auswählen.

4.  Geben Sie im Feld **Pfad für das Paket** den Speicherort, in der Sie das Paket Auftrag speichern möchten. In dieser Übung sollte der Speicherort auf einem Wechselmedium sein, wie ein USB-Laufwerk.

5.  Geben Sie im Feld **Pfad** den Speicherort, in der Sie die Ergebnisse speichern möchten. Standardmäßig ist dies der relative Pfad des ein. \\Ergebnisordner am selben Speicherort, in dem der Auftrag ausgeführt wird.

6.  Klicken Sie auf **OK**.

7.  Wenn der Auftrag verpackt wurde, wird der Speicherort des Auftrags geöffnet. Das USB-Laufwerk ausschließen.

**Schritt 2: Ausführen des Auftrags gepackte auf einem anderen computer**

1.  Übernehmen Sie das USB-Laufwerk, das den gepackten Auftrag an den Computer enthält, in dem der Auftrag ausgeführt werden soll.

2.  Öffnen Sie den Ordner, und doppelklicken Sie auf die Datei RunJob.cmd.

3.  Klicken Sie im **Benutzerkontensteuerung**auf **Ja**.

4.  Klicken Sie im Fenster Assessment Launcher fügen Sie ausführen Hinweise zum Identifizieren des Computers, der der Auftrag ausgeführt wird, klicken Sie auf hinzu.

5.  Lassen Sie im Textfeld **Pfad** den Standardspeicherort zum Speichern der Ergebnisse auf die USB-Laufwerk ein.

6.  Klicken Sie auf **Auftrag auf diesem Computer ausführen**.

7.  Wenn der Auftrag abgeschlossen ist, werden die Ergebnisse in der Windows-Assessment-Konsole angezeigt. Schließen Sie die Windows-Assessment-Konsole und entfernen Sie das USB-Gerät vom Computer.

Wenn der Auftrag erfolgreich abgeschlossen ist, können Sie die Ergebnisse der USB-Laufwerk auf einen anderen Computer übernehmen und darauf zugreifen zu Vergleichszwecken.

**Schritt 3: Vergleichen der Ergebnisse**

1.  Fügen Sie das USB-Gerät an den Computer, auf dem die Windows-Assessment-Konsole installiert ist.

2.  Klicken Sie in der Windows-Assessment-Konsole auf **Optionen**, und klicken Sie dann auf **Importergebnisse**.

3.  Klicken Sie im Dialogfeld **Importergebnisse** auf **Durchsuchen** , um die Ergebnisse zu suchen, die auf das USB-Flashlaufwerk gespeichert.

4.  Suchen nach dem Ordner, in dem Sie den Auftrag für das USB-Gerät verpackt, klicken Sie auf den Ergebnisordner, und klicken Sie dann auf **Ordner auswählen**. Der Pfad des Ordners in das **Importieren von** im Dialogfeld **Importergebnisse** wird angezeigt.

5.  Klicken Sie auf **Weiter**. Die Windows-Konsole Assessment importiert die ausgewählten Ergebnisse in die Standardbibliothek Ergebnisse auf dem lokalen Computer.

6.  Wenn die Ergebnisse für den vorherigen Auftrag **Fertigung und Bereitstellung** nicht geöffnet sind, wählen Sie den Auftrag aus, und klicken Sie dann auf **Ergebnisse anzeigen**.

7.  Klicken Sie auf der Seite **Ergebnisse anzeigen** in der oberen rechten Ecke auf **Ergebnisse hinzufügen**.

8.  Wählen Sie die Ergebnisse, die mit den gepackte Auftrag aus, und klicken Sie dann auf **Hinzufügen** , um diese in eine nebeneinander Ansicht mit den Ergebnissen zu öffnen, die bereits geöffnet werden.

9.  Sie können die Ergebnisse, um nur die Unterschiede zwischen den Ergebnisse anzeigen filtern. Klicken Sie auf **Zeilen auswählen** , und klicken Sie dann auf **Unterschiede anzeigen**.

Beim Vergleichen von zwei oder mehr Ergebnisse sind die besten Metriken ggf. blau hervorgehoben.

## <a name="summary"></a>Zusammenfassung


In diesem Leitfaden Sie Aufträge mit den empfohlenen Einstellungen ausgeführt haben, und Sie einen benutzerdefinierten Auftrag erstellt. Darüber hinaus einen Auftrag gepackt und Ausführung auf einem anderen Computer und die Ergebnisse verglichen. Dies sind die grundlegende Szenarios, die Ihnen das Verständnis von wie die Bewertung zu verwenden, die bereitgestellt werden und wie die Windows® Assessment-Konsole navigieren bieten.

### <a name="more-things-to-try"></a>Weitere Punkte zu testen

Führen Sie zusätzliche Aufträge selbst. Beispielsweise wird Folgendes empfohlen:

-   [Speicherbedarf](memory-footprint.md). Diese Bewertung hilft Ihnen, eine Basisinstallation gegen eine Installation von Windows vergleichen, die mit zusätzliche Software geändert wurden. Die Bewertung identifiziert die bestimmten Komponenten, die physischen System Speicherbedarf, wie Treiber, Add-In-Programme, Softwarepakete und Antivirenprogramme beeinflussen.

-   [Basislinienergebnisse erstellen](create-baseline-results-for-comparing-windows-images.md). In diesem Thema führt Sie durch die Schritte, die erforderlich sind, um eine geplante Installation von Windows für eine Installation vergleichen, die mit zusätzlicher Software, die geändert wurde.

-   [Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md). Diesen Auftrag bietet eine automatisierte Möglichkeit bewerten Energie-Effizienz und die Akkulaufzeit eines tragbaren Computers zu messen.

-   [Erstellen und Ausführen einer Energie Effizienz Auftrag](create-and-run-an-energy-efficiency-job.md). Beschreibt das Erstellen und Ausführen eines Auftrags, bei dem die Batterie Leben und weniger Energie Effizienz eines tragbaren Computers analysiert.

-   [Ein-/ausschalten Übergang Leistung](onoff-transition-performance.md). Diese Bewertung Hilfe, die Sie die Dauer zwischen Übergänge von anderen Computer Zustände, z. B. Boot messen, aus dem Standbymodus fortsetzen und Ruhezustand. Erweiterte Problem Analysis steht auf Probleme, die gefunden werden, sodass Probleme zu der Quelle mit Event Trace Logging und Windows® Performance Analyzer (WPA) zurückverfolgt werden können.

## <a name="related-topics"></a>Verwandte Themen


[Bewertung](assessments.md)

 

 







