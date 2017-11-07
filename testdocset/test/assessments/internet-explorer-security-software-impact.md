---
title: Internet Explorer Software Sicherheitsrisiko
description: Internet Explorer Software Sicherheitsrisiko
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d71e8ac3-f160-4554-8a26-2d3a95ac059e
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 0feeea13688d55bfea948993a0c5f56ea3b36a8d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="internet-explorer-security-software-impact"></a>Internet Explorer Software Sicherheitsrisiko


Internet Explorer Software Auswirkungen Bestandsaufnahme misst Aspekte von Internet Explorer, die von Modul und andere Browser-add-ins in der Regel betroffen sind. Die Bewertung misst die Auswirkungen der Sicherheits-Software auf die Anzeigedauer, CPU-Zeit und Ressourcenverwendung von Internet Explorer.

Weitere Informationen zu Ergebnisse und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für Internet Explorer Security Software Auswirkungen Assessment](results-for-internet-explorer-security-software-impact-assessment.md).

## <a name="before-you-begin"></a>Bevor Sie beginnen


Die erste Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Die besten Ergebnisse zu erzielen:

-   Vergleichen Sie Ergebnisse aus dieser Bewertung von Ergebnissen aus der gleichen Bewertung auf einem PC mit einer Neuinstallation Windows Bild mit nur Windows Defender ausgeführt. Dies hilft Ihnen das Identifizieren der Auswirkungen der Antischadsoftware auf das Bild hinzugefügt.

### <a name="system-requirements"></a>Systemanforderungen

Sie können diese Bewertung unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows RT

-   Windows 8.1

-   Windows 8.1 RT

-   Windows-10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Sie können diese Bewertung auf einem Windows RT 8.1 System in einem der folgenden Methoden ausführen:

-   Packen Sie den Bewertungssauftrag zur in der Windows-Assessment-Konsole, und führen sie dann auf Windows RT 8.1. Weitere Informationen zu dieser Option finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services. Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idbkmk-settingsasettings"></a><a href="" id="bkmk-settings"></a>Einstellungen


Sie können die Standardeinstellungen oder Anpassen der Einstellungen für eine Bewertung. Wenn Sie die Ergebnisse geprüft haben, können Sie sehen, ob die Bewertung der empfohlenen Einstellungen oder benutzerdefinierte Einstellungen verwendet, sodass Sie Ergebnisse aus der gleichen Aufträge auf mehreren Computern oder über einen Zeitraum vergleichen können.

In der folgenden Tabelle werden die Einstellungen für die Assessment empfohlen, Werte und alternative Werte für jede Einstellung beschrieben.

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
<td><p>Diese Einstellung können Sie die Anzahl der Male angeben, der die Bewertung ausgeführt wird. Die Ergebnisse sind durchschnittlich Iterationen. In der Standardeinstellung werden zehn Iterationen ausgeführt, um eine genauere Ergebnis zu erhalten.</p></td>
</tr>
<tr class="odd">
<td><p>URL</p></td>
<td><p>Diese Einstellung können Sie eine Website für die Bewertung im Rahmen des Tests statt der lokalen Testseite enthalten, die bei der Bewertung verwenden angeben.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Es wird empfohlen, die Standardeinstellung zu verwenden. Die lokalen Testseite gehört zum Lieferumfang der Bewertung und ohne Internet Connectivity ausgeführt werden kann. Wenn Sie eine Website, die für die Bewertung Internetverbindung erforderlich sind angeben, können Sie neue Variablen verursachen, die die Ergebnisse des Tests auswirken könnten.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für Internet Explorer Security Software Auswirkung Bewertung](results-for-internet-explorer-security-software-impact-assessment.md)

 

 







