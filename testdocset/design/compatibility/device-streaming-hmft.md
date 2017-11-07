---
title: Device.Streaming.HMFT
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 22f4c577b2cf087e1d293cc21fbc3c4db1512e76
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Streaming.HMFT

 - [Device.Streaming.HMFT](#device.streaming.hmft)
 -->
 
<a name="device.streaming.hmft"></a>
##Device.Streaming.HMFT

### <a name="devicestreaminghmftdecoding"></a>Device.Streaming.HMFT.Decoding

*Hardware Media Foundation transformieren (HMFT) muss video Decodierung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**Unterstützte Formate**

Video Decoder HMFT wird nur für MPEG-4 Teil 2 und MJPEG unterstützt. Beide Formate werden If-implementiert.

**Media Foundation Compliance** Der video Decoder Hardware Media Foundation transformieren (HMFT) muss die folgenden Schnittstellen Media Foundation transformieren (MFT) vollständig entsprechen:

-   IMFTransform
-   IMFMediaEventGenerator
-   IMFShutdown
-   IMFQualityAdvise
-   IMFRealTimeClientEx

HMFT-video-Decoder muss Media Foundation Arbeit Warteschlange Support (keine Erstellen von Threads) über **IMFRealTimeCLientEx::SetWorkQueue**verwendet werden. Dadurch wird sichergestellt Folgendes:

-   Multimedia Class Scheduler-Dienst (MMCSS) Unterstützung für Wiedergabe und Aufnahme/codieren
-   Verbesserte Core Skalierbarkeit

Der HMFT-video-Decoder **IMF2DBuffer2** -Unterstützung für erweiterte Sicherheit, aber auch mit input Puffer vom Typ **IMF2DBuffer**und **IMFMediaBuffer** arbeiten, in dieser Reihenfolge der Priorität.

**DirectX Rendering**

Der video Decoder HMFT muss DirectX (DX) 9 und unterstützen, DX11 Geräte, und es muss Kopien an- und Abmelden DX11 Komponenten vermeiden.

Klicken Sie auf MFT\_festgelegt\_D3D\_Manager, der video Decoder HMFT muss zuerst Abfragen für DirectX Graphics Infrastruktur (DXGI)-Manager und dann für D3D9 Manager Abfragen, wenn DXGI Manager nicht gefunden wird.

HMFT-video-Decoder muss Unterstützung der vom System Arbeitsspeicher Ausgabe, da einige Transformationen in der Pipeline nur System Speicherpuffern unterstützen können.

Wenn der HMFT video Decoder auf einer GPU basiert, muss es DX11 unterstützen.

**Speicherauslastung**

Der video Decoder HMFT muss eine asynchrone MFT sein. Dadurch wird den Speicher Arbeitssatz um etwa 50 Prozent reduziert.

**Wert der vertrauenswürdigen Zertifizierungsstelle und Überprüfung**

Der video Decoder HMFT muss den Prozess Wert Zertifizierung vertrauenswürdige und Überprüfung unterstützen, gemäß über das Windows Hardware Zertifizierung-Kit.

Jede HMFT-video-Decoder muss als separate binäre bereitgestellt werden und einzeln signiert werden muss.

Video Decoder HMFT müssen keine Unterstützung für mehr als eine Komprimierung standard ankündigen.

Alle HMFTs müssen die folgenden Attribute des Media Foundation beim Registrieren der MFT mit dem System festlegen:

-   MFT\_ENUM\_HARDWARE\_URL\_Attribut
-   MFT\_ENUM\_HARDWARE\_HERSTELLER\_ID\_Attribut

**Format-Anforderungen**

Video Decoder HMFT müssen nicht zugänglich gemacht Unterstützung für Posteingang Formate von DirectX Video Acceleration (DXVA) (h. 264, h. 264, WMV, MPEG2) unterstützt.

**Wenn implementiert**: HMFT-video-Decoder für MPEG-4 Teil 2 einfacher und erweiterte einfache-Profil (sofern es sich um eine globale Motion Vergütung (GMCH) nicht unterstützt wird und klicken Sie dann der Medientyp abgelehnt werden muss, damit den Softwaredecoder für die Wiedergabe verwendet werden können,) unterstützt, und alle Ebenen.

-   Der Decoder muss vollständig konform Spezifikationen, die für das Format definiert sind.

-   Der MPEG-4 Teil 2 Decoder muss darüber hinaus vollständig unterstützen h. 263 Baseline Inhalt und Unterstützung für diesen Medientyp ankündigen.

Zusätzlich zu den oben beschriebenen Anforderungen wird empfohlen, die die Nachbearbeitung für deblocking und deringing Decoder-Unterstützung.

Lieferanten vorsehen andere HMFTs video Decoder für die Formate nicht werden unterstützt Posteingang, aber es sind keine Überprüfungstests oder Logozertifizierung verfügbar.

**Hinweis:** Die Empfehlungen und Anforderungen, die in diesem Dokument definiert sind gelten für alle Formate.

**Funktionalität**

Der video Decoder HMFT muss die folgenden Funktionen unterstützt:

-   Dynamische-Format und Auflösung Änderungen
-   Modi (Wiedergabe Rate-Steuerelement, Durchforstung Modus) zu verleiten und seek

**Interlaced-Unterstützung**

Der HMFT-video-Decoder muss das Eingabeformat für beide interlaced und progressiv Bit Streams unterstützen. Es muss nicht aufheben der Interlaced. Es kann inverse Telecine (IVTC) unterstützen.

**Mehrere Instanzen**

Der video Decoder HMFT muss mehrere Instanzen der Decoder unterstützen in parallel (prozessinternes Protokoll und außerhalb des Prozesses) mehrere gleichzeitige Videowiedergabe Datenströme in demselben oder auf unterschiedlichen Anwendungen aktivieren.

**Hinweise zum Entwurf**

Der HMFT-video-Decoder muss installiert und deinstalliert werden über einen Gerätetreiber, der Windows-sicherheitsanforderungen erfüllt.  Der Treiber muss nicht dazu, dass das Betriebssystem abstürzt oder hängen und müssen nicht Arbeitsspeicher Verstöße zulassen.

Jeder HMFT-Komponente muss eine Separate binary, einzeln zertifizierten und signierten.

### <a name="devicestreaminghmftencoding"></a>Device.Streaming.HMFT.Encoding

*Hardware Media Foundation transformieren (HMFT) muss video Codierung unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>10 Windows Mobile x86</p>
<p>10 Windows Mobile x64</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

**A. h. 264-Codierung**


Wenn Ihre Hardware h. 264-Codierung unterstützt, müssen Sie folgende Schritte ausführen:

**A. 1 Eingabeformat-Unterstützung**

Der Encoder muss NV12 Format für input Frames unterstützen. Optional kann der Encoder IYUV unterstützen und YUY2 formatiert.

Encoder muss Support für die [IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx), [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx), implementieren und [IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx) Media Puffer-Schnittstellen.

**A. 2-Profil-Unterstützung**

Der Encoder muss Daten aneinander erstellen Ausgabe Inhalte, das auf die folgenden Profile übereinstimmt:

 - Geplante Profil
 - Eingeschränkte Baseline-Profil
 - Hauptfenster Profil
 - Eingeschränkte hohe Profil

Der Encoder muss Daten aneinander entsprechenden Syntax Kopfzeilenelemente signalisieren, dass er auf die oben aufgeführten Profile codiert wird, um zu generieren.

**Support-Anforderungen für a. 3-Schnittstelle**

Der h. 264-Encoder muss die folgenden Schnittstellen unterstützen:

A.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

Implementierung der folgenden Methoden der [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx) -Schnittstelle ist erforderlich:

A.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

A.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

A.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

A.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

A.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

A.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

A.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

A.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

A.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

A.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

A.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

A.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

Muss die MEEncodingParameters Ereignisbehandlung

A.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

A.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

A.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

A.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

A.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

A.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

A.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

Der Encoder muss bestimmte Methoden und Eigenschaft GUIDs der ICodecAPI-Schnittstelle unterstützt.

A.3.2.1 erforderlichen Methoden

Implementierung der folgenden Methoden der ICodecAPI-Schnittstelle ist erforderlich:

A.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

A.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

A.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

A.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

A.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

A.3.2.2 erforderliche Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist erforderlich

A.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

A.3.2.2.2 CODECAPI\_AVEncCommonQuality

A.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

A.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

A.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

A.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

A.3.2.2.8 CODECAPI\_AVLowLatencyMode

A.3.2.2.9 CODECAPI\_AVEncCommonQualityVsSpeed

A.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

A.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

A.3.2.2.12 CODECAPI\_AVEncVideoTemporalLayerCount

A.3.2.2.13 CODECAPI\_AVEncVideoSelectLayer

Optionale A.3.2.3-Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist optional.

A.3.2.3.1 CODECAPI\_AVEncH264CABACEnable

A.3.2.3.2 CODECAPI\_AVEncMPVDefaultBPictureCount

A.3.2.3.3 CODECAPI\_AVEncVideoEncodeFrameTypeQP

A.3.2.3.4 CODECAPI\_AVEncSliceControlMode

A.3.2.3.5 CODECAPI\_AVEncSliceControlSize

A.3.2.3.6 CODECAPI\_AVEncVideoMaxNumRefFrame

A.3.2.3.7 CODECAPI\_AVEncVideoMeanAbsoluteDifference

A.3.2.3.8 CODECAPI\_AVEncVideoROIEnabled

A.3.2.3.9 CODECAPI\_AVEncVideoMinQP

A.3.2.3.10 CODECAPI\_AVEncVideoMaxQP

A.3.2.3.11 CODECAPI\_AVEncVideoLTRBufferControl

A.3.2.3.12 CODECAPI\_AVEncVideoMarkLTRFrame

A.3.2.3.13 CODECAPI\_AVEncVideoUseLTRFrame

A.3.2.3.14 CODECAPI\_AVEncLowPowerEncoder

A.3.2.3.15 CODECAPI\_AVScenarioInfo

A.3.2.3.16 CODECAPI\_AVEncMPVGOPSizeMin

A.3.2.3.17 CODECAPI\_AVEncMPVGOPSizeMax

A.3.2.3.18 CODECAPI\_AVEncVideoMaxTem

A.3.2.3.19 CODECAPI\_AVEncMaxFrameRate

A.3.2.3.20 CODECAPI\_VideoEncoderDisplayContentType

A.3.2.3.22 CODECAPI\_AVEncEnableVideoProcessing

A.3.2.3.23 CODECAPI\_AVEncVideoGradualIntraRefresh

A.3.2.4 optionale Eigenschaft Notizen

Wenn Ihre h. 264-Encoder langen Begriff Verweis Frames implementiert wird, sollte die folgenden CodecAPI-Schnittstellen (in einem Frame-Verzögerung abgeschlossen) implementiert werden:

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

Wenn Ihre h. 264-Encoder langen Begriff Verweis Frames implementiert wird, muss das Attribut IMFSample LongTermReferenceFrameInfo unterstützt werden.

**A. 4 MF Media Type-Attribut Anforderungen**

Unterstützung ist für die folgenden MF Attribute Medientyp erforderlich:

A.4.1 [MF\_MT\_INTERLACE\_MODUS](http://msdn.microsoft.com/library/ms694868.aspx)

A.4.2 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

A.4.3 [MF\_MT\_UNTERTYP](http://msdn.microsoft.com/library/ms700208.aspx)

A.4.4 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

A.4.5 [MF\_MT\_FRAME\_RATE](http://msdn.microsoft.com/library/ms700140.aspx)

A.4.6 [MF\_MT\_FRAME\_GRÖßE](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

A.4.7 [MF\_MT\_AVG\_BITRATE](http://msdn.microsoft.com/library/ms703792.aspx)

A.4.8 [MF\_MT\_MPEG2\_PROFIL](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_VIDEO\_PROFIL)*

A.4.9 [MF\_MT\_MPEG2\_EBENE](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_VIDEO\_EBENE)*

A.4.10 [MF\_MT\_PIXEL\_ASPEKT\_VERHÄLTNIS](http://msdn.microsoft.com/library/ms704767.aspx)

A.4.11 [MF\_MT\_VIDEO\_NOMINAL\_BEREICH](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

A.4.12 [MF\_MT\_VIDEO\_GRUNDFARBEN](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

A.4.13 [MF\_MT\_ÜBERTRAGEN\_FUNKTION](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

A.4.14 [MF\_MT\_YUV\_MATRIX](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

A.4.15 [MF\_MT\_VIDEO\_CHROMA\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

A.4.16 [MF\_NALU\_LÄNGE\_FESTLEGEN](http://msdn.microsoft.com/en-us/library/hh870258.aspx)

**A. 5 MF Beispiel Attribut Support-Anforderungen**

A.5.1 Beispiel Attribute erforderlich

Kann ein ICodecAPI oder MF Media Type-Attribut gibt an, ob festgelegt ist müssen die folgenden Attribute Beispiel Eingabe- oder Beispiele vorhanden sein:

A.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

Die MFSampleExtension\_MeanAbsoluteDifference Beispiel-Attribut ist auf Ausgabe Beispiele erforderlich, wenn die CODECAPI\_AVEncVideoMeanAbsoluteDifference-Eigenschaft auf einen Wert ungleich NULL festgelegt wurde. Beachten Sie, dass, da CODECAPI\_AVEncVideoMeanAbsoluteDifference ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoMeanAbsoluteDifference wird unterstützt.

A.5.1.2 MFSampleExtension\_LongTermReferenceFrameInfo

Die MFSampleExtension\_LongTermReferenceFrameInfo Beispiel-Attribut ist auf Ausgabe Beispiele erforderlich, wenn die CODECAPI\_AVEncVideoLTRBufferControl wurde angegeben, dass eine oder mehrere langfristige Verweis Frames vorhanden sein können. Beachten Sie, dass, da CODECAPI\_AVEncVideoLTRBufferControl ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoLTRBufferControl wird unterstützt.

A.5.1.3 MF\_NALU\_LÄNGE\_INFORMATIONEN

MF\_NALU\_LÄNGE\_Beispiel Attribut ist auf Ausgabe Beispiele erforderlich, wenn die MF\_NALU\_LÄNGE\_SET Media Type-Attribut auf einen Wert ungleich NULL festgelegt wurde.

A.5.1.4 MFSampleExtension\_ROIRectangle

Input-Beispiel kann ein MFSampleExtension enthalten\_ROIRectangle sample Attribut aus, wenn die CODECAPI\_AVEncVideoROIEnabled-Eigenschaft auf einen Wert ungleich NULL festgelegt wurde. Beachten Sie, dass, da CODECAPI\_AVEncVideoROIEnabled ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoROIEnabled wird unterstützt.

A.5.2 Beispiel optionale Attribute

Die folgenden Attribute input-Beispiel können vorhanden sein. Es ist optional, ob der Encoder die durch diese Attribute enthaltene Informationen verwendet.

A.5.2.1 MFSampleExtension\_DirtyRects

A.5.2.2 MFSampleExtension\_MoveRegions

**A. 6 MFT-Attribute**

Encoder ist erforderlich, um die [IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx) unterstützen, die die [IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx) -Schnittstelle zurückzugeben wird, die Zugriff auf MFT Attribute ermöglicht. Unterstützung für die Verarbeitung die folgenden Attribute des MFT MF ist erforderlich:

A.6.1 [MFT\_ENUM\_HARDWARE\_URL\_Attribut](http://msdn.microsoft.com/library/dd388664.aspx)

A.6.2 [MFT\_ENUM\_HARDWARE\_HERSTELLER\_ID\_Attribut](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

A.6.3 [MFT\_ENCODER\_UNTERSTÜTZT\_CONFIG\_EREIGNIS](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

A.6.4 [MF\_VIDEO\_MAX\_MB\_PRO\_s](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

MFT A.6.5\_globalen Soundeffekts\_TREIBER\_VERSION\_ID\_Attribut

MFT A.6.6\_ENCODER\_FEHLER

**A. 7 Funktionalität Support-Anforderungen**

H. 264-Encoder muss folgende Funktionen unterstützen:

A.7.1 VBR Spitzenzeiten eingeschränkten Rate Steuerelementmodus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate, CODECAPI\_AVEncCommonMaxBitRate und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der maximale Bitrate verletzt wird (CODECAPI\_AVEncCommonMaxBitRate) beim zusammengeführt, um eine Bitrate des CODECAPI\_AVEncCommonMeanBitRate für die gesamte Videoclips.

A.7.2 VBR Quality-basierten Rate Steuerelementmodus

Der Encoder verwendet den Wert der CODECAPI\_AVEncCommonQuality oder CODECAPI\_AVEncVideoEncodeQP um Konstante Qualität des komprimierten Videos zu erzielen. Der Encoder wird ein konstanter QP für alle Frames verwenden.

Steuerung des A.7.3 CBR Rate-Modus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der angegebenen Bitrate verletzt wird (CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE).

A.7.4 GOP Abstand

Encoder erzeugt einen Schlüssel-Frame, in dem durch den Wert der CODECAPI angegebenen Frame Intervall\_AVEncMPVGOPSize-Eigenschaft. IntMAX der Wert für diese Eigenschaft gibt an, dass nur der erste Frame eine wichtige Frame werden soll.

A.7.5 Frame-basierte QP-Steuerelement

Muss unter minimale QP Bereich von 20 bis 40 unterstützen. Muss einen Fehler zurück, wenn Sie ein ungültiger Wert (z. B. 52) festgelegt ist.

A.7.6 erzwungenes Schlüssel-Frame-Steuerelement

SPS/PPS muss IDR vorangestellt werden Wenn die Anzahl der Ebenen zeitliche &gt; 1, Key Frame eingefügt werden muss im nächsten Frame zeitliche Basisgrößen, um die zeitliche Struktur beibehalten. Für einen einzelnen Layer-Bit-Stream muss im nächsten Frame Key Frame eingefügt werden.

A.7.7 Qualität und Geschwindigkeit-Steuerelement

A.7.8 geringer Latenz-Steuerelement

Der Encoder muss die Möglichkeit, die in den Modus mit geringer Latenz festgelegt werden unterstützt. In diesem Modus sollte der Encoder Beispielen input nicht Puffer. Erzeugen einer Ausgabebeispiel für jede input-Beispiel muss.

Encoder muss auch entweder POC Typ 2 erzwingen oder legen Sie die Benutzerschnittstelle für Spracheingabe-Bit-Stream\_Einschränkung Flag auf TRUE und Benutzerschnittstelle für Spracheingabe Num\_Neuanordnen\_Frames auf 0.

A.7.8 zeitliche Layer-Unterstützung

Es ist erforderlich, dass der Encoder hierarchische P unterstützen frames-Codierung und aneinander Bitreams von 1, 2 oder 3 temporär unabhängigen Ebenen generieren.

A.7.9 langfristig Verweis Frame-Unterstützung

Wenn Ihre h. 264-Encoder langen Begriff Verweis Frames implementiert wird, sollte die folgenden CodecAPI-Schnittstellen (in einem Frame-Verzögerung abgeschlossen) implementiert werden:

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

**A.8 asynchrone MFT-Unterstützung**

Es wird empfohlen, dass Sie eine [asynchrone MFT](http://msdn.microsoft.com/library/dd317909.aspx)implementieren. Eine asynchrone MFT erfordert die Implementierung der [IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) und [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx) Schnittstellen.

**9 Dokumentieren IMFRealTimeClientEx**

Die Registrierung mit über IMFRealTimeCLientEx::SetWorkQueue UND Leistungsziele erfüllt ist, wird die Implementierung der [IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx) -Schnittstelle daher empfohlen.

**9 Dokumentieren mehrere Anforderungen Instanz**

Es ist erforderlich, dass Ihre h. 264-Encoder mindestens 4 gleichzeitiger Instanzen unterstützen muss. Der Encoder sollten keine Einschränkung für die Anzahl der Instanzen. Es sollte durch die Speicherverwendung begrenzt werden.

Diese Instanzen können in demselben Prozess oder in verschiedenen Prozessen sein.

**A.10 Wert Validierung**

Es ist erforderlich, dass Ihre h. 264-Encoder die Überprüfung des vertrauenswürdigen Wert unterstützt.

Es ist erforderlich, dass Ihre h. 264-Encoder separate binäre, einzeln zertifiziert und signiert.

**A.11 zusätzlichen Anforderungen**

Die [Windows-MP4 Datei Empfänger](http://msdn.microsoft.com/library/dd757763.aspx)muss Ihre h. 264-Encoder entwickelt.

Ihre h. 264-Encoder muss die richtige Reihenfolge der Codierung Konfiguration implementieren.

Ihre h. 264-Encoder muss gültige von Bitstreams mit bis zu 3 zeitliche Ebenen werden erzeugen.

Präfix des h. 264-Encoder NALU voranzustellen jedes Segment und mit von Bitstreams mit 1 bis 3 zeitliche Ebenen korrekte Syntax ist.

Ihre h. 264-Encoder muss eine im Batchmodus GPU Anforderung pro Frame senden.

Ihre h. 264-Encoder muss ein AUD NALU vor jeder Frame eingefügt werden.

Ihre h. 264-Encoder muss in Sitzung 0 ordnungsgemäß.

**A.12-Installation**

Es ist erforderlich, die Ihre h. 264-Encoder registriert und zusammen mit der verwendete im Encoder Gerätetreiber nicht registriert ist.

**A.113 dynamisches Format ändern**

Es ist erforderlich, dass Ihre h. 264-Encoder dynamische Formatänderungen der folgenden innerhalb unterstützt:

Profil ändern

Auflösung und Framerate ändern

Hinzufügen und Löschen von zeitliche Ebenen

Maximal zulässige Anzahl von Verweis frames

Wenn mehrere Änderungen angefordert werden, bevor ein Frame Ausgabe erzeugt wird, sollten die letzte Änderung berücksichtigt werden.

**B. VC++-1 codieren**

Wenn Ihre Hardware VC++ 1 codieren unterstützt, müssen Sie folgende Schritte ausführen:

**B. 1 auf Eingabe:**

B.1.1 Support NV12

B.1.2, wenn Ihre Hardware unterstützt:

B.1.2.1 IYUV und YUY2 unterstützen

B.1.3 Unterstützung input Puffer des (und Abfrage in der angegebenen Reihenfolge):

B.1.3.1 IMF2DBuffer2

B.1.3.2 [IMF2DBuffer](http://msdn.microsoft.com/library/ms699894.aspx)

B.1.3.3 [IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx)

**B. 2 auf Ausgabe:**

Unterstützung für einfache B.2.1-Profil

B.2.2 Unterstützung Main Profil

Erweiterte Unterstützung B.2.3-Profil

**B. 3 Ihr VC++-1-Encoder muss die folgenden Schnittstellen verfügbar machen:**

B.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

B.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

B.3.2.1 ICodecAPI erfordert die folgenden Funktionen implementiert werden:

B.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

B.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

B.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

B.3.2.2 ICodecAPI erfordert die folgenden Eigenschaften werden unterstützt:

B.3.2.2.1 VBR Spitzenzeiten eingeschränkten Modus

B.3.2.2.2 Qualität-basierte VBR-Modus

B.3.2.2.3 CBR-Codierung

B.3.2.2.4 GOP Abstand

B.3.2.2.5 Frame QP-Steuerelement

B.3.2.2.6 Adaptive Bitrate-Steuerelement

B.3.2.2.7-Force-Schlüssel-Frame-Steuerelement

B.3.2.2.8 QualityVsSpeed-Steuerelement

B.3.2.2.9 geringer Latenz Codierung

B.3.2.3 empfohlen wird, dass Sie zusätzlich die folgenden Funktionen implementieren:

B.3.2.3.1 [GetDefaultValue](http://msdn.microsoft.com/library/dd311955.aspx)

B.3.2.3.2 [GetParameterRange](http://msdn.microsoft.com/library/dd311956.aspx)

B.3.2.3.3 [GetParameterValues](http://msdn.microsoft.com/library/dd311957.aspx)

B.3.2.3.4 [IsModifiable](http://msdn.microsoft.com/library/dd311959.aspx)

B.3.2.3.5 [SetAllDefaults](http://msdn.microsoft.com/library/dd311962.aspx)

B.3.3 [IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx)

B.3.3.1 über [IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx)

B.3.3.2 sind die beiden erforderlichen Attribute:

B.3.3.2.1 [MFT\_ENUM\_HARDWARE\_URL\_Attribut](http://msdn.microsoft.com/library/dd388664.aspx)

MFT B.3.3.2.2\_ENUM\_HARDWARE\_HERSTELLER\_ID\_Attribut

B.3.4 es wird empfohlen, eine [asynchrone MFT](http://msdn.microsoft.com/library/dd317909.aspx)zu implementieren.

Asynchrone MFTs B.3.4.1 erfordern die folgenden zusätzlichen Schnittstellen:

B.3.4.1.1 [IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx)

B.3.4.1.2 [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx)

Asynchrone MFTs B.3.4.2 wird empfohlen, das Erstellen von Threads vermeiden und wird empfohlen, den MF Thread-Pool verwenden.

Registrierung eines B.3.4.2.1 mit über IMFRealTimeCLientEx::SetWorkQueue UND ist entscheidend für die Leistungsziele zu erfüllen.

B.3.5 IMFRealTimeClientEx wird empfohlen.

**B4-Kodierung**

B.4.1 durch Eingabe Medientyp Aushandlung, muss der Encoder VC++ 1 unterstützen:

B.4.1.1 [MF\_MT\_INTERLACE\_MODUS](http://msdn.microsoft.com/library/ms694868.aspx)

B.4.1.1.1 Encoder muss beibehalten von Input output oder ablehnen Interlaced Interlaced.

B.4.1.2 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

B.4.2 über Ausgabe Media Type Aushandlung, die VC++-1-Encoder muss Folgendes unterstützen:

B.4.2.1 [MF\_MT\_UNTERTYP](http://msdn.microsoft.com/library/ms700208.aspx)

B.4.2.2 [MF\_MT\_FRAME\_GRÖßE](http://msdn.microsoft.com/library/ms701619.aspx)

BC.4.2.3 [MF\_MT\_FRAME\_RATE](http://msdn.microsoft.com/library/ms700140.aspx)

B.4.2.4 [MF\_MT\_AVG\_BITRATE](http://msdn.microsoft.com/library/ms703792.aspx)

B.4.2.5 [MF\_MT\_PIXEL\_ASPEKT\_VERHÄLTNIS](http://msdn.microsoft.com/library/ms704767.aspx)

B.4.3 Es wird empfohlen, dass Ihre VC++-1-Encoder unterstützt:

B.4.3.1. B-Frame Codierung

**B5 mehrere Instanzen**

B.5.1 ist es erforderlich, dass Ihre Encoder VC++-1 mindestens 3 gleichzeitiger Instanzen unterstützen muss. Encoder sollten Beschränkung auf Anzahl der Instanzen nicht speichern. Es sollte durch die Speicherverwendung begrenzt.

B.5.1.1 möglicherweise diese Instanzen in demselben Prozess oder in verschiedenen Prozessen.

**B6 Wert Validierung**

B.6.1 ist es erforderlich, dass Ihre Encoder VC++ 1 die Überprüfung des vertrauenswürdigen Wert unterstützt.

B.6.2 ist es erforderlich, dass Ihre Encoder VC++ 1 separate binäre, einzeln zertifiziert und signiert.

**Zusätzliche Anforderungen b. 7**

Die [Windows ASF Datei Empfänger](http://msdn.microsoft.com/library/ee663576.aspx)muss Ihr VC++-1-Encoder B.7.1 entwickelt.

B.7.2 Ihr VC++-1-Encoder muss die richtige Reihenfolge der Codierung Konfiguration implementieren.

B.7.3 Ihr VC++-1 Encoder muss ordnungsgemäß in Sitzung 0.

**B. 8-Installation**

B.8.1 ist es erforderlich, die Ihre Encoder VC++ 1 registriert und zusammen mit der im Encoder verwendete Gerätetreiber nicht registriert ist.

**C. H.265 codieren**

Wenn Ihre Hardware H.265 codieren unterstützt, müssen Sie folgende Schritte ausführen:

**C. 1 Eingabeformat-Unterstützung**

Der Encoder muss NV12 Format für input Frames unterstützen. Optional kann der Encoder IYUV unterstützen, und YUY2 formatiert.

Der Encoder implementieren muss die Unterstützung für die [IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx), [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx), und [IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx) Media Puffer-Schnittstellen.

**C. 2-Profil-Unterstützung**

Der Encoder muss Daten aneinander über das Erstellen der Ausgabecache-Inhalte, das auf das Profil Main übereinstimmt.

Der Encoder muss die entsprechenden Kopfzeilenelemente des Syntax, um darauf hinzuweisen, dass er auf das Profil Main codiert wird generieren kann.

**C. 3-Schnittstelle Support-Anforderungen**

H.265 Encoder muss die folgenden Schnittstellen unterstützen:

C.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

Implementierung der folgenden Methoden der [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx) -Schnittstelle ist erforderlich:

C.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

C.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

C.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

C.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

C.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

C.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

C.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

C.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

C.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

C.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

C.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

C.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

Das Ereignis MEEncodingParameters müssen behandelt werden:

C.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

C.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

C.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

C.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

C.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

C.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

C.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

Der Encoder muss bestimmte Methoden und Eigenschaft GUIDs der ICodecAPI-Schnittstelle unterstützt.

A.3.2.1 erforderlichen Methoden

Implementierung der folgenden Methoden der ICodecAPI-Schnittstelle ist erforderlich:

C.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

C.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

C.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

C.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

C.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

C.3.2.2 erforderliche Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist erforderlich:

C.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

C.3.2.2.2 CODECAPI\_AVEncCommonQuality

C.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

C.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

C.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

C.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

C.3.2.2.8 CODECAPI\_AVLowLatencyMode

C.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

C.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

Optionale C.3.2.3-Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist optional.

C.3.2.3.1 CODECAPI\_AVEncCommonQualityVsSpeed

C.3.2.3.2 CODECAPI\_AVEncVideoTemporalLayerCount

C.3.2.3.3 CODECAPI\_AVEncVideoSelectLayer

C.3.2.3.4 CODECAPI\_AVEncMPVDefaultBPictureCount

C.3.2.3.5 CODECAPI\_AVEncVideoEncodeFrameTypeQP

C.3.2.3.6 CODECAPI\_AVEncSliceControlMode

C.3.2.3.7 CODECAPI\_AVEncSliceControlSize

C.3.2.3.8 CODECAPI\_AVEncVideoMaxNumRefFrame

C.3.2.3.9 CODECAPI\_AVEncVideoMeanAbsoluteDifference

C.3.2.3.10 CODECAPI\_AVEncVideoROIEnabled

C.3.2.3.11 CODECAPI\_AVEncVideoMinQP

C.3.2.3.12 CODECAPI\_AVEncVideoMaxQP

C.3.2.3.13 CODECAPI\_AVEncVideoLTRBufferControl

C.3.2.3.14 CODECAPI\_AVEncVideoMarkLTRFrame

C.3.2.3.15 CODECAPI\_AVEncVideoUseLTRFrame

C.3.2.3.16 CODECAPI\_AVEncLowPowerEncoder

C.3.2.3.17 CODECAPI\_AVScenarioInfo

C.3.2.3.18 CODECAPI\_AVEncMPVGOPSizeMin

C.3.2.3.19 CODECAPI\_AVEncMPVGOPSizeMax

C.3.2.3.20 CODECAPI\_AVEncVideoMaxTem

C.3.2.3.21 CODECAPI\_AVEncMaxFrameRate

C.3.2.3.22 CODECAPI\_VideoEncoderDisplayContentType

C.3.2.3.23 CODECAPI\_AVEncEnableVideoProcessing

C.3.2.3.24 CODECAPI\_AVEncVideoGradualIntraRefresh

C.3.2.4 optionale Eigenschaft Notes

Wenn Ihre H.265 Encoder langen Begriff Verweis Frames implementiert wird, sollten die folgenden Schnittstellen CodecAPI (in einem Frame-Verzögerung abgeschlossen) implementiert werden:

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

Wenn Ihre H.265 Encoder langen Begriff Verweis Frames implementiert wird, muss das Attribut IMFSample LongTermReferenceFrameInfo unterstützt werden.

**C. 4 MF Media Type-Attribut Anforderungen**

Unterstützung ist für die folgenden MF Attribute Medientyp erforderlich:

C.4.1 [MF\_MT\_INTERLACE\_MODUS](http://msdn.microsoft.com/library/ms694868.aspx)

C.4.2 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

C.4.3 [MF\_MT\_UNTERTYP](http://msdn.microsoft.com/library/ms700208.aspx)

C.4.4 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

C.4.5 [MF\_MT\_FRAME\_RATE](http://msdn.microsoft.com/library/ms700140.aspx)

C.4.6 [MF\_MT\_FRAME\_GRÖßE](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

C.4.7 [MF\_MT\_AVG\_BITRATE](http://msdn.microsoft.com/library/ms703792.aspx)

C.4.8 [MF\_MT\_MPEG2\_PROFIL](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_VIDEO\_PROFIL)*

C.4.9 [MF\_MT\_MPEG2\_EBENE](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_VIDEO\_EBENE)*

C.4.10 [MF\_MT\_PIXEL\_ASPEKT\_VERHÄLTNIS](http://msdn.microsoft.com/library/ms704767.aspx)

C.4.11 [MF\_MT\_VIDEO\_NOMINAL\_BEREICH](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

C.4.12 [MF\_MT\_VIDEO\_GRUNDFARBEN](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

C.4.13 [MF\_MT\_ÜBERTRAGEN\_FUNKTION](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

C.4.14 [MF\_MT\_YUV\_MATRIX](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

C.4.15 [MF\_MT\_VIDEO\_CHROMA\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

C.4.16 [MF\_NALU\_LÄNGE\_FESTLEGEN](http://msdn.microsoft.com/en-us/library/hh870258.aspx)

**C.5 MF Beispiel Attribut Support-Anforderungen**

C.5.1 Beispiel Attribute erforderlich

Kann ein ICodecAPI oder MF Media Type-Attribut gibt an, ob festgelegt ist müssen die folgenden Attribute Beispiel Eingabe- oder Beispiele vorhanden sein:

C.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

Die MFSampleExtension\_MeanAbsoluteDifference Beispiel-Attribut ist auf Ausgabe Beispiele erforderlich, wenn die CODECAPI\_AVEncVideoMeanAbsoluteDifference-Eigenschaft auf einen Wert ungleich NULL festgelegt wurde. Beachten Sie, dass, da CODECAPI\_AVEncVideoMeanAbsoluteDifference ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoMeanAbsoluteDifference wird unterstützt.

C5.1.2 MFSampleExtension\_LongTermReferenceFrameInfo

Die MFSampleExtension\_LongTermReferenceFrameInfo Beispiel-Attribut ist auf Ausgabe Beispiele erforderlich, wenn die CODECAPI\_AVEncVideoLTRBufferControl wurde angegeben, dass eine oder mehrere langfristige Verweis Frames vorhanden sein können. Beachten Sie, dass, da CODECAPI\_AVEncVideoLTRBufferControl ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoLTRBufferControl wird unterstützt.

C5.1.3 MF\_NALU\_LÄNGE\_INFORMATIONEN

MF\_NALU\_LÄNGE\_Beispiel Attribut ist auf Ausgabe Beispiele erforderlich, wenn die MF\_NALU\_LÄNGE\_SET Media Type-Attribut auf einen Wert ungleich NULL festgelegt wurde.

C.5.1.4 MFSampleExtension\_ROIRectangle

Input-Beispiel kann ein MFSampleExtension enthalten\_ROIRectangle sample Attribut aus, wenn die CODECAPI\_AVEncVideoROIEnabled-Eigenschaft auf einen Wert ungleich NULL festgelegt wurde. Beachten Sie, dass, da CODECAPI\_AVEncVideoROIEnabled ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoROIEnabled wird unterstützt.

C.5.2 Beispiel optionale Attribute

Die folgenden Attribute input-Beispiel können vorhanden sein. Es ist optional, ob der Encoder die durch diese Attribute enthaltene Informationen verwendet.

C.5.2.1 MFSampleExtension\_DirtyRects

Die MFSampleExtension\_DirtyRects-Attribut ist ein BLOB mit der folgenden Struktur:

```
typedef struct \_DIRTYRECT\_INFO
{
UINT FrameNumber;
UINT NumDirtyRects;
RECT DirtyRects\[1\];
} DIRTYRECT\_INFO;
```

Dieses Attribut ist für die Komprimierung von Bildschirminhalt verwendet werden soll und im Fenster-Manager, um Informationen über die dirty Rechtecke im Bildschirm Frame übergeben kann.

C.5.2.2 MFSampleExtension\_MoveRegions

Die MFSampleExtension\_MoveRegions-Attribut ist ein BLOB mit der folgenden Struktur:

```
typedef struct \_MOVE\_RECT
{
POINT SourcePoint;
RECT DestRect;
} MOVE\_RECT;

typedef struct \_MOVEREGION\_INFO
{
UINT FrameNumber;
UINT NumMoveRegions;
MOVE\_RECT MoveRegions\[1\];
} MOVEREGION\_INFO;
```

**C. 6 MFT-Attribute**

Encoder ist erforderlich, um die [IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx) unterstützen, die die [IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx) -Schnittstelle zurückzugeben wird, die Zugriff auf MFT Attribute ermöglicht. Unterstützung für die Verarbeitung die folgenden Attribute des MFT MF ist erforderlich:

A.6.1 [MFT\_ENUM\_HARDWARE\_URL\_Attribut](http://msdn.microsoft.com/library/dd388664.aspx)

C.6.2 [MFT\_ENUM\_HARDWARE\_HERSTELLER\_ID\_Attribut](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

C.6.3 [MFT\_ENCODER\_UNTERSTÜTZT\_CONFIG\_EREIGNIS](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

C.6.4 [MF\_VIDEO\_MAX\_MB\_PRO\_s](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

MFT C.6.5\_globalen Soundeffekts\_TREIBER\_VERSION\_ID\_Attribut

MFT C.6.6\_ENCODER\_FEHLER

**7 Funktionalität Support-Anforderungen**

Der H.265 Encoder muss die folgende Funktionalität unterstützen:

C.7.1 VBR Spitzenzeiten eingeschränkten Ratecontrol Modus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate, CODECAPI\_AVEncCommonMaxBitRate und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der maximale Bitrate verletzt wird (CODECAPI\_AVEncCommonMaxBitRate) beim zusammengeführt, um eine Bitrate des CODECAPI\_AVEncCommonMeanBitRate für die gesamte Videoclips.

C.7.2 Qualität-basierte VBR Ratecontrol Modus

Der Encoder verwendet den Wert der CODECAPI\_AVEncCommonQuality oder CODECAPI\_AVEncVideoEncodeQP um Konstante Qualität des komprimierten Videos zu erzielen. Der Encoder wird ein konstanter QP für alle Frames verwenden.

C.7.3 CBR Ratecontrol Modus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der angegebenen Bitrate verletzt wird (CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE).

C.7.4 GOP Abstand

Encoder erzeugt einen Schlüssel-Frame, in dem durch den Wert der CODECAPI angegebenen Frame Intervall\_AVEncMPVGOPSize-Eigenschaft. IntMAX der Wert für diese Eigenschaft gibt an, dass nur der erste Frame eine wichtige Frame werden soll.

C.7.5 Frame-basierte QP-Steuerelement

Muss unter minimale QP Bereich von 20 bis 40 unterstützen. Muss einen Fehler zurück, wenn Sie ein ungültiger Wert (z. B. 52) festgelegt ist.

C.7.6 erzwungenes Schlüssel-Frame-Steuerelement

SPS/PPS muss IDR vorangestellt werden Wenn die Anzahl der Ebenen zeitliche &gt; 1, Key Frame eingefügt werden muss im nächsten Frame zeitliche Basisgrößen, um die zeitliche Struktur beibehalten. Für einen einzelnen Layer-Bit-Stream muss im nächsten Frame Key Frame eingefügt werden.

C.7.7 Qualität und Geschwindigkeit-Steuerelement

C.7.8 geringer Latenz-Steuerelement

Der Encoder muss die Möglichkeit, die in den Modus mit geringer Latenz festgelegt werden unterstützt. In diesem Modus sollte der Encoder Beispielen input nicht Puffer. Erzeugen einer Ausgabebeispiel für jede input-Beispiel muss.

Encoder muss auch entweder POC Typ 2 erzwingen oder legen Sie die Benutzerschnittstelle für Spracheingabe-Bit-Stream\_Einschränkung Flag auf TRUE und Benutzerschnittstelle für Spracheingabe Num\_Neuanordnen\_Frames auf 0.

C.7.8 zeitliche Layer-Unterstützung

Es ist erforderlich, dass der Encoder hierarchische P unterstützen frames-Codierung und aneinander Bitreams von 1, 2 oder 3 temporär unabhängigen Ebenen generieren.

C.7.9 langfristig Verweis Frame-Unterstützung

Wenn Ihre H.265 Encoder langen Begriff Verweis Frames implementiert wird, sollten die folgenden Schnittstellen CodecAPI (in einem Frame-Verzögerung abgeschlossen) implementiert werden:

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

**C. 8 asynchronen MFT-Unterstützung**

Es wird empfohlen, dass Sie eine [asynchrone MFT](http://msdn.microsoft.com/library/dd317909.aspx)implementieren. Eine asynchrone MFT erfordert die Implementierung der [IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) und [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx) Schnittstellen.

**C. 9 IMFRealTimeClientEx**

Die Registrierung mit UND über IMFRealTimeCLientEx::SetWorkQueue ist entscheidend für die Leistungsziele; aus diesem Grund empfiehlt sich die Implementierung der [IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx) -Schnittstelle.

**C. 9 mehrere Anforderungen Instanz**

Es ist erforderlich, dass Ihre Encoder H.265 mindestens 3 gleichzeitiger Instanzen unterstützen muss. Der Encoder sollten keine Einschränkung für die Anzahl der Instanzen. Es sollte durch die Speicherverwendung begrenzt werden.

Diese Instanzen können in demselben Prozess oder in verschiedenen Prozessen sein.

**C.10 Wert Validierung**

Es ist erforderlich, dass Ihre H.265 Encoder die Überprüfung des vertrauenswürdigen Wert unterstützt.

Es ist erforderlich, dass Ihre H.265 Encoder separate binäre, einzeln zertifiziert und signiert.

**C.11 zusätzlichen Anforderungen**

Die [Windows-MP4 Datei Empfänger](http://msdn.microsoft.com/library/dd757763.aspx)muss Ihre H.265 Encoder entwickelt.

Ihre H.265 Encoder muss ordnungsgemäße Codierung Konfigurationsreihenfolge implementieren.

Ihre H.265 Encoder muss gültige von Bitstreams mit bis zu 3 zeitliche Ebenen erzeugen.

Präfix des H.265 Encoder NALU voranzustellen jedes Segment und mit von Bitstreams mit 1 bis 3 zeitliche Ebenen korrekte Syntax ist.

Ihre H.265 Encoder muss es sich um eine im Batchmodus GPU Anforderung pro Frame senden.

Ihre H.265 Encoder muss ein AUD NALU vor jeder Frame eingefügt werden.

Ihre H.265 Encoder muss in Sitzung 0 ordnungsgemäß funktionieren.

**C.12-Installation**

Es ist erforderlich, die Ihre H.265 Encoder registriert und zusammen mit der im Encoder verwendete Gerätetreiber nicht registriert ist.

**C.113 dynamisches Format ändern**

Es ist erforderlich, dass Ihre Encoder H.265 dynamische Formatänderungen der folgenden innerhalb unterstützt:

Profil ändern

Auflösung und Framerate ändern

Hinzufügen und Löschen von zeitliche Ebenen

Maximal zulässige Anzahl von Verweis frames

Wenn mehrere Änderungen angefordert werden, bevor ein Frame Ausgabe erzeugt wird, sollten die letzte Änderung berücksichtigt werden.

**D. VP9/VP8 codieren**

Wenn Ihre Hardware VP9/VP8 codieren unterstützt, müssen Sie folgende Schritte ausführen:

**D. 1 Eingabeformat-Unterstützung**

Der Encoder muss NV12 Format für input Frames unterstützen. Optional kann der Encoder IYUV unterstützen, und YUY2 formatiert.

Der Encoder implementieren muss die Unterstützung für die [IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx), [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx), und [IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx) Media Puffer-Schnittstellen.

**2-Profil-Unterstützung**

Der Encoder muss Daten aneinander über das Erstellen der Ausgabecache-Inhalte, das an die Profile0 übereinstimmt.

Der Encoder muss die entsprechenden Kopfzeilenelemente des Syntax, um darauf hinzuweisen, dass es mit der Profile0 codiert wird generieren kann.

**Support-Anforderungen bei D.3-Schnittstelle**

Der VP9/VP8 Encoder muss die folgenden Schnittstellen unterstützen:

D.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

Implementierung der folgenden Methoden der [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx) -Schnittstelle ist erforderlich:

D.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

D.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

D.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

D.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

D.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

D.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

D.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

D.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

D.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

D.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

D.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

D.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

Das Ereignis MEEncodingParameters müssen behandelt werden:

D.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

D.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

D.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

D.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

D.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

D.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

D.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

Der Encoder muss bestimmte Methoden und Eigenschaft GUIDs der ICodecAPI-Schnittstelle unterstützt.

A.3.2.1 erforderlichen Methoden

Implementierung der folgenden Methoden der ICodecAPI-Schnittstelle ist erforderlich:

D.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

D.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

D.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

D.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

D.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

D.3.2.2 erforderlichen Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist erforderlich:

D.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

D.3.2.2.2 CODECAPI\_AVEncCommonQuality

D.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

D.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

D.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

D.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

D.3.2.2.8 CODECAPI\_AVLowLatencyMode

D.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

D.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

Optionale D.3.2.3-Eigenschaften

Unterstützung für die folgenden ICodecAPI-Eigenschaft GUIDs ist optional.

D.3.2.3.1 CODECAPI\_AVEncCommonQualityVsSpeed

**D.4 MF Media Type-Attribut Anforderungen**

Unterstützung ist für die folgenden MF Attribute Medientyp erforderlich:

D.4.1 [MF\_MT\_INTERLACE\_MODUS](http://msdn.microsoft.com/library/ms694868.aspx)

D.4.2 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

D.4.3 [MF\_MT\_UNTERTYP](http://msdn.microsoft.com/library/ms700208.aspx)

D.4.4 [MF\_MT\_MINDESTENS\_ANZEIGE\_BLENDE](http://msdn.microsoft.com/library/ms700173.aspx)

D.4.5 [MF\_MT\_FRAME\_RATE](http://msdn.microsoft.com/library/ms700140.aspx)

D.4.6 [MF\_MT\_FRAME\_GRÖßE](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

D.4.7 [MF\_MT\_AVG\_BITRATE](http://msdn.microsoft.com/library/ms703792.aspx)

D.4.8 [MF\_MT\_MPEG2\_PROFIL](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_VIDEO\_PROFIL)*

D.4.9 [MF\_MT\_MPEG2\_EBENE](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_VIDEO\_EBENE)*

D.4.10 [MF\_MT\_PIXEL\_ASPEKT\_VERHÄLTNIS](http://msdn.microsoft.com/library/ms704767.aspx)

D.4.11 [MF\_MT\_VIDEO\_NOMINAL\_BEREICH](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

D.4.12 [MF\_MT\_VIDEO\_GRUNDFARBEN](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

D.4.13 [MF\_MT\_TRANSFER\_FUNKTION](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

D.4.14 [MF\_MT\_YUV\_MATRIX](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

D.4.15 [MF\_MT\_VIDEO\_CHROMA\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

**D. 5 MF Beispiel Attribut Support-Anforderungen**

D.5.1 Beispiel Attribute erforderlich

Kann ein ICodecAPI oder MF Media Type-Attribut gibt an, ob festgelegt ist müssen die folgenden Attribute Beispiel Eingabe- oder Beispiele vorhanden sein:

D.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

Die MFSampleExtension\_MeanAbsoluteDifference Beispiel-Attribut ist auf Ausgabe Beispiele erforderlich, wenn die CODECAPI\_AVEncVideoMeanAbsoluteDifference-Eigenschaft auf einen Wert ungleich NULL festgelegt wurde. Beachten Sie, dass, da CODECAPI\_AVEncVideoMeanAbsoluteDifference ist eine optionale Eigenschaft, die Unterstützung für dieses Attribut ist nur erforderlich, für den Fall, in dem CODECAPI\_AVEncVideoMeanAbsoluteDifference wird unterstützt.

D.5.2 Beispiel optionale Attribute

Die folgenden Attribute input-Beispiel können vorhanden sein. Es ist optional, ob der Encoder die durch diese Attribute enthaltene Informationen verwendet.

D.5.2.1 MFSampleExtension\_DirtyRects

Die MFSampleExtension\_DirtyRects-Attribut ist ein BLOB mit der folgenden Struktur:

```
typedef struct \_DIRTYRECT\_INFO
{
UINT FrameNumber;
UINT NumDirtyRects;
RECT DirtyRects\[1\];
} DIRTYRECT\_INFO;
```

Dieses Attribut ist für die Komprimierung von Bildschirminhalt verwendet werden soll und im Fenster-Manager, um Informationen über die dirty Rechtecke im Bildschirm Frame übergeben kann.

D.5.2.2 MFSampleExtension\_MoveRegions

Die MFSampleExtension\_MoveRegions-Attribut ist ein BLOB mit der folgenden Struktur:

```
typedef struct \_MOVE\_RECT
{
POINT SourcePoint;
RECT DestRect;
} MOVE\_RECT;

typedef struct \_MOVEREGION\_INFO
{
UINT FrameNumber;
UINT NumMoveRegions;
MOVE\_RECT MoveRegions\[1\];
} MOVEREGION\_INFO;
```

**D.6 MFT-Attribute**

Encoder ist erforderlich, um die [IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx) unterstützen, die die [IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx) -Schnittstelle zurückzugeben wird, die Zugriff auf MFT Attribute ermöglicht. Unterstützung für die Verarbeitung die folgenden Attribute des MFT MF ist erforderlich:

A.6.1 [MFT\_ENUM\_HARDWARE\_URL\_Attribut](http://msdn.microsoft.com/library/dd388664.aspx)

D.6.2 [MFT\_ENUM\_HARDWARE\_HERSTELLER\_ID\_Attribut](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

D.6.3 [MFT\_ENCODER\_UNTERSTÜTZT\_CONFIG\_EREIGNIS](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

D.6.4 [MF\_VIDEO\_MAX\_MB\_PRO\_s](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

MFT D.6.5\_globalen Soundeffekts\_TREIBER\_VERSION\_ID\_Attribut

MFT D.6.6\_ENCODER\_FEHLER

**D.7 Funktionalität Support-Anforderungen**

Der VP9/VP8 Encoder muss die folgende Funktionalität unterstützen:

D.7.1 VBR Spitzenzeiten eingeschränkten Ratecontrol Modus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate, CODECAPI\_AVEncCommonMaxBitRate und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der maximale Bitrate verletzt wird (CODECAPI\_AVEncCommonMaxBitRate) beim zusammengeführt, um eine Bitrate des CODECAPI\_AVEncCommonMeanBitRate für die gesamte Videoclips.

D.7.2 Qualität-basierte VBR Ratecontrol Modus

Der Encoder verwendet den Wert der CODECAPI\_AVEncCommonQuality oder CODECAPI\_AVEncVideoEncodeQP um Konstante Qualität des komprimierten Videos zu erzielen. Der Encoder wird ein konstanter QP für alle Frames verwenden.

D.7.3 CBR Ratecontrol Modus

Der Encoder verwenden die Werte von der CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE und CODECAPI\_AVEncCommonBufferSize-Eigenschaften, um sicherzustellen, dass der theoretische Puffer nicht mit der angegebenen Bitrate verletzt wird (CODECAPI\_AVEncCommonMeanBitRate oder MF\_MT\_AVG\_BITRATE).

D.7.4 GOP Abstand

Encoder erzeugt einen Schlüssel-Frame, in dem durch den Wert der CODECAPI angegebenen Frame Intervall\_AVEncMPVGOPSize-Eigenschaft. IntMAX der Wert für diese Eigenschaft gibt an, dass nur der erste Frame eine wichtige Frame werden soll.

D.7.5 Frame-basierte QP-Steuerelement

Muss unter minimale QP Bereich von 20 bis 40 unterstützen. Muss einen Fehler zurück, wenn Sie ein ungültiger Wert (z. B. 52) festgelegt ist.

D.7.6 erzwungenes Schlüssel-Frame-Steuerelement

SPS/PPS muss IDR vorangestellt werden Wenn die Anzahl der Ebenen zeitliche &gt; 1, Key Frame eingefügt werden muss im nächsten Frame zeitliche Basisgrößen, um die zeitliche Struktur beibehalten. Für einen einzelnen Layer-Bit-Stream muss im nächsten Frame Key Frame eingefügt werden.

D.7.7 Qualität und Geschwindigkeit-Steuerelement

D.7.8 geringer Latenz-Steuerelement

Der Encoder muss die Möglichkeit, die in den Modus mit geringer Latenz festgelegt werden unterstützt. In diesem Modus sollte der Encoder Beispielen input nicht Puffer. Erzeugen einer Ausgabebeispiel für jede input-Beispiel muss.

**D. 8 asynchronen MFT-Unterstützung**

Es wird empfohlen, dass Sie eine [asynchrone MFT](http://msdn.microsoft.com/library/dd317909.aspx)implementieren. Eine asynchrone MFT erfordert die Implementierung der [IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) und [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx) Schnittstellen.

**D. 9 IMFRealTimeClientEx**

Die Registrierung mit UND über IMFRealTimeCLientEx::SetWorkQueue ist entscheidend für die Leistungsziele; aus diesem Grund empfiehlt sich die Implementierung der [IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx) -Schnittstelle.

**D. 9 mehrere Anforderungen Instanz**

Es ist erforderlich, dass Ihre Encoder VP9/VP8 mindestens 3 gleichzeitiger Instanzen unterstützen muss. Der Encoder sollten keine Einschränkung für die Anzahl der Instanzen. Es sollte durch die Speicherverwendung begrenzt werden.

Diese Instanzen können in demselben Prozess oder in verschiedenen Prozessen sein.

**D. 10 Wert Validierung**

Es ist erforderlich, dass Ihre Encoder VP9/VP8 des Überprüfungsvorgangs vertrauenswürdigen Wert unterstützt.

Es ist erforderlich, dass Ihre VP9/VP8 Encoder separate binäre, einzeln zertifiziert und signiert.

**Zusätzliche Anforderungen d. 11**

Ihre VP9/VP8 Encoder muss ordnungsgemäßen Codierung Konfigurationsreihenfolge implementieren.

Ihre VP9/VP8 Encoder muss eine im Batchmodus GPU Anforderung pro Frame senden.

Ihre VP9/VP8 Encoder muss ordnungsgemäß in Sitzung 0.

**D.12-Installation**

Es ist erforderlich, die Ihre VP9/VP8 Encoder registriert und zusammen mit der im Encoder verwendete Gerätetreiber nicht registriert ist.

**D.113 dynamisches Format ändern**

Es ist erforderlich, dass Ihre Encoder VP9/VP8 dynamische Formatänderungen der folgenden innerhalb unterstützt:

Profil ändern

Auflösung und Framerate ändern

Wenn mehrere Änderungen angefordert werden, bevor ein Frame Ausgabe erzeugt wird, sollten die letzte Änderung berücksichtigt werden.
