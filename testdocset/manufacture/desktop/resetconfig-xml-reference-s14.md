---
author: Justinha
Description: ResetConfig XML (engl.)
ms.assetid: dc9f16c9-d094-49d6-9aaf-3a02c381ccc0
MSHAttr: PreferredLib:/library/windows/hardware
title: ResetConfig XML (engl.)
ms.openlocfilehash: b79d244ebaf6a07bc078e3d87a713cfe228f6214
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resetconfig-xml-reference"></a>ResetConfig XML (engl.)


In dieser Referenz beschreibt alle XML-Elemente, die zum Erstellen der ResetConfig.xml-Datei zum Konfigurieren von Windows Recovery Environment Drucktaste zurücksetzen Features verwendet werden.

## <a name="span-idresetspanspan-idresetspanspan-idresetspanreset"></a><span id="Reset"></span><span id="reset"></span><span id="RESET"></span>Zurücksetzen


Die `Reset` -XML-Element kann die Elemente enthalten: `Run` und `SystemDisk`.

## <a name="span-idresetconfigrunspanspan-idresetconfigrunspanspan-idresetconfigrunspanrun"></a><span id="ResetConfigRun"></span><span id="resetconfigrun"></span><span id="RESETCONFIGRUN"></span>Ausführen


Die `Run` XML-Element wird verwendet, um benutzerdefinierte Skripts auf Drucktaste zurücksetzen Features hinzufügen.

Sie können bis zu vier angeben `Run` Elemente in einer einzigen ResetConfig.xml-Datei. Jedes `Run` -Element muss ein anderes enthalten * \[ExtPoint\] * Wert für die `Phase` Attribut.

