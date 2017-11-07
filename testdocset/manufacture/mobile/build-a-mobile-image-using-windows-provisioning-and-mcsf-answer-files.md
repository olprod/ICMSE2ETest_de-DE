---
title: Erstellen einer mobilen Bild mit einer Hybridmethode
description: "Sie können die Vorteile der Bereitstellung Framework für Windows und die MCSF mithilfe einer Hybridmethode zum Erstellen von benutzerdefinierten mobilen Abbilds nutzen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3A6BEF64-BCE1-4BF9-8A2F-14A79F956F7B
ms.openlocfilehash: ce35385fb79bb0d8cfa4a914721e5d9dfcf2be16
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-a-hybrid-method"></a>Erstellen einer mobilen Bild mit einer Hybridmethode


Sie können die Vorteile der Bereitstellung Framework für Windows und die MCSF mithilfe einer Hybridmethode zum Erstellen von benutzerdefinierten mobilen Abbilds nutzen. Dies bedeutet, dass:

-   Eine [Anpassung Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn757452) MCSF können Sie vollständig Anpassen der geräteeinstellungen, Hardware und Diensten, apps Vorinstallation, Hinzufügen von Objekten wie Klingeltöne und lokalisierten Zeichenfolgen und konfigurieren Sie weitere [MCSF Einstellungen in der Windows-Bereitstellung nicht unterstützt](https://msdn.microsoft.com/library/windows/hardware/mt573153).

-   Sie können eine [Windows provisioning Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn916153) so definieren Sie den neuen Runtime-Einstellungen, Unternehmensrichtlinien, Einstellungen für die Registrierung verwenden und andere [unterstützt nur bei der Bereitstellung von Windows mobile-Einstellungen](https://msdn.microsoft.com/library/windows/hardware/mt560342)konfigurieren.

-   Windows Imaging und Designer (ICD) CLI-Konfiguration können Sie um Ihr Bild zu erstellen.

    **Hinweis**  Nur die Windows ICD CLI ermöglicht Ihnen, eine Anpassungsdatei Antwort MCSF und Antwort eine Windows-Bereitstellungsdatei zum Erstellen eines benutzerdefinierten mobilen Abbilds verwenden.

     

## <a name="to-build-a-customized-mobile-image-using-a-hybrid-method"></a>Erstellen ein benutzerdefiniertes mobiles Abbilds mithilfe einer Hybridmethode


Nachfolgend finden Sie die allgemeinen Schritte, die Sie durchführen, um ein benutzerdefiniertes mobile Abbild mithilfe der Windows-ICD CLI erstellen müssen:

1.  Wählen Sie, wie der Pakete und Features in Ihrem Bild enthalten definieren.

    -   Sie können BSP.config.xml Datei - verwenden, wenn wählen Sie diese Methode, dies bereits im Rahmen Ihres BSP Kits ist oder Sie können eigene mithilfe der Konfigurationstools dessen Hersteller SoC generieren.

    -   Eine OEMDevicePlatform.xml und OEMInput.xml-Datei können Sie Ihre Plattform definieren. Zu diesem Zweck führen Sie die Schritte 1 bis 4 in der Liste allgemeine Schritte in [Erstellen einer mobilen Bild ImgGen.cmd verwenden](building-a-phone-image-using-imggencmd.md).

2.  Erstellen Sie Ihre Antwortdateien, um die Einstellungen zu definieren, die Sie für das Bild konfigurieren möchten.

    -   Erstellen Sie eine MCSF- [Anpassungsdatei Antwort](https://msdn.microsoft.com/library/windows/hardware/dn757452) um eines der verfügbaren Anpassungen in MCSF Framework anpassen. Weitere Informationen finden Sie unter der *Anpassungen für &lt;Feature&gt; * Abschnitte in [Anpassen mithilfe von mobilen MCSF Framework](https://msdn.microsoft.com/library/windows/hardware/dn757433).

    -   Erstellen Sie eine [Antwortdatei der Windows-Bereitstellung](https://msdn.microsoft.com/library/windows/hardware/dn916153) , um die verfügbaren Einstellungen im Windows provisioning Rahmen zu definieren. Weitere Informationen finden Sie unter [Bereitstellen von Windows (Referenz)](https://msdn.microsoft.com/library/windows/hardware/dn953942).

    Wenn Sie in beiden Antwortdateien multivariant Einstellungen hinzufügen möchten, stellen Sie sicher, ob die multivariant Regeln in beiden Antwortdateien konsistent sind. Finden Sie im Abschnitt *Ziel, TargetState, Bedingung und Prioritäten* in [Erstellen einer Bereitstellung Paket mit multivariant Einstellungen](https://msdn.microsoft.com/library/windows/hardware/dn916108) für eine Liste der unterstützten Bedingungen, aber halten Sie sich an das Schema für die Antwortdatei, den Sie erstellen, wenn Sie Ihre **Ziele** in die Antwortdatei angeben.

    Stellen Sie außerdem sicher, dass keine duplizierten Einstellungen in beiden Antwortdateien vorhanden sind. Die [MCSF Windows Provisioning Settings Zuordnung](https://msdn.microsoft.com/library/windows/hardware/mt450421) können Sie Ihnen die Einstellungen zu erkennen, die jedes Framework entsprechen.

3.  Führen Sie die Windows ICD CLI, um das Bild zu erstellen. Weitere Informationen finden Sie unter [erstellen ein Bilds für Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image).

4.  Signieren Sie das Bild, sodass es zu einem Gerät zugeordnet werden kann. Weitere Informationen finden Sie unter [Signieren einer vollständigen flash aktualisierungsabbild (FFU)](sign-a-full-flash-update--ffu--image.md).

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und mobilen blinkende](building-and-flashing-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20a%20hybrid%20method%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





