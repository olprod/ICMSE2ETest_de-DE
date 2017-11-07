---
author: Justinha
Description: Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)
ms.assetid: 0802bca0-646e-4453-b78c-6257f1ed7e80
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)
ms.openlocfilehash: 0d2913622d1f0d44709de456710b370c58a1e27c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-on-a-vhd-native-boot"></a>Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)


Erstellen und Bereitstellen von virtuelle Festplatten (VHDs) mit systemeigenem Start-Funktionen zum Testen von Geräten oder mehrere Betriebssysteme auf einem Gerät ohne Neupartitionierung des Laufwerks zu verwalten.

## <a name="span-idcreatingvhdsspanspan-idcreatingvhdsspanspan-idcreatingvhdsspancreating-vhds"></a><span id="Creating_VHDs"></span><span id="creating_vhds"></span><span id="CREATING_VHDS"></span>Erstellen virtueller Festplatten

Sie können virtuellen Festplatten (VHD- oder .vhdx-Dateien) mithilfe des DiskPart-Tools oder Datenträger Management Microsoft Management Console (MMC) erstellen. Sie können Dateien .vhdx von PowerShell erstellen, wenn Sie die Hyper-V-Manager-Rolle installiert haben.

Sodass sie als ein Systemlaufwerk angezeigt wird, partitionieren, formatieren und das Betriebssystem zu installieren, können Sie die virtuelle Festplatte anfügen.

## <a name="span-iddeployingvhdsspanspan-iddeployingvhdsspanspan-iddeployingvhdsspandeploying-vhds"></a><span id="Deploying_VHDs"></span><span id="deploying_vhds"></span><span id="DEPLOYING_VHDS"></span>Bereitstellen von virtuellen Festplatten

Sie können eine angefügte VHD-DATEI mithilfe von Datenträgerabbildern Software wie das Tool Deployment Image Servicing and Management (DISM) unterstütztes Windows-Abbild bereitstellen. Die virtuelle Festplatte kann dann zu einem oder mehreren Systemen entweder kopiert werden, um auf einem virtuellen Computer oder für den systemeigenen Start ausgeführt werden sollen.

Weitere Informationen finden Sie unter [herunterladen und Installieren von Windows PE (Windows PE), damit Sie starten können von einem USB-Laufwerk oder eine externe USB-Festplatte](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md).

Beim ersten systemeigenen Start übergeben Sie die Konfiguration *specialize* ausgeführt wird und computerspezifische Informationen für das Windows-Betriebssystem auf die virtuelle Festplatte angewendet werden. Die Instanz der virtuellen Festplatte kann nicht auf einem anderen System kopiert oder nach Abschluss des Konfigurationsdurchgangs auf einem virtuellen Computer ausgeführt werden. Die ursprüngliche virtuelle Festplatte, die ein Windows-Abbild hat kann kopiert und auf mehreren Computern bereitgestellt werden weiterhin, wenn das Bild für die Installation mit dem Sysprep-Tool mit der Option **/ specialize** bereits vorbereitet wurde. Sie können auch eine Antwortdatei verwenden, um das Bild für die Installation vorzubereiten, mithilfe von Microsoft-Windows-Deployment | Verallgemeinern Sie die Einstellung. Weitere Informationen zu Konfigurationsphasen **specialize** und **verallgemeinern** finden Sie unter [Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md). Weitere Informationen zur Verwendung die Einstellung verallgemeinern in eine Antwortdatei verwendet finden Sie unter Windows® unbeaufsichtigte Installation Reference.

Die Windows-Bereitstellung Serverrolle unterstützt die Bereitstellung von Abbilddateien für virtuelle Festplatten zusätzlich zu WIM-Dateien. Windows Deployment Server automatisiert die netzwerkbereitstellung von Abbildern systemeigenem Start-Verwendung. Windows-Bereitstellungsserver kann zum Kopieren von VHD-Abbilds auf einer lokalen Partition und zum Konfigurieren der lokalen Boot Configuration Data (BCD) für den systemeigenen Start von der virtuellen Festplatte verwendet werden.

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[Grundlegendes zu virtuellen Festplatten mit systemeigenem Start](understanding-virtual-hard-disks-with-native-boot.md)</p></td>
<td align="left"><p>Enthält häufig auftretende Szenarien, Anforderungen und Empfehlungen für die Installation von Windows auf einer virtuellen Festplatte mit systemeigenem Start.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Starten Sie VHD (systemeigenen Start): Hinzufügen einer virtuellen Festplatte zum Startmenü](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)</p></td>
<td align="left"><p>Erstellen und Bereitstellen einer virtuellen Festplatte auf einem Zielcomputer.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Herunterladen Sie und installieren Sie Windows PE (Windows PE) aus, damit Sie von einem USB-Laufwerk oder eine externe USB-Festplatte gestartet werden kann](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)</p></td>
<td align="left"><p>Aktualisieren von einem Computer mit einem Windows 7 oder Windows 8 Boot-Umgebung, und fügen Sie eine virtuelle Festplatte zum BCD-Konfiguration.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

 

 






