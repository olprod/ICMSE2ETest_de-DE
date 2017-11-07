---
title: Verbundene Standby Energie-Effizienz
description: Verbundene Standby Energie-Effizienz
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9a23aaaa-922c-410d-a27d-ffd5eb67b546
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 22a5e57c77ada31e7a0172118ef6e0c96c1cf0e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="connected-standby-energy-efficiency"></a>Verbundene Standby Energie-Effizienz


Im Rahmen des Auftrags **Akkulaufzeit während dem Standbymodus verbunden** misst die Bewertung **Standby verbunden Energieeffizienz** wirken sich die Software und Geräte auf die Akkulaufzeit eines Systems Standby verbunden wird. Die Bewertung misst auch die aufgewendete Zeit Übergang in und aus dem Standbymodus verbunden.

In diesem Thema:

-   [Arbeitslasten](#bkmk-photoworkloads)

-   [Einstellungen](#settings)

Weitere Informationen zu Ergebnisse und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für die verbundene Standby Energie Effizienz Bewertung](results-for-the-connected-standby-energy-efficiency-assessment.md).

## <a name="a-href-idbeforeyoubeginabefore-you-begin"></a><a href="" id="beforeyoubegin"></a>Bevor Sie beginnen


Der ersten Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Bei der Ausführung dieser Bewertung auf Windows 8.1, stellen Sie sicher, dass die Einstellung **Sammeln Analysis Trace** bei der Beurteilung der erwarteten Akkulaufzeit deaktiviert ist. Wenn diese Option aktiviert ist, wird diese Option eine falsche Schätzung erstellt.

Aktivieren Sie Analyse Trace-Auflistung nur, wenn Sie weitere Informationen zum Untersuchen von anderen Probleme im Zusammenhang mit Energie benötigen.

### <a name="requirements"></a>Anforderungen

-   Das System muss dem Standbymodus verbunden unterstützen. Zum bestätigen, dass dieser Standbymodus unterstützt wird, öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie den folgenden Befehl aus:

    **Powercfg/a**

    Wenn Ihr System verbunden Standby unterstützt, wird in der Liste der verfügbaren Standbymodus Zustände **Standby (verbunden)** sein.

-   Stellen Sie sicher, dass das System auf Power DC (Batterie) ausgeführt wird. Energie Effizienz Aufträge dienen nur auf mobilen Geräten ausgeführt werden. Wenn eine Batterie nicht erkannt wurde, erhalten Sie einen Fehler.

**Wichtige**  
Um die Standby verbunden Energie Effizienz Bewertung auf einem Gerät mit Windows RT oder Windows RT 8.1 auszuführen, müssen Sie Folgendes ein:

1.  WAC-Computers fügen Sie ein USB-Speichergerät ein. Das Speichergerät sollte mindestens 60 MB verfügbarer Speicherplatz.

2.  Klicken Sie in WAC Packen Sie die Bewertung, und wählen Sie das USB-Speichergerät als Ziel. Weitere Informationen finden Sie unter [Packen Sie einen Auftrag verwenden und es auf einem anderen Computer ausführen](package-a-job-and-run-it-on-another-computer.md).

3.  Übertragen Sie das USB-Speichergerät auf das Gerät, auf dem Windows RT oder Windows RT 8.1 ausgeführt wird.

4.  Kopieren Sie den Inhalt des Geräts, USB-Speicher zu einem Ziel auf dem Gerät, auf dem Windows RT oder Windows RT 8.1 ausgeführt wird.

5.  Öffnen Sie auf dem Gerät, auf dem Windows RT oder Windows RT 8.1 ausgeführt wird eine Eingabeaufforderung mit Administratorrechten aus.

6.  Navigieren Sie zum Speicherort des Assessment-Pakets.

7.  Navigieren Sie zu der Assessment1\\Arm-Verzeichnis.

8.  Führen Sie InstallKitsPolicy.cmd aus. Dadurch wird das Gerät neu gestartet.

9.  Nach dem Neustart wieder in den Stamm des Speicherorts Paket Assessment navigieren Sie, und führen Sie RunJob.cmd.

Führen Sie folgende Schritte aus, um die Richtlinie zu entfernen:

1.  Navigieren Sie zum Speicherort des Assessment-Pakets.

2.  Navigieren Sie zu der Assessment1\\Arm-Verzeichnis.

3.  Führen Sie DeleteKitsPolicy.cmd. Dadurch wird das Gerät neu gestartet.

 

### <a name="recommendations"></a>Empfehlungen

Bevor Sie beginnen, konfigurieren Sie die Einstellungen des tragbaren Computers reduzieren das Risiko von Warnungen in den Ergebnissen generieren und Stromverbrauchs beeinträchtigen. Die folgenden Richtlinien werden Einstellungen empfohlen. Sie sind nicht für die Ausführung des Auftrags erforderlich, aber die Ergebnisse beeinträchtigt werden, wenn der Computer nicht ordnungsgemäß konfiguriert ist.

-   Stellen Sie sicher, dass drahtlosen aktiviert ist und dass der Computer mit einem Netzwerk verbunden ist. Andernfalls können die Ergebnisse realistische Szenarien nicht wider.

    Öffnen Sie in der Systemsteuerung **Drahtlosnetzwerke verwalten**. Falls drahtlosen Funktionalität ist nicht aktiviert, schalten Sie ihn, und Verbinden mit einem drahtlosen Netzwerk.

    **Hinweis**  
    Wenn drahtlosen Verbindung ist auf, aber es kein Netzwerk ist für die Verbindung, sind die Ergebnisse noch betroffen.

     

-   Installieren Sie und aktivieren Sie Antivirussoftware. Wenn die Antivirensoftware nicht aktiviert ist und ausgeführt wird, können die Ergebnisse realistische Szenarien nicht wider.

    Öffnen Sie in der Systemsteuerung **Action Center**, wählen Sie **Sicherheit**, und überprüfen Sie, dass der **Virenschutz** **aktiviert**ist. Wenn dies nicht der Fall ist, wählen Sie **Aktion Center-Einstellungen ändern** , und wählen Sie dann das Kontrollkästchen **Virenschutz** .

-   Stellen Sie sicher, dass die Richtlinie Power **ausgeglichen**festgelegt ist. Standardmäßig generiert eine beliebige andere Power-Richtlinie eine Warnung ausgegeben, die das Ergebnis beeinflussen können.

    Klicken Sie in der Systemsteuerung öffnen Sie **Energieoptionen**, und wählen Sie dann auf **abgestimmt**.

-   Stellen Sie sicher, dass der Computer konfiguriert ist, damit ein Kennwort nicht erforderlich ist, wenn der Computer aus einem Bildschirmschoner wird.

-   Stellen Sie sicher, dass alle Gerätetreiber ordnungsgemäß installiert sind. Ergebnisse können deutlich abweichen, wenn der Computer mit fehlenden oder falschen Treiber verfügt. Die [Überprüfung der Treiber](driver-verification.md) Bewertung können Sie um Treiberprobleme auf dem Computer zu ermitteln, die Sie bewerten möchten.

-   Die besten Ergebnisse zu erzielen wird empfohlen, dass Sie den Auftrag als gepackte Auftrag ausgeführt. Informationen zum Erstellen und Ausführen eines Auftrags gepackten finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

### <a name="system-requirements"></a>Systemanforderungen

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows 8.1

-   Windows RT

-   Windows 8.1 RT

-   Windows 10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

## <a name="a-href-idbkmk-photoworkloadsaworkloads"></a><a href="" id="bkmk-photoworkloads"></a>Arbeitslasten


Eine Arbeitslast ist ein Satz von automatischen Aufgaben, die Aktivität des Benutzers auf eine vordefinierte, wiederholbare Weise simulieren. Führen Sie die Arbeitslasten unabhängig voneinander. Sie können eine beliebige Kombination von diese Arbeitslasten während der Bewertung ausführen auswählen. Diese Bewertung misst Dauer und Durchsatz für jede Arbeitslast, die Sie verwenden, und speichert die Kriterien in der Datei mit den Suchergebnissen.

Die folgende Tabelle beschreibt die Arbeitslasten, die für die Bewertung verfügbar sind.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Arbeitslast</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Diagnose-Modus</p></td>
<td><p>Verwendet schwer Tracing, generieren zusätzliche Tracing, Metriken und Probleme, die zur Diagnose von Energie Effizienz Probleme verwendet werden. Wenn die Option <strong>Generate Diagnoseinformationen</strong> unter <strong>Energie Effizienz Einstellungen</strong>aktiviert ist, wird die erste Iteration im Diagnosemodus ausgeführt.</p></td>
</tr>
<tr class="even">
<td><p>Arbeitslast-Modus</p></td>
<td><p>Einfache Tracing verwendet. Arbeitslast Modus generiert keine Metriken oder Probleme. Wenn die Option <strong>Generate Diagnoseinformationen</strong> unter <strong>Energie Effizienz Einstellungen</strong>aktiviert ist, während der Ausführung der ersten Iteration im Diagnosemodus und führen Sie die verbleibenden Iterationen im Modus Arbeitslast. Führen andernfalls alle Iterationen im Arbeitslast-Modus.</p></td>
</tr>
</tbody>
</table>

 

## <a name="settings"></a>Einstellungen


Microsoft definiert empfohlene Einstellungen, sodass Sie die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen können. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet. Bei Bedarf können Sie diese Einstellungen ändern.

In der folgenden Tabelle werden die verbunden Standby Energie Effizienz Assessment Einstellungen beschrieben.

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
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet wird. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Minute(n)</p></td>
<td><p>Gibt die Zeitspanne pro Iteration in Minuten, die der Computer im Standbymodus verbunden aufwendet.</p></td>
</tr>
<tr class="odd">
<td><p>Deaktivieren Sie Stille Stunden</p></td>
<td><p>Gibt an, ob die Funktion stillen Stunden während der Bewertung zu deaktivieren. Standardmäßig wird das automatische Stunden Feature nicht deaktiviert.</p></td>
</tr>
</tbody>
</table>

 

 

 






