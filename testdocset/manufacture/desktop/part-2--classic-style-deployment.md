---
author: Justinha
Description: "Übung 2 Classic-Schreibweise-Bereitstellung verwendet Befehlszeilentools in Windows ADK zum Anpassen und Bereitstellen eines Windows-Abbilds."
ms.assetid: 31ec67f4-8a6b-4bc3-a8b8-12e6c537d6a6
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 2: Classic-Schreibweise Imaging und Bereitstellung"
ms.openlocfilehash: c852145c24058f829a7bab2f56ee67ea4e48697e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idpart2classic-styledeploymentspanlab-2-classic-style-imaging-and-deployment"></a><span id="part_2__classic-style_deployment"></span>Übung 2: Classic-Schreibweise Imaging und Bereitstellung

Übung 2, klassischen-Stil-Bereitstellung verwendet Befehlszeilentools in Windows ADK zum Anpassen und Bereitstellen eines Windows-Abbilds.

## <a name="span-iddesignyourimagesspanspan-iddesignyourimagesspanspan-iddesignyourimagesspandesign-your-images"></a><span id="Design_your_images"></span><span id="design_your_images"></span><span id="DESIGN_YOUR_IMAGES"></span>Entwerfen Sie Ihrer Bilder

Hier ist ein Beispielsatz von Hardwarekonfigurationen, die Sie möglicherweise entwerfen.

|                              |              |                     |                                   |
|------------------------------|--------------|---------------------|-----------------------------------|
| Hardware-Konfiguration:      | 1            | 1 B                  | 2                                 |
| Formfaktor                  | Kleine tablet | 2-in-1              | Notizbuch                          |
| Arbeitsspeicher (RAM)                          | 1 GB         | 2 GB                | 4 GB                              |
| Datenträgerkapazität und Typ       | 16 GB eMMC   | 32 GB eMMC          | 500 GB-FESTPLATTE                        |
| Anzeigegröße                 | 8"           | 10"                 | 14"                               |
| Windows-SKU                  | Kern         | Pro                 | Kern                              |
| Sprache(n)                  | EN-US        | EN-US, FR-FR, ES-ES | EN-GB, DE-DE, FR-FR, ES-ES ZH-CN |
| Cortana                      | Ja          | Ja                 | Ja                               |
| Posteingang apps (Universal)       | Ja          | Ja                 | Ja                               |
| Stift                          | Nein           | Ja                 | Nein                                |
| Office (Universal)           | Ja          | Ja                 | Ja                               |
| Windows-desktopanwendungen | Nein           | Ja                 | Ja                               |
| Office 2016                  | Nein           | Ja                 | Ja                               |
| Compact OS                   | Ja          | Ja                 | Nein                                |

 

Übung 2 enthält alle Schritte zum Anpassen und Bereitstellen eines Windows-Abbilds mit optionalen Schritte für die Hardware-Konfiguration 1 b und 2. Übung 2a zeigt, wie weiter anpassen des Abbilds durch Hinzufügen von Windows-desktopanwendungen. Übung 2 b zeigt, wie Ihre benutzerdefinierten Abbilds mit Windows-Updates.

## <a name="span-idprepimagesspanspan-idprepimagesspancustomize-and-deploy-a-windows-image"></a><span id="prepimages"></span><span id="PREPIMAGES"></span>Anpassen und Bereitstellen eines Windows-Abbilds


In dieser Übungseinheit ändern Sie Ihren Bildern durch Hinzufügen und Entfernen von Sprachen und Treiber Pakete. Sie können das Windows-Abbild und die integrierten Wiederherstellungstools, fügen Sie eine Sprache, Sprachkomponenten und wichtige Faktoren (wie Treiber oder die Grafiktreiber) als auch die Edition aktualisieren und festlegen, dass für die werksseitige Wartung im Überwachungsmodus automatisch gestartet.

![Bild: Bilddateien und Bereitstellungsskripts kopieren](images/dep-win8-sxs-createmodelspecificfiles.jpg)

