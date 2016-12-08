---
title: Was ist neu in Windows Performance Toolkit
description: Was ist neu in Windows Performance Toolkit
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3e27707c-fcba-4052-8cd9-bd04760b7439
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1cd94adaaccae6449803205a6a63722f0bf3deda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-the-windows-performance-toolkit"></a>Was ist neu in Windows Performance Toolkit


Windows Performance Analyzer (WPA) Visualisierung Spuren von Windows Performance Aufzeichnung und Windows-Assessment-Konsole als Diagramme und Tabellen, damit Sie System- und Anwendungsleistung analysieren können. WPA bietet die folgenden neuen Features:

-   Analyse-Assistent-Bereich, hilfreiche Inhalte können Sie bestimmen, wie Sie einer bestimmten Grafik, Voreinstellung oder Analysis Registerkarte am besten mit angezeigt. Rich-Text-Unterstützung für die Analysis-Assistenten, mit der Sie, formatieren Sie den Text zu lesen und analysieren sowie Hinzufügen von Links zu Referenzmaterial, Videos und ausführlichere Hilfeseiten im Web erleichtern.

-   [Liste der WPA Diagramme](list-of-wpa-graphs.md) für den Verweis

-   Neue Version des [im Menü Datei](introduction-to-the-wpa-user-interface.md) (gewählte Rich Menü) mit der Option, wechseln Sie wieder zum klassischen Menü

-   Zeigen Sie in Zeit [Rechteck Viewer](how-to-use-the-rectangle-viewer.md) , mit dem Sie zum visualisieren, wo auf dem Bildschirm während Ihrer trace

-   [Bereiche von Interesse](regions-of-interest.md) , die Sie zum Hervorheben von wichtigen Zeiträume in einer Ablaufverfolgung für zulassen

-   [Stack-Tags](stack-tags.md) zum Erstellen von Beschriftungen, die Ihnen helfen Sie uns bei identifizieren, welche Teile der der Anruf Stack(s) betroffen sind

-   Unterstützung für mehrere ablaufverfolgungen in einer einzigen Sitzung

-   Unterstützung für die Wiederherstellung eines Profils

Windows Performance Aufzeichnung (WPR) ist eine Performance-Tool, das Sie zum Erfassen Systemereignisse, die Sie anschließend analysieren können mithilfe von WPA verwenden können. WPR bietet die folgenden neuen Features:

-   Nach der Aufzeichnung einer Verfolgung, können Sie jetzt unmittelbar es WPA Öffnen durch Auswählen der Schaltfläche **in WPA öffnen** .

-   Leiten Sie Behandlung von CLR-Symbole, damit keine Flags beim Konfigurieren und Verwenden von [NGEN unterstützen](using-clr-40-ngen-pdb-support.md) erforderlich sind

Der Kernel Trace-Steuerelement API-Referenz wird die Kernel Trace-Steuerelement API verfügbar in früheren Versionen von WPA behandelt. Diese API ist eine Erweiterung der ETA Ereignis Tracing API und wird für die Abwärtskompatibilität mit vorhandenen Skripts und Profile unterstützt. Jedoch ist veraltet und neue Profile mithilfe der aktuellen Version erstellt werden soll. Es ist keine öffentliche API für die aktuelle Version von WPA verfügbar. Diese API ermöglicht das Erfassen von Kernel-Stapel Spuren, Zusammenführen mehrerer Tracedateien für die Analyse und einschließlich Systeminformationen in die zusammengeführten Dateien. Von Zeit zu Zeit werden Funktionen hinzugefügt oder aktualisiert. Dieses Referenzdokument fügt die folgenden neuen Funktionen:

-   [StartHeapTrace](startheaptrace.md)

-   [UpdateHeapTrace](updateheaptrace.md)

## <a name="related-topics"></a>Verwandte Themen


[Windows Performance Toolkit technische Referenz](windows-performance-toolkit-technical-reference.md)

 

 







