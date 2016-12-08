---
author: kpacquer
Description: Teilweise Bild signieren
ms.assetid: dac19053-5243-45f2-9041-b9de9ea0bd80
MSHAttr: PreferredLib:/library/windows/hardware
title: Teilweise Bild signieren
ms.openlocfilehash: ec80d4f41b1d35e1e9a6feed31f8927a40ba8aed
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="partial-image-signing"></a>Teilweise Bild signieren


Frühere Versionen des Clients Aufnahme unterstützt nur vollständige FFU Bilder signieren. Es gibt jedoch mehrere gültige Szenarien, in denen Sie eine partielle FFU Bild anstatt ein Vollbild angemeldet sein, z. B. übermitteln möchten:

-   Zwischenspeichern-Funktionen wie in Windows Standard Paket Konfiguration (WSPC) Szenario ausführlich beschrieben, wie beschrieben unter [Windows Standard Packen Konfiguration (WSPC)-Anforderungen für den Einzelhandel Bilder](https://msdn.microsoft.com/library/dn756781)Paket signiert.

-   MMOS Pakete für die Validierung und Problembehandlung bei der Herstellung signieren.

-   Eine schnelle Testen von Updates für Fehler, die nicht selbst auf Test Bilder manifest. Beispielsweise zuvor könnte eine Verzögerung von Woche oder mehr zwischen dem Zeitpunkt Ihrer Fix eingecheckt wird auf den tatsächlichen Build der mit dem Fix Binärdatei. Um diese Wartezeit zu reduzieren, können Sie jetzt erstellen eine lokale Kopie der Binärdatei, erstellen Sie das Paket, übermitteln der partiellen Package, um Verkaufsversion signiert werden und anschließendes entgegennehmen signierten teilweise Verkaufsversion Paket vor erneut integrieren und es mit IUTool auf das Telefon blinken.

-   Installieren von testen und Debuggen von Tools Retail Bilder zum Debuggen von Problemen, die sich nur auf Retail Bilder manifest.

Die neueste Version des Clients Aufnahme implementiert jetzt Funktionen zur Unterstützung der partiellen Bild signieren, verursachten die Notwendigkeit für Sie manuell eine eigene erstellen "hergestellt" Pakete und UpdateHistory.xml-Dateien beim Senden von Paketen an den Client Aufnahme signiert werden. Beachten Sie, dass Ihr Konto die Berechtigung zum Signieren von Teile von Bildern, um diese neue Funktionalität anderweitig zu verwenden benötigen solche Übermittlungen schlägt fehl.

## <a name="span-idcontextualindividualpackagesigningspanspan-idcontextualindividualpackagesigningspanspan-idcontextualindividualpackagesigningspancontextual-individual-package-signing"></a><span id="Contextual_Individual_Package_Signing"></span><span id="contextual_individual_package_signing"></span><span id="CONTEXTUAL_INDIVIDUAL_PACKAGE_SIGNING"></span>Kontextbezogene einzelnen Paket signieren


OEMs möglicherweise ein Paket caching-Mechanismus zur Optimierung ihrer Buildvorgang nutzen. In diesem werden Prozess sowie Retail signierte Pakete zwischengespeichert, damit sie über mehrere Bilder wiederverwendet werden können. Daher muss neuer Code Retail angemeldet, und klicken Sie dann in den Paketcache, um sie über mehrere Bilder erneut verwenden hinterlegt sein. Dazu sollten Sie ein neues Paket erstellen, das binäre und ein Bild enthält. Jedoch können anstelle der Übermittlung von allen Paketen aus diesem Abbild Retail signiert werden Sie jetzt nur das Paket senden, das das Update enthält. Verwenden Sie dazu des Aufnahme Clients `Initialize-FirmwareSubmission` Cmdlet mit `-TypeOfSubmission PartialImage`; angemeldet Angabe des Verzeichnisses, das das neue Paket liegend Retail enthält, zusammen mit der UpdateHistory.xml-Datei, die während der Generierung der Abbilder in ein Verzeichnis erstellt. Die Aufnahme-Client wird das Paket und die Datei UpdateHistory.xml abrufen. Microsoft wird dann die Übermittlung basierend auf der Datei UpdateHistory.xml überprüfen und Einzelhandel Signieren des Pakets. Anschließend können Sie die `Get-SignedFirmwareSubmission` Cmdlet, um die Retail signierten Pakets erhalten und platzieren es im Paketcache. Beachten Sie, dass Ihr Konto über die Berechtigung zum Signieren der einzelnen Pakete auf diese Weise, um diese neue Funktionalität anderweitig zu verwenden benötigen, schlägt fehl, alle solchen Übermittlungen.

## <a name="span-idcontextfreeindividualpackagesigningspanspan-idcontextfreeindividualpackagesigningspanspan-idcontextfreeindividualpackagesigningspancontext-free-individual-package-signing"></a><span id="Context_Free_Individual_Package_Signing"></span><span id="context_free_individual_package_signing"></span><span id="CONTEXT_FREE_INDIVIDUAL_PACKAGE_SIGNING"></span>Kontext freien einzelnen Paket signieren


OEMs jetzt können auch den Aufnahme Client Sie "Kontext kostenlose" Übermittlungen erstellen. Angenommen, wenn Sie ein neues MMOS Paket basierend auf Änderungen an einer Produktlinie an, die kürzlich vorgenommen wurden erstellen müssen, können Sie tätigen MMOS-Paket in einem Verzeichnis das Verzeichnis angeben, wenn die Aufnahme Client während der Übermittlung als auch angeben, dass die Übermittlung "Kontext frei." ist Eine solche Paket Übermittlungen werden ausschließlich die EKU-Kombination Grundlage angemeldet.

## <a name="span-idpartialimagepackagesigningexamplespanspan-idpartialimagepackagesigningexamplespanspan-idpartialimagepackagesigningexamplespanpartial-image-package-signing-example"></a><span id="Partial_Image_Package_Signing_Example"></span><span id="partial_image_package_signing_example"></span><span id="PARTIAL_IMAGE_PACKAGE_SIGNING_EXAMPLE"></span>Beispiel für partielle Bild-Paket signieren


So bereiten Sie eine partielle FFU signiert werden vor:

``` syntax
PS> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue -TypeOfSubmission PartialImage -UpdateHistoryPath c:\input\UpdateHistory.xml -OemInputPath c:\input -OutputFilePath c:\output -PartialImageDirectory c:\input\spkg
```

 

 





