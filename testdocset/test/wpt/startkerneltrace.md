---
title: StartKernelTrace
description: StartKernelTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b8eab537-85ae-441e-aea9-486626ec0c16
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 49b8528d26dba62ea2732370a107f22570d70f01
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startkerneltrace"></a>StartKernelTrace


Diese Funktion registriert und startet eine Kernel-Ereignis Tracing-Sitzung. Sie können auch Stackwalking für bestimmte Kernelereignisse, die mit dieser Funktion aktivieren.

``` syntax
ULONG
WINAPI
StartKernelTrace(
__out PTRACEHANDLE TraceHandle,
__inout PEVENT_TRACE_PROPERTIES Properties,
__in ULONG cStackTracingEventIds
);
```

## <a name="parameters"></a>Parameter


<a href="" id="tracehandle--out-"></a>*TraceHandle* \[,\]  
Speichert einen Handle für ein Ereignis Tracing-Sitzung. Dieser Parameter ist auf 0 (null) festgelegt, wenn das Handle ungültig ist. Dieser Parameter sollte nicht mit UNGÜLTIGE verglichen werden\_BEHANDELN\_WERT. Verwenden Sie dieses Handle nicht auf, wenn die Funktion fehlschlägt.

<a href="" id="properties--in--out-"></a>*Eigenschaften* \[eingehend, ausgehend\]  
Speichert einen Zeiger auf ein [EREIGNIS\_TRACE\_EIGENSCHAFTEN Struktur](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409). EREIGNIS\_TRACE\_EIGENSCHAFTEN konfiguriert bestimmte Aspekte des Verhaltens der Sitzung.

