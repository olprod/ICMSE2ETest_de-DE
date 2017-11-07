---
title: Device.Network.Switch.Manageability
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 611f7cb905510e8e6ae15a312f8c89d705aaef7a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Network.Switch.Manageability

 - [Device.Network.Switch.Manageability](#device.network.switch.manageability)
-->

<a name="device.network.switch.manageability"></a>
##Device.Network.Switch.Manageability

### <a name="devicenetworkswitchmanageabilitynetworkswitchprofile-if-implemented"></a>Device.Network.Switch.Manageability.NetworkSwitchProfile (sofern implementiert)

*Device.Network.Switch.Manageability.NetworkSwitchProfile*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die vorgeschlagenen DTMF-Netzwerk wechseln Profil definiert das CIM-Objektmodell und die zugehörigen Verhalten für die Verwaltung von einem Netzwerk-Switch (einschließlich der CIM-Klassen, Zuordnungen, Angaben, Methoden und Eigenschaften).  Es ist nicht erforderlich, dass ein Rechenzentrum Netzwerkswitch das vollständige vorgeschlagenen DMTF Netzwerk wechseln Profil, implementiert, da nur eine Teilmenge der Funktionalität erforderlich sind, diese Verwaltbarkeit Anforderung erfüllen.  Diese Teilmenge muss die folgenden Verwaltungsvorgänge über implementierte CIM Klassen Remote über WS-gar. enthalten Diese Anforderung ist eine Voraussetzung Wenn implementiert, und die Funktionalität, die erfüllt sein, wenn dies implementiert ist, lautet wie folgt:

-   Erhalten möchten, aktivieren und Deaktivieren von Features für Switch

-   Erhalten möchten Sie, aktivieren und Deaktivieren von Ports

-   Set-Port in Access oder Trunk-Modus

-   Get, Set-Port-Beschreibung

-   Abrufen einer Liste von VLANs für einen Trunk-Port

-   Rufen Sie das VLAN für eine Access-Port

-   Entfernen Sie ein VLAN zu/aus einer Trunk-Port hinzufügen /

-   Abrufen einer Liste von VLANs

-   Ein VLAN aktivieren/deaktivieren

-   Ein VLAN erstellen/löschen

-   VLAN-Namen ändern

-   Herunterfahren/Neustarten Switch

-   Erhalten möchten Sie, legen Sie Switch-Hostnamen

-   Abrufen der Firmware-Versionsinformationen

-   Erhalten möchten Sie, legen Sie Banner für die Anmeldung

### <a name="devicenetworkswitchmanageabilitynetworkswitchprofileview"></a>Device.Network.Switch.Manageability.NetworkSwitchProfileView

*Dies ist zwingend erforderlich, damit Zertifizierung, die Layer 3 fähige Netzwerkswitch benötigen, die Möglichkeit, die von der Windows PowerShell gewünschten Zustand Konfiguration (DSC) Mechanismus konfiguriert werden.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Gewünschten Zustand Konfiguration (DSC) ermöglicht das Bereitstellen und Verwalten von Konfigurationsdaten für Dienste und Verwalten von der Umgebung aus, in der diese Dienste ausgeführt werden. Weitere Informationen finden Sie unter <http://technet.microsoft.com/en-us/library/dn249912.aspx>.

Ein Datacenter Layer 3 Netzwerk Switch systemeigener OMI basierend-Anbieter implementiert eine bestimmte Gruppe von View-Klassen, die die DSC Erfahrung und Anforderungen zu definieren. Der Entwurf der Ansichtsklassen ermöglicht eine Abstraktion höherer Ebene aufgabenbasierte im Vergleich zu den vollständigen Netzwerk Switch CIM Schema. Der Entwurf der Ansichtsklassen würde auf dem Standard CIM von DMTF im Sinne dieser Publikation <http://www.dmtf.org/sites/default/files/standards/documents/DSP0004_3.0.0.pdf>basieren.

Diese deklarativen Weise Konfigurieren der Switches ist sichergestellt, dass mehrere Roundtrips für die Konfiguration sind nicht erforderlich, und bietet einen Hersteller unabhängig Schnittstelle an, die zu erzielen. Darüber hinaus wird auch gewährleistet, dass die Netzwerkswitches nicht von diesem Erstkonfiguration, wodurch verbessert die Zuverlässigkeit der Bereitstellung abweichen.

Der Ansatz mit CIM Ansichtsklassen erheblich vereinfacht das Schema für die Erstkonfiguration und ermöglicht die oben genannten Ziele der Konfiguration. Die Switch-Anbietern haben die Flexibilität, wählen Sie ihre eigene zugrunde liegenden Implementierung für den Vertrag des Anbieters DSC dargestellt durch die Klassen anzeigen erfüllen.

Alle Kategorien der Verwaltbarkeit Vorgänge würde wie folgt überprüft werden:

1.  Das Anforderung DSC Änderungsdokument, eine Datei Managed Object Format Datei (MOF) erfolgreich empfangen und Identitätsdaten durch den Netzwerkswitch. Dieses Dokument gibt den gewünschten Zustand, in dem der Netzwerk-Switch Übergang muss.

2.  Je nach den vorgesehenen Funktionsbereich der Netzwerk-Switch werden verschiedene Methoden zum Überprüfen des gewünschten Zustands der Netzwerk-Switch. Die verwandten Anforderungen Aufrufen diese einzeln.

Zusätzlich zu der Verbrauch DSC Dokumente in der oben genannten Arten unterstützt die Option auch aufzählen und Get-Funktionen auf Konfiguration Elemente, damit eine explizite auflisten oder Get-Operation für den Umstieg auf die Zustandsinformationen Konfigurationselemente zurückgeben aufgerufen werden kann.

Ein Netzwerkswitch Datacenter Layer 3 bietet diese Unterstützung systemintern ohne Hilfe eines externen Begleit-Anbieters Betrieb in einer separaten Gerät Anlage.
