---
title: Erstellen einer mobilen Abbilds mithilfe von Windows ICD
description: "Verwenden Sie Windows ICD, wenn Sie ein Gerät erstellen, die auf einen Verweis Entwurf von einem Anbieter SoC basiert, oder wenn Sie für einen Prozess und optimiert für das Erstellen einer mobilen Bild suchen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9F7346F3-688F-4DB7-B535-1A4A86DEB3B4
ms.openlocfilehash: 26adf46bc8fdf725ccb092c007dbd6161b9c3695
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-windows-icd"></a>Erstellen einer mobilen Abbilds mithilfe von Windows ICD


Windows Imaging und Konfiguration Designer (ICD) ist ein Windows-provisioning-Tool, das Sie optimieren anpassen und Bereitstellen eines Windows-Abbilds kann. Es bietet eine Benutzeroberfläche oder die Befehlszeilenschnittstelle, die Sie verwenden können:

-   Konfigurieren von Einstellungen und Richtlinien für ein neue Anpassungen primär in Unternehmen und Education-spezifischen Szenarien wie Massen Registrierung und Unternehmensrichtlinien, einschließlich mobilen Bild und erstellen Sie das angepasste Bild.
-   Erstellen Sie ein multivariant Bild erstellen ein provisioning Paket, definiert Ziele und fügt die Bedingungen, die angeben, wenn die Einstellungen für eine Variante angewendet werden, und klicken Sie dann als Eingabe für die Erstellung eines mobilen Abbilds mithilfe des provisioning-Pakets.

Verwenden Sie Windows ICD, wenn Sie ein Gerät erstellen, die auf einen Verweis Entwurf von einem Anbieter SoC basiert, oder wenn Sie für einen Prozess und optimiert für das Erstellen einer mobilen Bild suchen.

## <a name="to-build-a-mobile-image-using-the-windows-icd-ui"></a>Erstellen einer mobilen Bild mithilfe der Windows-ICD-Benutzeroberfläche


Die Windows-ICD-Benutzeroberfläche (UI) stellt eine leicht zu bedienende-Schnittstelle zum Erstellen eines benutzerdefinierten mobilen Abbilds bereit. Die Benutzeroberfläche zeigt alle Einstellungen, dass Sie für ein einzelnes variant mobilen Bild konfigurieren können und es dann führt Sie durch ein schrittweiser Prozess zum Erstellen und sogar flash angepassten Abbilds.

