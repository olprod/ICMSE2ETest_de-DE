---
title: "Hinzufügen von Ressourcen zu Windows Assessment Services Inventar"
description: "Hinzufügen von Ressourcen zu Windows Assessment Services Inventar"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bddc94de-3531-4de9-a1bc-5ae359d1f6c6
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 759254f00694edb9949121925739d5ce17ec2820
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-assets-to-windows-assessment-services-inventory"></a>Hinzufügen von Ressourcen zu Windows Assessment Services Inventar


In diesem Thema wird beschrieben, wie die Windows Assessment Services Inventar Objekte wie Computer, Windows-Abbilder und unbeaufsichtigte Dateien hinzugefügt. Klicken Sie dann können die Tools zur Bewertung für die Bereitstellung und die Bewertung von verschiedenen Computern und Windows-Bilder, die sich in der Inventar. Treiber werden an den Windows-Bereitstellungsdienst-Treiber Store hinzugefügt, damit sie in das Windows-Abbild während der Bereitstellung eingefügt werden können.

In diesem Thema:

-   [Hinzufügen von Testcomputern zu Ihrem Inventar](#addcomps)

-   [Hinzufügen von Treibern zu Driver store](#adddrivers-was)

-   [Hinzufügen von Bildern und unbeaufsichtigte Dateien](#addimages-was)

## <a name="a-href-idaddcompsaadding-test-computers-to-your-inventory"></a><a href="" id="addcomps"></a>Hinzufügen von Testcomputern Ihrem Inventar


Sie können bare-Metal Computern (Computer, die ein ausgeführten Betriebssystem nicht verfügbar) hinzufügen und Computer, auf denen ein ausgeführtes Betriebssystem auf dem Windows Assessment Services Inventar. Klicken Sie dann können die Tools zur Bewertung der diese Computer bewerten. Bei der Testcomputer ein ausgeführten Betriebssystem verfügt, mithilfe des Skripts Windows Assessment Services es das Inventar hinzufügen. Bei der Testcomputer kein ausgeführten Betriebssystem, das USB-Laufwerk, starten Sie den Computer, und fügen Sie sie den Bestand verwenden. Weitere Informationen zum Hinzufügen von bare-Metal-Computers zu Inventar finden Sie unter [Prepare to deploy und Bewerten von einem bare-Metal-Computer](prepare-to-deploy-and-assess-a-bare-metal-computer.md).

**Warnung**  
Sie sollten nicht gleichzeitig einen Testcomputer in mehreren Windows Assessment Services Server Bestände einschließen. Wenn ein Testcomputer in mehreren Windows Assessment Services Server Bestände angezeigt wird, wird eine Racebedingung zwischen den Windows-Bereitstellungsdienst-Instanzen auf jedem Server. Wenn Sie aus einem Inventar in eine andere in der Windows-Assessment-Services - Client (Windows ASC), einen Testcomputer verschieben müssen Computer Vermögenswerts im ersten Windows Assessment Services Bestand löschen und dann das Inventar auf dem neuen Windows Assessment-Services-Server hinzuzufügen.

 

**Die Inventar ausgeführten Computer hinzu**

1.  Melden Sie sich an den Windows-Assessment-Services-Server, auf einem Testcomputer ausgeführt wird. Geben Sie zum Beispiel an einer Eingabeaufforderung:

    ``` syntax
    Net use \\<servername>\relax /u:localadmin Pass.word
    ```

    **Hinweis**  
    Dieses Konto und Kennwort werden während der Installation von Windows Assessment Dienste und die Initialisierung eingerichtet. Dies ist keinem Administratorkonto an.

     

2.  Löschen Sie auf dem Testcomputer C:\\entspannen Ordner, sofern vorhanden.

3.  Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten CompleteDeployment.cmd ein. Ist der vollständige Pfad des Befehls \\ \\ * &lt;Servername&gt;*\\entspannen\\Skripts\\TestMachine\\ CompleteDeployment.cmd.

    Eine Beschreibung der Zweck des Skripts wird im Eingabeaufforderungsfenster angezeigt.

4.  Drücken Sie die EINGABETASTE, um den Vorgang fortzusetzen. Der Computer wird neu gestartet, wenn sie den Bestand hinzugefügt wird.

    **Warnung**  
    Enthält der Namen des Computers einen Unterstrich, kann es nicht erreichbar über DNS, RFC erfüllt sein. In diesem Fall wird nicht der Inventar der Computer hinzugefügt werden. Out-of-Box-Experience (OOBE) ermöglicht Computernamen mit einem Unterstrich, aber nicht Windows Assessment Services Inventar.

     

5.  Öffnen Sie die ASC Windows im Menü **Start** . Stellen Sie sicher, dass die richtige Anzahl von Computern auf Ihrem Server Inventar hinzugefügt wurden, auf der Seite **Erste Schritte** .

## <a name="a-href-idadddrivers-wasaadding-drivers-to-the-driver-store"></a><a href="" id="adddrivers-was"></a>Hinzufügen von Treibern zu Driver store


Wenn Sie Ihre Inventar ausgeführten Computer hinzufügen, werden die Out-of-Box-Treiber vom Computer erfasst und gespeichert auf dem Server Windows Assessment Services bei Systemlaufwerk %\\entspannen\\Treiber\\Computername%. In diesem Fall nur, wenn Sie einen Computer der Bestand hinzufügen, das ein ausgeführten Betriebssystem verfügt. Es wird nicht auf bare-Metal-Computern passieren, die Sie den Bestand über das Windows PE USB-Laufwerk hinzufügen. Im folgenden Verfahren fügen Sie diese Treiber an der Windows-Bereitstellungsdienste Treiber speichern, damit sie für das Einfügen von Treibern während der Bild-Bereitstellung verfügbar sind.

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

    -   Klicken Sie auf der Seite **Erste Schritte** auf **jetzt Bilder importieren**, und wählen Sie die Bilder. Klicken Sie auf **Importieren**, und klicken Sie dann auf **OK**.

    -   In der ASC Windows im Menü **Server** auf **Inventar Manager**, klicken Sie auf die Registerkarte **Bilder** und klicken Sie dann auf **Hinzufügen**.

**So fügen eine Freigabe Antwortdateien hinzu**

1.  Eine standardmäßige Antwortdatei für jede unterstützte Architektur wird bereitgestellt, bei Systemlaufwerk %\\entspannen\\Skripts\\Vorlagen. Sie können die standardmäßige Antwortdatei verwenden, oder Sie können die Vorlage Unattend.xml kopieren und ändern Sie ihn in Windows System Image Manager. Weitere Informationen dazu, wie Sie eine Antwortdatei ändern finden Sie die [Technische Referenz zu Windows System Image Manager (Windows SIM)](http://go.microsoft.com/fwlink/?LinkId=214570).

2.  Kopieren von Antwortdateien Unattend.xml Systemlaufwerk %\\entspannen\\Unattendfiles. Wenn Sie separate unbeaufsichtigten Antwortdateien für bestimmte Bilder bereitstellen, übergeben Sie einen eindeutigen Namen an jede neue Antwortdatei bevor Sie es in Systemlaufwerk % kopieren\\entspannen\\Unattendfiles.

3.  Beim Hinzufügen von Bildern auf ein Projekt in der Windows-ASC, geben Sie den Pfad der Antwortdatei, die Sie mit diesem Bild verwenden möchten.

    **Wichtige**  
    Wenn Sie ein Bild mit einem System OEM Activation 3.0 (bei Zugriff 3.0) bereitstellen, verwenden Sie eine benutzerdefinierte Antwortdatei mit einem Product Key ein, der das Bild zugeordnet ist.

     

**Zuordnen von Antwortdateien mit Bildern**

1.  Klicken Sie im Menü **Server** auf **Bestand verwalten**.

2.  Klicken Sie im Fenster **Bestandsaufnahme** klicken Sie auf die Registerkarte **Bilder** , und klicken Sie dann verwenden Sie das Textfeld Filter, um die Filterkriterien hinzufügen, damit das Bild zu suchen, das Sie benötigen.

3.  Maustaste auf die Spaltenüberschrift, und klicken Sie dann auf **Pfad für die unbeaufsichtigte Installation** , um dieses Feld als Spalte anzeigen.

4.  Verwenden Sie die vertikale Bildlaufleiste, um die **für die unbeaufsichtigte Installation Pfad** -Spalte zu erhalten. Standardmäßig ist das Feld leer. Doppelklicken Sie auf das Feld, und geben Sie den UNC-Pfad für die Antwortdatei ein, die Sie mit der ausgewählten Bilds, beispielsweise Systemlaufwerk % verwenden möchten\\entspannen\\Unattendfiles\\*&lt;meine\_Antwort\_Datei&gt;*XML.

## <a name="related-topics"></a>Verwandte Themen


[Windows Assessment Services häufige Szenarien](windows-assessment-services-how-to-topics--wastechref.md)

 

 







