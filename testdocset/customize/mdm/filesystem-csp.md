---
title: FileSystem CSP
description: FileSystem CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9117ee16-ca7a-4efa-9270-c9ac8547e541
ms.openlocfilehash: a793f07474e2400619f1dd40bf3b8dc4faf8b0ef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="filesystem-csp"></a>FileSystem CSP


Der Dienstanbieter für FileSystem-Konfiguration wird verwendet, um Abfragen, hinzufügen, bearbeiten und Löschen von Dateien, Verzeichnisse und Dateiattribute auf dem mobilen Gerät. Es kann Abrufen von Informationen zum oder Verwalten von Dateien in ROM, Dateien in permanenten Speicher und Dateien auf alle austauschbaren Speicherkarte, das im Gerät vorhanden ist. Es funktioniert für Dateien, die der Benutzer als auch solche, die für den Benutzer sichtbar sind ausgeblendet werden.

> **Hinweis**  FileSystem CSP ist nur in Windows 10 Mobile unterstützt.

 

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_CSP\_OEM-Funktionen, die aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

Im folgenden Diagramm wird das Dateisystem Configuration Service Provider Management-Objekts im Strukturformat von OMA DM verwendet. Das Protokoll OMA-Clientbereitstellung wird von dieser Konfigurationsdienstanbieter nicht unterstützt.

![FileSystem Csp (dm)](images/provisioning-csp-filesystem-dm.png)

<a href="" id="filesystem"></a>**FileSystem**  
Erforderlich. Definiert den Stamm des File System Management-Objekts. Es fungiert als das Stammverzeichnis für File Systemabfragen.

Rekursive Abfragen oder gelöscht werden für dieses Element nicht unterstützt. Fügen Sie Befehle eine neue Datei oder ein Verzeichnis im Stammpfad hinzufügen möchten.

Die folgenden Eigenschaften werden für den Stammknoten unterstützt:

-   `Name`: Der Name des Stamm-Knoten. Get-Command ist der einzige unterstützte Befehl.

-   `Type`: Den MIME-Typ der Datei, die com.microsoft/windowsmobile/1.1/FileSystemMO ist. Get-Command ist der einzige unterstützte Befehl.

-   `Format`: Das Format, das ist `node`. Get-Command ist der einzige unterstützte Befehl.

-   `TStamp`: Eine standardmäßige OMA-Eigenschaft, die angibt, dem Zeitpunkt der letzten Dateiverzeichnis wurde geändert. Der Wert wird durch eine Zeichenfolge mit einer UTC basiert, grundlegende ISO 8601-Format, vollständige Darstellung eines Wertes für Datum und Uhrzeit dargestellt, z. B. 20010711T163817Z bedeutet, dass am 11. Juli 2001 bei 16 Stunden, 38 Minuten und 17 Sekunden. Get-Command ist der einzige unterstützte Befehl.

-   `Size`: Nicht unterstützt.

-   `msft:SystemAttributes`: Einer benutzerdefinierten Eigenschaft, die Verzeichnisattributen Datei. Dieser Wert ist eine ganze Zahl Bitmaske, die die DATEI entspricht\_Attributwerte und Flags, die in der Kopfzeile Datei winnt.h definiert. Der Befehl Get und der Replace-Befehl unterstützt.

<a href="" id="file-directory"></a>***Dateiverzeichnis***  
Optional Gibt den Namen eines Verzeichnisses in das Gerätedateisystem zurück. Alle *Dateiverzeichnis* -Element kann Verzeichnisse und Dateien als untergeordnete Elemente enthalten.

Der Befehl Get gibt den Namen der Datei des Verzeichnisses zurück. Get-Befehl mit `?List=Struct` rekursiv zurückgegebenen alle untergeordneten Elementnamen (einschließlich Unterverzeichnis Namen). Get-Befehl mit `?list=StructData` Abfrage wird nicht unterstützt und gibt einen 406 Fehlercode zurück.

