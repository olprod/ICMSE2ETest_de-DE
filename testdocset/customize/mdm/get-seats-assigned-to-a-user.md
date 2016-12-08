---
title: "Abrufen von einem Benutzer zugewiesenen Arbeitsplätzen"
description: "Die Get-Arbeitsplätzen ein Benutzervorgang zugewiesen werden Informationen zu zugewiesenen Arbeitsplätzen im Windows Store für Business abgerufen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CB963E44-8C7C-46F9-A979-89BBB376172B
ms.openlocfilehash: 509b6b1dda68464ff1b5d4c17ae96e1a5ada1b3e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-seats-assigned-to-a-user"></a>Abrufen von Arbeitsplätzen zu einem Benutzer zugewiesen

Der Vorgang **Abrufen Arbeitsplätze, die einem Benutzer zugewiesen** werden Informationen zu zugewiesenen Arbeitsplätzen im Windows Store für Business abgerufen.

## <a name="request"></a>Anforderung

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Methode</th>
<th>Anforderungs-URI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>GET</p></td>
<td><p>Https:<span></span>/ / bspmts.mp.microsoft.com/V1/Users/{username}/Seats?continuationToken={ContinuationToken}&amp;MaxResults = {MaxResults}</p></td>
</tr>
</tbody>
</table>


### <a name="uri-parameters"></a>URI-Parameter

Die folgenden Parameter können in der Anforderung URI angegeben werden.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>useName</p></td>
<td><p>string</p></td>
<td><p>UserPrincipalName (UPN) erfordert. Der Benutzername des Zielbenutzerkontos.</p></td>
</tr>
<tr class="even">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="odd">
<td><p>maxResults</p></td>
<td><p>Inteter-32</p></td>
<td><p>Optional Default = 25, Maximum = 100</p></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthalten [SeatDetailsResultSet](data-structures-windows-store-for-business.md#seatdetailsresultset).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlercode</th>
<th>Beschreibung</th>
<th>"Wiederholen"</th>
<th>Datenfeld</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>400</p></td>
<td><p>Ungültige Parameter</p></td>
<td><p>Nein</p></td>
<td><p>Parametername</p>
<p>Ursache: Ungültiger parameter</p>
<p>Details: Zeichenfolge</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td><p>Typ: Benutzer</p>
<p>Werte: Benutzername</p></td>
</tr>
</tbody>
</table>

 

 





