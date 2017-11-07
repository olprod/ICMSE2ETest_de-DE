---
author: Justinha
Description: 'Secure Boot isn''t configured correctly: troubleshooting'
ms.assetid: a2b9b89f-9d42-4537-a3f8-0403cd67df16
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Secure Boot isn''t configured correctly: troubleshooting'
ms.openlocfilehash: b6d799d77e6265b0892fe981fc603194ecdd2193
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot-isnt-configured-correctly-troubleshooting"></a>Sichere Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung


Das Wasserzeichen "Sicheren Boot ist nicht richtig konfiguriert" wird auf dem Windows-Desktop angezeigt, wenn der PC verwenden, die Sicherheitsfunktion Secure Boot ist jedoch das Feature ist nicht aktiviert oder nicht richtig konfiguriert.

Diese Meldung kann nach dem Aktualisieren des PCs aus Windows 8 Windows 8.1 angezeigt.

## <a name="span-idwhatissecurebootspanspan-idwhatissecurebootspanspan-idwhatissecurebootspanwhat-is-secure-boot"></a><span id="What_is_Secure_Boot_"></span><span id="what_is_secure_boot_"></span><span id="WHAT_IS_SECURE_BOOT_"></span>Was ist Secure Boot?


Secure Boot können Sie sicherstellen, dass Ihrem PC gestartet wird, wobei nur Firmware an, die vom Hersteller vertrauenswürdig ist. Weitere Informationen zu Secure Boot finden Sie unter [Secure Boot Overview](secure-boot-overview.md).

## <a name="span-idismypcunsafespanspan-idismypcunsafespanspan-idismypcunsafespanis-my-pc-unsafe"></a><span id="Is_my_PC_unsafe_"></span><span id="is_my_pc_unsafe_"></span><span id="IS_MY_PC_UNSAFE_"></span>Ist mein PC unsichere?


PC möglicherweise OK, aber es ist nicht als geschützt, wie es werden konnte, da Secure Boot nicht ausgeführt wird.

Sie müssen möglicherweise deaktivieren Secure Boot Wenn einige Hardware, Grafikkarten oder wie Linux oder früheren Versionen von Windows-Betriebssystemen ausgeführt werden soll. Weitere Informationen finden Sie unter [Secure Boot deaktivieren](disabling-secure-boot.md).

Auf Ihrem PC überprüfen Sie den Status des Secure Boot. Klicken Sie auf `Start`, und geben Sie msinfo32 und drücken die EINGABETASTE. Unter System lässt sich sagen können Sie die BIOS-Modus und Secure Boot Status angezeigt. Wenn BIOS-Modus UEFI ist und Secure Boot Zustand deaktiviert ist, ist Secure Boot deaktiviert.

## <a name="span-idcanijustdismissthisalertorremovethewatermarkspanspan-idcanijustdismissthisalertorremovethewatermarkspanspan-idcanijustdismissthisalertorremovethewatermarkspancan-i-just-dismiss-this-alert-or-remove-the-watermark"></a><span id="Can_I_just_dismiss_this_alert_or_remove_the_watermark_"></span><span id="can_i_just_dismiss_this_alert_or_remove_the_watermark_"></span><span id="CAN_I_JUST_DISMISS_THIS_ALERT_OR_REMOVE_THE_WATERMARK_"></span>Kann ich nur schließen diese Warnung oder entfernen das Wasserzeichen?


Ja. Rufen Sie Windows Update für einen Patch, der das Wasserzeichen entfernen Ruft ab.

