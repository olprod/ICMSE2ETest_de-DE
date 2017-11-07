---
title: Stack-Tags
description: "In der Windows® Performance Analyzer (WPA) Stack Tags ist ein Feature, das Sie Beschriftungen (-Tags), die Sie unterstützen eine bessere erstellen kann ermitteln, welche Teile der der Anruf Stack(s) betroffen sind."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 07FACEE4-E906-4267-BF48-5C3D590F67C3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a003865887b4c73a2c8552196daa35e916016cdc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stack-tags"></a>Stack-Tags


In Windows® Performance Analyzer (WPA) Stack Tags ist ein Feature, das Sie Etiketten (-Tags), mit denen Sie eine bessere erstellen kann ermitteln, welche Teile der der Anruf Stack(s) betroffen sind.

## <a name="understanding-differences-between-stack-tags-and-stack-frame-tags"></a>Grundlegendes zu den Unterschieden zwischen Stapel und Stack-Frame-tags


Sie können als zwei Ansichten derselben Daten in der Spalte **Stack** verfügbaren **Stapel (Frame-Tags)** und **Stack** Tags vorstellen. Konfigurieren Sie eine Spalte ein Stapel als Stack Tag oder Stack Spalte (Frame-Tag) im Ansicht-Editor angezeigt werden.

Eine Aufrufliste besteht aus einer Liste von Frames. Wenn eine Aufrufliste in Form eines A - ist&gt; B -&gt; C, sind drei Frames: A, B und c Stack Spalten (Frame-Tags) zuordnen jeder Anruf Stack Frame an einem Tag oder wird standardmäßig auf *Modul*! *Methode* , wenn kein Tag vorhanden ist.

Rufen Sie beispielsweise Stack-A -&gt; B -&gt; C -&gt; D, in der Ansicht **Stapel (Frame-Tags)** kann werden A -&gt; FrameTagB -&gt; FrameTagC -&gt; D. Jeweils die Frame-Tags kann eine Hierarchie basierend auf der Definition der Tags in der Hierarchie verwendet die \*.stacktags-Datei (Istwert des FrameTagB kann beispielsweise "HTML\\Skript\\OM").

Ein Tag Stapel sind eine ganze Aufrufliste mithilfe eines einzelnen Tags namens zusammengefasst. Beispielsweise unten wird die meisten zugeordneten Frame-Tag normalerweise das Tag Stack hergestellt, es sei denn Priorität für Tags angegeben. Verwenden Sie das gleiche A -&gt; B -&gt; C -&gt; D Beispiel, in dem Frame-Tag-Ansicht eine ist -&gt; FrameTagB -&gt; FrameTagC -&gt; D, Stack-Tag-Ansicht ist nur: FrameTagC.

Neben dem normalen Tag für genau übereinstimmenden Modul- und -Methode können Sie auch HintTag mit HintOperator als angerufenen oder Anrufer definieren. Eine HintTag mit HintOperator als angerufenen ist beispielsweise für b definiert. Die Aufrufliste A -&gt; B -&gt; C -&gt; D in der Ansicht **Stapel (FrameTags)** kann werden A -&gt; FrameTagB -&gt; ModuleOfC -&gt; D und dessen StackTag Ansicht ist FrameTagB -&gt; ModuleOfC. Das Modul c wird als ein neues Tag Stapel dynamisch erstellt. Das *OnlyShowModule* -Attribut des HintTag explizit als False festlegen, würde C ein neues Stack Tag, sondern als ModuleOfC stellen. *OnlyShowModule* Attribut ist standardmäßig auf true. Die Standardverwendung Groß-/Kleinschreibung werden automatisch Attribut RPC-Server-Funktionen. Die direkte Aufrufer-Funktion ist rpcrt4.dll! Rufen Sie\_epilog1\_starten. Sie können eine HintTag für diese Funktion für allgemeine Anrufer zu diesem Zweck definieren.


## <a name="identify-the-cost-of-a-common-function-by-defining-a-hint-tag"></a>Identifizieren der Kosten für eine allgemeine Funktion durch die Definition eines Hinweis-Tags

