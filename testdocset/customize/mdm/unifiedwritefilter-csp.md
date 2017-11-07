---
title: UnifiedWriteFilter CSP
description: "Konfiguration Dienstanbieters UnifiedWriteFilter (UWF) ermöglicht den IT-Administrator für die Remoteverwaltung der UWF zum Schutz der physischen Medien einschließlich beliebiger beschreibbaren Speicher."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F4716AC6-0AA5-4A67-AECE-E0F200BA95EB
ms.openlocfilehash: ddde3764fdd09d30987ba5eb89b659a65f7c48a7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="unifiedwritefilter-csp"></a>UnifiedWriteFilter CSP


Der Dienstanbieter für UnifiedWriteFilter (UWF) Konfiguration ermöglicht den IT-Administrator für die Remoteverwaltung der UWF zum Schutz der physischen Medien einschließlich beliebiger beschreibbaren Speicher.

> **Hinweis**  UnifiedWriteFilter CSP ist nur in Windows 10 Enterprise und Windows 10 Education unterstützt.

 

Das folgende Diagramm zeigt den UWF Konfigurationsdienstanbieter in der Strukturformat.

![Universalwritefilter csp](images/provisioning-csp-uwf.png)

<a href="" id="currentsession"></a>**CurrentSession**  
Erforderlich. Stellt die aktuelle UWF-Konfiguration in der aktuellen Sitzung (ein-/ausschalten).

<a href="" id="currentsession-filterenabled"></a>**CurrentSession/FilterEnabled**  
Erforderlich. Gibt an, ob UWF für die aktuelle Sitzung aktiviert ist.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-overlayconsumption"></a>**CurrentSession/OverlayConsumption**  
Erforderlich. Die aktuelle Größe in MB, der Überlagerung UWF.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-availableoverlayspace"></a>**CurrentSession/AvailableOverlaySpace**  
Erforderlich. Die verfügbaren Speicherplatz, in Megabyte für die Überlagerung UWF verfügbar.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-criticaloverlaythreshold"></a>**CurrentSession/CriticalOverlayThreshold**  
Erforderlich. Die Größe des kritischen Schwellenwert in Megabyte. UWF sendet einen kritischen Grenzwert Benachrichtigungsereignis aus, wenn die UWF Überlagerung Größe erreicht oder dieser Wert übersteigt.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="currentsession-warningoverlaythreshold"></a>**CurrentSession/WarningOverlayThreshold**  
Erforderlich. Die Warnung Schwellenwert Größe in MB. UWF sendet eine Warnung Schwellenwert für die Benachrichtigungsereignis aus, wenn die UWF Überlagerung Größe erreicht oder dieser Wert übersteigt.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="currentsession-overlaytype"></a>**CurrentSession/OverlayType**  
Erforderlich. Gibt den Typ der Überlagerung in der aktuellen Sitzung an.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-maximumoverlaysize"></a>**CurrentSession/MaximumOverlaySize**  
Erforderlich. Gibt die maximale Cachegröße in Megabyte, der Überlagerung in der aktuellen Sitzung an.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-persisitdomainsecretkey"></a>**CurrentSession/PersisitDomainSecretKey**  
Erforderlich. Gibt an, ob der Domäne geheimen Registrierungsschlüssel in der Registrierung Ausschlussliste aus. Wenn der Registrierungsschlüssel nicht in der Ausschlussliste ist, führen Sie Änderungen nach einem Neustart Sitzungen nicht bestehen.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-persisttscal"></a>**CurrentSession/PersistTSCAL**  
Erforderlich. Gibt an, ob der Registrierungsschlüssel Terminal Server Client Access License (TSCAL) in der UWF Registrierung Ausschlussliste aus. Ist der Registrierungsschlüssel nicht in der Ausschlussliste, führen Sie Änderungen nach einem Neustart Sitzungen nicht bestehen.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-registryexclusions"></a>**CurrentSession/RegistryExclusions**  
Erforderlich. Der Stammknoten, der alle Registrierung Ausschlüsse enthält.

