---
title: DMClient CSP
description: "Der Dienstanbieter für DMClient Konfiguration wird verwendet, um zusätzliche unternehmensspezifische Mobilgerät Management-Konfigurationseinstellungen für das Gerät in der Enterprise-Domäne Sicherheit Risikominderung für Erneuerung von Zertifikaten und Enterprise Server ausgelöst Unenrollment identifizieren angeben."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a5cf35d9-ced0-4087-a247-225f102f2544
ms.openlocfilehash: cfbc8dfa30ef45e7b45651d22d4f3a4a7753119f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dmclient-csp"></a>DMClient CSP


Der Dienstanbieter für DMClient Konfiguration wird verwendet, um zusätzliche unternehmensspezifische Mobilgerät Management-Konfigurationseinstellungen für das Gerät in der Enterprise-Domäne Sicherheit Risikominderung für Erneuerung von Zertifikaten und Enterprise Server ausgelöst Unenrollment identifizieren angeben.

Das folgende Diagramm zeigt den DMClient Konfiguration-Dienstanbieter in der Strukturformat.

![DMClient csp](images/provisioning-csp-dmclient-th2.png)

<a href="" id="dmclient"></a>**DMClient**  
Stammknoten für den CSP.

<a href="" id="updatemanagementserviceaddress"></a>**UpdateManagementServiceAddress**  
Für die Bereitstellung nur Pakete. Gibt die Liste der Server (durch Semikolons getrennten) an. Der erste Server in der Liste durch Semikolons getrennt ist der Server, der zum Instanziieren MDM Sitzungen verwendet werden. Die Liste kann eine Variation oder eine Teilmenge der Serverliste der vorhandenen sein. Neue Server kann nicht der Liste mithilfe dieser Knoten hinzugefügt werden.

<a href="" id="provider"></a>**Anbieter**  
Erforderlich. Der Stammknoten für alle Einstellungen, die zu einem zentralen Verwaltungsserver gehören. Bereich wird dauerhaft gelöscht.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid"></a>**Anbieter / ***_ProviderID_**  
Optional Dieser Knoten enthält den URI-codierte Wert des Bootstrapperkomponenten Gerät Managementkonto-ID-Anbieter. Bereich ist dynamisch. Es empfiehlt sich verwenden Sie Text, die XML-URI Escapezeichen erfordern nicht.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="provider-providerid-entdevicename"></a>* *Anbieter /*ProviderID*/EntDeviceName**  
Optional Zeichenfolge, die von der IT-Verwaltungskonsole verwendet benutzerfreundlichen Gerätename enthält. Der Wert wird während der Registrierungsprozess über den DMClient Konfigurationsdienstanbieter festgelegt. Sie können diese später während einer Sitzung OMA DM abrufen.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="provider-providerid-entdmid"></a>* *Anbieter /*ProviderID*/EntDMID**  
Optional Zeichenfolge, die das Gerät eindeutige Enterprise-ID. Der Wert wird vom Verwaltungsserver während der Registrierungsprozess über den DMClient Konfigurationsdienstanbieter festgelegt. Sie können diese später während einer Sitzung OMA DM abrufen.

Unterstützte Vorgänge sind Get und hinzufügen.

> **Hinweis**   Hardware Geräte-ID eindeutig sein garantiert werden, ist von Bedeutung, dass dies während einer Sitzung DM nicht letztlich durchsetzbar ist. Die Geräte-ID konnte von einem anderen Management Server über die w7 ANWENDUNG Konfiguration des Dienstanbieters **USEHWDEVID** Parameter geändert werden. So wird eine neue Geräte-ID während Enterprise Bootstrap und die Registrierung, vom Enterprise Server angegeben.
Dieser Knoten ist erforderlich und muss vom Server festgelegt werden, bevor die Client Zertifikat Erneuerung ausgelöst wird.

 

<a href="" id="provider-providerid-exchangeid"></a>* *Anbieter /*ProviderID*/ExchangeID**  
Optional Zeichenfolge, die enthält die eindeutige Exchange Geräte-ID verwendet, die für Outlook-Kontos des Benutzers an, der die Sitzung ausgeführt wird. Dies ist hilfreich für den Enterprise-Verwaltungsserver Korrelieren und Zusammenführen von Einträgen für ein Gerät, das von Exchange verwaltet und systemintern von einem dedizierten Management Server verwaltet.

> **Hinweis**  In einigen Fällen für Desktop wird dieser Knoten "wurde nicht gefunden" zurück, bis der Benutzer ihre e-Mails festgelegt.

 

Unterstützte Vorgang ist Get.

Es folgt eine Get-Command-Beispiel.

