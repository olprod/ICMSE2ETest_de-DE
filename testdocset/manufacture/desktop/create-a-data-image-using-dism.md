---
author: Justinha
Description: Erstellen einer Datenabbild mithilfe von DISM
ms.assetid: e182335f-fe0e-4e85-8c2b-807d22af6d4b
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen einer Datenabbild mithilfe von DISM
ms.openlocfilehash: cf499f4ff64b46fbd5d3f63bef3ec96329e2970e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-data-image-using-dism"></a>Erstellen eines Datenabbilds mithilfe von DISM


Zum Hinzufügen von Anwendungen, Dateien und andere Ressourcen zu Windows® während der Installation können Sie ein Datenabbild erstellen. Mithilfe des Tools Abbildern Bereitstellung und Verwaltung (DISM) zu verwenden, können Sie zusätzliche Windows-Abbild an (WIM-Dateien) erstellen, die enthalten nur die Dateien und Anwendungen, die Sie auf der Windows-Installation kopieren möchten.

Aktivieren Sie Datenabbilder hinzufügen:

-   Anwendungen, Dateien, Skripts und anderen Ressourcen, die Windows während der Installation.

-   Dateien, Ressourcen und anderen Daten in eine Partition als Betriebssystempartition.

**Hinweis**  
Nur für neue Dateien in einer Windows-Installation hinzufügen, müssen Datenabbilder verwendet werden. Verwenden Sie Datenabbilder nicht vorhandene Windows-Dateien ersetzt. Überschreiben von Daten des Betriebssystems wird nicht unterstützt.

 

Vorherige Methoden zum Übertragen von Daten in einer Windows-Installation erforderlich, die Verwendung von $OEM$ Folders. Dieser Ordnerstrukturen werden weiterhin unterstützt, aber Datenabbilder bieten ein einfacher und effizienter Möglichkeit zum Übertragen von zusätzlichen Daten auf Windows.

So installieren Sie das Windows-Abbild wird in unbeaufsichtigte Installationen vom angegeben der `OSImage` in der Microsoft-Windows-Setup-Komponente festlegen. Sie können eine oder mehrere hinzufügen `DataImage` Einstellungen in der Microsoft-Windows-Setup-Komponente, die zusätzliche Datenabbilder darstellen, die Sie mit dem System hinzufügen. Weitere Informationen finden Sie unter Windows® unbeaufsichtigte Installation Reference.

**So erstellen Sie ein Datenabbild**

1.  Suchen Sie nach den Daten, denen Sie ein Datenabbild für erstellen.

2.  Öffnen Sie ein Eingabeaufforderungsfenster als Administrator an, oder starten Sie den Computer zu Windows PE an der Windows PE-Eingabeaufforderungsfenster zu öffnen.

3.  Verwenden Sie DISM um die Datendateien in eine WIM-Datei zu komprimieren. Beispiel:

    ``` syntax
    Dism /Capture-Image /ImageFile:c:\data\myData.wim /CaptureDir:C:\data\dataFiles /Name:MyData
    ```

    In diesem Beispiel werden alle Elemente unter Laufwerk C:\\Daten\\Datendateien Verzeichnis der WIM-Datei hinzugefügt wird und die WIM-Datei erhält die Bezeichnung "MyData". Alle Dateien und Ordner unter C:\\Daten\\Datendateien werden in den Stamm des dem angegebenen Laufwerk auf die Antwortdatei extrahiert.

    Weitere Informationen zur Verwendung von DISM finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

4.  Kopieren Sie das Datenabbild auf einen verfügbaren Speicherort wie eine andere Partition oder eine Netzwerkfreigabe, während der Installation von Windows.

**Einen Bild Datenpfad zu einer Antwortdatei hinzufügen**

1.  Verwenden Sie Windows System Image Manager (Windows SIM) zum Erstellen einer Antwortdatei enthält, die den Pfad zu der die Bilddaten installieren und den Speicherort für die Installation.

2.  Hinzufügen das Microsoft-Windows-Setup\\ `DataImage` Einstellungen, um die entsprechende Konfiguration für Ihre Umgebung zu übergeben. Beispiel: `windowsPE`.

3.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM.

    Die Antwortdatei muss dem folgenden Beispiel ähneln:

    ``` syntax
       <settings pass="windowsPE">
          <component name="Microsoft-Windows-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <ImageInstall>
                <DataImage wcm:action="add">
                   <InstallTo>
                      <DiskID>0</DiskID>
                      <PartitionID>1</PartitionID>
                   </InstallTo>
                   <InstallFrom>
                      <Credentials>
                         <Domain>Fabrikam</Domain>
                         <Username>MyUsername</Username>
                         <Password>MyPassword</Password>
                      </Credentials>
                   <Path>\\networkshare\share\MyData.wim</Path>
                   </InstallFrom>
                      <Order>1</Order>
                </DataImage>
             </ImageInstall>
          </component>
       </settings>
    ```

4.  Führen Sie Setup.exe, den Speicherort der Antwortdatei angibt. Beispiel:

    ``` syntax
    setup /unattend:C:\unattend.xml
    ```

Alle Dateien und Ordner im Datenabbild angegeben werden während der Installation in den Stamm des Laufwerks extrahiert. Ausführbare Dateien und Skripts werden nicht ausgeführt, wenn das Datenabbild angewendet wird; Sie werden nur in das Laufwerk kopiert. Sie können `FirstLogonCommands` Befehle zum ersten Mal ein Benutzer an dem Computer anmeldet ausführen festgelegt werden. Weitere Informationen zu `FirstLogonCommands`, finden Sie unter Windows® unbeaufsichtigte Installation Reference.

 

 





