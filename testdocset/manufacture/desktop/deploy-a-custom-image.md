---
author: Justinha
Description: Bereitstellen eines benutzerdefinierten Abbilds
ms.assetid: 7eb6bc78-d1ce-42f2-bf1a-b34c4b14ed66
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen eines benutzerdefinierten Abbilds
ms.openlocfilehash: 9d3b1da2ee4abf32c25640a358c1b5745a807a83
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-a-custom-image"></a>Bereitstellen eines benutzerdefinierten Abbilds


In diesem Thema erstellen Sie eine Referenzinstallation, ein Abbild der Installation und führen Sie erneut aus Windows® Setup mit einer Antwortdatei, die auf das benutzerdefinierte Abbild verweist. Bereitstellen eines benutzerdefinierten Abbilds mithilfe von Windows Setup bietet verschiedene Vorteile gegenüber dem Anwenden der Schwelle, die ein Image Capture-Tool verwenden.

Setup unterstützt die folgenden:

-   Anwenden einer anderen Antwortdatei für zusätzliche erforderliche Anpassungen vor während der Bereitstellung.

-   Neukonfigurieren der Datenträgerkonfiguration.

-   Hinzufügen von zusätzlichen Treiber.

-   Ersetzen einen Product Key ein.

-   Auswählen einer anderen Sprache installieren.

-   Auswählen aus einer Liste von Bildern für die Installation, wenn Ihre Bilddatei mehrere Bilder enthält.

-   An ein anderes Laufwerksspeicherort zu installieren.

-   Aktualisieren einer vorhandenen Windows-Installation.

-   Konfigurieren des Computers auf Dual-Boot-Betriebssysteme.

-   Sicherstellen, dass die Hardware Windows 8 unterstützen kann.

Es gibt einige Einschränkungen auf ein benutzerdefiniertes Bild mithilfe von Windows Setup installieren. Weitere Informationen finden Sie unter [Windows-Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md).

In diesem Thema:

-   [Kopieren der Quelldateien für die Windows Produkt-DVD in eine Netzwerkfreigabe](#bkmk-1)

-   [Erstellen einer master-Installations](#bkmk-2)

-   [Ein Abbild der installation](#bkmk-3)

-   [Erstellen einer benutzerdefinierten Antwortdatei](#bkmk-4)

-   [Bereitstellen des Abbilds mithilfe von Windows Setup](#bkmk-5)

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Referenzcomputer. Ein Referenzcomputer ist jeder Computer, auf dem Windows Assessment and Deployment Kit (Windows ADK) Tools installiert ist.

-   Eine Windows 8-Produkt-DVD.

-   Ein Master-Shape Computer, auf dem Sie installieren und Ihr benutzerdefinierte Abbild aufzeichnen.

-   Startbare Windows PE-Medium. Es gibt mehrere Typen von Windows PE-Medien, die Sie erstellen können. Weitere Informationen zu diesen Optionen finden Sie unter [Windows PE für Windows 10](winpe-intro.md).

-   Zugriff auf eine Netzwerkfreigabe, in dem benutzerdefinierte Bild und Windows-Quelldateien gespeichert.

## <a name="span-idbkmk1spanspan-idbkmk1spanstep-1-copy-the-windows-product-dvd-source-files-to-a-network-share"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Schritt 1: Kopieren Sie die Quelldateien für Windows-Produkt-DVD in eine Netzwerkfreigabe


Kopieren Sie auf dem Referenzcomputer den gesamten Inhalt des Windows-Produkt-DVD in eine Netzwerkfreigabe. Beispiel:

``` syntax
net use N: \\server\share\
xcopy D: N:\WindowsDVD\ /s
```

D: ist das DVD-ROM-Laufwerk, auf dem lokalen Computer.

## <a name="span-idbkmk2spanspan-idbkmk2spanstep-2-create-a-master-installation"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>Schritt 2: Erstellen einer Master-Shape Installations


1.  Erstellen einer Master-Shape Installations mithilfe einer der folgenden Methoden:

    -   [Starten Sie von einer DVD](boot-from-a-dvd.md)

    -   [Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

2.  Nachdem die Installation abgeschlossen ist, müssen Sie den Computer herunterzufahren.

## <a name="span-idbkmk3spanspan-idbkmk3spanstep-3-capture-an-image-of-the-installation"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>Schritt 3: Ein Abbild der installation


In diesem Schritt erstellen Sie ein Abbild der Installation Verweis mithilfe der Deployment Image Servicing und Verwaltungstool (**DISM**) und dann das benutzerdefinierte Bild auf einer Netzwerkfreigabe speichern.

1.  Starten des Referenzcomputers mit Ihrer startbare Windows PE-Medium.

2.  An einer Eingabeaufforderung ein Abbild der Installation. Sie geben einen Namen und eine Beschreibung als Teil Ihrer abbildaufzeichnung an. Alle Werte werden von Setup Windows benötigt. Wenn diese Werte in eine WIM-Datei nicht enthalten ist, wird das Bild nicht ordnungsgemäß installiert. Beispiel:

    ``` syntax
    Dism /Capture-Image /ImageFile:C:\myimage.wim /CaptureDir:c:\ /Compress:fast /CheckIntegrity /ImageName:"x86_Ultimate" /ImageDescription:"x86 Ultimate Compressed"
    ```

3.  Ersetzen Sie die Standard-Install.wim auf der Netzwerkfreigabe mit Ihrer benutzerdefinierten Bild. Das Bild muss Install.wim aufgerufen werden. Beispiel:

    ``` syntax
    net use N: \\server\share\
    copy C:\myimage.wim N:\WindowsDVD\sources\install.wim
    ```

    Falls erforderlich, geben Sie für den entsprechenden Netzwerkzugriff Anmeldeinformationen für das Netzwerk.

Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## <a name="span-idbkmk4spanspan-idbkmk4spanstep-4-create-a-custom-answer-file"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>Schritt 4: Erstellen einer benutzerdefinierten Antwortdatei


In diesem Schritt erstellen Sie eine Antwortdatei, die auf das benutzerdefinierte Abbild verweist. Dieser Schritt wird davon ausgegangen, dass Sie bereits eine Antwortdatei erstellt haben und einen Katalog arbeiten.

1.  Öffnen Sie auf dem Referenzcomputer **Windows System Image Manager**.

2.  Klicken Sie im Menü **Datei** auf **Neue Antwortdatei**.

3.  Klicken Sie im **Windows-Abbild** von Windows SIM erweitern Sie zum Anzeigen der verfügbaren Einstellungen **Komponenten** .

4.  Fügen Sie die folgenden Komponenten zu Ihrer Antwortdatei mithilfe der rechten Maustaste auf die Komponente auswählen und dann auf die entsprechende Konfiguration übergeben.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Komponente</th>
    <th align="left">Konfigurationsphasen</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\CreatePartitions\ CreatePartition</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\ModifyPartitions\ ModifyPartition</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\ImageInstall\OSImage\InstallTo</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    </tbody>
    </table>

    **Hinweis**  
    Erweitern Sie die Komponentenliste, bis Sie sehen, dass die niedrigste Einstellung in der vorherigen Tabelle aufgeführt, und fügen Sie der Antwortdatei diese Einstellung. Diese Tastenkombination wird die Einstellung zusammen mit allen übergeordneten Einstellungen der Antwortdatei in einem Schritt hinzufügen.

5.  Alle Einstellungen, die Sie hinzugefügt haben, muss im Bereich **Antwortdatei** angezeigt. Wählen Sie aus, und konfigurieren Sie jede Einstellung wie in der folgenden Tabelle angegeben.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Komponente</th>
    <th align="left">Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>WillShowUI = OnError</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>DiskID = 0
    WillWipeDisk = true</code></pre></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\CreatePartitions\CreatePartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = false
    Order = 1
    Size = 300</code></pre>
    <pre class="syntax" space="preserve"><code>Type = Primary</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\CreatePartitions\CreatePartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = true
    Order = 2</code></pre>
    <pre class="syntax" space="preserve"><code>Type = Primary</code></pre></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\ModifyPartitions\ModifyPartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Active = true
    Extend = false
    Format = NTFS
    Label = System
    Letter = S
    Order = 1
    PartitionID = 1</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft-Windows-Setup\DiskConfiguration\Disk\ModifyPartitions\ModifyPartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = false
    Format = NTFS
    Label = Windows
    Letter = C
    Order = 2
    PartitionID = 2</code></pre>
    <p></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft-Windows-Setup\ImageInstall\OSImage\</ starken ></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>WillShowUI = OnError</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft-Windows-Setup\ImageInstall\OSImage\InstallTo</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>DiskID = 0
    PartitionID = 2</code></pre></td>
    </tr>
    </tbody>
    </table>

6.  Kopieren Sie die Antwortdatei an einem Speicherort im Netzwerk, in einem Eingabeaufforderungsfenster. Beispiel:

    ``` syntax
    net use N: \\server\share\
    md N:\AnswerFiles
    copy C:\deploy_unattend.xml N:\AnswerFiles\
    ```

    Falls erforderlich, geben Sie für den entsprechenden Netzwerkzugriff Anmeldeinformationen für das Netzwerk.

## <a name="span-idbkmk5spanspan-idbkmk5spanstep-5-deploy-the-image-by-using-windows-setup"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>Schritt 5: Bereitstellen des Abbilds mithilfe von Windows Setup


In diesem Schritt wird das benutzerdefinierte Abbild von einer Netzwerkfreigabe auf einem Zielcomputer bereitgestellt.

1.  Starten Sie den Zielcomputer mithilfe des startbaren Windows PE-Mediums.

2.  Verbinden mit der Netzwerkfreigabe, die im angegebenen [Schritt 4: erstellen eine benutzerdefinierten Antwortdatei](#bkmk-4), und führen Sie Setup mit Ihrer Antwortdatei. Beispiel:

    ``` syntax
    net use N: \\server\share
    N:\WindowsDVD\setup /unattend:N:\AnswerFiles\deploy_unattend.xml
    ```

    Falls erforderlich, geben Sie für den entsprechenden Netzwerkzugriff Anmeldeinformationen für das Netzwerk.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte


Sie können die Antwortdatei so zusätzliche Optionen gehören weiter anpassen. Sie können auch eine Bereitstellung DVDs erstellen, die den gleichen Inhalt enthält, den auf der Netzwerkfreigabe enthalten. Eine einzelne Bereitstellung DVD bietet eine portable Installation-Lösung, die keine Netzwerk- oder zusätzlichen Ressourcen benötigt. Der Prozess umfasst eine Konfiguration festgelegt und alle Quelldateien auf einer einzigen DVD Neuaufnahme erstellen.

**Wichtige**  
DVD-Medien, die Sie erstellen ist ausschließlich für die interne Bereitstellung Verwendung. Sie können keine Datenträger verteilen.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Starten Sie von einer DVD](boot-from-a-dvd.md)

[Verwenden Sie einen Konfigurationssatz mit Windows-Setup](use-a-configuration-set-with-windows-setup.md)

[Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md)

 

 






