---
author: KPacquer
Description: "Übung 5: Hinzufügen von Sprachen"
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 5: Hinzufügen von Sprachen"
ms.openlocfilehash: dd2be5018db5793ad4e72818f4c11590b62ba557
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idaddlanguagesspanlab-5-add-languages"></a><span id="Add_languages"></span>Übung 5: Hinzufügen von Sprachen

**Notizen** 

*    **Hinzufügen von Updates vor Sprachen.** Dazu gehören Hotfixes, die allgemein verfügbare Versionen und Servicepacks. Wenn Sie ein Update später hinzufügen möchten, müssen Sie die Sprache erneut hinzufügen.

*    **Sprachen hinzufügen, bevor Sie apps**. Dazu gehören universellen Windows-apps, die **Posteingang apps (erforderlich)** und -desktopanwendungen. Zeigen wir Ihnen diese hinzufügen wie weiter unten in [Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste Pins](add-universal-apps-sxs.md)

*    **Ihre Sprachen zu Ihrem Wiederherstellungsabbild zu hinzufügen**: viele allgemeine Sprachen können zum Recovery-Abbild hinzugefügt werden. Zeigen wir Ihnen diese hinzufügen wie weiter unten in [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md).

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>Stellen Sie das Abbild

**Schritt 1: Stellen Sie das Abbild**

Verwenden Sie die Schritte auf [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) zum Bereitstellen des Abbilds. Die Kurzversion:

1.  Öffnen Sie als Administrator der Befehlszeile (**Starten** > geben **Bereitstellung** > Maustaste **Bereitstellung und Imaging Tools Umgebung** > **als Administrator ausführen**.)