``` syntax
<Get>
   <CmdID>12</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/DMClient/Provider/<ProviderID>/ExchangeID</LocURI>
      </Target>
   </Item>
</Get>
```

<a href="" id="provider-providerid-publisherdeviceid"></a>* *Anbieter /*ProviderID*/PublisherDeviceID**  
(Nur für Windows 10 Mobile.) Optional. Die PublisherDeviceID ist eine Gerät-eindeutige ID erstellt basierend auf der Enterprise Publisher-ID. Publisher-ID erstellt basierend auf den Enterprise-Anwendung Token und die Enterprise-ID über ./Vendor/MSFT/EnterpriseAppManagement/&lt;Enterprise-Id&gt;/EnrollmentToken. Es wird sichergestellt, dass für eine Enterprise jedes Gerät eine eindeutige ID zugeordnet ist. Für dasselbe Gerät wird besitzt mehrere Unternehmen Applications, jeder Enterprise unterschiedlich identifiziert.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-signedentdmid"></a>**Anbieter /* ProviderID*/SignedEntDMID** Optional. Zeichenfolge, die Geräte-ID. enthält Dieser Knoten und den Knoten **CertRenewTimeStamp** kann Clientidentität überprüfen, um die Registrierungsdatensatz zu aktualisieren, nachdem das Gerät Zertifikat erneuert wird vom mobilen Gerät Management-Server verwendet werden. Das Gerät auf Anzeichen für die **EntDMID ** mit dem alten Clientzertifikat während der Erneuerung des Zertifikats und speichert die Signatur lokal.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-certrenewtimestamp"></a>* *Anbieter /*ProviderID*/CertRenewTimeStamp**  
Optional Die Zeit in der OMA DM Standardzeitformat. Dieser Knoten ist darauf ausgelegt, zur Risikominderung des Zertifikats von einem anderen Gerät verwendet wird. Das Gerät zeichnet die Zeit, die das neue Zertifikat erstellt wurde.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-managementserviceaddress"></a>* *Anbieter /*ProviderID*/ManagementServiceAddress**  
Erforderlich. Die Zeichenfolge, die Adresse des Geräts Management Server enthält. Sie können während einer Sitzung OMA DM vom Verwaltungsserver zu dem Server für den Lastenausgleich an einen anderen Server in Situationen, in dem zu viele Geräte mit dem Server verbunden sind, aktualisiert werden.

> **Hinweis**  Bei der ManagementServerAddressList-Wert festgelegt ist, wird das Gerät den Wert im ManagementServiceAddress ignoriert.

 

Der Dienstanbieter für DMClient Konfiguration speichern die Adresse an den gleichen Speicherort wie die w7 und DMS Konfiguration-Dienstanbieter, um sicherzustellen, dass der Management-Client eine zentrale Stelle zum Abrufen der Adresse des aktuellen Servers hat. Der Anfangswert für diesen Knoten ist denselben Server Adresse-Wert wie Bootstrapperkomponenten über den [w7 ANWENDUNG Konfiguration-Dienstanbieter](w7-application-csp.md).

Windows-10, Version 1511 ab, diesem Knoten unterstützt mehrere Serveradressen im Format &lt;URL1&gt;&lt;URL2&gt;&lt;URL3&gt;. Es ist nur eine einzelne URL, und klicken Sie dann die &lt; &gt; sind nicht erforderlich. Dies ist für Desktop- und mobilen Geräten unterstützt.

Während einer Sitzung DM das Gerät verwendet die erste Adresse in der Liste und klicken Sie dann laufen weiter, der Liste nach unten, bis eine erfolgreiche Verbindung erreicht wird. Der DM Client sollte die URL erfolgreich verbundenen Server für die nächste Sitzung zwischenspeichern.

Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="provider-providerid-upn"></a>* *Anbieter /*ProviderID*/UPN**  
Optional Ermöglicht den Verwaltungsserver so aktualisieren Sie die Benutzer Principal Name (UPN) von der registrierten Benutzer. Dies ist nützlich in Szenarien, in dem die e-Mail-Adresse des Benutzers in vom Identitätssystem oder in das Szenario, in dem der Benutzer gibt eine ungültige UPN während der Registrierung und behebt den UPN während der Registrierung Verbundpartner. Der UPN, werden aufgezeichnet, und die UX den aktualisierten UPN wiedergegeben wird.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="provider-providerid-helpphonenumber"></a>* *Anbieter /*ProviderID*/HelpPhoneNumber**  
Optional Die Zeichenfolge, die die Benutzeroberfläche eine Telefonnummer benutzerdefinierte Hilfe enthalten, die der Endbenutzer werden können, anzeigen und verwenden, wenn sie Hilfe oder Unterstützung benötigen ermöglicht.

