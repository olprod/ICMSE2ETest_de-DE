---
author: Justinha
Description: Aktivieren Sie oder deaktivieren Sie des Windows-Features mithilfe von DISM
ms.assetid: a5280bba-7808-4752-92ca-7605a9ea29f0
MSHAttr: PreferredLib:/library/windows/hardware
title: Aktivieren Sie oder deaktivieren Sie des Windows-Features mithilfe von DISM
ms.openlocfilehash: 231846d0c9ed29ed9fd7877dac2766166a6a9f62
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-or-disable-windows-features-using-dism"></a>Aktivieren Sie oder deaktivieren Sie des Windows-Features mithilfe von DISM


Das Tool Abbildern Bereitstellung und Verwaltung (DISM) ist ein Befehlszeilentool, mit dem Windows® Bilder ändern. Sie können DISM verwenden, aktivieren oder Deaktivieren des Windows-Features direkt über die Befehlszeile oder indem Sie eine Antwortdatei auf das Bild anwenden. Sie können aktivieren oder Deaktivieren der Windows-Features auf einer WIM oder VHD-Datei offline oder online auf einem Betriebssystem ausgeführt wird.

## <a name="to-mount-an-offline-image-for-servicing"></a>Zum Bereitstellen einer offline-Abbilds für die Wartung

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten.

2.  Um DISM aus einer Installation von Windows Assessment and Deployment Kit (Windows ADK) verwenden, zu dem Wartung Windows ADK-Ordner, und navigieren Sie zu diesem Verzeichnis. DISM wird standardmäßig unter C: installiert\\Program Files (x86)\\Windows Kits\\10.0\\Assessment and Deployment Kit\\Bereitstellungstools\\ in Windows 10, C:\\Program Files (x86)\\Windows Kits\\8.1\\Assessment and Deployment Kit\\Bereitstellungstools\\ in Windows 8.1and C:\\Program Files (x86)\\Windows Kits\\8.0\\Assessment and Deployment Kit\\Bereitstellungstools\\ in Windows 8.

    DISM ist in verfügbar:

    -   Windows-10
    -   Windows 8.1
    -   Windows 8
    -   Windows Server 2016 – Technische Vorschau
    -   Windows Server 2012 R2
    -   WindowsServer 2012
    -   Vorinstallation Windows-Umgebung (Windows PE) für Windows 10
    -   Windows PE 5.0
    -   Windows PE 4.0

    Sie können DISM Bereitstellung und andere imaging Tools installieren, wie Windows System Image Manager (Windows System Image Manager) auf einem anderen Betriebssystem aus der Windows-ADK unterstützt. Weitere Informationen finden Sie unter [DISM unterstützte Plattformen](dism-supported-platforms.md).

3.  Verwendung der `/Get-ImageInfo` Option zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten. Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine Bilddatei angeben.

    Beispielsweise geben Sie in der Befehlszeile:

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