**Schritt 1: Kopieren der Windows-Bild Basisdatei**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.
2.  Erstellen Sie eine Kopie des Bilds, das Sie ändern möchten. Verwenden Sie für die Zwecke dieser Übungseinheit die base 10 Windows-Bilddatei für X64 oder X86:

    ``` syntax
    copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\WindowsWithOffice.wim
    ```

    Dies kann mehrere Minuten dauern.

**Schritt 2: Bereitstellen der Windows-Bilddatei**

-   Stellen Sie das Windows-Abbild. Den Aktivierungsvorgang ordnet dem Inhalt einer Bilddatei an einem Speicherort, in dem Sie anzeigen und ändern das bereitgestellte Abbild können.

    ``` syntax
    md C:\mount\windows
    Dism /Mount-Image /ImageFile:"C:\Images\WindowsWithOffice.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize
    ```

    Wobei *C* der Laufwerkbuchstabe des Laufwerks ist, die das Bild und *1* enthält ist der Index des Bilds, das Sie verwenden möchten.

    Dieser Schritt kann einige Minuten dauern.

    **Problembehandlung**

    Wenn dieser Befehl ein Fehler auftritt, stellen Sie sicher, dass Sie die Windows-10-Version von DISM verwenden, die mit der Windows-ADK installiert ist.

    Wenn Ihre Techniker PC 8.1 Windows, Windows 8 oder Windows 7 verwendet, verwenden Sie die **Bereitstellung und Imaging Tools Umgebung** auf die Tools zugreifen, die zusammen mit der Windows-10-Version von Windows ADK installiert sind.

    Bilder zu geschützten Ordnern an, wie Ihre Benutzer nicht bereitstellen\\-Dokumentordner.

    Wenn DISM Prozesse unterbrochen werden, können Sie vorübergehend aus dem öffentlichen Netzwerk trennen und Virenschutz deaktivieren.

    Wenn DISM Prozesse unterbrochen werden, sollten Sie die Befehle von der Windows PE-Umgebung ausführen.

**Schritt 3: Bereitstellen von Windows RE Bilddatei an**

-   Binden Sie die Windows RE-Bilddatei. Die Windows RE-Bilddatei ist Teil des Windows-Abbilds an.

    ``` syntax
    md C:\mount\winre
    ```

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\mount\windows\Windows\System32\Recovery\winre.wim" /Index:1 /MountDir:"C:\mount\winre"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Schritt kann einige Minuten dauern.

    **Hinweis**   Es wird empfohlen, dass Sie zum Aktualisieren der Windows- und Windows RE-Bilder zur selben Zeit, um sicherzustellen, dass alle erforderlichen Dateien in beide Bilder enthalten sind.

     

**Schritt 4: Hinzufügen von Treibern zu Windows**

