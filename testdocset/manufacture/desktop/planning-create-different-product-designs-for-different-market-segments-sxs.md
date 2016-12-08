---
author: Justinha
Description: "Planen: Anpassen von Verweis Bilder für unterschiedliche Benutzergruppen"
ms.assetid: b98343dd-bb5e-4904-9b40-f44cea88fbf0
MSHAttr: PreferredLib:/library/windows/hardware
title: "Planen: Anpassen von Verweis Bilder für unterschiedliche Benutzergruppen"
ms.openlocfilehash: 746e53de2b5525e27ef41a7dab323e28f5db0657
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="planning-customizing-reference-images-for-different-audiences"></a>Planen: Anpassen von Verweis Bilder für unterschiedliche Benutzergruppen

Anstatt ein Gerät Design, das versucht, alle Benutzer angepasst wird, unterstützen Windows Image-Verwaltungstools Sie anpassen, Gerätedesigns, um den spezifischen Bedürfnissen von verschiedenen Kunden zu erfüllen.

Um zu Beginn sollten ein Hardware-Design, das auf eine bestimmte Benutzergruppe, Land/Ihrer Region oder Preis abzielt auswählen. Erstellen Sie eine Basis-Image für dieses Design und Testen Sie es. Im nächsten Schritt Anpassen von Windows für die betreffende Benutzergruppe, umfassen branding, Logos, Sprachen und apps.

## <a name="span-iddevicetypesspanspan-iddevicetypesspanspan-iddevicetypesspandevice-types"></a><span id="Device_types"></span><span id="device_types"></span><span id="DEVICE_TYPES"></span>Arten von Geräten

Sollten Sie separate Entwürfe für unterschiedliche Gerätetypen, wie kostengünstige oder Leistung Laptops oder Desktops kostengünstige oder Leistung erstellen. Jedes dieser Formate enthält verschiedene wichtige Unterscheidungsmerkmale, wie etwa Akkulaufzeit Leben oder Grafiken.

Obwohl Windows Basis Treiber für viele allgemeine Geräte umfasst, erfordert einige Hardware spezialisierte Gerätetreibern, die installiert und gelegentlich aktualisiert werden müssen.

Viele Treiber dienen zum offline installiert werden, ohne die Windows-Abbild zu starten.

Verwenden Sie Windows-Bewertungstools dafür sorgen, dass die apps und Hardware, die Sie installieren auch in verschiedenen Umständen ausführen können.

## <a name="span-idarchitecturespanspan-idarchitecturespanspan-idarchitecturespanarchitecture"></a><span id="Architecture"></span><span id="architecture"></span><span id="ARCHITECTURE"></span>Architektur

Wenn Sie planen, erstellen Sie Geräte mit 64-Bit- und 32-Bit-(x86) Chipsätze und Architekturen werde benötigen Sie separate Bilder basieren. Sie benötigen auch verschiedene Versionen von Treibern, Pakete und Updates.

## <a name="span-idretailcustomersandbusinesscustomersspanspan-idretailcustomersandbusinesscustomersspanspan-idretailcustomersandbusinesscustomersspanretail-customers-and-business-customers"></a><span id="Retail_customers_and_business_customers"></span><span id="retail_customers_and_business_customers"></span><span id="RETAIL_CUSTOMERS_AND_BUSINESS_CUSTOMERS"></span>Privatkunden und Geschäftskunden

