---
author: kpacquer
Description: Sicherheitsanforderungen blinken
ms.assetid: 78c22243-e9a4-4394-9f91-5922c15286e8
MSHAttr: PreferredLib:/library/windows/hardware
title: Sicherheitsanforderungen blinken
ms.openlocfilehash: f2b653aa757d8a2a324f3ec67e8340cda39c7f74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flashing-security-requirements"></a>Sicherheitsanforderungen blinken


Bevor blinken auftritt, muss alle OEM blinkendes Mechanismen kryptografischen Signaturen im Bild diese Kette Tasten Besitz der OEM überprüft werden. Diese Überprüfung der kryptografischer Signatur auf das Bild auf dem Gerät (nicht auf einem desktop blinkende Tool) ausgeführt werden muss und ausgeführt werden muss, bevor das Bild auf eMMC Arbeitsspeicher aktualisiert wird. Diese Anforderung ist um zu verhindern, dass die Geräte Gefährdung von Benutzern, die versuchen, die datensicherheit im System unterlaufen vorgesehen. Mechanismen und aktualisieren Sie den Zustand des Geräts (Debugger, Arbeitsspeicher Inspectors usw.) oder flash kann, die nicht ordnungsgemäß gesichert werden konnte, um das Gerät Sicherheitsmechanismen zu umgehen von einem Angreifer verwendet werden.

Die implementierten Lösungen müssen vollständig ausfallsichere sein, auch wenn das Gerät reverse Engineering (d. h., selbst wenn der Benutzer den Vorgang des Codes Sicherheit in der Firmware oder SoC versteht).

## <a name="span-idflashingsecurityrequirementssummaryspanspan-idflashingsecurityrequirementssummaryspanspan-idflashingsecurityrequirementssummaryspanflashing-security-requirements-summary"></a><span id="Flashing_security_requirements_summary"></span><span id="flashing_security_requirements_summary"></span><span id="FLASHING_SECURITY_REQUIREMENTS_SUMMARY"></span>Zusammenfassung sicherheitsanforderungen blinken


Sicherheit für den Einzelhandel Geräte muss auch die folgenden Anforderungen erfüllen:

-   Sichere blinkende Technologien können nur auf Geräten Retail enthalten sein.

-   Bilder, die blinken soll müssen über einen Prozess, die vom OEM oder Microsoft überprüft und gesteuert, kryptografisch signiert werden.

-   Kryptografische Signaturen für Bilder zugeordnet werden müssen durch den Code auf dem Gerät unmittelbar vor dem blinken überprüft werden.

-   Code, die auf dem Gerät kryptografische Signaturen überprüft muss arbeitet, und kryptografische Schlüsselmaterial auf dem Gerät für die Überprüfung verwendet sein trustworthy an der Stelle in der Zeit, die sie verwendet wird.

-   Groß genug Verschlüsselungsalgorithmen müssen verwendet werden – mindestens 2048 mit SHA-256 RSA.

-   Das blinkende Tool muss die SMBIOS Gerät Identification Werte vor blinken überprüfen. Weitere Informationen finden Sie unter [Developing benutzerdefinierten OEM blinkende Tools](developing-custom-oem-flashing-tools.md).

-   Das blinkende Tool muss Bild Integrität Validierung zum Schutz vor unbefugt geänderten Bilder implementieren. Weitere Informationen finden Sie unter [Developing benutzerdefinierten OEM blinkende Tools](developing-custom-oem-flashing-tools.md).

-   Best Practices für Source Code Entwicklung und Bereitstellung Kette Sicherheit müssen eingehalten werden.

-   Ein Bedrohungsmodell muss zum Identifizieren Risiken Priorität, Bedrohungen und Sicherheitslücken angewendet werden.

## <a name="span-idrecommendedflashingsolutionspanspan-idrecommendedflashingsolutionspanspan-idrecommendedflashingsolutionspanrecommended-flashing-solution"></a><span id="Recommended_flashing_solution"></span><span id="recommended_flashing_solution"></span><span id="RECOMMENDED_FLASHING_SOLUTION"></span>Empfohlene Lösung blinkende


Im folgende Diagramm veranschaulicht eine blinkende Lösung, die den blinkende sicherheitsanforderungen entspricht. Bilder, die blinken soll müssen signiert sein, vom OEM Signieren mit dokumentierte Verfahren Behörde sicherstellen, dass ein hohes Maß an Steuerung und Sicherheit über den gesamten Prozess vorhanden ist. Die Komponente, die den blinkenden Vorgang initiiert muss eine kryptografische Bestätigung der Signatur auf das Bild mit trustworthy Schlüsselmaterial unmittelbar vor dem blinken blinken ausführen.

Der kryptografische Schlüssel gespeichert werden soll, sodass er gebunden ist entweder auf sichere Boot wichtige Material (OEM\_PK\_HASH oder UEFI Variable PK) oder mit einem öffentlichen Schlüssel, die in einer Binärdatei eingebettet ist, die von sicheren Boot kryptografisch überprüft wird. Es ist nicht akzeptabel den öffentlichen oder privaten Schlüssel in der DPP oder in eine beliebige andere nicht signierte und nicht überprüfte Dateispeicher gespeichert.

![OEM\-Fieldservicesec\-Flashingreq](images/oem-fieldservicesec-flashingreq.png)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Entwickeln von benutzerdefinierten OEM blinkendes tools](developing-custom-oem-flashing-tools.md)

[Implementieren von Bild Integrität Überprüfung in benutzerdefinierten blinkende tools](implementing-image-integrity-validation-in-custom-flashing-tools.md)

 

 