1.  Fügen Sie alle INF-Schreibweise Treiber für Ihre Hardware erforderlich ist.

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

    wobei "C:\\Treiber\\PnP.Media.V1\\media1.inf" ist die Basis INF-Datei in das Treiberpaket.

    **Hinweis**  Für diesen Abschnitt wir fügen/LogPath für den Fall, dass etwas geht falsche – liegt ein Problem mit den Treiber hinzufügen, und öffnen Sie diese Datei auf schnell Fehler überprüfen.
    
    Um alle Treiber aus einem Ordner und alle Unterordner installieren, zeigen Sie auf den Ordner, und verwenden Sie der Option/recurse.

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:c:\drivers /Recurse
    ```

    **Warnung**  Während/recurse praktisch sein kann, ist es einfach, Aufblasen Ihr Bild zu. Einige Treiberpakete enthalten mehrere INF-Treiberpakete, die häufig Nutzlast Dateien im gleichen Ordner gemeinsam nutzen. Während der Installation wird jede INF-Paket in einen gesonderten Ordner, jeweils mit einer Kopie der Dateien Nutzlast erweitert. Wir haben Fällen gesehen, in denen ein beliebter Treiber in einem Ordner 900MB 10 GB Bilder, wenn mit der Option/recurse hinzugefügt hinzugefügt.

2.  Stellen Sie sicher, dass der Treiber Teil des Bilds ist:

    ``` syntax
    Dism /Get-Drivers /Image:"C:\mount\windows"
    ```

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste den Treiber enthält.

3.  Wenn diese Treiber äußerst wichtig für die Hardware sind zu starten, zu dem Windows RE-Abbild hinzufügen.

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\winre" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

4.  Optional: Sie können alle INF-Treiber aus vorherigen Tests zu entfernen:

    ``` syntax
    Dism /Remove-Driver /Image:"C:\mount\windows" /Driver:"VideoDriver-Old.inf" /LogPath=C:\mount\dism.log
    ```

5.  Für alle Treiber setup.exe-Schreibweise müssen Sie dies später im Überwachungsmodus installieren oder verwenden eine Bereitstellung Paket. Weiter unten in diesem Abschnitt zeigen wir Ihnen zum Einrichten der PC im Überwachungsmodus automatisch gestartet.

In Windows 10 können OEMs das Standardlayout Start ändern und das Layout von OEM-Kacheln angeben, indem Sie eine LayoutModification.xml-Datei erstellen, und platzieren diese Datei in den richtigen Systemspeicherort.

**Schritt 5: Hinzufügen der Dateien, die Sie das Start-Layout (Optional) ändern müssen.**

1.  Erstellen Sie eine LayoutModification.xml-Datei. Für diese Übungseinheit können Sie das Beispiel aus dem Dokument älter als Version Requesites verwenden. Im Beispiel wird auf dem Gerät (Schritt 8) vorinstallierte werden Office, OneNote und Reader beginnen anheften. Um eine eigene Datei LayoutModification.xml erstellen mithilfe eines XML-Editor, finden Sie unter den [Beispielskripts](windows-deployment-sample-scripts-sxs.md).
2.  Das Windows-Abbild Ihrer LayoutModification.xml-Datei hinzugefügt. Sie müssen die Datei in die folgenden Position vor dem ersten Start zu platzieren. Wenn die Datei vorhanden ist, sollten Sie die LayoutModification.XML ersetzen, die bereits im Bild enthalten ist.

    ``` syntax
    C:\Mount\Windows\Users\Default\AppData\Local\Microsoft\Windows\Shell\
    ```

3.  Wenn Sie Kacheln, die URL oder .lnk Dateien erfordern fixiert, fügen Sie die Dateien die folgenden legacy-Menü Start Verzeichnisse hinzu:
    -   ANWENDUNGSDATEN %\\Microsoft\\Windows\\Startmenü\\Programme\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\Startmenü\\Programme\\

**Hinweis**  Das Layout Start kann der Benutzer auf dem Computer mit der integrierten Wiederherstellungstools zurücksetzt verloren. Sie erfahren, wie Sie sicherstellen, dass diese Einstellungen auf dem Gerät im [Beispielskripts](windows-deployment-sample-scripts-sxs.md)bleiben.

 

## <a name="span-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanadd-or-change-languages-and-cortana-features-on-demand-optional"></a><span id="Add_or_change_languages_and_Cortana_features_on_demand__Optional_"></span><span id="add_or_change_languages_and_cortana_features_on_demand__optional_"></span><span id="ADD_OR_CHANGE_LANGUAGES_AND_CORTANA_FEATURES_ON_DEMAND__OPTIONAL_"></span>Hinzufügen oder Ändern von Sprachen und Cortana Features bei Bedarf (Optional)


**Hinweis**  Überspringen Sie diesen Abschnitt für Hardwarekonfiguration 1.

 

Verwenden Sie immer Language Packs und Features-On-Demand (Departements)-Pakete, die mit der Sprache des Windows-Bilds Plattform übereinstimmen.

Features bei Bedarf (FODs) sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Wenn ein Benutzer ein neues Feature benötigt, können sie das Feature Packs von Windows Update anfordern. OEMs können diese Features aktivieren auf ihren Geräten sofort einsetzbar vorinstallieren.

Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung. Einige dieser Features sind erforderlich, um vollständige Cortana-Funktionen zu aktivieren.

In der folgenden Tabelle werden die Arten von Language Packs und Komponenten verfügbar für Windows 10:

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
<td align="left"><code>lp.cab</code></td>
<td align="left">Keine</td>
<td align="left">Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.</td>
</tr>
<tr class="even">
<td align="left">Benutzeroberflächen-Sprachpaket</td>
<td align="left"><code>lp.cab</code></td>
<td align="left">Erfordert ein bestimmtes vollständig lokalisierte oder teilweise lokalisierte Language Pack. Beispiel: ca-ES erfordert es-ES. Weitere Informationen finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).</td>
<td align="left"><p>Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.</p></td>
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
</tbody>
</table>

 

**Schritt 6: Hinzufügen oder Ändern von Sprachen**

1.  Fügen Sie das Windows-Abbild Sprachen und Features On Demand.

    Pakete mit Abhängigkeiten Vergewissern Sie sich, dass Sie die Pakete in Reihenfolge installieren. Beispielsweise zum Cortana aktivieren möchten, installieren: **lp.cab**, klicken Sie dann **– grundlegende**, klicken Sie dann **– Schriftarten**, und klicken Sie dann **– TextToSpeech**, und klicken Sie dann **– Speech**, in der angegebenen Reihenfolge. Wenn Sie nicht die Abhängigkeiten sicher sind, ist es OK, um alle im selben Ordner ablegen und dann alle mit dem gleichen DISM/Add-Package Befehl hinzufügen. Nicht jede Region verfügt über Schriftarten oder Funktion Packs für jedes Feature.

    Beispiel:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\fr-fr x64\lp.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab" /LogPath=C:\mount\dism.log
    ```

