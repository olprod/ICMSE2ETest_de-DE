---
title: ICSPNode kopieren
description: ICSPNode kopieren
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: cd5ce0bc-a08b-4f82-802d-c7ff8701b41f
ms.openlocfilehash: aa3dca9dbd9f50b6d701dbcf9cac46ac9005787f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodecopy"></a>ICSPNode::Copy

Diese Methode erstellt eine Kopie des aktuellen Knotens im angegebenen Pfad innerhalb des Konfigurations-Dienstanbieters. Wenn der Zielknoten vorhanden ist, sollten sie überschrieben.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT Copy([in] IConfigManager2URI* puriDestination,
             [in, out] ICSPNode** ppNewNode, 
             [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>Parameter

<a href="" id="puridestination"></a>*puriDestination*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Pfad und Name des neuen Knotens Position in Bezug auf die Konfiguration des Dienstanbieters Stammknoten.

<a href="" id="ppnewnode"></a>*ppNewNode*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Neue Knoten erstellt durch den Kopiervorgang.

<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Features, die auf dem neuen Knoten unterstützt.

<table style="margin-left:26px">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Featurename</th>
<th>Bit-Wert (in Hex)</th>
<th>Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>CSPNODE_OPTION_NATIVESECURITY</code></p></td>
<td><p>0 x 01</p></td>
<td><p>Die Option systemeigene Sicherheit gibt an, dass der Knoten verarbeitet eine eigene Sicherheit überprüft und, dass ConfigManager2 nicht vorhanden ist, zum Verwalten der Sicherheit für diesen Knoten.</p></td>
</tr>
<tr class="even">
<td><p><code>CSPNODE_OPTION_INTERNALTRANSACTION</code></p></td>
<td><p>0 x 02</p></td>
<td><p>Die Option interne Transactioning weist ConfigManager2, der Dienstanbieter für die Konfiguration der Transactioning (Rollback und Engagement) für den Knoten verarbeitet wird. Behandeln Sie interne Transactioning muss der Knoten der [ICSPNodeTransactioning](icspnodetransactioning.md)implementieren.</p></td>
</tr>
<tr class="odd">
<td><p><code>CSPNODE_OPTION_HANDLEALLPROPERTIES</code></p></td>
<td><p>0 x 04</p></td>
<td><p>Nicht verwendet.</p></td>
</tr>
<tr class="even">
<td><p><code>CSPNODE_OPTION_SECRETDATA</code></p></td>
<td><p>0 x 08</p></td>
<td><p>Nicht verwendet.</p></td>
</tr>
</tbody>
</table>

 
## <a name="return-value"></a>Rückgabewert

Ein Wert von S\_OK gibt an, dass der Knoten am neuen Speicherort kopiert wurde. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **Copy** -Methode nicht unterstützt.

## <a name="remarks"></a>Hinweise

Für extern – ungeachtet Knoten wird diese Methode implementiert wird, klicken Sie dann [ICSPNode::Add](icspnodeadd.md), [ICSPNode::SetValue](icspnodesetvalue.md), [ICSPNode::Clear](icspnodeclear.md)und [ICSPNode::DeleteChild](icspnodedeletechild.md) müssen auch implementiert oder Rollback schlägt fehl.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)






