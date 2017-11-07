---
author: Justinha
Description: Festplatte Speicherort Pfadformat
ms.assetid: 9f9d96ae-4fec-487d-95d2-ffd09b7d9fd1
MSHAttr: PreferredLib:/library/windows/hardware
title: Festplatte Speicherort Pfadformat
ms.openlocfilehash: 1d4ffeb42480ecd7520ced5b9ec1c731e831033f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hard-disk-location-path-format"></a>Festplatte Speicherort Pfadformat


In diesem Thema wird das Format der Festplatte-Pfad zum Speicherort. Dieses Format wird verwendet, um jedem Datenträger in das DiskPart-Tool ermitteln Sie mithilfe des Pfads zum Speicherort. Der Pfad zum Speicherort Formatierung basiert auf der physikalischen Verbindung mit dem Computer.

Anweisungen, in denen beschrieben so konfigurieren Sie Windows®, um ein Laufwerk, auf der Grundlage der Pfad zum Speicherort Formats zu ermitteln, finden Sie unter [Konfigurieren von mehreren Festplatten](configure-multiple-hard-drives.md).

## <a name="span-idlocationpathformatspanspan-idlocationpathformatspanspan-idlocationpathformatspanlocation-path-format"></a><span id="LocationPathFormat"></span><span id="locationpathformat"></span><span id="LOCATIONPATHFORMAT"></span>Pfad zum Speicherort Format


Die grundlegende Syntax für den Pfad zum Speicherort Festplatten mit einer (SCSI = Small Computer System Interface), Serial Attached SCSI (SAS) oder Array von unabhängigen RAID (Redundant Disks) Bus-Typ ist wie folgt auf:

&lt;*Plug & Play-Pfad des Adapters*&gt;**\#**&lt;*Bus-Typ*&gt;(**P**&lt;*Pfad-ID*&gt;**T**&lt;*Ziel-ID*&gt;**L**&lt;*LUN-ID*&gt;)

Die grundlegende Syntax für den Pfad zum Speicherort für Datenträger, auf die ein Advanced Technology Attachment (ATA) oder ATA-SATA (Serial) Bus-Typ ist lautet wie folgt:

&lt;*Plug & Play-Pfad des Adapters*&gt;**\#**&lt;*Bus-Typ*&gt;(**C**&lt;*Channel-ID*&gt;**T**&lt;*Ziel-ID*&gt;**L**&lt;*LUN-ID*&gt;)

In der folgenden Tabelle werden die Elemente in den Pfad zum Speicherort definiert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>&lt;<em>Plug & Play-Pfad des Adapters</em>&gt;</p></td>
<td align="left"><p>Der Pfad des Adapters. Rufen Sie den Pfad durch Aufrufen der SetupDiGetDeviceProperty mit der DEVPKEY_Device_LocationPaths-Eigenschaft.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>#</strong>&lt;<em>Bus-Typ</em>&gt;</p></td>
<td align="left"><p>Die folgenden Arten: ATA-GERÄTS, SCSI, SAS- oder RAID.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>P</strong>&lt;<em>Path ID</em>&gt;</p></td>
<td align="left"><p>Der SCSI_ADDRESS PathId-Feld. Rufen Sie die PathID, indem Sie IOCTL_SCSI_GET_ADDRESS aufrufen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>C</strong>&lt;<em>Channel-ID</em>&gt;</p></td>
<td align="left"><p>Der SCSI_ADDRESS PathId-Feld. Rufen Sie die PathID, indem Sie IOCTL_SCSI_GET_ADDRESS aufrufen.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Bei Datenträgern, die den Typ des ATA/SATA-Bus verwenden, bezieht sich Kanal-ID zum Feld PathID. Das Präfix C wird weiterhin verwendet.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>T</strong>&lt;<em>Ziel-ID</em>&gt;</p></td>
<td align="left"><p>TargetId Feld der SCSI_ADDRESS. Abrufen der TargetId IOCTL_SCSI_GET_ADDRESS aufrufen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>L</strong>&lt;<em>LUN ID</em>&gt;</p></td>
<td align="left"><p>Logische (Organizational Unit Number, LUN)-Feld der SCSI_ADDRESS. Rufen Sie die LUN, indem Sie IOCTL_SCSI_GET_ADDRESS aufrufen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idexamplesspanspan-idexamplesspanspan-idexamplesspanexamples"></a><span id="Examples"></span><span id="examples"></span><span id="EXAMPLES"></span>Beispiele für


Die folgende Tabelle enthält ein Beispiel für den Pfad für die einzelnen Bus oder Datenträger:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Bus oder Datenträgertyp</th>
<th align="left">Pfad zum Speicherort</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Integrated Development Environment (IDE), ATA-GERÄTS, Parallel ATA-GERÄT (PATA) oder SATA</p></td>
<td align="left"><p>PCIROOT(0)#PCI(0100)#ATA(C01T03L00)</p></td>
</tr>
<tr class="even">
<td align="left"><p>SCSI</p></td>
<td align="left"><p>PCIROOT(0)#PCI(1C00)#PCI(0000)#SCSI(P00T01L01)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SAS</p></td>
<td align="left"><p>PCIROOT(1)#PCI(0300)#SAS(P00T03L00)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Peripherer Komponente Interconnect (PCI) RAID</p></td>
<td align="left"><p>PCIROOT(0)#PCI(0200)#PCI(0003)#PCI(0100)#RAID(P02T00L00)</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren Sie mehrerer Festplatten](configure-multiple-hard-drives.md)

[Die Befehlszeilensyntax DiskPart](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






