---
title: LoadIntoXML
description: LoadIntoXML
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: aa5556fa-d58a-450d-b217-93986c383239
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b76fc68e9155814a19fbe56797b07b373ef66fd9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadintoxml"></a>LoadIntoXML


Ruft das XML-Format aller Profile im [IProfileCollection](iprofilecollection.md) -Objekt ab.

## <a name="syntax"></a>Syntax


``` syntax
[id(5), helpstring("LoadIntoXML")] HRESULT LoadIntoXML([out] BSTR* pbstrResults);
```

## <a name="parameters"></a>Parameter


<a href="" id="pbstrresults--out-"></a>*pbstrResults* \[,\]  
Zeiger auf eine Ergebniszeichenfolge.

## <a name="return-value"></a>Rückgabewert


## <a name="remarks"></a>Bemerkungen


Diese Funktion gibt eine kombinierte Profil für die Profile, die zur Benutzerprofildienst-Auflistung hinzugefügt wurden.

## <a name="related-topics"></a>Verwandte Themen


[IProfileCollection](iprofilecollection.md)

 

 







