---
title: StartShutdownRecording
description: StartShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 763c2f77-aeed-43af-9238-c0a041e02867
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 861ed47cb4687eedea3ccd778726e9baedf9bed5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startshutdownrecording"></a>StartShutdownRecording


Herunterfahren Aufzeichnung startet.

## <a name="syntax"></a>Syntax


``` syntax
HRESULT StartShutdownRecording
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>Parameter


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[in\] gibt das **IProfileCollection** -Objekt.

## <a name="return-value"></a>Rückgabewert


In der folgenden Tabelle werden mögliche Rückgabewerte beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rückgabewert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>Die Funktion wurde erfolgreich Herunterfahren Aufzeichnung gestartet.</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>Mindestens eine der Funktionsargumente ist null.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_RUNNING</p></td>
<td><p>Aufzeichnung wird bereits ausgeführt (es sollte vor dem Aufruf dieser Funktion beendet/abgebrochen sein).</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_RUNTIME_STATE_BOOT_RECORDING</p></td>
<td><p>Aufzeichnung starten bereits ausgeführt wird (es sollte vor dem Aufruf dieser Funktion beendet/abgebrochen sein).</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_EVENT_SESSION_RUNNING</p></td>
<td><p>Einer der Ereignis-Sitzungen, die gestartet werden soll wird bereits ausgeführt. Es konnte zuvor von einer anderen Anwendung (oder aufgrund von WPR Zustand hin, beispielsweise nach WPR Absturz) gestartet werden.</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_STARTSHUTDOWN_OPERATION</p></td>
<td><p>Ungültiges Profil für Herunterfahren Aufzeichnung (z. B. Protokollierungsmodus Arbeitsspeicher, aber nur für das Herunterfahren unterstützt Datei ist).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







