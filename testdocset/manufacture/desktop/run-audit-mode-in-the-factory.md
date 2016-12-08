---
author: Justinha
Description: "Führen Sie im Überwachungsmodus im Unternehmen"
ms.assetid: e8262c69-3fae-455e-9cbd-88c486f92094
MSHAttr: PreferredLib:/library/windows/hardware
title: "Führen Sie im Überwachungsmodus im Unternehmen"
ms.openlocfilehash: bb4da88d9308ec72a8e06353a5eb42a210503128
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="run-audit-mode-in-the-factory"></a>Führen Sie im Überwachungsmodus im Unternehmen


In Build-zu-eins-Szenarien OEMs starten das Ziel PCs Überwachungsmodus um kundenspezifische apps, die Sprachen, die Treiber zu installieren und zusätzliche Konfigurationen vornehmen.

Nach dem letzten Assembly des PCs führen Sie die Integrität zu testen, um sicherzustellen, dass der PC-Option ordnungsgemäß konfiguriert ist.

Wenn Sie bereit sind, starten Sie den PC mit Windows PE oder ein anderes Betriebssystem, das Ihnen die Installation des benutzerdefinierten Windows-Abbilds auf den PC ermöglicht. Können Sie den PC mit einem USB-Schlüssel starten, oder Sie können den PC über das Netzwerk mit PXE-Start und Windows-Bereitstellungsdienste starten.

Es wird empfohlen, dass Sie Windows PE und DISM zum Starten des PCs und Anwenden des benutzerdefinierten Windows-Abbilds verwenden.

-   [Anwenden von Abbildern mithilfe von DISM](apply-images-using-dism.md)

-   [Windows PE für Windows 10](winpe-intro.md)

-   [Übersicht über die Dienste von Windows-Bereitstellung](http://technet.microsoft.com/library/hh831764.aspx)

Wenn das Bild angewendet wird, starten Sie den PC im Überwachungsmodus.

-   [Übersicht über Audit-Modus](audit-mode-overview.md)

Klicken Sie im Überwachungsmodus aktiviert, installieren Sie Kunden angefordert Software, Treiber in Bezug auf dem PC und weitere Elemente. Während Sie im Überwachungsmodus Sie außerdem die neuesten Windows-Updates installieren können. In den folgenden Themen finden Sie weitere Details zum Treiber, Language Packs und Windows-Updates installieren:

-   [Gerätetreibern und Übersicht über die Bereitstellung](device-drivers-and-deployment-overview.md)

-   [Language Packs](language-packs-and-windows-deployment.md)

-   [Ein Windows-Abbild mithilfe von DISM-Service](service-a-windows-image-using-dism.md)

Denken Sie daran, die die weitere Elemente, die Sie installieren auf des Factory Floor erhöht den Zeitaufwand für die Zusammenstellung von, installieren und den PC Feld.

Nachdem Sie Ihre Audit Modus Installationen abgeschlossen haben, müssen Sie Sysprep/oobe um sicherzustellen, dass der Endbenutzer die Out-of-Box-Experience durchläuft und die Lizenzbedingungen akzeptiert ausführen. Erfassen Sie die Windows-Installation auf die Wiederherstellungspartition rest den PC-Option auf Standardeinstellung bei Benutzern helfen. Auf diese Weise in der Factory können Sie sicherstellen, dass die Build-zu-eins-Anpassungen, die Kunden im Bild Recovery sind.

Sie müssen den PC zu Windows PE erneut zu erfassen und gelten die Windows-Installation für die Wiederherstellungspartition zu starten.

Im folgende Thema wird beschrieben, wie das Wiederherstellungsabbild zu erstellen:

-   [Bereitstellen von Drucktaste Reset-Features](deploy-push-button-reset-features.md)

Nach das Wiederherstellungsabbild erfasst wird, können Sie den PC Herunterfahren, Textfelder und liefern.

Abhängig vom Umfang der Einheiten, die Sie ausgeliefert werden, sollten Sie es in Erwägung ziehen einen oder mehrere PCs aus der Zeile, um sicherzustellen, dass die Systeme, die Sie erstellen Qualität ungewöhnlich erfüllen.

 

 





