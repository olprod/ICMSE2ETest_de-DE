---
author: kpacquer
Description: Definition der MMOS-Bild
ms.assetid: 3b548778-0551-4ca0-9768-725d0f33dfca
MSHAttr: PreferredLib:/library/windows/hardware
title: Definition der MMOS-Bild
ms.openlocfilehash: 5e9b0a5644ca2222abfb365b3f8c167b568dea21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mmos-image-definition"></a>Definition der MMOS-Bild


Dieser Abschnitt enthält eine Anleitung zum Erstellen von Windows 10 Mobile MMOS Bildern. Dieser Prozess ähnelt der Prozess für die Erstellung des primären Betriebssystemabbilds.

## <a name="span-idcreatinganmmosimagespanspan-idcreatinganmmosimagespanspan-idcreatinganmmosimagespancreating-an-mmos-image"></a><span id="Creating_an_MMOS_image"></span><span id="creating_an_mmos_image"></span><span id="CREATING_AN_MMOS_IMAGE"></span>Erstellen ein Bild MMOS


Während dieses Vorgangs erstellte MMOS Image erfordert der Hersteller SoC und zusätzlich zu den von Microsoft bereitgestellten OEM-Pakete. OEM-Pakete, die in die Beispielkonfigurationsdatei MfgOEMInput.xml enthalten sind, werden nur zur Veranschaulichung. OEMs sollten Entfernen dieser Beispiel-Pakete und Ersetzen Sie sie durch ihren eigenen OEM-Pakete. Es ist Aufgabe der OEM, um zu ermitteln, die zum Einschließen in MMOS festgelegt. OEMs können zusätzliche OEM-Pakete mit testanwendungen hinzufügen und Controller usw. testen.

**Wichtige**  
Alle Imaging und Tools zum Packen befinden sich in WPDKCONTENTROOT %\\Tools\\Bin\\i386. In diesem Pfad muss in Ihrer Umgebung Pfad für Tools arbeiten enthalten sein. Sie müssen diese Tools aus ein Befehlszeilenfenster Visual Studio als Administrator mit Zugriff auf MakeCat.exe im Umgebungspfad ausführen.

 

### <a name="span-idcreatingoempackagesspanspan-idcreatingoempackagesspanspan-idcreatingoempackagesspancreating-oem-packages"></a><span id="Creating_OEM_packages"></span><span id="creating_oem_packages"></span><span id="CREATING_OEM_PACKAGES"></span>Erstellen von OEM-Paketen

Hinzufügen von Inhalt zu einem Bild erfolgt, indem Sie Ihre eigenen Pakete zu erstellen. OEM-Pakete können durch Ändern der MfgOEMInput.xml-Datei vor dem Erstellen eines Abbilds mit Windows Imaging und Konfiguration Designer (ICD) ein Bild hinzugefügt werden.

