---
author: Justinha
Description: "Einstellungen für UEFI Startkonfigurationsdaten System"
ms.assetid: bfafe378-7ac3-453e-99ca-e5fde83dee2f
MSHAttr: PreferredLib:/library/windows/hardware
title: "System Startkonfigurationsdaten Einstellungen für UEFI"
ms.openlocfilehash: 36f32e696b52e56a2d112af7b8cc2aa2368e6fa1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bcd-system-store-settings-for-uefi"></a>System Startkonfigurationsdaten Einstellungen für UEFI


Für eine typische Bereitstellungsszenario müssen Sie nicht den BCD-Speicher zu ändern. In diesem Thema werden die verschiedenen BCD-Einstellungen im BCD-Speicher, den Sie ändern können. Auf UEFI-Systemen umfasst diese Einstellungen für die folgenden Boot-Anwendungen:

1.  [Windows-Start-Manager](#windowsbootmanager)

2.  [Windows-Startladeprogramm](#windowsbootloader)

3.  [Testprogramm für Windows-Speicher](#windowsmemorytester)

Den folgenden Abschnitten werden die verfügbaren Einstellungen für alle diese Anwendungen Boot im Detail und wie Sie jede Anwendung für UEFI-Systemen zu ändern.

Zur Vereinfachung ändern die BCDEdit Beispiele in diesem Abschnitt Startkonfigurationsdaten System. Fügen Sie den Store Namen in der Befehlszeile aus, um einen anderen Speicher, wie etwa eine Kopie der BCD-Vorlage zu ändern.

## <a name="span-idwindowsbootmanagerspanspan-idwindowsbootmanagerspanspan-idwindowsbootmanagerspanwindows-boot-manager-settings-for-uefi"></a><span id="WindowsBootManager"></span><span id="windowsbootmanager"></span><span id="WINDOWSBOOTMANAGER"></span>Windows-Start-Manager-Einstellungen für UEFI


Windows-Start-Manager (`{bootmgr}`) des Startvorgangs verwaltet. UEFI-basierte Systeme enthalten eine Firmware-Start-Managers Bootmgfw.efi, das eine EFI-Anwendung geladen wird, die basierend auf Variablen, die im NVRAM gespeichert sind.

Die BCD-Einstellungen für die `device` und `path` Elemente in Windows-Start-Manager Geben Sie an der Firmware-Start-Manager. Die Vorlage mit dem Namen BCD Vorlage für Windows umfasst die folgenden Einstellungen für den Windows-Start-Manager.

``` syntax
## Windows Boot Manager

identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
```

### <a name="span-iddevicesettingspanspan-iddevicesettingspanspan-iddevicesettingspandevice-setting"></a><span id="Device_Setting"></span><span id="device_setting"></span><span id="DEVICE_SETTING"></span>Gerät-Einstellung

Die `device` -Element gibt das Volume, enthält der Start-Manager für Windows, an. Für UEFI-Systemen die `device` Element für Windows-Start-Manager auf dem System Partition Volumebuchstaben festgelegt ist. Um den richtigen Volumebuchstaben zu bestimmen, verwenden Sie das Diskpart-Tool zum Anzeigen der Datenträgerpartitionen. Im folgende Beispiel wird davon ausgegangen, dass das System eine einzelne Festplatte verfügt, die mehrere Partitionen aufweist, einschließlich einer Partition, die einen Laufwerkbuchstaben des S. zugewiesen wurde

Die folgenden Befehle Diskpart wählen Sie Datenträger 0 und klicken Sie dann die Details der Volumes auf dem Datenträger, einschließlich ihrer Laufwerkbuchstaben aufgelistet. Volume 2 wird als Systempartition.

``` syntax
DISKPART> select disk 0
DISKPART> list volume

  Volume ###  Ltr  Label   Fs     Type        Size     Status     Info
  ----------  ---  ------  -----  ----------  -------  ---------  ------
  Volume 0     D           NTFS   Partition    103 GB  Healthy
  Volume 1     C           NTFS   Partition     49 GB  Healthy    Boot
  Volume 2     S           FAT32  Partition    200 MB  Healthy    System
```

Wenn die Systempartition keinen Laufwerkbuchstabe zugewiesen, weisen Sie einen mit dem Befehl **Diskpart zuweisen** . Im folgende Beispiel wird davon ausgegangen, dass die Systempartition Datenträger 2 und S als Laufwerkbuchstabe weist.

``` syntax
Diskpart
select disk 0
list volume
select volume 2   // assuming volume 2 is the system partition
assign letter=s
```

Nachdem Sie das Partition Systemvolume bestimmt haben, legen Sie die `device` Element für Windows-Start-Manager auf den entsprechenden Laufwerksbuchstaben. Im folgenden Beispiel wird `device` auf Laufwerk S.

``` syntax
Bcdedit /set {bootmgr} device partition=s:// system partition
```

### <a name="span-idpathsettingspanspan-idpathsettingspanspan-idpathsettingspanpath-setting"></a><span id="Path_Setting"></span><span id="path_setting"></span><span id="PATH_SETTING"></span>Pfad-Einstellung

Die `path` Element gibt den Speicherort der Start-Manager für Windows-Anwendung auf dem Datenträger. Für UEFI Systeme `path` gibt an, der Firmware-Start-Managers, dessen Pfad ist \\EFI\\Microsoft\\Boot\\Bootmgfw.efi.

Sie können überprüfen, ob BCD Vorlage den richtigen Pfad durch die Werte in den Speicher wie folgt auflisten hat:

``` syntax
bcdedit /store bcd-template /enum all
```

Explizit festgelegt `path` auf \\EFI\\Microsoft\\Boot\\Bootmgfw.efi ist, verwenden Sie den folgenden Befehl.

``` syntax
Bcdedit /set {bootmgr} path \efi\microsoft\boot\bootmgfw.efi
```

### <a name="span-idothersettingsspanspan-idothersettingsspanspan-idothersettingsspanother-settings"></a><span id="Other_Settings"></span><span id="other_settings"></span><span id="OTHER_SETTINGS"></span>Andere Einstellungen

Sie sollten Windows-Start-Manager auf das erste Element in der Anzeigereihenfolge der Firmware UEFI werden festgelegt, wie im folgenden Beispiel dargestellt.

``` syntax
Bcdedit /set {fwbootmgr} displayorder {bootmgr} /addfirst
```

Sie sollten auch der obersten Windows Boot Loader Webanwendungsdienst in der Windows-Start-Manager angezeigten Reihenfolge angeben. Im folgenden Beispiel wird gezeigt, wie einer angegebenen Windows-Startladeprogramm am oberen Rand der Anzeigereihenfolge platzieren.

``` syntax
Bcdedit /set {bootmgr} displayorder {<GUID>} /addfirst
```

Im vorstehenden Beispiel &lt;GUID&gt; ist der Bezeichner für das angegebene Windows Boot Loader-Objekt. Im nächste Abschnitt wird dieser Bezeichner ausführlich erläutert.

**Hinweis**  
Multiboot Systemen mit mehreren installierten Betriebssysteme verfügt über mehrere Instanzen von dem Startladeprogramm Windows. Jede Instanz der Windows-Startladeprogramm verfügt über einen eigenen Bezeichner. Sie können die standardmäßigen Windows-Startladeprogramm festlegen (`{default}`) auf einen Bezeichner.

 

## <a name="span-idwindowsbootloaderspanspan-idwindowsbootloaderspanspan-idwindowsbootloaderspanwindows-boot-loader-settings"></a><span id="WindowsBootLoader"></span><span id="windowsbootloader"></span><span id="WINDOWSBOOTLOADER"></span>Windows Boot Loader-Einstellungen


Ein BCD-Speicher verfügt über mindestens eine Instanz und optional auch mehrere Instanzen von dem Startladeprogramm Windows. Ein separates BCD-Objekt stellt jede Instanz. Jede Instanz lädt eine der installierten Versionen von Windows mit einer Konfiguration, die das Objekt Elemente angegeben haben. Jedes Windows Boot Loader-Objekt verfügt über einen eigenen Bezeichner und des Objekts `device` und `path` Einstellungen geben Sie die richtige Partition und Boot-Anwendung an.

`BCD-template`für Windows ein einzelnes Windows Boot Loader-Objekt, das den folgenden Einstellungen verfügt.

``` syntax
## Windows Boot Loader

identifier              {9f25ee7a-e7b7-11db-94b5-f7e662935912}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Microsoft Windows Server
locale                  en-US
inherit                 {bootloadersettings}
osdevice                partition=C:
systemroot              \Windows
```

Der Bezeichner für dieses Windows-Startladeprogramm ist {9f25ee7a-e7b7-11db-94b5-f7e662935912}. Sie können diese GUID auf Ihrem System verwenden oder ermöglichen des BCDEdit-Tools eine neue GUID zu generieren.

Zur Vereinfachung der BCDEdit-Befehlen kann eine der die Windows-Boot angeben Ladeprogramme im BCD System als das standardmäßige Ladeprogramm gespeichert. Anschließend können Sie die standard-ID (`{default}`) anstelle der vollständigen GUID. Im folgende Beispiel gibt die Windows-Startladeprogramm EFI als Standard-Startladeprogramm, vorausgesetzt, dass es sich um die ID-GUID aus BCD-Vorlage verwendet an.

``` syntax
Bcdedit /default {9f25ee7a-e7b7-11db-94b5-f7e662935912}
```

### <a name="span-iddeviceandosdevicesettingsspanspan-iddeviceandosdevicesettingsspanspan-iddeviceandosdevicesettingsspandevice-and-osdevice-settings"></a><span id="Device_and_OSDevice_Settings"></span><span id="device_and_osdevice_settings"></span><span id="DEVICE_AND_OSDEVICE_SETTINGS"></span>Gerät und OS-Devices-Einstellungen

Die folgenden Elemente angeben wichtige Speicherorten:

Die `device` -Element gibt die Partition, die Boot-Anwendung enthält.

Die `osdevice` -Element gibt an, der Partition, das Stammverzeichnis des Systems enthält.

Starten für den Windows-Ladeprogramm für EFI, beide Elemente sind in der Regel auf der Laufwerkbuchstabe der Windows-Systempartition festgelegt. Jedoch Wenn BitLocker aktiviert ist, oder einen Computer hat mehrere installierten Versionen von Windows, `osdevice` und `device` möglicherweise auf verschiedenen Partitionen festgelegt werden. BCD-Vorlage wird beide Elemente auf Laufwerk C, die dem normalen Wert entspricht. Sie können auch explizit festlegen, die `osdevice` und `device` Werte, wie im folgenden Beispiel dargestellt. Im Beispiel wird davon ausgegangen, dass Sie den Windows-Startladeprogramm EFI als das Startladeprogramm Standardobjekt angegeben haben.

``` syntax
Bcdedit /set {default} device partition=c:
Bcdedit /set {default} osdevice partition=c:
```

### <a name="span-idpathsettingspanspan-idpathsettingspanspan-idpathsettingspanpath-setting"></a><span id="Path_Setting"></span><span id="path_setting"></span><span id="PATH_SETTING"></span>Pfad-Einstellung

Die `path` Element von einer Windows-Startladeprogramm gibt den Speicherort der des Startladeprogramms auf dem Datenträger. Für UEFI-Systeme `path` gibt die Windows-Startladeprogramm für EFI, dessen Pfad ist \\Windows\\System32\\Winload.efi.

Sie können überprüfen, ob BCD-Vorlage die richtige verfügt über `path` Wert durch die Werte im Speicher auflisten. Sie können auch explizit festlegen, die `path` Wert, wie im folgenden Beispiel dargestellt.

``` syntax
Bcdedit /set {default} path \windows\system32\winload.efi
```

## <a name="span-idwindowsmemorytesterspanspan-idwindowsmemorytesterspanspan-idwindowsmemorytesterspanwindows-memory-tester-settings"></a><span id="WindowsMemoryTester"></span><span id="windowsmemorytester"></span><span id="WINDOWSMEMORYTESTER"></span>Windows Arbeitsspeicher Tester-Einstellungen


Arbeitsspeicher unter Testprogramm für Windows (`{memdiag}`) Speicherdiagnose beim Systemstart wird ausgeführt. Die BCD-Einstellungen für der Anwendung `device` und `path` Elemente geben Sie die Anwendung an.

**Hinweis**  
Hinweis: Intel Itanium-Computern ein Testprogramm für Windows Speicher nicht einschließen und erfordern keinen `{memdiag}` Settings.

 

BCD-Vorlage für Windows verfügt über die folgenden Einstellungen.

``` syntax
## Windows Memory Tester

identifier              {memdiag}
device                  partition=\Device\HarddiskVolume1
path                    \boot\memtest.exe
description             Windows Memory Diagnostic
```

### <a name="span-iddevicesettingspanspan-iddevicesettingspanspan-iddevicesettingspandevice-setting"></a><span id="Device_Setting"></span><span id="device_setting"></span><span id="DEVICE_SETTING"></span>Gerät-Einstellung

Für UEFI-Systemen die `device` -Element für das Testprogramm für Windows Arbeitsspeicher auf der System Partition Laufwerkbuchstabe festgelegt ist. Im folgende Beispiel wird davon ausgegangen, dass die Systempartition S, Laufwerk ist, wie in den vorherigen Beispielen.

``` syntax
Bcdedit /set {bootmgr} device partition=s:  // system partition
```

### <a name="span-idpathsettingspanspan-idpathsettingspanspan-idpathsettingspanpath-setting"></a><span id="Path_Setting"></span><span id="path_setting"></span><span id="PATH_SETTING"></span>Pfad-Einstellung

Die `path` Element gibt den Speicherort des Windows-Test-Manager auf dem Datenträger, die die `device` -Element angegeben wurde. Für UEFI-Systeme `path` gibt die EFI-Version der Anwendung (\\EFI\\Microsoft\\Boot\\Memtest.efi).

Sie können überprüfen, ob BCD-Vorlage die richtige verfügt über `path` Wert durch die Werte im Speicher auflisten. Sie können auch das Tool BCDEdit explizit festlegen der `path` Wert, wie im folgenden Beispiel dargestellt.

``` syntax
Bcdedit /set {memdiag} path \efi\microsoft\boot\memtest.efi
```

 

 





