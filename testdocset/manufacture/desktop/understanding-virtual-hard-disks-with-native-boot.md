---
author: Justinha
Description: Grundlegendes zu virtuellen Festplatten mit systemeigenem Start
ms.assetid: e063e475-6f39-4ed9-9473-ea7537adc30a
MSHAttr: PreferredLib:/library/windows/hardware
title: Grundlegendes zu virtuellen Festplatten mit systemeigenem Start
ms.openlocfilehash: bed073d5696d45f11a9dbf1cd60923501e06c5c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="understanding-virtual-hard-disks-with-native-boot"></a>Grundlegendes zu virtuellen Festplatten mit systemeigenem Start


Systemeigene Start ermöglicht virtuellen Festplatten (VHDs) auf einem Computer ohne einen virtuellen Computer oder *Hypervisor*ausgeführt. Ein Hypervisor ist eine Ebene der Software unter dem Betriebssystem, das virtuellen Maschinen ausgeführt wird.

## <a name="span-idbkmkwhatisvhdspanspan-idbkmkwhatisvhdspanspan-idbkmkwhatisvhdspanwhat-is-vhd-with-native-boot"></a><span id="BKMK_whatIsVHD"></span><span id="bkmk_whatisvhd"></span><span id="BKMK_WHATISVHD"></span>Was ist eine virtuelle Festplatte mit systemeigenem Start?


Eine virtuelle Festplatte kann als ausgeführtes Betriebssystem für die designierte Hardware, ohne andere übergeordnetes Betriebssystem, virtuellen Computer oder Hypervisor verwendet werden. Windows datenträgerverwaltung Tools, das DiskPart-Tool und die Datenträger Verwaltung von Microsoft® Management Console (Diskmgmt.msc), können zum Erstellen einer VHD-Datei verwendet werden. Eine unterstützte Windows, die WIM-Datei auf einer virtuellen Festplatte und die virtuelle Festplatte angewendet werden kann kann mit mehreren Systemen kopiert werden. Der Windows-Start-Manager kann zum direkt in die virtuelle Festplatte Starten konfiguriert werden.

Die virtuelle Festplatte kann auch auf einem virtuellen Computer für die Verwendung mit der Hyper-V-Rolle in Windows Server verbunden werden.

Systemeigenem Start VHDs nicht entwickelt und Vollbild-Bereitstellung auf allen Clients oder Server Systemen ersetzen soll. Enterprise-Umgebungen bereits Verwaltung und Verwendung von VHD-Dateien für die Bereitstellung des virtuellen Computers erhalten am meisten profitieren vom systemeigenem Start VHD Funktionen. Verwenden die VHD-Datei als eine allgemeine Container Bildformat für virtuelle Computer und designierte Hardware vereinfacht die Image-Verwaltung und Bereitstellung in einer unternehmensumgebung.

Weitere Informationen zur Virtualisierung in Windows finden Sie unter [diese Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=142055). Weitere Informationen zu virtuellen Festplatten mit systemeigenem Start finden Sie unter [diese Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=142054).

## <a name="span-idbkmkcommonscenariosspanspan-idbkmkcommonscenariosspanspan-idbkmkcommonscenariosspancommon-scenarios"></a><span id="BKMK_commonScenarios"></span><span id="bkmk_commonscenarios"></span><span id="BKMK_COMMONSCENARIOS"></span>Häufige Szenarien


In den folgenden Szenarien werden häufig virtuellen Festplatten mit systemeigenem Start verwendet:

-   Verwenden die datenträgerverwaltung Tools zum Erstellen und *Anfügen* einer virtuellen Festplatte für die offline-Abbild-Verwaltung. Verwenden Sie zum Anfügen einer Virtuellen den Befehl **Attach Vdisk** die virtuelle Festplatte aktiviert, sodass es auf dem Host als Laufwerk anstelle von als VHD-Datei angezeigt wird.

-   Bereitstellen Verweis Abbildern auf Remotefreigaben für Abbildern.

-   Verwalten und Bereitstellen einer allgemeinen Referenzabbilds im virtuellen oder physischen Computern ausgeführt werden.

-   Konfigurieren von VHD-Dateien für den systemeigenen Start ohne vollständige übergeordnete Installation.

