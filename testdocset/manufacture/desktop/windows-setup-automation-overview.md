---
author: Justinha
Description: "Übersicht über die Automatisierung von Windows-Setup"
ms.assetid: 240b02ae-1f06-4b92-9b46-b4dbd1089c65
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übersicht über die Automatisierung von Windows-Setup"
ms.openlocfilehash: fd0fe5ec99d084ba0a624e9c7f992b7c2740eb18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-automation-overview"></a>Übersicht über die Automatisierung von Windows-Setup

## <a name="use-setupconfigini-to-install-windows"></a>Verwenden Sie zum Installieren von Windows Setupconfig.ini

### <a name="what-is-a-setupconfig-file"></a>Was ist eine Setupconfig-Datei?

Setupconfig ist eine Konfigurationsdatei, die verwendet wird, um eine Reihe von Kennzeichen oder Parameter an Windows setup.exe übergeben. Verwenden Sie diese Datei als Alternative zum Übergeben von Parametern an Windows Setup in einer Befehlszeile. Diese Funktion ist in Windows 10, Version 1511 und höher verfügbar.

Die Datei Setupconfig können IT-Experten Parameter Windows Setup vom Windows Update und Windows Server Update Services hinzufügen.

Die verschiedenen Parameter, die mit Windows 10 Setup.exe verwendet werden können, werden in diesem Thema beschrieben.

Setupconfig.ini Dateien enthalten können einzelne Parameter oder Parameter und Wert-Paare. Nehmen Sie keine "/" Zeichen und mit dem Parameter-Wert-Paaren, zwischen den beiden enthalten "=". 

Beispielsweise erstellen Sie eine Setupconfig.ini durch Folgendes. Beachten Sie, dass die Kopfzeile `[SetupConfig]` erforderlich ist.

```syntax
[SetupConfig]
NoReboot
ShowOobe=None
Telemetry=Enable
ReflectDrivers = <path of folder containing INF and SYS files for the encryption drivers>
```

Dies ist gleichbedeutend mit der folgenden Befehlszeile:

```syntax
Setup /NoReboot /ShowOobe None /Telemetry Enable
```

### <a name="how-does-windows-setup-use-setupconfigini"></a>Wie wird Windows Setup Setupconfig.ini verwendet?

#### <a name="using-mediaiso-file"></a>Verwenden von Medien-ISO-Datei

Wenn Sie Windows Setup von Medium oder eine ISO-Datei ausführen, müssen Sie den Speicherort der Datei Setupconfig in der Befehlszeile einschließen ("/ ConfigFile `<path>`") beim Ausführen von setup.exe. Beispiel:

```syntax
Setup.exe /ConfigFile <path to Setupconfig.ini>
```

Wenn Sie einen Parameter in der Befehlszeile, und derselbe Parameter in der Datei Setupconfig einschließen, hat die Setupconfig Dateiparameter und Wert Vorrang vor. 

#### <a name="using-windows-update"></a>Mithilfe von Windows Update

Wenn das Update über Windows Update angeboten wird, sucht Setup Windows einen Standardspeicherort für eine Setupconfig-Datei. Sie können die Setupconfig-Datei einschließen:

"% systemdrive%\Users\Default\AppData\Local\Microsoft\Windows\WSUS\SetupConfig.ini"


## <a name="use-an-answer-file-while-installing-windows"></a>Verwenden Sie eine Antwortdatei während der Installation von Windows

Sie können Windows-Installation mithilfe einer Antwortdatei automatisieren:

**Verwenden Sie ein USB-Laufwerk**

1.  Verwenden Sie eine Beispieldatei Antwort ein, oder erstellen Sie eigene mit Windows System Image Manager (Windows SIM).

2.  Speichern Sie die Datei als **Autounattend.xml** auf der Stammebene der einem USB-Laufwerk ein.

3.  Auf einem neuen PC tragen Sie die Windows-Produkt-DVD und der USB flash-Laufwerk, und starten Sie den PC. Wenn keine andere Antwortdatei ausgewählt ist, sucht Windows Setup nach dieser Datei.

