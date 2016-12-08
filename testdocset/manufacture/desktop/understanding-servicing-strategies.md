---
author: Justinha
Description: Grundlegendes zu Wartungsstrategien
ms.assetid: 2e24e9e3-8216-4d8a-bd63-c61adddc6ac8
MSHAttr: PreferredLib:/library/windows/hardware
title: Grundlegendes zu Wartungsstrategien
ms.openlocfilehash: 9d7c41971ed142b7aaa4de2ab2a337f796f8287e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="understanding-servicing-strategies"></a>Grundlegendes zu Wartungsstrategien


A Windows® Bild in verschiedenen Phasen der Bereitstellung auf folgende Weise bedient werden kann: offline, während einer automatischen Installation oder online. Die Phase der Bereitstellung, die Sie auswählen, hängt von Ihrer Bereitstellungsstrategie ab.

[– Wartung offline](#offlineservicingstrategy): Hinzufügen und Entfernen von Updates, Treibern und Sprachpakete, und konfigurieren andere Einstellungen ohne Starten von Windows umfasst. Eine offline ist eine effiziente Möglichkeit zum Verwalten von vorhandenen Bilder, die auf einem Server gespeichert werden, da es die Notwendigkeit entfällt für aktualisierte Abbilder neu zu erstellen. Führen Sie offline zum Warten auf ein Bild, das bereitgestellt oder auf einem Laufwerk oder Verzeichnis angewendet wird.

[Warten eines Abbilds mithilfe von Windows Setup](#servicingdeploymentstrategy): umfasst das Bereitstellen einer Antwortdatei (Unattend.xml) Windows Setup implementiert. Die Antwortdatei enthält spezifische Wartungsvorgänge wie Treibern, Updates, Sprachpakete und andere Pakete hinzufügen. Warten eines Abbilds während einer automatischen Installations kann auf einfache Weise implementiert werden und eignet sich ideal für Setup-basierte Bereitstellung.

[Warten eines Betriebssystems ausgeführt](#onlineservicingstrategy): auch als online – Wartung bezeichnet, bei dieser Methode wird zum Hinzufügen von Treibern, Anwendungen und andere Pakete im Überwachungsmodus starten. Online – Wartung ist ideal für Treiber, wenn die Treiberpakete gemeinsame Installer oder Anwendung Abhängigkeiten vorhanden sind. Es ist außerdem effiziente, wenn die meisten Ihrer Wartung Pakete Installer, haben die Updates in der MSI-Datei oder KB.exe-Dateiformate sind oder die Anwendung installiert Windows-Dienste und Technologien (wie die .NET Framework oder die vollständige Plug & Play-Unterstützung) abhängig.

Die folgende Abbildung zeigt die Wartung Verkaufschancen in den verschiedenen Phasen der Bereitstellung zur Verfügung.

![Windows-Strategien für die Wartung](images/dep-win8-l-servicingstrategy.jpg)

## <a name="span-idofflineservicingstrategyspanspan-idofflineservicingstrategyspanspan-idofflineservicingstrategyspanoffline-servicing"></a><span id="OfflineServicingStrategy"></span><span id="offlineservicingstrategy"></span><span id="OFFLINESERVICINGSTRATEGY"></span>Offline – Wartung


Eine Offline wurde mit Windows Vista eingeführt. Eine Offline tritt beim Ändern oder ein Windows-Abbild vollständig offline service, ohne es zuerst zu starten. Für Windows Vista wurde das Paket-Manager-Befehlszeilentool zum Aktualisieren von Windows-Abbildern bereitgestellt. In Windows 7 und Windows 8 ersetzt Deployment Image Servicing and Management (DISM) Package Manager. Für Windows 8 können die meisten Betriebssystem Wartungsvorgänge auf Schwelle Windows offline mithilfe des Befehlszeilentools DISM ausgeführt werden. DISM ist mit Windows 8 installiert, und auch im Windows Assessment and Deployment Kit (Windows ADK). Weitere Informationen zu DISM finden Sie unter [DISM - Bereitstellung Abbildern und M\\Anagement technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

DISM kann offline Bildes verwendet werden:

-   Bereitstellen, stellen Sie erneut bereit, und heben Sie die Bereitstellung eines Bilds in einer WIM-Datei für die Wartung.

-   Abfragen von Informationen zu einem Windows-Abbild.

-   Hinzufügen oder entfernen und Aufzählen von Treibern, die als INF-Dateien bereitgestellt.

-   Hinzufügen, entfernen und Aufzählen von Paketen, einschließlich Language Packs als CAB-Dateien bereitgestellt.

-   Hinzufügen von MSU-Dateien.

-   Konfigurieren von internationalen Einstellungen.

-   Aktivieren, deaktivieren und Aufzählen von Features des Windows-Betriebssystems.

-   Upgrade auf eine höhere Version von Windows.

-   Überprüfen Sie die Verfügbarkeit eines Patches für Windows Installer-Anwendung (MSP-Datei).

-   Auflisten von Anwendungen und Anwendungspatches, die in einem Windows-Abbild installiert.

-   Gelten Sie offline-Wartung Abschnitt einer Antwortdatei.

-   Aktualisieren eines Abbilds Windows Vorinstallation Environment (Windows PE).

Weitere Informationen dazu, wie Sie einer bereitgestellten Abbilds finden Sie unter [Service ein Windows-Abbild bereitgestellt](service-a-mounted-windows-image.md).

Weitere Informationen zum Warten eines angewendeten Abbilds finden Sie unter [Service ein Windows-Abbild angewendet](service-an-applied-windows-image.md).

## <a name="span-idservicingdeploymentstrategyspanspan-idservicingdeploymentstrategyspanspan-idservicingdeploymentstrategyspanservicing-an-image-by-using-windows-setup"></a><span id="ServicingDeploymentStrategy"></span><span id="servicingdeploymentstrategy"></span><span id="SERVICINGDEPLOYMENTSTRATEGY"></span>Warten eines Abbilds mithilfe von Windows Setup


Verwenden Sie eine Antwortdatei mit Windows Setup zum Warten eines Abbilds während der unterschiedlichen Konfigurationsphasen von Windows Setup. Die Antwortdatei enthält alle Einstellungen, die zum Konfigurieren und aktualisieren das Windows-Abbild verwendet werden. Setup Ruft die Antwortdatei mehrmals während des Bereitstellungsprozesses. Nachdem das Betriebssystem installiert ist, können Sie Modus oder im Windows-Willkommensseite Überwachungsmodus starten. Weitere Informationen zur Installation von Windows finden Sie unter [Technische Referenz zu Windows Setup](windows-setup-technical-reference.md). Weitere Informationen zu Konfigurationsphasen finden Sie unter [Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md).

Eine Antwortdatei kann während der Installation verwendet werden:

-   Hinzufügen oder Entfernen eines Language Packs.

-   Konfigurieren von internationalen Einstellungen.

-   Hinzufügen und Entfernen von Treibern.

-   Hinzufügen und Entfernen von Paketen.

-   Aktivieren und Deaktivieren von Features des Windows-Betriebssystems.

## <a name="span-idonlineservicingstrategyspanspan-idonlineservicingstrategyspanspan-idonlineservicingstrategyspanservicing-a-running-operating-system"></a><span id="OnlineServicingStrategy"></span><span id="onlineservicingstrategy"></span><span id="ONLINESERVICINGSTRATEGY"></span>Warten eines Betriebssystems ausgeführt


Es gibt mehrere Tools, die verwendet werden können, zu ein ausgeführten Betriebssystem (auch bekannt als für die Wartung) service. Sie sollten im hinzu, das Windows-Abbild Updates Überwachungsmodus starten. Überwachungsmodus erfordert keine Einstellungen in der Windows-Willkommensseite angewendet werden soll, einen schnelleren Zugriff auf dem Desktop zulassen. Nachdem Sie im Überwachungsmodus gestartet haben, können Sie Hinzufügen von Plug & Play-Gerätetreibern, Anwendungen und Komponenten des Systems installieren und testen die Gültigkeit der Installation. Weitere Informationen dazu, wie Sie den Überwachungsmodus verwenden, finden Sie unter [Überwachungsmodus oder OOBE Boot für Windows](boot-windows-to-audit-mode-or-oobe.md).

Die folgenden Tools werden in der Regel verwendet, so aktualisieren Sie ein Windows-Betriebssystem ausgeführt wird:

-   Mithilfe von DISM Treiber, internationalen Einstellungen, Pakete und Features aufgelistet werden, und unbeaufsichtigte dateieinstellungen zu übernehmen. Weitere Informationen finden Sie unter [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

-   Verwenden Sie DPInst Treiber für erkannte Hardware hinzufügen. Informationen zu DPInst und andere Tools in Windows Driver Kit (WDK) verfügbar sind finden Sie unter [Download Kits und Tools für Windows](http://go.microsoft.com/fwlink/?LinkId=89603).

-   Verwenden Sie PNPUtil zum Hinzufügen oder entfernen und Aufzählen von Treibern. Weitere Informationen finden Sie unter [Use PnPUtil in einer Befehlszeile installieren eines Plug & Play-Geräts](http://go.microsoft.com/fwlink/?LinkId=139151).

-   Verwenden Sie Windows Update Standalone-Installer Servicepacks oder andere MSU-Dateien hinzufügen. Weitere Informationen finden Sie unter [Hinweise zum Windows Update Standalone-Installer (Wusa.exe) und zu MSU-Dateien in Windows Vista](http://go.microsoft.com/fwlink/?LinkId=90850)

-   Verwenden Sie zum Hinzufügen oder Entfernen von Sprachpaketen LPKSetup.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Deployment Image Servicing and Management (DISM) bewährte Methoden](deployment-image-servicing-and-management--dism--best-practices.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






