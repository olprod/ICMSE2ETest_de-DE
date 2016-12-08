---
Description: In this section, we'll focus on adding the Start layout modification file, preloading an app, and configuring some customization settings using MCSF.For more detailed information about the various customizations you can do, see https://msdn.microsoft.com/library/windows/hardware/dn757433.
ms.assetid: 507fea31-f113-4cd3-84bf-1ab14898782f
MSHAttr: PreferredLib:/library
title: "Konfigurieren der Einstellungen für die Anpassung"
author: CelesteDG
ms.openlocfilehash: 919d399a7b2e449fab5a6121a6642138f679c6fa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-customization-settings"></a>Konfigurieren der Einstellungen für die Anpassung


Anpassungen sind Möglichkeiten, die Sie ändern können, die Windows Gerät Benutzeroberfläche Konnektivitätseinstellungen und Benutzerinteraktion besser widerzuspiegeln Ihre Marke und erfüllen der Netzwerk- und Markt, in dem das Gerät ausgeliefert wird. Anpassungen sind möglich, Hinzufügen von apps, Bearbeiten des Layouts starten, Konfigurieren mithilfe der Verwaltung von Geräten, die Standardwerte auf dem Bildschirm Einstellungen ändern oder Hinzufügen von neuen Hintergrundbilder Netzwerkeinstellungen.