2.  Stellen Sie sicher, dass das Sprachpaket Teil des Bilds ist:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.10020.0
    State : Installed
    ```

3.  Überprüfen Sie, ob die Sprachkomponenten Teil des Bilds sind:

    ``` syntax
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste der Pakete enthält. Beispiel:

    ``` syntax
    Capability Identity : Language.Basic~~~fr-fr~0.0.1.0
    State : Installed
    ...
    Capability Identity : Language.Handwriting~~~fr-fr~0.0.1.0
    State : Installed
    ```

4.  Ändern Sie die Standardsprache, um die bevorzugte Sprache für Ihre Kunden übereinstimmen.

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\windows
    ```

**Schritt 7: Entfernen der Ausgangssprache (nur für nicht-englischen Regionen erforderlich)**

1.  Um Speicherplatz zu sparen, können Sie englische Komponenten entfernen, wenn Sie für nicht-englischen Regionen bereitstellen. Sie müssen deinstallieren Sie diese in umgekehrter Reihenfolge aus, wie Sie diese hinzufügen.

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks.

2.  Stellen Sie sicher, dass das Sprachpaket nicht mehr Teil des Bilds ist:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

3.  Stellen Sie sicher, dass die Language-Komponenten nicht mehr Teil des Bilds sind:

    ``` syntax
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

4.  Entfernen Sie die optionalen Windows RE-Komponenten. Nach dem entfernen, vergewissern Sie sich, dass sie nicht mehr in das Bild befinden.

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

5.  **Bekanntes Problem**: Wenn Sie das englische Sprachpaket in Windows 10 erstellen 10240 entfernt haben, müssen Sie das Bild im Überwachungsmodus starten und verwenden Sie den Befehl: `sfc.exe /scannow /verify` Probleme mit Windows 32-Bit-apps zu reparieren. Ein Beispiel dafür, wie Sie mit einem Skript dazu, finden Sie unter [Lab 2a: Antwortdateien: Aktualisieren von Einstellungen und Ausführen von Skripts](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md).

**Schritt 8: Neuinstallation Posteingang apps (bei jedem Hinzufügen von Sprachen erforderlich)**

1.  Entfernen Sie die vorhandenen Posteingang apps. **(Dieser Schritt ist nicht erforderlich, wenn Sie nach 18 August 2015 abgerufen universelle apps verwenden)**. Das folgende Beispiel veranschaulicht die Posteingang Einstieg in die app zu entfernen. Wiederholen Sie diese Schritte für jede der apps Posteingang (mit Ausnahme von AppConnector), indem Sie das entsprechende Paket ersetzen.

    ``` syntax
    Dism /Image:"c:\mount\windows" /Remove-ProvisionedAppxPackage /PackageName:Microsoft.Getstarted_2015.522.28.1146_neutral_~_8wekyb3d8bbwe
    ```

    **Hinweis**  Um alle apps gleichzeitig zu entfernen, öffnen Sie ein Eingabeaufforderungsfenster als Administrator, navigieren Sie zum Bildordner, und führen Sie das Beispielskript: "entfernen\_apps\_in\_offline\_image.cmd" aus den [Beispielskripts](windows-deployment-sample-scripts-sxs.md).

     

