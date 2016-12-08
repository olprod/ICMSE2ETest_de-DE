---
title: Basislinienergebnisse erstellen
description: Basislinienergebnisse erstellen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4aa70366-047d-4381-b592-fe6e66696a9f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 4ee92c55b96572f529555bc0c886840ef88528b6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-baseline-results"></a>Basislinienergebnisse erstellen


In diesem Thema wird beschrieben, wie Bewerten von einem Computer, der eine unveränderte Windows-Abbild installiert ist, und klicken Sie dann Speichern der Ergebnisse in einem externen Laufwerk oder einer Dateifreigabe. In diesem Thema beschrieben klicken Sie dann auf einen Computer mit einer benutzerdefinierten Windows-Abbilds (oder Drittanbieter-Software und Hardware) bewerten und vergleichen Sie die Ergebnisse auf anderen Ergebnisse aus dem gleichen Computer oder einem anderen Computer.

Wir empfehlen dieses Szenario für Original Equipment Manufacturers (OEMs) und System-Builder, die zur Bewertung basislinienergebnisse um zu bestimmen, wie Anpassungen für eine bestimmte Hardwarekonfiguration Systemleistung einrichten möchten.

Allgemeine Informationen dazu, wie Sie mithilfe der Windows-Assessment-Verwaltungskonsole auf einen Computer bewerten finden Sie unter [schrittweise Anleitung für Windows-Assessment-Konsole](windows-assessment-console-step-by-step-guide.md).

**Basislinienergebnisse erstellen**

1.  Installieren Sie eine clean (oder nicht angepasste) Version von Windows 8 oder Windows 10 auf einer bare-Metal-Referenz-Computer. Ein bare-Metal-Referenz-Computer verfügt nicht über ein Betriebssystem oder die Software installiert und die Hardware ist ein Computermodell, das den spezifischen Typ des Computer repräsentiert, die Sie Herstellung oder verkauft werden sollten.

2.  Wenn Windows Setup abgeschlossen ist, herunter, und installieren Sie das Windows Assessment Toolkit aus dem Windows Assessment and Deployment Kit (Windows ADK).

3.  Klicken Sie auf **Start**, geben Sie **Assessment-Konsole**, und klicken Sie dann auf **Windows-Assessment-Konsole**. Die Windows-Konsole Assessment wird geöffnet.

4.  Wählen Sie in der Windows-Assessment-Konsole einen Auftrag aus **der Startseite** , wählen Sie eine Bewertung der einzelne oder Erstellen eines neuen Auftrags. Sie können beispielsweise Erstellen eines neuen Auftrags und verwenden Sie die Vorlage Fertigung und Bereitstellung zur Erkennung von Problemen mit Treiber und Geräte, einschließlich der Anforderungen an das Logo, und Verzögerungen bei der ersten Boot-Erfahrung des Endbenutzers zu identifizieren.

5.  Klicken Sie auf **Optionen**und klicken Sie dann auf **Konfigurieren Ergebnisse**in der oberen rechten Ecke der Windows-Konsole zur Bewertung.

6.  Klicken Sie im Dialogfeld **Assessment Ergebnisse Bibliothek Speicherorte** auf **Hinzufügen**. Das Dialogfeld **Ordner "Include" in Bewertung von Suchergebnissen** wird geöffnet.

7.  Wählen Sie einen Speicherort, in dem Sie Assessment-Ergebnisse für späteren Vergleich, wie etwa einer Netzwerkfreigabe speichern und klicken Sie dann auf **Ordner aufnehmen**können.

    **Wichtige**  
    Sie müssen Speichern der Ergebnisse in einer Netzwerkfreigabe Wenn Sie planen, Windows auf dieser Referenz-Computer neu installieren. Wenn den referenzierten Computer neu abzubilden, die Ergebnisse werden überschrieben und nicht für den Vergleich, wenn sie lokal gespeichert sind.

     

8.  Wählen Sie den Standardspeicherort für das Ergebnis (**"UserProfile" %\\Dokumente\\Assessment Ergebnisse**), und klicken Sie dann auf **Entfernen**.

