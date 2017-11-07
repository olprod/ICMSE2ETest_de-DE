---
author: kpacquer
Description: "Verwenden einen Host-PC zum Neustart eines Geräts mit Modus blinkt, und erhalten Sie Informationen zur version"
ms.assetid: 19499cb0-b45d-4971-9934-778f17a87e52
MSHAttr: PreferredLib:/library/windows/hardware
title: "Verwenden einen Host-PC zum Neustart eines Geräts blinken Modus, und erhalten Sie Informationen zur version"
ms.openlocfilehash: fdaf844d037f01842137db1276f5aa95bbb0e374
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-a-host-pc-to-reboot-a-device-to-flashing-mode-and-get-version-information"></a>Verwenden einen Host-PC zum Neustart eines Geräts blinken Modus und erhalten Sie Informationen zur version


Wenn ein Windows-10-Mobile-Gerät mit einem PC-Host über ein USB-Kabel verbunden ist, können Sie die folgenden Aufgaben in einer Anwendung ausführen, die auf dem Hostcomputer ausgeführt wird. Diese Aufgaben sind in bestimmten Fertigung oder Kunden Vorsicht Szenarien hilfreich.

-   Neustart des Geräts blinken Modus.

-   Abrufen von Informationen zur Version vom Gerät.

Die Host-app verwendet Windows-API tragbaren Geräte für diese Aufgaben.

## <a name="span-idunderstandingthewindowsportabledevicesapispanspan-idunderstandingthewindowsportabledevicesapispanspan-idunderstandingthewindowsportabledevicesapispanunderstanding-the-windows-portable-devices-api"></a><span id="Understanding_the_Windows_Portable_Devices_API"></span><span id="understanding_the_windows_portable_devices_api"></span><span id="UNDERSTANDING_THE_WINDOWS_PORTABLE_DEVICES_API"></span>Grundlegendes zu Windows tragbaren Geräte API


Die Windows Portable Geräte (WPD) API ist eine COM-basierte API, mit dem Computer mit angeschlossene Geräte kommunizieren kann. Weitere Informationen zu dieser API finden, finden Sie in den folgenden Ressourcen:

