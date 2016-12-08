---
title: "Packen Sie einen Auftrag aus, und führen es auf einem anderen Computer aus"
description: "Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen computer"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e4271d06-2f50-44d2-b073-bf72b4d37d99
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 6f8aecaa310f438245ec0fba509bfd783a736e94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="package-a-job-and-run-it-on-another-computer"></a>Packen Sie einen Auftrag und führen Sie es auf einem anderen computer


Wenn Sie einen Auftrag zu Sie auf einem anderen Computer ausführen möchten erstellen, müssen Sie das Windows Assessment Toolkit auf diesem Computer installiert. Die Windows-Assessment-Konsole können Sie die Löschung Paket zusammenzufassen, sodass sie alle erforderlichen Dateien und Tools zum Ausführen auf einem anderen Computer enthält.

**Wichtige**  
Ein gepackte Auftrag kann von einer Netzwerkfreigabe, aber für die besten Ergebnisse erzielen, führen Sie den Auftrag aus dem lokalen Computer, um Laufzeitfehler zu reduzieren oder Leistungsprobleme durch das Netzwerk ausgeführt werden.

 

**So packen Sie einen Auftrag zum Ausführen auf einem anderen computer**

1.  Zum Suchen und die Assessment Windows-Konsole zu starten, klicken Sie auf **Start**, geben **Assessment-Konsole**und klicken Sie dann auf **Windows-Assessment-Konsole**.

2.  Wählen Sie in der Windows-Assessment-Konsole einen Auftrag aus **der Homepage** , wählen Sie eine einzelne Bewertung, Erstellen eines neuen Auftrags oder einen vorhandenen Auftrag zu öffnen.

3.  Nachdem Sie den Auftrag öffnen, passen Sie die Einstellungen und je nach Bedarf die Assessment-Parameter.

4.  Klicken Sie auf **Paket**.

5.  Geben Sie in das Dialogfeld **Paket einen Auftrag zum Ausführen auf einem anderen Computer** Notizen, mit denen Sie Ihre Arbeit zu ermitteln, wenn Sie Ergebnisse zu öffnen und anzeigen auswählen.

6.  Geben Sie im Feld **Pfad für das Paket** den Speicherort, in der Sie das Paket Auftrag speichern möchten. Kann diesen Speicherort auf dem lokalen Computer sein, oder Wechselmedium wie einem USB flash-Laufwerk.

7.  Geben Sie im Feld **Pfad** den Speicherort, in der Sie die Ergebnisse speichern möchten. In der Standardeinstellung ist dies der relative Pfad des einer \\Ergebnisordner am selben Speicherort, in dem der Auftrag ausgeführt wird.

8.  Klicken Sie auf **OK**.

    Wenn der Auftrag verpackt wurde, wird der Speicherort des Auftrags geöffnet. Sie können den Ordner auf einen anderen Computer und Ausführung des Auftrags ohne Installation von der Windows-Toolkit zur Bewertung mithilfe der RunJob.cmd-Datei, die in dem Ordner befindet.

**Zum Ausführen eines gepackten Auftrags auf einem anderen computer**

1.  Übernehmen Sie den Ordner mit den gepackte Auftrag an dem Computer, auf dem den Auftrag ausgeführt werden soll.

2.  Öffnen Sie den Ordner, und doppelklicken Sie auf die Datei **RunJob.cmd** .

3.  Klicken Sie im **Benutzerkontensteuerung**auf **Ja**.

4.  Klicken Sie im Fenster **Assessment Launcher** fügen Sie ausführen Notizen hinzu.

5.  Geben Sie im Feld **Pfad** einen neuen Speicherort sollten Sie den Speicherort zu ändern, der beim Erstellen des Auftrags verpackt wurde angegeben wurde.

6.  Klicken Sie auf **Auftrag auf diesem Computer ausführen**.

7.  Wenn das **Microsoft Assessment-Start** -Fenster angezeigt wird, können Sie den Auftrag abbrechen oder klicken Sie auf **Details** , um den Status des Auftrags überwachen.

    **Hinweis**  
    Für einige Bewertung sehen Sie das Fenster **Assessment Startprogramm** kurz, aber es nicht für die Überwachung der Auftrag beibehalten.

     

8.  Bevor der Auftrag gestartet wird, überprüft der Auftrag die Computerkonfiguration, um sicherzustellen, dass die Bewertung erfolgreich ausgeführt werden kann. Der Auftrag generiert Fehlermeldungen, Warnungen und informative Nachrichten basierend auf der Computerkonfiguration als auch den Anforderungen der Bewertung.

9.  Wenn der Auftrag abgeschlossen ist, wird die Ergebnisse in der Windows-Assessment-Konsole angezeigt und werden gespeichert, der \\Ergebnisse-Ordner, den Sie angegeben haben.

Nachdem Sie einen Auftrag auf einem anderen Computer ausführen können Sie importieren die Ergebnisse in der Bibliothek Ergebnisse auf dem Computer, auf dem die Windows-Assessment-Konsole installiert ist, und vergleichen Sie die Ergebnisse auf mehreren Computern.

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien Windows Assessment-Konsole](windows-assessment-console-common-scenarios.md)

[Windows-Assessment-Konsole](windows-assessment-console.md)

[Vergleich der Ergebnisse](compare-results.md)

[Importergebnisse](import-results.md)

 

 







