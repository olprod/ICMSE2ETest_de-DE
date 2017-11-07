---
author: Justinha
Description: DISM Sprachen und International Befehlszeilenoptionen zum Warten
ms.assetid: 6434373a-a7f9-43ff-be28-e4d48fa0b70f
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Sprachen und International Befehlszeilenoptionen zum Warten
ms.openlocfilehash: 8d9ac0bae96fc24984fe1af22ee38c500b2d5d07
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-languages-and-international-servicing-command-line-options"></a>DISM Sprachen und International Befehlszeilenoptionen zum Warten


Internationale Befehle können verwendet werden, um internationale für Windows und Windows-Vorinstallation Environment (Windows PE) ändern Bilder. Sie können auch die vorhandene Einstellungen in einer Windows-Abbild offline- oder Onlinemodus Abfragen.

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe des Deployment Image Servicing und Verwaltungstool (DISM.exe) lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_offline\_Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Es gibt drei Typen von internationalen Wartung Befehle aus:

-   **Get-Befehle**. Ruft ein Bericht zu den internationalen Einstellungen für ein offline-Abbild oder einem ausgeführten Betriebssystem ab.
-   **Legen Sie Befehle**. Legt die unterschiedlichen internationalen Einstellungen für ein offline-Abbild.
-   **Gen-LangIni-Befehle**. Generiert die Lang.ini-Datei, die während der Installation verwendet wird.

Die folgenden internationalen Optionen stehen für ein Image offline zur Verfügung:

**DISM.exe/Image:**&lt;*Pfad\_auf\_offline\_Bild\_Verzeichnis* &gt; \[ **/Get-Intl** \] \[ **/Set-UILang** | **/Set-UILangFallback** | **/Set-SysLocale** | **/Set-UserLocale** | **/Set-InputLocale** | **Standardsprache** | **Option** | **/Set-SKUIntlDefaults** | **/Set-layereddriver** \] \[ **/Gen-LangINI** | **/Set-SetupUILang** | **/Distribution**\]

Die folgenden internationalen Optionen stehen für ein Betriebssystem ausgeführt wird:

**DISM.exe / Online** **/ Get-Intl**

In der folgenden Tabelle enthält eine Beschreibung des wie jede internationale Wartungsoptionen verwendet werden kann. Diese Optionen sind nicht Groß-/Kleinschreibung beachtet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option-Argument</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Option: <strong>/Get-Help /?</strong></p></td>
<td align="left"><p>Wenn unmittelbar nach einer internationalen Wartung Befehlszeilenoption verwendet wird, wird Informationen über die Option und den Argumenten angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild angegeben wird.</p>
<p>Beispiele für die:</p>
<p><strong>DISM /image:C:\test\offline/Set-UILang /?</strong></p>
<p><strong>DISM / online/Get-Intl /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Get-Intl</strong></p></td>
<td align="left"><p>Zeigt Informationen zu den internationalen Einstellungen und Sprachen.</p>
<p>Verwenden der <strong>Option/Online</strong> zum Anzeigen von Informationen zu internationalen Einstellungen und Sprachen im Betriebssystem ausgeführt wird.</p>
<p>Verwenden Sie die <strong>/image/Image</strong>:&lt;<em>Pfad_zum_Offlineabbildverzeichnis</em> &gt; Option, um Informationen zu den internationalen Einstellungen und Sprachen im Bild offline anzuzeigen.</p>
<p>Bei Verwendung mit den Optionen <strong>/Distribution</strong> werden Informationen zu internationalen Einstellungen und Sprachen in der Verteilung angezeigt. Der Name des Ordners in der Verteilung Freigabe wird nicht überprüft. Es wird als ...\Langpacks gemeldet\&Lt; <em>Gebietsschema_Name</em> &gt;\Lp.cab. Wobei &lt; <em>Gebietsschema_Name</em> &gt; ist der Name des Ordners.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Das Gebietsschema des Benutzers wird nur für offline-Images gemeldet. Der Bericht ist diese Einstellung nicht für die Ausführung von Betriebssystemen enthalten.</p>
</div>
<div>
 
