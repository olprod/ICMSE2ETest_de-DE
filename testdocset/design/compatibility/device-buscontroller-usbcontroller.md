---
title: Device.BusController.UsbController
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 5fbf26151b20bd2cf29fcae04f6ec2748bde235d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.UsbController

 - [Device.BusController.UsbController](#device.buscontroller.usbcontroller)
-->

<a name="device.buscontroller.usbcontroller"></a>
##Device.BusController.UsbController

### <a name="devicebuscontrollerusbcontrollerimplementatleastonexhcispcstructforusb2"></a>Device.BusController.UsbController.ImplementAtLeastOneXhciSpcStructForUSB2

*xHCI Controller müssen mindestens ein xHCI Protokoll-Funktion unterstützten Struktur für USB 2.0 implementieren.*

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

Erweiterbare Host Controller Interface (xHCI) Controller müssen mindestens ein xHCI unterstützt Protokoll Funktion Struktur für USB 2.0 implementiert, wie im Abschnitt 7.2 der xHCI-Spezifikation beschrieben.

Dies wirkt sich auf die Abwärtskompatibilität mit USB 2.0.

### <a name="devicebuscontrollerusbcontrollermaintaindevicestateonresumes1ands3"></a>Device.BusController.UsbController.MaintainDeviceStateOnResumeS1andS3

*USB-Hostcontroller muss Gerätestatus auf Fortsetzen aus S1 oder S3 verwalten.*

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

Für den Hostcontroller, um den Gerätestatus beizubehalten muss der USB-Hostcontroller einen USB-Bus zurücksetzen auf ein System dem Standbymodus Statusübergang von S3 nach S0 oder von S1 auf S0 nicht ausführen.

USB-Hostcontroller an, die integriert oder in den Chipsatz South Bridge eingebettet werden müssen den USB-Bus zurücksetzen aus den PCI-Bus zurückgesetzt, damit Sie um Resume Zeitraum zu verkürzen entkoppeln. Resume-Vorgänge von S1 oder S3 müssen USB-Bus zurückgesetzt nicht generiert werden. Ein USB-Bus Reset ist ein Zurücksetzen Signal, das über den USB-Bus USB-Geräte gesendet wird, die mit den USB-Hostcontroller verbunden sind. 

Systeme, die eine USB-Tastatur angeschlossen ist, dürfen USB-Bus zurückgesetzt, um das System mit einem Kennwort bei Reaktivierung des Systems aus S3 entsperren ausführen.

Aus Sicherheitsgründen darf das BIOS in einem mobilen System Problem einen USB-Bus zurückgesetzt, wenn das System mit einer Dockingstation angefügt ist, das eine Festplatte (HDD) verfügt, die auf ersten Resume Kennwort gesperrt ist.

Zurücksetzen des Kennworts HDD ist zulässig, unabhängig davon, ob das mobile System angedockt ist. Die folgenden Szenarien sind zulässig:
 

-   Nicht angedockte Systeme mit einer HDD Kennwort aktiviert

-   Angedockten Systeme mit einer HDD Kennwort aktiviert

-   Hinzufügen oder Entfernen von einer Festplatte

Wenn die Dockingstation verfügt nicht über eine systemeigene HDD oder die Dockingstation verfügt nicht über ein Kennwort, müssen das BIOS keinen USB-Bus-Reset ausgeben.

Es ist akzeptabel, zulassen den Controller Power s3 verloren gehen, wenn das System auf Batterie ist.

*Hinweise zum Entwurf*  

Finden Sie unter Erweiterte Host Controller Interface-Spezifikation für Universal Serial Bus, Version 1.0, Anhang A.

Dies gilt nicht für Systeme, die Standbymodus verbunden zu unterstützen.
 

### <a name="devicebuscontrollerusbcontrollermustresumewithoutforcedreset"></a>Device.BusController.UsbController.MustResumeWithoutForcedReset

*Alle USB-Hostcontroller müssen beim Fortsetzen aus dem Standbymodus, im Ruhezustand, ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene zurücksetzen.*

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

Alle USB-Hostcontroller beim Fortsetzen aus dem Standbymodus, im Ruhezustand, ordnungsgemäß funktioniert oder neu starten, ohne eine erzwungene Zurücksetzen des USB-Hostcontroller.

*Hinweise zum Entwurf*

Zurückgesetzt werden, der gesamte USB-Host Controller Ergebnisse deutlich mehr Zeit, die für alle USB-Geräte nach dem System fortsetzen, da es möglicherweise nur ein Gerät bei Adresse 0 zu einem Zeitpunkt verfügbar ist, hat diese Enumeration für alle USB-Geräte auf dem Bus serialisiert werden soll. Wir haben auch gesehen zurücksetzen den Hostcontroller einen ungültigen SE1 Signal Status auf einige Hostcontroller dazu führen, dass kann die einige USB-Geräte hängen oder drop aus dem Bus wiederum verursachen. Darüber hinaus können nicht Geräte alle privaten Status über dem Standbymodus fortsetzen verwalten, wie diesen Status auf Zurücksetzen verloren.

### <a name="devicebuscontrollerusbcontrollerpreservedevicestateafterdisableenable"></a>Device.BusController.UsbController.PreserveDeviceStateAfterDisableEnable

*USB-Controller muss beibehalten Gerätestatus nach dem deaktivieren und wieder zu aktivieren.*

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

Wenn ein USB-Controller deaktiviert ist, und klicken Sie dann erneut aktiviert, müssen alle Geräte, die an den Controller angeschlossen waren, bevor der USB-Controller deaktiviert wurde werden vorhanden, nachdem Sie der USB-Controller wieder aktiviert werden.

### <a name="devicebuscontrollerusbcontrollerusbifcertification"></a>Device.BusController.UsbController.UsbifCertification

*USB-Hostcontroller ist USB, WENN zertifiziert.*

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

USB-Hostcontroller müssen übergeben (Sofern es USB-Implementierer Forum) zu testen. Weitere Informationen hierzu finden Sie in den folgenden Link:

-   <https://msdn.Microsoft.com/en-us/library/Windows/Hardware/dn434058.aspx>

USB-Typ-C PD Silicon (z. B. PD Controller) muss der Version 1.1 der Spezifikation USB-Typ-C oder höher und Version 2.0 v1. 1 der Spezifikation PD oder höher implementieren und zertifiziert werden müssen, entsprechend der USB-IF des USB-C Produkt Matrix testen.

Hinweis: Seit USB-WENN derzeit nicht Controller für Windows auf ARM-Systemen Zertifizierung ist, sind die Fenster auf ARM-Domänencontrollern von benötigen zum Abrufen des vollständigen USB ausgenommen-IF-Zertifizierung. Stattdessen werden die WoA Controller erwartet, dass alle Windows Hardwarezertifizierung Tests übergeben, darunter-Ereignisdienst, Schleifen und Register-Tests, die als Teil des USB ausführen möchten-IF-Zertifizierung.

### <a name="devicebuscontrollerusbcontrollerusbtypecaltmodecertification"></a>Device.BusController.UsbController.UsbTypeCAltModeCertification

*USB-Typ-C alternativen Modus Subsysteme werden mit ihren jeweiligen Organisationen zertifiziert.*

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

Wenn der USB-Typ-C PD Silicon (z. B. PD Controller) unterstützt eine alternative Modus Standard- und die Branche-Gruppe, besitzt, dass Standard eine entsprechende Zertifizierung verfügt, muss den Silicon abrufen, Zertifizierung, zusätzlich zur USB-IF-Zertifizierung.

Beispielsweise wenn USB-Typ-C PD Silicon DisplayPort alternativen Modus zusätzlich zu USB und PD unterstützt, klicken Sie dann, Silicon muss werden von zertifiziert VESA für diese Funktionalität DisplayPort außerdem an den USB-IF USB und PD-Funktionalität.

Zertifizierung für herstellerspezifische alternative Modi ist nicht erforderlich.

### <a name="devicebuscontrollerusbcontrollerusbtypecucm"></a>Device.BusController.UsbController.UsbTypeCUCM

*USB-Typ-C-Subsysteme unterstützen UCM*

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

USB-Typ-C PD Silicon (z. B. PD Controller), die auf einem Windows-10-System ausgeführt und nicht zu UCSI implementieren muss im Lieferumfang einer 3<sup>rd</sup>-Party UCMCx Client Treiber. 3<sup>rd</sup>-Party UCMCx Clienttreiber müssen gemäß den Anweisungen in den folgenden MSDN-Dokumentationen implementiert werden:

-   <https://msdn.microsoft.com/en-us/library/windows/hardware/mt188011.aspx>.

UCMCx-Client-Treiber ist erforderlich, der die folgenden APIs implementieren:

 - UcmInitializeDevice

 - UcmConnectorCreate

 - UcmConnectorTypeCAttach

 - UcmConnectorTypeCDetach

 - UcmConnectorTypeCCurrentAdChanged

 - UcmConnectorChargingStateChanged

Wenn das System oder Controller Stromversorgung unterstützt, gelten die folgenden zusätzlichen Anforderungen:

 - UcmConnectorPowerDirectionChanged

 - UcmConnectorPdSourceCaps

 - UcmConnectorPdPartnerSourceCaps

 - UcmConnectorPdConnectionStateChanged

Wenn das System oder Controller dual Rolle Ports verfügbar macht, gelten die folgenden zusätzlichen Anforderungen:

 - UcmConnectorDataDirectionChanged

### <a name="devicebuscontrollerusbcontrollerusbtypecucsi"></a>Device.BusController.UsbController.UsbTypeCUCSI

*USB-Typ-C Subsysteme, die UCSI unterstützen implementieren korrekt*

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

USB-Typ-C PD Silicon (z. B. PD Controller), die auf Windows 10 ausgeführt wird und seine Zustandsautomat PD/USB-Typ-C in einem eingebetteten Controller implementiert muss implementieren UCSI v1. 0 (oder höher). Darüber hinaus müssen sie die folgenden optionalen Features aus UCSI Spec implementieren.

*Befehle*

-   ERSTE\_ALTERNATIVE\_MODI

-   ERSTE\_CAM\_UNTERSTÜTZTE

-   ERSTE\_g.

-   LEGEN Sie\_BENACHRICHTIGUNG\_AKTIVIEREN

    -   Das System oder Controller muss die folgenden Benachrichtigungen innerhalb dieses Befehls unterstützen:

        -   Anbieter unterstützten Funktionen ändern

        -   Ausgehandelte Power Änderung

-   ERSTE\_CONNECTOR\_STATUS

    -   Das System oder Controller muss die folgenden Connector Statusänderungen innerhalb dieses Befehls unterstützen:

        -   Unterstützte Anbieter Funktionen ändern

        -   Ausgehandelte Power Änderung

<!-- -->

-   Die System- oder Controller muss folgende Feld in GET unterstützen\_CONNECTOR\_STATUS Status Struktur

    -   Grund der Anbieter Funktionen begrenzt

### <a name="devicebuscontrollerusbcontrollertestedusingmicrosoftusbstack"></a>Device.BusController.UsbController.TestedUsingMicrosoftUsbStack

*xHCI Domänencontroller müssen mit Microsofts xHCI Stack installiert getestet werden.*

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

Erweiterbare Host Controller Interface (xHCI) Controller müssen mit Microsofts xHCI Stapel auf einem Windows-System installiert und aktiviert getestet werden. Unterstützung für alle Typen von USB-Übertragung (ISoch Interrupt und Bulk) wird geprüft werden, um grundlegende Kompatibilität sicherzustellen.

### <a name="devicebuscontrollerusbcontrollerxhciac64bit"></a>Device.BusController.UsbController.XhciAc64Bit

*xHCI Controller müssen das AC64-Bit im HCCPARAMS Register auf 1 festgelegt.*

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

xHCI Controller müssen das AC64-Bit im Register HCCPARAMS 1 gemäß der Spezifikation xHCI Abschnitt 5.3.6 festgelegt werden.
Aus diesem Grund muss der Controller unterstützen:

-   64-Bit-Adressierung, beschrieben im Abschnitt 5.3.6

-   Registrieren von 64-Bit-Access, im Abschnitt 5.1 beschrieben

*Hinweise zum Entwurf*: Suchen nach AC64 festzulegende ist eine einfache Kontrollkästchen in der Compliance-Treiber registrieren.
Um 64-Bit-Adressierung zu testen, müssen wir erfordern des Benutzers WLK Client-System mindestens 6 GB RAM verfügen.  Der Test wird MmAllocateContiguousMemorySpecifyCache verwenden, um physischen Speicher über 4 GB abzurufen.  Es wird auf irgendeine Weise überprüfen, ob der Controller diese Arbeitsspeicher Bereich zugreifen kann.
Der Test versucht Schreiben einer oder weitere Register, die mit einer 64-Bit-Access registrieren und Lesebereich wieder mit 64-Bit-registrieren Zugriff, um zu bestätigen, dass Register ordnungsgemäß aktualisiert werden.  Ein Beispiel für eine angemessene Register zu testen ist: "**-Ereignis Ring Segment Tabelle Base Adresse registrieren (ERSTBA)**" (Abschnitt 5.5.2.3.2).

Wenn AC64 nicht festgelegt ist, ist nichts zu testen.

### <a name="devicebuscontrollerusbcontrollerxhciaddincardsmapportsconsistently"></a>Device.BusController.UsbController.XhciAddInCardsMapPortsConsistently

*xHCI-add-in-Karten müssen konsistent USB 3.0 und USB 2.0-Anschlüsse zuordnen.*

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

Konsistente USB 2.0- und 3.0 USB-Anschluss Zuordnung ist erforderlich, die das Betriebssystem effektiv verwalten die Ports zu unterstützen. 

Hinweis: Diese Anforderung gilt nur für Add-in-Karten, da die Zuordnung für integrierte xHCI Controller über Advanced Configuration and Power Interface (ACPI) ausgeführt werden soll. Weitere Informationen finden Sie unter die SYSFUND 226-Anforderung.

Erweiterbare Host Controller Interface (xHCI)-Add-in-Karten (, in dem "Add-In-Karte" ist definiert als eine Karte, die nicht in die Hauptplatine integriert ist), die Komplexität der dieser Anforderung erheblich variiert, je nachdem, ob die Karte-Add-in alle internen Hubs (integriert oder eingebetteten) enthält.

Wenn keine interne Hubs vorhanden sind, muss dann der Port-Nummerierung gemäß xHCI v1.x Spezifikation korrelieren. Die zweite mit Sekunde usw. muss d. h., der erste 3.0 USB-Anschluss an den gleichen Konnektor als zuerst 2.0-Port verbunden. Wenn der USB 2.0-Ports liegen im Bereich nummerierten 1 und 2 und den USB-3.0 Ports liegen im Bereich nummerierten 3 und 4, beispielsweise Ports 1 und 3 müssen an den gleichen Konnektor zuordnen, und 2 und 4 Ports müssen an den gleichen Konnektor zuordnen. Weitere Informationen finden Sie unter xHCI v1.x-Spezifikation, 4.24.2.1 und 4.24.2.2 Abschnitte. Wenn der Host alle internen Hubs nicht vorhanden ist, kann der restliche Text über diese Anforderung ignoriert werden.

Jedoch ist interne Hubs (integriert oder eingebettet) vorhanden sind, die Anforderung komplizierter. Beachten Sie, dass eigentlich XHCI Spezifikation keine solche Hubs für add-in-Karten zulässt, da die Zuordnungsinformationen Port kann nicht die Software über ACPI mitgeteilt werden. Aber über diese Anforderung wir solche Hubs zulassen, und die erforderliche Port-Zuordnung definieren. Allerdings dieser Mechanismus weist einige Nachteile, und lässt nicht beliebige Konfigurationen, die für integrierte Controller beim von ACPI beschrieben zulässig sind.

Für Add-in-Karten möglicherweise xHCI Hostcontroller "integrierte Hubs" und/oder "eingebettete Hubs" implementieren, wie in xHCI Spezifikation 4.24.2.1 und 4.24.2.2 definiert.  Eingebettete Hubs müssen nicht auf der Hauptplatine wird beschränkt sein.  Es gelten jedoch die folgenden Nachteile:

-   Eingebettete Hubs der add-in-Karten muss 3.0 USB-Hubs (diese Einschränkung ist für das Szenario dieser Anforderung eindeutig und nicht Teil der Spezifikation xHCI).

-   Eine Add-In-Karte kann höchstens 1 integrierten Hub haben.

-   Weist eine Add-In-Karte einen integrierten Hub, benötigen sie nur 1 USB2 Protokollport auf dem Stammhub.  Dieser Port ist der Port, an den integrierten Hub angeschlossen.

-   Eine xHCI-Add-in-Karte, die implementiert einen integrierten Hub muss die integrierte Hub implementiert (IHI) in der USB 2.0-xHCI unterstützt Protokoll Funktion Struktur auf "1" für den Stamm Hub Port verbunden, um einen integrierten Hub bit festgelegt (siehe Abschnitt 7.2.2.1.3.2 der xHCI-Spezifikation).

-   Alle integriert oder eingebetteten Hubs müssen in ihrer übergeordneten Ports nicht entfernbar markiert werden.

Die Implementierung der integrierten Hubs bestimmt die externe Ports für den Controller.  Externe Ports sind ein Konzept im Abschnitt 4.24.2 der xHCI-Spezifikation zum Order-Ports definiert, damit sie die Connectors zugeordnet werden können.  In allen Fällen lassen *n* USB2 Protokoll externe Ports von 1 bis *n*und *m* USB3 Protokoll externe Ports nummeriert *n*+ 1 bis *n*vorhanden sein+*m*.

 
Externe Portnummern werden die folgenden Eigenschaften (nicht in der Spezifikation für xHCI definiert) erfüllen zugewiesen.  Beachten Sie, dass integrierte Hubs USB 2.0-Hubs sein müssen.

-   Wenn die xHCI einen integrierten Hub implementiert wird, ist *n*die Anzahl der USB2 Protokoll externe Ports, die Anzahl der downstream internetbasierte Ports auf dem Hub für integrierte gleich.

-   Andernfalls ist *n* die Anzahl der downstream internetbasierte USB2 Protokollports auf dem Stammhub gleich.

-   *m*, die Anzahl der USB3 Protokoll externe Ports, entspricht die Anzahl der downstream internetbasierte USB3 Protokollports auf den Root-Hub an.

-   Zahlen von zuweisen externe Ports so, dass externe Ports 1 bis *n* USB2 Protokollports und externe Ports *n*+ 1 bis *n*+*m* USB3 Protokoll externe Ports sind und die Reihenfolge Ports innerhalb jedes Protokoll beibehalten wird.

 
**Wenn eingebettete Hub(s) nicht vorhanden sind:** Die USB2 Protokoll externe Ports und USB3 Protokoll externe Ports müssen auf-Konnektoren mithilfe der "Default" Zuordnung beschrieben in Abschnitt 4.24.2.2 der Spezifikation xHCI unter der Überschrift "Wenn ein Embedded-Hub nicht implementiert ist" zugeordnet werden.

**Wenn eingebettete Hub(s) vorhanden sind:** Der eingebettete Hubs muss 3.0 USB-Hubs.  So ermitteln Sie zunächst die Zuordnung Connector wie wäre es ohne alle eingebetteten Hubs, verwenden die Zuordnung von "Default" aus der Spezifikation xHCI Abschnitt 4.24.2.2.  Für jedes eingebettete-Hub müssen beide Upstream-Ports an den gleichen Konnektor verbunden sein.  Embedded Hubs downstream-Ports Zuordnung auf neue Connectors auf die gleiche Weise wie die Ports des einen 3.0 USB-Hub nicht eingebettet.

**Connectors nicht verfügbar gemacht:** In den Hostcontroller eingebettete Geräte müssen in ihrer übergeordneten Ports nicht entfernbar markiert werden.  Wenn gemäß der Zuordnung Connector über eine nicht austauschbares peripherer Gerät Connector mit einem zweiten Port freigegeben ist, muss der zweite Port nicht verbunden oder verbindbaren an alle Geräte sein.  Andererseits, muss wird jeder Connector, deren Ports alle wie austauschbaren markiert sind, als einen verfügbar gemachten Connector, d. h., es werden physisch verbindbaren.

Beachten Sie, dass wenn keine ACPI Informationen vorhanden ist, ein Root-Hub ein eingebettetes USB2 Gerät und einen integrierten USB2 Hub ist nicht möglich; embedded-Gerät muss stattdessen die integrierte Hub zugeordnet werden.

### <a name="devicebuscontrollerusbcontrollerxhciaddincardsreportinternaldevices"></a>Device.BusController.UsbController.XhciAddInCardsReportInternalDevices

*xHCI Controller-add-in-Karten müssen intern angeschlossene Geräte ordnungsgemäß gemeldet.*

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

Erweiterbare Host Controller Interface (xHCI) Controller müssen intern angeschlossene Geräte anzugeben, indem das Gerät austauschbaren (DR) Bit im Register PORTSC 1 für jeden Port, der ein intern angeschlossenen Gerät verfügt. Dies gilt für Domänencontroller, die nicht ACPI Informationen verfügen. Weitere Informationen finden Sie im Abschnitt 5.4.8 von der xHCI Spezifikation.
 

-   Diese Anforderung wird verhindert, dass das Betriebssystem nicht austauschbare Geräte als entfernbar kennzeichnen.

-   Add-in-Karten sind als Hostcontroller definiert, die nicht in die Hauptplatine integriert sind.

*Hinweise zum Entwurf*

Hinweis: Diese Anforderung gilt nur für Add-in-Karten, da die Zuordnung für integrierte xHCI Controller über Advanced Configuration and Power Interface (ACPI) ausgeführt werden soll.

### <a name="devicebuscontrollerusbcontrollerxhcisupportdebuggingonallexposedports"></a>Device.BusController.UsbController.XhciSupportDebuggingOnAllExposedPorts

*xHCI Domänencontroller müssen USB-Debuggen auf alle verfügbar gemachten Ports unterstützen.*

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

Erweiterbare Host Controller Interface (xHCI) Hostcontroller befinden sich auf alle Ports Debug-fähige. Ports, die nicht entfernbar Geräte angeschlossen eingebetteten müssen nicht Bericht Debug-Funktion.
 

-   USB-debugging ist in Abschnitt 7.6 der xHCI-Spezifikation definiert.  

-   Dies gilt nicht für add-in-Karte Hostcontroller. 

### <a name="devicebuscontrollerusbcontrollerxhcisupportmsimsixinterrupts"></a>Device.BusController.UsbController.XhciSupportMsiMsixInterrupts

*xHCI Domänencontroller müssen MSI unterstützen und/oder MSI-X unterbrochen wird.*

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

Erweiterbare Host Controller Interface (xHCI)-Domänencontroller unterstützen Nachricht signalisiert Interrupts (MSI) und MSI-X Interrupts wie im Abschnitt 6.8 der lokalen PCI-Bus-Spezifikation, Version 3.0 und im Abschnitt 5.2.6 der xHCI Spezifikation definiert.

### <a name="devicebuscontrollerusbcontrollerxhcisupportsminimum31streams"></a>Device.BusController.UsbController.XhciSupportsMinimum31Streams

*xHCI Domänencontroller müssen mindestens 31 primären Datenströme pro Endpunkt unterstützen.*

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

Finden Sie in der eXtensible Host Controller Interface-Spezifikation, Abschnitt 4.12.2.

Dies ist für die MaxPSASize in der HCCPARAMS mit mindestens 4 festgelegt werden soll, ultimate Datenübertragungsrate mit UAS-Geräte zu aktivieren.

Basierend auf USB-Attached SCSI-Protokoll (UASP) Speichergeräten nutzt Streams um schnellere Datenübertragungsrate, wie Sie Daten zu erreichen.  Um die beste Erfahrung mit diesen Geräten zu aktivieren, müssen alle xHCI Controller mindestens 31 primären Streams unterstützen.

### <a name="devicebuscontrollerusbcontrollerxhcisupportsruntimepowermanagement"></a>Device.BusController.UsbController.XhciSupportsRuntimePowerManagement

*USB-Hostcontroller für xHCI müssen Runtime Power Management einschließlich unterstützen, wenn implementiert, Common Language Runtime Remoteaktivierung.*

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

Alle USB-Hostcontroller xHCI müssen Runtime Power Management nach Bedarf durch die eXtensible Host Controller Interface-Spezifikation, Version 1.0, Abschnitt 4.15 unterstützen.

Common Language Runtime ist definiert als arbeiten Systemstatus (S0), einschließlich verbunden Standby untergeordnete Status S0, wenn der Controller auf einem System getestet wird, die Standbymodus verbunden unterstützt.

Power-Verwaltung von den Hostcontroller umfasst Software initiierte im Leerlauf Herunterfahren (Controller Energiesparmodus wie D3), Software initiierte Power bis, und (optional) Signale Remoteaktivierung Hardware initiiert hat.

Wenn der Controller xHCI zur Unterstützung von Common Language Runtime Remoteaktivierung Signale gemeldet wird, muss sich selbst erfolgreich auf eines der folgenden Ereignisse reaktivieren sein: A) alle Port erkennen Gerät Remoteaktivierung Signale B) jeden beliebigen port erkennen, eine Verbindung herstellen, Verbindung trennen oder Überspannungsschutz, wenn die entsprechenden PORTSC Remoteaktivierung Xxx Bit auf "1" festgelegt ist.
Weitere Informationen finden Sie unter Abschnitt 4.15 der xHCI-Spezifikation.

