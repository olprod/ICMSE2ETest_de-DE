---
author: Justinha
Description: DISM Bild Management-Befehlszeilenoptionen
ms.assetid: a6382d83-5748-4b08-9d9a-46ff576bac54
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Bild Management-Befehlszeilenoptionen
ms.openlocfilehash: 82ddf698b02150b0bdc0333f48a8d5c3d12ac671
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-image-management-command-line-options"></a>DISM Bild Management-Befehlszeilenoptionen


Bereitstellung Bild Wartung und Verwaltung (DISM.exe) bindet ein Windows-Abbilddatei (WIM) oder die virtuelle Festplatte (VHD- oder .vhdx) für die Wartung. Sie können auch den Befehl DISM Bild Management verwenden, so Listen Sie die Indexnummern Image zum Überprüfen der Architektur für das Bild, das Sie bereitstellen werden, fügen Sie ein Bild, Anwenden der Schwelle, Erfassen eines Abbilds und Löschen eines Bilds. Nachdem Sie das Bild aktualisieren, müssen Sie es und entweder entladen einen commit oder verwerfen von Änderungen, die Sie vorgenommen haben.

In diesem Thema wird DISM-Befehlen im Zusammenhang mit Image-Verwaltung. Andere Befehlszeilenoptionen finden Sie unter [Deployment Image Servicing and Management (DISM) Command-Line Options](deployment-image-servicing-and-management--dism--command-line-options.md). Weitere Informationen zu gängigen DISM Szenarien finden Sie unter [Was ist DISM?](what-is-dism.md).

