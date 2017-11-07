---
title: Optionale Features zum Erstellen von mobilen Bilder
description: "Sie können optionale Features Bilder hinzufügen, indem sie unter dem Features-Element in der OEMInput-XML-Datei eingeschlossen werden."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8147e170-f21f-4ed3-8130-4d498368ff92
ms.openlocfilehash: e5ba14b60503190ca2db0657f3f2c9c54829a0c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="optional-features-for-building-mobile-images"></a>Optionale Features zum Erstellen von mobilen Bilder


Sie können optionale Features Bilder hinzufügen, indem sie unter dem **Features** -Element in der OEMInput-XML-Datei eingeschlossen werden. Hinzufügen eines Features werden die Pakete, die das Feature zum Bild zugeordnet hinzufügen. Einige Features können nur bei bestimmte Bildtypen verwendet werden. Weitere Informationen zur Verwendung von optionalen Features finden Sie unter [Erstellen eines Bildes ImgGen.cmd mit](building-a-phone-image-using-imggencmd.md).

Updates getestet werden sollte, durch das Senden von OS fordert mithilfe des Clients aufnehmen und Überprüfen der erfolgreichen OS Updates zu aktualisieren.

## <a name="conditional-features"></a>Bedingte features


Ein Gerät für ein Feature in der folgenden Tabelle aufgelisteten Bedingungen aus Installation erfüllt, schlägt der Aktualisierungspfad für das Gerät fehl, es sei denn, das Feature installiert ist. Beispielsweise gibt es entfernt ein Update für Rich Kommunikationsplattform Suite-Unterstützung für Windows 10 Mobile, und Sie dieses Feature von einem Gerät, die der Nutzung andernfalls kann dann gesamte Update-Paket (und alle nachfolgenden Updates) werden nicht installiert. Zum Abrufen von Updates müssen Sie erneut, um ein Bild, das das Feature für Kunden umfasst übermitteln und lassen sie das Gerät erneut flash.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name des Features und -ID</th>
<th>Aktualisierungspfad</th>
<th>Bedingung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Rich-Suite Kommunikationsplattform-Unterstützung (RCS_FEATURE_PACK)</td>
<td>Windows-10 für Windows 8.1</td>
<td><p>Installieren, wenn PhoneManufacturer = NOKIA</p>
<p>Aktualisieren, sofern installiert</p></td>
</tr>
<tr class="even">
<td>In der Nähe Zahlen/blockieren und Filter (MS_COMMSENHANCEMENT * apps)</td>
<td>Windows-10 für Windows 8.1</td>
<td><p>MS_COMMSENHANCEMENTCHINA installieren, wenn HKEY_LOCAL_MACHINE\system\Platform\DeviceTargetingInfo\phoneromlanguage = 0804. Aktualisieren Sie, wenn es bereits installiert ist.</p>
<p>Installieren Sie MS_COMMSENHANCEMENTGLOBAL Wenn HKEY_LOCAL_MACHINE\system\Platform\DeviceTargetingInfo\phoneromlanguage &lt; &gt; 0804. Aktualisieren Sie, wenn es bereits installiert ist.</p></td>
</tr>
</tbody>
</table>

 

## <a name="retail-features-defined-by-microsoft"></a>Einzelhandel mit Microsoft definierten features


Die folgende Tabelle beschreibt die Microsoft-defined Features, die von OEMs im **Features** -Element in der Datei OEMInput für den Einzelhandel Geräte verwendet werden können.

