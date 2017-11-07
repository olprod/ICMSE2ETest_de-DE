---
author: Justinha
Description: Bereitstellung von Paketen in Silos zusammengefasst
MSHAttr: PreferredLib:/library/windows/hardware
title: Silo provisioning Pakete
ms.openlocfilehash: 95c68d004ab972c9403bbd6fc78d4c6196b17992
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="siloed-provisioning-packages"></a>Bereitstellen von Lösungspaketen in Silos zusammengefasst

Silo provisioning Pakete sind eine neue Art von Bereitstellung-Paket, das für Windows 10 1607 Version verfügbar ist. Bei traditionellen provisioning Pakete erfassen können alle klassische Windows-Anwendungen und Einstellungen, die mit einem Windows-Abbild installiert sind, ein Silo provisioning Paket kann erfassen klassische Windows-Clientanwendungen einzeln Treiber plus Applications, Einstellungen oder Capture-Add-Ons für die Bereitstellung der Pakete, die zuvor erfasst wurden. Dies bietet mehr Flexibilität für den Fertigungsprozess und reduziert die erforderliche Zeit zum Erstellen von Windows-basierten Computer in der Factory.

## <a name="performance-comparison"></a>Leistungsvergleich

Die folgende Tabelle zeigt einen Vergleich zwischen der Verwendung der Office Installer Vs Silo provisioning Pakete in einem typischen Factory Floor-Prozess verwenden.  Beim Installieren von Office, die Basis Office En Pakete mithilfe der Silo Bereitstellung von-uns Verpacken, zusammen mit der Add-On Office fr-fr und de-de-Pakete für Office werden mit dem User State Migration Tool (USMT) ScanState.exe-Dienstprogramm als einmaligen Vorgang in der imaging Übungseinheit erfasst.
Die Daten in der folgenden Tabelle wurde von einer Stichprobe führen Sie auf einen virtuellen Computer mit Windows 10, Version 1607 Desktopimage abgeleitet.  Die tatsächliche Uhrzeit, die einsparungen auf werksseitige variiert basierend auf der Anzahl und Größe des zu installierenden Anwendungen und der Hardware Spezifikation der physischen Geräte.  Die Zeitersparnis kann durch berechnet werden:

(Zeit zu Sysprep & starten im Überwachungsmodus + Zeit auf Installieren Clientanwendungen + Anwendungen in einer PPKG erfasst Zeit + _< optional_> Zeit, um eine Instanz der PPKG) – (Zeit Sysprep & Boot im Überwachungsmodus SPPs + Zeit zuweisen)

| Phase/Aufgabe | Mithilfe von Office-Installer-Factory-Prozess | Mit Silo provisioning-Paketen-Factory-Prozess |
|------------|----------------------------------------|----------------------------------------------------|
| Bild auf das Gerät anwenden | min 4.                  | 4 min.                                             |
| Installieren von Sprachpaketen – fr-fr & de-de | 20 min.    | min 20.                                            |
| Führen Sie BCDBoot.exe | unerheblich                        | unerheblich                                         |
| Führen Sie DISM Silo Office En anwenden, um-Basis us, Office fr-fr und de-de-Pakete für Office | n/v | min 3.       |
| Führen Sie Sysprep & im Überwachungsmodus starten |10 Minuten.           | 19 min.                                            |
| Installieren von Office 2016 En-us, fr-fr & de-de | 12 min. | n/v                                                |
| Führen Sie zum Office in provisioning-Paket (für PBR) erfassen ScanState | 10 Minuten. | n/v                      |
| (Optional – für wenig Speicherplatz) Single instancing Office-Dateien in das Paket provisioning erfasst | 7 min. | n/v |
| **Insgesamt**  | **56-63 min.**                         | **46 min.**                                        |
| **Zeitpunkt der gesamten Anwendung Installation** |              | **45 65 % schneller**                                  |
| **Gesamtdauer der E2E-Bereitstellung** |                   | **18-30 % schneller**                                  |

## <a name="capturing-a-siloed-provisioning-package"></a>Das Erfassen eines Silo provisioning-Pakets

USMT ScanState.exe wurde verbessert, um eine einzelne klassischen Windows-Anwendung zu erfassen und erfasst nur die Komponenten aus dem Windows-Namespace. Eine Konfigurationsdatei kann angegeben werden, um die Komponenten, die erfasst werden, wenn Sie eine einzelne klassische Windows-Anwendung aufzeichnen einzuschränken. Eine Standardkonfigurationsdatei für diesen Zweck wird im Windows-ADK bereitgestellt, die im folgenden Ordner nachlesen können bei der Installation von USMT:

*< % Windows ADK installieren Stamm % >*\User Migrationstools\\*< Bogen*> \Config_AppsOnly.xml

Mit dieser Konfigurationsdatei kann zum Erfassen von mehr oder weniger Komponenten im Paket Silo Bereitstellung angepasst werden. Mit dieser Konfigurationsdatei ist in einer Übungseinheit imaging nützlich, wenn Sie nur die app-Dateien und die Einstellungen für eine einzelne Win32-app, ohne andere Einstellungen nicht relevant erfassen möchten. 

Hinweis: Es wird empfohlen beginnen immer mit einer Neuinstallation von Windows und nur Installieren einer Anwendung in einem Silo provisioning Paket erfassen. In dieser Methode wird verhindert, dass Sie unerwünschten Einstellungen im Paket einbezogen wird. 

Im folgende Beispiel zeichnet ein Silo provisioning Paket einer einzelnen klassischen Windows-Anwendung, die auf einem Gerät Verweis installiert:

```syntax
ScanState.exe /apps:-sysdrive /o /v:13 /config:Config_AppsOnly.xml /ppkg e:\repository\office16_base.spp
```

In der folgenden Tabelle werden einige der Parameter erläutert.

<table border="1" cellspacing="0" cellpadding="0">
    <tbody>
        <tr>
            <td width="96" valign="top">
                <p>
Parameter </p>
            </td>
            <td width="528" valign="top">
                <p>
Beschreibung </p>
            </td>
        </tr>
        <tr>
            <td width="96" valign="top">
                <p>
-Sysdrive (oder + Sysdrive) </p>
            </td>
            <td width="528" valign="top">
                <p>
Erfahren Sie mehr ScanState alle Ordner außerhalb des Windows-Namespaces ignoriert. Beispielsweise ist ein Ordner c:\Folder, der Ordner wird aufgezeichnet werden bei Ausführung mit /apps (oder /apps: + Sysdrive), aber es wird nicht aufgezeichnet werden, wenn mit /apps ausgeführt:-Sysdrive.
                    <br/>
In der Regel verwenden Sie + packen Sysdrive, wenn Sie den gesamten Zustand des Computers in einer einzelnen Silo provisioning erfassen möchten. Verwenden Sie - Sysdrive, wenn Sie eine einzelne Anwendung (oder eine kleine Gruppe von Clientanwendungen) erfassen möchten.
                </p>
                <p>
Der Windows-Namespace ist der Satz von Ordnern in der Regel von einer Windows-Installation erstellt: </p>
                <ul>
                    <li>
%SystemDrive%\Users </li>
                    <li>
%SystemDrive%\ProgramData </li>
                    <li>
%SystemDrive%\Programme\Microsoft-Dateien </li>
                    <li>
%SystemDrive%\Programme\Microsoft Dateien (x86) </li>
                    <li>
%SystemDrive%\Windows </li>
                    <li>
%SystemDrive%\Inetpub </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td width="96" valign="top">
                <p>
/ o </p>
            </td>
            <td width="528" valign="top">
                <p>
Überschreibt vorhandenen Daten im Speicher. Wenn nicht angegeben ist, schlägt ScanState fehl, wenn der Speicher bereits Daten enthält.
                </p>
            </td>
        </tr>
        <tr>
            <td width="96" valign="top">
                <p>
/v:13 </p>
            </td>
            <td width="528" valign="top">
                <p>
Erstellt eine MigLog.xml-Datei, die angibt, was ruft erfasst.
                </p>
            </td>
        </tr>
    </tbody>
</table>

Ein Schalter/diff kann mit der Befehlszeilenoption /apps Add-on Anwendungskomponenten relativ zum übergeordneten Applikationen bereits im Silo provisioning Pakete erfasst erfasst verwendet werden. Beispiel:

```syntax
ScanState.exe /apps:-sysdrive /o /v:13 /config:Config_AppsOnly.xml /diff:e:\repository\office16_base.spp /ppkg e:\repository\office16_fr-fr.spp
```

