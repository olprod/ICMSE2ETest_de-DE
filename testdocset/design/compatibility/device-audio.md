---
title: Device.Audio
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 8c98c341281d036e6b6ccca12808d851fbbddfe2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceaudio"></a>Device.Audio

 - [Device.Audio.APO](#device.audio.apo)
 - [Device.Audio.Base](#device.audio.base)
 - [Device.Audio.HardwareAudioProcessing](#device.audio.hardwareaudioprocessing)
 - [Device.Audio.HDAudio](#device.audio.hdaudio)
 - [Device.Audio.USB](#device.audio.usb)

<a name="device.audio.apo"></a>
## <a name="deviceaudioapo"></a>Device.Audio.APO

*Diese APO muss alle APO Tests übereinstimmen.*

### <a name="deviceaudioapobestpractices"></a>Device.Audio.APO.BestPractices

*Befolgen bewährte Methoden für Windows nicht möglich*

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

Alle möglich (Audio Processing-Objekte), sollten die im Whitepaper Windows APO Best Practices beschriebenen bewährten Methoden befolgen.

In diesem Whitepaper finden Sie auf MSDN: <http://go.microsoft.com/fwlink/?LinkId=716913>

### <a name="deviceaudioapomicarrayrawdata"></a>Device.Audio.APO.MicArrayRawData

*System Effekt im Pfad Capture bietet Rohdaten aus Mikrofon Array, wenn vom Client angefordert.*

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

Ist ein Mikrofon Array Verarbeitungsalgorithmus, sofern in einem Windows-System ausgeführt Verarbeitung von Audiosignalen-Objekt (APO) in ein Stream-Effekt (Umfassende) instanziiert Punkt im Pfad Capture einfügen, muss diese einzelne Audiostreams als Kanäle aus dem Array bereitstellen, wenn ein Client ein Format mit der Anzahl der Kanäle gleich der Anzahl von Mikrofon Elementen im Array anfordert. Dadurch wird die APO anzugebende Hardware Vergütung Verarbeitung und Mikrofon Array Verarbeitung an den Client, der die gesamte APO nutzt, ermöglicht aber auch Clients, die auf das Mikrofon Array verarbeitet werden, basieren befindet sich höher in audio Teilsystems Hardware Vergütung in der APO, aber nicht die Verarbeitung darin Array nutzen.

Es wird dringend für integrierte-Position Mikrofon Array (mehrere kombinierten Elementen) auf einem System empfohlen, eine optimierte wünschen "Speech Platform Gerät Recommendations Spezifikation" folgen.

<a name="device.audio.base"></a>
## <a name="deviceaudiobase"></a>Device.Audio.Base

*Dieses Gerät muss alle Basiskalender Tests übereinstimmen.*

### <a name="deviceaudiobaseaudioprocessing"></a>Device.Audio.Base.AudioProcessing

*Audiogeräte müssen ordnungsgemäße Verarbeitung Ermittlung und Steuerung Audio unterstützen.*

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

Treiber

Mindestens ein Treiber einen rohen-Modus unterstützen muss oder eine Standard-Modus Pin auf Rendern Pins. Zumindest muss ein Treiber Roh-Modus auf Stifte Capture unterstützen. Auf die Pins zur Verfügung gestellt, das System der Hardware muss Kooperation nach der Mischung Datenträger, wenn eine) mischen unterstützt oder b) Audio abnimmt. Darüber hinaus ist die Hardware stumm schalten, klicken Sie auf der Seite rendern muss angeben, wenn eine) gemischt oder b) audio Offloading unterstützt oder c) komprimiert.

Effekte Endpunkt muss Szenario neutral. Die Effekte Endpunkt müssen in allen Szenarien arbeiten. Effekte, die ein Szenario wie Real-Time Communications beschädigen oder nur von Vorteil sein, um ein Szenario muss der Effekt in den Modus Effekte platziert werden, die speziell für dieses Szenario sind. Die einzige zulässig Endpunkt Effekte (EFX) und unformatierte Modus Effekte (MFX im unformatierten Modus) Vergütung Lautsprecher und Mikrofon Schutz sind.

Treiber, die Unterstützung des ROHEN-Modus müssen außerdem folgende je nach Ihrer Treiber Struktur unterstützen:

-   Ein Treiber, ohne mischen unterstützt, Abladung Support (unterstützt mehrere gleichzeitige Modi jedoch nicht Offloading) umfassen eine KSNODETYPE\_SUM-Knoten und keine KSNODETYPE\_AUDIO\_ENGINE Knoten. Der Knoten hat eine einzelne input Verbindung, die von der Software Pin Factory und stellt den Punkt, wobei mehrere Instanzen des Drehbezugspunkts gemischt werden.

-   Die KSNODETYPE\_AUDIO\_ENGINE oder KSNODETYPE\_SUMME Knoten im Pfad zwischen der Software Pin Diensttypen und die Endpunkt-Brücke Pin sein muss. Der Knoten wird im gleichen Filter als die Software Pin Diensttypen sein.

