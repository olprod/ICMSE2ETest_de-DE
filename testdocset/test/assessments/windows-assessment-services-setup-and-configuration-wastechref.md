---
title: Windows-Assessment-Services-Setup und Konfiguration
description: Windows Assessment Services Einrichtung und Konfiguration
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f624a482-23c6-4f84-b16b-9431e7259ba8
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 817bdc80c5930c34d935e6196633c9ad10c8a1f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-services-setup-and-configuration"></a>Windows-Assessment-Services-Setup und Konfiguration


Bevor Sie beginnen, die Assessment Tools verwenden, müssen Sie Windows Assessment Services initialisieren. Mehrere Windows ASC Computer können mit dem gleichen Windows Assessment Services-Server kommunizieren. Zusätzliche Konfigurationsschritte enthalten Vorbereiten eines startbaren Windows PE USB-Laufwerks Inventar auf dem Testcomputer erfassen die kein ausgeführten Betriebssystem installiert sind. Bei Computern, die ein ausgeführten Betriebssystem installiert ist, wird das Skript CompleteDeployment für diese Computer Bestandsaufnahme hinzufügen bereitgestellt. Sie müssen auch Ihre Inventar Faktoren und Bilder hinzufügen. Die Verfahren in diesem Thema durchgehen dieser Prozess.

In diesem Thema:

-   [Beim Initialisieren des Windows-Assessment-Dienste](#configwas)

-   [Konfigurieren von Symbolen](#bkmk-wasc-symbols)

-   [Netzwerkadapter-Treiber Boot.wim hinzufügen](#bkmk-wac-nicdrivers)

-   [Vorbereiten der Test Computer Inventar Windows PE USB-Laufwerk](#prepwinpe)

-   [Hinzufügen von Testcomputern zu Ihrem Inventar](#addcomps)

-   [Hinzufügen von Treibern an den Store-Treiber](#adddrivers-was)

-   [Hinzufügen von Bildern und unbeaufsichtigte Dateien](#addimages-was)

## <a name="a-href-idconfigwasainitializing-windows-assessment-services"></a><a href="" id="configwas"></a>Beim Initialisieren des Windows Assessment Services


Zum Initialisieren von Windows Assessment Services müssen Sie Windows ASC vom Server ausführen.

**Wichtige**  
Port 8000 muss auf dem Server geöffnet werden, sodass Windows ASC- und der Testcomputer kommunizieren können. Windows Assessment Services Initialisierung Fügt eine Firewallregel um Port 8000 zu öffnen. Der Port wird nicht geöffnet werden, wenn es durch eine Gruppenrichtlinie blockiert wird.

 

1.  Klicken Sie auf **Start**, und geben Sie dann auf **Windows-Assessment-Services - Client** zum Suchen und Öffnen der Anwendung.

2.  Klicken Sie in das Textfeld Geben Sie den Namen des Servers, auf dem Windows Assessment Services installiert ist, und klicken Sie dann auf **OK**.

    Das erste Mal, das der Server initialisiert wurde, kann es etwa 15 bis 30 Minuten dauern. Es wird eine Meldung angezeigt, wenn der Server erfolgreich initialisiert wurde.

**Warnung**  
Bei Windows Assessment Services-Server-Konfiguration wird Windows Deployment Services (WDS) zur Liste Windows Assessment Services als der erste Anbieter in der Liste der Anbieter für Client Boot Services über das Netzwerk konfiguriert. Der erste Anbieter alle Clients effektiv Annahme von verweigert Anforderungen alle anderen Anbieter in der Liste. Es wird nicht empfohlen, dass Sie Windows Assessment Services auf einem Produktionsserver installieren.

 

## <a name="a-href-idbkmk-wasc-symbolsaconfiguring-symbols"></a><a href="" id="bkmk-wasc-symbols"></a>Konfigurieren von Symbolen


Einige Bewertung benötigen Zugriff auf Symbole. Wenn die Symbole nicht verfügbar sind, können die Ergebnisse Assessment falsch oder unvollständig sein. Internet-Verbindung und Zugriff auf Microsoft öffentlichen Symbolserver erfüllen diese Abhängigkeit. In anderen Fällen sich-Verbindung zum Internet nicht zur Verfügung, wie eine Lab-Umgebung befindet, können Sie Access Symbol mithilfe einer Antwortdatei während der Bereitstellung konfigurieren oder manuell konfiguriert werden können.

**Die Symbol-Umgebungsvariable so konfigurieren Sie mithilfe einer Antwortdatei**

1.  Kopieren Sie die Symbole für die Drittanbieter-Komponenten zu **Systemlaufwerk %\\entspannen\\Symbole\\% PROCESSOR\_ARCHITEKTUR %\\ ** auf dem Server mit Windows Assessment Services.

2.  Wenn der Testcomputer hat keinen Zugriff auf das Internet und Microsoft öffentliche Symbolserver kann nicht zugegriffen werden, verbinden Sie den Testcomputer mit dem Internet, und befolgen Sie die Anweisungen in [http://support.microsoft.com/kb/311503](http://go.microsoft.com/fwlink/p/?linkid=235360) , um die entsprechende Windows-Komponentensymbole herunterladen. Klicken Sie dann den Testcomputer wieder mit dem ursprünglichen Netzwerk verschieben und kopieren Sie die heruntergeladene Symbole auf **Systemlaufwerk %\\entspannen\\Symbole\\% PROCESSOR\_ARCHITEKTUR %\\ ** auf dem Server mit Windows Assessment Services.

3.  Ändern Sie die unbeaufsichtigte-Vorlagendatei für Bereitstellungsabbilder, klicken Sie unter **C:\\entspannen\\Skripts\\tempate**, durch Hinzufügen der Folgendes in der `<FirstLogonCommands>` Abschnitt. Aktualisieren Sie die Nummer der letzten Sequenz der synchronen Befehle.

    ``` syntax
    <SynchronousCommand>
    ```

    ``` syntax
       <Order>8</Order>
    ```

    ``` syntax
       <CommandLine>setx _NT_SYMBOL_PATH SRV*%systemdrive%\relax\symbols\%PROCESSOR_ARCHITECTURE%;%systemdrive%\relax\symbols\%PROCESSOR_ARCHITECTURE% /M</CommandLine>
    ```

    ``` syntax
       <Description>"Setting _NT_SYMBOL_PATH"</Description>
    ```

    ``` syntax
    </SynchronousCommand>
    ```

4.  Vor der Übernahme Inventar und Bilder auf den Testcomputern bereitstellen können, konfigurieren Sie den Symbolpfad in der Datei: \\ \\ &lt;Server&gt;\\entspannen\\Skripts\\Testmachine\\setenvironment.cmd.

5.  Nach dem Bereitstellen von Windows und Bestandsaufnahme der Testcomputer müssen Sie den Symbolpfad des richtigen in festlegen &lt;Systemlaufwerk&gt;:\\entspannen\\setenvironment.cmd.

Wenn Windows Assessment Services das Bild auf den Testcomputer bereitstellt, haben der Testcomputer müssen die \_NT\_SYMBOL\_PATH-Umgebungsvariablen.

Weitere Informationen zum Festlegen des Pfads Symbol und Symbole downloaden, finden Sie unter [MSDN: Unterstützung der Symbole](http://go.microsoft.com/fwlink/?LinkId=235359).

**So konfigurieren Sie manuell die Symbol-Umgebungsvariable**

1.  Öffnen Sie die Datei-Explorer rechten Maustaste auf **Computer**, und klicken Sie dann auf **Eigenschaften**.

2.  Klicken Sie im Fenster **Eigenschaften** auf **Erweiterte Systemeinstellungen**.

3.  Klicken Sie im Fenster **Systemeigenschaften** auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.

4.  Klicken Sie unter **Systemvariablen**auf **neu** , um die Symbol-Umgebungsvariable mithilfe einer der folgenden Pfade festlegen:

    -   **Verwenden Sie den öffentlichen Symbolserver (erfordert eine Internet-Verbindung)**

        Verbinden Sie den Computer mit dem Internet, damit es Microsoft Symbolserver zugreifen kann, und konfigurieren Sie die \_NT\_SYMBOL\_PATH-Umgebungsvariablen in http://msdl.microsoft.com/downloads/symbols Microsoft Symbolserver verwendet.

    -   **Verwenden Sie einen vernetzten Symbolpfad (erfordert eine LAN-Verbindung)**

        Herstellen einer Verbindung des lokalen Intranets mit dem Computer, und konfigurieren Sie anschließend die \_NT\_SYMBOL\_PATH-Umgebungsvariablen, einen Intranet-Symbolpfad zu verwenden.

    -   **Verwenden Sie einen Pfad lokales symbol**

        Laden Sie die Symbole auf dem Computer Windows Assessment Services Server, und zeigen auf dem Testcomputer diesen Speicherort durch Festlegen der \_NT\_SYMBOL\_PATH-Umgebungsvariablen, verwenden einen Pfad zu den Symbolen etwa auf dem Server ** \\ \\WASServer\\entspannen\\Symbole**.

Weitere Informationen dazu, wie Sie den Symbolpfad festzulegen, und Laden Sie Symbole, finden Sie unter [MSDN: Symbole Support](http://go.microsoft.com/fwlink/?LinkId=235359).

## <a name="a-href-idbkmk-wac-nicdriversaadding-network-adapter-drivers-to-bootwim"></a><a href="" id="bkmk-wac-nicdrivers"></a>Netzwerkadapter-Treiber Boot.wim hinzufügen


Fügen Sie der Windows-Bereitstellungsdienste verwendet Windows PE-Abbilder Netzwerkadapter (NIC)-Treiber hinzu. Dieser Schritt ist erforderlich, nur, wenn der Testcomputer Out-of-Box NIC-Treiber benötigen, sodass sind Netzwerkkonnektivität während Inventar oder das Windows-Abbild bereitgestellt wird. Sie benötigen die NIC-Treiber beim Starten eines bare-Metallen-Computers (ein Computer, für das Betriebssystem installiert ist) in Windows PE.

**Die boot.wim NIC-Treiber hinzu**

1.  Erstellen Sie einen Ordner für die NIC-Treiber, und kopieren Sie sie in den Ordner, auf dem Server. Wenn die Treiber auf einer Freigabe gespeichert sind, können Sie beispielsweise einen Befehl wie den folgenden verwenden:

    ``` syntax
    robocopy \\Server\share\drivers  C:\Drivers\amd64NIC /MIR
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

14. Klicken Sie im **Treiberpakets in Abbild hinzufügen** -Assistenten auf der Seite **Vorbereitung** auf **Weiter**.

15. Klicken Sie auf der Seite **Treiberpakete auswählen** klicken Sie auf **Paket-Klasse**, und klicken Sie dann auf **Bearbeiten**.

16. Löschen Sie alles mit Ausnahme von **Net**, und klicken Sie dann auf **OK**.

17. Im Assistenten **Treiberpakets in Abbild hinzufügen** klicken Sie auf **Suche für Pakete**, klicken Sie auf **Weiter**und klicken Sie dann auf **Weiter** .

18. Wenn die Treiber hinzugefügt werden, klicken Sie auf **Fertig stellen**.

Boot-Abbild verfügt nun über Out-of-Box-NIC-Treiber. Wiederholen Sie diese Schritte für jede Windows-Bereitstellungsdienste boot.wim Architektur.

## <a name="a-href-idprepwinpeapreparing-the-windows-pe-usb-drive-for-test-computer-inventory"></a><a href="" id="prepwinpe"></a>Vorbereiten der Test Computer Inventar Windows PE USB-Laufwerk


Um eine Inventur bare-Metal-Computern (ein Computer ohne Betriebssystem installiert), müssen Sie ein startbares USB-Laufwerk zum Starten des Computers und Hinzufügen der Kontaktobjekte zu den Bestand erstellen. Weitere Informationen dazu, wie Sie ein startbare Windows PE USB-Laufwerk vorbereiten, finden Sie unter [Exemplarische Vorgehensweise: Installieren von Windows PE auf CD, USB Flash-Laufwerk oder USB-Festplatte](http://go.microsoft.com/fwlink/p/?linkid=219488). Die exemplarischen Vorgehensweise erstellt startbare Medien mithilfe von standardmäßigen Windows PE-Abbild (wird) ohne anpassen. Bevor Sie das startbare USB-Laufwerk für Inventar verwenden, müssen Sie die Datei RelaxWinPE.wim in den Quellordner auf das USB-Laufwerk kopieren.

**Wichtige**  
Um X86-basierte Testcomputern Bestandsaufnahme, müssen Sie ein X86-basierte Windows PE-Abbild verwenden. Wenn Testcomputern AMD64-basierten Bestandsaufnahme, müssen Sie ein Bild AMD64-basierten Windows PE verwenden. Dieses Verfahren wird ein Bild X86-basierte verwendet. Wenn Ihre Testcomputern X86 und AMD64-basierten sind, erstellen Sie ein USB-Laufwerk für jede Architektur.

 

**Um die Datei boot.wim durch Windows AS wird die Datei zu ersetzen**

1.  Geben Sie auf dem Referenzcomputer, auf dem Sie die Windows PE-Buildumgebung erstellt haben folgenden Befehl ein:

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x86\Images\RelaxWinPE.wim c:\winpe_x86\media\sources\boot.wim
    ```

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x64\Images\RelaxWinPE.wim c:\winpe_x64\media\sources\boot.wim
    ```

2.  Wiederholen Sie den vorherigen Schritt, um ein USB-Laufwerk für jede Architektur zu erstellen, die für den Testcomputern benötigt.

    **Wichtige**  
    Um X86-basierte Testcomputern Bestandsaufnahme, müssen Sie ein X86-basierte Windows PE-Abbild verwenden. Wenn Testcomputern AMD64-basierten Bestandsaufnahme, müssen Sie ein Bild AMD64-basierten Windows PE verwenden.

     

Nun, da das startbare Windows PE USB-Laufwerk vorbereitet wird und NIC-Treiber vorhanden sind, können Sie Inventar auf Ihrem Server hinzufügen und fügen Sie sie in Ihre Projekte und Projekte.

## <a name="a-href-idaddcompsaadding-test-computers-to-your-inventory"></a><a href="" id="addcomps"></a>Hinzufügen von Testcomputern zu Ihrem Inventar


Sie können bare-Metal-Computern (Computer ohne ein ausgeführtes Betriebssystem) hinzufügen, und Computer, auf denen ein ausgeführtes Betriebssystem Windows Assessment Services auch eine Inventur, damit Sie die Tools zur Bewertung der bewerten können diese Computer verwenden können. Wenn auf der Testcomputer ein ausgeführten Betriebssystem verfügt, verwenden Sie das USB-Laufwerk starten Sie den Computer und Hinzufügen der Kontaktobjekte zu den Windows-Assessment-Services-Inventar. Bei der Testcomputer ein ausgeführten Betriebssystem verfügt, mithilfe des Skripts Windows Assessment Services es das Inventar Windows Assessment Services hinzufügen.

**Warnung**  
Sie sollten nicht gleichzeitig einen Testcomputer in mehreren Windows Assessment Services Server Bestände einschließen. Wenn ein Testcomputer in mehreren Windows Assessment Services Server Bestände angezeigt wird, wird eine Racebedingung zwischen den Windows-Bereitstellungsdienst-Instanzen auf jedem Server. Wenn Sie aus einem Inventar in eine andere in der Windows-Assessment-Services - Client (Windows ASC), einen Testcomputer verschieben müssen Computer Vermögenswerts im ersten Windows Assessment Services Bestand löschen und dann das Inventar auf dem neuen Windows Assessment-Services-Server hinzuzufügen.

 

**Zum Hinzufügen von Computern zum Bestandsaufnahme bare-metal**

1.  Legen Sie das USB-Laufwerk, in dem Testcomputer.

2.  Aktivieren Sie auf dem Computer ein, und drücken Sie die Taste, die das Startvolumes Auswahlmenü für den Computer, beispielsweise Esc wird geöffnet.

3.  Wählen Sie das USB-Laufwerk als Boot-Gerät.

    Beim Neustart des Computers bieten Sie die folgende Informationen:

    -   Name des Computers. Der Namen des Computers muss nur alphanumerische Zeichen und Bindestriche enthalten. Enthält der Namen des Computers ein Unterstrich oder andere erweiterten Zeichen enthalten, kann der Computer nicht über Domain Name System (DNS) sichtbar sein. Der Namen des Computers muss 15 Zeichen oder weniger.

    -   Standort des Computers. Der Speicherort der Computer muss 78 Zeichen oder weniger.

    -   Gibt an, ob Sie die Treiber Aufräumen ausführen möchten. Treiber, die auf dem Computer, den Windows-Assessment-Services-Treiberspeicher kopiert.

4.  Entfernen Sie das USB-Laufwerk aus dem Testcomputer. Der Computer wird neu gestartet.

    **Hinweis**  
    Wenn Sie Bilder mithilfe der Windows-Assessment-Dienste bereitstellen, sollten die Startreihenfolge im BIOS festlegen, sodass Systemanalyse vor dem Start Execution Environment (PXE) in der Startreihenfolge erste ist. Auf diese Weise müssen Sie manuell drücken die Tastenkombination Startreihenfolge und select Netzwerkstart, bevor ein Auftrag startet.

     

5.  Öffnen Sie die ASC Windows im Menü **Start** . Stellen Sie sicher, dass die richtige Anzahl von Computern auf Ihrem Server Inventar hinzugefügt wurden, auf der Seite **Erste Schritte** .

**Zum Hinzufügen von laufenden Computers Artikel**

1.  Melden Sie sich an den Windows-Assessment-Services-Server, auf einem Testcomputer ausgeführt wird. Geben Sie beispielsweise an der Befehlszeile:

    ``` syntax
    Net use \\<servername>\relax /u:localadmin Pass.word
    ```

    **Hinweis**  
    Dieses Konto und Kennwort werden während der Installation von Windows Assessment Dienste und die Initialisierung eingerichtet. Dies ist keinem Administratorkonto an.

     

2.  Löschen Sie auf dem Testcomputer C:\\entspannen Ordner, sofern vorhanden.

3.  Führen Sie von einer Eingabeaufforderung mit erhöhten Rechten CompleteDeployment.cmd. Ist der vollständige Pfad für den Befehl \\ \\ &lt;Servername&gt;\\entspannen\\Skripts\\TestMachine\\CompleteDeployment.cmd.

    Eine Beschreibung der Zweck des Skripts wird im Eingabeaufforderungsfenster angezeigt.

4.  Drücken Sie die EINGABETASTE, um den Vorgang fortzusetzen. Der Computer wird neu gestartet, wenn sie den Bestand hinzugefügt wird.

    **Warnung**  
    Enthält der Namen des Computers einen Unterstrich, kann es nicht erreichbar über DNS, RFC erfüllt sein. In diesem Fall wird nicht der Inventar der Computer hinzugefügt werden. Out-of-Box-Experience (OOBE) ermöglicht Computernamen mit einem Unterstrich, aber nicht Windows Assessment Services Inventar.

     

5.  Öffnen Sie die ASC Windows im Menü **Start** . Stellen Sie sicher, dass die richtige Anzahl von Computern auf Ihrem Server Inventar hinzugefügt wurden, auf der Seite **Erste Schritte** .

## <a name="a-href-idadddrivers-wasaadding-drivers-to-the-driver-store"></a><a href="" id="adddrivers-was"></a>Hinzufügen von Treibern an den Store-Treiber


Wenn Sie Ihre Inventar ausgeführten Computer hinzufügen, werden die Out-of-Box-Treiber vom Computer erfasst und gespeichert auf dem Server Windows Assessment Services bei Systemlaufwerk %\\entspannen\\Treiber\\Computername%. In diesem Fall nur, wenn Sie einen Computer auf den Inventoty hinzufügen, das ein ausgeführten Betriebssystem verfügt. Es wird nicht auf bare-Metal-Computern passieren, die Sie den Bestand über das Windows PE USB-Laufwerk hinzufügen. Im folgenden Verfahren fügen Sie diese Treiber an der Windows-Bereitstellungsdienste Treiber speichern, damit sie für das Einfügen von Treibern während der Bild-Bereitstellung verfügbar sind.

**Warnung**  
Die folgenden Schritte gelten nur für Windows Server 2012. Wenn Sie Windows Server 2008 R2 verwenden, müssen Sie die Treiber in das Bild vor der Bereitstellung einfügen, da dynamische Treiber Bereitstellung in Windows-Bereitstellungsdienste unter Windows Server 2008 R2 nicht unterstützt wird.

 

**Zum Importieren der Treiber in der Treiberspeicher**

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Windows-Bereitstellungsdienste**.

2.  Erweitern Sie den Knoten **Server** und dann der Name Ihres Servers.

3.  Mit der rechten Maustaste **Treiber**, und klicken Sie dann auf **Paket hinzufügen**.

4.  Im Assistenten Treiberpakets hinzufügen klicken Sie auf **allen Treiberpaketen für aus einem Ordner auswählen**, und klicken Sie dann auf **Durchsuchen**.

5.  Navigieren Sie zum Laufwerk C:\\entspannen\\Treiberordner, und klicken Sie dann auf **OK**.

6.  Klicken Sie im Paket hinzufügen-Assistenten auf **Weiter**.

7.  Klicken Sie auf der Seite **Verfügbare Treiberpakete** auf **Weiter**.

8.  Klicken Sie auf der Seite **Zusammenfassung** auf **Weiter**.

9.  Wenn die Treiber an den Treiber Store kopiert werden, klicken Sie auf **Weiter**.

10. Klicken Sie auf der Seite **Treiber-Gruppen** auf **eine vorhandene Treibergruppe auswählen**, stellen Sie sicher, dass **DriverGroup1** ausgewählt ist, und klicken Sie dann auf **Weiter**.

11. Klicken Sie auf **Fertig stellen**.

## <a name="a-href-idaddimages-wasaadding-images-and-unattended-answer-files"></a><a href="" id="addimages-was"></a>Hinzufügen von Bildern und unbeaufsichtigte Dateien


Sie müssen die Windows imaging (WIM-Dateien) für die Freigabe Bild kopieren, bevor Sie diese in der Inventardatenbank importieren und sie für die Bereitstellung verwenden.

**Zum Hinzufügen von Bildern in der Images gemeinsam genutzt und Bestandsdaten**

1.  Kopieren Sie auf dem Server Windows Assessment Services WIM-Dateien nach C:\\entspannen\\Bilder.

    **Hinweis**  
    Der Pfad des Bildes darf keine Leerzeichen enthalten.

     

2.  Diese Bilder werden in die Windows Assessment Services Bild Serverfreigabe, aber sie noch nicht in der Inventardatenbank importiert wurden. Verwenden Sie zum Importieren von Bildern in der Inventardatenbank eine der folgenden Methoden:

    -   Klicken Sie auf der Seite **Erste Schritte** klicken Sie auf **jetzt Bilder importieren**, wählen Sie die Bilder, klicken Sie auf **Importieren**, und klicken Sie dann auf **OK**.

    -   In der ASC Windows im Menü **Server** auf **Inventar Manager**, klicken Sie auf die Registerkarte **Bilder** und klicken Sie dann auf **Hinzufügen**.

**So fügen eine Freigabe Antwortdateien hinzu**

1.  Eine standardmäßige Antwortdatei für jede unterstützte Architektur wird bereitgestellt, bei Systemlaufwerk %\\entspannen\\Skripts\\Vorlagen. Sie können die standardmäßige Antwortdatei verwenden, oder Sie können die Vorlage Unattend.xml kopieren und ändern Sie ihn in Windows System Image Manager. Weitere Informationen dazu, wie Sie eine Antwortdatei ändern finden Sie die [Technische Referenz zu Windows System Image Manager (Windows SIM)](http://go.microsoft.com/fwlink/?LinkId=214570).

2.  Kopieren Sie die Antwortdateien Unattend.xml Systemlaufwerk %\\entspannen\\Unattendfiles. Wenn Sie separate unbeaufsichtigten Antwortdateien für bestimmte Bilder bereitstellen, übergeben Sie einen eindeutigen Namen an jede neue Antwortdatei bevor Sie es in Systemlaufwerk % kopieren\\entspannen\\Unattendfiles.

3.  Nachdem Sie ein Projekt in der Windows-ASC Bilder hinzugefügt haben, können Sie den Pfad der Antwortdatei angeben, die Sie mit diesem Bild verwenden möchten. Klicken Sie im Menü **Server** auf **Bestand verwalten**. Ändern Sie den **Pfad für die unbeaufsichtigte Installation**, auf der Registerkarte **Bild** .

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

[Installieren von Windows-Assessment-Services](installing-windows-assessment-services-wastechref.md)

 

 







