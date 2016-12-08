---
Description: "Der Windows Imaging und Konfiguration Designer (ICD)-Befehlszeilenschnittstelle (CLI) können Sie um ein neues Windows 10 Mobile Bild zu generieren."
ms.assetid: 941023d3-14d5-415f-817b-a48ac2a4ec87
MSHAttr: PreferredLib:/library
title: Verwenden der Windows-ICD CLI anpassen und Erstellen einer mobilen Bild
author: CelesteDG
ms.openlocfilehash: f8c138400079c3a4e5abc05e1b24cdbb1ccca693
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-windows-icd-cli-to-customize-and-build-a-mobile-image"></a>Verwenden der Windows-ICD CLI anpassen und Erstellen einer mobilen Bild


Windows Imaging und Konfiguration Designer (ICD) Befehlszeilen-Schnittstelle (CLI) können Sie um ein neues Windows 10 Mobile Bild zu generieren.

Diese imaging-Methode erfordert eine vorinstallierte OS Kit müssen Sie alle notwendigen Microsoft OS Pakete und Features in Ihrem standardmäßigen Manifestdateien verfügen Installationspfad. Benötigen Sie außerdem entweder eine BSP.config.xml-Datei, die Informationen über die Hardware-Komponente-Pakete für Ihre Pinnwand Support-Paket (BSP) enthält, oder Sie können eine OEMInput.xml-Datei verwenden.

Wenn Sie eine Datei BSP.config.xml verwenden, können Sie folgende Schritte ausführen:

-   Verwenden Sie die BSP.config.xml-Datei, die Sie heruntergeladen haben als Teil der BSP-Kit, oder

-   Generieren Sie Ihre eigene BSP.config.xml durch Ausführen von das BSP Kit Konfigurationstools SoC dessen Hersteller und die Komponententreiber auswählen.

## <a name="span-idcreateawpafwithmultivariantsupportspanspan-idcreateawpafwithmultivariantsupportspanspan-idcreateawpafwithmultivariantsupportspancreate-a-wpaf-with-multivariant-support"></a><span id="Create_a_WPAF_with_multivariant_support"></span><span id="create_a_wpaf_with_multivariant_support"></span><span id="CREATE_A_WPAF_WITH_MULTIVARIANT_SUPPORT"></span>Erstellen Sie eine WPAF mit multivariant-Unterstützung


Multivariant stellt einen generischen Mechanismus für die Erstellung eines einzelnen Bilds, das für mehrere Märkte arbeiten kann. Es können Sie die Sprache, branding und Netzwerkeinstellungen dynamisch während der Laufzeit basierend auf der Mobilfunkbetreiber und Gebietsschema Land/konfigurieren.

