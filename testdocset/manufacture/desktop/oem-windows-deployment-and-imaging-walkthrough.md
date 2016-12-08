---
author: KPacquer
Description: OEM-Windows-Desktop-Bereitstellung und Imaging Lab
ms.assetid: 04dace4d-9df9-4ead-b23d-f168832c9c04
MSHAttr: PreferredLib:/library/windows/hardware
title: OEM-Windows-Desktop-Bereitstellung und Imaging Lab
ms.openlocfilehash: 726d3a6433970629fe1374e3dc0cc81387d9c59f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oem-windows-desktop-deployment-and-imaging-lab"></a>OEM-Windows-Desktop-Bereitstellung und Imaging Lab

Erste zum Erstellen und Testen der Windows-10-Desktop-PCs bereit? Diese Übungseinheit enthält Strategien für die Basis Bilder erstellen und diese mit Befehlszeilentools zu aktualisieren. Die Befehle können in Skripte integriert werden hilft Ihnen, schnell neue Bilder für bestimmte Märkte Kunden Ihre Bedürfnisse anpassen.

Neu in dieser Übungseinheit: 

* Mit Silo provisioning-Paketen können Sie jetzt erfassen und Windows-desktopanwendungen während der Bereitstellung jeweils einzeln anwenden. Dadurch werden einige der zeitaufwändige Schritte im Zusammenhang mit verallgemeinern und Bilder Neuaufnahme vermieden.

Steigen wir!

**Vorbereitung**

*  [Planen: Anpassen von Verweis Bilder für unterschiedliche Benutzergruppen](planning-create-different-product-designs-for-different-market-segments-sxs.md)

**Bereitstellen von Bildern**

*  [Abrufen von Tools zum Anpassen von Windows benötigt](get-the-tools-needed-to-customize-windows-sxs.md)
*  [Abrufen der Beispielskripts](windows-deployment-sample-scripts-sxs.md)
*  [Übung 1: Installieren von Windows PE](install-windows-pe-sxs.md)
*  [Übung 2: Bereitstellen von Windows mithilfe eines Skripts](deploy-windows-with-a-script-sxs.md)

**Anpassen der Fenster Bilder**

In diesen Übungseinheiten benötigen Sie das Windows-Abbild (install.wim) ändern. Während Sie die meisten dieser Aufgaben in beliebiger Reihenfolge ausführen können, sind nur einige abhängig:
*    **Hinzufügen von Updates vor Sprachen.** Dazu gehören Hotfixes, die allgemein verfügbare Versionen und Servicepacks. Wenn Sie ein Update später hinzufügen möchten, müssen Sie die Sprache erneut hinzufügen.
*    **Sprachen hinzufügen, bevor Sie apps**. Dazu gehören universellen Windows-apps und -desktopanwendungen. Wenn Sie später eine Sprache hinzufügen, müssen Sie die apps erneut hinzufügen.

Um die Änderungen vornehmen, müssen Sie den Bildinhalt in einen temporären Ordner bereitstellen und mithilfe von Tools wie DISM die Änderungen vornehmen. Heben Sie die Bereitstellung der Bilder und erneut bereitstellen.
   ![Bild: Bereitstellen eines Abbilds, Änderungen vornehmen und Aufheben der Bereitstellung des Abbilds](images/dep-win8-sxs-createmodelspecificfiles.jpg)

*  [Übung 3: Hinzufügen von Gerätetreibern (INF-Format)](add-device-drivers.md) (einschließlich Grundlagen zum Bereitstellen von Bilder)
*  [Übung 4: Hinzufügen von Updates und Upgraden Sie die edition](servicing-the-image-with-windows-updates-sxs.md)
*  [Übung 5: Hinzufügen von Sprachen](add-drivers-langs-universal-apps-sxs.md)
*  [Übung 6: Hinzufügen von universellen Windows-apps, Kacheln und Taskleiste pins](add-universal-apps-sxs.md)
*  [Übung 7: Einstellungen ändern, geben Sie die Product Keys und Ausführen von Skripts mit einer Antwortdatei (unattend.xml)](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)
*  [Übung 8: Hinzufügen eines Lizenzvertrags (OOBE.xml)](add-a-license-agreement.md)
*  [Übung 9: Ändern von Windows (Überwachungsmodus aktiviert)](prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md)

**Abschließende Vorgänge**

*  [Übung 10: Aktualisieren der Wiederherstellung](update-the-recovery-image.md)
*  [Übung 11: Verkleinern Sie die Bildgröße](shrink-your-image-size.md)
*  [Übung 12: Hinzufügen von desktopanwendungen und Einstellungen mit Silos zusammengefasst provisioning Pakete (SPPs)](add-desktop-apps-wth-spps-sxs.md) (einschließlich der Einstellungen für Microsoft Office Windows Store)
