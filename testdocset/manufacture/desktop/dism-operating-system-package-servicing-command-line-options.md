---
author: Justinha
Description: DISM Betriebssystem-Paket (CAB-Dateien oder MSU)-Befehlszeilenoptionen zum Warten
ms.assetid: ddb5f223-1c65-4380-95eb-316918e880fc
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Betriebssystem-Paket (CAB-Dateien oder MSU)-Befehlszeilenoptionen zum Warten
ms.openlocfilehash: 78d2240f0557b77875509a3c1ab5e55dda2b6aab
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-operating-system-package-cab-or-msu-servicing-command-line-options"></a>DISM Betriebssystem-Paket (CAB-Dateien oder MSU) Befehlszeilenoptionen zum Warten


Zum Installieren oder Entfernen von Updates, Servicepacks, Language Packs und zum Aktivieren oder Deaktivieren der Windows-Features mithilfe von DISM mit Windows CAB- oder Windows Update Standalone-Installer (MSU)-Dateien. Features sind optionale Komponenten für das Kern-Betriebssystem. 

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax

``` syntax
DISM.exe {/Image:<path_to_image_directory> | /Online} [dism_global_options] {servicing_option} [<servicing_argument>]
```

Die folgenden Betriebssystem zum Warten von Paketen Optionen sind für ein offline-Abbild verfügbar:

``` syntax
DISM.exe /Image:<path_to_image_directory> [/Get-Packages | /Get-PackageInfo | /Add-Package | /Remove-Package ] [/Get-Features | /Get-FeatureInfo | /Enable-Feature | /Disable-Feature ] [/Cleanup-Image]
```

Folgende Betriebssystem zum Warten von Paketen Optionen stehen für ein Betriebssystem ausgeführt wird:

``` syntax
DISM.exe /Online [/Get-Packages | /Get-PackageInfo | /Add-Package | /Remove-Package ] [/Get-Features | /Get-FeatureInfo | /Enable-Feature | /Disable-Feature ] [/Cleanup-Image]
```

## <a name="span-idoperatingsystempackage-servicingoptionsspanspan-idoperatingsystempackage-servicingoptionsspanspan-idoperatingsystempackage-servicingoptionsspanoperating-system-package-servicing-options"></a><span id="Operating_system_package-servicing_options"></span><span id="operating_system_package-servicing_options"></span><span id="OPERATING_SYSTEM_PACKAGE-SERVICING_OPTIONS"></span>Betriebssystem zum Warten von Paketen Optionen

In diesem Abschnitt wird beschrieben, wie Sie jede Betriebssystem-Option zum Warten von Paketen. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ Get-Help /?

Wenn sofort nach einer Befehlszeilenoption zum Warten von Paketen verwendet wird, werden Informationen zur Option und zu den Argumenten angezeigt.

Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild angegeben wird.

Syntax:

``` syntax
Dism /Get-Help 
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Add-Package /?
```

``` syntax
Dism /Online /Get-Packages /?
```

### <a name="span-idget-packagesformattablelistspanspan-idget-packagesformattablelistspanspan-idget-packagesformattablelistspanget-packages"></a><span id="_Get-Packages___Format__Table___List__"></span><span id="_get-packages___format__table___list__"></span><span id="_GET-PACKAGES___FORMAT__TABLE___LIST__"></span>/ Get-Pakete 

Grundlegende Informationen zu allen Paketen im Bild angezeigt. Verwenden Sie das Argument Standardausgabeformat oder/Format: List, um die Ausgabe als Tabelle oder einer Liste anzuzeigen.

Syntax:

``` syntax
Dism /Get-Packages [/Format:{Table | List}]
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Get-Packages
```

``` syntax
Dism /Image:C:\test\offline /Get-Packages /Format:Table
```

``` syntax
Dism /Online /Get-Packages
```

