---
title: Neustart CSP
description: Neustart CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4E3F1225-BBAD-40F5-A1AB-FF221B6BAF48
ms.openlocfilehash: d4750d4f47fee2e890885585bce43ff13d1da13d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reboot-csp"></a>Neustart CSP


Der Neustart Konfiguration-Dienstanbieter wird verwendet, um Einstellungen Neustart konfigurieren.

Das folgende Diagramm veranschaulicht die Neustart-Konfiguration dienstanbieterobjekten Management im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM), OMA-Clientbereitstellung und Enterprise-DM verwendet.

![Neustart](images/reboot-csp.png)

<a href="" id="--vendor-msft-reboot"></a>**./Vendor/MSFT/Reboot**  
Der für den Neustart Konfigurationsdienstanbieter Stammknoten.

Der unterstützte Vorgang ist abrufen.

<a href="" id="rebootnow"></a>**RebootNow**  
Dieser Knoten führt einen Neustart des Geräts aus.

> **Hinweis**  Wenn dieser Knoten im Zustand Execute bleibt, wird das Gerät bei jeder Synchronisierung neu gestartet. Es wird empfohlen, dass Sie den Execute-Zustand gelöscht werden, sobald die Synchronisierung aufgetreten ist.

 

Der unterstützte Vorgang ist ausführen.

<a href="" id="schedule"></a>**Zeitplan**  
Der unterstützte Vorgang ist abrufen.

<a href="" id="schedule-single"></a>**Zeitplan/Single**  
Dieser Knoten wird ein Neustart des Computers zu einer geplanten Zeitpunkt ausgeführt. Festlegen eines Datums mit null (leeren), löschen Sie den vorhandenen Zeitplan. Der Wert für Datum und Uhrzeit ISO8601 ist, und das Datum und die Uhrzeit werden benötigt. Beispiel: 2015-12-15T07:36:25Z

Der unterstützte Vorgang ist Get und ersetzen.

<a href="" id="schedule-dailyrecurrent"></a>**Zeitplan/DailyRecurrent**  
Dieser Knoten wird ein Neustart des Computers zu einem bestimmten Zeitpunkt beginnend mit dem konfigurierten Startzeit und Datum pro Tag ausgeführt. Festlegen eines Datums mit null (leeren) werden den vorhandenen Zeitplan gelöscht werden. Der Wert für Datum und Uhrzeit ISO8601 ist, und das Datum und die Uhrzeit werden benötigt. Beispiel: 2015-12-15T07:36:25Z

Der unterstützte Vorgang ist Get und ersetzen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






