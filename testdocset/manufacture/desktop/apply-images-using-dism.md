---
author: Justinha
Description: Anwenden von Abbildern mithilfe von DISM
ms.assetid: f9e0727d-a210-4efa-85af-5b222c53624e
MSHAttr: PreferredLib:/library/windows/hardware
title: Anwenden von Abbildern mithilfe von DISM
ms.openlocfilehash: 111e495f5841895e85cbc9d85763e4b6cdcee3a3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="apply-images-using-dism"></a>Anwenden von Abbildern mithilfe von DISM


In diesem Thema wird beschrieben, wie Bilder, die auf Ihrem Computer Verweis auf eine oder mehrere Zielcomputer mit dem Deployment Image Servicing Management (DISM) Tool und erfasst bereitstellen. Weitere Informationen zum Konfigurieren der empfohlenen Partitionen finden Sie unter [Configure UEFI/GPT-Based Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md) und [Configure BIOS/MBR-Based Hard-Partitionen](configure-biosmbr-based-hard-drive-partitions.md).

## <a name="span-idbootusingwindowspespanspan-idbootusingwindowspespanspan-idbootusingwindowspespanapply-a-windows-image"></a><span id="BootUsingWindowsPE"></span><span id="bootusingwindowspe"></span><span id="BOOTUSINGWINDOWSPE"></span>Anwenden eines Windows-Abbilds


Auf dem Zielcomputer erstellen Sie eine Struktur für die Partitionen, auf dem Sie Ihre Bilder anwenden. Die Partitionsstruktur auf dem Zielcomputer muss die Partitionsstruktur des Referenzcomputers übereinstimmen.

Wenn Sie ein Bild auf einem Datenträger mit einer vorhandenen Installation von Windows anwenden möchten, können Dateien aus der vorherigen Installation nicht gelöscht werden. Formatieren Sie die Lautstärke mit einem Tool wie DiskPart vor dem das neue Bild zuweisen aus.

**Partitionieren die Festplatte und Anwenden der Schwelle**

1.  Starten Sie den Zielcomputer Windows PE. Weitere Informationen finden Sie unter [Technische Referenz zu Windows PE (Windows PE)](winpe-intro.md).

2.  Eine Verbindung mit der Verteilung Netzwerkfreigabe, in dem das Windows-Abbild gespeichert ist. Beispielsweise können Sie den Befehl **net Use** dazu verwenden:

    ``` syntax
    net use n: \\server\share
    ```

    Geben Sie bei Aufforderung die Anmeldeinformationen für das Netzwerk.

3.  Geben Sie an der Eingabeaufforderung Windows PE `diskpart` an das **Diskpart** -Tool zu starten.

