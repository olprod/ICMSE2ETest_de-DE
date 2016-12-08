---
title: "Übung 2 - Protokoll manuell ETW speichern für Medien Szenarien für den Einsatz von WPR"
description: "Automatisierte Tests werden gut überprüfen die Audio- oder zeitliche Videoqualität eines Geräts für ein bestimmtes automatisierte Szenario; jedoch, wenn eine Audio- oder Videodatei Störung während eines manuellen Tests auftritt, klicken Sie dann das Tool Windows Performance Aufzeichnung (WPR) verwendbar um manuell eine Trace Event Tracing for Windows (ETW) während einer Reproduzieren des Problems zu erfassen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 89203B18-8C1F-40ED-9DF5-B68F2995BFD9
ms.openlocfilehash: e706f5b2a8de0ebd36c6f0f55549fda35d5bd022
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-2---manually-collect-etw-logs-for-media-scenarios-using-wpr"></a>Übung 2 - Protokoll manuell ETW speichern für Medien Szenarien für den Einsatz von WPR


Automatisierte Tests sind hervorragende Audio- oder zeitliche Videoqualität eines Geräts für ein bestimmtes automatisierte Szenario zu überprüfen. jedoch erfolgt eine Audio- oder Videodatei Störung während eines manuellen Tests, kann dann das Tool **Windows Performance Aufzeichnung (WPR)** verwendet werden um manuell eine Trace Event Tracing for Windows (ETW) während einer Reproduzieren des Problems zu erfassen.

## <a name="step-1-collect-an-etw-trace-using-wpr"></a>Schritt 1: Zusammenstellen eines ETW Trace mit WPR


1.  Mit der rechten Maustaste auf **das Startmenü** , und klicken Sie auf **der Befehlszeile (Admin)**.

2.  Navigieren Sie zu dem Ordner, in dem Sie **WPR** installiert haben.

3.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    wpr -cancel
    ```

4.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    wpr -start Media.wprp -filemode
    ```

5.  Führen Sie eine Arbeitslast wie Videowiedergabe oder einem Real-Time Communications-Szenario.

6.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    wpr -stop Media.etl
    ```

## <a name="step-2-visualize-the-etw-trace-in-mxa"></a>Schritt 2: Visualisieren Sie ETW Trace in MXA


1.  Installieren der **Medienfunktionen Analyzer (MXA)** die heruntergeladen werden kann [hier](https://go.microsoft.com/fwlink/?linkid=525711).

2.  Mit der rechten Maustaste auf **das Startmenü** , und klicken Sie auf **der Befehlszeile (Admin)**.

3.  Navigieren Sie zu dem Ordner, in dem Sie **MXA**installiert.

4.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    xa -i <Media.etl location>\Media.etl
    ```

    Beispiel: bei Media.etl im Verzeichnis C: gespeichert wurden\\Leistung\\Medien, geben Sie den folgenden Befehl ein:

    ``` syntax
    xa -i C:\Performance\Media\Media.etl
    ```

5.  Drücken Sie die Schaltfläche **Symbole deaktivieren** , um die Symbol-Lookup zu deaktivieren.

6.  Erkunden Sie die verschiedenen Medien weiterführende Datasets und Anbieter in der Verfolgung aktiviert.

 

 






