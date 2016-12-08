---
title: IConfigServiceProvider2 GetNode
description: IConfigServiceProvider2 GetNode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4dc10a59-f6a2-45c0-927c-d594afc9bb91
ms.openlocfilehash: 87f4d1aaf000229f7fb3196925ad611a1afd8a78
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2getnode"></a>IConfigServiceProvider2::GetNode


Diese Methode gibt einen Knoten vom Konfigurationsdienstanbieter basierend auf den Pfad, der übergeben wurde. Der zurückgegebene Knoten ist ein untergeordneter des Stammknotens.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetNode([in] IConfigManager2URI* pURI, 
                [out] ICSPNode** ppNode,
                [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>Parameter

<a href="" id="puri"></a>*pUri*
<ul style="list-style-type:none">
<li>
Der URI des untergeordneten Knotens relativ zu den Stammknoten. Beispielsweise ruft ConfigManager2 Zugriff auf den Knoten "./Vendor/Contoso/SampleCSP/ContainerA/UserName" die Konfiguration des Dienstanbieters `GetNode` -Methode auf und übergibt eine IConfigManager2URI-Instanz, die den URI "SampleCSP/ContainerA/UserName" darstellt.
</li>
</ul>
<br>
<a href="" id="ppnode"></a>*ppNode*
<ul style="list-style-type:none">
<li>
Wenn die Abfrage erfolgreich ist, wird die ICSPNode-Instanz an der Position *pUri* in die Konfiguration des Dienstanbieters Struktur zurückgegeben.
</li>
</ul>
<br>
<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*
<ul style="list-style-type:none">
<li>
Knoten unterstützen die folgenden Features.

<table>
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
</li>
</ul>
<br>

## <a name="return-value"></a>Rückgabewert

Diese Methode gibt ein ICSPNode zurück. Wenn die Funktion gibt null zurück, rufen Sie GetLastError, wenn Sie den Fehlerwert erhalten möchten.

Der Wert S\_OK gibt an, dass ein Knoten erfolgreich gefunden wurde. CFGMGR\_E\_NODENOTFOUND gibt an, dass der Knoten nicht vorhanden ist. Beachten Sie, dass dies normal, wie in der Groß-/Kleinschreibung des optionalen Knoten sein kann.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

 






