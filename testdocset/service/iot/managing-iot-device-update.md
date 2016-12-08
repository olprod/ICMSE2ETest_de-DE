---
author: kpacquer
Description: "OEM und Unternehmenskunden, die mithilfe von Windows 10 IoT Kern Pro (IoT Kern Pro) können Gerätemanagement Konfiguration-Dienstanbieter (CSP) nutzen die einige Steuerung Geräteupdates ermöglichen."
ms.assetid: c25c6a6a-9965-40d6-b1da-725e45d2f00a
MSHAttr: PreferredLib:/library/windows/hardware
title: "Verwalten von Geräteupdates IoT Core"
ms.openlocfilehash: 7f5ce201788ea7d8c69f042914a7cdcf2dd3a524
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manage-iot-core-device-updates"></a>Verwalten von Geräteupdates IoT Core


OEM und Unternehmenskunden, die mithilfe von Windows 10 IoT Kern Pro (IoT Kern Pro) können Gerätemanagement Konfiguration-Dienstanbieter (CSP) nutzen die einige Steuerung Geräteupdates ermöglichen.

**Hinweis**  Verwaltung von Windows 10 IoT Core (IoT Core) betrifft nur Windows 10 IoT Kern Pro. Weitere Informationen zu Lizenzierung Windows 10 IoT Kern Pro finden Sie unter [Microsoft kommerziellen Begriffe der Verwendung für Windows 10 IoT Core](http://go.microsoft.com/fwlink/?LinkID=614849).

 

Richtlinie zur Verwaltung Gerät kann mithilfe des Tools Windows Imaging und Konfiguration Designer (ICD) oder ein mobiles Gerät-Verwaltungsdienst (MDM) festgelegt werden. Ausführlichere Informationen zu Gerät Management Protokolle finden Sie unter [Verwaltung mobiler Geräte](https://msdn.microsoft.com/windows/hardware/dn914769.aspx ) .

## <a name="span-idallowautoupdatetoturnupdatesonoroffspanspan-idallowautoupdatetoturnupdatesonoroffspanspan-idallowautoupdatetoturnupdatesonoroffspanallowautoupdate-to-turn-updates-on-or-off"></a><span id="AllowAutoUpdate_to_turn_updates_on_or_off"></span><span id="allowautoupdate_to_turn_updates_on_or_off"></span><span id="ALLOWAUTOUPDATE_TO_TURN_UPDATES_ON_OR_OFF"></span>AllowAutoUpdate zu aktivieren oder deaktivieren Sie die updates


Updates für IoT Kern Pro können durch Festlegen der AllowAutoUpdate Richtlinie deaktiviert werden.

-   Wenn die Richtlinie AllowAutoUpdate nicht konfiguriert ist, erhalten Geräte IoT Core Updates wie gewohnt am 03: 00 Uhr.
-   Wenn die Richtlinie AllowAutoUpdate auf **5**festgelegt wird, sind automatische Updates für IoT Core deaktiviert.

![allowautoupdate5](images/policy1.png)

## <a name="span-idallowautoupdatetocontrolupdatesspanspan-idallowautoupdatetocontrolupdatesspanspan-idallowautoupdatetocontrolupdatesspanallowautoupdate-to-control-updates"></a><span id="AllowAutoUpdate_to_control_updates"></span><span id="allowautoupdate_to_control_updates"></span><span id="ALLOWAUTOUPDATE_TO_CONTROL_UPDATES"></span>AllowAutoUpdate zur Steuerung des updates


Die Richtlinie AllowAutoUpdate kann auch den Zeitpunkt des Updates für IoT Core steuern:

Wenn die Richtlinie AllowAutoUpdate auf **4**festgelegt ist, IoT Core-Updates werden automatisch installiert und das Gerät wird neu gestartet, zu einem bestimmten Zeitpunkt. IT-Administratoren gibt die Installation Tag/Zeit (d. h., jeden Sonntag um 03: 00 Uhr). Wenn kein Tag/Uhrzeit angegeben wird, standardmäßig den Zeitpunkt der Installation täglich 03: 00 Uhr. Aktualisiert alle Endbenutzer-bezogenen sowie Benachrichtigungen unterdrückt werden.
Anzeigen die festgelegte Zeit in ` <LocURI>./Vendor/MSFT/PolicyManager/Device/Update/ScheduledInstallDay</LocURI>` oder ` <LocURI>./Vendor/MSFT/PolicyManager/Device/Update/ScheduledInstallTime</LocURI>` in **Syncml**.

![allowautoupdate4](images/policy2.png)

## <a name="span-iddeferringupdatesspanspan-iddeferringupdatesspanspan-iddeferringupdatesspandeferring-updates"></a><span id="Deferring_updates"></span><span id="deferring_updates"></span><span id="DEFERRING_UPDATES"></span>Zurückstellen updates


Die Richtlinie AllowAutoUpdate kann auch den Zeitpunkt des Updates für IoT Core steuern:

Nicht kritischen Updates für IoT Core können maximal 120 Tage verschoben werden, mithilfe von Windows Server Update Services (WSUS). Bei diesem Verfahren werden die Geräte so konfiguriert, dass um den WSUS-Server für Updatedienst nicht mit Windows Update zu verwenden. Der IT-Administrator ruft IoT Core Updates vom Microsoft Update-Katalog und downloads der Updates später bereitstellen.
**Hinweis**  Wenn ein WSUS-Server auf einem Gerät IoT Core konfiguriert ist, wird der Server für die Updates ping Trigger unterdrückt.

 

So konfigurieren Sie WSUS auf ein Bild IoT Core

1.  Wählen Sie auf der **Startseite von Windows ICD**des IoT Core-Projekts, das Sie ändern möchten.
2.  Erweitern Sie unter **Anpassungen verfügbar**bis **Runtime Einstellungen**, **Richtlinien**und dann **Aktualisieren**.
3.  Ändern Sie im im Infobereich **Richtlinien/aktualisieren** der **UpdateServiceURL** auf die Adresse des WSUS-Servers, der verwendet werden soll.

![updateserviceurl](images/updateurl.png)

Um IoT Core Updates in der WSUS-Katalogwebsite auszuwählen:

1.  Wählen Sie in der WSUS-Verwaltungskonsole **Updates aus**, und klicken Sie im Bereich Aktionen auf **Import-Updates**.
2.  Auf der Website für Microsoft Update Katalog wird ein Browserfenster geöffnet.
3.  Sie können diese Website IoT Core Updates vom Gerät, OEM und Firmware suchen. Wenn Sie diejenigen, die Sie benötigen gefunden, fügen sie Ihrem Warenkorb hinzu.
4.  Wechseln Sie zur Warenkorb, und klicken Sie auf **Importieren** , um die Updates auf den Server zu importieren. Um die Updates herunterladen direkt und ohne sie importieren möchten, deaktivieren Sie das Kontrollkästchen **Import direkt in Windows Server Update Services** und speichern Sie die heruntergeladene Datei zu.

## <a name="span-idosupdatesonlyspanspan-idosupdatesonlyspanspan-idosupdatesonlyspanos-updates-only"></a><span id="OS_updates_only"></span><span id="os_updates_only"></span><span id="OS_UPDATES_ONLY"></span>Nur OS updates

Ein Gerät IoT Core kann festgelegt werden, OS Updates von Microsoft und nicht OEM Updates zu erhalten:

**Für Windows 10, Version 1607**: Verwenden von IoT\_GENERISCHEN\_POP im OemInput XML. (Sie können die Intel.Generic.DeviceInfo.cab nicht mehr verwenden, diese Datei wurde entfernt.)

**Für Windows 10, Version 1511**: um ein Gerät empfangen nur OS Updates zu konfigurieren, müssen Sie die OEM Feature Manifest-XML für das Gerät bearbeiten. Der Feature-Manifestdatei unterstützten Geräte finden Sie unter den folgenden Verzeichnisspeicherort auf dem Gerät:

-   **MinnowBoard Max:**` C:\Program Files (x86)\Windows Kits\10\FMFiles\x86\MBMFM.xml`
-   **Himbeeren Pi 2:**` C:\Program Files (x86)\Windows Kits\10\FMFiles\arm\RPi2FM.xml`
-   **Qualcomm DragonBoard:**` C:\Program Files (x86)\Windows Kits\10\FMFiles\arm\QCDB410CFM.xml`

In der ** &lt;DeviceLayoutPackages&gt; ** und ** &lt;Features&gt;**Abschnitte, entfernen Sie die Geräte-ID und Ersetzen durch **generische**. Beispielsweise wird **Intel.MBM.DeviceInfo.cab** **Intel.Generic.DeviceInfo.cab**.

![generische Pop auf mbm](images/genericpop.png)

 

 





