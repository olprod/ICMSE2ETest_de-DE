---
title: Definieren Sie das Bild mit OEMInput und feature-Manifestdateien
description: "Informationen Sie zum Erstellen einer OEMInput und feature Manifestdateien, damit der Inhalt Ihrer mobilen Abbilds vollständig zu definieren."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A3E05C3B-450D-4AFD-8368-241EAB7F8036
ms.openlocfilehash: b62da13fb20718e47e5255110ec9b9fc359327dd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="define-the-image-using-oeminput-and-feature-manifest-files"></a>Definieren Sie das Bild mit OEMInput und feature-Manifestdateien


Informationen Sie zum Erstellen einer OEMInput und feature Manifestdateien, damit der Inhalt Ihrer mobilen Abbilds vollständig zu definieren.

## <a name="in-this-section"></a>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="oeminput-file-contents.md">Inhalt der Datei OEMInput</a></p></td>
<td><p>Eine OEMInput.xml-Datei enthält die erforderlichen und optionalen Elemente zum Definieren einer mobilen Bild verwendet. Das Betriebssystem verwendet diese Datei, um festzustellen, Anwendungen Prozessor, build Typ, Benutzeroberfläche Sprachen, Region Standardformat, Auflösung und andere Eigenschaften zum Einschließen in das Bild, das generiert wird.</p>
<p>Dieses Thema enthält eine vollständige Auflistung der XML-Schema für die Datei.</p></td>
</tr>
<tr class="even">
<td><p><a href="optional-features-for-building-images.md">Optionale Features zum Erstellen von mobilen Bilder</a></p></td>
<td><p>Sie können optionale Features Bilder hinzufügen, indem sie unter dem <strong>Features</strong> -Element in der OEMInput-XML-Datei eingeschlossen werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="feature-manifest-file-contents.md">Feature-Manifestdatei Inhalt</a></p></td>
<td><p><em>Feature-Manifestdatei (FM) Dateien</em> werden verwendet, um bestimmte Arten von Builds Bild zu definieren, die unterschiedliche optionale Pakete enthalten. In diesem Thema werden die erforderlichen und optionalen Elemente in einer FM-Datei.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-feature-and-include-it-in-an-image.md">Erstellen Sie ein Feature und fügen Sie es in einem Bild</a></p></td>
<td><p>In diesem Thema zeigt, wie ein Feature erstellen und Hinzufügen eines Bilds.</p></td>
</tr>
<tr class="odd">
<td><p><a href="adding-a-driver-to-a-test-image.md">Hinzufügen eines Treibers dem Test-Bild</a></p></td>
<td><p>In diesem Thema zeigt, wie ein Feature erstellen und Hinzufügen zu einem Testbild.</p></td>
</tr>
<tr class="even">
<td><p><a href="feature-groupings-and-constraints.md">Gruppierung von Features und Einschränkungen</a></p></td>
<td><p>Gruppen Feature und Feature Einschränkungen können zusätzliche Logik, die Buildsystem zur Unterstützung der intelligenten Verarbeitung des OEMInput XML hinzugefügt werden soll.</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-device-platform-information.md">Set-Plattform Geräteinformationen</a></p></td>
<td><p>Informationen Sie zu den erforderlichen Komponenten für die Erstellung von einem Bild, das an ein mobiles Gerät, einschließlich weiteres Gerät Plattforminformationen wie Partnernamen, Versionsnummern und Gerätenamen, bevor das Bild für den Einzelhandel Geräte definitiv zugeordnet werden kann.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und mobilen blinkende](building-and-flashing-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Define%20the%20image%20using%20OEMInput%20and%20feature%20manifest%20files%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





