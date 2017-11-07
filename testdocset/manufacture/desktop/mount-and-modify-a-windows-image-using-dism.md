---
author: Justinha
Description: "Bereitstellen Sie und ändern Sie ein Windows-Abbild mithilfe von DISM"
ms.assetid: f48b4681-bc59-4eb1-89c9-0163594467f7
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bereitstellen Sie und ändern Sie ein Windows-Abbild mithilfe von DISM"
ms.openlocfilehash: 82d127bdda4e6f7eef73a53f27b0784a04f1559e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mount-and-modify-a-windows-image-using-dism"></a>Bereitstellen Sie und ändern Sie ein Windows-Abbild mithilfe von DISM


Das Tool Deployment Image Servicing and Management (DISM) können Sie ein Windows-Abbild von einer WIM oder VHD-Datei bereitstellen. Bereitstellen eines Abbilds ordnet den Inhalt des Bilds in ein Verzeichnis zu, damit Sie das Abbild mithilfe von DISM ohne starten das Bild zu bearbeiten können. Allgemeine Dateivorgänge, beispielsweise Kopieren und Einfügen auf einer bereitgestellten Bild bearbeiten können Sie auch ausführen.

**Hinweis**  
DISM kann keinem Windows-Abbild einer virtuellen Festplatte unter Windows Vista mit Service Pack 1 (SP1) oder Windows Server 2008 bereitgestellt werden. Fügen Sie die virtuelle Festplatte mit dem DiskPart-Tool aus, bevor Sie DISM verwenden können, die-Abbild. Wenn Sie Abbildern, die mithilfe von DiskPart angefügt wurden Service, die Änderungen werden automatisch mit jedem Vorgang ein Commit ausgeführt und können nicht gelöscht werden.

 

Sie können bereitstellen und mehrere Bilder auf einem einzelnen Computer ändern. Weitere Informationen finden Sie unter [Deployment Image Servicing und Best Practices Management (DISM)](deployment-image-servicing-and-management--dism--best-practices.md).

## <a name="span-idmountinganimagespanspan-idmountinganimagespanspan-idmountinganimagespanmounting-an-image"></a><span id="Mounting_an_Image"></span><span id="mounting_an_image"></span><span id="MOUNTING_AN_IMAGE"></span>Bereitstellen eines Abbilds


Sie können ein Bild mit der Option **/ Optimieren** , anfänglichen Mount Zeit reduziert bereitstellen. Jedoch werden bei Verwendung die Option **/ Optimieren** Prozesse, die normalerweise während der Bereitstellung eines ausgeführt werden stattdessen beim ersten Mal ausgeführt werden, dass Sie Zugriff auf ein Verzeichnis. Daher kann ein Anstieg in der Zeit, die erforderlich sind, Zugriff auf ein Verzeichnis zum ersten Mal nach dem Bereitstellen eines Abbilds mit der Option **/ optimize** vorhanden sein.

**Ein Abbild bereitstellen**

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten. Bei Verwendung eine Version von Windows als Windows 8 oder Windows 10, verwenden Sie die Bereitstellung Tools Cmd Prompt mit ADK installiert oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.

2.  Stellen Sie das Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
    ```

    **Hinweis**  
    Um ein Windows-Abbild aus einer VHD-Datei bereitzustellen, müssen Sie angeben `/index:1`.

     

    Sie können auch Optionen zum Bereitstellen des Image mit Leseberechtigungen oder zur Reduzierung der anfänglichen Mount-Zeit mit der Option **/Optimize** hinzufügen. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline /ReadOnly /Optimize
    ```

    Weitere Informationen zu den für die Option **/Mount-Image** DISM verfügbaren Optionen finden Sie unter [Befehlszeilenoptionen für DISM Bild Management](dism-image-management-command-line-options-s14.md).

## <a name="span-idmodifyinganimagespanspan-idmodifyinganimagespanspan-idmodifyinganimagespanmodifying-an-image"></a><span id="Modifying_an_Image"></span><span id="modifying_an_image"></span><span id="MODIFYING_AN_IMAGE"></span>Ändern eines Bildes


Nachdem Sie ein Abbild bereitstellen, können Sie das Verzeichnis des Bilds durchsuchen. Sie können die Datei- und Ordnerstruktur überprüfen und hinzufügen, bearbeiten oder Löschen von Dateien und Ordnern.

Sie können das Tool DISM auch zum Hinzufügen und Entfernen der Treiber und Pakete, einschließlich Language Packs, Treiber und Pakete auflisten, Konfigurationseinstellungen und vieles mehr zu ändern. Weitere Informationen finden Sie unter [Service ein DISM mithilfe eines Windows Bild](service-a-windows-image-using-dism.md).

