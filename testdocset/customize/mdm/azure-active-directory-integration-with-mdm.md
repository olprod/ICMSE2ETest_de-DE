---
title: Azure Active Directory-Integration mit MDM
description: "Azure Active Directory ist die Welt größten Enterprise Identity Management Clouddienst."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D03B0765-5B5F-4C7B-9E2B-18E747D504EE
ms.openlocfilehash: ef92a03c2996ea8b4756c14a800007c08f1ec6e3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<head>
<style type='text/css'>Table.topalign td {vertikale Ausrichtung: oben}</style>
</head>

# <a name="azure-active-directory-integration-with-mdm"></a>Azure Active Directory-Integration mit MDM

Azure Active Directory ist der Welt größten Enterprise Identity Management Clouddienst. Es wird von Millionen von Access Office 365-Organisationen und Tausende von Geschäftsanwendungen von Microsoft und Drittanbietern Software als ein Anbieter Service (SaaS) verwendet. Viele der die Rich-Text, den, die Windows-10 für organisatorische Benutzer (wie Speicherzugriff oder OS Zustand roaming) guter, verwenden Azure AD als die zugrunde liegende Identitätsinfrastruktur. Windows-10 bietet eine integrierte Konfiguration Erfahrung mit Azure AD-Geräte in Azure Active Directory registriert und einen reibungslosen integrierte Fluss in MDM registriert werden.

Nachdem ein Gerät MDM registriert ist, kann die MDM Einhaltung von Unternehmensrichtlinien, hinzufügen oder Entfernen von apps und vieles mehr. Darüber hinaus kann die MDM des Geräts Compliance Azure AD melden. Auf diese Weise können Azure AD zum Zulassen des Zugriffs auf Unternehmensressourcen oder Anwendungen von Azure Active Directory nur für Geräte, die Einhaltung von Richtlinien gesichert. Um diese umfassenden Erfahrungen mit Produkts MDM zu unterstützen, können MDM Herstellern in Azure AD integriert werden. In diesem Thema werden die folgenden Schritte ausgeführt werden.

## <a name="connect-to-azure-ad"></a>Verbinden mit Azure AD

Verschiedene Möglichkeiten, die Geräte zu verbinden:

Für unternehmenseigene Geräte:
-   Fügen Sie Windows eine herkömmliche Active Directory-Domäne
-   Teilnehmen an der Windows Azure AD

Für PDAs (BYOD):
-   Hinzufügen einer Microsoft-Konto Arbeit zu Windows

### <a name="azure-ad-join"></a>Azure AD-Verknüpfung

Unternehmen gehören, dass Geräte mit der lokalen Active Directory-Domäne der Organisation traditionell verbunden sind. Diese Geräte können mithilfe von Gruppenrichtlinien oder Computer-Verwaltungssoftware wie System Center Configuration Manager verwaltet werden. In Windows 10 ist es auch möglich, mit einer MDM Domäne beitreten-Geräte verwalten

Windows 10 führt eine neue Möglichkeit zum Konfigurieren und Bereitstellen von corporate Besitzer Windows-Geräte. Dieser Mechanismus wird aufgerufen Azure AD teilnehmen. Ebenso wie herkömmliche Domäne beitreten können Azure AD Join-Geräte bezeichnet und von einer Organisation verwaltet werden. Mit Azure AD beitreten authentifiziert Windows Azure AD, anstatt die Authentifizierung auf einem Domänencontroller.

Azure AD-teilnehmen können auch Unternehmen gehören Geräte automatisch registriert, und von einer MDM verwaltet werden Darüber hinaus können Azure AD beitreten auf einem PC gebrannten in der Out-of-Box-Experience (OOBE), ausgeführt werden dem können Organisationen ihre gerätebereitstellung optimieren. Ein Administrator kann festlegen, dass Benutzer eine oder mehrere Gruppen von ihren Geräten für die Verwaltung mit einer MDM registrieren sperrt Wenn die automatische Registrierung während der Teilnahme von Azure Active Directory erforderlich, um ein Benutzer konfiguriert ist, wird diese Registrierung ein erforderlicher Schritt beim Konfigurieren von Windows. Wenn die Registrierung MDM ein Fehler auftritt, wird das Gerät nicht Azure AD verknüpft werden.

