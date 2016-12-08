---
author: Justinha
Description: Was ist DISM?
ms.assetid: ad08e68c-616f-404a-bfc6-c7bf1a4666f0
MSHAttr: PreferredLib:/library/windows/hardware
title: Was ist DISM?
ms.openlocfilehash: 48ff493c511b89811c6cff3baa33d854a590e9ed
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="what-is-dism"></a>Was ist DISM?


Bereitstellung Bild Wartung und Verwaltung (DISM.exe) ist ein Befehlszeilentool, mit denen service und Vorbereiten von Windows-Bildern, einschließlich derjenigen für [Windows PE](winpe-intro.md), [Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md) und [Windows-Setup](windows-setup-technical-reference.md)verwendet werden kann. DISM kann auf einem Windows-Abbild (WIM) oder eine virtual Hard Disk (VHD- oder .vhdx)-service verwendet werden.

DISM ist verfügbar, über die Befehlszeile oder von Windows PowerShell. Weitere Informationen zum Verwenden von DISM mit PowerShell finden Sie unter [Deployment Imaging – Wartung Management (DISM) Windows PowerShell-Cmdlets](http://go.microsoft.com/fwlink/?LinkId=393917).

Dieses Thema enthält:

-   [Systemanforderungen](#bkmk-reqs)
-   [Vorteile](#bkmk-benefits)
-   [Allgemeine Wartung und Szenarien der Verwaltung](#bkmk-common)
-   [Einschränkungen](#bkmk-limitations)

## <a name="span-idbkmkreqsspanspan-idbkmkreqsspanspan-idbkmkreqsspanimage-requirements"></a><span id="BKMK_reqs"></span><span id="bkmk_reqs"></span><span id="BKMK_REQS"></span>Bild-Anforderungen


DISM kann Mount zu Dienst ein Windows-Abbild aus einer WIM-Datei, VHD-Datei oder eine .vhdx-Datei oder in einigen Fällen verwendet werden um zu ein ausgeführten Betriebssystem zu aktualisieren. Sie können mit älteren Windows-Abbilddateien (WIM-Dateien) verwendet werden. Sie können nicht jedoch mit Windows-Abbilder verwendet werden, die aktueller ist als die installierte Version von Windows Assessment and Deployment Kit (Windows ADK) DISM ausgeliefert werden. DISM wird auch mit den Windows 10, Windows 8-Betriebssystemen und Windows 8.1 installiert.

Eine vollständige technische Beschreibung von WIM finden Sie unter [Whitepaper Windows Imaging File Format (WIM)](http://go.microsoft.com/fwlink/?LinkId=92227).

DISM kann zum Warten der folgenden Betriebssysteme verwendet werden:

-   Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen)
-   Windows Server 2016 – Technische Vorschau
-   Windows 8.1
-   Windows 8
-   Windows Server 2012 R2
-   WindowsServer 2012
-   Windows 7
-   Windows Server 2008 R2
-   Windows Server 2008 SP2
-   Windows PE für Windows 10
-   Windows PE 5.0
-   Windows PE 4.0
-   Vorinstallation Windows-Umgebung (Windows PE) 3.0
-   [Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)

**Hinweis**   DISM kann keinem Windows-Abbild einer virtuellen Festplatte auf Windows Vista® mit Service Pack 1 (SP1) oder Windows Server 2008 bereitgestellt werden. Fügen Sie die virtuelle Festplatte mit dem DiskPart-Tool aus, bevor Sie DISM verwenden können, um das Bild zu bedienen. Wenn Sie Abbildern, die mithilfe von DiskPart angefügt wurden Service, die Änderungen werden automatisch mit jedem Vorgang ein Commit ausgeführt und können nicht gelöscht werden.

 

Eine Liste der unterstützten Plattformen und Architekturtypen finden Sie unter [DISM unterstützte Plattformen](dism-supported-platforms.md).

## <a name="span-idbkmkbenefitsspanspan-idbkmkbenefitsspanspan-idbkmkbenefitsspanbenefits"></a><span id="BKMK_benefits"></span><span id="bkmk_benefits"></span><span id="BKMK_BENEFITS"></span>Vorteile


Sie können DISM mit WIM-Dateien zu verwenden:

-   Erfassen und Anwenden von Windows-Abbildern.
-   Anfügen und Bildern in einer WIM-Datei zu löschen.
-   WIM-Dateien in mehreren kleineren Dateien aufgeteilt.

Sie können DISM mit WIM-, .vhdx oder VHD-Dateien zu verwenden:

-   Hinzufügen oder entfernen und Aufzählen von Paketen, Treibern, Sprachen.
-   Aktivieren Sie oder deaktivieren Sie des Windows-Features.
-   Basierend auf den Abschnitt **OfflineServicing** eine Antwortdatei Änderungen übernehmen.
-   Konfigurieren von internationalen Einstellungen.
-   Aktualisieren Sie ein Windows-Abbild auf eine andere Edition.
-   Bereiten Sie eine Windows PE-Abbild.
-   Geben Sie detaillierte Protokolle für die Problembehandlung.
-   Frühere Versionen von Windows wie Windows-Service 8.x, Windows 7, Windows Server 2008 R2, Windows Vista.
-   Alle Plattformen (32-Bit, 64-Bit)-Service.
-   Eine 32-Bit-Bild aus einem 64-Bit-Host-Service und eine 64-Bit-Bild aus einem 32-Bit-Host-service. Weitere Informationen finden Sie im Abschnitt "Einschränkungen" weiter unten in diesem Thema.
-   Stellen Sie ALTER Paket-Manager-Skripts verwenden.

## <a name="span-idbkmkcommonspanspan-idbkmkcommonspanspan-idbkmkcommonspancommon-servicing-and-management-scenarios"></a><span id="BKMK_common"></span><span id="bkmk_common"></span><span id="BKMK_COMMON"></span>Allgemeine Wartung und von Verwaltungsszenarien


Bild Wartung und Verwaltung Lösungen werden in zwei Hauptkategorien unterteilt:

-   Verwalten von Daten oder Informationen in der Windows-Bilds, beispielsweise aufzählen oder Erstellen eines Inventars der Komponenten, Updates, Treiber oder Anwendungen, die in einem Bild enthalten sind, erfassen oder Teilen eines Abbilds, Anfügen oder Löschen von Bildern in einer WIM-Datei oder das Bereitstellen eines Abbilds enthalten.
-   Warten des Abbilds selbst, einschließlich hinzufügen oder Entfernen von Treiberpaketen und Treibern, ändern spracheinstellungen, aktivieren oder Deaktivieren des Windows-Features und Upgraden auf eine höhere Version von Windows.

Es folgen einige häufige Szenarien für Bild Wartung und Verwaltung:

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><strong>Aufgaben</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Erfassen eines Abbilds und als eine WIM-Datei speichern.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Listen Sie alle Bilder in einer WIM-, VHD- oder .vhdx-Datei.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Verwalten Sie mehrere Bilder in einer einzigen WIM-Datei anfügen, entfernen oder Aufzählen von Bilder.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Bereiten Sie eine Windows PE-Abbild.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Informationen zu einem Windows PE-Abbild aufgelistet.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Stellen Sie eine Windows-Abbild.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Liste bestimmte Informationen zu einem Bild, das aus einer Datei WIM-, VHD- oder .vhdx, einschließlich, wo es bereitgestellt ist, den Bereitstellungsstatus und der Index der einzelnen Abbilder in einer WIM-Datei bereitgestellt.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Listen Sie aller Treiber in einem Abbild oder Informationen zu einem bestimmten Treiber auf.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Fügen Sie Out-of-Box oder wichtigen Treiber zur Unterstützung der neuen Hardware hinzu.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Betriebssystem-Updates wie Hotfixes und Windows-Features hinzufügen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hinzufügen oder Entfernen eines Language Packs und internationale Einstellungen konfigurieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Listen Sie alle internationalen Einstellungen und Sprachen in einem Bild.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Problembehandlung über integrierte Status, und klicken Sie mit der Protokollierung.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Verwalten Sie mehrerer Versionen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Listen Sie aller Features in einem Paket oder bestimmte Informationen zu einem Windows-Feature auf.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Überprüfen Sie die Verfügbarkeit einer Windows® Installer.msp-Datei.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Aktualisieren Sie mehrere Windows-Editionen durch ein einzelnes Bild aktualisieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Upgrade auf eine höhere Version von Windows.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Listen Sie aller Windows-Editionen, denen ein Abbild aktualisiert werden kann auf.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Anwenden von Einstellungen in eine Antwortdatei.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Teilen Sie eine große WIM-Datei in mehrere kleinere Dateien auf ausgewählten Medien passen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>Einschränkungen


**Versionskompatibilität.** DISM kann mit Bilder von älteren Windows-Betriebssystemen verwendet werden, jedoch nicht mit der Betriebssysteme, die mehrere Bilder aktueller ist als die installierte Version von Windows ADK welche DISM wird verteilt. DISM aus Windows 10, beispielsweise kann Version 1511 Windows 10, Version 1511 und 1507 aber nicht Version 1607 bedienen. Finden Sie weitere Informationen finden Sie unter [DISM unterstützte Plattformen](dism-supported-platforms.md).

**Remote-Installation.** Installieren von Paketen auf einem Remotecomputer über ein Netzwerk wird nicht unterstützt. Das Windows-Abbild muss auf dem lokalen System vorhanden sein. DISM Pakete auf einer Netzwerkfreigabe zugreifen kann, aber es müssen sie in einem temporären, sofern nicht schreibgeschützte Verzeichnis (ein *Scratch Directory*genannt) kopieren. Es wird empfohlen, dass Sie ein eindeutiges Scratch Verzeichnis auf einem lokalen Laufwerk für jedes Paket verwenden, die Sie installieren. Nach der Installation können den Inhalt des Verzeichnisses Scratch gelöscht werden.

**Antwortdateien.** Wenn Sie eine Antwortdatei (Unattend.xml) für ein Bild angeben, werden nur die angegebenen im **OfflineServicing** Konfiguration Durchgang Einstellungen angewendet. Alle anderen Einstellungen in die Antwortdatei werden ignoriert. Weitere Informationen finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

**Service Packs.** Servicepacks müssen online mit dem eigenständige Windows Installer installiert werden. Weitere Informationen zu Windows Update Standalone Installer finden Sie unter [Beschreibung von Windows Update Standalone Installer in Windows](http://go.microsoft.com/fwlink/?LinkId=90850).

**Verwenden Sie eine Antwortdatei, um Paket Abhängigkeiten sicherzustellen.** Einige Pakete müssen andere Pakete zuerst installiert werden. Aufgrund dieser Anforderung Abhängigkeit sollten Sie eine Antwortdatei verwenden, wenn Sie mehrere Pakete installieren. Durch Anwenden einer Antwortdatei mithilfe von DISM, können mehrere Pakete in der richtigen Reihenfolge installiert werden. Dies ist die bevorzugte Methode zum Installieren von mehreren Paketen.

**Reihenfolge der Installation des Pakets.** Pakete werden in der Reihenfolge installiert, dass sie in der Befehlszeile aufgelistet sind. Im folgenden Beispiel, 1.inf, 2.inf und 3. wird in der Reihenfolge INF-Datei installiert werden, in der in der Befehlszeile aufgeführt sind.

``` syntax
DISM.exe /image:"c:\images\Image1" /Add-Driver /ForceUnsigned /DriverName:"C:\Drivers\1.inf" /DriverName:"C:\Drivers\2.inf" /DriverName:"C:\Drivers\3.inf"
```

**Sie sind dynamisch unterstützten Befehle zum Warten.** Die Befehle und Optionen, die für das Warten eines Abbilds von bedienen welches Windows-Betriebssystem, und ob das Bild ist offline verfügbar sind oder ein aktuell ausgeführtes Betriebssystem.

**Mehrere für die unbeaufsichtigte Installation Dateien werden nicht unterstützt.** Sie können mehrere Treiber oder Pakete in einer Befehlszeile angeben. Mehrere Unattend.xml Antwortdateien werden jedoch nicht unterstützt. In einer Befehlszeile kann nur eine einzige Antwortdatei angegeben werden.

**Mehrere Befehle zum Warten werden nicht unterstützt.** Sie können mehrere Treiber (1.inf, 2.inf) oder Pakete angeben, aber Sie können nicht mehrere Befehle ( **beispielsweise/Add-Driver** **Driver** **oder/Add-Driver** **/add-package/Add-Package**) in der gleichen Befehlszeile angeben.

**Protokollierung in eine Netzwerkfreigabe.** Wenn Sie einen Computer, der nicht mit einer Netzwerkdomäne verbunden ist verwenden, verwenden Sie **net Use** mit Domänenanmeldeinformationen Zugriffsberechtigungen festlegen, bevor Sie den Pfad für das DISM-Protokoll angeben, die auf einer Netzwerkfreigabe gespeichert ist.

**Platzhalter.** Platzhalter werden in DISM-Befehlszeilen nicht unterstützt.

**Installieren Sie ein Language Pack nicht nach einer Aktualisierung.** Wenn Sie ein Update installieren (Hotfix, allgemein verfügbare Version \[GDR\], oder Servicepack \[SP\]) vor der Installation eines Sprachpakets Language-abhängigen Ressourcen enthält, die sprachspezifische Änderungen, die in dem Update enthalten sind, werden nicht übernommen. Installieren Sie Sprachpakete immer vor der Installation von Updates.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Verweis (Deployment Image Servicing and Management)](dism-reference--deployment-image-servicing-and-management.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[Gerätetreibern und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md)

[Language Packs](language-packs-and-windows-deployment.md)

[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

 

 






