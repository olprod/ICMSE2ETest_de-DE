---
title: IControlManager
description: IControlManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4c6d4a0b-5a66-4fcc-ad8a-69c68a7e7fcc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6510c4d68929662bad4eec1965d147017b5175d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolmanager"></a>IControlManager


Stellt den Manager Windows Performance Aufzeichnung, der Event Tracing for Windows (ETW) Sitzungen gesteuert. Der Client sendet eine Auflistung von Benutzerprofilen mithilfe der Benutzeroberfläche [IProfileCollection](iprofilecollection.md) , und der Manager kann starten, aktualisieren, Abbrechen, speichern, beenden oder Abfragen der ETW-Sitzung oder Anbieter, die einzelnen Profile beschreibt. Der Client kann an den [IControlProgressHandler](icontrolprogresshandler.md) -Handler, Updates über den Vorgang zu erhalten, die der Manager führt zu einem Zeiger übergeben.

## <a name="syntax"></a>Syntax


``` syntax
{
  [propget, id(1), helpstring("property ControlProgressHandler")] HRESULT ControlProgressHandler
    ([out, retval] IControlProgressHandler** ppControlProgressHandler);
  [propput, id(1), helpstring("property ControlProgressHandler")] HRESULT ControlProgressHandler
    ([in] IControlProgressHandler* pControlProgressHandler);
  [id(2), helpstring("Start")] HRESULT Start
    ([in] IProfileCollection* pProfileCollection);
  [id(3), helpstring("Update")] HRESULT Update
    ([in] IProfileCollection* pProfileCollection);
  [id(4), helpstring("Cancel")] HRESULT Cancel
    ([in] IProfileCollection* pProfileCollection);
  [id(5), helpstring("Save")] HRESULT Save
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties);
  [id(6), helpstring("Stop")] HRESULT Stop
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties);
  [id(7), helpstring("QueryXML")] HRESULT QueryXML
    ([out] BSTR* pbstrResults,
    [in] VARIANT_BOOL fValidateRuntimeState);
  [id(8), helpstring("Query")] HRESULT Query
    ([out] IProfileCollection** ppProfileCollection,
    [in] VARIANT_BOOL fValidateRuntimeState);
  [propget, id(9), helpstring("property TraceMergeTextHandler")] HRESULT TraceMergeTextHandler
    ([out, retval] ITraceMergeTextHandler** ppTraceMergeTextHandler);
  [propput, id(9), helpstring("property TraceMergeTextHandler")] HRESULT TraceMergeTextHandler
    ([in] ITraceMergeTextHandler* pTraceMergeTextHandler);
  [propget, id(10), helpstring("property TemporaryTraceDirectory")] HRESULT TemporaryTraceDirectory
    ([out, retval] BSTR* pbstrTemporaryTraceDirectory);
  [propput, id(10), helpstring("property TemporaryTraceDirectory")] HRESULT TemporaryTraceDirectory
    ([in] BSTR bstrTemporaryTraceDirectory);
  [id(11), helpstring("GetProviderNameFromGuid")] HRESULT GetProviderNameFromGuid
    ([out] BSTR* bstrProviderIdStr,
    [in] REFGUID ProviderId);
  [id(12), helpstring("GetProviderGuidFromName")] HRESULT GetProviderGuidFromName
    ([out] GUID* ProviderId,
    [in] BSTR bstrProViderName);
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
<td><p>[Starten](start-icontrolmanager.md)</p></td>
<td><p>Startet eine Aufzeichnung.</p></td>
</tr>
<tr class="even">
<td><p>[Update](update-icontrolmanager.md)</p></td>
<td><p>Aktualisiert eine Benutzerprofildienst-Auflistung.</p></td>
</tr>
<tr class="odd">
<td><p>[Abbrechen](cancel.md)</p></td>
<td><p>Beendet eine Aufzeichnung ohne Speichern der Daten.</p></td>
</tr>
<tr class="even">
<td><p>[Speichern](save-icontrolmanager.md)</p></td>
<td><p>Speichert eine Aufzeichnung, die in zirkulären Puffer im Arbeitsspeicher auf dem angegebenen Ereignis Ablaufverfolgungs-Protokolldatei (ETL) angemeldet ist.</p></td>
</tr>
<tr class="odd">
<td><p>[Beenden](stop-icontrolmanager.md)</p></td>
<td><p>Beendet eine Aufzeichnung, und speichert ihn in die angegebene Ereignis Trace-Protokolldatei (ETL).</p></td>
</tr>
<tr class="even">
<td><p>[QueryXML](queryxml.md)</p></td>
<td><p>Gibt das XML-Format des derzeit ausgeführten Profils und gibt an, ob das Profil ordnungsgemäß ausgeführt wird.</p></td>
</tr>
<tr class="odd">
<td><p>[Abfrage](query-icontrolmanager.md)</p></td>
<td><p>Fragt die Eigenschaften der Sitzung und Anbieter in allen Profilen.</p></td>
</tr>
<tr class="even">
<td><p><strong>propget</strong></p></td>
<td><p>Ruft die angegebene Eigenschaft ab.</p></td>
</tr>
<tr class="odd">
<td><p><strong>propput</strong></p></td>
<td><p>Legt die angegebene Eigenschaft fest.</p></td>
</tr>
<tr class="even">
<td><p>[GetProviderNameFromGuid](getprovidernamefromguid.md)</p></td>
<td><p>Ruft den Namen des von der angegebenen GUID ab.</p></td>
</tr>
<tr class="odd">
<td><p>[GetProviderGuidFromName](getproviderguidfromname.md)</p></td>
<td><p>Ruft den Anbieter GUID der dem angegebenen Namen ab.</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>Eigenschaften


In der folgenden Tabelle beschreibt die Parameter der Eigenschaften an, denen diese Schnittstelle abgerufen oder festgelegt werden kann.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaft</th>
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ControlProgressHandler</strong></p></td>
<td><p><em>PpControlProgressHandler</em> [Out]</p></td>
<td><p>Zeiger auf die Client-seitigen Implementierung der [IControlProgressHandler](icontrolprogresshandler.md) -Schnittstelle.</p></td>
</tr>
<tr class="even">
<td><p><strong>ControlProgressHandler</strong></p></td>
<td><p><em>pControlProgressHandler</em> [in]</p></td>
<td><p>Zeiger auf die Client-seitigen Implementierung der <strong>IControlProgressHandler</strong> -Schnittstelle. E_POINTER gibt ein ungültiger Zeiger an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TraceMergeTextHandler</strong></p></td>
<td><p><em>PpTraceMergeTextHandler</em> [Out]</p></td>
<td><p>Zeiger auf den Text und einige andere Merge Zeitinformationen in der Verfolgung von [ITraceMergeTextHandler](itracemergetexthandler.md) -Schnittstelle eingefügt.</p></td>
</tr>
<tr class="even">
<td><p><strong>TraceMergeTextHandler</strong></p></td>
<td><p><em>pTraceMergeTextHandler</em> [in]</p></td>
<td><p>Zeiger auf den Text und einige andere Merge Zeitinformationen in der Verfolgung von <strong>ITraceMergeTextHandler</strong> -Schnittstelle eingefügt. E_POINTER gibt ein ungültiger Zeiger an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TemporaryTraceDirectory</strong></p></td>
<td><p><em>PbstrTemporaryTraceDirectory</em> [Out]</p></td>
<td><p>Zeiger auf den Pfad des Verzeichnisses, in dem die Überprüfung vor dem zusammengeführten Ablaufverfolgungsdateien angemeldet sind. Der Standardwert ist der Ordner % Temp%.</p></td>
</tr>
<tr class="even">
<td><p><strong>TemporaryTraceDirectory</strong> [in]</p></td>
<td><p><em>bstrTemporaryTraceDirectory</em></p></td>
<td><p>Der Pfad des Verzeichnisses, in dem die Überprüfung vor dem zusammengeführten Ablaufverfolgungsdateien angemeldet sind.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







