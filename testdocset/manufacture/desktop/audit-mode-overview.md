---
author: Justinha
Description: "Übersicht über Audit-Modus"
ms.assetid: c4d7921f-0709-40bd-bbc5-38fd793d6b88
MSHAttr: PreferredLib:/library/windows/hardware
title: "Übersicht über Audit-Modus"
ms.openlocfilehash: ef245b8febfd1b8c11117aed8cc1e5b03c916467
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="audit-mode-overview"></a>Übersicht über Audit-Modus


Wenn Windows gestartet wird, wird es in beiden Modi Out-Of-Box-Experience (OOBE) oder im Überwachungsmodus aktiviert. OOBE ist die standardmäßige Out-of-Box, die ermöglicht es Endbenutzern, geben ihre Kontoinformationen, wählen Sie Sprache, akzeptieren die Microsoft Terms und Netzwerke einrichten.

Sie können Windows für das Starten im Überwachungsmodus stattdessen konfigurieren. Im Überwachungsmodus aktiviert können Sie zusätzliche Änderungen an der Windows-Installation machen, vor dem Senden des Computers an einen Kunden oder das Bild für die Wiederverwendung in Ihrem Unternehmen erfassen. Sie können beispielsweise in einem Paket enthaltenen Treiber zu installieren, installieren Clientanwendungen oder stellen andere Updates, die die Windows-Installation ausgeführt werden, erfordern. Wenn Sie eine Antwortdatei verwenden, verarbeitet Windows-Einstellungen in den Konfigurationsphasen [AuditSystem](auditsystem.md) und [AuditUser](audituser.md) .

Beim Starten im Überwachungsmodus melden Sie sich an das System über das integrierte Administratorkonto an. Nach der Anmeldung an das System ist das integrierte Administratorkonto der in der Phase der [AuditUser](audituser.md) Konfiguration sofort deaktiviert. Das nächste Mal an, dem dem Neustart des Computers bleibt das integrierte Administratorkonto deaktiviert. Weitere Informationen finden Sie unter [Aktivieren und deaktivieren Sie das integrierte Administratorkonto](enable-and-disable-the-built-in-administrator-account.md).

**Wichtige**  
-   Wenn Sie im Überwachungsmodus aktiviert sind und ein kennwortgeschützte Bildschirmschoner gestartet wird, kann Sie nicht wieder an, um das System anmelden. Das integrierte Administratorkonto, das verwendet wurde, melden Sie sich im Überwachungsmodus wird unmittelbar nach der Anmeldung deaktiviert.

    Um den Bildschirmschoner zu deaktivieren, ändern Sie den Plan Power über die Systemsteuerung entweder oder konfigurieren und Bereitstellen ein benutzerdefiniertes Plans. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Power planen](create-a-custom-power-plan-technicalreference.md).

-   Einstellungen in einer Antwortdatei aus [der Konfigurationsphase](oobesystem.md) werden nicht im Überwachungsmodus aktiviert angezeigt.

 

## <a name="span-idbenefitsofusingauditmodespanspan-idbenefitsofusingauditmodespanspan-idbenefitsofusingauditmodespanbenefits-of-using-audit-mode"></a><span id="Benefits_of_using_Audit_Mode"></span><span id="benefits_of_using_audit_mode"></span><span id="BENEFITS_OF_USING_AUDIT_MODE"></span>Vorteile der Verwendung des Überwachungsmodus


Im Überwachungsmodus aktiviert können Sie Folgendes ein:

-   **OOBE umgehen.** Sie können den Desktop so schnell wie möglich zugreifen. Sie müssen keinen Konfigurieren von Standardeinstellungen wie ein Benutzerkonto, Speicherort und Zeitzone.

-   **Installieren Sie Applications, Hinzufügen von Gerätetreibern und Ausführen von Skripts.** Können Sie eine Verbindung mit einem Netzwerk herstellen und Zugriff auf zusätzliche Installationsdateien und Skripts. Sie können auch zusätzliche Language Packs und Gerätetreiber installieren. Weitere Informationen finden Sie unter [Hinzufügen eines Treibers Online im Überwachungsmodus aktiviert](add-a-driver-online-in-audit-mode.md).

