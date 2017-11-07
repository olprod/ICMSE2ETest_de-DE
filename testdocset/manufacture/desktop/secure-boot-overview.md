---
author: Justinha
Description: Sichere Boot
ms.assetid: 3917c13b-4a23-4d3b-b76a-f22b6f5e5fb1
MSHAttr: PreferredLib:/library/windows/hardware
title: Sichere Boot
ms.openlocfilehash: 529e17c30e710062385acd5db161fcfd1388ee59
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot"></a>Sichere Boot


Sichere Boot ist ein standard Wertpapier entwickelt, die von Mitgliedern der PC-Industrie sicherzustellen, dass Ihre PC gestartet wird, wobei nur Software, die vom PC-Hersteller als vertrauenswürdig ist. Unterstützung für Secure Boot wurde in Windows 8 eingeführt.

Beim Starten des PCs-Option überprüft die Firmware die Signatur der einzelnen Boot-Software, einschließlich Firmwaretreiber (Option ROM), EFI Applications und das Betriebssystem. Wenn eine gute die Signaturen sind, der PC gestartet wird, und die Firmware gibt die Kontrolle an das Betriebssystem.

 

## <a name="span-idfrequentlyaskedquestionsspanspan-idfrequentlyaskedquestionsspanspan-idfrequentlyaskedquestionsspanfrequently-asked-questions"></a><span id="Frequently_asked_questions_"></span><span id="frequently_asked_questions_"></span><span id="FREQUENTLY_ASKED_QUESTIONS_"></span>Häufig gestellte Fragen:


-   **Benötige ich, um das upgrade auf die neueste Version von Windows Secure Boot?**

    Nein. Es gibt keine zusätzliche Hardware oder Firmware Anforderungen von Windows Vista oder Windows 7 auf die neueste Version von Windows aktualisieren.


