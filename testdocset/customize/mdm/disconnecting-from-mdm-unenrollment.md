---
title: Trennen die Verwaltungsinfrastruktur (Unenrollment)
description: "Trennen der Verbindung möglicherweise durch den Benutzer auf dem Telefon lokal oder Remote von der IT-Administrator mit Management Server initiiert werden."
MS-HAID:
- p\_phdevicemgmt.disconnecting\_from\_the\_management\_infrastructure\_\_unenrollment\_
- p\_phDeviceMgmt.disconnecting\_from\_mdm\_unenrollment
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 33B2B248-631B-451F-B534-5DA095C4C8E8
ms.openlocfilehash: a1502f31f72f8de7b6057c68f531b630d68b1117
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disconnecting-from-the-management-infrastructure-unenrollment"></a>Trennen die Verwaltungsinfrastruktur (Unenrollment)

Trennen der Verbindung kann vom Benutzer über das Telefon lokal oder Remote von der IT-Administrator mit Verwaltungsserver eingeleitet werden. Trennung vom Benutzer initiierte erfolgt ähnlich wie die ursprüngliche Verbindung, und es wird aus den gleichen Speicherort in der Systemsteuerung Einstellung als Erstellung des Kontos Jahrestag initiiert. Benutzer können auswählen, für eine beliebige Anzahl von Gründe, einschließlich das Unternehmen verlassen oder ein neues Gerät und nicht mehr weil Zugriff auf ihre LOB-apps auf dem alten Gerät erste getrennt. Wenn ein Administrator eine Trennung initiiert, führt der Client Registrierung die Trennung während seiner nächsten regelmäßige Wartung Sitzung. Administratoren können auswählen, um das Gerät des Benutzers zu trennen, oder nachdem sie das Unternehmen verlassen haben, da das Gerät regelmäßig Fehler, zur Einhaltung der Einstellungen für Sicherheitsrichtlinien für die Organisation aufgetreten ist.

Während der Trennung führt der Client Folgendes aus:

-   Entfernt das Token der Enterprise-Anwendung, die Installation und Ausführung von LOB-apps zulässig. Dieses Token Enterprise zugeordneten Geschäftsanwendungen werden ebenfalls entfernt.
-   Entfernt die Zertifikate, die von MDM Server konfiguriert sind.
-   Nicht mehr Erzwingung von Einstellungen für Richtlinien, die die Verwaltungsinfrastruktur angewendet wurde.
-   Entfernt Gerätekonfiguration Management Client und andere Einstellungskonfiguration von MDM-Server, einschließlich der geplanten Wartungsaufgabe hinzugefügt. Der Client bleibt inaktiv, es sei denn, der Benutzer auf die Verwaltungsinfrastruktur unterbricht.
-   Berichte erfolgreich eingeleitet Aufhebens mit der Managementinfrastruktur, wenn der Administrator den Prozess initiiert hat. Beachten Sie, dass in Windows Aufhebens benutzerinitiierter als bemüht an den Server gemeldet wird.


## <a name="in-this-topic"></a>In diesem Thema

