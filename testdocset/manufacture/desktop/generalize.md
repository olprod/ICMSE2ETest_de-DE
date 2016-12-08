---
author: Justinha
Description: Verallgemeinern
ms.assetid: 90b8329e-dc6a-49e6-ad6a-09c56b27f6e8
MSHAttr: PreferredLib:/library/windows/hardware
title: Verallgemeinern
ms.openlocfilehash: 3264f3ab11bf2c47a627d2d055846ca7d81e66c9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="generalize"></a>Verallgemeinern


Übergeben Sie den **verallgemeinern** Konfiguration von Windows® Setup wird verwendet, um ein Windows-Abbild Verweis zu erstellen, die in der gesamten Organisation verwendet werden kann. Einstellungen im Durchgang Konfiguration **verallgemeinern** aktivieren Sie das Verhalten bei allen Bereitstellungen von dieses Referenzabbild, zu automatisieren. Im Vergleich aktivieren im Durchgang Konfiguration [specialize](specialize.md) angewendeten für Sie Verhalten für eine einzelne, spezifische Bereitstellung außer Kraft gesetzt.

Wenn ein System allgemeiner (engl.) ist, werden-spezifische Konfigurationsdaten für eine bestimmte Installation von Windows entfernt. Beispielsweise werden während des Schritts **verallgemeinern** Konfiguration die eindeutige Sicherheits-ID (SID) und andere Hardware-spezifischen Einstellungen aus dem Bild entfernt.

Übergeben Sie die Konfiguration **verallgemeinern** führt nur, wenn Sie den Befehl **Sysprep** mit der Option **/ verallgemeinern** verwenden. Beantworten Sie dateieinstellungen in die `<generalize>` Abschnitt einer Antwortdatei gelten für das System bevor **Sysprep** Generalisierung erfolgt. Das System wird heruntergefahren.

Das folgende Diagramm zeigt den Prozess von der Konfiguration **verallgemeinern** übergeben.

![Verallgemeinern Konfigurationsphasen](images/dep-win8-l-generalizeunattend.jpg)

Übergeben Sie die Konfiguration [specialize](specialize.md) unmittelbar nach der nächsten, die beim Start des Systems ausgeführt wird. Wenn Sie **Sysprep**ausführen, können Sie entscheiden, ob Windows im Überwachungsmodus oder die Windows-Willkommensseite gestartet werden kann, **indem/audit** **oder/Oobe**angeben. Die Konfiguration **specialize** übergeben immer ausgeführt wird, nachdem ein Computer allgemeiner (engl.) wurde ist unabhängig davon, ob der Computer konfiguriert ist, zum Starten Modus oder im Windows-Willkommensseite zu überwachen.

Jede Methode verschieben oder Kopieren eines Windows-Abbilds zu einem neuen Computer muss mit vorbereitet werden die **Sysprep / verallgemeinern** Befehl. Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[specialize](specialize.md)

[windowsPE](windowspe.md)

 

 






