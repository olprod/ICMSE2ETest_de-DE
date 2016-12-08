---
title: "OEM Bereitstellung von Windows-10 für desktop-Editionen"
author: Justinha
description: "Rufen Sie Schritt-Anleitung für OEMs Windows 10 auf Desktopcomputern, Laptops und 2-in-1 s bereitstellen. Hier finden Sie Informationen zum Aktivieren von imageless, Drucktaste zurücksetzen Recovery und mehr."
ms.openlocfilehash: 11c7a1e2b78ce02ab19a863e1dfe34635e0b3195
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oem-deployment-of-windows-10-for-desktop-editions"></a>OEM Bereitstellung von Windows-10 für desktop-Editionen

In diesem Handbuch werden eine unterstützende Methode für die Bereitstellung von Windows 10, Version 1511 Verwendung der klassischen Bereitstellungstools. Viele der Tools und Methoden, die in einer klassischen Windows 8.1-Bereitstellung verwendeten gelten für Windows 10. Die größte Änderung erfolgt ist der Wiederherstellungsprozess, auf dem Windows-10 Bild weniger Wiederherstellung ermöglicht.  

Dieses Handbuch ist für OEMs vorgesehen und gilt für Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen). IT-Experten zur Verwendung dieses Handbuchs sollte vorhandene Kenntnisse über die grundlegenden Windows-Verwaltung und Problembehandlung. Weitere Informationen zu den Neuigkeiten neu im Windows-10-Bereitstellung finden Sie unter [Windows-10-Bereitstellung und Tools](https://technet.microsoft.com/library/mt297512.aspx).

Die neueste Version finden Sie unter [Windows 10, Version 1607 Version dieses Handbuchs](oem-deployment-for-desktop-1607.md). 

## <a name="about-this-guide"></a>Informationen zu diesem Handbuch

In diesem Handbuch wird um drei Hardware- und Softwarekonfigurationen organisiert.

| Hardwarekonfiguration       | 1            | 1 b           | 2            |
|------------------------------|--------------|--------------|--------------|
| Formfaktor                  | Kleine tablet | 2-in-1       | Notizbuch     |
| Arbeitsspeicher (RAM)                          | 1 GB         | 2 GB         | 4 GB         |
| Datenträgerkapazität und Typ       | 16 GB eMMC   | 32 GB eMMC   | 500 GB-FESTPLATTE   |
| Anzeigegröße                 | 8"           | 10"          | 14"          |
| Windows-SKU                  | Kern         | Pro          | Kern         |
| Sprache(n)                  | EN-US        | EN-US, DE-DE | EN-US, DE-DE |
| Cortana                      | Ja          | Ja          | Ja          |
| Posteingang apps (Universal)       | Ja          | Ja          | Ja          |
| Stift                          | Nein           | Ja          | Nein           |
| Office (Universal)           | Ja          | Ja          | Ja          |
| Windows-desktopanwendungen | Nein           | Ja          | Ja          |
| Office 2016                  | Nein           | Ja          | Ja          |
| Compact OS                   | Ja          | Ja          | Nein           |

Viele der Tools und Techniken Bereitstellung sind dieselben wie für Windows 8.1. Windows 10 hat WIMBoot veraltet und ersetzt ihn durch [Compact OS](compact-os.md). 

### <a name="oem-activation-30"></a>OEM-Aktivierung 3.0

Für OEMs Bereitstellung von Systemen mit **OEM Activation 3.0 (bei Zugriff 3.0)** aktiviert wenden Sie sich besonders wichtige zusätzliche Schritte und Hilfestellung bezüglich Aspekte **bei Zugriff 3.0** .

### <a name="deployment-and-imaging-tools-environment"></a>Bereitstellung und Imaging-Tools-Umgebung

Das Windows Assessment and Deployment Kit (Windows ADK) ist eine Sammlung von Tools und Dokumentation, die OEMs, ODMs und IT-Experten zum Anpassen, bewerten und Bereitstellen von Windows-Betriebssystemen auf neuen Computern verwenden. Bereitstellungstools können Sie anpassen, verwalten und Bereitstellen von Windows-Abbildern. Sie können auch zum Automatisieren der Windows-Bereitstellungen, entfernen die Notwendigkeit für die Benutzerinteraktion während der Installation von Windows verwendet werden.

Sie müssen für die Bilder die entsprechende Version von Windows ADK verwenden, die Sie anpassen möchten. Wenn Sie ein Abbild basierend auf Windows 10, Version 1511, anpassen müssen Sie die Windows-ADK aus Windows 10, Version 1511 verwenden.  


|  Windows-version  | Link zu ADKSetup.exe ausführen      |
|-------------------|-------------------------------|
| Windows-10, RTM-Version    | [**Windows ADK**](http://download.microsoft.com/download/8/1/9/8197FEB9-FABE-48FD-A537-7D8709586715/adk/adksetup.exe)  |
| Windows-10, Version 1511 | [**Windows ADK**](https://go.microsoft.com/fwlink/p/?LinkId=823089) |

Die Tools in Windows ADK, das Sie mit diesem Handbuch verwenden möchten:

-   10 Windows PE

-   Tool Abbildern Bereitstellung und Verwaltung (DISM)

-   Windows System Image Manager (SIM)

-   OSCDIMG, BCDBoot und andere tools und Schnittstellen

-   User State Migrationstool (USMT)

-   Treiber für Windows Überlagerung Filter (Routingereignisalias):

    -   Windows-10-Version von Routingereignisalias Treiber unterstützt Compact OS

    -   Abwärtskompatibel zu WIMBoot v1 auf älteres Betriebssystem

    -   Posteingang in Windows 10 und 10 Windows PE

    -   Installation mit Bereitstellungstools Kategorie mit unterstützten Vorgängerversionen Host (auf Windows 7)

### <a name="prerequisites"></a>Voraussetzungen

Zum Ausführen der Schritte in diesem Handbuch werden OEMs ist Folgendes erforderlich:

-   **Ein Referenzcomputer**: ein PC mit Windows 10 oder Windows 8.1 auf dem [Windows ADK](http://go.microsoft.com/fwlink/?LinkId=293840) installiert werden. 32-Bit-PCs erfordern eine 32-Bit-Version von Windows einige Tools verwenden.

Hinweis: Dieses Handbuch enthält Windows PowerShell-Beispielskript zum automatisieren Wartung offline-Abschnitt. Um das Skript zu verwenden, benötigen Sie ein Referenzcomputer unter Windows 10.

-   **Eine Referenz-Computer**: ein PC, das alle PCs in ein einziges Modell Linie darstellt beispielsweise der Fabrikam-Notizbuch PC Datenreihe.
    
    Wählen Sie für diesen PC von einem Element, das die Hardware-Konfigurationstabelle ähnelt.

    ![Was ist der ADK?](images/what-is-adk.png)

    Hinweis: Es wird empfohlen, da die 32-Bit-Version unterstützt die 32-Bit- und 64-Bit-Bereitstellungen mithilfe von der 32-Bit-Version von Windows auf dem Referenzcomputer.

    Führen Sie die auf dem Bildschirm Anweisungen zum Installieren von **Windows 10 ADK**, einschließlich der **Bereitstellungstools**, **Windows-Vorinstallation-Umgebung**und **Windows Assessment Toolkit** -Features.

    ![Auswählen von ADK-Funktionen](images/adk-select-features.png)

    Wenn die Installation erfolgreich ist, klicken Sie auf **Installieren**.

#### <a name="creating-my-usb-b"></a>Erstellen von meiner USB-B

-   Die Schritte zur Bereitstellung in diesem Handbuch richten sich nach der Beispielkonfigurationsdateien in **USB-B**enthalten. Sie können die [USB-B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip) aus dem Microsoft Download Center herunterladen. 

-   Die Inhalte der Konfigurationsdateien in **USB-B** enthalten sind Beispiele, in denen Sie gemäß Ihrer Auswahl branding und Produktion ändern können. Allerdings muss Dateinamen und die Hierarchie der Ordner und Dateien die gleichen wie unten dargestellt, um Ihre Bereitstellungsverfahren in diesem Handbuch ausrichten.

Formatieren des gewünschten USB-Laufwerk ein, und nennen Sie sie wie folgt:

![Extrahieren von USB](images/extract-usb.png) 

### <a name="software-downloads"></a>Software-downloads

Zum Ausführen dieses Handbuch sind viele OPK Downloads von <https://www.microsoftoem.com>erforderlich. In der folgenden Tabelle gezeigt, dass die erforderlichen und optionalen downloads vor der ersten auf den Vorgang.

In diesem Handbuch verwendet Windows RTM-VERSION 10 Bilder als Beispiele zum Erstellen von Bildern. Sie sollten für das aktuelle OPK auf <https://www.microsoftoem.com> überprüfen, bevor Sie in den Abschnitten in diesem Handbuch.

**Wichtig: Die Version des Windows-Komponenten, Windows ADK, Sprachpakete, Departements und Benutzeroberflächen-Sprachpaket muss die Windows-10-Image-Version übereinstimmen.**

#### <a name="windows-10-rtm-images-and-updates"></a>Windows RTM-VERSION 10 Bilder und updates

|           |                                  |
|-----------|----------------------------------|
| X20 09658 | 10 Windows Home 32 64 Englisch OPK    |
| X20 09716 | 10 Windows Home SL 32 64 Englisch OPK |
| X20 09737 | Windows 10 Pro 32 64 Englisch OPK     |

#### <a name="optional-windows-10-language-packs-fods-and-appx-bundles"></a>Optional: Windows 10 Sprachpakete, FODs und Appx fasst

Hinweis: Wenn installieren neue oder zusätzliche Language packs, FODs und Appx Pakete Downloads erforderlich sind.

|           |                                            |
|-----------|--------------------------------------------|
| X20 20209 | Windows 10 32 64 mehrsprachige OPK LangPackAll     |
| X20 53652 | Windows-10 für desktop-Editionen OPK Supp Updates Sep15     |
| X20 52949 | Office Mobile mehrsprachige OPK-2             |
| X19 96440 | Office 2013 Single Image v15.4 englische OPK |

#### <a name="windows-10-version-1511-images-and-updates"></a>Windows 10, Version 1511 Bilder und updates

|  |       |
|-----------|----------------------------------------|
| X20 74664 | Windows 10 Home, Version 1511 32/64 English OPK     |
| X20 74668 | Windows 10 Home SL, Version 1511 32/64 English OPK  |
| X20 74669 | Windows 10 Home SL, Version 1511 32/64 Eng internes OPK |
| X20 74672 | Windows 10 Pro, Version 1511 32/64 English OPK      |

#### <a name="optional-windows-10-version-1511-language-packs-fods-and-appx-bundles"></a>Optional: Windows 10, Version 1511 Sprachpakete, FODs und Appx fasst

Hinweis: Wenn installieren neue oder zusätzliche Language packs, FODs und Appx Pakete Downloads erforderlich sind.

|   |   |
|-----------|-------------------------------------------------|
| X20 74675 | Windows-10, Version 1511 32/64 mehrsprachige OPK LangPackAll/LIP |
| X20 74677 | Windows-10, Version 1511 32/64 mehrsprachige OPK Feat bei Bedarf  |
| X20 87906 | Windows-10, Version 1511 32-BIT-/ X 64 mehrsprachige OPK App aktualisieren |
| X20 52949 | Office Mobile mehrsprachige OPK-2                  |
| X19 96440 | Office 2013 Single Image v15.4 englische OPK      |

## <a name="windows-10-deployment-procedure"></a>Windows-10-Bereitstellungsverfahren

Dieser Abschnitt führt Sie durch die Skripts und Schritte zum Erstellen eines Windows-10-Bilds.

In diesem Handbuch wird verwendet, Beispiele für Konfigurationsdateien und Skripts als auch eine Kopie der Windows-Installationsdateien auf einem USB-Schlüssel gespeichert. Bevor Sie dieses Handbuch starten, die Schritte in [Erstellen von Meine USB-B](#creating-my-usb-b).

Dieses Flussdiagramm zeigt die Schritte zur Bereitstellung:

![Bereitstellungsprozess](images/deployment-process.png)

### <a name="create-a-winpe-bootable-usb"></a>Erstellen Sie eine startbare Windows PE-USB

1.  Drücken Sie die Windows-Taste, um im Menü **Start** angezeigt. Typ:
    
        Deployment and Imaging Tools Environment

    Maustaste auf den Namen des Tools aus, und klicken Sie dann auf **als Administrator ausführen**.

    Optional: beschleunigen Sie die Optimierung und Image Capture Prozesse durch Festlegen des Power Schemas mit hoher Leistung:

    -   Klicken Sie auf **Start**, geben Sie **powercfg.cpl**ein. Systemsteuerungsoption **Energieoptionen** wird angezeigt.

    -   Wählen Sie das **Hohe Leistung** Power-Schema. (Wenn sie nicht angezeigt wird, wählen Sie **zusätzliche Pläne anzeigen**.)

1.  Der "Bereitstellungsumgebung Tools Eingabeaufforderung" Basis Windows PE in einen neuen Ordner auf dem Referenzcomputer kopieren.
    
    Wenn Sie ein Bild **X64** Windows 10, Kopie der X64 Windows PE Ordnerstruktur verwenden:

        Copype amd64 C:\winpe_amd64

    Wenn Sie ein Bild **X86** Windows 10, Kopie der X86 Windows PE Ordnerstruktur verwenden:

        Copype x86 C:\winpe_x86

1.  **Optional**: Mount Windows PE Bild zur Darstellung der zusätzliche Pakete und Sprachen hinzuzufügen.
   
    Wenn Sie ein Bild **X64** Windows 10, die X64 Mount Windows PE Bild verwenden:

        Dism /mount-image /imagefile:c:\WinPE_amd64\media\sources\boot.wim /index:1 /mountdir:c:\winpe_amd64\mount

    Wenn Sie ein Bild **X86** Windows 10, die X86 Mount Windows PE Bild verwenden:

        Dism /mount-image /imagefile:c:\WinPE_x86\media\sources\boot.wim /index:1 /mountdir:c:\winpe_x86\mount

#### <a name="add-packages-dependencies-and-language-packs"></a>Hinzufügen von Paketen, Abhängigkeiten und Sprachpakete

Verwenden Sie **Dism** -Befehl mit der **Option/Add-Package** . Beispielsweise müssen, um mithilfe von Windows PowerShell in Windows PE NetFx Abhängigkeit und die Language Packs installiert sein.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    dism /image:C:\winpe_amd64\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-NetFx.cab"
    dism /image:C:\winpe_amd64\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-NetFx_en-us.cab"
    dism /image:C:\winpe_amd64\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-PowerShell.cab"
    dism /image:C:\winpe_amd64\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Powershell_en-us.cab"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    dism /image:C:\winpe_x86\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\WinPE-NetFx.cab"
    dism /image:C:\winpe_x86\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\en-us\WinPE-NetFx_en-us.cab"
    dism /image:C:\winpe_x86\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\WinPE-PowerShell.cab"
    dism /image:C:\winpe_x86\mount /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\en-us\WinPE-Powershell_en-us.cab"

#### <a name="add-drivers"></a>Hinzufügen von Treibern 

Verwenden Sie Dism den Befehl mit der Option/Add-Driver. 

Hinweis: Diese Methode erfordert Treiber INF-basierte werden. Es wird empfohlen, INF-basierte Treiber vom IHV Lieferanten abgerufen.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    dism /image:C:\winpe_amd64\mount /Add-Driver /driver:"C:\Out-of-Box Drivers\mydriver.inf"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    dism /image:C:\winpe_x86\mount /Add-Driver /driver:"C:\Out-of-Box Drivers\mydriver.inf"

Hinweis: Zum Installieren von alle Treiber in einen Ordner und alle Unterordner verwenden der Option/recurse. 

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    dism /Image:C:\Winpe_amd64 /Add-Driver /Driver:c:\drivers /Recurse

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    dism /Image:C:\Winpe_x86 /Add-Driver /Driver:c:\drivers /Recurse

#### <a name="cleanup-bootwim"></a>Bereinigung boot.wim

Führen Sie Cleanup, um die Datenträger- und Arbeitsspeicher Speicherbedarf von Windows PE, zu verringern, für den unteren-Spec-Geräten (wie Geräten mit 1 GB Ram oder 16 GB Speicher) geeignet ist. Dadurch wird die Kompatibilität mit eine Breite Palette von Geräten erhöht. Beginnend mit Windows 10, Version 1607 verwenden, können Sie mit /Resetbase verzögern langer Cleanup Vorgänge auf die nächste automatische Verwaltung den /Defer-Parameter angeben. Es wird jedoch dringend empfohlen Sie **nur** als eine Option in der Factory, in denen DISM /Resetbase erfordert mehr als 30 Minuten, /Defer verwenden.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    dism /image:c:\winpe_amd64\mount /Cleanup-image /StartComponentCleanup /ResetBase

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    dism /image:c:\winpe_x86\mount /Cleanup-image /StartComponentCleanup /ResetBase 

#### <a name="optimize-winpe-on-boot"></a>Optimieren der Leistung von Windows PE starten

Online Windows PE durch Festlegen des Power Schemas auf hohe Leistung zu optimieren:

Hinweis: Einrichten von hohe Leistung kann zur Performnce des Geräts auswirken.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Notepad.exe c:\winpe_amd64\mount\windows\system32\startnet.cmd

Geben Sie in Editor ein:

    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c

Schließen Sie und speichern Sie Editor.

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Notepad.exe c:\winpe_x86\mount\windows\system32\startnet.cmd

Geben Sie in Editor ein: 

    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c

Schließen Sie und speichern Sie Editor.

![Startnet](images/startnet.png)

#### <a name="commit-changes-to-winpe"></a>Commit der Änderungen in Windows PE 

Führen Sie die Befehle in der folgenden Tabelle commit der Änderungen in Windows PE und Dateien zum Löschen markiert.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    dism /unmount-image /mountdir:c:\winpe_amd64\mount /commit
    dism /export-image /sourceimagefile:c:\winpe_amd64\media\sources\boot.wim /sourceindex:1 /DestinationImageFile:c:\winpe_amd64\mount\boot2.wim
    Del c:\winpe_amd64\media\sources\boot.wim
    Copy c:\winpe_amd64\mount\boot2.wim c:\winpe_amd64\media\sources\boot.wim
   
Wenn Sie ein Bild **X86** Windows 10 verwenden:

    dism /unmount-image /mountdir:c:\winpe_x86\mount /commit
    dism /export-image /sourceimagefile:c:\winpe_x86\media\sources\boot.wim /sourceindex:1 /DestinationImageFile:c:\winpe_x86\mount\boot2.wim
    Del c:\winpe_x86\media\sources\boot.wim
    Copy c:\winpe_x86\mount\boot2.wim c:\winpe_x86\media\sources\boot.wim

#### <a name="create-a-bootable-usb-key"></a>Erstellen eines startbaren USB-Schlüssels

1.  Verbinden **USB-A-** Laufwerk. Stellen Sie sicher, dass die Kapazität von mindestens 4 GB ist.

2.  Stellen Sie dem eingefügten USB ein startbare Windows PE-USB-Laufwerk.

    Hinweis: Wenn Sie Ihr USB-A-Stick gekennzeichnet haben, wird das folgende Skript die Bezeichnung "Windows PE" überschrieben. 

    Wenn Sie ein Bild **X64** Windows 10 verwenden:

        MakeWinPEMedia /UFD /f C:\winpe_amd64 E:

    Wenn Sie ein Bild **X86** Windows 10 verwenden:

        MakeWinPEMedia /UFD /f C:\winpe_x86 E:    
    
    (dabei E: ist der Laufwerkbuchstabe des **USB-A**)

### <a name="install-windows-with-basic-customizations"></a>Installieren von Windows mit grundlegenden Anpassungen

Ein Dokument, die Sie anpassen, die in der Datei unattend.xml definierten Anpassungen unterstützen finden Sie unter der [Windows 10 Update OEM Richtlinie Dokument (OPD)](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/COMM-Win10-OPD-RTM-Now-Avail.aspx).

Laden Sie Windows 10 Professional von [Digital Operations Center](http://www.microsoftoem.com/) Software Order Center, und verwenden Sie das Microsoft Media Creation-Tool aus [SOC Ressourcen](https://moo.microsoftoem.com/okdnet/SOCResources.aspx) , um die ISO-Dateien zu generieren. OEMs können das Windows-Kit herunterladen, das Ihnen im Hinblick auf Sprache und Edition anwendbar ist.

#### <a name="create-an-answer-file"></a>Erstellen einer Antwortdatei

"Antwortdatei" ist eine XML-basierte Datei mit Einstellungsdefinitionen und Werte, die während der Installation von Windows verwenden. In einer Antwortdatei geben Sie verschiedene Setupoptionen, einschließlich partitionieren, den Speicherort des Bilds Windows installieren und den Product Key anwenden. Werte, die für die Windows-Installation, wie die Namen von Benutzerkonten, gelten Einstellungen anzeigen und Internet Explorer-Favoriten kann auch angegeben werden. Die Antwortdatei für das Setup wird normalerweise **Unattend.xml**aufgerufen.

In Windows System Image Manager (Windows SIM) erstellte Antwortdateien sind ein bestimmtes Windows-Abbild zugeordnet. Auf diese Weise können, überprüfen die Einstellungen in die Antwortdatei an den Einstellungen im Windows-Abbild verfügbar. Da jede Antwortdatei verwendet werden kann, Windows-Abbild installieren, wenn Einstellungen in die Antwortdatei für Komponenten, die nicht in der Windows-Abbild vorhanden sind, werden diese Einstellungen ignoriert.

In diesem Handbuch werden drei unterschiedliche Antwortdateien verwendet:

![Drei Antwortdateien](images/three-answer-files.png)

Hinweis: Sie müssen Punkt Windows System Image Manager (SIM) an ein install.wim bevor Sie erstellen und die Antwortdatei anpassen können.

1.  Stellen Sie auf dem Referenzcomputer ISO-Abbild von Windows (siehe unten) durch Doppelklicken auf ihn bereit. Markieren Sie alle Dateien auf die bereitgestellten ISO E:\MyWindows, wie in der folgenden Abbildung dargestellt.

    ![Bereitgestellte Dateien](images/mounted-files.png)

1.  Führen Sie **Windows System Image Manager** zum Erstellen einer Antwortdatei von Grund auf neu starten. Dieses Tool ermöglicht die Erstellung oder Verwaltung Antwortdateien auf einfache und organisierte Weise.
    
    ![Erstellen einer Antwortdatei](images/create-answer-file.png)  
    
    Referenz: Näheres [WSIM Übersicht](https://technet.microsoft.com/library/hh825214.aspx) für Weitere Informationen zu Windows System Image Manager (SIM)-Benutzeroberfläche.

1.  Klicken Sie auf **Datei** > **Windows-Abbild auswählen**. Navigieren Sie zu E:\MyWindows\Sources\*Install.wim*. Eine Katalogdatei wird (CLG-Datei) für dieses bestimmte Wim erstellt werden.

    Problembehandlung bei: Erstellen des Katalogs kann aus verschiedenen Gründen fehlschlagen. Möglicherweise wird Folgendes angezeigt:

    ![Fehler beim Erstellen der Katalog](images/catalog-creation-fail.png)

1.  Klicken Sie auf **Ja**.

    Hinweis: Stellen Sie sicher install.wim verfügt über Lese-/Schreibberechtigungen und die Person, die dies erstellt der Administrator des lokalen Computers ist. Install.wim Bild und Windows 10 ADK Versionen müssen identisch sein. Wenn die folgenden Fehler angezeigt wird, stellen Sie sicher, dass die richtige Architektur von Windows 10 (X86 oder X64) auf dem Referenzcomputer installiert ist. 
    
    ![Architektur Nichtübereinstimmung](images/catalog-fail-arch-mismatch.png)

1.  Öffnen Sie eine Antwort-Beispieldatei oder erstellen Sie einen neuen Anwendungspool. Es wird empfohlen, verwenden die Beispiel-Antwortdateien im **USB-B**bereitgestellt.
    
    <table>
    <tr>
    <td>Bei Zugriff 3.0 Systeme:
    </td>
    <td>**USB-B**\ConfigSet\\**OA3.0**\AutoUnattend.xml
    </td>
    </tr>
    <tr>
    <td>Nicht bei Zugriff 3.0 - Systeme:
    </td>
    <td>**USB-B**\ConfigSet\\**Non_OA3.0**\AutoUnattend.xml
    </td>
    </tr>
    </table>
   
1.  Klicken Sie auf **OK** , wenn Sie dazu aufgefordert werden, um die Antwortdatei mit dem Windows-Abbild zuzuordnen.

#### <a name="customize-the-answer-file"></a>Die Antwortdatei anpassen

Hinweis: Ein leerer Zeichen in specialize | Microsoft-Windows-Shell-Setup | Abschnitt Computer Name die Antwortdatei führt Installationsfehler Windows.

1.  Grundlegende Anpassungen finden Sie die bereitgestellten Beispiel-Antwortdateien im **USB-B**. Beachten Sie, dass die Antwort-Beispieldateien im **USB-B** Platzhalterwerte verfügen, die vor der Verwendung geändert werden muss. Es wird empfohlen, OEMs Erstellen ihrer eigenen Antwortdateien und verwenden die folgenden Dateien als Punkt oder die Referenz:

    <table>
    <tr>
    <td>Bei Zugriff 3.0 Systeme:
    </td>
    <td>**USB-B**\ConfigSet\\**OA3.0**\AutoUnattend.xml
    </td>
    </tr>
    <tr>
    <td>Nicht bei Zugriff 3.0 - Systeme:
    </td>
    <td>**USB-B**\ConfigSet\\**Non_OA3.0**\\AutoUnattend.xml
    </td>
    </tr>
    </table>
   
    Addition Beispiele finden Sie unter [Technet-Referenz für die unbeaufsichtigte Installation Sample](https://technet.microsoft.com/library/cc732280.aspx) .

1.  Geben Sie den Product Key in die Antwortdatei ein. Diese Anpassung ist in der Beispieldatei Antwort im **USB-B**enthalten. Es gibt zwei verschiedene Möglichkeiten, um den Product Key in die Antwortdatei anzugeben:

    -   Verwenden Sie diese Einstellung [ProductKey](http://technet.microsoft.com/library/cc721925.aspx) in der Microsoft-Windows-Setup-Komponente während der **WindowsPE übergeben** an das Windows-Abbild während der Installation von Windows installiert. Der von dieser Einstellung angegebene Product Key wird nach der Installation auf dem Computer gespeichert. Wenn Windows aktiviert ist, wird dieser Product Key verwendet werden.

    -   Verwenden Sie diese Einstellung [ProductKey](http://technet.microsoft.com/library/cc749389.aspx) in der Komponente Microsoft-Windows-Shell-Setup während der **specialize übergeben** , um einen anderen Product Key zum Aktivieren der Windows anzugeben. Beispielsweise kann einen Product Key zum Installieren von Windows mit der ProductKey in Microsoft-Windows-Setup-Komponente aus, und geben Sie einen anderen Product Key zum Aktivieren von Windows angegeben werden.

Näheres Kit Handbuch Windows 10 Standard Manufacturing Schlüssel OEM PDF-DATEI, Standard Product Keys für **OA3.0** und **Nicht OA3.0** Schlüssel zu erhalten.

Beispiel: Navigieren Sie zu OPK X20 74664 Win Home 10 1511 32 64 englische OPK\Print Content\X20 09791 Kit Guide gewinnen 10 wichtigsten OEM\X2009791GDE.pdf Manufacturing Standard.

#### <a name="install-windows"></a>Installieren von Windows

1.  Verbinden der **USB-A-** Laufwerk ein, und Starten des Referenzcomputers.

    Hinweis: Wenn starten mit USB-Laufwerk ein Fehler auftritt, stellen Sie sicher, dass USB-Start anstelle von HDD Boot priorisiert wurden hat. Dazu kann es so wechseln zur des Referenzcomputers erforderlich sein / des Geräts BIOS-Menü, und passen Sie die Startreihenfolge Priorität, damit der USB-Schlüssel am oberen Rand der Liste ist.

1.  Nachdem Windows PE gestartet wurde, legen Sie ein **USB-B**.

2.  Bei der **X:\windows\system32 >** Prompt, Typ ***Diskpart*** , und drücken Sie die ** &lt;EINGABETASTE&gt; ** -Taste, um Diskpart zu starten.

3.  Bei der **\DISKPART&gt; ** Aufforderung geben Sie ***List Volume***.

    Hinweis: Überprüfen, welche Buchstaben USB-B in der Spalte "Ltr" zugewiesen wurde (Beispiel: E). Dies ist der Laufwerkbuchstabe, die während der Installation verwendet werden.

1.  Geben Sie zum Beenden der Diskpart ***zu beenden*** .

    ![Diskpart](images/diskpart.png)
    
1.  Führen Sie ***setup.exe*** mit einer Antwortdatei, und installieren Sie Windows 10 Updates mit zusätzlichen OEM Anpassungen. Kopieren Sie die Befehle in der folgenden Tabelle.

    <table>
    <tr>
    <td>Bei Zugriff 3.0 Systeme:
    </td>
    </tr>
    <tr>
    <td><code><br>Xcopy /herky e:\configset\$oem$ e:\MyWindows\Sources\$OEM$</br>
    <br>E:\MyWindows\Setup.exe /unattend:E:\Configset\OA3.0\AutoUnattend.xml
    </br></code>
    <p>Drücken Sie D für Verzeichnis, wenn Sie dazu aufgefordert werden.
    </p>
    </td>
    </tr>
    </table>
    
    <table>
    <tr>
    <td>Nicht bei Zugriff 3.0 - Systeme:
    </td>
    </tr>
    <tr>
    <td><code><br>Xcopy /herky e:\configset\$oem$ e:\MyWindows\Sources\$OEM$</br>
    <br>E:\MyWindows\Setup.exe /unattend:E:\Configset\non_oa3.0\AutoUnattend.xml
    </br></code>
    <p>Drücken Sie D für Verzeichnis, wenn Sie dazu aufgefordert werden.
    </p>
    </td>
    </tr>
    </table>
  
1.  Nachdem die Installationsdateien kopiert wurden, trennen **USB-A**.

2.  Trennen Sie die **USB-B** unmittelbar nach dem Neustart des Computers.

Wenn Sie die AutoUnattend verwenden, das System im Überwachungsmodus automatisch startet und das Systemvorbereitungstool (Sysprep) angezeigt wird. Wenn das Gerät die Sprachen startet oder die Hi es stattdessen Bildschirm, drücken Sie STRG + UMSCHALT + F3 Überwachungsmodus eingeben. Das Gerät neu gestartet wird, auf dem Desktop und das Systemvorbereitungstool (Sysprep) angezeigt wird. Jetzt ignorieren Sie Sysprep.

Hinweis: Viele Windows-Features, einschließlich im Startmenü und im Menü Einstellungen funktionieren nicht in dieser Umgebung.

#### <a name="apps-and-store-opportunities"></a>Apps und Store Verkaufschancen

Bis 10 für Windows und Windows Store müssen Sie enorme Chancen für Marke und Gerät Differenzierung, Umsatz Erstellung und Kundenzugriffs.

Windows Store-apps sind in der Mitte der Windows-10-Erfahrung. Sie werden universellen Windows-apps, damit Sie apps für Desktops, Tablets oder Telefone, auf denen Windows 10 ausgeführt erstellen können. Als OEM können Sie eine ansprechenden Kundenzufriedenheit bereitstellen und Erhöhen der Marke können durch die Bereitstellung einer Reihe von Mehrwert-Software und-Diensten zusammen mit der qualitativ hochwertige Hardware, die Sie erstellen.

Wichtig: Folgenden Schlüssel muss im Überwachungsmodus festgelegt werden. Wenn Sie im Abschnitt [Installieren Windows](#install-windows) abgeschlossen haben, sollten Sie im Überwachungsmodus aktiviert sein.

Ändern Sie die Einstellung der Registrierung und fügen Sie die OEM-ID. OEM Windows Store-Programm Teilnehmer, wenden Sie sich an <PartnerOps@microsoft.com> Abrufen Ihrer OEM-ID.

| **Element**  | **Speicherort in der Registrierung**                                                                   |
|-----------|--------------------------------------------------------------------------------------------|
| **OEMID** | HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Store OEMID (REG_SZ) |

***Regedit.exe***

1.  Führen Sie regedit.exe von einer Befehlszeile aus.

2.  Navigieren Sie zu HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Store.

3.  Mit der rechten Maustaste unter (Standard) &gt; klicken Sie auf **neu**.

4.  Klicken Sie auf **String-Wert**.

5.  Typ: 

        OEMID

6.  Doppelklicken Sie auf **OEMID** , und geben Sie den OEM-Namen in die **Wertdaten:** Text dar.

    Wichtig: Der Registrierungsschlüssel OEMID wird nicht automatisch während der PBR in Windows 10 wiederhergestellt. Weitere Informationen zum Wiederherstellen der OEMID Registrierungsschlüssel während PBR-Vorgang finden Sie unter [Prepare System für Wiederherstellungsszenarien drücken Sie die Schaltfläche Zurücksetzen](#prepare-system-for-recovery-push-button-reset-scenarios).

#### <a name="verify-customizations-in-audit-mode"></a>Vergewissern Sie sich im Überwachungsmodus Anpassungen

Herstellen einer Verbindung mit dem Computer mit dem Internet wird nicht empfohlen, während der Produktion Stufen. Es wird nicht empfohlen, zum Abrufen der Updates aus Windows Update im Überwachungsmodus aktiviert. Dies wird wahrscheinlich ein Fehler erzeugt, bei der Ausführung verallgemeinern + Syspreping auf dem Computer aus Überwachungsmodus aktiviert.

1.  Nach Abschluss der Installation meldet sich der Computer in Windows im Überwachungsmodus automatisch als Administrator.

2.  Überprüfen der Änderungen, die in die Antwortdatei (Siehe Herstellername, Rufnummer Support und anderen Anpassungen) angegeben wurden.

3.  Das Bild muss allgemeiner engl. werden, bevor Sie als Bild Fertigung verwendet werden; Aktivieren Sie das Kontrollkästchen **verallgemeinern** .

4.  Wählen Sie im Feld Systembereinigungsaktion **Systembereinigungsaktion Out-of-Box-Experience**.

5.  Wählen Sie im Optionenfeld beim Herunterfahren **Herunterfahren**aus.

    ![Verallgemeinern Sysprep](images/sysprep.png)

Wichtig: Das System muss auf verallgemeinern festgelegt und OOBE, um das Abbild zu bearbeiten sein. In den folgenden Abschnitten wird eine Datei im Überwachungsmodus auf dem System OOBE versiegelt wieder verwendet werden. Es bestehen bekannte Probleme beim Neuversiegeln im Überwachungsmodus in dieser Phase und es wird nicht empfohlen.

### <a name="capture-basic-image"></a>Erfassen Sie grundlegende Bild

1.  Verbinden "**USB-A**" und Starten des Referenzcomputers.

2.  Nachdem Windows PE gestartet wurde, eine Verbindung mit **USB-B**.

    Problembehandlung bei: Am Ende des vorherigen Abschnitt [Überprüfen Anpassungen im Überwachungsmodus aktiviert](#verify-customizations-in-audit-mode), Bezug auf den heruntergefahren wurde. Beim Einschalten Wenn das System zum Starten von interne HDD weiterhin, Windows wechselt specialize Durchlauf, und klicken Sie dann OOBE übergeben. **Um eine allgemeine Übersicht über und stabil Bild zu erfassen, die keines der Windows übergibt muss ausgefüllt werden. Um dieses Problem zu beheben, müssen wir das Bild erneut verallgemeinern. Drücken Sie auf dem Bildschirm OOBE ** &lt;STRG&gt;+&lt;UMSCHALT&gt;+&lt;F3&gt;. Der Neustart des Systems wird im Überwachungsmodus aktiviert. Im Überwachungsmodus aktiviert wechselt das System mithilfe der OOBE Herunterfahren und verallgemeinern Sysprep, wie im vorherigen Diagramm dargestellt. Nach dem Systemneustart, stellen Sie sicher zum Starten von **USB-A** zu einer Windows PE.

    Wenn das System weiterhin mit interne HDD startet, stellen Sie sicher, dass USB-Start anstelle von HDD Boot priorisiert ist. Dazu kann es sein, Neceesary eingeben klicken Sie im Menü BIOS-Referenz-Computer und die Priorität Startreihenfolge so anpassen, dass der USB-Schlüssel am oberen Rand der Liste ist.

1.  Windows-Partition Laufwerkbuchstaben zu identifizieren.

    -   An die **X:\windows\system32&gt; ** Prompt, Type ***Diskpart*** , und drücken Sie ** &lt;EINGABETASTE&gt; ** Diskpart zu starten.

    -   Bei der **\DISKPART&gt; ** Aufforderung geben Sie ***List Volume***.

    -   Suchen Sie die Lautstärke mit der Bezeichnung "Windows", unter der Spalte "Label".

    -   Beachten Sie, welche Buchstaben ist in der Spalte "Ltr" zugewiesen wurde (Beispiel: C). Dies ist der Laufwerkbuchstabe, die verwendet werden muss.

    -   Geben Sie zum Beenden der Diskpart ***zu beenden*** .

    ![Diskpart](images/diskpart-v10.png)

1.  Erfassen Sie das Abbild der Partition Windows **USB -**b. Dieser Vorgang kann mehrere Minuten.

    Hinweis: Es wird empfohlen Dism Vorgänge unter Verwendung von ein Cacheverzeichnis ausführen. Für dieses Beispiel erstellen wir eine Scratch Verzeichnis auf USB-B-TASTE für temporäre Dateien, die Laufwerkbuchstabe "E:" in den Beispielen zugewiesen wird. 

        MD e:\scratchdir

        Dism /Capture-Image /CaptureDir:C:\ /ImageFile:E:\Images\BasicImage.wim /Name:"myWinImage" /scratchdir:e:\scratchdir

### <a name="offline-servicing"></a>Offline – Wartung

Ändern Sie Ihren Bildern durch Hinzufügen und Entfernen von Sprachen und Treiber Pakete ein.

![Erstellen Sie ein bestimmtes Modell-Bild](images/create-model-specific-image.png)

#### <a name="mount-image"></a>Bereitstellen des Abbilds

Fügen Sie dem Referenzcomputer mit **USB-B** .

1.  Mount-Windows-Abbild (BasicImage.wim) in diesem Prozess extrahiert den Inhalt der Bilddatei an einem Speicherort, in denen die bereitgestellten Abbilds angezeigt und geändert werden können

        Md C:\mount\windows

        Dism /Mount-Wim /WimFile:E:\Images\BasicImage.wim /index:1 /MountDir:C:\mount\windows

    (E:\ ist, auf dem der Laufwerkbuchstabe des **USB-B**)

1.  Bereitstellen von Windows RE Bilddatei.

        Md c:\mount\winre

        Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\Recovery\winre.wim /index:1 /MountDir:C:\mount\winre

    Problembehandlung bei: Wenn winre.wim unter dem angegebenen Verzeichnis nicht sichtbar ist, verwenden Sie den folgenden Befehl die Datei sichtbar festlegen:

        attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim

Zu beheben: Wenn der Bereitstellung Fehler auftreten, stellen Sie sicher, dass die Windows-10-Version von DISM mit der Windows-ADK installiert ist. Stellen Sie sicher, dass Version verwendet wird und nicht mit einer älteren Version auf dem Referenzcomputer. Bereitstellen Sie Bilder zu geschützten Ordnern an, wie der Ordner User\Documents nicht. Wenn DISM Prozesse unterbrochen werden, können Sie vorübergehend vom Netzwerk trennen und Antivirusschutz deaktivieren.

#### <a name="add-drivers"></a>Hinzufügen von Treibern

1.  Hinzufügen von Treiberpakete (INF-Dateien) nacheinander. SampleDriver\driver.inf ist ein **Beispiel** -Treiber-Paket, das speziell für das Computermodell ist. (Geben Sie einen bestimmten Pfad). **Wenn vorhanden sind, dass mehrere Treiberpakete mit dem nächsten Schritt überspringen**.

2.  Mehrere Treiber können in einer Befehlszeile hinzugefügt werden, wenn ein Ordner anstelle einer INF-Datei angegeben wird. Um alle Treiber in einen Ordner und alle Unterordner installieren, verwenden Sie die **Option/recurse** .

        Dism /Image:C:\mount\windows /Add-Driver /Driver:c:\SampleDrivers /Recurse

        Dism /Add-Driver /Image:C:\mount\windows /Driver:"C:\SampleDriver\driver.inf"

1.  Überprüfen Sie den Inhalt von der %WINDIR%\Inf\ (C:\mount\windows\Windows\Inf\) Verzeichnis in bereitgestellten Windows-Abbild, um sicherzustellen, dass die INF-Dateien installiert wurden. Treiber hinzugefügt werden, auf dem Windows-Abbild heißen OEM\*. inf-Datei. Dadurch wird sichergestellt, eindeutigen Benennen von für neue Treiber auf dem Computer hinzugefügt werden. Beispielsweise sind die Dateien Treiber1.inf und Treiber2.inf umbenannte Oem0.inf und Oem1.inf.

2.  Stellen Sie sicher, dass der Treiber für beide Bilder installiert wurde.

        Dism /Image:C:\mount\windows /Get-Drivers
        

Wichtig: Wenn der Treiber das Installer-Paket enthält und verfügt nicht über eine INF-Datei, kann der Treiber im Überwachungsmodus installiert werden durch Doppelklicken auf das entsprechende Installer-Paket. Einige Treiber möglicherweise mit Sysprep-Tool nicht kompatibel; Sie werden entfernt, nachdem Sysprep verallgemeinern, auch wenn sie offline eingefügt wurde. 

In diesen Fällen müssen Sie PersistAllDeviceInstalls und DoNotCleanupNonPresentDevices (weiter unten) hinzufügen UnattendSysprep.xml zusätzlichen Parameter.

<table>
<tr>
<td>Bei Zugriff 3.0 Systeme:
</td>
<td>**USB-B**\AnswerFiles\\**OA3.0**\UnattendSysprep.xml
</td>
</tr>
<tr>
<td>Nicht bei Zugriff 3.0 - Systeme:
</td>
<td>**USB-B**\AnswerFiles\\**Non_OA3.0**\UnattendSysprep.xml
</td>
</tr>
</table>

##### <a name="persistalldeviceinstalls"></a>PersistAllDeviceInstalls

Um während der Installation Zeit zu sparen und die Out-of-Box-Experience für Endbenutzer zu beschleunigen, weisen Sie Windows Setup an, dass die Hardware des Referenzcomputers und den Zielcomputern identisch sind. Auf diese Weise verwaltet Windows Setup Treiberkonfigurationen während der abbildaufzeichnung und Bereitstellung.

Die folgende XML-Ausgabe gibt an, dass Treiber nicht während des Schritts verallgemeinern deinstalliert werden.

&lt;PersistAllDeviceInstalls&gt;true&lt;/PersistAllDeviceInstalls&gt;

Fügen Sie die Einstellung in der folgenden Tabelle zu \Answerfiles\OA3.0\UnattendSysprep.xml **USB-B**.

***X64/X86 Unterschied***

Mit X64 OEMs Windows 10 image, **USB-B**\Answerfiles\OA3.0\UnattendSysprep.xml die folgende Einstellung hinzufügen:

    <settings pass="generalize">
        <component name="Microsoft-Windows-PnpSysprep" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <PersistAllDeviceInstalls>true</PersistAllDeviceInstalls>
        </component>
    </settings>

Mithilfe von OEMs **X86 Windows 10 Bild**, **USB-B**\AnswerFiles\OA3.0\UnattendSysprep.xml folgende Einstellung hinzugefügt:

    <settings pass="generalize">
        <component name="Microsoft-Windows-PnpSysprep" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <PersistAllDeviceInstalls>true</PersistAllDeviceInstalls>
        </component>
    </settings>

##### <a name="donotcleanupnonpresentdevices"></a>DoNotCleanupNonPresentDevices

Die Einstellung **DoNotCleanUpNonPresentDevices** gibt an, ob auf dem Computer Plug & Play Informationen für Geräte, die nicht erkannt werden auf dem Zielcomputer während der nächsten Specialize bleiben sollen.

Wenn **PersistAllDeviceInstalls** und **DoNotCleanUpNonPresentDevices** auf **true**festgelegt werden, bleibt die Geräteinformationen jedoch auf dem Computer. Weitere Informationen finden Sie unter [DoNotCleanUpNonPresentDevices](https://msdn.microsoft.com/library/windows/hardware/dn915711.aspx).

Das folgende Diagramm beschreibt den Prozess, den Windows-Setup verwendet, um festzustellen, ob Plug & Play Informationen auf dem Computer verbleibt oder entfernt wird, oder entfernt und anschließend erneut initialisiert.

![DoNotCleanupNonPresentDevices](images/do-not-cleanup-nonpresent-devices.png)

Die folgende XML-Ausgabe gibt an, dass Treiber nicht während des Schritts verallgemeinern deinstalliert werden.

Mithilfe von Windows-10-Bild **X64** , OEMs hinzugefügt **USB-B**\AnswerFiles\OA3.0\UnattendSysprep.xml die folgende Einstellung:

    <settings pass="generalize">
        <component name="Microsoft-Windows-PnpSysprep" processorArchitecture="amd64"
        publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" 
        xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <DoNotCleanUpNonPresentDevices>true</DoNotCleanUpNonPresentDevices >
        </component>
    </settings>

Mithilfe von Windows 10 Bild **X86** , OEMs hinzugefügt **USB-B**\AnswerFiles\OA3.0\UnattendSysprep.xml die folgende Einstellung:

    <settings pass="generalize">
        <component name="Microsoft-Windows-PnpSysprep" processorArchitecture="x86" 
        publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" 
        xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <DoNotCleanUpNonPresentDevices>true</DoNotCleanUpNonPresentDevices >
        </component>
    </settings>

#### <a name="adding-lps-lips-fods-gdrs"></a>Hinzufügen von LPs / LIPs / FoDs / GDRs

In der folgenden Tabelle werden die Language Pack-Komponenten und Abhängigkeiten. Weitere Informationen finden Sie unter [Language Packs](language-packs-and-windows-deployment.md) und [Features bei Bedarf (Departements)](features-on-demand-v2--capabilities.md).


<table border="1" cellpadding="0">
    <tbody>
        <tr>
            <td>
                <p align="center">
                    <strong>Komponente</strong>
                </p>
            </td>
            <td>
                <p align="center">
                    <strong>Beispiel-Dateiname</strong>
                </p>
            </td>
            <td>
                <p align="center">
                    <strong>Abhängigkeiten</strong>
                </p>
            </td>
            <td>
                <p align="center">
                    <strong>Beschreibung</strong>
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Sprachpaket </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-Client-Language-Pack_x64_es-es.cab</code>
                </p>
            </td>
            <td>
                <p>
Keine </p>
            </td>
            <td>
                <p>
Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Benutzeroberflächen-Sprachpaket </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es.cab</code>
                </p>
            </td>
            <td>
                <p>
Erfordert ein bestimmtes vollständig lokalisierte oder teilweise lokalisierte Language Pack. Beispiel: ca-ES erfordert es-ES.
                </p>
            </td>
            <td>
                <p>
Benutzeroberflächentext, einschließlich grundlegende Cortana Funktionen.
                </p>
                <p>
Nicht alle Sprachressourcen für die Benutzeroberfläche sind in der LIP enthalten. Benutzeroberflächen-Sprachpaketen erfordern mindestens ein Sprachpaket (oder übergeordnete Sprache). Ein übergeordnetes Language Pack bietet Unterstützung für ein SPRACHPAKET. Die Teile der Benutzeroberfläche an, die nicht in der LIP-Sprache übersetzt werden werden in der übergeordneten Sprache angezeigt. In Ländern oder Regionen, in dem zwei Sprachen häufig verwendet werden, können Sie eine höhere benutzerfreundlichkeit bereitstellen, indem ein LIP über ein Language Pack anwenden.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Standard </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package</code>
                </p>
            </td>
            <td>
                <p>
Keine </p>
            </td>
            <td>
                <p>
Rechtschreibprüfung, Textvorhersage, Wortumbruch und Silbentrennung Wenn für die Sprache zur Verfügung.
                </p>
                <p>
Sie müssen diese Komponente hinzufügen, bevor Sie die folgenden Komponenten hinzufügen.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Schriftarten </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package</code>
                </p>
            </td>
            <td>
                <p>
Keine </p>
            </td>
            <td>
                <p>
Schriftarten.
                </p>
                <p>
Erforderlich für einige Regionen zum Rendern von Text, der in Dokumenten angezeigt wird. Beispielsweise ten-ten erfordert das Schriftart Thai Pack. 
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Optische zeichenerkennung </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package</code>
                </p>
            </td>
            <td>
                <p>
Standard </p>
            </td>
            <td>
                <p>
Erkennt und Text in einem Bild ausgegeben.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Handschrifterkennung </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package</code>
                </p>
            </td>
            <td>
                <p>
Standard </p>
            </td>
            <td>
                <p>
Ermöglicht handschrifterkennung für Geräte mit Input Stift.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Sprachsynthese </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package</code>
                </p>
            </td>
            <td>
                <p>
Standard </p>
            </td>
            <td>
                <p>
Text zu Sprachein-und-Ausgabe, von Cortana und die Sprachausgabe verwendet werden können.
                </p>
            </td>
        </tr>
        <tr>
            <td>
                <p>
Spracherkennung </p>
            </td>
            <td>
                <p>
                    <code>Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package</code>
                </p>
            </td>
            <td>
                <p>
Grundlegende, Sprachausgabe Spracherkennung </p>
            </td>
            <td>
                <p>
Erkennt VoIP Eingabe, von Cortana und Windows-Spracherkennung verwendet werden.
                </p>
            </td>
        </tr>
    </tbody>
</table>


Verwenden Sie immer Language Packs und Features-On-Demand (Departements)-Pakete, die mit der Sprache des Windows-Bilds Plattform übereinstimmen.

Features bei Bedarf (FODs) sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Wenn ein Benutzer ein neues Feature benötigt, können sie das Feature Packs von Windows Update anfordern. OEMs können diese Features aktivieren auf ihren Geräten Out-of-the-Box vorinstallieren.

Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung. Einige dieser Features sind erforderlich, um vollständige Cortana-Funktionen zu aktivieren.

Abrufen der Win 10 32 64 mehrsprachige OPK LangPackAll und der Win 10 32-BIT-X64 mehrsprachige OPK Feat bei Bedarf vom [DOC-Center](https://www.microsoftoem.com).

Hinweis: Sie müssen das Microsoft Media-Tool aus [SOC Ressourcen](https://moo.microsoftoem.com/okdnet/SOCResources.aspx) verwenden, ein einbindbar Bild für den Erfolg 10 die Ordnerstruktur DDP zusammengeführt 32-BIT-X64 mehrsprachige OPK Feat bei Bedarf aus DOC Center.

1.  Kopieren Sie die X86 und X64 Language Pack CAB-Dateien in E:\Languagepacks\.

1.  Kopieren Sie teilweise Sprachpakete **USB -**b.

3.  Markieren Sie alle de-de-Features für die Anforderung-Dateien und zum E:\LanguageFeaturePacks\ kopieren.

    ![Markieren von Sprachpaketen](images/highlight-language-packs.png)

    Dabei ist E: Laufwerkbuchstabe des **USB-B**

Wichtig: Installieren Sie ein Language Pack nicht nach einer Aktualisierung. Wenn ein Update (Hotfix, allgemein verfügbare Version [GDR] oder [SP] pack Service), die Language-abhängigen Ressourcen enthält installiert ist, bevor ein Language Pack installiert ist, wird die Liste der sprachspezifischen Änderungen, die in dem Update enthalten sind werden nicht übernommen das Update neu installiert werden müssen. Installieren von Language Packs immer vor der Installation von Updates.

Fügen Sie das Windows-Abbild Sprachen und Features On Demand.

Pakete mit Abhängigkeiten Vergewissern Sie sich, dass Sie die Pakete in Reihenfolge installieren. Beispielsweise um Cortana aktivieren möchten, installieren: das Language pack CAB-Datei, und klicken Sie dann –**grundlegende**, klicken Sie dann –**TextToSpeech**und dann –**Sprache**, in der angegebenen Reihenfolge. Wenn Sie nicht die Abhängigkeiten sicher sind, ist es OK, um alle im selben Ordner ablegen, und fügen sie alle im gleichen DISM/Add-Package-Befehl verwenden, wie in den Beispielen in den folgenden Tabellen (wobei E: ist das Laufwerk, auf dem Sprachpaket vorhanden ist) dargestellt. Beginnend mit Windows 10 Version 1607, umfassen Language Pack-Dateinamen der Windows-Edition, Plattformarchitektur und Gebietsschema. Die Features auf Anforderung (Departements) Pakete sollten von Medien befinden, die die Plattformarchitektur des Geräts entspricht. Verwenden Sie beispielsweise Departements Pakete aus X64 Medien für einen X64-basierten Computer.  

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath:"E:\LanguagePacks\Microsoft-Windows-Client-Language-Pack_x64_de-de.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Basic-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-OCR-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Handwriting-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Speech-de-de-Package.cab" /packagepath:"e:\LanguageFeaturePacks\x64\Microsoft-Windows-RetailDemo-OfflineContent-Content-de-de-Package.cab"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath:"E:\LanguagePacks\Microsoft-Windows-Client-Language-Pack_x86_de-de.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Basic-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-OCR-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Handwriting-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-TextToSpeech-de-de-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Speech-de-de-Package.cab" /packagepath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-RetailDemo-OfflineContent-Content-de-de-Package.cab"

Stellen Sie sicher, dass das Paket, das Windows-Abbild installiert wurde:

    Dism /Get-Packages /Image:C:\mount\windows

##### <a name="optional-add-a-language-with-additional-fonts"></a>[Optional] Fügen Sie eine Sprache hinzu, indem Sie zusätzliche Schriftarten

Im Rahmen der Language Pack erneut einbeziehen für Windows 10 wurden einige Sprachen mit Schriftarten in ihrer eigenen Sprache CAB-Dateien nicht berücksichtigt. In diesem Abschnitt wird das Bild mit der Sprache Schriftart Cab zusätzlich zu anderen Features Sprachpakete ja-JP Sprache hinzugefügt.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath:"E:\LanguagePacks\Microsoft-Windows-Client-Language-Pack_x64_ja-jp.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Basic-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-OCR-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Handwriting-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Speech-ja-jp-Package.cab" **/PackagePath:"E:\LanguageFeaturePacks\x64\Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package.cab"** /packagepath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-RetailDemo-OfflineContent-Content-ja-jp-Package.cab

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath:"E:\LanguagePacks\Microsoft-Windows-Client-Language-Pack_x86_ja-jp.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Basic-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-OCR-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Handwriting-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-TextToSpeech-ja-jp-Package.cab" /PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Speech-ja-jp-Package.cab" **/PackagePath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package.cab"** /packagepath:"E:\LanguageFeaturePacks\x86\Microsoft-Windows-RetailDemo-OfflineContent-Content-ja-jp-Package.cab"

#### <a name="add-languages-to-windows-re"></a>Hinzufügen von Sprachen zu Windows RE

Wenn Sie Windows Sprachen hinzufügen, fügen sie Sie Windows RE eine konsistente Sprache Erfahrung in Wiederherstellungsszenarien sicherzustellen.

Problembehandlung bei: Wenn winre.wim im angegebenen Verzeichnis nicht sichtbar ist, verwenden Sie den folgenden Befehl an um die Datei sichtbar zu machen:

    attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\lp.cab"    
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Rejuv_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-EnhancedStorage_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Scripting_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-SecureStartup_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-SRT_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-WDS-Tools_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-WMI_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-StorageWMI_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-HTA_de-de.cab"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\lp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-Rejuv_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-EnhancedStorage_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-Scripting_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-SecureStartup_de-de.cab"   
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-SRT_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-WDS-Tools_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-WMI_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-StorageWMI_de-de.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\de-de\WinPE-HTA_de-de.cab"

1.  Überprüfen Sie, ob die Sprachpakete Teil des Bilds sind:

        Dism /Get-Packages /Image:"C:\mount\winre"

    Dabei ist C der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste das Paket enthält. Beispiel:

        Package Identity : Microsoft-Windows-WinPE-Rejuv_de-de ... de-de~10.0.9926.0 State : Installed

##### <a name="optional-add-ja-jp-language-packs"></a>[Optional] Hinzufügen von Sprachpaketen ja-jp

Führen Sie in diesem Abschnitt nur, wenn Sie Sprachpakete ja-jp aus den optionalen Abschnitt [Hinzufügen einer Sprache in zusätzliche Schriftarten](#add-a-language-with-additional-fonts)hinzugefügt.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\lp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-Rejuv_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-EnhancedStorage_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-Scripting_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-SecureStartup_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-SRT_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-WDS-Tools_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-WMI_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-StorageWMI_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\ja-jp\WinPE-HTA_ja-jp.cab"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\lp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-Rejuv_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-EnhancedStorage_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-Scripting_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-SecureStartup_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-SRT_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-WDS-Tools_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-WMI_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-StorageWMI_ja-jp.cab"
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\x86\WinPE_OCs\ja-jp\WinPE-HTA_ja-jp.cab"

#### <a name="optional-remove-english-language-to-make-a-single-language-image"></a>[Optional] Entfernen Sie englische damit wird eine einzelne Sprache Bild

In Windows 10 wird Microsoft nur En-US-Versionen verfügbar machen. Damit das Bild ein einzelnes Bilds wird nach der Installation von de-DE im vorherigen Abschnitt, können Sie En-US aus diesem Abbild nur de-DE leicht entfernen.

OEMs müssen alle En-US Language Packs vom System entfernt. Im folgende Beispiel wird vor dem installierte Sprachen aus Windows 10 Professional entfernt.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /image:"c:\mount\windows" /remove-package /packagename:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename: Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384 /packagename:Microsoft-Windows-Prerelease-Client-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:Microsoft-Windows-RetailDemo-OfflineContent-Content-en-us-Package~31bf3856ad364e35~amd64~~10.0.10240.16384

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /image:"c:\mount\windows" /remove-package /packagename:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384 /packagename:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384 /packagename:Microsoft-Windows-Prerelease-Client-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:Microsoft-Windows-RetailDemo-OfflineContent-Content-en-us-Package~31bf3856ad364e35~x86~~10.0.10240.16384

Problembehandlung bei: Wenn ein Fehler auftritt, während ein Paket wie entfernen:

    Error: 0x800f0825
    Package Microsoft-Windows-LanguageFeatures-Basic-en-us-Package may have failed due to pending updates to servicing components in the image. Try the command again. The command completed with errors. For more information, refer to the log file. The DISM log file can be found at C:\windows\Logs\DISM\dism.log. 
    
Führen Sie dism.exe Remove-Paket erneut auf nur das Paket Fehler aufgetreten ist.

#### <a name="optional-remove-additional-languages-from-winre"></a>[Optional] Entfernen von zusätzlichen Sprachen in WinRE

Wenn Sie alle Sprachen entfernt haben, müssen sie auch aus WinRE entfernt werden.

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /image:"c:\mount\winre" /remove-package /packagename:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384 /packagename:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10240.16384

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /image:"c:\mount\winre" /remove-package /packagename:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-EnhancedStorage-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-HTA-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-Rejuv-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-Scripting-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-SecureStartup-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-SRT-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-StorageWMI-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-WDS-Tools-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384 /packagename:WinPE-WMI-Package~31bf3856ad364e35~x86~en-US~10.0.10240.16384

#### <a name="verify-language-components-are-part-of-the-image"></a>Überprüfen Sie, ob Sprachkomponenten Teil des Bilds werden

Verwenden Sie Dism, um sicherzustellen, dass Sprachkomponenten Teil des Bilds sind.

    Dism /Get-Capabilities /Image:"C:\mount\windows"

#### <a name="setting-language-regional-settings"></a>Festlegen der Sprache regionale Einstellungen

1.  Verwenden Sie Dism, um die Standardsprache des Bilds festzulegen:

        Dism /Image:C:\mount\windows /Set-AllIntl:de-DE

        Dism /Image:C:\mount\winre /Set-AllIntl:de-DE

1.  Überprüfen Sie Ihre Änderungen an:

        Dism /Image:C:\mount\windows /Get-Intl

1.  Legen Sie die Zeitzone für den Bereich der Standardsprache angewendet:

        Dism /Image:C:\mount\windows /set-timezone:"W. Europe Standard Time"

#### <a name="add-update-packages-kb-packages-to-the-image"></a>Hinzufügen von Updatepakete (KB Pakete) auf das Bild

Verwenden Sie Dism, um die neuesten GDR und alle erforderlichen KB-Artikel anzuwenden. Überprüfen Sie auf [SOC (Software Order Center)](https://www.microsoftoem.com) die neueste Version des Pakets "Windows Desktop OPK ergänzende". In diesem Handbuch wird beispielsweise die neuesten GDR 2015.11 d KB3118754 verwenden. 

**Wichtig: Installieren Sie ein Language Pack nicht nach einer Aktualisierung. Wenn ein Update (beispielsweise ein Hotfix, oder eine allgemein verfügbare Version [GDR] oder ein Servicepack [SP]), die Language-abhängigen Ressourcen enthält installiert ist, bevor ein Language Pack installiert ist, die sprachspezifische Änderungen, die in dem Update enthalten sind, werden nicht übernommen, und das Update neu installiert werden müssen. Installieren von Language Packs immer vor der Installation von Updates.**

Im folgenden Beispiel wird veranschaulicht, wie KB-Artikel aus dem Download OPK aus SOC. extrahieren

1.  Kopieren Sie beide Ordner Architektur für KB3081452 in \Updates **USB-B**.

    Navigieren Sie zu X20 53652 Windows Desktop OPK Supp Updates Sep15\Software - DVD\X20 53672 SW DVD5 Windows Supp Sep15 Datenträger 1 OEM\x20-53672.img, und doppelklicken Sie auf. Suchen Sie im Ordner 3081452 wie in der folgenden Abbildung dargestellt.
    
    ![3081452 aktualisieren](images/update-3081452.png)
    
1.  Kopieren Sie beide Ordner Architektur für KB3097617 in \Updates **USB-B**.

    Navigieren Sie zu X20 86795 Windows Desktop OPK Supp Updates Oct15\Software - DVD\X20 86816 SW DVD5 Windows Supp Oct15 OEM\x20-86816.img, und doppelklicken Sie auf. Suchen Sie im Ordner 3097617 wie in der folgenden Abbildung dargestellt.

    ![Aktualisieren 3097617](images/update-3097617.png)

##### <a name="apply-gdr-201511-d-kb3118754"></a>GDR 2015.11 d KB3118754 anwenden

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /Add-Package /Image:C:\mount\windows /PackagePath:"E:\updates\KB3118754\x64\NEU\Windows10.0-KB3118754-x64.msu"      

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /Add-Package /Image:C:\mount\windows /PackagePath:"E:\updates\KB3118754\x86\NEU\Windows10.0-KB3118754-x86.msu"

Hinweis: Jedes Paket wird in der Regel einer neuen KB, und nimmt Revisionsnummer Build von Windows auf dem Gerät. Die Revisionsnummer des Windows für ein Gerät finden Sie in den folgenden Registrierungsschlüssel: 

MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\UBR

#### <a name="add-update-packages-to-winre"></a>Update-Paketen in WinRE hinzufügen

Wichtig: KB3118754 muss auch auf ein bekanntes Problem beheben WinRE.wim angewendet werden: Fehler bei der Wiederherstellung während zurücksetzen/aktualisieren, wenn ein Scanstate-Paket (USMT.ppkg) eine Anwendung enthält, die einen Pfad mit einem führenden Leerzeichen hat. Beispiel: c: \programme\ Contoso\RunMe.exe.

GDR 2015.11 d KB3118754 anwenden

Wenn Sie ein Bild **X64** Windows 10 verwenden:

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"E:\updates\KB3118754\x64\NEU\Windows10.0-KB3118754-x64.msu"

Wenn Sie ein Bild **X86** Windows 10 verwenden:

    Dism /Add-Package /Image:C:\mount\windows /PackagePath:"E:\updates\KB3118754\x86\NEU\Windows10.0-KB3118754-x86.msu"

#### <a name="reinstall-inbox-apps"></a>Installieren von apps Posteingang

Wenn Sie Sprachpakete hinzufügen, sollten Sie den Posteingang apps neu installieren, durch die jeweilige app entfernen und dann mithilfe von DISM erneut installiert. Das folgende Verfahren zeigt, wie die Posteingang Einstieg in die app installieren, jedoch die Schritte funktionieren für alle apps durch Ersetzen durch das entsprechende Paket.

Überprüfen Sie auf [SOC (Software Order Center)](https://www.microsoftoem.com) die neueste Version des Pakets "Windows Desktop OPK ergänzende".

*Hinweis:* ist nicht mehr erforderlich, die Posteingang Einstieg in die app zu entfernen. Wenn Sie versuchen, mithilfe von DISM entfernen, wird möglicherweise der Befehl.

1.  Maustaste auf jeden Ordner, und extrahieren Sie alle in e:\apps.

    ![Extrahieren Sie die Dateien der Anwendung](images/extract-app-files.png)

Installieren der apps

**Hinweis: Es sind 27-Box-apps in das Bild neu installieren. Verwenden Sie der Liste unten, um die apps auf das Bild erneut anwenden zu identifizieren. Wenn ein ergänzendes Windows 10-Update nicht alle 27 enthält apps, die verbleibenden apps aus dem vorherigen Windows 10 zusätzliche OPK installieren.**

[Desktop_2015.1071.40.0_Microsoft.Camera.appxbundle_Windows10_PreinstallKit]

[Desktop_Builder3D_10.9.50.0_x86_x64.appxbundle_Windows10_PreinstallKit]

[Desktop_Mobile_x86_ARM_1.10.26007.0_MicrosoftMessaging.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_10.1510.9010.0_WindowsPhone.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_15.1001.16470.0_WindowsPhotos.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_3.6.13281.0_Music_Desktop_Production.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_3.6.13571.0_Video_Desktop_Production.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_ARM_10.0.2840.0_MicrosoftPeople.appxbundle_Windows10_PreinstallKit]

[Desktop_x86_x64_ARM_10.1510.13110.0_SoundRecorder.appxbundle_Windows10_PreinstallKit]

[GetSkype_3.2.1.0_x86_bundle.appxupload_Windows10_PreinstallKit]

[Microsoft.ConnectivityStore_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit]

[Microsoft.WindowsStore_8wekyb3d8bbwe_2015.1013.14.0.1509.Universal.appxbundle_Windows10_PreinstallKit]

[Mobile_Desktop_x86_x64_ARM_1.10.23004.0_CommsPhone.appxbundle_Windows10_PreinstallKit]

[MoneyApp_4.6.169.0_x86.appxbundle_Windows10_PreinstallKit]

[News_4.6.169.0_x86.appxbundle_Windows10_PreinstallKit]

[PC_storeandTH2_6314.2375.officehubim.appxbundle_Windows10_PreinstallKit]

[PC_Sway_6216.2025.storyim.appxbundle_Windows10_PreinstallKit]

[PC_TH2RC_store.16.0.6131.1005.onenoteim.appxbundle_Windows10_PreinstallKit]

[PC_TH2_store.16.0.6308.4227.Sc6131.1009.outlookim.appxbundle_Windows10_PreinstallKit]

[Solitaire_3.4.9241.0_x86_x64.appxbundle_Windows10_PreinstallKit]

[Universal_Maps.Windows_4.1509.50911.0_ARM_x64_x86.appxbundle_Windows10_PreinstallKit]

[Universal_Sports_4.6.169.0_x86.appxbundle_Windows10_PreinstallKit]

[Universal_Weather_4.6.169.0_x86.appxbundle_Windows10_PreinstallKit]

[Universal_x86_x64_ARM_10.1510.13020_WindowsCalculator.appxbundle_Windows10_PreinstallKit]

[Universal_x86_x64_ARM_10.1510.14020.0_WindowsAlarms.appxbundle_Windows10_PreinstallKit]

[Universal_x86_x64_ARM_2.4.13.0_GetStarted.appxbundle_Windows10_PreinstallKit]

[XboxApp_9.9.30030.0]

Wichtig: Die Appx fasst die übereinstimmenden Abhängigkeit Packages installieren müssen oder apps werden nicht nach OOBE funktioniert. Die richtige Abhängigkeit Pakete gemäß der \*.provxml-Dateien in den Ordnern app. Das folgende Beispiel weist die richtige Abhängigkeit-Pakete für die jeweilige app:

    dism /image:"c:\mount\windows" /Add-ProvisionedAppxPackage /PackagePath:"E:\apps\Universal_Microsoft.GetStarted_2.2.7.0_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit\aed1db6c4a954880b3ff43b8e4d1a76d.appxbundle" /DependencyPackagePath:"E:\Apps\Universal_Microsoft.GetStarted_2.2.7.0_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit\Microsoft.NET.Native.Framework.1.0_1.0.22929.0_ARM__8wekyb3d8bbwe.appx" /DependencyPackagePath:"E:\Apps\Universal_Microsoft.GetStarted_2.2.7.0_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit\Microsoft.NET.Native.Runtime.1.0_1.0.22929.0_ARM__8wekyb3d8bbwe.appx" /DependencyPackagePath:"E:\Apps\Universal_Microsoft.GetStarted_2.2.7.0_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_ARM__8wekyb3d8bbwe.appx" /licensepath:"E:\apps\Universal_Microsoft.GetStarted_2.2.7.0_8wekyb3d8bbwe.appxbundle_Windows10_PreinstallKit\aed1db6c4a954880b3ff43b8e4d1a76d_License1.xml"


#### <a name="adding-windows-universal-office-mobile"></a>Hinzufügen von Windows universelle Office Mobile

Abrufen von X20 88613 Office Mobile mehrsprachige v1. 2 OPK (Dies ist das neueste Update, wenn dieses Handbuchs veröffentlicht wird. Überprüfen Sie auf [www.microsoftoem.com](http://www.microsoftoem.com) > SOC (Software Order Center), wenn eine neuere Version des Updates beendet Pakete.

Weitere Einzelheiten finden Sie unter [Office Mobile Kommunikation](https://myoem.microsoft.com/oem/myoem/en/product/office/Pages/COMM-OfficeUnvrslAppsOPKRlsTmng.aspx) .

Hinweis: Microsoft Office-nur einem Bild Installation wird in den Abschnitt [geladen Microsoft Office nur einem Bild v15.4](#preload-microsoft-office-single-image-v15.4) bei Geräten mit Bildschirmgröße oben 10.1" behandelt.

Vor der Installation von Office einzelnen Abbilds (mit oder mit Out-unbefristete oder Abonnementlizenz) oder Office Mobile.  Office Mobile auf Geräten mit Bildschirmgröße 10.1" und unter verwendet werden muss, und nur einem Bild von Office muss auf Geräten mit Bildschirm größer als 10.1" verwendet werden. Für Geräte, die ein einzelnes fixed-Speicher-Laufwerk mit weniger als 32 GB haben, können OEMs Office Mobile, unabhängig von der Bildschirmgröße vorinstallieren. OEMs müssen nur ein Office-Bild auf das System gleichzeitig verbunden sein.

1.  Extrahieren Sie alle Ordner in E:\Universal_Office

    ![Extrahieren von Office](images/extract-office.png)

        dism /image:"c:\mount\windows" /add-provisionedappxpackage /packagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c.appxbundle" /dependencypackagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c_License1.xml"

        dism /image:"c:\mount\windows" /add-provisionedappxpackage /packagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056.appxbundle" /dependencypackagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056_License1.xml"

        dism /image:"c:\mount\windows" /add-provisionedappxpackage /packagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592.appxbundle" /dependencypackagepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592_License1.xml"

#### <a name="modify-the-start-layout"></a>Ändern des Layouts Start

Das Start Kachel Layout in Windows 10 bietet OEMs die Möglichkeit, auf das Standardlayout Start Einbeziehung Weblinks, sekundäre Kacheln, Windows-desktopanwendungen und universellen Windows-apps Kacheln angefügt werden soll. In diesem Layout können OEMs es auf mehrere Bereiche oder Märkte anwendbar tätigen, ohne einen Großteil der Arbeit zu duplizieren. Darüber hinaus können OEMs hinzufügen, bis zu drei Standard-apps in den Abschnitt häufig verwendeten apps im Bereich, der System-gesteuerte Listen an den Benutzer, einschließlich wichtiger oder auf die häufig zugegriffen Systemspeicherorte übermittelt und kürzlich installierten apps.

Nutzen Sie alle neuen Features und die am häufigsten robuste und vollständige Start Anpassung für Windows 10, sollten Sie eine Datei LayoutModification.xml erstellen. Diese Datei gibt an, wie die OEM-Kacheln in Start angeordnet werden. Weitere Informationen über das Layout für die neue Start anpassen finden Sie unter [Anpassen der Windows-10-Startseite](https://msdn.microsoft.com/library/windows/hardware/Mt170651.aspx).

1.  Erstellen Sie Layoutmodification.xml.

    Hinweis: Es wird empfohlen, mit dem Beispiel auf USB-B\StartLayout\layoutModification.xml zu starten, wie sie die Beispiele in diesem Dokument (nur Beispiel) entspricht.

    Das Beispiel LayoutModification.xml zeigt zwei Gruppen namens "Fabrikam Group 1" und "Gruppe" Fabrikam "2", die Kacheln enthalten, die angewendet wird, wenn das Gerät Land/Region übereinstimmt, was in Region angegeben wird (Deutschland und USA sind in diesem Fall die Regionen). Jede Gruppe enthält drei Kacheln und die verschiedenen Elemente müssen Sie je nach die Kachel verwenden, die Sie an Start anheften möchten.

    Behalten Sie beim Erstellen der Datei LayoutModification.xml Folgendes beachten:

    -   Wenn Sie eine Windows-desktop-Anwendung mit dem Tag **Start: DesktopApplicationTile** festhalten und die Anwendung Anwendung Benutzer Modell-ID nicht kennen, müssen Sie zum Erstellen einer LNK-Datei in ein legacy-Menü Startmenüverzeichnis vor dem ersten Start.

    -   Wenn Sie das **Start: DesktopApplicationTile** Tag verwenden, um eine Vorversion URL Verknüpfung mit Start anheften, müssen Sie eine URL-Datei erstellen und fügen Sie diese Datei in ein legacy-Menü Startmenüverzeichnis vor dem ersten Start.

    Für diese Szenarien können Sie die folgenden Verzeichnissen an um die URL oder lnk-Dateien zu platzieren:

    -   %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    -   %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

1.  Speichern Sie die Datei LayoutModification.xml.

2.  Das Windows-Abbild Ihrer LayoutModification.xml-Datei hinzugefügt. Sie müssen die Datei in die folgenden Position vor dem ersten Start zu platzieren. Wenn die Datei vorhanden ist, sollten Sie die LayoutModification.XML ersetzen, die bereits im Bild enthalten ist.

        Copy E:\StartLayout\layoutmodification.xml c:\mount\windows\users\default\AppData\Local\Microsoft\Windows\Shell\

    Dabei ist E: der Laufwerkbuchstabe des **USB-B**.

1.  Wenn Sie Kacheln angeheftet haben, die URL oder .lnk Dateien erfordern, fügen Sie den folgenden Verzeichnissen für legacy-Menü Start die Dateien hinzu:

    1.  %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    2.  %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

            Copy e:\StartLayout\Bing.url "C:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs\"

            copy e:\StartLayout\Paint.lnk "c:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Bing.url "c:\mount\windows\users\All Users\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Paint.lnk "C:\Mount\Windows\Users\All Users\Microsoft\Windows\Start Menu\Programs"

Hinweis: Wenn Sie keine LayoutModification.xml-Datei erstellen und Sie auch weiterhin mithilfe die Einstellungen für die unbeaufsichtigte Installation zu starten, das Betriebssystem verwendet die Antwortdatei für die unbeaufsichtigte Installation und die ersten 12 SquareTiles oder DesktoporSquareTiles Einstellungen in der Datei für die unbeaufsichtigte Installation angegeben werden. Das System platziert diese Kacheln automatisch in die neu erstellte Gruppen dann am Ende des Start – die ersten sechs Kacheln werden in der ersten OEM-Gruppe und der zweite Satz von sechs Kacheln in der zweiten OEM-Gruppe abgelegt sind. Wenn OEMName in der Datei für die unbeaufsichtigte Installation angegeben ist, wird der Wert für dieses Element nennen Sie die OEM-Gruppen, die erstellt wird.

##### <a name="add-an-oem-specific-license"></a>Hinzufügen einer OEM-spezifische-Lizenzvertrags

1.  OEM kann auf dem Bildschirm Lizenzbedingungen ersten Oberfläche die OEM-Lizenzbedingungen hinzufügen. 

    Hinweis: Wenn die Lizenzbedingungen enthalten sind, muss der OEM eine Version, die Lizenzbedingungen in allen Sprachen enthalten, die auf dem PC vorinstalliert ist. Ein Lizenz Begriff Text muss ein. **RTF** -Datei als gespeichert. **RTF** -Format.

1.  Erstellen Sie die Ordner im folgenden Verzeichnis: 

    C:\mount\windows\Windows\System32\oobe\info\default\

2.  Nennen Sie jeden Ordner C:\mount\windows\Windows\System32\oobe\info\default\ im Verzeichnis als **Decimal Sprach-ID** die Sprache entspricht. Wiederholen Sie diesen Schritt für jedes Sprachpaket, das Windows-Abbild hinzugefügt wurde.

    Die vollständige Liste der Sprache Dezimal entsprechenden Sprachen-IDs finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).

    Beispielsweise wenn En-uns und de-de Sprachpakete werden hinzugefügt, auf dem Windows-Abbild fügen einen Ordner namens "1033" (de-de darstellt-uns Sprache) unter C:\mount\windows\Windows\System32\oobe\info\default\. fügen Sie einen Ordner namens "1031" (Ereignisobjekten de-de Language) unter demselben Verzeichnis.

        MD c:\mount\windows\windows\system32\oobe\info\default\1033

        MD c:\mount\windows\windows\system32\oobe\info\default\1031

1.  Erstellen Sie die Lizenz Begriff Dokument für jede Sprache angegeben. Verschieben Sie jede Lizenz Begriff Dokument auf den entsprechenden Sprachordner.

    Verschieben der agreement.rtf **in Englisch** , beispielsweise die Datei:
    
    C:\mount\windows\Windows\System32\oobe\info\default\\**1033**\  
    
    Und die agreement.rtf Datei **in Deutsch** , verschieben: 
    
    C:\mount\windows\Windows\System32\oobe\info\default\\**1031**\ 

        Copy E:\resources\agreement.rtf c:\mount\windows\windows\system32\oobe\info\default\1033

1.  Erstellen Sie eine Datei **oobe.xml** , um den Dateipfad agreement.rtf anzugeben. In der folgenden Abbildung sehen Sie ein Beispiel oobe.xml sich auf dem Zielserver mit **USB-B**\ConfigSet\oobe.xml befindet.

    ![Beispiel OOBE](images/sample-oobe.png)

2.  Kopieren Sie **Datei oobe.xml** in jeder Sprachordner.

    Kopieren Sie beispielsweise oobe.xml in C:\mount\windows\Windows\System32\oobe\info\default\\**1033**\, in denen die agreement.rtf in Englisch gültig ist und C:\mount\windows\Windows\System32\oobe\info\default\\**1031**\ Verzeichnis, in dem die agreement.rtf auf Deutsch gültig ist.

        Copy e:\configset\oobe.xml c:\mount\windows\windows\system32\oobe\info\default\1033

1.  Schließlich muss jede Sprachordner eine Datei **oobe.xml** und eine agreement.rtf-Datei in die entsprechende Sprache enthalten.

    ![Vereinbarung und OOBE-Dateien](images/agreement-and-oobe-files.png)
    
    
#### <a name="modify-the-answer-file"></a>Ändern Sie die Antwortdatei

1.  OEM möglicherweise möchten Sie eine neue Antwortdatei erstellen. Die folgenden Beispielantwortdatei werden am häufigsten die erforderlichen Einstellungen für [Windows OEM Richtlinie Dokument (OPD)](http://click.email.microsoftemail.com/?qs=4e5762cd9d90bfec0d11dfa9bca1a9efd4924672c363af092f176011a77178f6f1caa72260b9766a)behandelt. Aus diesem Grund wird empfohlen, diese Antwortdatei verwenden:

    <table>
    <tr>
    <td>Bei Zugriff 3.0 Systeme:
    </td>
    <td><code>Copy /y E:\AnswerFiles\OA3.0\Unattend.xml C:\Mount\Windows\Windows\Panther</code><p>(wobei E:\ **USB-B**ist)</p>
    </td>
    </tr>
    <tr>
    <td>Nicht bei Zugriff 3.0 - Systeme:
    </td>
    <td><code>Copy /y E:\AnswerFiles\Non_OA3.0\Unattend.xml C:\Mount\Windows\Windows\Panther</code><p>(wobei E:\ **USB-B**ist)</p>
    </td>
    </tr>
    </table>

#### <a name="optimize-winre"></a>Optimieren der Leistung von WinRE

1.  Vergrößern Sie Onlinetreiberinstallation.

        Dism /image:"c:\mount\winre" /set-scratchspace:512

1.  Bereinigung, da nicht verwendete Dateien und Größe der winre.wim reduzieren.

        dism /image:"c:\mount\winre" /Cleanup-Image /StartComponentCleanup /Resetbase 

#### <a name="unmount-the-image"></a>Deaktivieren Sie das Bild

1.  Schließen Sie alle Programme, die Dateien aus dem Bild zugreifen können.

2.  Comit die Änderungen und heben Sie die Bereitstellung des Windows RE-Abbilds:

        Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit

    Dabei ist C der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

    Dieser Vorgang kann einige Minuten dauern.

1.  Stellen Sie eine Sicherungskopie des aktualisierten Windows RE-Abbilds:

    Problembehandlung: Wenn winre.wim im angegebenen Verzeichnis nicht angezeigt wird, verwenden Sie den folgenden Befehl an um die Datei sichtbar zu machen:

        attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim

        dism /export-image /sourceimagefile:c:\mount\windows\windows\system32\recovery\winre.wim /sourceindex:1 /DestinationImageFile:e:\images\winre_bak.wim

        Del c:\mount\windows\windows\system32\recovery\winre.wim

        Copy e:\images\winre_bak.wim c:\mount\windows\windows\system32\recovery\winre.wim

    Geben Sie bei Aufforderung "F" für die Datei.

1.  Überprüfen Sie die neue Größe des Windows RE-Abbilds.

        Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"

    Verwenden Sie die folgenden Partition Layout Größe Hinweise zum Bestimmen der Größe Ihrer Wiederherstellung Partition in Createartitions -&lt;Firmware&gt;TXT-Dateien. Die Menge an freiem Speicher ist, nachdem Sie in die ausgeblendete Partition winre.wim kopieren.

    Verweisen Sie bitte [Festplattenpartition Regeln](configure-uefigpt-based-hard-drive-partitions.md#DiskPartitionRules) für Weitere Informationen.

    -   Wenn die Partition kleiner als 500 MB ist, benötigen sie mindestens 50 MB freiem Speicherplatz.

    -   Ist die Partition 500 MB oder mehr hat, benötigen sie mindestens 320 MB freiem Speicherplatz.

    -   Wenn die Partition größer als 1 GB ist, wird empfohlen, dass er mindestens 1 GB freiem enthalten sollte.

            rem == Windows RE tools partition =============== 
            create partition primary size=500

    Optional: In diesem Abschnitt wird davon ausgegangen, dass Sie vielmehr winre.wim innerhalb install.wim auf die Sprachen und die Treiber synchron zu halten beibehalten würden. Wenn Sie etwas Zeit in der Fabrik speichern möchten, und wenn Sie diese Bilder OK separat verwalten, empfiehlt es sich pull winre.wim aus diesem Abbild und angewendet wird getrennt.

1.  Commit der Änderungen, und heben Sie die Bereitstellung des Windows-Abbilds:

        Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit

    Dabei ist C der Laufwerkbuchstabe des Laufwerks, das das Bild enthält.

Dieser Vorgang kann einige Minuten dauern.

### <a name="deploy-the-image-to-new-computers"></a>Bereitstellen des Abbilds auf neue Computer

In diesem Abschnitt wird das Gerät für die Bereitstellung von Windows PE starten, eine Partitionslayout erstellen und Bereitstellen des Abbilds vorbereitet.

#### <a name="boot-to-winpe"></a>Starten Sie Windows PE

1.  Suchen Sie auf dem Referenzcomputer die folgenden Dateien auf dem Zielserver mit /Deployment **USB-B**. [Erstellen von Meine USB-B](#creating-my-usb-b) zum Erstellen und Speichern von Dateien in den richtigen Pfaden finden Sie. Überspringen Sie diesen Schritt aus, wenn es zuvor ausgeführt wurde.

2.  Verbinden der **USB-A-** Laufwerk ein, und starten Sie den Referenzcomputer.

3.  Verbinden Sie nach Windows PE gestartet wurde, **USB-B**.

4.  Unter den **X:\Windows\system32&gt; ** Befehlszeile, Typ ***Diskpart*** und drücken Sie &lt;EINGABETASTE&gt; Diskpart zu starten.

5.  Bei der **\DISKPART&gt; ** -Befehlszeile, geben Sie ***List Volume***.

6.  Unter der "*Label"* Spalte, das **/ B-USB-** Laufwerk identifizieren, und notieren Sie den Buchstaben des Volumes unter der "*Ltr"* Spalte (beispielsweise E).

7.  Geben Sie zum Beenden der Diskpart ***zu beenden*** .

#### <a name="deploy-the-image"></a>Bereitstellen des Abbilds

Exemplarische Vorgehensweise für die Bereitstellung Skript-deploy.bat in **USB-B**/Deployment Ordner verwenden, die Partitionen auf dem Gerät ausrichten Sie, und wenden Sie das Abbild. 

**Wichtig: Die Wiederherstellungspartition muss der Partition nach der Windows-Partition, um sicherzustellen, dass winre.wim während der Lebensdauer des Geräts auf dem neuesten Stand aufbewahrt werden können.**

In Windows 10 Version 1511 sind wir unsere Empfehlung nach der Partition OS platziert WinRE-Partition einrichten zu ändern. Dadurch wird während des Updates künftiges Wachstum der WinRE Partition. Heute kann mit der Partition WinRE am Anfang des Datenträgers die Größe der nie geändert werden erschwert WinRE bei Bedarf zu aktualisieren. Es wird zur Unterstützung der WinRE Partition befindet sich in unterschiedlichen Bereichen des Datenträgers mit fortgesetzt, aber wir empfehlen Ihnen, den neuen Empfehlung.

    E:\Deployment\walkthrough-deploy.bat E:\Images\BasicImage.wim
    

Es gibt mehrere hält im Skript ein. Sie werden aufgefordert Y/N für den Vorgang übernehmen, ist dies eine Compact OS-Bereitstellung.

Hinweis: Nur verwenden Sie Compact OS auf Flashlaufwerk basierten Geräten, da Compact OS Leistung der Gerätefunktionen Speicher stark abhängig ist. Compact OS wird auf einen Geräten NICHT empfohlen. Weitere Informationen finden Sie unter [Compact OS](compact-os.md).

Nachdem der Computer auf dem Bildschirm OOBE startet, drücken Sie diese Tastenkombination starten im Überwachungsmodus aus:

    Ctrl+Shift+F3

### <a name="preload-microsoft-office"></a>Laden Sie Microsoft Office

Dieser Abschnitt enthält Richtlinien für die Überprüfung vor dem Laden 2016 von Office und Office v15.4.

#### <a name="preload-microsoft-office-2016"></a>Laden Sie Microsoft Office 2016

Dieses Handbuch enthält Informationen für lizenzierte Original Equipment Manufacturers (OEMs) zur Verwendung des Office-Bereitstellungstools zum Vorinstallieren von Office 2016 bei Geräten, die das Betriebssystem Microsoft Windows ausgeführt werden.

Hinweis: Dieses Handbuch nicht die PIPC Szenarien für OEMs in Japan beziehen. 

##### <a name="prepare-office-files-on-technician-pc"></a>Vorbereiten der Office-Dateien auf dem PC-Techniker

Erhalten Sie Office-Bereitstellungstool aus X20 92403 Office 2016 v16-Bereitstellungstool für OEM OPK.

1.  Stellen Sie X20 92403 Office 2016 v16-Bereitstellungstool für OPK\Software OEM - SW DVD5 DVD\X20 92404 Office 2016 v16-Bereitstellungstool für OEM\x20 92404.img bereit.
2.  Kopieren von Dateien vom Laufwerk mit eingebundene USB-b (wobei E:\ ist Laufwerkbuchstaben für USB-B) E:\OfficeV16.
3.  Klicken Sie e:\Officev16\officedeploymenttool.exe doppelklicken auf.
4.  Enthalten Sie Ordnerpfad zum Extrahieren der Dateien E:\Officev16.

    Setup.exe und "Configuration.xml" werden in E:\Officev16 extrahiert.

    ![Setup und "Configuration.xml"](images/setup-and-configuation.png)
    
    Office v16 in die gewünschte Sprache abrufen. In diesem Beispiel wird Englisch X20-39283 Office 2016 v16 32-BIT-X64 OPK Englisch.
    
5. Kopieren Sie den Ordner Office von bereitgestelltes Laufwerk X20 39283 Office 2016 v16 32-BIT-X64 OPK\Software - DVD\X20 37728 SW DVD5 Office Pro 2016 32 Englisch 64 englische C2ROPK Pro HS HB OEM\X20-37728.img USB-b (wobei E:\ ist Laufwerkbuchstaben für USB-B) E:\OfficeV16.

    ![Office-Ordner](images/office-folder.png)
    
    [Optional] Wenn Sie ein Language Interface Pack angewendet haben, können Sie das Language Interface Pack für Office 2016 sowie hinzufügen möchten. Die folgenden Beispiele wird mit dem Language Interface Pack angewendet angezeigt.    

6. Editor-E:\Officev16\ConfigureO365Home.xml

7. Hinzufügen von Sprachen-ID, und überprüfen Sie SourcePath wie im folgenden Screenshot dargestellt.

    ![Sprachen-ID](images/language-id.png)
    
8. ConfigureO365Home.xml speichern und schließen.

9. Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten als Administrator an.

10. Geben Sie E:\Officev16 und führen Sie setup.exe/Download ConfigureO365Home.xml:

    CD E:\Officev16 Setup.exe/Download ConfigureO365Home.xml
    
    Dadurch wird die Language Packs für Deutsch und Japanisch herunterladen.
    
11. Geben Sie ein, und führen Sie Echo %ERRORLEVEL%, und überprüfen Sie der Rückgabecode 0 ist.

12. Trennen Sie die USB-B aus dem Referenzcomputer. 

##### <a name="install-office-2016-on-reference-pc"></a>Installieren Sie Office 2016 auf Referenz-PC

1. Schließen Sie USB-B in dem Referenzcomputer im Überwachungsmodus aktiviert ist.
2.  Suchen Sie nach der Buchstabe des Laufwerks für USB-B; In diesem Beispiel wird USB-B E:\.
3.  Editor-ConfigureO365Home.xml.
4.  Konfigurieren der SourcePath USB-B E:\Officev16 auf.

    ![Konfigurieren des Quellpfades](images/configure-source-path.png)
    
    Hinweis: die einzige Produkt-ID, die in der Datei "Configuration.xml" angegeben werden muss ist O365HomePremRetail. Wenn der Benutzer einen Schlüssel für ein anderes Produkt eingibt, werden wie für Office Home und Student 2016, klicken Sie dann Office automatisch als den zugehörigen Produkt konfiguriert.
    
5.  ConfigureO365Home.xml speichern und schließen.
6.  Öffnen Sie ein Eingabeaufforderungsfenster, und navigieren Sie zu d:\Officev16.
7.  Typ:

    Setup.exe / configure ConfigureO365Home.xml

##### <a name="pin-office-tiles-to-the-start-menu"></a>PIN Office Kacheln im Startmenü

Müssen Sie die Office-Kacheln im Startmenü anheften, andernfalls wird Windows die Office-Dateien entfernen, OOBE Boot Phase.

Hinweis: Sie müssen werden verwenden Sie mindestens Version 10.0.10586.0 Windows 10. Die folgenden Schritte aus, die mit früheren Versionen von Windows 10 funktionieren nicht.

1. Öffnen Sie ein Eingabeaufforderungsfenster und geben:

        notepad C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml.
        
2. Hinzufügen von &lt;AppendOfficeSuiteChoice Wahlmöglichkeiten = "Desktop2016" /&gt; Layoutmodification, als Sie finden Sie im folgenden Beispiel hervorgehoben:

    ![Layout Änderung](images/layoutmodification.png)

    Hinweis: Das Choice-Attribut ist neu. Dadurch können unterschiedliche Versionen von Office auf der Startseite zur selben Zeit fixiert werden. Jetzt ist Desktop2016 der einzige gültige Wert. Andere Werte werden in der Zukunft verfügbar.

3. Layoutmodification.xml speichern und schließen.

    Hinweis: für die Wiederherstellung der layoutmodification.xml müssen während der Wiederherstellung kopiert werden. 
    
4.  Öffnen Sie ein Eingabeaufforderungsfenster und geben:

        copy C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml c:\recovery\OEM   

    Nachdem Sie der Computer nach dem durchgehen OOBE Desktop gestartet wird, müssen im Menü Start diese drei Kacheln angefügt wird, wie im folgenden Diagramm dargestellt: 
    
    ![Office-Kacheln fixiert im Startmenü](images/office-tiles-pinned-to-start-menu.png)
    
#####  <a name="configure-the-setup-experience-for-the-user"></a>Konfigurieren der Setup-Erfahrung für den Benutzer   

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

#### <a name="preload-microsoft-office-single-image-v154"></a>Laden Sie Microsoft Office nur einem Bild v15.4

Die aktuelle Teiler-Methode des Office 2013 unterscheidet sich von anderen desktop-apps. OEMs Vorinstallieren desktop-apps, damit der apps installiert werden. Dies bedeutet, dass wenn der Benutzer die app startet, wird die app bereits installiert ist und automatisch mit keine zusätzlichen Installationsaufgaben als Endbenutzer-LIZENZVERTRAG akzeptiert und/oder Benutzer Registrierung geöffnet wird. Mit Office werden komprimierte Setup-Dateien auf den Datenträger zusätzlich zu einer Anwendung Out-of-Box-Experience (OOBE) kopiert, die zeichnet Office File Associations auf und ermöglicht es den Benutzern einen Einstiegspunkt zum Testen, kaufen oder Office aktivieren. Benutzer haben keinen Zugriff auf Word oder Excel auf der Startseite oder in der Ansicht alle Apps, bis sie Office OOBE starten, der in der Regel auf der Startseite als Kachel zur Verfügung gestellt wird. Wenn der Benutzer Office OOBE gestartet wird, beginnt das Installationsprogramm von Office. Nach Abschluss der Installation von Office werden die komprimierte Setup-Dateien, die nicht mehr benötigt werden von der Festplatte entfernt.

-   Vor der Installation von Office einzelnen Abbilds (mit oder ohne unbefristete oder Abonnementlizenz) oder Office Mobile.  Office Mobile auf Geräten mit Bildschirmgröße 10.1" und unter verwendet werden muss, und nur einem Bild von Office muss auf Geräten mit Bildschirm größer als 10.1" verwendet werden. Für Geräte, die ein einzelnes fixed-Speicher-Laufwerk mit weniger als 32 GB haben, können OEMs Office Mobile, unabhängig von der Bildschirmgröße vorinstallieren. OEMs müssen nur ein Office-Bild auf das System gleichzeitig verbunden sein.

-   PIN Office Kacheln zum Menü Start in solchen Slots, die sichtbar sind, unabhängig von der OEM-Systemen Startmenü Layout angezeigt werden, ohne es sei denn, die Office-Kacheln oder Office Kachel als zutreffend, sind fixiert als Teil der Microsoft-Gruppe der Kacheln im Menü Start.

Herunterladen: Office einzelnen Bild OPK für Sprache für Ihre Region. Für dieses Dokument verwenden wir En-us OPK für Beispiel OPK X19 96440 Office 2013 Single Image v15.4 OPK Englisch.  Dies ist der neuesten Office OPK, wenn dieses Handbuchs veröffentlicht wird. Überprüfen Sie auf SOC ([https://www.microsoftoem.com](https://www.microsoftoem.com) &gt; Software Order Center), wenn eine neuere Version von Office einzelnen Bild OPK vorhanden ist.

Hinweis: Wenn Office Kacheln automatisch als Teil der Microsoft-Gruppe der Startmenü Kacheln fixiert sind, überspringen Sie den gesamten folgenden Abschnitt zu Kachel Ersetzung.

-   Für Office nur einem Bild v15 Pin die Kachel Office als mittlerer Größe Kachel oder größer.

-   Heften Sie für Office Mobile oder Office nur einem Bild v15 Nachfolger 3 Office Kacheln (Word, Excel, PowerPoint Kacheln an) als kleine Größe Kacheln oder mehr eine 2 x 2-Ausrichtung.

<table width="462" border="0" cellspacing="0" cellpadding="0">
    <tbody>
        <tr>
            <td width="110" valign="top">
            </td>
            <td width="167" valign="top">
                <p>
Windows 8, 8.1 </p>
            </td>
            <td width="185" valign="top">
                <p>
Windows-10 </p>
            </td>
        </tr>
        <tr>
            <td width="110" valign="top">
                <p>
Einzelnes Bild </p>
            </td>
            <td width="167" valign="top">
                <p>
Kachel für Version 15 = 1 </p>
                <p>
Weiterentwicklung = 3 Kacheln </p>
            </td>
            <td width="185" valign="top">
                <p>
Kachel für Version 15 = 1 </p>
                <p>
Weiterentwicklung = 3 Kacheln </p>
            </td>
        </tr>
        <tr>
            <td width="110" valign="top">
                <p>
"Universal" apps für Office </p>
            </td>
            <td width="167" valign="top">
                <p>
n/v </p>
            </td>
            <td width="185" valign="top">
                <p>
3 Kacheln </p>
            </td>
        </tr>
    </tbody>
</table>

3 werden Beispiele für feste nebeneinander angeordnet.                   

![4 Kacheln](images/four-tiles-pinning.png) ![3 Kacheln](images/three-tiles-pinning.png) 

1 festen Kachel-Beispiel

![1 Kachel](images/one-tile-pinning.png)

1.  Möglicherweise mehrere Sprachversionen von Office-nur einem Bild v15.4 OPK geladen werden. Laden Sie alle Microsoft Office-nur einem Bild v15.4 OPK Sprachen die für die Windows-Abbild hinzugefügt Sprachen relevant sind. Beispielsweise wenn Englisch als auch Französisch Sprachpakete zu Windows-Abbild hinzugefügt werden downloaden:

    -   Office 2013 32 64-Bit-nur einem Bild v15.4 **englische** OPK

    -   Office 2013 32 nur einem Bild von 64-Bit-v15.4 **Französisch** OPK

    Hinweis: Wenn fortlaufend verschiedene Sprachen von Office installiert erhalten möchten, wird jede zusätzliche Office mit anderen Sprache ~ 300 MB Speicherplatz anstelle von ~ 1 GB belegen. Beispielsweise wenn Office15 englische und Office15 Französisch installiert sind, erhalten möchten, sein Erforderlicher Speicherplatz ~1.3GB anstelle von ~ 2 GB.

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten (mit Administratorberechtigungen).

2.  Kopieren Sie den Inhalt des OPK in ein Verzeichnis, die die OfficeSingleImagev15.4 InstallationDirectory werden.

3.  Navigieren Sie zu dem Installationsverzeichnis an. Das Installationsverzeichnis ist der Ordner mit den Dateien in der folgenden Abbildung dargestellt:

    ![Abbildung zeigt die Ordner: Dokumente, office15, Oobe; und die Dateien: copytoserver.cmd und oemsetup.en us.cmd.](images/installation-directory.png)
    
    Beispiel: Cd C:\&Lt; OfficeSingleImagev15.4 InstallationDirectory&gt;

    Hinweis: Der Installationsvorgang für das OPK ist auch für Computer, auf denen 32-Bit-Betriebssysteme oder 64-Bit-Betriebssystemen ausgeführt werden sollen. Die 32-Bit-Version von Office 2013 kann auf Computern geladen werden, auf denen 32-Bit oder 64-Bit-Betriebssystemen ausgeführt. Die 64-Bit-Version von Office 2013 kann nur auf Computern geladen werden, auf denen 64-Bit-Betriebssystemen ausgeführt. Um mögliche Kompatibilitätsprobleme mit-add-ins oder drittanbieteranwendungen, Teiler *nur die 32-Bit-Version* von Office nur einem Bild auf 32-Bit- und 64-Bit-Computern zu verhindern.

1.  Starten Sie die Installation durch Ausführen des Skripts der Office-Installation.

    Einzelnes Bild Office installieren:

        Oemsetup.en-us.cmd

    Installieren Sie Office nur einem Bild mit AFO (Aktivierung für Office)

        Oemsetup.en-us.oa30.cmd

Nach Abschluss des Vorgangs wird die Microsoft Office-Anwendung Kachel auf der Startseite platziert werden. Der Benutzer kann jedoch nur eine Sprachversion von Office nur einem Bild v15.4 installieren. In der Standardeinstellung entspricht die Sprachversion der Anwendung OOBE spracheinstellungen Windows und die einzelnen Office-Bild v15.1 Sprache, die auf dem Computer installiert ist. Wenn diese Übereinstimmung stattfinden nicht, wird das Dialogfeld Sprache Sprachen enthalten, die auf die Sprachen für Office 2013 vorab geladen basieren.

### <a name="prepare-system-for-recovery-push-button-reset-scenarios"></a>System für die Wiederherstellung Drucktaste zurücksetzen Szenarien vorbereiten.

Drucktaste Reset, erstmals in Windows 8 ist ein integrierter Recovery-Tool, das Benutzern erlaubt, die das Betriebssystem Beibehaltung von Daten und wichtige Anpassungen ohne ihre Daten im Voraus Sicherung wiederherstellen. Es verringert bietet Benutzern so weitere Optionen und die Möglichkeit zum Reparieren von ihren eigenen PCs teilnehmen mit Confidence die Notwendigkeit für benutzerdefinierte Wiederherstellung Applications.

In Windows 10 wurden die Drucktaste zurücksetzen Features aktualisiert, um die folgenden Verbesserungen umfassen:

-   **Bild weniger Wiederherstellung**

    Drucktaste zurücksetzen Features nicht mehr erforderlich oder eine separate Recovery Bild auf einer lokalen Partition oder auf Medien unterstützt. Dadurch erheblich verringert die für die Unterstützung der erforderlichen Speicherplatzes und ermöglicht Recovery sogar auf Geräten mit begrenzter Speicherkapazität.

-   **Stellt die in den aktualisierten Zustand wieder her**

Jetzt wiederherstellen Drucktaste Reset-Features das Betriebssystem (OS) und Treiber (einschließlich Gerät Applets, die im Rahmen der INF-basierte Treiberpakete installiert sind) in den aktualisierten Zustand. Dadurch wird die Zeitdauer, die Benutzer verbringen Neuinstallieren der OS Updates und Treiber nach dem Ausführen einer Wiederherstellung müssen.

Die Benutzeroberfläche Drucktaste Zurücksetzen weiterhin Anpassung Verkaufschancen anbieten. Hersteller können benutzerdefinierte Skripts einfügen, installieren Anwendungen oder zusätzliche Daten zur Verfügung stehenden Erweiterungspunkte beibehalten.

Die folgenden Drucktaste Reset-Features sind für Benutzer mit Windows 10 PCs verfügbar:

-   **Aktualisieren von Ihrem PC**

    Behebt Softwareproblemen durch die Neuinstallation des Betriebssystems Beibehaltung der Benutzerdaten, Benutzerkonten und wichtige Einstellungen. Alle anderen vorinstallierten Anpassungen werden Factory Zustand wiederhergestellt. Im Windows-10 wird dieses Feature nicht mehr Benutzer erworben universellen Windows apps1 beibehalten.

-   **Zurücksetzen von Ihrem PC**

    Bereitet den PC für das recycling oder für die Übertragung von Gesamtbetriebskosten durch Neuinstallation des Betriebssystems, alle Benutzerkonten und Inhalt (z. B. Daten, Windows-desktopanwendungen und apps für universelle Windows) entfernen und Wiederherstellen von vorinstallierten Anpassungen für deren Status Factory vor.

-   **Bare-Metal-recovery**

    Die standardmäßigen oder vorkonfigurierte Partitionslayout auf dem Systemdatenträger wiederhergestellt und erneut installiert, das Betriebssystem und die vorinstallierten Anpassungen vom externen Medium.

Weitere Informationen finden Sie unter:
- [Drucktaste zurücksetzen](push-button-reset-overview.md)
- [Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)
- [Festplatten und Partitionen](hard-drives-and-partitions.md)

#### <a name="prepare-scanstate-tool"></a>Vorbereiten der ScanState-tool 

Vorbereiten der ScanState Tool erfasst Windows-desktopanwendungen, nachdem sie installiert wurden und zusätzliche Einstellungen wie Registrierung.

Hinweis: Dies im System Techniker erfolgt.

1.  Legen Sie Techniker PC USB-B.

    Wenn Sie ein Bild **X64** Windows 10 verwenden:

        md E:\ScanState_amd64
        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\amd64" E:\ScanState_amd64
        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\amd64\Sources" E:\ScanState_amd64
        
    Wenn Sie ein Bild **X86** Windows 10 verwenden:
    
        md E:\ScanState_x86
        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\x86" E:\ScanState_x86
        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\x86\Sources" E:\ScanState_x86

    Dabei ist E: der Laufwerkbuchstabe des USB-B.

#### <a name="create-scanstate-configuration-file"></a>Erstellen Sie ScanState-Konfigurationsdatei

OEM können eine Konfigurationsdatei zum Wiederherstellen und Registrierungsschlüssel und Dateien während des Aktivierungsvorgangs PBR ausschließen.

**Wichtig: Dieser Abschnitt enthält eine Umgehung für ein bekanntes Problem in Windows 10. Sie müssen diese Methode zur Vermeidung von Problemen mit dem Prozess PBR angewendet.**

In einigen Fällen können Windows Defender Einstellungen und Erkennung Verlauf von dem Tool ScanState in das Paket Anpassungen erfasst werden. Dies kann zu Fehlern während der Wiederherstellung aufgrund von Dateikonflikten führen und bewirkt, dass den PC-Option neu starten, und geben die Phase "Installieren von Windows" wiederholt.

Hinweis: Sie können die Beispielkonfigurationsdatei auf USB-B\Recovery\recoveryimage\pbr_config.xml; verwenden, die umfasst die folgenden Schritte aus.

1.  Verwenden Sie das Tool ScanState auf den **Verweis PC im Überwachungsmodus ausgeführt**.

    Wenn Sie ein Bild **X64** Windows 10 verwenden:
    
        MD c:\Recovery\OEM
        E:\ScanState_amd64\ScanState.exe /apps /genconfig:C:\Recovery\OEM\pbr_config.xml
    
    Wenn Sie ein Bild **X86** Windows 10 verwenden:
     
        MD c:\Recovery\OEM
        E:\ScanState_x86\ScanState.exe /apps /genconfig:C:\Recovery\OEM\pbr_config.xml
    

1.  Öffnen Sie die Konfigurationsdatei im Editor

        Notepad c:\Recovery\OEM\pbr_config.xml

1.  Suchen Sie die folgenden Zeilen in der Konfigurationsdatei:

    &lt;Komponente Displayname = "Windows-Defender-Uhr--Signaturen" migrieren = "yes"...

    &lt;Komponente Displayname = "Windows-Defender-Uhr-Engine" migrieren = "yes"...

    &lt;Komponente Displayname = "Security-Schadsoftware-Windows-Defender" migrieren = "yes"...

1.  Ändern des Werts "Migration" von "Ja" auf "Nein" für jede Zeile. Beispiel:

    &lt;Komponente Displayname = "Windows-Defender-Uhr--Signaturen" migrieren = "**keine**"...

    &lt;Komponente Displayname = "Windows-Defender-Uhr-Engine" migrieren = "**keine**"...

    &lt;Komponente Displayname = "Sicherheit-Schadsoftware-Windows-Defender" migrieren = "**keine**"...

#### <a name="create-scanstate-migration-file"></a>Erstellen Sie ScanState-Migrationsdatei

OEM kann es sich um eine Konfigurationsdatei zum Wiederherstellen von Registrierungsschlüsseln und Dateien verwenden.

Erstellen Sie eine XML-Migrationsdatei verwendet, um manuell eingegebene während manufacturing Prozess Registrierungswerte wiederherzustellen. Im folgenden Beispiel wird den OEMID Registrierungswert legen Sie weiter oben in diesem Dokument wiederhergestellt.

Hinweis: USB-B\recovery\recoveryimage\regrecover.xml Beispiel enthält bereits die Registrierungswerte.

    <migration urlid="http://www.microsoft.com/migration/1.0/migxmlext/test">

     <component type="System" context="UserAndSystem">

       <displayName>OEMID</displayName>

       <role role="Settings">

       <rules>

         <include>

            <objectSet>

               <pattern type="Registry">HKLM\Software\Microsoft\Windows\CurrentVersion\Store [OEMID]</pattern>

            </objectSet>

         </include>

       </rules>

       </role>

     </component>
    
    </migration>

#### <a name="create-recovery-package-using-scanstate"></a>Erstellen von ScanState Recovery-Pakets

Verwenden Sie das Tool ScanState erfasst die installierten Anpassungen in einer Bereitstellung Paket, und speichern Sie sie in den Ordner c:\Recovery\customizations. In diesem Dokument wird die **USB-B**\Recovery\RecoveryImage-Beispiele zum Erstellen des Pakets Scanstate verwendet.

Wichtig: Das ScanState-Paket von PBR verwendet eine .ppkg-Datei im Ordner C:\Recovery\Customizations gespeichert werden muss oder PBR werden nicht das Paket wiederherstellen.

1.  Erstellen Sie den Wiederherstellung OEM-Ordner, und kopieren Sie den Inhalt des **USB-B**\Recovery\RecoveryImage.

        Copy E:\Recovery\recoveryimage c:\recovery\OEM

        Copy E:\StartLayout\layoutmodification.xml c:\recovery\OEM

1.  Führen Sie ScanState, um die app und Anpassungen zu erfassen.

   Wenn Sie ein Bild **X64** Windows 10 verwenden:
    
    '''Syntax Mkdir c:\recovery\customizations E:\ScanState_amd64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /i:c:\recovery\oem\regrecover.xml /config:C:\Recovery\OEM\pbr_config.xml/o/c /v:13 /l:C:\ScanState.log '''
    
   Wenn Sie ein Bild **X86** Windows 10 verwenden:
    
    '''Syntax Mkdir c:\recovery\customizations E:\ScanState_x86\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /i:c:\recovery\oem\regrecover.xml /config:C:\Recovery\OEM\pbr_config.xml/o/c /v:13 /l:C:\ScanState.log '''
    
   Dabei ist E: der Laufwerkbuchstabe des **USB-B***

#### <a name="create-extensibility-scripts-to-restore-additional-settings"></a>Erstellen von Skripts, um zusätzliche Einstellungen wiederherzustellen Erweiterbarkeit

Sie können die Drucktaste zurücksetzen Benutzererlebnis Erweiterungspunkte konfigurieren. So können Sie benutzerdefinierte Skripts ausführen, installieren zusätzliche Applikationen oder zusätzliche Daten für Benutzer, der Anwendung oder der Registrierung beibehalten.

Das Beispielskript EnableCustomizations.cmd während PBR aufgerufen, und es werden zwei Schritte ausführen:

1.  Kopieren Sie die Datei unattend.xml für die erste Bereitstellung in den Ordner \windows\panther verwendet.

2.  Kopieren Sie den layoutmodification.xml an das System.

Dadurch wird die zusätzliche Layout Einstellungen von diese beiden Antwortdateien während PBR wiederhergestellt.

**Wichtig: Recovery-Skripts und unattend.xml in kopiert werden müssen c:\Recovery\OEM Ordner für PBR Pickup und ordnungsgemäß wiederhergestellt werden.**

Kopieren Sie unattend.xml-Dateien für das Wiederherstellen von Einstellungen.

Bei Zugriff 3.0 Systeme: 

    '''syntax
    Copy /y E:\AnswerFiles\OA3.0\Unattend.xml C:\Mount\Windows\Windows\Panther
    '''
    
Nicht bei Zugriff 3.0 - Systeme:

    '''syntax
    Copy /y E:\AnswerFiles\Non_OA3.0\Unattend.xml C:\Mount\Windows\Windows\Panther
    '''
    
Dabei ist E:\ **USB-B**

#### <a name="copy-winrewim-backup"></a>Kopieren Sie winre.wim Sicherung

Während der Bereitstellung wird die Datei winre.wim verschoben. Bevor das Aufzeichnen der endgültigen Abbilds die Sicherung winre.wim im Abschnitt 4.5.17 erstellt wieder kopiert werden muss andernfalls funktioniert Recovery-Umgebung auf die endgültige Bild Bereitstellung nicht.

    Copy e:\images\winre_bak.wim c:\windows\system32\recovery\winre.wim

### <a name="finalize-and-capture-the-manufacturing-image"></a>Erfassen Sie das Abbild Fertigung und Abschließen

1.  Installationsordner und Dateien, die erstellt wurden vorinstallierte Anwendung die beispielsweise sind *C:\Office-SingleImagev15.4-Setup*zu löschen. Vorhandensein dieser Ordner kann die Größe der WIM-Datei erhöhen, wenn das Abbild des Windows-Laufwerks erfasst dient zum Abrufen.

2.  Wenn das SysPrep-Tool geöffnet ist, schließen Sie es, und öffnen Sie ein Eingabeaufforderungsfenster als Administrator.

3.  Verallgemeinern Sie das Bild mit Antwortdatei mit zusätzliche Einstellungen.

    '''Syntax C:\Windows\System32\Sysprep\sysprep /unattend:c:\recovery\oem\Unattend.xml / / OOBE/Shutdown verallgemeinern '''

1.  Verbinden "**USB-A**" und Starten des Referenzcomputers.

2.  Verbinden Sie nach Windows PE gestartet wurde, **USB-B**.

    Problembehandlung bei: Bezug auf den wurde heruntergefahren. Beim Einschalten, wenn das System zum Starten von interne HDD weiterhin wird Windows die specialize-, und klicken Sie dann die OOBE übergeben eingeben. Um eine allgemeine und stabil Bild zu erfassen, müssen keines der Windows-übergibt die werden ausgeführt. Um dieses Problem zu beheben, müssen wir verallgemeinern erneut das Bild, und drücken auf dem Bildschirm OOBE &lt;STRG&gt;+&lt;UMSCHALT&gt;+&lt;F3&gt;. Das System neu gestartet und im Überwachungsmodus gestartet wird. Im Überwachungsmodus aktiviert wechselt das System mithilfe der OOBE Herunterfahren und verallgemeinern Sysprep, wie bereits erläutert. Nach dem Neustart des Systems sicherstellen von USB-A, Windows PE zu starten. 

    Wenn das System weiterhin mit interne HDD startet, stellen Sie sicher, dass USB-Start anstelle von HDD Boot priorisiert ist. Dazu kann es erforderlich sein, geben im Menü BIOS-Referenz-Computer und die Priorität Startreihenfolge so anpassen, dass der USB-Schlüssel am oberen Rand der Liste ist.

1.  Windows-Partition Laufwerkbuchstaben zu identifizieren.

    -   Unter den **X:\windows\system32&gt; ** Aufforderung, Typ ***Diskpart*** und drücken Sie die ** &lt;EINGABETASTE&gt; ** -Taste, um Diskpart zu starten.

    -   Bei der **\DISKPART&gt; ** Aufforderung geben Sie ***List Volume***.

    -   Suchen Sie unter der Spalte "Label" die Lautstärke mit der Bezeichnung "Windows".

    -   Beachten Sie, welche Buchstaben ist in der Spalte "Ltr" zugewiesen wurde (Beispiel: C). Dies ist der Laufwerkbuchstabe, die verwendet werden muss.

    -   Geben Sie zum Beenden der Diskpart ***zu beenden*** .

        ![Diskpart](images/diskpart-v10.png)
        
#### <a name="compact-os-limited-storage-devices-only-convert-installed-customizations"></a>[Compact OS begrenzt nur Speichergeräten] Convert installiert Anpassungen

Wiederholen Sie diesen Schritt nur, wenn Sie mit eingeschränkter Speichergerät bereitgestellt werden. Einzelinstanz wirkt sich auf die Leistung Einführung einige desktopanwendungen.

Wenden Sie sich für Weitere Informationen verwiesen Sie [Compact OS](compact-os.md) wird.

    DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\apps.ppkg /ImagePath:C:\ /SingleInstance

#### <a name="reduce-size-of-the-manufacturing-image"></a>Reduziert die Größe des Bilds Fertigung

Nachdem das Bild Fertigung bereit ist, wählen Sie die Größe des Bilds reduzieren, indem löschen Sie nicht den SXS Speicher mithilfe von DISM offline Dienst das Bild. Wechseln Sie zu dem Referenzcomputer, und stellen Sie das Abbild.

Wichtig: Standardmäßig werden nicht-wichtige Updates (z. B. ZDPs, KB, LCUs) nicht wiederhergestellt. Um sicherzustellen, dass während der Herstellung vorinstalliert Updates nach der Wiederherstellung nicht verworfen werden, sie gekennzeichnet werden soll wie permanente mithilfe des Befehls /Cleanup-Image in DISM mit der /StartComponentCleanup und [/ ResetBase [/Defer]] Optionen. Updates als permanente markiert werden immer während der Wiederherstellung wiederhergestellt. Mit dieser ist erforderlich, die beibehalten werden Updates während der Herstellung in Reihenfolge für PBR wiederherstellen im ersten 28 Tage angewendet.

    MD c:\scratchdir

    Dism /Cleanup-Image /Image:C:\ /StartComponentCleanup /resetbase /scratchdir:c:\scratchdir

    RD c:\scratchdir

#### <a name="capture-the-final-manufacturing-image"></a>Erfassen Sie das Abbild endgültigen Fertigung

Hinweis: Es wird empfohlen Dism Vorgänge unter Verwendung von ein Cacheverzeichnis ausführen. In diesem Beispiel erstellen wir eine Scratchdir auf USB-B-TASTE für temporäre Dateien. Sie können jedoch, dass für jede Festplatte eine große Menge an Speicherplatz zum Erstellen eines virtuellen Verzeichnisses ist.

    MD c:\scratchdir

    Dism /Capture-Image /CaptureDir:C:\ /ImageFile:E:\Images\FinalImage.wim /Name:"FinalImage" /scratchdir:c:\scratchdir

    RD c:\scratchdir

#### <a name="deploy-the-final-image-for-verification"></a>Bereitstellen des Abbilds endgültige Überprüfung

Führen Sie das Exemplarische Vorgehensweise deploy.cmd Beispielskript zum Bereitstellen der finalimage.wim.

    E:\Deployment\walkthrough-deploy.cmd E:\Images\FinalImage.wim

### <a name="verify-image-customizations-and-recovery"></a>Vergewissern Sie sich Bild Anpassungen und Wiederherstellung

-   Neustart des Computers und beginnt. Dies kann einige Minuten dauern.

-   Computer startet im OOBE-Modus. Erstellen Sie einen simulierte Benutzer die später gelöscht werden.

-   Überprüfen Sie Ihre Anwendungen werden hinzugefügt und offline Anpassungen sind ungültig.

    Beispiel:

    -   Taskleiste

    -   Angeheftete Apps

    -   Websites

    -   Desktop-Hintergrund

    -   OEM-Informationen

    -   OEM-App-ID

    -   Standarddesign

    -   Eine Anwendung starten auf ok

Hinweis: Erste Boot auf Desktop duplizierte Kacheln mit keine Titel anzeigen kann. Dies bezieht sich auf App-Promotions für Windows 10.

**Funktionsweise von App-Promotions**

Höhergestufte Apps werden direkt nach OOBE auf Windows-10-PCs installiert. Zwei Kacheln werden heruntergeladenen apps und drei Kacheln werden Tiefe Links im Speicher. Diese Kombination kann im Laufe der Zeit ändern. Wenn der PC während OOBE nicht mit dem Internet verbunden ist, werden Platzhalter Kacheln verwendet werden erst nach der PC verbunden ist.

![App-promotions](images/app-promotions.png)

#### <a name="verify-recovery"></a>Überprüfen der Wiederherstellung

1.  Stellen Sie sicher, dass die Anpassungen nach der Wiederherstellung wiederhergestellt werden und sie weiterhin durch Ausführen von **Ihrem PC aktualisieren** und **Zurücksetzen der PC** -Features über die folgenden Einstiegspunkte-Funktion:

    -   Einstellungen

        1. Klicken Sie im Startmenü auf **Einstellungen**.

        2. Klicken Sie auf **Update & Sicherheit**in der app Einstellungen, und klicken Sie dann auf **Wiederherstellung**.

        3. Klicken Sie auf **Erste Schritte** unter **diesem PC zurücksetzen** , und befolgen Sie die auf dem Bildschirm Anweisungen.

    -   Windows RE

        1. Klicken Sie im Fenster **Wählen Sie eine Option** in Windows RE klicken Sie auf " **Problembehandlung**".

        2. Klicken Sie auf **diesem PC zurücksetzen** , und folgen Sie den auf dem Bildschirm Anweisungen.

1.  Stellen Sie sicher, Wiederherstellungsmedien können erstellt werden, und überprüfen Sie seine Funktionalität durch das Feature bare-Metal-Recovery ausführen:

    1.  **Erstellen einer Wiederherstellungslaufwerk** über die Systemsteuerung zu starten.

    2.  Führen Sie die auf dem Bildschirm Anweisungen zum Erstellen des Wiederherstellung USB-Laufwerks.

    3. Starten Sie den Computer aus der Wiederherstellung USB-Laufwerk.

    4. Klicken Sie auf " **Problembehandlung**", klicken Sie im Fenster **Wählen Sie eine Option** .

    5. Klicken Sie auf **einem Laufwerk wiederherstellen** , und führen Sie dann die auf dem Bildschirm Anweisungen.

Hinweis: Der Drucktaste zurücksetzen Benutzeroberfläche wurde in Windows 10 überarbeitet. Meine Dateien Option **beibehalten** auf der Benutzeroberfläche jetzt entspricht das **Aktualisieren von Ihrem PCs** -Feature während der das Feature zum **Zurücksetzen von Ihrem PCs** entspricht die Option **Alles entfernen** . Überprüfen Sie die Wiederherstellung die Media erstellt werden kann.

### <a name="final-shipment"></a>Letzte Lieferung

OEMs schalten Sie mindestens einmal auf dem PC, und der Specialize Konfiguration von Windows Setup abgeschlossen ist, den PC-Option für Kunden ausgeliefert, zulassen.

Der Spezialisierungskonfigurationsdurchlauf der PC-Option Hardware-spezifischen Informationen hinzugefügt und ist abgeschlossen, wenn Windows OOBE wird angezeigt.

Bitte Referenzdokumentation [OEM Richtlinie](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/COMM-Win10-OPD-RTM-Now-Avail.aspx).

### <a name="create-recovery-media"></a>Erstellen von Wiederherstellungsmedien

Wählen Sie **Option 1** zu Wiederherstellungsmedien Fertigung Bild identisch erstellen. Dies ist die Standardeinstellung und empfohlen Wiederherstellungsmedien Konfigurationsoption aber Bedenken Sie, dass Ihr Bild Fertigung 4,6 GB Größe überschreiten möglicherweise. Wenn es ist und Sie als eine Wiederherstellungsmedien DVD verwenden, wird die Wiederherstellung Dateigröße die DVD Kapazität überschritten.

#### <a name="option-1-create-recovery-media-from-custom-manufacturing-image"></a>Option 1: Erstellen von Wiederherstellungsmedien aus benutzerdefinierten Manufacturing Bild

1.  Stellen Sie auf dem Referenzcomputer das Manufacturing-Abbild der als Wiederherstellungsmedien verwendet werden. Binden Sie das endgültige Bild.

        Dism /Mount-Wim /WimFile:E:\Images\FinalImage.wim /index:1 /MountDir:C:\mount\windows 
                                                                                            
        (where E:\ is the volume label of **USB-B**)      
        
1.  Erstellen Sie die Ordnerstruktur Windows PE. Führen Sie Bereitstellung und Imaging Tool Umgebung in erweiterten Berechtigungen aus, und geben Sie in:

    Wenn Sie ein Bild **X64** Windows 10 verwenden:
    
        copype amd64 C:\resetmedia
    
    Wenn Sie ein Bild **X86** Windows 10 verwenden:
    
        copype x86 C:\resetmedia
    
1.  Ersetzen Sie die standardmäßigen Windows PE Boot-Abbild (Boot.wim) mit Windows RE-Abbild des Bilds eingebundene Fertigung.

        xcopy C:\mount\windows\Windows\System32\Recovery\winre.wim C:\resetmedia \media\sources\boot.wim /H

1.  Heben Sie die Bereitstellung des Windows-Abbilds.

        dism /Unmount-Image /MountDir:C:\mount\windows /Discard 

1.  Windows-Bild Windows PE im Ordner als wird die Wiederherstellung Media Bild kopieren.

        copy E:\Images\FinalImage.wim C:\resetmedia \media\sources\install.wim 
                                                                               
        (where E:\ is the volume label of **USB-B**)  
        
1.  Führen Sie Bereitstellung und Imaging-Tool-Umgebung aus, und stellen Sie eine Iso-Datei.

        Makewinpemedia /iso C:\resetmedia C:\MyRecoveryImage.iso 

1.  Nach Abschluss der Prozess mit der rechten Maustaste RecoveryImage.iso und **Brennen CD-Abbild**auswählen.

2.  Diese Wiederherstellungsmedien startet Windows 10 Wiederherstellung Bildschirm

    ![Recovery-Bildschirm](images/recovery-screen.png)

Weitere Informationen zum Erstellen von Image-Wiederherstellung finden Sie unter [Bare-Metal Reset-Recovery: Erstellen von Wiederherstellungsmedien beim Bereitstellen neuer Geräte](create-media-to-run-push-button-reset-features-s14.md).

#### <a name="option-2-create-recovery-media-from-the-base-windows-10-opk"></a>Option 2: Erstellen von Wiederherstellungsmedien von der Basis 10 Windows OPK

Wählen Sie **Option 2** Wiederherstellungsmedien mithilfe der Basis 10 Windows OPK von Grund auf zu erstellen.

1.  Kopieren Sie das base 10 Windows-Abbild (**USB-B**\myWindows) in einen Ordner namens "My_distribution" finden Sie unter C:\.

        md C:\my_distribution                                                    
                                                                                
        xcopy /s E:\myWindows\*.\* C:\my_distribution\                        
                                                                                
        md C:\mount\boot                                                          
                                                                                
        md C:\mount\windows                                                       
                                                                                
        copy E:\Images\FinalImage.wim C:\my_distribution\sources\install.wim  
    
    (E:\ ist, auf dem die Volumebezeichnung eines **USB-B**)                             

##### <a name="add-language-packs-to-windows-setup"></a>Hinzufügen von Language Packs zu Windows Setup

1.  Um Windows Setup Sprachpakete hinzugefügt haben, müssen die gezielte Windows Distributon install.wim und winre.wim Bilder Language Pack-Dateien hinzugefügt werden.

2.  Stellen Sie das zweite Abbild (Index 2) in Boot.wim in einem lokalen Bereitstellungsverzeichnis mit dem Befehl **Dism /Mount-Image** bereit. Beispiel:

        Dism /mount-image /imagefile:C:\my_distribution\sources\boot.wim /index:2 /mountdir:C:\Mount\boot

1.  Add Windows PE Setup optionale Komponente und Language Packs in bereitgestellten Abbild mithilfe des Befehls **Dism/Add-Package** für jede Sprache, die Sie unterstützen möchten. Windows PE-Sprachpakete sind in der Windows-ADK verfügbar. Beispiel:

        Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"                        
                                                                                                                                                                                                                                 
        Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"         
                                                                                                                                                                                                                                 
        Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-Client_fr-fr.cab"  

1.  Für Japanisch (ja-JP) unterstützen Koreanisch (Ko-KR) und Chinesisch (Zh-HK, Zh-CN, Zh-TW), müssen Sie zusätzliche Schriftart hinzufügen zu Ihrer Bild. Geben Sie beispielsweise den folgenden Befehl zum Hinzufügen von Unterstützung für japanische Schriftarten ein. Beispiel:

        Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-FontSupport-JA-JP.cab" 

1.  Erstellen Sie die Lang.ini-Datei, die mit dem **Befehl/Dism Gen-LangINI** zusätzliche sprachunterstützung entsprechend neu.

        Dism /image:C:\mount\boot /gen-langINI /distribution:C:\my_distribution 

1.  Ändern Sie die Standardsprache für Windows Setup mithilfe von DISM. Beispiel:

        Dism /image:C:\mount\boot /Set-SetupUILang:fr-FR /distribution:C:\my_distribution 

1.  Speichern Sie Ihre Änderungen wieder zurück in das Bild mit dem Befehl **Dism entladen – Image/Commit** .

        Dism /unmount-image /mountdir:C:\mount\boot /commit 

1.  Wenn Sie das Standardbild boot.wim Schriftart-Unterstützung für Japanisch (ja-JP), Koreanisch (Ko-KR) oder Chinesisch (Zh-HK, Zh-CN, Zh-TW) hinzugefügt haben, müssen Sie auch Unterstützung für Schriftarten das erste Bild (Index 1) in der Datei Boot.wim hinzufügen.

    Verwenden Sie den Befehl **Dism /Mount-Image** , um das erste Abbild (Index 1) in der Datei Boot.wim in einem lokalen Bereitstellungsverzeichnis bereitzustellen. Beispiel:

        Md C:\mount\boot1                                                                                      
                                                                                                           
        Dism /mount-image /imagefile:C:\my_distribution\sources\boot.wim /index:1 /mountdir:C:\Mount\boot1  

1.  Fügen Sie die gleichen Unterstützung für Schriftarten, die Sie der boot.wim Boot Standardbild im vorherigen Schritt hinzugefügt. Um Unterstützung für japanische Schriftarten hinzuzufügen, geben Sie beispielsweise den folgenden Befehl:

        Dism /image:C:\mount\boot1 /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-FontSupport-JA-JP.cab" 

1.  Speichern Sie Ihre Änderungen wieder zurück in das Bild mit dem Befehl **Dism entladen-Image/Commit** :

        Dism /unmount-image /mountdir:C:\mount\boot1 /commit 

##### <a name="create-a-bootable-dvd-with-oscdimg-tool"></a>Erstellen einer startbaren DVD mit dem Tool oscdimg

1.  Starten Sie **Imaging Tools Bereitstellung und** mit erhöhten Rechten Administrator an.

2.  Tool **Oscdimg** mit folgenden Parametern ausführen. Beispiel:

        oscdimg -m -o -u2 -udfver102 -bootdata:2#p0,e,bc:\my_distribution\boot\etfsboot.com#pEF,e,bc:\my_distribution\efi\microsoft\boot\efisys.bin c:\my_distribution c:\myISOname.iso

       ![Oscdimg.exe](images/oscdimg.png)

1.  Brennen Sie die ISO-Datei auf eine neue DVD. Diese DVD wird den Wiederherstellungsmedien sein.

2.  Diese Wiederherstellungsmedien startet Windows Setup Windows 10 auf normale Weise installieren, indem Sie Ihre Dateien löschen.