Finden Sie in der Mobilfunkbetreiber für zusätzliche Verkaufsversion Features, die für bestimmte Mobilfunkbetreiber verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OPTIMIZED_BOOT</p></td>
<td><p>Ändert das Verhalten des Startvorgangs OS um einige Systemprozesse und Dienste zu starten, bevor alle Gerätetreiber gestartet werden. Aktivieren dieses Feature kann sinken, Startzeit kann, aber es auch Regressionen Boot-Verhalten in einigen Szenarien.</p></td>
</tr>
<tr class="even">
<td><p>STANDARD_FEATURE_1</p></td>
<td><p>Dieses Feature umfasst standard-Features, die in alle Bilder enthalten sein müssen.</p></td>
</tr>
<tr class="odd">
<td><p>NETLOG_RETAIL</p></td>
<td><p>Dieses Feature fügt Netzwerk Capture, bei der Behandlung von Netzwerkverbindungsproblemen Protokollierung. Dieses Feature wird von Feld Sanitäter Erfassung Diagnoseinformationen Netzwerk verwendet.</p></td>
</tr>
<tr class="even">
<td><p>NAVIGATIONBAR</p></td>
<td><p>Dieses Feature Fügt eine Phone-Einstellung, die Benutzern ermöglicht, konfigurieren Sie die Farbe der Schaltflächen Software.</p></td>
</tr>
<tr class="odd">
<td><p>FACEBOOK (ENGL.)</p></td>
<td><p>Dieses Feature umfasst Facebook im Bild.</p></td>
</tr>
<tr class="even">
<td><p>SKYPE</p></td>
<td><p>Dieses Feature umfasst die Skype Windows Phone Silverlight-Anwendung im Bild.</p></td>
</tr>
<tr class="odd">
<td><p>BINGAPPS</p></td>
<td><p>Dieses Feature fügt Bing News, Finanzen, Sportliga und Wetter hinzu.</p></td>
</tr>
<tr class="even">
<td><p>BINGFOOD</p></td>
<td><p>Dieses Feature fügt Bing Boot &amp; trinken.</p></td>
</tr>
<tr class="odd">
<td><p>BINGHEALTH</p></td>
<td><p>Dieses Feature fügt Bing Health &amp; Eignung.</p></td>
</tr>
<tr class="even">
<td><p>BINGTRAVEL</p></td>
<td><p>Dieses Feature fügt Bing Reisen.</p></td>
</tr>
<tr class="odd">
<td><p>WIFI_FEATURE_PACK</p></td>
<td><p>Dieses Feature entfernt alle Mobilfunk-bezogenen Funktionen vom Betriebssystem und dient nur für Geräte, die nicht mit einem Mobilfunknetz verbunden werden soll. Entfernt alle Mobilfunk weiterführende Kacheln, Symbole und Einstellungen aus der Benutzeroberfläche. Dieses Feature einschließlich reduziert Speicherverwendung und die Benutzeroberfläche verbessert, indem nicht angezeigt wird, funktioniert nicht Mobilfunk Einstellungen und Symbole.</p></td>
</tr>
<tr class="even">
<td><p>RELEASE_PRODUCTION</p></td>
<td><p>Veraltet, nicht mehr verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>COMMSENHANCEMENTGLOBAL</p></td>
<td><p>Die Funktion umfasst die Nachricht ein, und rufen Filtern Anwendung im Bild.</p></td>
</tr>
<tr class="even">
<td><p>COMMSENHANCEMENTCHINA</p></td>
<td><p>Das Feature umfasst Nachricht&amp;Anruffilter, Anruf Speicherort und Kategorie-Anwendung im Bild. Es wird nur für China verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>4GBFEATURESONDATA</p></td>
<td><p>Auf Geräten mit 4GB Speicher werden auf der Datenpartition bereitgestellten Pakete gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>8GBFEATURESONDATA</p></td>
<td><p>Bereitgestellten Pakete werden auf Geräten mit 8GB Speicherplatz auf der Datenpartition gespeichert.</p>
<div class="alert">
<strong>Hinweis</strong>  Es wird dringend empfohlen, dass Sie auch 8GBFEATURESONSYSTEM verwenden, wenn Sie dieses Feature angeben.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>8GBFEATURESONSYSTEM</p></td>
<td><p>Auf Geräten mit 8GB Speicherplatz werden auf der Partition OS bereitgestellten Pakete gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>16GBFEATURESONDATA</p></td>
<td><p>Auf Geräten mit 16GB Speicher werden die bereitgestellten Pakete auf der Datenpartition gespeichert.</p>
<div class="alert">
<strong>Hinweis</strong>  Es wird dringend empfohlen, dass Sie auch 16GBFEATURESONSYSTEM verwenden, wenn Sie angeben, dass dieses Feature.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>16GBFEATURESONSYSTEM</p></td>
<td><p>Bereitgestellten Pakete werden auf Geräten mit 16GB Speicherplatz auf der Partition OS gespeichert.</p></td>
</tr>
<tr class="even">
<td><p>SPATIALSOUND_FILTERDATA</p></td>
<td><p>Enthält die Datendateien und Registrierungsschlüssel, die erforderlich sind, um die räumliche Audio-Funktionalität auf einem mobilen Gerät zu aktivieren. Räumliche Audio wird verwendet, um Stellen Ton, so wie er von einer bestimmten Richtung stammt, und um die Audiodaten klingt, als es stellen natürlich innerhalb eines bestimmten Typs des Raums vorhanden.</p></td>
</tr>
<tr class="odd">
<td><p>TAIWAN_ENABLEMENT</p></td>
<td><p>Entfernen Sie Taiwan aus diesem Abbild.</p></td>
</tr>
<tr class="even">
<td><p>MYANMAR_ZAWGYI_ENABLEMENT</p></td>
<td><p>Aktivieren Sie dieses Bild zur Darstellung in Myanmar-Codierung Zawgyi verwendet. Sie sollten auch die Tastatur Zawgyi hinzufügen, wenn dieses Feature hinzufügen.</p></td>
</tr>
<tr class="odd">
<td><p>SOCProdTest_HSTI</p></td>
<td><p>Dieses Feature installiert den richtigen Treiber für die Sicherheit Wasserzeichen überprüft und ist für Windows 10 Mobile erforderlich. Wenn dieses Paket nicht installiert ist, wird das Wasserzeichen <strong>Nicht für den Einzelhandel</strong> angezeigt.</p>
<div class="alert">
<strong>Wichtig</strong>  Dieses Feature muss in das Betriebssystemabbild enthalten sein. Wenn dieses Feature nicht enthalten ist, kann das Gerät nicht gestartet.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>ATTWIFI</p></td>
<td><p>Dieses Feature installiert ein Drittanbieter-Plug-in, die mit einer AT ermöglicht&amp;T-SIM zur automatischen Verbindung AT&amp;T Hotspots.</p></td>
</tr>
<tr class="odd">
<td><p>DISABLE_ABNORMAL_RESET</p></td>
<td><p>Dieses Feature deaktiviert ungewöhnliche zurückgesetzt und nicht an Watson melden.</p></td>
</tr>
<tr class="even">
<td><p>Docking</p></td>
<td><p>Dieses Feature ermöglicht kontinuierliche für Windows 10 Mobile.</p></td>
</tr>
<tr class="odd">
<td><p>RESET_PROTECTION</p></td>
<td><p>Dieses Feature ermöglicht den Schutz zurücksetzen auf Einzelhandel-Abbild. Wenn das Gerät zum ersten Mal gestartet wird, werden die entsprechende sichere UEFI-Variable geschrieben.</p></td>
</tr>
<tr class="even">
<td><p>PERF_TRACING_TOOLS</p></td>
<td><p>Tools für die Leistungsanalyse, beispielsweise Tools für das Beenden und Zusammenführen von ETL-Tracing enthält.</p></td>
</tr>
<tr class="odd">
<td><p>ENABLE_BOOT_PERF_BASIC_TRACING</p></td>
<td><p>Starten Sie ermöglicht Leistung Ablaufverfolgungsereignisse generiert werden soll.</p></td>
</tr>
<tr class="even">
<td><p>ENABLE_BOOT_PERF_CPU_PROFILING_TRACING</p></td>
<td><p>CPU-Ereignissen ein Profil erstellen können. Zusätzlich zu den Boot Leistung Tracing Ereignisse, die mit ENABLE_BOOT_PERF_BASIC_TRACING aktiviert sind.</p></td>
</tr>
<tr class="odd">
<td><p>MESSAGINGGLOBAL</p></td>
<td><p>Dieses Feature installiert das Messaging-Paket, das Skype-Integration enthält. Es muss für alle Geräte mit Ausnahme der übermittelt NAL Zertifizierung in China verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>MESSAGINGLITE</p></td>
<td><p>Dieses Feature installiert das Messaging-Paket ohne Skype-Integration. Sie müssen für ein beliebiges Telefon oder ein anderes Gerät gesendet wird, die für die NAL-Zertifizierung in China (ausgenommen Hongkong (SAR) und Macau) verwendet werden.</p></td>
</tr>
<tr class="odd">
<td><p>SPATIALSOUND_FILTERDATA</p></td>
<td><p>Dieses Feature installiert <a href="https://dev.windows.com/holographic/spatial_sound">räumliche sound</a>.</p></td>
</tr>
</tbody>
</table>

 

