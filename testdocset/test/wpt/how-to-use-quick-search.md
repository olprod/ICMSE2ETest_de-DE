---
title: 'Gewusst wie: Verwenden der Schnellsuche'
description: 'Gewusst wie: Verwenden der Schnellsuche'
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 56F9E3CE-9584-411C-B55F-8E15E1073FAB
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6343de822b3dc29f02f18f529a5d2001ec067e35
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="how-to-use-quick-search"></a>Gewusst wie: Verwenden der Schnellsuche


In Windows Performance Analyzer (WPA) können Sie eine schnelle Suche über alle Zeilen in Datentabellen durchführen. Dies unterscheidet sich von einem regulären Datensuche ([Suche oder Filtern von Daten](search-or-filter-data.md)), dass Sie keinen Suchparameter wie beispielsweise eine Abfrage angeben, den Upgradeprozess (z. B. gleich, nicht gleich oder enthält) oder Filter wie Groß-/Kleinschreibung beachten, bis usw. suchen.

**Hinweis**  Sie können jedoch eine Abfrage aus, um die schnelle Suche Feinabstimmung hinzufügen.

 

**Schnellsuche verwenden**

1.  Klicken Sie auf das Lupensymbol auf der Titelleiste des Diagramms. Ein Popup-Menü wird geöffnet.

2.  Geben Sie den gewünschten Text ein. Bei der Eingabe teilweise Text (beispielsweise Cursorverhalten bei Eintritt CO für COM-Anruf) wird WPA die Daten in allen Zeilen mit dieser Zeichenfolge filtern. Wenn der Text nicht die Daten in den Zeilen übereinstimmt, wird das Feld Rot (, bevor Sie klicken), wenn der Text eingegeben wurde.

3.  Zum Suchen und markieren Sie alle Instanzen des Texts, den Sie angegeben haben, klicken Sie auf **Alle suchen**.

    WPA werden alle Zeilen (in der Tabelle), die Text enthalten, den, die Sie angegeben haben. Wenn eine Zeile nicht mit den Text, den Sie angegeben haben enthält, nicht hervorgehoben, sondern in einer Tabellenzeile bleibt; Dies ist wichtig, da es unterscheidet sich von wie WPA Suchergebnisse zurückgibt, wenn Sie **Filter zu** verwenden, wie in Schritt 4 beschrieben.

4.  Um nur die Instanzen zurückzugeben, die Text enthalten, den, die Sie angegeben haben, klicken Sie auf **Filter**. WPA dann nur zeigt die Zeilen, die eingegebenen Text enthalten und entfernt alle Zeilen, deren Daten nicht eingegebenen Text enthalten.

    WPA zeigt nur die Zeilen, die den Text enthalten, eingegeben und entfernt alle Zeilen, die nicht den Text enthalten, den Sie angegeben haben.

5.  Um die schnelle Suche eine Abfrage und/oder Filter hinzuzufügen, klicken Sie auf **...** , und klicken Sie dann auf **+** ein Dropdown-Liste der Abfragen anzeigen, können Sie hinzufügen.

6.  Verzögerungstyp hinzufügen, klicken Sie auf die Dropdownliste **enthält** aus, wählen Sie die Kriterien, die Sie verwenden möchten (beispielsweise gleich ist, enthält, usw.), und geben Sie die Suchzeichenfolge, die Sie verwenden möchten.
    **Tipp**  Wenn die Verzögerungstyp entfernen möchten, klicken Sie auf das **X** in der Zeile, die Verzögerung enthält (Wenn Sie mehrere verwenden können) Sie löschen möchten. Standardmäßig enthält die Abfrage Verzögerungstyp **enthält**, die Sie auch löschen können.

     

7.  Einwandfrei optimieren Sie Ihre Abfrage, wählen Sie eine der Optionen, wie die Groß-/Kleinschreibung beachten oder in den reduziert Zeilen).
8.  Klicken Sie auf **Alle suchen** , um alle Datenzeilen zu suchen, die Ihre Suchkriterien erfüllen.
9.  Klicken Sie auf **Weitersuchen,** um die nächste Datenzeile suchen, die Ihren Suchkriterien entspricht.
10. Klicken Sie auf **Abbrechen** , um die Abfrage für die Suche nicht enthalten.

## <a name="related-topics"></a>Verwandte Themen


[Suche oder Filtern von Daten](search-or-filter-data.md)

 

 







