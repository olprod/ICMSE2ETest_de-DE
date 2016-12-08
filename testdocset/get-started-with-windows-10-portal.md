---
title: Erste Schritte mit Windows 10
description: "Erstellen Sie innovative und differenziert Geräte mit Windows 10."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e9ebd4e2-f05e-40fb-9dc3-925f96dce182
ms.openlocfilehash: ba4410422bbba82efb8ef8fa428a7cee473b3f2e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-started-with-windows-10"></a>Erste Schritte mit Windows 10

Erstellen Sie innovative und differenziert Geräte mit Windows 10. Windows-10 kann auf eine Breite Palette von Geräten ausgeführt werden – von Desktops, Notebooks, Telefone und Geräte Internet Dinge (IoT). Das Betriebssystem common Core funktioniert überhaupt plattformübergreifend mit 80 Zoll-Bildschirme, 4 Zoll-Bildschirme oder Geräte mit keine Bildschirme.

Geräte für die Fingereingabe/Stift, Tastatur oder Maus, Controller/Gestik verwenden können, oder Sie können diese so wechseln Sie zwischen Eingabetypen erstellen.

## <a name="start-here"></a>Beginnen Sie hier

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong><em>Ich bin neu bei dies!</em></strong></td>
<td><strong><em>Ich bin zurück!</em></strong></td>
</tr>
<tr class="even">
<td><p>Informationen Sie zu den verschiedenen Kits zum Erstellen von Windows-Geräten verwendet.</p>
<p>[Machen Sie sich mit den Kits und tools](kits-and-tools-overview.md)</p>
<p>Laden Sie die Kits hier:</p>
<ul>
<li>[Windows-Treiberkits (WDK) 10](https://go.microsoft.com/fwlink/p/?LinkId=733614)</li>
<li>[Windows Hardware Lab-Kit (HLK) für Windows 10](https://go.microsoft.com/fwlink/p/?LinkId=733613)</li>
<li>[Windows Assessment and Deployment Kit (ADK) für Windows 10](https://go.microsoft.com/fwlink/p/?LinkId=733615)</li>
</ul></td>
<td><p>Willkommen zurück! Nachfolgend finden Sie Neuigkeiten:</p>
<ul>
<li>[... Windows 10](what-s-new-in-windows.md)</li>
<li>[... Windows ADK](what-s-new-in-kits-and-tools.md)</li>
<li>[... Windows Performance Toolkit](https://msdn.microsoft.com/en-us/library/windows/hardware/dn927303(v=vs.85).aspx)</li>
<li>[... Hardware Lab-Kit](https://msdn.microsoft.com/library/windows/hardware/mt187880.aspx)</li>
<li>[... Treiberentwicklung](https://msdn.microsoft.com/windows/hardware/drivers/what-s-new-in-driver-development)</li>
<li>[... Design](https://msdn.microsoft.com/library/windows/hardware/mt703371.aspx)</li>
<li>[... Anpassungen](https://msdn.microsoft.com/library/windows/hardware/mt723363(v=vs.85).aspx)</li>
<li>[... manufacturing](manufacture/whats-new-in-windows-manufacturing.md)</li>
<li>[... für die unbeaufsichtigte Installation Einstellungen](https://msdn.microsoft.com/library/windows/hardware/mt750416.aspx)</li>
<li>[... MDM Registrierung und Verwaltung](https://msdn.microsoft.com/library/windows/hardware/mt299056.aspx)</li>
<li>[... Windows PE](manufacture/desktop/whats-new-in-windows-pe-s14.md)</li>
</ul></td>
</tr>
</tbody>
</table>

Sie können die Hardware für Windows 10 in jeder Phase des Entwicklungsprozesses optimieren. Hier erläuterten schrittweise mithilfe bewertungseinrichtungen Entwicklung, Erstellung von universellen Windows Treiber für eine Vielzahl von Geräten und Sicherstellen der Hardwarekomponenten, Peripheriegeräte, und -Technologien sind kompatibel mit Windows 10.

## <a name="design-hardware-with-the-latest-features"></a>Entwerfen von Hardware mit den neuesten features

Aus Cortana, kontinuierliche an die zentrale Architektur sind in dieser Version Tonnen neue Plattformfeatures und Verbesserungen beim ansprechende Benutzeroberfläche auf einem beliebigen Formfaktor erstellen.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Kontinuierliche wechselt in von &quot;Tablet-Modus&quot;, zur Anpassung und Optimierung von apps und die Windows-Shell basierend auf den physischen Formularfaktor und Voreinstellungen des Kunden.</p>
<p>[Erfahren Sie mehr über die kontinuierliche implementieren](https://msdn.microsoft.com/en-us/library/windows/hardware/dn917883(v=vs.85).aspx)</p></td>
<td><p>Cortana, die persönlichen Assistenten Technologie auf Windows Phone 8.1, eingeführt wird nun auf allen Windows-10-Geräten unterstützt. Erfahren Sie Gerät Recommendations, und Testen Sie Setup in diesen Artikeln.</p>
<p>[Erfahren Sie mehr über einschließlich Cortana](https://msdn.microsoft.com/en-us/library/windows/hardware/dn915051(v=vs.85).aspx)</p></td>
<td><p>Windows Hello können Benutzer sicher zu einem Gerät mit einem biometrische Gerät wie ein Fingerabdruckleser oder eine Kamera Infrarot-Anmeldung.</p>
<p>[Erfahren Sie mehr über biometrische Anforderungen für Windows-Hello](https://msdn.microsoft.com/en-us/library/windows/hardware/mt587095(v=vs.85).aspx)</p></td>
</tr>
</tbody>
</table>
 
## <a name="develop-windows-universal-drivers"></a>Entwickeln von universellen Windows-Treiber

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Hier erfahren Sie grundlegende Konzepte zu Treibern.</p>
<p>[Erste Schritte mit Windows-Treiber](https://msdn.microsoft.com/en-us/library/windows/hardware/ff554690(v=vs.85).aspx)</p></td>
<td><p>Erstellen Sie eine universelle Sensor-Treibers basierend auf der Sharks Cove Dev Pinnwand. Hier erfahren Sie, wie Sie ein Windows-10-Bild laden und Bereitstellen dieser bewertungseinrichtungen für die Bereitstellung der Treiber, Debuggen und testen.</p>
<p>[Arbeiten Sie mit der Pinnwand Sharks Cove Hardware-Entwicklung](https://msdn.microsoft.com/en-us/library/windows/hardware/dn745910(v=vs.85).aspx)</p></td>
<td><p>Erstellen Sie einen einzelnen Treiber, der über mehrere verschiedene Gerätetypen von eingebetteten-Systeme und Tablets und Desktop-PCs ausgeführt wird. Vorlagen für UMDF und KMDF sind in Visual Studio, um Ihnen den Einstieg Hilfe enthalten.</p>
<p>[Erste Schritte mit universellen Windows-Treiber](http://go.microsoft.com/fwlink/p/?LinkId=526095)</p></td>
</tr>
</tbody>
</table>

## <a name="customize-windows-images-to-reflect-your-brand"></a>Passen Sie Windows-Abbilder Ihre Marke entsprechend an

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Erstellen Sie provisioning Pakete, die Ihre Einstellungen, die Sprachen, die Treiber zu sammeln und alle gleichzeitig anwenden auf ein neues Gerät mit Windows Imaging und Konfiguration Designer (ICD) können.</p>
<p>OEMs können die Pakete auf neue Geräte anwenden. Unternehmen können auf Geräte angewendet werden, dass ein Mitarbeiter von zu Hause bringen, schnell konfigurieren, um das Unternehmensnetzwerk verwenden.</p>
<p>[Erste Schritte mit Windows ICD](https://msdn.microsoft.com/en-us/library/windows/hardware/dn916112(v=vs.85).aspx)</p></td>
<td><p>Für desktop-PCs können Sie Ihre vorhandenen Einstellungsdatei (Unattend.xml) hinzufügen Einstellungen während der Installation von Windows verwenden.</p>
<p>[Erstellen Sie eine Vorlagedatei für Windows](manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)</p></td>
</tr>
</tbody>
</table>

## <a name="test-system-components-for-compatibility-and-performance"></a>Testen der Systemkomponenten für Kompatibilitäts- und Leistungsprobleme

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Schreiben und Testen der Automatisierung mit Authoring testen und Ausführung Framework (TAEF) ausführen. Freigeben von Tests für mehrere Techniken und Teams.</p>
<p>[Erste Schritte mit der Erstellung von Test und Ausführung Framework (TAEF)](https://msdn.microsoft.com/en-us/library/windows/hardware/hh439627(v=vs.85).aspx)</p></td>
<td><p>Testen Sie Ihre Hardware mit Windows Hardware Lab Kit.</p>
<p>[Erste Schritte mit Windows Hardware Lab-Kit](https://msdn.microsoft.com/en-us/library/windows/hardware/dn915002(v=vs.85).aspx)</p></td>
<td><p>Analysieren von System- und Anwendungsleistung Windows Performance Toolkit verwenden.</p>
<p>[Erste Schritte mit der Leistung von Windows-Leitfäden](https://msdn.microsoft.com/en-us/library/windows/hardware/mt634257(v=vs.85).aspx)</p></td>
</tr>
</tbody>
</table>

## <a name="a-href-idmanufacturing---putting-it-all-togetheramanufacturing-putting-it-all-together"></a><a href="" id="manufacturing---putting-it-all-together"></a>Manufacturing – Fazit

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Hier erfahren Sie Strategien zum Erstellen von Bildern für bestimmte Märkte verschiedene Kunden Anforderungen für desktop-PCs. Wenden Sie klassische und moderne apps für Windows, Treibern, Sprachen und anderen Anpassungen an und mischen Sie und übereinstimmen Sie Ihre Anpassungen, neue Windows-Editionen über automatisierte Skripts oder eine vertraute Oberfläche Windows veröffentlicht werden.</p>
<p>[Erstellen und Bereitstellen von Desktopgeräte](manufacture/desktop/oem-windows-deployment-and-imaging-walkthrough.md)</p></td>
<td><p>IoT Core Geräte, Anwenden von apps, Treibern und Einstellungen auf neue Geräte zu erstellen.</p>
<p>[Erstellen und Bereitstellen von IoT Core-Geräte](manufacture/iot/iot-core-manufacturing-guide.md)</p></td>
<td><p>OEMs und ODMs können erstellen und Testen von mobilen Geräten und Treiber.</p>
<p>[Erstellen und Bereitstellen von Telefonen](manufacture/mobile/mobile-deployment-and-imaging.md)</p></td>
</tr>
</tbody>
</table>

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bwdknodes\wdknodes%5D:%20Get%20started%20with%20Windows%C2%A010%20%20RELEASE:%20%286/20/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")
