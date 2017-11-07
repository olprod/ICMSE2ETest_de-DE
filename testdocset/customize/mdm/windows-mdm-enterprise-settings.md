---
title: Enterprise-Einstellungen, Richtlinien und app-Verwaltung
description: "Die tatsächlichen Management Interaktion zwischen dem Gerät und dem Server erfolgt über den DM-Client. Der DM Client kommuniziert mit dem Enterprise-Verwaltungsserver über DM 1.2 SyncML Syntax."
MS-HAID:
- p\_phdevicemgmt.enterprise\_settings\_\_policies\_\_and\_app\_management
- p\_phDeviceMgmt.windows\_mdm\_enterprise\_settings
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 92711D65-3022-4789-924B-602BE3187E23
ms.openlocfilehash: 602e4dcc2920876621cddd3dadd04147351cd15d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprise-settings-policies-and-app-management"></a>Enterprise-Einstellungen, Richtlinien und app-Verwaltung

Die tatsächlichen Management Interaktion zwischen dem Gerät und dem Server erfolgt über den Client DM. Der DM Client kommuniziert mit dem Enterprise-Verwaltungsserver über DM 1.2 SyncML Syntax. Der vollständige Erläuterung der OMA DM-Protokoll v1. 2 finden Sie unter der [OMA-Website](http://go.microsoft.com/fwlink/p/?LinkId=267526).

Windows unterstützt derzeit einen MDM Server. Der DM-Client, die über die Registrierung konfiguriert ist der Zugriff gewährt für die Unternehmenssuche bezogene Einstellungen. Enterprise-MDM Einstellungen werden über verschiedene Konfigurationsdienstanbieter an den Client DM verfügbar gemacht. Die Liste der verfügbaren Konfigurationsoptionen-Dienstanbieter finden Sie unter [Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md).

Der Client DM wird bei der Registrierung durch den Taskplaner MDM Server daher in regelmäßigen Abständen aufgerufen werden konfiguriert.

Das folgende Diagramm zeigt den Workflow zwischen Server und Client.

![Windows-Client und Server Mdm-Diagramm](images/enterprise-workflow.png)


## <a name="management-workflow"></a>Workflow für die Verwaltung

Dieses Protokoll definiert eine HTTPS-basierte Client/Server-Kommunikation mit DM SyncML XML als Nutzlast Paket, die von Verwaltungsanfragen und die Ergebnisse der Ausführung wird ausgeführt. Die Anforderung Konfiguration wird über ein verwaltetes Objekt (MO) behandelt. Die Einstellungen, die vom verwalteten Objekt unterstützt werden in einer konzeptionellen Struktur dargestellt. Dieser logische Ansicht der konfigurierbaren geräteeinstellungen vereinfacht der Server die geräteeinstellungen Adressen durch die Implementierungsdetails aus der konzeptionellen Struktur isolieren.

Um die Kommunikation mit dem Remoteserver für Enterprise Management mit erhöhter Sicherheit zu erleichtern, unterstützt Windows zertifikatbasierte gegenseitigen Authentifizierung über einen verschlüsselten HTTP-SSL-Kanal zwischen den DM Client und Management-Dienst. Die Zertifikate für Server und Clients werden während der Registrierung bereitgestellt.

DM-Client-Konfiguration, Unternehmen durchsetzen, Verwaltung von Business und Geräteübersicht sind alle verfügbar gemacht werden oder über den Konfigurations-Dienstanbieter (CSP) ausgedrückt. Kryptografiedienstanbieter sind der Windows-Begriff für verwalteten Objekte. Der Client DM kommuniziert mit dem Server und Kryptografiedienstanbieter Konfiguration Anforderung an. Der Server muss nur wissen, die logische lokalen URIs durch diesen Knoten CSP, um das Protokoll DM XML verwenden, um das Gerät verwalten definiert.

Hier ist eine Zusammenfassung der DM Aufgaben für Enterprise Management unterstützt:

-   Gruppenrichtlinien-Verwaltungskonsole des Unternehmens: Richtlinien sind über die Richtlinie CSP unterstützt Unternehmen ermöglicht Unternehmen, die verschiedene Einstellungen verwalten. Es ermöglicht dem Management-Dienst so konfigurieren Sie Gerät verwandte Richtlinien zu sperren, aktivieren/deaktivieren die Speicherkarte und die Verschlüsselung Gerätestatus Abfragen. RemoteWipe CSP können IT-Experten den internen Benutzer Datenspeicher Remote vollständig zu löschen.
-   Verwaltung von Enterprise: dies über Enterprise ModernApp Management CSP und mehrere ApplicationManagement-bezogene Richtlinien adressiert ist. Er wird verwendet, um das Token Enterprise installieren, Query Business Anwendungsnamen und Versionen usw. installiert. Dieser CSP kann nur vom Enterprise-Dienst zugegriffen werden.
-   Zertifikat Management: CertificateStore CSP, RootCACertificate CSP und ClientCertificateInstall CSP werden verwendet, um Zertifikate zu installieren.
-   Grundlegende Device-Inventar und Asset Management: einige grundlegende Geräteinformationen über DevInfo CSP, DevDetail Kryptografiedienstanbieter und DeviceStatus CSP abgerufen werden kann. Grundlegende Device Informationen wie OEM-Name, Gerätemodell, Hardwareversion, Betriebssystemversion, Prozessortypen usw. nutzen. Dies ist für Asset Management und Zielgerät. NodeCache CSP ermöglicht das Gerät nur senden Delta Inventar Einstellungen an den Server, um over-the-Daten zu verringern. NodeCache CSP ist nur durch den Enterprise-Dienst zugegriffen werden.

 






