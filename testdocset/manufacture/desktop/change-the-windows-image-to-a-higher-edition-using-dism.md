---
author: Justinha
Description: "Ändern Sie das Windows-Abbild in eine höhere Edition mithilfe von DISM"
ms.assetid: 754e7ef2-85fe-4b45-94d7-d7bd1db6eaa1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Ändern Sie das Windows-Abbild in eine höhere Edition mithilfe von DISM"
ms.openlocfilehash: 466f0acbe2be0476183f1787d379591d010cf536
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="change-the-windows-image-to-a-higher-edition-using-dism"></a>Ändern Sie das Windows-Abbild in eine höhere Edition mithilfe von DISM


Die Windows® Edition – Wartung Befehle können Sie um eine Version von Windows auf eine höhere Version von Windows zu ändern. Die Editionspakete für jede mögliche Zieledition werden im Windows-Abbild bereitgestellt. Dies ist ein Bild Edition-Familie genannt. Sie können die Befehlszeilenoptionen verwenden, um potenzielle Zieleditionen aufzulisten. Da die Ziel-Versionen bereitgestellt werden, können Sie ein einzelnes Bild service, und die Updates werden entsprechend auf jede Edition im Bild angewendet.

Benötigen Sie einen Product Key die Windows-Edition online zu ändern. Offline Änderungen erfordern keinen Product Key. Wenn Sie das Bild in eine höhere Version unter Verwendung von – Wartung offline ändern, können Sie den Product Key hinzufügen, indem Sie eine der folgenden Methoden:

-   Geben Sie den Product Key während der Out-of-Box-Experience (OOBE).

-   Verwenden einer Antwortdatei während des **specialize** Konfiguration Schritts den Product Key eingeben.

-   Verwenden Sie Deployment Image Servicing und Management (DISM) und die Windows Edition zum Warten Befehlszeilenoption **/set-productkey/Set-ProductKey** nach dem Festlegen der Edition offline.

Weitere Informationen zu Product Keys finden Sie unter [Arbeiten mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md).

## <a name="span-idfindandchangecurrenteditionofwindowsspanspan-idfindandchangecurrenteditionofwindowsspanspan-idfindandchangecurrenteditionofwindowsspanfind-and-change-current-edition-of-windows"></a><span id="Find_and_Change_Current_Edition_of_Windows"></span><span id="find_and_change_current_edition_of_windows"></span><span id="FIND_AND_CHANGE_CURRENT_EDITION_OF_WINDOWS"></span>Suchen Sie und ändern Sie der aktuellen Version von Windows


Sie können feststellen, dass die Version von Windows Ihr Bild zurzeit durch Bereitstellen des Abbilds und Ausführen von DISM-Befehlen für das bereitgestellte Abbild festgelegt ist.

**Die aktuelle Version suchen**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Geben Sie in der Befehlszeile den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images
    ```

3.  Geben Sie den folgenden Befehl zum Bereitstellen von offline-Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images /Index:1 /MountDir:C:\test\offline
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die eine Bilddatei angeben.

4.  Geben Sie folgenden Befehl, erhalten die Version von Windows Ihr Bild ist derzeit festgelegt.

    ``` syntax
    Dism /Image:C:\test\offline /Get-CurrentEdition
    ```

    Welche Edition von Windows, die das Abbild derzeit festgelegt ist, zu beachten. Wenn das Bild bereits auf eine höhere Version geändert wurde, sollten Sie sie nicht erneut ändern. Es wird empfohlen, dass Sie die niedrigste Edition als Ausgangspunkt verwenden.

5.  Heben Sie die Bereitstellung des Bilds oder fahren Sie mit dem nächsten Verfahren fort. Wenn Sie Ihr Bild aufzuheben, geben Sie den folgenden Befehl aus.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

**So ändern Sie auf eine höhere Version von Windows**

1.  Geben Sie den folgenden Befehl zum offline-Windows-Abbild (sofern es nicht bereits bereitgestellt wird) bereitstellen.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images /Name:<Image_name> /MountDir:C:\test\offline
    ```

2.  Geben Sie den folgenden Befehl zum Windows-Editionen finden, die Sie Ihr Bild ändern können.

    ``` syntax
    Dism /Image:C:\test\offline /Get-TargetEditions
    ```

    Notieren Sie die Edition-ID für die Edition, den, der Sie ändern möchten.

    **Hinweis**  
    Ein Windows-Bild kann nicht auf eine niedrigere Edition festgelegt werden. Die niedrigste Edition wird nicht angezeigt, wenn Sie die **Option/Get-TargetEditions** ausführen. Sie sollten dieses Verfahren nicht auf ein Bild verwenden, die bereits auf eine höhere Edition geändert wurde.

     

3.  Geben Sie den folgenden Befehl angeben die Edition-ID des Windows-Abbilds auf eine höhere Version zu ändern.

    ``` syntax
    Dism /Image:C:\test\offline /Set-Edition:Professional
    ```

4.  Geben Sie den folgenden Befehl zum Entladen des Bilds und die Änderungen zu übernehmen.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[DISM Windows Edition zum Warten von Befehlszeilenoptionen](dism-windows-edition-servicing-command-line-options.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






