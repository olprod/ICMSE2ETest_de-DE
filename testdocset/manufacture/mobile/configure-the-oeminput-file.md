---
Description: "Eine Datei OEMInput gibt an, der Geräteplattform, die Feature-Manifestdateien, die Freigabe, Gerätemodell, build-Typ, Sprachen zu unterstützen, Starten der Benutzeroberfläche Sprache, Gerät Auflösung und andere Attribute wie optionale Features, die Sie als Teil Ihres Bilds einschließen möchten."
ms.assetid: 67dc279e-a7f6-4686-bebf-6d0098d0f782
MSHAttr: PreferredLib:/library
title: Konfigurieren der Datei OEMInput
author: CelesteDG
ms.openlocfilehash: 6fed5046470a2e98da965906f9837942187fa8c2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-the-oeminput-file"></a>Konfigurieren der Datei OEMInput


Nun, dass Sie Ihre Einstellungen Anpassung in der MCSF CAF konfiguriert und benutzerdefinierte OEM-Features in der OEM-manifest-Datei hinzugefügt haben, müssen Sie zum Erstellen einer OEMInput-Datei, die angibt, der Geräteplattform, die Feature-Manifestdateien, die Freigabe, Gerätemodell build-Typ, Sprachen unterstützen, Sprache, Gerät Auflösung und andere Attribute wie optionale Features, die Sie einschließen, im Rahmen Ihres Bilds möchten Benutzeroberfläche starten möchten.