-   Unterstützt der Knoten KSPROPERTY\_AUDIOSIGNALPROCESSING\_MODI.

    -   Für Port Treibern unterstützt der Miniport IMiniportAudioSignalProcessing. Ist der Port KSPROPERTY hinzufügen\_AUDIOSIGNALPROCESSING\_MODI, um die entsprechenden Pin.<br/><br/>

-   Ein Treiber, der unterstützt (mit-Offloading und/oder mehrere Unterhaltungsmodi) mischen, haben eine Pin Loopback zu unterstützen.

-   Loopback-Pins muss im neue Pin Kategorie KSPINCATEGORY\_AUDIOLOOPBACK. Die Topologie darf einen Pfad aus der Software Pin Factory an den Hersteller der Loopback Pin haben.

-   Ein Treiber, der nicht Mischen unterstützt unterstützen KSPROPERTY\_AUDIOSIGNALPROCESSING\_MODI für den Endpunkt Software Pin Factory.

    -   Für Port Treibern haben der Miniport IMiniportAudioSignalProcessing zu unterstützen. Ist der Port KSPROPERTY hinzufügen\_AUDIOSIGNALPROCESSING\_MODI, die entsprechenden Pin.<br/><br/>

-   Die Software Pin Factory Datenbereichen umfassen KSATTRIBUTE\_AUDIO\_SIGNALPROCESSINGMODE. Das Attribut nicht gekennzeichnet werden KSATTRIBUTE\_ERFORDERLICH.

-   Pin-Erstellung Code prüft für KSDATAFORMAT\_ATTRIBUTE in die Daten formatieren und Verarbeiten der KSATTRIBUTE\_AUDIOSIGNALPROCESSINGMODE falls vorhanden.

Für Port Treibern, muss der Treiber Implementierung newStream gespeichert auf IMiniportWaveRT, IMiniportWavePci oder IMiniportWaveCyclic KSDATAFORMAT unterstützen\_ATTRIBUTE. Nicht möglich

-   Wenn die Treiber STANDARDMÄßIG unterstützt wird die Verschiebung Pin STANDARD unterstützt.

-   Die möglich sind alle Modi unterstützen, die durch die Pin Offloading unterstützt werden.

-   Alle von der Host-Pin unterstützten Modi unterstützt.

Discovery

Treiber muss alle Audioeffekt über die FXStreamCLSID, FXModeCLSID, und FXEndpointCLSID möglich (oder Proxy möglich) verfügbar machen. Die möglich müssen eine präzise Liste der Effekte, die aktiviert sind mit dem System beim abgefragt senden. Treiber müssen unterstützen APO ändern und das System nur benachrichtigen, wenn es sich bei eine Änderung eines APO aufgetreten ist.

Loopback

Loopback Datenstroms sollten die Stream-Objekt aus der Lautsprecher darstellen. Treiber mit Hardware-Verarbeitung müssen das System einen genaue Loopback Stream bereit.

### <a name="deviceaudiobaseendpoints"></a>Device.Audio.Base.Endpoints

*Audio-Subsystems stellt eine korrekte aktuelle Systemkonfiguration*

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

**Alle Audiogeräte**

Alle Audiogerät, die von keiner der Audiogerät-Aufzählung APIs verfügbar gemacht wird muss den aktuellen Status aller Endpunkte entsprechend überhaupt widerspiegeln Zeiten, wenn das System eingeschaltet ist. Dies gilt auch dann, wenn das System im Standbymodus verbunden ist. Integrierten Lautsprecher und Mikrofon müssen arbeiten, während das System ordnungsgemäß funktioniert.

Wenn ein Endpunkt von keines der Geräteenumeration-APIs verfügbar gemacht wird und gibt der Zustand wieder, die verbunden werden und kann streaming, er funktionieren muss (Capture/gerendert werden können). Audio Endpunkte verfügbar gemachte müssen weiterhin verfügbar, sogar während der Systemstatus ändert sich wie:

 - Während der Power Datenquelle Änderungen aus externen Batterie oder umgekehrt

 - Beim Wechsel von einem integrierten GPU in einer Descrete GPU und umgekehrt

**Geräte, die die Verwendung von Windows 10 Mobile**

Der Audiotreiber muss nicht ausgeblendeten Stream Umleitung ausführen, routing, wechseln, aufteilen, mischen, Muxing anderen verfügbar gemachten oder ausgeblendet logische Audiogeräte, Applikationen oder anderer Entitäten aber sie müssen sicherstellen, dass Audiodaten aus der Endpunkt-audio-System für ein bestimmtes Gerät logische nur an das entsprechende logische Gerät gerichtet ist, die die Anwendung mit der Windows-Benutzer in der Systemsteuerung von Windows Sound festgelegt, streaming ist.

