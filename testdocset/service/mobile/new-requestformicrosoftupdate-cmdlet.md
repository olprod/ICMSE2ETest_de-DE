---
author: kpacquer
Description: Neue RequestForMicrosoftUpdate-cmdlet
ms.assetid: be21b20d-a3bf-4b83-9633-211dcbeecdb3
MSHAttr: PreferredLib:/library/windows/hardware
title: Neue RequestForMicrosoftUpdate-cmdlet
ms.openlocfilehash: 173bd02d19491964c6ace884d2673ad572301578
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="new-requestformicrosoftupdate-cmdlet"></a>Neue RequestForMicrosoftUpdate-cmdlet


Verwenden Sie das Cmdlet **New-RequestForMicrosoftUpdate** , eine neue Anforderung für das Update (RFU) erstellen, die nur für Microsoft AK Binärdateien für ein bestimmtes Produkt, CPU, Updatetyp, Quell- und Ziel Microsoft OS Versionsnummern zusammen mit der Mobilfunkbetreiber Zielname und Telefon Zielname enthält.

Beginnen mit der Version von Windows 10, können OEMs nicht mehr nur OS-Updates für den Einzelhandel Geräte senden mithilfe des Cmdlets New-RequestForMicrosoftUpdate. Nur OS-Updates für den Einzelhandel Geräte werden von Microsoft Windows Update bereitgestellt.

OEMs können weiterhin OS nur Aktualisierungen für Test- und PartnerSelfHost Preview-Umgebungen zu übermitteln.

**Wichtige**  
Sie müssen ein Update für die Bildung von jedem Telefon-Operator zu übermitteln. Wenn Sie auf eine bestimmte Mobilfunkbetreiber zwei Telefonen haben, müssen Sie beispielsweise zwei-Anforderung für Updates (RFU) zu übermitteln. Wenn Sie über ein Telefon auf vier verschiedene MOs verfügen, müssen Sie vier RFUs übermitteln.

 

Dies ist die Syntax für das **New-RequestForMicrosoftUpdate**:

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


``` syntax
New-RequestForMicrosoftUpdate [-TypeOfCPU <string>] [-TypeOfProduct <string>] 
[-SourceOSVersion <String>] [-TargetOSVersion <String>] [-RequestForUpdateType <RequestForUpdateType>]
[-OemDeviceName <String>] [-MOId <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>]
[-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName <StoreName>]
[-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint <String>]
 [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


Normalerweise sind die einzigen Parameter, die für dieses Cmdlet angegeben sind **SourceOSVersion**, **TargetOSVersion**, **RequestForUpdateType**, **OemDeviceName**und **MOId**.

Die **SourceOSVersion** ist die Version des vorherigen Updates. Diese Einstellung wird empfohlen, und hilft schützen Sie sich vor der Veröffentlichung von Updates, die potenziell Update Fehler verursachen können. Veröffentlichung des geräteaktualisierungsdiensts behält sich das Recht RFUs ablehnen, die die SourceOSVersion des vorherigen Updates nicht enthalten. Weitere Informationen zu versionsverwaltung finden Sie unter [Anforderungen zu aktualisieren](update-requirements.md).

Die Version **TargetOS** ist die Version des Updates gesendet wird.

Die **RequestForUpdateType** muss auf einen der beiden Werte zusammengefasst hier festgelegt werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">RequestForUpdateType</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>RetailServicing</p></td>
<td align="left"><p>OEM BSP Updates dienen der Dienst in Markt Geräte. Diese Updates werden als Teil der geplanten OEM Update Trittfrequenz (A4, A5, A6 usw.) geliefert.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Test</p></td>
<td align="left"><p>Studien Updates werden Mobile Operator OTA Versuche und OEM Engineering Versuche.</p>
<ul>
<li><p>Mobile Operator OTA Versuche – OEM BSP Updates dienen der zulassen MOs um neue Geräte Vermarktung zu erzielen.</p></li>
<li><p>OEM Engineering Versuche – OEM R&amp;D Versuche soll OEMs So testen Sie die aktualisierbar Gerät Bild Kandidaten zu aktivieren.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

Die **OemDeviceName** ist der Name, an dem die Anforderung für das Update vorgesehen ist. Diese Option ist nur erforderlich, wenn Sie Geräte aktualisieren auf Windows Phone 8.1 oder höher befinden.

Die **MOId** ist den Mobilfunkbetreiber an dem die Anforderung für das Update vorgesehen ist.

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Szenarien


### <a name="span-idcreateanewrfuforuseintrialsspanspan-idcreateanewrfuforuseintrialsspanspan-idcreateanewrfuforuseintrialsspancreate-a-new-rfu-for-use-in-trials"></a><span id="Create_a_new_RFU_for_use_in_trials"></span><span id="create_a_new_rfu_for_use_in_trials"></span><span id="CREATE_A_NEW_RFU_FOR_USE_IN_TRIALS"></span>Erstellen einer neuen RFU für die Verwendung in einer Versuchsreihe

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderliche Komponenten

-   Es ist Wunsch übermitteln Sie eine neue Anforderung für das Update für Versuche, beispielsweise für OEM R & D.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Verwendungsbeispiel mit erwartete Ausgabe

Fordern Sie ein neues Update, und speichern Sie das Ergebnisobjekt in einer Windows PowerShell-Variablen mit dem Namen $result:

``` syntax
$result = New-RequestForMicrosoftUpdate -SourceOSVersion 8.10.12349.825 -TargetOSVersion 8.10.12359.845 -RequestForUpdateType Trial -OemDeviceName P4301 -MOId 000-22
```

Zeigen Sie das Ergebnis in der Konsole an:

``` syntax
PS> $result | Format-List

