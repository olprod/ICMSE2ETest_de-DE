---
title: BrowserFavorite CSP
description: BrowserFavorite CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5d2351ff-2d6a-4273-9b09-224623723cbf
ms.openlocfilehash: 0effbc5dcc36cc13bc89bb88007cdd6cc2afa8a5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="browserfavorite-csp"></a>BrowserFavorite CSP


Der Dienstanbieter für BrowserFavorite Konfiguration wird zum Hinzufügen und Entfernen von URLs aus der Favoritenliste auf einem Gerät verwendet.

> **Hinweis**  Windows Phone 8.1 wird nur BrowserFavorite CSP unterstützt.

 

BrowserFavorite Konfigurationsdienstanbieter werden nur die Favoriten auf der Stammebene Favoritenordner verwaltet. Verwalten nicht Unterordner unter dem Stammordner bevorzugten noch verwaltet jedoch Favoriten unter einem Unterordner.

> **Hinweis**  
Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_INTERNET\_EXPLORER\_FAVORITEN-Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Das folgende Diagramm zeigt den BrowserFavorite Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz Gerät (OMA)-Clientbereitstellung verwendet. Das Protokoll OMA Gerätemanagement wird mit dieser Konfigurationsdienstanbieter nicht unterstützt.

![Browserfavorite Csp (cp)](images/provisioning-csp-browserfavorite-cp.png)

<a href="" id="favorite-name-------------"></a>***Name des Favoriten***   
Erforderlich. Gibt den benutzerfreundlichen Namen des favorite URLS, die in der Liste der Favoriten von Internet Explorer angezeigt wird.

> **Hinweis**  Der *Name des Favoriten* sollte nur Zeichen enthalten, die im Dateisystem Windows gültig sind. Ungültigen Zeichen sind: \\ /: \* ? " &lt; &gt; |

 

Die gleichen bevorzugten zweimal hinzufügen wird nur ein Vorkommen der Favoritenliste hinzugefügt. Wenn Favoriten hinzugefügt wird, wenn eine andere bevorzugten mit dem gleichen Namen, aber eine andere URL bereits in der Favoritenliste ist, wird durch den neuen Favoriten der vorhandene Favoriten ersetzt.

<a href="" id="url"></a>**URL**  
Optional Gibt den vollständigen URL für den Favoriten an.

## <a name="oma-client-provisioning-examples"></a>Beispiele für die Bereitstellung OMA-client


Hinzufügen einen neuen Browser Favoriten an.

``` syntax
<?xml version="1.0" encoding="UTF-8" ?>
<wap-provisioningdoc>
  <characteristic type="BrowserFavorite">
    <characteristic type="Help and how-to">
      <parm name="URL" value="http://www.microsoft.com/windowsphone/en-US/howto/wp7/default.aspx"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


Die folgende Tabelle enthält die benutzerdefinierten Elemente von Microsoft, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elemente</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>noparm</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>nocharacteristic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p>
<p>Rekursive Abfrage: Ja</p>
<p>Abfragen auf oberster Ebene: Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






