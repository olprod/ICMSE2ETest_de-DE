---
title: "Verwenden der CLR 4.0 NGEN PDB-Unterstützung"
description: "Verwenden der CLR 4.0 NGEN PDB-Unterstützung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0297661e-99bf-44fa-9d1c-f624d6a96f41
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1b7e27954acca6dd36bafbc19210de8cda263720
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-clr-40-ngen-pdb-support"></a>Verwenden der CLR 4.0 NGEN PDB-Unterstützung


Mit aktivierter Common Language Runtime (CLR) 4.0 Native Image Generator (NGEN) PDB-Unterstützung können Xperf und Windows Performance-Aufzeichnung (WPR) ausführen.

**Hinweis**  WPR verarbeitet CLR Symbole direkt, sodass keine Flags beim Konfigurieren und Verwenden von NGEN Support erforderlich sind.

 

Wenn Sie eine Aufzeichnung der WPR-Benutzeroberfläche (UI) starten, werden neben gespeicherte Aufzeichnung NGEN Programmdatenbankdateien (PDB-Dateien) generiert. Diese PDB-Dateien decodieren Symbole von Modulen, die mithilfe von NGEN für verwaltete Szenarien erstellt wurden. Für **Recording.etl**, die NGEN PDB-Dateien im Ordner " **Recording.etl.NGENPDB** " sind.

## <a name="using-ngen-support-with-wpr"></a>Verwendung von NGEN Unterstützung mit WPR


Wir empfehlen das folgenden Setup vor der Ausführung von WPR mit aktivierter NGEN-Unterstützung:

-   (Optional, wird jedoch empfohlen) Legen Sie in einem lokalen Verzeichnis SymCache Path-Umgebungsvariablen

## <a name="using-ngen-support-with-xperf"></a>Verwenden von NGEN Unterstützung mit Xperf


Führen Sie folgende Schritte aus, um mit Xperf NGEN Support zu verwenden:

1.  Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
    ```

2.  Geben Sie Folgendes ein, um die Kernel-Sitzung zu starten:

    ``` syntax
    xperf -on Base -stackwalk Profile -f kernel.etl
    ```

3.  Geben Sie Folgendes ein, um die CLR-Laufzeit Sitzung Aufzeichnung starten:

    ``` syntax
    xperf -start ClrSession -on ClrAll:0x98:5 -f clr.etl -buffersize 128 -minbuffers 256 -maxbuffers 512
    ```

4.  Führen Sie das Szenario.

5.  Geben Sie Folgendes ein, um die CLR Rundownsitzung begonnen:

    ``` syntax
    xperf -start ClrRundownSession -on ClrAll:0x118:5+a669021c-c450-4609-a035-5af59af4df18:0x118:5 -f clr_DCend.etl -buffersize 128 -minbuffers 256 -maxbuffers 512
    ```

6.  Geben Sie Folgendes ein, um die Zeit für die CLR kurzer abschließen, indem Sie den Timeoutwert auf 15 festlegen:

    ``` syntax
    timeout /t 15
    ```

7.  Geben Sie die CLR-Laufzeit-Sitzung, CLR Rundownsitzung und Kernel-Sitzung zu beenden, und um sie zu einer einzigen Datei zusammenzuführen Folgendes:

    ``` syntax
    xperf -stop ClrSession ClrRundownSession -stop -d recording.etl
    ```

## <a name="decoding-a-recording-that-has-clr-40-ngen-pdb-support-enabled"></a>Aktiviert Decodieren einer aufzeichnungs, die CLR 4.0 NGEN PDB unterstützen hat


Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

``` syntax
set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
```

## <a name="transferring-a-recording-that-has-clr-40-ngen-pdb-support-enabled"></a>Übertragen einer aufzeichnungs, die CLR 4.0 NGEN PDB unterstützen ist aktiviert


Um eine Aufzeichnung mit aktivierter CLR 4.0 NGEN PDB-Unterstützung zu übertragen, in den Symbolpfad sind:

``` syntax
srv*C:\Symbols.NGEN
```

Um die Aufzeichnung auf einen anderen Computer zu übertragen, stellen Sie sicher, die **Recording.etl** und den gesamten Ordner **C:\\Symbols.NGEN** (zusammen mit seinen Unterordnern) übertragen werden.

## <a name="related-topics"></a>Verwandte Themen


[Symbol-Unterstützung](symbol-support.md)

[Symbole](symbols.md)

 

 