4.  Erstellen Sie mithilfe von **Diskpart** die Partitionsstruktur. Beispiel:

    ``` syntax
    select disk 0
    clean
    create partition primary size=3000 id=27
    format quick fs=ntfs label="Recovery"
    assign letter="R"
    create partition primary size=300
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    create partition primary
    format quick fs=ntfs label="Windows"
    assign letter="C"
    exit
    ```

    In diesem Beispiel wird vorübergehend weist diese Laufwerkbuchstaben: Windows = C, System = S und Recovery = R. Wenn Sie mit unformatierten Festplatten auf PCs bereitstellen, ändern Sie den Windows-Laufwerkbuchstaben in eines Briefs an, die am Ende der Alphabet wie W verwenden, um Laufwerk Buchstaben Konflikte zu vermeiden. Verwenden Sie nicht X, da diese Laufwerkbuchstaben für Windows PE reserviert ist. Nach dem Neustart des PCs-Option die Windows-Partition wird den Buchstaben C zugewiesen, und die anderen Partitionen nicht Laufwerkbuchstaben erhalten.

    Beispiele für empfohlene Partitionsstrukturen finden Sie unter [Configure BIOS/MBR-Based Hard Drive Partitionen](configure-biosmbr-based-hard-drive-partitions.md) und [Configure UEFI/GPT-Based Hard Drive-Partitionen](configure-uefigpt-based-hard-drive-partitions.md).

    **Hinweis**  
    Sie können diese Aufgabe mit Automatisieren der `diskpart /s <script>` Befehl. Weitere Informationen finden Sie unter [Diskpart Befehlssyntax Linie](http://go.microsoft.com/fwlink/?LinkId=128458).

     

5.  Verwenden Sie das Tool DISM, um Bilder in Ihrem Windows-Partition anzuwenden.

    Für jede Partition, dass Sie ein Bild, um die **DISM** **/apply-image** /imageFile ausführen anwenden: * &lt;Bild\_Datei&gt; * /index:*&lt;Index\_Anzahl&gt; * /ApplyDir:*&lt;Bild\_Pfad&gt; * Befehl.

    ``` syntax
    Dism /apply-image /imagefile:N:\Images\my-windows-partition.wim /index:1 /ApplyDir:C:\
    ```

    **Hinweis**  Wenn Sie der Befehl DISM /Apply-Image ein Fehler auftritt, stellen Sie sicher, dass Sie eine [unterstützte Version von DISM](dism-supported-platforms.md) für das Windows-Abbild verwenden. Um ein Windows-10-Bild anwenden möchten, benötigen Sie beispielsweise die Windows-10-Version von DISM eingetragenen.

     

6.  Zum Einrichten einer einfachen Systempartition können Sie BCDboot-Tool verwenden, um einen einfachen Satz von Systemdateien auf eine Systempartition zu kopieren. Diese Dateien enthalten Boot Daten (BCD) Konfigurationsinformationen, die zum Starten von Windows verwendet wird:

    Verwenden Sie das Tool BCDboot aus, um allgemeine Partition Systemdateien kopieren und Boot-Konfigurationsdaten nicht initialisiert werden:

    ``` syntax
    C:\Windows\System32\bcdboot C:\Windows /l en-US
    ```

    Weitere Informationen zum BCDboot-Tool finden Sie unter [BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md).

    **Hinweis**  
    Sie können die Systempartition einrichten, durch das Anwenden eines Abbilds. Verwenden Sie den Befehl **DISM** **/apply-image** . Beispiel:

    `Dism /apply-image /imagefile:N:\Images\my-system-partition.wim /index:1 /ApplyDir:S:\`

     

Sie können die Computer einrichten, das Windows-Abbild im Fall eines Systemausfalls neu installieren. Weitere Informationen finden Sie unter [Technische Referenz zu Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md).

**Wichtige**  
Microsoft Reserved-Partitionen (MSR) und erweiterte Partitionen werden vom Computer verwaltet. Wenden Sie ein Bild nicht auf diese Partitionen.

 

Sie können im Überwachungsmodus So testen Sie den Computer und zusätzliche erforderliche Anpassungen vor ausführen, bevor Sie es an Ihre Endbenutzer liefern verwenden. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

Führen Sie einige Anpassungen am Computer an, ohne es zu starten. Weitere Informationen finden Sie unter [Service ein Windows-Abbild angewendet](service-an-applied-windows-image.md).

**Hinweis**  
Wenn die Fehlermeldung angezeigt: **Bootmgr nicht gefunden. Drücken Sie STRG + ALT + ENTF**, darauf hin, dass Windows die Boot-Informationen in der aktiven Partition identifizieren kann. Wenn Sie diese Fehlermeldung angezeigt werden, überprüfen Sie Folgendes:

-   Verwenden Sie das Tool DiskPart, um zu überprüfen, um sicherzustellen, dass die Systempartition auf aktiv eingestellt ist.

-   Stellen Sie sicher, dass aktive Partition Systemdateien enthält.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Aufzeichnen von Abbildern von Festplattenpartitionen mithilfe von DISM](capture-images-of-hard-disk-partitions-using-dism.md)

[Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Anwenden von Bildern mithilfe eines Skripts](http://go.microsoft.com/fwlink/?LinkId=618399)

 

 






