---
title: Installieren von Windows-Assessment-Services
description: Installieren von Windows-Assessment-Services
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fbd2036a-8d3e-43ac-b8c9-3c499e7e8322
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 48fe05e94dca89961e0fc40f3d009332c289b1dd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="installing-windows-assessment-services"></a>Installieren von Windows-Assessment-Services


Windows Assessment Services und Windows Assessment Services - Client (Windows ASC) sind in Windows Assessment and Deployment Kit (Windows ADK) verfügbar. Installieren oder Laden Sie das Windows ADK, und wählen Sie aus der Features, die Sie installieren möchten.

Sie müssen auf einem Servercomputer Windows Assessment Services installieren, die Windows ASC auch auf dem Server installiert. Sie können auch eine eigenständige Version von Windows ASC auf einem Clientcomputer zu installieren und verwenden, um auf Windows Assessment Services verbinden.

Server mit Windows Assessment Services unterstützt die Systemanalyse vor dem Start Execution Environment PXE-basierte Abbild Bereitstellung mithilfe von Windows-Bereitstellungsdienste. Windows Assessment Services-Servers verwaltet auch Ihre Inventardatenbank, Auftrag Freigaben, Ergebnis Freigaben und verschiedene Skripts, die für die Automatisierung verwendet werden. Verwenden Sie zum Verwalten von Anlagen, die in den Bestand sind Windows ASC, einrichten und Planen von Projekten und Aufträgen, Überwachen des Fortschritts, und Ergebnisse anzeigen.

In diesem Thema:

