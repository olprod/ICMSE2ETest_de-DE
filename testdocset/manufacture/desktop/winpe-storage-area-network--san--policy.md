---
author: Justinha
Description: 'Windows PE: Storage Area Network (SAN) Richtlinie'
ms.assetid: fb9b42b2-432e-4c88-9973-4d9d832645df
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Storage Area Network (SAN) Richtlinie'
ms.openlocfilehash: efd546b56510f7bc295b6b758c2bcdd286de3894
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-storage-area-network-san-policy"></a>Windows PE: Storage Area Network (SAN) Richtlinie


Storage Area Network (SAN) Funktionalität ermöglicht es einem Computer, Datenträger und andere Speichermedien automatisch von anderen Computern bereitzustellen. Konfigurieren der SAN-Richtlinie für ein Abbild Windows Vorinstallation Environment (Windows PE), können Sie steuern, ob Festplatten automatisch bereitgestellt werden und welche Festplatten bereitgestellt werden können. Sie können auch Datenträger nicht automatisch bereitstellen, um die Richtlinie deaktivieren.

## <a name="span-idconfiguringthesanpolicyonawindowspeimagespanspan-idconfiguringthesanpolicyonawindowspeimagespanspan-idconfiguringthesanpolicyonawindowspeimagespanconfiguring-the-san-policy-on-a-windows-pe-image"></a><span id="Configuring_the_SAN_policy_on_a_Windows_PE_image"></span><span id="configuring_the_san_policy_on_a_windows_pe_image"></span><span id="CONFIGURING_THE_SAN_POLICY_ON_A_WINDOWS_PE_IMAGE"></span>Konfigurieren der SAN-Richtlinie auf einem Windows PE-Abbild


Für Windows PE-Bildern, die in dem Windows Assessment and Deployment Kit (Windows ADK) verfügbar sind, ist die Standardrichtlinie SAN verfügbare Festplatten automatisch bereitzustellen. Jedoch weist die SAN-Umgebung viele verfügbare Datenträger, wird diese automatisch eingebunden möglicherweise reduzieren die Leistung von Windows PE. Container-ID bestimmt den externen und internen Datenträgerstatus. Wenn Container-ID eines Datenträgers die Stamm-Container-ID identisch ist, ist der Datenträger interne. Andernfalls ist ihn extern. Die Setsanpolicy.cmd-Datei in den Pfad des Windows PE-Tools können Sie um die SAN-Richtlinie auf einem Windows PE-Abbild zu konfigurieren.

**Konfigurieren die SAN-Richtlinie auf einem Windows PE-Abbild**

1.  Stellen Sie das Windows PE-Abbild an einem verfügbaren Bereitstellungspunkt. Beispiel:

    ``` syntax
    Dism /mount-image /imagefile:C:\winpe_x86\ISO\sources\boot.wim /index:<image_index> /mountdir:C:\winpe_x86\mount
    ```

    wobei * &lt;Bild\_Index&gt; * ist die Anzahl der ausgewählten Bilds in der WIM-Datei.

