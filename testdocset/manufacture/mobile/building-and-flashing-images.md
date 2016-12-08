---
title: Erstellen und mobilen blinkende
description: "Hier finden Sie Informationen, die Sie erstellen und flash Bilder auf Ihrem Windows-10-Mobile-Gerät unterstützen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4862b9a9-3619-45cd-a612-77bd4ebb6ca2
ms.openlocfilehash: 1540184993830ac40d42160252a8413454f9f497
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="building-and-flashing-mobile-images"></a>Erstellen und mobilen blinkende


Hier finden Sie Informationen, die Sie erstellen und flash Bilder auf Ihrem Windows-10-Mobile-Gerät unterstützen.

## <a name="a-href-id1---define--customize--and-build-an-imagea1-define-customize-and-build-an-image"></a><a href="" id="1---define--customize--and-build-an-image"></a>1. definieren Sie, passen Sie an und erstellen Sie ein Bild


Um ein benutzerdefiniertes Abbild zu erstellen, das für mobile Geräte zugeordnet werden kann, können Sie entweder die neue Windows Imaging und Konfiguration Designer (ICD) oder klassische ImgGen.cmd oder einer hybriden dieser Methoden über die Windows-ICD-Befehlszeilenschnittstelle verwenden. Finden Sie unter [Anpassungen für Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/mt481438) , um zu entscheiden, welche Methode Sie eine Anpassung Gerät erfüllen mithilfe müssen muss.

-   **Verwenden von Windows ICD**: dieses Tool führt Sie durch den Prozess beim Erstellen von Bildern für Windows 10 Mobile mithilfe von Windows provisioning Framework. Verwenden Sie dieses Tool, wenn Sie ein Gerät erstellen, die auf einen Verweis Entwurf von einem Anbieter SoC basiert. Weitere Informationen zu dem Tool finden Sie unter [Windows Imaging und Konfiguration Designer](https://msdn.microsoft.com/library/windows/hardware/dn916113). Zum Erstellen einer mobilen Bild, finden Sie unter [Erstellen eines mobiles Abbilds mithilfe von Windows-ICD](build-a-mobile-image-using-windows-icd.md).

-   **Mithilfe von ImgGen.cmd**: Wenn Sie ein Gerät basierend auf Ihrer eigenen Hardware-Design erstellen oder Sie können mit MCSF Anpassung Antwortdateien und andere Ressourcen, die generiert wurden, verwenden der Windows Phone 8.1 ausgeliefert legacy-Tools eine angepasste mobile Bild verwenden dieses Tools generieren. Zum Einstieg finden Sie unter [Erstellen eines mobilen Abbilds ImgGen.cmd verwenden](building-a-phone-image-using-imggencmd.md).

-   **Bei Verwendung einer Hybridmethode**: Wenn Sie eine Datei OEMInput.xml, um den Inhalt des Abbilds vollständig definieren verwenden möchten, nutzen Sie die neuen Runtime-Einstellungen, Unternehmensrichtlinien und Registrierung verfügbaren Einstellungen im Windows-Bereitstellung und auch möglich vollständig anpassen Hardware und Konnektivität für die Geräte, apps Vorinstallation und Hinzufügen von Objekten wie Klingeltöne und lokalisierte Zeichenfolgen über MCSF , können Sie eine hybride Methode mithilfe der Windows-ICD CLI das Abbild erstellt. Finden Sie weitere Informationen finden Sie unter [Erstellen einer mobilen Bild mit einer Hybridmethode](build-a-mobile-image-using-windows-provisioning-and-mcsf-answer-files.md).

## <a name="2-sign-an-image"></a>2. Anmelden ein Bild


Unabhängig davon, welche Methode Sie zum Anpassen und Erstellen von Images verwendet haben, müssen Sie Ihr Bild kryptografisch signieren, bevor Sie es zu einem Gerät bereitstellen können.

-   [Melden Sie sich eine vollständige flash aktualisierungsabbild (FFU)](sign-a-full-flash-update--ffu--image.md)

## <a name="3-flash-an-image-to-a-device"></a>3. flash eines Bilds zu einem Gerät


Anhand der Informationen in den folgenden Themen erfahren blinken und Update-Tools:

-   [Verwenden von Microsoft bereitgestellten blinkende tools](use-the-flashing-tools-provided-by-microsoft.md)

-   [Update-Pakete auf einem Gerät und rufen Sie Update-Paketprotokolle](update-packages-on-a-phone-and-get-package-update-logs.md)

-   [Aktualisieren von Lösungspaketen in ein. FFU Bilddatei](update-packages-in-an-ffu-image-file.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Building%20and%20flashing%20mobile%20images%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")




