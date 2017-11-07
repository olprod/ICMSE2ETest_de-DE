---
author: Justinha
Description: "Hinzufügen von Language Packs zu Windows"
ms.assetid: 0734452f-aa09-4ec9-bbbf-fbc995dd803f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Language Packs zu Windows"
ms.openlocfilehash: 353957e0e2aaeeff674d3ae7b722d76e3a6a4de0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-language-packs-to-windows"></a>Hinzufügen von Language Packs zu Windows


OEMs können Sprachpakete zum Lokalisieren von PCs und Geräte für Kunden in unterschiedlichen Regionen hinzufügen.

Für Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), Sprachpakete in Sprachkomponenten geteilt und [Features auf Demand V2 (Funktionen)](features-on-demand-v2--capabilities.md). Diese Verringerung der Bildgröße kann hilfreich sein, beim Erstellen von Bildern für niedrigeren Kosten Geräte mit kleinen Speicher. Sie können auch den Zeitaufwand zum Erstellen und Bereitstellen der Bilder reduzieren.

## <a name="span-idlangpacktypesspanspan-idlangpacktypesspanspan-idlangpacktypesspanlanguage-pack-types"></a><span id="LangPackTypes"></span><span id="langpacktypes"></span><span id="LANGPACKTYPES"></span>Arten von Language Packs


Sie können mehrere Sprachen in der gleichen Windows 10 Bild installieren. Für jede Sprache, in denen verfügbar:

-   Fügen Sie das Language Pack und die **grundlegenden** Komponenten.
-   Zum Laden von Cortana Features müssen Sie auch fügen Sie die **Sprachsynthese**und **die Spracherkennung hinzu**.
-   Hinzufügen von **Schriftarten** und **optische zeichenerkennung** für die am häufigsten verwendeten Sprachen innerhalb einer Region zur Verbesserung der ersten des Benutzers-Erfahrung (dringend empfohlen). Wenn sie nicht bereits installiert sind, Windows heruntergeladen und installiert diese im Hintergrund, wenn ein Benutzer die Sprache zum ersten Mal.
-   Hinzufügen der **handschrifterkennung** für Geräte mit Stift Eingaben.
-   Fügen Sie Windows Recovery Environment (WinRE) Komponenten, damit Endbenutzer leichter ihren PCs teilnehmen wiederherstellen können.

Anderen Anpassungen, die Voreinstellung werden können:

-   Währung, Zeitzone oder Kalenderformate
-   [Tastatur-IDs und Eingabemethoden-Editoren für Windows](windows-language-pack-default-values.md)

Nicht alle Funktionen stehen für jede Sprache.

Achten Sie darauf, Beschränken der Umfang und die Typen von Sprachpaketen mit jedem Bild enthalten. Während der Language Packs von Windows 10 kleiner sind, müssen zu viele kann beeinflusst Speicherplatz und Leistung, insbesondere beim Aktualisieren und Wartung von Windows können beeinflussen.

