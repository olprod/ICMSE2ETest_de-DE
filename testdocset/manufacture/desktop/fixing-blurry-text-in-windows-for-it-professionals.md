---
author: Justinha
Description: "Beheben von verschwommenen Text in Windows 8.1 für IT-Experten"
ms.assetid: 02738ee5-e2d4-491f-8b25-a5a360383c7c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Beheben von verschwommenen Text in Windows 8.1 für IT-Experten"
ms.openlocfilehash: 24b3c3d0d69a413ea07ace86d3d5bfe23bf648d5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="fixing-blurry-text-in-windows-81-for-it-professionals"></a>Beheben von verschwommenen Text in Windows 8.1 für IT-Experten


Windows® desktop-apps werden im Allgemeinen gibt es in zwei Klassen unterteilt: apps, bei denen *DPI-bewusst* und welche nicht. DPI-bewusst apps können aktiv Windows beim Starten der Anwendung wissen, dass diese Skalierung selbst auch eine hohe DPI-Anzeige arbeiten werden. Diese apps enthalten: InternetExplorer, Office, Firefox und .NET 2.0 + (einschließlich WPF) apps. Diese apps funktionieren im Allgemeinen auch über eine Vielzahl von horizontal Faktoren. Daher, wenn Ihre Enterprise-Zeile des Geschäfts-apps auch DPI-bewusst werden, die Benutzer sollten kein Problem mit jeder Windows 8.1 zeigt oder skalieren Faktoren.

Wenn eine Anwendung nicht DPI-bewusst ist und eine hohe DPI-Anzeige ausgeführt wird, skaliert Windows die app jedoch um Bitmap Skalierung auf die Anwendungsausgabe anwenden. Dadurch wird sichergestellt, dass die Anwendung die richtige Größe auf eine hohe DPI-Anzeige. In den meisten Fällen, die dies in Applikationen scharfe und verwendbar, jedoch in einigen Fällen führt, das Ergebnis ist kleiner scharfe und möglicherweise ein etwas unscharf oder verschwommen aussehen aufgrund der Bitmap-skaliert.

**In diesem Thema:**

