---
author: kpacquer
Description: Neue RequestForUpdate-cmdlet
ms.assetid: 8fef568e-4687-4862-ac7e-7a518ccbfe67
MSHAttr: PreferredLib:/library/windows/hardware
title: Neue RequestForUpdate-cmdlet
ms.openlocfilehash: b37cd9197912c2c6de92155d3604e19e009518d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="new-requestforupdate-cmdlet"></a>Neue RequestForUpdate-cmdlet


Verwenden Sie **New-RequestForUpdate** zum Erstellen einer neuen Anforderung für das Update (RFU) basierend auf einer bestimmten Update und Firmware Einreichung Ticket-ID. Die Firmware Übermittlung muss erfolgreich angemeldet sein.

Bevor Sie eine RFU erstellen können, müssen Sie zum Vorbereiten der Übermittlung Firmware **TypeOfSubmission** legen Sie auf **Bild** [Initialize-FirmwareSubmission-Cmdlet](initialize-firmwaresubmission-cmdlet.md) mit. Weitere Informationen zum Prozess der Übermittlung der Bild finden Sie unter [Submit-Binärdateien Retail werden angemeldet](https://msdn.microsoft.com/library/windows/hardware/dn789223).

**Wichtige**  
Übermitteln Sie separate RFUs für jede Kopplung von Telefon-Operator. Wenn Sie zwei Telefonen auf eine bestimmte Mobile Operator (MO) verfügen, müssen Sie beispielsweise zwei RFUs übermitteln. Wenn Sie ein Gerät in vier verschiedene MOs vorhanden sind, müssen Sie vier RFUs übermitteln.

 

Dies ist die Syntax für das **New-RequestForUpdate**:

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
NAME
    New-RequestForUpdate
SYNTAX
    New-RequestForUpdate [-FirmwareSubmissionTicketId] <String>
    [-RequestForUpdateType] <RequestForUpdateType>
    [-SourceFirmwareSubmissionTicketId] <String>[[-OemDeviceName] <String>]
    [[-MOId] <String>]
    [-ServiceUri <Uri>]
    [-CertificateStoreLocation <StoreLocation>]
    [CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>]
    [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


Normalerweise sind die einzigen Parameter, die für dieses Cmdlet angegeben sind, **FirmwareSubmissionTicketId**, **RequestForUpdateType**, **SourceFirmwareSubmissionTicketId**, **OemDeviceName**und **MOId**.

Die **FirmwareSubmissionTicketId** -Eigenschaft ist die ID der Firmware Einreichung Ticket ID mit dem neuen RFU verknüpft wird.

Das **RequestForUpdateType** muss auf einen der folgenden zwei Werte festgelegt werden:

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
<td align="left"><p>Verwendet vom OEMs zur Updates über das Mobilfunknetz (OTA) für MOs für Lab Versuche und technische Annahme verfügbar machen. Updates in der Vorschau werden in der live produktionsumgebung gemäß veröffentlichte Ziele nach Erhalt der OEM-Genehmigung (Go live) veröffentlicht.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Test</p></td>
<td align="left"><p>Wird von OEMs OTA Updates testen und bewerten die Qualität ihrer RFUs vor dem Einreichen einer Einzelhandel – Wartung Übermittlung verwendet. Es wird auch zum Testen von Updates für commercializing neue Geräte verwendet.</p>
<p>Es ist nicht für MO Lab Testversionen vorgesehen. Hier veröffentlichten Updates führen Sie Microsoft Update Produktion nicht veröffentlicht.</p></td>
</tr>
</tbody>
</table>

 

Das **SourceFirmwareSubmissionTicketId** ist das Ticket ID der Geräte Übermittlung Firmware aktualisieren aus. Diese Option ist nur erforderlich, wenn die Telefone aktualisieren auf Windows Phone 8.1 oder höher sind. Zum Schutz vor Veröffentlichung Updates, die potenziell Aktualisierungsfehler, die Windows Phone verursachen können behält Geräteupdates Publishingdienst RFUs ablehnen, die die **SourceFirmwareSubmissionTicketId** des vorherigen Updates nicht enthalten. Weitere Informationen zu versionsverwaltung finden Sie unter [Anforderungen zu aktualisieren](update-requirements.md).

Die **OemDeviceName** ist der Name, an dem die Anforderung für das Update vorgesehen ist. Diese Option ist nur erforderlich, wenn das Gerät aktualisieren auf Windows Phone 8.1 oder höher verwendet werden.

Die **MOId** ist den Mobilfunkbetreiber an dem die Anforderung für das Update vorgesehen ist.

## <a name="span-idscenariocreateanewrfuforuseinretailservicingspanspan-idscenariocreateanewrfuforuseinretailservicingspanspan-idscenariocreateanewrfuforuseinretailservicingspanscenario-create-a-new-rfu-for-use-in-retail-servicing"></a><span id="Scenario__Create_a_new_RFU_for_use_in_retail_servicing"></span><span id="scenario__create_a_new_rfu_for_use_in_retail_servicing"></span><span id="SCENARIO__CREATE_A_NEW_RFU_FOR_USE_IN_RETAIL_SERVICING"></span>Szenario: Erstellen einer neuen RFU für die Verwendung im Einzelhandel – Wartung


### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   Eine Firmware signierenden Anforderung wurde erfolgreich übermittelt.

-   Die Firmware signierenden Anforderung Ticket-Nummer ist verfügbar.

-   Es gibt Wunsch eine neue Anforderung für das Update für den Einzelhandel – Wartung zu übermitteln.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Fordern Sie ein neues Update, und speichern Sie das Ergebnisobjekt in einer Windows PowerShell-Variablen mit dem Namen $result:

``` syntax
$result = New-RequestForUpdate -FirmwareSubmissionTicketId TKT-SIGN-PROD-ABCD56 –RequestForUpdateType RetailServicing -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName P4301 -MOId 000-22
```

Zeigen Sie die Ergebnisse in der Konsole an:

``` syntax
PS> $result | Format-List

Ticket             : TKT-SIGN-TEST-AB03ST-2
RfuType            : RetailServicing
IsApproved         : False
CreatedOn          : 7/18/2013 8:26:23 PM
ModifiedOn         : 7/18/2013 8:26:23 PM 
FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles            :
Attachments        :
Operations         : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOpera
                     tion}
ExtensionData      : System.Runtime.Serialization.ExtensionDataObjectFile      
```

## <a name="span-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanspan-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanspan-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanscenario-attempt-to-create-a-new-rfu-when-the-firmware-ticket-does-not-exist"></a><span id="Scenario__Attempt_to_create_a_new_RFU_when_the_firmware_ticket_does_not_exist"></span><span id="scenario__attempt_to_create_a_new_rfu_when_the_firmware_ticket_does_not_exist"></span><span id="SCENARIO__ATTEMPT_TO_CREATE_A_NEW_RFU_WHEN_THE_FIRMWARE_TICKET_DOES_NOT_EXIST"></span>Szenario: Versuch, eine neue RFU zu erstellen, wenn das Ticket Firmware nicht vorhanden ist


### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderliche Komponenten

-   OEM versucht, eine RFU Ticket-Nummer abzurufen, die nicht vorhanden ist.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Verwendungsbeispiel mit erwartete Ausgabe

``` syntax
$result = New-RequestForUpdate -FirmwareSubmissionTicketId TKT-SIGN-TEST-NONONO -RequestForUpdateType Trial -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName P4301 -MOId 000-22
```

``` syntax
New-RequestForUpdate : An error has ocurred.  The request could not be
processed because operation is not valid for current state of service.
Details: The specified FirmwareSubmission ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: 05818963-a8f4-4d9f-9472-5257374549a9.
At line:1 char:11
+ $result = New-RequestForUpdate -FirmwareSubmissionTicketId
TKT-SIGN-TEST-NONONO  ...
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>Hilfedokumentation von PowerShell


Es folgt der Hilfedokumentation für das **New-RequestForUpdate** -Cmdlet von Windows PowerShell.

``` syntax
PS C:\Windows\system32> get-help New-RequestForUpdate -full

NAME
    New-RequestForUpdate

SYNOPSIS
    Creates a new request for update of OEM binaries only.

SYNTAX
    New-RequestForUpdate [-FirmwareSubmissionTicketId] <String>
    [-RequestForUpdateType] <RequestForUpdateType>
    [[-SourceFirmwareSubmissionTicketId] <String>] [[-OemDeviceName] <String>]
    [[-MOId] <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace
    <String>] [-CertificateStoreLocation <StoreLocation>]
    [-CertificateStoreName <StoreName>] [-ClientCertificateThumbprint
    <String>] [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]


DESCRIPTION
    Creates a new request for update of OEM binaries, with a
    given update type and firmware submission ticket id. To create a Request
    For Update to Windows Phone 8.1 or higher, a source (ie. update "from")
    firmware submission ticket id is also required, along with the target
    mobile operator name, and target device name.


PARAMETERS
    -FirmwareSubmissionTicketId <String>
        Ticket id of the firmware submission phones update to.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -RequestForUpdateType <RequestForUpdateType>
        The type of update request.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SourceFirmwareSubmissionTicketId <String>
        Ticket id of the firmware submission phones update from. Only required
        if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
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

        Provides detailed information about the request for update (RFU).  The
        Ticket property is the ticket id for the actual RFU that should be
        recorded to allow for future communication about the RFU, for example
        through the command Get-RequestForUpdate which returns current status
        of the RFU.



    --------------  Example 1 --------------

    C:\PS>New-RequestForUpdate -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCD56 -RequestForUpdateType RetailServicing


    Creates a new request for update for retail servicing and links it to the
    firmware submission ticket id, TKT-SIGN-PROD-ABCD56.



    Ticket                   : TKT-RFU-PROD-ABCD56-1
                RfuType                  : RetailServicing
                IsApproved               : False
                CreatedOn                : 6/29/2013 7:44:07 AM
                ModifiedOn               : 6/29/2013 7:44:08 AM
                FirmwareSubmission       :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceFirmwareSubmission :
                SourceOSVersion          :
                TargetOSVersion          :
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject
                RfuPayloadType           : MicrosoftOemMixed



    --------------  Example 2 --------------

    C:\PS>New-RequestForUpdate -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCD56 -RequestForUpdateType RetailServicing
    -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName
    P4301 -MOId 000-22


    Creates a new request for update for retail servicing with source and
    target firmware submission ticket ids, meaning that the target OS version
    of the update is Windows Phone 8.1 or later.



    Ticket                   : TKT-RFU-PROD-ABCD56-1
                RfuType                  : RetailServicing
                IsApproved               : False
                CreatedOn                : 3/14/2014 7:44:07 AM
                ModifiedOn               : 3/14/2014 7:44:08 AM
                FirmwareSubmission       :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceFirmwareSubmission :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceOSVersion          : 8.10.12349.825
                TargetOSVersion          : 8.10.12359.845
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject
                RfuPayloadType           : MicrosoftOemMixed

RELATED LINKS
PS C:\Windows\system32>
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** None

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Senden Sie ein update](submit-an-update.md)

[Übermitteln von Binärdateien retail signiert sein](https://msdn.microsoft.com/library/windows/hardware/dn789223)

[Anforderung UpdateCancellation](request-updatecancellation.md)

 

 

