---
author: Justinha
Description: Sysprep (verallgemeinern) einer Windows-installation
ms.assetid: 455fa70e-6c13-45ae-ad4f-5d12e3b844e5
MSHAttr: PreferredLib:/library/windows/hardware
title: Sysprep (verallgemeinern) einer Windows-installation
ms.openlocfilehash: ee0e7a959ce04b56aedb3fdc8a2141acb71f71e9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-generalize-a-windows-installation"></a>Sysprep (verallgemeinern) einer Windows-installation


Verwenden Sie **Sysprep** , um eine Windows-Installation verallgemeinern. Um ein Windows-Abbild auf unterschiedliche PCs bereitzustellen, müssen Sie zuerst das Bild vorbereiten. Sie können entweder das System Vorbereitungstool (Sysprep) verwenden oder Sie können eine Einstellung angeben, in einer Antwortdatei So bereiten Sie das Bild als Teil einer unbeaufsichtigten Installation vor. Vorbereitung auf das Bild müssen Sie die Computer-spezifische Informationen aus dem Bild entfernen. Dieser Vorgang wird das Bild *verallgemeinern* bezeichnet.

In den meisten Bereitstellungsszenarios nicht mehr erforderlich, verwenden Sie die `SkipRearm` beantworten Datei-Einstellung, um die Aktivierung von Windows-Produkten Uhr zurückgesetzt, wenn Sie den Befehl **Sysprep** mehrmals auf einem Computer ausführen. Die `SkipRearm` Einstellung wird an der Windows-Lizenzierung Zustand verwendet. Wenn Sie eine Retail Product Key oder Volume License Product Product Key angeben, wird Windows automatisch aktiviert. Sie können den Befehl **Sysprep** bis 8 zusätzliche Zeiten auf ein einzelnes Windows Bild oben ausführen. Nach dem Ausführen von Sysprep 8 Zeiten, müssen Sie das Windows-Abbild neu erstellen. Weitere Informationen zu Windows-Komponenten und Einstellungen, die eine Antwortdatei hinzugefügt werden können, finden Sie unter der [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

**Vorsicht**  
Verwenden Sie den Windows Store nicht so aktualisieren Sie Ihre Windows Store-apps vor dem Ausführen **Sysprep / verallgemeinern**. **Sysprep** kann das Bild in diesem Szenario verallgemeinern. Dieses Problem betrifft auch die Windows Store-apps (beispielsweise E-Mail, Karten, Bing-Finance, Bing News und andere). Dies kann vorkommen, wenn Sie Ihre Installation im Überwachungsmodus als Administrator der integrierten anpassen oder ein bestimmtes Benutzerkonto verwenden. Die folgende Fehlermeldung angezeigt, in den Protokolldateien Sysprep (% WINDIR%\\System32\\Sysprep\\Panther):

`<package name> was installed for a user, but not provisioned for all users. This package will not function properly in the sysprep image.`

**Sysprep / verallgemeinern** erfordert, dass alle apps, die für alle Benutzer bereitgestellt werden. Jedoch beim Aktualisieren einer app aus dem Windows Store app wird nicht bereitgestellt und wird mit dem Benutzerkonto gebunden.

Statt Windows Store so aktualisieren Sie Ihre apps sollte Sideload Updates auf Ihre Line-of-Business-apps oder können Endbenutzer ihre apps mithilfe von Windows Store auf ihr Ziel PCs aktualisieren. In verwalteten Umgebungen Wenn Windows Store-Zugriff von einem IT-Administrator deaktiviert ist können nicht aktualisieren von Windows Store-apps Sie.

Weitere Informationen zu Sideloading Line-of-Business Windows Store-apps finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md) und [Anpassen der Startseite](customize-the-start-screen.md).

 

Wenn Ihr Server Remote Authentication Dial-In User Service (RADIUS)-Clients oder remote RADIUS-Server-Gruppen, die in der Konfiguration (Network Policy Server, NPS) definierten verfügt, sollten Sie diese Informationen vor der Bereitstellung auf einem anderen Computer entfernen. Weitere Informationen finden Sie unter [Vorbereiten einer Network Policy Server (NPS) für Imaging](prepare-a-network-policy-server--nps--for-imaging.md).

In diesem Thema:

