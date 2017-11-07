---
title: Device.Imaging.Printer
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: c8f7a0e9c4f0eff60951f4f20000208cb5a72f65
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceimagingprinter"></a>Device.Imaging.Printer

 - [Device.Imaging.Printer.Base](#device.imaging.printer.base)
 - [Device.Imaging.Printer.Mobile](#device.imaging.printer.mobile)
 - [Device.Imaging.Printer.Mobile.WSD20](#device.imaging.printer.mobile.wsd20)
 - [Device.Imaging.Printer.OXPS](#device.imaging.printer.oxps)
 - [Device.Imaging.Printer.USB](#device.imaging.printer.usb)
 - [Device.Imaging.Printer.WSD](#device.imaging.printer.wsd)
 - [Device.Imaging.Printer.XPS](#device.imaging.printer.xps)

<a name="device.imaging.printer.base"></a>
## <a name="deviceimagingprinterbase"></a>Device.Imaging.Printer.Base

### <a name="deviceimagingprinterbaseapplicationverifier"></a>Device.Imaging.Printer.Base.applicationVerifier

*Printer-Treiberkomponenten müssen Application Verifier Testkriterien entsprechen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle im Benutzermodus Module (DLL- oder .exe-Dateien), die Teil der jeweilige Druckertreiber sind erfüllen müssen, die Kriterien für Application Verifier-Tests. Während des Testens Treiber muss Application Verifier für Prozesse aktiviert werden in der Treiber-Module ausgeführt. Application Verifier verursacht eine Unterbrechung, wenn Application Verifier einen Fehler erkennt.
Für Druckertreiber sind dies allgemeine Anwendungen, die während der Tests eingeschaltet Application Verifier benötigen:

-   Splwow64.exe.

-   Spoolsv.exe. Der Prozess lädt das Rendering und die Benutzeroberfläche Teile des Treibers während der Tests print.

-   Printfilterpipelinesvc.exe. Der Prozess lädt die XPS Rendering Filter.

-   Alle Anbieters Anwendungen, die Teil des Treiberpakets, wie ein benutzerdefinierter Statusmonitor sind. Alle Teile des Treiberpakets, die signiert werden müssen robuste sein.

-   Alle Tests, die Treiber-Module für Rendering oder zur Benutzeroberfläche zu laden. Die Tests laden häufig Benutzeroberfläche und Rendering Module.

Die folgenden Tests Application Verifier müssen während der Tests für die folgenden Prozesse eingeschaltet sein:

-   Heap
-   Sperren
-   Verarbeitet
-   FilePaths
-   HighVersionLie
-   DFWChecksNonSetup
-   Dateiaktivitäten
-   Printing

*Hinweise zum Entwurf*

Informationen zu Application Verifier finden Sie unter <http://go.microsoft.com/fwlink/?LinkId=58371>*.*

### <a name="deviceimagingprinterbaseconfigurationfiles"></a>Device.Imaging.Printer.Base.configurationFiles

*Version 4-Druckertreiber müssen gültige Konfigurationsdateien bereitstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Version 4-Druckertreiber müssen gültige Konfigurationsdateien bereitstellen.

-   Diese Dateien müssen syntaktisch gültig gemäß dem WDK sein.

-   Wenn von der Hardware unterstützt, müssen die Konfigurationsdateien die folgenden Features unterstützt:

    -   Ausrichtung
    -   Duplexdruck
    -   Collate
    -   N-nach-oben
    -   Papierformat
    -   Papiertyp
    -   Schacht
    -   Qualität
    -   Farbe
    -   Heften
    -   Hole Stanzungen
    -   Bindung

-   GPD oder PPD Dateien sollten die Mehrzahl der Features und Einschränkungen in der Treiber PrintCapabilities dargestellt definieren. JavaScript-Implementierung sollten diese Funktionen ergänzen, je nach Bedarf.

-   JavaScript-Dateien müssen syntaktisch gültig gemäß dem WDK sein.

    -   Sie müssen in dem Paket enthalten sein und darf nicht in einem Unterverzeichnis des Pakets sein.

    -   Sie können nur mit Version 4-Druckertreiber enthalten sein.

    -   Sie sollten sicher entworfen und Überprüfen von nicht vertrauenswürdigen Daten, die analysiert werden soll; Dazu gehören PrintCapabilities, PrintTicket, XPS-Dokumente und -Eigenschaftenbehälter.

### <a name="deviceimagingprinterbaseconnectionrecovery"></a>Device.Imaging.Printer.Base.connectionRecovery

*Ein Drucker muss weiterhin normal ausgeführt werden, wenn ein Computer nicht verfügbar, während ein Druckauftrag ist.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn ein Computer während einer Druckauftrag (beispielsweise wird Wenn der Computer in dem Zustand wechselt oder ein Netzwerkfehler oder ein anderes Ereignis unterbrochen wird die Verbindung zwischen Computer und Drucker) nicht verfügbar, muss der Drucker wiederherstellen, so dass normale Druckvorgänge ohne Benutzereingriff fortgesetzt werden können.

*Hinweise zum Entwurf*

Der Drucker muss insbesondere nicht fehlschlagen in einen Zustand, in dem der Benutzer manuell Cycle power muss, den Drucker oder einen Papierstau deaktivieren.
Der Drucker hat keinen abgeschlossen ist, oder der print Auftragsfehlers fortgesetzt wird, wenn der Computer wieder verfügbar ist. Jedoch beim wiederhergestellten Computer Druckerkommunikation neue ist muss Druckaufträge Spoolen und normalerweise ausführen können.

### <a name="deviceimagingprinterbasedevicecapabilities"></a>Device.Imaging.Printer.Base.deviceCapabilities

*Ein Drucker muss ordnungsgemäß die DeviceCapabilities und GetDeviceCaps Anwendungsprogrammierschnittstellen (APIs) basierend auf die Richtlinien in der Windows-Treiberkits unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung verdeutlicht die Verwendung der vorhandenen WLK-Tests. Der Print-Treiber Gerätefunktionen Test bestimmt, ob der Druckertreiber die richtige Informationen für die **DeviceCapabilities** und **GetDeviceCaps** API-Aufrufe zurückgibt.
Weitere Informationen finden Sie unter <http://msdn.microsoft.com/en-us/library/dd183552.aspx> und <http://msdn.microsoft.com/en-us/library/ff566075.aspx>*.*

### <a name="deviceimagingprinterbasedrivercategory"></a>Device.Imaging.Printer.Base.driverCategory

*Version 4-Druckertreiber müssen eine gültige Drucker Kategorie deklariert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Alle V4-Druckertreiber müssen eine gültige DriverCategory in ihr Manifest Treiber deklariert werden. V3 Druckertreiber werden nicht erforderlich, um eine Kategorie zu deklarieren.  Wenn der jeweilige Druckertreiber V3 eine DriverCategory deklariert, muss es gültiger Wert sein.

Die DriverCategory muss einer der folgenden Werte sein:

-   PrintFax.Printer
-   PrintFax.Fax
-   PrintFax.Printer.File
-   PrintFax.Printer.Virtual
-   PrintFax.Printer.Service


### <a name="deviceimagingprinterbasedriverpdc-if-implemented"></a>Device.Imaging.Printer.Base.DriverPDC (sofern implementiert)

INF-Dateien benötigen korrekte Syntax, wenn PWG Raster Rendering Filter enthalten ist

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**:

Alle v4 drucken nutzen Sie die PrintDeviceCapabilities DataFile Treibern Typ muss ihre Datei PrintDeviceCapabilities ordnungsgemäß implementieren. Treiber, wodurch verwendet die standardmäßige Rendering Filter eine PrintDeviceCapabilities DataFile angeben muss, die diese Anforderung entspricht PWG Raster.

### <a name="deviceimagingprinterbasegdlfile"></a>Device.Imaging.Printer.Base.GDLFile

*GDL Dateien müssen in der Windows-Treiberkits gemäß den Richtlinien die richtige Syntax verwenden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung verdeutlicht die Verwendung der vorhandenen WLK-Tests. Den Test mit Richtigkeit generische Description Language (GDL) bestimmt, ob GDL Dateien die richtige Syntax entsprechend der WDK verwenden.
Weitere Informationen finden Sie unter <http://msdn.microsoft.com/en-us/library/ff549787.aspx> *und* <http://msdn.microsoft.com/en-us/library/ff563355.aspx>*.*

### <a name="deviceimagingprinterbaseinffile"></a>Device.Imaging.Printer.Base.infFile

*INF-Dateien müssen die korrekte Syntax gemäß den Richtlinien im Windows-Treiberkits verwenden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung verdeutlicht die Verwendung der vorhandenen WLK-Tests.
INFGate bestimmt, ob INF-Dateien und v4 Manifest die richtige Syntax entsprechend der WDK verwenden.
Version 4-Druckertreiber verwenden Version 4 INF-Dateien und Manifestdateien.
V4-Treiber INF-Datei muss:

-   Definieren einer PrinterDriverID für jeden Treiber INF-Datei angeben, wann Treiber aus Gründen der Druckerfreigabe kompatibel sind.

   -   PrinterDriverID muss eine GUID sein.

-   Festlegen einer Datendatei als GPD oder PPD-Datei.

-   Verwenden Sie nur die folgenden DestinationDirs: DriverStore, 66000; oder das Verzeichnis Farbe, 66003.

-   Geben Sie eine Filter XML-Pipeline-Konfigurationsdatei mit dem Namen \*-Datei pipelineconfig.xml, ODER Geben Sie RequiredClass im Manifest v4-Treiber.

V4-Treiber Manifestdateien müssen:

-   Definieren Sie eine PrinterDriverID für jeden Treiber im Manifest angeben, wann Treiber aus Gründen der Druckerfreigabe kompatibel sind.

   -   PrinterDriverID muss eine GUID sein.

-   Legen Sie eine Datendatei als GPD oder PPD-Datei.

V4-Treiber müssen nicht:

-   Nutzen Sie die folgenden INF-Datei Direktiven ClassInstall32, ClassInstall32.Services, DDInstall.Services, DDInstall.HW, DDInstall.CoInstallers, DDInstall.FactDef, DDInstall.LogConfigOverride, DDInstall.Interfaces, InterfaceInstall32, DefaultInstall, DefaultInstall.Services, AddReg, DelReg, DelFiles, RenFiles, AddService, DelService, AddInterface, BitReg, von LogConfig, "UpdateInis", "UpdateIniFields", oder Ini2Reg.

Version 3 INF-Dateien müssen die richtige Syntax entsprechend der WDK verwenden.
Weitere Informationen zu v3 INF-Dateien finden Sie unter <http://msdn.microsoft.com/en-us/library/ff560902.aspx> *und* <http://msdn.microsoft.com/en-us/library/ff563414.aspx>*.*



### <a name="deviceimagingprinterbaseprintprocessor"></a>Device.Imaging.Printer.Base.printProcessor

*Print Prozessoren müssen basierend auf die Richtlinien in der Windows-Treiberkits implementiert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung verdeutlicht die Verwendung der vorhandenen WLK-Tests. Der drucken-Prozessor-API-Test wird sichergestellt, dass print Prozessoren basierend auf WDK Richtlinien implementiert werden.
Alle print Prozessoren müssen die folgenden Endpunkte unterstützen:

-   OpenPrintProcessor
-   ClosePrintProcessor
-   ControlPrintProcessor
-   EnumPrintProcessorDatatypesW
-   PrintDocumentOnPrintProcessor
-   GetPrintProcessorCapabilities

Weitere Informationen finden Sie unter <http://msdn.microsoft.com/en-us/library/ff566084.aspx>*.*

### <a name="deviceimagingprinterbaseprintregions"></a>Device.Imaging.Printer.Base.printRegions

*Ein Drucker muss genau druckbare Regionen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der Drucker muss möglicherweise Ausgabe für den gesamten Bereich drucken, die in den druckbaren Bereich angezeigt wird, die der Benutzer, in der Windows-Benutzeroberfläche auswählen kann.

*Hinweise zum Entwurf*

Beachten Sie, dass wenn der Drucker ein "rahmenlose" Drucken Feature unterstützt, diese Einschränkung weniger strikt werden möglicherweise um Geräte ermöglichen den Dimensionen des Blatts physische Medien, dessen druckbaren Bereich überschreitet. In diesen Fällen muss der Drucker Ausgabe der Umfang der Dimension Seite drucken können.

In diesem Test gilt für alle Papierformate an, denen der Drucker physisch unterstützt. Wenn der Drucker unterstützt die automatische Skalierung und die Benutzeroberfläche verfügbar macht zusätzliche Papierformate an den Benutzer, der in den Drucker nicht physisch geladen werden kann, muss der Drucker richtigen Seitenverhältnis beim Ändern der Größe beibehalten. In diesem Kontext ist "Automatische Skalierung" jedem Feature in der Hardware oder Treiber, der den Druckauftrag an einen verfügbaren Papierformat ohne Benutzereingriff oder einer Warnung ändert.

Wenn der Drucker Drucken auf einem physischen Datenträger nicht unterstützt, das sich auf ist mindestens 4 "x 4" in den Drucker der Größe von dieser Anforderung ausgenommen.

### <a name="deviceimagingprinterbaseprintticket"></a>Device.Imaging.Printer.Base.printTicket

*Ein Druckertreiber muss PrintTicket/PrintCapabilities unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Print Geräte müssen die Objekte **PrintTicket** und **PrintCapabilities** vollständig unterstützen. Je nach der Implementierung Druckertreiber dies möglicherweise oder ist nicht erforderlich, bestimmte **PrintTicket** oder **PrintCapabilities** Schnittstellen implementieren. Weitere Informationen finden Sie unter der WDK-Dokumentation.

Druckertreiber müssen die öffentlichen Print Schema Elementtypen für jedes Schlüsselwort unterstützen, wenn der Druckertreiber oder Drucker die angegebene Funktionalität enthält. Druckertreiber müssen ebenfalls für jedes Schlüsselwort die öffentlichen Print Schema Elementtypen unterstützen, wenn die entsprechende Funktionalität vorhanden, aber nicht konfigurierbar ist. Die Elementtypen, die der Druckertreiber für jedes Schlüsselwort unterstützen müssen zählen alle diese Features, Optionen, ' ParameterDef ', ParameterRef, -Eigenschaft und ScoredProperty mit die öffentliche Print Schema Definition. Druckertreiber müssen keinen öffentlichen Print Schema Schlüsselwörter zu unterstützen, wenn die Druckertreiber oder Drucker nicht die angegebenen enthalten ist.

Druckertreiber müssen die folgenden grundlegenden Print Schema Elementtypen unterstützen:

-   DocumentCollate
-   JobCopiesAllDocuments
-   JobDuplexAllDocumentsContiguously
-   PageColorManagement
-   PageImageableSize
-   PageMediaSize
-   PageMediaType
-   PageOrientation
-   PageOutputColor
-   PageResolution
-   PageICMRenderingIntent
-   Einer der folgenden: JobInputBin, DocumentInputBin oder PageInputBin

### <a name="deviceimagingprinterbaserendering"></a>Device.Imaging.Printer.Base.rendering

*Ein Drucker muss Druckaufträge ordnungsgemäß gerendert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Diese Anforderung verdeutlicht die Verwendung der folgenden Tests der vorhandenen WLK um sicherzustellen, dass Drucker Druckaufträge ordnungsgemäß gerendert:

-   Pgremlin/Pgremlin2

    Bei diesem Test ergibt zahlreiche Seiten der Ausgabe, die Formen, gradientenfüllungen, alpha Farbverlauf und einige komplexen Schriftarten enthalten. Der Test überprüft Gerät Treiber Interface (DDI) Anrufe, die ein Treiber vornehmen können.

-   WinFX Markup Inhalte Rendern Test

    Der Test WinFX Markup Rendern von Inhalten acht WinFX XAML-Dateien geladen und die Ausgabe auf dem angegebenen Drucker.

-   Foto Print-Test

    Den Test mit Foto drucken Druckt Fotos im Querformat und Hochformat, um Printer-Funktionen.

Weitere Informationen zu Pgremlin finden Sie unter <http://msdn.microsoft.com/en-us/library/ff566081.aspx>*.*
Weitere Informationen zu Pgremlin2 finden Sie unter <http://msdn.microsoft.com/en-us/library/ff566079.aspx>*.*
Weitere Informationen zu den WinFX Markup Content-Rendering-Test finden Sie unter <http://msdn.microsoft.com/en-us/library/ff569275.aspx>*.*
Weitere Informationen zu den Test mit Foto drucken finden Sie unter <http://msdn.microsoft.com/en-us/library/ff565234.aspx>*.*

### <a name="deviceimagingprinterbasetcpmon"></a>Device.Imaging.Printer.Base.TCPMon

*Netzwerkdrucker, die Port 9100 Drucken mit dem Microsoft Standard Port Monitor (TCPMon) unterstützen müssen rich Status für das Gerät bereitstellen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Wenn der Drucker eine Verbindung Network Interface Port verwendet und Port 9100 drucken (unformatierte drucken) mit der Microsoft Standard Port Monitor (TCPmon) unterstützt, muss es Simple Network Management Protocol (SNMP), Host Resource Management Information Base (MIB), und allgemeine Drucker MIB und Drucker Port Monitor MIB 1.0 (IEEE ISTO5107.1 2005) unterstützen, sodass das Betriebssystem rich Status für das Gerät vornehmen können.

<a name="device.imaging.printer.mobile"></a>
## <a name="deviceimagingprintermobile"></a>Device.Imaging.Printer.Mobile

### <a name="deviceimagingprintermobilemobile-if-implemented"></a>Device.Imaging.Printer.Mobile.Mobile (sofern implementiert)

Drucker muss die folgenden Elemente in der Beschreibung, um sicherzustellen, dass ordnungsgemäße Funktionalität implementieren.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**:

<html>
    <ol style="list-style-type: decimal">
        <li>
            <p>Drucker implementieren müssen die &quot;MobilePrint&quot; Kategoriedefinition in ihre WS-Discovery-Nachricht PnP X DeviceCategory-Element.</p>

            <p>Devices which support Windows Mobile Printing must add the &quot;MobilePrinter&quot; category to their WS-Discovery ThisModel response.</p>
            <p>The following table provides additional information about the MobilePrinter category keyword.</p>

            <table>
                <thead>
                    <tr class="header">
                        <th>Constant/Value</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="odd">
                        <td>
                            <p>PNPX_DEVICECATEGORY_PRINTER_MOBILE</p>
                            <p>L&quot;MobilePrinter&quot;</p>
                        </td>
                        <td>
                            <p>MobilePrinter category</p>
                            <p>Keywords: Printer</p>
                        </td>
                    </tr>
                </tbody>
            </table>
        </li>

        <li><p>V4 print drivers that use PrintDeviceCapabilities must ensure that it is correctly defined by including a PrintDeviceCapabilities DataFile.</p></li>

        <li><p>If a v4 print driver includes the PWG Raster standard rendering filter, then a PrintDeviceCapabilities DataFile must be included.</p></li>
    </ol>
</html>


### <a name="deviceimagingprintermobilepdl-if-implemented"></a>Device.Imaging.Printer.Mobile.PDL (sofern implementiert) 

Drucker mit mobilen Druckfunktionen müssen eines der folgenden persönlichen Verteilerlisten unterstützen und die für sie relevanten Anforderungen entsprechen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**PWG-Raster**

Drucker unterstützen PWG Raster müssen PWG Raster Industriestandard entsprechen und die folgenden Anforderungen zu implementieren.

<html>
    <ol style="list-style-type: decimal">
        <li><p>Führen Sie alle Regeln, die in PWG 5102.4 2012 beschrieben.</p></li>
        <li><p>Unterstützende Duplex-Geräte müssen InsertPage Richtlinie unterstützen.</p></li>
        <li><p>Geräte müssen nutzen, alle Farbenformate und Lösungen, die in der Datei PrintDeviceCapabilities bekannt gegeben werden.</p></li>
        <li><p>Geräte müssen alle angekündigt Psk:PageMediaSizes aus der Datei PrintDeviceCapabilities, wenn in der PWG Raster Seitenkopf gemäß Definition Self beschreiben Mediennamen PWG 5101.1 des codiert unterstützen.</p></li>
        <li>
        <p>Geräten müssen eine der folgenden Farbenformate unterstützen.</p>
            <ul>
                <li><p>Srgb_8</p></li>
                <li><p>Cmyk_8</p></li>
                <li><p>Sgray_8</p></li>
            </ul>
        </li>
        <li><p>Geräte unterstützt Print WS-v2. 0 müssen Unterstützung für mindestens eine Psk:PageResolution angeben, die kleiner oder gleich 360 dpi ist.</p></li>
        <li><p>Für mobile-kompatiblen Modus muss Gerät 300 DPI Ausgabe unterstützen.</p></li>
        <li><p>Gerät muss für mobile kompatiblen Modus, Buchstaben akzeptieren oder A4 Formate.</p></li>
    </ol>
    <p><strong>PCLm</strong></p>
    <p>Drucker unterstützen PCLm müssen Industriestandard entsprechen und implementieren Sie die folgenden Anforderungen.</p>
    <ol style="list-style-type: decimal">
        <li><p>Gerät muss die Standardeinstellungen im Abschnitt 4.2.9 der Wi-Fi direkte Drucken technische Spezifikation Services v1. 0 definiert unterstützen:</p>
        <table>
            <thead>
                <tr class="header">
                    <th><strong>Attribut</strong></th>
                    <th><strong>Standardeinstellung</strong></th>
                </tr>
            </thead>
            <tbody>
                <tr class="odd">
                    <td>StripHeight</td>
                    <td>16</td>
                </tr>
                <tr class="even">
                    <td>Medien</td>
                    <td>Buchstabe</td>
                </tr>
                <tr class="odd">
                    <td>Lösung</td>
                    <td>600</td>
                </tr>
                <tr class="even">
                    <td>Duplex</td>
                    <td>Simplex</td>
                </tr>
                <tr class="odd">
                    <td>ColorSpace</td>
                    <td>sRGB</td>
                </tr>
                <tr class="even">
                    <td>Copies</td>
                    <td>1</td>
                </tr>
                <tr class="odd">
                    <td>Fest abschließende Vorgänge</td>
                    <td>Keine</td>
                </tr>
                <tr class="even">
                    <td>Anpassen in Seiten</td>
                    <td>False</td>
                </tr>
                <tr class="odd">
                    <td>Ausrichtung</td>
                    <td>Hochformat</td>
                </tr>
                <tr class="even">
                    <td>PrintQuality</td>
                    <td>Normal</td>
                </tr>
            </tbody>
        </table>
    </li>
    <li><p>Gerät muss Empfang von Inhalt mit 300 dpi unterstützen.</p></li>
    <li><p>Gerät muss Empfang von Inhalt mit Flate Codierung ausführen variabler Länge oder DCTDecode komprimiert unterstützen.</p></li>
    </ol>
    <p><strong>OXPS</strong></p>
    <p>Drucker unterstützen OpenXPS muss Industriestandard entsprechen und implementieren Sie die folgenden Anforderungen.</p>
    <ol style="list-style-type: decimal">
        <li><p>Wenn das Gerät OpenXPS Unterstützung implementiert wird, müssen sie alle Regeln im ECMA-388 beschrieben befolgen.</p></li>
        <li>
            <p>Gerät muss in der folgenden Reihenfolge der Priorität von PrintTickets verarbeiten (die wichtigsten autorisierenden Seiten -&gt; mindestens autorisierende):</p>
            <ol style="list-style-type: lower-alpha">
                <li><p>Seitenebenen-PrintTicket im Dokument eingebettet.</p></li>
                <li><p>Auf Dokumentebene PrintTicket im Dokument eingebettet.</p></li>
                <li><p>CreatePrintJob2 Job-Ebene PrintTicket</p></li>
                <li><p>Job-Ebene PrintTicket im Dokument eingebettet.</p></li>
            </ol>
        </li>
    </ol>
    <p><strong>Microsoft XPS</strong></p>
    <p>Unterstützung für Microsoft XPS Drucker muss dokumentiert Spezifikation entsprechen.</p>
    <ol style="list-style-type: decimal">
        <li><p>Drucker unterstützen Microsoft XPS entsprechen muss, und führen Sie alle Regeln, die in Microsoft XML Paper Specification 1.0 beschrieben</p></li>
    </ol>
</html>

<a name="device.imaging.printer.mobile.wsd20"></a>
## <a name="deviceimagingprintermobilewsd20"></a>Device.Imaging.Printer.Mobile.WSD20

### <a name="deviceimagingprintermobilewsd20pdc-if-implemented"></a>Device.Imaging.Printer.Mobile.WSD20.PDC (sofern implementiert)

Drucker unterstützen PrintDeviceCapabilities (PDC) muss die folgenden Elemente in der Beschreibung unterstützen.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

1.  Drucker unterstützen PrintDeviceCapabilities müssen mit alle Regeln gemäß der Print-Schemaspezifikation v2. 0 als auch das WDK entsprechen.

2.  Verfügbare Features können derzeit nur in einer Datei PrintDeviceCapabilities verfügbar gemacht werden. Drucker müssen ihre derzeit verfügbaren Features, Optionen und Parameter in einer Datei PrintDeviceCapabilities beschreiben.

    Wenn alle Features, Optionen und Parameter je nach Status einer installierbare Option wie Finisher bedingt verfügbar sind, müssen Sie dann diese Elemente nur in der Datei PrintDeviceCapabilities verfügbar gemacht werden Wenn die vorausgesetzte installierbare Option installiert ist.

3.  Alle Optionen im PageMediaSize müssen in PrintDeviceCapabilities Dateien verfügbar gemacht werden. Drucker müssen alle unterstützten Papierformaten mithilfe des Psk:PageMediaSize in eine Datei PrintDeviceCapabilities beschreiben.

4.  Alle Optionen im PageResolution müssen in PrintDeviceCapabilities Dateien verfügbar gemacht werden. Drucker müssen ihre unterstützten Geräte-Lösungen mithilfe der Psk:PageResolution-Funktion in einer Datei PrintDeviceCapabilities beschreiben.

5.  Drucker müssen mindestens eine mit Psk:JobInputBin, Psk:DocumentInputBin oder Psk:PageInputBin Features input Bin beschreiben.

6.  Drucker unterstützen PWG Raster müssen PwgRasterDocumentTypesSupported-Element in der Datei PrintDeviceCapabilities beschreiben die unterstützte Farbenformate enthalten.

7.  Drucker, die das DeviceProcessing-Attribut in einer PrintDeviceCapabilities-Datei angeben, müssen diese Features ohne Interaktion des Hosts unterstützen. Wenn der Drucker gibt an, dass eine Option oder Parameter verarbeitet wird, in der Hardware, die mithilfe der DeviceProcessing = "true"-Attribut es, die Option oder Parameter ohne die Beteiligung des Hosts verarbeiten MUSS.

### <a name="deviceimagingprintermobilewsd20wsd20support-if-implemented"></a>Device.Imaging.Printer.Mobile.WSD20.WSD20support (sofern implementiert)

Drucker unterstützen WS-drucken 2.0 muss die folgenden Anforderungen implementieren.

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

<html>
    <ol style="list-style-type: decimal">
        <li>
            <p>Drucker unterstützen WS-drucken v2. 0 müssen beschreiben und die folgenden MIME-Typen mithilfe einschließlich des Wprt2:PrinterFormats-Elements unter den Drucker Wprt:PrintCapabilities Element unterstützt werden.</p>
            <ul>
                <li>
                    <p>PrintDeviceCapabilities</p>
                    <ul>
                        <li><p>Application/vnd.ms-PrintDeviceCapabilities + xml</p></li>
                    </ul>
                </li>
                <li>
                    <p>PrintJobTicket</p>
                    <ul>
                        <li><p>Application/vnd.ms-PrintSchemaTicket + xml</p></li>
                    </ul>
                </li>
                <li>
                    <p>PrintDeviceResource</p>
                    <ul>
                        <li><p>Application/vnd.ms-Resx + xml</p></li>
                    </ul>
                </li>
            </ul>
        </li>
        <li><p>Drucker unterstützen WS-drucken v2. 0 müssen PrintDeviceCapabilitiesChangeID behandeln. Drucker müssen beschreiben das PrintDeviceCapabilitiesChangeID-Element im Wprt:PrinterConfiguration-Element, und erstellen Sie ein Ereignis, wenn die aktuelle PrintDeviceCapabilitiesChangeID ändert.</p>
            <ul>
                <li><p>Die PrintDeviceCapabilitiesChangeID muss über die Power-Zyklen des Geräts konsistent sein, es sei denn, ändert sich der Status des Druckers (z. B., wird eine Option installierbare hinzugefügt oder entfernt).</p></li>
            </ul>
        </li>
        <li><p>Beschreiben des entsprechenden MIME-Typs im Wprt:PrinterCapabilities Wprt:Format Element muss Drucker unterstützenden WS-Print v2. 0 eines der folgenden persönlichen Verteilerlisten unterstützen.</p>
            <ul>
                <li><p>Anwendung/oxps</p></li>
                <li><p>Application/vnd.ms-xpsdocument</p></li>
                <li><p>Bild/Pwg-raster</p></li>
                <li><p>Anwendung/pclm</p></li>
            </ul>
        </li>

        <li><p>Drucker unterstützen WS-drucken v2. 0 Abruf von Ressourcendateien im folgenden Format mithilfe des Vorgangs GetPrintDeviceResources unterstützen müssen, oder müssen den NoLocalizedResources SOAP-Fehler zurückgegeben.</p>
            <ul>
                <li><p>Application/vnd.ms-Resx + xml</p></li>
            </ul>
        </li>

        <li><p>Des Druckers WS-drucken v2. 0-Implementierung muss alle neuen Vorgänge beschrieben, die in der Spezifikation für WS-drucken v2. 0 unterstützen:</p>
            <ul>
                <li><p>CreatePrintJob2</p></li>
                <li><p>PrepareToPrint</p></li>
                <li><p>GetBidiSchemaExtensions</p></li>
                <li><p>GetPrintDeviceResources</p></li>
                <li><p>GetPrintDeviceCapabilities</p></li>
            </ul>
        </li>

        <li><p>Drucker unterstützen WS-drucken v2. 0 müssen das PrintJobTicket-Element verarbeiten, wenn es in der Anforderung CreatePrintJob2 enthalten ist. Drucker müssen im folgenden Format formatiert PrintJobTickets unterstützen.</p>
            <ul>
                <li><p>Application/vnd.ms-PrintSchemaTicket + xml</p></li>
            </ul>
        </li>

        <li><p>Unterstützung für Windows Mobile Drucker müssen WS-Print v2. 0 in Übereinstimmung mit der Anleitung im WDK implementieren.</p></li>
    </ol>
</html>

<a name="device.imaging.printer.oxps"></a>
##Device.Imaging.Printer.OXPS

### <a name="deviceimagingprinteroxpsoxps"></a>Device.Imaging.Printer.OXPS.OXPS

*V4-Treiber, OpenXPS unterstützen, müssen gemäß den Vorschriften WDK implementiert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Für Windows-10, ein Druckertreiber ordnungsgemäß implementierte Version 4 die XPS-Anforderungen erfüllen.  Der v4-Treiber kann MSXPS oder Open XPS unterstützen.
Print V4-Treiber, OpenXPS, unterstützen, müssen entweder ausschließlich oder im Modus mit XPS, Dual-Format unterstützt die folgenden Anforderungen erfüllen:

-   Treiber Manifest muss entweder angeben "XpsFormat = OpenXPS", "XpsFormat = OpenXPS XPS" oder "XpsFormat XPS, OpenXPS =" im Abschnitt DriverRender.

-   Der erste Filter muss OpenXPS Dokumentformat Wenn beispielsweise von der print Filter Pipeline-Manager bereitgestellt nutzen können.

-   Rendern der Regeln in der ECMA Open XML Paper Specification V müssen alle Filter entsprechen. 1.0 (Ecma 388).

-   Die Regeln für die Verarbeitung von PrintTicket in PrintSchema Spezifikation 1.0 müssen alle Filter entsprechen.

-   Eine Verteilerliste, die das print Zielgerät interpretiert werden kann, muss die v4-Treiber Filterpipeline ergeben.

-   Filter in der Pipeline v4-Treiber, die OpenXPS unterstützen müssen NICHT die folgenden Schritte ausführen:

    <!-- -->

    -   Rufen Sie in der Common Language Runtime (CLR) oder WinFX-Laufzeitkomponenten für Funktionen.

    -   Inhalte der Benutzeroberfläche (UI) anzeigen.

    <!-- -->

-   Treiber unterstützt OpenXPS muss allen anderen Regeln v4 entsprechen.  Dual-Format-Treiber müssen OpenXPS und MSXPS Anforderungen entsprechen und entweder Format erfolgreich zu behandeln.

<a name="device.imaging.printer.usb"></a>
## <a name="deviceimagingprinterusb"></a>Device.Imaging.Printer.USB

### <a name="deviceimagingprinterusbcompatid"></a>Device.Imaging.Printer.USB.CompatID

*Drucker müssen eine kompatible-ID in ihren IEEE1284 Zeichenfolge gemäß den Regeln in das WDK angegebenen implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Drucker müssen eine kompatible ID in ihren IEEE1284 Zeichenfolge für Geräte implementieren, die über USB und mithilfe der Port Monitor MIB WSD eine Verbindung herstellen.
Kompatible ID müssen Folgendes angeben:

-   Name des Herstellers oder Code

-   Beschreibung der Geräte-Klasse

<!-- -->

Empfohlen:

<!-- -->

-   Verteilerliste einschließen

-   alle relevanten Gerät Klasseninformationen

-   Beispiel: Fabrikam\_XPS\_A3\_Laserdruckern

Geräte, die das Windows 7-Logo vor dem 1. Juni 2012 empfangen wurden von dieser Anforderung ausgenommen.
Link zum White Paper kompatibel-ID: <http://msdn.microsoft.com/en-us/windows/hardware/gg463313.aspx>

### <a name="deviceimagingprinterusbjsbidiextender"></a>Device.Imaging.Printer.USB.JSBidiExtender

*USB-JavaScript Bidi Extender werden gemäß den Anweisungen im WDK implementiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

USB-JavaScript Bidi Extender werden gemäß den Anweisungen im WDK implementiert:

-   Sie müssen in dem Paket enthalten sein und darf nicht in einem Unterverzeichnis des Pakets sein.

-   Sie können nur mit Version 4-Druckertreiber enthalten sein.

-   Sie sollten sicher entworfen und Überprüfen von nicht vertrauenswürdigen Daten, die analysiert werden soll.

-   Sie müssen in der v4-Manifestdateien verwiesen werden.

Sie müssen syntaktisch gültige JavaScript, nach der WDK implementierte verwenden.

<a name="device.imaging.printer.wsd"></a>
## <a name="deviceimagingprinterwsd"></a>Device.Imaging.Printer.WSD

### <a name="deviceimagingprinterwsdcompatid"></a>Device.Imaging.Printer.WSD.CompatID

*Drucker müssen eine kompatible-ID in ihren IEEE1284 Zeichenfolge gemäß den Regeln in das WDK angegebenen implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Drucker müssen eine kompatible-ID in ihren IEEE1284 Zeichenfolge für Geräte implementieren, die eine Verbindung über USB und mithilfe der Port Monitor MIB WSD herzustellen.
Kompatible ID müssen Folgendes angeben:

-   Name des Herstellers oder Code

-   Beschreibung der Klasse Gerät

Empfohlen:

-   Verteilerliste einschließen

-   alle relevanten Gerät Klasseninformationen

-   Beispiel: Fabrikam\_XPS\_A3\_Laserdruckern

Lesen Sie [zum Implementieren von kompatibler Kennungen unter Druck Geräte](http://msdn.microsoft.com/en-us/windows/hardware/gg463313.aspx), ein entsprechendes Whitepaper.

<a name="device.imaging.printer.xps"></a>
## <a name="deviceimagingprinterxps"></a>Device.Imaging.Printer.XPS

### <a name="deviceimagingprinterxpsxps"></a>Device.Imaging.Printer.XPS.XPS

*Ein Drucker muss es sich um einen Treiber haben, der die XPSDrv Printer-Treiberarchitektur richtig implementiert.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Der v4-Treiber kann MSXPS oder Open XPS unterstützen.
Print V4-Treiber, MSXPS; unterstützen, müssen ausschließlich oder im Modus mit Open XPS Dual-Format unterstützt die folgenden Anforderungen erfüllen:

-   Treiber Manifest muss entweder angeben "XpsFormat = OpenXPS", "XpsFormat = OpenXPS XPS" oder "XpsFormat XPS, OpenXPS =" im Abschnitt DriverRender.

-   Der erste Filter muss das XPS-Dokumentformat Wenn beispielsweise von der print Filter Pipeline-Manager bereitgestellt nutzen können.

-   Rendern von Regeln in der XML Paper Specification müssen alle Filter entsprechen.

-   Die Regeln für die Verarbeitung von PrintTicket in PrintSchema Spezifikation 1.0 müssen alle Filter entsprechen.

-   Filter-Pipeline für die v4-Treiber muss eine Verteilerliste erstellt, die das Zielgerät print interpretiert werden kann.

-   Filter in der v4-Treiber Pipeline XPS unterstützen müssen die folgenden Aufgaben NICHT:

<!-- -->

    -   Rufen Sie in der Common Language Runtime (CLR) oder WinFX-Laufzeitkomponenten für Funktionen.

    -   Inhalte der Benutzeroberfläche (UI) angezeigt.

<!-- -->

-   XPS-Treiber unterstützt, muss auf allen anderen Regeln v4 entsprechen.  Dual-Format-Treiber müssen OpenXPS und MSXPS Anforderungen entsprechen und entweder Format erfolgreich zu behandeln.

Ein Drucker benötigen einen Treiber, der die XPSDrv Printer-Treiberarchitektur korrekt implementiert. 

Ein Treiber, der die XPSDrv Printer-Treiberarchitektur implementiert muss nicht Folgendes ausführen:

-   Implementieren einer GDI Rendering-Modul.

-   Implementieren eines print Prozessors.

Wenn der Treiber XPSDrv einen Drucker, der das Format XPS-Dokument als Drucker Beschreibungssprache (Verteilerliste) nutzen können unterstützt, sind keine Filter erforderlich. Andernfalls, wenn der Treiber Filter bereitstellt, muss der Treiber die folgenden Anforderungen erfüllen oder:

-   Der erste Filter in der Pipeline XPSDrv Treiber Filter muss das Format XPS-Dokument nutzen.

-   Filter-Pipeline für die XPSDrv-Treiber muss eine Verteilerliste erstellen, die das Zielgerät print interpretiert werden kann.

-   Filter in der Pipeline XPSDrv Treiber Filter müssen folgende Schritte ausführen:

<!-- -->

    -   Das Rendern von Regeln in XML Paper Specification entsprechen.

    -   Die Regeln für die Verarbeitung von PrintTicket in XML Paper Specification entsprechen.

<!-- -->

-   Filter in der Pipeline XPSDrv Treiber Filter müssen nicht die folgenden Schritte ausführen:

<!-- -->

    -   Rufen Sie in der Common Language Runtime (CLR) oder WinFX-Laufzeitkomponenten für Funktionen.

    -   Inhalte der Benutzeroberfläche (UI) angezeigt.

    XPSDrv muss die Objekte PrintTicket und PrintCapabilities vollständig unterstützen. XPSDrv-Treiber müssen auch die folgenden zusätzlichen Schlüsselwörter in der Beschreibung unter der Anforderung PrintTicket unterstützen.

    -   PageScaling

    -   JobDigitalSignatureProcessing

    -   PagePhotoPrintingIntent

    -   PageOutputQuality

    