Wenn Sie Designs für beide retail und Geschäftskunden, können Sie mit beginnen erstellen ein einzelnes basieren soll wie oder Windows 10 Pro 10 Home Edition und dann später aktualisieren, auf eine höhere Version wie Windows 10 Enterprise, je nach Bedarf. Nachdem Sie eine höhere Edition erstellt haben, können jedoch Sie es auf der unteren Edition nicht herabstufen. Weitere Informationen finden Sie unter [Aktualisierungspfade für Windows](http://go.microsoft.com/fwlink/?LinkId=526838).

Wenn Sie Geräte Privatkunden verkaufen erstellen, müssen Sie eine Reihe von Mindestanforderungen erfüllen. Informationen finden Sie in der Anleitung Lizenzierung und Richtlinie im [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358).

Wenn Sie Geräte für Unternehmen erstellen, müssen Sie weniger Einschränkungen. IT-Experten können ihren Geräten in auf unterschiedliche Weise anpassen. Allerdings sollten Sie die Auswirkungen der IT-Richtlinien als auch den Anforderungen der Kunden wie Migrieren von Daten, aktivieren Sicherheits-Tools und Verwalten von Volume Lizenzverträge und Product Keys.

## <a name="span-idregionsspanspan-idregionsspanspan-idregionsspanregions"></a><span id="Regions"></span><span id="regions"></span><span id="REGIONS"></span>Formularbereichen (engl.)

Erwägen Sie verschiedene Basis Bilder für die unterschiedlichen Regionen erstellen.

Die Ressourcendateien für Windows und andere apps wie Microsoft Office groß - sein können wie einige Ressourcen lokalisierten Handschrift und die Spracherkennung, dass Ressourcen mehrere hundert Megabyte sind.

Um Speicherplatz zu speichern, haben wir die Language Packs aufteilen. Dies kann Ihnen weitere Sprachen für Ihre Kunden Vorinstallation oder Speicherplatz auf dem Bild zu speichern. Beispielsweise um einen großen Bereich target, Sie möglicherweise Vorinstallation die grundlegenden Sprachkomponenten wie Text und Schnittstelle Benutzerdateien für viele Bereiche innerhalb der Region jedoch nur die handschrifterkennung für Geräte mit Stifte einschließen, oder umfassen nur Sprach- und Speech-Tools für Cortana auf Geräten mit integrierte Mikrofone. Benutzer können diese Komponenten später bei Bedarf herunterladen.

## <a name="span-idsampleplanspanspan-idsampleplanspanspan-idsampleplanspansample-plan"></a><span id="Sample_plan"></span><span id="sample_plan"></span><span id="SAMPLE_PLAN"></span>Beispielplan

In diesem Lab verwendet die folgenden drei Beispiele für Hardwarekonfigurationen.

|                              |              |                     |                                   |
|------------------------------|--------------|---------------------|-----------------------------------|
| Hardware-Konfiguration:      | 1            | 1 B                  | 2                                 |
| Formfaktor                  | Kleine tablet | 2-in-1              | Notizbuch                          |
| Architektur                 | x86          | x86                 | x64                               |
| Arbeitsspeicher (RAM)                          | 1 GB         | 2 GB                | 4 GB                              |
| Datenträgerkapazität und Typ       | 16 GB eMMC   | 32 GB eMMC          | 500 GB-FESTPLATTE                        |
| Komprimierung verwendet        | Ja          | Nein                  | Nein                                |
| Anzeigegröße                 | 8"           | 10"                 | 14"                               |
| Windows-SKU                  | Home (Homepage)          | Pro                 | Home (Homepage)                               |
| Region / Sprache(n)           | EN-US        | EN-US, FR-FR, ES-ES | EN-GB, DE-DE, FR-FR, ES-ES ZH-CN |
| Cortana                      | Ja          | Ja                 | Ja                               |
| Posteingang apps (Universal)       | Ja          | Ja                 | Ja                               |
| Stift                          | Nein           | Ja                 | Nein                                |
| Office (Universal)           | Ja          | Ja                 | Ja                               |
| Windows-desktopanwendungen | Nein           | Ja                 | Ja                               |
| Office 2016                  | Nein           | Ja                 | Ja                               |
| Compact OS                   | Ja          | Ja                 | Nein                                |
 
 Hinweise:
* Wir können ein Bild für Hardwarekonfiguration 1 b mit Hardware Konfiguration 1 als Basis-Bild erstellen.
* Wir können nicht aus Hardware Konfiguration 1 oder 1 b, Hardware Konfiguration 2 erstellt werden, da sie eine andere Architektur verwenden.
