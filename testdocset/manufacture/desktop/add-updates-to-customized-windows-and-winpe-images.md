---
author: Justinha
Description: "Microsoft bietet Updatepakete auf Windows-10, die müssen auf Ihrer angepassten Windows-Abbildern installiert werden zu können. Fügen Sie das Zero-Day-Paket (ZDP) zu Ihren vorhandenen Windows 10 Bildern, Ihren Benutzern mit den neuesten Updates bereitzustellen."
ms.assetid: 3273a638-d635-45e8-b418-ee9c5b06333e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Updates zu benutzerdefinierten Windows-Abbilder"
ms.openlocfilehash: 45f861a9e61b35c48ee20fce7138996ffb673c08
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-updates-to-customized-windows-images"></a>Hinzufügen von Updates zu benutzerdefinierten Windows-Abbilder


Microsoft bietet Updatepakete bis 10 für Windows, die auf Ihrer angepassten Windows-Abbildern installiert sein müssen. Fügen Sie das Zero-Day-Paket (ZDP) zu Ihren vorhandenen Windows 10 Bildern, Ihren Benutzern mit den neuesten Updates bereitzustellen.

In diesem Thema wird beschrieben, wie der ZDP zu einem Windows-Abbild, zusätzlich zu einem anderen Update zu installieren, die Microsoft für Windows 10 veröffentlicht wird.

Das Update ZDP ist, dass ein Rollup von alle Updates zwischen Windows 10 Build 10240 und dem heutigen freigegeben.

**Hinweis**  Wie 8. August 2015:
-   Verwenden Sie Windows PE und Windows RE Versionen von ADK Build 10240. Die Version von Windows PE oder Windows RE nicht aktualisiert werden, falls nichts anders gilt.
-   Verwenden Sie nach dem Anwenden der ZDP offline nicht **/ResetBase** (DISM /Cleanup-Image /ResetBase). Die ZDP hat ausstehende Aktionen, die erledigt werden müssen, bevor Sie /ResetBase ausführen.
-   Sie können nicht einfach den ZDP in eine unbeaufsichtigte Installation Antwortdatei hinzufügen – das gesamte Bild muss vor der Installation aktualisiert.

 

## <a name="span-idstartwithyourcustomizedimagespanspan-idstartwithyourcustomizedimagespanspan-idstartwithyourcustomizedimagespan-start-with-your-customized-image"></a><span id="_Start_with_your_customized_image"></span><span id="_start_with_your_customized_image"></span><span id="_START_WITH_YOUR_CUSTOMIZED_IMAGE"></span>Beginnen Sie mit Ihrer angepassten Abbilds


Beginnen Sie mit den vorhandenen Windows-Abbild mit Windows-10 Build 10240 angepasst werden.

Berücksichtigen Sie später hinzufügen Sprachpakete, bevor Sie die Updates ZDP hinzufügen – möglicherweise Sie sparen Zeit. Weitere Informationen finden Sie finden Sie in den Hinweisen am Ende dieses Thema und [Hinzufügen von Language Packs auf Windows](add-language-packs-to-windows.md).

## <a name="span-iddownloadthezdpspanspan-iddownloadthezdpspanspan-iddownloadthezdpspan-download-the-zdp"></a><span id="_Download_the_ZDP"></span><span id="_download_the_zdp"></span><span id="_DOWNLOAD_THE_ZDP"></span>Laden Sie die ZDP


Laden Sie die neuesten Updates. Beachten Sie, dass die ZDP ist ein kumulatives Update, müssen Sie nur das neueste Updatepaket erhalten möchten.