-   [Verallgemeinern ein Bild](#bkmk-1)

-   [Verallgemeinern einer virtuellen Festplatte](#bkmk-2)

## <a name="span-idbkmk1spanspan-idbkmk1spangeneralizing-an-image"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Verallgemeinern ein Bild


Wenn Sie ein Windows-Abbild verallgemeinern, verarbeitet Windows Setup Einstellungen im Durchgang Konfiguration [verallgemeinern](generalize.md) . Sie müssen den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** ausführen, selbst wenn der Computer und des Referenzcomputers die gleiche Hardwarekonfiguration haben. Die **Sysprep / verallgemeinern** Befehl entfernt eindeutigen Informationen von einer Windows-Installation, damit Sie das Abbild auf einem anderen Computer sicher wiederverwenden können. Aber Sie können während der verallgemeinern Konfigurationsdurchlauf Treiber beibehalten.

**Wichtige**  
Wenn Sie Ihre Referenz-Computer einrichten, installiert Windows Setup Treiber für alle erkannten Geräte. Standardmäßig entfernt Windows Setup diese Treiber, wenn Sie das System verallgemeinern. Wenn Sie das Bild auf Computern, die die gleiche Hardware und Geräte verfügen bereitstellen, sollten Sie die Windows-Setup diese dieselben Treiber neu installieren. Um diese Treiber Verallgemeinerung des Systems auf dem Computer zu belassen, legen Sie die Microsoft Windows-PnPSysprep | `PersistAllDeviceInstalls` auf **true**festlegen. Weitere Informationen zu **Sysprep**-verwandte Windows-Komponenten, die Sie zu einer Antwortdatei hinzufügen können finden Sie in der [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

 

Windows ersetzt nur die Computer Sicherheits-ID (SID) auf dem Betriebssystem Datenträger, beim Ausführen von **Sysprep**. Wenn **Sysprep** Schwelle verallgemeinert, verallgemeinert er nur die allgemeine Partition. So weist auf ein einzelner Computer mehrere Betriebssysteme, müssen Sie **Sysprep** auf jedes Bild einzeln ausführen.

**Um Ihr Bild verallgemeinern**

1.  Fügen Sie eine der folgenden Einstellungen zu Ihrer Antwortdatei hinzu:

    -   Verwenden Sie das Microsoft-Windows-Bereitstellung | `Generalize` Einstellung. Legen Sie `Mode` **OOBE** oder **Überwachung**, und einen Satz `ForceShutdownNow` auf **true fest**. Der Computer automatisch verallgemeinert das Bild und beendet wird.

        \endash oder \endash

    -   Hinzufügen der Microsoft-Windows-Deployment | `Reseal` auf [der Konfigurationsphase](oobesystem.md) festlegen. Legen Sie `Mode` zu **überwachende**. Nachdem der Computer im Überwachungsmodus startet und das Fenster **Systemvorbereitungstool zeigt** , verwenden Sie eine der folgenden Methoden:

        -   Klicken Sie im Fenster **Systemvorbereitungstool** auf **verallgemeinern**, klicken Sie auf **Herunterfahren**, und klicken Sie dann auf **OK**. Der Computer verallgemeinert das Bild und beendet wird.

            \endash oder \endash

        -   Schließen Sie das Fenster **Systemvorbereitungstool** , öffnen Sie ein Eingabeaufforderungsfenster als Administrator, und ziehen Sie dann auf die **%windir%\\system32\\Sysprep** Directory. Verwenden Sie den Befehl **Sysprep** zusammen mit der **/ verallgemeinern** **Shutdown** **und/Oobe** -Optionen. Beispiel:

            ``` syntax
            Sysprep /generalize /shutdown /oobe
            ```

            Der Computer verallgemeinert das Bild und beendet wird.

2.  Nach dem Herunterfahren des Computers, verwenden Sie ein Tool zum Aufzeichnen von Abbildern, um das Abbild aufzuzeichnen. Sie können den Befehl **Dism /capture-image** im Deployment Image Servicing and Management (**DISM**) Tool für diesen Zweck.

3.  Bereitstellen von dieses Bild in eine Referenz-Computer. Beim Starten des Referenzcomputers, wird es der Out-Of-Box-Experience (OOBE) angezeigt.

Weitere Informationen finden Sie unter [Einstellungen für OOBE automatisieren](settings-for-automating-oobe.md) und[Oobe.xml konfigurieren](configure-oobexml.md).

Wenn Sie zusätzliche erforderliche Anpassungen vor haben, können Sie im Überwachungsmodus manuell eingeben und Anpassungen vornehmen, bevor Sie verallgemeinern und des Abbilds bereitstellen.

**Optional: Überwachungsmodus eingeben verallgemeinern manuell, bevor Sie Ihr Bild**

1.  Drücken Sie STRG + UMSCHALT + F3, auf dem Bildschirm OOBE. Wird den Computer im Überwachungsmodus neu gestartet, und das Fenster **Systemvorbereitungstool** wird angezeigt.

    **Vorsicht**  
    Die Tastenkombination STRG + UMSCHALT + F3 umgehen nicht alle Teile des Prozesses OOBE wie Ausführen von Skripts und Anwenden von Antwortdatei Einstellungen in [der Konfigurationsphase](oobesystem.md) .

     

2.  Fügen Sie die Anpassungen, die Sie einschließen möchten.

3.  Klicken Sie im **Systemvorbereitungstool** auf **verallgemeinern**, klicken Sie auf **Herunterfahren**und klicken Sie dann auf **OK**. Der Computer verallgemeinert das Bild und beendet wird.

     \endash oder \endash

    Schließen Sie das Fenster **Systemvorbereitungstool** , öffnen Sie ein Eingabeaufforderungsfenster als Administrator, und ziehen Sie dann auf die **%windir%\\system32\\Sysprep** Directory. Verwenden Sie den Befehl **Sysprep** zusammen mit den Optionen **/ verallgemeinern**, **Shutdown** **und/Oobe** . Beispiel:

    ``` syntax
    Sysprep /generalize /shutdown /oobe
    ```

    Der Computer verallgemeinert das Bild und beendet wird.

4.  Nach dem Herunterfahren des Computers, verwenden Sie ein Tool zum Aufzeichnen von Abbildern, um das Bild zu erfassen. Sie können den Befehl **Dism /capture-image** im Tool **DISM** für diesen Zweck verwenden.

5.  Bereitstellen von dieses Bild in eine Referenz-Computer. Beim Starten des Referenzcomputers, wird es der OOBE angezeigt.

Weitere Informationen zum Überwachungsmodus finden Sie unter:

-   [Übersicht über Audit-Modus](audit-mode-overview.md)

-   [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

-   [Hinzufügen eines Treibers Online im Überwachungsmodus](add-a-driver-online-in-audit-mode.md)

-   [Aktivieren Sie und deaktivieren Sie des integrierten Administratorkontos](enable-and-disable-the-built-in-administrator-account.md)

## <a name="span-idbkmk2spanspan-idbkmk2spangeneralizing-a-virtual-hard-disk"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Verallgemeinern einer virtuellen Festplatte


**Sysprep** VM Modus können Sie eine virtuelle Festplatte verallgemeinern, die Sie als eine virtuelle Festplatte auf dem gleichen virtuellen Computer oder Hypervisor bereitstellen möchten. VM-Modus unterstützt eine schnelle Bereitstellung von virtuellen Computern. VM-Modus wird nur unterstützt, wenn Sie es aus innerhalb eines virtuellen Computers ausgeführt. Darüber hinaus ist VM-Modus nur über die Befehlszeile verfügbar. Sie können keine VM-Modus verwenden, zur Vorbereitung der Bereitstellung auf einem beliebigen Computer in einer virtuellen Festplatte.

**Um eine virtuelle Festplatte verallgemeinern**

1.  Öffnen Sie im Überwachungsmodus aktiviert, ein Eingabeaufforderungsfenster als Administrator, und ziehen Sie dann auf die **%windir%\\system32\\Sysprep** Directory.

2.  Verwenden Sie den Befehl **Sysprep** zusammen mit den Optionen **/ verallgemeinern**, **/ Oobe**und **/mode:vm** an. Beispiel:

    ``` syntax
    Sysprep /generalize /oobe /mode:vm
    ```

    Der Computer verallgemeinert VHD-Abbilds.

3.  Bereitstellen Sie allgemeine Übersicht über VHD-Abbilds auf demselben virtuellen Computer. Beim Neustart von den virtuellen Computer wird es der OOBE angezeigt.

Die gültigen VM-Modus nur zusätzlichen Optionen **sind/neu starten,** **Shutdown**und **/ Beenden**.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Sysprep-Prozess (Übersicht)](sysprep-process-overview.md)

[Sysprep-Befehlszeilenoptionen](sysprep-command-line-options.md)

[Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md)

[Arbeiten Sie mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md)

 

 