Eine andere Konfigurationsdatei in Windows ADK kann nur in einem Silo provisioning Paket Systemeinstellungen erfasst, ohne eine beliebige Anwendung Nutzlast erfassen verwendet werden.  Mit dieser Konfigurationsdatei eignet sich für die Erfassung von nur Systemeinstellungen als letzten Schritt in der Floor-Factory-Prozess, damit das Paket in den Ordner für die Wiederherstellung auf dem Gerät platziert werden kann.  Während der Wiederherstellung verarbeitet PBR das Silo provisioning-Paket in den Ordner für die Wiederherstellung im Paket erfassten Systemeinstellungen wiederherstellen.  

Die standardmäßige Konfigurationsdatei kann in den folgenden Ordner gefunden werden, bei der Installation von USMT.  Mit dieser Konfigurationsdatei kann auch angepasst.

*< % Windows ADK installieren Stamm % >*\User Migrationstools\\*< Bogen*> \Config_SettingsOnly.xml

Im folgende Beispiel zeichnet ein Silo provisioning Paket nur Systemeinstellungen auf einem Gerät:

```syntax
ScanState.exe /apps:-appfiles /o /v:13 /config:Config_SettingsOnly.xml /ppkg %systemdrive\Recovery\Customizations\systemsettings.spp
```

Angenommen Sie, dass in der Fabrik alle Bereitstellungsaufgaben für ein Gerät fertig sind und keine Win32 apps installiert wurden. ScanState kann nur die Systemeinstellungen erfassen, die nicht in allen app .spp Dateien erfasst wurden mithilfe von Config_SettingsOnly.xml. Das Silo provisioning-Paket kann im Ordner "Wiederherstellung" Wiederherstellung diese Einstellungen während PBR platziert werden.

Es gibt auch eine dritte Standardkonfigurationsdatei:

*< % Windows ADK installieren Stamm % >*\User Migrationstools\\*< Bogen*> \Config_AppsAndSettingsOnly.xml

Mit dieser Konfigurationsdatei ist auch anpassbar und kurzfristige erfasst beabsichtigten Win32-apps und Systemeinstellungen in einer .spp oder .ppkg installiert und in den Ordner für die Wiederherstellung für die Verwendung von PBR zu platzieren. 

Angenommen Sie, dass nach einem Gerät im Überwachungsmodus werksseitige gestartet wird, ein paar weitere Win32-apps installiert werden und erfasst werden müssen. In diesem Fall stehen zwei Optionen zur Verfügung:

- Erfassen Sie die zusätzliche apps und die entsprechenden Einstellungen in eine .spp mit der Befehlszeilenoption/diff und Config_AppsOnly.xml. Klicken Sie dann capture in einem separaten .spp mithilfe der Config_SettingsOnly.xml mit dem Befehl ScanState Systemeinstellungen.
- Erfassen Sie die zusätzliche apps und die Systemeinstellungen in einem mit der Befehlszeilenoption/diff und Config_AppsAndSettings.xml SPP an.

Ein weiteres Beispiel für die Verwendung der Datei Config_AppsAndSettingsOnly.xml ist, wo Sie alle apps und -Einstellungen in eine .spp-Datei, in dem imaging Labor oder werksseitige erfassen möchten. 

## <a name="applying-a-siloed-provisioning-package"></a>Anwenden eines Silo provisioning-Pakets

DISM wird auch zur Unterstützung der anwenden Silo provisioning Pakete auf einem Windows-Abbild, die auf einem Gerät angewendet wurde verbessert.  Ein neuer DISM-Anbieter, der nur in Windows ADK verfügbar ist, unterstützt Silo provisioning Pakete.  Für Windows 10 1607 Version, ist die einzige unterstützte Funktionalität Silo provisioning Pakete anwenden. 

Die Funktionalität für die Anwendung Silo provisioning Paketen mithilfe von DISM beträgt die folgenden Szenarien unterstützt:

- Die DISM SiloedPackageProvider ist nicht im Windows-Abbild enthalten noch in Windows PE 1607 Version enthalten.  Die Windows-ADK-Version von DISM muss installiert sein, auf dem Host zum Warten, und klicken Sie dann starten aus der Windows-ADK DISM.exe Speicherort installiert.  Auf einem Host, der von ADK Windows Installer, wie Windows PE nicht unterstützt wird die erforderlichen Binärdateien kopiert werden können, mit dem Host mit dem Skript CopyDandI.cmd in *< % Windows ADK installieren Stamm % > \Deployment Tools*.
- DISM unterstützt nur anwenden Silo provisioning Pakete zu einem Windows-Abbild, die im Stammverzeichnis des ein Datenträgervolume auf einem Gerät, z. B. "C:\" angewendet wurde.  Es wird nicht unterstützt, anwenden Silo provisioning Pakete auf einem Windows-Abbild, die für die Wartung offline bereitgestellt ist.  Herkömmliches Szenario ist Gerät, um Windows PE starten und die Windows ADK-Version von DISM in Windows PE Silo provisioning Pakete anwenden, nachdem das Windows-Abbild auf das Gerät angewendet wurde.
- Der Befehl DISM Silo provisioning Pakete auf einem Windows-Abbild (DISM übernehmen SiloedPackage) anwenden kann nur einmal ausgeführt werden.  Alle Silo provisioning Pakete auf das Windows-Abbild angewendet werden muss in der richtigen Reihenfolge in einem einzigen Befehlsvorgang angegeben werden. Die Reihenfolge der Installation wird beibehalten werden, damit die Pakete während PBR in der gleichen Reihenfolge wiederhergestellt werden können.
- Wenn zusätzliche Silo provisioning Pakete müssen zu einem Windows-desktop-Abbild angewendet werden, die bereits über den gesamten Bereitstellungsprozess bei der Verwendung von DISM eine Reihe von Silo provisioning Pakete anwenden versetzt wurde, kann das Bild Sysprep allgemeiner (engl.) und als ein neues Modell Bild erfasst sein.  DISM kann dann erneut ausgeführt werden, um mehr Silo provisioning Pakete anwenden, wenn dieses neue Modell Abbild auf anderen Geräten bereitgestellt wird.
- Silo provisioning Pakete müssen auf der gleichen Architektur angewendet werden, denen sie auf erfasst wurden. Zum Erfassen einer X86 wird nicht unterstützt-app in ein .spp und Zuweisen einer X64 Plattform. 
- Silo provisioning Pakete können auf eine andere Version von Windows angewendet werden. Beispielsweise kann eine Anwendung auf Windows 10 Enterprise erfasst auf Windows 10 Pro angewendet werden.
- Windows-10, Version 1607, unterstützt anwenden Silo provisioning Pakete auf eine allgemeine Übersicht über Bild, die zum Starten im Überwachungsmodus festgelegt wird nicht. Wenn das Starten im Überwachungsmodus erforderlich ist, verwenden Sie Unattend.xml im Überwachungsmodus erneut versiegeln ein.

Das folgende Beispiel startet DISM in Windows PE anzuwendende Silo provisioning-Pakete für Office-En-us, fr-fr und de-de angewendeten Windows-Abbild auf einem Gerät:

```syntax
C:\ADKTools\DISM.exe /Apply-SiloedPackage /ImagePath:C:\ /PackagePath:e:\repository\office16_base.spp /PackagePath:e:\repository\office16_fr-fr.spp /PackagePath:e:\repository\office16_de-de.spp
```

Informationen zur Syntax [DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)finden Sie unter oder ausführen ``` DISM.exe /Apply-SiloedPackage /? ``` aus den Zielspeicherort der CopyDandI.cmd. 

Alle Silo provisioning Pakete vom DISM angewendeten wird im Ordner %systemdrive%\Recovery\Customizations platziert werden.  

Wenn DISM Silo provisioning Pakete für das Betriebssystemabbild, die auf einem Gerät als Compact OS angewendet wurde gilt, werden standardmäßig die Pakete mit Anwendungsdateien Einzelinstanz-(mit WIMBoot v1 Formatvorlage) angewendet, um den Speicherplatz auf dem Gerät zu speichern.  Auf einem Gerät ohne ein Compact Betriebssystemabbild kann DISM /Apply-CustomDataImage Befehl während das Gerät mit Windows PE Einzel-Instanz die angewendete Silo provisioning Pakete gestartet wird ausgeführt werden. Beispiel:

```syntax
DISM.exe /Apply-CustomDataImage /ImagePath:C:\ /CustomDataImage:C:\Recovery\Customizations\myApp.spp /SingleInstance 
```

Der Befehl /Apply-SiloedPackage kann auch mit .ppkg Dateien arbeiten, und Sie können Silo provisioning Pakete zusätzlich zu einer herkömmlichen provisioning Paket anwenden. 

## <a name="push-button-reset"></a>Drucktaste zurücksetzen