2.  Erstellen Sie eine Sicherungskopie der Datei (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  Stellen Sie das Abbild (`md C:\mount\windows`, klicken Sie dann `Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddlanguagestotheimagespanadd-languages-to-the-image"></a><span id="Add_languages_to_the_image"></span>Hinzufügen von Sprachen für das Bild

Verwenden Sie immer Language Packs und Features-On-Demand (Departements)-Pakete, die mit der Sprache des Windows-Bilds Plattform übereinstimmen.

Features bei Bedarf (FODs) sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Wenn ein Benutzer ein neues Feature benötigt, können sie das Feature Packs von Windows Update anfordern. OEMs können diese Features aktivieren auf ihren Geräten sofort einsetzbar vorinstallieren.

Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung. Einige dieser Features müssen alle Cortana-Funktionen zu aktivieren.

Die folgende Tabelle zeigt die Typen von Language Packs und Komponenten verfügbar sind für Windows 10:

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
<td align="left"><code>Microsoft-Windows-Client-Language-Pack_x64_es-es</code></td>
<td align="left">Keine</td>
<td align="left">Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.</td>
</tr>
<tr class="even">
<td align="left">Benutzeroberflächen-Sprachpaket</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es</code></td>
<td align="left">Erfordert ein bestimmtes vollständig lokalisierte oder teilweise lokalisierte Language Pack. Beispiel: ca-ES erfordert es-ES. Weitere Informationen finden Sie unter <a href="available-language-packs-for-windows.md">Verfügbaren Language Packs für Windows</a>.</td>
<td align="left"><p>Benutzeroberflächentext, einschließlich der Grundfunktionen Cortana.</p></td>
</tr>
<tr class="odd">
<td align="left">Standard</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Rechtschreibprüfung, Textvorhersage, Wortumbruch und Silbentrennung Wenn für die Sprache zur Verfügung.</p>
<p>Sie müssen diese Komponente vor dem Hinzufügen der folgenden Komponenten hinzufügen.</p></td>
</tr>
<tr class="even">
<td align="left">Schriftarten</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Schriftarten.</p>
<p>Erforderlich für einige Regionen zum Rendern von Text, der in Dokumenten angezeigt wird. Beispielsweise ten-ten erfordert das Schriftart Thai Pack. Weitere Informationen finden Sie unter <a href="features-on-demand-v2--capabilities.md">Features auf Anforderung V2 (Funktionen).</p></td>
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
<td align="left">Ermöglicht die handschrifterkennung für Geräte mit Input Stift.</td>
</tr>
<tr class="odd">
<td align="left">Text-Sprach-</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Text zu Sprachein-und-Ausgabe, von Cortana und Sprachausgabe verwendet werden können.</td>
</tr>
<tr class="even">
<td align="left">Spracherkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package</code></td>
<td align="left">Grundlegende, Sprachausgabe Spracherkennung</td>
<td align="left">VoIP erkennt Eingaben, von Cortana und Windows-Spracherkennung verwendet werden.</td>
</tr>
<tr class="even">
<td align="left">Retail Demo Erfahrung</td>
<td align="left"><code>Microsoft-Windows-RetailDemo-OfflineContent-Content-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">[Retail Demo Erfahrung](https://msdn.microsoft.com/windows/uwp/monetize/retail-demo-experience)</td>
</tr>
</tbody>
</table>

**Schritt 2: Hinzufügen oder Ändern von Sprachen**

1.  Hinzufügen von Sprachen und Features auf Anforderung auf dem Windows-Abbild.

    Updates für Language müssen eine bestimmte Reihenfolge benötigten in installiert sein. Beispielsweise um Cortana aktivieren möchten, installieren: **Microsoft Windows-Client-Language Pack**, klicken Sie dann **– grundlegende**, klicken Sie dann **– Schriftarten**, und klicken Sie dann **– TextToSpeech**, und führen Sie dann **– Speech**, in der angegebenen Reihenfolge. Wenn Sie die Abhängigkeiten nicht wissen, ist dies für alle im selben Ordner ablegen und dann alle mit dem gleichen DISM/Add-Package Befehl hinzufügen. 
    
    Beispiel für das Hinzufügen von Französisch, X64:

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-Client-Language-Pack_x64_fr-fr" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab" /LogPath=C:\mount\dism.log
    ```

    Beispiel für Japanisch X64 hinzufügen. Beachten Sie, Japanisch eine Schriftart Pack ist erforderlich.

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-Client-Language-Pack_x64_ja-jp" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Basic-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-OCR-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Handwriting-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Speech-ja-jp-Package.cab" /PackagePath:"C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package.cab"  /LogPath=C:\mount\dism.log
    ```

    Nicht jede Region verfügt über Schriftarten oder Funktion Packs für jedes Feature.

2.  Stellen Sie sicher, dass das Sprachpaket Teil des Bilds ist:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.14393.0
    State : Installed
    ```

3.  Stellen Sie sicher, dass die Sprachkomponenten Teil des Bilds sind:

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
    Dism /Set-AllIntl:fr-fr /Image:"C:\mount\windows"
    ```
    
5.  Ändern der standardmäßigen Timezone entsprechend die Zeitzone für Ihre Kunden. [Liste der Timezones](default-time-zones.md)angezeigt.

    ``` syntax
    Dism /Set-TimeZone:"W. Europe Standard Time" /Image:"C:\mount\windows"
    ```

**Schritt 3: Entfernen der Ausgangssprache (nur für nicht-englischen Regionen erforderlich)**

1.  Um Speicherplatz zu sparen, können Sie englische Komponenten entfernen, wenn Sie für nicht-englischen Regionen bereitstellen. Sie können entweder deinstallieren Sie diese in umgekehrter Reihenfolge aus, wie Sie hinzufügen oder entfernen sie alle Kontakte gleichzeitig in demselben Befehl DISM/Remove-Package.

    ``` syntax
    dism /Remove-Package /Image:"c:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0  /LogPath=C:\mount\dism.fod2.log
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks.

    **Problembehandlung** Wenn das Paket entfernt aufgrund von ausstehende Updates fehlschlägt, führen Sie den Befehl erneut aus. 

2.  Stellen Sie sicher, dass das Sprachpaket nicht mehr Teil des Bilds ist:

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des das Laufwerk mit dem Bild.

3.  Stellen Sie sicher, dass die Language-Komponenten nicht mehr Teil des Bilds sind:

    ``` syntax
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

    Dabei ist *C* der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.
    ```


## <span id="Unmount_the_images"></span> Unmount the images

**Step 4: Unmount the images**

1.  Close all applications that might access files from the image.

2.  Commit the changes and unmount the Windows image:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

**Schritt 5: Wenden Sie das Abbild auf einen neuen PC**

Die Schritte von [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md) um das Bild auf den Speicher, USB-Laufwerk zu kopieren, wenden Sie das Abbild, und starten. Die Kurzversion:

1.  Kopieren Sie die Bilddatei mit dem Speicherlaufwerk.
2.  [Boot Verweis Gerät, um Windows PE mit Windows PE USB-Taste](install-windows-pe-sxs.md).
3.  Suchen Sie nach der Laufwerkbuchstabe des Laufwerks Speicher (`diskpart, list volume, exit`).
4.  Wenden Sie das Abbild: `D:\ApplyImage.bat D:\Images\install.wim`.
5.  Die Laufwerke, auf Trennen und dann neu starten (`exit`).

**Schritt 6: Überprüfen Sie, ob updates**

1.  Nach der PC startet, wenn Sie mehrere Sprachen installiert haben, erhalten Sie eine Liste der Lanugages während der Out-of-Box-Experience. 

2.  Entweder erstellen Sie ein neues Benutzerkonto zu, andernfalls drücken Sie STRG + UMSCHALT + F3 in das integrierte Administratorkonto (Dies ist auch bekannt als Überwachungsmodus) neu starten.

3.  Klicken Sie mit der rechten Maustaste auf **Start** , und wählen Sie **die Befehlszeile (Admin)**.

4.  Stellen Sie sicher, dass die Sprachpakete ordnungsgemäß angezeigt werden:

    ``` syntax
    C:\Windows\System32\Dism /Get-Packages /Online
    ```

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.14393.0
    State : Installed
    ```
    
Nächster Schritt: [Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste Pins](add-universal-apps-sxs.md)