Einige Funktionen haben Hinsicht, wie in der folgenden Tabelle dargestellt.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Komponente</th>
<th align="left">Beispiel-Dateiname</th>
<th align="left">Dependencies</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Sprachpaket</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Pack_x64_es-es.cab</code></td>
<td align="left">Keine</td>
<td align="left">Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.</td>
</tr>
<tr class="even">
<td align="left">Benutzeroberflächen-Sprachpaket</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es-valencia.cab</code></td>
<td align="left">Erfordert ein bestimmtes vollständig lokalisierte oder teilweise lokalisierte Language Pack. Beispiel: ca-es-Valencia erfordert es-es. Weitere Informationen finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).</td>
<td align="left"><p>Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.</p>
<p>Nicht alle Sprachressourcen für die Benutzeroberfläche sind in der LIP enthalten. Benutzeroberflächen-Sprachpaketen erfordern mindestens ein Sprachpaket (oder übergeordnete Sprache). Ein übergeordnetes Language Pack bietet Unterstützung für ein SPRACHPAKET. Die Teile der Benutzeroberfläche an, die nicht in der LIP-Sprache übersetzt werden werden in der übergeordneten Sprache angezeigt. In Ländern oder Regionen, in dem zwei Sprachen häufig verwendet werden, können Sie eine höhere benutzerfreundlichkeit bereitstellen, indem ein LIP über ein Language Pack anwenden.</p></td>
</tr>
<tr class="odd">
<td align="left">Standard</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Rechtschreibprüfung, Textvorhersage, Wortumbruch und Silbentrennung Wenn für die Sprache zur Verfügung.</p>
<p>Sie müssen diese Komponente hinzufügen, bevor Sie die folgenden Komponenten hinzufügen.</p></td>
</tr>
<tr class="even">
<td align="left">Schriftarten</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Schriftarten.</p>
<p>Erforderlich für einige Regionen zum Rendern von Text, der in Dokumenten angezeigt wird. Beispielsweise ten-ten erfordert das Schriftart Thai Pack. Weitere Informationen finden Sie unter [Features auf Anforderung V2 (Funktionen)](features-on-demand-v2--capabilities.md).</p></td>
</tr>
<tr class="odd">
<td align="left">Optische zeichenerkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Erkennt und Text in einem Bild ausgegeben.</td>
</tr>
<tr class="even">
<td align="left">Handschrifterkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Ermöglicht handschrifterkennung für Geräte mit Input Stift.</td>
</tr>
<tr class="odd">
<td align="left">Sprachsynthese</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Text zu Sprachein-und-Ausgabe, von Cortana und die Sprachausgabe verwendet werden können.</td>
</tr>
<tr class="even">
<td align="left">Spracherkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package</code></td>
<td align="left">Grundlegende, Sprachausgabe Spracherkennung</td>
<td align="left">Erkennt VoIP Eingabe, von Cortana und Windows-Spracherkennung verwendet werden.</td>
</tr>
<tr class="even">
<td align="left">Retail Demo Erfahrung</td>
<td align="left"><code>Microsoft-Windows-RetailDemo-OfflineContent-Content-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">[Retail Demo Erfahrung](https://msdn.microsoft.com/windows/uwp/monetize/retail-demo-experience)</td>
</tr>
<tr class="odd">
<td align="left">WinRE</td>
<td align="left">Mehrere, siehe [Windows RE anpassen](customize-windows-re.md).</td>
<td align="left">Keine</td>
<td align="left">Endbenutzer reparieren und Wiederherstellen von ihren PCs teilnehmen verwendet. Finden Sie unter [Anpassen von Windows RE](customize-windows-re.md).</td>
</tr>
</tbody>
</table>

 

## <a name="span-idwheredoidownloadthelanguagepacksspanspan-idwheredoidownloadthelanguagepacksspanspan-idwheredoidownloadthelanguagepacksspanwhere-do-i-download-the-language-packs"></a><span id="Where_do_I_download_the_language_packs_"></span><span id="where_do_i_download_the_language_packs_"></span><span id="WHERE_DO_I_DOWNLOAD_THE_LANGUAGE_PACKS_"></span>Wobei Laden Sie die Language packs


OEMs und System-Builder können der Pakete und Features von dedizierten Download Center für OEMs und System-Builder abrufen.

Benutzer können mehr Sprachen und Features auf **Einstellungen** installieren &gt; **Uhrzeit- und Sprache** &gt; **Region & Sprache** &gt; **Hinzufügen einer Sprache**. Finden Sie weitere Informationen finden Sie unter [wie eine Eingabe Sprache an den PC hinzufügen](http://go.microsoft.com/fwlink/?LinkId=619289).

Zur Verfügung stehen, finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).

## <a name="span-idotherconsiderationsspanspan-idotherconsiderationsspanspan-idotherconsiderationsspanother-considerations"></a><span id="Other_considerations"></span><span id="other_considerations"></span><span id="OTHER_CONSIDERATIONS"></span>Weitere Aspekte


