---
title: Inhalt der Datei OEMInput
description: "Eine OEMInput.xml-Datei enthält die erforderlichen und optionalen Elemente zum Definieren einer mobilen Bild verwendet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 945961d7-382e-4d66-9e00-bc01d3fbfa86
ms.openlocfilehash: 333ebba504c6dfe05b9962277cf0c257dffea82d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oeminput-file-contents"></a>Inhalt der Datei OEMInput


Eine OEMInput.xml-Datei enthält die erforderlichen und optionalen Elemente zum Definieren einer mobilen Bild verwendet. Das Betriebssystem verwendet diese Datei, um festzustellen, Applikationen Prozessor, build Type, Benutzeroberfläche Sprachen, Region Standardformat, Auflösung und andere Eigenschaften zum Einschließen in das Bild, das generiert wird.

Dieses Thema enthält eine vollständige Auflistung der XML-Schema für die Datei.

## <a name="required-elements-in-the-oeminput-file"></a>Erforderliche Elemente in der Datei OEMInput


In der folgenden Tabelle werden die erforderlichen Elemente in der Datei OEMInput beschrieben.

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
<td><p><strong>OEMInput</strong></p></td>
<td><p>Das Stammelement für die OEMInput-Datei.</p></td>
</tr>
<tr class="even">
<td><p><strong>Beschreibung</strong></p></td>
<td><p>Eine Zeichenfolge, die das Bild beschreibt. OEMs sollten hinzufügen, dass eine Beschreibung ein, die speziell für das Gerät das Bild wird für erstellt wird.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SOC</strong></p></td>
<td><p>Eine Zeichenfolge, die auf dem Gerät verwendet SoC identifiziert. Die folgenden Werte werden derzeit unterstützt:</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Anwendungen Prozessor</th>
<th>Unterstützte SOC Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>QC8974</strong></p></td>
<td><ul>
<li><p><strong>QC8974</strong>: erstellt ein Bild ohne eine Absturz Dump Partition. Verwenden Sie diesen Wert für Produktion Bilder.</p></li>
<li><p><strong>QC8974_Test</strong>: ein Bild mit einer Absturz Dump Partition mit mehr als 2 GB Größe erstellt. Verwenden Sie diesen Wert beim Test Bilder für Geräte mit mehr als 4 GB Speicher zu generieren.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>QC8x26</strong></p></td>
<td><ul>
<li><p><strong>QC8x26</strong>: erstellt ein Bild, ohne eine Dump Partitionen stürzt ab. Verwenden Sie diesen Wert für Produktion Bilder.</p></li>
<li><p><strong>QC8x26_Test</strong>: ein Bild mit zwei dedizierte Absturz Dump Partitionen auf eMMC erstellt. Die Gesamtgröße der zwei Partitionen ist 3,5-Mal die Größe des Gesamtspeichers RAM auf dem Telefon. Um ein Testbild zu erstellen, die auf einem Gerät mit mindestens 8 GB eMMC vollständige speichert und offline speichert unterstützt, verwenden Sie diesen Wert und das Feature DEDICATEDUMPONEMMC enthält.</p></li>
<li><p><strong>QC8x26_UseSD_Test</strong>: ein Abbild ohne dedizierten Partitionen zum Speichern von Abstürzen speichert auf Geräten mit weniger als 8 GB eMMC erstellt. Zum Erstellen von vollständige, Kernel oder offline Absturz speichert eine SD-Karte muss vorhanden sein, und das Feature DEDICATEDUMPONSD Feature muss angegeben werden, zur Umleitung von speichert an die SD-Karte. Die empfohlene Größe der SD-Karte für offline speichert beträgt 16 oder 32 GB. Weitere Informationen zum Angeben der Debugfeatures finden Sie unter <a href="optional-features-for-building-images.md">optionale Features zum Erstellen von Bildern</a>.</p></li>
</ul>
<p>Um eine QC8x26 Testbild zu erstellen, der vollständigen speichert und offline speichert auf einem Gerät mit weniger als 8 GB eMMC unterstützt, verwenden Sie QC8x26_UseSD_Test. Die DEDICATEDUMPONSD-Funktion zum Weiterleiten von speichert an die SD-Karte enthält. Die empfohlene Größe der SD-Karte für offline speichert beträgt 16 oder 32 GB.</p>
<p>Um ein Bild des QC8x26 Test zu erstellen, die auf einem Gerät mit mindestens 8 GB eMMC vollständige speichert und offline speichert unterstützt, <strong>QC8x26_Test</strong> verwenden und die DEDICATEDUMPONEMMC-Funktion enthält.</p>
<p>Um ein QC8x26 Einzelhandel oder Produktion Bild zu erstellen, in denen vollständige speichert und offline speichert nicht aktiviert sind, verwenden Sie <strong>QC8x26</strong>aus.</p></td>
</tr>
<tr class="odd">
<td><p><strong>QC8960</strong></p></td>
<td><ul>
<li><p><strong>QC8960</strong>: erstellt ein Bild ohne eine Absturz Dump Partition. Verwenden Sie diesen Wert für Produktion Bilder.</p></li>
<li><p><strong>QC8960_Test</strong>: erstellt ein Bild mit einer Absturz Dump Partition mit mehr als 2 GB Größe. Verwenden Sie diesen Wert beim Generieren von Test-Bilder für Telefone mit mehr als 4 GB an Speicher.</p></li>
<li><p><strong>QC8960_Test_4gb</strong>: erstellt ein Bild mit einer Absturz Dump Partition mit ungefähr 600 MB groß, groß genug ist, um ein einzelnes Absturzabbild für ein Gerät mit 512 MB RAM zu speichern. Verwenden Sie diesen Wert beim Generieren von Test-Bilder für Telefone mit nur 4 GB an Speicher.</p></li>
</ul>
<div class="alert">
<strong>Wichtige</strong>  
<p>Die 8960 SOC Optionen müssen nur für Bilder verwendet werden, die zum Erstellen von Updates für Windows 10 Mobile verwendet werden. Weitere Informationen finden Sie unter <a href="../../service/mobile/index.md">Update</a>.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
<tr class="even">
<td><p><strong>Gerät</strong></p></td>
<td><p>Eine Zeichenfolge zur Identifizierung des Modells ist für das Bild erstellt wird. Verwenden Sie diese Einstellung, um Pakete mit der <strong>DeviceSpecificPackages</strong> und der <strong>OEMDevicePlatformPackages</strong> Elemente in der Feature-Manifestdatei das entsprechende <strong>Gerät</strong> -Attribut markiert einzubeziehen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReleaseType</strong></p></td>
<td><p>Eine Zeichenfolge, die Version des Bilds angibt. Verwenden Sie diese Einstellung, um Pakete mit der entsprechenden <strong>ReleaseType</strong> Attributwert ein <strong>ReleasePackages</strong> -Element in der Feature-Manifestdatei markiert einzubeziehen. Die folgenden Werte werden unterstützt:</p>
<ul>
<li><p><strong>Produktion</strong>: Dieser Wert gibt an, dass alle Pakete im Bild Produktion angemeldet sind, und das Bild nur Produktion-Pakete (d. h., Pakete enthält, wobei das <strong>ReleaseType</strong> -Attribut in der XML-Paket auf <strong>Produktion</strong>festgelegt ist). Darüber hinaus müssen alle im Besitz der Microsoft Pakete mit einem Microsoft ausgestellten Zertifikat signiert werden. Dieser Wert sollte nur verwendet werden, beim Generieren des endgültigen Bilds.</p></li>
<li><p><strong>Testen Sie</strong>: Dieser Wert gibt an, dass das Bild kann Test signierte Pakete als auch Produktion signierten Paketen enthalten, und das Abbild eine Mischung aus Produktions- und Test-Pakete (d. h., Pakete enthält, in dem das <strong>ReleaseType</strong> -Attribut in das XML-Paket <strong>Testen</strong> oder <strong>Produktion</strong>festgelegt ist). Dieser Wert wird in der Produktion, Test, Integrität und Fertigung Bilder verwendet. Weitere Informationen zu anderen Bildtypen finden Sie unter <a href="building-a-phone-image-using-imggencmd.md">Erstellen von ein Telefon Bild ImgGen.cmd verwenden</a>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Buildtyp</strong></p></td>
<td><p>Eine Zeichenfolge, die angibt, ob beim Erstellen des Abbilds checked Build oder kostenlose Pakete verwendet wird. Wenn Sie ein getestetes Build mit Debugcode generiert werden soll, geben Sie <strong>Chk</strong>. Um einen freien Build ohne Debuggen Code generiert werden soll, geben Sie <strong>Fre</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SupportedLanguages</strong></p></td>
<td><p>Enthält die folgenden untergeordneten Elemente, die die Unterstützung von Sprachen in generierten Bilds angeben:</p>
<ul>
<li><p><strong>UserInterface</strong>: eine Zeichenfolge mit der Sprache für die Anzeigesprachen zum Einschließen in das Bild codes. Wenn mehrere Sprachcodes aufgelistet werden, sie müssen jedes eingeschlossen werden in einem eigenen <code>&lt;language&gt;</code> blockieren.</p></li>
<li><p><strong>Tastatur</strong>: eine Zeichenfolge, die Sprache enthält, codes für die Tastatursprachen zum Einschließen in das Bild (d. h., in welcher Text Korrektur und Vorschläge unterstützten, Sprachen). Wenn mehrere Sprachcodes aufgelistet werden, sie müssen jedes eingeschlossen werden in einem eigenen <code>&lt;language&gt;</code> blockieren.</p></li>
<li><p><strong>Speech</strong>: eine Zeichenfolge, die Sprache enthält, codes für die Sprache Sprachen zum Einschließen in das Bild. Wenn mehrere Sprachcodes aufgelistet werden, sie müssen jedes eingeschlossen werden in einem eigenen <code>&lt;language&gt;</code> blockieren.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>BootUILanguage</strong></p></td>
<td><p>Eine Zeichenfolge, die den Sprachcode für die standardmäßige gibt Anzeigesprache zum Einschließen in das Bild.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BootLocale</strong></p></td>
<td><p>Eine Zeichenfolge, die den Sprachcode für die Region Standardformat für das Bild angibt.</p></td>
</tr>
<tr class="even">
<td><p><strong>Auflösung</strong></p></td>
<td><p>Enthält ein Element der <strong>Lösung</strong> . Das <strong>Lösung</strong> -Element enthält eine Zeichenfolge, die eine Auflösung unterstützt durch das Bild darstellt. Die folgenden Werte werden unterstützt: <strong>480 x 800</strong>, <strong>540 960 x</strong>, <strong>720 x 1280</strong>, <strong>768 1280 x</strong>und <strong>1080 1920 x</strong>. Der Build enthält die entsprechende Lösung Pakete des Bilds für die angegebene Auflösung.</p>
<p>Beachten Sie, dass einige Auflösung nur für bestimmte Anwendungen Prozessoren unterstützt werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="optional-elements-in-the-oeminput-file"></a>Optionale Elemente in der Datei OEMInput


