---
title: Abrufen von Retail ETW-Protokolle
description: Abrufen von Retail ETW-Protokolle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a32d9f2b-1a4a-4d69-aae0-c5e80472a708
ms.openlocfilehash: 6afe072297e0ef5e9d3ec7888c722666b980abd4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="retrieve-retail-etw-logs"></a>Abrufen von Retail ETW-Protokolle


Sie können eine Vielzahl von Probleme verfolgen die Protokolle Retail diagnostizieren. Finden Sie weitere Informationen zum Verarbeiten und Anzeigen der Verkaufsversion Protokolle [erfassen Trace Ereignisprotokolle auf Windows 10 Mobile](capture-event-trace-logs-on-windows-phone.md) .

## <a name="retrieving-logs-from-a-retail-device"></a>Abrufen von Protokollen von einem Gerät Einzelhandel


Das Gerät in Massen-Speichermodus abzurufenden Protokolle von einem Gerät engineering oder Retail entsperrt gestartet werden müssen. Host-PC kann das Gerät als einem Speichergerät erkennen, wenn Sie in Massen-Speichermodus starten. Die Prozedur dazu hängt von Silicon Hersteller Einstellungen ab.

Dies ist wie vorhandene ETW-Protokolle von einem Gerät Retail abrufen:

1.  Entsperren des Geräts an.

2.  Drücken Sie eine bestimmte Tastenfolge auf dem Gerät im Modus Massenspeichergerät starten aus. Dies erfolgt normalerweise nur die Kamera Schaltfläche oder der Kamera und der Menge gedrückt, wenn Sie beim Einschalten gedrückt.

3.  Der Bildschirm wird etwa 5 Sekunden leer bleiben, und danach sehen Sie neue Speichergeräten in Windows Explorer. Suchen Sie nach dem Laufwerk, auf dem der Ordner EFIESP befindet.

4.  Kopieren Sie Sie in Windows Explorer die Dateien aus diesen beiden Verzeichnissen.

    ``` syntax
    <mass storage drive letter>:\Data\SystemData\Telemetry
    <mass storage drive letter>:\Data\SystemData\ETW
    ```

    In Abhängigkeit vom Umfang der Aktivität auf dem Telefon ETL-Protokolle, System speichert in Cab-Dateien und andere Protokolle werden in diesem Verzeichnis.

5.  Nachdem Sie die Protokolle vom Gerät kopiert haben, schließen Sie Windows Explorer, und klicken Sie dann ausschließen Sie das Gerät.

## <a name="related-topics"></a>Verwandte Themen


[Softwareablaufverfolgungfinden](index.md)

 

 







