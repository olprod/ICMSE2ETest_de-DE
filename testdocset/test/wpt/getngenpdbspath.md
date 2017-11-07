---
title: GetNGenPdbsPath
description: GetNGenPdbsPath
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b3abddcc-b83f-4cfc-9e9a-64ec96465b21
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 86ff5e32c29a925bfb74f1fcba64ce8f2257e612
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getngenpdbspath"></a>GetNGenPdbsPath


Gibt den Pfad für den Cache und Ziel NGEN PDB-Dateien für verwalteten Code zurück.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT GetNGenPdbsPath
  ([out] VARIANT_BOOL* pfEnable,
  [out] BSTR* pbstrNGenPdbsCachePath,
  [out] BSTR* pbstrNGenPdbsTargetPath)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pfenable"></a>*pfEnable*  
\[Skalieren\] eine vom Typ Boolean, der angibt, ob NGEN PDB-Dateien aktiviert sind.

<a href="" id="pbstrngenpdbscachepath"></a>*pbstrNGenPdbsCachePath*  
\[Skalieren\] einen Zeiger auf den Quellpfad.

<a href="" id="pbstrngenpdbstargetpath"></a>*pbstrNGenPdbsTargetPath*  
\[Skalieren\] einen Zeiger auf den Zielpfad einzugeben.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben. Fehler bei Rückgabewerte sind implementierungsspezifischen.

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
<td><p>Gibt Erfolg an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[ITraceMergeTextHandler](itracemergetexthandler.md)

 

 







