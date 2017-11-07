---
title: "Übersicht über die Windows-Assessment-Konsole"
description: "Übersicht über die Windows-Assessment-Konsole"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 12afc4f2-74be-41d9-ac09-a9e7c7d79d37
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 7179a0c85674b02d22c06a63219e7228ce73c26c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-console-overview"></a>Übersicht über die Windows-Assessment-Konsole


Das Windows Assessment-Konsole und Bewertung werden im Rahmen des Windows Assessment Toolkit installiert. Die Windows-Konsole Assessment ist eine Benutzeroberfläche, die Bewertung erkennen können, und vordefinierte Aufträge, Gruppe Bewertung erstellen neue Aufträge Ändern vorhandener Aufträge, Aufträge ausführen und Verwalten der Auftragsergebnisse. Ein Auftrag ist eine Auflistung von einen oder mehrere Bewertung (und deren Einstellungen), die gleichzeitig auf einem Computer ausgeführt. Häufig enthalten die Ergebnisse eines Auftrags zur Diagnose und-Wartung Informationen, die Ihnen helfen bestimmen, Bereiche, die zusätzliche Untersuchung und Maßnahme benötigen. Weitere Informationen zur Verwendung der Windows-Assessment-Konsole finden Sie unter [schrittweise Anleitung für Windows-Assessment-Konsole](windows-assessment-console-step-by-step-guide.md).

Eine Bewertung ist eine Kombination von XML und Binärdateien, die Auslösen von eines bestimmten Satz von Status auf einem Computer, messen und die Aktivität Datensatz, und die aufgezeichneten Ergebnisse zu erhalten. Sie können überprüfen, dass die Bewertungsfragen verfügbaren, um zu ermitteln, was Sie bewerten möchten. Klicken Sie dann können die Bewertung auf ein Projekt hinzufügen oder konfigurieren einen vordefinierten Auftrag zum enthalten die Bewertung und Einstellungen, die Ihren Anforderungen entsprechen. Weitere Informationen zu einzelnen Bewertung finden Sie unter [Bewertung](assessments.md).

In diesem Thema:

-   [Systemanforderungen](#asmt-sysreq)

-   [Vorteile](#asmt-benefits)

-   [Einschränkungen](#asmt-limitations)

-   [Häufige Szenarien](#asmt-scenarios)

## <a name="a-href-idasmt-sysreqasystem-requirements"></a><a href="" id="asmt-sysreq"></a>Systemanforderungen


Die Windows-Konsole Assessment können auf eine der folgenden Betriebssysteme installiert sein:

-   Windows 8

-   Windows 10

**Hinweis**  
Einige Bewertung müssen auf einem bestimmten Betriebssystem ausgeführt werden. Weitere Informationen zu Systemanforderungen für einzelne Bewertung finden Sie unter [Bewertung](assessments.md).

 

Darüber hinaus benötigen, auf dem die Windows-Assessment-Konsole installiert, Systempartition mindestens 200 Megabyte (MB) freier Speicherplatz zum Ausführen der Bewertung. Diese Anforderung ist für Event Tracing for Windows (ETW), ein Feature erforderlich, die alle Bewertung verwenden. Über die Zeit, zur Bewertungsergebnisse und Protokolldateien können Dateien eine große Menge an Speicherplatz beanspruchen.

## <a name="a-href-idasmt-benefitsabenefits"></a><a href="" id="asmt-benefits"></a>Vorteile


Die Windows-Konsole Assessment bietet die folgenden Vorteile:

-   Eine Benutzeroberfläche, die Sie verwenden können, auf einen Computer, bewerten Problemen, überprüfen die Empfehlungen und Ergebnisse verglichen werden.

-   Einige Auftragsergebnisse enthalten Links zu weiteren Informationen, die Ihnen helfen können die Computer und Links zu Windows Performance Analyzer (WPA) direkt verbessern, damit Sie die Ursache eines Problems wieder auf die Quelle verfolgen können.

-   Die Möglichkeit, einige Ergebnisse in der Detailansicht vergleichen und die Möglichkeit zum Vergleichen von eigenständigen Hunderte von Ergebnissen in eine Zusammenfassungsansicht. Weitere Informationen finden Sie unter [Vergleich der Ergebnisse](compare-results.md).

-   Die Möglichkeit zum Zusammenfassen eines Auftrags und speichern Sie es auf einem USB-Laufwerk, führen Sie ihn auf einem anderen Computer. Weitere Informationen finden Sie unter [Packen Sie einen Auftrag verwenden und es auf einem anderen Computer ausführen](package-a-job-and-run-it-on-another-computer.md).

-   Die Möglichkeit, die Ergebnisse auf die Standardbibliothek Ergebnisse aus anderen Speicherorten, wie Wechselmedium oder einer Netzwerkfreigabe zu importieren.

-   Vordefinierte Aufträge, die leicht sind zu finden und ausführen.

-   Die Möglichkeit, die empfohlenen Assessment Einstellungen wiederherstellen, wenn Sie sie geändert haben.

-   Die Möglichkeit, die Standardeinstellungen für die Vorlage wiederherstellen, wenn Sie einen vordefinierten Auftrag geändert haben.

-   Die Möglichkeit zum Anpassen eines Auftrags um enthalten die Bewertung und Einstellungen, die Sie verwenden möchten.

-   Die Möglichkeit verwenden benutzerdefinierte Analysen, die kompatibel mit der Bewertung Plattform in der Windows-Assessment-Konsole auf die gleiche Weise wie sind, die Sie verwenden die Bewertung, die das Toolkit bereitstellt. Weitere Informationen finden Sie unter [individuelle Beurteilung registrieren](register-and-unregister-custom-assessments.md).

    **Hinweis**  
    Eine Reihe von öffentlichen APIs können zum Erstellen und Erweitern von Analysen, die für die Bewertung Plattform kompatibel sind. Weitere Informationen finden Sie unter [MSDN: Assessment Execution Engine](http://go.microsoft.com/fwlink/?LinkId=236367).

     

## <a name="a-href-idasmt-limitationsalimitations"></a><a href="" id="asmt-limitations"></a>Einschränkungen


Diese Beschränkungen in der Windows-Bewertung Konsole angezeigt:

-   Windows-Konsole Assessment bewertet ein Computer zu einem Zeitpunkt. Weitere Informationen zu Remote mehreren Computern zur selben Zeit bewerten finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

-   Windows-Assessment-Konsole kann nicht auf einem Server installiert werden und ist nicht so konzipiert, dass Servercomputern bewerten.

-   In der Windows-Assessment-Verwaltungskonsole kann nicht auf Windows RW installiert werden Sie können jedoch einen Auftrag zu packen und auf Windows RT ausführen, wenn die Bewertung ARM-Prozessoren unterstützt. Nicht alle Bewertung unterstützen auf ARM-Prozessoren ausgeführt wird. Weitere Informationen finden Sie unter [Packen Sie einen Auftrag verwenden und es auf einem anderen Computer ausführen](package-a-job-and-run-it-on-another-computer.md). Weitere Informationen zu den Systemanforderungen für die Bewertung finden Sie unter [Bewertung](assessments.md).

## <a name="a-href-idasmt-scenariosacommon-scenarios"></a><a href="" id="asmt-scenarios"></a>Häufige Szenarien


Die Windows-Assessment-Konsole und die Bewertung erfüllen allgemeine Branche müssen für die Bewertung von eines Computers einheitlich basierend auf bestimmte Szenarien. Sie sind für diese Benutzergruppen bestimmt:

-   System-Builder, die Zeitachse wichtige Qualitätsmetriken und den Effekt mit verschiedenen Kombinationen der Komponente auf den Systemen, die sie erstellen möchten

-   Computer Prüfer und Analysten, die einheitlich Leistung, Zuverlässigkeit und Funktionalität gemessen werden soll

Die Windows-Konsole Assessment ist in der Regel in folgenden Szenarien verwendet:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Szenario</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Schwarz-Feld</p></td>
<td><p>Führen Sie einen vordefinierten Auftrag, und überprüfen Sie die Ergebnisse für ungewöhnliche Werte oder Anzeichen für Probleme mit Treibern, die Speicherverwendung oder andere Bereiche, die die Bewertung Adresse.</p></td>
</tr>
<tr class="even">
<td><p>Vergleich der Ergebnisse</p></td>
<td><p>Führen Sie einen vordefinierten Auftrag oder eine einzelne Bewertung mit Einstellungen für empfohlene Bewertung auf jedem Computer, auf denen ein unterstütztes Betriebssystem ausgeführt wird. Verwenden Sie die Windows-Assessment-Verwaltungskonsole zum Verpacken des Auftrags auf einem anderen Computer ausgeführt. Importieren Sie die Ergebnisse nach der Ausführung des Auftrags auf dem anderen Computer auf die Standardbibliothek Ergebnisse. Sie können die Ergebnisse von einem beliebigen 10 Windows-basierten Computer mit denen der anderen unterstützten Operating System zum Identifizieren der Unterschiede vergleichen.</p></td>
</tr>
<tr class="odd">
<td><p>Bereinigten computer</p></td>
<td><p>Bewertung auf einem <em>bereinigten Computer</em> (ein Computer, der nur das Betriebssystem enthält) ausführen, basislinienergebnisse System herzustellen. Anweisungen finden Sie unter [Create basislinienergebnisse](create-baseline-results-for-comparing-windows-images.md).</p></td>
</tr>
<tr class="even">
<td><p>Hinzugefügte Hardware- oder Komponenten</p></td>
<td><p>Das Computersystem bereinigten neue Hardware oder Software hinzu, und klicken Sie dann erneut ausführen Sie, die Bewertung, um die Ergebnisse mit bereinigen Computer Ergebnisse zu vergleichen. Anweisungen finden Sie unter [basislinienergebnisse erstellen](create-baseline-results-for-comparing-windows-images.md).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien Windows Assessment-Konsole](windows-assessment-console-common-scenarios.md)

[Bewertung](assessments.md)

[Assessment Plattform Befehlszeilensyntax](assessment-platform-command-line-syntax.md)

 

 







