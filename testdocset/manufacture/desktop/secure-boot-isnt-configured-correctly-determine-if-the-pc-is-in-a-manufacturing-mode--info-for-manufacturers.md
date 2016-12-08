---
author: Justinha
Description: 'Secure Boot isn''t configured correctly: Determine if the PC is in a manufacturing mode (info for manufacturers)'
ms.assetid: 68f143f8-c689-474f-a7b7-2f0fe7b0f1ec
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Secure Boot isn''t configured correctly: Determine if the PC is in a manufacturing mode (info for manufacturers)'
ms.openlocfilehash: 8a5a3413a4135dc69e74cea3998844e3910bb9af
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode-info-for-manufacturers"></a>Sichere Boot ist nicht ordnungsgemäß konfiguriert: ermitteln, ob der PC-Option in einem Fertigung-Modus (Info für Hersteller) ist


Während der Produktion PCs, wenn das Wasserzeichen "Sicheren Boot ist nicht richtig konfiguriert" auf dem Windows-Desktop angezeigt wird möglicherweise müssen Sie entscheiden, ob Secure Boot deaktiviert ist, oder wenn der Computer im Fertigung/Debugmodus befindet. Der PC ist im Modus Fertigung/Debuggen, wenn eine Richtlinie nicht in der Produktion installiert ist. Weitere Informationen hierzu finden Sie im Whitepaper: **Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung,** auf dem [Microsoft Connect](http://go.microsoft.com/fwlink/p/?linkid=92770) -Website oder in Kontakt Ihrem Microsoft Konto Manager.

**Hinweis**  
**Haben Sie das Wasserzeichen "Sicheren Boot ist nicht richtig konfiguriert" nach dem Upgrade auf Windows 8.1, Windows Server 2012 R2 oder Windows RT 8.1 gesehen?**

Werde veröffentlichen wir bald ein Patches, das das Wasserzeichen entfernen dient zum Abrufen.

Windows 8.1 und Windows Server 2012 R2-Benutzer können einen Patch zum sofortigen Entfernen von Wasserzeichen installieren: [Microsoft Knowledge Base-Artikel ID 2902864](http://go.microsoft.com/fwlink/p/?linkid=329932).

Weitere Informationen finden Sie unter [Secure Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung](secure-boot-isnt-configured-correctly-troubleshooting.md).

 

## <a name="span-iddeterminingifthepcisinamanufacturingmodespanspan-iddeterminingifthepcisinamanufacturingmodespanspan-iddeterminingifthepcisinamanufacturingmodespandetermining-if-the-pc-is-in-a-manufacturing-mode"></a><span id="Determining_if_the_PC_is_in_a_manufacturing_mode"></span><span id="determining_if_the_pc_is_in_a_manufacturing_mode"></span><span id="DETERMINING_IF_THE_PC_IS_IN_A_MANUFACTURING_MODE"></span>Feststellen, ob der PC-Option in einem Fertigung-Modus ist


Sie können eine der folgenden Methoden verwenden, um zu bestimmen, ob Secure Boot deaktiviert wurde oder wenn der Computer im ein Fertigung / Debug-Modus befindet.

-   **Verwenden Sie MSInfo32.** Klicken Sie auf **Start**, geben Sie **msinfo32**. Wenn **BIOS-Modus: UEFI** **UEFI** ist und **Secure Boot Zustand** ist **DEAKTIVIERT**, und klicken Sie dann Secure Boot deaktiviert ist.

-   **Überprüfen Sie die Ereignisprotokolle**. Wechseln Sie zu **Starten &gt; Anzeigen von Ereignisprotokollen &gt; Anwendungs- und Dienstprotokolle &gt; Microsoft &gt; Windows &gt; VerifyHardwareSecurity &gt; Admin**, und suchen Sie nach jedem dieser Ereignisse protokolliert:

    "Sicheren Boot ist deaktiviert. Aktivieren Sie Secureboot durch die Systemfirmware." (Der PC ist im Modus UEFI und Secure Boot ist deaktiviert.)

    "Nicht in der Produktion Secure Boot Richtlinie wurde erkannt. Entfernen von Debug-Vorabversion Richtlinie über die Systemfirmware." (Der PC ist in der Fertigung/Debugmodus.)

-   **Verwenden von PowerShell-Befehlen.**

    Öffnen Sie ein PowerShell-Fenster als Administrator, und verwenden Sie folgende Befehle aus:

    `Confirm-SecureBootUEFI`: überprüft, ob Secure Boot deaktiviert ist. Antworten:

    -   "True": sichere Boot ist aktiviert, und das Wasserzeichen wird nicht angezeigt.

    -   "False": sichere Boot ist deaktiviert, und Wasserzeichen angezeigt wird.

    -   "Cmdlet auf dieser Plattform nicht unterstützt": unterstützen der PC möglicherweise nicht Secure Boot oder der PC im Legacymodus BIOS konfiguriert werden kann. Das Wasserzeichen wird nicht angezeigt.

    -   "Kann nicht auf die entsprechenden Berechtigungen festlegen. Der Zugriff wurde verweigert. ": PowerShell schließen und erneut öffnen sie als Administrator.

    "Get-SecureBootPolicy": überprüft, ob Sie eine außerhalb der Produktion Richtlinie installiert haben. Antworten:

    -   "{77FA9ABD-0359-4D32-BD60-28F4E78F784B}": die richtige Secure Boot-Richtlinie ist vorhanden.

    -   Alles andere GUID: der PC ist im Modus Manufacturing/Debuggen und die GUID für die nicht für die Produktion Secure Boot-Richtlinie angezeigt wird.

    -   "Sicheren Boot-Richtlinie ist auf diesem Computer nicht aktiviert": entweder Secure Boot ist deaktiviert, oder der Computer konfiguriert ist, starten Sie legacy-BIOS-Modus. Wenn der Computer im legacy-BIOS-Modus befindet, sollte das Wasserzeichen nicht angezeigt werden.

    -   "Falsche Authentifizierungsdaten": PowerShell schließen und erneut öffnen sie als Administrator.

## <a name="span-idhowdoifixitspanspan-idhowdoifixitspanspan-idhowdoifixitspanhow-do-i-fix-it"></a><span id="How_do_I_fix_it_"></span><span id="how_do_i_fix_it_"></span><span id="HOW_DO_I_FIX_IT_"></span>Wie behebe ich es?


**Wenn Secure Boot ist deaktiviert**, wieder zu aktivieren. Weitere Informationen finden Sie unter [Secure Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung](secure-boot-isnt-configured-correctly-troubleshooting.md).

**Wenn Secure Boot ist aktiviert, aber der PC im Fertigung/Debug-Modus ist**, müssen Sie die Richtlinie nicht in der Produktion deinstallieren. Weitere Informationen hierzu finden Sie im Whitepaper: **Windows 8.1 Secure Boot Schlüssel Erstellung und Verwaltung,** auf dem [Microsoft Connect](http://go.microsoft.com/fwlink/p/?linkid=92770) -Website oder in Kontakt Ihrem Microsoft Konto Manager.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Sichere Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung](secure-boot-isnt-configured-correctly-troubleshooting.md)

 

 






