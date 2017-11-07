---
author: Justinha
Description: Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos
ms.assetid: d6011433-badb-4707-a5b9-9325f33b6a95
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos
ms.openlocfilehash: 817440ec1abb4b5e8c157c40a7d657df0c96fdaf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-and-disable-the-built-in-administrator-account"></a>Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos


Bei PCs Fertigung, können Sie das integrierte Administratorkonto, Programme und apps ausführen, bevor ein Benutzerkonto erstellt wird.

**Hinweis**  
In diesem Thema geht es um manufacturing PCs. Hilfe zu das Administratorkonto auf Ihrem eigenen PC versuchen Sie diese Seiten:

-   [Melden Sie sich als administrator](http://go.microsoft.com/fwlink/?LinkId=506857)

-   [Löschen Sie ein Konto mit dem Namen "Administrator"](http://go.microsoft.com/fwlink/?LinkId=506858)

-   [Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=277139)

 

Dieses Konto wird verwendet, wenn Sie das System mithilfe von im Überwachungsmodus Anmeldung oder beim Hinzufügen von Skripts zur Konfiguration [AuditUser](audituser.md) übergeben.

## <a name="span-idenablingthebuilt-inadministratoraccountspanspan-idenablingthebuilt-inadministratoraccountspanspan-idenablingthebuilt-inadministratoraccountspanenabling-the-built-in-administrator-account"></a><span id="Enabling_the_Built-in_Administrator_Account"></span><span id="enabling_the_built-in_administrator_account"></span><span id="ENABLING_THE_BUILT-IN_ADMINISTRATOR_ACCOUNT"></span>Aktivieren das integrierte Administratorkonto


**So aktivieren Sie das integrierte Administratorkonto können Sie eine der folgenden Methoden verwenden:**

1.  [Verwenden Sie eine Antwortdatei](#useananswerfile)

2.  [Melden Sie sich mithilfe von im Überwachungsmodus](#logonusingauditmode)

3.  [Verwenden Sie die lokale Benutzer und Gruppen MMC (gilt nur für Server-Versionen)](#usemmcconsole)

### <a name="span-iduseananswerfilespanspan-iduseananswerfilespanspan-iduseananswerfilespanuse-an-answer-file"></a><span id="UseAnAnswerFile"></span><span id="useananswerfile"></span><span id="USEANANSWERFILE"></span>Verwenden Sie eine Antwortdatei

Sie können das integrierte Administratorkonto während unbeaufsichtigter Installationen aktivieren, durch Festlegen der `AutoLogon` **-Administrator** festlegen, in der Microsoft-Windows-Shell-Setup-Komponente. Dadurch werden das integrierte Administratorkonto, selbst wenn ein Kennwort nicht im angegeben ist die `AdministratorPassword` Einstellung.

Sie können eine Antwortdatei mithilfe von Windows® System Image Manager (Windows SIM) erstellen.

Die folgende Antwort-Beispieldatei zeigt, wie das Administratorkonto aktivieren, ein Administratorkennwort angeben und automatisch melden Sie sich an das System.

**Hinweis**  
Sowohl die Microsoft-Windows-Shell-Setup\\ `Autologon` Abschnitt und die Microsoft-Windows-Shell-Setup\\ `UserAccounts` \\ `AdministratorPassword` Abschnitt sind für die automatische Anmeldung im Überwachungsmodus erforderlich, damit arbeiten. Übergeben Sie die **AuditSystem** Konfiguration muss beide dazu gehören.

 

Die folgende XML-Ausgabe zeigt, wie die entsprechenden Werte festgelegt:

``` syntax
   <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <AutoLogon>
         <Password>
            <Value>SecurePasswd123</Value> 
            <PlainText>true</PlainText> 
         </Password>
         <Username>Administrator</Username> 
         <Enabled>true</Enabled> 
         <LogonCount>5</LogonCount> 
      </AutoLogon>
      <UserAccounts>
         <AdministratorPassword>
            <Value>SecurePasswd123</Value> 
            <PlainText>true</PlainText> 
         </AdministratorPassword>
      </UserAccounts>
   </component>
```

Um zu verhindern, dass geben ein Kennwort für das integrierte Administratorkonto, nachdem Sie die Out-of-Box-Experience abgeschlossen haben, legen Sie die Microsoft-Windows-Shell-Setup\\ `UserAccounts` \\ `AdministratorPassword` in **der Konfigurationsphase** .

Die folgende XML-Ausgabe zeigt, wie die entsprechenden Werte festgelegt:

``` syntax
            <UserAccounts>
                <AdministratorPassword>
                    <Value>SecurePasswd123</Value>
                    <PlainText>true</PlainText>
                </AdministratorPassword>
            </UserAccounts>
```

Für Windows Server® 2012, der integrierte Administrator Kennwort bei der ersten Anmeldung geändert werden muss. Dadurch wird verhindert, dass das integrierte Administratorkonto standardmäßig über ein leeres Kennwort verfügt.

### <a name="span-idlogonusingauditmodespanspan-idlogonusingauditmodespanspan-idlogonusingauditmodespanlog-on-by-using-audit-mode"></a><span id="LogOnUsingAuditMode"></span><span id="logonusingauditmode"></span><span id="LOGONUSINGAUDITMODE"></span>Melden Sie sich mithilfe von im Überwachungsmodus

Wenn der Computer noch nicht über Out-Of-Box-Experience (OOBE) versetzt wurde, können Sie das integrierte Administratorkonto durch erneute Eingabe im Überwachungsmodus eingeben. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

### <a name="span-idusemmcconsolespanspan-idusemmcconsolespanspan-idusemmcconsolespanuse-the-local-users-and-groups-mmc-server-versions-only"></a><span id="UseMMCConsole"></span><span id="usemmcconsole"></span><span id="USEMMCCONSOLE"></span>Verwenden Sie die lokale Benutzer und Gruppen MMC (gilt nur für Serverversionen)

Ändern Sie die Eigenschaften des Administratorkontos mithilfe der lokale Benutzer und Gruppen Microsoft Management Console (MMC).

1.  Öffnen Sie MMC ein, und wählen Sie **Lokale Benutzer und Gruppen**.

2.  Mit der rechten Maustaste in des **Administratorkonto** ein, und wählen Sie dann **Eigenschaften**aus.

    Das Fenster **Eigenschaften von Administrator** wird angezeigt.

3.  Deaktivieren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Konto ist deaktiviert** .

4.  Schließen Sie MMC.

Administratorzugriff ist nun aktiviert.

## <a name="span-iddisablingthebuilt-inadministratoraccountspanspan-iddisablingthebuilt-inadministratoraccountspanspan-iddisablingthebuilt-inadministratoraccountspandisabling-the-built-in-administrator-account"></a><span id="Disabling_the_Built-in_Administrator_Account"></span><span id="disabling_the_built-in_administrator_account"></span><span id="DISABLING_THE_BUILT-IN_ADMINISTRATOR_ACCOUNT"></span>Deaktivieren das integrierte Administratorkonto


Nachdem der Benutzer ein Benutzerkonto im OOBE, erstellt, ist das integrierte Administratorkonto bei neuen Installationen deaktiviert.

Für Upgrade-Installationen bleibt das integrierte Administratorkonto aktiviert, wenn keine anderen aktiven lokaler Administrator auf dem Computer stattgefunden hat, und wenn der Computer nicht Mitglied einer Domäne ist.

**Verwenden Sie eine der folgenden Methoden, um das integrierte Administratorkonto zu deaktivieren:**

1.  **Führen Sie den Sysprep / verallgemeinern Sie Befehl**

    Beim Ausführen der **Sysprep / verallgemeinern** Command, beim nächsten des Computers starten das integrierte Administratorkonto deaktiviert werden wird.

2.  **Verwenden Sie den Benutzerbefehl net**

    Führen Sie den folgenden Befehl aus, um das Administratorkonto zu deaktivieren:

    ``` syntax
    net user administrator /active:no
    ```

    Sie können diesen Befehl ausführen, nachdem Sie den Computer konfiguriert haben und bevor Sie den Computer an einen Kunden übermitteln.

Original Equipment Manufacturers (OEMs) und System-Builder sind erforderlich, um das integrierte Administratorkonto vor der Bereitstellung von Computern für Kunden zu deaktivieren. Zu diesem Zweck können Sie eine der folgenden Methoden verwenden.

## <a name="span-idconfiguringthebuilt-inadministratorpasswordspanspan-idconfiguringthebuilt-inadministratorpasswordspanspan-idconfiguringthebuilt-inadministratorpasswordspanconfiguring-the-built-in-administrator-password"></a><span id="Configuring_the_Built-in_Administrator_Password"></span><span id="configuring_the_built-in_administrator_password"></span><span id="CONFIGURING_THE_BUILT-IN_ADMINISTRATOR_PASSWORD"></span>Der integrierte Administratorkennwort konfigurieren


**Anleitung**

-   Beim Ausführen der **Sysprep / verallgemeinern** Befehl auf Windows Server 2012 und Windows Server 2008 R2, das Tool Sysprep setzt das Kennwort des integrierte Administratorkontos. Das Tool Sysprep löscht nur das integrierte Administratorkonto Kennwort für Servereditionen, nicht für Clienteditionen. Beim nächsten des Computers starten wird eine Aufforderung zur Eingabe eines Kennworts angezeigt.

    **Hinweis**  
    In Windows Server 2012, Windows Server 2008 R2 und Windows Server 2008 erfordert die standardmäßige Kennwortrichtlinie ein sicheres Kennwort, für alle Benutzerkonten. Ein schwaches Kennwort verwenden um konfigurieren Sie können eine Antwortdatei, die Microsoft-Windows-Shell-Setup enthält,\\ `UserAccounts` \\ `AdministratorPassword` Einstellung. Sie können kein schwaches Kennwort verwenden aus, entweder manuell oder mithilfe eines Skripts wie der Befehl **net User** konfigurieren.

     

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

 

 






