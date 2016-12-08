---
title: What&quot;s new in Windows ADK und ADK-tools
description: What&quot;s new in Windows ADK und ADK-tools
Search.SourceType: Video
ms.assetid: EE27ABF7-C197-4E8E-AC1B-77266E2B9FD9
ms.openlocfilehash: 6e407e97f48b2a4ff15d86f8684943598e922f0c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-adk-kits-and-tools"></a>Was ist neu in ADK Kits und tools

## <a name="a-href-idadkawhats-new-in-the-the-windows-adk-for-windows-10-version-1607"></a><a href="" id="adk"></a>Neuigkeiten der die Windows ADK für Windows 10, Version 1607

### <a name="pick-and-choose-desktop-applications"></a>Wählen Sie und desktopanwendungen aus

Mit [Silo provisioning Pakete](manufacture/desktop/siloed-provisioning-packages.md)können Sie jetzt welche desktopanwendungen während der Bereitstellung zu Ihren Bildern hinzufügen wählen. Sie nicht mehr den gesamten Satz von Anwendungen in Ihrer Wiederherstellungsabbild erfassen müssen, sind in automatisch hinzugefügt. Diese Pakete unterstützen Features wie Compact OS und Single instancing Platz zu sparen. 

### <a name="build-iot-core-images-for-large-scale-deployment"></a>Erstellen von IoT Core Bilder für die Bereitstellung im großen Umfang

Erfassen Sie Ihre apps, Treiber und Einstellungen, und stellen Sie diese sicher für neue Geräte. Hier erfahren Sie, wie Sie mit der [Fertigung Führungslinien IoT Core](manufacture/iot/iot-core-manufacturing-guide.md).

### <a name="the-chinese-hong-kong-sar-language-pack-zh-hk-is-no-longer-used"></a>Das Sprachpaket für Chinesisch (Hongkong SAR) (Zh-HK) wird nicht mehr verwendet.

Das Sprachpaket für Chinesisch (Taiwan) (Zh-TW) unterstützt Taiwan und Hongkong Gebietsschemas. Weitere Informationen finden Sie unter verfügbaren Language Packs für Fenster.

### <a name="you-can-limit-access-to-a-single-windows-app-assigned-accesshttpsmsdnmicrosoftcomlibrarywindowshardwaremt620043"></a>Sie können Einschränken des Zugriffs auf eine einzelne Windows-app (zugewiesenen Access)] (https://msdn.microsoft.com/library/windows/hardware/mt620043)

### <a name="new-answer-file-settings-added"></a>Neue Antwort dateieinstellungen hinzugefügt