2.  Installieren Sie erneut die apps. Im folgende Beispiel veranschaulicht das die Posteingang Einstieg in die app installieren. Wiederholen Sie diese Schritte für jede der apps Posteingang (mit Ausnahme von AppConnector), indem Sie das entsprechende Paket ersetzen.

    ``` syntax
    Dism /Image:"c:\mount\windows" /Add-ProvisionedAppxPackage /packagepath:<path to appxbundle>\2b362ab83144485d9e9629ad2889a680.appxbundle /licensepath:<path to license file>\2b362ab83144485d9e9629ad2889a680_License1.xml
    ```

**Schritt 9: Hinzufügen von apps für Windows universelle oder 8.1 Windows Store-apps (Optional)**

1.  Mithilfe von DISM können Sie Ihr Bild universellen Windows-apps und Windows 8.1 Store-apps hinzufügen. In diesem Beispiel werden Sie Office OneNote und Windows Reader 8.1 vorinstallieren.

    Überspringen Sie diesen Schritt für Hardwarekonfiguration 1.

    Fügen Sie das Paket AppX hinzu.

    ``` syntax
    Dism /Image:c:\mount\windows /Add-ProvisionedAppxPackage /PackagePath:c:\samples\excelpreview\excel.appxbundle /LicensePath:c:\samples\excelpreview\excel_license.xml
    ```

    Der PackagePath, in dem Sie die app-Paket Bundle verweist.

2.  Wiederholen Sie den Befehl DISM für die OneNote, Leser, Word und PowerPoint Preview app Bundle-Pakete.

Wenn der PC-Option Probleme ausgeführt wird, ist Ihre Benutzer möglicherweise nicht in der Lese-/Wiederherstellung Bildschirmen verstehen, wenn Sie die entsprechende Sprachressourcen in Windows Recovery Environment (Windows RE) hinzufügen.

Nach Möglichkeit zum Hinzufügen und Entfernen von Sprachen in Windows RE gleichzeitig versuchen, die Sie hinzufügen und entfernen Sie sie in das Windows-Abbild, um sicherzustellen, dass eine konsistente Recovery Erfahrung. (Dies ist nicht immer möglich, wie nicht in allen Sprachen Windows RE-Entsprechungen verwendet werden.)

**Schritt 10: Hinzufügen von Sprachen für die wiederherstellungsumgebung (dringend empfohlen, beim Hinzufügen von Sprachen)**

1.  Hinzufügen von Sprachen. Diese Sprachen sind in der Windows-ADK enthalten. Sie müssen eine entsprechende Version von Windows ADK verwenden, die Windows RE-Abbild.

    **Hinweis**  Windows RE erfordert jetzt das Windows PE-HTA-Paket, dies ist neu in Windows 10.

    **Hinweis**  Das Windows PE-WLAN-Paket ist nicht sprachspezifische und muss nicht hinzugefügt werden, wenn andere Sprachen hinzufügen. Dies ist neu in Windows 10.

    ``` syntax
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

2.  Legen Sie die Standardsprache für die Wiederherstellung die bevorzugte Sprache für Ihre Kunden übereinstimmen.

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\winre
    ```

3.  Optional: Entfernen von Sprachen in Windows RE (nur für nicht-englischen Regionen erforderlich)

    Beim Entfernen von Sprachen aus Windows entfernen Sie sie aus Windows RE, um Speicherplatz einzusparen.

    Sie können entweder/PackagePath Switches (eine entsprechende Version von Windows und Windows ADK erforderlich) oder der Option/PackageName (Dies ist erforderlich, identifiziert das Paket, einschließlich der Versionsnummer).

    Beispiel:

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    ```

4.  Überprüfen Sie, ob die Sprachpakete Teil des Bilds sind:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

5.  Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Microsoft-Windows-WinPE-Rejuv_fr-fr ...  fr-FR~10.0.9926.0
    State : Installed
    ```