In der Regel identifiziert die **Stack-Tag** -Spalte die Kosten für eine einzige Funktion in einem einzigen Modul. WPA kann jedoch die Kosten Ofall der Funktionen von dieser Funktion aufgerufen wird, wenn Sie ein *Hinweis Tag* und ein *Hinweis Operator*definieren konsolidieren. Das Tag Hint ist eine Beschriftung für die allgemeine-Funktion und der Gruppe der Funktionen, die es aufruft und Operators Hint allgemeine Funktion als die aufrufende Funktion, die *Anrufer*oder Funktionsaufruf *angerufenen*identifiziert.

Die typische Verwendung Groß-/Kleinschreibung ist ein Hinweis Tag definieren, sodass WPA automatisch RPC-Server-Funktionen Attribute. Sie sollten auch ein Hinweis-Tag, beispielsweise zu definieren, zeigen Sie die Sperre Inhaber oder die Funktionen, die Heaps zuordnen.

### <a name="defining-hint-tags"></a>Hinweis Tags definieren

Hinweis Kategorien und Hint Operatoren sind in XML in der folgenden Syntax mit die Attribute und Werte in der folgenden Tabelle beschriebenen definiert.

<pre>
    &lt;HintTag Name = "<i>Zeichenfolge Bezeichnung</i>" Priorität = "<i>ganze Zahl</i>" HintOperator = "<i>Anrufer oder angerufenen</i>" OnlyShowModule = "<i>Boolean</i>"&gt;
        &lt;Einstiegspunkt Modul = "<i>Modulnamen</i>"-Methode = "<i>Methodennamen</i>" /&gt;
    &lt;/HintTag&gt;
</pre>

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Attribut</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<th rowspan="4">HintTag</th>
<td><i>Name</i></td>
<td>Die Zeichenfolge, die als Beschriftung verwendet werden</td>
</tr>
<tr class="even">

<td><i>Priorität</i></td>
<td>Ganzzahl Standardwert ist 0 (null).</td>
</tr>
<tr class="odd">

<td><i>HintOperator</i></td>
<td>Wert ist &quot;Anrufer&quot; oder &quot;angerufenen&quot; für das aufrufende oder Funktion, jeweils aufgerufen.</td>
</tr>
<tr class="even">

<td><i>OnlyShowModule</i></td>
<td>Boolescher Wert, optional. Standardwert ist true.</td>
</tr>
<tr class="odd">
<th rowspan="2">Einstiegspunkt</th>
<td><i>Modul</i></td>
<td>Name des Moduls, die <i>Methode</i>enthält.</td>
</tr>
<tr class="even">

<td><i>Methode</i></td>
<td>Der Name der Methode, die der Einstiegspunkt ist.</td>
</tr>
</tbody>
</table>

