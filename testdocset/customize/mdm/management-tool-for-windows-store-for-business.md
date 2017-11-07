---
title: "Verwaltungstool für den Windows Store for Business"
description: "Windows Store für Business hat einen neuen Webdienst, der für das Unternehmen zu erwerben, verwalten und Verteilen von Anwendungen in einer Sammeloperation entwickelt."
MS-HAID:
- p\_phdevicemgmt.business\_store\_portal\_management\_tool
- p\_phDeviceMgmt.management\_tool\_for\_windows\_store\_for\_business
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0E39AE85-1703-4B24-9A7F-831C6455068F
ms.openlocfilehash: 3099b195715898920867406ef384b3bf482ecdf0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="management-tool-for-the-windows-store-for-business"></a>Verwaltungstool für den Windows Store for Business

Windows Store für Business hat einen neuen Webdienst für das Unternehmen zu erwerben, verwalten und Verteilen von Anwendungen in einer Sammeloperation entwickelt. Des Speichers für die Business aktiviert mehrere Funktionen, die für das Unternehmen zum Verwalten des Lebenszyklus von Anwendungen aus Erwerb zu aktualisierende erforderlich sind.

Hier wird die Liste der verfügbaren Funktionen:

-   Unterstützung für Enterprise-Identitäten – ermöglicht den Benutzern innerhalb einer Organisation, die Identität zu verwenden, die Ihnen innerhalb der Organisation bereitgestellt wurde. Dies ermöglicht eine Organisation, die Steuerung der Anwendung beibehalten werden und entfällt die Notwendigkeit für eine Organisation zu einem anderen Satz von Identitäten für die Benutzer zu verwalten.
-   Massen-Erwerb Support-Anwendungen – ermöglicht das IT-Administratoren in einer Sammeloperation Applications erwerben. IT-Abteilungen können jetzt über die Beschaffung und Verteilung von Clientanwendungen steuern. Bisher erwerben Benutzer manuell Applications aus.
-   Lizenz machen und erneut verwenden – ermöglicht es Unternehmen, Wert in ihrer Einkäufe beibehalten werden durch die Möglichkeit, Zugriff auf eine Anwendung Zuweisung zulassen und dann neu zuordnen die Anwendung an einen anderen Benutzer. In Windows Store, wenn ein Benutzer mit einem Microsoft-Konto das Unternehmen verlässt behält heute, er den Besitz der Anwendung.
-   Flexible Verteilung Modelle für Windows Store-apps – ermöglicht Unternehmen, Ihre Infrastruktur eines Unternehmens integrieren die Prozesse zum Verteilen von Anwendungen für Geräte, die an Store für BusinessServices und für Geräte ohne Verbindung an den Store für BusinessServices verbunden sind.
-   Benutzerdefinierte Line of Business app unterstützen – ermöglicht die Verwaltung und Verteilung von unternehmensanwendungen über den Informationsspeicher für Unternehmen.
-   Unterstützung für Windows Desktop- und mobilen Geräten - der Store for Business desktop und mobile Geräte unterstützt.

