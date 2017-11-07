---
title: Problembehandlung bei Windows Assessment-Services
description: Problembehandlung bei Windows Assessment Services
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f0a1c2cb-9566-4451-a201-5dab89c7a0b9
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 4c96ec15974a40b3a6684b895c64b61fe92e335c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="troubleshooting-windows-assessment-services"></a>Problembehandlung bei Windows Assessment Services


Die folgenden Informationen können Sie behandeln häufig auftretender Probleme helfen.

Dieses Thema enthält:

-   [Protokolldateien](#bkmk-ts-logfiles)

-   [Richten Sie einen Symbolserver](#bkmk-ts-symbolserver)

-   [Keine Verbindung mit Server herstellen](#bkmk-ts-unableconnect)

-   [Computer in Inventar ist bereits vorhanden.](#bkmk-ts-computerexists)

-   [Schaltfläche "ausführen" ist nicht verfügbar](#bkmk-ts-runbuttondimmed)

-   [Bestandsaufnahme der Computer fehlerhaft mit WS\_E\_VORGANG\_ZEIT\_SKALIEREN](#bkmk-ts-inventoryfails)

-   [Bereitstellungsfehler Bild haben nicht ausreichend Informationen auf der Seite Überwachung.](#bkmk-ts-deploymentfails)

-   [DISM Fehler während der Computer Inventar](#bkmk-ts-dismerr)

-   [Testcomputern müssen einem neuen Image versehen werden, wenn Sie den Namen des Servers ändern](#bkmk-ts-reimagetestcomp)

-   [Fehler "Der Computer ist nicht erreichbar"](#bkmk-ts-machinereach)

-   [Ausführen von Windows Assessment Services - Clients von einem anderen Server als Windows Assessment Services-Servers](#bkmk-ts-msmq)

-   [Der Ordner speichert enthält keine Abbilddateien](#bkmk-ts-dumps)

## <a name="a-href-idbkmk-ts-logfilesalog-files"></a><a href="" id="bkmk-ts-logfiles"></a>Protokolldateien


-   Protokolldateien werden auf den Server kopiert, wenn Sie die Server-Inventar Computer hinzufügen. Sie sind gespeichert unter **C:\\entspannen\\Protokolle**.

-   Ein Serverprotokoll werden Ereignisse des Windows-Assessment-Services erfasst. Diese Protokolldatei finden Sie unter **C:\\Windows\\Temp\\relaxservice.tracelistener.Tracing**.

-   Fehler, die von der Benutzeroberfläche angezeigt werden können, in der Ereignisanzeige auf dem Clientcomputer unter **Anwendungs- und Dienstprotokolle** - **Windows Assessment Services Client**. Die Protokolldatei ist eine ETL-Datei befindet sich unter **%systemroot%\\system32\\Winevt\\Protokolle\\Windows Assessment Services Client.evtx**.

-   Bild Bereitstellungsprotokolle (Windows PE) werden von den Testcomputern auf kopiert **Systemlaufwerk %\\entspannen\\Protokolle**

-   Windows Server 2012, Windows-Bereitstellungsdienste (Windows DS) Probleme finden Sie in den Ereignisdetails Viewer unter **Anwendungs- und Dienstprotokolle** -**Microsoft** -**Windows** - **Windows Deployment Services-Diagnose**.

-   Unter Windows Server 2008 R2 müssen Sie Windows DS-Protokollierung aktivieren, durch Folgendes festlegen:

    -   **HKLM\\System\\CurrentControlSet\\Services\\WDSServer\\Anbieter\\WDSPXE! TracingDisabled auf 0**

    -   **HKLM\\Software\\Microsoft\\Tracing\\WDSServer! EnableFileTracing auf 1**

    WDS Protokoll wird zur generiert **%systemroot%\\Ablaufverfolgung\\wdsserver.log**.

-   WinRM-Protokoll finden Sie in den Ereignisdetails Viewer unter **Anwendungs- und Dienstprotokolle** -**Microsoft** -**Windows** -**Windows Remote Management**.

-   Wenn die Ergebnisse nicht auf den Server kopiert werden, können Sie auf dem Testcomputer suchen. Die Protokolldatei ganz Systemlaufwerk %\\entspannen\\&lt;GUID&gt;\\Auftrag\\results.log verweist auf die Ergebnisordner, in dem die Ergebnisse gespeichert wurden.

## <a name="a-href-idbkmk-ts-symbolserveraset-up-a-symbol-server"></a><a href="" id="bkmk-ts-symbolserver"></a>Richten Sie einen Server Symbol


Einige Bewertung benötigen Zugriff auf Symbole. In einigen Fällen kann die Informationen in den Ergebnissen zur Bewertung falsch oder fehlenden Informationen, wenn ein Symbol nicht verfügbar ist. In vielen Fällen ist diese Abhängigkeit vom Internet Connectivity und Zugriff auf den Microsoft-Server öffentliche Symbole erfüllt. In anderen Fällen, in dem-Verbindung zum Internet nicht wie eine Lab-Umgebung verfügbar ist, können einen privaten Symbolserver einrichten oder installieren die Symbole auf dem lokalen Computer aus, um die Vorteile der der Bewertungsfragen abzurufen.

**So legen Sie die Umgebungsvariable Symbole auf einem Testcomputer fest**

1.  Öffnen Sie die Datei-Explorer rechten Maustaste auf **Computer**, und wählen Sie **Eigenschaften**aus.

2.  Klicken Sie im Fenster Eigenschaften auf **Erweiterte Systemeinstellungen**.

3.  Klicken Sie im Fenster Systemeigenschaften auf der Registerkarte **Erweitert** auf **Umgebungsvariablen**.

4.  Klicken Sie unter Systemvariablen auf **neu** , um die Symbole Umgebungsvariable mithilfe einer der folgenden Pfade festlegen:

    1.  Verwenden Sie den öffentlichen Symbolserver (erfordert die Verbindung zum Internet)

        Verbinden Sie den Computer mit dem Internet, sodass es auf den Microsoft Symbolserver zugreifen kann, und konfigurieren Sie die \_NT\_SYMBOL\_PATH-Umgebungsvariablen Microsoft Symbolserver in einer **http://msdl.microsoft.com/downloads/symbols**verwendet.

    2.  Verwenden Sie einen Netzwerkpfad-verbundenen Symbole (LAN-Verbindung erforderlich)

        Herstellen einer Verbindung des lokalen Intranets mit dem Computer, und konfigurieren Sie anschließend die \_NT\_SYMBOL\_PATH-Umgebungsvariablen, einen Intranet Symbole Pfad zu verwenden.

    3.  Verwenden Sie einen Pfad lokale Symbole

        Die Symbole auf der Windows Assessment Services Servercomputer herunterladen, und zeigen auf dem Testcomputer diesen Speicherort durch Festlegen der \_NT\_SYMBOL\_PATH-Umgebungsvariablen einen Pfad zu den Symbolen auf den Server verwenden, wie z. \\ \\WASServer\\entspannen\\Symbole.

**So richten Sie interne Symbole ein**

1.  Installieren Sie der ADK und initialisieren Sie WAS zu.

2.  Rufen Sie eine IPSec-Grenze-Ausnahme für den WAS-Server-Computer. Dadurch wird sichergestellt, dass Testcomputern WAS die keine Termine Freigabe zugreifen können.

3.  Fügen Sie den Servercomputer WAS zur Domäne.

4.  Fügen Sie einen Domänenbenutzer an den Servercomputer WAS in der Gruppe Administratoren, die Zugriff auf interne Symbolserver verfügt.

5.  Beenden Sie den Dienst WAS durch den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten ausführen:

    **Net Stop WASSVC**

6.  Ändern des Anmeldekontos in die neue Domänenkonto.

7.  Führen den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten ersetzen &lt; *Pfad zu internen Symbolen* &gt; durch den entsprechenden Pfad:

    **SETX\_NT\_SYMBOL\_PFAD \\ \\ &lt;Pfad zu internen Symbolen&gt; /m**

8.  Starten Sie den Computer neu.

Weitere Informationen zum Festlegen des Pfads Symbole und Symbole downloaden, finden Sie unter [MSDN: Symbole Support](http://go.microsoft.com/fwlink/?LinkId=235359). Informationen zum Beheben von Problemen mit fehlende Symbolen, finden Sie unter [Depth Analysis Probleme](common-in-depth-analysis-issues.md#missingsymbols).

## <a name="a-href-idbkmk-ts-unableconnectaunable-to-connect-to-server"></a><a href="" id="bkmk-ts-unableconnect"></a>Keine Verbindung mit Server herstellen


Wenn die Windows-Assessment-Services - Client (Windows ASC) auf dem Server herstellen kann, erhalten Sie die folgende Fehlermeldung angezeigt:

*Es konnte keine Verbindung mit dem Remoteserver: ein Verbindungsversuch ist fehlgeschlagen, da die verbundene Partei nach einer bestimmten Zeitspanne nicht ordnungsgemäß reagiert hat, oder eine hergestellte Verbindung fehlgeschlagen, da der verbundene Host hat nicht geantwortet hat.*

Überprüfen Sie den Status des Servers mit dem Befehl **sc Query Wassvc** . Wenn der Server nicht ausgeführt wird, starten Sie den Dienst mit dem Befehl **net Start Wassvc** an.

**Warnung**  
Der sc Abfragebefehl funktioniert nur, wenn es auf dem Server mit Windows Assessment Services ausgeführt wird.

 

## <a name="a-href-idbkmk-ts-computerexistsacomputer-already-exists-in-inventory"></a><a href="" id="bkmk-ts-computerexists"></a>Computer in Inventar ist bereits vorhanden.


Wenn Sie die folgende Meldung angezeigt, vorhanden der Testcomputer in den Bestand Windows Assessment Services bereits:

*Führen Sie manuell alle Szenarien. Drücken Sie neu starten, beenden*

Wenn Sie den Computereintrag, klicken Sie im Server-Inventar nicht angezeigt werden, schließen Sie und erneut öffnen Sie das Fenster, um den Inhalt zu aktualisieren.

## <a name="a-href-idbkmk-ts-runbuttondimmedarun-button-is-unavailable"></a><a href="" id="bkmk-ts-runbuttondimmed"></a>Schaltfläche "ausführen" ist nicht verfügbar


Wenn die Schaltfläche **Ausführen** nicht verfügbar ist, stellen Sie sicher, dass bestimmte Computer und Bildern in den Details der **Ressourcen** ausgewählt haben. Wenn Sie bestimmte Computer und Bilder ausgewählt haben, aber keine Bewertung auf der Seite **Ergebnisse** angezeigt, schließen und dann das aktuelle Projekt neu erstellen.

## <a name="a-href-idbkmk-ts-inventoryfailsainventorying-test-machine-fails-with-wseoperationtimedout"></a><a href="" id="bkmk-ts-inventoryfails"></a>Bestandsaufnahme Test Computer funktioniert nicht mit WS\_E\_VORGANG\_ZEIT\_SKALIEREN


Wenn Sie die folgende Fehlermeldung angezeigt:

``` syntax
Error updating machine configuration in RelaxServer. Please check that the server is available and try again later. (ErrorCode:-2143485946)
```

Im Fehlerprotokoll am **C:\\keine Termine\\CompleteDeployment.log** für zusätzliche Fehlerdetails und erneut **CompleteDeployment.cmd**ausführen.

## <a name="a-href-idbkmk-ts-deploymentfailsaimage-deployment-failures-dont-have-enough-information-on-the-monitoring-page"></a><a href="" id="bkmk-ts-deploymentfails"></a>Bereitstellungsfehler Bild haben nicht ausreichend Informationen auf der Seite Überwachung.


**Fehlercode: Beenden des Szenarios bereitstellen: Fehler-ID = 2**

Verwenden Sie ein Bild nicht unterstütztes Format, die Antwortdatei unbeaufsichtigte Installation ist nicht vorhanden oder die Bilddatei ist nicht vorhanden.

**Fehlercode: Beenden des Szenarios bereitstellen: Fehler-ID = 38**

Die Datei ist beschädigt.

**Fehlercode: Beenden des Szenarios bereitstellen: Fehler-ID = 87**

BCDboot Fehler beim Aktualisieren des BCD-Speichers. Dies gilt nur für einige UEFI-Computerprototypen. Nicht umgangen werden zu diesem Zeitpunkt.

**Fehlercode: Beenden des Szenarios bereitstellen: Fehler-ID = 193**

BCDboot Fehler beim Aktualisieren des BCD-Speichers. Ein Bild des inkompatible Architektur wurde auf einem Testcomputer angewendet.

**Fehlercode: Beenden des Szenarios bereitstellen: Fehler-ID = 2147024809**

Diskpart konnte keine Festplattenlaufwerk gefunden, mit denen ein Bild angewendet werden konnte.

## <a name="a-href-idbkmk-ts-dismerradism-error-during-computer-inventory"></a><a href="" id="bkmk-ts-dismerr"></a>DISM Fehler während der Computer Inventar


Wenn Sie den folgenden Fehler beim Nachrichtenempfang Inventar eines Computers erhalten haben, müssen Sie den X86 verwenden Windows PE-Abbilds für das startbare USB-Laufwerk, das Sie für Inventar erstellt haben.

``` syntax
An error occurred. You cannot service an x86-based image from an x64-based host that does not support WOW64. Try the operation again from a host environment that supports WOW64. 
Error running Driver Scavenge. ErrorCode 193.
```

Wenn Sie einen Computer Bestandsaufnahme, Treiberinformationen gesammelt und gespeichert unter ** &lt;Systemlaufwerk %\\entspannen\\Treiber** DISM verwenden. DISM den Treiber – Wartung Befehl kann nicht ausgeführt werden auf eine X86 Windows image, von einer Windows PE X64-Umgebung. Weitere Informationen finden Sie unter DISM unterstützte Plattformen.

**Lösung**

Verwenden Sie ein startbares USB-Laufwerk für X86 erstellt (oder erstellen) Architektur. Weitere Informationen finden Sie unter [Windows Assessment Services Einrichtung und Konfiguration](windows-assessment-services-setup-and-configuration-wastechref.md).

## <a name="a-href-idbkmk-ts-reimagetestcompatest-computers-must-be-reimaged-if-you-change-the-server-name"></a><a href="" id="bkmk-ts-reimagetestcomp"></a>Testcomputern müssen einem neuen Image versehen werden, wenn Sie den Namen des Servers ändern


Wenn Sie den Windows-Assessment-Services-Server umbenennen und erneut zu initialisieren, müssen Sie erneut Windows bereitstellen auf dem Testcomputer vor dem Ausführen von zusätzlichen Bewertung.

## <a name="a-href-idbkmk-ts-machinereachamachine-not-reachable-errors"></a><a href="" id="bkmk-ts-machinereach"></a>Fehler "Der Computer ist nicht erreichbar"


DNS Auflösen von Computernamen Test bei der Bewertung Remote ausführen, abhängig Windows Assessment Services. Wenn DNS doppelte Einträge für den gleichen Namen, eine von einem Computer der Domäne beitreten und anderen von einem Arbeitsgruppencomputer aufweist, wird Windows und WinRM Computer auswählen, dem in DNS aufgelöst wird.

Wenn Sie eine Fehlermeldung, die erhalten "Computer nicht erreichbar" enthält, überprüfen Sie die DNS-Einträge für Duplikate an.

**Hinweis**  
Der Namen des Computers muss nur alphanumerische Zeichen und Bindestriche enthalten. Enthält der Namen des Computers ein Unterstrich oder andere erweiterten Zeichen enthalten, kann der Computer nicht über Domain Name System (DNS) sichtbar sein.

 

## <a name="a-href-idbkmk-ts-msmqarunning-windows-asc-from-a-server-other-than-the-windows-assessment-services-server"></a><a href="" id="bkmk-ts-msmq"></a>Ausführen von Windows ASC über eines anderen Servers als Windows-Assessment-Services-Servers


Wenn Sie Windows ASC auf einem WindowsServer ausgeführt werden, und Sie verfügen nicht über Windows Assessment Services auf diesem Server installiert ist, können Pushbenachrichtigungen nicht in Windows ASC aktivieren, wenn Sie es starten.

**Dieses Problem zu umgehen**

Aktivieren Sie auf dem Server, auf dem Windows ASC installiert ist die optionale Komponente MSMQ-Server mithilfe des folgenden Befehls DISM aus einer Eingabeaufforderung mit erhöhten Rechten.

``` syntax
Dism /Online /Enable-Feature:MSMQ-Server
```

Oder führen Sie Windows ASC auf einem Clientcomputer oder auf dem gleichen Server, auf dem Windows Assessment Services installiert ist.

## <a name="a-href-idbkmk-ts-dumpsathe-dumps-folder-does-not-contain-any-dump-files"></a><a href="" id="bkmk-ts-dumps"></a>Der Ordner speichert enthält keine Abbilddateien


Standardmäßig werden nach der Ausführung der Bewertung Dump-Dateien auf dem Server nicht kopiert. Wenn Sie speichert für Assessment Läufe erfassen möchten, bearbeiten Sie &lt;keine Termine Directory&gt;\\Skripts\\Kabelbäume\\Axe\\CompleteAssessment.cmd und ändern Sie den Wert für ein\_Copydumpstoserver auf "true". Standardmäßig ist dieser Wert "false".

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

 

 







