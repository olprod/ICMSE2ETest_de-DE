---
title: Vergleichsanalyse Ansichten
description: Vergleichsanalyse Ansichten
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3716cc38-b6f6-45bc-8a9d-e9fbc5076005
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 44fd79c0666cddc6f33d8ab18e7d183fd7f4311c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="comparative-analysis-views"></a>Vergleichsanalyse Ansichten


Beim Analysieren der Systemleistung ist es sinnvoll, in regelmäßigen Abständen Spuren erstellen, die zum Identifizieren der Quellen von Regressionstests verwendet werden kann. Beispielsweise können Sie eine geplante Verfolgung sofortige erstellen nach der Installation eines Betriebssystems. Sie können später nach der Installation von zusätzlichen Applications, Treiber oder Hardware, erstellen eine andere Trace und bestimmen, wie die Änderungen die Systemleistung beeinträchtigen.

In WPA enthielt zuvor jeder Registerkarte Informationen zu nur eine Trace an. Zum Vergleichen von zwei ablaufverfolgungen müssten Sie entweder zwischen Registerkarten wechseln oder jede Trace in einer eigenen Instanz des WPA zu öffnen.

Sie können die Ergebnisse der beiden Spuren jetzt Erstellen einer *Ansicht Vergleichsanalyse*vergleichen. In dieser Ansicht können Sie Bereiche auf einfache Weise ermitteln, wobei Leistung beeinträchtigt wurde wurde durch Hervorheben der Unterschiede zwischen der Spuren.

In einer Ansicht Vergleichsanalyse erstellt WPA eine Tabelle: Vergleich der, die die Unterschiede zwischen den beiden Spuren enthält. Einen Trace wird als eine *Baseline Trace*, in der Regel eine Verfolgung, die vor der Hardware erfasst wird angegeben, oder Software geändert werden. Der anderen Trace wird aufgerufen, die *Vergleich Trace*, Trace erfasst werden, wenn das System geändert wurden.

Die Tabelle, die erstellt WPA enthält den Wert Unterschiede zwischen der Basislinie und Vergleich Spuren (Vergleichswert – Baselinewert). Wenn eine Metrik im Vergleich Trace höher ist, wird die Differenz als eine positive Zahl angezeigt. Wenn die Anzahl die in der Verfolgung der Baseline höher ist, wird die Differenz als auch eine negative Zahl angezeigt. Ein Beispiel ist unten aufgeführt:

![mehr CPU-Aktivität im Vergleich trace](images/acm-wpa-diff-4.png)

**Bild 1:** Positive Zahlen in der Tabelle hervor, dass diese Prozesse in der Verfolgung der Vergleich mehr aktiv waren. Negative Zahlen würde laut der Prozesse in der Verfolgung der Baseline mehr aktiv waren.

**Hinweis**  
Obwohl Sie eine beliebige Anzahl von Spuren in einer einzigen Sitzung WPA geöffnet haben können, kann WPA die Ergebnisse nur zwei Spuren zu einem Zeitpunkt vergleichen.

 

## <a name="creating-a-comparative-analysis-view"></a>Erstellen einer Ansicht Vergleichsanalyse


1.  Öffnen Sie in WPA die erste Verfolgung durch Auswählen von **Datei**, **Öffnen**, Navigieren zum Speicherort der Trace und Auswählen der Option **OK**.

2.  Öffnen Sie den zweiten Trace mithilfe der Methode in Schritt 1.

    **Hinweis**  
    Um Unterscheidung open Spuren weist WPA jedes Trace ein eindeutiger Bezeichner und eine Farbe. In der **Grafik Explorer** -Fenster auf der linken Seite können Sie zwischen der open Spuren mithilfe der Registerkarten am unteren wechseln.

     

    ![mehrere open Spuren mit Registerkarten](images/acm-wpa-diff-1.png)

    **Bild 2:** Jede Trace wird durch eine eindeutige ID und eine Farbe dargestellt.

3.  Erstellen Sie eine neue Ansicht Vergleichsanalyse durch **Fenster** **Neue Marktanteilen Analysis-Ansicht**auswählen.

4.  Wählen Sie in der neuen Registerkarte die Basislinie und Vergleich Spuren wählen sie in der **Baseline:** und **Vergleich:** Listenfelder, und wählen Sie **Weiter** auf der rechten Seite.

    ![Auswählen der Basislinie und Vergleich Spuren](images/acm-wpa-diff-2.png)

    **Bild 3:** Auswählen der Basislinie und Vergleich Spuren.

