---
author: Justinha
Description: "Gerätetreiber"
ms.assetid: daa94074-a23d-4788-8e32-0e27c0a62d88
MSHAttr: PreferredLib:/library/windows/hardware
title: "Gerätetreiber"
ms.openlocfilehash: cb54f07ab351a1b8bf9fd9af43cf2852a26ef1e2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="device-drivers"></a>Gerätetreiber


Sie können ein Windows-Abbild vor, während oder nach Gerätetreiber hinzufügen Sie Bereitstellen des Abbilds. Zum Hinzufügen von Treibern zu Windows-Bereitstellung planen, es ist wichtig zu verstehen, wie Treiber Ordner hinzugefügt werden, auf das Bild wie Treiber Rangfolge Bereitstellung und die digitale Signatur Anforderungen für Treiber auswirkt.

In diesem Thema:

-   [Hinzufügen von Treibern](#addingdrivers)

-   [Verwalten von Ordnern Treiber](#drivermgmt)

-   [Grundlegendes zur Bewertung der Treiber](#driverranking)

-   [Grundlegendes zu digitalen Signatur Anforderungen](#signaturereqs)

-   [Weitere Ressourcen](#resources)

## <a name="span-idaddingdriversspanspan-idaddingdriversspanspan-idaddingdriversspanadding-drivers"></a><span id="AddingDrivers"></span><span id="addingdrivers"></span><span id="ADDINGDRIVERS"></span>Hinzufügen von Treibern


Sie können ein Windows-Abbild Gerätetreiber hinzufügen:

-   [Vor der Bereitstellung auf einem offline Windows-Bild](#offline)

-   [Während eine automatische Bereitstellung](#automated)

-   [Nach der Bereitstellung auf einem ausgeführten Betriebssystem](#online)

Weitere Informationen finden Sie unter [Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md).

### <a name="span-idofflinespanspan-idofflinespanadd-drivers-before-deployment-on-an-offline-windows-image-by-using-dism"></a><span id="offline"></span><span id="OFFLINE"></span>Hinzufügen von Treibern vor der Bereitstellung auf Schwelle Windows offline mithilfe von DISM

Offline – Wartung tritt auf, wenn Sie ein Windows-Abbild vollständig offline geändert wird, ohne das Betriebssystem starten. Sie können hinzufügen oder entfernen und die Treiber für ein Windows-Abbild offline mithilfe des Befehlszeilentools DISM auflisten. DISM ist mit Windows installiert wird und auch in dem Windows Assessment and Deployment Kit (Windows ADK). Weitere Informationen zu DISM finden Sie unter der [DISM - Bereitstellung Abbildern und technische Referenz für Windows Management](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

Wenn Sie ein offline-Abbild Treiber hinzufügen, hat es bereitgestellt oder im Abbild gespiegelt:

-   **Treiber erforderliche** widergespiegelt werden. Anders ausgedrückt, werden die Dateien in das Bild entsprechend der Angabe in der INF-Datei kopiert. Der PC-Option schließt Installationsaufgaben während der ersten Startvorgang einschließlich Critical Geräte-Datenbank (CDDB) und die Registrierung aktualisieren ab.

-   **Treiber, die nicht kritische Boot,** werden bereitgestellt. Anders ausgedrückt, sind die Treiber Store hinzugefügt. Nach dem Start von Windows Plug & Play-erkennt das Gerät und der entsprechenden Treiber aus dem Treiberspeicher installiert.

Sie können DISM-Befehle zum Hinzufügen oder Entfernen von Treibern für ein bereitgestelltes oder angewendetes Windows- oder Windows Vorinstallation Environment (Windows PE) Bild.

**Hinweis**  
Sie können DISM um Posteingang-Treiber (die standardmäßig unter Windows installierten Treiber) zu entfernen. Sie können nur für das Entfernen von Drittanbietern oder Out-of-Box-Treiber.

 

DISM-Befehlen können auch eine Antwortdatei auf ein bereitgestelltes oder angewendetes Windows Bild angewendet.

Weitere Informationen finden Sie unter [Hinzufügen und entfernen Treiber eine Offline-Windows-Abbild](add-and-remove-drivers-to-an-offline-windows-image.md).

Wenn Sie DISM verwenden, können Sie nur INF-Treiber ein offline-Windows-Abbild hinzufügen. Treiber, von die das Designed for Windows-Logo angezeigt werden als CAB-Dateien bereitgestellt. Erweitern Sie die CAB-Datei, bevor Sie die INF-Datei installieren, wenn Sie DISM für die Installation verwenden. Sie müssen einen Treiber, der als eine .exe-Datei oder eine andere Datei gepackt ist installieren auf einem Windows-Betriebssystem ausgeführt wird. Um eine .exe oder Paket Windows Installer (MSI) ausführen, können Sie zu einer Antwortdatei zum Installieren des Treiberpakets einen benutzerdefinierten Befehl hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Befehls zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915058).

### <a name="span-idautomatedspanspan-idautomatedspanadd-drivers-during-an-automated-deployment-by-using-windows-setup-and-an-answer-file"></a><span id="automated"></span><span id="AUTOMATED"></span>Hinzufügen von Treibern während eine automatische Bereitstellung mithilfe von Windows Setup und einer Antwortdatei

Eine Antwortdatei können Sie die Treiber zu einem Bild hinzufügen, wenn Sie Windows-Setup für die Bereitstellung verwenden. In dieser Antwortdatei können Sie den Pfad der Gerätetreiber in einer Netzwerkfreigabe (oder ein lokaler Pfad) angeben. Zu diesem Zweck der Microsoft-Windows-PnpCustomizationWinPE oder Microsoft-Windows-PnpCustomizationNonWinPE und Angeben der Konfigurations übergibt, in dem Sie sie installieren möchten. Wenn Sie Windows Setup ausführen und geben Sie den Namen der Antwortdatei, Out-of-Box-Treiber bereitgestellt sind (hinzugefügt Driver Store auf dem Bild) und Treiber erforderliche widergespiegelt werden (hinzugefügt, das Bild, sodass sie beim Start des Computers verwendet werden können). Setup verwendet die Antwortdatei. Durch Hinzufügen von Gerätetreibern während der Konfigurationsphasen **WindowsPE** oder **OfflineServicing** , können Sie die Windows-Abbild vor dem Starten des Computers Out-of-Box-Gerätetreibern hinzufügen. Sie können diese Methode auch verwenden, ein Windows-Abbild Treiber erforderliche hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Gerätetreibern zu Windows während Windows Setup](add-device-drivers-to-windows-during-windows-setup.md). Weitere Informationen zur Funktionsweise von Windows Setup finden Sie unter der [Technischen Referenz zu Windows Setup](windows-setup-technical-reference.md).

Wenn Sie Windows PE Treiber erforderliche hinzufügen möchten, verwenden Sie die **WindowsPE** Konfiguration Pass, um die Treiber aktualisiert, bevor das Windows PE-Abbild gestartet wird. Der Unterschied zwischen hinzufügen, dass erforderliche Treiber während der Konfiguration **WindowsPE** übergeben, und sie der in der Phase der **OfflineServicing** -Konfiguration hinzufügen, die während der Konfiguration **WindowsPE** -Durchgang ist, werden wichtige Faktoren für Windows PE verwenden wiedergegeben. Während des Schritts **OfflineServicing** Konfiguration werden der Treiber die Treiber Speicher auf dem Windows-Abbild bereitgestellt.

Methoden zum Hinzufügen von Gerätetreibern mithilfe von Windows Setup dazu gehören:

-   Mithilfe einer Antwortdatei Treiber während der **OfflineServicing** Konfiguration von Setup hinzufügen.

-   Verwenden einer Antwortdatei zum Hinzufügen von Treibern während der **WindowsPE** Konfiguration von Setup

-   For Windows Server®, platzieren von Treibern im Verzeichnis $ $WinPEDriver während der **WindowsPE** Konfiguration von Setup automatisch installiert werden. Alle Laufwerkbuchstaben mit einem Wert von C oder höher sind ein $WinPEDriver$ Verzeichnis überprüft. Das Laufwerk muss während der Installation zugreifen können auf der Festplatte. Stellen Sie sicher, dass das Laufwerk nicht erfordert, dass einen Treiber geladen werden muss, bevor darauf zugegriffen werden kann.

Weitere Informationen zu diesen und anderen Konfigurationsphasen finden Sie unter [Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md).

Wenn Sie Windows-Bereitstellungsdienste für die Bereitstellung in Windows Server verwenden, können Gerätetreiber auf Ihrem Server hinzufügen und so konfiguriert werden, die als Teil einer Netzwerk-basierte Installation auf Clients bereitgestellt werden. Sie konfigurieren diese Funktionalität durch Erstellen einer Treibergruppe auf den Server Pakete hinzugefügt, und klicken Sie dann Hinzufügen von Filtern zum definieren, welche Clients die Treiber installiert. Sie können die installierten Treiber konfigurieren, basierend auf dem Client-Hardware (beispielsweise Hersteller oder BIOS-Anbieter) und die Version des Windows-Abbilds, das während der Installation ausgewählt ist. Sie können auch konfigurieren, ob Clients Installieren aller Pakete in einer Treibergruppe oder nur die Treiber, die mit die installierte Hardware auf dem Client übereinstimmen. Weitere Informationen zum Implementieren dieser Funktionalität finden Sie in der Windows-Bereitstellungsdienste Dokumentation.

### <a name="span-idonlinespanspan-idonlinespanadd-drivers-after-deployment-on-a-running-operating-system-by-using-pnputil-or-an-answer-file"></a><span id="online"></span><span id="ONLINE"></span>Hinzufügen von Treibern mithilfe von PnPUtil oder eine Antwortdatei nach der Bereitstellung auf einem ausgeführten Betriebssystem

Sie können das Tool PnPUtil zum Hinzufügen oder Entfernen von Treibern auf einem ausgeführten Betriebssystem verwenden. Alternativ können Sie eine Antwortdatei zum Automatisieren der Installations der Treiber beim Start des Computers im Überwachungsmodus aktiviert ist. Diese Methoden ist hilfreich, wenn Sie möchten ein einfaches Windows-Abbild verwalten, und fügen Sie nur die Treiber, die für eine bestimmte Hardwarekonfiguration erforderlich sind. [Boot Windows Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md)finden Sie weitere Informationen zur Verwendung im Überwachungsmodus ist.

Methoden zum Hinzufügen von Gerätetreibern online zu einem ausgeführten Betriebssystem gehören:

-   Verwenden PnPUtil zum Hinzufügen oder Entfernen von Plug & Play-Treiber. Weitere Informationen finden Sie unter [Verwendung von PnPUtil in einer Befehlszeile installieren eines Plug & Play-Geräts](http://go.microsoft.com/fwlink/?LinkId=139151).

-   Verwenden eine Antwortdatei zur Automatisierung der Installations von Plug & Play-Treiber beim Start des Computers im Überwachungsmodus aktiviert. Weitere Informationen finden Sie unter [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md).

## <a name="span-iddrivermgmtspanspan-iddrivermgmtspanspan-iddrivermgmtspanmanaging-driver-folders"></a><span id="DriverMgmt"></span><span id="drivermgmt"></span><span id="DRIVERMGMT"></span>Verwalten von Ordnern Treiber


Wenn Sie mehrere Treiber hinzufügen, sollten Sie separate Ordner für jeden Treiber oder Treiberkategorie erstellen. Dadurch wird sichergestellt, dass keine Konflikte bestehen, beim Hinzufügen von Treibern, die denselben Dateinamen aufweisen. Nachdem der Treiber unter dem Betriebssystem installiert ist, wird Sie in Oem umbenannt\*INF, um sicherzustellen, dass eindeutigen Dateinamen für das Betriebssystem. Beispielsweise werden die bereitgestellten Treiber mit dem Namen Treiber1.inf und Treiber2.inf Oem0.inf und Oem1.inf umbenannt, nachdem sie installiert sind.

Wenn Sie einen Pfad Treiber in einer Antwortdatei angeben, werden alle INF-Treiber im angegebenen Verzeichnis und den Unterverzeichnissen Driver Store des Windows-Abbilds % SystemRoot%\System32\DriverStore\FileRepository hinzugefügt. Beispielsweise sollen alle Treiber in Laufwerk C:\\MyDrivers\\Netzwerke, C:\\MyDrivers\\Video- und C:\\MyDrivers\\Audiodaten Verzeichnisse in das Windows-Abbild verfügbar sein Geben Sie den Pfad Gerätetreibern, C:\\MyDrivers, in die Antwortdatei. Wenn Sie eine Antwortdatei nicht verwenden, können Sie den **Befehl/recurse** DISM verwenden. Weitere Informationen zu den **Befehl/recurse** finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-driver-servicing-command-line-options-s14.md). Mit diesem Befehl wird sichergestellt, dass alle Treiber in den einzelnen Unterverzeichnissen an den Treiber Store in das Windows-Abbild hinzugefügt werden.

Wenn das Bild alle Treiber im angegebenen Verzeichnis und den Unterverzeichnissen hinzugefügt werden, sollte Sie die Antwortdatei oder Ihre DISM-Befehle und diese Verzeichnisse sorgfältig verwalten. Sollten Sie sich eine Erhöhung der Größe des Bilds über unnötige Treiberpakete Übernahme.

Wenn es ist nicht möglich, zu verwalten, damit nur die erforderlichen Treiber für das Abbild hinzugefügt werden, können Sie das Tool Driver Package Installer (DPInst), Hinzufügen von Treibern, die nicht kritische Boot online sind. DPInst werden selektiv Treiber, die nicht Start erforderlich sind, nur, wenn die Hardware vorhanden ist oder wenn Treiberpakets eine bessere Übereinstimmung für das Gerät ist installiert.

## <a name="span-iddriverrankingspanspan-iddriverrankingspanspan-iddriverrankingspanunderstanding-driver-ranking"></a><span id="DriverRanking"></span><span id="driverranking"></span><span id="DRIVERRANKING"></span>Grundlegendes zur Bewertung der Treiber


Eine der am häufigsten auftretenden Probleme bei der Bereitstellung von Treibern geschieht, wenn ein Treiber erfolgreich in Driver Store importiert jedoch, nachdem das System Plug & Play ist mit höherer Priorität-Treiber Treiber findet und installiert diese stattdessen.

Windows-Plug & Play-Manager stuft diese Treiber-Paket-Eigenschaften in der Reihenfolge der Priorität:

1.  Signieren

2.  Plug & Play-ID-Übereinstimmung

3.  Treiberdatum

4.  Treiberversion

Beispielsweise wenn ein Gerät eine bessere Übereinstimmung Plug & Play-ID hat, aber nicht signiert ist, hat ein signierter Treiber, der eine kompatible ID Übereinstimmung hat Vorrang. Ein älterer Treiber kann einen neueren Treiber outrank, wenn der ältere Treiber eine bessere Plug & Play-ID-Übereinstimmung oder Signatur verfügt.

Weitere Informationen zu Treiber Rangfolgen finden Sie unter [Wie Windows Rangfolgen-Treiber](http://go.microsoft.com/fwlink/?LinkId=91227).

## <a name="span-idsignaturereqsspanspan-idsignaturereqsspanspan-idsignaturereqsspanunderstanding-digital-signature-requirements"></a><span id="SignatureReqs"></span><span id="signaturereqs"></span><span id="SIGNATUREREQS"></span>Grundlegendes zu digitalen Signatur Anforderungen


Signierte Gerätetreiber sind eine wichtige Sicherheitsfunktion in Windows. Faktoren, die auf X64-Computern installiert sind, benötigen eine digitale Signatur. Obwohl es nicht erforderlich ist, wird empfohlen, und stellen Sie sicher, dass Treiber vor der Installation auf X86-Computern angemeldet sind.

Alle wichtigen Treiber müssen eingebettete Signaturen enthalten. Eine digitale Signatur ist nicht erforderlich für (Plug & Play-) Plug & Play-Treiber. Jedoch ein nicht signierter Plug & Play-Treiber auf einem ausgeführten Betriebssystem installiert ist, sind Administratoranmeldeinformationen erforderlich, und Sie nicht auf 64-Bit-Betriebssystemen derartige Treiber installieren.

Es gibt zwei Methoden, um ein Treiber signiert werden kann:

-   Im Kernelmodus und wichtige Treiber sind über eine Methode eingebetteter Signatur digital signiert. Alle Binärdateien innerhalb des Treiberpakets wird mithilfe von eingebetteten Signatur signiert. Eingebettete Signaturen verbessern Boot Leistung beim Laden. Für Treibern, die nicht Plug & Play-sind sollten Signaturen eingebettet werden, damit sie bei einem Upgrade des Betriebssystems nicht unterbrochen werden.

-   Digital signierte Plug & Play-Treiber enthalten eine Katalogdatei (.cat), die digital signiert ist. Die Katalogdatei enthält einen Hash aller Dateien in der Treiber INF-Datei für die Installation. Eine signierte Katalogdatei ist die benötigen, wenn Sie die meisten Plug & Play-Treiber ordnungsgemäß installiert.

Einer der folgenden Quellen können Treiber signiert werden:

-   Windows Hardware Quality Labs (WHQL), die sicherstellt, dass der Treiber für das Windows-Hardware-Zertifizierungsprogramm qualifizieren. WHQL wird einen Katalog mit signierten Treibern erstellt. Für wichtige Faktoren sollten Sie eingebettete Signaturen angewiesen im Katalog hinzufügen. Eingebettete Signaturen in Treiber erforderliche Bilddateien Optimieren der Leistung von Boot des Betriebssystems aufgrund der Eliminierung erforderlich, dass die entsprechenden Katalog-Datei zu suchen, wenn Ladeprogramm des Betriebssystems die Treibersignatur überprüft.

-   Eine Zertifizierungsstelle (CA), mithilfe einer Software Publishing Zertifikat (ASP). Microsoft bietet wichtige und X64-basierten Kernel-Treiber ein zusätzliches Zertifikat, das zum Cross-Treiber Signieren verwendet werden kann. Treibern, die nicht kritische Boot müssen nicht von Microsoft Cross signiert oder eingebettet werden. Sie können Windows Kernel-Modus Code Signing verwenden, sollten Sie die Flexibilität der Signatur der Treiber selbst. Informationen zu digitalen Signaturen für Kernel-Module X64-basierte Systeme finden Sie unter [64-Bit-Treiber Richtlinien](http://go.microsoft.com/fwlink/?LinkId=529487).

Für Testzwecke können Sie auch Testzertifikate verwenden.

Wenn Sie einen nicht signierten Treiber von einem Anbieter zu Testzwecken erhalten haben, können Sie eine Testsignatur den Treiber und testen die Installation verwenden. Signieren der Test ist das digital signieren einer Anwendung mithilfe von einem privaten Schlüssel und ein entsprechendes Signieren von Code Zertifikat, das nur in der Grenzen der einer Umgebung vertraut wird.

Dies sind die primäre Methode zum solche Zertifikate generieren:

-   Entwickler können eigene selbstsignierte Zertifikate generieren.

-   Eine Zertifizierungsstelle kann Zertifikate aus.

In beiden Fällen müssen der Zertifikate nur zu Testzwecken entsprechend klar identifiziert werden. Beispielsweise das Wort "Test" in der Antragstellername des Zertifikats enthalten sein kann, und zusätzliche rechtlichen Haftungsausschlüsse im Zertifikat enthalten sein können. Produktionszertifikate, die kommerzieller Zertifizierungsstellen ausgestellt werden, müssen für die Anmeldung nur öffentliche Betaversionen und öffentliche die endgültige Version der Software und interne Line-of-Business reserviert werden.

Weitere Informationen finden Sie unter [Anforderungen für das Gerät Treiber signieren und Bereitstellen](http://go.microsoft.com/fwlink/?LinkId=210665).

Beim Hinzufügen von Test signierte Treiberpaketen an den Windows sollten Sie folgende Punkte:

-   Sie müssen die Testzertifikate auf einem ausgeführten Betriebssystem installieren. Sie können nicht offline installiert werden.

-   Das Zertifikat der Zertifizierungsstelle, die das Testzertifikat ausgestellt muss in den Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen eingefügt werden.

    **Hinweis**  
    Wenn das Testzertifikat selbstsigniert ist – beispielsweise mithilfe der Certificate Creation Tool (MakeCert) – das Testzertifikat im Zertifikatspeicher unter Vertrauenswürdige Stammzertifizierungsstellen eingefügt werden muss.

     

-   Das Testzertifikat, das zum Signieren des Treiberpakets verwendet wird, muss in den Zertifikatspeicher für vertrauenswürdige Herausgeber eingefügt werden.

-   Sie müssen Zertifikate hinzufügen online (an eine gestarteten Instanz des Windows-Abbilds) bevor Sie das Befehlszeilentool Deployment Image Servicing and Management (DISM) verwenden können, offline Test signierte Treiber hinzuzufügen.

-   DISM überprüft WHQL Zertifizierungen nur für wichtige Faktoren. Aber eine Befehlszeilenoption DISM kann dieses Verhalten außer Kraft setzen. Weitere Informationen finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-driver-servicing-command-line-options-s14.md).

-   Legen Sie Sie zum Installieren und Testen signierte Treiber unter 64-Bit-Betriebssystemen Überprüfen der Windows-Startkonfiguration Testmodus mithilfe des BCDedit-Tools auf dem Zielcomputer aus. Testmodus stellt sicher, dass das Treiberabbild ist signiert, aber zertifikatüberprüfung Pfad erfordert nicht den Aussteller als eine vertrauenswürdige Stammzertifizierungsstelle konfiguriert werden soll. Für die Installation des Plug & Play-Treibers und die Rangfolge Logik den Treiber ordnungsgemäß behandelt muss das Testzertifikat in dem vertrauenswürdigen Zertifikatspeicher des Bilds Betriebssystem gespeichert werden. Informationen zu Testmodus während der Entwicklung finden Sie unter [64-Bit-Treiber Richtlinien](http://go.microsoft.com/fwlink/?LinkId=62690).

**Vorsicht**  
Wenn Sie ein nicht signierten oder ungültigen wichtigen Gerätetreiber auf einem X64-basierten Computer installiert ist, wird der Computer nicht gestartet. Der nicht signierten oder ungültigen wichtigen Gerätetreiber wird einen Stop-Fehler verursacht. Sie sollten den Treiber aus der Datenbank für wichtige Geräte (CDDB) oder dem gespiegelten Ort im Bild entfernen. Wenn Sie ein Upgrade durchführen, stellen Sie sicher, nicht signierte Treiber und der zugehörigen Anwendung, Dienste, oder Geräte mit einem signierten Treiber aktualisiert oder entfernt werden.

Wenn Sie nicht im Testmodus mithilfe von BCDedit aktivieren Sie einen Test signierte Treiber installiert haben, wird der Computer nicht gestartet. Wenn Sie DISM verwenden, um die Treiber zu entfernen, möglicherweise nicht alle Instanzen des gespiegelten Treiberpakets entfernt. Daher wird empfohlen, Sie Bilder bereitstellen nicht, die Test-signierter Treiber installiert haben.

 

## <a name="span-idresourcesspanspan-idresourcesspanspan-idresourcesspanadditional-resources"></a><span id="Resources"></span><span id="resources"></span><span id="RESOURCES"></span>Weitere Ressourcen


Diese Websites finden Sie weitere Informationen zu den Gerätetreiber Anforderungen:

-   Weitere Informationen zur Bereitstellung von Plug & Play-Treiber finden Sie unter [Plug & Play-Gerät anmelden Anforderungen für die Installation](http://go.microsoft.com/fwlink/?LinkId=89602).

-   Weitere Informationen zu digitalen Signaturen und beim Entwickeln von Treibern finden Sie unter der entsprechenden Seite auf der [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?LinkId=139175) -Website.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Fügen Sie einen Gerät Treiberpfad zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915062)

[Hinzufügen eines Treibers Online im Überwachungsmodus](add-a-driver-online-in-audit-mode.md)

[Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)

[Hinzufügen und Entfernen von Treibern zu einem Offline-Windows-Bild](add-and-remove-drivers-to-an-offline-windows-image.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Verwalten Sie Treiberkonfigurationen, wenn Sie ein Windows-Abbild aufzeichnen](maintain-driver-configurations-when-capturing-a-windows-image.md)

[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[Problembehandlung von Bereitstellung und Protokolldateien](deployment-troubleshooting-and-log-files.md)

 

 






