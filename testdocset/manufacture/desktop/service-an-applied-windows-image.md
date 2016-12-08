---
author: Justinha
Description: Ein Bild angewendeten Windows-Dienst
ms.assetid: cdf543f7-7810-4ec5-9992-af0f3b6a789f
MSHAttr: PreferredLib:/library/windows/hardware
title: Ein Bild angewendeten Windows-Dienst
ms.openlocfilehash: 8138359ebba3872c401f045bd0ba3bde7cfbb4bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-an-applied-windows-image"></a>Ein Bild angewendeten Windows-Dienst


Windows® WIM-Dateien enthalten ein oder mehrere Volumeabbilder für ein Windows® Betriebssystem. Ein Volume Image stellt die aufgezeichneten Volume- oder eines Windows-Betriebssystems. Wenn Sie auf einem Windows-Abbild neu zu sammeln oder exportieren Sie eine Kopie einer bestimmten WIM-Datei in eine andere WIM-Datei oder fügen Sie ein Volume Image an eine vorhandene WIM-Datei verfügen, können Sie verwenden Sie das Tool Deployment Image Servicing and Management (DISM) das Bild anwenden und service klicken Sie dann das Bild aus, wenn sie angewendet wird. Anschließend können Sie ausstehende online Aktionen zu beheben und Hinzufügen von Anwendungen oder stellen Sie zusätzliche erforderliche Anpassungen vor, um im Überwachungsmodus starten.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen der exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Computer, der auf die neueste Version von Windows Assessment and Deployment Kit (Windows ADK) Tools installiert ist.

-   Bevor Sie ein Windows-Abbild auf einer Festplattenpartition anwenden können, müssen Sie die Festplattenpartitionen auf dem Zielcomputer erstellen. Weitere Informationen finden Sie unter [Festplatten und Partitionen](hard-drives-and-partitions.md).

-   Sie müssen einen Ort zur Verfügung, So fügen sie das Windows-Abbild hinzu master Windows-Abbild (WIM-Datei) und die Language Packs, Treiber oder andere Pakete verfügbar sein.

-   Ein startbare Windows PE-Datenträger. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md) Sie können auch das Bild von einem anderen Betriebssystem auf demselben Computer wie Windows 8 oder Windows 7 mit den neuesten ADK Tools installiert anwenden.

## <a name="span-idproceduresspanspan-idproceduresspanspan-idproceduresspanprocedures"></a><span id="Procedures"></span><span id="procedures"></span><span id="PROCEDURES"></span>Verfahren


### <a name="span-idstep1boottowindowspeandapplythewindowsimagespanspan-idstep1boottowindowspeandapplythewindowsimagespanspan-idstep1boottowindowspeandapplythewindowsimagespanstep-1-boot-to-windows-pe-and-apply-the-windows-image"></a><span id="Step_1__Boot_to_Windows_PE_and_Apply_the_Windows_Image"></span><span id="step_1__boot_to_windows_pe_and_apply_the_windows_image"></span><span id="STEP_1__BOOT_TO_WINDOWS_PE_AND_APPLY_THE_WINDOWS_IMAGE"></span>Schritt 1: Starten Sie Windows PE, und wenden Sie das Windows-Abbild

In diesem Schritt starten Sie Windows PE und ein Windows-Abbild anwenden, sodass es offline gewartet werden kann.

**Anwenden der Schwelle**

1.  Starten Sie auf dem Zielcomputer Windows PE. Weitere Informationen finden Sie unter [Windows PE für Windows 10](winpe-intro.md).

2.  Wenden Sie an einer Eingabeaufforderung das Master-Shape Windows-Abbild mithilfe von DISM ein. Beispiel:

    ``` syntax
    Dism /Apply-Image /ImageFile:C:\test\wim\install.wim /Index:1 /ApplyDir:C:\test\AppliedImages
    ```

    Weitere Informationen zu DISM-Befehlen finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

### <a name="span-idstep2addpackagestothewindowsimagespanspan-idstep2addpackagestothewindowsimagespanspan-idstep2addpackagestothewindowsimagespanstep-2-add-packages-to-the-windows-image"></a><span id="Step_2__Add_Packages_to_the_Windows_Image"></span><span id="step_2__add_packages_to_the_windows_image"></span><span id="STEP_2__ADD_PACKAGES_TO_THE_WINDOWS_IMAGE"></span>Schritt 2: Hinzufügen von Paketen an das Windows-Abbild

Mithilfe von DISM Pakete das Master-Shape Windows-Abbild hinzufügen.

**So fügen Sie ein Paket auf das Bild hinzu**

1.  Führen Sie an einer Eingabeaufforderung DISM mit der **Option/Add-Package aus** , und zeigen Sie auf die CAB-Dateien oder MSU-Paket, das Sie das Windows-Abbild hinzufügen möchten. Mehrere Pakete können in einer Befehlszeile hinzugefügt werden. Geben Sie beispielsweise den folgenden Befehl zum Hinzufügen mehrere Pakete ein:

    ``` syntax
    Dism /Image:C:\test\AppliedImages /Add-Package /PackagePath:C:\Test\Packages\package1.cab /PackagePath:C:\Test\Packages\package2.cab 
    ```

    Weitere Informationen zu diesen DISM-Befehlszeilenoptionen finden Sie unter [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

    Sie können auch DISM-Befehlszeilenoptionen für eine angewendeten Windows-Abbild Treiber hinzufügen, Sprachpakete hinzufügen, ändern Sie auf eine höhere Version von Windows oder Anwenden einer Antwortdatei. Weitere Informationen finden Sie unter:

    -   [Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)

    -   [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

    -   [DISM Windows Edition zum Warten von Befehlszeilenoptionen](dism-windows-edition-servicing-command-line-options.md)

    -   [DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

2.  Überprüfen Sie die Protokolldatei, um sicherzustellen, dass das Paket erfolgreich hinzugefügt wurde.

    Einige Pakete und Treiber, die hinzugefügt oder entfernt wurden möglicherweise in aussteht. Dies ist in der Regel, da ein Neustart erforderlich ist, um die Aktion auszuführen. Starten das Bild im Überwachungsmodus wird die Restart-Anforderung erfüllen, und Applikationen hinzufügen, und stellen Sie zusätzliche erforderliche Anpassungen vor. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

## <a name="span-idnextstepspanspan-idnextstepspanspan-idnextstepspannext-step"></a><span id="Next_Step"></span><span id="next_step"></span><span id="NEXT_STEP"></span>Als Nächstes


In dieser exemplarischen Vorgehensweise wird die grundlegende Offlinewartung eines angewendeten Windows-Abbilds in Windows PE veranschaulicht. Wenn Sie diesen Vorgang abgeschlossen haben, werden die Pakete dem Windows-Abbild hinzugefügt. Sie können nun entweder ausführen `sysprep /generalize /oobe` entfernen computerspezifischen Anpassungen und erfassen das Bild später bereitstellen oder ausführen `sysprep /oobe` um die speziellen Anpassungen und das Versenden von diesem Computer. Mithilfe der `/oobe` Option wird sichergestellt, dass der Computer im Modus Out-of-Box-Experience (OOBE) das nächste Mal gestartet wird, die es gestartet wird. Weitere Informationen finden Sie unter [Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[Ein Windows-Abbild mithilfe von DISM-Service](service-a-windows-image-using-dism.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[Windows ADK](http://go.microsoft.com/fwlink/p/?linkid=526803)

 

 






