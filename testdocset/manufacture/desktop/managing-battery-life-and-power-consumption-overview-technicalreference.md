---
author: Justinha
Description: "Verwalten von Akkulaufzeit und Power-Auslastung (Übersicht)"
ms.assetid: 9e5f962a-7647-431f-b10e-98c7589ec388
MSHAttr: PreferredLib:/library/windows/hardware
title: "Verwalten von Akkulaufzeit und Power-Auslastung (Übersicht)"
ms.openlocfilehash: 37da9176af68f0ba958343959b7c9c090e05d631
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="managing-battery-life-and-power-consumption-overview"></a>Verwalten von Akkulaufzeit und Power-Auslastung (Übersicht)


Windows® basierenden Laptops müssen Energie Effizienz gesetzlichen Anforderungen, beispielsweise das Programm Vereinigte Staaten Umweltschutzbehörde (EPA) Energie Stern erfüllen. Darüber hinaus haben Umfragen gezeigt, dass eine führende Anforderung von Verbrauchern werden weiterhin Akkulaufzeit für Laptops.

Hardware und Software Faktoren wie eine kostengünstige Batterie, einen prozessorintensive Treiber oder eine schlecht konfigurierte Power-Einstellung können eine erhebliche Verringerung in Akkulaufzeit führen. Wenn Sie Ihr System entwerfen, experimentieren Sie sollte mit verschiedenen Konfigurationen dieser Faktoren, das beste Gleichgewicht zwischen Akkulaufzeit und Leistung zu erhalten.

## <a name="span-idhardwarespanspan-idhardwarespanspan-idhardwarespanhardware"></a><span id="Hardware"></span><span id="hardware"></span><span id="HARDWARE"></span>Hardware


In diesem Abschnitt listet einige der die allgemeine Hardware Entwurfsaspekte, die Akkulaufzeit beeinflussen.

-   **Batteriekapazität.** Wenden Sie sich vom Hersteller Ihrer Batterie Batteriekapazität bestimmen.

-   **Andere Hardwarekomponenten.** Bitten Sie Ihre Hersteller für Energieverbrauchs Testergebnisse für jede Hardwarekomponente.

