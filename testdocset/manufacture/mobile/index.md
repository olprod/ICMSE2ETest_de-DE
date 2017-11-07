---
author: kpacquer
Description: "Nachdem Sie ein abgeschlossenes die Schritten in den anderen Handbüchern haben So bereiten Sie das Gerät vor behandelt, wechselt der Fokus auf das Gerät für die Konfiguration des endgültigen vorbereiten."
ms.assetid: f781b171-d37c-4b03-8e8b-da6d2e5d35b4
MSHAttr: PreferredLib:/library/windows/hardware
title: Mobile Fertigung
ms.openlocfilehash: f286154bf25e6351bfbd6aa680e5d391b9361221
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-manufacturing"></a>Mobile Fertigung


Nachdem Sie ein abgeschlossenes die Schritten in den anderen Handbüchern haben So bereiten Sie das Gerät vor behandelt, wechselt der Fokus auf das Gerät für die Konfiguration des endgültigen vorbereiten.

Während dieses Vorgangs legen Sie die Werte für die endgültige Konfiguration, Debug-Protokollierung entfernen und das Betriebssystem für Lieferung zu optimieren. Im nächsten Schritt legen Sie fest, wie die Hardware in der Fertigung Zeile des Betriebssystems übertragen werden sollen.

## <a name="span-idmanufacturingacronymsspanspan-idmanufacturingacronymsspanspan-idmanufacturingacronymsspanmanufacturing-acronyms"></a><span id="Manufacturing_acronyms"></span><span id="manufacturing_acronyms"></span><span id="MANUFACTURING_ACRONYMS"></span>Fertigung Akronyme


Hier sind einige häufige Akronyme, die stehen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><strong>DATUM</strong></p></td>
<td align="left"><p>Automatisierte Test equipment</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>BER</strong></p></td>
<td align="left"><p>Fehler Bitrate</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>BIST</strong></p></td>
<td align="left"><p>integrierte Selbsttest</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>MET</strong></p></td>
<td align="left"><p>Kosten des Tests</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>CIT testen</strong></p></td>
<td align="left"><p>Computer interaktive testen – Semi-Automatisches des Geräts testen. Während dieser Phase ist das Gerät mit einem PC oder einer Arbeitsstation verbunden.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>DIB</strong></p></td>
<td align="left"><p>Device Interface-Karte</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>DFT</strong></p></td>
<td align="left"><p>ist ausgelegt für test</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>DUT</strong></p></td>
<td align="left"><p>Gerät unter test</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ESD</strong></p></td>
<td align="left"><p>Elektrostatische Beendigung</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>EVM</strong></p></td>
<td align="left"><p>Fehler Vektor magnitude</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ANLAGEN</strong></p></td>
<td align="left"><p>endgültige assembly</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>FQC</strong></p></td>
<td align="left"><p>endgültige Qualität Kontrollkästchen</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>NIST</strong></p></td>
<td align="left"><p>National Institute of Standards and Technology</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>OOBT</strong></p></td>
<td align="left"><p>Out-of-Box-test</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>PIB</strong></p></td>
<td align="left"><p>Prüfpunkt Interface-Karte</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>RTC</strong></p></td>
<td align="left"><p>in Echtzeit Uhr – auf Pinnwand Hardware-Uhr verwendet, um die aktuelle Uhrzeit nachzuverfolgen</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SCM</strong></p></td>
<td align="left"><p>die vom Hersteller für Fremdarbeit</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SOC</strong></p></td>
<td align="left"><p>System auf einem chip</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>UPH</strong></p></td>
<td align="left"><p>Einheiten pro Stunde</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>UUT</strong></p></td>
<td align="left"><p>Klicken Sie unter Test Unit</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgeneralmanufacturingguidancespanspan-idgeneralmanufacturingguidancespanspan-idgeneralmanufacturingguidancespangeneral-manufacturing-guidance"></a><span id="General_manufacturing_guidance"></span><span id="general_manufacturing_guidance"></span><span id="GENERAL_MANUFACTURING_GUIDANCE"></span>Allgemeine Manufacturing Anleitung


Für Windows 10 Mobile Ziel ist es, dass Partner erfolgreich sind, bei der Ermittlung effiziente und effektive Prozesse, die span Produktion, testen und warten. Zu diesem Zweck wird Microsoft Hilfestellung für die Tools und Prozesse, die für Fertigung und Unterstützung der Windows-10-Mobile-Geräten verwendet werden. Diese Anleitung beschreibt die Tools und Techniken, die bei der Herstellung OEMs verfügbar sind.