**Wählen Sie eine Antwortdatei**

-   Sie können eine bestimmten Antwortdatei während der Installation von der Windows-Umgebung Vorinstallation starten und mit dem Befehl " **setup.exe** " und Auswählen der **/ für die unbeaufsichtigte Installation:***Filename* -Option. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

Beispiele für Antwortdateien und eine Liste der Einstellungen zur Automatisierung der Installation verwendet finden Sie unter [Windows-Setup automatisieren](automate-windows-setup.md).

## <a name="modify-an-existing-installation"></a>Ändern einer vorhandenen installation

Da Neustarts während des Setups erforderlich sind, wird eine Kopie der Antwortdatei zwischengespeichert, um die %windir%\\Panther Verzeichnis der Windows-Installation. Ändern Sie die Datei, um eine der folgenden Aktionen ausführen:

-   Aktualisieren Sie System und Control Panel Einstellungen, ohne das Abbild zu starten.

-   Vorbereiten des PCs-Option zum Starten im Überwachungsmodus zum Aktualisieren eines Bilds (finden Sie unter Microsoft Windows-Deployment\\Reseal\\[Modus](http://go.microsoft.com/fwlink/?LinkId=275830)).

-   Aktualisieren Sie die Reihenfolge, in der Treiber oder Pakete installiert sind. (Pakete mit Abhängigkeiten erfordert möglicherweise Installation in einer bestimmten Reihenfolge.)

**Ersetzen Sie die Antwortdatei in einem offline-Abbild**

1.  Erstellen einer benutzerdefinierten Antwortdatei Windows System Image Manager (Windows SIM).

2.  Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten.

3.  Stellen Sie das Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\images\CustomImage.wim" /Index:1 /MountDir:C:\mount
    ```

4.  Ändern oder Ersetzen Sie die Datei: \\Windows\\Panther\\unattend.xml im bereitgestellten Abbild.

    ``` syntax
    Copy CustomAnswerFile.xml C:\mount\Windows\Panther\unattend.xml
    ```

    **Hinweis**  
    Die Antwortdatei im Bild kann Einstellungen enthalten, die noch nicht verarbeitet. Wenn Sie diese Einstellungen auf verarbeitet abrufen möchten, bearbeiten Sie die vorhandene Datei, anstatt es zu ersetzen.

     

5.  Hängen Sie das Bild aus.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount /Commit
    ```

6.  Testen Sie das Abbild, indem es auf einen neuen PC, ohne Angabe einer Antwortdatei bereitgestellt. Wenn Windows Setup ausgeführt wird, sucht und diese Antwortdatei verwendet.

## <a name="implicit-answer-file-search-order"></a>Reihenfolge der Suche nach der impliziten Antwort


Windows-Setup sucht nach Antwortdateien am Anfang jeder Konfiguration Pass, einschließlich der Erstinstallation und nach dem anwenden, und starten ein Bild. Wenn eine Antwortdatei wurde gefunden, und es Einstellungen für die angegebene Konfiguration übergeben enthält, werden diese Einstellungen verarbeitet.

Windows-Setup identifiziert und protokolliert alle verfügbaren Antwortdateien, abhängig von der Reihenfolge der Suche. Die Antwortdatei mit der höchsten Priorität wird verwendet. Die Antwortdatei wird überprüft, und klicken Sie dann auf dem Computer zwischengespeichert. Gültige Antwortdateien werden auf die $Windows zwischengespeichert ~ BT\\Quellen\\Panther Directory während der Konfiguration [WindowsPE](windowspe.md) und [OfflineServicing](offlineservicing.md) übergibt. Nachdem die Windows-Installation auf der Festplatte extrahiert werden, wird die Antwortdatei % WINDIR% zwischengespeichert\\Panther.

In der folgenden Tabelle zeigt die Reihenfolge der impliziten Antwortdatei Suche nach.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Reihenfolge der Suche</th>
<th align="left">Speicherort</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1</p></td>
<td align="left"><p>Registrierung</p>
<p>HKEY_LOCAL_MACHINE\System\Setup\UnattendFile</p></td>
<td align="left"><p>Gibt einen Zeiger in der Registrierung zu einer Antwortdatei. Die Antwortdatei ist nicht erforderlich, damit Unattend.xml heißen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>%WINDIR%\Panther\Unattend</p></td>
<td align="left"><p>Der Name der Antwortdatei muss Unattend.xml oder Autounattend.xml sein.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Windows Setup wird dieses Verzeichnis nur bei abwärtskompatiblen Installationen. Wenn Windows Setup von Windows PE gestartet wird, wird das Verzeichnis %WINDIR%\Panther\Unattend nicht durchsucht werden.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>%WINDIR%\Panther</p></td>
<td align="left"><p>Windows-Setup zwischengespeichert Antwortdateien an diesem Speicherort für die Verwendung im nachfolgenden Phasen der Installation. Beim Neustart von eines Computers kann beispielsweise Setup fortgesetzt, um die Einstellungen in einer Antwortdatei anzuwenden. Wenn Sie eine Antwortdatei explizit mithilfe von Windows Setup oder Sysprep angeben, wird die in diesem Verzeichnis zwischengespeicherte Antwortdatei mit der explizit angegebene Antwortdatei überschrieben.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Führen Sie nicht verwenden, ändern oder die Antwortdatei in diesem Verzeichnis zu überschreiben. In diesem Verzeichnis die Antwortdatei wird während der Installation von Windows Setup gekennzeichnet. Diese Antwortdatei kann nicht in Windows SIM oder andere Windows-Installationen verwendet werden.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>Lese-/Schreibzugriff austauschbaren Medien in Reihenfolge des Laufwerkbuchstabens, im Stamm von Laufwerk.</p></td>
<td align="left"><p>Austauschbare Lese-/Schreibzugriff Media in der Reihenfolge des Laufwerkbuchstabens, im Stamm von Laufwerk.</p>
<p>Der Name der Antwortdatei muss Unattend.xml oder Autounattend.xml, und die Antwortdatei muss sich im Stamm des Laufwerks befinden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>5</p></td>
<td align="left"><p>Nur-Lese-Wechselmedium in der Reihenfolge des Laufwerkbuchstabens, im Stamm von Laufwerk.</p></td>
<td align="left"><p>Nur-Lese-Wechselmedium in der Reihenfolge des Laufwerkbuchstabens, im Stamm von Laufwerk.</p>
<p>Der Name der Antwortdatei muss Unattend.xml oder Autounattend.xml, und es muss sich im Stammverzeichnis des Laufwerks.</p></td>
</tr>
<tr class="even">
<td align="left"><p>6</p></td>
<td align="left"><p>Konfigurationsphasen [WindowsPE](windowspe.md) und [OfflineServicing](offlineservicing.md) :</p>
<ul>
<li><p>\Sources Directory in einer Windows-Verteilung</p></li>
</ul>
<p>Alle anderen Phasen:</p>
<ul>
<li><p>%WINDIR%\system32\sysprep</p></li>
</ul></td>
<td align="left"><p>In den Konfigurationsphasen [WindowsPE](windowspe.md) und [OfflineServicing](offlineservicing.md) muss der Name der Antwortdatei Autounattend.xml sein.</p>
<p>Für alle anderen Konfigurationsphasen muss der Dateiname Unattend.xml sein.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>7</p></td>
<td align="left"><p>SYSTEMLAUFWERK %</p></td>
<td align="left"><p>Der Antwort-Dateiname muss Unattend.xml oder Autounattend.xml sein.</p></td>
</tr>
<tr class="even">
<td align="left"><p>8</p></td>
<td align="left"><p>Laufwerk aus dem Windows-Setup (setup.exe) im Stamm von Laufwerk ausgeführt wird.</p></td>
<td align="left"><p>Der Name der Antwortdatei muss Unattend.xml oder Autounattend.xml und muss sich im Stammverzeichnis des Ordnerpfads Windows Setup.</p></td>
</tr>
</tbody>
</table>

 

## <a name="sensitive-data-in-answer-files"></a>Vertrauliche Daten in Antwortdateien


Setup entfernt vertrauliche Daten in der zwischengespeicherten Antwortdatei am Ende der einzelnen.

**Wichtige**  
Da Antwortdateien während der Installation von Windows auf dem Computer zwischengespeichert werden, werden auf dem Computer zwischen Neustarts Antwortdateien beibehalten. Bevor Sie den Computer an einen Kunden übermitteln, müssen Sie die zwischengespeicherten Antwortdatei in %windir% löschen\\Panther Directory. Wenn Sie Domänenkennwörter, die Product Keys oder andere vertraulichen Daten in die Antwortdatei einschließen möglicherweise potenzielle Sicherheitsrisiken vor. Jedoch, wenn Sie Einstellungen für nicht verarbeitete in der Konfiguration [OobeSystem](oobesystem.md) übergeben, die Sie beim Starten des Computers durch eines Endbenutzers ausführen möchten haben, sollten Sie löschen in den Abschnitten der Antwortdatei, die bereits verarbeitet wurden. Eine Option, die beim Ausführen des Befehls **Sysprep/oobe** möglicherweise eine separate Antwortdatei verwendet, die nur in der Konfigurationsphase Einstellungen enthält.

 

Jedoch wenn eine Antwortdatei in einem höheren Vorrang vor Ort als die zwischengespeicherte Antwortdatei eingebettet ist, kann dann die zwischengespeicherte Antwort am Anfang des jedem nachfolgenden Konfiguration Lauf überschrieben, wenn die eingebettete Antwortdatei den impliziten Suchkriterien entspricht. Wenn eine Antwortdatei %windir% eingebettet ist beispielsweise\\Panther\\unbeaufsichtigte Installation\\Unattend.xml, wird die eingebettete Antwortdatei die zwischengespeicherte Antwortdatei am Anfang der einzelnen ersetzen. Beispielsweise, wenn die eingebettete Antwortdatei Konfigurationsphasen [specialize](specialize.md) und [OobeSystem](oobesystem.md) , und klicken Sie dann auf die eingebettete Antwortdatei gibt wird für die Konfiguration **specialize** erkannt Durchgang zwischengespeichert, verarbeitet, und vertrauliche Daten ist deaktiviert. Die eingebettete Antwortdatei wird während der Konfigurationsphase erneut ermittelt und zwischengespeichert. Daher werden die sensiblen Daten für die Konfigurationsdurchgangs nicht mehr gelöscht. Vertrauliche Daten für zuvor verarbeitete Konfigurationsphasen werden nicht erneut gelöscht werden. Es sei denn, die die zwischengespeicherte Antwortdatei überschrieben werden muss, wird empfohlen, Antwortdateien an einem Standort eingebettet werden, die eine niedrige Priorität hat.

**Wichtige**  
Da Antwortdateien während der Installation von Windows auf dem Computer zwischengespeichert werden, werden auf dem Computer zwischen Neustarts Antwortdateien beibehalten. Bevor Sie den Computer an einen Kunden übermitteln, müssen Sie die zwischengespeicherten Antwortdatei in %windir% löschen\\Panther Directory. Wenn Sie Domänenkennwörter, die Product Keys oder andere vertraulichen Daten in die Antwortdatei einschließen möglicherweise potenzielle Sicherheitsrisiken vor. Jedoch, wenn Sie Einstellungen für nicht verarbeitete in der Konfiguration [OobeSystem](oobesystem.md) übergeben, die Sie beim Starten des Computers durch eines Endbenutzers ausführen möchten haben, sollten Sie löschen in den Abschnitten der Antwortdatei, die bereits verarbeitet wurden. Eine Option, die beim Ausführen des Befehls **Sysprep/oobe** möglicherweise eine separate Antwortdatei verwendet, die nur in der Konfigurationsphase Einstellungen enthält.

 

Sie können die Befehlsskript Setupcomplete.cmd einen Befehl hinzufügen, die alle zwischengespeicherten oder eingebetteten Antwortdateien auf dem Computer gelöscht. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md).

##<a name="windows-setup-annotates-configuration-passes-in-an-answer-file"></a>Windows-Setup fügt Konfigurationsphasen in einer Antwortdatei


Nach der Konfiguration erfolgreich verarbeitet wird, fügt Windows Setup die zwischengespeicherten Antwortdatei an, dass der Lauf verarbeitet wurden. Wenn die Konfigurationsdurchlauf erneut ausgeführt wird und die zwischengespeicherte Antwortdatei nicht ersetzt oder in der Zwischenzeit aktualisiert wurde, werden die Einstellungen der Antwort-Datei nicht erneut verarbeitet. Stattdessen wird Windows Setup nach impliziten Unattend.xml-Dateien gesucht, die an einem Ort mit niedrigerer Rangfolge als die zwischengespeicherte Unattend.xml-Datei.

Sie können beispielsweise Windows installieren, mit einer Antwortdatei, die Microsoft Windows-Deployment enthält /**RunSynchronous** Befehle in der Konfiguration [specialize](specialize.md) übergeben. Bei der Installation des Konfigurationsdurchgangs ausgeführt wird und die **RunSynchronous** Befehle ausführen. Führen Sie den Befehl **Sysprep** nach der Installation mit der Option **/ verallgemeinern** . Wenn es keine Antwortdatei in eine höhere Priorität ist als die zwischengespeicherte Antwortdatei oder einer Antwortdatei nicht explizit an das Sysprep-Tool übergeben wurde, startet Setup ausgeführt wird, die die Konfiguration Specialize übergeben dem nächsten Mal an, die den Computer an. Da die zwischengespeicherte Antwortdatei eine Anmerkung enthält, dass die Einstellungen für diese Konfiguration Durchlauf bereits angewendet wurden, führen Sie die **RunSynchronous** Befehle nicht ausgeführt.

## <a name="implicit-answer-file-search-examples"></a>Beispiele für implizite Antwortdateien Suche


Anhand der folgenden Beispiele beschreiben das Verhalten der impliziten Antwortdatei Dateisuchen.

### <a name="span-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspanspan-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspanspan-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspananswer-files-named-autounattendxml-are-automatically-discovered-by-windows-setup"></a><span id="Answer_Files_Named_Autounattend.xml_are_Automatically_Discovered_by_Windows_Setup"></span><span id="answer_files_named_autounattend.xml_are_automatically_discovered_by_windows_setup"></span><span id="ANSWER_FILES_NAMED_AUTOUNATTEND.XML_ARE_AUTOMATICALLY_DISCOVERED_BY_WINDOWS_SETUP"></span>Antwort-Dateien mit dem Namen Autounattend.xml werden automatisch von Windows Setup erkannt

1.  Erstellen Sie eine Antwortdatei mit dem Namen Autounattend.xml, die Einstellungen im [WindowsPE](windowspe.md) Konfiguration Durchgang enthält.

2.  Kopieren Sie Autounattend.xml in einem Wechseldatenträger.

3.  Konfigurieren Sie das BIOS des Computers zum Starten von CD- oder DVD.

4.  Starten Sie die Windows-Produkt-DVD.

5.  Legen Sie das Wechselmedium, wenn Windows gestartet wird. In diesem Beispiel wird davon ausgegangen, dass das Wechselmedium der Laufwerkbuchstabe D: zugewiesen ist\\.

    Windows-Setup startet und wird als gültige Antwortdatei. Da die Antwortdatei verwendet ein gültigen Dateinamen (Autounattend.xml), befindet sich in einer der gültigen Pfade (im Stammverzeichnis des D) und gültige Einstellungen für den aktuellen Konfigurationsdurchlauf ([WindowsPE](windowspe.md)) enthält, diese Antwortdatei verwendet wird.

    Die Antwortdatei wird auf dem Computer zwischengespeichert. Wenn keine zusätzlichen Antwortdateien, die in späteren Phasen entdeckt vorhanden sind, wird die zwischengespeicherte Antwortdatei während Windows Setup verwendet.

### <a name="span-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspanspan-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspanspan-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspananswer-files-are-discovered-in-order-of-precedence-in-predefined-search-paths"></a><span id="Answer_Files_are_Discovered_in_Order_of_Precedence_in_Predefined_Search_Paths"></span><span id="answer_files_are_discovered_in_order_of_precedence_in_predefined_search_paths"></span><span id="ANSWER_FILES_ARE_DISCOVERED_IN_ORDER_OF_PRECEDENCE_IN_PREDEFINED_SEARCH_PATHS"></span>Antwortdateien werden in der Rangfolge in vordefinierten Suche Pfade ermittelt.

1.  Installieren Sie Windows mit einer Antwortdatei mit den Schritten im vorherigen Szenario. Die Antwortdatei, die zum Installieren von Windows zwischengespeichert wird mit dem System in der %windir%\\Panther Directory.

2.  Kopieren Sie eine Unattend.xml-Datei in der %windir%\\System32\\Sysprep-Verzeichnis.

    Diese Antwortdatei hat die Einstellungen im Durchgang Konfiguration [verallgemeinern](generalize.md) .

3.  Führen Sie den Befehl **Sysprep** mit der Option **/ verallgemeinern** zum Erstellen eines Abbilds Verweis.

    Da die %windir%\\System32\\Sysprep-Verzeichnis ist in die implizite Suche Pfade, die Antwortdatei in dieses Verzeichnis kopiert wurde gefunden. Allerdings Antwortdatei, zum Installieren von Windows verwendet wurde ist auf dem Computer noch im Cache und enthält Einstellungen für den [verallgemeinern](generalize.md) Konfigurationsdurchlauf. Diese zwischengespeicherte Antwortdatei hat eine höhere Priorität als der in das Verzeichnis Sysprep kopiert. Die zwischengespeicherte Antwortdatei wird verwendet.

    **Hinweis**  
    Das Tool Sysprep kann als ein Befehlszeilentool oder als ein GUI-Tool ausgeführt werden. Wenn Sie das Tool Sysprep als ein GUI-Tool ausführen, können Sie das Kontrollkästchen **verallgemeinern** auswählen.

     

    Um die neue Antwortdatei verwenden, können Sie es in ein Verzeichnis mit höherer Rangfolge als die zwischengespeicherte Antwortdatei kopieren, oder Sie können die Antwortdatei angeben, mit der Option **/ für die unbeaufsichtigte Installation** aus. Beispiel:

    ``` syntax
    sysprep /generalize /unattend:C:\MyAnswerFile.xml
    ```

### <a name="answer-files-must-include-a-valid-configuration-pass"></a>Antwortdateien müssen eine gültige Konfiguration Phase enthalten.

1.  Kopieren Sie eine Unattend.xml-Datei in einem Wechseldatenträger.

    Die Datei Unattend.xml weist Einstellungen nur für die Konfigurationsphasen [AuditSystem](auditsystem.md) und [AuditUser](audituser.md) .

2.  Führen Sie auf einem installierten Windows-Betriebssystem die **Sysprep / / oobe verallgemeinern** Befehl.

    Obwohl die Antwortdatei in einem der impliziten Suche Pfade verfügbar ist, wird die Datei Unattend.xml, da sie keine gültige Phase für die Konfiguration [verallgemeinern](generalize.md) Durchlauf enthält ignoriert.

## <a name="span-idbkmkdspanspan-idbkmkdspanadditional-resources"></a><span id="bkmk_d"></span><span id="BKMK_D"></span>Weitere Ressourcen


Finden Sie unter den folgenden Themen Weitere Informationen zu Antwortdateien und Konfigurationsphasen:

-   [Bewährte Methoden zum Erstellen von Antwortdateien](https://msdn.microsoft.com/library/windows/hardware/dn915073)

-   [Erstellen Sie oder öffnen Sie eine Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915085)

-   [Konfigurieren von Komponenten und Einstellungen in einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915078)

-   [Überprüfen einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915106)

-   [Vertrauliche Daten in einer Antwortdatei ausblenden](https://msdn.microsoft.com/library/windows/hardware/dn915098)

-   [Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md)

[Windows Setup-Installationsvorgang](windows-setup-installation-process.md)

[Automatisieren der Windows-Setup](automate-windows-setup.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