Verwenden Sie das Verfahren, um die Tags Hint hinzufügen, die Sie in eine XML-Datei definiert haben, in die [Hinzufügen-Stapel-Tags der Stack Tags-Definitionsdatei](#adding-stack-tags-to-the-stack-tags-definition-file), weiter unten in diesem Thema.

### <a name="example-of-using-a-hint-tag"></a>Beispiel mit einem-Tag hint

Berücksichtigen Sie die Beispielsdaten in der folgenden Abbildung dargestellt.

<a href="images/wpa-hint-tag-example-1.jpg"><img src="images/wpa-hint-tag-example-1.jpg"></a>

In diesem Beispiel sind 4 RPC-Funktionen in WbemCore.dll aufgerufen:

-   **CWbemLevel1Login::NTLMLogin**
-   **CWbemNamespace::GetObjectW**
-   **CWbemNamespace::PutInstance**
-   **CWbemNamespace::ExecMethod**

Konsolidieren Sie die Kosten für den Aufruf dieser Funktionen ist nützlich, um die Kosten der RPC-Server-Side-Funktionen zu bestimmen, da WPA insgesamt Ausgaben als **RPC** in der Spalte **Stack Tag** angezeigt wird.

Mit der **rpcrt4.dll! Rufen Sie** Funktion als Einstiegspunkt für das Tag Hint **RPC**definiert und der Operator Hint angegeben, als der aufgerufene WPA stellt **rpcrt4.dll! Rufen Sie** mit **RPC**und **wbemcore.dll! CWbemLevel1Login::NTLMLogin** mit **RPC\\wbemcore.dll\\CWbemLevel1Login::NTLMLogin**. In der Spalte **Stack Tag** zeigt WPA also die Kosten der **wbemcore.dll! CWbemLevel1Login::NTLMLogin**, RPC-Server-Side-Funktion als 31.855774ms. In WbemCore.dll ist **NTLMLogin** die oberste RPC-Funktion in der Hierarchie der aufgerufenen Funktionen.

Das Tag Hint **RPC** wird durch den folgenden XML-CODE definiert.

<pre>
    &lt;HintTag Name = "RPC" HintOperator = "Angerufenen"&gt;
        &lt;Einstiegspunkt Module="rpcrt4.dll" Methode "Aufrufen" = /&gt;
    &lt;/HintTag&gt;
</pre>


## <a name="adding-stack-tags-to-the-stack-tags-definition-file"></a>Hinzufügen von Stack Tags der Stack Tags-Definitionsdatei

Um eine Stack-Tag-Definition der Definitionsdatei für Stapel Tags hinzuzufügen, führen Sie folgende Schritte aus:

1.  Klicken Sie im Menü Wählen Sie **Trace**, und wählen Sie dann **Trace-Eigenschaften**. Die Registerkarte **Trace-Eigenschaften** wird geöffnet.

2.  Klicken Sie im Bereich Stack Tags Definition an die gewünschte Position auf **Hinzufügen** .

3.  Navigieren Sie zu dem Bereich, der den Stapel enthält Tags Datei, wählen Sie sie aus, und klicken Sie dann auf **Öffnen**.


## <a name="removing-a-stack-tag-from-the-stack-tags-definition-file"></a>Entfernen ein Tag Stack aus der Stack Tags-Definitionsdatei

Um die Definition eines Stack Tag aus der Definitionsdatei für Stapel Tags entfernen möchten, führen Sie folgende Schritte aus:

1.  Klicken Sie im Menü Wählen Sie **Trace**, und wählen Sie dann **Trace-Eigenschaften**. Die Registerkarte **Trace-Eigenschaften** wird geöffnet.

2.  Wählen Sie im Bereich Stack Tags Definition die Definitionen der Stack-Tag, den, die Sie entfernen, und klicken Sie auf **Entfernen**möchten.

    **Warnung**  Stellen Sie sicher, dass Sie die ausgewählten Stapel Tag Definitionen entfernen möchten, da Sie nicht die Option zum Abbrechen, sobald Sie auf **Entfernen**klicken.

     

## <a name="reloading-the-stack-tags-definition-file"></a>Erneutes Laden der Definitionsdatei für Stapel tags


Gehen Sie wie folgt vor, um einen Stapel Tag-Definition der Stack Tags Definitionsdatei erneut zu laden:

1.  Klicken Sie im Menü Wählen Sie **Trace**, und wählen Sie dann **Trace-Eigenschaften**. Die Registerkarte **Trace Eigenschaften** wird geöffnet.

2.  Klicken Sie im Bereich Stack Tags Definition auf **erneut laden**. Sie können mehrere Stapel Tags durch Drücken und die UMSCHALTTASTE gedrückt halten und mit der linken Maustaste jedes Tags-Definition Stapel laden.

## <a name="troubleshooting-your-stack-tags-file"></a>Problembehandlung bei Ihrer Stapeldatei tags


Gehen Sie wie folgt vor, um Probleme innerhalb Ihrer Tags Stapeldatei in WPA zu untersuchen:

-   Klicken Sie im Menü **Fenster**klicken, und wählen Sie dann **Diagnostic Console**. Die Anzeige WPA teilt in zwei - mit der **Grafik Explorer** und **Analyse** in der oberen Hälfte des Bildschirms und der **Diagnostic Console** am unteren Hälfte des Bildschirms.

    **Tipp**  Sie können auch die Diagnose Konsole in der unteren linken Ecke des WPA zugreifen, indem Sie auf **Diagnostic Console**. Nachdem geöffnet ist, können Sie auch ziehen Sie es in einem separaten Fenster skalieren oder oben oder Seite andocken.

    Diagnostic Console enthält Informationen zu Ausnahmen, die während der Analyse Workflows auftreten. Sie können Probleme aus diese Konsole Decodierung Symbol diagnostizieren.

## <a name="related-topics"></a>Verwandte Themen


[Einführung in die WPA-Benutzeroberfläche](introduction-to-the-wpa-user-interface.md)

[Diagnose-Konsole](diagnostic-console.md)

 

 







