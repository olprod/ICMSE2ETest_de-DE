---
author: Justinha
Description: "Windows-10 enthält Tools, damit Sie weniger Speicherplatz verwenden."
ms.assetid: f58ee9cf-0dd1-4c46-9b1f-d16891247f2f
MSHAttr: PreferredLib:/library/windows/hardware
title: Kompakte OS, Single instancing und Bild-Optimierung
ms.openlocfilehash: 30860699b5024a6437d913d375129f05100007e7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="compact-os-single-instancing-and-image-optimization"></a>Kompakte OS, Single instancing und Bild-Optimierung


Windows-10 enthält Tools, damit Sie weniger Speicherplatz verwenden. Sie können jetzt die Dateien für das gesamte Betriebssystem, einschließlich Ihrer vorinstallierte desktopanwendungen komprimieren. Compact OS ermöglicht Ihnen das Ausführen des Betriebssystems aus komprimierte Dateien (analog zu WIMBoot in Windows 8.1 Update 1) und Single instancing können Sie Ihre vorinstallierte Windows desktopanwendungen komprimierte Dateien ausführen. Die neue Prozesse hilft bei minimalem Speicherbedarf über einen Zeitraum verwalten, indem Sie einzelnen Dateien, statt einer WIM-Datei zu kombinieren.

Nachfolgend finden Sie einige Methoden, die das Bild zu reduzieren, das Bild, und einige Aspekte bei der Bereitstellung für kostengünstige Geräte zu optimieren.

## <a name="span-iddeploymenttoolsthathelpsavespacespanspan-iddeploymenttoolsthathelpsavespacespanspan-iddeploymenttoolsthathelpsavespacespandeployment-tools-that-help-save-space"></a><span id="Deployment_tools_that_help_save_space"></span><span id="deployment_tools_that_help_save_space"></span><span id="DEPLOYMENT_TOOLS_THAT_HELP_SAVE_SPACE"></span>Bereitstellungstools unterstützen Speicherplatz


### <a name="span-idcompactosspanspan-idcompactosspanspan-idcompactosspancompact-os"></a><span id="Compact_OS"></span><span id="compact_os"></span><span id="COMPACT_OS"></span>Compact OS

Compact Betriebssystem installiert die Dateien des Betriebssystems als komprimierter Dateien. Compact Betriebssystem wird auf UEFI-basierten sowohl BIOS-basierten Geräten unterstützt.

Im Gegensatz zu WIMBoot da die Dateien nicht mehr in einer einzigen WIM-Datei kombiniert werden kann Windows Update ersetzen oder entfernen einzelne Dateien bei Bedarf zur Erhaltung der Speicherbedarf Laufwerk über einen Zeitraum.

**Hinweis**  Bei der Ausführung von Windows Imaging und Konfiguration Designer (ICD) auf einem Computer mit einer früheren Version von Windows, wie beispielsweise Windows 8.1, müssen Sie [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803) mit Windows ICD und - **Bereitstellungstools** Features zu installieren. Dadurch wird installiert die aktuellen Versionen der Treiber erforderliche DISM (wimmount.sys und adkwof.sys) verwendet, um Bilder Compact OS erstellen.

 

**Zum Bereitstellen von Compact OS mit einem startbaren USB-Laufwerk**

1.  Öffnen Sie auf Ihrem PC Techniker Windows ICD und erstellen Sie das Projekt.
2.  Schließen Sie ein USB-Laufwerk, und notieren Sie den Laufwerkbuchstaben (Beispiel: D:).
3.  Klicken Sie auf **Erstellen** &gt; **Produktion Media** &gt; **WIM** &gt; **OS Dateikomprimierung aktivieren: Ja** &gt; **nächsten** &gt; **startbare USB-Laufwerk** &gt; Laufwerkbuchstaben (d) &gt; **Next** &gt; **Build**.
4.  Starten Sie den Ziel-PC mithilfe des USB-Laufwerks. Windows wird automatisch installiert.

**Zum Bereitstellen von Compact OS mithilfe einer WIM-Datei**

1.  Erstellen Sie eine Auslagerungsdatei in Windows PE gleich 256 MB.

    ``` syntax
    Wpeutil createpagefile C:\pagefile /size=256
    ```

    Dabei ist "C" die Windows-Partition.

2.  Ihr Zielgerät mit der Windows-10-Version von Windows PE zu starten. (Um eine frühere Version von Windows PE verwenden, stellen Sie sicher, dass Sie die Windows-10-Version von DISM verwenden. Weitere Informationen finden Sie finden Sie unter [DISM auf einen anderen Computer kopieren](copy-dism-to-another-computer.md).)
3.  Formatieren und Vorbereiten von Partitionen und dann das Bild in eine Partition mit der Option DISM übernehmen-Image/Compact anwenden:

    ``` syntax
    DISM /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:D:\ /compact
    ```

    Dies erfolgt normalerweise durch ein Bereitstellungsskript ausführen. Finden Sie weitere Informationen finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

**Zum Bereitstellen von Compact OS aus einem FFU-Bild**

