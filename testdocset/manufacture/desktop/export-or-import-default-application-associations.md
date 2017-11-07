---
author: Justinha
Description: Exportieren Sie oder importieren Sie Zuordnungen von Dienstanwendungen
ms.assetid: 87eb7510-df1a-4e3f-9cd4-5400fa6e1a07
MSHAttr: PreferredLib:/library/windows/hardware
title: Exportieren Sie oder importieren Sie Zuordnungen von Dienstanwendungen
ms.openlocfilehash: 40b314583d33d7a3c07e62d71c0719d348c8d339
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="export-or-import-default-application-associations"></a>Exportieren Sie oder importieren Sie Zuordnungen von Dienstanwendungen


Das Tool Deployment Image Servicing and Management (DISM) können zum Ändern der Standardprogramme eine Dateinamenerweiterung oder Protokoll in einem Windows® Bild zugeordnet ist.

## <a name="span-idgeneratedefaultapplicationassociationsxmlfilespanspan-idgeneratedefaultapplicationassociationsxmlfilespanspan-idgeneratedefaultapplicationassociationsxmlfilespangenerate-default-application-associations-xml-file"></a><span id="Generate_Default_Application_Associations_XML_File"></span><span id="generate_default_application_associations_xml_file"></span><span id="GENERATE_DEFAULT_APPLICATION_ASSOCIATIONS_XML_FILE"></span>Generieren der XML-Datei Standard für die Zuordnungen


Bereitstellen Sie des Windows-Abbilds auf einem Testcomputer, und konfigurieren Sie die Programmen, die in Ihrem Bild enthalten sind. Sie können melden Sie sich bei Windows und mithilfe der Systemsteuerung Zuordnungen Ihre Standard-Anwendung aus. Die standardmäßigen Zuordnungen von dienstanwendungen können, die Sie in eine XML-Datei auf einer Netzwerkfreigabe oder Wechselmedium konfiguriert haben, damit Sie sie in der WIM- oder VHD-Datei importieren können, vor der Bereitstellung auf den Zielcomputern exportiert werden.

**Legen Sie Zuordnungen von dienstanwendungen**

1.  Installieren Sie das Windows-Abbild auf einem Testcomputer. Weitere Informationen zum Anwenden eines Windows-Abbilds, finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

2.  Starten Sie den Testcomputer, und schließen Sie Windows Setup.

3.  Klicken Sie auf **Suchen**, klicken Sie auf **Einstellungen**und geben Sie **Default Programs**. Klicken Sie auf **Programme**.

4.  Sie können Standardprogramme durch Erweiterung oder Anwendung konfigurieren. Beispielsweise zum Festlegen eines installierten Fotos anzeigen-Anwendung als Standard-Programm, das zum Öffnen aller Dateitypen und Protokolle, die er unterstützt verwendet wird, klicken Sie auf **Ihre Standardprogramme festlegen**, klicken Sie auf das Foto Anzeigen der Anwendung in der Programmliste, und klicken Sie dann auf **diese Anwendung als Standard festlegen**.

**Exportieren Sie die Standardeinstellungen der Anwendung Zuordnung**

1.  Öffnen Sie auf dem Testcomputer eine Eingabeaufforderung mit Administratorrechten. Wenn Sie eine Version von Windows als Windows 8 verwenden, verwenden Sie die Eingabeaufforderung für Bereitstellungstools installiert mit ADK oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.

2.  Exportieren Sie die Standardeinstellungen der Anwendung Zuordnung aus dem Testcomputer in eine XML-Datei auf einer Netzwerkfreigabe oder USB-Laufwerk. Geben Sie beispielsweise den folgenden Befehl an der Befehlszeile ein:

    ``` syntax
    Dism /Online /Export-DefaultAppAssociations:\\Server\Share\AppAssoc.xml
    ```

    Dabei gilt Folgendes:

    -   Server ist der Name des Servers oder der Computer, der die Freigabe enthält, dass Sie die Standardeinstellungen der Anwendung Zuordnung exportiert werden.

    -   Freigeben ist der Name der Freigabe ein, in dem Sie die Standardeinstellungen der Anwendung Association exportieren möchten.