-   Konfigurieren eines Computers starten Sie mehrere lokale VHD-Dateien, die verschiedene Arbeitslasten, ohne dass separate Datenträgerpartitionen enthalten.

-   Verwenden von Windows Deployment Services (WDS) für die netzwerkbereitstellung von Abbildern auf die Zielcomputer für den systemeigenen Start.

-   Verwalten von Desktopimage-Bereitstellung.

## <a name="span-idbkmkrequirementsspanspan-idbkmkrequirementsspanspan-idbkmkrequirementsspanrequirements"></a><span id="BKMK_requirements"></span><span id="bkmk_requirements"></span><span id="BKMK_REQUIREMENTS"></span>Anforderungen


Systemeigene Start virtueller Festplatten gelten die folgenden Abhängigkeiten:

-   Die lokale Festplatte benötigen Sie mindestens zwei Partitionen: eine Systempartition mit dem Windows 8 Boot-Umgebung Dateien und Speicher (Boot Configuration Data, BCD) und eine Partition VHD-Datei zu speichern. Das VHD-Format wird für den systemeigenen Start auf einem Computer mit einer Windows® 7 Boot-Umgebung unterstützt, jedoch müssen Sie die Systempartition zu einer Windows 8-Umgebung verwenden Sie das .vhdx-Dateiformat zu aktualisieren. Weitere Informationen zum Hinzufügen einer Windows 8 Boot-Umgebung für systemeigene Start virtueller Festplatten finden Sie unter [herunterladen und Installieren von Windows PE (Windows PE), damit Sie starten können von einem USB-Laufwerk oder eine externe USB-Festplatte](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md).

-   Die lokalen Datenträger-Partition, die VHD-Datei enthält, muss genügend freier Speicherplatz für das Erweitern einer dynamischen virtuellen Festplatte auf die maximale Größe und die Auslagerungsdatei beim Starten der virtuellen Festplatte erstellt haben. Die Seitendatei ist außerhalb der VHD-Datei anders als bei einem virtuellen Computer erstellt, in dem die Seitendatei innerhalb der virtuellen Festplatte enthalten ist.

## <a name="span-idbkmkbenefitsspanspan-idbkmkbenefitsspanspan-idbkmkbenefitsspanbenefits"></a><span id="BKMK_benefits"></span><span id="bkmk_benefits"></span><span id="BKMK_BENEFITS"></span>Vorteile


Die folgenden: Vorteile der Funktionen für VHDs systemeigenen Start

-   Verwenden die gleiche Bild-Verwaltungstools für erstellen, bereitstellen und Verwalten von Systemabbilder für die designierte Hardware oder auf einem virtuellen Computer installiert werden soll.

-   Eine Grafik auf einem virtuellen Computer oder einem bestimmten Computer, je nach kapazitätsplanung und Verfügbarkeit bereitstellen.

-   Bereitstellen von Windows für Szenarien mit mehreren Boot ohne separate Datenträgerpartitionen.

-   Bereitstellen von unterstützt Windows Bilder in eine virtuelle Festplatte Containerdatei für schnellere Bereitstellung von wiederverwendbaren Entwicklung und testumgebungen.

-   Ersetzen von Abbildern für Server für die erneute Bereitstellung oder Wiederherstellung.

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>Einschränkungen


Systemeigene Unterstützung von VHD weist die folgenden Nachteile:

-   Systemeigene Unterstützung für VHD Datenträger Management kann ungefähr 512 VHD-Dateien gleichzeitig anfügen.

-   Systemeigene Start virtueller Festplatten unterstützt keine Ruhezustand des Systems Energiesparmodus wird zwar unterstützt.

-   VHD-Dateien können nicht geschachtelt werden.

-   Systemeigene Start virtueller Festplatten wird über Server Message Block (SMB) Freigaben nicht unterstützt.

-   Windows BitLocker Drive Encryption kann nicht verwendet werden, die für den einbindungspunkt verschlüsselt, die VHD-Dateien enthält, die für systemeigene Start virtueller Festplatten verwendet werden, und BitLocker nicht verwendet werden, auf Volumes, die innerhalb einer virtuellen Festplatte enthalten sind.

-   Die übergeordnete Partition einer VHD-Datei kann nicht Teil einer Momentaufnahme des Volumes sein.

