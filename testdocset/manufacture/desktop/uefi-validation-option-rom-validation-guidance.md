---
author: Justinha
Description: UEFI Validierung Option ROM Anleitungen
ms.assetid: 357f9a94-98dc-4f78-9f4c-25935912edd6
MSHAttr: PreferredLib:/library/windows/hardware
title: UEFI Validierung Option ROM Anleitungen
ms.openlocfilehash: f456d28c7a300233b7aef4f8308e95e3c039e557
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-validation-option-rom-guidance"></a>UEFI Validierung Option ROM Anleitungen


Vishal Maman, Architekt, OEM Consulting,<vmanan@microsoft.com>

Jeremiah Cox, leitender SDET, Windows-Sicherheit & Identität Team,[jerecox@microsoft.com](mailto:%20jerecox@microsoft.com)

Tony verknüpfen, Dienst Engineer, TW WIN Plan Ökosystems Engineering,[tolin@microsoft.com](mailto:%20tolin@microsoft.com)

Version 1.3

Dieses Dokument unterstützt OEMs und ODMs überprüfen Sie, ob ihre Firmware die Signaturen die Option ROM als Teil der Secure Boot Vertrauenskette überprüft.

In diesem Handbuch wird davon ausgegangen, dass Sie die Grundlagen der UEFI, grundlegende Kenntnisse über Secure Boot (Kapitel 1, 2, 13, 20 und 27 der UEFI-Spezifikation) und PKI-Sicherheitsmodell kennen.

Auf dieser Seite:

-   [Einführung in die](#introduction)

-   [1. UEFI und Option ROM](#uefiandoptionroms)

-   [2. Problem-Anweisung](#problemstatement)

-   [3. betroffen?](#whoisaffected)

-   [4. wie überprüfen?](#howtotestforit)

-   [5. wie Sie diesen beheben](#howtofixit)

-   [6. Ressourcen](#resources)

-   [Anhang A: alternative Vorgehensweise zum Testen, nicht signierte Option ROM Treiber](#alternateapproachtotestingusingunsignedoptionromdrivers)

-   [Anhang B: Skripts zum Aktivieren der Secure Boot NULL DB](#scriptsforenablingsecurebootwithnulldb)

## <a name="span-idintroductionspanspan-idintroductionspanspan-idintroductionspanintroduction"></a><span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>Einführung in die


Option ROM (oder OpROMs) sind Firmware vom PC BIOS während der Initialisierung Plattform ausführen. Sie sind in der Regel auf einer-Plug-In-Karte gespeichert, obwohl sie auf der Hauptplatine befinden können.

Geräte, die normalerweise Option ROM benötigen sind Grafikkarten, Netzwerkadapter und Treiber für RAID-Module. Diese Option ROM bieten Firmwaretreiber normalerweise auch mit dem PC.

Dazu gehören verschiedene Typen von Firmware Treibern, einschließlich legacy PC-AT, Open Firmware und EFI Option ROM. Firmwaretreiber zählen Video-BIOS Grafikkarten, PXE-Treiber für Ethernet-Adapter und Treiber auf RAID-Controllern. Diese Geräte verfügen normalerweise über einige Option, die Firmwaretreiber bereitstellen.

Die Unified Extensible Firmware Interface (UEFI) bietet Unterstützung für Legacy-Modusoption ROM.

Gemäß den Anweisungen in neuesten UEFI-Spezifikation (zurzeit 2.3.1 Fehlerverzeichnis C – Abschnitt 2.5.1.2) ISA (Legacy) Option ROM sind nicht Teil der UEFI-Spezifikation. Im Rahmen dieser Diskussion werden nur die Option ROM UEFI-kompatible PCI-basierte berücksichtigt.

Es ist nicht möglich, Firmware des Geräts in der Firmware PC einbetten können Option ROM verwendet werden. Wenn die Option ROM des Treibers wird ausgeführt, kann unabhängigen Hardwarehersteller Nutzung dieser Treiber und lassen Sie die Treiber und das Gerät an einem Ort.

In diesem Dokument erläutert, warum Sie überprüfen, ob die Option ROM müssen und zeigt es einige Techniken.

### <a name="span-idsupportingbothuefibiosandlegacybiosspanspan-idsupportingbothuefibiosandlegacybiosspanspan-idsupportingbothuefibiosandlegacybiosspansupporting-both-uefi-bios-and-legacy-bios"></a><span id="Supporting_both_UEFI_BIOS_and_Legacy_BIOS"></span><span id="supporting_both_uefi_bios_and_legacy_bios"></span><span id="SUPPORTING_BOTH_UEFI_BIOS_AND_LEGACY_BIOS"></span>Unterstützung für UEFI BIOS und Legacy-BIOS

Viele Hersteller erstellen Geräte, die Option ROM und Firmware für eine Vielzahl von PCs enthalten. Allgemeine Kombinationen zählen:

-   Legacy-ROM

-   Systemeigene OpROM UEFI

-   Legacy-ROM + UEFI EBC OpROM

-   Legacy-ROM + UEFI X64 OpROM

-   Legacy-ROM UEFI X64 + UEFI 32

-   Legacy-ROM + UEFI X64 + UEFI EBC OpROM UEFI 32

UEFI BIOS können laden und ältere Firmwaretreiber ausführen, wenn eine Kompatibilität Support-Modul (CSM) aktiviert ist. Beachten Sie, dass wenn Secure Boot aktiviert ist, Ausführung der Kompatibilität unterstützen Modul und legacy-ROM unzulässig wird, weil ältere Firmwaretreiber Authentifizierung nicht unterstützen. Wenn das Option ROM Format an, in die BIOS-Konfiguration auf legacy ROM festgelegt ist, wird die Vorversion ROM immer auf dem Gerät verwendet.

Wenn das Option ROM Format auf **UEFI kompatibel**festgelegt ist, wird verwendet neuere EFI-ROM, sofern vorhanden ist und der Vorversion ROM ist eine nicht.

UEFI-Treiber sind für viele der neuen Firmware Sicherheit auf Elementebene Features sowie um UEFI Boot Sequences aktivieren erforderlich. Beispielsweise ist Installieren von Windows von einer optischen Platte das an eine kompatible Speichercontroller nicht UEFI angefügt ist nicht möglich, wenn ein System im UEFI-Modus gestartet wird, wenn Secure Boot aktiviert ist.

## <a name="span-iduefiandoptionromsspanspan-iduefiandoptionromsspanspan-iduefiandoptionromsspan1-uefi-and-option-roms"></a><span id="UEFIandOptionROMs"></span><span id="uefiandoptionroms"></span><span id="UEFIANDOPTIONROMS"></span>1. UEFI und Option ROM


![Diagramm der Uefi-Treiber zu berücksichtigen sind](images/dep-8-secureboot-uefidriversecurityconsideration.png)

*Abbildung 2: UEFI-Treiber Sicherheit Erwägung Source: UEFI 2.3.1 Fehlerverzeichnis C*

**Aktivieren Sie im Abschnitt 31.1.4 aus der UEFI 2.3.1 Fehlerverzeichnis C:**

Da im Benutzerprofil UEFI wird eine Reihe von Sicherheits-Berechtigungen erläutert, ist es wichtig, dass die Benutzer Identity Manager und Anmeldeinformationsanbieter Benutzer und der Umgebung, in der sie ausgeführt, vertrauenswürdig sind.

Dazu gehören:

-   Schützen der Bereich für die Speicherung, wo diese Treiber gespeichert werden.

-   Schützen der bedeutet, dass mit dem diese Treiber ausgewählt sind.

-   Schützen der Umgebung die Ausführung dieser Treiber nicht überprüfte Treiber.

-   Durch diese Treiber verwendeten Datenstrukturen sollte nicht durch nicht autorisierte Treiber beschädigt werden, während sie weiterhin verwendet werden.

Komponenten wie Benutzer Identity Manager, die Benutzeranmeldeinformationen-Treiber und Treiber vielleicht befindet sich an einem sicheren Ort wie schreibgeschützt Flashlaufwerk, von der Plattform Richtlinie als vertrauenswürdig ist.

Einige andere Treiber können auf eine ungeschützte Speicher befinden, Speicherorte wie Option ROM oder einer Festplattenpartition und können auf einfache Weise ersetzt werden. Diese Treiber müssen überprüft werden.

Beispielsweise die Standard-Plattform Richtlinie erfolgreich muss feststellen, ob der Treiber aufgeführt, die in der Treiber\# \# \# \# Optionen laden, da andernfalls der Benutzer muss vor dem verarbeiten diese Treiber identifiziert werden. Andernfalls sollte die Treiber Ausführung verzögert werden. Wenn das Benutzerprofil durch ein nachfolgender Aufruf an (identifizieren) oder über dynamische Authentifizierung den Treiber geändert wird\# \# \# \# Optionen möglicherweise nicht erneut verarbeitet werden.

Die Benutzerprofil-Datenbank wird geschlossen, verwenden verschiedene UEFI Signal Ereignisse basierend auf gibt an, ob er geschützt werden kann.

UEFI Treiber & UEFI Option ROM werden nur für Geräte in der Startpfad ausgeführt werden.

PCI-Spec kann mehrere Option ROM-Bilder auf demselben Gerät. Diese Option ROM konnte Legacy X86 & UEFI sein. UEFI-Firmware legt Plattform die Richtlinien für die Option ROM Entnahme Die können den optionalen Adapter ROM ausführen als eigenes Steuerelement Gerät machen.

Die Firmware überprüft Signaturen BDS und DXE Phasen. Die Abfolge der Ereignisse lautet wie folgt:

1.  PCI und abgeleiteter Bus initialisieren

2.  PCI-Geräte für die Option ROM Prüfpunkt

3.  Gefundenen Option ROM im Arbeitsspeicher zugeordnet sind

4.  DXE Phase lädt alle UEFI-Treiber in ROM

UEFI Option ROM kann eine beliebige Stelle im Arbeitsspeicher sein. Die Standardmethode ist auf die ROM auf der Karte das Gerät verwalten zu lassen. UEFI ermöglicht Plattform für die Steuerelement-Richtlinie um steuert, welche Option ROM welchem Gerät mit EFI\_PLATTFORM\_TREIBER\_außer Kraft SETZEN. UEFI unterstützt die Option ROM zum Registrieren einer Konfigurationsschnittstelle.

Auf einem PC mit Secure Boot aktiviert darstellen Option ROM-Treiber ein Sicherheitsrisiko darstellen, wenn sie nicht signiert oder nicht überprüft werden. Die Überprüfung der Signatur für die Option ROM ist eine WHCK-Anforderung. Dies gilt während gerade Option ROM aus, um sicherzustellen, dass das Update vor der Installation überprüft wird.

Aus der Spezifikation UEFI 2.3.1 Eratta C:

9. Zwingend erforderlich ist. **Überprüfung der Firmware Code Integrität signiert**. Firmware, die vom OEM installiert ist und ist schreibgeschützt oder durch die Aktualisierung einer sicheren Firmware zu, wie oben, definiert erwogen werden geschützt. **Systeme müssen überprüfen, ob alle ungeschützte Firmware Komponenten, UEFI Treiber und UEFI Applications signierten SHA-256 mit minimalen RSA-2048 sind (MD5 und SHA-1 sind unzulässig)**, und sicherstellen, dass UEFI-Anwendungen und Treiber, gemäß den Anweisungen in diesen Anforderungen nicht signiert sind, ein Fehler auftritt, ausführen (Dies ist die Standardrichtlinie für zulässige Signaturalgorithmen). Wenn eine Signatur Bilder sich nicht in der autorisierten Datenbank befindet oder in der unzulässige Datenbank gefunden wird, das Bild muss nicht gestartet werden, und stattdessen Informationen in das Bild Ausführung Informationen Table.11 platziert werden muss. Zwingend erforderlich ist. **Überprüfen Sie Signatur aller Boot Apps und Boot Ladeprogramme.** Beim Einschalten die Plattform Boot Firmware Ausführung beginnt und öffentlichem Schlüssel gemäß der Richtlinie Algorithmus zum Überprüfen der Signaturen aller Bilder in den Boot Sequenz bis zur und einschließlich des Start-Managers von Windows verwenden.

## <a name="span-idproblemstatementspanspan-idproblemstatementspanspan-idproblemstatementspan2-problem-statement"></a><span id="ProblemStatement"></span><span id="problemstatement"></span><span id="PROBLEMSTATEMENT"></span>2. Problem-Anweisung


Einige builds von UEFI BIOS Secure Boot aktiviert, einschließlich Brehm Core, nicht standardmäßig authentifizieren UEFI Option ROM, da signierte UEFI Option ROM während der Entwicklung Secure Boot nicht verfügbar waren. Dies macht eine Angriff Fläche/Sicherheitslücke in UEFI Secure Boot verfügbar.

### <a name="span-id21vulnerabilityspanspan-id21vulnerabilityspanspan-id21vulnerabilityspan21-vulnerability"></a><span id="2.1._Vulnerability"></span><span id="2.1._vulnerability"></span><span id="2.1._VULNERABILITY"></span>2.1. Sicherheitsrisiko

Dieses Sicherheitsrisiko wurde noch EDK II und UDK2010 ab August 2013 vorhanden. Die Quelle Maintainers bekannt des Problems und ein Fehler. Alle Firmware abgeleiteten EDK II und UDK2010 sollten überprüfen, wie die Option ROM Überprüfung verwaltet wird. Option ROM Überprüfung Verhalten wird durch einen Wert PCD gesteuert `PcdOptionRomImageVerificationPolicy` im EDK II SecurityPkg-Paket.

Der Quellcode für die Sicherheitslücke TianoCore ist SecurityPkg\\SecurityPkg.dec Datei:

``` syntax
## Pcd for OptionRom.
  #  Image verification policy settings:
  #  ALWAYS_EXECUTE                         0x00000000
  #  NEVER_EXECUTE                          0x00000001
  #  ALLOW_EXECUTE_ON_SECURITY_VIOLATION    0x00000002
  #  DEFER_EXECUTE_ON_SECURITY_VIOLATION    0x00000003
  #  DENY_EXECUTE_ON_SECURITY_VIOLATION     0x00000004
  #  QUERY_USER_ON_SECURITY_VIOLATION       0x00000005
gEfiSecurityPkgTokenSpaceGuid.PcdOptionRomImageVerificationPolicy|0x00|UINT32|0x00000001
```

Der Standardwert (0 x 00) ist IMMER\_EXECUTE, die nicht ordnungsgemäß Überprüfung von signierten Treibern in Option ROM für add-ins Peripheriegeräte durchgeführt wird. Dies ist kein idealer Wert für jedes System UEFI Secure Boot-Funktionalität implementieren.

Empfohlene Wert (am besten Security):`DENY_EXECUTE_ON_SECURITY_VIOLATION (0x04)`

Empfohlene Wert (am besten Flexibilität):`QUERY_USER_ON_SECURITY_VIOLATION (0x05)`

In EDK II & UDK2010 wird ordnungsgemäße Codierungsverfahren einen Mechanismus außer Kraft setzen, um PCD-Werte für die Plattform Firmware zu ändern. Aus diesem Grund wird der Wert für `PcdOptionRomImageVerificationPolicy` sollte nicht geändert werden, `SecurityPkg\SecurityPkg.dec`. Der Überschreibungswert sollte in die Plattform DSC Datei festgelegt werden. Ein Beispiel unter Verwendung von Nt32Pkg\\Nt32Pkg.dsc:

``` syntax
[PcdsFixedAtBuild]
gEfiSecurityPkgTokenSpaceGuid.PcdOptionRomImageVerificationPolicy|0x04
```

Die PCD Überschreibung platziert werden soll, klicken Sie unter der `[PcdsFixedAtBuild]` -Abschnitt der Datei DSC. Der genaue Mechanismus zum Überschreiben der Parameter kann je nach BIOS-Hersteller Tools unterscheiden.

**Hinweis**  
Dieses Sicherheitsrisiko kann in frühen Implementierungen von UEFI Secure Boot BIOS von unabhängigen BIOS-Anbietern vorhanden sein. Wenden Sie sich an den Hersteller Ihres BIOS, um festzustellen, ob Ihre Version beeinträchtigt werden kann.

 

## <a name="span-idwhoisaffectedspanspan-idwhoisaffectedspanspan-idwhoisaffectedspan3-who-is-affected"></a><span id="WhoIsAffected"></span><span id="whoisaffected"></span><span id="WHOISAFFECTED"></span>3. betroffen?


PC UEFI Secure Boot implementiert und verfügt über einen UEFI-Option ROM-Treiber, die nicht signiert ist. Darüber hinaus möglicherweise die Firmware für Kompatibilität zum Abrufen der vorhandenen Karten arbeiten ein Sicherheitsrisiko die Option ROM überprüfen, ob nicht.

**Notebooks, Netbooks, Ultrabooks und Tablets: die meisten sind nicht betroffen**. Option ROM sind normalerweise auf Rückwandplatine Bus wie PCI/e, ISA und deren Ableitung (ExpressCard Mini, CardBus, PC, LPC, ThunderBolt usw.). Wenn ein Laptop keiner dieser verfügbar gemachte verfügt, wird die Angriffsfläche erheblich verringert. Darüber hinaus ist es wahrscheinlich UEFI-Treiber für integrierte Laptop, die auf einem separaten Option ROM nicht gefunden Kern BIOS-Firmware Volume Komponenten integriert sind Daher sind die meisten Laptops nicht gefährdet. Wenn Legacy-Option ROM werden deaktiviert, sieht sie außerdem wie UEFI nur PCI-basierte Option ROM unterstützt.

Wenn Sie haben ein Desktop, Hauptplatine oder einen Server verfügt über ein BIOS UEFI und Secure Boot implementieren, können jedoch Sie beeinträchtigt. Auf eines Servers dedizierten RAID-Controller oder -add-ins Speichercontroller für SATA-, FC usw. oder PCIe Ethernet-Netzwerk möglicherweise Karten Option ROM. Add-in-Controller unterstützt eine Vielzahl von Funktionen auf Servern sind allgemeine dies vor allem für Speicherplatz auf dem Server gilt.

Dies kann 32-Bit- und 64-Bit-PCs Klasse 2 und 3-Klasse beeinträchtigen.

Wenn eine Secure Boot-Plattform unterstützt die Option ROM von Geräten, die nicht dauerhaft, die Plattform zugeordnet ist, die Möglichkeit unterstützt, diese Option ROM authentifizieren, und es muss in Netzwerkprotokolle beschriebenen Methoden für die Validierung der Option ROM unterstützen – UDP und MTFTP und die authentifizierten EFI Variablen in UEFI-Spezifikation 2.3.1 beschriebenen Fehlerverzeichnis C Abschnitt 7.2.

## <a name="span-idhowtotestforitspanspan-idhowtotestforitspanspan-idhowtotestforitspan4-how-to-test-for-it"></a><span id="HowToTestForIt"></span><span id="howtotestforit"></span><span id="HOWTOTESTFORIT"></span>4. wie überprüfen?


Wenn Sie die Firmware entwickeln und es auf Brehm Core basiert überprüfen Sie im Abschnitt 2.1 erwähnten Sicherheitsrisiko. Wenn Sie eine andere IBV Firmware Bitte Kontrollkästchen mit diesen verwenden. Oder Sie den Test ausführen konnte es selbst, wie weiter unten erläutert.

Sie benötigen Folgendes:

-   PC mit UEFI-Firmware getesteten

-   PCI-Gerät mit der Option ROM auf dem PC unter Test (wie eine Grafikkarte)

-   Stellen Sie sicher, dass Secure Boot aktiviert ist

Schritte zum Testen:

1.  Einfügen einer UEFI PCI-Karte mit UEFI Option ROM auf den PC getesteten hinzufügen.

    Bei Verwendung eine PCI-Grafikkarte zu Testzwecken Einbindung eine externen überwachen.

2.  Aktivieren Sie Secure Boot mit den folgenden Einstellungen:

    -   PK: Ihre PK oder eines selbstsignierten Test PK

    -   KEK: KEK oder einer anderen KEK MS KEK, Fabrikam PK signierte testen

    -   DB: NULL. (Dieser muss NULL sein.)

    -   DBX: NULL.

    -   SecureBoot: Die UEFI-Variable festgelegt werden sollte auf "true"

3.  Starten Sie den PC neu

4.  Erwarten Sie das folgende Ergebnis:

    -   Wenn UEFI-Firmware ordnungsgemäß implementiert wird, nicht der UEFI Option-ROM-Treiber geladen, seit das Vorhandensein einer Option ROM Zuständigkeit für die Firmware die "Db" prüfen, ob ein Zertifikat. Da der "Db" NULL der UEFI-Treiber kann nicht geladen werden ist. Beispielsweise, wenn Sie zum Testen die Videokarte verwenden, sehen Sie, dass nichts auf anzeigen angezeigt.

    -   Wenn die Firmware richtig implementiert nicht zur Verfügung, lädt UEFI Treiber von der Option ROM seit die Firmware nicht von Signaturen in der "Datenbank überprüfen". Beispielsweise bei Verwendung die Videokarte für Test sehen Sie, dass der Monitor mit der Option-ROM-Karte verknüpft angezeigt werden soll wird.

**Hinweis**  
Es ist unerheblich, ob der UEFI Option ROM Treiber oder nicht angemeldet ist, die Option ROM wird nicht geladen werden, wenn DB null ist und SB aktiviert ist (PK und KEK werden registriert).

 

Näheres Beispielskripts, die in der WHCK zum Generieren der PK und KEK verfügbar. Sie können die Skripts hier herunterladen: <http://go.microsoft.com/fwlink/?LinkId=321292> . Anhang B verfügt über Beispielskripts und weitere Details.

Sie können auch Anhang A für eine andere Möglichkeit zum Ausführen des oben genannten Tests verweisen. Dieser Ansatz ist es nicht erforderlich, das Festlegen der DB auf Null, aber einen nicht signierten UEFI Option-ROM--Treiber von unabhängigen Hardwarehersteller benötigt.

## <a name="span-idhowtofixitspanspan-idhowtofixitspanspan-idhowtofixitspan5-how-to-fix-it"></a><span id="HowToFixIt"></span><span id="howtofixit"></span><span id="HOWTOFIXIT"></span>5. wie Sie diesen beheben


Wenn die Prüfung fehlschlägt, arbeiten Sie mit Ihrem IBV erwerben der erforderlichen Versionen und konfigurieren, um die Option ROM überprüfen. Stellen Sie sicher, dass die Firmware der Test bestanden wird. Für PCs das ausgeliefert haben müssen Sie eine sichere Firmware-Aktualisierung führen. Verweisen auf [NIST Publikation 800 147](http://go.microsoft.com/fwlink/p/?linkid=321186) , und/oder finden Sie unter [Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung](windows-secure-boot-key-creation-and-management-guidance.md).

Sie können den PC testen und nutzen Windows HCK als Testtool (nicht um ein Tool Zertifizierung) für die sichere Firmwareupdates testen.

### <a name="span-id51signingthedriverspanspan-id51signingthedriverspanspan-id51signingthedriverspan51-signing-the-driver"></a><span id="5.1._Signing_the_driver"></span><span id="5.1._signing_the_driver"></span><span id="5.1._SIGNING_THE_DRIVER"></span>5.1. Signieren des Treibers

In Fällen, die Sie gefunden, die Sie möglicherweise auf UEFI Option einige Punkte unter zum beheben, die nicht signierte Treiber.

Signieren Sie jede Option ROM Treiber einzeln. Unterbricht, die das Format der PCI-Option. Sie müssen nur den Treiber UEFI melden Sie sich vor dem Erstellen der kombinierten Option.

Vor dem Einfügen des UEFI-Treibers in der OpROM, melden Sie sich das Bild UEFI und mit Secure Boot ON & OFF an der Shell UEFI (Laden/Entladen der Treiberdatei) zu testen. Platzieren Sie dann in der kombinierten Option ROM signierten Treiber

Sie können Ihre IHV Microsoft SysDev Center die Option UEFI abrufen, die ROM über einen Dienst verfügbar über SysDev Center angemeldet, verweisen.

### <a name="span-id52validationofupdatespanspan-id52validationofupdatespanspan-id52validationofupdatespan52-validation-of-update"></a><span id="5.2._Validation_of_update"></span><span id="5.2._validation_of_update"></span><span id="5.2._VALIDATION_OF_UPDATE"></span>5.2. Überprüfung des Updates

Führen Sie den Test aus, den, dem Sie zuvor erwähnt, um sicherzustellen, dass die Sicherheitslücke nicht existiert. Verwenden Sie die Tests HCK um sicherzustellen, dass keine funktionalen Regressionen vorhanden sind.

## <a name="span-idresourcesspanspan-idresourcesspanspan-idresourcesspan6-resources"></a><span id="Resources"></span><span id="resources"></span><span id="RESOURCES"></span>6. Ressourcen


-   UEFI Plattform Initialisierung-Spezifikation Volume 5-Standards 1.2.1 Fehlerverzeichnis A: <http://go.microsoft.com/fwlink/p/?linkid=220187>

-   Relevanter Informationen von UEFI 2.3.1-Spezifikation:

    -   2.5.1: Legacy Option ROM Probleme

    -   10: Protokolle – UEFI Driver Model

    -   13.4.2: PCI-Option ROM

    -   20: EFI Byte Code virtuellen Computer

    -   28: Übersicht über die HII

    -   29: HII Protokolle

    -   30: HII Konfiguration Verarbeitung und Browser-Protokoll

-   [UEFI-Forum Lerncenter](http://go.microsoft.com/fwlink/p/?LinkId=321289)

-   [UEFI IHV Ressourcen @ von Intel](http://go.microsoft.com/fwlink/?LinkId=321290)

-   Mithilfe der [TianoCore edk2 entwickl Verteilerliste](http://go.microsoft.com/fwlink/?LinkId=398276) für die Unterstützung von anderen Entwicklern UEFI

-   TechNet: [Best Practices for Enterprise Security: Security Strategien](http://go.microsoft.com/fwlink/p/?linkid=321288)

-   [UEFI-Spezifikation](http://go.microsoft.com/fwlink/p/?LinkID=220187) fehlerverzeichnis C

-   [Vertrauenswürdige Netzwerke Gruppe](http://go.microsoft.com/fwlink/p/?LinkID=78378)

-   [Tianocore UEFI Development Kit](http://go.microsoft.com/fwlink/?LinkId=398277)

-   [UEFI-Firmware](uefi-firmware.md)

-   [Intel Press: Hinter BIOS 2nd Edition](http://go.microsoft.com/fwlink/?LinkId=398278)

-   [Windows 8.1 sicheren Boot wichtige Erstellung und Verwaltung](windows-secure-boot-key-creation-and-management-guidance.md)

-   [Überprüfung der Funktionalität von Windows UEFI Firmware Update-Plattform](http://go.microsoft.com/fwlink/?LinkId=321291)

## <a name="span-idalternateapproachtotestingusingunsignedoptionromdriversspanspan-idalternateapproachtotestingusingunsignedoptionromdriversspanspan-idalternateapproachtotestingusingunsignedoptionromdriversspanappendix-a-alternate-approach-to-testing-using-unsigned-option-rom-drivers"></a><span id="AlternateApproachToTestingUsingUnsignedOptionROMDrivers"></span><span id="alternateapproachtotestingusingunsignedoptionromdrivers"></span><span id="ALTERNATEAPPROACHTOTESTINGUSINGUNSIGNEDOPTIONROMDRIVERS"></span>Anhang A: alternative Vorgehensweise zum Testen, nicht signierte Option ROM Treiber


Dieser Ansatz nutzt Abrufen von Tools aus IHV um sicherzustellen, dass der UEFI Option ROM Treiber signiert ist.

Sie benötigen Folgendes:

-   PC mit UEFI-Firmware getesteten

-   PCI-Gerät mit einem nicht signierte Option-ROM-Treiber, der PC-Option unter Test (wie eine Grafikkarte) zugeordnet ist

-   Stellen Sie sicher, dass Secure Boot aktiviert ist

-   Option IHV Tools zum Erkennen von Signatur auf Option-ROM-Laufwerk offensichtlich nicht, dass der Option ROM Treiber oder nicht signiert ist

Wenn die Firmware ordnungsgemäß implementiert ist, und die Option ROM nicht signiert ist sollte die Karte fehl, die Überprüfung von der Firmware und nicht geladen werden den Treiber auf der Karte. Der PC-Option sollte ein Fehlercode ausgegeben, wie **EFI\_BILD\_AUSFÜHRUNG\_AUTH\_SIG\_FOUND**. Für den Fall, dass Sie eine Grafikkarte verwenden, wird möglicherweise angezeigt, der PC-Option nur einen schwarzen Bildschirm angezeigt wird, da Option ROM geladen werden, nicht.

Wenn Sie die Firmware nicht richtig implementiert wird, funktioniert dieser Test.

## <a name="span-idscriptsforenablingsecurebootwithnulldbspanspan-idscriptsforenablingsecurebootwithnulldbspanspan-idscriptsforenablingsecurebootwithnulldbspanappendix-b-scripts-for-enabling-secure-boot-with-null-db"></a><span id="ScriptsForEnablingSecureBootWithNULLdb"></span><span id="scriptsforenablingsecurebootwithnulldb"></span><span id="SCRIPTSFORENABLINGSECUREBOOTWITHNULLDB"></span>Anhang B: Skripts zum Aktivieren der Secure Boot NULL DB


Sie können mithilfe der aktuelle Satz an Secure Boot Variablen (PK und KEK) oder Test sowie das Festlegen der für diese Tests zu generieren.

Im folgenden werden Schritte zum Generieren der Test PK, KEK und Einstellung Db auf NULL. Stellen Sie sicher, dass Secure Boot nicht aktiviert ist; Andernfalls würde folgendermaßen signierte UEFI Bin Dateien erfordern.

**Hinweis**  
Wir setzen Sie die Secure Boot Variable – Db, KEK und PK in umgekehrter Reihenfolge damit wir nicht die UEFI Bin Dateien signieren.

 

Vor diesem Schritt sollte der PC im Installationsmodus sein.

1.  **Erstellen von KEK und PK Zertifikate**

    Dieser Schritt erfordert das makecert.exe Tool im [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=271979)verfügbar.

    ``` syntax
    MakeCert.exe -cy authority -len 2048 -m 60 -a sha256  -pe -ss my -n "CN=DO NOT SHIP - Fabrikam Test KEK CA" Fabrikam_Test_KEK_CA.cer
    MakeCert.exe -cy authority -len 2048 -m 60 -a sha256  -pe -ss my -n "CN=DO NOT SHIP - Fabrikam Test PK" TestPK.cer
    ```

2.  **Skript zum Generieren der Test PK**

    Sie können verwenden Ihre eigene PK oder die Skripts aus der WHCK für diese <http://go.microsoft.com/fwlink/?LinkId=321292> nutzen

    Ein Beispiel finden Sie weiter unten.

        # this scripts demonstrates how to format the Platform key 
        # NOTE The PK is actually set in the Enable_OEM_SecureBoot.ps1 script 
        Import-Module secureboot
        $d = (pwd).Path

        ###############################################################################
        # Complete the following parameters
        ###############################################################################

        $certname = "TestPK"
        # TODO change this path to where you have the PK.cer file 
        # This is where you plugin the certificate generated by the HSM 
        $certpath = $d + "\" + $certname + ".cer"

        # Each signature has an owner SignatureOwner, which is a GUID identifying the agent which inserted the signature in the database. 
        # Agents might include the operating PC or an OEM-supplied driver or application. 
        # Agents may examine this field to understand whether they should manage the signature or not.
        # TODO replace with OEM SignatureOwner GUID.
        # You can use tools like Guidgen.exe tool in SDK or a similar tool to generate a GUID
        $sigowner = "55555555-5555-5555-5555-555555555555"

        $var = "PK"
        $efi_guid = "{8BE4DF61-93CA-11d2-AA0D-00E098032B8C}"
        $append = $false

        ###############################################################################
        # Everything else is calculated
        ###############################################################################

        # Workaround relative path bug
        # TODO substitute OEM with your OEM name 
        $siglist =  $certname + "_SigList.bin"
        $serialization = $certname + "_SigList_Serialization_for_" + $var + ".bin"
        $signature = $serialization + ".p7"

        $appendstring = "set_" 
        $attribute = "0x27"
        $example = "Example_SetVariable_Data-" + $certname + "_" + $appendstring + $var + ".bin" 

        Format-SecureBootUEFI -Name $var -SignatureOwner $sigowner -ContentFilePath $siglist -FormatWithCert -Certificate $certpath -SignableFilePath $serialization -Time 2011-05-21T13:30:00Z  -AppendWrite:$append

        # OutputFilePath - Specifies the name of the file created that contains the contents of what is set. 
        # If this parameter is specified, then the content are not actually set, just stored into this file.
        # Please note if -OutputFilePath is provided the PK is not set like in this case. The master script sets it at the end.

        # Time - you can change the time below as long as it isn't in the future. Nothing wrong with keeping it as is.
        
        Set-SecureBootUEFI -Name $var -Time 2011-05-21T13:30:00Z -ContentFilePath $siglist  -OutputFilePath $example -AppendWrite:$append
    

3.  **Generieren KEK testen oder verwenden Sie eine eigene OEM-KEK**

    Sie können Ihre eigenen OEM KEK oder Skripts aus der WHCK für dieses nutzen. Sie können auch die Fabrikam\_PK\_SigList.bin von <http://go.microsoft.com/fwlink/?LinkId=321292> anstelle von eigenen Test KEK generieren.

    Ein Beispiel finden Sie weiter unten.

        # script to add option OEM KEK
        Import-Module secureboot
        $d = (pwd).Path

        ###############################################################################
        # Complete the following parameters
        ###############################################################################

        $certname = "Fabrikam_Test_KEK_CA"
        # TODO change this path to where you have the PK.cer file 
        # This is where you plugin the certificate generated by the HSM 
        $certpath = $d + "\" + $certname + ".cer"

        # TODO change this path to where you have the OEM_KEK.cer file 
        # Each signature has an owner SignatureOwner, which is a GUID identifying the agent which inserted the signature in the database. 
        # Agents might include the operating system or an OEM-supplied driver or application. 
        # Agents may examine this field to understand whether they should manage the signature or not.
        # TODO replace with OEM SignatureOwner GUID.
        # You can use tools like Guidgen.exe tool in SDK or a similar tool to generate a GUID
        
        $sigowner = "00000000-0000-0000-0000-000000000000"

        $var = "KEK"
        $efi_guid = "{8BE4DF61-93CA-11d2-AA0D-00E098032B8C}"
        $append = $false

        ###############################################################################
        # Everything else is calculated
        ###############################################################################

        $siglist = $certname + "_SigList.bin"
        $serialization = $certname + "_SigList_Serialization_for_" + $var + ".bin"
        $signature = $serialization + ".p7"
        if ($append -eq $false) 
        { 
            $appendstring = "set_" 
            $attribute = "0x27"
        } else 
        {   
            $appendstring = "append_" 
            $attribute = "0x67"
        }
        $example = "Example_SetVariable_Data-" + $certname + "_" + $appendstring + $var + ".bin" 

        Format-SecureBootUEFI -Name $var -SignatureOwner $sigowner -ContentFilePath $siglist -FormatWithCert -CertificateFilePath $certpath -SignableFilePath $serialization -Time 2011-05-21T13:30:00Z -AppendWrite:$append 

        # -Time You can change the time below as long as it isn't in the future. Nothing wrong with keeping it as is.
        
        Set-SecureBootUEFI -Name $var -Time 2011-05-21T13:30:00Z -ContentFilePath $siglist -OutputFilePath $example -AppendWrite:$append
    

4.  **Db auf Null festgelegt wurde, und legen Sie KEK und PS**

    Mit diesem Skript wird zunächst ist die Db auf Null festgelegt werden.

    **Hinweis**  
    Bitte beachten Sie beibehalten, wenn die Fabrikam Test KEK Zertifizierungsstelle die einzige KEK Zertifizierungsstelle vorhanden ist (das heißt es ist keine Windows-KEK CA), kann der PC-Option in Windows RE starten.
    
        # Prior to script execution, run "Set-ExecutionPolicy Bypass -Force"
        
        Import-Module secureboot
        try 
        {
            Write-Host "Deleting db..."
            Set-SecureBootUEFI -Name db -Time "2011-06-06T13:30:00Z" -Content $null
        }
        catch
        {
        }
        Write-Host "Setting Fabrikam KEK..."
        Set-SecureBootUEFI -Time 2011-05-21T13:30:00Z  -ContentFilePath Fabrikam_Test_KEK_CA_SigList.bin  -Name KEK

        Write-Host "Setting self-signed Test PK..."
        Set-SecureBootUEFI -Time 2011-05-21T13:30:00Z -ContentFilePath TestPK_SigList.bin  -Name PK

        Write-Host "`n... operation complete.  `nSetupMode should now be 0 and SecureBoot should also be 0. Reboot and verify that Windows is correctly authenticated, and that SecureBoot changes to 1."

5.  **Die Option ROM Karte schließen und testen**

    Tests sollten erfolgreich oder Fehler basierend auf Firmware Korrektheit. Beispiel:

    Wenn die Option ROM in der Firmware ordnungsgemäß implementiert ist, und Sie eine Grafikkarte verwenden für das Testen, sollten keine Anzeige auf dem angeschlossenen Monitor vorhanden sein.

    Allerdings bei Verwendung von falschen Firmware sollte die Videokarte auf die Anzeige ausgegeben haben.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wichtige Windows sicheren Boot-Erstellung und Verwaltung](windows-secure-boot-key-creation-and-management-guidance.md)

[Secure Boot – Übersicht](secure-boot-overview.md)

[Überprüfung der Funktionalität von Windows UEFI Firmware Update-Plattform](validating-windows-uefi-firmware-update-platform-functionality.md)

 

 






