---
author: Justinha
Description: "Features für die Problembehandlung von Windows RE"
ms.assetid: 5812bba2-a4ed-4659-87b0-774de7a84bf5
MSHAttr: PreferredLib:/library/windows/hardware
title: "Features für die Problembehandlung von Windows RE"
ms.openlocfilehash: 9fea5e93c73a17cd5468102da2bf93afc1980a95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-re-troubleshooting-features"></a>Features für die Problembehandlung von Windows RE


Wenn ein Windows-Gerät gestartet werden kann, kann es automatisch über Windows Recovery Environment (Windows RE). Das Tool automatisch reparieren in Windows RE automatisiert die Diagnose und Reparatur von ein. Windows RE ist auch ein Ausgangspunkt für verschiedene Tools für die manuelle Wiederherstellung. In diesem Thema wird das Verhalten für automatisches Failover, manuelle Diagnose und Reparatur in Windows RE.

In diesem Thema:

-   [Wiederherstellen von Startproblemen](#bkmk-1)

-   [Erweiterte Dienstprogramme in Windows RE-Problembehandlung](#bkmk-2)

## <a name="span-idbkmk1spanspan-idbkmk1spanrecovering-from-startup-failures"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Wiederherstellen von Startproblemen


Wenn das System einen Boot-Fehler auf einem Computer mit Windows erkennt, automatisch ein Failover des Systems in das Windows RE-Tool auf dem Datenträger. Beim Start wird das Windows-Ladeprogramm ein Status-Flag, um anzugeben, dass der Boot-Prozess gestartet wurde. Windows löscht dieses Flag normalerweise, damit im Anmeldebildschirm von Windows angezeigt wird. Wenn der Boot Versuch ein Fehler auftritt, deaktivieren nicht Windows das Flag. Beim nächsten des Computers starten das Ladeprogramm erkennt die Kennzeichnung und wird davon ausgegangen, dass ein Boot-Fehler aufgetreten ist. In diesem Fall startet das Ladeprogramm Windows RE anstelle von Windows.

**Hinweis**  
Erkennung von Fehlern beim Starten nutzt Boot Abschluss und nicht, ob ein Fehler in Windows 8 aufgetreten ist. Beispielsweise kann ein falsch positives Ergebnis auftreten, wenn Power verloren, während des Startvorgangs geht, und Ihre Benutzer Windows RE startet, obwohl die Windows-Installation gestartet werden kann.

 

Da der Failover-Mechanismus auf der Windows-Start-Manager und dem Windows-Startladeprogramm basiert, können einige Fehler Windows RE nicht zugegriffen werden. In den folgenden Szenarien muss Ihre Benutzer startbaren Windows RE-Medien verwenden, um den Computer wiederherzustellen:

-   Beschädigte Datenträger-Metadaten im MBR (MBR), Partitionstabelle oder Boot-Sektor einer Windows RE-Partition vorhanden ist.

-   Der Start-Manager ist fehlt oder beschädigt.

-   Der Boot Configuration Data (BCD) Speicher ist fehlt oder ist beschädigt.

Wenn dem Startladeprogramm nicht lesen oder in das Boot Status-Flag schreiben, werden Windows kann nicht auf Windows RE automatisches Failover ausgeführt. Jedoch kann Benutzer das Tool auf dem Datenträger Windows RE über das Menü **Startoptionen** immer noch manuell starten.

## <a name="span-idbkmk2spanspan-idbkmk2spanadvanced-troubleshooting-utilities-in-windows-re"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Erweiterte Problembehandlung Dienstprogramme im Windows RE


Ihre Benutzer kann mehrere Systemprogramme Wiederherstellung nach dem Starten des Windows RE-Tools auf dem Datenträger aus Wiederherstellungsmedien oder aus dem Menü **Startoptionen** manuell starten. Mit Ausnahme von automatischer Reparatur enthalten Windows Assessment and Deployment Kit (Windows ADK) nicht diese Tools. Drucktaste Reset ist die empfohlene Lösung für die in Windows.

### <a name="span-idbkmkaspanspan-idbkmkaspanautomatic-repair"></a><span id="bkmk_a"></span><span id="BKMK_A"></span>Automatische Reparatur

Das Tool automatisch reparieren automatisiert häufig vorkommender Diagnose- und Reparaturaufgaben für nicht startbaren Operating System-Installationen. Automatischer Reparatur startet, wenn der Computer über Windows RE aufgrund eines Fehlers erkannte Boot ausfällt. Wenn der Automatisches Failover auf eine Instanz auf dem Datenträger Windows RE nicht verfügbar ist, können Ihre Benutzer auch automatischer Reparatur als Wiederherstellungstool manuelle von einer Windows RE-CD oder DVD starten.

### <a name="span-idbkmkcspanspan-idbkmkcspansystem-image-recovery"></a><span id="bkmk_c"></span><span id="BKMK_C"></span>Wiederherstellung des Systems Bild

Verwenden Sie System Image-Recovery für Sicherung und System Image Backup. Wiederherstellung des Systems Bild ist ein externes Speichergerät erforderlich. Sicherung die Benutzer können automatisch den zu sichernden Daten auswählen oder sie können einzelne Ordner, Bibliotheken und Laufwerke auswählen. Standardmäßig werden die Sicherungen in regelmäßigen Abständen erstellt. Die Benutzer können Ändern des Zeitplans und manuell eine Sicherung können Sie jederzeit erstellen. Nach der Wiederherstellung des Systems Bild Ihrer Benutzer einrichtet, werden von nachverfolgt Windows neue oder geänderte Dateien und Ordner, die Sicherung hinzugefügt.

Für System Image-Backup können die Benutzer ein System Image oder genaues Abbild eines Laufwerks erstellen. Ein System-Image enthält Windows- und Systemeinstellungen, Programme und Dateien. Die Benutzer können ein System-Image zum Wiederherstellen der Inhalte von ihrem Computer, wenn die Festplatte oder Computer reagiert nicht mehr verwenden.

Wenn Ihre Benutzer ihren Computer über ein System-Image wiederherstellen, wird die Wiederherstellung einer vollständigen Wiederherstellung. Ihre Benutzer können nicht zum Wiederherstellen einzelner Elemente auswählen. Alle aktuellen Programme, Systemeinstellungen und Dateien werden ersetzt.

Wenn Sie eine geplante Sicherung eingerichtet haben, können Sie ein Systemabbild mit nur die Laufwerke, auf einschließen benötigten Windows ausführen. Wenn Sie zusätzliche Datenlaufwerke einschließen möchten, können Sie manuell ein System-Image erstellen.

**Hinweis**  
System Image Vorgängerversionen sind Kopien von Dateien und Ordner von Windows im Rahmen des Prozesses Protection System automatisch gespeichert. Ihre Benutzer können je nach Typ der Datei oder einen Ordner eine frühere Version zu öffnen, speichern die Version an einem anderen Speicherort oder Wiederherstellen einer vorherigen Version. Die Benutzer können diese früheren Versionen Wiederherstellen versehentlich geänderte, gelöschte oder beschädigte Dateien und Ordnern. Jedoch da Windows diese Dateien durch neue Versionen ersetzt sind die Dateien nur verfügbar, wenn das Laufwerk ein Fehler auftritt.

 

### <a name="span-idbkmkdspanspan-idbkmkdspancommand-prompt"></a><span id="bkmk_d"></span><span id="BKMK_D"></span>Befehlszeile

Alle Windows PE Befehlszeilentools stehen aus ein Eingabeaufforderungsfenster. Beispielsweise können Sie Registrierungs-Editors (Regedit.exe), einschließlich Befehlszeilenoptionen aufgeführt, um die Windows-Registrierung zu ändern. Alternativ können Sie das Tool Chkdisk.exe Behandlung und Korrektur Volumes. Weitere Informationen finden Sie unter [Registrierungs-Editor](http://go.microsoft.com/fwlink/?LinkId=207693), [Chkdsk](http://go.microsoft.com/fwlink/?LinkId=207694)und [Tools zur Problembehandlung und Strategien](http://go.microsoft.com/fwlink/?LinkId=207695).

### <a name="span-idbkmkespanspan-idbkmkespancustom-support-and-recovery-tools"></a><span id="bkmk_e"></span><span id="BKMK_E"></span>Benutzerdefinierte Support- und Wiederherstellungstools

Computer Manufacturers können benutzerdefinierte Support- und Recovery Tools bereitstellen. Diese Tools variiert je nach Hersteller. Weitere Informationen finden Sie unter der Hersteller bereitgestellte Dokumentation.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[REAgentC Befehlszeilenoptionen](reagentc-command-line-options.md)

 

 