## <a name="span-idmodifyspanspan-idmodifyspanother-modifications"></a><span id="modify"></span><span id="MODIFY"></span>Sonstige Änderungen


**Schritt 11: Aktualisieren der Edition von Kern pro (Optional)**

1.  Verwenden Sie dieses Verfahren, um die Edition zu aktualisieren. Ein Windows-Bild kann nicht auf eine niedrigere Edition festgelegt werden. Sie sollten dieses Verfahren nicht auf ein Bild verwenden, die bereits auf eine höhere Edition geändert wurde.

    Bestimmen, welche Bilder Sie das Bild aktualisieren können: Beachten Sie die Edition IDs verfügbar.

    ``` syntax
    Dism /Get-TargetEditions /Image:C:\mount\windows
    ```

2.  Aktualisieren der Edition.

    ``` syntax
    Dism /Set-Edition:Professional /Image:C:\mount\windows
    ```

## <span id="unmount"></span><span id="UNMOUNT"></span>


**Schritt 12: Heben Sie die Bereitstellung der Bilder**

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.
2.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows RE-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

3.  Stellen Sie eine Sicherungskopie der aktualisierten Windows RE-Abbild (optional). Dadurch können Sie Ihre Arbeit zu speichern, für den Fall, dass das Windows-Abbild beschädigt.

    ``` syntax
    xcopy C:\mount\windows\Windows\System32\Recovery\winre.wim C:\Images\winre_with_drivers_for_fabrikam_model_1.wim /ah
    ```

    Geben Sie bei Aufforderung **F** für Datei.

    **Hinweis**  Diesem Lab wird davon ausgegangen, dass Sie vielmehr winre.wim in install.wim auf die Sprachen und die Treiber synchron zu halten beibehalten möchten. Wenn Sie etwas Zeit werksseitige speichern möchten, und wenn Sie diese Bilder OK separat verwalten, empfiehlt es sich, entfernen winre.wim aus dem Bild und angewendet wird getrennt.

     

