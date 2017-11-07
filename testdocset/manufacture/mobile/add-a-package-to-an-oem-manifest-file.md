---
Description: "Eine Feature-Manifestdatei (FM) Datei können Sie bestimmte Typen von Bild Builds definieren, die unterschiedliche optionale Pakete enthalten."
ms.assetid: 5355eea8-550f-4ab5-ba1c-a37689a88b95
MSHAttr: PreferredLib:/library
title: "Hinzufügen eines Pakets zu einer OEM-Manifestdatei"
author: CelesteDG
ms.openlocfilehash: f38e04e7fc0c40ff742df0971a79134ca79a5b1a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-package-to-an-oem-manifest-file"></a>Hinzufügen eines Pakets zu einer OEM-Manifestdatei


Eine Feature-Manifestdatei (FM) Datei können Sie bestimmte Typen von Bild Builds definieren, die unterschiedliche optionale Pakete enthalten. Weitere Informationen zum FM-Dateien finden Sie unter [Feature Dateiinhalten manifest](https://msdn.microsoft.com/library/windows/hardware/dn756745). Weitere Informationen zu zusätzlichen Logik, die das Buildsystem hinzugefügt werden können, finden Sie unter [Feature Gruppierungen und Einschränkungen](https://msdn.microsoft.com/library/windows/hardware/dn756740).

In dieser exemplarischen Vorgehensweise werden die Pakete hinzugefügt erstellten in [Erstellen von mobilen Pakete](creating-mobile-packages.md), in eine Datei FM neue OEM-Features zu definieren, die Sie später zum Erstellen einer mobilen Betriebssystemabbilds hinzufügen können.

**Hinzufügen ein Pakets zu einer FM-Datei**

1.  Erstellen Sie eine neue Datei FM oder Ändern einer vorhandenen Datei FM um umfassen zwei Pakete, die Sie erstellt haben und Feature-IDs für diese Pakete zu definieren. Ein Beispiel dafür, wie die Datei FM aussieht wie WPDKCONTENTROOT % finden Sie unter\\FMFiles\\Arm\\MSOptionalFeatures.xml im Installationsordner von Kit.

    Das folgende Beispiel zeigt, wie die Datei FM aussehen kann.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <FeatureManifest 
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">

      <!-- Other elements that you can configure
      <OEMDevicePlatformPackages>
        <PackageFile Name="Microsoft.Fake.OEMDevicePlatform.spkg" Path="$(mspackageroot)\firmware\Fake\$(cputype)\$(buildtype)" Device="Fake"/>
      </OEMDevicePlatformPackages>

      <BasePackages>
        <PackageFile Path="$(mspackageroot)\drivers\Fake\$(cputype)\$(buildtype)" Name="Microsoft.Fake.AX88772.spkg"/>
      </BasePackages>
      -->

      <Features>  
        <OEM>  
          <PackageFile Path="SourceDirectoryA" Name="MyEchoDriver.spkg">  
            <FeatureIDs>  
              <FeatureID>ECHO_DRIVER</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
          <PackageFile Path="SourceDirectoryB" Name="Contoso.Customization.Notifications.QuickActions.spkg">  
            <FeatureIDs>  
              <FeatureID>QUICK_ACTIONS</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
        </OEM>  
      </Features> 

    </FeatureManifest>
    ```

    Das **OEMDevicePlatformPackages** -Element und **BasePackages** Element sind Platzhalter und nur es zeigen, welche anderen Optionen konfigurieren in der FM-Datei zur Verfügung stehen.

    Weitere Informationen zum Erstellen einer FM Datei und andere Elemente, die möglicherweise Sie Ihrem Feature vollständig zu definieren müssen, finden Sie unter [Feature Dateiinhalt manifest](https://msdn.microsoft.com/library/windows/hardware/dn756745). Weitere Informationen zu zusätzlichen Logik, die Sie den Buildsystem hinzufügen können, finden Sie unter [Feature Gruppen und Einschränkungen](https://msdn.microsoft.com/library/windows/hardware/dn756740).

2.  Ersetzen Sie im ersten **PackageFile** -Element innerhalb des **OEM** -Abschnitts *SourceDirectoryA* durch den Speicherort des Ordners, der das Echo-Treiberpaket enthält, und Ersetzen Sie *MyEchoDriver.spkg* durch die tatsächlichen Namen des der .spkg mit dem Treiber.

3.  Ersetzen Sie im zweiten **PackageFile** Element innerhalb des Abschnitts **OEM** *SourceDirectoryB* durch den Speicherort des Ordners, der das Anpassung der Einstellung Paket enthält, und Ersetzen Sie *Contoso.Customization.Notifications.QuickActions.spkg* durch den tatsächlichen Namen des der .spkg, enthält die Einstellung der Anpassung.

4.  Speichern Sie Ihre FM-Datei in die WPDKCONTENTROOT %\\FMFiles\\Arm-Ordner. In diesem Beispiel als Namen der Datei als ContosoOptionalFeatures.xml.

 

 



