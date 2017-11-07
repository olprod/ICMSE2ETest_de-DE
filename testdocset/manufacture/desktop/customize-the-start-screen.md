---
author: Justinha
Description: Anpassen der Startseite
ms.assetid: b28584ec-487e-4b59-a7f6-deb797d464a8
MSHAttr: PreferredLib:/library/windows/hardware
title: Anpassen der Startseite
ms.openlocfilehash: 80032db4abf171bc31cf195207af2c3c0b9e524f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-the-start-screen"></a>Anpassen der Startseite


Sie können Ihre Business-apps auf einem Windows Bild, und passen **die Startseite einbeziehen** hinzufügen. Sie können **die Startseite** für Windows 10 Enterprise, Windows Server 2016 oder einer Domäne gehörenden PC unter Windows 10 Pro anpassen.

Line-of-Business (LOB) Windows Store-apps müssen nicht zertifizierte oder über den Windows Store installiert werden. Hinzufügen von apps, die nicht aus dem Windows-Speicher stammen, wird *Sideloading*aufgerufen. Sideloaded apps müssen mit einem Zertifikat signiert werden, die mit einem vertrauenswürdigen Stammzertifikat verkettet ist. Weitere Informationen zu Sideloading Windows Store-apps, einschließlich Anforderungen finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

Zum Installieren von Windows Store-apps, die nicht Teil der Business-Leitung sind, müssen Sie den Windows Store verwenden.

**In diesem Thema:**

