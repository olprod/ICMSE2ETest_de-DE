---
author: kpacquer
Description: FFU Katalog signieren
ms.assetid: 31956395-2253-430e-a578-fc0218952a90
MSHAttr: PreferredLib:/library/windows/hardware
title: FFU Katalog signieren
ms.openlocfilehash: cf03834da5cdb7fbeb3a838d3110a98898245be6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ffu-catalog-signing"></a>FFU Katalog signieren


Die Tools, die erstellt wurden, zur Vereinfachung der Engineering und Fertigungsprozesse stellen Sie ein Microsoft-Zertifikat in den Speicher PK (Plattformschlüssel) UEFI bereit. Auf diese Weise können Microsoft, um das Bild zu signieren. OEM-Partnern richten Sie eigene Zertifikate zu PK Zertifikatspeicher OEM zum Signieren der FFU zu aktivieren.

OEM kann auch FFUs anmelden, wenn der OEM einen eigenen UEFI Tool zum Bereitstellen der signierenden Root/Fortgeschrittene im Speicher PK schreibt. Dies ist jedoch nicht empfohlen, weil Komplexität und Sicherheitsrisiko für Sie sowohl Microsoft teilweise eingeführt da erstellen und pflegen von UEFI Tools und die Wartung der Code Signieren von Zertifikaten und Infrastruktur komplexer ist. Dies gilt insbesondere für kleine oder neue OEMs, wie ein verlorene privater Schlüssel würde ermöglichen, dass beliebige Entitäten FFUs anzumelden, die auf der QRD OEM-Gerät geladen werden können und Sie jedoch die Kommunikation mit Microsoft für alle anderen signieren müssen.

Aus diesem Grund wurde um reduziert die Komplexität, und vereinfachen des Signiervorgang FFU Katalogs, der Aufnahme Client mit der neuen Funktionalität zur Unterstützung von Retail Signieren von FFU Kataloge aktualisiert.

## <a name="span-idoemverificationspanspan-idoemverificationspanspan-idoemverificationspanoem-verification"></a><span id="OEM_Verification"></span><span id="oem_verification"></span><span id="OEM_VERIFICATION"></span>OEM-Überprüfung


Ein Katalog FFU signiert für OEM. Eine wäre einen gültigen FFU-Katalog für OEM B Geräte da an den Store PK Vorschriften Microsoft intermediate Zertifikat ist ein einzelnes intermediate Zertifikat. Dies ist ein Risiko Bestäubung genannt. Aus diesem Grund werden um Bilder erstellt, indem eine OEM Freigabefunktion Flash-auf einer anderen OEM-Geräte absichtlich oder versehentlich zu verhindern, verwendete Mechanismus zum Signieren FFU Kataloge in der neuesten Version des Clients Aufnahme anders als andere Pakete Signieren verwendeten Mechanismus behandelt. OEM-Überprüfung tritt während der Signierung durch Prüfen der Metadaten mit dem FFU-Katalog in der Übermittlung von. OEM-ID der Übermittlung wird die im Katalog enthaltenen OEM-ID überprüft werden. Wenn die Werte nicht übereinstimmen, wird der signieranforderung FFU-Katalog abgelehnt. Darüber hinaus wird der Client Aufnahme Vergewissern Sie sich mit der Geschäftsdatenkatalog-Metadaten FFU die Integrität des Katalogs, indem Sie überprüfen Hash-Werte übergeben. Im nachstehenden Diagramm zeigt den Katalog FFU und die zugehörigen Metadaten, die für diese Überprüfung verwendet werden soll:

![Ffu Katalog signieren](images/ffucatalogsigning.jpg)

Nachdem Sie die ersten Tests auf dem neuen Bild abgeschlossen haben, muss das Bild beispielsweise auf einem Gerät Retail getestet werden. Sie erstellen ein FFU Bild für blinken und der Katalog FFU muss Verkaufsversion von Microsoft signiert werden, bevor das Bild zu einem Gerät Verkaufsversion zugeordnet werden kann. Verwenden Sie des Aufnahme Clients `Initialize-FirmwareSubmission` Cmdlet mit `-TypeOfSubmission FfuCatalog`, den Speicherort des Bilds FFU angibt. Der Client Aufnahme Extrahieren der FFU Katalog und die zugehörigen Metadaten aus dem Bild FFU und übergeben Sie, dass bei Microsoft als Verkaufsversion angemeldet. Signieren von Code überprüft die Integrität des Katalogs FFU und überprüft die OEM-ID des Katalogs gegen die OEM-ID des Kontos, das Sie über die signierenden Anforderung gesendet. Solange die OEM-ID der FFU catalog Übereinstimmungen die OEM-ID des Kontos der signierenden Anforderung Microsoft verarbeitet und Signieren des Katalogs FFU. Nach Abschluss des Vorgangs können Sie die `Get-SignedFirmwareSubmission` -Cmdlet zum erhalten die Retail signiert FFU Katalog vor signierten Katalog erneut wieder zurück in das Bild FFU integrieren, damit es zu einem Gerät zu Testzwecken zugeordnet werden kann.

## <a name="span-idffucatalogsigningexamplespanspan-idffucatalogsigningexamplespanspan-idffucatalogsigningexamplespanffu-catalog-signing-example"></a><span id="FFU_Catalog_Signing_Example"></span><span id="ffu_catalog_signing_example"></span><span id="FFU_CATALOG_SIGNING_EXAMPLE"></span>FFU Katalog Signieren – Beispiel


So bereiten Sie einen Katalog FFU signiert werden vor:

``` syntax
PS> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue -TypeOfSubmission FfuCatalog -UpdateHistoryPath c:\input\UpdateHistory.xml -OemInputPath c:\input -OutputFilePath c:\output -FfuPath c:\input\flash.ffu
```

 

 





