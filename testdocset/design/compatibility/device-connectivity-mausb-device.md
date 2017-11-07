---
title: Device.Connectivity.MAUSB.Device
Description: "Anforderungen gelten für MA-USB-Geräte. Allerdings MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cd308bf987203d27936644cec9a6759fe83151e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.MAUSB.Device

 - [Device.Connectivity.MAUSB.Device ](#device.connectivity.mausb.device)
-->

<a name="device.connectivity.mausb.device"></a>
##Device.Connectivity.MAUSB.Device 

Die folgenden Anforderungen gelten für MA-USB-Geräte.

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Nach der Tabelle mit Definitionen im Kontext von Anforderungen MA-USB-Hub- and -Verwaltungs-Agent-USB-Gerät verwendet:

PAL MA-USB-Gerät:

MA-USB-Gerät PAL, ist gemäß Definition in der Spezifikation MA-USB-die Komponente eines MA-USB-Gerät oder MA-USB-Hub an, der den Transport von USB-Nutzlast über die Schnittstelle im MA Link verwaltet.

Integrierte USB-Gerät hinter einem MA-USB-Gerät:

Dies bezieht sich auf die USB-Gerät Logik Block in ein MA-USB-Gerät, das USB-Gerät funktioniert, verwendet wird, gemäß der Spezifikation USB 2.0 oder USB-3.1 mit Ausnahme der, die das physische USB-Medium betreffen. Der Kürze halber wird ein integriertes USB-Gerät hinter einem MA-USB-Gerät als integrierte USB-Gerät bezeichnet werden,

Integrierte USB 2.0 Hub hinter einem MA-USB-Hub:

Dies bezieht sich auf den USB-Hub Logik Block in einen Verwaltungs-Agent-USB-Hub, die USB-Gerät funktioniert gemäß der Spezifikation USB 2.0 außer diese portanforderungen Upstream-, an denen die physische USB mittelgroße beteiligt durchführt. Der Kürze halber wird eine integrierte USB 2.0-Hub hinter einem MA-USB-Hub als integrierte USB 2.0-Hub bezeichnet werden;

USB 3.1 integriert Hub hinter einem MA-USB-Hub:

Dies bezieht sich auf den USB-Hub Logik Block in einen Verwaltungs-Agent-USB-Hub, die USB-Gerät funktioniert gemäß der Spezifikation USB 3.1 außer diese portanforderungen Upstream-, an denen die physische USB mittelgroße beteiligt durchführt. Der Kürze halber wird eine integrierte USB-Hub für die 3.1 hinter einem MA-USB-Hub als integrierter USB-3.1 Hub bezeichnet werden,

Beachten Sie, dass integrierte USB-Geräte hinter einer USB 2.0 oder 3.1 USB-Hub hinter einem MA-USB-Hub für verkabelt USB-Gerät unter Device.Connectivity.UsbDevices Kategorie aufgeführten Mindestanforderungen erforderlich sind.

### <a name="deviceconnectivitymausbdevicebulkoutbuffersize"></a>Device.Connectivity.MAUSB.Device.BulkOutBufferSize

*MA-USB-Gerät muss über mindestens 64 KB Pufferspeicherplatz pro nicht SuperSpeed Massen Out-Endpunkten und mindestens 512 KB Pufferspeicherplatz pro SuperSpeed Massen Out Endpunkte unterstützen.*

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

MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden.


MA-USB-Gerät muss zuverlässig und für eine optimale Leistung (Durchsatz) arbeiten können, um diese minimale Puffergrößen unterstützen. Diese Puffergrößen werden vom MA-USB-Gerät in das Endpunkt Antwortpaket gemeldet durch MA-USB-Spezifikation v1.0a, Abschnitt 6.3.7 beschrieben.

 - SuperSpeed Massen Out - 512KB

 - nicht - SuperSpeed Massen Out - 64KB

### <a name="deviceconnectivitymausbdevicefunctionsuspendselectivesuspend"></a>Device.Connectivity.MAUSB.Device.FunctionSuspendSelectiveSuspend

*MA-USB-Geräte, die 3.1 Geräte hinter sie integriert haben müssen ordnungsgemäß Funktion anhalten implementieren.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Jede Funktion der integrierten 3.1 Geräts an, das im Ruhezustand ist, bevor ein MA-USB-Gerät angehalten wird verbleibt im Zustand Suspend Funktion, wenn das Verwaltungs-Agent-USB-Gerät aus dem Standbymodus fortgesetzt wird. Jede Funktion der integrierten 3.1 Geräts an, das im Ruhezustand ist, bevor das integrierte Gerät angehalten wird verbleibt im Zustand Suspend Funktion, wenn das integrierte Gerät aus dem Standbymodus fortgesetzt wird. Integrierte USB-Geräte, die aus dem Standbymodus fortgesetzt werden behalten einen minimalen Satz von Gerät Zustandsinformationen gemäß im Abschnitt 9.2.5.2 der USB-3.0-Spezifikation. Integriertes USB-Gerät in einer angehaltenen starren bevor ein MA-USB-Gerät angehalten wird bleibt im angehaltenen Zustand, wenn das Verwaltungs-Agent-USB-Gerät aus dem Standbymodus fortgesetzt wird.

### <a name="deviceconnectivitymausbdeviceipmode"></a>Device.Connectivity.MAUSB.Device.IPMode

*MA-USB-Geräten müssen Support für IP-Modus implementieren.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

MA-USB-Geräte müssen implementieren die Unterstützung für IP-Modus gemäß der MA-USB-Spezifikation v1.0a, Abschnitt 4.5.3.2 "Anforderungen für IP-Modus".

### <a name="deviceconnectivitymausbdeviceisochronousdeviceanddriver"></a>Device.Connectivity.MAUSB.Device.IsochronousDeviceAndDriver

*Isochrone USB-Gerät und Treiber-Anforderung*

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

MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden.

-   **Integrierte ISO-USB-Gerät und Treiber enthalten mehrere alternative Einstellungen zur Unterstützung der maximale Flexibilität der Hardware-Schnittstellenoptionen:**

    -   Wenn eine beliebige Einstellung alternative isochrone Bandbreite nutzt, enthalten Geräte und Treiber mehrere alternative Einstellungen für jede Schnittstelle.

-   **Integrierte USB-Gerät und Treiber verwenden nicht isochrone Bandbreite für alternative 0 festlegen:**

    -   Integraetd USB-Geräte und Treiber dürfen nicht isochrone Bandbreite für alternative 0 festlegen verwenden. Geräte müssen Bandbreite erforderlich, nur, wenn sie verwendet werden.

-   **Integriertes USB-isochrone schnellen oder Hochgeschwindigkeits Gerät mit mehr als 50 Prozent der USB-Busbandbreite bietet alternative Einstellungen:**

    -   Wenn eine integrierte USB-isochrone schnellen oder Hochgeschwindigkeits-Gerät mehr als 50 Prozent der Busbandbreite USB verwendet wird, muss es bieten alternative Einstellungen, mit denen das Gerät wechseln Sie auf eine Einstellung, die weniger als 50 Prozent der Busbandbreite verwendet und ausgeführt werden als ein Gerät der jeweiligen Klasse (ex. Wenn es eine Kamera ist, dann muss Sie weiterhin Video stream), obwohl es eine niedrigere Qualität Modus werden kann.
        Integrierte USB-Geräte mit angefügten Hostcontroller werden von dieser Anforderung ausgenommen.

-   **Integriertes USB-Gerät mit Schnittstellen mit isochrone Endpunkte hat mindestens eine alternative Schnittstelle für Szenarien mit niedriger Bandbreite:**

    -   Integriertes USB-Gerät muss mindestens einen alternativen Benutzeroberfläche für geringe Bandbreite angeben, wie in USB-Spezifikation, Version 2.0 oder höher, Abschnitt 9.6.5 beschrieben.

*Hinweise zum Entwurf*

Finden Sie im Abschnitt 9.6.5 der Universal Serial Bus-Spezifikation, Version 2.0.
Wenn mindestens zwei Geräte, die mehr als 50 Prozent der Busbandbreite verwenden und bieten keine andere Einstellungen verbunden sind, funktioniert nur eines der Geräte zu einem Zeitpunkt.
Finden Sie unter USB-Spezifikation, Version 2.0 oder höher, Abschnitte 5.6 und 5.7.

### <a name="deviceconnectivitymausbdevicemausbspeccompliance"></a>Device.Connectivity.MAUSB.Device.MAUSBSpecCompliance

*MA-USB-Geräten muss ein USB-IF-Spezifikation kompatibel*

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

MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden.

MA-USB-Geräte müssen mit MA-USB-Spezifikation v1.0a kompatibel oder höher sein.

### <a name="deviceconnectivitymausbdevicemsoscontainerid"></a>Device.Connectivity.MAUSB.Device.MsOsContainerId

*USB-Geräte, die den Microsoft OS Container ID-Deskriptor implementieren müssen ordnungsgemäß implementieren.*

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

MA-USB-Anforderungen sind derzeit optional und werden bis 2017 nicht erzwungen werden.

Wenn ein integriertes Multifunktions USB-Gerät Microsoft® Betriebssystem **ContainerID** Deskriptor implementiert wird, wird das Gerät im Deskriptor Feature Betriebssystem Microsoft. 

Microsoft Betriebssystem **ContainerID** Deskriptor ermöglicht Windows® zum Erkennen von integrierten Mehrzweckgeräte ordnungsgemäß. Deskriptor bietet eine Möglichkeit für die Geräteknoten als ein physisches Objekt in der **Geräte und Drucker** -Benutzeroberfläche (UI) angezeigt werden.

### <a name="deviceconnectivitymausbdevicemustbefunctionalafterresume"></a>Device.Connectivity.MAUSB.Device.MustBeFunctionalAfterResume

*MA-USB-Geräte müssen nach dem Fortsetzen aus den Status funktionsfähig sein.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Nach dem MA-USB-fortsetzen müssen MA-USB-Gerät PAL funktionsfähig sein, ohne eine MA-USB-Gerät zurückzusetzen. Darüber hinaus müssen integrierte USB-Gerät funktionsfähig nach USB Resume werden ohne MA-USB-Gerät zurückzusetzen, oder ein USB-Gerät zurückzusetzen.

Eingeben nicht rechtzeitig betriebsbereit Geräte werden Code 10 oder andere vom System markiert. Bestimmte Klassen von Geräten ordnungsgemäß reagieren nicht auf Systemereignisse, wie fortsetzen Sie, und erfordern Sie oberen Treiber oder erwarten Sie genaue Boot Anzeigedauer ordnungsgemäß funktionieren.

### <a name="deviceconnectivitymausbdevicemustnotdisconnectduringsuspend"></a>Device.Connectivity.MAUSB.Device.MustNotDisconnectDuringSuspend

*MA-USB-Geräte oder integrierte USB-Geräte müssen beim Wechseln zu oder Reaktivierung aus dem Standbymodus nicht trennen.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

MA-USB-Gerät muss nicht vom Host während MA-USB-anhalten oder fortsetzen getrennt.

Integrierte USB-Geräte müssen nicht während des USB-anhalten/fortsetzen oder Anhalten/Fortsetzen der MA-USB-trennen.

### <a name="deviceconnectivitymausbdevicerespondallstringrequests"></a>Device.Connectivity.MAUSB.Device.RespondAllStringRequests

*Ein integrierter USB-Gerät muss auf alle Zeichenfolge Anfragen reagieren, die der Host an Indizes sendet.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Integrierte USB-Geräte müssen entsprechend reagieren auf Zeichenfolge Anforderungen, die der Host sendet. Integrierte Geräte müssen hängen, wenn keine Zeichenfolge im abgefragten Index gespeichert ist oder wenn ein Anforderungsfehler vorhanden ist. Integrierte Geräte müssen nicht selbst zurücksetzen oder nicht mehr funktioniert. Dies wird beschrieben, in der USB-Spezifikation, Version 2.0 oder höher, Abschnitt 9.6.

### <a name="deviceconnectivitymausbdeviceresponseslimitedbywlengthfield"></a>Device.Connectivity.MAUSB.Device.ResponsesLimitedByWlengthField

*Integrierte USB-Gerät Responss auf Host Anforderungen werden vom Feld wLength Größe begrenzt.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Alle USB-Gerät Anforderungen enthalten ein Feld wLength. Antworten durch das integrierte USB-Gerät zum Host Anforderungen muss vom Größe &lt;= wLength Feld der Anforderung Gerät gemäß Definition in der USB-Spezifikation, Revision1.1 oder höher, Abschnitt 9.3.5.
 

### <a name="deviceconnectivitymausbdeviceserialnumbers"></a>Device.Connectivity.MAUSB.Device.SerialNumbers

*Fortlaufende Zahlen des USB-werden durch das integrierte USB-Gerät für bestimmte Geräteklassen implementiert und sind für bestimmte Gerätemodelle eindeutig.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Fortlaufende Zahlen des USB-muss durch die integrierte USB-Gerät für die folgenden Geräteklassen implementiert werden:

-   Bluetooth (Klassencode 0xE0, Unterklasse 0 x 01, 0 x 01 Protocol)

-   Kommunikation Device-Klasse (Klassencode 0 x 02)

-   Massenspeichergerät (Klassencode 0 x 08)

-   Scannen/Imaging (Code 0 x 06-Klasse)

-   Drucken (Code 0 x 07-Klasse)

-   Hosten Sie über das Netzwerkadapter und Geräte über das Netzwerkadapter (Klassencode 0xE0, Unterklasse 02)

Fortlaufende Zahlen des USB-sind für alle anderen Geräteklassen optional.    Darüber hinaus müssen Seriennummer des Geräts Modell implementiert werden, alle Geräte desselben Modells eindeutige fortlaufende Zahlen haben.

*Hinweise zum Entwurf*

Weitere Informationen über USB-Klasse Gerätedetails, finden Sie unter "Definierten 1.0-Klassencodes" unter: <http://go.microsoft.com/fwlink/?LinkId=40497>.
Weitere Informationen zur Implementierung der Seriennummer finden Sie unter USB-Spezifikation, Version 2.0 oder höher, Abschnitt 9.6.
 

### <a name="deviceconnectivitymausbdeviceserialnumbersusevalidcharacters"></a>Device.Connectivity.MAUSB.Device.SerialNumbersUseValidCharacters

*Eine integrierte USB-Gerät, mit der Seriennummer Hersteller definiert implementiert muss gültige Zeichen enthalten.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Eine USB-Seriennummer muss eine Zeichenfolge sein, die eine Hersteller bestimmt ID bestehend aus gültigen Zeichen enthält. Gültige Zeichen werden in der Windows-Treiberkits definiert "USB\_GERÄT\_DESKRIPTOR."

### <a name="deviceconnectivitymausbdevicespeedcapabilitymatch"></a>Device.Connectivity.MAUSB.Device.SpeedCapabilityMatch

*Integrierte USB-Gerät muss mit der USB-Geschwindigkeit im Deskriptor Funktion Geschwindigkeit des MA-USB-Geräts angekündigt auflisten.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

*Integrierte USB-Gerät muss mit der USB-Geschwindigkeit im Deskriptor Funktion Geschwindigkeit des MA-USB-Geräts angekündigt auflisten. Geschwindigkeit der Funktion Deskriptor ist Teil der Funktion Antwort vom MA-USB-Gerät als im angegebenen Abschnitt 6.3.3.1 eines MA-USB-Spezifikation v1.0a zurückgegeben.*

### <a name="deviceconnectivitymausbdevicesupportswifidirectandwsb"></a>Device.Connectivity.MAUSB.Device.SupportsWiFiDirectAndWSB

*MA-USB-Geräte unterstützen, direkte Verbindung WiFi und WiFi Serial Bus*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Implementierung von Netzwerk-Verwaltungs-Agent-USB-Gerät muss die folgenden Anforderungen Posteingang Windows MA-USB-Host zuverlässig entwickelt erfüllen:

-   MA-USB-Hub-Gerät muss unterstützen direkte Wi-Fi-Services (Peer-to-Peer Services 1.x) über ein 802. 11n / Ac und/oder 802.11ad NIC

    -   Verschiebt wahrscheinlich asp2 (Wi-Fi direkte Ermittlung und verbinden)

-   MA-USB-Hub-Gerät muss WSB v0.18 implementieren&lt;neueste&gt; als ein Werbekunden

### <a name="deviceconnectivitymausbdevicetcpimplementation"></a>Device.Connectivity.MAUSB.Device.TCPImplementation

*MA-USB-TCP Implementierung für Zuverlässigkeit*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

TCP-Implementierung der MA-USB-Gerät muss die folgenden Anforderungen Posteingang Windows MA-USB-Host zuverlässig entwickelt erfüllen:

-   TCP verzögerte Bestätigung Optimierung muss deaktiviert werden.

-   TCP Nagle-Algorithmus-Implementierung muss deaktiviert werden.

-   TCP muss mindestens 64 KB empfangen Pufferspeicherplatz bereitstellen.

### <a name="deviceconnectivitymausbdeviceuseusbclassonlyforcontrollerorhub"></a>Device.Connectivity.MAUSB.Device.UseUsbClassOnlyForControllerOrHub

*Drittanbieter-INF-Dateien enthalten die Klasse "USB" nur, wenn das Gerät ein USB-Hostcontroller einen Stamm oder einen externen Hub befindet.*

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

MA-USB-Anforderungen sind derzeit optional und werden nicht erzwungen, bis 2017.

Klasse USB wird häufig falsch für Geräte verwendet, die nicht über eine vordefinierte Klasse verfügen. Beispielsweise verwendet eine USB-Maus Klasse HID, während eine USB-Smartcard-Smartcard-Leser Klasse verwendet. Klasse USB ist für Hostcontroller und Root oder externen USB-Hubs reserviert. Wenn der Hersteller ein Gerät, die USB als den Bus verwendet jedoch keine Klasse Windows definiert wurde verfügt, muss er einen eigenen Klasse oder Klasse GUID definieren. Die Setupklasse zugeordnet USB-Gerät muss nicht mit dem Bustyp verwendet werden. Der Setupklasse "USB" (ClassGuid = {36fc9e60-c465-11cf-8056-444553540000}) ist für USB-Hostcontroller (einschließlich MA-USB-Hostcontroller PAL) und Stamm oder externen USB-Hubs reserviert. Sie müssen nicht für andere Gerätekategorien verwendet werden.

 
*Hinweise zum Entwurf*

Microsoft bietet systemdefinierte Setupklassen für die meisten Arten von Geräten. Systemdefinierte Setupklasse GUIDs sind definiert, in der Windows-Treiberkits "Devguid.h."
Wenn Sie die falsche Klasse auswählen, wird das Gerät in einen falschen Speicherort im Geräte-Manager und in die Windows Vista-Benutzeroberfläche angezeigt. Verwenden diese Klasse nicht richtig möglicherweise den Gerätetreiber Hardware Kompatibilitätstests ein Fehler auftritt.
Eine Liste der Windows-Klassenbibliothek GUIDs, finden Sie unter Windows-Treiberkits "System-Supplied Gerät Setupklassen": <http://msdn.microsoft.com/en-us/library/ff553419.aspx>.

