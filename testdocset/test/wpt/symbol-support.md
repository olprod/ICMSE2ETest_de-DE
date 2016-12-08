---
title: "Symbol-Unterstützung"
description: "Symbol-Unterstützung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3f4fcf1c-9d81-4842-82e5-a443f47f5255
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e56183594911e2b74a65bc6ff9663615a42e8bbb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="symbol-support"></a>Symbol-Unterstützung


Wenn Windows Performance Analyzer (WPA) ordnungsgemäß konfiguriert ist, zeigt WPA symbolische Namen aus der Symboldateien für Adressen, die in der Aufzeichnung gefunden werden.

Zum Decodieren von Symbolen, müssen die Tools die Datenbank Programmdateien bekannt als Programmdatenbankdateien (PDB) oder Symboldateien für gesamten Anruf Stapel suchen. Compiler und Linker PDB-Dateien generiert, wenn das System eine Komponente erstellt. Microsoft bietet das Programm Datenbankdateien für viele Microsoft-Produkte auf einem Symbolserver online. Verwenden Sie den online Symbolserver zum Nachschlagen von Informationen, die Microsoft Debugging Tools for Windows und WPA. Aus diesem Grund muss der Computer mit dem Internet verbunden werden, wenn die Symboldateien nicht lokal kopiert werden. Windows Performance Toolkit wird dasselbe Symbol Infrastruktur als den Windows-Debugger **Windbg.exe**Decodierung verwendet. Weitere Informationen finden Sie unter [WinDbg](http://go.microsoft.com/fwlink/p/?linkid=212249).

Zum Konfigurieren der Symbol Unterstützung, definieren Sie die ** \_NT\_SYMBOL\_PFAD** -Umgebungsvariablen. Im folgenden Beispiel wird den Symbolpfad Microsoft öffentlichen Symbolserver zusammen mit einem downstream Speicher in C: verwenden\\Symbole:

``` syntax
set _NT_SYMBOL_PATH= srv*C:\symbols*http://msdl.microsoft.com/downloads/symbols
```

Beachten Sie, dass in diesem Beispiel wird eine einzelne Befehlszeile ist.

Die URL in diesem Symbolpfad gibt online Microsoft Symbolserver an. Der Pfad zwischen den Sternchen (C:\\Symbole) gibt den Informationsspeicher downstream. Dies ist ein lokaler Cache, in dem das Symbol Lösung System Symboldateien hält. WPA Tools decodieren auch Symbole aus Komponenten, die Sie entwickeln. Fügen Sie einen oder mehrere Pfade zu ** \_NT\_SYMBOL\_PFAD** enthalten die PDB-Dateien für die Komponenten, die Sie aufzeichnen möchten. Im folgende Beispiel wird beispielsweise wie der Pfad für das vorherige Beispiel eingerichtet wurde:

``` syntax
set _NT_SYMBOL_PATH=c:\coding\fs\release;srv*C:\symbols*
```

Bei der Xperf oder WPA decodiert Symbole Xperf oder WPA speichert eine verkürzte Version des ursprünglichen Symboldateien oder PDB-Dateien, auf dem Datenträger in der ** \\Symcache** Verzeichnis. Zu diesem Zweck verwendet Xperf oder WPA die Symbole, die zum Zeitpunkt zur Verfügung stehen. Das Betriebssystem-Symbole, die außerhalb von Microsoft verfügbaren sind öffentliche Symbole. Diese Symbole enthalten weniger Daten als interne private Symbole. Schwarz-Feld zu testen, können Öffentliche Symbole auch falsche Informationen enthalten. Private zuverlässiger Symbole können unter nicht-Weitergabe Agreements abgerufen werden. Wenn ein Benutzer hat eine Aufzeichnung mithilfe von öffentlichen Symbole, decodiert und der Benutzer erhält dann private Symbole, muss der Benutzer Deaktivieren der ** \\Symcache** Directory bevor Xperf oder WPA die neue private Symbole erkennen kann.

## <a name="troubleshooting-symbol-decoding"></a>Problembehandlung bei Symbol Decodierung


Symbol Decodierung Unterstützung ist komplexer. Die folgenden Anforderungen müssen erfüllt sein:

-   Geben Sie `-symbols` auf die Xperf Befehlszeile oder **Symbole laden** im **Trace** in WPA auf Wählen Sie nach dem Öffnen einer aufzeichnungs.

-   Die Umgebungsvariablen müssen ordnungsgemäß konfiguriert sein. Weitere Informationen für Xperf finden Sie unter [Symbole](symbols.md).

-   Die ETW Kernel Aufzeichnungsdatei muss wurde beendet und korrekt zusammengeführt. Weitere Informationen finden Sie unter [einer Aufzeichnung beenden](stop-a-recording.md).

-   Windows Performance-Aufzeichnung (WPR) oder WPA führt die Benutzer Aufzeichnungsdatei ETW zusammen mit einer Datei der Kernel-Aufzeichnung, die gleichzeitig auf demselben Computer ausgeführt wird zusammen.

-   Sie benötigen Zugriff auf die Binärdatei und Symbol Quellen, die ** \_NT\_SYMBOL\_PFAD** gibt. Wenn Sie einen Symbolserver verwenden, ist der Symbolserver häufig nur einen Redirector an. In diesem Fall benötigen Sie Zugriff auf das Symbolserver und die Websites, denen auf der Symbolserver verweist, die die Binärdateien und Symbole hosten.

-   ** \_NT\_SYMBOL\_PFAD** muss an den richtigen Dateien zeigen. Wenn die Dateien aus einer anderen Build oder Architektur vorhanden sind, werden die Dateien nicht funktionsfähig. Ist die Version der Binärdateien der Anwendung nicht die gleiche Version wie die Symbole, die ** \_NT\_SYMBOL\_PFAD** Punkte, Sie können keine Stapel anzeigen.

    Verwenden Sie zum Symbol aus diesem auszuschließen, **Symchk.exe** von der **Debugtools für Windows** -Verteilung um sicherzustellen, dass die Symbole die Symboldateien auf dem Computer übereinstimmen, auf dem die Aufzeichnung durchgeführt wurde. Beispiel:

    ``` syntax
    symchk /v <local_file> /s <sympath_to_name.pdb>
    ```

    Um eine binäre Nichtübereinstimmung auszuschließen, verwenden Sie die `fc /b` Befehl aus, um sicherzustellen, dass die Binärdateien auf dem Computer, auf dem die Aufzeichnung stammt, die Binärdateien auf dem Drop übereinstimmen. Beispiel:

    ``` syntax
    fc /b <local_file> <drop_share_file>
    ```

-   In Xperf, müssen Sie mithilfe der Aufzeichnung ETW Kernel erfassen mindestens die `PROC_THREAD+LOADER` Kennzeichen. Diese Flags enthalten grundlegende Informationen zum Prozesslebensdauer und Bild virtuellen Adressbereiche im Prozessarbeitsspeicher. Diese Informationen helfen XPerf zum Decodieren von virtueller Adressen an, die Bilder und Symbole.

    Überprüfen Sie um zu überprüfen, dass diese Flags im Kernelmodus ETW-Aufzeichnung aktiviert wurden, Xperf **-Prozess** (**Erstellen**, **Löschen**, **Starten Sie kurzer**, **End kurzer**) und **Bild** -Ereignisse (**Load**, **Unload**, **Kurzer Start**, **End kurzer**) sind in der Tabelle, die generiert wird, mithilfe des folgenden Befehls vorhanden:

    ``` syntax
    xperf -i kernel.etl -a tracestats -detail
    ```

    **Hinweis**  
    Alle diese Ereignisse möglicherweise nicht aufgeführt werden, in der Tabelle, je nachdem, ob diese Ereignisse aufgetreten sind.

     

### <a name="limitation-in-xperf-symbol-decoding"></a>Einschränkung der Decodierung Xperf-Symbol

Xperf wird standardmäßig auf dem System Laufwerk, wenn ein Laufwerk für ein ausführbares Abbild nicht angegeben wird (z. B. ** \\Pfad\\Library.dll**). Beim Ausführen der `-d/-merge` Befehl, wenn Xperf finden kann ein ausführbares Bild, das vorhanden war in einem Prozess ausgeführt wird während der Aufzeichnung, Xperf kann nicht das entsprechende Bild und Symboldateiinformationen Identity abgerufen und die Informationen der zusammengeführten Aufzeichnung hinzufügen. Ohne diese Informationen kann nicht Xperf Symbol für das Bild in die Aufzeichnung Decodierung ausführen.

Dieses Problem wirkt sich nicht auf andere Dateipfade, wie die Pfade in Datenträger-e/a oder Datei-e/a aus.

So aktivieren Sie das Symbol Decodierung und helfen, aktivieren die richtige Bild laden und entladen Pfade in Xperf ETW Aufzeichnungen, sollten Sie alle ausführbare Bilder speichern, für die Sie möglicherweise erfordern Symbol Decodierung oder Bild laden und entladen Pfade auf dem Systemlaufwerk. Führen Sie dann die Bilder von diesem Laufwerk. Wenn dies nicht möglich ist, erstellen Sie eine Spiegelung der Bilder auf dem Systemlaufwerk, auch wenn Sie die Bilder von einem anderen Laufwerk ausführen. Beispielsweise wenn C: das Systemlaufwerk ist, erstellen Sie eine identische Kopie des **D:\\Spiel\\Bin\\binkw32.dll** am **C:\\Spiel\\Bin\\binkw32.dll**.

## <a name="related-topics"></a>Verwandte Themen


[Windows Performance Toolkit](index.md)

[Symbole](symbols.md)

[Verwenden der CLR 4.0 NGEN PDB-Unterstützung](using-clr-40-ngen-pdb-support.md)

[Häufige Probleme von eingehenderen Analysen](../assessments/common-in-depth-analysis-issues.md)

 

 