</div>
<p>Beispiele für die:</p>
<p><strong>DISM / online/Get-Intl</strong></p>
<p><strong>DISM /image:C:\test\offline/Get-Intl</strong></p>
<p><strong>DISM /image:C:\test\offline /distribution:C:\windows_distribution/Get-Intl</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Set-UILang:</strong></p>
<p>Argument: &lt; <em>Name_der_Sprache</em>&gt;</p></td>
<td align="left"><p>Standardmäßige Systemsprache der Benutzeroberfläche (UI) festgelegt. Wenn die Sprache nicht im Windows-Abbild installiert ist, wird der Befehl fehl.</p>
<p>&lt;<em>Name_der_Sprache</em> &gt; gibt den Namen der Sprache, legen Sie als Standard; ja-JP.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn Sie ein Language Interface Pack (LIP) installieren und dessen Sprache als Standardsprache für die Benutzeroberfläche angeben, wird die LIP-Sprache als die standardmäßige Benutzeroberflächensprache System (oder das Installieren von Language) festgelegt werden, und die übergeordnete Sprache wird als Standardsprache für die Benutzeroberfläche festgelegt werden.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-UILang:fr-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Set-UILangFallback:</strong></p>
<p>Argument: &lt; <em>Name_der_Sprache</em>&gt;</p></td>
<td align="left"><p>Fallback als Standardsprache für die Benutzeroberfläche des Systems festgelegt in der offline-Windows-Abbild. Diese Einstellung wird verwendet, nur, wenn die Sprache, die durch <strong>die UILang</strong> angegebenen teilweise lokalisiert ist.</p>
<p>&lt;<em>Name_der_Sprache</em> &gt; gibt den Namen der Sprache, die als Standard fallback; festlegen En-US.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-UILangFallBack:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Set-SysLocale:</strong></p>
<p>Argument: &lt; <em>Gebietsschema_Name</em>&gt;</p></td>
<td align="left"><p>Die Sprache für nicht-Unicode-Programme (auch gewählte Systemgebietsschema) sowie Schriftart festgelegt im Windows-Abbild offline.</p>
<p>&lt;<em>Gebietsschema_Name</em> &gt; gibt den Namen der Sprache und Gebietsschema festgelegt als Standardsprache für nicht-Unicode; En-US.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Sie können nicht nur-Unicode-Sprachen als das Standardgebietsschema des Systems festgelegt. Wenn Sie versuchen, die <strong>Option/Set-SysLocale</strong> schlägt fehl, und die Sprache für nicht-Unicode-Programme wird nicht geändert werden.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-SysLocale:fr-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Set-UserLocale:</strong></p>
<p>Argument: &lt; <em>Gebietsschema_Name</em>&gt;</p></td>
<td align="left"><p>Legt die &quot;Standards und Formate&quot; Sprache (auch als Gebietsschema des Benutzers bezeichnet) im Windows-Abbild offline. Die &quot;Standards und Formate&quot; Sprache ist eine Einstellung für einzelne Benutzer, die standardmäßige Sortierreihenfolge bestimmt und die Standardeinstellungen für die Formatierung von Datumsangaben, Zeitangaben, Währung und Zahlen.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-UserLocale:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Set-InputLocale:</strong></p>
<p>Argument: &lt; <em>Eingabegebietsschema</em>&gt;:&lt;<em>Tastaturlayout</em>&gt;</p></td>
<td align="left"><p>Die Eingabe und Tastaturlayout im Windows-Abbild offline verwenden festgelegt.</p>
<p>Der Wert der &lt; <em>Eingabegebietsschema</em>&gt;:&lt;<em>Tastaturlayout</em> &gt; Paar kann eine der folgenden sein:</p>
<ul>
<li><p>&lt;<em>Language_id</em>:<em>Tastaturlayout</em>&gt;</p>
<p>Beispiel: 0409: 00000409</p></li>
<li><p>&lt;<em>Gebietsschema_Name</em>&gt;</p>
<p>Bei Angabe En-US als der lokale Name, beispielsweise die <strong>Set-InputLocale:</strong> Option auch das für dieses Gebietsschema definierten Tastatur Standardlayout festgelegt.</p></li>
</ul>
<p>Sie können mehrere Werte angeben, durch Semikolons als Trennzeichen. Dies ist nützlich, wenn Sie Unterstützung für mehrere Tastaturen auf einem einzelnen Computer einschließen möchten. Der erste Wert wird als der Standardtastatur festgelegt.</p>
<p>Die gültigen Layouts an, die auf Ihrem Computer konfiguriert werden können werden in den folgenden Registrierungsschlüssel aufgelistet.</p>
<p><strong>HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Control\Keyboard Layouts</strong></p>
<p>Eine Liste der Werte finden Sie unter [Default Eingabe](default-input-locales-for-windows-language-packs.md) und [Standardeinstellungen für die Tastatur](windows-language-pack-default-values.md).</p>
<p>Verwenden Sie den Hexadezimalwert das Language-ID und Tastatur Layout, das Sie konfigurieren möchten.</p>
<p>Dieser Parameter ist optional.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>Dism /image:C:\test\offline /Set-InputLocale:fr-fr</code></pre>
<pre class="syntax" space="preserve"><code>Dism /image:C:\test\offline /Set-InputLocale:0410:00010410</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>Standardsprache:</strong></p>
<p>Argument: &lt; <em>Name_der_Sprache</em>&gt;</p></td>
<td align="left"><p>Legt die standardmäßige System-Benutzeroberflächensprache, die Sprache für nicht-Unicode-Programme, die &quot;Standards und Formate&quot; Sprache, und die Eingabe und Layouts für die angegebene Sprache im Windows-Abbild offline. Diese Option gibt den Sprachwert für die folgenden:</p>
<ul>
<li><p>Sprache der Benutzeroberfläche</p></li>
<li><p>Standardgebietsschema des Systems</p></li>
<li><p>Benutzergebietsschema</p></li>
<li><p>Das Gebietsschema</p></li>
</ul>
<p>Bei Verwendung mit den Optionen, die die einzelnen Sprache oder Gebietsschemas angeben, haben die einzelnen Einstellungen Vorrang vor.</p>
<p>&lt;<em>Name_der_Sprache</em> &gt; gibt den Namen und das Gebietsschema Sprachcode; beispielsweise En-US, es-ES oder fr-FR</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-AllIntl:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>Option:</strong></p>
<p>Argument: &lt; <em>Name_der_Zeitzone</em>&gt;</p></td>
<td align="left"><p>Legt die Standardzeitzone in einem Windows-Abbild fest. Bevor Sie die Zeitzone festlegen, DISM überprüft, ob die Zeitzone angegebene Zeichenfolge für das Abbild gültig ist.</p>
<p>&lt;<em>Name_der_Zeitzone</em> &gt; gibt den Namen der Zeitzone zu verwenden. beispielsweise Pazifik Normalzeit. Eine vollständige Liste der Zeitzone Zeichenfolgen finden Sie unter Windows® unbeaufsichtigte Installation Reference. Auf einem Computer, auf der Windows 7 ausgeführt wird, können Sie das Befehlszeilentool Tzutil verwenden, um die Zeitzone für diesen Computer aufzulisten. Das Tool Tzutil wird standardmäßig unter Windows 7 installiert.</p>
<p>Der Name der Zeitzone muss den Namen der Zeitzone Einstellungen in der Registrierung unter <strong>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\TimeZones\</strong>exakt übereinstimmen.</p>
<p>Wenn Sie eine benutzerdefinierte Zeitzone an Ihren Computer hinzufügen, können Sie diese benutzerdefinierte Zeitzone Zeichenfolge angeben.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline Option:&quot;w (Normalzeit)&quot;</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Set-SKUIntlDefaults:</strong></p>
<p>Argument: &lt; <em>Name_der_Sprache</em>&gt;</p></td>
<td align="left"><p>Legt die standardmäßige System Benutzeroberflächensprache die Sprache für nicht-Unicode-Programme, die &quot;Standards und Formate&quot; Sprache und die Eingabe Gebietsschemas Tastatur Layouts und Zeitwerte Zone in einem offline Windows Bild auf den Standardwert von angegebenen &lt; <em>Name_der_Sprache</em>&gt;. Die <strong>Option/Set-SKUIntlDefaults</strong> den Tastaturtreiber für japanische und koreanische Tastaturen nicht geändert. Sie müssen die <strong>Option/Set-layereddriver</strong> verwenden, um dies zu ändern.</p>
<p>Verwendung <strong>/ Set-SKUIntlDefaults</strong> so ändern Sie alle internationalen Einstellungen in einem offline Windows Bild, um die Standardwerte übereinstimmen, die während der Retail Installationen festgelegt werden. Weitere Informationen zu den Standardwerten von jedem Language Pack finden Sie unter [Default Input Gebietsschemas für Windows Language Packs](default-input-locales-for-windows-language-packs.md).</p>
<p>Dieser Parameter ist optional. Wenn mit in Kombination mit eine der Einstellungen weiter oben in diesem Abschnitt werden die einzelne Einstellung Priorität.</p>
<p>Wenn die übergeben Sprache ein nur-Unicode-Gebietsschema übereinstimmt festlegen, das Standardgebietsschema des Systems wird nicht geändert, aber der Befehl tritt kein Fehler auf.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-SKUIntlDefaults:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Set-layereddriver:</strong></p>
<p>Argumente: &lt; <em>1 bis 6</em>&gt;</p></td>
<td align="left"><p>Gibt einen Tastaturtreiber für japanische oder koreanische Tastaturen verwenden.</p>
<p>In Japan verwenden viele Benutzer Tastaturen mit 106 Tasten, während andere 101 oder 102 Tasten haben. In Korea stehen mehrere verschiedene Arten von Tastaturen einige bei einer unterschiedlichen Anzahl von Schlüsseln.</p>
<p>Die möglichen Werte für diese Einstellungen sind [1 bis 6]:</p>
<ol>
<li><p>Gibt an, dem PC / AT erweiterte Tastatur (101/102 Tasten).</p></li>
<li><p>Gibt an, das koreanische PC / AT-101 Tasten kompatible Tastatur/MS Natural Keyboard (Typ 1).</p></li>
<li><p>Gibt an, das koreanische PC / AT-101 Tasten kompatible Tastatur/MS Natural Keyboard (Typ 2).</p></li>
<li><p>Gibt an, das koreanische PC / AT-101 Tasten kompatible Tastatur/MS Natural Keyboard (Typ 3).</p></li>
<li><p>Legt die koreanische Tastatur (103/106 Tasten).</p></li>
<li><p>Gibt an, die japanische (106/109 Tasten) Tastatur.</p></li>
</ol>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-LayeredDriver:1</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Gen-LangINI:</strong></p></td>
<td align="left"><p>Generiert eine neue Lang.ini-Datei, die Setup so definieren Sie die Language Packs in das Bild verwendet wird, und außerhalb der Verteilung. Außerdem wird die Standardsprache für die Benutzeroberfläche für das Setup definiert.</p>
<p>Der Ordner "Sources" der Windows-Verteilung wird die neue Lang.ini-Datei hinzugefügt werden.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Sie werden nicht für die Berechtigung zum Überschreiben einer vorhandenen Datei Lang.ini aufgefordert werden. Die vorhandene Lang.ini-Datei wird automatisch überschrieben.</p>
</div>
<div>
 
