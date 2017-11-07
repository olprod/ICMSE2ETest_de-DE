---
title: Device.Portable
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 16e3a06e4ea69ee4f8e1b402484bd34a872e903e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceportable"></a>Device.Portable

 - [Device.Portable.Core](#device.portable.core)
 - [Device.Portable.DigitalCamera](#device.portable.digitalcamera)
 - [Device.Portable.DigitalVideoCamera](#device.portable.digitalvideocamera)
 - [Device.Portable.MediaPlayer](#device.portable.mediaplayer)
 - [Device.Portable.MobilePhone](#device.portable.mobilephone)

<a name="device.portable.core"></a>
## <a name="deviceportablecore"></a>Device.Portable.Core

*Core*

### <a name="deviceportablecoreaudiocodec"></a>Device.Portable.Core.AudioCodec

*Wenn ein tragbares Gerät Audioinhalte erfassen kann, muss dies mithilfe eines Formats in Windows systemintern unterstützt erfolgen.*

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

Wenn ein tragbares Gerät Audioinhalte erfassen kann, muss dies in einem Format erfolgen, die Windows systemintern versteht.

In den folgenden Tabellen stehen für die Liste der im Feld Formate, denen auf Windows gerendert wird. Dies ist nicht der vollständig unterstützte Dateiformate in Windows. Die vollständige Liste der unterstützten Formaten finden Sie unter: <http://go.microsoft.com/fwlink/?LinkID=242995&clcid=0x409>.

**Beachten Sie** , dass für ein bestimmtes Format in den folgenden Tabellen, die es nicht erforderlich ist, alle angegebenen Bitraten und Abtastrate unterstützen, es jedoch erforderlich ist, um ein Format zu unterstützen, die in den Bereichen ausgerichtet.

<html>
    <p><strong>MP4 (engl.) Audioinhalte</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="4">AAC</td>
                <td>Codec</td>
                <td>
Standard AAC AAC Profil Ebene 2 minimale (0 x 29),<br />
kompatibel mit (0 x 29, 0x2A, 0x2B, 0x2C, 0x2E, 0x2F, 0 x 30, 0x31, 0 x 32, 0 x 33)                </td>
            </tr>
            <tr class="even">
                <td>Bitrate CBR</td>
                <td>96, 128, 160, 192 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="even">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>MP3 Audio-Inhalt</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="4">MP3</td>
                <td>Codec</td>
                <td>Version1 Layer3</td>
            </tr>
            <tr class="even">
                <td>Bitrate CBR-Dateien</td>
                <td>Von 32 auf 320 Kilobit pro Sekunde (Kbit/s)</td>
            </tr>
            <tr class="odd">
                <td>Abtastrate</td>
                <td>16, 22,05, 24, 32, 44,1, 48 Kilohertz (kHz)</td>
            </tr>
            <tr class="even">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>Audioinhalte WMA</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="6">WMA-Standard</td>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="even">
                <td>Bitrate CBR-Dateien</td>
                <td>Von 32 auf 256 Kilobit pro Sekunde (Kbit/s)</td>
            </tr>
            <tr class="odd">
                <td>Durchschnittliche Bitrate VBR-Dateien</td>
                <td>Von 48 auf 160 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale Wert Bitrate VBR-Dateien</td>
                <td>256 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Abtastrate</td>
                <td>44,1 oder 48 Kilohertz (kHz)</td>
            </tr>
            <tr class="even">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
</html>
 

### <a name="deviceportablecorecustomdeviceservices"></a>Device.Portable.Core.CustomDeviceServices

*Ein tragbares Gerät, das implementiert benutzerdefinierte MTP Dienste muss die Anforderungen in der MTP Geräte Dienste Erweiterung Spezifikation definierten erfüllen.*

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

Der MTP Gerät-Erweiterung, das Media Transfer Protocol (MTP) hilft MTP Initiator, in diesem Fall Windows, suchen und Zugriff auf bestimmte Arten von Inhalt auf dem Gerät gespeicherten.  Erweiterungsmechanismen wurden definiert, die größere Flexibilität für Anwendungen bereitstellen, die bestimmte Inhaltstypen vom Gerät definierten betreffen. Diese Mechanismen bereit Erweiterbarkeit der größer als die vorhandenen Daten Code Mechanismen, die derzeit in der Media Transfer-Protokoll-Spezifikation Version 1.0 definiert.

Wenn das tragbare Gerät einen benutzerdefiniertes Gerät Dienst unterstützt, benötigen die Implementierung ein gültiges *ServiceInfo* -Dataset, ein gültiges *ServiceCapabilities* Dataset und ein gültiges *ServicePropertiesDesc* Dataset gemäß Definition in der Spezifikation für MTP Gerät Services Erweiterung. Aller erforderlichen Eigenschaften in der Spezifikation definierten müssen in den benutzerdefinierten Dienst unterstützt werden.

In der folgenden Tabelle wird eine Liste der Vorgänge, die beim Implementieren von MTP Services erforderlich sind:

| Verwendung              | Datacode MTP | Beschreibung                                                                                                                                                                               |
|------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GetServiceIDs          | 0x9301       | Diesem Vorgang gibt ein Array von ServiceIDs.                                                                                                                                            |
| GetServiceInfo         | 0x9302       | Diesem Vorgang gibt das ServiceInfo Dataset für einen Dienst zurück.                                                                                                                             |
| GetServiceCapabilities | 0x9303       | Alle Objekt-Format und -Methode Informationen zu Dateiformaten wird mithilfe des Vorgangs GetServiceCapabilities gemeldet.                                                                                |
| GetServicePropDesc     | 0x9304       | Dieser Vorgang gibt TheServicePropertyDesc Dataset für einen Dienst zurück.                                                                                                                      |
| GetServicePropList     | 0x9305       | Dieser Vorgang ist in der MTP-Spezifikation, Version 1.0 GetObjectPropList ähnelt. GetServicePropList liest Eigenschaften aus einem Dienst.                                                |
| SetServicePropList     | 0x9306       | Dieser Vorgang festgelegt ein ServiceProperty mithilfe von Dataset ServicePropList. Sie können das Schreiben von Eigenschaftswerten zu einem Dienst.                                                       |
| UpdateObjectPropList   | 0x9307       | Dieser Vorgang wird die Eigenschaftenliste für ein bestimmtes Objekt, das mit einem neuen binären Objekt aktualisiert wird. Dieser Vorgang kann verwendet werden, die binären Daten eines vorhandenen Objekts ersetzen. |
| DeleteObjectPropList   | 0x9308       | Dieser Vorgang entfernt die Eigenschaften, die in DeleteObjectPropList Dataset aus einem oder mehreren angegebenen Objekten angegeben sind.                                                        |
| DeleteServicePropList  | 0x9309       | Dieser Vorgang entfernt die Eigenschaften, die im DeleteServicePropList Dataset aus dem angegebenen Dienst angegeben sind.                                                                 |

 
Mithilfe der Vorgänge, Geräteeigenschaften usw. definiert in der MTP 1.0-Spezifikation (oder höher), und klicken Sie dann das Gerät diese Szenarien im Hinblick auf Gerät Services definieren muss und diese Dienste gemäß den Anforderungen in der MTP Gerät Services Erweiterung Spezifikation definierten unterstützen muss, wenn Szenarien, die mithilfe der Funktionen, die in der Spezifikation MTP definierten implementiert werden können nicht implementiert. Beispielsweise kann ein Media Exchange-Dienst zum Verwalten von Medien-Synchronisierung zwischen dem Initiator und Responder, die vom Standardverhalten MTP 1.0 unterstützten Funktionen ersetzt definiert werden.

Um eine benutzerdefinierte geräteupdate-Webdienst in Device Stage verfügbar machen, muss eine benutzerdefinierte Aufgabe erstellt und als Teil der Device Stage authoring Prozess definiert. Dies ist in Microsoft Device Erfahrung Development Kit beschrieben werden.

*Hinweise zum Entwurf*

-   Finden Sie in der MTP Gerät Services Erweiterung Spezifikation unter *http://msdn.microsoft.com/en-us/windows/hardware/gg463541.aspx*verfügbar.

-   Finden Sie im Microsoft Gerät Erfahrung Development Kit unter *http://msdn.microsoft.com/en-us/windows/hardware/gg463154.aspx*verfügbar.

### <a name="deviceportablecoredeviceservices"></a>Device.Portable.Core.DeviceServices

*Tragbare Geräte Support Services MTP definiert wurden, müssen diese Dienste gemäß den Anforderungen in der MTP Gerät Services für Windows Spezifikation definierten implementieren.*

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

Die MTP Gerät Dienstarchitektur ermöglicht Windows suchen und Verwenden der verschiedenen Dienste und Inhaltstypen, die sich auf einem Gerät befindet. Durch das Erstellen von Erweiterungen für das Protokoll WPD-API und MTP, Windows suchen, nutzen und interagieren mit nützlich, Inhalte und Dienste auf dem Gerät.

Persönliche Informationen (PIM) Verwaltungsdienste unterstützt:

-   Wenden Sie sich an Service
-   Kalenderdienst
-   Notes-Dienst
-   Aufgaben-Dienst

Andere unterstützte Dienste:

-   Status-Dienst
-   Hinweise Service
-   Gerät-Metadatendienst
-   Klingeltöne Service
-   SMS-Dienst

Wenn das Gerät eine oder mehrere der PIM-Dienste unterstützt, müssen sie auch eine der zwei Synchronisierungsdienste für die Daten zu synchronisieren unterstützt werden. Windows unterstützt die in-Box folgenden:

-   Sync (Aufzählung)
-   Anker-Synchronisierung

Bis zu ist, dass für das Gerät der Hersteller, um die Dienste zu wählen, der am besten geeignet.

Softwarehersteller, die zur Unterstützung von benutzerdefinierten Metadaten Device Stage-Pakete, wählen Sie sollten sicherstellen, dass die entsprechenden Vorgänge oder Geräteeigenschaften in dem Paket ordnungsgemäß verfügbar gemacht werden.

Für Dienste einen Dienst beachten Initiator zugänglich sein-bezogenen der folgende Dienst Vorgänge auch vom Gerät unterstützt werden müssen:

| Verwendung              | Datacode MTP | Beschreibung                                                                                                                                                                               |
|------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GetServiceIDs          | 0x9301       | Diesem Vorgang gibt ein Array von ServiceIDs.                                                                                                                                            |
| GetServiceInfo         | 0x9302       | Diesem Vorgang gibt das ServiceInfo Dataset für einen Dienst zurück.                                                                                                                             |
| GetServiceCapabilities | 0x9303       | Alle Objekt-Format und -Methode Informationen zu Dateiformaten wird mithilfe des Vorgangs GetServiceCapabilities gemeldet.                                                                                |
| GetServicePropDesc     | 0x9304       | Dieser Vorgang gibt TheServicePropertyDesc Dataset für einen Dienst zurück.                                                                                                                      |
| GetServicePropList     | 0x9305       | Dieser Vorgang ist in der MTP-Spezifikation, Version 1.0 GetObjectPropList ähnelt. GetServicePropList liest Eigenschaften aus einem Dienst.                                                |
| SetServicePropList     | 0x9306       | Dieser Vorgang festgelegt ein ServiceProperty mithilfe von Dataset ServicePropList. Sie können das Schreiben von Eigenschaftswerten zu einem Dienst.                                                       |
| UpdateObjectPropList   | 0x9307       | Dieser Vorgang wird die Eigenschaftenliste für ein bestimmtes Objekt, das mit einem neuen binären Objekt aktualisiert wird. Dieser Vorgang kann verwendet werden, die binären Daten eines vorhandenen Objekts ersetzen. |
| DeleteObjectPropList   | 0x9308       | Dieser Vorgang entfernt die Eigenschaften, die in DeleteObjectPropList Dataset aus einem oder mehreren angegebenen Objekten angegeben sind.                                                        |
| DeleteServicePropList  | 0x9309       | Dieser Vorgang entfernt die Eigenschaften, die in DeleteServicePropList Dataset aus dem angegebenen Dienst angegeben sind.                                                                 |

 

*Hinweise zum Entwurf*

-   Informationen zu definierten MTP Dienste finden Sie unter der MTP Gerät Dienste für Windows-Spezifikation unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463544>*.*

-   Informationen zu Service-Vorgänge und allgemeine Dienste finden Sie in der MTP Gerät Services Erweiterung Spezifikation unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463545>verfügbar.

-   Siehe auch Metadatenschema und Package-Format-Spezifikation unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463153>*.* verfügbar

### <a name="deviceportablecoremediasync"></a>Device.Portable.Core.MediaSync

*Tragbare Geräte, die Media-Inhalten zu unterstützen, müssen grundlegende Interoperabilität Anforderungen zum Übertragen von Inhalten mit einer MTP bewusst Media Player Anwendung erfolgreich auf Windows erfüllen.*

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

Ein Gerät MTP basierend muss möglicherweise übertragen von Daten zu und von einem PC mit einer Windows-basierten Anwendung, die MTP unterstützt.

**Beachten Sie** , die das Gerät Core MTP Media Behandeln von Funktionen mit einem benutzerdefinierten MTP-Dienst, und klicken Sie dann auf Interoperabilität mit Windows Media Player ersetzt nicht funktionieren wie erwartet. Geräte, die einen benutzerdefinierten Dienst implementieren benötigt funktional gleichwertig mit Core MTP Vorgänge zur Unterstützung der Übertragung von Mediendaten und Synchronisierung mit einer WPD-basierten Anwendung.

Die folgenden Anforderungen müssen erfüllt sein, bei der Interaktion mit Windows Media Player:

**Unterstützt die digitalen Medien Übertragungen vom Computer - Gerät** Das Gerät muss digitaler Medien Übertragungen, Computern über Applikationen unterstützen, die die Übertragung, wie die Erweiterung von tragbaren Gerät Shell-Namespace und die Windows Media Player zu ermöglichen.

**Unterstützt die digitalen Medien Übertragung von Computer zu Gerät-** Das Gerät muss die Übertragung von Unterstützte Medienformate vom Computer auf das Gerät mit Windows Media Player unterstützen. Das Gerät muss die Übertragung von alle Dateiformate vom Computer auf das Gerät über die Windows®-Namespace-Erweiterung unterstützen.

**Metadaten-Updates unterstützt-** Das Gerät muss die Updates auf MTP Metadaten unterstützen, nachdem der ursprüngliche Track auf das Gerät kopiert wurde. Die metadatenupdates werden mithilfe von Windows Media Player ausgeführt.

**Unterstützt die Löschung der Übertragung und Synchronisierung –** Das Gerät muss absagen von Übertragungen und Synchronisierungen unterstützen Mid Aufgabe ohne abstürzt oder hängenden des Geräts.

**Dateitypen - ordnungsgemäß identifiziert** Das Gerät muss nicht auf der Erweiterung einer Datei zum Ermitteln des Dateityps verlassen. Das Gerät können Sie das Format der MTP Objekt oder analysieren kann den Inhalt der Datei, um den Dateityp zu ermitteln.

**PROVIDE Gerät Objektmetadaten-** Wenn ein Host einen leeren Wert für Album, Künstlers oder Titel sendet, muss das Gerät anzeigen aussagekräftigen Text anstelle der leeren Metadaten und ermöglicht es dem Benutzer, den Inhalt zu erhalten, Suchen nach dem zugeordneten Feld in der Benutzeroberfläche des Geräts. Beispielsweise kann ein Gerät bei Erhalt des einen leeren Wert für Künstlers Metadaten, unbekannte Künstlers für des Künstlers verwenden. Wenn das Gerät anzeigen Genre Metadaten, klicken Sie dann unterstützt, wenn ein Host einen leeren Wert für Genre sendet, muss das Gerät anzeigen aussagekräftigen Text anstelle der leeren Metadaten und ermöglicht es dem Benutzer, den Inhalt zu erhalten, Suchen nach dem zugeordneten Feld in der Benutzeroberfläche des Geräts.

**Wiedergabeliste Transfer-** Das Gerät muss die Übertragung von manuell vom Benutzer erstellt mithilfe von Windows Media Player Wiedergabelisten unterstützen. Wenn eine manuelle Wiedergabeliste übertragen werden müssen mit Windows Media Player, die Wiedergabeliste und den Inhalt der Wiedergabeliste Verweise auf dem Gerät befinden.

Um Wiedergabelisten von Windows Media Player zu erhalten, muss ein Gerät Objektverweise unterstützen. Wenn Objektverweise unterstützt werden, müssen sie auf alle Media-Dateiformaten unterstützt. Unterstützung für Objektverweise wird angegeben, durch die Unterstützung der folgenden Befehle:

-   GetObjectReferences (0x9810)
-   SetObjectReferences (0x9811)

Das Gerät muss auch das Format AbstractAudioVideoPlaylist (0xBA05) unterstützen. Eine Wiedergabeliste wird für alle Objekte in der Wiedergabeliste als 0-Byte-Objekt mit einer Liste von Verweisen auf die Objekt-Handles gesendet.

### <a name="deviceportablecoremodelid"></a>Device.Portable.Core.ModelID

*Tragbare Geräte unterstützen möglicherweise die optionale ModelID-Eigenschaft, um die logische Gerät funktioniert in einer Multifunktionsgeräten eindeutig zu identifizieren.*

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

Plug & Play bietet Unterstützung für eine DevNode Eigenschaft mit dem Namen DEVPKEY\_Gerät\_ModelId. Dieser Schlüssel wird verwendet, um den Wert ModelID zu speichern, von dem einige Geräte in einer Klasse-gerätespezifischen oder herstellerspezifische Weise auf dem Gerät gespeichert werden.

Die ModelID umfasst logische Gerät funktioniert in einer Multifunktionsgeräten über eine interne Struktur in Windows 7 mit dem Namen anzeigen, die logische Geräte in einer einzigen "Stück Kunststoff" Darstellung aggregiert.  Die ModelID kann sein, wie bestimmte oder als generisch wie der Hersteller wählt. Beispielsweise kann Produktmodelle, Farben von einer einzelnen Modells oder sogar einzelne Geräte ModelID unterscheiden. Zur Unterstützung der ModelID muss der Gerät-Eigenschaftencode 0xD302 zusammen mit den erforderlichen Eigenschaften unterstützt werden.

*Hinweise zum Entwurf*

-   Finden Sie in der Spezifikation MTP Gerät Services Erweiterung, die mit dem Windows tragbaren Gerät aktivieren Kit, verfügbar unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463545>enthalten ist.

### <a name="deviceportablecoremtp"></a>Device.Portable.Core.MTP

*Tragbare Geräte müssen eine Kerngruppe von Eigenschaften in die Media-Transportprotokoll Version 1.0 oder höher, sowie die Eigenschaften des Geräts und Objekt Formate für den jeweiligen Gerätetyp gemäß und MTP Vorgänge unterstützen.*

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

Media Transfer Protocol (MTP) ist eine Erweiterung des Picture Transfer Protocol (ISO 15740).  Beide Spezifikationen optionale Befehle und Vorgänge enthalten einige davon für die Zertifizierung erforderlich sind. Es ist eine Kerngruppe von Vorgänge und Eigenschaften des Geräts, die von jeder Gerätekategorie erfüllt sein müssen, um mit Windows kompatibel sein. Implementierungsdetails für MTP werden in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert und verwendet werden als Referenz für die Zertifizierung aller tragbaren Geräte als Teil der Windows-Hardware-Zertifizierungsprogramm.

 
**Treiber unterstützt MTP** Ein tragbares Gerät muss die Posteingang MTP-Treiber entwickelt, die im Lieferumfang von Windows. Dies bedeutet, dass sie installieren und ohne die Installation von zusätzlichen Treiber oder Software sofort arbeiten müssen.

**MTP standardmäßig unterstützt** Tragbare Geräte müssen im Lieferumfang von MTP als den Standard-Verbindungsmodus aktiviert. Geräte können Masse Speicher Klasse (MSC) neben MTP unterstützen.

-   Das Gerät darf keine permanente zugänglich benutzereinstellung aktivieren oder deaktivieren den Modus MTP oder MSC.

-   Alle Speichervolumes auf einem Gerät (interne und externe) müssen mit dem Protokoll MTP zugänglich sein.

Ein Gerät haben einen abgesicherten Modus den Benutzer zum Starten der MSC im Modus für Gerät Wiederherstellungsszenarien kann. Nach dem der Benutzer ein Gerät angeschlossen im abgesicherten Modus getrennt wird, muss das Gerät normalen Betrieb wieder aufnehmen.

**Gerät Informationen Dataset** Das Gerät muss das Dataset MTP DeviceInfo unterstützen. In der folgenden Tabelle wird beschrieben, Feld-spezifischen Anforderungen, die implementiert werden müssen:

| DataSet-Feld               | Anforderung | Hinweise                                                                                                                                                                                                                                               |
|-----------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Standard-Version            | R           | Dies bezeichnet die PTP-Version, die dieses Gerät in Hundertstel unterstützt werden kann. Für MTP-Geräte ist dies der Wert 100 (für 1.00) enthalten.                                                                                                       |
| MTP Hersteller Erweiterung-ID     | R           | Die Version MTP-Erweiterung des Herstellers verwendet identifiziert dieses Gerät.                                                                                                                                                                             |
| MTP-Version                 | R           | Die Version der standardmäßigen MTP dieses Gerät unterstützt identifiziert. Für MTP-Geräte unter MTP 1.0 implementiert ist dies der Wert 100 (1.00 darstellt) enthalten. Für MTP Geräte unter MTP 2.0 implementiert ist dies der Wert 200 enthalten. |
| MTP-Erweiterungen              | I           | Diese Zeichenfolge wird verwendet, um eine beliebige Erweiterung auf MTP angewendet ermitteln.                                                                                                                                                                                  |
| Funktionale Modus             | R           | Modi können Gerät, um die unterschiedlichen Zustände mit unterschiedlichen Funktionen express. Wenn das Gerät nur einen einzigen Modus unterstützt, enthält dieses Feld den Wert 0 x 00000000. Finden Sie in der Spezifikation MTP ausführliche.                                                  |
| Unterstützte Vorgänge        | R           | Dieses Feld identifiziert durch Datacode alle Vorgänge, die dieses Gerät in der aktuellen funktionalen Modus unterstützt.                                                                                                                                          |
| Unterstützte Ereignisse            | I           | Dieses Feld identifiziert durch Datacode alle Ereignisse, die dieses Gerät im aktuellen Modus funktionsfähig generiert werden kann.                                                                                                                                          |
| Geräteeigenschaften unterstützt | R           | Dieses Feld identifiziert durch Datacode alle Geräteeigenschaften, die dieses Gerät in der aktuellen funktionalen Modus unterstützt.                                                                                                                                   |
| Erfassen von Formaten             | I           | Dieses Feld identifiziert durch Datacode Formatcodes Objekt für jedes Format, die dieses Gerät unabhängig voneinander generieren kann (die ohne die Inhalte auf dem Gerät platziert wird,).                                                                    |
| Wiedergabeformate            | I           | Dieses Feld identifiziert durch Datacode Formatcodes Objekt für jedes Format, die dieses Gerät kann zu verstehen und analysieren, wenn auf dem Gerät platziert.<br/><br/>Wenn das Gerät nicht identifizierten binäre Objekte ohne weiterführenden durchführen kann, wird dies durch das Einbeziehen von des Codes Undefined-Objekts (0 x 3000) in den Formaten Wiedergabe angezeigt werden. |
| Hersteller                | R           | Die Spezifikation MTP identifiziert dies als ein optionaler String; Es ist erforderlich für die Hardware-Zertifizierung. Dieses Feld enthält eine lesbare Zeichenfolge, die den Hersteller dieses Gerät identifiziert.                                                    |
| Modell                       | R           | Die Spezifikation MTP identifiziert dies als ein optionaler String; Es ist erforderlich für die Hardware-Zertifizierung. Dieses Feld enthält eine lesbare Zeichenfolge, die das Modell der dieses Gerät identifiziert.                                                           |
| Geräteversion              | R           | Die Spezifikation MTP identifiziert dies als ein optionaler String; Es ist erforderlich für die Hardware-Zertifizierung. Dieses Feld enthält eine lesbare Zeichenfolge, die die Software oder Firmware Version von dieses Gerät identifiziert.                                    |
| Seriennummer               | R           | Eine Seriennummer muss unter allen Geräten Freigabe identische Objektmodell und die Geräteversion Felder eindeutig sein.                                                                                                                                                 |

Dabei gilt Folgendes:<br/>
R = erforderlich<br/>
Ich = Wenn implementiert (Optional)<br/>
Nicht zutreffend = nicht zutreffend

**Unterstützt steuern Anfragen** Steuerungsanforderungen aktivieren MTP Initiator Out-of-Band-Anforderungen an den MTP-Responder senden. Das Gerät muss die folgenden Anforderungen unterstützen.

-   Abrufen des Status
-   Anforderung abbrechen
-   Zurücksetzen des Geräts Anforderung

**Vorgänge erforderlich** Diese Core festgelegt, der MTP Vorgänge Geräteeigenschaften durch jedes tragbaren Gerät erfüllt sein müssen, um mit Windows kompatibel sein  Implementierungsdetails für jede Eigenschaft Vorgang und Gerät sind in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert. Die markierten Vorgänge stellen die Kerngruppe von MTP-Vorgänge erforderlich, damit alle tragbaren Geräte dar.

|          &nbsp;         | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0 x 1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0 x 1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0 x 1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0 x 1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0 x 1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0 x 1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A Abgrenzung        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

Finden Sie unter **Vorgänge** in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten MTP Vorgänge.

Die folgenden Vorgänge werden dringend empfohlen, jedoch nicht erforderlich:

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808) - muss für diesen Befehl, Ihr Gerät auch Spezifikation des Ziels, unterstützt werden dem kann den Initiator MTP bestimmen einen übergeordneten Handle für das Objekt.

**Erforderliche Ereignisse** Die folgenden Ereignisse müssen für alle Objekte unterstützt werden:

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

Wenn das Gerät Wechselmedium unterstützt, müssen auch die folgenden Ereignisse unterstützt werden.

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**Vorgangsantworten** Für alle Vorgänge muss eine entsprechende Antwort zurückgegeben werden. Wenn ein Fehler auftritt, Antwort Fehlercodes werden auch definiert und müssen vom Gerät bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt "Antworten" der MTP-Spezifikation.

**Erforderliche Geräteeigenschaften**

|        &nbsp;           | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| Niveau           | 0x5001        | I            | I            | I              | I                    | I            |
| Synchronisierungspartner | 0xD401        | I            | I            | I              | I                    | I            |
| Anzeigename des Geräts    | 0xD402        | R            | R            | I              | I                    | I            |
| Gerätesymbol             | 0xD405        | I            | I            | I              | I                    | I            |

Finden Sie unter **Geräteeigenschaften** in der MTP-Spezifikation, Version 1.0 oder höher für eine vollständige Liste der definierten Eigenschaften des Geräts.

Gerätesymbol ist nicht erforderlich, jedoch wird dringend empfohlen. Bilder mit hoher Auflösung des Geräts können verwendet und in der Windows-Benutzeroberfläche verfügbar gemacht werden.

**Objekt-Formate**

In der folgenden Tabelle wird die Liste der *erforderlichen* Objekt-Formate für ein tragbaren Gerät darstellt. Jedes Objektformat enthält außerdem eine Liste der Objekteigenschaften, die pro Objekttyp unterstützt werden müssen. Das Format hervorgehobene Objekt ist erforderlich für alle MTP Geräte und gilt eine MTP Grundvoraussetzung für Windows.

 

|           &nbsp;                | Eigenschaftencode | Mobiltelefon    | MediaPlayer    | Digitale Kamera  | Digitale Videokamera | Andere (Basis)    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| Nicht definiert                       | 0 x 3000        | I               | I               | I               | I                    | I               |
| Zuordnung                     | 0x3001        | R               | R               | R               | R                    | R               |
| Abstrakte Audio Album            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | n/v             | n/v                  | I<sup>(2)</sup> |
| Abstrakte Audio und Video Wiedergabeliste | 0xBA05        | I               | I               | n/v             | n/v                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG-XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV (ENGL.)                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| Container MP4 (engl.)                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP Container                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3 G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

(1) tragbare Geräte, die wiedergegeben Audio-und/oder Videofunktionen genutzt werden, müssen mindestens eine der folgenden Formate unterstützen. Die folgende Tabelle stellt nicht die vollständige Liste der unterstützten Formate dar; Es stellt die Liste der häufig verwendeten Formate.
Finden Sie in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften **Objekt formatiert** .

(2) unterstützt die folgenden Objekteigenschaften ist für AbstractAudioAlbum Objekte obligatorisch:

-   Genre (0xDC8C)
-   Album Künstlers auswählen (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

Ein Gerät, das Format AbstractAudioAlbum und Bildformat unterstützt, möglicherweise optional Albumcover unterstützt. Albumcover ist die Grafik das Album RepresentativeSampleData Eigenschaft hinzufügen zu einem Objekt AbstractAudioAlbum angeschlossen.

Wenn ein tragbaren Gerät Albumcover unterstützt, muss das Gerät die folgenden Objekteigenschaften unterstützen:

-   PurchaseFlag (0xd901), eine Object-Eigenschaft in der Windows Media DRM 10 für tragbare Geräte MTP Extensions
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   Benutzer-Bewertung (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*Hinweise zum Entwurf*

-   "Picture Transfer-Protokoll (PTP) für digitale dennoch Foto Geräte," Version 1.0 des der PIMA15740: 2000 Picture Transfer Protocol-Spezifikation.
     
-   Das Media Transfer Protocol-Spezifikation, Version 1.0 ist unter *http://go.microsoft.com/fwlink/?LinkId=243145*verfügbar.
     
-   Zusätzliche Implementierungsdetails finden Sie in Windows 7 tragbaren Gerät aktivieren Kit für MTP, die unter <http://go.microsoft.com/fwlink/?LinkId=243146>verfügbar ist.

### <a name="deviceportablecoremtpfunctionality"></a>Device.Portable.Core.MTPFunctionality

*Ein Gerät, MTP unterstützt, muss allgemeine Funktionalität notwendig-Anforderungen, um sicherzustellen, dass Erwartetes Verhalten in Windows erfüllen.*

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

Tragbare Geräten müssen gemäß den Anforderungen unten definierte Verhalten. Das Gerät muss:

 
**Inhalte für alle übertragen Persist-** Das Gerät muss nicht Bericht empfangen von Inhalten, die es nicht gespeichert wurde.

**Erwartungsgemäß - reagiert** Bei eine MTP *GetDeviceStatus* -Anforderung Erhalt, die von einem Host ausgestellt wurden, muss ein tragbares Gerät reagieren.

**Unterstützung von unerwarteten Gerät trennt-** Unerwartet getrennt muss nicht dazu führen, dass das Gerät nicht mehr reagiert (hängen oder Absturz) oder neu zu starten.

### <a name="deviceportablecoremtpmultisession"></a>Device.Portable.Core.MTPMultiSession

*Tragbare Geräten, die MTP multisession-Funktionalität aktivieren müssen erforderliche Object Sitzung Vorgänge unterstützen.*

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

Um multisession MTP-Funktionalität und die Arbeit mit einem multisession bewusst Initiator erwartungsgemäß ordnungsgemäß zu unterstützen, muss das Gerät die folgenden Sitzung Vorgänge unterstützen:

-   CreateSession
-   GetSessionResponderInfo

Der Vorgang RestrictSession ist optional. Dieser Vorgang wird in Windows unterstützt und berücksichtigt Einschränkungen, die in einem Dataset RestrictSession Responder definiert sind.

Diese Vorgänge sind zusätzlich zu den Vorgängen für grundlegende Sitzung Vorgang in der Spezifikation MTP 1.0 definierten erforderlich; Diese Vorgänge sind OpenSession, CloseSession, Transaktions-ID, SessionID usw.. Es ist keine Voraussetzung für die minimale oder maximale Anzahl von Sitzungen, die ein Gerät unterstützen muss, wenn multisession.

*Hinweise zum Entwurf*

Implementierung Details finden Sie unter der Media Transfer-Protokoll Spezifikation Revision 2.0, verfügbar unter *http://go.microsoft.com/fwlink/?LinkId=243142.*

### <a name="deviceportablecoremtpobjectproperties"></a>Device.Portable.Core.MTPObjectProperties

*Ein MTP-Gerät muss die Objekteigenschaften für jede verwendet Media-Format unterstützen.*

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

Die folgenden Gerätefunktionen müssen für jedes vom Gerät gemeldet Format unterstützt werden. Wenn ein MP4-Container unterstützt wird, muss die Gerätefunktion die entsprechenden Eigenschaften in diesem Eintrag enthalten. Anhand dieser Informationen können Windows vorhergesagt werden, die richtige Codierung Profil und Codierung eine Datei für das Gerät, das Sie dann auf dem Gerät wiedergegeben werden kann.

In der folgenden Tabelle sind erforderlich (R) zusammengefasst und empfohlen, wenn implementiert (I) / Optional-Objekt Unterstützung für Eigenschaften, für alle Formate-Objekts. Dies ist eine vollständige Liste der verfügbaren, Objekteigenschaften für nicht die vollständige Liste finden Sie in der Tabelle Objekt Format Zusammenfassung in der Spezifikation MTP.

| Objekteigenschaft                     | Datacode MTP | Status              | Beschreibung                                                                                                                                                                              |
|-------------------------------------|--------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Speicher-ID                          | 0xDC01       | R                   | Bereich für die Speicherung, der das Objekt in gespeichert ist.                                                                                                                                           |
| Objektformat                       | 0xDC02       | R                   | Das Datenformat für das Objekt.                                                                                                                                                          |
| Schutzstatus                   | 0xDC03       | R                   | Der Schutzstatus des Objekts.                                                                                                                                                     |
| Größe des Objekts                         | 0xDC04       | R                   | Die Größe der Datenkomponente des Objekts in Bytes.                                                                                                                                  |
| Name der Objektdatei                    | 0xDC07       | R                   | Der Dateiname des Objekts.                                                                                                                                                             |
| Erstellungsdatum                        | 0xDC08       | I**<sup>(1)</sup>** | Diese Eigenschaft enthält das Datum und die Uhrzeit, wann das Objekt erstellt wurde.                                                                                                                    |
| Änderungsdatum                       | 0xDC09       | I**<sup>(1)</sup>** | Datum und Uhrzeit, wenn das Objekt zuletzt geändert wurde.                                                                                                                                      |
| Das übergeordnete Objekt                       | 0xDC0B       | R                   | Das übergeordnete Objekt des Objekts.                                                                                                                                                         |
| Persistent eindeutige Objekt-ID | 0xDC41       | R                   | Der persistent eindeutige Objektbezeichner des Objekts.                                                                                                                                   |
| Name                                | 0xDC44       | R                   | Der Name des Objekts.                                                                                                                                                                  |
| Verwendbarkeit nicht                      | 0xDC4F       | R                   | Gibt an, ob das Objekt auf den tragbaren Mediaplayer für Speicher nur übertragen wurde und daher ist nicht verfügbar, von dem tragbaren Gerät (beispielsweise wiedergegeben) genutzt werden. |

Dabei gilt Folgendes:<br/>
R = erforderlich<br/>
Ich = Wenn implementiert (Optional)<br/>
Nicht zutreffend = nicht zutreffend

(1) Es wird dringend empfohlen, Erstellungsdatum und Änderungsdatum geführt werden in der Reihenfolge für Applikationen können zu unterscheiden, welche Objekte zuvor importiert oder synchronisiert wurden. Dies ist besonders wichtig für Foto Erwerb Szenarien.

 
In der folgenden Tabelle zusammengefasst erforderlich, und wenn implementiert (Optional)-Eigenschaft Unterstützung von Objekten, Bild, audio und video-Objekts. Dies ist keine vollständige Liste der Eigenschaften für alle unterstützten-Objekts. Eine vollständige Liste finden Sie in der Spezifikation MTP Tabelle Zusammenfassung Property-Objekts.

| Objekteigenschaft              | Datacode MTP | Image | Audio               | Video |
|------------------------------|--------------|-------|---------------------|-------|
| Künstlers auswählen                       | 0xDC46       | n/v   | R                   | I     |
| Beschreibung                  | 0xDC48       | n/v   | I                   | I     |
| Vertreter Sampling-Format | 0xDC81       | I     | I                   | I     |
| Größe der Stichprobe Vertreter   | 0xDC82       | I     | I                   | I     |
| Vertreter Beispiel Höhe | 0xDC83       | I     | I                   | I     |
| Vertreter Beispiel Breite  | 0xDC84       | I     | I                   | I     |
| Vertreter Beispieldaten   | 0xDC86       | I     | I                   | I     |
| Width                        | 0xDC87       | R     | n/v                 | R     |
| Height                       | 0xDC88       | R     | n/v                 | R     |
| Dauer                     | 0xDC89       | n/v   | I                   | I     |
| Benutzer-Bewertung                  | 0xDC8a       | n/v   | I                   | I     |
| Nachverfolgen                        | 0xDC8b       | n/v   | R                   | I     |
| Genre                        | 0xDC8c       | n/v   | I                   | I     |
| Verwendungszähler                    | 0xDC91       | n/v   | I                   | I     |
| Eltern Bewertung              | 0xDC94       | n/v   | I                   | I     |
| Datum der ursprünglichen Freigabe        | 0xDC99       | n/v   | I                   | I     |
| Albumname                   | 0xDC9A       | n/v   | R                   | n/v   |
| Album Künstlers auswählen                 | 0xDC9B       | n/v   | R**<sup>(2)</sup>** | n/v   |
| Bitrate Typ                 | 0xDE92       | n/v   | I                   | I     |
| Abtastrate                  | 0xDE93       | n/v   | R                   | R     |
| Anzahl der Kanäle           | 0xDE94       | n/v   | R                   | R     |
| ScanType                     | 0xDE97       | n/v   | I                   | R     |
| Audio WAVE-Codec             | 0xDE99       | n/v   | R                   | R     |
| Audio Bitrate                | 0xDE9A       | n/v   | R                   | R     |
| Video FourCC Codec           | 0xDE9B       | n/v   | n/v                 | R     |
| Video-Bitrate                | 0xDE9C       | n/v   | n/v                 | R     |
| Frames pro Tausend Sekunden  | 0xDE9D       | n/v   | n/v                 | R     |
| Wichtige Frame Abstand           | 0xDE9E       | n/v   | n/v                 | I     |
| Codierung Profil             | 0xDEA1       | n/v   | I                   | R     |

(2) Album Künstlers auswählen (0xDC9B) nur ist erforderlich, wenn das gesamte Album verfügbar ist, einzelnen Audiodateien nur Künstlers auswählen (0xDC46) unterstützt werden muss.

Darüber hinaus Wenn das Gerät eine Objekteigenschaft Wenn implementiert (Optional) unterstützt, muss das Gerät in Übereinstimmung mit der MTP-Spezifikation und Richtlinien tun. Tests wurden entwickelt, um optionale Funktionalität zu überprüfen, wenn das Gerät unterstützt.

*Hinweise zum Entwurf*

Implementierungsdetails finden Sie in der Media Transfer-Protokoll Spezifikation Revision 1.0, Anhang B - Objekteigenschaften unter *http://go.microsoft.com/fwlink/?LinkId=243143*verfügbar.

### <a name="deviceportablecoremtpstreams"></a>Device.Portable.Core.MTPStreams

*Tragbare Geräten, die MTP Datenströme implementieren müssen erforderliche Object Stream Vorgänge unterstützen.*

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

Um MTP Stream Funktionalität ordnungsgemäß zu unterstützen, muss ein Gerät die folgenden Vorgänge unterstützen:

| Verwendung         | Status | Beschreibung                                                                           |
|-------------------|--------|---------------------------------------------------------------------------------------|
| OpenObjectStream  | R      | Dieser Vorgang wird ein Objekt als Stream geöffnet.                                           |
| ReadObjectStream  | R      | Dieser Vorgang liest einen Teil der Daten aus dem zuvor geöffnete Objektstream.      |
| WriteObjectStream | R      | Dieser Vorgang schreibt den Teil der Daten in den zuvor geöffnete Objektstream.     |
| SeekObjectStream  | R      | Dieser Vorgang sucht nach vorne lesen oder Schreiben des nächsten Datenblock im Stream-Objekt. |
| CloseObjectStream | R      | Dieser Vorgang schließt den Stream zuvor geöffnete Objekt und die zugeordneten frei  |

Dabei gilt Folgendes:<br/>
R = erforderlich<br/>
Ich = If (optional) implementiert.<br/>
Nicht zutreffend = nicht zutreffend

*Hinweise zum Entwurf*

-   Einzelheiten zur Implementierung finden Sie in der Media Transfer-Protokoll Spezifikation Revision 2.0, verfügbar unter <http://go.microsoft.com/fwlink/?LinkId=243144>.

### <a name="deviceportablecoretransportbluetooth"></a>Device.Portable.Core.TransportBluetooth

*Wenn ein tragbares Gerät den Bluetooth-Transport nutzt, und klicken Sie dann das Gerät muss die neuesten erforderlichen Spezifikation(en) für diesen Transport und die entsprechenden Tests unterstützen: Bluetooth (Spezifikationsversion 2.1 oder höher).*

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

Ein tragbares Gerät mit Bluetooth muss die folgenden Spezifikationen verwenden:

-   Bluetooth-Kern-Spezifikation Version 2.1 + EDR (mit dem neuesten fehlerverzeichnis) oder höher \[ <https://www.bluetooth.org/Technical/Specifications/adopted.htm>\]
-   MTP über Bluetooth-Profil-Spezifikation von Microsoft \[ *http://msdn.microsoft.com/en-us/windows/hardware/gg463543*\]

*Hinweise zum Entwurf*

-   Die Verbindung muss gemäß den Anforderungen für Bluetooth-Geräte definierten implementiert werden.

-   Ein Bluetooth-fähigen tragbares Gerät muss mit **Des Fensters Bluetooth-Klassen-Treiber** (in einer standardmäßigen MTP Unterhaltung über Bluetooth ähnlich wie USB und TCP/IP) kommunizieren. 

-   Bluetooth V2.1 + EDR, um sicherzustellen, dass Windows **Secure einfache Paarung (SSR)** optimierte paarungs wünschen nutzen können, muss ein Bluetooth-fähigen tragbares Gerät unterstützen.

-   Ein Bluetooth-fähigen tragbares Gerät muss L2CAP Transport MTP-Responder-Definition Diensteintrag erforderliche Parameter "**GetFormatCapabilities**" zum Abwehren von Format-Enumeration Leistungsprobleme nutzen.

### <a name="deviceportablecoretransportip"></a>Device.Portable.Core.TransportIP

*Wenn ein tragbares Gerät den IP-Transport nutzt, und klicken Sie dann das Gerät muss die neuesten Spezifikation(en) erforderlich für diesen Transport und die entsprechenden Tests unterstützen: IP (zusammen mit der MTP Netzwerk Zuordnung Erweiterung Spezifikation und die zugehörigen UPnP Spezifikationen).*

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

Ein Windows tragbares Gerät, das MTP Implementation unterstützt muss der Kamera und Imaging Produkte Zuordnung (CIPA) PTP over Internet Protocol (PTP/IP-Adresse)-Spezifikation (CIPA-005/2005) entsprechen, die die Spezifikation PTP Verwendung von TCP/IP PTP Operationen über drahtlose Netzwerke erweitert.

 
Ein MTP-IP-Gerät muss die folgenden drei Technologien zum Sicherstellen der Kompatibilität mit dem PC unterstützen:

1. **Basic UPnP-Gerät**

    MTP-IP-Geräte müssen Discovery als einen Universal Plug and Play (UPnP "für) grundlegende Device Simple Service Discovery Protocol (SSDP) unterstützen. Verweisen Sie auf die MTP Netzwerk Zuordnung Erweiterung Definition für Details.

2. **Transfer-Protokoll über IP-Bild**

    MTP-IP-Geräten müssen der Kamera und Imaging Produkte Zuordnung (CIPA) PTP over Internet Protocol (PTP und IP-Adresse)-Spezifikation (CIPA-005/2005) entsprechen, die die Spezifikation PTP Verwendung von TCP/IP PTP Operationen über drahtlose Netzwerke erweitert.

3. **MTP Netzwerk Association-Erweiterung**

    MTP-IP-Geräte müssen mit der Erweiterung Wi-Fi-Bereitstellung, die der Spezifikation für MTP und die Erweiterung MTP Netzwerk Zuordnung der MTP-Spezifikation entsprechen.

Unterstützung für diese Erweiterung MTP wird angegeben, indem Sie einschließlich der folgenden Zeichenfolge im Feld MTPVendorExtensionDesc der MTP DeviceInfo Dataset als Antwort auf die Operation MTP GetDeviceInfo zurückgegeben.

| DataSet-Feld          | Datentyp                   |
|------------------------|----------------------------|
| MTPVendorExtensionDesc | "microsoft.com/WPDNA: 1.0" |

 
Die von dieser Erweiterung definierte Geräteeigenschaft unterstützt Netzwerk Association-Konfiguration für Geräte, die 0 (null) oder Nennwert-Authentifizierung unterstützen. Sicherer Authentifizierung wird von dieser Erweiterung nicht unterstützt. sicherer Authentifizierung kann über einen benutzerdefinierten MTP Dienst implementiert werden, falls gewünscht. Die Definition MTP Netzwerk Zuordnung Erweiterung Weitere Informationen finden Sie unter.

**Empfehlungen für die Bereitstellung von Netzwerk**

Die Erweiterung MTP Wi-Fi Provisioning erweitert die Windows Connect Now-Architektur MTP Geräte. Dieser Erweiterung definiert ein neues Format der MTP-Objekt für Objekte WFC (Wireless-Konfigurationsdatei). Ein WFC-Objekt enthält die Netzwerkeinstellungen, die den Responder zur Teilnahme an einem drahtlosen Netzwerk ermöglichen. Unterstützung für die Architektur WCN Initiator werden können WFC Objekte auf das Gerät übertragen. Jedes WFC-Objekt stellt die Einstellungen für ein einzelnes drahtlosen Netzwerk. Der Responder möglicherweise mehrere WFC Objekte über einen Zeitraum. Jedes Objekt wird entsprechend die SSID des Netzwerks heißen.

Die folgenden DataType muss in das Feld MTPVendorExtensionDesc des Datasets DeviceInfo enthalten sein.

| DataSet-Feld          | Datentyp                    |
|------------------------|-----------------------------|
| MTPVendorExtensionDesc | "microsoft.com/WPDWCN: 1.0" |

 
**Empfehlungen zur Verbesserung der Leistung über IP** Um die Format-Enumeration Leistungsprobleme zu verringern, sollten MTP-IP-Geräten auch den Vorgang **GetFormatCapabilities** unterstützen, gemäß Definition in der Spezifikation MTP Gerät Services Extensions. Dieser Vorgang verbessert die Leistung von Abfragen von einem Gerät für die unterstützten Objekteigenschaften auf die Formate klassische MTP speichern (diese Formate, die im Dataset DeviceInfo angezeigt werden) zugeordnet werden. GetFormatCapabilities ist eine Massenvorgang, der die Funktionalität von GetObjectPropsSupported, GetObjectPropDesc und GetInterdependentPropDesc dupliziert. Responder sollten diese Operation implementieren, weil es mehrere Aufrufe an das Gerät mit einem einzigen, effizienter Aufruf ersetzt.

*Hinweise zum Entwurf*

-   Finden Sie in der Spezifikation PTP und IP-Adresse (CIPA-005/2005) "Picture Transfer-Protokoll über TCP/IP-Netzwerke".

-   Erweiterung Spezifikation für MTP Gerät Services unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463545>.

-   MTP Netzwerk Association, MTP Windows Connect Now und MTP Wi-Fi-Bereitstellung Erweiterung Dokumente sind verfügbar unter <http://msdn.microsoft.com/en-us/windows/hardware/gg463543>.

### <a name="deviceportablecoretransportipdlna"></a>Device.Portable.Core.TransportIPDLNA

*Anforderungen für Mediengeräten Netzwerklastenausgleichs definierten entspricht ein tragbaren Gerät, das als DMR oder DMS fungiert.*

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

Tragbare Geräte können eine oder mehrere der DLNA Geräteklassen wie implementieren:

-   Digitaler Medien Renderer (DMR)
-   Digitaler Medien-Server (DMS)

Das Gerät muss die Anforderungen, die für jedes Geräteklasse mit dem Namen im Abschnitt Mediengeräte Netzwerklastenausgleichs der Windows Hardware Zertifizierung Programm Anforderungen definiert erfüllen. DLNA wird unabhängig von MTP verwaltet.

*Hinweise zum Entwurf*

-   Finden Sie im Abschnitt Mediengeräte Netzwerklastenausgleichs Details der Anforderung. Informationen zur DLNA Zertifizierung finden Sie unter [http://www.dlna.org](http://www.dlna.org/).

### <a name="deviceportablecoretransportusb"></a>Device.Portable.Core.TransportUSB

*Wenn ein tragbaren Gerät die USB-Übertragung nutzt und anschließend das Gerät muss die neuesten erforderlichen Spezifikation(en) für diesen Transport und die entsprechenden Tests unterstützen: USB (Spezifikationsversion 2.0 oder höher).*

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

Ein tragbares Gerät mit USB muss Folgendes verwenden:

-   USB-Kern-Spezifikation Version 2.0 (mit dem neuesten fehlerverzeichnis) oder höher \[ <http://www.usb.org/developers/docs>\]

-   USB MTP DWG Spezifikation 1.0 (mit dem neuesten fehlerverzeichnis) oder höher \[ <http://www.usb.org/developers/devclass_docs>\]

*Hinweise zum Entwurf*

-   Verbunden-USB-Geräten müssen Hochgeschwindigkeits und schnellen unterstützen. Super Geschwindigkeit ist optional.

-   Die Verbindung muss gemäß den Anforderungen im Abschnitt Typ entsprechende Verbindung implementiert werden.

-   Es gibt keine spezifischen Windows Hardwarezertifizierung Anforderungen für den Typ des USB-Anschluss auf einem tragbaren Gerät verwendet.

### <a name="deviceportablecorevideocodec"></a>Device.Portable.Core.VideoCodec

*Wenn ein tragbares Gerät die Möglichkeit zum Erfassen von Videoinhalten aufweist, muss dies mithilfe eines Formats in Windows systemintern unterstützt geschehen.*

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

Wenn ein tragbares Gerät Videoinhalte erfassen kann, muss dies in einem Format erfolgen, die Windows systemintern ohne die Notwendigkeit zusätzlicher Codecs zu installierende decodiert werden können.

In den folgenden Tabellen stehen für die Liste der im Feld Formate, denen auf Windows gerendert wird. Dies ist nicht der vollständig unterstützte Formate. Die vollständige Liste der unterstützten Formaten finden Sie unter: <http://go.microsoft.com/fwlink/?LinkID=242995&clcid=0x409>.

**Beachten Sie** , dass für ein bestimmtes Format in den folgenden Tabellen, die es nicht erforderlich ist, alle angegebenen Bitraten und Abtastrate unterstützen, es jedoch erforderlich ist, um ein Format zu unterstützen, die in den Bereichen ausgerichtet.

<html>
    <p><strong>MP4 (engl.) Container-Inhalt</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="4">AAC</th>
                <td>Codec</td>
                <td>
AAC Standard, minimale AAC Profil der Ebene 2 (0 x 29),<br />
kompatibel mit 0, x 29 0x2A; 0x2B, 0x2C; 0x2E, 0x2F; 0 x 30, 0x31; 0 x 32, 0 x 33                </td>
            </tr>
            <tr class="even">
                <td>Bitrate CBR</td>
                <td>96, 128, 160, 192 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="even">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
            <tr class="odd">
                <th rowspan="5">H. 264</th>
                <td>Codec</td>
                <td>H. 264-Standard</td>
            </tr>
            <tr class="even">
                <td>Codec-Profil</td>
                <td>Geplante Stufe 3</td>
            </tr>
            <tr class="odd">
                <td>Auflösung, Pixel-Seitenverhältnis</td>
                <td>Alle (sofern angegeben)</td>
            </tr>
            <tr class="even">
                <td>Framerate</td>
                <td>Alle (sofern angegeben)</td>
            </tr>
            <tr class="odd">
                <td>Durchschnittliche Bitrate</td>
                <td>Alle (sofern angegeben)</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>Mobile WMV-Videoinhalten</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA-Standard</th>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>Aus 48 bis 96 Kilobit pro Sekunde (Kbit/s)</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>192 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV (ENGL.)</th>
                <td>Codec</td>
                <td>VC++-1</td>
            </tr>
            <tr class="odd">
                <td>Codec-Profil</td>
                <td>Einfach</td>
            </tr>
            <tr class="even">
                <td>Auflösung, Pixelseitenverhältnis</td>
                <td>
Einer der folgenden:                    <ul>
                        <li>176Ã – 144 Pixel, 1:1</li>
                        <li>220Ã – 176 Pixel, 1:1</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>Framerate</td>
                <td>15 oder 24 Frames pro Sekunde</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>Von 96 auf 384 KBit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>768 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale Puffer</td>
                <td>3 Sekunden</td>
            </tr>
            <tr class="odd">
                <td>Maximale Schlüssel-Frame-Entfernung</td>
                <td>15 Sekunden</td>
            </tr>
            <tr class="even">
                <td>Farbtiefe</td>
                <td>16 Bit pro pixel</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>Portable WMV-Videoinhalte</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA-Standard</th>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>Von 48 auf 128 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>256 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV (ENGL.)</th>
                <td>Codec</td>
                <td>VC++-1</td>
            </tr>
            <tr class="odd">
                <td>Codec-Profil</td>
                <td>Einfach</td>
            </tr>
            <tr class="even">
                <td>Auflösung, Pixelseitenverhältnis</td>
                <td>
Einer der folgenden:                    <ul>
                        <li>320 Ã – 240 Pixel, 1:1</li>
                        <li>480 Ã – 270 Pixel, 1:1</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>Framerate</td>
                <td>24, 25 oder 29,97 Frames pro Sekunde</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>Von 384 auf 850 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>1.700 KBit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale Puffer</td>
                <td>3 Sekunden</td>
            </tr>
            <tr class="odd">
                <td>Maximale Schlüssel-Frame-Entfernung</td>
                <td>15 Sekunden</td>
            </tr>
            <tr class="even">
                <td>Farbtiefe</td>
                <td>16 Bit pro pixel</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>Standard WMV-Videoinhalten</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>Einstellung</th>
                <th>Anforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA-Standard</th>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>64 bis 192 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>360 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV (ENGL.)</th>
                <td>Codec</td>
                <td>VC++ 1</td>
            </tr>
            <tr class="odd">
                <td>Codec-Profil</td>
                <td>Main</td>
            </tr>
            <tr class="even">
                <td>Auflösung, Pixel-Seitenverhältnis</td>
                <td>
Einer der folgenden:                    <ul>
                        <li>640 Ã – 480 Pixel, 1:1</li>
                        <li>720 Ã – 480 Pixel, 10:11</li>
                        <li>720 Ã – 480 Pixel, 40:33</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>Framerate</td>
                <td>24, 25 oder 29,97 Frames pro Sekunde</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>Von 1000 auf 3.000 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>6.000 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale Puffer</td>
                <td>2 Sekunden</td>
            </tr>
            <tr class="odd">
                <td>Maximale Schlüssel-Frame-Entfernung</td>
                <td>15 Sekunden</td>
            </tr>
            <tr class="even">
                <td>Farbtiefe</td>
                <td>16 oder 24 Bit pro pixel</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>High-Definition WMV-Videoinhalte</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>Einstellung</th>
                <th>Mindestanforderung</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA-Standard</th>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="even">
                <td>Durchschnittliche Bitrate</td>
                <td>64 bis 192 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale maximale Videobitrate</td>
                <td>360 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Abtastrate</td>
                <td>44,1 oder 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>Kanäle</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="5">WMA Professional</th>
                <td>Codec</td>
                <td>WMA9 oder höher</td>
            </tr>
            <tr class="odd">
                <td>Durchschnittliche Bitrate</td>
                <td>Von 320 auf 1.500 KBit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale maximale Videobitrate</td>
                <td>2500 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Abtastrate</td>
                <td>44,1, 48 oder 96 kHz</td>
            </tr>
            <tr class="even">
                <td>Kanäle</td>
                <td>bis zu 8</td>
            </tr>
            <tr class="odd">
                <th rowspan="9">WMV (ENGL.)</th>
                <td>Codec</td>
                <td>VC++-1</td>
            </tr>
            <tr class="even">
                <td>Codec-Profil</td>
                <td>Erweiterte</td>
            </tr>
            <tr class="odd">
                <td>Auflösung, Pixelseitenverhältnis</td>
                <td>1280 Ã – 720 Pixel, 1:1</td>
            </tr>
            <tr class="even">
                <td>Framerate</td>
                <td>24, 25 oder 29,97 Frames pro Sekunde</td>
            </tr>
            <tr class="odd">
                <td>Durchschnittliche Bitrate</td>
                <td>8.000 bis 10.000 Kbit/s</td>
            </tr>
            <tr class="even">
                <td>Maximale maximale Videobitrate</td>
                <td>20.000 Kbit/s</td>
            </tr>
            <tr class="odd">
                <td>Maximale Puffer</td>
                <td>2 Sekunden</td>
            </tr>
            <tr class="even">
                <td>Maximale Schlüssel-Frame-Entfernung</td>
                <td>15 Sekunden</td>
            </tr>
            <tr class="odd">
                <td>Farbtiefe</td>
                <td>24 Bit pro pixel</td>
            </tr>
        </tbody>
    </table>
</html>


<a name="device.portable.digitalcamera"></a>
## <a name="deviceportabledigitalcamera"></a>Device.Portable.DigitalCamera

*Digitale Kamera*

### <a name="deviceportabledigitalcameramtp"></a>Device.Portable.DigitalCamera.MTP

*Digitale Kameras müssen MTP-Vorgänge und-Eigenschaften in die Medien Transport Protocol Version 1.0 oder höher, zusammen mit bestimmten Objekts Formate pro Gerätetyp gemäß unterstützen.*

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

Media Transfer Protocol (MTP) ist eine Erweiterung des Picture Transfer Protocol (ISO 15740).  Beide Spezifikationen optionale Befehle und Vorgänge enthalten einige davon für die Zertifizierung erforderlich sind. Es ist eine Kerngruppe von Vorgänge und Eigenschaften des Geräts, die von jeder Gerätekategorie erfüllt sein müssen, um mit Windows kompatibel sein. Implementierungsdetails für MTP werden in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert und verwendet werden als Referenz für die Zertifizierung aller tragbaren Geräte als Teil der Windows-Hardware-Zertifizierungsprogramm.

**Erforderliche Vorgänge**

Diese Core festgelegt, der MTP Vorgänge Geräteeigenschaften durch jedes tragbaren Gerät erfüllt sein müssen, um mit Windows kompatibel sein  Implementierungsdetails für jede Eigenschaft Vorgang und Gerät sind in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert.

|        &nbsp;           | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0 x 1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0 x 1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0 x 1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0 x 1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0 x 1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0 x 1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A Abgrenzung        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
Dabei gilt Folgendes:<br/>
R = erforderlich<br/>
Ich = Wenn implementiert (Optional)<br/>
Nicht zutreffend = nicht zutreffend<br/>

Finden Sie unter **Vorgänge** in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten MTP Vorgänge.

Die folgenden Vorgänge werden dringend empfohlen, jedoch nicht erforderlich:

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808) - muss für diesen Befehl, Ihr Gerät auch Spezifikation des Ziels, unterstützt werden dem kann den Initiator MTP bestimmen einen übergeordneten Handle für das Objekt.

**Erforderliche Ereignisse**

Die folgenden Ereignisse müssen für alle Objekte unterstützt werden:

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

Wenn das Gerät Wechselmedium unterstützt, müssen auch die folgenden Ereignisse unterstützt werden.

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**Vorgangsantworten**

Für alle Vorgänge muss eine entsprechende Antwort zurückgegeben werden. Wenn ein Fehler auftritt, Antwort Fehlercodes werden auch definiert und müssen vom Gerät bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt "Antworten" der MTP-Spezifikation.

**Erforderliche Geräteeigenschaften**

|     &nbsp;              | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| Niveau           | 0x5001        | I            | I            | I              | I                    | I            |
| Synchronisierungspartner | 0xD401        | I            | I            | I              | I                    | I            |
| Anzeigename des Geräts    | 0xD402        | R            | R            | I              | I                    | I            |
| Gerätesymbol             | 0xD405        | I            | I            | I              | I                    | I            |

Finden Sie unter **Geräteeigenschaften** in der MTP-Spezifikation, Version 1.0 oder höher für eine vollständige Liste der definierten Eigenschaften des Geräts.
Gerätesymbol ist nicht erforderlich, aber es wird dringend empfohlen. Bilder mit hoher Auflösung des Geräts können verwendet und in der Windows-Benutzeroberfläche verfügbar gemacht werden.

**Objekt-Formate**

In der folgenden Tabelle wird die Liste der *erforderlichen* Objekt-Formate für ein tragbaren Gerät darstellt.
Jedes Objektformat enthält außerdem eine Liste der Objekteigenschaften, die pro Objekttyp unterstützt werden müssen.

|          &nbsp;                 | Eigenschaftencode | Mobiltelefon    | MediaPlayer    | Digitale Kamera  | Digitale Videokamera | Andere (Basis) |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|--------------|
| Nicht definiert                       | 0 x 3000        | I               | I               | I               | I                    | I            |
| Zuordnung                     | 0x3001        | R               | R               | R               | R                    | R            |
| Abstrakte Audio Album            | 0xBA03        | I               | I               | n/v             | n/v                  | I            |
| Abstrakte Audio und Video Wiedergabeliste | 0xBA05        | I               | I               | n/v             | n/v                  | I            |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| JPEG-XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| WMV (ENGL.)                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| Container MP4 (engl.)                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3GP Container                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3 G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I            |

(1) tragbare Geräte, die wiedergegeben Audio-und/oder Videofunktionen genutzt werden, müssen mindestens eine der folgenden Formate unterstützen. Die folgende Tabelle stellt nicht die vollständige Liste der unterstützten Formate dar; Es stellt die Liste der häufig verwendeten Formate.

Finden Sie in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften **Objekt formatiert** .

*Hinweise zum Entwurf*

-   "Picture Transfer-Protokoll (PTP) für digitale dennoch Foto Geräte," Version 1.0 des der PIMA15740: 2000 Picture Transfer Protocol-Spezifikation.

-   Das Media Transfer Protocol-Spezifikation, Version 1.0 ist unter *http://go.microsoft.com/fwlink/?LinkId=243145*verfügbar.

-   Zusätzliche Implementierungsdetails finden Sie in Windows 7 tragbaren Gerät aktivieren Kit für MTP, die unter <http://go.microsoft.com/fwlink/?LinkId=243146>verfügbar ist.

<a name="device.portable.digitalvideocamera"></a>
## <a name="deviceportabledigitalvideocamera"></a>Device.Portable.DigitalVideoCamera

*DigitalVideoCamera*

### <a name="deviceportabledigitalvideocameramtp"></a>Device.Portable.DigitalVideoCamera.MTP

*Digitale Videokameras muss MTP-Vorgänge und-Eigenschaften in die Medien Transport Protocol Version 1.0 oder höher, zusammen mit bestimmten Objekts Formate pro Gerätetyp gemäß unterstützen.*

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

Media Transfer Protocol (MTP) ist eine Erweiterung des Picture Transfer Protocol (ISO 15740).  Beide Spezifikationen optionale Befehle und Vorgänge enthalten einige davon für die Zertifizierung erforderlich sind. Es ist eine Kerngruppe von Vorgänge und Eigenschaften des Geräts, die von jeder Gerätekategorie erfüllt sein müssen, um mit Windows kompatibel sein. Implementierungsdetails für MTP werden in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert und verwendet werden als Referenz für die Zertifizierung aller tragbaren Geräte als Teil der Windows-Hardware-Zertifizierungsprogramm.

**Erforderliche Vorgänge**

Diese Core festgelegt, der MTP Vorgänge Geräteeigenschaften durch jedes tragbaren Gerät erfüllt sein müssen, um mit Windows kompatibel sein  Implementierungsdetails für jede Eigenschaft Vorgang und Gerät sind in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert.

|       &nbsp;            | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0 x 1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0 x 1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0 x 1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0 x 1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0 x 1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0 x 1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A Abgrenzung        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
Wobei: < /br/ > R erforderlichen < /br/ > = Ich = Wenn implementiert (Optional) < /br/ > n/v = nicht zutreffend

Finden Sie unter **Vorgänge** in der MTP-Spezifikation, Version 1.0 oder höher für vollständige Liste der definierten MTP Vorgänge.
Die folgenden Vorgänge werden dringend empfohlen, aber nicht erforderlich:

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808) - muss für diesen Befehl, Ihr Gerät auch Spezifikation des Ziels, unterstützt werden dem kann den Initiator MTP bestimmen einen übergeordneten Handle für das Objekt.

**Erforderliche Ereignisse**

Die folgenden Ereignisse müssen für alle Objekte unterstützt werden:

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

Wenn das Gerät Wechselmedium unterstützt, müssen auch die folgenden Ereignisse unterstützt werden.

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**Vorgangsantworten**

Für alle Vorgänge muss eine entsprechende Antwort zurückgegeben werden. Wenn ein Fehler auftritt, Antwort Fehlercodes werden auch definiert und müssen vom Gerät bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt "Antworten" der MTP-Spezifikation.

**Erforderliche Geräteeigenschaften**

|        &nbsp;           | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| Niveau           | 0x5001        | I            | I            | I              | I                    | I            |
| Synchronisierungspartner | 0xD401        | I            | I            | I              | I                    | I            |
| Anzeigename des Geräts    | 0xD402        | R            | R            | I              | I                    | I            |
| Gerätesymbol             | 0xD405        | I            | I            | I              | I                    | I            |

Finden Sie unter **Geräteeigenschaften** in der MTP-Spezifikation, Version 1.0 oder höher für eine vollständige Liste der definierten Eigenschaften des Geräts.
Gerätesymbol ist nicht erforderlich, aber es wird dringend empfohlen. Bilder mit hoher Auflösung des Geräts können verwendet und in der Windows-Benutzeroberfläche verfügbar gemacht werden.

**Objekt-Formate**

In der folgenden Tabelle wird die Liste der *erforderlichen* Objekt-Formate für ein tragbaren Gerät darstellt.
Jedes Objektformat enthält außerdem eine Liste der Objekteigenschaften, die pro Objekttyp unterstützt werden müssen.

|            &nbsp;               | Eigenschaftencode | Mobiltelefon    | MediaPlayer    | Digitale Kamera  | Digitale Videokamera | Andere (Basis) |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|--------------|
| Nicht definiert                       | 0 x 3000        | I               | I               | I               | I                    | I            |
| Zuordnung                     | 0x3001        | R               | R               | R               | R                    | R            |
| Abstrakte Audio Album            | 0xBA03        | I               | I               | n/v             | n/v                  | I            |
| Abstrakte Audio und Video Wiedergabeliste | 0xBA05        | I               | I               | n/v             | n/v                  | I            |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| JPEG-XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| WMV (ENGL.)                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| Container MP4 (engl.)                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3GP Container                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3 G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I            |

(1) tragbare Geräte, die wiedergegeben Audio-und/oder Videofunktionen genutzt werden, müssen mindestens eine der folgenden Formate unterstützen. Die folgende Tabelle stellt nicht die vollständige Liste der unterstützten Formate dar; Es stellt die Liste der häufig verwendeten Formate.
Finden Sie in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften **Objekt formatiert** .

*Hinweise zum Entwurf*

-   "Picture Transfer-Protokoll (PTP) für digitale dennoch Foto Geräte," Version 1.0 des der PIMA15740: 2000 Picture Transfer Protocol-Spezifikation.

-   Das Media Transfer Protocol-Spezifikation, Version 1.0 ist unter *http://go.microsoft.com/fwlink/?LinkId=243145*verfügbar.

-   Zusätzliche Implementierungsdetails finden Sie in Windows 7 tragbaren Gerät aktivieren Kit für MTP, die unter <http://go.microsoft.com/fwlink/?LinkId=243146>verfügbar ist.

<a name="device.portable.mediaplayer"></a>
## <a name="deviceportablemediaplayer"></a>Device.Portable.MediaPlayer

*MediaPlayer*

### <a name="deviceportablemediaplayermtp"></a>Device.Portable.MediaPlayer.MTP

*MediaPlayer müssen MTP-Vorgänge und-Eigenschaften in die Medien Transport Protocol Version 1.0 oder höher, zusammen mit bestimmten Objekts Formate pro Gerätetyp gemäß unterstützen.*

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

Media Transfer Protocol (MTP) ist eine Erweiterung des Picture Transfer Protocol (ISO 15740).  Beide Spezifikationen optionale Befehle und Vorgänge enthalten einige davon für die Zertifizierung erforderlich sind. Es ist eine Kerngruppe von Vorgänge und Eigenschaften des Geräts, die von jeder Gerätekategorie erfüllt sein müssen, um mit Windows kompatibel sein. Implementierungsdetails für MTP werden in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert und verwendet werden als Referenz für die Zertifizierung aller tragbaren Geräte als Teil der Windows-Hardware-Zertifizierungsprogramm.

**Erforderliche Vorgänge**

Diese Core festgelegt, der MTP Vorgänge Geräteeigenschaften durch jedes tragbaren Gerät erfüllt sein müssen, um mit Windows kompatibel sein  Implementierungsdetails für jede Eigenschaft Vorgang und Gerät sind in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert.

|       &nbsp;            | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0 x 1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0 x 1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0 x 1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0 x 1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0 x 1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0 x 1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A Abgrenzung        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
Dabei gilt Folgendes:<br/>
R = erforderlich<br/>
Ich = Wenn implementiert (Optional)<br/>
Nicht zutreffend = nicht zutreffend

Finden Sie unter **Vorgänge** in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten MTP Vorgänge.
Die folgenden Vorgänge werden dringend empfohlen, jedoch nicht erforderlich:

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808) - muss für diesen Befehl, Ihr Gerät auch Spezifikation des Ziels, unterstützt werden dem kann den Initiator MTP bestimmen einen übergeordneten Handle für das Objekt.

**Erforderliche Ereignisse**

Die folgenden Ereignisse müssen für alle Objekte unterstützt werden:

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

Wenn das Gerät Wechselmedium unterstützt, müssen auch die folgenden Ereignisse unterstützt werden.

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**Vorgangsantworten**

Für alle Vorgänge muss eine entsprechende Antwort zurückgegeben werden. Wenn ein Fehler auftritt, Antwort Fehlercodes werden auch definiert und müssen vom Gerät bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt "Antworten" der MTP-Spezifikation.

**Erforderliche Geräteeigenschaften**

|         &nbsp;          | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| Niveau           | 0x5001        | I            | I            | I              | I                    | I            |
| Synchronisierungspartner | 0xD401        | I            | I            | I              | I                    | I            |
| Anzeigename des Geräts    | 0xD402        | R            | R            | I              | I                    | I            |
| Gerätesymbol             | 0xD405        | I            | I            | I              | I                    | I            |

Finden Sie unter **Eigenschaften des Geräts** in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften.
Gerätesymbol ist nicht erforderlich, aber es wird dringend empfohlen. Bilder mit hoher Auflösung des Geräts können verwendet und in der Windows-Benutzeroberfläche verfügbar gemacht werden.

**Objekt-Formate**

In der folgenden Tabelle wird die Liste der *erforderlichen* Objekt-Formate für ein tragbaren Gerät darstellt.
Jedes Objektformat enthält außerdem eine Liste der Objekteigenschaften, die pro Objekttyp unterstützt werden müssen.

|        &nbsp;                   | Eigenschaftencode | Mobiltelefon    | MediaPlayer    | Digitale Kamera  | Digitale Videokamera | Andere (Basis)    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| Nicht definiert                       | 0 x 3000        | I               | I               | I               | I                    | I               |
| Zuordnung                     | 0x3001        | R               | R               | R               | R                    | R               |
| Abstrakte Audio Album            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | n/v             | n/v                  | I<sup>(2)</sup> |
| Abstrakte Audio und Video Wiedergabeliste | 0xBA05        | I               | I               | n/v             | n/v                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG-XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV (ENGL.)                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| Container MP4 (engl.)                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP Container                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3 G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

(1) tragbare Geräte, die wiedergegeben Audio-und/oder Videofunktionen genutzt werden, müssen mindestens eine der folgenden Formate unterstützen. Die folgende Tabelle stellt nicht die vollständige Liste der unterstützten Formate dar; Es stellt die Liste der häufig verwendeten Formate.
Finden Sie in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften **Objekt formatiert** .
(2) unterstützt die folgenden Objekteigenschaften ist für AbstractAudioAlbum Objekte obligatorisch:

-   Genre (0xDC8C)
-   Album Künstlers auswählen (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

Ein Gerät, das Format AbstractAudioAlbum und Bildformat unterstützt, möglicherweise optional Albumcover unterstützt. Albumcover ist die Grafik das Album RepresentativeSampleData Eigenschaft hinzufügen zu einem Objekt AbstractAudioAlbum angeschlossen.
Wenn ein tragbaren Gerät Albumcover unterstützt, muss das Gerät die folgenden Objekteigenschaften unterstützen:

-   PurchaseFlag (0xd901), eine Object-Eigenschaft in der Windows Media DRM 10 für tragbare Geräte MTP Extensions
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   Benutzer-Bewertung (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*Hinweise zum Entwurf*

-   "Picture Transfer-Protokoll (PTP) für digitale dennoch Foto Geräte," Version 1.0 des der PIMA15740: 2000 Picture Transfer Protocol-Spezifikation.

-   Das Media Transfer Protocol-Spezifikation, Version 1.0 ist unter *http://go.microsoft.com/fwlink/?LinkId=243145*verfügbar.

-   Zusätzliche Implementierungsdetails finden Sie in Windows 7 tragbaren Gerät aktivieren Kit für MTP, die unter <http://go.microsoft.com/fwlink/?LinkId=243146>verfügbar ist.

<a name="device.portable.mobilephone"></a>
## <a name="deviceportablemobilephone"></a>Device.Portable.MobilePhone

*MobilePhone*

### <a name="deviceportablemobilephonemtp"></a>Device.Portable.MobilePhone.MTP

*Mobiltelefone muss MTP-Vorgänge und-Eigenschaften in die Medien Transport Protocol Version 1.0 oder höher, zusammen mit bestimmten Objekts Formate pro Gerätetyp gemäß unterstützen.*

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

Media Transfer Protocol (MTP) ist eine Erweiterung des Picture Transfer Protocol (ISO 15740).  Beide Spezifikationen optionale Befehle und Vorgänge enthalten einige davon für die Zertifizierung erforderlich sind. Es ist eine Kerngruppe von Vorgänge und Eigenschaften des Geräts, die von jeder Gerätekategorie erfüllt sein müssen, um mit Windows kompatibel sein. Implementierungsdetails für MTP werden in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert und verwendet werden als Referenz für die Zertifizierung aller tragbaren Geräte als Teil der Windows-Hardware-Zertifizierungsprogramm.

**Erforderliche Vorgänge**

Diese Core festgelegt, der MTP Vorgänge Geräteeigenschaften durch jedes tragbaren Gerät erfüllt sein müssen, um mit Windows kompatibel sein  Implementierungsdetails für jede Eigenschaft Vorgang und Gerät sind in der Media Transfer-Protokoll-Spezifikation, Version 1.0 oder höher definiert.

|       &nbsp;            | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0 x 1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0 x 1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0 x 1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0 x 1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0 x 1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0 x 1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A Abgrenzung        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

Wo: R = erforderlich<br/>
Ich = Wenn implementiert (Optional)<br/>
Nicht zutreffend = nicht zutreffend

Finden Sie unter **Vorgänge** in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten MTP Vorgänge.

Die folgenden Vorgänge werden dringend empfohlen, jedoch nicht erforderlich:

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808) - muss für diesen Befehl, Ihr Gerät auch Spezifikation des Ziels, unterstützt werden dem kann den Initiator MTP bestimmen einen übergeordneten Handle für das Objekt.

**Erforderliche Ereignisse**

Die folgenden Ereignisse müssen für alle Objekte unterstützt werden:

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

Wenn das Gerät Wechselmedium unterstützt, müssen auch die folgenden Ereignisse unterstützt werden.

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**Vorgangsantworten**

Für alle Vorgänge muss eine entsprechende Antwort zurückgegeben werden. Wenn ein Fehler auftritt, Antwort Fehlercodes werden auch definiert und müssen vom Gerät bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt "Antworten" der MTP-Spezifikation.

**Erforderliche Geräteeigenschaften**

|        &nbsp;           | Eigenschaftencode | Mobiltelefon | MediaPlayer | Digitale Kamera | Digitale Videokamera | Andere (Basis) |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| Niveau           | 0x5001        | I            | I            | I              | I                    | I            |
| Synchronisierungspartner | 0xD401        | I            | I            | I              | I                    | I            |
| Anzeigename des Geräts    | 0xD402        | R            | R            | I              | I                    | I            |
| Gerätesymbol             | 0xD405        | I            | I            | I              | I                    | I            |

Finden Sie unter **Geräteeigenschaften** in der MTP-Spezifikation, Version 1.0 oder höher für eine vollständige Liste der definierten Eigenschaften des Geräts.

Gerätesymbol ist nicht erforderlich, aber es wird dringend empfohlen. Bilder mit hoher Auflösung des Geräts können verwendet und in der Windows-Benutzeroberfläche verfügbar gemacht werden.

**Objekt-Formate**

In der folgenden Tabelle wird die Liste der *erforderlichen* Objekt-Formate für ein tragbaren Gerät darstellt.
Jedes Objektformat enthält außerdem eine Liste der Objekteigenschaften, die pro Objekttyp unterstützt werden müssen.

|              &nbsp;             | Eigenschaftencode | Mobiltelefon    | MediaPlayer    | Digitale Kamera  | Digitale Videokamera | Andere (Basis)    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| Nicht definiert                       | 0 x 3000        | I               | I               | I               | I                    | I               |
| Abstrakte Audio Album            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | n/v             | n/v                  | I<sup>(2)</sup> |
| Abstrakte Audio und Video Wiedergabeliste | 0xBA05        | I               | I               | n/v             | n/v                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG-XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV (ENGL.)                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| Container MP4 (engl.)                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP Container                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3 G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

(1) tragbare Geräte, die wiedergegeben Audio-und/oder Videofunktionen genutzt werden, müssen mindestens eine der folgenden Formate unterstützen. Die folgende Tabelle stellt nicht die vollständige Liste der unterstützten Formate dar; Es stellt die Liste der häufig verwendeten Formate.

Finden Sie in der MTP-Spezifikation, Version 1.0 oder höher für die vollständige Liste der definierten Geräteeigenschaften **Objekt formatiert** .

(2) unterstützt die folgenden Objekteigenschaften ist für AbstractAudioAlbum Objekte obligatorisch:

-   Genre (0xDC8C)
-   Album Künstlers auswählen (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

Ein Gerät, das Format AbstractAudioAlbum und Bildformat unterstützt, möglicherweise optional Albumcover unterstützt. Albumcover ist die Grafik das Album RepresentativeSampleData Eigenschaft hinzufügen zu einem Objekt AbstractAudioAlbum angeschlossen.
Wenn ein tragbaren Gerät Albumcover unterstützt, muss das Gerät die folgenden Objekteigenschaften unterstützen:

-   PurchaseFlag (0xd901), eine Object-Eigenschaft in der Windows Media DRM 10 für tragbare Geräte MTP Extensions
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   Benutzer-Bewertung (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*Hinweise zum Entwurf*

-   "Picture Transfer-Protokoll (PTP) für digitale dennoch Foto Geräte," Version 1.0 des der PIMA15740: 2000 Picture Transfer Protocol-Spezifikation.

-   Das Media Transfer Protocol-Spezifikation, Version 1.0 ist unter *http://go.microsoft.com/fwlink/?LinkId=243145*verfügbar.

-   Zusätzliche Implementierungsdetails finden Sie in Windows 7 tragbaren Gerät aktivieren Kit für MTP, die unter <http://go.microsoft.com/fwlink/?LinkId=243146>verfügbar ist.