2.  Führen Sie den Befehl **Setsanpolicy** . Beispiel:

    ``` syntax
    Setsanpolicy.cmd <image_path> <policy_number>
    ```

    wobei * &lt;Bild\_Pfad&gt; * ist der Pfad des ein bereitgestelltes Windows PE-Abbild und * &lt;Richtlinie\_Anzahl&gt; * ist die Anzahl der SAN-Richtlinie.

    Diese Werte sind gültig * &lt;Richtlinie\_Anzahl&gt; * Werte:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Anzahl der SAN-Richtlinie</th>
    <th align="left">Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>1</p></td>
    <td align="left"><p>Alle verfügbaren Speichergeräten bindet.</p>
    <p>Dies ist der Standardwert.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>2</p></td>
    <td align="left"><p>Alle Speichergeräten mit Ausnahme der auf einem freigegebenen Bus bindet.</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>3</p></td>
    <td align="left"><p>Speichergeräten wird nicht eingebunden werden.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>4</p></td>
    <td align="left"><p>Neue Features für Windows 8. Interne Datenträger offline ist.</p>
    <div class="alert">
    <strong>Hinweis</strong>  
    <p>Alle externen Datenträger und der Startdatenträger sind online.</p>
    </div>
    <div>
     
    </div></td>
    </tr>
    </tbody>
    </table>

    In diesem Beispiel wird das Konfigurieren der SAN-Richtlinie auf einem Windows PE-Abbild bereitstellen alle Datenträger mit Ausnahme der Datenträger auf einem freigegebenen Bus veranschaulicht:

        Setsanpolicy C:\winpe_x86\mount <2>

    wobei * &lt;2&gt; * ist die Anzahl der SAN-Richtlinie, die alle Speichergerät mit Ausnahme der auf einem freigegebenen Bus bindet.

3.  Heben Sie die Bereitstellung des Bilds, und die Änderungen zu übernehmen. Beispiel:

    ``` syntax
    Dism /unmount-image /mountdir:C:\winpe_x86\mount /commit
    ```

## <a name="span-idconfiguringthesanpolicyonawindowsimagespanspan-idconfiguringthesanpolicyonawindowsimagespanspan-idconfiguringthesanpolicyonawindowsimagespanconfiguring-the-san-policy-on-a-windows-image"></a><span id="Configuring_the_SAN_Policy_on_a_Windows_Image"></span><span id="configuring_the_san_policy_on_a_windows_image"></span><span id="CONFIGURING_THE_SAN_POLICY_ON_A_WINDOWS_IMAGE"></span>Konfigurieren der SAN-Richtlinie auf einem Windows-Abbild


Sie können die SAN-Standardrichtlinie eines Windows-Abbilds mithilfe von Windows System Image Manager (Windows SIM) zum Anpassen der Komponente Microsoft-Windows-PartitionManager ändern. Verwenden Sie die `SanPolicy` Einstellung so konfigurieren Sie das Windows-Abbild während einer unbeaufsichtigten Installation.

**So konfigurieren Sie die SAN-Richtlinie mithilfe einer Antwortdatei**

1.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**, und wählen Sie dann **Windows System Image Manager**.

2.  Erstellen einer neuen Antwortdatei oder Aktualisieren einer vorhandenen Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085) und [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073).

3.  Klicken Sie im Menü **Einfügen** auf **RunSynchronous**.

4.  Wählen Sie die Konfiguration übergeben, wo Sie den Befehl installieren möchten. Dies kann die Konfigurationsdurchlauf [AuditUser](audituser.md) oder [OobeSystem](oobesystem.md) sein.

    **Hinweis**  
    Verwenden Sie nicht den Befehl **RunSynchronousNetsh Advfirewall** während der Konfiguration [specialize](specialize.md) übergeben.

    Das Dialogfeld **Synchronen Befehl erstellen** wird angezeigt.

5.  Geben Sie den Befehl **Netsh Advfirewall Firewall** So fügen sie die Antwortdatei hinzu, und klicken Sie dann auf **OK**.

    Weitere Informationen finden Sie unter der [Netzwerk-Shell (Netsh) technische Referenz zu](http://go.microsoft.com/fwlink/?LinkId=234733). Sie können Befehle Windows PowerShell® **Netsh** -Befehle konvertieren. Weitere Informationen finden Sie unter der [Netshell Powershell Konvertierung Guide](http://go.microsoft.com/fwlink/?LinkId=234734).

6.  Geben Sie im Eigenschaftenbereich **SynchronousCommand** , im Abschnitt **Einstellungen** neben der **Beschreibung**eine Beschreibung wie **Aktivieren Windows Messenger**.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Konfigurieren von Netzwerkeinstellungen in einer unbeaufsichtigten Installation](configure-network-settings-in-an-unattended-installation.md)

[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

 

 






