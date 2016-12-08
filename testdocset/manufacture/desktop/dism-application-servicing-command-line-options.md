---
author: Justinha
Description: DISM Anwendung (.msp) Befehlszeilenoptionen zum Warten
ms.assetid: 78ed3303-1e79-4257-ad04-d5f68d34b758
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM-Anwendung – Wartung Befehlszeilenoptionen (.msp)"
ms.openlocfilehash: 8a936ccba97650e16da7156f52f4713fa419ce0e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-application-servicing-msp-command-line-options"></a>DISM-Anwendung – Wartung Befehlszeilenoptionen (.msp)


Befehlszeilenoptionen zum Warten Anwendung kann auf einem offline-Abbild so überprüfen Sie die Verfügbarkeit der Windows Installer-Anwendungspatches (MSP-Dateien) und zum Abfragen der offline-Abbild Informationen zu installierten Windows Installer-Programme und Anwendungspatches (MSP-Dateien) verwendet werden.

Informationen zum Verwenden von Abbildern Bereitstellung und Verwaltung (DISM) mit app-Pakete finden Sie unter [DISM App-Paket (.appx oder .appxbundle) – Wartung Command-Line Options](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md).

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** **/Image:**&lt;*Pfad\_Bild\_Verzeichnis* &gt; \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Die folgenden Optionen stehen zum Auflisten von Windows Installer-Anwendung und Patches für MSP-Anwendung und die Verfügbarkeit einer Anwendung Patches für ein offline-Windows-Abbild überprüfen:

**DISM.exe/Image:**&lt;*Pfad\_auf\_Verzeichnis* &gt; \[ **/Check-AppPatch** | **/Get-AppPatchInfo:** | **/Get-AppPatches** | **/Get-AppInfo** | **/Get-Apps**\]

## <a name="span-idapplicationservicingoptionsspanspan-idapplicationservicingoptionsspanspan-idapplicationservicingoptionsspanapplication-servicing-options"></a><span id="Application_servicing_options"></span><span id="application_servicing_options"></span><span id="APPLICATION_SERVICING_OPTIONS"></span>Anwendung – Wartung Optionen


In diesem Abschnitt wird beschrieben, wie Sie jede Anwendung – Wartung Option. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ Get-Help /?

Unmittelbar nach der ein Paket – Wartung Befehlszeilenoption verwendet wird, ist Informationen zur Option und zu den Argumenten angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild festgelegt ist.

Beispiel:

**DISM /image:C:\\testen\\offline /Check-AppPatch /?**

### <a name="span-idcheck-apppatchpatchlocationpathtopatchmspspanspan-idcheck-apppatchpatchlocationpathtopatchmspspanspan-idcheck-apppatchpatchlocationpathtopatchmspspancheck-apppatch-patchlocationlt-pathtopatchmspgt"></a><span id="_Check-AppPatch__PatchLocation___path_to_patch.msp__"></span><span id="_check-apppatch__patchlocation___path_to_patch.msp__"></span><span id="_CHECK-APPPATCH__PATCHLOCATION___PATH_TO_PATCH.MSP__"></span>/ Kontrollkästchen AppPatch/PatchLocation:&lt; Pfad\_auf\_patch.msp&gt;

Zeigt Informationen nur, wenn die MSP-Patches auf offline-Abbild anwenden. Der Pfad zu der MSP-Patch-Datei muss angegeben werden. Mehrere Patchdateien können angegeben werden.

Beispiel:

**DISM /image:C:\\testen\\offline /Check-AppPatch /PatchLocation:C:\\testen\\MSIPatches\\MsiTestPatch1.msp /PatchLocation:C:\\testen\\MSIPatches\\MsiTestPatch2.msp**

### <a name="span-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanspan-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanspan-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanget-apppatchinfo-patchcodelt-patchcodeguidgt-productcodelt-productcodeguidgt"></a><span id="_Get-AppPatchInfo____PatchCode___patch_code_GUID_____ProductCode___product_code_GUID___"></span><span id="_get-apppatchinfo____patchcode___patch_code_guid_____productcode___product_code_guid___"></span><span id="_GET-APPPATCHINFO____PATCHCODE___PATCH_CODE_GUID_____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get-AppPatchInfo: \[Patchcode:&lt; Patch\_Code\_GUID&gt; \] \[/ProductCode:&lt; Produkt\_Code\_GUID&gt;\]

Enthält detaillierte Informationen zu installierten MSP-Patches nach &lt;Patch\_Code\_GUID&gt; und &lt;Produkt\_Code\_GUID&gt;.

Wenn die Option **Patchcode** angegeben wird, wird detaillierte Informationen für alle Windows Installer-Anwendung angezeigt, die auf der Patch angewendet wird.