Informationen zum Erstellen von Paketen finden Sie unter [Creating Pakete](https://msdn.microsoft.com/library/dn756642).

### <a name="span-idspecifyingfeaturesinmmosspanspan-idspecifyingfeaturesinmmosspanspan-idspecifyingfeaturesinmmosspanspecifying-features-in-mmos"></a><span id="Specifying_features_in_MMOS"></span><span id="specifying_features_in_mmos"></span><span id="SPECIFYING_FEATURES_IN_MMOS"></span>Angeben von Features in MMOS

Das **Feature** -Element können in der Datei MfgOEMInput.xml Sie optional von Microsoft bereitgestellten Pakete enthalten. Sie können die XML-Eingabedatei zur Unterstützung von verschiedenen Features in MMOS für die Entwicklung, Fertigung, und Dienste benötigt retail ändern.

**Produktion Entwicklung und Debuggen von Umgebung**

Die folgenden Features sind definiert und in der Fertigung Entwicklung und debugging-Umgebung unterstützt. Dieser Umgebung kann zum Erstellen von testanwendungen für die Verwendung in der Produktion verwendet werden.

**Wichtige**  
Die folgenden Features können nur für Test signierte Pakete verwendet werden und nicht in Kunden interessieren WIM-Abbilder einbezogen werden sollen.

 

**Allgemeine features**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_KEYS_TEST</p></td>
<td align="left"><p>Aktiviert ein Startmenü, der gestartet wird, halten Sie die Taste. Verwenden Sie die Volumenlizenzschlüssel navigieren und die Kamera-Taste, um auszuwählen. Dieses Feature ist mit <strong>ENABLE_BOOT_KEYS_RETAIL</strong>gegenseitig aus.</p></td>
</tr>
<tr class="even">
<td align="left"><p>MOBILECOREBOOTSH</p></td>
<td align="left"><p>Aktiviert den Bootsh-Dienst (Bootshscv), damit Features in startup.bsc, wie Telnet und ftp, verwendet werden können.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>LABIMAGE</p></td>
<td align="left"><p>Diese Funktion bewirkt, dass das Gerät den FFU Download-Modus automatisch eingeben, wenn das Gerät gestartet wird. Weitere Informationen finden Sie unter [verwenden die blinkende Tools von Microsoft bereitgestellt](https://msdn.microsoft.com/library/windows/hardware/dn789235).</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGTSHELL</p></td>
<td align="left"><p>TShell in MMOS und Fertigung Modus aktiviert. Wenn Sie dieses verwenden, müssen Sie den TestSirepServer Dienst automatisch in Ihrem Benutzerprofil Manufacturing festlegen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>OPTIMIZED_BOOT</p></td>
<td align="left"><p>Ändert das Verhalten des Startvorgangs OS einige Systemprozesse und die Dienste gestartet, vor dem alle Gerätetreiber gestartet werden. Aktivieren dieses Feature kann sinken, Startzeit kann, aber es auch Regressionen Boot-Verhalten in einigen Szenarien.</p></td>
</tr>
<tr class="even">
<td align="left"><p>BOOTKEYACTIONS_RETAIL</p></td>
<td align="left"><p>Dieses Feature ermöglicht eine Reihe von Aktionen für die Verwendung im Einzelhandel Geräte.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISABLE_FFU_PLAT_ID_CHECK</p></td>
<td align="left"><p>Deaktiviert die Gerät Plattform Überprüfung in die blinkende Microsoft-Anwendung an. Weitere Informationen zu den Checkout-Plattform blinken finden Sie unter [Verwenden der blinkende Tools von Microsoft bereitgestellt](https://msdn.microsoft.com/library/windows/hardware/dn789235).</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Die Gerät Plattform Validierung blinken muss im Einzelhandel Bilder nicht deaktiviert werden.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>PERF_TRACING_TOOLS</p></td>
<td align="left"><p>Tools für die Leistung Analysetypen Tools für das Beenden und Zusammenführen von ETL-Tracing enthält.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_PERF_BASIC_TRACING</p></td>
<td align="left"><p>Starten Sie ermöglicht Leistung Ablaufverfolgungsereignisse generiert werden soll.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ENABLE_BOOT_PERF_CPU_PROFILING_TRACING</p></td>
<td align="left"><p>CPU-Ereignisse auf der Basis was ENABLE_BOOT_PERF_BASIC_TRACING ermöglicht ein Profil erstellen können.</p></td>
</tr>
</tbody>
</table>

 

**Debuggen von features**

Verwenden Sie die folgenden Einstellungen, um das Transportprotokoll angeben, für das debugging verwendet wird. Wenn eine debugging-Funktion nicht angegeben ist, wird das Debuggen nicht in MMOS aktiviert sein.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>KDNETUSB_ON</p></td>
<td align="left"><p>Enthält alle Kernel Debugger Transporten und KDNET über USB ermöglicht.</p></td>
</tr>
<tr class="even">
<td align="left"><p>KDUSB_ON</p></td>
<td align="left"><p>Umfasst alle Kernel-Debugger Transporten und KDUSB ermöglicht.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Schließen Sie KDUSB_ON oder KDNETUSB_ON nicht MTP oder IP über USB im Bild aktivieren möchten. Wenn der Kernel-Debugger im Bild aktiviert ist und die Debuggen Transporten verwendet werden, um auf das Telefon zu verbinden, Kernel-Debugger ist zur exklusiven Verwendung des USB-Ports und verhindert MTP und IP-über USB arbeiten.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>KDSERIAL_ON</p></td>
<td align="left"><p>Enthält alle Kernel Debugger Transporten und KDSERIAL mit den folgenden Einstellungen ermöglicht: 115.200 Baud, 8-Bit, keine Parität.</p></td>
</tr>
<tr class="even">
<td align="left"><p>KD</p></td>
<td align="left"><p>Enthält alle Kernel-Debugger Transporten im Bild Kernel-Debugger wird nicht aktiviert.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGCRASHDUMPSUPPORT</p></td>
<td align="left"><p>Dieses Feature ermöglicht offline Absturz Dump Funktionen mithilfe der Wpcrdmp-Methode für MMOS Bilder. Wenn das Gerät stürzt ab, Wpcrdmp aktiviert und ein Abbild der des Speichers und der SOC Subsysteme auf den Datenträger für eine offline Untersuchung speichert.</p></td>
</tr>
<tr class="even">
<td align="left"><p>MWDBGSRV</p></td>
<td align="left"><p>Dieses Feature fügt die Unterstützung für den Benutzer Modus Debug-Server hinzu.</p></td>
</tr>
</tbody>
</table>

 

Das vorherige DEBUGGERON Feature ist veraltet.

**Andere Features Debuggen**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>Festlegen von Funktionen - die folgenden drei Features Speicherabzugsgröße muss nur mit Bildtypen Test- und Integrität verwendet werden. Diese Funktionen müssen nicht mit Retail Bilder verwendet werden. Nur eine Speicherabzugsgröße Einstellung kann zu einem Zeitpunkt ausgewählt werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DUMPSIZE512MB</p></td>
<td align="left"><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 592 MB. Dies ist für ein Telefon mit 512 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DUMPSIZE1G</p></td>
<td align="left"><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 1104 MB. Dies ist für ein Telefon mit 1024 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DUMPSIZE2G</p></td>
<td align="left"><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 2128 MB. Dies ist für ein Telefon mit 2048 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>Dump Datenspeicherort - die nächsten beiden Settings-Steuerelement, wenn Absturz Sicherungsdaten auf eMMC gespeichert ist oder Absturz Sicherungsdaten auf einer SD-Karte gespeichert ist. Nur eine dieser Einstellungen kann zu einem Zeitpunkt ausgewählt werden. Diese beiden Funktionen müssen nur mit der Test, Integrität und davon Bildtypen verwendet werden. Diese Funktionen müssen nicht mit Retail Bilder verwendet werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEDICATEDDUMPONEMMC</p></td>
<td align="left"><p>Gibt an, dass der Speicherort DedicatedDumpFile als c:\crashdump\dedicateddump.sys.</p>
<div class="alert">
<strong>Hinweis</strong>  Dies kann nicht mit DEDICATEDDUMPONSDCARD verwendet werden.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>DEDICATEDDUMPONSD</p></td>
<td align="left"><p>DEDICATEDDUMPONSD – gibt an, dass der Speicherort DedicatedDumpFile als d:\dedicateddump.sys</p>
<p>Wenn DEDICATEDDUMPONSD verwendet wird, wird Absturzabbild deaktiviert werden, wenn der Benutzer die SD-Karte entfernt oder wenn die Karte nicht vorhanden ist, wenn das Gerät gestartet ist. Um Absturzabbild wieder zu aktivieren:</p>
<ol>
<li><p>Legen Sie diesen Registrierungsschlüssel <code>HKLM\System\CurrentControlSet\Control\CrashControl\CrashDumpEnabled</code> auf den Wert der <code>HKLM\System\CurrentControlSet\Control\CrashControl\ExpectedCrashDumpEnabled</code></p></li>
<li><p>Starten Sie das Gerät neu.</p></li>
</ol>
<div class="alert">
<strong>Hinweis</strong>  Dies kann nicht mit DEDICATEDDUMPONEEMC verwendet werden.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>DBGCHKDISABLE</p></td>
<td align="left"><p>Dieses Feature deaktiviert Debugger Verbindung überprüfen und der Verbindungsstatus Debugger wird ignoriert.</p>
<p>Die Auswirkung auf das Debuggerverhalten unterscheidet sich je nach den SoC, die verwendet wird.</p>
<ul>
<li><p>Enthalten Sie für QC8x26 und QC8974-Geräte DBGCHKDISABLE, um sicherzustellen, dass offline speichert generiert werden, auch wenn das Gerät an einen Debugger verbunden ist. Andernfalls wird ein Dump Offline (Bug Check Code 0x14C Dump) nicht erstellt werden, aber ein unformatierte Dump weiterhin erstellt werden.</p></li>
<li><p>Umfassen Sie für 8960 Geräte DBGCHKDISABLE, um sicherzustellen, dass offline speichert generiert werden, auch wenn das Gerät an einen Debugger verbunden ist. Andernfalls wird ein Dump Offline (d. h. Bug Check Code 0x14C Dump) nicht erstellt werden.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>MSVCRT_DEBUG</p></td>
<td align="left"><p>Dieses Feature fügt die Unterstützung für die explizite Verknüpfung Debug c-Laufzeitbibliothek Bibliotheken einschließlich msvcp120d.dll und msvcr120d.dll im Bild hinzu. Weitere Informationen finden Sie unter in diesem Thema auf MSDN: [CRT-Bibliothek Features](http://msdn.microsoft.com/library/abx4dbyh.aspx).</p></td>
</tr>
<tr class="even">
<td align="left"><p>MWDBGSRV</p></td>
<td align="left"><p>Dieses Feature fügt die Unterstützung für den Benutzer Modus Debug-Server hinzu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>NOLIVEDUMPS</p></td>
<td align="left"><p>Fehlerberichte nicht schwerwiegenden Kernel deaktiviert.  Diese Berichte enthalten Debuginformationen für Entwickler von Betriebssystem und Treiber.</p></td>
</tr>
<tr class="even">
<td align="left"><p>TELEMETRYONSDCARD</p></td>
<td align="left"><p>Dieses Feature ermöglicht die temporäre Speicherung von Debuggen Protokolle und Dateien auf die SD-Karte.  Dieses Feature ist nur in der entsprechenden Test/selbst-Server-Bildern und nur auf Geräten mit weniger als 8 GB freiem Speicherplatz für primären Speicher.</p></td>
</tr>
</tbody>
</table>

 

**Kunden Vorsicht WIM-Bilder**

Die folgenden Features sind in der Produktion Manufacturing in MMOS unterstützt Umgebung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_KEYS_RETAIL</p></td>
<td align="left"><p>Eine Reihe von Schaltflächen auf dem Telefon für die Verwendung im Einzelhandel Gerät aktiviert. Dieses Feature ist mit <strong>ENABLE_BOOT_KEYS_TEST</strong> gegenseitig aus (siehe die vorherige Tabelle).</p></td>
</tr>
<tr class="even">
<td align="left"><p>ENABLE_IP_OVER_USB</p></td>
<td align="left"><p>Ermöglicht die IP über USB.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ENABLE_USB_COMPOSITE</p></td>
<td align="left"><p>Ermöglicht in MMOS Stapel zusammengesetzten USB-Systeme auf einem Chip (SoC) bereitgestellt.</p></td>
</tr>
</tbody>
</table>

 

**Features Dual verwenden**

Diese Features MMOS können mit Test- oder Retail Kunden Vorsicht Bilder verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_MMOS_CHARGING</p></td>
<td align="left"><p>Ermöglicht die Batterie aufgeladen, wenn im MMOS ausgeführt.</p></td>
</tr>
</tbody>
</table>

 

UEFI aufgeladen muss entweder deaktiviert oder aktiviert für MMOS arbeiten. Zu einem Zeitpunkt kann nur eine dieser Optionen festgelegt werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_UEFI_CHARGING</p></td>
<td align="left"><p>Bei Ausführung im UEFI aufgeladen Batterie ermöglicht.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISABLE_UEFI_CHARGING</p></td>
<td align="left"><p>Deaktiviert die Batterie aufgeladen, wenn im UEFI ausgeführt.</p></td>
</tr>
</tbody>
</table>

 

Es sind zusätzliche Features, die in anderen Bildtypen des Betriebssystems definiert sind, die in MMOS nicht unterstützt werden. Diese Liste ist nicht vollständig, aber es enthält Beispiele von Features, die nicht in der Fertigung oder Retail Umgebungen unterstützt werden:

-   TESTINFRASTRUCTURE

-   IMGFAKELED

-   LABIMAGE

-   LOCATIONFRAMEWORKAPP

### <a name="span-idaddingspanspan-idaddingspanspan-idaddingspanconfiguring-the-mmos-mfgoeminputxml-file"></a><span id="Adding"></span><span id="adding"></span><span id="ADDING"></span>Konfigurieren der Datei MMOS MfgOEMInput.xml

1.  Öffnen Sie die mithilfe eines Texteditors MfgOEMInput.xml Beispieldatei. Standardmäßig ist diese Datei % WPDKCONTENTROOT installiert\\OEMInputSamples\\8960Fluid.

2.  Fügen Sie erforderliche MMOS Features hinzu, wie oben beschrieben.

3.  Erforderliche OEM Pakete an der Datei hinzufügen.

4.  Suchen Sie das **Produkt** Element und sicherstellen, dass diese Liste festgelegt ist, "`Manufacturing OS`".

    Optional können Sie die Beschreibung zum Erfassen von Informationen über das Betriebssystemabbild aktualisieren.

    ``` syntax
    <Description>Manufacturing OS generation for ARM.fre</Description>
    <Product>Manufacturing OS</Product>
    ```

5.  Suchen Sie die Elemente **SOC** und **Geräte** , die nach Bedarf ändern.

6.  Hinzufügen von WPDKCONTENTROOT %\\Tools\\Bin\\i386 auf Ihre **Path** -Umgebungsvariablen.

 

 