-   [Tragbare Windows-Geräte](http://msdn.microsoft.com/library/windows/desktop/dd388998.aspx): in diesem Abschnitt der MSDN Library enthält Anleitungen und Verweis Dokumentation Architektur für Windows-API tragbaren Geräte.

-   [Portable Geräte COM-API-Beispiel](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d): in diesem Beispiel wird gezeigt, wie mithilfe der Windows Portable Geräte-API eine Vielzahl von Aufgaben, einschließlich der angeschlossenen Geräte beim Lesen der Eigenschaften von Inhalten auf einem Gerät verbundenen und MTP Befehle zu einem Gerät senden Auflistung ausgeführt.

-   [Portable Geräte Services COM-API-Beispiel](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-b1e2db21): Dieses Beispiel zeigt, wie Sie Windows-API tragbaren Geräten verwenden, um eine Vielzahl von Vorgängen für Device-Dienste, einschließlich Aufzählen von Diensten und Inhalten ausführen.

## <a name="span-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspanspan-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspanspan-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspandiscovering-windows-10-mobile-devices-that-are-connected-to-the-host-computer"></a><span id="Discovering_Windows_10_Mobile_devices_that_are_connected_to_the_host_computer"></span><span id="discovering_windows_10_mobile_devices_that_are_connected_to_the_host_computer"></span><span id="DISCOVERING_WINDOWS_10_MOBILE_DEVICES_THAT_ARE_CONNECTED_TO_THE_HOST_COMPUTER"></span>Ermitteln von Windows 10 Mobile Geräte, die auf den Hostcomputer verbunden sind


Bevor das Hosten von Apps Neustart ein Geräts blinken Modus und Abrufen von Informationen zur Version vom Gerät zu kann, müssen das Hosten von apps alle Geräte erkennen, die mit dem Computer verbunden sind.

1.  Erstellen Sie ein [IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx) -Objekt, und verwenden Sie die [IPortableDeviceManager::GetDevices](http://msdn.microsoft.com/library/windows/desktop/dd388693.aspx) -Funktion, um die Auflistung der Geräte-ID für alle angeschlossenen Geräte abzurufen.

2.  Die Auflistung der Geräte-IDs zu ermitteln, welches Gerät verbundenes Windows 10 Mobile For durchlaufen Jedes Geräte-ID, erstellen Sie ein Objekt [IPortableDevice](http://msdn.microsoft.com/library/windows/desktop/dd319361.aspx) , und klicken Sie dann zum Abrufen des Werts, der den WPD verwenden der Funktionen [IPortableDevice::Content](http://msdn.microsoft.com/library/windows/desktop/dd375688.aspx) und [IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx) \_GERÄT\_MODELL\_UNIQUE\_ID Gerät-Eigenschaft für das Gerät. Wenn das Gerät ein Windows-10-Mobile-Gerät den Wert der WPD ist\_GERÄT\_MODELL\_UNIQUE\_ID-Eigenschaft ist eine GUID, mit dem folgenden Wert.

    ``` syntax
    0x59f12ea9, 0x53ce, 0x452d, 0x97, 0x11, 0xca, 0x4e, 0xea, 0xf1, 0x80, 0x89
    ```

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>Beispiele und weitere Ressourcen

In der [Tragbaren Geräte COM API Beispiel](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d) die folgenden Codebeispiele veranschaulichen die folgenden verwandten Aufgaben:

-   Erstellen eines Objekts [IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx) : finden Sie unter der `ChooseDevice` -Funktion im DeviceEnumeration.cpp.

-   Abrufen der Geräte-IDs aller angeschlossenen Geräte: finden Sie unter der `EnumerateAllDevices` in DeviceEnumeration.cpp Funktion.

-   Abrufen von Eigenschaften des Geräts: finden Sie unter der `ReadContentProperties` -Funktion im ContentProperties.cpp.

Weitere Informationen zum Aufzählen von Geräten und Abrufen von Eigenschaften des Geräts finden Sie in den folgenden Artikeln:

-   [Aufzählen von Geräten](http://msdn.microsoft.com/library/windows/desktop/dd319331.aspx)

-   [Eigenschaften des Geräts](http://msdn.microsoft.com/library/windows/desktop/dd319322.aspx)

-   [Abrufen von Eigenschaften für ein einzelnes Objekt](http://msdn.microsoft.com/library/windows/desktop/dd375726.aspx)

## <a name="span-idrebootingawindows10mobiledeviceintoflashingmodespanspan-idrebootingawindows10mobiledeviceintoflashingmodespanspan-idrebootingawindows10mobiledeviceintoflashingmodespanrebooting-a-windows-10-mobile-device-into-flashing-mode"></a><span id="Rebooting_a_Windows_10_Mobile_device_into_flashing_mode"></span><span id="rebooting_a_windows_10_mobile_device_into_flashing_mode"></span><span id="REBOOTING_A_WINDOWS_10_MOBILE_DEVICE_INTO_FLASHING_MODE"></span>Neustarten von einem Windows-10-Mobile-Gerät in blinkendes Modus


Nachdem Sie ein [IPortableDevice](http://msdn.microsoft.com/library/windows/desktop/dd319361.aspx) -Objekt, das ein Windows 10 Mobile Gerät darstellt haben, können Sie einen MTP Befehl das Telefon neu starten in den Modus blinkt senden.

1.  Erstellen Sie ein [IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx) -Objekt und konfigurieren Sie, dass er die Befehlsparameter MTP einrichten:

    1.  Rufen Sie [IPortableDeviceValues::SetGuidValue](http://msdn.microsoft.com/library/windows/desktop/dd375671.aspx). WPD übergeben\_EIGENSCHAFT\_ALLGEMEINE\_BEFEHL\_KATEGORIE aus, um die *Key* -Parameter und übergeben Sie WPD\_BEFEHL\_MTP\_EXT\_EXECUTE\_BEFEHL\_OHNE\_DATEN\_PHASE.fmtid an der *Value* -Parameter.

    2.  Rufen Sie [IPortableDeviceValues::SetUnsignedIntegerValue](http://msdn.microsoft.com/library/windows/desktop/dd375681.aspx). WPD übergeben\_EIGENSCHAFT\_ALLGEMEINE\_BEFEHL\_-ID an, die *Key* -Parameter und übergeben Sie WPD\_BEFEHL\_MTP\_EXT\_EXECUTE\_BEFEHL\_OHNE\_DATEN\_PHASE.pid an der *Value* -Parameter.

    3.  Rufen Sie die [IPortableDeviceValues::SetUnsignedIntegerValue](http://msdn.microsoft.com/library/windows/desktop/dd375681.aspx) erneut. Übergeben Sie WPD\_EIGENSCHAFT\_MTP\_EXT\_VORGANG\_CODE auf die *Key* -Parameter und übergeben Sie den Wert **0x9401** an der *Value* -Parameter. Dieser Wert gibt den MTP-Befehl, der das Telefon in blinkendes Modus neu gestartet.

    4.  Erstellen eines [**IPortableDevicePropVariantCollection**](https://msdn.microsoft.com/library/windows/hardware/ff597589) -Objekts.

    5.  [**IPortableDeviceValues::SetIPortableDevicePropVariantCollectionValue**](https://msdn.microsoft.com/library/windows/hardware/ff597632)aufrufen. Übergeben Sie WPD\_EIGENSCHAFT\_MTP\_EXT\_VORGANG\_PARAMS Durchlauf der [**IPortableDevicePropVariantCollection**](https://msdn.microsoft.com/library/windows/hardware/ff597589) und der *Schlüssel* Parameter-Objekt wird an der *pValue* -Parameter.

2.  Rufen Sie [IPortableDevice::SendCommand](http://msdn.microsoft.com/library/windows/desktop/dd375691.aspx) , um den Befehl MTP zu senden. Übergeben Sie für den Parameter *pParameters* initialisierten [IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx) Objekts. Dieser Vorgang sendet den Befehl MTP, das Telefon in blinkendes Modus neu zu starten.

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>Beispiele und weitere Ressourcen

Die folgenden Codebeispiele veranschaulichen die Befehlsparameter MTP einrichten und einen Befehl MTP senden:

-   [Ausgabe des Befehls GetNumObjects](http://msdn.microsoft.com/library/windows/desktop/ff384842.aspx): in diesem Thema in der MSDN Library wird gezeigt, wie der standard GetNumObjects MTP-Befehl gesendet werden.

-   Die `SendhintsCommand` Funktion in ContentEnumeration.cpp in der [Tragbaren Geräte COM API Sample](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d).

Weitere Informationen zum Senden von MTP Befehlen mithilfe von Windows-API tragbaren Geräte finden Sie unter [Unterstützung MTP Extensions](http://msdn.microsoft.com/library/windows/desktop/ff384848.aspx).

## <a name="span-idretrievingversioninformationfromawindows10mobiledevicespanspan-idretrievingversioninformationfromawindows10mobiledevicespanspan-idretrievingversioninformationfromawindows10mobiledevicespanretrieving-version-information-from-a-windows-10-mobile-device"></a><span id="Retrieving_version_information_from_a_Windows_10_Mobile_device"></span><span id="retrieving_version_information_from_a_windows_10_mobile_device"></span><span id="RETRIEVING_VERSION_INFORMATION_FROM_A_WINDOWS_10_MOBILE_DEVICE"></span>Abrufen von Informationen zur Version aus einem Windows-10-Mobile-Gerät


Nachdem Sie die Geräte-ID für ein Windows-10-Mobile-Gerät, die mit dem Hostcomputer verbunden ist ermittelt, können Sie 10 für Windows Mobile-spezifischen Gerät Dienst namens MtpDuDeviceService zum Abrufen von Informationen zur Version aus dem Gerät verwenden.

**Hinweis**  
Wenn das Gerät mit einer PIN geschützt ist, ist die MtpDuDeviceService nur verfügbar, wenn die PIN-NUMMER eingegeben wurde, und das Gerät aufgehoben wird.

 

### <a name="span-idopenthemtpdudeviceservicespanspan-idopenthemtpdudeviceservicespanspan-idopenthemtpdudeviceservicespanopen-the-mtpdudeviceservice"></a><span id="Open_the_MtpDuDeviceService"></span><span id="open_the_mtpdudeviceservice"></span><span id="OPEN_THE_MTPDUDEVICESERVICE"></span>Öffnen Sie die MtpDuDeviceService

Zunächst über die Webdienste Gerät zum Öffnen eines [IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx) -Objekts für die MtpDuDeviceService auflisten.

1.  Rufen Sie ein Array mit IDs für alle Gerät Dienste vom Gerät unterstützt werden. Hierzu das vorhandene [IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx) -Objekt, ein [IPortableDeviceServiceManager](http://msdn.microsoft.com/library/windows/desktop/dd319402.aspx) umgewandelt, und die [IPortableDeviceServiceManager::GetDeviceServices](http://msdn.microsoft.com/library/windows/desktop/dd319408.aspx) -Methode aufzurufen. Übergeben Sie die Geräte-ID für das Windows-10-Mobile-Gerät an den *PszPnPDeviceID* -Parameter und der Wert [GUID\_DEVINTERFACE\_WPD\_SERVICE](http://msdn.microsoft.com/library/windows/desktop/dd319319.aspx) an den *GuidServiceCategory* -Parameter. Das Dienst-ID-Array wird in der *pServices* -Parameter zurückgegeben.

2.  Die Dienst-ID-Array durchlaufen Sie, und führen Sie die folgenden Aufgaben für jeden Dienst-ID:

    1.  Erstellen Sie ein [IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx) -Objekt, und rufen Sie die [IPortableDeviceService::Open](http://msdn.microsoft.com/library/windows/desktop/dd319453.aspx) -Funktion, um den Dienst zu öffnen. Übergeben Sie die aktuellen Dienst-ID für den Parameter *PszPnPServiceID* .

    2.  Rufen Sie die Dienst-ID durch Aufrufen der [IPortableDeviceService::GetServiceObjectID](http://msdn.microsoft.com/library/windows/desktop/dd319449.aspx) -Funktion. Sie benötigen die Dienst-ID Zugriff auf die Eigenschaften des Diensts.

    3.  Verwenden Sie die Funktionen [IPortableDeviceService::Content](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx) und [IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx) zum Abrufen der Auflistung von Eigenschaften für den Dienst (ein [IPortableDeviceProperties](http://msdn.microsoft.com/library/windows/desktop/dd388696.aspx) -Objekt).

    4.  Ein [IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx) -Objekt erstellen und Hinzufügen der benutzerdefinierten WPD WPD\_OBJEKT\_-Eigenschaft Namensschlüssel zu dieser Auflistung. Dieser Schlüssel gibt an, dass Sie den Anzeigenamen für den Dienst abrufen.

    5.  Aufruf der Funktion [IPortableDeviceProperties::GetValues](http://msdn.microsoft.com/library/windows/desktop/dd388714.aspx) , um ein Objekt [IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx) abzurufen, die Eigenschaftswerte enthält. Übergeben Sie die Dienst-ID an der *PszObjectID* -Parameter und der initialisierten [IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx) -Objekt an den *pKeys* -Parameter.

    6.  Rufen Sie die [IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx) -Funktion, und übergeben Sie die WPD WPD definiert\_OBJEKT\_Schlüssel für-Eigenschaft einen NAMEN für den *Schlüssel* Parameter.

    7.  Wenn die [IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx) -Funktion die Zeichenfolge **MtpDuDeviceService**zurückgibt, haben Sie das Objekt gefunden, auf dem Telefon Versionsinformationen abgerufen werden müssen. Beenden der Schleife, und fahren Sie mit dem nächsten Abschnitt fort.

        Ist der Name des Diensts nicht **MtpDuDeviceService**, rufen Sie die Funktion [IPortableDeviceService::Close](http://msdn.microsoft.com/library/windows/desktop/dd319441.aspx) , auf die nächste Dienst-ID von [IPortableDeviceServiceManager::GetDeviceServices](http://msdn.microsoft.com/library/windows/desktop/dd319408.aspx)zurückgegebene durchlaufen, und kehren Sie zu Schritt 2 zurück.

### <a name="span-idretrieveversioninformationfromthedevicespanspan-idretrieveversioninformationfromthedevicespanspan-idretrieveversioninformationfromthedevicespanretrieve-version-information-from-the-device"></a><span id="Retrieve_version_information_from_the_device"></span><span id="retrieve_version_information_from_the_device"></span><span id="RETRIEVE_VERSION_INFORMATION_FROM_THE_DEVICE"></span>Abrufen von Informationen zur Version vom Gerät

Nachdem Sie ein [IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx) -Objekt für die MtpDuDeviceService geöffnet haben, können Sie dieses Objekt verwenden, zum Abrufen von Informationen zur Version aus dem Gerät

1.  Verwenden Sie die Funktionen [IPortableDeviceService::Content](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx) und [IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx) zum Abrufen der Auflistung von Eigenschaften für den Dienst (ein [IPortableDeviceProperties](http://msdn.microsoft.com/library/windows/desktop/dd388696.aspx) -Objekt).

2.  Ein [IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx) -Objekt erstellen und Hinzufügen eines Werts [PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx) zu dieser Auflistung, das die Versionsdaten gibt an, den, die Sie vom Gerät abrufen möchten. Der Wert von [PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx) muss folgende Struktur verfügen:

    -   Feld *Fmtid* benötigen den folgenden GUID-Wert:

        ``` syntax
        0x9BFC64C1, 0x19C9, 0x4F3D, 0xA1, 0x4D,  0xC8,  0xDB,  0xE0,  0x47,  0x5D,  0x13
        ```

    -   Feld *pid* muss eines der in der folgenden Tabelle aufgeführten Werte sein.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Gerätedaten abrufen</th>
    <th align="left">PID-Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Die Build-Zeichenfolge, damit das Bild auf dem Gerät</p></td>
    <td align="left"><p>Verwenden Sie die Daten, die durch die folgenden pid-Werte zurückgegeben, die Zeichenfolge Build erstellen:</p>
    <ul>
    <li><p>4 (der Name der internen Microsoft Zweigniederlassung des Betriebssystems aus erstellt wurde)</p></li>
    <li><p>6 (der Windows-Buildnummer)</p></li>
    <li><p>7 (10 Mobile Windows-Buildnummer)</p></li>
    <li><p>8 (der Zeitstempel für den Build)</p></li>
    </ul>
    <p>Eine Zeichenfolge zum Beispiel Build ist WPMAIN.9600.12186.20130906 1624.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Die Version des Betriebssystems</p></td>
    <td align="left"><p>12</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Der Name der OEM-Gerät</p></td>
    <td align="left"><p>15</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Die Firmwareversion</p></td>
    <td align="left"><p>16</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Die Version SoC</p></td>
    <td align="left"><p>17</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Die Version der Software radio</p></td>
    <td align="left"><p>18</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Die Hardwareversion radio</p></td>
    <td align="left"><p>19</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Startladeprogramm-version</p></td>
    <td align="left"><p>20</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Die Plattform-ID (von SMBIOS).</p></td>
    <td align="left"><p>29</p></td>
    </tr>
    </tbody>
    </table>

     

3.  Rufen Sie die [IPortableDeviceProperties::GetValues](http://msdn.microsoft.com/library/windows/desktop/dd388714.aspx) -Funktion, um ein [IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx) -Objekt abzurufen, die die angeforderten Informationen enthält. Übergeben Sie die Dienst-ID an der *PszObjectID* -Parameter und der initialisierten [IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx) -Objekt an den *pKeys* -Parameter.

4.  Aufruf der Funktion [IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx) . Übergeben Sie für den Parameter *Schlüssel* den gleichen [PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx) -Wert, den Sie zuvor verwendet. Diese Funktion gibt die der angeforderten Versionsinformationen im Parameter *pValue* .

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>Beispiele und weitere Ressourcen

In der [Tragbaren Geräte Services COM API-Beispiel](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-b1e2db21) die folgenden Codebeispiele veranschaulichen die folgenden verwandten Aufgaben:

-   Auflisten von Gerät Dienste: finden Sie unter der `EnumerateContactsServices` in ServiceEnumeration.cpp Funktion.

-   Lesen der Eigenschaften eines Diensts: finden Sie unter der `ReadContentProperties` in ContentProperties.cpp Funktion.

Weitere Informationen über das Arbeiten mit Gerät Services finden Sie unter [Öffnen eines Diensts](http://msdn.microsoft.com/library/windows/desktop/dd375706.aspx), [Zugreifen auf den Dienst Objekteigenschaften](http://msdn.microsoft.com/library/windows/desktop/dd743198.aspx) und [Abrufen von Objekt Eigenschaften](http://msdn.microsoft.com/library/windows/desktop/dd375722.aspx).

 

 





