---
author: Justinha
Description: Deaktivieren von sicheren Boot
ms.assetid: 2b98718d-13ce-4a5d-bd89-d276a0dc493d
MSHAttr: PreferredLib:/library/windows/hardware
title: Deaktivieren von sicheren Boot
ms.openlocfilehash: bd984c1e34181abaa16a37f3a678289379002077
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disabling-secure-boot"></a>Deaktivieren von sicheren Boot


Sie müssen möglicherweise deaktivieren Secure Boot, wenn einige PC Grafikkarten, Hardware oder wie Linux oder frühere Version von Windows-Betriebssystemen ausgeführt werden soll.

Secure Boot hilft, um sicherzustellen, dass es sich bei Ihrem PC gestartet wird, wobei nur Firmware, die vom Hersteller vertrauenswürdig ist.

Für die meisten PCs teilnehmen können Sie über die PC Firmware (BIOS) Menüs Secure Boot deaktivieren. Logo zertifizierten Windows RT 8.1 und Windows RT PCs muss Secure Boot konfiguriert werden, damit es nicht deaktiviert werden kann.

**Warnung**  
-   Nach dem Deaktivieren Secure Boot und andere Software und Hardware installiert haben, kann Secure Boot erneut aktivieren, ohne Ihren PC auf den Status Factory wiederherstellen schwierig sein.

-   Seien Sie vorsichtig bei der BIOS-Einstellungen ändern. Das BIOS-Menü für fortgeschrittene Benutzer dient, und es ist möglich, eine Einstellung zu ändern, die Ihren PC nicht ordnungsgemäß gestartet verhindern könnten. Achten Sie darauf, dass Sie genau befolgen der Anweisungen des Herstellers.

 

**Secure Boot zu deaktivieren:**

1.  Überlegen Sie, ob es erforderlich ist, bevor Sie Secure Boot deaktivieren. Von Zeit zu Zeit kann vom Hersteller Ihrer die Liste der vertrauenswürdigen Hardware und Treiber Betriebssysteme für Ihren PC aktualisieren. Um nach Updates suchen, wechseln Sie zur Windows Update oder Überprüfen Sie der Website des Herstellers.

2.  Öffnen Sie das BIOS-PC-Menü. Sie können dieses Menü häufig zugreifen, eine Taste zu drücken, während die Sequenz Hochfahren wie F1, F2, F12 oder ESC-Taste.

    Oder von Windows, halten Sie die UMSCHALTTASTE gedrückt, während Sie auf **neu starten**. Wechseln Sie zu **Problembehandlung bei &gt; erweiterte Optionen: UEFI Firmware Einstellungen**.

3.  Hier finden Sie die **Secure Boot** -Einstellung, und legen sie Sie, wenn möglich auf **deaktiviert**. Diese Option ist in der Regel in der Registerkarte **Sicherheit** , Registerkarte " **Start** ", oder auf der Registerkarte **Authentifizierung** .

4.  Änderungen speichern und beenden. Neustart der PC.

5.  Installieren Sie die Grafikkarte, Hardware oder Betriebssystem, das nicht mit Secure Boot kompatibel ist.

    In einigen Fällen müssen Sie andere Einstellungen in der Firmware, wie das Aktivieren einer Kompatibilität unterstützen Modul (CSM) zur Unterstützung von älteren BIOS-Betriebssystemen zu ändern. Um eine CSM verwenden, müssen Sie auch mithilfe des Master Boot Record (MBR), das die Festplatte neu formatiert, und installieren Sie Windows neu. Weitere Informationen finden Sie unter [Windows Setup: Installieren von MBR- oder GPT-Formatvorlage partitionieren](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md).

6.  Wenn Sie Windows 8.1 nutzen, können Sie Wasserzeichen angezeigt, auf dem Desktop Sie darauf hinweist, dass Secure Boot nicht ordnungsgemäß konfiguriert ist. Rufen Sie diese [aktualisieren, um das Secure Boot desktop Wasserzeichen entfernen](http://go.microsoft.com/fwlink/p/?linkid=329932).

**Um Secure Boot wieder zu aktivieren:**

1.  Deinstallieren Sie alle Grafikkarten, Hardware oder Betriebssystemen, die nicht mit Secure Boot kompatibel sind.

2.  Öffnen Sie das BIOS-PC-Menü. Sie können dieses Menü häufig zugreifen, eine Taste zu drücken, während die Sequenz Hochfahren wie F1, F2, F12 oder ESC-Taste.

    Oder von Windows: Wechseln Sie zu **Einstellungen Charm &gt; Einstellungen ändern PC &gt; Update und Recovery &gt; Wiederherstellung &gt; erweiterte Startoptionen: jetzt neu starten**. Wenn Sie der PC neu gestartet wird, gehen Sie zum **Troubleshoot &gt; erweiterte Optionen: UEFI Firmware Einstellungen**.

3.  Hier finden Sie die **Secure Boot** -Einstellung, und legen sie Sie, wenn möglich **aktiviert**. Diese Option ist normalerweise in der Registerkarte **Sicherheit** , Registerkarte " **Start** " oder auf der Registerkarte **Authentifizierung** .

    Wählen Sie auf einige PCs **Benutzerdefiniert**, und Laden Sie die Secure Boot-Schlüssel, die in den PC integriert sind.

    Wenn der PC das Secure Boot aktivieren nicht zulässt, versuchen Sie das BIOS auf die herstellereinstellung zurückgesetzt.

4.  Änderungen speichern und beenden. Der PC neu gestartet wird.

5.  Ist der PC nicht nach dem Aktivieren der Secure Boot gestartet, wechseln Sie wieder in den Menüs BIOS deaktivieren Secure Boot, und versuchen Sie, den PC erneut zu starten.

6.  In einigen Fällen müssen Sie aktualisieren oder Ihren PC in den ursprünglichen Zustand zurückzusetzen, bevor Sie Secure Boot aktivieren können. Weitere Informationen finden Sie unter [Wiederherstellen, aktualisieren oder Zurücksetzen von Ihrem PC](http://go.microsoft.com/fwlink/p/?linkid=279534).

7.  Wenn die oben beschriebenen Schritte funktionieren nicht, und Sie weiterhin das Secure Boot-Feature verwenden möchten, fordern Sie vom Hersteller Ihrer Hilfe.

    Zusätzliche Schritte zur Problembehandlung für PC-Hersteller: finden Sie unter [Secure Boot ist nicht ordnungsgemäß konfiguriert: ermitteln, ob der PC-Option in einem Fertigung-Modus (Info für Hersteller) ist](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Secure Boot – Übersicht](secure-boot-overview.md)

[Sichere Boot ist nicht ordnungsgemäß konfiguriert: Problembehandlung](secure-boot-isnt-configured-correctly-troubleshooting.md)

 

 






