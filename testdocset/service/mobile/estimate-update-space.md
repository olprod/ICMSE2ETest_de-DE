---
author: kpacquer
Description: "Schätzung Update Speicherplatz"
ms.assetid: dfd2eed9-3202-4a08-87d1-d1f4f132b7c5
MSHAttr: PreferredLib:/library/windows/hardware
title: "Schätzung Update Speicherplatz"
ms.openlocfilehash: f272e3d69b8a3adb9bbd15ec4a359bfcb59db302
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="estimate-update-space"></a>Schätzung Update Speicherplatz


Die Menge des Arbeitsspeichers, die benötigt werden, auf dem Gerät zum Herunterladen und installieren Sie ein Update kann erheblich variieren. Der Prinzip Aspekte beim Schätzen der Anforderungen sind der Update- und Verarbeitung Arbeitsbereichs zum Herunterladen, Vorbereiten und installieren es erforderlich sind.

**Wichtige**  
Aufgrund von Faktoren wie Komprimierung, die vorgesehenen Pakete und den spezifischen binären Inhalt der Updates ist der Prozess Schätzung ungenauen. OEMs müssen einzeln testen, ein Update aus, um die genaue Größe erforderlich zu bestimmen.

 

## <a name="span-idfactorsthataffectupdatespacerequirementsspanspan-idfactorsthataffectupdatespacerequirementsspanspan-idfactorsthataffectupdatespacerequirementsspanfactors-that-affect-update-space-requirements"></a><span id="Factors_that_affect_update_space_requirements"></span><span id="factors_that_affect_update_space_requirements"></span><span id="FACTORS_THAT_AFFECT_UPDATE_SPACE_REQUIREMENTS"></span>Faktoren, die Einfluss auf Aktualisieren Erforderlicher Festplattenspeicher


Befinden sich in der Aktualisierungsprozess, von denen jedes eine eigene aus Platzgründen hat drei Phasen: herunterladen, Verarbeitung und Fertigstellung.

### <a name="span-idcompressionfordownloadingspanspan-idcompressionfordownloadingspanspan-idcompressionfordownloadingspancompression-for-downloading"></a><span id="Compression_for_downloading"></span><span id="compression_for_downloading"></span><span id="COMPRESSION_FOR_DOWNLOADING"></span>Komprimierung für das Herunterladen von

Updates sind für die Übermittlung an das Gerät komprimiert. Im Rahmen des Prozesses staging Updates werden die Updates dekomprimiert. Binäre ausführbare Dateien, Textdateien und Zuordnungsdaten können Variable Grad komprimiert werden. Aus diesem Grund kann der Umfang der Komprimierung variieren.

### <a name="span-idupdateprocessingspanspan-idupdateprocessingspanspan-idupdateprocessingspanupdate-processing"></a><span id="Update_processing"></span><span id="update_processing"></span><span id="UPDATE_PROCESSING"></span>Verarbeitung

Wenn Updates für die Installation bereitgestellt werden, sind sie bei der Validierung dekomprimiert. Zusätzlicher Speicherplatz ist erforderlich für das Staging und Überprüfung. In der letzten Phase des Updates Wenn das Gerät das Update OS startet, werden die Updates angewendet und temporäre Arbeitsbereich wird an das Betriebssystem zurückgegeben, wenn die Aktualisierung abgeschlossen ist.

Alle Updates erfordern eine bestimmte Menge Speicherplatz für die Verarbeitung. Arbeitsbereichs befindet sich auf der Hauptseite OS Partition. Datenspeicher für die SD-Karte und Benutzer werden während des Aktualisierungsvorgangs nicht verwendet. Die Größe des Arbeitsbereichs ist etwa 50 MB.

### <a name="span-idupdatedstatespanspan-idupdatedstatespanspan-idupdatedstatespanupdated-state"></a><span id="Updated_state"></span><span id="updated_state"></span><span id="UPDATED_STATE"></span>Aktualisierte Zustand

Je nach den Inhalt des Updates kann die endgültige Größe, die sie auf das Bild verbraucht variieren. Wenn das Update vorhandene Pakete überschreibt, möglicherweise einen Abfall oder einen Anstieg Menge an freiem Speicherplatz verfügbar auf dem Gerät. Beispielsweise würde das Update neue Dateien des Betriebssystems hinzufügt, die endgültige Größe die Größe der neuen Dateien widerspiegeln.

## <a name="span-idestimatingsizerequirementsspanspan-idestimatingsizerequirementsspanspan-idestimatingsizerequirementsspanestimating-size-requirements"></a><span id="Estimating_size_requirements"></span><span id="estimating_size_requirements"></span><span id="ESTIMATING_SIZE_REQUIREMENTS"></span>Schätzen der Größe Anforderungen


Aktualisierungsdateien enthalten nur die Unterschiede an, die zum Aktualisieren eines Pakets erforderlich sind. Nondifferential Updates sind inklusive und eigenständige. Wenn eine differenzielle Aktualisierung zu einem Paket anwenden möchten, wird ein intermediate-Paket erstellt, dass die Unterschiede klicken Sie dann auf angewendet werden. Dies bedeutet, dass ein Recht kleines differenzielle Update kann beträchtlichen zusätzlichen Speicherplatz in Phase und anwenden, wenn das gezielte Paket groß ist. Die meisten Microsoft OS Updates werden differenzielle und inkrementell auf bestimmte OS Versionen angegeben vorgesehen sind.

### <a name="span-iddifferentialupdatesspanspan-iddifferentialupdatesspanspan-iddifferentialupdatesspandifferential-updates"></a><span id="Differential_updates"></span><span id="differential_updates"></span><span id="DIFFERENTIAL_UPDATES"></span>Aktualisierungsdateien

Schätzen den erforderliche Speicherplatz für eine differenzielle Aktualisierung, die Größe des Pakets, dass das Update abzielt ermittelt werden müssen.

*(Die gezielte Pakete gemessen in MB \* 1.5) + Arbeitsbereich = geschätzt Update Speicherplatz in MB erforderlich.*

Wenn das Zielpaket 4 MB groß war, würde die Berechnung beispielsweise folgendermaßen aussehen:

*(4 \* 1.5) + 50 MB = 62 MB.*

Beachten Sie, dass die Größe des Pakets, das das differenzielle Update enthält in der Schätzung nicht verwendet wird.

### <a name="span-idnondifferentialupdatesspanspan-idnondifferentialupdatesspanspan-idnondifferentialupdatesspannondifferential-updates"></a><span id="Nondifferential_updates"></span><span id="nondifferential_updates"></span><span id="NONDIFFERENTIAL_UPDATES"></span>Nondifferential updates

Verwenden Sie die Schätzung den erforderliche Speicherplatz für eine typische nondifferential OEM-Update dieser Formel:

*(Das Update gemessen in MB \* 1.5) + Arbeitsbereich in MB = geschätzter Update Speicherplatz in MB.*

### <a name="span-idsvpartitionupdatesspanspan-idsvpartitionupdatesspanspan-idsvpartitionupdatesspansv-partition-updates"></a><span id="SV_partition_updates"></span><span id="sv_partition_updates"></span><span id="SV_PARTITION_UPDATES"></span>PA Partition updates

Informationen zum Schätzen der Größe der PA Partition Updates erhalten Sie der Halbleiterhersteller.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Update](index.md)

 

 