Zusätzlich zu das Befehlszeilentool ist DISM mithilfe von Windows PowerShell verfügbar. Weitere Informationen finden Sie unter [Windows PowerShell-Cmdlets Bereitstellung Imaging – Wartung Management (DISM)](http://go.microsoft.com/fwlink/?LinkId=239926).

Die folgenden Befehle können bereitstellen, aufheben, erfassen, angefügt werden soll, und löschen und Abfragen von WIM, VHD- und .vhdx-Dateien verwendet werden. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

## <a name="append-image"></a>/ Append-Bild

Eine WIM-Datei hinzugefügt ein zusätzliches Abbild. **/Append-Image** neue Dateien mit den Ressourcen in der vorhandenen WIM-Datei durch das **/ImageFile** -Argument angegebene vergleicht und speichert nur eine einzige Kopie jeder eindeutigen Datei, sodass jede Datei nur einmal erfasst wird. WIM-Datei kann nur eine zugewiesenen Komprimierungstyp verfügen. Daher können Sie nur Dateien mit dem gleichen Komprimierung anfügen.

Diese Befehlszeilenoption gilt nicht für Dateien virtual Hard Disk (VHD).

**Wichtige**  

Stellen Sie sicher, dass Sie genügend Speicherplatz für die Option **/Append-Image** ausgeführt haben. Wenn Sie nicht genügend Speicherplatz ausführen, während das Bild wird angefügt wird, kann die WIM-Datei beschädigt werden.

Syntax:

``` syntax
DISM.exe /Append-Image /ImageFile:<path_to_image_file> /CaptureDir:<source_directory> /Name:<image_name> [/Description:<image_description>] [/ConfigFile:<configurtion_file.ini>] [/Bootable] /WIMBoot [/CheckIntegrity] [/Verify] [/NoRpFix]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
|   / WIMBoot | Verwenden Sie /WIMBoot, um das Bild mit Windows-Bild-Datei (WIMBoot) Startkonfiguration anzufügen. Dies gilt nur für Windows 8.1 Bilder, die erfasst oder als WIMBoot-Datei exportiert wurden. Dieses Feature ist nicht in Windows 10 unterstützt.|
| / ConfigFile | Gibt den Speicherort einer Konfigurationsdatei, die Listen Ausschlüsse für die abbilderfassung und Befehle komprimieren. Weitere Informationen finden Sie unter [Liste der DISM-Konfiguration und WimScript.ini Dateien](dism-configuration-list-and-wimscriptini-files-winnext.md). |
| / Startbaren | Markiert ein Volume Image als einem startbaren Abbild durchführen. Dieses Argument ist nur für Abbildern Windows Vorinstallation Environment (Windows PE) verfügbar. Nur ein Volume Image kann in einer WIM-Datei als startbaren gekennzeichnet werden.|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / Überprüfen |  Überprüft auf Fehler und doppelter Dateien. |
| / NoRpFix  | Deaktiviert die Analyse Punkt Tag Korrektur an. Analyse ist eine Datei, die einen Link zu einer anderen Datei im Dateisystem enthält. Wenn /NoRpFix nicht angegeben ist, werden neue Punkte, die außerhalb von /ImageFile angegebenen Wert Pfade auflösen, nicht erfasst werden.|

Beispiel:

``` syntax
Dism /Append-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D
```

## <a name="apply-image"></a>/ Anwenden-Bild

Mit diesem Befehl für WIM gilt, eine Windows-Abbilddatei (WIM) oder eine Unterbrechung Windows Bilddateien (.swm) für eine angegebene Partition. Beginnend mit Windows Version 1607 10, DISM anwenden und erweiterten Attribute (EA) erfassen.

Für FFU gilt dieser Befehl eine vollständige flash (.ffu) Updateabbild für ein bestimmtes Laufwerk. Nicht unterstützt ein Bild aus einer Datei virtuelle Festplatte (.vhdx) anwenden, wenn Sie diesen Befehl verwenden können, um ein Vollbild auf einer virtuellen Festplatte anzuwenden. FFU gilt nur für Windows 10.

Diese Option unterstützt keine Anwenden der Schwelle von eine virtual Hard Disk (VHD), obwohl Sie diesen Befehl verwenden können, um Bilder in eine Datei .vhdx anzuwenden, die angefügt, aufgeteilt, und formatiert wurde.

Ausfall Dism /Apply-Image Fehler Code 5, und Sie werden mithilfe von Windows 10 Version 1607 Windows Teilsystem für Linux (WSL) Feature finden Sie [im KB-Artikel 319598](https://support.microsoft.com/kb/3179598).

Argumente für WIM:

``` syntax
DISM.exe /Apply-Image /ImageFile:<path_to_image_file> [/SWMFile:<pattern>] /ApplyDir:<target_directory> {/Index:< image_index> | /Name:<image_name>} [/CheckIntegrity] [/Verify] [/NoRpFix] [/ConfirmTrustedFile] [/WIMBoot (deprecated)] [/Compact] [/EA]
```

Argumente für FFU

``` syntax
DISM.exe /Apply-Image /ImageFile:<path_to_image_file> /ApplyDrive:<target_drive> [/SFUFile:<pattern>] [/SkipPlatformCheck]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet. |
| / Überprüfen | Überprüft auf Fehler und doppelter Dateien. |
| / NoRpFix | Deaktiviert die Analyse Punkt Tag Fehlerbehebung. Analyse ist eine Datei, die eine Verknüpfung zu einer anderen Datei im Dateisystem enthält. Wenn /NoRpFix nicht angegeben ist, werden neue Punkte, die in Pfaden außerhalb von /ImageFile angegebenen Wert aufgelöst werden nicht erfasst werden. |
| / SWMFile | Ermöglicht Ihnen das geteilte WIM-Dateien (SWMs) verweisen. *Muster* ist der Benennungsmuster und Speicherort der Split-Dateien. Sie können auch Platzhalterzeichen angeben. Beispielsweise "E:\image\install.swm" gelten alle Split-Dateien in die E:\image Verzeichnis mit dem Namen install1.swm install2.swm und So weiter. |
| / ConfirmTrustedFile | Überprüft das Bild für vertrauenswürdige Desktop auf einem Windows 10, Windows 8.1 oder Windows 8. Diese Option kann nur ausgeführt werden, auf einem Computer mit mindestens Windows PE 4.0. Wenn Sie mit der Option /ConfirmTrustedFile in Windows PE /Apply-Image verwenden, immer Geben Sie die gezeigt an einem Speicherort Speichermedien/ScratchDir Option an. Dadurch wird sichergestellt, dass die Angabe kurzer Dateinamen immer zur Verfügung stehen. Weitere Informationen zum Standardverhalten der Option/ScratchDir finden Sie unter [DISM globale Optionen für Command-Line Syntax](dism-global-options-for-command-line-syntax.md) . Beginnend mit Windows 10, Version 1607, können HA Sie erweiterte Attribute anwenden.  |
|   / WIMBoot | Verwenden Sie /WIMBoot, um das Bild mit Windows-Bild-Datei (WIMBoot) Startkonfiguration anzufügen. Dies gilt nur für Windows 8.1 Bilder, die erfasst oder als WIMBoot-Datei exportiert wurden. Dieses Feature ist nicht in Windows 10 unterstützt.|
| / Komprimieren | Wendet ein Bild in compact Modus Speicherplatz zu speichern. WIMBoot ersetzt. Für Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) nur. | 
| HA      | Neu in Windows 10 1607 Version. Erweiterte Attribute gilt. |
| / ApplyDrive  | Gibt das logische Laufwerk, verwenden die Geräte-ID an. Wenn die Geräte-ID an der Befehlszeile erhalten möchten, geben Sie "Wmic Laufwerk List kurze". Hinweis: eine virtuellen Festplatte scheint mit dem Namen "PhysicalDrive" in der Beschreibung, beispielsweise \.\PhysicalDrive2.|
| / SFUFile  | Verwenden Sie /SFUFile auf geteilten FFU-Dateien (SFUs) verweisen. *Muster* ist der Benennungsmuster und den Speicherort der Split-Dateien. |
|  / SkipPlatformCheck | Verwenden Sie /SkipPlatformCheck, wenn die FFU-Datei angewendet wird, ein anderes Gerät als das Gerät, auf die Anwendung ausgeführt abgestimmt ist. Eine spezielle FFU Datei ist erforderlich. |