> **Wichtig**  Jeder Benutzer, für die automatische Registrierung von MDM mit Azure AD Join aktiviert muss eine gültige [Azure Active Directory Premium](https://msdn.microsoft.com/library/azure/dn499825.aspx) -Lizenz zugewiesen werden.

 
### <a name="byod-scenario"></a>BYOD-Szenario

Windows 10 führt auch eine einfachere Möglichkeit zum Konfigurieren von persönlicher Geräten zu apps für Access arbeiten und Ressourcen. Benutzer können ihre Microsoft-Konto Arbeit Windows hinzufügen und einfacher und sicherer Zugriff auf die apps und Ressourcen der Organisation verfügen. Während dieses Vorgangs erkennt Azure AD, wenn die Organisation ein MDM konfiguriert wurde Wenn dies der Fall ist, versucht Windows registrieren Sie das Gerät im MDM als Teil des Datenflusses "Konto hinzufügen". Es ist wichtig, beachten Sie, dass im Fall BYOD Benutzer die MDM Begriffe Verwendung ablehnen können – in diesem Fall das Gerät nicht in MDM registriert ist und der Zugriff auf Unternehmensressourcen ist in der Regel beschränkt.

## <a name="integrated-mdm-enrollment-and-ux"></a>Integrierte MDM Registrierung und UX

Zwei Szenarien für die Azure AD MDM-Registrierung:
-   Teilnehmen an einem Gerät für Geräte unternehmenseigene Azure AD
-   Hinzufügen eines Kontos für die Arbeit mit einem persönlichen Gerät (BYOD)

In beiden Szenarien Azure AD ist verantwortlich für die Authentifizierung der Benutzer und das Gerät, der einen Gerätebezeichner überprüften eindeutige bereitstellt, die verwendet werden können fo MDM Registrierung.

In beiden Szenarien der Registrierung Ablauf bietet die Möglichkeit für den Dienst MDM, diese zu rendern ist eigenen Benutzeroberfläche, mithilfe einer Webansicht. MDM Herstellern sollten diese zum Rendern der Begriffe der verwenden (Rechtlichen), die für unterschiedlich sein können verwenden unternehmenseigene und BYOD Geräte. MDM Lieferanten können die Webansicht auch um zusätzliche Benutzeroberflächenelemente, beispielsweise, wenn Sie für eine einmalige PIN, wenn dies Teil der Organisation den Geschäftsprozess ist zu rendern.

Im Out-of-Box-Szenario ist die Webansicht 100 % Vollbild, die dem Hersteller MDM zum Zeichnen einer Edge-Edge-wünschen ermöglicht. Große Lieferumfang auch eine große Verantwortung! Es ist wichtig, dass MDM-Anbietern, die gewählten zur Einhaltung der Windows Azure AD 10 Entwurfsrichtlinien des Buchstabens zu integrieren. Dazu gehören mithilfe einer schnell Webdesigns und unter Berücksichtigung der Windows-Eingabehilfen-Richtlinien, die weiterleiten und Schaltflächen zurück, die der Logik für die Navigation ordnungsgemäß verkabelt sind. Weiter unten in diesem Thema werden weitere Details bereitgestellt.

Sie müssen für die Azure AD-Registrierung an die Arbeit für eine Active Directory-Verbunddiensten (AD FS) Azure AD-Konto gesichert, Kennwortauthentifizierung für das Intranet in den AD FS-Dienst aktivieren, wie beschrieben in Lösung \#2 in [diesem Artikel](http://go.microsoft.com/fwlink/?LinkId=690246).

Sobald ein Benutzer ein Azure AD-Konto Windows 10 hinzugefügt und in MDM registriert hat, kann die Registrierung über **Einstellungen** verwaltet &gt; **Konten** &gt; **Arbeit zugreifen**. Gerätemanagement entweder Azure AD-Teilnahme für corporate Szenarien oder BYOD Szenarien ähneln.

> **Hinweis**  Benutzer können nicht das Gerät Registrierung über die Benutzeroberfläche von **Access arbeiten** entfernt, da die Verwaltung der Azure AD gebunden ist oder Konto arbeiten.

 
### <a name="mdm-endpoints-involved-in-azure-ad-integrated-enrollment"></a>Integrierte Azure AD-Registrierung beteiligt MDM-Endpunkte

Azure AD MDM Registrierung umfasst zwei Schritte:

1.  Anzeigen von MSN Messenger, und erfassen Sie Zustimmung des Benutzers.

    Dies ist eine passive Ablauf, in dem der Benutzer in einem Webbrowser-Steuerelement (Webansicht) umgeleitet an die URL der Begriffe der Verwendung der MDM

2.  Registrieren Sie das Gerät.

    Hierbei handelt es sich um eine aktiven Flow, in dem ruft Windows OMA DM-Agent die MDM-auf das Gerät zu registrieren.

Zur Unterstützung der Azure AD-Registrierung müssen MDM Anbieter gehostet und einen Endpunkt rechtlichen Hinweise und einen MDM Registrierung Endpunkt verfügbar machen.

<a href="" id="terms-of-use-endpoint-"></a>**Begriffe des Endpunkts verwenden**   
Verwenden Sie diesen Endpunkt, um die Benutzer der Methoden zu informieren, in dem ihr Gerät von ihrer Organisation gesteuert werden kann. Die rechtlichen Hinweise Seite ist verantwortlich für die Zustimmung des Benutzers erfassen, bevor die tatsächliche Registrierung Phase beginnt.

Es ist wichtig zu verstehen, dass der rechtlichen Hinweise Ablauf auf Windows Azure AD "Black Box" ist. Die gesamte Webansicht auf Ausdrücken verwenden URL umgeleitet, und wird erwartet, dass des Benutzers nach der Genehmigung wieder (oder in einigen Fällen ablehnen) weitergeleitet werden die Begriffe. Dies ermöglicht die MDM-Hersteller, um ihre Begriffe Verwendung für verschiedene Szenarien anpassen (z. B. verschiedene Ebenen des Steuerelements werden angewendet auf BYOD im Vergleich zu unternehmenseigene Geräte) oder implementieren Benutzer-/Gruppen-basierte targeting (z. B. Benutzer in bestimmten Ländern möglicherweise gelten strengere Geräterichtlinien Management).

Der rechtlichen Hinweise Endpunkt kann verwendet werden, um zusätzliche Geschäftslogik, wie etwa eine einmalige PIN von bereitgestellten sammeln implementieren IT Gerät Registrierung zu steuern. MDM Herstellern müssen jedoch nicht den Ablauf von Ausdrücken verwenden verwenden, das Erfassen von Anmeldeinformationen des Benutzers, der zu einer stark beeinträchtigter Benutzeroberfläche führen könnte. Es ist nicht erforderlich, da Teil der MDM Integration wird sichergestellt, dass der Dienst MDM verstehen, welche von Azure AD ausgestellte Token.

<a href="" id="mdm-enrollment-endpoint"></a>**MDM Registrierung Endpunkt**  
Nachdem der Benutzer akzeptiert die Begriffe Verwendung, das Gerät in Azure Active Directory registriert ist, und die automatische Registrierung MDM beginnt.

Das folgende Diagramm veranschaulicht den allgemeinen Ablauf der tatsächlichen Registrierungsprozess beteiligt. Das Gerät wird zuerst mit Azure Active Directory registriert. Dieser Prozess weist eine eindeutige Geräte-ID des Geräts und das Gerät bietet die Möglichkeit, sich selbst mit Azure AD (Geräteauthentifizierung) zu authentifizieren. Anschließend wird das Gerät für die Verwaltung mit den MDM registriert Dies erfolgt durch Aufrufen des Registrierung Endpunkts und Registrierung für den Benutzer und Gerät anfordern. Zu diesem Zeitpunkt wurde der Benutzer authentifiziert und Gerät registriert und mit Azure Active Directory authentifiziert wurden. Die MDM in Form von Ansprüchen in einem Zugriffstoken an den Endpunkt der Registrierung präsentiert wird diese Informationen zur Verfügung gestellt.

![Ablauf von Azure Ad-Registrierung](images/azure-ad-enrollment-flow.png)

Die MDM wird erwartet, dass diese Information über das Gerät (Geräte-ID) reporting Gerät Compliance wieder in Azure Active Directory mithilfe der [Azure AD-Diagramm-API](http://go.microsoft.com/fwlink/p/?LinkID=613654)verwenden. Weiter unten in diesem Thema wird ein Beispiel für das Gerät Compliance reporting bereitgestellt.

## <a name="make-the-mdm-a-reliable-party-of-azure-ad"></a>Stellen Sie die MDM eine zuverlässige Partei von Azure Active Directory

Zur Teilnahme an des im vorherigen Abschnitt beschriebenen integrierte Registrierung Ablauf muss die MDM Zugriffstoken ausgestellt von Azure AD nutzen können. Bericht Compliance Azure AD muss die MDM authentifizieren selbst Azure AD und Autorisierung in Form von ein Zugriffstoken, das sie zum Aufrufen der [Azure AD-Diagramm-API](http://go.microsoft.com/fwlink/p/?LinkID=613654)ermöglicht zu erhalten.

### <a name="add-a-cloud-based-mdm"></a>Hinzufügen einer Cloud-basierten MDM

Ein Cloud-basierten MDM ist eine SaaS-Anwendung, die in der Cloud Device Management-Funktionen bereitstellt. Es ist eine Anwendung mit mehreren Mandanten. Diese Anwendung ist mit Azure AD im home Mandanten des Herstellers MDM registriert. Wenn ein IT-Administrator beschließt, die diese Lösung MDM verwenden, wird eine Instanz dieser Anwendung im Mandanten des Kunden sichtbar gemacht.

Der Hersteller MDM muss zuerst registrieren Sie die Anwendung in ihre private Mandanten und als Anwendung mit mehreren Mandanten markieren. Hier ein Codebeispiel aus GitHub, die erklärt, wie Sie mit mehreren Mandanten Applications Azure AD, [WepApp-WebAPI-MultiTenant-OpenIdConnect-DotNet](http://go.microsoft.com/fwlink/p/?LinkId=613661)hinzufügen.

> **Hinweis**  Wenn Sie eine vorhandene Azure AD-Tentant mit einem Azure AD-Abonnement, die Sie verwalten besitzen, führen Sie für den Anbieter MDM schrittweise Anleitung in [einem Azure AD-Mandanten hinzufügen und Azure AD-Abonnement](add-an-azure-ad-tenant-and-azure-ad-subscription.md) zu richten Sie einen Mandanten und fügen Sie ein Abonnement über der Azure-Portal verwalten Sie.

 
Die Schlüssel von der Anwendung MDM Zugriffstoken von Azure AD anfordern, werden in den Mandanten des Herstellers MDM und nicht für einzelne Kunden sichtbar verwaltet. Demselben Schlüssel wird von der Anwendung mit mehreren Mandanten MDM zum selbst Authentifizierung mit Azure AD, unabhängig von der Grundgedanke Kunden zu dem das Gerät verwalteten gehört.

Verwenden Sie die folgenden Schritte zum Registrieren einer Cloud-basierten MDM-Anwendung mit Azure AD. Zu diesem Zeitpunkt müssen Sie arbeiten mit dem Azure AD-Entwicklungsteam diese Anwendung über die Azure AD-app-Katalog verfügbar machen.

1.  Melden Sie sich an dem Azure-Verwaltungsportal mit einem Administratorkonto in Ihrem home-Mandanten.
2.  Klicken Sie im linken Navigationsbereich auf das **Active Directory**.
3.  Klicken Sie auf das Verzeichnis Mandanten in der Anwendung registriert werden soll.
    
    Stellen Sie sicher, dass Sie bei Ihrem Mandanten privat angemeldet sind.
4.  Klicken Sie auf die Registerkarte **Applications** .
5.  Klicken Sie in der Papiereinzug auf **Hinzufügen**.
6.  Klicken Sie auf **eine Anwendung, die meien Organisation entwickelt hinzufügen**.
7.  Geben Sie einen Anzeigenamen für die Anwendung, wie etwa ContosoMDM, wählen Sie **Web Application und oder Web-API**und dann auf **Weiter**.
8.  Geben Sie die Anmelde-URL für den Dienst MDM.
9.  Geben Sie für die App-ID **https://&lt;Ihrer\_Mandanten\_Namen&gt;/ContosoMDM**, klicken Sie dann auf OK.
10. Noch in der Azure-Portal, klicken Sie auf der Registerkarte " **Konfiguration** " der Anwendung.
11. Markieren einer Anwendung als **mit mehreren Mandanten**.
12. Hier finden Sie die Client-ID-Wert, und kopieren Sie die Datei.

    Sie werden dies später benötigen, wenn Sie Ihre Anwendung konfigurieren. Dieser Client-ID wird verwendet, wenn Zugriffstoken abrufen und Clientanwendungen in der Azure AD-app-Katalog hinzufügen.
13. Generieren eines Schlüssels für die Anwendung, und kopieren Sie die Datei.

    Sie benötigen diese Option, um die Azure AD-Diagramm-API auf Bericht Gerät Compliance aufzurufen. Dies wird in den nachfolgenden Abschnitt behandelt.

Weitere Informationen dazu, wie Sie die Schritte zum Registrieren der **TodoListService Web-API** in [NativeClient DotNet](http://go.microsoft.com/fwlink/p/?LinkId=613667) finden Sie eine beispielanwendung mit Azure Active Directory registrieren

### <a name="add-an-on-premises-mdm"></a>Hinzufügen einer lokalen MDM

Eine lokale MDM-Anwendung ist anders, die eine Cloud MDM Es ist eine Single-Mandanten an, die eindeutig innerhalb der Mandant des Kunden vorhanden ist. Aus diesem Grund müssen Kunden die Anwendung direkt in ihre eigenen Mandanten hinzufügen. Darüber hinaus wird jede Instanz einer Anwendung der lokalen MDM muss separat registriert werden und verfügt über einen separaten Schlüssel für die Authentifizierung mit Azure AD.

Die Kundenzufriedenheit zum Hinzufügen einer lokalen MDM zu ihrer Mandanten ähnelt dem als die Cloud-basierten MDM Es ist ein Eintrag im Azure AD app-Katalog hinzufügen, dass eine lokale MDN der Mandanten und Administratoren die erforderlichen URLs für die Registrierung und rechtlichen konfigurieren kann.

Ihre lokale MDM Produkt muss eine einfache Konfiguration verfügbar machen, in dem Administratoren der Client-ID, app-ID und den Schlüssel in ihrem Verzeichnis für die Anwendung MDM konfigurierten bereitstellen können. Können diese Client-ID und Schlüssel Anforderung Token aus dem Azure Active Directory beim Gerät Compliance-Berichte.

Weitere Informationen zum Registrieren von Anwendungen mit Azure AD finden Sie unter [Grundlagen der Registrieren einer Anwendung in Azure AD](http://go.microsoft.com/fwlink/p/?LinkId=613671).

### <a name="key-management-and-security-guidelines"></a>Verwalten von Schlüsseln und Sicherheitsrichtlinien

Die von Ihrem Dienst MDM verwendeten Anwendungsschlüssel sind eine vertrauliche Ressource. Sie sollten geschützt und regelmäßig für eine höhere Sicherheit über zurückgesetzt. Zugriffstoken erhalten von Ihrem Dienst MDM Azure AD-Diagramm-API-Aufrufen Bearer Token sind und zur Vermeidung von nicht autorisierten Offenlegung geschützt werden sollte.

Bewährte Methoden für Sicherheit finden Sie unter [Sicherheitsmaßnahmen für Windows Azure](http://go.microsoft.com/fwlink/p/?LinkId=613715).

Sie können Rollover der Anwendung von einem cloudbasierten MDM Dienst TAB-ohne Eingreifen des Kunden. Es ist ein einzelner Satz von Schlüssel mandantenübergreifend konstant von Kunden, die vom Hersteller MDM in ihren Azure AD-Mandanten verwaltet werden.

Für die lokale MDM die Schlüssel verwendet, um die Authentifizierung mit Azure AD befinden sich innerhalb der Mandant des Kunden und müssen zurückgesetzt werden, das die Kunden-Administrator. In diesem Fall sollten Sie die Anleitung für die Kunden zu Rollen über und schützen die Tasten, um verbesserte Sicherheit bereitstellen.

## <a name="publish-your-mdm-app-to-azure-ad-app-gallery"></a>Veröffentlichen Sie Ihre app MDM in Azure AD-app-Katalog


IT-Administratoren mithilfe des Azure AD-app-Katalogs hinzu ein MDM für ihre Organisation zu verwenden. Der app-Katalog ist ein rich-Speicher mit über 2400 SaaS-Clientanwendungen, die in Azure AD integriert sind.

Die folgende Abbildung zeigt, wie MDM Applikationen im Azure app-Katalog in einer Kategorie auf MDM Software dedizierte angezeigt werden.

![Hinzufügen eine app für Mdm von Azure ad](images/azure-ad-app-gallery.png)

### <a name="add-cloud-based-mdm-to-the-app-gallery"></a>Hinzufügen von Cloud-basierten MDM zu den app-Katalog

Sie sollten mit dem Azure AD-Entwicklungsteam arbeiten, wenn Ihre Anwendung MDM cloudbasierten ist. Die folgende Tabelle enthält die erforderliche Informationen zum Erstellen eines Eintrags im Azure AD-app-Katalog.

<table> 
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p><strong>ID der Anwendung</strong></p></td>
<td style="vertical-align:top"><p>Die Client-ID Ihrer MDM-App, die innerhalb Ihres Mandanten konfiguriert ist. Dies ist der eindeutige Bezeichner für Ihre app mit mehreren Mandanten.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>Herausgeber</strong></p></td>
<td style="vertical-align:top"><p>Eine Zeichenfolge, die den Herausgeber der app identifiziert.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>Die URL</strong></p></td>
<td style="vertical-align:top"><p>Eine URL zu der Angebotsseite Ihrer App, in dem die Administratoren können erhalten weiterer Informationen über die MDM-app und enthält einen Link auf der Angebotsseite Ihrer App. Diese URL ist nicht für die tatsächliche Registrierung verwendet.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>Beschreibung</strong></p></td>
<td style="vertical-align:top"><p>Eine kurze Beschreibung Ihrer App MDM, die weniger als 255 Zeichen sein muss.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>Symbole</strong></p></td>
<td style="vertical-align:top"><p>Eine Reihe von Symbolen für die MDM app Logo. Dimensionen: 45 X 45, 150 X 122, 214 X 215</p></td>
</tr>
</tbody>
</table>

 
### <a name="add-on-premises-mdm-to-the-app-gallery"></a>Hinzufügen von lokalen MDM zu den app-Katalog

Es sind keine speziellen Anforderungen für das lokale MDM dem app-Katalog hinzufügen. Ein generischer Eintrag Administrator hinzufügen eine app, die ihre Mandanten ist vorhanden.

Unterscheidet sich jedoch Key Management für lokale MDM Sie müssen die Client-ID (app-ID) und Schlüssel, der an die app MDM innerhalb der Mandant des Kunden beziehen. Diese dienen zur Autorisierung Access Azure AD-Diagramm-API und für die berichterstellung Gerät Compliance zu erhalten.

## <a name="themes"></a>Designs

Die Seiten gerendert, indem die MDM als Teil der integrierten Registrierungsprozess müssen Windows 10-Vorlagen ([Laden Sie die Windows-10-Vorlagen und CSS-Dateien](http://download.microsoft.com/download/3/E/5/3E535D52-6432-47F6-B460-4E685C5D543A/MDM-ISV_1.1.3.zip)) verwenden. Dies ist wichtig für die Registrierung während der Teilnahme von Azure AD Erfahrung in OOBE, in dem alle Seiten Edge-Edge-HTML-Seiten werden. Versuchen Sie nicht die Vorlagen kopiert, da nie die Platzierung der Schaltfläche rechten Sie erzielen. Mithilfe von freigegebenen Windows-10 sicherstellen Vorlagen eine nahtlose für den Kunden.

Es gibt 3 verschiedene Szenarien:

1.  MDM Registrierung als Teil des Azure AD in Windows OOBE teilnehmen.
2.  MDM Registrierung als Teil des Azure AD beitreten, nach Windows OOBE von **Einstellungen**.
3.  MDM Registrierung im Rahmen des Hinzufügens eines Microsoft zusammenarbeiten Konto auf einem persönlichen Gerät (BYOD).

Szenarien, 1, 2 und 3 sind in Windows 10 Pro, Windows 10 Enterprise und Windows 10 Education verfügbar. Szenario 1 und 3 sind in Windows 10 Mobile verfügbar. Unterstützung für Szenario 1 wurde in Windows 10 Mobile Version 1511 hinzugefügt.

Die CSS-Dateien, die von Microsoft bereitgestellten enthält Informationen zur Version, und es wird empfohlen, dass Sie die neueste Version verwenden. Es gibt separate CSS-Dateien für Desktop- und mobilen Geräten, OOBE, und Post-OOBE auftritt. [Laden Sie die Windows-10-Vorlagen und CSS-Dateien](http://download.microsoft.com/download/3/E/5/3E535D52-6432-47F6-B460-4E685C5D543A/MDM-ISV_1.1.3.zip).

### <a name="using-themes"></a>Verwendung von Designs

Vordefinierte Designs je nach Szenario muss eine Seite MDM entsprechen, die angezeigt wird. Beispielsweise ist die Kopfzeile CXH HOSTHTTP FRX, das Szenario OOBE ist, muss die Seite ein dunkles Design mit blaue Hintergrundfarbe unterstützen, die WinJS Datei Benutzeroberfläche dark.css Ver 4.0 und Oobe desktop.css Ver 1.0.4 verwendet.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>CXH-HOST (HTTP-HEADER)</th>
<th>Senario</th>
<th>Hintergrunddesign</th>
<th>WinJS</th>
<th>Szenario CSS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">FRX</td>
<td style="vertical-align:top">OOBE</td>
<td style="vertical-align:top">Dunkles Design + blaue Hintergrundfarbe</td>
<td style="vertical-align:top">Dateiname: Ui-dark.css</td>
<td style="vertical-align:top">Dateiname: Oobe-dekstop.css</td>
</tr>
<tr class="even">
<td style="vertical-align:top">MOSET</td>
<td style="vertical-align:top">Einstellungen /
<p>POST OOBE</p></td>
<td style="vertical-align:top">Helles Design</td>
<td style="vertical-align:top">Dateiname: Ui-light.css</td>
<td style="vertical-align:top">Dateiname: Einstellungen-desktop.css</td>
</tr>
</tbody>
</table>

 
## <a name="terms-of-use-protocol-semantics"></a>Ausdrücke verwenden Protokoll Semantik

Der rechtlichen Hinweise Endpunkt wird vom MDM Server gehostet. Bei Ablauf Protokoll Azure AD teilnehmen führt Windows eine ganzseitige Umleitung an diesen Endpunkt. Auf diese Weise können die MDM zum Anzeigen von Bedingungen, die anwenden und ermöglicht Benutzern die akzeptieren oder Ablehnen der Registrierung zugeordnet Begriffe. Nachdem der Benutzer die Begriffe annimmt, leitet der MDM wieder auf Windows für den Registrierungsprozess, um den Vorgang fortzusetzen.

### <a name="redirect-to-the-terms-of-use-endpoint"></a>Umleiten Sie an den Endpunkt der rechtlichen Hinweise

Hierbei handelt es sich um eine ganze Seite Umleitung an den von der MDM gehostet Begriffe des Benutzer-Endpunkt Es folgt ein Beispiel-URL, Https:<span></span>/ / fabrikam.contosomdm.com/TermsOfUse.

Die folgenden Parameter werden in der Abfragezeichenfolge übergeben:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>redirect_uri</p></td>
<td style="vertical-align:top"><p>Nachdem der Benutzer annimmt oder Ausdrücken verwenden ablehnt, wird der Benutzer zu dieser URL umgeleitet.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Client-Anforderung-id</p></td>
<td style="vertical-align:top"><p>Eine GUID, die zum Korrelieren Protokolle Diagnosedaten und Debuginformationen Zwecken verwendet wird. Verwenden Sie diesen Parameter zum Melden oder Nachverfolgen den Status der Anforderung Registrierung zu helfen, die Ursache bei Fehlern finden.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>API-version</p></td>
<td style="vertical-align:top"><p>Gibt die Version des Protokolls vom Client angefordert. Dies bietet einen Mechanismus zur Unterstützung der Version Überarbeitungen des Protokolls.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Modus</p></td>
<td style="vertical-align:top"><p>Gibt an, dass das Gerät im Unternehmen gehören, wenn Mode = Azureadjoin. Dieser Parameter ist nicht für BYOD Geräte vorhanden.</p></td>
</tr>
</tbody>
</table>

 
### <a name="access-token"></a>Zugriffstoken

Ein Zugriffstoken Bearer wird ausgegeben, von Azure AD Authorization-Header der HTTP-Anforderung übergeben wird. Hier ist eine übliche Format:

**Autorisierung: Bearer** CI6MTQxmCF5xgu6yYcmV9ng6vhQfaJYw...

Die folgenden Ansprüche werden in das Zugriffstoken an den Endpunkt der Begriffe der Verwendung von Windows übergeben erwartet:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Objekt-ID</p></td>
<td style="vertical-align:top"><p>Bezeichner des Benutzerobjekts, des authentifizierten Benutzers entspricht.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>UPN</p></td>
<td style="vertical-align:top"><p>Eine Forderung, die den Benutzerprinzipalnamen (UPN) des authentifizierten Benutzers enthält.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>TID</p></td>
<td style="vertical-align:top"><p>Eine Forderung, die Mandanten-ID des Mandanten darstellt. Im obigen Beispiel ist es Fabrikam.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Ressource</p></td>
<td style="vertical-align:top"><p>Ein sicherer URL, die MDM Anwendung darstellt. Beispiel, Https:<span></span>/ / fabrikam.contosomdm.com.</p></td>
</tr>
</tbody>
</table>
 
> **Hinweis**  Es ist kein Gerät ID Forderung im Zugriffstoken, da das Gerät nicht noch zu diesem Zeitpunkt registriert werden kann.

 
Zum Abrufen der Liste der Gruppenmitgliedschaften für den Benutzer können Sie die [Azure AD-Diagramm-API](http://go.microsoft.com/fwlink/p/?LinkID=613654)verwenden.

Es folgt eine Beispiel-URL ein.

``` syntax
https://fabrikam.contosomdm.com/TermsOfUse?redirect_uri=ms-appx-web://ContosoMdm/ToUResponse&client-request-id=34be581c-6ebd-49d6-a4e1-150eff4b7213&api-version=1.0
Authorization: Bearer eyJ0eXAiOi
```

Wird erwartet, dass die MDM überprüfen Sie die Signatur des Zugriffstokens zum sicherstellen, dass es Azure AD ausgestellt wurde, und stellen Sie sicher, dass dieser Empfänger geeignet ist.

### <a name="terms-of-use-content"></a>Begriffe von Inhalt verwenden

Die MDM möglicherweise andere zusätzliche leitet bei Bedarf vor dem Anzeigen des Inhalts der rechtlichen Hinweise für den Benutzer ausführen. Der entsprechende rechtlichen Inhalte sollte mit dem Anrufer (Windows) zurückgegeben werden, sodass es für den Endbenutzer in das Webbrowser-Steuerelement angezeigt werden kann.

Die Inhalte der rechtlichen Hinweise sollte die folgenden Schaltflächen enthalten:

-   **Accept** - Benutzers akzeptiert die Begriffe Verwendung und mit Registrierung wird fortgesetzt.
-   **Ablehnen** – der Benutzer ablehnt und der Registrierungsprozess beendet.

Der rechtlichen Hinweise Inhalt muss konsistent mit dem Design für die anderen Seiten gerendert werden, während dieses Vorgangs verwendet wird.

### <a name="terms-of-use-endpoint-processing-logic"></a>Rechtliche Hinweise Verwendung Endpunkt Verarbeitungslogik

Zu diesem Zeitpunkt ist der Benutzer auf der rechtlichen Hinweise Seite während OOBE oder von der Einstellung Erfahrungen angezeigt. Der Benutzer hat die folgenden Optionen auf der Seite:

-   Der **Benutzer klickt auf die Schaltfläche Accept** - die MDM müssen auf die Umleitung angegebenen URI umleiten\_Uri-Parameter in der eingehenden Anforderung. Die folgenden Abfragezeichenfolgen-Parameter werden erwartet:
    -   **IsAccepted** - diese obligatorisch boolescher Wert muss festgelegt werden, auf "true".
    -   **OpaqueBlob** - Erforderlicher Parameter, wenn der Benutzer annimmt. Die MDM können diese stellen einige Informationen an den Endpunkt der Registrierung zur Verfügung. Der Wert beibehalten hier zur Verfügung gestellt wird am Endpunkt Registrierung bleibt unverändert. Die MDM kann diesen Parameter Korrelation Zwecken verwenden.
    -   Es folgt eine Beispiel-Umleitung - ms-Appx-web://MyApp1/ToUResponse? OpaqueBlob = Wert & IsAccepted = True
-   Der **Benutzer klickt auf die Schaltfläche Ablehnen** – der MDM müssen auf umleiten angegebenen URI umleiten\_Uri in der eingehenden Anforderung. Die folgenden Abfragezeichenfolgen-Parameter werden erwartet:
    -   **IsAccepted** - dieser obligatorisch boolescher Wert muss auf False festgelegt sein. Dies gilt auch dann, wenn der Benutzer die Begriffe Verwendung übersprungen.
    -   **OpaqueBlob** - dieser Parameter wird nicht verwendet werden, da die Registrierung mit einer Fehlermeldung, die dem Benutzer angezeigt wird, beendet wurde erwartet.

Benutzer überspringen MSN Messenger, wenn sie ihr Gerät ein Konto bei Microsoft Arbeit hinzugefügt werden. Allerdings kann nicht es während des Aktivierungsvorgangs Azure AD teilnehmen überspringen. Die Schaltfläche Ablehnen muss im Azure AD Join-Prozess nicht angezeigt werden, da MDM Registrierung kann nicht vom Benutzer abgelehnt werden, wenn vom Administrator für die Teilnahme zu Azure AD konfiguriert.

Es wird empfohlen, dass Sie die Client-Anforderung-Id-Parameter in der Abfragezeichenfolge im Rahmen dieser Umleitungsantwort senden.

### <a name="terms-of-use-error-handling"></a>Begriffe der Verwendung Fehlerbehandlung

Wenn während der Verarbeitung der Verwendung der Begriffe ein Fehler aufgetreten ist, kann die MDM zwei Parameter – ein Fehler und der Fehler zurückgeben\_Parameter Description in seiner Redirect-Anforderung an den Windows sichern. Beachten Sie, dass die URL codiert wird, und der Inhalt des Fehlers\_Beschreibung Englisch als nur-Text sein sollte. Dieser Text ist nicht sichtbar für den Endbenutzer und Lokalisierung der Fehlermeldung Beschreibung ist daher kein Bedeutung.

Nachfolgend finden Sie im URL-Format:

``` syntax
HTTP/1.1 302
Location:
<redirect_uri>?error=access_denied&error_description=Access%20is%20denied%2E


Example:
HTTP/1.1 302 
Location: ms-appx-web://App1/ToUResponse?error=access_denied&error_description=Acess%20is%20denied%2E
```

Die folgende Tabelle zeigt die Fehlercodes.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ursache</th>
<th>HTTP-status</th>
<th>Fehler</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>API-version</p></td>
<td style="vertical-align:top"><p>302</p></td>
<td style="vertical-align:top"><p>invalid_request</p></td>
<td style="vertical-align:top"><p>nicht unterstützte version</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Mandanten oder Benutzer Daten handelt es sich um Missingor anderen erforderlich, dass die erforderlichen Komponenten für die Registrierung des Geräts nicht erfüllt sind</p></td>
<td style="vertical-align:top"><p>302</p></td>
<td style="vertical-align:top"><p>unauthorized_client</p></td>
<td style="vertical-align:top"><p>nicht autorisierter Benutzer oder des Mandanten</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Fehler bei der Azure AD-token-Überprüfung</p></td>
<td style="vertical-align:top"><p>302</p></td>
<td style="vertical-align:top"><p>unauthorized_client</p></td>
<td style="vertical-align:top"><p>unauthorized_client</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Interner Dienstfehler</p></td>
<td style="vertical-align:top"><p>302</p></td>
<td style="vertical-align:top"><p>server_error</p></td>
<td style="vertical-align:top"><p>Interner Dienstfehler</p></td>
</tr>
</tbody>
</table>

 
## <a name="enrollment-protocol-with-azure-ad"></a>Registrierung Protokoll mit Azure AD

Mit Azure integrierte MDM Registrierung gibt es keine Discovery Phase und Such-URL ist direkt an das System vom übergebenen Azure. Die folgende Tabelle zeigt den Vergleich zwischen der herkömmlichen und Azure Registrierung für die.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Detail</th>
<th>Herkömmliche MDM-Registrierung</th>
<th>Azure AD-Join (firmeneigenen Gerät)</th>
<th>Azure AD hinzufügen ein Kontos Arbeit (Gerät im Besitz des Benutzers)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>MDM-AutoErmittlung mit e-Mail-Adresse zum Abrufen von MDM Such-URL</p></td>
<td style="vertical-align:top"><p>Registrierung</p></td>
<td style="vertical-align:top"><p>Nicht zutreffend</p>
<p>In Azure bereitgestellte Such-URL</p></td>
<td style="vertical-align:top"><p></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>MDM Such-URL verwendet</p></td>
<td style="vertical-align:top"><p>Registrierung</p>
<p>Erneuerung der Registrierung</p>
<p>ROBO</p></td>
<td style="vertical-align:top"><p>Registrierung</p>
<p>Erneuerung der Registrierung</p>
<p>ROBO</p></td>
<td style="vertical-align:top"><p>Registrierung</p>
<p>Erneuerung der Registrierung</p>
<p>ROBO</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Ist MDM Registrierung erforderlich?</p></td>
<td style="vertical-align:top"><p>Ja</p></td>
<td style="vertical-align:top"><p>Ja</p></td>
<td style="vertical-align:top"><p>Nein</p>
<p>Benutzer kann ablehnen.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Authentifizierungstyp</p></td>
<td style="vertical-align:top"><p>Lokale Verwaltungs</p>
<p>Verbund</p>
<p>Zertifikat</p></td>
<td style="vertical-align:top"><p>Verbund</p></td>
<td style="vertical-align:top"><p>Verbund</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>EnrollmentPolicyServiceURL</p></td>
<td style="vertical-align:top"><p>Optional (alle Authentifizierung)</p></td>
<td style="vertical-align:top"><p>Optional (alle Authentifizierung)</p>
<p></p></td>
<td style="vertical-align:top"><p>Optional (alle Authentifizierung)</p>
<p></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>EnrollmentServiceURL</p></td>
<td style="vertical-align:top"><p>Erforderlich (alle Authentifizierung)</p></td>
<td style="vertical-align:top"><p>(Alle Authentifizierung) verwendet</p></td>
<td style="vertical-align:top"><p>(Alle Authentifizierung) verwendet</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>EnrollmentServiceURL enthält, Betriebssystemversion, Betriebssystemplattform und andere Attribute von MDM Such-URL bereitgestellt</p></td>
<td style="vertical-align:top"><p>Dringend empfohlen</p></td>
<td style="vertical-align:top"><p>Dringend empfohlen</p></td>
<td style="vertical-align:top"><p>Dringend empfohlen</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>AuthenticationServiceURL verwendet</p></td>
<td style="vertical-align:top"><p>Verwendete (Federated Authentifizierung)</p></td>
<td style="vertical-align:top"><p>Übersprungen</p></td>
<td style="vertical-align:top"><p>Übersprungen</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>BinarySecurityToken</p></td>
<td style="vertical-align:top"><p>Benutzerdefinierte pro MDM</p></td>
<td style="vertical-align:top"><p>Azure AD ausgestellten token</p></td>
<td style="vertical-align:top"><p>Azure AD ausgestellten token</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>EnrollmentType</p></td>
<td style="vertical-align:top"><p>Vollständige</p></td>
<td style="vertical-align:top"><p>Gerät</p></td>
<td style="vertical-align:top"><p>Vollständige</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Registrierten Zertifikattyp</p></td>
<td style="vertical-align:top"><p>Benutzerzertifikat</p></td>
<td style="vertical-align:top"><p>Gerät-Zertifikat</p></td>
<td style="vertical-align:top"><p>Benutzerzertifikat</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Registrierten Zertifikatspeicher</p></td>
<td style="vertical-align:top"><p>Meine / Benutzer</p></td>
<td style="vertical-align:top"><p>Meine / System</p></td>
<td style="vertical-align:top"><p>Meine / Benutzer</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>CSR Antragstellername</p></td>
<td style="vertical-align:top"><p>Benutzerprinzipalname</p></td>
<td style="vertical-align:top"><p>Geräte-ID</p></td>
<td style="vertical-align:top"><p>Benutzerprinzipalname</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>EnrollmentData Begriffe der Verwendung eines BLOBs als AdditionalContext für EnrollmentServiceURL</p></td>
<td style="vertical-align:top"><p>Nicht unterstützt</p></td>
<td style="vertical-align:top"><p>Unterstützt</p></td>
<td style="vertical-align:top"><p>Unterstützt</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Kryptografiedienstanbieter zugegriffen werden, während der Registrierung</p></td>
<td style="vertical-align:top"><p>Windows-10-Unterstützung:</p>
<ul>
<li>DMClient</li>
<li>CertificateStore</li>
<li>RootCATrustedCertificates</li>
<li>ClientCertificateInstall</li>
<li>EnterpriseModernAppManagement</li>
<li>PassportForWork</li>
<li>Richtlinie</li>
<li>ANWENDUNG W7</li>
</ul>
<p>Legacy-Unterstützung:</p>
<ul>
<li>EnterpriseAppManagement (Windows Phone 8.1)</li>
</ul></td>
<td style="vertical-align:top"><p>identisch mit herkömmlichen MDM-Registrierung</p></td>
<td style="vertical-align:top"><p>identisch mit herkömmlichen MDM-Registrierung</p></td>
</tr>
</tbody>
</table>

 

## <a name="management-protocol-with-azure-ad"></a>Management-Protokoll mit Azure AD

Es gibt zwei verschiedene MDM Registrierung verwendete Typen, die Vorteile der Integration von Azure AD nutzen, und stellen Sie daher von Azure Active Directory-Benutzer und Gerät Identitäten aus. Je nach der Registrierung Typ müssen MDM-Dienst auf einem einzelnen Benutzer oder mehrere Benutzer verwalten.

<a href="" id="multiple-user-management-for-azure-ad-joined-devices"></a>**Benutzerverwaltung mehrerer für Azure AD verbunden Geräte**  
In diesem Szenario, angewendet die Registrierung MDM jeder Azure AD wird, Benutzer, der sich die Azure AD Gerät verbunden – diese Registrierung Anruftyp, ein Gerät Registrierung oder eine Registrierung Rückschreiben durch mehrere Benutzer. Der Verwaltungsserver kann die Identität des Benutzers bestimmen, Schluss kommen, welche Richtlinien für diesen Benutzer ausgelegt sind und entsprechende Richtlinien an das Gerät gesendet. Damit können Verwaltungsserver zum aktuellen Benutzer zu identifizieren, der an das Gerät angemeldet ist, verwendet der OMA DM-Client die Azure AD-Benutzer-Token. Jede Sitzung Management enthält einen zusätzlichen HTTP-Header, der ein Azure AD-Benutzer-Token enthält. Diese Informationen werden im DM-Paket an den Verwaltungsserver gesendet bereitgestellt. Jedoch ist in einigen Fällen Azure AD-Benutzer Token nicht über an den Verwaltungsserver gesendet. Ein solches Szenario tritt unmittelbar nach der Registrierung für die MDM abgeschlossen ist, während der Vorgang des Beitritts Azure AD. Bis Azure AD Join abgeschlossen ist und Azure AD-Benutzer sich bei dem Computer meldet, ist Azure AD-Benutzertoken nicht an den Prozess OMA DM verfügbar. In der Regel nach Abschluss MDM Registrierung Azure AD-Benutzer meldet sich am Computer und die anfängliche Management-Sitzung enthält kein Azure AD-Benutzer-Token. Der Verwaltungsserver sollte überprüfen, ob das Token fehlt und nur Geräterichtlinien in diesem Fall senden. Ein weiterer Grund für ein fehlenden Azure AD-Token in der Nutzlast OMA DM ist, wenn ein Gastbenutzer an dem Gerät angemeldet ist.

<a href="" id="adding-a-work-account-and-mdm-enrollment-to-a-device"></a>**Hinzufügen von einem Konto Arbeit und MDM Registrierung zu einem Gerät**  
In diesem Szenario wird ein einzelner Benutzer, der anfänglich hinzugefügt sein Konto Arbeit und das Gerät registriert die Registrierung MDM betrifft. Bei dieser Art der Registrierung kann der Verwaltungsserver Azure AD-Token ignorieren, die während der Management-Sitzung gesendet werden kann. Ob Azure AD-Token vorhanden ist, sendet der Verwaltungsserver Richtlinien für Benutzer und Gerät an das Gerät.

<a href="" id="evaluating-azure-ad-user-tokens"></a>**Auswerten von Azure AD-Benutzertoken**  
Das Azure AD-Token ist im HTTP-Authorization-Header im folgenden Format:

``` syntax
Authorization:Bearer <Azure AD User Token Inserted here>
```

Zusätzlicher Ansprüche können wie im Azure AD-Token vorhanden sein:

-   Benutzer - Benutzer derzeit angemeldeten
-   Gerät Compliance - festgelegte Wert der der Dienst MDM in Azure
-   Geräte-ID - identifiziert das Gerät, das eingecheckt wird
-   Mandanten-ID

Ausgestellt von Azure AD-Zugriffstoken werden JSON Web Token (JWTs). Ein gültiges Token JWT wird am Endpunkt MDM Registrierung Initiieren der Registrierung von Windows angezeigt. Es gibt einige Optionen für die Token ausgewertet werden soll:

-   Verwenden Sie die Erweiterung JWT Token Handler für WIF zum Überprüfen der Inhalt des Zugriffstokens und Extrahieren von Ansprüchen für die Verwendung erforderlich. Weitere Informationen finden Sie unter [JSON Web Token Handler](http://go.microsoft.com/fwlink/p/?LinkId=613820).
-   Finden Sie in der Azure AD-Authentifizierung Codebeispiele herunter, die ein Beispiel für die Arbeit mit Zugriffstoken abzurufen. Ein Beispiel finden Sie unter [NativeClient DotNet](http://go.microsoft.com/fwlink/p/?LinkId=613667).

## <a name="device-alert-1224-for-azure-ad-user-token"></a>Gerät für Azure AD-Benutzertoken Alert 1224

Eine Benachrichtigung wird gesendet, wenn die Sitzung DM startet und eine Azure AD-Benutzer angemeldet ist. Die Benachrichtigung wird gesendet, in der OMA DM Pkg\#1. Es folgt ein Beispiel:

``` syntax
Alert Type: com.microsoft/MDM/AADUserToken
 
Alert sample: 
<SyncBody> 
 <Alert> 
  <CmdID>1</CmdID> 
  <Data>1224</Data> 
  <Item> 
   <Meta> 
    <Type xmlns=”syncml:metinf”>com.microsoft/MDM/AADUserToken</Type> 
    <Format xmlns=”syncml:metinf”>chr</Format> 
   </Meta> 
   <Data>UserToken inserted here</Data> 
  </Item> 
 </Alert> 
 … other xml tags … 
</SyncBody> 
```

## <a name="determine-when-a-user-is-logged-in-through-polling"></a>Bestimmen Sie, wenn ein Benutzer über Abruf angemeldet ist

Eine Warnung senden an den Server MDM in DM-Paket ist\#1.

-   Benachrichtigungstyp - com.microsoft/MDM/LoginStatus
-   Format - chr warnen
-   Warnen, Daten - Status der Anmeldeinformationen für das aktuelle aktive angemeldeten Benutzer bereitzustellen.
    -   Angemeldeten Benutzer, der ein Azure AD-Konto - vordefinierter Text hat: Benutzer.
    -   Angemeldeten Benutzer ohne ein Azure AD-Konto-vordefinierte Text: andere Personen.
    -   Keine aktiven Benutzer - vordefinierter Text: keine

Es folgt ein Beispiel.

``` syntax
<SyncBody> 
 <Alert> 
  <CmdID>1</CmdID> 
  <Data>1224</Data> 
  <Item> 
   <Meta> 
    <Type xmlns=”syncml:metinf”>com.microsoft/MDM/LoginStatus</Type> 
    <Format xmlns=”syncml:metinf”>chr</Format> 
   </Meta> 
   <Data>user</Data> 
  </Item> 
 </Alert> 
 … other xml tags … 
</SyncBody>
```

## <a name="report-device-compliance-to-azure-ad"></a>Bericht Gerät Compliance Azure AD

Nachdem ein Gerät mit der MDM für Management registriert ist, werden auf dem Gerät Unternehmensrichtlinien, die von der IT-Administrator konfiguriert erzwungen. Die Gerät Einhaltung konfigurierten Richtlinien durch die MDM ausgewertet und dann Azure AD gemeldet. In diesem Abschnitt wird den Diagramm-API-Aufruf, den Sie verwenden können, um ein Compliance-Gerätestatus Azure AD melden behandelt.

Ein Beispiel, das veranschaulicht, wie ein MDM ein Zugriffstoken mit OAuth 2.0-Client abrufen kann\_Anmeldeinformationen erteilen Typ, finden Sie unter [Filterdaemon\_CertificateCredential DotNet](http://go.microsoft.com/fwlink/p/?LinkId=613822).

-   **Cloud-basierten MDM** - Wenn Ihr Produkt einer Cloud-basierten mehrinstanzenfähige MDM-Dienst ist, müssen Sie einen einzelnen Schlüssel für den Dienst innerhalb Ihres Mandanten. Verwenden Sie diesen Schlüssel des MDM-Diensts mit Azure AD authentifiziert, um die Autorisierung zu erhalten.
-   **Der lokale MDM** - Wenn Ihr Produkt einer lokalen MDM ist, müssen Kunden Ihr Produkt mit dem Schlüssel verwendet, um die Authentifizierung mit Azure AD konfigurieren. Dies ist, da jede lokale Instanz des Produkts MDM einen anderen Mandanten-spezifische Schlüssel verfügt. Zu diesem Zweck müssen Sie möglicherweise eine einfache Konfiguration in Ihrem MDM Produkt verfügbar machen, die Administratoren geben Sie die Taste, um zur Authentifizierung mit Azure Active Directory verwendet werden können.

### <a name="use-azure-ad-graph-api"></a>Verwenden von Azure AD-Diagramm-API

Der folgende Beispiel-REST-API-Aufruf veranschaulicht, wie ein MDM API Azure AD-Diagramm zu den Bericht Compliance Status eines Geräts derzeit von ihm verwalteten verwenden kann.

``` syntax
Sample Graph API Request: 

PATCH https://graph.windows.net/contoso.com/devices/db7ab579-3759-4492-a03f-655ca7f52ae1?api-version=beta HTTP/1.1 
Authorization: Bearer eyJ0eXAiO……… 
Accept: application/json 
Content-Type: application/json 
{  “isManaged”:true,  
   “isCompliant”:true 
} 
```

Dabei gilt Folgendes:

-   **"contoso.com"** – ist dies der Name des Azure AD-Mandanten zu, den Verzeichnis das Gerät hinzugefügt wurde.
-   **db7ab579-3759-4492-a03f-655ca7f52ae1** – ist dies die Geräte-ID für das Gerät, dessen Informationen zur Einhaltung Azure AD gemeldet werden.
-   **eyJ0eXAiO**... – Dies ist das Bearer Zugriffstoken ausgestellt von Azure Active Directory für die MDM, die autorisiert den MDM Azure AD-Diagramm-API-aufrufen. Das Zugriffstoken wird im HTTP-Authorization-Header der Anforderung platziert.
-   **IsManaged** und **IsCompliant** - diese boolesche Attribute Kompatibilitätsstatus angibt.
-   **api-Version** - Verwendung dieser Parameter, welche Version des Diagramms API angefordert wird.

Antwort:

-   Erfolg: HTTP 204 ohne Inhalt.
-   / Fehler - HTTP 404 nicht gefunden. Dieser Fehler möglicherweise zurückgegeben werden soll, wenn das angegebene Gerät oder des Mandanten nicht gefunden werden kann.

## <a name="data-loss-during-unenrollment-from-azure-active-directory-join"></a>Datenverlust während einer Unenrollment von Azure Active Directory teilnehmen

Wenn ein Benutzer in MDM über Azure Active Directory beitreten registriert wird und anschließend die Registrierung getrennt, besteht keine Warnung, dass der Benutzer Windows Informationen Schutz (WIP) Daten verloren. Die Nachricht Trennen von wird Datenverlust WIP nicht angegeben werden.

![Aadj unenerollment](images/azure-ad-unenrollment.png)

## <a name="error-codes"></a>Fehlercodes

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Code</th>
<th>ID</th>
<th>Fehlermeldung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top">0x80180001</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / MENROLL_E_DEVICE_MESSAGE_FORMAT_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180002</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / MENROLL_E_DEVICE_AUTHENTICATION_ERROR</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180003</td>
<td style="vertical-align:top">&quot;IdErrorAuthorizationFailure&quot;, / / MENROLL_E_DEVICE_AUTHORIZATION_ERROR</td>
<td style="vertical-align:top"><p>Dieser Benutzer ist nicht autorisiert zu registrieren. Sie können versuchen, wiederholen Sie diesen Vorgang, oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180004</td>
<td style="vertical-align:top">&quot;IdErrorMDMCertificateError&quot;, / / MENROLL_E_DEVICE_CERTIFCATEREQUEST_ERROR</td>
<td style="vertical-align:top"><p>Es ist ein Zertifikat aufgetreten. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180005</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / MENROLL_E_DEVICE_CONFIGMGRSERVER_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180006</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / MENROLL_E_DEVICE_CONFIGMGRSERVER_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180007</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / MENROLL_E_DEVICE_INVALIDSECURITY_ERROR</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180008</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / MENROLL_E_DEVICE_UNKNOWN_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180009</td>
<td style="vertical-align:top">&quot;IdErrorAlreadyInProgress&quot;, / / MENROLL_E_ENROLLMENT_IN_PROGRESS</td>
<td style="vertical-align:top"><p>Eine andere Registrierung wird gerade durchgeführt. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x8018000A</td>
<td style="vertical-align:top">&quot;IdErrorMDMAlreadyEnrolled&quot;, / / MENROLL_E_DEVICE_ALREADY_ENROLLED</td>
<td style="vertical-align:top"><p>Dieses Gerät ist bereits registriert. Erhalten Sie vom Systemadministrator mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x8018000D</td>
<td style="vertical-align:top">&quot;IdErrorMDMCertificateError&quot;, / / MENROLL_E_DISCOVERY_SEC_CERT_DATE_INVALID</td>
<td style="vertical-align:top"><p>Es ist ein Zertifikat aufgetreten. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x8018000E</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / MENROLL_E_PASSWORD_NEEDED</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x8018000F</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / MENROLL_E_WAB_ERROR</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180010</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / MENROLL_E_CONNECTIVITY</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180012</td>
<td style="vertical-align:top">&quot;IdErrorMDMCertificateError&quot;, / / MENROLL_E_INVALIDSSLCERT</td>
<td style="vertical-align:top"><p>Es ist ein Zertifikat aufgetreten. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180013</td>
<td style="vertical-align:top">&quot;IdErrorDeviceLimit&quot;, / / MENROLL_E_DEVICECAPREACHED</td>
<td style="vertical-align:top"><p>Scheint, es sind zu viele Geräte oder Benutzer für dieses Konto. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180014</td>
<td style="vertical-align:top">&quot;IdErrorMDMNotSupported&quot;, / / MENROLL_E_DEVICENOTSUPPORTED</td>
<td style="vertical-align:top"><p>Dieses Feature wird nicht unterstützt. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180015</td>
<td style="vertical-align:top">&quot;IdErrorMDMNotSupported&quot;, / / MENROLL_E_NOTSUPPORTED</td>
<td style="vertical-align:top"><p>Dieses Feature wird nicht unterstützt. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180016</td>
<td style="vertical-align:top">&quot;IdErrorMDMRenewalRejected&quot;, / / MENROLL_E_NOTELIGIBLETORENEW</td>
<td style="vertical-align:top"><p>Der Server hat die Anforderung nicht akzeptiert. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180017</td>
<td style="vertical-align:top">&quot;IdErrorMDMAccountMaintenance&quot;, / / MENROLL_E_INMAINTENANCE</td>
<td style="vertical-align:top"><p>Der Dienst ist in der Wartung. Sie können versuchen, zu einem späteren Zeitpunkt erneut dafür, oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x80180018</td>
<td style="vertical-align:top">&quot;IdErrorMDMLicenseError&quot;, / / MENROLL_E_USERLICENSE</td>
<td style="vertical-align:top"><p>Es wurde ein Fehler mit der Lizenz. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x80180019</td>
<td style="vertical-align:top">&quot;IdErrorInvalidServerConfig&quot;, / / MENROLL_E_ENROLLMENTDATAINVALID</td>
<td style="vertical-align:top"><p>Sieht wie der Server nicht ordnungsgemäß konfiguriert ist. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">&quot;rejectedTermsOfUse&quot;</td>
<td style="vertical-align:top">&quot;idErrorRejectedTermsOfUse&quot;</td>
<td style="vertical-align:top"><p>Ihre Organisation erfordert, dass Sie die Begriffe Verwendung zustimmen. Versuchen Sie es erneut, oder Support-Mitarbeiter Weitere Informationen erhalten.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c0001</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / DSREG_E_DEVICE_MESSAGE_FORMAT_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c0002</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / DSREG_E_DEVICE_AUTHENTICATION_ERROR</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c0003</td>
<td style="vertical-align:top">&quot;IdErrorAuthorizationFailure&quot;, / / DSREG_E_DEVICE_AUTHORIZATION_ERROR</td>
<td style="vertical-align:top"><p>Dieser Benutzer ist nicht autorisiert zu registrieren. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c0006</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / DSREG_E_DEVICE_INTERNALSERVICE_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c000B</td>
<td style="vertical-align:top">&quot;IdErrorUntrustedServer&quot;, / / DSREG_E_DISCOVERY_REDIRECTION_NOT_TRUSTED</td>
<td style="vertical-align:top">Der Server hergestellt wird, ist nicht vertrauenswürdig. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c000C</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / DSREG_E_DISCOVERY_FAILED</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c000E</td>
<td style="vertical-align:top">&quot;IdErrorDeviceLimit&quot;, / / DSREG_E_DEVICE_REGISTRATION_QUOTA_EXCCEEDED</td>
<td style="vertical-align:top"><p>Scheint, es sind zu viele Geräte oder Benutzer für dieses Konto. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c000F</td>
<td style="vertical-align:top">&quot;IdErrorDeviceRequiresReboot&quot;, / / DSREG_E_DEVICE_REQUIRES_REBOOT</td>
<td style="vertical-align:top"><p>Zum Abschließen der Registrierung Gerät ist ein Neustart erforderlich.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c0010</td>
<td style="vertical-align:top">&quot;IdErrorInvalidCertificate&quot;, / / DSREG_E_DEVICE_AIK_VALIDATION_ERROR</td>
<td style="vertical-align:top"><p>Anscheinend verwenden Sie ein gültiges Zertifikat verfügen. Wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c0011</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / DSREG_E_DEVICE_ATTESTATION_ERROR</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c0012</td>
<td style="vertical-align:top">&quot;IdErrorServerConnectivity&quot;, / / DSREG_E_DISCOVERY_BAD_MESSAGE_ERROR</td>
<td style="vertical-align:top"><p>Fehler bei der Kommunikation mit dem Server. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator mit den Fehlercode {0</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top">0x801c0013</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / DSREG_E_TENANTID_NOT_FOUND</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top">0x801c0014</td>
<td style="vertical-align:top">&quot;IdErrorAuthenticationFailure&quot;, / / DSREG_E_USERSID_NOT_FOUND</td>
<td style="vertical-align:top"><p>Es konnte keine Authentifizierung Ihr Konto oder Gerät. Sie können versuchen, wiederholen Sie diesen Vorgang oder wenden Sie sich an Ihren Systemadministrator, mit dem Fehlercode {0}.</p></td>
</tr>
</tbody>
</table>

 

 





