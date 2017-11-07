---
author: Justinha
Description: "Hinzufügen und Entfernen von Treibern zu einem Offline-Windows-Bild"
ms.assetid: 71651630-2e26-4174-8161-8f83b8ae4bc3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen und Entfernen von Treibern zu einem Offline Windows-Bild"
ms.openlocfilehash: 8bc27dda494a405404dee0bf8cb7272e5363bc7e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-drivers-to-an-offline-windows-image"></a>Hinzufügen und Entfernen von Treibern zu einem Offline Windows-Bild


Sie können das Tool Deployment Image Servicing and Management (DISM) zu installierendes oder Treiberdateien (INF) in einer Windows-Abbild offline zu verwenden. Können Sie entweder eine Antwortdatei auf einer bereitgestellten WIM-, VHD- oder .vhdx Datei anwenden, oder Sie können hinzufügen oder Entfernen der Treiber direkt über die Befehlszeile.

Wenn Sie DISM verwenden, um einen Gerätetreiber zu einem offline Bild zu installieren, wird der Gerätetreiber Driver Store in offline-Abbild hinzugefügt. Wenn das Abbild gestartet wird, Plug & Play (Plug & Play-) ausgeführt, und ordnet die Treiber im Speicher für die entsprechende Geräte auf dem Computer.

**Hinweis**   Zum Hinzufügen von Treibern zu einem Windows-10-Abbild müssen Sie offline, ein Referenzcomputer unter 10 Windows, Windows Server 2016 Technical Preview oder Windows Vorinstallation Environment (Windows PE) für Windows 10 verwenden. Überprüfung der Treiber Signatur kann misslingen, wenn Sie einen Treiber aus ein Referenzcomputer unter einem anderen Betriebssystem zu einem Windows-10-Abbild hinzufügen.


## <a name="to-add-drivers-to-an-offline-image-by-using-dism"></a>So ein offline-Abbild mithilfe von DISM Treiber hinzu

1.  Bei einer Eingabeaufforderung mit erhöhten Rechten Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine WIM-Datei angeben. Sie müssen für eine VHD-Datei angeben `/Index:1`.

2.  Stellen Sie die offline-Windows-Abbild bereit. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows Drive" /MountDir:C:\test\offline
    ```

3.  Hinzufügen eines Treibers für das Bild.

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\drivers\mydriver.inf
    ```

    Um alle Treiber aus einem Ordner und alle Unterordner installieren, zeigen Sie auf den Ordner, und verwenden Sie der **Option/Recurse** .

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:c:\drivers /Recurse
    ```

    **Warnung**  Während/recurse praktisch sein kann, ist es einfach, Aufblasen Ihr Bild zu. Einige Treiberpakete enthalten mehrere INF-Treiberpakete, die häufig Nutzlast Dateien im gleichen Ordner gemeinsam nutzen. Während der Installation wird jede INF-Paket in einen gesonderten Ordner, jeweils mit einer Kopie der Dateien Nutzlast erweitert. Wir haben Fällen gesehen, in denen ein beliebter Treiber in einem Ordner 900MB 10 GB Bilder, wenn mit der Option/recurse hinzugefügt hinzugefügt.

    Um eine nicht signierte Treiber zu installieren, verwenden Sie **Option/ForceUnsigned** die Anforderung außer Kraft gesetzt, die auf X64-basierte Computer installierten Treiber eine digitale Signatur benötigen.

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\drivers\mydriver.inf /ForceUnsigned
    ```

4.  Überprüfen Sie die Liste der Treiberdateien im Windows-Abbild Drittanbieter-(INF). Treiber hinzugefügt werden, auf dem Windows-Abbild heißen Oem\*. inf-Datei. Dies ist eindeutigen Benennen von neuen Treiber hinzugefügt werden, auf dem Computer zu gewährleisten. Beispielsweise sind die Dateien Treiber1.inf und Treiber2.inf umbenannte Oem0.inf und Oem1.inf.

    ``` syntax
    Dism /Image:C:\test\offline /Get-Drivers 
    ```

5.  Commit der Änderungen, und heben Sie die Bereitstellung des Abbilds.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-remove-drivers-from-an-offline-image-by-using-dism"></a>Zum Entfernen von Treibern aus einem offline-Abbild mithilfe von DISM

1.  Rufen Sie an einer Eingabeaufforderung mit erhöhten Rechten ab der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine WIM-Datei angegeben. Sie müssen für eine VHD-Datei angeben `/Index:1`.

2.  Binden Sie die offline-Windows-Abbild. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 10 Home" /MountDir:C:\test\offline
    ```

3.  Entfernen eines bestimmten Treibers aus dem Bild. In einer Befehlszeile können mehrere Treiber entfernt werden.

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Driver /Driver:OEM1.inf /Driver:OEM2.inf
    ```

    **Warnung**  
    Entfernen eines wichtigen Treiberpakets kann die offline-Windows-Abbild nicht startbaren tätigen. Weitere Informationen finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-driver-servicing-command-line-options-s14.md).
     

