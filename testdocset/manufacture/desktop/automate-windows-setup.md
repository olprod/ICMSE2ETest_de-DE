---
author: Justinha
Description: Automatisieren der Windows-Setup
ms.assetid: 882a3774-d0c3-405f-af31-2b9a5d1458d5
MSHAttr: PreferredLib:/library/windows/hardware
title: Automatisieren der Windows-Setup
ms.openlocfilehash: 0811a566f920a01fbeb30302f37b4b34de552042
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="automate-windows-setup"></a>Automatisieren der Windows-Setup


Sie können einige oder alle Seiten der Benutzeroberfläche (UI) von Windows® Setup verhindern, dass während der Installation angezeigt wird. Das Standardverhalten von Windows Setup wird zum Anzeigen der Setup-Benutzeroberfläche, wenn die erforderlichen Werte falsch oder leer sind.

## <a name="span-iduseananswerfilewhileinstallingwindowsspanspan-iduseananswerfilewhileinstallingwindowsspanspan-iduseananswerfilewhileinstallingwindowsspanuse-an-answer-file-while-installing-windows"></a><span id="Use_an_answer_file_while_installing_Windows"></span><span id="use_an_answer_file_while_installing_windows"></span><span id="USE_AN_ANSWER_FILE_WHILE_INSTALLING_WINDOWS"></span>Verwenden Sie eine Antwortdatei während der Installation von Windows


Sie können Windows-Installation mithilfe einer Antwortdatei automatisieren:

**Verwenden Sie ein USB-Laufwerk**

1.  Verwenden Sie eine Beispieldatei Antwort ein, oder erstellen Sie eigene mit Windows System Image Manager (Windows SIM).

2.  Speichern Sie die Datei als **Autounattend.xml** auf der Stammebene der einem USB-Laufwerk ein.

3.  Auf einem neuen PC tragen Sie die Windows-Produkt-DVD und der USB flash-Laufwerk, und starten Sie den PC. Wenn keine andere Antwortdatei ausgewählt ist, sucht Windows Setup nach dieser Datei.

**Wählen Sie eine Antwortdatei**

-   Sie können eine bestimmten Antwortdatei während der Installation von der Windows-Umgebung Vorinstallation starten und mit dem Befehl " **setup.exe** " und Auswählen der **/ für die unbeaufsichtigte Installation:***Filename* -Option.

Beispiele für Antwortdateien und eine Liste der Einstellungen, zum Automatisieren einer Installation verwendet werden finden Sie unter Einstellungen für die Automatisierung von Windows Setup.

## <a name="span-idsampleanswerfilesspanspan-idsampleanswerfilesspanspan-idsampleanswerfilesspansample-answer-files"></a><span id="Sample_answer_files"></span><span id="sample_answer_files"></span><span id="SAMPLE_ANSWER_FILES"></span>Beispiele für Antwortdateien


Die folgenden Beispieldateien umfasst Windows Assessment and Deployment Kit (Windows ADK) in den folgenden Ordner:

C:\\Programmdateien (x86)\\Windows Kits\\8.0\\Assessment and Deployment Kit\\Bereitstellungstools\\Beispiele\\unbeaufsichtigten.

## <a name="span-idlistofsettingsspanspan-idlistofsettingsspanspan-idlistofsettingsspanlist-of-settings"></a><span id="List_of_settings"></span><span id="list_of_settings"></span><span id="LIST_OF_SETTINGS"></span>Liste der Einstellungen


Es folgt eine Liste der Einstellungen in diese Antwortdateien verwendet:

-   Windows-Setup spracheinstellungen: Microsoft-Windows-International-Core-Windows PE\\[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224328) und Microsoft-Windows-International-Core-Windows PE\\SetupUILanguage\\[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224329).

