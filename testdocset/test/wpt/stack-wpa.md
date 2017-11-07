---
title: Stapel
description: Stapel
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 21653c0c-ed2b-45d2-aecb-872eac23d3dd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cbddd13ceaf1b8494e89b9c09af0c807eac62984
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stack"></a>Stapel


Beschreibt die Kernelereignisse auf denen Stapel aktiviert werden sollen.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Stacks](stacks.md)&gt;

                    &lt;**Stack**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;[Stacks](stacks.md)&gt;

                                     &lt;**Stack**&gt;

                          &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;[Stacks](stacks.md)&gt;

                                     &lt;**Stack**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Stack Value = "AlpcClosePort" | "AlpcConnectFail" | "AlpcConnectRequest" ...>
</Stack>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente


### <a name="attributes"></a>Attribute

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Beschreibung</th>
<th>Datentyp</th>
<th>Erforderlich</th>
<th>Standard</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Wert</strong></p></td>
<td><p>Gibt den System-Stapel an.</p></td>
<td><p>Mögliche Werte finden Sie unter "Hinweise".</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Stapel](stacks.md)</p></td>
<td><p>Stellt eine Auflistung von Stapeln.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


In der folgenden Tabelle werden die möglichen Werte für das **Value** -Attribut beschrieben.

**AlpcClosePort**

Ein erweiterte lokalen Prozeduraufruf (ALPC) schließen Sie Portnachricht.

**AlpcConnectFail**

Verbinden Sie EINEN Fail-Nachricht.

**AlpcConnectRequest**

Verbinden Sie EINEN Anforderung.

**AlpcConnectSuccess**

EINEN verbinden die Anforderung erfolgreich abgeschlossen wurde.

**AlpcReceiveMessage**

Es wurde eine ALPC-Nachricht empfangen.

**AlpcSendMessage**

Es wurde ein ALPC Nachrichten gesendet.

**AlpcUnwait**

Eine ALPC Wait Anforderung wurde abgebrochen.

**AlpcWaitForNewMessage**

Warten Sie EINEN für neue Nachricht Anforderung.

**AlpcWaitForReply**

EINEN warten auf Antwort Anforderung.

**CcCanIWriteFail**

**CcFlushCache**

**CcFlushSection**

**CcLazyWriteScan**

**CcReadAhead**

**CcWorkitemComplete**

**CcWorkitemDequeue**

**CcWorkitemEnqueue**

**CcWriteBehind**

**ContiguousMemoryGeneration**

Ein Ereignis für die Generierung zusammenhängender Arbeitsspeicher.

**CSwitch**

Ein Kontextschalter.

**DiskFlushInit**

Initialisierung von einem Datenträger rechtsbündig.

**DiskReadInit**

Initialisierung von einem Datenträger Lesevorgang.

**DiskWriteInit**

Initialisierung des ein Schreibvorgang Datenträger.

**ExecutiveResource**

Ein Vorgang executive Ressource.

**FileCleanup**

Bereinigung von Dateien.

**FileClose**

Schließen einer Datei.

**DateiErstellen**

Erstellen einer Datei.

**Datei löschen**

Löschen einer Datei.

**FileDirEnum**

Ein Dateiverzeichnis-Enumeration.

**FileDirNotify**

Eine-e/a-Dateiereignis, das protokolliert wird, wenn eine Änderung Directory Steuerelement Interrupt Anforderung Prozedur mit einem Directory Benachrichtigung minor-Code empfangen wird.

**FileFlush**

Eine Datei rechtsbündig.

**FileFSCTL**

Ein Steuerelement Vorgang, der Datei.

**FileOpEnd**

Das Ende von Dateien.

**FileQueryInformation**

Eine Abfrage für Dateiinformationen.

**FileRead**

Ein Lesen aus einer Datei.

**FileRename**

Umbenennen einer Datei.

**FileSetInformation**

