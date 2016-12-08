---
Description: "Dieser Abschnitt zeigt, wie ein fiktives Treiber und eine MCSF Anpassung Einstellung als Teil des Pakets hinzufügen."
ms.assetid: 9d776681-9006-4dd5-b69e-fb195a888f7d
MSHAttr: PreferredLib:/library
author: CelesteDG
title: Erstellen von mobilen Pakete
ms.openlocfilehash: c3856aad95d10845253e58b85ca6a100059c5419
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-mobile-packages"></a>Erstellen von mobilen Pakete


In Windows 10 Mobile Pakete bilden die Bausteine für das Betriebssystem, und sie können alle Dateien, Bibliotheken, registrierungseinstellungen, ausführbare Dateien, und die Daten auf dem mobilen Gerät enthalten. Jede Komponente OS, von Gerätetreiber-Systemdateien, muss in einem Paket enthalten sein.

Als OEM Wenn Sie gerätespezifischen Treiber oder Anpassungen, die Sie für das Betriebssystem hinzufügen möchten müssen Sie ein Paket zu erstellen. In diesem Abschnitt zeigt, wie ein fiktives Treiber und eine MCSF Anpassung Einstellung als Teil des Pakets hinzufügen.

Ausführlichere Informationen zu mobilen Pakete, einschließlich der Angabe von anderen Komponenten und Zusammenführen von Paket finden Sie unter [Erstellen von mobilen Pakete](https://msdn.microsoft.com/library/dn756642).

### <a name="span-idaddadrivercomponentspanspan-idaddadrivercomponentspanadd-a-driver-component"></a><span id="add_a_driver_component"></span><span id="ADD_A_DRIVER_COMPONENT"></span>Hinzufügen einer Treiberkomponente

Erfahren mehr über Treiber und erste Schritte mit Schreiben eigene, finden Sie unter [Gerät und Treiber-Technologien](https://msdn.microsoft.com/library/windows/hardware/ff557557).

In dieser exemplarischen Vorgehensweise wir den Beispiel Echo KMDF Treiber Dateien herunterladen konvertieren in eine universelle Windows-Treiber, und klicken Sie dann mithilfe von Visual Studio eine Paketdatei erstellen.

**So fügen Sie einen Treiber hinzu**

1.  Laden Sie das Echo universelle Treiber Sample.

    1.  Laden Sie die Datei master.zip und speichern Sie sie in der lokalen Festplatte: <https://github.com/microsoft/windows-driver-samples/archive/master.zip>.

    2.  Extrahieren Sie den Inhalt der master.zip-Datei. Geben Sie einen neuen Ordner, z. B. *C:\\DriverSamples*, oder Durchsuchen, um eine vorhandene zum Speichern der extrahierten Dateien.

    3.  Nachdem die Dateien extrahiert wurden, fahren Sie mit den allgemeinen\\Echo\\Kmdf Unterordner innerhalb des Ordners, in dem Sie die extrahierten Dateien die Lösung Treibers für das Echo Treiber Beispiel suchen gespeichert. Beispiel: bei der Erstellung einer *C:\\DriverSamples* Ordner im vorherigen Schritt, suchen Sie die Projektmappe Treiber unter *C:\\DriverSamples\\allgemeine\\Echo\\Kmdf*.

2.  Das vorhandene Echo-Treiber Projekt mit einem universellen Windows-Treiber Projekt zu konvertieren.

    1.  Öffnen Sie in Visual Studio 2015 die vorhandenen Kmdfecho Treiber Project, kmdfecho.sln.

    2.  Speicherort im Projektmappen-Explorer in Visual Studio. Klicken Sie im Bereich Projektmappen-Explorer mit der rechten Maustaste auf **die Lösung 'Kmdfecho' (3 Projekte)** , und wählen Sie **Konfigurations-Manager**.

    3.  Klicken Sie im **Konfigurations-Manager** auf **Windows 10**festgelegt das Betriebssystem.

    4.  Mit der rechten Maustaste auf das Projekt Treiber, und wählen Sie dann **Eigenschaften**aus. Klicken Sie unter **Configuration Manager** &gt; **Treiber**, überprüfen, ob der **Zielplattform** in **Universal**festgelegt ist.

        Andere Optionen in **Zielplattform** zählen **Mobile**. Sie können diese Option auswählen, wenn Sie möchten einen Treiber erstellen, der nur auf Windows 10 Mobile ausgeführt wird.

3.  Visual Studio 2015 verwenden Sie PkgGen zum Generieren einer Package-Datei.

    1.  Mit der rechten Maustaste auf das Projekt Treiber, und wählen Sie **Hinzufügen**-&gt;**Neues Element**.

    2.  Klicken Sie unter **Visual C++** &gt; **Windows-Treiber**, wählen Sie **Package Manifest**, und klicken Sie dann auf **Hinzufügen**.

        Visual Studio fügt eine Datei namens Package.pkg.xml Sie Ihrem Projekt Treiber. Sie können mit der rechten Maustaste auf die Datei und wählen Sie **Eigenschaften** , um sicherzustellen, dass der Elementtyp auf **PkgGen**festgelegt ist. Auf der gleichen Eigenschaftenseite können Sie **aus Build ausgeschlossen** auf **Ja** festlegen, wenn Sie später entscheiden, dass Sie dieses Projekt Treiber erstellen und eine Package-Datei zu generieren möchten.

    3.  Klicken Sie auf **OK**.

    4.  Mit der rechten Maustaste auf das Projekt Treiber, und wählen Sie **Eigenschaften**. Klicken Sie unter **Konfigurationseigenschaften**öffnen Sie den Knoten **PackageGen** , und ändern Sie die **Version** auf eine einen beliebigen Wert aus, der Sie. Beispielsweise können Sie die Version auf *1.0.0.0*festlegen.

    5.  Legen Sie das Paket **Eigentümer**, **Komponente**und **CMYK** -Werte.

4.  Mit der rechten Maustaste auf das Projekt Treiber, und wählen Sie **Eigenschaften**. Legen Sie die Testzertifikate auf eines der OEM Testzertifikate verwenden, die installiert wurde, wenn Sie installoemcerts.cmd ausgeführt haben.

    Sie können beispielsweise CN = Windows Phone OEM Root (TEST NUR 2013).

5.  Speichern Sie Ihre Arbeit, und starten Sie Visual Studio als Administrator.

6.  Erstellen Sie den Treiber. Visual Studio gegen die erforderlichen Bibliotheken verknüpft und generiert eine CAT-Datei, eine INF-Datei, einen binären Treiber und eine .spkg-Datei.

    Nachdem der Treiber integriert ist, sollten Sie einen neuen Ordner mit dem Namen *Projektname*.spkg, die der CAB enthält und die .spkg sehen.

    Wir verwenden die .spkg Treiber, die Sie in dieser exemplarischen Vorgehensweise erstellt und der Kombination mit der .spkg aus der nächsten exemplarischen Vorgehensweise zum Erstellen einer mobilen Betriebssystemabbilds.

Informationen über das Ausführen von PkgGen.exe außerhalb von Visual Studio finden Sie im nächsten Abschnitt zum Hinzufügen von eine Einstellung für die Anpassung. Außerdem finden Sie im Abschnitt *Führen Sie das Tool pkggen.exe* [Erstellen von mobilen Pakete](https://msdn.microsoft.com/library/dn756642).

### <a name="span-idaddanmcsfcustomizationsettingspanspan-idaddanmcsfcustomizationsettingspanadd-an-mcsf-customization-setting"></a><span id="add_an_mcsf_customization_setting"></span><span id="ADD_AN_MCSF_CUSTOMIZATION_SETTING"></span>Fügen Sie eine MCSF Anpassung-Einstellung

In Windows 10 Mobile stehen die folgenden beiden unterstützten Anpassung Frameworks: verwaltete zentralisierte Einstellungen Framework (MCSF) und Windows-Bereitstellung. Weitere Informationen zu diesen Frameworks finden Sie unter [Anpassungen für mobile Geräte](https://msdn.microsoft.com/library/windows/hardware/mt481438). Wenn es darum geht, eine benutzerdefinierte Einstellung der OEM-Anpassung hinzufügen, ist nur MCSF erweiterbare und für OEMs eigene verschiedene mobilen OS Einstellungen in eine einfache und einheitliche Möglichkeit zu deklarieren, die an den Microsoft-Anpassung Einstellungen ähnlich ist verfügbar.

Erfahren Sie, wie Sie MCSF und das Paket XML-Schema zum Deklarieren und auf benutzerdefinierte OEM-Einstellungen zugreifen, finden Sie in den Abschnitten in [Verwalteten zentralisierte Einstellungen Framework (MCSF)](https://msdn.microsoft.com/library/windows/hardware/dn772150).

In dieser exemplarischen Vorgehensweise sind wir erweitern, um die Anpassung [für schnelles konfigurieren Aktionen](https://msdn.microsoft.com/library/windows/hardware/dn757416) , um das Schema MCSF verwenden, um eine richtlinieneinstellung für die zu erstellen, die die verschiedenen Steckplätze verfügbar macht, damit sie auf einfache Weise später konfiguriert werden können ohne die Registrierungsschlüssel und Werte merken müssen. Zu diesem Zweck fügen wir die Richtlinie Einstellungen-Deklarationen in einer. pkg.xml-Datei und dann Build dieser Datei wird in ein Paket zu erstellen.

**So fügen Sie eine Einstellung für die Anpassung hinzu**

1.  Schreiben Sie MCSF-Einstellung, die entspricht, in den folgenden Registrierungsschlüssel:

    ``` syntax
    $(HKLM.SOFTWARE)\Microsoft\Shell\OEM\QuickActions\Slot\X
    Type:  REG_SZ
    Possible values:  
       Microsoft.QuickAction.AllSettings
       Microsoft.QuickAction.Connect
       Microsoft.QuickAction.Note
       Microsoft.QuickAction.Flashlight
       Microsoft.QuickAction.RotationLock
       Microsoft.QuickAction.BatterySaver
       Microsoft.QuickAction.Bluetooth
       Microsoft.QuickAction.WiFi
       Microsoft.QuickAction.AirplaneMode
       Microsoft.QuickAction.Vpn
       Microsoft.QuickAction.Cellular
       Microsoft.QuickAction.MobileHotspot
       Microsoft.QuickAction.Camera
       Microsoft.QuickAction.Brightness
       Microsoft.QuickAction.QuietHours
       Microsoft.QuickAction.Location
    ```

    Die *X* im Registrierungsschlüssel sollte mit der konfigurierten Steckplatznummer (beginnend mit 1) ersetzt werden. Slots sind rechts-nach-links-sortiert. Es ist ein Maximum von 5 Steckplätze auf einem mobilen Gerät großen Bildschirm während mobile Geräte ohne einem großen Bildschirm 4 Steckplätze haben.

    Im folgenden Codebeispiel wird veranschaulicht, wie die MCSF Richtlinieneinstellungen für die schnellen Aktionen deklariert werden können:

    ``` syntax
        <SettingsGroup Path="Notifications/QuickActions">  
          <!-- Default Quick actions configuration -->  
          <Setting Name="QuickActionSlot1" Description="App to place in quick action slot 1.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\1" Type="REG_SZ" Default="Microsoft.QuickAction.AllSettings" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting>  
          <Setting Name="QuickActionSlot2" Description="App to place in quick action slot 2.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\2" Type="REG_SZ" Default="Microsoft.QuickAction.RotationLock" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>     
          </Setting> 
          <Setting Name="QuickActionSlot3" Description="App to place in quick action slot 3.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\3" Type="REG_SZ" Default="Microsoft.QuickAction.Bluetooth" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot4" Description="App to place in quick action slot 4.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\4" Type="REG_SZ" Default="Microsoft.QuickAction.WiFi" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot5" Description="App to place in quick action slot 5.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\5" Type="REG_SZ" Default="Microsoft.QuickAction.Camera" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
        </SettingsGroup>
    ```

2.  Erstellen einer. pkg.xml Datei, und fügen Sie die Richtlinien im vorherigen Schritt auf der. pkg.xml Datei. Im folgenden Beispiel wird gezeigt, wie dazu.

    ```XML
    <?xml version="1.0" encoding="utf-8">
    <Package xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"
      Owner=""
      Component=""
      SubComponent=""
      OwnerType="OEM"
      ReleaseType="">
       <Components>
        <SettingsGroup Path="Notifications/QuickActions">  
          <!-- Default Quick actions configuration -->  
          <Setting Name="QuickActionSlot1" Description="App to place in quick action slot 1.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\1" Type="REG_SZ" Default="Microsoft.QuickAction.AllSettings" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting>  
          <Setting Name="QuickActionSlot2" Description="App to place in quick action slot 2.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\2" Type="REG_SZ" Default="Microsoft.QuickAction.RotationLock" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>     
          </Setting> 
          <Setting Name="QuickActionSlot3" Description="App to place in quick action slot 3.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\3" Type="REG_SZ" Default="Microsoft.QuickAction.Bluetooth" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot4" Description="App to place in quick action slot 4.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\4" Type="REG_SZ" Default="Microsoft.QuickAction.WiFi" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot5" Description="App to place in quick action slot 5.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\5" Type="REG_SZ" Default="Microsoft.QuickAction.Camera" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
        </SettingsGroup>
       </Components>
    </Package>
    ```

3.  Fügen Sie Werte für die **Besitzer-**, **Component**, **SubComponent**und **ReleaseType** Elemente hinzu. Beispiel:

    -   **Besitzer**= "Contoso"
    -   **Komponente**= "Customization.Notifications"
    -   **CMYK**= "QuickActions"
    -   **ReleaseType**= "Test"

    Weitere Informationen zu den Elementen und Attributen finden Sie unter [primäre Elemente und Attribute einer Projektdatei Paket](https://msdn.microsoft.com/library/dn756796).

4.  Benennen und speichern Sie die. pkg.xml Datei als "QuickActions.pkg.xml".

5.  Generieren Sie ein Paket oder mit der "QuickActions.pkg.xml".spkg-Datei als Eingabe. Weitere Informationen finden Sie unter *Ausführen des Tools pkggen.exe* in [mobilen Paketen erstellen](https://msdn.microsoft.com/library/dn756642).

    **Ein Paket mit QuickActions.pkg.xml generieren**

    1.  Öffnen Sie eine Befehlszeile mit Administratorrechten.

    2.  Geben Sie den folgenden Befehl zum Erstellen eines Pakets aus QuickActions.pkg.xml aus.

        **PkgGen QuickActions.pkg.xml /config:"%WPDKCONTENTROOT%\\Tools\\Bin\\i386\\pkggen.cfg.xml"**

        Mit diesem Befehl wird ein Paket aufgerufen Customization.Notifications.QuickActions.spkg generiert. Im nächsten Abschnitt wir verwenden Sie dieses Paket und einer Featuremanifestdatei hinzugefügt.

 

 