Unterstützte Vorgänge sind Get, ersetzen, und löschen.

<a href="" id="provider-providerid-helpwebsite"></a>* *Anbieter /*ProviderID*/HelpWebsite**  
Optional Die Zeichenfolge, die die Benutzeroberfläche auf eine benutzerdefinierte Hilfewebsite umfassen, die der Endbenutzer werden anzeigen und verwenden, wenn sie Hilfe oder Unterstützung benötigen ermöglicht.

Unterstützte Vorgänge sind Get, ersetzen, und löschen

<a href="" id="provider-providerid-helpemailaddress"></a>* *Anbieter /*ProviderID*/HelpEmailAddress**  
Optional Zeichenfolge, die Benutzeroberfläche, um eine benutzerdefinierte Hilfe e-Mail-Adresse enthalten, die der Endbenutzer werden einsehen und nutzen, wenn sie Hilfe oder Unterstützung benötigen ermöglicht.

Unterstützte Vorgänge sind Get, ersetzen, und löschen.

<a href="" id="provider-providerid-requiremessagesigning"></a>* *Anbieter /*ProviderID*/RequireMessageSigning**  
Boolean-Typ. Primarly weitergeleitet, woraufhin für SSL-bridging-Modus, in dem durch Firewalls und Proxys bereitgestellt werden, auf dem Gerät Clientidentität erforderlich ist. Wenn aktiviert, wird jede Nachricht SyncML vom Gerät mit dem Namen MDM-Signatur zusätzlichen HTTP-Header übertragen. Diese Kopfzeile enthält Cryptographic Message-Syntax BASE64-codierten mithilfe einer getrennten Signatur der vollständige SyncML Nachricht SHA-2 (einschließlich der SyncHdr und SyncBody). Signieren wird mit dem privaten Schlüssel des Zertifikats Sitzung Management, das registriert wurde als Teil des Registrierungsvorgangs ausgeführt. Die öffentlichen Geräteschlüssel und PKCS9 UTC Signatur einen Zeitstempel sind Bestandteil der authentifizierten Attribute in der Signatur.

Standardwert ist "false" können, wobei der Gerät Management-Client nicht Authentifizierungsinformationen Management-Sitzung HTTP-Header enthalten ist. Auf "true", in dem die Authentifizierungsinformationen Client im HTTP-Header Management Sitzung bereitgestellt wird, optional festlegen.

Wenn aktiviert, der MDM Server die Signatur überprüfen sollte und der Zeitstempel des Geräts identifizieren Zertifikat als Teil des MS-MDE-registriert, stellen Sie sicher, dass das Zertifikat und die Uhrzeit gültig sind und sicherzustellen, dass der Server MDM die Signatur vertrauenswürdig ist.

Unterstützte Vorgänge sind Get, ersetzen, und löschen.

<a href="" id="provider-providerid-syncapplicationversion"></a>* *Anbieter /*ProviderID*/SyncApplicationVersion**  
Optional Verwendet vom Verwaltungsserver die DM Sitzung Version festlegen, die dem Server und dem Gerät verwendet werden soll. Der Standardwert lautet 1.0. In Windows 10 wird die DM Sitzung Protocol, Version des Clients 2.0. Wenn der Server zur Unterstützung der 2.0 aktualisiert wird, sollten Sie diesen Wert auf 2.0 festgelegt. Überprüfen Sie in der nächsten Sitzung um festzustellen, ob zwischen 1.0 und 2.0 Client Verhalten geändert wird.

> **Hinweis**  
Dieser Knoten ist nur in Windows 10 und höher unterstützt.

Sobald Sie den Wert auf 2.0 festgelegt, wird es nicht 1.0 zurückkehren.

 

Unterstützte Vorgänge sind Get, ersetzen, und löschen.

<a href="" id="provider-providerid-maxsyncapplicationversion"></a>* *Anbieter /*ProviderID*/MaxSyncApplicationVersion**  
Optional Vom Client verwendet, um die neueste Version des DM-Sitzung anzugeben, die sie unterstützt. Der Standardwert lautet 2.0.

Beim Abfragen von diesem Knoten ein Client Windows 10 2.0 zurückgegeben, und Clientidentität Windows 8.1 wird einen Fehlercode (404 Knoten wurde nicht gefunden) zurückzugeben.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-aadresourceid"></a>* *Anbieter /*ProviderID*/AADResourceID**  
Optional Dies ist der ResourceID verwendet, wenn das Benutzertoken aus der Sitzung OMA DM für Azure Active Directory-Registrierung (AAD teilnehmen oder Konten hinzufügen) anfordern. Das Token ist Benutzergruppe bestimmte, wodurch andere Service Prinzipale (Registrierung im Vergleich zu Gerätemanagement) ermöglicht. Es kann sein, eine Anwendungs-ID oder den Endpunkt, den Sie zugreifen möchten.

