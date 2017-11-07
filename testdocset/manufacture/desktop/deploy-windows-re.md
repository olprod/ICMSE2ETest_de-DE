---
author: Justinha
Description: Bereitstellen von Windows RE
ms.assetid: 93c71c50-b3f9-49f7-bf3a-32a412b048ed
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen von Windows RE
ms.openlocfilehash: 4bb8621b39ce915f6e75841f0ae74ad5f168ae00
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-re"></a>Bereitstellen von Windows RE


Verwenden Sie diese Schritte zum Bereitstellen von Windows® Recovery Environment (Windows RE) zu einem neuen Computer, Endbenutzer einen PC zu reparieren, tritt ein Systemfehler an.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Zum Ausführen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

-   Ein Zielcomputer, der wurde, konfiguriert mit einer Windows RE-Tools Partition und optional eine Recovery-Image-Partition. Weitere Informationen finden Sie unter [Capture und Anwenden von Windows, System, und Recovery-Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).
-   Optional: Passen Sie die Wiederherstellungsmedien an. Weitere Informationen finden Sie unter [Windows RE anpassen](customize-windows-re.md).
-   Optional: Passen Sie die Wiederherstellungsmedien zum Einschließen von benutzerdefinierten Tools. Weitere Informationen finden Sie unter [Hinzufügen ein benutzerdefiniertes Tool zum Menü Windows RE Boot Optionen](add-a-custom-tool-to-the-windows-re-boot-options-menu.md).

## <a name="span-iddeploywindowsrespanspan-iddeploywindowsrespanspan-iddeploywindowsrespanstep-1-deploy-windows-re"></a><span id="DeployWindowsRE"></span><span id="deploywindowsre"></span><span id="DEPLOYWINDOWSRE"></span>Schritt 1: Bereitstellen von Windows RE


1.  Erstellen Sie ein neues Verzeichnis, in der Windows RE-Tools Partition, und kopieren Sie Ihre Windows RE-Tools-Abbild (Winre.wim) in diesem Verzeichnis. Es folgen Beispiele basierend auf Ihren Typ Firmware:

    **UEFI:**

    ``` syntax
    mkdir T:\Recovery\WindowsRE

    xcopy /h W:\Windows\System32\Recovery\Winre.wim T:\Recovery\WindowsRE
    ```

    Dabei ist *T:* der Laufwerkbuchstabe Ihrer Windows RE-Tools Partition. Beispiel:

    **BIOS:**

    ``` syntax
    mkdir S:\Recovery\WindowsRE

    xcopy /h W:\Windows\System32\Recovery\Winre.wim S:\Recovery\WindowsRE
    ```

    Dabei ist *s* die Systempartition.

2.  Registrieren Sie Ihre Windows RE-Tools-Abbild:

    **UEFI:**

    ``` syntax
    C:\Windows\System32\Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows
    ```

    Dabei ist *T:* der Partition Windows RE-Tools.

    **BIOS**

    ``` syntax
    C:\Windows\System32\Reagentc /setreimage /path S:\Recovery\WindowsRE /target W:\Windows
    ```

    Dabei ist *s* die Systempartition.

3.  Optional: Wenn Sie ein benutzerdefiniertes Tool für Ihre Windows RE Boot-Abbild hinzugefügt haben, registrieren Sie es so, dass auf das Menü **Startoptionen** angezeigt wird:

    ``` syntax
    Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
    ```

    Weitere Informationen zum Hinzufügen eines benutzerdefinierten Tools finden Sie unter [Hinzufügen auf das Menü Windows RE Boot Optionen für ein benutzerdefiniertes Tool](add-a-custom-tool-to-the-windows-re-boot-options-menu.md).

4.  Optional: Konfigurieren einer Recovery-Taste (oder Schaltflächenkombination) um einen sekundären Boot-Pfad auszuführen, der Windows RE enthält. Weitere Informationen finden Sie unter [Hinzufügen einer Taste Wiederherstellung starten Windows RE](add-a-hardware-recovery-button-to-start-windows-re.md).

## <a name="span-idpreparescriptsspanspan-idpreparescriptsspanspan-idpreparescriptsspanstep-2-identify-the-recovery-partitions-and-hide-the-drive-letters"></a><span id="PrepareScripts"></span><span id="preparescripts"></span><span id="PREPARESCRIPTS"></span>Schritt 2: Identifizieren der Wiederherstellungspartitionen und die Laufwerkbuchstaben ausblenden