<a href="" id="currentsession-registryexclusions-excludedregistry"></a>**CurrentSession/RegistryExclusions / ***_ExcludedRegistry_**  
Optional Einen Registrierungsschlüssel in der Registrierung Ausschlussliste für UWF in der aktuellen Sitzung.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-servicingenabled"></a>**CurrentSession/ServicingEnabled**  
Erforderlich. Gibt an, wenn die Wartung der aktuellen Sitzung aktiviert ist.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-volume"></a>**CurrentSession-Volume**  
Erforderlich. Den Stammknoten enthält alle Volumes, die in der aktuellen Sitzung durch UWF geschützt.

<a href="" id="currentsession-volume-volume"></a>**CurrentSession-Volume / ***_Volume_**  
Optional Stellt ein bestimmtes Volume in der aktuellen Sitzung.

<a href="" id="currentsession-volume-volume-protected"></a>* *CurrentSession-Volume/*Volume*/ geschützte **  
Erforderlich. Gibt an, ob die Lautstärke derzeit in der aktuellen Sitzung durch UWF geschützt ist.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-volume-volume-bindbydriveletter"></a>* *CurrentSession-Volume/*Volume*/BindByDriveLetter**  
Erforderlich. Gibt den Typ der Bindung, die die Lautstärke in der aktuellen Sitzung verwendet wird.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-volume-volume-driveletter"></a>* *CurrentSession-Volume/*Volume*/DriveLetter**  
Erforderlich. Der Laufwerkbuchstabe des Volumes. Wenn das Volume nicht mit einen Laufwerkbuchstaben vorhanden ist, ist dieser Wert NULL.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-volume-volume-exclusions"></a>* *CurrentSession/Volume/*Volume*/Exclusions**  
Erforderlich. Die Stammknoten, der alle Ausschlüsse für das Volume enthält.

<a href="" id="currentsession-volume-volume-exclusions-exclusionpath"></a>* *CurrentSession/Volume/*Volume*/Ausschlüsse / ***_ExclusionPath_**  
Optional Eine Zeichenfolge, die den vollständigen Pfad der Datei oder des Ordners relativ zu der Lautstärke enthält.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-volume-volume-commitfile"></a>* *CurrentSession-Volume/*Volume*/CommitFile**  
Erforderlich. Diese Methode führt einen Commit Änderungen aus der Überlagerung der physischen Datenträger für eine angegebene Datei auf einem Datenträger geschützt durch Unified schreiben Filter (UWF).

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="currentsession-volume-volume-commitfiledeletion"></a>* *CurrentSession/Volume/*Volume*/CommitFileDeletion**  
Erforderlich. Diese Methode löscht die angegebene Datei und führt ein Commit für den Löschvorgang auf den physischen Datenträger.

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="currentsession-shutdownpending"></a>**CurrentSession/ShutdownPending**  
Erforderlich. Dieser Wert ist True, wenn das System aussteht auf Herunterfahren. Andernfalls ist er False.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="currentsession-commitregistry"></a>**CurrentSession/CommitRegistry**  
Erforderlich. Diese Methode führt ein Commit für Änderungen an den angegebenen Registrierungsschlüssel und den Wert.

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="currentsession-commitregistrydeletion"></a>**CurrentSession/CommitRegistryDeletion**  
Erforderlich. Diese Methode löscht den angegebenen Registrierungsschlüssel oder Registrierungswert und führt ein Commit für das Löschen.

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="nextsession"></a>**NextSession**  
Erforderlich.

Der Stammknoten, der Einstellungen für die nächste UWF Sitzung (nach einem Neustart) enthält.

