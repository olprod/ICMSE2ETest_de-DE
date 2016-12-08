---
author: kpacquer
Description: "Updates und Zurücksetzen des Geräts"
ms.assetid: ad197224-ed30-4483-816e-a48ec385197d
MSHAttr: PreferredLib:/library/windows/hardware
title: "Updates und Zurücksetzen des Geräts"
ms.openlocfilehash: a8b3a3d6c96d24454d0bdb6e99aafc2c70b1d1b4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updates-and-resetting-the-device"></a>Updates und Zurücksetzen des Geräts


OEMs müssen berücksichtigen wie Updates betroffen sind, wenn der Benutzer das Gerät zurückgesetzt. Informationen zu den Grundlagen von wie das Betriebssystem das Gerät zurückzusetzen ändert, überprüfen Sie sorgfältig [das Gerät zurückzusetzen](../../manufacture/mobile/resetting-a-phone-during-manufacturing.md).

## <a name="span-idosandbspupdatesspanspan-idosandbspupdatesspanspan-idosandbspupdatesspanos-and-bsp-updates"></a><span id="OS_and_BSP_updates"></span><span id="os_and_bsp_updates"></span><span id="OS_AND_BSP_UPDATES"></span>Betriebssystem und BSP updates


Updates für Microsoft OS und OEM Board Support-Paket (BSP) – und dazugehörige registrierungsänderungen – beibehalten werden, nachdem das Gerät zurückgesetzt wird. Für den Benutzer bedeutet dies, dass Updates müssen nicht heruntergeladen werden, wenn das Gerät zurückgesetzt wird. Für OEM bedeutet dies, dass neuere Versionen des Updates für Betriebssystem und BSP müssen entwickelt werden, um Kompatibilität mit älteren apps zu ermöglichen, deren Updates zurückgesetzt, wenn das Gerät zurückgesetzt wird.

## <a name="span-idpreloadedappsspanspan-idpreloadedappsspanspan-idpreloadedappsspanpreloaded-apps"></a><span id="Preloaded_apps"></span><span id="preloaded_apps"></span><span id="PRELOADED_APPS"></span>Vorinstallierte apps


Wenn das Gerät zurückgesetzt wird, installieren Sie vorinstallierte apps aus der aktuellen Version von dem XAP, die auf dem Telefon gespeichert ist. Die aktuelle Version handelt sich um den ursprünglichen XAP-, die auf dem Gerät geliefert oder der aktuellsten Version, die empfangen wurde in OEM over-the (OTA) aktualisieren. Der Benutzer müssen möglicherweise trotzdem Herunterladen von Updates für die apps höhere Versionen, an den Store veröffentlicht wurden, jedoch nicht im Rahmen eines Updates OTA geliefert wurden.

Es sind weitere wichtige Aspekte zum Aktualisieren von vorinstallierte System Einstellung apps. Weitere Informationen finden Sie unter [System Einstellungen apps und Updates](system-settings-apps-and-updates.md).

## <a name="span-idplaceholderappsspanspan-idplaceholderappsspanspan-idplaceholderappsspanplaceholder-apps"></a><span id="Placeholder_apps"></span><span id="placeholder_apps"></span><span id="PLACEHOLDER_APPS"></span>Platzhalter-apps


Platzhalter-apps sind neu aus dem aktuellen app-Paket auf dem Gerät installiert. Die aktuelle Version ist das ursprüngliche Paket, das auf dem Gerät geliefert oder die neueste Version, die im Rahmen eines Updates OTA empfangen wurde.

## <a name="span-iduserappsanddataspanspan-iduserappsanddataspanspan-iduserappsanddataspanuser-apps-and-data"></a><span id="User_apps_and_data"></span><span id="user_apps_and_data"></span><span id="USER_APPS_AND_DATA"></span>Benutzer-apps und Daten


Alle Benutzer installiert Store-apps und zugehörigen Daten werden entfernt, wenn das Gerät zurückgesetzt wird. Der Benutzer kann mithilfe die Sicherung und Feature, das diese apps wiederherstellen wiederherstellen. Weitere Informationen finden Sie unter [Sichern von Meine Auswahl](http://go.microsoft.com/fwlink/p/?LinkId=331631).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Update](index.md)

 

 






