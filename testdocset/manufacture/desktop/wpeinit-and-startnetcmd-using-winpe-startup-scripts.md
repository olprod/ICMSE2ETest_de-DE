---
author: Justinha
Description: 'Wpeinit und Startnet.cmd: Verwenden von Skripts zum Starten des Windows PE'
ms.assetid: d43621bb-b9ab-4e19-8fb4-8d05d5ee3d07
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Wpeinit und Startnet.cmd: mithilfe von Skripts zum Starten des Windows PE'
ms.openlocfilehash: c1071e6ddcdb51f1506bda8f4927eb0e78cd9f1b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpeinit-and-startnetcmd-using-winpe-startup-scripts"></a>Wpeinit und Startnet.cmd: Verwenden von Skripts zum Starten des Windows PE


Verwenden Sie Wpeinit und Startnet.cmd Skripts zum Starten des ausführen, wenn Windows PE (Windows PE) zuerst ausgeführt wird.

Wpeinit Ausgaben Melden von Nachrichten an **C:\\Windows\\system32\\wpeinit.log**.

## <a name="span-idstartnetcmdspanspan-idstartnetcmdspanstartnetcmd"></a><span id="startnet.cmd"></span><span id="STARTNET.CMD"></span>Startnet.cmd


Sie können benutzerdefinierte Befehlszeilenskripts in Windows PE mithilfe Startnet.cmd hinzufügen. Windows PE enthält standardmäßig ein Startnet.cmd Skript befindet sich unter %SystemRoot%\\System32 angepassten Windows PE-Abbild.

Startnet.cmd startet Wpeinit.exe. Wpeinit.exe installiert Plug & Play-Geräte, verarbeitet Unattend.xml Einstellungen und lädt Netzwerkressourcen.

Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

## <a name="span-idwpeinitcommand-lineoptionsspanspan-idwpeinitcommand-lineoptionsspanspan-idwpeinitcommand-lineoptionsspanwpeinit-command-line-options"></a><span id="Wpeinit_Command-Line_Options"></span><span id="wpeinit_command-line_options"></span><span id="WPEINIT_COMMAND-LINE_OPTIONS"></span>Wpeinit Befehlszeilenoptionen


Die folgende Befehlszeile aus ist für Wpeinit verfügbar:

**Wpeinit** \[-für die unbeaufsichtigte Installation:*&lt;Pfad\_auf\_Antwort\_Datei&gt; *\]

Beispiel:

``` syntax
Wpeinit -unattend:"C:\Unattend-PE.xml"
```

## <a name="span-idsupportedunattendsettingsspanspan-idsupportedunattendsettingsspanspan-idsupportedunattendsettingsspansupported-unattend-settings"></a><span id="Supported_Unattend_settings"></span><span id="supported_unattend_settings"></span><span id="SUPPORTED_UNATTEND_SETTINGS"></span>Unterstützte für die unbeaufsichtigte Installation-Einstellungen


Sie können eine Antwortdatei erstellen und geben Sie die folgenden Einstellungen für die Verwendung mit Windows PE:

-   Einrichten von Microsoft Windows /[Anzeigen](https://msdn.microsoft.com/library/windows/hardware/dn915285)

-   Einrichten von Microsoft Windows /[EnableFirewall](https://msdn.microsoft.com/library/windows/hardware/dn915375)

-   Einrichten von Microsoft Windows /[com+](https://msdn.microsoft.com/library/windows/hardware/dn915383)

-   Einrichten von Microsoft Windows /[LogPath](https://msdn.microsoft.com/library/windows/hardware/dn915490)

-   Einrichten von Microsoft Windows /[Auslagerungsdatei](https://msdn.microsoft.com/library/windows/hardware/dn915671)

-   Einrichten von Microsoft Windows /[neu starten](https://msdn.microsoft.com/library/windows/hardware/dn915783)

-   Einrichten von Microsoft Windows /[RunAsynchronous](https://msdn.microsoft.com/library/windows/hardware/dn915800)

-   Einrichten von Microsoft Windows /[RunSynchronous](https://msdn.microsoft.com/library/windows/hardware/dn915804)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Identifizieren Sie Laufwerkbuchstaben mit einem Skript](winpe-identify-drive-letters.md)

[Windows PE für Windows 10](winpe-intro.md)

[Winpeshl.ini Referenz: Starten einer app beim Start von Windows PE](winpeshlini-reference-launching-an-app-when-winpe-starts.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Referenz für unbeaufsichtigte Windows-Setup](http://go.microsoft.com/fwlink/?LinkId=206281)

 

 






