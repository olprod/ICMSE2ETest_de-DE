---
author: KPacquer
Description: "Übung 1: Anpassen und Installieren von Windows mithilfe von Windows Imaging und Konfiguration Designer (ICD)"
ms.assetid: 97f2cc2b-ae4b-4117-a73b-42e508fe7a03
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 1: Anpassen und Installieren von Windows mithilfe von Windows Imaging und Konfiguration Designer (ICD)"
ms.openlocfilehash: 9e846ee5fb866fb7d589fd7bcbe0fa9795f36ac0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1-customize-and-install-windows-using-the-windows-imaging-and-configuration-designer-icd"></a>Übung 1: Anpassen und Installieren von Windows mithilfe von Windows Imaging und Konfiguration Designer (ICD)


Die schnellste Methode zum Bereitstellen von benutzerdefinierten Windows-Geräte ist durch Erstellen von startbaren USB-Schlüsseln mithilfe von Windows Imaging und Konfiguration Designer (ICD). Mit diesem Tool können Sie die Gerätetreiber installieren, Systemeinstellungen festlegen und Sprachen hinzufügen, sodass Sie schnell Windows auf Test- oder Verkaufsversion Geräten installieren können.

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
| Office 2013                  | Nein           | Ja                 | Ja                               |
| Compact OS                   | Ja          | Ja                 | Nein                                |

 
, ## <span id="loadImage"> </span> <span id="loadimage"> </span> <span id="LOADIMAGE"> </span>Schritt 1: Erstellen eines neuen Projekts in Windows ICD


1.  Klicken Sie auf **Start**, geben Sie **Icd**, und klicken Sie dann auf **Windows Imaging und Konfiguration-Designer**.

    Wenn das Fenster **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Ja**.

2.  Klicken Sie auf **neue Windows-Abbild anpassen**.
3.  Anhand der folgenden Informationen, und klicken Sie dann auf **Weiter**, auf der Seite **Projektdetails eingeben** :
    -   Geben Sie im Feld **Name den Namen** **Fabrikam\_Notizbuch\_1**.
    -   Lassen Sie das **Projektordner** als-ist.
    -   Geben Sie im Feld **Beschreibung** **Basis Hardware-Design für Fabrikam Notizbuch PC Reihe 1**ein.

4.  Klicken Sie auf der Seite **Wählen Sie imaging Quellformat** auf **der Windows-Abbild basiert auf einem Windows-Abbilddatei (WIM)** &gt; **Weiter**.
5.  Klicken Sie auf der Seite **Bild auswählen** auf **Durchsuchen**.
    -   Navigieren Sie zu **C:\\Bilder\\Win10\_X64\\Quellen**, klicken Sie auf **install.wim**, und klicken Sie dann auf **Öffnen**.
    -   Arbeiten mit Design 1 Wählen Sie 10 Startseite. Arbeiten mit Design 1 b Wählen Sie Windows 10 Pro aus.
    -   Klicken Sie auf **Weiter**.

6.  Klicken Sie auf der Seite **Importieren eines Pakets Provisioning (Optional)** Wenn Sie eine Bereitstellung-Paket (ähnlich, die Sie in Übung 1 b erstellen), haben können Sie jetzt hinzufügen, und klicken Sie dann auf **Fertig stellen**. Andernfalls können Sie diesen Schritt leer lassen, und klicken Sie auf **Fertig stellen**.

Das Projekt wird erstellt und das Hauptfenster bearbeiten angezeigt.

