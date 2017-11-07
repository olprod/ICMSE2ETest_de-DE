---
title: Device.Input.Location
Description: "Windows 10 Speicherort Treiber können entweder GNSS-Treiber, die in der Vorversion Sensor-Klasse Erweiterung Treiber integriert sind implementieren oder GNSS-Treiber, die in der GNSS DDI integrieren in Windows 10 eingeführt."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: e2e798929b6d558188451d2dc975aee2b0232cec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.Location

 - [Device.Input.Location](#device.input.location)
-->

<a name="device.input.location"></a>
##Device.Input.Location

*Windows 10 Speicherort Treiber können eine der folgenden Treibermodelle implementieren.*

-   Integrieren in der Vorversion Sensor-Klasse Erweiterung Treiber GNSS-Treiber

*OR*

-   Integrieren in der GNSS DDI GNSS Treiber eingeführt in Windows 10

### <a name="deviceinputlocationactivetracking-if-implemented"></a>Device.Input.Location.ActiveTracking (sofern implementiert)

*Aktive Überwachung breadcrumbing*

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

Diese Anforderung kann einen GNSS Chip aktiv den Standort eines Benutzers basierend auf Breadcrumbing Technologie verfolgen. Das Betriebssystem wird Abladung von Breadcrumbing der Hardware und Standort des Benutzers bei Bedarf erhalten. Diese features ermöglicht das Betriebssystem, um die Speicherort aufgezeichneten eines Benutzers auf eine genauere Weise zu erfassen.

### <a name="deviceinputlocationassistedgnss-if-implemented"></a>Device.Input.Location.AssistedGNSS (sofern implementiert)

*Nur relevant, wenn die Hardware den Speicherort-Stapel für unterstützt GNSS des angegebenen Typs verwendet wird.*

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

Unterstützung an den Empfänger GNSS wird verwendet, um den Empfänger an eine Position erwerben schneller, um auch im Falle einer sehr schwache Signal Erwerb aktivieren, und das zu weniger Strom zu aktivieren. Der Speicherort Plattform unterstützt das GNSS Gerät mit einer groben Position bereitstellen, kann ungefähre Zeit und es auch als Proxy der vom Gerät GNSS unterstützten Formate proprietäre Ephemeris dienen.

### <a name="deviceinputlocationbase"></a>Device.Input.Location.Base

*Speicherort Geräte müssen die folgenden grundlegende Funktionen unterstützen.*

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

Speicherort Geräten muss ordnungsgemäß interagieren mit der Plattform empfangen Speicherort Anfragen und bieten eine Antwort mit einer Position oder einen Fehler. Der Austausch von Funktionen müssen unterstützt, und die Konfigurationsbefehle für verwendeten Funktionen in der Benutzeroberfläche Treiber vorhanden und zwingend erforderlich ist. Stellen Sie sicher, dass sie ein Intervall bestimmt den Typ der Speicherort Sitzung und den Speicherort Sitzungsparameter Standortdaten Bericht müssen alle Speicherort Geräte. Die Anwendung gewünschten Genauigkeit und anderen Sitzungsparameter sollte so effizient wie möglich anzugebende Standortdaten berücksichtigt werden.

Da zwei Treibermodelle für das unterstützt werden, haben wir Anforderungen spezifische Anforderungen und Tests für die einzelnen an.

***Integrieren in der Vorversion Sensor-Klasse Erweiterung Treiber GNSS-Treiber***

Das GNSS-Gerät muss die folgenden grundlegenden Anforderungen unterstützen:

<html><!--edit: improve layout and tagging of these lists, tables, and blockquotes-->
    <ul>
        <li><p><strong>Feld-Unterstützung für Speicherort Berichte Daten</strong></p></li>
    </ul>
    <blockquote>
        <p>-Der Ort API macht Standortdaten über integrierter Standardberichte verfügbar. Diese Berichte werden von Ortungsanbietern aufgefüllt, die den Speicherort API automatisch verwaltet.</p>
        <p>-Speicherort Sensor Geräte, die die Kategorie als SENSOR_CATEGORY_LOCATION meldet, (obwohl Gerät Treiber Schnittstellen ISensorDriver::OnGetSupportedSensorObjects und IsensorDriver::OnGetProperties()) eines integrierten Berichts unterstützen muss, damit der Speicherort API er seine Daten und den Sensor verwalten kann. Jede integrierten Berichts verfügt über eine Reihe von erwarteten Datenfeldern (obwohl Gerät Treiber Schnittstelle IsensorDriver::OnGetSupportedDataFields() und IsensorDriver::OnGetDataFields()), das den Speicherort API sucht nach.</p>
        <p>-Alle integrierten Berichte müssen SENSOR_DATA_TYPE_TIMESTAMP zusätzlich zu den angegebenen Feldern bereitgestellt werden. Dieses Feld hat den Zeitpunkt, zu dem die Daten in UTC erfasst wurden.</p>
        <p>-Der Ort API unterstützt ein integriertes Berichts: die LatLongReport, die in der Antwort Maße für Breitengrad/Längengrad (Lat/Long) und ein Fehler erforderlich sind.  Unterstützung für die LatLongReport ist erforderlich für alle Speicherort aufgeführt.</p>
        <p>Zur Unterstützung der LatLongReport sind die folgenden Felder erforderlich:</p>
    </blockquote>
    <table>
        <thead>
            <tr class="header">
                <th>Datenfeld</th>
                <th>Datentyp</th>
                <th>Details</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_LATITUDE_DEGREES</td>
                <td>VT_R8</td>
                <td>Zeigt die aktuelle Breite in Grad, die im Bereich [-90, + 90] sein müssen</td>
            </tr>
            <tr class="even">
                <td>SENSOR_DATA_TYPE_LONGITUDE_DEGREES</td>
                <td>VT_R8</td>
                <td>Zeigt die aktuellen Längengrad in Grad, die im Bereich [-180, und + 180] sein müssen</td>
            </tr>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_ERROR_RADIUS_METERS</td>
                <td>VT_R8</td>
                <td>Die tatsächlichen Breiten- und Längengrad müssen innerhalb eines Kreises, mit diesem Radius (in Metern) zu um die gemeldeten (Breitengrad, Längengrad) gezeichnet sein. Ermöglicht der API Speicherort Sensoren priorisieren. dynamisch aktualisiert werden sollen, und müssen ungleich NULL und positive sein.</td>
            </tr>
        </tbody>
    </table>
    <p>Als Teil der LatLongReport die folgenden Felder sind optional, jedoch müssen gemeldet werden, sobald Sie verfügbar sind:</p>
    <table>
        <thead>
            <tr class="header">
                <th>Optionale Datenfeld</th>
                <th>Datentyp</th>
                <th>Details</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_ALTITUDE_ELLIPSOID_METERS</td>
                <td>VT_R8</td>
                <td>Die Höhe im Hinblick auf die WGS84 Ellipsoid (in Metern)</td>
            </tr>
            <tr class="even">
                <td>SENSOR_DATA_TYPE_ALTITUDE_ELLIPSOID_ERROR_METERS</td>
                <td>VT_R8</td>
                <td>Der Fehler des Messung des aktuellen Höhe (in Metern)</td>
            </tr>
        </tbody>
    </table>
    <blockquote>
        <p>
            <br />
Wichtig: Die Speicherort-API unterstützt eine zusätzliche Reihe von Datenfeldern (die Datenfelder NMEA entsprechen). Weitere Informationen finden Sie unter Sensoren in den Abschnitt Gerät und Treiber Technologien der WDK.
        </p>
    </blockquote>
    <p> </p>
    <blockquote>
        <p>Die nachfolgenden Anforderung wird sichergestellt, dass der Treiber die richtige Weise Speicherort-Bericht-Ereignisse auslöst. Wenn nicht das richtige Verhalten gefolgt wird, der Speicherort API blockiert des Sensors und Clientanwendungen erhalten keine Daten.</p>
    </blockquote>
    <ul>
        <li>
            <p>
                <strong>Generieren von Berichten für Sensor-Daten</strong></p>
                <p>Das Gerät muss eine Reihe von gültigen ISensorDataReports für eine oder beide der beiden Typen Speicherort Berichte generieren können. Jeden Bericht generiert muss mindestens die minimale Datenfelder für den Bericht () enthalten.<br />
Der-Sensor und der Speicherort Plattform hängen Daten zur Verfügung gestellt, die Plattform über Gerätetreibern, die der Sensor Device Driver Interface implementiert haben. In den meisten Fällen werden Geräte mithilfe der Sensor und Speicherort Plattform überprüft werden.
            </p>
        </li>
        <li>
            <p>
                <strong>Hinweise zu den konfigurierbaren Eigenschaften</strong></p>
                <p>Die folgenden Eigenschaften festgelegt werden müssen im Gerätetreiber als Filter- und Leistung Management Kriterien genutzt werden. Beide Eigenschaften müssen auf Basis-Client überwacht werden.
            </p>
        </li>
    </ul>
    <blockquote>
        <p>Die Eigenschaften sind als konfigurierbare implementiert werden:</p>
    </blockquote>
    <table>
        <thead>
            <tr class="header">
                <th>Eigenschaft</th>
                <th>Datentyp</th>
                <th>Details</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_PROPERTY_CURRENT_REPORT_INTERVAL</td>
                <td>VT_UI4</td>
                <td>Legt die minimale Frequenz (in Millisekunden), die ein Client Datenberichte Sensor empfangen möchte.</td>
            </tr>
            <tr class="even">
                <td>
SENSOR_PROPERTY_LOCATION_DESIRED_ACCURACY<br />
                </td>
                <td>VT_UI4</td>
                <td>
Legt einen Hinweis, wie genau der Treiber bemühen sollten, sein.<br />
DESIRED_ACCURACY_DEFAULT: Der Sensor sollte Power und anderen Aspekten Kosten optimieren. GNS Sensoren werden nicht von der Location-API aufgelistet werden, es sei denn, Standortdaten von anderen Anbietern im System nicht verfügbar ist oder Genauigkeit der Daten kleiner als 500m ist.<br />
DESIRED_ACCURACY_HIGH: Der Sensor sollte den höchsten Genauigkeit Bericht möglich übermitteln. Der Speicherort-API wird immer auf alle Speicherort aufgeführt (einschließlich GNSS), um die genauesten Position mögliche erwerben verbunden.
                </td>
            </tr>
        </tbody>
    </table>
    <p><em><strong>Integrieren in der GNSS DDI Treiber in Windows 10 für GNSS eingeführt</strong></em></p>
    <p>Das GNSS-Gerät muss die folgenden grundlegenden Anforderungen unterstützen:</p>
    <table>
        <thead>
            <tr class="header">
                <th><strong>Plattform und Treiber Funktion Exchange</strong></th>
                <td>
                    <p>Überprüfen Sie für den Datenaustausch zwischen der Plattform (GNSS_SEND_PLATFORM_CAPABILITY) und die Treiber (GNSS_GET_DEVICE_CAPABILITY) zu ihren jeweiligen Funktionen im Zusammenhang mit. Es wird erwartet, dass der Treiber ordnungsgemäß seine Gerätefunktionen an der Plattform gesendet, da die Plattform Speicherort ihr Verhalten entsprechend anpassen wird.</p>
                    <p>Funktionen wie Abstand Tracking und Geofencing darf nur deklariert werden, wenn sie auf das Gerät GNSS übergeben werden können, ist dies, wenn sie keine erfordern, dass den Anwendung Prozessor, führen Sie die Verfolgung.</p>
                </td>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td><strong>Treiber Befehl Kontrollkästchen</strong></td>
                <td>Überprüfen Sie, dass die grundlegende Gerätetreibers Befehle für Produkt- und Test-Aktivierung erforderlich sind. Ähnliche, ClearAgnssData.</td>
            </tr>
            <tr class="even">
                <td><strong>Überprüfen Sie grundlegende einzelnen Screenshot</strong></td>
                <td>Ein einzelnes Aufnahme Sitzung beginnt und ausgeführt wird, bis eine endgültige Fix empfangen wird. Davon ausgehen Sie, dass eine endgültige Behebung innerhalb von zwei Minuten übermittelt werden. In diesem Fall konnte Informationen zur Unterstützung verfügbar sein. Für den Fall, dass Informationen zur Unterstützung verfügbar ist wird erwartet, dass eine endgültige Fehlerbehebung in 10 Sekunden übermittelt werden.</td>
            </tr>
            <tr class="odd">
                <td><strong>Eigenständige grundlegende einzelnen Aufnahme solcher überprüfen</strong></td>
                <td>Stellt sicher, dass ein Treiber, der befindet sich in einer kalt Zustand und hat keinen Zugriff auf AGNSS eines beliebigen Typs, weiterhin eine endgültige Fehlerbehebung für eine einzelne Anforderung Einmalmodus erreichen kann. Davon ausgehen Sie, dass eine endgültige Behebung innerhalb von zwei Minuten übermittelt werden.</td>
            </tr>
            <tr class="even">
                <td><strong>Screenshot mehrere angrenzenden Sitzung Prüfung</strong></td>
                <td>Überprüft, ob die hundert einzelnen Aufnahme Sitzungen nach dem anderen ohne Probleme ausgeführt werden kann. Erwarten Sie, dass jeder einzelnen Einmalmodus Sitzung eine endgültige Fix fehlerfrei erreicht.</td>
            </tr>
        </tbody>
    </table>
</html>


### <a name="deviceinputlocationgeofencing-if-implemented"></a>Device.Input.Location.Geofencing (sofern implementiert)

*Diese Anforderung wird nur unterstützt, wenn die Hardware Geofencing unterstützt und der Treiber GNSS von der GNSS DDI in Windows 10 eingeführt integrieren.*

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

Dies ermöglicht GPS geografische Grenzen oder virtuellen Hürden zu definieren. Wenn ein Gerät eingibt oder Sie der Geofence verlässt ermöglicht es den Administrator eines mobilen Geräts mit Triggeraktionen und Benachrichtigungen. Praktische Anwendungsbereiche sind die Möglichkeit für einen Retail Store Besitzer zum Erstellen einer Geofence das Geschäft Einzelhandel und Coupons an einen Kunden mit den Retail Store-app auf seinen mobilen Gerät zu senden.

Wenn implementiert, muss das Gerät die folgenden Anforderungen unterstützen.

| **Grundlegende Geofence**    | GeoFence kann erfolgreich hinzugefügt und gelöscht werden. Überprüfen Sie bei der Konsistenz müssen.                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Geofence nachverfolgen 1**   | Fügen Sie einer Geofence, um die aktuelle Position mit UNBEKANNTEN Zustand hinzu, und überprüfen Sie EINTRAG-Ereignis.                                                                                                          |
| **Geofence Spur 2**   | Fügen Sie eine Geofence mit ANGEGEBENE Zustand so, dass die aktuelle Position außerhalb der Geofence ist. Vergewissern Sie sich Exit-Ereignis.                                                                              |
| **Geofence nachverfolgen 3**   | Hinzufügen einer Geofence, um die aktuelle Position mit ANGEGEBENE Zustand, und stellen Sie sicher, dass kein Ereignis ausgelöst wird                                                                                            |
| **Geofence nachverfolgen 4**   | Fügen Sie ein Geofence mit EXITED Zustand hinzu, sodass die aktuelle Position außerhalb der Geofence ist. Stellen Sie sicher, dass kein Ereignis ausgelöst wird.                                                                    |
| **Geofence nachverfolgen 5**   | Fügen Sie eine Geofence, um die aktuelle Position mit UNBEKANNTEN Zustand und Benachrichtigungstyp als EXIT nur und stellen Sie sicher, dass kein Ereignis empfangen werden                                                                 |
| **Geofence nachverfolgen 6**   | Fügen Sie eine Geofence (mit angegebene Zustand hinzu), sodass die aktuelle Position außerhalb des Geofence und die Warnung Geben Sie EINGEBEN und sicherzustellen, dass KEIN Ereignis empfangen wird                           |
| **Zuverlässigkeit**        | Ruft die maximale Anzahl von Geofences an, denen die Hardware unterstützt. Legen Sie diese maximale Anzahl von Geofences, um die aktuelle Position mit unbekanntes Zustand und erwarten, dass die Anzahl der Eintrag/Exit-Ereignis. |
| **Geofence löschen**    | Fügen Sie mehrerer Geofences hinzu, und klicken Sie dann alle gleichzeitig löschen. Muss auf Konsistenz überprüfen.                                                                                                             |
| **Negative Geofence** | Fügen Sie eine Geofence mit Parametern Bad (null Radius) hinzu.                                                                                                                                               |
| **Geofence Grenze** | Hinzufügen einer Geofence mit sehr kleine Radius (5m).                                                                                                                                                     |

### <a name="deviceinputlocationsupl-if-implemented"></a>Device.Input.Location.SUPL (sofern implementiert)

*Diese Anforderung gilt nur für einen GNSS Treiber integrieren in der GNSS DDI eingeführt in Windows 10.*

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

Der Client Secure Benutzer Ebene Speicherort (SUPL) muss von unabhängigen Hardwarehersteller Mobilfunkbetreiber für die Unterstützung implementiert werden. Die Treiberschnittstelle bietet Mechanismen zum Konfigurieren des Clients SUPL mit den Informationen für den Mobilfunkbetreiber abgerufen. Die einzigen SUPL Konfigurationen von der Location-Plattform unterstützt, sind die, die ein Mobilfunkbetreiber zugeordnet sind, und nur eine SUPL Konfiguration wird zu einem Zeitpunkt unterstützt.

Die Tests in diesem Abschnitt wird sichergestellt, dass der Client SUPL SUPL Konfigurationsbefehle von der Plattform Speicherort empfangen kann. Es sind keine Tests in der HLK, um die Integration zwischen dem GNSS-Treiber und der Speicherort-Plattform für die Unterstützung der Benutzer Benachrichtigungen beim Empfang der NI (Netzwerk initiiert) Speicherort Anfragen zu überprüfen. Eine solche Überprüfungen erfolgen müssen mit dedizierten Systeme und Test-Suites, mit denen die Konformität SUPL OMA überprüft.

### <a name="deviceinputlocationv2pul-if-implemented"></a>Device.Input.Location.V2PUL (sofern implementiert)

*Dies gilt nur für eine Integration in die GNSS DDI eingeführt in Windows 10 GNSS Treiber zur Verfügung.*

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

Speicherort von V2-Ebene (V2UPL)-Anforderung gilt nur für Geräte mit mobilverbindungen CDMA, und gegebenenfalls durch den Mobilfunkbetreiber.