Weitere Informationen zur Registrierung von Azure Active Directory finden Sie unter [Integration mit MDM Azure Active Directory](azure-active-directory-integration-with-mdm.md).

<a href="" id="provider-providerid-enableomadmkeepalivemessage"></a>* *Anbieter /*ProviderID*/EnableOmaDmKeepAliveMessage**  
In Windows-10, Version 1511 hinzugefügt. Ein boolescher Wert, der angibt, ob der DM Client eine Anfrage ausstehenden Benachrichtigung in Fall die Gerät als Antwort auf eine Anforderung DM senden soll ist zu langsam.

Wenn der Server eine Konfiguration-Anforderung sendet, manchmal dauert des Clients länger als die HTTP-Timeout zusammen alle Informationen und anschließend die Sitzung beendet unerwartet aufgrund eines Timeouts. Standardmäßig werden der MDM-Client keine Benachrichtigung gesendet, dass eine Anforderung DM aussteht.

Das Timeout zu umgehen, können Sie diese Einstellung die Sitzung durch Senden von Heartbeat-Nachrichten an den Server zurückgesendet beibehalten werden soll. Dies ist eine SyncML Nachricht mit einem bestimmten Gerät alert-Element im Text senden, bis der Client wieder auf dem Server mit den angeforderten Informationen reagieren kann.

Es folgt ein Beispiel DM Nachricht vom Gerät gesendet wird, wenn im Zustand steht:

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncHdr>
<VerDTD>1.2</VerDTD>
        <VerProto>DM/1.2</VerProto>
        <SessionID>10</SessionID>
        <MsgID>2</MsgID>
      <Target>
         <LocURI>https://www.contoso.com/mgmt-server</LocURI>
      </Target>
      <Source>
         <LocURI>{unique device ID}</LocURI>
      </Source>
  </SyncHdr>
  <SyncBody>
<Alert>
    <CmdID>2</CmdID>
    <Data>1224</Data> 
    <Item>
        <Meta>
            <Type xmlns="syncml:metinf">Reversed-Domain-Name:com.microsoft.mdm.requestpending</Type>
        </Meta>
        <Data>1</Data>
    </Item>
</Alert>
  </SyncBody>
</SyncML>
```

<a href="" id="provider-providerid-aaddeviceid"></a>* *Anbieter /*ProviderID*/AADDeviceID**  
In Windows 10, Version 1607 hinzugefügt. Gibt die Geräte-ID für die Registrierung des Azure Active Directory Gerät zurück.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-enrollmenttype"></a>* *Anbieter /*ProviderID*/EnrollmentType**  
In Windows 10, Version 1607 hinzugefügt. Gibt den Registrierungs-Typ (Gerät oder vollständig).

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-hwdevid"></a>* *Anbieter /*ProviderID*/HWDevID**  
In Windows 10, Version 1607 hinzugefügt. Gibt die Hardware-Geräte-ID.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-commercialid"></a>* *Anbieter /*ProviderID*/CommercialID**  
In Windows 10, Version 1607 hinzugefügt. Konfiguriert den Bezeichner verwendet, um diese Telemetriedaten dieses Geräts gehört zu einer bestimmten Organisation eindeutig zuzuordnen. Wenn Ihre Organisation in ein Programm, die dieses Gerät teilnimmt identifiziert werden, als Teil Ihrer Organisation benötigt verwenden Sie diese Einstellung, Kennung bereitstellen. Der Wert für diese Einstellung wird für das Programm von Microsoft im Rahmen des Prozesses Onboarding bereitgestellt werden. Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, klicken Sie dann werden Microsoft kann nicht dieser Bezeichner zuordnen dieser Computer und seine Telemetriedaten zu Ihrer Organisation verwendet.

Unterstützte Vorgänge sind Add, Get-ersetzen, und löschen.

<a href="" id="provider-providerid-managementserveraddresslist"></a>* *Anbieter /*ProviderID*/ManagementServerAddressList**  
In Windows 10, Version 1607 hinzugefügt. Die Liste der Management Server-URLs im Format &lt;URL1&gt;&lt;URL2&gt;&lt;URL3&gt;usw.... Wenn es nur ein, die spitzen Klammern gibt (&lt;&gt;) sind nicht erforderlich.

> **Hinweis**  Die &lt; und &gt; sollten geschützt werden.

 

``` syntax
   <Replace>
       <CmdID>101</CmdID>
       <Item>
           <Target>
               <LocURI>
                  ./Vendor/MSFT/DMClient/Provider/<ProviderID>/ManagementServerAddressList
               </LocURI>
           </Target>
           <Data>&lt;https://server1&gt;&lt;https:// server2&gt; </Data>
       </Item>
   </Replace>
