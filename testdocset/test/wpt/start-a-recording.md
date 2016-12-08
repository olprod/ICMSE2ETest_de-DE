---
title: Starten einer Aufzeichnungs
description: Starten einer Aufzeichnungs
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a873691c-d198-4131-aa5d-849b4c6159d7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c5fc78b926e184cf0bf189ee9bec9264fa7e41f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start-a-recording"></a>Starten einer Aufzeichnungs


Dieses Verfahren beschreibt eine Aufzeichnung Windows Performance Aufzeichnung (WPR) aus der Benutzeroberfläche (UI) zu starten. Informationen zum Starten eine Aufzeichnung über die Befehlszeile finden Sie unter [WPR Command-Line Options](wpr-command-line-options.md).

WPR erfordert Windows 7 oder höhere Version des Betriebssystems.

**Um eine Aufzeichnung starten**

1.  Klicken Sie auf **der Startseite** auf **Windows Performance Aufzeichnung**.

2.  Wenn Sie das Standardprofil ausgeführt werden soll, klicken Sie auf **Start**. Oder, um anzuzeigen, und verwenden Sie andere Profile, klicken Sie auf **Weitere Optionen**.

    1.  Wählen Sie im Feld **Profile für Leistung Aufzeichnung** über mindestens ein Profil.

    2.  Optional können Sie ein benutzerdefiniertes Profil hinzufügen. Hierzu klicken Sie auf **Profile hinzufügen**, navigieren Sie zu die gewünschte Profil und klicken Sie dann auf **Öffnen**. Wählen Sie unter **benutzerdefinierte Maßeinheiten**das Profil.

    3.  Wählen Sie aus der Dropdownliste **Leistung Szenario** das Szenario, das Sie möchten. Wenn ein Szenario ein-/ausschalten die Aufzeichnung ist, wählen Sie **Allgemein**aus.

    4.  Sie können optional auf der Ebene der Beleuchtung Detail aufzeichnen. (**Verbose** ist die default.level.) Hierzu wählen Sie in der Dropdownliste **Detailstufe** **Licht** .

    5.  Um die Aufzeichnung in einer Datei protokollieren, wählen Sie in der Dropdownliste **Protokollierung Modus** **Datei** . **Arbeitsspeicher** ist der Standard Protokollierungsmodus, mit Ausnahme von ein-/ausschalten Übergang-Protokollen, in denen in einer Datei protokolliert werden müssen ein.

        **Vorsicht**  
        Wählen Sie für mehr Aufzeichnungen **Arbeitsspeicher**. Wenn Sie die **Datei**auswählen, kann die Datei sehr groß werden, da die einzige Einschränkung auf die Dateigröße der verfügbare Speicherplatz ist. Windows Performance Analyzer (WPA) können nicht sehr große Dateien analysieren.

         

3.  Klicken Sie auf **Starten** , um die Aufzeichnung zu beginnen, oder klicken Sie auf **Abbrechen** , um ohne Aufzeichnung beenden.

**Hinweis**  
Wenn Sie während einer anderen Anwendung (wie Xperf oder eine Anwendung, NT Kernel-Protokollierung, wie Logman oder PerfTrace verwendet) aufzeichnet WPR starten, WPR wird nicht sofort erkennen, dass eine Aufzeichnung erfolgt, und es werden zunächst eine Meldung angezeigt, dass die Aufzeichnung nicht gestartet wurde. Jedoch, wenn Sie versuchen, eine Aufzeichnung in WPR während der Zeit zu starten, die einer anderen Anwendung aufzeichnet, WPR einen Konflikt erkennt und fordert Sie mit der folgenden Abfrage:

`An existing session is already running. Click OK to stop the running session and start the selected profile(s) or Cancel to abort the operation.`

Klicken Sie auf **OK**, um die aktuelle Sitzung zu beenden. WPR wird gestartet, um aufzuzeichnen. Beachten Sie, dass diese Aktion die Anwendung auswirken kann, die die abgebrochene Sitzung gestartet hat. Wenn die aktuelle Sitzung, um den Vorgang fortzusetzen zulassen möchten, klicken Sie auf **Abbrechen**. In diesem Fall WPR keine Aufzeichnung gestartet, und die andere Anwendung ist nicht betroffen.

 

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

[Aufzeichnung für die Diagnose von grundlegenden System](recording-for-basic-system-diagnosis.md)

 

 