-   [Systemanforderungen](#sysreq-was)

-   [Installieren von Windows-Assessment-Services](#installwas)

-   [Installieren von Windows Assessment Services-Client](#installwasc)

-   [Sichern der Windows Assessment Services Inventar-Datenbank](#installwasc-backupinventory)

-   [Nächste Schritte](#installwasc-nextsteps)

## <a name="a-href-idsysreq-wasasystem-requirements"></a><a href="" id="sysreq-was"></a>Systemanforderungen


**Server-Computer**

Um Windows Assessment Services zu installieren, muss der Server die folgenden Anforderungen erfüllen:

-   Windows Server 2012 oder Windows Server 2008 R2 Enterprise, Standard oder Datacenter Edition. Windows Assessment Services wird nicht unterstützt, auf Server Core, Windows Server Essentials oder einem Server, der ein Domänencontroller ist.

    Windows ASC wird mit Windows Assessment Services standardmäßig installiert. Sie müssen die Remote Management 3.0 zum Ausführen von Windows ASC unter Windows Server 2008 R2 installieren.

    Wenn Sie Windows-Assessment-Services auf einem Windows Server 2012-Server installieren, wird Windows Deployment Services (WDS) wie folgt konfiguriert:

    -   Microsoft-Windows-Bereitstellungsdienste Microsoft-Windows-Deployment-Services-Transport-Server und Microsoft-Windows-Deployment-Services-Deployment-Server aktiviert sind.

    -   Windows Assessment Services wird über das Netzwerk als der erste Anbieter in der Liste der Anbieter für Client Boot-Dienste aufgeführt.

    -   Wenn WDS nicht initialisiert wird, Windows Assessment Services initialisiert und den "REMINST" Ordner % SYSTEMLAUFWERK\\"REMINST".

    -   Das WDS Bild Inventar werden Boot WIM-Dateien, die mit Windows Assessment Services installiert werden hinzugefügt.

    Wenn Sie Windows Assessment Services auf einem Windows Server 2008 R2-Server installieren, wird Windows Deployment Services (WDS) wie folgt konfiguriert:

    -   Microsoft-Windows-Bereitstellungsdienste und Microsoft-Windows-Deployment-Services-Transport-Server aktiviert sind.

    -   Die Freigabe "REMINST" erstellt, auf SYSTEMLAUFWERK %\\"REMINST", der Ordner freigegeben ist, und die Berechtigungen für den Benutzer Windows ASC (Localadmin) festgelegt werden.

    -   Startdateien werden aus dem Windows Assessment Services Directory... / entspannen/Installationsskripts, auf die Freigabe "REMINST" kopiert.

    -   Die WDS-Komponente, Wdstftp, konfiguriert ist.

    -   Windows-Assessment-Services ist als der erste Anbieter in der Liste der Anbieter für Client Boot Services über das Netzwerk aufgeführt.

    -   Die WDS Bild Inventar werden Boot WIM-Dateien, die mit Windows Assessment Services installiert wurden hinzugefügt.

    -   WDS Server neu gestartet wird.

    **Hinweis**  
    Bei der Installation von Windows Assessment Services auf einem Server wird mit diese Vorteile und Einschränkungen der Windows-Bereitstellungsdienste aktiviert:

    -   Windows-Bereitstellungsdienste ist so konfiguriert, dass um PXE-basierten Computer Discovery- und Bild-Bereitstellung zu automatisieren. Wenn Sie ein Bild, um Testcomputer bereitstellen, müssen Sie eine Windows WIM-Datei verwenden, die mit dem Tool Sysprep Generalisierung.

    -   Windows Assessment Services unter Windows Server 2012 verwendet Windows Deployment Services dynamische Treiber-Bereitstellung (DDP) passenden Plug & Play-Treiber während der Bereitstellung von Bild einfügen. Windows Assessment Services unterstützt keine DDP unter Windows Server 2008 R2. Auf entweder Serverbetriebssystem können Sie DISM.exe Treiber in das WIM-Abbild offline vor der Bereitstellung einfügen.

    -   Wenn der Server Mitglied einer Domäne ist, müssen Sie festlegen, die Internet Protocol Security (IPsec) Ausschlussrichtlinie mit Windows-Bereitstellungsdienste bereitstellen Images und Bewertung auf Testcomputern ausgeführt werden.

    -   Sie können Windows-Bereitstellungsdienste Image-Bereitstellung überspringen, wenn der Testcomputer bereits ein unterstütztes Betriebssystem ausgeführt wird, oder wenn es wurde ein Bild, ist äußeren Windows Assessment-Dienste bereitgestellt.

    -   Internetprotokoll, Version 4 (IPv4) wird unterstützt.

     

-   Microsoft .NET Framework 3.5 und .NET Framework 4

    **Hinweis**  
    Für Windows Server 2008 R2 .NET Framework 3.5 wird standardmäßig installiert und .NET Framework 4 mit dem Assessment Toolkit installiert wird.

     

    Für Windows Server 2012 .NET Framework 4 ist standardmäßig installiert, und Sie müssen .NET Framework 3.5 vor der Installation von Windows Assessment Services aktivieren. Geben Sie zum Aktivieren der .NET Framework 3.5 auf dem Server, an der Befehlszeile Folgendes ein:

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
    ```

-   Netzwerk: Netzwerkadapter 1 Gigabyte (GB)

-   Freier Festplattenspeicher: 50 GB Speicher pro Testcomputer.

-   Arbeitsspeicher: 8 GB RAM, 16 GB für Server, die mehr als 100 Testcomputern zu unterstützen.

**Des Referenzcomputers**

Standardmäßig ist der ASC Windows auf dem Server installiert, auf dem Windows Assessment Services werden installiert. Sie können auch auf einem Clientcomputer installieren. Zum Installieren von Windows ASC muss Ihren Computer eines der folgenden Betriebssysteme ausgeführt werden:

-   Windows Server 2008 R2 mit Remote Management 3.0 installiert

-   WindowsServer 2012

-   Windows 8

-   Windows 10

**Testcomputern**

Testcomputern müssen diesen Anforderungen entsprechen:

-   USB-Boot-Unterstützung

-   Netzwerk (PXE) Boot-Unterstützung

-   Treiber für Netzwerkadapter

**Netzwerkinfrastruktur**

Mindestens sollten Ihre Netzwerkinfrastruktur diese Anforderungen erfüllen:

-   Alle Computer müssen sich im gleichen Subnetz sein. Wenn dies nicht der Fall ist, sollte die IP-Adresse des Windows-Assessment-Services-Server und Windows-Bereitstellungsdienste in der Liste der Optionen für alle Testcomputer, die Sie mithilfe von Windows Assessment Services bereitstellen IP Helper-Adresse sein.

-   Ein Server Dynamic Host Configuration Protocol (DHCP) muss im gleichen Netzwerk zum Zuweisen von IP-Adressen auf Testcomputer verfügbar sein.

**Sicherheitshinweis:**

Einschränken des Zugriffs auf dem Server mit Windows Assessment Services aus Sicherheitsgründen mit einem der folgenden Schritte:

-   Blockieren von Port 8000 für Benutzer außerhalb der gleichen Teilmenge von einem Administrator, wenn in einer Arbeitsgruppe oder mithilfe von Gruppenrichtlinien, wenn der Computer in einer Domäne befinden.

-   Bearbeiten Sie eine Firewallregel auf dem Server, der als Bereich definiert:

    -   Spezielles Subnetz

    -   Einen bestimmten IP-Bereich

    -   Eine vordefinierte Gruppe von Computern

    -   Bestimmte Benutzer oder bestimmte Computer

## <a name="a-href-idinstallwasainstalling-windows-assessment-services"></a><a href="" id="installwas"></a>Installieren von Windows-Assessment-Services


**Wichtige**  
Sie können an einer neueren Version von Windows Assessment Services aktualisieren. Bei einer Aktualisierung werden zur der Bewertungsergebnisse auf dem Server beibehalten. Project, Job- und Auftragsinformationen werden nicht beibehalten.

 

1.  Doppelklicken Sie auf dem Servercomputer auf **ADKSetup.exe**.

2.  Klicken Sie auf **herunterladen** , um Windows ADK herunterladen. Oder, wenn der Server während der Installation mit dem Internet verbunden bleiben kann, klicken Sie auf **Installieren**.

3.  Akzeptieren Sie die Microsoft-Software-Lizenzbedingungen.

4.  Die folgenden Features auswählen:

    -   Bereitstellungstools

    -   Vorinstallation Windows-Umgebung

    -   Windows-Assessment-Services

    -   Windows Performance Toolkit

5.  Klicken Sie auf **Installieren**.

**Hinweis**  
Eine Instanz von Microsoft SQL Server 2012 Express wird zusammen mit Windows Assessment Services installiert. Der Name der Instanz von SQL Server ist ADK. Wenn eine Instanz von SQL Server mit dem Namen ADK ist vorhanden, sollte Sie entfernen oder benennen Sie sie vor der Installation von Windows Assessment Services. Wenn Sie nicht möchten, wird die vorhandene Instanz verwendet.

Standardmäßig wird Windows ASC auch zusammen mit Windows Assessment Services auf dem Server installiert.

 

## <a name="a-href-idinstallwascainstalling-windows-assessment-services---client"></a><a href="" id="installwasc"></a>Installieren von Windows-Assessment-Services - Client


Windows ASC wird standardmäßig auf dem Server installiert, bei der Installation von Windows Assessment Services. Jedoch können Sie es auch auf einem Computer Client (oder Techniker) installieren.

1.  Doppelklicken Sie auf dem Referenzcomputer **ADKSetup.exe**.

2.  Klicken Sie auf **herunterladen** , um Windows ADK herunterladen. Oder wenn der Computer mit dem Internet verbunden während des Setups verbleiben kann, klicken Sie auf **Installieren**.

3.  Wählen Sie **Bereitstellungstools**, **Zur Bewertung-Client für Windows**und **Windows Performance Toolkit**, und klicken Sie dann auf **Installieren**.

## <a name="a-href-idinstallwasc-backupinventoryabacking-up-the-windows-assessment-services-inventory-database"></a><a href="" id="installwasc-backupinventory"></a>Sichern der Windows Assessment Services Inventar-Datenbank


Wenn Sie beabsichtigen, das Serverbetriebssystem aktualisieren, auf dem Windows Assessment Services installiert ist, müssen Sie sichern Sie die Windows-Assessment-Services-Datenbank und alle relevanten benutzerdefinierte Skripts Bestandsaufnahme machen. Obwohl es erforderlich, nicht dann, wenn Sie Deinstallation und Neuinstallation von Windows Assessment Services werden, zudem wird empfohlen Sichern der Datenbank und Skripts angepasst.

**So sichern Sie die Windows Assessment Services Inventar-Datenbank**

1.  Installieren Sie Microsoft SQL Server Management Studio Express (ENU\\X86\\SQLManagementStudio\_X86\_ENU.exe), aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=251597).

2.  Verwenden Sie **net Stop Wassvc** , um Windows Assessment Services zu beenden.

3.  Öffnen Sie SQL Server Management Studio 2012, und trennen Sie die Windows-Assessment-Services-Datenbank. Weitere Informationen zum Trennen einer Datenbank mithilfe von SQL Server Management Studio 2012 finden Sie unter [MSDN: Trennen eine Datenbank](http://go.microsoft.com/fwlink/?LinkId=251595).

4.  Kopieren der Datenbank (MDB-Datei) und die Transaktionsprotokolle Systemlaufwerk %\\Ordner "ProgramData"\\Windows Assessment Services\\an einem sicheren Speicherort backup-Datenbanken.

    **Hinweis**  
    Wenn Sie Skripts in den Ordner .../relax/scripts angepasst haben, kopieren Sie sie auch an einem sicheren Speicherort für die Sicherung.

     

5.  Deinstallieren Sie Windows Assessment Services, aktualisieren Sie Ihre Server-Betriebssystem und installieren Sie Windows Assessment Services anschließend neu.

6.  Initialisieren des Servers mit Windows Assessment Services Windows ASC öffnen und Herstellen einer Verbindung mit dem Server.

7.  Verwenden Sie **net Stop Wassvc** , um Windows Assessment Services zu beenden.

8.  Öffnen Sie SQL Server Management Studio 2012, und trennen Sie die neue Windows Assessment Services-Datenbank, die erstellt wurde, wenn Sie auf den Server mit Windows Assessment Services initialisiert.

9.  Entfernen Sie die neue Datenbank aus Systemlaufwerk %\\Ordner "ProgramData"\\Windows Assessment Services\\Datenbanken.

10. Kopieren die alte Datenbank aus dem Sicherungsspeicherort in Systemlaufwerk %\\Ordner "ProgramData"\\Windows Assessment Services\\Datenbanken.

11. Öffnen Sie SQL Server Management Studio 2012, und fügen Sie die Windows-Assessment-Services-Datenbank. Weitere Informationen zum Anfügen einer Datenbank mithilfe von SQL Server Management Studio 2012 finden Sie unter [MSDN: Anfügen einer Datenbank](http://go.microsoft.com/fwlink/?LinkId=251596).

12. Setzen Sie Ihre benutzerdefinierte Skripts wieder in das Verzeichnis .../relax/scripts.

13. Verwenden Sie **net Start Wassvc** zum Starten von Windows Assessment Services.

## <a name="a-href-idinstallwasc-nextstepsanext-steps"></a><a href="" id="installwasc-nextsteps"></a>Nächste Schritte


Initialisieren Sie nach der Installation von Windows Assessment Services und die Windows-ASC den Server, und konfigurieren Sie der Kommunikation zwischen Windows Assessment Services und die Windows-ASC-Computer. Sie können mehrere Windows ASC Computer zur Kommunikation mit dem Server mit Windows Assessment Services konfigurieren. Weitere Informationen finden Sie unter [Windows Assessment Services-Setup und Konfiguration](windows-assessment-services-setup-and-configuration-wastechref.md).

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

 

 







