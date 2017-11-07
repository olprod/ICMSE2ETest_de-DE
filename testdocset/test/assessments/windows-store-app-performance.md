---
title: Windows Store-app-Leistung
description: Windows Store-app-Leistung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dfd6d400-fd14-4fbb-b75f-657b4a213026
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 5cdd93b75be954b6d8d1e8e2f6f4d0ffadf8e989
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-store-app-performance"></a>Windows Store-app-Leistung


Das Windows Store-app Performance Assessment helfen Ihnen Ihre app für eine Steigerung der Kundenzufriedenheit zu optimieren. Die Bewertung misst wie schnell die app wird geöffnet, und hält, und die Größe der Ressourcen auf dem PC verwendet. Können diese Bewertung unterstützen sollen, eine einzelne app zu verbessern oder zur Optimierung von einem Windows-Abbild Berechnung schnelles und flüssiges Zusammenspiel apps, die auch auf Ihrem PC ausgeführt.

In diesem Thema:

-   [Bevor Sie beginnen](#bkmk-begin)

-   [Einstellungen](#bkmk-settings)

Weitere Informationen zu Ergebnisse und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für die Windows Store-App-Performance-Bewertung](results-for-the-windows-store-app-performance-assessment.md).

## <a name="a-href-idbkmk-beginabefore-you-begin"></a><a href="" id="bkmk-begin"></a>Bevor Sie beginnen


**Warnung**  
Der ersten Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

 

**Warnung**  
Führen Sie diese Bewertung nur während der Desktop im Vollbildmodus ist. Diese Bewertung kann nicht ausgeführt werden, wenn Sie eine andere Windows Store-app geöffnet-nebeneinander mit dem Desktop haben.

 

**Hinweis**  
Das Windows Store-app Performance Assessment enthält nur Ergebnisse für Windows Store-apps auf dem PC, ist es nicht desktopanwendungen bewerten.

 

Die besten Ergebnisse zu erzielen:

-   Beenden Sie alle geöffneten desktopanwendungen.

-   Führen Sie alle Aufgaben ersten Ausführung auf apps, den, die Sie bewerten möchten. Beispielsweise erfordern einige apps ein Benutzerkonto Benutzerakzeptanz einen Lizenzvertrag oder Benutzeroberflächeneinstellungen erstmalig die app ausgeführt wird.

-   Stellen Sie sicher, dass alle apps auf dem neuesten Stand sind. Öffnen Sie den Windows Store zu prüfen, ob alle ausstehenden Aktualisierungen auf apps auf Ihrem PC installiert.

-   Interagieren Sie sich nicht mit dem PC, während die Bewertung ausgeführt wird.

-   Stellen Sie sicher, dass Ngen.exe für die jeweilige app vor der ersten Ausführung der Bewertung ausgeführt wurde, indem Sie einen der folgenden Schritte ausführen:

    1.  Führen Sie Ngen.exe manuell mithilfe des folgenden Befehls über eine mit erhöhten Rechten dazu aufgefordert werden, ersetzen * &lt;DotNetVersion&gt; * für alle Versionen von .NET, die auf dem Computer installiert ist:

        `%WinDir%\Microsoft.NET\Framework\<DotNetVersion>\Ngen.exe ExecuteQueuedItems`

    2.  Führen Sie die app für ungefähr 30 Sekunden. Daraufhin wird eine geplante Aufgabe ausgeführt, die Ngen.exe enthält.

### <a name="system-requirements"></a>Systemanforderungen

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows® RT

-   Windows 8.1

-   Windows 8.1 RT

-   Windows 10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Diese Bewertung können auf einem Windows RT 8.1 System in einem der folgenden Methoden ausgeführt werden:

-   Packen Sie den Bewertungssauftrag zur in der Windows® Assessment-Konsole und führen sie dann auf Windows RT 8.1. Weitere Informationen zu dieser Option finden Sie unter [Paket einen Auftrag und Ausführen der Anwendung auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services. Weitere Informationen finden Sie unter [Technische Referenz zu Windows Assessment Services](http://go.microsoft.com/fwlink/?LinkId=215628).

## <a name="a-href-idbkmk-settingsasettings"></a><a href="" id="bkmk-settings"></a>Einstellungen


Sie können die Standardeinstellungen oder Anpassen der Einstellungen für eine Bewertung. Wenn Sie die Ergebnisse geprüft haben, können Sie sehen, ob die Bewertung der empfohlenen Einstellungen oder benutzerdefinierte Einstellungen verwendet, sodass Sie Ergebnisse aus der gleichen Aufträge auf mehreren Computern oder über einen Zeitraum vergleichen können.

In der folgenden Tabelle wird beschrieben, die Einstellungen für die Bewertung empfohlene Werte und alternative Werte für jede Einstellung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Empfohlene Einstellungen verwenden</p></td>
<td><p>Standardmäßig ist dieses Kontrollkästchen aktiviert und empfohlene Einstellungen verwendet werden. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Iterationen</p></td>
<td><p>Diese Einstellung können Sie die Anzahl der Male angeben, der die Bewertung ausgeführt wird. Die Ergebnisse sind durchschnittlich Iterationen. In der Standardeinstellung werden drei Iterationen ausgeführt, um eine genauere Ergebnis zu erhalten.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Während jeder Iteration öffnet die Bewertung jedes Windows Store-app. Die Länge jeder Iteration ist proportional zur Gesamtanzahl von apps, die analysiert werden. Apps können auch in der Vorbereitungsphase der Bewertung öffnen.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>Starten Sie jeden Windows Store-app</p></td>
<td><p>Diese Einstellung können Sie erzwingen, dass jeder app nicht fortsetzen und stattdessen eine app, die möglicherweise bereits auf dem PC open neu starten.</p></td>
</tr>
<tr class="even">
<td><p>Geben Sie die Namen der Windows Store-app</p></td>
<td><p>Diese Einstellung können Sie ein app anzugeben, verwenden Sie für die Bewertung anstelle die Bewertung auf alle apps wird ausgeführt werden soll. Die Bewertung umfasst alle apps, die den Namen entsprechen, die, den Sie eingeben. Einen partielle app-Namen können Sie mehr als eine app übereinstimmen. Bei Eingabe von <strong>Contoso</strong> auf einem PC mit einer <strong>"Contoso" Finance</strong> -app und einer <strong>Contoso News</strong> -app installiert würde die Bewertung beispielsweise beide apps enthalten.</p></td>
</tr>
<tr class="odd">
<td><p>Aktivieren Sie ausführliche CPU-Metriken</p></td>
<td><p>Diese Einstellung können Sie ausführliche Informationen über die CPU-Auslastung Aufschlüsselung einer App erhalten. Sie müssen-Symbole zur Verwendung dieser Einstellung konfigurieren. Weitere Informationen finden Sie unter [Symbol Unterstützung](../wpt/symbol-support.md).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für den Windows Store-App-Performance-Bewertung](results-for-the-windows-store-app-performance-assessment.md)

 

 