1.  Für die Bereitstellung ein FFU Bilds als komprimierte muss das ursprüngliche FFU Bild als komprimierten Bild erstellt werden.

    Windows ICD, klicken Sie auf **Create** &gt; **Produktion Media** &gt; **FFU** &gt; **OS Dateikomprimierung aktivieren: Ja** &gt; nennen Sie die Datei, z. B. D:\\flash.ffu &gt; **Erstellen**.

2.  Sie können das Bild FFU direkt auf einem Laufwerk von Windows ICD oder von Windows Vorinstallation Environment (Windows PE) bereitstellen. Finden Sie weitere Informationen finden Sie unter [Bereitstellen von Windows verwenden vollständige Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md).

**Zum Bereitstellen von Compact OS aus Windows Setup**

-   Verwenden Sie eine unattend.xml-Datei mit der Einstellung: Einrichten von Microsoft Windows\\ImageInstall\\OSImage\\[Compact](https://msdn.microsoft.com/library/windows/hardware/dn949267).

**Command-Line-Unterstützung** In der nächsten Version von Windows-10 und Windows PE können Sie Abfragen, ob das Betriebssystem Compact OS ausgeführt wird, und ändern Sie es zu einem beliebigen Zeitpunkt mit dem [Compact.exe]( http://go.microsoft.com/fwlink/?LinkId=623487) Befehl.

**Windows PE zu bestimmen, ob das Betriebssystem komprimiert wird:**


``` syntax
Compact.exe /CompactOS:Query /WinDir:E:\Windows
```

Wobei E:\\Windows ist der Ordner, in dem Windows installiert wurde.

**Ändern Sie aus einer online-Installation von nicht komprimiert komprimierte Betriebssystem:**


``` syntax
Compact.exe /CompactOS:always
```

### <a name="span-idsingle-instancingofprovisioningpackagesspanspan-idsingle-instancingofprovisioningpackagesspanspan-idsingle-instancingofprovisioningpackagesspansingle-instancing-of-provisioning-packages"></a><span id="Single-instancing_of_provisioning_packages"></span><span id="single-instancing_of_provisioning_packages"></span><span id="SINGLE-INSTANCING_OF_PROVISIONING_PACKAGES"></span>Single instancing von provisioning Pakete

Für Windows 10 beim Hinzufügen von neuer Windows-desktopanwendungen auf einem Gerät, benötigen Sie diese Änderungen in einem komprimierten provisioning Paket für die Verwendung durch die automatische Wiederherstellungstools erfassen. Statt die Originaldateien und die Bereitstellung Paket aufbewahren, können Sie DISM verwenden, entfernen Sie die ursprünglichen Dateien und Ausführen von direkt aus dem komprimierten provisioning Paket stattdessen. Dies wird als das Bild Single instancing bezeichnet.

Obwohl Single instancing Solid-State-Laufwerke und Rotation Laufwerke, aus Gründen der Systemleistung unterstützt wird empfehlen wir, dass einzelne Instanzen nur auf Geräten mit Solid-State-Laufwerke verwendet wird.

Beispiel:

``` syntax
DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
```

Dabei ist *C* der Laufwerkbuchstabe des Windows-Partition.

**Warnung**  Stellen Sie nicht Anführungszeichen durch die /ImagePath:C:\\ Option.

Sie können bestimmen, ob eine Bereitstellung Paket (.ppkg) Einzelinstanz-mithilfe von fsutil.exe ist:

``` syntax
fsutil.exe wim enumwims C:
```

Dabei ist *C* das Laufwerk mit der Bereitstellung Paket. Ausgabe des Befehls wird jedes Einzelinstanz-Bereitstellung Paket auf dem Laufwerk aufgeführt. Mit dem Befehl wird zurückgegeben, wenn keine Fehler vorliegen, "Fehler: des Systems angegebene Datei kann nicht gefunden werden."

### <a name="span-idimageoptimizationspanspan-idimageoptimizationspanspan-idimageoptimizationspanimage-optimization"></a><span id="Image_optimization"></span><span id="image_optimization"></span><span id="IMAGE_OPTIMIZATION"></span>Bild-Optimierung

Nach dem Anwenden einer Windows-Updates image Cleanup das Bild, und klicken Sie dann in eine neue Datei zu exportieren:

``` syntax
md c:\mount\Windows
md C:\mount\temp

Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:C:\mount\Windows

Dism /Cleanup-Image /Image=C:\mount\Windows /StartComponentCleanup /ResetBase /ScratchDir:C:\mount\temp

Dism /Unmount-Image /MountDir:C:\mount\Windows /Commit

Dism /Export-Image /SourceImageFile:C:\Images\install.wim /SourceIndex:1 /DestinationImageFile:C:\Images\install_cleaned.wim
```

dabei *C:\\Bilder\\install.wim* ist eine Windows-Bilddatei, die Sie aktualisieren möchten. Beginnend mit Windows 10, Version 1607, optional können Sie den Parameter /Defer mit /ResetBase langer Cleanup Vorgänge mit der nächsten automatische Wartung verzögern angeben, aber es wird ausdrücklich empfohlen, **nur** /Defer als Option in der Factory, in denen DISM /ResetBase erfordert mehr als 30 Minuten, verwenden. 

## <a name="span-idsizerequirementsandconsiderationsspanspan-idsizerequirementsandconsiderationsspanspan-idsizerequirementsandconsiderationsspansize-requirements-and-considerations"></a><span id="Size_requirements_and_considerations"></span><span id="size_requirements_and_considerations"></span><span id="SIZE_REQUIREMENTS_AND_CONSIDERATIONS"></span>Größe und-Überlegungen


Sie müssen weiterhin minimale Größe der Festplatte, RAM, Ressource: Einsatz Anwendung und Datenspeicher erfüllen.

### <a name="span-idharddrivespanspan-idharddrivespanspan-idharddrivespanhard-drive"></a><span id="Hard_Drive"></span><span id="hard_drive"></span><span id="HARD_DRIVE"></span>Festplatte

Windows-10 erfordert mindestens 16 Gigabyte (GB) Speicherplatz auf 32-Bit-Geräte und 20 GB auf 64-Bit-Geräte.

Obwohl einige Konfigurationen von Windows auf kleinere Laufwerke angepasst wird, bei der Erstinstallation Windows angezeigt werden können, sind 8 GB SSDs nicht groß genug. Selbst wenn ein Benutzer eine 8 GB-Festplatte mit einem zweiten Laufwerk-Paaren, die 4 GB oder mehr für Anwendung und Daten-Dateispeicher, 8 GB-Festplatten nicht für die Anhebung der Arbeitsspeicherbedarf Windows zulassen, die möglicherweise auftreten, wenn Benutzer auf ihrem Computer arbeiten.

Einige der wichtigsten Gründe für die Anhebung der über einen Zeitraum in der Arbeitsspeicherbedarf zählen folgende:

-   **– Wartung**. Freier Festplattenspeicher muss für Softwarepatches für das Betriebssystem und für Service Pack-Versionen reserviert werden.
-   **Wiederherstellungspunkte System**. Windows wird automatisch Wiederherstellungspunkte generieren. Den Abstand an, die standardmäßig erforderlich ist ist relativ zu der Größe der Festplatte. Weitere Informationen zu Wiederherstellungspunkte finden Sie unter dem Thema [Wiederherstellungspunkte](http://go.microsoft.com/fwlink/?LinkId=142170) auf MSDN.
    **Hinweis**   Benutzer können den Speicherplatz auf dem Computer für die Wiederherstellung mithilfe der Benutzeroberfläche **System Protection** (Sysdm.cpl) im Dialogfeld **Systemeigenschaften** verwendet anpassen. Benutzer können auch Sicherungskopien System verwenden, die auf eine externe Festplatte zum Wiederherstellen von einem System gespeichert sind.

-   **Protokolle und Caches**. Das Betriebssystem speichert Dateien wie Ereignis- und Fehlerprotokolle, die auf dem Laufwerk.

### <a name="span-idramspanspan-idramspanram"></a><span id="RAM"></span><span id="ram"></span>RAM

Die Dateien Pagefile.sys und Hiberfil.sys Größe direkt proportional zu der Größe des Arbeitsspeichers auf dem Computer erhöhen. Windows-Installationen auf 16 GB-Festplatten müssen weniger Speicherbedarf aus, wenn der Computer maximal 1 GB RAM ist. Erhöhte Größe der Systemdateien und weniger Speicherplatz auf der Festplatte für andere Programme und Dateien führt ein Anstieg auf eine Größe, die größer als 1 GB RAM. Erhöhen die Größe der Festplatte, beeinflusst jedoch nicht die Größe der diese Systemdateien.

### <a name="span-idapplicationsspanspan-idapplicationsspanspan-idapplicationsspanapplications"></a><span id="Applications_"></span><span id="applications_"></span><span id="APPLICATIONS_"></span>Anwendungen

Softwareanwendungen, die auf dem Computer installiert sind, können zusätzlichen Speicherplatz für Caches, Protokolle und Updates erfordern. Speicherplatz muss auch auf dem Laufwerk, temporäre Anstieg der Ressourcenverwendung berücksichtigt werden während der Installation von Anwendungen, Patches und Updates verfügbar sein.

### <a name="span-iduserdataspanspan-iduserdataspanspan-iduserdataspanuser-data"></a><span id="User_Data"></span><span id="user_data"></span><span id="USER_DATA"></span>Benutzerdaten

Auf Computer, die Wechselmedium zu unterstützen, wie beispielsweise einer SD-Karte oder USB flash-Laufwerk, können Benutzer auf einfache Weise persönliche Daten Dateispeicher für Benutzerdokumente erweitern, mithilfe dieser Wechselmedium. Jedoch wird empfohlen, dass Benutzer einige Speicherplatz auf der Festplatte für diese Typen von Dateien zu reservieren.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows Imaging und Konfiguration-Designer](https://msdn.microsoft.com/library/windows/hardware/dn916113)

[Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

 

 






