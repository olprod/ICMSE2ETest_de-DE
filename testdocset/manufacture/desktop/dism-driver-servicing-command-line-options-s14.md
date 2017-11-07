---
author: Justinha
Description: DISM-Treiber (INF) Befehlszeilenoptionen zum Warten
ms.assetid: 39beacf3-7982-477c-93f6-4c6883efd69e
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM-Treiber (INF) Befehlszeilenoptionen zum Warten
ms.openlocfilehash: f1857e018eff1397fee3868c5b9f49770d316e44
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-driver-servicing-inf-command-line-options"></a>DISM-Treiber (INF) Befehlszeilenoptionen zum Warten


Verwenden Sie DISM mit INF-Schreibweise Treiber hinzufügen, entfernen oder ein online oder offline Windows WIM-Treiber aufgelistet. Microsoft Windows Installer oder andere Pakettreibertypen (wie .exe-Dateien) werden nicht unterstützt.

Sie können ein Verzeichnis angeben, in dem die INF-Dateien befinden, oder Sie können auf einen Treiber durch Angeben des Namens der INF-Datei zeigen.

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_ Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Die folgenden Treiberoptionen stehen für ein offline-Abbild.

**DISM.exe/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis* &gt; \[ **/Get-Drivers** | **/Get-DriverInfo** | **/Add-Driver** | **Driver** | **/Export-Driver**\]

Die folgenden Treiberoptionen stehen für ein Betriebssystem ausgeführt wird.

**DISM.exe / Online** \[ **/Get-Drivers** | **/Get-DriverInfo** | **/Export-Driver**\]

Die folgende Tabelle enthält eine Beschreibung der wie jeder Option Wartung Treiber verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option-Argument</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Option: <strong>/Get-Help /?</strong></p></td>
<td align="left"><p>Unmittelbar nach der Treiber – Wartung Befehlszeilenoption verwendet wird, ist Informationen über die Option und den Argumenten angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild angegeben wird.</p>
<p>Beispiele für die:</p>
<p><strong>DISM /image:C:\test\offline/Add-Driver /?</strong></p>
<p><strong>DISM / online/Get-Drivers /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Get-Drivers</strong></p>
<p>Argumente:</p>
<p><strong>/ All</strong></p>
<p><strong>/ Format: {Tabelle | Liste}</strong></p></td>
<td align="left"><p>Zeigt grundlegende Informationen zur Treiberpakete in das Bild online oder offline.</p>
<p>Standardmäßig werden nur ein Drittanbieter-Treiber aufgeführt. Verwenden Sie das <strong>Argument/all</strong> , zum Anzeigen von Informationen zu standardmäßigen und Treiber von Drittanbietern. Verwenden Sie das Argument <strong>Standardausgabeformat</strong> <strong>oder/Format: List</strong> , um die Ausgabe als Tabelle oder einer Liste anzuzeigen.</p>
<p>Wenn Sie auf ein Bild zeigen, können Sie bestimmen, welche Treiber im Bild, zusätzlich zu den Status der Treiber (installiert oder bereitgestellt) sind.</p>
<p>Beispiel:</p>
<p><strong>/ Get DISM-/image:C:\test\offline Drivers</strong></p>
<p><strong>DISM / online/Get-Drivers</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Get-DriverInfo</strong></p>
<p>Argumente:</p>
<p><strong>/ Treiber:</strong>&lt;<em>Installed_INF_FileName</em>&gt;</p>
<p><strong>/ Treiber:</strong>&lt;<em>Pfad_zum_Treiber.inf</em>&gt;</p></td>
<td align="left"><p>Zeigt ausführliche Informationen zu einem bestimmten Treiberpaket.</p>
<p>Sie können zeigen Sie auf einer INF-Datei in das Bild oder eine, die noch nicht installiert ist installiert. Sie können den Namen des den deinstalliert oder der Drittanbieter-Treiber im Geräte-Treiberspeicher angeben. Installierten Treiber von Drittanbietern im Treiberspeicher werden Oem0.inf, Oem1.inf usw. heißen. Dies ist der Name der veröffentlichten genannt.</p>
<p>Sie können mehrere Treiber in der Befehlszeile mithilfe der <strong>Option/Driver</strong> mehrmals angeben.</p>
<p>Beispiel:</p>
<p>Verwenden Sie zuerst die <strong>Option/Get-Drivers</strong> , damit Sie eine INF-Datei identifizieren können. Führen Sie den folgenden Befehl ein:</p>
<p><strong>DISM /image:C:\test\offline /Get-DriverInfo/Driver:&lt;Pfad_zum_Treiber.inf&gt;</strong></p>
<p><strong>DISM / online /Get-DriverInfo /driver:C:\test\drivers\usb\usb.inf</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Add-Driver</strong></p>
<p>Argumente:</p>
<p><strong>/ Treiber:</strong>&lt;<em>Ordner_mit_INF_Datei</em>&gt;</p>
<p><strong>/ Treiber:</strong>&lt;<em>Pfad_zum_Treiber.inf</em>&gt;</p>
<p><strong>/ Recurse</strong></p>
<p><strong>/ ForceUnsigned</strong></p></td>
<td align="left"><p>Ein offline-Windows-Abbild hinzugefügt Drittanbieter-Treiberpakete.</p>
<p>Wenn Sie die <strong>Option/Driver</strong> verwenden, um auf einen Ordner verweisen, werden INF-Dateien, die keine gültigen Treiberpakete werden ignoriert. Diese Dateien werden in der Konsole gemeldet, wenn der Befehl ausgeführt wird, und eine Warnung in der Protokolldatei enthalten ist. Sie erhalten eine Fehlermeldung nicht.</p>
<p>Zeigen Sie auf einen Pfad und der <strong>Option/Recurse</strong> verwenden, werden alle Unterordner nach hinzuzufügenden Treiber abgefragt.</p>
<p>Für Testzwecke können Sie <strong>Option/ForceUnsigned</strong> nicht signierte Treiber hinzuzufügen und die Anforderung, X64-basierte Computer installierten Treiber, eine digitale Signatur benötigen zu überschreiben. Weitere Informationen zu Anforderungen Signieren von Treibern finden Sie unter [Gerätetreibern und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md).</p>
<p>Beispiele für die:</p>
<p><strong>DISM /image:C:\test\offline/Add-Driver /driver:C:\test\drivers\</strong></p>
<p><strong>DISM /image:C:\test\offline/Add-Driver /driver:C:\test\drivers/recurse</strong></p>
<p><strong>DISM /image:C:\test\offline/Add-Driver /driver:C:\test\drivers\mydriver.inf</strong></p>
<p><strong>DISM /image:C:\test\offline/Add-Driver /driver:C:\test\drivers\mydriver.inf Option/ForceUnsigned</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>Driver</strong></p>
<p>Argumente:</p>
<p><strong>/ Treiber:</strong>&lt;<em>Published_name</em>&gt;</p></td>
<td align="left"><p>Drittanbieter-Treiber entfernt aus einem offline-Abbild.</p>
<p>Wenn Drittanbieter-Treiber hinzugefügt werden, werden sie als Oem0.inf, Oem1.inf usw. bezeichnet. Sie müssen angeben, die &lt; <em>veröffentlicht Name</em> &gt; (beispielsweise Oem1.inf) Entfernen des Treibers. Standardtreiber können nicht entfernt werden.</p>
<div class="alert">
<strong>Warnung</strong>  
<p>Entfernen eines wichtigen Treiberpakets kann die offline-Windows-Abbild nicht startbaren tätigen.</p>
</div>
<div>
 