Beispiele für die:

``` syntax
Dism /apply-image /imagefile:install.wim /index:1 /ApplyDir:D:\
```

``` syntax
Dism /apply-image /imagefile:install.swm /swmfile:install.swm /index:1 /applydir:D:
```

``` syntax
DISM.exe /Apply-Ffu /ImageFile:flash.ffu /ApplyDrive:\\.\PhysicalDrive0
```

``` syntax
DISM.exe /Apply-Ffu /ImageFile:flash.sfu /SFUFile:flash*.sfu /ApplyDrive:\\.\PhysicalDrive0
```

## <a name="capture-customimage"></a>/ Capture-CustomImage

Erfasst die inkrementelle Datei Änderungen basierend auf der bestimmten install.wim-Datei in eine neue Datei, die für ein Bild WIMBoot custom.wim. Sie können nicht auf ein leeres Verzeichnis erfassen. Die aufgezeichneten Dateien werden in Zeiger Dateien konvertiert. Die custom.wim wird im selben Ordner neben der install.wim platziert.

**Wichtige**

- / Capture-CustomImage werden nur die Anpassungsdateien erfasst. Es kann nicht verwendet werden, in einer neuen WIM-Installationsdateien erfasst.
- Trennen Sie die Dateien install.wim und custom.wim. Wechseln Sie nicht die Datei custom.wim oder der install.wim-Datei.
- Sie können das benutzerdefinierte Bild nur einmal erfassen. Nicht entfernen oder ein custom.wim nach der Aufzeichnung Ändern der inkrementellen erfassen.

Syntax: 

