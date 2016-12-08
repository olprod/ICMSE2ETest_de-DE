---
title: "MDM Registrierung von Windows-basierten Geräten"
description: "Registrierung von Windows-basierten Geräten MDM"
MS-HAID:
- p\_phdevicemgmt.enrollment\_ui
- p\_phDeviceMgmt.mdm\_enrollment\_of\_windows\_devices
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4651C81B-D2D6-446A-AA24-04D01C1D0883
ms.openlocfilehash: 62d7858add6d28f471df6723d4cb12c5cfe4de9b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mdm-enrollment-of-windows-based-devices"></a>Registrierung von Windows-basierten Geräten MDM


In diesem Thema wird die Benutzeroberfläche eingeschrieben 10 Windows-basierten PCs und Geräte.

In der Cloud beschränkten modernen Enterprise IT Abteilungen zunehmend Mitarbeiter schalten Sie ihre eigenen Geräte oder sogar wählen und kaufen firmeneigenen Geräte ermöglichen möchten. Herstellen einer Verbindung mit Ihrer Geräten arbeiten erleichtert es den Ressourcen Ihrer Organisation (beispielsweise apps, Unternehmensnetzwerk und e-Mail) Zugriff auf.

> **Hinweis**  Wenn Sie das Gerät mithilfe des mobilen Geräts Management (MDM) Registrierung verbinden, kann Ihre Organisation bestimmte Richtlinien auf Ihrem Gerät erzwingen.

 

## <a name="connecting-corporate-owned-windows-10-based-devices"></a>Herstellen einer Verbindung mit firmeneigenen 10 Windows-basierte Geräte


Corporate gehören Geräte hergestellt werden können, entweder für die Verwendung durch Verknüpfen das Gerät mit einer Active Directory-Domäne oder einer Domäne Azure Active Directory (AD Azure). Windows 10 erfordert keine persönliches Microsoft-Konto auf Geräten mit Azure AD verknüpft oder in einer lokalen Active Directory-Domäne.

![Active Directory Azure Ad-Anmeldung](images/unifiedenrollment-rs1-1.png)

### <a name="connecting-your-device-to-an-active-directory-domain-join-a-domain"></a>Verbinden des Geräts mit Active Directory-Domäne (beitreten zu einer Domäne)

Geräte unter Windows 10 Pro, kann Windows 10 Enterprise oder Windows 10 Education mit einer Active Directory-Domäne verbunden sein. Diese Geräte können mit Einstellungsapp verbunden werden.

> **Hinweis**  Mobile Geräte können nicht mit einer Active Directory-Domäne verbunden sein.

 

### <a name="out-of-box-experience-oobe"></a>Out-of-Box-Experience (OOBE)

Da das Gerät mit einer Active Directory-Domäne beitreten, während der OOBE nicht unterstützt wird, müssen Sie zuerst ein lokales Konto erstellen, und verbinden Sie dann das Gerät mit der app Settings.

1.  Klicken Sie auf die **, die Eigentümer von diesem PC?** **Meine Arbeit "oder" Schule besitzt es**wählen Sie Seite.

    ![OOBE lokales Konto erstellen](images/unifiedenrollment-rs1-2.png)

2.  Wählen Sie im nächsten Schritt aus **einer Domäne**.

    ![Wählen Sie Domäne oder Azure ad](images/unifiedenrollment-rs1-3.png)

3.  Als Nächstes sehen Sie dazu aufgefordert werden, richten Sie ein lokales Konto auf dem Gerät ein. Geben Sie Ihre lokale Kontodetails, und klicken Sie dann auf **Weiter** .

    ![pc-Konto erstellen](images/unifiedenrollment-rs1-4.png)

### <a name="using-the-settings-app"></a>Verwenden der app Einstellungen

1.  Starten Sie die app Settings.

    ![Windows-Einstellungsseite](images/unifiedenrollment-rs1-5.png)

2.  Wählen Sie im nächsten Schritt **Konten**.

    ![Wählen Sie Windows-Einstellungen für Konten](images/unifiedenrollment-rs1-6.png)

3.  Navigieren Sie zu **Access Arbeit "oder" Schule**.

    ![Wählen Sie Access Arbeit "oder" school](images/unifiedenrollment-rs1-7.png)

4.  Klicken Sie auf **eine Verbindung herstellen**.

    ![Herstellen einer Verbindung mit arbeiten oder Schule](images/unifiedenrollment-rs1-8.png)

