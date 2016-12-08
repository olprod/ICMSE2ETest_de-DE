---
author: kpacquer
Description: Aktualisieren von Anforderungen
ms.assetid: 3f2c96f5-cc52-44a2-b61d-279b649995fc
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktualisieren von Anforderungen
ms.openlocfilehash: 2b62f3b9adb69bda3e6707c18b594a490fb014d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-requirements"></a>Aktualisieren von Anforderungen


Dieser Abschnitt enthält die Anforderungen für alle Updates, die auf den Einzelhandel Geräten installiert werden.

## <a name="span-idgeneralupdaterequirementsspanspan-idgeneralupdaterequirementsspanspan-idgeneralupdaterequirementsspangeneral-update-requirements"></a><span id="General_update_requirements"></span><span id="general_update_requirements"></span><span id="GENERAL_UPDATE_REQUIREMENTS"></span>Allgemeine Anforderungen für


Ein OEM-Updatepaket muss die folgenden Anforderungen entsprechen.

-   Vorinstallierte apps müssen mit den Speicher aktualisiert werden.

-   Update Zielgruppenadressierung Informationen in das Bild und die Mobile Operator-ID festgelegt werden muss und Geräte-ID von OEM-Partnern mit jeder updateanforderung übermittelt werden müssen. Weitere Informationen zum Festlegen von Mobile Operator-ID und Geräte-ID beim Erstellen einer updateanforderung finden Sie unter [New-RequestForUpdate Cmdlet](new-requestforupdate-cmdlet.md).

