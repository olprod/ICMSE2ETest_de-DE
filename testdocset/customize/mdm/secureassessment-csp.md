---
title: SecureAssessment CSP
description: SecureAssessment CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6808BE4B-961E-4638-BF15-FD7841D1C00A
ms.openlocfilehash: e1294917c23927e6ef0e81088a6aed3a460cfff2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secureassessment-csp"></a>SecureAssessment CSP


Der Dienstanbieter für SecureAssessment Konfiguration wird verwendet, um die Konfigurationsinformationen für den sicheren Assessment Browser bereitstellen.

Das folgende Diagramm zeigt die SecureAssessment Konfiguration dienstanbieterobjekten Management im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM), OMA-Clientbereitstellung und Enterprise-DM verwendet.

![secureassessment](images/secureassessment-csp.png)

<a href="" id="--vendor-msft-secureassessment"></a>**./Vendor/MSFT/SecureAssessment**  
Der Stammknoten für den Dienstanbieter für SecureAssessment-Konfiguration.

Der unterstützte Vorgang ist abrufen.

<a href="" id="launchuri"></a>**LaunchURI**  
URI-Link zu einer Bewertung, die automatisch geladen wird, wenn der sicheren Assessment Browser gestartet wird.

Der unterstützte Vorgang ist hinzufügen, löschen, Get und ersetzen.

<a href="" id="testeraccount"></a>**TesterAccount**  
Der Benutzername des Tests Berücksichtigung.

-   Verwenden Sie zum Angeben eines Domänenkontos Domäne\\Benutzer.
-   Verwenden Sie zum Angeben eines Kontos AAD username@tenant.com ein.
-   Verwenden Sie den Benutzernamen aus, um ein lokales Konto anzugeben.

Der unterstützte Vorgang ist hinzufügen, löschen, Get und ersetzen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






