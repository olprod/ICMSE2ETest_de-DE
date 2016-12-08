---
title: Enterprise-app-Verwaltung
description: "In diesem Thema wird eine der wichtigsten mobiles Gerät (MDM) Verwaltungsfeatures in Windows 10 für die Verwaltung des Lebenszyklus von apps in allen Windows behandelt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 225DEE61-C3E3-4F75-BC79-5068759DFE99
ms.openlocfilehash: 5c03726ec42d32da29cfbd6d4bd0a03e077a191f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprise-app-management"></a>Enterprise-app-Verwaltung

In diesem Thema wird eine der wichtigsten Mobilgerät (MDM) Verwaltungsfeatures in Windows 10 für die Verwaltung des Lebenszyklus von apps in allen Windows behandelt. Es ist die Möglichkeit, Speicher und nicht-Store-apps als Teil der systemeigenen Funktionen von MDM verwalten. Neue ist in Windows 10 die Möglichkeit, Bestandsaufnahme der alle Ihre apps übernehmen.

## <a name="application-management-goals"></a>Application Management Ziele

Windows-10 bietet die Möglichkeit für Verwaltungsserver an:

-   Installieren von apps direkt aus dem Windows Store for Business
-   Bereitstellen von offline Store- und Lizenzen
-   Bereitstellen von Line-of-Business (LOB) apps (nicht-Store-apps)
-   Bestandsaufnahme alle apps für einen Benutzer (Store und nicht-Store-apps)
-   Bestandsaufnahme alle apps für ein Gerät (Store und nicht-Store-apps)
-   Deinstallieren Sie alle apps für einen Benutzer (Store und nicht-Store-apps)
-   Bereitstellen von apps, sodass sie für alle Benutzer von einem Gerät unter Windows 10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) installiert werden
-   Entfernen der bereitgestellten app auf dem Gerät, auf dem Windows-10 für desktop-Editionen

## <a name="inventory-your-apps"></a>Bestandsaufnahme Ihrer apps

Windows-10 können Sie die Bestandsaufnahme alle apps, die für einen Benutzer und alle apps für alle Benutzer eines Geräts auf Windows-10 für desktop Edition bereitgestellt. Der [EnterpriseModernAppManagement](enterprisemodernappmanagement-csp.md) Konfiguration-Dienstanbieter (CSP) inventarisiert gepackte apps und enthält keinen herkömmlichen Win32 apps über MSI oder ausführbare Dateien installiert. Wenn die apps inventarisierten sind werden basierend auf der folgenden Klassifikationen in der app getrennt:

-   Store - Apps, die aus dem Windows Store sind. Apps direkt aus dem Speicher installiert oder im Lieferumfang des Unternehmens aus dem Speicher für Unternehmen
-   NonStore - Apps, die nicht aus dem Windows Store erworben wurden.
-   System - Apps, die Teil des Betriebssystems sind. Diese apps kann nicht deinstalliert werden. Diese Klassifizierung ist schreibgeschützt und kann nur inventarisierten sein.

Diese Klassifikationen werden als Knoten im EnterpriseModernAppManagement CSP dargestellt.

Das folgende Diagramm zeigt die EnterpriseModernAppManagement CSP in einer Struktur.

![Enterprisemodernappmanagement Csp Diagramm](images/provisioning-csp-enterprisemodernappmanagement.png)![Enterprisemodernappmanagement Csp Diagramm](images/provisioning-csp-enterprisemodernappmanagement2.png)

Jeder app werden einem einzelnen Paket-Produktfamilie Name und vollständiger Namen von 1-n-Paket für installierte apps angezeigt. Die apps werden basierend auf ihren Ursprung (Store, NonStore System) kategorisiert.

Inventar kann ausgeführten rekursiv auf jeder Ebene aus dem AppManagement Knoten über das Paket vollständiger Name sein. Inventar kann auch nur für eine bestimmte Inventar-Attribut ausgeführt werden.

Inventar ist speziell für das Paket vollständiger Name und Listen gebündelt Sprachpaketen und Ressourcen Packs gegebenenfalls unter dem Namen der Paket-Familie.

> **Hinweis**  Unter Windows Mobile 10 haben XAP-Pakete die Produkt-ID an der Stelle Paket-Produktfamilie Name und Vollständiger Paketname.

 
Hier sind die Knoten für den vollständigen Namen jedes Paket:

-   Name
-   Version
-   Herausgeber
-   Architektur
-   InstallLocation
-   IsFramework
-   IsBundle
-   InstallDate
-   ResourceID
-   RequiresReinstall
-   PackageStatus
-   Benutzer
-   IsProvisioned

Eine ausführliche Beschreibung der einzelnen Knoten finden Sie unter [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md).

### <a name="app-inventory"></a>App-Inventar

Sie können EnterpriseModernAppManagement CSP, die Abfrage für alle apps, die für einen Benutzer oder Gerät installiert. Die Abfrage gibt alle apps unabhängig davon zurück, wenn sie über die MDM oder anderen Methoden installiert wurden. Inventar kann auf Benutzer oder Geräteebene ausgeführt werden. Inventar auf Device-Ebene werden Informationen für alle Benutzer auf dem Gerät zurückgegeben.

