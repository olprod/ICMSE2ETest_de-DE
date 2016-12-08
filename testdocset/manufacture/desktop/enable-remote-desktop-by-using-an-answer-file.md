---
author: Justinha
Description: Aktivieren von Remotedesktop mithilfe einer Antwortdatei
ms.assetid: bee7ad87-7fb4-4313-baab-109a6f067ccc
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktivieren von Remotedesktop mithilfe einer Antwortdatei
ms.openlocfilehash: 6b3fd47cb4701ba1c4b918fb1cfd7b7bf3cdd23d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-remote-desktop-by-using-an-answer-file"></a>Aktivieren von Remotedesktop mithilfe einer Antwortdatei


Um bei einer unbeaufsichtigten Installation desktop Remoteverbindungen zu aktivieren, müssen Sie mehrere Einstellungen konfigurieren und aktivieren die Gruppe Remotedesktop in Windows®-Firewall mit erweiterter Sicherheit.

**Zum Erstellen einer Antwortdatei, um remote desktop Verbindungen aktivieren**

1.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**und wählen Sie dann **Windows System Image Manager**.

2.  Erstellen einer neuen Antwortdatei oder Aktualisieren einer vorhandenen Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085) und [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073).

    Fügen Sie diese Einstellungen zu Ihrer Antwortdatei im angegebenen Konfigurationsdatei Durchgang hinzu:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Komponente</th>
    <th align="left">Konfigurationsphasen</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft-Windows-TerminalServices-LocalSessionManager</p></td>
    <td align="left"><p><strong>4 specialize</strong></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Netzwerke-MPSSVC-Svc\FirewallGroups\FirewallGroup</p></td>
    <td align="left"><p><strong>4 specialize</strong></p></td>
    </tr>
    </tbody>
    </table>

     

3.  Konfigurieren Sie im Bereich **Antwortdatei** diese Einstellungen:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Komponente</th>
    <th align="left">Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft-Windows-TerminalServices-LocalSessionManager</p></td>
    <td align="left"><p><code>fDenyTSConnections=false</code></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Netzwerke-MPSSVC-Svc\FirewallGroups\FirewallGroup</p></td>
    <td align="left"><p><code>Active=true</code></p>
    <p><code>Group=Remote Desktop</code></p>
    <p><code>Profile=all</code></p></td>
    </tr>
    </tbody>
    </table>

     

4.  (Optional) Geben Sie an, wie Benutzer authentifiziert werden. Die folgende Einstellung angeben hilft sicherzustellen, dass Benutzer von Computern, auf denen Remotedesktop ausgeführt nicht mithilfe der Authentifizierung auf Netzwerkebene, eine Remoteverbindung herstellen können. Um remote desktop Verbindungen von Computern aktivieren, die eine beliebige Version von Remotedesktop ausgeführt werden, fügen Sie diese Einstellung der Antwortdatei:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Komponente</th>
    <th align="left">Konfigurationsphasen</th>
    <th align="left">Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft-Windows-TerminalServices-RDP-WinStationExtensions</p></td>
    <td align="left"><p><strong>4 specialize</strong></p></td>
    <td align="left"><p><code>UserAuthentication=0</code></p></td>
    </tr>
    </tbody>
    </table>

Sie sind jetzt bereit, das Windows-Abbild zu installieren.

Weitere Informationen zu Windows® Komponenten und Einstellungen, die eine Antwortdatei hinzugefügt werden können, finden Sie in der [Referenz für unbeaufsichtigte Windows](https://msdn.microsoft.com/library/windows/hardware/dn923277).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren der Windows-Firewall mit erweiterter Sicherheit mithilfe einer Antwortdatei](configure-windows-firewall-with-advanced-security-by-using-an-answer-file.md)

[Automatisieren der Windows-Setup](automate-windows-setup.md)

[Konfigurieren von Netzwerkeinstellungen in einer unbeaufsichtigten Installation](configure-network-settings-in-an-unattended-installation.md)

[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

 

 






