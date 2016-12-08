---
title: IProfile
description: IProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 62442c73-627c-4f91-b33e-ec3e55293d70
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4b178fcafcf4eb79b0c446833419d9f0ca43f99e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iprofile"></a>IProfile


Stellt ein Profil, das der Client gesteuert. Die Schnittstelle bietet Funktionen, die ein Profil im XML-Format, entweder aus einer Datei oder aus einer Zeichenfolge geladen wird. Der Client kann bestimmen, ob der Benutzer berechtigt ist, auf das Profil zu aktualisieren, indem hinzufügen oder Entfernen von Event Tracing for Windows (ETW) Anbieter.

## <a name="syntax"></a>Syntax


``` syntax
{
  typedef enum
  {
    LoggingMode_Unknown,
    LoggingMode_Memory,
    LoggingMode_File,
  }
  CLoggingMode;
  typedef enum
  {
    DetailLevel_Unknown,
    DetailLevel_Light,
    DetailLevel_Verbose,
  }
  CDetailLevel;
  [propget, id(1), helpstring("IsMutable")] HRESULT IsMutable
    ([out, retval] VARIANT_BOOL* pfMutable);
  [propput, id(1), helpstring("IsMutable")] HRESULT IsMutable
    ([in] VARIANT_BOOL fMutable);  [propget, id(2), helpstring("Version")] HRESULT Version
    ([out, retval] float* pVersion);
  [propget, id(3), helpstring("Author")] HRESULT Author
    ([out, retval] BSTR* pbstrAuthor);
  [propget, id(4), helpstring("Team")] HRESULT Team
    ([out, retval] BSTR* pbstrTeam);
  [propget, id(5), helpstring("Comments")] HRESULT Comments
    ([out, retval] BSTR* pbstrComments);
  [propget, id(6), helpstring("Company")] HRESULT Company
    ([out, retval] BSTR* pbstrCompany);
  [propget, id(7), helpstring("Copyright")] HRESULT Copyright
    ([out, retval] BSTR* pbstrCopyright);
  [propget, id(8), helpstring("Tag")] HRESULT Tag
    ([out, retval] BSTR* pbstrTag);
  [propget, id(9), helpstring("Id")] HRESULT Id
    ([out, retval] BSTR* pbstrId);
  [propget, id(10), helpstring("Name")] HRESULT Name
    ([out, retval] BSTR* pbstrName);
  [propget, id(11), helpstring("Description")] HRESULT Description
    ([out, retval] BSTR* pbstrDescription);
  [propget, id(12), helpstring("LoggingMode")] HRESULT LoggingMode
    ([out, retval] CLoggingMode* pLoggingMode);
  [propget, id(13), helpstring("LoggingModeString")] HRESULT LoggingModeString
    ([out, retval] BSTR* pbstrLoggingMode);
  [propget, id(14), helpstring("DetailLevel")] HRESULT DetailLevel
    ([out, retval] CDetailLevel* pDetailLevel);
  [propget, id(15), helpstring("DetailLevelString")] HRESULT DetailLevelString
    ([out, retval] BSTR* pbstrDetailLevel);
  [propget, id(16), helpstring("IsStrict")] HRESULT IsStrict
    ([out, retval] VARIANT_BOOL* pfStrict);
  [propget, id(17), helpstring("IsDefault")] HRESULT IsDefault
    ([out, retval] VARIANT_BOOL* pfDefault);
  [propget, id(18), helpstring("ProblemCategories")] HRESULT ProblemCategories
    ([out, retval] BSTR* pbstrProblemCategories);
  [id(19), helpstring("LoadFromFile")] HRESULT LoadFromFile
    ([in] BSTR bstrProfileName,
    [in] BSTR bstrFileName);
  [id(20), helpstring("LoadFromString")] HRESULT LoadFromString
    ([in] BSTR bstrProfile);
  [id(21), helpstring("IsEqual")] HRESULT IsEqual
    ([in] IProfile* pProfile);};
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
<td><p><strong>propput</strong></p></td>
<td><p>Legt die angegebene Eigenschaft fest.</p></td>
</tr>
<tr class="odd">
<td><p>[LoadFromFile](loadfromfile.md)</p></td>
<td><p>Lädt ein Profil aus der angegebenen Datei.</p></td>
</tr>
<tr class="even">
<td><p>[LoadFromString](loadfromstring.md)</p></td>
<td><p>Lädt ein Profil aus der angegebenen XML-Profil-Definition-Zeichenfolge an.</p></td>
</tr>
<tr class="odd">
<td><p>[IsEqual](isequal.md)</p></td>
<td><p>Vergleicht zwei <strong>IProfile</strong> -Objekte.</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>Eigenschaften


Diese Schnittstelle stellt die Eigenschaften, die in der folgenden Tabelle beschrieben.

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
<td><p><strong>IsMutable</strong></p></td>
<td><p><em>pfMutable</em></p></td>
<td><p>[out] Gibt einen booleschen Wert, der angibt, dass Sitzungen und Anbieter ein vorhandenes Profil hinzugefügt werden können zusammen mit dem gleichen Namen Profile mit der <strong>IProfileCollection::Add</strong> -Methode. S_OK gibt Erfolg an.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsMutable</strong></p></td>
<td><p><em>fMutable</em></p></td>
<td><p>[in] Ein boolescher Wert, der angibt, ob die Profile-Sitzungen und Anbieter hinzugefügt werden können. S_OK gibt Erfolg an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Version</strong></p></td>
<td><p><em>pVersion</em></p></td>
<td><p>[out] Gibt die Version der Profile.</p></td>
</tr>
<tr class="even">
<td><p><strong>Author</strong></p></td>
<td><p><em>pbstrAuthor</em></p></td>
<td><p>[out] Gibt den Autor der Profile an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Team</strong></p></td>
<td><p><em>pbstrTeam</em></p></td>
<td><p>[out] Gibt an, das Team, das die Profile erstellt haben.</p></td>
</tr>
<tr class="even">
<td><p><strong>Comments</strong></p></td>
<td><p><em>pbstrComments</em></p></td>
<td><p>[out] Optionale Kommentare zu den Profilen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Firma</strong></p></td>
<td><p><em>pbstrCompany</em></p></td>
<td><p>[out] Gibt an, das Unternehmen, das die Profile erstellt haben.</p></td>
</tr>
<tr class="even">
<td><p><strong>Copyright</strong></p></td>
<td><p><em>pbstrCopyright</em></p></td>
<td><p>[out] Gibt copyright-Informationen im Zusammenhang mit der Profile an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tag</strong></p></td>
<td><p><em>pbstrTag</em></p></td>
<td><p>[out] Optionale Eigenschaftswert, die verwendet werden kann, um zwischen verschiedenen Profilen zu unterscheiden.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID</strong></p></td>
<td><p><em>pbstrId</em></p></td>
<td><p>[out] Gibt den Bezeichner des Profils an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p><em>pbstrName</em></p></td>
<td><p>[out] Gibt den Namen des Profils an.</p></td>
</tr>
<tr class="even">
<td><p><strong>Beschreibung</strong></p></td>
<td><p><em>pbstrDescription</em></p></td>
<td><p>[out] Gibt die Beschreibung des Profils an.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LoggingMode</strong></p></td>
<td><p><em>pLoggingMode</em></p></td>
<td><p>[out] Gibt den Protokollierungsmodus.</p></td>
</tr>
<tr class="even">
<td><p><strong>LoggingModeString</strong></p></td>
<td><p><em>pbstrLoggingMode</em></p></td>
<td><p>[out] Gibt die Protokollierung Modus Zeichenfolge an. Mögliche Werte sind &quot;Speicher&quot; und &quot;Datei&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DetailLevel</strong></p></td>
<td><p><em>pDetailLevel</em></p></td>
<td><p>[out] Gibt den Umfang an.</p></td>
</tr>
<tr class="even">
<td><p><strong>DetailLevelString</strong></p></td>
<td><p><em>pbstrDetailLevel</em></p></td>
<td><p>[out] Gibt die Ebene Detail-Zeichenfolge an. Mögliche Werte sind &quot;verbose&quot; und &quot;Licht&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsStrict</strong></p></td>
<td><p><em>pfStrict</em></p></td>
<td><p>[out] Ein boolescher Wert, der angibt, ob die Aufzeichnung setzt zurück, wenn alle Collector oder Anbieter kann nicht gestartet werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsDefault</strong></p></td>
<td><p><em>pfDefault</em></p></td>
<td><p>[out] Ein boolescher Wert, der angibt, ob dies ein Standardprofil ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProblemCategories</strong></p></td>
<td><p><em>pbstrProblemCategories</em></p></td>
<td><p>[out] Gibt an, die Probleme, die dieses Profil ist darauf ausgelegt, um zu erkennen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







