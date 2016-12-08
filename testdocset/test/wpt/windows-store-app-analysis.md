---
title: Windows Store-App-Analyse
description: Windows Store-App-Analyse
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
Search.SourceType: Video
ms.assetid: 6643a13f-c164-4fc3-80e3-91ea2b7b8a80
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 7d5af3d93d7af4a61a25d6c2539707082a5d49de
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-store-app-analysis"></a>Windows Store-App-Analyse


WPA umfasst jetzt die Funktionen, die Ihnen helfen Windows Store app Leistung zu analysieren. Das Video unten für einen schnellen Überblick über einige dieser Features:

<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/bf588be3-5aa0-4679-9f00-7dcaa93df127/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

[Senden Sie Feedback zu diesem Video, oder fordern Sie neue Performance Analysis Videos.](mailto:lhdocfb@microsoft.com?subject=HCKTestLevelsVIDEO&body=%0D%0A%0D%0AMicrosoft%20uses%20your%20feedback%20to%20improve%20its%20products,%20services%20and%20documentation.%20While%20we%20are%20investigating%20the%20issue%20you%20report,%20we%20may%20send%20e-mail%20to%20you%20to%20ask%20for%20further%20details%20or%20clarification%20on%20the%20feedback%20you%20send%20to%20us,%20and%20we%20may%20send%20e-mail%20to%20you%20to%20let%20you%20know%20that%20your%20feedback%20has%20been%20addressed.%C2%A0%20We%20do%20not%20use%20your%20e-mail%20address%20for%20any%20other%20purpose.%0D%0AFor%20technical%20support,%20contact%20http://go.microsoft.com/fwlink/?LinkId=143702.%0D%0A%0D%0A%20For%20further%20information%20about%20the%20Microsoft%20Online%20Privacy%20Statement,%20please%20see%20http://go.microsoft.com/fwlink/?LinkId=143701.)

## <a name="windows-store-app-profiles"></a>Windows Store-App-Profile


Diese Methode bietet eine Reihe von Profilen, mit denen Jumpstart Analyse Windows Store-app eine. Diese Profile sind im **Profilkatalog** enthalten, die gefunden werden kann, wenn Sie eine offene Kontur ein Profil zuweisen:

-   AppLaunch – enthält Vorgaben in einer Ansicht, die für die Analyse der app-Start ausgerichtet ist.

-   XAMLApplicationAnalysis – enthält alle Vorgaben und Ansichten zum Einstieg in die Analyse der XAML-basierten Windows Store-app erforderlich.

-   HTMLApplicationAnalysis – enthält alle Vorgaben und Ansichten zum Einstieg in die Analyse der HTML-basierte Windows Store-app erforderlich.

Weitere Informationen hierzu finden Sie unter [Profile anzeigen](view-profiles.md).

Weitere Informationen, einschließlich Videos, in denen die ersten Schritte mit den Windows Store-app Analysis-Profilen finden Sie unter den folgenden Links:

-   [Überblick](big-picture.md)

-   [Frame-Analyse](frame-analysis.md)

## <a name="attributed-cpu-usage"></a>Attributierten CPU-Auslastung


CPU-Auslastung wird im Diagramm **Ergebnisarray als Attribut zugewiesen CPU-Auslastung** verschiedene Aktivitäten zugeordnet. Beispielsweise kann ein Abschnitt der Aktivität zum Zeichnen von Inhalten auf dem Bildschirm, während eine andere Abschnitt für die Verarbeitung von JavaScript-Code Ergebnisarray als Attribut zugewiesen werden kann zugeordnet werden. Diese Tags identifizieren können Sie wie Ihre app Zeit verbringen ist einfacher zu identifizieren.

![Bereiche von Interesse: Grafik](images/acm-wpt-regions-1.png)

Das CPU-Auslastung Ergebnisarray als Attribut zugewiesen Diagramm enthält die folgenden Vorgaben CPU-Auslastung in Ihrer Windows Store-app zerlegen, die:

-   DWM Thread CPU des Ressourcenstrukturplans

-   Rendern von HTML-Thread CPU des Ressourcenstrukturplans

-   HTML-Benutzeroberfläche Thread CPU des Ressourcenstrukturplans

-   Aufschlüsselung der bekannten Thread-CPU

-   Nutzung von Prozess, Thread, Aktivität

-   XAML-Render Thread CPU des Ressourcenstrukturplans

-   XAML-Benutzeroberfläche Thread CPU des Ressourcenstrukturplans

Wenn Sie über die Balken im Diagramm bewegen, sehen Sie zusätzlichen Metadaten für die entsprechende Aktivität.

In der Tabelle **CPU-Auslastung Ergebnisarray als Attribut zugewiesen** kann die Spalte **Name Thread** Sie wichtige Threads in Ihrer app schnell zu identifizieren. Im folgenden Screenshot sehen Sie die **HTML-Benutzeroberflächen-Thread**, einen benannten Thread, die während der **Layout** -Aktivität bearbeitet:

![bekannte Thread cpu des Ressourcenstrukturplans-Tabelle](images/acm-wpt-regions-2.png)

**Warnung**  
Regionen mit Interesse Definitionen zur CPU-Auslastung an verschiedene Aktivitäten-Attribut nutzt die **CPU-Auslastung Ergebnisarray als Attribut zugewiesen** -Tabelle. Wenn Sie mehrere Regionen Dateien verwenden, können unterschiedliche Regionen von Interesse überlappen und in Konflikt stehen. Wenn diese Konflikte auftreten, kann WPA nicht genau eine einzelne Aktivität an einen bestimmten Thread in einem bestimmten Zeitraum Attribut. Um diese mögliche Konflikte zu vermeiden, verwenden Sie nur eine Region-Definitionsdatei zu einem Zeitpunkt.

 

## <a name="thread-naming"></a>Benennen von Threads


Windows Store-apps verwenden unterschiedliche Threads für verschiedene Arten von Arbeit. Beispielsweise übergibt der XAML-UI-Thread Arbeit an die Renderthread zum Zeichnen auf dem Bildschirm. WPA verwendet beschreibenden Threadnamen um eindeutig zu identifizieren, was der Thread tut. Wissen, welche der vielen Threads in der Tabelle ist der Renderthread und ermöglicht das XAML-UI-Thread ist nach bestimmten Mustern Verhalten, insbesondere zwischen Threads suchen.

![beschreibenden Threadnamen in wpa](images/acm-wpa-store-app-analysis-thread-names.png)

Die vorstehende Abbildung zeigt die Aktivität aus der XAML-UI Thread, der Thread XAML rendern und der Thread Desktop Window Manager (DWM).

 

 






