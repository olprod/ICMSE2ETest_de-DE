---
author: Justinha
Description: "Hinzufügen von Gerätetreibern Windows während der Installation von Windows"
ms.assetid: adb22778-06a2-493a-81de-3a1306a0b208
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Gerätetreibern Windows während der Installation von Windows"
ms.openlocfilehash: 22d78edfc2a2c180044a89d3fc5420460657dc2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-device-drivers-to-windows-during-windows-setup"></a>Hinzufügen von Gerätetreibern Windows während der Installation von Windows


Zum Installieren von Windows® auf einigen Entwürfen Hardware müssen Sie möglicherweise Windows Setup Gerätetreiber hinzugefügt. Hinzufügen von Treibern zu Windows Setup mithilfe einer Antwortdatei, die den Pfad zu der Treiberdateien angibt. Zu diesem Zweck in neuen Installationen fügen Sie die Komponente Microsoft-Windows-PnpCustomizationWinPE während des [WindowsPE](windowspe.md) Konfiguration Schritts, fügen Sie die Treiberpfade und geben Sie dann die Antwortdatei.

Sie können auch ändern vorhandene Bilder und hinzufügen und Entfernen von Treibern. Sie können offline Bilder auf unterschiedliche Weise bedienen. Angenommen, können Sie fügen Sie die Microsoft-Windows-PnpCustomizationsNonWinPE Komponente der in der Phase der [OfflineServicing](offlineservicing.md) -Konfiguration hinzufügen oder entfernen Sie die Treiberpfade und geben Sie den Namen der Antwortdatei. Weitere Informationen dazu, wie Sie auf ein offline-Windows-Abbild Treiber mithilfe einer Antwortdatei und auch anderer Methoden zum Hinzufügen, und Entfernen von Treiber aus einer vorhandenen Bild ändern finden Sie unter [Hinzufügen und Entfernen der Treiber, die ein Offline-Windows-Abbild](add-and-remove-drivers-to-an-offline-windows-image.md).

## <a name="span-idbkmk1spanspan-idbkmk1span-add-drivers-to-new-installations-windowspe"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Hinzufügen von Treibern zu neuen Installationen (WindowsPE)


Fügen Sie für neue Installationen Treiber während des [WindowsPE](windowspe.md) Konfiguration Schritts hinzu.

Diese Methode initialisiert Windows Vorinstallation Environment (Windows PE) und verarbeitet Windows PE Einstellungen aus der Antwortdatei wie folgt:

1.  Windows-Stufen der Windows PE-Treiber im RAM Treiber speichern. Windows lädt wichtige Treibern, die Windows PE benötigt Zugriff auf den lokalen Datenträger und Netzwerk. Wenn Sie mit der rechten **DevicePaths Maustaste** und **Einfügen von neuen Wert für PathAndCredentials mit Windows PE**auswählen, verarbeitet Windows PE andere Windows PE Anpassungen, die die Antwortdatei angibt.

2.  Die Windows-Setupvorgang gilt das Windows-Abbild. Treiber erforderliche werden auf dem Windows-Abbild angezeigt, vor dem Setup das Abbild installiert. Andere Faktoren, die Sie dem Windows PE-Treiberspeicher hinzugefügt werden im Windows-Bild Driver Store angezeigt. Wenn Windows Setup die Pass [OfflineServicing](offlineservicing.md) verarbeitet, fügt Windows Setup Treiber, die den Pfad des Treibers angibt auch an den Windows-Bild-Treiber Store.

**So fügen Sie eine Gerätetreiber während des Schritts WindowsPE hinzu**

1.  Verwenden Sie Windows System Image Manager (Windows SIM) zum Erstellen einer Antwortdatei enthält, das die Pfade zu Gerätetreiber, die Sie installieren möchten.

2.  Fügen Sie der Komponente **Microsoft-Windows-PnpCustomizationsWinPE** zu Ihrer Antwortdatei im Durchgang [WindowsPE](windowspe.md) Konfiguration.

3.  Erweitern Sie den **Microsoft-Windows-PnpCustomizationsWinPE** Knoten in die Antwortdatei ein. Mit der rechten Maustaste **DevicePaths**ein, und wählen Sie dann den **Neuen Wert für PathAndCredentials einfügen**.

    Ein neuer **Wert für PathAndCredentials** Listeneintrag wird angezeigt.

4.  Fügen Sie für jeden Standort, auf die Sie zugreifen, ein separates Listenelement **vom Typ PathAndCredentials** hinzu.

    Sie können mehrere Geräte Treiberpfade einschließen, indem mehrere **Wert für PathAndCredentials** Listenelemente hinzufügen. Wenn Sie mehrere Listenelemente hinzufügen, erhöhen Sie die `Key` Wert für die einzelnen Pfade. Beispielsweise, wenn Sie zwei separate Treiberpfade hinzufügen, verwendet der erste Pfad der `Key` Wert der `1`, und der zweite Pfad verwendet die `Key` Wert der `2`.

5.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM. Die Antwortdatei muss dem folgenden Beispiel ähneln:

    ``` syntax
    <?xml version="1.0" encoding="utf-8" ?> 
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
       <settings pass="windowsPE">
          <component name="Microsoft-Windows-PnpCustomizationsWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1" wcm:action="add">
                   <Credentials>
                      <Domain>Fabrikam</Domain> 
                      <Password>MyPassword</Password> 
                      <Username>MyUserName</Username> 
                   </Credentials>
                   <Path>\\server\share\drivers</Path> 
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

6.  Starten Sie Windows PE.

7.  Führen Sie an einer Eingabeaufforderung Setup. Geben Sie den Namen der Antwortdatei ein. Beispiel:

    ``` syntax
    Setup /unattend:C:\unattend.xml
    ```

    Windows Setup fügt Treiber in der \\ \\Server\\freigeben\\Treiber Pfad für die während der Installation.

Weitere Informationen zu Treibern finden Sie unter [Gerätetreiber und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md) und [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md). Weitere Informationen zu Windows-Komponenten finden Sie unter [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Starten Sie von einer DVD](boot-from-a-dvd.md)

[Bereitstellen eines benutzerdefinierten Abbilds](deploy-a-custom-image.md)

[Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

[Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

[Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md)

 

 






