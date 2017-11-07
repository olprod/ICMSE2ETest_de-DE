---
title: "Schrittweise Anleitung für Windows Assessment Services"
description: "Schrittweise Anleitung für Windows Assessment Services"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 42b89aeb-e92b-4571-a609-87f22941193c
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 22198ee21f73bb12411de85af7a3f76aa375f6e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-services-step-by-step-guide"></a>Schrittweise Anleitung für Windows Assessment Services


Windows-Assessment-Services ist ein Testframework, die verwendet wird, um Maßangaben Qualität, beispielsweise die Leistung, Zuverlässigkeit und Funktionalität, die in einer laborumgebung auf mehreren Computern automatisieren. Das Windows-Assessment-Services - Client (Windows ASC) ist die grafische Benutzeroberfläche, die verwendet wird, zum Verwalten von Einstellungen und Objekte, wie die Laborcomputer Test, welche Bilder auf den Computern angewendet werden soll und welche Bewertung zum Testen der Computer verwendet werden soll. Windows ASC wird auch verwendet, um den Status einer laufenden Auftrags zu überwachen und zum Anzeigen der Ergebnisse, die erstellt wurden. Informationen zum Computer oder Bild Qualität bewerten, führt Windows Assessment Services Framework zum Testen der Folgendes aus:

-   Automatisiert Bereitstellung mit Bild zum Testen von Computern mithilfe von Windows Deployment Services (WDS) und einer angepassten Abbilds Windows Vorinstallation Environment (Windows PE)

-   Automatisiert das Ausführen von Analysen mithilfe von Windows-Remoteverwaltung (WinRM)

-   Automatisiert die Auflistung der Ergebnisse von Testcomputern mithilfe der WinRM Ergebnisse an den Windows-Assessment-Services-Server zu kopieren.

In der folgenden Abbildung werden die Topologie Windows Assessment Services beschrieben:

![Topologie für Windows Assessment services](images/dep-was-sxs-topology.jpg)

Dieses Handbuch enthält schrittweise Anleitungen für das Windows Assessment Toolkit installieren, Konfigurieren von Windows Assessment Services und die Windows-ASC, Bewerten von mehreren Computern und überprüfen Sie dann die Ergebnisse an.

In diesem Thema:

-   [Erforderliche Komponenten](#bkmk-wastr-prereqs)

-   [Schritt 1: Installation und Konfiguration](#bkmk-wastr-step1)

-   [Schritt 2: Erstellen eines Projekts](#bkmk-wastr-step3)

-   [Schritt 3: Erstellen eines Auftrags](#bkmk-wastr-step4)

-   [Schritt 4: Ausführen des Auftrags](#bkmk-wastr-step5)

-   [Schritt 5: Überprüfen Sie die Ergebnisse](#bkmk-wastr-step6)

-   [Abschluss](#bkmk-wastr-conclude)

## <a name="a-href-idbkmk-wastr-prereqsaprequisites"></a><a href="" id="bkmk-wastr-prereqs"></a>Prequisites


Um die in diesem Handbuch beschriebenen Schritte erfolgreich abzuschließen, vergewissern Sie sich, dass Sie über Folgendes verfügen:

-   Windows Server 2012 mit den folgenden:

    -   Empfohlen: Netzwerkkarte, 1 GB

    -   Empfohlen: Veränderbar Speicherplatz für Ablaufverfolgungsdateien, Ergebnisse und Bilder

        **Hinweis**  
        In diesem Szenario können Sie Windows Server 2008 R2 verwenden. Windows Server 2008 R2 unterstützt jedoch nicht dynamische Treiber Provisioning (DDP) wie in Schritt 1 und Schritt 2, in dem es verwendet wird, zum Hinzufügen von NIC-Treiber und importieren zusätzliche Treiber in Driver Store beschrieben werden. Sie können dieses Problem umgehen mithilfe von Deployment Image Servicing and Management (DISM) Treiber zu Ihrem Windows-Abbild hinzufügen. Weitere Informationen finden Sie unter [Deployment Image Servicing and Management (DISM) Technical Reference](http://go.microsoft.com/fwlink/?LinkId=214571).

         

-   Einen oder mehrere Testcomputer, die über Folgendes verfügen:

    -   USB-Boot-Unterstützung

    -   Netzwerk (PXE) Boot-Unterstützung

    -   Netzwerkkarten-Treiber

    **Hinweis**  
    Der Testcomputer kann bare-Metal Computer (kein Betriebssystem installiert) oder Computer, auf denen Windows 8 ausgeführt werden.

     

-   Ein Windows 8-Bild (Wenn Sie bare-Metal-Computern verwenden)

-   512 MB USB flash-Laufwerk

-   Alle Computer müssen sich im gleichen Subnetz sein.

-   Ein DHCP-Server zum Zuweisen von IP-Adressen auf Testcomputer

Weitere Informationen zu den Systemanforderungen finden Sie unter [Installieren von Windows Assessment Services](installing-windows-assessment-services-wastechref.md).

## <a name="a-href-idbkmk-wastr-step1astep-1-installation-and-configuration"></a><a href="" id="bkmk-wastr-step1"></a>Schritt 1: Installation und Konfiguration


Sie müssen auf einem Servercomputer Windows Assessment Services installieren, die Windows ASC auch auf dem Server installiert. Sie können auch eine eigenständige Version von Windows ASC auf einem Clientcomputer installieren. Weitere Informationen zum Installieren von Windows Assessment Services und Windows ASC finden Sie unter [Installieren von Windows Assessment Services](installing-windows-assessment-services-wastechref.md).

Setup und Konfiguration umfasst die folgenden Schritte aus:

-   Beim Initialisieren des Windows-Assessment-Dienste

-   Konfigurieren des Zugriffs auf Symbole

-   Hinzufügen von NIC-Treiber zu Windows PE-Abbild, die Dienste für Windows-Bereitstellung verwendet. Dieser Schritt ist erforderlich, nur, wenn der Testcomputer Out-of-Box-NIC-Treiber benötigen, sodass über Netzwerkkonnektivität verfügen, während Inventar oder das Windows-Abbild bereitgestellt wird.

-   Vorbereiten des Windows PE USB-Laufwerks Test Computer Inventar. Um bare-Metal-Computern Bestandsaufnahme, müssen Sie ein startbares USB-Laufwerk zum Starten des Computers und Hinzufügen der Kontaktobjekte zu den Bestand erstellen.

-   Hinzufügen von Test-Computer, Bilder und unbeaufsichtigte Dateien zu der Inventar.

-   Hinzufügen von Out-of-Box-Treiber an den Windows-Bereitstellungsdienst-Treiber Store, damit sie für das Einfügen von Treibern während der Bild-Bereitstellung verfügbar sind.

Weitere Informationen hierzu finden Sie unter [Windows-Assessment-Services-Setup und Konfiguration](windows-assessment-services-setup-and-configuration-wastechref.md).

## <a name="a-href-idbkmk-wastr-step3astep-2-create-a-project"></a><a href="" id="bkmk-wastr-step3"></a>Schritt 2: Erstellen eines Projekts


Ein Projekt ist eine Auflistung von Anlagen, die Sie bewerten möchten. Es gibt mehrere Computer und mehrere Bilder, die einer Teilmenge von allen Computern und Bilder, die Sie Ihrem Inventar hinzugefügt. Ein Projekt bietet eine kontextabhängige, verwaltbare Ansicht Anlagen von Interesse und Paare von jedem Computer mit einer Datei Bild und Antwort. Ein Projekt enthält keine Bewertung.

In diesem Schritt erstellen Sie ein Projekt, indem Sie eine Reihe von Testcomputern aus Ihrem Inventar. Wenn der Computer, die Sie auswählen bare-Metal-Computern sind oder Sie das Abbild auf dem Testcomputer aktualisieren möchten, wählen Sie auch die Bilder, die Sie auf jedem Computer anwenden möchten. Achten Sie darauf, dass Bilder auswählen, die die Architektur der Testcomputer entsprechen.

**Erstellen eines Projekts**

1.  Klicken Sie auf der Seite Erste Schritte auf **Neues Projekt erstellen**.

2.  Geben Sie in das Textfeld **Projektname** **Project1**aus.

3.  Geben Sie in das Textfeld **Beschreibung** eine Beschreibung ein. Beispielsweise **Hierbei handelt es sich um einen Testlauf erfahren, wie von Assessment Services in Meine laborumgebung.**

4.  Klicken Sie im Textfeld **Schlüsselwörter** Geben Sie Schlüsselwörter ein **Project1**, und klicken Sie dann auf **Weiter**.

5.  Klicken Sie im Fenster **Computer zum Einschließen in dieses Projekt auswählen** auf **Hinzufügen** , und wählen Sie den Computer, den in diesem Projekt enthalten sein sollen. Klicken Sie auf **OK** , und klicken Sie dann auf **Weiter**.

6.  Klicken Sie im Fenster **Bild Inventar** auf **Hinzufügen** , und wählen Sie Bilder, die Sie Ihrem Projekt hinzufügen. Klicken Sie auf **OK** , und klicken Sie dann auf **Fertig stellen**.

    **Hinweis**  
    Wenn Ihre Testcomputern bereits ein ausgeführten Betriebssystem haben, müssen Sie keinen Bilder dem Projekt hinzuzufügen.

     

Die Homepage für Windows ASC wird geöffnet.

## <a name="a-href-idbkmk-wastr-step4astep-3-create-a-job"></a><a href="" id="bkmk-wastr-step4"></a>Schritt 3: Erstellen eines Auftrags


In diesem Schritt erstellen Sie einen Auftrag, passen Sie die Einstellungen und einen Auftrag in Ihrem Projekt zu speichern. Ein Auftrag zuordnet Bewertung Objekte (ein Computer und ein Windows-Abbild). Ein Auftrag kann mehreren Computern, die entsprechenden Bilder und unbeaufsichtigte Antwortdateien und mehrere Bewertung enthalten. Sie können eine beliebige Anzahl von Bewertungen zum Ausführen auf den Testcomputern auswählen, jedoch in diesem Handbuch veranschaulicht eine einzelne Bewertung auf mehreren Testcomputern durchführen.

**Hinzufügen einer Bewertung zu den Auftrag**

1.  Klicken Sie auf der Startseite auf **Neuer Auftrag erstellen**.

2.  Geben Sie im Fenster Neuer Auftrag im Textfeld **Auftragsname** **Treiber überprüfen**.

3.  Die folgenden Auftragstypen sind verfügbar:

    1.  **Erstellen eines benutzerdefinierten Auftrags**. Wenn Sie diese Option auswählen, fügen Sie Analysen, die für die allgemeine Verwendung in der Windows-ASC entworfen wurden, der benutzerdefinierte Auftrag wird geöffnet.

    2.  **Erstellen Sie einen Auftrag aus einer Vorlage**. Wenn Sie diese Option auswählen, wird ein Template-Fenster geöffnet, und fügen vorkonfigurierten Aufträge oder Bewertungen, die Einstellungen vorkonfiguriert haben.

    3.  **Erstellen einer Energie Effizienz Auftrag**. Wenn Sie diese Option auswählen, fügen Sie Analysen, die als Arbeitslasten So testen Sie die Batterie Leben und weniger Energie Effizienz auf Laptops ausgeführt werden sollen.

    Klicken Sie auf **Erstellen eines benutzerdefinierten Auftrags**.

4.  In der neuen Registerkarte in Windows ASC werden die Einstellungen eines Auftrags für standardmäßig hervorgehoben. Im Detailbereich auf der rechten Seite können Sie den Namen ändern, fügen Sie eine Beschreibung hinzu und Hinzufügen von Schlüsselwörtern, um das Projekt und die Ergebnisse zu identifizieren.

    Passen Sie die folgenden Einstellungen:

    1.  Geben Sie Schlüsselwörter ein, um den Auftrag bei der Suche zu identifizieren.

    2.  Wählen Sie ein **Verhalten bei Fehlern** aus der Dropdownliste aus, und wählen Sie dann auf **Beenden** , um den Auftrag zu beenden, wenn ein Fehler vorliegt, da wir nur eine Bewertung in diesen Auftrag ausgeführt werden.

    3.  Wählen Sie unter **Configure Analysis Option Sie bevorzugen**wird eine Option für die Analyse der Ergebnisse.

        **Vollständige Analyse auf dem Server** ist standardmäßig aktiviert. Dieser Option können Sie dem Zielcomputer für andere Zwecke freizugeben und nutzen Sie die Ressourcen auf dem Server mit der Analyse Zeit sparendes verwenden Symbole, die bereits auf dem Server geladen.

5.  Klicken Sie unter **Assessment**klicken Sie auf **Bewertung hinzufügen**.

6.  Klicken Sie im Detailbereich auf der rechten Seite auf das Pluszeichen (**+**) neben **Treiber Überprüfung** des Auftrags das Assessment hinzugefügt.

**Hinzufügen von Testcomputern, die keine Bereitstellung benötigen**

1.  In der Windows-ASC unter **Einstellungen eines Auftrags für**auf **Übersicht**und deaktivieren Sie das Kontrollkästchen **Bild übernehmen** .

2.  Klicken Sie unter **Einstellungen für** **Anlagen**auf und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

3.  Wählen Sie im Fenster **Wählen Evaluation Objekte** die Computer, die bereits ein unterstütztes Betriebssystem installiert ist, und klicken Sie dann auf Fertig stellen.

**Hinzufügen von Computern und Bilder, die Bereitstellung benötigen**

1.  In der Windows-ASC unter **Einstellungen eines Auftrags für** **Übersicht**auf und wählen Sie dann das Kontrollkästchen **Bild übernehmen** .

2.  Wenn Sie übereinstimmenden Plug & Play einschleusen Treiber aus einer dynamische Treiber Bereitstellung Treiber während der Bereitstellung von Bild speichern möchten, wählen Sie **Dynamische Treiber-Bereitstellung**.

3.  Klicken Sie unter **Einstellungen für** **Anlagen**auf und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

4.  Wählen Sie im Fenster **Wählen Evaluation-Objekte** die Computer, die zu untersuchenden. Klicken Sie auf **Weiter**, und klicken Sie dann auf **Fertig stellen**.

5.  Die Computer auf der rechten Seite des Windows ASC unter **Evaluation Anlagen**angezeigt werden. Wählen Sie einen Computer, klicken Sie auf **Das Bild ändern**, wählen Sie das Bild, das Sie auf diesem Computer anwenden möchten, und klicken Sie dann auf **OK**.

    **Warnung**  
    Der Computer und die Architektur Bild müssen übereinstimmen, außer dass Sie ein Bild X86 basierend auf einem X64-basierten Computer bereitstellen auswählen können.

     

## <a name="a-href-idbkmk-wastr-step5astep-4-run-the-job"></a><a href="" id="bkmk-wastr-step5"></a>Schritt 4: Ausführen des Auftrags


Sie können einem Auftrag auf alle Anlagen, die führen Sie zum Projekt hinzugefügt, führen Sie einen Auftrag auf eine Teilmenge dieser Ressourcen oder andere Aufträge auf verschiedene Objekte, die im Projekt verfügbar sind. In diesem Schritt legen Sie die Einstellungen zur Laufzeit, Ausführung des Auftrags und Anzeigen des Status des Auftrags werden.

**Ausführen des Auftrags**

1.  Klicken Sie in der Windows-ASC auf **Ausführen** , um die Auftragsinstanz zu starten.

2.  Klicken Sie im Dialogfeld **Auftrag ausführen** Geben Sie **Auftrag Instanz Tag** und **Testdurchlauf** Informationen ein, und klicken Sie dann auf **OK**.

    **Hinweis**  
    Das Auftrag Instanz Tag identifiziert die Iteration, Installationsart oder Fokus des Vergleichs. Beispielsweise OEM-Win7, Clean Win7, OEM-Win8, Clean Win8. Sie können einen Auftrag oft ausführen. Aus diesem Grund haben Sie mehrere Instanzen des Auftrags. Der Testdurchlauf stellt einen Meilenstein, eine logische Gruppe von Computern oder andere Differentiations, beispielsweise Phase A, B Phase, Phase C, d Phase. Diese Schlüsselwörter können Sie die entsprechenden Ergebnisse feststellen, wenn Sie über eine Liste der Ergebnisse suchen, aber sie nicht erforderliche Felder werden.

    Wenn der Auftrag abgeschlossen ist, werden die Ergebnisse wieder auf dem Server unter kopiert \\ \\% WAS Server\\entspannen\\Ergebnisse\\Projekt %\\TestPass %\\Auftragsname %\\Computername%\\JobInstanceTag %\_Zeitstempel %\\.

     

3.  Wenn die Registerkarte Ergebnisse geöffnet wird, überprüfen Sie den Status des Auftrags auf jedem Computer.

4.  Klicken Sie in Windows ASC, klicken Sie im Fenster Monitor Instanzen auf **Details anzeigen**.

5.  Klicken Sie auf den Namen des Computers, zusätzliche Einzelheiten zu den Fortschritt des Auftrags auf diesem Computer ausgeführt.

    **Hinweis**  
    Wenn Sie ein Bild auf dem Testcomputer anwenden möchten, kann es für den Vorgang so schließen Sie ein paar Minuten dauern.

     

## <a name="a-href-idbkmk-wastr-step6astep-5-review-the-results"></a><a href="" id="bkmk-wastr-step6"></a>Schritt 5: Überprüfen Sie die Ergebnisse


Wenn Sie mehrere Ergebnisse in Windows-ASC öffnen erhalten Sie einen Überblick über die Ergebnisse. Die Ansicht "Zusammenfassung" zeigt jede Auftragsinstanz als Spalte an. Unter den Tabellen Übersicht angezeigt werden als Diagramm Metriken für jedes Assessment in die Auftragsinstanz. Diese Zusammenfassung enthält Informationen zu dem Computer, den Auftrag, der ausgeführt wurde und allgemeine Metriken, die gemessen wurden. Es enthält einen visuellen Vergleich der gleichen Metrik auf mehrere Auftragsinstanzen und können Sie auswählen, welche Metriken angezeigt werden. Diese Ansicht der Ergebnisse kann Ihnen dabei Identifizieren einzelner Computer in Ihrer laborumgebung, die Qualität Verbesserungen benötigen.

In diesem Schritt müssen Sie die Ergebnisse für den abgeschlossenen Auftrag anzeigen.

**Überprüfen Sie das Ergebnis**

1.  Klicken Sie auf den Pfeil, um zur Ansicht Instanz Auftrag zurückzukehren.

2.  Stellen Sie sicher, dass der Auftrag abgeschlossen ist, wählen Sie den Auftrag aus, und klicken Sie dann auf **Ergebnisse anzeigen**.

    **Hinweis**  
    Die Schaltfläche **Ergebnisse anzeigen** ist nicht verfügbar, bis eine Auftragsinstanz abgeschlossen und markiert ist.

     

3.  Überprüfen Sie auf der Seite **Übersicht über die Ergebnisse** , die Gesamtanzahl der Fehler und Warnungen, die für jeden Computer in gemeldet wurden die **Übersicht: Allgemeine Probleme** Tabelle.

4.  Alle sichtbare Metriken haben Balkendiagrammen unter Übersicht über die Tabellen. In einer der Bewertung metrischen Zeilen wie etwa **Treiber Überprüfung: fehlende Geräte Treiber** klicken Sie auf **Sortieren** , um das Diagramm in ein aufsteigender oder absteigender Reihenfolge anordnen.

5.  Wählen Sie den ersten Balken im Diagramm die entsprechende Spalte in der Übersicht zu markieren.

6.  Klicken Sie auf **Details anzeigen** in der unteren rechten Ecke, um ausführliche Auftragsergebnisse für den ausgewählten Computer anzuzeigen.

7.  Erweitern Sie die Metrik, die mit dem höchsten Wert enthält, und wählen Sie ein einzelnes Problem Weitere Informationen im Detailbereich auf der rechten Seite angezeigt.

8.  Erweitern Sie im Bereich Probleme eines der Probleme zu finden Sie unter Was für die Behebung empfohlen wird. Entfernen von zusätzlichen Treiber wird beispielsweise empfohlen, wenn Sie Geräte mit mehrere Treiber haben. Falls zusätzliche Treiber aufgelistet sind, navigieren Sie zum Speicherort Datei für diesen Computer, die unter **zusätzliche Treiber, die entfernt werden kann**, angegeben und löschen Sie zusätzliche Treiber. Wenn Sie den Auftrag erneut ausführen, sollten Sie feststellen, dass Sie keine zusätzlichen Treiber haben.

## <a name="a-href-idbkmk-wastr-concludeaconclusion"></a><a href="" id="bkmk-wastr-conclude"></a>Abschluss


In diesem Leitfaden Computern und Bildern testen Sie installierte und konfigurierte Windows Assessment Services erstellt eine Inventur der, setup dynamische Treiber Bereitstellung, ein Projekt erstellt, einen Auftrag mit der Treiber Überprüfung Assessment ausgeführt wurde und überprüft die Bewertungsergebnisse. Hierbei handelt es sich um ein einfaches Szenario. Erweiterte Szenarien gehören die folgenden:

-   Mehrere Bewertung auf Testcomputern ausgeführt.

-   Den gleichen Satz von Bewertung auf einem einzelnen Computer ausgeführt, aber verschiedene Bilder verwenden.

-   Anzeigen von Vergleich Berichten für Assessment Aufträge, die verschiedene Bilder enthalten.

-   Erfassen und Bereitstellen von Bildern mit anderen Formaten.

## <a name="next-steps"></a>Nächste Schritte


Erstellen ein anderes Projekt, und versuchen Sie es anderen Bewertung fügen Sie weiterer Computer hinzu, oder verwenden Sie ein anderes Bild. Wenn Sie den letzten Auftrag mithilfe der Windows Assessment Services zur Bereitstellung von Windows auf Computern ausgeführt haben, können Sie Zeit sparen, durch die Bewertung von Computern, die bereits für Windows 8 installiert.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

[Häufige Szenarien Windows Assessment Services](windows-assessment-services-how-to-topics--wastechref.md)

[Analysieren Sie die Ergebnisse auf ein anderes Gerät](analyze-results-on-another-device.md)

 

 







