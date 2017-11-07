---
title: Device.Connectivity.Server
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: f12460d25dba7b316e6327d425d1f8246df472e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.Server

 - [Device.Connectivity.Server](#device.connectivity.server)
-->

<a name="device.connectivity.server"></a>
##Device.Connectivity.Server

### <a name="deviceconnectivityserverserveroutofbandmanageability"></a>Device.Connectivity.Server.ServerOutOfBandManageability

*Server Baseboard Management Controller (BMC) Geräte müssen Out-of-Band-Management-Funktionen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

BMC Geräte müssen Server Hardware Out-of-Band-Management-Funktion mit IPMI 2.0 über ein LAN und/oder serielle Schnittstellen sowie über den KCS Systemkanal über den IPMI-Treiber in-Band unterstützen.

Es ist nicht erforderlich, dass der BMC die vollständige IPMI 2.0-Spezifikation implementiert, da nur eine Teilmenge der Funktionalität für Out-of-Band-Verwaltung erforderlich ist. Der BMC muss die folgenden Funktionen unterstützen:

1.  Das System Boot Quelle ist über die BMC konfigurierbar.

    1.  Der BMC muss die folgenden Vorgänge durchgeführt werden, auf dem Server unterstützen. Diese Funktionalität wird mithilfe des Befehls Set System Boot Options implementiert.

        1.  Der Server kann zum nächsten Starten von der PXE-Server konfiguriert werden Zeit wird zurückgesetzt

        2.  Der Server kann von der Festplatte des nächsten Starten konfiguriert werden Zeit wird zurückgesetzt

        3.  Der Server kann so konfiguriert werden, um immer vom PXE-Server zu starten

        4.  Der Server kann so konfiguriert werden, dass immer von der Festplatte zu starten

2.  Des Systems BMC Firmware und BIOS-Version, dass Informationen durch den BMC verfügbar gemacht wird.

    1.  Der BMC muss die Versionsinformationen für die folgenden Komponenten verfügbar machen:

        1.  BIOS (über den Befehl Get-System Info Parameters).

        2.  BMC Management Firmware (über die Geräte-Id abrufen-Befehl).

3.  Die OOB Management LAN-Konfiguration kann durch den BMC aktualisiert werden.

    1.  Dies gilt nur für Systeme, die über den IPMI/LAN-Kanal BMC verfügbar machen. Das Verwaltungsvorgänge werden über in-Band-Kanal, über den IPMI-Treiber durchgeführt. Der BMC muss die folgende Informationen über einen eigenen LAN-Konfiguration mithilfe des Befehls Get LAN Konfigurationsparameter verfügbar machen:

        1.  Indikator wird, ob der BMC mit einer statischen IP-Adresse konfiguriert ist oder wenn eine von DHCP zugewiesen.

        2.  IP-Adresse

        3.  Subnetzmaske

        4.  Standardgateway

    2.  BMC muss die folgenden Vorgänge durchgeführt werden, über den Befehl LAN Konfigurationsparameter festlegen unterstützen:

        1.  BMC kann mit einer statischen IP-Adresse, Subnetzmaske und Standard-Gateway-IP-Adresse konfiguriert werden

        2.  BMC kann so konfiguriert werden, um die IP-Adresse vom DHCP-Server zu erhalten.

4.  Der Status des Systems Power kann über die BMC verwaltet werden.

    1.  Der BMC muss die folgenden Server Systeminformationen verfügbar machen:

        1.  Aktuellen Power Status des Servers (über den Befehl Get-Chassis-Status)

    2.  Der BMC muss die folgenden Vorgänge durchgeführt werden, auf dem Server über den Befehl Chassis-Steuerelement unterstützen:

        1.  Die Leistungsfähigkeit der Server kann deaktiviert werden.

        2.  Der Server kann eingeschaltet werden

        3.  Die Leistungsfähigkeit Server kann zurückgesetzt werden

5.  BMC verhindert nicht vertrauenswürdigen Zugriff auf die Server-Systems.

    1.  Der IPMI belegt Authentifizierungsmechanismus stellt eine Reihe von Sicherheitsrisiken, die Sicherheitslücken in einem BMC mit unsichere Konfiguration sind. Um einige dieser Sicherheitslücken zu verringern, ist die folgende Konfiguration auf zertifizierten BMCs vorhanden:

        1.  BMC darf keine Remotezugriff auf die LAN-Kanal, mit der RAKP zulassen-keine Algorithmus Authentication.

        2.  BMC darf kein Benutzerkonto für anonyme Benutzer standardmäßig konfiguriert haben. Wenn dieses Konto vorhanden ist, muss es deaktiviert werden.

6.  Das System Lösungsentwickler wird durch den BMC verfügbar gemacht.

    1.  Der BMC muss die folgenden Server Systeminformationen verfügbar machen:

        1.  Hersteller der Serverhardware (Read FRU Data-Befehl)

        2.  Modell der Serverhardware (Read FRU-Data-Befehl)

        3.  Server SMBIOS GUID (System GUID Get-Befehl)

            1.  Das erwartete Format der GUID in der Leitung entspricht dem Format in der SMBIOS 2,8-Spezifikation (DSP0134) beschrieben. D. h., die 00112233-4455-6677-8899-AABBCCDDEEFF GUID wird als 33 22 11 00 55 44 77 66 88 99 übertragen AA BB CC DD EE FF durch den Befehl System-GUID abgerufen.

        4.  Asset-Tag des Servers (Read FRU Data-Befehl)

        5.  Seriennummer des Servers (Read FRU-Data-Befehl)

        6.  Ereignisprotokoll Systemzeit des Servers (Get Auswahl Time-Befehl)

        7.  Ereignisprotokoll Kapazität Systeminformationen (Auswahl Ablage-Befehl)

7.  Der BMC ermöglicht Verwaltung von remote-Anmeldeinformationen.

    1.  Der BMC muss seine Administratorkennwort geändert wird, über den Befehl Benutzerkennwort festlegen unterstützen. Dieser Vorgang wird mit der in-Band-Kanal über den IPMI-Treiber ausgeführt.

8.  Die (Systemereignisprotokoll) können durch den BMC verwaltet werden

    1.  Die Auswahl Einträge können (erste Auswahl Eintrag-Befehl) gelesen werden

    2.  Das Systemereignisprotokoll kann (Clearsel-Befehl) gelöscht werden soll

Es folgt eine Liste der den IPMI-Befehle, die zum Verwalten von BMC Geräten verwendet werden:

-   Session öffnen

-   RAKP Nachrichten

-   Set-Sitzung Berechtigungsebene

-   Sitzung Informationen abrufen

-   Schließen der Sitzung

-   Geräte-Id abrufen

-   System-GUID abgerufen

-   Erste System Info-Parameter

-   Lesen von Daten FRU

-   Chassis-Steuerelement

-   Abrufen des Chassis-Status

-   Get-Channel-Info

-   Abrufen der Konfigurationsparameter für LAN

-   Festlegen der Konfigurationsparameter für LAN

-   Warm zurücksetzen

-   Abrufen des Auswahl-Eintrag

-   Auswahl Informationen abrufen

-   Reservieren Auswahl

-   Auswahl löschen

-   Auswahl Zeit abrufen

-   Erste Systemstartoptionen

-   Festlegen von Optionen für System Boot

-   Abrufen von Benutzernamen

-   Benutzerkennwort festlegen

**Erzwingung**

Dies ist eine optionale Gerät "If-implementierte" Anforderung. Dies ist eine Voraussetzung erforderlichen Gerät für Server zu Out-of-Band-verwaltbaren mit den IPMI Industriestandard werden. Diese Anforderung wird also tatsächlich bei der Freigabe von Windows Server 2016.