Beachten Sie jedoch, dass es gibt einige Einstellungen, die nicht über das Windows-Framework Bereitstellung verfügbar sind und diese sind also nicht so konfigurieren Sie mithilfe von Windows ICD verfügbar. Dazu gehören [MCSF Einstellungen nicht unterstützt bei der Bereitstellung von Windows](https://msdn.microsoft.com/library/windows/hardware/mt573153) als auch die Unterstützung für Datenbestand (beispielsweise Klingeltöne, lokalisierten Zeichenfolgen usw.).

Wenn Sie nicht diese Einstellungen und Objekte für das Bild konfigurieren müssen, können die Benutzeroberfläche des Windows-ICD das individuelle, einzelne Variante mobile Abbild erstellt durch Befolgen der Anweisungen in [Erstellen und Bereitstellen eines Abbilds für Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/dn916106).

## <a name="to-build-a-mobile-image-using-the-windows-icd-cli"></a>Erstellen einer mobilen Bild mit der Windows-ICD CLI


Wenn Sie möchten mehr Flexibilität beim Erstellen des Abbilds jedoch die verfügbaren mobilen Einstellungen in Windows provisioning Framework konfigurieren möchten, können Sie der Windows-ICD Befehlszeilenschnittstelle (CLI) verwenden. Verwenden der Windows ICD CLI, ermöglichen Folgendes:

-   Wählen Sie, wie der Pakete und Features in Ihrem Bild enthalten definieren – entweder durch die Verwendung einer OEMInput.xml oder einer BSP.config.xml-Datei als eine der Eingaben.
-   Erstellen Sie ein einzelnes variant mobiles Bild.
-   Erstellen Sie eine Bereitstellung Paket mit multivariant Einstellungen, die Sie für die Erstellung einer mobilen multivariant Bild als eine der Eingaben verwenden können.

Ob Sie ein multivariant oder einzelnen variant Bild erstellen, müssen Sie auswählen, wie Sie den Inhalt des Bilds definieren möchten. Diese Einstellung bestimmt die Pakete oder Features, die Teil des Bilds werden sein und Hardware enthalten Unterstützung der Sprachen, Land/Ihrer Region-spezifische apps oder Funktionen, und so weiter.

**Definieren Sie den Inhalt des Bilds**

1.  **Mithilfe einer BSP.config.xml-Datei**. Sie können diese als Teil des BSP Kit herunterladen oder Sie können eine eigene BSP.config.xml Datei ausführen das BSP Kit Konfigurationstools SoC dessen Hersteller und die Komponententreiber generieren.

    Die Datei BSP.config.xml ist erforderlich, wenn Sie haben versucht, oder ICD Benutzeroberfläche von Windows verwenden, um das Bild erstellen möchten. Wenn Sie ein mobiles Bild für ein Hardware-Design-Referenz entwickeln, sollten Sie die Datei BSP.config.xml bereits Verweis für Ihre Hardware verfügen.

2.  **Mithilfe einer OEMInput.xml-Datei**. Eine OEMInput.xml-Datei beschreibt die erforderlichen und optionalen Elemente, die für die Definition der mobilen Bilds verwendet werden. Wenn Sie eine mobile Bild für ein Hardware-Verweis-Design oder Ihre eigene Hardware-Design erstellen und Sie auch Ihre eigenen Features als Teil des Bilds hinzufügen möchten, können die Datei OEMInput.xml dazu auf.

    Das mobile Kit enthält OEMInput.xml-Beispiele, die Sie als Ausgangspunkt verwenden können. Finden Sie in der Windows-Ordner, C: Installieren\\Program Files (x86)\\Windows Kits\\10\\OEMInputSamples auf X64 hosten, Computern oder C:\\Program Files\\Windows Kits\\10\\OEMInputSamples auf X86-Hostcomputer.

    Erfahren Sie mehr über OEMInput Inhalt und andere Features, die Sie Ihr Bild hinzufügen können, finden Sie unter [OEMInput Dateiinhalte](oeminput-file-contents.md) und [optionalen Features zum Erstellen von Bildern](optional-features-for-building-images.md). Wenn Sie bereits mit OEMInput.xml vertraut sind und wissen, wie Sie Ihre eigene Funktion in das Bild und andere Funktionen Sie hinzufügen möchten, finden Sie unter den anderen Themen unter [definieren das Bild mit OEMInput und Feature-Manifestdateien](define-the-image-using-oeminput-and-feature-manifest-files.md).

Um einen mobilen Bild zu erstellen, benötigen Sie auch eine provisioning-Paket oder Windows Bereitstellungsdatei Antwort als Eingabe verwenden. Diese Dateien geben die Anpassung Einstellungen und Objekte, die Sie in das Abbild einschließen möchten.

-   Benutzeroberfläche ICD von Windows können durch Konfigurieren der Einstellungen, und klicken Sie dann Exportieren einer Bereitstellung Paket ein provisioning Paket generiert wird.

-   Der Windows-ICD-Benutzeroberfläche können Sie schnell Antwort eine Windows-Bereitstellungsdatei generieren. Bei jedem start von ein neues Projekt mithilfe der Benutzeroberfläche erstellt Windows ICD immer eine customizations.xml im Projektordner. Dies in der Regel befindet sich in Ihren Dokumenten\\Windows Imaging und Konfiguration Designer (WICD)\\*Projekt\_Namen* Ordner. Wenn Sie einen von Grund auf neu erstellen möchten, finden Sie unter [Windows Bereitstellungsdatei Antwort](https://msdn.microsoft.com/library/windows/hardware/dn916153) zu verstehen sind das Schema, und klicken Sie dann finden Sie unter [Windows-Bereitstellung (Referenz)](https://msdn.microsoft.com/library/windows/hardware/dn953942) auf Informationen zu den Einstellungen, die Sie konfigurieren.

    **Hinweis**  Es wird empfohlen, mithilfe der Windows-ICD-Benutzeroberfläche das provisioning-Paket oder die Antwortdatei der Windows-Bereitstellung auf einfache Weise zu generieren.

     

Um ein einzelnes variant mobilen Bild zu erstellen, gehen Sie wie folgt vor:

**Erstellen Sie ein einzelnes variant mobiles Bild**

1.  Finden Sie unter [Erste Schritte mit Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916112) , und befolgen Sie die Anweisungen zum Starten der Windows-ICD CLI aus.

2.  [Erstellen Sie ein Bild für Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image) Windows ICD CLI verwenden.

Windows unterstützt einen Mechanismus, der können Sie ein einzelnes Bild erstellen können, die für mehrere Märkte können. Sie können dynamisch Sprachen konfigurieren branding, apps und -Einstellungen je nach Bedingungen. Erstellen einer mobilen-Abbild mit multivariant Einstellungen ist nur über die Windows-ICD CLI möglich.

Der Prozess zum Erstellen eines multivariant mobilen Abbilds ähnelt erstellen ein einzelnes variant mobiles Bild mit der Ausnahme, dass ein provisioning Paket zu erstellen, müssen mit multivariant Einstellungen zuerst und anschließend müssen verwenden dieses Paket als eine der Eingaben Wenn Sie bereit sind, das Bild zu erstellen.

Multivariant mobile Bild zu erstellen, gehen Sie wie folgt vor:

**Erstellen einer mobilen multivariant Bild**

1.  Erstellen Sie das Bereitstellung Paket. Weitere Informationen finden Sie unter [Erstellen einer Bereitstellung Paket mit multivariant Settings](https://msdn.microsoft.com/library/windows/hardware/dn916108).

    Sie verwenden dieses Paket als eine der Eingaben für den nächsten Schritt.

2.  [Erstellen Sie ein Bild für Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image) Verwendung der Windows-ICD CLI.

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und mobilen blinkende](building-and-flashing-images.md)

[Erstellen einer mobilen Bild mit einer Hybridmethode](build-a-mobile-image-using-windows-provisioning-and-mcsf-answer-files.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20Windows%20ICD%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





