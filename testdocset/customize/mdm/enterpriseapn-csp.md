---
title: EnterpriseAPN CSP
description: "Der Dienstanbieter für EnterpriseAPN Konfiguration wird vom Unternehmen zum Bereitstellen einer APN für das Internet verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E125F6A5-EE44-41B1-A8CC-DF295082E6B2
ms.openlocfilehash: 52725c17cd3f121db6b4b65e915b1699fc0f5151
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseapn-csp"></a>EnterpriseAPN CSP


Der EnterpriseAPN Konfiguration-Dienstanbieter (CSP) wird vom Unternehmen zum Bereitstellen einer APN für das Internet verwendet.

> **Hinweis** Der EnterpriseAPN Konfiguration-Dienstanbieter (CSP) ist in Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) nicht unterstützt.

Die folgende Abbildung zeigt den EnterpriseAPN Konfigurationsdienstanbieter im Strukturformat dar.

![Enterpriseapn csp](images/provisioning-csp-enterpriseapn-rs1.png)

<a href="" id="enterpriseapn"></a>**EnterpriseAPN**  
Der Stammknoten für den Dienstanbieter für EnterpriseAPN-Konfiguration.

<a href="" id="enterpriseapn-connectionname"></a>**EnterpriseAPN / ***_ConnectionName_**  
Name der Verbindung Ressourcenverfügbarkeitsdaten vom Windows-Verbindungs-Manager.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-apnname"></a>* *EnterpriseAPN /*ConnectionName*/APNName**  
Enterprise-APN Name.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-iptype"></a>* *EnterpriseAPN /*ConnectionName*/IPType**  
Dieser Wert kann eine der folgenden sein:

-   IPv4 - nur IPv4-Verbindungstyp
-   IPv6 - nur IPv6 Verbindungstyp
-   IPv4v6 (Standard)-IPv4 und IPv6 gleichzeitig.
-   IPv4v6xlat - IPv6 mit IPv4 bereitgestellt von 46xlat

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-isattachapn"></a>* *EnterpriseAPN /*ConnectionName*/IsAttachAPN**  
Boolescher Wert, der angibt, ob diese APN als Teil einer DIESER anfügen angefordert werden sollte. Standardwert ist false.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-classid"></a>* *EnterpriseAPN /*ConnectionName*/ClassId**  
GUID, die an das Modem APN-Klasse definiert. Dies ist identisch mit der OEMConnectionId in CM\_CellularEntries CSP. Normalerweise ist diese Einstellung nicht vorhanden. Es ist nur erforderlich, wenn IsAttachAPN True und Anhängen APN ist nicht nur als die APN Internet verwendet wird.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-authtype"></a>* *EnterpriseAPN /*ConnectionName*/AuthType**  
Authentifizierungstyp. Dieser Wert kann eine der folgenden sein:

-   Keine (Standard)
-   Automatisch
-   PAP
-   CHAP
-   MSCHAPv2

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-username"></a>* *EnterpriseAPN /*ConnectionName*/UserName**  
Der Benutzername für die Verwendung mit PAP, CHAP oder MSCHAPv2 Authentifizierung.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-password"></a>* *EnterpriseAPN /*ConnectionName*/Password**  
Das Kennwort zum Benutzernamen.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-iccid"></a>* *EnterpriseAPN /*ConnectionName*/IccId**  
Chip Karte ID (ICCID) dem Verbindungsprofil Mobilfunk zugeordnet. Wenn dieser Knoten nicht vorhanden ist, wird die Verbindung erstellt, auf einem einzelnen-Steckplatz Gerät mithilfe der ICCID von der UICC und auf einem Dual-Steckplatz Gerät mithilfe der ICCID von der UICC, die für Daten aktiv ist.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-alwayson"></a>* *EnterpriseAPN /*ConnectionName*/AlwaysOn**  
In Windows 10, Version 1607 hinzugefügt. Boolescher Wert, der angibt, ob die CM automatisch auf den APN verbinden versucht, wenn keine Verbindung verfügbar ist.

Der Standardwert ist true.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-connectionname-enabled"></a>* *EnterpriseAPN /*ConnectionName*/ aktiviert **  
In Windows 10, Version 1607 hinzugefügt. Boolescher Wert, der angibt, ob die Verbindung aktiviert ist.

Der Standardwert ist true.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="enterpriseapn-settings"></a>**EnterpriseAPN-Einstellungen**  
In Windows 10, Version 1607 hinzugefügt. Der Knoten, die globale Einstellungen enthält.

<a href="" id="enterpriseapn-settings-allowusercontrol"></a>**EnterpriseAPN/Einstellungen/AllowUserControl**  
In Windows 10, Version 1607 hinzugefügt. Boolescher Wert, der angibt, ob die Mobile UX Benutzern die Verbindung mit anderen als den Enterprise APN APNs zulässt.

Der Standardwert ist false.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="enterpriseapn-settings-hideview"></a>**EnterpriseAPN/Einstellungen/HideView**  
In Windows 10, Version 1607 hinzugefügt. Vom Typ Boolean, der angibt, ob die Mobile UX anzuzeigenden Enterprise APNs zulässig ist. Nur verfügbar, wenn AllowUserControl auf true festgelegt ist.

Der Standardwert ist false.

Unterstützte Vorgänge sind Get und ersetzen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






