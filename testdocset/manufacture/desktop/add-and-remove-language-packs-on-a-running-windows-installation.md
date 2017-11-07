---
author: Justinha
Description: "Hinzufügen und Entfernen von Language Packs auf einem ausgeführten Windows-Installation"
ms.assetid: 0e3f0b85-417e-4e17-869e-05ae37e98c8f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen und Entfernen von Language Packs auf einem ausgeführten Windows-Installation"
ms.openlocfilehash: 14f96d0bc2f2ec2361a4f3f105ae983dafcc7dca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-language-packs-on-a-running-windows-installation"></a>Hinzufügen und Entfernen von Language Packs auf einem ausgeführten Windows-Installation


Sie können die Unterstützung für zusätzliche Sprachen auf einem ausgeführten Betriebssystem oder zu einem offline Bild hinzufügen. Informationen zum Installieren zu einem offline-Abbild Sprachen finden Sie unter [Hinzufügen und Entfernen von Language Packs Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md).

Informationen zum Installieren von Benutzeroberflächen-Sprachpaketen (Benutzeroberflächen-Sprachpaketen) finden Sie unter [Hinzufügen von Benutzeroberflächen-Sprachpaketen Windows](add-language-interface-packs-to-windows.md).

In Windows 10 Benutzer können installieren mehr Sprachen und Features auf **Einstellungen** &gt; **Uhrzeit- und Sprache** &gt; **Region & Sprache** &gt; **Hinzufügen einer Sprache**. 

## <a name="span-idonlinespanspan-idonlinespanadd-a-language-pack-online"></a><span id="online"></span><span id="ONLINE"></span>Hinzufügen eines Language Packs im Onlinemodus


Wenn Sie mithilfe von DISM Sprachpakete hinzufügen, werden die lizenzierungsbedingungen für wie viele Language Packs für die Windows-Edition ausgeführt werden dürfen nicht überprüft. Wenn Sie mehrere Sprachpakete hinzufügen, werden alle nicht standardmäßigen und nicht vom Benutzer ausgewählte Sprachen vom Computer nach einer bestimmten Zeitspanne entfernt. Weitere Informationen finden Sie unter [Hinzufügen von Language Packs auf Windows](add-language-packs-to-windows.md).

**Hinweis**  
Language Packs können Sie auch Vorinstallation von Windows und Windows-Wiederherstellung Installationen hinzufügen. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md) und [Windows RE anpassen](customize-windows-re.md).

 

**So fügen Sie ein Language Pack mithilfe von DISM hinzu**

1.  Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, auf dem laufenden Betriebssystem.

2.  Geben Sie den folgenden Befehl zum Hinzufügen eines Language Packs (in diesem Beispiel Spanisch) für das Betriebssystem. 

    ``` syntax
    Dism /online /Add-Package /PackagePath:C:\test\LangPacks\Microsoft-Windows-Client-Language-Pack_x64_es-es.cab
    ```

Weitere Informationen zu DISM Internationale Wartung-Befehlen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Ein Windows-Abbild mithilfe von DISM-Service](service-a-windows-image-using-dism.md)

[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

 

 






