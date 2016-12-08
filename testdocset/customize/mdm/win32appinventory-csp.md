---
title: Win32AppInventory CSP
description: Win32AppInventory CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C0DEDD51-4EAD-4F8E-AEE2-CBE9658BCA22
ms.openlocfilehash: 4744b46878b2d7ebc0538f430d07d00709bced70
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="win32appinventory-csp"></a>Win32AppInventory CSP


Dienstanbieter Win32AppInventory Konfiguration wird verwendet, um eine Inventur der installierten Programme auf einem Gerät bereitstellen.

Im folgende Diagramm veranschaulicht die Win32AppInventory-Konfiguration dienstanbieterobjekten Management im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM) OMA-Clientbereitstellung und Enterprise DM verwendet.

![win32appinventory Csp Diagramm](images/provisioning-csp-win32appinventory.png)

<a href="" id="--vendor-msft-win32appinventory"></a>**./Vendor/MSFT/Win32AppInventory**  
Der Stammknoten für den Dienstanbieter für Win32AppInventory-Konfiguration.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram"></a>**Win32InstalledProgram**  
Dies stellt eine Inventur der installierten Win32-Anwendung auf dem Gerät.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram"></a>**Win32InstalledProgram /** *InstalledProgram*  
Ein Knoten, der Informationen für eine bestimmte Anwendung enthält.

<a href="" id="win32installedprogram-installedprogram-name"></a>**Win32InstalledProgram /** *InstalledProgram* **/ Name**  
Eine Zeichenfolge, die den Namen der Anwendung angibt.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-publisher"></a>**Win32InstalledProgram /** *InstalledProgram* **Zertifikatsdatei**  
Eine Zeichenfolge, die vom Herausgeber der Anwendung angibt.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-version"></a>**Win32InstalledProgram /** *InstalledProgram* **/ Version**  
Eine Zeichenfolge, die Version der Anwendung angibt.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-language"></a>**Win32InstalledProgram /** *InstalledProgram* **/ Language**  
Eine Zeichenfolge, die Sprache der Anwendung angibt.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-regkey"></a>**Win32InstalledProgram /** *InstalledProgram* **/RegKey**  
Eine Zeichenfolge, die Produkt Code oder in der Registrierung Unterschlüssel angibt.

Bei MSI-basierte Anwendungen ist dies der Produktcode.

Für Applikationen in Software gefunden wurde ist dies der Registrierungsunterschlüssel.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-source"></a>**Win32InstalledProgram /** *InstalledProgram* **/ Source**  
Eine Zeichenfolge, die angibt, in dem die Anwendung ermittelt wurde, beispielsweise MSI oder Programme hinzufügen/entfernen.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-msiproductcode"></a>**Win32InstalledProgram /** *InstalledProgram* **/MsiProductCode**  
Eine GUID, die ein bestimmtes Produkt MSI eindeutig identifiziert.

Der unterstützte Vorgang ist Get.

<a href="" id="win32installedprogram-installedprogram-msipackagecode"></a>**Win32InstalledProgram /** *InstalledProgram* **/MsiPackageCode**  
Eine GUID, die ein MSI-Paket identifiziert. Mehrere Produkte können auf einem einzelnen Paket bereit bilden.

Der unterstützte Vorgang ist Get.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






