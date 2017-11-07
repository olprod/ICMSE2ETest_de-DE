---
author: Justinha
Description: Starten Sie von einer DVD
ms.assetid: f64eb16b-15b3-4a6d-af68-526a8097edb7
MSHAttr: PreferredLib:/library/windows/hardware
title: Starten Sie von einer DVD
ms.openlocfilehash: 56d22fdebefede6547e5b01aac605bea9ba9c765
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-from-a-dvd"></a>Starten Sie von einer DVD


Die einfachste Möglichkeit zum Installieren von Windows auf neuer Hardware ist direkt über die Windows-Produkt-DVD mithilfe einer Antwortdatei mit dem Namen Autounattend.xml starten. Diese Methode bietet Flexibilität beim Zugriff auf das Netzwerk nicht verfügbar ist oder wenn Sie nur ein paar Computer erstellen. Auf die gleiche Weise können Sie die um anfänglichen Schwelle in einem Image-basierte Bereitstellungsszenario, in der Regel als *master Installation*bekannt zu erstellen.

Mithilfe die Antwortdatei können Sie alle oder einen Teil der Windows-Installation automatisieren. Sie können eine Antwortdatei mithilfe von Windows System Image Manager (Windows SIM) erstellen. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085).

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Eine Antwortdatei auf Wechseldatenträger (CD- oder DVD-ROM) oder ein USB-Laufwerk. Die Antwortdatei muss Autounattend.xml heißen. Die Antwortdatei muss sich im Stammverzeichnis des Mediums.

-   Eine Windows-Produkt-DVD.

**So installieren Sie Windows aus der Windows-Produkt-DVD**

1.  Aktivieren Sie auf dem neuen Computer.

    **Hinweis**  
    In diesem Beispiel wird davon ausgegangen, dass die Festplatte leer ist.

     

2.  Fügen Sie der Windows-Produkt-DVD und das Wechselmedium, die die Antwortdatei auf dem neuen Computer enthält.

    **Hinweis**  
    Wenn Sie ein USB-Flashlaufwerk verwenden, legen Sie das Laufwerk direkt in der primären Satz der USB-Ports für den Computer. Bei einem Desktopcomputer ist dies in der Regel Rückseite des Computers.

     

3.  Neustart des Computers durch Drücken der Tastenkombination STRG + ALT + ENTF. Windows-Setup (Setup.exe) wird automatisch gestartet.

    Standardmäßig durchsucht Windows Setup im Stamm von Laufwerk und andere Orte, wie Wechselmedium für eine Antwortdatei mit dem Namen Autounattend.xml. Dies tritt auf, auch wenn Sie nicht explizit eine Antwortdatei angeben. Weitere Informationen finden Sie unter "Implizit suchen für eine Antwortdatei" und "Implizite Antwort Reihenfolge Suche nach" in [Windows Setup Automation Overview](windows-setup-automation-overview.md).

4.  Nach Abschluss des Setup-Programms zu überprüfen, dass alle Anpassungen angewendet, und klicken Sie dann den Computer mithilfe des Befehls **Sysprep** zusammen mit der Option **/ verallgemeinern** reseal aus.

    Das Sysprep-Tool entfernt alle-spezifische Informationen und setzt den Computer. Beim nächsten des Computers starten können Ihre Kunden die Microsoft-Software-Lizenzbedingungen akzeptieren und Hinzufügen von benutzerspezifischen Informationen.

    Optional: Um das Sysprep-Tool automatisch nach der Installation auszuführen, legen Sie Microsoft-Windows-Deployment | Reseal Komponente Einstellung in die Antwortdatei (Autounattend.xml) wie folgt an:

    `ForceShutdownNow = true, Mode =OOBE`

    Optional: Um das Tool Sysprep manuell aus einem ausgeführten Betriebssystem ausführen, geben Sie Folgendes an der Befehlszeile:

    `c:\windows\system32\sysprep /oobe /shutdown`

Weitere Informationen finden Sie unter [Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md).

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Diese exemplarische Vorgehensweise veranschaulicht eine einfache unbeaufsichtigte Installation, die keine Benutzereingaben erforderlich sind. Sie können weitere Anpassungen neu installierten Betriebssystems manuell hinzufügen. Wenn dies ist ein master-Installation oder eine Installation, die Sie für die Image-Bereitstellung verwenden, müssen Sie den Computer herunterzufahren. Klicken Sie dann ein Abbild der Installation mithilfe des Tools Deployment Image Servicing and Management (DISM) oder imaging Software von Drittanbietern.

**Wichtige**  
Sie müssen das Ausführen der **Sysprep / verallgemeinern** Befehl, bevor Sie ein Windows-Abbild auf einen neuen Computer mit welcher Methode verschieben. Diese Methoden umfassen Imaging, Festplattenduplizierung und andere Methoden. Verschieben oder Kopieren eines Windows-Abbilds auf einen anderen Computer ohne Ausführung der **Sysprep / verallgemeinern** Befehl wird nicht unterstützt, auch wenn Sie der neue Computer die gleiche Hardwarekonfiguration hat. Eindeutigen Informationen verallgemeinern das Bild aus der Windows-Installation entfernt werden, sodass Sie das Abbild auf anderen Computern anwenden können.

Beim nächsten Starten des Windows-Abbilds wird die Konfiguration [specialize](specialize.md) Durchlauf ausgeführt. Während dieser Konfigurationsphase Aktionen viele Komponenten, die auftreten muss, wenn Sie ein Windows-Abbild auf einem neuen Computer starten. Weitere Informationen finden Sie unter [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md).

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

[Bereitstellen eines benutzerdefinierten Abbilds](deploy-a-custom-image.md)

[Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md)

 

 