``` syntax
Dism /Capture-CustomImage /CaptureDir:<source_directory> [/ConfigFile:<configuration_file.ini>] [/CheckIntegrity] [/Verify] [/ConfirmTrustedFile]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / CaptureDir | Gibt das Verzeichnis, das Bild angewendet und angepasst wurde. |
| / ConfigFile | Gibt den Speicherort einer Konfigurationsdatei, die Listen Ausschlüsse für die abbilderfassung und komprimieren Befehle. Weitere Informationen finden Sie unter [Liste der DISM-Konfiguration und WimScript.ini Dateien](dism-configuration-list-and-wimscriptini-files-winnext.md).
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / Überprüfen | Überprüft auf Fehler und doppelter Dateien. |
| [/ConfirmTrustedFile | Überprüft das Bild für vertrauenswürdige Desktop auf einem Windows 10, Windows 8.1 oder Windows 8. Diese Option kann nur ausgeführt werden, auf einem Computer mit mindestens Windows PE 4.0. |

Beispiel:

``` syntax
Dism /Capture-CustomImage /CaptureDir:D:\
```

## <a name="capture-image"></a>/ Capture-Bild

Zeichnet ein Abbild ein Laufwerk, um eine neue WIM-Datei. Aufgezeichnete Verzeichnissen gehören alle Unterordner und Daten. Sie können nicht auf ein leeres Verzeichnis erfassen. Ein Verzeichnis muss mindestens eine Datei enthalten.

Erfassen Sie das Abbild als Windows WIM-Datei oder eine Reihe von Teilen Windows Bilddateien (.swm); Diese Option unterstützt nicht das Erfassen einer Datei virtual Hard Disk (.vhd/.vhdx) oder ein Bild vollständige flash-Update (.ffu). Beginnend mit Windows Version 1607 10, DISM anwenden und erweiterten Attribute (EA) erfassen.

Syntax:

``` syntax
Dism /Capture-Image /ImageFile:<path_to_image_file> /CaptureDir:<source_directory> /Name:<image_name> [/Description:<image_description>]
[/ConfigFile:<configuration_file.ini>] {[/Compress:{max|fast|none}] [/Bootable] | [/WIMBoot]} [/CheckIntegrity] [/Verify] [/NoRpFix] [/EA]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / ConfigFile | Gibt den Speicherort einer Konfigurationsdatei, die Listen Ausschlüsse für die abbilderfassung und Befehle komprimieren. Weitere Informationen finden Sie unter [Liste der DISM-Konfiguration und WimScript.ini Dateien](dism-configuration-list-and-wimscriptini-files-winnext.md).
| / Komprimieren |   Gibt den Typ der Komprimierung verwendet, für den ersten Capture-Vorgang. Die Option **maximum** bietet die beste Komprimierung, aber mehr Zeit zum Erfassen des Abbilds akzeptiert. Die Option **fast** bietet schnellere bildkomprimierung, aber die daraus resultierenden Dateien sind größer als die Option maximum mit komprimiert. Dies ist auch die Komprimierung Standardtyp, der verwendet wird, wenn Sie nicht das Argument angeben. Die Option **keine** Komprimieren das erfasste Bild nicht überhaupt. |
| / Startbaren | Markiert ein Volume Image als einem startbaren Abbild durchführen. Dieses Argument ist nur für Windows PE-Abbilder verfügbar. Nur ein Volume Image kann in einer WIM-Datei als startbaren gekennzeichnet werden.|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / Überprüfen | Überprüft auf Fehler und doppelter Dateien. |
| / NoRpFix  | Deaktiviert die Analyse Punkt Tag Korrektur an. Analyse ist eine Datei, die einen Link zu einer anderen Datei im Dateisystem enthält. Wenn /NoRpFix nicht angegeben ist, werden neue Punkte, die außerhalb von /ImageFile angegebenen Wert Pfade auflösen, nicht erfasst werden.|
|   / WIMBoot | Verwenden Sie /WIMBoot, um das Bild mit Windows-Bild-Datei (WIMBoot) Startkonfiguration anzufügen. Dies gilt nur für Windows 8.1 Bilder, die erfasst oder als WIMBoot-Datei exportiert wurden. Dieses Feature ist nicht in Windows 10 unterstützt.|
| HA      | Neu in Windows 10 1607 Version. Erweiterte Attribute erfasst. Die Option muss explizit angegeben werden, um erweiterte Attribute zu erfassen. DISM erfasst die erweiterte-Attribute Bits, wenn sie in den Komponenten festgelegt sind, das in der WIM-Abbild aufgezeichnet werden. Wenn keine Bits festgelegt sind, nicht DISM sie gesetzt. Nur die Posteingang Komponenten der CAB-Paketen und Treibern müssen diese erweiterte Attribut Bits, nicht den AppX Paketkomponenten oder Win32-Anwendungskomponenten. Erweiterte Attribute mit dem Präfix "$Kernel". im Feld Name wird übersprungen, da nur erweiterte Attribute Benutzermodus werden erfasst. Wenn Sie in Windows 10 DISM verwenden, Version 1607 auf Erweiterte Attribute erfassen und mit einer früheren Version von DISM auf das Bild, die Operation erfolgreich jedoch die erweiterten Attribute werden nicht auf das Bild angewendete festgelegt werden.  |

Beispiele für die:

``` syntax
Dism /Capture-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D
```

```syntax
dism /Capture-Image /CaptureDir:C:\ /ImageFile:"C:\WindowsWithOffice.wim" /Name:"Chinese Traditional" /ea
```

## <a name="cleanup-mountpoints"></a>/ Cleanup-Bereitstellungspunkte

Löscht alle Ressourcen zugeordnet einer bereitgestellten Bild, das beschädigt ist. Mit diesem Befehl wird nicht deaktiviert werden Bilder, die bereits bereitgestellt werden, noch werden Bilder, die mit dem Befehl **/Remount-Image** wiederhergestellt werden können gelöscht. 

