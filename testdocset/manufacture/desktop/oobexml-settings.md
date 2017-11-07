---
author: Justinha
Description: OOBE.XML Einstellungen
ms.assetid: 2c8ecddc-7099-451e-a069-642f654d4fbf
MSHAttr: PreferredLib:/library/windows/hardware
title: OOBE.XML Einstellungen
ms.openlocfilehash: e8817a2407a831cabd0e4264ceb69cc9a7e17e1d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oobexml-settings"></a>OOBE.XML Einstellungen


In diesem Thema werden die Einstellungen, die in "Oobe.xml" festgelegt werden können.

## <a name="span-idoobexmlsettingsspanspan-idoobexmlsettingsspanoobexml-settings"></a><span id="oobe.xml_settings"></span><span id="OOBE.XML_SETTINGS"></span>OOBE.XML Einstellungen


Die folgenden Tabellen werden die verfügbaren Einstellungen in der Datei Oobe.xml, indem Sie im Abschnitt zusammen mit der Beschreibung und der Wert für jede Einstellung.

**HID Kopplung mit.**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
<th align="left">Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>mouseImagePath</p></td>
<td align="left"><p>Absoluter Pfad zur Maus Paarung Anweisung Bild.</p>
<p>Das Bild darf nicht größer als 630 x 372 Pixel sein. Es ist angepasst im Hochformat oder kleine Formfaktoren.</p></td>
<td align="left"><p>Absoluter Pfad zu Bild</p></td>
</tr>
<tr class="even">
<td align="left"><p>mouseText</p></td>
<td align="left"><p>Hilfe von Text, der am unteren Rand der Seite angezeigt, wenn die Maus eine Kopplung Anweisung Bild kann nicht geöffnet werden. Dieser Text wird auch von Sprachausgabe für Eingabehilfen verwendet.</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>mouseErrorImagePath</p></td>
<td align="left"><p>Absoluter Pfad zur Maus Paarung Fehlerbild.</p>
<p>Das Bild darf nicht größer als 630 x 372 Pixel sein. Es wird im Hochformat oder kleine Formfaktoren gestreckt skaliert werden.</p></td>
<td align="left"><p>Absoluter Pfad zu dem Bild</p></td>
</tr>
<tr class="even">
<td align="left"><p>mouseErrorText</p></td>
<td align="left"><p>Dieser Fehlertext wird angezeigt, wenn Probleme beim Laden der Maus Paarung Fehlerbild. Dieser Text wird auch von Sprachausgabe für Eingabehilfen verwendet.</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardImagePath</p></td>
<td align="left"><p>Absoluter Pfad zur ersten Anweisung Bild Paarung Tastatur.</p>
<p>Das Bild darf nicht größer als 630 x 372 Pixel sein. Es wird im Hochformat oder kleine Formfaktoren gestreckt skaliert werden.</p></td>
<td align="left"><p>Absoluter Pfad zu dem Bild</p></td>
</tr>
<tr class="even">
<td align="left"><p>keyboardText</p></td>
<td align="left"><p>Können Sie Text, der am unteren Rand der Seite angezeigt, wenn die Tastatur eine Kopplung Anweisung Bild kann nicht geöffnet werden. Dieser Text wird auch von Sprachausgabe für Eingabehilfen verwendet.</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardPINImagePath</p></td>
<td align="left"><p>Absoluter Pfad zur zweiten Tastatur eine Kopplung Anweisung Bild.</p>
<p>Das Bild darf nicht größer als 630 x 372 Pixel sein. Es ist angepasst im Hochformat oder kleine Formfaktoren.</p></td>
<td align="left"><p>Absoluter Pfad zu dem Bild</p></td>
</tr>
<tr class="even">
<td align="left"><p>keyboardErrorImagePath</p></td>
<td align="left"><p>Absoluter Pfad zur Tastatur eine Kopplung Fehlerbild.</p>
<p>Das Bild darf nicht größer als 630 x 372 Pixel sein. Es ist angepasst im Hochformat oder kleine Formfaktoren.</p></td>
<td align="left"><p>Absoluter Pfad zu dem Bild</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardErrorText</p></td>
<td align="left"><p>Dieser Fehlertext wird angezeigt, wenn Probleme beim Laden der Tastatur eine Kopplung Fehlerbild vorliegen. Dieser Text wird auch von Sprachausgabe für Eingabehilfen verwendet.</p></td>
<td align="left"><p>String</p></td>
</tr>
</tbody>
</table>

 