Das erste Element des EREIGNISSES\_TRACE\_EIGENSCHAFTEN Struktur ist ein [WNODE\_IPX](http://go.microsoft.com/fwlink/p/?LinkID=212222&clcid=0x409), hier als **Wnode**bezeichnet.

Die folgenden EREIGNIS\_TRACE\_EIGENSCHAFTEN. Wnode Mitglieder müssen zum Konfigurieren von Kernel Trace Steuerelement festgelegt werden.

<a href="" id="buffersize"></a>**Puffergröße**  
Dieser Member enthält die Gesamtgröße des Speichers für die Sitzungseigenschaften tracing Ereignis in Bytes. Die Größe des Arbeitsspeichers muss genügend Speicherplatz zum Speichern der folgenden Daten enthalten:

-   Das EREIGNIS\_TRACE\_EIGENSCHAFTEN Struktur.

-   Die Sitzung Zeichenfolge.

-   Die Log-Dateinamenzeichenfolge.

<a href="" id="guid"></a>**GUID**  
Jede Tracingsitzung muss eine GUID, die definiert, um die Sitzung verweisen verfügen.

Für eine Sitzung der NT Kernel-Protokollierung muss dieser Member auf SystemTraceControlGuid festgelegt sein. Weitere Informationen zur Protokollierung Mode-Konstanten finden Sie unter [NT Kernel-Protokollierung-Konstanten](http://go.microsoft.com/fwlink/p/?LinkID=212229&clcid=0x409).

<a href="" id="clientcontext"></a>**ClientContext**  
Dieser Member wird die Uhr Auflösung, die verwendet wird, wenn der Protokollierung Zeitstempel für jedes Ereignis berechnet wird. Der Standardwert für diesen Member ist ein Leistungsindikator Abfrage.

Sie können einen der folgenden Werte angeben:

-   **1:** Abfrage Leistungsindikator (Abfrageverarbeitungskomponente). Die Abfrageverarbeitungskomponente enthält einen Zeitstempel für hohe Auflösung (100 Nanosekunden), jedoch ist schwieriger teurer abgerufen. Verwenden Sie diese Auflösung an, wenn Sie hohe Ereignis Sätze verfügen oder wenn der Consumer Ereignisse aus verschiedenen Puffer zusammengeführt. Auf Computern, die älter sind der Zeitstempel präzise möglicherweise nicht, da der Indikator manchmal vorwärts aufgrund von Hardwarefehlern übersprungen.

-   **2:** Systemzeit. Die Systemzeit enthält einen Zeitstempel für mit niedriger Auflösung (10 Millisekunden), jedoch ist schwieriger kostengünstigeren abrufen. Wenn die Lautstärke von Ereignissen hoch ist, kann die Lösung für Systemzeit nicht feine genug ist, um die Abfolge der Ereignisse zu bestimmen sein. In diesem Fall eine Reihe von Ereignissen müssen auf den gleichen Zeitstempel, aber die Reihenfolge, in der ETW die Ereignisse bietet, möglicherweise nicht korrekt.

-   **3:** CPU-Zyklus Counter. Der CPU Leistungsindikator bietet den höchsten Auflösung Zeitstempel und kostengünstigsten abgerufen wird. Allerdings der Indikator CPU ist unzuverlässig und sollte nicht in der Produktion verwendet werden. Beispielsweise ändert der Timer auf einigen Computern aufgrund von Thermal Häufigkeit und Power ändert, zusätzlich zur Unterbrechung der Ausführung im einige Staaten. Wenn Ihre Hardware dieses Typs Uhr nicht unterstützt, wird ETW Systemzeit verwendet. Dieser Wert wird in Windows Server 2003, Windows XP mit SP1 und Windows XP nicht unterstützt. Es wurde in Windows Server 2003 mit SP1 und Windows XP mit SP2 eingeführt.

<a href="" id="flags"></a>**Flags**  
Dieser Member muss WNODE enthalten\_FLAG\_RAYTRACED\_GUID, um anzugeben, dass die Datenstruktur Tracing Ereignisinformationen enthält und die Informationen, um eine Protokollierung gesendet werden. WNODE\_FLAG\_RAYTRACED\_GUID in Evntrace.h definiert ist.

Das folgende EREIGNIS\_TRACE\_müssen ebenfalls Elemente von EIGENSCHAFTEN festgelegt werden:

<a href="" id="logfilemode"></a>**LogFileMode**  
Gibt an, welche Protokollierung Modi werden in den Kernel-Ereignis Tracingsitzung verwendet werden. Dieser Member können Sie festlegen, dass Ereignisse in einer Protokolldatei und/oder in Echtzeit Consumer geschrieben werden soll.

Dieser Member kann auch verwendet werden, um anzugeben, dass die Sitzung eine private Protokollierung Sitzung ist. Eine oder mehrere Modi können angegeben werden. Eine Liste der möglichen Modi finden Sie unter [Logging Mode-Konstanten](https://msdn.microsoft.com/library/windows/desktop/aa364080.aspx).

**Hinweis**  
Geben Sie in Echtzeit Protokollierung, es sei denn, es in Echtzeit Consumer bereit gibt, um die Ereignisse zu verarbeiten. Wenn keine Echtzeit Consumer vorhanden sind, werden die Ereignisse in eine Datei Wiedergabe geschrieben. Die Größe der Datei Wiedergabe ist beschränkt. Wenn der Grenzwert erreicht ist, werden keine neuen Ereignisse in der Protokolldatei oder die Wiedergabe Datei protokolliert. Die Protokollierungsfunktionen ein Fehler auftritt, mit dem STATUS\_PROTOKOLL\_DATEI\_VOLLSTÄNDIGE.

 

<a href="" id="enableflags"></a>**EnableFlags**  
Dieser Member ist nur für NT Kernel-Protokollierung-Sitzungen verwendet. Es identifiziert wird, welche Ereignisse Trace an den Kernelprotokollierung. Logisches **OR**verwenden, kann dieser Member einen oder mehrere Werte enthalten. Zusätzlich zu der angegebenen Ereignisse protokolliert die Kernelprotokollierung auch Hardwareereignisse Konfiguration.

Die folgenden Steuerelements Ablaufverfolgungsflags stehen zusätzlich zu den angebotenen-Ereignis\_TRACE\_EIGENSCHAFTEN:

-   [EREIGNIS\_TRACE\_FLAG\_VERTEILER](https://msdn.microsoft.com/library/dn640677.aspx)

-   [EREIGNIS\_TRACE\_FLAG\_VIRTUELLEN\_ZUORDNEN](https://msdn.microsoft.com/library/dn631804.aspx)

<a href="" id="logfilenameoffset"></a>**LogFileNameOffset**  
Stellt diese Zahl zugewiesen der Offset vom Beginn des Arbeitsspeichers auf die Struktur bis zum Anfang der die Null endende Zeichenfolge, die den Namen der Protokolldatei enthält.

Folgendes gilt:

-   Die Dateinamenerweiterung sollte ETL sein.

-   Alle Ordner im Pfad müssen vorhanden sein.

-   Der Pfad kann relative, absolute, lokal oder remote sein.

-   Der Pfad muss Umgebungsvariablen, nicht enthalten, da diese Variablen nicht erweitert werden.

-   Der Benutzer, der die Ablaufverfolgung initiiert benötigen Schreibberechtigung für den Ordner.

-   Der Name der Protokolldatei ist auf 1024 Zeichen begrenzt.

-   Wenn Sie auf EREIGNIS **LogFileMode** festlegen\_TRACE\_PRIVATE\_PROTOKOLLIERUNG\_MODUS oder eine EREIGNISPROZEDUR\_TRACE\_DATEI\_MODUS\_NEWFILE, sicherzustellen, dass genügend Speicher zum Einschließen von der Prozess-ID, die an der Dateiname private Protokollierung Sitzungen als auch die fortlaufende Zahl, die hinzugefügt wird und die Protokolldateien angefügt wird erstellt werden mit den neuen Dateimodus Protokoll.

-   Wenn Sie nicht, zum Protokollieren von Ereignissen in einer Protokolldatei möchten (beispielsweise angeben von EREIGNIS\_TRACE\_REALEN\_ZEIT\_nur im MODUS), **LogFileNameOffset** auf 0 (null) festgelegt. Wenn Sie nur in Echtzeit Protokollierung angeben und einen Offset auch mit einer gültigen Protokolldateiname bereitstellen, wird der Name der Protokolldatei ein Protokoll sequenziellen Datei und Protokolldateien Ereignisse in die Protokolldatei erstellen. Die sequenzielle Protokolldatei ist auch erstellt, wenn **LogFileMode** 0 (null ist) und einen Offset werden durch eine gültige Protokolldateiname bereitgestellt.

-   Wenn Sie Ereignisse in einer Protokolldatei protokollieren möchten, müssen Sie genügend Arbeitsspeicher für diese Struktur Einbeziehung der Name der Protokolldatei und der Sitzungsname der Struktur reservieren. Der Name der Protokolldatei muss den Sitzungsnamen im Arbeitsspeicher folgen.

-   Ablaufverfolgungsdateien werden die standardmäßige Security Descriptor, was bedeutet, dass die Protokolldatei dieselbe ACL als das übergeordnete Verzeichnis hat mit erstellt. Wenn Sie Zugriff auf die Dateien einschränken möchten, erstellen Sie ein übergeordnetes Verzeichnis mit den entsprechenden Zugriffssteuerungslisten.

<a href="" id="loggernameoffset"></a>**LoggerNameOffset**  
Dieser Member stellt den Offset vom Anfang des Arbeitsspeichers, die die Struktur, die den Anfang der Null endende Zeichenfolge, die den Sitzungsnamen enthält zugewiesen ist.

Folgendes gilt:

-   Der Sitzungsname ist auf 1024 Zeichen begrenzt.

-   Der Sitzungsname wird Groß-/Kleinschreibung unterschieden und muss eindeutig sein.

-   Beim Arbeitsspeicher für diese Struktur zuordnen, muss über genügend Arbeitsspeicher zum zählen der Sitzungsname und der Struktur Protokolldateiname reserviert werden.

-   Der Sitzungsname muss vor der Name der Protokolldatei im Arbeitsspeicher stehen. Der Name der Protokolldatei muss in der versetzten Bereich kopiert werden. Diese Funktion schreibt der Sitzungsname von KERNEL definierten\_PROTOKOLLIERUNG\_NAME.

Je nach Art der Protokolldatei gewählt kann es erforderlich sind, um die Member **MaximumFileSize** festgelegt sein.

**Hinweis**  
Es ist nicht notwendig, den Namen der Protokollierung auf die **LoggerNameOffset** festgelegt werden, da diese Funktion immer den KERNEL verwendet\_PROTOKOLLIERUNG\_Namenswert StartKernelTrace aufrufen. Diese Funktion überprüft, ob die **Wnode.Guid** **SystemTraceControlGuid**entspricht. Wenn keine FEHLER zurückgegeben\_UNGÜLTIGE\_PARAMETER. Wenn **Wnode.Guid** **KernelRundownGuid**entspricht, sollte der Name der Protokollierung angegeben werden. Die **KernelRundownGuid** ist das Steuerelement GUID verwendet zum Protokollieren von Ereignissen wie vorhandenen Prozessinformationen Thread, Bilder pro Prozess, geladen und Hardwarekonfiguration wie CPU, Video, Datenträger, Netzwerkkarten, Services, power Plug & Play und IDE-Kanäle auf dem Datenträger.

 

## <a name="return-value"></a>Rückgabewert


FEHLER\_der Vorgang ERFOLGREICH war erfolgreich.

Mögliche Fehler werden in der folgenden Tabelle beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlerwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ERROR_ALREADY_EXISTS</p></td>
<td><p>Nur eine einzige Instanz der Kernelprotokollierung, die auf dem System ausgeführt werden. Wenn diese Funktion versucht, starten, nachdem eine weitere Komponente Kernel Protokollierung gestartet wurde, wird dieser Fehler möglicherweise zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><p>ERROR_INVALID_FLAGS</p></td>
<td><p>Möglicherweise gibt an, dass ungültige Ablaufverfolgungsflags in <strong>Properties.EnableFlags</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>ERROR_OUT_OF_MEMORY</p></td>
<td><p>Möglicherweise gibt Fehler EVENT_TRACE_PROPERTIES reserviert werden.</p></td>
</tr>
</tbody>
</table>

 

Wenn die Funktion einen anderen aufgeführten Grund ein Fehler auftritt, wird ein Systemfehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise


Wenn **StackTracingEventIds** Ereignisse enthalten, die nicht in der **EREIGNIS aktiviert sind\_TRACE\_EIGENSCHAFTEN. EnableFlags** Feld oder konnte nicht decodiert werden durch Kernel Trace-Steuerelement, die Flags werden ignoriert und keine Fehlercode wird zurückgegeben.

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Funktionen](functions-wpa.md)

[Benutzerdefinierte Einfügung von Systeminformationen](custom-injection-of-system-information.md)

 

 







