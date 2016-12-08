---
title: EnterpriseModernAppManagement CSP
description: EnterpriseModernAppManagement CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9DD0741A-A229-41A0-A85A-93E185207C42
ms.openlocfilehash: 581196a453472b3db564beb2da2c8cb36508644e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisemodernappmanagement-csp"></a>EnterpriseModernAppManagement CSP


Der EnterpriseModernAppManagement Konfiguration-Dienstanbieter (CSP) ist für die Bereitstellung und des modernen Enterprise apps reporting verwendet. Ausführliche Informationen zur Verwendung dieser CSP zu Berichtszwecken apps Inventar, Installation und Deinstallation von apps für Benutzer apps auf Geräten bereitstellen und Verwalten von app-Lizenzen finden Sie unter [Enterprise-app-Verwaltung](enterprise-app-management.md).

> **Hinweis**  Windows Hologramm unterstützt nur benutzerspezifische Konfiguration EnterpriseModernAppManagement CSP.

 

Die folgende Abbildung zeigt den EnterpriseModernAppManagement Konfiguration-Dienstanbieter im Strukturformat dar.

![Enterprisemodernappmanagement Csp Diagramm](images/provisioning-csp-enterprisemodernappmanagement.png)![Enterprisemodernappmanagement Csp Diagramm](images/provisioning-csp-enterprisemodernappmanagement2.png)

<a href="" id="device-or-user-context"></a>**Gerät oder einen Benutzerkontext**  
Benutzerkontext **./User/Vendor/MSFT** Pfad verwenden und für Device-Kontext **./Device/Vendor/MSFT** Pfad verwenden.

> **Hinweis**  Hologramm Windows und Windows 10 Mobile unterstützen nur benutzerspezifische Konfiguration des EnterpriseModernAppManagement CSP.

 

<a href="" id="appmanagement"></a>**AppManagement**  
Erforderlich. Verwendet für Inventar und app-Verwaltung (nach der Installation).

<a href="" id="appmanagement-updatescan"></a>**AppManagement/UpdateScan**  
Erforderlich. Verwendet, um die Windows Update-Überprüfung starten.

Unterstützte Vorgang ist ausführen.

<a href="" id="appmanagement-lastscanerror"></a>**AppManagement/LastScanError**  
Erforderlich. Meldet den letzten vom Update-Scan zurückgegebenen Fehlercode.

Unterstützte Vorgang ist Get.

<a href="" id="appmanagement-appinventoryquery"></a>**AppManagement/AppInventoryQuery**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Gibt die Abfrage für app-Inventar.

Abfrageparameter:

-   Output - bestimmt die Parameter für die Informationen in AppInventoryResults Vorgang zurückgegeben. Mehrere Wert muss durch separate |. Gültige Werte sind:
    -   PackagesName - gibt die *PackageFamilyName* und *PackageFullName* der app zurück. Standard, falls nichts angegeben ist.
    -   PackageDetails - gibt alle Inventar-Attribute des Pakets. Dies umfasst alle Informationen über den Parameter PackageNames, aber RequiresReinstall wird nicht validiert.
    -   RequiredReinstall - überprüft den app-Status der apps in der Abfrage Inventar zu ermitteln, ob sie eine Neuinstallation erfordern. Dieses Attribut kann die Systemleistung nach der Anzahl der apps installiert beeinträchtigen. Neuinstallieren erfordern tritt auf, wenn Ressource Paket aktualisiert oder wenn die app in einem unbefugt geänderten Zustand befindet.
