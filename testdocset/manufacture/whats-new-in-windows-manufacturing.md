---
author: kpacquer
Description: "Windows 10 IoT Core (IoT Core) ist eine Version von Windows 10, die für kleinere Geräte mit oder ohne Bildschirmanzeige optimiert ist. IoT Kern verwendet die umfassenden, erweiterbare universelle Windows Plattform (UWP) API zum Erstellen von großartige Lösung."
MSHAttr: PreferredLib:/library
title: Was ist neu in IoT Core manufacturing
ms.openlocfilehash: cb3f0ca7a1f07e84a72583847f0fc68fb1d1d1e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-windows-manufacturing"></a>Was ist neu in Windows Fertigung

In diesem Thema wird die neue Verbesserungen für Desktop, Mobile und IoT Fertigung behandelt. 

## <a name="span-idwhatsnewindesktopmanufacturingspanwhats-new-in-desktop-manufacturing"></a><span id="Whats_new_in_desktop_Manufacturing"></span>Was ist neu in desktop Fertigung 

**17 November 2016**

[Hinzufügen von Language Packs Windows](desktop/add-language-packs-to-windows.md): hinzugefügt Retail Demo Erfahrung (Microsoft-Windows-RetailDemo-OfflineContent-Content-fr-fr-Package), um der Liste der Features bei Bedarf.

**11 November 2016**

– Wartung Stack Update (SSU): KB3199209 ist erforderlich, bevor Sie die neuesten General Distribution Release (GDR, derzeit KB 3200970) oder alle zukünftigen GDRs anwenden.

So aktualisieren Sie Install aktualisiert den aktuellen Informationen zu: 

