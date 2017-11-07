---
author: Justinha
Description: DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten
ms.assetid: 3a2de7c0-d132-41ec-9603-a54e958fee2c
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten
ms.openlocfilehash: 6aeedd8aae97a87a63c83cc85c1ed5edd13e4fc8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-app-package-appx-or-appxbundle-servicing-command-line-options"></a>DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten


Sie können die app-Paket – Wartung Befehle verwenden, hinzufügen, entfernen und Liste app-Pakete (.appx oder .appxbundle) in einem Windows-Abbild bereitgestellt. Ein .appxbundle, neue Features für Windows-10 ist eine Auflistung der app und Ressource Pakete zusammen verwendet, um die app Funktionsspektrum, während der Datenträger Speicherbedarf auf einem bestimmten PC minimieren. Eine ausführliche Dokumentation zu .appxbundle Pakete und die Pipeline Store finden Sie unter [App Packen](http://go.microsoft.com/fwlink/p/?LinkId=698643). Nur eine Teilmenge der Pakete innerhalb einer .appxbundle möglicherweise das Bild hinzugefügt werden, wenn eine Bundle mithilfe von DISM bereitgestellt wird. Weitere Informationen finden Sie unter [Understanding wie DISM fügt .appxbundle Ressource Pakete zu einem Bild](#bkmk-understanding).

Bereitgestellten app-Pakete ein Windows-Abbild hinzugefügt werden und dann installiert sind für alle neuen oder vorhandenen Benutzerprofil das nächste Mal, wenn, das der Benutzer anmeldet. Weitere Informationen, einschließlich Anforderungen für app-Paket Bereitstellung finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

Sie können auch PowerShell hinzufügen, entfernen und app-Pakete (.appx oder .appxbundle) pro Bild oder pro Benutzer in einer Windows-Installation aufgelistet. Weitere Informationen finden Sie unter [Deployment Imaging – Wartung Management (DISM) Windows PowerShell-Cmdlets](http://go.microsoft.com/fwlink/?LinkId=239926) und [App-Installations-Cmdlets in Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=247300).

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Die folgenden app-Paket (.appx oder .appxbundle) Optionen stehen für ein offline-Abbild.

**DISM.exe/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis* &gt; \[ **/Get-ProvisionedAppxPackages** | **/Add-ProvisionedAppxPackage** | **/Remove-ProvisionedAppxPackage** | **/Set-ProvisionedAppxDataFile**\]

Die folgenden app-Paket (.appx oder .appxbundle) Optionen stehen für ein Betriebssystem ausgeführt wird.

**DISM.exe / Online** \[ **/Get-ProvisionedAppxPackages** | **/Add-ProvisionedAppxPackage** | **/Remove-ProvisionedAppxPackage** | **/Set-ProvisionedAppxDataFile**\]

## <a name="span-idapppackageservicingoptionsspanspan-idapppackageservicingoptionsspanspan-idapppackageservicingoptionsspanapp-package-servicing-options"></a><span id="App_package_servicing_options"></span><span id="app_package_servicing_options"></span><span id="APP_PACKAGE_SERVICING_OPTIONS"></span>App-Paket Wartung)


In diesem Abschnitt wird beschrieben, wie Sie jede Option Wartung app. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ Get-Help /?

Wenn unmittelbar nach der ein app-Paket – Wartung Befehlszeilenoption verwendet wird, werden Informationen zur Option und die Argumente angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild angegeben wird.

Beispiele für die:

**DISM /image:C:\\testen\\offline /Add-ProvisionedAppxPackages /?**

**DISM / online /Get-ProvisionedAppxPackages /?**

### <a name="span-idget-provisionedappxpackagesspanspan-idget-provisionedappxpackagesspanspan-idget-provisionedappxpackagesspanget-provisionedappxpackages"></a><span id="_Get-ProvisionedAppxPackages"></span><span id="_get-provisionedappxpackages"></span><span id="_GET-PROVISIONEDAPPXPACKAGES"></span>/ Get-ProvisionedAppxPackages

Zeigt Informationen zur app-Pakete (.appx oder .appxbundle), in einem Bild, die für jeden neuen Benutzer installieren festgelegt sind.

**DISM /Image:C:\\testen\\offline /Get-ProvisionedAppxPackages**

### <a name="span-idadd-provisionedappxpackagespanadd-provisionedappxpackage"></a><span id="Add-ProvisionedAppxPackage"></span>/ Add-ProvisionedAppxPackage

**/ Add-ProvisionedAppxPackage {/FolderPath:&lt; App\_Ordner\_Pfad&gt; \[/SkipLicense\] \[/CustomDataPath:&lt; benutzerdefinierte\_Datei\_Pfad&gt; \] | / PackagePath:&lt; Hauptfenster\_Paket\_Pfad&gt; \[/DependencyPackagePath:&lt; Abhängigkeit\_Paket\_Pfad&gt; \] {\[/LicenseFile:&lt; Lizenz\_Datei\_Pfad&gt;\]|\[/SkipLicense\]} \[/CustomDataPath:&lt; benutzerdefinierte\_Datei\_Pfad&gt; \] }**

Das Bild hinzugefügt eine oder mehrere app-Pakete.

Die app wird das Windows-Abbild hinzugefügt werden und für jede vorhandene registriert oder neue Benutzerprofil der nächsten Anmeldung des Benutzers. Wenn die app zu einem online Bild hinzugefügt wird, wird die app nicht für den aktuellen Benutzer registriert werden, bis das nächste Mal der Benutzer anmeldet.

Verwenden Sie **/FolderPath** , um einen Ordner der entpackten app-Dateien mit einem Hauptfenster Paket, Abhängigkeit Pakete und die Lizenzdatei anzugeben. Dies ist nur für ein Paket entpackt app unterstützt.

Verwenden **Sie/PackagePath** , um ein app-Paket (.appx oder .appxbundle) anzugeben. **/ PackagePath** können beim Bereitstellen einer Line-of-Business-app online.

**Wichtige**  
Verwenden Sie den **Parameter/PackagePath** .appxbundle-Pakete bereitgestellt werden soll.

**/ PackagePath** wird nicht von einem PC-Host unterstützt, die Windows-Vorinstallation-Umgebung (Windows PE) 4.0, Windows Server 2008 R2 oder einer früheren Version von Windows ausgeführt wird.

 

Wenn das Paket abhängig, die architekturspezifische sind ist, müssen Sie alle anwendbaren-Architekturen für die Abhängigkeit auf dem Zielbild installieren. Beispielsweise auf ein X64 Bild als Ziel, einen Pfad zu den X86 und X64 Abhängigkeit-Paketen enthalten oder beide in den Ordner app entpackten Dateien einbinden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Computerarchitektur</th>
<th align="left">Abhängigkeiten zu installieren:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>x64</p></td>
<td align="left"><p>X64 und x86</p></td>
</tr>
<tr class="even">
<td align="left"><p>x86</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ARM</p></td>
<td align="left"><p>Windows RT nur (ARM)</p></td>
</tr>
</tbody>
</table>

 

Verwenden Sie **/CustomDataPath** , um eine Datei optional benutzerdefinierte Daten für eine app anzugeben. Sie können einen beliebigen Dateinamen angeben. Die Datei wird in Custom.dat umbenannt werden, wenn das Bild hinzugefügt wird.

Verwenden Sie **/LicensePath** mit der **Option/PackagePath** , um den Speicherort der XML-Datei mit Ihrer Anwendung Lizenz anzugeben.

Verwenden Sie **/SkipLicense** nur für apps, die keine Lizenz auf eine Sideloading-fähigen Computer erforderlich ist. Verwenden von **/SkipLicense** in anderen Szenarien kann ein Bild beeinträchtigen.

Beispiele:

**DISM /Image:C:\\testen\\offline /Add-ProvisionedAppxPackage /FolderPath:c:\\testen\\Apps\\MyUnpackedApp /CustomDataPath:c:\\testen\\Apps\\CustomData.xml**

**DISM / Online /Add-ProvisionedAppxPackage /PackagePath:C:\\Test\\Apps\\MyPackedApp\\MainPackage.appx /DependencyPackagePath:C:\\Test\\Apps\\MyPackedApp\\Framework-x86.appx /DependencyPackagePath:C:\\Test\\Apps\\MyPackedApp\\Framework-x64.appx /LicensePath:C:\\Test\\Apps\\MyLicense.xml**

**DISM / Online /Add-ProvisionedAppxPackage /FolderPath:C:\\Test\\Apps\\MyUnpackedApp /SkipLicense**

**DISM /Image:C:\\testen\\offline /Add-ProvisionedAppxPackage /PackagePath:C:\\testen\\Apps\\MyPackedApp\\MainPackage.appxbundle /SkipLicense**

### <a name="span-idremove-provisionedappxpackagespanremove-provisionedappxpackage"></a><span id="Remove-ProvisionedAppxPackage"></span>/ Remove-ProvisionedAppxPackage

**/ Remove-ProvisionedAppxPackage/PackageName:&lt; Paketname&gt;**

Bereitstellung für app-Pakete (.appx oder .appxbundle) aus dem Bild entfernt. App-Pakete werden nicht für neue Benutzerkonten registriert werden, die erstellt werden.

**Wichtige**  
Diese Option wird nur Entfernen der Bereitstellung für ein Paket, wenn es Benutzerprofil registriert ist. Verwenden Sie das Cmdlet [Remove-AppxPackage](http://go.microsoft.com/fwlink/?LinkId=215772) in PowerShell, um die app für jeden Benutzer zu entfernen, die es bereits registriert ist, um die app aus dem Bild vollständig zu entfernen.

Wenn die app keine Benutzerprofil registriert wurde, wird die Option /Remove-ProvisionedAppxPackage das Paket vollständig entfernt.

 

Um app-Pakete aus einem Windows Server 2012-Abbild zu entfernen, die den Desktop Experience installiert wurde, müssen Sie die app-Pakete entfernen, bevor Sie den Desktop Experience entfernen. Der Desktopdarstellung ist eine Voraussetzung der **/Remove-ProvisionedAppxPackage** Option für die Server Core-Installationen von Windows Server 2012.

Beispiele für die:

**DISM /Image:C:\\testen\\offline /Remove-ProvisionedAppxPackage /PackageName:microsoft.devx.appx.app1\_1.0.0.0\_neutrale\_ac4zc6fex2zjp**

### <a name="span-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanspan-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanspan-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanset-provisionedappxdatafile-customdatapathlt-customfilepathgt-packagenamelt-packagenamegt"></a><span id="_Set-ProvisionedAppxDataFile___CustomDataPath___custom_file_path____PackageName___PackageName_"></span><span id="_set-provisionedappxdatafile___customdatapath___custom_file_path____packagename___packagename_"></span><span id="_SET-PROVISIONEDAPPXDATAFILE___CUSTOMDATAPATH___CUSTOM_FILE_PATH____PACKAGENAME___PACKAGENAME_"></span>/ Set-ProvisionedAppxDataFile \[/CustomDataPath:&lt; benutzerdefinierte\_Datei\_Pfad&gt; \] /PackageName:&lt; Paketname&gt;

Fügt eine Datei für benutzerdefinierte Daten in das angegebene app-Paket (.appx oder .appxbundle) hinzu.

Angegebene app-Paket (.appx oder .appxbundle) muss bereits auf das Bild vor dem hinzugefügt werden, wenn Sie die benutzerdefinierten Datendatei mit dieser Option hinzufügen. Wenn Sie die Option **/Add-ProvisionedAppxPackage** verwenden, können Sie auch eine Datei für benutzerdefinierte Daten hinzufügen.

Verwenden Sie **/CustomDataPath** , um eine Datei optional benutzerdefinierte Daten für eine app angeben. Sie können einen beliebigen Dateinamen angeben. Die Datei wird in Custom.dat umbenannt werden, wenn das Bild hinzugefügt wird. Wenn eine Datei Custom.dat bereits vorhanden ist, wird sie überschrieben.

Verwenden **Sie/PackageName** , um ein app-Paket (.appx oder .appxbundle) anzugeben.

Beispiele für die:

**DISM.exe /Image:C:\\testen\\offline /Set-ProvisionedAppxDataFile /CustomDataPath:c:\\testen\\Apps\\Custom.dat /PackageName:microsoft.appx.app1\_1.0.0.0\_neutrale\_ac4zc6fex2zjp**

## <a name="span-idbkmkunderstandingspanspan-idbkmkunderstandingspanspan-idbkmkunderstandingspanunderstanding-how-dism-adds-appxbundle-resource-packages-to-an-image"></a><span id="BKMK_understanding"></span><span id="bkmk_understanding"></span><span id="BKMK_UNDERSTANDING"></span>Grundlegendes zu wie DISM Schwelle .appxbundle Ressource Pakete hinzufügt


Wenn das Bild eines .appxbundle hinzugefügt wird, sind nicht alle Ressource Pakete im Bundle anwendbar. Beispielsweise, wenn eine app zu einem Windows-Abbild mit einer Standardsprache Spanisch (Spanien) hinzugefügt wird, sollte Französisch (Frankreich) Ressourcen nicht eingeschlossen werden. Um zu bestimmen, welche Ressourcen auf das Bild hinzugefügt werden, wird mit Paket anwendbar bestimmt:

-   **Sprachpakete Ressource**: ist eine Betriebssystemsprache nicht vorhanden, wird das entsprechende Sprachpaket Ressource app nicht hinzugefügt. Sie möglicherweise beispielsweise ein Bild, das eine Windows-10 mit Englisch (USA) als Standardsprache und ein Spanisch (Spanien)-Sprachpaket enthalten ist. Das Bild werden Englisch (USA) und Spanisch (Spanien) app Ressource Packs hinzugefügt werden. Wenn ein Französisch (Frankreich) Ressource Pack (oder in einer anderen Sprache) in der app-Bundle verfügbar ist, wird es nicht hinzugefügt werden.

-   **Skalierung und DirectX (DXFL) Ressource Packs**: Skalierung und DirectX (DXFL) Ressource Packs hängen von der Hardware-Konfiguration des Windows-Geräts. Da der Typ der Ziel-Hardware zum Zeitpunkt bekannt sein kann nicht die DISM-Befehle werden ausgeführt, alle Skalierung und DXFL Ressource Pakete das Bild an der Bereitstellung der Zeit hinzugefügt werden. Weitere Informationen zum Entwickeln einer app mit Skalierung Ressourcen finden Sie unter [Richtlinien für die Skalierung auf Pixeldichte (Windows Store-apps)](http://go.microsoft.com/fwlink/?LinkId=320890).

Für ein Bild, das mehrere Sprachpakete enthält werden das Bild für jede Sprache app Ressource Pakete hinzugefügt werden. Nachdem Sie der erste Benutzer angemeldet hat, auf den PC mit dem Bild bereitgestellt und der Benutzer verfügt über eine Sprache während OOBE, die nicht zutreffende Ressource Pakete, (Ressource Sprachpakete, Skalierung Ressource Packs und DXFL Ressource Pakete), die nicht übereinstimmen ausgewählt werden für die Benutzerprofile entfernt.

Beispielsweise könnte eine app Amerikanisches Englisch, Französisch (Frankreich) und Spanisch (Spanien) Sprachen unterstützen. Wenn die app, um ein Bild mit Englisch (USA hinzugefügt wird) und Spanisch (Spanien) Sprachpakete vorhanden, wird nur Englisch (USA) und Spanisch (Spanien) werden Ressource Packs auf das Bild hinzugefügt. Klicken Sie dann, wenn ein Benutzer zum ersten Mal anmeldet, und wählt während OOBE, Englisch (USA) als ihre Betriebssystemsprache, werden Pakete Ressource Spanisch (Spanien) entfernt nach Abschluss der Anmeldung.

**Wichtige**  
Wenn Sie hinzufügen oder eines Language Packs aus einem Bild entfernen, ändern Sie den Anwendungsbereich Kontext, die in eine Menge falsch oder unvollständig Ressource Pakete im Bild verlassen führen können. Wenn ein Sprachpaket hinzugefügt oder entfernt wird, müssen Sie das Bild erneut, aller .appxbundle-Pakete (einschließlich aller Abhängigkeit Pakete und Windows Store-Lizenz-Datei) hinzufügen. Dadurch wird sichergestellt, dass die korrekte Liste der Ressource Pakete bereitgestellt ist.

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


-   Sie können kein app-Paket (.appx) auf einem Betriebssystem installieren, die apps für Windows 8 nicht unterstützt. Sie können ein app-Paket-Paket (.appxbundle) nicht installieren, auf einem Betriebssystem, die mindestens nicht unterstützt Windows 8.1 apps. Apps werden nicht auf Windows PE 4.0, die Windows Server 2012 Server Core-Installationsoption oder auf alle Versionen von Windows, die älter sind als Windows 8 und Windows Server 2012 unterstützt.

    Zum Installieren und Ausführen von apps auf Windows Server 2012, müssen Sie den [Desktop Experience](http://go.microsoft.com/fwlink/?LinkId=247330)installieren.

-   Die Option **/FolderPath** wird nur für app-Pakete, die auf der Grundlage der Formats .appx unterstützt.

-   **/ PackagePath** muss immer für .appxbundle Pakete verwendet werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md)
