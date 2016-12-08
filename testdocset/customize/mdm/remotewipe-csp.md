---
title: RemoteWipe CSP
description: RemoteWipe CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6e89bd37-7680-4940-8a67-11ed062ffb70
ms.openlocfilehash: dd01f00604b70b54455e6e2b05809cdd9b595d38
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotewipe-csp"></a>RemoteWipe CSP


Dienstanbieter RemoteWipe Konfiguration kann auf einem Gerät Remote Wischen Mobilfunkbetreibern DM Server oder Enterprise Management Server verwendet werden. Dienstanbieter RemoteWipe Konfiguration kann stellen Sie die Daten im Arbeitsspeicher und zur Wiederherstellung nach einem verlorenen oder gestohlenen Remote das Gerät bereinigt ist schwierig Festplatten gespeichert.

Das folgende Diagramm veranschaulicht das RemoteWipe Configuration Service Provider Management-Objekts im Strukturformat von OMA DM sowohl OMA-Clientbereitstellung verwendet. Enterprise IT Professionals können diese Einstellungen mithilfe der Exchange-Server aktualisieren.

![Remotewipe Csp (dm, cp)](images/provisioning-csp-remotewipe-dmandcp.png)

<a href="" id="dowipe"></a>**doWipe**  
Gibt an, dass eine Remotezurücksetzung des Geräts ausgeführt werden soll. Der Rückgabestatuscode gibt an, ob das Gerät mit den Befehl Exec akzeptiert.

Bei Verwendung mit OMA-Clientbereitstellung sollten simulierte Wert "1" für dieses Element eingebunden werden.

Unterstützte Vorgang ist Exec.

<a href="" id="dowipepersistprovisioneddata"></a>**doWipePersistProvisionedData**  
Gibt an, dass Daten-Bereitstellung werden an einen permanenten Speicherort gesichert sollten und eine Remotezurücksetzung des Geräts ausgeführt werden sollte.

Unterstützte Vorgang ist Exec.

Bei Verwendung mit OMA-Clientbereitstellung sollten einem Platzhalterwert von "1" für dieses Element eingebunden werden.

Die Informationen, die gesichert wurde, wird wiederhergestellt und auf dem Gerät angewendet, wenn es fortgesetzt werden. Der Rückgabestatus-Code zeigt, ob das Gerät mit den Befehl Exec akzeptiert.

## <a name="the-remote-wipe-process"></a>Der Prozess Remotezurücksetzung


Der Befehl Remotezurücksetzung wird als ein XML-Bereitstellungsdatei an das Gerät gesendet. Seit der RemoteWipe Konfigurationsdienstanbieter OMA DM und WAP verwendet wird, wird die Authentifizierung zwischen Client und Server und Übermittlung der Bereitstellung XML-Datei von provisioning behandelt.

In Windows Mobile 10 wird der Befehl Remotezurücksetzung auf dem Gerät mithilfe der Funktion **ResetPhone** implementiert. Auf dem Desktop löst die Remotezurücksetzung die Funktionalität **dieser PC zurücksetzen** mit der Option **Alles entfernen** .

> **Hinweis**  Auf dem Desktop führt die Remotezurücksetzung effektiv Herstellerstandard zurücksetzen und PC nicht keine Informationen über den Befehl beibehalten, wenn der Löschvorgang abgeschlossen ist. Antwort vom Gerät zu den aktuellen Status oder das Ergebnis des Befehls möglicherweise inkonsistent und unzuverlässige die MDM Informationen entfernt wurden.

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