-   **Was geschieht, wenn neue Hardware von meinem PC Hersteller als vertrauenswürdig eingestuft wird?**

    PC möglicherweise nicht gestartet. Es gibt zwei Arten von Problemen, die auftreten können:

    -   Die Firmware kann nicht das Betriebssystem, Option ROM, Treiber oder app vertrauen, da es die Secure Boot-Datenbank nicht vertrauenswürdig ist.

    -   Einige Hardware erfordert Kernelmodus-Treiber, die signiert werden müssen. Hinweis: viele ältere Treiber von 32-Bit (x 86) werden nicht angemeldet, da im Kernelmodus Treiber signieren letzte Voraussetzung für die Secure Boot ist. Weitere Informationen finden Sie unter [Secure Boot-Funktion, die Anforderungen für den Kernelmodus - Treiber signieren](http://msdn.microsoft.com/library/windows/desktop/hh848062.aspx).

    Weitere Informationen finden Sie unter [Windows 8 mit Secure Boot aktiviert unter Umständen nicht mehr nach der Installation neuen Hardware starten](http://support.microsoft.com/kb/2800988).

-   **Wie kann ich hinzufügen Hardware oder ausführen Software oder Betriebssystemen, die noch nicht vertrauenswürdig meinem PC-Hersteller?**

    -   Die meisten Software und Hardware sollten nahtlos Windows arbeiten, da sie von einem vertrauenswürdigen Microsoft-Zertifikat zur Unterstützung von UEFI Secure Boot signiert sind.

    -   Sie können nach Softwareupdates von Microsoft und/oder PC-Hersteller suchen.

    -   Wenden Sie die vom Hersteller Ihrer um anzufordern, neue Hardware oder Software, die Secure Boot-Datenbank hinzugefügt werden soll.

    -   Für die meisten PCs teilnehmen können Sie Secure Boot über den PC-BIOS deaktivieren. Weitere Informationen finden Sie unter [Secure Boot deaktivieren](disabling-secure-boot.md).

    -   Sie können anpassen, welche Zertifikate von Secure Boot über den PC-BIOS, im Startmenü Secure anpassen als vertrauenswürdig eingestuft werden.

        
-   **Wie bearbeite ich meinen PC Secure Boot Datenbank?**

    Dies kann nur vom PC-Hersteller erfolgen.

## <a name="span-idmanufacturingrequirementsspanspan-idmanufacturingrequirementsspanspan-idmanufacturingrequirementsspanmanufacturing-requirements"></a><span id="Manufacturing_Requirements"></span><span id="manufacturing_requirements"></span><span id="MANUFACTURING_REQUIREMENTS"></span>Fertigung Anforderungen


Sichere Boot erfordert einen PC, die die UEFI Spezifikationen Version 2.3.1 Fehlerverzeichnis C erfüllt oder höher.

Sichere Boot wird für UEFI-Klasse 2 und 3-PCs-Klasse unterstützt. Für UEFI-Klasse 2 PCs wenn Secure Boot aktiviert ist, muss das Modul für Kompatibilität-Unterstützung (CSM) deaktiviert werden, damit der PC-Option nur autorisierten, UEFI-basierte Betriebssysteme gestartet werden kann.

Sichere Boot erfordert kein Modul TPM (Trusted Platform).

Debuggen im Kernelmodus zu aktivieren, aktivieren TESTSIGNING oder n x deaktivieren, müssen Sie Secure Boot deaktivieren. Detaillierte Informationen für OEMs können finden Sie unter [Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung](windows-secure-boot-key-creation-and-management-guidance.md).

## <a name="span-idhowitworksspanspan-idhowitworksspanspan-idhowitworksspanhow-it-works"></a><span id="How_it_works"></span><span id="how_it_works"></span><span id="HOW_IT_WORKS"></span>Funktionsweise


OEM verwendet Anweisungen des Herstellers Firmware Secure Boot Schlüssel erstellen und sie in der Firmware PC zu speichern. Informationen finden Sie unter [Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung,](windows-secure-boot-key-creation-and-management-guidance.md) [Secure Boot Schlüssel generieren und die Signierung mithilfe von Entsprechenden (Beispiel)](secure-boot-key-generation-and-signing-using-hsm--example.md), oder wenden Sie sich an den Hardwarehersteller Ihres.

Beim Hinzufügen von UEFI-Treiber (auch bekannt als Option ROM) müssen Sie auch um sicherzustellen, dass diese angemeldet sind, und in der Datenbank Secure Boot enthalten. Info finden Sie unter [UEFI Validierung Option ROM Validierung Anweisungen](uefi-validation-option-rom-validation-guidance.md).

Wenn Secure Boot auf einem PC aktiviert wird, überprüft der PC jede Softwarekomponente, einschließlich der Option ROM und das Betriebssystem, gegen Datenbanken funktionierenden Signaturen in der Firmware verwaltet. Wenn jede Softwarekomponente gültig ist, führt die Firmware die Software und das Betriebssystem.

### <a name="span-idsignaturedatabasesandkeysspanspan-idsignaturedatabasesandkeysspanspan-idsignaturedatabasesandkeysspansignature-databases-and-keys"></a><span id="Signature_Databases_and_Keys"></span><span id="signature_databases_and_keys"></span><span id="SIGNATURE_DATABASES_AND_KEYS"></span>Signatur Datenbanken und Schlüssel

Vor der PC bereitgestellt wird, werden der OEM die Secure Boot-Datenbanken auf dem PC gespeichert. Dazu gehören die *Signaturdatenbank* (Db), *widerrufen Signaturen-Datenbank* (Dbx) und *Schlüssel der Registrierung-Datenbank* (KEK) auf dem PC. Diese Datenbanken werden auf der Firmware nicht veränderlichen RAM (NV-RAM) unter manufacturing Zeit gespeichert.

Die *Signaturdatenbank* (Db) und die *Signaturen Datenbank gesperrt* (Dbx) Signaturgeber auflisten oder Bild Hashes UEFI Applications, operating System Ladeprogramme (beispielsweise Microsoft Operating Systemladeprogramm oder Start-Manager) und UEFI Treibern, die geladen werden können, klicken Sie auf den einzelnen PCs und die gesperrten Bilder für Artikel, die nicht mehr vertrauenswürdig und nicht geladen werden.

Die *Schlüssel der Registrierung-Datenbank* (KEK) ist eine separate Datenbank der Signaturschlüssel, die zum Aktualisieren der Signaturdatenbank und die gesperrten Signaturen-Datenbank verwendet werden können. Sie müssen einen angegebenen Schlüssel in der Datenbank KEK einbezogen werden, damit künftig Microsoft neue Betriebssysteme, um die Signaturdatenbank hinzuzufügen oder der Datenbank widerrufenen Signaturen bekannte fehlerhafte Bilder hinzufügen kann.

Nachdem diese Datenbanken hinzugefügt wurden und nach dem letzten Firmware Hinweise zur Überprüfung und Testen der OEM sperrt die Firmware bearbeiten können, mit Ausnahme der Updates, die mit dem richtigen Schlüssel signiert sind oder von einem physisch Benutzer Firmware Menüs verwendet und generiert anschließend einen Plattformschlüssel (PK) aktualisiert. Die PK kann zum Signieren von Aktualisierungen an der KEK oder Secure Boot deaktivieren verwendet werden.

OEMs sollten ihre Firmware Tools und Unterstützung bei der Erstellung diese Datenbanken Hersteller. Weitere Informationen finden Sie unter [Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung](windows-secure-boot-key-creation-and-management-guidance.md).

### <a name="span-idbootsequencespanspan-idbootsequencespanspan-idbootsequencespanboot-sequence"></a><span id="Boot_Sequence"></span><span id="boot_sequence"></span><span id="BOOT_SEQUENCE"></span>Startsequenz

1.  Nachdem der PC-Option aktiviert ist, werden die Signatur Datenbanken jeweils mit Schlüssels Plattform verglichen.

2.  Wenn Sie die Firmware nicht vertrauenswürdig ist, muss UEFI-Firmware OEM-spezifische Wiederherstellung der vertrauenswürdigen Firmware initiiert werden.

3.  Liegt ein Problem mit Windows-Start-Manager, versucht die Firmware, eine Sicherungskopie des Windows-Start-Manager starten. Wenn dies auch fehlschlägt, muss die Firmware OEM-spezifische Remediation initiieren.

4.  Nachdem Windows Boot Manager ausgeführt wird, gestartet wurde, liegt ein Problem mit der Treiber oder NTOS Kernel, wird Windows Recovery Environment (Windows RE), damit diese Treiber oder das Kernelabbild wiederhergestellt werden kann geladen.

5.  Windows lädt Antischadsoftware.

6.  Windows lädt andere Kernel-Treiber und initialisiert die Prozesse im Benutzermodus.

Weitere Informationen finden Sie im Whitepaper: [Boot gesichert und gemessen starten: verstärken der Sicherheit frühe Boot Komponenten gegen Malware](http://go.microsoft.com/fwlink/?LinkId=278911).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Sichere Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung](secure-boot-isnt-configured-correctly-troubleshooting.md)

[Sichere Boot ist nicht ordnungsgemäß konfiguriert: ermitteln, ob der PC-Option in einem Modus Manufacturing (Info für Hersteller) ist](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md)

[Gesicherte Start- und gemessene Boot: verstärken der Sicherheit Komponenten für den frühen Boot gegen Schadsoftware](http://go.microsoft.com/fwlink/?LinkId=278911)

[UEFI-Firmware](uefi-firmware.md)

 

 