**Kopfhörer Connectors, Lautsprecher Connectors, HDMI Connectors, DisplayPort Connectors, Geräte über eine Dockingstation drahtlosen verbunden und Verbindung mit Netzwerk-Audiogeräte**

Der Treiber muss den Verbindungsstatus der entsprechenden Geräte ordnungsgemäß express.

Wenn der Anschluss nicht angeschlossen ist, oder das drahtlose oder Netzwerkgerät befindet sich nicht in einer verwendbar Verbindungsstatus und anschließend der Treiber muss entweder:

1.  Legen Sie die KSJACK\_BESCHREIBUNG. IsConnected-Element auf "false", oder

2.  Deaktivieren Sie die KS Filter-Schnittstelle

    -   Für AvStream Treiber: deklarieren eine Verbindung wird getrennt durch die Implementierung der folgenden Eigenschaften und Ereignisse:

        -   KSPROPSETID\_Jack

            -   KSPROPERTY\_JACK\_BESCHREIBUNG

            -   KSPROPERTY\_JACK\_DESCRIPTION2

        -   KSEVENTSETID\_PinCapsChange

            -   KSEVENT\_PINCAPS\_JACKINFOCHANGE

    -   Für Port Treibern: Aufheben der Registrierung der Subdevice Port-Klasse durch Aufrufen von PcUnregisterSubdevice

In ähnlicher Weise bei der Anschluss angeschlossen ist, oder das drahtlose oder Netzwerk angeschlossen ist ein in einem verwendbaren Zustand, klicken Sie dann der Treiber muss entweder:

1.  Legen Sie die KSJACK\_BESCHREIBUNG. IsConnected-Element auf "true", oder

2.  Aktivieren Sie die KS Filter-Schnittstelle:

    -   Für AvStream Treiber: Deklarieren Sie eine Verbindung durch die Implementierung der folgenden Eigenschaften und Ereignisse angeschlossen ist:

        -   KSPROPSETID\_Jack

            -   KSPROPERTY\_JACK\_BESCHREIBUNG

            -   KSPROPERTY\_JACK\_DESCRIPTION2

        -   KSEVENTSETID\_PinCapsChange

            -   KSEVENT\_PINCAPS\_JACKINFOCHANGE

    -   Für Port Treibern: registriert die Subdevice Port-Klasse durch Aufrufen von PcRegisterSubdevice

Wenn der Treiber die KSJACK ändert\_BESCHREIBUNG. IsConnected-Member, Generieren der Treiber muss das Ereignis KSEVENTSETID\_PinCapsChange / KSEVENT\_PINCAPS\_JACKINFOCHANGE.

Das oben beschriebene Verhalten wird sichergestellt, dass Windows leitet der Connector oder Gerät audio, nur, wenn es streaming tatsächlich zur Verfügung steht.

Für Connectors und drahtlose oder Netzwerkgeräte, Mechanismus (a) bevorzugt werden soll. Dadurch das Gerät im System Benutzeroberfläche (z. B. der Signalton für den Windows-Systemsteuerung) angezeigt, obwohl es möglicherweise nicht sofort verwendet werden, und es wird sichergestellt, dass das Gerät mit dem richtigen Status angezeigt wird.

Für Geräte, die in einer Dockingstation entfernbar sind, empfiehlt sich Mechanismus (b).

Für Connectors, die auf einer Dockingstation entfernbar sind, wird Mechanismus (b) empfohlen, um die Anlage der Dockingstation widerzuspiegeln. Mechanismus (a) wird empfohlen, um anzugeben, ob der Anschluss angeschlossen ist.

*Design Notes:* Finden Sie im Whitepaper Microsoft LF HD Audio Pin Programming Konfigurationsrichtlinien für zusätzliche Clarifications für die angegebene Jack Connectors, die Erkennung von Jack erfordern.

http://go.Microsoft.com/fwlink/?LinkId=716908

### <a name="deviceaudiobasefunctionspostupgrade"></a>Device.Audio.Base.FunctionsPostUpgrade

*Audiogeräte Funktion ordnungsgemäß, nachdem das Betriebssystem aktualisiert wurde*

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

Zur Unterstützung der häufig aktualisieren das Windows-Betriebssystem, sollten alle Audiotreiber ordnungsgemäß im Rahmen des Prozesses aktualisieren Windows migrieren. Nach Aktualisierung das Audiogerät ordnungsgemäß funktioniert und sollte gleich oder größere Funktionalität wie sie vor dem Upgrade haben.

Um diese Anforderung erfüllen, sollten keine Funktion (Dateien, Registrierungseinträge usw.) außerhalb eines Treiberpakets mit Ausnahme von Betriebssystemkomponenten oder andere Treiber im System installiert abhängig. Beispielsweise Treiber Anpassungen (z. B. Voreinstellungen, Mikrofon-Array Geometrie Info, OEM-Anpassung) zu im Audiotreiber-Paket enthalten, anstatt direkt auf dem System werksseitige installiert. Im Idealfall würde die Installation des Treibers deterministisch mit nur INF-Datei Direktiven installiert werden.

