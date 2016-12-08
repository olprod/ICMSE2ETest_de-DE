---
title: EnterpriseAppManagement CSP
description: EnterpriseAppManagement CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 698b8bf4-652e-474b-97e4-381031357623
ms.openlocfilehash: bc8864e2084921dede15565d8f68ee3b6682c140
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseappmanagement-csp"></a>EnterpriseAppManagement CSP


Die EnterpriseAppManagement Dienstanbieter für Enterprise-Konfiguration verwendet, um die Verwaltung von Enterprise behandeln, die Aufgaben wie das Installieren von einem Enterprise-Anwendung Token, die erste zum automatischen Herunterladen von app-Verknüpfung, Abfragen installierten unternehmensanwendungen (Name und Version) automatische Aktualisierung bereits installiert unternehmensanwendungen, und entfernen alle installierten Enterprise apps (einschließlich des Enterprise-app-Tokens) während Unenrollment.

> **Hinweis**   EnterpriseAppManagement CSP ist nur in Windows 10 Mobile unterstützt.

 

Das folgende Diagramm zeigt den EnterpriseAppManagement Konfiguration-Dienstanbieter in der Strukturformat.

![Enterpriseappmanagement csp](images/provisioning-csp-enterpriseappmanagement.png)

<a href="" id="enterpriseid"></a>***Unternehmens-ID***  
Optional Ein dynamisches Knoten, der die Unternehmens-ID als GUID darstellt. Es wird verwendet, um zu registrieren oder Anmeldung unternehmensanwendungen kündigen.

Unterstützte Vorgänge sind hinzufügen, löschen, und erhalten möchten.

<a href="" id="enterpriseid-enrollmenttoken"></a>***Unternehmens-ID*/EnrollmentToken**  
Erforderlich. Zum Installieren oder aktualisieren die binäre Darstellung des Tokens Registrierung Anwendung (AET) und initiieren 'Telefon Privat' tokenüberprüfung verwendet. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

