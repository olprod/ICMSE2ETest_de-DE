---
title: "Serveranforderungen für die Verwendung der OMA DM zum Verwalten von Windows-Geräten"
description: "Serveranforderungen für die Verwendung der OMA DM zum Verwalten von Windows-Geräten"
MS-HAID:
- p\_phDeviceMgmt.server\_requirements\_for\_oma\_dm
- p\_phDeviceMgmt.server\_requirements\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5b90b631-62a6-4949-b53a-01275fd304b2
ms.openlocfilehash: ef4e13f94de994a4f19352df6ff84598f4a034ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="server-requirements-for-using-oma-dm-to-manage-windows-devices"></a>Serveranforderungen für die Verwendung der OMA DM zum Verwalten von Windows-Geräten

In der folgenden Liste zeigt die allgemeine serveranforderungen für die Verwendung der OMA DM zum Verwalten von Windows-Geräten:

-   Der OMA DM-Server muss die OMA DM v1.1.2 oder höher-Protokoll unterstützen.

-   Secure Sockets Layer (SSL) muss auf dem Server OMA DM, und er muss Server zertifikatbasierte Authentifizierung, Daten Überprüfung der Integrität und Verschlüsselung von Daten bereitstellen. Wenn das Zertifikat nicht von einer kommerziellen Zertifizierungsstelle ausgegeben wird, dessen Stammzertifikat im Gerät vorinstalliert ist, müssen Sie das Stammzertifikat für Unternehmen in das Gerät Stammspeicher bereitstellen.

-   Für die Authentifizierung des Clients auf Anwendungsebene müssen Sie Basic oder MD5-Client-Authentifizierung verwenden.

-   Die Server MD5 Nonce muss in jede Sitzung DM verlängert. Der DM Client sendet die neue Server Nonce für die nächste Sitzung mit dem Server über die Status-Element in jeder DM-Sitzung.

-   MD5 binary Nonce ist über XML B64 codierten Format, aber oktale Form von binären Daten senden sollte verwendet werden, wenn der Dienst den Hash berechnet.

    Weitere Informationen zu Basic oder Clientauthentifizierung MD5, MD5-Hash und Nonce MD5, die OMA Gerät Management Security-Spezifikation finden Sie unter (OMA-TS-DM\_Security-V1\_2\_1-20080617-A), von der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)zur Verfügung.

-   Der Server muss über HTTPS unterstützen.

 





