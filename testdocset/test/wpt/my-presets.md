---
title: Meine Vorgaben
description: Beschreibt das Fenster Meine Vorgaben in WPA an.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8d3652d09c4e01a873d099a7867abe6564bef755
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="my-presets"></a>Meine Vorgaben

WPA speichert die Vorgaben, die geändert oder explizit gespeichert und im Fenster **Meine Vorgaben** angezeigt, damit Sie sie auf einfache Weise wiederverwenden können. **Meine Vorgaben** besteht aus einer Symbolleiste und Struktur an. Der Inhalt des Fensters wird gemeinsam verwendet werden, über die Verwendung von WPA und über gleichzeitig geöffneten Instanzen (mit Ausnahme von ungespeicherten Vorgaben nicht über geöffneten Instanzen gemeinsam verwendet werden).

![WPA Fenster mit Meine Vorgaben auf der rechten Seite angezeigt.](images/my-presets.png)

Die Strukturanzeige enthält einen Eintrag für Ihre gespeicherten oder geänderten Vorgaben. Unter diesem Eintrag werden die Vorgaben durch das Diagramm gruppiert sie stammen. Neben einer Voreinstellung Namen Sternchen gibt an, dass es geändert aber nicht gespeichert wurde. Ein grau gibt nicht verfügbar Namen an, dass der aktuelle Trace keine Daten für das entsprechende Diagramm enthält. Nach dem Anwenden eines Profils an, enthält dass Profil in einem gesonderten Eintrag, zusammen mit den Diagrammen angezeigt wird und bewirkt, dass es.

Sie können die Befehle für Voreinstellungen auf der Symbolleiste oder eine Voreinstellung mit der rechten Maustaste, und klicken Sie dann auswählen eine Option in der folgenden Tabelle beschriebenen zugreifen.

| Option | Beschreibung |
|---|---|
| **Import** | Importiert Vorgaben aus einer Vorgaben (. WpaPresets) Datei oder open Vorgaben von einem Profil (. WpaProfile) Datei. |
| **Exportieren** | Die ausgewählten Vorgaben exportiert in eine Datei, damit Sie die Vorgaben freigeben können. Die Datei hat die Erweiterung *. WpaPresets*. |
| **Speichern** | Speichert den aktuellen Status der Voreinstellung an. Wenn die Voreinstellung handelt es sich um eine integrierte-Vorgabe wurde geändert und dann WPA ein Dialogfeld **Speichern** unter wird angezeigt, weil die Vorgaben nicht überschrieben werden können. Beachten Sie, die Wenn mehrere Instanzen der gleichen Voreinstellung öffnen, werden die zuletzt Instanz geändert wird gespeichert. |
| **Anwenden** | Gilt die Voreinstellung in der zuletzt verwendeten **Analyse** oder **Vergleichende Analyseansicht**. Sie können auch eine Vorgabe anwenden, durch Doppelklicken auf seinen Namen. |
| **Löschen** | Löscht die Voreinstellung aus dieser Ansicht, und alle Instanzen von diese Vorgaben, die in einem Diagramm geöffnet sind umstellen. |
<br/>

Die Vorgaben in dieser Ansicht bleiben Sie mit den nicht standardmäßigen Vorgaben für jedes Diagramm (Zugriff durch das Dropdown-Menü neben dem Namen Trace open grafisch) synchronisiert. Speichern, ändern oder Löschen einer Voreinstellung an einem Ort wirkt sich auf der anderen.
