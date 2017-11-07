---
title: Update CSP
description: Update CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F1627B57-0749-47F6-A066-677FDD3D7359
ms.openlocfilehash: 7f8c05848846e3f2f9f2b69b86593b5cb48ba66a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-csp"></a>Update CSP


Der Update Konfigurationsdienstanbieter kann IT-Administratoren verwalten und Steuern der Einführung der neuen Updates.

Das folgende Diagramm zeigt den Update-Konfiguration-Dienstanbieter in der Strukturformat.

![Csp Diagramm aktualisieren](images/provisioning-csp-update.png)

<a href="" id="update"></a>**Update**  
Den Stammknoten.

Unterstützte Vorgang ist Get.

<a href="" id="approvedupdates"></a>**ApprovedUpdates**  
Knoten für die Aktualisierung Genehmigungen und EULA Annahme im Namen der Endbenutzer.

> **Hinweis** Wenn die Richtlinie RequireUpdateApproval festgelegt ist, verwendet die MDM ApprovedUpdates List, übergeben die genehmigte GUIDs an. Diese GUIDs sollte eine Teilmenge der Liste InstallableUpdates sein.

Die MDM muss zuerst den Endbenutzer-LIZENZVERTRAG zu präsentieren IT und lassen sie ihn akzeptieren, bevor das Update genehmigt wurde. Wenn dies nicht der Fall ist eine Verletzung der rechtlichen oder vertragliche Verpflichtungen. Diese Verträge aus der Update-Metadaten abgerufen werden können und über eigene EULA-ID. Es ist möglich, mehrere Updates für den gleichen EULA gemeinsam nutzen. Es ist nur erforderlich, um den Endbenutzer-LIZENZVERTRAG einmal pro EULA-ID nicht eine pro Update zu genehmigen.

Das Update Genehmigung Liste ermöglicht der IT zu genehmigen einzelne Updates Klassifikationen aktualisieren. Automatische Genehmigung von Update Klassifikationen ermöglicht es IT-Definition (d. h., Updates, die Definitionen von Viren und Spyware auf Geräten) und Sicherheitsupdates (d. h., produktspezifische Updates für sicherheitsbezogene Sicherheitsrisiko) automatisch genehmigen. Die Genehmigung Updateliste unterstützt nicht die Deinstallation des Updates durch Aufheben der Genehmigung der bereits installierten Updates. Updates werden basierend auf UpdateID genehmigt, und ein UpdateID muss nur einmal genehmigt werden. Ein Update UpdateID und RevisionNumber sind Teil des Typs UpdateIdentity. Ein UpdateID kann mehrere UpdateIdentity GUIDs aufgrund von Änderungen an der Einstellung RevisionNumber zugeordnet werden. MDM Dienste müssen die UpdateIdentity von einer UpdateID basierend auf den neuesten RevisionNumber zum Abrufen des neuesten Metadaten für ein Update synchronisieren. Genehmigung von vorgangsaktualisierungen basiert jedoch auf UpdateID.

> **Hinweis**  Der Client müssen möglicherweise für den Build Windows 10 neu starten, nachdem Weitere Updates hinzugefügt wurden.

 

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="approvedupdates-approved-update-guid"></a>**ApprovedUpdates / ***_Update Guid genehmigt_**  
Gibt an, das Update GUID.

Wenn Sie eine Klasse von Updates automatisch genehmigen können Sie die [Update-Klassifikationen](http://go.microsoft.com/fwlink/p/?LinkId=526723) GUIDs angeben. Es wird dringend empfohlen die DefinitionsUpdates Klassifizierung (E0789628-CE08-4437-BE74-2495B842F43B), an die für Antischadsoftware-Signaturen verwendet werden. Es freigegeben wurden in regelmäßigen Abständen (mehrere Male einen Tag). Einige Unternehmen möchten möglicherweise auch automatisch genehmigen von Sicherheits-Updates, damit sie schnell bereitgestellt angezeigt.

Unterstützte Vorgänge sind Get und hinzufügen.

Syncml Beispiel:

```
<LocURI>./Vendor/MSFT/Update/ApprovedUpdates/%7ba317dafe-baf4-453f-b232-a7075efae36e%7d</LocURI>
```

<a href="" id="approvedupdates-approved-update-guid-approvedtime"></a>* *ApprovedUpdates /*genehmigt Update Guid*/ApprovedTime**  
Gibt die Zeitspanne, die das Update genehmigt wird.

Unterstützte Vorgänge sind Get und hinzufügen.

<a href="" id="failedupdates"></a>**FailedUpdates**  
Gibt die genehmigten Updates, die nicht auf einem Gerät installieren.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid"></a>**FailedUpdates / ***_Guid Update Failed_**  
Aktualisieren Sie Feld ID der UpdateIdentity-GUID, die ein Update darstellen, die nicht herunterladen, oder installieren Sie.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid-hresult"></a>* *FailedUpdates /*Fehler beim Update Guid*/HResult**  
Der Fehlercode des Update Fehler.

Unterstützte Vorgang ist Get.

<a href="" id="failedupdates-failed-update-guid-status"></a>* *FailedUpdates /*Fehler beim Update Guid*/Status**  
Gibt den Status Updatefehlern (beispielsweise herunterladen, installieren).

Unterstützte Vorgang ist Get.

<a href="" id="installedupdates"></a>**InstalledUpdates**  
Die Updates, die auf dem Gerät installiert werden.

Unterstützte Vorgang ist Get.

<a href="" id="installedupdates-installed-update-guid"></a>**InstalledUpdates / ***_Guid Update installiert_**  
UpdateIDs, die die Updates installiert sind, auf einem Gerät darstellen.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates"></a>**InstallableUpdates**  
Die Updates, die anwendbar und noch nicht auf dem Gerät installiert werden. Dazu gehören Updates, die noch nicht genehmigt werden.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid"></a>**InstallableUpdates / ***_installierbares Update-Guid_**  
Update-Bezeichner, die die Updates zutreffend und nicht auf einem Gerät installierten darstellen.

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid-type"></a>* *InstallableUpdates /*installierbares Update Guid*/Type**  
Der Wert der UpdateClassification des Updates. Gültige Werte sind:

-   0 – keine
-   1 – Sicherheit
-   2 = kritisch

Unterstützte Vorgang ist Get.

<a href="" id="installableupdates-installable-update-guid-revisionnumber"></a>* *InstallableUpdates /*installierbares Update Guid*/RevisionNumber**  
Die Revisionsnummer für das Update, das in Server-zu-Server-Synchronisierung zum Abrufen der Metadaten für das Update übergeben werden muss.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates"></a>**PendingRebootUpdates**  
Die Updates, die für die Durchführung die Update-Sitzung ein Neustart erforderlich.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates-pending-reboot-update-guid"></a>**PendingRebootUpdates / ***_Ausstehender Neustart Update Guid_**  
Bezeichner für den Neustartstatus ausstehender zu aktualisieren.

Unterstützte Vorgang ist Get.

<a href="" id="pendingrebootupdates-pending-reboot-update-guid-installedtime"></a>* *PendingRebootUpdates /*Ausstehender Neustart Update Guid*/InstalledTime**  
Die Zeit, die das Update installiert ist.

Unterstützte Vorgang ist Get.

<a href="" id="lastsuccessfulscantime"></a>**LastSuccessfulScanTime**  
Die letzte erfolgreiche Scan-Zeit.

Unterstützte Vorgang ist Get.

<a href="" id="deferupgrade"></a>**DeferUpgrade**  
Upgrades verzögert, bis die nächste Periode.

Unterstützte Vorgang ist Get.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