-  [SSU:KB3199209](http://www.catalog.update.microsoft.com/Search.aspx?q=KB3199209) und die [neuesten GDR](https://support.microsoft.com/en-us/help/12387/windows-10-update-history) (derzeit [KB 3200970](http://www.catalog.update.microsoft.com/Search.aspx?q=3200970)), aus dem [Microsoft Update-Katalog](http://www.catalog.update.microsoft.com)herunterladen.

-  Anwenden Sie dieser SSU, und anschließend die neuesten GDR in Windows und WinRE.

-  Führen Sie DISM /Cleanup-Image /Resetbase aus.  Dieser Schritt wird empfohlen, nach dem kumulativen Update, und es ist in diesem Fall erforderlich, um sicherzustellen, dass die Änderungen in Kraft bleiben, nachdem ein Benutzer ihren PC wieder auf OOBE zurückgesetzt.

   Weitere Informationen zum Anwenden von Updates finden Sie unter [Übung 4: Updates hinzufügen und aktualisieren Sie die Edition](desktop/servicing-the-image-with-windows-updates-sxs.md) und [Übung 10: Aktualisieren der Wiederherstellung](desktop/update-the-recovery-image.md).

Der SSU:KB3199209 behebt zwei Probleme:
 
1.  Fehler beim Einfügen GDRs in winre.wim – erforderlich, er SSU in winre.wim einfügt.

2.  Drucktaste zurücksetzen unzureichende für OEM vorinstalliert GDRs:

    1.  Die Hälfte des Updates erfordert SSU in das Windows-Bild einfügen: Dieses Webpart ermöglicht GDRs gekennzeichnet als permanente mit /ResetBase nach PBR zurückkehren. 

    2.  Die andere Hälfte des Updates erfordert er die GDR in WinRE.wim einfügt.

**30 September 2016**

-  Die empfohlene Größe für Windows RE-Partition wurde von 500 MB auf 450 MB verkleinert. Die Größe Ihrer eigenen Windows RE-Partition kann variieren, basierend auf-add-ins wie [wichtige Faktoren und Sprachen](desktop/add-drivers-langs-universal-apps-sxs.md). 

-  Neues Thema: [Optimieren der Leistung von Windows PE](desktop/winpe-optimize.md) Boot Windows PE schneller nach dem Hinzufügen von Anpassungen wie Sprachen oder Start erforderliche Treiber unterstützt.

**20 September 2016**

-  Verwenden Sie zum Bereitstellen von einzelnen Windows-desktop-apps [Siloed provisioning Pakete (SPPs)](desktop/siloed-provisioning-packages.md). Zu diesem Zweck müssen Sie eine Version von DISM aus der Windows-ADK, nicht die integrierte Version von Windows oder Windows PE ausführen. Das Installationsprogramm DISM sollte WimMountADKSetup(x86/amd64).exe von nicht Wechseldatenträger ausgeführt werden. Eine exemplarische Vorgehensweise finden Sie unter [Lab 1f: Hinzufügen von Windows-desktopanwendungen mit Silo provisioning Paketen](desktop/add-desktop-apps-wth-spps-sxs.md). Wenn Befehlszeilenhilfe erhalten möchten, verwenden Sie **C:\ADKTools\DISM /Apply-SiloedPackage /?**.

**6 September 2016**

-  [Features bei Bedarf](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/features-on-demand-v2--capabilities): Wir haben die Liste [aller verfügbaren Sprachfeatures](http://download.microsoft.com/download/8/3/0/830AC3A9-68CF-4F10-9357-F27E0A03148A/Windows%2010%201607%20FOD%20to%20LP%20Mapping%20Table.xlsx)hinzugefügt.

**2 September 2016**

-  Aktualisiert [Drucktaste zurücksetzen](desktop/push-button-reset-overview.md), Details zu den geänderten Features für Windows 10, Version 1607 hinzugefügt.  

**1 September 2016**

-  In Windows 10 sollte Version 1607-Sprachpakete aus dem Windows ADK nicht für WinRE verwendet werden. Verwenden Sie stattdessen die Sprachpakete aus dem Language Pack ISO verfügbar.

**25 August 2016**

-  In Windows-10, Version 1607, ist es nicht mehr erforderlich zum Posteingang apps zu entfernen, wenn ein Language Pack hinzufügen. Wenn Sie versuchen, um apps zu entfernen, kann der DISM-Befehl ein Fehler auftritt. 
   Aktualisierte Themen: 
   -  [Hinzufügen von Language Packs zu Windows](desktop/add-language-packs-to-windows.md)
   -  [Lab 1D: Fügen Sie wichtige Faktoren, Sprachen und universelle apps für Windows](desktop/add-drivers-langs-universal-apps-sxs.md).
   -  [OEM Bereitstellung von Windows-10 für desktop-Editionen](desktop/oem-deployment-of-windows-10-for-desktop-editions.md)

**15 August 2016**

-  In Windows 10, Version 1607, enthält das Wiederherstellungsabbild Basis (WinRE) eine neue optionale Komponente: Windows PE-WLAN-Paket. Sie sollte nicht der Skripts ändern müssen. Dieses Paket ist kein sprachspezifische und muss nicht hinzugefügt oder daraus entfernt, wenn die verfügbaren Sprachen ändern.

**4 August 2016**

-  Desktop-apps, Treibern und Einstellungen im Überwachungsmodus hinzugefügt müssen separat erfasst werden, damit sie von der Drucktaste Wiederherstellungstools wiederhergestellt werden können. Weitere Informationen finden Sie unter [Übung 1g: Ändern von Überwachungsmodus](desktop/prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md).

-  Desktop-apps und Treiber Einstellungen aus Silo provisioning-Pakete (SPPs) hinzugefügt werden automatisch konfiguriert. 

**26 Juli 2016**

-  Neue Beispielskript: [Windows PE: identifizieren, indem Sie ein Skript Laufwerkbuchstaben](desktop/winpe-identify-drive-letters.md)

**21 Juli 2016**

Die folgenden Änderungen sind für Windows 10, Version 1607 neu:

- Sysprep unterstützt vorbereiten ein Bild, die von einer früheren Version von Windows 10 aktualisiert wurde. Weitere Informationen finden Sie unter [Übersicht über die Sysprep](desktop/sysprep--system-preparation--overview.md).

- Silo provisioning Pakete sind eine neue Art von Bereitstellung-Paket, das klassische Windows-Clientanwendungen kann einzeln erfassen, Treiber plus Anwendungen und mehr. Sie bieten mehr Flexibilität für den Fertigungsprozess und Verringerung des Zeitaufwands Factory Computer erstellen, die Windows-Hilfe. ScanState.exe und Dism.exe sind beide verbessert, um die aufzeichnen und Anwenden von provisioning Pakete jeweils in Silos zusammengefasst. 

- Dateinamen für Language Packs und Benutzeroberflächen-Sprachpakete wurden umbenannt. Beispiele für die neuen Dateinamen finden Sie unter [Language Packs](desktop/language-packs-and-windows-deployment.md).

- Das Sprachpaket für Chinesisch (Hongkong SAR) (Zh-HK) wird nicht mehr verwendet. Das Sprachpaket für Chinesisch (Taiwan) (Zh-TW) unterstützt Taiwan und Hongkong Gebietsschemas. Weitere Informationen finden Sie unter [Verfügbaren Language Packs für Windows](desktop/available-language-packs-for-windows.md).

- Language Packs für Windows PE und WinRE wurde verschoben zu der Language Packs DVD. OEMs und System-Builder mit Microsoft-Software-Lizenzbedingungen können Language Packs und Benutzeroberflächen-Sprachpaketen der [Website für Microsoft OEM](http://go.microsoft.com/fwlink/?LinkId=131359) oder das [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358)heruntergeladen werden.

- Ein neuer /Defer Parameter angegeben werden kann, zusammen mit/ResetBase, wenn Sie sehr langer Cleanup Vorgänge auf die nächste automatische Verwaltung, doch verzögern [reduziert die Größe des Speichers Komponente](desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image.md) wird empfohlen,- **nur** als Option in der Factory, in denen mehr als 30 Minuten für die Durchführung von DISM /ResetBase erfordert, Zurückstellen/verwenden.

- Ein neuer Parameter HA Dism /Apply-Image hinzugefügt wurde, und /Capture-Image Befehle zum Erfassen und Anwenden von erweiterten Attributen. Für Windows werden im erweiterten Attribute für Posteingang authentifizieren Code Szenarien Katalog Speicherort Hinweise erfasst. Auf diese Weise können schneller Überprüfung des weiteren, um sicherzustellen, dass Dateien/Systemkomponenten, die nicht geändert wurden. Der Prozess beim Erstellen der Datenbank und diese Hashes geschieht beim ersten Start von Sysprep-allgemeine Bild. Wenn erweiterte Attribute erfassen und wenden Sie das Abbild verwendet werden, werden diese Attribute entfernen die Zeit für diese neu erstellen und Aktivieren eines schnelleren ersten Starts auch über, ausgeführt. Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](desktop/dism-image-management-command-line-options-s14.md). 

- Eine neue Anforderung für Windows-Hardware-Anwendungskompatibilitätsprogramm, [Device.Graphics.AdapterBase.RunFromDriverStore](https://msdn.microsoft.com/windows/hardware/commercialize/design/compatibility/device-graphics#device-graphics-adapterbase), kann es sich um OEM lädt auswirken. Treiber müssen geschrieben werden, damit ihre Komponenten direkt aus dem Speicher Treiber ausgeführt werden können. % SystemRoot%\System32\DriverStore\FileRepository sind die Treiber installiert.

## <a name="span-idwhatsnewinmobilemanufacturingspanwhats-new-in-mobile-manufacturing"></a><span id="Whats_new_in_Mobile_Manufacturing"></span>Was ist neu in mobilen Fertigung


**4 Oktober 2016**

- Neues [Feature optional](https://msdn.microsoft.com/library/windows/hardware/dn756780.aspx): **16GBFEATURESONDATA** in Windows 10, Version 1607 hinzugefügt. Dieses Feature wird mehrere allgemeine Posteingang Apps auf die Datenpartition verschoben. 

## <a name="span-idwhatsnewiniotcoremanufacturingspanwhats-new-in-iot-core-manufacturing"></a><span id="Whats_new_in_IoT_Core_Manufacturing"></span>Was ist neu in IoT Core manufacturing

**4 November 2016**

- Hinzugefügten Verweise so ändern Sie die automatische Aktualisierung Einstellungen in [Lab 1D: Hinzufügen eines provisioning Pakets zu einem Bild](iot/add-a-provisioning-package-to-an-image.md).
- Schritte zur Problembehandlung, networking hinzugefügt [Lab 1D: Hinzufügen eines provisioning Pakets zu einem Bild](iot/add-a-provisioning-package-to-an-image.md): Überprüfen Sie die Wi-Fi-broadcast-Häufigkeit. Einige Wi-Fi-Adapter, einschließlich der integriert die Himbeeren Pi-3 unterstützen nicht 5 GHz Wi-Fi-Netzwerke.

**17 Oktober 2016**

- Schritte zur Problembehandlung hinzugefügt [Lab 1D: Hinzufügen eines provisioning Pakets zu einem Bild](iot/add-a-provisioning-package-to-an-image.md).

**12 Oktober 2016**

[Lab 1D: Hinzufügen eines provisioning Pakets zu einem Bild](iot/add-a-provisioning-package-to-an-image.md): 
-  Neue Schritte hinzugefügt, um sicherzustellen, dass das Feature-Manifest OEMCommonFM.xml, ist in der Datei TestOEMInput.xml enthalten.
-  Neue Netzwerkschnittstelle und Problembehandlungsschritte hinzugefügt.

**5 Oktober 2016**

[Windows 10 IoT Core ist jetzt kostenlos](iot/set-up-your-pc-to-customize-iot-core.md). Sie benötigen nicht mehr ein MSDN-Abonnement oder ein Konto als eine registrierte Microsoft OEM Obwohl Sie ein Microsoft-Konto benötigen.

**4 Oktober 2016**

- Die [Feature: **IOT\_SPEECHDATA\_DE\_US** ](iot/iot-core-feature-list.md) ist in Windows 10, Version 1607 veraltet. Fügen Sie dieses Feature nicht. Das Standardbild umfasst Sprachdaten für Englisch (USA).

**22 September 2016**

- In Windows 10 Version 1607, um [zu verhindern, dass der benutzerdefinierte BSPs automatische Updates](../service/iot/managing-iot-device-update.md), verwenden Sie die IoT\_GENERISCHEN\_POP-Paket im OemInput XML. (Sie können die Intel.Generic.DeviceInfo.cab nicht mehr verwenden, diese Datei wurde entfernt.)

- Neue [Befehlszeilenoptionen](iot/iot-core-adk-addons-command-line-options.md): 

    - Jede Nacht Erstellungstools: **BuildAgent**, **BuildKitAgent**.

    - Tools zum Konvertieren von apps, die Treiber zu Bereitstellungspaketen: **Appx2pkg**, **Inf2Pkg**

    - Tool zum Erstellen von Updatepakete: **newupdate.cmd**. Funktioniert wie **newpackage.cmd**, und ein einfacher nachverfolgen durch Speichern von Versionsnummern (versioninfo.txt) und Aktualisieren von mehreren Ordnern für die einzelnen dieses Update für den Vergleich (updateversions.txt).

**6 September 2016**

Sie können Ihre IoT Core Geräten synchronisieren [die Uhrzeit](iot/update-the-time-server.md) aus einem oder mehreren Zeitservern festlegen.

**3 August 2016**

Das integrierte Administratorkonto ist standardmäßig in Windows Version 1607, 10 jetzt deaktiviert. 

   -  Fügen das Standardkonto für Inhaltszugriff zurück, das IOT_ENABLE_ADMIN-Feature im Feature Manifest enthält diese hinzufügt das Konto mit dem Benutzernamen: Administrator und das Kennwort: `p@ssw0rd`.
   
   -  Um ein neues Konto mit einem eigenen Benutzernamen und Kennwort (empfohlen) hinzufügen, aktualisieren Sie die Datei OEMCustomizations.cmd Benutzername und Kennwort verwenden, und fügen Sie es in Ihren Build mithilfe des OEM_CustomCmd-Pakets. Weitere Informationen finden Sie unter [Übung 1 b: Hinzufügen einer app zu Ihr Bild](iot/deploy-your-app-with-a-standard-board.md).

Zusätzliche [Features für Windows 10, Version 1607](iot/iot-core-feature-list.md) Features: 
   
   - IOT_UNIFIED_WRITE_FILTER – fügt [Unified schreiben Filter (UWF)](https://developer.microsoft.com/windows/iot/docs/uwf) , um physische Speichermedium-Schreibvorgänge zu schützen.
   
   - IOT_GENERIC_POP – fügt die generische für die Zielgruppenadressierung Geräteinformationen für OS nur aktualisiert. 
   
   - IOT_NANORDPSERVER – fügt [Remote-Anzeige-Pakete](https://developer.microsoft.com/windows/iot/docs/remotedisplay).
   
   - IOT_SHELL_HOTKEY_SUPPORT – fügt Unterstützung zum Starten Standard-app mithilfe eines Hotkeys: [VK_LWIN (linke Windows-Taste)]
   
   - IOT_POWER_SETTINGS – (umbenannt aus IOT_POWER_SETIINGS)
   
   - IOT_ENABLE_ADMIN - Funktion zum Testen
   
   Sprachen: 
   
   -  IOT_SPEECHDATA_JA_JP: Fügt Sprachdaten für Japanisch
   
   -  IOT_SPEECHDATA_ZH_HK: Fügt Sprachdaten für Chinesisch (Hongkong SAR)
   
   -  IOT_SPEECHDATA_ZH_TW: Fügt Sprachdaten für Chinesisch (Taiwan)
   

**28 Juni 2016**

-  Details zum Signieren Verkaufsversion Bilder hinzugefügt: [Erstellen eines Abbilds Einzelhandel](iot/build-retail-image.md)

-  Aktualisierte [Anweisungen zum Erstellen Ihrer eigenen BSP](iot/create-a-new-bsp.md)hinzugefügt Details zum [IoT Gerät Layout](iot/device-layout.md).

**20 Juni 2016**

*  Neue BSP Tools hinzugefügt:
   -  Neue Ordnerstruktur: BSPs sind nun in separaten Ordnern gespeichert \iot-adk-addonkit\Source-&lt;Bogen&gt;\BSP. Mehrere Projekte können nun leichter im gleichen Ordner BSP gemeinsam nutzen.
   -  Aktualisiertes Tool: Newproduct: jetzt können Sie mit einer benutzerdefinierten BSP verknüpfen. Standardmäßig Arm erstellt die standardmäßigen RPi2, X86 MBM standardmäßig erstellt.
   -  Aktualisierte Lab: [Übung 2: Erstellen Ihrer eigenen Board Support-Paket](iot/create-a-new-bsp.md).

**9 Juni 2016:** 

Mehrere Updates des [Befehlszeilentools durchgeführt](iot/iot-core-adk-addons-command-line-options.md):
*  Neues Tool: BuildImage.cmd. CreateImage.cmd ähnlich, kann dieses Tool mehrere Bilder zu einem Zeitpunkt erstellen, die für automatisierte Tests hilfreich sein kann.  

   Um zu beheben, finden Sie unter Protokolldateien unter \\erstellen\\&lt;Bogen&gt;\\Pckg\\Protokolle.   

*  Aktualisiert: [Aktualisieren von apps auf Ihren Geräten IoT Core](../service/iot/updating-iot-core-apps.md). Dasselbe Verfahren können Sie die um app-Pakete und app-Pakete zu erstellen. Für Windows 10, Version 1607, können Sie auch Ihre apps über den Windows Store aktualisieren. 

**2016, Mai 18:** 

Mehrere Updates des [Befehlszeilentools durchgeführt](iot/iot-core-adk-addons-command-line-options.md):
*  Neue Tools hinzugefügt: 
   -  NewAppxPkg: Erstellt und bereitet Arbeitsordner für das Erstellen von app-Pakete basierend auf .appx Dateien, Zertifikaten und Abhängigkeiten.
   
   -  NewDrvPkg: Erstellt und bereitet Arbeitsordner für das Erstellen von Treiberpakete basierend auf INF-Dateien.
   
   -  NewCommonPkg: Erstellt und bereitet Arbeitsordner für Dateien, Ordner, Registrierungsschlüssel und andere Elemente, die nicht architekturspezifische sind.  
   
   -  Inf2Cab: Konvertiert eine INF-Datei in einer CAB-Datei.
   
   -  BuildPkg: Builds CAB-Pakete Arbeitsordner verwenden.

*  Veraltete Tools: 
   
   -  BuildAllPackages. Verwenden Sie stattdessen BuildPkg.
   
   -  NewPkg. Verwenden Sie stattdessen Newappxpkg, Newdrvpkg und Newcommonpkg.

*  Problembehandlung und Protokollierung: beim Erstellen von Paketen, erhalten Sie eine Bereinigung-Anzeige nur mit der Pakete, die verarbeitet wurden und Fehlern. Um zu beheben, können nun die vollständige Protokolldateien an angezeigt \\erstellen\\&lt;Bogen&gt;\\Pckg\\Protokolle.

*  Aktualisiert: CreatePkg unterstützt jetzt nur die Namen Component.Subcomponent hinzufügen. Beispiel:

    ``` syntax
    createpkg Registry.SystemSettings
    ```

*  Manufacturing Labs: aktualisiert Labs, um neue NewAppPkg, NewDriverPkg, NewCommonPkg Tools zu verwenden.