---
title: IParsingErrorInfo
description: IParsingErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bdec574b-3863-499f-8bf3-fe89d4400d29
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ef44c7c6ed88e1495975d278e150b6d5f8829acc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iparsingerrorinfo"></a>IParsingErrorInfo


Stellt Funktionen, die angeben, in dem Fehler bei der Überprüfung einer XML-Datei bereit. Die Schnittstelle wird von der COM- [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161) -Schnittstelle, die Funktionen bereitstellt, die kontextbezogene Fehlerinformationen zugreifen.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("GetColumnNumber")] HRESULT GetColumnNumber
    ([out, retval] ULONG* pColumnNumber);
  [id(2), helpstring("GetLineNumber")] HRESULT GetLineNumber
    ([out, retval] ULONG* pLineNumber);
  [id(3), helpstring("GetElementType")] HRESULT GetElementType
    ([out, retval] BSTR* pbstrElementType);
  [id(4), helpstring("GetElementId")] HRESULT GetElementId
    ([out, retval] BSTR* pbstrElementId);
};
```

## <a name="functions"></a>Funktionen


In der folgenden Tabelle beschreibt die Funktionen, die diese Schnittstelle bereitstellt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[GetColumnNumber](getcolumnnumber.md)</p></td>
<td><p>Gibt die Spaltennummer der Überprüfungsfehler zurück.</p></td>
</tr>
<tr class="even">
<td><p>[GetLineNumber](getlinenumber.md)</p></td>
<td><p>Gibt die Nummer der Überprüfungsfehler zurück.</p></td>
</tr>
<tr class="odd">
<td><p>[GetElementType](getelementtype.md)</p></td>
<td><p>Gibt den Typ des Elements, an dem der Validierungsfehler aufgetreten ist.</p></td>
</tr>
<tr class="even">
<td><p>[GetElementId](getelementid.md)</p></td>
<td><p>Gibt den Element Bezeichner bei dem Überprüfungsfehler aufgetreten ist.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