9.  Stellen Sie sicher, dass der neue Speicherort in der Liste als dem Standardspeicherort angezeigt wird, und klicken Sie dann auf **OK**.

10. Klicken Sie auf **Ausführen** , um Bewerten des Computers zu starten.

11. Wenn das Projekt abgeschlossen ist, werden die Ergebnisse in der Windows-Assessment-Konsole auf der Seite **Ergebnisse anzeigen** angezeigt.

12. Klicken Sie auf der Seite **Ergebnisse anzeigen** auf **Configure Auftrag**.

13. Klicken Sie auf der Seite **Configure Auftrag** in der unteren rechten Ecke auf **Paket**.

14. Geben Sie im Dialogfeld **Paketauftrag** Notizen, mit denen Sie Ihre Arbeit zu identifizieren, wenn Sie die Ergebnisse zu öffnen und anzeigen auswählen.

15. Geben Sie im Feld **Pfad für das Paket** den Speicherort, in der Sie das Paket Auftrag speichern möchten. Diesem Speicherort sollte auf einem Wechselmedium wie ein USB-Laufwerk.

16. Geben Sie im Feld **Pfad** den Speicherort, in der Sie die Ergebnisse speichern möchten. Standardmäßig ist dies der relative Pfad der eine \\Ergebnisordner am selben Speicherort, in dem der Auftrag ausgeführt wird.

17. Klicken Sie auf **OK**.

**Zum Ausführen des gleichen Auftrags auf ein benutzerdefiniertes Windows-Abbild**

1.  Anpassen des Windows-Abbilds und auf dem gleichen Referenz-Computer installiert werden. Weitere Informationen zu Windows-Anpassung und Bereitstellung finden Sie unter [Bereitstellung und Imaging technische Referenz zu Tools](http://go.microsoft.com/fwlink/?LinkId=214548).

2.  Wenn Windows Setup abgeschlossen ist, öffnen Sie den Ordner, in dem Sie den Auftrag gepackten gespeichert, kopieren Sie den Ordner auf dem lokalen Computer, und doppelklicken Sie dann auf die **RunJob.cmd** -Datei, um die gleiche Aufgabe auszuführen, die Sie im vorherigen Verfahren ausgeführt haben.

    **Wichtige**  
    Ein gepackte Auftrag kann von einer Netzwerkfreigabe, jedoch für die besten Ergebnisse erzielen, führen Sie den Auftrag aus dem lokalen Computer, um Laufzeitfehler zu reduzieren oder Leistungsprobleme durch das Netzwerk ausgeführt.

     

3.  Wenn das Projekt abgeschlossen ist, werden die Ergebnisse in der Windows-Assessment-Konsole angezeigt.

**Um die Ergebnisse zu vergleichen.**

1.  In der Windows-Assessment-Konsole auf **Optionen**und klicken Sie dann auf **Open Results**.

2.  Klicken Sie im Fenster **Ergebnisse auswählen** auf **Durchsuchen**.

3.  Navigieren Sie im Datei-Explorer zum Speicherort, in dem die Ergebnisdateien werden gespeichert, wählen Sie aus der XML-Dateien, die Sie und klicken Sie dann auf **Öffnen** , um die Ergebnisse in der Windows-Assessment-Konsole anzuzeigen.

    Wenn Sie mehr als eine Ergebnisdatei auswählen, werden die Ergebnisse nebeneinander in der Windows-Assessment-Konsole angezeigt, sodass Sie auf einfache Weise die Baseline-Ergebnisse an alle nachfolgenden Ergebnisse vergleichen können.

Basierend auf den Vergleich von Ergebnissen, können Sie Verbesserungen an der angepassten Abbilds vornehmen. Sie können weiterhin die führen, überprüfen und Überarbeiten Prozess, bis die Ergebnisse zu erhalten, die Sie möchten.

## <a name="related-topics"></a>Verwandte Themen


[Bewertung](assessments.md)

[Windows-Assessment-Konsole](windows-assessment-console.md)

[Häufige Szenarien Windows Assessment-Konsole](windows-assessment-console-common-scenarios.md)

 

 