-   Quelle – Gibt die app-Klassifizierung, die an die vorhandenen Knoten Inventar ausgerichtet. Sie können einen bestimmten Filter verwenden oder kein Filter angegeben wurde werden alle Quellen zurückgegeben. Wenn kein Wert angegeben ist, werden alle Klassifikationen zurückgegeben. Gültige Werte sind:
    -   AppStore - wird dieser Klassifizierung für apps, die von Windows Store erworben wurden. Diese wurden apps direkt aus Windows Store oder Enterprise-apps aus Windows Store für Business installiert.
    -   NonStore - wird dieser Klassifizierung für apps, die nicht aus dem Windows Store erworben wurden.
    -   System - Apps, die Teil des Betriebssystems sind. Diese apps kann nicht deinstalliert werden. Diese Klassifizierung ist schreibgeschützt und kann nur inventarisierten sein.
-   PackageTypeFilter - gibt eine oder mehrere Arten von Pakete, die Sie verwenden können, um dem Benutzer oder Gerät abzufragen. Mehrere Werte müssen durch getrennt werden |. Gültige Werte sind:

    -   Main - gibt das Hauptfenster installierte Paket zurück.
    -   Verpacken - Bundle installierten Pakete zurückgegeben.
    -   Framework - gibt Framework installierten Pakete.
    -   Ressource – gibt die Ressourcen der installierten Pakete zurück. Ressourcen werden entweder Sprache, horizontal oder DirectX Ressourcen. Sie sind Teil einer Bundle aus.
    -   XAP - Rückgabetypen XAP-Paket.
    -   Alle – gibt alle Pakettypen zurück.

    Wenn kein Wert angegeben ist, werden die Kombination von Main, Bundle, Framework und XAP-zurückgegeben.

-   PackageFamilyName - gibt den Namen eines bestimmten Pakets. Sie diesen Parameter angeben, wird der Name des Paket-Produktfamilie zurückgegeben enthält das Paket diesen Wert.

    Wenn Sie diesen Wert nicht angeben, werden alle Pakete zurückgegeben.

-   Publisher - gibt den Herausgeber eines bestimmten Pakets. Dieser Parameter angegeben wird, wird die Publisher zurückgegeben, wenn der Wert im Feld Publisher vorhanden ist.

    Wenn Sie diesen Wert nicht angeben, werden alle Verleger zurückgegeben.

Unterstützte Operation wird Get und ersetzen.

Im folgenden Beispiel wird die Abfrage Inventar für den Paketnamen wird und überprüft den Status für die Neuinstallation für alle Hauptfenster Pakete, die NonStore apps sind.

``` syntax
<Replace>
   <CmdID>10</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppInventoryQuery</LocURI>
      </Target>
      <Meta><Format xmlns="syncml:metinf">xml</Format></Meta>
      <Data><Inventory Output="PackageNames|RequiresReinstall" Source="nonStore" PackageTypeFilter="Main" /></Data>
   </Item>
</Replace>
```

<a href="" id="appmanagement-appinventoryresults"></a>**AppManagement/AppInventoryResults**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Gibt die Ergebnisse für app-Inventar, die nach der Operation AppInventoryQuery erstellt wurde.

Unterstützte Vorgang ist Get.

Es folgt ein Beispiel des AppInventoryResults-Vorgangs.

``` syntax
<Get>
   <CmdID>11</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppInventoryResults</LocURI>
      </Target>
   </Item>
</Get>
```

<a href="" id="appmanagement-nonstore"></a>**AppManagement/nonStore**  
Zum Verwalten von Enterprise-apps oder Entwickler-apps, die nicht aus dem Windows Store erworben wurden.

Unterstützte Vorgang ist Get.

<a href="" id="appmanagement-system"></a>**AppManagement-System**  
Meldet apps, die als Teil des Betriebssystems installiert.

Unterstützte Vorgang ist Get.

<a href="" id="appmanagement-appstore"></a>**AppManagement/AppStore**  
Erforderlich. Verwendet zum Verwalten von apps aus dem Windows Store.

Unterstützte Vorgänge sind Get und löschen.

<a href="" id="----packagefamilyname"></a>**... / ***_PackageFamilyName_**  
Optional Paket-Produktfamilie Name (PFN) der app. Es ist eine für jede PFN auf dem Gerät beim Inventarberichte. Diese Elemente werden unter ihren Ursprung signierenden zurückgehen.