5.  Klicken Sie unter **alternative Aktionen**klicken Sie auf **dieses Gerät eine lokale Active Directory-Domäne beitreten**.

    ![Konto mit active Directory-Domäne beitreten](images/unifiedenrollment-rs1-9.png)

6.  Geben Sie in Ihren Domänennamen, befolgen Sie die Anweisungen, und klicken Sie dann auf **Weiter** . Nachdem Sie den Ablauf abgeschlossen und Ihr Gerät neu starten, sollte er an Ihre Active Directory-Domäne verbunden sein. Sie können jetzt in das Gerät mit Ihren Domänenanmeldeinformationen anmelden.

    ![Geben Sie im Domänennamen](images/unifiedenrollment-rs1-10.png)

### <a name="help-with-connecting-to-an-active-directory-domain"></a>Hilfe beim Herstellen einer Verbindung mit Active Directory-Domäne

Es gibt einige Instanzen, in dem das Gerät mit einer Active Directory-Domäne verbunden werden kann:

| Verbindungsproblem                                                | Erläuterung                                                                                                                                                                                                               |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Das Gerät ist bereits mit einer Active Directory-Domäne verbunden. | Das Gerät kann jeweils nur einer Active Directory-Domäne verbunden werden.                                                                                                                                          |
| Ihr Gerät ist mit einer Azure AD-Domäne verbunden.                 | Das Gerät kann entweder ein Azure AD-Domäne zu einer Active Directory-Domäne verbunden werden. Sie können nicht gleichzeitig auf beide verbinden.                                                                                       |
| Sie sind als Standardbenutzer angemeldet.                           | Das Gerät kann nur mit einer Azure AD-Domäne verbunden werden, wenn Sie als Administrator angemeldet sind. Sie müssen so wechseln Sie zu einem Administratorkonto an, um den Vorgang fortzusetzen.                                                    |
| Ihr Gerät wird Windows 10 Home ausgeführt.                         | Dieses Feature ist nicht auf Windows 10 Home verfügbar, damit Sie mit einer Active Directory-Domäne kann nicht hergestellt werden. Sie müssen zum Upgraden auf Windows 10 Pro, Windows 10 Enterprise oder Windows 10 Education, um den Vorgang fortzusetzen. |

 

### <a name="connecting-your-device-to-an-azure-ad-domain-join-azure-ad"></a>Verbinden des Geräts mit einer Azure AD-Domäne (Azure AD-Join)

Alle Windows-Geräte können mit einer Azure AD-Domäne angeschlossen sein. Diese Geräte können während OOBE verbunden sein. Darüber hinaus können Desktopgeräte einer mit Einstellungsapp Azure AD-Domäne verbunden sein.

### <a name="out-of-box-experience-oobe"></a>Out-of-Box-Experience (OOBE)

1.  **Meine Arbeit "oder" Schule besitzt es**wählen und dann auf **nächsten.**

    ![OOBE lokales Konto erstellen](images/unifiedenrollment-rs1-11.png)

2.  Klicken Sie auf **teilnehmen von Azure AD** **nächsten.**

    ![Wählen Sie Domäne "oder" Azure ad](images/unifiedenrollment-rs1-12.png)

3.  Geben Sie in Ihrem Azure AD-Benutzername. Dies ist die e-Mail-Adresse, die Sie zur Anmeldung bei Microsoft Office 365 und ähnliche Dienste verwenden.

    Ist der Mandant eine nur-Cloud-Mandanten, zum Anzeigen der Organisation benutzerdefiniertes branding wird auf dieser Seite ändern, und das Kennwort direkt auf dieser Seite eingeben können. Wenn der Mandanten Bestandteil einer verbunddomäne ist, werden Sie der Organisation lokalen Verbundserver wie Active Directory Federation Services (AD FS) für die Authentifizierung umgeleitet.

    Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor der Authentifizierung zu diesem Zeitpunkt bieten. Wenn Ihre Azure AD-Mandanten die automatische Registrierung konfiguriert hat, wird Ihr Gerät auch in MDM während dieser Ablauf registriert. Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/). Wenn es sich bei Ihrem Mandanten für die automatische Registrierung nicht konfiguriert ist, müssen Sie den Ablauf der Registrierung ein zweites Mal durchlaufen Ihr Gerät mit MDM verbunden Nachdem Sie den Ablauf abgeschlossen haben, wird Ihr Gerät mit Azure AD-Domäne Ihrer Organisation verbunden sein.

    ![Azure Ad-Anmeldung](images/unifiedenrollment-rs1-13.png)