Eine Änderung in Dateiinformationen.

**FileWrite**

Ein Schreibvorgang in eine Datei.

**HardFault**

Ein schwerer Fehler.

**HeapAllocation**

Ein Heapzuordnung.

**HeapCreate**

Erstellung von einem Heap.

**HeapDestroy**

Vernichtung von einem Heap.

**HeapFree**

Freigeben von einem Heap.

**HeapRangeCreate**

Erstellen eines Bereichs Heap.

**HeapRangeDestroy**

Löschen eines Bereichs Heap.

**HeapRangeRelease**

Version von einem Heap Bereich.

**HeapRangeReserve**

Ein Bereich Heap wurde reserviert.

**HeapReallocation**

Erneutes Zuweisen von einem Heap.

**ImageLoad**

Ein Bild wurde geladen.

**ImageUnload**

Ein Bild wurde entladen.

**KernelQueueEnqueue**

Etwas wurde an die Warteschlange Kernel hinzugefügt.

**KernelQueueDequeue**

Etwas wurde aus der Warteschlange Kernel entfernt.

**KernelSignal**

**KernelSignalInit**

**KernelSync**

**KernelSyncAll**

**KernelWaitSync**

**KernelWaitSyncAll**

**MapFile**

Eine Datei.

**Mark**

**MiniFilterPostOpInit**

**MiniFilterPreOpInit**

**PageAccess**

Zugriff auf eine Seite.

**PagefaultAV**

Ein Access Violation Seitenfehler.

**PagefaultCopyOnWrite**

Eine Kopie bei Schreibvorgang Seitenfehler.

**PagefaultDemandZero**

Ein Seitenfehler bei Bedarf-0 (null).

**PagefaultGuard**

Ein Fehler auf eine Guard Page.

**PagefaultHard**

Einer harte Seitenfehler.

**PagefaultTransition**

Ein Übergang Seitenfehler.

**PagefileBackedImageMapping**

**PagefileMappedSectionCreate**

Erstellung eines zugeordneten Abschnitts einer Seitendatei.

**PagefileMappedSectionDelete**

Löschen eines zugeordneten Abschnitts einer Seitendatei.

**PageRangeAccess**

Zugriff auf einen Seitenbereich.

**PageRangeRelease**

Version von einem Seitenbereich.

**PageRelease**

Die Version einer Seite.

**PoolAllocation**

Ein arbeitsspeicherreservierung Pool.

**PoolAllocationSession**

Session-Pool-Zuweisung.

**PoolFree**

Freigeben von einer arbeitsspeicherreservierung für den Pool.

**PoolFreeSession**

Freigeben eines Pools Sitzung.

**PowerDeviceNotify**

Power Gerät Benachrichtigung.

**PowerDeviceNotifyComplete**

Das Ende einer Power Gerät Benachrichtigung.

**PowerIdleStateChange**

Eine Änderung im Leerlauf.

**PowerPerfStateChange**

Eine Änderung Power Zustand, einschließlich der alte und neue Prozessor Häufigkeit und die Prozessoren auf angewendet wird.

**PowerPostSleep**

Das Gerät entwickelte aus dem Ruhezustand.

**PowerPreSleep**

Das Gerät wird dem Ruhezustand eingeben.

**PowerSessionCallout**

Der Kernel ist einen Power Übergang ausführen.

**PowerSessionCalloutReturn**

Die **PowerSessionCallout** abgeschlossen ist und Status oder Fehler protokolliert.

**PowerSetDevicesState**

Einstellung des Geräts.

**PowerSetDevicesStateReturn**

Die **PowerSetDevicesState** abgeschlossen ist und Status oder Fehler protokolliert.

**PowerSetPowerAction**

Festlegen einer Power-Aktion.

**PowerSetPowerActionReturn**

Gibt den Status nach einer Power-Aktion.

**PowerThermalConstraint**

