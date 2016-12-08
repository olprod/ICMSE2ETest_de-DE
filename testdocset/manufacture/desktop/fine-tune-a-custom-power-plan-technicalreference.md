---
author: Justinha
Description: Optimieren eines benutzerdefinierten Power Plans
ms.assetid: 3f3b0d9d-d84a-4b87-a271-159d80ebbcc7
MSHAttr: PreferredLib:/library/windows/hardware
title: Optimieren eines benutzerdefinierten Power-Plans
ms.openlocfilehash: 1baf2ed1045fb08c9dba3063640a858808fbc966
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="fine-tune-a-custom-power-plan"></a>Optimieren eines benutzerdefinierten Power Plans


Ein Plan Power ist eine Auflistung von Hardware- und Systemeinstellungen, die verwaltet werden, wie die Computer verwenden und Strom sparen. Können Sie die benutzerdefinierten Power Pläne erstellen für bestimmte Computer optimiert sind.

Sie können die am häufigsten verwendete Power Planen von Einstellungen über die Systemsteuerung verwalten. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Power planen](create-a-custom-power-plan-technicalreference.md). Verwenden Sie das PowerCfg Tool, um verfeinern Hardware-spezifische Konfigurationen, die nicht über die Systemsteuerung konfigurierbar sind.

## <a name="span-idmodifypowerplanspanspan-idmodifypowerplanspanspan-idmodifypowerplanspanmanually-modifying-a-power-plan"></a><span id="ModifyPowerPlan"></span><span id="modifypowerplan"></span><span id="MODIFYPOWERPLAN"></span>Manuelles Ändern eines Power-Plans


Sie können mithilfe von alle konfigurierbaren Windows Energieoptionen Anpassen der `powercfg` Befehl von einer Eingabeaufforderung mit erhöhten Rechten. Dazu gehören Hardware-spezifische Konfigurationen, die nicht über die Systemsteuerung konfigurierbar sind.

**So Listen Sie die verfügbaren Power-Pläne**

-   Auf dem Referenzcomputer an einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    powercfg -LIST
    ```

    Der Computer wird die Liste der verfügbaren Power Pläne zurück. In den folgenden Beispielen werden diese Pläne *abgestimmt* und *Energiesparmodus*.

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    ```

    Beachten Sie die GUIDs vor, die neben den Power-Plänen aufgeführt, die Sie ändern möchten. Sie benötigen diese GUIDs manuell aktualisieren Einstellungen und erfassen die Power-Pläne.

**Power Plan to geändert werden als aktiv festlegen**

-   Um einen Plan zu ändern, verwenden Sie die GUID des Plans Power, die Sie zum Festlegen von Power Plans wie der aktiven Power Plan ändern möchten. Beispiel:

    ``` syntax
    powercfg -SETACTIVE {guidPlan2}
    ```

**So passen Sie die Einstellungen an**

1.  In diesem Abschnitt wird beschrieben, wie andere Power-Konfigurationseinstellungen mithilfe von manuell konfigurieren der `powercfg` Befehl. Testen Sie diese Einstellungen, um eine optimale Leistung Plan für Ihr System zu erstellen.

    **Hier finden Sie Informationen über die vorhandene Power-Einstellung.**

    1.  Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

        ``` syntax
        powercfg -QUERY
        ```

        Der Computer Zeigt Informationen für alle für die Power für diesen Plan.

    2.  Hier finden Sie die GUID für die Untergruppe der Einstellung, die Sie ändern möchten. Beispielsweise um eine Einstellung für die Anzeige zu ändern, suchen Sie die GUID für die Anzeige Untergruppe:

        ``` syntax
        Subgroup GUID: {guidSubgroup-Display}  (Display)
        ```

    3.  Hier finden Sie die GUID für die Einstellung, die Sie ändern möchten. Beispielsweise, um die Helligkeit der Anzeige-Einstellung zu ändern, suchen Sie die GUID für die Einstellung (Helligkeit der Anzeige):

        ``` syntax
        Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
        ```

    4.  Lesen der Informationen aus den Abfragebefehl, überprüfen die möglichen Einstellungen und Bestimmen eines Werts, der für Ihren Computer.

        **Hinweis**  
        Sie müssen diese Werte mithilfe von Dezimalzahlen eingeben. Jedoch als hexadezimale Werte, die speziell für die Einstellung werden die Werte auf dem Bildschirm angezeigt.

        Geben Sie den Wert als 50 beispielsweise die maximale Helligkeit auf 50 Prozent Helligkeit festlegen. Bei Verwendung der `powercfg -QUERY` Befehl aus, um die Einstellung Bestätigen der Wert wird als 0x00000032 angezeigt.

        ``` syntax
        Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
          Minimum Possible Setting: 0x00000000
          Maximum Possible Setting: 0x00000064
          Possible Settings increment: 0x00000001
          Possible Settings units: %
         Current AC Power Setting Index: 0x00000064
         Current DC Power Setting Index: 0x00000032
        ```

2.  Passen Sie den Wert für die Power-Einstellung für Zeiten, wenn der Computer angeschlossen ist. Um die Helligkeit Anzeigeebene auf 100 % festgelegt, wenn der Computer angeschlossen ist, geben Sie beispielsweise Folgendes ein:

    ``` syntax
    powercfg -SETACVALUEINDEX {guidPlan-New} {guidSubgroup-Display}  {guidPowerSetting-Brightness} 100
    ```

3.  Passen Sie den Wert für die Power-Einstellung für Zeiten, wenn der Computer auf Batterie ist. Um die Helligkeit Anzeigeebene auf 75 Prozent festlegen, wenn der Computer auf Batterie ist, geben Sie beispielsweise Folgendes ein:

    ``` syntax
    powercfg -SETDCVALUEINDEX {guidPlan-New} {guidSubgroup-Display}  {guidPowerSetting-Brightness} 75
    ```

4.  Verwenden Sie den **Abfrage** -Befehl, um die Einstellung sicherzustellen. Beispiel:

    ``` syntax
    powercfg -QUERY
    ```

    Der Computer Zeigt den neuen Power Einstellung Index in hexadezimaler Schreibweise. Beispiel:

    ``` syntax
    Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
          Minimum Possible Setting: 0x00000000
          Maximum Possible Setting: 0x00000064
          Possible Settings increment: 0x00000001
          Possible Settings units: %
        Current AC Power Setting Index: 0x00000064
        Current DC Power Setting Index: 0x0000004b
    ```

    Der Hexadezimalwert 0x00000064 repräsentiert 100 Prozent die Helligkeit, wenn der Computer angeschlossen ist. Der Hexadezimalwert 0x0000004b stellt 75 Prozent Helligkeit der Anzeige, bei der Computer Batterie verwendet wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Erstellen eines benutzerdefinierten Power-Plans](create-a-custom-power-plan-technicalreference.md)

[Festlegen des Standard-Power-Plans](set-the-default-power-plan-technicalreference.md)

 

 