-  Fügen Sie weitere Kacheln zum Menü Start: Microsoft-Windows-Shell-Setup [| StartTiles | SquareTiles | SquareTiles | SquareOrDesktopTile7](https://msdn.microsoft.com/library/windows/hardware/dn915881) über [SquareOrDesktopTile12](https://msdn.microsoft.com/library/windows/hardware/dn915868)

-  [Erweiterte Stift Einstellungsapp](https://msdn.microsoft.com/library/windows/hardware/mt757353) hinzufügen

-  Ermöglichen eines [in einer Sitzung RAS-Chatfenster](https://msdn.microsoft.com/library/windows/hardware/mt752384)

-  Legen Sie [Automatische Helligkeit Steuerelemente](https://msdn.microsoft.com/library/windows/hardware/dn757391)

-  Finden Sie unter Weitere [neue Antwort Datei-Einstellungen](https://msdn.microsoft.com/library/windows/hardware/mt750416.aspx)

### <a name="mdm-enhanced-device-and-pc-management"></a>MDM: Erweiterte Gerät und PC-Verwaltung

Checken Sie die [neuen Kryptografiedienstanbieter-Einstellungen](https://msdn.microsoft.com/en-us/library/windows/hardware/mt299056(v=vs.85).aspx#whatsnew_1607).

### <a name="more-changes"></a>Weitere Änderungen

Finden Sie unter What's new in [Entwurf](https://msdn.microsoft.com/library/windows/hardware/mt703371.aspx), [Anpassungen](https://msdn.microsoft.com/en-us/library/windows/hardware/mt723363(v=vs.85).aspx), [Fertigung](manufacture/whats-new-in-windows-manufacturing.md).

## <a name="a-href-idadkawhats-new-in-the-windows-adk-version-1511"></a><a href="" id="adk"></a>Was ist neu in der Windows-ADK Version 1511

Windows ADK enthält jetzt [Windows Imaging und Konfiguration Designer](https://msdn.microsoft.com/library/windows/hardware/dn916113.aspx), das [Windows Assessment Toolkit](test/assessments/index.md), das [Windows Performance Toolkit](test/wpt/index.md)und mehrere neue und verbesserte Bereitstellungstools, die Ihnen helfen können Automatisieren einer umfangreichen bereitstellungs von Windows 10.

### <a name="windows-imaging-and-configuration-designer-icd"></a>Windows Imaging und Konfiguration-Designer (ICD)

-   Erstellen Sie schnell eine provisioning-Paket, das Sie zum Anpassen von Geräten ohne imaging erneut verwenden können.
-   Erstellen Sie ein benutzerdefiniertes Windows 10-Abbild bei bestimmten Marktsegmenten und Regionen.

Weitere Informationen finden Sie unter [Erste Schritte mit Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916112.aspx) .

### <a name="push-button-reset-incorporates-system-updates-by-default"></a>Drucktaste zurücksetzen beinhaltet Systemupdates standardmäßig

Benutzer können jetzt aktualisieren oder stellen Sie ihren PCs teilnehmen in der aktualisierten Version der Systemdateien anstelle der jedes Update einzeln neu installieren wieder her.

### <a name="partial-language-packs-now-available"></a>Teilweise Sprachpakete jetzt verfügbar

Möchten Sie weitere Sprachen für Benutzer hinzufügen, wenn sie auf ihrem Gerät aktivieren? Speichern Sie anstatt vollständige Language Packs Speicherplatz, indem nur die Basis Benutzeroberflächendateien für eine Sprache hinzufügen. Später, wenn Ihre Benutzer Handschrift oder VoIP Spracherkennung Funktionen benötigt, können Windows herunterladen bei Bedarf.

Weitere Informationen finden Sie unter [Language Packs (lp.cab)](manufacture/desktop/language-packs-and-windows-deployment.md).

### <a name="new-package-type-capabilities"></a>Neue Pakettyp: Funktionen

Dieses neue Windows Pakettyp können Sie Dienste, wie Microsoft .NET oder Sprachen ohne Angabe der Version anfordern. Verwenden Sie das Tool DISM mehrere Quellen durchsuchen wie Windows Update oder Ihre Unternehmensserver zum Suchen und installieren die neueste Version.

### <a name="save-space-by-running-windows-from-compressed-os-files"></a>Speichern von Speicherplatz durch Ausführen von Windows über komprimierte OS-Dateien

Sie können jetzt Windows direkt aus komprimierter Dateien ausführen. Dies ist ähnlich wie WIMBoot, in Windows 8.1 Update 1 eingeführt. Dieser neue Prozess verwendet einzelne Dateien anstelle einer statischen WIM-Datei. Beim Aktualisieren von Systemdateien ersetzt Windows jetzt die alten Dateien anstatt beide Kopien beibehalten.


## <a name="related-topics"></a>Verwandte Themen

- [Übersicht über Kits und tools](kits-and-tools-overview.md)

- [Was ist neu in Treiberentwicklung](https://msdn.microsoft.com/windows/hardware/drivers/what-s-new-in-driver-development)

- [Was ist neu in Windows Performance Toolkit](https://msdn.microsoft.com/en-us/library/windows/hardware/dn927303(v=vs.85).aspx)

- [Was ist neu in die Hardware Lab-Kit](https://msdn.microsoft.com/library/windows/hardware/mt187880.aspx)
 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_getstarted\p_getstarted%5D:%20What's%20new%20in%20kits%20and%20tools%20%20RELEASE:%20%286/15/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





