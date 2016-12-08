---
title: IOnOffTransitionManager
description: IOnOffTransitionManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9d719b05-f720-4464-be7a-c991a1d7639e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6c8c0baada8cf7fff6fc162a54381e2e5c639b9f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ionofftransitionmanager"></a>IOnOffTransitionManager


Ermöglicht dem Client die Profile in der [IProfileCollection](iprofilecollection.md) der Registrierung für Boot Tracing gespeichert, aber die Profile wird nicht ausgeführt. Dieses Verhalten Vergleich mit der[IControlManager](icontrolmanager.md), der das Profil sofort ausgeführt wird. Beim Systemstart, Event Tracing for Windows (ETW) liest die Registrierungsschlüssel und Anbietern für Boot entsprechend tracing ermöglicht. Die Bibliothek aktiviert PCW Datensammlung Starten eines Task Scheduler Auftrags so konfiguriert, dass beim Start ausführen.

## <a name="syntax"></a>Syntax


``` syntax
{
  [id(1), helpstring("EnableBootRecording")] HRESULT EnableBootRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(2), helpstring("DisableBootRecording")] HRESULT DisableBootRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(3), helpstring("StartShutdownRecording")] HRESULT StartShutdownRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(4), helpstring("UpdateShutdownRecording")] HRESULT UpdateShutdownRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(5), helpstring("MergeShutdownRecording")] HRESULT MergeShutdownRecording
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties)
  ;
};
```

## <a name="functions"></a>Funktionen


Diese Schnittstelle stellt die Funktionen in der folgenden Tabelle beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktion</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[EnableBootRecording](enablebootrecording.md)</p></td>
<td><p>Ermöglicht das Starten Aufzeichnung für die angegebene Profil-Auflistung.</p></td>
</tr>
<tr class="even">
<td><p>[DisableBootRecording](disablebootrecording.md)</p></td>
<td><p>Deaktiviert die Aufzeichnung für die angegebene Profil-Auflistung zu starten.</p></td>
</tr>
<tr class="odd">
<td><p>[StartShutdownRecording](startshutdownrecording.md)</p></td>
<td><p>Herunterfahren Aufzeichnung startet.</p></td>
</tr>
<tr class="even">
<td><p>[UpdateShutdownRecording](updateshutdownrecording.md)</p></td>
<td><p>Herunterfahren Aufzeichnung aktualisiert.</p></td>
</tr>
<tr class="odd">
<td><p>[MergeShutdownRecording](mergeshutdownrecording.md)</p></td>
<td><p>Herunterfahren Aufzeichnungen verbindet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Schnittstellen](interfaces-wprcontrol.md)

 

 