**Retail Boot Sequence-Einstellungen**

Das nächsten beiden Einstellungen-Steuerelement das Telefon starten. Nur eine kann ausgewählt werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>BOOTSEQUENCE_RETAIL</p></td>
<td><p>Dieses Feature ermöglicht die Startreihenfolge standard Verkaufsversion.</p></td>
</tr>
</tbody>
</table>

 

**Microsoft interne Retail features**

Die folgenden Komponenten sind für die Microsoft nur interne Verwendung reserviert, jedoch werden hier der Vollständigkeit dokumentiert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>DAVON</p></td>
<td><p>Dieses Feature fügt Komponenten, die ausschließlich für Self-hosting-Szenarios in Microsoft verwendet.</p></td>
</tr>
<tr class="even">
<td><p>FieldMedicCustomProfiles</p></td>
<td><p>Dieses Feature fügt zusätzlichen Tracing Profile von Feld Sanitäter verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>RESET_PROTECTION_INTERNAL</p></td>
<td><p>Dieses Feature ermöglicht den Schutz zurücksetzen auf einem Test-Abbild. Wenn das Gerät zum ersten Mal gestartet wird, werden die entsprechende sichere UEFI-Variable geschrieben.</p></td>
</tr>
</tbody>
</table>

 

**Retail Demo Experience-features**

Den Einzelhandel Demo auftreten Überseeischen offline Retail Demo Inhalt enthält, der für eine hervorragende Retail Demo Erfahrung von entscheidender Bedeutung ist. Dieser Inhalt offline enthält Windows- und der Office-Inhalte, die zusammen mit OEM oder Händler Retail Demo Inhalt angezeigt wird. Hinzufügen von diesem Retail Demo Erfahrung Überseeischen ist erforderlich und für alle OEMs beteiligt sind aktivieren eine Retail Demo Erfahrung auf ihren Windows-10-Geräten erforderlich.

-   MS\_RETAILDEMOCONTENT\_AR-SA
-   MS\_RETAILDEMOCONTENT\_BG-BG
-   MS\_RETAILDEMOCONTENT\_CS-CZ
-   MS\_RETAILDEMOCONTENT\_DA-DK
-   MS\_RETAILDEMOCONTENT\_DE-DE
-   MS\_RETAILDEMOCONTENT\_EL g
-   MS\_RETAILDEMOCONTENT\_EN-GB
-   MS\_RETAILDEMOCONTENT\_EN-US
-   MS\_RETAILDEMOCONTENT\_ES-ES
-   MS\_RETAILDEMOCONTENT\_ES-MX
-   MS\_RETAILDEMOCONTENT\_ET-EE
-   MS\_RETAILDEMOCONTENT\_FI-FI
-   MS\_RETAILDEMOCONTENT\_FR-CA
-   MS\_RETAILDEMOCONTENT\_FR-FR
-   MS\_RETAILDEMOCONTENT\_IE-IL
-   MS\_RETAILDEMOCONTENT\_HR-HR
-   MS\_RETAILDEMOCONTENT\_HU-HU
-   MS\_RETAILDEMOCONTENT\_ID-Nummer
-   MS\_RETAILDEMOCONTENT\_IT-IT
-   MS\_RETAILDEMOCONTENT\_JA-JP
-   MS\_RETAILDEMOCONTENT\_KO-KR
-   MS\_RETAILDEMOCONTENT\_LT-LT
-   MS\_RETAILDEMOCONTENT\_LV LV
-   MS\_RETAILDEMOCONTENT\_NB-NO
-   MS\_RETAILDEMOCONTENT\_NEUTRAL
-   MS\_RETAILDEMOCONTENT\_NL-NL
-   MS\_RETAILDEMOCONTENT\_PL-PL
-   MS\_RETAILDEMOCONTENT\_PT-BR
-   MS\_RETAILDEMOCONTENT\_PT-PT
-   MS\_RETAILDEMOCONTENT\_RO RO
-   MS\_RETAILDEMOCONTENT\_RU-RU
-   MS\_RETAILDEMOCONTENT\_SK SK
-   MS\_RETAILDEMOCONTENT\_SL-SI
-   MS\_RETAILDEMOCONTENT\_SR-LATN-RS
-   MS\_RETAILDEMOCONTENT\_SV-SE (engl.)
-   MS\_RETAILDEMOCONTENT\_ten-ten
-   MS\_RETAILDEMOCONTENT\_TR-TR
-   MS\_RETAILDEMOCONTENT\_Großbritannien-UA
-   MS\_RETAILDEMOCONTENT\_VI-VN
-   MS\_RETAILDEMOCONTENT\_ZH-CN
-   MS\_RETAILDEMOCONTENT\_ZH-HK
-   MS\_RETAILDEMOCONTENT\_ZH-TW