Weitere Informationen zum Anmelden für Unternehmen finden finden Sie unter den Themen TechNet im [Windows Store für Business](https://technet.microsoft.com/library/mt606951.aspx).

## <a name="management-services"></a>Rights Management services

Des Speichers für die Business enthält Dienste, mit die ein Verwaltungstool für neue und aktualisierte Applikationen im Namen einer Organisation synchronisieren können. Sobald synchronisiert ist, können Sie neue und aktualisierte Anwendungen mithilfe von Windows Management Framework verteilen. Die Dienste bietet verschiedene Funktionen, einschließlich der Bereitstellung von Anwendungsdaten, die Möglichkeit, zuweisen und Freigeben von Anwendungen und die Möglichkeit, offline lizenziert Anwendungspakete herunterzuladen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Anwendungsdaten</p></td>
<td style="vertical-align:top"><p>Der Store für Business-Dienst bietet Metadaten für Anwendungen, die über den Speicher für Unternehmen erworben wurden. Dazu gehören die ID, die zur Bereitstellung von online-Lizenz-Anwendungen verwendet wird Grafik für eine Anwendung, die zum Erstellen einer Unternehmensportal verwendet wird und eine lokalisierte Beschreibung für Applikationen.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Lizenzierungsmodelle</p></td>
<td style="vertical-align:top"><p><strong>Im Vergleich zu Online Offline</strong></p>
<p>Online lizenziert Clientanwendungen erfordern Connectivity an den Windows Store. Benutzer benötigen die Azure Active Directory-Identität und basieren auf den Store-Diensten auf dem Gerät eine Anwendung aus dem Speicher erwerben können. Es ist ähnlich wie Anwendungen aus dem Windows Store mit Microsoft-Konto erworben werden. Zuweisen oder freigeben Arbeitsplätzen für eine Anwendung benötigen einen Anruf an den Store für Business-Services.</p>
<p>Offline lizenziert Applikationen aktivieren eine Organisation, um die Anwendung für Imaging und für Geräte, die möglicherweise keinen Konnektivität auf den Speicher oder möglicherweise keinen Azure Active Directory zu verwenden. Anwendung offline lizenziert erfordern keinen Konnektivität zu im Speicher, aber es direkt aus dem Speicher aktualisiert werden kann, wenn das Gerät Verbindung eine und Richtlinien für die Aktualisierung der app erlauben, Updates über den Speicher verteilt werden sollen.</p></td>
</tr>
</tbody>
</table>

 

### <a name="offline-licensed-application-distribution"></a>Verteilung der Anwendung offline lizenziert

Die folgende Abbildung bietet eine Übersicht über app-Verteilung von Erwerb einer Anwendung offline lizenziert Verteilung an einen Client. Sobald aus dem Store for Business synchronisiert wird, können das Verwaltungstool für das Windows Management Framework zum Verteilen von Anwendungen für Geräte aus.

![Business Store offline app Verteilung](images/businessstoreportalservices2.png)

### <a name="online-licensed-application-distribution"></a>Verteilung der Anwendung Online lizenziert

Im folgende Diagramm bietet eine Übersicht über app-Verteilung von Erwerb einer Anwendung online lizenziert Verteilung an einen Client. Sobald aus dem Store for Business synchronisiert wird, können das Verwaltungstool für das Windows Management Framework zum Verteilen von Anwendungen für Geräte aus. Für Applikationen online lizenziert Ruft das Verwaltungstool zurück in den Speicher für Business-Verwaltungsdienste zuweisen eine Anwendung, bevor Sie die Richtlinie zur Installation der Anwendung.

![Business Store online app Verteilung](images/businessstoreportalservices3.png)

## <a name="integrate-with-azure-active-directory"></a>Integrieren Sie in Azure Active Directory

Des Speichers für Unternehmensdienste, Azure Active Directory für die Authentifizierung nutzen. Das Verwaltungstool muss als Anwendung Azure AD innerhalb einer Organisation Mandanten des Speichers für die Business authentifizieren registriert werden.

Weitere Informationen zu Azure AD und zum Registrieren der Anwendung innerhalb von Azure Active Directory finden Sie sind im folgenden einige Themen für die ersten Schritte:

-   Hinzufügen einer Anwendung zur Azure Active Directory - [Integration von Azure Active Directory MDM](azure-active-directory-integration-with-mdm.md)
-   Zugreifen auf andere Webanwendungen und Konfigurieren der Anwendung zu anderen APIs - [Integration von Clientanwendungen mit Azure Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=623021) zugreifen
-   Authentifizierung für den Speicher für die Business Services über Azure AD - [Authentifizierungsszenarien für Azure Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=623023)

Codebeispiele finden Sie unter [Microsoft Azure Active Directory Beispiele und Dokumentation](http://go.microsoft.com/fwlink/p/?LinkId=623024) in GitHub. Muster sind [Filterdaemon DotNet](http://go.microsoft.com/fwlink/p/?LinkId=623025) und [ConsoleApp-GraphAPI-DotNet](http://go.microsoft.com/fwlink/p/?LinkId=623026)sehr ähnlich.

## <a name="configure-your-azure-ad-application"></a>Konfigurieren Sie Ihre Anwendung Azure AD

Hier werden die Schritte zum Konfigurieren Ihrer Azure AD-app. Weitere Informationen finden Sie unter [Integration von Clientanwendungen mit Azure Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=623021):

1.  Melden Sie sich bei Microsoft Azure-Verwaltungsportal (https:manage.windowsazure.com)
2.  Wechseln Sie zu der Active Directory-Modul.
3.  Wählen Sie Ihr Verzeichnis aus.
4.  Klicken Sie auf die Registerkarte **Applications** .

    ![Business-Verwaltungstool](images/businessstoreportalservices8.png)

5.  Klicken Sie auf **Hinzufügen**.

    ![Business-Verwaltungstool](images/businessstoreportalservices9.png)

6.  Wählen Sie **eine Anwendung, die meien Organisation entwickelt hinzufügen**.

    ![Business-Verwaltungstool](images/businessstoreportalservices10.png)

7.  Geben Sie einen Namen ein, und wählen Sie **WEB-ANWENDUNG oder WEB-API**.

    ![Business-Verwaltungstool](images/businessstoreportalservices11.png)

8.  Die **SIGN-ON URL** zu Ihrer Anwendung angeben.

    ![Business-Verwaltungstool](images/businessstoreportalservices12.png)

9.  Geben Sie an, ob Ihre app mit mehreren Mandanten oder einzelnen Mandanten ist. Weitere Informationen finden Sie unter [Integration von Clientanwendungen mit Azure Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=623021).

    ![Business-Verwaltungstool](images/businessstoreportalservices13.png)

10. Erstellen Sie einen Clientschlüssel.

    ![Business-Verwaltungstool](images/businessstoreportalservices14.png)

   > **Hinweis**  In der vorherigen Version des Tools wurde ein Update für das app-Manifest, um die Anwendung zu autorisieren erforderlich. Dies ist nicht mehr erforderlich.
     
11. Melden Sie sich anmelden für Unternehmen und Ihre Anwendung aktivieren. Schrittweise Anleitung finden Sie unter [Konfigurieren eines Anbieters MDM](https://technet.microsoft.com/library/mt606939.aspx).


## <a name="azure-ad-authentication-for-mts"></a>Azure AD-Authentifizierung für MTS

MTS erfordert Aufrufe mit einem Azure AD-OAuth-Token Bearer authentifiziert werden. Das Autorisierungstoken ist für die Azure AD-Anwendung, die MDM-Komponente (Dienst/Filterdaemon/auf-Prem Instanz) im Kontext des Verzeichnis/Mandanten in Auftrag arbeiten darstellt-des.

Hier werden die Details für das Anfordern einer Autorisierungstoken:

-   Anmeldung Authority = Https:<span></span>//login.windows.net/&lt;TargetTenantId&gt;
-   Ressource/Benutzergruppe\* = Https:<span></span>//onestore.microsoft.com
-   ClientId = Ihrer AAD Anwendung Client-Id
-   ClientSecret = Ihre AAD Anwendung Client Secret/Schlüssel

\*Die token Benutzergruppe URI sollte als Bezeichner der Anwendung für die das Token generiert wird, und es ist keine URL für einen Endpunkt oder eine Webseite.

## <a name="using-the-management-tool"></a>Verwenden das Verwaltungstool

Nach dem Registrieren Ihrer-Verwaltungstools mit Azure AD, kann das Verwaltungstool für die Verwaltungsdienste anrufen. Es gibt einige Anruf Muster:

-   Erste die Möglichkeit zum Abrufen der neuen oder aktualisierten Applications.
-   Zweiter die Möglichkeit zum Zuweisen oder Anwendungen freizugeben.

Im folgenden Diagramm zeigt die Anruf Mustern für Erwerb einer neuen oder aktualisierten Anwendung.

![Business Store Service Portal-Flussdiagramm](images/businessstoreportalservicesflow.png)

**Hier wird die Liste der verfügbaren Vorgänge**:

-   [Abrufen von Inventar](get-inventory.md)
-   [Hier finden Sie Produktdetails](get-product-details.md)
-   [Hier finden Sie lokalisierte Produktdetails](get-localized-product-details.md)
-   [Offline-Lizenz abrufen](get-offline-license.md)
-   [Abrufen der Produktpakete](get-product-packages.md)
-   [Abrufen der Produktpaket](get-product-package.md)
-   [Abrufen von Arbeitsplätzen](get-seats.md)
-   [Abrufen von Arbeitsplatz](get-seat.md)
-   [Zuweisen von Arbeitsplätzen](assign-seats.md)
-   [Freigeben von Benutzer Arbeitsplatz](reclaim-seat-from-user.md)
-   [Massen zuweisen und freizugeben Arbeitsplätzen für Benutzer](bulk-assign-and-reclaim-seats-from-user.md)
-   [Abrufen von einem Benutzer zugewiesenen Arbeitsplätzen](get-seats-assigned-to-a-user.md)

 





