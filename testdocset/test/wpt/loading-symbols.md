---
title: Laden von Symbolen
description: Laden von Symbolen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: db27f063-0ae8-4762-8df4-66e3d14e55ed
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: aba08b62d0207c1c26054849b1e68cf3f9186c3b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loading-symbols"></a>Laden von Symbolen


Sie können die folgenden Voreinstellungen des Benutzers in Windows Performance Analyzer (WPA) festlegen:

-   **Symbole laden**

-   **Konfigurieren Sie Symbolpfade**

Um diese Optionen ändern, öffnen Sie eine Aufzeichnung, und wählen Sie dann die Option im **Ablaufverfolgungsprotokoll** .

Inhalt dieses Artikels:

-   [Verwaltete Symbole](#mansym)

-   [Relative Pfade und eingebettete Umgebungsvariablen](#relative)

-   [SymCache Pfad](#symcachepath)

-   [Symbolpfad](#symbolpath)

## <a name="a-href-idmansymamanaged-symbols"></a><a href="" id="mansym"></a>Verwaltete Symbole


Symbol Auflösung und Stapel für verwaltete Prozesse werden auf den folgenden Systemen unterstützt:

-   Mit .NET Framework 4.5 oder eine spätere Version unter Windows 8 oder zukünftigen Version

-   Mit .NET Framework 4.0 oder eine spätere Version auf X86 Maschinen

Wenn Sie eine Verfolgung mithilfe von WPR erfassen, ermöglicht WPR alle Anbieter, die zum Auflösen verwaltete Symbole in der Verfolgung erforderlich sind. WPR erstellt einen Ordner neben der gespeicherten Trace, der dieser verwalteten Symbole PDB-Dateien enthält. Wenn WPA Trace geöffnet wird, WPA sucht nach diesem Ordner und automatisch den Symbolpfad hinzugefügt. Wenn WPR nicht verwendet wurde, um die Ablaufverfolgung zu generieren, möglicherweise keine Symbole für .NET Framework-Programme vollständig decodieren oder überhaupt decodieren.

## <a name="javascript-symbols"></a>JavaScript-Symbole


Symbole Auflösung und Stapel für JavaScript Prozesse auf Systemen unterstützt werden, die die folgende Software ausgeführt werden:

-   Windows 7 zusammen mit Internet Explorer 10 oder höhere version

-   Webanwendungen, die unter Windows 8 JavaScript verwenden

WP ermöglicht die erforderliche Anbieter zum Decodieren Symbole für JavaScript-Code auf unterstützten Systemen. Die JavaScript-Methode Adressen und Stack-Frames werden auf eine JavaScript-Dateiname, den Methodennamen, die Zeilennummer und die Spaltennummer decodieren.

## <a name="a-href-idrelativearelative-paths-and-embedded-environment-variables"></a><a href="" id="relative"></a>Relative Pfade und eingebettete Umgebungsvariablen


Die ** \_NT\_SYMBOL\_PFAD** und ** \_NT\_SYMCACHE\_PFAD** Umgebungsvariablen können relative Pfade, absolute Pfade, Netzwerkpfade freigeben oder eingebetteten Umgebungsvariablen. WPA konvertiert relative Pfade in absolute Pfade beim Festlegen der relative Pfade. WPA konvertiert relativen Pfade, die WPA von Umgebungsvariablen geladen wird, wenn die Anwendung gestartet wird.

WPA konvertiert relative Pfade, die Sie im Dialogfeld **Symbolpfade konfigurieren** eingeben, wenn Sie das Dialogfeld schließen. Ändert das aktuelle Verzeichnis haben keinen Einfluss auf relative Pfade, die Sie bereits festgelegt haben. Zeigt das Dialogfeld **Symbolpfade konfigurieren** den aktuell festgelegten Pfade, wenn Sie im Dialogfeld zum ersten Mal öffnen, damit Sie die Möglichkeit, dass WPA relative Pfade erweitert sehen Feld.

WPA erweitert eingebetteten Umgebungsvariablen gleichzeitig, dass es relative Pfade erweitert wird. Da WPA Umgebungsvariablen erfasst wird, wenn die Anwendung gestartet wird, werden Änderungen an der Umgebungsvariablen, die außerhalb einer derzeit ausgeführten Instanz der WPA sind nicht in dieser Instanz angezeigt.

Andere Programme, die mithilfe der ** \_NT\_SYMCACHE\_PFAD** Umgebungsvariable wie **WinDbg** oder **Microsoft Visual Studio**, relative Pfade möglicherweise nicht verarbeiten oder eingebetteten Umgebungsvariablen auf die gleiche Weise.

## <a name="a-href-idsymcachepathasymcache-path"></a><a href="" id="symcachepath"></a>SymCache Pfad


WPA verwendet SymCache Dateien Cacheinformationen Symbol aus Programmdatenbankdateien (PDB) in eine Möglichkeit, die kompakter und leicht zugänglich ist. Nachdem WPA einen SymCache Ordner mit den Symbolen für eine Verfolgung aufgefüllt werden, ist die Symbole für diese Trace Neuladen viel schneller. Wenn eine Datei SymCache zu groß oder ist nicht mehr erforderlich ist, können Sie diese Datei SymCache sicher löschen. WPA füllt ihn wieder auf den Ordner SymCache mit neuen Dateien bei Bedarf. Sie können auch SymCache Dateien auf einen anderen Computer kopieren oder Freigeben von Dateien über ein Netzwerk an Symbol Laden auf unterschiedlichen Computern zu beschleunigen.

Wenn Sie das Dialogfeld **Symbolpfade konfigurieren** verwenden, um festzulegen der ** \_NT\_SYMCACHE\_PFAD** Umgebungsvariablen in einen Ordner, die WPA nicht zugreifen kann, die Schaltfläche **OK** schließt das Dialogfeld nicht. Sie erhalten jedoch keine Fehlermeldung angezeigt.

Wenn der ** \_NT\_SYMCACHE\_PFAD** -Umgebungsvariable nicht zugewiesene oder leer ist, WPA erstellt einen SymCache-Ordner im Stamm des Laufwerks, das die ausführbare Datei WPA enthält. Wenn die ** \_NT\_SYMCACHE\_PFAD** Umgebungsvariable auf einer Netzwerkfreigabe ausgeführt wird, die Variable erstellt einen SymCache-Ordner im Stamm des Laufwerks, im Ordner Program Files enthält. Dies ist in der Regel Laufwerk c: festgelegt.

### <a name="symcache-examples"></a>Beispiele für SymCache

Der folgende Befehl setzt die SymCache-Datei der **C:\\SymCache** Ordner:

``` syntax
C:\SymCache
```

Der folgende Befehl setzt die SymCache-Datei der **C:\\SymCache Ordner**, sucht der ** \\ \\Netzwerk\\SymCache** Ordner für Symbole, und klicken Sie dann auf Prozesse der ** \_NT\_SYMBOL\_PFAD** Umgebungsvariable:

``` syntax
C:\SymCache*\\network\SymCache
```

In diesem Beispiel werden alle Symbole, die im Beispiel in findet die ** \\ \\Netzwerk\\SymCache** Ordner in der **C:\\SymCache** Ordner. Dies ermöglicht dem Benutzer, erstellen Sie einen großen SymCache Ordner und kopieren Sie nur die Dateien, die der Benutzer für eine bestimmte Verfolgung in den festgelegten Ordner benötigt.

Um mehrere alternative SymCache Ordner suchen, Ordner Anfügen an den Suchpfad mit einem Sternchen (\*) Trennzeichen. Wenn WPA eine SymCache-Datei in einem der alternative Speicherorte findet, wird die Datei WPA nur in den ersten SymCache Ordner im Pfad kopiert. WPA versetzt neu erstellte SymCache Dateien auch in den ersten SymCache Ordner im Pfad.

Kopieren und schreiben jedoch weiterhin verwenden, deaktivieren, um die hierarchische Suchfeature die erste Position in der Pfad leer ist, lassen Sie wie im folgenden Beispiel dargestellt:

``` syntax
*\\network\SymCache
```

Wenn Sie mit diesem Befehl ausgeben, WPA sucht die \\ ** \\Netzwerk\\SymCache** Ordner. Allerdings WPA nicht kopieren Sie die Ergebnisse oder die generierten SymCache Dateien in einen anderen Ordner schreiben.

## <a name="a-href-idsymbolpathasymbol-path"></a><a href="" id="symbolpath"></a>Symbolpfad


Grundlegende Informationen zum **der \_NT\_SYMBOL\_PFAD** Umgebungsvariable, finden Sie unter den folgenden MSDN-Artikeln:

-   [Verwenden von SymSrv](http://go.microsoft.com/fwlink/p/?linkid=226201)

-   [Für Symbolpfade](http://go.microsoft.com/fwlink/p/?linkid=226202)

Symbol Laden in WPA hängt die Pfade, die ** \_NT\_SYMBOL\_PFAD** -Umgebungsvariable gibt (mit Ausnahme von Symbolen, die WPA bereits im Ordner SymCache zwischengespeicherte enthält). WPA durchsucht die Pfade sequenziell, beginnend auf der linken Seite. Laden von Symbolen aus einer PDB-Datei in einen dieser Pfade kann jedoch zeitaufwendig, insbesondere dann, wenn die PDB-DATEI auf einem Remotecomputer vorhanden ist. Aus diesem Grund wird empfohlen, Netzwerkpfade nach lokalen Pfade zu platzieren und für die Verwendung eines lokalen PDB-Caches für jeden Symbolserver, remote. Allerdings, auch wenn alle Symbole lokal gespeichert sind, kann WPA während der Zeit reagiert, sie Symbole geladen. WPA wird auf eine interaktive zurückgesetzt, nach dem Laden von Symbolen abgeschlossen ist.

Wenn die ** \_NT\_SYMBOL\_PFAD** Umgebungsvariable nicht festgelegt ist, WPA wird der folgende Standardwert verwendet:

``` syntax
 .;SRV*\Symbols* http://msdl.microsoft.com/download/symbols;
```

Semikolons (;) unterschiedlichen Pfaden zu trennen. Der erste Pfad entspricht dem Punkt (.). WPA ordnet diesen Pfad im aktuellen Ordner, wenn WPA Trace geladen wird. Finden Sie im Abschnitt [SymCache Pfad](#symcachepath) in diesem Artikel finden Sie weitere Informationen darüber, wie WPA relative Pfade verarbeitet.

Der zweite Pfad lautet wie folgt:

``` syntax
 SRV*\Symbols* http://msdl.microsoft.com/download/symbols
```

Außerdem müssen Sie den Pfad NGEN PB festlegen:

``` syntax
set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
```

Wenn Sie diesem Pfad angeben, WPA Symbole von Microsoft öffentliche Symbolserver-downloads und speichert die PDB-Dateien in den ** \\Symbole** Ordner (dieses Ordners ist relativ zu dem Installationsordner Windows Performance Toolkit)... Aus diesem Grund wird WPA den Ordner Symbole neben den Ordner SymCache. Ist der SymCache Ordner auf einer Netzwerkfreigabe, erstellt WPA jedoch den Symbole Ordner im Stamm des Laufwerks, die im Ordner Program Files enthält. Dies ist normalerweise Laufwerk c: festgelegt.

Wenn Sie nicht möchten, suchen und Laden Symbole von PDB-Dateien, legen Sie die ** \_NT\_SYMBOL\_PFAD** Umgebungsvariablen in einen lokalen Ordner, der keine Symbole, wie etwa einem Punkt (.) enthält. Lassen Sie nicht die ** \_NT\_SYMBOL\_PFAD** Umgebungsvariable leer. Wenn Sie lassen die ** \_NT\_SYMBOL\_PFAD** Umgebungsvariable leer ist, WPA wird standardmäßig verwendet.

Wenn WPA eine Aufzeichnung geöffnet wird, sieht WPA für einen Ordner mit dem gleichen Namen wie die Ablaufverfolgung, die die Erweiterung **.ngenpdb** verwendet. Wenn WPA dieses Ordners findet, fügt WPA den Ordner am Ende der ** \_NT\_SYMBOL\_PFAD** -Umgebungsvariablen. Windows Performance Aufzeichnung (WPR) erstellt automatisch einen Ordner mit PDB-Dateien für verwalteten Code, die während der Aufzeichnung WPR erfasst. Wenn Sie öffnen, beispielsweise die **C:\\trace.etl** WPA aufzeichnen, WPA sucht nach der **C:\\trace.etl.ngenpdb** Ordner. Wenn dieser Ordner vorhanden ist, fügt WPA des Ordners die ** \_NT\_SYMBOL\_PFAD** Umgebungsvariable.

## <a name="related-topics"></a>Verwandte Themen


[WPA-Features](wpa-features.md)

[Symbole laden oder Symbolpfade konfigurieren](load-symbols-or-configure-symbol-paths.md)

[Verwenden der CLR 4.0 NGEN PDB-Unterstützung](using-clr-40-ngen-pdb-support.md)

[Häufige Probleme von eingehenderen Analysen](../assessments/common-in-depth-analysis-issues.md)

 

 







