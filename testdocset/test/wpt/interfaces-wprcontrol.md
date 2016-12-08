---
title: Schnittstellen
description: Schnittstellen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d986953c-cadf-4c6e-a204-12a29e0b672e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b351c1a93d934aa5ee02e3badd928360523dde00
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="interfaces"></a>Schnittstellen


Dieser Abschnitt beschreibt die Schnittstellen, die die WPRControl-API bietet.

## <a name="in-this-section"></a>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[IControlErrorInfo](icontrolerrorinfo.md)</p></td>
<td><p>Bietet Funktionen, die Abrufen von Informationen zu Fehlern, die auftreten, wenn der Steuerelement-Manager einen Vorgang ausführt.</p></td>
</tr>
<tr class="even">
<td><p>[IControlManager](icontrolmanager.md)</p></td>
<td><p>Stellt die Windows Performance Aufzeichnung (WPR)-Manager, die ETW-Sitzungen steuert.</p></td>
</tr>
<tr class="odd">
<td><p>[IControlProgressHandler](icontrolprogresshandler.md)</p></td>
<td><p>Stellt einen Client-Side-Handler, von der Updates erhält, wenn die Bibliothek einen Vorgang ausführt.</p></td>
</tr>
<tr class="even">
<td><p>[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)</p></td>
<td><p>Bietet eine COM-Enumeration Standardmethode für eine Auflistung von [IControlErrorInfo](icontrolerrorinfo.md) -Schnittstellen auflisten.</p></td>
</tr>
<tr class="odd">
<td><p>[IEnumProfile](ienumprofile.md)</p></td>
<td><p>Bietet eine COM-Enumeration Standardmethode für eine Auflistung von [IProfile](iprofile.md) -Schnittstellen auflisten.</p></td>
</tr>
<tr class="even">
<td><p>[IOnOffTransitionManager](ionofftransitionmanager.md)</p></td>
<td><p>Ermöglicht dem Client die Profile von der [IProfileCollection](iprofilecollection.md) der Registrierung für Boot Tracing gespeichert.</p></td>
</tr>
<tr class="odd">
<td><p>[IParsingErrorInfo](iparsingerrorinfo.md)</p></td>
<td><p>Funktionen, die Abrufen von Informationen zu XML-Überprüfungsfehler enthält.</p></td>
</tr>
<tr class="even">
<td><p>[IProfile](iprofile.md)</p></td>
<td><p>Stellt ein einzelnes Profil, das der Client gesteuert.</p></td>
</tr>
<tr class="odd">
<td><p>[IProfileCollection](iprofilecollection.md)</p></td>
<td><p>Stellt eine Auflistung von Profilen, die als Einheit die Bibliothek ausgeführt wird.</p></td>
</tr>
<tr class="even">
<td><p>[ITraceMergeProperties](itracemergeproperties.md)</p></td>
<td><p>Ermöglicht dem Client Richtlinien zum Zusammenführen mehrerer Ereignis (ETL) ablaufverfolgungsprotokolldateien mithilfe von XML angeben.</p></td>
</tr>
<tr class="odd">
<td><p>[ITraceMergeTextHandler](itracemergetexthandler.md)</p></td>
<td><p>Ruft den Text und andere Metadaten, die vom Benutzer hinzugefügt wurde.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[WPRControl-API-Referenz](wprcontrol-api-reference.md)

 

 







