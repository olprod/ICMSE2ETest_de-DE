---
author: Justinha
Description: "Hinzufügen eines Treibers Online im Überwachungsmodus"
ms.assetid: 3b7e2d24-4bd4-4ca3-8e6f-2bd771ebab3b
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen eines Treibers Online im Überwachungsmodus"
ms.openlocfilehash: 90b76852f2a72c84958d469745df29911773c9ac
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-driver-online-in-audit-mode"></a>Hinzufügen eines Treibers Online im Überwachungsmodus


Eine Antwortdatei können zum Automatisieren der Installations von Gerätetreibern beim Start des Computers im Überwachungsmodus aktiviert ist.

## <a name="span-idbkmk2spanspan-idbkmk2spanadding-a-device-driver"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Hinzufügen eines Gerätetreibers


Die [AuditSystem](auditsystem.md) Durchlauf Prozesse unbeaufsichtigten Setup Konfigurationseinstellungen während Windows im Kontext des System, bevor ein Benutzer anmeldet, an dem Computer im Überwachungsmodus ausgeführt wird. Übergeben Sie die **AuditSystem** Konfiguration führt nur dann, wenn der Computer im Überwachungsmodus gestartet wurde. Gerätetreiber hinzufügen, der in der Phase der **AuditSystem** Konfiguration, die Antwortdatei im Durchgang **AuditSystem** Konfiguration die Komponente [Microsoft-Windows-PnpCustomizationsNonWinPE](https://msdn.microsoft.com/library/windows/hardware/dn923009) hinzugefügt, und geben Sie den Pfad für jeden Gerätetreiber. Starten von Windows nach dem Ausführen von Setup im Überwachungsmodus aktiviert. Führen Sie den Befehl **Sysprep** mit der **Option/audit** so konfigurieren Sie den Computer im Überwachungsmodus aktiviert das nächste Mal gestartet wird, das es gestartet wird. Oder in die Antwortdatei konfigurieren Sie die Microsoft-Windows-Deployment\\Reseal\\ `Mode` zu **überwachenden**festlegen. Weitere Informationen finden Sie unter [Referenz für unbeaufsichtigte Windows](https://msdn.microsoft.com/library/windows/hardware/dn923277).

### <a name="span-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanspan-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanspan-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanto-add-a-device-driver-during-the-auditsystem-configuration-pass"></a><span id="To_add_a_device_driver_during_the_auditSystem_configuration_pass"></span><span id="to_add_a_device_driver_during_the_auditsystem_configuration_pass"></span><span id="TO_ADD_A_DEVICE_DRIVER_DURING_THE_AUDITSYSTEM_CONFIGURATION_PASS"></span>So fügen Sie Gerätetreiber während des AuditSystem Konfiguration Schritts hinzu

1.  Suchen Sie die INF-Dateien, die Sie im Überwachungsmodus für den Gerätetreiber installieren möchten.

2.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**, und wählen Sie dann **Windows System Image Manager**.

3.  Öffnen Sie die Antwortdatei, und erweitern Sie den Knoten **Komponenten** , um die verfügbare Einstellungen anzeigen.

4.  Fügen Sie die Komponente Microsoft-Windows-PnpCustomizationsNonWinPE zu Ihrer Antwortdatei im **AuditSystem** Konfiguration Durchgang.

5.  Erweitern Sie den Knoten **Microsoft-Windows-PnpCustomizationsNonWinPE** in die Antwortdatei ein. Mit der rechten Maustaste **DevicePaths**, und klicken Sie dann auf **Neuen Wert für PathAndCredentials einfügen**.

    Ein neuer **Wert für PathAndCredentials** Listeneintrag wird angezeigt.

6.  Fügen Sie für jeden Standort, auf die Sie zugreifen, ein separates Listenelement **vom Typ PathAndCredentials** hinzu.

7.  Geben Sie den Pfad der Gerätetreiber und die Anmeldeinformationen, die verwendet werden, auf die Datei zuzugreifen, wenn die Datei auf einer Netzwerkfreigabe befindet, in der Microsoft-Windows-PnpCustomizationsNonWinPE-Komponente.

    **Hinweis**  
    Sie können mehrere Gerätetreiber Pfade einschließen, indem mehrere **Wert für PathAndCredentials** Listenelemente hinzufügen. Wenn Sie mehrere Listenelemente hinzufügen, erhöhen Sie den Wert der `Key` für die einzelnen Pfade. Beispielsweise, wenn Sie zwei separate Treiberpfade hinzufügen, verwendet der erste Pfad der `Key` Wert **1**und der zweite Pfad verwendet die `Key` Wert von **2**.

     

8.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM. Die Antwortdatei muss in diesem Beispiel ähneln:

    ``` syntax
    <?xml version="1.0" encoding="utf-8" ?> 
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
       <settings pass="auditSystem">
          <component name="Microsoft-Windows-PnpCustomizationsNonWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1" wcm:action="add">
                   <Credentials>
                      <Domain>Fabrikam</Domain> 
                      <Password>MyPassword</Password> 
                      <Username>MyUserName</Username> 
                   </Credentials>
                   <Path>\\networkshare\share\drivers</Path> 
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

9.  In Windows Vorinstallation Environment (Windows PE) starten Sie, führen Sie Setup aus, und geben Sie den Namen der Antwortdatei. Beispiel:

    ``` syntax
    Setup /unattend:C:\unattend.xml
    ```

    Die angegebenen Antwortdatei wird an das System zwischengespeichert, damit Sie der Computer bei der Ausführung im Überwachungsmodus Einstellungen in die Antwortdatei gilt.

    Setup abgeschlossen ist.

10. Führen Sie den Befehl **Sysprep** mit der **Option/audit** so konfigurieren Sie den Computer im Überwachungsmodus aktiviert das nächste Mal gestartet wird, das es gestartet wird. Beispiel:

    ``` syntax
    Sysprep /audit /reboot
    ```

    Beim Neustart von Windows im Überwachungsmodus werden Gerätetreiber, die Sie in die Antwortdatei angegeben hinzugefügt.

Mit dem Tool PNPUtil können Sie hinzufügen oder entfernen und Aufzählen von Treibern auf einem Betriebssystem ausgeführt wird. Weitere Informationen zur Verwendung von PNPUtil zum Hinzufügen oder Entfernen von Plug & Play-Treiber finden Sie unter [Installieren eines Plug & Play-Geräts](http://go.microsoft.com/fwlink/?LinkId=139151).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Gerätetreibern und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)

[Hinzufügen und Entfernen von Treibern zu einem Offline-Windows-Bild](add-and-remove-drivers-to-an-offline-windows-image.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

 

 






