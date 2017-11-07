---
author: Justinha
Description: "Passen Sie das Standardprofil für Benutzer mithilfe von CopyProfile"
ms.assetid: 4aa887d1-1ecb-4fad-9119-ac851c273ab3
MSHAttr: PreferredLib:/library/windows/hardware
title: Anpassen des Standardbenutzerprofils mithilfe von CopyProfile
ms.openlocfilehash: 204212a2c11d16ffd18099f8a7df594a22fe7567
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-the-default-user-profile-by-using-copyprofile"></a>Passen Sie das Standardprofil für Benutzer mithilfe CopyProfile


Sie können die `CopyProfile` Einstellung, um ein Benutzerprofil anpassen und kopieren Sie das Profil in das Standardprofil für Benutzer. Windows® verwendet das Standardprofil für Benutzer als Vorlage, um jedem neuen Benutzer ein Profil zuzuweisen. Indem Sie das Standardprofil für Benutzer anpassen, können Sie Einstellungen für alle Benutzerkonten konfigurieren, die auf dem Computer erstellt werden. Mithilfe von `CopyProfile`; Sie können installierten Programme, Treiber, desktop Hintergründe, Internet Explorer-Einstellungen und weitere Konfigurationen anpassen. Beachten Sie, dass einige Einstellungen nicht, mithilfe von beibehalten werden `CopyProfile`.

IT-Experten und Unternehmen können `CopyProfile` auf das Kachel benutzerdefinierte Layout der Gruppen auf **der Startseite** beizubehalten.

In diesem Thema:

-   [Beibehalten von für Benutzerprofile](#bkmk-preserve)

-   [Konfigurieren von Standardeinstellungen für Benutzerprofil](#bkmk-configure)

-   [Zur Problembehandlung CopyProfile](#bkmk-troubleshoot)

## <a name="span-idbkmkpreservespanspan-idbkmkpreservespancreating-an-answer-file-with-the-copyprofile-setting"></a><span id="bkmk_preserve"></span><span id="BKMK_PRESERVE"></span>Erstellen einer Antwortdatei mit der Einstellung CopyProfile


Verwenden Sie das folgende Verfahren zum Erstellen einer Antwortdatei, um **Sysprep** für Benutzerprofile zu kopieren, wenn Sie das Windows-Abbild verallgemeinern anzuweisen.

**Erstellen Sie eine separate Antwortdatei für das Kopieren von für Benutzerprofile**

1.  Öffnen Sie auf dem Referenzcomputer Windows System Image Manager (Windows SIM). Klicken Sie auf **Start**, geben Sie **Windows System Image Manager**, und wählen Sie dann **Windows System Image Manager**. Weitere Informationen zu Windows SIM finden Sie unter [Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445).

2.  Erstellen Sie eine neue Antwortdatei mit **Sysprep**verwenden:

    1.  Klicken Sie auf **Datei**, und klicken Sie dann auf **Neue Antwortdatei**. Klicken Sie im Bereich **Antwortdatei** wird eine leere Antwortdatei angezeigt.

        **Hinweis**  
        Wenn die Katalogdatei klicken Sie im **Windows-Abbild** nicht angezeigt wird, befolgen Sie die Anweisungen in [Windows-Abbild oder Katalogdatei öffnen](https://msdn.microsoft.com/library/windows/hardware/dn915104).

         

    2.  Erweitern Sie im **Windows-Abbild** **Komponenten**der rechten Maustaste auf **amd64\_Microsoft-Windows-Shell-Setup**, und klicken Sie dann auf **Hinzufügen-Einstellung, um Pass 4 specialize**.

    3.  Die **Antwortdatei** wählen Sie im Bereich der **Komponenten\\4\_specialize\\amd64-Microsoft-Windows-Shell-Setup\_neutrale** Ordner.

    4.  Geben Sie in der **Microsoft-Windows-Shell-Setup** Eigenschaftenbereich in den Abschnitt **Einstellungen für** den Wert `CopyProfile = true`.

    5.  Speichern Sie diese neue Antwortdatei in das Stammverzeichnis des Wechselmedium oder Speicherort im Netzwerk, und nennen Sie es **CopyProfile**.

Weitere Informationen finden Sie unter [Bewährte Methoden für die Erstellung von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073) und [Unbeaufsichtigten Windows Setup-Referenzhandbuch](http://go.microsoft.com/fwlink/?LinkId=206281).

## <a name="span-idbkmkconfigurespanspan-idbkmkconfigurespanconfiguring-default-user-profile-settings"></a><span id="bkmk_configure"></span><span id="BKMK_CONFIGURE"></span>Konfigurieren von Standardeinstellungen für Benutzerprofil


Verwenden Sie das folgende Verfahren zum Konfigurieren von benutzereinstellungen im Überwachungsmodus aktiviert, und klicken Sie dann verallgemeinern Sie die Windows-Installation mithilfe einer Antwortdatei, enthält die `CopyProfile` Einstellung. Wenn Sie Windows mit einer anderen Antwortdatei installieren, sollte nicht die Antwortdatei enthalten die `CopyProfile` Einstellung oder eine beliebige Einstellung, die zusätzliche Benutzerkonten erstellen.

**Zum Konfigurieren von Standardeinstellungen für Benutzerprofil und Verallgemeinern des Abbilds**

1.  Installieren von Windows auf eine Referenzcomputers und Boot im Überwachungsmodus aktiviert. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

    **Wichtige**  
    Verwenden Sie ein Domänenkonto nicht, da die `CopyProfile` Einstellung ausgeführt wird, nachdem der Computer beim Ausführen von **Sysprep**aus der Domäne entfernt wird. Daher verlieren Sie alle Einstellungen, die Sie in einer Domäne konfiguriert. Wenn Sie das Standardprofil für Benutzer ändern und dann den Computer zu einer Domäne hinzufügen, erscheint die Anpassungen, die Sie für die Standard-Benutzerprofil vorgenommen auf neue Domänenkonten.

     

2.  Passen Sie das integrierte Administratorkonto durch Installieren von Anwendungen, desktop Verknüpfungen und andere Einstellungen.

    **Wichtige**  
    Es besteht ein Grenzwert der Anzahl der bereitgestellten Windows-Runtime-basierter apps, die Sie installieren können. Sie können jedoch Skripts zum Installieren von zusätzlichen nicht bereitgestellte apps erstellen. Weitere Informationen finden Sie unter [Sideload-Apps mit DISM](sideload-apps-with-dism-s14.md).

     

3.  Nach Abschluss der Anpassungen legen Sie das Medium, die die Antwortdatei CopyProfile in des Referenzcomputers enthält. Beispielsweise können Sie die Antwortdatei auf ein USB-Laufwerk kopieren.

4.  Auf dem Referenzcomputer Öffnen einer Eingabeaufforderung mit erhöhten Rechten, und geben Sie folgenden Befehl:

    ``` syntax
    C:\Windows\System32\Sysprep\Sysprep /generalize /oobe /shutdown /unattend: F:\CopyProfile.xml
    ```

    wobei *F* der Buchstabe des USB flash-Laufwerk oder Wechselmedium ist. Das **Sysprep** -Tool entfernt computerspezifischen Informationen aus dem Bild, Beibehaltung für die Benutzerprofile, die Sie konfiguriert haben. Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

Nachdem das Bild allgemeiner (engl.) ist, Herunterfahren des Computers, erfassen Sie das Abbild durch Windows PE starten und dann mithilfe von DISM Erfassen der Windows-Installations. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md) und [Erfassen Bilder der Festplatte Partitionen mithilfe DISM](capture-images-of-hard-disk-partitions-using-dism.md). Nachdem das Abbild erfasst wird, können Sie es auf einem Zielcomputer mithilfe von DISM bereitstellen. Weitere Informationen finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

## <a name="span-idtesttheuserprofilecustomizationsspanspan-idtesttheuserprofilecustomizationsspanspan-idtesttheuserprofilecustomizationsspantest-the-user-profile-customizations"></a><span id="Test_the_User_Profile_Customizations"></span><span id="test_the_user_profile_customizations"></span><span id="TEST_THE_USER_PROFILE_CUSTOMIZATIONS"></span>Testen Sie die Profil Benutzeranpassungen


Nachdem angepassten Abbilds auf einem Zielcomputer bereitgestellt wird, können Sie die Profil benutzeranpassungen testen. Sie können über Out-Of-Box-Erfahrung (OOBE) zum Testen des Endbenutzers wechseln, oder Sie können die benutzeranpassungen im Überwachungsmodus testen.

**Wichtige**  
Apps basierend auf Windows-Runtime wird nicht im Überwachungsmodus gestartet werden, da im Überwachungsmodus das integrierte Administratorkonto verwendet. Zum Ausführen von Windows-Runtime-basierter apps müssen Sie einen Registrierungsschlüssel ändern, bevor Sie Ihre Windows-Installation im Überwachungsmodus überprüfen können.

 

**So testen Sie die Benutzerprofil Anpassungen nach OOBE**

1.  Installieren von Windows auf einem Testcomputer.

2.  Nach der Installation von Windows OOBE durchlaufen Sie, und geben Sie den Namen des Computers, Benutzerkontonamen und andere Elemente. Nachdem OOBE abgeschlossen ist, wird der Windows-Startseite angezeigt.

3.  Melden Sie sich an dem Computer mit dem Benutzerkonto während der OOBE angegeben, und stellen Sie sicher, dass Ihre apps und Anpassungen angezeigt werden.

**So testen Sie die Benutzerprofil Anpassungen im Überwachungsmodus aktiviert**

1.  Starten Sie im Überwachungsmodus mithilfe einer Antwortdatei oder durch Drücken von STRG + UMSCHALT + F3 beim OOBE starten. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

2.  Stellen Sie sicher, dass Ihre Anpassungen wie vorgesehen funktionieren. Um Windows-Runtime-basierter apps zu testen, ändern Sie den folgenden Registrierungsschlüssel:

    1.  Führen Sie von einer Eingabeaufforderung mit erhöhten Rechten Regedit.exe.

    2.  Navigieren Sie zu der **HKEY\_LOKALEN\_COMPUTER\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Richtlinien\\System\\FilterAdministratorToken** Registrierungsschlüssel.

    3.  Klicken Sie auf **FilterAdministrationToken**, und geben Sie als Wert **1** .

    4.  Melden Sie sich vom Computer ab.

    5.  Melden Sie sich am Computer angemeldet, und starten Sie die Windows-Runtime-basierte apps um sicherzustellen, dass Ihre Anpassungen wie vorgesehen funktionieren.

    6.  Nach Abschluss der Überprüfung Ihrer Apps Windows-Runtime-basierte setzen Sie den Registrierungsschlüssel **FilterAdministrationToken** auf **0**zurück.

## <a name="span-idbkmktroubleshootspanspan-idbkmktroubleshootspantroubleshooting-copyprofile"></a><span id="bkmk_troubleshoot"></span><span id="BKMK_TROUBLESHOOT"></span>Problembehandlung bei CopyProfile


Wenn für die Benutzerprofile werden nicht erfolgreich kopiert:

1.  Stellen Sie sicher, dass Sie festlegen, die `CopyProfile` während der Bereitstellung nur einmal festlegen.

2.  Wenn Sie benutzereinstellungen anpassen, nur verwenden Sie nur das integrierten Administratorkonto auf dem Computer um zu vermeiden versehentlich Einstellungen aus dem falschen Profil kopieren.

3.  Vergewissern Sie sich, dass Sie ein Domänenkonto verwendet haben.

4.  Stellen Sie sicher, dass es keine zusätzliche Benutzerkonten als das integrierte Administratorkonto, das Sie konfiguriert sind:

    1.  Klicken Sie auf **Start**, und geben Sie dann auf **Systemsteuerung**.

    2.  Klicken Sie auf **Systemsteuerung**, und klicken Sie dann auf **Hinzufügen oder Entfernen von Benutzerkonten**.

    3.  Wählen Sie jedes zusätzliche Benutzerkonto als das integrierte Administratorkonto, das Sie konfiguriert haben, und löschen Sie ihn.

    **Hinweis**  
    Löschen Sie alle anderen Benutzerkonten auf dem Computer, vor dem Anpassen der integrierten Administratorkonto an.

     

5.  Stellen Sie sicher, dass nicht bereitgestellte Windows-Runtime-basierte apps, die in das Layout Kachel gespeichert sind, innerhalb von zwei Stunden Benutzer melden Sie sich installiert sind an das Kachel Layout auf **der Startseite** beibehalten, wenn apps registriert werden, nachdem der neue Benutzer zuerst anmeldet.

6.  Einige Einstellungen können nur mithilfe von konfiguriert werden die `CopyProfile` für die unbeaufsichtigte Installation Einstellung und andere Einstellungen mithilfe von Gruppenrichtlinien konfiguriert werden können.

    -   Verwenden von Gruppenrichtlinien zum Konfigurieren von Einstellungen, die durch die Anmeldung des neuen Benutzers zurückgesetzt werden. Sie können auch Skripts zum Definieren dieser benutzereinstellungen erstellen.

        \endash oder \endash

    -   Verwendung der `CopyProfile` für die unbeaufsichtigte Installation stattdessen festlegen. Weitere Informationen finden Sie unter [Referenz für unbeaufsichtigte Windows](http://go.microsoft.com/fwlink/?LinkId=206281).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md)

[Sysprep-Prozess (Übersicht)](sysprep-process-overview.md)

[Sysprep-Befehlszeilenoptionen](sysprep-command-line-options.md)

 

 






