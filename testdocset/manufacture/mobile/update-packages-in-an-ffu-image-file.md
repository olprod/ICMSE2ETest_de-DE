---
title: "Aktualisieren von Lösungspaketen in ein. FFU Bilddatei"
description: "Aktualisieren von Lösungspaketen in ein. FFU Bilddatei"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 39d965d5-880d-407f-9e16-ea6a1a8f42d0
ms.openlocfilehash: 18419ce2a38f6efcdaab049c966b02ac7c693869
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-packages-in-an-ffu-image-file"></a>Aktualisieren von Lösungspaketen in ein. FFU Bilddatei


ImageApp.exe können Sie eine neue oder aktualisierte Paket einer vorhandenen hinzufügen. FFU Bilddatei Produktions-, Integrität und Testen von Bildern.

ImageApp bietet die folgenden wichtigen Nachteile:

-   ImageApp sollte nur für das Hinzufügen von Paketen zu Produktion, Test und Health Bildern verwendet werden. Verwenden Sie nicht ImageApp Retail Bilder, ändern, wie es Update Zuverlässigkeit und die Sicherheit des Geräts beeinträchtigen kann. ImageApp kann nicht zum Ändern des Layouts Partition ein vorhandenes Bild verwendet werden. Wenn eine andere Partitionslayout benötigt wird, wird das Bild müssen neu erstellt werden. Weitere Informationen finden Sie unter [Erstellen eines Geräts Abbilds ImgGen.cmd verwenden](building-a-phone-image-using-imggencmd.md).
-   ImageApp kann nicht verwendet werden, um Pakete aus einem Bild zu entfernen.
-   Zur Vorbereitung von einer Geräteplattform für die komprimierte Partitionen mit CompactOS verwenden, benötigen Sie einen PC mit der Windows-10-Version von DISM. Wenn Ihre Techniker PC eine frühere Version von Windows ausgeführt wird, können Sie dies durch Installieren von Windows Assessment and Deployment Kit (ADK) für Windows 10 oder durch Kopieren und die Installation des Treibers DISM abrufen. Dieser Prozess ist identisch mit demjenigen, der zur Installation von DISM auf Windows PE verwendet. Weitere Informationen finden Sie unter [Installieren von Windows-10 mit einer früheren Version von Windows PE: DISM in Windows PE-Abbild hinzufügen](../desktop/copy-dism-to-another-computer.md).

Beim Aktualisieren eines vorhandenen Pakets sollten Sie unbedingt die Versionsnummer erhöhen. Weitere Informationen finden Sie unter [Aktualisieren von Anforderungen](../../service/mobile/update-requirements.md). Beim Hinzufügen eines Pakets, das noch nicht vorhanden im Bild kann eine beliebige Anzahl Version verwendet werden.

Geben Sie die Paketen in eine XML-Eingabedatei ähnlich dem hier dargestellten hinzugefügt werden soll.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<UpdateOSInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
   <Description>Add Debugger On package</Description>
   <PackageFiles>
      <PackageFile>C:\Program Files\Windows Kits\10\Packages\Microsoft.BCD.DebuggerOn.spkg</PackageFile>
   </PackageFiles>
</UpdateOSInput>
```

Angenommen, wenn die `updateInput.xml` Datei befindet sich in der C:\\temporärer Ordner, der mit diesem Befehl werden die angegebenen Pakete den vorhandenen hinzufügen `flash.ffu` Bilddatei an.

``` syntax
ImageApp flash.ffu /UpdateInputXML:C:\temp\updateInput.xml
```

## <a name="command-line-syntax-for-imageappexe"></a>Die Befehlszeilensyntax für ImageApp.exe


``` syntax
ImageApp.exe <imageFile.ffu> </UpdateInputXML:updateInputfile.xml> 
```

In der folgenden Tabelle werden die Befehlszeilenparameter für ImageApp.exe beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ImageFile</em>.ffu</p></td>
<td><p>Der Name der Datei FFU aktualisiert werden.</p></td>
</tr>
<tr class="even">
<td><p>/ UpdateInputXML:<em>UpdateInputfile</em>.xml</p></td>
<td><p>Der Name der XML-Datei, die identifiziert das Paket, das Bild hinzugefügt werden soll. Wenn diese Datei nicht im aktuellen Verzeichnis ist, müssen Sie den Pfad zur Datei einbeziehen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="troubleshooting"></a>Problembehandlung


**"STATUS\_DATEI\_IS\_A\_VERZEICHNIS"**: Diese Fehlermeldung wird angezeigt, wenn ein Bild mit CompactOS von einem PC zu erstellen, die die Windows-10-Version von DISM besitzt. Sie erhalten diese durch Installieren von Windows ADK für Windows 10 oder nur beim Installieren der DISM aus einer anderen PC mit Windows ADK für Windows 10-Treiber installiert. Finden Sie weitere Informationen finden Sie unter [installieren Windows 10 mithilfe einer früheren Version von Windows PE](../desktop/copy-dism-to-another-computer.md).

## <a name="related-topics"></a>Verwandte Themen


[Erstellen ein Bild mit ImgGen.cmd](building-a-phone-image-using-imggencmd.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Update%20packages%20in%20an%20.FFU%20image%20file%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





