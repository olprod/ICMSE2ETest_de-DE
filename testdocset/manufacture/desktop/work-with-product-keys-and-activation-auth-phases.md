---
author: Justinha
Description: Arbeiten Sie mit Product Keys und Aktivierung
ms.assetid: 923c0cd1-527c-4610-b979-e068fcc0ef99
MSHAttr: PreferredLib:/library/windows/hardware
title: Arbeiten Sie mit Product Keys und Aktivierung
ms.openlocfilehash: 1dbf0cb2c98b48736789bdb08b462ddf779f15be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="work-with-product-keys-and-activation"></a>Arbeiten Sie mit Product Keys und Aktivierung


Sie können einen Product Key während einer automatischen Installation von Windows® durch Einschließen in die Antwortdatei eingeben.

Die Product Keys können auch ein Bild, das während einer automatisierten Installation von Windows installieren wählen.

## <a name="span-idinthistopicspanspan-idinthistopicspanspan-idinthistopicspanin-this-topic"></a><span id="In_this_Topic"></span><span id="in_this_topic"></span><span id="IN_THIS_TOPIC"></span>In diesem Thema


-   [Wählen Sie die Windows-Edition zu installieren](#selectwhichwindowstoinstall)

-   [Aktivieren von Windows](#activatewindowsbyusingaproductkey)

## <a name="span-idselectwhichwindowstoinstallspanspan-idselectwhichwindowstoinstallspanspan-idselectwhichwindowstoinstallspanselect-which-windows-edition-to-install"></a><span id="SelectWhichWindowsToInstall"></span><span id="selectwhichwindowstoinstall"></span><span id="SELECTWHICHWINDOWSTOINSTALL"></span>Wählen Sie die Windows-Edition zu installieren


Um eine Windows-Edition installieren ausgewählt haben, können Sie eine der folgenden Aktionen ausführen:

-   Installieren Sie Windows manuell, ohne eine Antwortdatei ein. Windows-Setup installiert die Standard-Edition von Windows-Produkt-DVD.

-   Installieren von Windows mit einer Antwortdatei, und fügen Sie einen Product Key in Microsoft-Windows-Setup\\UserData\\ProductKey\\`Key`. Jeder Product Key ist spezifisch für eine Windows-Version. Eingeben des Product Keys in dieser Einstellung wird Windows nicht aktiviert.

-   Installieren von Windows mit einer Antwortdatei, und geben Sie manuell in einem Product Key während der Installation von Windows. Der Product Key wählt eine Windows-Edition zu installieren.

**Warnung**  
Wenn Sie mehrere Windows-Abbilder mit der gleichen Windows-Edition, die in der gleichen Windows-Bilddatei (WIM) gespeichert sind verfügen, können Sie die Einstellung: Einrichten von Microsoft Windows\\ImageInstall\\OSImage\\InstallFrom\\ `MetaData` , sie zu unterscheiden. Sie müssen einen Product Key mit einer der Methoden in der vorherigen Liste aufgeführten weiterhin angeben.

 

Informationen zum Verwalten von Product Keys für Windows, wenn das Windows-Abbild auf eine höhere Edition ändern finden Sie unter [Ändern des Windows-Abbilds auf eine höhere Edition DISM verwenden](change-the-windows-image-to-a-higher-edition-using-dism.md).

## <a name="span-idactivatewindowsbyusingaproductkeyspanspan-idactivatewindowsbyusingaproductkeyspanspan-idactivatewindowsbyusingaproductkeyspanactivate-windows"></a><span id="ActivateWindowsByUsingAProductKey"></span><span id="activatewindowsbyusingaproductkey"></span><span id="ACTIVATEWINDOWSBYUSINGAPRODUCTKEY"></span>Aktivieren von Windows


Um automatisch Windows über einen Product Key aktivieren, können Sie eine der folgenden Aktionen ausführen:

-   Verwenden Sie das Microsoft-Windows-Shell-Setup\\ `ProductKey` für die unbeaufsichtigte Installation Einstellung. Sie können einen einfachen Verwendung Product Key oder Volume License Multiple Activation Key verwenden. Weitere Informationen finden Sie unter [Volume Activation Planning Guide](http://go.microsoft.com/fwlink/p/?LinkID=734870).

    Der Product Key verwendet, um Windows zu aktivieren, muss die Windows-Version übereinstimmen, die Sie installieren. Wenn Sie einen Product Key zum Auswählen einer Version von Windows verwenden, wird empfohlen, die mit demselben Schlüssel, um Windows, zu aktivieren, damit die zu installierende Edition die Edition identisch ist, die Sie aktivieren.

-   Original Equipment Manufacturers (OEMs) können OEM-spezifische Aktivierung Tools verwenden.

Wenn Sie ein Product Key nicht vor dem Out-Of-Box-Experience (OOBE) bereitgestellt werden, fordert OOBE der Endbenutzer einen Product key. Wenn der Endbenutzer dies während OOBE überspringt, wird der Benutzer einen gültigen Product Key eingeben später erinnert werden.

**Warnung**  
In den meisten Bereitstellungsszenarios für Windows 8, Sie müssen nicht mehr verwenden Sie die `SkipRearm` beantworten Datei-Einstellung, um die Windows-produktaktivierung Uhr zurückgesetzt, wenn Sie den Befehl **Sysprep** mehrmals auf einem Computer ausführen. Windows 8 die `SkipRearm` Einstellung wird an der Windows-Lizenzierung Zustand verwendet. Wenn Sie eine Retail Product Key oder Volume License Product Product Key angeben, wird Windows automatisch aktiviert. Sie können den Befehl **Sysprep** bis 8 zusätzliche Zeiten auf ein einzelnes Windows Bild oben ausführen. Nach dem Ausführen von Sysprep 8 Zeiten auf einem Windows 8-Abbild, müssen Sie das Windows-Abbild neu erstellen. Weitere Informationen zu Windows-Komponenten und Einstellungen, die Sie zu einer Antwortdatei hinzufügen können, finden Sie in der [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[Sysprep (verallgemeinern) einer Windows-installation](sysprep--generalize--a-windows-installation.md)

[Ändern Sie das Windows-Abbild auf eine höhere Edition mithilfe von DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)

 

 






