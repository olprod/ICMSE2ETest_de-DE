---
title: "ICSPNode hinzufügen"
description: "ICSPNode hinzufügen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5f03d350-c82b-4747-975f-385fd8b5b3a8
ms.openlocfilehash: ce7ed552315358a78d8b1ac111d8870b05092a4a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeadd"></a>ICSPNode::Add

Diese Methode einen direkten untergeordneten Knoten zu einem Konfiguration Service Provider Knoten hinzugefügt und gibt einen Zeiger auf den neuen Knoten.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT Add([in] IConfigManager2URI* pChildName,
            [in] CFG_DATATYPE DataType,
            [in] VARIANT varValue, 
            [in, out] ICSPNode** ppNewNode, 
            [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>Parameter

<a href="" id="pchildname"></a>*pChildName*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Name des untergeordneten Knoten hinzufügen.

<a href="" id="datatype"></a>*Datentyp*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Der Datentyp des den untergeordneten Knoten hinzufügen. Unterstützte Typen gehören:
-   CFG\_DATATYPE\_KNOTEN

-   CFG\_DATATYPE\_NULL

-   CFG\_DATATYPE\_BINARY

-   CFG\_DATATYPE\_ganze ZAHL

-   CFG\_DATATYPE\_ZEICHENFOLGE

-   CFG\_DATATYPE\_MEHRERE\_ZEICHENFOLGE

<a href="" id="varvalue"></a>*varValue*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Wert für den untergeordneten Knoten hinzufügen.

<a href="" id="ppnewnode"></a>*ppNewNode*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Neue untergeordnete Knoten zurückgegeben.

<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Features, die auf den neuen untergeordneten Knoten unterstützt.
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
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_NATIVESECURITY</code></p></td>
<td style="vertical-align:top"><p>0 x 01</p></td>
<td style="vertical-align:top"><p>Die Option systemeigene Sicherheit gibt an, der Knoten verarbeitet wird, eine eigene Sicherheit überprüfen und ConfigManager2 nicht zum Verwalten der Sicherheit für diesen Knoten verfügt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_INTERNALTRANSACTION</code></p></td>
<td style="vertical-align:top"><p>0 x 02</p></td>
<td style="vertical-align:top"><p>Die Option interne Transactioning weist ConfigManager2, der Dienstanbieter für die Konfiguration der Transactioning (Rollback und Engagement) für den Knoten verarbeitet wird. Behandeln Sie interne Transactioning muss der Knoten der [ICSPNodeTransactioning](icspnodetransactioning.md)implementieren.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_HANDLEALLPROPERTIES</code></p></td>
<td style="vertical-align:top"><p>0 x 04</p></td>
<td style="vertical-align:top"><p>Nicht verwendet.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_SECRETDATA</code></p></td>
<td style="vertical-align:top"><p>0 x 08</p></td>
<td style="vertical-align:top"><p>Nicht verwendet.</p></td>
</tr>
</tbody>
</table>

 
## <a name="return-value"></a>Rückgabewert

Diese Methode gibt eine ICSPNode und die Featureoptionen auf dieser untergeordnete Knoten unterstützt. Wenn die Methode gibt null zurück, rufen Sie GetLastError, um den Fehlerwert zu erhalten.

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CMN\_E\_BEREITS\_EXISTS gibt an, dass ein untergeordneter Knoten mit dem gleichen Namen bereits vorhanden ist. CFGMGR\_E\_COMMANDNOTALLOWED gibt an, dass dieser Knoten die **Add** -Methode nicht unterstützt.

## <a name="remarks"></a>Hinweise

Extern – ungeachtet Knoten, für Wenn diese Methode implementiert ist, klicken Sie dann [ICSPNode::Clear](icspnodeclear.md) und [ICSPNode::DeleteChild](icspnodedeletechild.md) muss auch implementiert werden oder Rollback schlägt fehl.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






