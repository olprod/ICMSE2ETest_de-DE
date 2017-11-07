---
author: Justinha
Description: Konfigurieren der Windows-Firewall mit erweiterter Sicherheit mithilfe einer Antwortdatei
ms.assetid: 6243caf7-3b74-431e-b6f9-76b98106bf42
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren der Windows-Firewall mit erweiterter Sicherheit mithilfe einer Antwortdatei
ms.openlocfilehash: c2e4dfa7b38c180f5ca9bad38cdaebe3310a7336
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-firewall-with-advanced-security-by-using-an-answer-file"></a>Konfigurieren der Windows-Firewall mit erweiterter Sicherheit mithilfe einer Antwortdatei


Für unbeaufsichtigte Installationen können Sie mithilfe der Netzwerk-MPSSVC-Svc-Komponente Windows®-Firewall mit erweiterter Sicherheit Einstellungen in einer Antwortdatei konfigurieren. Zusätzlich zu den Einstellungen Antwort Angabe für Windows-Firewall mit erweiterter Sicherheit können Sie einen Befehl **RunSynchronous** erstellen, der während der Konfigurationsdurchlauf [AuditUser](audituser.md) oder [OobeSystem](oobesystem.md) **Netsh Advfirewall** Befehle ausgeführt wird.

## <a name="span-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanspan-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanspan-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanadding-modifying-or-deleting-rules-for-windows-firewall-with-advanced-security"></a><span id="Adding__Modifying__or_Deleting_Rules_for_Windows_Firewall_with_Advanced_Security"></span><span id="adding__modifying__or_deleting_rules_for_windows_firewall_with_advanced_security"></span><span id="ADDING__MODIFYING__OR_DELETING_RULES_FOR_WINDOWS_FIREWALL_WITH_ADVANCED_SECURITY"></span>Hinzufügen, ändern oder Löschen von Regeln für Windows-Firewall mit erweiterter Sicherheit


Verwenden Sie **RunSynchronous** Befehle nur zum Hinzufügen, ändern oder Löschen von Regeln für Windows-Firewall mit erweiterter Sicherheit. Um Regelgruppen zu ändern, verwenden Sie die **Gruppenrichtlinien der Firewall** -Einstellung in der **Netzwerk-MPSSVC-Svc** -Komponente. Weitere Informationen zu Windows-Komponenten und Einstellungen, die eine Antwortdatei hinzugefügt werden können, finden Sie unter [Unbeaufsichtigte Windows Setup-Referenzhandbuch](http://go.microsoft.com/fwlink/?LinkId=206281).

**So fügen Sie einen Befehl Netsh zu einer Antwortdatei hinzu**

1.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**, und wählen Sie dann **Windows System Image Manager**.

2.  Erstellen einer neuen Antwortdatei oder Aktualisieren einer vorhandenen Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085) und [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073).

3.  Klicken Sie im Menü **Einfügen** auf **RunSynchronous**.

4.  Wählen Sie die Konfiguration übergeben, wo Sie den Befehl installieren möchten. Dies kann die Konfigurationsdurchlauf [AuditUser](audituser.md) oder [OobeSystem](oobesystem.md) sein.

    **Hinweis**  
    Verwenden Sie nicht den Befehl **RunSynchronousNetsh Advfirewall** während der Konfiguration [specialize](specialize.md) übergeben.

     

5.  Das Dialogfeld **Synchronen Befehl erstellen** wird angezeigt.

6.  Geben Sie im Feld **Befehlszeile eingeben** die Befehlszeilensyntax wie **Netsh Advfirewall Firewall**. Weitere Informationen finden Sie unter der [Netzwerk-Shell (Netsh) technische Referenz zu](http://go.microsoft.com/fwlink/?LinkId=234733).

7.  Wählen Sie im Feld **Reihenfolge** der Reihenfolge der Befehle, die ausgeführt werden sollen, und klicken Sie dann auf **OK**.

    Der Befehl wird die Antwortdatei im ausgewählten Konfiguration Durchgang wie folgt hinzugefügt:

    1.  Befehle, die die Pass **6 AuditUser übergibt** Konfiguration hinzugefügt werden, angezeigt, in der Einstellung Microsoft-Windows-Deployment\\RunSynchronous.

    2.  Befehle, die der **7** Konfigurationsphase hinzugefügt werden, angezeigt, in der Einstellung der Microsoft-Windows-Shell-Setup\\FirstLogonCommands.

8.  Geben Sie im Eigenschaftenbereich **SynchronousCommand** , im Abschnitt **Einstellungen** neben der **Beschreibung**eine Beschreibung wie **Aktivieren Windows Messenger**.

9.  Der Befehl wird die Antwortdatei unter die Konfigurationsdurchlauf hinzugefügt, die Sie ausgewählt haben. In diesem Beispiel wird veranschaulicht, wie eine eingehende Regel für Windows Messenger konfiguriert ist:

    ``` syntax
          <RunSynchronous>
             <RunSynchronousCommand wcm:action="add">
                <Path>Netsh advfirewall firewall 
                      add rule name="allow messenger" dir=in 
                      program="c:\programfiles\messenger\msmsgs.exe"
                      action=allow
                </Path>
                <Description>Enable Windows Messenger</Description>
                <Order>1</Order>
             </RunSynchronousCommand>
          </RunSynchronous>
    ```

**Hinweis**  
Der Befehl **Netsh Advfirewall** erfordert Administratorberechtigungen ausgeführt. Wenn der Befehl **RunSynchronous** in Konfiguration erfolgreich ausgeführt, die im Kontext des Benutzers ausgeführt wird wird, muss mit dem Benutzerkonto Administratorberechtigungen verfügen.

 

## <a name="span-idusingthenetshadvfirewallcommand-linetoolspanspan-idusingthenetshadvfirewallcommand-linetoolspanspan-idusingthenetshadvfirewallcommand-linetoolspanusing-the-netsh-advfirewall-command-line-tool"></a><span id="Using_the_Netsh_Advfirewall_Command-Line_Tool"></span><span id="using_the_netsh_advfirewall_command-line_tool"></span><span id="USING_THE_NETSH_ADVFIREWALL_COMMAND-LINE_TOOL"></span>Mithilfe des Befehlszeilentools Netsh Advfirewall


Im folgenden Beispiel wird veranschaulicht, wie eine neue ausgehende Firewallregel zum Blockieren eines Ports mithilfe des Befehlszeilentools **Netsh Advfirewall** hinzufügen.

**So fügen Sie eine neue ausgehende Firewallregel hinzu**

-   Geben Sie eine Eingabeaufforderung mit erhöhten Rechten Syntax, die eine neue ausgehende Firewallregel zum Blockieren eines Ports hinzufügt. Beispiel:

    ``` syntax
    Netsh advfirewall firewall add rule name="allow80" protocol=TCP
    dir=out localport=80 action=block
    ```

    Dabei ist der blockierte Port TCP-Port 80.

Sie können Windows PowerShell-Befehle **Netsh** -Befehle konvertieren. Weitere Informationen finden Sie unter der [Netshell Powershell Konvertierung Guide](http://go.microsoft.com/fwlink/?LinkId=234734).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

 

 