-   **Testen Sie die Gültigkeit einer Windows-Installation.** Bevor Sie das System für Endbenutzer bereitstellen, können Sie die Tests auf dem System durchführen, ohne das Erstellen eines Benutzerkontos. Sie können dann in OOBE beim nächsten Start startet das System vorbereiten.

-   **Fügen Sie weitere Anpassungen auf ein Bild Verweis.** Dadurch wird die Anzahl der Bilder, die Sie verwalten. Beispielsweise können Sie ein Bild für die einzelnen Verweis erstellen mit den grundlegenden Anpassungen, die Sie für alle Windows Bilder anwenden möchten. Sie können das Bild Verweis im Überwachungsmodus, und stellen Sie zusätzliche Änderungen, die speziell für den Computer starten. Diese Änderungen können Kunden angeforderte Applications oder bestimmte Gerätetreiber sein.

## <a name="span-idboottoauditmodespanspan-idboottoauditmodespanspan-idboottoauditmodespanboot-to-audit-mode"></a><span id="Boot_to_Audit_Mode"></span><span id="boot_to_audit_mode"></span><span id="BOOT_TO_AUDIT_MODE"></span>Starten im Überwachungsmodus


Sie können in einer neuen oder vorhandenen Windows-Installation im Überwachungsmodus starten. Weitere Informationen finden Sie unter [Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md).

## <a name="span-idautomaticallydisplaythewindows8desktopspanspan-idautomaticallydisplaythewindows8desktopspanspan-idautomaticallydisplaythewindows8desktopspanautomatically-display-the-windows-8-desktop"></a><span id="Automatically_Display_the_Windows_8_Desktop"></span><span id="automatically_display_the_windows_8_desktop"></span><span id="AUTOMATICALLY_DISPLAY_THE_WINDOWS_8_DESKTOP"></span>Automatisch den Windows 8-Desktop anzeigen


In einigen Windows 8-Startbildschirm Produktion oder testing Szenarien, die müssen Sie möglicherweise den Windows 8 Desktop anstelle der Windows 8 automatisch angezeigt wird, nach dem Neustart des PCs-Option. Dies kann erforderlich sein, wenn Sie Fertigung Tools, Status für ein Fenster auf dem Desktop anzeigen, und Ihre Factory Techniker auf einfache Weise Probleme zu erkennen, ohne dass auf dem Desktop manuell aus dem Windows 8-Startbildschirm geöffnet werden soll.

Sie können automatisch den Windows 8-Desktop anzeigen, indem Sie %windir%\\System32\\Oobe\\AuditShD.exe. AuditShD.exe muss über ein Konto mit Administratorberechtigungen ausgeführt werden.

Es wird empfohlen, als ein RunAsynchronousCommand im AuditUser Konfiguration Durchgang diesem Command-Line zur Antwortdatei hinzufügen. Verwenden Sie Windows System Image Manager Hinzufügens von **Microsoft Windows-Deployment** | **RunAsynchronous** | **RunAsynchronousCommand** mit dem Wert **%windir%\\System32\\Oobe\\AuditShD.exe**.

Die Antwortdatei erstellten sieht etwa wie folgt:

``` syntax
<settings pass="auditUser">
<component name="Microsoft-Windows-Deployment" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <RunAsynchronous>
       <RunAsynchronousCommand wcm:action="add">
          <Description>Show Desktop</Description>
          <Order>1</Order>
          <Path>cmd.exe /c %WINDIR%\System32\oobe\AuditShD.exe</Path>
       </RunAsynchronousCommand>
    </RunAsynchronous>
  </component>
</settings> 
```

Bevor einem Windows 8-PC an einen Kunden geliefert wird, muss Windows so starten Sie den Bildschirmen OOBE und Anzeigen der Startseite beim ersten Start konfiguriert werden. Überprüfen, ob AuditShD.exe ist nur für die Ausführung im Überwachungsmodus konfiguriert und beim OOBE nicht verwendet wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Grundlegendes zu Wartungsstrategien](understanding-servicing-strategies.md)

[Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)

[Funktionsweise von Konfigurationsphasen](how-configuration-passes-work.md)

[Windows-Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md)

[Windows Setup-Installationsvorgang](windows-setup-installation-process.md)

[Übersicht über die Automatisierung von Windows-Setup](windows-setup-automation-overview.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