</div>
<p>Geben Sie eine offline-Windows-Abbild (<strong>/Image:</strong>&lt;<em>path_to_offline_image.wim</em> &gt; und einer Verteilergruppe (<strong>/Distribution:</strong>&lt;<em>Path_to_distribution_directory</em>&gt;).</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Gen-LangINI /distribution:C:\windows_distribution</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Option: <strong>/Set-SetupUILang:</strong></p>
<p>Argument: &lt; <em>Name_der_Sprache</em>&gt;</p></td>
<td align="left"><p>Definiert die Standardsprache, die vom Setup verwendet werden. Wenn diese Sprache nicht verwendet werden kann, werden von Setup automatisch Englisch verwendet.</p>
<p>Dies ist ein optionaler Befehl. Wenn nicht verwendet, wird die Standardsprache für die Benutzeroberfläche im Bild verwendet werden. Wenn die Sprache nicht vorhanden ist, wird die erste Sprache in der Liste der vorhandenen Sprachen verwendet werden.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-SetupUILang:fr-FR /distribution:C:\windows_distribution</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Option: <strong>/Distribution:</strong></p>
<p>Argument: &lt; <em>Pfad_zur_WIM Distribution_directory</em>&gt;</p></td>
<td align="left"><p>Gibt den Pfad für die Windows-Verteilung. Die Windows-Verteilung ist eine Kopie des Inhalts, der auf der Windows-Produkt-DVD frei. Diese Option ist nur für die Verwendung mit der <strong>Option/Get-Intl</strong> <strong>und/Gen-LangINI</strong> , wenn externe Language Packs vorhanden sind.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Gen-LangINI /distribution:C:\windows_distribution</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


-   Die Wartung DISM International-Befehle können nicht für eine Windows Vista oder Windows Server 2008-Bild verwendet werden. Informationen zum Warten von Windows Vista und Windows Server 2008-Abbildern finden Sie unter Windows Vista SP1-Version des Windows OEM-Vorinstallationskit (Windows OPK) oder Windows Automated Installation Kit (Windows AIK).
-   Sie können nicht in der gleichen Befehlszeile mit Internationale Wartung Befehlen anderer Befehle zum Warten verwenden.
-   Eine nur-Unicode-Sprache kann nicht als das Standardgebietsschema des Systems festgelegt werden.

    Die folgenden Sprachen werden Unicode-only (Sprachen sind in der Tabelle im Format aufgelistet: Sprache - Land/Region):

    Amharisch - Äthiopien

    Kasachisch - Kasachstan

    Odia - Indien (Odia Schrift)

    Armenisch - Armenien

    Khmer - Kambodscha

    Paschto - Afghanistan

    Assamesisch - Indien

    Konkani - Indien

    Punjabi - Indien (Gurmukhi-Skript)

    Bangla - Bangladesch

    Laotisch - Demokratische Volksrepublik LAOS

    Sanskrit - Indien

    Bangla - Indien (Bengali-Schrift)

    Malayalam - Indien (Malayalam-Schrift)

    Sinhala - Bangladesch

    Divehi - Malediven

    Maltesisch - Malta

    Syrisch - Syrien

    Georgisch - Georgien

    Maori - Neuseeland

    Tamil - Indien

    Gujarati - Indien (Gujarati-Skript)

    Marathi - Indien

    Telugu - Indien (Telugu-Schrift)

    Hindi - Indien

    Mongolisch (Mongolisch) - VR CHINA

    Tibetisch - Volksrepublik CHINA

    Inuktitut (Silbenschrift) - Kanada

    Nepali - Federal Demokratische Republik der Nepalesische

    Yi - Volksrepublik CHINA

    Kannada - Indien (Kannada-Skript)

     

-   Installieren Sie ein Language Pack nicht nach einer Aktualisierung.

    Wenn Sie ein Update installieren (Hotfix, allgemein verfügbare Version \[GDR\], oder Servicepack \[SP\]), vor der Installation eines Sprachpakets die Language-abhängigen Ressourcen enthält, die sprachspezifische Änderungen, die in dem Update enthalten sind, werden nicht übernommen. Installieren von Language Packs immer vor der Installation von Updates.

-   Beim Angeben einer Zeitzone mithilfe von **Option:**&lt;*Timezone\_Namen* &gt; müssen Sie geraden Anführungszeichen für mehrere Wörter verwenden. Beispielsweise **Option: "Pazifik Normalzeit"**. Wenn Sie kopieren und der Zeitzonenname einfügen, einschließlich der Anführungszeichen, von einem Microsoft® Word-Dokument und die Anführungszeichen möglicherweise nicht erkannt werden, und die Befehlszeile können Fehler auftreten.
-   Wenn Sie – internationale Schwelle Wartung sind und der hostumgebung unterstützt nicht die Sprache in diesem Bild, können Sie möglicherweise keine Fehlermeldung, die stammt aus diesem Abbild internationale lesen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