-   [Wie Sie feststellen, ob eine Anwendung nicht DPI-bewusst ist.](#recognize)

-   [Informationen zu apps Möglichkeiten, die DPI-bewusst nicht sind](#unaware)

-   [Teilen Sie skalieren eine app, die nicht DPI-bewusst ist nicht für Windows](#dontscale)

## <a name="span-idrecognizespanspan-idrecognizespanhow-to-tell-if-an-application-is-not-dpi-aware"></a><span id="recognize"></span><span id="RECOGNIZE"></span>Wie Sie feststellen, ob eine Anwendung nicht DPI-kompatibel ist.


Verwenden Sie das [Tool Process Explorer](http://go.microsoft.com/fwlink/p/?linkid=204774) zu ermitteln, ob eine app DPI-bewusst ist. *Abbildung 1 Process Explorer* zeigt dieses Dienstprogramm verwendet wird, mit der Spalte für **DPI zur Förderung des Bekanntheitsgrads** aktiviert. (Standardmäßig wird Prozess Explorer nicht die **DPI-Ausführung** -Spalte angezeigt. Um diese Spalte zu aktivieren, klicken Sie auf das Menü **Ansicht** , klicken Sie auf **Spalten auswählen**, aktivieren Sie das Kontrollkästchen für **DPI zur Förderung des Bekanntheitsgrads**, und klicken Sie auf **OK**.) Die Spalte mit dem Titel **DPI zur Förderung des Bekanntheitsgrads** erfahren Sie, ob ein bestimmter Prozess DPI bekannt ist.

![Prozess Explorer - sysinternals](images/processexplorersysinternals.jpg)

**Abbildung 1 Prozess Explorer**

Windows 8.1 unterscheidet zwischen drei Klassen von Anwendungen.

**Tabelle 1 DPI zur Förderung des Bekanntheitsgrads Apps**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">DPI-Ausführung</th>
<th align="left">Beispiele</th>
<th align="left">Verhalten</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Nicht bekannt</p></td>
<td align="left"><p><strong>MMC.exe</strong> (Microsoft Management Console und seine-Plug-Ins)</p></td>
<td align="left"><p>Windows Bitmap skaliert die Anwendung auf eine beliebige hohe DPI angezeigt, die das System angefügt sind; kann auf 125 % und 150 % Skalierungsfaktor fuzzy sein.</p></td>
</tr>
<tr class="even">
<td align="left"><p>System-fähigen</p></td>
<td align="left"><p>Apps für Office</p></td>
<td align="left"><p>Anwendung skaliert selbst beim Start auf das System DPI (in der Regel identisch mit der primären Anzeige DPI); Windows skaliert die app zeigt an, die dies nicht übereinstimmen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Pro-Monitor-fähigen</p></td>
<td align="left"><p>InternetExplorer 11</p></td>
<td align="left"><p>Anwendung skaliert selbst dynamisch zur Anzeige DPI.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idunawarespanspan-idunawarespanwhat-you-can-do-about-apps-that-arent-dpi-aware"></a><span id="unaware"></span><span id="UNAWARE"></span>Informationen zu apps Möglichkeiten, die nicht DPI-bewusst sind


### <a name="span-idrunthelatestversionoftheapporasktheapplicationvendortoupdatetheirapptobedpiawarespanspan-idrunthelatestversionoftheapporasktheapplicationvendortoupdatetheirapptobedpiawarespanspan-idrunthelatestversionoftheapporasktheapplicationvendortoupdatetheirapptobedpiawarespanrun-the-latest-version-of-the-app-or-ask-the-application-vendor-to-update-their-app-to-be-dpi-aware"></a><span id="Run_the_latest_version_of_the_app_or_ask_the_application_vendor_to_update_their_app_to_be_DPI_aware"></span><span id="run_the_latest_version_of_the_app_or_ask_the_application_vendor_to_update_their_app_to_be_dpi_aware"></span><span id="RUN_THE_LATEST_VERSION_OF_THE_APP_OR_ASK_THE_APPLICATION_VENDOR_TO_UPDATE_THEIR_APP_TO_BE_DPI_AWARE"></span>Führen Sie die neueste Version der app oder bitten Sie den Hersteller der Anwendung so aktualisieren Sie ihre app zum DPI-bewusst sein.

Microsoft empfiehlt, dass alle Anwendungen werden DPI-bewusst. Es ist möglich, dass neuere Versionen der Anwendungen bereits DPI-bewusst sind. Wenn sie nicht sind, können Sie den Hersteller Ihrer app so aktualisieren Sie ihre app zum DPI-bewusst sein bitten. Microsoft bietet Entwicklerressourcen, mit deren Hilfe können ihre app, einschließlich der folgenden aktualisieren:

-   [Tätigen Ihren Desktop-Apps scheinen auf High-DPI zeigt (BUILD 2013 Präsentation)](http://go.microsoft.com/fwlink/p/?linkid=329827)

-   [Schreiben von DPI-bewusst Desktopanwendungen in Windows 8.1](http://go.microsoft.com/fwlink/p/?LinkID=307061)

-   [Dynamische DPI-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=329826)

### <a name="span-iddontscalespanspan-iddontscalespantell-windows-not-to-scale-an-app-thats-not-dpi-aware"></a><span id="dontscale"></span><span id="DONTSCALE"></span>Teilen Sie eine app zu skalieren, die nicht DPI-bewusst ist nicht für Windows

In den Fällen, in dem Benutzer die Bitmap bewältigen können nicht, kann Skalierung von apps, die nicht DPI-bewusst (beispielsweise 125 % Skalierung und fuzzy Applications) sind einzelne Windows-desktopanwendungen shimmed werden, um nicht skaliert werden. Benutzer können diese Schritte durchführen, mithilfe der Registerkarte **Kompatibilität** , der die Anwendung **Eigenschaften** Benutzeroberfläche. *Abbildung 2 Anwendungseigenschaften* beispielsweise zeigt, wie ein Benutzer Bitmap skaliert deaktiviert werden kann:

![Anwendungseigenschaften](images/applicationproperties.jpg)

**Abbildung 2 Anwendungseigenschaften**

Sie können die Anwendungstypen Bulk shimming verwalten, mithilfe des Tools Compatadmin, die im Application Compatibility Toolkit zur Verfügung steht, die in dem Windows Assessment and Deployment Kit (ADK) enthalten ist. Sie können Windows ADK von [Windows Assessment and Deployment Kit (ADK) für Windows® 8](http://go.microsoft.com/fwlink/p/?linkid=288775)herunterladen. Weitere Informationen dazu, wie Sie das Tool Compatadmin verwenden finden Sie unter [Gewusst wie: Verwenden Sie das Dienstprogramm Compatibility Administrator in Windows](http://go.microsoft.com/fwlink/p/?linkid=329828).

**Wichtige**  
Deaktivieren der Anzeige Skalierung kann Inhalte führen, die ist zu klein zum Lesen oder zuverlässig interaktiv sein; Sie können auch visuelle Artefakte wie abgeschnittene oder überlappende Inhalte zur Folge. Diese Probleme hängen Details wie die app geschrieben wurde. Aus diesem Grund wird empfohlen, nur diese Einstellung ändern, wenn Sie unbedingt erforderlich ist. Dieser Shim werden soll nicht angewendet, apps, die keine erfordern oder Geräte, die keine erfordern.

 

### <a name="span-idimpracticalspanspan-idimpracticalspanuse-windows-8-dpi-scaling-not-generally-recommended"></a><span id="impractical"></span><span id="IMPRACTICAL"></span>Verwenden Sie Windows 8 DPI Skalierung (nicht empfohlen)

Windows 8.1 umfasst eine Windows 8-Kompatibilität Skalierung Modus, in dem alle visual Weichzeichnen Probleme mit bestimmten zeigt Adresse bereitgestellt werden kann. Beachten Sie, dass alle Vorteile der Features Windows 8.1 DPI mit den Kompatibilitätsmodus deaktiviert werden. Diese Methode sollte nur als letztes Mittel verwendet werden, enthält die Enterprise-Umgebung zu viele apps, die DPI-bewusst, durch die Anwendung shimming anwenden gemindert werden nicht sind. Benutzer können in diesem Modus in der Benutzeroberfläche der DPI-Systemsteuerungsoption Mobilgeräts auf das Kontrollkästchen **selbst auswählen eine Skalierung Ebene für alle meine zeigt**zugreifen:

![Anzeigen](images/controlpaneldisplay.jpg)

**Abbildung 3 Ebenen Option Skalierung**

Diese Einstellung kann auch während der Bereitstellung angewendet werden, wenn Sie viele bestimmte apps, müssen Wartung haben und Einführen einer großen Maßstab zu niedrig oder Mid Dichte angezeigt werden soll. Sie können das Bild im Überwachungsmodus vor der Bereitstellung anpassen. Finden Sie unter [Übersicht über Audit-Modus](http://go.microsoft.com/fwlink/p/?linkid=214469). Siehe auch im nächsten Abschnitt, der erklärt, wie Gerät Erkennung und Registrierung Anpassung programmgesteuert ausführen.

### <a name="span-iddisplayspanspan-iddisplayspanunderstanding-high-dpi-display-types-and-windows-scaling"></a><span id="DISPLAY"></span><span id="display"></span>Zeigen Sie Grundlegendes zu Hochauflösenden an, Inhaltstypen und Skalieren von Windows

Windows 8.1 skaliert apps, die dynamisch DPI-wissen nicht, durch Ändern der Größe der von der Anwendung generierte Bitmap. Bitmap funktioniert am besten Skalierung, wenn am Ganzzahl skaliert Vielfache (beispielsweise 1 X, X 2, 3 X), er kann jedoch haben visuelle Artefakte, die häufig als verschwommene/fuzzy unter nicht-Integer Vielfache (beispielsweise 125 %, 150 %) angesehen werden

Windows unterstützt eine gesamte Spektrum der Bildschirmgrößen, Auflösung und daher DPI. Fallen einige DPI-Bereiche, die das Ergebnis nicht optimal Windows bei apps, die nicht wissen DPI Skalierung.

*Tabelle 2 Skalierung Werte* beschreibt die mögliche Probleme, die Benutzer an unterschiedlichen Fenstern Skalierung Werten auftreten können:

**Tabelle 2 Werte Skalierung**

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Skalierungsfaktor</th>
<th align="left">100 % mainstream</th>
<th align="left">125 % Wert</th>
<th align="left">150 % premium</th>
<th align="left">200 % premium</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Vorteil Skalierung</p></td>
<td align="left"><p>n/v</p></td>
<td align="left"><p>Kleine Größe zur Verbesserung der</p></td>
<td align="left"><p>Zur Verbesserung der erhebliche Größe</p></td>
<td align="left"><p>Zur Verbesserung der kritischen Größe</p></td>
</tr>
<tr class="even">
<td align="left"><p>Bitmap-Skalierung von apps nicht bekannt</p></td>
<td align="left"><p>n/v</p></td>
<td align="left"><p>Die meisten Renderingzeit Unschärfe</p></td>
<td align="left"><p>Weniger erkennbar Unschärfe</p></td>
<td align="left"><p>Klares</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Skalierung von unterstützenden apps</p></td>
<td align="left"><p>n/v</p></td>
<td align="left"><p>Klares</p></td>
<td align="left"><p>Klares</p></td>
<td align="left"><p>Klares</p></td>
</tr>
</tbody>
</table>

 

Wie in der obigen Tabelle gezeigt, manifest die meisten Probleme bei der Skalierung Verhältnis 125 %. Aus diesem Grund sollten alle Risikominderung apps Ziel, die auf 125 % nur Systeme Skalierung nicht DPI-bewusst sind.

Informationen zu wie zum Identifizieren 125 % Systeme oder Windows 8 Skalierung Verhalten für ein System 125 % wiederherzustellen finden Sie unter [DPI-bezogene APIs und die Registrierung konfiguriert](dpi-related-apis-and-registry-settings.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hochauflösenden Unterstützung für IT-Experten](high-dpi-support-for-it-professionals.md)

 

 