### <a name="deviceaudiobasehardwarearchitecture"></a>Device.Audio.Base.HardwareArchitecture

*Audio-Subsysteme müssen eine kompatibel mit Windows-Technologie verwenden.*

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

**Integrierte Audiogeräte**

Ein *integrierten Audiogerät* ist, eine interne Komponente unterstützt, oder ein Port, der ausschließlich für Media-Inhalten verwendet wird. Hier sind einige Beispiele für integrierte Audiogeräte aus:

-   Lautsprecher

-   Mikrofone und Mikrofon arrays

-   Analoge audio-Anschlüsse (Kopfhöreranschluss, Zeile, Zeile in Mikrofon Jack)

-   S/PDIF

-   Digitale Ausgaben wie HDMI und DisplayPort

Für diese Geräte audio Hardwarearchitektur verwendet werden können Sie mindestens *eine* der folgenden ist true bereitgestellt:

-   Das Gerät bietet grundlegende Funktionen für aller Endpunkte bei Verwendung mit einer der vom audio-Klasse Treiber mit Windows gepackt.

-   Ein Treiber ist über Windows Update, die Grundfunktionen für alle das Gerät Endpunkte aktiviert wird.

**Extern angeschlossenen Audiogeräte**

Eine *extern Audiogerät angeschlossen* ist eine, ist nicht mit dem System integriert und verfügt über eine Verbindung, die speziell für Audio- oder auf dem Installationsmedium nicht zur Verfügung. Hier sind einige Beispiele für externe Audiogeräte aus:

-   USB-audio

-   Bluetooth-audio

Für diese Geräte audio Hardwarearchitektur verwendet werden kann, aber es wird dringend empfohlen, diese Geräte den standard-Spezifikationen entsprechen und grundlegende mit einem Windows-Treiber für audio-Klasse Funktionalität. Auf bestimmten Windows-Geräten, die die Installation von einem Drittanbieter-Treiber keine zulassen, ist die einzige Möglichkeit für ein externes Audiogerät-Funktion, wenn sie mit einer Klassentreiber kompatibel ist.

**Alle Audiogeräte**

Wenn die Plug & Play-ID eines Audiogeräts mit einer der vom audio-Klasse Treiber gepackt mit Windows kompatibel ist, muss das Gerät Grundfunktionen für alle Endpunkte, Treiber nutzen können.

Ein Gerät stellt die *Grundfunktionen* bereit, wenn alle die Windows-Hardware-Zertifizierung Audiogerät erfüllt.

**Weitere Informationen**

