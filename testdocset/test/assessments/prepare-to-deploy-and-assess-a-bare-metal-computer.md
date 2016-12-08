---
title: Vorbereiten der Bereitstellung und Bewerten von einem bare-Metal-computer
description: Vorbereiten der Bereitstellung und Bewerten von eines bare-Metallen-Computers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a1e0a35c-c074-4833-86a0-046aa6d4baf5
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 9c0d99edaad1a4b28a6d039a5c52dcecd417027a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prepare-to-deploy-and-assess-a-bare-metal-computer"></a>Vorbereiten der Bereitstellung und Bewerten von einem bare-Metal-computer


In diesem Thema führt Sie durch den Schritten, die zum Vorbereiten und Hinzufügen eines bare-Metallen-Computers zu Ihrer Windows Assessment Services Inventar erforderlich sind. Erstellen Sie dann ein Projekt und Auftrag, den der Computer und auch das Bild enthält und die Antwortdatei ein, die verwendet werden, um ein Bild auf diesem Computer bereitstellen, bevor er bewertet wird.

In diesem Thema:

-   [Schritt 1: Hinzufügen der Boot.wim Netzwerkadapter-Treiber](#bkmk-addnicdrivers)

-   [Schritt 2: Vorbereiten des Windows PE USB-Laufwerks für den Test Computer Bestand](#bkmk-prepwinpe)

-   [Schritt 3: Hinzufügen von Testcomputern Ihrem Inventar](#bkmk-addcomps)

-   [Schritt 4: Hinzufügen von Bildern und unbeaufsichtigte Dateien](#bkmk-addimages)

-   [Schritt 5: Hinzufügen von Ressourcen zu einem Projekt](#bkmk-assetproject)

-   [Schritt 6: Hinzufügen der Objekte mit einem Projekt](#bkmk-assetjob)

## <a name="a-href-idbkmk-addnicdriversaadding-network-adapter-drivers-to-the-bootwim"></a><a href="" id="bkmk-addnicdrivers"></a>Hinzufügen der Boot.wim Netzwerkadapter-Treiber


Fügen Sie der Windows-Bereitstellungsdienste verwendet Windows PE-Abbilder Netzwerkadapter (NIC)-Treiber hinzu. Dieser Schritt ist erforderlich, nur, wenn der Testcomputer Out-of-Box NIC-Treiber benötigen, sodass sind Netzwerkkonnektivität während Inventar oder das Windows-Abbild bereitgestellt wird. Sie benötigen die NIC-Treiber beim Starten eines bare-Metallen-Computers (ein Computer, für das Betriebssystem installiert ist) in Windows PE.

**Die boot.wim NIC-Treiber hinzu**

1.  Erstellen Sie einen Ordner für die NIC-Treiber, und kopieren Sie sie in den Ordner, auf dem Server. Wenn die Treiber auf einer Freigabe gespeichert sind, können Sie beispielsweise einen Befehl wie den folgenden verwenden:

    ``` syntax
    robocopy \\Server\share\drivers C:\Drivers\amd64NIC /MIR
    ```

2.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Windows-Bereitstellungsdienste**.

3.  Erweitern Sie den Knoten **Server** und der Name Ihres Servers.

4.  Mit der rechten Maustaste **Treiber**, und klicken Sie dann auf **Paket hinzufügen**.

5.  Im Assistenten Treiberpakets hinzufügen klicken Sie auf **allen Treiberpaketen für aus einem Ordner auswählen**, und klicken Sie dann auf **Durchsuchen**.

6.  Navigieren Sie zu dem Ordner, der die Out-of-Box NIC-Treiber enthält, und klicken Sie dann auf **OK**.

7.  Klicken Sie im Paket hinzufügen-Assistenten auf **Weiter**.

8.  Klicken Sie auf der Seite **Verfügbare Treiberpakete** auf **Weiter**.

9.  Klicken Sie auf der Seite **Zusammenfassung** auf **Weiter**.

10. Wenn die Treiber an den Treiber Store kopiert werden, klicken Sie auf **Weiter**.

11. Klicken Sie auf der Seite **Treiber-Gruppen** auf **eine vorhandene Treibergruppe auswählen**, stellen Sie sicher, dass **DriverGroup1** ausgewählt ist, und klicken Sie dann auf **Weiter**.

12. Klicken Sie auf **Fertig stellen**.

13. Klicken Sie auf **den Knoten** auf **Start**, rechtsklicken Sie Boot den Treiber eingefügt werden soll und klicken Sie dann auf **Bild Treiberpakete hinzufügen**.

14. Klicken Sie in Treiberpakets hinzufügen in Boot-Bild-Assistenten auf der Seite **Vorbereitung** auf **Weiter**.

15. Klicken Sie auf der Seite **Treiberpakete auswählen** klicken Sie auf **Paket-Klasse**, und klicken Sie dann auf **Bearbeiten**.

16. Löschen Sie alles mit Ausnahme von **Net**, und klicken Sie dann auf **OK**.

17. Klicken Sie in Add Treiberpakets in Boot Image Wizard auf **Suche für Pakete**, klicken Sie auf **Weiter**, und klicken Sie dann auf **Weiter** .

18. Wenn die Treiber hinzugefügt werden, klicken Sie auf **Fertig stellen**.

Boot-Abbild verfügt nun über Out-of-Box-NIC-Treiber. Wiederholen Sie diese Schritte für jede Windows-Bereitstellungsdienste boot.wim Architektur.

## <a name="a-href-idbkmk-prepwinpeapreparing-the-windows-pe-usb-drive-for-test-computer-inventory"></a><a href="" id="bkmk-prepwinpe"></a>Vorbereiten der Test Computer Inventar das Windows PE USB-Laufwerk


Um eine Inventur bare-Metal-Computern, müssen Sie ein startbares USB-Laufwerk zum Starten des Computers und Hinzufügen der Kontaktobjekte zu der Inventar erstellen. Weitere Informationen dazu, wie Sie ein startbare Windows PE USB flash-Laufwerk vorbereiten, finden Sie unter [Exemplarische Vorgehensweise: Installieren von Windows PE auf CD, USB Flash-Laufwerk oder USB-Festplatte](http://go.microsoft.com/fwlink/p/?linkid=219488). Die exemplarischen Vorgehensweise erstellt startbare Medien mithilfe von standardmäßigen Windows PE-Abbild (wird) ohne anpassen. Bevor Sie das startbare USB flash-Laufwerk für Inventar verwenden, müssen Sie Quellordners auf die USB-Laufwerk RelaxWinPE.wim Datei kopieren, siehe das Verfahren im folgenden Abschnitt.

**Wichtige**  
Um X86-basierte Testcomputern Bestandsaufnahme, müssen Sie ein X86-basierte Windows PE-Abbild verwenden. Wenn Testcomputern AMD64-basierten Bestandsaufnahme, müssen Sie ein Bild AMD64-basierten Windows PE verwenden. Dieses Verfahren wird ein Bild X86-basierte verwendet. Wenn Ihre Testcomputern X86 und AMD64-basierten sind, erstellen Sie ein USB-Laufwerk für jede Architektur.

 

**Um die Datei boot.wim durch Windows AS wird die Datei zu ersetzen**

1.  Erstellen Sie auf dem Referenzcomputer, in dem Sie die Windows PE erstellt, Umgebung, geben Sie den folgenden Befehl ein:

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x86\Images\RelaxWinPE.wim c:\winpe_x86\media\sources\boot.wim
    ```

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x64\Images\RelaxWinPE.wim c:\winpe_x64\media\sources\boot.wim
    ```

2.  Wiederholen Sie den vorherigen Schritt zum Erstellen von einem USB-Laufwerk für jede Architektur, die für den Testcomputern benötigt.

    **Wichtige**  
    Um X86-basierte Testcomputern Bestandsaufnahme, müssen Sie ein X86-basierte Windows PE-Abbild verwenden. Wenn Testcomputern AMD64-basierten Bestandsaufnahme, müssen Sie ein Bild AMD64-basierten Windows PE verwenden.

     

Nun, da das startbare Windows PE USB flash-Laufwerk vorbereitet wird und NIC-Treiber vorhanden sind, können Sie die Windows Assessment Services Bestand Objekte wie Computern, Bilder und Antwortdateien hinzufügen und fügen Sie dann die Anlagen in Ihre Projekte und Aufträge.

## <a name="a-href-idbkmk-addcompsaadding-test-computers-to-your-inventory"></a><a href="" id="bkmk-addcomps"></a>Hinzufügen von Testcomputern zu Ihrem Inventar


Sie können zusätzlich zu den Computern bare-Metal-Computern (Computer ohne ein ausgeführtes Betriebssystem) hinzufügen, die ein ausgeführten Betriebssystem auf dem Windows Assessment Services Inventar aufweisen, damit Sie die Tools zur Bewertung der bewerten können diese Computer verwenden können. Wenn der Testcomputer ein ausgeführten Betriebssystem verfügt, werden verwenden Sie das USB-Laufwerk zum Starten und Bestandsaufnahme des Computers, wie im folgenden Abschnitt Verfahren gezeigt.

**Warnung**  
Sie sollten nicht gleichzeitig einen Testcomputer in mehreren Windows Assessment Services Server Bestände einschließen. Wenn ein Testcomputer in mehreren Windows Assessment Services Server Bestände angezeigt wird, wird eine Racebedingung zwischen den Windows-Bereitstellungsdienst-Instanzen auf jedem Server. Wenn Sie aus einem Inventar in eine andere in der Windows-Assessment-Services - Client (Windows ASC), einen Testcomputer verschieben müssen Computer Vermögenswerts im ersten Windows Assessment Services Bestand löschen und dann das Inventar auf dem neuen Windows Assessment-Services-Server hinzuzufügen.

 

**So Ihrer Inventar bare-Metal-Computern hinzu**

1.  Legen Sie das USB-Laufwerk, in dem Testcomputer.

2.  Aktivieren Sie auf dem Computer ein, und drücken Sie die Taste, die das Startvolumes Auswahlmenü für den Computer, beispielsweise Esc wird geöffnet.

3.  Wählen Sie die USB-Laufwerk als Boot-Gerät aus.

    Beim Neustart des Computers bieten Sie die folgende Informationen:

    -   Name des Computers. Der Namen des Computers muss nur alphanumerische Zeichen und Bindestriche enthalten. Enthält der Namen des Computers ein Unterstrich oder andere erweiterten Zeichen enthalten, kann der Computer nicht über Domain Name System (DNS) sichtbar sein. Der Namen des Computers muss 15 Zeichen oder weniger.

    -   Standort des Computers. Der Speicherort der Computer muss 78 Zeichen oder weniger.

    -   Gibt an, ob Sie die Treiber Aufräumen ausführen möchten. Treiber Aufräumen kopiert Treiber, die auf dem Computer an den Windows-Assessment-Services-Treiber Store.

4.  Entfernen Sie das USB-Laufwerk aus dem Testcomputer. Der Computer wird neu gestartet.

    **Hinweis**  
    Wenn Sie Bilder mithilfe der Windows-Assessment-Dienste bereitstellen, sollten die Startreihenfolge im BIOS festlegen, sodass Systemanalyse vor dem Start Execution Environment (PXE) in der Startreihenfolge erste ist. Auf diese Weise müssen Sie manuell drücken die Tastenkombination Startreihenfolge und select Netzwerkstart, bevor ein Auftrag startet.

     

5.  Öffnen Sie die ASC Windows im Menü **Start** . Stellen Sie sicher, dass die richtige Anzahl von Computern auf Ihrem Server Inventar hinzugefügt wurden, auf der Seite **Erste Schritte** .

## <a name="a-href-idbkmk-addimagesaadding-images-and-unattended-answer-files"></a><a href="" id="bkmk-addimages"></a>Hinzufügen von Bildern und unbeaufsichtigte Dateien


Sie müssen vor dem Importieren Sie sie in der Windows-Assessment-Services-Inventar und deren Verwendung für die Bereitstellung die Windows imaging (WIM-Dateien) zur Freigabe ein Bild kopieren. Die Antwortdateien, die Sie für die Bereitstellung verwenden möchten, müssen auch in die entsprechenden Serverfreigabe verfügbar sein.

**Zum Hinzufügen von Bildern in der Images gemeinsam genutzt und Bestandsdaten**

1.  Kopieren Sie auf dem Server Windows Assessment Services WIM-Dateien nach C:\\entspannen\\Bilder.

    **Hinweis**  
    Der Pfad des Bildes darf keine Leerzeichen enthalten.

     

2.  Diese Bilder werden in die Windows Assessment Services Bild Serverfreigabe, aber sie noch nicht in der Inventardatenbank importiert wurden. Verwenden Sie zum Importieren von Bildern in der Inventardatenbank eine der folgenden Methoden:

    -   Klicken Sie auf der Seite **Erste Schritte** klicken Sie auf **jetzt Bilder importieren**, wählen Sie die Bilder, klicken Sie auf **Importieren**, und klicken Sie dann auf **OK**.

    -   In der ASC Windows im Menü **Server** auf **Inventar Manager**, klicken Sie auf die Registerkarte **Bilder** und klicken Sie dann auf **Hinzufügen**.

**So fügen eine Freigabe Antwortdateien hinzu**

1.  Eine standardmäßige Antwortdatei für jede unterstützte Architektur wird bereitgestellt, bei Systemlaufwerk %\\entspannen\\Skripts\\Vorlagen. Sie können die standardmäßige Antwortdatei verwenden, oder Sie können die Vorlage Unattend.xml kopieren und ändern Sie ihn in Windows System Image Manager. Weitere Informationen dazu, wie Sie eine Antwortdatei ändern finden Sie die [Technische Referenz zu Windows System Image Manager (Windows SIM)](http://go.microsoft.com/fwlink/?LinkId=214570).

2.  Kopieren von Antwortdateien Unattend.xml Systemlaufwerk %\\entspannen\\Unattendfiles. Wenn Sie separate unbeaufsichtigte Dateien für bestimmte Bilder bereitstellen, benennen Sie jede neue Antwortdatei eindeutige bevor Sie es in Systemlaufwerk % kopieren\\entspannen\\Unattendfiles.

3.  Beim Hinzufügen von Bildern auf ein Projekt in der Windows-ASC, geben Sie den Pfad der Antwortdatei, die Sie mit diesem Bild verwenden möchten.

    **Wichtige**  
    Wenn Sie ein Bild mit einem System OEM Activation 3.0 (bei Zugriff 3.0) bereitstellen, verwenden Sie eine benutzerdefinierte Antwortdatei mit einem Product Key ein, der das Bild zugeordnet ist.

     

## <a name="a-href-idbkmk-assetprojectaadding-assets-to-a-project"></a><a href="" id="bkmk-assetproject"></a>Hinzufügen von Ressourcen zu einem Projekt


Ein Projekt ist eine Auflistung von Anlagen, die Sie bewerten möchten. Mehrere Computer und mehrere Bilder, die sind eine Teilmenge der allen Computern und Bilder, die Sie Ihrem Inventar hinzugefügt identifiziert. Die Computer, die Sie zum Projekt hinzufügen bare-Metal-Computern befinden, oder wenn Sie das Abbild auf dem Testcomputer aktualisieren möchten, wählen Sie auch die Bilder, die Sie auf jedem Computer anwenden möchten.

Wenn mehrere Personen mit verschiedenen Testcomputern und Bildern in der gleichen Server Inventar arbeiten, können Sie Projekte Partitionieren eines einzelnen Benutzers Workspace verwenden.

**So fügen Sie Objekte in ein neues Projekt hinzu**

1.  Klicken Sie in der Windows-ASC auf der Seite **Erste Schritte** auf **Neues Projekt erstellen**.

2.  Geben Sie in das Feld **Projektname** einen Namen für das Projekt ein.

3.  Geben Sie im Feld **Beschreibung** eine Beschreibung ein.

4.  Geben Sie im Feld **Stichwörter** Schlüsselwörter ein, und klicken Sie dann auf **Weiter**.

5.  Klicken Sie im Fenster **Computer in dieses Projekt einschließen auswählen,** klicken Sie auf **Hinzufügen** , und wählen Sie den Computer, den Sie verwenden möchten, in diesem Projekt enthalten, klicken Sie auf **OK**, und klicken Sie dann auf **Weiter**.

6.  Klicken Sie im Fenster **Bild Inventar** auf **Hinzufügen** , und wählen Sie Bilder, fügen Sie Ihrem Projekt, klicken Sie auf **OK**, und klicken Sie dann auf **Fertig stellen**.

    **Hinweis**  
    Wenn die Testcomputern bereits ein ausgeführten Betriebssystem verfügen, müssen Sie dem Projekt Bilder hinzufügen.

     

## <a name="a-href-idbkmk-assetjobaadding-assets-to-a-job"></a><a href="" id="bkmk-assetjob"></a>Hinzufügen von Anlagen mit einem Projekt


Ein Auftrag zuordnet Bewertung Objekte (einem Computer und einem Windows-Abbild). Ein Auftrag kann mehreren Computern, die entsprechenden Bilder und unbeaufsichtigte Antwortdateien und mehrere Bewertung enthalten. Sie können mithilfe der Objekte, die dem Projekt hinzugefügt wurden, verwenden Sie nur eine Teilmenge dieser Ressourcen oder führen Sie verschiedene Aufträge auf andere Objekte, die im Projekt verfügbar sind.

**Anlagen eines Auftrags hinzufügen und Bereitstellen eines Abbilds**

1.  Erstellen Sie in der Windows-ASC oder öffnen Sie ein Projekt.

2.  Unter **Einstellungen eines Auftrags für**auf **Übersicht**und stellen Sie sicher, dass das Kontrollkästchen **Bild anwenden** aktiviert ist.

3.  Wenn Sie übereinstimmenden Plug & Play einschleusen Treiber aus einer dynamische Treiber Bereitstellung Treiber während der Bereitstellung von Bild speichern möchten, wählen Sie **Dynamische Treiber-Bereitstellung**.

4.  Klicken Sie unter **Einstellungen eines Auftrags für**klicken Sie auf **Objekte**, und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

5.  Wählen Sie im Fenster **Wählen Evaluation-Objekte** die Computer, die Sie verwenden möchten, bewerten, klicken Sie auf **Weiter**, und klicken Sie dann auf **Fertig stellen**.

6.  Die Computer auf der rechten Seite des Windows ASC unter **Evaluation Anlagen**angezeigt werden. Wählen Sie einen Computer, klicken Sie auf **Das Bild ändern**, wählen Sie das Bild, das Sie auf diesem Computer anwenden möchten, und klicken Sie dann auf **OK**.

    **Hinweis**  
    Der Computer und die Architektur Bild müssen übereinstimmen, außer dass Sie ein Bild X86 basierend auf einem X64-basierten Computer bereitstellen auswählen können.

     

## <a name="next-steps"></a>Nächste Schritte


In den folgenden Schritten vorbereitet Windows PE Boot-Umgebung, einen bare-Metallen-Computer gestartet und das Inventar Windows Assessment Services hinzugefügt werden. Klicken Sie dann den Server Inventar der Computer, Bilder und Antwortdateien hinzugefügt und erstellt ein Projekt und ein Projekt, das diese Ressourcen enthalten. Im nächste Schritt wird Bewertung dem Projekt hinzufügen, konfigurieren Sie die Einstellungen Auftrag und Bewertung und klicken Sie dann auf ausführen. Bei der Ausführung des Auftrags wird auf dem Computer das Windows-Abbild bereitgestellt, vor dem Ausführen der Bewertung, die in den Auftrag enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Windows Assessment Services häufige Szenarien](windows-assessment-services-how-to-topics--wastechref.md)

 

 