### <a name="using-the-settings-app"></a>Verwenden der app Einstellungen

1.  Starten Sie die app Settings.

    ![Windows-Einstellungsseite](images/unifiedenrollment-rs1-14.png)

2.  Navigieren Sie anschließend auf **Konten**.

    ![Wählen Sie Windows-Einstellungen für Konten](images/unifiedenrollment-rs1-15.png)

3.  Navigieren Sie zu **Access Arbeit "oder" Schule**.

    ![Wählen Sie Access Arbeit "oder" school](images/unifiedenrollment-rs1-16.png)

4.  Klicken Sie auf **Verbinden**.

    ![Herstellen einer Verbindung mit arbeiten oder Schule](images/unifiedenrollment-rs1-17.png)

5.  Klicken Sie auf **dieses Gerät zu Azure Active Directory beitreten**, klicken Sie unter **Alternative Aktionen**.

    ![Fügen Sie arbeiten oder Schule Konto Azure ad](images/unifiedenrollment-rs1-18.png)

6.  Geben Sie in Ihrem Azure AD-Benutzername. Dies ist die e-Mail-Adresse, die Sie zur Anmeldung bei Office 365 und ähnliche Dienste verwenden.

    ![Azure Ad-Anmeldung](images/unifiedenrollment-rs1-19.png)

7.  Wenn der Mandant eine Cloud ist nur Mandanten, ändert sich diese Seite zum Anzeigen der Organisation benutzerdefiniertes branding und können direkt auf dieser Seite das Kennwort eingeben. Wenn der Mandant Teil einer verbunddomäne ist, werden Sie der Organisation lokalen Verbundserver wie AD FS für die Authentifizierung umgeleitet.

    Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor Authentifizierung zu diesem Zeitpunkt bereitstellen.

    Wenn Ihre Azure AD-Mandanten die automatische Registrierung konfiguriert hat, wird das Gerät auch in MDM während dieser Ablauf registriert. Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/). Wenn es sich bei Ihrem Mandanten für die automatische Registrierung nicht konfiguriert ist, müssen Sie den Ablauf der Registrierung ein zweites Mal durchlaufen Ihr Gerät mit MDM verbunden

    Nachdem Sie das Ende des Datenflusses erreichen, sollte das Gerät mit Azure AD-Domäne Ihrer Organisation verbunden werden. Sie können jetzt melden Sie Ihr aktuelles Konto und melden Sie sich mit Ihrem Benutzernamen Azure AD.

    ![im Unternehmen anmelden](images/unifiedenrollment-rs1-20.png)

### <a name="help-with-connecting-to-an-azure-ad-domain"></a>Hilfe beim Herstellen einer Verbindung mit einer Domäne Azure AD

Es gibt einige Instanzen, in dem Ihr Gerät mit einer Azure AD-Domäne verbunden werden kann:

| Verbindungsproblem                                                | Erläuterung                                                                                                                                                                                                                |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ihr Gerät ist mit einer Azure AD-Domäne verbunden.                 | Das Gerät kann nur an eine einzelne verbunden werden Azure AD-Domäne zu einem Zeitpunkt.                                                                                                                                                   |
| Ihr Gerät ist bereits mit Active Directory-Domäne verbunden. | Das Gerät kann entweder ein Azure AD-Domäne zu einer Active Directory-Domäne verbunden werden. Sie können nicht gleichzeitig auf beide verbinden.                                                                                        |
| Das Gerät hat bereits einen Benutzer mit einem Konto Arbeit verbunden ist.     | Sie können eine Verbindung mit einer Azure AD-Domäne oder eine Verbindung mit einem Konto arbeiten oder Schule. Sie können nicht gleichzeitig auf beide verbinden.                                                                                            |
| Sie sind als Standardbenutzer angemeldet.                           | Das Gerät kann nur mit einer Azure AD-Domäne verbunden werden, wenn Sie als Administrator angemeldet sind. Sie müssen so wechseln Sie zu einem Administratorkonto an, um den Vorgang fortzusetzen.                                                     |
| Ihr Gerät wird bereits durch MDM verwaltet.                          | Mit dem Azure AD-Flow verbinden versucht, das Gerät in MDM registrieren, wenn Ihre Azure AD-Mandanten einen vorkonfigurierten MDM Endpunkt hat. Das Gerät muss aus MDM in diesem Fall mit Azure Active Directory verbinden können unenrolled sein. |
| Ihr Gerät wird Windows 10 Home ausgeführt.                         | Dieses Feature ist nicht verfügbar auf Windows 10 Home, damit Sie mit einer Azure AD-Domäne kann nicht hergestellt werden. Sie müssen zum Upgraden auf Windows 10 Pro, Windows 10 Enterprise oder Windows 10 Education, um den Vorgang fortzusetzen.          |

 

