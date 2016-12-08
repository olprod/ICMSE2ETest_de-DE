---
title: IConfigServiceProvider2 ConfigManagerNotification
description: IConfigServiceProvider2 ConfigManagerNotification
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b1f0fe0f-afbe-4b36-a75d-34239a86a75c
ms.openlocfilehash: deff995252c8779d08fcead630d4e3847d74f4bb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2configmanagernotification"></a>IConfigServiceProvider2::ConfigManagerNotification


Diese Methode ermöglicht ConfigManager2 zum Senden von Benachrichtigungen der Ereignisse mit einem Konfigurationsdienstanbieter wie bei der Konfigurationsdienstanbieter geladen oder entladen wird, wenn frühere Versionen ausgeführt werden und beim Aufrufen von Aktionen auf Knoten.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT ConfigManagerNotification([in] CFGMGR_NOTIFICATION cmnfyState, 
                                  [in] LPARAM lpParam);
```

## <a name="parameters"></a>Parameter


<a href="" id="cmnfystate"></a>*cmnfyState*
<ul style="list-style-type:none">
<li>
Die folgenden Ereignisse werden von allen Konfiguration Dienstanbietern unterstützt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignis</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_LOAD</p></td>
<td><p>Erstmaliges ist der Konfigurationsdienstanbieter geladen/instanziiert wird.</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINCOMMANDPROCESSING</p></td>
<td><p>Zu den ersten Befehl einer Transaktion ausführen.</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDCOMMANDPROCESSING</p></td>
<td><p>Transaktion letzter Befehl wurde ausgeführt. Dieses Ereignis wird immer ausgelöst, wenn <code>BEGINCOMMANDPROCESSING</code> ausgelöst wurde, auch wenn die Handhabung von <code>BEGINCOMMANDPROCESSING</code> ist fehlgeschlagen.</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINCOMMIT</p></td>
<td><p>Zu den ersten Befehl einer Transaktion Commit ausgeführt werden.</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDCOMMIT</p></td>
<td><p>Letzter Befehl einer Transaktion wurde ein Commit ausgeführt. Dieses Ereignis wird immer ausgelöst, wenn <code>BEGINCOMMIT</code> ausgelöst wurde, auch wenn die Handhabung von <code>BEGINCOMMIT</code> ist fehlgeschlagen.</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINROLLBACK</p></td>
<td><p>Zu den ersten Befehl der Transaktion einen Rollback.</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDROLLBACK</p></td>
<td><p>Letzter Befehl der Transaktion wurde ein Rollback ausgeführt. Dieses Ereignis wird immer ausgelöst, wenn <code>BEGINROLLBACK</code> ausgelöst wurde, auch wenn die Handhabung von <code>BEGINROLLBACK</code> ist fehlgeschlagen.</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_UNLOAD</p></td>
<td><p>Der Konfigurationsdienstanbieter wird entladen/gelöscht werden.</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_SETSESSIONOBJ</p></td>
<td><p>Session-Objekt ist für die Verwendung verfügbar. <em>LpParam</em> können in einer IConfigSession2 Zeiger umgewandelt werden.</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINTRANSACTIONING</p></td>
<td><p>In erster Linie verwendet für die Kompatibilität mit v1 Konfiguration-Dienstanbieter. Den Anfang einer Sequenz Transactioning signalisiert.</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDTRANSACTIONING</p></td>
<td><p>In erster Linie verwendet für die Kompatibilität mit v1 Konfiguration-Dienstanbieter. Signalisiert das Ende einer Sequenz Transactioning.</p></td>
</tr>
</tbody>
</table>
</li>
</ul>
<br>


<a href="" id="lpparam"></a>*lpParam*
<ul style="list-style-type:none">
<li>
Normalerweise NULL, aber einen Zeiger auf eine IConfigSession2-Instanz enthält, wenn *CmnfState* CFGMGR ist\_BENACHRICHTIGUNG\_SETSESSIONOBJ.
</li>
</ul>
<br>

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt Erfolg an.

## <a name="remarks"></a>Hinweise

ConfigManager2 gewährleistet, dass, wenn sie eines der ANFANGS-Ereignisse ausgelöst

-   CFGMGR\_BENACHRICHTIGUNG\_BEGINCOMMANDPROCESSING
-   CFGMGR\_BENACHRICHTIGUNG\_' BeginCommit '
-   CFGMGR\_BENACHRICHTIGUNG\_BEGINROLLBACK

Anschließend wird das entsprechende END-Ereignis ausgelöst werden, auch wenn die Handhabung der Benachrichtigung, beginnen Sie mit DEM Fehler bei.
Für jede Transaktion wird die Abfolge der Benachrichtigungen an:

1.  BEGINCOMMANDPROCESSING

2.  BEGINTRANSACTIONING

3.  ENDTRANSACTIONING

4.  ENDCOMMANDPROCESSING

5.  ' BeginCommit ' oder BEGINROLLBACK, je nachdem, ob die Transaktion erfolgreich war oder nicht.

6.  ENDCOMMIT oder ENDROLLBACK, je nachdem, ob die Transaktion erfolgreich war oder nicht.

Jede Konfigurationsdienstanbieter erhält die relevanten BEGIN/END-Benachrichtigungen genau einmal pro jede Transaktion, die ConfigManager2 ausgeführt wird.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

 