**Seite ' Registrierung '**

Die folgende Tabelle zeigt die Registrierung seiteneinstellungen und ihrer zulässigen Werte in "Oobe.xml" an.

**Hinweis**  
Das kaufmännische und-Zeichen Symbol, "&", kann nicht in diesem Abschnitt der OOBE.xml verwendet werden. Verwenden Sie das Wort "und" stattdessen.

 

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Abschnitt</th>
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
<th align="left">Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>title</p></td>
<td align="left"><p>Erforderlich. Text, der Titel der Seite ' Registrierung '.</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 25 Zeichen.</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>Untertitel</p></td>
<td align="left"><p>Erforderlich. Text, der die Registrierungsseite beschreiben.</p></td>
<td align="left"><p>Zeichenfolge mit maximal 200 Zeichen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>"TextBox1"</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Text, der Bezeichnung "TextBox1". Erforderlich für die Bezeichnung "TextBox1" angezeigt werden.</p></td>
<td align="left"><p>Zeichenfolge mit maximal 20 Zeichen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>InputScope</p></td>
<td align="left"><p>Umfang der Bildschirmtastatur festzulegende Wert.</p></td>
<td align="left"><p>Zwei Bereiche werden unterstützt:</p>
<p>4 (IS_EMAIL_USERNAME)</p>
<p>29 (IS_NUMBERS)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>"TextBox2"</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Text, der Bezeichnung "TextBox2". Erforderlich für die Bezeichnung "TextBox2" angezeigt werden.</p>
<p></p></td>
<td align="left"><p>Zeichenfolge mit maximal 20 Zeichen.</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>InputScope</p></td>
<td align="left"><p>Der Wert, der Bereich der Bildschirmtastatur festgelegt.</p></td>
<td align="left"><p>Zwei Bereiche werden unterstützt:</p>
<p>4 (IS_EMAIL_USERNAME)</p>
<p>29 (IS_NUMBERS)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Bezeichnung "CheckBox1"</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Text, der Bezeichnung "CheckBox1". Erforderlich für die Bezeichnung "CheckBox1" angezeigt werden.</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 250 Zeichen. Es wird dringend empfohlen, dass Sie nicht mehr als 100 Zeichen verwenden, weil diese Länge von Text in einer Zeile passt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>DefaultValue</p></td>
<td align="left"><p>Wert, der Bezeichnung "CheckBox1" als ausgewählten oder nicht ausgewählten festgelegt.</p></td>
<td align="left"><p>True oder False. "True" bedeutet, dass das Kontrollkästchen Standardeinstellungen aktiviert ist. False bedeutet, dass das Kontrollkästchen Standardeinstellungen nicht ausgewählt ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>"CheckBox2"</strong></p>
<p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Text, der Bezeichnung "CheckBox2". Erforderlich für "CheckBox2" angezeigt werden</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 250 Zeichen. Es wird dringend empfohlen, dass Sie nicht mehr als 100 Zeichen verwenden, da diese Länge des Texts in einer einzigen Zeile angepasst wird.</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>DefaultValue</p></td>
<td align="left"><p>Der Wert "CheckBox2" als ausgewählte oder nicht ausgewählt festzulegen.</p></td>
<td align="left"><p>True oder False. "True" bedeutet, dass das Kontrollkästchen Standardeinstellungen aktiviert ist. False bedeutet, dass das Kontrollkästchen Standardeinstellungen nicht ausgewählt ist.</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>CheckBox3</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Text, der checkbox3 bezeichnen. Erforderlich für checkbox3 angezeigt werden</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 250 Zeichen. Es wird dringend empfohlen, dass Sie nicht mehr als 100 Zeichen verwenden, da diese Länge von Text in einer Zeile passt.</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>DefaultValue</p></td>
<td align="left"><p>Wert, der als ausgewählte oder nicht ausgewählte checkbox3 festgelegt.</p></td>
<td align="left"><p>True oder False. "True" bedeutet, dass das Kontrollkästchen Standardeinstellungen aktiviert ist. False bedeutet, dass das Kontrollkästchen Standardeinstellungen nicht ausgewählt ist.</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>LINK1</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Beschriftung für den Link, um die <strong>RTF</strong> -Datei. Erforderlich für link1 angezeigt werden.</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 100 Zeichen.</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>Link</p></td>
<td align="left"><p>Datei muss linkfile1.rtf heißen. OOBE sucht nach Dateien mit dem Namen linkfile1.rtf, linkfile2.rtf oder linkfile3.rtf unterhalb des Ordners Oobe\info. OOBE sucht nach Dateien mit den entsprechenden Gebietsschema- und bestimmte Unterordner Oobe\info.</p></td>
<td align="left"><p>linkfile1.RTF</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Link2</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Beschriftung für den Link zum der <strong>RTF</strong> -Datei. Erforderlich für link2 angezeigt werden.</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 100 Zeichen.</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>Link</p></td>
<td align="left"><p>Datei muss linkfile2.rtf heißen. OOBE sucht nach Dateien mit dem Namen linkfile1.rtf, linkfile2.rtf oder linkfile3.rtf unterhalb des Ordners Oobe\info. OOBE sucht nach Dateien mit den entsprechenden Gebietsschema- und bestimmte Unterordner des Oobe\info.</p></td>
<td align="left"><p>linkfile2.RTF</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Link3</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Beschriftung für den Link, um die <strong>RTF</strong> -Datei. Erforderlich für link3 angezeigt werden.</p></td>
<td align="left"><p>Zeichenfolge mit bis zu 100 Zeichen.</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>Link</p></td>
<td align="left"><p>Datei muss linkfile3.rtf heißen. OOBE sucht nach Dateien mit dem Namen linkfile1.rtf, linkfile2.rtf oder linkfile3.rtf unterhalb des Ordners Oobe\info. OOBE sucht nach Dateien mit den entsprechenden Gebietsschema- und bestimmte Unterordner des Oobe\info.</p></td>
<td align="left"><p>linkfile3.RTF</p></td>
</tr>
</tbody>
</table>

 