-   Windows 8.1 und Windows Server 2012 R2-Benutzer können auch herunterladen dieser Patch manuell: [Update entfernt das Wasserzeichen "Windows 8.1 SecureBoot ist nicht ordnungsgemäß konfiguriert" in Windows 8.1 und Windows Server 2012 R2 (Microsoft Knowledge Base Artikel ID 2902864)](http://go.microsoft.com/fwlink/p/?linkid=329932)

-   Windows 8.1 RT: Rufen Sie diesen Patch über Windows Update.

## <a name="span-ididliketousethisfeaturehowcanienableitspanspan-ididliketousethisfeaturehowcanienableitspanid-like-to-use-this-feature-how-can-i-enable-it"></a><span id="i_d_like_to_use_this_feature._how_can_i_enable_it_"></span><span id="I_D_LIKE_TO_USE_THIS_FEATURE._HOW_CAN_I_ENABLE_IT_"></span>Ich möchte dieses Feature verwenden können. Wie kann ich es aktivieren?


Versuchen Sie, aktivieren Secure Boot durch Verwenden der PC-BIOS-Menüs.

**Warnung**  
Seien Sie vorsichtig bei der BIOS-Einstellungen ändern. Klicken Sie im Menü BIOS eignet sich für fortgeschrittene Benutzer, und es ist möglich, eine Einstellung zu ändern, die Ihren PC verhindern konnte nicht ordnungsgemäß gestartet. Befolgen Sie die Anweisungen des Herstellers genau sein.

 

**Aktivieren der sicheren Boot**

1.  Öffnen Sie das BIOS-PC-Menü. Sie können dieses Menü häufig zugreifen, eine Taste zu drücken, während die Sequenz Hochfahren wie F1, F2, F12 oder ESC-Taste.

    Oder von Windows: Wechseln Sie zu **Einstellungen Charm &gt; Einstellungen ändern PC &gt; Update und Recovery &gt; Wiederherstellung &gt; erweiterte Startoptionen: jetzt neu starten**. Wenn der PC neu gestartet wird, wechseln Sie zur **Troubleshoot &gt; erweiterte Optionen: UEFI Firmware Einstellungen**.

2.  Hier finden Sie die **Secure Boot** -Einstellung, und legen sie Sie, wenn möglich **aktiviert**. Diese Option ist in der Regel in der Registerkarte **Sicherheit** , Registerkarte " **Start** ", oder auf der Registerkarte **Authentifizierung** .

    Wählen Sie auf einige PCs **Benutzerdefiniert**, und Laden Sie die Secure Boot-Schlüssel, die in den PC integriert sind.

    Wenn der PC das Secure Boot aktivieren nicht zulässt, versuchen Sie das BIOS auf die herstellereinstellung zurückgesetzt.

3.  Änderungen speichern und beenden. Der PC neu gestartet wird.

4.  Wenn der PC nicht nach dem Aktivieren der Secure Boot gestartet ist, wechseln Sie wieder in den Menüs BIOS deaktivieren Secure Boot, und versuchen Sie, den PC erneut zu starten.

5.  In einigen Fällen müssen Sie aktualisieren oder vor Sie Secure Boot aktivieren können Ihren PC auf den ursprünglichen Zustand zurückgesetzt. Weitere Informationen finden Sie unter [Wiederherstellen, aktualisieren oder Zurücksetzen von Ihrem PC](http://go.microsoft.com/fwlink/p/?linkid=279534).

6.  Wenn die oben beschriebenen Schritte funktionieren nicht, und Sie weiterhin das Secure Boot-Feature verwenden möchten, wenden Sie sich an den Hersteller Ihres Hilfe.

    Weitere Schritte zur Fehlerbehebung für PC-Hersteller: finden Sie unter [Secure Boot ist nicht ordnungsgemäß konfiguriert: ermitteln, ob der PC-Option in einem Fertigung-Modus (Info für Hersteller) ist](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Warum ist es "SecureBoot ist nicht ordnungsgemäß konfiguriert" Wasserzeichen auf meinem Desktop?](http://go.microsoft.com/fwlink/?LinkId=624321)

[Secure Boot – Übersicht](secure-boot-overview.md)

[Microsoft Support-KB-Artikel 2902864](http://support.microsoft.com/kb/2902864)

[Deaktivieren von sicheren Boot](disabling-secure-boot.md)

 

 