Unterstützte Vorgänge sind Get und löschen.

> **Hinweis**  XAP-Dateien verwenden Product ID anstelle von PackageFamilyName. Es folgt ein Beispiel der XAP-Produkt-ID (einschließlich der geschweiften Klammern), {12345678-9012-3456-7890-123456789012}.

 

Es folgt ein Beispiel für eine app zu deinstallieren:

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
        <!-- Uninstall app -->
        <delete>
           <CmdID>2</CmdID>
              <Item>
                 <Target>
                    <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/%7b12345678-9012-3456-7890-123456789012%7D</LocURI>
                 </Target>
              </Item>
        </delete>
     <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="----packagefamilyname-packagefullname"></a>**.../* PackageFamilyName*/****_PackageFullName_**  
Optional Vollständiger Name des Pakets installiert.

Unterstützte Vorgänge sind Get und löschen.

> **Hinweis**  XAP-Dateien verwenden Product ID anstelle von PackageFullName. Es folgt ein Beispiel der XAP-Produkt-ID (einschließlich der geschweiften Klammern), {12345678-9012-3456-7890-123456789012}.

 

<a href="" id="----packagefamilyname-packagefullname-name"></a>**.../* PackageFamilyName*/*PackageFullName*/Name**  
Erforderlich. Name der app. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-version"></a>**.../* PackageFamilyName*/*PackageFullName*/Version**  
Erforderlich. Version der app. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-publisher"></a>**.../* PackageFamilyName*/*PackageFullName*/Publisher**  
Erforderlich. Publisher-Name der app. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-architecture"></a>**.../* PackageFamilyName*/*PackageFullName*/Architecture**  
Erforderlich. Architektur der installierten Paket. Werttyp ist Zeichenfolge.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-installlocation"></a>**.../* PackageFamilyName*/*PackageFullName*/InstallLocation**  
Erforderlich. Installationsort der app auf dem Gerät. Werttyp ist Zeichenfolge.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-isframework"></a>**.../* PackageFamilyName*/*PackageFullName*/IsFramework**  
Erforderlich. Unabhängig davon, ob die app ein Framework-Paket ist. Werttyp ist int. Der Wert ist 1, wenn die app ein Framework-Paket und den Wert 0 (null) für alle anderen Fälle ist.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-isbundle"></a>**.../* PackageFamilyName*/*PackageFullName*/IsBundle**  
Erforderlich. Der Wert ist 1, wenn das Paket einer app-Paket und 0 (null) für alle anderen Fälle ist. Werttyp ist int.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-installdate"></a>**.../* PackageFamilyName*/*PackageFullName*/InstallDate**  
Erforderlich. Datum, die der Installation der app an. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-resourceid"></a>**.../* PackageFamilyName*/*PackageFullName*/ResourceID**  
Erforderlich. Ressourcen-ID der app. Dies ist null für die Haupt-app, ~ für ein Paket, und enthält Informationen zu Ressourcen für Ressourcen Pakete. Werttyp ist Zeichenfolge.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-packagestatus"></a>**.../* PackageFamilyName*/*PackageFullName*/PackageStatus**  
Erforderlich. Enthält Informationen zu den Status des Pakets. Werttyp ist int. Gültige Werte sind:

-   OK (0) - Paket kann verwendet werden.
-   LicenseIssue (1): die Lizenz des Pakets ist ungültig.
-   Geänderte (2) – die Paket-Nutzlast von einer unbekannten Quelle geändert wurde.
-   Unbefugt geänderten (4) - Paket Nutzlast absichtlich beschädigt war.
-   (8): deaktiviert das Paket ist nicht für die Verwendung verfügbar. Sie können weiterhin verarbeitet werden.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-requiresreinstall"></a>**.../* PackageFamilyName*/*PackageFullName*/RequiresReinstall**  
Erforderlich. Gibt an, ob der Paket Zustand geändert hat und eine Neuinstallation der app erfordert. Dies kann vorkommen, wenn neue app-Ressourcen erforderlich sind, beispielsweise wenn ein Gerät eine Änderung in bevorzugte Sprache oder eine neue DPI hat. Es kann auch Eintreten des Pakets wurde beschädigt. Wenn der Wert 1 ist, wird die Neuinstallation der app durchgeführt. Werttyp ist int.

