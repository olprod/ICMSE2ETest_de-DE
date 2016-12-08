<!---<a name="bk_CreateAzureSubscription"> </a>-->

# <a name="associate-your-office-365-account-with-azure-ad-to-create-and-manage-apps"></a>Ordnen Sie Ihre Office 365-Konto Azure AD erstellen und Verwalten von apps

Um Ihre Anwendung zu authentifizieren, müssen Sie diese in Microsoft Azure Active Directory (AD Azure) registrieren. Dies ist, auf dem Office 365-Benutzer-Konto und Anwendung Informationen gespeichert ist. Zum Verwalten von Azure AD über dem Azure-Verwaltungsportal benötigen Sie ein Microsoft Azure-Abonnement. Mit dem-Verwaltungsportal in Microsoft Azure können Sie Benutzer, Rollen und apps verwalten. 

Dieser Artikel führt Sie durch Azure AD erstellen und Verwalten von apps Ihrer Office 365-Konto zuordnen.


## <a name="prerequisites"></a>Voraussetzungen

**Office 365 für Unternehmen-Konto**

Wenn Sie nicht über eine vorhandene Office 365 für Business Konto verfügen, können Sie:

- Melden Sie sich für ein [Office 365 für Unternehmen plant](http://products.office.com/en-us/business/compare-office-365-for-business-plans) , die zuvor genannten oder
- [Das Office 365 Developer-Programm teilnehmen, und erhalten Sie eine kostenlose 1 Jahr Abonnements zu Office 365](https://aka.ms/devprogramsignup).

**Microsoft Azure-Abonnement** 

- Wenn Sie ein vorhandenes Microsoft Azure-Abonnement haben können, können Sie es von Office 365 für Unternehmen Abonnement zuordnen. 

- Andernfalls müssen Sie ein neues Azure-Abonnement erstellen und verknüpfen ihn mit Ihrem Office 365-Konto, um die Registrierung und Verwaltung von apps.


<!---<a name="bk_AssociateExistingAzureSubscription"> </a>-->

## <a name="to-associate-an-existing-azure-subscription-with-your-office-365-account"></a>Zuordnen ein vorhandenes Azure-Abonnement mit Ihrem Office 365-Konto


1. Melden Sie sich mit Ihren vorhandenen Azure Anmeldeinformationen (beispielsweise Ihr Microsoft-ID wie die [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)user@live.com).
        
2. Wählen Sie den **Active Directory** -Knoten, und klicken Sie dann wählen Sie die Registerkarte **Verzeichnis** und am unteren Rand des Bildschirms, wählen Sie **neu**. 
     
4. Wählen Sie im Menü **neu** aus **Active Directory** > **Verzeichnis** > **Benutzerdefinierte zu erstellen**.
    
5. Wählen Sie im **Verzeichnis hinzufügen**im Feld Dropdown- **Verzeichnis** **vorhandenes Verzeichnis verwenden**. Überprüfen Sie **ich bin bereit, um abgemeldet werden**, und wählen Sie dann das Kontrollkästchen in der unteren rechten Ecke aus. 
    
    Dadurch wird wieder auf dem Azure-Verwaltungsportal.
        
3. Melden Sie sich mit Ihrem Office 365-Kontoinformationen. 
    
    Sie werden aufgefordert, ob Ihr Verzeichnis mit Azure verwendet. 
    
    **Wichtig** Um Ihr Office 365-Konto Azure AD zuzuordnen, benötigen Sie ein Office 365-Business-Konto mit globaler Administrator-Berechtigungen. 
    
        
4. Wählen Sie **Weiter**, und klicken Sie dann **Abmelden**.
        
5. Schließen Sie den Browser, und öffnen Sie das [Portal](https://manage.windowsazure.com). Andernfalls erhalten Sie die Fehlermeldung Zugriff verweigert.
    
        
6. Melden Sie sich erneut mit den Anmeldeinformationen Ihres vorhandenen Azure (beispielsweise Ihre Microsoft-ID wie user@live.com). Navigieren auf den **Active Directory** -Knoten und **im Verzeichnis**sollten nun Ihr Office 365-Konto aufgeführt angezeigt.
    

<!--<a name="bk_AssociateNewAzureSubscription"> </a>-->

## <a name="to-create-a-new-azure-subscription-and-associate-it-with-your-office-365-account"></a>So erstellen ein neues Azure-Abonnement und verknüpfen ihn mit Ihrem Office 365-Konto


1. Melden Sie sich an den Office 365. Wählen Sie aus **der Homepage** des **Admin** -Symbols, das Office 365 Administrationscenter zu öffnen.
2. Klicken Sie auf der im Menü auf der linken Seite der Seite einen Bildlauf nach unten zu **Admin** , und wählen Sie **Azure AD**.

    **Wichtig** Zum Öffnen der Office 365-Verwaltungskonsole und Azure Active Directory zugreifen, benötigen Sie ein Office 365-Business-Konto mit globaler Administrator-Berechtigungen. 
    
3. Erstellen Sie ein neues Abonnement.
        
    Wenn Sie eine Testversion von Office 365 verwenden, sehen Sie eine Meldung angezeigt, dass Azure AD für Kunden mit kostenpflichtige Services beschränkt ist. Sie können weiterhin eine Testversion Azure 30-Tage-Abonnement kostenlos erstellen, jedoch müssen Sie einige zusätzliche Schritte ausführen:
    
    1. Wählen Sie Ihr Land oder Ihre Region aus, und klicken Sie dann auf **Azure-Abonnement**.
    2. Geben Sie Ihre persönlichen Informationen aus. Zwecks Überprüfung Geben Sie eine Telefonnummer ein, an dem Sie erreicht werden können, und geben an, ob eine Textnachricht gesendet oder aufgerufen werden soll.
    3. Nachdem Sie Ihre Überprüfungscode erhalten haben, geben Sie sie ein, und klicken Sie auf **Code überprüfen**.
    4. Geben Sie Zahlungsinformationen, überprüfen Sie des zu, und wählen Sie **Registrieren**.
        
        Ihre Kreditkarte wird nicht belastet.
        
        Schließen Sie oder aktualisieren Sie den Browser während der Erstellung der Azure-Abonnement nicht.
            
4. Sobald Ihr Azure-Abonnement erstellt wird, wählen Sie **Portal**.
        
5. Azure-Tour wird angezeigt. Sie können ihn anzeigen oder wählen Sie **X** zu schließen.
        
    Nun sollte alle Elemente in der Azure-Abonnement angezeigt werden. Eine Verzeichnis mit dem Namen Ihres Office 365-Mandanten aufgelistet.
    