-   In einigen Sprachen muss weitere Festplatten-Speicherplatz als andere.
-   Obwohl Sie eine Reihe von Language Packs gleichzeitig mit den Befehlen hinzufügen können: **DISM/Add-Package**, **DISM/Apply-Unattend**oder [LPKSetup](http://go.microsoft.com/fwlink/?LinkID=624512), hinzufügen, nicht zu viele gleichzeitig, da das Gerät möglicherweise nicht genügend Speicher zum behandeln. Allgemeine Empfehlungen: aus Windows im Überwachungsmodus aktiviert, nicht mehr als 20 Language Packs gleichzeitig hinzufügen. Windows PE sollte fügen Sie nicht mehr als 7 werden hinzu. Wenn Windows PE noch nicht genügend Arbeitsspeicher ausgeführt wird, können Sie [Windows PE durch Hinzufügen von temporärer Speicher (Scratch Leerzeichen) anpassen](winpe-mount-and-customize.md).
-   Cross-Sprache-Updates werden nicht unterstützt. Dies bedeutet, dass während des Upgrades oder Migrationen, wenn Sie ein Betriebssystem mit mehreren Language Packs installiert haben, migrieren oder aktualisieren Sie können aktualisieren oder nach Systemsprache Standard-Benutzeroberfläche migrieren. Wenn Englisch die Standardsprache ist, können Sie beispielsweise aktualisieren oder nur in Englisch migrieren.
-   Die Standardsprache kann nicht entfernt werden, da sie verwendet wird, um Computer Sicherheits-IDs (SIDs) zu generieren. Die Standardsprache für die Benutzeroberfläche ist die Sprache, die während der Out-Of-Box-Experience (OOBE), der Sprache der Benutzeroberfläche im Befehlszeilentool Deployment Image Servicing and Management (DISM) oder in die Antwortdatei angegeben, wenn Sie OOBE überspringen ausgewählt ist.
-   Wenn Language Packs mithilfe von Windows PE hinzufügen möchten, müssen Sie Windows PE Auslagerungsdatei Unterstützung hinzufügen. Weitere Informationen finden Sie unter [Deployment Image Servicing und Best Practices Management (DISM)](deployment-image-servicing-and-management--dism--best-practices.md).
-   Installieren Sie ein Language Pack nicht nach einer Aktualisierung. Wenn Sie ein Update installieren (Hotfix, allgemein verfügbare Version \[GDR\], oder Servicepack \[SP\]), die Language-abhängigen Ressourcen enthalten soll, bevor Sie ein Sprachpaket installieren, die sprachspezifische Änderungen, die in dem Update enthalten sind, nicht übernommen werden und Sie das Update zu installieren müssen. Installieren von Language Packs immer vor der Installation von Updates.
-   Die Version des Language Packs muss die Version von Windows übereinstimmen. Sie können nicht, beispielsweise Windows 8 ein Windows-10-Sprachpaket hinzugefügt oder Hinzufügen von Language Packs im Windows 8 bis 10 für Windows. Zusätzlich muss die Buildnummer übereinstimmen.

## <a name="span-idlpinstallmethodsspanspan-idlpinstallmethodsspanspan-idlpinstallmethodsspaninstallation-methods"></a><span id="LPInstallMethods"></span><span id="lpinstallmethods"></span><span id="LPINSTALLMETHODS"></span>Installationsmethoden


Sie können ein Language Pack zu einem Bild auf folgende Weise hinzufügen:

-   [**Offline-Installation**](#add-offline). Wenn Sie Hinzufügen eines Language Packs oder internationale Einstellungen auf benutzerdefinierte Windows-Abbild konfigurieren müssen, können Sie DISM verwenden.
-   [**Mithilfe von Windows Setup.**](#add-setup)
-   **Auf einem Betriebssystem ausgeführt wird.** Wenn Sie das Betriebssystem zum Installieren einer Anwendung oder zum Testen und Überprüfen der Installation starten müssen, können Sie ein Sprachpaket für das ausgeführte Betriebssystem mithilfe von DISM oder das Language Pack-Setup-Tool (Lpksetup.exe) hinzufügen. Sie können diese Methode nur für Language Packs verwenden, die außerhalb des Windows-Abbilds gespeichert sind. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Language Packs in einer Windows-Installation ausgeführt](add-and-remove-language-packs-on-a-running-windows-installation.md) und [Von Benutzeroberflächen-Sprachpaketen Windows hinzufügen](add-language-interface-packs-to-windows.md).

## <a name="span-idaddsetupspanspan-idaddsetupspanadd-or-remove-languages-using-windows-setup"></a><span id="add_setup"></span><span id="ADD_SETUP"></span>Hinzufügen oder Entfernen von Sprachen mithilfe von Windows Setup


**Eine mehrsprachige Edition von Windows mithilfe von Windows Setup bereitstellen**

1.  Hinzufügen oder Entfernen von Language Packs in der ** \\Langpacks** Ordner in einer Verteilerliste freigeben.
2.  Erstellen Sie die Datei "lang.ini" neu. Windows-Setup verwendet die Lang.ini-Datei zum Identifizieren der Language Packs, die sich innerhalb des Abbilds und in der Windows-Verteilungsfreigabe befinden. Die Lang.ini-Datei identifiziert auch die Sprache, die während der Installation von Windows angezeigt wird. Sie müssen auch die Lang.ini-Datei erneut generieren, wenn Sie beabsichtigen, Wiederherstellungsmedien für Bilder erstellen, die mehrere Sprachen enthalten.

    Internationale Befehlszeilenoptionen zum Warten DISM können Sie um die Lang.ini-Datei basierend auf Language Pack-Updates neu zu erstellen. Ändern Sie die Lang.ini-Datei nicht manuell. Finden Sie weitere Informationen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

3.  Wenn Sie ein mehrsprachiges Abbild bereitstellen oder ein bestimmtes Language Pack auf einem Windows-Abbild für ein bestimmtes Gerät anwenden müssen, können Sie das Language Pack mithilfe von Windows Setup und einer Antwortdatei hinzufügen. Das Sprachpaket muss auf das Bild hinzugefügt werden, bevor internationale Einstellungen konfiguriert werden können. Weitere Informationen zum Hinzufügen ein Language Packs zu einer Antwortdatei finden Sie unter [Hinzufügen eines Pakets zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915066). Verwenden Sie zum Hinzufügen eines Language Packs und internationale Einstellungen konfiguriert haben, übergeben Sie die Konfiguration **WindowsPE** an das Language Pack hinzufügen und anderen Konfigurationsphasen internationale Einstellungen konfigurieren. Weitere Informationen finden Sie unter [Configure International Settings in Windows](configure-international-settings-in-windows.md)
    
    **Hinweis**  Wenn in einer Antwortdatei Einstellungen von Sprachen und Gebietsschemas angegeben sind, überschreiben diese Einstellungen alle vorherigen Standard. Wenn Sie zuerst die Einstellung ändern, beispielsweise `UILanguage` tool auf einem offline-Abbild FR-FR mithilfe der Befehlszeile DISM festlegen und dann später Anwenden einer Antwortdatei aus, die als Sprache der Benutzeroberfläche EN-US angibt, EN-US ist die Standardsprache für die Benutzeroberfläche.   

4.  Verwenden Sie Setup die Language Packs zu installieren, die in der Freigabe der Verteilung sind.

Weitere Informationen finden Sie finden Sie unter [Hinzufügen von Unterstützung mehrerer Sprachen in eine Windows-Distribution](add-multilingual-support-to-a-windows-distribution.md) oder [Hinzufügen von Unterstützung mehrerer Sprachen zu Windows Setup](add-multilingual-support-to-windows-setup.md).

## <a name="span-idaddofflinespanspan-idaddofflinespanadd-or-remove-languages-offline"></a><span id="add_offline"></span><span id="ADD_OFFLINE"></span>Hinzufügen oder Entfernen von Sprachen offline

Hier wird zum Hinzufügen und Entfernen von Sprachen auf einem offline-Abbild (install.wim).

Um Speicherplatz zu sparen, können Sie englische Komponenten entfernen, wenn Sie für nicht-englischen Regionen bereitstellen. Sie müssen deinstallieren Sie diese in umgekehrter Reihenfolge aus, wie Sie diese hinzufügen.

**Binden Sie die Bilder**

-   Binden Sie Windows und Windows RE-Bilder. Die Windows RE-Bilddatei ist Teil des Windows-Abbilds an.

    ``` syntax
    md C:\mount\windows
    Dism /Mount-Image /ImageFile:install.wim /Index:1 /MountDir:"C:\mount\windows"
    md C:\mount\winre
    Dism /Mount-Image /ImageFile:"C:\mount\windows\Windows\System32\Recovery\winre.wim" /index:1 /MountDir:"C:\mount\winre"
    ```

**Fügen Sie eine Sprache hinzu**

1.  Fügen Sie die Sprache auf Windows. Die/Add-Package oder /Add-Capabilities-Befehlen können Sie die Funktionen hinzufügen.

    Pakete mit Abhängigkeiten Vergewissern Sie sich, dass Sie die Pakete in Reihenfolge installieren. Beispielsweise um Cortana aktivieren möchten, installieren: das Language pack **CAB**, klicken Sie dann **grundlegende**, auf **TextToSpeech**und anschließend auf **Sprache**, in der angegebenen Reihenfolge.

    Wenn Sie nicht die Abhängigkeiten sicher sind, ist es OK, um alle im selben Ordner ablegen und dann alle gleichzeitig mit dem gleichen DISM/Add-Package Befehl hinzufügen.

    Nach dem Hinzufügen des Sprachpakets, stellen Sie sicher, dass es in den Bildern ist.

    ``` syntax
    rem Remove the paragraph marks to make this into one really big, long command. 
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab"
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

2.  Fügen Sie andere Funktionen, wie beispielsweise Schriftarten, die für diese Region erforderlich. Weitere Informationen finden Sie unter [Features auf Anforderung V2 (Funktionen)](features-on-demand-v2--capabilities.md).

    ``` syntax
    rem Thai example (add th-TH first).
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package"
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

3.  Wenn Sie, dass die Sprachen für Windows, wenn möglich, diese WinRE, um sicherzustellen, dass eine konsistente Sprache Erfahrung in Wiederherstellungsszenarien hinzufügen hinzufügen. Dies ist eine entsprechende Version von Windows und Windows ADK erforderlich. Windows RE erfordert jetzt das Windows PE-HTA-Paket, dies ist neu in Windows 10.

    Nach dem Hinzufügen der Pakete, stellen Sie sicher, dass das Bild laufenden.

    ``` syntax
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

    Beispielausgabe/Get-Packages: Paketidentität: Microsoft-Windows-Windows PE-Rejuv\_fr-fr fr-FR ~ 10.0.9926.0 Zustand: installiert

**Fügen Sie ein Language Interface Pack (LIP)**

1.  Fügen Sie Sie dem Windows-Abbild der LIP und Bedarf/verfügbaren Funktionen hinzu. Einige Regionen besitzen keine verwandten Funktionen, andere teilweisen oder vollständigen festgelegt.

    Nach dem Hinzufügen der Pakete, stellen Sie sicher, dass das Bild laufenden.

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\Microsoft-Windows-Client-Language-Pack_x64_bn-in.cab
         /PackagePath="C:\Languages\bn-in x64\Microsoft-Windows-LanguageFeatures-Basic-bn-in-Package.cab"
    ```

2.  Fügen Sie andere Funktionen, wie beispielsweise Schriftarten, die für diese Region erforderlich.

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package"
    ```

3.  Stellen Sie sicher, dass das Bild laufenden.

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows" 
    ```

**Entfernen einer Sprache**

1.  Um Speicherplatz zu sparen, können Sie die Sprachen aus einem Bild entfernen.

    Sie müssen deinstallieren Sie diese in umgekehrter Reihenfolge aus, wie Sie diese hinzufügen.

    Sie können keine Funktion, der andere Pakete abhängig entfernen. Wenn Sie die französische Handschrift und grundlegender Funktionen installiert haben, können nicht Sie beispielsweise die grundlegende Funktion entfernen. Dies schlägt fehl.

    Sie können DISM/Remove-Package oder DISM /Remove-Capability Befehl verwenden, um eine Funktion und /DISM/Get-Packages oder DISM /Get-Capabilities um sicherzustellen, dass sie nicht mehr im Bild sind zu entfernen.

    ``` syntax
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Speech~~~en-US~0.0.1.0 
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.TextToSpeech~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Handwriting~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.OCR~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Basic~~~en-US~0.0.1.0
    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    DISM /Get-Packages /Image:"C:\mount\windows"
    DISM /Get-Capabilities /Image:"C:\mount\windows"
    ```

    Es ist außerdem OK, um das Language Pack einfach zu entfernen, ohne die Sprachfunktionen entfernen. Eine Woche nach dem Abschluss des Benutzers OOBE, wenn der Benutzer die Sprache, die Sprache der Liste nicht hinzugefügt, bereinigt Windows automatisch die nicht verwendete Sprache-Funktionen.

2.  Entfernen Sie die optionalen Windows RE-Komponenten. Nach dem entfernen, vergewissern Sie sich, dass sie nicht mehr in das Bild befinden. Ersetzen Sie die Buildnummer 10.0.10120.0 mit dem von Ihnen verwendeten Build. 

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

3.  **Bekanntes Problem**: Wenn Sie das englische Sprachpaket in Windows 10 erstellen 10240 entfernt haben, müssen Sie das Bild im Überwachungsmodus starten und verwenden Sie den Befehl: `sfc.exe /scannow /verify` Probleme mit Windows 32-Bit-apps zu reparieren. Ein Beispiel dafür, wie Sie mit einem Skript dazu, finden Sie unter [Lab 2a: Antwortdateien: Aktualisieren von Einstellungen und Ausführen von Skripts](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md).

**Installieren von apps (bei jedem Hinzufügen von Sprachen erforderlich)**

Hinweis: In Windows 10, Version 1607, ist es nicht mehr erforderlich, Posteingang apps zu entfernen. Wenn Sie versuchen, zu diesem Zweck, kann der Befehl DISM fehlschlagen.

1.  Installieren Sie erneut die apps. Im folgende Beispiel veranschaulicht das die Posteingang Einstieg in die app installieren. Wiederholen Sie diese Schritte für jede der apps Posteingang (mit Ausnahme von AppConnector), indem Sie das entsprechende Paket ersetzen.

    ``` syntax
    Dism /Image:"c:\mount\windows" /Add-ProvisionedAppxPackage /packagepath:<path to appxbundle>\2b362ab83144485d9e9629ad2889a680.appxbundle /licensepath:<path to license file> \2b362ab83144485d9e9629ad2889a680_License1.xml
    ```

2.  Windows-desktopanwendungen: häufig müssen Sie diese installieren, da diese oft sprachspezifische Dateien enthalten, die bei der Installation ausgewählt werden. Sie werden nicht diese mithilfe von – Wartung offline aktualisieren können. Stattdessen müssen Sie das Bild zu erfassen, oder erstellen Sie ein separates provisioning Paket für die Windows-desktop-Anwendung.

**Aktualisieren Sie für Installationen von Windows-Setup oder Verteilung Freigaben verwaltet werden der Sprachenliste**

1.  Diese Option ist nur erforderlich, wenn Sie mehrsprachige Windows-setupmedien verteilen, oder Windows über eine Dateifreigabe verteilen.

    Erstellen Sie die lang.ini-Datei erneut.

    ``` syntax
    Dism /Image:C:\mount\windows /gen-langini /distribution:C:\my_distribution
    ```

    Die lang.ini-Datei in C:\\MyDistribution\\Quellen sollte etwa wie folgt aussehen:

    ``` syntax
    [Available UI Languages]
    ca-ES = 2
    es-ES = 3
     
    [Fallback Languages]
    es-ES = en-us
    ```

2.  Überprüfen Sie die Standardeinstellungen internationale im Windows-Abbild mithilfe von DISM.

    ``` syntax
    Dism /Image:C:\mount\windows /get-intl
    ```

    Beispielsweise sollte ähnlich wie die folgende Ausgabe angezeigt:

    ``` syntax
    Reporting offline international settings.
     
    Default system UI language : es-ES
    System locale : ca-ES
    Default time zone : Romance Standard Time
    User locale for default user : ca-ES
    Location : Spain (GEOID = 217)
    Active keyboard(s) : 0403:0000040a
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)
     
    Installed language(s): ca-ES
      Type : Partially localized language, LIP type.
    Installed language(s): es-ES
      Type : Fully localized language.
     
    Reporting distribution languages.
     
    The default language in the distribution is:
    es-ES
    ```

**Ändern Sie die Standardsprache**

-   Legen Sie die Windows-Standardsprache, die bevorzugte Sprache für Ihre Kunden übereinstimmen.

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\windows
    ```

**Heben Sie die Bereitstellung der Bilder**

-   Heben Sie die Bereitstellung der Windows RE und Windows-Bildern.

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idlpremovaltimerspanspan-idlpremovaltimerspanspan-idlpremovaltimerspanthe-language-pack-removal-task"></a><span id="LPRemovalTimer"></span><span id="lpremovaltimer"></span><span id="LPREMOVALTIMER"></span>Die Aufgabe der Language Packs entfernen


In Windows 10 wird die Language Pack entfernen Aufgabe auf alle Editionen von Windows ausgeführt. Alle Sprachen, die von Benutzern in der Systemsteuerung von Abschnitt Voreinstellungen Sprache ausgewählt sind werden jedoch nicht entfernt. Benutzer können auswählen, mehrere Sprachen ausgeführt und Language Packs, die nicht vom Benutzer verwendet werden, werden vom Computer entfernt. Darüber hinaus wird Sprachpaket, das von einem Benutzer installiert wird nicht entfernt.

Ausführen des Tools Sysprep setzt die Language Packs entfernen Uhr. Die Uhr wird nicht erneut gestartet werden, bis das nächste Mal OOBE ausgeführt und dem Neustart des Computers. Wenn Sie das Windows-Abbild anpassen, sollten Sie so machen Sie Ihre Anpassungen im Überwachungsmodus starten. Die Language Pack entfernen Aufgabe wird beim Start im Überwachungsmodus nicht gestartet werden. Weitere Informationen zu den Überwachungsmodus aktiviert finden Sie unter [Start für Windows Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md). Sie können auch das Windows-Abbild aktualisieren, ohne das Abbild zu starten. Weitere Informationen finden Sie unter [Service ein Windows Bild mithilfe von DISM](service-a-windows-image-using-dism.md)

Mithilfe der `SkipMachineOobe` Einstellung in der Microsoft-Windows-Shell-Setup-Komponente Aufgabe entfernen Language Packs nicht übersprungen.

**Hinweis**  
Die Aufgabe der Language Packs entfernen entfernt Benutzeroberflächen-Sprachpaketen nicht.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Language Packs](language-packs-and-windows-deployment.md)

[Verfügbare Sprachpakete für Windows](available-language-packs-for-windows.md)

[Features auf Anforderung V2 (Funktionen)](features-on-demand-v2--capabilities.md)

[Windows Language Pack-Standardwerte](windows-language-pack-default-values.md)

[Eingabe für Language Packs von Windows Standard](default-input-locales-for-windows-language-packs.md)

 

 






