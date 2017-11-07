---
title: CSP-Bereitstellung
description: "Dienstanbieter Provisioning Konfiguration wird für die Registrierung von Massen Benutzer an einen Dienst MDM verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5D6C17BE-727A-4AFA-9F30-B34C1EA1D2AE
ms.openlocfilehash: df5aac53628115223a3e2acbbb21a21a384b2c1a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="provisioning-csp"></a>CSP-Bereitstellung


Dienstanbieter Provisioning Konfiguration wird für die Registrierung von Massen Benutzer an einen Dienst MDM verwendet.

> **Hinweis**  Massen-Registrierung funktioniert nicht, wenn zwei Faktoren-Authentifizierung aktiviert ist.

 

Massen-Registrierung schrittweise Anleitung finden Sie unter [Bulk-Registrierung](bulk-enrollment-using-windows-provisioning-tool.md).

Das folgende Diagramm zeigt den Provisioning Konfiguration-Dienstanbieter im Strukturformat dar.

![Bereitstellung Csp-Diagramm](images/provisioning-csp-provisioning.png)

<a href="" id="--vendor-msft"></a>**./Vendor/MSFT**  
Stammknoten für CSP bereitstellen.

<a href="" id="provisioning-enrollments"></a>**Bereitstellung/Registrierung**  
Knoten zum Definieren von Massen-Registrierung von Benutzern in einem Webdienst MDM.

<a href="" id="provisioning-enrollments-upn"></a>**Bereitstellung/wichtige / ***_UPN_**  
Eindeutiger Bezeichner für die Registrierung. Für die Registrierung Massen muss dies ein Dienstkonto, das zum Registrieren Sie mehrere Benutzer zulässig ist. Beispiel"generic-device@contoso.com"

<a href="" id="provisioning-enrollments-upn-discoveryservicefullurl"></a>* *Provisioning/wichtige/*UPN*/DiscoveryServiceFullURL**  
Der vollständige URL für den Suchdienst.

<a href="" id="provisioning-enrollments-upn-secret"></a>* *Provisioning/wichtige/*UPN*/Secret**  
Diese Informationen sind abhängig von der AuthPolicy verwendet wird. Mögliche Werte:

-   Kennwortzeichenfolge für die Authentifizierung auf standortbasierte Registrierung
-   Verbundpartner Sicherheitstoken für Verbundpartner Registrierung
-   Zertifikat Ziehpunkt print für die zertifizierten Basis-Registrierung

<a href="" id="provisioning-enrollments-upn-authpolicy"></a>* *Provisioning/wichtige/*UPN*/AuthPolicy**  
Gibt die Authentifizierungsrichtlinie vom MDM-Dienst verwendet. Gültige Werte:

-   Lokale Verwaltungs
-   Zertifikat

<a href="" id="provisioning-enrollments-upn-policyservicefullurl"></a>* *Provisioning/wichtige/*UPN*/PolicyServiceFullURL**  
Gibt die Richtlinie-Dienst-URL.

<a href="" id="provisioning-enrollments-upn-enrollmentservicefullurl"></a>* *Provisioning/wichtige/*UPN*/EnrollmentServiceFullURL**  
Gibt die Registrierung-Dienst-URL.

 

 






