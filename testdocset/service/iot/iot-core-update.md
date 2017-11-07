---
author: kpacquer
Description: "Windows 10 IoT Core (IoT Core) Geräte erhalten automatisch OS Updates über Windows Update wenn mit dem Internet verbunden."
ms.assetid: d8298c99-6fa7-4825-a0b8-181b99e40975
MSHAttr: PreferredLib:/library/windows/hardware
title: IoT Core Update
ms.openlocfilehash: 0d4b5ead233fc6a1aae4dc0f76e8da5043905366
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-update"></a>IoT Core Update


Windows 10 IoT Core (IoT Core)-Geräte erhalten automatisch OS Updates über Windows Update, wenn mit dem Internet verbunden.

-   **OS Updates.** OS Updates beinhaltet Sicherheits-Updates für alle Microsoft-Pakete (Releasetype = Produktion) in der ESP (EFI-Systempartition) und Main OS Partition vorhanden. Diese Updates werden automatisch ausgeführt. OEM und Unternehmenskunden können mithilfe von Windows 10 IoT Kern Pro SKU OS Updates verwalten. Finden Sie weitere Informationen finden Sie unter [Verwalten von Updates](managing-iot-device-update.md).

-   **Windows Store-app-updates.** Ihre aktualisierten, signierten Pakets an den Windows Store zu übermitteln. Wenn Ihre Geräte mit dem Internet verbunden sind, werden sie in regelmäßigen Abständen Suchen nach Updates aus dem Windows Store und Updates automatisch installieren. 

<!---   **OEM updates.** These are also referred to as Board Support Package (BSP) updates. OEMs develop specific BSP updates for their devices such as the Raspberry Pi 2 and the Minnowboard Max. These are then published to the Microsoft Update server where specified IoT Core devices can download and receive the OEM updates automatically. -->
