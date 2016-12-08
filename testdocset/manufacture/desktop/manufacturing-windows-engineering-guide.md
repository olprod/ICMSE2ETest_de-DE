---
author: Justinha
Description: Fertigung Windows Engineering Guide
MSHAttr: PreferredLib:/library/windows/hardware
title: Fertigung Windows Engineering Guide
ms.openlocfilehash: 8a32125263f634e5da8f05db996444a9f51cac8d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-windows-engineering-guide-weg"></a>Manufacturing Windows Engineering Guide (WEG)

Die Fertigung WEG enthält (Original Equipment Manufacturer) und ODM-Partner mit einer Übersicht über die ideale Fertigungsprozess für Windows-10-Geräte mit Anleitungen für potenzielle Fehler und Verkaufschancen Optimieren des Prozesses an. 

## <a name="manufacturing-overview"></a>Übersicht über die Fertigung

Viele Entscheidungen, die Einfluss auf Manufacturability werden einem frühen Zeitpunkt im engineering Aufwand eines neuen Geräts, vorgenommen, damit sorgfältige erfolgen soll, um sicherzustellen, dass der geringsten Aufwand Herstellung ausgewählt ist. Zusätzliche einer Minute für die Fertigung aufgewendeten entspricht, um zusätzliche Kosten für das endgültige Produkt. Die Fertigung WEG soll OEM und ODM-Partner mit einer Übersicht über die ideale Fertigungsprozess bereitstellen, die Software und Hardware in der Fabrik zusammenführt. Dieser WEG bietet außerdem die Gelegenheit, Optimierung der Prozess und Richtlinien zum Planen und häufige Probleme zu vermeiden. Unsere Empfehlung Fertigung und Bereitstellung helfen, die Sie unterstützen: 

- Optimieren der Bild Datenträger Speicherbedarf auf desktops
- Aktivieren der Windows-Bereitstellung auf kleine Kapazität Datenträgern auf desktops
- Verkürzte Bereitstellungszeit Bild
- Möchten Sie den Vorgang zu vereinfachen
- OEM (OA3) Einfügung/reporting Aktivierungsprozess auf Desktops zu vereinfachen. Mobile Geräte ist keine Aktivierung erforderlich.
- Testen Sie und kalibrieren Sie das Gerät in der Zeile assembly
- Unterstützung von anderen Schlüsselszenarien um großartige Geräte zu erstellen

Für dieses Dokument würde eine generische Version des Fertigungsprozesses desktop sieht folgendermaßen aus:

![Generische desktop Fertigungsprozess](images/generic-desktop-manufacturing-process.png)

Der Fertigungsprozess für mobile Geräte würde wie folgt aussehen:

![Generische mobilen Fertigungsprozess](images/generic-mobile-manufacturing-process.png)

