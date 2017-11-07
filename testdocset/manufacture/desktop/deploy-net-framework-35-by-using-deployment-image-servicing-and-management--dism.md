---
author: Justinha
Description: Bereitstellen von .NET Framework 3.5 mithilfe von Deployment Image Servicing and Management (DISM)
ms.assetid: c21b1e0f-d480-4f51-99d1-d5f7acba3a4a
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen von .NET Framework 3.5 mithilfe von Deployment Image Servicing and Management (DISM)
ms.openlocfilehash: 23eec125eb87af989c62687223f3e57997f59f9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-net-framework-35-by-using-deployment-image-servicing-and-management-dism"></a>Bereitstellen von .NET Framework 3.5 mithilfe von Deployment Image Servicing and Management (DISM)


Sie können das Befehlszeilentool Deployment Image Servicing and Management (DISM) zum Erstellen eines geänderten Bildes zum Bereitstellen von .NET Framework 3.5 verwenden.

**Wichtige**  
Für Bilder, die mehrere Sprachen unterstützen, müssen Sie .NET Framework 3.5 Binärdateien vor dem Hinzufügen von Language Packs hinzufügen. Dieser Auftrag wird sichergestellt, dass .NET Framework 3.5 Sprachressourcen in das Bild Verweis ordnungsgemäß installiert und für Benutzer und Anwendungen verfügbar sind.

 

**In diesem Thema:**

