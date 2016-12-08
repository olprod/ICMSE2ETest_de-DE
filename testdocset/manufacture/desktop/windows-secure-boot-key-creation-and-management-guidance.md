---
author: Justinha
Description: Wichtige Windows sicheren Boot-Erstellung und Verwaltung
ms.assetid: 603ae3a4-d9b6-4d2a-bf46-b2fdffcd6baf
MSHAttr: PreferredLib:/library/windows/hardware
title: Wichtige Windows sicheren Boot-Erstellung und Verwaltung
ms.openlocfilehash: 1afc5211d0180e8c7554b749b12fb2acbaf053d0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-secure-boot-key-creation-and-management-guidance"></a>Wichtige Windows sicheren Boot-Erstellung und Verwaltung


**Vishal Maman Architekt, OEM Consulting**,<vmanan@microsoft.com>

**Arie van der Hoeven, Architekt, OEM Consulting**<ariev@microsoft.com>

Dieses Dokument hilft Handbuch OEMs und ODMs in die Erstellung und Verwaltung der Secure Boot Schlüssel und Zertifikate in einer Umgebung mit Fertigung. Fragen im Zusammenhang mit der Erstellung, Speicherung und den Abruf von Plattform Schlüssel (PKs), sichere Firmware Update Schlüssel und Drittanbieter Key Exchange Schlüssel (KEKs) behandelt.

**Hinweis:** Diese Schritte sind nicht speziell für PC-OEMs. Unternehmen und Kunden können diese Schritte auch so konfigurieren Sie ihre Server zur Unterstützung der Secure Boot verwenden. 

