---
author: Justinha
Description: Windows-Setup-Status
ms.assetid: f67b1396-b2a5-4ac1-8104-7188e5cff54c
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows-Setup-Status
ms.openlocfilehash: a3cef06c11e28eff172e69249d205c36b91cb4ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-states"></a>Windows-Setup-Status


Es gibt mehrere Zustände, die während der Installation auf ein Bild Windows® zugewiesen. Diese Zustandsinformationen kann verwendet werden, automatisch die jeweiligen Status und Phasen von Windows Setup erkannt.

## <a name="span-idwindowssetupstatesspanspan-idwindowssetupstatesspanspan-idwindowssetupstatesspanwindows-setup-state-information"></a><span id="WindowsSetupStates"></span><span id="windowssetupstates"></span><span id="WINDOWSSETUPSTATES"></span>Windows Setup Zustandsinformationen


Der Windows-Bild-Zustand ist an zwei Orten, in der Registrierung und in einer Datei gespeichert.

-   In der Registrierung:

    SCHLÜSSEL: **HKEY\_LOKALE\_COMPUTER\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Setup\\Zustand**

    TYP: REG\_SU

    WERT: *StateName*

-   In einer Datei:

    DATEI: %Windir%\\Setup\\Zustand\\State.ini

    ABSCHNITT: \[Zustand\]

    WERT: *StateName*

In der folgenden Tabelle werden die Werte, die für *StateName*vorhanden sind.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Bundesland name</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_COMPLETE</p></td>
<td align="left"><p>Das Bild wurde erfolgreich installiert. Konfigurationsphasen <strong>specialize</strong> und <strong>OobeSystem</strong> sind abgeschlossen. Dieses Bild kann nicht auf einem Computer mit einer anderen Hardwarekonfiguration, da es jetzt hardwareunabhängige ist bereitgestellt werden. Um dieses Bild für einen Computer bereitzustellen, der eine anderen Hardwarekonfiguration hat, müssen Sie ausführen <strong>Sysprep / verallgemeinern</strong>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE _UNDEPLOYABLE</p></td>
<td align="left"><p>Dies ist der Standardstatus für ein Bild in einer bestimmten Phase der Windows-Installation, die noch nicht abgeschlossen ist. Wenn ein Prozess den Wert IMAGE_STATE abfragt und IMG_UNDEPLOYABLE zurückgegeben wird, wird das Bild in einem der folgenden Zustände:</p>
<ul>
<li><p>Das Setup ausgeführt wird und die Phase nicht vollständig ausgeführt wurde. Nach eine bestimmte Phase abgeschlossen ist, wird IMAGE_STATE auf einen entsprechenden Abschlusswert festgelegt.</p></li>
<li><p>Wenn online abgefragt, wenn Setup nicht ausgeführt wird, ein Fehler aufgetreten beim Setup Phasen abschließen. Dieses Bild muss neu installiert werden.</p></li>
<li><p>Offline abgefragt wird, wird das Bild eine Phase wurde nicht abgeschlossen und werden nie bereitgestellt werden.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_GENERALIZE_RESEAL_TO_OOBE</p></td>
<td align="left"><p>Das Bild wurde erfolgreich abgeschlossen <strong>verallgemeinern</strong> Konfiguration und wird in <strong>Konfigurationsphase</strong> fortgesetzt, wenn Setup initiiert wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE_GENERALIZE_RESEAL_TO_AUDIT</p></td>
<td align="left"><p>Das Bild wurde erfolgreich abgeschlossen <strong>verallgemeinern</strong> Konfiguration und wird im Überwachungsmodus fortgesetzt, wenn Setup initiiert wird.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE</p></td>
<td align="left"><p>Das Bild wurde erfolgreich abgeschlossen <strong>specialize</strong> und wird in <strong>Konfigurationsphase</strong> fortgesetzt, wenn Setup initiiert wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE_SPECIALIZE_RESEAL_TO_AUDIT</p></td>
<td align="left"><p>Das Bild wurde erfolgreich abgeschlossen <strong>specialize</strong> Konfiguration und wird im Überwachungsmodus fortgesetzt, wenn Setup initiiert wird.</p></td>
</tr>
</tbody>
</table>

 

Die folgenden Beispiele zeigen, wie Sie Zugriff auf Statusinformationen.

-   Zugriff auf Statusinformationen aus der Registrierung:

    ``` syntax
    C:\>reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Setup\State /v Imag
    eState

    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Setup\State
        ImageState    REG_SZ    IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE
    ```

-   Zugriff auf Statusinformationen aus einer Datei:

    ``` syntax
    C:\>type %windir%\Setup\State\State.ini
    [State]
    ImageState="IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE"
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows Setup-Befehlszeilenoptionen](windows-setup-command-line-options.md)

[Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[Windows-Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md)

 

 