**Endbenutzer-LIZENZVERTRAG Datei und Sprache, Gebietsschema und Zeitzone Standardwerte.**

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Abschnitt</th>
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
<th align="left">Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>"eulafilename"</p></td>
<td align="left"><p>Sprache und Speicherort-spezifische Version des Herstellers Endbenutzer-Lizenzvertrag (EULA).</p></td>
<td align="left"><p>RTF-Datei.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Standardeinstellungen</p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>language</p></td>
<td align="left"><p>Dezimal-ID für das Gebietsschema.</p></td>
<td align="left"><p>Dezimal-ID für das Gebietsschema. Im folgenden Thema, [Standard Eingabe Gebietsschemas für Windows Language Packs](default-input-locales-for-windows-language-packs.md)können diese Werte gefunden werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>Speicherort</p></td>
<td align="left"><p>Der Speicherort wird angegeben, mithilfe eines GEOID-Werts, das in einen Dezimalwert konvertiert wird.</p></td>
<td align="left"><p>Eine Liste der GEOIDs finden Sie unter dieser [MSDN-Website](http://go.microsoft.com/fwlink/?LinkId=141804).</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>Gebietsschema</p></td>
<td align="left"><p>Das Gebietsschema wird mit einem Wert der Gebietsschema-ID (LCID) angegeben.</p></td>
<td align="left"><p>Eine vollständige Liste der LCIDs finden Sie unter diese [Microsoft Global Development-Website](http://go.microsoft.com/fwlink/?LinkId=63028). Laden Sie eine Liste der LCIDs sowie den Versionen von Windows, in denen sie verfügbar sind, [ &quot;Windows (Language Code Identifier, LCID) Verweis&quot; ](http://go.microsoft.com/fwlink/?LinkId=140989) von MSDN. In diesem Dokument im linken Bereich, wechseln Sie zur &quot;Anhang A: Windows-Verhalten&quot; um eine Tabelle anzuzeigen, die die LCIDS der Windows-Version und, in dem sie verfügbar ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>Tastatur</p></td>
<td align="left"><p>Gibt das Tastaturlayout an.</p></td>
<td align="left"><p>Verwenden des Tastatur-Werts, der aufgeführt wird in der Registrierung unter <strong>HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Keyboard Layouts</strong>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>Zeitzone</p></td>
<td align="left"><p>Gibt die Zeitzone des Endbenutzers des Computers an. Die Zeitzone wird durch eine Zeichenfolge festgelegt, der die Zeitzone für den Computer angibt. Die maximale Länge beträgt 256 Zeichen. Neue Zeitzonen kann in zukünftigen Versionen angezeigt werden. Um die Unterstützung für eine neue Zeitzone hinzuzufügen, müssen Sie die genaue Zeitzonenzeichenfolge eingeben.</p></td>
<td align="left"><p>Eine vollständige Liste der Zeitzonen finden Sie in der Registrierung unter <strong>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones</strong> auf einem Computer mit Windows® 7 aufgeführten Werte. Auf einem Computer unter Windows 7 können Sie das Befehlszeilentool Tzutil verwenden, um die Zeitzone für diesen Computer aufzulisten. Das Tzutil-Tool ist standardmäßig auf Windows Server 2008 R2 installiert.</p>
<div class="alert">
<strong>Warnung</strong>  
<p>Wenn die Zeitzone nicht angegeben ist, wird ein Zeitzone Standardwert verwendet. Die Standardzeitzone basiert auf der installierten Sprache und Region in einer Antwortdatei angegeben. Wenn eine Region mehr als eine Zeitzone hat, wird die Zeitzone auf die Standardzeitzone für diese Region festgelegt. Die Standardzeitzone für diese Region wird, hängt vom Speicherort der Stadt ein großes/Major angegeben. Beispielsweise wenn En-CA angegeben wird, wird <strong>Ostküstenzeit</strong> als die Standardzeitzone verwendet, da die Kanadische Capital, Ottawa, Eastern Standard Time verwendet. Wird als En-US angegeben die <code>UserLocale</code>, Pacific Standard Time wird standardmäßig die Zeitzone des Windows-Installation.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>adjustForDST</p></td>
<td align="left"><p>Gibt an, ob der Sommerzeit angepasst. Diese Einstellung gilt nur bei Verwendung in Kombination mit der <code>timezone</code> und <code>hideTimeAndDate</code> Einstellungen an die Zeiteinstellungen für den Endbenutzer.</p></td>
<td align="left"><p>True oder False.</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>hideRegionalSettings</p></td>
<td align="left"><p>Wenn diese Einstellung auf <strong>True</strong>festgelegt ist, und klicken Sie dann die Regionaleinstellungen-Seite angezeigt, auch wenn alle Werte für diese Seite vorkonfiguriert wurden.</p></td>
<td align="left"><p>True oder False.</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>hideTimeAndDate</p></td>
<td align="left"><p>Wenn diese Einstellung auf <strong>True</strong>festgelegt ist, und klicken Sie dann die Seite das Datum und Uhrzeit angezeigt, auch wenn alle Werte für diese Seite vorkonfiguriert wurden.</p></td>
<td align="left"><p>True oder False.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idhowtocustomizeoobespanspan-idhowtocustomizeoobespanspan-idhowtocustomizeoobespanhow-to-customize-oobe"></a><span id="How_to_Customize_OOBE"></span><span id="how_to_customize_oobe"></span><span id="HOW_TO_CUSTOMIZE_OOBE"></span>Gewusst wie: Anpassen von OOBE


**Zum Anpassen von OOBE mithilfe von "Oobe.xml"**

1.  Erstellen Sie eine Datei namens Oobe.xml, und speichern Sie diese Datei in Windows\\System32\\Oobe\\Info.

2.  Aktualisieren Sie Oobe.xml mithilfe von XML-Editor oder einem Text-Editor wie Editor ein, mit der entsprechenden Dateien, Pfaden und Inhalte.

3.  Speichern Sie die aktualisierte Version von "Oobe.xml" in Windows\\System32\\Oobe\\Info, oder in die entsprechende Sprache und Gebietsschema-spezifisches Ordner für Ihre Anpassungen erforderlich.

4.  Test OOBE.

    **Test OOBE**

    1.  Zeigen Sie auf **Alle Programme**, und klicken Sie dann auf **Zubehör**, klicken Sie im Menü **Start** auf.

    2.  Maustaste auf die Verknüpfung an der Eingabeaufforderung, und klicken Sie auf **als Administrator ausführen**. Akzeptieren Sie das Dialogfeld **Benutzerkontensteuerung** .

    3.  Navigieren Sie zu \\Windows\\System32\\Sysprep

    4.  Führen Sie **Sysprep/oobe**aus.

    5.  Starten des Computers.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Konfigurieren von Oobe.xml](configure-oobexml.md)

 

 