Ticket                   : TKT-RFU-PROD-PQRST-1
RfuType                  : Trial
IsApproved               : False
CreatedOn                : 5/2/2014 5:42:51 PM
ModifiedOn               : 5/2/2014 5:42:52 PM
FirmwareSubmission       :
SourceFirmwareSubmission :
SourceOSVersion          : 8.10.12349.825
TargetOSVersion          : 8.10.12359.845
Pop                      : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles                  :
Attachments              :
Operations               : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
Status                   : Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
RfuPayloadType           : MicrosoftAKOnly
ExtensionData            : System.Runtime.Serialization.ExtensionDataObject
      
```

### <a name="span-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanhelp-documentation-from-windows-powershell"></a><span id="Help_documentation_from_Windows_PowerShell"></span><span id="help_documentation_from_windows_powershell"></span><span id="HELP_DOCUMENTATION_FROM_WINDOWS_POWERSHELL"></span>Hilfedokumentation von Windows PowerShell

Es folgt der Hilfedokumentation für das **New-RequestForMicrosoftUpdate** -Cmdlet von Windows PowerShell.

``` syntax
PS C:\Windows\system32> get-help New-RequestForMicrosoftUpdate -full

NAME
    New-RequestForMicrosoftUpdate

SYNOPSIS
    Creates a new request for update of Microsoft AK-only binaries.

SYNTAX
    New-RequestForMicrosoftUpdate [-TypeOfCPU <string>] [-TypeOfProduct <string>] 
[-SourceOSVersion <String>] [-TargetOSVersion <String>] [-RequestForUpdateType <RequestForUpdateType>]
[-OemDeviceName <String>] [-MOId <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>]
[-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName <StoreName>]
[-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint <String>]
 [<CommonParameters>]

DESCRIPTION
    Creates a new request for update of Microsoft AK-only binaries with a
    given update type, source and target Microsoft OS version numbers, along
    with the target mobile operator name, and target device name.


PARAMETERS
    -TypeOfProduct <String>
        The product targeted for the update.The product must be one of WindowsPhoneBlue, WindowsPhoneThreshold, WindowsHolographicThreshold.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TypeOfCPU <String>
        The CPU of the product targeted for the update.The CPU must be one of ARM, x86.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SourceOSVersion <String>
        Microsoft AK OS version the phone updates from.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TargetOSVersion <String>
        Microsoft AK OS version the phone updates to.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -RequestForUpdateType <RequestForUpdateType>
        The type of update request.

        Required?                    true
        Position?                    4
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OemDeviceName <String>
        Device name at which the Request for Update is being targeted. Only
        required if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
        Position?                    5
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -MOId <String>
        Mobile operator ID at which the Request for Update is being targeted.
        Only required if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
        Position?                    6
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -ServiceUri <Uri>
        The service URI. The default value for this parameter is read from the
        configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ServiceAccessControlNamespace <String>
        The namespace for Partner Services Access Control. The default value
        for this parameter is read from the configuration file. Should only be
        modified if instructed by the system administrator or Microsoft.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreLocation <StoreLocation>
        The certificate store location. The default value for this parameter
        is read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreName <StoreName>
        The certificate store name. The default value for this parameter is
        read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ClientCertificateThumbprint <String>
        The client certificate thumbprint. The default value for this
        parameter is read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -EncryptionCertificateThumbprint <String>
        The encryption certificate thumbprint. The default value for this
        parameter is read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information,
    see
        about_CommonParameters
    (http://go.microsoft.com/fwlink/p/?linkid=113216).

INPUTS


OUTPUTS
    RequestForUpdate

        Provides detailed information about the request for update (RFU) of
        Microsoft AK-only binaries.  The Ticket property is the ticket id for
        the actual RFU that should be recorded to allow for future
        communication about the RFU, for example through the command
        Get-RequestForUpdate which returns current status of the RFU.



    --------------  Example 1 --------------

    C:\PS>New-RequestForMicrosoftUpdate -SourceOSVersion 8.10.12349.825
    -TargetOSVersion 8.10.12359.845 -RequestForUpdateType Trial -OemDeviceName
    P4301 -MOId 000-22


    Creates a new request for update for retail servicing with source and
    target firmware submission ticket ids, meaning that the target OS version
    of the update is Windows Phone 8.1 or later.



    Ticket                   : TKT-RFU-PROD-PQRST-1
                RfuType                  : Trial
                IsApproved               : False
                CreatedOn                : 5/2/2014 5:42:51 PM
                ModifiedOn               : 5/2/2014 5:42:52 PM
                FirmwareSubmission       :
                SourceFirmwareSubmission :
                SourceOSVersion          : 8.10.12349.825
                TargetOSVersion          : 8.10.12359.845
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                Status                   :
    Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
                RfuPayloadType           : MicrosoftAKOnly
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject

RELATED LINKS

PS C:\Windows\system32>
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Header:** None

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Senden Sie ein update](submit-an-update.md)

[Anforderung UpdateCancellation](request-updatecancellation.md)

 

 