So melden Sie, ob der Controller Runtime Remoteaktivierung Signale unterstützt:
- Für Add-in-Controller muss der Controller PCI-Konfigurationsbereich meldet genau, ob der Controller über PME reaktiviert kann.  Hinweis: meldet, dass der Controller unterstützt über PME reaktiviert impliziert, dass der Controller kann sowohl erfolgreich PCI-Aktivierung zur Laufzeit durchführen und erfolgreich das System von einem System Energiesparmodus, gemäß der entsprechenden PCI-Spezifikation aktiviert.
- Für integrierte Controller, ACPI \_S0W-Objekt muss melden, ob der Controller Runtime Remoteaktivierung Signale kann.

### <a name="devicebuscontrollerusbcontrollerxhciversioncompliant"></a>Device.BusController.UsbController.XhciVersionCompliant

*USB-3.0-Domänencontroller sind XHCI Version kompatibel.*

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

3.0 USB-Controller Extensible Host Controller Interface (xHCI) Spezifikation Version 1.0 entsprechen und USB-IF-Fehlern, die von der USB freigegeben sind-IF. 2019 Microsoft wird auf den Text des dieser Anforderung an den Übergang "USB 3.1 Controller Extensible Host Controller Interface (xHCI) Spezifikation Version 1.1 entsprechen und alle USB-IF-Fehlern, die von der USB freigegeben sind-IF. “. Microsoft empfiehlt die Übergang zu wird vor dem Datum 2019 kompatibel mit der Spezifikation, Version 1.1.

