---
title: ITraceMergeTextHandler
description: ITraceMergeTextHandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0827802d-a62a-4420-8bb9-83f8af650669
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e3a2dc5baef5e80ba378fe83d776fbea50159a1b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="itracemergetexthandler"></a>ITraceMergeTextHandler


Ruft den Text und andere Metadaten, die vom Benutzer hinzugefügt wurde.

## <a name="syntax"></a>Syntax


``` syntax
{
    [propget, id(1), helpstring("Count")] HRESULT Count([out, retval] ULONG* cText);
    [id(2), helpstring("GetText")] HRESULT GetText([in] ULONG iText, [out] BSTR* pbstrText);
    [id(3), helpstring("WaitForText")] HRESULT WaitForText([in] ULONG Milliseconds);
    [id(4), helpstring("GetFileName")] HRESULT GetFileName([out] BSTR* pbstrFileName);
    [id(5), helpstring("GetNGenPdbsPath")] HRESULT GetNGenPdbsPath([out] VARIANT_BOOL* pfEnable, [out] BSTR* pbstrNGenPdbsCachePath, [out] BSTR* pbstrNGenPdbsTargetPath);
};
```

## <a name="functions"></a>Funktionen


In der folgenden Tabelle werden die Funktionen, die diese Schnittstelle stellt beschrieben.

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
<td><p><strong>propget</strong></p></td>
<td><p>Gibt den Wert der angegebenen Eigenschaft zurück.</p></td>
</tr>
<tr class="even">
<td><p>["GetText"](gettext.md)</p></td>
<td><p>Ruft die Zeichenfolge aus der angegebenen Datei.</p></td>
</tr>
<tr class="odd">
<td><p>[WaitForText](waitfortext.md)</p></td>
<td><p>Wartet, bis der Benutzer die entsprechenden Textzeichenfolgen und ruft hinzufügt.</p></td>
</tr>
<tr class="even">
<td><p>[GetFileName](getfilename.md)</p></td>
<td><p>Ruft den Dateinamen ab.</p></td>
</tr>
<tr class="odd">
<td><p>[GetNGenPdbsPath](getngenpdbspath.md)</p></td>
<td><p>Ruft den Pfad zum NGEN PDB-Dateien.</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>Eigenschaften


Die folgende Tabelle beschreibt die Eigenschaften, die diese Schnittstelle bereitstellt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Anzahl</strong></p></td>
<td><p>Gibt die Anzahl der Einträge im Text vom Benutzer hinzugefügt wurden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