-   Eine angefügte VHD-DATEI kann nicht als *dynamische Datenträger*konfiguriert werden. Eine dynamische Festplatte bietet Features, die Basisdatenträger keine wie die Möglichkeit zum Erstellen von Volumes, die mehrere Datenträger (übergreifende und Stripeset Volumes) umfassen und die Möglichkeit, fehlertolerante Datenträger (gespiegelte und RAID-5-Volumes) erstellen. Alle Volumes auf dynamischen Datenträgern werden als dynamische Volumes bezeichnet.

-   Das übergeordnete Volume der virtuellen Festplatte kann nicht als dynamische Datenträger konfiguriert werden.

## <a name="span-idbkmkrecommendationsspanspan-idbkmkrecommendationsspanspan-idbkmkrecommendationsspanrecommended-precautions"></a><span id="BKMK_recommendations"></span><span id="bkmk_recommendations"></span><span id="BKMK_RECOMMENDATIONS"></span>Empfohlene Vorsichtsmaßnahmen


Die folgenden werden Maßnahmen ergreifen, für die Verwendung von virtuellen Festplatten mit systemeigenem Start empfohlen:

-   Verwenden Sie feste Virtuelle Datenträgertypen für Produktionsserver, steigern der Leistung und Schützen von Benutzerdaten. Verwenden Sie dynamische oder Differenzierung VHD Datenträgertypen nur in testumgebungen, wie beispielsweise zum Entwickeln und testen.

-   Bei Verwendung von dynamischen VHDs Datenspeicher kritische Anwendung oder Benutzer auf Datenträgerpartitionen, die außerhalb der VHD-Datei sind, wenn es möglich ist. Dies reduziert die Größe-Anforderungen der virtuellen Festplatte. Es erleichtert auch Anwendung oder Benutzer Daten wiederherstellen, wenn das Bild VHD nicht mehr aufgrund eines schwerwiegenden Herunterfahren wie eines Stromausfalls verwendet werden kann.

## <a name="span-idbkmktypesofvhdsspanspan-idbkmktypesofvhdsspanspan-idbkmktypesofvhdsspantypes-of-virtual-hard-disks"></a><span id="BKMK_typesOfVHDs"></span><span id="bkmk_typesofvhds"></span><span id="BKMK_TYPESOFVHDS"></span>Typen von virtuellen Festplatten


Drei Arten von VHD-Dateien können mithilfe der Tools für die Verwaltung von Datenträgern erstellt werden:

-   **Feste Festplattenabbild.** Eine feste Festplattenabbild ist eine Datei, die die Größe des virtuellen Datenträgers zugewiesen wird. Beispielsweise, wenn Sie eine virtuelle Festplatte erstellen, die 2 Gigabyte (GB) ist, wird das System einen Host-Datei ungefähr 2 GB Größe erstellen. Feste Festplatte Bilder werden empfohlen, für den Produktionsservern und Arbeiten mit Kundendaten.

-   **Dynamische Festplattenabbild.** Ein dynamisches Festplattenabbild ist eine Datei, die so groß wie den tatsächlichen Daten zu einem bestimmten Zeitpunkt geschrieben ist. Weitere Daten geschrieben werden, erhöht sich die Datei dynamisch Größe. Beispielsweise ist die Größe einer Datei sichern eine virtuelle Festplatte 2 GB anfänglich rund 2 Megabyte (MB) auf dem Hostsystem-Datei. Wenn Daten in dieses Bild geschrieben werden, nimmt es mit einer maximalen Größe von 2 GB.

    Dynamische Festplatte Bilder werden bei Entwicklung und testing empfohlen. Dynamische VHD-Dateien sind kleiner, einfacher zu kopieren und werden erweitert, sobald Sie bereitgestellt.

-   **Differenzierung Festplattenabbild.** Ein Versionsvergleich Festplattenabbild zum Beschreiben der Änderung eines übergeordneten Abbilds. Diese Art von Festplattenabbild ist nicht unabhängig; Es hängt ein anderes Festplattenabbild voll funktionsfähig sein. Die weiter oben erwähnt Festplattenabbild-Typen, einschließlich einer anderen Versionsvergleich Festplattenabbild möglich das übergeordneten Festplattenabbild.