<a href="" id="nextsession-filterenabled"></a>**NextSession/FilterEnabled**  
Erforderlich. Boolescher Wert, der angibt, ob für die nächste Sitzung UWF aktiviert ist.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-hormenabled"></a>**NextSession/HORMEnabled**  
In Windows 10, Version 1607 hinzugefügt. Erforderlich. Boolean-Wert, der angibt, wenn einmal Ruhezustand / Resume viele (HORM) für die nächste Sitzung aktiviert ist.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-overlaytype"></a>**NextSession/OverlayType**  
Erforderlich. Gibt den Typ der Überlagerung für die nächste Sitzung an.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-maximumoverlaysize"></a>**NextSession/MaximumOverlaySize**  
Erforderlich. Gibt die maximale Cachegröße in Megabyte, der Überlagerung für die nächste Sitzung an.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-persisitdomainsecretkey"></a>**NextSession/PersisitDomainSecretKey**  
Erforderlich. Gibt an, ob der geheime Domäne-Registrierungsschlüssel in der Registrierung Ausschlussliste ist. Wenn der Registrierungsschlüssel nicht in der Ausschlussliste ist, führen Sie Änderungen nach einem Neustart Sitzungen nicht bestehen.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-persisttscal"></a>**NextSession/PersistTSCAL**  
Erforderlich. Gibt an, ob der Registrierungsschlüssel Terminal Server Client Access License (TSCAL) in der UWF Registrierung Ausschlussliste aus. Wenn der Registrierungsschlüssel nicht in der Ausschlussliste ist, führen Sie Änderungen nach einem Neustart Sitzungen nicht bestehen.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-registryexclusions"></a>**NextSession/RegistryExclusions**  
Erforderlich. Den Stammknoten, der alle Registrierung Ausnahmen für die nächste Sitzung enthält.

Unterstützte Vorgänge sind hinzufügen, löschen, und ersetzen.

<a href="" id="nextsession-registryexclusions-excludedregistry"></a>**NextSession/RegistryExclusions / ***_ExcludedRegistry_**  
Optional Einen Registrierungsschlüssel in der Registrierung Ausschlussliste für UWF.

Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

<a href="" id="nextsession-servicingenabled"></a>**NextSession/ServicingEnabled**  
Erforderlich. Gibt an, wann – Wartung zu aktivieren.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-volume"></a>**NextSession-Volume**  
Erforderlich. Der Stammknoten, der alle Volumes geschützt durch UWF für die nächste Sitzung enthält.

<a href="" id="nextsession-volume-volume"></a>**NextSession-Volume / ***_Volume_**  
Optional Stellt ein bestimmtes Volume in der nächsten Sitzung.

Unterstützte Vorgänge sind hinzufügen, löschen, und Ersetzen Sie.

<a href="" id="nextsession-volume-volume-protected"></a>* *NextSession-Volume/*Volume*/ geschützte **  
Erforderlich. Gibt an, ob die Lautstärke aktuell in der nächsten Sitzung durch UWF geschützt ist.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-volume-volume-bindbydriveletter"></a>* *NextSession-Volume/*Volume*/BindByDriveLetter**  
Erforderlich. Gibt den Typ der Bindung, die das Volume in der nächsten Sitzung verwendet wird.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="nextsession-volume-volume-driveletter"></a>* *NextSession-Volume/*Volume*/DriveLetter**  
Der Laufwerkbuchstabe des Volumes. Wenn das Volume nicht mit einen Laufwerkbuchstaben vorhanden ist, ist dieser Wert NULL.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="nextsession-volume-volume-exclusions"></a>* *NextSession-Volume/*Volume*/Exclusions**  
Erforderlich. Den Stammknoten, der enthält alle Ausschlüsse für dieses Volume in der nächsten Sitzung.

<a href="" id="nextsession-volume-volume-exclusionsexclusionpath"></a>* *NextSession-Volume/*Volume*/Ausschlüsse / ***_ExclusionPath_**  
Optional Eine Zeichenfolge, die den vollständigen Pfad der Datei oder des Ordners relativ zu der Lautstärke enthält.

Unterstützte Vorgänge sind Get hinzufügen, löschen, und ersetzen.

<a href="" id="resetsettings"></a>**ResetSettings**  
Erforderlich. UWF Einstellungen wiederhergestellt in den ursprünglichen Zustand, der bei der Installation erfasst wurde.

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="shutdownsystem"></a>**ShutdownSystem**  
Erforderlich. Sicher fährt ein System durch UWF, geschützt, auch wenn die Überlagerung voll ist.

Unterstützte Vorgänge sind Get und ausführen.

<a href="" id="restartsystem"></a>**RestartSystem**  
Erforderlich. Ein System durch UWF, geschützt wird sicher neu gestartet, auch wenn die Überlagerung voll ist.

Unterstützte Vorgänge sind Get und ausführen.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 





