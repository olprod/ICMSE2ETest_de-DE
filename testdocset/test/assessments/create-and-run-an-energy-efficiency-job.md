---
title: "Erstellen und Ausführen eines Energie Effizienz Auftrags"
description: "Erstellen und Ausführen eines Energie Effizienz Auftrags"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c98256c9-59a4-4bcb-b39a-6821719c34fc
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 28f645ccdca30ebb512a13bf5f4c6ab2ae6ca146
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-and-run-an-energy-efficiency-job"></a>Erstellen und Ausführen eines Energie Effizienz Auftrags


In diesem Thema wird beschrieben, wie erstellen und Ausführen eines Auftrags, bei dem die Batterie Leben und weniger Energie Effizienz eines tragbaren Computers analysiert.

Ein herkömmliches Szenario für diesen Auftrag umfasst nur einmal Ausführen des Auftrags. Verwenden Sie beim ersten, den Sie den Auftrag ausführen den Modus **Batterie führen Sie nach unten mit Energie Effizienz Diagnose** mit Arbeitslasten, die den Computer wie Übung, dass Sie oder Ihren vorgesehenen Endbenutzer auf den Computer verwenden würden. Es sind mehrere Arbeitslasten verfügbar. Datei oder Foto Behandlung, beim Durchsuchen des Internets, streaming Media und sogar eine Arbeitslast Leerlaufzeit simuliert beinhalten. Die Diagnose Hilfe behandeln Sie Energie-Effizienz Probleme treten während im Leerlauf Zeiträume und die Batterieverbrauch beeinflussen. Bevor Sie den Auftrag erneut ausführen, Beheben von Problemen, die Sie identifiziert. Wenn die Ergebnisse der Ausführung des Auftrags im Modus **Batterie führen Sie nach unten mit Energie Effizienz Diagnose** zulässig sind, Ausführung des Auftrags erneut die Akkulaufzeit zu überprüfen, ohne zu diagnostic Ergebnissen mithilfe von Modus **Batterie nur nach unten ausgeführt** .

Eine andere herkömmliches Szenario enthält dieses Typs des Auftrags für kurze Zeit mithilfe des **Energie-Effizienz durch nur Diagnose** -Modus ausgeführt. In diesem Modus verwenden, können Sie bestimmen, wie effizient der Computer Energie unter normalen Arbeitslasten verwendet, während der Ausführung auf Batterie.

Es gibt mehrere Arbeitslasten und Modi für einen Auftrag Energie-Effizienz. Die folgenden Schritte bieten einen Leitfaden aber können Sie festlegen, welche Modi und welche Arbeitslasten ausüben.

In diesem Thema:

-   [Erforderliche Komponenten](#prerequisites)

-   [Schritt 1: Erstellen eines neuen Auftrags Energie-Effizienz](#step1)

-   [Schritt 2: Konfigurieren von Einstellungen eines Auftrags für](#step2)

-   [Schritt 3: Konfigurieren von Einstellungen für Energie-Effizienz](#step3)

-   [Schritt 4: Hinzufügen einer Arbeitslast](#step4)

-   [Schritt 5: Ausführen des Auftrags](#step5)

## <a name="prerequisites"></a>Voraussetzungen


**Anforderungen**

Der Computer muss auf Batterie ausgeführt. Energie Effizienz Aufträge dienen nur auf mobilen Geräten ausgeführt werden. Wenn der Auftrag eine Batterie nicht erkennt, erhalten Sie einen Fehler.

**Empfehlungen**

Bevor Sie beginnen, konfigurieren Sie die Einstellungen des tragbaren Computers reduzieren das Risiko von Warnungen in den Ergebnissen generieren und Stromverbrauchs beeinträchtigen. Die folgenden Richtlinien werden Einstellungen empfohlen. Sie sind nicht erforderlich für die Ausführung des Auftrags, aber die Ergebnisse beeinträchtigt werden, wenn der Computer ist nicht richtig konfiguriert.

-   Stellen Sie sicher, dass drahtlosen Funktionalität aktiviert und mit dem Netzwerk verbunden ist. Wenn drahtlosen Funktionen aktiviert und verbunden nicht zur Verfügung, können die Ergebnisse realistische Szenarien nicht wider.

    Öffnen Sie in der Systemsteuerung **Drahtlosnetzwerke verwalten**. Wenn wireless-Funktion nicht aktiviert ist, schalten Sie ihn und Verbinden mit einem drahtlosen Netzwerk.

    **Hinweis**  
    Wenn drahtlosen Verbindung ist auf, aber es kein Netzwerk ist für die Verbindung, sind die Ergebnisse weiterhin betroffen.

     

-   Installieren und Aktivieren von Antivirussoftware. Wenn die Antivirensoftware nicht aktiviert ist und ausgeführt wird, können die Ergebnisse realistische Szenarien nicht wider.

    Öffnen Sie in der Systemsteuerung **Action Center**, klicken Sie auf **Sicherheit**und überprüfen Sie, dass **Virenschutz** auf **aktiviert**festgelegt ist. Wenn es nicht auf **aktiviert**festgelegt ist, klicken Sie auf **Aktion Center-Einstellungen ändern**, und wählen Sie dann das Kontrollkästchen **Virenschutz** aus.

-   Stellen Sie sicher, dass die Power-Richtlinie auf **Balanced**festgelegt ist. Alle anderen Power Richtlinien generiert standardmäßig eine Warnung ausgegeben, die das Ergebnis beeinflussen können.

-   Stellen Sie sicher, dass der Computer so konfiguriert ist, dass ein Kennwort nicht erforderlich ist, wenn der Computer aus einem Bildschirmschoner wird.

-   Stellen Sie sicher, dass alle Gerätetreiber ordnungsgemäß installiert sind. Ergebnisse können deutlich variieren, wenn Ihr Computer mit fehlenden oder falschen Treiber verfügt. Die [Überprüfung der Treiber](driver-verification.md) Bewertung können Sie um Treiberprobleme auf dem Computer zu identifizieren, die Sie ermitteln möchten.

**Hinweis**  
Dieser Auftrag wird mit minimaler Benutzeroberfläche ausgeführt, und Sie möglicherweise nicht er nicht abgebrochen werden, nachdem es gestartet wurde. Je nachdem, welche Arbeitslasten ausgewählt sind, möglicherweise keine weiteren vorhanden, auf dem der Auftrag ausgeführt wird, nachdem es gestartet wurde.

 

## <a name="a-href-idstep1astep-1-create-a-new-energy-efficiency-job"></a><a href="" id="step1"></a>Schritt 1: Erstellen eines neuen Auftrags Energie-Effizienz


Ein Auftrag Energie-Effizienz verwendet Arbeitslasten zum simulieren die Benutzeraktivitäten und zum Generieren von Ergebnissen für Batterie Leben und weniger Energie Effizienz. Energie Effizienz Auftragsergebnisse enthalten keine Arbeitslast-spezifischen Leistungsergebnisse. Die Ergebnisse, die protokolliert werden, wenn der Auftrag Arbeitslasten verwendet sind zur Energie-Effizienz spezifisch. Sie hinweisen nicht, inwieweit die Arbeitslast ausgeführt wurde. Im folgenden Verfahren Erstellen eines neuen Auftrags und klicken Sie dann Energie-Effizienz als der Auftragstyp angeben, sodass die richtigen Konfigurationseinstellungen und Arbeitslasten dem Projekt hinzugefügt werden können.

**Zum Erstellen eines neuen Auftrags Energieeffizienz**

1.  Klicken Sie in der Windows-Assessment-Konsole auf **Optionen**, und klicken Sie dann auf **Neuer Auftrag**.

2.  Geben Sie im Dialogfeld **Neuer Auftrag** einen Auftrag ein, und klicken Sie auf **eine Energie Effizienz Auftrag erstellen**.

    Eine neue Registerkarte wird im Windows-Assessment-Konsole, mit der Bezeichnung mit dem Namen Job angezeigt.

## <a name="a-href-idstep2astep-2-configure-job-settings"></a><a href="" id="step2"></a>Schritt 2: Konfigurieren der Einstellungen eines Auftrags für


Nachdem Sie die Auftragstyp ausgewählt haben, können Sie die Einstellungen eines Auftrags für anpassen. In diesem Schritt konfigurieren Sie die allgemeinen Einstellungen.

**So konfigurieren Sie die Einstellungen eines Auftrags für**

1.  Klicken Sie unter **Einstellungen eines Auftrags für**auf **Übersicht** , wenn sie nicht bereits ausgewählt ist.

2.  Verwenden Sie die Felder **Name**, **Beschreibung**und **Notizen** , Informationen zu diesen Auftrag hinzuzufügen, klicken Sie im Detailbereich auf der rechten Seite.

3.  Sie können auch diese Einstellungen anpassen:

    -   **Beenden Sie diesen Auftrag, wenn ein Fehler auftritt**. Aktivieren Sie dieses Kontrollkästchen So beenden Sie den Auftrag aus endet, wenn ein Fehler auftritt. Diese Einstellung ist nützlich, wenn ein Auftrags für einen längeren Zeitraum ausgeführt wird. Es kann lange Wartezeiten verhindern, wenn der Auftrag ein Fehler auftritt. Kürzere Aufträge ist der Auftrag gestoppt wird im Allgemeinen nicht erforderlich, wenn ein Fehler auftritt.

    -   **Alle von Bewertungen erstellte temporäre Dateien beibehalten**. Wenn die Fehlerdateien untersuchen, die während der Ausführung des Auftrags erstellt werden soll, aktivieren Sie dieses Kontrollkästchen.

## <a name="a-href-idstep3astep-3-configure-energy-efficiency-settings"></a><a href="" id="step3"></a>Schritt 3: Konfigurieren von Einstellungen für Energie-Effizienz


Nachdem Sie die Einstellungen eines Auftrags für anpassen, konfigurieren Sie die Einstellungen, die bestimmte Informationen über die Ausführung des Auftrags Energie-Effizienz bereitstellen.

**So konfigurieren Sie Einstellungen Energie-Effizienz**

1.  Klicken Sie unter **Einstellungen eines Auftrags für** **Energie Effizienz Einstellungen**auf.

2.  Klicken Sie im Detailbereich auf der rechten Seite in **der Liste** auf einen der folgenden Modi:

    -   **Batterie nur nach unten ausgeführt**. Verwenden Sie diesen Modus, um die Zeitspanne zu ermitteln, die ein portablen Computers auf Batterie ausgeführt werden kann.

    -   **Batterie nach unten mit Energie Effizienz Diagnosen ausführen**. Verwenden Sie diesen Modus, um Batterie rundown Ergebnisse zusätzlich zur Diagnose Metriken für die CPU-Auslastung Datenträgerverwendung und andere Verhaltensweisen Energie und Leistung zu erhalten. Wenn Sie die im Leerlauf Arbeitslast verwenden, werden diagnostische Metriken für Intervalle im Leerlauf und andere Aktivitäten im Leerlauf ebenfalls angezeigt.

    -   **Energie-Effizienz mit nur Diagnose**. Verwenden Sie diesen Modus Energie-Effizienz bewerten, während der Computer die verfügbaren Arbeitslasten ausübt. Dieser Modus erzeugt diagnostic Metriken und Probleme, aber es nicht Batterie rundown Metriken generiert.

3.  Wenn Sie den Auftrag zu starten, bevor die Batterie vollständig geladen, wählen ist möchten die **Starten bevor aufgeladen** das Kontrollkästchen. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wenn Sie diese Option auswählen, müssen Sie einen Prozentsatz im Feld **Batterie starten %** eingeben.

4.  Wenn Sie ausgewählt haben die **starten, bevor vollständig geladen** das Kontrollkästchen, geben Sie eine Zahl zwischen 1 und 100 im Feld **Batterie starten %** , um den Prozentsatz darstellen, die Batterie aufgeladen wird, wenn der Auftrag wird gestartet werden soll. Es wird empfohlen, eine vollständig geladenen Batterie für den Modus **Batterie nur nach unten ausgeführt** .

    **Hinweis**  
    Es kann nicht möglich, die über einen bestimmten Prozentsatz Batterie sein. Wenn die Batterie nicht aufgeladen bevor er den Wert **Batterie start %** erreicht, wird davon ausgegangen, vollständig geladen.

     

5.  Wenn Sie den Auftrag beenden, bevor die Batterie vollständig entladen wird möchten, aktivieren Sie das Kontrollkästchen **vor dem Entladen vollständig beendet** . Standardmäßig ist dieses Kontrollkästchen aktiviert, und Sie können einen Prozentsatz im Feld **Batterie End %** eingeben. Standardmäßig ist der Wert 5.

6.  Wenn Sie das Kontrollkästchen **vor dem Entladen vollständig beendet** deaktivieren, werden der Auftrag beendet, wenn die Batterie vollständig entladen wird.

7.  Wenn der Auftrag ohne eingabeaufforderungen ausgeführt werden soll, aktivieren Sie das Kontrollkästchen **automatische Ausführen** . Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wenn Sie diese Option auswählen, geben Sie trennen und Wiederherstellen von Power-Befehle in den nächsten beiden Feldern des Auftrags betreffenden Phase zu erhalten.

8.  Wenn Sie das Kontrollkästchen **Führen Sie automatisierte** ausgewählt haben, geben Sie einen Befehl Trennen Power im **Power zu trennen** .

9.  Wenn Sie das Kontrollkästchen **Führen Sie automatisierte** ausgewählt haben, geben Sie einen Befehl zur Wiederherstellung Power im **Power Befehl Wiederherstellen** .

10. Im Feld **Protokollierung Häufigkeit (in Minuten)** angeben, in Minuten an, wie oft Ergebnisse auf den Datenträger geschrieben werden, nachdem die Batterie den kritischen Grenzwert erreicht, die dem Computer deaktiviert. Der Standardwert ist 1 Minute. Wenn Ergebnisse seltener geschrieben werden, sind weitere Ergebnisse verloren, wenn die Leistungsfähigkeit Batterie abläuft.

## <a name="a-href-idstep4astep-4-add-a-workload"></a><a href="" id="step4"></a>Schritt 4: Hinzufügen einer Arbeitslast


Eine Arbeitslast ist ein Satz von automatisierten Aufgaben, bei die den Computer auf eine vordefinierte, wiederholbare Weise Übung ebenso wie eine Bewertung. Es sind mehrere Arbeitslasten verfügbar. In diesem Schritt wählen Sie die Arbeitslast, die Sie Übung, während Sie die Batterie und Energie-Effizienz bewerten haben möchten. Sie sollten Arbeitslasten auswählen, die den Computer wie Übung, die möglicherweise von Ihrem beabsichtigten Endbenutzer. Sie können mischen Arbeitslasten übereinstimmen, und Sie können nur einmal eine Arbeitslast hinzufügen. Der Auftrag Energie-Effizienz durchlaufen die Arbeitslasten aus, bis der Auftrag abgeschlossen ist.

**Hinzufügen eine Arbeitslast**

1.  Klicken Sie in der Windows-Assessment-Konsole unter **Bewertung**, auf **Bewertung hinzufügen**.

    Arbeitslast, die für einen Auftrag Energie-Effizienz verfügbar sind, werden auf der rechten Seite angezeigt.

2.  Klicken Sie auf das blaue Pluszeichen (**+**) neben eine oder mehrere der Arbeitslast um sie in das Projekt hinzuzufügen. Diese Arbeitslasten sind verfügbar:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Arbeitslast</th>
    <th>Beschreibung</th>
    <th>Anforderungen</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Dateiverarbeitung (Arbeitslast)</strong></p></td>
    <td><p>Ein Benutzer, der ist kopieren, verschieben, komprimieren, extrahieren und Löschen von Dateien und Ordnern simuliert.</p></td>
    <td><p>Erfordert Windows 8 oder Windows 10.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Im Leerlauf Energieeffizienz (Aufgaben)</strong></p></td>
    <td><p>Setzt das System im Leerlauf für eine angegebene Zeitspanne.</p></td>
    <td><p>Erfordert Windows 8 oder Windows 10.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Streaming Media (Arbeitslast)</strong></p></td>
    <td><p>Simuliert ein Benutzer, der ein Video in Internet Explorer überwacht wird.</p></td>
    <td><p>Erfordert Windows 8 oder Windows 10, und InternetExplorer 9 oder InternetExplorer 10.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Windows Media Player Wiedergabe (Arbeitslast)</strong></p></td>
    <td><p>Simuliert das streaming von Videos mithilfe von Windows Media Player.</p></td>
    <td><p>Erfordert Windows 8 oder Windows 10.</p></td>
    </tr>
    </tbody>
    </table>

     

3.  Wählen Sie eine Arbeitslast zum Ändern der Einstellungen aus:

    -   Die Arbeitslast Dateiverarbeitung hat die folgenden Einstellungen verfügbar:

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
        <td><p>Gibt an, ob die Arbeitslast Dateiverarbeitung ausgeführt wird, verwenden die empfohlenen Werte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
        </tr>
        <tr class="even">
        <td><p>Iterationen</p></td>
        <td><p>Gibt die Anzahl der Versuche, die diese Arbeitslast ausgeführt wird. Standardmäßig ist der Wert 1.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Source</p></td>
        <td><p>Gibt den Speicherort der Dateien und Ordner, die die Arbeitslast kopiert. Standardmäßig ist die Quelle auf dem lokalen Computer. Verwenden Sie diese Einstellung an einen anderen Speicherort oder andere Dateien verwenden.</p></td>
        </tr>
        <tr class="even">
        <td><p>Ziel</p></td>
        <td><p>Gibt den Speicherort an, dem die Arbeitslast Dateien oder Ordner kopiert. Sie benötigen Schreibzugriff auf den Zielordner. Sie können den Standardordner verwenden oder einen anderen Ordner. Wenn Sie einen anderen Zielordner bereitstellen, muss der Ordner leer sein, bevor der Auftrag ausgeführt.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Datenspeicherort importieren</p></td>
        <td><p>Gibt an, für die Verwendung von Benutzern erstellte Nutzlast während des Betriebs der Arbeitslast. Wenn Sie einen Speicherort importieren Daten angeben, werden die Daten aus dem Importspeicherort in den Ordner Quelle kopiert. Wenn die Arbeitslast ausgeführt wird, wird der Inhalt der Quelle in den Zielordner kopiert. Aus diesem Grund beim Importieren von Daten, müssen sowohl die Quell-als auch Ordner leer sein, wenn der Auftrag wird gestartet.</p></td>
        </tr>
        </tbody>
        </table>

         

        Weitere Informationen zum Behandeln von Datei Assessment finden Sie unter [Dateiverarbeitung](file-handling.md).

    -   Die Arbeitslast im Leerlauf Energieeffizienz hat die folgenden Einstellungen verfügbar:

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
        <td><p>Gibt an, ob die Arbeitslast im Leerlauf Energieeffizienz ausgeführt wird, verwenden die empfohlenen Werte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
        </tr>
        <tr class="even">
        <td><p>Minuten</p></td>
        <td><p>Gibt die Anzahl der Minuten an, denen das System bleiben sollen im Leerlauf Modus an. Standardmäßig ist der Wert 11.</p></td>
        </tr>
        </tbody>
        </table>

         

    -   Die Streaming Media-Arbeitslast hat die folgenden Einstellungen verfügbar:

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
        <td><p>Gibt an, ob die Streaming Media-Arbeitslast ausgeführt wird, unter Verwendung der Standardwerte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
        </tr>
        <tr class="even">
        <td><p>Iterationen</p></td>
        <td><p>Gibt die Anzahl der Versuche, die die Arbeitslast ausgeführt wird. Standardmäßig ist der Wert 3.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Inhaltspfad</p></td>
        <td><p>Gibt den Pfad der das Quellverzeichnis für das Dataset, das Medien und HTML-Dateien, die die Arbeitslast enthält. Standardmäßig wird die Inhalte am Inhalt/Streaming Media verwendet.</p></td>
        </tr>
        <tr class="even">
        <td><p>Servername</p></td>
        <td><p>Gibt den Namen des streaming Media-Server auf dem lokalen Netzwerk an. Obwohl das werden leer angezeigt wird, ist der Pfad des Standardserver definierten. Wenn Sie ein alternativen Servernamen nicht angegeben ist, wird die Arbeitslast streaming-Server auf dem lokalen Computer gestartet.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Port</p></td>
        <td><p>Gibt an, auf der Port, den der Server akzeptiert anfordert. Der Standardwert ist Port 80.</p></td>
        </tr>
        <tr class="even">
        <td><p>Streaming Zeit</p></td>
        <td><p>Gibt die maximale Zeit in Sekunden, die der Auftrag wartet, bis ein video Arbeitslast um die Wiedergabe abzuschließen. Standardmäßig ist der Wert für diese Einstellung 65.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Arbeitslasten</p></td>
        <td><p>Die Streaming Media-Arbeitslast streamen Video auf Internet Explorer, mithilfe von Inhalten, die verschiedene Auflösungen hat. Der Standardwert ist 720p (30 f/s).</p></td>
        </tr>
        </tbody>
        </table>

         

        Weitere Informationen zu den Streaming Media-Bewertung finden Sie unter [Streaming Media-Leistung](streaming-media-performance.md).

    -   Die Windows Media Player Wiedergabe Arbeitslast hat die folgenden Einstellungen verfügbar:

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
        <td><p>Gibt an, ob die Windows Media Player Wiedergabe Arbeitslast ausgeführt wird, unter Verwendung der Standardwerte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
        </tr>
        <tr class="even">
        <td><p>Inhaltspfad</p></td>
        <td><p>Gibt Quellordners für Medienclips, die abgespielt werden in Windows Media Player an, wenn die Arbeitslast ausgeführt wird. Standardmäßig ist an \Content\Streaming Medien zur Bewertung der Ordner. Wenn Sie Ihre eigene Medieninhalte angeben, geben Sie den vollständigen Pfad zu den Inhalt auf dem lokalen Computer oder einer Netzwerkfreigabe.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Dauer</p></td>
        <td><p>Gibt die Dauer der einzelnen Wiedergabe-Sitzung in Sekunden an. Der Standardwert ist 600.</p></td>
        </tr>
        </tbody>
        </table>

         

    -   Die Internet Explorer-Arbeitslast Wiedergabe (HTML5) hat die folgenden Einstellungen verfügbar:

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
        <td><p>Gibt an, ob die Internet Explorer Wiedergabe (HTML5) Wiedergabe Arbeitslast ausgeführt wird, verwenden die Standardwerte. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
        </tr>
        <tr class="even">
        <td><p>Inhaltspfad</p></td>
        <td><p>Gibt Quellordners für Medienclips, die abgespielt werden in Internet Explorer Wiedergabe (HTML5) an, wenn die Arbeitslast ausgeführt wird. Standardmäßig ist die Datei, die verwendet wird, \Content\Streaming Media Assessment\720p.mp4. Wenn Sie Ihre eigene Medieninhalte angeben, geben Sie den vollständigen Pfad zu den Inhalt auf dem lokalen Computer oder einer Netzwerkfreigabe.</p></td>
        </tr>
        <tr class="odd">
        <td><p>Dauer</p></td>
        <td><p>Gibt die Dauer der einzelnen Wiedergabe-Sitzung in Sekunden an. Der Standardwert ist 600.</p></td>
        </tr>
        </tbody>
        </table>

         

## <a name="a-href-idstep5astep-5-run-the-job"></a><a href="" id="step5"></a>Schritt 5: Ausführen des Auftrags


Wenn ein Auftrag Energie-Effizienz ausgeführt wird, wird es im Hintergrund, um zu verhindern, dass Windows Assessment Konsole Benutzeroberfläche aus Stromverbrauchs beeinträchtigen und beeinträchtigen die Auftragsergebnisse ausgeführt. Aber mehrere Dialogfelder angezeigt werden, vor dem Start des Auftrags. Das folgenden Verfahren können Sie über diese Dialogfelder.

**Zum Ausführen des Auftrags**

1.  Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Ausführen**.

    Wenn das Dialogfeld " **Benutzerkontensteuerung** " angezeigt wird, klicken Sie auf **Ja**.

2.  Im nächste Dialogfeld dient. Schließen Sie alle öffnen Applikationen vor der Auftrag gestartet wurde, und klicken Sie dann auf **Weiter**.

    Vor dem Start des Auftrags überprüft des Auftrags der Computerkonfiguration, um sicherzustellen, dass die Arbeitslasten erfolgreich ausgeführt werden können. Weitere Informationen zu Computerkonfiguration finden Sie unter [Voraussetzungen](#prerequisites). Der Auftrag generiert Fehlermeldungen, Warnungen und informative Nachrichten basierend auf der Konfiguration des Computers. Wenn Sie den Auftrag im Hintergrund ausführen, protokolliert der Auftrag die Benachrichtigungen. Andernfalls die Benachrichtigungen klicken Sie im Dialogfeld **Assessment Launcher** werden wie folgt angezeigt:

    -   Fehler blockieren den Anfang des Auftrags. Fehlermeldungen angezeigt, wenn das Projekt findet ein Problem mit der Computerhardware oder Konfiguration, die behoben werden muss, bevor der Auftrag fortgesetzt werden kann. Wenn eine Fehlermeldung angezeigt wird, nicht die Schaltfläche **Start** im Dialogfeld zur Verfügung.

    -   Warnungen angezeigt werden, wenn der Auftrag ein Problem gefunden werden, die Ausführung des Auftrags blockiert nicht jedoch möglicherweise das Ergebnis beeinflussen. Überprüfen die Warnungen können, Probleme beheben und klicken Sie dann auf **Aktualisieren**. Oder ignorieren Sie die Warnung, und klicken Sie auf **Start**.

    -   Informative Nachrichten bieten zusätzliche Anweisungen oder Informationen zu Aktionen, die ausgeführt wird, wenn der Auftrag ausgeführt wird. Nachdem Sie die Informationen gelesen haben, klicken Sie auf **Starten** , um den Auftrag zu starten.

    Klicken Sie auf das Symbol (&gt;) um zusätzliche Informationen zu jeder Nachricht anzuzeigen, die in das **Microsoft Assessment Startprogramm** -Fenster angezeigt wird.

3.  Wenn das Dialogfeld **System vorbereiten** angezeigt wird, müssen Sie warten, bis das System für Aufgaben aktiviert ist, zu denen das Betriebssystem geplant ausgeführt hat. Wenn eine Aufgabe geplant ist, führt der Computer vor dem Start des Auftrags. Dieser Prozess kann mehrere Minuten dauern, bis zu einer Stunde, je nach den Aufgaben abgeschlossen, die geplant werden. Wenn die Aufgaben abgeschlossen haben, klicken Sie auf **Weiter**.

4.  Wenn die Batterie vollständig geladen ist nicht, wird möglicherweise das Dialogfeld **Batterie lädt** angezeigt. Sie können einen der folgenden Schritte ausführen:

    -   Zulassen den Auftrag gestartet, vor die Batterie durch Auswählen von vollständig geladen ist die **Starten bevor aufgeladen** Kontrollkästchen und Start Prozentsatz im Feld **Batterie beginnen %** festlegen. Dadurch wird den Auftrag gestartet, sofern die aktuelle Batterie Leistung über die End-Bedingung ist, die Sie in die Energie-Effizienz Einstellungen angegeben.

    -   Die Batterie aufgeladen warten.

5.  Im nächste Dialogfeld gibt an, wann die Batterie vollständig geladen ist. Sie müssen aus Stromversorgung für den Auftrag so starten Sie Ihren Computer entfernen.

6.  Ein Dialogfeld wird beschrieben, wann der Auftrag gestartet wird. Klicken Sie auf **Jetzt starten** , um Ausführung des Auftrags oder warten, bis des Countdowns auf Fertig stellen, und lassen Sie den Auftrag automatisch gestartet.

**Wichtige**  
Nachdem der Auftrag gestartet wurde, interagieren Sie nicht mit dem Computer. Der Bildschirm möglicherweise dunkel wechseln und fortsetzen, aber keine Interaktion ist erforderlich, es sei denn, des Computers Herunterfahren während der Ausführung des Auftrags. Wenn der Computer beendet wird, schließen Sie das Netzkabel und starten Sie den Computer neu. Der Status des Auftrags Energie-Effizienz werden über den Neustart beibehalten, wenn die End-Bedingung erfüllt war nicht. Nach dem Starten des Auftrags die Arbeitslasten ausüben können Sie den Auftrag nicht abbrechen.

 

## <a name="next-steps"></a>Nächste Schritte


Wenn der Auftrag abgeschlossen ist, überprüfen Sie die Ergebnisse und Probleme.

## <a name="related-topics"></a>Verwandte Themen


[Bewertung](assessments.md)

[Windows-Assessment-Konsole](windows-assessment-console.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

 

 







