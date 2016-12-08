---
title: ICSPNode
description: ICSPNode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 023466e6-a8ab-48ad-8548-291409686ac2
ms.openlocfilehash: 017c74b93528f5efa5e29b9f5d48ccb04d38cca2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnode"></a>ICSPNode

Diese Schnittstelle ist die meisten Aufgaben in einem Konfigurationsdienstanbieter. Jeder einzelne Knoten in einer Konfiguration Service Provider Struktur wird durch eine separate Implementierung dieser Schnittstelle dargestellt. Die Aktionen eines Clients ConfigManager2 werden in der Regel in Anrufe an eine Instanz einer ICSPNode übersetzt.

Diese Methoden müssen, wenn sie nicht möchten, den Knoten Zustand am Ende der Methode den Status entspricht vor dem Aufruf der Methode implementiert werden.

Einige Knoten werden nicht für bestimmte Aktionen ausführen, und können CFGMGR zurückgeben\_E\_COMMANDNOTALLOWED für diese Methoden. Für jede Methode, die implementiert wird für extern – ungeachtet Knoten, muss die contrary-Methode auch implementiert werden durch "Determine Knotenvorgänge" Entwerfen [eines benutzerdefinierten Konfiguration Dienstanbieters](design-a-custom-windows-csp.md)definierten.

Die folgende Tabelle zeigt die von dieser Schnittstelle, die OEMs implementieren müssen definierten Methoden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Methode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[ICSPNode::Add](icspnodeadd.md)</p></td>
<td><p>Ein Knoten Konfiguration Service Provider ein direkt untergeordnetes Element hinzugefügt, und gibt einen Zeiger auf den neuen untergeordneten Knoten.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::Clear](icspnodeclear.md)</p></td>
<td><p>Löscht den Inhalt und die untergeordneten Elemente des aktuellen Knotens der Konfiguration Service Provider. Wird aufgerufen, bevor Sie [ICSPNode::DeleteChild](icspnodedeletechild.md).</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::Copy](icspnodecopy.md)</p></td>
<td><p>Es wird eine Kopie des aktuellen Knotens im angegebenen Pfad innerhalb des Konfigurations-Dienstanbieters. Wenn der Zielknoten vorhanden ist, sollten sie überschrieben.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::DeleteChild](icspnodedeletechild.md)</p></td>
<td><p>Löscht den angegebenen untergeordneten Knoten aus der Knoten Konfiguration Service Provider.</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::DeleteProperty](icspnodedeleteproperty.md)</p></td>
<td><p>Löscht eine Eigenschaft aus einem Knoten Konfiguration Service Provider.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::Execute](icspnodeexecute.md)</p></td>
<td><p>Führt eine Aufgabe auf einem intern ungeachtet Konfiguration Service Provider-Knoten in der angegebenen Benutzerdaten übergeben und ein Ergebnis zurückgibt.</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::GetChildNodeNames](icspnodegetchildnodenames.md)</p></td>
<td><p>Gibt die Liste der untergeordneten Elemente für ein Knoten Konfiguration Service Provider zurück.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::GetProperty](icspnodegetproperty.md)</p></td>
<td><p>Gibt einen Eigenschaftswert aus einem Konfiguration Service Provider Knoten zurück.</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::GetPropertyIdentifiers](icspnodegetpropertyidentifiers.md)</p></td>
<td><p>Gibt eine Liste der von den Knoten unterstützt nicht standardmäßigen Eigenschaften zurück. Das zurückgegebene Array mit zugeteilt <code>CoTaskMemAlloc</code>.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::GetValue](icspnodegetvalue.md)</p></td>
<td><p>Ruft den Typ von Wert und Daten für den Knoten ab. Interior (innerer Knotenebene) Knoten möglicherweise keinen Wert haben.</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::Move](icspnodemove.md)</p></td>
<td><p>Verschiebt dieses Knotens an einen neuen Speicherort innerhalb der Konfigurationsdienstanbieter. Die Ziel-Node bereits vorhanden, sollte sie überschrieben.</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::SetProperty](icspnodesetproperty.md)</p></td>
<td><p>Legt den Wert einer Eigenschaft für ein Knoten Konfiguration Service Provider.</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::SetValue](icspnodesetvalue.md)</p></td>
<td><p>Legt den Wert des Knotens Konfiguration Service Provider. Es ist ein Fehler zu versuchen, den Wert des inneren Knoten festzulegen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