Wenn Sie ScanState mit herkömmlichen provisioning Pakete erfassen, kann nur ein Paket mit den Anwendungen und Systemeinstellungen im Ordner %systemdrive%\Recovery\Customizations platziert werden.  Während der Drucktaste zurücksetzen (PBR) wird der einzelnen provisioning Paket bereit, um die Anwendungen und Systemeinstellungen wiederherzustellen verarbeitet.

Beginnend mit Windows 10, Version 1607, Applikationen können aufgezeichnet werden in mehreren Silo provisioning-Paketen und Systemeinstellungen können auch in einem separaten Silo provisioning Paket erfasst werden. Daher ist PBR können mehrere Silo provisioning Pakete angewendet werden in der sie mithilfe von Dism Apply-Siloed Paket angewendet wurden, in der Reihenfolge beibehalten erweitert. Die Pakete können in die Warteschlange gestellt und während PBR zum Wiederherstellen der Applications und in diese Pakete erfasst Systemeinstellungen in der richtigen Reihenfolge verarbeitet werden. Die Pakete mit Single instancing angewendet wurden, werden berücksichtigt werden beim PBR an dem Gerät wiederhergestellt. 

Single instancing automatisch auftreten kann, wenn Compact OS verwendet wird, oder manuell. 

- Wenn Sie Windows PE und dann Anwenden eines Bilds als Compact OS verwenden, klicken Sie dann zuweisen SPPs, Windows automatisch den Inhalt des Pakets Single-Instanzen. Weitere Informationen finden Sie unter [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md)
- Wenn Sie provisioning Pakete im Überwachungsmodus erstellen, können Sie Einzel-Instanz den Inhalt auswählen, mithilfe des DISM /Apply-CustomDataImage /SingleInstance-Befehls. Weitere Informationen finden Sie unter [Übung 9: Ändern von Windows (Überwachungsmodus)](prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md).

## <a name="copy-script"></a>Kopieren Sie Skript

Um die Silo provisioning Package-Funktionalität auf einer Hostplattform wie Windows PE abzurufen, die vom Installationsprogramm Windows ADK nicht unterstützt wird, Tool, das in mehreren Ordnern unter Windows ADK ScanState.exe und DISM.exe erforderliche Binärdateien kopiert werden müssen Speicherort auf einem anderen unterstützten Host installieren.  Zur Erleichterung des Kopiervorgangs ist ein Skript in der Windows-ADK bereitgestellt, die in den folgenden Ordner bei der Installation von Bereitstellungstools Kategorie gefunden wird:

*< % Windows ADK installieren Stamm % >*\Deployment Tools\CopyDandI.cmd

Beispiel für die erforderlichen Tools für die amd64-Architektur in einen Ordner auf einem austauschbaren Laufwerk E: Kopieren\:

```syntax
CopyDandI.cmd amd64 D:\ADKTools
```
Bevor Sie das Tool verwenden, müssen Sie die Tools ADK erneut auf ein nicht austauschbaren Laufwerk, auf dem Zielgerät zu kopieren. Kopieren die Datei an einen Speicherort nicht entfernbar vermeidet Fehler zugeordnet DISM von Wechseldatenträgern installieren.

```syntax
xcopy D:\ADKTools\ W:\ADKTools\ /s
```

Sie müssen die Verwaltungstools installiert:
```syntax
W:\ADKTools\amd64\WimMountAdkSetupAmd64.exe /Install /q
```

Und führen Sie die Tools von diesem Speicherort:
```syntax
W:\ADKTools\amd64\DISM.exe /Apply-SiloedPackage /ImagePath:C:\ /PackagePath:e:\repository\office16_base.spp /PackagePath:e:\repository\office16_fr-fr.spp /PackagePath:e:\repository\office16_de-de.spp
```

Die vollständige Exemplarische Vorgehensweise finden Sie unter [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md)

## <a name="scenarios-for-using-siloed-provisioning-packages"></a>Szenarien für die Verwendung in Silos zusammengefasst provisioning Pakete

In diesem Abschnitt werden die Szenarien zum Aufzeichnen und Anwenden von Silo provisioning Pakete behandelt. 

### <a name="capturing-and-applying-independent-applications"></a>Aufzeichnen und Anwenden von unabhängigen Applikationen