4.  Commit der Änderungen, und deaktivieren Sie das Bild.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-add-drivers-to-an-offline-windows-image-by-using-an-unattended-answer-file"></a>So ein offline-Windows-Abbild mithilfe einer Antwortdatei Treiber hinzu

1.  Suchen Sie die Gerätetreiber INF-Dateien, die Sie auf dem Windows-Abbild installieren möchten.

    **Hinweis**  
    Alle Treiber im Verzeichnis und Unterverzeichnisse, die in die Antwortdatei verwiesen werden, werden das Bild hinzugefügt. Sie sollten die Antwortdatei und diese Verzeichnisse sehr sorgfältig, um über das Vergrößern des Bilds mit Lösungspaketen unnötige Treiber verwalten.

2.  Verwenden Sie Windows System Image Manager (Windows SIM) zum Erstellen einer Antwortdatei enthält, die die Pfade zu Gerätetreiber, die Sie installieren möchten.

3.  Die Antwortdatei im Durchgang **OfflineServicing** Konfiguration die Komponente Microsoft-Windows-PnpCustomizationsNonWinPE hinzugefügt.

4.  Erweitern Sie den Knoten **Microsoft-Windows-PnpCustomizationsNonWinPE** in die Antwortdatei ein. Mit der rechten Maustaste **DevicePaths**, und wählen Sie dann den **Neuen Wert für PathAndCredentials einfügen**.

    Ein neuer **Wert für PathAndCredentials** Listeneintrag wird angezeigt.

5.  Für jeden Standort, den Sie für den Zugriff auf eine separate **vom Typ PathAndCredentials** Listenelement hinzufügen möchten.

6.  Geben Sie in der Microsoft-Windows-PnpCustomizationsNonWinPE-Komponente den Pfad zu den Gerätetreiber und die Anmeldeinformationen, die Zugriff auf die Datei verwendet werden, wenn die Datei auf einer Netzwerkfreigabe ist.

    **Hinweis**  
    Sie können mehrere Geräte Treiberpfade einschließen, indem mehrere **Wert für PathAndCredentials** Listenelemente hinzufügen. Wenn Sie mehrere Listenelemente hinzufügen, müssen Sie den Wert des **Schlüssels** für jeden Pfad erhöhen. Beispielsweise können Sie zwei separate Treiberpfade, in denen der Wert des **Schlüssels** für den ersten Pfad ist gleich **1** und der Wert des **Schlüssels** für den zweiten Pfad ist gleich **2,**hinzufügen.

7.  Speichern Sie die Antwortdatei und Beenden von Windows SIM. Die Antwortdatei muss wie im folgende Beispiel aussehen.

    ``` syntax
    <?xml version="1.0" ?><unattend xmlns="urn:schemas-microsoft-com:asm.v3" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State">
       <settings pass="offlineServicing">
          <component name="Microsoft-Windows-PnpCustomizationsNonWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1">
                   <Path>\\networkshare\share\drivers</Path>
                   <Credentials>
                      <Domain>Fabrikam</Domain>
                      <Username>MyUserName</Username>
                      <Password>MyPassword</Password>
                   </Credentials>
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

8.  Stellen Sie das Windows-Abbild, das Sie die Treiber mithilfe von DISM installieren möchten. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine WIM-Datei angeben. Sie müssen für eine VHD-Datei angeben `/Index:1`.

9.  Verwenden Sie DISM, um die Antwortdatei auf das bereitgestellte Windows-Abbild anzuwenden. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    Weitere Informationen zum Anwenden einer Antwortdatei finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md).

    Die INF-Dateien im Pfad in die Antwortdatei verwiesen werden die Windows-Abbild hinzugefügt.

10. Die Liste der Treiberdateien in das Windows-Abbild Drittanbieter-(INF) lesen. Treiber hinzugefügt werden, auf dem Windows-Abbild heißen Oem\*. inf-Datei. Dadurch wird sichergestellt, dass alle neuen Treiber, die an dem Computer hinzugefügt werden, eindeutig benannt sein. Beispielsweise sind die Dateien Treiber1.inf und Treiber2.inf umbenannte Oem0.inf und Oem1.inf.

    Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Get-Drivers 
    ```

11. Heben Sie die Bereitstellung der WIM-Datei, und die Änderungen zu übernehmen. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

Treiber für Windows PE auf der lokalen Festplatte oder ein Netzwerk angezeigt werden sollen, müssen Sie die **WindowsPE** Konfiguration Durchlauf der eine Antwortdatei Treiber zu Windows PE Driver Store hinzufügen und wichtige Treiber erforderliche Windows PE entsprechend verwenden. Weitere Informationen finden Sie unter [Hinzufügen von Treibern zu Windows während Windows Setup](add-device-drivers-to-windows-during-windows-setup.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Gerätetreiber und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






