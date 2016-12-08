---
author: Justinha
Description: 'Windows PE: Debuggen von Apps'
ms.assetid: 30fe59bc-f169-4534-b5a5-dbe58a10cb83
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Debuggen von Apps'
ms.openlocfilehash: ef34d5de6f3a443b5f058fb0ed4703be98f79d93
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-debug-apps"></a>Windows PE: Debuggen von Apps


Sie können Windows-Debugger wie Ntsd.exe, Cdb.exe, und Windbg.exe und unterstützende Tools Anwendungen auf Windows PE Debuggen und den Kernel Windows PE Debuggen verwenden. Debugtools werden im [Windows-10-SDK]( http://go.microsoft.com/fwlink/?LinkId=526807)enthalten. Sie müssen die debugging Tools verfügbar auf dem Computer Windows PE machen, indem entweder lokal kopieren oder von einer Freigabe verwendet werden.

Um die Remote Windows PE Debuggen, müssen Sie möglicherweise die integrierte Firewall auf dem PC zu deaktivieren:

``` syntax
wpeutil disablefirewall
```

## <a name="span-iduser-modedebuggingspanspan-iduser-modedebuggingspanspan-iduser-modedebuggingspanuser-mode-debugging"></a><span id="User-mode_debugging"></span><span id="user-mode_debugging"></span><span id="USER-MODE_DEBUGGING"></span>Debuggen im Benutzermodus


Die einfachste debugging im Benutzermodus-Methode ist einen Prozessserver auf dem Computer Windows PE ausführen und Verbinden mit es über ein Debugger auf einem anderen Computer. Prozess-Server gehört zum Lieferumfang der Debugtools im [Windows-10-SDK]( http://go.microsoft.com/fwlink/?LinkId=526807).

**Zum Ausführen eines Process-Servers im Benutzermodus**

1.  Kopieren Sie das Tool Windows Debuggen Prozessserver: **dbgsrv.exe**aus dem Ordner debugging Tools [10-SDK für Windows]( http://go.microsoft.com/fwlink/?LinkId=526807) (Beispiel: C:\\Program Files (x86)\\Windows Kits\\10.0\\Debugger\\X64), auf dem Windows PE-Computer.

2.  Deaktivieren Sie an der Eingabeaufforderung Windows PE die Firewall.

    ``` syntax
    wpeutil disablefirewall
    ```

3.  Starten Sie den Windows-Debuggen Prozessserver, eine Verbindungsmethode mit dem PC, beispielsweise ein TCP-Port angeben:

    ``` syntax
    dbgsrv.exe -t tcp:port=1234
    ```

    Weitere Informationen finden Sie unter [Aktivieren eines Prozess-Servers (Windows-Debugger)]( http://go.microsoft.com/fwlink/p/?LinkId=698645).

4.  Verwenden Sie den Prozess-Server aus dem remote-Computer Anfügen an oder starten Prozesse auf dem Zielcomputer Windows PE:

    ``` syntax
    windbg -premote tcp:server=Server, port=1234
    ```

    Weitere Informationen finden Sie unter [ein Intelligenter Client (Windows-Debugger) aktivieren](http://go.microsoft.com/fwlink/p/?LinkId=698646).

Es ist auch möglich, den Debugger direkt auf dem Computer Windows PE ausführen. Jedoch hierfür muss einrichten Symbol und Quelle Pfade nach jedem Neustart des Windows PE-Computer. Es wird empfohlen, Sie führen Sie das Debuggen von einem Computer mit einer vollständigen Version von Windows, wie in diesem Verfahren beschrieben.

Das folgende Verfahren debugging ist nützlich, wenn startnet.cmd oder setup.exe zu umgehen und direkt in einem Eingabeaufforderungsfenster zu Debuggingzwecken fortgesetzt werden soll. Dieses Verfahren umgeht alle Initialisierung, einschließlich Setup aus, und führt keine Befehle, wie beispielsweise Wpeinit.exe. Dieses Verfahren muss auf einem Betriebssystem online online ausgeführt werden.

**So aktivieren Sie im Benutzermodus Debuggen vor der Initialisierung**

1.  Löschen Sie die Datei unter dem winpeshl.ini, sofern vorhanden. Wenn die winpeshl.ini Datei nicht vorhanden ist, kann dann Benutzermodus Debuggen standardmäßig zugegriffen werden.

2.  Halten Sie die STRG-Taste während des Startvorgangs gedrückt, bevor der Eingabeaufforderung angezeigt wird. An der Eingabeaufforderung angezeigt wird.

3.  Fahren Sie fort mit Debuggen.

## <a name="span-idkernel-modedebuggingspanspan-idkernel-modedebuggingspanspan-idkernel-modedebuggingspankernel-mode-debugging"></a><span id="Kernel-mode_debugging"></span><span id="kernel-mode_debugging"></span><span id="KERNEL-MODE_DEBUGGING"></span>Debuggen im Kernelmodus


Um im Kernelmodus zu debuggen, müssen Sie aktivieren, Debuggen im Kernelmodus, bevor das System gestartet wird. Die Boot-Konfigurationsdatei hat eine Einstellung für das Debuggen Kernel im, die mithilfe des Befehlszeilentools bcdedit.exe so ändern Sie den Speicher (Boot Configuration Data, BCD) aktiviert ist. Kernel-debugging kann nur mithilfe von bcdedit.exe ausgeführt werden. Bcdedit.exe befindet sich der \\Windows\\Verzeichnis System32 des Windows-Partition.

Die Standardeinstellungen Debugger sind wie folgt:

``` syntax
----------------- 
identifier              {dbgsettings} 
debugtype               Serial 
debugport               1 
baudrate                115200
```

Aktivieren Sie den Kernel mit BCD-Einträge für das Erstellen von ISOs für VM-Umgebungen, vor dem Erstellen der ISO.

Speichern Sie Informationen dazu, wie Sie die Standard-BCD ändern (default.bcd), finden Sie unter [wie BCD Speichern mittels Bcdedit geändert](http://go.microsoft.com/fwlink/p/?LinkId=698647).

**So aktivieren Sie das Debuggen im Kernelmodus**

1.  Suchen Sie nach der BCD-Speicher, die in eine Datei namens **bcd**enthalten ist. Diese Datei befindet sich innerhalb des Verzeichnisses Boot im Stamm des Mediums, das Windows PE-Abbild enthält.

2.  Geben Sie an der Befehlszeile den folgenden Befehl Bcdedit auf das Debugflag von Startkonfigurationsdaten verwendet, um das Abbild auf gestartet festgelegt `debug on`:

    ``` syntax
    bcdedit /store <path to winpe>/boot/bcd /set {default} debug on
    ```

    Die `{default}` müssen möglicherweise durch den eindeutigen Bezeichner (UID) ersetzt werden, der die Option für Windows PE zum Starten.

    Alternativ können Sie auch aktivieren Kerneldebuggen durch Drücken von F8 während des Startvorgangs und Auswählen der Option Debuggen.

    **Hinweis**  
    Um ein Symbolserver aus Windows PE verwenden möchten, verwenden Sie die `net use` Befehl auf dem Server Symbole und Dateifreigaben.

     

Weitere Informationen zu Befehlszeilenoptionen, die Debuggen steuern, finden Sie unter [BCDEdit Command-Line Options](http://go.microsoft.com/fwlink/p/?LinkId=526808).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Wpeutil Befehlszeilenoptionen](wpeutil-command-line-options.md)

[Winpeshl.ini Referenz: Starten einer app beim Start von Windows PE](winpeshlini-reference-launching-an-app-when-winpe-starts.md)

[BCDEdit Befehlszeilenoptionen](http://go.microsoft.com/fwlink/p/?LinkId=526808)

 

 






