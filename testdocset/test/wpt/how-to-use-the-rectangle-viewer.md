---
title: Verwendung der Rechteck-Viewers
description: Verwendung der Rechteck-Viewers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: BAB2EC57-2B5E-428F-AEEE-ECF8C7C62E2A
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 04267611e5d065ce4002c19dcbdd969aa8001f23
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="how-to-use-the-rectangle-viewer"></a>Verwendung der Rechteck-Viewers


In Windows Performance Analyzer (WPA), verwenden Sie den Viewer Rechteck sehen, was auf dem Bildschirm, während die Ablaufverfolgung für einen bestimmten Punkt in der Zeit passiert ist.

Rechteck-Viewer bietet auch die folgenden Vorteile:

-   Sehen Sie sich einen Punkt in Zeit (oder in einem Frame) im Gegensatz zu Plotter Werte über einen Zeitraum
-   Herauszufiltern Sie bestimmte Zeilen ein, sodass sie wird nicht im Diagramm angezeigt werden. Wenn Sie nur ungefilterte Frames ("dirty Frames") anzeigen möchten, können Sie also nach unten zu, die filtern und finden Sie unter genau das.
-   Anzeigen der Markierung, während es durchläuft die Diagramme ("Dickichte über Uhrzeit")

**Hinweis**  Standardmäßig ist diese Funktion in die DWM Frame Details und den HTML-Frame Detailbereich Diagrammen als ein Paar von Vorgaben. Die Punkte in Anzeige auf der Zeitachse Zeit (in diesem Fall Rahmen).

 

**Des Rechtecks Viewers**

1.  Klicken Sie auf **&gt;** in der unteren linken Ecke des Diagramms (in der Nähe der Ursprung 0,0, des Diagramms) in Zeit nach vorn verschoben oder halten, um Zeit zu verschieben.

    ![Screenshot des Rechtecks Viewer.](images/rectangle-viewer.png)

2.  Vergrößern oder verkleinern, indem Sie mit der linken Maustaste und Aufbewahren von links nach rechts, bis Sie den Rahmen erfassen möchten anzuzeigen, und klicken Sie dann klicken Sie auf den ausgewählten Rechteckbereich (blau hervorgehoben), und klicken Sie auf **Vergrößern**.

    Wenn Sie einen Bereich mit dem Rechteck Viewer auswählen, können Sie den Mauszeiger, um eine QuickInfo anzuzeigen, die Informationen, abhängig von der Tabelle angibt. Im Diagramm DWM Frame Detailbereich würde die QuickInfo beispielsweise die Dauer und die Anfangs- und Endzeiten (in Sekunden) die Ablaufverfolgung für den ausgewählten Bereich anzuzeigen.

## <a name="gold-bar-indicator-of-the-rectangle-viewer"></a>Anzeige des Rechtecks Viewers Gold


Im folgenden Beispiel sehen Sie die Dimensionen Rechteck rechts neben der gold Leiste (plus der Frame starten/beenden in der Konfiguration Diagramm definiert).

Wenn Sie bestimmte Zeilen herauszufiltern, wird Sie von WPA kein Diagramm. Wenn Sie nur ungefilterte Rahmen ("dirty Rahmen") anzeigen möchten, können Sie also auf das ungefilterte Frames filtern. Dieses Feature funktioniert mit anderen Diagramme in der Registerkarte, sodass Sie sehen Ihre Auswahl in der gesamten den Diagrammen weitergegeben, aber auch die Zeitauswahl verschieben, wie Sie durch die Zeit zu bereinigen.

![Screenshot des Rechtecks Viewer mit Indikator gold Balken hervorgehoben.](images/rectangle-viewer-gold-indicator.png)

## <a name="related-topics"></a>Verwandte Themen


[Klicken Sie auf ein Zeitintervall vergrößern](zoom-in-on-a-time-interval.md)

 

 







