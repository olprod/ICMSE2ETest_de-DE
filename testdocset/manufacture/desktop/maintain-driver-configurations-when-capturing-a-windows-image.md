---
author: Justinha
Description: Verwalten Sie Treiberkonfigurationen, wenn Sie ein Windows-Abbild aufzeichnen
ms.assetid: 4712b33a-c6ab-4715-ba55-041c0c6fa2b1
MSHAttr: PreferredLib:/library/windows/hardware
title: Verwalten Sie Treiberkonfigurationen, wenn Sie ein Windows-Abbild aufzeichnen
ms.openlocfilehash: 10c8b4058cb7056104944ec4d68fd679bf865533
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="maintain-driver-configurations-when-capturing-a-windows-image"></a>Verwalten Sie Treiberkonfigurationen, wenn Sie ein Windows-Abbild aufzeichnen


Bereitstellung häufig wird ein einzelnes Windows-Bild aus einem Referenzcomputer erfassen und anschließend das Bild für eine Gruppe von Zielcomputern, die identischer Hardwarekonfiguration anwenden.

Windows Setup verwalten die Treiberkonfigurationen aus des Referenzcomputers als Teil des Windows-Abbilds können anweisen, während der Installation Zeit sparendes und, um die Out-of-Box-Experience (OOBE) für Endbenutzer zu beschleunigen. Nur, wenn die Hardware des Referenzcomputers und der Hardware auf den Zielcomputern identisch sind, sollten diese Schritte durchführen. Wenn Sie dies tun, verwaltet Windows Setup Treiberkonfigurationen während der abbildaufzeichnung und Bereitstellung.

In diesem Thema:

-   [Weisen Sie Windows-Setup Treiberkonfigurationen verwalten](#bkmk-1)
-   [Übersicht über die](#bkmk-2)
-   [Bewährte Methoden für die Treiber Überarbeitungen und Treiber Rangfolge](#bkmk-3)
-   [Problembehandlung bei unterschiedlichen Hardware-Konfigurationen](#bkmk-4)
-   [Problembehandlung bei Treiberkonflikte](#bkmk-5)

## <a name="span-idbkmk1spanspan-idbkmk1spaninstructing-windows-setup-to-maintain-driver-configurations"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Windows-Setup zum Aufrechterhalten der Treiberkonfigurationen angewiesen


Bevor Sie ein Bild zu erfassen, Verallgemeinern des Computers mithilfe einer Antwortdatei, mit der Windows-Setup die Treiberkonfigurationen verwalten angewiesen.

**Treiberkonfigurationen mithilfe einer Antwortdatei verwalten**

1.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**und wählen Sie dann **Windows System Image Manager**.
2.  Erstellen einer neuen Antwortdatei oder Aktualisieren einer vorhandenen Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085) und [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073).
3.  Hinzufügen der Microsoft Windows-PnpSysprep /**PersistAllDeviceInstalls** festlegen. Weitere Informationen finden Sie im Abschnitt " [Übersicht](#bkmk-2) " in diesem Thema.
4.  Wenn der Computer nicht erkannt Hardware verfügt, umfassen die Microsoft-Windows-PnpSysprep /**DoNotCleanUpNonPresentDevices** festlegen. Weitere Informationen finden Sie im Abschnitt [nicht erkannt Hardware](#undetectablehardware) in diesem Thema.
5.  Verallgemeinern Sie die Antwortdatei mit den Computer. Beispiel:

    ``` syntax
    Sysprep /generalize /unattend:C:\unattend.xml
    ```

## <a name="span-idbkmk2spanspan-idbkmk2spanoverview"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Übersicht über die


Die Windows-Box-Treiber-Pakete enthalten Gerätetreibern, die ein breites Spektrum an häufig verwendete Hardware zu unterstützen. Wenn Ihre spezifische Hardware zusätzliche Gerätetreiber starten erforderlich sind, können Sie zusätzliche Gerätetreiber auf Ihrem Windows-Abbild vorinstallieren. Unabhängige Hardwareanbieter (unabhängigen Hardwareanbietern) angeben oft zusammen mit ihren Gerätehardware diese zusätzliche Gerätetreiber. Weitere Informationen zum Hinzufügen von Gerätetreibern finden Sie unter [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md).

Um ein Windows-Abbild für die Bereitstellung auf mehreren Computern vorzubereiten, müssen Sie das System Vorbereitungstool (Sysprep) an das Windows-Abbild verallgemeinern verwenden. Ein Windows-Abbild verallgemeinern entfernt die computerspezifischen Informationen und bereitet die Gerätetreiber für den ersten Start. Diese Vorbereitung umfasst die folgenden Schritte:

-   Gerätestatus für Hardware wurde entfernt.

-   Treiber erforderliche Einstellungen werden auf ihre Standardwerte zurückgesetzt.

-   Geräteprotokolldateien werden gelöscht.

Wenn Sie den Computer verallgemeinern, verwenden Sie eine Antwortdatei, die die Microsoft Windows-PnpSysPrep hat\\**PersistAllDeviceInstalls** -Einstellung, um Zeit zu sparen. Diese Einstellung wird verhindert, dass Windows-Setup aus entfernen und Neukonfigurieren der Gerätestatus für identische Hardware. Beim ersten Start sind die erkannten Gerätetreiber bereits vorkonfiguriert potenziell eine schnellere ersten Starten zu aktivieren.

**Wichtige**  
Vermeiden der Verwendung von Einstellung **PersistAllDeviceInstalls** , wenn die Hardware und der Hardware-Konfiguration auf dem Referenzcomputer nicht auf diejenigen der Zielcomputer identisch sind. Geringfügige Unterschiede bei der Hardware oder Hardwarekonfiguration können auch scheinbar erheblich oder Probleme übersehen. Weitere Informationen finden Sie unter der [Konfiguration Unterschiede bei der Problembehandlung Hardware](#bkmk-4) Abschnitt dieses Themas.

 

Es empfiehlt sich nicht für die Einstellung **PersistAllDeviceInstalls** auf dem Bild primäre Referenz zu verwenden. Laden Sie stattdessen für jede Gruppe von Computern, die eine anderen Hardwarekonfiguration verfügen, zuerst das primäre Referenzabbild auf einem neuen Referenzcomputer, der die geplanten Hardwarekonfiguration verfügt. Im nächsten Schritt erfassen Sie ein neues Abbild von Setup und verwenden Sie Einstellung **PersistAllDeviceInstalls** .

Weitere Informationen dazu, wie Sie das Windows-Abbild verallgemeinern finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

## <a name="span-idbkmk3spanspan-idbkmk3spanbest-practices-for-driver-revisions-and-driver-ranking"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>Bewährte Methoden für die Treiber Überarbeitungen und Treiber Rangfolge


Verwalten Sie nicht mehrere Versionen oder Überarbeitungen des gleichen Treiberpakets in demselben Bild. Verwenden Sie offline- oder Onlinemodus Wartung Tools Treiber aktualisieren.

In der Regel bestimmt Setup beim Setup Windows einen Computer startet und mehrerer Versionen eines Treiberpakets auf diesem Computer vorhanden, welcher Treiber zu installieren, indem Sie mit der Treiber Rangfolge. Aber bei Verwendung die Einstellung **PersistAllDeviceInstalls** nicht normalen Vorgängen auf Treiber Rangfolge auftreten. Geräte, die veraltete Treiber verwenden können also installiert bleiben. Weitere Informationen zu Treiber ranking finden Sie unter [Wie Windows Rang Treiber](http://go.microsoft.com/fwlink/?LinkId=91227) auf MSDN.

Wenn Sie einen Gerätetreiber zu einem Bild, die die Einstellung der **PersistAllDeviceInstalls** verwendet hinzufügen müssen, können Sie Ihre Gerätetreiber mithilfe einer der folgenden Methoden aktualisieren:

-   Verwenden Sie offline Wartung Tools, wie das Tool Deployment Image Servicing and Management (DISM) oder einer Antwortdatei ein. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Treiber eine Offline-Windows-Abbild](add-and-remove-drivers-to-an-offline-windows-image.md).

-   Verwenden Sie online Wartung Methoden oder Tools, wie einer Antwortdatei ein. Weitere Informationen finden Sie unter [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md).

## <a name="span-idbkmk4spanspan-idbkmk4spantroubleshooting-hardware-configuration-differences"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Problembehandlung bei unterschiedlichen Hardware-Konfigurationen


Für die Einstellung **PersistAllDeviceInstalls** ordnungsgemäß funktioniert, muss die Hardwarekonfiguration des Referenzcomputers und auf den Zielcomputern identisch sein. Hardwarekonfiguration umfasst die folgenden Komponenten:

-   **Hardware Hersteller und Modell.**

-   **Firmware.** Updates, Überarbeitungen und Unterschiede bei der Konfiguration können dazu führen, dass einige Geräte Bericht verschiedene Kriterien für übereinstimmende Gerätetreiber oder andere Ressourcen zu verwenden. Beispiel:

    -   Periphere Component Interconnect PCI-basierten Geräten können verschiedene Subsystem-Revisionsnummern in ihre gemeldeten Hardware-IDs einbetten.

    -   BIOS-Versionen können den Namespace Advanced Configuration and Power Interface (ACPI) zu ändern. Daraufhin wird Windows Setup vorhandene Geräten unterschiedlich Unwichtigstes oder vorhandene Geräte als neue Geräte einführen.

    -   BIOS-System Konfigurationsunterschiede können dazu führen, dass unterschiedliche Speicher-, e/a, direkter Speicherzugriff (DMA) Forderung Systemgeräte oder unterbrechen Anforderung (IRQ) Ressourcen.

-   **Physischen Standort.** Hardwarekonfigurationen müssen die gleichen Steckplatz, Port oder Socket Zahlen Verbindung mit externen Geräten verwenden. Beispiel:

    -   PCI-Erweiterungskarten müssen in den gleichen Steckplatz Zahlen eingefügt werden.

    -   USB-Geräte müssen verbunden sein oder mit der gleichen Portnummern auf die gleiche USB-Hostcontroller verkabelt und Hubs integriert.

    -   Speichergeräten müssen mit der gleichen Speichercontroller und Kanäle verbunden sein.

### <a name="span-idtypesofhardwarelikelytocauseproblemsspanspan-idtypesofhardwarelikelytocauseproblemsspanspan-idtypesofhardwarelikelytocauseproblemsspanlow-risk-medium-risk-and-high-risk-differences-in-hardware-configuration"></a><span id="TypesOfHardwareLikelyToCauseProblems"></span><span id="typesofhardwarelikelytocauseproblems"></span><span id="TYPESOFHARDWARELIKELYTOCAUSEPROBLEMS"></span>Sorgt, Mittel-Risiken und hohem Unterschiede bei der Hardwarekonfiguration

Wenn Sie die Einstellung **PersistAllDeviceInstalls** verwenden, können alle Hardwareunterschiede potenziell Probleme auftreten. Jedoch einige Unterschiede eher als andere Probleme.

### <a name="span-idlow-riskdifferencesspanspan-idlow-riskdifferencesspanspan-idlow-riskdifferencesspanlow-risk-differences"></a><span id="Low-risk_differences"></span><span id="low-risk_differences"></span><span id="LOW-RISK_DIFFERENCES"></span>Sorgt Unterschiede

Für die folgenden Typen von Hardwareunterschieden können Sie möglicherweise Treiberkonflikte umgehen und Einstellung **PersistAllDeviceInstalls** weiterhin zu verwenden:

-   Taktfrequenz der CPU

-   Größe des Arbeitsspeichers

-   Datenträgerkapazität

-   Externe Eingabegeräte, wie Tastaturen und

-   Monitore

### <a name="span-idmedium-riskdifferencesspanspan-idmedium-riskdifferencesspanspan-idmedium-riskdifferencesspanmedium-risk-differences"></a><span id="Medium-risk_differences"></span><span id="medium-risk_differences"></span><span id="MEDIUM-RISK_DIFFERENCES"></span>Unterschiede bei der mittleren-Risiko

Die folgenden Typen von Hardwareunterschieden wird empfohlen, dass Sie nicht die Einstellung **PersistAllDeviceInstalls** verwenden:

-   Grafikkarten

-   Speicher Laufwerke und Medien Leser wie optische Laufwerke und Kartenleser

-   Interne oder integrierte Busgeräte wie USB oder IEEE 1394-Geräte

Wenn diese Typen von Hardwareunterschieden vorhanden sind, kann mit dieser Einstellung nicht Installationsdauer, reduziert, auch wenn Sie Treiberkonflikte umgehen.

### <a name="span-idhigh-riskdifferencesspanspan-idhigh-riskdifferencesspanspan-idhigh-riskdifferencesspanhigh-risk-differences"></a><span id="High-risk_differences"></span><span id="high-risk_differences"></span><span id="HIGH-RISK_DIFFERENCES"></span>Unterschiede mit hohem Risiko

Für größere Hardware verwenden Unterschiede, Sie nicht die Einstellung **PersistAllDeviceInstalls** . Dazu zählen:

-   Hauptplatine Chipsatz oder CPU Marke

-   Speichercontroller

-   Formfaktor Unterschiede, wie eine Änderung von einem Desktop mit einem Laptop oder aus einem Laptop auf einem desktop

-   Tastatur Layout Unterschiede, wie eine Änderung vom standard 101-Tasten japanische 106-Tasten

-   Alle anderen Geräte, die im Pfad des Windows Enumeration sind Start volume

### <a name="span-idwhattypesofproblemscanoccurspanspan-idwhattypesofproblemscanoccurspanspan-idwhattypesofproblemscanoccurspantypes-of-problems-that-can-occur-with-a-hardware-configuration-change"></a><span id="WhatTypesOfProblemsCanOccur"></span><span id="whattypesofproblemscanoccur"></span><span id="WHATTYPESOFPROBLEMSCANOCCUR"></span>Arten von Problemen, die bei einer Änderung an der Konfiguration Hardware auftreten können

Geringfügige Unterschiede bei der Hardware oder Hardwarekonfiguration können auch scheinbar erheblich oder übersehen Probleme wie den folgenden:

-   Systemstabilität

-   Verwenden Sie einige einfache oder erweiterte Funktionen eines Geräts nicht möglich

-   Erweiterte Installationszeiten und erweiterte Boot-Zeiten

-   Falsch geschriebenen Geräte in den Ordner Geräte und Drucker, Geräte-Manager und andere Gerät im Zusammenhang mit der Schnittstellen

-   Schwerwiegende Probleme, die den Computer in einer nicht startbaren Zustand hinterlassen

### <a name="span-idbootcriticaldriverpackagesspanspan-idbootcriticaldriverpackagesspanspan-idbootcriticaldriverpackagesspanhardware-configuration-differences-that-can-cause-system-boot-failures"></a><span id="BootCriticalDriverPackages"></span><span id="bootcriticaldriverpackages"></span><span id="BOOTCRITICALDRIVERPACKAGES"></span>Die unterschiedlichen Konfigurationen Hardware, die System Boot-Fehlern führen können

Wenn die erforderliche Hardware nicht auf dem Referenzcomputer und den Zielcomputern identisch ist, kann unter Verwendung der Einstellung **PersistAllDeviceInstalls** erheblich System beeinträchtigen, die den Computer in einer nicht startbaren Zustand hinterlassen können.

Erforderliche Treiberpakete können gehören zu einer der folgenden Windows-Gerät Setup Klassen, wie identifizierte ClassGUID Richtlinie in der * &lt;Version&gt; * Abschnitt der INF-Dateien in ihre Treiberpakete.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Gerät vom System generierten Setup-Klasse</th>
<th align="left">ClassGUID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>System</p></td>
<td align="left"><p>{4D36E97D-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>Computer</p></td>
<td align="left"><p>{4D36E966-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Prozessor</p></td>
<td align="left"><p>{50127DC3-0F36-415E-A6CC-4CB3BE910B65}</p></td>
</tr>
<tr class="even">
<td align="left"><p>PCMCIA</p></td>
<td align="left"><p>{4D36E977-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>HDC</p></td>
<td align="left"><p>{4D36E96A-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>SCSIAdapter</p></td>
<td align="left"><p>{4D36E97B-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Laufwerk</p></td>
<td align="left"><p>{4D36E967-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>CD-ROM-</p></td>
<td align="left"><p>{4D36E965-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>FDC</p></td>
<td align="left"><p>{4D36E969-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>FloppyDisk</p></td>
<td align="left"><p>{4D36E980-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Band</p></td>
<td align="left"><p>{71A27CDD-812A-11D0-BEC7-08002BE2092F}</p></td>
</tr>
<tr class="even">
<td align="left"><p>USB</p></td>
<td align="left"><p>{36FC9E60-C465-11CF-8056-444553540000}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SBP2</p></td>
<td align="left"><p>{D48179BE-EC20-11D1-B6B8-00C04FA372A7}</p></td>
</tr>
<tr class="even">
<td align="left"><p>1394</p></td>
<td align="left"><p>{6BDD1FC1-810F-11D0-BEC7-08002BE2092F}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Enum1394</p></td>
<td align="left"><p>{C459DF55-DB08-11D1-B009-00A0C9081FF6}</p></td>
</tr>
<tr class="even">
<td align="left"><p>Keyboard</p></td>
<td align="left"><p>{4D36E96B-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Maus</p></td>
<td align="left"><p>{4D36E96F-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>HIDClass</p></td>
<td align="left"><p>{745A17A0-74D3-11D0-B6FE-00A0C90F57DA}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Ports</p></td>
<td align="left"><p>{4D36E978-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen zu diesen Gerät Setupklassen finden Sie unter [System-Supplied Gerät Setupklassen](http://go.microsoft.com/fwlink/?LinkId=237677) auf MSDN.

### <a name="span-idundetectablehardwarespanspan-idundetectablehardwarespanspan-idundetectablehardwarespanundetectable-hardware"></a><span id="UndetectableHardware"></span><span id="undetectablehardware"></span><span id="UNDETECTABLEHARDWARE"></span>Hardware nicht erkannt

Wenn Sie einen neuen Computer an einen Endbenutzer bereitstellen, einige Hardware, wie ein austauschbares Gerät oder ein Gerät, das einen ein-/ausschalten-Switch vorhanden oder erkannte beim ersten Start möglicherweise nicht. Windows Setup entfernt standardmäßig beim ersten Start der vorkonfigurierten Gerätestatus für erkanntes Hardware.

Hardware bereitstellen, die nicht vorhanden oder beim ersten Start ermittelte zutreffend Gerätetreiber auf das Bild Verweis hinzufügen, eine Verbindung herstellen oder aktivieren Sie die entsprechenden Geräte so, dass Windows installieren und der Microsoft Windows-PnpSysprep verwenden kann /**DoNotCleanUpNonPresentDevices** festlegen, wenn Sie das Abbild aufzuzeichnen.

**Wichtige**  
Unter Verwendung der Einstellung **DoNotCleanUpNonPresentDevices** kann dazu führen, dass die unnötige Speicherung der überzähligen Gerätestatus und beitragen zu langsamer Start des Servers.

 

## <a name="span-idbkmk5spanspan-idbkmk5spantroubleshooting-driver-conflicts"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>Problembehandlung bei Treiberkonflikte


Um Treiberkonflikte zwischen unabhängigen wichtigen Treiberpakete zu vermeiden, muss unabhängigen Hardwarehersteller sicherstellen, dass jedes Gerätetreiber verschiedenen Dienstnamen, Registrierungsschlüsselwerte und binäre Dateinamen verwendet.

### <a name="span-idexampleofapotentialdriverconflictspanspan-idexampleofapotentialdriverconflictspanspan-idexampleofapotentialdriverconflictspanexample-of-a-potential-driver-conflict"></a><span id="Example_of_a_potential_driver_conflict"></span><span id="example_of_a_potential_driver_conflict"></span><span id="EXAMPLE_OF_A_POTENTIAL_DRIVER_CONFLICT"></span>Beispiel für einen möglichen Treiberkonflikt

Im folgenden Beispiel wird eine fiktive IHV mit dem Namen "Fabrikam" zwei Arten von Speichercontroller erzeugt: StandardController und ExtremeController. Fabrikam wird davon ausgegangen, dass nur ein Typ von Speichercontroller gleichzeitig auf einem bestimmten Computer installiert ist.

Treiberpakets definiert die StandardController und ExtremeController-Konfigurationen, um die gleichen Treiber Dienstname Storctrl verwenden. Der Storctrl-Treiber-Dienst verwendet wird, unterschiedliche Einstellungen, die sich ändern je nachdem, die welche Hardware (StandardController oder ExtremeController) installiert ist. Da StandardController und ExtremeController den gleichen Dienst verwenden, können nicht sie koexistieren.

Dieses Beispiel zeigt den Inhalt des Treibers Paketdatei Storctrl.inf:

``` syntax
[Version]
Signature = "$WINDOWS NT$"
Class = SCSIAdapter
ClassGuid = {4D36E97B-E325-11CE-BFC1-08002BE10318}
...
[Manufacturer]
%Fabrikam% = Fabrikam,NTx86

[Fabrikam.NTx86]
%StandardController% = StandardController_DDInstall,PCI\VEN_ABCD&DEV_0001
%ExtremeController%  = ExtremeController_DDInstall, PCI\VEN_ABCD&DEV_0002

...

[StandardController_DDInstall.Services]
AddService = storctrl,0x00000002,StandardController_ServiceInstall

[StandardController_ServiceInstall]
ServiceType  = 1 ; SERVICE_KERNEL_DRIVER
StartType    = 0 ; SERVICE_BOOT_START
ErrorControl = 1 ; SERVICE_ERROR_NORMAL
ImagePath    = %12%\storctrl.sys
AddReg       = StandardController_ServiceSettings

[StandardController_ServiceSettings]
HKR,Settings,LowPowerMode,0x00010001,1
HKR,Settings,ErrorCorrection,0x00010001,1

...

[ExtremeController_DDInstall.Services]
AddService = storctrl,0x00000002,ExtremeController_ServiceInstall

[ExtremeController_ServiceInstall]
ServiceType  = 1 ; SERVICE_KERNEL_DRIVER
StartType    = 0 ; SERVICE_BOOT_START
ErrorControl = 1 ; SERVICE_ERROR_NORMAL
ImagePath    = %12%\storctrl.sys
AddReg       = ExtremeController_ServiceSettings

[ExtremeController_ServiceSettings]
HKR,Settings,LowPowerMode,0x00010001,0
HKR,Settings,ErrorCorrection,0x00010001,4
...
```

Wenn StandardController auf dem Referenzcomputer ist und seine Einstellungen werden während der abbildaufzeichnung verwaltet, ist der Storctrl Treiberdienst vorkonfiguriert. Wenn ExtremeController auf dem Zielcomputer ist, können Windows verwenden, die vorkonfigurierte Einstellungen und Dateien, die für StandardController gedacht sind. Dadurch können unerwartete Ergebnisse.

Unabhängigen Hardwarehersteller helfen den Konflikt beheben, indem Sie mit einer der folgenden Optionen:

-   Erstellen Sie separater Treiberpakete, die für jede Konfiguration separate INF-Dateien vorhanden sind, und importieren Sie nur das erforderlichen Treiber-Paket in das Windows-Abbild während der Bereitstellung. Beispielsweise Teilen Sie Storctrl.inf in zwei separate INF-Dateien, die eine Version für StandardController und eine Version für ExtremeController und importieren Sie nur das erforderlichen Treiber-Paket in das Windows-Abbild.

<!-- -->

-   Erstellen Sie einen anderen Dienst im Treiberpaket für jede Konfiguration. Geben Sie jeden Dienst einen anderen Namen (beispielsweise Storctrl und Storctrlx), und zeigen Sie auf eine andere binäre Bilddatei (z. B. Storctrl.sys und Storctrlx.sys).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Gerätetreiber und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md)

 

 