Windows-Anforderungen für UEFI und Secure Boot finden Sie in der [Windows-Zertifizierungsstelle Hardwareanforderungen](http://go.microsoft.com/fwlink/p/?linkid=320504). In diesem Whitepaper einführen neue Anforderungen oder darstellen ein offizielle Windows-Programms nicht. Sie sollte als Leitfaden jenseits Zertifizierung Anforderungen, bei der effizienten und sichere Prozesse für das Erstellen und Verwalten von sicheren Boot-Schlüssel erstellen. Dies ist wichtig, weil UEFI Secure Boot auf die Verwendung der Public Key-Infrastruktur zum Authentifizieren von Code vor basiert ausgeführt.

Der Leser wird erwartet, dass die Grundlagen der UEFI, grundlegende Kenntnisse über Secure Boot (Kapitel 27 der [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187)) und PKI-Sicherheitsmodell zu kennen.

Anforderungen, Tests und Tools überprüfen Secure Boot Windows stehen heute über die [Windows Hardware Zertifizierung Kit (HCK)](http://go.microsoft.com/fwlink/p/?linkid=254893). Diese Ressourcen HCK berücksichtigen jedoch nicht Erstellung und Verwaltung der Schlüssel für Windows-Bereitstellungen. In diesem Whitepaper Adressen Key Management als Ressource Guide-Partner über die Bereitstellung der Schlüssel, der von der Firmware verwendet. Es dient nicht als Leitfäden und umfasst keine neuen Anforderungen.

Auf dieser Seite:

-   [1. secure Boot, Windows und Key Management](#securebootkeymanagement) enthält Informationen zu Boot-Sicherheit und PKI-Architektur angewendet auf Windows und Secure Boot.

-   [2. Key Management-Lösungen](#keymanagementsolutions) soll vermitteln, Partner, die eine wichtige Management und Entwurf Lösung entwerfen, die ihren Anforderungen entspricht.

-   [3. Zusammenfassung und Ressourcen](#summaryandresources) Anhänge, Prüflisten, APIs und anderer Verweise auf enthält.

Dieses Dokument dient als Ausgangspunkt bei der Entwicklung von Kunden PCs, Factory Bereitstellungstools und bewährte Methoden für wichtige Sicherheitselemente bereit.

## <a name="span-idsecurebootkeymanagementspanspan-idsecurebootkeymanagementspanspan-idsecurebootkeymanagementspan1-secure-boot-windows-and-key-management"></a><span id="SecureBootKeyManagement"></span><span id="securebootkeymanagement"></span><span id="SECUREBOOTKEYMANAGEMENT"></span>1. secure Boot, Windows und Verwalten von Schlüsseln


UEFI (Unified Extensible Firmware Interface)-Spezifikation definiert eine Firmware Ausführung Authentifizierungsprozess Secure Boot aufgerufen. Als ein Branchenstandard Secure Boot definiert, wie Plattform Firmware Zertifikate verwaltet, Firmware und das Betriebssystem wie bei diesem Prozess Schnittstellen authentifiziert.

Sichere Boot basiert auf der Public Key-Infrastruktur (PKI) Prozess Module authentifizieren, bevor sie ausgeführt werden dürfen. Diese Module können Firmwaretreiber, Option ROM UEFI Treiber auf Datenträger, UEFI Applications oder UEFI Boot Ladeprogramme umfassen. Über die Bild-Authentifizierung vor der Ausführung reduziert Secure Boot das Risiko eines Angriffs wie Rootkits vor dem Start Malware. Microsoft nutzt die UEFI Secure Boot in Windows 8 und höher als Teil seiner vertrauenswürdige Boot Sicherheitsarchitektur Plattform Sicherheit für unsere Kunden verbessern können. Sichere Boot ist erforderlich für Windows 8 Client-PCs, und geben Sie für Windows Server 2016, wie in der Windows-Kompatibilität Hardwareanforderungen definiert.

Secure Startvorgang funktioniert wie folgt und wie in Abbildung 1 dargestellt:

1.  **Firmware Boot Komponenten:** Die Firmware überprüft Ladeprogramm des Betriebssystems ist vertrauenswürdig (Windows oder einem anderen vertrauenswürdigen Betriebssystem.)

2.  **Starten Sie Windows Komponenten: BootMgr WinLoad, Windows Kernel beim Starten.** Komponenten für Windows Start überprüfen Sie, ob die Signatur für jede Komponente. Alle nicht vertrauenswürdigen Komponenten werden nicht geladen und stattdessen Secure Boot Remediation ausgelöst werden.

    -   **Antivirus- und Antischadsoftware-Initialisierung:** Diese Software für eine spezielle Signatur sichergestellt haben, dass es sich um einen vertrauenswürdigen Boot wichtigen Treiber ist Microsoft einstufen aktiviert ist, und wird in den Startvorgang früh gestartet.

    -   **Kritische Boot-Treiber-Initialisierung:** Die Signaturen für alle wichtigen Treiber werden im Rahmen der Secure Boot Überprüfung im WinLoad überprüft.

3.  **Zusätzliche OS Initialisierung**

4.  **Windows-Anmeldebildschirm**

![Bild der Integrität Plattformarchitektur](images/dep-8-secureboot-platform-integrity-architecture.png)

*Abbildung 1: Windows vertrauenswürdige Boot-Architektur*

Implementierung von UEFI Secure Boot ist Teil der Architektur von Microsoft vertrauenswürdige Boot, in Windows 8.1 eingeführt. Bei der Entwicklung von Malware-Exploits vermehrt abzielt der Startpfad als eine bevorzugte Angriffen. Diese Klasse-Angriff wurde schwierig zum Schutz gegen, da Modul Produkte von Schadsoftware deaktiviert werden können, die verhindert, dass sie vollständig geladen. Mit Windows vertrauenswürdige Boot-Architektur und seiner Einrichtung eines Stammverzeichnisses der Vertrauensstellung mit Secure Boot kann der Kunde von bösartigen Code, die in der Startpfad durch sicherstellen, dass nur signierte, zertifizierten "bekannten ausreichend, gut" Code ausgeführt geschützt ist, und Boot Ladeprogramme können bevor das Betriebssystem selbst Lasten ausführen.

### <a name="span-id11public-keyinfrastructurepkiandsecurebootspanspan-id11public-keyinfrastructurepkiandsecurebootspanspan-id11public-keyinfrastructurepkiandsecurebootspan11-public-key-infrastructure-pki-and-secure-boot"></a><span id="1.1_Public-Key_Infrastructure__PKI__and_Secure_Boot"></span><span id="1.1_public-key_infrastructure__pki__and_secure_boot"></span><span id="1.1_PUBLIC-KEY_INFRASTRUCTURE__PKI__AND_SECURE_BOOT"></span>1.1 Public-Key-Infrastruktur (PKI) und sicheren Boot

Die PKI stellt Echtheit und Vertrauensstellung in einem System her. Secure Boot nutzt PKI für zwei allgemeine Zwecke:

1.  Während des Startvorgangs zu ermitteln, ob frühe Start-Module für die Ausführung als vertrauenswürdig gelten.

2.  Zum Authentifizieren werden ebenfalls Anfragen Serviceanfragen Secure Boot-Datenbanken und Updates auf Plattform Firmware ändern.

Eine PKI besteht aus:

-   Eine Zertifizierungsstelle (CA), die die digitale Zertifikate ausstellt.

-   Eine Registrierungsstelle die Identität von Benutzern, die von der Zertifizierungsstelle ein Zertifikat anfordern.

-   Einem zentralen Verzeichnis, in dem gespeichert und Indexschlüssel.

-   Ein Zertifikat Managementsystem.

### <a name="span-id12publickeycryptographyspanspan-id12publickeycryptographyspanspan-id12publickeycryptographyspan12-public-key-cryptography"></a><span id="1.2_Public_Key_Cryptography"></span><span id="1.2_public_key_cryptography"></span><span id="1.2_PUBLIC_KEY_CRYPTOGRAPHY"></span>1.2 öffentlichen Schlüsseln

Öffentlichem Schlüssel verwendet ein paar mathematisch verwandte kryptografischen Schlüssel, als öffentliche und private Schlüssel bezeichnet. Wenn Sie eine der Tasten kennen, berechnen nicht auf einfache Weise, was anderen angegeben ist. Wenn Sie einen Schlüssel zum Verschlüsseln von Informationen verwendet wird, kann nur mit der entsprechende Schlüssel, die betreffenden Informationen entschlüsseln. Für Secure Boot der private Schlüssel zum digitalen Signieren von Code verwendet wird, und der öffentliche Schlüssel zum Überprüfen der Signatur auf diesen Code zum Nachweis seiner Echtheit verwendet wird. Wenn Sie ein privater Schlüssel gefährdet ist, sind nicht mehr Systeme mit entsprechenden öffentlichen Schlüssel sicher. Dies kann dazu führen, dass Kit Angriffe starten und die Reputation der dafür verantwortlich, die Sicherheit des privaten Schlüssels sicherzustellen Entität wird beschädigen.

In einem öffentlichen Schlüssel Secure Boot-System müssen Sie Folgendes:

-   **1.2.1 RSA 2048-Verschlüsselung**

    RSA-2048 ist einem asymmetrischen kryptografischen Algorithmus. Die zum Speichern einer RSA 2048 Modulo unformatiert benötigten Speicherplatzes ist 2048 Bit.

-   **1.2.2 eines selbstsignierten Zertifikats**

    Ein Zertifikat signiert, durch den privaten Schlüssel, der mit den öffentlichen Schlüssel des Zertifikats übereinstimmt, wird als ein selbstsigniertes Zertifikat bezeichnet. Stammzertifizierungsstellen Zertifizierungsstelle (CA) Zertifikaten fallen in dieser Kategorie.

-   **1.2.3 Zertifizierungsstelle**

    Die Zertifizierungsstelle (CA) Probleme bei der Zertifizierungsstelle signiert Zertifikate, die die Identität des Betreffs Zertifikat bestätigen und Binden von dieser Identität auf den öffentlichen Schlüssel im Zertifikat enthalten. Die Zertifizierungsstelle signiert das Zertifikat mit dem privaten Schlüssel. Es gibt den entsprechenden öffentlichen Schlüssel an alle beteiligten Parteien in ein selbstsigniertes Stammzertifikat der Zertifizierungsstelle.

    In Secure Boot Zertifizierungsstellen (CAs) umfassen OEM (oder ihrer Stellvertreter) und Microsoft. Die CAs generiert die Schlüssel-Paaren, die bilden die vertrauenswürdige Stammzertifizierungsstelle, und klicken Sie dann die privaten Schlüssel verwenden, um legitime Vorgänge wie zulässig frühe Boot EFI Module und Behandlung Anfragen Firmware signieren. Die entsprechenden öffentlichen Schlüssel Secure Boot-fähige PCs in der Firmware UEFI eingebetteten geliefert werden und werden verwendet, um diese Vorgänge zu überprüfen.

    (Weitere Informationen zur Verwendung von Zertifizierungsstellen und Schlüsselaustausch ist auf das Internet auf die einzelnen Details des Modells Secure Boot bezieht verfügbar.)

-   **1.2.4 öffentlichen Schlüssel**

    Die Öffentlichkeit Plattformschlüssel verwendet werden soll, auf dem PC und ist verfügbar oder "public". In diesem Dokument werden wir das Suffix "Pub" verwenden, um die öffentlichen Schlüssel zu kennzeichnen. Angenommen, kennzeichnet die öffentliche Hälfte der PS. PKpub

-   **1.2.5 privaten Schlüssels**

    Für den privaten Schlüssel arbeiten PKI sicher verwaltet werden muss. Es sollten einige äußerst vertrauenswürdige Personen in einer Organisation zugänglich sein und befindet sich in einer physisch sicheren Ort mit strenge Richtlinie Einschränkungen vorhanden. In diesem Dokument verwenden wir das Suffix "Priv" privaten Schlüssel zu kennzeichnen. Beispielsweise gibt die PKpriv private Hälfte des die PS.

-   **1.2.6-Zertifikate**

    So überprüfen Sie den Ursprung des signierten Daten enthält, wie Binärdateien usw. wird vor allem verwendet für digitale Zertifikate. Eine häufige Verwendung von Zertifikaten ist für Internet Message Security Transport Layer Security (TLS) oder Secure Sockets Layer (SSL) verwenden. Überprüfen die signierten Daten mit einem Zertifikat den Empfänger die Herkunft der Daten ermöglicht, und wenn es während der Übertragung geändert wurde.

    Ein digitales Zertifikat hat, im Allgemeinen auf allgemeiner Ebene, einen definierten Namen (DN), einem öffentlichen Schlüssel und eine Signatur enthält. Der DN identifiziert eine Entität – ein Unternehmen, beispielsweise –, die den privaten Schlüssel enthält, der mit den öffentlichen Schlüssel des Zertifikats übereinstimmt. Signieren das Zertifikat mit einem privaten Schlüssel und das Zertifikat die Signatur versehen verbindet den privaten Schlüssel auf den öffentlichen Schlüssel.

    Zertifikate können einige andere Typen von Daten enthalten. Ein x. 509-Zertifikat umfasst beispielsweise das Format des Zertifikats, die Seriennummer des Zertifikats, den Algorithmus zum Signieren des Zertifikats, den Namen der Zertifizierungsstelle, die das Zertifikat, den Namen und den öffentlichen Schlüssel der Entität anfordern des Zertifikats und Signatur der Zertifizierungsstelle ausgestellt.

-   **1.2.7 Verketten von Zertifikaten**

    Von: [Zertifikatketten](http://go.microsoft.com/fwlink/?LinkId=321183):

    ![Stammzertifizierungsstelle ist selbstsigniert, andere Personen von Stammzertifizierungsstelle signiert](images/dep-8-secureboot-threecertificatechain.png)

    *Abbildung 2: Drei-Zertifikatkette*

    Von Benutzerzertifikaten werden häufig von einer anderen privaten Schlüssel, beispielsweise einen privaten Schlüssel der Zertifizierungsstelle signiert. Dies stellt eine zwei-Zertifikatkette. Überprüfen, ob ein Benutzerzertifikat genuine ist umfasst, überprüfen die Signatur, die den öffentlichen Schlüssel der Zertifizierungsstelle, aus dessen Zertifikat erforderlich sind. Aber bevor des öffentlichen Schlüssels der Zertifizierungsstelle, die verwendet werden kann, muss das Zertifikat der einschließende überprüft werden. Da das Zertifizierungsstellen-Zertifikat selbstsigniert ist, wird der öffentliche Schlüssel Zertifizierungsstelle das Zertifikat überprüfen.

    Ein Benutzerzertifikat muss nicht von der private Schlüssel des das Stammzertifikat der Zertifizierungsstelle signiert sein. Es konnte von der private Schlüssel des Vermittlung signiert sein, dessen Zertifikat mit dem privaten Schlüssel der Zertifizierungsstelle signiert wurde. Dies ist eine Instanz einer drei Zertifikatkette: Benutzerzertifikat, zwischengeschaltete Zertifikat und das Zertifikat. Mehr als ein Kontakt kann jedoch Kettenglied, damit Zertifikatketten beliebig lang sein können.

### <a name="span-id13securebootpkirequirementsspanspan-id13securebootpkirequirementsspanspan-id13securebootpkirequirementsspan13-secure-boot-pki-requirements"></a><span id="1.3_Secure_Boot_PKI_requirements"></span><span id="1.3_secure_boot_pki_requirements"></span><span id="1.3_SECURE_BOOT_PKI_REQUIREMENTS"></span>1.3 secure Boot PKI-Anforderungen

Vertrauenswürdige Stammzertifizierungsstelle UEFI definiert besteht aus den Plattform-Schlüssel, und alle Schlüssel ein OEM oder ODM enthält, in der Firmware Core. Älter als Version UEFI Sicherheit und eine vertrauenswürdige Stammzertifizierungsstelle werden nicht durch den Prozess UEFI Secure Boot sondern durch National Institute of Standards und Technology (NIST) und Trusted Computing Group (TCG) Publikationen auf die in diesem Dokument verwiesen wird behandelt werden.

-   **1.3.1 secure Boot-Anforderungen**

    Sie müssen die folgenden Parameter für die Implementierung von Secure Boot berücksichtigen:

    -   Kunden-Anforderungen

    -   Windows-Hardware-Kompatibilität

    -   Erzeugung und Anforderungen für das Projektmanagement.

    Sie müssen Hardware für Secure Boot Key Management wie Hardware Security Modules (HSMs) auswählen, sollten spezielle Anforderungen auf PCs an Behörden und anderen Behörden und schließlich auf den Prozess der Erstellung, Auffüllen und Verwalten des Lebenszyklus der verschiedenen Secure Boot Schlüssel geliefert.

-   **1.3.2 sicheren Boot weiterführende Schlüssel**

    Die Schlüssel für Secure Boot verwendet werden unter:

    ![PK, Kek, Db, Dbx und Firmware-Schlüssel Winrt-Schlüssel](images/dep-8-secureboot-allkeys.png)

    *Abbildung 3: Schlüssel im Zusammenhang mit Secure Boot*

    Abbildung 3 oben stellt die Signaturen und Schlüssel in einem PC mit Secure Start. Die Plattform ist über einen Plattformschlüssel gesichert, die der OEM in Firmware während der Herstellung installiert. Andere Schlüssel werden von Secure Boot zum Schutz des Zugriffs auf Datenbanken, bei denen Schlüssel zulassen oder verweigern die Ausführung der Firmware gespeichert.

    Die autorisierte Datenbank (Db) enthält die öffentlichen Schlüssel und Zertifikate, die vertrauenswürdige Firmware Komponenten und Loader-Programmen Operating System darstellen. Die Signaturdatenbank unzulässige (Dbx) Hashes bösartige und anfällig Komponenten enthält als auch Schlüsseln und Zertifikaten und Blöcke Ausführung dieser böswilligen Komponenten gefährdet. Die Stärke des diese Richtlinien basiert auf Signieren Firmware mit Authenticode und Public Key-Infrastruktur (PKI). PKI ist ein etablierten Prozess für das Erstellen und Verwalten von Sperren von Zertifikaten, die während der Informationsaustausch Vertrauensstellung einrichten. PKI ist das Herzstück über das Sicherheitsmodell für Secure Boot.

    Im folgenden sind weitere Details für diese Schlüssel.

-   **1.3.3 Plattform Schlüssel (PK)**

    Gemäß den Anweisungen im Abschnitt 27.5.1 der UEFI 2.3.1 Fehlerverzeichnis C richtet Schlüssels Plattform eine Vertrauensstellung zwischen den Plattform-Besitzer und die Plattform Firmware. Der Besitzer Plattform registriert die öffentliche Hälfte des Schlüssels (PKpub) in die Plattform Firmware gemäß **Abschnitt 7.2.1 der UEFI 2.3.1 Fehlerverzeichnis C**ein. Dieser Schritt wird die Plattform in Benutzermodus vom Setupmodus verschoben. Microsoft empfiehlt, die Plattform-Taste vom Typ **EFI\_CERT\_X509\_GUID** mit Algorithmus für öffentliche Schlüssel RSA von 2.048 Bit lang und Signatur Algorithmus sha256RSA Länge des öffentlichen Schlüssels. Der Plattform Besitzer können Typ **EFI\_CERT\_Rsa2048\_GUID** Wenn Speicherplatz von Belang ist. Öffentliche Schlüssel dienen zum Überprüfen von Signaturen, wie weiter oben in diesem Dokument beschrieben. Der Besitzer Plattform können später die private Hälfte des Schlüssels (PKpriv):

    -   Um Plattform Besitzer ändern, die Sie in die Firmware einfügen müssen definiert UEFI **Installationsmodus** Secure Boot wird deaktiviert. Es wird empfohlen, nur dann, wenn während der Herstellung hierzu müssen Installationsmodus wiederherstellen.
    
    -   Verwalten von für desktop-PC OEMs PK und erforderlichen PKI zugeordnet. Für Server, OEMs standardmäßig PK und erforderlichen PKI verwalten. Unternehmenskunden oder Server-Kunden können auch PS, Anpassen der OEM-vertrauenswürdige PK durch eine benutzerdefinierte proprietären PK zum Sperren der Vertrauensstellung in UEFI Secure Boot Firmware auf sich selbst ersetzen.

    **1.3.3.1 zu registrieren oder Aktualisieren einer Taste Exchange Schlüssel (KEK) zum Registrieren von der Plattform-Schlüssel**

    Der Besitzer Plattform registriert die öffentliche Hälfte des Schlüssels-Plattform (**PKpub**) durch den Aufruf der UEFI Boot Service SetVariable() als im angegebenen Abschnitt 7.2.1 UEFI Spec 2.3.1 fehlerverzeichnis C und Zurücksetzen der Plattform. Wenn die Plattform im Setup-Modus ist, wird die neue **PKpub** mit Gegenstück **PKpriv** signiert werden. Ist die Plattform im Benutzermodus, muss die neue **PKpub** mit der aktuellen **PKpriv**signiert werden. Wenn die PK vom Typ ist **EFI\_CERT\_X509\_GUID**, klicken Sie dies durch die sofortige **PKpriv**, nicht für einen privaten Schlüssel alle unter die PS. Zertifikat signiert werden muss

    **1.3.3.2 löschen, die Plattform-Taste**

    Der Besitzer Plattform werden durch Aufrufen der UEFI Boot Ser¬vice SetVariable() mit einer Variablen Größe von 0 und Zurücksetzen der Plattform die öffentliche Hälfte des Schlüssels-Plattform (**PKpub**) gelöscht. Wenn die Plattform im Setup-Modus ist, klicken Sie dann muss die leere Variable nicht authentifiziert werden. Ist die Plattform im Benutzermodus, muss die leere Variable mit der aktuellen **PKpriv**signiert werden; finden Sie im Abschnitt 7.2 (Variable Dienste) unter [UEFI Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) 2.3.1 Fehlerverzeichnis C für Details. Es wird dringend empfohlen, dass die Produktion PKpriv zum Signieren eines Pakets an die Plattform zurücksetzen, da dadurch Secure Boot programmgesteuert deaktiviert werden nie verwendet werden. Dies ist in erster Linie ein Präproduktion Testszenario aus.

    Die Plattform-Taste kann auch mithilfe einer sicheren plattformspezifische Methode gelöscht werden soll. In diesem Fall muss die globale Variable Installationsmodus auch auf 1 aktualisiert werden.

    ![Bild: Pk bestimmt Setup-Modus oder im Benutzermodus](images/dep-8-secureboot-pkstate.png)

    *Abbildung 4: Plattform Schlüssel-Statusdiagramm*

    **1.3.3.3 PK-Generierung**

    Gemäß den Anweisungen in UEFI Recommendations muss der öffentliche Schlüssel in permanenter Speicher manipuliert wird gespeichert und gegen löschen auf dem PC. Der Private Schlüssel sichere Partner oder in des OEMs Sicherheit Office bleiben, und nur der öffentliche Schlüssel auf der Plattform geladen wird. Es sind weitere Details im Abschnitt 2.2.1 und 2.3.

    Die Anzahl der PK generiert wird im Ermessen des Besitzers Plattform (OEM). Hierüber sind möglich:

    1.  **Eine pro PC**. Müssen Sie einen eindeutigen Schlüssel für jedes Gerät. Dies kann für Behörden, Finanzinstituten oder andere Server-Kunden mit Hochsicherheitsmodus Anforderungen erforderlich sein. Zusätzlicher Speicher und Kryptografie Leistung zum Generieren von privaten und öffentlichen Schlüssel für eine große Anzahl von PCs vorschreiben. Dadurch wird die Komplexität der Zuordnung Geräte mit ihren entsprechenden PK hinzugefügt, wenn in der Zukunft Firmware-Updates für die Geräte pushen. Es gibt einige andere HSM-Lösungen für große Anzahl von Schlüssel basierend auf der HSM-Händler verwalten verfügbar. Weitere Informationen finden Sie unter [Secure Boot Key Generation mithilfe von HSM](http://go.microsoft.com/fwlink/?LinkId=321184).

    2.  **Eine Tabelle pro Modell**. Wenn eine Taste pro PC-Modell. Hier der Nachteil ist, dass bei einem Angriff auf ein Schlüssel allen Computern innerhalb desselben Modells anfällig wäre. Dies ist für desktop-PCs von Microsoft empfohlen.

    3.  **Eine pro Produktlinie**. Wenn eine Taste gefährdet ist wäre anfällig eine gesamte Produktlinie.

    4.  **Eine pro OEM**. Während dies am einfachsten eingerichtet sein, wenn der Schlüssel gefährdet ist, wird jeder PC hergestellten betroffen sein. Um werksseitige Vorgang beschleunigen, konnte der PK und potenziell andere Tasten vorab generiert und an einem sicheren Ort gespeichert werden. Diese können später abgerufen und in der Zeile Assembly verwendet. Kapitel 2 und 3 haben weitere Details.

    **1.3.3.4 Erstellen neuer Schlüssel den PK**

    Dies kann die PK gefährdet dient zum Abrufen oder als eine Anforderung von einem Kunden erforderlich sein, die aus Sicherheitsgründen beschließen, registrieren Sie ihre eigenen PS.

    Erstellen neuer Schlüssel konnte vorgenommen werden, entweder für ein Modell oder PC basierend auf welche Methode zum Erstellen von PS. ausgewählt wurde Alle neueren PCs werden mit der neu erstellten PS. signiert abrufen

    Aktualisieren der PK auf einem Produktions-PC, müsste entweder eine Variable mit der vorhandenen PK, der die PK oder eine Firmware-Updatepaket ersetzt signiert aktualisieren. OEM kann auch SetVariable() erstellen und verteilen, die mit einer einfachen Anwendung wie PowerShell, die nur die PS. ändert Das Firmware-Updatepaket würde durch den sicheren Firmware Update Key signiert und von der Firmware bestätigt werden. Wenn einer Firmware Update zum Aktualisieren der PK Weise vorgenommen um sicherzustellen, dass die KEK Db und Dbx werden beibehalten.

    Auf allen PCs wird nicht verwenden die PK als Schlüssel sichere Firmware Update empfohlen. Wenn die PKpriv gefährdet ist trifft dies der Schlüssel sichere Firmware Update (da diese identisch sind). In diesem Fall möglicherweise das Update zum Registrieren einer neuen PKpub nicht möglich, da der Vorgang der Aktualisierung auch beeinträchtigt wurde.

    Auf SOCs PCs ist ein weiterer Grund für die PK nicht als sichere Firmware Update Schlüssel verwendet werden. Dies ist, da der Schlüssel sichere Firmware Update dauerhaft gebrannt in auf PCs fixiert ist, die Windows-Hardware-Zertifizierung Anforderungen erfüllen.

-   **1.3.4 wichtige Exchange-Taste (KEK)** Austausch der Sitzungsschlüssel Schlüssel Einrichten einer Vertrauensstellung zwischen dem Betriebssystem und die Plattform Firmware. Jedes Betriebssystem (und potenziell, jede 3rd Party-Anwendung die Kommunikation mit Plattform Firmware müssen) registriert einen öffentlichen Schlüssel (**KEKpub**) in der Firmware Plattform.

    **1.3.4.1 zum Registrieren von Austausch der Sitzungsschlüssel Schlüssel**

    Austausch der Sitzungsschlüssel Schlüssel werden in einer Signaturdatenbank gespeichert, wie in [1,4 Signatur-Datenbanken (Db und Dbx)](#signaturedatabase)beschrieben. Die Signaturdatenbank ist als authentifizierter UEFI Variable gespeichert.

    Der Besitzer Plattform registriert die Schlüssel Austausch der Sitzungsschlüssel durch entweder aufrufende SetVariable() als im angegebenen Abschnitt 7.2 (Variable Services) unter [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) 2.3.1 Fehlerverzeichnis C. mit EFI\_VARIABLE\_APPEND\_SCHREIBEN Attributsatz und der Data-Parameter, die dem neuen Schlüssel enthält oder die Datenbank mithilfe des GetVariable() Beitrag, Anhängen die neue Schlüsselaustausch-Taste, um die vorhandenen Schlüssel, und klicken Sie dann die Datenbank mithilfe der Funktionen ' SetVariable ' () als im angegebenen Abschnitt 7.2 (Variable Services) unter [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) 2.3.1 Fehlerverzeichnis C ohne Schreiben der EFI\_VARIABLE\_APPEND\_Attributsatz SCHREIBEN.

    Wenn die Plattform im Modus der Installation ist, die Signatur Datenbankvariable muss nicht signiert werden, aber die Parameter für den Aufruf der SetVariable() weiterhin als vorbereitet werden werden festgelegt für authentifizierte Variablen in Abschnitt 7.2.1. Wenn die Plattform im Benutzermodus ist, muss die Signaturdatenbank mit den aktuellen PKpriv signiert werden

    **1.3.4.2 clearing der KEK**

    Es ist möglich, "Clear" (löschen) der KEK. Beachten Sie, wenn die PK auf der Plattform nicht installiert ist, "clear" Anforderungen nicht signiert werden. Wenn sie angemeldet sind, klicken Sie dann zum Löschen der KEK erfordert ein Paket PK signiert und Db oder Dbx deaktivieren erfordert ein Paket signiert von allen in der KEK vorhanden.

    **1.3.4.3 Microsoft KEK**

    Die Microsoft-KEK ist erforderlich, um die Sperrung von ungültigen Abbildern aktivieren, indem Sie die Dbx aktualisieren und potenziell zum Aktualisieren der Db zur Vorbereitung der neueren Windows signiert Bilder.

    Fügen Sie der Microsoft Corporation KEK Zertifizierungsstelle 2011 in der KEK-Datenbank mit den folgenden Werten:

    -   SHA-1-Cert Hash: `31 59 0b fd 89 c9 d7 4e d0 87 df ac 66 33 4b 39 31 25 4b 30`.

    -   SignatureOwner GUID: `{77fa9abd-0359-4d32-bd60-28f4e78f784b}`.

    -   Microsoft bietet das Zertifikat für Partner und hinzugefügt werden entweder als ein **EFI\_CERT\_X509\_GUID** oder ein **EFI\_CERT\_Rsa2048\_GUID** Typsignatur.

    Das Zertifikat Microsoft KEK kann heruntergeladen werden: <http://go.microsoft.com/fwlink/?LinkId=321185>.

    **1.3.4.4 KEKDefault** Die Serverplattform-Anbietern kann einen Standardsatz Key Exchange Schlüssel in der Variablen KEKDefault angeben. Bitte [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) Abschnitt 27.3.3 Weitere Informationen zu verweisen.

    **1.3.4.5 OEM / 3. KEK - mehrere KEK Hinzufügen von Drittanbietern**

    Kunden und Besitzer Plattform müssen nicht ihren eigenen KEK haben. Auf nicht - Windows RT-PCs müssen OEM möglicherweise zusätzliche KEKs, um zusätzliche OEM oder eines vertrauenswürdigen erlauben 3. Partei Steuerung der Db und Dbx.
 
-   **1.3.5 secure Boot Firmware Update Schlüssel** Der Schlüssel für sichere Firmware Update wird die Firmware zu signieren, wenn es aktualisiert werden muss. Dieser Schlüssel verfügt über eine minimale Stärke des Schlüssels RSA-2048 verwendet haben. Alle Firmwareupdates müssen sicher vom OEM, vertrauenswürdigen Stellvertreter wie die ODM oder IBV (Independent BIOS-Anbieter) oder von einem sicheren signierenden Dienst angemeldet sein.

    Alle Elemente der Richtlinien muss gemäß den Anweisungen in [NIST Publikation 800-147 Feld Firmware Update](http://go.microsoft.com/fwlink/?LinkId=321186) unterstützen:

    Eine Aktualisierung der Firmware flash-Speicher muss vom Ersteller signiert werden.

    Firmware muss Signatur des Updates überprüfen.

-   **1.3.6 Erstellung von Schlüsseln für Firmwareupdates Secure**

    Demselben Schlüssel dienen alle Firmwareupdates seit der Öffentlichkeit anmelden, die Hälfte auf dem PC befinden wird. Sie konnte das Firmware-Update auch mit einem Schlüssel signieren welche Lieferketten Secure Firmware Schlüssel aktualisieren.

    Es kann einen Schlüssel pro PC wie PS oder eine Tabelle pro Modell oder eine pro Zeile Produkt. Wenn es einen Schlüssel pro PC, die bedeuten würde, dass Millionen von eindeutigen Updatepakete generiert werden müssen. Erwägen Sie, basierend auf ressourcenverfügbarkeit, welche Methode Sie funktionieren würde. Ein Schlüssel pro Modell oder Produktlinie ist einen guten Kompromiss.

    Würde den öffentlichen Schlüssel Secure Firmware Update (oder dessen Hash um Speicherplatz einzusparen) gespeichert werden in einigen geschützten Speicher auf die Plattform – im Allgemeinen geschützt, Flash (PC) oder one-einmalig programmierbare fixiert (SOC).

    Wenn nur der Hash der dieser Schlüssel (um Speicherplatz zu sparen) gespeichert wird, und klicken Sie dann die Aktualisierung der Firmware Sie den Schlüssel schließen wird und die erste Phase des Prozesses Update überprüfen, die ermittelt des öffentlichen Schlüssels im Update des Hashs der Plattform gespeichert.

    Kapseln sind eine Möglichkeit, nach denen das Betriebssystem Daten UEFI-Umgebung in einen Neustart übergeben können. Windows ruft die UEFI UpdateCapsule() bis auf System und PC Firmwareupdates übermitteln. Beim Start vor dem Aufrufen von ExitBootServices () wird Windows in neue Firmwareupdates gefunden in Windows Store-Treiber in UpdateCapsule() übergeben. Dieser Prozess können UEFI Systemfirmware um bis auf System und PC-Firmware zu aktualisieren. Durch Nutzung dieser Windows Firmware-Unterstützung kann OEM auf die gleiche allgemeine Format und Prozess zum Aktualisieren der Firmware für sowohl System und PC-Firmware verlassen. Firmware muss die Tabelle ACPI ESRT zur Unterstützung der UEFI UpdateCapsule() für Windows implementieren.

    Für Informationen zum Implementieren der Unterstützung für die Plattform Windows UEFI Firmware Update finden Sie in der folgenden Dokumentation: Windows UEFI Firmware Update-Plattform.

    Update kapseln kann im Arbeitsspeicher oder auf dem Datenträger. Windows unterstützt in Speicher aktualisiert.

    **1.3.6.1 "Kapseln" ("Kapseln" im Arbeitsspeicher)**

    Folgendes ist der Ablauf der Ereignisse für eine In-Memory-Update "Kapseln" funktioniert.

    1.  Eine "Kapseln" wird im Speicher von einer Anwendung in das Betriebssystem abgelegt.

    2.  Postfach-Ereignis ist auf BIOS von ausstehenden Updates informieren festgelegt

    3.  PC neu gestartet wird, überprüft das ' Kapseln ' Bild und Update erfolgt über das BIOS

-   **1.3.7 Workflow für eine typische Firmware-Aktualisierung**

    1.  Herunterladen und Installieren des Firmware-Treibers.

    2.  Starten Sie neu.

    3.  OS Loader erkennt und überprüft, ob die Firmware.

    4.  OS Loader übergibt ein binäres Blob an UEFI.

    5.  UEFI führt die Firmware-Aktualisierung (dieser Prozess wird die Halbleiterhersteller als Besitzer).

    6.  OS Loader Erkennung erfolgreich abgeschlossen.

    7.  OS Bootvorgang abgeschlossen hat.

### <a name="span-idsignaturedatabasespanspan-idsignaturedatabasespanspan-idsignaturedatabasespan14-signature-databases-db-and-dbx"></a><span id="SignatureDatabase"></span><span id="signaturedatabase"></span><span id="SIGNATUREDATABASE"></span>1.4 Signatur-Datenbanken (Db und Dbx)

-   **1.4.1 zulässige Signatur-Datenbank (Db)**

    Der Inhalt der EFI \_BILD\_SECURITY\_DATENBANK Db steuern, welche Bilder beim Überprüfen der geladenen Bilder vertrauenswürdig sind. Die Datenbank kann mehrere Zertifikate, Schlüssel und Hashes zum Identifizieren der zulässigen Bilder enthalten.

    Die **Microsoft Windows Produktion PCA 2011** mit einem SHA-1 Cert Hash des `58 0a 6f 4c c4 e4 b6 69 b9 eb dc 1b 2b 3e 08 7b 80 d0 67 8d` muss in der Datenbank enthalten sein, damit das Windows-Betriebssystem-Ladeprogramm geladen werden können. Der Windows-Zertifizierungsstelle kann hier heruntergeladen werden: <http://go.microsoft.com/fwlink/p/?linkid=321192>.

    Klicken Sie auf nicht - Windows RT-PCs OEM sollten einschließlich der **Microsoft Corporation UEFI Zertifizierungsstelle 2011** mit einem Zertifikathash SHA-1, der `46 de f6 3b 5c e6 1c f8 ba 0d e2 e6 63 9c 10 19 d0 ed 14 f3`. Signieren UEFI können Faktoren und Clientanwendungen mit dieses Zertifikats UEFI Faktoren und Anwendungen von Drittanbietern 3. auf dem PC ausgeführt werden, ohne zusätzliche Schritte für den Benutzer ansetzt. Die Zertifizierungsstelle UEFI kann hier heruntergeladen werden: <http://go.microsoft.com/fwlink/p/?linkid=321194>.

    Auf nicht - Windows RT-PCs OEM auch möglicherweise zusätzliche Elemente in der Datenbank, um andere Betriebssysteme oder OEM-approved UEFI Treiber oder apps zu ermöglichen, aber diese Bilder müssen die Sicherheit des PCs keinerlei nicht gefährden.

-   **1.4.2 DbDefault**: die Plattform Hersteller vorsehen einen Standardsatz von Einträgen für die Datenbank Signatur in der Variablen DbDefault. Weitere Informationen finden Sie im Abschnitt 27.5.3 UEFI-Spezifikation.

-   **1.4.3 unzulässige Signaturdatenbank (Dbx)**

    Der Inhalt der **EFI\_BILD\_SIGNATUR\_DATABASE1** Dbx muss überprüft werden, wenn die Bilder überprüfen, bevor dieser Db und keine Übereinstimmung überprüft das Bild aus der Ausführung verhindern muss. Die Datenbank kann mehrere Zertifikate, Schlüssel und Hashes, um identifizieren verbotene Bilder enthalten. Die Windows-Zertifizierung Hardwareanforderungen, dass ein Dbx vorhanden ist, stehen muss, damit eine-Wert wie der SHA-256 Hash Dummy state `0`, können als sichere Platzhalter verwendet werden, solange diese Microsoft beginnt spielt Dbx Updates. [Klicken Sie hier](http://www.uefi.org/revocationlistfile) zum Herunterladen der neuesten UEFI Sperrliste von Microsoft.

-   **1.4.4 DbxDefault**: die Plattform Hersteller vorsehen einen Standardsatz von Einträgen für die Datenbank Signatur in der Variablen DbxDefault. Weitere Informationen finden Sie im Abschnitt 27.5.3 UEFI-Spezifikation.

### <a name="span-id15keysrequiredforsecurebootonallpcsspanspan-id15keysrequiredforsecurebootonallpcsspanspan-id15keysrequiredforsecurebootonallpcsspan15-keys-required-for-secure-boot-on-all-pcs"></a><span id="1.5_Keys_Required_for_Secure_Boot_on_all_PCs"></span><span id="1.5_keys_required_for_secure_boot_on_all_pcs"></span><span id="1.5_KEYS_REQUIRED_FOR_SECURE_BOOT_ON_ALL_PCS"></span>1,5 Schlüssel zum Start auf alle PCs Secure erforderliche

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Name der Key-db</th>
<th align="left">Variable</th>
<th align="left">Besitzer</th>
<th align="left">Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>PKpub</p></td>
<td align="left"><p>PK</p></td>
<td align="left"><p>OEM</p></td>
<td align="left"><p>PK – nur 1. RSA muss 2048 oder stärkere sein.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Corporation KEK Zertifizierungsstelle 2011</p></td>
<td align="left"><p>KEK</p></td>
<td align="left"><p>Microsoft</p></td>
<td align="left"><p>Ermöglicht Db und Dbx-Updates:</p>
<p>[http://go.microsoft.com/fwlink/p/?linkid=321185](http://go.microsoft.com/fwlink/p/?linkid=321185).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft Windows-Produktion Zertifizierungsstelle 2011</p></td>
<td align="left"><p>DB</p></td>
<td align="left"><p>Microsoft</p></td>
<td align="left"><p>Diese Zertifizierungsstelle in der Signatur-Datenbank (Db) ermöglicht Windows für das starten: [http://go.microsoft.com/fwlink/?LinkId=321192](http://go.microsoft.com/fwlink/?LinkId=321192).</p></td>
</tr>
<tr class="even">
<td align="left"><p>Unzulässige Signaturdatenbank</p></td>
<td align="left"><p>dbx</p></td>
<td align="left"><p>Microsoft</p></td>
<td align="left"><p>Liste der bekannten fehlerhafte Schlüssel, CAs oder Bilder von Microsoft.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sichern der Firmware Update-Taste</p></td>
<td align="left"><p></p></td>
<td align="left"><p>OEM</p></td>
<td align="left"><p>Es wird empfohlen, diesen Schlüssel von PK abweichen haben</p></td>
</tr>
</tbody>
</table>

 

*Tabelle 1: Schlüssel/Db für Secure Boot erforderlich ist*


## <a name="span-idkeymanagementsolutionsspanspan-idkeymanagementsolutionsspanspan-idkeymanagementsolutionsspan2-key-management-solutions"></a><span id="KeyManagementSolutions"></span><span id="keymanagementsolutions"></span><span id="KEYMANAGEMENTSOLUTIONS"></span>2. Key Management-Lösungen


Im folgenden werden einige der Metriken der angegebene wir für den Vergleich verwendet.

### <a name="span-id21metricsusedspanspan-id21metricsusedspanspan-id21metricsusedspan21-metrics-used"></a><span id="2.1_Metrics_used"></span><span id="2.1_metrics_used"></span><span id="2.1_METRICS_USED"></span>2.1 Auswertungskriterien

Die folgenden Metriken helfen Ihnen die eines HSM-PCs hängt von den Anforderungen von [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) 2.3.1 Fehlerverzeichnis C und Ihren Anforderungen zu aktivieren.

**Public Key Infrastruktur (PKI) Weiterführende**

-   Unterstützt RSA 2048 oder höher? -Der [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) 2.3.1 Fehlerverzeichnis C empfiehlt die Schlüssel RSA-2048 oder besser sein.

-   Hat es die Möglichkeit zum Generieren von Schlüsseln und melden Sie sich?

-   Wie viele Schlüssel kann es werden gespeichert? Speichert es Schlüssel auf HSM oder angefügte-Server?

-   Authentifizierungsmethode für wichtige abrufen.

    Einige PCs unterstützt mehrere Authentifizierung Entitäten für den Abruf von Schlüssel vorhanden sind.

**Preise**

-   Was ist der Preis? HSMs können Preis 1.500 €70.000 je nach verfügbaren Funktionen umfassen.

**Fertigung-Umgebung**

-   Geschwindigkeit des Vorgangs in Fabrik. Erstellen und Access können Kryptografie Prozessoren beschleunigen.

-   Einfaches Setup, Bereitstellung, Wartung.

-   Skillset und Schulung erforderlich?

-   Netzwerkzugriff für die Sicherung und hohe Verfügbarkeit

**Standards und Kompatibilität**

-   Welche Ebene der FIPS-Konformität ist hat er? Ist es vor Missbrauch?

-   Unterstützung für andere Standards, beispielsweise MS Kryptografie-APIs.

-   Erfüllen es Behörden und andere Agency?

**Zuverlässigkeit und Disaster recovery**

-   Ermöglicht es für die Sicherung Schlüssel?

    Sicherungen gespeichert werden können sowohl vor Ort, an einem sicheren Ort, die einem anderen physischen Standort als die Zertifizierungsstellencomputer und HSM und und/oder an einem anderen Standort ist.

-   Können für hohe Verfügbarkeit für die Wiederherstellung zu?

### <a name="span-id22keymanagementoptionsspanspan-id22keymanagementoptionsspanspan-id22keymanagementoptionsspan22-key-management-options"></a><span id="2.2_Key_Management_Options"></span><span id="2.2_key_management_options"></span><span id="2.2_KEY_MANAGEMENT_OPTIONS"></span>2.2 Schlüsselverwaltungsdienst-Optionen

-   **2.2.1 Hardware Security Module (HSM)**

    Basierend auf den oben aufgeführten Kriterien ist dies wahrscheinlich die am besten geeigneten und sichere Lösung. Die meisten HSM haben FIPS 140-2 Level 3 Compliance. FIPS 140-2 Level 3 Compliance ist strenge Authentifizierung und erfordert, dass der Schlüssel nicht exportiert oder von der HSM importiert werden.

    Sie unterstützen verschiedene Arten der Speicherung von Schlüsseln. Sie können entweder lokal auf dem Hardwaresicherheitsmodul selbst oder auf dem Server, der HSM zugeordnet ist, gespeichert werden. Die Schlüssel verschlüsselt werden, und die auf dem Server gespeichert und empfiehlt sich für Lösungen, die viel Schlüssel zu speichernden erforderlich sind.

    Die kryptografische Modul Codezugriffssicherheits-Richtlinie ist eine physische Sicherheitsrichtlinien, einschließlich physischen Sicherheitsmechanismen, die in einem Modul kryptografische, z. B. implementiert werden, manipuliert Inhaltselements Siegel, sperren, manipuliert Antwort und Zeroization Switches und Alarmen anzugeben. Darüber hinaus können mithilfe der Operatoren erforderliche, um sicherzustellen, dass physische Sicherheit verwaltet wird, wie regelmäßige Überprüfung der manipuliert Inhaltselements Siegel oder Testen von manipuliert Antwort und Zeroization Switches Aktionen angeben.

    **2.2.1.1 HSM Netzwerk**

    Diese Lösung ist am besten in seiner Klasse im Hinblick auf Sicherheit, Einhaltung der Standards (engl.), Key Generation, speichern und abrufen. Die meisten dieser PCs hohe Verfügbarkeit und haben die Möglichkeit zum backup-Schlüssel.

    Die Kosten für diese Produkte darf Zehntausende Dollar basierend auf der zusätzlichen Dienste, die sie bieten.

    **2.2.1.2 eigenständig HSM**

    Diese funktionieren hervorragend mit Standalone-Server. Eine kann Microsoft CAPI und CNG oder andere von HSM unterstützt und sichere API verwenden. Diese HSMs sind in verschiedenen Formfaktoren USB-, PCIe und PCMCIA-Bus unterstützen.

    Sie unterstützen optional Sicherung und hohe Verfügbarkeit.

-   **2.2.2 benutzerdefinierte Lösungsanbieter**

    Public Key-Kryptografie kann eine Herausforderung sein und erfordern ein Verständnis des kryptografischen Konzepte welche möglicherweise neu. Sind benutzerdefinierte Lösungsanbieter, die mit der erste Secure Boot-Hilfe konnte in der Fertigung-Umgebung arbeiten.

    Es sind Varianten von benutzerdefinierten Lösungen angebotenen BIOS-Herstellern, HSM Unternehmen und PKI consulting Unternehmen Secure Boot PKI arbeiten in der Fertigung Umgebung abzurufen.

    Einige der Anbieter sind unten aufgeführt:

    **2.2.2.1 BIOS-Herstellern**

    Einige BIOS-Lieferanten für die Bereitstellen von benutzerdefinierten Lösungen möglicherweise sind vorhanden.

    **2.2.2.2 HSM Lieferanten**

    Einige HSM Anbieter möglicherweise benutzerdefinierten consulting bereitzustellen. Weitere Informationen finden Sie unter [Secure Boot Schlüssel generieren und die Signierung mithilfe von Entsprechenden (Beispiel)](secure-boot-key-generation-and-signing-using-hsm--example.md).

-   **2.2.3 trusted Platform Module (TPM)**

    Ein Modul TPM (Trusted Platform) ist ein Hardwarechip auf der Hauptplatine, die kryptografische Schlüssel für die Verschlüsselung gespeichert werden. Viele Computer verfügen über ein TPM, jedoch wenn der PC enthalten nicht, ist es nicht möglich, einen hinzufügen. Nach der Aktivierung kann der Trusted Platform Module sichere vollständige Datenträger Verschlüsselung Produkte wie Microsoft BitLocker-Funktionen helfen. Behält Festplatten gesperrt oder versiegelt, bis der PC ein System Überprüfung-Authentifizierung oder der Vorgang abgeschlossen ist.

    Das TPM kann generieren, speichern und bei der Verschlüsselung und Entschlüsselung verwendeten Schlüssel schützen.

    Nachteile des TPMs sind, dass es keine fast Kryptografie Prozessoren, um die Verarbeitung in der Fertigung-Umgebung zu beschleunigen besitzen. Sie sind auch nicht zum Speichern von großen Anzahl von Schlüsseln geeignet. Sicherung und hohe Verfügbarkeit und Einhaltung von Standards FIPS 140-2 auf 3 möglicherweise nicht zur Verfügung.

-   **2.2.4 Smart Karten**

    Eine Smartcard können generieren und Schlüssel speichern. sie einige Features, welche HSM Support, wie Authentifizierung und manipuliert Proofing, freigeben, die nicht viel Speicherung von Schlüsseln oder Sicherung enthalten jedoch. Sie eingreifen und möglicherweise nicht geeignet für Automatisierung und Verwendung in der produktionsumgebung als die vielleicht geringe Leistung.

    Die Nachteile der Smart-Karten ähneln TPMs. Sie verfügen nicht über die fast Kryptografie Prozessoren, um die Verarbeitung in der Fertigung-Umgebung zu beschleunigen. Sie sind auch nicht zum Speichern von großen Anzahl von Schlüsseln geeignet. Sicherung und hohe Verfügbarkeit und Einhaltung der Standards FIPS 140-2 Level 3 möglicherweise nicht zur Verfügung.

-   **2.2.5 erweiterter Überprüfung Zertifikat**

    EV sind hohe Assurance Zertifikate, deren private Schlüssel in Hardware-Tokens gespeichert werden. Auf diese Weise stärkere Schlüsselverwaltungsdienst-Methoden einzurichten. EV Zertifikate haben die gleiche Nachteile als Smart Karten.     

-   **2.2.6 softwarebasierten Ansätze (NICHT EMPFOHLEN)**

    Verwenden Sie Kryptografie-APIs für Key Management. Dies kann beinhalten einen Schlüssel aus einem Container auf eine verschlüsselte Festplatte speichern und möglich für zusätzliche Sandkästen und Sicherheit verwenden einen virtuellen Computer.

    Diese Lösungen sind nicht so sicher wie die Verwendung einer HSM und machen Sie eine höhere Angriffen verfügbar.

    **2.2.6.1 Makecert (NICHT EMPFOHLEN)**

    MakeCert ist ein Microsoft-Tool und für wichtige Generation wie folgt verwendet werden kann. Um sicherzustellen, dass die Angriffsfläche minimiert wird möglicherweise müssen Sie "Lücke air" dem PC. Der PC-Option, für die der PKpriv besitzt sollte nicht mit dem Netzwerk verbunden werden. Es sollte an einem sicheren Ort und idealerweise Smartcard-Leser, wenn keine echte HSM mindestens verwenden soll.

    ``` syntax
    makecert -pe -ss MY -$ individual -n "CN=your name here" -len 2048 -r
    ```

    Weitere Informationen finden Sie unter [Certificate Creation Tool (Makecert.exe)](http://go.microsoft.com/fwlink/p/?linkid=211849).

    Diese Lösung wird nicht empfohlen.

### <a name="span-id23hsmkeygenerationandstorageforsecurebootkeysspanspan-id23hsmkeygenerationandstorageforsecurebootkeysspanspan-id23hsmkeygenerationandstorageforsecurebootkeysspan23-hsm-key-generation-and-storage-for-secure-boot-keys"></a><span id="2.3_HSM_Key_generation_and_storage_for_Secure_Boot_keys"></span><span id="2.3_hsm_key_generation_and_storage_for_secure_boot_keys"></span><span id="2.3_HSM_KEY_GENERATION_AND_STORAGE_FOR_SECURE_BOOT_KEYS"></span>2.3 HSM Schlüssel generieren und Speicher für Secure Boot-Schlüssel

-   **2.3.1 Speichern von privaten Schlüsseln**

    Den Speicherplatzbedarf für jeden Schlüssel RSA 2048 ist 2048 Bit. Der tatsächliche Speicherort der die Speicherung der Schlüssel, hängt von der Lösung ausgewählt. HSM sind eine gute Möglichkeit zum Speichern von Schlüsseln.

    Der physische Speicherort des PCs werksseitige muss einen geschützten Bereich mit begrenzten Benutzerzugriff wie eine sichere Cage werden.

    Je nach Ihren Anforderungen konnte hierüber auch verschiedene geografische gespeichert oder an einem anderen Speicherort gesichert werden.

    Die rekeying Anforderungen für diese Schlüssel variieren können basierend auf dem Kunden (finden Sie in Anhang A für Federal Bridge Zertifizierungsstelle Erstellen neuer Schlüssel Richtlinien).

    Diese konnte einmal pro Jahr vorgenommen werden. Möglicherweise müssen den Zugriff auf diese Schlüssel für bis zu 30 Jahren (je nach den rekeying Anforderungen usw..).

-   **2.3.2 Abrufen der privaten Schlüssel**

    Die Schlüssel müssen viele aus Gründen der abgerufen werden soll.

    1.  Die PK möglicherweise abgerufenen zum Ausstellen von einer aktualisierten PK aufgrund der Gefährdung oder Behörden einhalten / andere Agency Bestimmungen.

    2.  KEKpri wird zum Aktualisieren der Db und Dbx verwendet werden.

    3.  Sichere Firmwareupdates wichtige – Pri neueren Updates Signieren verwendet werden.

-   **2.3.3 Authentifizierung**

    Gemäß den Anweisungen in FIPS 140-2-Authentifizierung Zugriffsebene basiert.

    **Ebene 2**

    Sicherheitsstufe 2 erforderlich ist, an eine minimale, rollenbasierte Authentifizierung, in der ein kryptografisches Modul die Autorisierung des einen Operator authentifiziert zu nehmen Sie eine bestimmte Rolle, und führen einen entsprechenden Satz von Diensten.

    **Ebene 3**

    Sicherheitsstufe 3 erfordert Identität-basierter Authentifizierungsmechanismen Verbesserung der Sicherheits durch rollenbasierte Authentifizierungsmechanismen für Sicherheit Ebene 2 angegeben. Ein kryptografisches Modul authentifiziert die Identität eines Operators und stellt sicher, dass der identifizierte Operator dazu berechtigt ist, nehmen Sie eine bestimmte Rolle, und führen Sie einen entsprechenden Satz von Diensten.

    PCs wie HSMs Security Level 3, unterstützen die Identität-basierter "k m Authentifizierungstyp" erforderlich sind. Dies bedeutet, dass k Entitäten sind erhält Zugriff auf die HSM an einen Token jedoch zu einem bestimmten Zeitpunkt mindestens k nicht genügend die m-Token für die Authentifizierung zu arbeiten, um Zugriff auf einen privaten Schlüssel aus HSM abrufen vorhanden sein müssen.

    Sie könnten beispielsweise 3 von 5 haben Token HSM Zugriff authentifiziert werden sollen. Diese Mitglieder konnte die Sicherheits-Managern, Transaktion Authorizer und/oder Mitglieder aus der Geschäftsführung werden.

    **HSM Token**

    Sie möglicherweise eine Richtlinie auf dem Hardwaresicherheitsmodul, die eine erfordern das Token vorhanden sein:

    -   Lokal

    -   Remote

    -   So konfiguriert, dass automatisiert werden

    Als ratsam verwenden Sie eine Kombination aus Token und pro token Kennwort.

### <a name="span-id24securebootand3rdpartysigningspanspan-id24securebootand3rdpartysigningspanspan-id24securebootand3rdpartysigningspan24-secure-boot-and-3rd-party-signing"></a><span id="2.4_Secure_Boot_and_3rd_party_signing"></span><span id="2.4_secure_boot_and_3rd_party_signing"></span><span id="2.4_SECURE_BOOT_AND_3RD_PARTY_SIGNING"></span>2.4 secure Boot und 3. Partei signieren

-   **2.4.1 UEFI Treiber signieren**

    UEFI-Treiber muss von einer Zertifizierungsstelle oder Schlüssel in der Db gemäß an anderer Stelle im Dokument signiert sein oder über den Hash der Treiber-Image, die in der Datenbank enthalten. Microsoft wird einen UEFI-Treiber-signierenden Dienst ähnelt der Signierung-Dienst mithilfe der **Microsoft Corporation UEFI Zertifizierungsstelle 2011**WHQL-Treiber bietet. Alle signierten von diesem Treiber werden nahtlos auf eine beliebige PCs ausgeführt, die die Microsoft UEFI Zertifizierungsstelle enthalten. Es ist außerdem möglich, dass ein OEM Signieren vertrauenswürdige Treiber und der OEM-Zertifizierungsstelle in der Datenbank enthalten oder Hashes der Treiber in der Datenbank enthalten. In allen Fällen muss ein UEFI-Treiber (Option ROM) nicht ausgeführt, wenn es in der Datenbank nicht vertrauenswürdig ist.

    Alle Treiber, die in das System Firmware-Image enthalten sind, müssen nicht erneut überprüft werden. Als Teil der gesamten System Image bietet eine ausreichende Garantie, dass der Treiber auf dem PC als vertrauenswürdig ist.

    Microsoft hat sich dies für Personen, die eine UEFI Treiber signieren verfügbar gemacht. Dieses Zertifikat ist Teil der Windows HCK Secure Boot-Tests. Gehen Sie folgendermaßen vor [diesen Blog] ((https://blogs.msdn.microsoft.com/windows_hardware_certification/2013/12/03/microsoft-uefi-ca-signing-policy-updates/) zum Lesen von Informationen zu signierenden UEFI CA-Richtlinie und Updates.

-   **2.4.2 Boot Ladeprogramme**

    Die Microsoft-UEFI Signaturzertifikat Treiber für die Anmeldung andere Betriebssysteme verwendet werden kann. Beispielsweise werden von dieser des Fedora Linux des Startladeprogramms angemeldet.

    Diese Lösung erfordern keine weitere Zertifikate, die Taste Db hinzugefügt werden soll. Nicht nur kostengünstig sondern, können sie für jeder Distribution verwendet werden. Diese Lösung funktioniert für Hardware, das Windows unterstützt, daher es hilfreich für eine Breite Palette von Hardware zuzuordnen ist.

    Die UEFI-Zertifizierungsstelle kann hier heruntergeladen werden: <http://go.microsoft.com/fwlink/p/?LinkID=321194>. Die folgenden Links wurden weitere Informationen zu Windows HCK UEFI signieren und Übermittlung:

    -   [Windows-Entwicklungscenter Hardware-Dashboard](http://go.microsoft.com/fwlink/p/?LinkID=321287)

    -   [Windows-Zertifizierung Dashboard-Verwaltung](http://go.microsoft.com/fwlink/?LinkId=321286)

    -   [UEFI Firmware signieren](http://go.microsoft.com/fwlink/?LinkId=321285)

    -   [Windows-Hardware-Zertifizierung Blog: UEFI signing CA-Update](http://go.microsoft.com/fwlink/p/?linkid=398267)

## <a name="span-idsummaryandresourcesspanspan-idsummaryandresourcesspanspan-idsummaryandresourcesspan3-summary-and-resources"></a><span id="SummaryAndResources"></span><span id="summaryandresources"></span><span id="SUMMARYANDRESOURCES"></span>3. Zusammenfassung und Ressourcen


In diesem Abschnitt möchte, über den vorstehend genannten Abschnitten zusammenfassen und einen Schritt-für-Schritt-Ansatz anzeigen:

1.  **Einrichten einer sicheren Zertifizierungsstellenzertifikats oder Identifizieren eines Partners, um sichere generieren und Schlüssel speichern**

    Wenn Sie eine 3. Partei Lösung nicht verwenden:

    1.  **Installieren Sie und konfigurieren Sie die HSM-Software auf dem Server HSM.** Überprüfen Sie Ihre HSM Referenzhandbuch Anweisungen zur Installation. Der Server werden entweder auf eine eigenständige oder Netzwerk HSM verbunden.

        Info zu HSM Konfiguration finden Sie im Abschnitt 2.2.1, 2.3 und Anhang C.

        Die meisten HSMs bieten FIPS 140-2 Ebene 2 und 3 Compliance. Konfigurieren Sie das HSM für Stufe 2 oder Stufe 3 Compliance. Ebene 3 Compliance strengere Anforderungen, um die Authentifizierung und Schlüssel Zugriff hat und daher sicherer ist. Ebene 3 wird empfohlen.

    2.  **Konfigurieren von HSM für hohe Verfügbarkeit, Sicherung und Authentifizierung.** Überprüfen Sie Ihre HSM Referenzhandbuch.

        Befolgen Sie die HSM Anbieter Richtlinien zum Einrichten von HSM für hohe Verfügbarkeit und Backup.

        Darüber hinaus haben Netzwerk HSMs in der Regel mehrere Netzwerkports Aufteilen des Datenverkehrs; zulassen, dass einen Server mit Netzwerk HSMs auf einem anderen Netzwerk vom regulären Produktionsnetzwerk kommunizieren.

        Einmal Teams, die Mitglieder, die Teil des Security Teams sind identifiziert wurden und Token zugewiesen werden. Sie müssen den Setup HSM Hardware für k-m-Authentifizierung.

    3.  **Secure Boot-Schlüssel und vorab-Zertifikats.** Finden Sie unter Abschnitte 1,3 bis 1,5

        HSM APIs verwenden, um vor dem generieren (generieren im voraus) PK und Firmware Update Schlüssel und Zertifikate.

        Erforderlich - PK (1 pro Modell empfohlen), Aktualisierung der Firmware Schlüssel (empfohlen 1 pro Modell), Microsoft KEK, Db, DbxNOTE: The Microsoft KEK, Db und Dbx müssen nicht vom OEM generiert werden und Vollständigkeit erwähnten sind. Optional - OEM / 3. Partei KEK Db, Dbx und allen anderen Schlüsseln, die in OEM-Db wechseln würden.

2.  **Anwenden eines Windows-Abbilds auf den PC.**

3.  **Installieren Sie Microsoft Db und Dbx**aus. Finden Sie im Abschnitt 1.3.6 und [Anhang B – sichere APIs starten](#securebootapis).

    1.  Installieren Sie die **Microsoft Windows Produktion PCA 2011** in Db.

    2.  Installieren Sie ein leeres Dbx, wenn Microsoft nicht zur Verfügung stellt. Windows wird DBX auf die neuesten DBX über Windows Update auf dem ersten Neustart automatisch aktualisiert.

    **Hinweis**  
    Verwenden von PowerShell-Cmdlets sind Teil der Tests Windows HCK oder BIOS-Anbieter bereitgestellte Methoden verwenden.

     

4.  **Installieren von Microsoft KEK**. Finden Sie im Abschnitt 1.3.3 ein.

    Installieren von Microsoft KEK in die Datenbank UEFI KEK

    **Vorsicht**  
    Verwenden von PowerShell-Cmdlets die sind Teil der Windows-HCK Tests oder BIOS-Anbieter bereitgestellte Methoden verwenden.

     

5.  **Optionaler Schritt - OEM / 3. Partei sichere starten Komponenten**. Finden Sie im Abschnitt 1.3.4 und 1.4 aus.

    1.  Identifizieren Sie, ob Sie benötigen einen OEM erstellen / 3. KEK, Db und Dbx von Drittanbietern.

    2.  Signieren OEM / 3rd Party Db und Dbx mit OEM / 3rd Party KEK(generated earlier) HSM-API verwenden.

    3.  Installieren von OEM / 3. KEK, Db und Dbx von Drittanbietern.

6.  **Signieren von Treibern UEFI** – finden Sie unter Abschnitt 2.4.

    Wenn Add-in-Karten oder andere UEFI Treiber/apps/Bootloaders unterstützen, installieren Sie **Microsoft Corporation UEFI Zertifizierungsstelle 2011** UEFI Db.

7.  **Secure Boot Firmware Update Schlüssel** - finden Sie im Abschnitt 1.3.5.

    1.  Nur nicht-Windows RT-PCs: Installieren Sie den öffentlichen Schlüssel für sichere Firmware Update oder dessen Hash um Speicherplatz einzusparen.

    2.  Nur SoC, Sie müssen auf andere Aktionen, z. B., Brennen Schlüssel für sichere Firmware-Update: Public oder seine Hash.

8.  **Sichere Boot aktivieren**. Finden Sie in [Anhang B – sichere APIs starten](#securebootapis).

    1.  Installieren der OEM/ODM PKpub (Zertifikat bevorzugter, aber Schlüssel ist kein Problem) in die UEFI PS.

    2.  Registrieren Sie die PK Secure Boot-API verwenden. Der PC-Option sollte nun für Secure Boot aktiviert sein.

    **Hinweis**  
    Wenn Sie die PK an das Ende der KEK MS-Db installieren, Dbx signiert sein müssen nicht – keine SignerInfo muss vorhanden sein. Dies ist eine Verknüpfung.

     

9.  **Secure Boot testen**: alle proprietäre und Windows HCK Tests gemäß den Anweisungen in Anweisungen ausführen. Finden Sie in [Anhang B – sichere APIs starten](#securebootapis).

10. **Liefern Plattform**: die PKpriv wird wahrscheinlich niemals wieder verwendet werden, schützen Sie es.

11. **Servicing**: Firmwareupdates Zukunft sicher mit dem "privaten" Secure Firmware Update-Schlüssel mithilfe des signierenden Diensts angemeldet sind.

### <a name="span-id31resourcesspanspan-id31resourcesspanspan-id31resourcesspan31-resources"></a><span id="3.1_Resources"></span><span id="3.1_resources"></span><span id="3.1_RESOURCES"></span>3.1 Ressourcen

Sicherheit Strategien Whitepaper - <http://go.microsoft.com/fwlink/p/?linkid=321288>

Windows HCK Übermittlung -<http://go.microsoft.com/fwlink/p/?linkid=321287>

## <a name="span-idsecurebootpkichecklistspanspan-idsecurebootpkichecklistspanspan-idsecurebootpkichecklistspanappendix-a-secure-boot-pki-checklist-for-manufacturing"></a><span id="SecureBootPKIChecklist"></span><span id="securebootpkichecklist"></span><span id="SECUREBOOTPKICHECKLIST"></span>Anhang A – sichere Boot PKI Prüfliste für die Fertigung


Im folgenden ist eine allgemeine Checkliste für die Aktivierung Secure Boot auf nicht - Windows RT-PCs erforderlichen Schritte zusammenfassen.

**Einrichten von Secure Boot**

1.  Definieren der Sicherheitsstrategie für die (identifizieren Risiken, proaktive und reaktive Strategie definieren) gemäß den Anweisungen in das Whitepaper im Abschnitt 4.

2.  Identifizieren Sie Security Team gemäß den Anweisungen in das Whitepaper im Abschnitt 4.

3.  Einrichten einer sicheren Zertifizierungsstellenzertifikats oder Identifizieren eines Partners (empfohlene Lösung), um sichere generieren und Schlüssel speichern.

4.  Identifizieren Sie Richtlinien für wie häufig Sie Schlüssel Erstellen neuer Schlüssel werden soll. Dies kann von abhängen, wenn Sie besonderen Kunden wie Behörden oder anderen Behörden benötigen.

5.  Haben Sie einen Alternativplan für den Fall, dass der Schlüssel für die Secure Boot gefährdet ist.

6.  Wie viele PK und andere Tasten identifizieren werden Sie gemäß den Anweisungen in Abschnitt 1.3.3 und 1,5 generiert werden.

    Dies wird auf Kunden, wichtige speicherlösung und Sicherheit von PCs basieren.

    Sie können Schritte 7 und 8 überspringen, wenn Sie über die Verwendung einer 3. Party für Key Management die empfohlene Lösung verwenden.

7.  Beschaffen Sie Server und Hardware für Key Management. – Netzwerk- oder eigenständigen HSM pro Abschnitt 2.2.1. Überlegen Sie, ob Sie eine benötigen oder mehrere HSMs für hohe Verfügbarkeit und Ihre Schlüssel Strategie sichern.

8.  Identifizieren von mindestens 3 und 4 Teammitglieder, die ein Authentifizierungstoken für die Authentifizierung auf HSM verfügen sollen.

9.  Verwenden Sie HSM oder 3. Teilnehmer, um Secure Boot-bezogenen Schlüsseln und Zertifikaten vorab zu generieren. Die Schlüssel hängt von den PC-Typ: SoC, Windows RT oder nicht - Windows-RW Weitere Informationen finden Sie unter Abschnitte 1.3 über 1,5.

10. Füllen Sie die Firmware mit den entsprechenden Schlüsseln.

11. Registrieren Sie den Secure Boot-Plattform, um Secure Boot aktivieren. Weitere Informationen finden Sie in Anhang B.

12. Führen Sie alle proprietäre und HCK Secure Boot Tests gemäß den Anweisungen in Anweisungen. Einzelheiten finden Sie unter Anhang B.

13. Liefern Sie den PC-Option. Die PKpriv wird wahrscheinlich niemals wieder verwendet werden, schützen Sie es.

**– Wartung (Updating Firmware)**

Sie müssen möglicherweise Firmware verschiedenen Gründen wie eine Komponente UEFI aktualisieren oder Beheben von Gefährdung des Schlüssels Secure Boot oder regelmäßigen Erstellen neuer Schlüssel Secure Boot Schlüssel aktualisieren.

Weitere Informationen finden Sie unter 1.3.5 und Abschnitt 1.3.6.

## <a name="span-idsecurebootapisspanspan-idsecurebootapisspanspan-idsecurebootapisspanappendix-b-secure-boot-apis"></a><span id="SecureBootAPIs"></span><span id="securebootapis"></span><span id="SECUREBOOTAPIS"></span>Anhang B – sichere Boot-APIs


1.  **Secure Boot-API**

    Die folgenden APIs sind UEFI/Secure Boot relevant:

    1.  [GetFirmwareEnvironmentVariableEx](http://go.microsoft.com/fwlink/?LinkId=398262): Ruft den Wert der angegebenen Firmware-Umgebungsvariablen ab.

    2.  [SetFirmwareEnvironmentVariableEx](http://go.microsoft.com/fwlink/?LinkId=398263): der Wert der angegebenen Firmware-Umgebungsvariable festgelegt.

    3.  [GetFirmwareType](http://go.microsoft.com/fwlink/?LinkId=398264): Ruft den Typ der Firmware ab.

2.  **Einstellung PK**

    Verwenden Sie das Cmdlet Set-SecureBootUEFI, um Secure Boot zu aktivieren. Nach Ihrem Code die PK festgelegt, wird System Erzwingung von Secure Boot nicht erst beim nächsten Neustart wirksam. Vor dem Neustart konnte Code rufen Sie GetFirmwareEnvironmentVariableEx() oder des PowerShell-Cmdlets: Get-SecureBootUEFI, um den Inhalt der Datenbanken Secure Boot zu bestätigen.

3.  **Überprüfung**

    Msinfo32.exe oder PowerShell-Cmdlets können Sie um Variablen Secure Boot-Status zu überprüfen. Es ist keine WMI-Schnittstelle. Sie könnten auch, dass eine Person Einfügen einer falsch signiert startbaren USB-Stick (z. B. von der Windows HCK Secure Boot Manual Logo Test), und stellen Sie sicher, dass es nicht starten testen.

4.  **Sichere Boot-Powershell-Cmdlets**

    -   **Vergewissern Sie sich SecureBootUEFI**: ist UEFI sicheren Boot "AUF" True oder False?

        SetupMode == 0 & & SecureBoot == 1

    -   **Set-SecureBootUEFI**: Set oder Append authentifiziert SecureBoot UEFI Variablen

    -   **Get-SecureBootUEFI**: Get authentifiziert SecureBoot UEFI Variablenwerte

    -   **Format-SecureBootUEFI**: EFI erstellt\_SIGNATUR\_Listen & EFI\_VARIABLE\_AUTHENTIFIZIERUNG\_2 Serialisierungen

5.  **Windows HCK und sicheren Boot-Anweisungen**

    Die folgenden Schritte gelten für System und nicht-Klasse Treiber PC Tests.

    1.  Secure Boot Schutzebenen zu deaktivieren.

        Geben Sie Ihre BIOS-Konfiguration, und deaktivieren Sie Secure Boot.

    2.  Installieren der Clientsoftware HCK.

    3.  Führen Sie alle Tests Windows HCK, mit Ausnahme der folgenden aus:

        -   BitLocker TPM und Recovery Kennwort tests mit PCR\[7\]

        -   BitLocker TPM und Recovery Kennwort Tests für ARM-PCs mit Secure Boot

        -   Sichere Boot-Logo-Test

        -   Sichere Boot manuelle-Logo-Test

    4.  Geben Sie Ihre BIOS-Konfiguration, aktivieren Sie Secure Boot und Wiederherstellen von Secure Boot auf die Standardkonfiguration.

    5.  Führen Sie die folgenden Tests BitLocker- und Secure Boot aus:

        -   BitLocker TPM und Recovery Kennwort tests mit PCR\[7\]

        -   BitLocker TPM und Recovery Kennwort Tests für ARM-PCs, mit Secure Boot

        -   Secure Boot-Logo-Test (automatisiert)

    6.  Geben Sie die BIOS-Konfiguration, und deaktivieren Sie die Secure Startkonfiguration. Dadurch wird den PC-Option durch Löschen PK und andere Tasten Setup Modus wiederhergestellt.

        **Hinweis**  
        Unterstützung für Clearing ist für PCs X86/X64 erforderlich.

         

    7.  Führen Sie den Test mit sicheren Boot manuelle Logo.

        **Hinweis**  
        Sichere Boot erfordert Windows HCK signiert oder VeriSign Treiber auf nicht - Windows RT-PCs

         

6.  **Windows HCK Secure Boot-Logo-Test (automatisiert)**

    Bei diesem Test werden für die ordnungsgemäße Out-of-Box Secure Startkonfiguration überprüfen. Dazu gehören:

    -   Sichere Boot ist aktiviert.

    -   Die PK ist nicht bekannte Test PS.

    -   KEK enthält die Produktion Microsoft KEK.

    -   DB enthält die Produktion Windows-Zertifizierungsstelle.

    -   Dbx vorhanden.

    -   Viele 1kB Variablen werden erstellt/gelöscht.

    -   Eine 32kB Variable wird erstellt/gelöscht.

7.  **Windows HCK Secure Boot manuellen Tests Ordner layout**

    Das Windows HCK Secure manuell Startbildschirm Test Ordner Layout wird im folgenden beschrieben:

    -   `“\Test”`Ordner enthält die folgenden:

        -   Fertigung und – Wartung Test

        -   Programmgesteuertes aktivieren Secure Boot in Testkonfiguration

        -   Wartung von Tests

        -   Fügen Sie ein Zertifikat an Db, überprüfen Sie die Funktion

        -   Fügen Sie einen Hash an Dbx, überprüfen Sie die Funktion

        -   Fügen Sie ein Zertifikat an Dbx, überprüfen Sie die Funktion

        -   Fügen Sie 600 Hashes an Dbx, vergewissern Sie sich Größe

        -   Programmgesteuertes Ändern der PS

    -   `“\Generate”`Ordner hat Skripts die wie folgt aussehen:

        -   Wie Testzertifikate erstellt wurden

        -   Testzertifikate und private Schlüssel sind enthalten

        -   Wie alle Tests erstellt wurden

        -   Aktivieren der Zertifikate und Hashes in signierte Pakete

        -   Sie können selbst ausführen, ersetzen eigene Zertifikate

    -   `“\certs”`Ordner hat alle Zertifikate, die Sie, um Windows zu starten benötigen:

        **Hinweis**  
        Nicht verwenden Sie die Methode "ManualTests\\generieren\\TestCerts" zum Generieren von Schlüsseln und Zertifikaten. Dies ist Windows HCK nur für Testzwecke gedacht. Schlüsseln, die auf dem Datenträger gespeichert werden, die am wenigsten sicher und nicht empfohlen wird verwendet. Dies ist nicht für die Verwendung in einer produktionsumgebung vorgesehen.

         

    -   `“ManualTests\example\OutOfBox”`Ordner hat, Skripts, die Sie für die Installation des Secure Boot auf Produktion PCs nutzen können.

        Die "ManualTests\\generieren\\Tests\\subcreate\_Outofbox\_example.ps1" veranschaulicht, wie in diesen Beispielen generiert wurden und "Erledigen" Abschnitte haben, wenn ein Partner ihre PK und andere Metadaten ersetzen kann.

8.  **Windows HCK UEFI signieren und Übermittlung**

    Die folgenden Links wurden weitere Informationen:

    -   [Developer Center für die Hardware-Dashboard](http://go.microsoft.com/fwlink/p/?linkid=321287)

    -   [UEFI Firmware signieren](http://go.microsoft.com/fwlink/p/?linkid=321285)

    -   [Windows-Zertifizierung Dashboard-Verwaltung](http://go.microsoft.com/fwlink/p/?linkid=321286)

    -   [Windows-Hardware-Zertifizierung Blog: Microsoft UEFI Zertifizierungsstelle Signieren Aktualisierungen von Gruppenrichtlinien](http://go.microsoft.com/fwlink/?LinkId=398267)

## <a name="span-idfbcacertificatepolicyassurancemappingsspanspan-idfbcacertificatepolicyassurancemappingsspanspan-idfbcacertificatepolicyassurancemappingsspanappendix-c-federal-bridge-certification-authority-certificate-policy-assurance-mappings"></a><span id="FBCACertificatePolicyAssuranceMappings"></span><span id="fbcacertificatepolicyassurancemappings"></span><span id="FBCACERTIFICATEPOLICYASSURANCEMAPPINGS"></span>Anhang C – Federal Bridge Zertifizierung Autorität Zertifikat Richtlinie Assurance Zuordnungen


1.  **Rudimentäre**

    Dieser Ebene enthält das niedrigste Maß an Sicherheit, die über die Identität der Person. Eine der wichtigsten Funktionen von dieser Ebene ist um Datenintegrität zu signierende Informationen bereitzustellen. Dieser Ebene ist relevant Umgebungen, in denen das Risiko von Aktivitäten vermutet niedrig betrachtet wird. Es ist nicht geeignet für Transaktionen, die eine Authentifizierung, und im Allgemeinen für Transaktionen mit Vertraulichkeit unzureichend ist, aber möglicherweise verwendet werden für den zweiten Inhaltstyp, in dem Zertifikate mit höherer Assurance nicht verfügbar sind.

2.  **Grundlegende**

    Diese Stufe bietet die grundlegende Assurance für Umgebungen Risiken und Konsequenzen Gefährdung der Daten vorhanden sind, wobei ein sie gelten nicht als Haupt-Vielfache von Bedeutung. Dies kann Zugriff auf private Informationen enthalten, in dem die Wahrscheinlichkeit von böswilligen Access nicht hoch ist. Auf dieser Sicherheitsebene wird vorausgesetzt, dass Benutzer keine wahrscheinlich böswilligen besitzen.

3.  **Mittel**

    Diese Ebene ist relevant für Umgebungen, in denen Risiken und Konsequenzen Gefährdung der Daten Moderater besitzen. Dies kann Transaktionen müssen dabei ist die Wahrscheinlichkeit von böswilligen Access erhebliche erhebliche Währungswert oder Risiko von Betrug oder büroumzüge Zugriff auf private Informationen enthalten.

4.  **Hohe**

    Dieser Ebene eignet sich für die Verwendung, in dem die Bedrohungen für Daten sind hoch oder die Konsequenzen des Fehlers Sicherheitsdienste sind hoch. Dies kann sehr hohen Wert Transaktionen oder hohe Betrug Risiko enthalten.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Secure Boot Erzeugung und Signieren mit HSM (Beispiel)](secure-boot-key-generation-and-signing-using-hsm--example.md)

[UEFI Validierung Option ROM Validierung Anleitungen](uefi-validation-option-rom-validation-guidance.md)

[Secure Boot – Übersicht](secure-boot-overview.md)

 

 