Beachten Sie, dass Durchführen einer vollständigen Inventur eines Geräts kann ressourcenintensiv auf dem Client basierend auf der Hardware und der Anzahl von apps, die installiert werden. Die zurückgegebenen Daten können auch sehr groß sein. Sie möchten diese Anforderungen an die Auswirkung auf Clients und den Netzwerkverkehr zu reduzieren aufteilen.

Es folgt ein Beispiel einer Abfrage für alle apps auf dem Gerät.

``` syntax
<!-- Get all apps under AppManagement -->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

Es folgt ein Beispiel einer Abfrage für eine bestimmte app für einen Benutzer.

``` syntax
<!-- Get all information of a specific app for a user -->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

### <a name="store-license-inventory"></a>Lizenz-Shop

Sie können EnterpriseModernAppManagement CSP, die Abfrage für alle app-Lizenzen für einen Benutzer oder Gerät installiert. Die Abfrage gibt alle app-Lizenzen unabhängig davon zurück, wenn sie über die MDM oder anderen Methoden installiert wurden. Inventar kann auf Benutzer oder Geräteebene ausgeführt werden. Inventar auf Device-Ebene werden Informationen für alle Benutzer auf dem Gerät zurückgegeben.

Hier sind die Knoten für jede Lizenz-ID:

-   LicenseCategory
-   LicenseUsage
-   RequestedID

Eine ausführliche Beschreibung der einzelnen Knoten finden Sie unter [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md).

> **Hinweis**  Die LicenseID im CSP ist die Inhalts-ID für die Lizenz.


Es folgt ein Beispiel einer Abfrage für alle app-Lizenzen auf einem Gerät.

``` syntax
<!-- Get all app licenses for the device -->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppLicenses/StoreLicenses?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

Es folgt ein Beispiel einer Abfrage für alle app-Lizenzen für einen Benutzer.

``` syntax
<!-- Get a specific app license for a user -->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppLicenses/StoreLicenses/{license id}?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

## <a name="enable-the-device-to-install-non-store-apps"></a>Aktivieren Sie das Gerät nicht Store-apps installieren

Es gibt zwei grundlegende Arten von apps, die Sie bereitstellen können: Store-apps und Enterprise apps signiert. Zum Bereitstellen von Enterprise signiert-apps müssen Sie eine Einstellung auf dem Gerät, um vertrauenswürdige apps zulassen aktivieren. Apps können von einem Microsoft genehmigt-Stamm (wie Symantec) angemeldet sein, ein Unternehmens bereitgestellt, Stamm- oder apps, die selbstsignierten sind. In diesem Abschnitt werden die Schritte zum Konfigurieren des Geräts für die Bereitstellung nicht Store-app behandelt.

### <a name="unlock-the-device-for-non-store-apps"></a>Entsperren Sie das Gerät für nicht-Store-apps

