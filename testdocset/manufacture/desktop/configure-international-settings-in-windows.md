---
author: Justinha
Description: Konfigurieren von internationalen Einstellungen in Windows
ms.assetid: 2ed4a22d-8cd1-49b8-8141-06ebbf26b24d
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren von internationalen Einstellungen in Windows
ms.openlocfilehash: 477da06f42bb60c5e16bd064cddb4666165df612
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-international-settings-in-windows"></a>Konfigurieren von internationalen Einstellungen in Windows


Sie können die Standardsprache, Gebietsschema und Tastatur Werte angeben, während der Bereitstellung oder nach der Installation von Windows. Sie können mithilfe der internationalen Moduls für Windows PowerShell, Windows Setup mit einer Antwortdatei oder mithilfe von Bereitstellung Imaging Wartung und Verwaltung (DISM) internationale Einstellungen konfigurieren.

Informationen zum Verwenden von DISM internationale Einstellungen in Schwelle Windows offline zu konfigurieren finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

**Wichtige**  
In Windows 10 unterstützt nicht die neuen Einstellungen in den Abschnitt Region und Sprache der Systemsteuerung die Befehlszeilentools intl.cpl. Für Windows 10 sollten mithilfe der International Windows PowerShell-Cmdlet-Einstellungen zum Anpassen von internationale Einstellungen zu automatisieren.

Darüber hinaus sollte Bereitstellung Imaging Wartung und Verwaltung (DISM) auch nur gegen Schwelle offline Windows verwendet werden. Windows-10 werden Sprachoptionen dynamisch basierend auf der Liste des Benutzers Sprache konfiguriert. Einstellungen, beispielsweise die Anzeigesprache, standardmäßige Eingabemethode und Gebietsschema des Benutzers können dynamisch Voreinstellungen des Benutzers für eine ausgeführte Windows-Installation zurückgesetzt. Verwenden Sie die Einstellungen der International PowerShell-Cmdlet die internationalen Einstellungen für eine ausgeführte Windows-Installation zu ändern.


## <a name="span-idpowershellspanspan-idpowershellspanspan-idpowershellspanconfigure-international-settings-by-using-winbows-powershell"></a><span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>Konfigurieren von internationalen Einstellungen mithilfe von Winbows-PowerShell


In Windows 10 können Sie den internationalen Einstellungen Windows PowerShell-Cmdlets zum Ändern der Sprache für eine ausgeführte Windows-Installation. 

1.  Öffnen Sie eine Windows PowerShell-Eingabeaufforderung.

