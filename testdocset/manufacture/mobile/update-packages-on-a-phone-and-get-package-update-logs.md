---
title: "Update-Pakete auf einem Gerät und rufen Sie Paket Update-Protokolle"
description: "Update-Pakete auf einem Gerät und rufen Sie Update-Paketprotokolle"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d0594281-56f4-4676-9d00-19b6910ab50f
ms.openlocfilehash: 858ca01b53daa83b54379c320ca957cc93f2630f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-packages-on-a-device-and-get-package-update-logs"></a>Update-Pakete auf einem Gerät und rufen Sie Paket Update-Protokolle


Windows Driver Kit (WDK) enthält das Tool zum Aktualisieren der Pakete auf einem Gerät (IUTool.exe) und ein Tool für die erste Paket Update-Protokolle von einem Gerät (GetDULogs.exe). Diese Tools sind verfügbar unter WPDKCONTENTROOT %\\Tools\\Bin\\i386.

## <a name="using-iutoolexe-to-update-packages-on-a-device"></a>Verwenden IUTool.exe zum Pakete auf einem Gerät aktualisieren


IUTool.exe ist ein Befehlszeilentool, das ein vorhandenes Paket auf einem Gerät aktualisieren oder Hinzufügen eines neuen Pakets zu einem Gerät verwendet werden kann. IUTool.exe muss ein Befehlszeilenfenster verwendet werden, die als Administrator geöffnet ist. Die Befehlszeilensyntax zum IUTool.exe ist Folgendes.

``` syntax
IUTool -p <path to packages>
```

In der folgenden Tabelle werden die Befehlszeilenparameter für IUTool.exe beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>-p</strong><em>Pfad zu Paketen</em></p></td>
<td><p>Gibt ein oder mehrere Pakete auf dem Gerät aktualisieren oder das Gerät hinzu. Der <em>Pfad zu Paketen</em> -Parameter kann folgenden Formate aufweisen:</p>
<ul>
<li><p>Geben Sie den vollständigen Pfad zu dem Paket zum Aktualisieren oder Hinzufügen von einem einzelnen Paket bereit, auf dem Entwicklungscomputer installiert.</p></li>
<li><p>Geben Sie zum Aktualisieren oder mehrere Pakete hinzugefügt werden, eine durch Semikolons getrennte Liste der Pakete auf dem Entwicklungscomputer installiert. Beispiel:</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages\Contoso.Device.SampleDriver.spkg;C:\ContosoPackages\Contoso.Device.SampleApplication.spkg</code></pre></li>
<li><p>Zum Aktualisieren oder ein Pakete für das Gesamtes Verzeichnis hinzuzufügen, geben Sie den Pfad zu dem Verzeichnis. Beispiel:</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages</code></pre></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>

 

### <a name="package-versioning"></a>Versionskontrolle für Pakete

Wenn das angegebene Paket bereits auf dem Gerät ist, die neue Version des Pakets müssen eine höhere Version als dem Paket aktuell auf dem Gerät oder das Update schlägt fehl. Verwenden Sie zur Angabe der Version für ein Paket den **Befehlszeilenparameter/Version** für PkgGen.exe beim Generieren des Pakets. Weitere Informationen finden Sie unter [Befehlszeilenargumente für das Paket-Generator](https://msdn.microsoft.com/library/windows/hardware/dn756636).

## <a name="using-getdulogsexe-to-get-package-update-logs-from-a-device"></a>Verwenden GetDULogs.exe zum Paket updateprotokolle von einem Gerät zu erhalten


GetDULogs.exe ist ein Befehlszeilentool, das zum Abrufen von updateprotokolle Paket von einem Gerät verwendet werden kann. GetDULogs.exe muss ein Befehlszeilenfenster verwendet werden, die als Administrator geöffnet ist. Die Befehlszeilensyntax zum GetDULogs.exe ist Folgendes.

``` syntax
GetDULogs -o <output file path>
```

In der folgenden Tabelle werden die Befehlszeilenparameter für GetDULogs.exe beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>-o</strong><em>Ausgabedateipfad</em></p></td>
<td><p>Der vollständige Pfad der Datei auf dem Entwicklungscomputer die Protokollinformationen zu schreiben.</p></td>
</tr>
</tbody>
</table>

 

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Update%20packages%20on%20a%20device%20and%20get%20package%20update%20logs%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")