## <a name="span-idbkmktechnologiesspanspan-idbkmktechnologiesspanspan-idbkmktechnologiesspantechnologies-related-to-vhds-with-native-boot"></a><span id="BKMK_technologies"></span><span id="bkmk_technologies"></span><span id="BKMK_TECHNOLOGIES"></span>Im Zusammenhang mit virtuellen Festplatten mit systemeigenem Start Technologien


Virtuelle Festplatten mit systemeigenem Start verwenden im Allgemeinen die folgenden Technologien:

### <a name="span-idbcdbootspanspan-idbcdbootspanspan-idbcdbootspanbcdboot"></a><span id="BCDboot"></span><span id="bcdboot"></span><span id="BCDBOOT"></span>BCDboot

BCDboot-Tool wird zum Initialisieren des BCD-Speichers und Boot-Umgebung Dateien auf der Systempartition während der Bereitstellung Bild kopiert. BCD-Dateien beschreiben Boot-Anwendungen und Anwendungseinstellungen zu starten. Die Objekte und Elemente im Speicher ersetzen Sie die Datei Boot.ini effektiv. Bei der Installation einer VHD systemeigenem Start auf designierte Hardware müssen Sie möglicherweise auf einem Windows 8 BCD-Speicher zu aktualisieren. Weitere Informationen zum BCDboot-Tool finden Sie unter [BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md).

### <a name="span-idbcdeditspanspan-idbcdeditspanspan-idbcdeditspanbcdedit"></a><span id="BCDedit"></span><span id="bcdedit"></span><span id="BCDEDIT"></span>BCDedit

BCDedit ist ein Befehlszeilentool zum Verwalten von BCD-Speichern. Sie können für verschiedene Zwecke wie Erstellen neuer Speicher, Ändern vorhandener Speicher und Hinzufügen von Boot-Menü-Parameter verwendet werden. Weitere Informationen über das Tool BCDedit finden Sie unter [diese Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=128459).

### <a name="span-iddiskpartspanspan-iddiskpartspanspan-iddiskpartspandiskpart"></a><span id="DiskPart"></span><span id="diskpart"></span><span id="DISKPART"></span>DiskPart

DiskPart ist ein Befehlszeilentool unter Windows, die Sie Objekte wie Festplatten, Partitionen oder Volumes, mithilfe von Skripts oder an der Befehlszeile verwalten können. In Windows 8 kann das DiskPart-Tool zum Erstellen, Partition, und fügen Sie VHDs verwendet werden. Weitere Informationen zum DiskPart-Tool finden Sie unter [diese Website von Microsoft](http://go.microsoft.com/fwlink/?LinkId=128458).

### <a name="span-idwindowsdeploymentservicesspanspan-idwindowsdeploymentservicesspanspan-idwindowsdeploymentservicesspanwindows-deployment-services"></a><span id="Windows_Deployment_Services_"></span><span id="windows_deployment_services_"></span><span id="WINDOWS_DEPLOYMENT_SERVICES_"></span>Windows-Bereitstellungsdienste

Windows-Bereitstellungsdienste ist ein Netzwerk-basierte Installation-Server, der ermöglicht es Unternehmen, Remote zu verwalten und die neuesten Betriebssysteme mithilfe von Windows PE und Windows-Bereitstellungsdienst-Server bereitstellen. Windows-Bereitstellungsdienste unterstützt die Bereitstellung von Abbilddateien für virtuelle Festplatten zusätzlich zu WIM-Dateien. Verwenden von Windows-Bereitstellungsdienste automatisiert die netzwerkbereitstellung von Abbildern für den systemeigenen Start. Windows-Bereitstellungsdienste verarbeitet VHD-Abbilds auf einer lokalen Partition kopieren möchten, und Konfigurieren der lokalen Startkonfigurationsdaten für den systemeigenen Start von der virtuellen Festplatte.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)](deploy-windows-on-a-vhd--native-boot.md)

[Starten Sie VHD (systemeigenem Start): Hinzufügen einer virtuellen Festplatte zum Startmenü](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[Herunterladen und Installieren von Windows PE (Windows PE), damit Sie von einem USB-Laufwerk oder eine externe USB-Festplatte gestartet werden kann](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)

 

 






