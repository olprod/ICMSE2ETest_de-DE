---
author: Justinha
Description: Liste der DISM-Konfiguration und WimScript.ini Dateien
ms.assetid: 8e765558-4138-4215-bf53-09e46666a718
MSHAttr: PreferredLib:/library/windows/hardware
title: Liste der DISM-Konfiguration und WimScript.ini-Dateien
ms.openlocfilehash: 167aaaa7c4c096de29844fb3c27f6499a51b679e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-configuration-list-and-wimscriptini-files"></a>Liste der DISM-Konfiguration und WimScript.ini-Dateien


Das Tool Deployment Image Servicing and Management (DISM) ist ein Befehlszeilentool, das Sie zum Aufzeichnen und Anwenden von Windows-Abbildern verwenden können. Erstellen Sie eine Konfigurationsdatei für die Liste Folgendes bestimmen:

-   Wenn Sie die Option **/Capture-Image** mit dem Tool DISM verwenden, müssen das welche Dateien und Ordner vom Prozess Capture ausgeschlossen werden.

-   Welche Ordner, Dateien und Dateitypen aus der Komprimierung bei werden müssen Sie das Argument **ausgeschlossen/Komprimieren** verwenden.

Das **Argument/ConfigFile** können Sie bestimmte Komprimierung, erfassen und Grenze Ausrichtung Aktionen für alle Dateien und Ordner anpassen, wenn Sie ein Bild mit DISM.exe erfassen. Sie können eine Liste (INI) Konfigurationsdatei mithilfe von einem Text-Editor wie Editor erstellen.

## <a name="span-idcreatingaconfigurationlistfilespanspan-idcreatingaconfigurationlistfilespanspan-idcreatingaconfigurationlistfilespancreating-a-configuration-list-file"></a><span id="Creating_a_Configuration_List_File"></span><span id="creating_a_configuration_list_file"></span><span id="CREATING_A_CONFIGURATION_LIST_FILE"></span>Erstellen einer Konfigurationsdatei für die Liste


In den folgenden Abschnitten werden in der Konfigurationsdatei Liste DISM angezeigt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Abschnitt</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><code>[ExclusionList]</code></p></td>
<td align="left"><p>Ermöglicht Ihnen das Definieren von Dateien und Ordner zum ausschließen, wenn Sie die Option <strong>/Capture-Image</strong> verwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>[ExclusionException]</code></p></td>
<td align="left"><p>Ermöglicht Ihnen die Standardliste Ausschluss überschreiben, wenn Sie die Option <strong>/Capture-Image</strong> verwenden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>[CompressionExclusionList]</code></p></td>
<td align="left"><p>Ermöglicht Ihnen, um bestimmte Dateien und Ordner zu definieren und Angeben der Dateitypen zum ausschließen, wenn Sie das <strong>Argument/Komprimieren</strong> verwenden.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Datei oder Ordner entsprechen können Sie eine Datei aus der Komprimierung ausschließen. Können Sie Übereinstimmung einen vollständigen Pfad angeben, oder Sie können das Platzhalterzeichen (*) verwenden. Können beispielsweise <strong>\WINDOWS\inf\*.pnf</strong> entsprechend ein bestimmtes Typs der Datei, oder <strong>\WINDOWS\inf\* </strong> mit einen ganzen Ordner übereinstimmt.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

### <a name="span-iddefaultexclusionlistspanspan-iddefaultexclusionlistspanspan-iddefaultexclusionlistspandefault-exclusion-list"></a><span id="Default_Exclusion_List"></span><span id="default_exclusion_list"></span><span id="DEFAULT_EXCLUSION_LIST"></span>Standard-Ausschlussliste

Standardmäßig wird das Tool DISM.exe die folgenden Dateien ausschließen.

``` syntax
[ExclusionList]
\$ntfs.log
\hiberfil.sys
\pagefile.sys
\swapfile.sys
"\System Volume Information"
\RECYCLER
\Windows\CSC

[CompressionExclusionList]
*.mp3
*.zip
*.cab
\WINDOWS\inf\*.pnf
```

### <a name="span-idexclusionlistguidelinesspanspan-idexclusionlistguidelinesspanspan-idexclusionlistguidelinesspanexclusion-list-guidelines"></a><span id="Exclusion_List_Guidelines"></span><span id="exclusion_list_guidelines"></span><span id="EXCLUSION_LIST_GUIDELINES"></span>Richtlinien der Ausschlussliste

-   Sie können Platzhalterzeichen nur in der letzten Komponente in einem Dateipfad verwenden, die nicht mit einem umgekehrten Schrägstrich beginnt. Beispiel:

    ``` syntax
    myfolder\*.txt
    ```

-   Sie können einen umgekehrten Schrägstrich Limit-Datei- und Directory-Abgleich relativ zum Stammverzeichnis verwenden. Beispielsweise können Sie diese Ausschlussliste verwenden:

    ``` syntax
    \myfolder
    \folder\subfolder
    ```

    Dieser Liste werden die folgenden Dateien und Verzeichnisse ausschließen, wenn Sie erfassen die "C:\\" Laufwerk:

    ``` syntax
    C:\myfolder
    C:\folder\subfolder
    ```

    DISM wird jedoch nicht ausschließen, Dateien oder Verzeichnisse, die im folgenden Beispiel enthalten sind.

    ``` syntax
    C:\main\myfolder
    C:\data\folder\subfolder
    ```

-   Sie können die Standardliste Ausschluss außer Kraft setzen, mithilfe der `[ExclusionException]` Abschnitt. Beispiel:

    ``` syntax
    [ExclusionException]
    \pagefile.sys
    "\System Volume Information"
    ```

-   Wenn eine explizite `[ExclusionException]` Abschnitt ist, sofern die WIM-Konfigurationsdatei es immer Vorrang, über haben wird die `[Exclusion List]` Abschnitt.

-   Der Standard-Komprimierung Ausschlussliste kann nicht überschrieben werden, mithilfe der `[ExclusionException]` Abschnitt.

## <a name="span-idusingtheconfigurationfilespanspan-idusingtheconfigurationfilespanspan-idusingtheconfigurationfilespanusing-the-configuration-file"></a><span id="Using_the_Configuration_File"></span><span id="using_the_configuration_file"></span><span id="USING_THE_CONFIGURATION_FILE"></span>Mithilfe der Konfigurationsdatei


Wenn Sie eine Datei mit dem Namen Custom Configuration erstellen und speichern Sie sie außerhalb des Verzeichnisses DISM, können Sie den Befehl DISM zum Ausführen der Datei verwenden. Öffnen Sie das Verzeichnis DISM, an einer Eingabeaufforderung. Beispiel:

``` syntax
Dism /Capture-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D /ConfigFile:<configuration list>
```

oder

``` syntax
Dism /Append-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D /ConfigFile:<configuration list>
```

wobei * &lt;Konfigurationsliste&gt; * enthält den vollständige Verzeichnispfad für die Konfigurationsdatei. Beispielsweise `c:\imaging\configuration_list.ini`. Sie müssen die Option **/Capture-Image** zum Erstellen einer neuen WIM-Datei oder die Option **/Append-Image** anfügen eine vorhandenen WIM-Datei verwenden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

 

 