-   64-Bit-Version von Windows 10: <http://go.microsoft.com/fwlink/?LinkId=619271>.
-   32-Bit-Version von Windows 10: [http://go.microsoft.com/fwlink/?LinkId=619272](http://go.microsoft.com/fwlink/?LinkId=619271).

## <a name="span-idupdateyourimagesspanspan-idupdateyourimagesspanspan-idupdateyourimagesspanupdate-your-images"></a><span id="Update_your_images"></span><span id="update_your_images"></span><span id="UPDATE_YOUR_IMAGES"></span>Aktualisieren Sie Ihre Bilder


1.  Ihres PC-Technikers und klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.
2.  Erstellen Sie ein Mount-Verzeichnis für das Windows-Abbild (install.wim), und stellen Sie das Abbild.

    ``` syntax
    md C:\mount\Windows

    Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:C:\mount\Windows
    ```

3.  Aktualisieren Sie Ihre Windows-Abbilder mit den neuesten ZDP an. Beispiel:

    ``` syntax
    Dism /Add-Package /Image:C:\mount\Windows /PackagePath:C:\MSU\Windows10-KBxxxxxxx-x64.msu /LogPath:AddPackage.log
    ```

    Wobei C:\\MSU\\Windows10-KBxxxxxxx-x64.msu die aktuellste Version von der ZDP verfügbar ist.

4.  Heben Sie die Bereitstellung des Windows-Abbilds.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\Windows /Commit
    ```

**Empfohlen: Starten Sie das Bild, um den Vorgang abzuschließen, und klicken Sie dann das Bild bereinigen**

1.  Starten eines Reference-Geräts mit Windows PE.
2.  Drücken Sie **STRG + UMSCHALT + F3** OOBE Bildschirmen Überwachungsmodus eingeben.
3.  Öffnen Sie das Eingabeaufforderungsfenster als Administrator.
4.  Bereinigen Sie die Windows-Abbild. (Es ist OK, um /ResetBase verwenden Sie nun an, dass der PC-Option im Überwachungsmodus gestartet wurde.)

    ``` syntax
    Dism /Cleanup-Image /Online /StartComponentCleanup /ResetBase
    ```

    **Hinweis**  Kann werden nicht zum Bereinigen des Windows-Abbilds erst nach der es gestartet haben.

     

5.  Verwenden Sie Sysprep verallgemeinern, und fahren Sie den PC.

    ``` syntax
    C:\Windows\System32\Sysprep\sysprep /generalize /shutdown /oobe
    ```

6.  Starten Sie den PC zu Windows PE. Wenn der PC Windows neu gestartet startet, müssen Sie lassen Sie ihn abschließt, und dann mithilfe von Sysprep verallgemeinern, und fahren Sie den PC erneut.
7.  Erstellen Sie ein temporäres Verzeichnis Scratch für DISM auf einem physischen Laufwerk, statt das Standard Windows PE virtuellen-Laufwerk, um Probleme im Zusammenhang mit der Angabe kurzer Dateinamen zu vermeiden. Damit das Aufzeichnen der DISM von in der das Bild Ereignisprotokollen wird, wählen Sie einen Speicherort, das in der Liste DISM Ausschluss ist, beispielsweise in C:\\Recycler. Weitere Informationen finden Sie unter [Liste der DISM-Konfiguration und WimScript.ini Dateien](dism-configuration-list-and-wimscriptini-files-winnext.md).

    ``` syntax
    md C:\Recycler\Scratch
    ```

8.  Erfassen Sie das Windows-Abbild. Dies zeichnet die angewendeten Updates und entfernt alle Dateien, die als während DISM /Cleanup-Image abgelöst gekennzeichnet wurden. Speichern Sie die Datei an einem Speicherort auf einem USB-Laufwerk oder im Netzwerk (Beispiel: N:\\Bilder), und benennen Sie dem Bild (Beispiel: "Enterprise\_X64 mit ZDP KBxxxxxxx").

    ``` syntax
    DISM /Capture-Image /ImageFile:"N:\Images\install_updated.wim" /CaptureDir:C: /Name: "Enterprise_x64 with ZDP KBxxxxxxx" /ScratchDir:C:\Recycler\Scratch
    ```

 **Startbare Windows-setupmedien aktualisieren**

1.  Kopieren Sie startbaren Medium (DVDs oder anderen startbaren Medien für Setup Windows, Windows Deployment Services (WDS) oder System Center) in einen beschreibbaren Ordner auf Ihrem PC.

    ``` syntax
    Xcopy D:\ C:\InstallMedia /s /h
    ```

2.  Binden Sie die Datei: Quellen\\boot.wim.

    ``` syntax
    md C:\mount\boot
    Dism /Mount-Image /ImageFile:"C:\InstallMedia\sources\boot.wim" /Index:1 /MountDir:C:\mount\boot
    ```

3.  Fügen Sie der ZDP hinzu.

    ``` syntax
    Dism /Add-Package /PackagePath:/PackagePath:C:\MSU\Windows10-KBxxxxxxx-x64.msu /Image:C:\mount\boot /LogPath:AddPackage.log
    ```

    Wobei C:\\MSU\\Windows10-KBxxxxxxx-x64.msu ist die aktuellste Version von den ZDP verfügbar.

4.  Navigieren Sie im Windows-Explorer zum Stammordner bereitgestellten Abbild und sortieren Sie die Liste der Dateien nach Änderungsdatum. Kopieren Sie alle Elemente, die wurde zuletzt geändert (setup.exe, locale.nls, setupplatform.dll, setupplatform.exe, reagent.dll und keine anderen Einstellungen, die zuletzt geändert von sieht) in den Stamm des Mediums installieren.
5.  Heben Sie die Bereitstellung der Datei boot.wim.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\boot /Commit
    ```

6.  Erstellen eines startbaren Mediums (DVDs oder andere startbaren Medien für das Setup für Windows, Windows Deployment Services (WDS) oder System Center) mithilfe der Dateien. Weitere Informationen finden Sie unter [Technische Referenz für Windows](windows-setup-technical-reference.md).

## <a name="span-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanspan-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanspan-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanadding-languages-after-adding-the-zdp-or-other-rollup-packages"></a><span id="Adding_languages_after_adding_the_ZDP_or_other_rollup_packages"></span><span id="adding_languages_after_adding_the_zdp_or_other_rollup_packages"></span><span id="ADDING_LANGUAGES_AFTER_ADDING_THE_ZDP_OR_OTHER_ROLLUP_PACKAGES"></span>Hinzufügen von Sprachen nach dem Hinzufügen der ZDP oder andere Rollup-Pakete


Idealerweise sollten Sie alle Language Packs und Komponenten hinzufügen, bevor Sie ZDPs oder Windows Rollup Pakete hinzufügen.

Wenn Sie bei Bedarf nach der Installation der ZDP oder anderen Rollup Package Language Packs oder Sprachfeatures hinzufügen müssen, müssen Sie das Paket ZDP-Rollup anschließend erneut anwenden. Sie andernfalls die Benutzeroberfläche von Windows möglicherweise nicht ordnungsgemäß lokalisiert und Benutzer möglicherweise aufgefordert, die Sprachressourcen von Windows Update herunterladen.

## <a name="span-idsamplescriptspanspan-idsamplescriptspanspan-idsamplescriptspansample-script"></a><span id="Sample_script"></span><span id="sample_script"></span><span id="SAMPLE_SCRIPT"></span>Beispielskript


Das folgende Beispielskript ändert ein Windows Bild durch alle Updates in einem bestimmten Ordner in das Bild hinzufügen. Nach dem Hinzufügen des Bilds, bereinigt es das Bild ein.

``` syntax
REM # InjectPackages.cmd: Adds packages (.cbs, .cab, .msu) to a Windows image
REM # Usage:   InjectPackages <.WIM file> <Index> <Folder with CBS packages>
REM # Example: InjectPackages C:\Images\install.wim 1 C:\Packages\ZDP
REM #
REM # Given a Windows image, an index, and a folder with packages (.cbs, .cab, or .msu),
REM # this injects the packages into the wim offline
REM #

@echo off
echo %date% - %time%:: starting ,,,

set _dism_log=%~dp0dism_add_packages.log
del %_dism_log%

set _input_wim=%1
echo %date% - %time%:: caller gave us a wim: [%_input_wim%]. dir it to verify ,,,
     dir %_input_wim%
if not exist %_input_wim% (
 echo fail!!! %_input_wim% not found
 exit /b 2
)

set _index=%2
echo %date% - %time%:: caller gave us index=[%_index%]. verify it,,,
echo %date% - %time%:: dism /logpath=%_dism_log% /get-imageinfo /imagefile=%_input_wim% /index=%_index%
     dism /logpath=%_dism_log% /get-imageinfo /imagefile=%_input_wim% /index=%_index%
if %errorlevel% neq 0 (
  echo dism failed!!! please verify index [%_index%] is correct.
  exit /b %errorlevel%
)


set _package_folder=%3
echo %date% - %time%:: caller gave us folder: [%_package_folder%]. dir it to verify ,,,
     dir %_package_folder%\
if not exist %_package_folder%\ (
 echo fail!!! %_package_folder%\ not found!
 exit /b 2
)

if not exist %~dp0mnt\ (
 mkdir %~dp0mnt\
)

echo %date% - %time%:: unmount to start clean. you can ignore if this fails.
echo %date% - %time%:: dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /discard
     dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /discard

echo %date% - %time%:: mount the input wim ,,,
echo dism /logpath=%_dism_log% /mount-image /imagefile=%_input_wim% /index=%_index% /mountdir=%~dp0mnt\ 
     dism /logpath=%_dism_log% /mount-image /imagefile=%_input_wim% /index=%_index% /mountdir=%~dp0mnt\ 
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)
echo %date% - %time%:: good.

echo %date% - %time%:: look for *.msu files ,,,
echo dir %_package_folder%\*.msu
     dir %_package_folder%\*.msu
for /r %_package_folder% %%a in (*.msu) do (
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
  if %errorlevel% neq 0 (
    echo dism failed!!! 
    exit /b %errorlevel%
  )
)

echo %date% - %time%:: look for *.cab files ,,,
echo dir %_package_folder%\*.cab
     dir %_package_folder%\*.cab
for /r %_package_folder% %%a in (*.cab) do (
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
  if %errorlevel% neq 0 (
    echo dism failed!!! 
    exit /b %errorlevel%
  )
)

echo %date% - %time%:: DONE adding packages.

echo %date% - %time%:: run clean up ,,,
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /cleanup-image /startcomponentcleanup
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /cleanup-image /startcomponentcleanup
  REM ### Do not use /ResetBase. The ZDP has pending actions that must be completed first.##

  if %errorlevel% neq 0 (
    echo dism failed to clean up. we ignore this for now.
  )



echo %date% - %time%:: commiting the changes ,,,
echo dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /commit
     dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /commit
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)


echo %date% - %time%:: exporting the wim to reduce size ,,,
echo dism /logpath=%_dism_log% /export-image /sourceimagefile=%_input_wim% /sourceindex=%_index% /destinationimagefile=%_input_wim%_exported.wim
     dism /logpath=%_dism_log% /export-image /sourceimagefile=%_input_wim% /sourceindex=%_index% /destinationimagefile=%_input_wim%_exported.wim
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)

echo %date% - %time%:: ALL DONE.
dir %_input_wim% 
dir %_input_wim%_exported.wim
echo please use %_input_wim%_exported.wim for further testing.
```

 

 





