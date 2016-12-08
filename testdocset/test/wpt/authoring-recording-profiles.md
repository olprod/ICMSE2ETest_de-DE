---
title: Authoring Aufzeichnung Profile
description: Authoring Aufzeichnung Profile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1eea16bd-f96d-4d17-a857-f93c0d0717b7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 048db3b52b5dca730dff0d06c74412a77b503a53
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="authoring-recording-profiles"></a>Authoring Aufzeichnung Profile


Sie können Windows Performance Aufzeichnung (WPR) Aufzeichnen von Benutzerprofilen in eine XML-Datei, die die Erweiterung .wprp hat erstellen. Aufzeichnung Profile enthalten alle erforderlichen Informationen zum Aktivieren der Leistung für ein bestimmtes Szenario aufzeichnen. Diese Daten enthält Informationen über Sitzungen, Anbieter und Schlüsselwörter Event Tracing for Windows (ETW). Jede .wprp-Datei enthält mindestens ein Profildefinition, die einen bestimmten Satz von ETW-Sitzungen und Anbieter konsolidiert. Die Profildefinition eines umfasst auch die Sitzung, und Anbieter Attribute, die Start- und Steuerelement Leistung Aufzeichnung.

WPR Profile unterstützen die folgenden ETW Features:

-   Sequenzielle Datei und kreisförmige Arbeitsspeicher Protokollierung Modi.

-   Vom Benutzer angegebener Anzahl der Puffer und Puffergrößen für jede Sitzung.

-   ETW-System Protokollierung Sitzungen zusammen mit der NT-Kernel-Protokollierung. Fusion bietet die Möglichkeit, Schlüsselwörter, Stapel und Speicher Pooltags angeben.

-   Ereignis-Sitzungen, die einen Wert ProviderName oder GUID, Schlüsselwörter, Stack, Detailstufe und nicht ausgelagerte Arbeitsspeicher angeben.

-   Erfassen Zustand Authentifizierungsanbieter an, der Zustand während erfassen starten oder Vorgänge nur zu speichern.

Die Datei .wprp muss bestimmte Definitionen enthalten, die in einer bestimmten Reihenfolge aufgeführt sind. In den folgenden Themen wird beschrieben, wie die Definitionen in dieser Reihenfolge erstellen.

## <a name="authoring-wprp-files-in-visual-studio"></a>Erstellen von .wprp-Dateien in Visual Studio


Visual Studio können so erstellen Sie eine Aufzeichnung Profil mithilfe der Schemadatei WPR WPRControlProfiles.xsd, das im Installationsordner WPT verfügbar ist:

1.  Öffnen Sie die .wprp Datei in Visual Studio.

2.  Klicken Sie im Hauptmenü wählen Sie **XML**, und wählen Sie dann **Schemas...**

3.  Der **XML-Schemas** im Dialogfeld, das angezeigt wird, wählen Sie **hinzufügen...**

4.  Wählen Sie das Schema WPRControlProfiles.xsd. Standardmäßig ist diese Datei im Verzeichnis WPT installieren:

    -   `C:\Program Files (x86)\Windows Kits\8.1\Windows Performance Toolkit`

Nachdem Sie das Schema ausgewählt haben, können kontextbezogene IntelliSense Sie um Ihre .wprp-Datei zu erstellen.

## <a name="in-this-section"></a>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[1. Collector-Definitionen](1-collector-definitions.md)</p></td>
<td><p>Wie Kollektoren Profil zu definieren.</p></td>
</tr>
<tr class="even">
<td><p>[2. System- und Ereignis Anbieter-Definitionen](2-system-and-event-provider-definitions.md)</p></td>
<td><p>Wie Sie Anbieter für ein Profil zu definieren.</p></td>
</tr>
<tr class="odd">
<td><p>[3. Definitionen für Profil](3-profile-definitions.md)</p></td>
<td><p>Wie Sie ein Profil zu definieren.</p></td>
</tr>
<tr class="even">
<td><p>[Strict Anbieter](strict-providers.md)</p></td>
<td><p>Wie Sie das Attribut <strong>Strict</strong> verwenden.</p></td>
</tr>
<tr class="odd">
<td><p>[Vererbung (engl.)](inheritance.md)</p></td>
<td><p>Beschreibt die Vererbung beim Verfassen von Aufzeichnung Profile.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Aufzeichnung Profile](recording-profiles.md)

[Erstellen eines benutzerdefinierten Aufzeichnung-Profils](author-a-custom-recording-profile.md)

[Hinzufügen oder Entfernen eines benutzerdefinierten Aufzeichnung-Profils](add-or-remove-a-custom-recording-profile.md)

 

 