Die folgende Tabelle beschreibt die optionalen Elemente, die in der Datei OEMInput OEMs enthalten kann.

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
<td><p><strong>PA</strong></p></td>
<td><p>Eine Zeichenfolge zur Identifizierung den Hersteller der SoC auf dem Gerät verwendet. Verwenden Sie diese Einstellung, um Pakete mit der entsprechenden <strong>SVPackages</strong> Elements in der Feature-Manifestdatei markiert einzubeziehen.</p></td>
</tr>
<tr class="even">
<td><p><strong>Produkt</strong></p></td>
<td><p>Eine Zeichenfolge, die angibt, welche OS Variant erstellen. Geben Sie den Wert <strong>Manufacturing OS</strong> Schwelle MMOS (Microsoft Manufacturing OS) erstellen die den minimalen Satz an erforderlichen MMOS OS Pakete enthält. Zum Erstellen eines vollständigen Betriebssystemabbilds Auslassen dieses Elements.</p>
<p>Weitere Informationen zum Erstellen eines Abbilds MMOS finden Sie unter <a href="mmos-image-definition.md">MMOS Bild Definition</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FormatDPP</strong></p></td>
<td><p>Eine Zeichenfolge, die angibt, ob eine leere formatierte Gerät provisioning Partition (DPP) im Bild umfassen. Geben Sie den Wert <strong>true,</strong> um ein Bild zu generieren, die eine leere formatierte DPP enthält. Geben Sie den Wert <strong>false</strong> oder lassen Sie dieses Element, um zu verhindern, dass den DPP überschrieben werden aus.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcludePrereleaseFeatures</strong></p></td>
<td><p>Eine Zeichenfolge, die angibt, ob Features als Vorabversion angesehen werden, werden aus dem Build ausgeschlossen. Geben Sie den Wert <strong>"true"</strong> zum Generieren eines Bilds, das die Vorabversion Features ausschließt, geben Sie <strong>false</strong> einbeziehen. Builds, die mit ExcludePrereleaseFeatures auf <strong>true</strong>festgelegt erstellt werden kann als bezeichnet werden &quot;beschränkt&quot; erstellt. Wenn dieser Eintrag nicht in der Datei OEMInput enthalten ist, werden die Vorabversion Features im Bild enthalten.</p>
<p>Wenn diese Option auf <strong>true</strong> festgelegt ist möglicherweise einige Features Ersatz im Bild vorhanden. Wenn kein Ersatz Features konfiguriert sind, klicken Sie dann werden nicht im Build vorhanden sie.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Features</strong></p></td>
<td><p>Enthält eine oder mehrere untergeordnete Elemente, die angeben, die Namen der optionalen Features verwiesen wird, wenn das Bild zu erstellen. Jede Funktion entspricht mindestens Pakete, die im Bild eingeschlossen werden sollen. Um ein Feature zu verwenden, muss das Feature in einem FeatureManifest definiert werden, die unter dem Element <strong>AdditionalFMs</strong> aufgeführt wird. Weitere Informationen zu den Features und Feature-Manifests finden Sie unter <a href="building-a-phone-image-using-imggencmd.md">Erstellen von ein Telefon Bild mit ImgGen.cmd</a> und <a href="feature-manifest-file-contents.md">Feature-Manifestdatei Inhalt</a>.</p>
<p>Das <strong>Features</strong> -Element enthält eine oder mehrere der folgenden untergeordneten Elemente:</p>
<ul>
<li><p><strong>Microsoft</strong> enthält eine oder mehrere <strong>Feature</strong> -Elemente, die Namen der optionale Microsoft Funktionen zum Einschließen in das Bild angeben. Weitere Informationen zu Microsoft-Features finden Sie unter <a href="optional-features-for-building-images.md">optionale Features zum Erstellen von Bildern</a>.</p></li>
<li><p><strong>OEM</strong> enthält eine oder mehrere <strong>Feature</strong> -Elemente, die die Namen der optionale OEM-Features zum Einschließen in das Bild angeben. Weitere Informationen zum Hinzufügen von OEM-Features finden Sie unter <a href="feature-manifest-file-contents.md">Feature Dateiinhalt manifest</a>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>AdditionalFMs</strong></p></td>
<td><p>Enthält eine oder mehrere <strong>AdditionalFM</strong> -Elemente. Jedes Element <strong>AdditionalFM</strong> enthält einen String-Wert, der den vollständigen Pfad der einer Featuremanifestdatei verweisen beim Erstellen von das Bild angibt.</p>
<p>Feature-Manifests definieren die Pakete, die automatisch in bestimmte Arten von Bilder enthalten sind und Feature-Namen, die unter dem Element <strong>Features</strong> Einbeziehung zusätzliche Pakete im Bild verwiesen werden können auch definieren. Weitere Informationen zu Features Manifestdateien finden Sie unter <a href="feature-manifest-file-contents.md">Feature Dateiinhalten manifest</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PackageFiles</strong></p></td>
<td><p>Enthält einen Satz von <strong>PackageFile</strong> -Elementen, die zusätzliche Pakete zum Einschließen in das Bild angeben.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Das <strong>PackageFiles</strong> Element kann nur in vorab retail Bilder wie Test und Integrität Bilder verwendet werden. Es sollte nur in Szenarien verwendet werden, Sie ein Ad-hoc-Paket schnell zu einer Überprüfung vor dem retail Bild hinzufügen müssen. Im Einzelhandel Bilder müssen alle Pakete mit ein Feature, das unter dem Element <strong>Features</strong> oder in einer Feature-Manifestdatei, die unter dem Element <strong>AdditionalFMs</strong> verwiesen wird aufgeführt ist verwiesen werden. Weitere Informationen zu den Features und Feature-Manifests finden Sie unter <a href="building-a-phone-image-using-imggencmd.md">Erstellen von ein Telefon Bild mit ImgGen.cmd</a> und <a href="feature-manifest-file-contents.md">Feature-Manifestdatei Inhalt</a>.</p>
</div>
<div>
 