## <a name="connecting-personally-owned-devices-bring-your-own-device"></a>Verbinden von Geräten persönlich gehören (schalten Sie Ihr eigenes Gerät)


Privat genutzte Geräte, auch bekannt als eigene Gerät oder BYOD bringen, ein Konto arbeiten oder Schule oder MDM hergestellt werden kann Windows 10 erfordert ein persönliches Microsoft-Konto auf Geräten arbeiten oder Schule, um die Verbindung nicht.

### <a name="connecting-to-a-work-or-school-account"></a>Herstellen einer Verbindung mit einem Konto arbeiten oder Schule

Alle 10 Windows-basierte Geräte können in ein Arbeit oder Schule Konto verbunden sein. Sie können auf ein arbeiten oder Schule durch die app Einstellungen oder über eine der zahlreichen universellen Windows-Plattform (UWP) apps wie die universelle Office-apps verbinden.

### <a name="using-the-settings-app"></a>Verwenden der app Einstellungen

1.  Starten Sie die app Settings.

    ![Windows-Einstellungsseite](images/unifiedenrollment-rs1-21.png)

2.  Navigieren Sie anschließend auf **Konten**.

    ![Wählen Sie Windows-Einstellungen für Konten](images/unifiedenrollment-rs1-22.png)

3.  Navigieren Sie zu **Access Arbeit "oder" Schule**.

    ![Wählen Sie Access Arbeit "oder" school](images/unifiedenrollment-rs1-23.png)

4.  Klicken Sie auf **eine Verbindung herstellen**.

    ![Herstellen einer Verbindung mit arbeiten oder Schule](images/unifiedenrollment-rs1-24.png)

5.  Geben Sie in Ihrem Azure AD-Benutzername. Dies ist die e-Mail-Adresse, die Sie zur Anmeldung bei Office 365 und ähnliche Dienste verwenden.

    ![Fügen Sie arbeiten oder Schule Konto Azure ad](images/unifiedenrollment-rs1-25.png)

6.  Wenn der Mandant eine Cloud ist nur Mandanten, ändert sich diese Seite zum Anzeigen der Organisation benutzerdefiniertes branding und direkt in die Seite das Kennwort eingeben können. Wenn der Mandant Teil einer verbunddomäne ist, werden Sie der Organisation lokalen Verbundserver wie AD FS für die Authentifizierung umgeleitet.

    Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor der Authentifizierung zu diesem Zeitpunkt bieten.

    Wenn Ihre Azure AD-Mandanten die automatische Registrierung konfiguriert hat, wird Ihr Gerät auch in MDM während dieser Ablauf registriert. Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/). Wenn es sich bei Ihrem Mandanten für die automatische Registrierung nicht konfiguriert ist, müssen Sie den Ablauf der Registrierung ein zweites Mal durchlaufen Ihr Gerät mit MDM verbunden

    ![im Unternehmen anmelden](images/unifiedenrollment-rs1-26.png)

7.  Nachdem Sie den Ablauf abgeschlossen haben, werden Ihrem Microsoft-Konto Arbeit oder Schule-Konto verbunden.

    ![Konto erfolgreich hinzugefügt.](images/unifiedenrollment-rs1-27.png)

### <a name="connecting-to-mdm-on-a-desktop-enrolling-in-device-management"></a>Herstellen einer Verbindung mit MDM auf einem Desktop (Enrolling in Gerätemanagement)

Alle 10 Windows-basierte Geräte können mit einer MDM verbunden sein Sie können mit einer MDM durch die Einstellungsapp verbinden.

### <a name="using-the-settings-app"></a>Verwenden der app Einstellungen

1.  Starten Sie die app Settings.

    ![Windows-Einstellungsseite](images/unifiedenrollment-rs1-28.png)

2.  Navigieren Sie anschließend auf **Konten**.

    ![Windows-Konten Einstellungsseite](images/unifiedenrollment-rs1-29.png)

