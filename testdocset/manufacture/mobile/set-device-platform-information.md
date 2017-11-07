---
title: "Set-Plattform Geräteinformationen"
description: "Informationen Sie zu den erforderlichen Komponenten für die Erstellung von einem Bild, das an ein mobiles Gerät, einschließlich weiteres Gerät Plattforminformationen wie Partnernamen, Versionsnummern und Gerätenamen, bevor das Bild für den Einzelhandel Geräte definitiv zugeordnet werden kann."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3bf177d9-fd4a-4221-958b-ed98e5bd4e70
ms.openlocfilehash: 2261e7ef0bd9c0a929a9b4fc83f39e680db4be4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="set-device-platform-information"></a>Set-Plattform Geräteinformationen


Um die Erstellung eines Images vorzubereiten, müssen OEMs erforderlichen Informationen für die Plattform Zielgerät angeben, um die folgenden Aufgaben ausführen:

-   Legen Sie mehrere Geräte Plattformwerte in die Struktur der SMBIOS System, auf den Geräten.

-   Erstellen Sie ein *Geräteplattform* -Paket.

Der Engineering-Toolsets von Microsoft bereitgestellten blinkendes vergleicht die Werte in das System die Struktur der SMBIOS mit den entsprechenden Werten im Paket Plattform Gerät vor blinkt ein Bild. Diese Überprüfung wird sichergestellt, dass ein Bild zu einem bestimmten Gerät zugeordnet werden kann, nur dann, wenn es für die entsprechende Geräteplattform erstellt wurde. Es wird empfohlen, dass die gleiche Überprüfung führen Sie die blinkende Tools, die für ihre Umgebung Fertigung OEMs erstellen. Weitere Informationen finden Sie unter [Überprüfen der Plattform Geräteinformationen vor blinkendes eines Bilds zu einem Gerät](#validating) in diesem Thema.

**Hinweis**  
In diesem Thema werden die erforderlichen Komponenten für die Erstellung von einem Bild, das zu einem Gerät zugeordnet werden kann. OEMs müssen zusätzliche Plattform Geräteinformationen Partnernamen, Versionsnummern und Gerätenamen einschließlich, bevor ein Bild für den Einzelhandel Geräte abgeschlossen ist festgelegt.

 

## <a name="a-href-idsetting-smbios-system-information-values-asetting-smbios-system-information-values"></a><a href="" id="setting-smbios-system-information-values-"></a>Festlegen von SMBIOS System Informationen-Werten


Auf jedem Geräteplattform müssen OEMs sicher, dass die folgenden Werte in das System die Struktur der SMBIOS festgelegt werden:

-   PhoneManufacturer

-   Familie

-   Produktname

-   Version

Diese Werte können durch den Hersteller SoC auf die Standardwerte festgelegt werden. OEMs müssen diese durch die Werte für die Geräteplattform ersetzen. OEMs müssen auch andere Werte SMBIOS gemäß den Hersteller SoC festgelegt. Weitere Informationen dazu, wie Sie diese Werte lesen oder festlegen finden Sie in Dokumentation des Herstellers SoC.

Weitere Informationen über die erwartete Größen und Datentypen für diese Werte finden Sie im Abschnitt 7.2 in [System Management BIOS (SMBIOS) Reference Specification](http://go.microsoft.com/fwlink/?LinkId=267529) (PDF).

**Wichtige**  
Die Einstellung PhoneManufacturer muss einen von Microsoft, die der OEM entspricht, angegebenen Code enthalten. Diese Einstellung wird für die Zielgruppenadressierung Geräteupdates, für die Verbindung mit dem Store-in-a-Store in Windows Store und Watson-Berichten verwendet. Der Wert muss eine gültige OEM-ID. Wenn Sie die gültigen OEM-ID erhalten möchten, die für Sie gilt, wenden Sie sich an Ihrem Microsoft-Partner.

 

## <a name="creating-the-device-platform-package"></a>Erstellen das Gerät Plattform-Paket


Das Gerät Plattform Paket enthält nur eine Datei: eine XML-Datei mit dem Namen **OEMDevicePlatform.xml** , die Informationen speziell für die Geräteplattform enthält, für die das Bild erstellt wird. Jedes Bild muss ein Gerät Plattform-Paket enthalten. OEMs müssen das Gerät Plattform Paket angeben, mit dem OEMDevicePlatformPackages-Element in einer FM-Datei, die im Bild enthalten ist.

Um das Gerät Plattform-Paket zu erstellen, erstellen Sie zuerst eine OEMDevicePlatform.xml-Datei, die Plattform Geräteinformationen im Format erforderlichen Schema enthält. Erstellen Sie dann ein Paket, das diese XML-Datei enthält.

### <a name="creating-the-xml-file"></a>Erstellen der XML-Datei

Die OEMDevicePlatform.xml-Datei enthält ein einzelnes **OEMDevicePlatform** -Element mit der folgenden untergeordneten Elemente.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>MinSectorCount</strong></p></td>
<td><p>Dieser Wert gibt die minimale Bereiche, die in einem Gerätespeicher erwartet werden. Imaging-Tool verwendet diesen Wert, um sicherzustellen, dass der Inhalt auf dem Gerät passt. Die Anzahl der tatsächlichen Sektor möglicherweise mehr als diesem minimale. Die Größe ist 512 Bytes an, wie in das Gerät Layout-Paket von Microsoft bereitgestellten definiert.</p></td>
</tr>
<tr class="even">
<td><p><strong>DevicePlatformID</strong></p></td>
<td><p>Dies ist einer der folgenden Zeichenfolgen, die von Werten vom SMBIOS System die Struktur verkettet und mit jeder Wert, getrennt durch einen Punkt (.) besteht aus:</p>
<ul>
<li><p><em>PhoneManufacturer</em>. - <em>Familie</em>. <em>Produktname</em></p></li>
<li><p><em>PhoneManufacturer</em>. <em>Familie</em>. <em>Produktname</em>. <em>Version</em></p></li>
</ul>
<p>OEMs können, ob die <em>Version</em> der einzuschließenden in dieser Zeichenfolge wird oder nicht.</p>
<p>Wenn in der Anwendung blinkendes Microsoft Gerät Plattform Validierung aktiviert ist, werden in dieser Zeichenfolge angegebenen Werte mit den entsprechenden Werten in das System die Struktur der SMBIOS verglichen. Weitere Informationen finden Sie unter [Verwenden der blinkende Tools von Microsoft bereitgestellt](use-the-flashing-tools-provided-by-microsoft.md).</p>
<p>Gerät-Plattform-XML-Datei kann nur ein <strong>DevicePlatformID</strong> oder <strong>DevicePlatformIDs</strong> -Element, jedoch nicht beide haben.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DevicePlatformIDs</strong></p></td>
<td><p>OEMs können mehrere Geräts festlegen Plattform-IDs mit den folgenden XML-Syntax hat jede Zeichenfolge das gleiche Format wie für das <strong>DevicePlatformID</strong> -Element beschrieben.</p>
<pre class="syntax" space="preserve"><code>&lt;DevicePlatformIDs&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z101._012&lt;/ID&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z101._013&lt;/ID&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z102&lt;/ID&gt;
&lt;/DevicePlatformIDs&gt;</code></pre>
<p>Gerät-Plattform Validierung erfolgreich, wenn die IDs der PhoneManufacturer.Family.Product.Version oder der angegebenen PhoneManufacturer.Family.Product übereinstimmen.</p>
<p>Gerät-Plattform-XML-Datei kann nur ein <strong>DevicePlatformID</strong> oder <strong>DevicePlatformIDs</strong> -Element, jedoch nicht beide haben.</p></td>
</tr>
<tr class="even">
<td><p><strong>AdditionalMainOSFreeSectorsRequest</strong></p></td>
<td><p>Optional Dieser Wert gibt die Anzahl der Bereiche durch das Betriebssystem für zukünftige Updates reservierter Speicher-Pool hinzugefügt. Es gibt keine Garantie, dass die Bereiche, die mit dem <strong>AdditionalMainOSFreeSectorsRequest</strong> -Element angegeben für OEM-spezifische Updates immer verfügbar ist. die Bereiche werden stattdessen auf einem einzelnen Speicherpool hinzugefügt, die für alle Updates von Microsoft und OEMs reserviert ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MainOSRTCDataReservedSectors</strong></p></td>
<td><p>Optional Dieser Wert gibt die Anzahl der Bereiche durch das Betriebssystem für die Verwendung von Common Language Runtime-Konfigurationsdaten während der Sicherung und Wiederherstellung reserviert Speicher-Pool hinzugefügt. Es kann bis zu 100 MB reserviert werden.</p>
<p>Im folgenden Beispiel wird veranschaulicht, 50 MB reservieren.</p>
<pre class="syntax" space="preserve"><code>&lt;MainOSRTCDataReservedSectors&gt;102400&lt;/MainOSRTCDataReservedSectors&gt;</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>CompressedPartitions</strong></p></td>
<td><p>Optional Verwenden Sie dieses Element, um CompactOS in Ihrem mobilen Bild zu aktivieren.</p>
<p>Dieses Element enthält eine oder mehrere untergeordnete <strong>Namen</strong> Elemente, die angeben, welche Partitionen zu komprimieren. Derzeit die einzige unterstützte Partition ist die Main OS Partition, und die einzige unterstützte unter dieses Element ist <strong>MainOS</strong>, wie im folgenden Beispiel dargestellt.</p>
<pre class="syntax" space="preserve"><code>&lt;CompressedPartitions&gt;
  &lt;Name&gt;MainOS&lt;/Name&gt;
&lt;/CompressedPartitions&gt;</code></pre>
<div class="alert">
<strong>Wichtig</strong>  Der Hostcomputer, auf dem das Bild erstellt wird, muss Windows 10 ausgeführt werden. Sie können auch das Bild auf einem Windows 8.1-Hostcomputer erstellen, oder Windows Server 2012 R2 mit [KB3066427](https://support.microsoft.com/kb/3066427) installiert haben.
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

Im folgenden Beispiel wird eine OEMDevicePlatform.xml-Datei.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<OEMDevicePlatform xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
   xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
   <MinSectorCount>20971520</MinSectorCount>
   <DevicePlatformID>Contoso.ContosoFamily.ContosoDevice.v1</DevicePlatformID>
   <AdditionalMainOSFreeSectorsRequest>204800</AdditionalMainOSFreeSectorsRequest>
</OEMDevicePlatform>
```

### <a name="creating-the-package"></a>Erstellen des Pakets

Führen Sie zum Erstellen eines Pakets, das die OEMDevicePlatform.xml-Datei enthält, die Anweisungen in [Paketen erstellen](creating-mobile-packages.md)aus. Im folgenden Beispiel wird eine Gerät Plattform XML-Datei, die eine einzelnes Gerät Plattform-ID angibt

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
   Owner="OEMName" OwnerType="OEM" Component="OEMDevicePlatform" 
   ReleaseType="Production" Platform="DeviceName">
   <Components>
      <OSComponent>
         <Files>
            <File Source="OEMDevicePlatform.xml" DestinationDir="$(runtime.windows)\ImageUpdate" 
                  Name="OEMDevicePlatform.xml"/>
         </Files>
      </OSComponent>
   </Components>
</Package>
```

Beachten Sie die folgenden Details über die in diesem Beispiel wird ein:

-   Achten Sie darauf, dass die Einträge "*OEMName*" und "*DeviceName*" durch die entsprechenden Werte zu ersetzen.

-   Die `$(runtime.windows)` Zeichenfolge im Pfad für das **DestinationDir** -Attribut ein global definierte Makro ist. Der Pfad **DestinationDir** muss mit einem global definierte Makro für ein Verzeichnis beginnen. Weitere Informationen über das Attribut **DestinationDir** finden Sie unter [Specifying Dateien und Registrierungseinträge in einer Projektdatei Paket](https://msdn.microsoft.com/windows/hardware/dn789219). Weitere Informationen zu Makros finden Sie unter [primäre Elemente und Attribute einer Projektdatei Paket](https://msdn.microsoft.com/library/windows/hardware/dn756796).

**Das Gerät Plattform-Paket einschließlich im Bild**

Nachdem das Gerät Plattform-Paket erstellt wird, muss sie mithilfe des OEMDevicePlatformPackages-Elements in einer Featuremanifestdatei angegeben werden. Weitere Informationen finden Sie unter [Feature Dateiinhalten manifest](feature-manifest-file-contents.md).

## <a name="a-href-idvalidatingavalidating-the-device-platform-information-before-flashing-an-image-to-a-device"></a><a href="" id="validating"></a>Überprüfen der Plattform Geräteinformationen vor blinkendes eines Bilds zu einem Gerät


Um sicherzustellen, dass ein Bild zu einem Gerät zugeordnet werden soll für das Gerät tatsächlich entworfen wurde, die blinkende Toolsets OEMs erstelltes der *Hersteller*, *Familienangehörige*und *Produktname* SMBIOS System Informationen Strukturwerte auf dem Gerät überprüfen und vergleichen diese Werte gegen den *Hersteller*. *Familie*. *Produktname* -Teil der Zeichenfolge **DevicePlatformID** im Paket Plattform Gerät. Das blinkende Tool sollte mit dem blinkende fortgesetzt werden nur, wenn diese Werte übereinstimmen. Das blinkende Tool kann optional überprüfen, ob auch mit dem Wert der *Version* übereinstimmt, aber dies nicht erforderlich ist. Weitere Informationen finden Sie unter [Developing benutzerdefinierte OEM blinkende Tools](developing-custom-oem-flashing-tools.md).

Standardmäßig überprüft der Anwendung, die von Microsoft bereitgestellten blinkendes Gerät clientseitigen UEFI an, dass die Plattform Geräteinformationen im SMBIOS die Plattform Geräteinformationen im Bild übereinstimmt. Weitere Informationen finden Sie unter [Verwenden der blinkende Tools von Microsoft bereitgestellt](use-the-flashing-tools-provided-by-microsoft.md).

Beim Migrieren von ein Telefon einen neuen Satz von Gerät Plattformwerte erforderlich ist, empfiehlt Microsoft den folgenden Vorgang aus:

-   Erstellen Sie ein Übergang Bild, das die neuen SMBIOS Werte enthält jedoch weiterhin verweist auf die alte **DevicePlatformID** -Zeichenfolge im Paket Plattform Gerät.

-   Flash dieses Bild, auf das Telefon an. Dieser Prozess wird die SMBIOS Werte auf das Telefon mit den neuen SMBIOS-Werten überschrieben.

-   Aktualisieren Sie in der Definition Bild die Zeichenfolge **DevicePlatformID** das Gerät Plattform-Paket in den neuen SMBIOS Werten entsprechen. Dadurch wird das Bild, das an das Telefon aktualisiert werden.

## <a name="related-topics"></a>Verwandte Themen


[Entwickeln von benutzerdefinierten OEM Tools blinken](developing-custom-oem-flashing-tools.md)

[Verwenden Sie die blinkende von Microsoft bereitgestellten tools](use-the-flashing-tools-provided-by-microsoft.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Set%20device%20platform%20information%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





