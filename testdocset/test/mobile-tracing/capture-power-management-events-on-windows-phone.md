---
title: Erfassen Sie Power Management Ereignisse auf Windows 10 Mobile
description: Erfassen Sie Power Management Ereignisse auf Windows 10 Mobile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 23f40b02-33ec-4a67-8a1c-f036e720c5bf
ms.openlocfilehash: c3e5a9682bd5ef13c4171e9fc16417ed44a8eb78
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-power-management-events-on-windows-10-mobile"></a>Erfassen Sie Power Management Ereignisse auf Windows 10 Mobile


TraceLog und Xperf dienen zum Erfassen Ablaufverfolgungsprotokolle auf 10 Mobile Windows Power-Management-Ereignis.

**Wichtige**  
Zum Erfassen von Ablaufverfolgungsprotokollen muss das Telefon Bild mit den entsprechenden Typ und die Pakete erstellt werden. Dies erfolgt durch Ändern der OEMInput-Datei, um das Element **ReleaseType** auf **Test**festgelegt und das Element **Features** **TESTINFRASTRUCTURE** hinzuzufügen.

 

## <a name="step-1-install-the-windows-performance-toolkit"></a>Schritt 1: Installieren von Windows Performance Toolkit


Windows Performance Toolkit (WPT) ist erforderlich, um den Prozess Ereignis Ablaufverfolgungsprotokolle mit Xperf. Die WPT ist Teil der [Windows Assessment and Deployment Kit (Windows ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803).

## <a name="step-2-install-and-configure-tshell"></a>Schritt 2: Installieren und Konfigurieren von TShell


TShell ist erforderlich, Tracelog ausgeführt.

## <a name="step-3-verify-device-is-connected"></a>Schritt 3: Stellen Sie sicher, dass das Gerät verbunden ist


Stellen Sie sicher, dass das Gerät mit TShell verbunden ist, indem Sie den Befehl Dird im Befehlsfenster TShell ausführen. Stellen Sie sicher, dass ein Verzeichnis aufgelistet, auf dem Telefon angezeigt wird. Wenn eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass die TShell ordnungsgemäß konfiguriert ist, und an der Eingabeaufforderung Gerät wird oberhalb der regulären Befehlszeile im Fenster TShell ähnlich der folgenden angezeigt:

``` syntax
DEVICE C:\
PS C:\>
```

## <a name="step-4-run-tracelog-to-start-power-management-event-trace-logging"></a>Schritt 4: Ausführen Tracelog Power Management Trace Protokollierung starten


Führen Sie im Befehlsfenster TShell verwenden, Tracelog mit den empfohlenen Power Management-Anbieter und die Einstellungen weiter unten.

**Wichtige**  
Unter Windows Mobile 10 Tracelog muss die Protokolle innerhalb der C: platzieren\\Daten Directory aufgrund größeneinschränkungen Partition. Achten Sie darauf mit dem Flag-f Tracelog C: Verwendung konfigurieren\\Daten.

 

Detaillierte Tracelog Befehlszeilen-Syntax finden Sie unter [Tracelog Befehlssyntax](http://msdn.microsoft.com/library/windows/hardware/ff553012.aspx). Weitere Beispiele finden Sie unter [Tracelog Beispiele](https://msdn.microsoft.com/library/windows/hardware/ff553026).

Verwenden Sie die folgenden Befehle, um eine Sitzung namens "MyPowerTrace" erstellen und Aktivieren von des Microsoft-Windows-Kernel-Power-Anbieters.

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

Aktivieren Sie zusätzliche Power Management weiterführende Anbieter aus, falls gewünscht.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Provider</th>
<th>Befehlszeile</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft.Windows.Kernel.Processor.Power</p></td>
<td><p>Cmdd ' Tracelog-MyPowerTrace - Guid #0F67E49F-FE51-4E9F-B490-6F2948CC6027 aktivieren '</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Windows.PDC</p></td>
<td><p>Cmdd ' Tracelog-MyPowerTrace - Guid #A6BF0DEB-3659-40AD-9F81-E25AF62CE3C7 aktivieren '</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Windows.Kernel.ACPI</p></td>
<td><p>Cmdd ' Tracelog-MyPowerTrace - Guid #C514638F-7723-485B-BCFC-96565D735D4A aktivieren '</p></td>
</tr>
</tbody>
</table>

 

Der folgende Befehl fordert des Dienstanbieters für das Melden von Statusinformationen an. Sammeln von Zustandsinformationen wird an den Anfang oder das Ende einer Ablaufverfolgung für initiiert. Dadurch wird sichergestellt, dass die erforderlichen Informationen für den Zustand zu einem bestimmten Zeitpunkt in der Verfolgung zu bestimmen angemeldet ist.

``` syntax
cmdd 'tracelog -capturestate MyPowerTrace -guid #331C3B3A-2005-44C2-AC5E-77220C37D6B4'
```

## <a name="step-5-run-scenarios-or-tests"></a>Schritt 5: Szenarien oder Tests ausführen


Ereignis-ablaufverfolgungsprotokollierung ist nun aktiviert. Führen Sie Tests aus, den, die Sie analysieren möchten, oder Szenarien.

## <a name="step-6-run-tracelog-to-flush-the-buffers-and-stop-event-trace-logging"></a>Schritt 6: Run Tracelog leeren Puffer und Trace ereignisprotokollierung beenden


Wenn die Szenarien oder Tests abgeschlossen sind, verwenden Sie Tracelog leeren Puffer und Trace Protokollierung beenden.

``` syntax
cmdd 'tracelog -flush MyPowerTrace'
cmdd 'tracelog -stop MyPowerTrace'
```

## <a name="step-7-run-xperf-on-the-device"></a>Schritt 7: Ausführen Xperf auf dem Gerät


Führen Sie Xperf am Gerät, um das Protokoll zu verarbeiten.

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
PS C:\> getd C:\data\MyPowerLogOut.etl C:\Users\username\Documents\NewName.etl
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\
PS C:\>
```

## <a name="step-9-run-xperf-on-the-pc"></a>Schritt 9: Ausführen von Xperf auf dem PC


Führen Sie Xperf auf dem PC für die weitere Verarbeitung weiterleitet. Auf 32-Bit-Betriebssystemen Xperf installiert ist, in C:\\Program Files\\Windows Kits\\10\\Windows Performance Toolkit. Auf 64-Bit-Betriebssystemen installiert ist C:\\Program Files (x86)\\Windows Kits\\10\\Windows Performance Toolkit.

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i MyPowerLogOut.etl -o MyPowerLogCSV.csv -tle
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

 

 