3.  Navigieren Sie zu **Access Arbeit "oder" Schule**.

    ![Access Arbeit "oder" school](images/unifiedenrollment-rs1-30.png)

4.  Klicken Sie auf den Link **Registrieren nur in Gerätemanagement** (verfügbar in – Wartung Build 14393.82, KB3176934). Verwenden Sie für ältere Builds [Verbinden des Windows-10-basierten Geräts zum Arbeiten mit deep-Link](#connecting-your-windows-10-based-device-to-work-using-a-deep-link)ein.

    ![Herstellen einer Verbindung mit arbeiten oder Schule](images/unifiedenrollment-rs1-31.png)

5.  Geben Sie Ihre geschäftliche e-Mail-Adresse ein.

    ![Einrichten von Arbeit oder Schule-Konto](images/unifiedenrollment-rs1-32.png)

6.  Wenn das Gerät einen Endpunkt gefunden, der nur lokale Authentifizierung unterstützt werden, wird auf dieser Seite ändern und Sie nach Ihrem Kennwort gefragt. Wenn das Gerät einen Endpunkt MDM, der Verbundauthentifizierung unterstützt findet, wird ein neues Fenster angezeigt, die Sie für zusätzliche Authentifizierungsinformationen gefragt werden.

    Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor der Authentifizierung zu diesem Zeitpunkt bieten.

    Nach Abschluss den Ablauf wird Ihr Gerät mit Ihrer Organisation MDM verbunden sein

    ![im Unternehmen anmelden](images/unifiedenrollment-rs1-33.png)

### <a name="connecting-to-mdm-on-a-phone-enrolling-in-device-management"></a>Herstellen einer Verbindung mit MDM auf einem Telefon (Enrolling in Gerätemanagement)

1.  Starten der app **Einstellungen** , und klicken Sie dann auf **Konten**.

    ![telefoneinstellungen](images/unifiedenrollment-rs1-38.png)

2.  Klicken Sie auf **Zugriff Arbeit "oder" Schule**.

    ![telefoneinstellungen](images/unifiedenrollment-rs1-39.png)

3.  Klicken Sie auf den Link **nur in Gerätemanagement registrieren** . Dies ist nur in der Wartung Build 14393.82 (KB3176934) verfügbar. Verwenden Sie für ältere Builds [Verbinden des 10 Windows-basierten Geräts zum Arbeiten mit einer deep-Link](#connecting-your-windows-10-based-device-to-work-using-a-deep-link)ein.

    ![Zugriff auf Arbeit oder Schule Seite](images/unifiedenrollment-rs1-40.png)

4.  Geben Sie Ihre geschäftliche e-Mail-Adresse ein.

    ![Geben Sie Ihre e-Mail-Adresse](images/unifiedenrollment-rs1-41.png)

5.  Wenn das Gerät einen Endpunkt gefunden, der nur lokale Authentifizierung unterstützt werden, wird auf dieser Seite ändern und Sie nach Ihrem Kennwort gefragt. Wenn das Gerät einen MDM Endpunkt gefunden, der Verbundauthentifizierung unterstützt werden, wird ein neues Fenster angezeigt, die Sie für zusätzliche Authentifizierungsinformationen gefragt werden.

    Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor der Authentifizierung zu diesem Zeitpunkt bieten.

6.  Nach Abschluss den Ablauf wird Ihr Gerät mit Ihrer Organisation MDM verbunden sein

    ![Abgeschlossene Mdm-Registrierung](images/unifiedenrollment-rs1-42.png)

### <a name="help-with-connecting-personally-owned-devices"></a>Hilfe beim Herstellen einer Verbindung zur Identifikation gehören Geräte

Einige Instanzen, in dem das Gerät möglicherweise nicht mehr zum Herstellen einer Verbindung mit arbeiten, wie in der folgenden Tabelle beschrieben, sind.

| Fehlermeldung                                                                                                                                                                              | Beschreibung                                                                                         |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| Das Gerät ist bereits in Ihrer Organisation Cloud verbunden.                                                                                                                             | Das Gerät ist bereits entweder Azure AD, verbunden geschäftlichen oder Schule Konto oder eine AD-Domäne.     |
| Wir Ihre Identität nicht in Ihrer Organisation Cloud gefunden.                                                                                                                              | Der eingegebene Benutzername bei Ihrem Mandanten Azure AD nicht gefunden.                                     |
| Ihr Gerät wird bereits von einem Unternehmen verwaltet.                                                                                                                                   | Ihr Gerät wird entweder bereits von MDM oder System Center Configuration Manager verwaltet.                |
| Sie müssen nicht die richtigen Berechtigungen zum Ausführen dieses Vorgangs. Bitte wenden Sie sich an Ihrem Administrator.                                                                                                  | Das Gerät kann nicht als Standardbenutzer in MDM registriert werden. Sie muss auf einem Administratorkonto an. |
| Es konnte nicht automatisch-einen Vergleich der Benutzername eingegebene Management-Endpunkt ermitteln. Überprüfen Sie Ihren Benutzernamen, und versuchen Sie es erneut. Wenn Sie die URL zu Ihrer Endpunkt Management kennen, geben Sie ihn ein. | Sie müssen einen Server-URL für Ihre MDM oder Überprüfen Sie die Schreibweise des Benutzernamens, den Sie angegeben haben.  |

 

## <a name="connecting-your-windows-10-based-device-to-work-using-a-deep-link"></a>Herstellen einer Verbindung mit Ihrer Windows-10-basiertes Gerät funktioniert mit einer deep-link


Windows-10-basierten Geräten können für die Verwendung von deep-Link verbunden sein. Benutzer können sehen, klicken Sie auf oder Öffnen ein Links in einem bestimmten format aus an einer beliebigen Stelle in Windows 10 und auf die neue Oberfläche für die Registrierung geleitet werden.

In Windows 1607 Version 10, wird deep Links nur unterstützt, für die Verbindung von Geräten mit MDM Es wird nicht unterstützt, eine Arbeit hinzufügen oder Schule teilnehmen an einem Gerät Azure AD und teilnehmen an einem Gerät mit Active Directory-Konto.

Der deep-Link zum Verbinden des Geräts verwendet wird, funktioniert verwendet immer das folgende Format:

**MS-Gerät-Registrierung: ?mode = {Modus\_Name}**

| Parameter | Beschreibung                                                  | Unterstützte Wert für Windows 10, Version 1607 |
|-----------|--------------------------------------------------------------|----------------------------------------------|
| Modus      | Beschreibt, welche Weise in der Registrierung app ausgeführt wird. | "Mdm"                                        |

 

### <a name="connecting-to-mdm-using-a-deep-link"></a>Herstellen einer Verbindung mit MDM mithilfe eines deep-links

Bei der Verbindung mit MDM mithilfe eines deep-links ist dies der URI verwendet werden soll

**MS-Gerät-Registrierung: ?mode = Mdm**

Das folgende Verfahren beschreibt, wie Benutzer ihre Geräte mit MDM verwenden deep-Links verbinden können.

1.  Beginnend mit Windows 10 1607 Version, können Sie eine Verknüpfung zum Starten der integrierten Registrierung app mit dem URI erstellen **ms-Gerät-Registrierung: ?mode = Mdm** und benutzerfreundlichen Anzeigetext, z. B., **Klicken Sie hier, um Windows zu verbinden**:

    > **Hinweis**  Dadurch wird den Ablauf der registrieren entspricht in Management-Option in Windows 10, Version 1511 Gerät gestartet.

    - IT-Administratoren können diese Verknüpfung einer e hinzuzufügen, denen Benutzer auf klicken, um diese in MDM registrieren

      ![Mithilfe der Registrierung Deeplink per e-Mail](images/deeplinkenrollment1.png)

    - IT-Administratoren können auch diese Verknüpfung zu einer internen Webseite hinzufügen, die Benutzer auf die Registrierung Anweisungen zu verweisen.

2.  Nach dem Klicken auf den Link oder ausgeführt werden kann, wird Windows 10 die Registrierung app in einem speziellen Modus gestartet, die nur für die Registrierung für die MDM (vergleichbar mit der registrieren in Gerät Managementoption in Windows 10, Version 1511) zulässt.

    Geben Sie Ihre geschäftliche e-Mail-Adresse ein.

    ![Einrichten von Arbeit oder Schule-Konto](images/deeplinkenrollment3.png)

3.  Wenn das Gerät einen Endpunkt gefunden, der nur lokale Authentifizierung unterstützt werden, wird auf dieser Seite ändern und Sie nach Ihrem Kennwort gefragt. Wenn das Gerät einen MDM Endpunkt gefunden, der Verbundauthentifizierung unterstützt werden, wird ein neues Fenster angezeigt, die Sie für zusätzliche Authentifizierungsinformationen gefragt werden.

    > **Hinweis**  Basierend auf IT-Richtlinien, können Sie auch aufgefordert, einen zweiten Faktor der Authentifizierung zu diesem Zeitpunkt bieten.

    Nach Abschluss den Ablauf wird Ihr Gerät mit Ihrer Organisation MDM verbunden sein

    ![im Unternehmen anmelden](images/deeplinkenrollment4.png)

## <a name="managing-connections"></a>Verwalten von Verbindungen


Ihre arbeiten oder Schule Verbindungen können verwaltet werden, auf die **Einstellungen für** &gt; **Konten** &gt; **Access Arbeit "oder" Schule** Seite. Ihre Verbindung werden auf dieser Seite angezeigt, und klicken auf einem werden erweitert, Optionen für diese Verbindung.

![Verwalten von Arbeit oder Schule-Konto](images/unifiedenrollment-rs1-34.png)

### <a name="manage"></a>Manage

Die Schaltfläche **Verwalten** kann auf Arbeit oder Schule Verbindungen im Zusammenhang mit Azure AD gefunden werden. Dazu gehören die folgenden Szenarien:

-   Verbinden des Geräts mit einer Azure AD-Domäne
-   Herstellen einer Verbindung mit einem Konto arbeiten oder Schule.

Durch Klicken auf die Schaltfläche verwalten wird geöffnet, das dieser Verbindung in Ihrem Standardbrowser zugeordnete Azure AD-Portal.

### <a name="info"></a>Info

Die Schaltfläche **Info** finden Sie auf geschäftlich oder Schule Verbindungen im Zusammenhang mit MDM Dazu gehören die folgenden Szenarien:

-   Verbinden des Geräts mit einer Azure AD-Domäne, besteht die automatische Registrierung in MDM konfiguriert.
-   Verbinden des Geräts mit einem arbeiten oder Schule an, verfügt die automatische Registrierung in MDM konfiguriert.
-   Verbinden des Geräts mit MDM

Durch Klicken auf die Schaltfläche **Info** wird eine neue Seite in der app Einstellungen geöffnet, das Details zu Ihrer MDM Verbindung bereitstellt. Sie benötigen Supportinformationen Ihrer Organisation angezeigt (sofern konfiguriert) auf dieser Seite werden sollen. Sie können vermutlich auch eine Sync-Sitzung zu starten, die Ihr Gerät an den MDM Server kommunizieren und Abrufen von Updates für Richtlinien bei Bedarf erzwungen wird.

![Arbeit oder Schule info](images/unifiedenrollment-rs1-35.png)

### <a name="disconnect"></a>Verbindung trennen

Die Schaltfläche **Trennen** kann auf alle Arbeit Verbindungen gefunden werden. Im Allgemeinen wird durch Klicken auf die Schaltfläche **Trennen** die Verbindung vom Gerät zu entfernen. Es gibt einige Ausnahmen:

-   Geräte, die die Richtlinie AllowManualMDMUnenrollment erzwingen lässt nicht Benutzern MDM Registrierung für das Entfernen. Diese Verbindungen müssen entfernt werden, indem eine vom Server initiierte Anmeldung Befehl kündigen.
-   Sie können nicht auf mobilen Geräten Azure AD trennen. Diese Verbindungen können nur durch das Gerät verlorener entfernt werden.

> **Warnung**  Trennen der Verbindung möglicherweise den Verlust von Daten auf dem Gerät.

 

![Trennen Sie arbeiten oder Schule-Konto](images/unifiedenrollment-rs1-36.png)

## <a name="collecting-diagnostic-logs"></a>Sammeln von Diagnoseprotokollen


Sie können von Diagnoseprotokollen um Ihre Arbeit Verbindungen sammeln, indem Sie auf **Einstellungen** &gt; **Konten** &gt; **Access Arbeit "oder" Schule**, und klicken auf den Link **Exportieren Management-Protokolle** unter **Verwandte Einstellungen für**. Nachdem Sie auf den Link klicken, klicken Sie auf **Exportieren** , und führen Sie den Pfad zum Abrufen Ihrer Management-Protokolldateien angezeigt.

![Sammeln von Registrierung Management-Protokolldateien](images/unifiedenrollment-rs1-37.png)

 






