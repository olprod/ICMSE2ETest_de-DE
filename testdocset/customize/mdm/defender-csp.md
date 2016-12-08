---
title: Defender CSP
description: Defender CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 481AA74F-08B2-4A32-B95D-5A3FD05B335C
ms.openlocfilehash: 88cc8351e50f8db216ea5dc92bac5660045bfa43
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="defender-csp"></a>Defender CSP


Der Dienstanbieter für Windows Defender Konfiguration wird verwendet, um verschiedene Windows Defender Aktionen innerhalb des Unternehmens zu konfigurieren.

Die folgende Abbildung zeigt den Windows Defender Konfiguration-Dienstanbieter in der Baumstruktur

![Defender Csp Diagramm](images/provisioning-csp-defender.png)

<a href="" id="detections"></a>**Erkannte**  
Ein interior-Knoten alle von Windows Defender erkannten Bedrohungen gruppiert.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid"></a>**Erkannte / ***_ThreatId_**  
Die ID einer Bedrohung an, das von Windows Defender erkannt wurde.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-name"></a>* *Erkannte /*ThreatId*/Name**  
Der Name der einer bestimmten Bedrohung.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-url"></a>* *Erkannte /*ThreatId*/URL**  
URL-Link für Weitere Informationen.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-severity"></a>* *Erkannte /*ThreatId*/Severity**  
Bedrohung Severity-ID.

Der Datentyp ist eine ganze Zahl.

In der folgenden Liste sind die unterstützten Werte:

-   0 = unbekannt
-   1 = niedrig
-   2 = Mittel
-   4 = hoch
-   5 = Severe

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-category"></a>* *Erkannte /*ThreatId*/Category**  
Bedrohung Kategorie-ID.

Der Datentyp ist eine ganze Zahl.

In der folgenden Tabelle werden die unterstützten Werte beschrieben:

| Wert | Beschreibung                 |
|-------|-----------------------------|
| 0     | Ungültig                     |
| 1     | Adware                      |
| 2     | Spyware                     |
| 3     | "Password Stealer"            |
| 4     | Trojanischen downloader           |
| 5     | Wurm                        |
| 6     | Backdoor                    |
| 7     | Remotezugriff trojanischen        |
| 8     | Trojanischen                      |
| 9     | E-Mail-flooder               |
| 10    | Keylogger                   |
| 11    | Wählhilfe                      |
| 12    | Software für die Überwachung         |
| 13    | Browser-Modifizierer            |
| 14    | Cookie                      |
| 15    | Browser-Plug-in              |
| 16    | AOL-Exploits                 |
| 17    | Nuker                       |
| 18    | Einschränkt und Sicherheit           |
| 19    | Scherzprogramm                |
| 20    | Schädlichen ActiveX-Steuerelement     |
| 21    | Software bundler            |
| 22    | Stealth Modifizierer            |
| 23    | Einstellungen Modifizierer           |
| 24    | Toolbar                     |
| 25    | Remotesteuerung-software     |
| 26    | Trojanischen FTP                  |
| 27    | Potenzielle unerwünschter software |
| 28    | ICQ-Exploits                 |
| 29    | Trojanischen telnet               |
| 30    | Exploits                     |
| 31    | Datei-sharing-Programm        |
| 32    | Tool zum Erstellen von Schadsoftware       |
| 33    | Remotesteuerung software     |
| 34    | Tool                        |
| 36    | Trojanischen Denial-of-service    |
| 37    | Trojaner              |
| 38    | Trojanischen Masse mailer          |
| 39    | Trojanischen Software für die Überwachung  |
| 40    | Trojanischen Proxyserver         |
| 42    | Virenschutz                       |
| 43    | Bekannte                       |
| 44    | Unbekannt                     |
| 45    | SPP                         |
| 46    | Verhalten                    |
| 47    | Sicherheitsrisiko               |
| 48    | Richtlinie                      |

 

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-currentstatus"></a>* *Erkannte /*ThreatId*/CurrentStatus**  
Informationen über den aktuellen Status der Bedrohung.

Der Datentyp ist eine ganze Zahl.

In der folgenden Liste sind die unterstützten Werte:

-   0 = unbekannt
-   1 = erkannt
-   2 = bereinigt
-   3 = isoliert
-   4 = entfernt
-   5 = zugelassen
-   6 = blockiert
-   102 = Clean ist fehlgeschlagen
-   103 = Isolieren fehlgeschlagen
-   104 = Fehler beim Entfernen
-   105 = konnte nicht zulassen
-   106 = abgebrochen
-   107 = Block ist fehlgeschlagen

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-executionstatus"></a>* *Erkannte /*ThreatId*/ExecutionStatus**  
Informationen zu den Ausführungsstatus der Bedrohung.

