---
title: "Verwaltung mobiler Geräte"
description: "Windows 10 enthält eine Enterprise-Management-Lösung, mit denen IT-Experten Unternehmen Sicherheitsrichtlinien und Geschäftsanwendungen zu verwalten, gleichzeitig Gefährdung der Privatsphäre des Benutzers, auf ihren persönlichen Geräten zu vermeiden."
MS-HAID:
- p\_phDeviceMgmt.provisioning\_and\_device\_management
- p\_phDeviceMgmt.mobile\_device\_management\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 50ac90a7-713e-4487-9cb9-b6d6fdaa4e5b
ms.openlocfilehash: 6b62ae3a537790152cd9362fe0c70c90204ce884
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-device-management"></a>Verwaltung mobiler Geräte


Windows 10 enthält eine Enterprise-Management-Lösung, mit denen IT-Spezialisten Unternehmen Sicherheitsrichtlinien und Geschäftsanwendungen und vermeiden Gefährdung der Privatsphäre auf ihren persönlichen Geräten der Benutzer verwalten. Eine integrierte Management-Komponente kann mit dem Verwaltungsserver kommunizieren.

Es gibt zwei Teilen die Verwaltungskomponente Windows 10:

-   Registrierung Client registriert wird und das Gerät zur Kommunikation mit dem Enterprise-Verwaltungsserver konfiguriert.
-   Die Management Client herunter, der mit dem Verwaltungsserver nach Updates suchen und Anwenden der neuesten vom festgelegten Richtlinien in regelmäßigen Abständen synchronisiert IT.

Drittanbieter-MDM Server können mithilfe des Protokolls MDM Windows 10 verwalten. Der integrierten Management-Client kann mit einem Drittanbieter-Server-Proxy zu kommunizieren, die die Protokolle beschrieben in diesem Dokument zum Ausführen von Verwaltungsaufgaben für Enterprise unterstützt. Drittanbieter-Server müssen die gleiche konsistente erste Teilnehmern Benutzeroberfläche für die Registrierung, die auch Einfachheit für Windows 10 Benutzer bereitstellt. MDM Server müssen nicht zum Erstellen oder zum Verwalten von Windows-10-Client herunterladen. Einzelheiten zu den MDM-Protokollen finden Sie unter [ \[MS-MDM\]: Mobile Gerät Management Protocol](http://go.microsoft.com/fwlink/p/?LinkId=619346) und [ \[MS-MDE2\]: Mobile Device Registrierung Protocol Version 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347).

## <a name="learn-about-device-enrollment"></a>Erfahren Sie mehr über die Registrierung des Geräts


-   [Registrierung des mobilen Geräts](mobile-device-enrollment.md)
-   [Verbundauthentifizierung Gerät Registrierung](federated-authentication-device-enrollment.md)
-   [Registrierung von Zertifikaten Authentifizierung Gerät](certificate-authentication-device-enrollment.md)
-   [Authentifizierung Gerät Registrierung am Standort](on-premise-authentication-device-enrollment.md)

## <a name="learn-about-device-management"></a>Erfahren Sie mehr über die Verwaltung von Geräten


-   [Azure Active Directory-Integration mit MDM](azure-active-directory-integration-with-mdm.md)
-   [Enterprise-app-Verwaltung](enterprise-app-management.md)
-   [Verwaltung der geräteaktualisierung](device-update-management.md)
-   [Aktivieren von offline-Upgrades auf Windows-10 für Windows Embedded 8.1 Handheld-Geräte](enable-offline-updates-for-windows-embedded-8-1-handheld-devices-to-windows-10.md)
-   [Unterstützung des Protokolls für OMA DM](oma-dm-protocol-support.md)
-   [Struktur der OMA DM Dateien zur Bereitstellung](structure-of-oma-dm-provisioning-files.md)
-   [Anforderungen für OMA DM](server-requirements-windows-mdm.md)
-   [Enterprise-Einstellungen, Richtlinien und app-Verwaltung](windows-mdm-enterprise-settings.md)

## <a name="learn-about-configuration-service-providers"></a>Erfahren Sie mehr über die Konfiguration-Dienstanbieter


-   [Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)
-   [WMI-Anbieter in Windows 10 unterstützt](wmi-providers-supported-in-windows.md)
-   [Verwenden von PowerShell-Skripts mit dem WMI-Anbieter-Brücke](using-powershell-scripting-with-the-wmi-bridge-provider.md)
-   [MDM Bridge WMI-Anbieter](https://msdn.microsoft.com/library/windows/hardware/dn905224)

 

 






