---
author: Justinha
Description: "Übersicht über die Sysprep (Vorbereitung System)"
ms.assetid: f16f9f4e-c897-4a08-8c0f-e9d64043738c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übersicht über die Sysprep (Vorbereitung System)"
ms.openlocfilehash: 661dd1af3778f98c7348c37707223e32e8bff5f5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-system-preparation-overview"></a>Übersicht über die Sysprep (Vorbereitung System)

**Sysprep** (System Preparation) wird eine Windows-Installation (Windows-Client und Windows Server) für Imaging ermöglicht es Ihnen, eine benutzerdefinierte Installation erfassen vorbereitet. **Sysprep** entfernt PC-spezifische Informationen aus einer Windows-Installation "verallgemeinern" die Installation, sodass es auf unterschiedliche PCs installiert werden kann. Mit **Sysprep** können Sie den PC starten Überwachungsmodus, wobei können Sie zusätzliche geändert oder aktualisiert das Abbild stellen konfigurieren. Oder Sie können Windows zum Starten der Out-of-Box-Experience (OOBE) konfigurieren.

Sysprep ist Teil des Windows-Abbilds und im Überwachungsmodus verwendet wird.

## <a name="span-idbkmkoverspanspan-idbkmkoverspanfeature-description"></a><span id="BKMK_OVER"></span><span id="bkmk_over"></span>Featurebeschreibung


Sysprep bietet folgende Features:

-   Entfernt PC-spezifische Informationen aus dem Windows-Abbild, einschließlich der PC-Sicherheits-ID (SID). Dadurch können Sie das Abbild aufzuzeichnen und auf anderen PCs angewendet wird. Dies wird als Verallgemeinern des PCs-Option bezeichnet.

-   Deinstalliert PC-spezifische Treiber vom Windows-Abbild.

-   Bereitet den PC-Option für die Übermittlung an einen Kunden durch Festlegen des PCs, OOBE zu starten.

-   Ermöglicht Ihnen das Hinzufügen von Antwortdatei (unbeaufsichtigten) Einstellungen einer vorhandenen Installation.

## <a name="span-idbkmkappspanspan-idbkmkappspanpractical-applications"></a><span id="BKMK_APP"></span><span id="bkmk_app"></span>In der Praxis


Sysprep können Sie die Unternehmensziele Art zu lösen:

-   Unterstützung bei der Verwaltung von mehreren PCs durch Erstellen eines generischen Bilds, das über mehrere Hardwareentwürfe verwendet werden kann.

-   Bereitstellen von PCs durch das Erfassen und Bereitstellen von Bildern mit eindeutigen Sicherheits-IDs.

-   Optimieren der einzelnen PCs Setup Hinzufügen von apps, Sprachen oder Treiber im Überwachungsmodus aktiviert. Weitere Informationen finden Sie unter [Übersicht über Audit-Modus](audit-mode-overview.md).

-   Bereitstellen zuverlässiger PCs vor dem Senden von Kunden im Überwachungsmodus testen.

## <a name="span-idbkmknewspanspan-idbkmknewspannew-and-changed-functionality"></a><span id="BKMK_NEW"></span><span id="bkmk_new"></span>Neue und geänderte Funktionalität

Beginnend mit Windows 10, Version 1607, kann Sysprep verwendet werden, um ein Bild vorzubereiten, die aktualisiert wurde. Beispiel:

- Sie können mit einem Computer starten, die Windows-10, Version 1511 oder Windows 10, Version 1507 ausgeführt wird.
- Aktualisieren Sie den Computer zum Ausführen von Windows 10, 1607 Version.
- Ausführen Sysprep auf dem aktualisierten Bild verallgemeinern, erfassen Sie erneut das aktualisierte Abbild und Bereitstellen des Abbilds auf neue Geräte.

Dabei kann Unternehmen auf dem neuesten Stand Windows 10 Bereitstellungsabbilder effizient und fortlaufend Rollout. 

Beginnen mit Windows 8.1, ist die Benutzeroberfläche Sysprep veraltet. Die Sysprep UI wird weiterhin in dieser Version unterstützt werden, aber es in einer zukünftigen Version entfernt werden kann. Es wird empfohlen, dass Sie Ihre Bereitstellungsworkflow zum Verwenden von Sysprep über die Befehlszeile aktualisiert werden. Weitere Informationen finden Sie unter [Sysprep Command-Line Options](sysprep-command-line-options.md).

## <a name="span-iddependenciesspanspan-iddependenciesspanspan-iddependenciesspandependencies"></a><span id="Dependencies"></span><span id="dependencies"></span><span id="DEPENDENCIES"></span>Abhängigkeiten


-   Sie müssen Windows Setup ausführen, bevor Sie Sysprep verwenden.

-   Sie benötigen ein Tool zum Erfassen eines Abbilds der Installation, wie [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md) oder andere Datenträgerabbildern Software.

**Hinweis**  
Wenn Sie Windows-Abbilder zwischen PCs kopieren, möglicherweise die Referenz und Ziel-PCs nicht kompatible Hardwareabstraktionsschichten (HALs) verfügen. Die Option detecthal in Boot Configuration Data (BCD) ermöglicht ein System, das zum Installieren der richtigen HAL Sysprep bereits ausgeführt wurde.

 

## <a name="span-idbkmk4spanspan-idbkmk4spanlimitations"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Einschränkungen


Sysprep weist die folgenden Nachteile:

-   Die Sicherheits-ID (SID) wird beim Ausführen von Sysprep nur auf dem Betriebssystem Datenträger ersetzt. Wenn ein einzigen PC mehrere Betriebssysteme verfügt, müssen Sie Sysprep auf jedes Bild einzeln ausführen.