## <a name="test-features-defined-by-microsoft"></a>Testen Sie die Features von Microsoft definierten


In der folgenden Tabelle wird beschrieben, die Microsoft-defined Testfeatures, die im **Features** -Element in der Datei OEMInput von OEMs verwendet werden können. Diese Features sind in MSOptionalFeatures.xml, das in der MobileOS unter WPDKCONTENTROOT % enthalten ist definiert\\FMFiles.

### <a name="boot-option-features"></a>Starten Sie die Option features

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BOOTSEQUENCE_TEST</p></td>
<td><p>Dieses Feature umfasst die BCD Sequenz Startkonfiguration für das in der vollständigen Betriebssystem in einem Test-Abbild starten. Dieses Feature umfasst auch eine vor dem Start Absturz Dump-Anwendung und ein Absturz vor dem Start Dump-Eintrag.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die folgenden Features schließen sich gegenseitig aus; nur von einer in einer Datei OEMInput verwiesen werden kann: BOOTSEQUENCE_TEST, MMOSLOADER_TEST.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>MMOSLOADER_TEST</p></td>
<td><p>Dieses Feature umfasst die BCD Sequenz Startkonfiguration zur Unterstützung der MMOS in einem Testbild starten. Dieses Feature umfasst auch eine vor dem Start Absturz Dump Anwendung und einen vor dem Start Absturz Dump-Eintrag. Weitere Informationen zu MMOS finden Sie unter <a href="mmos-image-definition.md">MMOS image-Definition</a>.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Die folgenden Features schließen sich gegenseitig aus; nur von einer in einer Datei OEMInput verwiesen werden kann: BOOTSEQUENCE_TEST, MMOSLOADER_TEST.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>MOBILECOREBOOTSH</p></td>
<td><p>Können den Dienst Bootsh (Bootshscv), damit startup.bsc Features wie Telnet und ftp, verwendet werden können.</p></td>
</tr>
<tr class="even">
<td><p>MOBILECORE_TEST</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>PRODUKTION</p></td>
<td><p>Enthält die Kern-Dateien, die zur Unterstützung von Basisfunktionalität OS für Produktion Builds in das Hauptfenster Betriebssystem, UEFI und das Update OS verwendet werden. Dieses Feature ist für PRODUKTION Bildtypen verwendet.</p></td>
</tr>
<tr class="even">
<td><p>PRODUCTION_CORE</p></td>
<td><p>Dieses Feature fügt Boot Produktions- und Hauptfenster OS-Binärdateien auf das Bild. PRODUCTION_CORE enthält automatisch die folgenden Features:</p>
<ul>
<li><p>CODEINTEGRITY_PROD</p></li>
</ul>
<p>Da diese Features bereits enthalten sind, sie sollten nicht manuell aufgenommen werden in PRODUCTION_CORE erstellt.</p></td>
</tr>
<tr class="odd">
<td><p>DISABLE_FFU_PLAT_ID_CHECK</p></td>
<td><p>Deaktiviert die Gerät Plattform Überprüfung in die blinkende Microsoft-Anwendung an. Weitere Informationen zum Einchecken blinken Plattform finden Sie unter <a href="use-the-flashing-tools-provided-by-microsoft.md">Verwenden der blinkende Tools von Microsoft bereitgestellt</a>.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Die Gerät Plattform Validierung blinken muss im Einzelhandel Bilder nicht deaktiviert werden.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>RESET_PROTECTION_INTERNAL</p></td>
<td><p>Dieses Feature ermöglicht den Schutz zurücksetzen auf dem Gerät. Wenn das Gerät zum ersten Mal gestartet wird, werden die entsprechende sichere UEFI-Variable geschrieben.</p></td>
</tr>
</tbody>
</table>

 

### <a name="boot-option-feature-constraints"></a>Boot Option Feature Integritätsregeln

Sie können angeben, dass das Feature Einschränkungen vermieden unlogische oder unzulässiges Konfigurationen erstellen.

Einige Einstellungen schließen sich gegenseitig aus, und es sollte nur eine Einstellung zu einem Zeitpunkt angegeben werden. Angenommen, die Features, VERSION\_PRODUKTIONS- und RELEASE\_TEST. Diese Features schließen sich gegenseitig aus. Dies bedeutet, dass bei VERSION\_TEST festgelegt ist, VERSION\_PRODUKTION muss nicht festgelegt werden. Weitere Informationen zu Einschränkungen wie in XML angegebenen anzuzeigen, [Feature Gruppen und Einschränkungen](feature-groupings-and-constraints.md).

Wenn &lt;ReleaseType&gt;Produktion&lt;/ReleaseType&gt; wird festgelegt, in der Datei OEMInput, diese Karten Version\_PRODUKTION. Beim &lt;ReleaseType&gt;Test&lt;/ReleaseType&gt; wird festgelegt, in der Datei OEMInput, diese Karten auf VERSION\_TEST. Weitere Informationen zu den Versionstyp finden Sie unter [OEMInput Dateiinhalten](oeminput-file-contents.md).