Nachdem Sie **Weiter**auswählen, wird WPA eine neue Registerkarte **Vergleichsanalyse** im Bereich **Analysis** erstellt. Klicken Sie auf der linken Seite der Registerkarte ist ein Bild, das zeigt, die beiden Spuren verwendet, um die Ansicht Vergleichsanalyse erstellen. Die linke Hälfte des Bilds repräsentiert die Baseline-Ablaufverfolgung der rechten Bildschirmseite angegeben Trace Vergleich.

![Registerkarte mit mehreren farbige Vergleichsanalyse](images/acm-wpa-diff-3.png)

**Abbildung 4:** Eine Vergleichsanalyse Registerkarte angezeigt, Trace 1 dient als eine geplante Verfolgung und Trace 2 wird ein Vergleich Trace verwendet.

WPA können auch eine Ansicht Vergleichsanalyse zum Vergleichen von zwei Abschnitte mit der gleichen Trace-erstellen. Wählen Sie hierzu müssen Sie beim Erstellen der Ansicht Vergleichsanalyse gleichen Trace für die Baseline und die Spuren Vergleich aus.

## <a name="analyzing-a-comparative-analysis-view"></a>Analysieren einer Vergleichsanalyse-Ansicht


Klicken Sie beim Anzeigen eines der ablaufverfolgungen, ziehen Sie ein Diagramm relevanten aus dem **Diagramm Explorer** -Bereich auf die **Analysis** -Bereich in der Mitte aus. Stellen Sie sicher, dass das Diagramm und die Tabelle angezeigt werden, indem Sie auf die Schaltfläche **Diagramm und Tabelle anzeigen** in der oberen rechten Ecke des Bereichs.

Der Diagrammbereich enthält Informationen zu nur eine Trace zu einem Zeitpunkt. Zoom-wie bei Single-Trace-Analyse auf eine bestimmte Zeitspanne durch Hervorheben eines Bereichs, mit der rechten Maustaste, und den Befehl **Zoom (engl.)**. Die Tabelle enthält Daten nur aus der aktuellen vergrößert Zeitspannen für die Verfolgung.

Um unterschiedliche Bereiche der Zeit aus der Basislinie und Vergleich Spuren zu vergleichen, verwenden Sie die Umschaltfläche in der unteren linken Ecke des Bereichs. Diese Funktion schaltet die Ablaufverfolgungsinformationen aktiv ist, damit Sie auf die verschiedenen Bereiche in das Diagramm für jeden Trace vergrößern können. Nach dem Vergrößern an eine Region in einen Trace können Sie in den anderen Trace wechseln und WPA hervorgehoben derselben vergrößerte Region auf derselben Zeitspanne für beide Zoomen ermöglicht.

![Verwenden Sie die Umschaltfläche zum Umschalten zwischen open ablaufverfolgungen](images/acm-wpa-diff-5.png)

**Bild 5:** Verwenden Sie die Umschaltfläche, um zwischen open Spuren wechseln.

Nun, dass es auf einen Bereich in jedem Trace vergrößert haben, benötigen wir nicht mehr die Diagrammansicht. Tabelle nur eine Ansicht wechseln Sie, indem Sie auf die Schaltfläche **zeigt die Tabelle nur** in der oberen rechten Ecke des Bereichs. Die Tabelle enthält Vergleichsinformationen zum anhand der vergrößert Zeitspannen von beide. Numerische Werte werden als Unterschiede zwischen den Vergleich Trace-Werten und Werte der Baseline Trace (Vergleichswert – Baselinewert) berechnet. In **Abbildung 1** oben zeigt die **CPU-Auslastung (abgetastete)** -Tabelle, dass mehrere Prozesse in der Verfolgung der Vergleich mehr aktiv waren.

## <a name="using-profiles-with-comparative-analysis-views"></a>Verwenden von Benutzerprofilen mit Vergleichsanalyse Ansichten


Sie können auch ein Profil anwenden, die eine Ansicht Vergleichsanalyse auf zwei open ablaufverfolgungen enthält:

1.  Klicken Sie im Menü Wählen Sie **Profile**, **anwenden**.

2.  Wenn Sie ein benutzerdefiniertes Profil haben, wählen Sie **Durchsuchen...**, wählen Sie Ihr Profil und wählen Sie dann auf **Öffnen**.

    **Hinweis**  
    Sie können auch im Lieferumfang von WPA ein Profil Vergleichsanalyse ermöglicht den schnellen Einstieg Analyse können Sie verwenden. Dieses Profil verwenden, wählen die Option **Katalog durchsuchen**und wählen Sie die Datei **PresetsForComparativeAnalysis.wpaProfile** .

     

3.  Wählen Sie die entsprechenden ablaufverfolgungen für **Profile Trace Steckplatz \#1** und **Profil Trace Steckplatz \#2**.

4.  Wählen Sie **Übernehmen** für das Profil anzuwenden.

 

 






