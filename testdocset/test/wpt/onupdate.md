---
title: OnUpdate
description: OnUpdate
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0dff0606-a8f9-4698-a086-1f8ad7e6b695
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5af3c38ce663c9984888ededbf601c56096ac471
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onupdate"></a>OnUpdate


Weist die Bibliothek, um eine Operation fortzusetzen.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT OnUpdate
  ([in] ULONG CurrentValuePercent)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="currentvaluepercent"></a>*CurrentValuePercent*  
\[in\] gibt den Prozentsatz der Operation, die abgeschlossen wurde.

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
<td><p>Der Client hat angefordert, dass die Bibliothek den Vorgang abzubrechen. Beispielsweise, wenn der Benutzer auf <strong>Abbrechen</strong>klickt, gibt der Client auf die Objektbibliothek dieser Code zurück.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Diese Funktion wird häufig während einer Aktion aufgerufen, wenn einige Aktualisierung ausgeführt wird. Beispielsweise wird beim Starten der Protokollierung sie aufgerufen, nachdem alle Anbieter aktiviert ist und beim Beenden und Zusammenführen von Trace nach bestimmten Prozentsatz der Puffer zusammengeführt wird.

## <a name="related-topics"></a>Verwandte Themen


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







