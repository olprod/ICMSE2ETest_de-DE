---
Description: Here's what you'll need to start customizing, testing, and deploying Windows on mobile devices.
ms.assetid: 57bc2066-0b27-4fcb-b938-1c73a361b212
MSHAttr: PreferredLib:/library
title: "Vorbereiten Sie für Windows mobile-Entwicklung"
author: CelesteDG
ms.openlocfilehash: e5fdd1fce8bf6a6926487df060b4785a6596ccd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prepare-for-windows-mobile-development"></a>Vorbereiten Sie für Windows mobile-Entwicklung


Nachfolgend finden Sie benötigen Folgendes um anpassen, testen und Bereitstellen von Windows auf mobilen Geräten zu starten.

## <a name="span-idmeetalltheprerequisitesspanspan-idmeetalltheprerequisitesspanstep-1-meet-all-the-prerequisites"></a><span id="meet_all_the_prerequisites"></span><span id="MEET_ALL_THE_PREREQUISITES"></span>Schritt 1: Erfüllen Sie die erforderlichen Komponenten


Bevor Sie auf Ihrem Windows mobile-Entwicklung beginnen können, stellen Sie sicher, dass Sie diese Anforderungen erfüllen:

-   Sie haben Zugriff auf die Microsoft Connect-Website, auf dem mobilen Partner die neuesten mobilen OS Kits und Pakete herunterladen können.

    Wenn Sie keinen Zugriff haben oder benötigen Sie weitere Informationen, wenden Sie sich an Ihrem Microsoft-Partner.

-   Einem Entwicklungscomputer Arbeitsstation oder einem Techniker

    Diesen PC wird während der Entwicklung erforderlichen Tools auszuführen. Der PC muss eine der folgenden Betriebssysteme ausgeführt werden:

    -   Windows 10 32-Bit (x 86) oder 64-Bit (x 64)
    -   Windows 8.1 32-Bit (x 86) oder 64-Bit (x 64)
    -   Windows 7, 32-Bit (x 86) oder 64-Bit (x 64)

    Sie müssen alle wichtigen Windows-Updates zur Vermeidung von Problemen bei Verwendung der mobilen Kits installieren.

-   Deinstallieren von früheren Versionen von Tools und kits

    Wenn Sie eine andere Version verwenden der Tools und Kits als die Verbundpartner in den Abschnitt *Pairing Informationen* Kit Anmerkungen zu dieser Version, müssen Sie zuerst alle diese Komponenten zugeordnet Programme deinstallieren.

-   Laden Sie die Kits und OS-Pakete

    Laden Sie die neuesten Kits und Tools für Windows 10 Mobile von der Microsoft Connect-Website. Finden Sie unter Inhalte des mobilen Builds erfahren Sie mehr über den Inhalt des MobileOS Kit für verschiedene Silicon Architekturen.

