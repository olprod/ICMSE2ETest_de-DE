---
title: Dies ist nur ein Test-Markup
description: Dies ist nur ein Test-Markup
Search.SourceType: 
ms.assetid: 
ms.openlocfilehash: 86c9c37f3a382e9bc9bce3270a172f018ae64811
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lost-space-between-character-formatting-tags"></a>Abstand zwischen Zeichen Tags Formatierung verloren

In diesem Thema nur, um ein Problem veranschaulichen vorhanden ist. Auf dem Stagingserver ist Leerzeichen 0 (null) zwischen dem Schließen und öffnen die Formatierung der Zeichen. Beispielsweise eine der folgenden Zeilen:

```
<b>command -option1</b> <i>parameter</i> <b>-option2</b>
**command -option1** *parameter* **-option2**
```

wird für die Veröffentlichung mit NULL Leerzeichen vor oder nach "Parameter" dargestellt:

<b>Befehl - Option 1</b> <i>Parameter</i> <b>-option2</b>

**Befehl - Option 1** *Parameter* **-option2**

Ist ein Workaround für HTML und Abzugsverteilung(en) hinzufügen ** \&Nbsp;** zwischen den markierten von Zeichenfolgen. Dies wahrscheinlich funktioniert in den meisten Befehlszeilen, aber wäre es nützlicher Leerraum beibehalten, statt verloren haben. Möglicherweise gibt es Situationen, in denen ein geschütztes Leerzeichen wünschenswert nicht zur Verfügung.




