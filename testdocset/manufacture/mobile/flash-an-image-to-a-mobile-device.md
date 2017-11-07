---
Description: "Blinken ist der Vorgang des Abrufens eines mobilen Bilds in ein mobiles Gerät."
ms.assetid: 40d64242-b299-4cc5-ac6d-6b154c90d8b2
MSHAttr: PreferredLib:/library
title: "Flash eines Bilds zu einem mobilen Gerät"
author: CelesteDG
ms.openlocfilehash: 2687fcdfd13aaa991df497db7f0ba98870fe79f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flash-an-image-to-a-mobile-device"></a>Flash eines Bilds zu einem mobilen Gerät


Blinken ist der Vorgang des Abrufens eines mobilen Bilds in ein mobiles Gerät. Jeder Hersteller hat verschiedenen Techniken und Tools, die sie für die Herstellung und service ein Windows mobiles-Gerät verwenden, und dies bedeutet, dass jeder OEM, welche blinken bestimmen muss und Fertigungsprozess am besten für sie funktioniert. Weitere Informationen finden Sie unter [Tools blinken](../mobile/flashing-tools.md).

In dieser exemplarischen Vorgehensweise verwenden wir ffutool.exe, die als Teil der ADK Windows installiert ist, das Bild eines mobilen Geräts blinken. Weitere Informationen zu blinken und erläutert, was Sie benötigen, um Ihr Gerät für blinken vorzubereiten finden Sie unter [verwenden die blinkende Tools von Microsoft bereitgestellt](https://msdn.microsoft.com/library/windows/hardware/dn789235).

**Ein Bild blinkt**

1.  Starten Sie das Gerät in FFU Modus blinkt, während er auf den Hostcomputer verbunden ist.

    Wenn Sie die optionale Funktion LABIMAGE beim Generieren des Test-Abbilds einschließen, können Sie das Gerät in FFU Modus manuell durch Drücken und Loslassen der Power blinkendes starten Sie das Gerät und klicken Sie dann sofort gedrückt halten der Lautstärke Schaltfläche erzwingen. Beachten Sie jedoch, dass diese Option ist nur verfügbar, wenn ein FFU zunächst an das Gerät aktualisiert wurde wurde.

2.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten.

3.  Führen Sie an der Befehlszeile das Bild blinkt ffutool.exe.

    **Ffutool-flash TestFlash.ffu**

Es dauert ein paar Minuten, damit das Bild vollständig auf das Gerät aktualisiert werden. Nach Abschluss der blinken Geräteinstallation durchlaufen, und stellen Sie sicher, dass die Anpassungen als Teil des Bilds angezeigt werden.

 

 



