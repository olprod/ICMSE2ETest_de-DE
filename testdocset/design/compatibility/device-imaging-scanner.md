---
title: Device.Imaging.Scanner
Description: Requirements.
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 3555fdac0870f223e9a73cf044c7cffd24b4e334
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceimagingscanner"></a>Device.Imaging.Scanner

 - [Device.Imaging.Scanner.Base](#device.imaging.scanner.base)
 - [Device.Imaging.Scanner.WSD](#device.imaging.scanner.wsd)

<a name="device.imaging.scanner.base"></a>
## <a name="deviceimagingscannerbase"></a>Device.Imaging.Scanner.Base

### <a name="deviceimagingscannerbasedatatransfer"></a>Device.Imaging.Scanner.Base.dataTransfer

*WIA-Treiber müssen bestimmte Daten übertragen Implementierungen unterstützen.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Windows Image Erwerb (WIA) Treiber müssen Folgendes ausführen:

-   Verwenden Sie nur die Methoden **zu schreiben**, **Seek**und **SetSizeIStream** während des Downloads.

-   Verwenden Sie nur die Methoden **Lesen**, **Seek**und **StatIStream** während Uploads.

-   Senden Sie gültige **lPercentComplete** Werte während des Aufrufs der **IWiaMiniDrvTransferCallback::SendMessage**&lt;Element&gt;.  **lPercentComplete** muss zwischen 0 und 100 sein.

-   Senden Sie richtige UlTransferredBytes Werte während des Aufrufs IWiaMiniDrvTransferCallback::SendMessage.

-   Fügen Sie neue Daten an das Ende des Streams, die die **IWiaMiniDrvTransferCallback::GetNextStream**&lt;Element&gt; erhält, wenn die Datenströme nicht leer sind.

-   Rückgabewerte Erfolg aus der I**Wia MiniDrv::drvAcquireItemData** -Methode bei der Treiber ruft ich**WiaMiniDrv::drvAcquireItemData** mithilfe von gute Parameter in allen unterstützten Formaten.

-   Freigeben Sie ihre Referenzen zum **IStream** -Anwendungsobjekt vor deren Methoden **IWiaMiniDrv::drvAcquireItemData** zurück oder rufen Sie **IWiaMiniDrvTransferCallback::GetNextStream**.

-   Senden einer Stream, der eine mehrseitige Datei während des Downloads enthält, indem Sie alle unterstützt TYMED\_MULTIPAGE\_-Dateiformate.

-   Senden Sie einen Datenstrom für jedes Element während des Downloads mithilfe von alle TYMED unterstützten\_Dateiformaten.

-   Return S\_aus IWiaMiniDrv::drvAcquireItemData IWiaMiniDrvTransferCallback::SendMessage zurück FALSE S\_"false".

-   Weiterhin alle nachfolgenden Elemente nach **IWiaMiniDrvTransferCallback::GetNextStream** WIA gibt bei mehreren Elementen Downloads übertragen\_STATUS\_ÜBERSPRINGEN\_ELEMENTS.

-   Return S\_OK aus **IWiaMiniDrv::drvAcquireItemData** bei Single- und mit mehreren Element Downloads nach der **IWiaMiniDrvTransferCallback::GetNextStream** WIA gibt\_STATUS\_ÜBERSPRINGEN\_ARTIKEL für jedes Element.

-   Abbruch Übertragung aller Elemente nach **IWiaMiniDrvTransferCallback::GetNextStream** gibt S\_"false".

-   Aus **IWiaMiniDrv::drvAcquireItemData** Anrufe bei der Übertragung von abgebrochenen in kürzerer Zeit als bei der Übertragung von abgeschlossenen zurück.

-   Von IWiaMiniDrv::drvAcquireItemData einen Fehler zurück, wenn IWiaMiniDrvTransferCallback::GetNextStream ein Fehler auftritt.

-   Zurückgegeben Sie ein standard COM-Fehlercode aus **IWiaMiniDrv::drvAcquireItemData** , wenn **IWiaMiniDrvTransferCallback::GetNextStream** einen NULL-Zeiger Stream-Objekt zurückgibt.

-   Von IWiaMiniDrv::drvAcquireItemData einen Fehler zurück, wenn IWiaMiniDrvTransferCallback::SendMessage ein Fehler auftritt.

-   Übertragen Sie erfolgreich Artikel eine identische Gerät installiert ist, wenn das identische Gerät ein Element gleichzeitig überträgt.

-   Von **IWiaMiniDrv::drvAcquireItemData** einen Fehler zurück, wenn eine **IStream** -Methode ein Fehler auftritt.

-   Suchen der richtigen Streamposition nach der Treiber die Übertragung beginnt oder **IWiaMiniDrvTransferCallback::GetNextStream** oder **IWiaMiniDrvTransferCallback::SendMessage**aufruft.

-   Ordnungsgemäß, wenn der WIA-Dienst während der Übertragung beendet und dann neu gestartet, und eine neue Übertragung angefordert wird.

-   Ignorieren Sie Anrufe an die **DrvNotifyPnPEvent**&lt;Element&gt; , enthalten WIA\_EREIGNIS\_ABBRECHEN\_e/a, wenn die Übertragung nicht ausgeführt wird, und nicht abstürzen oder hängen.

-   Übertragen erfolgreich Elemente nach einer gültigen WIA\_IPA\_TYMED-Eigenschaftswert mithilfe einer Varianttyp mit oder ohne Vorzeichen geschrieben wird.

WIA-Treiber müssen nicht die folgenden Schritte ausführen:

-   Rufen Sie eine Methode eines Objekts von einer Anwendung **IStream** als die **IUnknown** -Methode nach einer Anwendung Übertragung Rückruf gibt S\_FALSE, WIA\_STATUS\_ÜBERSPRINGEN\_ELEMENT oder einen Fehler.

-   Rufen Sie eine Methode des einer Anwendung **IStream** Objekts als die **IUnknown** -Methode nach dem Zurückgeben der Treiber **IWiaMiniDrv::drvAcquireItemData** Methode oder Anrufe **IWiaMiniDrvTransferCallback::GetNextStream** während der Übertragung mehrere Elemente an.

-   Rufen Sie mithilfe von WIA **IWiaMiniDrvTransferCallback::SendMessage** \_ÜBERTRAGEN\_MSG\_END\_VON\_STREAM und WIA\_ÜBERTRAGEN\_MSG\_END\_VON\_ÜBERTRAGUNG Nachrichten.

-   Rufen Sie IWiaMiniDrvTransferCallback::SendMessage oder IWiaMiniDrvTransferCallback::GetNextStream nach IWiaMiniDrvTransferCallback::SendMessage gibt S\_FALSE oder einen Fehler.

-   Abstürzt oder nicht reagieren, wenn ein Gerät einen Upload anfordert, indem ein Stream ungültig oder leer.

 

### <a name="deviceimagingscannerbasewia20"></a>Device.Imaging.Scanner.Base.wia20

*Scanner und mit mehreren Funktion aus, die Überprüfung Möglichkeit haben müssen die WIA 2.0 Treiberarchitektur entsprechend die Windows-Treiberkits Richtlinien implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Scanner und mit mehreren Funktion aus, die Überprüfung Möglichkeit haben müssen WIA 2.0-Treiberarchitektur gemäß den Richtlinien in der Windows-Treiberkits implementieren.
Scanner unterstützen datenstrombasierte Bild Transfers. In datenstrombasierte Übertragungen Anwendung erhalten WIA zu verwenden, und klicken Sie dann den Treiber Streams liest oder schreibt in das Stream-Objekt. Der Datenstrom möglicherweise einen Dateidatenstrom, einen Datenstrom Arbeitsspeicher oder eine andere Art von Stream-Objekt. Das Stream-Objekt ist für den Treiber transparent. Mithilfe von Streams bietet auch einfache Integration mit dem Bild Verarbeitung Filter. Dadurch werden um Komplikationen zu verhindern, die auftreten, wenn der Zieltyp (Arbeitsspeicher oder Datei).
Scanner müssen ordnungsgemäß implementieren Windows WIA Scanner Element Architektur für Flachbett, Anwendungsdefinitionsdatei und Filmscanner und Scanner, die Speicher verfügen. Beschreiben die WIA Scanner Element Architektur der Windows-Treiberkits Verweis Dokumente und Tools. Gerätehersteller müssen WIA-Unterstützung implementieren, wie in der Windows-Treiberkits beschrieben wird.

*Hinweise zum Entwurf*

WIA 2.0 können neue datenstrombasierte Übertragung Modelle und bestimmten Erweiterungen, die ein Image-Verarbeitung Filter, Segmentierung Filter und Fehlerbehandlung enthalten. Weitere Informationen zu WIA 2.0 finden Sie unter "Introduction to WIA 2.0" unter <http://www.microsoft.com/whdc/device/stillimage/WIA20-intro.mspx> *und "*WIA 2.0" unter <http://msdn.microsoft.com/en-us/library/ms630379.aspx>*.* Neuigkeiten

### <a name="deviceimagingscannerbasewiaproperties"></a>Device.Imaging.Scanner.Base.WIAProperties

*Scanner müssen Support für alle erforderlichen WIA Eigenschaften und Eigenschaftenwerte implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
<p>Windows Server 2016 X64</p>
</td></tr></table>

**Beschreibung**

Die Windows Driver Kit (WDK) Verweis Dokumente und Tools beschreiben die Eigenschaften und Eigenschaftenwerte für WIA. Scanner müssen WIA implementiert, wie in der WDK beschrieben.

<a name="device.imaging.scanner.wsd"></a>
## <a name="deviceimagingscannerwsd"></a>Device.Imaging.Scanner.WSD

### <a name="deviceimagingscannerwsdwsscan"></a>Device.Imaging.Scanner.WSD.WSScan

*Scanner, die eine Verbindung zum Netzwerk besteht, müssen das WS-Scan-Protokoll implementieren.*

<table>
<tr>
<th>Gilt für</th>
<td>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X64</p>
<p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) X86</p>
</td></tr></table>

**Beschreibung**

Dies gilt für Scanner oder Multifunktionsdrucker Scannen Möglichkeit haben, die mit dem Netzwerk verbunden und haben eine physische Scan Schaltfläche auf dem Gerät. Diese Scanner oder Multifunktionsdrucker müssen die folgenden WS-Scan protokollanforderungen implementieren, wie beschrieben in das WS-Scan Spezifikation V1. 0:

-   Das Gerät muss alle Ereignisse und Vorgänge, die die Spezifikation definiert ordnungsgemäß implementieren.

<!-- -->

-   Das Gerät muss die **ScanAvailableEvent** unterstützen, damit Benutzer eine Überprüfung vom Scanner initiieren und schieben das Dokument an eine Anwendung Scan können.

<!-- -->

-   Das Gerät muss den Microsoft WSD Scan Klassentreiber für alle Geräte Features unterstützen, das WS-Scan verfügbar macht.

-   Weist das Gerät Anwendungsdefinitionsdatei und Platte scannen, muss das Gerät über WS-Scan diese Medien unterstützen.

Weitere Informationen finden Sie unter "Implementieren von Web Services auf Geräten für Drucken und Scannen" unter <http://www.microsoft.com/whdc/connect/rally/wsdspecs.mspx>*.*