-   [Fertigung workflow](#manufacturing-workflow)

-   [Beispiel des Testbereichs nach der Phase des Fertigung](#example-test)

-   [Verwenden eines Hostcomputers zum Neustart Telefon so Modus blinkt, und erhalten Sie Informationen zur version](using-a-host-computer-to-reboot-a-phone-to-flashing-mode-and-get-phone-version-information.md)

## <a name="span-idmanufacturingsecurityrequirementsspanspan-idmanufacturingsecurityrequirementsspanspan-idmanufacturingsecurityrequirementsspanmanufacturing-security-requirements"></a><span id="Manufacturing_security_requirements"></span><span id="manufacturing_security_requirements"></span><span id="MANUFACTURING_SECURITY_REQUIREMENTS"></span>Sicherheitsanforderungen Fertigung


Endgültigen Bilder müssen konfiguriert sein, um eine Reihe von sicherheitsanforderungen erfüllen. Damit OEMs stellen Sie sicher, dass ihre Bilder Retail diese Anforderungen erfüllt werden, überprüft Windows 10 Mobile automatisch für einige der diesen Anforderungen beim ersten starten. Sonstige Anforderungen müssen von OEMs überprüft werden.

## <a name="span-idmobiledeploymentandimagingspanspan-idmobiledeploymentandimagingspanspan-idmobiledeploymentandimagingspanmobile-deployment-and-imaging"></a><span id="Mobile_deployment_and_imaging"></span><span id="mobile_deployment_and_imaging"></span><span id="MOBILE_DEPLOYMENT_AND_IMAGING"></span>Mobile Bereitstellung und imaging


Erste zum Erstellen und Testen von 10 für Windows mobile Editions bereit? Es folgt eine Übungseinheit, die durchlaufen neue mobile Geräte zu erstellen und anpassen, um den Bedürfnissen Ihrer Kunden zu erfüllen.

-   [Mobile Bereitstellung und imaging](mobile-deployment-and-imaging.md)

## <a name="span-idmanufacturingmodeofthefulloperatingsystemspanspan-idmanufacturingmodeofthefulloperatingsystemspanspan-idmanufacturingmodeofthefulloperatingsystemspanmanufacturing-mode-of-the-full-operating-system"></a><span id="Manufacturing_mode_of_the_full_operating_system"></span><span id="manufacturing_mode_of_the_full_operating_system"></span><span id="MANUFACTURING_MODE_OF_THE_FULL_OPERATING_SYSTEM"></span>Modus des vollständigen Betriebssystems Fertigung


Fertigung-Modus ist eine des vollständigen Betriebssystems, die für die Fertigung-bezogene Aufgaben wie das Komponente verwendet werden kann und getestet.

-   [Fertigung-Modus](manufacturing-mode.md)

-   [Boot Modus Management UEFI-Protokoll](boot-mode-management-uefi-protocol.md)

## <a name="span-idmicrosoftmanufacturingosmmosspanspan-idmicrosoftmanufacturingosmmosspanspan-idmicrosoftmanufacturingosmmosspanmicrosoft-manufacturing-os-mmos"></a><span id="Microsoft_Manufacturing_OS__MMOS_"></span><span id="microsoft_manufacturing_os__mmos_"></span><span id="MICROSOFT_MANUFACTURING_OS__MMOS_"></span>Microsoft Fertigung OS (MMOS)


Microsoft Fertigung OS (MMOS) ist eine optimierte Konfiguration des Betriebssystems, die eine effiziente Fertigung vereinfacht.

-   [Microsoft Fertigung OS](microsoft-manufacturing-os.md)

-   [Definition der MMOS-Bild](mmos-image-definition.md)

-   [Flash MMOS an das Gerät](flash-mmos-to-the-phone.md)

-   [Entwickelt testanwendungen MMOS](develop-mmos-test-applications.md)

-   [Fertigung testumgebung unterstützten APIs](manufacturing-test-environment-supported-apis.md)

-   [Bereitstellen und Testen einer Benutzermodus-testanwendung in MMOS](deploy-and-test-a-user-mode-test-application-in-mmos.md)

-   [Arbeiten mit WIM MMOS Bilder](working-with-wim-mmos-images.md)

## <a name="span-idflashingtoolsspanspan-idflashingtoolsspanspan-idflashingtoolsspanflashing-tools"></a><span id="Flashing_tools"></span><span id="flashing_tools"></span><span id="FLASHING_TOOLS"></span>Blinken-tools


Sie können ein benutzerdefiniertes blinkendes Tool die Lebenszyklus Bedürfnisse des Geräts entwickeln.

-   [Blinken tools](flashing-tools.md)

-   [Entwickeln von benutzerdefinierten OEM blinkendes tools](developing-custom-oem-flashing-tools.md)

## <a name="span-idmanufacturingworkflowspanspan-idmanufacturingworkflowspanspan-idmanufacturingworkflowspanmanufacturing-workflow"></a><span id="Manufacturing_workflow"></span><span id="manufacturing_workflow"></span><span id="MANUFACTURING_WORKFLOW"></span>Fertigung workflow


OEMs müssen Sie die Fertigung, um MMOS in ihren Fertigungsanlagen implementieren ermitteln.

Besprechen Sie den Fertigungsprozess ein vereinfachtes Modell der Fertigungslinie Workflow verwendet werden. Beachten Sie, dass jeder OEM einen eindeutigen Prozess hat. Dieses vereinfachte Modell wird als ein allgemeiner Referenzpunkt verwendet.

### <a name="span-idsimplefactoryflowspanspan-idsimplefactoryflowspanspan-idsimplefactoryflowspansimple-factory-flow"></a><span id="Simple_factory_flow"></span><span id="simple_factory_flow"></span><span id="SIMPLE_FACTORY_FLOW"></span>Einfache Factory Fluss

![OEM\-zu\-einfache\-Factory\-Ablauf\-Apollo](images/oem-manu-simple-factory-flow-apollo.png)

**Pinnwand Tests/SMT** – Bild blinkt über Gang Programmierer.

**Endgültige Assembly, Boot** – Marry Board mit Kunststoff; zum ersten Mal auf die Fertigung das Gerät gestartet wird.

**Manuellen Tests** – Zeile Worker führt Tests für Geräte wie Ton, Vibration, Kamera, Tastatur und So weiter.

Testen, in dem das Gerät angeschlossen ist, zum Aktivieren von Power und die Aufzeichnung von Testdaten, **RF/Anruf testen** – automatisiert werden.

**Endgültige Bereitstellung** – Automated Process where IMEI Daten geschrieben, Anpassungen werden geladen und beschriften abgeschlossen ist.

**Endgültige QA zum Packen** – endgültige manuelle Überprüfung des Geräts, klicken Sie dann auf packen.

**Random Beispiel testen** – eine angegebene Anzahl von Geräten sind nicht mehr Verpackung und getestet. Wenn Fehler einen bestimmten Schwellenwert erreicht ist, kann die gesamte Zeile zurückgerufen.

### <a name="span-idmanufacturingprocessoptionsspanspan-idmanufacturingprocessoptionsspanspan-idmanufacturingprocessoptionsspanmanufacturing-process-options"></a><span id="Manufacturing_process_options"></span><span id="manufacturing_process_options"></span><span id="MANUFACTURING_PROCESS_OPTIONS"></span>Fertigung Prozessoptionen

Jeder Hersteller hat verschiedenen Techniken und Tools, mit denen sie Windows-10-Mobile-Geräten herstellen. Hier werden zwei Optionen beschrieben, aber der OEM wird empfohlen, kombinieren Ansätze und Veränderungen bei Bedarf. Die beste technische Kenntnisse, Bezug Fertigung mit denen sich befindet, die die OEM Fertigung Zeile integriert. Wählen Sie die Anweisungen, die für Ihre Fertigungsprozesse und Unternehmen arbeitet.

Hier ist eine Zusammenfassung der beiden Beispiel Fertigungsprozesse bereitgestellt.

### <a name="span-idmanufacturingprocessoption1bootfromwimmmosimagespanspan-idmanufacturingprocessoption1bootfromwimmmosimagespanspan-idmanufacturingprocessoption1bootfromwimmmosimagespanmanufacturing-process-option-1-boot-from-wim-mmos-image"></a><span id="Manufacturing_process_option_1__boot_from_WIM_MMOS_image"></span><span id="manufacturing_process_option_1__boot_from_wim_mmos_image"></span><span id="MANUFACTURING_PROCESS_OPTION_1__BOOT_FROM_WIM_MMOS_IMAGE"></span>Manufacturing Prozessoption 1: Starten von WIM MMOS Bild

Sie können vorübergehend kopieren Sie ein Bild WIM (Windows Imaging) Microsoft Manufacturing OS (MMOS) über zu einem Gerät, und starten, Bild, das im Arbeitsspeicher veränderliche ausgeführt wird. Weitere Informationen zu MMOS finden Sie unter [Microsoft Manufacturing OS](microsoft-manufacturing-os.md).

Da der Test WIM MMOS Bild, das noch nie ausgeliefert wird auf dem Gerät verwendet wird, ermöglicht dieser Ansatz die Bereitstellung von zusätzlichen Fertigung Tools (Transporten, Extender). Darüber hinaus können OEMs funktionalen systemeigene APIs im Testbild. Zusätzliche Factory Test nur Treiber oder weitere Software kann im Bild WIM MMOS enthalten sein.

Ein Vorteil von diesem Ansatz ist, dass das Starten von einem WIM-Abbild im RAM schneller als das Bild blinkt ist.

![OEM\-zu\-Factory\-Prozesse\-Wim\-Mmos](images/oem-manu-factory-processes-wim-mmos.png)

Weitere Informationen finden Sie unter [Arbeiten mit Bildern WIM-MMOS](working-with-wim-mmos-images.md).

### <a name="span-idmanufacturingprocessoption2reflashthedevicespanspan-idmanufacturingprocessoption2reflashthedevicespanspan-idmanufacturingprocessoption2reflashthedevicespanmanufacturing-process-option-2-reflash-the-device"></a><span id="Manufacturing_process_option_2__reflash_the_device"></span><span id="manufacturing_process_option_2__reflash_the_device"></span><span id="MANUFACTURING_PROCESS_OPTION_2__REFLASH_THE_DEVICE"></span>Manufacturing Prozessoption 2: einen reflash das Gerät

Dieser Prozess verwendet zwei Bildern: einem zu Testzwecken Factory, und eine endgültige goldene Bild für das endgültige des Protokollversands Gerät. Wie das Bild MMOS WIM wird das Testbild, das noch nie ausgeliefert wird auf dem Gerät verwendet werden. Bedeutet dies, dass zusätzliche Manufacturing Tools (Transporten, Extender) enthalten sein können und nur systemeigenen APIs manufacturing aufgerufen werden kann.

![OEM\-zu\-einfache\-aktualisieren\-Fluss\-Apollo](images/oem-manu-simple-refresh-flow-apollo.png)

Dieser Ansatz ermöglicht es, falls zutreffend, um eine andere Version des Betriebssystems für den Test verwendet. Eine nützliche vorläufige Maßnahme möglicherweise wie Windows 10 Mobile testanwendungen migriert werden.

Einen Nachteil bei diesem Ansatz besteht darin, dass die Fertigung Zeile ausgelegt sein muss die Flashspeichers Mal gegen Ende des Prozesses Manufacturing auftritt.

Weitere Informationen zum Arbeiten mit der blinkende Tools finden Sie unter [Tools blinken](flashing-tools.md).

## <a name="span-idexampletestspanspan-idexampletestspanspan-idexampletestspanexample-test-area-by-manufacturing-phase"></a><span id="Example_test"></span><span id="example_test"></span><span id="EXAMPLE_TEST"></span>Beispiel des Testbereichs nach der Phase des Fertigung


Nach der Phase des Fertigung Testbereichs wird nur als Beispiel bereitgestellt. Jeder Hersteller möglicherweise möchten Sie die Tests anders anordnen.

**Modem testen (RF Mobilfunk Test)**

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Modem RF Kalibrierung</p></td>
</tr>
<tr class="even">
<td align="left"><p>Wi-Fi RX/TX-Leistung</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bluetooth-RX/TX-Leistung</p></td>
</tr>
</tbody>
</table>

 

**Gerät testen**

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Anzeige</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tastatur</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SIM-Schnittstelle</p></td>
</tr>
<tr class="even">
<td align="left"><p>Speicherkarte</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Kamera</p></td>
</tr>
<tr class="even">
<td align="left"><p>RTC</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Vortrag</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mikrofon</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sensor – ALS</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sensor – Magnetometer</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sensor – Nähe</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sensor – Beschleunigungsmesser</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hörer-Schnittstelle</p></td>
</tr>
<tr class="even">
<td align="left"><p>Potenz – Standby aktuelle</p></td>
</tr>
</tbody>
</table>

 

**Gerät-Bereitstellung**

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>IMEI</p></td>
</tr>
<tr class="even">
<td align="left"><p>SIM-Sperre</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bluetooth MAC</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sensoren Kalibrierung</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bereitstellen von Sicherheit</p></td>
</tr>
<tr class="even">
<td align="left"><p>MO-Bereitstellung</p></td>
</tr>
</tbody>
</table>

 

 

 





