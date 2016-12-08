---
author: Justinha
Description: Mehrsprachige Windows Image-Erstellung
ms.assetid: 5bec65d1-44b0-484c-a5b6-959f221a4290
MSHAttr: PreferredLib:/library/windows/hardware
title: Mehrsprachige Windows Image-Erstellung
ms.openlocfilehash: 9b9b0f3370717a878cda272d9a94c5b18fe72ee0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="multilingual-windows-image-creation"></a>Mehrsprachige Windows Image-Erstellung


Diese exemplarische Vorgehensweise beschreibt das Windows Assessment and Deployment Kit (Windows ADK) zum Erstellen und Bereitstellen von mehrsprachigen Versionen von Windows 10 verwenden. Es beschreibt das Erstellen einer mehrsprachigen Windows-Bild, um die Anzahl der Windows-Abbilder zu reduzieren, die für andere Regionen beibehalten werden müssen. Sie können die Bilder bereitstellen, die mithilfe dieser Vorgang von einer Netzwerkfreigabe, von einem Server oder von Medien erstellt werden.

In dieser exemplarischen Vorgehensweise wird beschrieben, wie eine offline-Windows-Abbild und Windows Recovery Bild Language Packs und andere Updatepakete hinzugefügt. Sie starten Sie dann Windows zum Überwachungsmodus und Hinzufügen von Anwendungen und Treiber. Erfassen eines Abbilds die Installation, und verwenden Sie das master-Abbild neu aufgezeichnete zu Testzwecken ein. Nachdem Sie das Bild zu testen, verwenden Sie es regionale Bilder durch Entfernen nicht benötigter Sprachressourcen erstellen. Sie können dann diese regionale Bilder bereitstellen.

Der in dieser exemplarischen Vorgehensweise beschriebene Prozess ist in erster Linie für OEMs vorgesehen, die die Anzahl der Windows-Abbilder reduzieren, die sie verwalten möchten. Durch Hinzufügen von Language Packs zu einem Bild offline, können Sie Zeitaufwand für Windows-Installation und Reduzierung der Anzahl der Bilder, die Sie verwalten. Da ein einzelnes Bild mehrere Sprachpakete hinzugefügt werden, wird die Größe des Windows-Abbilds erhöht.

IT-Experten, die ihre gesamte Bild verkleinern möchten sollten stattdessen das in [Hinzufügen von Unterstützung mehrerer Sprachen in eine Windows-Distribution](add-multilingual-support-to-a-windows-distribution.md)beschriebene Verfahren verwenden. Dieser Prozess wird beschrieben, wie die lp.cab-Datei in der Windows-Verteilung verringert die Gesamtgröße der Bild kopieren.

In diesem Handbuch:

-   [Schritt 1: Hinzufügen von Sprachpaketen auf ein Windows-Bild](#addlang)

-   [Schritt 2 (optional): Hinzufügen von Language packs Windows Setup](#optlang)

-   [Schritt 3: Testen Sie die Windows-Installation](#test)

-   [Schritt 4: Starten Sie im Überwachungsmodus, Hinzufügen von Anwendungen und Sysprep auszuführen](#bootaudit)

-   [Schritt 5: Erfassen Sie das Abbild](#imagex)

-   [Schritt 6: Erstellen von regionalen Bilder durch Entfernen von Sprachpaketen](#removepacks)

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Grundkenntnisse allgemeine desktopbereitstellung Technologien und Prozesse. Sie sollten auch grundlegend des Dateiformats Windows Imaging (WIM) verfügen. Die Schritte in diesem Handbuch wird davon ausgegangen, dass Sie ein einzelnes Windows-Abbild in der WIM-Datei verwenden. Wenn Sie die Anzahl der Bilder reduzieren, die Sie verwalten möchten, können Sie verwenden die niedrigste Edition von Windows verfügbar in Ihre WIM-Datei, und klicken Sie dann mithilfe von DISM upgrade auf eine höhere Edition von Windows. Wenn Sie mehrere Bilder verwalten möchten, können Sie die Schritte in diesem Handbuch für jedes Windows-Abbild in der WIM-Datei zum Erstellen von mehreren Versionen des Windows-Abbilds regionale wiederholen.

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-   Windows-Installationsmedium (DVD oder Windows-Installationsdateien) für mehrere Sprachen. In diesem Handbuch wird verwendet, EN-US, FR-FR Medien und De-DE.

-   Ein oder mehrere Language Packs.

-   Ein Referenzcomputer, die dem Windows Assessment and Deployment Kit (Windows ADK) installiert hat.

-   Einem Testcomputer, den Sie zum Installieren und Testen von Windows verwenden können.

## <a name="span-idaddlangspanspan-idaddlangspanstep-1-add-language-packs-to-a-windows-image"></a><span id="addlang"></span><span id="ADDLANG"></span>Schritt 1: Hinzufügen von Sprachpaketen auf ein Windows-Bild


In diesem Schritt verwenden Sie Deployment Image Servicing and Management (DISM) zum Hinzufügen von Language Packs zu einem Windows-Abbild. Nachdem Sie Sprachpakete hinzugefügt haben, können Sie die Update-Paketen hinzufügen. Das Windows-Abbild, dem Sie mit beginnen kann in einer beliebigen Sprache sein. Beispielsweise können Sie mit einem Bild Englisch (En-US) starten, und Hinzufügen von Unterstützung für Französisch (fr-FR) und Deutsch (de-DE).

Wenn Sie das Windows-Abbild Sprachpakete hinzufügen, wird der Benutzer mit einem Dialogfeld ihrer bevorzugte Sprache während Out-Of-Box-Experience (OOBE) auswählen angezeigt.

Mithilfe dieser Methode sind die Größen der Windows-Abbilder größer; Installationsdauer ist jedoch schneller, und Sie können sicherstellen, dass alle Updates, die Sie das Windows-Abbild hinzufügen auf die diesem Bild installierten Sprachen anwenden. Verwenden Sie diese Methode, wenn Sie Windows so schnell wie möglich installieren möchten.

**Wichtige**  
Das Windows-Abbild muss ein kürzlich installiertes und aktuelles Abbild. Dadurch wird sichergestellt, dass das Windows-Abbild ausstehende online Aktionen nicht vorhanden ist.

Installieren Sie Sprachpakete immer vor der Installation von Updates. Wenn Sie ein Update installieren (Hotfix, allgemein verfügbare Version \[GDR\], begrenzt Verteilung Release \[LDR\], oder Servicepack \[SP\]), vor der Installation eines Sprachpakets die Language-abhängigen Ressourcen enthält, die sprachspezifische Änderungen, die in dem Update enthalten sind, werden nicht übernommen. Pakete, die Language Pack Abhängigkeiten haben identifiziert werden können, mithilfe der `Dism /Get-PackageInfo` Befehl. Suchen Sie im Abschnitt "Benutzerdefinierte Eigenschaften" des Berichts, für die Abhängigkeit = "Language Pack" Schlüssel/Wert-Paar. Wenn Language Packs nach einem LDR oder GDR-Paket, die dieses Attribut hat installiert sind, muss das Update neu installiert werden.

 

**Zum Hinzufügen von Language Packs zu einem Windows-Abbild**

1.  Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten Bereitstellung und Imaging Tools Environment.

2.  Geben Sie die folgenden Befehle erstellen die folgenden Ordner:

    ``` syntax
    Mkdir C:\mount\windows
    Mkdir C:\mount\winre 
    Mkdir C:\mount\boot
    Mkdir C:\LanguagePack
    Mkdir C:\my_Distribution 
    ```

3.  Kopieren Sie den gesamten Inhalt des En-US Windows DVD in C:\\meine\_Verteilung. Beispiel:

    ``` syntax
    xcopy e:\windows C:\my_distribution /s /e
    ```

4.  Kopieren Sie jedes Sprachpaket auf dem Referenzcomputer ein. Beispiel:

    ``` syntax
    xcopy H:\LPs\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab C:\LanguagePack
    xcopy H:\LPs\Microsoft-Windows-Client-Language-Pack_x64_de-de.cab C:\LanguagePack
    ```

5.  Geben Sie den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten:

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\my_distribution\sources\install.wim
    ```

    Notieren Sie den Index oder Name-Wert des Bilds, das Sie ändern möchten.

6.  Verwenden Sie DISM, um das Windows-Abbild bereitzustellen. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

7.  Verwenden Sie DISM, um das Windows Recovery Environment-Abbild bereitstellen, das im Windows-Abbild vorhanden ist. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

8.  Hinzufügen von Sprachpaketen auf das bereitgestellte offline Windows-Abbild. Sie können mehrere Pakete über eine Befehlszeile hinzufügen.

    ``` syntax
    Dism /Add-Package /image:C:/mount/windows /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_de-de.cab /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
    ```

9.  Hinzufügen von Sprachpaketen auf das bereitgestellte offline Windows Recovery-Abbild. Die Sprachpakete, die für das Windows-Wiederherstellungsabbild verwendet werden sind die gleichen lp.cab-Dateien mit Windows PE verwendet. Verwenden Sie die Language Packs für Windows PE, die mit der Windows-ADK installiert sind. Beispiel:

    ``` syntax
    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\lp.cab"

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    ```

    Dieser Vorgang kann einige Minuten dauern.

10. (Optional) Fügen Sie zusätzliche optionale Komponenten und Language Packs auf das Bild der Windows-Wiederherstellung. Wenn Sie auf das Bild Recovery zusätzliche optionale Komponenten installieren möchten, müssen Sie zuerst die sprachneutrale CAB-Datei installieren, und fügen Sie die Sprache bestimmtes CAB-Dateien. Führen Sie beispielsweise den folgenden Befehl die optionale Komponente Windows PE-WinReCfg.cab hinzufügen:

    ``` syntax
    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-WinReCfg.cab"

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-WinReCfg_de-de.cab" 

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WinReCfg_fr-fr.cab"
    ```

    Es wird empfohlen, Hinzufügen von Language Packs für die folgenden optionalen Komponenten, die mit Windows Recovery Bild enthalten sind:

    -   Windows PE-WinReCfg

    -   Windows PE-Rejuv

    -   Windows PE-EnhancedStorage

    -   Windows PE für das Skripting

    -   Windows PE SecureStartup

    -   Windows PE SRT

    -   Windows PE-WDS-Tools

    -   Windows PE WMI

    -   Windows PE-HTA

11. Konfigurieren Sie die Standardeinstellungen für die Sprache, in dem Windows-Abbild zu verwenden.

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:fr-fr
    ```

12. Konfigurieren Sie die Standardeinstellungen für die Sprache im Windows-Wiederherstellungsabbild verwenden.

    ``` syntax
    Dism /image:C:\mount\winre /set-allIntl:fr-fr
    ```

13. Erstellen Sie die lang.ini-Datei erneut.

    ``` syntax
    Dism /image:C:\mount\windows /gen-langini /distribution:C:\my_distribution
    ```

14. Stellen Sie sicher, dass die Sprachen installiert werden und die richtige Sprache als Standard konfiguriert ist.

    ``` syntax
    Dism /image:C:\mount\windows /get-intl /distribution:C:\my_distribution 
    Dism /image:C:\mount\winre /get-intl
    ```

    Die Ausgabe für das Windows-Abbild sollte etwa wie folgt aussehen:

    ``` syntax
    Reporting offline international settings.

    Default system UI language : fr-FR
    System locale : fr-FR
    Default time zone : Pacific Standard Time
    User locale for default user : fr-FR
    Location : France (GEOID = 84)
    Active keyboard(s) : 040c:0000040c
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): de-DE
      Type : Fully localized language.
    Installed language(s): en-US
      Type : Fully localized language.
    Installed language(s): fr-FR
      Type : Fully localized language.

    Reporting distribution languages.

    The default language in the distribution is:
    en-US

    The other available languages in the distribution are:
    No languages found

    The operation completed successfully.
    ```

    Die Ausgabe für das Windows-Wiederherstellungsabbild sollte ähnlich der folgenden:

    ``` syntax
    Reporting offline international settings.

    Default system UI language : fr-FR
    System locale : fr-FR
    Default time zone : Pacific Standard Time
    User locale for default user : fr-FR
    Location : France (GEOID = 84)
    Active keyboard(s) : 040c:0000040c
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): de-DE
      Type : Fully localized language.
    Installed language(s): en-US
      Type : Fully localized language.
    Installed language(s): fr-FR
      Type : Fully localized language.

    The operation completed successfully.
    ```

15. Aufheben der Bilder, die Änderungen zu übernehmen. Beachten Sie, dass Sie das Windows-Wiederherstellungsabbild heben Sie die Bereitstellung müssen vor der hebt die Bereitstellung und das Windows-Abbild commit.

    ``` syntax
    DISM /unmount-image /mountdir:C:\mount\winre /commit
    DISM /unmount-image /mountdir:C:\mount\windows /commit
    ```

## <a name="span-idoptlangspanspan-idoptlangspanstep-2-optional-add-language-packs-to-windows-setup"></a><span id="optlang"></span><span id="OPTLANG"></span>Schritt 2 (optional): Hinzufügen von Language packs Windows Setup


In diesem Schritt fügen Sie die Unterstützung mehrerer Sprachen zu Windows Setup. Dadurch wird ein Endbenutzer Windows Setup ausführen, und wählen Sie eine bestimmte Sprache, die Sie installieren. Sie die Standarddatei boot.wim Sprachpakete hinzugefügt, und kopieren Sie in die Windows-Verteilung Sprachressourcen.

**Hinweis**  
Dieser Schritt ist optional. Wenn Sie diesen Schritt abgeschlossen haben, können Sie Windows Setup in einer anderen Sprache als der Sprache ausführen, die Sie für das Betriebssystem auswählen. Dies wird jedoch nicht hinzufügen von Unterstützung für Schriftarten für alle Sprachen behandelt.

 

**So das Standardbild Boot Sprachpakete hinzu**

1.  Öffnen Sie Bereitstellungstools an der Eingabeaufforderung mit erhöhten Berechtigungen.

2.  Verwenden Sie DISM zum Bereitstellen von Index 2 der Datei Boot.wim. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\boot.wim /Index:2 /MountDir:C:\mount\boot
    ```

3.  Fügen Sie Windows PE-Language Packs und Windows Setup optionalen Komponenten auf das bereitgestellte Abbild für jede Sprache, die Sie unterstützen möchten. Beispiel:

    ``` syntax
    DISM /add-package /image:C:\mount\boot /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab" 

    DISM /add-package /image:C:\mount\boot /packagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\lp.cab"
    ```

4.  Fügen Sie die optionalen Komponenten Windows PE Setup hinzu. Beispiel:

    ``` syntax
    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Setup.cab" 

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Setup-client.cab"
    ```

    **Hinweis**  
    Diese Windows-Setup-Sprachpakete sind für nur die Clienteditionen von Windows. Für Windows Server müssen Sie Windows PE-Setup-Server-CAB-Dateien verwenden.

     

5.  Fügen Sie die Windows PE Sprache bestimmten optionalen Komponenten. Beispiel:

    ``` syntax
    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-client_fr-fr.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Setup_de-de.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Setup-client_de-de.cab"
    ```

6.  Kopieren Sie in Ihrem Windows-Verteilung die sprachspezifische Setupressourcen aus jeder Sprache bestimmtes Windows-Verteilung in den Ordner Datenquellen in Ihrer Verteilung freigeben. Beispielsweise legen Sie die Windows-DVD für Fr-FR in das DVD-Laufwerk (e), und kopieren Sie Quellordners Fr-FR in die Windows-Verteilung.

    ``` syntax
    Mkdir C:\my_distribution\sources\fr-fr 
    Mkdir C:\my_distribution\sources\de-de

    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    xcopy E:\sources\de-de C:\my_distribution\sources\de-de /cherkyi
    ```

7.  Verwenden Sie DISM, um das Windows-Abbild bereitzustellen. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

8.  Rufen Sie die Language-Einstellungen, die im Windows-Abbild mit dem Parameter/Get-Intl konfiguriert sind. Zum Beispiel

    ``` syntax
    Dism /image:C:\mount\windows /Get-Intl
    Dism /image:C:\mount\winre /Get-Intl
    ```

9.  Ändern Sie die Standardsprache, Gebietsschema und andere internationalen Einstellungen mithilfe des /set-allInlt-Parameters.

    ``` syntax
    Dism /image:C:\mount\boot /set-allIntl:fr-fr
    ```

10. Erstellen Sie die lang.ini-Datei erneut. Die Datei "lang.ini" muss jedes Mal neu erstellt werden, hinzufügen oder entfernen Sprachressourcen aus Ihrer Verteilung und beim Hinzufügen oder Entfernen von Language Packs aus dem Windows-Abbild.

    ``` syntax
    Dism /image:C:\mount\windows /Gen-Langini /distribution:C:\my_distribution
    ```

11. Kopieren Sie die lang.ini-Datei aus der Windows-Verteilung in der Datei boot.wim an. Die in der Datei Boot.wim verwendeten Lang.ini-Datei muss die Lang.ini-Datei für das Betriebssystem-Bild übereinstimmen.

    ``` syntax
    Xcopy C:\my_distribution\sources\lang.ini C:\mount\winre\sources\lang.ini
    ```

12. Mithilfe von DISM Windows Boot Image entladen und wechselt. Sie müssen auch das Windows-Abbild hängen. Da keine der Dateien im Windows-Abbild geändert haben, können Sie die Änderungen verwerfen. Beispielsweise

    ``` syntax
    Dism /Unmount-image /MountDir:C:\mount\boot /Commit 
    Dism /Unmount-image /MountDir:C:\mount\Windows /Discard
    ```

## <a name="span-idtestspanspan-idtestspanstep-3-test-the-windows-installation"></a><span id="test"></span><span id="TEST"></span>Schritt 3: Testen Sie die Windows-Installation


In diesem Schritt installieren Sie Windows, das Auswählen einer Sprache während der Installation von Windows, und überprüfen, dass mehrere Sprachen installiert sind.

Um einen Computer ohne Betriebssystem zu starten, müssen Sie das startbare Windows PE-Medien erstellen. Diese exemplarische Vorgehensweise enthält Anweisungen zum Erstellen von Windows PE auf einem startbaren USB-Laufwerk. Zusätzliche Optionen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

**Zum Installieren von Windows**

1.  Erstellen Sie ein Windows PE-Abbild auf dem Referenzcomputer. Beispiel:

    ``` syntax
    Copype amd64 C:\winpe_amd64
    ```

    Die folgenden Verzeichnisse werden erstellt:

    -   C:\\Windows PE\_amd64\\Medien

    -   C:\\Windows PE\_amd64\\bereitstellen

    Wenn Sie Windows PE erforderliche Treiber oder anderen optionalen Komponenten hinzufügen müssen, finden Sie unter [Windows PE: Hinzufügen von Paketen (optionalen Komponenten Verweis)](winpe-add-packages--optional-components-reference.md).

2.  Fügen Sie den Referenzcomputer ein USB-Laufwerk, und führen Sie den folgenden Befehl aus:

    ``` syntax
    Makewinpemedia /ufd C:\winpe_amd64 F:
    ```

    Wobei *F* der Laufwerkbuchstabe des USB-Laufwerk ist.

    Windows PE wird mit dem USB-Laufwerk kopiert.

3.  Kopieren Sie den Inhalt der Windows-Verteilung auf ein anderes USB-Laufwerk, das über ausreichend freien Speicherplatz verfügt. Je nach der Größe der Datei install.wim müssen Sie möglicherweise das USB-Laufwerk als NTFS-Dateien zu unterstützen, die größer als 4 GB sind und formatieren.

    Beispielsweise

    ``` syntax
    Xcopy C:\my_distribution G:\my_distribution /cherkyi
    ```

    Dabei ist *G* der Buchstabe des zweiten USB-Laufwerk.

4.  Legen Sie das Windows PE USB-Laufwerk mit testen. Starten Sie den Testcomputer, um sicherzustellen, dass das Windows PE USB-Laufwerk konfiguriert ist, um zuerst gestartet. Möglicherweise müssen Sie die Startoptionen beim des Computers in der Firmware zu ändern.

5.  Nachdem die Windows PE-Befehlszeile angezeigt wird, legen Sie das USB-Laufwerk, das die Windows-Verteilung auf dem Testcomputer enthält.

6.  Identifizieren Sie die Laufwerke, Volumes und Laufwerkbuchstaben auf dem Testcomputer. Geben Sie über die Windows PE-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Diskpart 
    List volume 
    ```

    Identifizieren der Laufwerkbuchstabe des USB-Laufwerk, das die Windows-Verteilung enthält. In diesem Beispiel wird "F:\\". Beenden Sie Diskpart.

    ``` syntax
    exit
    ```

7.  Installieren Sie Windows durch Ausführen von Setup für Windows.

    ``` syntax
    F:\my_distribution\setup.exe
    ```

    Windows-Setup gestartet, und Sie werden aufgefordert, wählen Sie Ihre Sprache (französischen, deutschen oder auf Englisch). Wählen Sie eine der Sprachen und die Installation fortgesetzt. Stellen Sie sicher, dass während der Installation die richtige Sprache angezeigt wird.

## <a name="span-idbootauditspanspan-idbootauditspan-step-4-boot-to-audit-mode-add-applications-and-run-sysprep"></a><span id="bootaudit"></span><span id="BOOTAUDIT"></span>Schritt 4: Starten Sie im Überwachungsmodus, Hinzufügen von Anwendungen und Sysprep auszuführen


In diesem Schritt installieren das Windows-Abbild auf einem Testcomputer und im Überwachungsmodus starten. Während der Computer im Überwachungsmodus ausgeführt wird, fügen Sie Anwendungen, die online installiert werden müssen, und testen das Betriebssystem. Nach dem Anwendungen werden hinzugefügt, und der Computer wird getestet, führen Sie des Tools Sysprep Vorbereitung auf das Bild, das auf einem Computer bereitgestellt werden, das an einen Endbenutzer ausgeliefert wird.

**Starten im Überwachungsmodus**

1.  Führen Sie eine der folgenden auf einen Testcomputer im Überwachungsmodus zu starten:

    -   Drücken Sie für ein Benutzer die Installation die OOBE angezeigt wird **STRG + UMSCHALT + F3**.

    -   Verwenden Sie bei einer unbeaufsichtigten Installation eine Antwortdatei, mit der Microsoft-Windows-Bereitstellung\\Reseal\\Modus zu **überwachende**konfiguriert. Diese Einstellung sollte in **der Konfigurationsphase** angezeigt werden.

    -   Führen Sie den Befehl **Sysprep/audit** in ein Eingabeaufforderungsfenster.

    Weitere Informationen finden Sie unter [Grundlegendes zu Überwachungsmodus aktiviert](http://go.microsoft.com/fwlink/?LinkId=148031).

2.  Installieren von Microsoft Office oder einer anderen Anwendung, und Testen Sie den Computer. Weitere Informationen finden Sie unter [Anpassen von Windows im Überwachungsmodus aktiviert](http://go.microsoft.com/fwlink/?LinkId=148032).

3.  Bereiten Sie den Computer für die Bereitstellung, indem Sie einen der folgenden Schritte ausführen:

    -   Führen Sie im Überwachungsmodus den Befehl **Sysprep** mit der **/Oobe/Shutdown / verallgemeinern** Optionen.

    -   Konfigurieren Sie in unbeaufsichtigte Installationen, die Microsoft-Windows-Deployment\\Reseal\\Einstellung **Oobe**Modus. Weitere Informationen zu dieser Einstellung finden Sie in der Referenz für unbeaufsichtigte Windows (Unattend.chm).

    Weitere Informationen finden Sie unter [Technische Referenz zu Sysprep](http://go.microsoft.com/fwlink/?LinkId=148028).

    Nach Abschluss der Sysprep wird der Testcomputer beendet.

## <a name="span-idimagexspanspan-idimagexspanstep-5-capture-the-windows-installation"></a><span id="imagex"></span><span id="IMAGEX"></span>Schritt 5: Erfassen Sie die Windows-installation


In diesem Schritt des Windows-Abbilds aus dem Testcomputer erfassen und speichern Sie sie für die Verwendung als master-Abbild.

**Zum Erfassen des Abbilds**

1.  Starten Sie den Testcomputer durch Windows PE starten.

2.  Identifizieren Sie die Laufwerke, Volumes und Laufwerkbuchstaben auf dem Testcomputer. Geben Sie über die Windows PE-Eingabeaufforderung Folgendes ein:

    ``` syntax
    Diskpart 
    List volume 
    ```

    Identifizieren der Laufwerkbuchstabe des das USB-Laufwerk mit Windows-Verteilung. Beenden Sie Diskpart.

    ``` syntax
    exit
    ```

3.  Erfassen Sie an der Eingabeaufforderung Windows PE das Windows-Abbild. In diesem Beispiel wird E:\\ als den Speicherort der Windows-Installation. Beispiel:

    ``` syntax
    dism /Capture-Image /CaptureDir:E:\ /ImageFile:E:\MyInstall.wim /Name:"Fabrikam"
    ```

4.  Kopieren Sie das Abbild auf einem USB-Laufwerk oder auf einer Netzwerkfreigabe. Beispiel:

    ``` syntax
    xcopy E:\MyInstall.wim G:\MyInstall.wim
    ```

    Dabei ist *G* der Buchstabe des USB-Laufwerk.

## <a name="span-idremovepacksspanspan-idremovepacksspanstep-6-create-regional-images-by-removing-language-packs"></a><span id="removepacks"></span><span id="REMOVEPACKS"></span>Schritt 6: Erstellen von regionalen Bilder durch Entfernen von Sprachpaketen


In diesem Schritt erstellen Sie eine regionale Windows-Abbild durch Entfernen von Language Packs aus dem Abbild, während sie offline ist. Dieses Bild enthält nur die Sprachen, die für die Bereitstellung in einem bestimmten Bereich erforderlich sind.

**Wichtige**  
Sie sollten ein Language Pack nicht von einem offline-Windows-Abbild entfernen, wenn online Aktionen ausstehen. Das Windows-Abbild muss ein kürzlich installiertes und aktuelles Abbild handeln. Dadurch wird sichergestellt, dass das Windows-Abbild keine ausstehenden online Aktionen, die ein Neustart erforderlich.

 

**So entfernen ein Language pack**

1.  Suchen Sie das Windows-Bild, dem Sie Sprachen entfernen möchten, und kopieren Sie es auf dem Referenzcomputer. Beispiel:

    ``` syntax
    xcopy F:\sources\MyInstall.wim C:\my_images\MyInstall.wim
    ```

2.  Öffnen Sie die Bereitstellungstools an der Eingabeaufforderung mit erhöhten Berechtigungen.

3.  Geben Sie den folgenden Befehl an das Windows-Abbild bereitgestellt werden.

    ``` syntax
    Dism /mount-image /ImageFile:C:\my_images\MyInstall.wim /Name:"Fabrikam" /MountDir:C:\mount\windows 
    Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

4.  Optional: Geben Sie den folgenden Befehl aus, um die Pakete aufzulisten, die in der offline-Abbild installiert sind.

    ``` syntax
    Dism /Image:C:\mount\windows /Get-Packages 
    Dism /Image:C:\mount\winre /Get-Packages
    ```

    Sie können `> packagelist.txt` mit dem Namen PackageList, um die Liste in eine Textdatei auszugeben. Beachten Sie die Paketidentität des Language Packs, den Sie entfernen möchten.

5.  Entfernen eines Language Packs aus dem Bild. Sie können mehrere CAB-Dateien, die ein Command-Line-Anweisung entfernen.

    **Hinweis**  
    Sie können die mithilfe der **Option/PackageName** Paketidentität angeben oder Sie können auf die ursprüngliche Quelle des Pakets über die **Option/PackagePath** verweisen. Beispiel:

    ``` syntax
    Dism /Image:C:\mount\windows /Remove-Package /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
    Dism /Image:C:\mount\winre /Remove-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    ```

    Weitere Informationen finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

6.  Wenn Sie das Bild Wiederherstellung zusätzliche optionale Komponenten hinzugefügt haben, entfernen Sie die Liste der sprachspezifischen optionalen Komponenten und ändern Sie die Standardeinstellungen für die Sprache. Beispiel:

    ``` syntax
    Dism /image:C:/mount/winre /Remove-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WinReCfg_fr-fr.cab"
    ```

7.  Optional Wenn Sie der Datei boot.wim zusätzliche sprachunterstützung hinzugefügt haben, entfernen Sie sprachspezifische Ressourcen und optionalen Komponenten aus der Datei boot.wim. Beispiel:

    ``` syntax
    Dism /mount-image /ImageFile:C:\my_distribution\boot.wim /index:2 /MountDir:C:\mount\boot  

    Dism /remove-package /image:C:\mount\boot /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab" 

    Dism /remove-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    Dism /remove-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-client_fr-fr.cab" 

    Dism /image:C:\mount\boot /set-allIntl:de-de

    rmdir C:\my_distribution\sources\fr-fr /s

    ```

8.  Erstellen Sie die Datei "lang.ini" neu, und ändern Sie die Standardeinstellungen für die Sprache mithilfe des folgenden Befehls:

    ``` syntax
    Dism /image:C:\mount\winre /Set-AllIntl:de-de
    Dism /image:C:\mount/windows /Gen-LangINI /distribution:C:\my_distribution /Set-AllIntl:de-DE
    ```

9.  Optional Wenn Sie aus der Datei boot.wim Sprachen entfernt haben, kopieren Sie die aktualisierte lang.ini-Datei zum Boot Bild. Nachdem Sie die lang.ini-Datei in die boot.wim aktualisiert haben, hebt die Bereitstellung der Datei boot.wim.

    ``` syntax
    Dism /unmount-image /MountDir:C:\mount\boot /Commit
    ```

10. Geben Sie den folgenden Befehl commit der Änderungen und Aufheben der Bilder.

    ``` syntax
    Dism /unmount-image /MountDir:C:\mount\winre /Commit 
    Dism /unmount-image /MountDir:C:\mount\windows /Commit
    ```

 

 