```

Wenn ManagementServerAddressList Knoten festgelegt ist, das Gerät nur verwenden Sie die URL des Servers, die in diesem Knoten konfiguriert und der Wert ManagementServiceAddress ignoriert.

Wenn der Server nach einer bestimmten Anzahl der Wiederholungsversuche nicht reagiert, versucht das Gerät verwenden die URL des nächste Servers in der Liste, bis sie erfolgreich eine Verbindung hergestellt wird. Nachdem die Serverliste aktualisiert wurde, verwendet der Client die aktualisierte Liste bei der nächsten Sitzung in der Liste mit dem ersten auf starten.

Unterstützte Vorgänge sind Get und ersetzen. Werttyp ist Zeichenfolge.

<a href="" id="provider-providerid-poll"></a>* *Anbieter /*ProviderID*/Poll**  
Optional Abruf Zeitpläne müssen DMClient CSP verwenden. Registrierungspfade zuvor Abrufe mit dem CSP Registrierung zugeordnet sind nun veraltet.

Unterstützte Vorgänge sind Get und hinzufügen.

Es gibt drei Zeitpläne unter dem Knoten Umfrage verwaltet die ermöglichen eine umfangreiche Abruf Zeitplan Erfahrung ermöglichen größere Flexibilität bei der Verwaltung der Möglichkeit, in der Geräte den Management Server abzufragen. Es gibt verschiedene Arten in denen Abruf Zeitpläne festgelegt werden können. Wenn eine ungültige Abruf Konfiguration festgelegt ist, wird das Gerät korrigieren oder entfernen die Zeitpläne, um die Abstimmungsfrage Zeitpläne wieder auf eine ungültige Konfiguration wiederherstellen.

Wenn kein unendlichen Zeitplan festgelegt ist, ein 24-Stunden-Zeitplan erstellt und geplant, in der Wartungsfensters zu starten.

**Gültige Umfrage Zeitplan: Sigmoidfunktion Abrufzeitplan mit unendlichen Zeitplan (empfohlen).**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Zeitplanname</th>
<th>Zeitplan, festgelegt vom server</th>
<th>Istwert abgefragt auf Gerät</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IntervalForFirstSetOfRetries</p></td>
<td><p>15</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>NumberOfFirstRetries</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForSecondSetOfRetries</p></td>
<td><p>60</p></td>
<td><p>60</p></td>
</tr>
<tr class="even">
<td><p>NumberOfSecondRetries</p></td>
<td><p>10</p></td>
<td><p>10</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForRemainingScheduledRetries</p></td>
<td><p>1440</p></td>
<td><p>1440</p></td>
</tr>
<tr class="even">
<td><p>NumberOfRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

**Gültige Umfrage Zeitplan: nur die ersten Registrierung \[kein unendlichen Zeitplan\]**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Zeitplanname</th>
<th>Zeitplan, festgelegt vom server</th>
<th>Istwert abgefragt auf Gerät</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IntervalForFirstSetOfRetries</p></td>
<td><p>15</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>NumberOfFirstRetries</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForSecondSetOfRetries</p></td>
<td><p>60</p></td>
<td><p>60</p></td>
</tr>
<tr class="even">
<td><p>NumberOfSecondRetries</p></td>
<td><p>10</p></td>
<td><p>10</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>NumberOfRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

**Ungültige Umfrage Zeitplan: Deaktivieren Sie alle Umfrage Zeitpläne**

> **Hinweis**   Deaktivieren Umfrage plant, führt zu einem nicht DEFINIERTEN Verhalten und Registrierung möglicherweise fehl, wenn der Umfrage Zeitpläne auf 0 (null) festgelegt werden.

 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Zeitplanname</th>
<th>Zeitplan, festgelegt vom server</th>
<th>Istwert abgefragt auf Gerät</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IntervalForFirstSetOfRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>NumberOfFirstRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForSecondSetOfRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>NumberOfSecondRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>NumberOfRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

**Ungültige Umfrage Zeitplan: zweier unendlichen Zeitpläne**

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Zeitplanname</th>
<th>Zeitplan, festgelegt vom server</th>
<th>Tatsächliche Zeitplan auf Gerät festlegen</th>
<th>Tatsächliche Erfahrung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IntervalForFirstSetOfRetries</p></td>
<td><p>15</p></td>
<td><p>15</p></td>
<td><p>Gerät Umfragen</p></td>
</tr>
<tr class="even">
<td><p>NumberOfFirstRetries</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
<td><p>Gerät Umfragen</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForSecondSetOfRetries</p></td>
<td><p>1440</p></td>
<td><p>1440</p></td>
<td><p>Gerät fragt den Server einmal in 24 Stunden ab.</p></td>
</tr>
<tr class="even">
<td><p>NumberOfSecondRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p>Gerät fragt den Server einmal in 24 Stunden ab.</p></td>
</tr>
<tr class="odd">
<td><p>IntervalForRemainingScheduledRetries</p></td>
<td><p>1440</p></td>
<td><p>0</p></td>
<td><p>Dritte Zeitplan ist deaktiviert.</p></td>
</tr>
<tr class="even">
<td><p>NumberOfRemainingScheduledRetries</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p>Dritte Zeitplan ist deaktiviert.</p></td>
</tr>
</tbody>
</table>

 

Wenn das Gerät mit Abrufzeitplan direkt über Registrierungsschlüsselwerte konfiguriert zuvor MDM registriert wurde, muss der MDM Server unterstützt die Verwendung von DMClient CSP Abruf Terminplan aktualisieren, die zuerst einen Befehl hinzufügen auf Hinzufügen Senden einer **./Vendor/MSFT/DMClient/Enrollment/&lt;ProviderID&gt;/Abfragen** Knoten vor dem Senden eines Befehls Get/ersetzen zum Abfragen oder Abruf Parameter über DMClient CSP aktualisieren

Bei Verwendung der DMClient CSP Abruf Zeitplanparameter Konfigurieren der Server muss nicht alle sechs Abruf-Parameter auf 0 festlegen, oder alle 3 Anzahl der Wiederholungsversuche Knoten auf 0 festlegen, da es einen Konfigurationsfehler verursacht.

<a href="" id="provider-providerid-poll-intervalforfirstsetofretries"></a>* *Anbieter /*ProviderID*/Umfrage/IntervalForFirstSetOfRetries **  
Optional Die Wartezeit (in Minuten) für den ersten Satz Wiederholungsversuche wie angegeben durch die Anzahl der Wiederholungsversuche in /&lt;ProviderID&gt;/Umfrage/NumberOfFirstRetries. Wenn IntervalForFirstSetOfRetries nicht festgelegt ist, wird der Standardwert verwendet. Der Standardwert ist 15. Wenn der Wert auf 0 festgelegt ist, ist dieser Zeitplan deaktiviert.

Unterstützte Vorgänge sind Get und ersetzen.

Die IntervalForFirstSetOfRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\AuxRetryInterval Pfad, die zuvor die Registrierung CSP genutzt.

<a href="" id="provider-providerid-poll-numberoffirstretries"></a>* *Anbieter /*ProviderID*/Umfrage/NumberOfFirstRetries **  
Optional Die Anzahl der Häufigkeit, mit die der Client DM wiederholen sollten, um mit dem Server herstellen, wenn der Client zunächst konfiguriert oder die Kommunikation mit dem Server registriert. Wenn der Wert festgelegt ist wird auf 0 und der Wert nicht ist IntervalForFirstSetOfRetries 0, und klicken Sie dann auf den Zeitplan eine unbegrenzte Anzahl von Klicks wiederholt werden sollen und zweiten Gruppe und dieser Gruppe von Zeitplan werden nicht festgelegt in diesem Fall. Der Standardwert ist 10.

Unterstützte Vorgänge sind Get und ersetzen.

Die NumberOfFirstRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\AuxNumRetries Pfad, die zuvor die Registrierung CSP genutzt.

Der erste Satz von Wiederholungsversuche Geben Sie dem Verwaltungsserver zwischengespeicherten Weile Richtlinien und Einstellungskonfiguration an das Gerät gesendet werden soll. Die gesamte Zeitdauer für den ersten Satz von Wiederholungsversuche darf nicht mehr als ein paar Stunden sein. Der Server sollte nicht NumberOfFirstRetries 0 festgelegt. RemainingScheduledRetries wird für das lange Gerät Abrufe Zeitplan verwendet.

<a href="" id="provider-providerid-poll-intervalforsecondsetofretries"></a>* *Anbieter /*ProviderID*/Umfrage/IntervalForSecondSetOfRetries **  
Optional Die Wartezeit (in Minuten) für die zweite Gruppe von Wiederholungsversuche wie angegeben durch die Anzahl der Wiederholungsversuche in /&lt;ProviderID&gt;/Umfrage/NumberOfSecondRetries. Standardwert ist 0. Wenn Sie diesen Wert auf NULL festgelegt ist, wird dieser Zeitplan deaktiviert.

Unterstützte Vorgänge sind Get und ersetzen.

Die IntervalForSecondSetOfRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\RetryInterval Pfad, die zuvor die Registrierung CSP genutzt.

<a href="" id="provider-providerid-poll-numberofsecondretries"></a>* *Anbieter /*ProviderID*/Umfrage/NumberOfSecondRetries **  
Optional Die Anzahl der DM-Client der Verbindung mit dem Server, wenn der Client zunächst konfiguriert/registriert Kommunikation mit dem Server ist eine zweite Rundung wiederholen soll. Standardwert ist 0. Wenn der Wert auf 0 festgelegt ist und IntervalForSecondSetOfRetries nicht auf 0 festgelegt ist UND der erste Satz der Wiederholungsversuche als unendlich Wiederholungsversuche nicht festgelegt ist, wird der Zeitplan eine unbegrenzte Anzahl von Klicks wiederholt. Jedoch ist der erste Satz von Wiederholungsversuchen auf unendlich festgelegt, wird dieser Zeitplan deaktiviert.

Unterstützte Vorgänge sind Get und ersetzen.

Die NumberOfSecondRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\' NumRetries ' Pfad, die zuvor die Registrierung CSP genutzt.

Der zweite Satz der Wiederholungsversuche ist ebenfalls optional und vorübergehend, ein Wiederholungsversuch durchgeführt, dass die gesamte Dauer für mehr als einen Tag letzten werden soll. Und die IntervalForSecondSetOfRetries länger als IntervalForFirstSetOfRetries sein. RemainingScheduledRetries wird für das Abrufen der Zeitplan Long ausführen-Gerät verwendet.

<a href="" id="provider-providerid-poll-intervalforremainingscheduledretries"></a>* *Anbieter /*ProviderID*/Umfrage/IntervalForRemainingScheduledRetries **  
Optional Die Wartezeit (in Minuten) für den ersten Satz Wiederholungsversuche wie angegeben durch die Anzahl der Wiederholungsversuche in /&lt;ProviderID&gt;/Umfrage/NumberOfRemainingScheduledRetries. Standardwert ist 0. Wenn IntervalForRemainingScheduledRetries auf 0 festgelegt ist, ist dieser Zeitplan deaktiviert.

Unterstützte Vorgänge sind Get und ersetzen.

Der IntervalForRemainingScheduledRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\Aux2RetryInterval Pfad, den die Registrierung CSP zuvor genutzt.

<a href="" id="provider-providerid-poll-numberofremainingscheduledretries"></a>* *Anbieter /*ProviderID*/Umfrage/NumberOfRemainingScheduledRetries **  
Optional Die Anzahl der DM Client mit dem Server verbinden wiederholen sollte, wenn der Client zunächst konfiguriert/registriert Kommunikation mit dem Server ist. Standardwert ist 0. Wenn der Wert 0 und IntervalForRemainingScheduledRetries UND für die erste und zweite Satz von Wiederholungsversuche nicht als unendlich Wiederholungsversuche festgelegt ist, wird der Zeitplan festgelegt werden, für eine unbegrenzte Anzahl von Klicks wiederholt werden sollen. Jedoch, wenn eine oder beide der ersten und zweiten Reihe von Wiederholungsversuche als unendlich festgelegt sind, wird dann dieser Zeitplan deaktiviert.

Unterstützte Vorgänge sind Get und ersetzen.

Die NumberOfRemainingScheduledRetries ersetzt die veraltete HKLM\\Software\\Microsoft\\Registrierung\\OmaDmRetry\\Aux2NumRetries Pfad, die zuvor die Registrierung CSP genutzt.

Die RemainingScheduledRetries wird für das Abfrageintervall Zeitplan lange Gerät verwendet. IntervalForRemainingScheduledRetries sollte nicht im 8.1 für Windows Phone-Gerät für kleiner als 1440 Minuten (24 Stunden) festgelegt werden. Windows Phone 8.1 unterstützt MDM Server Pushbenachrichtigungen.

<a href="" id="provider-providerid-poll-pollonlogin"></a>* *Anbieter /*ProviderID*/Umfrage/PollOnLogin **  
Optional Boolescher Wert, der ermöglicht der IT-Administrator muss das Gerät Management-Sitzung auf eine beliebige Benutzername unabhängig von starten, wenn der Benutzer eineingestellt angemeldet hat. Anmeldung ist nicht identisch mit Gerät entsperren. Standardwert ist "false" können, wobei bei der ersten Anmeldung Abruf deaktiviert ist. Unterstützte Werte sind true oder false.

Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="provider-providerid-poll-alluserspollonfirstlogin"></a>* *Anbieter /*ProviderID*/Umfrage/AllUsersPollOnFirstLogin **  
Optional Boolescher Wert, der der IT-Administrator muss das Gerät zum Starten einer Management-Sitzung auf der ersten Anmeldung für alle NT-Benutzer kann. Eine Sitzung wird nur aus der ersten ausgeschlossen werden, die ein Benutzer auf das System anmeldet; nachfolgende Anmeldungen werden eine Sitzung MDM nicht ausgelöst. Anmeldung ist nicht identisch mit Gerät entsperren. Standardwert ist "false" können, wobei bei der ersten Anmeldung Abruf deaktiviert ist. Unterstützte Werte sind true oder false.

Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="provider-providerid-push"></a>* *Anbieter /*ProviderID*/Push**  
Optional Während der WAP Provisioining XML nicht konfigurierbar. Wenn entfernt, werden ausgelöst, indem Push DM-Sitzungen nicht mehr unterstützt.

Unterstützte Vorgänge sind hinzufügen und löschen.

<a href="" id="provider-providerid-push-pfn"></a>* *Anbieter /*ProviderID*/Push/PFN **  
Erforderlich. Eine Zeichenfolge von der Windows-10-Ökosystem für eine Lösung für die Verwaltung mobiler Geräte bereitgestellt. Verwendet ein Gerät für Push-Benachrichtigungen registriert. Der Server muss die gleiche PFN wie die Geräte verwenden, die verwaltet wird.

Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="provider-providerid-push-channeluri"></a>* *Anbieter /*ProviderID*/Push/ChannelURI **  
Erforderlich. Eine Zeichenfolge, die den DDE-Kanal enthält, den der Client WNS ausgehandelt hat für den OMA DM-Client auf dem Gerät basierend auf der PFN, die bereitgestellt wurden. Wenn keine gültige PFN derzeit festgelegt ist, gibt ChannelURI null zurück.

Unterstützte Vorgang ist Get.

<a href="" id="provider-providerid-push-status"></a>* *Anbieter /*ProviderID*/Push/Status **  
Erforderlich. Eine ganze Zahl, die eine bekannte Fehlerstatus oder Bedingung im System zuordnet.

Unterstützte Vorgang ist Get.

Die Zuordnung der Status-Fehler sind unten aufgeführt.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Status</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Erfolg</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Fehler: Ungültige PFN</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Fehler: Ungültige oder abgelaufene Geräteauthentifizierung mit MSA</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Fehler: WNS Clientregistrierung ist aufgrund einer ungültigen oder gesperrt PFN</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>Fehler: kein DDE-Kanal-URI zugewiesen</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>Fehler: Channel-URI ist abgelaufen.</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>Fehler: Channel-URI konnte nicht aufgehoben werden</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Fehler: push Notification empfangen, aber nicht möglich, eine Sitzung OMA DM aufgrund von Einschränkungen Power oder Verbindung herzustellen.</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>Unbekannter Fehler</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="provider-providerid-unenroll"></a>* *Anbieter /*ProviderID*/ Anmeldung kündigen **  
Erforderlich. Der Knoten akzeptiert Unenrollment über den Befehl OMA DM Exec fordert und ruft den Registrierungs-Client, um das Gerät aus dem Verwaltungsserver Anmeldung kündigen, dessen Provider-ID, in angegeben wird, der "<Data>` tag under the `<Item>' Element. Bereich wird dauerhaft gelöscht.

Unterstützte Vorgänge sind Get und Exec.

Beachten Sie, dass &lt;LocURI&gt;./Vendor/MSFT/DMClient/Unenroll&lt;/LocURI&gt; wird für die Abwärtskompatibilität unterstützt.

Die folgenden SyncML veranschaulicht, wie das Gerät Remote Anmeldung kündigen. Beachten Sie, dass dieser Befehl soll, in den allgemeinen DM-Paketen an das Gerät vom Server gesendet eingefügt werden.

``` syntax
    <Exec>
       <CmdID>2</CmdID>
       <Item>
          <Target>
             <LocURI>./Vendor/MSFT/DMClient/Provider/<ProviderID>/Unenroll</LocURI>
          </Target>
          <Meta>
             <Format xmlns=”syncml:metinf”>chr</Format>
          </Meta>
          <Data>TestMDMServer</Data> 
          <!-- Data Field in Threshold is now IGNORED -->
       </Item>
    </Exec>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






