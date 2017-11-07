---
author: Justinha
Description: "Normalerweise können Sie wieder in Windows Imaging und Konfiguration Designer (ICD) Projekte, bearbeiten und erneut bereitstellen und immer wieder gehen."
ms.assetid: 88b2c902-4bd2-4d09-814b-be86c75c8085
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übung 1c: Ändern einer vorhandenen Windows ICD Project"
ms.openlocfilehash: 2f25e2bb65d4c2970894cc961bfe94961ffe531c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1c-modify-an-existing-windows-icd-project"></a>Übung 1c: Ändern einer vorhandenen Windows ICD Project


Sie können in der Regel wechseln Sie wieder in Windows Imaging und Konfiguration Designer (ICD) Projekte, bearbeiten und erneut bereitstellen immer wieder.

**Hinweis**  Kopieren Sie alle neuen Quelldateien wie die Bereitstellung Pakete wieder auf den PC-Techniker, bevor Sie beginnen. Dies verringert das Risiko unterbrechen Buildvorgang aus ein Problem mit der temporären oder das USB-Gerät zu trennen.

 

## <a name="span-idchangetheeditionforexamplefromcoretoprospanspan-idchangetheeditionforexamplefromcoretoprospanspan-idchangetheeditionforexamplefromcoretoprospanchange-the-edition-for-example-from-core-to-pro"></a><span id="Change_the_edition__for_example__from_Core_to_Pro_"></span><span id="change_the_edition__for_example__from_core_to_pro_"></span><span id="CHANGE_THE_EDITION__FOR_EXAMPLE__FROM_CORE_TO_PRO_"></span>Ändern Sie die Edition (z. B. von Kern pro)


Exportieren Sie Ihr Projekt Windows ICD in einer Bereitstellung Paket. Sie können ein neues Projekt klicken Sie dann in ein anderes Bild schnell auf eine andere Edition erstellen mithilfe dieses provisioning Paket Windows ICD erstellen.

## <a name="span-idtousemorethanoneprovisioningpackagespanspan-idtousemorethanoneprovisioningpackagespanspan-idtousemorethanoneprovisioningpackagespanto-use-more-than-one-provisioning-package"></a><span id="To_use_more_than_one_provisioning_package_"></span><span id="to_use_more_than_one_provisioning_package_"></span><span id="TO_USE_MORE_THAN_ONE_PROVISIONING_PACKAGE_"></span>Verwenden Sie mehrere provisioning-Pakets:


Verwenden Sie den Befehl ICD.exe, um die Bereitstellung Pakete zu kombinieren.

``` syntax
"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\icd.exe" /Build-ImageFromWIM /MediaPath:"c:\WICDOutput" /SourceImage:"C:\Images\install.wim" /ImageIndex:1 /ProvisioningPackage:"c:\users\terry\Documents\Windows Imaging and Configuration Designer (WICD)\Fabrikam_Notebook_1\Fabrikam_Notebook_1.ppkg" /DeploymentConfigXml:"C:\Samples\DeploymentConfig.xml" /CustomizationXML:"C:\Samples\Customizations.xml" 
```

Wobei /ImageIndex der Index des Windows-Abbilds ist, den Sie verwenden möchten. Beachten Sie welches Windows-Abbild verwenden. Die Client-SKU install.wim-Datei umfasst zwei verschiedene Bilder:

-   Index 1 ist Windows 10 Professional
-   Index 2 ist Windows 10 Core

## <a name="span-idcreateadeploymentconfigurationfilespanspan-idcreateadeploymentconfigurationfilespanspan-idcreateadeploymentconfigurationfilespancreate-a-deployment-configuration-file"></a><span id="Create_a_deployment_configuration_file"></span><span id="create_a_deployment_configuration_file"></span><span id="CREATE_A_DEPLOYMENT_CONFIGURATION_FILE"></span>Erstellen einer Konfigurationsdatei für die Bereitstellung


Der Befehl ICD.exe erfordert eine Bereitstellung XML-Konfigurationsdatei. Wenn Sie die UI WICD verwenden, wird diese Datei für Sie erstellt. Bei Verwendung der Command-Line ICD müssen Sie es erstellen und es als DeploymentConfigXml-Parameter im Befehl angeben. Es folgt ein Beispiel, das Sie für diese Übungseinheit verwenden können:

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<DeploymentConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Deployment-Config.v1.0">
    <EnableCompactOS>false</EnableCompactOS>
    <MediaScenario>Production</MediaScenario>
</DeploymentConfig>
 
```

Windows ICD erstellt das Projekt im Pfad, den Sie auswählen. Sie können dann kopieren Sie diese Daten in einen USB-Schlüssel und laden das Abbild auf einen neuen PC.

## <a name="span-idcreateablankcustomizationsfilespanspan-idcreateablankcustomizationsfilespanspan-idcreateablankcustomizationsfilespancreate-a-blank-customizations-file"></a><span id="Create_a_blank_customizations_file"></span><span id="create_a_blank_customizations_file"></span><span id="CREATE_A_BLANK_CUSTOMIZATIONS_FILE"></span>Erstellen Sie eine leere Anpassungsdatei


Für diesen Build von Windows 10 müssen Sie eine Anpassungsdatei mithilfe des Parameters CustomizationXML angeben. Das Bereitstellung Paket sollte alle Ihre Anpassungen enthalten, damit wir eine leere Anpassungen-XML-Datei für diese Übungseinheit erstellen können:

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<WindowsCustomizations>
  <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
    <ID>{c4b32e84-249f-4a07-976a-e482f0a2ee58}</ID>
    <Name>Fabrikam_Notebook_1_Core</Name>
    <Version>1.0</Version>
    <OwnerType>OEM</OwnerType>
    <Rank>0</Rank>
  </PackageConfig>
  <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
</Settings>
</WindowsCustomizations>

 
```

## <a name="span-idcongratulationsspanspan-idcongratulationsspanspan-idcongratulationsspancongratulations"></a><span id="Congratulations_"></span><span id="congratulations_"></span><span id="CONGRATULATIONS_"></span>Herzlichen Glückwunsch!


Sie haben den Windows-ICD Teil der Übungseinheit abgeschlossen. Hier erfahren Sie mehr über die klassische Windows-Bereitstellungsverfahren in [Übung 2](part-2--classic-style-deployment.md).

 

 





