---
author: Justinha
Description: Ein Windows-Abbild mithilfe von DISM Service
ms.assetid: 7578765f-15ca-4cdd-9327-cfe42a36add2
MSHAttr: PreferredLib:/library/windows/hardware
title: Ein Windows-Abbild mithilfe von DISM Service
ms.openlocfilehash: 1175dde3fe059f60f301888d46662b75c4fd63d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-a-windows-image-using-dism"></a>Ein Windows-Abbild mithilfe von DISM Service


Das Tool Deployment Image Servicing and Management (DISM) kann Benutzer Treiber und Pakete auflisten, Konfigurationseinstellungen ändern, hinzufügen und Entfernen von Treibern ohne Verwendung einer Antwortdatei und mehr. Sie können DISM online oder offline auf einer WIM oder VHD-Datei auf einem ausgeführten Betriebssystem verwenden.

Eine Offline können Sie ändern oder die Dienst-ein Windows® Bild vollständig offline, ohne es zuerst zu starten. Dies kann Bereitstellungskosten reduziert werden, da Sie Bilder zu einem gewissen Grad anpassen können, bevor das Betriebssystem auf dem Computer bereitgestellt wird. Darüber hinaus Wenn ein gespeicherter master-Abbild stellen Sie sicher, dass Sie die gewünschten ist immer auf dem aktuellen Stand ist, können Sie es verwalten, ohne das Abbild zu starten.

DISM können auch um ein Abbild online zu warten. Wenn Sie das Betriebssystem zum Installieren einer Anwendung oder testen und Überprüfen der Installation starten müssen, können Sie starten, um im Überwachungsmodus und Treiber und Pakete hinzufügen oder Aktivieren der Features und internationalen Einstellungen.

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[Hinzufügen und Entfernen von Treibern zu einem Offline-Windows-Bild](add-and-remove-drivers-to-an-offline-windows-image.md)</p></td>
<td align="left"><p>Hinzufügen oder Entfernen von Treibern aus einem offline-Abbild mithilfe von DISM oder einer Antwortdatei.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Aktivieren Sie oder deaktivieren Sie des Windows-Features mithilfe von DISM](enable-or-disable-windows-features-using-dism.md)</p></td>
<td align="left"><p>Aktivieren oder Deaktivieren von Features in einem Windows-Abbild mithilfe von DISM. Sie können auch ein Feature, das bei Bedarf installieren entfernen und Wiederherstellen ein zuvor entferntes Features.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Hinzufügen oder Entfernen von Paketen mithilfe von DISM Offline](add-or-remove-packages-offline-using-dism.md)</p></td>
<td align="left"><p>Hinzufügen oder Entfernen von Paketen über ein offline-Abbild mithilfe von DISM oder einer Antwortdatei.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md)</p></td>
<td align="left"><p>Hinzufügen oder Entfernen von Sprachpaketen und internationale Einstellungen in einem offline-Abbild mithilfe von DISM konfigurieren.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md)</p></td>
<td align="left"><p>Installieren Sie Line-of-Business (LOB) Windows Store-apps auf einem Windows-Abbild mithilfe von Windows PowerShell® oder die Deployment Image Servicing and Management (DISM) Plattform.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Vorinstallieren von Apps mithilfe von DISM](preinstall-apps-using-dism.md)</p></td>
<td align="left"><p>Vorinstallieren von apps in einem Windows-Abbild.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Anpassen der Startseite](customize-the-start-screen.md)</p></td>
<td align="left"><p>Passen Sie die Startseite zum Einschließen von Windows Store-apps und desktop-apps, die Sie in Ihrem Unternehmen verwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Ändern Sie das Windows-Abbild in eine höhere Edition mithilfe von DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)</p></td>
<td align="left"><p>Abfrage ein Bild, um zu bestimmen, welche Edition von Windows das Bild wird und wie Sie das Bild auf eine höhere Version von Windows zu ändern.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Exportieren Sie oder importieren Sie Zuordnungen von Dienstanwendungen](export-or-import-default-application-associations.md)</p></td>
<td align="left"><p>Ändern der Standardprogramme einer Erweiterung oder Protokoll in einem Windows-Abbild zugeordnet werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Dienst bereitgestellten Windows-Abbilds](service-a-mounted-windows-image.md)</p></td>
<td align="left"><p>Verwenden Sie DISM zum Bereitstellen eines Abbilds und ändern.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Ein Bild angewendeten Windows-Dienst](service-an-applied-windows-image.md)</p></td>
<td align="left"><p>Mithilfe von DISM anwenden der Schwelle und anschließend zu ändern.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[Bestandsaufnahme eines Bilds oder einer Komponente mithilfe von DISM](take-inventory-of-an-image-or-component-using-dism.md)

 

 