Zum Bereitstellen von app, die nicht aus dem Windows Store sind, müssen Sie die Richtlinie ApplicationManagement/AllowAllTrustedApps konfigurieren. Diese Richtlinie ermöglicht die Installation von nicht-Store-apps auf dem Gerät, vorausgesetzt, dass eine Kette an ein Zertifikat auf dem Gerät vorhanden ist. Die app kann mit einem Stammzertifikat auf dem Gerät (beispielsweise Symantec Enterprise), ein Stammzertifikat für Unternehmen Besitzer oder ein Zertifikat für den Bericht über Peer-Vertrauensstellung auf dem Gerät bereitgestellten signiert werden. Weitere Informationen zum Bereitstellen von Benutzerlizenz finden Sie unter [Bereitstellen einer offline-Lizenz für einen Benutzer](#deploy-an-offline-license-to-a-user).

Die Richtlinie AllowAllTrustedApps ermöglicht die Installation-apps, die durch ein Zertifikat im vertrauenswürdigen Personen auf dem Gerät oder ein Stammzertifikat in der vertrauenswürdigen Stammzertifizierungsstellen des Geräts als vertrauenswürdig eingestuft werden. Die Richtlinie ist nicht standardmäßig konfiguriert, was bedeutet, dass nur apps aus dem Windows Store installiert werden können. Wenn der Verwaltungsserver implizit den Wert OFF festgelegt wird, wird die Einstellung in der Systemsteuerung Einstellungen auf dem Gerät deaktiviert.

Weitere Informationen über die Richtlinie AllowAllTrustedApps finden Sie unter [CSP Richtlinie](policy-configuration-service-provider.md).

Es folgen einige Beispiele.

``` syntax
<!-- Get policy (Default)-->
<Get>
  <CmdID>1</CmdID>
  <Item>
    <Target>
      <LocURI>./Vendor/MSFT/Policy/Result/ApplicationManagement/AllowAllTrustedApps?list=StructData</LocURI>
    </Target>
    </Item>
</Get>
<!-- Update policy -->
<Replace>
  <CmdID>2</CmdID>
  <Item>
    <Target>                        
      <LocURI>./Vendor/MSFT/Policy/Config/ApplicationManagement/AllowAllTrustedApps</LocURI>
    </Target>
    <Meta> 
      <Format>int</Format> 
      <Type>text/plain</Type> 
    </Meta> 
    <Data>1</Data>                        
  </Item>
</Replace>
```

### <a name="unlock-the-device-for-developer-mode"></a>Entsperren Sie das Gerät zum Entwicklermodus

Entwicklung von apps auf Windows-10 nicht mehr ist eine spezielle Lizenz erforderlich. Aktivieren Sie das Debuggen und die Bereitstellung von nicht gepackt apps in Richtlinie CSP ApplicationManagement/AllowDeveloperUnlock Richtlinie verwenden.

AllowDeveloperUnlock Richtlinie ermöglicht den Entwicklungsmodus auf dem Gerät. Die AllowDeveloperUnlock ist nicht in der Standardeinstellung konfiguriert bedeutet, dass nur Windows Store-apps installiert werden können. Wenn der Verwaltungsserver explizit den Wert OFF festgelegt wird, wird die Einstellung in der Systemsteuerung Einstellungen auf dem Gerät deaktiviert.

Bereitstellung von apps für Windows 10 für desktop Edition erfordert, dass eine Kette an ein Zertifikat auf dem Gerät vorhanden ist. Die app kann mit einem Stammzertifikat auf dem Gerät (beispielsweise Symantec Enterprise), ein Stammzertifikat für Unternehmen Besitzer oder ein Zertifikat für den Bericht über Peer-Vertrauensstellung auf dem Gerät bereitgestellten signiert werden. Bereitstellung auf Windows 10 Mobile überprüft nicht, ob der Store-eine gültige vertrauenswürdige Stammzertifizierungsstelle auf dem Gerät verfügen.

Weitere Informationen über die Richtlinie AllowDeveloperUnlock finden Sie unter [Richtlinie CSP](policy-configuration-service-provider.md).

Es folgt ein Beispiel.

``` syntax
<!-- Get policy (Default)-->
<Get>
  <CmdID>1</CmdID>
  <Item>
    <Target>
      <LocURI>./Vendor/MSFT/Policy/Result/ApplicationManagement/AllowDeveloperUnlock?list=StructData</LocURI>
    </Target>
  </Item>
</Get>
<!-- Update policy -->
<Replace>
  <CmdID>2</CmdID>
  <Item>
    <Target>                  
      <LocURI>./Vendor/MSFT/Policy/Config/ApplicationManagement/AllowDeveloperUnlock</LocURI>
    </Target>
    <Meta> 
      <Format>int</Format> 
      <Type>text/plain</Type> 
    </Meta> 
    <Data>1</Data>                        
  </Item>
</Replace>
```

## <a name="install-your-apps"></a>Installieren Sie Ihre apps

Sie können apps für einen bestimmten Benutzer oder für alle Benutzer eines Geräts installieren. Apps werden direkt aus dem Windows Store oder in einigen Fällen von einem Hostspeicherort, beispielsweise einen lokalen Datenträger, UNC-Pfad oder HTTPS-Speicherort installiert. Verwenden Sie den Knoten AppInstallation [EnterpriseModernAppManagement CSP](enterprisemodernappmanagement-csp.md) , um apps zu installieren.

### <a name="deploy-apps-to-user-from-the-store"></a>Bereitstellen von apps für Benutzer aus dem Speicher

Zum Bereitstellen einer app, die einem Benutzer direkt aus dem Windows Store führt der Verwaltungsserver eine Befehle hinzufügen und Exec auf dem AppInstallation Knoten des EnterpriseModernAppManagement CSP. Dies ist nur im Kontext Benutzers unterstützt und im Gerätekontext nicht unterstützt.

Wenn Erwerb einer app aus dem Speicher für Unternehmen und die app für eine online-Lizenz angegeben ist, müssen der app und die Lizenz direkt aus dem Windows Store erworben werden.

Hier sind die Anforderungen für dieses Szenario:

-   Die app wird ein Benutzer Azure Active Directory (AAD) Identität in den Speicher für Unternehmen zugewiesen. Sie können diese direkt im Speicher für Unternehmen oder über einen Verwaltungsserver Schritte durchführen.
-   Das Gerät ist eine Verbindung an den Windows Store.
-   Windows Store-Dienste müssen auf dem Gerät aktiviert sein. Beachten Sie, dass die Windows Store-Benutzeroberfläche durch den Enterprise-Administrator deaktiviert werden kann
-   Der Benutzer muss sich mit ihren AAD Identität signiert werden.

Es folgen einige Beispiele.

``` syntax
<Exec>
   <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/StoreInstall</LocURI>
            </Target>
            <Meta>
                <Format xmlns="syncml:metinf">xml</Format>
            </Meta>
            <Data><Application id="{ProductID}" flags="0" skuid=" "/></Data>
          </Item>
</Exec>
```

Hier sind die Änderungen aus der vorherigen Version:

1.  Der Verweis "{CatID}" muss auf "{ProductID}" aktualisiert werden. Dieser Wert wird als Teil des Speichers für die Business-Verwaltungstool erworben.
2.  Der Wert für Flags kann "0" oder "1" sein.

    Bei Verwendung von "0" Ruft das Verwaltungstool zurück an den Store für Business Sync einem Benutzer einen Sitz einer Anwendung zuweisen. Bei Verwendung von "1" ist das Verwaltungstool nicht wieder des Speichers für Unternehmen Sync zuweisen einem Benutzers einen Sitz einer Anwendung anrufen. Der Kryptografiedienstanbieter wird einen Sitz geltend, sofern verfügbar.

3.  Die Skuid ist ein neuer Parameter, der erforderlich ist. Dieser Wert wird als Teil des Speichers für die Business Management Tool synchronisieren erworben.

### <a name="deploy-an-offline-license-to-a-user"></a>Bereitstellen einer offline-Lizenzvertrags für einen Benutzer

Wenn Sie eine app aus dem Speicher für Unternehmen erworben haben, muss auf dem Gerät die app-Lizenz bereitgestellt werden.

Die app-Lizenz muss nur im Rahmen der ersten Installation der app bereitgestellt werden. Während einer Aktualisierung wird dem Benutzer nur die app bereitgestellt.

In der SyncML müssen Sie die folgende Informationen in den Befehl Exec angeben:

-   Lizenzieren von ID - dies in der LocURI angegeben ist. Die Lizenz-ID für die offline-Lizenz wird als "Content-ID" in der Lizenzdatei bezeichnet. Sie können diese Informationen aus dem Base64-codierten Lizenz herunterladen aus dem Speicher für Business abrufen.
-   Lizenzieren von Inhalten – dies im Datenabschnitt angegeben wird. Die Lizenz Inhalt ist die Base64-codierte Blob der Lizenz.

Es folgt ein Beispiel einer offline-Lizenz-Installation.

``` syntax
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>          
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppLicenses/StoreLicenses/{LicenseID}/AddLicense</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">xml</Format>
      </Meta>
      <Data><License Content="{LicenseBlob}"></Data>
   </Item>
</Exec>
```

<a href="" id="deploy-from-hosted-loc"></a>
### <a name="deploy-apps-to-a-user-from-a-hosted-location"></a>Bereitstellen von apps, die einem Benutzer von einem gehosteten Standort

Erwerb einer app aus dem Speicher für Unternehmen und die app für eine offline-Lizenz angegeben ist, oder die app ist eine nicht-Store-app, muss die app von einem gehosteten Standort bereitgestellt werden.

Hier sind die Anforderungen für dieses Szenario:

-   Der Speicherort der app kann einen lokalen Dateisystem sein (C:\\StagedApps\\app1.appx), einem UNC-Pfad (\\\\Server\\freigeben\\app1.apx), oder einen HTTPS-Speicherort (https://contoso.com/app1.appx\_
-   Der Benutzer muss der Inhaltsspeicherort Zugriffsberechtigung für. Für HTTPs können Sie Server-Authentifizierung oder Zertifikatauthentifizierung mithilfe einer der Registrierung zugeordnete Zertifikat. HTTP-Adressen werden unterstützt, jedoch nicht empfohlen, aufgrund fehlender Anforderungen für die Authentifizierung.
-   Das Gerät muss nicht Konnektivität mit Windows Store Informationsspeicher-Dienste haben oder die ist die Windows speichern Benutzeroberfläche, die aktiviert werden.
-   Muss der Benutzer angemeldet sein, jedoch Zuordnung mit AAD Identität ist nicht erforderlich.

> **Hinweis**  Sie müssen das Gerät zum Bereitstellen von apps NonStore entsperren oder müssen Sie die app-Lizenz vor der Bereitstellung von offline-apps bereitstellen. Weitere Informationen hierzu finden Sie unter [Deploy eine offline-Lizenz für einen Benutzer](#deploy-an-offline-license-to-a-user).

 
Der Befehl hinzufügen, für den Paketnamen Familie ist erforderlich, um sicherzustellen, dass ordnungsgemäße zum Entfernen der app am Unenrollment.

Es folgt ein Beispiel einer Line-of-Business-app-Installation.

``` syntax
<!-- Add PackageFamilyName -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}</LocURI>
      </Target>
   </Item>
</Add> 
<!-- Install appx -->
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/HostedInstall</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">xml</Format>
      </Meta>
      <Data><Application PackageUri="\\server\share\HelloWorld10.appx" /></Data>
   </Item>
</Exec>
```

Es folgt ein Beispiel einer app-Installation mit Abhängigkeiten.

``` syntax
<!-- Add PackageFamilyName -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName</LocURI>
      </Target>
   </Item>
</Add> 
<!-- Install appx with deployment options and framework dependencies-->
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/HostedInstall</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">xml</Format>
      </Meta>
      <Data>
         <Application PackageUri="\\server\share\HelloWorld10.appx" DeploymentOptions="0" >
            <Dependencies>
                      <Dependency PackageUri=”\\server\share\HelloWorldFramework.appx” />
                <Dependency PackageUri=”\\server2\share\HelloMarsFramework.appx” />
            </Dependencies>
        </Application>
      </Data>
   </Item>
</Exec>
```

### <a name="provision-apps-for-all-users-of-a-device"></a>Bereitstellung von apps für alle Benutzer eines Geräts

Bereitstellung können Sie Phase die app auf das Gerät, und alle Benutzer des Geräts können die app auf ihren nächsten Anmeldung registriert haben. Dies wird nur unterstützt, für die app aus dem Speicher für Unternehmen erworben und die app für eine offline-Lizenz angegeben ist oder die app ist eine nicht-Store-app. Die app muss von einem Speicherort gehosteten angeboten werden. Die app ist als lokales System installiert. Um in einer lokalen Dateifreigabe installieren, muss das "lokale System" des Geräts auf die Freigabe zugreifen.

Hier sind die Anforderungen für dieses Szenario:

-   Der Speicherort der app kann der lokalen Dateisystem sein (C:\\StagedApps\\app1.appx), einem UNC-Pfad (\\\\Server\\freigeben\\app1.apx), oder einen HTTPS-Speicherort (https://contoso.com/app1.appx\_
-   Der Benutzer muss über die Berechtigung zum der Inhaltsspeicherort zugreifen. Für HTTPs können Sie Server-Authentifizierung oder mit einem Zertifikat, das der Registrierung zugeordnet Zertifikatauthentifizierung verwenden. HTTP-Adressen werden unterstützt, jedoch nicht empfohlen, aufgrund fehlender Anforderungen für die Authentifizierung.
-   Das Gerät muss nicht Connectivity an den Windows Store haben oder aktivierten Dienste gespeichert werden.
-   Das Gerät ist eine beliebige AAD Identität oder die Domänenmitgliedschaft nicht erforderlich.
-   Für NonStore-app muss Ihr Gerät aufgehoben werden.
-   Für offline Store-apps müssen die erforderlichen Lizenzen vor der Bereitstellung von apps bereitgestellt werden.

Um die app für alle Benutzer eines Geräts von einem gehosteten Standort bereitstellen möchten, führt der Verwaltungsserver einen Befehl hinzufügen und Exec auf den Knoten AppInstallation im Gerätekontext. Der Befehl hinzufügen, für den Paketnamen Familie ist erforderlich, um sicherzustellen, dass ordnungsgemäße Entfernen der app am Unenrollment.

> **Hinweis**  Wenn Sie die bereitgestellte app entfernen, wird es nicht von den Benutzern entfernt, die die app bereits installiert.

 

Es folgt ein Beispiel des app-Installation.

> **Hinweis**  Dies ist nur für desktop-Editionen in Windows 10 unterstützt.


``` syntax
<!-- Add PackageFamilyName -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName</LocURI>
      </Target>
   </Item>
</Add> 
<!-- Provision appx to device -->
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/HostedInstall</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">xml</Format>
      </Meta>
      <Data><Application PackageUri="\\server\share\HelloWorld10.appx" /></Data>
   </Item>
</Exec>
```

Der Befehl HostedInstall Exec enthält einen Datenknoten, der eine eingebettete XML-DATEI benötigt. Hier sind die Anforderungen für die XML-Daten:

-   Knoten Application ist einen erforderlichen Parameter, PackageURI an, der einen lokalen Dateispeicherort UNC; sein kann oder HTTPs-Speicherort.
-   Abhängigkeiten angegeben werden können, falls erforderlich, um mit dem Paket installiert werden. Dieser Schritt ist optional.

Der Parameter DeploymentOptions ist nur im Kontext Benutzers verfügbar.

Es folgt ein Beispiel des app-Installation mit Abhängigkeiten.

> **Hinweis**  Dies ist nur für desktop-Editionen in Windows 10 unterstützt.


``` syntax
<!-- Add PackageFamilyName -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName</LocURI>
      </Target>
   </Item>
</Add> 
<!-- Provision appx with framework dependencies-->
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/HostedInstall</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">xml</Format>
      </Meta>
      <Data>
         <Application PackageUri="\\server\share\HelloWorld10.appx" />
            <Dependencies>
                     <Dependency PackageUri=”\\server\share\HelloWorldFramework.appx” />
               <Dependency PackageUri="\\server2\share\HelloMarsFramework.appx"/>
            </Dependencies>
         </Application>
      </Data>
   </Item>
</Exec>
```

### <a name="get-status-of-app-installations"></a>Abrufen des Status der app-Installationen

Wenn eine app-Installation abgeschlossen ist, wird eine Windows-Benachrichtigung gesendet. Sie können auch den Status der mithilfe des Knotens AppInstallation Abfragen. Hier wird die Liste der Informationen, die Sie in der Abfrage erhalten können:

-   Status – zeigt den Status der app-Installation.
    -   NICHT\_INSTALLED (0) – der Knoten wurde hinzugefügt, aber die Ausführung wurde nicht abgeschlossen.
    -   Installieren VON (1) - Ausführung wurde gestartet, aber die Bereitstellung nicht abgeschlossen. Wenn die Bereitstellung abgeschlossen, unabhängig davon Suceess ist wird dieser Wert aktualisiert.
    -   FEHLER (2) – Fehler bei der Installation. Die Details des Fehlers können unter LastError und LastErrorDescription gefunden werden.
    -   (3) - INSTALLED nach eine Installation erfolgreich ist dieser Knoten wird bereinigt, jedoch in der Ereignisprozedur Bereinigen Actio nicht abgeschlossen wurde, derselbe Status kurz angezeigt werden soll.
-   LastError - ist dies die letzte der app-Server-Bereitstellung meldet einen Fehler.
-   LastErrorDescription – beschreibt den letzten Fehler gemeldet vom Server app-Bereitstellung.
-   Status – ist dies eine ganze Zahl, die den Fortschritt der app-Installation angibt. In Fällen einen Https-Standort wird den geschätzte Downloadstatus.

    Status ist nicht verfügbar für die Bereitstellung und nur für benutzerbasierte Installationen verwendet. Für die Bereitstellung, ist der Wert immer 0.

Wenn eine app erfolgreich installiert ist, ist der Knoten bereinigt, nach oben und nicht mehr vorhanden. Der Status der app kann unter dem Knoten AppManagement angezeigt werden.

Es folgt ein Beispiel einer Abfrage für eine bestimmte app-Installation.

``` syntax
<!-- Get all app status under AppInstallation for a specific app-->
<Get>
   <CmdID>2</CmdID>
   <Item>
      <Target>    
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

Es folgt ein Beispiel einer Abfrage für alle app-Installationen.

``` syntax
<!-- Get all app status under AppInstallation-->
<Get>
   <CmdID>2</CmdID>
   <Item>
      <Target>    
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

### <a name="alert-for-installation-completion"></a>Benachrichtigung für den Abschluss der installation

Anwendungsinstallationen können einige Zeit in Anspruch nehmen, daher sie erfolgt asynchron. Wenn der Befehl Exec abgeschlossen ist, sendet der Client eine Benachrichtigung an den Verwaltungsserver mit dem Status, ob es sich bei einem Fehler oder Erfolg ist.

Es folgt ein Beispiel einer Warnung.

``` syntax
<Alert>
    <CmdID>4</CmdID>
    <Data>1226</Data>
        <Item>
            <Source>
                <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/{PackageFamilyName}/HostedInstall</LocURI> 
            </Source>
            <Meta>
                <Type xmlns="syncml:metinf">Reversed-Domain-Name:com.microsoft.mdm.EnterpriseHostedAppInstall.result</Type>
                <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>0</Data>
        </Item>
</Alert>
```

Verwenden Sie für Benutzer-basierte Installation die. / Pfad und verwenden Sie für die Bereitstellung von apps, die. / Gerätepfad.

Der Wert des Felds Daten 0 (null) gibt Erfolg, andernfalls handelt es sich um ein Fehlercode. Wenn ein Fehler vorliegt, können Sie weitere Details aus dem Knoten AppInstallation abrufen.

> **Hinweis**  Zu diesem Zeitpunkt ist die Benachrichtigung für die Installation von Store-app noch nicht verfügbar.


## <a name="uninstall-your-apps"></a>Deinstallieren Sie Ihre apps

Sie können apps von Benutzern an Windows 10 Geräte deinstallieren. Um eine app zu deinstallieren, löschen Sie es aus dem AppManagement Knoten der CSP. Innerhalb des Knotens AppManagement werden Pakete basierend auf ihren Ursprung gemäß der folgenden Knoten organisiert:

-   AppStore - sind diese apps für den Windows Store. Apps können direkt aus dem Speicher installiert oder des Unternehmens aus dem Speicher für Unternehmen übermittelt werden.
-   NonStore – diese apps, die nicht aus dem Windows Store erworben wurden.
-   System - diese apps sind Teil des Betriebssystems. Diese apps kann nicht deinstalliert werden.

Um eine app zu deinstallieren, löschen Sie es unter der Origin-Knoten, -Produktfamilie Paketname und vollständige Paketname. Verwenden Sie zum Deinstallieren eines XAP die Produkt-ID anstelle der Paket-Produktfamilie Nane und des vollständigen Namens Paket.

Es folgt ein Beispiel für die Deinstallation aller Versionen einer App für einen Benutzer.

``` syntax
<!-- Uninstall App for a Package Family-->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}</LocURI>
      </Target>
   </Item>
</Delete>
```

Es folgt ein Beispiel für eine bestimmte Version der app für einen Benutzer zu deinstallieren.

``` syntax
<!-- Uninstall App for a specific package full name-->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}/{PackageFullName}</LocURI>
      </Target>
   </Item>
</Delete>
```

### <a name="removed-provisioned-apps-from-a-device"></a>Bereitgestellte apps entfernt aus einem Gerät

Sie können von einem Gerät für eine bestimmte Version oder für alle Versionen des Paket-Produktfamilie bereitgestellte apps entfernen. Wenn eine bereitgestellte app entfernt wird, ist es nicht für zukünftige Benutzer für das Gerät verfügbar. Angemeldete Benutzer, der die app registriert hat sie weiterhin den Zugriff auf die app. Wenn die app für diese Benutzer entfernt werden soll, müssen Sie die app für diese Benutzer explizit deinstallieren.

> **Hinweis**  Sie können nur Entfernen einer app mit dem Inventar Wert IsProvisioned = 1.

 
Entfernen von bereitgestellten app tritt auf, im Gerätekontext.

Es folgt ein Beispiel zum Entfernen einer bereitgestellten app von einem Gerät aus.

``` syntax
<!— Remove Provisioned App for a Package Family-->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}</LocURI>
      </Target>
   </Item>
</Delete>
```

Es folgt ein Beispiel für eine bestimmte Version einer bereitgestellten App von einem Gerät entfernen:

``` syntax
<!-- Remove Provisioned App for a specific package full name-->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}/{PackageFullName}</LocURI>
      </Target>
   </Item>
</Delete>
```

### <a name="remove-a-store-app-license"></a>Entfernen Sie eine Store-app-Lizenz

Sie können app-Lizenzen von einem Gerät pro app basierend auf der Content-ID entfernen.

Es folgt ein Beispiel für das Entfernen einer app-Lizenzvertrags für einen Benutzer.

``` syntax
<!-- Remove App License for a User-->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppLicenses/StoreLicenses/{license id}</LocURI>
      </Target>
   </Item>
</Delete>
```

Es folgt ein Beispiel für das Entfernen einer app-Lizenzvertrags für ein bereitgestellten Paket (Gerätekontext).

``` syntax
<!-- Remove App License for a provisioned package (device) -->
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppLicenses/StoreLicenses/{license id}</LocURI>
      </Target>
   </Item>
</Delete>
```

### <a name="alert-for-app-uninstallation"></a>Benachrichtigung über app-Deinstallation

Deinstallation einer App dauert einige Zeit abgeschlossen ist, wird daher die Deinstallation asynchron ausgeführt wird. Wenn der Befehl Exec abgeschlossen ist, sendet der Client eine Benachrichtigung an den Verwaltungsserver mit dem Status, ob es sich bei einem Fehler oder Erfolg ist.

Verwenden Sie für die benutzerbasierte Deinstallation. / Benutzer in der LocURI und für die Bereitstellung, zu verwenden. / Gerät in der LocURI.

Es folgt ein Beispiel. Es gibt nur ein deinstallieren für gehostet und store-apps.

``` syntax
<Alert>
    <Data>1226</Data>
    <Item>
        <Source>
            <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/{PackageFamilyName}</LocURI>
        </Source>
        <Meta>
            <Type xmlns="syncml:metinf">Reversed-Domain-Name:com.microsoft.mdm.EnterpriseAppUninstall.result</Type>
            <Format xmlns="syncml:metinf">int</Format>
        </Meta>
        <Data>0</Data>
    </Item>
</Alert>
```

## <a name="update-your-apps"></a>Aktualisieren Sie Ihre apps

Apps, die auf einem Gerät installiert können mit dem Verwaltungsserver aktualisiert werden. Apps können direkt aus dem Speicher aktualisiert oder von einem gehosteten Speicherort installiert werden.

### <a name="update-apps-directly-from-the-store"></a>Aktualisieren von apps direkt aus dem Speicher

Zum Aktualisieren einer app aus Windows Store erfordert das Gerät Kontakt mit den Diensten anmelden.

Es folgt ein Beispiel einer Update-Überprüfung.

``` syntax
<!— Initiate a update scan for a user-->
<Exec>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/UpdateScan</LocURI>
      </Target>
   </Item>
</Exec>
```

Es folgt ein Beispiel der statusüberprüfung auf einen aus.

``` syntax
<!— Get last error related to the update scan-->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/LastScanError</LocURI>
      </Target>
   </Item>
</Get>
```

### <a name="update-apps-from-a-hosted-location"></a>Aktualisieren von einem Standort gehostete apps

Aktualisieren einer vorhandenen app folgt demselben Prozess wie einer Erstinstallation. Weitere Informationen finden Sie unter [Bereitstellen von apps, die einem Benutzer von einem gehosteten Standort](#deploy-apps-to-a-user-from-a-hosted-location).


### <a name="update-provisioned-apps"></a>Bereitgestellte apps aktualisieren

Eine app bereitgestellte werden automatisch aktualisiert, wenn eine Aktualisierung app an den Benutzer gesendet wird. Sie können auch eine bereitgestellte app mit den gleichen Prozess als anfänglichen Bereitstellung aktualisieren. Weitere Informationen zu der anfänglichen Bereitstellung finden Sie unter [Bereitstellung von apps für alle Benutzer eines Geräts](#provision-apps-for-all-users-of-a-device).

### <a name="prevent-app-from-automatic-updates"></a>Verhindern, dass die app von Automatische updates

Sie können verhindern, dass bestimmte apps, die automatisch aktualisiert wird. Hiermit können Sie automatische Updates für apps mit bestimmten apps durch den IT-Administrator definierten ausgeschlossen aktivieren

Deaktivieren des Updates gilt nur für Updates aus dem Windows Store auf Device-Ebene. Dieses Feature ist auf der Benutzerebene nicht verfügbar. Sie können weiterhin eine app aktualisieren, wenn die offline-Pakete von gehosteten Installationsort abgelegt wird.

Es folgt ein Beispiel.

``` syntax
<!— Prevent app from being automatically updated-->
<Replace>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/{PackageFamilyName}/DoNotUpdate</LocURI>
         </Target>
      <Meta>
         <Format xmlns="syncml:metinf">int</Format>
         <Type xmlns="syncml:metinf">text/plain</Type>
      </Meta>
      <Data>1</Data></Item>
</Replace>
```

## <a name="additional-app-management-scenarios"></a>Weitere app-Szenarios

Die folgenden Unterabschnitte enthalten Informationen zu Konfigurationen zusätzliche Einstellungen.

### <a name="restrict-app-installation-to-the-system-volume"></a>Einschränken des app-Installation auf dem Systemdatenträger

Sie können die app auf kein Systemlaufwerk Volumes, beispielsweise eine zweite Partition oder Wechselmedium (USB oder SD-Karten) installieren. Sie können die Richtlinie RestrictApptoSystemVolume apps aus abrufen installiert oder kein Systemlaufwerk Volumes verschoben verhindern. Weitere Informationen zu dieser Richtlinie finden Sie unter [CSP Richtlinie](policy-configuration-service-provider.md).

> **Hinweis**  Dies wird nur bei mobilen Geräten unterstützt.


Es folgt ein Beispiel.

``` syntax
<!-- Get policy (Default)-->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/Policy/Result/ApplicationManagement/RestrictAppToSystemVolume?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
<!-- Update policy -->
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/Policy/Config/ApplicationManagement/RestrictAppToSystemVolume</LocURI>
      </Target>
   <Meta> 
      <Format>int</Format> 
      <Type>text/plain</Type> 
   </Meta> 
   <Data>1</Data>                        
</Item>
</Replace>
```

### <a name="restrict-appdata-to-the-system-volume"></a>Einschränken von Anwendungsdaten auf dem Systemdatenträger

Administratoren können in Windows 10 Mobile SIE eine Richtlinie zum Einschränken von Benutzer Anwendungsdaten für eine Windows Store-app auf dem Systemdatenträger, unabhängig davon, wo das Paket installiert oder verschoben wird festlegen.

> **Hinweis**  Das Feature ist nur für Windows 10 Mobile.

 
Die Richtlinie RestrictAppDataToSystemVolume im [Bereich CSP Richtlinie](policy-configuration-service-provider.md) können Sie alle Benutzer Anwendungsdaten auf dem Systemdatenträger bleiben einschränken. Wenn die Richtlinie nicht konfiguriert ist oder wenn es deaktiviert ist, und Sie ein Paket verschieben oder wenn es auf einen Datenträger Unterschied installiert ist, klicken Sie dann die Benutzerdaten für die Anwendung werden verschoben auf die gleiche Volumes. Sie können diese Richtlinie auf 0 (deaktiviert, Standard) oder 1 festgelegt.

Es folgt ein Beispiel.

``` syntax
<!-- Get policy (Default)-->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/Policy/Result/ApplicationManagement/RestrictAppDataToSystemVolume?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
<!-- Update policy -->
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>                  
         <LocURI>./Vendor/MSFT/Policy/Config/ApplicationManagement/RestrictAppDataToSystemVolume</LocURI>
      </Target>
   <Meta> 
      <Format>int</Format> 
      <Type>text/plain</Type> 
   </Meta> 
   <Data>1</Data>                        
   </Item>
</Replace>
```

### <a name="enable-shared-user-app-data"></a>Gemeinsam genutzte Benutzer app-Daten aktivieren

Die universellen Windows app hat die Möglichkeit, die Benutzer des Geräts Anwendungsdaten gemeinsam. Die Möglichkeit zum Freigeben von Daten kann auf eine Produktfamilie Paket-Ebene oder pro Gerät festgelegt werden.

> **Hinweis**  Dies gilt nur auf mehrere Benutzer Geräte.


Die Richtlinie AllowSharedUserAppData im [Bereich CSP Richtlinie](policy-configuration-service-provider.md) aktiviert oder deaktiviert app-Pakete zum Freigeben von Daten zwischen app-Pakete, wenn mehrere Benutzer vorhanden sind. Wenn Sie diese Richtlinie aktivieren, können Applications Daten zwischen Paketen in ihre Paket Familie freigeben. Daten können über ShareLocal Ordner für dieses Paket-Produktfamilie und den lokalen Computer gemeinsam genutzt werden. Dieser Ordner ist über die API Windows.Storage verfügbar.

Wenn Sie diese Richtlinie deaktivieren, können nicht Applications Benutzer Anwendungsdaten durch mehrere Benutzer freigeben. Allerdings werden vordefinierter freigegebene Daten beibehalten. Verwenden Sie die Bereinigung vor dem geschrieben freigegebener Daten DISM ((/ Get-ProvisionedAppxPackage zu überprüfen, ob eine freigegebene Daten und /Remove-SharedAppxData entfernen).

Gültige Werte sind 0 (deaktiviert, Standardwert) und 1 (aktiviert).

Es folgt ein Beispiel.

``` syntax
<!-- Get policy (Default)-->
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/Policy/Result/ApplicationManagement/AllowSharedUserAppData?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
<!-- Update policy -->
<Replace>
   <CmdID>2</CmdID>
   <Item>
      <Target>                  
         <LocURI>./Vendor/MSFT/Policy/Config/ApplicationManagement/AllowSharedUserAppData</LocURI>
      </Target>
   <Meta> 
      <Format>int</Format> 
      <Type>text/plain</Type> 
   </Meta> 
   <Data>1</Data>                        
   </Item>
</Replace>
```

 