Ein Ereignis, das die zur Einschränkung oder Cap für ein Gerät ändert.

**ProcessCreate**

Ein Vorgang wurde erstellt.

**ProcessDelete**

Ein Prozess wurde gelöscht.

**SampledProfile**

Gibt ein aufgenommene Profil an.

**SampledProfileSetInterval**

Festlegen des Samplingintervalls für ein Profil.

**ReadyThread**

Ein Ereignis Thread bereit.

**RegistryCloseKey**

Schließen des einen Registrierungsschlüssel.

**RegistryCreateKey**

Erstellen eines Registrierungsschlüssels.

**RegistryDeleteKey**

Löschen eines Registrierungsschlüssels.

**RegistryDeleteValue**

Löschen eines Registrierungswerts.

**RegistryEnumerateKey**

Enumeration von einem Registrierungsschlüssel.

**RegistryEnumerateValueKey**

Ein Registrierungsschlüsselwert-Enumeration.

**RegistryFlush**

Eine Registrierung rechtsbündig.

**RegistryKcbCreate**

Erstellung einer Registrierung Schlüssel Control Block.

**RegistryKcbDelete**

Löschen einer Registrierung Schlüssel Control Block.

**RegistryOpenKey**

Öffnen von einem Registrierungsschlüssel.

**RegistryQueryKey**

Eine Abfrage eines Registrierungsschlüssels.

**RegistryQueryMultipleValue**

Eine Abfrage mehrere Registrierungswerte.

**RegistryQuerySecurity**

Eine Abfrage von Sicherheitseinstellungen für die Registrierung.

**RegistryQueryValue**

Eine Abfrage eines Registrierungswerts.

**RegistrySetInformation**

Die Einstellung der Registrierungsinformationen.

**RegistrySetSecurity**

Wenn Sie die Sicherheit der Registrierung festlegen.

**RegistrySetValue**

Durch Festlegen eines Registrierungswerts.

**RegistryVirtualize**

Virtualisierung der Registrierung.

**SplitIO**

Gibt an, e/a, die in separaten Pakete aufgeteilt wurde.

**SystemCallEnter**

Der Anfang eines Aufrufs System.

**SystemCallExit**

Das Ende des Anrufs System.

**ThreadCreate**

Erstellen eines Threads.

**ThreadDCEnd**

Das Ende des Kontexts einer Thread-Gerät.

**ThreadDCStart**

Der Anfang des Kontexts einer Thread-Gerät.

**ThreadDelete**

Löschen eines Threads.

**ThreadPoolCallbackCancel**

Stornieren Threadpool Rückruf an.

**ThreadPoolCallbackDequeue**

Threadpool ihrerseits entfernt aus der Warteschlange.

**ThreadPoolCallbackEnqueue**

Platzieren einen Rückruf Threadpool in der Warteschlange.

**ThreadPoolCallbackStart**

Anfang eines Rückrufs Threadpool.

**ThreadPoolCallbackStop**

Ende eines Rückrufs Threadpool.

**ThreadPoolClose**

Schließen des Threadpools.

**ThreadPoolCreate**

Erstellen eines Thread-Pools.

**ThreadPoolSetMaxThreads**

Durch die maximale Anzahl von Threads in einem Threadpool festlegen.

**ThreadPoolSetMinThreads**

Durch die minimale Anzahl von Threads in einem Threadpool festlegen.

**ThreadSetBasePriority**

Durch Festlegen der Priorität eines Threads Basiskalender.

**ThreadSetPriority**

Festlegen der Priorität eines Threads.

**TimerPeriodic**

Eine periodische Timer-Ereignis.

**TimerOnShot**

Eine einmalige Timer-Ereignis.

**UnMapFile**

Zuordnung einer Datei.

**VirtualAllocation**

Eine virtuelle Zuweisung von Arbeitsspeicher.

**VirtualFree**

Eine virtuelle Freigeben von Arbeitsspeicher.

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