</div>
<p></p>
<p>Sie können mehrere Treiber in der Befehlszeile mithilfe der <strong>Option/Driver</strong> mehrmals angeben.</p>
<p>Beispiele für die:</p>
<p><strong>DISM /image:C:\test\offline Driver /driver:oem1.inf</strong></p>
<p><strong>DISM/Image: C:\test\offline Driver /driver:oem1.inf /driver:oem2.inf</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Export-Driver</strong></p>
<p>Argumente:</p>
<p><strong>/ Ziel:</strong>&lt;<em>Path_to_destination_folder</em>&gt;</p></td>
<td align="left"><p>Allen Treiberpaketen für Drittanbieter-exportiert aus einer Windows-Abbild in einen Zielpfad. Die exportierte Treiber können dann zu einem offline Bild eingefügt werden, mithilfe des Befehls <strong>DISM hinzufügen-Treiber</strong> . Dieser Befehl ist neu in Windows 8.1-Update.</p>
<p>Beispiele für die:</p>
<p><strong>DISM / Online /Destination:C:\destpath Export-Treiber</strong></p>
<p><strong>DISM /Image:C\test\offline Export-Treiber /Destination:C:\destpath</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


-   Der Befehl Wartung Treiber unterstützt nur INF-Dateien. Windows Installer oder andere Treiber-Paket (beispielsweise .exe-Dateien) werden nicht unterstützt.
-   Treiber werden in der Reihenfolge installiert, dass sie in der Befehlszeile aufgelistet sind. Im folgenden Beispiel, 1.inf, 2.inf und 3. wird in der Reihenfolge INF-Datei installiert werden, dass sie in der Befehlszeile aufgeführt sind.

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\test\drivers\1.inf /Driver:C:\test\drivers\2.inf /Driver:C:\test\drivers\3.inf
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






