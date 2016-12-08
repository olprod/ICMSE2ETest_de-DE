---
title: "Einführung in die WPA-Benutzeroberfläche"
description: "Einführung in die WPA-Benutzeroberfläche"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2a4e4be8-18a0-4962-a57d-eb8627dd8374
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3bbb328145c9f8e611e5261f2436b2e4cc7013c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="introduction-to-the-wpa-user-interface"></a>Einführung in die WPA-Benutzeroberfläche


Die Windows Performance Analyzer (WPA)-Benutzeroberfläche (UI) besteht aus einer Auflistung von angedockte Fenster, die einen zentralen Arbeitsbereich umgeben. Diesem zentralen Arbeitsbereich enthält **Analysis** Registerkarten. Alle Fenster können abgedockt oder verschoben und angedockt an einem anderen Speicherort. Um ein geschlossenes Fenster zu öffnen, wählen Sie das Fenster im Menü **Fenster** .

Die folgende Abbildung zeigt die WPA-Benutzeroberfläche. Diagnose Konsolenfenster wird nicht angezeigt.

![Modell für wpa Layout mit Etiketten auf verschiedenen Bereichen](images/wpalayout.jpg)

## <a name="graph-explorer-window"></a>Diagramm Explorer-Fenster


Wenn Sie eine Aufzeichnung in WPA Miniaturansichten aller öffnen die die Diagrammen, die für die Aufzeichnung gelten im Graph-Explorer-Fenster angezeigt werden unter mehrere Knoten gruppiert. Wenn Sie um einen Knoten zu erweitern, klicken Sie auf das kleine Dreieck neben dem Knotennamen.

Um das vollständige Diagramm angezeigt wird, ziehen Sie im Diagramm auf der Registerkarte **Analyse** . Sie können mehrere Diagramme auf der Registerkarte **Analyse** ziehen.

Weitere Informationen finden Sie unter [Diagramm Explorer](graph-explorer.md).

## <a name="analysis-tab"></a>Registerkarte Analyse


Wenn Sie ein Diagramm aus dem Diagramm Explorer-Fenster auf der Registerkarte **Analyse** ziehen, wird das Diagramm zusammen mit einer **Legende** Steuerelement auf der linken Seite angezeigt. Das **Legende** Steuerelement erklärt die Bedeutung der Linien oder Balken im Diagramm. Wenn Sie dieselben Daten in Tabellenform anzeigen möchten, klicken Sie auf das Symbol Layout ganz rechts auf der Titelleiste Diagramm. Dadurch wird die zugeordneten Datentabelle geöffnet und im Diagramm auf eine Miniaturansicht reduziert. Wenn Sie das Diagramm in Originalgröße und die Datentabelle anzeigen möchten, klicken Sie auf das Symbol des am weitesten links Layout.

Den rechts Dropdown-Pfeil können auf der Titelleiste des Diagramms zum Wechseln von einem Liniendiagramm ein gestapeltes Liniendiagramm oder ein gestapeltes Balkendiagramm.

Die Dropdown-nach-links können auf der Titelleiste des Diagramms aus verschiedenen Parametern für das Diagramm, wenn weitere Parameter verfügbar sind. Beispielsweise können Sie die CPU-Auslastung von Prozess, CPU oder nach Prozess und Thread anzeigen.

Alle Diagramme auf der Registerkarte **Analyse** freigeben eine einzelne Zeitachse. Zum Anzeigen von Diagrammen, die einen anderen Zeitplan haben, öffnen Sie eine andere **Analysis** -Registerkarte, indem Sie **Neue Analyseansicht** klicken Sie im Menü **Fenster** .

Weitere Informationen finden Sie auf der [Registerkarte Analyse](analysis-tab.md).

## <a name="analysis-assistant-window"></a>Fenster des Analysis-Assistenten


Bei der Auswahl einer bestimmten Grafik oder eine Datentabelle werden Informationen zu diesem bestimmten Diagramm und die Tabelle in der Analyse-Assistent angezeigt. Verwenden Sie dies als Anleitung bei der Analyse.

Weitere Informationen finden Sie unter [Analysis-Assistenten](analysis-assistant.md).

## <a name="issues-window"></a>Problemfenster


Wenn Sie die Plattform zur Bewertung die Aufzeichnung erstellt haben, enthält das Fenster Probleme Probleme, die die Bewertung identifiziert. In diesem Fenster wird an der oberen rechten Ecke verankert. Wenn Sie nicht die Aufzeichnung der Assessment-Plattform erstellt haben, wird das Fenster minimiert, da keine Daten vorhanden sind.

Wenn Sie ein Problem in diesem Fenster klicken, werden Details zu diesem Problem im Detailfenster angezeigt. Alle identifizierte Probleme werden auf der Registerkarte **Analyse** unter alle Diagramme, die Sie geöffnet haben.

Weitere Informationen finden Sie unter [Fenster Probleme](issues-window.md).

## <a name="details-window"></a>Im Dialogfeld Details


Wenn Sie die Plattform zur Bewertung die Aufzeichnung erstellt haben, wird im Dialogfeld Details der unter das Fenster Probleme in der unteren rechten Ecke des Arbeitsbereichs angezeigt. Das Fenster Details finden Sie Informationen über das ausgewählte Problem und empfohlene Lösungen.

Weitere Informationen finden Sie [Im Dialogfeld Details](details-window.md).

## <a name="diagnostic-console-window"></a>Diagnose Konsolenfenster


Diagnose Konsolenfenster wird am unteren Rand des Arbeitsbereichs verankert. In diesem Fenster enthält eine Liste der Ausnahmen aufzeichnen sowie Details im Zusammenhang mit Symbol laden und decodieren.

Weitere Informationen finden Sie unter [Diagnostic Konsolenfenster](diagnostic-console.md).

## <a name="classic-menu-and-rich-menu"></a>Klassische und Rich-Menü


Standardmäßig verwendet WPA im klassischen Menü beim Öffnen einer aufzeichnungs. Wie die meisten Applikationen zeigt im klassischen Menüs (Datei, Trace usw.) oben. Auf Wunsch eine kompakte, intuitive und moderne Benutzeroberfläche können Sie im Rich Menü verwenden. Klicken Sie im Menü Rich:

-   Die alte Menüs bündelt aus dem klassischen Menü
-   Tastenkombinationen für Menüs Features verwenden Sie häufig, z. B. öffnen, Profil anwenden, Symbole laden.
-   Verwendet nur ein Menü (Datei) als den Einstiegspunkt für alle im Menüoptionen

Weitere Informationen zu den Unterschieden zwischen dem Menü klassische Menü- und Rich-Text und wie Sie und wieder zwischen ihnen wechseln finden Sie unter [klassische im Vergleich zu Rich-Menü](classic-versus-rich-menu.md).

## <a name="related-topics"></a>Verwandte Themen


[WPA Quick Start-Handbuch](wpa-quick-start-guide.md)

 

 