Die Manufacturing WEG sollte nicht die [Mindestanforderungen für Hardware Windows](https://msdn.microsoft.com/library/windows/hardware/dn915086.aspx) oder OEM-Richtlinie Dokument (OPD) kommunizieren. Die WHCR und OPD Dokumente haben Vorrang vor alle Informationen in der Produktion WEG. Sie müssen WHCR und OPD einhalten.

## <a name="overall-considerations"></a>Allgemeine Überlegungen

### <a name="manufacturing-path"></a>Fertigung Pfad

Es gibt zwei allgemeine Manufacturing Pfade können je nach Ihrem Unternehmen durchführen – Build Stock (BTS) und Build auf Reihenfolge (BTO). Beachten Sie die Richtlinien in diesem Dokument überprüfen, bei der der Fertigung Pfad für das Gerät zum Investitionen in jeder Phase priorisieren und möglichst für Ihre benutzerdefinierten Prozess wie viel Zeit sparen. 

Eine exemplarische Vorgehensweise Desktopgeräte verwenden finden Sie unter unsere [manufacturing Ende zum Lab](http://go.microsoft.com/fwlink/p/?LinkId=526101).

Für mobile Geräte müssen Sie den Pfad des BTS Fertigung verwenden.

### <a name="build-to-order-bto"></a>Erstellen Sie auf Reihenfolge (BTO)

BTO Geräte mit einem einfachen Image starten und klicken Sie dann den Großteil ihrer Anpassungen bei der Herstellung erhalten.

Der Hauptvorteil ist die flexible Software Stückliste, wodurch topaktuelle Änderungen ermöglicht. Nachteile enthalten eine komplexere Image-Erstellung und manufacturing Prozess, zusätzliche Zeit für die werksseitige und die wachsende Bild Größen. 

### <a name="build-to-stock-bts"></a>Erstellen Sie in den Bestand (BTS)

BTS Geräte verfügen Bilder, die nahezu vollständig in der Übungseinheit angepasst werden. BTS-Prozessen sind einfacher zu planen und zu erzeugen, schneller haben Sie in der Fabrik höhere Qualitätskontrolle und einer kontrollierten Datenträgergröße haben. BTS Geräte müssen noch aktuelle Änderungen in der Fabrik zulassen. Für desktop-Editionen von Windows 10, viele diese Änderungen erfolgen – Wartung offline verwenden.

### <a name="push-button-reset"></a>Drucktaste zurücksetzen

Die Drucktaste Reset-Tools ist nicht mehr erforderlich, eine separate Wiederherstellung des gesamten Systems Bild auf einer separaten Partition. Dies kann mehrere Gigabyte Speicherplatz sparen. Wenn Benutzer müssen zum Aktualisieren oder Zurücksetzen des Geräts, werden so lange ihre installierten Windows-Updates, statt herunterladen und installieren sie alle erneut. Sie werden auch alle Anpassungen halten, die Sie bereitgestellt haben. 

Partitionslayout für die neue ähnelt die herkömmlichen Partitionslayouts von Windows 8.1, mit Ausnahme der Windows RE wird jetzt Partition bis zum Ende des Laufwerks verschoben und ist nicht mehr benötigt eine Wiederherstellung des gesamten Systems separaten Partition.

![Standardlayout Partition](images/default-partition-layout.png)

Weitere Informationen finden Sie unter [Drucktaste zurücksetzen](push-button-reset-overview.md)

Drucktaste Zurücksetzen wird auf mobilen Geräten nicht unterstützt. Führen Sie stattdessen Herstellerstandard zurücksetzen.

### <a name="compact-os"></a>Compact OS

Sie können nun ausführen, die das gesamte Betriebssystem, einschließlich Ihrer vorinstallierte Windows-desktopanwendungen, mit Dateien, komprimiert mithilfe der Compact OS und Single instancing-features. Diese Features ersetzen die WIM-Boot-Funktion von Windows 8.1 Update 1 und einen kleineren Datenträger Speicherbedarf langfristig helfen. 

Das Betriebssystem Compact für alle Geräte wird zwar unterstützt, empfehlen wir Compact OS nur auf Geräten mit Solid-State-Laufwerke, aufgrund der Leistungseinbußen Rotation Laufwerke. 

Weitere Informationen finden Sie unter [Compact OS Single instancing und Optimierung Bild](compact-os.md).

Compact Betriebssystem wird auf mobilen Geräten nicht unterstützt.

### <a name="provisioning-packages"></a>Bereitstellen von Lösungspaketen

Um Zeit beim Erstellen der Bilder zu speichern, können Sie jetzt erfassen und Anwenden von Windows-desktopanwendungen während der Image-Bereitstellung mithilfe von provisioning Pakete. Dies speichert die zeitaufwändige Schritte verallgemeinern und das gesamte Bild Neuaufnahme und ermöglicht es Ihnen, schnell BTO Geräte bereitstellen.

### <a name="language-packs"></a>Language packs

Anstatt vollständige Language Packs, sparen Sie Platz durch Hinzufügen, dass die benötigten Ressourcen für das Gerät desktop durch Auswählen der einzelne Paketen für Zeichenfolgen, Handschrift, Sprache und Sprachausgabe anzuzeigen. Später, wenn Ihre Benutzer zusätzliche Sprachfunktionen benötigt, können Windows die Pakete Bedarf herunterladen. 

Sprache und regionale SKU Entscheidungen können die Datenträger Speicherbedarf und die Komplexität des Systems Erstellung Bild erheblich beeinträchtigen. Vorsicht werden zur Begrenzung der Umfang und die Typen von Sprachpaketen mit jedem Bild enthalten. 

Mobilen Geräten verwenden ein weltweit Bild, sodass alle Sprachen in jedes Bild enthalten sind.

### <a name="driver-co-installers"></a>Treiber Co-Installer

Treiber sind in der Regel ein sehr kleine Teil der Datenträger Speicherbedarf, jedoch die gemeinsame Installer oder Desktopgerät apps, die die Treiber begleiten können Hunderten von Megabyte. Überlegen Sie sich, wenn die Geräte die zugehörige klassische Windows-Anwendung voll funktionsfähig sein muss.

### <a name="hardware-components"></a>Hardware-Komponenten

Hardware Entscheidungen können auch den Fertigungsprozess beeinträchtigen. Neben der Herausforderungen auf die physischen Assembly der Hardware kann der Inklusion oder Ausschluss von bestimmten Geräten den Factory-Prozess erschweren. Für beispielsweise Touch-Bildschirme und Sensoren eingebunden werden, müssen sie auf jedem Gerät kalibriert werden. Wenn Sie Geräte wie Ethernet-Ports ausschließen, können nicht Sie PXE-Start verwenden, die zusätzliche Kosten verbunden werden können.

### <a name="antimalware-apps"></a>Modul-apps

**Empfehlung:** Konfigurieren Sie Ihre Geräte zur Vermeidung von vollständigen Scan der Datenträger während der ersten Anmeldung. Arbeiten Sie mit Ihrem Modul Lieferanten bewährte Methoden für diese Überprüfung limiting bestimmen.

Wir haben gesehen, mehrere Instanzen, in dem Modul-Tools einen vollständigen Datenträger ausführen werden, während der ersten Anmeldung für den Benutzer zu überprüfen. Die Überprüfung konkurriert mit kritische Vorgänge, die während der ersten Anmeldevorgang, wodurch sehr langsam ersten anmelden, ein beeinträchtigter Start Erfahrung und Systemleistung auftreten. 

Für Windows Defender kann dies durch Hinzufügen der eindeutige Bezeichnern zu Ihren Bildern konfiguriert werden. Weitere Informationen finden Sie finden Sie [eine vertrauenswürdige Bild Bezeichner für Windows Defender konfigurieren](http://go.microsoft.com/fwlink/?LinkId=532775).

### <a name="windows-defender"></a>Windows-Defender

## <a name="pre-factory-floor-image-updates"></a>Vor dem factory Floor Image-updates

Goldene Bilder werden in der Regel an übergeben der ODM aus der OEM vor Beginn der Produktion. Diese Bilder erfordern fast immer einige aktualisieren. Wenn Sie das goldene Bild aktualisieren, müssen Sie die Updates auf jedem Gerät ausführen. Dies führt zu weniger Zeit für jedes Gerät werksseitige und Qualität erhöht. 

Updates für das Abbild können Treiber, Windows-Updates, Software, OEM Anpassungen und app-Pakete (.appx) enthalten.

### <a name="considerations"></a>Erwägungen

Wenn Sie Bilder mit – Wartung offline Aktualisieren, müssen Sie regelmäßig die Bilder zu verwalten. Die werksseitige eingesparte Zeit sollte es sinnvoll machen.

### <a name="goals"></a>Ziele

Reduzieren Sie pro Einheit werksseitige Zeitaufwand und verringern Sie der Beträge von Fehlern in Produktion Geräte.

### <a name="implementation"></a>Implementierung

Auf einem System BTO müssen einige optionalen Faktoren und einige apps optional an der Software herunterladen hinzuzufügen, um das Gerät aufzunehmen angewendet werden soll. Diese Änderungen sollten, um die Wahrscheinlichkeit, dass der Fehler verringern und zur Verbesserung der Fertigung Zeit minimiert werden.

### <a name="image-creation"></a>Image-Erstellung

Der Erstellungsprozess insgesamt goldene Desktopimage OEM Bild Übungseinheiten ähnelt der vorhandenen Prozess.

![Golden Image-Erstellungsprozess](images/golden-image-creation-process.png)

Um Kompatibilitätsprobleme zu vermeiden, verwenden Sie die neue Version von Windows PE bei der Arbeit auf dem Gerät Verweis in der Bild-Übungseinheit erstellen. 


### <a name="region-specific-policy-for-skype-removal-on-desktop"></a>Regionsspezifische Richtlinie für Skype entfernen, auf dem desktop

Windows bereitgestellten apps sind standardmäßig in allen Windows-Bilder enthalten. Diese apps können nicht mit Ausnahme von geändert werden, in denen explizit in Windows OEM Richtlinie Dokument (OPD) angegeben.

Wenn Sie zum Entfernen der Posteingang Skype app aufgrund von Anforderungen für erforderlich sind, können Sie das Tool DISM.exe oder DISM Windows PowerShell-Cmdlets verwenden, um die app zu entfernen. Weitere Informationen zu dieser Richtlinie Anforderung finden Sie unter der neuesten OEM Richtliniendokument. 

So entfernen Sie online Skype im Überwachungsmodus unter Windows PowerShell

```syntax
get-provisionedappxpackage -online | where-object {$_.displayname -eq "Microsoft.SkypeApp"} | Remove-ProvisionedAppxPackage -online
```

So entfernen Sie offline Skype mit Windows PowerShell

```syntax
get-provisionedappxpackage -path c:\mount | where-object {$_.displayname -eq "Microsoft.SkypeApp"} | Remove-ProvisionedAppxPackage
```

Entfernen von Skype Dism.exe offline verwenden:

1. Erhalten Sie den vollständige Paketname:

    ```syntax
    Dism.exe /image:<Windows_volume> /get-provisionedappxpackages
    ```
2. Entfernen Sie das Paket mit der <PackageName> aus der Liste Microsoft.SkypeApp:

    ```syntax
    Dism.exe /image:<Windows_volume> /remove-provisionedappxpackage /PackageName:<PackageName>
    ```
    
Es wird empfohlen, die Windows-10-Version von Windows Vorinstallation Environment (Windows PE) verwenden.

Hinweis: Wenn Sie über die Windows 8-Version von Windows PE verwenden, müssen nach allen Vorgängen zum Warten, Sie den Zeitstempel der Dateien aktualisieren; Andernfalls können Sie nicht das Bild mit der Lizenzierung OEM Activation 3.0-Methode aktiviert sein. Darüber hinaus meldet Feld in Lizenzierung Diagnosetool licensingdiag.exe, dass das Bild manipuliert wurde. 

Um dieses Problem zu beheben, nachdem alle Vorgänge zum Warten von der Windows 8-Version von Windows PE ausgeführt, muss der OEM ausgeführt: 

```syntax
dir %windir%\System32\catroot\{F750E6C3-38EE-11D1-85E5-00C04FC295EE}
```

### <a name="language-pack-updates"></a>Updates für Language Packs

Nach der Installation einer neuen Sprache, müssen Sie alle APPX fasst und Posteingang Windows apps zur Unterstützung der neuen Sprachen installieren. Andernfalls wird nicht die APPX fasst Unterstützung für die neuen Sprachen enthalten.

### <a name="apps-in-audit-mode"></a>Apps im Überwachungsmodus aktiviert

Nach der Installation einer neuen Sprache, müssen Sie alle APPX fasst und Posteingang Windows apps zur Unterstützung der neuen Sprachen installieren. Andernfalls wird nicht die APPX fasst Unterstützung für die neuen Sprachen enthalten.

Um den app-Bereitschaft Dienst offline zu deaktivieren:

1.  Erstellen einer REG-Datei, in dem HKLM\Software\Microsoft\Windows\CurrentVersion\AppReadiness DisableInAuditMode auf einen Wert von 1 festgelegt ist.
2.  Stellen Sie das Windows-Abbild. Beispiel:
    
    ```syntax
    Dism /Mount-Image /ImageFile:"C:\Images\ModelSpecificImage.wim" /Name:"Fabrikam" /MountDir:"C:\mount\windows" /Optimize
    ```
    
3.  Die Registrierungsstruktur zu laden. Beispiel:
    
    ```syntax
    reg load hklm\LoadedHive C:\mount\Windows\System32\config\SYSTEM
    ```
    
4.  Fügen Sie den Registrierungswert hinzu. Verwenden von REG-Datei aus Ihrem USB-Stick beispielsweise:
    
    ```syntax
    regedit /s e:\registry\regFile.reg
    ```
    
5.  Entfernen der Struktur.

    ```syntax
    reg unload hklm\LoadedHive
    ```
    
6.  Heben Sie die Bereitstellung des Windows-Abbilds geändert. Beispiel:

    ```syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```
    
Es wird empfohlen, dass Sie den Dienst offline deaktivieren, bevor Sie im Überwachungsmodus eingeben. Jedoch können sie online im Überwachungsmodus auch deaktivieren. Sie müssen das Bild verallgemeinern, nachdem Sie den Dienst deaktivieren.
App-Bereitschaft Dienst zu deaktivieren:

1. Starten Sie im Überwachungsmodus aktiviert, `regedit`.
2. Navigieren Sie zu HKLM\Software\Microsoft\Windows\CurrentVersion\AppReadiness DisableInAuditMode. 
3. Legen Sie den Wert des Schlüssels auf 1 fest.

Ausführen von Sysprep verallgemeinern bevor Sie fortfahren.

## <a name="smt-assembly-phase"></a>SMT / Assembly Phase

Geräte müssen Kunden am besten kalibriert werden und die Windows Hardware Lab Kit Tests zu übergeben.

### <a name="implementation"></a>Implementierung

- Kalibrierungen
    - Sensoren
    - Touchpad
    - Touchscreen
    - RF
    - Kamera

Festlegen der Uhrzeit in UTC und ACPI Änderungen folgenden beschriebene implementieren.

## <a name="hardware-test-and-run-in-phase"></a>Testen und fortlaufender phase

Es wird empfohlen, Tests auf eine vollständige Version von Windows. Auf diese Weise können Sie die endgültige Hardware und Software Interaktionen zu testen, wie der Benutzer werden.

### <a name="considerations"></a>Erwägungen

Die Vollversion von Windows, die Sie mit den Protokollversand werden werden ermöglicht testen und Überprüfung in der genauen gleichen Umgebung, die der Endbenutzer sehen werden. Windows PE ist kein unterstütztes Betriebssystem für Test – nur als ein Fahrzeug Bereitstellung verwendet werden soll.

### <a name="goals"></a>Ziele

Stellen Sie Produkte höchsten Qualität und Fertigung Zeiten unter der Absolute minimale weiterhin möglich zu.

### <a name="implementation"></a>Implementierung

Die Installation des Tests OS kann verschiedene Arten behandelt werden. Da der Test OS weniger Fluktuationsrate hat als den Versand OS auf das Bild auf dem Datenträger zu einem beliebigen Zeitpunkt vorgesehenen werden können, die die Zeitspanne beeinträchtigen können Anwenden des Abbilds werksseitige ausgegeben. Optionen gehören, müssen vor dem geblinkt von unabhängigen Hardwarehersteller, oder mithilfe von Duplizierung auf Website.

**Wichtig**: Wenn einer Test OS, um sicherzustellen, dass beide eine gute Leistung und sicherstellen, dass der Benutzer OS Starts des Moduls besitzt deaktivieren TPM (Trusted Platform Module) automatische Bereitstellung. Zu diesem Zweck in Windows müssen Sie die folgenden Registrierungsschlüsseln festlegen: 

```syntax
[HKLM\System\CurrentControlSet\Services\Tpm\WMI\NoAutoProvision] (REG_DWORD) to 1
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\TPM\WMI]
"NoAutoProvision"=dword:00000001
```

## <a name="software-download-phase"></a>Phase der Software-download

### <a name="considerations"></a>Erwägungen

Sollte geachtet werden, die für diese Phase aufgewendete Zeit minimieren. Während einige langer Dauer (beispielsweise BTO Anpassungen) werden, empfehlen wir unsere Partner zum Berechnen der Kosten im Vergleich zu Benfits optimiert so weit wie möglich. 

### <a name="goals"></a>Ziele

Erstellen Sie ein effizientes und ausfallsicheres imaging-System mit minimalem Aufwand. Verschieben Sie so viele Schritte wie möglich auf Pre-Factory Floor Image-Updates. 

### <a name="implementation"></a>Implementierung

1. Starten Sie den Computer zu einer Windows PE. Zum Bereitstellen von Compact OS müssen Sie die Windows-10-Version von Windows PE verwenden. Sie können Windows PE auf verschiedene Arten starten:

    - Verwenden von PXE
    - Verwenden einen USB-stick
    - Vorinstallieren von Windows PE auf der Festplatte 
    
2. Erstellen Sie die Festplatte Partition-Struktur mit Diskpart. 

    ```syntax
    diskpart /s F:\CreatePartitions-UEFI.txt
    ```
    
    Weitere Informationen finden Sie unter [UEFI, GPT-basierten Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md)
    
3. Anwenden der Bilder, die Sie erstellt haben, mithilfe von DISM in der Windows-Partitionen. 

    ```syntax
    ApplyImage F:\Images\ThinImage.wim
    ```
    
    Weitere Informationen finden Sie unter [Capture und Anwenden von Windows, System, und Recovery-Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).
    
    Optional: Verwenden Sie dasselbe Bild als Image-Wiederherstellung auf einem separaten USB flash-Laufwerk. USB-Datenträger muss nicht mehr aus einer autorisierten Replicator stammen. Weitere Informationen finden Sie unter [Create Media Drucktaste auszuführenden zurücksetzen Features](create-media-to-run-push-button-reset-features-s14.md).

4.  Starten Sie das Gerät im Überwachungsmodus aktiviert.

    - Nehmen Sie eine beliebige endgültige Bild Änderungen vor. Dies ist, auf dem viele BTO Änderungen vorgenommen werden.
    - Wenn APPX apps installiert wurden, bevor Sie zusätzliche Language Packs hinzugefügt wurden, neu installieren Sie apps, damit die neuen Sprachen unterstützt werden können. Dazu gehören Posteingang Applications. 
    - Microsoft empfiehlt dringend empfohlen, dass OEMs DISM mit der /StartComponentCleanup /resetbase Flags um zusätzlichen freien Speicherplatz zu erhalten ausgeführt.
    - Stellen Sie sicher, dass .NET Framework-apps kompiliert werden, indem Sie die folgenden Befehle ausführen
        
        ```syntax
        C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe update /queue
        C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe eqi
        ```
        
        Führen Sie die gleichen für 64-Bit-CLR an, auf 64-Bit-Computern:

        ```syntax
        C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngen.exe update /queue
        C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngen.exe eqi
        ```
        
    - Erstellen Sie den OA3 Computer Buildbericht (CBR) mithilfe von OAtool.exe, fügen Sie den Schlüssel in der Firmware und überprüfen Sie die Bereitstellung zu.
    - Wenn Sie Windows-Vorinstallation-Umgebung (Windows PE) nutzen 5.x, korrigieren Sie die Zeitstempel. (Dieser Schritt ist nicht erforderlich, wenn Sie Windows PE für Windows 10 verwenden).

        ```syntax
        dir %windir%\System32\catroot\{F750E6C3-38EE-11D1-85E5-00C04FC295EE}
        ``` 
        
    - Führen Sie Sysprep/OOBE, um das System für den Endbenutzer vorzubereiten.
    - Aktivieren Sie Secure Boot (sofern implementiert).
 
## <a name="quality-assurance-phase"></a>Qualität Assurance phase

Qualität sollte ausgeführt werden, auf einem Computer in der Produktion ausführen, um sicherzustellen, dass alle Anpassungen erfolgreich installiert wurden. In dieser Phase QA sollte auch auf die Überprüfung der OA3 Implementierung verwendet werden.

### <a name="considerations"></a>Erwägungen

Nachdem das System OOBE für diese Phase QA durchlaufen wurde, muss er zurückgesetzt werden, um sicherzustellen, dass durch der Endbenutzer hervorragend ist. 

### <a name="goals"></a>Ziele

Gewährleisten Sie einen gute Kundenzufriedenheit zu, und reduzieren Sie die Zeit für Wiederherstellung Computer.

### <a name="implementation"></a>Implementierung

Das Gerät sollte in die Produktion Zeile erneut abgebildeten werden zurückgegeben.

## <a name="remanufacturing"></a>Remanufacturing

Nachdem das Gerät über OOBE (für die aus irgendeinem Grund) übergeben wurde muss das Gerät zu einem neuen Image versehen werden. Bei der Herstellung kann das Gerät einfach wieder bei der Software herunterladen Station hinzugefügt werden, nachdem das TPM (sofern ausgestattet) gelöscht wurde. 

An, wenn das Gerät in einem muss Feld von einem 3rd Partei und dann Schaltfläche Zurücksetzen sollte verwendet werden. Dadurch wird sichergestellt, dass der Computer wieder an die vollständigen Factory Konfiguration bleiben Sie immer noch einfach auszuführen zurückgegeben wird. 

### <a name="considerations"></a>Erwägungen

Während PBR alle Funktionen für Factory remanufacturing erforderlich ist, bietet die Möglichkeit, die Aktionen Skript keine und bietet keine bearbeitungsfähige Fehlercodes, die für die Automatisierung, die in der Produktion im großen Maßstab erforderlich wäre benötigt.

### <a name="goals"></a>Ziele

Vergewissern Sie sich einen gute Kundenzufriedenheit beim Schützen der Benutzerdaten.

### <a name="implementation"></a>Implementierung

Deaktivieren Sie das TPM verwenden Sie die folgenden Befehle:

```syntax
$Tpm = Get-WmiObject -class Win32_Tpm -namespace "root\CIMv2\Security\MicrosoftTpm"
$Tpm.SetPhysicalPresenceRequest(22)
```

Wenn Sie Windows PE verwenden, benötigen Sie ein benutzerdefiniertes Windows PE-Abbild mit:

- SOC-spezifische Treiber für Ftpm.
- Optionale Komponenten: SecureStartup, WMI, PowerShell und .NET Framework.

## <a name="manufacturing-checklist"></a>Fertigung Prüfliste

### <a name="windows-10-manufacturing-task-timeline"></a>Windows-10 manufacturing Aufgabe Zeitachse

Diese Prüfliste können Sie Ihre Produktion Aufgaben planen.

<table width="97%">
<thead>
<tr>
<td>
<p><strong>Aufgabe</strong></p>
</td>
<td>
<p><strong>Älter als Version EV phase</strong></p>
</td>
<td>
<p><strong>EV phase</strong></p>
</td>
<td>
<p><strong>DV-phase</strong></p>
</td>
<td>
<p><strong>PV-phase</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td>
<p><strong>Erforderliche Fertigung Arbeit:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>ODM entschieden?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>OEM Zugriff auf Windows&nbsp;10?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Zugriff auf Windows ODM&nbsp;10?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>OEM-Zugriff auf Manufacturing WEG?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Zugriff auf Manufacturing WEG?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Punkt des Kontakts erkannt?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>OEM Punkt des Kontakts erkannt?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM-Kickoff?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>OEM-Kickoff?</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Reguläre Fertigung Anruf?</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p><strong>Bereitstellung:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>OEM Verständnis der Konzepte der Bereitstellung</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Verständnis der Konzepte der Bereitstellung</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Verwenden von Windows&nbsp;10 DISM</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Verwenden von Windows&nbsp;10 Windows PE</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Erweiterte Attribute über DISM angewendet</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>WinSxS überprüft, die ausgeführt werden? / AnalyzeComponentStore</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Bild wird bereinigt? (DISM /Cleanup-Image /StartComponentCleanup /ResetBase)</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Drucktaste zurücksetzen</p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>OEM Verständnis der Konzepte Drucktaste zurücksetzen</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Verständnis der Konzepte Drucktaste zurücksetzen</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Empfohlene Partitionslayout für Windows RE und Drucktaste zurücksetzen?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Wenn eine nicht standardmäßige Partitionslayout verwendet wird, ist bare-Metal-Wiederherstellung konfiguriert?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Bild ACL-wiederherstellungseinstellungen beheben?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Aktualisieren/zurücksetzen Zeit ist innerhalb von Richtlinien?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
</tr>
<tr>
<td>
<p><strong>Windows RE:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>OEM-Kenntnisse über Windows RE-Konzepte</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Verständnis der Windows RE-Konzepte</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Windows RE ist aktiviert.</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Windows RE-Speicherort ist richtig.</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>BCD-GUID für Windows RE entspricht Windows RE-GUID-Eintrag in Reagent.xml</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Bildindex ist korrekt.</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p><strong>Fertigung:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>Windows RE Partitionsgröße (MB) und Position auf dem ausgewählten Datenträger</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Test-Partition verwendet vollständige Windows</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Image-Bereitstellung über [NIC] oder [Duplizierung]</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>OPM wichtige Bereitstellung planen fertig?</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Sprachpakete pro SKU</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p><strong>Sichere Boot:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>OEM Verständnis der Sicherheitskonzepte</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>ODM Verständnis der Sicherheitskonzepte</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Sichere Startvorgang mit vor der Produktion Signieren getestet?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Wasserzeichen deaktiviert?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
</tr>
<tr>
<td>
<p>Treiber signiert von IHV/ISV?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
</tr>
<tr>
<td>
<p>Von Microsoft signierte Treiber?</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
</tr>
<tr>
<td>
<p>Erneutes manufacturing Prozess abgeschlossen [Factory]</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Erneutes manufacturing Prozess abgeschlossen [Service Feld]</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Secure Boot und Debuggen von FT überprüft Richtlinie Pläne</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>-</td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p><strong>BEI 3.0 ZUGRIFF:</strong></p>
</td>
<td>
<p><strong>Älter als Version EV</strong></p>
</td>
<td>
<p><strong>EV</strong></p>
</td>
<td>
<p><strong>DV</strong></p>
</td>
<td>
<p><strong>BW</strong></p>
</td>
</tr>
<tr>
<td>
<p>Verwenden die aktualisierte OA3tool.exe</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Überprüfen des Image/offline-Taste</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
<tr>
<td>
<p>Einfügung in durchgeführt`[Windows PE][Windows]`</p><p>Finden Sie im Abschnitt OEM Activation 3.0.</p>
</td>
<td>
<p>-</p>
</td>
<td>
<p>-</p>
</td>
<td><img src="https://i-technet.sec.s-msft.com/en-us/itpro/windows/manage/images/checkmark.png" alt="supported" /></td>
<td>
<p>-</p>
</td>
</tr>
</tbody>
</table>

## <a name="appendix"></a>Anhang

### <a name="small-disk-footprint-optimization"></a>Kleine Datenträger Bilanz Optimierung

Die Basisdatenträger Speicherbedarf von Windows 10 X86 mit Office und 2 GB RAM enthält: 

<table width="97%">
<tbody>
<tr>
<td>
<p>Windows (w/Office), Seite Datei, Hiberfile, Auslagerungsdatei und zwei Language packs</p>
</td>
<td>
<p>11.7 GB</p>
</td>
</tr>
<tr>
<td>
<p>WinRE</p>
</td>
<td>
<p>500MB</p>
</td>
</tr>
<tr>
<td>
<p>Systempartitionen (MSR, ESP)</p>
</td>
<td>
<p>428MB</p>
</td>
</tr>
<tr>
<td>
<p>Insgesamt</p>
</td>
<td>
<p>~ 23GB</p>
</td>
</tr>
<tr>
<td>
<p>Verfügbare Platz für OEM-Anpassungen auf einem Gerät 32GB (29GB verfügbar)</p>
</td>
<td>
<p>~ 6GB</p>
</td>
</tr>
</tbody>
</table>

Annahmen:

- Datenträger-Bilanz mit GetDiskFreeSpaceEx() berechnet 
- Daten werden sofort nach der Installation OS vor NGEN ausgeführt, bevor Sie Aufgaben im Leerlauf erfasst. 
- Messung enthält Auslagerungsdateien
- Windows Update ist deaktiviert.
- Build verfügt über mehrere ausgeführt wird. in diesem Bericht wird die max-Bilanz verwendet.
- Kapazität wird in Basis 2 Größen: 32 GB konvertiert == 32,000,000,000 Bytes == 30518MiB (oder 29GiB).

### <a name="language-packs"></a>Language packs

Language Packs umfassen einige der größten Datenträger Speicherplatz Ergänzungen OEM stellen wahrscheinlich ist. Eine Sprache mit alle optionalen Komponenten enthalten kann schätzungsweise 275MB (Größe variiert basierend auf Sprache) während der Language Packs für Office auf 300 MB (auch je nach Sprache) geschätzt werden können.

Windows wird nicht verwendeten Sprachpakete erhöhen, nachdem der Endbenutzer eine primäre Sprache während OOBE ausgewählt hat. Nachdem sie entfernt werden, werden nicht diesen Sprachen Drucktaste zurücksetzen verfügbar sein.

Um einen kleineren Datenträger Speicherbedarf zu gewährleisten, sollten Sie auf jedem des Protokollversands SKU installierten Sprachen zu reduzieren. 

### <a name="servicing"></a>– Wartung

Hinzufügen von Windows Update KB Paketen kann die Größe des Datenträgers erheblich hinzufügen. Der Speicherbedarf von einem Bild nach dem Hinzufügen von Updates zu reduzieren:

1.  Installieren Sie KB und neu starten Sie, wenn Sie dazu aufgefordert werden
2.  Führen Sie von einer Eingabeaufforderung mit erhöhten Rechten die folgenden Befehle ein:

    ```syntax
    dism.exe /online /cleanup-image /startcomponent
    ```
    
3.  Starten Sie das Gerät neu.

### <a name="real-time-clock-rtc"></a>Echtzeit Uhr (RTC)

Die RTC ist eine batteriegepufferten Zeitquelle, die gespeichert und verwaltet Systemzeit, wenn ein Gerät ausgeschaltet. ACPI 5.0 definiert das Uhrzeit- und Alarm Gerät, das zugrunde liegenden Hardwaregeräts abstrahiert die Plattform Zeit verwaltet. Das Gerät ACPI Uhrzeit- und Alarm ist die bevorzugte Methode zum Festlegen und Plattform Abfragezeit unter Windows, auch auf einem System mit einer herkömmlichen CMOS RTC basiert. Die ACPI-Schnittstelle bietet den Zeitunterschied für den Zeitwert von abgerufen oder in der Gruppe RTC geschrieben. Dieses Feld zusätzliche Informationen Adressen basierend ein langjähriger Problem mit CMOS RTC, wobei ein Betriebssystem wie interpretiert werden die von der Hardware Uhr lesen Zeit nicht bekannt ist.

#### <a name="factory-floor-considerations"></a>Factory Floor Aspekte

Windows-Abfragen RTC Aktualisierung des Systems Uhrzeit:

- Es ist keine Synchronisierung Zeitdienst verfügbar.
- Der Computer gibt dem Standbymodus (S3) oder Ruhezustand (S4) Power Zustand.
- Kernel-Debugger ist aktiviert. 

OEMs richten Sie die RTC in die Ortszeit (LT) in der Regel für Geräte, die im Lieferumfang von Windows 7. Windows 7 verwendet die CMOS Zeit-Schnittstelle ausschließlich um RTC-Zeit abzurufen, die als LT. interpretiert wird In Windows 8 Unterstützung für die ACPI Uhrzeit- und Alarmgerät wurde hinzugefügt, jedoch Windows 8 verwendet auch das CMOS RTC, wenn es verfügbar ist, und die Zeit als LT. zurückgegebenes behandelt Dieses Verhalten (im Zusammenhang mit der CMOS RTC-Schnittstelle) ist nicht kompatibel mit den meisten nicht-Windows-Betriebssystemen. Darüber hinaus möchten Hostinganbieter wie Azure verwenden UTC-Zeit in ihrer virtualisierten Hardware zur Vereinfachung der Verwaltung und Migration von Gästen, die möglicherweise eine Anzahl von unterschiedlichen Zeitzonen müssen. 

Um diese Probleme zu beheben, wird Microsoft Weg mithilfe der CMOS RTC-Benutzeroberfläche und vertrauende Seite in erster Linie für die ACPI Zeit- und Alarmgerät Übergang werden. 

Für OEMs finden Sie die Richtlinien:

- Implementieren Sie das Gerät ACPI Uhrzeit- und Alarm.
- Legen Sie "CMOS RTC nicht vorhanden" Flag in festen ACPI Beschreibung Tabelle (FADT). Die zugrunde liegende Hardware kann weiterhin sein, CMOS RTC; gesicherten jedoch Windows nur die ACPI Uhrzeit- und Alarmgerät verwendet wird, wenn dieses Flag festgelegt ist.
- Es ist nicht für die Plattform Firmware so aktualisieren Sie die RTC über eine Grenze für die Sommerzeit empfohlen. Wenn es, jedoch muss die Firmware sicherstellen koordinierte Weltzeit (UTC) kann immer berechnet werden, indem Sie die Time-Wert, d. h., UTC den Zeitunterschied hinzufügen = LT + TZ. Windows ignoriert Feld Sommerzeit aus der Steuerelement-Methode _GRT empfangen. 
- TZ (auf 0x7FF festgelegt) über Firmware ungültig, wenn RTC Mal jemals über CMOS RTC-Schnittstelle aktualisiert wird. 

### <a name="ensuring-a-good-first-sign-in-experience"></a>Sicherstellen, dass eine gute erste Anmeldung

Das Windows-Team hat eine Reihe von Problemen, die eine gute Leistung des Benutzers die erste Version von Windows-Blockierung sichtbar, und die folgende Hinweise sollen beheben Sie gängige Probleme bei der Vorbereitung von OS Bilder für Ihre Kunden. 

#### <a name="antimalware-tools-scanning-disk-during-first-sign-in"></a>Modul Tools Scannen Datenträger während der ersten Anmeldung

Wir haben gesehen, mehrere Instanzen wobei Modul-Tools einen vollständigen Datenträger machen Scannen während der ersten Anmeldung für den Benutzer. Das Scannen konkurriert mit kritische Vorgänge, die während der ersten Anmeldevorgang, was sehr langsam ersten anmelden, ein beeinträchtigter Start Erfahrung und Systemleistung auftreten. 

**Empfehlung**: Geräte sollte so konfiguriert werden, dass um vollständige Überprüfung des Datenträgers während der ersten Anmeldung zu vermeiden. Spezifische Leitfäden für a/v-Lösungen sollte vom a/v Lieferanten bereitgestellt werden. 

#### <a name="windows-defender"></a>Windows Defender

Fügen Sie eindeutige Bezeichner zu Ihren Bildern, um zu verhindern, dass Windows Defender erneut Scannen aller Dateien, die Sie in der ursprünglichen Festplattenabbild bereitgestellt. Weitere Informationen finden Sie finden Sie [eine vertrauenswürdige Bild Bezeichner für Windows Defender konfigurieren](http://go.microsoft.com/fwlink/?LinkId=532775).

#### <a name="running-ngen-commands"></a>NGEN-Befehle ausführen

Systemeigene Bild GENeration ist eine Aufgabe Kompilieren der .NET Framework MSIL (virtueller Computercode) in systemeigene Bilder (Plattform bestimmte ausführbare Dateien). Im Allgemeinen wird CLR Startzeit der Anwendung von mehr als eine Reihenfolge erheblich verbessert. Einzelheiten finden Sie unter [Der Leistung Vorteile von NGen](http://go.microsoft.com/fwlink/?LinkId=532790) . 

**Empfehlung**: befolgen Sie diese Anweisungen, um sicherzustellen, dass .NET Framework-apps kompiliert werden. Führen Sie nach der Installation von Updates für alle OS die folgenden Befehle ein: 

Klicken Sie auf 32-Bit-X86 oder ARM-Geräte:

```syntax
C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe update /queue
C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe eqi
```

Auf 64-Bit-Geräte Dies gilt für beide Versionen von .NET Framework:

```syntax
C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe update /queue
C:\Windows\Microsoft.NET\Framework\v4.0.30319\ngen.exe eqi
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngen.exe update /queue
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngen.exe eqi
```

#### <a name="graphics-drivers"></a>Graphics-Treiber

Die richtige DirectX Graphics-Treiber für die Hardware sollte im Lieferumfang von Windows-Gerät. Um den richtigen Treiber zu installieren, die Fehler aufweisen erzeugt ein Fallback auf eine softwarebasierte Graphics-Treiber. Dies führt zu beeinträchtigter Erfahrungen mit Windows, einschließlich der ersten Anmeldung Leistung.

**Empfehlung**: Installieren den richtigen Graphics-Treiber für Ihre Hardware im Überwachungsmodus.

### <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

#### <a name="windows-pe"></a>Windows PE

- **Frage**: kann ich die neue Windows PE zum Bereitstellen, verwalten und frühere Versionen von Windows-service verwenden?

    **Antwort**: Updates für Windows PE wirkt sich nicht auf die derzeit unterstützten Windows-Versionen. Die aktualisierte Windows PE können Sie die vorherige Windows-Versionen, einschließlich Windows 7 bereitstellen.

-   **Frage**: haben zum Migrieren zu der neuen Bereitstellungstools als Teil des Windows-10?

    **Antwort**: Nein Sie nicht. Sie müssen nur auf eine neuere Version der Bereitstellungstools (Windows PE, DISM) zu aktualisieren, wenn Sie Compact OS implementieren möchten.

- **Frage**: wie wirkt sich dieser Datenträger Bilanz Optimierung auf Meine PXE-Umgebung?

    **Antwort**: Sie müssen nur der PXE-Umgebung auf eine neuere Version der Bereitstellungstools (Windows PE, DISM) zu aktualisieren, wenn Sie ein "apply" in der PXE-Umgebung ausgeführt werden. Wenn Sie nur einen Download (Kopieren von Dateien vom Server an Client) ausgeführt werden, müssen Sie Ihre PXE-Umgebung zu aktualisieren.

#### <a name="push-button-recovery-pbr-and-windows-recovery-environment-winre"></a>Drucktaste Wiederherstellung (PBR) und Windows Recovery Environment (WinRE)

- **Frage**: Will WinRE ebenfalls aktualisiert werden?

    **Antwort**: Ja, wird eine neue WinRE.wim benötigt.
    
- **Frage**: kann der Benutzer weiterhin erstellen Sie einen PBR USB Schlüssel?

    **Antwort**: Ja. Wenn das Standardlayout Partition verwendet wird, ist keine zusätzliche Einrichtung vom OEM erforderlich um dies zu ermöglichen.

#### <a name="storage"></a>Storage

- **Frage**: solid-State-Datenträger werden nur unterstützt?

    **Antwort**: Nein, wir nun Solid-State und herkömmliche Rotation Medien unterstützen. Es wird empfohlen, Single instancing nur auf Solid-State-Datenträgern aufgrund von Leistungsproblemen verwendet wird.

- **Frage**: kann ich verwenden, Single instancing von provisioning Pakete auf einer Konfiguration mit zwei Datenträger (HDD + SSD)?

    **Antwort**: Single instancing kann nur auf demselben Datenträger implementiert werden.
    
#### <a name="disk-footprint"></a>Datenträger-Bilanz

- **Frage**: wie löschen Sie die Sprachpakete, die der Benutzer nicht während OOBE ausgewählt werden?

    **Antwort**: die Language Packs vom Gerät gelöscht werden, und wird bei Drucktaste Wiederherstellungsoperationen nicht mehr verfügbar sein.
    
- **Frage**: wie Sie Datenträgergröße berechnen? Melden Sie beispielsweise eine Größe von 14.8 GB auf einem Datenträger 16 GB.

    **Antwort**: die Speicherkapazität wird in Basis 2 konvertiert. Beispielsweise ist 16,000,000,000 (Milliarden Bytes) ~14.8 GB gleich.

- **Frage**: kann ich nur verwenden Compact OS auf kleinen Geräten, beispielsweise mit 1 GB RAM und 16 GB-Datenträger?

    **Antwort**: Compact OS angewendet werden soll, auf eine beliebige 32-Bit oder 64-Bit-Plattform mit > = 16 GB solid State-Speicher.

- **Frage**: empfehlen Sie 16 GB-Datenträger auf einer 64-Bit-Plattform unter 64-Bit-Windows verwenden?

    **Antwort**: Es wird eine minimale Kapazität von 32 GB empfohlen, für 64-Bit-Windows. 

#### <a name="imaging-and-deployment"></a>Imaging und Bereitstellung

- **Frage**: Was sind die Änderungen an den Befehl DISM Compact OS unterstützt?

    **Antwort**: können DISM /Apply-Image... Konvertierte und /Apply-CustomDataImage. Weitere Informationen finden Sie unter [DISM Image Management Command-Line Options](http://go.microsoft.com/fwlink/?LinkId=532791).

- **Frage**: unterstützt Compact OS GPT- und MBR Partitionslayout?

    **Antwort**: Ja.

- **Frage**: ist ein aktualisiertes OA3-Tool mit Windows 10 erforderlich?
    
    **Antwort**: Ja.

- **Frage**: kann ich noch mithilfe von Windows SIM, Antwortdateien und Einstellungen mit Windows 10 unbeaufsichtigten?

    **Antwort**: Ja, obwohl möglicherweise einige Einstellungen geändert. Finden Sie unter [geänderte Antwort dateieinstellungen aus Windows 8.1 und Windows Server 2012 R2](http://go.microsoft.com/fwlink/?LinkId=532812).

#### <a name="language-packs-and-apps"></a>Language Packs und apps

- **Frage**: kann mehrere Sprachpakete verwendet?

    **Antwort**: Ja, jedoch wird dringend empfohlen, den Datenträger Bilanz Auswirkungen der Anzahl von Sprachen (Windows, Office, Treiber und apps) pro Bild zu überprüfen. 

- **Frage**: Gibt es eine Änderung in wie ich Language Packs installieren?

    **Antwort**: Ja, wenden die Basis lp.cab auf die gleiche Weise wie vor, um mehrere Benutzeroberflächenoptionen erhalten möchten, aber möglicherweise Text eingeben oder Unterstützung erhalten möchten, Sie optional Sprachkomponenten hinzufügen müssen. Weitere Informationen finden Sie unter [Hinzufügen von Language Packs auf Windows](http://go.microsoft.com/fwlink/?LinkId=532792).
    
- **Frage**: Gibt es eine Änderung in wie ich Desktop- oder Windows Store-apps installieren?

    **Antwort**: keine Änderung im wie Desktop oder Windows Store-apps aus Windows 8.1 installieren.

- **Frage**: Was ist die Benutzeroberfläche auf einer mehrsprachigen Konfiguration oder wenn ein Benutzer eine zusätzliche Language Pack hinzugefügt?

    **Antwort**: Sprachpakete weiterhin die gleiche Weise wie funktionieren diese in früheren Versionen von Windows.
    
- **Frage**: Gibt es Probleme mit der Anwendungskompatibilität mit desktop-apps?

    **Antwort**: der Typ des apps, die unten aufgeführten sorgfältig überprüft werden müssen. 
    
    - Vollständige Volume-Verschlüsselungstools sollten WIM-Images zum Beschränken der Auswirkung auf die Leistung nicht verschlüsselt werden. Solche Tools sollten Überprüfung der Integrität von der unverschlüsselte WIM um Manipulation zu verhindern.
    - Alle Tool, mit dem Systemdateien schreibt kann betroffen sein:
        - Imaging-Applications sollten auf Blockebene sichern und Wiederherstellen von ALLEN Datenträgern durchführen.
        - Fehlerhafte/unvollständig Wiederherstellungsvorgänge können ein System nicht startbaren gerendert werden.
        - Verschlüsselung/Back-nach-oben/Defragmentierung Tools möglicherweise versehentlich Systemdateien vergrößert werden soll. 

- **Frage**: gilt Compact OS auch für die Windows Embedded?

    **Antwort**: die Compact Implementierung und Feature Betriebssystementwurf wir shared Windows 10 für desktop Edition (Start, Pro und Enterprise) beschränkt ist. Allerdings sollten Sie Ihr Windows Embedded Ansprechpartner und informieren Sie sich über einen Plan für die Datenträger Bilanz Optimierung.

#### <a name="policy"></a>Richtlinie

- **Frage**: Gibt es eine Änderung an vorhandenen 10 GB freier Festplattenspeicher Richtlinie erforderlich? 

    **Antwort**: Verweisen auf die aktualisierte Windows Compatibility Hardwareanforderungen.

#### <a name="servicing"></a>– Wartung

- **Frage**: wie vor allem bei der Wiederherstellungsabbild mit Datenträger Bilanz Optimierung Arbeit aktualisiert?

    **Antwort**: Upgrade sind weiterhin funktionsfähig.


