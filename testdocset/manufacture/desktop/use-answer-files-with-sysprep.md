---
author: Justinha
Description: Verwenden von Antwortdateien mit Sysprep
ms.assetid: baa66548-b1f8-42f4-8027-3d515441ac0c
MSHAttr: PreferredLib:/library/windows/hardware
title: Verwenden von Antwortdateien mit Sysprep
ms.openlocfilehash: 90a374e51e6a8126ac71dcd75613398b6b25c868
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-answer-files-with-sysprep"></a>Verwenden von Antwortdateien mit Sysprep


Eine Antwortdatei zusammen mit dem Tool System Preparation (**Sysprep**) können Sie unbeaufsichtigte Windows® Setup Einstellungen konfigurieren. In diesem Thema werden einige Aspekte und Prozesse für die Verwendung von Antwortdateien zusammen mit **Sysprep**beschrieben. Weitere Informationen zu Windows-Komponenten und Einstellungen, die eine Antwortdatei hinzugefügt werden können, finden Sie unter der [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

In diesem Thema:

-   [Ausführen von Sysprep eine unbegrenzte Anzahl von Klicks](#bkmk-skiprearm)

-   [Anwenden von Einstellungen in der verallgemeinern AuditSystem und AuditUser Konfigurationsphasen](#bkmk-1)

-   [Zwischenspeichern von Antwortdateien auf dem Computer](#bkmk-2)

-   [Speichern von Plug & Play-Gerätetreibern während der verallgemeinern Konfigurationsphasen](#bkmk-3)

-   [Anzeigen von RunSynchronous Aktionen in einer Antwortdatei](#bkmk-4)

## <a name="span-idbkmkskiprearmspanspan-idbkmkskiprearmspanspan-idbkmkskiprearmspanrunning-sysprep-an-unlimited-number-of-times"></a><span id="bkmk_skipRearm"></span><span id="bkmk_skiprearm"></span><span id="BKMK_SKIPREARM"></span>Ausführen von Sysprep eine unbegrenzte Anzahl von Klicks


Wenn Sie einen Product Key angeben, Windows wird automatisch aktiviert, und Sie können dem Befehl **Sysprep** eine unbegrenzte Anzahl von Klicks ausführen. Um Windows automatisch durch Bereitstellen einen Product Key zu aktivieren, geben Sie einen gültigen Product Key in der Microsoft-Windows-Shell-Setup\\ `ProductKey` für die Einstellung der in der Phase der [specialize](specialize.md) Konfiguration unbeaufsichtigte Installation. Wenn Sie automatisch Windows aktivieren nicht durch einen Product Key bereitstellen, fordert Windows die Endbenutzer einen Product key. Wenn der Benutzer diesen Schritt während OOBE überspringt, erinnert Windows später einen gültigen Product Key eingeben den Endbenutzer.

## <a name="span-idbkmk1spanspan-idbkmk1spanapplying-settings-in-the-generalize-auditsystem-and-audituser-configuration-passes"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Anwenden von Einstellungen in der verallgemeinern, AuditSystem und AuditUser Konfigurationsphasen


Nicht alle Konfigurationsphasen führen während der Windows-Installation. Konfigurationsphasen [verallgemeinern](generalize.md), [AuditSystem](auditsystem.md)und [AuditUser](audituser.md) stehen nur, wenn Sie **Sysprep**ausführen.

Wenn Sie die Antwortdatei in diesen Konfigurationsphasen Einstellungen hinzugefügt haben, führen Sie **Sysprep** aus, um diese Einstellungen wie folgt angewendet:

-   Wenn die Einstellungen in den Konfigurationsphasen [AuditSystem](auditsystem.md) und [AuditUser](audituser.md) anwenden möchten, müssen Sie im Überwachungsmodus mithilfe des Befehls **Sysprep/Audit** starten.

-   Wenn die Einstellungen im Durchgang Konfiguration [verallgemeinern](generalize.md) anwenden möchten, müssen Sie den Befehl **Sysprep/verallgemeinern** verwenden. Übergeben Sie die verallgemeinern Konfiguration entfernt die systemspezifische-Einstellungen, damit Sie das gleiche Bild auf mehreren Computern bereitstellen können.

Weitere Informationen finden Sie unter [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md).

## <a name="span-idbkmk2spanspan-idbkmk2spancaching-answer-files-to-the-computer"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Zwischenspeichern von Antwortdateien auf dem Computer


Wenn Sie mithilfe einer Antwortdatei Windows installieren, wird an das System die Antwortdatei zwischengespeichert. Wenn höher ausgeführt Konfigurationsphasen, gilt der Computer Einstellungen in die Antwortdatei für das System. Da diese Antwortdatei zwischengespeichert wird, wenn Sie den Befehl **Sysprep** ausführen, werden die Einstellungen in der zwischengespeicherten Antwortdatei angewendet. Wenn Sie die Einstellungen in eine andere Antwortdatei verwenden, können Sie mithilfe eine separate Unattend.xml-Datei angeben der **Sysprep / für die unbeaufsichtigte Installation:***&lt;Datei\_Namen&gt; * Option. Weitere Informationen finden Sie unter [Sysprep Command-Line Options](sysprep-command-line-options.md). Weitere Informationen dazu, wie Sie zu einer impliziten Antwortdatei-Suche finden Sie unter[Übersicht über die Automatisierung von Windows-Setup](windows-setup-automation-overview.md).

## <a name="span-idbkmk3spanspan-idbkmk3spanpersisting-plug-and-play-device-drivers-during-the-generalize-configuration-pass"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>Speichern von Plug & Play-Gerätetreibern während der verallgemeinern Konfigurationsphasen


Sie können Gerätetreiber beibehalten, wenn Sie den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** ausführen. Geben Sie dazu die `PersistAllDeviceInstalls` Einstellung in der Microsoft Windows-PnPSysprep-Komponente. Während des Schritts [specialize](specialize.md) Konfiguration Plug & Play Überprüfen des Computers für Geräte und installiert dann Gerätetreiber für die erkannten Geräte. Standardmäßig entfernt den Computer diese Gerätetreiber aus dem System, wenn Sie das System verallgemeinern. Wenn Sie die Microsoft-Windows-PnPSysprep festlegen\\ `PersistAllDeviceInstalls` in eine Antwortdatei auf **true** festlegen, wird nicht Sysprep die erkannten Gerätetreiber entfernen.

## <a name="span-idbkmk4spanspan-idbkmk4spandisplaying-runsynchronous-actions-in-an-answer-file"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Anzeigen von RunSynchronous Aktionen in einer Antwortdatei


Sie können den Status für die Microsoft-Windows-Bereitstellung anzeigen, im Überwachungsmodus aktiviert,\\ `RunSynchronous` Befehle, die während der [AuditUser](audituser.md) Konfigurationsdurchlauf ausgeführt. Das Fenster **AuditUI** zeigt den Status für Befehle und stellt diese bereit:

-   Visuelle Fortschrittsanzeige, um anzugeben, dass eine Installation fortgeführt und nicht angehalten ist.

-   Visuell der wann und wo Fehler auftreten. Dies stellt eine schnelle Diagnose bereit, wenn Sie der Befehl keine Protokolldateien erstellt.

Enthält die Antwortdatei Microsoft Windows-Deployment\\ `RunSynchronous` Befehle in die Konfiguration [AuditUser](audituser.md) übergeben wird, klicken Sie im Fenster **AuditUI** wird eine Liste der Befehle angezeigt. Die Befehle in der Reihenfolge angezeigt, die Microsoft-Windows-Deployment\\ `RunSynchronous` \\ `RunSynchronousCommand` \\ `Order` Einstellung wird angegeben. Jedes Listenelement auf der Benutzeroberfläche wird die Zeichenfolge aus eine der folgenden:

-   Microsoft Windows-Deployment\\ `RunSynchronous` \\ `RunSynchronousCommand` \\ `Description` (falls vorhanden)

-   Microsoft-Windows-Bereitstellung\\`RunSynchronous`\\`RunSynchronousCommand`\\`Path`

Alle **Sysprep** verarbeitet `RunSynchronous` Befehle in der Reihenfolge. Wenn der Befehl erfolgreich ausgeführt wird, erhält das zugehörige Listenelement ein grünes Häkchen Annotation. Wenn der Befehl fehlschlägt, erhält das zugehörige Listenelement ein rotes X Annotation. Der Befehl einen Neustart anfordert, Fenster **AuditUI** nach dem Start angezeigt, aber nur nicht verarbeitete Listenelementen angezeigt werden. Verarbeitete Elemente zuvor nicht mehr im Fenster **AuditUI** angezeigt. Wenn die Liste der Elemente im Fenster **AuditUI** die Höhe der Anzeige überschreitet, wird die Liste ist, auf die Anzeige gekürzt und rollt nicht. Daher können Sie nicht finden einige Elemente sein.

Windows-Setup interpretiert die Rückgabecodes als Statuswerte im Fenster **AuditUI** . Ein NULL-Wert gibt an, einem Erfolg wird. Ein Wert ungleich Null gibt einen Fehler an. Der Rückgabewert des Befehls kann sich auf das Verhalten der Windows-Installation, abhängig vom Wert der Microsoft-Windows-Bereitstellung auswirken\\`RunSynchronous`\\`RunSynchronousCommand`\\**WillReboot** Einstellung.

Wenn die `WillReboot` Befehl auf **Always**festgelegt ist:

-   Wenn Sie der Befehl 0 zurückgegeben wird, erhält das zugehörige Listenelement ein grünes Häkchen Annotation. Ein Neustart wird sofort ausgeführt.

-   Wenn der Befehl eine Zahl ungleich NULL zurückgegeben wird, erhält das zugehörige Listenelement ein rotes X Annotation. Ein Neustart wird sofort ausgeführt. Ein Wert ungleich NULL ist nicht als ein schwerwiegender Fehler behandelt beim `WillReboot` **immer** oder **nie**festgelegt ist.

Wenn die `WillReboot` Befehl auf **Never**festgelegt ist:

-   Wenn der Befehl gibt 0 zurück, erhält das zugehörige Listenelement ein grünes Häkchen Annotation.

-   Wenn der Befehl eine Zahl ungleich NULL zurückgegeben wird, erhält das zugehörige Listenelement ein rotes X Annotation. Ein Wert ungleich NULL ist nicht als ein schwerwiegender Fehler behandelt beim `WillReboot` **immer** oder **nie**festgelegt ist.

Wenn die `WillReboot` Befehl auf **OnRequest**festgelegt ist:

-   Wenn der Befehl 0 zurückgibt, erhält das zugehörige Listenelement ein grünes Häkchen Annotation.

-   Wenn der Befehl 1 zurückgibt, erhält das zugehörige Listenelement ein grünes Häkchen Annotation. Ein Neustart wird sofort ausgeführt.

-   Wenn Sie der Befehl 2 zurückgegeben wird, erhält das zugehörige Listenelement vorübergehend ein grünes Häkchen Annotation. Ein Neustart wird sofort ausgeführt. Nach dem Neustart wird das zugehörige Listenelement erneut im Fenster **AuditUI** ohne Anmerkung, da der Befehl noch verarbeitet wird.

-   Wenn Sie der Befehl andere Werte zurückgegeben werden, ein schwerwiegender Fehler auftritt und ein blockierenden Dialogfeld wird angezeigt. Wenn die Datei Errorhandler.cmd vorhanden ist, wird kein Dialogfeld angezeigt. Weitere Informationen zur Datei Errorhandler.cmd finden Sie unter [Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md)

[Sysprep-Befehlszeilenoptionen](sysprep-command-line-options.md)

[Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md)

[Sysprep-Prozess (Übersicht)](sysprep-process-overview.md)

[Problembehandlung von Bereitstellung und Protokolldateien](deployment-troubleshooting-and-log-files.md)

 

 