Die Version Einschränkungen für VERSION\_PRODUKTION kann wie folgt zusammengefasst werden.

-   Entweder VERSION\_PRODUKTION oder CODEINTEGRITY\_"Bemerkungen" ausgewählt werden kann. Dies ist, da die Produktion Integrität des Codes wird automatisch aktiviert, wenn RELEASE\_PRODUKTION ausgewählt ist und deshalb nicht manuell aktiviert werden.

Diese Funktion Einschränkungen können verwendet werden, um falschen Build Option Konfigurationen zu verhindern. Diese Feature Einschränkungen angeben, die PRODUKTION\_CORE schließen sich gegenseitig aus mit VERSION ist\_PRODUKTIONS- und TEST, ist aber keine mit STATUS, die PRODUKTION oder DAVON gegenseitig aus.

Diese Tabelle enthält eine Zusammenfassung der Buildoptionen und gibt an, ob die Option eine andere Option exklusiv ist.

<table style="width:100%;">
<colgroup>
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>RELEASE_PRODUCTION</th>
<th>TEST</th>
<th>INTEGRITÄT</th>
<th>PRODUKTION</th>
<th>DAVON</th>
<th>PRODUCTION_CORE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RELEASE_PRODUCTION</p></td>
<td><p>NV</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>TEST</p></td>
<td><p>Ja</p></td>
<td><p>NV</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>INTEGRITÄT</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>NV</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>PRODUKTION</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>NV</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>DAVON</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>NV</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>PRODUCTION_CORE</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>NV</p></td>
</tr>
</tbody>
</table>

 

### <a name="other-boot-related-features"></a>Andere verwandte Features starten

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STARTUPOVERRIDES</p></td>
<td><p>Dieses Feature wird der FTP-Dienst (ftpd.exe) und Telnet-Dienst (telnetd.exe) beim Start automatisch gestartet.</p></td>
</tr>
<tr class="even">
<td><p>LABIMAGE</p></td>
<td><p>Diese Funktion bewirkt, dass das Gerät den FFU Download-Modus automatisch eingeben, wenn das Gerät gestartet wird. Weitere Informationen finden Sie unter <a href="use-the-flashing-tools-provided-by-microsoft.md">Verwenden der blinkende Tools von Microsoft bereitgestellt</a>.</p></td>
</tr>
<tr class="odd">
<td><p>BOOTKEYACTIONS_RETAIL</p></td>
<td><p>Dieses Feature ermöglicht eine Reihe von Aktionen für die Verwendung im Einzelhandel Geräte.</p></td>
</tr>
<tr class="even">
<td><p>SKIPOOBE</p></td>
<td><p>Dieses Feature wird der anfänglichen Setupassistent Prozess deaktiviert. Dieses Feature ist in Test, Integrität und Produktion Bildtypen unterstützt. Dieses Feature muss nicht im Einzelhandel Bilder verwendet werden.</p></td>
</tr>
</tbody>
</table>

 

### <a name="security-related-features"></a>Sicherheitsbezogene features

