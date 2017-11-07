---
title: IConfigServiceProvider2
description: IConfigServiceProvider2
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8deec0fb-59a6-4d08-8ddb-6d0d3d868a10
ms.openlocfilehash: 93fdb533d5fa92f8ae3c31ae280a0f9179e00127
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2"></a>IConfigServiceProvider2


OEMs werden benötigt, um diese einmal pro Konfiguration-Dienstanbieter-Schnittstelle implementieren. ConfigManager2 Clients verwenden diese Schnittstelle zur Instanziierung des Dienstanbieters Konfiguration allgemeine Statusinformationen an den Konfigurationsdienstanbieter kommunizieren und häufig, um zugreifen oder Knoten erstellen.

Die folgende Tabelle zeigt die von dieser Schnittstelle, die OEMs implementieren müssen definierten Methoden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Methode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[IConfigServiceProvider2::ConfigManagerNotification](iconfigserviceprovider2configmanagernotification.md)</p></td>
<td><p>ConfigManager2 zum Senden von Benachrichtigungen mit einem Konfigurationsdienstanbieter der Ereignisse wie bei Konfigurationsdienstanbieter geladen oder entladen wird, wenn frühere Versionen ausgeführt werden und beim Aufrufen von Aktionen auf Knoten ermöglicht.</p></td>
</tr>
<tr class="even">
<td><p>[IConfigServiceProvider2::GetNode](iconfigserviceprovider2getnode.md)</p></td>
<td><p>Gibt einen Knoten vom Konfigurationsdienstanbieter basierend auf den Pfad relativ zu den Stammknoten zurück.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 






