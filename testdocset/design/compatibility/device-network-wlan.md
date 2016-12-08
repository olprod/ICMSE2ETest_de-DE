---
title: Device.Network.WLAN
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7859ae0ed6526bba95d7a832518dd1aae9943a4a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworkwlan"></a>Device.Network.WLAN

 - [Device.Network.WLAN](#device.network.wlan)
 - [Device.Network.WLAN.SupportConnectionToAP](#device.network.wlan.supportconnectiontoap)
 - [Device.Network.WLAN.SupportWakeFromLowPower](#device.network.wlan.supportwakefromlowpower)
 - [Device.Network.WLAN.SupportMACAddressRandomization](#device.network.wlan.supportmacaddressrandomization)
 - [Device.Network.WLAN.SupportHotspot2Dot0](#device.network.wlan.supporthotspot2dot0)
 - [Device.Network.WLAN.SupportDot11W](#device.network.wlan.supportdot11w )
 - [Device.Network.WLAN.SupportFIPS](#device.network.wlan.supportfips)
 - [Device.Network.WLAN.SupportWiFiDirect](#device.network.wlan.supportwifidirect)
 - [Device.Network.WLAN.SupportWiFiDirectServices](#device.network.wlan.supportwifidirectservices )
 - [Device.Network.WLAN.SupportWirelessDocking](#device.network.wlan.supportwirelessdocking)
 - [Device.Network.WLAN.SupportHostedNetwork](#device.network.wlan.supporthostednetwork)

<a name="device.network.wlan"></a>
## <a name="devicenetworkwlan"></a>Device.Network.WLAN

*Windows-10 WLAN-Treiber können eine der folgenden Treibermodelle implementieren:*

 - WDI Driver Model eingeführt in Windows 10 (unterstützt neue Features für Windows 10)

*OR*

 - Systemeigene Wi-Fi Driver Model (bietet keine Unterstützung für neue Features für Windows 10)

<a name="device.network.wlan.supportconnectiontoap"></a>
## <a name="devicenetworkwlansupportconnectiontoap"></a>Device.Network.WLAN.SupportConnectionToAP

### <a name="devicenetworkwlansupportconnectiontoapconnectiontoap-mandatory"></a>Device.Network.WLAN.SupportConnectionToAP.ConnectionToAP (erforderlich)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Geräte müssen Informationen für jede Kategorie der jeweiligen unterstützten Band melden. Darüber hinaus muss die folgenden Anforderungen Gerät entsprechen.

**Minimieren der CPU-Auslastung**

Das Gerät Wi-Fi sollte die folgenden Anforderungen für die Minimierung der CPU-Auslastung entsprechen.

-   Im Modus EXTSTA und D0 Zustand, müssen WLAN-Geräte nicht OS mehr als 1 Mal pro Packet Data unterbrechen (nicht D0 gemischt zusammengefügt nur Pakete. WLAN-Gerätesoftware D0 Paket zusammenfügenden sollten WLAN-Gerät mit der COALESCE D0 Packet-Spezifikation entsprechen für D0 Pakete gemischt zusammengefügt). Beachten Sie, dass wenn WLAN-Gerät SDIO Bus-Schnittstelle verwendet, generierten durch SDIO-Hostcontroller pro Datenpaket aus dieser Anforderung ausgenommen werden.  Nicht Daten Packet-bezogene Interrupts, falls erforderlich, darf nicht mehr als 3 Interrupts pro Sekunde durchschnittlich Wenn über einen Zeitraum von zwei Minuten gemessen.  Es empfiehlt sich, im aktiven Zustand (wenn Datenverkehr vorhanden ist), auch das Paket nicht mit Daten verknüpft Interrupts sollte innerhalb von 1 Millisekunde, der einen gültigen Packet-bezogene Interrupt ausgestellt werden.

-   In D0 Status müssen (falls vorhanden) alle Miniport bestimmte regelmäßige Wartung Zeitgeber mithilfe einer API verfügbar "Timer zusammenfügenden" mit mindestens 2 zweiten Punkt und 1 Sekunde Toleranz angegeben werden.  Diese Anforderung wird in ein langer Verbindungsstatus getestet wird, wenn keine in Verbindung Änderung.  Im Zustand D3 müssen alle solchen Zeitgeber abgebrochen werden.  Beachten Sie, dass diese Anforderung für Zeitgeber, z. B. in IEEE 802.11-Spezifikation definierten Verbindung Zeitgeber wie Association-Zeitgeber, roaming Zeitgeber usw. nicht zutrifft.  

-   Eine einzelne DPC (zurückgestellt prozedurale Call) Dauer MUSS 2 Millisekunden nicht überschreiten. Kumulierte DPC Dauer sollte über alle 10 Millisekunden Fenster kleiner als 4 Millisekunden sein.

In den Energiesparmodus Zustände Wenn das Gerät nicht Remoteaktivierung über Wireless-fähigen, ist muss WLAN-Gerät nicht die CPU unterbrechen. Wenn das Gerät Remoteaktivierung über Wireless-fähigen ist, muss WLAN-Gerät nicht die CPU außer auf Aktivierung Trigger angegeben durch NDIS für Remoteaktivierung über drahtlosen LAN abgebrochen. Alle nicht im Zusammenhang mit der Trigger reaktivieren Interrupts müssen abgebrochen werden.

**Unterstützen Sie mehrerer Geräteinstanzen**

Plug & Play kann mehrere Instanzen eines Geräts unterstützen. Mehrere Instanzen des Geräts können vorhanden und im selben System gleichzeitig fungieren. Für Communications Netzwerkgeräte MÜSSEN die Plug & Play-IDs und die Unterstützung von Ressourcen mehrere Netzwerk Kommunikationsgeräte, das System automatisch hinzugefügt werden soll möglich sein. Diese Anforderung impliziert, dass alle Ressourcen für Geräte festgelegt und über die standard-Schnittstellen bereitgestellt von der auf dem sich das Gerät befindet Bus gelesen werden MÜSSEN. Für PCI-Geräte ist diese Schnittstelle der PCI-Konfigurationsbereich. Darüber hinaus MÜSSEN die Parameter für Geräte in der Registrierung gespeichert werden.

**Einhaltung der folgenden Spezifikationen: NDIS 6.50, WDF/KMDF**

Netzwerk-Gerätetreibern müssen nur NDIS Network Driver Interface Specification () 6.50 oder Windows Treiber Foundation (WDF) Anrufe vornehmen. Alle Anrufe und Kernel-Modus-Komponenten sind nicht zulässig.

**Zuordnung Timing-Anforderung**

Auf WPA2-PSK-Netzwerken müssen WLAN-Geräte die Zuordnung in **300ms**Fertig stellen.  Gemessen, wie die Zeit zwischen den Ereignissen, wenn Probleme mit dem Betriebssystem eine OID "OID\_WDI\_AUFGABE\_VERBINDEN" und Miniport sendet ein "NDIS\_STATUS\_WDI\_ANGABE\_ASSOCIATION\_ERGEBNIS" weist darauf hin, an das Betriebssystem. 

**Roaming von Timing-Anforderung**

Für Geräte, *keine* Unterstützung für Fast-Roaming (Dies bedeutet, dass die Station weder senden/empfangen-Aktion Frames unterstützt noch utilitizes 802.11r Fast BSS Übergänge. Darüber hinaus AP-Side 802.11 k benachbarten Berichte und 802.11r ist nicht aktiviert in der Zugriffspunkt): Roaming Aktion muss innerhalb von **100 ms**ausführen. Diesmal wird gemessen starten, wenn das Betriebssystem den Objektbezeichner gibt\_WDI\_AUFGABE\_CONNECT- oder OID\_WDI\_AUFGABE\_ROAMING Befehl und endet, wenn die NDIS\_STATUS\_WDI\_ANGABE\_ZUORDNUNG\_ERGEBNIS Benachrichtigung wird vom Betriebssystem mit der AssociationStatus legen Sie auf WDI empfangen\_ASSOC\_STATUS\_ERFOLG.

Für Geräte, *Führen Sie* Unterstützung für Fast-Roaming (Dies bedeutet, dass die Station senden/empfangen-Aktion Frames unterstützt und 802.11r nutzt Fast BSS Übergänge. Darüber hinaus werden AP-Side 802.11 k-Neighbour-Berichten und 802.11r, in dem Zugriffspunkt aktiviert): in **50 ms**muss Roaming Aktion ausführen. Dieses Mal wird gemessen starten, wenn das Betriebssystem den Objektbezeichner gibt\_WDI\_AUFGABE\_CONNECT- oder OID\_WDI\_AUFGABE\_ROAMING Befehl und endet, wenn die NDIS\_STATUS\_WDI\_ANGABE\_ZUORDNUNG\_ERGEBNIS Benachrichtigung wird vom Betriebssystem mit der AssociationStatus auf WDI festgelegt empfangen\_ASSOC\_STATUS\_ERFOLG.

**Gerät Initialisierung Timing-Anforderung**

WLAN-Geräte müssen während des Starts folgende Anforderung erfüllen, Wiederaufnahme aus dem Ruhezustand und Aktionen aktivieren/deaktivieren.

Gerät muss innerhalb einer Sekunde die OpenAdapterHandler Routine ausführen. Wird die Zeit gemessen zwischen Wenn NDIS als Teil eines Plug & Play-Betrieb des Systems und OpenAdapterCompleteHandler OpenAdapterHandler-Funktion aufruft (NDIS\_STATUS\_ERFOLG) wird zurückgegeben. In OpenAdapterHandler der Treiber muss alle seine Gerät die Initialisierung abgeschlossen haben.

**Radio Status ändern Timing-Anforderung**

WLAN-Geräten müssen den Status des Senders innerhalb 2 Sekunden ändern können. Wird diese Dauer zwischen gemessen die Anforderung wird über OID gesendet\_WDI\_AUFGABE\_FESTGELEGT\_RADIO\_-STATUS und wann der Miniport NDIS gibt an\_STATUS\_WDI\_ANGABE\_RADIO\_STATUS zurück.

**Bevorzugter Kanal legt Scan**

Bevorzugte Kanäle Set: Wenn unterstützt und von der Domäne gesetzlich zulässig, der Miniporttreiber muss empfiehlt sich die folgende Kanäle beim Suchen nach verfügbaren Netzwerken oder zu Kandidat roaming Zugriffspunkt:

-   Mit 2,4 Ghz Kanäle: 1 bis 14

-   5GHz U NII niedrig Kanäle: 36, 40, 44, 48

-   5GHz U NII Mid Kanäle: 52, 56, 60,64

-   5GHz U NII weltweit Kanäle: 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140

-   U-NII oberen 5GHz-Kanäle: 149, 153, 157, 161,165

Der Treiber muss Support für diese melden und andere Kanäle es unterstützt über die in der WDI bereitgestellten ChannelList\_BAND\_INFO des OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**Scannen Aktion-Anforderung**

WLAN-Gerät muss bei Erhalt des Überprüfung starten einer "OID\_WDI\_AUFGABE\_SCAN"von Betriebssystem und Antwort zurück mit Angabe"NDIS\_STATUS\_WDI\_weist darauf HIN\_SCAN\_VOLLSTÄNDIG" für das Betriebssystem, sobald sie die Überprüfung abgeschlossen ist. Im Fall eines WAN-aktive Scannen wird erwartet, dass Miniport senden, dass der aktive Platzhalter für den Scan Ziele und der Netzwerk-Prüfpunkte. Im Fall eines WAN-passive Überprüfung wird Miniport keine Tests an die Netzwerkkanäle senden erwartet.

Ausführen eines Scans sollten diese Prioritätsreihenfolge befolgt werden:

1.  NLO Hinweis Kanäle

2.  Bevorzugte Kommunikationskanäle

3.  Alle verbleibenden Kanäle

Die unten aufgeführten Anzeigedauer werden aus den Zeitstempel gemessen werden, wenn das Gerät OID empfängt "OID\_WDI\_AUFGABE\_SCAN" vom Betriebssystem auf den Zeitstempel, wenn die jeweilige Angabe für das Betriebssystem durch den Miniport bereitgestellt wird.

-   Wenn die Hinweise auf das Netzwerk Liste-Offloading verfügbar sind, sollte das Gerät nutzen die Netzwerk-Liste-Offloading Hinweise zur Optimierung der Scan Verhalten und zurückgeben "NDIS\_STATUS\_WDI\_ANGABE\_NLO\_DISCOVERY" weist darauf hin, wenn ein passendes Profil in der folgenden Anzeigedauer gefunden wird:

    <!-- -->

    -   Scannen ein Netzwerk, in dem aktiven Scan - 20 ms-Kanal zulässig ist

    -   Scannen ein Netzwerk, in dem nur die passive Überprüfung - 120ms-Kanal zulässig ist

    <!-- -->

-   Wenn keine Übereinstimmung mit Hinweisen Abladung von Netzwerk-Liste vorhanden ist, sollten WLAN-Gerät als Nächstes die bevorzugte Kanäle in der obigen Liste scannen.  Zum Überprüfen der Kanäle in der Liste Bevorzugte Channel, sollte WLAN-Gerät nicht mehr als 3,5 Sekunden dauern (Zeit umfasst die Suche nach aktiven und passiven Kanäle). Die neu erstellte Liste des umgebenden BSS Einträge sollte auf die nächste BSS Listenabfrage vom Betriebssystem zurückgegeben werden.

-   Wenn keine Übereinstimmung gefunden oben 2 Fällen vorhanden ist, sollte WLAN-Gerät weiter alle verbleibenden Kanäle überprüft. WLAN-Gerät sollte nicht mehr als 4 s für den gesamten Scanvorgang verwenden. 

**Scan Verhalten bei der Wiederaufnahme aus dem Standbymodus/Bildschirm deaktiviert**

Bei der Wiederaufnahme aus dem Standbymodus/Bildschirm deaktiviert wird erwartet, dass das WLAN-Gerät an den gleichen Zugriffspunkt erneut, die er mit verbunden wurde, bevor er deaktiviert, sofern es vorhanden ist. WLAN-Geräte müssen die folgenden Anzeigedauer für die Erkennung der Präsenz erfüllen:

-   Wiederherstellen der Verbindung mit einem Kanal aktiv waren Scannen zulässig ist - 50 ms

-   Wiederherstellen der Verbindung mit einem Kanal wurden nur die Passive Überprüfung ist zulässig - 120ms

Wenn das zuletzt verbundene Netzwerk nicht gefunden wird, muss der WLAN-Gerät für Netzwerke in der folgenden Prioritätsreihenfolge überprüft.

-   NLO Hinweis Kanäle

-   Bevorzugte Kommunikationskanäle

-   Alle verbleibenden Kanäle

WLAN-Gerät muss oben im Abschnitt Allgemein Scan definiert Timing Nebenbedingungen entsprechen.  Die Anzeigedauer werden von den Zeitstempel gemessen werden, wenn das Gerät als D0 Status meldet (OID\_WDI\_FESTGELEGT\_POWER\_ZUSTAND Abschluss) mit dem Zeitstempel, wenn die jeweilige Angabe für das Betriebssystem nach dem Miniport bereitgestellt wird.

**Scannen Sie nicht Broadcast-Netzwerke**

WLAN-Gerät muss die Suchen nach und das Vorhandensein von nicht-Broadcast melden können (d. h., ausgeblendet) Netzwerke.

**Unterstützung der koordinierten Überprüfung (If-implementierte) (nur WDI-Treiber)**

VOIP-Vorgängen muss können Netzwerkressourcen priorisieren, wobei weiterhin für Mobilität Datenqualität verwaltet wird. In den drahtlosen-Stapel haben wir das Konzept der Streaming Media-Modus als solche eingeführt. Diese Funktion ruft insbesondere die Überprüfung der Auswirkungen Taste / Verhalten im Streaming Media-Modus. Finden Sie in der Spezifikation WDI Weitere Informationen.

**Unterstützen Sie Roh-Aktion Rahmen (If-implementierte) (nur WDI-Treiber)**

Roh-Aktion Frames sind erforderlich für die Übertragung von ANQP Antwortzeiten Frames, 802.11 k-Neighbour-Bericht/Anforderung Rahmen und 802.11v BSS Übergang Management Bericht/Anforderung Frames. Das Gerät muss roh-Aktion Frames im WDI unterstützt melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN. Finden Sie in der Spezifikation WDI Implementierungsdetails. 802.11 k-Neighbour-Berichten und 802.11vBSS Übergang Management Frames zum Verbessern der Leistung von servergespeicherten im Betriebssystem verwendet werden. Durch die Nutzung von 802.11k benachbarten erstellenund 802.11v BSS Übergang Management Frames, die das Betriebssystem verfügt über eine verbesserte Grundlegendes zur Umgebung und ermöglicht eine höhere Leistung roaming, dies führt zu weniger Probleme für den Endbenutzer, wenn Sie sich bei einem Aufruf Sprache/Video.

**Unterstützung 802.11r Fast BSS Übergang (If-implementierte) (nur WDI Treiber)**

802.11r zulassen fast BSS Übergänge für höhere Geschwindigkeit Austausch der Sitzungsschlüssel, führende für eine bessere Leistung Roamingbenutzer zu erhöhen. Der Treiber muss unterstützen einen neuen Zuordnung für Fast BSS Zuordnungen und werden die entsprechenden Angaben an das Betriebssystem während der Exchange-Prozess Association-Taste zu senden. Finden Sie in der Spezifikation WDI aus Weitere Informationen.

**Geringe Latenz Leistung**

WLAN-Geräte sollte geringer Latenz Applications/Szenarien wie etwa Wi-Fi-Anzeige/Lync/Skype unterstützen können. Hierzu muss WLAN-Geräte die folgenden Funktionen:

-   WMM sollten unterstützt werden, auf alle Ports virtualisierten Ports – ExtSTA, einschließlich Wi-Fi Direct-Rolle (Gruppenbesitzer) und Wi-Fi Direct Rolle Anschluss (Client).

-   WMM Wi-Fi Direct Rolle Port (Gruppenbesitzer) unterstützt werden soll und Wi-Fi Direct Role-Port (Client), auch wenn der Zugriffspunkt über Port ExSTA verbunden unterstützt keine WMM.

-   Die NIC sollte Priorisierung über zwei Ports (ExtSTA & eine Wi-Fi Direct Rolle Port) gleichzeitig unterstützen.

-   Geräte sollten in der Lage, basierend auf 802.11e Datenverkehr zu priorisieren Access Kategorie (AC) markieren.

-   Wenn die NIC in einzelnen Kanal mit Parallelität virtualisiert ist, sollte es übertragen Datenverkehr über verschiedene virtuelle Ports basierend auf WMM & Streaming Media-Angabe priorisieren sein.

-   Wenn die NIC über verschiedene Kanäle mit Parallelität virtualisiert ist, sollte er Datenverkehr übertragen über verschiedene virtuelle Ports basierend auf WMM und Streaming Media-Angabe priorisieren werden und Empfangen von Datenverkehr wird über das gleichzeitige Kanäle bearbeitet.

Wenn WMM Priorisierung verwendet wird, mit AC\_VI oder AC\_VO (Sprache/Video) WLAN-Gerät muss die folgenden Latenz und Paket Verlust Anforderungen erfüllen.

<html>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>ExSTA</th>
                <th>Wi-Fi Direct Rolle Port</th>
                <th>Max. Eine Möglichkeit Wartezeit in UDP für AC_VI/AC_VO-Datenverkehr</th>
                <th>Paketverlust für AC_VI/AC_VO-Datenverkehr</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Nur ExSTA</td>
                <td>AC_VI/AC_VO</td>
                <td>NV</td>
                <td>30ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr class="odd">
                <td>ExSTA + Wi-Fi direkt in Single-Channel-Parallelität</td>
                <td>AC_VI/AC_VO</td>
                <td></td>
                <td>30ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>30ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>AC_VI/AC_VO</td>
                <td>30ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr class="odd">
                <td>ExSTA + Wi-Fi direkte Multi-Channel Gleichzeitigkeit</td>
                <td>AC_VI/AC_VO</td>
                <td></td>
                <td>40ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>40ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>AC_VI/AC_VO</td>
                <td>50 ms</td>
                <td>0,5 %, nicht mehr, 3 Consequetive-Pakete</td>
            </tr>
        </tbody>
    </table>
</html>

**Minimale Durchsatzleistung**

**Durchsatz bei gleichzeitiger Vorgang:** 802.11-Geräte müssen haben keinen mehr als 20 % aggregierte Durchsatz Beeinträchtigung Datenfluss zwischen 3-Ports (mit und ohne Multi-Channel Band Vorgang) aufgeteilt wird, nämlich – ExtSTA, Wi-Fi direkte Rolle Port (GO) und Wi-Fi Direct Rolle Port (Client) im Vergleich mit aggregierte Durchsatz, wenn nur eine Wi-Fi-Port verbunden ist.

**Durchsatz:**

Diese Anforderung an den Durchsatz ist einzeln für alle Arten von Ports (ExtSTA, Wi-Fi direkte Rolle Port (GO) und Wi-Fi Direct Role-Port (Client)).

Gerät muss die unterstützen die folgenden Durchsatz Zahlen über eine TCP-Verbindung für eine bestimmte Kombination von Phy-Typ, Anzahl der Datenströme und Channel Breite. Auf der Anwendungsebene mit NTTTCP Perf Messung Tool Windows Hardware Zertifizierung Kit integriert wird der Durchsatz gemessen.

-   Wenn WLAN-Gerät 802.11ac unterstützt Phy-Typ (Beachten Sie, 802.11ac Support Phy-Typ ist optional für WLAN-Geräte. 802.11ac Geräte für 802. 11n werden ebenfalls getestet Vorgänge)

    -   802.11ac werden auf 5 Ghz Band nur Kombinationen getestet.

    -   Beide senden und Empfangen von Seite Durchsatz wird getestet. Gerät wird erwartet, dass dieselbe Durchsatz Anzahl (siehe unten) für eine bestimmte Kombination Übertragung und Empfang aufseiten erfüllen.

Max unterstützten räumliche Stream durch die NIC wird getestet werden soll. Z. B., wenn die NIC 3 räumliche Datenströme unterstützt, Kombinationen mit räumliche Stream 3 getestet.

<html>
    <table>
        <thead>
            <tr class="header">
                <th><em>DDE-Kanalbreite</em></th>
                <th colspan="2"><em>20 Mhz</em></th>
                <th colspan="2"><em>40 Mhz</em></th>
                <th colspan="2"><em>80 Mhz</em></th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th># Räumliche Datenströme </th>
                <td>Max Phy Rate (100 %)</td>
                <td>Durchsatz von Windows-Zertifizierungsstelle erwartet</td>
                <td>Max Phy Rate (100 %)</td>
                <td>Durchsatz von Windows-Zertifizierungsstelle erwartet</td>
                <td>Max Phy Rate (100 %)</td>
                <td>Durchsatz von Windows-Zertifizierungsstelle erwartet</td>
            </tr>
            <tr class="even">
                <th>1 Stream-Objekt</th>
                <td>86</td>
                <td>18</td>
                <td>200</td>
                <td>42</td>
                <td>433</td>
                <td>90</td>
            </tr>
            <tr class="odd">
                <th>2 Stream-Objekt</th>
                <td>173</td>
                <td>38</td>
                <td>400</td>
                <td>88</td>
                <td>866</td>
                <td>191</td>
            </tr>
            <tr class="even">
                <th>Stream 3 oder höher\*</th>
                <td>258</td>
                <td>47</td>
                <td>600</td>
                <td>110</td>
                <td>1300</td>
                <td>237</td>
            </tr>
        </tbody>
    </table>
    <p><em>\*Alle kumulativ sind in Mbit/s.</em></p>
    <p><em>\*Tastenkombinationen für die Geräte SDIO und USB 2.0-Bus-Typ nicht erforderlich. Diese Geräte mit Unterstützung für mehr als 2 Streams muss für 2 Streams aufgeführten Werte zu erreichen. Beachten Sie, dass 3.0 USB-Geräten nicht ausgeschlossen werden.</em></p>
    <ul>
        <li>
            <p>802. 11n WLAN-Geräte</p>
            <ul>
                <li><p>802. 11n Kombinationen werden über mit 2,4 Ghz und 5 Ghz Bereichen getestet werden, wenn beide Bereiche auf dem Gerät unterstützt werden.</p></li>
                <li><p>Beide senden und Empfangen von Seite Durchsatz wird getestet. Gerät wird erwartet, dass dieselbe Durchsatz Anzahl (siehe unten) für eine bestimmte Kombination Übertragung und Empfang aufseiten erfüllen.</p></li>
                <li><p>Maximale unterstützte räumliche Datenströme durch die NIC werden getestet werden soll. Z. B., wenn die NIC 3 räumliche Datenströme unterstützt, Kombinationen mit räumliche Strömen 3 getestet.</p></li>
            </ul>
        </li>
    </ul>
    <table>
        <thead>
            <tr class="header">
                <th>DDE-Kanalbreite</th>
                <th colspan="2">20 Mhz</th>
                <th colspan="2">40 Mhz</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th># Räumliche Datenströme</th>
                <td>Max Phy Rate (100 %)</td>
                <td>Durchsatz von Windows-Zertifizierungsstelle erwartet</td>
                <td>Max Phy Rate (100 %)</td>
                <td>Durchsatz von Windows-Zertifizierungsstelle erwartet</td>
            </tr>
            <tr class="even">
                <th>1 Stream-Objekt</th>
                <td>72</td>
                <td>15</td>
                <td>150</td>
                <td>31</td>
            </tr>
            <tr class="odd">
                <th>2 Stream-Objekt</th>
                <td>144</td>
                <td>32</td>
                <td>300</td>
                <td>66</td>
            </tr>
            <tr class="even">
                <th>Stream 3 oder höher\*</th>
                <td>216</td>
                <td>40</td>
                <td>450</td>
                <td>82</td>
            </tr>
        </tbody>
    </table>
    <p><em>\*In Mbit/s sind alle kumulativ.</em></p>
    <p><em>\*Tastenkombinationen für die Geräte SDIO Bus-Typ nicht erforderlich. SDIO Geräte mit Unterstützung für mehr als 2 Datenströme muss für 2 Streams aufgeführten Werte zu erreichen.</em></p>
</html>

**Wi-Fi Power-Modus speichern**

Wi-Fi-Treiber ist erforderlich, wenn Erkennung und der entsprechenden Wi-Fi Power speichern Modus (PSM) zwischen dem Gerät und dem Zugriffspunkt Wi-Fi-Aushandlung ausführen und als AutoPowerSaveMode in der WDI\_STATION\_ATTRIBUTE.  Wenn sich der Treiber meldet, dass es PSM Erkennung unterstützt, delegiert WLAN-Dienst standardmäßig die Entscheidung PSM an den Treiber.

Wenn der Treiber die Funktion AUTOMATISCHE PSM unterstützt der Wi-Fi-Dienst wird nicht mehr zu den Miniport Beacons erhalten Filters broadcast Management festgelegt und stattdessen eine OID So schalten Sie automatische PSM im Treiber legt fest.  Im Auto-PSM, sollte der Treiber immer aushandeln PSM-Modus, wenn es erkennt, dass der Zugriffspunkt unterstützt und die Verwendung von PSM zwischen dem Gerät und dem Zugriffspunkt Wi-Fi, um eine optimale Konnektivität sicherzustellen, dass während der Verwendung des geringsten Power verwalten.

**Verlust der Verbindung**

Alle WLAN-Geräte müssen erkennen, und geben Sie an, die zum Verlust von der verbundenen Zugriffspunkt (keine Beacons) in 20 Signal Intervallen.

**Zulassen der Elemente mit Zuordnung Frames (Anforderung und Antwort) hinzugefügt werden**

Alle 802.11-Geräte müssen zulassen Informationselemente Frames Zuordnung hinzugefügt werden Anforderungen und Antworten. Dazu gehören Hinzufügen von Elementen des aktuell angegebenen Informationen, wie Wi-Fi Protected Setup sowie anderer Anbieter Informationselemente erweitert.

**Unterstützung für 32 Multicastadressen Filterung**

WLAN-Hardware muss mindestens 32 Multicastadressen auf jedem Port unterstützen. Station und Wi-Fi-Direct Ports müssen separat Filtern von 32 Multicastadressen unterstützen.

**Unterstützung von separaten Signal und Informationselemente Prüfpunkt**

Alle 802.11-Geräte müssen separat Wi-Fi Protected Setup Datenreihen an, die in Signalframes und Test-Response-Rahmen empfangen werden. Wenn das Gerät aus einer bestimmten BSSID sowohl eine Signal und einem Frame Prüfpunkt-Antwort erhalten hat, müssen sie zwei Instanzen von Internet Explorer, angeben, in dem eine Instanz ist, die am häufigsten kurzem WPS IE aus der Signal und eine Instanz ist die am häufigsten kürzlich WPS IE aus der Prüfpunkt Antwort erhalten.

**Übertragen von Pakete auf eine beliebige Grenze**

Puffer Ausrichtung bezieht sich auf ein Puffer gibt an, ob eine ungerade-Byte, Word, Double Word oder andere Grenze beginnt. Geräte müssen mit einem der Pakete Bruchstücke beginnend am eine ungerade-Byte-Grenze-Pakete übermittelt werden können. Aus Gründen der Systemleistung müssen in zusammenhängenden Puffer an einem Double Wortanfang Pakete empfangen werden.

**TCP-Prüfsumme Verschiebung (If-implementierte) (nur WDI-Treiber)**

TCP/IP-Protokoll soll zuverlässige Daten Übertragungsmechanismus bereit. Dies von Anrufen für den TCP-Stapel zum Implementieren verschiedener Schutzmechanismen zum Erkennen und beheben diese Fehler. Eine solche Mechanismus ist das Konzept der "Prüfsumme" verwenden, um die Zuverlässigkeit sicherzustellen. Windows führen wir die Prüfsumme Berechnungen in das Betriebssystem anfordern Wiederholungsversuche der Pakete und verwalten Sie die Pakete in den HOST. Das WLAN-Gerät muss melden, verlagert unterstützt und in der Lage OS vorgeschriebenen Weise abnimmt. Gerät muss erkennen, wenn die Verschiebung Leistungsprobleme verursacht und möglicherweise die Offloading deaktivieren. Verlagert sollte über Station Konnektivität und direkte Wi-Fi Verwendungsszenarien funktioniert.

**Konnektivität Typen**

Alle WLAN-Geräte müssen eine Verbindung herstellen, verwenden die folgenden Verbindungstypen Wi-Fi sein. Deklarieren Sie alle WLAN-Geräte Unterstützung für diese über WDI\_Algorithmus\_PAARE gemeldet OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN

Unterstützung der Authentifizierung und Verschlüsselung in Infrastrukturmodus erforderlich:

| Authnetication  | Verschlüsselung     |
|-----------------|------------|
| Öffnen            | Keine       |
| Öffnen            | WEP - 40 bit  |
| Öffnen            | WEP - 104 bit |
| Öffnen            | WEP        |
| WPA-Unternehmen  | TKIP       |
| WPA-Unternehmen  | CCMP       |
| WPA-Persönlich    | TKIP       |
| WPA-Persönlich    | CCMP       |
| WPA2-Unternehmen | TKIP       |
| WPA2-Unternehmen | CCMP       |
| WPA2-Persönlich   | TKIP       |
| WPA2-Persönlich   | CCMP       |

\[Systemeigene Wi-Fi-Treiber nur\] (If-implementierte) Authentifizierung und Verschlüsselung Support in Ad-hoc-(IBSS) Modus erforderlich:

| Authnetication | Verschlüsselung     |
|----------------|------------|
| Öffnen           | Keine       |
| Öffnen           | WEP - 40 bit  |
| Öffnen           | WEP - 104 bit |
| Öffnen           | WEP        |
| WPA2-Persönlich  | CCMP       |

**Unterstützung für den Ruhezustand und fortsetzen**

Wenn das Gerät unterstützt das Ruhezustand und das fortsetzen, das Gerät nicht werden, die aus dem Bus als Teil seiner Firmware Initial (Startzeit) Prozess heruntergeladen werden soll oder beim Wechsel zu Ruhezustand Zustand.

**Unterstützung Radio Management (Radio On/Off)**

Gerät muss die Verwaltung des Senders Anfragen aus dem Betriebssystem über die WDI unterstützen\_AUFGABE\_FESTLEGEN\_RADIO\_ZUSTAND Befehl. Finden Sie in der Spezifikation WDI Weitere Informationen.

**Unterstützung von Wi-Fi Protected Setup (WPS)**

Geräte müssen Wi-Fi Protected Setup unterstützen. OS WDI Problem wird\_FESTGELEGT\_P2P\_WPS\_AKTIVIERT Befehl die LE an, wenn WPS festgelegt ist. Finden Sie in der Spezifikation WDI Weitere Informationen.

**Paketfilter (If-implementierte) unterstützen**

Paketfilter ermöglichen das Betriebssystem um verschiedene Typen von Paketen beim Erhalt zu filtern. Das Betriebssystem verwendet die WDI\_TLV\_PAKET\_FILTER\_TLV PARAMETER, um anzugeben, welche Art von Paket zum Filtern von. Finden Sie in der Spezifikation WDI Weitere Informationen.

**Abrufen von WFA Zertifizierungen (If-implementierte)**

Es wird dringend empfohlen, Geräte die folgenden WFA Zertifizierungen abzurufen:

-   802. 11n
-   WMM
-   WPA2Protected Management Frames (PMF)

**Implementieren der 802. 11a (If-implementierte)**

Gerät muss 802. 11a melden PHY-Typ 4 (WDI\_PHY\_TYP\_OFDM) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**Implementieren von 802. 11 b (erforderlich)**

Gerät muss 802. 11 b melden PHY-Typ 2 (WDI\_PHY\_TYP\_HRDSS) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**Implementieren von 802.11g (If-implementierte)**

Gerät muss 802. 11 g PHY-Typ 5 melden (WDI\_PHY\_TYP\_ERP) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**802. 11n implementieren (If-implementierte)**

Für eine optimale Leistung der WLAN-empfohlen.

Gerät muss 802. 11n melden PHY-Typ 7 (WDI\_PHY\_TYP\_HT) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**Implementieren der 802.11ac (If-implementierte)**

Gerät muss 802.11ac melden 8 PHY-Typ (WDI\_PHY\_TYP\_VHT) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

**Unterstützung von Auflegen Erkennung und Recovery (If-implementierte) (nur WDI-Treiber)**

Wi-Fi Gerätefirmware ist bekannt, dass hängen und / oder in einem unterbrochene Zustand erhalten möchten. Wenn in diesem Fall würde der untere Rand Treiber entweder Absturz verursacht eine 9F (blauer Bildschirm) oder das Wi-Fi-Subsystem ruft in einen Zustand erfordert einen Neustart des Systems für das Gerät erneut funktionsfähig sein. In beiden Fällen wird der Benutzer in ihrer Konnektivität einen negativen Umgang mit konfrontiert, und ihre allgemeine Systemverwendung unterbrochen ist. Als Bestandteil des WDI wir einen Mechanismus, um zu erkennen, wann die Firmware in dieser Zustände ruft entworfen haben und das Gerät nahtlos wiederherstellen. Dadurch wird sichergestellt, dass der Benutzer einen Geschäftsablauf im Dienst angezeigt, indem sichergestellt wird, dass Gerätestapel Wi-Fi wiederhergestellt und Verbindung mit dem Netzwerk ohne das System benötigen einen Neustart fortgesetzt. Geräte müssen Unterstützung bei der Erkennung hängen und Wiederherstellung in WDI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN. Finden Sie in der Spezifikation WDI Implementierungsdetails.

Anforderung – Hardware / Firmware

System ACPI Firmware: Bereitstellen des Systems ACPI Methoden zum PDLR auf das Gerät an einen Bus oder auf Device-Ebene.

System-Hardware: ist für eine PDLR (vollständige Gerät Ebene Reset) zulässig. Alle Systeme müssen PDLR unterstützen.

System: Im System wird die Unterstützung für die Unterstützung von PDLR angezeigt.

Gerät: Der untere Rand Treiber speichert mit 25 ms und Größe von 250 Kb sammeln werden können

System: Das System müssen innerhalb von 10 Sekunden zurücksetzen.

<a name="device.network.wlan.supportwakefromlowpower"></a>
## <a name="devicenetworkwlansupportwakefromlowpower"></a>Device.Network.WLAN.SupportWakeFromLowPower

### <a name="devicenetworkwlansupportwakefromlowpowerwakefromlowpower-if-implemented"></a>Device.Network.WLAN.SupportWakeFromLowPower.WakeFromLowPower (If-implementierte)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

Implementieren der Aktivierung für WLAN

**Beschreibung:**

WLAN-Geräte, die WoWLAN (zur Aktivierung auf drahtlosen LAN) implementieren müssen alle Features im Zusammenhang mit der Funktion WoWLAN unterstützen. Implementierung der Teilmenge der folgenden Features werden nicht für die Zertifizierung berücksichtigt. WLAN-Geräte sollten folgendermaßen vorgehen:

-   Muss die bestimmten Remoteaktivierung über Funktion drahtlosen LAN (WoWLAN) angeben, die unterstützt wird.

-   Muss mindestens 22 WoWLAN Bitmap Reaktivierung-Muster von 128 Byte unterstützen.

-   GTK (WPA/WPA2) durchführen und muss IGTK aktualisieren (WPA2) in die Dx Zustand.

-   Aktivierung müssen auf GTK und IGTK Handshake Fehler unterstützt werden.

-   Muss unterstützen Aktivierung bei 802.1 X EAP-Request/Identity-Paket empfangen wird.

-   Muss die Aktivierung bei vier unterstützen-Wege-Handshake fordert empfangen wird.

-   Aktivierung müssen auf Zuordnung mit aktuellen AP verloren unterstützt werden.

-   Aktivierung müssen unterstützt werden, wenn ein Netzwerk NLO (Network-Liste Offloading) Hinweise entspricht.

-   Aktivierung Paket Angabe müssen unterstützt werden. NIC sollte das Paket, wodurch die Aktivierung auf Hardware cache und nach oben weiterleiten, wenn das Betriebssystem für empfangen bereit ist.

-   ARP und NS verlagert um linkerkennungs-lokales Netzwerk sicherzustellen muss unterstützt werden. WLAN-Gerät muss möglicherweise Reaktion auf Anfragen ARP und NS ohne Unterbrechung der CPU, wenn das Gerät in den Energiesparmodus (D3) ist. Geräten müssen mindestens 1 ARP-Offloading und mindestens 2 NS verlagert (mit bis zu 2 IPv6-Zieladressen jedes NS-Offloading) unterstützen.

Netzwerk-Liste Offloading

**Beschreibung:**

WLAN-Geräte sollte 10 ausgelagerten BSSID Profile unterstützen. Wi-Fi-Profile, die gekennzeichnet sind zum automatischen Verbinden, wird durch das Betriebssystem auf den Gerätetreiber übergeben werden.  Das Gerät sollte die Netzwerk-Offloading Liste als Hinweis verwenden, Scan Verhalten zu optimieren und zurückgeben "NDIS\_STATUS\_WDI\_ANGABE\_NLO\_DISCOVERY" weist darauf hin, wenn ein passendes Profil gefunden wird.

<a name="device.network.wlan.supportmacaddressrandomization"></a>
## <a name="devicenetworkwlansupportmacaddressrandomization"></a>Device.Network.WLAN.SupportMACAddressRandomization

### <a name="devicenetworkwlansupportmacaddressrandomizationmacaddressrandomization-if-implemented-wdi-drivers-only"></a>Device.Network.WLAN.SupportMACAddressRandomization.MACAddressRandomization (If-implementierte) **(nur WDI-Treiber)**

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Die Wi-Fi-MAC-Adresse wird derzeit verwendet, zur Überwachung von Benutzern, wenn diese über öffentliche Leerzeichen aus hot vor Ort zu hot-Spot- und sogar innerhalb einer Abteilung Store oder eine Mall übergeben. Durch die MAC-Adresse zufällige, können nicht ohne ihre Zustimmung Windows Phones Benutzer nachverfolgt werden. Um dieses Feature zu unterstützen, muss das Gerät an das Betriebssystem melden, MAC-Adresse zufällige über WDI unterstützt\_ABRUFEN\_ADAPTER\_FUNKTIONEN. Finden Sie in der Spezifikation WDI Implementierungsdetails Feature.

<a name="device.network.wlan.supporthotspot2dot0"></a>
## <a name="devicenetworkwlansupporthotspot2dot0"></a>Device.Network.WLAN.SupportHotspot2Dot0

### <a name="devicenetworkwlansupporthotspot2dot0hotspot2dot0-if-implemented-wdi-drivers-only"></a>Device.Network.WLAN.SupportHotspot2Dot0.Hotspot2Dot0 (wenn implementiert) **(nur WDI-Treiber)**

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Gerät muss gemeldet werden, dass es in WDI ActionFrameSupport unterstützt\_TLV\_SCHNITTSTELLE\_FUNKTIONEN und Optinally meldet, dass es in WDI ConnectToSSIDsBelongingToHESSID unterstützt\_STATION\_ATTRIBUTE. Finden Sie in der Spezifikation WDI Implementierungsdetails.

<a name="device.network.wlan.supportdot11w "></a>
## <a name="devicenetworkwlansupportdot11w"></a>Device.Network.WLAN.SupportDot11W 

### <a name="devicenetworkwlansupportdot11wdot11w-if-implemented"></a>Device.Network.WLAN.SupportDot11W.Dot11W (If-implementierte)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Gerät muss die Unterstützung für 802.11w melden geschützte Management Frames im WDI\_STATION\_ATTRIBUTE. IEEE 802.11w ist eine Ergänzung zu IEEE 802.11-Suite Standards zur Verbesserung der Sicherheit von Management Frames. Finden Sie in der Spezifikation WDI Implementierungsdetails.

<a name="device.network.wlan.supportfips"></a>
## <a name="devicenetworkwlansupportfips"></a>Device.Network.WLAN.SupportFIPS

### <a name="devicenetworkwlansupportfipsfips-if-implemented"></a>Device.Network.WLAN.SupportFIPS.FIPS (If-implementierte)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Unterstützung für FIPS in WDI melden\_STATION\_ATTRIBUTE. Finden Sie in der Spezifikation WDI Implementierungsdetails. Die FIPS (Federal Information Processing Standards) ist eine USA Behörden-Anforderung für eine Verwendung auf Kommunikation und Computersystemen.

Ihr WLAN-Gerät muss eine der beiden folgenden Lösungen für FIPS-Unterstützung unterstützen:

1.  Hardware-basierte Lösung: Sie können zur Unterstützung von FIPS direkt über das Gerät auswählen. Sie können dazu DOT11 deklarieren\_EXTSTA\_ATTRIBUTE\_abgesicherten MODUS\_ZERTIFIZIERT (für NWIFI-Treiber) und WDI\_STATION\_ATTRIBUTE – Host FIPS-Modus (für implementiert WDI Treiber) in der Treiber. Wenn Sie Hardware mit Unterstützung für FIPS deklarieren können Sie den Hersteller des Geräts verantwortlich für die Einhaltung der FIPS-Standard. Windows kann nicht und Einhaltung der FIPS-Standard in diesem Modus nicht testen.

2.  Software-basierte Lösung: Windows implementiert eine-basierte softwarelösung, die die FIPS-Standard entspricht. DOT11 deklarieren Sie dazu\_EXTSTA\_ATTRIBUTE\_abgesicherten MODUS\_OID\_UNTERSTÜTZTE und Implementieren von OID\_DOT11\_SICHERE\_MODUS\_AKTIVIERT oder OID\_DOT11\_SICHERE\_MODUS\_HT\_AKTIVIERT in der Treiber.

<a name="device.network.wlan.supportwifidirect"></a>
## <a name="devicenetworkwlansupportwifidirect"></a>Device.Network.WLAN.SupportWiFiDirect

### <a name="devicenetworkwlansupportwifidirectwifidirect-if-implemented"></a>Device.Network.WLAN.SupportWiFiDirect.WiFiDirect (If-implementierte)

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

#### <a name="support-wi-fi-direct-base-functionality"></a>Direkte Basisfunktionen Wi-Fi-Unterstützung

**Beschreibung**

Wenn implementiert, die Unterstützung für Wi-Fi direkt über der Wi-Fi-Treiber Miracast, öffentlichen APIs für Wi-Fi direkt zu ermöglichen, eine Kopplung mit & vom PC, annehmen und Herstellen einer Verbindung mit anderen direkte Wi-Fi-Gerät für UNTERWEGS & der Client-Rolle zu aktivieren. Hierzu zählen außerdem Unterstützung für gleichzeitige Vorgang über direkte Wi-Fi & Station.

**Details**  

Gerät muss die relevanten-Funktionen in der WIFI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN gemäß der Spezifikation WDI

-   WIFI\_VIRTUALISIERUNG\_ATTRIBUTE
-   WIFI\_P2P\_ATTRIBUTE
-   WIFI\_BAND\_INFO
-   WIFI\_PHY\_INFO

Wenn diese Anforderungen wird unterstützt, muss das Gerät folgende Aktion ausführen, wie in der Spezifikation WDI definiert sein

-   Suchen Sie nach direkte Wi-Fi-Geräte & Gehe ZU

-   Als direkte Wi-Fi-Gerät & GO sichtbar sein

-   Direkte Wi-Fi-Geräte & GO Paarung

-   Akzeptieren Sie eingehender eine Kopplung von direkten Wi-Fi-Geräte & Gehe ZU

-   Verbinden Sie mit einer direkten Wi-Fi-Client oder Gehe ZU

-   Akzeptieren Sie, dass eingehende Verbindungen von Wi-Fi-Client oder auf eine direkte

-   Unterstützung für Extensible Datenreihen in während Paarung & (Zuordnung erneut)

-   Unterstützung für die Bereitstellung der Sätze Übertragungsqualität & Durchsatz für die direkte Wi-Fi-Verbindung unabhängig von der Rolle

-   Unterstützung für Anzeichen Betriebssystem DDE-Kanal zu WECHSELN oder Rolle über das WLAN-Client in\_ANGABE\_LINK\_ZUSTAND\_ÄNDERN

#### <a name="support-background-discovery"></a>Unterstützung Hintergrund Discovery

**Beschreibung**

Wenn implementiert, Unterstützung für die Ermittlung der Hintergrund der direkten Wi-Fi-Geräte, dadurch Anwendungen, die die direkte Wi-Fi-API verwenden, um die Verschiebung der Ermittlung, um umfangreichere Szenarien durch Zulassen der Anwendung an eine Benachrichtigung erhalten, wenn ein Gerät gefunden wird, im Vergleich zu müssen in regelmäßigen Abständen für diese Überprüfung zu aktivieren. Unterstützung für dieses Feature ermöglicht auch eine bessere Nutzung der Ressource.  

**Details**  

Gerät muss die relevanten-Funktionen in der WIFI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN gemäß der Spezifikation WDI

-   WIFI\_VIRTUALISIERUNG\_ATTRIBUTE
-   WIFI\_P2P\_ATTRIBUTE 

Wenn das Gerät dieser Anforderung unterstützt, muss das Scannen für direkte Wi-Fi-Geräte & GO auf alle unterstützt in regelmäßigen Abständen in D0 state sein.

#### <a name="support-ecsa"></a>Unterstützung eCSA

**Beschreibung**

Wenn implementiert, die Unterstützung für erweiterte Channel-Switch Annoucement (eCSA) gemäß den Anweisungen in der 802.11-Spezifikation, die direkte Wi-Fi-Client und in der Wi-Fi direkten WECHSELN. Dies ermöglicht eine bessere Leistung durch NIC verschieben UNTERWEGS oder reagieren auf eCSA Anfragen aus dem zu WECHSELN, die mit verbunden ist.


**Details**

Gerät muss die relevanten-Funktionen in der WIFI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN gemäß der Spezifikation WDI

-   WIFI\_SCHNITTSTELLE\_ATTRIBUTE 


Wenn diese Anforderungen wird unterstützt, müssen alle Wi-Fi Direct Ports eCSA unterstützen. Das Gerät ist im Modus WECHSELN muss es sein können erkennen, wenn das remote-Gerät (das es verbunden ist) eCSA unterstützt und eCSA zum Verschieben in einzelnen Channel-Konfiguration verwenden. Wenn das Gerät im Clientmodus befindet, klicken Sie dann reagieren Sie auf eCSA Anforderungen vom remote-Gerät (, die es verbunden ist). Das Gerät muss Änderung des Betriebssystem DDE-Kanal für Client & GO über das WLAN melden\_ANGABE\_P2P\_GRUPPE\_BETRIEBSSYSTEM\_CHANNEL weist darauf hin.

OS wird das Verhalten eCSA des Geräts nicht steuern, ist dies Gerät Implementierung.

#### <a name="support-concurrency"></a>Parallelität unterstützen

**Beschreibung**

Wenn implementiert, Unterstützung für den Betrieb von Szenarien wie Miracast oder Wi-Fi direkte & Wi-Fi-Online-Dienste zusammen mit der Verbindung zum Internet. Ohne Unterstützung für dieses das Gerät werden nur ein Endpunkt herstellen – Beispiel kann keine Verbindung hergestellt, Miracast beim auch mit dem Internet verbunden wird.


**Details**

Gerät muss die relevanten-Funktionen in der WIFI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN gemäß der Spezifikation WDI

-   WIFI\_VIRTUALISIERUNG\_ATTRIBUTE
-   WIFI\_P2P\_ATTRIBUTE


Diese Anforderungen wird unterstützt, muss Gerät der Unterstützung von mindestens 2 Wi-Fi direkte Rolle Ports gleichzeitig in der folgenden Konfiguration zusätzlich zu der Wi-Fi Direct Gerät Port werden:

-   Eine Gruppe Besitzer (GO) auf einem Wi-Fi Direct Port und -Client auf den anderen Wi-Fi direkte Anschlüsse gleichzeitig

-   Ein Client auf jedem Wi-Fi Direct Port gleichzeitig

-   Gerät kann während der Infrastruktur von Diensten für unterschiedliche Kanäle über die verschiedenen Bereiche (2,4/5 GHz) mit einer 2 gleichzeitiger Kanäle unterstützen.


Beispiel der erwarteten unterstützte Matrix für 2-Kanal & 2 Port Parallelität

-   Wenn das Gerät WLAN-802.11ac unterstützt:

| &nbsp;       | **ExTSTA Port** |     &nbsp;    |     &nbsp;     | **Wi-Fi Direct Rolle Port 1** |     &nbsp;    |    &nbsp;      | **Wi-Fi Direct Rolle Port 2** |    &nbsp;     |    &nbsp;      |
|-------------|-----------------|---------|----------|------------------------------|---------|----------|------------------------------|---------|----------|
| **Case\#** | 802. 11n         | 802. 11n | 802.11ac | 802. 11n                      | 802. 11n | 802.11ac | 802. 11n                      | 802. 11n | 802.11ac |
| ** **       | 2,4 mit Ghz         | 5 Ghz   | 5 GHz    | 2,4 mit Ghz                      | 5 Ghz   | 5 GHz    | 2,4 mit Ghz                      | 5 Ghz   | 5 GHz    |
| **1**       | STATION             | x       | x        | GEHE ZU                           | x       | x        | x                            | x       | x        |
| **2**       | STATION             | x       | x        | Client                       | x       | x        | x                            | x       | x        |
| **4**       | STATION             | x       | x        | x                            | Client  | x        | x                            | x       | x        |
| **6**       | STATION             | x       | x        | x                            | x       | Client   | x                            | x       | x        |
| **7**       | STATION             | x       | x        | GEHE ZU                           | x       | x        | Client                       | x       | x        |
| **8**       | STATION             | x       | x        | Client                       | x       | x        | Client                       | x       | x        |
| **9**       | STATION             | x       | x        | GEHE ZU                           | x       | x        | x                            | Client  | x        |
| **10**      | STATION             | x       | x        | Client                       | x       | x        | x                            | Client  | x        |
| **11**      | STATION             | x       | x        | GEHE ZU                           | x       | x        | x                            | x       | Client   |
| **12**      | STATION             | x       | x        | Client                       | x       | x        | x                            | x       | Client   |
| **14**      | STATION             | x       | x        | x                            | Client  | x        | x                            | Client  | x        |
| **16**      | STATION             | x       | x        | x                            | Client  | x        | x                            | x       | Client   |
| **18**      | STATION             | x       | x        | x                            | x       | Client   | x                            | x       | Client   |
| **19**      | x               | STATION     | x        | GEHE ZU                           | x       | x        | x                            | x       | x        |
| **20**      | x               | STATION     | x        | Client                       | x       | x        | x                            | x       | x        |
| **21**      | x               | STATION     | x        | x                            | GEHE ZU      | x        | x                            | x       | x        |
| **22**      | x               | STATION     | x        | x                            | Client  | x        | x                            | x       | x        |
| **23**      | x               | STATION     | x        | x                            | x       | GEHE ZU       | x                            | x       | x        |
| **24**      | x               | STATION     | x        | x                            | x       | Client   | x                            | x       | x        |
| **25**      | x               | STATION     | x        | GEHE ZU                           | x       | x        | Client                       | x       | x        |
| **26**      | x               | STATION     | x        | Client                       | x       | x        | Client                       | x       | x        |
| **27**      | x               | STATION     | x        | GEHE ZU                           | x       | x        | x                            | Client  | x        |
| **28**      | x               | STATION     | x        | Client                       | x       | x        | x                            | Client  | x        |
| **29**      | x               | STATION     | x        | GEHE ZU                           | x       | x        | x                            | x       | Client   |
| **30**      | x               | STATION     | x        | Client                       | x       | x        | x                            | x       | Client   |
| **31**      | x               | STATION     | x        | x                            | GEHE ZU      | x        | x                            | Client  | x        |
| **32**      | x               | STATION     | x        | x                            | Client  | x        | x                            | Client  | x        |
| **33**      | x               | STATION     | x        | x                            | GEHE ZU      | x        | x                            | x       | Client   |
| **34**      | x               | STATION     | x        | x                            | Client  | x        | x                            | x       | Client   |
| **35**      | x               | STATION     | x        | x                            | x       | GEHE ZU       | x                            | x       | Client   |
| **36**      | x               | STATION     | x        | x                            | x       | Client   | x                            | x       | Client   |
| **37**      | x               | x       | STATION      | GEHE ZU                           | x       | x        | x                            | x       | x        |
| **38**      | x               | x       | STATION      | Client                       | x       | x        | x                            | x       | x        |
| **39**      | x               | x       | STATION      | x                            | GEHE ZU      | x        | x                            | x       | x        |
| **40**      | x               | x       | STATION      | x                            | Client  | x        | x                            | x       | x        |
| **41**      | x               | x       | STATION      | x                            | x       | GEHE ZU       | x                            | x       | x        |
| **42**      | x               | x       | STATION      | x                            | x       | Client   | x                            | x       | x        |
| **43**      | x               | x       | STATION      | GEHE ZU                           | x       | x        | Client                       | x       | x        |
| **44**      | x               | x       | STATION      | Client                       | x       | x        | Client                       | x       | x        |
| **45**      | x               | x       | STATION      | GEHE ZU                           | x       | x        | x                            | Client  | x        |
| **46**      | x               | x       | STATION      | Client                       | x       | x        | x                            | Client  | x        |
| **47**      | x               | x       | STATION      | GEHE ZU                           | x       | x        | x                            | x       | Client   |
| **48**      | x               | x       | STATION      | Client                       | x       | x        | x                            | x       | Client   |
| **49**      | x               | x       | STATION      | x                            | GEHE ZU      | x        | x                            | Client  | x        |
| **50**      | x               | x       | STATION      | x                            | Client  | x        | x                            | Client  | x        |
| **51**      | x               | x       | STATION      | x                            | GEHE ZU      | x        | x                            | x       | Client   |
| **52**      | x               | x       | STATION      | x                            | Client  | x        | x                            | x       | Client   |
| **53**      | x               | x       | STATION      | x                            | x       | GEHE ZU       | x                            | x       | Client   |
| **54**      | x               | x       | STATION      | x                            | x       | Client   | x                            | x       | Client   |
| **55**      | x               | x       | x        | GEHE ZU                           | x       | x        | Client                       | x       | x        |
| **56**      | x               | x       | x        | Client                       | x       | x        | Client                       | x       | x        |
| **57**      | x               | x       | x        | GEHE ZU                           | x       | x        | x                            | Client  | x        |
| **58**      | x               | x       | x        | Client                       | x       | x        | x                            | Client  | x        |
| **59**      | x               | x       | x        | GEHE ZU                           | x       | x        | x                            | x       | Client   |
| **60**      | x               | x       | x        | Client                       | x       | x        | x                            | x       | Client   |
| **62**      | x               | x       | x        | x                            | Client  | x        | x                            | Client  | x        |
| **63**      | x               | x       | x        | x                            | GEHE ZU      | x        | x                            | x       | Client   |
| **64**      | x               | x       | x        | x                            | Client  | x        | x                            | x       | Client   |
| **66**      | x               | x       | x        | x                            | x       | Client   | x                            | x       | Client   |


-   Wenn WLAN-Gerät 802.11ac nicht unterstützt:

| **Case\#** | **Infrarot-Port** |   &nbsp;    | **Atemgerät Port 1** |    &nbsp;    | **Atemgerät Port 2** |   &nbsp;     |
|-------------|----------------|-------|----------------|--------|----------------|--------|
| ** **       | 2,4 mit Ghz        | 5 Ghz | 2,4 mit Ghz        | 5 Ghz  | 2,4 mit Ghz        | 5 Ghz  |
| **1**       | STATION            | x     | GEHE ZU             | x      | x              | X      |
| **2**       | STATION            | x     | Client         | x      | x              | X      |
| **4**       | STATION            | x     | x              | Client | X              | X      |
| **5**       | STATION            | x     | GEHE ZU             | x      | Client         | X      |
| **6**       | STATION            | x     | Client         | x      | Client         | X      |
| **7**       | STATION            | x     | GEHE ZU             | x      | x              | Client |
| **8**       | STATION            | x     | Client         | x      | x              | Client |
| **10**      | STATION            | x     | x              | Client | x              | Client |
| **11**      | x              | STATION   | GEHE ZU             | x      | x              | x      |
| **12**      | x              | STATION   | Client         | x      | x              | x      |
| **13**      | x              | STATION   | x              | GEHE ZU     | x              | x      |
| **14**      | x              | STATION   | x              | Client | x              | x      |
| **15**      | x              | STATION   | GEHE ZU             | x      | Client         | x      |
| **16**      | x              | STATION   | Client         | x      | Client         | x      |
| **17**      | x              | STATION   | GEHE ZU             | x      | x              | Client |
| **18**      | x              | STATION   | Client         | x      | x              | Client |
| **19**      | x              | STATION   | x              | GEHE ZU     | x              | Client |
| **20**      | x              | STATION   | x              | Client | x              | Client |
| **21**      | x              | x     | GEHE ZU             | x      | Client         | x      |
| **22**      | x              | x     | Client         | x      | Client         | x      |
| **23**      | x              | x     | GEHE ZU             | x      | x              | Client |
| **24**      | x              | x     | Client         | x      | x              | Client |
| **26**      | x              | x     | x              | Client | x              | Client |

 

#### <a name="support-internet-sharing"></a>Gemeinsame Nutzung Internet unterstützen

**Beschreibung**

Wenn implementiert werden, die Unterstützung für Tethering über wozu die Unterstützung für benutzerdefinierte SSID und WPA2 Auth/Verschlüsselung für gleichzeitige Betrieb von tethering und Station Connectivity virtualisierte Wi-Fi-Port.  

Geräte werden zur Unterstützung von mindestens 3 Clients tethering empfohlen.

Gerät muss die relevanten-Funktionen in der WIFI melden\_ABRUFEN\_ADAPTER\_FUNKTIONEN gemäß der Spezifikation WDI

-   WIFI\_VIRTUALISIERUNG\_ATTRIBUTE
-   WIFI\_P2P\_ATTRIBUTE
-   WIFI\_BAND\_INFO
-   WIFI\_PHY\_INFO

Unterstützung der erweiterten WMM Ebenen über Atemgerät Role-Ports

**Beschreibung**

Diese Anforderungen erfasst Aufwand von der WLAN-Treiber durchgeführt werden. Hierzu zählen außerdem Unterstützung für gleichzeitige Vorgang über Miracast, Station & Bluetooth.

**Details**

Die Qualität der Verbindung & Performance von Wi-Fi Direct ist für das Szenario Miracast entscheidend. Die Bewertung des Gerätetreibers werden die Ergebnisse für das Gerät bereitzustellen, finden Sie unter Richtlinien für eine angemessene Qualität Miracast Verbindung.  

WMM virtualisierten Ports – ExtSTA, einschließlich aller Ports unterstützt werden Wi-Fi Direct-Rolle (Gruppenbesitzer) und Wi-Fi Direct Rolle Anschluss (Client).

-   Die NIC sollte Priorisierung über zwei Ports (ExtSTA & eine Wi-Fi Direct Rolle Port) gleichzeitig unterstützen.

-   Priorisieren von Datenverkehr basierend auf 802.11e Access Kategorie (AC) markieren.

-   Wenn die NIC mit gleichzeitig in einzelnen Kanal virtualisiert ist, muss es übertragen Datenverkehr über verschiedene virtuelle Ports basierend auf WMM & Streaming Media-Angabe priorisieren sein.

-   Wenn die NIC über verschiedene Kanäle mit Parallelität virtualisiert ist, er muss möglicherweise übertragen Datenverkehr über verschiedene virtuelle Ports basierend auf WMM und Streaming Media-Angabe priorisieren und Empfangen von Datenverkehr wird über das gleichzeitige Kanäle bearbeitet.

Wenn WMM Priorisierung verwendet wird mit AC\_VI oder AC\_VO (Sprache/Video) WLAN-Gerät sollten die folgenden Anforderungen für Wartezeit und Paketverluste Verlust erfüllen.

| ** **                                                  | **ExSTA**     | **Wi-Fi Direct Rolle Port** | **Max. Eine Möglichkeit Wartezeit in der UDP für AC\_VI/AC\_VO Datenverkehr** | **Paketverlust für AC\_VI/AC\_VO Datenverkehr** |
|--------------------------------------------------------|---------------|-----------------------------|-----------------------------------------------------------|-------------------------------------------|
| **Nur ExSTA**                                         | AC\_VI/AC\_VO | NV                          | 30ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| ** **                                                  |               |                             |                                                           |                                           |
| **ExSTA + Wi-Fi direkt in Single-Channel-Parallelität** | AC\_VI/AC\_VO | &nbsp;                      | 30ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| **&nbsp;**                                             | &nbsp;        | AC\_VI/AC\_VO               | 30ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| **&nbsp;**                                             | AC\_VI/AC\_VO | AC\_VI/AC\_VO               | 30ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| ** **                                                  |               |                             |                                                           |                                           |
| **ExSTA + Wi-Fi direkt in Multi-Channel-Parallelität**  | AC\_VI/AC\_VO | &nbsp;                      | 40ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| **&nbsp;**                                             | &nbsp;        | AC\_VI/AC\_VO               | 40ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |
| **&nbsp;**                                             | AC\_VI/AC\_VO | AC\_VI/AC\_VO               | 50 ms                                                      | 0,5 %, nicht mehr als 3 aufeinander folgende Pakete |

<a name="device.network.wlan.supportwifidirectservices "></a>
## <a name="devicenetworkwlansupportwifidirectservices"></a>Device.Network.WLAN.SupportWiFiDirectServices 

### <a name="devicenetworkwlansupportwifidirectwifidirectservices-if-implementedwdi-drivers-only"></a>Device.Network.WLAN.SupportWiFiDirect.WiFiDirectServices (If-implementierte)**(nur WDI-Treiber)**

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>

**Beschreibung**

Wenn**,** Unterstützung für direkte Wi-Fi vom Wi-Fi-Treiber zum Aktivieren des direkten Wi-Fi-Diensts für abonnieren und Veröffentlichen von direkten Wi-Fi-Diensten implementiert. Windows SDK wird bieten APIs für die Verwendung von Wi-Fi-Online-Dienste, app-Entwickler beispielsweise über Peer-to-Peer-Anwendungen erstellen können: Multiplayer Spiele, Dateifreigabe oder mit Gerät synchronisieren 

**Details**  

Gerät muss die folgenden Funktionen gemäß der Spezifikation WDI gemeldet:

-   Frames-Aktion in unterstützten WDI\_SCHNITTSTELLE\_ATTRIBUTE

-   Unterstützt in WDI Discovery-Service\_P2P\_ATTRIBUTE

P2P Service Namen Discovery unterstützt in WDI\_P2P\_ATTRIBUTESMax P2P Service Name Ankündigung Bytes in unterstützt WDI\_P2P\_ATTRIBUTESOptional Support wird empfohlen, die unten aufgeführten Funktionen:

-   Ermittlung von P2P-Geräte und Dienste in WDI Hintergrund\_P2P\_ATTRIBUTE (dringend empfohlen)

-   Passiv belauschen Verfügbarkeitsstatus in WDI\_P2P\_ATTRIBUTE (dringend empfohlen)

-   Unterstützt in WDI Informationssuche Service P2P\_P2P\_ATTRIBUTE

-   Max P2P Dienst Informationen Ankündigung Bytes in WDI unterstützt\_P2P\_ATTRIBUTE

Wenn diese Anforderung unterstützt wird, muss das Gerät folgende Aktion ausführen, wie in der Spezifikation WDI definiert sein:

-   Unterstützung für Wi-Fi direkt

-   Unterstützung für das Senden der Anforderung und Antwort-Aktion Frames

-   Unterstützung für das Abfragen AQNP

-   Unterstützung für die Angabe der empfangenen Aktion Rahmen

<a name="device.network.wlan.supportwirelessdocking"></a>
## <a name="devicenetworkwlansupportwirelessdocking"></a>Device.Network.WLAN.SupportWirelessDocking

### <a name="devicenetworkwlansupportwirelessdocking-if-implemented-wdi-drivers-only"></a>Device.Network.WLAN.SupportWirelessDocking (If-implementierte) **(nur WDI-Treiber)**

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>
**Beschreibung:**

Drahtlosen docking-Lösung über 802.11ac oder 802.11ad muss Treiber Wi-Fi-Treiber-Schnittstelle (WDI) verwenden, die bietet Andocken und Zubehör Discovery / Verbindung über einen einheitlichen Peer zu Peer und direkte Wi-Fi-Services-Protokoll. Entnehmen Sie Wi-Fi-Treiber-Schnittstelle (WDI) Spezifikation 1.0.20 oder höher für Implementierungsdetails feature

Wenn 802.11ad verwendet wird, der folgenden neue PHY-Typ anzugeben:

**Implementieren der 802.11ad (If-implementierte)**

Gerät muss 802.11ad melden PHY-Typ 9 (WDI\_PHY\_TYP\_DMG) in der WDI\_PHY\_INFO Strukturen zurückgegebene OID\_WDI\_ABRUFEN\_ADAPTER\_FUNKTIONEN.

<a name="device.network.wlan.supporthostednetwork"></a>
## <a name="devicenetworkwlansupporthostednetwork"></a>Device.Network.WLAN.SupportHostedNetwork

### <a name="devicenetworkwlansupporthostednetworkhostednetwork-if-implemented-native-wi-fi-drivers-only"></a>Device.Network.WLAN.SupportHostedNetwork.HostedNetwork (If-implementierte) **(nur für systemeigene Wi-Fi-Treiber)**

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop Edition (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
</td></tr></table>
**Beschreibung:**

Mit diesem Feature kann ein Windows-Computer einen einzelnen physischen drahtlosen Adapter für die Verbindung als Client für einen Hardware Access Point (AP), während gleichzeitig die fungiert als Softwareupdate AP andere WLAN-fähigen Geräte zulassen zum Herstellen der Verbindung verwenden.

