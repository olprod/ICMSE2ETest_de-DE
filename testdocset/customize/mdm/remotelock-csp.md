---
title: RemoteLock CSP
description: RemoteLock CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c7889331-5aa3-4efe-9a7e-20d3f433659b
ms.openlocfilehash: 8fbb0b3468f8b83ad22bdfba5ed1974a531ac9df
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotelock-csp"></a>RemoteLock CSP


RemoteLock CSP unterstützt die Möglichkeit, ein Gerät zu sperren, die eine PIN festlegen auf dem Gerät oder Zurücksetzen der PIN auf einem Gerät, die möglicherweise oder verfügen nicht über eine PIN-NUMMER festgelegt wurde.

> **Hinweis**   RemoteLock CSP ist nur in Windows 10 Mobile unterstützt.

 

Das folgende Diagramm zeigt den RemoteLock Konfiguration-Dienstanbieter in einer Struktur.

![Bereitstellung\-Csp\-Remotelock](images/provisioning-csp-remotelock.png)

<a href="" id="lock"></a>**Sperren**  
Erforderlich. Der Knoten akzeptiert Anfragen auf dem Bildschirm zu sperren. Dem Bildschirm wird sofort sperren, wenn eine PIN-NUMMER festgelegt wurde. Wenn keine PIN festgelegt ist, die Sperre Anforderung wird ignoriert, und der Fehler OMA DM (405) Systemrichtlinie nicht zugelassen wird über die Verwaltung von DDE-Kanal zurückgegeben. Alle OMA DM-Fehler aufgelistet sind [hier](http://go.microsoft.com/fwlink/p/?LinkId=522607) in der Protokollspezifikation für. Die unterstützten Exec ist.

<table>
<colgroup>
<col width="20%" />
<col width="40%" />
<col width="40%" />
</colgroup>
<thead>
<tr class="header">
<th>Status</th>
<th>Beschreibung</th>
<th>Bedeutung [Standard]</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>(200) OK</p></td>
<td><p>Das Gerät wurde erfolgreich gesperrt.</p></td>
<td><p>Der Befehl und die zugehörigen Alert-Aktion werden erfolgreich abgeschlossen.</p></td>
</tr>
<tr class="even">
<td><p>(405)</p></td>
<td><p>Das Gerät konnte nicht gesperrt werden, da es keine PIN, die derzeit auf dem Gerät festgelegt ist.</p></td>
<td><p>Der angeforderte Befehl ist im Ziel nicht zulässig.</p></td>
</tr>
<tr class="odd">
<td><p>Fehler (500)</p></td>
<td><p>Das Gerät wurde für einige aus unbekanntem Grund nicht gesperrt.</p></td>
<td><p>Nicht-spezifische Fehler wurden vom Empfänger beim Versuch, führen Sie den Befehl erstellt.</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="lockandresetpin"></a>**LockAndResetPIN**  
Dieser Knoten kann zum Sperren und Zurücksetzen der PIN auf dem Gerät verwendet werden. Es wird in Verbindung mit dem NewPINValue Knoten verwendet. Nachdem der Vorgang **Exec** erfolgreich auf diesem Knoten aufgerufen wurde, wird die vorherige PIN funktionieren nicht mehr und kann nicht wiederhergestellt werden. Die unterstützten Exec ist.

Dieser Knoten wird mit den folgenden Status zurückgegeben. Alle OMA DM-Fehler aufgelistet sind [hier](http://go.microsoft.com/fwlink/p/?LinkId=522607) in der Protokollspezifikation für.

<table>
<colgroup>
<col width="20%" />
<col width="40%" />
<col width="<40></40>%" />
</colgroup>
<thead>
<tr class="header">
<th>Status</th>
<th>Beschreibung</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>(200) OK</p></td>
<td><p>Das Gerät wurde mit einem neuen Kennwort gesperrt, die zurückgesetzt wurde.</p></td>
<td><p>Der Befehl und die zugeordnete Alert Aktion werden erfolgreich abgeschlossen.</p></td>
</tr>
<tr class="even">
<td><p>Fehler (500)</p></td>
<td><p>n/v</p></td>
<td><p>Non-spezifische Fehler wurden beim Versuch zum Ausführen des Befehls durch den Empfänger erstellt.</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="newpinvalue"></a>**NewPINValue**  
Dieser Knoten enthält die PIN-NUMMER nach Exec für /RemoteLock/LockAndResetPIN aufgerufen wurde. Wenn LockAndResetPIN noch nie aufgerufen wurde, wird der Wert null sein. Wenn Get auf diesem Knoten nach einem erfolgreichen Aufruf Exec auf/RemoteLock/LockAndResetPIN aufgerufen wird, wird die neue PIN bereitgestellt werden. Wenn eine andere Get-Command auf diesem Knoten aufgerufen wird, wird der Wert null sein. Wenn Sie erneut die PIN zurücksetzen müssen, können einer anderen LockAndResetPIN Exec Gerät, um eine neue PIN generieren kommuniziert werden. Auf die PIN Komplexität Mindestanforderungen der zusammengeführten Richtlinien, die auf dem Gerät festgelegt sind, wird der PIN-Wert entsprechen. Wenn keine PIN-Richtlinie auf dem Gerät festgelegt wurde, das Gerät eine 8 vierstellige numerische PIN generieren und setzen Sie das Gerät diese PIN-NUMMER haben.

Der zurückgegebene Datentyp ist eine Zeichenfolge.

Der unterstützte Vorgang ist abrufen.

Get-Vorgang auf diesem Knoten muss einen Exec Vorgang für den /RemoteLock/LockAndResetPIN Knoten in der richtigen Reihenfolge und in der gleichen SyncML Nachricht entsprechen. Sicherstellen die Reihenfolge, in der Befehle verarbeitet werden, kann das Tag Sequenz verwendet werden.

## <a name="examples"></a>Beispiele


Initiieren einer remote-Sperrung des Geräts an.

``` syntax
<Exec>
   <CmdID>1</CmdID> 
   <Item> 
      <Target> 
         <LocURI>./Vendor/MSFT/RemoteLock/Lock </LocURI> 
      </Target> 
   </Item> 
</Exec>
```

Initiieren einer remote Lock und PIN zurücksetzen des Geräts an. Um die neue Gerät generierte PIN erfolgreich abrufen zu können, müssen die Befehle zusammen und in der richtigen Reihenfolge ausgeführt werden, wie unten dargestellt.

``` syntax
<Sequence>
    <CmdID>1</CmdID> 
    <Exec>
        <CmdID>2</CmdID> 
        <Item> 
            <Target> 
                <LocURI>./Vendor/MSFT/RemoteLock/LockAndResetPIN </LocURI> 
            </Target> 
        </Item> 
    </Exec>
    <Get>
       <CmdID>3</CmdID> 
       <Item> 
            <Target> 
                <LocURI>./Vendor/MSFT/RemoteLock/NewPINValue </LocURI> 
            </Target> 
        </Item> 
    </Get>
</Sequence>
```

> **Hinweis**  Wenn Sie einen remote sperren oder remote Lock und der Befehl Zurücksetzen PIN zu einem Gerät, die bereits gesperrt ist senden, wird das Gerät neu gestartet.

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