-   In einigen Fällen angepasst Applications, installieren, bevor Sie das Windows-Abbild erfassen erfordern möglicherweise einen konsistente Laufwerkbuchstaben. Einige Anwendungen speichern Pfade, die das System Laufwerkbuchstaben einschließen. Deinstallation, warten und Reparieren Szenarien möglicherweise nicht einwandfrei funktionsfähig, wenn das System Laufwerkbuchstaben nicht der Buchstabe des Laufwerks übereinstimmt, der die Anwendung angibt.

-   Plug & Play-Geräte auf den Verweis und Ziel PCs müssen nicht vom selben Hersteller sein. Zu diesen Geräten gehören Modems, Sound-, Netzwerkadapter und Grafikkarten. Die Installation muss jedoch die Treiber für diese Geräte einschließen.

-   Nicht alle Serverrollen unterstützen Sysprep. Wenn Sie eine Windows Server-Installation, die bestimmte Serverrollen konfiguriert wurde verallgemeinern, können diese Serverrollen nicht weiterhin nach den Prozess Imaging und Bereitstellung. Weitere Informationen finden Sie unter [Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md).

-   Wenn Sie auf eine Partition mit dem NTFS-Dateisystem Sysprep, die verschlüsselte Dateien oder Ordner enthält ausführen, werden die Daten in diesen Ordnern vollständig kann nicht gelesen werden und können nicht wiederhergestellt.

-   Sysprep-Tool führt nur dann, wenn der PC ein Mitglied einer Arbeitsgruppe, nicht zu einer Domäne ist. Wenn der PC-Option Mitglied einer Domäne ist, entfernt Sysprep den PC aus der Domäne an.

-   Wenn ein PC einer Domäne Mitglied ist und die Gruppenrichtlinie dieser Domäne eine starke Konto Kennwortrichtlinie auf den PC weist, werden alle Benutzerkonten sichere Kennwörter erforderlich. Ausführen von Sysprep oder OOBE wird die Richtlinie für sichere Kennwörter nicht entfernt.

    **Warnung**  
    Wenn Sie kein sicheres Kennwort zu einem Benutzerkonto zuweisen vor dem Ausführen von Sysprep oder OOBE, können Sie nicht zur Anmeldung bei dem Computer sein. Es wird empfohlen, dass Sie immer sichere Kennwörter für Ihre Benutzerkonten verwenden.

     

## <a name="span-idbkmk3spanspan-idbkmk3spanunsupported-scenarios"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>Nicht unterstützte Szenarien


Die folgenden Szenarien werden nicht unterstützt:

-   Verschieben oder Kopieren eines Windows-Abbilds an einem anderen Computer ohne Verallgemeinern des PCs-Option wird nicht unterstützt.

-   Mit einer anderen Version des Tools Sysprep so konfigurieren Sie ein Bild wird nicht unterstützt. Sie müssen nur die Version des Sysprep-Tools verwenden, die mit dem Windows-Abbild installiert ist, die Sie konfigurieren möchten. Sysprep wird mit jeder Version von Windows installiert. Sie müssen immer Sysprep aus der %windir%\\system32\\Sysprep-Verzeichnis.

-   Bei Verwendung eine Windows-Version vor Windows 10, Version 1607, wird mithilfe des Tools Sysprep Upgrade Installationstyp, oder so konfigurieren Sie eine vorhandene Installation von Windows neu, die bereits bereitgestellt wurde nicht unterstützt. In diesem Fall muss Sysprep ausschließlich zum Konfigurieren von neuer Installationen von Windows verwendet werden. Sie können Sysprep ausführen eine unbegrenzte Anzahl von Klicks zum Erstellen und konfigurieren die Installation von Windows.

-   Automatisieren von Sysprep mithilfe von Microsoft-Windows-Deployment\\[RunSynchronous](http://go.microsoft.com/fwlink/?LinkId=286336) Befehl wird nicht unterstützt. Sie können jedoch die Microsoft-Windows-Deployment\\[verallgemeinern](http://go.microsoft.com/fwlink/?LinkId=286337) Einstellung zur Vorbereitung der Imaging nach der Installation des PCs-Option.

-   VM Ausführungsmodus außerhalb eines virtuellen Computers (VM) wird nicht unterstützt. Sie können keine VM-Modus verwenden, um eine virtuelle Festplatte für die Bereitstellung auf jedem PC vorzubereiten.

-   Sysprep kann nicht im Kontext des ein Systemkonto ausgeführt werden. Ausführen von Sysprep im Kontext des Systemkonto mithilfe des Taskplaners oder PSExec, wird beispielsweise nicht unterstützt.

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>Siehe auch


Die folgende Tabelle enthält Links zu Ressourcen, die im Zusammenhang mit diesem Szenario.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Inhaltstyp</th>
<th align="left">Verweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Produktbewertung</strong></p></td>
<td align="left"><p>[Übersicht über den Sysprep Upgradeprozess](sysprep-process-overview.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md) | [Anpassen Default Benutzerprofil durch Verwendung CopyProfile](customize-the-default-user-profile-by-using-copyprofile.md) | [Antwortdateien mit Sysprep verwenden](use-answer-files-with-sysprep.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Tools und Einstellungen</strong></p></td>
<td align="left"><p>[Befehlszeilenoptionen für Sysprep](sysprep-command-line-options.md) | [Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Verwandte Technologien</strong></p></td>
<td align="left"><p>[Windows-Setup](http://microsoft.com) | [Audit Modus Übersicht](audit-mode-overview.md) | [Boot Windows-Modus oder OOBE überwachen](boot-windows-to-audit-mode-or-oobe.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