**Problembehandlung:** Wenn Sie beim Erstellen des Projekts eine Fehlermeldung erhalten, stellen Sie sicher, dass Sie das Windows-Abbild von einem dedizierten Downloadcenter für OEMs und System-Builder erhalten haben. [Windows 10-Installationsmedium](http://go.microsoft.com/fwlink/p/?LinkId=626022) , die mit dem Tool zum Erstellen von Medien heruntergeladen werden können, kann nicht mit Windows Imaging-Tools verwendet werden.

## <a name="span-idstep2addtheuniversalwindowsappsandwindows81appsoptionalspanspan-idstep2addtheuniversalwindowsappsandwindows81appsoptionalspanstep-2-add-the-universal-windows-apps-and-windows-81-apps-optional"></a><span id="step_2__add_the_universal_windows_apps_and_windows_8.1_apps__optional_"></span><span id="STEP_2__ADD_THE_UNIVERSAL_WINDOWS_APPS_AND_WINDOWS_8.1_APPS__OPTIONAL_"></span>Schritt 2: Hinzufügen der universellen Windows-apps und apps für Windows 8.1 (Optional)


Das Bild kann universellen Windows-apps vorab laden, damit sie auf dem Computer verfügbar, sind Wenn Ihre Kunden PC zum ersten Mal starten. Mit Windows-ICD fügen Sie Windows 8.1 apps die gleiche Weise Sie Ihr Bild universellen Windows apps hinzu.

Für Hardwarekonfiguration 1 können Sie diesen Schritt überspringen, wenn kein Geräts Bilanz wenig apps, die hinzugefügt werden soll.

In dieser exemplarischen Vorgehensweise fügen wir die Vorschau von Office-apps (Word, Excel und PowerPoint). Wiederholen Sie diese Schritte für alle apps für universelle Windows und Windows 8.1-apps, den, die Sie dem Bild hinzufügen möchten.

1.  Erweitern Sie **Bereitstellung Anlagen**in Windows ICD, unter **Verfügbare Anpassungen**und klicken Sie dann auf **Applications**.
2.  Klicken Sie im Feld **Pfad für das Paket** auf **Durchsuchen**. Ändern die Ansicht auf **Anwendungspakets (\*.appxbundle)**, wählen Sie das Word-Vorschau app Bundle-Paket, und klicken Sie dann auf **Open.**
3.  Geben Sie im Feld **Name den Namen** **Word Preview**aus.
4.  Klicken Sie im Feld **Pfad Lizenz** auf **Durchsuchen**. Wählen Sie die Word-Vorschau-Lizenz-Datei, und klicken Sie dann auf **Öffnen**.
5.  Klicken Sie auf **Hinzufügen**. Name der app sollte im Bereich **ausgewählte Anpassungen** angezeigt werden.

Wiederholen Sie die Schritte 1 bis 5 für die Vorschau von Excel und PowerPoint-Vorschau app Bundle Pakete und alle anderen apps für universelle Windows und Windows 8.1-apps, den, die Sie dem Bild hinzufügen möchten. OneNote und Reader 8.1-apps sind auf dem Ereignis bereitgestellten USB enthalten.

## <a name="span-idadddriverspanspan-idadddriverspanspan-idadddriverspanstep-3-add-a-driver-to-the-image"></a><span id="addDriver"></span><span id="adddriver"></span><span id="ADDDRIVER"></span>Schritt 3: Hinzufügen eines Treibers für das Bild


Windows-ICD können Sie Ihre eigene INF-basierte Treiber für das Abbild hinzufügen.

1.  In Windows-ICD unter **Verfügbare Anpassungen**erweitern Sie **Bereitstellung Objekte**und klicken Sie dann auf **Treiber**.
2.  Klicken Sie im mittleren Bereich neben **Ordnerpfad Treiber**auf **Durchsuchen**. Navigieren Sie zu der Treiber INF-basierte, und klicken Sie dann auf OK.

    Die INF-Datei wird im Feld **Treiber** angezeigt. Wenn mehrere Treiber in diesem Ordner vorhanden sind, werden alle Treiber in dem Ordner hinzugefügt werden.

    **Hinweis**  Einige Treiber sind als ZIP oder .exe-Dateien enthalten. Sie müssen Entzippen oder vor dem Hinzufügen dieser Dateien zu extrahieren. Einige Treiberdateien, wie der Beispieltreiber angegeben, include-Dateien für X86 und X64 Geräte ist dies OK.

     

3.  Geben Sie im Feld **Name den Namen** *"Fabrikam" Video Karte 100*.

    Wenn Sie neue Geräteentwürfe Prototyp oder Vorabversion Treiber vom Hardwarehersteller testen, aktivieren Sie das Kontrollkästchen **erzwingen, dass nicht signierte installieren** und dann auf **Hinzufügen**. Der beschreibende Name des Treibers sollte im Bereich **ausgewählte Anpassungen** angezeigt werden.

## <a name="span-idaddsettingsspanspan-idaddsettingsspanspan-idaddsettingsspanstep-4-add-some-customized-settings-to-the-image"></a><span id="addSettings"></span><span id="addsettings"></span><span id="ADDSETTINGS"></span>Schritt 4: Hinzufügen von einigen benutzerdefinierten Einstellungen für das Bild


1.  In Windows ICD, klicken Sie im Bereich **Verfügbare Anpassungen** erweitern Sie- **Bild Zeiteinstellungen**, und klicken Sie dann auf **OEM**.
2.  Geben Sie im mittleren Bereich im Feld *Name den Namen* **Fabrikam**.
3.  Klicken Sie im **Anpassungen verfügbar** unter **OEM**, klicken Sie auf **Informationen.**

    Füllen Sie die folgenden Informationen ein:

    -   Geben Sie im Feld **Hersteller** **Fabrikam**.
    -   Geben Sie im Feld **SupportHours** **8 bis 5 Uhr**.
    -   Geben Sie im Feld **SupportPhone** **555-1212**.
    -   Geben Sie im Feld **SupportURL** **http://support.fabrikam.com**ein.

Klicken Sie im Bereich **ausgewählte Anpassungen** werden die Einstellungen angezeigt.

## <a name="span-idstep5customizethestartlayoutspanspan-idstep5customizethestartlayoutspanspan-idstep5customizethestartlayoutspanstep-5-customize-the-start-layout"></a><span id="Step_5__Customize_the_Start_layout"></span><span id="step_5__customize_the_start_layout"></span><span id="STEP_5__CUSTOMIZE_THE_START_LAYOUT"></span>Schritt 5: Anpassen des Layouts Start


In Windows 10 können OEMs das Standardlayout Start ändern und das Layout von OEM-Kacheln angeben, indem Sie eine **LayoutModification.xml** -Datei erstellen, und platzieren diese Datei in den richtigen Systemspeicherort.

1.  Erstellen Sie eine layoutmodification.xml-Datei. Für diese Übungseinheit können Sie das Beispiel auf den USB-verwenden. Im Beispiel wird Office, OneNote und Reader 8.1 beginnen anheften, wenn sie auf dem Gerät (Schritt2) vorinstallierte wurden. Eine eigene Datei layoutmodification.xml erstellen mithilfe eines XML-Editor, finden Sie unter die [Beispielskripts](windows-deployment-sample-scripts-sxs.md).
2.  Einstellungen Sie in Windows ICD, klicken Sie im Bereich **Verfügbare Anpassungen** **Runtime**-, klicken Sie auf **Start**und klicken Sie dann auf **StartLayout**.
3.  Klicken Sie im mittleren Bereich auf **Durchsuchen.**
4.  Navigieren Sie zu dem Speicherort die Datei LayoutModification.xml.
5.  Wählen Sie die Datei aus, und klicken Sie dann auf **Öffnen**. Den Wert der StartLayout sollte festgelegt.

    Die Einstellung wird in den Bereich ausgewählte Anpassungen.

    **Hinweis**  Sie können nicht direkt in Windows ICD URL und lnk-Dateien hinzufügen. Wenn Sie diese Dateien haben, führen Sie Schritt2 in Übung 2 im Abschnitt "Hinzufügen die Dateien, die Sie das Layout Start ändern müssen".

     

## <a name="span-idaddlangspanspan-idaddlangspanspan-idaddlangspanstep-6-add-a-language"></a><span id="addLang"></span><span id="addlang"></span><span id="ADDLANG"></span>Schritt 6: Hinzufügen einer Sprache


Windows-ICD bietet eine einfache Methode zum Hinzufügen von Sprachen.

1.  In Windows ICD, klicken Sie im Bereich **Verfügbare Anpassungen** erweitern Sie **Bereitstellung Objekte**und klicken Sie dann auf **Language Packs**.
2.  Klicken Sie im mittleren Bereich neben **CAB-Datei**auf **Durchsuchen**. Navigieren Sie zu die Language Pack-Datei, z. B.: **C:\\Beispiele\\Sprachen\\fr-fr X64-Client**, klicken Sie auf **lp.cab**, und klicken Sie dann auf **Open.**
3.  Klicken Sie im Feld **Name** Geben Sie **französische Benutzeroberfläche**, und klicken Sie dann auf **Hinzufügen**.

    Das Language Pack sollte im Bereich **ausgewählte Anpassungen** angezeigt werden.

Diese Methode wird die Sprachressourcen für Windows-Anwendungen auch nicht aktualisiert. Die Windows-Posteingang-apps, einschließlich. Während einige apps für Windows über Windows Update automatisch aktualisiert werden, möglicherweise andere Personen zu einem späteren Zeitpunkt erneut installiert werden müssen.

Um die Ressourcen für Windows RE und apps zu aktualisieren, ändern Sie das Windows install.wim Bild in die Anweisungen aus [Übung 2: Classic-Schreibweise Bereitstellung](part-2--classic-style-deployment.md). Können Sie die Schritte 4 und 5 (Windows-Treiber hinzufügen und Bearbeiten des Layouts Start) überspringen, und Sie können optionale Schritte 11 und 12 (aktualisieren die Windows-Edition und das Bild, das Starten im Überwachungsmodus festlegen) überspringen.

## <a name="span-idaddlangcompspanspan-idaddlangcompspanspan-idaddlangcompspanstep-7-add-features-on-demand"></a><span id="addLangComp"></span><span id="addlangcomp"></span><span id="ADDLANGCOMP"></span>Schritt 7: Hinzufügen von Features bei Bedarf


Features bei Bedarf (FODs) sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Wenn ein Benutzer ein neues Feature benötigt, können sie das Feature Packs von Windows Update anfordern. OEMs können diese Features aktivieren auf ihren Geräten sofort einsetzbar vorinstallieren.

Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung. Einige dieser Features sind erforderlich, um vollständige Cortana-Funktionen zu aktivieren. In der folgenden Tabelle zeigt die Typen der Sprachkomponenten verfügbar sind für Windows und Cortana, welche zuweisen.

Darüber hinaus Cortana aktivieren oder für die Unterstützung der Stift müssen Features in einer bestimmten Reihenfolge hinzugefügt werden. Installieren Sie beispielsweise um Cortana zu aktivieren, diese Features in dieser Reihenfolge: **lp.cab**; auf **grundlegende**, und klicken Sie dann **TextToSpeech**und anschließend auf **Sprache**. Um Stift Support zu aktivieren, installieren Sie diese Features in dieser Reihenfolge: **lp.cab**, auf **einfache**und anschließend auf **Handschrift**.

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

 

1.  In Windows ICD, klicken Sie im Bereich **Verfügbare Anpassungen** erweitern Sie **Bereitstellung Objekte**und klicken Sie dann auf **Features bei Bedarf**.
2.  Klicken Sie im mittleren Bereich, neben **Features Pfad zu packen**auf **Durchsuchen**. Navigieren Sie zu der Datei Departements beispielsweise: **C:\\Beispiele\\Sprachen\\fr-fr X64-Client**, klicken Sie auf **Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab**, und klicken Sie dann auf **Open.**
3.  Geben Sie im Feld **Name** **grundlegende französische Komponente**, und klicken Sie dann auf **Hinzufügen**.

    Die Sprachkomponente sollte im Bereich **konfigurierte Anpassungen** angezeigt werden.

4.  Klicken Sie im mittleren Bereich neben **CAB-Datei**auf **Durchsuchen**. Navigieren Sie zu der Datei Departements zum Beispiel: **C:\\Beispiele\\Sprachen\\fr-fr X64-Client**, klicken Sie auf **Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab**, und klicken Sie dann auf **Open.**
5.  Klicken Sie im Feld **Name** Geben Sie **französische Sprache Sprachkomponenten**, und klicken Sie dann auf **Hinzufügen**.

    Die Sprachkomponenten sollte im Bereich **Selected Anpassungen** angezeigt werden.

6.  Wiederholen Sie die Schritte aus, um die **Sprachsynthese** und **die** Komponenten hinzuzufügen. Die Sprachkomponenten sollte im Bereich **ausgewählte Anpassungen** angezeigt werden.
7.  Fügen Sie das Schriftart Pack für Sprachen, die Schriftarten, wie Chinesisch (vereinfacht), erfordern. Welche Sprachen Schriftarten erfordern finden Sie unter [Features auf Anforderung V2 (Funktionen)](features-on-demand-v2--capabilities.md).

    Klicken Sie im mittleren Bereich neben **CAB-Datei**auf **Durchsuchen**. Navigieren Sie zu der Datei Departements beispielsweise: **C:\\Beispiele\\Sprachen\\Zh-Cn X64-Client**, klicken Sie auf **Microsoft-Windows-LanguageFeatures-Fonts-Hans-Package.cab**, und klicken Sie dann auf **Öffnen**.

    Geben Sie in **das Feld** **die Sprachkomponente Schriftart für Chinesisch (vereinfacht)**, und klicken Sie dann auf **Hinzufügen**.

    Die Sprachkomponenten sollte im Bereich **konfigurierte Anpassungen** angezeigt werden.

**Hinweis**  
-   Die Sprache, in der Windows-Recovery-Umgebung von Windows ICD kann nicht aktualisiert werden. Standardmäßig werden ein Fehler auftritt, das Gerät Wiederherstellung Bildschirme auf Englisch nur angezeigt.
-   Sie führen Dism.exe (oder ein Skript), um nach dem Hinzufügen einer anderen Sprache Englisch zu entfernen. Ein Beispiel finden Sie unter [Übung 2: Classic-Schreibweise Bereitstellung](part-2--classic-style-deployment.md), Schritt 7.
-   Nach dem Hinzufügen einer Sprache, müssen Sie die universellen apps (APPX) erneut hinzufügen. Dieser Prozess muss im Überwachungsmodus ausgeführt werden. Weitere Informationen zum Entfernen, und fügen Sie diese Programme erneut hinzu, verweisen Sie auf [Übung 2: Classic-Schreibweise Bereitstellung](part-2--classic-style-deployment.md), Schritt 8. In Windows-10-Builds nach **18 August 2015**können Sie jetzt neue Universal apps (APPX) auf der Basis der vorhandene hinzufügen. Es ist nicht mehr erforderlich, die früheren Versionen zu entfernen, bevor Sie sie erneut hinzufügen.

 

## <a name="span-idbuildusbkeyspanspan-idbuildusbkeyspanspan-idbuildusbkeyspanstep-8-save-the-image"></a><span id="buildUSBKey"></span><span id="buildusbkey"></span><span id="BUILDUSBKEY"></span>Schritt 8: Speichern Sie das Bild


Windows-ICD können das gesamte Bild in eine einzelne gespeichert werden. FFU-Datei. Das Format FFU wurde mit Sektor-basierte Imaging und Sicherheit Kopfzeilen für die [Bereitstellung schneller und sicherer](wim-vs-ffu-image-file-formats.md) entwickelt.

1.  Klicken Sie auf **Erstellen** &gt; **Produktion Medien**.
2.  Wählen Sie **FFU** &gt; **Weiter**.
3.  Hardwareentwürfe 1 und 1 b Wählen Sie **Ja** unter **Compact OS aktivieren**aus, und klicken Sie dann auf **Weiter**.
4.  Der **Start konfigurieren im Überwachungsmodus**lassen Sie alle Optionen in der Standardeinstellung, und klicken Sie dann auf **Weiter**.
5.  Geben Sie **auswählen, auf dem die FFU-Datei gespeichert wurde**, in der Datei ein Name, beispielsweise C:\\Bilder\\MyFFUImage.ffu, und klicken Sie dann auf **Weiter**.
    **Hinweis**  Wir empfehlen Auswahl einer Position auf einer Festplatte statt einen USB-Schlüssel, wie es die FFU Erstellung beschleunigt werden kann.

     

6.  Überprüfen Sie die Einstellungen, und stellen Sie sicher, dass sie richtig sind. Klicken Sie auf **Erstellen**. Windows-ICD erstellt die FFU-Datei mit dem Namen und den im vorherigen Schritt angegebenen Pfad. Dies kann einige Minuten dauern. Klicken Sie auf **Fertig stellen**.

    **Problembehandlung: Wenn das Projekt nicht erstellen:**

    1.  Überprüfen Sie, stellen Sie sicher, dass der Projektname ist keine Leerzeichen beginnen oder enden. Wenn vorhanden ist, erstellen Sie das Projekt neu.
    2.  **Der angeforderte Vorgang konnte nicht abgeschlossen werden, aufgrund einer Datei Uploaddatei**: Stellen Sie sicher, dass das Laufwerk mit dem NTFS-Dateiformat formatiert ist und dass mindestens 5 GB freiem.
    3.  Wenn jederzeit Sie wiederholte in dieser exemplarischen Vorgehensweise, schließlich Wenn Sie die dasselbe Projekt verwenden möchten, löschen Sie den vorhandenen Projektordner aus **Dokumente\\Windows Imaging und Konfiguration Designer (WICD)** bevor erneut starten.

7.  Kopieren Sie die FFU-Datei auf einen Wechseldatenträger, wie ein separater USB-Schlüssel oder eine externe USB-Laufwerk ein. Möglicherweise müssen Sie das Laufwerk mit dem NTFS-Format, sodass sehr große Dateien - je nachdem, wie viele Sprachen, Treibern und apps, die Sie hinzufügen akzeptieren, neu formatiert die. FFU Datei kann auf einfache Weise 5GB oder mehr. Wahrscheinlich nicht möglich, verwenden Sie die Taste Windows PE für dieses – mit FAT32, die nur Dateien akzeptiert, 4 GB formatiert ist oder zu verkleinern.

## <a name="span-idbootreferencepcspanspan-idbootreferencepcspanspan-idbootreferencepcspanstep-9-install-windows-on-the-reference-device"></a><span id="bootReferencePC"></span><span id="bootreferencepc"></span><span id="BOOTREFERENCEPC"></span>Schritt 9: Installieren von Windows auf dem Gerät Verweis


1.  Legen Sie das **Windows PE** USB-Laufwerk in Ihrem Gerät Verweis.
2.  Starten Sie das Gerät Verweis auf das Startmenü des Geräts Auswahl. Sie dazu, Einschalten des Geräts schnell Drücken einer bestimmten Taste oder die Schaltfläche (beispielsweise die **Esc** -Taste oder die Schaltfläche **Lautstärke nach unten** ), und wählen die USB-Taste.
3.  Legen Sie das **FFU** USB-Laufwerk, in dem Gerät Verweis. Bestimmen Sie, welche Laufwerkbuchstaben dieses Laufwerk zugewiesen ist, die folgenden Schritte durch:

    1.  Geben Sie über die Befehlszeile Windows PE: **Diskpart** und drücken Sie die EINGABETASTE.
    2.  Geben Sie an der Diskpart-Eingabeaufforderung**List Volume** , und drücken Sie die EINGABETASTE.

    Hier werden alle Volumes im System vorhanden. Bestimmen der Treiber Buchstabe, das dem FFU USB-Schlüssel, beispielsweise G. entspricht

4.  Geben Sie in der Windows PE-Befehlszeile Folgendes ein:

    ``` syntax
    Dism.exe /apply-image /imagefile=G:\MyFFUImage.ffu /applydrive=\\.\physicaldrive0 /skipplatformcheck /logpath:G:\dism.applyffu.log
    ```

    Wobei G:\\MyFFUImage.ffu ist der Speicherort der Datei FFU.

**Wiederholen Sie Schritt 9: mithilfe des neuen Schlüssels des Windows-Installation können Sie weitere Geräte einrichten**. Deaktivieren Sie auf dem Bildschirm **fast Wechsel zu erhalten möchten** halten die Schaltfläche Power das Gerät. Führen Sie die OOBE nicht für den Kunden.

Es ist ein bekannter Fehler, auf dem PC, einen USB-Schlüssel automatisch starten festgelegt ist, es get in einer Schleife während des Installationsvorgangs abgefangen wird: nach der Installation von Windows neu installiert wieder. Um diese Schleife zu vermeiden:

**Lösung: Vorbereiten des Geräts Verweis**

1.  Öffnen Sie auf dem Gerät Referenz des Geräts Boot-Menüs. Sie dazu in der Regel das Gerät eingeschaltet, und drücken schnell eine bestimmte Taste oder die Schaltfläche (beispielsweise die **Esc** -Taste oder die Schaltfläche **Lautstärke nach oben** ).
2.  Hier finden Sie das Reihenfolge Startmenü (dieses Menü enthält verschiedene Namen und Speicherorte), und stellen Sie sicher, dass die **Festplatte** für die erste in der Startsequenz nicht das USB-Laufwerk werden eingerichtet ist.
3.  Wenn Ihr Gerät eine Möglichkeit zum Ändern der Startreihenfolge auf während der Startsequenz werden nicht angezeigt wird, kann die Option deaktiviert werden. Für eine Option wie "Enable Boot Optionen auf Startup" oder "Startmenü F12" Suchen Sie, und aktivieren Sie im Menü.

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


Wenn Windows auf dem Gerät Verweis nicht installiert werden, versuchen Sie jeden dieser Schritte aus:

-   **USB-Schlüssel wird in den Menüs beim Starten nicht angezeigt**: versuchen, mit anderen USB-ports auf dem Computer. Vermeiden der Verwendung von USB-Hubs oder Kabel.

    Starten Sie den Computer neu, und öffnen Sie das Gerät Boot-Menüs. Suchen Sie nach eine Option, um ein Menü Boot Device Auswahl beim Starten aktivieren (Beispiel: "F12 Startmenü"). Wenn Sie einen finden, aktivieren Sie es!

-   **UEFI oder BIOS**: Wenn Ihre Menüs Boot Wahl zwischen Starten im UEFI oder BIOS-Modus übergeben möchten, wählen Sie UEFI-Modus.
-   Wenn das Gerät bis zu das **Laufwerk** Auswahlmenü startet, wählen Sie die primäre Festplatte, dies ist in der Regel das Laufwerk **C** . Wenn Sie nicht sicher sind, welches Laufwerk ist, drücken Sie **UMSCHALT-F10** auf das Eingabeaufforderungsfenster zu öffnen. Geben Sie **Diskpart** ein, und drücken Sie die EINGABETASTE. Geben Sie an der Diskpart-Eingabeaufforderung **List Volume ein** , um die Partitionen anzeigen. Geben Sie **exit**ein. Drücken Sie **Alt + Tab** erneut versuchen.
-   Wenn das Gerät bis 6 % der Installation Ruft, und klicken Sie dann fehlschlägt, müssen Sie möglicherweise das Laufwerk vorbereiten:

    1.  Schließen Sie den USB-Schlüssel an.
    2.  Wählen Sie **Problembehandlung bei &gt; erweiterte Optionen &gt; Eingabeaufforderung**.
    3.  Geben Sie **Diskpart** ein, und drücken Sie die EINGABETASTE. Geben Sie an der Diskpart-Eingabeaufforderung **Liste Volume** zum Auflisten der Laufwerke. Geben Sie an den Diskpart auffordern lassen Sie **zu beenden** .
    4.  Typ **Diskpart/s D:\\Beispiele\\CreatePartitions UEFI.txt**

        Dabei ist D der Laufwerkbuchstabe des USB-Schlüssels.

        Verwenden Sie für BIOS-basierte PCs stattdessen CreatePartitions BIOS.txt.

    5.  Geben Sie an der Befehlszeile lassen **zu beenden** .
    6.  Wählen Sie **Ihren PC deaktivieren**.
    7.  Aktivieren Sie das Gerät, und öffnen Sie die Auswahl der Boot-Gerät. Wenn Sie eine Wahl zwischen Starten im Modus für das BIOS oder UEFI verfügen, wählen Sie UEFI-Modus. Windows-ICD sollte ordnungsgemäß installiert.

-   Wenn das Gerät startet bis zu der **Wählen Sie eine Option: Problembehandlung bei / Ausschalten von Ihrem PC** Menü Sie ein bekanntes Problem mit USB 3.0 und Windows-ICD Bilder sehen. Versuchen Sie erneut mit einem **USB 2.0** -Taste oder Port.
-   Stellen Sie sicher, das Gerät und das Windows-Abbild übereinstimmen. Wenn sie nicht übereinstimmen, versuchen Sie, erstellen das Bild mithilfe der richtigen Architektur erneut.

## <a name="span-idverifyspanspan-idverifyspantest-the-customizations"></a><span id="verify"></span><span id="VERIFY"></span>Testen der Anpassungen


Führen Sie diese Schritte, um ein Bild zu testen. Beachten Sie dass, erfordert dies Abschließen der ersten Eindruck des Benutzers und beim Erstellen eines Benutzerkontos. Nach Ausführung dieser Schritte müssen Sie in der Regel Windows auf das Gerät neu installieren, bevor sie an einen Kunden gesendet.

1.  Stellen Sie sicher, dass das Gerät nicht mit dem Netzwerk verbunden ist, und schalten Sie es.
2.  Nachdem das Gerät startet, wenn der **Sprachen** Bildschirm angezeigt und die französische Sprache zeigt wurde das Sprachpaket ordnungsgemäß hinzugefügt. Wählen Sie die Sprache, die, der Sie am häufigsten mit vertraut sind, wählen Sie die Tastatur und klicken Sie dann auf **Weiter**.
3.  Führen Sie die Out of Box-Experience (OOBE): Diese Schritte können basierend auf Sprache variieren.
4.  Klicken Sie auf **annehmen**, auf dem Bildschirm **Hi vorhanden** .
5.  Wenn sie Sie für einen Product Key aufgefordert werden, klicken Sie auf **dies später**. Wenn Sie eine Netzwerkverbindung angeschlossen sind, können Sie aufgefordert, einen Product Key bereitstellen. Vermeiden der Verwendung von eines Product Keys, trennen Sie das Gerät und versuchen Sie es erneut.
6.  Klicken Sie auf **annehmen** , klicken Sie auf **diesen Schritt überspringen**, und klicken Sie dann auf **express Einstellungen verwenden**.
7.  Klicken Sie auf die **, die Eigentümer von diesem PC?** Seite, klicken Sie auf **ich tun**, und klicken Sie dann auf **Weiter**.
8.  Klicken Sie auf der Seite **selbst erwerben** auf **diesen Schritt überspringen**.
9.  Fügen Sie einen Benutzernamen ein (Beispiel: "Terry"), und klicken Sie dann auf **Weiter**.
10. Das Gerät schließt Setup und Neustarts, auf dem Desktop.
11. Wenn der Desktop angezeigt wird, in den **Einstellungen** unter **System &gt; zu**; sollte angezeigt werden die technischen Support-Informationen, die Sie zuvor eingegeben werden angezeigt (Firmenname, Support-Telefonnummer und Support-Website).

 

 