Microsoft-Partner kann Silo provisioning Pakete während in dem imaging Labor einzelne klassischen Windows-Anwendung erfassen, und dann eine beliebige Kombination von Silo provisioning Pakete in einer benutzerdefinierten Reihenfolge unter werksseitige installieren.  Beispielsweise konnte Partner Silo provisioning-Pakete für Office 2016, Adobe Acrobat Reader und AVG Schutz erfassen, und installieren Sie Office 2016 und AVG Protection-Pakete für ein bestimmtes Gerätemodell unter werksseitige.

![Übung für die Erfassung von unabhängigen Applications Imaging](images/imaging-lab-for-capturing-independent-applications.png)

1.  Installieren Sie Windows 10, Version 1607 auf einem Gerät Verweis.
2.  Installieren Sie Office 2016, auf dem Desktop.
3.  Ausführen von ScanState.exe zum Erfassen von Office 2016 Silo provisioning Paket.
4.  Wischen Sie und installieren Sie das Gerät Verweis
5.  Wiederholen Sie Schritte 2 bis 4 für Adobe Acrobat Reader und AVG-Schutz.

Alternativ können die Silo provisioning Pakete über eine VM anstatt ein physisches Gerät erfasst werden:

1.  Erstellen Sie einen virtuellen Computer, und starten Sie es online mit einer Windows-10, Version 1607 VHD/VHDX Bild.
2.  Erstellen eines Kontrollpunkts von der Neuinstallation des Betriebssystems auf dem virtuellen Computer.
3.  Installieren Sie Office 2016, auf dem Desktop.
4.  Ausführen von ScanState.exe zum Erfassen von Office 2016 Silo provisioning Paket.
5.  Die VM des Prüfpunkts zurückkehren.
6.  Installieren Sie Adobe Acrobat Reader, auf dem Desktop.
7.  Ausführen von ScanState.exe zum Erfassen von Adobe Acrobat Reader Silo provisioning-Paket.
8.  Wiederholen Sie Schritt 5 bis 7 AVG Protection Silo provisioning Paket erfasst.

![Zum Anwenden von unabhängigen Applications Fabrik](images/factory-floor-for-applying-independent-applications.png)

1.  Klicken Sie auf das Zielgerät Windows PE starten, und das Fenster 10, Version 1607 Desktopimage anwenden.
2.  Klicken Sie in Windows PE Befehl DISM /Apply-SiloedPackage mit Office 2016 und AVG Protection Pakete, die Dateien der Anwendung in die Pakete auf der angewendeten Desktopimage anwenden.
3.  Führen Sie den Rest der Anpassungsaufgaben offline.
4.  Durchläuft ersten Start und Ausführen bis specialize im Überwachungsmodus abrufen.
5.  Führen Sie die Aufgaben online Anpassung-Konfiguration.
6.  (Optional) Führen Sie im Überwachungsmodus, ScanState, um nur die Systemeinstellungen in Silo provisioning Paket erfassen und speichern Sie sie in den Ordner für die Wiederherstellung.
7.  Führen Sie die restlichen Factory Floor Aufgaben und Herunterfahren-Siegel-Produkts.

### <a name="capturing-and-applying-applications-with-dependencies"></a>Aufzeichnen und Anwenden von Clientanwendungen mit Abhängigkeiten 

Microsoft-Partner können die Diff Capture Support zur zusätzlichen generieren (oder Add-on) provisioning Pakete, die für eine zuvor aufgezeichnete übergeordneten Silo provisioning-Paket von Bedeutung sind in Silos zusammengefasst.  Die Silo provisioning Pakete können mit übergeordneten Paket zuerst gefolgt von Kombinationen von zusätzlichen Pakete in der angepassten Reihenfolge klicken Sie dann auf Geräten unter Fabrik, installiert werden. Beispiel:

- Sie konnte AVG Schutz Silo provisioning Basisversion, erfassen und dann aufnehmen Diff AVG Schutz Patchdateien (MSP) in Silos zusammengefasst provisioning Pakete mit der Basisversion als übergeordnetes Element.  Unter der Fabrik können der Basisversion AVG-Schutz und eine Auswahl von Patch-Pakete in der gewünschten Reihenfolge angegeben klicken Sie dann auf ein bestimmtes Modell Gerät installiert werden.
- Oder Sie erfassen konnte, Office 2016 En-us als die Basis Silo Bereitstellung packen, und klicken Sie dann Diff Capture-Bereitstellung in anderen Sprachen von Office 2016 Silos zusammengefasst verpackt mithilfe des Basis-Pakets.  Unter Factory können Floor, das Office 2016 Basis-Paket und eine selektive Language Packs in beliebiger Reihenfolge angegeben klicken Sie dann auf ein bestimmtes Modell Gerät installiert werden.