</div>
<p>Jedes <strong>PackageFile</strong> -Element enthält einen Textwert, der den Pfad und den Namen eines einzelnen Pakets angibt. Wenn keine zusätzlichen Pakete auf das Bild hinzugefügt werden, muss das <strong>PackageFiles</strong> -Element aus der Datei angegeben werden. Die Pakete können an einem Standort, auf dem Entwicklungscomputer installiert sein. Eine Umgebungsvariable kann in den Pfad zum jedes Paket im <strong>PackageFile</strong> -Element verwendet werden.</p>
<p></p></td>
</tr>
</tbody>
</table>

 

## <a name="xml-schema-for-the-oeminput-file"></a>XML-Schema für die OEMInput-Datei


Das folgende XML-Schema wird die Datei OEMInput überprüft. Mit diesem Schema können Sie um die OEMInput-XML-Dateien zu überprüfen, die Sie erstellen. Zu diesem Zweck in Visual Studio müssen speichern Sie dies zunächst in einer Datei mit der Erweiterung XSD. Wählen Sie in Visual Studio **XML** &gt; **Schemas** und wählen Sie die Datei, die Sie erstellt haben. Jegliche Abweichung in der XML-CODE aus dem Schema werden hervorgehoben. Bewegen Sie den Mauszeiger über die markierten Elemente um zusätzliche Informationen anzuzeigen.