**Hinweis**   Wenn Sie Konfigurieren von Features für Windows 8-Editionen Drucktaste zurücksetzen möchten, diesen Abschnitt überspringen, und wechseln Sie zum Thema: [Bereitstellen von Features für Push-Button zurückgesetzt](deploy-push-button-reset-features.md).

 

Konfigurieren Sie die Partitionen als Recovery Partitionen und blenden Sie die Laufwerkbuchstaben aus, damit die Partitionen nicht gemeinsam Windows Menüs, z. B. Datei-Explorer angezeigt.

**Vorbereiten einer DiskPart-Skript zum Identifizieren der Wiederherstellungspartitionen und Laufwerkbuchstaben ausblenden**

1.  Erstellen Sie im Editor eine Textdatei, die enthält Befehle zum Identifizieren und die Wiederherstellungspartitionen ausblenden. Die folgenden Beispiele basieren auf den Typ der Firmware:

    **UEFI:**

    Verwenden Sie die ID: PARTITION\_MSFT\_WIEDERHERSTELLUNG\_GUID (de94bba4-06d1-4d40-a16a-bfd50179d6ac) zu definieren, die Partitionen als Wiederherstellungspartitionen.

    Verwenden Sie GPT-Attribute: 0x8000000000000001, um die Laufwerkbuchstaben auszublenden und die sie nach Bedarf, markieren Sie eine Kombination von zwei Attribute mit: GPT\_BASIC\_DATEN\_ATTRIBUT\_NO\_LAUFWERK\_BUCHSTABEN und GPT-\_ATTRIBUT\_PLATTFORM\_ERFORDERLICH.

    Weitere Informationen zu UEFI Festplatte Partition Attributen finden Sie unter [PARTITION\_INFORMATIONEN\_GPT-Struktur](http://go.microsoft.com/fwlink/?LinkId=240300).

    ``` syntax
    rem == HideRecoveryPartitions-UEFI.txt
    select disk 0
    select partition 1
    remove
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    gpt attributes=0x8000000000000001
    rem == If Push-button reset features are included, add the following commands:
    rem    select partition 5
    rem    remove
    rem    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    rem    gpt attributes=0x8000000000000001
    list volume
    ```

    **BIOS:**

    Verwenden Sie das Attribut: `id=27` zum Definieren der Systempartition, und verwenden Sie die `remove` Befehl aus, um den Laufwerkbuchstaben entfernen.

    ``` syntax
    rem == HideRecoveryPartitions-BIOS.txt
    select disk 0
    select partition 3
    set id=27
    remove
    list volume
    exit
    ```

2.  Speichern Sie Ihre abgeschlossenen Datei entweder als E:\\Wiederherstellung\\HideRecoveryPartitions UEFI.txt oder E:\\Wiederherstellung\\HideRecoveryPartitions-BIOS.txt basierend auf Ihrer Firmware-Typ.

**Identifizieren und die Laufwerkbuchstaben ausblenden**

-   Führen Sie das Diskpart-Skript zum Identifizieren und die Wiederherstellungspartitionen ausblenden:

    ``` syntax
    Diskpart /s E:\Recovery\HideRecoveryPartitions-<firmware>.txt
    ```

    Wobei * &lt;Firmware&gt; * UEFI oder BIOS ist.

**Stellen Sie sicher, dass die Windows RE-Konfiguration ordnungsgemäß festgelegt ist**

-   Ein administrative Eingabeaufforderungsfenster zu öffnen.

    Überprüfen Sie die Windows RE-Informationen ein:

    ``` syntax
    reagentc /info
    ```

    Überprüfen Sie Folgendes:

    -   Windows RE-Status ist aktiviert.
    -   Windows RE-Speicherort befindet sich auf die richtige Partition.
    -   Der GUID BCD-Eintrag für WinRE ist identisch mit der WinRE GUID-Eintrag in der Datei: reagent.xml. Auf BIOS-basierten PCs, befindet sich auf der Systempartition an \\Wiederherstellung\\(GUID)\\. Auf UEFI-basierten PCs, befindet sich auf der Partition Windows RE-Tools an \\Wiederherstellung\\WindowsRE\\.
    -   WinRE befindet sich der \\Wiederherstellung\\WindowsRE-Verzeichnis

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Anpassen von Windows RE](customize-windows-re.md)

[Fügen Sie ein benutzerdefiniertes Tool an den Windows RE-Optionen Startmenü](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)

 

 