## <a name="span-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanspan-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanspan-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanadd-or-remove-default-application-association-settings-to-a-windows-image"></a><span id="Add_or_Remove_Default_Application_Association_Settings_to_a_Windows_Image"></span><span id="add_or_remove_default_application_association_settings_to_a_windows_image"></span><span id="ADD_OR_REMOVE_DEFAULT_APPLICATION_ASSOCIATION_SETTINGS_TO_A_WINDOWS_IMAGE"></span>Hinzufügen oder Entfernen von Standardeinstellungen Anwendung Zuordnung zu einem Windows-Abbild


Sie können die Standardeinstellungen für die Zuordnung von Anwendung in einer Datei WIM oder VHD ändern, bevor Sie ihn auf den Zielcomputern bereitstellen. Sie können auch hinzufügen und entfernen Standardeinstellungen der Anwendung Zuordnung aus einem online Bild.

**Importieren Sie die Standardeinstellungen der Anwendung Zuordnung**

1.  Öffnen Sie eine Eingabeaufforderung auf dem Referenzcomputer mit administrativen Anmeldeinformationen. Wenn Sie eine Version von Windows als Windows 8 verwenden, verwenden Sie die Eingabeaufforderung für Bereitstellungstools mit ADK installiert oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.

2.  Binden Sie ein Windows-Abbild aus einer WIM oder VHD-Datei. Geben Sie beispielsweise den folgenden Befehl an der Befehlszeile ein:

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows" /MountDir:C:\test\offline
    ```

3.  Importieren Sie die XML-Datei, die die Standardeinstellungen für die Zuordnung von Anwendung auf dem Windows-Abbild verfügt. Geben Sie beispielsweise den folgenden Befehl an der Befehlszeile ein:

    ``` syntax
    Dism.exe /Image:C:\test\offline /Import-DefaultAppAssociations:\\Server\Share\AppAssoc.xml
    ```

    Dabei gilt Folgendes:

    -   Server ist der Name des Servers oder der Computer, der die Freigabe enthält, dass Sie die Standardeinstellungen der Anwendung Association exportieren möchten.

    -   Freigeben ist der Name der Freigabe ein, in dem Sie die Standardeinstellungen der Anwendung Association exportieren möchten.

**Überprüfen Sie die Standardeinstellung für die Zuordnung von Anwendung in einem Bild**

1.  Öffnen Sie ein Eingabeaufforderungsfenster auf dem Referenzcomputer mit administrativen Anmeldeinformationen. Wenn Sie eine Version von Windows als Windows 8 verwenden, verwenden Sie die Eingabeaufforderung für Bereitstellungstools mit ADK installiert, oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.

2.  Liste der Zuordnungen von dienstanwendungen, die auf das bereitgestellte Abbild angewendet wurden. Geben Sie beispielsweise den folgenden Befehl an der Befehlszeile ein:

    ``` syntax
    Dism.exe /Image:C:\test\offline /Get-DefaultAppAssociations
    ```

**Standardeinstellungen der Anwendung Zuordnung zu entfernen**

1.  Öffnen Sie ein Eingabeaufforderungsfenster auf dem Referenzcomputer mit administrativen Anmeldeinformationen. Wenn Sie eine Version von Windows als Windows 8 verwenden, verwenden Sie die Eingabeaufforderung für Bereitstellungstools mit ADK installiert oder navigieren Sie zum Verzeichnis DISM auf Ihrem lokalen Computer.

2.  Entfernt die benutzerdefinierte Anwendung Zuordnung, die auf das bereitgestellte Abbild hinzugefügt wurden. Geben Sie beispielsweise den folgenden Befehl an der Befehlszeile ein:

    ``` syntax
    Dism.exe /Image:C:\test\offline /Remove-DefaultAppAssociations
    ```

 

 





