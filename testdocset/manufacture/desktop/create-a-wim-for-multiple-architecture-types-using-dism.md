---
author: Justinha
Description: "Erstellen einer WIM-DATEI für mehrere Architekturtypen mithilfe von DISM"
ms.assetid: fcb1b461-72c1-40c5-8405-38a5db05dd34
MSHAttr: PreferredLib:/library/windows/hardware
title: "Erstellen einer WIM-DATEI für mehrere Architekturtypen mithilfe von DISM"
ms.openlocfilehash: 932c4d8e47e23bd7514c6fc1f7fdc64be571f46a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-wim-for-multiple-architecture-types-using-dism"></a>Erstellen einer WIM-DATEI für mehrere Architekturtypen mithilfe von DISM


Berücksichtigen Sie beim Planen der Bereitstellungsszenarien, wie Sie bereitstellen und Verwalten Ihrer Bilder für andere Architekturtypen. Es gibt verschiedene Methoden, die Sie mehrere Windows® Bilder für mehrere Architekturtypen verwalten können. Da Sie sowohl 32-Bit- und 64-Bit-Windows-Bilder aus einer Vorinstallation 32-Bit-Umgebung bereitstellen können, können Sie die 32-Bit- und 64-Bit-Windows-Bilder in der gleichen Windows WIM-Datei oder eine separate WIM-Dateien beibehalten.

Da Sie mehrere Windows-Abbilder in einer einzigen WIM-Datei speichern können, können Sie architekturspezifische WIM-Dateien oder einer einzigen WIM-Datei mit Bilder für mehrere Architekturtypen erstellen.

-   nur die 32-Bit-Grafiken

    Sie können eine WIM-Datei erstellen, die Windows-Abbilder für einen einzelnen Architektur enthält. In diesem Szenario erstellen Sie eine WIM-Datei, die für 32-Bit-Systeme nur ein oder mehrere Windows-Bilder enthält. Sie erstellen separate WIM-Dateien für andere Architekturtypen.

-   nur 64-Bit-Grafiken

    Sie können eine WIM-Datei erstellen, die enthält eine oder mehrere der 64-Bit-Windows-Bilder, die Sie bereitstellen.

-   32-Bit- und 64-Bit-Bilder

    Sie können eine WIM-Datei erstellen, die mehrere Windows-Editionen für mehrere Architekturtypen enthält. Beispielsweise können Sie ein Windows-Abbild erstellen, die zwei Versionen von Windows, Architekturen für 32-Bit- und 64-Bit-Architekturen enthält.

## <a name="span-idtocreateawindowsimageformultiplearchitecturetypesspanspan-idtocreateawindowsimageformultiplearchitecturetypesspanspan-idtocreateawindowsimageformultiplearchitecturetypesspanto-create-a-windows-image-for-multiple-architecture-types"></a><span id="To_Create_a_Windows_Image_for_Multiple_Architecture_Types"></span><span id="to_create_a_windows_image_for_multiple_architecture_types"></span><span id="TO_CREATE_A_WINDOWS_IMAGE_FOR_MULTIPLE_ARCHITECTURE_TYPES"></span>Zum Erstellen eines Windows-Abbilds für mehrere Architekturtypen


Sie können eine einzelne WIM-Datei erstellen, die 32-Bit- und 64-Bit-Windows-Abbilder umfasst. Sie müssen eine 32-Bit-Windows-Verteilung und eine 64-Bit-Datei Install.wim verfügen. (Eine Windows-Verteilung ist die Auflistung der Dateien auf dem Windows-Installationsmedium die umfasst nicht nur die Datei Install.wim jedoch zusätzliche Dateien und Verzeichnisse, die für die Installation erforderlich sind.) Plattformübergreifende Bereitstellung wird nur von 32-Bit-Windows-Setup unterstützt.

1.  Kopieren Sie die gesamte 32-Bit-Windows-Verteilung in ein temporäres Verzeichnis auf dem lokalen Computer.

2.  Kopieren der 64-Bit-Install.wim Datei in ein separates temporäres Verzeichnis auf dem lokalen Computer.

3.  Verwenden Sie an einer Eingabeaufforderung **Dism** Befehl, um die 64-Bit-Windows-Abbilder in der Install.wim-Datei in der Windows-Verteilung exportieren.

4.  Wiederholen Sie den Befehl **Dism /Export-Image** für jedes 64-Bit-Windows-Abbild, die Sie für die Windows-Verteilung hinzufügen möchten.

Wenn Sie die Verteilung kopieren beispielsweise\\WindowsDistribution und der 64-Bit-Install.wim Dateiname C:\\Windows64-Bit, verwenden Sie Folgendes an der Befehlszeile.

``` syntax
Dism /Export-Image /SourceImageFile:c:\windows64-bit\install.wim /SourceIndex:1 /DestinationImageFile:c:\windowsdistribution\sources\install.wim /DestinationName:"Fabrikam 64-bit Image"
```

**Hinweis**  
Es ist wichtig, den Namen des Windows-Abbilds, um anzugeben, dass es für 64-Bit-Computern nur ist hinzufügen.

 

Die 64-Bit-Windows-Abbild und alle zugehörigen Metadaten werden in der Install.wim-Datei in einen neuen Index während des Exportvorgangs kopiert. Wenn Sie alle Windows-Abbilder auf die Datei Install.wim hinzugefügt haben, ist die Windows-Verteilung in Ihrer Umgebung verwendet werden bereit.

Während der Benutzer-Installationen werden Benutzer zum auswählen, welches architekturspezifische Windows-Bild (X86 oder X64 Bilder) installieren aufgefordert.

Unbeaufsichtigte Installationen, wenn Sie mehrere Windows-Editionen für mehrere Architekturtypen in einer einzigen WIM-Datei speichern müssen Sie explizit angeben welches Abbild installiert während der Installation von Windows mit der `MetaData` Einstellung.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