4.  Stellen Sie die offline-Windows-Abbild bereit. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Base Windows Image" /MountDir:C:\test\offline
    ```

## <a name="to-find-available-windows-features-in-an-image"></a>Verfügbare Windows-Features in ein Bild zu finden sind

1.  Listen Sie aller Features im Betriebssystem verfügbar auf. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-Features
    ```

    Um ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Get-Features
    ```

    Sie können `>featurelist.txt` zur Umleitung von der Ausgabe des Befehls an eine Textdatei mit dem Namen Komponentenliste.

2.  Überprüfen Sie die Liste der Features, das Feature zu erhalten, das Sie aktivieren, deaktivieren, entfernen oder wiederherstellen möchten.

3.  Verwendung `/Get-FeatureInfo` zu Listeninformationen zu einem bestimmten Feature Sie interessiert sind. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

## <a name="to-enable-windows-features"></a>Windows-Features aktivieren

1.  Aktivieren Sie ein bestimmtes Feature im Bild. Sie können die `/All` Argument für alle übergeordneten Features in demselben Befehl aktivieren. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Enable-Feature /FeatureName:TFTP /All
    ```

    Um ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Enable-Feature /FeatureName:TFTP /All
    ```

2.  Optional: Rufen Sie den Status des Features, die Sie aktiviert haben. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    Wenn der Status **Pending nutzten**ist, müssen Sie das Bild, um das Feature vollständig aktivieren starten.

## <a name="to-restore-removed-windows-features"></a>Wiederherzustellende entfernt Windows-features

1.  Aktivieren Sie ein bestimmtes Feature im Bild. Wenn Sie eine Quelle nicht angeben, sucht DISM am Standardspeicherort durch Gruppenrichtlinien für die erforderlichen Dateien zum Aktivieren des Features für Weitere Informationen finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md)erforderlich festgelegt.

    Wenn die Dateien am Standardspeicherort nicht gefunden werden, kontaktiert DISM Windows Update (WU) nach der erforderlichen Dateien. Sie können die `/LimitAccess` Argument für die Kontaktaufnahme mit WU DISM zu verhindern.

    Wenn Sie mehrere angeben `/Source` Argumente, die Dateien gesammelt werden die erste Position, wo sie sind vorhanden, und der Rest der Speicherorte werden ignoriert.

    Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Online /Enable-Feature /FeatureName:TFTP /Source:Z:\sources\SxS /Source:C:\test\mount\windows /LimitAccess
    ```

    Wenn Sie ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Enable-Feature /FeatureName:TFTP /Source:C:\test\mount\windows
    ```

2.  Optional: Rufen Sie den Status des Features, die Sie aktiviert haben. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    Wenn der Status **EnablePending**ist, müssen Sie das Bild, um das Feature vollständig aktivieren starten.

## <a name="to-disable-windows-features"></a>So deaktivieren Sie Windows-features

1.  Deaktivieren Sie ein bestimmtes Feature im Bild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Disable-Feature /FeatureName:TFTP
    ```

    Wenn Sie ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Disable-Feature /FeatureName:TFTP
    ```

2.  Optional: Verwenden Sie `DISM /GetFeatureInfo` um den Status des Features erhalten Sie deaktiviert haben. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    Wenn der Status **DisablePending**ist, müssen Sie das Bild, um das Feature vollständig deaktivieren starten.

## <a name="to-remove-windows-features-for-on-demand-installation"></a>Entfernen von Windows-Features für die Installation bei Bedarf

1.  Entfernen Sie ein bestimmtes Feature im Bild, ohne das Feature Manifest aus diesem Abbild entfernen. Diese Option kann nur verwendet werden, wenn Windows 10, 8.1 Windows, Windows 8, Windows Server 2016 Technical Preview, Windows Server 2012 R2 oder Windows Server 2012 – Wartung. Weitere Informationen finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md).

    Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Disable-Feature /FeatureName:TFTP /Remove
    ```

    Um ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Disable-Feature /FeatureName:TFTP /Remove
    ```

2.  Optional: Verwenden Sie `DISM /GetFeatureInfo` um den Status des Features erhalten Sie deaktiviert haben. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    Der Status ist **deaktiviert**. Beginnend mit Windows 10, wird die Nutzlast nicht aus Windows entfernt, Client-SKUs zur Unterstützung der Drucktaste zurückgesetzt. Nutzlast wurde von Windows Server-SKUs entfernt.

## <a name="to-enable-or-disable-windows-features-by-using-dism-and-an-answer-file"></a>So aktivieren oder Deaktivieren des Windows-Features mithilfe von DISM und einer Antwortdatei

1.  Klicken Sie in Windows System Image Manager Öffnen eines vorhandenen Katalogs, indem Sie im Menü **Datei** auf **ein Windows-Abbild auswählen** und Angeben des Dateityps Katalog (CLG) in der Dropdown Liste, oder Erstellen eines neuen Katalogs, indem Sie im **Katalog erstellen** im Menü **Extras** .

2.  Erweitern Sie den Katalog im Bereich **Windows-Abbild** , und klicken Sie dann **Pakete**.

3.  Erweitern Sie **Foundation**und **Microsoft Windows Foundation-Paket**Maustaste.

4.  Klicken Sie auf die **Antwortdatei hinzufügen**.

5.  Klicken Sie neben den Features, die Sie verwenden möchten, aktivieren oder deaktivieren Sie auf **aktiviert** oder **deaktiviert** . Klicken Sie auf den Pfeil, um die entgegengesetzte Auswahl treffen.

    Möglicherweise müssen Sie ein Element, um alle untergeordneten finden Sie unter erweitern. Sie müssen das übergeordnete aktivieren, wenn eine der untergeordneten Elemente aktiviert sind.

    **Hinweis**  
    Sie können nicht wiederhergestellt oder entfernt ein Windows-Feature für Features bei Bedarf mit einer Antwortdatei.

6.  Klicken Sie im Hauptmenü auf **Extras** , und klicken Sie dann auf **Antwortdatei überprüfen**.

7.  Korrigieren Sie etwaige Fehler, die im Bereich **Meldungen** angezeigt werden, und speichern Sie die Antwortdatei.

8.  Geben Sie an der Befehlszeile den folgenden Befehl aus, um die Antwortdatei auf das Bild anzuwenden.

    ``` syntax
    Dism /online /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    Wenn Sie ein Abbild offline warten, geben Sie den Speicherort des Verzeichnisses bereitgestellten Abbild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

## <a name="to-commit-changes-on-an-offline-image"></a>Klicken Sie auf ein offline-Abbild Commits

-   Commit der Änderungen, und deaktivieren Sie das Bild. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

[Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md)

 

 






