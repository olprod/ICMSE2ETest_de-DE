---
Description: "Müssen Sie eine mobile Bild signieren, bevor Sie es zu einem Gerät bereitstellen können."
ms.assetid: b5f9d31b-7293-4308-a761-c5cc87801e3c
MSHAttr: PreferredLib:/library
title: Melden Sie einen mobilen Bild
author: CelesteDG
ms.openlocfilehash: 3d21999b9074ea9f241e351b523b3ed637cd5c33
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sign-a-mobile-image"></a>Melden Sie einen mobilen Bild


Sie müssen ein Bild mobile anmelden, bevor Sie es zu einem Gerät, bereitstellen können. Weitere Informationen zum Signieren von Bildern finden Sie unter [Signieren einer vollständigen flash (FFU) Updateabbild](https://msdn.microsoft.com/library/windows/hardware/dn789216).

Bevor Sie beginnen, stellen Sie sicher, dass Sie die Schritten im gefolgt *Schritt 5: Test-Zertifikate installieren OEM* [Vorbereiten für Windows mobile](preparing-for-windows-mobile-development.md)-Entwicklung. Wenn Sie noch nicht geschehen, führen Sie diese zuerst vor dem Fortsetzen des mit den Schritten zum Signieren eines Bilds.

In dieser exemplarischen Vorgehensweise konzentrieren wir uns auf Test das Bild manuell zu signieren. Zusätzlich zu ImageSigner verwenden wir auch Sign.cmd.

**So testen Sie Signieren eines Bilds**

1.  Öffnen Sie eine Aufforderung für Entwickler mit Administratorrechten in das Verzeichnis, das die Ausgabe aus der Generierungsprozess Bild enthält.

2.  Extrahieren Sie den Katalog nicht signierte FFU-Datei mithilfe des folgenden Befehls:

    **ImageSigner GETCATALOG TestFlash.ffu TestFlash.cat**

3.  Melden Sie sich den Katalog mit der Option /pk. Es gibt zwei Teilen zu diesem Schritt aus:

    **ANMELDEN festlegen\_OEM = 1**

    **Sign.cmd /pk TestFlash.cat**

4.  Signieren der FFU mit der signierte Katalogdatei ImageSigner verwenden.

    **ImageSigner ANMELDUNG TestFlash.ffu TestFlash.cat**

Nachdem das Bild angemeldet ist, können Sie das Bild auf Ihrem mobilen Gerät flash.

 

 



