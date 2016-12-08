---
title: Erfassen von Trace Ereignisprotokolle auf Windows 10 Mobile
description: Erfassen von Trace-Ereignisprotokollen auf Windows 10 Mobile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5a4a7408-3dd8-4322-91ce-73ab75135470
ms.openlocfilehash: 5d91f2a45bb48a4c7eb0cdff71ea5bff15edb39e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-event-trace-logs-on-windows-10-mobile"></a>Erfassen von Trace-Ereignisprotokollen auf Windows 10 Mobile


TraceLog und Xperf dienen zum Ereignis Ablaufverfolgungsprotokolle unter Windows 10 Mobile zu erfassen.

**Wichtige**  
Zum Erfassen von Ablaufverfolgungsprotokollen muss das Geräteabbild mit den entsprechenden Typ und die Pakete erstellt werden. Dies erfolgt durch Ändern der OEMInput-Datei, um das Element **ReleaseType** auf **Test**festgelegt und das Element **Features** **TESTINFRASTRUCTURE** hinzuzufügen.

 

## <a name="step-1-install-the-windows-performance-toolkit"></a>Schritt 1: Installieren von Windows Performance Toolkit


Windows Performance Toolkit (WPT) ist erforderlich, um den Prozess Ereignis Ablaufverfolgungsprotokolle mit Xperf. Die WPT ist Teil der [Windows Assessment and Deployment Kit (Windows ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803).

## <a name="step-2-install-and-configure-tshell"></a>Schritt 2: Installieren und Konfigurieren von TShell


TShell ist erforderlich, Tracelog ausgeführt.

## <a name="step-3-verify-device-is-connected"></a>Schritt 3: Stellen Sie sicher, dass das Gerät verbunden ist


Stellen Sie sicher, dass das Gerät mit TShell verbunden ist, indem Sie den Befehl Dird im Befehlsfenster TShell ausführen. Sicherstellen Sie, dass ein Verzeichnis aufgelistet, die auf dem Gerät angezeigt wird. Wenn eine Fehlermeldung angezeigt wird, sicherzustellen Sie, dass TShell ordnungsgemäß konfiguriert ist und an der Eingabeaufforderung Gerät wird oberhalb der regulären Befehlszeile im Fenster TShell ähnlich der folgenden angezeigt:

``` syntax
DEVICE C:\
PS C:\>
```

## <a name="step-4-run-tracelog-to-start-event-trace-logging"></a>Schritt 4: Ausführen Tracelog Trace Protokollierung starten


Verwenden das Befehlsfenster TShell, führen Sie Tracelog gewünschten Parameter Trace Protokollierung starten. Zwei grundlegende Beispiele sind unten aufgeführt.

**Wichtige**  
Unter Windows Mobile 10 Tracelog muss die Protokolle innerhalb der C: platzieren\\Daten Directory aufgrund größeneinschränkungen Partition. Achten Sie darauf mit dem Flag-f Tracelog C: Verwendung konfigurieren\\Daten.

 

Detaillierte Tracelog Befehlszeilen-Syntax finden Sie unter [Tracelog Befehlssyntax](http://msdn.microsoft.com/library/windows/hardware/ff553012.aspx). Weitere Beispiele finden Sie unter [Tracelog Beispiele](http://msdn.microsoft.com/library/windows/hardware/ff553026.aspx).

### <a name="example-1"></a>In Beispiel 1

Der folgende Befehl startet eine Sitzung, die Verfolgung von Prozess und die Thread-erstellen/löscht, Kernel und Modus Bild laden/entladen Ereignisse, DPC Ereignisse, Kontextwechsel und CPU Samplingprofile ermöglicht.

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\data
PS C:\> cmdd 'tracelog -start MyTrace -f c:\data\MyLog.etl -eflag PROC_THREAD+LOADER+DPC+CSWITCH+PROFILE'

Turning On group: PROC_THREAD
Turning On group: LOADER
Turning On group: DPC
Turning On group: CSWITCH
Turning On group: PROFILE
Adding GroupMask ExtItem
Logger Started...
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyTrace
Logger Id:              0x14
Logger Thread Id:       0000054C
Guid:                   77eaa944-426b-11e1-86a3-fb317490c92a
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            8 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      26
Free Buffers:           0
Buffers Written:        28
Events Lost:            177
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process Thread ImageLoad CxtSwap Dpc Profile
Log Filename:           c:\data\MyLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>In Beispiel 2

Die folgenden Befehle starten Sie eine neue Sitzung mit dem Namen "MyPowerTrace" und den Microsoft Windows Kernel Power Anbieter aktivieren.

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\data
PS C:\> cmdd 'tracelog -start MyPowerTrace -b 1024 -f C:\data\MyPowerLog.etl -eflags Process'
Turning On group: PROCESS
Adding GroupMask ExtItem
Logger Started...
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyPowerTrace
Logger Id:              0x1d
Logger Thread Id:       00000C38
Guid:                   52dd9cee-926c-11e1-bc7e-0011beb0dbf4
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            1024 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      4
Free Buffers:           3
Buffers Written:        1
Events Lost:            0
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process
Log Filename:           C:\data\MyPowerLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\> cmdd 'tracelog -enable MyPowerTrace -guid #331C3B3A-2005-44C2-AC5E-77220C37D6B4'
Enabling 331c3b3a-2005-44c2-ac5e-77220c37d6b4 (Flags = 0x00000000 Level = 0  ) to logger 29
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyPowerTrace
Logger Id:              0x1d
Logger Thread Id:       00000C38
Guid:                   52dd9cee-926c-11e1-bc7e-0011beb0dbf4
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            1024 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      4
Free Buffers:           2
Buffers Written:        1
Events Lost:            0
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process
Log Filename:           C:\data\MyPowerLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

## <a name="step-5-run-scenarios-or-tests"></a>Schritt 5: Szenarien oder Tests ausführen


Ereignis-ablaufverfolgungsprotokollierung ist nun aktiviert. Führen Sie Tests aus, den, die Sie analysieren möchten, oder Szenarien.

## <a name="step-6-run-tracelog-to-flush-the-buffers-and-stop-event-trace-logging"></a>Schritt 6: Run Tracelog leeren Puffer und Trace ereignisprotokollierung beenden


Wenn die Szenarien oder Tests abgeschlossen sind, verwenden Sie Tracelog leeren Puffer und Trace Protokollierung beenden.

### <a name="example-1"></a>In Beispiel 1

Die folgenden Befehle geleert und beendet die Sitzung "MyTrace".

``` syntax
cmdd 'tracelog -flush MyTrace'
cmdd 'tracelog -stop MyTrace'
```

### <a name="example-2"></a>In Beispiel 2

Die folgenden Befehle geleert und beendet die Sitzung "MyPowerTrace".

``` syntax
cmdd 'tracelog -flush MyPowerTrace'
cmdd 'tracelog -stop MyPowerTrace'
```

## <a name="step-7-run-xperf-on-the-device"></a>Schritt 7: Ausführen Xperf auf dem Gerät


Führen Sie Xperf am Gerät, um das Protokoll zu verarbeiten.

### <a name="example-1"></a>In Beispiel 1

``` syntax
DEVICE C:\data
PS C:\> cmdd 'xperf -merge MyLog.etl c:\data\MyLogOut.etl'
Merged Etl: c:\data\MyLogOut.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>In Beispiel 2

``` syntax
DEVICE C:\data
PS C:\> cmdd 'xperf -merge MyPowerLog.etl c:\data\MyPowerLogOut.etl'
Merged Etl: c:\data\MyPowerLogOut.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

## <a name="step-8-copy-trace-log-from-device"></a>Schritt 8: Kopieren Sie Ablaufverfolgungsprotokoll vom Gerät


Kopieren Sie mithilfe des Befehls **Getd** im Befehlsfenster TShell zusammengeführten Ablaufverfolgungsprotokoll auf dem Telefon.

### <a name="example-1"></a>In Beispiel 1

``` syntax
DEVICE C:\data
PS C:\> getd MyLogOut.etl C:\Users\username\Documents
C:\data\MyLogOut.etl
1 file(s) copied from device.
DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>In Beispiel 2

``` syntax
DEVICE C:\data
PS C:\> getd MyPowerLogOut.etl C:\Users\username\Documents
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\data
PS C:\>
```

Sie können die Datei auch umbenennen, kopieren Sie jederzeit.

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\
PS C:\> getd C:\data\MyPowerLogOut.etl C:\Users\username\Documents\NewName.etl
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\
PS C:\>
```

## <a name="step-9-run-xperf-on-the-desktop-pc"></a>Schritt 9: Ausführen Xperf auf dem desktop-PC


Führen Sie Xperf auf den desktop-PC für die weitere Verarbeitung weiterleitet. Auf 32-Bit-Betriebssystemen Xperf installiert ist, in C:\\Program Files\\Windows Kits\\10\\Windows Performance Toolkit. Auf 64-Bit-Betriebssystemen installiert ist C:\\Program Files (x86)\\Windows Kits\\10\\Windows Performance Toolkit.

### <a name="example-1"></a>In Beispiel 1

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i d:\MyLogOut.etl -o MyLogCSV.csv -tle
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

### <a name="example-2"></a>Beispiel 2

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i MyPowerLogOut.etl -o MyPowerLogCSV.csv -tle 
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

 

 