-   Mobile Hardware Verweis

    Das mobile Gerät sollte die mobilen Geräten in ein einziges Modell Zeile darstellen; beispielsweise den Contoso Windows Phone. Weitere Informationen zu detaillierten hardwareanforderungen für jedes Gerät, das Windows 10 Mobile ausgeführt wird, finden Sie *im Abschnitt 2.0 – die Mindestanforderungen für Hardware für Windows 10 Mobile* in [Mindestanforderungen für Hardware](https://msdn.microsoft.com/library/windows/hardware/dn915086).

-   Pinnwand Support-Paket (BSP) erforderliche Komponenten

    Stellen Sie sicher, dass Sie alle erforderlichen BSP-Dateien für die Verweis-Hardware verfügen. Eine BSP ist ein Satz von Dateien und Treibern, die Windows 10 Mobile wird verwendet, um die Kommunikation mit der Hardware auf dem Gerät, um das Betriebssystem zu starten und ein Betriebssystemabbilds erstellen, das an die Verweis Hardware ausgeführt werden können. Der Hersteller SoC bietet BSP für Ihre Hardware Verweis.

## <a name="span-idinstallthetoolsanddevelopmentkitsspanspan-idinstallthetoolsanddevelopmentkitsspanstep-2-install-the-tools-and-development-kits"></a><span id="install_the_tools_and_development_kits"></span><span id="INSTALL_THE_TOOLS_AND_DEVELOPMENT_KITS"></span>Schritt 2: Installieren Sie die Tools und Development kits


Die folgenden Kits und Tools sind für Windows mobile Entwicklung verwendet:

-   Visual Studio 2015 ist die primäre Entwicklungsumgebung für das Schreiben von apps und Treiber.

-   Windows Mobile Betriebssystem 10, die im MobileOS-Paket enthalten ist.

-   Windows Assessment and Deployment Kit (ADK), mit Tools, die Sie verwenden können sind, für das Erstellen und Anpassen des Abbilds wie und einige andere, die Sie Bereitstellungstools können zur einfacheren automatisieren eine umfangreiche Bereitstellung von Windows verwenden.

-   Windows Driver Kit (WDK) und Windows 10 eigenständige SDK, die separat installieren oder installieren die Enterprise WDK (EWDK), das eine Version der treiberkits und SDK enthält werden können.

-   Windows Hardware Lab Kit (HLK), der ein Testframework, die Sie zum Testen von Hardwaregeräten für Windows verwenden können.

Die folgende Tabelle gibt an, welche Entwicklungsszenarien für jede Kits und Tools erforderlich.

| Entwicklungsszenario                                                                   | MobileOS-kit | Windows ADK  | Windows eigenständige SDK | WDK          | Visual Studio 2015 |
|----------------------------------------------------------------------------------------|--------------|--------------|------------------------|--------------|--------------------|
| Kompilieren Sie Code, der auf dem mobilen Gerät (z. B. Treiber, Dienste und apps) ausgeführt wird | Eingabe erforderlich     | Eingabe erforderlich     | Eingabe erforderlich               | Eingabe erforderlich     | Eingabe erforderlich           |
| Erstellen von Paketen                                                                         | Nicht erforderlich | Erforderlich     | Nicht erforderlich           | Nicht erforderlich | Nicht erforderlich       |
| Sign-Binärdateien und Paketen                                                             | Nicht erforderlich | Erforderlich     | Nicht erforderlich           | Nicht erforderlich | Nicht erforderlich       |
| Erstellen und Anpassen von mobilen Bilder auf der Befehlszeile mit ImgGen                     | Erforderlich     | Nicht erforderlich | Eingabe erforderlich               | Eingabe erforderlich     | Nicht erforderlich       |
| Erstellen und Anpassen von mobilen Bildern mithilfe von Windows ICD                                    | Eingabe erforderlich     | Eingabe erforderlich     | Nicht erforderlich           | Nicht erforderlich | Nicht erforderlich       |

 

**Installieren des Kits und tools**

1.  Befolgen Sie die Anweisungen zum Herunterladen und Installieren von [Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=533470), das [Windows Driver Kit (WDK) 10](https://go.microsoft.com/fwlink/p/?LinkId=733614)und das [Windows-10-SDK](https://go.microsoft.com/fwlink/p/?LinkId=616887).

    **Hinweis**  Visual Studio 2015 ist nur erforderlich, wenn Sie Code kompilieren, die auf dem mobilen Gerät, wie Treiber und apps ausgeführt wird.

     

    Bestätigen, dass das Windows SDK ordnungsgemäß installiert wurde, sicher, dass der in der folgenden Tabelle aufgeführten Unterverzeichnisse auf Ihrem PC-Techniker vorhanden. Einige der diese Unterverzeichnisse möglicherweise nicht im Installationsverzeichnis Kit angezeigt, wenn Sie sie aus der Installations-Assistent für Windows SDK ausgewählt haben.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Verzeichnisstruktur für Windows-installation</th>
    <th align="left">Unterverzeichnisse in der Verzeichnisstruktur</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Für eine 32-Bit-Betriebssystem: <strong>C:\Program c:\Programme\Windows Kits\10</strong></p>
    <p>Für eine 64-Bit-Betriebssystem: <strong>c:\Programme\Gemeinsame Dateien (x86) \Windows Kits\10</strong></p></td>
    <td align="left"><ul>
    <li><strong>Papierkorb</strong></li>
    <li><strong>Kataloge</strong></li>
    <li><strong>Debugger</strong></li>
    <li><strong>Entwurfszeit vorgesehen</strong></li>
    <li><strong>Einschließen</strong></li>
    <li><strong>LIB</strong></li>
    <li><strong>Redist</strong></li>
    <li><strong>Verweise</strong></li>
    <li><strong>Tastenkombinationen</strong></li>
    <li><strong>Testen</strong></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

     

    Um zu bestätigen, dass das WDK ordnungsgemäß installiert wurde, stellen Sie sicher, dass die in der folgenden Tabelle aufgeführten Unterverzeichnisse auf Ihrem PC-Techniker vorhanden sind.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Verzeichnisstruktur für Windows-installation</th>
    <th align="left">Unterverzeichnisse in der Verzeichnisstruktur</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Für eine 32-Bit-Betriebssystem: <strong>C:\Program c:\Programme\Windows Kits\10</strong></p>
    <p>Für eine 64-Bit-Betriebssystem: <strong>c:\Programme\Gemeinsame Dateien (x86) \Windows Kits\10</strong></p></td>
    <td align="left"><ul>
    <li><strong>Erstellen</strong></li>
    <li><strong>BuildLabSupport</strong></li>
    <li><strong>CodeAnalysis</strong></li>
    <li><strong>CrossCertificates</strong></li>
    <li><strong>Debuggen</strong></li>
    <li><strong>Hilfe</strong></li>
    <li><strong>Remote</strong></li>
    <li><strong>Tools</strong></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

     

2.  Installieren der [Windows 10 ADK](http://go.microsoft.com/fwlink/p/?LinkId=526740).

    Stellen Sie sicher, dass der **Installationspfad** auf das Installationsverzeichnis Kit festgelegt ist **C:\\Program Files\\Windows Kits\\10** (für eine 32-Bit-Betriebssystem) oder **C:\\Program Files (x86)\\Windows Kits\\10** (für eine 64-Bit-Betriebssystem).

    Wählen Sie auf der Seite **Wählen Sie die Features, die Sie installieren möchten** Folgendes ein:

    -   **Bereitstellungstools**
    -   **Vorinstallation Windows-Umgebung (Windows PE)**
    -   **Imaging und Konfiguration Designer (ICD)**
    -   **Konfiguration-Designer**
    -   **User State Migrationstool (USMT)**

    Bestätigen, dass der Windows-ADK ordnungsgemäß installiert wurde, sicher, dass die **Assessment and Deployment Kit** unter Windows-Installationsverzeichnis angezeigt wird.

3.  Herunterladen Sie der neuesten mobilen OS Kits und Paketen aus der Microsoft Connect-Website und kopieren Sie den Inhalt in ein lokales Verzeichnis auf der Entwicklungsarbeitsstation.

    Die Kits und Pakete enthalten die Dateien und die erforderlichen Tools zum Erstellen eines Bilds Windows 10 Mobile.

4.  Extrahieren Sie die Dateien auf den Installationsspeicherort Kit und Pakete.

    1.  Extrahieren Sie das Paket MobileOS-Arm-fre.zip.
    2.  Öffnen Sie das extrahierte Paket, und kopieren Sie alle Unterordner und deren Inhalte auf das Installationsverzeichnis Kit **C:\\Program Files\\Windows Kits\\10** (für eine 32-Bit-Betriebssystem) oder **C:\\Program Files (x86)\\Windows Kits\\10** (für eine 64-Bit-Betriebssystem). Die Ordner werden sollte: FieldMedic, FMFiles, MSPackages, OEMCustomization und OEMInputSamples.

5.  Suchen Sie im Ordner **OEM** Doppelklicken auf **Setup.exe** , um die folgenden mobilen Komponenten installieren:

    -   Windows Phone-Treiberkits (WPDK)
    -   Symbole Debugger
    -   Windows Hardware Lab Kit-Inhalte für Telefon
    -   Testen Sie die Shell (TShell)
    -   Kern-Pakete

## <a name="span-idinstallothertoolsspanspan-idinstallothertoolsspanstep-3-install-other-tools"></a><span id="install_other_tools"></span><span id="INSTALL_OTHER_TOOLS"></span>Schritt 3: Installieren von anderen tools


Sie können einige Tools getrennt von den mobilen Kit installieren. Diese Tools, die im unabhängigen Hardwarehersteller enthaltenen\_Tools Ordner, sind unten aufgeführt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Installer-Paket</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>WP_CPTT_NT-X86-fre.msi</p></td>
<td align="left"><p>Die Windows phone allgemeine Verpackung und TestTools.</p></td>
</tr>
<tr class="even">
<td align="left"><p>WP8KDConn.msi</p></td>
<td align="left"><p>Das Paket KDBG-Diensten, das enthält die folgenden Komponenten:</p>
<ul>
<li><p>Virtuelle Ethernet-Tool (VirtEth.exe)</p></li>
<li><p>Virtuelles Netzwerk-Treiber (Virtual PC 2007 Filter, VmNetSrv), die für das virtuelle Ethernet-Tool erforderlich ist, es sei denn, Virtual PC 2007 bereits installiert ist; der Benutzer werden aufgefordert, zwei nicht signierte Treiber zu installieren.</p></li>
<li><p>Serielle USB-Treiber (usb2ethernet und Usbcompcom)</p></li>
<li><p>USB-Debugger-Treiber (usb2dbg); der Benutzer wird aufgefordert werden, um eine signierte Treiber zu installieren.</p></li>
</ul>
<p>Der Treiber virtuelles Netzwerk ist in der virtuellen PC\Utility\VMNetSrv %ProgramFiles%\Microsoft (oder das % ProgramFiles (x86) %\Microsoft virtuellen PC\Utility\VMNetSrv für eine 64-Bit-Betriebssystem) installiert Directory.</p>
<p>Die anderen drei Komponenten werden in der Windows Phone 8 KDBG Connectivity %ProgramFiles%\Microsoft (oder das % ProgramFiles (x86) %\Microsoft Windows Phone 8 KDBG Konnektivität für eine 64-Bit-Betriebssystem) installiert Verzeichnisstruktur mit dem virtuellen Ethernet-Tool im Unterverzeichnis Bin, die seriellen USB-Treiber im Unterverzeichnis drivers\Usb2Eth und die USB-Debugger Treiber im Unterverzeichnis drivers\Usb2Dbg.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>TShell.msi</p></td>
<td align="left"><p>Der Test-Verwaltungsshell eine Reihe von Befehlszeilentools für die Verwendung in der Unterlagen-nach-oben und Testen von einem mobilen Gerät ist. TShell können für Aufgaben wie das Kopieren von Dateien auf dem mobilen Gerät und Protokolle anzeigen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsetupenvironmentvariablesspanspan-idsetupenvironmentvariablesspanstep-4-set-up-environment-variables"></a><span id="set_up_environment_variables"></span><span id="SET_UP_ENVIRONMENT_VARIABLES"></span>Schritt 4: Einrichten von Umgebungsvariablen


Gehen Sie zum Einrichten der Umgebungsvariablen, die für eine funktionsfähige Buildumgebung erforderlich sind.

**Einrichten einer Build-Umgebung in Visual Studio 2015**

1.  Ein **Entwickler für VS2015** Eingabeaufforderungsfenster zu öffnen.

2.  Legen Sie die WPDKCONTENTROOT-Umgebungsvariable auf den Speicherort des Installationsverzeichnisses Windows 10 Mobile Kit.

    -   Für Computer mit einer 32-Bit-Version von Windows, standardmäßig dieser ProgramFiles% ist\\Windows Kits\\10.

        **Legen Sie WPDKCONTENTROOT ProgramFiles% =\\Windows Kits\\10**

    -   Für Computer mit einer 64-Bit-Version von Windows, standardmäßig dies %ProgramFiles(x86)% ist\\Windows Kits\\10.

        **Festlegen von WPDKCONTENTROOT=%ProgramFiles(x86) %\\Windows Kits\\10**

3.  Die WDKCONTENTROOT-Umgebungsvariable auf den Speicherort des Installationsverzeichnisses WDK Kit festgelegt.

    -   Für Computer mit einer 32-Bit-Version von Windows, in der Standardeinstellung dies ProgramFiles% ist\\Windows Kits\\10.

        **Legen Sie WDKCONTENTROOT ProgramFiles% =\\Windows Kits\\10**

    -   Für Computer mit einer 64-Bit-Version von Windows, in der Standardeinstellung dies %ProgramFiles(x86)% ist\\Windows Kits\\10.

        **Legen Sie WDKCONTENTROOT=%ProgramFiles(x86) %\\Windows Kits\\10**

4.  Hinzufügen der X86 Verzeichnis Tools für die Windows-Kits und das Verzeichnis Windows Kit-Tools zur PATH-Umgebungsvariablen.

    **Legen Sie PFAD = PFAD %; WDKCONTENTROOT %\\Bin\\X86; WPDKCONTENTROOT %\\Tools\\Bin\\i386**

## <a name="span-idinstalloemtestcertsspanspan-idinstalloemtestcertsspanspan-idinstalloemtestcertsspanstep-5-install-oem-test-certs"></a><span id="install_OEM_test_certs"></span><span id="install_oem_test_certs"></span><span id="INSTALL_OEM_TEST_CERTS"></span>Schritt 5: Install OEM Test-Zertifikate


Um Binärdateien und Pakete zu signieren, müssen Sie die OEM Testzertifikate installieren.

**OEM-Test Zertifikate installieren.**

-   Führen Sie nach der sicherstellen, dass WPDKCONTENTROOT auf den Pfad des Speicherorts Installation Kit festgelegt ist InstallOEMCerts.cmd mit dem folgenden Befehl ein:

    **WPDKCONTENTROOT %\\Tools\\Bin\\i386\\InstallOEMCerts.cmd**

    Weitere Informationen finden Sie unter [Einrichten der signierenden Umgebung](https://msdn.microsoft.com/library/windows/hardware/dn756804).

 

 



