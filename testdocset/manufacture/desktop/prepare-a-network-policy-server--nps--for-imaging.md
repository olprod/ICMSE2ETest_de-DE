---
author: Justinha
Description: "Vorbereiten von einem Netzwerkserver Richtlinie (NPS) für Imaging"
ms.assetid: 7ac7f98a-f3db-4c54-a56a-fe766beb4344
MSHAttr: PreferredLib:/library/windows/hardware
title: "Vorbereiten von einem Netzwerkserver Richtlinie (NPS) für Imaging"
ms.openlocfilehash: 7f8bfda08005d1295576a3c26b901a0577542d6a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prepare-a-network-policy-server-nps-for-imaging"></a>Vorbereiten von einem Netzwerkserver Richtlinie (NPS) für Imaging


Wenn Sie beabsichtigen, erstellen ein Abbild der Installation für die Bereitstellung auf einem anderen Computer, und der Dienst Network Policy Server (NPS) auf dem Quellserver installiert ist, müssen Sie möglicherweise zuerst vertrauliche Informationen entfernt, die auf dem Server gespeichert ist. Verwenden Sie diese Verfahren, um die entsprechenden Einstellungen und Daten aus der NPS-Konfiguration entfernen.

**So löschen Sie RADIUS-Clients aus der NPS-Konfiguration**

1.  Zeigt eine Liste von Clients, Remote Authentication Dial-In User Service (RADIUS) auf dem NPS-Server. Klicken Sie dazu Öffnen einer Eingabeaufforderung mit erhöhten Rechten, geben Sie folgenden Befehl, und drücken Sie die EINGABETASTE:

    ``` syntax
    Netsh nps show client
    ```

2.  Löschen Sie jeden RADIUS-Client in der Liste. Zu tun, an der Eingabeaufforderung mit erhöhten Rechten, geben Sie folgenden Befehl ein, und drücken Sie die EINGABETASTE:

    ``` syntax
    Netsh nps delete client [name]
    ```

    Dieser Befehl löscht beispielsweise RADIUS-Client mit dem Namen * &lt;WirelessAP1&gt; * aus der NPS-Server-Konfiguration:

    ``` syntax
    Netsh nps delete client name = <WirelessAP1>
    ```

    Sie können mehrere RADIUS-Clients durch ein Komma zwischen jedem Client einfügen löschen. Beispiel:

    ``` syntax
    Netsh nps delete client name = <WirelessAP1>,<WirelessAP2>,<WirelessAP3>
    ```

    Sie können auch RADIUS-Client mit dem folgenden Befehl entfernen.

    ``` syntax
    Remove-NpsRadiusClient [-Name] <Radius Client Name>-
    ```

3.  Wiederholen Sie dieses Verfahren für jeden RADIUS-Client, der auf dem NPS-Server konfiguriert ist.

**So löschen Sie eine remote-RADIUS-Servergruppe aus der NPS-Serverkonfiguration**

1.  Zeigt eine Liste von remote RADIUS-Server-Gruppen, die auf dem NPS-Server konfiguriert sind. Klicken Sie dazu öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, geben Sie den folgenden Befehl ein und drücken Sie die EINGABETASTE:

    ``` syntax
    Netsh nps show remoteservergroup
    ```

2.  Jede Gruppe remote-Server in der Liste zu löschen. Zu tun, an der Eingabeaufforderung mit erhöhten Rechten, geben Sie folgenden Befehl ein, und drücken Sie die EINGABETASTE:

    ``` syntax
    Netsh nps delete remoteservergroup [name =] name
    ```

    Dieser Befehl löscht beispielsweise eine remote-RADIUS-Servergruppe mit dem Namen * &lt;RemoteServers1&gt; * aus der NPS-Server-Konfiguration:

    ``` syntax
    Netsh nps delete remoteservergroup name = <RemoteServers1>
    ```

    **Hinweis**  
    Wenn Sie eine remote-RADIUS-Servergruppe löschen, werden alle RADIUS-Server, die in der Gruppe enthaltenen gelöscht werden.

     

3.  Wiederholen Sie dieses Verfahren für jede Gruppe von remote RADIUS-Server, der auf dem Server NPS konfiguriert ist.

Sie können Befehle Windows PowerShell® **Netsh** -Befehle konvertieren. Weitere Informationen finden Sie unter der [Netshell Powershell Konvertierung Guide](http://go.microsoft.com/fwlink/?LinkId=234734).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren von Windows Server-Rollen](configure-windows-server-roles.md)

[Sysprep (verallgemeinern) einer Windows-installation](sysprep--generalize--a-windows-installation.md)

[Windows Server-Bereitstellungsoptionen](windows-server-deployment-options.md)

 

 