Die folgende Tabelle beschreibt die gültigen Elemente, die hinzugefügt werden, können, die `Run` Element:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><code>Run Phase=&quot;[ExtPoint]&quot;&quot;</code></p></td>
<td align="left"><p>Jedes <code>Run</code> -Element definiert das Erweiterbarkeit, zeigen Sie auf verwendet werden, das Skript, die an diesem Erweiterbarkeitspunkt ausgeführt wird, und geschätzte Dauer in Minuten.</p>
<p>Die <code>Phase</code> Attribut ist erforderlich. Es akzeptiert nur die folgenden Werte für <em>[ExtPoint]</em>:</p>
<ul>
<li><p><code>BasicReset_BeforeImageApply</code>. Führt das angegebene Programm bei Erweiterbarkeit Punkt A.</p></li>
<li><p><code>BasicReset_AfterImageApply</code>. Führt das angegebene Programm an Erweiterbarkeit Punkt B</p></li>
<li><p><code>FactoryReset_AfterDiskFormat</code>. Führt das angegebene Programm Erweiterbarkeit Punkt C</p></li>
<li><p><code>FactoryReset_AfterImageApply</code>. Führt das angegebene Programm Erweiterbarkeit Punkt D</p></li>
</ul>
<p>Sie können bis zu vier angeben <code>Run</code> Abschnitte in einer einzelnen ResetConfig.xml-Datei. Jedoch jeder <code>Run</code> Abschnitt muss einen anderen Wert für das Phasenattribut enthalten.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>Path</code></p></td>
<td align="left"><p>Gibt den Speicherort des Skripts für einen bestimmten <code>Run</code> Abschnitt.</p>
<p>Der Pfad muss den relativen Pfad des Skripts aus dem Ordner, der ResetConfig.xml (in der Regel ist dies C:\Recovery\OEM) enthält.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>Duration</code></p></td>
<td align="left"><p>Gibt die geschätzte Zeit in Minuten, die Sie erwarten, dass das benutzerdefinierte Skript ausführen. Bei dieser Schätzung wird verwendet, um Statusinformationen in der Benutzeroberfläche anzuzeigen.</p>
<p>Die Dauer muss eine ganze Zahl sein und muss zwischen 1 und 5.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>Param</code></p></td>
<td align="left"><p>Gibt die Befehlszeilenparameter zu verwenden, wenn Sie die benutzerdefinierten Skript oder eine ausführbare Datei ausführen. Der Wert wird als Zeichenfolge behandelt, und es kann mehrere Parameter enthalten.</p>
<p><code>Param</code> leere Elemente unterstützt nicht. Wenn das Skript nicht Parameter erforderlich sind, klicken Sie dann enthalten Sie nicht dieses Elements. Beispiele finden Sie unter [Verwenden von ResetConfig.xml](#usingresetconfig-xml) weiter unten in diesem Thema.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idresetconfigxmlsysdiskoptionsspanspan-idresetconfigxmlsysdiskoptionsspansystemdisk"></a><span id="resetconfig.xml_sysdisk_options"></span><span id="RESETCONFIG.XML_SYSDISK_OPTIONS"></span>SystemDisk


Die `SystemDisk` Element passt bare-Metal-Recovery-Funktionalität. Weitere Informationen finden Sie unter [Erstellen von Medien zum Ausführen Push-Button zurücksetzen Features](create-media-to-run-push-button-reset-features-s14.md).

Sie können einen angeben `SystemDisk` Abschnitt. Nachfolgend finden Sie die erforderlichen und optionalen Elemente:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><code>MinSize</code>
<p></p></td>
<td align="left"><p>Erforderlich Gibt die erforderliche Mindestgröße für die primäre Festplatte in Megabyte.</p>
<p>Bare-Metal-Recovery wird nicht fortgesetzt werden, wenn der Systemdatenträger dieser Größe Anforderung nicht erfüllt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>DiskpartScriptPath</code></p></td>
<td align="left"><p>Erforderlich. Pfad relativ zur C:\Recovery\OEM Diskpart-Skript. Das Skript sollte wird davon ausgegangen, dass alle vorhandene Partitionen gelöscht wurden, und der Systemdatenträger den Fokus in Diskpart hat.</p>
<p>Wenn die Wiederherstellung Skripts finden Sie unter sind beispielsweise <code>C:\Recovery\OEM\Scripts\RecreatePartitions.dps</code>, verwenden Sie den Wert <code>\Scripts\RecreatePartitions.dps</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>OSPartition</code></p></td>
<td align="left"><p>Erforderlich. Der Partition, die das Betriebssystem wiederhergestellt werden soll. Der ESP oder aktiven Partition muss sich auf demselben Laufwerk wie das Betriebssystem sein.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>RestoreFromIndex</code></p></td>
<td align="left"><p>Optional Der Index des Bilds in der install.wim während bare-Metal-Recovery angewendet werden. Dieses Element ist optional und ist nur erforderlich, auf die vom Hersteller erstellte Wiederherstellungsmedien</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>WindowsREPartition</code></p></td>
<td align="left"><p>Optional Gibt die Partition, in der Windows RE Boot-Abbild installiert ist.</p>
<p>Die <code>WindowsREPartition</code> und <code>WindowsREPath</code> Elemente sind optional, aber sie müssen gemeinsam verwendet werden. Wenn nur eine der folgenden Elemente vorhanden ist, werden die Benutzer kann nicht auf die Festplatte partitionieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>WindowsREPath</code></p></td>
<td align="left"><p>Optional Gibt den Ordnerpfad, in dem das Winre.wim Boot Bild kopiert und mehrstufigen, relativ zum Stammverzeichnis der Partition im angegebenen, an die <code>WindowsREPartition</code> Element.</p>
<p>Die <code>WindowsREPartition</code> und <code>WindowsREPath</code> Elemente sind optional, jedoch müssen sie gemeinsam verwendet werden. Wenn nur eine der folgenden Elemente vorhanden ist, werden Ihre Benutzer kann nicht neu partitionieren der Festplatte gespeichert.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>Compact</code></p></td>
<td align="left"><p>Optional Gibt an, ob das Wiederherstellungsabbild mit aktivierter pro Datei Komprimierung angewendet werden soll. Dieses Element ist optional und ist nur erforderlich, auf Wiederherstellungsmedien Hersteller erstellt.</p>
<p><code>Compact</code> akzeptiert die folgenden Werte:</p>
<ul>
<li><code>True</code>: Dateien aus dem Bild angewendet werden einzeln komprimiert.</li>
<li><code>False</code> (Standardwert): Komprimierung wird nicht verwendet werden.</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><code>RecoveryImagePartition</code></p></td>
<td align="left"><p>Diese Einstellung ist in Windows 10 veraltet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>RecoveryImagePath</code></p></td>
<td align="left"><p>Diese Einstellung ist in Windows 10 veraltet.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>RecoveryImageIndex</code></p></td>
<td align="left"><p>Diese Einstellung ist in Windows 10 veraltet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>WIMBoot</code></p></td>
<td align="left"><p>Diese Einstellung ist in Windows 10 veraltet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idusingresetconfigxmlspanspan-idusingresetconfigxmlspanusing-resetconfigxml"></a><span id="usingresetconfig.xml"></span><span id="USINGRESETCONFIG.XML"></span>Verwenden von ResetConfig.xml


Wenn Sie einen Text-Editor zum Erstellen der XML-Dateien verwenden, müssen Sie speichern Sie das Dokument mit der Erweiterung XML-Datei und UTF-8-Codierung verwenden. Sie müssen nicht die ANSI-Codierung verwenden.

Diese Dateien gespeichert werden sollen, im Ordner C:\\Wiederherstellung\\OEM, und wird durch Drucktaste zurücksetzen Features automatisch erkannt werden.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


Dies ist ein Codebeispiel für die ResetConfig.xml-Datei.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Reset>
 <Run Phase="BasicReset_BeforeImageApply">
   <Path>Fabrikam\CopyFiles.cmd</Path>
   <Duration>2</Duration>
 </Run>
 <Run Phase="BasicReset_AfterImageApply">
   <Path>Fabrikam\InstallDrivers.cmd</Path>
   <Param>/allDrivers</Param>
   <Duration>2</Duration>
 </Run>
 <Run Phase="FactoryReset_AfterDiskFormat">
   <Path>Fabrikam\FixPartitions.exe</Path>
   <Duration>2</Duration>
 </Run>
 <Run Phase="FactoryReset_AfterImageApply">
   <Path>Fabrikam\InstallDrivers.cmd</Path>
   <Param>/allDrivers</Param>
   <Duration>2</Duration>
 </Run>
 <SystemDisk>
   <MinSize>75000</MinSize>
   <DiskpartScriptPath>Fabrikam\CreatePartition.txt </DiskpartScriptPath>
   <OSPartition>4</OSPartition>
   <RestoreFromIndex>2</RestoreFromIndex>
   <WindowsREPartition>1</WindowsREPartition>
   <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
   <Compact>False</Compact>
 </SystemDisk>
</Reset>
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Drucktaste zurücksetzen](push-button-reset-overview.md)

[Erstellen von Medien zum Ausführen der Drucktaste Reset-Features](create-media-to-run-push-button-reset-features-s14.md)

 

 