-   Für alle Pakete müssen OEMs erforderlichen Attributwerte festgelegt. Weitere Informationen finden Sie im Abschnitt "Paketattributen" im [primären Elemente und Attribute einer Projektdatei Paket](https://msdn.microsoft.com/library/dn756796).

## <a name="span-idwindowsstandardpackageconfigurationwspccompliancespanspan-idwindowsstandardpackageconfigurationwspccompliancespanspan-idwindowsstandardpackageconfigurationwspccompliancespanwindows-standard-package-configuration-wspc-compliance"></a><span id="Windows_Standard_Package_Configuration__WSPC__compliance"></span><span id="windows_standard_package_configuration__wspc__compliance"></span><span id="WINDOWS_STANDARD_PACKAGE_CONFIGURATION__WSPC__COMPLIANCE"></span>Windows Standard Paket-Konfiguration (WSPC) compliance


Retail Pakete müssen die [Anforderungen für den Einzelhandel Bilder Windows Standard Packen Konfiguration (WSPC)](https://msdn.microsoft.com/library/dn756781)entsprechen.

Wenn Sie Firmwareupdates übermitteln, wird Bild Validierung zweimal ausgeführt:

-   Beim Ausführen von [Cmdlet Initialize-FirmwareSubmission](initialize-firmwaresubmission-cmdlet.md) ohne den Parameter - NonWspcCompliant überprüft der Client Erfassung die Übermittlung. Wenn die Bild-Überprüfung fehlschlägt, schlägt die Übermittlung Bild nicht initialisiert werden.

-   Nachdem Sie die Änderungen zu senden, die Microsoft Update-Systeme Validierung Bild ein zweites Mal zum Signieren von Code vor dem verarbeiten. Wenn die Überprüfung Bild diese Überprüfung fehlschlägt, wird die Übermittlung nicht weiterhin zum Signieren von Code verarbeitet werden.

## <a name="span-idfirmwareversioningrequirementsspanspan-idfirmwareversioningrequirementsspanspan-idfirmwareversioningrequirementsspanfirmware-versioning-requirements"></a><span id="Firmware_versioning_requirements"></span><span id="firmware_versioning_requirements"></span><span id="FIRMWARE_VERSIONING_REQUIREMENTS"></span>Firmware Versioning Anforderungen


**Versioning-Schema**

Erstellen Sie ein Versioning-Schema, das eine vierteilige Versionsnummer enthält.

Pakete werden nur aktualisiert, wenn die neue Paket Zahl größer als die Anzahl der alten Paket wird. Die Paket-Nummern müssen ein hierarchisches Schema von links nach rechts und Netzwerktools verwenden diese Version 2.0.0.0 ist größer als 1.9.9.9 Version.

Wir empfehlen, die Halbleiterhersteller verwenden (PA) Versionsnummer, gefolgt von der OEM-Versionsnummer. Beispiel: *PA-Major.SV-Minor.OEM-Major.OEM-Nebenversion*. Aus Gründen der Konsistenz, erwogen werden Build Umgebungsvariablen, wie etwa das Datum beim Erstellen Ihrer Versioning Schemas.

Erstellen Sie bei jeder Aktualisierung neu eine neue Versionsnummer. Geben Sie die alte und neue Versionsnummer, beim Senden des Updates. Beispiel:

1.  0001.0001.0001.20140801 -&gt; 0001.0040.0055.20140808

2.  0001.0040.0055.20140808 -&gt; 0001.0040.0077.20140815

3.  0001.0040.0077.20140815 -&gt; 0002.0000.0077.20140822

Installationsfehler, diese Anforderung erfüllen führt zu entweder ignorierten Pakete während Update Generation (für die Pakete, wobei die Version nicht erhöht) oder einem vollständigen Fehlschlagen in die Update-Generierung Prozesse.

**So verhindern Sie Versioning-Fehler:**

-   Überblick über die Versionsnummern in einem separaten Arbeitsblatt.

-   Zwei Versionen der gleichen Paket mit der gleichen Anzahl der vorherigen Version nicht senden – jedes Update auf die vorherige Version miteinander verkettet werden muss. Veröffentlichung des geräteaktualisierungsdiensts behält sich das Recht zum Ablehnen von Anfragen für Updates (RFUs), die nicht die Zielversion des vorherigen Updates als die Source-Version des neuen Updates enthalten.

**Versioning – häufig gestellte Fragen**

*Was geschieht, wenn ich meine Versionsnummer und den Inhalt des Meine Paket Änderungen nicht ändern?*

Um die vorhandene Version identisch sein des Pakets berücksichtigt werden und wird nicht heruntergeladen und installiert werden, wenn Benutzer das Gerät aktualisieren

*Verwende ich die gleichen Versionsnummern über alle meine Pakete?*

Einigen Versionen möglicherweise anders, wenn sie genau hinweisen, dass eine frühere Paketversion verwendet wird. Sie sollten konsistent mit dem Schema Versioning sein, die beispielsweise wird wie Versionsnummern erhöht werden und welche jedes Element in die vier Versionsnummer gibt verwendet.

*Alle Versionen der Treiber Versionen für jedes Update Pakete übereinstimmen soll?*

Es wird empfohlen, Zahlen folgen-Paket die Treiberversion haben eine ähnliche Versioning Schema so weit wie möglich, aber es ist nicht erforderlich, dass alle Versionen von alle Pakete identisch sein. Jedes Paket aktualisiert werden, benötigen eine höhere Versionsnummer.

## <a name="span-idupdatepartitionrequirementsspanspan-idupdatepartitionrequirementsspanspan-idupdatepartitionrequirementsspanupdate-partition-requirements"></a><span id="Update_partition_requirements"></span><span id="update_partition_requirements"></span><span id="UPDATE_PARTITION_REQUIREMENTS"></span>Aktualisierung von partition


**Warnung**  
Alle Benutzerdaten und Einstellungen werden beibehalten, wenn Updates auf dem Gerät installiert werden. Sie sind erforderlich, um sicherzustellen, dass die Einstellungen beibehalten werden, wenn Geräte aktualisiert werden.

 

Die meisten Updates werden an das Hauptfenster Betriebssystem vorgenommen. Möglicherweise gibt es andere Partitionen in das Gerät aktualisieren müssen. Dieser Abschnitt enthält Informationen zu den Partitionen aktualisiert werden können.

Info zu den PA Partitionen erhalten Sie den SoC Hersteller.

**Wichtige**  
Partition Layout Änderungen werden auf dem Gerät nicht unterstützt.  Wenn Sie binäre Partition Pakete, die eine neue Partitionslayout abhängig sind senden, auftreten nicht definierte Ergebnisse, wenn sie auf das Gerät angewendet werden

 

Die folgenden Partitionen können aktualisiert werden:

-   EFIESP – Start-Manager, Boot-Konfigurationsdatenbank, UEFI-apps

-   UEFI

-   SBL1, SBL2, SBL3 – sichere Boot Ladeprogramme

-   U/MIN

-   TZ

-   PLAT – ACPI-Tabelle

-   WINSECAPP

-   Hauptfenster OS

OEMs müssen die folgenden Partitionen nicht aktualisieren.

-   DPP

-   Daten – Partition der Benutzerdaten

-   SD-Karte

-   Aktualisieren des Betriebssystems

## <a name="span-idacpitableversioningduringbspupdatesspanspan-idacpitableversioningduringbspupdatesspanspan-idacpitableversioningduringbspupdatesspanacpi-table-versioning-during-bsp-updates"></a><span id="ACPI_table_versioning_during_BSP_updates"></span><span id="acpi_table_versioning_during_bsp_updates"></span><span id="ACPI_TABLE_VERSIONING_DURING_BSP_UPDATES"></span>ACPI Tabelle Versioning während BSP-updates


Jedes Mal, wenn Sie eine ACPI-Tabelle in einem Update BSP ändern, sollten Sie das Feld **OEMRevision** im **DefinitionBlock** -Objekt für die Tabelle erhöhen. Dies stellen Sie sicher, dass das Betriebssystem die neuesten ACPI Konfigurationsdaten verwendet wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Neue RequestForMicrosoftUpdate-cmdlet](new-requestformicrosoftupdate-cmdlet.md)

[Neue RequestForUpdate-cmdlet](new-requestforupdate-cmdlet.md)

 

 