Beispiel: 

``` syntax
Dism /Cleanup-Mountpoints
```

Weitere Informationen finden Sie unter [Reparieren einer Windows-Abbild](repair-a-windows-image.md)

## <a name="commit-image"></a>/ Commit-Bild

Wendet die Änderungen, die Sie auf das bereitgestellte Abbild vorgenommen haben. Das Bild bleibt eingebundene, bis die Option **/Unmount-Image** verwendet wird.

Syntax:

``` syntax
Dism /Commit-Image /MountDir:<path_to_mount_directory> [/CheckIntegrity] [/Append]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / Fügen Sie   |  Fügt das geänderte Abbild der vorhandenen WIM-Datei anstelle des Originalbilds überschreiben. Die /CheckIntegrity und/Append Argumente gelten nicht für virtuelle Festplatte (VHD) Dateien. |

Beispiel: 

``` syntax
Dism /Commit-Image /MountDir:C:\test\offline
```

## <a name="delete-image"></a>/ Delete-Bild

Löscht das angegebene Volume Image aus einer WIM-Datei, die mehrere Volumeabbilder enthält. Diese Option wird nur der Metadaten und XML-Einträge gelöscht. Die Streamdaten werden nicht gelöscht, und die WIM-Datei wird nicht optimiert.

Diese Befehlszeilenoption gilt nicht für Dateien virtual Hard Disk (VHD).

Syntax:

``` syntax
Dism /Delete-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>} [/CheckIntegrity]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |

Beispiel: 

``` syntax
Dism /Delete-Image /ImageFile:install.wim /Index:1
```

## <a name="export-image"></a>/ Export-Bild

Exportiert eine Kopie des angegebenen Bilds in einer anderen Datei. Die Quell- und Ziel-Dateien müssen die Art der gleichen Komprimierung verwenden. Sie können auch ein Bild optimieren, indem Sie in eine neue Abbilddatei exportieren. Wenn Sie ein Abbild ändern, speichert DISM zusätzliche Ressourcendateien, die die Gesamtgröße des Bilds erhöht. Exportieren des Abbilds werden nicht benötigte Ressourcendateien entfernt.

Diese Befehlszeilenoption gilt nicht für Dateien virtual Hard Disk (VHD).

Syntax:

``` syntax
Dism /Export-Image /SourceImageFile:<path_to_image_file> {/SourceIndex:<image_index> | /SourceName:<image_name>} /DestinationImageFile:<path_to_image_file> [/DestinationName:<Name>] [/Compress:{fast|max|none|recovery}] [/Bootable] [/WIMBoot] [/CheckIntegrity]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
|  / SWMFile     |  Ermöglicht Ihnen das Verweisen auf geteilte WIM-Dateien. Muster ist der Benennungsmuster und den Speicherort der Split-Dateien. Sie können auch Platzhalterzeichen angeben. "E:\image\install*.swm" wird beispielsweise die Split-Dateien in die E:\image exportieren Verzeichnis mit dem Namen install1.swm install2.swm und So weiter.|
| / Komprimieren | Gibt den Typ der Komprimierung verwendet, für den ersten Capture-Vorgang. Das Argument /Compress wird nicht angewendet, wenn Sie ein Bild in eine vorhandene WIM-Datei zu exportieren, Sie können dieses Argument nur verwenden, wenn Sie ein Bild in eine neue WIM-Datei zu exportieren. Die Option **maximum** bietet die beste Komprimierung, aber benötigt mehr Zeit zum Erfassen des Abbilds. Die Option **fast** bietet schnellere bildkomprimierung, aber die daraus resultierenden Dateien sind größer als mithilfe die Option **maximum** komprimiert. Dies ist auch die Komprimierung Standardtyp, der verwendet wird, wenn Sie nicht das Argument angeben. Verwenden Sie die Option **Recovery** Drucktaste zurücksetzen Bilder exportieren. Die daraus resultierenden Dateien sind viel kleiner Größe, die wiederum erheblich den reduzieren benötigter Speicherplatz für das Speichern des Drucktaste zurücksetzen auf einem Wiederherstellungslaufwerk. Die Zieldatei muss mit der Erweiterung .esd angegeben werden. Die Option **keine** Komprimieren das erfasste Bild nicht überhaupt. |
| / Startbaren | Markiert ein Volume Image als einem startbaren Abbild durchführen. Dieses Argument ist nur für Windows PE-Abbilder verfügbar. Nur ein Volume Image kann in einer WIM-Datei als startbaren gekennzeichnet werden.|
|   / WIMBoot | Verwenden Sie /WIMBoot, um das Bild mit Windows-Bild-Datei (WIMBoot) Startkonfiguration anzufügen. Dies gilt nur für Windows 8.1 Bilder, die erfasst oder als WIMBoot-Datei exportiert wurden. Dieses Feature ist nicht in Windows 10 unterstützt.|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |

Beispiel: 

``` syntax
Dism /Export-Image /SourceImageFile:install.wim /SourceIndex:1 /DestinationImageFile:install2.wim
```

## <a name="get-mountedimageinfo"></a>/ Get-MountedImageInfo

Listen der Bilder, die derzeit bereitgestellten und Informationen zu den bereitgestellten Abbild wie gibt an, ob das Bild gültig ist Lese-/Schreibzugriff Berechtigungen, Mount-Speicherort, bereitgestellter Dateipfad und bereitgestellten Abbildindex.

Beispiel: 

``` syntax
Dism /Get-MountedImageInfo
```

## <a name="get-imageinfo"></a>/ Get-ImageInfo

Zeigt Informationen zu den Bildern, die in der Datei WIM-, Vhd oder .vhdx enthalten sind. Bei Verwendung mit der/Index oder Name-Argument Informationen über das angegebene Bild wird angezeigt, wenn ein Bild ein Bild WIMBoot ist, wenn das Bild Windows 8.1 ist, finden Sie unter Inventar eines Bilds oder einer Komponente mithilfe von DISM dauern. Das Argument/Name gilt nicht für VHD-Dateien. Sie müssen die/Index: 1 für VHD-Dateien angeben.

Syntax: 

``` syntax
Dism /Get-ImageInfo /ImageFile:<path_to_image.wim> [{/Index:<Image_index> | /Name:<Image_name>}]
```

Beispiele für die: 

``` syntax
Dism /Get-ImageInfo /ImageFile:C:\test\offline\install.wim
```

``` syntax
Dism /Get-ImageInfo /ImageFile:C:\test\images\myimage.vhd /Index:1
```

## <a name="get-wimbootentry"></a>/ Get-WIMBootEntry

Verwenden Sie /Get-WIMBootEntry WIMBoot Konfigurationseinträge für den angegebenen Datenträger angezeigt.

Weitere Informationen dazu, wie Sie WIMBoot Konfigurationseinträge angezeigt werden finden Sie unter Inventory eines Bilds oder einer Komponente mithilfe von DISM dauern.

Dies gilt nur für Windows 8.1; Dieses Feature ist nicht in Windows 10 unterstützt.

Syntax:

``` syntax
Dism /Get-WIMBootEntry /Path:<volume_path>
```

Beispiel: 

``` syntax
Dism /Get-WIMBootEntry /Path:C:\
```

## <a name="list-image"></a>/-Liste-Bild

Eine Liste der Dateien und Ordner in ein angegebenes Bild angezeigt.

Diese Befehlszeilenoption gilt nicht für Dateien virtual Hard Disk (VHD).

Syntax:

``` syntax
Dism /List-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>}
```

Beispiel: 

``` syntax
Dism /List-Image /ImageFile:install.wim /Index:1
```

## <a name="mount-image"></a>/ Mount-Bild

Bindet ein Bild aus einer Datei WIM-, VHD- oder .vhdx auf das angegebene Verzeichnis, damit es zum Warten verfügbar ist. Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine WIM-Datei angeben. 

Syntax:

``` syntax
Dism /Mount-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>} /MountDir:<path_to_mount_directory> [/ReadOnly] [/Optimize] [/CheckIntegrity]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / ReadOnly  | Legt das bereitgestellte Abbild Leseberechtigungen fest. Optional |
| / Optimieren |   Reduziert die anfängliche Mount-Zeit. |
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |

Beispiele für die: 

``` syntax
Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
```

``` syntax
Dism /Mount-Image /ImageFile:C:\test\images\myimage.vhd /index:1 /MountDir:C:\test\offline /ReadOnly
```

## <a name="optimize-image-wimboot"></a>/ /WIMBoot optimieren-Bild

