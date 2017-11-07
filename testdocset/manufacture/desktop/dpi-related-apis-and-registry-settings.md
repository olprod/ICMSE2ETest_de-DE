---
author: Justinha
Description: "DPI-bezogene APIs und Registrierungsschlüssel Einstellungen"
ms.assetid: 23b0e272-a09e-4081-a129-d330b6878d8e
MSHAttr: PreferredLib:/library/windows/hardware
title: "DPI-bezogene APIs und Registrierungsschlüssel Einstellungen"
ms.openlocfilehash: c1ec3558a4217cea24fea244fc44ba55557dad54
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dpi-related-apis-and-registry-settings"></a>DPI-bezogene APIs und Registrierungsschlüssel Einstellungen


Wenn Sie die bereitstellungsanpassungen durchführen müssen, wird in den folgenden Abschnitten die Registrierungsschlüssel und Systemparameter, die für den Zugriff auf Ihre Skripts nach der Installation möglicherweise erläutert.

**In diesem Thema:**

-   [Primäre systemeigene Auflösung](#native)

-   [Primäre Anzeige DPI Skalierungsfaktor](#scale)

-   [Skalierung Modus](#scalingmode)

-   [Skalierung Außerkraftsetzung in Windows 8.1 Skalierung Modus](#override)

-   [Systemweite Skalierungsfaktor in Windows 8 Skalierung Modus](#system)


## <a name="span-idnativespanspan-idnativespanprimary-display-native-resolution"></a><span id="native"></span><span id="NATIVE"></span>Primäre systemeigene Auflösung


*Tabelle 1 Windows 8.1 Skalierung Ebenen*, liefert zwar keine vollständige Informationen in der Windows 8.1 Skalierung für eine Reihe von allgemeinen zeigt. **Systemsteuerung DPI** zeigt die physischen Pixeldichte des Bereichs und der **Skalierung Ebene** des Skalierungsfaktors, der zum Anzeigen verwendet werden.

**Tabelle 1 Windows 8.1 Skalierung Ebenen**

<table>
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Anzeigegröße</th>
<th align="left">Anzeigeauflösung</th>
<th align="left">Horizontal (in Pixel)</th>
<th align="left">Vertikal (in Pixel)</th>
<th align="left">Systemsteuerung DPI</th>
<th align="left">Skalierung Ebene</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>10.6&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>208</p></td>
<td align="left"><p>150 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>10.6&quot;</p></td>
<td align="left"><p>HD</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>148</p></td>
<td align="left"><p>100 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>11.6&quot;</p></td>
<td align="left"><p>WUXGA</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1200</p></td>
<td align="left"><p>195</p></td>
<td align="left"><p>150 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>11.6&quot;</p></td>
<td align="left"><p>HD</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>135</p></td>
<td align="left"><p>100 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>WUXGA</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1200</p></td>
<td align="left"><p>170</p></td>
<td align="left"><p>150 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>QHD</p></td>
<td align="left"><p>2560</p></td>
<td align="left"><p>1440</p></td>
<td align="left"><p>221</p></td>
<td align="left"><p>200 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>HD</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>118</p></td>
<td align="left"><p>100 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>15,4&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>143</p></td>
<td align="left"><p>125 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>15,6&quot;</p></td>
<td align="left"><p>QHD +</p></td>
<td align="left"><p>3200</p></td>
<td align="left"><p>1800</p></td>
<td align="left"><p>235</p></td>
<td align="left"><p>200 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>17&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>130</p></td>
<td align="left"><p>125 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>23"</p></td>
<td align="left"><p>QFHD (4K)</p></td>
<td align="left"><p>3840</p></td>
<td align="left"><p>2160</p></td>
<td align="left"><p>192</p></td>
<td align="left"><p>200 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>24&quot;</p></td>
<td align="left"><p>QHD</p></td>
<td align="left"><p>2560</p></td>
<td align="left"><p>1440</p></td>
<td align="left"><p>122</p></td>
<td align="left"><p>125 %</p></td>
</tr>
</tbody>
</table>

 

Damit diese Informationen für alle Geräte programmgesteuert ermittelt wird, können Sie ein Hilfsprogramm schreiben, die Daten wieder meldet. Die primäre Auflösung wird durch Aufrufen der API- [GetDeviceCaps()-Funktion](http://go.microsoft.com/fwlink/p/?linkid=331144), mit der Hdc für den Desktop und die HORZRES und VERZRES Indizes abgerufen:

``` syntax
// Get desktop dc
desktopDc = GetDC(NULL);
// Get native resolution
horizontalResolution = GetDeviceCaps(desktopDc,HORZRES);
verticalResolution = GetDeviceCaps(desktopDc,VERZRES);
```

Weitere Informationen zu GetDC finden Sie unter [GetDC()-Funktion](http://go.microsoft.com/fwlink/p/?linkid=331145).

## <a name="span-idscalespanspan-idscalespanprimary-display-dpi-scale-factor"></a><span id="scale"></span><span id="SCALE"></span>Primäre Anzeige DPI Skalierungsfaktor


In ähnlicher Weise können Sie die Pixeldichte mithilfe der Indizes LOGPIXELSX und LOGPIXELSY abrufen:

``` syntax
// Get desktop dc
desktopDc = GetDC(NULL);
// Get native resolution
horizontalDPI = GetDeviceCaps(desktopDc,LOGPIXELSX);
verticalDPI = GetDeviceCaps(desktopDc,LOGPIXELSY);
```

Diese Ergebnisse werden in einem Koordinatensystem zurückgegeben wie in *Tabelle 2 DPI horizontal Faktoren*dargestellt in welche 96 100 %, entspricht.

**Tabelle 2 DPI horizontal Faktoren**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">DPI</th>
<th align="left">Skalierungsfaktor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>96</p></td>
<td align="left"><p>100</p></td>
</tr>
<tr class="even">
<td align="left"><p>120</p></td>
<td align="left"><p>125</p></td>
</tr>
<tr class="odd">
<td align="left"><p>144</p></td>
<td align="left"><p>150</p></td>
</tr>
<tr class="even">
<td align="left"><p>192</p></td>
<td align="left"><p>200</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Diese API gibt unterschiedliche Ergebnisse je nach den DPI zur Förderung des Bekanntheitsgrads Modus der Anwendung zurück. Konfigurieren den Modus zur Förderung des Bekanntheitsgrads erfordert das Anwendungsmanifest nachstehend beschriebene XML-CODE hinzufügen:

| DPI zur Förderung des Bekanntheitsgrads Modus | Manifest-Einstellung | Rückgabewert |
| ------------------ | ---------------- | -------------- |
| Keine               | Keine             |  96 für alle angezeigt, unabhängig von der Skalierungsfaktor |
| System-DPI-bewusst      | \<DpiAware > True\</dpiAware > | Der DPI-Wert für den ersten Bildschirm zum Zeitpunkt der Windows-Sitzung wurde gestartet (wenn der Benutzer zuerst an den Windows angemeldet) |
| DPI-bewusst pro Monitor | \<DpiAware > True/PM\</dpiAware > | Der DPI-Wert für den ersten Bildschirm zum Zeitpunkt der Windows-Sitzung wurde gestartet (wenn der Benutzer zuerst an den Windows angemeldet). Um den Wert für DPI der Anzeige zu erhalten, die auf dem sich die Anwendung befindet, verwenden Sie [GetWindowDpi()](https://msdn.microsoft.com/en-us/library/windows/desktop/mt748624.aspx) oder [GetDpiForMonitor()](https://msdn.microsoft.com/en-us/library/windows/desktop/dn280510.aspx) |


Weitere Informationen zu dieser Einstellung manifest finden Sie unter [SetProcessDPIAware-Funktion](http://go.microsoft.com/fwlink/p/?linkid=331146).

## <a name="span-idscalingmodespanspan-idscalingmodespanscaling-mode"></a><span id="scalingmode"></span><span id="SCALINGMODE"></span>Skalierung Modus


Die **Systemsteuerung\\ Darstellung und Anpassung\\anzeigen** -Benutzeroberfläche (UI) enthält ein Kontrollkästchen: **selbst eine Skalierung Ebene für alle meine anzeigen auswählen**, die steuert, ob das System einen einzelnen Skalierungsfaktor auf alle zeigt (wie in Windows 8 und frühere Versionen von Windows wendet) oder anderen Maßstab, die Faktoren von jedem Monitor (Windows 8.1 Standard) die Pixeldichte berücksichtigen. Dieses Kontrollkästchen konfiguriert die **HKCU\\Control Panel\\Desktop\\Win8DpiScaling** in Windows 8.1 Registrierungsschlüssel.

**Tabelle 3 HKCU\\-Systemsteuerung\\Desktop\\Win8DpiScaling Werte**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Wert des Schlüssels</th>
<th align="left">Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0</p></td>
<td align="left"><p>Anderen Maßstab Faktoren für jeden Bildschirm: Windows 8.1 Standard. Inhalte, die von einer Anzeige an eine andere verschoben wird die richtige Größe werden, aber es sind Bitmap-skaliert.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1</p></td>
<td align="left"><p>Zeigt alle dieselbe Skalierungsfaktor angewendet wird: Windows 8 und früheren Windows-Versionen Verhalten. Inhalte, die von einer Anzeige an eine andere verschoben wird möglicherweise die falsche Größe.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idoverridespanspan-idoverridespanscaling-override-in-windows-81-scaling-mode"></a><span id="override"></span><span id="OVERRIDE"></span>Skalierung Außerkraftsetzung in Windows 8.1 Skalierung Modus


Wenn das Kontrollkästchen **selbst auswählen eine Skalierung Ebene für alle meine zeigt** deaktiviert ist und das System im Windows 8.1 Skalierung Modus ausgeführt wird, wird der Benutzer mit einem Schieberegler bereitgestellt, mit denen sie dem aktuellen Skalierungsfaktor aus kleiner auf Mittel, oder größer außer Kraft setzen können. Diese Einstellung wird der **HKCU\\Systemsteuerung\\Desktop\\DesktopDPIOverride** Registrierungsschlüssel.

**Tabelle 4 HKCU\\-Systemsteuerung\\Desktop\\DesktopDPIOverride Werte**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Wert des Schlüssels</th>
<th align="left">Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>&lt;0</p></td>
<td align="left"><p>Jede Anzeige Skalierungsfaktor aus der Standard-reduzieren, indem Sie diesen Wert (beispielsweise, wenn der standardmäßige Skalierung 150 % war,-1 entspricht 125 %,-2 auf 100 %).</p></td>
</tr>
<tr class="even">
<td align="left"><p>0</p></td>
<td align="left"><p>Verwenden Sie den Standardwert für jeden Bildschirm.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0&gt;</p></td>
<td align="left"><p>Erhöhen Sie jeden Faktor für die Anzeige durch diesen Wert (mithilfe der, die im vorherige Beispiel + 1 auf 200 % skalieren entspricht).</p></td>
</tr>
</tbody>
</table>

 

Alle anzeigen Skalierungsfaktor in diesem Modus werden auf einen der folgenden vier Werte werden eingeschränkt: 100 %, 125 %, 150 %, 200 %. Darüber hinaus nach Skalierung angewendet wird, erwarten Applications mindestens 720 effektive Zeilen für die Auflösung (d. h., die physischen vertikale Auflösung der Anzeige geteilt durch den Skalierungsfaktor); Dies kann den Bereich der zulässigen Anzeige Skalierungsfaktor weiter einschränken. *Tabelle 5 Anzeigewerte* zeigt, welche Werte für verschiedene zulässig sind zeigt die Größe:

**Tabelle 5 Anzeigewerte**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Vertikale Linien</th>
<th align="left">Unterstützte Skalierungsfaktor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>&lt;900</p></td>
<td align="left"><p>100 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>&gt;= 900 und &lt;1080</p></td>
<td align="left"><p>100 %, 125 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>&gt;= 1080 und &lt;1440</p></td>
<td align="left"><p>100 %, 125 %, 150 %</p></td>
</tr>
<tr class="even">
<td align="left"><p>&gt;= 1440</p></td>
<td align="left"><p>100 %, 125 %, 150 %, 200 %</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsystemspanspan-idsystemspansystem-wide-scale-factor-in-windows-8-scaling-mode"></a><span id="system"></span><span id="SYSTEM"></span>Systemweite Skalierungsfaktor in Windows 8 Skalierung Modus


Wenn das Kontrollkästchen **selbst eine Skalierung Ebene für alle meine zeigt auswählen** aktiviert ist, kann der Benutzer einen Skalierungsfaktor angeben, der für alle anzeigen, unabhängig von jedem Monitor Pixeldichte gilt. Die benutzerdefinierte Einstellung verwenden, kann der Benutzer andere Werte als 100 %, 125 %, 150 %, 200 %, auswählen, obwohl sie auf den Bereich (100 % - 500 %) beschränkt sind. Diese Einstellung wird der **HKCU\\ControlPanel\\Desktop\\LogPixels** Registrierungsschlüssel.

**Tabelle 6 HKCU\\ControlPanel\\Desktop\\LogPixels Werte**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Wert des Schlüssels</th>
<th align="left">Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>96</p></td>
<td align="left"><p>100 % Skalierung bei jedem anzeigen</p></td>
</tr>
<tr class="even">
<td align="left"><p>120</p></td>
<td align="left"><p>125 % Skalierung bei jedem anzeigen</p></td>
</tr>
<tr class="odd">
<td align="left"><p>144</p></td>
<td align="left"><p>150 % Skalierung bei jedem anzeigen</p></td>
</tr>
<tr class="even">
<td align="left"><p>192</p></td>
<td align="left"><p>Skalierung auf jede Anzeige von 200 %</p></td>
</tr>
<tr class="odd">
<td align="left"><p>&lt;andere&gt;</p></td>
<td align="left"><p>&lt;andere&gt;* 100/96 Skalierung bei jedem anzeigen</p></td>
</tr>
</tbody>
</table>

 
## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Dokumentation zur Anwendungsentwicklung Hochauflösenden](https://msdn.microsoft.com/library/windows/desktop/dd464646.aspx)

[Hochauflösenden Unterstützung für IT-Experten](high-dpi-support-for-it-professionals.md)

 

 