![Das Erfassen eines Silo provisioning-Pakets für die Basis-Anwendung](images/capturing-base-app-spp.png)

![Eine Option für das Aufzeichnen eines Silo provisioning-Pakets für ein Add-on-app](images/capturing-add-on-app-spp-option-one.png)

![Option 2 für das Aufzeichnen eines Silo provisioning-Pakets für ein Add-on-app](images/capturing-add-on-app-spp-option-two.png)

1.  Installieren Sie Fenster 10, Version 1607 auf einem Gerät Verweis.
2.  Installieren Sie auf dem Desktop Office 2016 En-us.
3.  Sysprep verallgemeinern und erfassen Sie das Abbild OS vom Gerät Verweis.
4.  Ausführen von ScanState.exe zum Erfassen von Office 2016 En-us Silo provisioning Paket basieren.
5.  Installieren Sie Office 2016 fr-fr.
6.  Ausführen von ScanState.exe Diff Capture Office 2016 fr-fr Silo provisioning Paket mit Office 2016 Basis-Paket
7.  Fortfahren Sie die bereits erfassten Base und Sprachpakete auf eine andere Office 2016 Silo provisioning Sprachpaket erfassen die Option Diff mit:
    1. Installieren Sie Office 2016 de-de.
    2. Ausführen von ScanState.exe Diff Capture Office 2016 de-de Silo provisioning Paket mit Office 2016 Basisversion und fr-fr-Paket.
8. Oder Remotegerätzurücksetzung und Start clean erneut auf dem Gerät Verweis zu erfassen einer anderen Office 2016 Silo provisioning Sprachpaket:
    1. Wischen Sie, und installieren Sie das Verweis Gerät mithilfe der in Schritt 3 erfasst Betriebssystemabbilds.
    2. Installieren Sie auf dem Desktop Office 2016 de-de.
    3. Ausführen von ScanState.exe Diff Capture Office 2016 de-de Silo provisioning Paket mit Office 2016 Basisversion in Schritt 4 erfasst.
9. Wiederholen Sie Schritt 7 oder 8, wenn Sie den Rest der Office 2016 Sprache in Silos zusammengefasst provisioning Pakete zu erfassen.

Alternativ können die Silo provisioning Pakete über VM anstatt ein physisches Gerät erfasst werden.  Wenn Sie einen virtuellen Computer verwenden:

1.  Erstellen eines virtuellen Computers und online mit einem Fenster 10, Version 1607 VHD/VHDX Bild zu starten.
2.  Installieren Sie auf dem Desktop Office 2016 En-us.
3.  Erstellen ein Prüfpunkts (auch bekannt als Snapshot) der OS Installation mit Office 2016 En-us auf dem virtuellen Computer.
4.  Ausführen von ScanState.exe zum Erfassen von Office 2016 En-us Silo provisioning Paket basieren.
5.  Installieren Sie Office 2016 fr-fr an.
6.  Ausführen von ScanState.exe Diff Capture Office 2016 fr-fr Silo provisioning Paket, mithilfe des Office-2016-Basis-Pakets als Referenz.
7.  Fortzusetzen, die bereits erfassten Base und Sprachpakete auf eine andere Office 2016 Silo provisioning Sprachpaket erfassen Diff-Switch mit:
    1. Installieren Sie Office 2016 de-de.
    2. Ausführen von ScanState.exe bis Diff Capture Office 2016 Silos de-de provisioning-Pakets mithilfe des Office-2016 Basis-Pakets und fr-fr Paket zusammengefasst.
8.  Oder Neustart der VM zu einer anderen Office 2016 Silo provisioning Sprachpaket erfassen:
    1. Zurücksetzen der VM des Prüfpunkts in Schritt 3 generiert.
    2. Installieren Sie Office 2016 de-de, auf dem Desktop.
    3. Ausführen von ScanState.exe Diff Capture Office 2016 de-de Silo provisioning Paket mithilfe des Basis Office 2016-Pakets in Schritt 4 erfasst.
9.  Wiederholen Sie Schritt 7 oder 8, wenn Sie den Rest der Office 2016 Sprache in Silos zusammengefasst provisioning Pakete zu erfassen.

