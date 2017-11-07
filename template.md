---
title: TITEL DES ARTIKELS | DIENSTNAME
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: cabb720ffd42484be0cc23924f460b5ccfc2edd2
ms.sourcegitcommit: e608a62703fcc6bfb1e51713ca9cda10b5be3614
translationtype: MT
---
# <a name="metadata-and-markdown-template"></a>Metadaten und Abzugsverteilung(en)-Vorlage

Diese Vorlage docs.ms enthält Beispiele von Abzugsverteilung(en) Syntax sowie Anleitungen zum Festlegen der Metadaten. Es ist in das Stammverzeichnis der einzelnen Repository langen Pilot (z. B. ~/Azure-RMSDocs-pr /template.md) verfügbar und dient als Abzugsverteilung(en)-Datei gelesen werden sollen, auch wenn Sie auf [die veröffentlichte Version](https://stage.docs.microsoft.com/en-us/rights-management/template) finden Sie unter verweisen können wie die Rendeer Abzugsverteilung(en) Beispiele.

Erstellen einer Abzugsverteilung(en) Datei Shluld Kopie die Vorlage in eine neue Datei, füllen Sie die Metadaten wie unten angegebenen die H1-Überschrift an den Titel des Artikels, und löschen Sie den Inhalt. 


## <a name="metadata"></a>Metadaten 

Die vollständige Metadaten-Block ist oben, aufgeteilt Pflichtfelder und optionale Felder; finden Sie unter den [Vorgängen IN Metadaten Spickzettel](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) für weitere Details. Einige wichtige Hinweise:

- Sie **müssen** haben ein Leerzeichen zwischen dem Doppelpunkt (:)) und den Wert für ein Metadata-Element.
- Wenn Sie eine optionale Metadata-Element keinen Wert haben, kommentieren Sie das Element mit einem # (nicht verlassen sie leer oder verwenden "NV"); Wenn Sie einen Wert auf ein Element, die Commnted out wurde hinzufügen, müssen Sie unbedingt die # entfernen.
- Doppelpunkte in einen Wert (z. B. Titel) unterbrechen den Parser Metadaten. Verwenden Sie anstelle der HTML-Codierung der & #58; (z. B. "Titel: Azure Rights Management & #58; die Grundlagen | Azure, RMS").
- **Titel**: Dieser Titel wird in Suchergebnissen angezeigt. Der Titel endet mit einer senkrechter Strich (|) gefolgt vom Namen des Diensts (z. B. Siehe oben). Den Titel in die H1-Überschrift identisch der Titel müssen nicht (und wahrscheinlich sollte nicht) sein. Es sollte ungefähr 65 Zeichen (einschließlich | DIENSTNAME)
- **Autor**, **Manager**, **Reviewer**: das Autorenfeld sollte die **Github Benutzername** des Autors, nicht ihre Alias enthalten.  Die Felder "Manager" und "Reviewer" sollte Aliase andererseits, enthalten. MS.Reviewer gibt den Namen der PM, den Artikel oder Dienst zugeordnet ist.
- **ms.AssetID**: Dies ist die GUID des Artikels aus GROßBUCHSTABEN. Wenn Sie eine neue Abzugsverteilung(en)-Datei zu erstellen, rufen Sie eine GUID aus [https://www.guidgenerator.com](https://www.guidgenerator.com). 
- **ms.Prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: Mögliche Werte für diese Elemente finden Sie [hier](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## <a name="basic-markdown-and-gfm"></a>Grundlegende Abzugsverteilung(en) und GFM

Alle grundlegenden und Github flavored Abzugsverteilung(en) wird unterstützt. Weitere Informationen dazu finden Sie unter:

- [Geplante Abzugsverteilung(en) syntax](https://daringfireball.net/projects/markdown/syntax)
- [Github flavored Abzugsverteilung(en) (GFM) Dokumentation](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Überschriften

Beispiele für Überschriften der ersten und zweiten Ebene sind oben. 

Es **muss nur eine Überschrift der ersten Ebene im Thema, das als Titel auf der Seite angezeigt wird** .  

Überschriften der zweiten Ebene generiert das Inhaltsverzeichnis auf der Seite, die im Abschnitt "In diesem Artikel" unterhalb des Titels auf der Seite angezeigt wird.

### <a name="third-level-heading"></a>Überschrift der dritten Ebene
#### <a name="fourth-level-heading"></a>Überschrift der vierten Ebene
##### <a name="fifth-level-heading"></a>Fünften Ebene Überschrift
###### <a name="sixth-level-heading"></a>Überschrift der sechsten-Ebene

## <a name="text-styling"></a>Text formatieren

*Kursiv* 

**Fett** 

~~Durchgestrichen~~



## <a name="links"></a>Verknüpfungen

Verwenden Sie zum Verknüpfen mit einer Abzugsverteilung(en)-Datei in der gleichen Repo [relative Links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Beispiel: [Was ist Azure-Rechteverwaltung](./understand-explore/what-is-azure-rms.md)

Um eine Kopfzeile in der gleichen Abzugsverteilung(en) Datei verknüpfen, die Quelle des veröffentlichten Artikels, suchen Sie die Id der Head (z. B. `id="blockquote"`, und Verknüpfen mit # + -Id (z. B. `#blockquote`).

- Beispiel: [Blockquotes](#blockquote)

Verwenden Sie zum Verknüpfen mit einer Kopfzeile in einer Datei Abzugsverteilung(en) in der gleichen Repo relative verknüpfen + Hashtag verknüpfen.

- Beispiel: [technische Overiew des Anmeldevorgangs](./understand-explore/rms-for-individuals-user-sign-up.md#technical-overview-of-the-sign-up-process)

Verwenden Sie Hyperlinks zu einer externen Datei, die vollständige URL als den Link ein.

- Beispiel: [Github](http://www.github.com)

Wenn eine URL in einer Abzugsverteilung(en)-Datei angezeigt wird, wird es in einem Link umgewandelt.

- Beispiel: http://www.github.com

## <a name="lists"></a>Listen

### <a name="ordered-lists"></a>Sortierte Listen

1. Dies 
1. Ist
1. Ein
1. Bestellt
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Sortierte Liste mit einer eingebetteten Liste

1. Hier
1. stammen
1. ein
1. eingebettete
    1. Verpassen leicht
    1. Pflaume Dozenten
1. bestellt
1. Liste


### <a name="unordered-lists"></a>Nicht sortierte Listen

- Dies
- ist
- a
- Aufzählung
- Liste


##### <a name="unordered-list-with-an-embedded-lists"></a>Ungeordnete Liste mit einer eingebetteten Listen

- Dies 
- Aufzählung 
- Liste
    - Frau Peacock
    - John Green
- contains  
- andere
    1. Colonel Senf
    1. Frau weiß
- Listen


## <a name="horizontal-rule"></a>Horizontale Linie

---

## <a name="tables"></a>Tabellen

| Tabellen        | Sind           | Leuchtstoff  |
| ------------- |:-------------:| -----:|
| Spalte 3 ist      | rechts ausgerichtet | $1600 |
| Spalte 2 ist      | Zentriert      |   $12 |
| SP 1 ist Standard | Linksbündig     |    $1 |


## <a name="code"></a>Code

### <a name="codeblock"></a>Codeblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Inline-code

Dies ist ein Beispiel für `in-line code`.

## <a name="blockquotes"></a>Blockquotes

> Der Dürre jetzt für zehn Millionen Jahre dauerte hatte, und die von der schlechte Lizards Kaiserherrschaft hatte lange inzwischen beendet. Hier auf die Äquator, in dem Kontinent, die einen Tag als Afrika bezeichnet werden würde der Wettbewerb um Vorhandensein hatte erreicht eine neue Climax der Kämpfe, und die Victor wurde noch nicht im Blick. In diesem Land barren und verdorrt ist konnte nur kleine oder der Swift der harten Schnörkel oder sogar hoffe überstehen.

## <a name="images"></a>Bilder

### <a name="static-image"></a>Statisches Bild

![Dies ist die Alt-text](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Verknüpftes Bild

[![Alternativtext für verknüpfte Bild](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>Animierte GIF-Datei

![animierte GIF-Datei](./media/hololens.gif)

## <a name="alerts"></a>Warnungen

### <a name="note"></a>Hinweis

> [!NOTE]
> Hierbei handelt es sich um HINWEIS

### <a name="warning"></a>Warnung

> [!WARNING]
> Dies ist eine WARNUNG

### <a name="tip"></a>Tipp

> [!TIP]
> Hierbei handelt es sich um TIPP

### <a name="important"></a>Wichtig

> [!IMPORTANT]
> Dies ist WICHTIG

## <a name="videos"></a>Videos

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube (engl.)

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms-Erweiterungen

### <a name="button"></a>Schaltfläche

> [!div class="button"]
[Schaltflächenlinks](/rights-management)

### <a name="selector"></a>Auswahl

> [!div class="op_single_selector"]
- ["Foo"](/rights-management/template.md)
- [häufig verwendete Hyperlinks](/rights-management/scratch.md)

### <a name="step-by-step"></a>Schrittweise

>[!div class="step-by-step"]
[Älter als Version](https://www.example.com)
[Weiter](https://www.example.com)