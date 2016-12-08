---
title: "System-Generator Bereitstellung von Windows-10 für desktop-Editionen"
author: Justinha
description: "Rufen Sie Schritt-Anleitung für System-Builder zum Bereitstellen von Windows 10 auf Desktopcomputern, Laptops und 2-in-1."
ms.openlocfilehash: e94a13a258d49ec66ccfb2fa1ce068ec6f8d0dec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="system-builder-deployment-of-windows-10-for-desktop-editions"></a>System-Generator Bereitstellung von Windows-10 für desktop-Editionen 

Sie können dieses Handbuch zum Bereitstellen von Windows-10 für eine Reihe von Computern verwenden. Es enthält einen verbindlichen Leitfaden für die Bereitstellung von Windows 10, einschließlich online und offline Anpassungen und optionale Schritte für bestimmte Szenarien. Es soll vermitteln, System-Builder (Level 200) (Techniker) mit 64-Bit- und 32-Bit-Konfigurationen und gilt für Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen). 

## <a name="prepare-your-lab-environment"></a>Vorbereiten der laborumgebung

Der erste Schritt besteht umfasst die Installation der neuesten Windows Assessment and Deployment Kit (Windows ADK) Tools auf dem Referenzcomputer festgelegten Testlabor, einrichten. Der Computer muss Windows 10 X64 ausgeführt, wenn Sie beabsichtigen, X64 bereitstellen Bilder oder ausführen Windows 10 X86 für X86 image-Bereitstellung. Unterstützte Architektur Konflikt möglicherweise falsche Konfigurationen beim Verwenden von Bereitstellungstools in der Windows-ADK. Soweit nicht anders angegeben, befolgen Sie die entsprechenden Richtlinien für entweder eine 64-Bit im Vergleich zu 32-Bit-Bereitstellung.