Der Datentyp ist eine ganze Zahl.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-initialdetectiontime"></a>* *Erkannte /*ThreatId*/InitialDetectionTime**  
Zum ersten Mal in bestimmten Bedrohung erkannt wurde.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-lastthreatstatuschangetime"></a>* *Erkannte /*ThreatId*/LastThreatStatusChangeTime**  
Der letzte Zeitpunkt diese spezielle Bedrohung geändert wurde.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="detections-threatid-numberofdetections"></a>* *Erkannte /*ThreatId*/NumberOfDetections**  
Anzahl der vorkommen, die auf einem bestimmten Client diese Bedrohung erkannt wurde.

Der Datentyp ist eine ganze Zahl.

Unterstützte Vorgang ist Get.

<a href="" id="health"></a>**Integrität**  
Ein interior-Knoten Informationen zu Windows Defender Integritätsstatus zusammenzufassen.

Unterstützte Vorgang ist Get.

<a href="" id="health-computerstate"></a>**Integrität/ComputerState**  
Geben Sie den aktuellen Status des Geräts.

Der Datentyp ist eine ganze Zahl.

In der folgenden Liste sind die unterstützten Werte:

-   0 = bereinigen
-   1 = ausstehende vollständigen Scan
-   2 = Ausstehender Neustart
-   4 = ausstehende manuelle Schritte
-   8 = ausstehenden offline Scan
-   16 = ausstehende kritischen Fehler

Unterstützte Vorgang ist Get.

<a href="" id="health-defenderenabled"></a>**Integrität/DefenderEnabled**  
Gibt an, ob der Dienst Windows Defender ausgeführt wird.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-rtpenabled"></a>**Integrität/RtpEnabled**  
Gibt an, ob Schutz in Echtzeit ausgeführt wird.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-nisenabled"></a>**Integrität/NisEnabled**  
Gibt an, ob Schutz ausgeführt wird.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-quickscanoverdue"></a>**Integrität/QuickScanOverdue**  
Gibt an, ob ein Windows Defender schneller Scan für das Gerät überfällig ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-fullscanoverdue"></a>**Integrität/FullScanOverdue**  
Gibt an, ob eine vollständige Überprüfung Windows Defender überfällig für das Gerät ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-signatureoutofdate"></a>**Integrität/SignatureOutOfDate**  
Gibt an, ob die Signatur Windows Defender veraltet sind.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-rebootrequired"></a>**Integrität/RebootRequired**  
Gibt an, ob ein geräteneustart erforderlich ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-fullscanrequired"></a>**Integrität/FullScanRequired**  
Gibt an, ob eine vollständige Überprüfung Windows Defender erforderlich ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgang ist Get.

<a href="" id="health-engineversion"></a>**Integrität/%ENGINEVERSION%**  
Versionsnummer des aktuellen Moduls Windows Defender auf dem Gerät.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="health-signatureversion"></a>**Integrität/SignatureVersion**  
Die Versionsnummer der aktuellen Windows Defender Signaturen auf dem Gerät.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="health-defenderversion"></a>**Integrität/DefenderVersion**  
Die Versionsnummer von Windows Defender auf dem Gerät.

Der Datentyp ist eine Zeichenfolge an.

Unterstützte Vorgang ist Get.

<a href="" id="health-quickscantime"></a>**Integrität/QuickScanTime**  
Zeitpunkt des letzten Windows Defender quick Scannen des Geräts.

Der Datentyp ist eine Zeichenfolge an.

Unterstützte Vorgang ist Get.

<a href="" id="health-fullscantime"></a>**Integrität/FullScanTime**  
Zeitpunkt der letzten vollständigen Windows Defender-Scan des Geräts.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="health-quickscansigversion"></a>**Integrität/QuickScanSigVersion**  
Signatur-Version für die letzten quick Überprüfung des Geräts verwendet.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="health-fullscansigversion"></a>**Integrität/FullScanSigVersion**  
Signatur-Version für die letzte vollständige Überprüfung des Geräts verwendet.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="scan"></a>**Überprüfung**  
Auf einem Gerät scan-Knoten, die verwendet werden kann, um eine Windows-Defender zu starten.

Gültige Werte sind:
- 1 – schnell-scan
- 2 - vollständige Überprüfung

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="updatesignature"></a>**Auf**  
Knoten, der verwendet werden kann, um Signatur-Updates für Windows Defender auszuführen.

Unterstützte Vorgänge sind Get und ausführen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