[Verwenden Sie CopyProfile Start Bildschirmlayout beibehalten](#bkmk-copyprofile)

[Kopieren Sie die Datei AppsFolderLayout.Bin Standardlayout Start-Bildschirm festlegen](#bkmk-appfolder)

[Verwenden Sie StartTiles Einstellungen für das Layout der Startseite](#bkmk-starttiles)

## <a name="span-idbkmkcopyprofilespanspan-idbkmkcopyprofilespanspan-idbkmkcopyprofilespanuse-copyprofile-to-preserve-start-screen-layout"></a><span id="BKMK_CopyProfile"></span><span id="bkmk_copyprofile"></span><span id="BKMK_COPYPROFILE"></span>Verwenden Sie CopyProfile Start Bildschirmlayout beibehalten


Die CopyProfile-Methode können Sie Kacheln aus dem Bildschirm **Start** entfernen, Kacheln hinzufügen, Ändern der Größe Kacheln und bezeichnen Kachel Gruppen. CopyProfile können Sie auch Bildschirmfarbe **Starten** , **Starten Sie** Bildschirm Akzent und desktop-Hintergrund anpassen.

Sie können bereitgestellten app-Pakete (.appx) hinzufügen und **die Startseite** für das Windows-Abbild anpassen, bevor Sie das Abbild bereit. Windows-apps, die das Windows-Abbild hinzugefügt werden, heißen apps *bereitgestellt* . Bereitgestellte apps werden im Bild bereitgestellt und installiert sein, damit alle Benutzer des Windows-Abbilds bei der ersten Anmeldung geplant werden.

**Hinweis**  
Wenn Sie sowohl die StartTiles die CopyProfile Einstellungen in die Antwortdatei verwenden, wird CopyProfile die StartTiles Einstellungen außer Kraft setzen. Um die Einstellungen StartTiles auf ein Bild mit CopyProfile generiert verwenden möchten, löschen Sie die appsFolderLayout.bin-Datei aus dem Bild ein. Weitere Informationen zu dieser Datei finden Sie unter [Kopieren Sie die Datei AppsFolderLayout.Bin, um Standardlayout Start-Bildschirm festzulegen](#bkmk-appfolder).

 

**Zum Hinzufügen von apps, die Sie anheften können auf der Startseite**

-   Hinzufügen oder Entfernen von apps aus dem Bild.

    Stellen Sie das Windows-Abbild offline und bereitgestellten app-Pakete für Ihre Business Linie hinzufügen können. Bereitgestellte apps werden für jeden Benutzer bei der ersten Anmeldung die Windows-Abbild installiert. Sie können auch bereitgestellten app-Pakete vom Windows-Abbild, einschließlich Posteingang apps entfernen. Verwenden Sie das Cmdlet Get-AppxProvisionedPackage für PowerShell oder das Deployment Image Servicing and Management Tool (DISM.exe), um eine Liste der Windows Store-apps abzurufen, die im Bild bereitgestellt werden, und wählen Sie apps, die Sie entfernen möchten.

    Weitere Informationen zur Bereitstellung von apps finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

    **Hinweis**  
    Verwenden Sie Windows Store nicht, bevor Sie das Abbild bereit. Sysprep schlägt fehl, wenn Sie apps herunterladen oder app-Updates für bereitgestellte apps, die in das Bild herunterladen. Weitere Informationen finden Sie unter [Entfernen oder Aktualisieren von Windows 8 integrierten Windows Store-apps bewirkt, dass Sysprep ein Fehler auftritt](http://go.microsoft.com/fwlink/?LinkId=271005).

     

    Weitere Informationen zu einem Windows-Abbild bereitstellen finden Sie unter [Mount und eine DISM mithilfe eines Windows Bild ändern](mount-and-modify-a-windows-image-using-dism.md). Weitere Informationen zu DISM-Cmdlets für PowerShell finden Sie unter [Deployment Image Servicing and Management (DISM) Windows PowerShell-Cmdlets](http://go.microsoft.com/fwlink/?LinkId=239926).

**So aktivieren Sie das Administratorkonto**

1.  Bereitstellen des Abbilds auf einem Testcomputer.

    Wenden Sie das Abbild auf einem Testcomputer. Geben Sie beispielsweise an einer Eingabeaufforderung mit erhöhten Rechten:

    ``` syntax
    Dism /apply-image /imagefile:F:\install.wim /index:1 /ApplyDir:C:\
    ```

    Finden Sie weitere Informationen zum Anwenden der Schwelle [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md)ein.

2.  Erstellen Sie ein Testkonto.

    Führen Sie die Bildschirmen Out-of-Box-Experience (OOBE), um ein neues Benutzerprofil einzurichten.

3.  Sideloading zu aktivieren.

    Nachdem Sie ein neues Benutzerprofil erstellt haben, können Sie anmelden, um das Bild und die gruppenrichtlinieneinstellungen für Sideloading aktivieren, wenn Sie nicht bereits getan haben. Weitere Informationen finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

4.  Aktivieren Sie das Administratorkonto an.

    Sie können das Administratorkonto im Windows-Abbild aktivieren. Beispiel:

    1.  Geben Sie im Bildschirm **Start** Computer. Maustaste auf **Computer** in den Suchergebnissen aus, und klicken Sie in der app-Leiste am unteren Rand des Bildschirms auf **Verwalten** .
    2.  Klicken Sie auf **Systemprogramme** , in das Fenster **Computerverwaltung** &gt; **Lokale Benutzer und Gruppen** &gt; **Benutzer** &gt; **Administrator**.
    3.  Deaktivieren Sie im Fenster **Eigenschaften von Administrator** **Konto ist deaktiviert**aus.

5.  Legen Sie den Registrierungsschlüssel FilterAdministratorToken an.

    Sie müssen den Registrierungsschlüssel FilterAdministratorToken festlegen, um das Administratorkonto zum Ausführen von Windows Store-apps zu ermöglichen. Geben Sie zum Beispiel an einer Eingabeaufforderung:

    ``` syntax
    cmd /c reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v FilterAdministratorToken /t REG_DWORD /d 1 /f
    ```

6.  Melden Sie sich als Administrator.

    Melden Sie sich das Testkonto, und melden Sie sich als Administrator.

Jetzt können Sie **die Startseite** in Ihr Administratorkonto konfigurieren, die Sie für jedes neue Benutzerprofil kopieren möchten.

### <a name="span-idstartscreenspanspan-idstartscreenspanspan-idstartscreenspanto-design-the-start-screen"></a><span id="StartScreen"></span><span id="startscreen"></span><span id="STARTSCREEN"></span>Entwerfen **die-Startseite**

Sie können die Startseite für Ihr Unternehmen auf unterschiedlichste Weise anpassen. Sie können Kacheln für Ihre LOB-apps hinzufügen, entfernen Kacheln, Kachel Gruppen verschieben und bezeichnen Kachel Gruppen.

1.  PIN apps auf dem Bildschirm **Start** . Geben Sie den Namen der app, aus dem Bildschirm **Start** . Wenn die app in der Ansicht "Suchergebnisse" angezeigt wird, mit der rechten Maustaste in der app, und klicken Sie dann auf **Pin zu starten**.
2.  Ziehen Sie die Kacheln auf dem Bildschirm **Start** neu anordnen oder gruppieren.
3.  Klicken Sie auf das Lupensymbol in der unteren rechten Ecke im Menü **Start** um **die Startseite** in semantische Zoom anzuzeigen.
4.  Maustaste auf eine Gruppe von apps, und wählen Sie **Gruppe mit Namen**.
5.  Geben Sie einen Namen für jede Gruppe von apps auf **der Startseite** .

### <a name="span-idtosetcopyprofileinanunattendedanswerfilespanspan-idtosetcopyprofileinanunattendedanswerfilespanspan-idtosetcopyprofileinanunattendedanswerfilespanto-set-copyprofile-in-an-unattended-answer-file"></a><span id="To_set_CopyProfile_in_an_unattended_answer_file"></span><span id="to_set_copyprofile_in_an_unattended_answer_file"></span><span id="TO_SET_COPYPROFILE_IN_AN_UNATTENDED_ANSWER_FILE"></span>In einer Antwortdatei CopyProfile festlegen

Eine Antwortdatei können Sie die Beibehaltung des Layouts **der Startseite** , die Sie entworfen. Fügen Sie die Antwortdatei CopyProfile Einstellung auf der specialize-.

1.  Erstellen Sie oder öffnen Sie eine Antwortdatei in Windows System Image Manager (Windows SIM). Weitere Informationen finden Sie unter [Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445).
2.  Klicken Sie im **Windows-Bild** mit der rechten Maustaste **amd64\_Microsoft-Windows-Shell-Setup** oder **X86\_Microsoft-Windows-Shell-Setup**, und wählen Sie dann auf **Hinzufügen-Einstellung zu Pass 4 specialize**.
3.  Wählen Sie im Bereich **Antwortdatei** von Windows SIM **Komponenten\\4 specialize\\Microsoft-Windows-Shell-Setup\_neutrale**.
4.  Klicken Sie im Bereich **Eigenschaften der Microsoft-Windows-Shell-Setup** im Abschnitt **Einstellungen** **CopyProfile** auf **true**festgelegt.

Beispiel für den XML-CODE in einer Antwortdatei CopyProfile festlegen:

``` syntax
<settings pass="specialize">
   <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
     <CopyProfile>true</CopyProfile>
   </component>
</settings>
```

In diesem Beispiel wird für einen Computer mit einer X86 Architektur.

### <a name="span-idtogeneralizeanddeploytheimagespanspan-idtogeneralizeanddeploytheimagespanspan-idtogeneralizeanddeploytheimagespanto-generalize-and-deploy-the-image"></a><span id="To_generalize_and_deploy_the_image"></span><span id="to_generalize_and_deploy_the_image"></span><span id="TO_GENERALIZE_AND_DEPLOY_THE_IMAGE"></span>Verallgemeinern und Bereitstellen des Abbilds

Sie können das Bild bereinigt, vor der Bereitstellung. Bevor Sie ihn auf weiteren Computern bereitstellen können, müssen Sie auch das Bild verallgemeinern. Wenn Sie nicht das Abbild verallgemeinern, kann das Bild nicht mehr verwendet werden.

**Hinweis**   Stellen Sie sicher, dass alle app-Pakete im Bild bereitgestellt werden. Entfernen Sie vor dem Ausführen von Sysprep Pakete app nicht bereitgestellt. Beispielsweise können Sie alle nicht bereitgestellte app-Pakete in PowerShell entfernen:`Get-appxpackage | Remove-appxpackage`

 

Wenn Sie ein Bild mit dem Tool Sysprep verallgemeinern, werden die Hardware-spezifischen Einstellungen aus dem Bild entfernt. Geben Sie die Antwortdatei mit der CopyProfile-Einstellung, um die angepasste beibehalten **Starten** Bildschirmlayout, die Sie erstellt haben.

**Um das Bild zu bereinigen**

1.  Löschen Sie das Testkonto.

    Sie können das Benutzerprofil löschen, die, das Sie verwendet, um das Administratorkonto aktivieren, wenn Sie nicht zum Einschließen in das Windows-Abbild, die Sie in Ihrem Unternehmen bereitstellen möchten. Weitere Informationen finden Sie unter [deaktivieren und Löschen von Benutzerprofilen](http://go.microsoft.com/fwlink/?LinkId=272330).

2.  Setzen Sie den Registrierungsschlüssel zurück.

    Sie sollten den Registrierungsschlüssel FilterAdministratorToken zurückzusetzen, bevor das Abbild bereit. Geben Sie zum Beispiel an einer Eingabeaufforderung:

    ``` syntax
    cmd /c reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v FilterAdministratorToken /t REG_DWORD /d 0 /f
    ```

**Um das Bild verallgemeinern**

-   Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten Sysprep aus, und geben Sie den Speicherort der Datei unbeaufsichtigte. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    %windir%\system32\Sysprep\Sysprep.exe /oobe /generalize /shutdown /unattend:f:\unattend.xml
    ```

Sie können das allgemeine Bild mit dem Tool DISM erfassen und auf mehreren Computern bereitstellen. Weitere Informationen finden Sie unter der [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md). Wenn Sie das Bild anwenden möchten, müssen Sie die angepasste Datei Unattend.xml mit CopyProfile auf "true" festlegen verwenden, um die Änderungen auf dem Bildschirm **Start** beibehalten.

## <a name="span-idbkmkappfolderspanspan-idbkmkappfolderspanspan-idbkmkappfolderspancopy-the-appsfolderlayoutbin-file-to-set-default-start-screen-layout"></a><span id="BKMK_AppFolder"></span><span id="bkmk_appfolder"></span><span id="BKMK_APPFOLDER"></span>Kopieren Sie die Datei AppsFolderLayout.Bin Standardlayout Start-Bildschirm festlegen


Sie können **die Startseite** für Windows 10 Enterprise, Windows Server 2016 oder einer Domäne gehörenden Computer Windows 10 Pro durch Kopieren einer angepassten AppsFolderLayout.bin-Datei in das Standard-Benutzerprofil im Windows-Abbild anpassen. Bei dieser Methode Sie Bereitstellen des Abbilds auf einem Testcomputer, erstellen ein Benutzerprofil, visuell entwerfen **die-Startseite** und diesen Entwurf wieder zurück in das Master-Shape Bild kopieren. Sie können aus dem Bildschirm **Start** app Kacheln entfernen, Kacheln für apps für Windows hinzufügen, Größe Kacheln und bezeichnen Kachel Gruppen.

1.  Auf einen Verweis PC mit Windows 10 Enterprise anpassen Windows Server 2016 oder einer Domäne gehörenden PC unter Windows 10 Pro **die Startseite** .

2.  Führen Sie das Sysprep-Tool zum System Cleanup zu initialisieren. Beispielsweise von einem Typ Befehlszeile:

    ``` syntax
    %windir%\System32\Sysprep\sysprep.exe
    ```

    Wählen Sie **Geben Sie System Überwachungsmodus aktiviert** und **neu starten,** und klicken Sie auf **OK**.

3.  Kopieren Sie die Datei AppsFolderLayout.bin aus dem Benutzerprofil mit der benutzerdefinierten **-Startseite** . Angenommen, um die **Starten** Bildschirm Anpassungen für "TestProfile" auf einem USB-Laufwerk, an der Befehlszeile zu kopieren, geben Sie Folgendes ein:

    ``` syntax
    xcopy C:\Users\TestProfile\AppData\Local\Microsoft\Windows\AppsFolderLayout.bin F:\ /h
    ```

4.  Kopieren Sie in die bereitgestellt oder online Windows-Bild, dem Sie Anpassungen Bildschirm **Starten** , um hinzufügen möchten die AppsFolderLayout.bin-Datei in das Standard-Benutzerprofil. Geben Sie zum Beispiel an einer Eingabeaufforderung:

    ``` syntax
    xcopy F:\AppsFolderLayout.bin C:\Users\Default\AppData\Local\Microsoft\Windows
    ```

    Weitere Informationen zum Bereitstellen eines offline Windows-Abbilds für die Wartung finden Sie unter [Mount und eine DISM mithilfe eines Windows Bild ändern](mount-and-modify-a-windows-image-using-dism.md).

Die **Start** -Bildschirm Anpassungen werden auf jedes neue Benutzerprofil angewendet, die erstellt wird.

Die Datei AppsFolderLayout.bin wird überschrieben, wenn Sie das Abbild verallgemeinern. Sie müssen die Datei hinzufügen, nachdem Sie das Bild allgemeiner (engl.) haben.

## <a name="span-idbkmkstarttilesspanspan-idbkmkstarttilesspanspan-idbkmkstarttilesspanuse-starttiles-settings-to-lay-out-the-start-screen"></a><span id="BKMK_StartTiles"></span><span id="bkmk_starttiles"></span><span id="BKMK_STARTTILES"></span>Verwenden Sie StartTiles Einstellungen für das Layout der Startseite


Sie können Einstellungen in einer Antwortdatei angeben, wie die app die Anzeige auf dem Bildschirm **Start** angeordnet. Kacheln kann nicht entfernt werden, aus dem Bildschirm **Start** oder Beschriftung Gruppen mithilfe der unbeaufsichtigten Einstellungen, jedoch können Sie angeben, wie Kacheln für 24 installierten apps werden mithilfe der StartTiles-Einstellungen angezeigt. Jede Einstellung ordnet eine feste Position in der Bildschirm-Vorlagen **Starten** , und diese Positionen variieren je nach Bildschirmgröße das Ziel des PCs, Auflösung und DPI. Jede Einstellung gibt an, ob die Kachel eine große Kachel oder eine quadratische Kachel für eine app ist oder wenn es sich um eine quadratische Kachel für desktop-app handelt.

**Hinweis**   Wenn Sie sowohl die StartTiles die CopyProfile Einstellungen in die Antwortdatei verwenden, wird CopyProfile die StartTiles Einstellungen außer Kraft setzen.

 

1.  Rufen Sie die AppID Ihrer LOB-Apps.

    Um die Einstellungen für die unbeaufsichtigte Installation verwenden, benötigen Sie die spezifische AppID-Zeichenfolge, die eine installierte app zugeordnet ist. Sie können diese Zeichenfolge erstellen, mit dem Cmdlet Get-AppxPackage in Windows PowerShell. Im folgende Beispiel veranschaulicht das Abrufen der AppID-Zeichenfolge, die in den Einstellungen für die unbeaufsichtigte Installation für jede app verwenden, die bereits auf dem Computer installiert ist:

    ``` syntax
    $installedapps = get-AppxPackage
    foreach ($app in $installedapps)
    {
        foreach ($id in (Get-AppxPackageManifest $app).package.applications.application.id)
        {
            $app.packagefamilyname + "!" + $id
        }
    }
    ```

2.  Öffnen Sie eine Antwortdatei ein.

    Erstellen Sie oder öffnen Sie eine Antwortdatei in Windows System Image Manager (Windows SIM). Weitere Informationen finden Sie unter [Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445).

3.  Fügen Sie der Antwortdatei StartTiles Einstellungen hinzu.

    Verwenden Sie das Microsoft-Windows-Shell-Setup | StartTiles | &lt;TileSetting&gt; Einstellung, um die der app AppID anzugeben, dessen Kachel sollte standardmäßig in einer bestimmten Position auf **der Startseite** angezeigt. Die Kachel Einstellungen führen Sie die drei Benennungsschema:

    -   WideTile und eine Reihe von 01 bis 06.

        Jede app, die Sie für diese Einstellungen angeben muss Ressourcen im app-Manifest angeben, die eine große Kachel bieten. Jede app-Einstellung erfordert, dass Sie die AppID eingeben.

    -   SquareTile und eine Zahl von 01 bis 12.

        Jede app-Einstellung erfordert, dass Sie die AppID eingeben.

    -   DesktopOrSquareTile und eine Zahl zwischen 01 und 06.

        Für apps in einige oder alle der Einstellungen für DesktopOrSquare müssen Sie die AppID für die entsprechenden app oder den Pfad zu der desktop-app angeben.

    **Hinweis**  Wenn Sie eine app, der Breite Kacheln in einem quadratischen Kachel vor Ort unterstützt eingefügt, wird die Kachel gezwungen, quadratisch sein müssen anstelle der gesamten.

     

    Wenn Sie eine Einstellung überspringen, ordnet die Fenster den Ablauf des app-Kacheln, um die Position des app-Kachel Einstellung auf **der Startseite** .

4.  Bereitstellen des Windows-Abbilds geänderte Antwortdatei verwenden.

    Weitere Informationen finden Sie unter [Deploy ein benutzerdefiniertes Bild](deploy-a-custom-image.md).

Weitere Informationen zu diesen Einstellungen finden Sie unter den Themen StartTiles Einstellungen in der Microsoft-Windows-Shell-Setup-Komponente in der [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281) auf TechNet.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md)

[Bereitstellen Sie und ändern Sie ein Windows-Abbild mithilfe von DISM](mount-and-modify-a-windows-image-using-dism.md)

[Anpassen des Standardbenutzerprofils mithilfe von CopyProfile](customize-the-default-user-profile-by-using-copyprofile.md)

[Bereitstellung Imaging – Wartung Management (DISM)-Cmdlets in Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=239926)

 

 