Der Befehl hinzufügen wird verwendet, um ein neues Verzeichnis zu erstellen. Ein neues Verzeichnis unter der Dateisystem-Root hinzufügen wird nicht unterstützt und gibt einen 405 Fehlercode zurück.

Der Replace-Befehl wird nicht unterstützt.

Der Befehl Löschen wird verwendet, um alle Dateien und Unterordner in diesem *Verzeichnis*zu löschen.

Die folgenden Eigenschaften werden für Verzeichnisse unterstützt:

-   `Name`: Name der Directory. Get-Command ist der einzige unterstützte Befehl.

-   `Type`: Die MIME-Typ der Datei, die eine leere Zeichenfolge für Verzeichnisse, die den Stammknoten nicht sind. Get-Command ist der einzige unterstützte Befehl.

-   `Format`: Das Format, das ist `node`. Get-Command ist der einzige unterstützte Befehl.

-   `TStamp`: OMA Standardeigenschaft, die angibt, das letzte Mal Dateiverzeichnis wurde geändert. Der Wert wird durch eine Zeichenfolge mit einer UTC basiert, grundlegende ISO 8601-Format, vollständige Darstellung eines Wertes für Datum und Uhrzeit dargestellt, z. B. 20010711T163817Z bedeutet, dass am 11. Juli 2001 bei 16 Stunden, 38 Minuten und 17 Sekunden. Der Befehl Get ist der einzige unterstützte Befehl.

-   `Size`: Nicht unterstützt.

-   `msft:SystemAttributes`: Eine benutzerdefinierte Eigenschaft, die Datei Verzeichnisattributen enthält. Dieser Wert ist eine Bitmaske ganze Zahl, die die DATEI entspricht\_Attributwerte und Flags, die in der Kopfzeile Datei winnt.h definiert. Diese Funktion unterstützt den Befehl Get und den Befehl ersetzen.

<a href="" id="file-name"></a>***Dateiname***  
Optional Eine Datei im Binärformat zurückgeben. Wenn die Datei ist zu groß für den Konfigurationsdienst zurückgegeben ist, gibt es stattdessen Fehlercode 413 (Anforderungsentität ist zu groß).

Der Befehl Löschen Löscht die Datei.

Der Replace Befehl wird eine gesamte Datei mit neuen Dateiinhalt aktualisiert.

Der Befehl hinzufügen Fügt die Datei in das Verzeichnis

Get-Command wird auf einem Element *Dateiname* , nur auf die Eigenschaften des Elements nicht unterstützt.

Die folgenden Eigenschaften werden für Dateien unterstützt:

-   `Name`: Der Name der Datei. Get-Command ist der einzige unterstützte Befehl.

-   `Type`: Die MIME-Typ der Datei. Dieser Wert wird immer in den generischen MIME-Typ festgelegt: `application/octet-stream`. Der Befehl Get ist der einzige unterstützte Befehl.

-   `Format`: Das Format, das für die binäre Daten codiert b64 ist wird für binäre Daten, die über Wbxml gesendet über XML und Bin-Format gesendet. Der Befehl Get ist der einzige unterstützte Befehl.

-   `TStamp`: Eine standard OMA Eigenschaft geändert, die der letzten Speicherung der Datei angegeben wurde. Der Wert wird durch eine Zeichenfolge mit einer UTC basiert, grundlegende ISO 8601-Format, vollständige Darstellung eines Wertes für Datum und Uhrzeit dargestellt, z. B. 20010711T163817Z bedeutet, dass am 11. Juli 2001 bei 16 Stunden, 38 Minuten und 17 Sekunden. Get-Command ist der einzige unterstützte Befehl.

-   `Size`: Die decodierter Content Dateigröße in Byte. Get-Command ist der einzige unterstützte Befehl.

-   `msft:SystemAttributes`: Einer benutzerdefinierten Eigenschaft, die Dateiattribute enthält. Dieser Wert ist eine Bitmaske ganze Zahl, die die DATEI entspricht\_Attributwerte und Flags, die in der Kopfzeile Datei winnt.h definiert. Der Befehl Get und der Replace-Befehl unterstützt.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






