---
title: "Datenstrukturen für Windows Store for Business"
MS-HAID:
- p\_phdevicemgmt.business\_store\_data\_structures
- p\_phDeviceMgmt.data\_structures\_windows\_store\_for\_business
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ABE44EC8-CBE5-4775-BA8A-4564CB73531B
description: 
ms.openlocfilehash: 669c06f1bedafeb6f7b185a76fcc561b9d49e29d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="data-structures-for-windows-store-for-business"></a>Datenstrukturen für Windows Store for Business


Hier wird die Liste der Datenstrukturen in Windows Store für Business-REST-APIs verwendet:

-   [AlternateIdentifier](#alternateidentifier)
-   [BulkSeatOperationResultSet](#bulkseatoperationresultset)
-   [FailedSeatRequest](#failedseatrequest)
-   [FrameworkPackageDetails](#frameworkpackagedetails)
-   [InventoryDistributionPolicy](#inventorydistributionpolicy)
-   [InventoryEntryDetails](#inventoryentrydetails)
-   [InventoryResultSet](#inventoryresultset)
-   [InventoryStatus](#inventorystatus)
-   [LicenseType](#licensetype)
-   [LocalizedProductDetail](#localizedproductdetail)
-   [OfflineLicense](#offlinelicense)
-   [PackageLocation](#packagelocation)
-   [ProductArchitectures](#productarchitectures)
-   [Produktdetails](#productdetails)
-   [ProductImage](#productimage)
-   [ProductKey](#productkey)
-   [ProductPackageDetails](#productpackagedetails)
-   [ProductPackageFormat](#productpackageformat)
-   [ProductPackageSet](#productpackageset)
-   [ProductPlatform](#productplatform)
-   [PublisherDetails](#publisherdetails)
-   [SeatAction](#seataction)
-   [SeatDetails](#seatdetails)
-   [SeatDetailsResultSet](#seatdetailsresultset)
-   [SeatState](#seatstate)
-   [SupportedProductPlatform](#supportedproductplatform)
-   [VersionInfo](#versioninfo)

## <a name="alternateidentifier"></a>AlternateIdentifier


Gibt die Eigenschaften des Bezeichners Alternative.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Typ</p></td>
<td><p>string</p></td>
<td><p>LegacyWindowStoreProductId, LegacyWindowsPhoneProductId, RedirectToThresholdProductId</p></td>
</tr>
<tr class="even">
<td><p>value</p></td>
<td><p>string</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="bulkseatoperationresultset"></a>BulkSeatOperationResultSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>seatDetails</p></td>
<td><p>Auflistung von [SeatDetails](#seatdetails)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>failedSeatOperations</p></td>
<td><p>Auflistung von [FailedSeatRequest](#failedseatrequest)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="failedseatrequest"></a>FailedSeatRequest


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>failureReason</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>productKey</p></td>
<td><p>[ProductKey](#productkey)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Benutzername</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="frameworkpackagedetails"></a>FrameworkPackageDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>Identifiziert eine bestimmte Anwendung</p></td>
</tr>
<tr class="odd">
<td><p>Speicherort</p></td>
<td><p>[PackageLocation](#packagelocation)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageFullName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageIdentityName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Architekturen</p></td>
<td><p>Auflistung von [ProductArchitectures](#productarchitectures)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageFormat</p></td>
<td><p>[ProductPackageFormat](#productpackageformat)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Plattformen</p></td>
<td><p>[ProductPlatform](#productplatform) -Auflistung</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>fileSize</p></td>
<td><p>ganze Zahl-64</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageRank</p></td>
<td><p>ganze Zahl-3232</p></td>
<td><p>Optional</p></td>
</tr>
</tbody>
</table>

 

## <a name="inventorydistributionpolicy"></a>InventoryDistributionPolicy


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Öffnen</p></td>
<td></td>
<td><p>Offenen Distribution Richtlinie - können Lizenzen/Arbeitsplätzen ohne Begrenzung zugeordnet/verbraucht werden</p></td>
</tr>
<tr class="even">
<td><p>eingeschränkt</p></td>
<td></td>
<td><p>Eingeschränkte Verteilergruppen Richtlinie - Lizenzen-Sitzplätze muss entsprechend der Anzahl der verfügbaren zugewiesen/verbraucht</p></td>
</tr>
</tbody>
</table>

 

## <a name="inventoryentrydetails"></a>InventoryEntryDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>productKey</p></td>
<td><p>[ProductKey](#productkey)</p></td>
<td><p>Bezeichner verwendet, um zusätzliche Inhalte wie Produkt Beschreibungen, offline Lizenz erhalten möchten, und Laden Sie URLs nachfolgenden Anforderungen.</p></td>
</tr>
<tr class="even">
<td><p>seatCapacity</p></td>
<td><p>Integer-64</p></td>
<td><p>Gesamtzahl der Arbeitsplätze, die für eine Anwendung erworben wurden</p></td>
</tr>
<tr class="odd">
<td><p>availableSeats</p></td>
<td><p>Integer-64</p></td>
<td><p>Anzahl der verfügbaren Arbeitsplätze verbleibenden für eine Anwendung.</p></td>
</tr>
<tr class="even">
<td><p>lastModified</p></td>
<td><p>dateTime</p></td>
<td><p>Gibt das Datum der letzten Änderung für eine Anwendung an. Änderungen für eine Anwendung enthält aktualisierte Produktdetails, Updates zu einer Anwendung und Aktualisierungen an die Menge einer Anwendung.</p></td>
</tr>
<tr class="odd">
<td><p>licenseType</p></td>
<td><p>[LicenseType](#licensetype)</p></td>
<td><p>Gibt an, ob die für eine bestimmte Anwendung Arbeitsplätzen unterstützt online oder offline-Lizenzierung.</p></td>
</tr>
<tr class="even">
<td><p>distributionPolicy</p></td>
<td><p>InventoryDistributionPolicy</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>status</p></td>
<td><p>InventoryStatus</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="inventoryresultset"></a>InventoryResultSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>ContinuationToken ist nur verfügbar, wenn eine nächste Seite vorhanden ist</p></td>
</tr>
<tr class="even">
<td><p>inventoryEntries</p></td>
<td><p>Auflistung von</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="inventorystatus"></a>InventoryStatus


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>aktive</p></td>
<td><p></p></td>
<td><p>Eintrag ist in der Organisation Inventar verfügbar</p></td>
</tr>
<tr class="even">
<td><p>entfernt</p></td>
<td><p></p></td>
<td><p>Eintrag wurde aus Bestand der Organisation entfernt</p></td>
</tr>
</tbody>
</table>

 

## <a name="licensetype"></a>LicenseType


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Online</p></td>
<td><p>Anwendung Online-Lizenz.</p></td>
</tr>
<tr class="even">
<td><p>Offline</p></td>
<td><p>Offline-Lizenz Application.</p></td>
</tr>
</tbody>
</table>

 

## <a name="localizedproductdetail"></a>LocalizedProductDetail


Gibt die Eigenschaften des lokalisierten Produkts.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>language</p></td>
<td><p>string</p></td>
<td><p>Sprache oder fallback Sprache, wenn die angegebene Sprache nicht verfügbar ist.</p></td>
</tr>
<tr class="even">
<td><p>displayName</p></td>
<td><p>string</p></td>
<td><p>Der Anzeigename der Anwendung.</p></td>
</tr>
<tr class="odd">
<td><p>description</p></td>
<td><p>string</p></td>
<td><p>App-Beschreibung, die vom Entwickler bereitgestellten kann bis zu 10.000 Zeichen sein.</p></td>
</tr>
<tr class="even">
<td><p>Bilder</p></td>
<td><p>Auflistung von [ProductImage](#productimage)</p></td>
<td><p>Grafik und Symbol mit der Anwendung verbunden sind.</p></td>
</tr>
<tr class="odd">
<td><p>Publisher</p></td>
<td><p>[PublisherDetails](#publisherdetails)</p></td>
<td><p>Herausgeber der Anwendung.</p></td>
</tr>
</tbody>
</table>

 

## <a name="offlinelicense"></a>OfflineLicense


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>productKey</p></td>
<td><p>[ProductKey](#productkey)</p></td>
<td><p>Identifiziert eine Reihe von Arbeitsplätzen mit einer Anwendung verbunden sind.</p></td>
</tr>
<tr class="even">
<td><p>licenseBlob</p></td>
<td><p>string</p></td>
<td><p>Base64-codierte offline Lizenz, die über einen CSP installiert werden kann.</p></td>
</tr>
<tr class="odd">
<td><p>licenseInstanceId</p></td>
<td><p>string</p></td>
<td><p>Version der Lizenz.</p></td>
</tr>
<tr class="even">
<td><p>requestorId</p></td>
<td><p>string</p></td>
<td><p>Organisation die Lizenz anfordert.</p></td>
</tr>
<tr class="odd">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>Die von einer Anwendung benötigt bestimmte Lizenz identifiziert.</p></td>
</tr>
</tbody>
</table>

 

## <a name="productarchitectures"></a>ProductArchitectures


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>neutral</p></td>
</tr>
<tr class="even">
<td><p>ARM</p></td>
</tr>
<tr class="odd">
<td><p>x86</p></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
</tr>
</tbody>
</table>

 

## <a name="packagecontentinfo"></a>PackageContentInfo


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>productPlatforms</p></td>
<td><p>[ProductPlatform](#productplatform) -Auflistung</p></td>
</tr>
<tr class="even">
<td><p>packageFormat</p></td>
<td><p>string</p></td>
</tr>
</tbody>
</table>

 

## <a name="packagelocation"></a>PackageLocation


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL</p></td>
<td><p>URI</p></td>
<td><p>CDN-Speicherort der Pakete. URL-Ablauf basiert auf die geschätzte Zeit bis zum Herunterladen des Pakets.</p></td>
</tr>
</tbody>
</table>

 

## <a name="productdetails"></a>Produktdetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>productKey</p></td>
<td><p>[ProductKey](#productkey)</p></td>
<td><p>Bezeichner verwendet, um zusätzliche Inhalte wie Produkt Beschreibungen, offline Lizenz erhalten möchten, und Laden Sie URLs nachfolgenden Anforderungen.</p></td>
</tr>
<tr class="even">
<td><p>productType</p></td>
<td><p>string</p></td>
<td><p>Typ des Produkts.</p></td>
</tr>
<tr class="odd">
<td><p>supportedLanguages</p></td>
<td><p>Auflistung von Zeichenfolgen</p></td>
<td><p>Der Satz von lokalisierten Sprachen für eine Anwendung.</p></td>
</tr>
<tr class="even">
<td><p>des publisherId</p></td>
<td><p>string</p></td>
<td><p>Publisher-Bezeichner.</p></td>
</tr>
<tr class="odd">
<td><p>category</p></td>
<td><p>string</p></td>
<td><p>Anwendungskategorie.</p></td>
</tr>
<tr class="even">
<td><p>alternateIds</p></td>
<td><p>Auflistung von [AlternateIdentifier](#alternateidentifier)</p></td>
<td><p>Die Bezeichner, die zum Instanziieren Sie der Installations von auf online-Anwendung verwendet werden können.</p></td>
</tr>
<tr class="odd">
<td><p>packageFamilyName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>supportedPlatforms</p></td>
<td><p>[ProductPlatform](#productplatform) -Auflistung</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="productkey"></a>ProductKey


Gibt die Eigenschaften des Product Keys an.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Produkt-ID</p></td>
<td><p>string</p></td>
<td><p>Produkt-ID für eine Anwendung, die durch den Speicher für Unternehmen verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>Produkt-ID, die eine bestimmte SKU einer Anwendung angibt.</p></td>
</tr>
</tbody>
</table>

 

## <a name="productimage"></a>ProductImage


Gibt die Eigenschaften des Bilds Produkt an.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Speicherort</p></td>
<td><p>URI</p></td>
<td><p>Speicherort der Bilder herunterladen.</p></td>
</tr>
<tr class="even">
<td><p>Zweck</p></td>
<td><p>string</p></td>
<td><p>App-Screenshots und Symbole</p></td>
</tr>
<tr class="odd">
<td><p>height</p></td>
<td><p>string</p></td>
<td><p>Die Höhe des Bilds in Pixeln.</p></td>
</tr>
<tr class="even">
<td><p>width</p></td>
<td><p>string</p></td>
<td><p>Breite des Bilds in Pixeln.</p></td>
</tr>
<tr class="odd">
<td><p>Beschriftung</p></td>
<td><p>string</p></td>
<td><p>Unbeschränkt</p></td>
</tr>
<tr class="even">
<td><p>backgroundColor</p></td>
<td><p>string</p></td>
<td><p>Format #RRGGBB</p></td>
</tr>
<tr class="odd">
<td><p>foregroundColor</p></td>
<td><p>string</p></td>
<td><p>Format #RRGGBB</p></td>
</tr>
<tr class="even">
<td><p>fileSize</p></td>
<td><p>long</p></td>
<td><p>Größe der Datei.</p></td>
</tr>
</tbody>
</table>

 

## <a name="publisherdetails"></a>PublisherDetails


Gibt die Eigenschaften Details Publisher an.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>publisherName</p></td>
<td><p>string</p></td>
<td><p>Der Name des Herausgebers.</p></td>
</tr>
<tr class="even">
<td><p>publisherWebsite</p></td>
<td><p>string</p></td>
<td><p>Die Website des Herausgebers.</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackagedetails"></a>ProductPackageDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>frameworkDependencyPackages</p></td>
<td><p>Auflistung von [FrameworkPackageDetails](#frameworkpackagedetails)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>Eine bestimmte Anwendung identifiziert.</p></td>
</tr>
<tr class="odd">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Speicherort</p></td>
<td><p>[PackageLocation](#packagelocation)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageFullName</p></td>
<td><p>string</p></td>
<td><p>beispielsweise Microsoft.BingTranslator_1.1.10917.2059_x86__8wekyb3d8bbwe</p></td>
</tr>
<tr class="even">
<td><p>packageIdentityName</p></td>
<td><p>string</p></td>
<td><p>beispielsweise Microsoft.BingTranslator</p></td>
</tr>
<tr class="odd">
<td><p>Architekturen</p></td>
<td><p>Auflistung von [ProductArchitectures](#productarchitectures)</p></td>
<td><p>Werte {X86, x 64, arm, neutral}</p></td>
</tr>
<tr class="even">
<td><p>packageFormat</p></td>
<td><p>[ProductPackageFormat](#productpackageformat)</p></td>
<td><p>AppX, Appxbundle, xap</p></td>
</tr>
<tr class="odd">
<td><p>Plattformen</p></td>
<td><p>[ProductPlatform](#productplatform) -Auflistung</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>fileSize</p></td>
<td><p>Integer-64</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageRank</p></td>
<td><p>Integer-32</p></td>
<td><p>optional</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackageset"></a>ProductPackageSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>packageSetId</p></td>
<td><p>string</p></td>
<td><p>Ein Bezeichner für die Kombination aus Anwendungspakete.</p></td>
</tr>
<tr class="even">
<td><p>productPackages</p></td>
<td><p>Auflistung von [ProductPackageDetails](#productpackagedetails)</p></td>
<td><p>Eine Auflistung von Anwendungspakete.</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackageformat"></a>ProductPackageFormat


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AppX</p></td>
</tr>
<tr class="even">
<td><p>appxBundle</p></td>
</tr>
<tr class="odd">
<td><p>XAP</p></td>
</tr>
</tbody>
</table>

 

## <a name="productplatform"></a>ProductPlatform


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>platformName</p></td>
<td><p>string</p></td>
</tr>
<tr class="even">
<td><p>minVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="odd">
<td><p>maxTestedVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
</tbody>
</table>

 

## <a name="seataction"></a>SeatAction


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Zuweisen</p></td>
</tr>
<tr class="even">
<td><p>Freigeben</p></td>
</tr>
</tbody>
</table>

 

## <a name="seatdetails"></a>SeatDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>assignedTo</p></td>
<td><p>string</p></td>
<td><p>Format = UPN(user@domain)</p></td>
</tr>
<tr class="even">
<td><p>dateAssigned</p></td>
<td><p>DateTime</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Zustand</p></td>
<td><p>[SeatState](#seatstate)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>productKey</p></td>
<td><p>[ProductKey](#productkey)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="seatdetailsresultset"></a>SeatDetailsResultSet


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Arbeitsplätzen</p></td>
<td><p>Auflistung von [SeatDetails](#seatdetails)</p></td>
</tr>
<tr class="even">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
</tr>
</tbody>
</table>

 

## <a name="seatstate"></a>SeatState


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>aktive</p></td>
</tr>
<tr class="even">
<td><p>widerrufen</p></td>
</tr>
</tbody>
</table>

 

## <a name="supportedproductplatform"></a>SupportedProductPlatform


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>platformName</p></td>
<td><p>string</p></td>
</tr>
<tr class="even">
<td><p>minVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="odd">
<td><p>maxTestedVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="even">
<td><p>Architekturen</p></td>
<td><p>Auflistung von ProductArchitectures</p></td>
</tr>
</tbody>
</table>

 

## <a name="versioninfo"></a>VersionInfo


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Typ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Haupt-</p></td>
<td><p>ganze Zahl 23</p></td>
</tr>
<tr class="even">
<td><p>Nebenversion</p></td>
<td><p>ganze Zahl 23</p></td>
</tr>
<tr class="odd">
<td><p>Build</p></td>
<td><p>ganze Zahl 23</p></td>
</tr>
<tr class="even">
<td><p>Revision</p></td>
<td><p>ganze Zahl 23</p></td>
</tr>
</tbody>
</table>

 

 






