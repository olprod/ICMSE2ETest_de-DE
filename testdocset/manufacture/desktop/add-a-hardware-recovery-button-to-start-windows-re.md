---
author: Justinha
Description: "Auf UEFI-basierte Computer können Sie eine Hardware konfigurieren Wiederherstellung Schaltfläche (oder Schaltflächenkombination) zum Starten des Windows RE, einschließlich Drucktaste zurücksetzen Features für Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen)."
ms.assetid: d7edf215-ced0-4052-a442-08a6c19e6078
MSHAttr: PreferredLib:/library/windows/hardware
title: "Fügen Sie eine Recovery-Taste zum Starten des Windows RE hinzu"
ms.openlocfilehash: eb76e6462d650abb16f96caa7ed00a27f120791d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-hardware-recovery-button-to-start-windows-re"></a>Fügen Sie eine Recovery-Taste, um Windows NEU zu starten


Auf UEFI-basierte Computer können Sie eine Hardware konfigurieren Wiederherstellung Schaltfläche (oder Schaltflächenkombination) zum Starten des Windows RE, einschließlich Drucktaste zurücksetzen Features für Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen). Dadurch können Benutzer die Windows RE-Menüs leichter zu erhalten.

Relative Windows 8/8.1 wurde die empfohlene Implementierung in Windows 10 für solche Tasten erheblich vereinfacht. Sie müssen nicht mehr Windows-Startdateien einer nicht verwalteten Position auf die EFI-Systempartition (ESP) zum Erstellen eines sekundären Boot Pfads zu kopieren. Stattdessen Windows konfiguriert und verwaltet alle auf dem Datenträger Ressourcen zur Unterstützung der Schaltflächen Hardware erforderlich. Der Entwurf kann wie folgt zusammengefasst werden:

1.  Windows 10 erstellt automatisch einen sekundären Speicher (Boot Configuration Data, BCD) im Ordner \\EFI\\Microsoft\\Wiederherstellung.

    Wenn Windows RE installiert ist, wird dieser sekundären Startkonfigurationsdaten standardmäßig automatisch mit den entsprechenden Einstellungen für den Start von Windows RE aufgefüllt.

    Wenn Sie der Speicherort des Windows RE (beispielsweise aufgrund von zukünftige Updates) geändert wird, wird die sekundäre Startkonfigurationsdaten automatisch aktualisiert.

2.  Sie benötigen weiterhin einen statischen Boot Gerät-Eintrag für die Wiederherstellung am Ende der Liste UEFI Firmware Boot Reihenfolge zu erstellen.

    Sollte dieser Eintrag der Boot-Gerät zeigen Sie auf der standardmäßigen Windows-Start-Manager (bootmgfw.efi) im Ordner \\EFI\\Microsoft\\Boot auf die ESP.

    Der Boot-Eintrag Gerät muss angeben, die `/RecoveryBCD` Parameter.

    Wenn die Hardware-Schaltfläche ausgelöst wird, sollte der Wiederherstellung Boot-Gerät Eintrag automatisch ausgewählt.

    Finden Sie weitere Informationen finden Sie unter des Geräteherstellers Anweisungen zum Ändern der UEFI-Firmware auf dem Gerät.

3.  Beim Windows-Start-Manager starten wird mit der `/RecoveryBCD` -Parameter verwendet sekundäre Startkonfigurationsdaten die zum Starten von Windows-RE anstelle des Standard-Informationsspeichers BCD konfiguriert ist.

Das folgende Diagramm veranschaulicht die empfohlene Implementierung und die verschiedenen Startpfade:

![Diagramm zum Programmkompatibilitäts-Prozess zum Firmware Schaltfläche hinzufügen](images/dep-winre-hardwarebuttonoverview.png)

## <a name="span-iddesignrecommendationsforthehardwarebuttonspanspan-iddesignrecommendationsforthehardwarebuttonspanspan-iddesignrecommendationsforthehardwarebuttonspandesign-recommendations-for-the-hardware-button"></a><span id="Design_recommendations_for_the_hardware_button_"></span><span id="design_recommendations_for_the_hardware_button_"></span><span id="DESIGN_RECOMMENDATIONS_FOR_THE_HARDWARE_BUTTON_"></span>Entwurfsempfehlungen für Websites für die Schaltfläche Hardware:


Die Hardware Recovery Schaltfläche (oder Tastenkombination) sollte, auch wenn der PC ausgeschaltet ist verwendet werden. Beim Auslösen, sollte der PC-Option schalten und der sekundären Startpfad durchlaufen. Dadurch entfällt die Notwendigkeit für Benutzer die Schaltfläche in einem Fenster sehr kurzfristig während und nach POST drücken.

Für PCs die Firmware Optionsmenü unterstützen, sollte die Schaltfläche (oder Tastenkombination) auslösen zuerst ein einfaches Menü angezeigt werden, das Benutzer die Optionen entweder Boot Windows RE oder das Optionsmenü Firmware eingeben können. Dadurch wird die Notwendigkeit, mehrere Tastenkombinationen unterstützen entfernt.

**Hinweis**  Die Taste ist nicht möglich, starten den PC Windows RE bis Windows RE installiert ist. Im Allgemeinen bedeutet dies nach der PC des Konfigurationsdurchgangs abgeschlossen wurde.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellen von Windows RE](deploy-windows-re.md)

 

 