<a href="" id="enterpriseid-storeproductid"></a>***Unternehmens-ID*/StoreProductID**  
Erforderlich. Der Knoten, den Knoten ProductId hosten. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-storeproductid-productid"></a>**/ StoreProductID/ProductId**  
Die Zeichenfolge mit der ID der ersten Enterprise an (in der Regel ein Unternehmen Hub-app), der automatisch auf dem Gerät installiert wird. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="enterpriseid-storeuri"></a>***Unternehmens-ID*/StoreUri**  
Optional Die Zeichenfolge mit dem URI der ersten enterpriseanwendung auf dem Gerät installiert werden soll. Der Registrierung-Client herunterladen und installieren die Anwendung von diesem URI. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="enterpriseid-certificatesearchcriteria"></a>***Unternehmens-ID*/CertificateSearchCriteria**  
Optional Die Zeichenfolge, die die Suchkriterien für das DM registriert Clientzertifikat suchen enthält. Das Zertifikat wird für die Clientauthentifizierung beim Download von Enterprise-Anwendung verwendet. Inhalt des Unternehmens-Anwendungsserver sollten das Enterprise-registriert Clientzertifikat verwenden, um das Gerät zu authentifizieren. Der Wert muss eine URL-codiert Darstellung des x. 500 distinguished Name der Client Zertifikate Subject-Eigenschaft. X. 500-Name muss das Format von der Funktion [CertStrToName](http://go.microsoft.com/fwlink/p/?LinkId=523869) erforderlich entsprechen. Diese Suchparameter wird Groß-/Kleinschreibung beachtet. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get und hinzufügen.

> **Hinweis**   Verwenden Sie KEINE Subject = CN % 3DB1C43CD0-1624-5FBB-8E54-34CF17DFD3A1\\X00. Der Server muss diesen Wert in dem bereitgestellten Clientzertifikat ersetzen. Wenn Ihr Server ein Clientzertifikat mit dem gleichen betreffwert zurückgegeben wird, kann dies unerwartetes Verhalten verursachen. Der Server sollte immer Vorrang vor den Betreff-Wert und verwenden Sie die Standardeinstellung nicht Gerät bereitgestellten Geräte-ID Subject = Betreff = CN % 3DB1C43CD0-1624-5FBB-8E54-34CF17DFD3A1\\X00

 

<a href="" id="enterpriseid-status"></a>***Unternehmens-*ID/Status**  
Erforderlich. Der Ganzzahlwert, der den aktuellen Status der Registrierung Anwendung angibt. Gültige Werte sind 0 (AKTIVIERT), 1 (INSTALLIEREN\_DEAKTIVIERT), 2 (GESPERRT) und 3 (UNGÜLTIG). Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="enterpriseid-crlcheck"></a>***Unternehmens-ID*/CRLCheck**  
Optional Zeichenwert, der angibt, ob das Gerät eine Zertifikatsperrlistenprüfung geschehen soll, wenn Sie ein Zertifikat zum Authentifizieren des Servers verwenden. Gültige Werte sind "1" (Zertifikatsperrlistenprüfung erforderlich), "0" (Zertifikatsperrlistenprüfung nicht erforderlich). Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="enterpriseid-enterpriseapps"></a>***Unternehmens-ID*/EnterpriseApps**  
Erforderlich. Der Stammknoten an, für die einzelnen Enterprise-Anwendung bezogene Einstellungen. Bereich ist dynamisch (dieser Knoten wird automatisch erstellt, wenn der Konfigurationsdienstanbieter Unternehmens-ID hinzugefügt wird).

Unterstützte Vorgang ist Get.

<a href="" id="-enterpriseapps-inventory"></a>**/ EnterpriseApps/Inventar**  
Erforderlich. Der Stammknoten für die einzelnen Enterprise-Anwendungseinstellungen Inventar. Bereich ist dynamisch (dieser Knoten wird automatisch erstellt, wenn die Konfigurationsdienstanbieter Unternehmens-ID hinzugefügt wird).

Unterstützte Vorgang ist Get.

<a href="" id="-inventory-productid"></a>**/ Inventar / ***_ProductID_**  
Optional Ein Knoten, der s einzelnen Enterprise-Anwendung-Produkt-ID in GUID-Format enthält. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-inventory-productid-version"></a>* */Inventory/*ProductID*/Version**  
Erforderlich. Die Zeichenfolge, die die aktuelle Version der installierten enterpriseanwendung enthält. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-inventory-productid-title"></a>* */Inventory/*ProductID*/Title**  
Erforderlich. Die Zeichenfolge, die den Namen der installierten enterpriseanwendung enthält. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-inventory-productid-publisher"></a>* */Inventory/*ProductID*/Publisher**  
Erforderlich. Die Zeichenfolge, die den Namen des Herausgebers der installierten enterpriseanwendung enthält. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-inventory-productid-installdate"></a>* */Inventory/*ProductID*/InstallDate**  
Erforderlich. Die Zeit (in das Zeichen formatieren Sie JJJJ-MM-TT-HH: mm:), die die Anwendung installiert oder aktualisiert wurde. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-enterpriseapps-download"></a>**/ EnterpriseApps/Download**  
Erforderlich. Dieser Knoten gruppiert Anwendung Download-bezogenen Parameter. Enterprise-Server kann installierten unternehmensanwendungen nur automatisch aktualisiert werden. Der Endbenutzer steuert die enterpriseanwendungen herunterladen und installieren. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-download-productid"></a>**/ Download / ***_ProductID_**  
Optional Dieser Knoten enthält die GUID für die installierten Enterprise-Anwendung. Jede installierte Anwendung verfügt über einen eindeutigen Bezeichner ab. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="-download-productid-version"></a>* */Download/*ProductID*/Version**  
Optional Die Zeichenfolge, die für die Anwendung derzeit heruntergeladene Versionsinformationen (vom Anrufer festgelegt) enthält. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="-download-productid-name"></a>* */Download/*ProductID*/Name**  
Erforderlich. Die Zeichenfolge, die mit dem Namen der installierten Anwendung zurück. Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-download-productid-url"></a>* */Download/*ProductID*/URL**  
Optional Die Zeichenfolge, die die URL für die aktualisierte Version der installierten Anwendung enthält. Das Gerät wird von diesem Link Anwendungsupdates herunterladen. Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

<a href="" id="-download-productid-status"></a>* */Download/*ProductID*/Status**  
Erforderlich. Der Ganzzahlwert, der angibt, den Status des aktuellen herunterladen Prozess. In der folgenden Tabelle sind die möglichen Werte.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>0: BESTÄTIGEN</p></td>
<td><p>Warten auf Bestätigung vom Benutzer.</p></td>
</tr>
<tr class="even">
<td><p>1: IN DER WARTESCHLANGE</p></td>
<td><p>Warten auf Download zu starten.</p></td>
</tr>
<tr class="odd">
<td><p>2: HERUNTERLADEN</p></td>
<td><p>Gerade herunterladen.</p></td>
</tr>
<tr class="even">
<td><p>3: HERUNTERGELADEN</p></td>
<td><p>Wartet für die Installation zu starten.</p></td>
</tr>
<tr class="odd">
<td><p>4: INSTALLIEREN VON</p></td>
<td><p>Übergeben für die Installation.</p></td>
</tr>
<tr class="even">
<td><p>5: INSTALLIERT</p></td>
<td><p>Erfolgreich installiert</p></td>
</tr>
<tr class="odd">
<td><p>6: FEHLER</p></td>
<td><p>Anwendung wurde abgelehnt (nicht signiert ordnungsgemäß, usw. fehlerhaftes XAP-Format nicht ordnungsgemäß registriert.)</p></td>
</tr>
<tr class="even">
<td><p>7:DOWNLOAD_FAILED</p></td>
<td><p>Keine Verbindung mit Server herstellen, Datei nicht vorhanden ist, usw..</p></td>
</tr>
</tbody>
</table>

 

Bereich ist dynamisch. Unterstützte Vorgänge sind Get, hinzufügen, und Ersetzen Sie.

<a href="" id="-download-productid-lasterror"></a>* */Download/*ProductID*/LastError**  
Erforderlich. Der Ganzzahlwert, der das HRESULT des letzten Fehlercode angibt. Wenn keine Fehler aufgetreten sind, ist der Wert 0 (S\_OK). Bereich ist dynamisch.

Unterstützte Vorgang ist Get.

<a href="" id="-download-productid-lasterrordesc"></a>* */Download/*ProductID*/LastErrorDesc**  
Erforderlich. Die Zeichenfolge, die die lesbare Beschreibung des letzten Fehlercodes enthält.

<a href="" id="-download-productid-downloadinstall"></a>* */Download/*ProductID*/DownloadInstall**  
Erforderlich. Der Knoten, der Server das heruntergeladen und installiert eine aktualisierte Version des Benutzers auslösen kann die Anwendung installiert. Das Format für diesen Knoten ist null. Der Server muss das Gerät später zum Bestimmen des Status Abfragen. Für jedes Produkt-ID wird das Statusfeld für bis zu einer Woche beibehalten. Bereich ist dynamisch.

Unterstützte Vorgang ist Exec.

## <a name="remarks"></a>Hinweise


### <a name="install-and-update-line-of-business-lob-applications"></a>Installieren und die Aktualisierung Zeile des Business (LOB)

Ein Arbeitsbereich kann automatisch installieren und Aktualisieren von Line of Business Applications während einer Sitzung Management. Branchenanwendungen unterstützt eine Vielzahl von Dateitypen, einschließlich XAP-(8.0 und 8.1) und AppX AppXBundles. Ein Arbeitsbereich kann auch Applications aus XAP-Dateiformate Appx und AppxBundle Formate durch den gleichen Kanal aktualisieren. Weitere Informationen finden Sie im Abschnitt Beispiele.

### <a name="uninstall-line-of-business-lob-applications"></a>Deinstallieren von Zeile des Business (LOB) Applikationen

Ein Arbeitsbereich kann auch Remote Line of Business Applications auf dem Gerät deinstallieren. Es ist nicht möglich, dieser Mechanismus deinstallieren Store-Apps auf dem Gerät oder Line of Business Applications, die nicht installiert werden von der registrierten Jahrestag (Seite geladen Anwendungsszenarien verwenden). Weitere Informationen finden Sie im Abschnitt Beispiele

### <a name="query-installed-store-application"></a>Query installiert Store-Anwendung

Sie können bestimmen, wenn eine Store-Anwendung auf einem System installiert ist. Sie benötigen die GUID des Store-Anwendung. Sie erhalten die GUID die Informationsspeicher Anwendung indem Sie auf die URL der Anwendung Store.

Die Anwendung Microsoft Store hat eine GUID des d5dc1ebb-a7f1-df11-9264-00237de2db9e.

Verwenden Sie Folgendes Format SyncML zum Abfragen, um festzustellen, ob die Anwendung auf einem verwalteten Gerät installiert ist:

``` syntax
<Get>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7B D5DC1EBB-A7F1-DF11-9264-00237DE2DB9E%7D</LocURI>
        </Target>
      </Item>
    </Get>
```

Die Antwort vom Gerät (er enthält Liste der Unterknoten, wenn diese app im Gerät installiert ist).

``` syntax
<Results>
   <CmdID>3</CmdID>
   <MsgRef>1</MsgRef>
   <CmdRef>2</CmdRef>
   <Item>
      <Source>
          <LocURI>
             ./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7B D5DC1EBB-A7F1-DF11-9264-00237DE2DB9E%7D</LocURI>
      </Source>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
         <Type xmlns="syncml:metinf"></Type>
      </Meta>
<Data>Version/Title/Publisher/InstallDate</Data>
   </Item>
</Results>
```

### <a name="node-values"></a>Knotenwerten

Alle Knotenwerte, die unter dem ProviderID interior-Knoten der Richtlinienwerte darstellen, die der Verwaltungsserver festlegen möchte.

-   Ein Befehl hinzufügen oder ersetzen auf diesen Knoten gibt Erfolg in den beiden folgenden Fällen:

    -   Der Wert wird auf dem Gerät tatsächlich angewendet.

    -   Der Wert wird an das Gerät nicht angewendet, da das Gerät sichereren Wert bereits festgelegt wurde.

Aus Gründen der Sicherheit entspricht der Richtlinie an, die mindestens so sicher wie diejenige angefordert wird das Gerät.

-   Get-Befehl auf diesen Knoten gibt den Wert, den der Server an das Gerät nach unten geschoben.

-   Wenn Sie ein Befehl Ersetzen ein Fehler auftritt, wird der Knotenwert festgelegt, den vorherigen Wert sein, bevor der Befehl "ersetzen" angewendet wurde.

-   Wenn ein Befehl hinzufügen ein Fehler auftritt, wird der Knoten nicht erstellt werden.

Der Wert tatsächlich angewendet auf das Gerät kann über den Knoten unter dem DeviceValue interior Knoten abgefragt werden.

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Enterprise-ID "4000000001" zum ersten Mal zu registrieren:

``` syntax
<Add>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnrollmentToken</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>InsertTokenHere</Data>
   </Item>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/EnterpriseAppManagement/4000000001/CertificateSearchCriteria
         </LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>SearchCriteriaInsertedHere</Data>
   </Item>
</Add>
```

Aktualisieren Sie das Registrierung Token (beispielsweise so aktualisieren Sie eine Anwendung Abgelaufene Registrierung Token):

``` syntax
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnrollmentToken</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>InsertUpdaedTokenHere</Data>
   </Item>
</Replace>
```

Abfragen von allen installierten Anwendungen, die Enterprise-ID "4000000001" gehören:

``` syntax
<Get>
   <CmdID>2</CmdID>
   <Item>
      <Target>
          <LocURI>
    ./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory?list=StructData
          </LocURI>
      </Target>
   </Item>
</Get>
```

Die Antwort vom Gerät (die zwei installierten Programme enthält):

``` syntax
<Results>
   <CmdID>3</CmdID>
   <MsgRef>1</MsgRef>
   <CmdRef>2</CmdRef>
   <Item>
      <Source>
          <LocURI>
             ./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory
          </LocURI>
      </Source>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
         <Type xmlns="syncml:metinf"></Type>
      </Meta>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D 
         </LocURI>
      </Source>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
         <Type xmlns="syncml:metinf"></Type>
      </Meta>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D
         </LocURI>
      </Source>
      <Meta>
         <Format xmlns="syncml:metinf">node</Format>
         <Type xmlns="syncml:metinf"></Type>
      </Meta>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Version
         </LocURI>
      </Source>
      <Data>1.0.0.0</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Title
         </LocURI>
      </Source>
      <Data>Sample1</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Publisher
         </LocURI>
      </Source>
      <Data>ExamplePublisher</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/InstallDate
         </LocURI>
      </Source>
      <Data>2012-10-30T21:09:52Z</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Version
         </LocURI>
      </Source>
      <Data>1.0.0.0</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Title
         </LocURI>
      </Source>
      <Data>Sample2</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/Publisher
         </LocURI>
      </Source>
      <Data>Contoso</Data>
   </Item>
   <Item>
      <Source>
         <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB0322158-C3C2-44EB-8A31-D14A9FEC450E%7D/InstallDate
         </LocURI>
      </Source>
      <Data>2012-10-31T21:23:31Z</Data>
   </Item>
</Results>
```

## <a name="install-and-update-an-enterprise-application"></a>Installieren Sie und aktualisieren Sie eine Enterprise-Anwendung


Installieren oder Aktualisieren der installierten Anwendung mit der Produkt-ID "{B316008A-141D-4A79-810F-8B764C4CFDFB}".

Ein XAP-Update ausführen, erstellen den Namen, führen Sie URL, die Version und DownloadInstall Knoten zunächst, klicken Sie dann eine "ausführen" auf den Knoten "DownloadInstall" (alle in einem Vorgang "Atomarisch"). Wenn die Anwendung nicht vorhanden ist, wird die Anwendung automatisch ohne Eingriffe des Benutzers installiert werden. Wenn die Anwendung installiert werden kann, wird der Benutzer mit einer Warnung benachrichtigt wird.

> **Hinweis**  
1.  Wenn ein vorherige app-Update Knoten vorhanden war für dieses Produkt-ID (der Knoten kann beibehalten von bis zu 1 Woche oder sieben Tage nach eine Installation abgeschlossen ist), klicken Sie dann eine 418 (bereits vorhanden) auf "Hinzufügen" Fehler zurückgegeben. Um den 418 Fehler zu erhalten, sollte der Server einen Befehl "ersetzen" für die Knoten, die URL und der Version, und führen Sie dann auf "DownloadInstall" (in einem Vorgang "Atomarisch").

2.  Anwendung Product ID geschweiften Klammern müssen, auf dem Escapezeichen eingefügt werden {% 7 b ist und} %7 D ist.

 

``` syntax
<Atomic>
   <CmdID>2</CmdID>
   <!-- The Add command can be used if the download node does not have a matching product ID
        node in it or if the application was installer 7 or more days old. Otherwise, use the Replace command. -->
   <Add>
      <CmdID>3</CmdID>
      <Item>
         <Target>
            <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Download/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D/Name
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
         </Meta>
         <Data>ContosoApp1</Data>
      </Item>
      <Item>
         <Target>
            <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Download/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D/URL
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
         </Meta>
         <Data>http://contoso.com/enterpriseapps/ContosoApp1.xap</Data>
      </Item>
      <Item>
         <Target>
            <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Download/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D/Version</LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
         </Meta>
         <Data>2.0.0.0</Data>
      </Item>
      <Item>
         <Target>
            <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Download%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D/DownloadInstall
            </LocURI>
         </Target>
         <Data>1</Data>
      </Item>
   </Add>
   <Exec>
      <CmdID>4</CmdID>
      <Item>
         <Target>
            <LocURI>
./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Download/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D/DownloadInstall
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>0</Data>
      </Item>
   </Exec>
</Atomic>
```

## <a name="uninstall-enterprise-application"></a>Deinstallieren von Enterprise-Anwendung


Deinstallieren Sie eine installierte Enterprise-Anwendung mit der Productid "{7BB316008A-141D-4A79-810F-8B764C4CFDFB}":

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Delete>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/EnterpriseAppManagement/4000000001/EnterpriseApps/Inventory/%7BB316008A-141D-4A79-810F-8B764C4CFDFB%7D</LocURI>
        </Target>
      </Item>
    </Delete>
    <Final/>
  </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Referenz zum Konfiguration Service provider](configuration-service-provider-reference.md)

 

 






