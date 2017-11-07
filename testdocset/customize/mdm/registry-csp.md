---
title: Registrierung CSP
description: Registrierung CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2307e3fd-7b61-4f00-94e1-a639571f2c9d
ms.openlocfilehash: f28cd427bd5c747378a04301a63bdbb27e3811a4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="registry-csp"></a>Registrierung CSP


Der Dienstanbieter für Registrierung Konfiguration wird verwendet, um die Einstellungen in der Registrierung zu aktualisieren. Jedoch ist Konfiguration-Dienstanbieter, die speziell für die Einstellungen, die aktualisiert werden müssen, verwenden Sie den Workflowkonfiguration-Dienstanbieter.

>  **Hinweis**   Die Registrierung CSP wird nur für OEM-Konfiguration in Windows 10 Mobile unterstützt. Verwenden Sie diese CSP nicht für Enterprise-Remoteverwaltung.
Für Windows 10 Mobile nur dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_CSP\_OEM-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Für den CSP Registrierung nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.

Der Registrierung Konfiguration-Dienstanbieter kann über die OMA-Clientbereitstellung und das Protokoll OMA DM verwaltet werden. Wenn OMA DM verwenden, um einen Registrierungsschlüssel hinzufügen, muss auch ein untergeordneten Registrierungswert im XML-Code hinzugefügt werden.

Für die Bereitstellung von OMA Client gelten die folgenden Hinweise:

-   Abfragen der Registrierung auf der obersten Ebene ist nicht zulässig. Alle Parameter müssen einzeln abgefragt werden. Der zugrunde liegenden Datenspeicher der Registrierung eingegeben wird. Das **Datatype** -Attribut des verwenden Sie die * &lt;Parameter&gt; * Tag.

-   In dieser Dokumentation werden die Standardeigenschaften beschrieben. [Weitere Merkmale können hinzugefügt werden.

-   Da der **Registrierung** Konfiguration-Dienstanbieter den umgekehrten Schrägstrich verwendet (\) Zeichen als Trennzeichen zwischen den Schlüsselnamen umgekehrte Schrägstriche, die auftreten, verwenden Sie im Namen eines Registrierungsschlüssels geschützt werden muss. Umgekehrte Schrägstriche mithilfe von zwei sequenzielle umgekehrte Schrägstriche Escapezeichen umgewandelt werden können (\\\).

Die standardmäßige Sicherheitsrolle ordnet jeder untergeordnete Knoten, es sei denn, die untergeordneten Knoten bestimmte Berechtigung gewährt wird. Die Sicherheitsrolle für Unterknoten spezifischen Implementierung ist, und kann von OEMs und Mobilfunkbetreiber geändert werden.

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierte Elemente


In der folgenden Tabelle werden die benutzerdefinierten Microsoft-Elemente, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt veranschaulicht.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elemente</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfrage</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>noparm</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p>
<p>Rekursive Abfrage: Ja</p>
<p>Abfragen auf oberster Ebene Ebene: Nein</p></td>
</tr>
</tbody>
</table>

 

Verwenden Sie diese Elemente standard OMA-Clientbereitstellung XML-Konfigurationsdatei zu erstellen. Informationen zu bestimmten Elementen finden Sie unter MSPROV DTD Elemente.

## <a name="supported-data-types"></a>Unterstützte Datentypen


In der folgenden Tabelle zeigt die Datentypen, die von die dieser Konfigurationsdienstanbieter unterstützt.

<table>
<colgroup>
<col width="15%" />
<col width="15%" />
<col width="70%" />
</colgroup>
<thead>
<tr class="header">
<th>XML-Datentyp</th>
<th>Systemeigene Registrierungstyp</th>
<th>XML-Format</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>integer</p></td>
<td><p>REG_DWORD</p></td>
<td><p>Ganzzahl Eine Abfrage dieses Parameters gibt vom Typ Integer zurück.</p></td>
</tr>
<tr class="even">
<td><p>boolean</p></td>
<td><p>REG_DWORD</p></td>
<td><p>Integer-Wert von 1 oder 0. Eine Abfrage dieses Parameters gibt vom Typ Integer zurück.</p></td>
</tr>
<tr class="odd">
<td><p>float</p></td>
<td><p>REG_SZ</p></td>
<td><p>Gleitkommazahl Eine Abfrage dieses Parameters gibt einen String-Typ.</p></td>
</tr>
<tr class="even">
<td><p>string</p></td>
<td><p>REG_SZ</p></td>
<td><p>Zeichenfolge Eine Abfrage dieses Parameters gibt einen String-Typ.</p></td>
</tr>
<tr class="odd">
<td><p>multiplestring</p></td>
<td><p>REG_MULTI_SZ</p></td>
<td><p>Sind mehrere Zeichenfolgen durch getrennt <strong> &amp;#xF000;</strong> und beendet mit zwei <strong> &amp;#xF000;</strong>  - Eine Abfrage dieses Parameters gibt einen Mehrfachzeichenfolge Typ.</p></td>
</tr>
<tr class="even">
<td><p>Binär</p></td>
<td><p>REG_BINARY</p></td>
<td><p>Base64-Codierung. Eine Abfrage dieses Parameters gibt ein binary-Typs zurück.</p></td>
</tr>
<tr class="odd">
<td><p>Uhrzeit</p></td>
<td><p>FILETIME im REG_BINARY</p></td>
<td><p>Das Format entspricht der ISO8601 standard, mit dem optionalen Datumsteil. Datum angegeben wird, auch auslassen der &quot;T&quot; als Trennzeichen. Eine Abfrage dieses Parameters gibt ein binary-Typs zurück.</p></td>
</tr>
<tr class="even">
<td><p>date</p></td>
<td><p>FILETIME in REG_BINARY</p></td>
<td><p>Das Datumsformat entspricht der ISO8601 standard, klicken Sie mit der Zeitteil optional. Den Zeitbereich fehlt, auch auslassen der &quot;T&quot; als Trennzeichen. Eine Abfrage dieses Parameters gibt ein binary-Typs zurück.</p></td>
</tr>
</tbody>
</table>

 

Es ist nicht möglich, unter dem aktuellen Pfad mithilfe des Registrierung Konfiguration Dienstanbieters geschachtelt Registrierungsschlüssel zuzugreifen. In diesem Fall müssen die Werte des Unterschlüssels separat mithilfe einer neuen Merkmal zugegriffen werden.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