Vor das Bereitstellungsverfahren beginnen, müssen Sie die Kits herunterladen, die in diesem Handbuch verwendet werden. Wechseln Sie zu der [OEM Partner Center](http://www.microsoft.com/oem/en/pages/index.aspx#fbid=7JcJYKYGEfo) > **Downloads und Installation** > **Grundlegendes zu ADKs und OPKs**. Eine Liste mit Ressourcen und Kits, die verwendet werden und sie erhalten, finden Sie unter [Was Sie benötigen und wo darauf zuzugreifen](#what-you-will-need-and-where-to-get-it).

Sie benötigen zwei USB-Laufwerke. USB-A zum Starten des Systems in Windows-Vorinstallation-Umgebung (Windows PE) verwendet werden. USB-B wird zum Verschieben von Dateien zwischen Computern, Speicher Bereitstellung und Recovery-Skripts, und speichern und Anwenden von erstellte Bilder verwendet werden.

<table>
<th>USB-Festplatte Name</th>
<th>Format</th>
<th>Mindestgröße</th>
<tr>
<td>USB-A</td>
<td>FAT32</td>
<td>~ 4GB</td>
</tr>
<tr>
<td>USB-B</td>
<td>ALS NTFS</td>
<td><p>~ 16GB x86</p><p>~ Amd64 32GB</p></td>
</tr>
</table>

### <a name="creating-my-usb-b"></a>Erstellen von meiner USB-B

-   Formatieren des USB-Laufwerk ein, und nennen Sie sie wie folgt:

    ![Extrahieren von USB](images/extract-usb.png) 

-   Laden Sie dann [USB-B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip) aus dem Microsoft Download Center herunter. Speichern Sie die ZIP-Datei USB-b, und extrahieren Sie den Inhalt vorhanden. 

-   Die Inhalte der Konfigurationsdateien in USB-B enthalten sind Beispiele, in denen Sie gemäß Ihrer Auswahl branding und Produktion ändern können. Allerdings muss Dateinamen und die Hierarchie der Ordner und Dateien die gleichen wie unten dargestellt, um Ihre Bereitstellungsverfahren in diesem Handbuch ausrichten.

## <a name="customizations-throughout-the-document"></a>Anpassungen im gesamten Dokument

| **Übergeben Sie**        | **Einstellung**                              | **Aktion**                                                            |
|-----------------|------------------------------------------|-----------------------------------------------------------------------|
| **Windows PE**       | Benutzeroberflächensprache Setup                        | EN-US                                                                 |
|                 | Benutzerdaten                                | Vorinstallation Product Key für für ODR - definiert                         |
| **Specialize**  | Internet Explorer-Startseite              | in die Antwortdatei                                                    |
|                 | OEM-Name                                 | Definiert, in die Antwortdatei                                            |
|                 | OEM-Logo                                 | Definiert, in die Antwortdatei                                            |
|                 | Modell                                    | Definiert, in die Antwortdatei                                            |
|                 | Supportinformationen                             | Definiert, in die Antwortdatei                                            |
| **OOBE-System** | Reseal                                   | Audit/OOBE                                                            |
|                 | StartTiles                               | Quadratische Kacheln / SquareOrDesktopTiles festgelegt, so heften Sie desktop-apps an.      |
|                 | TaskbarLinks (bis zu 6 angeheftete lnk-Dateien) | Tastenkombinationen Paint und Systemsteuerung wurden festgelegt.                       |
|                 | Designs                                   | Benutzerdefiniertes Design mit OEM-Logo als das Hintergrundbild wurde festgelegt. |
|                 | Visuelle Effekte                           | SystemDefaultBackground set                                           |

## <a name="additional-customizations"></a>Zusätzliche erforderliche Anpassungen vor

### <a name="product-deployment"></a>Einsatz des Produkts

-   Office-nur einem Bild v15.4 vorab OPK geladen.

### <a name="image-customization"></a>Bildanpassung

- Hinzufügen von Benutzeroberflächen-Sprachpakete zu Windows

- Hinzufügen von Treibern und System-Updatepakete

- Hinzufügen von OEM-spezifische Dateien für Logo und Hintergrund zu Windows

- Optimierung der Bild-Größe

- Verankern desktopanwendungen Sceen starten

## <a name="create-a-usb-drive-that-can-boot-to-winpe"></a>Erstellen Sie ein USB-Laufwerk, die gestartet werden kann zu einer Windows PE

Sie müssen die entsprechende Version des Windows ADK verwenden, für die Bilder angepasst wird. Wenn ein Bild mit der RTM-Abbild erstellen möchten, verwenden Sie Windows ADK für Windows 10. Bei Verwendung einer Windows-10, Version 1511 Bild, verwenden Sie die Windows ADK für Windows 10, Version 1511.
Weitere Informationen zu den Windows-ADK finden Sie unter [Windows 10 ADK Dokumentation zur Homepage](https://technet.microsoft.com/library/mt297512.aspx).

|  Windows-version  | Link zu ADKSetup.exe ausführen      |
|-------------------|-------------------------------|
| Windows-10, RTM-Version    | [**Windows ADK**](http://download.microsoft.com/download/8/1/9/8197FEB9-FABE-48FD-A537-7D8709586715/adk/adksetup.exe)  |
| Windows-10, Version 1511 | [**Windows ADK**](http://download.microsoft.com/download/3/8/B/38BBCA6A-ADC9-4245-BCD8-DAA136F63C8B/adk/adksetup.exe) |


1.  Führen Sie die auf dem Bildschirm Anweisungen, um die Windows-ADK, einschließlich der **Bereitstellungstools**, **Windows-Vorinstallation-Umgebung**und **Windows Assessment Toolkit** installieren.

    ![Auswählen von ADK-Funktionen](Images/adk-select-features.png)

1.  Drücken Sie die Windows-Taste, um im Menü **Start** angezeigt. Typ:
    
        Deployment and Imaging Tools Environment

    Maustaste auf den Namen des Tools, und klicken Sie dann auf **als Administrator ausführen**.

2.  Windows ADK können Sie **Windows-Vorinstallation-Umgebung**zu erstellen. Kopieren Sie Basis Windows PE zum neuen Ordner.

    Wenn Sie ein Bild **X64** Windows 10, Kopie der X64 Windows PE Ordnerstruktur verwenden:

        Copype amd64 C:\winpe_amd64

    Wenn Sie ein Bild **X86** Windows 10, Kopie der X86 Windows PE Ordnerstruktur verwenden:

        Copype x86 C:\winpe_x86

1.  Sie können Pakete und/oder Treiber Windows PE hier hinzufügen.

2.  Schließen Sie ein USB-Laufwerk, das mindestens 4 GB ist. Formatieren Sie ihn, wie in diesem Diagramm dargestellt:

    ![Verbinden von USB](Images/connect-usb.png)

3.  Stellen Sie eine neue startbare Windows PE-USB eingefügte USB.

    Wenn Sie ein Bild **X64** Windows 10 verwenden, stellen Sie eine X64 WinPE USB:

        MakeWinPEMedia /UFD C:\winpe_amd64 F:

    Wenn Sie ein Bild **X86** Windows 10 verwenden, stellen Sie eine X86 WinPE USB:

        MakeWinPEMedia /UFD C:\winpe_x86 F:

    (Wobei F: der Laufwerkbuchstabe des USB)

## <a name="install-windows-with-basic-customizations"></a>Installieren von Windows mit grundlegenden Anpassungen

Erwerben Sie Windows 10 X86/X64 DVD-Medien von einem autorisierten Microsoft-Händler.

Finden Sie für ein Dokument können Sie die Anpassungen in der Datei unattend.xml definierten anpassen können die [Windows-Richtlinien für System-Builder](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_129) und [Windows-Richtlinie für System-Builder](https://oem.microsoft.com/downloads/worldwide/windows_10/Windows_10_Policy_SB.pdf).

1.  Kopieren Sie die Quellen\\Install.wim Datei aus dem Verzeichnis, in den Windows-10-Medien, die Sie auf dem lokalen Desktop (~ 3 gb) bereitstellen möchten.

    ![WIM kopieren](Images/copy-wim.png)

1.  Führen Sie **Windows System Image Manager** zum Erstellen einer Antwortdatei von Grund auf neu starten. Dieses Tool ermöglicht Ihnen das Erstellen oder Verwalten von Antwortdateien auf einfache und organisierte Weise.

    ![Führen Sie SIM](Images/run-sim.png)

1.  Navigieren Sie **zur Datei** &gt; **Windows-Abbild auswählen**. Navigieren Sie auf dem lokalen Desktop, und wählen Sie **Install.wim**. Katalogdatei wird für diese angegebenen Wim (CLG-Datei) erstellt werden.

    Problembehandlung bei: Erstellen des Katalogs kann aus verschiedenen Gründen fehlschlagen. Stellen Sie sicher, dass install.wim Lese-/Schreibberechtigungen verfügt. Wenn weiterhin Fehler angezeigt, stellen Sie sicher, dass die richtige Architektur (X86 oder X64) Windows 10 auf Referenzcomputer installiert ist. Wenn Sie Katalog für X64 erstellen Windows 10 Bild, Sie sind erforderlich X64 verwendet Windows 10 auf X64 Windows 10 Computer installiert. Install.wim Bild und Windows 10 ADK Versionen müssen identisch sein.

1.  Öffnen Sie eine Antwort-Beispieldatei oder erstellen Sie einen neuen Anwendungspool.

    -   Dies ist der Antwort-Beispieldatei enthalten in den USB-B:

        USB-B\ConfigSet\AutoUnattend.Xml

1.  Klicken Sie auf **OK** , um die Antwortdatei das Windows-Abbild zuzuordnen. 

3.  Um einen Treiber Windows PE hinzuzufügen, klicken Sie auf select **Einfügen** **Treiberpfad** wählen Sie Pass **1 WindowsPE** , und navigieren Sie dann zu der Treiber. Hinweis: Dieser Schritt ist optional und nur erforderlich, wenn ein Drittanbieter-Treiber für derzeit in der Windows-Vorinstallation Umgebung benötigt wird. 

2.  Um ein Paket hinzuzufügen, klicken Sie auf **Einfügen**, wählen Sie **Paket**und navigieren Sie dann auf das Paket, den, das Sie hinzufügen möchten. Dieser Schritt ist optional.

### <a name="customize-the-answer-file"></a>Die Antwortdatei anpassen

Problembehandlung bei: Ein leerer Zeichen in **specialize | Microsoft-Windows-Shell-Setup | Computername** , Windows Installationsfehler bewirken.

1.  Finden Sie ein Beispiel einer Antwortdatei für grundlegende Anpassungen:

    -   USB-B\ConfigSet\AutoUnattend.Xml

    Verwenden Sie die Beispielantwortdatei und ändern die entsprechenden Teile oder von vorne beginnen, indem Sie einige grundlegenden Anpassungen angeben.

    Finden Sie unter, und verwenden Sie der Windows-10 Standard Product Key vom [OEM Partner Center](https://www.microsoft.com/OEM/en/products/windows/Pages/windows-10-build.aspx#fbid=nV7H02bHHiv) unter **Product Keys für Standard** Registerkarte aufgelistet.

1.  Fügen Sie einen Product Key ein, der die Windows-Edition entspricht. Dieser Schlüssel wird nicht verwendet, um Windows aktivieren, damit Sie denselben Schlüssel für mehrere Installationen wiederverwenden können:

    -   Wählen Sie im Bereich **Antwortdatei** **Components\1 windowsPE\amd64_Microsoft-Windows-Setup_neutral\UserData\ProductKey**aus. Geben Sie im Eigenschaftenbereich **ProductKey** , klicken Sie unter **Einstellungen für**den Wert neben Schlüssel.

    Wichtig: Dieser Product Keys *kann nicht* verwendet werden für die Aktivierung. Sie müssen während des Installationsvorgangs für die Aktivierung einen Software-Product Key eingeben. Dieser Schlüssel werden entfernt Sysprep beim verallgemeinern ausgeführt werden. Der Endbenutzer werden benötigt, um den eindeutigen Product Key aus dem Zertifikat der Echtheit (Echtheitszertifikat) Geben Sie beim ersten Starten von Windows 10.

1.  Fügen Sie die Supportinformationen hinzu:

    Wählen Sie im Bereich **Antwortdatei** **Components\4 specialize\amd64_Microsoft-Windows-Shell-Setup_neutral\OEMInformation**aus.

    Aktualisieren Sie die folgenden Werte im Bereich **OEMInformation Eigenschaften** im Abschnitt **Einstellungen** : Firmenname (Hersteller), Stunden (SupportHours), Telefonnummer (SupportPhone), und die Website (SupportURL).

1.  Vorbereiten des Computers im Überwachungsmodus nach Abschluss die Windows-Installation zu starten:

    Klicken Sie im **Windows-Abbild** **Komponenten**erweitern, mit der rechten Maustaste **amd64_Microsoft-Windows-Deployment**und wählen Sie dann die **Einstellung zu Pass 7 OobeSystem hinzufügen**aus.

    Wählen Sie im Bereich **Antwortdatei** **Components\7 oobeSystem\amd64_Microsoft-Windows-Deployment _neutral\Reseal**.

    Fügen Sie im Bereich **Reseal Eigenschaften** im Abschnitt **Einstellungen für** den folgenden Wert: Mode = Audit.

1.  Legen Sie auf der Homepage des Internet Explorer:

    Klicken Sie im **Windows-Bild** mit der rechten Maustaste **Amd64_Microsoft Windows Internet Explorer Internet Explorer**, und wählen Sie dann auf **Hinzufügen-Einstellung, um Pass 4 specialize**.

    Wählen Sie im Bereich **Antwortdatei** **Components\4 specialize\amd64_Microsoft-Windows-Microsoft-Windows-IE-InternetExplorer_neutral**.

    Klicken Sie im Eigenschaftenbereich **IE-Internet Explorer** , im Abschnitt **Einstellungen** wählen Sie Home_page, und fügen Sie die URL Ihrer Website.

1.  OEMs können **Datenträgerkonfiguration** angeben, die zum Datenträgerpartitionen erstellen/ändern, und legen Sie die Image-Installationspartition verwendet wird. Dieser Schritt ist optional und wird in der Antwort-Beispieldatei USB-B\ConfigSet\AutoUnattend.xml Konfiguration enthalten.

    Speichern Sie die Antwortdatei auf USB-B\ConfigSet\AutoUnattend.xml, und schließen Sie Windows SIM.

### <a name="install-windows"></a>Installieren von Windows

1.  Führen Sie [Meine USB-B erstellen](#creating-my-usb-b) im Abschnitt bevor überspringen diesen Schritt, um sicherzustellen, dass die Windows-Installationsdateien kopiert wurden in das Verzeichnis **MyWindows** USB-B.

2.  Starten des Referenzcomputers und Einfügen USB-A.

3.  Nach dem Windows PE gestartet wurde, fügen Sie USB-B.

    Beheben: WENN starten mit USB ein Fehler auftritt, stellen Sie sicher, dass USB-Start anstelle von HDD Boot eine Priorität zugewiesen haben. Hierzu geben Sie BIOS-Menü, und passen Sie Startreihenfolge wie die Auswahl der ersten Option als USB-Start.

1.  Typ *Diskpart* und Treffer eingeben, um Diskpart zu starten. Geben Sie die *Liste Volume* zum Identifizieren der Volumebezeichnung eines USB-B (zum Beispiel: E:\). Geben Sie schließlich *Beenden* , um Diskpart zu beenden.

    ![Diskpart](Images/diskpart.png)

1.  Verwenden Sie den folgenden Befehl, um die Installation zu starten. Dieser Befehl löst *setup.exe* mit einer Antwortdatei zum Installieren von Windows 10 mit zusätzliche erforderliche Anpassungen vor.

        Xcopy /herky e:\configset\$oem$ e:\MyWindows\Sources\$OEM$

        E:\myWindows\setup.exe /unattend:E:\ConfigSet\AutoUnattend.xml

1.  Nachdem die Installationsdateien kopiert wurden, trennen USB-A.

2.  Trennen Sie die USB-B rechts nach einem des Computers Neustart.

### <a name="verify-customizations-in-audit-mode"></a>Vergewissern Sie sich im Überwachungsmodus Anpassungen

Wichtig: Herstellen einer Verbindung mit dem Computer mit Internet wird nicht empfohlen, während der Phasen manufacturing Es wird nicht empfohlen, zum Abrufen der Updates aus Windows Update im Überwachungsmodus aktiviert. Dadurch wird einen Fehler beim verallgemeinern + Syspreping den Computer wahrscheinlich im Überwachungsmodus generiert.

1.  Nach dem Setup wurde nach Abschluss des Vorgangs Computer anmeldet Windows im Überwachungsmodus automatisch als Administrator.

2.  Klicken Sie auf die *Kachel Desktop* , um den Desktop anzeigen, und Sie sollte das Sysprep-Fenster angezeigt.

3.  Vergewissern Sie sich Ihre Änderungen, die Sie in die Antwortdatei (Siehe Herstellername, Rufnummer Support und anderen Anpassungen) angegeben haben.

    ![Sysprep](Images/sysprep.png)

1.  Das Bild muss allgemeiner engl. werden, bevor Sie als Bild Fertigung verwendet werden; Wählen Sie das Kontrollkästchen **verallgemeinern** .

2.  Wählen Sie im Feld Systembereinigungsaktion **Systembereinigungsaktion Out-of-Box-Experience**.

3.  Wählen Sie im Optionenfeld beim Herunterfahren **Herunterfahren**aus.

## <a name="capture-an-image"></a>Erfassen eines Abbilds

1.  Starten des Referenzcomputers und verbinden USB-A.

2.  Nachdem Windows PE gestartet wurde, eine Verbindung herstellen Sie USB-B.

    Problembehandlung: Falls mit USB starten ein Fehler auftritt, stellen Sie sicher, dass USB-Boot anstelle von HDD Boot eine Priorität zugewiesen haben. Dazu öffnen Sie das BIOS-Menü, und passen Sie die Startreihenfolge, sodass die erste Option USB-Start ist. Das System im Laufe Starten von HDD geben Windows Sie specialize und OOBE übergeben. Um eine allgemeine und stabil Bild zu erfassen, müssen keines der Windows-übergibt die werden ausgeführt. Um das Bild erneut verallgemeinern, drücken Sie STRG + UMSCHALT + F3 OOBE und Boot im Überwachungsmodus überspringen. Sysprep-Modus das System mithilfe von OOBE neu starten, überwachen und Switches verallgemeinern. Nach dem Neustart des Systems sicherstellen von USB-A, Windows PE zu starten.

1.  Typ *Diskpart* und Treffer eingeben, um Diskpart zu starten. Dann Typ *Liste Volume* zum Identifizieren der Volumebezeichnung eines Windows-Installation Volume mit der Bezeichnung "Windows" (zum Beispiel: C:\). Geben Sie schließlich *Beenden* , um Diskpart zu beenden

2.  Erfassen Sie das Abbild der Partition Windows, die USB-B. Dieser Vorgang kann mehrere Minuten.

        MD E:\scratchdir

        Dism /Capture-Image /CaptureDir:C:\ /ImageFile:E:\Images\ThinImage.wim /Name:"myWinImage" /scratchdir:e:\scratchdir

    C:\ ist die Volumebezeichnung eines installierten Windows an. E:\ ist die Volumebezeichnung eines USB-B.

## <a name="update-images-for-each-model-offline-servicing"></a>Aktualisieren von Bildern für jedes Modell: offline – Wartung

1.  Nehmen Sie eine Sicherungskopie im gleichen Verzeichnis befindet, und benennen Sie das Bild, das als ModelSpecificImage.wim geändert wird, vor dem Bereitstellen und Bearbeiten des Bildes.

        Copy E:\Images\ThinImage.wim E:\Images\ModelSpecificImage.wim

### <a name="mount-images"></a>Binden Sie Bilder

1.  Mount-Windows-Abbild (ModelSpecificImage.wim) in diesem Prozess extrahiert den Inhalt der Bilddatei an einem Speicherort, in dem Sie anzeigen und ändern das bereitgestellte Abbild können.

        Md C:\mount\windows

        Dism /Mount-Wim /WimFile:E:\Images\ModelSpecificImage.wim /index:1 /MountDir:C:\mount\windows

    Dabei ist E:\ der Laufwerkbuchstabe des USB-B.

1.  Bereitstellen von Windows RE Bilddatei.

        Md c:\mount\winre

        Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\Recovery\winre.wim /index:1 /MountDir:C:\mount\winre

    Problembehandlung bei: Wenn bereitstellen Operation ein Fehler auftritt, stellen Sie sicher, dass Sie die Windows-10-Version von DISM, die mit der Windows-ADK installiert ist und nicht mit einer älteren Version aus dem Referenzcomputer verwenden. Bereitstellen Sie nicht Bilder zu geschützten Ordnern an, wie Ihre User\Documents Ordner. Wenn DISM Prozesse unterbrochen werden, können Sie vorübergehend vom Netzwerk trennen und Virenschutz deaktivieren.

    ![Binden Sie](Images/mount.png)

    ![Windows-Ordner](Images/windows-folder.png)

### <a name="modify-images"></a>Ändern von Bildern

#### <a name="add-drivers"></a>Hinzufügen von Treibern

Wenn Sie ein X64 verwenden Windows 10 Bild, fügen Sie X64 Treiber; Wenn Sie ein X86 verwenden Windows 10 Bild, fügen Sie X86 Treiber.

1.  Hinzufügen von Treiberpaketen nacheinander aus. (INF-Dateien) SampleDriver\driver.inf ist ein **Beispiel** -Treiber-Paket, das speziell für das Computermodell ist. Geben Sie Ihre eigene Treiberpfad. Wenn Sie mehrere Treiberpakete haben, fahren Sie mit dem nächsten Schritt fort.

        Dism /Add-Driver /Image:C:\mount\windows /Driver:"C:\SampleDriver\driver.inf"

        Dism /Add-Driver /Image:C:\mount\winre /Driver:"C:\SampleDriver\driver.inf"

1.  Mehrere Treiber können in einer Befehlszeile hinzugefügt werden, wenn Sie einen Ordner anstelle einer INF-Datei angeben. Um alle Treiber in einen Ordner und alle Unterordner installieren, verwenden Sie die **Option/recurse** .

        Dism /Image:C:\mount\windows /Add-Driver /Driver:c:\drivers /Recurse

1.  Überprüfen Sie den Inhalt von der %WINDIR%\Inf\ (C:\mount\windows\Windows\Inf\) Verzeichnis in bereitgestellten Windows-Abbild, um sicherzustellen, dass die INF-Dateien installiert wurden. Treiber hinzugefügt werden, auf dem Windows-Abbild heißen Oem\*. inf-Datei. Dadurch wird sichergestellt, eindeutigen Benennen von für neue Treiber auf dem Computer hinzugefügt werden. Beispielsweise sind die Dateien Treiber1.inf und Treiber2.inf umbenannte Oem0.inf und Oem1.inf.

2.  Stellen Sie sicher, dass der Treiber für beide Bilder installiert wurde.

        Dism /Image:C:\mount\windows /Get-Drivers

        Dism /Image:C:\mount\winre /Get-Drivers

Wichtig: Wenn der Treiber das Installer-Paket enthält und verfügt nicht über eine INF-Datei, Sie können den Treiber im Überwachungsmodus durch Doppelklicken auf das entsprechende Installer-Paket zu installieren. Einige Treiber möglicherweise mit Sysprep-Tool nicht kompatibel; Sie werden entfernt, nachdem Sysprep verallgemeinern, auch wenn sie offline eingefügt wurde.

In diesem Fall müssen Sie einen zusätzlichen Parameter USB-B\AnswerFiles\UnattendSysprep.xml hinzufügen, um die Treiber im Bild beibehalten, wenn das Bild allgemeiner engl. sein wird.

&lt;PersistAllDeviceInstalls&gt;true&lt;/PersistAllDeviceInstalls&gt;

Diese Eigenschaft muss USB-B\AnswerFiles\UnattendSysprep.xml der verallgemeinern Phase hinzugefügt werden, um die Treiber im Bild beibehalten werden. Weitere Informationen zu den Details dieser Eigenschaft sowie zum Hinzufügen zu einer Antwortdatei finden Sie unter [PersistAllDeviceInstalls](http://technet.microsoft.com/library/ff716298.aspx).

#### <a name="add-language-interface-packs"></a>Hinzufügen von Benutzeroberflächen-Sprachpaketen

Abrufen von Windows-10-Benutzeroberflächen-Sprachpaketen [OEM Partner](https://www.microsoft.com/OEM/en/installation/downloads/Pages/Windows-10-v1511-Language-Interface-Packs.aspx#fbid=nV7H02bHHiv) Center auf der Registerkarte **Benutzeroberflächen-Sprachpaketen** .

Weitere Informationen zu den Benutzeroberflächen-Sprachpaketen finden Sie unter [Hinzufügen von Benutzeroberflächen-Sprachpaketen für Windows 10](add-language-interface-packs-to-windows.md).

**Wichtig: Versionen der LIP müssen andere Windows-Komponente-Versionen für das Bild und ADK übereinstimmen.**

Wenn Sie ein X64 verwenden Windows 10 Bild, Install X64 Benutzeroberflächen-Sprachpaketen; Wenn Sie ein X86 verwenden Windows 10 Bild, Install X86 Benutzeroberflächen-Sprachpaketen.

1.  Kopieren des LIP-Ordners in den Ordner USB-B\LanguagePack\x64 oder USB-B\LanguagePack\x86:

    ![Kopieren der LIP](Images/copy-lip.png)

1.  Anwenden des LIPS auf bereitgestellte Abbild.

    *Amd64-Architektur*

        Dism /image:C:\mount\windows /add-package /packagepath:e:\LanguagePacks\amd64\ga-ie\lp.cab

    *X86 Architektur*

        Dism /image:C:\mount\windows /add-package /packagepath:e:\LanguagePacks\x86\ga-ie\lp.cab

**Wichtig: Installieren Sie ein Language Pack nicht nach einer Aktualisierung. Wenn ein Update (Hotfix, allgemein verfügbare Version [GDR] oder [SP] pack Service), die Language-abhängigen Ressourcen enthält installiert ist, bevor ein Language Pack installiert ist, wird die Liste der sprachspezifischen Änderungen, die in dem Update enthalten sind werden nicht übernommen das Update neu installiert werden müssen. Installieren von Language Packs immer vor der Installation von Updates.**

#### <a name="add-update-packages"></a>Hinzufügen von Updatepakete

Wenn Sie ein X64 verwenden Windows 10 image, Hinzufügen von X64-Updatepakete; Wenn Sie ein X86 verwenden Windows 10 image, Hinzufügen von X86-Updatepakete.

Zum Abrufen von Updatepakete Herunterladen von [Microsoft Update-Katalog](http://catalog.update.microsoft.com/v7/site/Home.aspx).

1.  Starten Sie Internet Explorer, und navigieren Sie zu [Microsoft Update-Katalog](http://catalog.update.microsoft.com/v7/site/Home.aspx) -Webseite. Weitere Informationen zu den Paketen Sie aus Microsoft Update-Katalog verwenden sollten finden Sie unter [Was Sie benötigen und wo darauf zuzugreifen](#what-you-will-need-and-where-to-get-it) .

2.  Geben Sie jedes einzelne Aktualisierungspaket einzeln in das Suchfeld ein, und klicken Sie auf **Suchen**.

    ![Update-Katalog](Images/update-catalog.png)

1.  Nachdem die Suche abgeschlossen ist, klicken Sie neben die Version und die Architektur des Pakets, die Sie herunterladen möchten auf **Hinzufügen** .

    ![Update-Katalog hinzufügen](Images/add-update-catalog.png)

1.  Nachdem Sie alle folgenden Updates hinzugefügt haben, klicken Sie auf **Auswahlkorb anzeigen** und **herunterladen**.

    ![Laden Sie die Update-Katalog](Images/download-update-catalog.png)
    
    ![Download abgeschlossen](Images/download-update-catalog-complete.png)

    **Beheben:** WENN Sie als "die Website ein Problem aufgetreten" nach dem Klicken auf "Herunterladen" ein Fehler auftritt, sollten Sie vorübergehend deaktivieren von Popupblocker in Internet Explorer oder Deaktivieren des geschützten Modus in Internet Explorer

    ![Geschützten Modus aktivieren](Images/enable-protected-mode.png)

1.  Alle aufgeführten wichtige Updates für den Download, fügen Sie nach **Updatepaketen** (KB Pakete) auf das Bild einzeln mithilfe des folgenden Befehls:

    *Amd64-Architektur*

        Dism /Add-Package /Image:C:\mount\windows /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x64.msu"

    *X86 Architektur*

        Dism /Add-Package /Image:C:\mount\windows /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x86.msu"

1.  Hinzufügen von Updates zu winre.wim (wobei sie gelten; nicht alle Updates für winre.wim)

    *Amd64-Architektur*

        Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x64.msu"

    *X86 Architektur*

        Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x86.msu"

#### <a name="add-oem-specific-visual-customizations"></a>Hinzufügen von OEM bestimmte visuelle Anpassungen

1.  OEM-Ordner C:\mount\windows\Windows\system32\ im Verzeichnis zu erstellen.

2.  Kopieren Sie das OEM-Logo auf C:\mount\windows\Windows\system32\OEM\**FabrikamLogo.bmp* *OEM-Informationen* Verzeichnis, in zugeordnet werden, für die unbeaufsichtigte Installation Datei in *| Logo** Eigenschaft.

    Finden Sie in der folgenden Abbildung in eine Antwortdatei OEM-Logo hinzu.

    -   %windir%\system32\OEM\FabrikamLogo.bmp

    **VERWEIS:** OEM-Logo-Datei muss im BMP-Format und 120px x 120px Größe. Informationen finden Sie in Windows-Richtlinien für System-Builder OEM-Logo.

    ![Details der OEM-Logo](Images/oem-logo-details.png)

1.  Um eine bestimmte OEM desktop-Hintergrundbild angezeigt, die Bilddatei muss in %windir%\system32\OEM platziert werden\**Fabrikam.bmp** Verzeichnis. Überprüfen, ob der Pfad in die Antwortdatei OobeSystem entspricht derselben ist &gt; Microsoft-Windows-Shell-Setup &gt; Designs &gt; DesktopBackground-Eigenschaft. Finden Sie unter der unterhalb des Symbols in eine Antwortdatei desktop Hintergrund hinzu.

    ![Desktop-Hintergrund hinzufügen](Images/add-desktop-background.png)

#### <a name="modify-start-layout"></a>Ändern der Start-layout

Das Start Kachel Layout in Windows 10 bietet OEMs die Möglichkeit, auf das Standardlayout Start Einbeziehung Weblinks, sekundäre Kacheln, Windows-desktopanwendungen und universellen Windows-apps Kacheln angefügt werden soll. In diesem Layout können OEMs es auf mehrere Bereiche oder Märkte anwendbar tätigen, ohne einen Großteil der Arbeit zu duplizieren. Darüber hinaus können OEMs hinzufügen, bis zu drei Standard-apps in den Abschnitt häufig verwendeten apps im Bereich, der System-gesteuerte Listen o den Benutzer, einschließlich wichtiger oder auf die häufig zugegriffen System Standorten übermittelt und kürzlich installierten apps.

1.  Erstellen Sie Layoutmodification.xml.

    Hinweis: Es wird empfohlen, mit dem Beispiel auf **USB-B**\StartLayout\layoutModification.xml zu starten, wie sie in den Beispielen in diesem Handbuch (Beispiel nur) entspricht.

    Das Beispiel LayoutModification.xml zeigt zwei Gruppen namens "Fabrikam Group 1" und "Gruppe" Fabrikam "2", die Kacheln enthalten, die angewendet wird, wenn das Gerät Land/Region übereinstimmt, was in Region angegeben wird (Deutschland und USA sind in diesem Fall die Regionen). Jede Gruppe enthält drei Kacheln und die verschiedenen Elemente müssen Sie je nach die Kachel verwenden, die Sie an Start anheften möchten.

    Behalten Sie beim Erstellen der Datei LayoutModification.xml Folgendes beachten:

    - Wenn Sie eine Windows-desktop-Anwendung mit dem Tag **Start: DesktopApplicationTile** festhalten und die Anwendung Anwendung Benutzer Modell-ID nicht kennen, müssen Sie zum Erstellen einer LNK-Datei in ein legacy-Menü Startmenüverzeichnis vor dem ersten Start.

    - Wenn Sie das **Start: DesktopApplicationTile** Tag verwenden, um eine Vorversion URL Verknüpfung mit Start anheften, müssen Sie eine URL-Datei erstellen und fügen Sie diese Datei in ein legacy-Menü Startmenüverzeichnis vor dem ersten Start.

    Die folgenden Verzeichnisse können Sie für die oben genannten Szenarien um die URL oder lnk-Dateien zu platzieren:

    - %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    - %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

1.  Speichern Sie die Datei LayoutModification.xml.

2.  Das Windows-Abbild Ihrer LayoutModification.xml-Datei hinzugefügt. Sie müssen die Datei in die folgenden Position vor dem ersten Start zu platzieren. Wenn die Datei vorhanden ist, sollten Sie die LayoutModification.XML ersetzen, die bereits im Bild enthalten ist.

        Copy E:\StartLayout\layoutmodification.xml c:\mount\windows\users\default\AppData\Local\Microsoft\Windows\Shell\

    E: ist, auf dem der Laufwerkbuchstabe des USB-B.

1.  Wenn Sie Kacheln, die URL oder .lnk Dateien erfordern fixiert, fügen Sie die Dateien die folgenden legacy-Menü Start Verzeichnisse hinzu:

    1.  %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    2.  %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

            Copy e:\StartLayout\Bing.url "C:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs\"

            Copy e:\StartLayout\Paint.lnk "C:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Bing.url "C:\mount\windows\users\All Users\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Paint.lnk "C:\Mount\Windows\Users\All Users\Microsoft\Windows\Start Menu\Programs"

    Hinweis: Wenn Sie keine LayoutModification.xml-Datei erstellen und Sie auch weiterhin mithilfe die Einstellungen für die unbeaufsichtigte Installation zu starten, das Betriebssystem verwendet die Antwortdatei für die unbeaufsichtigte Installation und die ersten 12 SquareTiles oder DesktoporSquareTiles Einstellungen in der Datei für die unbeaufsichtigte Installation angegeben werden. Diese Kacheln automatisch in die neu erstellte Gruppen platziert dann am Ende des Start. Die ersten sechs Kacheln befinden sich in der ersten OEM-Gruppe, und der zweite Satz von sechs Kacheln befinden sich in der zweiten OEM-Gruppe. Wenn OEMName in der Datei für die unbeaufsichtigte Installation angegeben ist, wird der Wert für dieses Element nennen Sie die OEM-Gruppen, die erstellt wird.

#### <a name="modify-the-answer-file"></a>Ändern Sie die Antwortdatei

Ein System-Builder möchten möglicherweise zusätzliche erforderliche Anpassungen vor über eine Datei für die unbeaufsichtigte Installation vornehmen. Die Beispieldatei für die unbeaufsichtigte Installation auf USB-B enthält zusätzliche allgemeine Anpassungen.

    Copy /y E:\AnswerFiles\Unattend.xml C:\Mount\Windows\Windows\Panther

Dabei ist E:\ USB-B.

### <a name="optimize-winre"></a>Optimieren der Leistung von WinRE

1.  Vergrößern Sie Onlinetreiberinstallation.

        Dism /image:c:\mount\winre /set-scratchspace:512

1.  Bereinigung nicht verwendete Dateien und Größe der winre.wim reduzieren

        Dism /image:"c:\mount\winre" /Cleanup-Image /StartComponentCleanup /Resetbase

### <a name="unmount-images"></a>Heben Sie die Bereitstellung Bilder

1.  Schließen Sie alle Programme, die Dateien aus diesem Abbild zugreifen können

2.  Comit die Änderungen und heben Sie die Bereitstellung des Windows RE-Abbilds:

        Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit

    Dabei ist C der Laufwerkbuchstabe des das Laufwerk mit dem Bild.

    Dieser Vorgang kann einige Minuten dauern.

1.  Stellen Sie eine Sicherungskopie der aktualisierten Windows RE-Abbild.

    Problembehandlung: Wenn winre.wim unter dem angegebenen Verzeichnis nicht angezeigt wird, verwenden Sie den folgenden Befehl die Datei sichtbar festlegen:

        attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim

        Dism /export-image /sourceimagefile:c:\mount\windows\windows\system32\recovery\winre.wim /sourceindex:1 /DestinationImageFile:e:\images\winre_bak.wim

        Del c:\mount\windows\windows\system32\recovery\winre.wim

        Copy e:\images\winre_bak.wim c:\mount\windows\windows\system32\recovery\winre.wim

    Wenn Sie dazu aufgefordert werden, geben Sie **F** für Datei

1.  Überprüfen Sie die neue Größe des Windows RE-Abbilds.

            Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"

    Verwenden Sie die folgenden Partition Layout Größe Hinweise zum Bestimmen der Größe Ihrer Wiederherstellung Partition in Createpartitions -&lt;Firmware&gt;TXT-Dateien. Die Menge an freiem Speicher ist, nachdem Sie in die ausgeblendete Partition winre.wim kopieren.

    Verweisen Sie bitte [Festplattenpartition Regeln](https://technet.microsoft.com/library/hh824839.aspx#DiskPartitionRules) für Weitere Informationen.

    - Wenn die Partition kleiner als 500 MB ist, benötigen sie mindestens 50 MB freiem Speicherplatz.

    - Ist die Partition 500 MB oder mehr hat, benötigen sie mindestens 320 MB freiem Speicherplatz.

    - Wenn die Partition größer als 1 GB ist, wird empfohlen, dass er mindestens 1 GB freiem enthalten sollte.

            rem == Windows RE tools partition =============== 
            create partition primary size=500

    Optional: In diesem Abschnitt wird davon ausgegangen, dass Sie vielmehr winre.wim innerhalb install.wim auf die Sprachen und die Treiber synchron zu halten beibehalten würden. Wenn Sie etwas Zeit in der Fabrik speichern möchten, und wenn Sie diese Bilder OK separat verwalten, empfiehlt es sich pull winre.wim aus diesem Abbild und angewendet wird getrennt.

1.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

        Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
 
    Dabei ist C der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

## <a name="deploy-the-image-to-new-computers-windows-installation"></a>Bereitstellen des Abbilds auf neue Computer (Windows-Installation)

1.  Suchen Sie auf dem Referenzcomputer die folgenden Dateien in USB-B/Bereitstellung. Bitte finden Sie unter [Meine USB-B erstellen](#creating-my-usb-b) zum Erstellen und speichern die Dateien im richtigen Pfade. 

    ![Suchen nach USB-Dateien](Images/locate-usb-files.png)

2.  Starten des Referenzcomputers und verbinden USB-A.

3.  Verbinden Sie nach dem Start von Windows PE USB-B.

4.  Typ *Diskpart* und Treffer eingeben, um Diskpart zu starten. Geben Sie die *Liste Volume* zum Identifizieren der Volumebezeichnung eines USB-B (zum Beispiel: E:\). 

        E:\Deployment\Walkthrough-Deploy.bat E:\Images\ModelSpecificImage.wim

    Hinweis: Es sind mehrere hält im Skript. Sie werden aufgefordert Y/N für den Vorgang übernehmen, ist dies eine Compact OS-Bereitstellung.

1.  Hinweis: Nur verwenden Sie Compact OS auf Flashlaufwerk basierten Geräten, da der Speicher Gerätefunktionen Compact OS Leistung hängt. Compact OS wird NICHT empfohlen, auf Rotation Geräten. Weitere Informationen finden Sie unter [Compact OS](compact-os.md).

    Remove-USB-A- und USB-B, und geben Sie:

        Exit

## <a name="update-images-manually-by-using-audit-mode-online-servicing"></a>Aktualisieren Sie Bilder manuell mithilfe der ÜBERWACHUNGSMODUS (online – Wartung)

Wichtig: Herstellen einer Verbindung mit dem Computer mit Internet wird nicht empfohlen, während der Phasen manufacturing Es wird nicht empfohlen, zum Abrufen der Updates aus Windows Update im Überwachungsmodus aktiviert. Dadurch wird einen Fehler beim verallgemeinern + Syspreping den Computer wahrscheinlich im Überwachungsmodus generiert.

1.  Windows-Start im ÜBERWACHUNGSMODUS aktiviert und standardmäßig, für Benutzerprofile werden während des Aktivierungsvorgangs Generalisierung entfernt.

2.  Informationen zum Installieren von Office, finden Sie unter [Laden vorab Microsoft Office nur einem Bild v15.4 OPK](#preload-microsoft-office-single-image-v15.4-opk) Microsoft Office einzelnen Bild v15.4 oder [Laden Sie vorab Microsoft Office 2016](#preload-microsoft-office-2016) für Office 2016.

### <a name="preload-microsoft-office-2016"></a>Laden Sie Microsoft Office 2016

Dieses Handbuch enthält Informationen für lizenzierte Original Equipment Manufacturers (OEMs) zur Verwendung des Office-Bereitstellungstools zum Vorinstallieren von Office 2016 bei Geräten, die das Betriebssystem Microsoft Windows ausgeführt werden.

Hinweis: Dieses Handbuch nicht die PIPC Szenarien für OEMs in Japan beziehen. 

#### <a name="prepare-office-files-on-technician-pc"></a>Vorbereiten der Office-Dateien auf dem PC-Techniker

Office-Bereitstellungstool aus von X20 92403 Office 2016 v16-Bereitstellungstool für OEM OPK abrufen.

1.  Stellen Sie X20 92403 Office 2016 v16-Bereitstellungstool für OPK\Software OEM - SW DVD5 DVD\X20 92404 Office 2016 v16-Bereitstellungstool für OEM\x20 92404.img bereit.
2.  Kopieren von Dateien vom Laufwerk mit eingebundene USB-b (wobei E:\ ist Laufwerkbuchstaben für USB-B) E:\OfficeV16.
3.  Klicken Sie e:\Officev16\officedeploymenttool.exe doppelklicken auf.
4.  Enthalten Sie Ordnerpfad zum Extrahieren der Dateien E:\Officev16.

    Setup.exe und "Configuration.xml" werden in E:\Officev16 extrahiert.

    ![Setup und "Configuration.xml"](Images/setup-and-configuation.png)
    
    Office v16 in die gewünschte Sprache abrufen. In diesem Beispiel wird ASCII X20 39283 Office 2016 v16 32-BIT-X64 OPK Englisch.
    
5. Kopieren Sie den Ordner Office von bereitgestelltes Laufwerk X20 39283 Office 2016 v16 32-BIT-X64 OPK\Software - DVD\X20 37728 SW DVD5 Office Pro 2016 32 Englisch 64 englische C2ROPK Pro HS HB OEM\X20-37728.img USB-b (wobei E:\ ist Laufwerkbuchstaben für USB-B) E:\OfficeV16.

    ![Office-Ordner](Images/office-folder.png)
    
    [Optional] Wenn Sie ein Language Interface Pack angewendet haben, können Sie das Language Interface Pack für Office 2016 sowie hinzufügen möchten. Die folgenden Beispiele wird mit dem Language Interface Pack angewendet angezeigt.    

6. Editor-E:\Officev16\ConfigureO365Home.xml

7. Hinzufügen von Sprachen-ID, und überprüfen Sie SourcePath wie im folgenden Screenshot dargestellt.

    ![Sprachen-ID](Images/language-id.png)
    
8. ConfigureO365Home.xml speichern und schließen.

9. Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten als Administrator an.

10. Geben Sie E:\Officev16 und führen Sie setup.exe/Download ConfigureO365Home.xml:

    CD E:\Officev16 Setup.exe/Download ConfigureO365Home.xml
    
    Dadurch wird die Language Packs für Deutsch und Japanisch herunterladen.
    
11. Geben Sie ein, und führen Sie Echo %ERRORLEVEL%, und überprüfen Sie der Rückgabecode 0 ist.

12. Trennen Sie die USB-B aus dem Referenzcomputer. 

#### <a name="install-office-2016-on-reference-pc"></a>Installieren Sie Office 2016 auf Referenz-PC

1. Schließen Sie USB-B in dem Referenzcomputer im Überwachungsmodus aktiviert ist.
2.  Suchen Sie nach der Buchstabe des Laufwerks für USB-B; In diesem Beispiel wird USB-B E:\.
3.  Editor-ConfigureO365Home.xml.
4.  Konfigurieren der SourcePath USB-B E:\Officev16 auf.

    ![Konfigurieren des Quellpfades](Images/configure-source-path.png)
    
    Hinweis: die einzige Produkt-ID, die in der Datei "Configuration.xml" angegeben werden muss ist O365HomePremRetail. Wenn der Benutzer einen Schlüssel für ein anderes Produkt eingibt, werden wie für Office Home und Student 2016, klicken Sie dann Office automatisch als den zugehörigen Produkt konfiguriert.
    
5.  ConfigureO365Home.xml speichern und schließen.
6.  Öffnen Sie ein Eingabeaufforderungsfenster, und navigieren Sie zu d:\Officev16.
7.  Typ:

    Setup.exe / configure ConfigureO365Home.xml

#### <a name="pin-office-tiles-to-the-start-menu"></a>PIN Office Kacheln im Startmenü

Müssen Sie die Office-Kacheln im Startmenü anheften, andernfalls wird Windows die Office-Dateien entfernen, OOBE Boot Phase.

Hinweis: Sie müssen werden verwenden Sie mindestens Version 10.0.10586.0 Windows 10. Die folgenden Schritte aus, die mit früheren Versionen von Windows 10 funktionieren nicht.

1. Öffnen Sie ein Eingabeaufforderungsfenster und geben:

        notepad C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml.
        
2. Hinzufügen von &lt;AppendOfficeSuiteChoice Wahlmöglichkeiten = "Desktop2016" /&gt; Layoutmodification, als Sie finden Sie im folgenden Beispiel hervorgehoben:

    ![Layout Änderung](Images/layoutmodification.png)

    Hinweis: Das Choice-Attribut ist neu. Dadurch können unterschiedliche Versionen von Office auf der Startseite zur selben Zeit fixiert werden. Jetzt ist Desktop2016 der einzige gültige Wert. Andere Werte werden in der Zukunft verfügbar.

3. Layoutmodification.xml speichern und schließen.

    Hinweis: für die Wiederherstellung der layoutmodification.xml müssen während der Wiederherstellung kopiert werden. 
    
4.  Öffnen Sie ein Eingabeaufforderungsfenster und geben:

        copy C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml c:\recovery\OEM   

    Nachdem Sie der Computer nach dem durchgehen OOBE Desktop gestartet wird, müssen im Menü Start diese drei Kacheln angefügt wird, wie im folgenden Diagramm dargestellt: 
    
    ![Office-Kacheln fixiert im Startmenü](Images/office-tiles-pinned-to-start-menu.png)
    
####  <a name="configure-the-setup-experience-for-the-user"></a>Konfigurieren der Setup-Erfahrung für den Benutzer   

Nach der Installation von Office auf dem Gerät müssen Sie auch die Setup-Erfahrung für den Benutzer zu konfigurieren. Dies ist die Erfahrung der Benutzer erhält beim Öffnen einer Office-app zum ersten Mal auf dem Gerät. Dies ist auch vorgesehen, um sicherzustellen, dass Office ordnungsgemäß lizenziert und aktiviert ist.

|   Setup-Modus  | Beschreibung   |
|---------------|---------------|
|   OEM         | In diesem Modus kann Kunden versuchen, gekauft oder Office mit einer vorhandenen Kontos, PIN oder Product Key aktivieren auswählen. Dieser Modus unterstützt keine Aktivierung für Office (AFO) oder AFO späte Bindung. Wenn Sie diesen Modus auswählen, müssen Sie daher den Kunden mit einer Aktivierung-Karte (früher als einer Product Key oder ein Microsoft-Produkt-ID (MPI) bezeichnet) enthalten. |
|   OEMTA       |   In diesem Modus unterstützt die Try, gekauft oder Aktivieren der OEM-Modus sowie unterstützenden AFO und AFO Erfahrung spätes Binden. Dieser Modus unterstützt die Aktivierung von Office über das Gerät Windows-Product Key, was bedeutet, dass der Kunden einen 5 x 5-Produkt Tastencode eingeben muss würde nicht. |


OEM-Modus – Provide Benutzer mit Aktivierung Karte
1.  In Command Prompt Gehe zu Laufwerkbuchstaben für USB-B\Officev16
2.  Geben Sie ein, und führen: 

    OEMSETUP.cmd Mode = OEM

OEMTA Modus – erfolgt die Aktivierung über das Gerät Windows-Product Key.

1. Geben Sie ein, und führen:
 
    OEMSETUP.cmd Mode = OEMTA Verweis =####

### <a name="preload-microsoft-office-single-image-v154-opk"></a>Laden Sie Microsoft Office nur einem Bild v15.4 OPK

Laden Sie Microsoft Office nur einem Bild v15.4 aus dem [OEM Partner Center](http://www.microsoft.com/OEM/en/installation/downloads/Pages/office-single-image-v15-opk.aspx).

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten.

2.  Kopieren Sie den Inhalt des OPK in ein Verzeichnis, in der OfficeSingleImagev15.4InstallationDirectory verwendet wird.

3.  Navigieren Sie zu dem Installationsverzeichnis an. Das Installationsverzeichnis ist der Ordner mit den Dateien in der folgenden Abbildung dargestellt.

        Cd C:\<OfficeSingleImagev15.4InstallationDirectory>

    ![Installationsverzeichnis](Images/installation-directory.png)

    Wichtig: Der Installationsvorgang für das OPK gilt für Computer, auf denen 32-Bit-Betriebssysteme oder 64-Bit-Betriebssystemen ausgeführt werden sollen. Sie können die 32-Bit-Version von Office 2013 auf Computern Vorinstallation, auf denen 32-Bit oder 64-Bit-Betriebssystemen ausgeführt werden. Sie können die 64-Bit-Version von Office 2013 nur auf Computern Vorinstallation, auf denen 64-Bit-Betriebssystemen ausgeführt werden. Um mögliche Kompatibilitätsprobleme mit-add-ins oder drittanbieteranwendungen, Teiler *nur die 32-Bit-Version* des OPK auf 32-Bit- und 64-Bit-Computern zu verhindern.

1.  Führen Sie oemsetup.en-Skript für uns.

        oemsetup.en-us.cmd

1.  Nach Abschluss der Installation wird nur einem Bild von Microsoft Office v15.4 OOBE Anwendung Kachel für Apps Ansicht platziert werden.

2.  PIN bis die auf der Startseite finden Sie im *Abschnitt 4.2.4 Verankern Desktop-Apps-Startseite und Taskleiste* und Typ in **%allusersprofile%\Microsoft\Windows\Start Users\Startmenü\Programme\Microsoft installieren.lnk** auf &lt;AppIdOrPath&gt; Eigenschaft. Erhalten Sie, dass diese Anpassung bereits in die Antwortdatei USB-B\AnswerFiles\UnattendSysprep.xml stattfindet.

### <a name="prepare-the-system-for-recovery-with-push-button-reset"></a>Bereiten Sie das System für die Wiederherstellung mit der Schaltfläche Zurücksetzen

Verweisen auf bitte [Drucktaste zurücksetzen](push-button-reset-overview.md) und [Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md) und [Festplatten und Partitionen](hard-drives-and-partitions.md) für Weitere Informationen.

1.  Bereiten Sie das Tool ScanState vor.

    Wenn Sie ein Bild **X64** Windows 10 verwenden:

        md E:\ScanState_amd64

        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\amd64" E:\ScanState_amd64

        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\amd64\Sources" E:\ScanState_amd64

    Wenn Sie ein Bild **X86** Windows 10 verwenden:

        md E:\ScanState_x86

        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\x86" E:\ScanState_x86

        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\x86\Sources" E:\ScanState_x86

    Dabei ist E: Laufwerkbuchstaben USB-B.

1.  Erstellen einer Konfigurationsdatei.

    Sie können eine Konfigurationsdatei zum Wiederherstellen und Registrierungsschlüssel und Dateien während des Aktivierungsvorgangs PBR ausschließen verwenden.

    Wichtig: Dieser Abschnitt enthält eine Umgehung für ein bekanntes Problem in Windows 10. Sie müssen diese zu umgehen zur Vermeidung von Problemen mit dem Prozess PBR anwenden. 

    In einigen Fällen können Windows Defender Einstellungen und Erkennung Verlauf von dem Tool ScanState in das Paket Anpassungen erfasst werden. Dadurch kann dazu führen, dass Fehler während der Wiederherstellung aufgrund von Dateikonflikten, und den PC neu starten, und geben der Phase der **Installation von Windows** wiederholt.

    Hinweis: Verwenden Sie die pbr_config.xml-Konfigurationsdatei, die zuvor generiert wurde.

1.  Erstellen Sie das Wiederherstellungspaket.

    Verwenden Sie ScanState Tool zum Erfassen von der installierten Anpassungen in einer Bereitstellung Paket, und speichern Sie sie in den Ordner c:\Recovery\customizations. In diesem Dokument wird die Beispiele von USB-B\Recovery\RecoveryImage ScanState Paket erstellt verwendet.

    Wichtig: Das ScanState-Paket von PBR verwendet eine .ppkg-Datei im Ordner C:\Recovery\Customizations gespeichert werden muss oder PBR werden nicht das Paket wiederherstellen.

2.  Die Wiederherstellung OEM-Ordner und die Kopie Inhalt des USB-B\Recovery\RecoveryImage zu erstellen.

        Copy E:\Recovery\recoveryimage c:\recovery\OEM

        Copy E:\StartLayout\\*.\* c:\recovery\OEM

1.  Führen Sie ScanState um die app und Anpassungen zu erfassen.

    Wenn Sie ein Bild **X64** Windows 10 verwenden:

        E:\ScanState_amd64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /config:c:\Recovery\OEM\pbr_config.xml /o /c /v:13 /l:C:\ScanState.log

    Wenn Sie ein Bild **X86** 10 Windows verwenden:

        E:\ScanState_x86\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /config:C:\Recovery\OEM\pbr_config.xml /o /c /v:13 /l:C:\ScanState.log

    E: ist, auf dem der Laufwerkbuchstabe des USB-B.

1.  Erstellen Sie ein Skript Erweiterbarkeit, um zusätzliche Einstellungen und Anpassungen wiederherzustellen.

    Sie können die Drucktaste zurücksetzen Benutzererlebnis Erweiterungspunkte konfigurieren. So können Sie benutzerdefinierte Skripts ausführen, installieren zusätzliche Applikationen oder zusätzliche Daten für Benutzer, der Anwendung oder der Registrierung beibehalten.

    Das Beispielskript EnableCustomizations.cmd während PBR aufgerufen, und es werden zwei Schritte ausführen:

    ein.  Kopieren Sie die Datei unattend.xml für die erste Bereitstellung in den Ordner \windows\panther verwendet.

    b.  Kopieren Sie den layoutmodification.xml an das System.

### <a name="finalize-and-capture-manufacturing-image"></a>Abschließen und Fertigung Bild erfassen

1.  Löschen Sie die Installationsordner und Dateien erstellten vorinstallierte Anwendungsmöglichkeiten. Beispielsweise *C:\Office-SingleImagev15.4-Setup*und der Ordner *C:\LIPsToBeInstalled* . Existenz dieser Ordner möglicherweise die Größe der WIM-Datei erhöhen, wenn das Abbild des Windows-Laufwerks erfasst dient zum Abrufen.

2.  Wenn Sysprep geöffnet ist, schließen Sie es, und öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten.

3.  Kopieren Sie Winre Sicherung in Windows aus.

        Copy e:\images\winre_bak.wim c:\windows\system32\recovery\winre.wim

1.  Kopie unattend.xml zum Aktivieren der Wiederherstellung der Ordner für die Wiederherstellung für die unbeaufsichtigte Installation Einstellungen während der Schaltfläche im Besitzerzeichnungsmodus zurückgesetzt.

        Copy USB-B\answerfiles\unattendsysprep.xml c:\Recovery\OEM\unattend.xml

1.  Verbinden Sie USB-B mit Referenz-Computer.

2.  Verallgemeinern Sie das Bild mithilfe der Antwortdatei, die angibt, die Änderungen im Abschnitt [Bilder manuell mithilfe der ÜBERWACHUNGSMODUS (online – Wartung) aktualisieren](#update-images-manually-by-using-audit-mode-online-servicing).

    Hierzu gehören auch Microsoft Office Kachel Komponente auf dem Bildschirm Start fixiert.

        Cmd /c C:\Windows\System32\Sysprep\sysprep /unattend:c:\Recovery\OEM\Unattend.xml /generalize /oobe /shutdown

1.  Starten des Referenzcomputers und verbinden USB-A.

2.  Nachdem Windows PE gestartet wurde, eine Verbindung herstellen Sie USB-B.

3.  Typ *Diskpart* und Treffer eingeben, um Diskpart zu starten. Geben Sie dann die *Liste Volume* zum Identifizieren des Windows-Installation Datenträgers mit der Bezeichnung "Windows" Volumebezeichnung (zum Beispiel: E:\). Geben Sie schließlich *Beenden* , um Diskpart zu beenden.

4.  Starten Sie die Bereinigung des Bilds.

    Wichtig: Standardmäßig werden nicht-wichtige Updates (beispielsweise ZDPs oder LCUs) nicht wiederhergestellt. Um sicherzustellen, dass während der Herstellung vorinstalliert Updates nach der Wiederherstellung nicht verworfen werden, sollten sie als permanente gekennzeichnet werden mithilfe des Befehls /Cleanup-Image in DISM mit den Optionen /StartComponentCleanup und /ResetBase. Updates als permanente markiert werden immer während der Wiederherstellung wiederhergestellt. 

        MD e:\scratchdir

        dism /Cleanup-Image /Image:e:\ /StartComponentCleanup /resetbase /scratchdir:e:\scratchdir

1.  Erfassen Sie das Abbild der Windows-Partition. Dieser Vorgang kann mehrere Minuten.

        dism /Capture-Image /CaptureDir:E:\ /ImageFile:F:\Images\ModelSpecificImage.wim /Name:"myWinImageWithMSIUpdated" /scratchdir:e:\scratchdir

    Dabei steht die Volumebezeichnung Windows und F E die Volumebezeichnung eines USB-B.

1.  Kopieren Sie das Bild in USB-B. Dieser Vorgang kann mehrere Minuten.

        copy E:\ModelSpecificImage.wim H:\Images\

    H ist, auf dem die Volumebezeichnung eines USB-B.

    Dadurch wird das Bild im Abschnitt [Bereitstellen das Bild, das neue Computer](#deploy-the-image-to-new-computers)erstellt überschrieben.

## <a name="deploy-the-image"></a>Bereitstellen des Abbilds 

Verwenden Sie dem Bereitstellungsskript Layout Partitionen auf dem Gerät, und wenden Sie das Abbild. Die exemplarische Vorgehensweise-deploy.bat im Ordner USB-B\deployment wird das Gerät basierend auf Gerätemodus partitionieren.

**Wichtig: Die Wiederherstellungspartition muss der Partition nach der Windows-Partition, um sicherzustellen, dass winre.wim während der Lebensdauer des Geräts auf dem neuesten Stand aufbewahrt werden können.**

In Windows 10 Version 1511 sind wir unsere Empfehlung nach der Partition OS platziert WinRE-Partition einrichten zu ändern. Dadurch wird während des Updates künftiges Wachstum der WinRE Partition. Heute kann mit der Partition WinRE am Anfang des Datenträgers die Größe der nie geändert werden erschwert WinRE bei Bedarf zu aktualisieren. Es wird weiterhin zur Unterstützung die WinRE Partition befindet sich in verschiedenen Teilen eines Datenträger, doch neugierig werden auf die neue Empfehlung müssen.

E:\Deployment\walkthrough-Deploy.bat E:\Images\BasicImage.wim

Hinweis: Es sind mehrere hält im Skript. Sie werden aufgefordert Y/N für den Vorgang übernehmen, ist dies eine Compact OS-Bereitstellung.

Hinweis: Nur verwenden Sie Compact OS auf high-End-Speichergeräten, da der Speicher Gerätefunktionen Compact OS Leistung abhängt. Compact OS wird NICHT empfohlen, auf einen Geräte oder größer als 32 GB Speicher. Weitere Informationen finden Sie unter [Compact OS](compact-os.md).

Remove-USB-A- und USB-B und Type Neustart des Computers mit Windows 10 *Beenden* .

## <a name="finalize-deployment"></a>Abschließen der Bereitstellung

1.  Beim Bereitstellen von Ihrem Modell bestimmte Bild zur Darstellung der Zielcomputer, starten Sie den Computer mit master-Abbild zum ersten Mal im ÜBERWACHUNGSMODUS aktiviert

    Wichtig: In Reihenfolge beim ersten Start minimieren (Start > Specialize > OOBE > Startseite) specialize Durchlauf im Unternehmen ausgeführt werden muss. Specialize Durchlauf konfiguriere Hardware spezifische Informationen, die Windows ausgeführt werden soll.

    Weitere Informationen zu den ersten Boot Zeit Anforderungen finden Sie unter [Windows-Richtlinie für System-Builder](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_008).

1.  Beachten Sie, dass am Ende des Abschnitts [Update Bilder manuell mithilfe der ÜBERWACHUNGSMODUS (online – Wartung)](#update-images-manually-by-using-audit-mode-online-servicing-), das System OOBE-Modus verschlüsselt. Fahren Sie mit der Überwachung. Wenn das System in OOBE startet, drücken Sie STRG + UMSCHALT + F3, um OOBE und Boot im Überwachungsmodus übergeben.

2.  Wenn Sie zusätzliche Schritte, z. B. OEM-Diagnose und so weiter ausgeführt anwenden möchten sie hier angewendet werden.

3.  Schließlich führen Sie das Tool Sysprep (C:\Windows\System32\Sysprep\sysprep.exe) und das System wieder auf **OOBE** und **Herunterfahren** , jedoch *ohne* **verallgemeinern**bereit.

4.  Das System kann geliefert.

    Wichtig: Wenn Sie wenig Geräte ohne Verwendung eines Bilds Verwalten von Tool wie Duplicators Datenträger oder Windows-Bereitstellungsdienst manufacturing werden, Sie können die folgenden Methoden verwenden:

    1. Sie können diese Geräte Herstellung, durch die erste starten in Windows PE - einfügen USB-A. 
    2. Fügen Sie dann USB-B, in dem endgültigen Fertigung Bild enthalten ist. 
    3. Führen Sie Skript Walktrough bereitstellen, um das Bild zu übernehmen. 
    4. Nachdem Sie das Bild angewendet haben, führen Sie die Schritte in diesem Abschnitt Finalize zur Bereitstellung. 
    5. Jetzt kann das Gerät mit Ihrem letzten Fertigung Bild und PBR Feature implementiert geliefert werden sollen. 
    6. Replizieren Sie schließlich die gleiche Prozedur mit den anderen Geräten.

## <a name="appendix"></a>Anhang

### <a name="differences-between-64-bit-and-32-bit-deployment"></a>Unterschiede zwischen der 64-Bit- und 32-Bit-Bereitstellung

Es wird empfohlen, 64-Bit-Bereitstellung im Vergleich zu 32-Bit-Bereitstellungen Datenträger Bilanz gemäß den Speicher des Geräts berücksichtigt werden sollten, den Sie manufacturing sind.

64-Bit- und 32-Bit-Bereitstellung unterscheiden nicht der gesamten Bereitstellung Ablauf in diesem Handbuch erwähnten. Nur einige der Ressource Versionen und wie diese Ressourcen erstellt werden abweicht. In der folgenden Tabelle werden die Unterschiede X64/X86 behandelt.

| **Unterschied**                         | **Beschreibung**                                                                                                                                                                                                                                                                              | **Verwandte Abschnitt**                  |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| Windows auf Supporttechniker Computer installiert | Wenn Windows ADK auf einem Computer Supporttechniker installiert Ruft die würde die Bereitstellungstools in ADK entsprechend der Architektur von Windows auf dem Referenzcomputer installiert werden. Kurz gesagt Wenn ADK X64 von Windows installiert ist, wäre die Tools installiert 64-Bit-Version oder umgekehrt. | [Vorbereiten der laborumgebung](#prepare-your-lab-environment)         |
| Erstellen von Windows PE Ordnerstruktur         | Windows PE unterscheidet sich zwischen X64 und X86 Architektur, sodass Sie verschiedene Befehle verwenden, erstellen Sie einen anderen Ordner Windows PE für jede Architektur.                                                                                                                                                    | [Erstellen von startbare Windows PE-USB](#create-winpe-bootable-usb) |
| Treiber                                 | Treiberversionen unterscheiden sich zwischen verschiedenen Architekturen. Wenn Sie ein 64-Bit-Windows-Abbild Produktion, geben Sie für 32-Bit-Windows verwenden X64 Treiber und umgekehrt.                                                                                                                                                   | [Hinzufügen von Treibern](#add-drivers)         |
| Update-Paketen für Windows-Abbild       | Paket-Updateversionen unterscheiden zwischen verschiedenen Architekturen. Wenn Sie ein 64-Bit-Windows-Abbild Bitte verwenden manufacturing sind aktualisieren X64 für 32-Bit-Windows Pakete und umgekehrt.                                                                                                                                   | [Hinzufügen von Updatepakete](#add-update-packages) |
| Benutzeroberflächen-Sprachpakete                | WENN Sie X64 verwenden Windows 10 Bild, Install X64 Benutzeroberflächen-Sprachpaketen oder wenn Sie X86 verwenden Windows 10-Abbild installiert X86 Benutzeroberflächen-Sprachpaketen.                                                                                                                                                                    | [Bereiten Sie das System für die Wiederherstellung mit Drucktaste zurücksetzen](#prepare-the-system-for-recovery-with-push-button-reset)                          |

### <a name="what-you-will-need-and-where-to-get-it"></a>Sie benötigen, und es erhalten

Bevor Sie beginnen, das Bereitstellungsverfahren OEM erfordert bestimmte Kits herunterladen, die in diesem Handbuch, wie beispielsweise Microsoft Office nur einem Bild-v15.4 verwendet werden, Updatepakete von Benutzeroberflächen-Sprachpaketen usw.... Im folgenden ist die vollständige Liste der Ressourcen/Kits OEM benötigt, herunter, und wo sie herunterladen.

| Resource-Kit  |   Verfügbar unter    | Verwandte Abschnitt   |
|---------------|-------------------|-------------------|
| Windows 10 ADK|   [http://www.Microsoft.com/en-US/Download/Details.aspx?id=39982](http://www.microsoft.com/en-US/download/details.aspx?id=39982) | [Erstellen von startbare Windows PE-USB](#create-winpe-bootable-usb) |
| Windows 10 X64/X86 DVD-Medien (Sprache) | Rufen Sie Windows-10-Medien ab, die Sie anpassen werden von autorisierten Microsoft-Händler | [Installieren von Windows mit grundlegenden Anpassungen](#install-windows-with-basic-customizations) |
| Windows 10 Standard Product Keys | Standard-Product Keys befinden sich unter [OEM Partner Center](https://www.microsoft.com/OEM/en/products/windows/Pages/windows-10-build.aspx#fbid=nV7H02bHHiv) gemäß der Registerkarte **Standard die Product keys** | [Die Antwortdatei anpassen](#customize-the-answer-file) |
| Benutzeroberflächen-Sprachpakete | Benutzeroberflächen-Sprachpaketen sind finden Sie unter [OEM Partner Center](https://www.microsoft.com/OEM/en/installation/downloads/Pages/Windows-10-v1511-Language-Interface-Packs.aspx#fbid=nV7H02bHHiv) **Benutzeroberflächen-Sprachpaketen** Registerkarte aufgeführt | [Bereiten Sie das System für die Wiederherstellung mit der Schaltfläche Zurücksetzen](#prepare-the-system-for-recovery-with-push-button-reset) |
| Liste der wichtige Updates vom November 2015, KB 3118754 Update-Paketen | Updatepakete durch Herunterladen von [Microsoft Update-Katalog](http://catalog.update.microsoft.com/v7/site/Home.aspx)zu erhalten. Das Herunterladen von Updatepakete detaillierte Verfahren wird im Abschnitt Releated genannt. | [Hinzufügen von Benutzeroberflächen-Sprachpaketen](#add-language-interface-packs) |
| Microsoft Office v15.4 | Microsoft Office v15.4 durch Herunterladen von [OEM Partner Center](http://www.microsoft.com/OEM/en/installation/downloads/Pages/office-single-image-v15-opk.aspx) zu erhalten | [Laden Sie Microsoft Office nur einem Bild v15.4 OPK](#preload-microsoft-office-single-image-v15-4-opk) |


## <a name="references"></a>Verweise

[Windows-Richtlinien für System-Builder](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_129)

[Windows-Richtlinie für System-Builder](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_008)