Auf jedem dieser Faktoren Akkulaufzeit Informationen finden Sie [Mobile Batterie Lebensdauer Solutions: A Guide für Mobile Plattform Experten](http://go.microsoft.com/fwlink/?LinkId=209929).

## <a name="span-idsoftwarespanspan-idsoftwarespanspan-idsoftwarespansoftware"></a><span id="Software"></span><span id="software"></span><span id="SOFTWARE"></span>Software


In diesem Abschnitt listet einige der die allgemeine Software Entwurfsaspekte die Akkulaufzeit auswirken können.

-   **Treiber.** Beachten Sie beim Hinzufügen von jedem neuen Treiber für das System den Treiber Beeinträchtigung des Stromverbrauchs. Ein einzelnes Treiber mit geringer Leistung kann die Systemleistung erheblich beeinträchtigen.

-   **Anwendungen, Dienste und andere Software.** Beachten Sie beim Hinzufügen von jede neue softwareanwendung auf das System die Anwendung Beeinträchtigung des Stromverbrauchs. Eine einzelne Anwendung mit geringer Leistung kann die Systemleistung erheblich beeinträchtigen.

-   **Windows Power-Richtlinieneinstellungen.** Windows Power-Richtlinieneinstellungen des Lastenausgleichs für leistungsanforderungen und Akkulaufzeit zu optimieren. Weitere Informationen finden Sie im Abschnitt: [Windows Power-Richtlinieneinstellungen](#configurablesettingsimpactingbatterylife).

Weitere Informationen zu den einzelnen dieser Batterie Lebensdauer Faktoren, finden Sie unter [Mobile Batterie Lebensdauer Solutions: A Guide für Mobile Plattform Experten](http://go.microsoft.com/fwlink/?LinkId=209929).

## <a name="span-idconfigurablesettingsimpactingbatterylifespanspan-idconfigurablesettingsimpactingbatterylifespanspan-idconfigurablesettingsimpactingbatterylifespanwindows-power-policy-settings"></a><span id="ConfigurableSettingsImpactingBatteryLife"></span><span id="configurablesettingsimpactingbatterylife"></span><span id="CONFIGURABLESETTINGSIMPACTINGBATTERYLIFE"></span>Windows Power-Richtlinieneinstellungen


In diesem Abschnitt listet einige häufige konfigurierbare Einstellung, die Akkulaufzeit auswirken können. Testen Sie diesen und anderen Einstellungen, erstellen Sie einen optimale Leistung Plan für Ihr System.

Einstellungen können auf Batterie power (DC) oder speziell für gibt an, ob der Computer in (AC) angeschlossen ist werden. Sie können die folgenden Einstellungen konfigurieren:

-   **Helligkeit der Anzeige**

    Die effizienteste des Energieverbrauchs auf einem mobilen Computer zu reduzieren, wenn die Anzeige verwendet wird ist um die Helligkeit der Anzeige zu verringern. Die angefügte Anzeige ist der größte Verbraucher Power. Die Anzeige wird bis zu 40 % des Stromverbrauchs der gesamten verwendet.

    Standardmäßig wird Windows erheblich die Helligkeit der Anzeige reduziert, wenn ein mobiler Computer Batterie ist. Abhängig von Ihrer Hardware und den Anforderungen Ihrer Benutzer können Sie die Helligkeit der Anzeige Standard festlegen unteren Akkulaufzeit, steigern anpassen oder höher, um die Anzeige Lesbarkeit.

-   **Display-timeout**

    Mobile PC Akkulaufzeit kann mithilfe einer kurzen Anzeige Leerlauftimeout erheblich erweitert werden.

    **Hinweis**  
    **Anzeigen von Abblenden**: dim tragbaren Computern, auf denen Windows 8.1 und Windows Server 2012 R2 ausgeführt die Anzeige auf 15 Sekunden vor dem **Timeout angezeigt**. Dieser Wert wird nicht mehr konfigurierbar.

     

-   **Timeout Festplatte**

    Obwohl der Festplatte nicht primäre Power Consumer in der normalen mobile Computer ist, können Sie Strom sparen, indem Sie sich eine Erhöhung des Timeouts Festplatte sein.

    Wenn die Festplatte für einen Zeitraum im Leerlauf befindet, wird die Festplatte Motor beendet. Das nächste Mal an, dem der Computer der Zugriff auf die Festplatte muss reagiert das System möglicherweise langsam, während die Festplatte erneut Rotieren beginnt.

    Abhängig von Ihrer Hardware und den Anforderungen Ihrer Benutzer können Sie das Festplatte Standardtimeout Akkulaufzeit erhöhen niedriger oder höher, um die Verfügbarkeit der Festplatte zu erhöhen anpassen.

-   **Energiesparmodus**

    Standardmäßig, wenn der Prozessor sich im Leerlauf befindet und der Endbenutzer ist nicht den Computer mit Windows in den Energiesparmodus wechselt oder Ruhezustand. Das nächste Mal an, dass der Computer den Prozessor wieder benötigt Systemantwort möglicherweise langsam während der Prozessor reaktiviert.

    Abhängig von Ihrer Hardware und den Anforderungen Ihrer Benutzer können Sie die Standard-Ruhezustand unten, um die Akkulaufzeit zu erhöhen, oder höher, um die Verfügbarkeit des Prozessors erhöhen anpassen.

-   **Drahtlose Adapter Stromversorgung speichern Modi**

    In der Standardeinstellung wird Windows die 802.11 Energiesparmodus **Maximale** Leistung für AC und Batterie Power konfiguriert. Bei dieser Konfiguration bleibt den drahtlosen Adapter aktiv ist, auch wenn keine Daten übertragen werden. Dies vermindert Kompatibilitätsprobleme zwischen einigen drahtlosen Adapter und Zugriffspunkte, die nicht mit 802.11-Energiesparmodi kompatibel sind.

    Bei der Erstellung benutzerdefinierter Power-Richtlinien, um mehr Leistung zu speichern und Hilfe Akkulaufzeit erweitern, wenden Sie sich an den Hersteller des drahtlosen Adapters über die Effekte der Ändern des Power-Richtlinienwert für **maximale Power** oder **Mittel Power speichern**.

Sie können die Power-Einstellungen für jede Konfiguration integrierten Power manuell ändern. Weitere Informationen zu dieser Einstellungen sowie andere allgemeine konfigurierbar Power-Einstellungen finden Sie unter [Mobile Batterie Lebensdauer Solutions: A Guide für Mobile Plattform Experten](http://go.microsoft.com/fwlink/?LinkId=209929) und [Power Richtlinienkonfiguration und Bereitstellung in Windows](http://go.microsoft.com/fwlink/p/?linkid=129584).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Batterie Lebensdauer Lösungen: Leitfaden für Mobile Plattform Experten](http://go.microsoft.com/fwlink/?LinkId=209929)

[Festlegen des Standard-Power-Plans](set-the-default-power-plan-technicalreference.md)

[Erstellen eines benutzerdefinierten Power-Plans](create-a-custom-power-plan-technicalreference.md)

[Windows Performance Toolkit](http://go.microsoft.com/fwlink/p/?linkid=210214)

[Power-Richtlinienkonfiguration und Bereitstellung in Windows](http://go.microsoft.com/fwlink/p/?linkid=129584)

 

 