Windows 10 Mobile unterstützt zwei Anpassung Frameworks: MCSF und Windows-Bereitstellung. Weitere Informationen zu jedem Framework finden Sie unter [Anpassungen für mobile Geräte](https://msdn.microsoft.com/library/windows/hardware/mt481438).

In diesem Abschnitt konzentrieren wir uns auf Start Layoutdatei Änderung hinzufügen, vorgezogene Laden einer app und einige MCSF von Anpassung Einstellungen konfigurieren.

Ausführlichere Informationen zu den verschiedenen Anpassungen, alles möglich ist finden Sie unter [https://msdn.microsoft.com/library/windows/hardware/dn757433](https://msdn.microsoft.com/library/windows/hardware/dn757433).

## <a name="span-idcreateanmcsfcustomizationanswerfilespanspan-idcreateanmcsfcustomizationanswerfilespancreate-an-mcsf-customization-answer-file"></a><span id="create_an_mcsf_customization_answer_file"></span><span id="CREATE_AN_MCSF_CUSTOMIZATION_ANSWER_FILE"></span>Erstellen Sie eine Anpassungsdatei Antwort MCSF


Die MCSF- [Antwort-Anpassungsdatei](https://msdn.microsoft.com/library/windows/hardware/dn757452) (CAF) können Sie angeben, die Einstellungen und Varianten, die Sie für ein benutzerdefiniertes mobilen Betriebssystemabbild konfigurieren möchten. Je nach der Tools, die Sie verwenden, um das Bild zu erstellen, können Sie den MCSF CAF als Eingabe in ImgGen.cmd oder Windows Imaging und Designer (ICD) CLI-Konfiguration. Diese Antwortdatei wird basierend auf dem MCSF-Schema, wenn Sie beschließen, ein anderes Schema, wie die Bereitstellung Windows-Schema, müssen Sie eine andere Antwortdatei schreiben, die dieses Schema stattdessen folgt.

Wenn Sie nicht über eine bereits vorhandene MCSF CAF verfügen, führen Sie in dieser exemplarischen Vorgehensweise erfahren, wie eine grundlegende MCSF CAF mit multivariant Unterstützung zu erstellen. Multivariant ist der allgemeine Mechanismus, der ermöglicht die Erstellung ein einzelnes Bilds, das für mehrere Märkte durch dynamisch konfigurieren die Sprache, branding, apps und networking Einstellungen Laufzeit basierend auf den unterstützten von, wie Mobilfunkbetreiber und Gebietsschema arbeiten können. Wenn Sie ein einzelnes variant Bild erstellen, können Sie in dieser exemplarischen Vorgehensweise überspringen.

**So erstellen Sie die MCSF CAF mit multivariant-Unterstützung**

1.  Erstellen einer XML-Datei, und fügen Sie folgenden Inhalt.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name=""  
                         Description="Use to configure settings for custom mobile image."  
                         Owner=""  
                         OwnerType="OEM"> 

      <!-- Use to set up targets and conditions for the variants -->
      <Targets>  
       <Target Id="">  
          <TargetState>  
            <Condition Name="" Value="" />  
            <Condition Name="" Value="" />  
          </TargetState>  
        </Target>  
       <Target Id="">  
          <TargetState>  
            <Condition Name="" Value="" />  
            <Condition Name="" Value="" />  
          </TargetState>  
        </Target> 
      </Targets>  
      
      <!-- Use to specify the customizations for a single variant when used without the Variant element, 
           or customizations that apply to all variants when used with the Variant element -->
      <Static>  
        <!-- Use to preload apps to install for all variants -->
        <Applications>
          <Application Source=""
                       License=""
                       ProvXML="" />
        </Applications>

        <!-- Section where you specify the settings you want to configure -->
        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings>
      </Static>

      <!-- These settings in the Variant groups will only be applied if the associated target&#39;s conditions are met. -->
      <!-- The settings shown here will only be applied for this variant -->
      <Variant Name="">  
        <!-- Only one TargetRef can be used for each variant -->
        <TargetRefs>  
          <TargetRef Id="" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>  

      <!-- The settings shown here will only be applied for this variant -->
      <Variant Name="">  
        <!-- Only one TargetRef can be used for each variant -->
        <TargetRefs>  
          <TargetRef Id="" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant> 

    </ImageCustomizations>
    ```

2.  Geben Sie die Werte für die folgenden Attribute, um zu bestimmen, den Besitzer für die Anpassungen:

    -   **Name** – eine Zeichenfolge, die den Namen der Anpassung oder des Pakets angibt. Sie können den Namen basierend auf dem Gerät, Sie sind konfigurieren, z. B. "XDeviceCustomizations" oder ein allgemeiner Name wie "MobileCustomizations" angeben.
    -   **Beschreibung** – eine Zeichenfolge zur einfacheren Identifizieren Sie die Anpassungen in die CAF definiert sind.
    -   **Besitzer** - eine Zeichenfolge zur Angabe des Besitzers, beispielsweise den OEM-Namen.
    -   **Besitzertyp** - legen Sie den "OEM".

3.  Geben Sie die **Ziele** für die Varianten verwendet. **Ziele** muss beschreiben Sitzposition für einen Variant-Wert und beschrieben oder vor dem deklariert werden, bevor durch den Variant-Wert sein. Dazu:

    **So richten Sie ein Ziel ein**

    1.  Nennen Sie die **Ziel-Id**an.

    2.  Legen Sie die **Bedingung**(s) für das Ziel des Vorgangs durch den **Namen** und den **Wert**bereitstellen.

    Wenn wir Erstellen von Varianten für zwei fiktive Mobilfunkbetreiber, die Telefongesellschaft und Fabrikam und wir ihre MCC und MNC verfügen, können wir beispielsweise eine Ziel für jeden Operator mit dem MCC und MNC erstellen.

    ```XML
      <!-- Use to set up targets and conditions for the variants -->
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
      
    ```

    Weitere Informationen zu den unterstützten **Bedingungsname**s finden, die Sie verwenden können, finden Sie im Abschnitt *Ziel, TargetState, Bedingung, und Prioritäten* in [einer Bereitstellung Paket mit multivariant Einstellungen erstellen](https://msdn.microsoft.com/library/windows/hardware/dn916108). Beachten Sie, dass in dieser exemplarischen Vorgehensweise wir kein provisioning Paket verwenden, um unsere multivariant Einstellungen zu deklarieren. Stattdessen möchten wir diese direkt in die MCSF CAF hinzufügen.

4.  Richten Sie den Variant-Wert. Dabei folgendermaßen vor:

    **So definieren Sie einen Variant-Wert**

    1.  Geben Sie den **Variant-Name**.

    2.  Geben Sie die **TargetRef-Id** für den Variant-Wert. Dies sollte eine der **Ziel-Id**s übereinstimmen, die Sie im Abschnitt **Ziele** der CAF angegeben. Beachten Sie, dass es sollte nur eine **TargetRef Id** pro Variante vorhanden sein.

    Unsere fiktiven Mobilfunkbetreiber, die Telefongesellschaft und Fabrikam können wir die Varianten für jede dieser Operatoren definieren mithilfe, wie im folgenden Beispiel dargestellt:

    ```XML
      <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>  

      <!-- The settings shown here will only be applied for Fabrikam -->
      <Variant Name="Fabrikam">  
        <TargetRefs>  
          <TargetRef Id="Id_Fabrikam" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>   
    ```

5.  Den Namen Sie, und speichern Sie die XML-Datei. beispielsweise *C:\\Contoso\\Anpassungen\\MobileCustomizations.xml*.

    Wir werden in die nächste exemplarische Vorgehensweisen für die statische (common oder Variant unabhängig) und Anpassung von Variant-spezifischen Einstellungen und Werte hinzufügen.

## <a name="span-idconfigurethestartlayoutmcsfspanspan-idconfigurethestartlayoutmcsfspanconfigure-the-start-layout"></a><span id="configure_the_start_layout_mcsf"></span><span id="CONFIGURE_THE_START_LAYOUT_MCSF"></span>Das Start-Layout konfigurieren


In diesem Abschnitt wird die MCSF starten Einstellungen zum Hinzufügen der Start Layout Modification-Dateien, die Sie unter [Konfigurieren des Start-Layouts](configure-the-start-layout.md)erstellt verwendet. Wir verwenden eine der Layout Änderung Dateien als allgemeine Start Layout und verwenden wir die anderen Änderung Layoutdatei für eine der Varianten fiktiven Mobilfunkbetreiber.

1.  Erstellen Sie und bearbeiten Sie die MCSF CAF; beispielsweise *C:\\Contoso\\Anpassungen\\MobileCustomizations.xml*.

2.  Legen Sie *C:\\Contoso\\Anpassungen\\LayoutModification1.xml* als das allgemeine Start Layout.

    Legen Sie innerhalb der **statischen** Sie im Abschnitt der CAF `LayoutModificationFilePath` auf den Dateipfad Layoutdatei Änderung.

    ```XML
      <Static>  
        <!-- Use to preload apps to install for all variants -->
        <Applications>
          <Application Source=""
                       License=""
                       ProvXML="" />
        </Applications>

        <!-- Section where you specify the settings you want to configure -->
        <Settings Path="StartLayoutModificationFilePath">  
          <Setting Name="LayoutModificationFilePath" Value="C:\Contoso\Customizations\LayoutModification1.xml" />
        </Settings>  
      </Static>
    ```

    Indem Sie einen neuen Standardspeicherort für der LayoutModification.xml angeben, überschreiben Sie das Standardlayout für das Starten, die in C: ist\\Daten\\Ordner "ProgramData"\\Microsoft\\starten\\Layouts.

3.  Legen Sie *C:\\Contoso\\Anpassungen\\LayoutModification2.xml* als das Standardlayout Start für das fiktive Mobilfunkbetreiber, die Telefongesellschaft.

    Legen Sie **Variant** im Abschnitt mit dem Namen ThePhoneCompany `LayoutModificationFilePath` auf den Dateipfad für die zweite Änderung Layoutdatei.

    ```XML
      <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <Settings Path="StartLayoutModificationFilePath">  
          <Setting Name="LayoutModificationFilePath" Value="C:\Contoso\Customizations\LayoutModification2.xml" />
        </Settings> 
      </Variant>  
    ```

**Hinweis** `LayoutModificationFilePath` ist eine Einstellung FirstVariationOnly, was bedeutet, dass er nur während der ersten Variante geändert werden kann in der Regel ist, wenn die erste gültige Konfiguration (beispielsweise wenn ein SIM eingefügt wird und marked-Konfiguration für den SIM gefunden wird) gefunden wird.   Wenn die Konfiguration geändert wird, wird wie beispielsweise während einer Swap SIM der Wert für die Einstellung FirstVariationOnly nicht erneut geändert werden.

 

In diesem Beispiel wird, wenn das Gerät startet nach der Aktualisierung eines neuen mobilen Bilds, und es ist keine SIM eingefügt wird das mobile Gerät oder eine SIM für das fiktive Fabrikam Mobilfunkbetreiber (MCC = 310 MNC = 610) ist bereits im Gerät, LayoutModification1.xml (Start-Layout mit einem Ordner) verwendet werden. Wenn eine SIM für das fiktive The Phone Company (MCC = 410 MNC = 510) wird eingefügt, danach den Anfang Layout wird nicht geändert. Allerdings wird, wenn das Gerät startet nach der Aktualisierung eines neuen mobilen Bilds, und es bereits eine SIM für die Telefongesellschaft im Gerät eingefügt ist, LayoutModification2.xml (Start-Layout mit keine Ordner) verwendet werden.

## <a name="span-idpreloadappsspanspan-idpreloadappsspanpreload-apps"></a><span id="preload_apps"></span><span id="PRELOAD_APPS"></span>Vorinstallation apps


Partner können Vorinstallation apps gepackt und so konfiguriert, dass während des Installationsvorgangs anfänglichen Gerät auf mobilen Geräten installieren. Zusätzlich zur vorab geladene spielen, Lifestyle apps und andere Genres von apps, können Partner System Einstellungen apps oder Partner Konto Setup apps, nur ein paar zu nennen Vorinstallation. Weitere Informationen zu vorab apps finden Sie unter [Preinstallable apps für mobile Geräte](https://msdn.microsoft.com/library/windows/hardware/dn707972).

**Wichtige**  In Windows-10 Wenn Sie arbeiten mit einer app-Entwickler oder Erstellen Ihrer eigenen app So laden Sie auf dem Gerät sind müssen Sie jetzt ein Vorinstallation Paket für die app anfordern. Weitere Informationen zu diesem Teil des Prozesses finden Sie unter [Pakete für OEMs Vorinstallieren generieren](http://go.microsoft.com/fwlink/p/?LinkId=624851). Die ZIP-Datei, die zurückgegeben wird, als Teil dieses Vorgangs die app-Quelldatei (beispielsweise ein .appx, .appxbundle oder XAP-Datei) enthalten soll, eine Bereitstellungsdatei (.provxml) und eine Lizenz-Datei (XML). Wenn Ihr preinstall Paket nicht alle diese Dateien enthalten, können nicht Sie die app erfolgreich laden.

 

**So laden eine app**

1.  Stellen Sie sicher, dass das Vorinstallieren von app-Paket alle Dateien enthält, Sie eine app Vorinstallation müssen: Quellcode-Datei, Bereitstellungsdatei und Lizenzdatei.

2.  Fügen Sie die app auf das Bild. Gehen Sie hierzu folgendermaßen vor:

    1.  Einen Abschnitt **Applications** die CAF hinzufügen.

        ```XML
            <!-- Use to preload apps to install for all variants -->
            <Applications>
              <Application Source=""
                           License=""
                           ProvXML="" />
            </Applications>
        ```

        **Hinweis**  Sie können die CAF, was, dass die app installiert wird für alle Bilder unabhängig von den Variant-Wert bedeutet, innerhalb des Abschnitts **statische** im Abschnitt **Webanwendungen** hinzufügen oder Sie können innerhalb einer bestimmten **Variante**, was bedeutet, dass nur installiert wird für eine bestimmte Variante hinzufügen. Wenn Sie mehr als eine app vorgezogene Laden sind, kann eine allgemeine alle Varianten (oder innerhalb des Abschnitts **statische** ) sein, während eine andere gilt nur für einen bestimmten Variant-Wert (oder in einem **Variant** -Abschnitt): Ein Beispiel letzteren Fall kann sein, wenn Sie eine app verwenden, die Sie müssen nur installieren für eine bestimmte Mobilfunkbetreiber oder Land/Region und so weiter.

         

    2.  **Quelle** auf den Speicherort und den Namen der Quelldatei app festgelegt; beispielsweise *C:\\Contoso\\Anpassungen\\Apps\\SampleApp.appx*.

    3.  Set- **Lizenz** für den Speicherort und Namen der Datei für Ihre app-Lizenz; beispielsweise *C:\\Contoso\\Anpassungen\\Apps\\SampleAppLicense.xml*.

    4.  Legen Sie **ProvXML** auf den Speicherort und den Namen der Bereitstellungsdatei Ihrer app. beispielsweise *C:\\Contoso\\Anpassungen\\Apps\\Mpap\_Sampleapp\_001.abc Provxml*.

        Die Datei ProvXML folgt eine vorgeschriebene Benennungskonvention. Weitere Informationen finden Sie unter [Preinstallable apps für mobile Geräte](https://msdn.microsoft.com/library/windows/hardware/dn707972) .

3.  Speichern der CAF, sobald Sie fertig sind alle apps hinzufügen.

In einigen Fällen müssen Sie eine app laden, die auf andere Komponenten oder Pakete abhängig ist. In diesem Fall müssen Sie sicherstellen, dass die anderen Pakete oder Komponenten vorinstallierten zuerst, bevor Sie Ihre app sind. Ihre app Teiler schlägt fehl, wenn die abhängigen Pakete oder Komponenten zuerst nicht installiert sind. Wir werden nicht in diesem Szenario durchlaufen, aber Sie finden diese Informationen in [einer app mit einer Abhängigkeit geladen](https://msdn.microsoft.com/library/windows/hardware/mt691485)dokumentiert.

## <a name="span-idconfiguredevicetargetinginfometadataspanspan-idconfiguredevicetargetinginfometadataspanconfigure-the-devicetargetinginfo-metadata-for-the-device"></a><span id="configure_devicetargetinginfo_metadata"></span><span id="CONFIGURE_DEVICETARGETINGINFO_METADATA"></span>Konfigurieren Sie die DeviceTargetingInfo Metadaten für das Gerät


Um mindestens ein mobiles Gerät, zum gehören, müssen Sie die erforderlichen Einstellungen in [Telefon Metadaten in DeviceTargetingInfo](https://msdn.microsoft.com/library/windows/hardware/dn772214)beschrieben festlegen. Beispiele für Metadaten erforderlich sind:

-   OEM und Mobilfunkbetreiber Informationen zum Anzeigen Zeichenfolgen in der Benutzeroberfläche des geräteupdate, eine Verbindung mit den Windows Store, und so weiter.
-   Komponente Hardwareversionen und Softwareversionen, Benutzergruppenorientierten Bereitstellung von Updates für Geräte und für die Unterstützung für Benutzer verwendet.
-   Modellname des Geräts, den Mobilfunkbetreiber Namen und den Namen des Herstellers, die im Bildschirm **zur** **Einstellungen**angezeigt werden.

**So konfigurieren Sie die DeviceTargetingInfo-Metadaten**

1.  Bearbeiten der MCSF CAF; beispielsweise *C:\\Contoso\\Anpassungen\\MobileCustomizations.xml*.

2.  In den **statischen** Teil der CAF aufnehmen einer `DeviceInfo/Static` Einstellungsgruppe.

    ```XML
      <Static>  
        <!-- Other settings groups may already precede the DeviceInfo/Static group -->

        <Settings Path="DeviceInfo/Static">       
          <Setting Name="PhoneManufacturer" Value="" />    
          <Setting Name="PhoneManufacturerDisplayName" Value="" /> 
          <Setting Name="PhoneROMVersion" Value="" /> 
          <Setting Name="PhoneHardwareRevision" Value="" />    
          <Setting Name="PhoneSOCVersion" Value="" /> 
          <Setting Name="PhoneFirmwareRevision" Value="" />   
          <Setting Name="PhoneRadioHardwareRevision" Value="" />    
          <Setting Name="PhoneRadioSoftwareRevision" Value="" /> 
          <Setting Name="PhoneBootLoaderVersion" Value="" />    
          <Setting Name="PhoneROMLanguage" Value="" /> 
          <Setting Name="PhoneHardwareVariant" Value="" /> 
       </Settings> 

      </Static>
    ```

    Diese Einstellungen sind Bild Zeit nur und werden direkt in der Registrierungsstruktur versetzt werden. Beachten Sie, dass einige Einstellungen in der `DeviceInfo/Static` Gruppe sind optional, sodass Sie nicht für alle Werte für die Dateien angeben oder den CAF daraus auswählen können. Welche Einstellungen sind erforderlich, optional, und die Halbleiterhersteller, welche stammen, werden in der folgenden Tabelle zusammengefasst.

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Erforderliche Einstellung</th>
    <th align="left">Optionale Einstellung</th>
    <th align="left">Festlegen von SoC-Anbieter</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>PhoneManufacturer</p>
    <p>PhoneFirmwareRevision</p>
    <p>PhoneROMLanguage</p>
    <p>PhoneHardwareVariant</p></td>
    <td align="left"><p>PhoneManufacturerDisplayName</p>
    <p>PhoneRadioHardwareRevision</p></td>
    <td align="left"><p>PhoneROMVersion</p>
    <p>PhoneHardwareRevision</p>
    <p>PhoneSOCVersion</p>
    <p>PhoneRadioSoftwareRevision</p>
    <p>PhoneBootLoaderVersion</p></td>
    </tr>
    </tbody>
    </table>

     

    **Hinweis**  Sie müssen Ihr Microsoft-Ansprechpartner, um den Wert zu erhalten, die Sie, für verwenden sollten `PhoneManufacturer`.

     

3.  Fügen Sie in den **Variant** Teil der CAF, eine `DeviceInfo/Variant` Einstellungsgruppe.

    Unser Beispiel fügen die Einstellungen für ThePhoneCompany innerhalb des Abschnitts variant wir

    ```XML
       <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <!-- Other settings with the Variant section not included here for simplicity --> 

        <Settings Path="DeviceInfo/Variant">
          <Setting Name="PhoneMobileOperatorName" Value="" /> 
          <Setting Name="PhoneManufacturerModelName" Value="" />    
          <Setting Name="PhoneMobileOperatorDisplayName" Value="" /> 
          <Setting Name="PhoneSupportPhoneNumber" Value="" />    
          <Setting Name="PhoneSupportLink" Value="" /> 
          <Setting Name="PhoneOEMSupportLink" Value="" />    
          <Setting Name="PhoneModelName" Value="" /> 
          <Setting Name="RoamingSupportPhoneNumber" Value="" />
       </Settings> 
     
      </Variant>  
    ```

    Diese Einstellungen werden nur die erste Variante und können zur Laufzeit konfiguriert werden, also potenziell anhand der SIM-Wert. Beachten Sie, dass einige Einstellungen in der `DeviceInfo/Variant` Gruppe sind optional, sodass Sie beschließen, geben Sie Werte für diese oder Aufheben der CAF nicht. In der folgenden Tabelle werden die Einstellungen sind erforderlich, optional, und die Halbleiterhersteller, welche stammen zusammengefasst.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Erforderliche Einstellung</th>
    <th align="left">Optionale Einstellung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>PhoneMobileOperatorName</p>
    <p>PhoneManufacturerModelName</p>
    <p>PhoneModelName</p></td>
    <td align="left"><p>PhoneMobileOperatorDisplayName</p>
    <p>PhoneSupportPhoneNumber</p>
    <p>PhoneSupportLink</p>
    <p>PhoneOEMSupportLink</p>
    <p>PhoneRoamingSupportPhoneNumber</p></td>
    </tr>
    </tbody>
    </table>

     

4.  Speichern der CAF Sie abschließend wählen hinzufügen alle Werte für die erforderlichen Einstellungen oder alle optionalen Einstellungen festgelegt. Befolgen Sie die Anweisungen in [Telefon Metadaten in DeviceTargetingInfo](https://msdn.microsoft.com/library/windows/hardware/dn772214) , um sicherzustellen, dass Sie die richtigen Werte und ihre Formate festlegen.

## <a name="span-idconfigureothercustomizationsettingsspanspan-idconfigureothercustomizationsettingsspanconfigure-other-customization-settings"></a><span id="configure_other_customization_settings"></span><span id="CONFIGURE_OTHER_CUSTOMIZATION_SETTINGS"></span>Konfigurieren Sie andere Einstellungen der Anpassung


Es gibt eine Vielzahl von anderen Anpassung Einstellungen, die Sie für Windows mobile-Geräten konfigurieren können. Für Telefone insbesondere müssen auch in der Regel Sie zum Bereitstellen von Konnektivitätseinstellungen wie die MMS APN MMS-Proxy, IMS Services (falls unterstützt) und So weiter. In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie diese Einstellungen bereits konfiguriert haben, damit wir zum Konfigurieren dieser Einstellungen Connectivity verdeckt wird. Der Abschnitt MCSF der Partner-Dokumentation enthält szenariobasierte Dokumentationen für die Einstellungen zu identifizieren, die Sie konfigurieren möchten basierend auf der Szenarien oder Bereiche, die Sie aktivieren möchten. Weitere Informationen zu diesen Anpassungen finden Sie unter:

-   [Anpassungen für Gerätemanagement](https://msdn.microsoft.com/library/windows/hardware/dn757439) Informationen zum Aufheben der Standardeinstellung CountryTable.xml, festlegen den UICC Steckplatz für das branding, Konfiguration und vieles mehr.
-   [Anpassungen für die Hardwarekomponenten](https://msdn.microsoft.com/library/windows/hardware/dn757441) für Informationen zum Anpassen der Anzeige, Speicherung, Fingereingabe und usw..
-   [Anpassungen für Anwendungen und Komponenten von Microsoft](https://msdn.microsoft.com/library/windows/hardware/dn757434) für Informationen zum Hinzufügen von app ein Telefonanruf/SMS-Filter und aktiven Abdeckung telefoneinstellungen.
-   [Anpassungen für Boot, ersteinrichtung, und beim Herunterfahren](https://msdn.microsoft.com/library/windows/hardware/dn757435) von Informationen zum Konfigurieren der Timezone-Bestätigung Seite und die Sprache der Auswahl bei der Geräteinstallation und viele weitere.
-   [Anpassungen für Browser](https://msdn.microsoft.com/library/windows/hardware/dn757436) für Info Möglichkeiten, dass Sie Microsoft Edge anpassen können.
-   [Anpassungen für Konnektivität](https://msdn.microsoft.com/library/windows/hardware/dn757437) erfahren Sie mehr über die benutzerdefinierten Prozentsätze für Signalstärke Balken, bevorzugte Anbieter Datenliste, servergespeicherte Filter usw. festlegen.
-   Von [Anpassungen für Desktop guter](https://msdn.microsoft.com/library/windows/hardware/dn757438) Bildtyp Symbol und Standardwerte in der anpassen, die angezeigt wird, wenn das mobile Gerät mit dem Desktop verbunden ist.
-   [Anpassungen für e-Mail](https://msdn.microsoft.com/library/windows/hardware/dn757440) Informationen zum Ändern der e-Mail-app zu immer einen hellen Hintergrund haben.
-   [Anpassungen für Karten](https://msdn.microsoft.com/library/windows/hardware/dn757442) für vorgezogene Laden Zuordnungsdaten in der Benutzerspeicher oder SD-Karte Info-Zuordnungen für Telefone, die im Lieferumfang von China und vieles mehr.
-   [Anpassungen für Anrufe](https://msdn.microsoft.com/library/windows/hardware/dn757443) zu erfahren Sie mehr über das branding für Telefonanrufe, visual Voicemail, Sofortnachrichten Services und RCS und viele weitere aktivieren einrichten.
-   [Anpassungen für Fotos, Musik und Videos](https://msdn.microsoft.com/library/windows/hardware/dn757445) für Info zur Beschränkung der Lautstärke, Hinzufügen von OEM Tiefenschärfe apps und so weiter.
-   [Anpassungen für die Einstellungen](https://msdn.microsoft.com/library/windows/hardware/dn757448) für alle viele Anpassungen Sie lernen können für die Einstellungen konfigurieren, die innerhalb der app **Einstellungen** auf mobilen Geräten angezeigt werden.
-   [Anpassungen für SMS- und MMS](https://msdn.microsoft.com/library/windows/hardware/dn757449) für Weitere Informationen zum Hinzufügen von Codierung Erweiterungstabellen für SMS, maximale Länge für Nachrichten, Intercept verweigern Liste und vieles mehr.
-   [Anpassungen für Start](https://msdn.microsoft.com/library/windows/hardware/dn757450) so ändern Sie das Standardverhalten von der Windows Store-live-Kachel. Beachten Sie, dass Sie können das Layout Start zu konfigurieren, jedoch hat, die im [Layout für 10 für Windows mobile-Editionen starten](https://msdn.microsoft.com/library/windows/hardware/mt171093) behandelte Problem zu und als Beispiel in dieser exemplarischen Vorgehensweise gezeigt.

 

 