> **Hinweis**  Gilt nicht für XAP-Dateien.

 

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-users"></a>**.../* PackageFamilyName*/*PackageFullName*/Users**  
Erforderlich. Registrierte Benutzer der app. Wenn die Abfrage auf Device-Ebene ist, wird die registrierte Benutzer das Gerät zurückgegeben. Wenn Sie den Benutzerkontext Abfragen, wird nur den aktuellen Benutzer zurückgegeben. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-packagefullname-isprovisioned"></a>**.../* PackageFamilyName*/*PackageFullName*/IsProvisioned**  
Erforderlich. Der Wert ist 0 oder 1, der angibt, ob die app auf dem Gerät bereitgestellt wird. Der Werttyp ist "int"

Unterstützte Vorgang ist Get.

<a href="" id="----packagefamilyname-donotupdate"></a>* *... /*PackageFamilyName*/DoNotUpdate**  
Erforderlich. Gibt an, ob Sie eine bestimmte app aus, die über automatische Updates aktualisiert blockieren möchten.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="----packagefamilyname-appsettingpolicy---only-for---user-vendor-msft-"></a>* *... /*PackageFamilyName*/AppSettingPolicy** (nur für ./User/Vendor/MSFT)  
In Windows-10, Version 1511 hinzugefügt. Interior-Knoten für alle verwalteten app Festlegen von Werten. Dieser Knoten ist nur im Kontext Benutzers unterstützt.

<a href="" id="----packagefamilyname-appsettingpolicy-settingvalue---only-for---user-vendor-msft-"></a>**.../* PackageFamilyName*/AppSettingPolicy / ***_SettingValue_ * * (nur für ./User/Vendor/MSFT) in Windows 10, Version 1511 hinzugefügt. Die *SettingValue* und Daten darzustellen ein Schlüssel-Wert-Paar für die app konfiguriert werden soll. Der Knoten stellt den Namen des Schlüssels und steht für den Wert der Daten.

Diese Einstellung funktioniert nur für apps, die das Feature unterstützen, und es wird nur im Kontext Benutzers unterstützt.

Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Add, Get-ersetzen, und löschen.

Im folgenden Beispiel wird den Wert für den 'Server'

``` syntax
<!— Configure app settings -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/PackageFamilyName/AppSettingPolicy/Server</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>server1.contoso.com</Data>
   </Item>
</Add>
```

Im folgende Beispiel ruft alle verwalteten app-Einstellungen für eine bestimmte app ab.

