---
Description: "Zwei verschiedene Tools können Sie eine angepasste mobile Bild (FFU) in Windows 10 erstellen:"
ms.assetid: c29e417c-90a5-4928-b416-aa940efe68ab
MSHAttr: PreferredLib:/library
title: Erstellen einer mobilen Bild mit ImgGen
author: CelesteDG
ms.openlocfilehash: f16f5946e392fa4074396ce46603a2b74c1a7046
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-imggen"></a>Erstellen einer mobilen Bild mit ImgGen


Zwei verschiedene Tools können Sie eine angepasste mobile Bild (FFU) in Windows 10 erstellen:

-   ImgGen.cmd verwenden, ist die eine Befehlsdatei, die das klassische imaging Tool ImageApp.exe ausgeführt wird. Dieses Tool wurde auch die verfügbaren früheren Versionen von Windows 10 Mobile einschließlich Windows Phone 8.1 und die verschiedenen GDRs.

-   Die Befehlszeilenschnittstelle Windows Imaging und Konfiguration Designer (ICD) verwenden, ist die für Windows 10 neu.

In dieser exemplarischen Vorgehensweise zeigen wir, wie Sie ImgGen.cmd verwenden, um das benutzerdefinierte mobile Bild zu erstellen. In einer anderen exemplarischen Vorgehensweise gehen wir über ein anderes Bild mobile erstellen, das wir bisher zusätzlich zu anderen Anpassungen, die nur über die Windows-Bereitstellung durch verfügbar gemacht haben mithilfe der Windows-ICD CLI die Anpassungen enthält.

**Erstellen einer angepassten Abbilds mit ImgGen**

1.  Öffnen Sie ein **Entwickler für VS2015** Eingabeaufforderungsfenster als Administrator.

2.  Wenn Sie Windows 8.1 ausgeführt werden, führen Sie die folgenden Schritte aus, um die Größe des USN Journal Registrierung auf Ihrer Entwicklungs-PC auf 1 Mb festzulegen. Anderenfalls fahren Sie mit dem nächsten Schritt fort.

    1.  Ändern Sie den Registrierungsschlüssel für USN Mindestgröße durch den folgenden Befehl ausführen:

        **REG hinzufügen HKEY\_LOKALE\_COMPUTER\\SYSTEM\\CurrentControlSet\\Steuerelement\\FileSystem/v NtfsAllowUsnMinSize1Mb/t REG\_DWORD/d 1**

    2.  Neustart des Rechners, ehe Sie mit dem nächsten Schritt fortfahren.

3.  Führen Sie ImgGen.cmd mithilfe von den folgenden Befehl aus.

    **ImgGen** *TestFlash.ffuContosoTestOEMInput.xml* **"WPDKCONTENTROOT %\\MSPackages"** *MobileCustomizations.xml 10.0.0.1*

    Diesem Befehl wird ein Bild erstellt, die TestFlash.ffu aufgerufen werden.

    **Hinweis**  Mit diesem Befehl wird davon ausgegangen, dass Sie über den Rest der exemplarischen Vorgehensweisen in diesem Abschnitt navigiert sind. Weitere Informationen zur Befehlszeilensyntax für ImgGen.cmd finden Sie unter Using *ImgGen.cmd zum Generieren des Bilds* in [eine mobile Bild mit ImgGen.cmd erstellen](https://msdn.microsoft.com/library/windows/hardware/dn756630).

     

Nachdem das Bild aufbaut, müssen Sie es sich, damit es zu einem mobilen Gerät zugeordnet werden kann.

 

 



