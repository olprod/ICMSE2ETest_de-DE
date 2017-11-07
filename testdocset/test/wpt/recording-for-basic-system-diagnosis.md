---
title: "Aufzeichnung für die Diagnose grundlegende System"
description: "Aufzeichnung für die grundlegende System-Diagnose"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bfaa08d7-0bb0-4786-a925-dc54c6f78ffc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 311f23a2af96a3bdb83c49c6e40e48440381c8f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recording-for-basic-system-diagnosis"></a>Aufzeichnung für die grundlegende System-Diagnose


In der Standardeinstellung führt Windows Performance Aufzeichnung (WPR) das **Allgemeine** Profil für jede Aufzeichnung. Dieses Profil werden grundlegende Systemprobleme und die Leistungsdaten.

Inhalt dieses Artikels:

-   [Allgemeine Profileinstellungen](#generalpro)

-   [Identifizieren von Leistungsproblemen anhaltend](#sus)

-   [Identifizieren von Leistungsproblemen vorübergehende](#trans)

## <a name="a-href-idgeneralproageneral-profile-settings"></a><a href="" id="generalpro"></a>Allgemeine Profileinstellungen


Das **Allgemeine** Profil verwendet die folgenden Kollektoren:

**NT-Kernel-Protokollierung-Sammlung**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Puffergröße (KB)</p></td>
<td><p>1024</p></td>
</tr>
<tr class="even">
<td><p>Anzahl der Puffer</p></td>
<td><p>198</p></td>
</tr>
<tr class="odd">
<td><p>System-Schlüsselwörter</p></td>
<td><p>CpuConfig, CSwitch, DiskIO, DPC, HardFaults, unterbrechen, KernelQueue, Ladeprogramm, MemoryInfo, ProcessCounter, Strom, ProcessThread, ReadyThread, SampledProfile, ThreadPriority</p></td>
</tr>
</tbody>
</table>

 

**WPR\_initiiert\_WPR Ereignissammlung**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Puffergröße (KB)</p></td>
<td><p>1024</p></td>
</tr>
<tr class="even">
<td><p>Anzahl der Puffer</p></td>
<td><p>39</p></td>
</tr>
<tr class="odd">
<td><p>Anbieter</p></td>
<td><p>PerfTrack:: 0 x 04</p>
<p>Microsoft-Windows-fesselnden-Shell: 0x0000000000100000: 0 x 04</p>
<p>Microsoft-Windows-Kernel-Leistung: 0x0000000000000004: 0xff</p>
<p>Microsoft Windows Win32k: 0x0000000000402000: 0xff</p>
<p>Microsoft-Windows-WLAN-AutoConfig: 0x0000000000000200: 0xff</p>
<p>.NET common Language Runtime: 0x0000000000000098: 0 x 05</p>
<p>Microsoft-JScript: 0 x 0000000000000001: 0xff e7ef96be-969f-414f - 97d 7-3ddb7b558ccc: 0 x 0000000000002000: 0xff</p>
<p>MUI-Ressource Trace:: 0xff</p>
<p>Microsoft Windows COMRuntime: 0x0000000000000003: 0xff</p>
<p>Microsoft-Windows-Netzwerke-Korrelation:: 0xff</p>
<p>Microsoft-Windows-RPCSS:: 0 x 04</p>
<p>Microsoft-Windows-RPC-:: 0 x 04 a669021c-c450-4609-a035-5af59af4df18:: 0 x 00</p>
<p>Microsoft-Windows-Kernel-Prozessor-Energie:: 0xff</p>
<p>Microsoft-Windows-Kernel-StoreMgr:: 0xff e7ef96be-969f-414f - 97d 7-3ddb7b558ccc:: 0xff</p>
<p>Microsoft Windows UserModePowerService:: 0xff</p>
<p>Microsoft-Windows-Win32k:: 0xff</p>
<p>Microsoft Windows ReadyBoostDriver:: 0xff</p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen zu Kollektoren und Anbieter finden Sie unter [Kollektoren](collectors.md) und [Anbieter](providers.md).

## <a name="a-href-idsusaidentify-sustained-performance-issues"></a><a href="" id="sus"></a>Identifizieren von Leistungsproblemen anhaltend


Um anhaltend Leistungsprobleme identifiziert haben, können Sie das **Allgemeine** Profil zusammen mit den anderen Standardeinstellungen ausführen. Dies sind: **Verbose** Logging Details und melden Sie sich auf den **Speicher**. Nach dem start der aufzeichnungs in WPR, bleibt sie bis zum Beenden und speichern die Aufzeichnung.

## <a name="a-href-idtransaidentify-transient-performance-issues"></a><a href="" id="trans"></a>Identifizieren von Leistungsproblemen vorübergehende


Da jedoch nicht vorhersehbar Wenn vorübergehende Leistungsprobleme stattfindet, müssen Sie das **Allgemeine** Profil ausführen, bis das Problem herausstellt.

**Vorübergehende Leistungsprobleme identifiziert.**

1.  Wenn die Optionen ausgeblendet sind, klicken Sie auf dem Bildschirm WPR auf **Weitere Optionen**.

2.  Wählen Sie aus dem Dropdownmenü **Leistung Szenarien** **Allgemein**.

3.  Wählen Sie aus dem Dropdownmenü **Protokollierung Modus** **Speicher**.

4.  Klicken Sie auf **Start** , und führen Sie die Aufzeichnung, bis das Problem auftritt.

5.  Klicken Sie auf **Speichern**, und klicken Sie dann auf **Durchsuchen** , um die Datei speichern, indem Sie einen Namen oder einem anderen Speicherort als Standard verwenden. Der Standardspeicherort ist die ** \\Benutzer\\%UserName%\\Dokumente\\WPR Dateien** Ordner auf dem Systemlaufwerk.

6.  Geben Sie eine Beschreibung des Problems.

7.  Klicken Sie auf **Speichern**.

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

[Leistung Szenarien](performance-scenarios.md)

 

 







