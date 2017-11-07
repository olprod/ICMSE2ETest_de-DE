---
title: Benutzerdefinierte Einschleusung von Systeminformationen
description: "Benutzerdefinierte Einfügung von Systeminformationen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 18d70466-eb0c-4a3a-a711-59cda913b477
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 93154357f92ff783f1e6f57d1e785d90f959ecb0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="custom-injection-of-system-information"></a>Benutzerdefinierte Einfügung von Systeminformationen


Kernel Trace Steuerelement können benutzerdefinierte Einfügung von Systeminformationen, wenn mehrere Ablaufverfolgungsdateien in einer gemeinsamen Ausgabedatei Trace zusammengeführt werden. Zum Einbeziehen von Systeminformationen wird eine einzelne Flag oder eine Kombination von Flags in der [CreateMergedTraceFile](createmergedtracefile.md) -Funktion festgelegt. Folgender Flags definieren Sie die Systeminformationen die zusammengeführten Ablaufverfolgungsdatei hinzugefügt werden:

<a href="" id="-define-event-trace-merge-extended-data-none-0x00000000"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_NONE 0 x 00000000  
Keine Systeminformationen sollte die zusammengeführten Ablaufverfolgungsdatei hinzugefügt werden.

<a href="" id="-define-event-trace-merge-extended-data-imageid-0x00000001"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_IMAGEID 0 x 00000001  
Fügen Sie Bildinformationen wie Prüfsumme und Zeitstempel beim Symbol-Lookup verwendet.

<a href="" id="-define-event-trace-merge-extended-data-buildinfo-0x00000002"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_BUILDINFO 0 x 00000002  
Betriebssystem Buildinformationen wie Produktname eingefügt, und Erstellen von Lab.

<a href="" id="-define-event-trace-merge-extended-data-volume-mapping-0x00000004"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_VOLUME\_0 x 00000004 ZUORDNEN  
Fügen Sie Volume Zuordnung zwischen MS-DOS- und Windows NT-Pfade. Die Nutzlast des Ereignisses enthält zwei NULL terminierte Unicode-Zeichenfolgen. Die erste Zeichenfolge enthält den Pfad des Windows NT und die zweite Zeichenfolge enthält den MS-DOS-Pfad. Die Länge der Nutzlast ist die Größe in Bytes, die zwei Zeichenfolgen, einschließlich der NULL-Zeichen.

Beispielsweise ein Windows NT-Path "\\Gerät\\HarddiskVolume1\\" in der MS DOS-Pfad übersetzt werden würde "C:\\".

<a href="" id="-define-event-trace-merge-extended-data-winsat-0x00000008"></a>\#EREIGNIS definieren\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_WINSAT 0 x 00000008  
Fügen Sie WinSat Informationen.

<a href="" id="-define-event-trace-merge-extended-data-event-metadata-0x00000010"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_EREIGNIS\_0 x 00000010 METADATEN  
Fügen Sie Trace-Header (TDH) Metadaten für Ereignisse, die auf anderen Computern als dem Computer erfasst werden, auf denen die Ereignisse analysiert werden. Weitere Informationen zu Ablaufverfolgungsinformationen Daten-Header finden Sie unter [Event Tracing](https://msdn.microsoft.com/library/bb968803.aspx).

<a href="" id="-define-event-metadata-log-type-trace-event-info-0x20"></a>\#EREIGNIS definieren\_METADATEN\_PROTOKOLL\_TYP\_TRACE\_EREIGNIS\_INFO 0 x 20  
Einfügen von Trace-Informationen, die durch EREIGNIS protokollierten Ereignisse identifiziert\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_EREIGNIS\_METADATEN.

<a href="" id="-define-event-metadata-log-type-event-map-info-0x21"></a>\#Definieren von EREIGNIS\_METADATEN\_PROTOKOLL\_TYP\_EREIGNIS\_Zuordnung\_INFO 0 x 21  
Fügen Sie die Informationen, die die Metadaten für die durch das Festlegen des EREIGNISSES protokollierten Ereignisse definiert\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_EREIGNIS\_METADATEN-Flag. Weitere Informationen finden Sie unter [EREIGNIS\_Zuordnung\_INFO-Struktur](https://msdn.microsoft.com/library/windows/desktop/aa964762.aspx).

<a href="" id="-define-event-trace-merge-extended-data-perftrack-metadata-0x00000020"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_PERFTRACK\_0 x 00000020 METADATEN  
Fügen Sie **PerfTrack** Ereignisse Metadaten für die Decodierung **PerfTrack** Ereignisse auf unterschiedlichen Computern. Diese Ereignisse werden nur unter Windows 7 und Windows Server 2008 eingefügt.

<a href="" id="-define-event-trace-merge-extended-data-default-0x000fffff"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_STANDARD 0x000FFFFF  
Fügen Sie die Daten für das Bild, Build, Volume-Zuordnung, WinSat, Metadaten und **PerfTrack** Metadaten.

<a href="" id="-define-event-trace-merge-extended-data-all-0xfffffff"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_ALLE 0xFFFFFFF  
Fügen Sie alle erweiterten Dateninformationen zur Trace Ausgabedatei.

<a href="" id="-define-event-trace-merge-extended-data-network-interface-0x00000040"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_NETZWERK\_SCHNITTSTELLE 0 x 00000040  
Fügen Sie Netzwerkschnittstelleninformationen.

<a href="" id="-define-event-trace-merge-extended-data-ngen-pdb------------0x00000080"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_NGEN\_PDB 0x00000080  
Erstellen Sie PDB-Dateien, um Symbol laden NGEN Binärdateien zu aktivieren, die in der Verfolgung angezeigt werden.

<a href="" id="-define-event-trace-merge-extended-data-compress-trace------0x10000000"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_KOMPRIMIEREN\_TRACE 0 x 10000000  
Komprimieren Sie den zusammengeführten Trace. Nur unterstützt Windows 8 und höher.

<a href="" id="-define-event-trace-merge-extended-data-inject-only---------0x40000000"></a>\#Definieren von EREIGNIS\_TRACE\_ZUSAMMENFÜHREN\_EXTENDED\_DATEN\_EINLEGEN\_NUR 0 x 40000000  
Nur Identifikationsinformationen Bild einfügen, Ereignisse nicht aus der Eingabe Ablaufverfolgung(en) kopieren.

## <a name="remarks"></a>Hinweise


**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Kernel Trace Steuerelement API-Referenz](kernel-trace-control-api-reference.md)

[CreateMergedTraceFile](createmergedtracefile.md)

 

 