-   [Mithilfe von DISM mit Internetkonnektivität](#internet)

-   [Mithilfe von DISM ohne Internetverbindung](#nointerent)

## <a name="span-idinternetspanspan-idinternetspanusing-dism-with-internet-connectivity"></a><span id="internet"></span><span id="INTERNET"></span>Mithilfe von DISM mit Internetkonnektivität


### <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen

-   Verbindung mit dem Internet

-   Zugriff auf Windows Update. Wenn der PC oder Server einer Firewall hinter oder einen Proxyserver verwendet, finden Sie unter [KB900935 - Client wie Windows Update bestimmt, welcher Proxyserver für die Verbindung mit der Windows Update-Website verwenden](http://support.microsoft.com/kb/900935).

-   Windows 8, Windows Server® 2012 oder [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?linkid=325506) -Tools.

-   Installationsmedien

-   Administratorrechte verfügen. Der aktuelle Benutzer muss ein Mitglied der lokalen Gruppe Administratoren hinzufügen oder Entfernen von Windows-Features.

### <a name="span-idforanonlinereferenceimagethatcanaccesswindowsupdatespanspan-idforanonlinereferenceimagethatcanaccesswindowsupdatespanspan-idforanonlinereferenceimagethatcanaccesswindowsupdatespanfor-an-online-reference-image-that-can-access-windows-update"></a><span id="For_an_online_reference_image_that_can_access_Windows_Update"></span><span id="for_an_online_reference_image_that_can_access_windows_update"></span><span id="FOR_AN_ONLINE_REFERENCE_IMAGE_THAT_CAN_ACCESS_WINDOWS_UPDATE"></span>Für ein Referenz online Image, die auf Windows Update zugreifen können

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Systemadministratorrechte (als Administrator ausführen) in Windows 8 oder Windows Server 2012 ein.

2.  Verwenden Sie zum Installieren von .NET Framework 3.5-Feature-Dateien über Windows Update folgenden Befehl ein:

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All 
    ```

    Verwenden *Sie/All* , um alle übergeordneten Features des angegebenen Features zu aktivieren. Weitere Informationen zu DISM Argumenten finden Sie unter [Aktivieren oder Deaktivieren von Windows Features mithilfe von DISM](http://go.microsoft.com/fwlink/p/?linkid=259118).

3.  Klicken Sie auf Windows 8 PCs, nach der Installation, die auf .NET Framework 3.5 als aktiviert werden, **Aktivieren Sie Windows-features ein- oder ausschalten** , in der Systemsteuerung angezeigt wird. Für Windows Server 2012-Systeme kann Installationsstatus für Features im Server-Manager angezeigt werden.

### <a name="span-idforanofflinereferenceimagespanspan-idforanofflinereferenceimagespanspan-idforanofflinereferenceimagespanfor-an-offline-reference-image"></a><span id="For_an_offline_reference_image"></span><span id="for_an_offline_reference_image"></span><span id="FOR_AN_OFFLINE_REFERENCE_IMAGE"></span>Für ein Image offline Verweis

1.  Führen Sie den folgenden Befehl DISM (Abbild bereitgestellt, um die **c:\\testen\\offline** Ordner und dem Installationsdatenträger in den **D:**\\Laufwerk) .NET 3.5 zu installieren:

    ``` syntax
    DISM /Image:C:\test\offline /Enable-Feature /FeatureName:NetFx3 /All /LimitAccess /Source:D:\sources\sxs
    ```

    Verwenden *Sie/All* , um alle übergeordneten Features des angegebenen Features zu aktivieren.

    Verwenden Sie */LimitAccess* DISM Kontaktaufnahme mit Windows Update/WSUS verhindern.

    Verwenden *Sie/Source* , um den Speicherort der Dateien anzugeben, die erforderlich sind, um das Feature wiederherstellen.

    Um DISM aus einer Installation von Windows ADK verwenden, zu dem Wartung Windows ADK-Ordner, und navigieren Sie zu diesem Verzeichnis. Standardmäßig DISM installiert ist, am **C:\\Program Files (x86)\\Windows Kits\\8.0\\Assessment and Deployment Kit\\Bereitstellungstools\\**. Sie können DISM Bereitstellung und andere imaging Tools installieren, wie Windows System Image Manager (Windows System Image Manager) auf einem anderen Betriebssystem aus der Windows-ADK unterstützt. Informationen zu DISM unterstützte Plattformen finden Sie unter [DISM unterstützte Plattformen](http://go.microsoft.com/fwlink/p/?LinkId=698536).

2.  Führen Sie den folgenden Befehl zum Nachschlagen von den Status von .NET Framework 3.5 (offline-Abbild Anbindung an **c:\\testen\\offline**):

    ``` syntax
    DISM /Image:c:\test\offline /Get-Features /Format:Table
    ```

    **Ausstehende aktivieren** Status gibt an, dass das Bild online geschaltet werden muss, um die Installation abzuschließen.

### <a name="span-idnointerentspanspan-idnointerentspanusing-dism-with-no-internet-connectivity"></a><span id="nointerent"></span><span id="NOINTERENT"></span>Mithilfe von DISM ohne Internetverbindung

Sie können mithilfe von DISM hinzufügen auf .NET Framework 3.5 und gewähren Sie Zugriff auf die ** \\Quellen\\SxS** Ordner auf dem Installationsmedium einer Installation von Windows®, die nicht mit dem Internet verbunden ist.

### <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen

-   Windows 8, Windows Server 2012 oder [Windows ADK](http://go.microsoft.com/fwlink/p/?linkid=325506) -Tools.

-   Installationsmedien

-   Administratorrechte verfügen. Der aktuelle Benutzer muss ein Mitglied der lokalen Gruppe Administratoren hinzufügen oder Entfernen von Windows-Features.

### <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>Schritte

1.  Öffnen Sie ein Eingabeaufforderungsfenster mit Systemadministratorrechte (als Administrator ausführen) in Windows 8 oder Windows Server 2012.

2.  Verwenden Sie zum Installieren von .NET Framework 3.5 vom Installationsmedium befindet sich auf dem Laufwerk **D:** den folgenden Befehl ein:

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All /LimitAccess /Source:d:\sources\sxs
    ```

    Verwenden *Sie/All* , um alle übergeordneten Features des angegebenen Features zu aktivieren.

    Verwenden Sie */LimitAccess* DISM Kontaktaufnahme mit Windows Update/WSUS verhindern.

    Verwenden *Sie/Source* den Speicherort der Dateien an, die benötigt werden, um das Feature wiederherstellen.

    Weitere Informationen zu DISM Argumenten finden Sie unter [Aktivieren oder Deaktivieren von Windows Features mithilfe von DISM](http://go.microsoft.com/fwlink/p/?linkid=259118).

Auf Windows 8-PCs wird nach der Installation auf .NET Framework 3.5 angezeigt als in **Windows-Features aktivieren oder deaktivieren** in der Systemsteuerung aktiviert.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellungsaspekte für Microsoft .NET Framework 3.5](microsoft-net-framework-35-deployment-considerations.md)

 

 