4.  Überprüfen Sie die neue Größe des Windows RE-Abbilds.

    ``` syntax
    Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"
    ```

    Wenn die Größe der Partition 524,288,000 Bytes größer ist, konvertieren Sie die Dateigröße in Megabyte freien Speicherplatz hinzufügen und ändern Sie das Bereitstellungsskript: CreatePartitions -&lt;Firmware&gt;.txt mit dem neuen Wert. Weitere Informationen zum freien Speicherplatz Empfehlungen finden Sie unter [UEFI/GPT-basierten Festplattenpartitionen](http://go.microsoft.com/fwlink/?LinkId=526950). Beispiel:

    ``` syntax
    rem == 3. Windows RE tools partition ===============
    create partition primary size=600
    ```

5.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    Dabei ist *C* der Laufwerkbuchstabe des das Laufwerk mit dem Bild.

    Dieser Vorgang kann einige Minuten dauern.

**Schritt 13: Kopieren der Skripts Bild und Bereitstellung in einen USB-Schlüssel**

1.  Schließen Sie den Windows PE USB-Schlüssel, und notieren Sie den Laufwerkspeicherort, z. B. **D:**.
2.  Kopieren Sie das Bild und die vorgefertigten Bereitstellungsskripts beispielsweise auf einen USB-Schlüssel:

    ``` syntax
    copy C:\Images\WindowsWithOffice.wim D:

    copy C:\Samples\Scripts\* D:
    ```

    **Hinweis**  Wenn die Taste Windows PE genügend Speicherplatz vorhanden ist, kopieren Sie das Bild und die Skripts auf einem anderen USB-Schlüssel.

    **Hinweis**  Wenn das Bild größer als 4 GB ist, müssen Sie den USB-Schlüssel mit dem NTFS-Dateiformat Vorformatieren.

     
**Schritt 14: Anwenden von Windows-Abbildern mithilfe eines Skripts**

-   Verwenden Sie Bereitstellungsskripts, um eine neu erfasste Bild auf einem Testgerät anzuwenden. Diese Skripts richten Sie die Festplattenpartitionen und fügen Sie die Dateien aus dem Windows-Abbild auf die Partitionen.

    **Hinweis**  In Windows 10 haben wir das Partitionslayout geändert. Während wir noch Image-Tools separate Wiederherstellung verwenden, benötigt Windows nicht mehr einer separaten Wiederherstellung des gesamten Systems Drucktaste zurücksetzen Features zu verwendende Bild zu. Dies kann mehrere GB Speicherplatz sparen. Außerdem verwenden wir eine kleinere GPT (unten 128MB 16 MB).
    
    **Hinweis**  Sie können die [Beispielskripts](windows-deployment-sample-scripts-sxs.md) für verschiedene Firmware Gerätetypen (die neuere UEFI-basierten, oder der Vorversion BIOS) verwenden. Einige UEFI-basierte Geräte beinhalten Unterstützung für das ältere legacy-BIOS. Weitere Informationen finden Sie unter [UEFI Firmware](http://go.microsoft.com/fwlink/?LinkId=526945).

    ![Bild zeigt an, um einen Referenzcomputer mit Anpassungen erstellen, einen neuen Computer, eine Bilddatei und Bereitstellungsskript benötigen.](images/dep-win8-sxs-createdeploymentscript.jpg)

**Schritt 15: Formatieren Sie, und richten Sie die Festplattenpartitionen auf dem Gerät Verweis**

1.  Starten Sie das Gerät Verweis zu Windows PE, mit dem Windows PE USB-Schlüssel.
2.  Suchen Sie nach der Laufwerkbuchstabe des USB-Schlüssels mithilfe von Diskpart:

    ``` syntax
    diskpart
    DISKPART> list volume
    DISKPART> exit
    ```

    Beispielsweise die Laufwerke können werden mit einem Buchstaben gekennzeichneten wie folgt: C = Windows; D = USB-Laufwerk.

3.  Formatieren Sie die primäre Festplatte, erstellen Sie die Partitionen, und wenden Sie das Abbild mithilfe der vorbereiteten [Beispielskripts](windows-deployment-sample-scripts-sxs.md). Das Skript **ApplyImage.bat** nutzt diese anderen Skripts im gleichen Ordner platziert werden:

    -   **CreatePartitions UEFI.txt**
    -   **CreatePartitions BIOS.txt**
    -   **HideRecoveryPartitions UEFI.txt**
    -   **HideRecoveryPartitions-BIOS.txt:**

    Sie können die Skripts aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=800657)herunterladen. 

    ``` syntax
    D:
    D:ApplyImage.bat D:\WindowswithOffice.wim
    ```

    Dabei ist *D* der Laufwerkbuchstabe des USB flash-Laufwerk.

    Bei Aufforderung durch das Skript: 
    
    -  Geben Sie Y ein, um das Laufwerk formatieren 
    -  Drücken Sie Y ein, um Compact OS oder N wählen Sie ein Betriebssystem nicht komprimiert auswählen:
        -   **Y**: das Bild mit Compact OS gilt. Dies ist am besten für Geräte mit Solid-State und Laufwerke mit beschränktem freien Speicherplatz. Verwenden Sie dies für Hardwarekonfiguration 1 und 2 aus.
        -   **N**: das Bild als Bild vollständig dekomprimiert gilt. Dies ist am besten für High Performance Geräte oder Geräte, die herkömmliche Festplatten mit Rotation Media verwenden. Verwenden Sie dies für Hardwarekonfiguration 3.
    -  Drücken Sie N, um anzugeben, dass das Bild enthält keinen erweiterten Attribute (EA).

    Die Skripts wenden Sie das Abbild auf dem Laufwerk, und dann auf Fertig stellen.

**Schritt 16: Neustarten des Geräts**

-   Trennen Sie den USB-Laufwerk und das externe USB-Festplatte und Typ `exit`.

    Während der Vorbereitungsphase für die Durchführung warten Sie zurück zu Ihrem PC-Techniker, und fahren Sie mit dem Labor.

    **Warnung** **Problembehandlung**: Wenn das Gerät nicht gestartet wird, aktivieren Sie das Gerät, und drücken Sie den Schlüssel, der das Auswahlmenü Startvolumes (beispielsweise die **Esc** -Taste) wird geöffnet.  

     

 

 