``` syntax
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      elementFormDefault="qualified" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      xmlns:mstns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="OEMInput">  
      <xs:complexType>  
         <xs:all>  
            <xs:element name="Product" type="xs:string" minOccurs="0" maxOccurs="1"/>  
            <xs:element name="Description" type="xs:string" minOccurs="0" maxOccurs="1" />  
            <xs:element name="SV" type="xs:string" minOccurs="0" maxOccurs="1"/>  
            <xs:element name="SOC" type="xs:string" minOccurs="1" maxOccurs="1"/>  
            <xs:element name="Device" type="xs:string" minOccurs="1" maxOccurs="1"/>  
  
            <xs:element name="ReleaseType" minOccurs="1" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="Test"/>  
                     <xs:enumeration value="Production"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
              
            <xs:element name="BuildType" minOccurs="1" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="fre"/>  
                     <xs:enumeration value="chk"/>  
                     <xs:enumeration value="%BUILDTYPE%"/> 
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="FormatDPP" minOccurs="0" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="true"/>  
                     <xs:enumeration value="false"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="ExcludePrereleaseFeatures" minOccurs="0" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="true"/>  
                     <xs:enumeration value="false"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="OEMDevicePlatform" type="xs:string" minOccurs="0" maxOccurs="1"/>  
              
            <xs:element name="SupportedLanguages" minOccurs="1" maxOccurs="1">  
               <xs:complexType>  
                  <xs:all>  
                     <xs:element name="UserInterface" minOccurs="1" maxOccurs="1">  
                        <xs:complexType>  
                        <xs:sequence>  
                           <xs:element name="Language" type="xs:string" 
                              minOccurs="1" maxOccurs="unbounded" />  
                        </xs:sequence>  
                     </xs:complexType>  
                     </xs:element>  
                     <xs:element name="Keyboard" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Language" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                     <xs:element name="Speech" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Language" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                  </xs:all>  
               </xs:complexType>  
            </xs:element>  

            <xs:element name="BootUILanguage" type="xs:string" minOccurs="1" maxOccurs="1"/>  
              
            <xs:element name="BootLocale" type="xs:string" minOccurs="1" maxOccurs="1"/>  
              
            <xs:element name="Resolutions" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="Resolution" type="xs:string" minOccurs="1" 
                        maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="Features" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="Microsoft" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Feature" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                     <xs:element name="OEM" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Feature" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="AdditionalFMs" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="AdditionalFM" type="xs:string" 
                        minOccurs="1" maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
            <!-This element is only for use with Windows 8 Phone device update images -->       
            <xs:element name="UserStoreMapData" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:attribute name="SourceDir" type="xs:string" />  
                  <xs:attribute name="UserStoreDir" type="xs:string" />  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="PackageFiles" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="PackageFile" type="xs:string" 
                        minOccurs="1" maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
         </xs:all>  
      </xs:complexType>  
   </xs:element>  
</xs:schema>
```

## <a name="related-topics"></a>Verwandte Themen


[Erstellen ein Bild mit ImgGen.cmd](building-a-phone-image-using-imggencmd.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20OEMInput%20file%20contents%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





