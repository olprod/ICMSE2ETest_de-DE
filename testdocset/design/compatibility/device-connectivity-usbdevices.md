---
title: Device.Connectivity.UsbDevices
Description: "Anforderungen für alle Geräte, die über USB, einschließlich USB-Hubs, aber nicht USB-Controller verbinden."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7c2d24859b1a1228e81c3ee197b8768d4d10ac21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.UsbDevices

 - [Device.Connectivity.UsbDevices](#device.connectivity.usbdevices)
-->

<a name="device.connectivity.usbdevices"></a>
##Device.Connectivity.UsbDevices

*Gilt für alle Geräte über USB, einschließlich USB-Hubs verbunden sind. Gilt nicht für USB-Controller.*

### <a name="deviceconnectivityusbdevicesdebugcomplieswithdebugspec"></a>Device.Connectivity.UsbDevices.DebugCompliesWithDebugSpec

*USB-Debug-Gerät muss die USB2 Debug Device Specification entsprechen.*

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

USB-Geräten konzipiert zum Debuggen über USB 2.0 müssen USB2 Debuggen Gerät Funktionsspezifikation, entsprechen, die Details auf dem Gerät Framework, Befehle und zusätzliche operative Anforderungen enthält.

### <a name="deviceconnectivityusbdevicesdebugcomplieswithdebugspecusb3"></a>Device.Connectivity.UsbDevices.DebugCompliesWithDebugSpecUSB3

*USB-3.0 Debug Kabel müssen die USB-3.0-Spezifikation entsprechen.*

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

USB-Kabel für USB-3.0 Host debuggen müssen die Universal Serial Bus 3.0-Spezifikation, Abschnitt 5.5.2 entsprechen.

### <a name="deviceconnectivityusbdevicesdeviceattachlessthan100ms"></a>Device.Connectivity.UsbDevices.DeviceAttachLessThan100ms

*USB-Gerät, die Signale Gerät Anfügen muss nach mindestens 100 ms reagieren.*

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

Wenn das USB-Gerät Gerät anschließen signalisiert hat, das Betriebssystem bietet ein Debounce Intervall von 100 ms. Das Gerät muss am Ende dieses Intervall reagieren. Dies wird im USB-Spezifikation, Revision2.0, Abschnitt 7.1.7.3 beschrieben. Dadurch wird sichergestellt, dass die Stromversorgung und mechanischen Verbindungen stabil sind, bevor das angeschlossene Gerät zurückgesetzt wird.

### <a name="deviceconnectivityusbdevicesfunctionsuspendselectivesuspend"></a>Device.Connectivity.UsbDevices.FunctionSuspendSelectiveSuspend

*3.0 USB-Geräten müssen ordnungsgemäß Funktion unterbrechen und selektive aussetzen implementieren.*

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

Jede Funktion, die im Ruhezustand ist, bevor ein Gerät selektiv ist ausgesetzt bleibt die Funktion Suspend-Status auf, wenn das Gerät aus der selektiven Ruhezustand fortgesetzt wird. Geräte müssen nicht alle platzieren Gerätefunktionen in der Funktion suspend-Zustand. Geräte müssen melden, dass die selektive Zustand angehalten werden soll.

SuperSpeed Geräte ignorieren das GERÄT\_REMOTE\_REAKTIVIERUNG Feature-Auswahl.

Wenn alle Funktionen eines Geräts SuperSpeed in der Funktion sind suspend-Status und der PORT\_U2\_TIMEOUT Feld ist so programmiert, dass 0xFF, initiiert das Gerät U2 nach 10 Millisekunden (ms) der Inaktivität Link. Weitere Informationen finden Sie im Abschnitt 9.2 der USB-3.0-Spezifikation.

Geräte, die aus der selektiven fortgesetzt werden suspend-Zustand beibehält, einen minimalen Satz von Gerät Zustandsinformationen als im angegebenen Abschnitt 9.2.5.2 der USB-3.0-Spezifikation.
 

### <a name="deviceconnectivityusbdevicesinternaldevicesmustsupportsuspend"></a>Device.Connectivity.UsbDevices.InternalDevicesMustSupportSuspend

*Alle intern verbundenen USB-Geräte müssen nach der Inaktivität selektive Anhalten von wechseln.*

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

Alle intern verbundenen USB-Geräte müssen Daten aneinander nach Treiber für diese Geräte das USB-selektive aussetzen initiieren eingeben, wird den Suspend-Zustand. Treiber von Drittanbietern für interne Geräte auf entsprechenden Systemen müssen USB-selektive aussetzen implementieren.

Geräte in dieser Geräteklassen abwählen können USB-selektive aussetzen unterstützen:

-   Drucker

-   Scanner

-   Fax

### <a name="deviceconnectivityusbdevicesisochronousdeviceanddriver"></a>Device.Connectivity.UsbDevices.IsochronousDeviceAndDriver

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

**1. ISO-USB-Gerät und Treiber enthalten mehrere alternative Einstellungen zur Unterstützung der maximale Flexibilität der Hardware-Schnittstellenoptionen:**

Wenn eine beliebige Einstellung alternative isochrone Bandbreite nutzt, enthalten Geräte und Treiber mehrere alternative Einstellungen für jede Schnittstelle.

**2. USB-Gerät und Treiber verwenden nicht isochrone Bandbreite für alternative 0 festlegen:**

Geräte und Treiber dürfen nicht isochrone Bandbreite für alternative 0 festlegen verwenden. Geräte müssen Bandbreite erforderlich, nur, wenn sie verwendet werden.

**3. USB isochrone schnellen oder Hochgeschwindigkeits Gerät mit mehr als 50 Prozent der USB-Busbandbreite bietet alternative Einstellungen:**

Wenn ein USB-isochrone schnellen oder Hochgeschwindigkeits-Gerät mehr als 50 Prozent der Busbandbreite USB-verwendet, müssen sie bieten alternative Einstellungen, mit denen das Gerät wechseln Sie auf eine Einstellung, die weniger als 50 Prozent der Busbandbreite verwendet und ausgeführt werden als ein Gerät der jeweiligen Klasse (ex. Wenn es eine Kamera ist, dann muss Sie weiterhin Video stream), obwohl es eine niedrigere Qualität Modus werden kann.
Geräte mit angefügten Hostcontroller werden von dieser Anforderung ausgenommen.

**4. USB-Gerät mit Schnittstellen mit isochrone Endpunkte hat mindestens eine alternative Schnittstelle für Szenarien mit niedriger Bandbreite:**

USB-Gerät muss über mindestens einen alternativen Benutzeroberfläche für geringe Bandbreite bereitstellen, wie in USB-Spezifikation, Version 2.0 oder höher, Abschnitt 9.6.5 beschrieben.

*Hinweise zum Entwurf*

Finden Sie im Abschnitt 9.6.5 der Universal Serial Bus-Spezifikation, Version 2.0.
Wenn mindestens zwei Geräte, die mehr als 50 Prozent der Busbandbreite verwenden und bieten keine andere Einstellungen verbunden sind, funktioniert nur eines der Geräte zu einem Zeitpunkt.
Finden Sie unter USB-Spezifikation, Version 2.0 oder höher, Abschnitte 5.6 und 5.7.
 

### <a name="deviceconnectivityusbdevicesmsoscontainerid"></a>Device.Connectivity.UsbDevices.MsOsContainerId

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

Wenn ein USB-Mehrzweckgerät Microsoft® Betriebssystem **ContainerID** Deskriptor implementiert wird, wird das Gerät im Microsoft-Betriebssystem Feature Deskriptor. 

Microsoft-Betriebssystem **ContainerID** Deskriptor ermöglicht Windows® Mehrzweckgeräte ordnungsgemäß zu erkennen. Deskriptor bietet eine Möglichkeit für die Geräteknoten als ein physisches Objekt in der **Geräte und Drucker** -Benutzeroberfläche (UI) angezeigt werden.

### <a name="deviceconnectivityusbdevicesmustbefunctionalafterresume"></a>Device.Connectivity.UsbDevices.MustBeFunctionalAfterResume

*Angeschlossene USB-Geräte müssen nach dem Fortsetzen aus den Status funktionsfähig sein.*

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

Eingeben nicht rechtzeitig betriebsbereit Geräte werden Code 10 oder andere vom System markiert. Bestimmte Klassen von Geräten ordnungsgemäß reagieren nicht auf Systemereignisse, wie fortsetzen Sie, und erfordern Sie oberen Treiber oder erwarten Sie genaue Boot Anzeigedauer ordnungsgemäß funktionieren. Ein Gerät muss in der Lage, ohne einen Anschluss zurücksetzen nach Resume-Funktion, aber Sie müssen auch weiterhin funktionsfähig, wenn ein Zurücksetzen auftritt.
Ein Gerät muss den angefügte Status (USB-Spezifikation 2.0, Abschnitt 9.1) konfiguriert werden soll, und das Gerät muss den konfigurierten Status vor dem zugehörigen Funktionen vielleicht verwendet (auch bekannt als, kann das Gerät verwendet). Dies erfolgt gemäß der Spezifikation USB 2.0 wie in den Abschnitten 9.1 und 9.2.6.2 "nach ein Port zurücksetzen oder fortgesetzt wurde wird, die USB-Systemsoftware erwartet wird, ein Wiederherstellungsintervall von""10 ms bereitzustellen, bevor das Gerät an den Anschluss angeschlossen erwartet wird, um auf Datenübertragungen zu reagieren. Das Gerät kann Datenübertragungen während des Intervalls Wiederherstellung ignorieren."

*Klärung:*

Geräten muss funktionieren nach dem Fortsetzen aus den Status, ob ein Port zurücksetzen oder nicht ausgegeben wird.

### <a name="deviceconnectivityusbdevicesmustnotdisconnectduringsuspend"></a>Device.Connectivity.UsbDevices.MustNotDisconnectDuringSuspend

*USB-Geräte müssen nicht vom Upstream-Port beim Zugriff auf trennen, oder Fortsetzen von selektive angehalten werden soll.*

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

USB-Geräte müssen nicht trennen der Upstream-Port während der selektiven Prozess anhalten.

Zum Testen dieser Anforderung verursacht wir das Gerät zum Wechseln in die selektive suspend-Zustand, und klicken Sie dann fortsetzen des Geräts. Während dieses Vorgangs wir Beachten Sie die Bits Port Status des Ports Upstream- und stellen Sie sicher, dass das Gerät nicht während dieser Zeit getrennt wird. Wir werden dieses Prozesses mehrere Male wiederholt.
 

### <a name="deviceconnectivityusbdevicesmustresumewithoutforcedreset"></a>Device.Connectivity.UsbDevices.MustResumeWithoutForcedReset

*Alle USB-Geräte beim Fortsetzen aus dem Standbymodus, im Ruhezustand, ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene Zurücksetzen des USB-Hostcontroller.*

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

Alle USB-Geräte beim Fortsetzen aus dem Standbymodus, im Ruhezustand, ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene Zurücksetzen des USB-Hostcontroller.

*Hinweise zum Entwurf*  

Registrierungsschlüssel ForceHCResetOnResume die unten aufgeführten KB dokumentiert nicht, für die Geräte erforderlich ist ordnungsgemäß nach Resume in Windows 7: <http://support.microsoft.com/kb/928631>.
Beachten Sie, dass eine bekannte Gruppe von vorhandene Geräten derzeit führen erfordern eine erzwungene zurücksetzen auf fortsetzen, sollten diese Geräte in einer Liste, die durch das Betriebssystem, wodurch diese Geräte bei Resume zurückgesetzt wird gehalten behandelt werden. Das Ziel dieser Anforderung wird sichergestellt, dass diese Liste der Geräte, die zurückgesetzt werden müssen, um nach Resume nicht wächst angezeigt und diese Geräte dem Standbymodus Statusübergänge ordnungsgemäß verarbeiten kann, ohne zurückgesetzt.
Ein Zurücksetzen der gesamte USB-Hostcontroller Ergebnisse in deutlich mehr Zeit, die für alle USB-Geräte verfügbar wird nach dem System fortsetzen, da es möglicherweise nur ein Gerät bei Adresse 0 zu einem Zeitpunkt, hat diese Enumeration für alle USB-Geräte auf dem Bus serialisiert werden soll. Wir haben auch gesehen zurücksetzen den Hostcontroller einen ungültigen SE1 Signal Status auf einige Hostcontroller dazu führen, dass kann die einige USB-Geräte hängen oder drop aus dem Bus wiederum verursachen. Darüber hinaus können nicht Geräte alle privaten Status über dem Standbymodus fortsetzen verwalten, wie diesen Status auf Zurücksetzen verloren.

### <a name="deviceconnectivityusbdevicesmustsignalattachwithin500ms"></a>Device.Connectivity.UsbDevices.MustSignalAttachWithin500ms

*Geräte müssen signalisieren innerhalb 500 ms anfügen, nachdem das System fortgesetzt.*

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

Nachdem das System aus dem Standbymodus fortgesetzt, wird der Hub-Treiber den Status des Ports abrufen, mit dem das Gerät verbunden ist. Wenn das Gerät nicht angezeigt wird als verbunden, Warten der Hub-Treiber 500 Millisekunden (ms) vor der Hub-Treiber den Port-Status erneut abgefragt. Wenn das Gerät innerhalb dieser Zeit als verbundenen angezeigt wird, müssen der Hub nicht das Gerät zum Plug & Play aufgelistet erneut eine höhere benutzerfreundlichkeit führt. Für Bus-Geräten in der USB-Spezifikation ist dies bereits vorhanden. Die Anforderung wird nun auch auf Geräten mit Self angewendet.

### <a name="deviceconnectivityusbdevicesmustsupportsuspend"></a>Device.Connectivity.UsbDevices.MustSupportSuspend

*Alle Bus-basiertes USB-Geräte müssen nach der Inaktivität selektives USB-unterstützen.*

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

Der Treiber für ein Bus-Gerät initiiert den USB-selektive aussetzen Prozess. Das Gerät kann den Suspend-Zustand aus alle eingeschaltet eingeben. Nachdem es eine Konstante Leerlauf auf den Upstream-internetbasierte Bus Zeilen für mehr als 3.0 ms erkennt, muss das Gerät den Übergang in den Suspend-Zustand beginnen. Suspend-Zustand, das Gerät muss nur zeichnen anhalten aktuellen aus dem Bus nach nicht mehr als 10 ms Bus Inaktivität alle ihre Ports wie in der USB-Spezifikation, Version 2.0, 7.1.7.6, 6 9.1.1.6 und 9.2.6.2 Abschnitten beschrieben.

Erläuternde Hinweise zu USB-selektive anhalten im eingebetteten USB-Geräten finden Sie in der folgenden Anforderung: Device.Connectivity.UsbDevices.InternalDevicesMustSupportSuspend.

Erläuternde Hinweise zu USB-selektive aussetzen in Windows RT-Systemen finden Sie in der folgenden Anforderungen: Device.Connectivity.UsbDevices.MustSupportSuspendOnRT.

### <a name="deviceconnectivityusbdevicesrespondallstringrequests"></a>Device.Connectivity.UsbDevices.RespondAllStringRequests

*Ein USB-Gerät muss auf allen Zeichenfolge Anfragen reagieren, die der Host an Indizes sendet.*

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

USB-Geräte müssen entsprechend reagieren auf Zeichenfolge Anforderungen, die der Host sendet. Geräte müssen hängen, wenn keine Zeichenfolge im abgefragten Index gespeichert ist oder wenn ein Anforderungsfehler vorhanden ist. Geräte müssen nicht selbst zurücksetzen oder nicht mehr funktioniert. Dies wird beschrieben, in der USB-Spezifikation, Version 2.0 oder höher, Abschnitt 9.6.

### <a name="deviceconnectivityusbdevicesresponseslimitedbywlengthfield"></a>Device.Connectivity.UsbDevices.ResponsesLimitedByWlengthField

*USB-Gerät Antworten auf Host Anforderungen werden vom Feld wLength Größe begrenzt.*

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

Alle USB-Gerät Anforderungen enthalten ein Feld wLength. Antworten vom USB-Gerät zum Host Anforderungen muss vom Größe &lt;= wLength dar, der die Anforderung Gerät gemäß Definition in der USB-Spezifikation, Revision1.1 oder höher, Abschnitt 9.3.5.
 

### <a name="deviceconnectivityusbdevicesserialnumbers"></a>Device.Connectivity.UsbDevices.SerialNumbers

*USB-Seriennummer für bestimmte Geräteklassen implementiert werden und sind für bestimmte Gerätemodelle eindeutig.*

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

Fortlaufende Zahlen des USB-muss für die folgenden Geräteklassen implementiert werden:

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
 

### <a name="deviceconnectivityusbdevicesserialnumbersusevalidcharacters"></a>Device.Connectivity.UsbDevices.SerialNumbersUseValidCharacters

*Ein USB-Gerät, die fortlaufende Zahlen des Herstellers definierten implementiert muss gültige Zeichen enthalten.*

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

Eine USB-Seriennummer muss eine Zeichenfolge sein, die eine Hersteller bestimmt ID bestehend aus gültigen Zeichen enthält. Gültige Zeichen werden in der Windows-Treiberkits definiert "USB\_GERÄT\_DESKRIPTOR."

### <a name="deviceconnectivityusbdevicessuperspeedonconnectviausb3port"></a>Device.Connectivity.UsbDevices.SuperSpeedOnConnectViaUsb3Port

*Wenn Upstream-SuperSpeed Beendigung steht, müssen Geräte immer eine Verbindung her, auf dem 3.0 USB-Anschluss und nie eine Verbindung herstellen, auf den USB 2.0-Port.*

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

In einem 3.0 USB-Hub freigeben zwei downstream Ports, USB 2.0-Anschluss und einen Port Superspeed denselben Connector. Wenn ein SuperSpeed (d. h., nicht Hub) an diese Connectors Gerät angeschlossen ist, das Gerät muss immer auf den Port SuperSpeed verbinden. Das Gerät muss auf den USB 2.0-Anschluss nie eine Verbindung herstellen.

Um dies zu testen, wird die Software sicherstellen, dass der 3.0 USB-Anschluss Statusbits ein verbundenes Gerät anzeigen und die USB 2.0-Port-Statusbits ein verbundenes Gerät nicht angezeigt werden. 

Definition des "Verbinden" finden Sie im Abschnitt 2 des USB-Spezifikation 3.0 unter "verbunden".

### <a name="deviceconnectivityusbdevicestestedusingmicrosoftusbstack"></a>Device.Connectivity.UsbDevices.TestedUsingMicrosoftUsbStack

*USB-Geräte müssen mit Microsofts xHCI Stack installiert getestet werden.*

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

Alle USB-Geräte (niedrig, vollständig, hoch und Geschwindigkeit Super-Geräte) muss mit Microsofts Extensible Host Controller Interface (xHCI) auf einem Windows-System installiert und aktiviert Stack getestet werden.

**Hinweis:** Während der USB-Self Tests eine bestimmte USB-Test Stack zu Testzwecken installiert ist, dies der erwartete und zulässige ist.

### <a name="deviceconnectivityusbdevicesusbifcertification"></a>Device.Connectivity.UsbDevices.UsbifCertification

*USB-Geräte müssen Sie USB-IF-Tests übergeben oder USB-IF zertifiziert werden.*

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

USB-Geräte müssen übergeben (Sofern es USB-Implementierer Forum) Tests oder USB-WENN zertifiziert.

USB-C PD-fähigen Geräte, Hubs Ladegeräte implementieren müssen, Version 1.1 der Spezifikation USB-Typ-C oder höher und Version 2.0 v1. 1 der Spezifikation PD oder höher und müssen PD Silicon, das entsprechend der USB zertifiziert ist verwenden-IF des USB-C Produkt Matrix testen.

Weitere Informationen finden Sie im Whitepaper auf Windows-Logo Kit USB-IF zu testen:

-   <http://www.Microsoft.com/whdc/Connect/USB/wlk-USB-if-Testing.mspx>

### <a name="deviceconnectivityusbdevicesusbtypecaltmodecertification"></a>Device.Connectivity.UsbDevices.USBTypeCAltModeCertification

*USB-Typ-C alternativen Modus Geräte sind mit ihren jeweiligen Organisationen zertifiziert.*

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

Wenn ein USB-Typ-C-Gerät unterstützt eine alternative Modus Standard- und der Branche, die besitzt, dass Standard eine entsprechende Zertifizierung verfügt, muss das Gerät PD Silicon, die von dieser Branche zusätzlich zu den USB-zertifiziert ist verwenden-IF.

Angenommen, wenn ein USB-Typ-C Gerät PD Silicon DisplayPort alternativen Modus zusätzlich zu USB und PD unterstützt, klicken Sie dann, Silicon muss werden von zertifiziert VESA für die Funktionalität DisplayPort darüber hinaus an den USB-IF USB und PD-Funktionalität.

Zertifizierung für herstellerspezifische alternative Modi ist nicht erforderlich.

### <a name="deviceconnectivityusbdevicesusbtypeccertifiedcables"></a>Device.Connectivity.UsbDevices.USBTypeCCertifiedCables

*USB-Typ-C-Geräte, die im Lieferumfang von Kabel im Lieferumfang von certified Kabel*

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

Wenn ein Gerät USB-Typ-C ist ein Kabel oder ein Adapter, die Kabel und/oder Adapter im Lieferumfang von müssen und USB-WENN zertifiziert.

Darüber hinaus, wenn die USB-Typ-C Kabel oder Adapter für eine alternative Modus Standard- und der Branche, die besitzt, dass eine entsprechende Zertifizierung-Standard besitzt die verwendet wird, muss das Kabel oder Adapter diese Zertifizierung abgerufen werden.

### <a name="deviceconnectivityusbdevicesusbtypecaltmodedevicecompat"></a>Device.Connectivity.UsbDevices.USBTypeCAltModeDeviceCompat

*USB-Typ-C alternativen Modus Device-Kompatibilität*

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

Einen alternativen Modus Gerät, das nur einen einzigen USB-Anschluss verfügt, der auf den downstream internetbasierte Port (DFP) verbindet muss auch der alternativen Modus entsprechende USB-Funktionalität bereitstellen.

Beispielsweise muss einem Speichergerät Thunderbolt alternative Modus USB-C auch Funktion als ein USB-Massenspeichergerät über USB 2.0 oder USB-3.0 sein.

Hinweis: Alternativen Modus Adapter müssen nicht gleichbedeutend mit seinem alternative Modus USB-Funktionalität zu ermöglichen. Beispielsweise muss ein Adapter DisplayPort oder MHL alternative Modus USB-C nicht auch ein video Protokoll unterstützt werden, die über USB 2.0 oder USB-3.0 arbeitet.

### <a name="deviceconnectivityusbdevicesuseusbclassonlyforcontrollerorhub"></a>Device.Connectivity.UsbDevices.UseUsbClassOnlyForControllerOrHub

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

Klasse USB wird häufig falsch für Geräte verwendet, die nicht über eine vordefinierte Klasse verfügen. Beispielsweise verwendet eine USB-Maus Klasse HID, während eine USB-Smartcard-Smartcard-Leser Klasse verwendet. Klasse USB ist für Hostcontroller und Root oder externen USB-Hubs reserviert. Wenn der Hersteller ein Gerät, die USB als den Bus verwendet jedoch keine Klasse Windows definiert wurde verfügt, muss er einen eigenen Klasse oder Klasse GUID definieren. Die Setupklasse zugeordnet USB-Gerät muss nicht mit dem Bustyp verwendet werden. Der Setupklasse "USB" (ClassGuid = {36fc9e60-c465-11cf-8056-444553540000}) für die USB-Hostcontroller und Root oder externen USB-Hubs reserviert ist. Sie müssen nicht für andere Gerätekategorien verwendet werden.

 
*Hinweise zum Entwurf*

Microsoft bietet systemdefinierte Setupklassen für die meisten Arten von Geräten. Systemdefinierte Setupklasse GUIDs sind definiert, in der Windows-Treiberkits "Devguid.h."
Wenn Sie die falsche Klasse auswählen, wird das Gerät in einen falschen Speicherort im Geräte-Manager und in die Windows Vista-Benutzeroberfläche angezeigt. Verwenden diese Klasse nicht richtig möglicherweise den Gerätetreiber Hardware Kompatibilitätstests ein Fehler auftritt.
Eine Liste der Windows-Klassenbibliothek GUIDs, finden Sie unter Windows-Treiberkits "System-Supplied Gerät Setupklassen": <http://msdn.microsoft.com/en-us/library/ff553419.aspx>.

### <a name="deviceconnectivityusbdeviceswirelessusbobtainswusblogofromusbif"></a>Device.Connectivity.UsbDevices.WirelessUsbObtainsWusbLogoFromUsbif

*Drahtlose USB-Gerät oder Host benötigen ein Certified Wireless-USB-Logo aus der USB-IF.*

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

Alle Wireless-USB-Geräte, benötigen Sie ein Certified Wireless USB-Logo aus der USB-IF.

### <a name="deviceconnectivityusbdeviceswirelessusbwimediaalliace"></a>Device.Connectivity.UsbDevices.WirelessUsbWiMediaAlliace

*Zertifizierte Wireless USB-Gerät oder Host muss alle erforderlichen WiMedia Allianz Kompatibilitätstests übergeben.*

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

Drahtloses USB-Gerät muss WiMedia Allianz Radio Kompatibilitätstests übergeben.