-   Produktschlüssel: Einrichten von Microsoft Windows\\UserData\\ProductKey\\[Schlüssel](http://go.microsoft.com/fwlink/?LinkId=224330).

## <a name="span-idautomatingwindowssetupspanspan-idautomatingwindowssetupspanspan-idautomatingwindowssetupspanautomating-windows-setup"></a><span id="Automating_Windows_Setup"></span><span id="automating_windows_setup"></span><span id="AUTOMATING_WINDOWS_SETUP"></span>Automatisieren von Windows Setup


Fügen Sie zum Automatisieren von Windows Setup Einstellungen für jede der folgenden Seiten Windows Setup zu Ihrer Antwortdatei. Wenn eine Einstellung für eine Windows-Setup-Seite konfiguriert ist, überspringt Windows Setup diese Seite an.

### <a name="span-idlanguageregionandinputmethodselectionpagespanspan-idlanguageregionandinputmethodselectionpagespanspan-idlanguageregionandinputmethodselectionpagespanlanguage-region-and-input-method-selection-page"></a><span id="Language__Region__and_Input_Method_Selection_Page_"></span><span id="language__region__and_input_method_selection_page_"></span><span id="LANGUAGE__REGION__AND_INPUT_METHOD_SELECTION_PAGE_"></span>Sprache und Region Eingabemethode Auswahlseite

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-International-Core-Windows PE | [UILanguage](http://go.microsoft.com/fwlink/?LinkId=224328)</p></td>
<td align="left"><p>Gibt die Standardsprache für das installierte Windows-Betriebssystem verwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft-Windows-International-Core-Windows PE | SetupUILanguage | [UILanguage](http://go.microsoft.com/fwlink/?LinkId=224329)</p></td>
<td align="left"><p>Gibt die Standardsprache, während der Installation von Windows verwenden. Während der Installation zeigt Windows Setup Installationsstatus in der ausgewählten Sprache.</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Wenn Sie eine Autounattend.xml-Datei mit Windows Setup verwenden und einer Suche impliziten Antwortdatei abhängig, wird die Sprache Auswahlseite im Setup nicht angezeigt, selbst wenn Sie spracheinstellungen nicht explizit in der Antwortdatei konfigurieren. Weitere Informationen zu impliziten Antwortdateien finden Sie unter [Übersicht über die Automatisierung von Windows Setup](windows-setup-automation-overview.md).

 

### <a name="span-idtypeyourproductkeyforactivationpagespanspan-idtypeyourproductkeyforactivationpagespanspan-idtypeyourproductkeyforactivationpagespantype-your-product-key-for-activation-page"></a><span id="Type_your_Product_Key_for_Activation_Page"></span><span id="type_your_product_key_for_activation_page"></span><span id="TYPE_YOUR_PRODUCT_KEY_FOR_ACTIVATION_PAGE"></span>Geben Sie den Product Key für die Aktivierungsseite

Der Product Key muss die Windows-Version übereinstimmen, die Sie installieren möchten. Weitere Informationen finden Sie unter [Arbeiten mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | UserData | ProductKey | [Schlüssel](http://go.microsoft.com/fwlink/?LinkId=224330)</p></td>
<td align="left"><p>Gibt den Product Key zum Installieren von Windows verwendet.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Einrichten von Microsoft Windows | ImageInstall | OSImage | InstallFrom | Metadaten | ([Schlüssel](http://go.microsoft.com/fwlink/?LinkId=252771) und [Wert](http://go.microsoft.com/fwlink/?LinkId=252772)).</p></td>
<td align="left"><p>Schlüssel verwenden und Wert zusammen aus einem bestimmten Windows-Abbild zu installieren. Bei einigen Windows Server® 2012-Editionen erforderlich.</p>
<p>Sie können die Bildinformationen abrufen, mit dem DISM /Get-ImageInfo Befehl. Weitere Informationen finden Sie unter [Image Management Command-Line Options](http://go.microsoft.com/fwlink/?LinkId=208186).</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idacceptmicrosoftsoftwarelicensetermspagespanspan-idacceptmicrosoftsoftwarelicensetermspagespanspan-idacceptmicrosoftsoftwarelicensetermspagespanaccept-microsoft-software-license-terms-page"></a><span id="Accept_Microsoft_Software_License_Terms_Page"></span><span id="accept_microsoft_software_license_terms_page"></span><span id="ACCEPT_MICROSOFT_SOFTWARE_LICENSE_TERMS_PAGE"></span>Akzeptieren Sie, dass Microsoft-Software-Lizenz Seite Begriffe

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | "UserData" | [AcceptEula](http://go.microsoft.com/fwlink/?LinkId=224331)</p></td>
<td align="left"><p>Gibt an, ob während des Setups Windows Microsoft-Software-Lizenzbedingungen zu akzeptieren.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idselectupgradeorcustominstallationpagespanspan-idselectupgradeorcustominstallationpagespanspan-idselectupgradeorcustominstallationpagespanselect-upgrade-or-custom-installation-page"></a><span id="Select_Upgrade_or_Custom_Installation_Page"></span><span id="select_upgrade_or_custom_installation_page"></span><span id="SELECT_UPGRADE_OR_CUSTOM_INSTALLATION_PAGE"></span>Wählen Sie Upgrade oder Seite benutzerdefinierte Installation

Standardmäßig wird eine Antwortdatei verwendet, diese Seite wird nicht angezeigt und Windows als eine neue Installation konfiguriert ist. Fügen Sie die folgende Einstellung, um Windows als ein Upgrade zu konfigurieren:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | UpgradeData | [Aktualisieren](http://go.microsoft.com/fwlink/?LinkId=224332)</p></td>
<td align="left"><p>Gibt an, dass die Installation vorhanden, ein Upgrade von einer früheren Version von Windows ist.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspecify-where-to-install-windows-page"></a><span id="Specify_Where_to_Install_Windows_Page"></span><span id="specify_where_to_install_windows_page"></span><span id="SPECIFY_WHERE_TO_INSTALL_WINDOWS_PAGE"></span>Geben Sie an, wo auf der Seite Windows installieren.

Sie können entweder die genaue Datenträger-ID und Partitions-ID angeben, oder Sie können Windows auf der ersten verfügbaren Partition installieren. Um den Partitionen vorkonfigurieren, müssen Sie auch Ihre-Partitionen zu konfigurieren. Vollständige XML-Beispielen und empfohlene Partition Konfigurationen finden Sie unter [wie Configure UEFI/GPT-Based Festplattenpartitionen](http://go.microsoft.com/fwlink/?LinkId=214261) oder [Configure BIOS/MBR-Based Festplatte Partitionen](http://go.microsoft.com/fwlink/?LinkId=214260).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-Setup | ImageInstall | OSImage | InstallTo | [DiskID](http://go.microsoft.com/fwlink/?LinkId=224334)</p></td>
<td align="left"><p>Gibt den Datenträger, auf dem Windows installiert wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Einrichten von Microsoft Windows | ImageInstall | OSImage | InstallTo | [PartitionID](http://go.microsoft.com/fwlink/?LinkId=224335)</p></td>
<td align="left"><p>Gibt die Partition, auf dem Windows installiert wird.</p></td>
</tr>
</tbody>
</table>

 

\endash oder \endash

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | ImageInstall | OSImage | [\ImageInstall\OSImage](http://go.microsoft.com/fwlink/?LinkId=224335)</p></td>
<td align="left"><p>Gibt an, dass Windows auf der ersten verfügbaren Partition installieren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsettingstousewithunattendedwindowsdeploymentservicesspanspan-idsettingstousewithunattendedwindowsdeploymentservicesspanspan-idsettingstousewithunattendedwindowsdeploymentservicesspansettings-to-use-with-unattended-windows-deployment-services"></a><span id="Settings_to_Use_with_Unattended_Windows_Deployment_Services"></span><span id="settings_to_use_with_unattended_windows_deployment_services"></span><span id="SETTINGS_TO_USE_WITH_UNATTENDED_WINDOWS_DEPLOYMENT_SERVICES"></span>Einstellungen für die Verwendung mit dem unbeaufsichtigten Windows-Bereitstellungsdienste


Beim Bereitstellen von Windows mithilfe von Windows-Bereitstellungsdienste jede Einstellung in den folgenden Abschnitten der unbeaufsichtigten Installation Antwortdatei hinzufügen. Dies sind die einzigen Einstellungen für eine unbeaufsichtigte Installation erforderlich.

### <a name="span-idselectalanguageandlocalepagespanspan-idselectalanguageandlocalepagespanspan-idselectalanguageandlocalepagespanselect-a-language-and-locale-page"></a><span id="Select_a_Language_and_Locale_Page"></span><span id="select_a_language_and_locale_page"></span><span id="SELECT_A_LANGUAGE_AND_LOCALE_PAGE"></span>Wählen Sie eine Sprache und Gebietsschema-Seite

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-International-Core-Windows PE | SetupUILanguage | [UILanguage](http://go.microsoft.com/fwlink/?LinkId=224337)</p></td>
<td align="left"><p>Gibt die Standardsprache, die während der Installation von Windows verwenden.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idprovidewindowsdeploymentservicescredentialspagespanspan-idprovidewindowsdeploymentservicescredentialspagespanspan-idprovidewindowsdeploymentservicescredentialspagespanprovide-windows-deployment-services-credentials-page"></a><span id="Provide_Windows_Deployment_Services_Credentials_Page"></span><span id="provide_windows_deployment_services_credentials_page"></span><span id="PROVIDE_WINDOWS_DEPLOYMENT_SERVICES_CREDENTIALS_PAGE"></span>Bereitstellen von Windows Deployment Services-Seite Anmeldeinformationen

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | WindowsDeploymentServices | [Anmeldung](http://go.microsoft.com/fwlink/?LinkId=224338)</p></td>
<td align="left"><p>Gibt die Anmeldeinformationen für die Windows-Bereitstellungsdienste Anmeldung verwendet, und gibt an, in welchen Umständen die Benutzeroberfläche für die Anmeldung angezeigt wird.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idselectanimagetoinstallpagespanspan-idselectanimagetoinstallpagespanspan-idselectanimagetoinstallpagespanselect-an-image-to-install-page"></a><span id="Select_an_Image_to_Install_Page"></span><span id="select_an_image_to_install_page"></span><span id="SELECT_AN_IMAGE_TO_INSTALL_PAGE"></span>Wählen Sie ein Bild auf der Seite installieren

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | WindowsDeploymentServices | [ImageSelection](http://go.microsoft.com/fwlink/?LinkId=224339)</p></td>
<td align="left"><p>Gibt das Bild, das installiert werden und der Speicherort, auf dem er installiert ist, sowie, ob die Benutzeroberfläche angezeigt wird.</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspecify-where-to-install-windows-page"></a><span id="Specify_Where_to_Install_Windows_Page"></span><span id="specify_where_to_install_windows_page"></span><span id="SPECIFY_WHERE_TO_INSTALL_WINDOWS_PAGE"></span>Festlegen Sie, wohin Seite Windows installieren

Diese Einstellung wird davon ausgegangen, dass Sie auf einem partitionierten Laufwerk installieren.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Einrichten von Microsoft Windows | WindowsDeploymentServices | ImageSelection | InstallTo | [DiskID](http://go.microsoft.com/fwlink/?LinkId=224340)</p></td>
<td align="left"><p>Gibt die ID der Datenträger des Datenträgers, der das Bild ist installiert werden soll.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Einrichten von Microsoft Windows | WindowsDeploymentServices | ImageSelection | InstallTo | [PartitionID](http://go.microsoft.com/fwlink/?LinkId=224342)</p></td>
<td align="left"><p>Gibt die ID der Partition, die das Bild ist installiert werden soll.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Einstellungen für die Automatisierung von OOBE](settings-for-automating-oobe.md)

[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

 

 