-   [Trennen von vom Benutzer initiierte](#user-initiated-disconnection)
-   [Trennung vom Server initiierte](#server-initiated-disconnection)
-   [Unenrollment Work Access Einstellungen auf der Seite](#unenrollment-from-work-access-settings-page)
-   [IT-Admin – angefordert Trennen von](#it-admin-requested-disconnection)
-   [Unenrollment von Azure Active Directory-Verknüpfung](#dataloss)


## <a name="user-initiated-disconnection"></a>Vom Benutzer initiierte Trennen von

In Windows wird nach der Benutzer überprüft, den Konto Löschbefehl ob und bevor das Konto gelöscht wird, MDM-Client sendet einer Benachrichtigung an den MDM Server benachrichtigen, die den Server das Konto entfernt werden. Dies ist eine best Effort Aktion wie keine Wiederholung integrierten, um sicherzustellen, dass die Benachrichtigung an das Gerät erfolgreich gesendet wird.

Diese Aktion verwendet die OMA DM generische Warnung 1226 Funktion, um einem Benutzer eine MDM Unenrollment Benutzer Benachrichtigung an den Server MDM gesendet, nachdem das Gerät die Benutzer Unenrollment Anforderung akzeptiert, aber bevor es löscht alle Daten zu Enterprise. Der Server sollte festgelegt der Annahme, Unenrollment möglicherweise erfolgreich oder fehlgeschlagen und der Server kann prüfen Sie, ob das Gerät entweder Mobilgeräts unenrolled ist, ob das Gerät dann zurückruft zum geplanten Zeitpunkt oder durch Senden einer Push-benachrichtigungs an das Gerät, um festzustellen, ob es wieder reagiert. Wenn der Server plant, eine Push-Benachrichtigung senden, sollten Sie für einige Verzögerung für das Gerät ein zulassen die Zeit für die Durchführung die Unenrollment Arbeit.

> **Hinweis**  Die Benutzer Unenrollment ist ein OMA DM-Standard. Weitere Informationen über die generische 1226 Warnung, finden Sie in der Spezifikation OMA Gerät Management Protocol (OMA-TS-DM\_Protokoll V1\_2\_1-20080617-A), von der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=267526)zur Verfügung.

 
Des Herstellers verwendet das Type-Attribut an, welche Art von generischen Warnung Es ist. Für Gerät MDM Unenrollment initiiert hat, ist der Typ der Warnung **com.microsoft:mdm.unenrollment.userrequest**.

Nachdem der Benutzer Anmeldung kündigen auswählt, werden alle aktiven MDM OMA DM-Sitzungen beendet. Danach DM-Client startet eine DM-Sitzung, einschließlich eines Benutzers Anmeldung kündigen generische Benachrichtigung des ersten Pakets, der an den Server gesendet.

Im folgende Beispiel zeigt eine erste OMA DM-Paket, das eine generische Warnung enthält. Weitere Informationen zur Unterstützung von WP OMA DM finden Sie unter dem Thema [OMA DM-Protokoll unterstützen](oma-dm-protocol-support.md) .

```
<SyncML xmlns=&#39;SYNCML:SYNCML1.2&#39;>
   <SyncHdr>
      <VerDTD>1.2</VerDTD>
      <VerProto>DM/1.2</VerProto>
      <SessionID>1</SessionID>
      <MsgID>1</MsgID>
      <Target>
         <LocURI>{unique device ID}</LocURI>
      </Target>
      <Source>
         <LocURI>https://www.thephone-company.com/mgmt-server</LocURI>
      </Source>
   </SyncHdr>
   <SyncBody>
      <Alert>
    <CmdID>2</CmdID>
        <Data>1226</Data> <!-- generic alert -->
        <Item>
          <Meta>
             <Type xmlns=”syncml:metinfo”> com.microsoft:mdm.unenrollment.userrequest</Type>
          <Format xmlns= “syncml:metinfo”>int</Format>
           </Meta>
        <Data>1</Data>
         </Item>
       </Alert>

<!-- other device information -->
      <Replace>
         <CmdID>2</CmdID>
         <Item>
            <Source>
               <LocURI>./DevInfo/DevID</LocURI>
            </Source>
         <Data>{unique device ID}</Data>
         </Item>
         <Item>
        ...
         </Item>
      </Replace>
      <Final/>
   </SyncBody>
</SyncML>
```

Nachdem das vorherige Paket gesendet wird, beginnt die Unenrollment.


## <a name="server-initiated-disconnection"></a>Trennung vom Server initiierte

Wenn der Server eine Trennung initiiert, werden alle Gegenstand Sitzungen für die Registrierung ID sofort zur Vermeidung von Deadlocks abgebrochen. Der Server wird nicht für die Unenrollment eine Antwort erhalten möchten, stattdessen generische Warnung erhält eine Benachrichtigung mit Messageid = 1.

``` syntax
<Alert>
      <CmdID>4</CmdID>
      <Data>1226</Data>
      <Item>
        <Meta>
          <Type xmlns="syncml:metinf">com.microsoft:mdm.unenrollment.userrequest</Type>
         <Format xmlns="syncml:metinf">int</Format>
        </Meta>
        <Data>1</Data>
      </Item>
</Alert>
```


<a href="" id="work-access"></a>
## <a name="unenrollment-from-work-access-settings-page"></a>Unenrollment Work Access Einstellungen auf der Seite

Wenn der Benutzer in MDM mit einer Azure Active Directory registriert ist (AAD teilnehmen oder indem Sie ein Konto bei Microsoft Arbeit), das Konto MDM unter der Seite Access arbeiten angezeigt wird. Jedoch ist die Schaltfläche **Trennen** , und kann nicht zugegriffen werden abgeblendet. Benutzer können dieses Kontos MDM entfernen, durch die Zuordnung AAD an das Gerät zu entfernen.

Die Seite Work Access können nur unter folgenden Umständen Anmeldung kündigen:

-   Registrierung durchgeführt wurde von Massen-Registrierung.
-   Registrierung wurde mit der Seite Arbeit Access erstellt.


<a href="" id="dataloss"></a>
## <a name="unenrollment-from-azure-active-directory-join"></a>Unenrollment von Azure Active Directory-Verknüpfung

Wenn ein Benutzer in MDM über Azure Active Directory beitreten registriert wird und anschließend die Registrierung getrennt, besteht keine Warnung, dass der Benutzer Windows Informationen Schutz (WIP) Daten verloren. Die Nachricht Trennen von wird Datenverlust WIP nicht angegeben werden.

![Aadj unenerollment](images/azure-ad-unenrollment.png)

Wenn ein Gerät in MDM über Azure Active Directory beitreten registriert und dann Remote unenrolled, kann das Gerät in einen Zustand erhalten, in dem sie erneut abgebildet werden muss. Wenn Geräte remote von MDM unenrolled sind, wird die Zuordnung AAD auch entfernt. Diese Sicherheitsvorkehrung verlässt direkt zur Vermeidung Corporated Geräte in nicht verwalteten Zustand.

Vor dem Remote unenrolling corporate Geräte, müssen Sie sicherstellen, dass es mindestens ein Administrator die Aktivierung auf dem Gerät, das nicht Teil des Azure Mandanten ist, andernfalls das Gerät haben keiner Administratorbenutzer nach der Operation.

Remote Unenrollment für Azure Active Directory verbunden Geräte schlägt fehl, mobilen Geräten. Um diese Geräte corporate Inhalt entfernen, wird empfohlen, dass Sie das Gerät Remote Wischen.

<a href="" id="it-admin-requested-disconnection"></a>
## <a name="it-adminrequested-disconnection"></a>IT-Admin – angefordert Trennen von

Der Server fordert eine Enterprise Management Trennen von Anforderung durch das Ausstellen eines Exec OMA DM SyncML XML-Befehls für das Gerät mit DMClient Configuration-Dienstanbieter Unenroll Knoten während der nächsten Client initiierte DM Sitzung. Tag für die Daten innerhalb des Befehls Exec sollte den Wert des bereitgestellten DM Servers ProviderID sein. Weitere Informationen finden Sie die Enterprise-spezifischen DM Client Konfiguration.

Wenn die Trennung abgeschlossen ist, wird der Benutzer benachrichtigt, dass das Gerät aus Enterprise getrennt wurde.

 






