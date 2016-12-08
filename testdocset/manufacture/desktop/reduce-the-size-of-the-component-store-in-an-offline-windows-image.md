---
author: Justinha
Description: "Verringern Sie die Größe des Speichers Komponente in einem Offline-Windows-Bild"
ms.assetid: 2cdff215-30b9-4360-9e2c-cc2c3d695608
MSHAttr: PreferredLib:/library/windows/hardware
title: "Verringern Sie die Größe des Speichers Komponente in einem Offline-Windows-Bild"
ms.openlocfilehash: 04ace359dbb7f5755977318ae001d460cdb20b76
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reduce-the-size-of-the-component-store-in-an-offline-windows-image"></a>Verringern Sie die Größe des Speichers Komponente in einem Offline-Windows-Bild


Das Tool Deployment Image Servicing and Management (DISM) können Sie ein Windows-Abbild aus einer Datei WIM, VHD oder VHDX bereitstellen und ändern.

## <a name="span-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespanspan-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespanspan-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespananalyze-and-clean-up-the-component-store-winsxs-folder-in-an-offline-windows-image"></a><span id="Analyze_and_clean_up_the_Component_Store__WinSxS_folder__in_an_offline_Windows_image"></span><span id="analyze_and_clean_up_the_component_store__winsxs_folder__in_an_offline_windows_image"></span><span id="ANALYZE_AND_CLEAN_UP_THE_COMPONENT_STORE__WINSXS_FOLDER__IN_AN_OFFLINE_WINDOWS_IMAGE"></span>Analysieren Sie und bereinigen Sie die Komponente Store (Ordner WinSxS) in einem offline Windows-Bild


Zum Ausführen der exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Computer unter Windows 10, 8.1 Windows, Windows 8, Windows 7, Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 mit der Windows 8.1-Version von Windows ADK Tools installiert ist.

-   Eine WIM-, VHD- oder .vhdx-Datei eines Bilds Windows 10 oder Windows Server 2016 – Technische Vorschau.

**Analysieren der Größe des Speichers Komponente in einem offline-Windows-Bild**

1.  Kopieren Sie eine WIM-Datei, eine VHD- oder eine .vhdx, die auf dem lokalen Laufwerk ein Windows-Abbild enthält. Beispielsweise C:\\testen\\Bilder.

2.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

3.  Erstellen Sie einen Ordner für das bereitgestellte Abbild. Beispielsweise C:\\testen\\offline.

4.  Führen Sie den Befehl **DISM /Get-ImageInfo** zum Abrufen der Name oder die Indexnummer für das Bild, das Sie aktualisieren möchten. Beispiel:

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\MyImage.wim
    ```

5.  Stellen Sie das Windows-Abbild. Beispiel:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /Index:1 /MountDir:C:\test\offline
    ```

    Da WIM-Dateien ein oder mehrere Bilder enthalten können, müssen Sie einen Index oder Name-Wert angeben. Um ein Bild aus einer virtuellen Festplatte bereitzustellen, müssen Sie angeben `/Index:1`.

6.  Analysieren Sie die Größe des Speichers Komponente. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /AnalyzeComponentStore
    ```

    Um die verschiedenen Werte in die Anzeige zu verstehen, finden Sie unter [Determine die tatsächliche Größe des Ordners WinSxS](determine-the-actual-size-of-the-winsxs-folder.md).

7.  Wenn die Komponente Store Bereinigung im angezeigten Bericht empfohlen wurde, können Sie die Bereinigung des Bilds starten. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /StartComponentCleanup
    ```

8.  Sie können die Größe des Speichers Komponente weiter reduzieren, indem der /ResetBase-Parameter hinzufügen. Beispiel:

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /StartComponentCleanup /ResetBase
    ```
    
    Beginnend mit Windows 10, Version 1607 verwenden, können Sie mit /Resetbase verzögern langer Cleanup Vorgänge auf die nächste automatische Verwaltung den /Defer-Parameter angeben. Es wird jedoch dringend empfohlen Sie **nur** als eine Option in der Factory, in denen DISM /Resetbase erfordert mehr als 30 Minuten, /Defer verwenden. 
   
    Wartung wird wöchentlich, mit einem zwei Wochen Stichtag Ausführung geplant.  In der ersten Woche wird die Wartungsaufgabe nur während im Leerlauf Wartungsfenster System ausgeführt.  Wenn nicht abgeschlossen werden (beispielsweise der Computer ist ausgeschaltet wann nicht in Verwendung) und klicken Sie dann der Taskplaner häufiger ausgeführt wird und die Aufgabe möglicherweise ausgeführt, während das System nicht im Leerlauf ist.
 
    Um die Leistung Effekte finden Sie unter während der Task ausgeführt wird, klicken Sie auf Start > ausführen, und geben Sie den folgenden Befehl ein:
    
    ```syntax
    Schtasks.exe /Run /I /TN \Microsoft\Windows\Servicing\StartComponentCleanup
    ```
    
9.  Commit die Änderungen und hebt die Bereitstellung des Bilds, um die Änderungen zu speichern, die Sie vorgenommen haben. Beispiel:

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Verwalten der Komponente Store](manage-the-component-store.md)

[Bereinigen des Ordners WinSxS](clean-up-the-winsxs-folder.md)

[Bestimmen Sie die tatsächliche Größe des Ordners WinSxS](determine-the-actual-size-of-the-winsxs-folder.md)

[Wo ist mein Space? (Blogbeitrag)](http://blogs.technet.com/b/askcore/archive/2013/03/01/where-did-my-space-go.aspx)

[NTFS-Metadateien Blogbeitrag](http://blogs.technet.com/b/askcore/archive/2009/12/30/ntfs-metafiles.aspx)

[Zeigt, wie Sie zum Erstellen und Bearbeiten von NTFS-Verknüpfung](http://support.microsoft.com/kb/205524)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

 

 






