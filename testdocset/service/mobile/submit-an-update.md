---
author: kpacquer
Description: Senden Sie ein update
ms.assetid: c7052c5d-53f8-4f94-a919-ac6939e310a6
MSHAttr: PreferredLib:/library/windows/hardware
title: Senden Sie ein update
ms.openlocfilehash: 3a9bb9fc8b07da45868eb9fcdea97b2ab392a18e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="submit-an-update"></a>Senden Sie ein update


Updates den Unterschied zwischen der aktuellen Firmware und die Firmware auf Aktualisieren Sie herausfinden erstellt werden, und erstellen ein Update Bundle, enthält die Unterschiede. Diese Unterschiede werden berechnet, erstellt und auf der Microsoft Update-Servern gehostet.

Beginnen mit der Version von Windows 10, können OEMs nicht mehr nur OS-Updates für den Einzelhandel Geräte senden mit dem [Cmdlet "New-RequestForMicrosoftUpdate"](new-requestformicrosoftupdate-cmdlet.md). Nur OS-Updates für den Einzelhandel Geräte werden von Microsoft auf Windows Update bereitgestellt werden.

OEMs können weiterhin nur OS Aktualisierungen für Test- und PartnerSelfHost Preview Umgebungen zu übermitteln.

## <a name="span-idsubmitanoemupdatespanspan-idsubmitanoemupdatespanspan-idsubmitanoemupdatespansubmit-an-oem-update"></a><span id="Submit_an_OEM_update"></span><span id="submit_an_oem_update"></span><span id="SUBMIT_AN_OEM_UPDATE"></span>Übermitteln Sie eine OEM-Aktualisierung


1.  Rufen Sie die Quelle Firmware Übermittlung-Ticket-ID aus dem Zeitpunkt der letzten dieses Paket Aktualisierung.

2.  Rufen Sie eine Ziel Firmware Übermittlung Ticket-ID: aktualisieren die Binärdateien in das Paket, und [übermitteln, die Binärdateien Retail werden angemeldet](https://msdn.microsoft.com/library/windows/hardware/dn789223) , erhalten Sie eine neue Ticket-ID.

3.  Übermitteln Sie mit sowohl das alte und neue Ticket IDs die updateanforderung mit dem [Cmdlet New-RequestForUpdate](new-requestforupdate-cmdlet.md):

    ``` syntax
    New-RequestForUpdate 
       -FirmwareSubmissionTicketId TKT-SIGN-PROD-ABCD56 
       -RequestForUpdateType RetailServicing 
       -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 
       -OemDeviceName P4301
       -MOId 000-22
    ```

    Die Ausgabe dieses Befehls können Sie eine Anforderung für Update (RFU)-ID.

4.  Verwenden Sie die RFU-ID, um den Status mit dem [Cmdlet Get-RequestForUpdate](get-requestforupdate-cmdlet.md)zu überprüfen:

    ``` syntax
    Get-RequestForUpdate
       -RequestForUpdateTicketId TKT-RFU-PROD-ABCD56-1
    ```

    Wenn alles OK ist, werden wir die Anforderung genehmigen und an den Microsoft Preview Test-Server zu senden.

5.  Sie und Ihr Partner Mobilfunkbetreiber können über das Netzwerk testen.

6.  Sie und Ihre Mobilfunkbetreiber partner [das Update zu genehmigen](approve-an-update.md).

7.  Wir werden das Update auf dem Produktionsserver Microsoft Update, das Gerät können hier [Scannen, herunterladen und installieren Sie das Update](scan--download--and-install-updates.md)veröffentlichen.

Das folgende Diagramm zeigt dieses Verfahren:

![Diagramm zeigt Übermittlung Aktualisierungsvorgang](images/oem-update-submitanupdate.png)

**Hinweis**  OS optionale Features in der Datei OEMInput.xml zwischen Updates kann nicht geändert werden. Wenn ein Feature geändert wird, wird das Update vom publishing System abgelehnt.

 

## <a name="span-idsubmitmicrosoftupdatesspanspan-idsubmitmicrosoftupdatesspanspan-idsubmitmicrosoftupdatesspansubmit-microsoft-updates"></a><span id="Submit_Microsoft_updates"></span><span id="submit_microsoft_updates"></span><span id="SUBMIT_MICROSOFT_UPDATES"></span>Übermitteln von Microsoft-updates


1.  Verwenden Sie das [Cmdlet New-RequestForMicrosoftUpdate](new-requestformicrosoftupdate-cmdlet.md), über die alte und neue Version Zahlen, die den Typ einer Aktualisierung (RetailServicing oder Testversion), und der OEM-Gerätename und Mobile Operator-ID:

    Mit dem Ticket-IDs für die vorhandenen Firmware und die neue Firmware fordern Sie ein Update mit dem [Cmdlet "New-RequestForUpdate"](new-requestforupdate-cmdlet.md).

    ``` syntax
    New-RequestForMicrosoftUpdate
       -SourceOSVersion 8.10.12349.825
       -TargetOSVersion 8.10.12359.845
       -RequestForUpdateType Trial
       -OemDeviceName P4301
       -MOId 000-22
    ```

2.  Das Update wird auf Microsoft Update Produktionsserver, in dem das Gerät kann, [Scannen, herunterladen und installieren Sie das Update](scan--download--and-install-updates.md)veröffentlicht.

 

 

