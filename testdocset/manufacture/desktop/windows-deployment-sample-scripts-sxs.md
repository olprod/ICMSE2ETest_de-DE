---
author: Justinha
Description: "Die folgenden Skripts werden in der Übungseinheit verwendet. Es kann hilfreich sein, diese gleichzeitig erstellen können oder Herunterladen der Beispiele aus dem Web sein."
ms.assetid: 621503da-e74f-4eef-8315-72c8be67747a
MSHAttr: PreferredLib:/library/windows/hardware
title: Beispielskripts
ms.openlocfilehash: 45d1f4104eeb781a5c5a83eef14233d191f1f9e0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sample-scripts"></a>Beispielskripts

[Laden Sie die Beispielskripts in dieser Übungseinheit verwendet](http://go.microsoft.com/fwlink/p/?LinkId=800657) 

Kopieren Sie diese Skripts in den Stamm des Speichers USB-Laufwerk.  Verweisen Sie auf diese Seite zu verstehen, was in den Skripts ist.

Nächster Schritt: [Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md)

## <a name="span-idimagedeploymentscriptsspanspan-idimagedeploymentscriptsspanspan-idimagedeploymentscriptsspanimage-deployment-scripts"></a><span id="Image_deployment_scripts"></span><span id="image_deployment_scripts"></span><span id="IMAGE_DEPLOYMENT_SCRIPTS"></span>Bild Bereitstellungsskripts

Die folgenden Skripts Einrichten von Windows-Geräten mithilfe einer Bilddatei, und Konfigurieren von Features Drucktaste zurücksetzen.

### <a name="span-idcreatepartitions-firmwaretxtspanspan-idcreatepartitions-firmwaretxtspanspan-idcreatepartitions-firmwaretxtspancreatepartitions-firmwaretxt"></a><span id="CreatePartitions-_firmware_.txt"></span><span id="createpartitions-_firmware_.txt"></span><span id="CREATEPARTITIONS-_FIRMWARE_.TXT"></span>TXT CreatePartitions-(Firmware)

Verwenden Sie diese Skripts zusammen mit DiskPart zu formatieren, und richten Sie die Festplattenpartitionen für Windows, einschließlich Wiederherstellungstools. Anpassen der Partitionsgröße, um das Laufwerk bei Bedarf zu füllen.

### <a name="applyimagebat"></a>ApplyImage.bat

Verwenden Sie dieses Skript ein Windows-Abbild auf ein neues Gerät anwenden.

``` syntax
@echo ApplyImage.bat
@echo     Applies a Windows image to a desktop PC.
@echo     To run this script, boot the device using WinPE first.
@echo     NOTE: This script erases the primary hard drive
@echo.
@echo UPDATE (JULY 2016):
@echo * This script stops just after applying the image.
@echo   This gives you an opportunity to add siloed provisioning packages (SPPs)
@echo   so that you can include them in your recovery tools.
@echo.
@echo   After the script is complete, use apply-recovery.bat to finish
@echo   setting up the recovery tools.
@echo.
@echo * Checks whether the PC is booted into BIOS or UEFI mode
@echo   and applies the appropriate disk configuration.
@echo.
@echo * Includes support for the /EA variables for quicker
@echo   image capture and recovery.
@echo.
@echo * Checks to see if you're booted into Windows PE.
@echo.
@if not exist X:\Windows\System32 echo ERROR: This script is built to run in Windows PE.
@if not exist X:\Windows\System32 goto END
@if %1.==. echo ERROR: To run this script, add a path to a Windows image file.
@if %1.==. echo Example: ApplyImage D:\WindowsWithFrench.wim
@if %1.==. goto END
@echo *********************************************************************
@echo Checking to see if the PC is booted in BIOS or UEFI mode.
wpeutil UpdateBootInfo
for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
@echo            Note: delims is a TAB followed by a space.
@if x%Firmware%==x echo ERROR: Can't figure out which firmware we're on.
@if x%Firmware%==x echo        Common fix: In the command above:
@if x%Firmware%==x echo             for /f "tokens=2* delims=    "
@if x%Firmware%==x echo        ...replace the spaces with a TAB character followed by a space.
@if x%Firmware%==x goto END
@if %Firmware%==0x1 echo The PC is booted in BIOS mode. 
@if %Firmware%==0x2 echo The PC is booted in UEFI mode. 
@echo *********************************************************************
@echo Formatting the primary disk...
@if %Firmware%==0x1 echo    ...using BIOS (MBR) format and partitions.
@if %Firmware%==0x2 echo    ...using UEFI (GPT) format and partitions. 
@echo CAUTION: All the data on the disk will be DELETED.
@SET /P READY=Erase all data and continue? (Y or N):
@if %READY%.==y. set READY=Y
@if not %READY%.==Y. goto END
if %Firmware%==0x1 diskpart /s %~dp0CreatePartitions-BIOS.txt
if %Firmware%==0x2 diskpart /s %~dp0CreatePartitions-UEFI.txt
@echo *********************************************************************
@echo  == Set high-performance power scheme to speed deployment ==
call powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
@echo *********************************************************************
@echo  == Apply the image to the Windows partition ==
@SET /P COMPACTOS=Deploy as Compact OS? (Y or N):
@if %COMPACTOS%.==y. set COMPACTOS=Y
@echo Does this image include Extended Attributes?
@echo    (If you're not sure, type N).
@SET /P EA=(Y or N):
@if %EA%.==y. set EA=Y
if %COMPACTOS%.==Y.     if %EA%.==Y.     dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /Compact /EA
if not %COMPACTOS%.==Y. if %EA%.==Y.     dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /EA
if %COMPACTOS%.==Y.     if not %EA%.==Y. dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /Compact
if not %COMPACTOS%.==Y. if not %EA%.==Y. dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\
@echo *********************************************************************
@echo == Copy boot files to the System partition ==
W:\Windows\System32\bcdboot W:\Windows /s S:
@echo *********************************************************************
@echo   Next steps:
@echo   * Add Windows desktop applications (optional):
@echo       DISM /Apply-SiloedPackage /ImagePath:W:\ 
@echo            /PackagePath:"D:\App1.spp" /PackagePath:"D:\App2.spp"  ...
@echo   * Add the recovery image:
@echo       ApplyRecovery.bat
@echo   * Reboot:
@echo       exit
:END
```

Dieses Skript basiert auf den folgenden zwei DiskPart-Skripts, CreatePartitions UEFI.txt und CreatePartitions-BIOS.txt, die im selben Ordner platziert werden muss:

### <a name="createpartitions-uefitxt"></a>CreatePartitions UEFI.txt

Erstellt die Tools Partitionen System, MSR, Windows und Wiederherstellung für UEFI-basierte PCs.

Dieses Skript vorübergehend weist diese Laufwerkbuchstaben: System = S, Windows = W und Recovery = R. GPT erhalten kein Briefs. Der Buchstabe W wird verwendet, um potenzielle Laufwerk Buchstaben Konflikte zu vermeiden. Nachdem das Gerät neu gestartet wurde, wird die Windows-Partition den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

Das folgende Diagramm zeigt die resultierende Partitionskonfiguration:

![Diagramm der Partition Standardlayout: System, Msr, Windows und Wiederherstellung](images/dep-win10-partitions-uefi.png)

``` syntax
rem == CreatePartitions-UEFI.txt ==
rem == These commands are used with DiskPart to
rem    create four partitions
rem    for a UEFI/GPT-based PC.
rem    Adjust the partition sizes to fill the drive
rem    as necessary. ==
select disk 0
clean
convert gpt
rem == 1. System partition =========================
create partition efi size=100
rem    ** NOTE: For Advanced Format 4Kn drives,
rem               change this value to size = 260 ** 
format quick fs=fat32 label="System"
assign letter="S"
rem == 2. Microsoft Reserved (MSR) partition =======
create partition msr size=16
rem == 3. Windows partition ========================
rem ==    a. Create the Windows partition ==========
create partition primary 
rem ==    b. Create space for the recovery tools ===
shrink minimum=500
rem       ** NOTE: Update this size to match the
rem                size of the recovery tools 
rem                (winre.wim)                    **
rem ==    c. Prepare the Windows partition ========= 
format quick fs=ntfs label="Windows"
assign letter="W"
rem === 4. Recovery partition ======================
create partition primary
format quick fs=ntfs label="Recovery"
assign letter="R"
set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
gpt attributes=0x8000000000000001
list volume
exit
```

### <a name="createpartitions-biostxt"></a>CreatePartitions BIOS.txt

Erstellt die System, Windows und Recovery Tools Partitionen für BIOS-basierte PCs.

Dieses Skript vorübergehend weist diese Laufwerkbuchstaben: System = S, Windows = W und Recovery = R. Der Buchstabe W wird verwendet, um Laufwerk Buchstaben Konflikte vermieden werden. Nachdem das Gerät neu gestartet wurde, wird die Windows-Partition den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

Das folgende Diagramm zeigt die resultierende Partitionskonfiguration:

![Diagramm der Partition Standardlayout: System, Windows und Wiederherstellung](images/dep-win10-partitions-bios.png)

``` syntax
rem == CreatePartitions-BIOS.txt ==
rem == These commands are used with DiskPart to
rem    create three partitions
rem    for a BIOS/MBR-based computer.
rem    Adjust the partition sizes to fill the drive
rem    as necessary. ==
select disk 0
clean
rem == 1. System partition ======================
create partition primary size=100
format quick fs=ntfs label="System"
assign letter="S"
active
rem == 2. Windows partition =====================
rem ==    a. Create the Windows partition =======
create partition primary
rem ==    b. Create space for the recovery tools  
shrink minimum=500
rem       ** NOTE: Update this size to match the
rem                size of the recovery tools 
rem                (winre.wim)                 **
rem ==    c. Prepare the Windows partition ====== 
format quick fs=ntfs label="Windows"
assign letter="W"
rem == 3. Recovery partition ====================
create partition primary
format quick fs=ntfs label="Recovery image"
assign letter="R"
set id=27
list volume
exit
```

### <a name="applyrecoverybat"></a>ApplyRecovery.bat

Verwenden Sie dieses Skript, um der Windows-Wiederherstellungspartition vorzubereiten.

``` syntax
@echo == ApplyRecovery.bat ==
@echo  *********************************************************************
@echo  == Copy the Windows RE image to the Windows RE Tools partition ==
md R:\Recovery\WindowsRE
xcopy /h W:\Windows\System32\Recovery\Winre.wim R:\Recovery\WindowsRE\
@echo  *********************************************************************
@echo  == Register the location of the recovery tools ==
W:\Windows\System32\Reagentc /Setreimage /Path R:\Recovery\WindowsRE /Target W:\Windows
@echo  *********************************************************************
@echo  == If Compact OS, single-instance the recovery provisioning package ==
@echo     Options: N: No
@echo              Y: Yes
@echo              D: Yes, but defer cleanup steps to first boot.
@echo                 Use this if the cleanup steps take more than 30 minutes.
@echo                 defer the cleanup steps to the first boot.
@SET /P COMPACTOS=Deploy as Compact OS? (Y, N, or D):
@if %COMPACTOS%.==y. set COMPACTOS=Y
@if %COMPACTOS%.==d. set COMPACTOS=D
if %COMPACTOS%.==Y. dism /Apply-CustomDataImage /CustomDataImage:W:\Recovery\Customizations\USMT.ppkg /ImagePath:W:\ /SingleInstance
if %COMPACTOS%.==D. dism /Apply-CustomDataImage /CustomDataImage:W:\Recovery\Customizations\USMT.ppkg /ImagePath:W:\ /SingleInstance /Defer
@rem *********************************************************************
@echo Checking to see if the PC is booted in BIOS or UEFI mode.
wpeutil UpdateBootInfo
for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
@echo            Note: delims is a TAB followed by a space.
@if x%Firmware%==x echo ERROR: Can't figure out which firmware we're on.
@if x%Firmware%==x echo        Common fix: In the command above:
@if x%Firmware%==x echo             for /f "tokens=2* delims=    "
@if x%Firmware%==x echo        ...replace the spaces with a TAB character followed by a space.
@if x%Firmware%==x goto END
@if %Firmware%==0x1 echo The PC is booted in BIOS mode. 
@if %Firmware%==0x2 echo The PC is booted in UEFI mode. 
@echo  *********************************************************************
@echo == Hiding the recovery tools partition
if %Firmware%==0x1 diskpart /s %~dp0HideRecoveryPartitions-BIOS.txt
if %Firmware%==0x2 diskpart /s %~dp0HideRecoveryPartitions-UEFI.txt
@echo *********************************************************************
@echo == Verify the configuration status of the images. ==
W:\Windows\System32\Reagentc /Info /Target W:\Windows
@echo    (Note: Windows RE status may appear as Disabled, this is OK.)
@echo *********************************************************************
@echo      All done!
@echo      Disconnect the USB drive from the reference device.
@echo      Type exit to reboot.
@echo.
:END
```

Dieses Skript nutzt die folgenden beiden DiskPart Skripts, HideRecoveryPartitions UEFI.txt und HideRecoveryPartitions-BIOS.txt, die im selben Ordner platziert werden muss:

### <a name="hiderecoverypartitions-uefitxt"></a>HideRecoveryPartitions UEFI.txt

``` syntax
rem === HideRecoveryPartitions-UEFI.txt ===
select disk 0
select partition 4
set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
gpt attributes=0x8000000000000001
remove
list volume
```

### <a name="hiderecoverypartitions-biostxt"></a>HideRecoveryPartitions BIOS.txt

``` syntax
rem === HideRecoveryPartitions-BIOS.txt ===
select disk 0
select partition 3
set id=27
remove
list volume
```


## <a name="span-idstartlayoutlayoutmodificationxmlspanspan-idstartlayoutlayoutmodificationxmlspanstart-layout-layoutmodificationxml"></a><span id="start_layout__layoutmodification.xml_"></span><span id="START_LAYOUT__LAYOUTMODIFICATION.XML_"></span>Starten Sie Layout (LayoutModification.xml)


Das Start Kachel Layout in Windows 10 bietet OEMs die Möglichkeit Kacheln an das Standardlayout Start Einbeziehung Weblinks, sekundäre Kacheln, apps für Windows und Windows-desktopanwendungen angefügt. OEMs können dieses Layout verwenden, um es auf mehrere Bereiche oder Märkte anwendbar vorzunehmen, ohne zu duplizieren einen Großteil der Arbeit. Darüber hinaus können OEMs hinzufügen, bis zu drei Standard-apps in den Abschnitt häufig verwendeten apps im Bereich, der Listen System-gesteuerte o den Benutzer, einschließlich wichtiger oder auf die häufig zugegriffen System Standorten übermittelt und kürzlich installierten apps.

Nutzen Sie alle neuen Features und die am häufigsten robuste und vollständige Start Anpassung für Windows 10, sollten Sie eine Datei LayoutModification.xml erstellen. Diese Datei gibt an, wie die OEM-Kacheln in Start angeordnet werden. Weitere Informationen über das Layout für die neue Start anpassen finden Sie unter [Anpassen der Windows-10-Startseite](https://msdn.microsoft.com/library/windows/hardware/mt170651) in der Dokumentation zu Windows 10 Partner.

Beispiel **LayoutModification.xml**:

``` syntax
<LayoutModificationTemplate
    xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
    xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
    xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
    Version="1">
  <RequiredStartGroupsCollection>
    <RequiredStartGroups
      Region="DE|ES|FR|GB|IT|US">
      <AppendGroup
        Name="Fabrikam Group 1">
        <start:Tile
          AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:DesktopApplicationTile
          DesktopApplicationID="Microsoft.Windows.Explorer"
          Size="2x2"
          Row="0"
          Column="2"/>
        <start:Tile
          AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
          Size="2x2"
          Row="0"
          Column="4"/>
      </AppendGroup>    
      <AppendGroup
        Name="Fabrikam Group 2">
        <start:Tile
          AppUserModelID="Microsoft.Reader_8wekyb3d8bbwe!Microsoft.Reader"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:DesktopApplicationTile
          DesktopApplicationID="http://www.bing.com/"
          Size="2x2"
          Row="0"
          Column="2"/>
        <start:DesktopApplicationTile
          DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"
          Size="2x2"
          Row="0"
          Column="4"/>
      </AppendGroup>
    </RequiredStartGroups>
    <RequiredStartGroups>
      <AppendGroup
        Name="Fabrikam Group 1">
        <start:Tile
          AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:SecondaryTile
          AppUserModelID="Microsoft.Windows.Spartan_cw5n1h2txyewy!Microsoft.Spartan.Spartan"
          TileID="FabrikamWeblinkTile"
          Arguments="http://www.fabrikam.com"
          DisplayName="Fabrikam"
          Square150x150LogoUri="ms-appx:///Assets/SpartanMedium.png"
          ShowNameOnSquare150x150Logo="true"
          BackgroundColor="#FF112233"
          Size="2x2"
          Row="0"
          Column="2"/>
      </AppendGroup>    
    </RequiredStartGroups>
  </RequiredStartGroupsCollection> 
  <TopMFUApps>
    <Tile AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App" />
  </TopMFUApps>  
</LayoutModificationTemplate>
```

**Exemplarische Vorgehensweise Layout starten**

1.  Falls nicht bereits vorhanden, erstellen Sie eine Datei namens **LayoutModification.xml**.
2.  Wenn Sie müssen angeben, ob die Append-Gruppen auf bestimmte Regionen nur angewendet werden müssen, verwenden Sie das optionale **Region** -Attribut im **RequiredStartGroups** -Element. Der Wert Region muss zwei Buchstaben Land/Region Codes entsprechen. Verwenden Sie eine Pipe "|" als Trennzeichen, wenn Sie mehrere Länder/Regionen angeben müssen.

    ``` syntax
    <RequiredStartGroups
          Region="DE|ES|FR|GB|IT|US">
    ```

3.  Geben Sie die Kacheln, den, die Sie in eine **AppendGroup**aufnehmen möchten. OEMs können bis zu zwei **AppendGroup**hinzufügen. Das folgende Beispiel zeigt zwei Gruppen namens "Fabrikam Group 1" und "Gruppe" Fabrikam "2", die Kacheln enthalten, die angewendet wird, wenn das Gerät Land/Region übereinstimmt, was in **Region** angegeben wird (Deutschland, Spanien, Frankreich, Großbritannien, Italien und USA sind in diesem Fall die Regionen). Jede Gruppe enthält drei Kacheln und die verschiedenen Elemente müssen Sie je nach die Kachel verwenden, die Sie an Start anheften möchten.

    ``` syntax
    <RequiredStartGroups
          Region="DE|ES|FR|GB|IT|US">
          
          <!-- OEMs can add a maximum of two AppendGroup. Each AppendGroup specifies a group of
               tiles that will be appended to Start. -->
          <AppendGroup
            Name="Fabrikam Group 1">
            <!-- Add the News Universal Windows app to Start -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Add a Windows desktop application with a known AppUserModelID  -->
            <start:DesktopApplicationTile
              DesktopApplicationID="Microsoft.Windows.Explorer"
              Size="2x2"
              Row="0"
              Column="2"/>
            <!-- Add the Excel Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
              Size="2x2"
              Row="0"
              Column="4"/>
          </AppendGroup>
          
          <AppendGroup
            Name="Fabrikam Group 2">
            <!-- Add a Windows 8.1 app -->
            <start:Tile
              AppUserModelID="Microsoft.Reader_8wekyb3d8bbwe!Microsoft.Reader"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Web link tile with associated .url file is in legacy Start Menu folder. This requires
                 a shortcut or .url file to be added in one of several legacy Start Menu directories, such as
                 "%APPDATA%\Microsoft\Windows\Start Menu\Programs\" 
                 or the all users profile "%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\" -->
            <start:DesktopApplicationTile
              DesktopApplicationID="http://www.bing.com/"
              Size="2x2"
              Row="0"
              Column="2"/>
            <!-- Add a Windows desktop application link in a legacy Start Menu folder. You must add the .lnk file 
                 in the specified location when the device first boots. -->
            <start:DesktopApplicationTile
              DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"
              Size="2x2"
              Row="0"
              Column="4"/>
          </AppendGroup>
        </RequiredStartGroups>
    ```

    Im folgenden Codebeispiel wird eine Gruppe mit dem Namen "Fabrikam Gruppe 1", die angewendet wird, falls das Gerät Land/Region nicht in der vorherigen RequiredStartGroups angegebenen davon entspricht.

    ``` syntax
        <!-- Non-region specific group -->
        <RequiredStartGroups>
          <AppendGroup
            Name="Fabrikam Group 1">
            <!-- Add the Word Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Add the Excel Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
              Size="2x2"
              Row="0"
              Column="2"/>
          </AppendGroup>    
        </RequiredStartGroups>
    ```

    Behalten Sie beim Erstellen der Datei LayoutModification.xml Folgendes beachten:

    -   Wenn Sie eine Windows-desktopanwendungen mit dem **Start: DesktopApplicationTile** Tag festhalten, und der Anwendung Anwendung Modell Mitgliedsname nicht kennen, müssen Sie eine LNK-Datei in einem legacy-Menü Startmenüverzeichnis vor dem ersten Start erstellen.
    -   Wenn Sie das Tag **Start: DesktopApplicationTile** verwenden, so heften Sie an eine Verknüpfung legacy URL beginnen, müssen Sie erstellen Sie eine URL-Datei und fügen Sie diese Datei in ein legacy-Menü Startmenüverzeichnis vor dem ersten Start.

    Die folgenden Verzeichnisse können Sie für die oben beschriebenen Szenarien um die URL oder lnk-Dateien zu platzieren:

    -   ANWENDUNGSDATEN %\\Microsoft\\Windows\\Startmenü\\Programme\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\Startmenü\\Programme\\

4.  Optional können Sie bis zu 3 hinzufügen apps Abschnitt häufig verwendeten Systembereich. Im folgenden Beispiel wird veranschaulicht, wie häufig verwendeten Systembereich die Rechner app hinzugefügt.

    ``` syntax
      <!-- Add the calculator app to the frequently used system area -->
      <TopMFUApps>
        <Tile AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App" />
      </TopMFUApps>
    ```

5.  Speichern Sie die Datei LayoutModification.xml.

    Nachdem Sie die Datei LayoutModification.xml erstellt haben, müssen Sie diese Datei an der richtigen System mithilfe von Windows ICD oder Bereitstellung Classic-Format speichern. Weitere Informationen zur Vorgehensweise finden Sie unter:

    -   Windows ICD - Übung 1, Schritt 7: Anpassen des Layouts Start
    -   Classic-Schreibweise Bereitstellung - Lab 2a, Schritt 5: Hinzufügen die Dateien Sie das Layout Start ändern müssen

    Wenn Sie keine LayoutModification.xml-Datei erstellen und Sie auch weiterhin mithilfe die Einstellungen für die unbeaufsichtigte Installation zu starten, wird das Betriebssystem die Antwortdatei für die unbeaufsichtigte Installation verwenden und übernehmen die ersten 12 SquareTiles oder DesktoporSquareTiles Einstellungen in der Datei für die unbeaufsichtigte Installation angegeben. Das System platziert diese Kacheln automatisch in die neu erstellte Gruppen dann am Ende des Start – die ersten sechs Kacheln werden in der ersten OEM-Gruppe und der zweite Satz von sechs Kacheln in der zweiten OEM-Gruppe abgelegt sind. Wenn OEMName in der Datei für die unbeaufsichtigte Installation angegeben ist, wird der Wert für dieses Element verwendet, um die Gruppen OEM benennen, die erstellt wird.

## <a name="span-idmicrophonesettingsspeechsettingcmdspanspan-idmicrophonesettingsspeechsettingcmdspanmicrophone-settings-speechsettingcmd"></a><span id="microphone_settings__speechsetting.cmd_"></span><span id="MICROPHONE_SETTINGS__SPEECHSETTING.CMD_"></span>Mikrofon Settings (SpeechSetting.cmd)


Verwenden Sie dieses Skript für die Optimierung Ihres Geräts Mikrofon, um die Sprache Genauigkeit für Funktionen wie Cortana maximieren. Um zu erfahren, wie die entsprechenden Werte für das Gerät zu testen, finden Sie unter [Cortana Geräteinstallation testen](https://msdn.microsoft.com/library/windows/hardware/dn957009) der Hardware WEG.

### <a name="speechsettingcmd"></a>SpeechSetting.cmd

``` syntax
@echo off
@echo.
@echo This script will set the Device.SpeechRecognition.DefaultMicGain values.
@echo.
 
setlocal
setlocal ENABLEDELAYEDEXPANSION
 
if "%1"=="" goto :InputPrompt
 call :tohex %1
@echo %_DECVAL% == 0x%_HEXVAL%
set /a Percentage=%_DECVAL%/100
 
set RegPath=HKLM\Software\Microsoft\Speech_OneCore\AudioInput\MicWiz
set RegKey=DefaultDefaultMicGain
set RegValue=0x%_HEXVAL%
 
@echo reg add %RegPath% /v %RegKey% /t REG_DWORD /d %RegValue% /f
reg add %RegPath% /v %RegKey% /t REG_DWORD /d %RegValue% /f
if %errorlevel% NEQ 0 echo Reg Add function failed. && goto :Error
@echo.
@echo Successfully set the MicGain value to %Percentage% percent.
@echo.
goto :end
 
:ToHex
     set _DECVAL=%1
     set _HEXVAL=
     set _VAL=%1
     if %1 LSS 0 (
         REM break the number into two parts so that we can output the
         REM full value within the bounds of a 32 bit signed value
         set /A _offset="-(-2147483647 - !_VAL!) + 2"
         set /A _VAL="!_offset! / 16 + 0x7FFFFFF"
         set /A _P="!_offset! %% 16 + 0xF"
 
         if !_P! GEQ 16 (
         set /A _VAL="!_VAL! + 1"
         set /A _P="!_P! %% 16"
         )
         if !_P! LEQ 9 set _HEXVAL=!_P!!_HEXVAL!
         if "!_P!" == "10" set _HEXVAL=A!_HEXVAL!
         if "!_P!" == "11" set _HEXVAL=B!_HEXVAL!
         if "!_P!" == "12" set _HEXVAL=C!_HEXVAL!
         if "!_P!" == "13" set _HEXVAL=D!_HEXVAL!
         if "!_P!" == "14" set _HEXVAL=E!_HEXVAL!
         if "!_P!" == "15" set _HEXVAL=F!_HEXVAL!
     )
 
     :hexloop
     set /A _P="%_VAL% %% 16"
     if %_P% LEQ 9 set _HEXVAL=%_P%%_HEXVAL%
     if "%_P%" == "10" set _HEXVAL=A%_HEXVAL%
     if "%_P%" == "11" set _HEXVAL=B%_HEXVAL%
     if "%_P%" == "12" set _HEXVAL=C%_HEXVAL%
     if "%_P%" == "13" set _HEXVAL=D%_HEXVAL%
     if "%_P%" == "14" set _HEXVAL=E%_HEXVAL%
     if "%_P%" == "15" set _HEXVAL=F%_HEXVAL%
     set /A _VAL="%_VAL% / 16"
     if "%_VAL%" == "0" goto :endloop
     goto :hexloop
 
:InputPrompt
      @echo.
      @echo Incorrect Usage.
      @echo.
      @echo Please input a decimal value as a parameter.
      @echo.
      @echo Example:
      @echo SpeechSetting.cmd 4200
      @echo.
      @echo This example sets the MicGain as 42 percent which is 0x1068.
      @echo.
goto :end
 
:Error
@echo.
@echo Error occurred.
@echo.
goto :end
 
:endloop
     set _offset=
     set _P=
     set _VAL=
goto :eof
 
:end 
```

## <a name="span-idremovewindowsappsspanspan-idremovewindowsappsspanspan-idremovewindowsappsspanremove-windows-apps"></a><span id="Remove_Windows_apps"></span><span id="remove_windows_apps"></span><span id="REMOVE_WINDOWS_APPS"></span>Entfernen von Windows-apps


Wenn Sie Sprachpakete zu einem Bild hinzufügen, müssen Sie zum Entfernen und Neuinstallieren aller Ihrer apps für Windows, stellen Sie sicher, dass sie die Sprachressourcen enthalten.

Nachfolgend finden Sie zwei Skripts, der verwendet werden kann, um apps aus einem offline-Abbild zu entfernen und eine andere, die im Überwachungsmodus verwendet werden können, um apps aus einer laufenden Abbild zu entfernen:

### <a name="removeappsinofflineimagecmd"></a>Entfernen von\_apps\_in\_offline\_image.cmd

Dieses Skript nimmt an, dass der Dateiname install.wim, die das Skript vom gleichen Ordner wie install.wim, ausgeführt wird, das der zu ändernde Index ist \#1, und keine anderen Windows-Bilder an anderen Orten Index sind (\#2, \#(3), die beibehalten werden müssen.

``` syntax
@echo off
@rem Run this script from the same folder that includes install.wim 
cls
md mount
dism /mount-image /mountdir:mount /imagefile:install.wim /index:1
if exist appx.txt del appx.txt
if exist applist.txt del applist.txt
if exist appremove.cmd del appremove.cmd
dism /image:mount /get-provisionedappxpackages > appx.txt
findstr /c:"PackageName" appx.txt > applist.txt
setlocal enabledelayedexpansion
set INTEXTFILE=applist.txt
set OUTTEXTFILE=appremove.cmd
set SEARCHTEXT=PackageName : 
set REPLACETEXT=dism /image:mount /remove-provisionedappxpackage /packagename:
set OUTPUTLINE=

for /f "tokens=1,* delims=¶" %%A in ( '"type %INTEXTFILE%"') do (
SET string=%%A
SET modified=!string:%SEARCHTEXT%=%REPLACETEXT%!

echo !modified! >> %OUTTEXTFILE%
)
del appx.txt
del applist.txt
call appremove.cmd
dism /unmount-image /mountdir:mount /commit
echo "Check to make sure operations completed successfully. If not, press Ctrl+C."
pause
ren install.wim install-temp.wim
dism /export-image /sourceimagefile:install-temp.wim /sourceindex:1 /destinationimagefile:install.wim
del install-temp.wim
```

### <a name="removeappsinauditmodecmd"></a>Entfernen von\_apps\_in\_Überwachen\_mode.cmd

Mit diesem Skript wird davon ausgegangen, dass Sie auf den Verweis PC im Überwachungsmodus ausführen.

``` syntax
@echo off
@rem Use MOUNT folder in folder where script is run 
cls
dism /mount-image /mountdir:mount /imagefile:install.wim /index:1
if exist appx.txt del appx.txt
if exist applist.txt del applist.txt
if exist appremove.cmd del appremove.cmd
dism /image:mount /get-provisionedappxpackages > appx.txt
findstr /c:"PackageName" appx.txt > applist.txt
setlocal enabledelayedexpansion
set INTEXTFILE=applist.txt
set OUTTEXTFILE=appremove.cmd
set SEARCHTEXT=PackageName : 
set REPLACETEXT=dism /image:mount /remove-provisionedappxpackage /packagename:
set OUTPUTLINE=

for /f "tokens=1,* delims=¶" %%A in ( '"type %INTEXTFILE%"') do (
SET string=%%A
SET modified=!string:%SEARCHTEXT%=%REPLACETEXT%!

echo !modified! >> %OUTTEXTFILE%
)
del appx.txt
del applist.txt
call appremove.cmd
dism /unmount-image /mountdir:mount /commit
ren install.wim install-temp.wim
dism /export-image /sourceimagefile:install-temp.wim /sourceindex:1 /destinationimagefile:install.wim
del install-temp.wim
```

## <a name="span-idboottoauditspanspan-idboottoauditspanspan-idboottoauditspanboottoaudit"></a><span id="BootToAudit"></span><span id="boottoaudit"></span><span id="BOOTTOAUDIT"></span>BootToAudit


Hinzufügen eine Antwortdatei auf dem Windows-Abbild in C:\\binden\\Windows\\Windows\\Panther\\unattend.xml angewiesen, im Überwachungsmodus zu starten. Sie können diese Antwortdatei in Windows System Image Manager erstellen.

### <a name="boottoaudit-x64"></a>BootToAudit x64

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<unattend xmlns="urn:schemas-microsoft-com:unattend">
<!-- BootToAudit-x64.xml -->
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Deployment" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <Reseal>
                <Mode>Audit</Mode>
            </Reseal>
        </component>
    </settings>
</unattend>
```

### <a name="boottoaudit-x86"></a>BootToAudit x86

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<unattend xmlns="urn:schemas-microsoft-com:unattend">
<!-- BootToAudit-x86.xml -->
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Deployment" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <Reseal>
                <Mode>Audit</Mode>
            </Reseal>
        </component>
    </settings>
</unattend>
```

## <a name="span-idkeepingwindowssettingsthrougharecoveryspanspan-idkeepingwindowssettingsthrougharecoveryspanspan-idkeepingwindowssettingsthrougharecoveryspankeeping-windows-settings-through-a-recovery"></a><span id="Keeping_Windows_settings_through_a_recovery"></span><span id="keeping_windows_settings_through_a_recovery"></span><span id="KEEPING_WINDOWS_SETTINGS_THROUGH_A_RECOVERY"></span>Nachhaltiger Schutz von Windows-Einstellungen über eine Wiederherstellung


Windows speichern nicht Automatisches von Einstellungen über unattend.xml Setup-Dateien erstellt wurden, noch Windows-Startmenü Anpassungen, die bei einer gesamten Systems Zurücksetzen noch Info aus oobe.xml erste Anmeldung mit LayoutModification.xml erstellt haben.

Um sicherzustellen, dass Ihre Anpassungen gespeichert sind, die Schritte aus, um die unattend.xml sowie LayoutModification.xml und oobe.xml platzieren sichern Dateien in eine Position. Nachfolgend finden Sie einige Beispielskripts, die zeigen, wie werden diese Einstellungen beibehalten, und setzen Sie sie wieder in die richtigen stellen. Speichern von Kopien der unattend.xml, LayoutModification.xml, "Oobe.xml" sowie diese zwei Textdateien, in C:\\Wiederherstellung\\OEM\\:

### <a name="resetconfigxml"></a>ResetConfig.xml

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
<Reset>
  <Run Phase="BasicReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <Run Phase="FactoryReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
</Reset>
```

### <a name="enablecustomizationsafterrecoverycmd"></a>EnableCustomizationsAfterRecovery.cmd

``` syntax
rem EnableCustomizationsAfterRecovery.cmd

rem Set the variable %TARGETOS%      (Typically this is C:\Windows)
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Set the variable %TARGETOSDRIVE% (Typically this is C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256


rem EnableCustomizationsAfterRecovery.cmd
set ScriptFolder=%~dp0

for /f "skip=2 tokens=2,*" %%a in ('reg.exe query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v "TargetOS"') do set "TargetOS=%%b"
echo TargetOS: %TargetOS% >> %LogFile%
for %%A in (%TargetOS%) do set "TargetOSDrive=%%~dpA"

copy "%ScriptFolder%\Unattend.xml" "%TargetOSDrive%\Windows\Panther\Unattend.xml" /y
copy "%ScriptFolder%\LayoutModification.xml" "%TargetOSDrive%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
copy "%ScriptFolder%\oobe.xml" "%TargetOSDrive%\System32\Info\Oobe.xml" /y
```

Für die Bereitstellung in mehreren Sprachen wird "Oobe.xml" eine komplexere Ordnerstruktur verwendet. Es ist nur die gesamte Ordnerstruktur C: kopiert\\Wiederherstellung\\OEM, und ändern Sie das Skript, um die gesamte Ordner kopieren:

``` syntax
xcopy "%ScriptFolder%\Info\" "%TargetOSDrive%\System32\Info\" /s
```

Weitere Informationen zum Verwenden von Erweiterungspunkte für Drucktaste Zurücksetzen finden Sie unter [Hinzufügen eines Skripts auf Features Drucktaste zurücksetzen](http://go.microsoft.com/fwlink/?LinkId=618946).

## <a name="span-idreinstallwindowsinboxappsspanreinstall-windows-inbox-apps-windows-10-version-1607"></a><span id="Reinstall_Windows_inbox_apps"></span>Installieren von apps für Windows Posteingang (Windows 10 1607 Version)

Installieren von apps für Windows nach dem Hinzufügen einer neuen Sprache. Sie können die apps installieren, ohne sie zuerst zu entfernen. 

### <a name="reinstallinboxapps-x64cmd"></a>ReinstallInboxApps x64.cmd

``` syntax
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsAlarms_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsAlarms_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.BingWeather_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.BingWeather_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCalculator_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCalculator_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCamera_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCamera_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Getstarted_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Getstarted_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsMaps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsMaps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Messaging_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Messaging_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Office.OneNote_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Office.OneNote_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.People_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.People_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Windows.Photos_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Windows.Photos_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.Advertising.Xaml.x64.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.Advertising.Xaml.x86.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsStore_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsStore_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.XboxApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.XboxApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.ZuneMusic_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.ZuneMusic_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.ZuneVideo_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.ZuneVideo_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.SkypeApp_kzf8qxf38zg5c.appxbundle /LicensePath:e:\apps\amd64\Microsoft.SkypeApp_kzf8qxf38zg5c.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.OneConnect_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.OneConnect_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
```

### <a name="reinstallinboxapps-x86cmd"></a>ReinstallInboxApps x86.cmd

``` syntax
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsAlarms_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsAlarms_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.BingWeather_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.BingWeather_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCalculator_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCalculator_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCamera_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCamera_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Getstarted_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Getstarted_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsMaps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsMaps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Messaging_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Messaging_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Office.OneNote_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Office.OneNote_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.People_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.People_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Windows.Photos_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Windows.Photos_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.Advertising.Xaml.x86.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsStore_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsStore_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.XboxApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.XboxApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.ZuneMusic_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.ZuneMusic_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.ZuneVideo_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.ZuneVideo_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.SkypeApp_kzf8qxf38zg5c.appxbundle /LicensePath:e:\apps\x86\Microsoft.SkypeApp_kzf8qxf38zg5c.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.OneConnect_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.OneConnect_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx
```


 