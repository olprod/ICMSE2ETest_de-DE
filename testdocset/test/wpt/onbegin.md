---
title: OnBegin
description: OnBegin
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 125d9c1c-bc34-4642-ae9c-ddd0f62745cb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e0eda73f9536214c87cada6f39e8bf3017564b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onbegin"></a>OnBegin


Weist die Bibliothek, um den Fortschritt eines Vorgangs Vorgang fortzusetzen.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT OnBegin();
```

## <a name="parameters"></a>Parameter


Keiner.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rückgabewert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>Gibt Erfolg an. Der Vorgang fortgesetzt wird.</p></td>
</tr>
<tr class="even">
<td><p>E_ABORT</p></td>
<td><p>Der Client hat angefordert, um den Vorgang abzubrechen. Wenn der Benutzer auf <strong>Abbrechen</strong>klickt, gibt der Client beispielsweise diesen Code zurück.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Diese Methode wird in Rückrufe für verschiedene Tracing Aktionen wie starten oder Beenden eines Traces verwendet. Wird aufgerufen, unmittelbar bevor die Aktion beginnt.

## <a name="related-topics"></a>Verwandte Themen


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







