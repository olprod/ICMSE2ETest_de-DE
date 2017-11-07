# <a name="authenticate-microsoft-graph-endpoints-using-the-v2-authentication-endpoint"></a>Authentifizieren von Microsoft Graph-Endpunkte, die mithilfe des Endpunkts v2-Authentifizierung


<!--
### Preview documentation
There are features and functionality of the converged authentication model that are not yet supported in the public preview period. You should be aware of them if you are building applications during the public preview. For more information, see [Limitations and restrictions of the converged authentication model preview](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/).
-->

## <a name="signing-in-microsoft-account-and-azure-ad-users-with-a-single-authentication-model"></a>Anmelden bei Microsoft-Konto und Azure Active Directory-Benutzer mit einer einzelnen Authentifizierungsmodell

Mithilfe des v2 Authentifizierung Endpunkts können Sie apps erstellen, die sowohl Arbeit und School (Azure AD) sowie persönliche (Microsoft-Konto) Identitäten akzeptieren.

In der Vergangenheit Wenn Sie eine app zur Unterstützung von Microsoft-Konten und Azure Active Directory, entwickeln möchten mussten Sie zwei vollständig getrennten Systemen zu integrieren. Den Endpunkt v2-Authentifizierung verwenden, können Sie jetzt beide Arten von Konten mit einem einzelnen Integration unterstützen. Ein einfacher Vorgang sofort eine Benutzergruppe zu erreichen, die von Millionen Benutzern mit Konten von persönlichen Features Arbeit/Schule umfasst.   

Nachdem Sie Ihre apps mit dem v2 Authentifizierung Endpunkt integrieren, können sie sofort die Microsoft Graph-Endpunkte für persönliche und Arbeit/Schule Konten verfügbar wie zugreifen: 

| Data              | Endpunkt                                       |
|:------------------|:-----------------------------------------------|
| Benutzerprofil      | `https://graph.microsoft.com/v1.0/me`          |
| Outlook-mail      | `https://graph.microsoft.com/v1.0/me/messages` |
| Outlook-Kontakte  | `https://graph.microsoft.com/v1.0/me/contacts` |
| Outlook-Kalendern | `https://graph.microsoft.com/v1.0/me/events`   |
| OneDrive          | `https://graph.microsoft.com/v1.0/me/drive`    |

 >**Hinweis:** Einige Microsoft Graph-Endpunkte wie Gruppen und Aufgaben gelten nicht für Persönliche Konten.  

## <a name="microsoft-graph-api-authentication-scopes"></a>Microsoft Graph-API-Authentifizierung Bereiche

Endpunkt v2 Authentifizierung unterstützt alle berechtigungsbereiche für die Verwendung mit Azure AD-Authentifizierung im [Microsoft Graph berechtigungsbereiche](permission_scopes.md) Thema aufgelistet. Der Endpunkt v2-Authentifizierung unterstützt keine jedoch zurzeit nur-app-Bereiche.

>**Hinweis:** Aktuell, müssen Sie die URL der Ressource 'https://graph.microsoft.com' als Präfix für den Bereich-Zeichenfolge übergeben. Beispiel für das Verwenden der `Files.Read` Bereich, geben Sie den Bereich als `https://graph.microsoft.com/Files.Read`.

Weitere Informationen zum Verwenden von Bereichen mit den Endpunkt des v2-Authentifizierung und Unterschiede zum Verwenden von Ressourcen in Azure AD finden Sie unter [Bereiche, die nicht Ressourcen](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare/#scopes-not-resources).

<!--
The table below lists the authentication scopes to use with the converged authentication model preview. For more information about using scopes with the converged authentication model, and how it differs from using resources in Azure AD, see [Scopes, not resources](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare/#scopes-not-resources).


| **Scope**             | **Permission**                        | **Description**                                                                                                                                         |
|:----------------------|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `User.Read`           | Enable sign-in and read user profile  | Allows users to sign-in to the app, and allows the app to read the profile. It also allow the app to read basic company information of signed-in users. |
| `User.ReadWrite`      | Read and write access to user profile | Allows the app to read the profile of signed-in users, and to update profile information on behalf of signed-in users.                                  |
| `Mail.Read`           | Read user mail                        | Allows this app to read messages in user mailboxes.                                                                                                     |
| `Mail.ReadWrite`      | Read and write access to user mail    | Allows the app to read, update, create, and delete messages in user mailboxes.                                                                          |
| `Mail.Send`           | Send mail as a user                   | Allows the app to send messages as users in the organization.                                                                                           |
| `Contacts.Read`       | Read user contacts                    | Allows the app to read user contacts.                                                                                                                   |
| `Contacts.ReadWrite`  | Have full access to user contacts     | Allows the app to read, update, create and delete user contacts.                                                                                        |
| `Calendars.Read`      | Read user calendars                   | Allows the app to read events in user calendars.                                                                                                        |
| `Calendars.ReadWrite` | Have full access to user calendars    | Allows the app to read, update, create, and delete events in user calendars.                                                                            |
| `Files.Read`          | Read users' files                     | Allows the application to read the current user's files.                                                                                                |
| `Files.ReadWrite`     | Edit or delete users' files           | Allows the app to edit or delete the current user's files.                                                                                              |
| `openid`              | Sign users in                         | Allows users to sign in to the app and allows the app to see basic user profile information.                                                            |
| `offline_access`      | Read and write user's information     | Allows the app to see and update user's data, even when the user is not actively using the app.                                                         |

**Note**: currently it is required to pass the resource url of 'https://graph.microsoft.com' as prefix for the scope string. For example, to use the `Files.Read` scope you would specify the scope as `https://graph.microsoft.com/Files.Read`.
-->


## <a name="next-steps"></a>Nächste Schritte

[Registrieren einer app aus, um den Endpunkt des v2 Authentifizierung verwenden](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-app-registration/)

## <a name="learn-more"></a>Weitere Informationen

[Was ist neu an das Authentifizierungsmodell v2](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare)

[Einschränken der Authentifizierungsmodell v2](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/)

[Microsoft Azure v2 Authentifizierung Endpunkt-Dokumentation](https://azure.microsoft.com/en-us/documentation/articles/?service=active-directory&term=app+model+v2.0)