``` syntax
<!—Get app settings -->
<Get>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/PackageFamilyName/AppSettingPolicy?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

<a href="" id="appinstallation"></a>**AppInstallation**  
Erforderlicher Knoten. Dient zum app-Installation durchführen.

<a href="" id="appinstallation-packagefamilyname"></a>**AppInstallation / ***_PackageFamilyName_**  
Optionale Knoten. Paket-Produktfamilie Name (PFN) der app. Es ist eine für jede PFN auf dem Gerät beim Inventarberichte. Diese Elemente werden unter ihren Ursprung signierenden zurückgehen.

Unterstützte Vorgänge sind Get und hinzufügen.

> **Hinweis**  XAP-Dateien verwenden Product ID anstelle von PackageFamilyName. Es folgt ein Beispiel der XAP-Produkt-ID (einschließlich der geschweiften Klammern), {12345678-9012-3456-7890-123456789012}.

 

<a href="" id="appinstallation-packagefamilyname-storeinstall"></a>* *AppInstallation /*PackageFamilyName*/StoreInstall**  
Erforderlich. Eine Installation von einer app und eine Lizenz aus dem Windows Store auszuführende Befehl.

Unterstützte Vorgang ist ausführen.

<a href="" id="appinstallation-packagefamilyname-hostedinstall"></a>* *AppInstallation /*PackageFamilyName*/HostedInstall**  
Erforderlich. Der Befehl eine Installation der app-Paket von einem gehosteten Standort ausführen (Dies kann einem lokalen Laufwerk, UNC oder Https-Datenquelle sein).

Unterstützte Vorgang ist ausführen.

<a href="" id="appinstallation-packagefamilyname-lasterror"></a>* *AppInstallation /*PackageFamilyName*/LastError**  
Erforderlich. Letzter Fehler im Zusammenhang mit der Installation der app.

Unterstützte Vorgang ist Get.

> **Hinweis**  Dieses Element ist nicht vorhanden, nachdem die app installiert ist.

 

<a href="" id="appinstallation-packagefamilyname-lasterrordescription"></a>* *AppInstallation /*PackageFamilyName*/LastErrorDescription**  
Erforderlich. Beschreibung des letzten Fehlers im Zusammenhang mit der app-Installation.

Unterstützte Vorgang ist Get.

> **Hinweis**  Dieses Element ist nicht vorhanden, nachdem die app installiert ist.

 

<a href="" id="appinstallation-packagefamilyname-status"></a>* *AppInstallation /*PackageFamilyName*/Status**  
Erforderlich. Status der app-Installation. Die folgenden Werte werden zurückgegeben:

-   NICHT\_INSTALLED (0) – der Knoten wurde hinzugefügt, jedoch die Ausführung noch nicht abgeschlossen.
-   Installieren VON (1) - Ausführung wurde gestartet, aber die Bereitstellung nicht abgeschlossen. Wenn die Bereitstellung unabhängig davon erfolgreich abgeschlossen wird, wird dieser Wert aktualisiert.
-   FEHLER (2) – Fehler bei der Installation. Die Details des Fehlers können unter LastError und LastErrorDescription gefunden werden.
-   (3) - INSTALLED nach eine Installation erfolgreich ist dieser Knoten wird bereinigt, jedoch in der Ereignisprozedur Bereinigen Aktion nicht abgeschlossen wurde, derselbe Status kurz angezeigt werden soll.

Unterstützte Vorgang ist Get.

> **Hinweis**  Dieses Element ist nicht vorhanden, sobald die app installiert ist.

 

<a href="" id="appinstallation-packagefamilyname-progessstatus"></a>* *AppInstallation /*PackageFamilyName*/ProgessStatus**  
Erforderlich. Eine ganze Zahl der gibt den Fortschritt der app-Installation. Für Https-Speicherorte bedeutet dies den Downloadstatus an. ProgressStatus ist nicht verfügbar für die Bereitstellung, und es ist nur für benutzerbasierte Installationen. Bei der Bereitstellung, der Wert ist immer 0 (null).

Unterstützte Vorgang ist Get.

> **Hinweis**  Dieses Element ist nicht vorhanden, sobald die app installiert ist.

 

<a href="" id="applicenses"></a>**AppLicenses**  
Erforderlicher Knoten. Zum Verwalten von Lizenzen für app-Szenarien.

<a href="" id="applicenses-storelicenses"></a>**AppLicenses/StoreLicenses**  
Erforderlicher Knoten. Zum Verwalten von Lizenzen für Store-apps.

<a href="" id="applicenses-storelicenses-licenseid"></a>**AppLicenses/StoreLicenses / ***_LicenseID_**  
Optionale Knoten. Lizenz-ID für einen Speicher installiert app. Die Lizenz-ID ist im Allgemeinen der PFN der app.

Unterstützte Vorgänge sind Add, Get und löschen.

<a href="" id="applicenses-storelicenses-licenseid-licensecategory"></a>* *AppLicenses/StoreLicenses/*LicenseID*/LicenseCategory**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Kategorie der Lizenz, die zum Klassifizieren von verschiedenen Lizenz Quellen verwendet wird. Gültige Wert:

-   Unbekannt - unbekannte Lizenzkategorie
-   Verkauft Retail - Lizenz Einzelhandel in der Regel aus dem Windows Store
-   Enterprise - Lizenz verkauft über die Enterprise sales-Kanal, in der Regel aus dem Speicher für Unternehmen
-   OEM - Lizenz ausgestellt für OEM
-   Entwickler - Entwicklerlizenz, in der Regel während des app-Entwicklung oder Seite laden Scernarios installiert.

Unterstützte Vorgang ist Get.

<a href="" id="applicenses-storelicenses-licenseid-licenseusage"></a>* *AppLicenses/StoreLicenses/*LicenseID*/LicenseUsage**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Gibt die zulässige Verwendung für die Lizenz an. Gültige Werte:

-   Unbekannt - Verwendung ist unbekannt
-   Online - ist nur die Lizenz für online Usage gültig. Dies ist für Anwendungen mit Anforderungen an die Übereinstimmung wie eine app auf mehreren Computern verwendet werden, jedoch nur auf einem zu einem bestimmten Zeitpunkt verwendet werden kann.
-   Offline - ist die Lizenz für die Offlineverwendung gültig. Eine Verbindung mit dem Internet verwenden diese Lizenz ist nicht erforderlich.
-   Enterprise-Stamm-

Unterstützte Vorgang ist Get.

<a href="" id="applicenses-storelicenses-licenseid-requesterid"></a>* *AppLicenses/StoreLicenses/*LicenseID*/RequesterID**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Der Bezeichner für die Entität, die die Lizenz, beispielsweise der Client angefordert haben, die die Lizenz erworben. Beispielsweise alle Lizenzen des Speichers für die Business für einen bestimmten Enterprise Client einstufen der gleichen RequesterID hat.

Unterstützte Vorgang ist Get.

<a href="" id="applicenses-storelicenses-licenseid-addlicense"></a>* *AppLicenses/StoreLicenses/*LicenseID*/AddLicense**  
Erforderlich. Der Befehl Lizenz hinzuzufügen.

Unterstützte Vorgang ist ausführen.

<a href="" id="applicenses-storelicenses-licenseid-getlicensefromstore"></a>* *AppLicenses/StoreLicenses/*LicenseID*/GetLicenseFromStore**  
In Windows-10, Version 1511 hinzugefügt. Erforderlich. Befehl aus, um die Lizenz aus dem Speicher abzurufen.

Unterstützte Vorgang ist ausführen.

## <a name="examples"></a>Beispiele


Beispiele für die Verwendung dieser CSP, für reporting apps Inventar, Installation und Deinstallation von apps für Benutzer apps auf Geräten bereitstellen und Verwalten von app-Lizenzen finden Sie unter [Enterprise-app-Verwaltung](enterprise-app-management.md).

Das Gerät für eine bestimmte app Unterkategorie, wie etwa NonStore apps Abfragen.

``` syntax
<Get>
  <CmdID>1</CmdID>
  <Item>
    <Target>
      <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore</LocURI>
    </Target>
  </Item>
</Get>
```

Das Ergebnis enthält eine Liste von apps, z. B. &lt;Daten&gt;App1/App2/App3&lt;Vorlagendateien&gt;.

Nachfolgende Abfrage für eine bestimmte app für seine Eigenschaften.

``` syntax
  
<Get>
   <CmdID>1</CmdID>
   <Item>
     <Target>
       <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore/App1?list=StructData</LocURI>
     </Target>
   </Item>
</Get>
<Get>
  <CmdID>2</CmdID>
  <Item>
    <Target>
      <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore/App2?list=StructData</LocURI>
    </Target>
  </Item>
</Get>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






