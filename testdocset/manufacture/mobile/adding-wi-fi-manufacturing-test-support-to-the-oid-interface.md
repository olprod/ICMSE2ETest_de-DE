---
author: kpacquer
Description: "Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle"
ms.assetid: f041b6a9-8c05-487d-9dd1-e538865a9104
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle"
ms.openlocfilehash: 134a491463d6d14c0d39da9c56343c15f4f90d0b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="adding-wi-fi-manufacturing-test-support-to-the-oid-interface"></a>Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle


Um sicherzustellen, dass alle Gerätekomponenten ordnungsgemäß funktioniert, integriert sind, ordnungsgemäß, kalibriert und behördliche Anforderungen entsprechen, wird eine Anzahl von standard-Ad-hoc-Tests durch, um sicherzustellen, dass keine Probleme gefunden und korrigiert, bevor das Gerät an den Einzelhandel wechselt OEMs ausführen. Diese Tests sind auch gelegentlich unter Einzelhandel zu prüfen, ob erforderlichen Komponente Vorgang ausführen. Die Implementierung dieser Test Schnittstellen und Mechanismen wird in der Hardware (unabhängigen Hardwareanbietern) ausgeführt.

Dieser Abschnitt beschreibt eine Erweiterung der [OID Wi-Fi-Dokumentation](http://msdn.microsoft.com/library/ff560670.aspx) , damit unabhängigen Hardwareanbietern eine Reihe von Schnittstellen implementiert werden können, mit denen OEMs testanwendungen erstellen.

## <a name="span-idassumptionsspanspan-idassumptionsspanspan-idassumptionsspanassumptions"></a><span id="Assumptions"></span><span id="assumptions"></span><span id="ASSUMPTIONS"></span>Annahmen


Um diese Fertigung Tests auszuführen, muss das Gerät in einem speziellen Vorgang Modus aufgerufen Fertigung Modus ausgeführt werden. In der Fertigung-Modus werden nur bestimmte Teile des Betriebssystems geladen, um die ordnungsgemäße Ausführung von Komponententests zu aktivieren. Normal Wi-Fi-Vorgänge, wie etwa untersucht und automatisch eine Verbindung mit Netzwerken sind deaktiviert, wenn das Gerät im Fertigung Modus ausgeführt wird.

Fertigung Modus kann in der Fertigung Umgebung oder während der Kundendienst eingegeben werden. Schreiben auf Gerät Provisioning Partition (DPP) kann nur in der Fertigung Umgebung ausgeführt werden. Wenn in einer Umgebung nicht Fertigung eine, die in den DPP schreibt OID aufgerufen wird, schlägt der Versuch zum Schreiben in den DPP. Fertigungsprozesse sollte nur eine vorübergehende Auswirkung auf das System, und der Status sollten auch nach einem Neustart Sitzungen nicht bestehen.

## <a name="span-iddriverrequirementsspanspan-iddriverrequirementsspanspan-iddriverrequirementsspandriver-requirements"></a><span id="Driver_requirements"></span><span id="driver_requirements"></span><span id="DRIVER_REQUIREMENTS"></span>Treiber Anforderungen


Wi-Fi-Miniporttreiber muss im normalen Modus oder manufacturing Testmodus ausgeführt werden können, und es muss zwischen Modi können Sie jederzeit wechseln können. Der Treiber bestimmt den entsprechenden Modus während der Initialisierung von Abfragen von einem bestimmten Registrierungsschlüssel.

Die folgende Abbildung zeigt die Architektur des Tests Fertigung Umgebung.

![Migrationstabellen-Editor-design](images/oem-manu-mte-design.png)

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_this_section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


<span id="Reporting_operating_mode_capabilities"></span><span id="reporting_operating_mode_capabilities"></span><span id="REPORTING_OPERATING_MODE_CAPABILITIES"></span>[Berichtsfunktionen funktionieren Modus](reporting-operating-mode-capabilities.md)  
Beschreibt die Anforderungen und das Verhalten für Änderungen mit Treibern, die im Testmodus manufacturing reporting.

<span id="Supporting_updated_OID_behavior_in_manufacturing_mode"></span><span id="supporting_updated_oid_behavior_in_manufacturing_mode"></span><span id="SUPPORTING_UPDATED_OID_BEHAVIOR_IN_MANUFACTURING_MODE"></span>[Unterstützung von aktualisierten OID Verhalten in Manufacturing Modus](supporting-updated-oid-behavior-in-manufacturing-mode.md)  
Beschreibt die aktualisierte OIDs, die durch den Miniporttreiber Wi-Fi unterstützt werden müssen.

<span id="Supporting_existing_OID_commands_in_manufacturing_mode"></span><span id="supporting_existing_oid_commands_in_manufacturing_mode"></span><span id="SUPPORTING_EXISTING_OID_COMMANDS_IN_MANUFACTURING_MODE"></span>[Unterstützung von vorhandenen OID Befehlen in Manufacturing Modus](supporting-existing-oid-commands-in-manufacturing-mode.md)  
Beschreibt die vorhandenen OIDs, die von der Wi-Fi-Miniporttreiber unterstützt werden müssen.

<span id="Supporting_new_OID_commands_for_manufacturing_mode"></span><span id="supporting_new_oid_commands_for_manufacturing_mode"></span><span id="SUPPORTING_NEW_OID_COMMANDS_FOR_MANUFACTURING_MODE"></span>[Unterstützung für neue OID Befehle für Fertigung-Modus](supporting-new-oid-commands-for-manufacturing-mode.md)  
Beschreibt die neuen OIDs, die von der Wi-Fi-Miniporttreiber unterstützt werden müssen.

<span id="Supporting_new_callbacks_for_manufacturing_mode"></span><span id="supporting_new_callbacks_for_manufacturing_mode"></span><span id="SUPPORTING_NEW_CALLBACKS_FOR_MANUFACTURING_MODE"></span>[Unterstützung für neue Rückrufe für Fertigung-Modus](supporting-new-callbacks-for-manufacturing-mode.md)  
Beschreibt den neuen OID-Rückruf, der von der Wi-Fi-Miniporttreiber unterstützt werden muss.

 

 





