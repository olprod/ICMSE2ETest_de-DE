---
title: Xperf Profile verwenden
description: Xperf Profile verwenden
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 31673dde-fe06-4b54-afe2-f9bd9c5e60d2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d28b041175192220be1d3d5e782b87aca0e23288
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-xperf-profiles"></a>Xperf Profile verwenden


In diesem Abschnitt veranschaulicht die Spuren mithilfe von Profilen erfassen. Wenn Sie Speicher analysieren, sollten Sie Ihre Trace in eine Datei schreiben ETW über schreibt und den Cache nicht gestört. Wenn Sie Datenträger-e/a analysieren, sollten Sie Ihre Trace in einem zirkulären Puffer im Arbeitsspeicher gespeichert. Es gibt auch andere Aspekte z. B., ob Sie müssen zum Erfassen einer Ablaufverfolgungs für langen, der nicht in einen Puffer im Arbeitsspeicher passen würde, oder wenn Sie nur den letzten 5 bis 10 Sekunden des Inhalts Trace interessieren.

## <a name="procedure"></a>Vorgehensweise


1.  Wählen Sie ein Profil wie **Perf! FileIOProfiles.InBuffer** und mit Befehl ähnlich dem folgenden Beispiel Informationen anzuzeigen.

    ``` syntax
    xperf -profiles perf!FileIOProfiles.InBuffer
    ```

    Mit diesem Befehl werden alle Profile, gefolgt vom Sitzungen und Anbieter in diesem Profil aufgelistet:

    Profil: FileIOProfiles.InBuffer

    Sitzungen: FileIOProfiles.InBuffer.Sessions

    Sitzung: FileIOProfiles.InBuffer.Sessions\[0\]. Kernel\[0\]

    Sitzung: FileIOProfiles.InBuffer.Sessions\[0\]. Benutzer\[0\]

    Anbieter: FileIOProfiles.InBuffer.Providers

    Anbieter: FileIOProfiles.InBuffer.Providers\[0\]. Kernel\[0\]

    Anbieter: FileIOProfiles.InBuffer.Providers\[0\]. Benutzer\[0\]

2.  Angenommen, Sie eine dateibasierten Verfolgung verwenden haben, starten Sie ein **InSequentialFile** Trace-Profil mithilfe des folgenden Befehls.

    ``` syntax
    xperf -start perf!GeneralProfiles.InSequentialFile
    ```

    Wenn ein Problem auftritt, wird ein Fehler gemeldet. Beispielsweise würde das gleiche Profil zweimal starten ein Laufzeitfehler, der die Sitzung bereits ausgeführt wird.

3.  Anzeigen der **InSequentialFile** Protokollierungsmodule für ein bestimmtes Profil bereits gestartet haben, mithilfe des folgenden Befehls.

    ``` syntax
    xperf -profileloggers perf!GeneralProfiles.InSequentialFile
    ```

    Die Antwort auf diesen Befehl ist ähnlich wie im folgenden Beispiel.

    Sitzungsstatus für "Korrektur! GeneralProfiles.InSequentialFile":

    "NT-Kernel-Protokollierung": ausgeführt

    PerfCoreUserSession\_InSequentialFile: ausgeführt

4.  Beenden Sie das **InSequentialFile** Trace-Profil, die Spuren speichern und anschließende Zusammenführen zu einer Ablaufverfolgungsdatei, beispielsweise "merged.ETL" enthält, mithilfe des folgenden Befehls.

    ``` syntax
    xperf -stop perf!GeneralProfiles.InSequentialFile merged.etl
    ```

    Wenn ein Problem auftritt, wird ein Fehler gemeldet.

5.  Starten Sie das Profil **InSequentialFile** Trace, überschreiben, Start nacheinander, *MaxPuffer* Werte für alle ETW-Sitzungen, die für die Protokollierungsmodule 256 gestartet werden sollen. Verwenden Sie den folgenden Befehl, um diese Aktion auszuführen.

    ``` syntax
    xperf -start perf!GeneralProfiles.InSequentialFile -MaxBuffers 256
    ```

    Wenn ein Problem auftritt, wird ein Fehler gemeldet.

6.  Aktualisieren Sie *MaxPuffer* Werte für die aktive **InSequentialFile** ETW Protokollierungsmodule mithilfe des folgenden Befehls in das Ablaufverfolgungsprotokoll Profil angegeben.

    ``` syntax
    xperf -update perf!GeneralProfiles.InSequentialFile -MaxBuffers 256
    ```

    Keine Antwort wird nach dem Ausführen dieses Befehls angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Profile](xperf-profiles.md)

 

 







