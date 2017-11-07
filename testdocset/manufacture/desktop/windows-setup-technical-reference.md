---
author: Justinha
Description: Technische Referenz zu Windows Setup
ms.assetid: f0fa0e04-e8ca-43b8-a789-0ef854e09333
MSHAttr: PreferredLib:/library/windows/hardware
title: Technische Referenz zu Windows Setup
ms.openlocfilehash: 3174512fbf67482f3f647be4ea95be79213e0154
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-technical-reference"></a>Technische Referenz zu Windows Setup


Windows Setup ist ein startbaren Programm, das Windows-Betriebssystem installiert.

## <a name="span-idbkmkappspanspan-idbkmkappspanpractical-applications"></a><span id="BKMK_APP"></span><span id="bkmk_app"></span>In der Praxis


-   Sie können installieren oder aktualisieren Sie das Betriebssystem Microsoft Windows auf einem PC aus einen USB-Schlüssel, der eine eingebundene. ISO-Datei, DVD oder Netzwerkgerät.
-   Sie können den Installationsvorgang Windows, einschließlich Konfiguration der Treiber, Pakete, Dateien und Windows-Systemeinstellungen mithilfe von [Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445)erstellte Antwortdateien automatisieren.
-   Sie können Windows Setup als Installationsprogramm für Ihre eigenen benutzerdefinierten Windows-Abbilder verwenden.
-   Die Menüs können im Windows-Setup Sie die Festplatten vor der Installation vorbereiten.

## <a name="span-idwhatsnewspanspan-idwhatsnewspanspan-idwhatsnewspanwhats-new"></a><span id="What_s_New"></span><span id="what_s_new"></span><span id="WHAT_S_NEW"></span>Neuigkeiten


-   Windows 8.1 Upgrades unterscheiden sich von der vorherigen Windows-Upgradeszenarien. Weitere Informationen finden Sie unter [Windows 8.1 aktualisieren Szenarien für OEMs](windows-81-upgrade-scenarios-for-oems.md).

-   Windows Setup kann nicht zur Durchführung von automatisierten Upgrades für die meisten Editionen von Windows 8.1 verwendet werden.

    Volumenlizenz Editionen von Windows verwenden, haben wir eine neue Befehlszeilenoption hinzugefügt `setup /auto`, um Upgrades zu aktivieren. Beachten Sie, wir diese Option für Upgrades auf Windows 8.1 verwenden möchten, und wir können entfernen Sie die Option in zukünftigen Versionen von Windows. Weitere Informationen finden Sie unter [Windows Setup Command-Line Options](windows-setup-command-line-options.md).

-   [Einstellungen für OOBE automatisieren](settings-for-automating-oobe.md): die Einstellung [NetworkLocation](https://msdn.microsoft.com/library/windows/hardware/dn923171) ist nicht mehr erforderlich, um OOBE zu automatisieren. Die Funktionalität der [ProtectYourPC](https://msdn.microsoft.com/library/windows/hardware/dn915741) Einstellung geändert wurde.

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>Siehe auch


Die folgende Tabelle enthält Links zu Ressourcen, die im Zusammenhang mit diesem Szenario.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Inhaltstyp</th>
<th align="left">Verweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Planung</strong></p></td>
<td align="left"><p>[Windows Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md) | [Windows Setup Automatisierung (Übersicht)](windows-setup-automation-overview.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Bereitstellung</strong></p></td>
<td align="left"><p>[Windows Setup-Installationsvorgang](windows-setup-installation-process.md) | [Windows 8.1 aktualisieren Szenarien für OEMs](windows-81-upgrade-scenarios-for-oems.md) | [Boot von einer DVD](boot-from-a-dvd.md) | [Windows aus einem USB Flash-Laufwerk installieren](install-windows-from-a-usb-flash-drive.md) | [Deploy ein benutzerdefiniertes Bild](deploy-a-custom-image.md) | [Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[Windows Setup automatisieren](automate-windows-setup.md) | [Verwendung eine Konfiguration mit Windows Setup festgelegt](use-a-configuration-set-with-windows-setup.md)| [Hinzufügen von Gerätetreibern während Windows Setup Windows](add-device-drivers-to-windows-during-windows-setup.md) | [Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md) | [mehrsprachige Windows-Abbild Erstellung](multilingual-windows-image-creation.md) | [Boot Windows-Modus oder OOBE überwachen](boot-windows-to-audit-mode-or-oobe.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Tools und Einstellungen</strong></p></td>
<td align="left"><p>[Windows Setup-Befehlszeilenoptionen](windows-setup-command-line-options.md) | [Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md) | [Windows Setup Staaten](windows-setup-states.md) | [Setup Windows-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md) | [Windows Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md) | [Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Verwandte Technologien</strong></p></td>
<td align="left"><p>[Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445) | [Referenz für das unbeaufsichtigte Windows Setup](http://go.microsoft.com/fwlink/?LinkId=206281) | [Sysprep (System Preparation) Übersicht](sysprep--system-preparation--overview.md) | [Windows PE für Windows 10](winpe-intro.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






