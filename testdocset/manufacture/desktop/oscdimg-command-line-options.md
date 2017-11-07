---
author: Justinha
Description: Oscdimg Befehlszeilenoptionen
ms.assetid: 4c64a7fe-3bab-4ab9-97ed-1b14e820b0c8
MSHAttr: PreferredLib:/library/windows/hardware
title: Oscdimg Befehlszeilenoptionen
ms.openlocfilehash: bc4e934f1d027de1e93046f5cfc7cf009ca7a6f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oscdimg-command-line-options"></a>Oscdimg Befehlszeilenoptionen


Oscdimg ist ein Befehlszeilentool, das Sie zum Erstellen einer Bilddatei (ISO) einer angepassten 32-Bit oder 64-Bit-Version von Windows Vorinstallation Environment (Windows PE) verwenden können. Anschließend können Sie die ISO-Datei auf eine CD oder DVD brennen. Oscdimg unterstützt ISO 9660, Joliet und Universal Disk Format (UDF) Datei-Systeme.

In diesem Thema:

-   [Datei Systemoptionen](#file)

-   [CD- oder DVD-Startoptionen](#bootoptions)

-   [Optimierungsoptionen](#optim)

-   [Reihenfolge-Optionen](#order)

-   [DVD-Video und Audio-Optionen](#video)

-   [E-Mail-Optionen](#mess)

-   [Allgemeine Image-Erstellungsoptionen](#general)

-   [Beispiele für](#examples)

## <a name="span-idoscdimgcommand-lineoptionsspanspan-idoscdimgcommand-lineoptionsspanspan-idoscdimgcommand-lineoptionsspanoscdimg-command-line-options"></a><span id="Oscdimg_Command-Line_Options"></span><span id="oscdimg_command-line_options"></span><span id="OSCDIMG_COMMAND-LINE_OPTIONS"></span>Oscdimg Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen stehen für Oscdimg zur Verfügung.

**Oscdimg** \[ * &lt;Optionen&gt; * \] * &lt;SourceLocation&gt; * * &lt;Systems&gt; *

### <a name="span-idfilespanspan-idfilespanfile-system-options"></a><span id="file"></span><span id="FILE"></span>Datei Systemoptionen

Das Tool Oscdimg Microsoft Windows Image mastering API (IMAPI) unterstützt drei Dateiformate und System: ISO 9660, Joliet und UDF.

### <a name="span-idisospanspan-idisospaniso-9660-options"></a><span id="iso"></span><span id="ISO"></span>ISO 9660-Optionen

ISO 9660 Optionen können nicht mit Optionen Joliet oder UDF kombiniert werden. Die Länge des Dateinamens in Kombination mit der Länge von der Dateinamenerweiterung darf 30 Zeichen im ISO 9660 Dateisystem nicht überschreiten.

Die Optionen **– d** und **nt-** können nicht gemeinsam verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>– d</strong></p></td>
<td align="left"><p>Kleinbuchstaben Dateinamen ermöglicht. Erzwingt keine Dateinamen Kleinbuchstaben in Großbuchstaben.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-n</strong></p></td>
<td align="left"><p>Ermöglicht die Dateinamen DOS 8.3-Dateinamen überschreitet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>nt-</strong></p></td>
<td align="left"><p>Ermöglicht die Angabe langer Dateinamen, die mit Windows NT 3.51 kompatibel sind.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idjolietspanspan-idjolietspanjoliet-options"></a><span id="joliet"></span><span id="JOLIET"></span>Joliet-Optionen

Joliet ist eine Erweiterung des Dateisystems ISO 9660. Joliet ermöglicht längere Dateinamen, Unicode-Zeichen und Directory Tiefen größer als acht. Joliet Optionen können nicht mit ISO 9660 Optionen kombiniert werden.

Die **-j2** Joliet Option kann nicht mit UDF Optionen verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-j1</strong></p></td>
<td align="left"><p>Ermöglicht die beiden Dateisystemen So zeigen Sie alle Daten auf dem Datenträger an. Mit dieser Option werden alle Dateien auf das Bild nicht verdoppelt. Diese Option codiert Joliet Unicode-Dateinamen und generiert DOS-kompatible 8.3-Dateinamen im ISO-9660-Namespace. Diese Dateinamen können von Joliet-Systemen oder herkömmlichen ISO-9660-Systemen gelesen werden. Oscdimg kann jedoch einige der Dateinamen im ISO-9660-Namespace zur Einhaltung von DOS 8.3 und ISO 9660 Beschränkungen bei der Benennung ändern.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-j2</strong></p></td>
<td align="left"><p>Codiert Joliet Unicode-Dateinamen ohne standardmäßige ISO-9660-Namen. Diese Option wird verwendet, um ein Bild zu erstellen, die im Dateisystem Joliet enthält.  Für alle Systeme, die nicht gelesen Joliet kann erhält nur eine Standard-Textdatei, die dem Benutzer benachrichtigt, dass dieses Bild, nur auf Computern zur Verfügung Joliet unterstützt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Js-</strong></p></td>
<td align="left"><p>Überschreibt die standardmäßige Textdatei, die verwendet wird, wenn der Benutzer gibt an, die <strong>-j2</strong> Option. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-jsC:\readme.txt</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idudfspanspan-idudfspanudf-options"></a><span id="udf"></span><span id="UDF"></span>UDF-Optionen

UDF-Optionen können nicht mit ISO 9660 Optionen kombiniert werden. Die **- Ue**, **-Uf**, und **-uns** Optionen gelten nur, wenn sie zusammen mit verwendet werden die **-u2** Option.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-u1</strong></p></td>
<td align="left"><p>Erzeugt ein Bild, das die UDF-Dateisystem und das Dateisystem ISO 9660 hat. ISO 9660 Dateisystem wird mithilfe von DOS-kompatible 8.3-Dateinamen geschrieben. Das UDF-Dateisystem wird mit Unicode-Dateinamen geschrieben.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-u2</strong></p></td>
<td align="left"><p>Erzeugt ein Bild, das nur das UDF-Dateisystem enthält. Für alle Systeme, die UDF lesen kann nicht erhält nur eine Standard-Textdatei, die dem Benutzer informiert, dass dieses Bild, nur auf Computern verfügbar ist, die UDF zu unterstützen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-udfver102</strong></p></td>
<td align="left"><p>Gibt die UDF-Dateisystem Version 1.02 an.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-ue</strong></p></td>
<td align="left"><p>Eingebettete Dateien erstellt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-uf</strong></p></td>
<td align="left"><p>UDF-Datei Bezeichner Einträge einbettet.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-der</strong></p></td>
<td align="left"><p>Überschreibt die standardmäßige Textdatei, die zusammen mit verwendet wird die <strong>-u2</strong> Option. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-urC:\Readme.txt</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-uns</strong></p></td>
<td align="left"><p>Erstellt wenige Dateien, wenn verfügbar, um die Speicherplatzverwendung effizienter werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yl</strong></p></td>
<td align="left"><p>Lange Zuweisung Deskriptoren anstelle von kurzen Zuweisung Deskriptoren gibt.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idbootoptionsspanspan-idbootoptionsspanspan-idbootoptionsspancd-or-dvd-boot-options"></a><span id="bootOptions"></span><span id="bootoptions"></span><span id="BOOTOPTIONS"></span>CD- oder DVD-Startoptionen

Startoptionen können verwendet werden, um startbaren CD- oder DVD-Bilder zu erstellen. Die folgenden Startoptionen können verwendet werden, Single-Boot Einträge generiert. Weitere Informationen finden Sie unter [Verwendung einer einzigen Boot-Eintrag zum Erstellen eines startbaren Abbilds](#example-singleboot).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ b</strong><em>&lt;BootSectorFile&gt;</em></p></td>
<td align="left"><p>Gibt die El Torito Sektor Startdatei, die in der Boot-Sektor oder Bereiche des Datenträgers geschrieben werden soll. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<p>Klicken Sie auf UEFI: <code>-bC:\winpe_x86\Efisys.bin</code></p>
<p>Klicken Sie auf BIOS: <code>-bC:\winpe_x86\Etfsboot.com</code></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>– e</strong></p></td>
<td align="left"><p>Diskette Emulation im Katalog El Torito deaktiviert.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-p</strong></p></td>
<td align="left"><p>Gibt den Wert für die Plattform-ID im El Torito-Katalog verwendet. Die Standard-ID ist 0xEF zur Darstellung von einem System Unified Extensible Firmware Interface (UEFI). 0 x 00 stellt ein BIOS-System.</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;sourceLocation&gt;</em></p></td>
<td align="left"><p>Erforderlich. Gibt den Speicherort der Dateien, die in ein ISO-Abbild erstellt werden soll.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;Zieldatei&gt;</em></p></td>
<td align="left"><p>Gibt den Namen der ISO Bilddatei an.</p></td>
</tr>
</tbody>
</table>

 

**Wichtige**  
Single-Boot und mit mehreren Boot-Einträge können nicht in demselben Befehl kombiniert werden.

 

Die folgenden Startoptionen können verwendet werden, um mit mehreren Start Einträge zu generieren. Weitere Informationen finden Sie unter [Verwendung mit mehreren Start Einträge zum Erstellen einer Bilddatei](#examples-multi-boot).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>b</strong><em>&lt;BootSectorFile&gt;</em></p></td>
<td align="left"><p>Gibt die El Torito Sektor Startdatei, die in der Boot-Sektor oder Bereiche des Datenträgers geschrieben werden soll. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<p>Klicken Sie auf UEFI: <code>bEfisys.bin</code></p>
<p>Klicken Sie auf BIOS: <code>bEtfsboot.com</code></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-Bootdata:</strong><em>&lt;Anzahl&gt;</em></p></td>
<td align="left"><p>Gibt ein Multi-Boot-Bild, gefolgt von der Anzahl der Einträge Boot. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-bootdata:&lt;3&gt;#&lt;defaultBootEntry&gt;#&lt;bootEntry1&gt;#&lt;bootEntryN&gt;</code></pre>
<p>wobei <em> &lt;3&gt; </em> ist die Anzahl der Boot-Einträge, die folgen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>e</strong></p></td>
<td align="left"><p>Diskette Emulation im Katalog El Torito deaktiviert.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>p</strong></p></td>
<td align="left"><p>Gibt den Wert für die Plattform-ID im El Torito-Katalog verwendet. Die Standard-ID ist 0xEF ein UEFI System darstellen. 0 x 00 stellt ein BIOS-System.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>t</strong></p></td>
<td align="left"><p>Gibt das El Torito Load-Segment an. Wenn nicht angegeben, ist diese Option standardmäßig 0x7C0.</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;sourceLocation&gt;</em></p></td>
<td align="left"><p>Erforderlich. Gibt den Speicherort der Dateien, die in ein ISO-Abbild erstellt werden soll.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;Zieldatei&gt;</em></p></td>
<td align="left"><p>Gibt den Namen der ISO Bilddatei an.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idoptimspanspan-idoptimspanoptimization-options"></a><span id="optim"></span><span id="OPTIM"></span>Optimierungsoptionen

Optimierungsoptionen können zu Speicher optimieren, indem Sie Codieren von doppelten Dateien nur einmal verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-o</strong></p></td>
<td align="left"><p>Verwendet einen Hashalgorithmus MD5 Dateien vergleichen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-oc</strong></p></td>
<td align="left"><p>Verwendet einen binären Vergleich jeder Datei, und ist langsamer als die Option <strong>-o</strong> .</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-oi</strong></p></td>
<td align="left"><p>Zeitstempel der Diamond-Komprimierung ignoriert, beim Vergleichen von Dateien.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idorderspanspan-idorderspanorder-options"></a><span id="order"></span><span id="ORDER"></span>Reihenfolge-Optionen

Reihenfolge-Optionen wird die Reihenfolge der Datei auf dem Datenträger angegeben. Die Reihenfolge der Datei hat keinen so Listen Sie alle Dateien. Alle Dateien, die nicht in dieser Datei erscheinen werden wie normalerweise wäre sortiert (d. h., wenn die Sortierung Datei nicht vorhanden war). Weitere Informationen finden Sie unter [Angeben der Startreihenfolge](#example-bootorder).

Die **-yo** Option hat Vorrang vor den **-y5** Option.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-y5</strong></p></td>
<td align="left"><p>Gibt die Dateilayout auf dem Datenträger an. Diese Option schreibt alle Dateien in ein Verzeichnis i386 erste und in umgekehrter Sortierreihenfolge.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yo</strong>&lt;bootOrder.txt&gt;</p></td>
<td align="left"><p>Gibt eine Textdatei mit einem Layout für die Dateien in das Bild gestellt werden. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-yoC:\temp\bootOrder.txt</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idvideospanspan-idvideospandvd-video-and-audio-options"></a><span id="video"></span><span id="VIDEO"></span>DVD-Video und Audio-Optionen

Die DVD Video- und Datenträger Erstellungsoptionen können nicht mit Optionen ISO 9660, Joliet oder UDF kombiniert werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-Ausschneiden</strong></p></td>
<td align="left"><p>Schneidet den Abschnitt ISO 9660 des Bilds während der Erstellung der DVD-video und audio Datenträger ab. Wenn diese Option verwendet wird, werden nur die VIDEO_TS AUDIO_TS und JACKET_P Verzeichnisse im Dateisystem ISO 9660 angezeigt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-uv</strong></p></td>
<td align="left"><p>Gibt die Kompatibilität der UDF während der Erstellung der DVD-video und audio Datenträger an. Während der Erstellung werden UDF 1.02 und ISO 9660 auf den Datenträger geschrieben. Alle Dateien in den Verzeichnissen VIDEO_TS AUDIO_TS und JACKET_P werden zuerst geschrieben. Diese Verzeichnisse haben Vorrang vor allen anderen Reihenfolge Regeln, die für dieses Bild verwendet werden.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idmessspanspan-idmessspanmessaging-options"></a><span id="mess"></span><span id="MESS"></span>E-Mail-Optionen

E-Mail-Optionen anpassen, wie Dateien und Verzeichnisse Informationen angezeigt wird.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-eine</strong></p></td>
<td align="left"><p>Zeigt die Verteilung Zusammenfassung für Dateien und Verzeichnisse.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-Betriebssystem</strong></p></td>
<td align="left"><p>Werden doppelte Dateien angezeigt, wenn das Bild wird erstellt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-w1</strong></p></td>
<td align="left"><p>Gibt alle Dateinamen oder Verzeichnisse, die nicht ISO- oder Joliet-kompatibel sind.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-w2</strong></p></td>
<td align="left"><p>Zeigt alle Dateinamen, die nicht DOS kompatibel sind.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-w3</strong></p></td>
<td align="left"><p>Gibt alle Dateien der Länge Null.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-w4</strong></p></td>
<td align="left"><p>Gibt den Namen der Dateien, der auf das Bild kopiert werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-yd</strong></p></td>
<td align="left"><p>Unterdrückt Warnungen für nicht identische Dateien, die gleichen ersten 64.000 Bytes aufweisen.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idgeneralspanspan-idgeneralspangeneral-image-creation-options"></a><span id="general"></span><span id="GENERAL"></span>Allgemeine Image-Erstellungsoptionen

Allgemeine Image-Erstellungsoptionen können zusammen mit einer einzigen Betriebssystem Eintrag oder mit mehreren Boot-Eintrag Optionen zum Erstellen von startbaren CD- oder DVD-Bilder verwendet werden. Weitere Informationen finden Sie unter [Startoptionen](#bootoptions) und [Beispiele](#examples).

Die Optionen **-m** und **Maxsize-** können nicht gemeinsam verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>-c</strong></p></td>
<td align="left"><p>Gibt an, dass das System ANSI-Dateinamen anstelle von OEM-Dateinamen verwendet werden muss.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-g</strong></p></td>
<td align="left"><p>Codiert Zeitwerte als koordinierte Weltzeit (UCT) für alle Dateien, anstatt die Ortszeit.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-h</strong></p></td>
<td align="left"><p>Enthält alle Dateien und Verzeichnisse im Quellpfad des Bilds.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-k</strong></p></td>
<td align="left"><p>Erstellt ein Bild, selbst wenn einige der Quelldateien nicht geöffnet werden kann.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-l</strong><em>&lt;%VolumeLabel&gt;</em></p></td>
<td align="left"><p>Gibt die Volumebezeichnung an. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-l&lt;volumeLabel&gt;</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-m</strong></p></td>
<td align="left"><p>Ignoriert die maximal zulässige Größe eines Bildes.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Maxsize-:</strong><em>&lt;Grenzwert&gt;</em></p></td>
<td align="left"><p>Überschreibt die standardmäßige maximale Größe eines Bildes. Der Standardwert ist eine 74-Minuten-CD. UDF verwendet wird, ist die Standardeinstellung jedoch keine maximale Dateigröße. Verwenden Sie keine Leerzeichen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-maxsize:&lt;4096&gt;</code></pre>
<p>wobei <em> &lt;4096&gt; </em> das Bild auf 4096 MB beschränkt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Q-</strong></p></td>
<td align="left"><p>Nur die Quelldateien überprüft. Diese Option wird ein Bild nicht erstellt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>R-</strong></p></td>
<td align="left"><p>Neue Features für Windows 8. Symbolische Links in ihren Zielspeicherort aufgelöst wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>d -</strong><em>&lt;mm/tt/jjjj hh: mm:&gt;</em></p></td>
<td align="left"><p>Gibt den Zeitstempel für alle Dateien und Verzeichnisse. Verwenden Sie keine Leerzeichen. Sie können eine beliebige Trennzeichen zwischen den Elementen verwenden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>-t12/31/2000,15:01:00</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-y6</strong></p></td>
<td align="left"><p>Gibt an, dass Directory Datensätze am Ende des Bereiche genau ausgerichtet werden müssen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yw</strong></p></td>
<td align="left"><p>Source-Dateien mit Schreibzugriff Freigabe öffnet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idexamplesspanspan-idexamplesspanexamples"></a><span id="examples"></span><span id="EXAMPLES"></span>Beispiele für


Diese Beispiele veranschaulichen, wie die folgenden Aufgaben ausführen:

-   Erstellen Sie eine startbare CD oder DVD für einen UEFI-basierten Computer mithilfe eines einzigen Betriebssystem-Eintrags.

-   Erstellen Sie ein startbaren CD- oder DVD für einen UEFI-basierten oder BIOS-basierten Computer mithilfe eines Multi-Boot-Eintrags.

-   Geben Sie die Datei Startreihenfolge auf einem Datenträger.

### <a name="span-idexamplesinglebootspanspan-idexamplesinglebootspanuse-a-single-boot-entry-to-create-a-bootable-image"></a><span id="example_singleboot"></span><span id="EXAMPLE_SINGLEBOOT"></span>Verwenden Sie einen einzigen Betriebssystem Eintrag zum Erstellen eines startbaren Abbilds

Das Tool Oscdimg können Sie eine startbare CD oder DVD mit einem einzigen Betriebssystem-Eintrag erstellen.

**Verwenden Sie einen einzigen Betriebssystem-Eintrag**

-   Erstellen einer Bilddatei für einen UEFI-basierten Computer. Beispiel:

    ``` syntax
    Oscdimg -bC:\winpe_amd64\Efisys.bin -pEF -u1 -udfver102 C:\winpe_amd64\media C:\winpe_amd64\winpeamd64.iso
    ```

    wobei C:\\Windows PE\_amd64\\Media ist der Speicherort der Quelldateien und C:\\Windows PE\_amd64\\winpeamd64.iso ist der Pfad des die ISO-Datei.

### <a name="span-idexamplesmulti-bootspanspan-idexamplesmulti-bootspanuse-multi-boot-entries-to-create-a-bootable-image"></a><span id="examples_multi-boot"></span><span id="EXAMPLES_MULTI-BOOT"></span>Verwenden Sie zum Erstellen eines startbaren Abbilds mit mehreren Start Einträge

Das Tool Oscdimg können Sie eine startbare CD oder DVD mithilfe von Multi-Boot-Einträge erstellen. Wenn Sie dies tun, beachten Sie Folgendes:

-   Die Anzahl der Einträge in den Befehl Boot muss die Option **Bootdata** folgen (**- Bootdata:***&lt;Anzahl&gt;*).

-   Jeder Eintrag Multi-Boot muss mithilfe eines Symbols Hash begrenzt werden (\#).

-   Jede Option für einen Eintrag Boot muss mit einem Komma (,) begrenzt werden.

-   Jeder Eintrag Boot muss die Plattform-ID angeben.

**Multi-Boot-Einträge verwenden**

-   Erstellen einer Bilddatei für entweder einen UEFI-basierten oder BIOS-basierten Computer mit einem Multi-Boot-Befehl. Beispiel:

    ``` syntax
    Oscdimg -bootdata:2#p0,e,bEtfsboot.com#pEF,e,bEfisys.bin -u1 
    -udfver102 C:\winpe_amd64\media C:\winpe_amd64\winpeamd64.iso
    ```

    wobei dieser Befehl startet die Startdatei Etfsboot.com für ein Bild BIOS und startet dann die Startdatei Efisys.bin für ein Bild UEFI.

### <a name="span-idexamplebootorderspanspan-idexamplebootorderspanspecify-the-boot-order"></a><span id="example_bootorder"></span><span id="EXAMPLE_BOOTORDER"></span>Geben Sie die Startreihenfolge

Für Bilder, die größer als 4,5 GB müssen Sie eine Datei für die Startreihenfolge dafür sorgen, dass Startdateien am Anfang des Bilds gespeichert sind erstellen.

Die Regeln für die Sortierung Datei lauten folgendermaßen:

-   Die Reihenfolge-Datei muss in ANSI sein.

-   Die Reihenfolge-Datei muss in einer neuen Zeile enden.

-   Die Reihenfolge-Datei muss eine Datei pro Zeile enthalten.

-   Jede Datei muss relativ zum Stammverzeichnis des Bilds angegeben werden.

-   Jede Datei muss als einen langen Dateinamen angegeben werden. Keine kurzen Namen sind zulässig.

-   Jeder Dateipfad darf nicht länger als MAX\_PFAD. Dies umfasst den Namen des Volumes.

Beispielsweise D:\\CDAbbild würde folgendermaßen aussehen (wobei D ist der Laufwerkbuchstabe des DVD-Laufwerk):

-   D:\\CDAbbild\\1\\1. Txt

-   D:\\CDAbbild\\2\\2.Klicken Txt

-   D:\\CDAbbild\\3\\3. Txt

-   D:\\CDAbbild\\3\\3\_5. Txt

-   D:\\CDAbbild\\*&lt;LongFileName&gt;*.txt

**Erstellen Sie eine Datei für die Startreihenfolge**

-   Erstellen Sie eine Datei für die Startreihenfolge. Beispiel:

    ``` syntax
    Oscdimg -m -n -yoC:\temp\bootOrder.txt 
    -bC:\winpe_amd64\Efisys.bin C:\winpe_amd64\winpeamd64.iso
    ```

    BootOrder.txt enthält, in der folgenden Liste der Dateien:

    ``` syntax
    boot\bcd
    boot\boot.sdi
    boot\bootfix.bin
    boot\bootsect.exe
    boot\etfsboot.com
    boot\memtest.efi
    boot\memtest.exe
    boot\en-us\bootsect.exe.mui
    boot\fonts\chs_boot.ttf
    boot\fonts\cht_boot.ttf
    boot\fonts\jpn_boot.ttf
    boot\fonts\kor_boot.ttf
    boot\fonts\wgl4_boot.ttf
    sources\boot.wim
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Referenz zu Windows-Bereitstellung Befehlszeilentools](windows-deployment-command-line-tools-reference.md)

 

 






