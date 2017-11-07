---
author: kpacquer
Description: "In Windows 10 Mobile eingeführt wurde, ist Fertigung Modus ein Modus der Vollversion des Betriebssystems, die für die Fertigung-bezogene Aufgaben wie das Komponente verwendet werden kann und getestet."
ms.assetid: 9c5831f5-a200-436c-97cc-8bd92b30cb3e
MSHAttr: PreferredLib:/library/windows/hardware
title: Fertigung-Modus
ms.openlocfilehash: ae3d9d861123199b3caad447bdaec0eda1ff743a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-mode"></a>Fertigung-Modus


In Windows 10 Mobile eingeführt wurde, ist der Fertigung Modus ein Modus der Vollversion des Betriebssystems, die für die Fertigung-bezogene Aufgaben wie das Komponente verwendet werden kann und getestet.

In Windows Phone 8.1 musste das Microsoft Fertigung Betriebssystem (MMOS) um Manufacturing Tests durchführen flash und in den Prozessen, z. B. Test-Hardware sprengen fixiert Sicherheitsschlüssel. Nachdem die Tests abgeschlossen werden konnten, mussten Sie flash Vollversion des Betriebssystems. Diese hinzugefügt zusätzliche Zeit auf die Fertigung.

Dieses neue Feature können Sie ein Fertigung Modus des vollständigen Betriebssystems starten (und führen Sie diese Schritte Fertigung) ohne Schwelle MMOS flash an.

## <a name="span-idmanufacturingprofilesspanspan-idmanufacturingprofilesspanspan-idmanufacturingprofilesspanmanufacturing-profiles"></a><span id="Manufacturing_profiles"></span><span id="manufacturing_profiles"></span><span id="MANUFACTURING_PROFILES"></span>Fertigung Profile


Ein Profil Fertigung definiert die Einstellungen, die verwendet werden soll, wenn das Betriebssystem im Modus Fertigung gestartet wird. Das Gerät kann mehrere Fertigung Profil haben. Ein Profil mit dem Namen Default gehört zum Lieferumfang von Windows 10 Mobile. Das Standardprofil enthält die Einstellungen für Microsoft-Komponenten, mit die die Gerät Boot für Manufacturing-Modus in einer Umgebung mit minimalem können.

Fertigung Profile werden in der Registrierung auf dem Gerät an folgendem Speicherort gespeichert:

**HKEY\_LOKALE\_COMPUTER\\System\\CurrentControlSet\\Steuerelement\\ManufacturingMode** Sie müssen einen Unterschlüssel für jedes Fertigung-Profil erstellen. Unter dem Profilschlüssel können Sie die Einstellungen für einige Komponenten auswählen des Betriebssystems für, wenn das System im Fertigung Modus gestartet wird, ändern. Beispielsweise können Sie ändern, welche Dienste gestartet werden, wenn dieses Profil Manufacturing aktiviert ist. Sie können Ihre eigenen Dienste im Unterschlüssel Services hinzufügen, wie unten dargestellt. Wenn Sie alle Dienste auf den gleichen Starttyp festlegen möchten, können Sie eine \* für den Dienst ein. Wenn die \* Platzhalter nicht verwendet wird, werden allen Win32-Diensten, die nicht im Profil Manufacturing enthalten sind ihre Start Standardtyp verwenden.

**Hinweis**  Die \* Platzhalter betrifft nur Win32-Services, ausgenommen Kernelmodus-Treiber.

 

Im folgenden Beispiel wird ein Fertigung Profil mit dem Namen CustomProfile erstellt, bewirkt, dass der Dienst mit dem Namen OEMFactoryTestService für den automatischen start und alle anderen Win32-Dienste manuell starten:

``` syntax
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\OEMFactoryTestService]
"Start"=dword:00000002

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\*]
"Start"=dword:00000003
```

Das Profil Fertigung weniger als 64 Zeichen sein.

Sie können nicht für den Namen Ihres Profils Fertigung **aktuelle** verwenden. Dieser Name wird für das derzeit aktive Manufacturing Profil reserviert.

 

 





