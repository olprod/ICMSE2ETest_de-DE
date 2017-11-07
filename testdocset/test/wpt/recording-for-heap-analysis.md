---
title: "Für die Analyse Heap aufzeichnen"
description: "Für die Analyse Heap aufzeichnen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9acc8558-67ef-471a-af69-1173cb49bdb4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 7d25f9dc4f7a467558aac20da83f5aeb7a5662d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recording-for-heap-analysis"></a>Für die Analyse Heap aufzeichnen


Windows Performance Aufzeichnung (WPR) ermöglicht Heap-Analyse für alle Vorgänge auf dem System.

**So aktivieren Sie Heap Tracing für desktop-app**

1.  Wählen Sie aus dem Dropdown-Menü **Weitere Optionen** das **Heap** Verwendungsprofil.

2.  Hinzufügen ein Registrierungseintrags für den Prozess mithilfe des folgenden Befehls in einem Eingabeaufforderungsfenster mit erhöhten rechten Fenster ersetzen * &lt;Prozess\_Name&gt; * mit dem Namen des Prozesses verfolgt werden sollen:

    **Hinzufügen von Reg "HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options\\&lt;Prozess\_Namen&gt;" / v TracingFlags/t REG\_DWORD/d 1/f**

**So aktivieren Sie Heap Tracing für eine Windows Store-app**

1.  Wählen Sie aus dem Dropdown-Menü **Weitere Optionen** das **Heap** Verwendungsprofil.

2.  Wenn Sie möchten ein Anwendungspaket verfolgen, die in einem Prozess (beispielsweise WWAHost.exe) gehostet wird, fügen Sie einen Registrierungseintrag für den Prozess mithilfe des folgenden Befehls in einem Fenster Eingabeaufforderung mit erhöhten Rechten ersetzen * &lt;Prozess\_Namen&gt;*, * &lt;Paket vollständiger Name&gt;*, und * &lt;Paket relativ app-ID&gt; * mit Ihrer app-Informationen:

    **Hinzufügen von Reg "HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options\\&lt;Prozess\_Namen&gt;\\&lt;Paket vollständiger Name&gt;! &lt;Paket relativ app-ID&gt;"/ v TracingFlags/t REG\_DWORD-WERT/d 1/f**

    **Hinweis**  
    Diese Kombination (Paket vollständiger Name + app-ID) ist keine app Benutzer Modell ID (Familie Paketname + app-ID). Die IFEO Verarbeitung Routinen verwenden den vollständigen Namen, können sie verschiedene Versionen von einem einzelnen Paket-app mit unterschiedlichem Verhalten gilt.

     

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

[Optionen für die Ausführung des Image-Datei](http://go.microsoft.com/fwlink/p/?LinkId=268419)

 

 