[Audiogerät Technologies](http://msdn.microsoft.com/en-us/library/windows/hardware/gg454527.aspx): http://go.microsoft.com/fwlink/?LinkId=716909

### <a name="deviceaudiobasepowermanagement"></a>Device.Audio.Base.PowerManagement

*Verwandte Power Management Spezifikationen muss Audiogerät entsprechen.*

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

**Alle Audiogeräte und Treiber**

Audiogeräte müssen Audio Gerät Klasse Power Management Verweis Spezifikation entsprechen, die Definitionen von der Power-Gerätestatus (D0 – D3) für diese Geräte zur Verfügung stehen. Die Spezifikation wird auch die Funktion des Geräts in jedem Power-Status und die möglichen Reaktivierung Ereignisdefinitionen für die Klasse erwartet behandelt. Das Gerät und Treiber müssen Support für Power Zustand D3 implementieren. Unterstützung für andere Power Management-Gerätestatus ist optional.

**Bluetooth-Audiogeräte**

Bluetooth-Audiogeräte müssen ein HCIDisconnect führen Sie vor dem Herunterfahren.

Die HCIDisconnect ist erforderlich, damit die rechtzeitige Benachrichtigung an das System ermöglicht, dass das Gerät nicht mehr verfügbar ist. Hiermit wird umgeleitet audio an einen alternativen Empfänger audio nahtlos, wenn das Audiogerät Bluetooth ausgeschaltet wird.

**Verweise**

ACPI-Spezifikation: <http://www.acpi.info/>

Bluetooth-Spezifikationen: <https://www.bluetooth.org/en-us/specification/adopted-specifications>

MSDN: http://go.microsoft.com/fwlink/?LinkId=716910

### <a name="deviceaudiobasesamplepositionaccuracy"></a>Device.Audio.Base.SamplePositionAccuracy

*Audiotreiber Berichte Rendern Beispiel Position mit definierten Genauigkeit für die Synchronisierung des Stream-Objekt.*

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

Für alle Endpunkte audio berichtet IAudioClock::GetPosition Zeitstempel mit:

-   | Bias | &lt;= 1 ms

-   | skew | &lt;= 1%

-   Jitter &lt;= 1 ms

Dies gilt sowohl Rendern und für alle Formate erfassen Modi und Pins (Host, Verschiebung, Loopback).

### <a name="deviceaudiobasestreamingformats"></a>Device.Audio.Base.StreamingFormats

*Audio-Subsysteme müssen von Windows unterstützten Formate verwenden.*

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

**Alle Audiogeräte**

Dies gilt für Eingabe (Erfassung) und Ausgabegeräten (Render).

Ein Audiogerät muss mit Windows kompatiblen Unterstützung für mindestens einen PCM (Pulse Code Modulation) codierte Format verfügbar machen.

Mindestens eine der folgenden Container und Bittiefen muss verwendet werden:

-   8-Bit-Version (ohne Vorzeichen)
-   16-Bit-
-   20 Bit in einem 24-Bit-container
-   24-bit
-   24-Bit in einem 32-Bit-container
-   32-Bit-

Die Beispiele muss die ganze Zahl oder IEEE-754 Float.

Alle Samplingrate funktioniert mit der Windows-audio-Pipeline. jedoch wird empfohlen, 48 kHz und 44,1 kHz für eine optimale Leistung Leistung in Media Szenarien unterstützt werden.

Wenn das Gerät Eingabe- und Ausgabeparameter Funktionen unterstützt, muss das Audiogerät unabhängige Auswahl der Formate unterstützen und gleichzeitige streaming am willkürlich ausgewählten Formate unterstützen.

Channel-Konfigurationen muss mindestens eine der folgenden:

-   (Mono)
-   (Stereo)
-   2.1
-   3.1
-   4.0
-   5.0
-   5.1
-   7.1

Wenn das Audiogerät mehrfach audio-Formate unterstützt, muss der Treiber Audiogerät Channel Masken konsistent mit den Inhalt und die aktuelle Konfiguration des ausgewählten Lautsprecher bewältigen.

Loopback-Pins sollte das Format der ihren entsprechenden Standard Modus Host Render-Pins entsprechen.

**Digitale Geräte mit externen Verbindungen**

Für Geräte, in eine Beziehung Quelle und Empfänger (wie HDMI und Bluetooth) es vorhanden ist, muss ein Source-Gerät unterstützen und verfügbar machen alle erforderlichen Empfänger Formate. Beispielsweise HDMI erfordert ein Empfänger unterstützen, 48 kHz *oder* 44,1 kHz; aus diesem Grund muss eine Datenquelle HDMI (mindestens) unterstützen, beide 48 kHz *und* 44,1 kHz, damit alle HDMI Empfänger Gerät verbunden wird ordnungsgemäß. Es wird empfohlen, dass Quellen alle möglichen Empfänger Formate für die beste benutzerumgebung unterstützen.

**Hardware-Beschleunigung (Verschiebung)**

Geräte, die ein DSP für audio-Verschiebung nutzen müssen eine Obermenge von Formaten unterstützen, die durch die Pin Host (System) auf demselben Gerät unterstützt werden. Dadurch wird sichergestellt, dass wird nach Möglichkeit der Arbeitslast und unnötige zurückgreifen auf die Host-Pin Verbindung vermeidet.

**Verweise**

MSDN: <http://go.microsoft.com/fwlink/?LinkId=716911>

MSDN: <https://msdn.microsoft.com/en-us/library/windows/hardware/ff537083.aspx>

### <a name="deviceaudiobasesupportwindowsapis"></a>Device.Audio.Base.SupportWindowsAPIs

*Treiber sollte mit allen Windows-Audio-APIs ordnungsgemäß funktionieren.*

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

Treiber sollten ordnungsgemäß streamen, wenn eines der Windows-Audio-APIs verwenden. Dies umfasst, ist aber nicht auf die folgenden beschränkt:

-   Media Foundation-APIs

<!-- -->

-   XAudio2-APIs

-   WASAPI

-   MediaCapture-APIs

### <a name="deviceaudiobasevolumecontrol"></a>Device.Audio.Base.VolumeControl

*Audiotreiber Lautstärkeregler linear und angemessene Lösung.*

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

Signalisieren Sie Antwort (gemessen nach Stromversorgung oder digitalen Audiosignals) Änderungen in Linearität mit den Lautstärkeregler innerhalb der Toleranz 3 %. Beispiel: eine Volume Schieberegler Änderung von 10 dB führt eine gemessene Volumen Änderung zwischen 9.7 dB und 10.3 dB + oder – 0.3dB.

Topologie Volume Knoten müssen eine Auflösung gleich oder besser als 1,5 dB haben und implementieren die Unterstützung für Lautstärkepegel gemäß Definition im Windows-Treiberkits Treiber.

Finden Sie unter Windows-Treiberkits "KSPROPERTY\_AUDIO\_VOLUMELEVEL" für weitere Details.

<a name="device.audio.hardwareaudioprocessing"></a>
## <a name="deviceaudiohardwareaudioprocessing"></a>Device.Audio.HardwareAudioProcessing

*HardwareAudioProcessing*

### <a name="deviceaudiohardwareaudioprocessingaudiohardwareoffloading"></a>Device.Audio.HardwareAudioProcessing.AudioHardwareOffloading

*Hardware, dass unterstützt audio Render Verarbeitung übergeben muss diese Anforderung erfüllen.*

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

**Eine hardwarelösung ausgelagerten audio Render-Verarbeitung unterstützt, muss der Treiber offen, ein KS Filter und einer einzelnen KSNODETYPE\_AUDIO\_Knoten mit entsprechenden Pin Diensttypen ENGINE verbunden.**

Wenn eine Hardware-Lösung unterstützt die Verschiebung von Audiodaten Verarbeitung, mischen oder Decodierung rendern, muss der Treiber einen KS Filter verfügbar machen. Für jeden Pfad Rendering, Filter, Hardware unterstützt, Verschiebung des Treibers verfügbar machen einer einzelnen KSNODETYPE\_AUDIO\_ENGINE-Knoten, nur die folgenden Pin Diensttypen direkte Verbindung:

-   Zwei KS Auffangen Diensttypen Pin verwenden.

-   eine einzelne KS Quelle Pin Factory für Verweis Stream-Unterstützung

**Wenn ein Treiber eine KSNODETYPE verfügbar macht\_AUDIO\_ENGINE-Knoten, der Treiber und Hardware müssen Base-Funktionalität unterstützen.**

Wenn ein Treiber eine KSNODETYPE verfügbar macht\_AUDIO\_ENGINE Knoten der Treiber und Hardware müssen unterstützt der folgenden Funktionen:

-   Audiomixer mit mindestens 3 gleichzeitige Eingaben (2-Offloading und 1 Hostprozesse)

-   Lautstärke und stumm Funktionen vor und nach dem gemischt

-   Verweisstream (Unterstützung für das Senden von Audiodaten der stream nach der Mischung zurück an den Windows-audio-Stapel)

-   Der bereitgestellten Verweisstream sollte die endgültige Ausgabe an, in das Audiogerät werden oder wenn Codierung vor der Codierung stattfindet.

**Wenn Hardware Softwaremessungsdatenbank reporting (Unterstützung unterstützt für das Abfragen pro Stream Spitzenzeiten Werte vor & nach der Mix)**

-   Für Stream Softwaremessungsdatenbank (vor dem Mischen), sollten Messung Ebenen hinter der Umfassende und vor Lautstärkeregler gemeldet werden

-   Für den Endpunkt Softwaremessungsdatenbank (nach dem Mischen), werden Messung Ebenen berichtet:

    -   Bevor Sie Lautstärkeregler und EFX, wenn die EFX ein Encoder ist

    -   Nach der EFX und vor Lautstärkeregler, wenn die EFX kein Encoder ist

**Wenn ein Treiber eine KSNODETYPE verfügbar macht\_AUDIO\_ENGINE-Knoten, der Treiber muss bestimmte Pin Diensttypen verfügbar zu machen.**

Wenn ein Treiber eine KSNODETYPE verfügbar macht\_AUDIO\_ENGINE-Knoten, der Treiber muss die folgenden Pin Diensttypen verfügbar zu machen:

-   Prozess Pin-Hostinstanz

    -   Muss über mindestens eine Instanz unterstützen

-   Abladung von Pin-factory

    -   Muss mindestens zwei Instanzen unterstützen

-   Loopback-Pin-factory

    -   Muss mindestens eine einzelne Instanz unterstützen

Darüber hinaus muss Folgendes erfüllt sein:

-   Loopback-Pins müssen:

    -   Verfügen über eine "mögliche globale Instanzen" mindestens 1

    -   Unterstützung von mindestens 1-Instanz, unabhängig davon, was im System vor sich geht

-   Zum Aktivieren werden Szenarien wie Cross-ausblenden, Offloading-fähige Endpunkte 1 Loopback Pin Instanz + 1 Pin-Hostinstanz unterstützen müssen + folgender isoliert, sofern keine andere Abladung von Endpunkten zur Zeit verwendet:

    -   Eine der unterstützten PCM Format + eines unterstützten PCM-Format (das gleiche oder andere)

<!-- -->

-   Die Loopback Pin muss unterstützen.

    -   Die Hardware Mix-format

    -   Das Geräteformat (das öffentlich aus den Endpunkt Eigenschaftenspeicher abgefragt werden kann)

**Wenn ein Hardware Lösung unterstützt ausgelagert Audio Verarbeitung rendern, muss die gleiche Funktionalität bereitgestellt, die in der Hardware (z. B. Verarbeitung, Effekte usw.) auf dem Host Pin sowie verfügbar sein.**

Um ein einheitliches Benutzererlebnis bieten und verhindern Sie Verwechslungen aus, wenn ein Benutzer aktiviert oder Funktionen, die existiert in nur Hardware- oder nur konfiguriert, müssen die bereitgestellte Funktionen in Hardware und Software entsprechen.

**Andere Überlegungen**

Ausgelagerten Audiogeräte müssen akzeptieren und ordnungsgemäß bis zum Ende des Segments (EOS) Kommunikation vom Betriebssystem reagieren.

Wenn ein Hardware Lösung unterstützt ausgelagert Audio Verarbeitung rendern, muss der Treiber IMiniportAudioEngineNode und IMiniportStreamAudioEngineNode2 implementieren

IMiniportAudioEngineNode enthält eine Liste der Methoden im Zusammenhang mit der Zielgruppenadressierung des audio-Modul Knotens über KS Filter Handle Offloading KS-Eigenschaften. Eine Miniporttreiber WaveRT benötigten Miniport-Klasse nicht nur von IMiniportWaveRT Schnittstelle erbt, muss es auch IMiniportAudioEngineNode Schnittstelle erben und alle definierten Methoden implementieren.

<a name="device.audio.hdaudio"></a>
## <a name="deviceaudiohdaudio"></a>Device.Audio.HDAudio

*Dieses Audiogerät verwendet den HD-Audiotreiber.*

### <a name="deviceaudiohdaudiohdaudiospeccompliance"></a>Device.Audio.HDAudio.HDAudioSpecCompliance

*HD Audio-Codec für Audio muss der Intel High Definition Audio-Spezifikation entsprechen.*

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

Ein **High Definition Audio Codec** müssen die folgenden Spezifikationen entsprechen:

-   Intel High-Definition-Audio-Spezifikation und DCNs

-   Plug & Play-Richtlinien für High-Definition-Audiogeräte

Darüber hinaus muss der Code die folgenden Features implementieren, der von der Intel High Definition Audio-Spezifikation nicht unbedingt erforderlich sind:

Lautsprecher Vergütung ist der einzige gültige Szenario für Audiosignal Verarbeitung eines Audiostreams durch einen Codec, und klicken Sie dann es gilt nur, wenn die Lautsprecher verdrahtete auf die komplexe Pin, die den Verarbeitungsknoten (wie integrierte Laptop-Lautsprecher) enthält. Dies gilt nicht für die Entschlüsselung der geschützte Audiostreams.

<ol style="list-style-type: decimal">
<li><p>Wenn alle einem HDAudio Codec-Widgets in der duldet Verarbeitungsstatus konfiguriert sind, führt der Codec keine nichtlinearen oder Time-Variante Verarbeitung von passieren audio-Streams.</p></li>
<li><p>Ein HDAudio Codec muss nur über die HDAudio Bus-Controller zugreifen können. Der Codec muss registriert oder andere Hardware Mechanismen, die über Arbeitsspeicher oder e/a-Adressraum zugänglich sind nicht verfügbar machen. Dies ist nicht HDMI oder DisplayPort umfassen. HDMI oder DisplayPort finden Sie auf der HD audio HDMI DCN.</p></li>
<li><p>Modem- und audio-Funktionalität darf nicht kombiniert werden. Obwohl der gleiche Teil Silicon Modem und Audiogeräte untergebracht werden kann, müssen die Funktionen getrennter Geräte und müssen keine Ressourcen Software oder Hardware (wie MDE oder DACs) freigeben.</p></li>
<li><p>Wenn die HD Audio-Verknüpfung ausgeführt wird (in D0 ist HD Audio Controller), muss auf Befehle, auch wenn heruntergefahren alle erforderlichen Power-Management-Gerätestatus HD Audio Codecs reagieren. Tatsächlich muss der digitale Abschnitt des Codecs eingeschaltet bleiben.</p></li>
<li><p>Codecs muss auf ein Verb reagieren, auch wenn auf eine nicht vorhandene Widget adressiert ist oder wenn das Verb selbst ungültig ist.</p></li>
<li><p>Gruppieren von Knoten Funktion benötigen Knoten-IDs im Bereich von 0 bis 127. Diese Beschränkung gilt nicht für Knoten-IDs für Widget-Knoten.</p></li>
<li><p>Sind die Standarddaten in die HD Audio Codec Pin Konfiguration Register nicht so dargestellt die Hardwarefunktionen und die Konfiguration Standard registriert darf nicht null sein (Nullen).</p></li>
<li><p>Eine Funktionsgruppe in einem HDAudio Codec muss eine ID ungleich NULL Subsystem verfügbar machen. Die BIOS überschreibt die ID Subsystem bei Bedarf. Wenn das BIOS können nicht die ID Subsystem Programm aus, oder wenn dies der Fall falsch ist, muss die Hardware einen Standardwert angeben, herstellerspezifische Subsystem-ID.</p></li>
<li><p>Jede HD Audio Codec Port stellt eine Verbindung her, nur einen einzigen Audioquelle Ziel oder Jack. Kompatibilität mit der Klassentreiber führen Sie nicht Double-nach-oben Sie auf Eingabe- oder Ports in Möglichkeiten, die an den Klassentreiber, durch die Informationen in die Pin Konfiguration Register offen gelegt werden. Entwürfe, in denen GPIOs unter Kontrolle der Treiber Drittanbieter-Funktion verwendet müssen eine geeignete Hardware-Konfiguration standardmäßig bei der Klassentreiber geladen wird.</p></li>
<li><p>HD Audio Codec-Treiber muss nicht verlassen einer Funktionsgruppe in D3Cold Zustand bei entladen. Durch das Verlassen eines IRP Handler für IRP_MJ_PNP/IRP_MN_REMOVE_DEVICE benötigen ein HD-Audiocodec Treiber:</p>
<ol style="list-style-type: lower-alpha">
<li><p>Gespeicherte oder den aktuellen Status Power der Funktionsgruppe erkannt</p></li>
<li><p>Wenn diese aktuellen Funktion Power Gruppenstatus D3 kalt war, muss der Treiber es in einen anderen versetzt geändert haben. Die Funktion Power Gruppenstatus nach dem verlassen muss D3 sein.</p></li>
</ol></li>
</ol>

**HD Audio Controller müssen die folgenden Anforderungen erfüllen:**

1.  Intel High Definition Audio Controller-Spezifikation

2.  Zur Einhaltung der Spezifikation für zukünftige Überarbeitungen aktualisiert werden

3.  Mit der neuesten HD Audio Spezifikation ECRs gemäß den Richtlinien, um neue Hardware entsprechen.

4.  HD Audio-Hardware, die mit HD Audio Spezifikation, Version 1.0 entspricht muss die richtige Versionsnummer in die entsprechenden Register festgelegt. Die Register VMAJ und VMIN müssen die Hauptversionsnummer 01 h und eine Nebenversionsnummer des 00 h angeben.

<a name="device.audio.usb"></a>
## <a name="deviceaudiousb"></a>Device.Audio.USB

*Dieses Audiogerät verwendet den USB-Audiotreiber.*

### <a name="deviceaudiousbhidcontrols"></a>Device.Audio.USB.HIDControls

*USB-Audiogerät verwendet Audiosteuerelemente USB HID zum Speichern des Betriebssystems Benutzerinteraktionen mit dem Gerät informiert.*

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

USB-Audiogeräte müssen Spezifikation-kompatiblen HID USB HID verwenden, um grundlegende Funktionen zu steuern. Wenn Regulierung Lautstärkeregler auf dem USB-Audiogerät implementiert werden, muss es sich selbst als Consumer-Steuerelement Gerät (Usage 0 x 01) gemäß der Definition in der Consumer-Seite 0x0C in den Tabellen des USB-Verwendung für HID Stromversorgungseinheiten, Version 1.1, deklarieren und in Windows Audiosteuerelemente HID-basierte Unterstützung.

Kommunikationsgeräte, die eine USB-HID-Schnittstelle implementieren, müssen mit der USB-Gerät Klassendefinition für Geräte HID (Human Interface), Version 1.1 und USB-Nutzung Tabellen für HID Stromversorgungseinheiten, Version 1.12 kompatibel sein.

Geräte sind nicht reservierte Verwendungen von jeder Standard Usage Seite verwenden.

Weitere Informationen zum Entwurf finden Sie unter "HID Audio-Steuerelemente und Windows" am <http://go.microsoft.com/fwlink/?LinkId=40491> und Windows-Treiberkits, "AUSGEBLENDET und Windows".

### <a name="deviceaudiousbusb"></a>Device.Audio.USB.USB

*USB-Audiogerät muss UAA USB-audio Entwurfsrichtlinien folgen.*

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

Beschreibung: Ein USB-Audio-basierte Audiogerät in einer eigenständigen externe Formfaktor oder ein AVR oder andere Variationen entspricht der Device.Audio.Base.HardwareArchitecture.

Besondere Aufmerksamkeit sollte wie folgt vorgenommen werden:

-   USB-Audiogerät muss an den Zweck des Geräts entsprechend der USB-Spec <http://www.usb.org/developers/devclass_docs/termt10.pdf>Descriptor ordnungsgemäß festgelegt werden.

-   Ein extern angeschlossenen USB-Basis Mikrofon Array Gerät Klassendefinition die USB-Gerät für Audio-Geräte 2.0 entsprechen, und muss gemäß den Richtlinien unter "Mikrofon Array Support in Windows Vista" implementiert werden Das Gerät muss sich selbst und seine Funktionen entsprechend der Entwurfsrichtlinien für die in den Microsoft USB-Audio Mikrofon Array Entwurfsrichtlinien gemeldet werden.

**Referenz:**

Universal Serial Bus-Gerät Klassendefinition für Audio Geräte 2.0 unter [ *http://www.usb.org/developers/docs/devclass\_Dokumente /*](http://www.usb.org/developers/docs/devclass_docs/)