Silo provisioning Pakete können auch Clientanwendungen mit Abhängigkeiten erfassen. Wenn Sie beispielsweise mehrere apps zu erfassen, die auf .NET Framework basieren:

1.  Erstellen eines virtuellen Computers und online mit einem Fenster 10, Version 1607 VHD/VHDX Bild zu starten.
2.  Installieren von .NET Framework. 
3.  Erstellen ein Kontrollpunkts von der der OS Installation mit .NET Framework.
4.  Erfassen einer Basis .spp, beispielsweise DotNet.spp.
5.  Installieren Sie App1, erfassen Sie es als App1.spp, /diff:DotNet.spp verwenden.
6.  Zurückkehren Sie die VM, die in Schritt 3 erstellte Prüfpunkt.
7.  Installieren Sie App2, erfassen Sie es als App2.spp, /diff:DotNet.spp verwenden.

Um die Abhängigkeit zu erhalten, gelten Sie die Pakete in dieser Reihenfolge:

- DotNet.spp, App1.spp, App2.spp

\endash oder \endash

- DotNet.spp, App2.spp, App1.spp

Wichtig ist, dass DotNet.spp zuerst angewendet werden muss. 

### <a name="capturing-and-applying-applications-for-bto-model"></a>Aufzeichnen und Anwenden von Anwendungen für BTO-Modell

Im Modell BTO konnte die letzte Minute Anpassungen an der Fabrik enthalten Installieren von der klassischen Windows-Anwendungen auf der Basis was bereits im Basiskalender Modell-Abbild installiert wurden.  Wenn alle klassischen Windows-Anwendungen, die nicht in einer Bereitstellung Silo Paketen in dem imaging Labor erfasst wurden vorhanden sind, werden die Aufgaben, die in der folgenden Abbildung dargestellt Floor-Factory-Prozess aufgenommen.

![Aufzeichnen und Anwenden von Anwendungen für Bto-Modell](images/capturing-and-applying-applications-for-bto-model.png)

1.  Klicken Sie auf das Zielgerät Windows PE starten, und Fenster 10, Version 1607 Desktopimage anwenden.
2.  Klicken Sie in Windows PE führen Sie DISM /Apply-SiloedPackage Befehl alle Silo provisioning Pakete Anwendungsdateien in den Paketen auf der angewendeten Desktopimage anwenden.
3.  Führen Sie den Rest der Anpassungsaufgaben offline.
4.  Durchläuft ersten Start und Ausführen bis specialize im Überwachungsmodus abrufen.
5.  Installieren Sie online in Überwachungsmodus klassischen Windows-Anwendung.
6.  Führen Sie die Aufgaben online Anpassung-Konfiguration.
7.  Ausführen ScanState.exe zu erfassen die Anwendungen installiert, die in Schritt 5 in einem einzigen Silo provisioning Paket von Silo provisioning Pakete für die Anwendungen im Modell Basis Bild als Referenz bereits installiert.
8.  (Optional) Führen Sie ScanState, um nur die Systemeinstellungen in Silo provisioning Paket erfassen und speichern Sie sie in den Ordner für die Wiederherstellung aus.
9.  (Optional) Starten Sie das Gerät zu Windows PE, und führen Sie dem DISM-Befehl aus, um eine Instanz der Anwendungsdateien im Silo provisioning-Paket in Schritt 7 erfasst.
10. Führen Sie die restlichen Factory Floor Aufgaben und Herunterfahren-Siegel-des Produkts.

**Bevorzugte Prozess Richtlinien für BTO Modell**: wie in den vorherigen Schritten beschrieben, die Diff Capture-Unterstützung flexibel, um ermöglichen eine klassische Windows Applications Fabrik als letzte Minute Anpassungen zu installieren. Die Aufnahme Vergleichsvorgang kann jedoch einige Zeit in Anspruch, je nach Anzahl und die Größe der Silo provisioning Pakete auf Diff gegen benötigten, dauern. Es gibt auch Gemeinkosten für die anderen Schritte im Prozess. Daher ist die bevorzugte Richtlinie für die Installation von einer klassischen Windows-Anwendung im Modell BTO die einmalige Kosten für das Aufzeichnen der Silo provisioning-Pakete für diese Anwendung in der imaging Übungseinheit erforderlich war. Dann können sie bei Bedarf für die kurzfristige Anpassungen werksseitige angewendet werden.   