Wenn die **Option/ProductCode** angegeben wird, werden Informationen zu allen MSP-Patches in der angegebenen Anwendung angezeigt.

Wenn die Optionen **Patchcode** **und/ProductCode** angegeben sind, werden Informationen angezeigt, nur, wenn der angegebene Patch auf die angegebene Windows Installer-Anwendung angewendet wird.

Mithilfe der **Option/Get-AppPatches** finden Sie den Patch code GUID und Produktcode-GUID, die speziell für den Patch. Verwenden Sie die **Option/Get-Apps** , um alle Produktcode-GUIDs für eine installierte Windows Installer-Anwendung aufzulisten.

Wenn **Patchcode** **und/ProductCode** nicht angegeben wurden, alle installierten Windows Installer-Pakete und MSP-Patches werden angezeigt.

Beispiel:

**DISM /image:C:\\testen\\/offline Get-AppPatchInfo**

**DISM /image:C:\\testen\\/offline Get-AppPatchInfo: Patchcode: {B0B9997C-GUID-GUID-GUID-74D866BBDFFF}**

**DISM /image:C:\\testen\\/offline Get-AppPatchInfo: / ProductCode: {B0F9497C-GUID-GUID-GUID-74D866BBDF59}**

**DISM /image:C:\\testen\\/offline Get-AppPatchInfo: Patchcode: {B0B9997C-GUID-GUID-GUID-74D866BBDFFF} / ProductCode: {B0F9497C-GUID-GUID-GUID-74D866BBDF59}**

### <a name="span-idget-apppatchesproductcodeproductcodeguidspanspan-idget-apppatchesproductcodeproductcodeguidspanspan-idget-apppatchesproductcodeproductcodeguidspanget-apppatches-productcodelt-productcodeguidgt"></a><span id="_Get-AppPatches____ProductCode___product_code_GUID___"></span><span id="_get-apppatches____productcode___product_code_guid___"></span><span id="_GET-APPPATCHES____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get-AppPatches: \[/ProductCode:&lt; Produkt\_Code\_GUID&gt;\]

Zeigt grundlegende Informationen zu allen angewendeten MSP-Patches für alle Anwendungen, die auf die offline-Abbild installiert. Wenn ein Produktcode-GUID angegeben wird, werden Informationen zu allen Patches in der angegebenen Windows Installer-Anwendung angezeigt.

Beispiele:

**DISM /image:C:\\testen\\/offline Get-AppPatches**

**DISM /image:C:\\testen\\/ / offline Get-AppPatches ProductCode: {B0F9497C-GUID-GUID-GUID-74D866BBDF59}**

### <a name="span-idget-appinfoproductcodeproductcodeguidspanspan-idget-appinfoproductcodeproductcodeguidspanspan-idget-appinfoproductcodeproductcodeguidspanget-appinfo-productcodelt-productcodeguidgt"></a><span id="_Get-AppInfo____ProductCode___product_code_GUID___"></span><span id="_get-appinfo____productcode___product_code_guid___"></span><span id="_GET-APPINFO____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get-AppInfo: \[/ProductCode:&lt; Produkt\_Code\_GUID&gt;\]

Zeigt ausführliche Informationen zu einer bestimmten installierten Windows Installer-Anwendung.

Verwenden Sie die **Option/Get-Apps** , um die GUID für eine installierte Windows Installer-Anwendung zu erhalten. Wenn ein Produktcode-GUID nicht angegeben ist, werden Informationen für alle Windows Installer-Anwendungen in der offline-Abbild installiert angezeigt.

Beispiele:

**DISM /image:C:\\testen\\offline /Get-AppInfo**

**DISM /image:C:\\testen\\offline /Get-AppInfo/ProductCode: {B0F9497C-GUID-GUID-GUID-74D866BBDF59}**

### <a name="span-idget-appsspanspan-idget-appsspanspan-idget-appsspanget-apps"></a><span id="_Get-Apps_"></span><span id="_get-apps_"></span><span id="_GET-APPS_"></span>/ Get-Apps

Grundlegende Informationen zu allen Anwendungen für Windows Installer im Offlinemodus Bild angezeigt.

Beispiel:

**DISM /image:C:\\testen\\/offline Get-Apps**

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


**/ Get-AppPatches** **und/Get-AppPatchInfo** gelten nur für installierte Patches (MSP-Dateien).

Wenn Sie die Verfügbarkeit der MSP-Patch ermittelt haben, werden nur der Windows Installer-Anwendung, die für die Patches anwendbar ist angezeigt. Zu viele installierten Clientanwendungen kann ein Update installieren und viele Patches auf eine Anwendung anwenden können.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)

 

 






