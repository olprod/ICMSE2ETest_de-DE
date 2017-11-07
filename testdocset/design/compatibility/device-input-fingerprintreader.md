---
title: Device.Input.FingerPrintReader
Description: "Allgemeine Anforderungen für biometrische Fingerabdruckleser."
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 557aa6c2868514606ea77e6c5827c46e4b1634bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.FingerPrintReader
 - [Device.Input.FingerPrintReader](#device.input.fingerprintreader)
-->

<a name="device.input.fingerprintreader"></a>
##Device.Input.FingerPrintReader 

### <a name="deviceinputfingerprintreaderbase"></a>Device.Input.FingerPrintReader.Base

*Biometrisches Fingerabdruck Reader allgemeinen Anforderungen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Biometrische Fingerabdruckleser certified unter dieses Programm müssen über die Windows Biometric Framework (WBF) verfügbar gemacht werden. WBF Plug-in-Komponenten müssen alle Einstiegspunkte zu implementieren und entsprechen die WBF-Plug-in-Schnittstellen, die auf MSDN ([*http://msdn.microsoft.com/library/dd401553.aspx*](http://msdn.microsoft.com/library/dd401553.aspx)) dokumentiert sind.

Die allgemeinen folgenden Kriterien müssen erfüllt sein:

<html>
    <ul>
        <li><p>Treiberpakets muss es sich um einen WBDI Treiber und eine Kombination von Plug-In-Adapter enthalten.</p></li>
        <li><p>Geräte, die im erweiterten Modus ausgeführt werden, können einen zusammengesetzten Adapter implementieren. Ein zusammengesetzter Adapter möglicherweise eine proprietäre Sensor, Modul, und Datenbank-Adapter oder eine beliebige Kombination von Adapter enthalten.</p></li>
        <li><p>Die WBDI Treiber und Plug-in-Komponenten müssen keine Schadsoftware wie trojanischen Pferden oder backdoor Software enthalten.</p></li>
    </ul>
    <p>Plug-in-Komponenten müssen keine Schadsoftware wie trojanischen Pferden oder backdoor Software enthalten.</p>
    <p>Die folgende Tabelle enthält die hardwareanforderungen für Fingerabdruck Sensoren.</p>
    <table>
        <thead>
            <tr class="header">
                <th>Anforderung</th>
                <th colspan="2">Begründung/Notizen</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Sensortyp</td>
                <td>Empfohlen Wenn implementiert Touch</td>
                <td>Touch Sensortyp ist die bevorzugte "Option Compare", führen Sie eine streifbewegung Sensor. Aufgrund der Art, Platzierung und feste Ausrichtung von führen Sie eine streifbewegung Sensoren vor allem auf Geräten, die können mehrere Ausrichtung (beispielsweise Tablets, die im Querformat und Hochformat Modus funktionieren können) haben, führen sie ergonomischen Herausforderungen für den Benutzer, die Fehler erfasst eine genaue Fingerabdruck, wodurch die Notwendigkeit für mehrere Kundenkarte führen können.</td>
            </tr>
            <tr class="even">
                <td>Des Energieverbrauchs</td>
                <td>Betrieb (während der Aufnahme) 100mW</td>
                <td>Erforderlich, damit verbundene Standby-Geräte und für andere Benutzer empfohlen.</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>Wenn Sie der Fingerabdruckleser nicht Fingerabdruck Bilder unabhängig von aufzeichnen ist, ist das System selbst in den Energiesparmodus, Status oder nicht - 1mW</td>
                <td>Erforderlich, damit verbunden Standby-Geräte und für andere Benutzer empfohlen.</td>
            </tr>
            <tr class="even">
                <td>Leistung</td>
                <td colspan="2">Empfohlene &lt;1 % FRR @ 0,01 % FERNER gemäß Fingerabdruck Sensor-Spezifikation</td>

            </tr>
            <tr class="odd">
                <td>Liveness Detection</td>
                <td colspan="2">Recommended to be able to provide a minimum of one of the anti-spoofing measures based on the fingerprint sensor specification</td>

            </tr>
            <tr class="even">
                <td>WBF Compliant with HCK</td>
                <td colspan="2">Yes</td>

            </tr>
        </tbody>
    </table>
    <p><em>Design Notes: </em></p>
    <p>Biometric devices measure an unchanging physical characteristic to uniquely identify an individual. Fingerprints are one of the most common biometric characteristic measured. Beginning with Windows 7, a new set of components, the Windows Biometric Framework, provides support for fingerprint biometric devices. These components, created using the Windows Biometric Framework API, can perform the following tasks:</p>
    <ul>
        <li><p>Capture biometric samples and use them to create a template.</p></li>
        <li><p>Securely save and retrieve biometric templates.</p></li>
        <li><p>Map each template to a unique identifier such as a GUID (globally unique identifier) or SID (system identifier).</p></li>
        <li><p>Enroll new biometric templates.</p></li>
    </ul>
    <p>For more complete information about WBF and its components, see &quot;Introduction to the Windows Biometric Framework (WBF),&quot; a white paper, at <em><a href="http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx" class="uri">http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx</a>.</em></p>
</html>

### <a name="deviceinputfingerprintreaderextensions"></a>Device.Input.FingerPrintReader.Extensions

*Vom Hersteller bereitgestellte Treiber oder andere Erweiterungskomponenten müssen andere Erweiterungskomponenten nicht umgebrochen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Treiber und Adapter-Plug-ins, die das Windows-Biometrieframework erweitern müssen nicht andere Treiber oder Adapter-Plug-ins umbrochen, außer wenn die Methode explizit der Dokumentation-Komponente von Microsoft bereitgestellten zulässig ist.

### <a name="deviceinputfingerprintreadermanagementapps"></a>Device.Input.FingerPrintReader.ManagementApps

*Biometrisches Fingerabdruck Reader Management-Anwendungen*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

<html>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>ARM-Geräte</th>
                <th>X86/X64 Geräte</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Registrierung Erfahrung (FMA)</td>
                <td>Nicht zulässig. Eine Posteingang Registrierung wünschen Benutzer Einstellungsseite integriert ist verfügbar.</td>
                <td>
                    <p>Nicht empfohlen. Die Registrierung Erfahrung Posteingang bereitgestellt und mit der Seite benutzereinstellungen integriert. MÖGLICHERWEISE eine benutzerdefinierte Registrierung Erfahrung im Paket WBF enthalten und auf dem System installierte jedoch es in Einstellungsseite für Benutzer oder -Systemsteuerung nicht integriert wird.</p>
                    <p>Benutzerdefinierte Registrierung Erfahrung ist nicht zulässig, nicht der Domäne Benutzer zu registrieren.</p>
                </td>
            </tr>
        </tbody>
    </table>
    <p><strong>Ausnahmen</strong>
    <p>Geräte für die Verwendung durch die Benutzer vorgesehen benötigen keine 3. Partei FMA installiert. 3. Partei FMAs können installiert und aktiviert auf Windows-Geräten Ziel in Unternehmen (Enterprise und kleine und mittlere Unternehmen) sein. In diesen Fällen sollten deutlich der Benutzer benachrichtigt werden, wenn Core Posteingang Erfahrungen durch die Verwendung der 3. Partei FMA während der Registrierung beeinträchtigt sein werden.</p>
<html>

### <a name="deviceinputfingerprintreadersensorenginedb"></a>Device.Input.FingerPrintReader.SensorEngineDB

*Fingerabdruck-Reader Sensor, Modul und Speicher-Plug-In-Anforderung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

-   Alle Einstiegspunkte für die Schnittstelle implementiert werden müssen, und jedes Element muss die Definition der jeweiligen Adapters Plug-in-Schnittstelle entsprechen.

-   Plug-in-Komponenten müssen sequenzierten Aufruf des IIS ihre Schnittstellen unterstützen, die aus allen der obersten Ebene Windows biometrische Framework (WBF) APIs aufrufen.

-   Die Reihenfolge der WBF API-Aufrufe wird von der Anmeldeinformationsanbieter WBF für die Windows-Anmeldung muss in 1,5 Sekunden oder weniger abgearbeitet werden.

-   Alle Adapter digital signiert werden, wie in der Windows-Biometrieframework beschrieben: Code Signing Richtlinien Whitepaper unter [*http://msdn.microsoft.com/library/windows/hardware/gg463093.aspx*](http://msdn.microsoft.com/library/windows/hardware/gg463093.aspx).

-   Der Adapter muss unter Application Verifier ausgeführt, ohne Fehler generieren.

Ein Paket kann mehrere Geräte unterstützt, aber die Zertifizierung Kriterien für jede der unterstützten Fingerabdruckleser muss separat übergeben. Eine separate Übermittlung muss für jedes unterstützte Gerät vorgenommen werden.

| Netzwerkadapteranforderungen für | Hinweise                                                                                                                                             |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Modul adapter       | Erforderlich, wenn das Gerät ein erweitert wird, die auf Gerät entsprechen kann.                                                                        |
| Storage-adapter      | Auf den Adapter für Posteingang wird empfohlen, es sei denn, es ist eine bestimmte erforderlich Speicheradapter benutzerdefinierte wie für erweiterte Sensoren aufnehmen. |
| Sensor adapter       | Für Posteingang Sensor Adapter Relying wird empfohlen, es sei denn, die einer bestimmten müssen Sie einen benutzerdefinierten Sensor Adapter aufnehmen.                                |

### <a name="deviceinputfingerprintreaderwbdi"></a>Device.Input.FingerPrintReader.WBDI

*Biometrisches Fingerabdruck Reader WBDI Treiber-Anforderung*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>10 Windows Mobile ARM</p>
<p>10 Windows Mobile x86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Treiber Windows biometrische Treiber-Schnittstelle (WBDI) müssen die folgenden Kriterien erfüllen:

-   Alle obligatorisch IOCTLs müssen vollständig implementiert und WBDI Funktionsspezifikation.

-   Wenn ein optionales IOCTL implementiert ist, muss der WBDI-Spezifikation entsprechen.

-   Der Treiber WBDI muss biometrische IOCTL Abfolge von unterstützen.

-   Wenn der biometrische Fingerabdruckleser kein Plug & Play-Gerät ist, müssen sie hinzukommen und weggehen Ereignisse entsprechend den Empfehlungen in der Spezifikation WBDI erstellen.

-   Das Installationsprogramm WBDI INF-Datei muss richten Sie Plug-in zugehörigen Komponenten und Fingerabdruck-Management-Anwendungen, die in dem Paket enthalten sind.

Richtlinien in dieser Anforderung gelten gleichermaßen gut für die-Kernel- und Benutzermodus-Treiber. Folgendes muss unterstützt werden:

-   Vorwärts- und Kompatibilität. Treiber benötigen einen Mechanismus, der verschiedene Versionen von Komponenten im Benutzermodus und im Kernelmodus bestimmt. Wenn zwei Versionen der gleiche Treiber auf dem Computer installiert wurden, muss die Kernel-Komponente Kommunikation mit den richtigen Treiber ermitteln. In Remoting-Szenarien kann auch mit einem einzelnen Treiber der Konflikt auftreten.

Die folgenden Elemente darf nicht verwendet werden:

-   Out-of-Band-Kommunikation. Da die im Benutzermodus und im Kernelmodus-Treiber auf einem PC ausgeführt werden, können sie über verschiedene aus dem e/a-Manager APIs Kanäle zusammen gekoppelt. Ziel ist es, stellen Sie sicher, dass Treiber keine impliziten oder expliziten Out-of-Band-Kommunikation.

Hier sind einige Beispiele, die Terminaldienste Umleitung verhindern würden:

-   Freigegebener Speicher muss nicht direkt zwischen Benutzermodus-Anwendungen und Benutzermodus oder Kernelmodus-Treiber verwendet werden. Für jedes Datenelement gesendet und empfangen werden muss eine entsprechende e/a-Anforderung vorhanden sein. Freigeben des Speichers mithilfe einer Datei zugeordneten oder durch gesperrte Seiten durch direkte e/a-aufrufen.

-   Registrierung Kommunikation (d. h., sämtlichen Registrierungsschlüsseln, die vom Benutzermodus-Treiber festlegen und Lesen von Kernelmodus-Treiber oder umgekehrt werden). Es ist problematisch, wenn eine Anwendung auf dem Server ausgeführt wird und die Treiber auf dem Client geladen werden, da die Registrierung auf dem Server, jedoch nicht auf dem Client festgelegt ist.

-   Kernelobjekte (alle Kernel-Objekthandles in e/a-Puffer, z. B. Handles Ereignissen oder Semaphoren übergeben).

-   Datenzeiger (Übergabe von Datenzeiger in e/a-Puffer). Beispielsweise kann ein Treiber versuchen Sie, eine verknüpfte Liste oder anderen komplizierte Datenstruktur aus dem Kernel gelesen.

-   Inkompatibilität zwischen der 32-Bit- und 64-Bit-Plattformen Implementierungen der e/a-Anforderung Packet (IRP) Anforderungen (Felder in den Datenstrukturen, die unterschiedlich, je nach der Bitness kompiliert werden). Inkompatibilität der Strukturen auf der Grundlage Bitness Ergebnisse in anderen Offsets und Daten Größe für diese Strukturen. Die Daten werden bei einem Terminaldienste-Client und der Server nicht die gleiche Plattform sind nicht richtig interpretiert.

-   Eine exakte Timing Erwartung zu wie schnell Kerneltreiber Abhängigkeit antwortet. Da Treiber Remoting über das Netzwerk sind, wird die Antwort von der Hardware zusätzlicher Latenz hinzugefügt. Dass Wartezeit von 10 ms auf mehrere Sekunden reichen kann. Ein möglicher Grund kann langsame oder Paketverlusten handeln. Ein Treiber für eine Antwort programmiert ist, die in niedriger als üblichen Netzwerklatenz kommt das Remoting schlägt fehl.

    Festlegen einer Zugriffssteuerungsliste (ACL) oder sonstige Laufzeitfehler Sicherheit, die jeder Anwendung öffnen Gerätetreiber verhindern würden. Beispielsweise ist ein Treiber zulässig, Anrufe nur von bestimmten Dienst annehmen. Da alle Anrufe auf einem TS-Client PC Sicherheitskontext des Prozesses Client Remoting fertig sind, können sie ein Fehler auftritt.

**Hinweise zum Entwurf** 

Biometrische Geräte gemessen ein unveränderlicher physischen Merkmal, um eine einzelne Person eindeutig zu identifizieren. Fingerabdrücke sind die am häufigsten verwendeten biometrischen Merkmal gemessen. Beginnend mit Windows 7, einen neuen Satz von Komponenten, die Windows Biometric Framework (WBF), bietet Unterstützung für Fingerabdruck biometrische Geräte. Diese Komponenten, die mit der API WBF erstellt können folgenden Aufgaben ausführen:

-   Erfassen biometrische Beispiele und nutzt sie dazu um eine Vorlage zu erstellen.

-   Sicher speichern und Abrufen von biometrische Vorlagen.

-   Ordnen Sie jede Vorlage ein eindeutiger Bezeichner, wie etwa eine GUID (globally unique Identifier) oder SID (System Identifier).

-   Registrieren Sie neue biometrische Vorlagen.

-   Damit ein Gerät über WBF angezeigt werden, muss das Gerät, über einen Treiber verfügbar gemacht werden, die den Treiber WBDI als auch eine geeignete Kombination von Sensor, Modul und Datenbankkomponenten-Plug-in implementiert wird. Ausführlichere Informationen zum WBF und die zugehörigen Komponenten finden Sie unter "Einführung an der Windows biometrische Framework (WBF)," ein Whitepaper, unter [*http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx*](http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx).