Im Gegensatz zu Benutzeroberfläche ICD von Windows können Sie die Windows ICD CLI zu verwenden, ein Bild zu erstellen, das multivariant unterstützt. Zu diesem Zweck müssen Sie zuerst eine Antwortdatei Windows-Bereitstellung (WPAF), bearbeiten customizations.xml, und fügen Sie die **Ziele** und **Variant** Abschnitte in der Datei. [Erstellen einer Bereitstellung Paket mit multivariant Einstellungen](https://msdn.microsoft.com/library/windows/hardware/dn916108) bietet eine weitere Informationen zur multivariant-Unterstützung in Windows 10 und eine Liste der Bedingungen, die zusammen mit ihren Prioritäten unterstützt. Darüber hinaus ein schrittweises Beispiel auf die erforderlich ist.

In diesem Abschnitt wird nun die Datei customizations.xml geändert, die aus der [Verwendung der Windows-ICD-Benutzeroberfläche anpassen und Erstellen einer mobilen Bild](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md) erstellt wurde und **Ziele** und **Variant** Abschnitte zur Unterstützung der Multivariant einschließen. Wenn Sie ein einzelnes variant Bild entwickeln, können Sie diesen Abschnitt überspringen.

1.  Suchen nach der Bereitstellung Paketdatei customizations.xml. Wenn Sie den Standardspeicherort für das Projekt nicht ändern, finden Sie das Paket in * &lt;Laufwerk:&gt;*\\Benutzer\\*&lt;Benutzer\_Namen&gt;*\\Dokumente\\Windows Imaging und Konfiguration Designer (WICD)\\*&lt;Projekt\_Namen&gt;*.

2.  Verwenden Sie zum Öffnen der Datei customizations.xml einen XML- oder Text-Editor.

    Das folgende Beispiel zeigt den Inhalt der Datei customizations.xml verwendet [Die Windows-ICD-Benutzeroberfläche zum Anpassen und Erstellen einer mobilen Abbilds](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md)erstellt.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

3.  Bearbeiten Sie die Datei customizations.xml und Erstellen eines Abschnitts **Ziele** , um die Bedingungen zu beschreiben, die Ihre multivariant Einstellungen behandelt.

    Das folgende Beispiel zeigt die customizations.xml, die Einbeziehung der Bedingung **MCC** und **MNC**geändert wurde. Für die Parität verwendet das Beispiel die gleichen fiktiven-IDs und Bedingungen, die verwendet wurden im Abschnitt *Erstellen einer Antwort MCSF-Anpassungsdatei* in [Configure Customization Einstellungen](configure-customization-settings.md)an.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

4.  Erstellen Sie in der Datei customizations.xml zwei Abschnitte **Variant** aus:

    1.  Geben Sie einen **Namen** für jeden Variant-Wert.

    2.  Fügen Sie ein untergeordnetes **TargetRefs** -Element hinzu.

    3.  Fügen Sie innerhalb des Elements **TargetRefs** ein **TargetRef** -Element hinzu.

    Im folgenden Beispiel wird zeigt, was die customizations.xml aussieht, nach dem Hinzufügen von zwei Varianten, ThePhoneCompany und Fabrikam, und klicken Sie dann mithilfe der zwei **Ziel-Id**s definierte im vorherigen Schritt für jede Variante als **TargetRef Id** verwenden.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
          <Variant Name="ThePhoneCompany"> 
            <TargetRefs> 
              <TargetRef Id="Id_PhoneCo" /> 
            </TargetRefs> 
          </Variant> 
          <Variant Name="Fabrikam"> 
            <TargetRefs> 
              <TargetRef Id="Id_Fabrikam" /> 
            </TargetRefs> 
          </Variant> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

5.  Verschieben Sie kompatible Einstellungen im Abschnitt **Allgemeine** **Variant** .

    **Hinweis**  Einstellungen, die sich im Abschnitt **Allgemeine** befinden werden uneingeschränkt auf jedes auslösende Ereignis angewendet.

     

    Im folgenden Beispiel verwendet die `DeviceLock/MaxInactivity` Richtlinie unter ThePhoneCompany Variant während der `DeviceLock/ScreenTimeoutWhileLocked` Richtlinie wurde verschoben, unter der Fabrikam-Variant-Wert.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
          <Variant Name="ThePhoneCompany"> 
            <TargetRefs> 
              <TargetRef Id="Id_PhoneCo" /> 
            </TargetRefs> 
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
              </DeviceLock>
            </Policies>
          </Variant> 
          <Variant Name="Fabrikam"> 
            <TargetRefs> 
              <TargetRef Id="Id_Fabrikam" /> 
            </TargetRefs> 
            <Policies>
              <DeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
          </Variant> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

6.  Speichern Sie die aktualisierte customizations.xml-Datei, und notieren Sie den Pfad zu dieser aktualisierte Datei. Sie werden den Pfad als einen der Werte benötigen, wenn Sie sich auf das Bild erstellen vorzubereiten.

7.  Verwenden der Windows-ICD Befehlszeilenschnittstelle (CLI) provisioning Paket mit den aktualisierten customizations.xml erstellen. Weitere Informationen zum Erstellen eines Pakets provisioning und eine Beschreibung der Befehlsschalter und Parameter finden Sie unter **erstellen ein Pakets Bereitstellung** verwendet [die Windows-ICD-Befehlszeilenschnittstelle](https://msdn.microsoft.com/library/windows/hardware/dn916115).

    Beispiel:

    ``` syntax
    icd.exe /Build-ProvisioningPackage /CustomizationXML:"C:\CustomProject\customizations.xml" /PackagePath:"C:\CustomProject\output.ppkg" /StoreFile:C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\Microsoft-Common-Provisioning.dat"
    ```

    In diesem Beispiel entspricht der **StoreFile** den Speicherort für die Einstellungen, die zum Erstellen des Pakets für die erforderlichen Windows-Edition verwendet werden.

    **Hinweis**  Das Bereitstellung Paket erstellt in diesem Schritt wird die multivariant Einstellungen enthalten. Sie können dieses Paket entweder als ein eigenständiges-Paket, das Sie auf einem Windows-Gerät anwenden können, verwenden Sie es als Basis beim Starten von einem anderen Projekt oder als eine der Eingaben (**/ProvisioningPackage**) beim Erstellen von entweder eine Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) Bild oder Windows 10 Mobile Bild verwenden.

     

## <a name="span-idbuildamobileimageusingthewindowsicdclispanspan-idbuildamobileimageusingthewindowsicdclispanbuild-a-mobile-image-using-the-windows-icd-cli"></a><span id="build_a_mobile_image_using_the_windows_icd_cli"></span><span id="BUILD_A_MOBILE_IMAGE_USING_THE_WINDOWS_ICD_CLI"></span>Erstellen einer mobilen Abbilds mithilfe von Windows ICD CLI


In dieser exemplarischen Vorgehensweise wird das Windows ICD CLI verwenden Sie zum Erstellen einer mobilen Bild veranschaulicht. Weitere Informationen zu den Windows ICD CLI, einschließlich Beispiele für die Verwendung und eine Beschreibung der Parameter finden Sie unter [Verwenden der Windows-ICD-Befehlszeilenschnittstelle](https://msdn.microsoft.com/library/windows/hardware/dn916115).

1.  Öffnen Sie ein Befehlszeilenfenster mit Administratorrechten.

2.  Navigieren Sie zu Windows ICD Installationsverzeichnis, über die Befehlszeile aufgerufen:

    -   Klicken Sie auf eine X64 Computer, wechseln Sie zu: C:\\Program Files (x86)\\Windows Kits\\10\\Assessment and Deployment Kit\\Imaging und Konfiguration Designer\\X86

    -   Klicken Sie auf eine X86 Computer, wechseln Sie zu: C:\\Program Files\\Windows Kits\\10\\Assessment and Deployment Kit\\Imaging und Konfiguration Designer\\X86

3.  Mit der aktualisierten customizations.xml (mit multivariant-Einstellungen) und die MCSF CAF erstellt in [die Anpassung Einstellungen konfigurieren](configure-customization-settings.md), die Windows-ICD CLI zum Erstellen einer mobilen Bild.

    Dies mit Beispieldateien und mit einer bsp.config.xml finden Sie unter den folgenden Befehl ein:

    **icd.exe /Build-ImageFromPackages /ImagePath: "** *C:\\Contoso\\Anpassungen\\TestFlash2.ffu* **"/BSPConfigFile:"** *C:\\ContosoXDevice.bsp.config.xml* **"/ImageType:** *Test* **/CustomizationXML: "** *C:\\Contoso\\Anpassungen\\customizations.xml* **"/OEMCustomizationVer:** *1.0.0.0* **/MCSFCustomizationXML: "***C:\\Contoso\\Anpassungen\\MobileCustomizations.xml***"** "

    Es folgen einige Dinge im Hinterkopf behalten:

    -   Ersetzen Sie die Platzhalterwerte für jeden Parameter mit den Werten, die Ihre Ressourcen und Verzeichnisspeicherort entsprechen
    -   Geben Sie /ImageType an, da wir /BSPConfigFile verwenden
    -   Verwenden Sie /CustomizationXML So zeigen Sie auf die customizations.xml
    -   Windows-ICD erfordert /OEMCustomizationVer, wenn ProvisioningPackage definiert ist
    -   Vergewissern Sie sich das Format für die Versionsnummer /OEMCustomizationVer *wird &lt;wichtigsten&gt;.&lt; Minor&gt;. &lt;SubVersion&gt;. &lt;SubMinorVersion&gt;*, wie etwa 1.0.0.0

    Hierzu die Beispieldateien und mithilfe einer OEMInput.xml-Datei finden Sie unter den folgenden Befehl ein:

    **icd.exe /Build-ImageFromPackages /ImagePath: "** *C:\\Contoso\\Anpassungen\\TestFlash2.ffu* **"/OEMInputXML:"** *C:\\ContosoTestOEMInput.xml* **"/CustomizationXML:"** *C:\\Contoso\\Anpassungen\\customizations.xml* **"/OEMCustomizationVer:** *1.0.0.0* **/MCSFCustomizationXML: "***C:\\Contoso\\Anpassungen\\MobileCustomizations.xml***"** "

Sobald das Bild (FFU) erstellt wird, können Sie es mithilfe von ffutool.exe oder **der Bereitstellungsoption** in der Windows-Benutzeroberfläche ICD auf Ihrem mobilen Gerät flash. Finden Sie weitere Informationen im folgenden Abschnitt.

## <a name="span-idflashanimagetoamobiledevicespanspan-idflashanimagetoamobiledevicespanspan-idflashanimagetoamobiledevicespanflash-an-image-to-a-mobile-device"></a><span id="Flash_an_image_to_a_mobile_device"></span><span id="flash_an_image_to_a_mobile_device"></span><span id="FLASH_AN_IMAGE_TO_A_MOBILE_DEVICE"></span>Flash eines Bilds zu einem mobilen Gerät


Es gibt zwei Methoden, mit denen Sie ein Bild zu einem mobilen Gerät flash:

-   Verwenden ffutool.exe, oder,
-   Verwenden die integrierte blinkende Funktionalität in Windows ICD

In diesem Abschnitt veranschaulicht die beiden Schritte durchführen. Wählen Sie eine der folgenden Methoden auf das Bild auf Ihrem mobilen Gerät flash.

Gehen Sie folgendermaßen vor, wenn Sie das Bild, das das Gerät mit Windows ICD blinken.

**Ein Bild mit Windows ICD blinkt**

1.  Starten Sie das Gerät im Bild oder FFU Download-Modus. So erzwingen Sie das Telefon in Abbild oder FFU Downloadmodus manuell, drücken und halten, um Telefon neu starten, und klicken Sie dann sofort drücken und halten die Lautstärke Schaltfläche nach oben. Beachten Sie, dass diese Option verfügbar ist, nachdem eine anfängliche FFU wurde auf dem Telefon aktualisiert wurde.

    Wenn dies nicht funktioniert, überprüfen Sie, und befolgen Sie das Anweisungen des Herstellers SoC blinkendes Gerät.

2.  Verbinden Sie Ihr Telefon mit einem USB-Kabel auf den Hostcomputer.

3.  Starten Sie Windows ICD.

4.  Klicken Sie im Hauptmenü auf **Bereitstellen** , und wählen Sie zum Bereitstellen von FFU Bild auf das Gerät **zu USB-Gerät angeschlossen** .

5.  Klicken Sie im Fenster **Wählen Sie ein Bild FFU** klicken Sie auf **Durchsuchen...** , Datei-Explorer zu starten, und wählen Sie die FFU, die Sie auf Ihr Zielgerät flash möchten, und klicken Sie dann auf **Weiter**.

6.  Wählen Sie das Zielgerät oder Laufwerk aus der Liste aus. Wenn Ihr Gerät oder Laufwerk nicht aufgeführt ist, klicken Sie auf **Aktualisieren**.

7.  Klicken Sie auf **Weiter**.

8.  Wählen Sie im Fenster **Deploy Gerät** **Flash** , um das Bild blinkt zu starten.

9.  Klicken Sie auf **Fertig stellen** , um die Seite für die **Bereitstellung** zu schließen.

Gehen Sie folgendermaßen vor, wenn Sie das Bild, das das Gerät mit ffutool.exe blinken.

**Ein Bild mit ffutool.exe blinkt**

1.  Starten Sie das Gerät in FFU Modus blinkt, während er auf den Hostcomputer verbunden ist.

    Wenn Sie die optionale LABIMAGE-Funktion, wenn das Testbild generiert einschließen, können Sie das Gerät in FFU Modus manuell durch Drücken und Loslassen der Power blinkt, starten das Gerät und klicken Sie dann sofort gedrückt halten der Lautstärke Schaltfläche erzwingen. Beachten Sie jedoch, dass diese Option ist nur verfügbar, wenn ein FFU zunächst an das Gerät aktualisiert wurde hat.

2.  Öffnen Sie eine Eingabeaufforderung mit Administratorrechten.

3.  Führen Sie an der Befehlszeile das Bild blinkt ffutool.exe ein.

    **Ffutool-flash TestFlash.ffu**

Unabhängig davon, welche Methode Sie verwendet, um das Bild auf das Gerät flash, dauert es einige Minuten, damit das Bild vollständig aktualisiert werden. Nach Abschluss der blinken Geräteinstallation durchlaufen, und stellen Sie sicher, dass die Anpassungen als Teil des Bilds angezeigt werden.

 

 



