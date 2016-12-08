---
author: Justinha
Description: "Übersicht über den Sysprep Upgradeprozess"
ms.assetid: e764e19f-8a8a-4fae-aa1f-22e70caf1599
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übersicht über den Sysprep Upgradeprozess"
ms.openlocfilehash: d25dee3b0e055479d5d91687eb7ed0a9e4bcf045
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-process-overview"></a>Übersicht über den Sysprep Upgradeprozess


Das Tool System Preparation (**Sysprep**) wird verwendet, um Windows® Bilder aus dem allgemeinen Status auf einen speziellen Zustand ändern und dann auf allgemeine Übersicht über einen bekannten Zustand zurück. Eine allgemeine Übersicht über Bild kann auf allen Computern bereitgestellt werden. Ein spezieller Bild ist auf einem bestimmten Computer abgestimmt. Sie müssen reseal oder verallgemeinern, ein Windows-Abbild vor dem Bereitstellen des Abbilds und erfassen. Angenommen, wenn Sie das **Sysprep** -Tool verwenden, um ein Abbild verallgemeinern, **Sysprep** entfernt alle-spezifische Informationen und setzt den Computer. Beim nächsten des Computers Neustart können Ihre Kunden hinzufügen benutzerspezifische Informationen über Out-Of-Box-Experience (OOBE) und die Microsoft-Software-Lizenzbedingungen akzeptieren.

**Sysprep.exe** befindet sich der **%windir%\\system32\\Sysprep** Verzeichnis auf allen Windows-Installationen.

Wenn Sie ein Windows-Abbild auf einen anderen Computer übertragen, müssen Sie den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** ausführen, selbst wenn der andere Computer die gleiche Hardwarekonfiguration verfügt. Die **Sysprep / verallgemeinern** Befehl eindeutigen Informationen aus der Windows-Installation entfernt, sodass Sie das Abbild auf einem anderen Computer wiederverwenden können. Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

In diesem Thema:

-   [Sysprep ausführbare Datei](#sysprepexecutable)

-   [Übersicht über den Sysprep Upgradeprozess](#sysprepprocess)

-   [Beibehalten der Hardwarekonfiguration](#bkmk-new)

-   [Hinzufügen von Gerätetreibern](#device)

-   [Zum Überwachen von Modus oder OOBE starten](#bootingtoauditmodeorwindowswelcome)

-   [Ermitteln des Status eines Windows-Abbilds](#detectingthestateofawindowsimage)

-   [Sysprep-Protokolldateien](#syspreplogfiles)

-   [Erstellen und Verwenden von Sysprep-Anbieter](#creatingandusingsysprepproviders)

## <a name="span-idsysprepexecutablespanspan-idsysprepexecutablespanspan-idsysprepexecutablespansysprep-executable"></a><span id="SysprepExecutable"></span><span id="sysprepexecutable"></span><span id="SYSPREPEXECUTABLE"></span>Sysprep ausführbare Datei


**Sysprep.exe** wird das Hauptfenster Programm, das andere ausführbaren Dateien aufruft, die Windows-Installation vorbereiten. **Sysprep.exe** befindet sich der **%windir%\\system32\\Sysprep** Verzeichnis auf allen Windows-Installationen. Wenn Sie die Befehlszeile anstelle der **Systemvorbereitungstool** GUI verwenden, müssen Sie zuerst schließen die Benutzeroberfläche und führen Sie **Sysprep** aus der **%windir%\\system32\\Sysprep** Directory. Sie müssen auch **Sysprep** auf dieselbe Version von Windows ausführen, die Sie verwendet, um **Sysprep**zu installieren.

**Wichtige**  
Beginnen mit Windows 8.1, ist die Benutzeroberfläche Sysprep veraltet. Die Sysprep UI wird weiterhin in dieser Version unterstützt werden, aber es in einer zukünftigen Version entfernt werden kann. Es wird empfohlen, dass Sie Ihre Windows-Bereitstellungsworkflow, um mithilfe der Befehlszeile Sysprep aktualisieren. Weitere Informationen zu Sysprep-Befehlszeilentools finden Sie unter [Sysprep Command-Line Options](sysprep-command-line-options.md).

 

## <a name="span-idsysprepprocessspanspan-idsysprepprocessspanspan-idsysprepprocessspansysprep-process-overview"></a><span id="SysprepProcess"></span><span id="sysprepprocess"></span><span id="SYSPREPPROCESS"></span>Übersicht über den Sysprep Upgradeprozess


Sysprep ausgeführt wird, erfolgt über den folgenden Prozess:

1.  **Sysprep-Überprüfung**. Stellt sicher, dass Sysprep ausgeführt werden kann. Nur Administratoren kann Sysprep ausführen. Nur eine Instanz von Sysprep kann zu einem Zeitpunkt ausführen. Darüber hinaus muss Sysprep auf der Version von Windows ausgeführt, die Sie zum Installieren von Sysprep verwendet.

2.  **Initialisierung Protokollierung**. Die Protokollierung wird initialisiert. Weitere Informationen finden Sie unter [Sysprep-Protokolldateien](#syspreplogfiles).

3.  **Befehlszeilenargumente analysieren**. Befehlszeilenargumente analysiert. Wenn ein Benutzer keine Befehlszeilenargumente bereitstellt, wird ein Fenster Systemvorbereitungstool angezeigt und kann Benutzer Sysprep-Aktionen angeben.

4.  **Verarbeiten von Sysprep-Aktionen**. Sysprep-Aktionen verarbeitet, entsprechende DLL-Dateien und ausführbare Dateien aufgerufen und die Protokolldatei Aktionen hinzugefügt.

5.  **Sysprep Überprüfen Verarbeiten von Aktionen**. Überprüft, ob alle DLL-Dateien wurden alle ihre Aufgaben verarbeitet, und klicken Sie dann entweder heruntergefahren oder startet das System neu.

## <a name="span-idbkmknewspanspan-idbkmknewspanpersisting-the-hardware-configuration"></a><span id="bkmk_new"></span><span id="BKMK_NEW"></span>Beibehalten der Hardwarekonfiguration


Wenn Sie ein Abbild dieser Installation für die Bereitstellung auf einem anderen Computer erstellen, müssen Sie den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** ausführen, selbst wenn der andere Computer die identische Hardwarekonfiguration verfügt. Die **Sysprep / verallgemeinern** Befehl eindeutigen Informationen von einer Windows-Installation entfernt, sodass Sie das Abbild auf anderen Computern wiederverwenden können. Beim nächsten Starten des Windows-Abbilds führt die [specialize](specialize.md) Konfiguration übergeben.

Wenn Sie ein Windows-Abbild auf Computern installieren, die die gleiche Hardwarekonfiguration haben möchten, können Sie die Gerätetreiber Installation in einem Windows-Abbild beibehalten. Geben Sie dazu in die Antwortdatei Einstellung **PersistAllDeviceInstalls** , in der **Microsoft Windows-PnPSysprep** -Komponente. Der Standardwert ist **false**. Wenn Sie die Einstellung auf **true**festlegen, bleiben die Plug & Play-Geräte auf dem Computer während der Konfiguration [verallgemeinern](generalize.md) übergeben. Sie müssen keinen diese Geräte während der Konfiguration [specialize](specialize.md) Durchlauf neu installieren. Weitere Informationen finden Sie unter [Verwendung von Antwortdateien mit Sysprep](use-answer-files-with-sysprep.md) und unbeaufsichtigte Windows-Setup-Referenzhandbuch.

## <a name="span-iddevicespanspan-iddevicespanadding-device-drivers"></a><span id="device"></span><span id="DEVICE"></span>Hinzufügen von Gerätetreibern


Plug & Play-Geräten gehören Modems, Sound-, Netzwerkadapter und Grafikkarten. Plug & Play-Geräte auf den Verweis und Zielcomputer müssen nicht vom selben Hersteller stammen. Sie müssen jedoch die Installation der Treiber für diese Geräte enthalten. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Treiber eine Offline-Windows-Abbild](add-and-remove-drivers-to-an-offline-windows-image.md) und [Gerätetreiber hinzufügen, um Windows während Windows Setup](add-device-drivers-to-windows-during-windows-setup.md).

## <a name="span-idbootingtoauditmodeorwindowswelcomespanspan-idbootingtoauditmodeorwindowswelcomespanspan-idbootingtoauditmodeorwindowswelcomespanbooting-to-audit-mode-or-oobe"></a><span id="BootingToAuditModeOrWindowsWelcome"></span><span id="bootingtoauditmodeorwindowswelcome"></span><span id="BOOTINGTOAUDITMODEORWINDOWSWELCOME"></span>Zum Überwachen von Modus oder OOBE starten


Wenn Windows gestartet wird, Starten des Computers kann in einem von zwei Modi:

-   OOBE

    OOBE, ebenfalls den Namen der Out-of-Box-Experience (OOBE), wird die erste Benutzeroberfläche. OOBE ermöglicht Endbenutzern zum Anpassen der Windows-Installations. Endbenutzer können Benutzerkonten erstellen, lesen und akzeptieren der Lizenzbedingungen für Microsoft® Software und wählen Sie ihre Sprache und Zeitzonen aus. Standardmäßig starten Sie alle Windows-Installationen OOBE zuerst. [Die Konfigurationsphase](oobesystem.md) wird unmittelbar vor dem OOBE ausgeführt.

    Wenn Sie nicht automatisch Windows aktivieren mithilfe von einen Product Key, fordert OOBE den Benutzer für einen Product Key. Wenn der Benutzer diesen Schritt während OOBE überspringt, fragt Windows den Benutzer später einen gültigen Product Key eingeben. Um automatisch Windows über einen Product Key aktivieren, geben Sie einen gültigen Product Key in das **Microsoft-Windows-Shell-Setup\\ProductKey** für die unbeaufsichtigte Installation Einstellung während der Konfiguration [specialize](specialize.md) übergeben. Weitere Informationen finden Sie unter [Arbeiten mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md).

-   Im Überwachungsmodus

    Wenn Sie einen Computer im Überwachungsmodus zum Konfigurieren der Installation starten OOBE ausführen, verwenden Sie **Sysprep** GUI, oder führen Sie den Befehl **Sysprep/OOBE** . Um einen Computer für den Endbenutzer vorzubereiten, müssen Sie den Computer, OOBE zu starten, wenn ein Endbenutzer den Computer zum ersten Mal startet konfigurieren. In einer Standardinstallation von Windows beginnt OOBE nach Abschluss der Installation, jedoch Sie überspringen können OOBE und Boot direkt im Überwachungsmodus zum Anpassen von Bildern.

    Sie können direkt im Überwachungsmodus starten mithilfe der Microsoft Windows-Deployment **für Windows konfigurieren | Reseal | Modus** in einer Antwortdatei festlegen. Im Überwachungsmodus aktiviert verarbeitet der Computer in einer Antwortdatei in Konfigurationsphasen [AuditSystem](auditsystem.md) und [AuditUser](audituser.md) Einstellungen.

    Im Überwachungsmodus können Sie Windows-Abbilder Anpassungen hinzufügen. Überwachungsmodus erfordert nicht, dass Sie die Einstellungen in OOBE anwenden. Indem OOBE umgehen, können Sie schneller auf den Desktop zugreifen und Ihre Anpassungen führen. Sie können weitere Gerätetreiber hinzufügen, Applikationen installieren und testen die Gültigkeit der Installation.

Weitere Informationen finden Sie unter:

-   [Übersicht über Audit-Modus](audit-mode-overview.md)

-   [Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md)

-   [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

-   [Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos](enable-and-disable-the-built-in-administrator-account.md)

-   [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md)

## <a name="span-iddetectingthestateofawindowsimagespanspan-iddetectingthestateofawindowsimagespanspan-iddetectingthestateofawindowsimagespandetecting-the-state-of-a-windows-image"></a><span id="DetectingTheStateOfAWindowsImage"></span><span id="detectingthestateofawindowsimage"></span><span id="DETECTINGTHESTATEOFAWINDOWSIMAGE"></span>Ermitteln des Status eines Windows-Abbilds


Sysprep können Sie um den Status des Windows-Abbild zu identifizieren. D. h., können Sie bestimmen, ob das Abbild um zu überwachenden Modus oder OOBE gestartet wird oder wenn das Bild noch im Installationsprozess ist. Weitere Informationen finden Sie unter [Windows Setupvorgang Installation](windows-setup-installation-process.md).

## <a name="span-idsyspreplogfilesspanspan-idsyspreplogfilesspanspan-idsyspreplogfilesspansysprep-log-files"></a><span id="SysprepLogFiles"></span><span id="syspreplogfiles"></span><span id="SYSPREPLOGFILES"></span>Sysprep-Protokolldateien


Das Tool **Sysprep** protokolliert Windows Setup Aktionen in unterschiedlichen Verzeichnissen, je nach den Konfigurationsdurchlauf. Da die Konfiguration [verallgemeinern](generalize.md) Durchlauf bestimmte Windows Setup-Protokolldateien gelöscht werden, verallgemeinern-Protokolle und die **Sysprep** Aktionen außerhalb der standardmäßigen Windows-Setup-Protokolldateien. In der folgenden Tabelle zeigt anderes Protokoll Speicherorte, die **Sysprep** verwendet wird.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Protokollpfad</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Verallgemeinern</strong></p></td>
<td align="left"><p><strong>%WINDIR%\System32\Sysprep\Panther</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Specialize</strong></p></td>
<td align="left"><p><strong>%WINDIR%\Panther\</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Unbeaufsichtigte Installation von Windows-Aktionen</p></td>
<td align="left"><p><strong>%WINDIR%\Panther\Unattendgc</strong></p></td>
</tr>
</tbody>
</table>

 

Weitere Informationen finden Sie unter [Bereitstellung Problembehandlung und Protokolldateien](deployment-troubleshooting-and-log-files.md).

## <a name="span-idcreatingandusingsysprepprovidersspanspan-idcreatingandusingsysprepprovidersspanspan-idcreatingandusingsysprepprovidersspancreating-and-using-sysprep-providers"></a><span id="CreatingAndUsingSysprepProviders"></span><span id="creatingandusingsysprepproviders"></span><span id="CREATINGANDUSINGSYSPREPPROVIDERS"></span>Erstellen und Verwenden von Sysprep-Anbieter


Unabhängige Softwarehersteller (ISVs) und unabhängige Hardwareanbieter (unabhängigen Hardwareanbietern) können **Sysprep** Anbieter erstellen, die ihre Anwendungen zur Unterstützung von Imaging und Bereitstellung Szenarien zu ermöglichen. Wenn eine Anwendung derzeit nicht unterstützt verallgemeinern Vorgänge mit dem Tool **Sysprep** , können Sie einen Anbieter, der entfernt alle Software und Hardware-spezifischen Informationen aus der Anwendung erstellen.

Um einen Anbieter **Sysprep** zu erstellen, müssen Sie Folgendes ausführen:

1.  Bestimmen Sie, welche Konfiguration übergeben (**Cleanup**, **verallgemeinern**oder **specialize**) Ihre Sysprep-Anbieter-Adressen.

2.  Erstellen Sie den entsprechenden Einstiegspunkt für Ihr **Sysprep** -Anbieter, basierend auf Ihrer Wahl von Konfiguration übergeben.

3.  Registrieren des **Sysprep** -Anbieters für die Verwendung durch das **Sysprep** -Tool.

4.  Testen des Anbieters **Sysprep** , um zu überprüfen, dass der Provider ordnungsgemäß funktioniert. Stellen Sie sicher, dass Sie die Protokolldateien für Warnungen und Fehler überprüfen.

Weitere Informationen zu **Sysprep** Anbietern finden Sie im [System Preparation (Sysprep) Tool Anbieter Developer's Guide](http://go.microsoft.com/fwlink/?LinkId=205568).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Sysprep (Vorbereitung System)](sysprep--system-preparation--overview.md)

[Sysprep-Befehlszeilenoptionen](sysprep-command-line-options.md)

[Sysprep (verallgemeinern) einer Windows-installation](sysprep--generalize--a-windows-installation.md)

[Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md)

[Verwenden Sie Antwortdateien mit Sysprep](use-answer-files-with-sysprep.md)

 

 