Führt zu einem offline-Abbild angegebene Konfigurationen.

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / WIMBoot  | Konfigurieren Sie ein offline Bild für die Installation auf einem Windows Bild Dateisystem Boot (WIMBoot). |
| / Optimieren |   Reduziert die anfängliche Mount-Zeit. / Optimieren-Bild /WIMBoot betrifft nur Windows 8.1 Bilder, die erfasst oder als WIMBoot-Datei exportiert wurden. Verwenden Sie nur /Optimize-Image mit Bildern, die für WIMBoot unterstützt Systeme verwendet werden. Wenn /Optimize-Image mit einem WIMBoot nicht unterstützte System Image verwendet wird, funktioniert Windows möglicherweise nicht wie erwartet, nach der Installation auf einem Gerät WIMBoot nicht unterstützt. |

Beispiel: 

``` syntax
Dism /Image:C:\test\offline /Optimize-Image /WIMBoot
```

## <a name="remount-image"></a>/ Erneute Bereitstellung-Bild

Stellt wieder bereit, ein bereitgestelltes Abbild, kann nicht zugegriffen werden, die für die Wartung zur Verfügung gestellt.

Syntax: 

``` syntax
Dism /Remount-Image /MountDir:<path_to_mount_directory>
```

Beispiel:

``` syntax
Dism /Remount-Image /MountDir:C:\test\offline
```

## <a name="split-image"></a>/ Split-Bild

Für WIM wird mit diesem Befehl eine vorhandenen WIM-Datei in mehrere Read-only aufgeteilten SVM-Dateien aufgeteilt.

Diese Option erstellt die SVM-Dateien im angegebenen Verzeichnis naming jede Datei dieselbe als die angegebene *Path_to_swm*, wobei jedoch eine angefügte Nummer. Wenn Sie festlegen, dass *Path_to_swm* als beispielsweise `c:\Data.swm`, diese Option erstellt eine Data.swm-Datei, eine Datei Data2.swm, eine Datei Data3.swm und usw., Definieren jeder Teil der geteilten WIM-Datei und speichern sie in das Verzeichnis C:\.

Diese Befehlszeilenoption gilt nicht für Dateien virtual Hard Disk (VHD).

Für FFU wird mit diesem Befehl eine vorhandenen Updatedatei vollständig Flash (.ffu) in mehrere schreibgeschützt geteilten .sfu Dateien aufgeteilt.

Die Option /Split-Ffu gilt nur für Windows-10 für desktop-Editionen.

Diese Option werden die .sfu Dateien im angegebenen Verzeichnis naming jede Datei dieselbe als die angegebenen /SFUFile, wobei jedoch eine angefügte Anzahl erstellt. Wenn Sie verwenden, beispielsweise `c:\flash.sfu`, erhalten Sie eine Datei flash.sfu, eine flash2.ffu-Datei, eine Datei flash3.sfu und usw., Definieren jeder Teil der geteilten .sfu-Datei und speichern Sie es in das Verzeichnis C:\.

Die Syntax für WIM:

``` syntax
Dism /Split-Image /ImageFile:<path_to_image_file> /SWMFile:<path_to_swm> /FileSize:<MB-Size> [/CheckIntegrity]
```

Die Syntax für FFU:

``` syntax
Dism /Split-Ffu /ImageFile:<path_to_image_file> /SFUFile:<pattern> /FileSize:<MB-Size>
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / FileSize     | Gibt die maximale Größe in Megabyte (MB) für jede erstellte Datei an. Wenn eine einzelne Datei größer als der Wert in der Option /FileSize, eine der geteilten .swm Dateien Ergebnisse größer als der Wert in der Option /FileSize ist, um die große Datei aufzunehmen angegeben werden.  |
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / ImageFile  | Gibt den Pfad der ein. Datei unter dem Namen FFU Beispiel: flash.ffu. |
|  / SFUFile  | Verweise Aufteilen von FFU-Dateien (SFUs). *Muster* ist der Benennungsmuster und Speicherort der Split-Dateien.

Beispiele für die:

``` syntax
Dism /Split-Image /ImageFile:install.wim /SWMFile:split.swm /FileSize:650
```

``` syntax
DISM.exe /Split-Ffu /ImageFile:flash.ffu /SFUFile:flash.sfu /FileSize:650
```

## <a name="unmount-image"></a>/ Entladen-Bild 

Hebt die Bereitstellung der WIM-, VHD- oder .vhdx-Datei und entweder führt ein Commit oder verwirft die Änderungen, die vorgenommen wurden, wenn das Abbild bereitgestellt wurde.

Sie müssen dieses oder /discard Argument verwenden, wenn Sie die Option /Unmount-Image verwenden.

Syntax: 

``` syntax
Dism /Unmount-Image /MountDir:<path_to_mount_directory> {/Commit | /Discard} [/CheckIntegrity] [/Append]
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / CheckIntegrity | Erkennt und verfolgt WIM-Datei eine Beschädigung bei Verwendung mit Capture heben Sie die Bereitstellung, exportieren und Vorgänge zu übernehmen. / CheckIntegrity beendet den Vorgang, wenn DISM erkennt, dass die WIM-Datei beschädigt ist, wenn mit übernehmen und Mount-Operationen verwendet wird. |
| / Fügen Sie   |  Fügt das geänderte Abbild der vorhandenen WIM-Datei anstelle des Originalbilds überschreiben. Die /CheckIntegrity und/Append Argumente gelten nicht für virtuelle Festplatte (VHD) Dateien. |