### <a name="span-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanspan-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanspan-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanget-packageinfo"></a><span id="_Get-PackageInfo___PackageName___name_in_image_____PackagePath___path_to_cabfile__"></span><span id="_get-packageinfo___packagename___name_in_image_____packagepath___path_to_cabfile__"></span><span id="_GET-PACKAGEINFO___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE__"></span>/ Get-PackageInfo 

Zeigt ausführliche Informationen zu einem Paket als eine CAB-Datei bereitgestellt. CAB-Dateien können angegeben werden. Sie können diesen Befehl um Paketinformationen für MSU-Dateien zu erhalten. / PackagePath kann einer CAB-Datei oder einen Ordner verweisen.

Sie können mithilfe der Option/Get-Packages den Namen des Pakets im Bild oder Sie können den Pfad zu der CAB-Datei angeben. Der Pfad zu der CAB-Datei sollten verweisen auf die ursprüngliche Quelle des Pakets, nicht jedoch zum, in dem die Datei auf offline-Abbild installiert ist.

Syntax:

``` syntax
Dism /Get-PackageInfo {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Get-PackageInfo /PackagePath:C:\packages\package.cab
```

``` syntax
Dism /Image:C:\test\offline /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanspan-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanspan-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanadd-package"></a><span id="_Add-Package__PackagePath___path_to_cabfile____IgnoreCheck_____PreventPending_"></span><span id="_add-package__packagepath___path_to_cabfile____ignorecheck_____preventpending_"></span><span id="_ADD-PACKAGE__PACKAGEPATH___PATH_TO_CABFILE____IGNORECHECK_____PREVENTPENDING_"></span>/-Paket hinzufügen 

Installiert eine angegebene CAB-Dateien oder MSU-Paket im Bild. MSU-Pakets wird nur unterstützt, wenn das Zielabbild offline ist, entweder eingebunden oder angewendet. 

Mehrere Pakete können in einer Befehlszeile hinzugefügt werden. Die Verfügbarkeit der einzelnen Pakete wird überprüft. Wenn das Paket auf das angegebene Bild angewendet werden kann, erhalten Sie eine Fehlermeldung angezeigt. Verwenden Sie das Argument/IgnoreCheck, wenn Sie den Befehl ohne Überprüfung der Verfügbarkeit der einzelnen Pakete verarbeiten soll.

Verwenden Sie die Option /PreventPending, um die Installation des Pakets überspringen, wenn das Paket oder die Windows-Abbild ausstehende online Aktionen hat. (Eingeführt in Windows 8/Windows PE 4.0).

/ PackagePath kann zu verweisen:

-   Einzelne CAB-Dateien oder MSU-Datei.  

-   Ein Ordner, der eine einzelnen erweiterten CAB-Datei enthält.

-   Ein Ordner, der eine einzelnen MSU-Datei enthält.

-   Ein Ordner, der mehrere CAB-Dateien oder MSU-Dateien enthält.

**Hinweis**  
Wenn/PackagePath in einen Ordner, der im Stammverzeichnis einer CAB-Dateien oder MSU-Dateien enthält verweist, werden alle Unterordner auch rekursiv CAB und MSU-Dateien geprüft.

Syntax:

``` syntax
Dism /Add-Package /PackagePath:<path_to_cabfile> [/IgnoreCheck] [/PreventPending]
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /LogPath:AddPackage.log /Add-Package /PackagePath:C:\packages\package.msu
```

``` syntax
Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab /IgnoreCheck
```

``` syntax
Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\test\packages\package.cab /PreventPending
```

### <a name="span-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanspan-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanspan-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanremove-package"></a><span id="_Remove-Package___PackageName___name_in_image_____PackagePath___path_to_cabfile__"></span><span id="_remove-package___packagename___name_in_image_____packagepath___path_to_cabfile__"></span><span id="_REMOVE-PACKAGE___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE__"></span>/ Remove-Paket 

Entfernt einen angegebenen CAB-Datei-Paket aus dem Bild. CAB-Dateien können angegeben werden. Sie können diesen Befehl um MSU-Dateien zu entfernen.

**Hinweis**  
Entfernen Sie ein Paket aus einem offline Bild mit diesem Befehl werden die Bildgröße nicht verkleinert.

Sie können die Option/PackagePath verwenden, zeigen Sie auf die ursprüngliche Quelle des Pakets, geben Sie den Pfad zur CAB-Datei, oder Sie können das Paket nach Namen angeben, wie er in das Bild aufgeführt ist. Verwenden Sie die Option/Get-Packages, den Namen des Pakets im Bild zu suchen.

Syntax:

``` syntax
/Remove-Package {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0 /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~x86~~6.1.6801.0
```

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab
```

### <a name="span-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanspan-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanspan-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanget-features"></a><span id="_Get-Features___PackageName___name_in_image_____PackagePath___path_to_cabfile_____Format__Table___List__"></span><span id="_get-features___packagename___name_in_image_____packagepath___path_to_cabfile_____format__table___list__"></span><span id="_GET-FEATURES___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE_____FORMAT__TABLE___LIST__"></span>/ Get-Features 

Grundlegende Informationen zu allen Features (Betriebssystemkomponenten, die optionale Windows Foundation Features enthalten) in einem Paket angezeigt. Sie können die Option/Get-Features verwenden, um den Namen des Pakets im Bild finden, oder Sie können den Pfad der ursprünglichen Quelle des Pakets angeben. Wenn Sie ein Paket oder Pfadname nicht angeben, werden alle Features im Bild aufgelistet. / PackagePath kann einer CAB-Datei oder einen Ordner verweisen.

Komponentennamen Groß-/Kleinschreibung Wenn Sie ein Windows-Abbild als Windows 8 bedienen.

Verwenden Sie das Argument Standardausgabeformat oder/Format: List, um die Ausgabe als Tabelle oder einer Liste anzuzeigen.

Syntax:

``` syntax
/Get-Features {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>} [/Format:{Table | List}]
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Get-Features
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /Format:List
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /PackagePath:C:\packages\package1.cab
```

### <a name="span-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanspan-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanspan-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanget-featureinfo"></a><span id="_Get-FeatureInfo__FeatureName__name_in_image____PackageName___name_in_image_____PackagePath___path_to_cabfile___"></span><span id="_get-featureinfo__featurename__name_in_image____packagename___name_in_image_____packagepath___path_to_cabfile___"></span><span id="_GET-FEATUREINFO__FEATURENAME__NAME_IN_IMAGE____PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE___"></span>/ Get-FeatureInfo

Zeigt ausführliche Informationen zu einem Feature. Sie müssen/Featurename verwenden. Komponentennamen Groß-/Kleinschreibung Wenn Sie ein Windows-Abbild als Windows-10 oder Windows bedienen 8.x. Die Option/Get-Features können Sie um den Namen des Features im Abbild zu ermitteln.

/ Paketname und/PackagePath sind optional und können verwendet werden, um ein bestimmtes Feature in einem Paket zu suchen.

Syntax:

``` syntax
/Get-FeatureInfo /FeatureName:<name_in_image> [{/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}]
```

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts
```

``` syntax
Dism /Image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts /PackagePath:C:\packages\package.cab
```

### <a name="span-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanspan-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanspan-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanenable-feature"></a><span id="_Enable-Feature__FeatureName___name_in_image___PackageName___name_in_image_____Source___source_____LimitAccess___All_"></span><span id="_enable-feature__featurename___name_in_image___packagename___name_in_image_____source___source_____limitaccess___all_"></span><span id="_ENABLE-FEATURE__FEATURENAME___NAME_IN_IMAGE___PACKAGENAME___NAME_IN_IMAGE_____SOURCE___SOURCE_____LIMITACCESS___ALL_"></span>/ Enable-Feature 

Aktiviert oder aktualisiert das angegebene Feature im Bild. Sie müssen die Option/Featurename verwenden. Komponentennamen Groß-/Kleinschreibung Wenn Sie ein Windows-Abbild als Windows 8 bedienen. Verwenden Sie die Option/Get-Features, um den Namen des Features im Bild zu suchen.

Mehrere Male können Sie die Option/Featurename in einem einzigen Befehl für Features angeben, die das gleichen übergeordneten Paket freigeben.

Sie müssen keinen angeben den Paketnamen DISM-Option verwenden, wenn das Paket ein Windows Foundation-Paket ist. Verwenden Sie andernfalls/PackageName übergeordneten Paket des Features an.

Sie können wiederherstellen und aktivieren ein Feature, das zuvor aus dem Bild entfernt wurde. Verwenden Sie das Argument/Source, um den Speicherort der Dateien anzugeben, die erforderlich sind, um das Feature wiederherzustellen. Die Quelle für die Dateien kann mithilfe der Windows-Ordner in einem bereitgestellten Abbild, beispielsweise c:\test\mount\Windows. Sie können auch einen Windows-Side-by-Side-Ordner als Quelle für die Dateien, zum Beispiel z:\sources\SxS.

Wenn Sie mehrere/Source Argumente angeben, werden die Dateien aus dem ersten Speicherort erfasst, wobei sie sind vorhanden und der Rest der Speicherorte werden ignoriert. Wenn Sie keine/Source für ein Feature angeben, die entfernt wurde, der Standardspeicherort in der Registrierung wird verwendet, oder online von Bildern, Windows Update (WU) verwendet.

Verwenden Sie /LimitAccess um DISM Kontaktaufnahme WU online von Bildern zu verhindern.

Verwenden Sie/All, um alle übergeordneten Features des angegebenen Features zu aktivieren.

Die/Source /LimitAccess, und/alle Argumente können mit Windows 10, Windows verwendet werden 8.x und Windows PE-Abbilder über 4.0.

Syntax:

``` syntax
/Enable-Feature /FeatureName:<name_in_image> [/PackageName:<name_in_image>] [/Source: <source>] [/LimitAccess] [/All]
```

Beispiele für die:

``` syntax
Dism /Online /Enable-Feature /FeatureName:Hearts /All
```

``` syntax
Dism /Online /Enable-Feature /FeatureName:Calc /Source:c:\test\mount\Windows /LimitAccess
```

``` syntax
Dism /Image:C:\test\offline /Enable-Feature /FeatureName:Calc /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespanspan-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespanspan-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespandisable-feature"></a><span id="_Disable-Feature__FeatureName___name_in_image____PackageName___name_in_image_____Remove_"></span><span id="_disable-feature__featurename___name_in_image____packagename___name_in_image_____remove_"></span><span id="_DISABLE-FEATURE__FEATURENAME___NAME_IN_IMAGE____PACKAGENAME___NAME_IN_IMAGE_____REMOVE_"></span>/ Disable-Feature 

Deaktiviert das angegebene Feature im Bild. Sie müssen die Option/Featurename verwenden. Komponentennamen Groß-/Kleinschreibung Wenn Sie ein Windows-Abbild als Windows 8 bedienen. Verwenden Sie die Option/Get-Features, um den Namen des Features im Bild zu suchen.

Sie können/Featurename mehrmals in einem einzigen Befehl für Features im gleichen übergeordneten Paket angeben.

Sie müssen keinen angeben den Paketnamen DISM-Option verwenden, wenn sie das Paket ist ein Windows Foundation-Paket. Verwenden Sie andernfalls/PackageName übergeordneten Paket des Features an.

Verwenden Sie/Remove ein Feature zu entfernen, ohne das Feature Manifest aus diesem Abbild entfernen. Diese Option kann nur verwendet werden kann verwendet werden, mit 10 Windows, Windows 8.x und Windows PE-Abbilder oberhalb 4.0. Das Feature wird wie "Entfernt" bei Verwendung des FeatureInfo anzuzeigenden Details feature und wiederhergestellt werden können und mit/Enable-Feature mit der Option/Source aktiviert aufgeführt.

Syntax:

``` syntax
/Disable-Feature /FeatureName:<name_in_image> [/PackageName:<name_in_image>] [/Remove]
```

Beispiele für die:

``` syntax
*Dism /Online /Disable-Feature /FeatureName:Hearts
```

``` syntax
Dism /Image:C:\test\offline /Disable-Feature /FeatureName:Calc /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspanspan-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspanspan-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspancleanup-image"></a><span id="_Cleanup-Image___RevertPendingActions____SPSuperseded___HideSP_____StartComponentCleanup___ResetBase_____AnalyzeComponentStore____CheckHealth____ScanHealth____RestoreHealth___Source___filepath_____LimitAccess__"></span><span id="_cleanup-image___revertpendingactions____spsuperseded___hidesp_____startcomponentcleanup___resetbase_____analyzecomponentstore____checkhealth____scanhealth____restorehealth___source___filepath_____limitaccess__"></span><span id="_CLEANUP-IMAGE___REVERTPENDINGACTIONS____SPSUPERSEDED___HIDESP_____STARTCOMPONENTCLEANUP___RESETBASE_____ANALYZECOMPONENTSTORE____CHECKHEALTH____SCANHEALTH____RESTOREHEALTH___SOURCE___FILEPATH_____LIMITACCESS__"></span>/ Cleanup-Bild

Führt Cleanup oder Wiederherstellung Operationen für das Bild. / AnalyzeComponentStore und /ResetBase können mit 10 Windows, Windows 8.1 und Windows PE Bilder über 5.0 verwendet werden. Beginnend mit Windows 10 1607 Version, können Sie mit /ResetBase /Defer angeben. Es wird jedoch dringend empfohlen Sie **nur** als eine Option in der Factory, in denen DISM /Resetbase erfordert mehr als 30 Minuten, /Defer verwenden. / StartComponentCleanup kann mit 10 Windows, Windows verwendet werden 8.x und Windows PE-Abbilder über 4.0. / CheckHealth, /ScanHealth, /RestoreHealth, / Source und /LimitAccess mit 10 Windows, Windows verwendet werden können 8.x und Windows PE-Abbilder oberhalb 4.0. / HideSP und /SPSuperseded können nicht verwendet werden, wenn Sie eine Version von Windows warten, die älter als Bild für Windows 7 Service Pack 1 (SP1) ist.

**Tipp**  
Um zu bestimmen, wenn die Option /ResetBase zuletzt ausgeführt wurde, überprüfen Sie den LastResetBase_UTC Registrierungseintrag unter diesem Registrierungspfad:

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component basierend – Wartung

Syntax:

``` syntax
/Cleanup-Image {/RevertPendingActions | /SPSuperseded [/HideSP] | /StartComponentCleanup [/ResetBase [/Defer]] | /AnalyzeComponentStore | /CheckHealth | /ScanHealth | /RestoreHealth [/Source: <filepath>] [/LimitAccess]}
```

|   Parameter     |   Beschreibung     |
|-----------------|-------------------|
| / RevertPendingActions | Wenn einen Boot-Fehler auftreten, können Sie die Option/RevertPendingActions verwenden, das System wiederherzustellen. Der Vorgang wird alle Ausstehende Aktionen aus den vorherigen Wartungsvorgängen, da diese Aktionen die Ursache des Fehlers Boot möglicherweise zurückgesetzt. Die Option/RevertPendingActions wird auf einem ausgeführten Betriebssystem oder einer Windows PE oder Windows Recovery Environment (Windows RE) nicht unterstützt. Wichtig: Sie sollten die Option/RevertPendingActions nur in einem Szenario System-Wiederherstellung auf einem Windows-Abbild verwenden, die nicht gestartet.|
| SPSuperseded | Entfernt alle Sicherungsdateien, die während der Installation eines Service Packs erstellt. Verwenden Sie /HideSP um zu verhindern, dass das Servicepack in der Systemsteuerung von Updates installiert aufgeführt wird. Das Servicepack kann nicht deinstalliert werden, nachdem die /SPSuperseded abgeschlossen ist. |
| / StartComponentCleanup | Bereinigt die ersetzten Komponenten und reduziert die Größe des Speichers Komponente. Verwenden Sie /ResetBase auf die Basis der ersetzte Komponenten zurückgesetzt, der Größe der Komponente weiter verringern kann. Windows-Updates nicht deinstalliert werden können, nach der Ausführung von /StartComponentCleanup mit der Option /ResetBase installiert. Verwenden Sie /Defer mit /ResetBase langer Bereinigungen zum nächsten automatische Wartung zu verzögern.|
| / AnalyzeComponentStore | Erstellt einen Bericht des Speichers Komponente. Weitere Informationen zu den Bericht und wie Sie die Informationen im Bericht verwenden finden Sie unter [Determine die tatsächliche Größe des Ordners WinSxS](determine-the-actual-size-of-the-winsxs-folder.md). |
| / CheckHealth | Überprüft, ob das Bild als von einem fehlgeschlagenen Prozess beschädigt gekennzeichnet wurden und ob Beschädigung repariert werden kann. |
| / ScanHealth | Führt eine Überprüfung auf das Bild für eine Beschädigung der Komponente Store zu. Dieser Vorgang wird einige Minuten dauern.  |
| / RestoreHealth | Scannt das Bild für eine Beschädigung der Komponente Store zu und führt dann reparieren Vorgänge automatisch. Dieser Vorgang wird einige Minuten dauern. |
| / Quelle | Wird mit /RestoreHealth verwendet, um den Speicherort der bekannten gute Versionen der Dateien anzugeben, die zur Reparatur wie ein Pfad zur Windows-Verzeichnis von einem bereitgestellten Abbild verwendet werden können.|
| / LimitAccess | Verhindert, dass DISM Kontaktaufnahme mit Windows Update zur Reparatur von online Bildern. | 

Beispiele für die:

``` syntax
Dism /Image:C:\test\offline /Cleanup-Image /RevertPendingActions
```

``` syntax
Dism /Image:C:\test\offline /Cleanup-Image /SPSuperseded /HideSP
```

``` syntax
Dism /Online /Cleanup-Image /ScanHealth
```

``` syntax
Dism /Online /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows /LimitAccess
```

Weitere Informationen finden Sie unter [Reparieren einer Windows-Abbild](repair-a-windows-image.md).

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


-   Bei der Installation eines Pakets in ein offline-Abbild ist der Paketstatus "installieren ausstehende" aufgrund von ausstehenden Aktionen online. Anders ausgedrückt, wird das Paket installiert werden, wenn das Abbild gestartet und die online Aktionen verarbeitet werden. Wenn nachfolgende Aktionen angefordert werden, können sie erst nach Abschluss der vorherigen ausstehende online Aktion verarbeitet werden. Wenn Sie ein Paket mit/AddPackage, um die Installation eines Pakets überspringen, wenn online Aktionen ausstehen hinzufügen, können Sie die Option /PreventPending verwenden.
-   Einige Pakete müssen andere Pakete zuerst installiert sein. Sie sollten nicht davon ausgehen, dass Abhängigkeiten erfüllt werden, werden. Wenn Abhängigkeit Anforderungen vorhanden sind, sollten Sie eine Antwortdatei zum Installieren der notwendigen Pakete verwenden. Indem Sie eine Antwortdatei an DISM, können mehrere Pakete in der richtigen Reihenfolge installiert werden. Dies ist die bevorzugte Methode zum Installieren von mehreren Paketen. Weitere Informationen finden Sie unter [Hinzufügen / Entfernen Pakete Offline mithilfe von DISM](add-or-remove-packages-offline-using-dism.md).
-   Pakete werden in der Reihenfolge installiert, dass sie in der Befehlszeile aufgeführt sind.
-   Beim DISM verwenden, um die Liste der optionalen Komponenten in einer Windows PE-Abbild, werden die optionalen Komponenten, auch wenn der Wartung Vorgang erfolgreich war immer als ausstehend aufgelistet. Dies ist entwurfsbedingt und erfordert keine weiteren Aktionen von Ihnen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

 