Weitere Informationen zu jedem Element in der OEMInput-Datei finden Sie unter [OEMInput Inhalt](https://msdn.microsoft.com/library/windows/hardware/dn756778).

In dieser exemplarischen Vorgehensweise werden die zwei Features hinzugefügt, die wir zum [Hinzufügen eines Pakets zu einer OEM-Manifestdatei](#adding-a-package-to-an-oem-manifest-file), Angeben von Sprachen, die wir unterstützen möchten und definieren die restlichen unser Bild definiert haben.

**So konfigurieren Sie die Datei OEMInput**

1.  Erstellen Sie eine neue Datei OEMInput.xml oder Ändern einer vorhandenen OEMInput-Datei. Ein Beispiel dafür, wie die Datei OEMInput.xml aussieht wie WPDKCONTENTROOT % finden Sie unter\\OEMInputSamples\\gefälschte im Installationsordner von Kit.

    Im folgenden Beispiel kopiert wir den Inhalt der WPDKCONTENTROOT %\\OEMInputSamples\\gefälschte\\TestOEMInput.xml-Datei und die folgenden Änderungen vorgenommen:

    -   Eine neue Beschreibung hinzugefügt.

    -   Hinzugefügte Englisch (Vereinigtes Königreich), Französisch (Frankreich), Spanisch (Spanien) und Chinesisch (vereinfacht) zur Liste der eingeschlossene Geräte Sprachen neben Englisch (USA). Wir haben dies im Abschnitt **UserInterface** hinzugefügt. Weitere Informationen zu anderen Sprachen, dass Sie auf Ihrem mobilen Gerät hinzufügen können einschließlich [mobilen Gerät Sprachen](https://msdn.microsoft.com/library/windows/hardware/dn772212)finden Sie die Standardsprache Gerät und regionalen Format ändern.

    -   Die ContosoOptionalFeatures.xml Featuremanifestdatei, dass wir in dieser exemplarischen Vorgehensweise [Hinzufügen eines Pakets zu einer OEM-manifest-Datei](#adding-a-package-to-an-oem-manifest-file) erstellt und platziert es unter dem Abschnitt **AdditionalFMs** der Datei OEMInput durch Hinzufügen einer neuen **AdditionalFM** zu- und Angeben der Speicherort und den Namen des Features Manifestdatei hinzugefügt.

    -   Das ECHO hinzugefügt\_TREIBER und SCHNELLE\_AKTIONEN Features durch Hinzufügen einer neuen **OEM** Unterabschnitt innerhalb des Abschnitts **Features** der OEMInput Datei. Für jedes Feature, die wir innerhalb des Abschnitts **OEM** hinzufügen, wir einen neuen Eintrag **Feature** hinzufügen und geben dann den Namen der Funktion, die wir in der Feature-Manifestdatei definierten.

    **Hinweis**  Wenn Sie ein Verweis mobilen Gerät verwenden, stellen Sie sicher, dass die Werte in den Abschnitten der OEMInput.xml **SOC**, **PA**und **Geräte** zu aktualisieren. Sie können auch ändern der **ReleaseType** , je nachdem, was Sie tun möchten. Stellen Sie sicher, dass Sie die Anweisungen in [Dateiinhalten OEMInput](https://msdn.microsoft.com/library/windows/hardware/dn756778) einhalten, wenn Sie Werte für diese Elemente angeben.

     

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <OEMInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
              xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
              xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
      <Description>Windows mobile image test FFU generation</Description>
      <SOC>FAKE_SOC_Test</SOC>
      <SV>Microsoft</SV>
      <Device>FAKE</Device>
      <ReleaseType>Test</ReleaseType>
      <BuildType>fre</BuildType>
      <SupportedLanguages>
        <UserInterface>
          <Language>en-US</Language>
          <Language>en-GB</Language>
          <Language>fr-FR</Language>
          <Language>es-ES</Language>
          <Language>zh-CN</Language>
        </UserInterface>
        <Keyboard>
          <Language>en-US</Language>
        </Keyboard>
        <Speech>
          <Language>en-US</Language>
        </Speech>
      </SupportedLanguages>
      <BootUILanguage>en-US</BootUILanguage>
      <BootLocale>en-US</BootLocale>
      <Resolutions>
        <Resolution>480x800</Resolution>
      </Resolutions>
      <AdditionalFMs>
        <AdditionalFM>%WPDKROOT%\FMFiles\arm\ContosoOptionalFeatures.xml</AdditionalFM>
        <AdditionalFM>%WPDKROOT%\FMFiles\arm\MSOptionalFeatures.xml</AdditionalFM>
      </AdditionalFMs>
      <Features>
        <Microsoft>
          <Feature>IMGFAKEMODEM</Feature>
          <Feature>TEST_DISABLE_DISK_IDLE</Feature>
          <Feature>STANDARD_FEATURE_1</Feature>
          <Feature>CODEINTEGRITY_TEST</Feature>
          <Feature>SELFHOST_AUTOMATIC_DEVICE_CONFIGURATOR</Feature>
          <Feature>LOCATIONFRAMEWORKAPP</Feature>
          <Feature>FACEBOOK</Feature>
          <Feature>COMMSENHANCEMENTGLOBAL</Feature> 
          <Feature>KDNETUSB_TEST_ON</Feature>
          <Feature>TESTINFRASTRUCTURE</Feature>
          <Feature>TEST</Feature>
          <Feature>STARTUPOVERRIDES</Feature>
          <Feature>GWPCERTTESTPROV</Feature>
          <Feature>MOBILECORE_TEST</Feature>
          <Feature>DRIVERS_WDTFINFRA</Feature>
          <Feature>SKYPE</Feature>
          <Feature>BOOTSEQUENCE_TEST</Feature>
          <Feature>SKIPOOBE</Feature>
          <Feature>CORTANADBG_TEST_PROTECTED</Feature>
          <Feature>TEST_PROTECTED</Feature>
          <Feature>PSEUDOLOCALES</Feature>
        </Microsoft>
        <OEM>
          <Feature>ECHO_DRIVER</Feature>
          <Feature>QUICK_ACTIONS</Feature>
        </OEM>
      </Features>
      <Product>Windows Phone</Product>
    </OEMInput>
    ```

2.  Benennen Sie und speichern Sie Ihre OEMInput.xml Datei. In unserem Beispiel wir mit dem Namen ContosoTestOEMInput.xml, und es in den WPDKCONTENTROOT % gespeichert\\ContosoOEMInput Ordner.

 

 



