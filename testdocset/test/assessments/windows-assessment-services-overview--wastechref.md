---
title: "Windows-Assessment-Services (Übersicht)"
description: "Windows Assessment Services (Übersicht)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 192c0739-dabd-4ff8-9ac8-5bf6e026757f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 716b3419d98aad9d33d6bc16cae15121d086a813
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-services-overview"></a>Windows Assessment Services (Übersicht)


Windows Assessment Services Automatisieren der Planung der Bewertung von einem zentralen Ort auf mehreren Computern ausgeführt wird. Es wird zur Qualitätsprobleme und Lösung von Problemen beschleunigen verwendet. Es ist ideal für konsistente Testprozesse und schnellere Lösung von Problemen zu ermöglichen.

## <a name="how-does-windows-assessment-services-work"></a>Wie funktioniert Windows Assessment Services?


Windows-Assessment-Services ist Testframework, das zum interagieren mit und zum Speichern von Objekten wie Testcomputer, Windows-Abbilder und Antwortdateien in Windows Assessment Services Freigaben konfiguriert ist. Bei Installation unter Windows Server 2012, Windows-Bereitstellungsdienste (Windows DS) bietet dynamische Treiber Provisioning (DDP) und zur Testcomputer für Computer-Suche und PXE-basierten Image-Bereitstellung verwendet wird. Wenn eine Bewertung abgeschlossen ist, werden die Ergebnisse auf den Server kopiert und in der Windows-Assessment-Services Ergebnisse Freigabe gespeichert, sodass sie in der Windows-Assessment-Services - Client (Windows ASC) verfügbar sind. Die Windows-ASC ist graphical User Interface, die Interaktion mit Windows Assessment Services verwendet wird.

Windows Assessment Services und die Windows-ASC können Sie folgende Aktionen ausführen:

-   Senden Sie mehrere Auftrag Anforderungen von Windows ASC Computern auf einem Windows Assessment Services server

-   Verwalten Sie Computer Inventar und bewerten Sie alle oder eine Teilmenge der Testcomputer, die in Inventar sind

-   Erstellen von Projekten mit verschiedenen Computern und verschiedenen Bildern

-   Erstellen von Aufträgen, die ein oder mehrere Bewertung enthalten

-   Führen Sie Aufträge auf eine oder mehrere Testcomputern

-   Analyse der Bewertungsergebnisse auf dem Server, um Testcomputern für andere Zwecke freizugeben

-   Analyse der Bewertungsergebnisse zur auf einem Server mit mehr Ressourcen als Testcomputer ausgeführt

-   Analyse der Bewertungsergebnisse mit erneut ausführen Diagnose oder Symbole aktualisiert

-   Überwachen Sie Auftragsstatus, während die Bewertung auf dem Testcomputer ausgeführt wird

-   Ergebnisse aus den Ergebnissen Server zuzugreifen freigeben und präsentieren sie konsistent zu überprüfen und Vergleich

## <a name="common-scenarios"></a>Häufige Szenarien


-   Wenden Sie ein Bild auf eine Gruppe von Computern, und führen Sie bestimmte Bewertung auf diesen Computern zum Vergleichen von eigenständigen Computer und Bild-Merkmale.

-   Führen Sie die gleiche Bewertung auf mehreren Computern oder mehrere Bewertung auf demselben Computer oder auf mehreren Computern mehrere Bewertung.

-   Importergebnisse aus mehreren Windows Assessment Services Labs in einer zentralen SQL-Datenbank für die Generierung von konsolidierten Berichten.

-   Führen Sie Analyse der Bewertungsergebnisse auf dem Server, auf dem Zielcomputer, für andere Zwecke freizugeben, die Ressourcen auf dem Server, der Analyse Zeit sparendes nutzen, und verwenden Sie Symbole, die bereits auf dem Server geladen.

## <a name="benefits"></a>Vorteile


-   Expedited Lösung für die Qualitätsprobleme durch die Zusammenarbeit von OEM, ODM, IHV und ISV vor dem Computer wechselt zu Fertigung auf.

-   Eine End-to-End-Tests und Validierung Plattform für die Verwendung in der OEM und ODM Factory-Prozess, der Microsoft-Tests, Diagnose und Debuggen Kompetenzen verwendet wird.

-   Leicht identifizierbar Qualität Unterscheidungsmerkmale für OEMs Einzelhandelsunternehmen und Privatkunden.

## <a name="limitations"></a>Einschränkungen


-   Windows Assessment Services unterstützt einen Auftrag zur selben Zeit auf ein Maximum von 150 Testcomputern ausgeführt. Bei der Bewertung von mehr als 150 Computern zur selben Zeit möglicherweise eine Beeinträchtigung der Systemleistung angezeigt.

-   Der Testcomputer müssen nicht Mitglied einer Domäne sein. WinRM erteilen nicht Berechtigungen Programme auf Domäne ausführen Computer beigetreten ist.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Services](windows-assessment-services-technical-reference.md)

[Windows Assessment Services häufige Szenarien](windows-assessment-services-how-to-topics--wastechref.md)

 

 