Beispiele für die:

``` syntax
Dism /Unmount-Image /MountDir:C:\test\offline /commit
```

``` syntax
Dism /Unmount-Image /MountDir:C:\test\offline /discard
```

## <a name="update-wimbootentry"></a>/ Update-WIMBootEntry

Aktualisiert den Eintrag WIMBoot Konfiguration, die angegebenen Data Source-ID zugeordnet, mit der Bilddatei umbenannte oder verschobene Image-Dateipfad.

**Hinweis:** **/Update-WIMBootEntry** erfordert einen Neustart angezeigt, in der Reihenfolge für alle Updates wirksam wird.

Syntax:

```
Dism /Update-WIMBootEntry /Path:<Volume_path> /DataSourceID:<Data_source_id> /ImageFile:<Renamed_image_path>
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / Pfad | Gibt den Datenträger der WIMBoot Konfiguration. |
|  / DataSourceID  | Gibt die Datenquellen-ID an, wie Sie von /Get-WIMBootEntry angezeigt. |

Beispiel:

``` syntax
DISM.exe /Update-WIMBootEntry /Path:C:\ /DataSourceID:0 /ImageFile:R:\Install.wim
```

## <a name="apply-siloedpackage"></a>/ Anwenden-SiloedPackage

Wendet eine oder mehrere Silo provisioning Pakete (SPPs) zu einem angegebenen Bild. Diese Option ist nur verfügbar, nach der ADK für Windows 10, Version 1607, CopyDandI.cmd verlaufende und Ausführen von ``` dism.exe /Apply-SiloedPackage ``` aus den Zielordner durch CopyDandI.cmd erstellt. 

**Hinweis:** **/Apply-SiloedPackage** kann nur einmal für ein Windows-Abbild ausgeführt werden, **jedoch/PackagePath** können in demselben Befehl nur einmal verwendet, um mehrere SPPs anwenden. SPPs werden in der angegebenen Reihenfolge aus, damit eine Abhängigkeit vor der SPP angegeben werden sollte, die davon abhängigen angewendet. 

Weitere Informationen über Silo provisioning Pakete und wie Sie CopyDandI.cmd verwenden, finden Sie unter [provisioning Pakete in Silos zusammengefasst.](siloed-provisioning-packages.md)

Erfahren Sie, wie zum Arbeiten mit Silo provisioning-Paketen finden Sie unter [Übung 12: Hinzufügen von desktopanwendungen und mit Einstellungen in Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md).

``` Syntax
/Apply-SiloedPackage /PackagePath:<package_path> /ImagePath:<applied_image_path>
```

|  Parameter   | Beschreibung  |
|--------------|--------------|
| / PackagePath | Gibt den Pfad einer Silo provisioning Package-Datei. |
| / Image   | Gibt den Pfad des Windows-Abbilds, auf dem Sie den spp anwenden |

Beispiel:

``` syntax
Dism.exe /apply-SiloedPackage /PackagePath:C:\test\Word.spp /PackagePath:C:\test\spp2.spp /ImagePath:C:\
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[Was ist DISM?](what-is-dism.md)

[DISM globale Optionen für Befehlszeilensyntax](dism-global-options-for-command-line-syntax.md)

[Bereitstellen von Windows mithilfe der vollständigen Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md)

[WIM im Vergleich zu VHD im Vergleich zu FFU: Bilddateiformate vergleichen](wim-vs-ffu-image-file-formats.md)