**Anzeigen und Ändern eines Abbilds**

1.  Öffnen Sie auf dem Referenzcomputer das bereitgestellte Verzeichnis. Beispielsweise

    ``` syntax
    cd C:\mounted_images
    ```

2.  Löschen, bearbeiten oder Hinzufügen von zusätzliche Dateien und Ordner zu dem Speicherort, wo diese auftreten müssen, nachdem sie auf dem Zielcomputer angewendet wurden. Beispielsweise C:\\Programm\_Dateien\\Anwendung\_Name.

    **Wichtige**  
    Wenn Sie eine Anwendung oder ein Gerät hinzufügen müssen, stellen Sie sicher, dass Sie alle erforderlichen Dateien enthalten. Obwohl Sie Anwendungsdateien und Ordner hinzufügen können, wird nicht Applikationen installieren.

     

## <a name="span-idcommittingchangestoanimagespanspan-idcommittingchangestoanimagespanspan-idcommittingchangestoanimagespancommitting-changes-to-an-image"></a><span id="Committing_Changes_to_an_Image"></span><span id="committing_changes_to_an_image"></span><span id="COMMITTING_CHANGES_TO_AN_IMAGE"></span>Ausführen eines Commits für Änderungen zu einem Bild


Sie können ein Bild Commits ohne Aufheben der Bereitstellung des Abbilds.

**Commits für ein Bild**

-   Geben Sie an der Befehlszeile Folgendes ein:

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

    Verwenden Sie **/CheckIntegrity** zum Erkennen und WIM-Datei eine Beschädigung zu verfolgen, wenn Sie für das Bild Commits. Beim Anwenden oder stellen Sie das Abbild, verwenden Sie **/CheckIntegrity** erneut aus, um den Vorgang zu beenden, wenn eine Beschädigung der Datei erkannt wurde. **/CheckIntegrity** kann nicht mit virtual Hard Disk (VHD) Dateien verwendet werden.

## <a name="span-idunmountinganimagespanspan-idunmountinganimagespanspan-idunmountinganimagespanunmounting-an-image"></a><span id="Unmounting_an_Image"></span><span id="unmounting_an_image"></span><span id="UNMOUNTING_AN_IMAGE"></span>Aufheben der Bereitstellung eines Abbilds


Nachdem Sie ein Bild ändern, müssen Sie die Bereitstellung aufheben. Wenn Sie Ihr Bild mit den Lese-/Schreibzugriff Standardberechtigungen bereitgestellt haben, können Sie die Änderungen zu übernehmen. Dadurch wird Ihre Änderungen einen permanenten Teil des Bilds.

**Ein Bild Bereitstellung aufzuheben.**

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten. Wenn Sie eine Version von Windows als Windows 8 oder Windows 10 verwenden, verwenden Sie die Bereitstellung von Tools Cmd Prompt mit ADK installiert oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.


2.  Hängen Sie das Bild aus.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /commit
    ```

    wobei `C:\test\offline` ist der Speicherort des Verzeichnisses bereitstellen. Wenn Sie nicht die Parameter zum Entladen angeben, wird diese Option enthält eine Liste aller bereitgestellten Abbilder jedoch keine entladen-Aktion ausgeführt wird.

    **Wichtige**  
    Wenn Sie die Option **/ heben Sie die Bereitstellung** verwenden, müssen Sie **die/Commit** **oder/verwerfen** -Argument verwenden.

     

Nach dem Ändern der Schwelle, können Sie das Bild, von einer Netzwerkfreigabe oder auf einem lokalen Datenträger anwenden, wie eine CD/DVD oder ein USB-Flashlaufwerk (UFD).

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


**Die DISM-Befehle in diesem Thema ausfallen, versuchen Sie Folgendes:**

1.  Stellen Sie sicher, dass Sie die Windows-10-Version von DISM verwenden, die mit der ADK Windows installiert ist.

2.  Wenn Sie eine Windows 8.1, Windows 8 oder Windows 7-PC verwenden, verwenden Sie die **Bereitstellung und Imaging Tools Umgebung** auf die Tools zugreifen, die mit der Windows-10-Version von Windows ADK installiert sind.

3.  Bilder zu geschützten Ordnern an, wie Ihre Benutzer nicht bereitstellen\\-Dokumentordner.

4.  Wenn DISM Prozesse unterbrochen werden, können Sie vorübergehend vom Netzwerk trennen und Virenschutz deaktivieren.

5.  Wenn DISM Prozesse unterbrochen werden, sollten Sie stattdessen die Befehle aus der Windows-Vorinstallation-Umgebung (Windows PE) ausführen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Ein Windows-Abbild mithilfe von DISM Service](service-a-windows-image-using-dism.md)

 

 