3.  Zeigen Sie die Gebietsschemainformationen auf dem Computer mithilfe des folgenden Befehls:

    ``` syntax
    Get-WinSystemLocale
    ```

    Legen Sie das Gebietsschema für die Region und die gewünschte Sprache. Der folgende Befehl wird beispielsweise das Standardgebietsschema des Systems auf Japanisch (Japan):

    ``` syntax
    Set-WinSystemLocale ja-JP
    ```

    Eine vollständige Beschreibung dieser Cmdlets finden Sie unter [Get-WinSystemLocale](http://go.microsoft.com/fwlink/p/?linkid=242247) und [Set-WinSystemLocale](http://go.microsoft.com/fwlink/p/?linkid=242254). Weitere Informationen zum Verwenden von internationalen PowerShell Cmdlets finden Sie unter [Internationalen Einstellungen Cmdlets](http://go.microsoft.com/fwlink/p/?linkid=238265).

## <a name="span-idcontrolpanelspanspan-idcontrolpanelspanspan-idcontrolpanelspanconfigure-international-settings-by-using-control-panel"></a><span id="ControlPanel"></span><span id="controlpanel"></span><span id="CONTROLPANEL"></span>Konfigurieren der internationale Einstellungen mithilfe der Systemsteuerung

Für eine ausgeführte Windows-Installation können Sie der Systemsteuerung wählen Sie Sprachpakete und zusätzliche internationale Einstellungen konfigurieren.

1.  Klicken Sie auf der Startseite Geben Sie **Sprache**, und wählen Sie **eine Sprache hinzufügen**.

4.  Durchsuchen Sie oder suchen Sie nach der Sprache, die Sie installieren möchten. Beispielsweise **Katalanisch**wählen Sie aus, und wählen Sie dann auf **Hinzufügen**.

    Katalanisch wird nun als eines der Sprachen hinzugefügt.

5.  Klicken Sie im Bereich **Ändern Ihrer spracheinstellungen** wählen Sie **Optionen** neben der Sprache, die Sie hinzugefügt haben.

6.  Wenn ein Language Pack für Ihre Sprache verfügbar ist, wählen Sie **herunterladen und Installieren von Language Packs**.

7.  Wenn das Language Pack installiert ist, wird die Sprache für die Windows-Anzeigesprache verwenden als verfügbar angezeigt.

8.  Damit diese Sprache die Anzeigesprache wird, verschieben Sie es an den Anfang der Sprachenliste aus.

9.  Melden Sie sich ab und dann wieder anmelden Windows, damit die Änderung wirksam wird.

Viele zusätzliche Language Packs installieren und wirkt sich auf Datenträger Speicherplatz und Systemleistung. Insbesondere unterliegen Datenträger Speicherplatz und Systemleistung während der Wartung von Operationen, z. B. Service Pack-Installationen Aus diesem Grund wird empfohlen, dass Sie nur, wenn Sie planen, verwenden das Language Pack ein Language Pack auf Ihrem Computer hinzufügen.

Language Packs können auch mehrere Benutzer, die ein select distinct Anzeige Computersprachen freigeben. Beispielsweise kann einen Benutzer auswählen, dass finden in den Dialogfeldern, Menüs und sonstigen Text in Japanisch, während ein anderer Benutzer auswählen kann, um den gleichen Inhalt in französischer Sprache anzuzeigen.

## <a name="span-iddismspanspan-iddismspanconfigure-international-settings-by-using-dism"></a><span id="DISM"></span><span id="dism"></span>Konfigurieren von internationalen Einstellungen mithilfe von DISM


Bereitstellung Imaging Wartung und Verwaltung (DISM) können Sie ändern die internationalen Einstellungen für eine offline-Windows-Abbild

1.  Stellen Sie eine Windows-Abbild. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

2.  Rufen Sie die Language-Einstellungen, die im Windows-Abbild mit dem **Parameter/Get-Intl** konfiguriert sind. Zum Beispiel

    ``` syntax
    Dism /image:C:\mount\windows /Get-Intl
    ```

3.  Ändern Sie die Standardsprache, Gebietsschema und andere internationalen Einstellungen mithilfe des Parameters **/set-allInlt** .

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:fr-fr
    ```

Zusätzliche Parameter und andere Optionen finden Sie unter [DISM Sprachen und internationalen Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

## <a name="span-idanswerfilespanspan-idanswerfilespanspan-idanswerfilespanconfigure-international-settings-by-using-an-answer-file"></a><span id="AnswerFile"></span><span id="answerfile"></span><span id="ANSWERFILE"></span>Konfigurieren von internationalen Einstellungen mithilfe einer Antwortdatei


Sie können die internationale Einstellungen in einer Antwortdatei folgendermaßen konfigurieren:

-   Language Packs installiert sind, aus einer Verteilung Freigabe und Einstellungen konfiguriert sind, wird beim **WindowsPE** Konfiguration Durchlauf installiert.

    Unternehmen, die in der Regel eine mehrsprachige Edition von Windows bereitstellen erstellen Sie eine Antwortdatei, die während des **WindowsPE** Konfiguration Schritts internationale Einstellungen konfiguriert. Für die Bereitstellung in mehreren Sprachen können Language Packs in beide eine Verteilung Freigabe und das Bild vorhanden sein. Können Sie hinzufügen und Konfigurieren von Language Packs von der Freigabe Verteilung der in der Phase der **WindowsPE** -Konfiguration, oder Sie können diese cks) (Pa Sprache engl. während der Konfiguration **WindowsPE** übergeben, und konfigurieren Sie die Einstellungen in einer anderen Konfiguration Durchlauf hinzufügen.

    Die Microsoft-Windows-International-Core-Windows PE-Komponente enthält die Einstellungen, die können Sie das Ändern der Sprache und Gebietsschema während der Konfiguration **WindowsPE** übergeben. Darüber hinaus können Sie durch Angeben von Werten in dieser Komponente Benutzeroberflächensprache für Windows Setup ändern.

-   Language Packs installiert werden, um das Windows-Abbild und Einstellungen konfiguriert sind, während der Konfiguration **specialize** und **Oobesystem** übergibt.

    OEMs und Unternehmen, die eine einzige Sprache-Edition von Windows in der Regel für die verschiedenen Regionen bereitstellen, für jede Region eine Antwortdatei erstellen, und legen die Einstellungen der Gebietsschema und Tastatur im Durchgang Konfiguration **specialize** . In diesem Szenario wird das Windows-Abbild das Sprachpaket hinzugefügt, bevor internationale Einstellungen konfiguriert werden.

    Die Microsoft-Windows-International-Core-Komponente enthält die Einstellungen, die können Sie das Ändern der Sprache und Gebietsschema während der Konfiguration **specialize** und **OobeSystem** übergibt.

    Können Sie vor dem Wählen Sie eine Sprache und direkt von der Windows-Willkommensseite Sprache Benutzeroberfläche Auswahlseite für Benutzer durch Angeben von Sprache und Gebietsschema in der Konfiguration **OobeSystem** übergeben wird, in der Microsoft-Windows-International-Core-Komponente. Im Allgemeinen kann der Benutzer wählen zwischen die Standardsprache für das Setup und zusätzlichen Sprachen, die im Abbild installiert sind. Die Auswahl der Sprache aktualisiert die anderen regionalen Einstellungen auf die Standardwerte, die diese Sprache zugeordnet sind. Der Benutzer kann dann einzeln die Standardeinstellungen ändern.

**Übergeben zum Konfigurieren von internationale Einstellungen während der Konfiguration von Windows PE**

1.  Stellen Sie sicher, dass die erforderlichen Language Packs im Bild oder in einer Windows-Verteilungsfreigabe verfügbar sind. Weitere Informationen zu mehrsprachigen Verteilung Freigaben finden Sie unter [Hinzufügen von Unterstützung mehrerer Sprachen in eine Windows-Distribution](add-multilingual-support-to-a-windows-distribution.md).

2.  Öffnen Sie Windows System Image Manager (Windows SIM) und erstellen Sie eine Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085).

3.  Die Antwortdatei Einstellungen während des **WindowsPE** Konfiguration Schritts anwenden die Microsoft-Windows-International-Core-Windows PE-Komponente hinzugefügt.

4.  Konfigurieren von internationalen Einstellungen in der Microsoft-Windows-International-Core-Windows PE Komponente. Beispielsweise wenn das Sprachpaket für Spanisch in der Verteilung Freigabe verfügbar ist, können Sie *es-ES* Werte für die Komponente hinzufügen, die Einstellungen in der Konfiguration **WindowsPE** weitergeben.

    Die meisten Systemgebietsschemas ist einen Neustart erforderlich. Wenn Sie Ihr Gebietsschema, die während der Konfiguration **WindowsPE** Einstellungen übergeben konfigurieren, wird der Computer automatisch neu gestartet. Zusätzliche Neustarts sind nicht erforderlich.

    Finden Sie weitere Informationen zu diesen Einstellungen die Microsoft-Windows-International-Core-Windows PE-Komponenten in der Windows® Referenz für unbeaufsichtigte aus.

5.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM. Das Language Pack in der Verteilung Freigabe automatisch hinzugefügt und internationalen Einstellungen angewendet werden, wenn Sie Windows Setup ausführen, und geben Sie diese Datei annehmen.

**Übergeben zum Konfigurieren von internationale Einstellungen während der Konfiguration specialize**

1.  Stellen Sie sicher, dass die erforderlichen Language Packs im Abbild verfügbar sind. Weitere Informationen zum Hinzufügen eines Sprachpakets offline finden Sie unter [Hinzufügen und Entfernen von Language Packs Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md). Weitere Informationen dazu, wie Sie ein Language Pack mithilfe einer Antwortdatei hinzufügen finden Sie unter [Hinzufügen eines Pakets zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915066).

2.  Öffnen Sie Windows SIM, und erstellen Sie eine neue Antwortdatei. Weitere Informationen finden Sie unter [Erstellen oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085).

3.  Fügen Sie die Microsoft-Windows-International-Core-Komponente, um während der Konfigurationsphasen **specialize** und **OobeSystem** Einstellungen gelten hinzu.

    Die meisten Systemgebietsschemas ist einen Neustart erforderlich. Wenn Sie spracheinstellungen während der Konfigurationsphasen **specialize** oder **OobeSystem** verarbeiten, möglicherweise der Computer einen zusätzlichen Neustart erforderlich.

4.  Bearbeiten Sie die Einstellungen für die Microsoft-Windows-International-Core-Komponente zum Konfigurieren der internationaler Einstellungen für eine bestimmte Region. Beispielsweise können Sie hinzufügen, dass Werte an den Microsoft-Windows-International-Core-Einstellungen in der Konfiguration **specialize** *EN-US* übergeben.

    Können Sie auch vor dem Auswählen einer Sprache und Sprachen angeben und Gebietsschema in der Konfiguration **OobeSystem** übergeben wird, in der Microsoft-Windows-International-Core-Komponente. Wenn Sie dies tun, wird der Windows-Willkommensseite Sprache Benutzeroberfläche Auswahlseite beim Starten der Benutzer die Windows-Willkommensseite übersprungen. Im Allgemeinen kann der Benutzer auswählen, zwischen die Standardsprache für das Setup und zusätzlichen Sprachen, die im Abbild installiert sind. Die Auswahl der Sprache wird die anderen regionalen Einstellungen auf die Standardwerte dieser Sprache zugeordnet aktualisiert. Der Benutzer kann dann diese Standardeinstellungen ändern einzeln.

    Finden Sie weitere Informationen zu diesen Einstellungen die Microsoft-Windows-International-Core-Komponente in der Windows® Referenz für unbeaufsichtigte aus.

5.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM. Wenn Sie diese Antwortdatei angeben Windows Setup ausführen, werden die regionalen Einstellungen, die Sie in die Antwortdatei angegeben angewendet werden.

**So ändern Sie die internationale Einstellungen in separaten Konfigurationsphasen in der gleichen Antwortdatei:**

-   Erstellen Sie mehrere Abschnitte in einer Antwortdatei aus, die verschiedene Sprachoptionen in verschiedenen Phasen des Windows-Installation verarbeitet werden soll. Dadurch können Sie mehrere spracheinstellungen in einer Antwortdatei zu konfigurieren, durch Angeben von unterschiedlichen Einstellungen in unterschiedlichen Konfigurationsphasen verarbeitet werden. Weitere Informationen finden Sie unter [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md).

    Beispielsweise können Sprache und Gebietsschema in der Konfiguration **WindowsPE** übergeben, mit der Microsoft-Windows-International-Core-Windows PE-Komponente.

    Sie können die Standardeinstellung, Einstellungen in der **OobeSystem** oder die Konfiguration **specialize** durch Hinzufügen von Einstellungen zu Microsoft-Windows-International-Hauptkomponenten weitergeben, klicken Sie dann ändern.

    Beispielsweise können Sie *EN-US* als Standardsprache für die Verwendung auf dem Computer im **WindowsPE** Konfiguration Durchgang angeben. Wenn Sie den Computer zu einem anderen Bereich senden möchten, können Sie **der Konfigurationsphase** klicken Sie dann weitere Einstellungen von Sprachen und Gebietsschemas hinzufügen.

    Wenn während **der Konfigurationsphase** spracheinstellungen verarbeitet werden, kann ein Neustart erforderlich sein. Darüber hinaus kann die erforderliche Zeit für den Computer zum Verarbeiten von spracheinstellungen der Endbenutzer verhindern, Windows-Willkommensseite schnell.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445)

[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md)

 

 