Es gibt zwei auf einem Windows 10 Mobile Gerät Retail und Test Code Modi signieren. Mit Einzelhandel muss der gesamte Code Produktion werden sollen, führen Sie auf dem Gerät angemeldet sein. Test anmeldet, muss der gesamte Code mit Testzertifikaten signiert werden. Weitere Informationen zum Signieren von Code finden Sie unter [Signieren von Code](https://msdn.microsoft.com/library/windows/hardware/dn756634).

Der beiden Code signierenden Modi im Buildsystem automatisch verwaltet werden. Die vorherigen Einstellungen für DISABLETESTSIGNING und ENABLETESTSIGNING Feature werden nicht mehr verwendet. Stattdessen wird Test Signieren von Code in den folgenden Arten von Build automatisch aktiviert:

-   TEST

-   INTEGRITÄT

-   PRODUKTION

-   DAVON

Test Signieren von Code nicht aktiviert werden, in der VERSION\_PRODUKTION build-Typ, der für den Einzelhandel Geräte verwendet wird

In der folgenden Tabelle werden die Sicherheit zusammengefasst verwandte Features.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CODEINTEGRITY_PROD</p></td>
<td><p>Dieses Feature umfasst Code Integrität Binärdateien, die für die Überprüfung der Signatur auf Produktion Bilder verwendet werden. Integrität des Codes überprüft die Integrität der Binärdateien vom Betriebssystem in den Arbeitsspeicher geladen werden. Dieses Feature ist automatisch enthalten, wenn PRODUCTION_CORE ausgewählt ist. Aus diesem Grund sollten CODEINTEGRITY_PROD nicht manuell hinzugefügt werden, wenn PRODUCTION_CORE ausgewählt ist.</p></td>
</tr>
<tr class="even">
<td><p>CODEINTEGRITY_TEST</p></td>
<td><p>Dieses Feature umfasst Code Integrität Binärdateien, die für die Überprüfung der Signatur auf Test Bilder verwendet werden. Integrität des Codes überprüft die Integrität der Binärdateien, wie sie vom Betriebssystem in den Arbeitsspeicher geladen werden.</p></td>
</tr>
<tr class="odd">
<td><p>GWPCERTTESTPROV</p></td>
<td><p>Dieses Feature stellt diese bereit, eine Reihe von Test im Bild Genuine Windows Phone-Zertifikate (GWPC) Zertifikate.</p></td>
</tr>
</tbody>
</table>

 

### <a name="test-related-features"></a>Testen Sie verwandte features

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TEST</p></td>
<td><p>Dieses Feature hinzugefügt, dass viele Treiber, Anwendungen und anderen Komponenten verwendet werden, für das Testen des Betriebssystems in unterschiedlichen Bedingungen testen.</p></td>
</tr>
<tr class="even">
<td><p>TESTINFRASTRUCTURE</p></td>
<td><p>Dieses Feature fügt die folgenden Komponenten auf das Bild:</p>
<ul>
<li><p>MinTE.exe und anderer Komponenten, die eine minimale testumgebung Umgebung für Tests Authoring testen und Ausführung Framework (TAEF) unterstützen.</p></li>
<li><p>Das Verifier.cmd-Skript zum Konfigurieren der Überprüfung der Gerätetreiber verwendet wird.</p></li>
<li><p>Tux.exe und anderen Komponenten im Zusammenhang mit der Tux Testprogramm für systemeigenen Code.</p></li>
<li><p>TuxNet.exe und anderen Komponenten im Zusammenhang mit der TuxNet Testprogramm für verwalteten Code.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>INTEGRITÄT</p></td>
<td><p>Dieses Feature fügt Komponenten zum Ausführen von Tests, die im Zusammenhang mit der Leistung.</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFINFRA</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>DRIVERS_WDTFPOWER</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFPLGINS</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>DRIVERS_WDTFDRVCOV</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFIOSPY</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
</tbody>
</table>

 

### <a name="debug-related-features"></a>Debuggen Sie verwandte features

Verwenden Sie die folgenden Einstellungen, um das Transportprotokoll angeben, für das debugging verwendet wird. Das vorherige DEBUGGERON Feature ist veraltet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>Debuggen transporteinstellungen</strong></p></td>
</tr>
<tr class="even">
<td><p>KDNETUSB_ON</p></td>
<td><p>Enthält alle Kernel-Debugger Transporten und KDNET über USB ermöglicht.</p>
<p>Die Debug-Transport-Standardeinstellungen für dieses Feature sind eine IP-Adresse des &quot;1.2.3.4&quot;, eine Portadresse des &quot;50000&quot;, und dem Schlüssel Debugger &quot;4.3.2.1&quot;. Um die Standard-IP-Adresse 1.2.3.4 zu verwenden, führen Sie VirtEth.exe mit dem <em>/autodebug</em> -Flag. Verwenden Sie zum Herstellen einer Verbindung ein Kernel-Debugger auf dem Telefon den folgenden Befehl ein.</p>
<p>WinDbg -k Net: Port = 50000 Schlüssel = 4.3.2.1</p></td>
</tr>
<tr class="odd">
<td><p>KDUSB_ON</p></td>
<td><p>Enthält alle Kernel Debugger Transporten und KDUSB ermöglicht.</p>
<p></p>
<p>Der Standardwert Debug Transport Zielname für dieses Feature ist WOATARGET. Verwenden Sie zum Herstellen einer Verbindung ein Kernel-Debugger auf dem Telefon den folgenden Befehl ein.</p>
<p>WinDbg -k Usb:targetname = WOATARGET</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Schließen Sie KDUSB_ON oder KDNETUSB_ON nicht MTP oder IP über USB im Bild aktivieren möchten. Wenn der Kernel-Debugger im Bild aktiviert ist und die Debuggen Transporten verwendet werden, um auf das Gerät eine Verbindung herstellen, Kernel-Debugger ist zur exklusiven Verwendung des USB-Ports und verhindert MTP und IP-über USB arbeiten.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>KDSERIAL_ON</p></td>
<td><p>Enthält alle Kernel-Debugger Transporten und ermöglicht KDSERIAL mit den folgenden Einstellungen: 115.200 Baud, 8-Bit, keine Parität.</p></td>
</tr>
<tr class="odd">
<td><p>KD</p></td>
<td><p>Enthält alle Kernel Debugger Transporten im Bild Kernel-Debugger wird nicht aktiviert.</p></td>
</tr>
<tr class="even">
<td><p>KD_TEST</p></td>
<td><p>Enthält alle Kernel Debugger Transporten im Bild Kernel-Debugger wird nicht aktiviert.</p></td>
</tr>
<tr class="odd">
<td><p>KDNETUSB_TEST_ON</p></td>
<td><p>Enthält alle Kernel-Debugger Transporten und KDNET über USB in Test Bilder ermöglicht. Diese Option muss nur mit Test-Bilder verwendet werden.</p></td>
</tr>
</tbody>
</table>

 

**Andere Debugeinstellungen**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Festlegen von Funktionen - die folgenden drei Features Speicherabzugsgröße muss nur mit der Test- und Integrität Bildtypen verwendet werden. Diese Funktionen müssen nicht mit Retail Bilder verwendet werden. Nur eine Speicherabzugsgröße Einstellung kann zu einem Zeitpunkt ausgewählt werden.</p></td>
</tr>
<tr class="even">
<td><p>DUMPSIZE512MB</p></td>
<td><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 592 MB. Dies ist für ein Telefon mit 512 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="odd">
<td><p>DUMPSIZE1G</p></td>
<td><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 1104 MB. Dies ist für ein Telefon mit 1024 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="even">
<td><p>DUMPSIZE2G</p></td>
<td><p>Gibt eine vorab zugewiesene Absturz Dump Dateigröße 2128 MB. Dies ist für ein Telefon mit 2048 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="odd">
<td><p>DUMPSIZE4G</p></td>
<td><p>Gibt eine vorab zugewiesene Absturz Dump Größe von 4 GB. Dies ist für ein Telefon mit 4096 MB Arbeitsspeicher vorgesehen.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Dump Datenspeicherort - die nächsten beiden Settings-Steuerelement, wenn Absturz Sicherungsdaten auf eMMC gespeichert ist oder Absturz Sicherungsdaten auf einer SD-Karte gespeichert ist. Nur eine dieser Einstellungen kann zu einem Zeitpunkt ausgewählt werden. Diese beiden Funktionen müssen nur mit der Test, Integrität und davon Bildtypen verwendet werden. Diese Funktionen müssen nicht mit Retail Bilder verwendet werden.</p></td>
</tr>
<tr class="odd">
<td><p>DEDICATEDDUMPONEMMC</p></td>
<td><p>Gibt an, dass der Speicherort DedicatedDumpFile als c:\crashdump\dedicateddump.sys.</p></td>
</tr>
<tr class="even">
<td><p>DEDICATEDDUMPONSD</p></td>
<td><p>DEDICATEDDUMPONSD – gibt an, dass der Speicherort DedicatedDumpFile als d:\dedicateddump.sys</p>
<p>Wenn DEDICATEDDUMPONSD verwendet wird, wird Absturzabbild deaktiviert werden, wenn der Benutzer die SD-Karte entfernt oder wenn die Karte nicht vorhanden ist, wenn das Gerät gestartet ist. Um Absturzabbild wieder zu aktivieren:</p>
<ol>
<li><p>Legen Sie diesen Registrierungsschlüssel <code>HKLM\System\CurrentControlSet\Control\CrashControl\CrashDumpEnabled</code> auf den Wert der <code>HKLM\System\CurrentControlSet\Control\CrashControl\ExpectedCrashDumpEnabled</code></p></li>
<li><p>Starten Sie Telefon neu.</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Testen Sie Datenträger im Leerlauf Verhalten - die nächsten beiden Einstellungen bestimmen, wenn Speichergeräten (interne und SD-Karte) können in den Energiesparmodus eingeben, nachdem sie den Leerlauf. Sie müssen nicht mit Retail Bilder verwendet werden.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>TEST_ENABLE_DISK_IDLE</p></td>
<td><p>Dieses Feature ermöglicht die Speichergeräten (interne und SD-Karte) in den Energiesparmodus wechseln, kurz nachdem sie Leerlauf. Diese Einstellung kann die Auflistung von Crashdumps auf den Geräten MSM8960 Prozessor verhindern. Wenn Crashdumps von einem Gerät MSM8960 erfasst werden müssen, verwenden Sie stattdessen die TEST_DISABLE_DISK_IDLE-Funktion.</p></td>
</tr>
<tr class="odd">
<td><p>TEST_DISABLE_DISK_IDLE</p></td>
<td><p>Dieses Feature wird verhindert, dass die Speichergeräten (interne und SD-Karte) aus den Energiesparmodus aufruft, nachdem sie den Leerlauf. Diese Einstellung sollte verwendet werden, wenn Crashdumps von Geräten MSM8960 gesammelt werden müssen.</p></td>
</tr>
<tr class="even">
<td><p>DRVRF_SIPLAT</p></td>
<td><p>Treiber Verifier Parameter festgelegt für OEMs und SoC Treiber. Dieses Feature wird die VerifyDriverLevel mit einem Wert von 002209BB und VerifierOptions 00000009. Windows-Treiber von Microsoft bereitgestellten werden mit dem Schlüssel VerifyDrivers ausgeschlossen. Den folgende Befehl Debuggen können zum Auflisten der Treiber, die überprüft werden in Ihrer Umgebung.</p>
<pre class="syntax" space="preserve"><code>!verifier 1    </code></pre></td>
</tr>
<tr class="odd">
<td><p>DBGCHKDISABLE</p></td>
<td><p>Dieses Feature deaktiviert Debugger Verbindung überprüfen, und der Verbindungsstatus Debugger wird ignoriert.</p>
<p>Die Auswirkung auf das Debuggerverhalten unterscheidet sich je nach den SoC, die verwendet wird.</p>
<ul>
<li><p>Enthalten Sie für QC8x26 und QC8974-Geräte DBGCHKDISABLE, um sicherzustellen, dass offline speichert generiert werden, auch wenn das Gerät an einen Debugger verbunden ist. Andernfalls wird ein Dump Offline (Bug Check Code 0x14C Dump) nicht erstellt werden, aber ein unformatierte Dump weiterhin erstellt werden.</p></li>
<li><p>Umfassen Sie für 8960 Geräte DBGCHKDISABLE, um sicherzustellen, dass offline speichert generiert werden, auch wenn das Gerät an einen Debugger verbunden ist. Andernfalls wird ein Dump Offline (d. h. Bug Check Code 0x14C Dump) nicht erstellt werden.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MSVCRT_DEBUG</p></td>
<td><p>Dieses Feature bietet Unterstützung für explizite Verknüpfung Debug c-Laufzeitbibliothek Bibliotheken einschließlich msvcp120d.dll und msvcr120d.dll im Bild. Weitere Informationen finden Sie unter in diesem Thema auf MSDN: <a href="http://msdn.microsoft.com/library/abx4dbyh.aspx">CRT-Bibliothek Features</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MWDBGSRV</p></td>
<td><p>Dieses Feature fügt die Unterstützung für den Benutzer Modus Debug-Server hinzu.</p></td>
</tr>
<tr class="even">
<td><p>NOLIVEDUMPS</p></td>
<td><p>Fehlerberichte nicht schwerwiegenden Kernel deaktiviert.  Diese Berichte enthalten Debuginformationen für Entwickler von Betriebssystem und Treiber.</p></td>
</tr>
<tr class="odd">
<td><p>TELEMETRYONSDCARD</p></td>
<td><p>Dieses Feature ermöglicht die temporäre Speicherung von Debuggen, Protokolle und Dateien auf die SD-Karte.  Dieses Feature ist nur in der entsprechenden Test/selbst-Server-von Bildern und nur auf Geräten mit weniger als 8 GB freiem Speicherplatz für primären Speicher.</p></td>
</tr>
</tbody>
</table>

 

### <a name="non-production-features"></a>Nicht-Produktion features

Es folgen einige Features, die für die Entwicklung und Unterstützung verwendet werden können.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>POWERTRACINGTOOL</p></td>
<td><p>Dieses Feature fügt PowerTracingTool.exe, die zum Sammeln von Power-bezogene ETW-Protokolle, die auf das Bild verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>TASKSCHEDULERTOOL</p></td>
<td><p>Dieses Feature fügt TaskSchTestUtil.exe, dient zum Planen von bezogenen Vorgänge auf das Bild task ausführen können.</p></td>
</tr>
<tr class="odd">
<td><p>DISABLEPREBOOTCRASHDUMP</p></td>
<td><p>Dieses Feature hinzugefügt, dass eine Einstellung in der Registrierung, die offline Absturz deaktiviert bildet.</p></td>
</tr>
<tr class="even">
<td><p>ALWAYSKEEPMEMORYDUMP</p></td>
<td><p>Dieses Feature Fügt eine registrierungseinstellung, die weist das Gerät Kernel Dumpdateien gespeichert werden.</p></td>
</tr>
<tr class="odd">
<td><p>AUTOREBOOT</p></td>
<td><p>Dieses Feature Fügt eine Einstellung in der Registrierung, die dem Neustart des Geräts, unmittelbar nachdem ein Absturzabbild abgeschlossen ist.</p></td>
</tr>
<tr class="even">
<td><p>DISABLEDEBUGCHECKSCREEN</p></td>
<td><p>Dieses Feature Fügt einen Registrierungseintrag, der den Fehler Kontrollkästchen Bildschirm unterdrückt.</p></td>
</tr>
</tbody>
</table>

 

### <a name="other-features"></a>Andere features

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>FAKEVIBRA</p></td>
<td><p>Dieses Feature Fügt einen Test Hardware Benachrichtigung Treiber zum Steuern des Mechanismus Vibration Feedback.</p></td>
</tr>
<tr class="even">
<td><p>IMGFAKELED</p></td>
<td><p>Dieses Feature Fügt einen Test Hardware Benachrichtigung Treiber zum Steuern der LED auf das Bild.</p></td>
</tr>
<tr class="odd">
<td><p>LOCATIONFRAMEWORKAPP</p></td>
<td><p>Dieses Feature fügt LFApp, einer Test- und Debuggingtools Anwendung für den Speicherort Framework.</p></td>
</tr>
<tr class="even">
<td><p>PSEUDOLOCALES</p></td>
<td><p>Dieses Feature ermöglicht die Verwendung von Pseudogebietsschemata für das Testen der Lokalisierung. Weitere Informationen finden Sie unter <a href="http://msdn.microsoft.com/library/windows/desktop/dd374118.aspx">Using Pseudonamens-Gebietsschemas für das Testen der Lokalisierung</a> auf MSDN.</p></td>
</tr>
<tr class="odd">
<td><p>GRAPHICSSOFTWAREDRIVERS</p></td>
<td><p>Dieses Feature fügt BasicDisplay und WARP Graphics-Treiber. Dieses Feature wird normalerweise vom Anbieter SoC im frühe Gerät bringen-Up verwendet.</p></td>
</tr>
</tbody>
</table>

 

## <a name="microsoft-internal-features"></a>Interne Microsoft-features


Die folgenden Komponenten sind für die Microsoft nur interne Verwendung reserviert, jedoch werden hier der Vollständigkeit dokumentiert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DAVON</p></td>
<td><p>Dieses Feature fügt Komponenten, die ausschließlich für Self-hosting-Szenarios in Microsoft verwendet.</p></td>
</tr>
<tr class="even">
<td><p>IMGUPD_POWERTOYS</p></td>
<td><p>Dieses Feature umfasst mehrere Dienstprogramme bereit, die im Zusammenhang mit der Pakete auf Geräten aktualisieren.</p></td>
</tr>
<tr class="odd">
<td><p>INSTRUMENT_FOR_COVERAGE</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="even">
<td><p>IMGFAKEMODEM</p></td>
<td><p>Informationen zu diesem Feature wird in einer zukünftigen Version dieser Dokumentation bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>USE_WMC</p></td>
<td><p>Dieses Feature dient zum Testen von Microsoft.</p></td>
</tr>
<tr class="even">
<td><p>CORTANADBG_TEST_PROTECTED</p></td>
<td><p>Dieses Feature ist für die Verwendung durch Microsoft vorgesehen.</p></td>
</tr>
<tr class="odd">
<td><p>BEGRENZT</p></td>
<td><p>Dieses Feature ist für die Verwendung durch Microsoft vorgesehen.</p></td>
</tr>
<tr class="even">
<td><p>TEST_PROTECTED</p></td>
<td><p>Dieses Feature ist für die Verwendung durch Microsoft vorgesehen.</p></td>
</tr>
<tr class="odd">
<td><p>SELFHOST_PROTECTED</p></td>
<td><p>Dieses Feature ist für die Verwendung durch Microsoft vorgesehen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und blinkende](building-and-flashing-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Optional%20features%20for%20building%20mobile%20images%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





