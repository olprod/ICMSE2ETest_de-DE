---
author: kpacquer
Description: Get-RequestForUpdate-cmdlet
ms.assetid: f2b86f24-b5ff-4c9d-ac46-66898ad79e8c
MSHAttr: PreferredLib:/library/windows/hardware
title: Cmdlet &quot;Get-RequestForUpdate&quot;
ms.openlocfilehash: f4588cc4658c7e8114eb8f875b6e412b72d62a71
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-requestforupdate-cmdlet"></a>Cmdlet "Get-RequestForUpdate"


Verwenden Sie das Cmdlet **Get-RequestForUpdate** um den aktuellen Status einer Anforderung für die Aktualisierung abzurufen.

Dies ist die Syntax für das **Get-RequestForUpdate**.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
NAME
     Get-RequestForUpdate
SYNTAX
     Get-RequestForUpdate
      [-RequestForUpdateTicketId] <string> 
      [-ServiceUri <uri>]
      [-ServiceAccessControlNamespace <string>]
      [-CertificateStoreLocation <StoreLocation> {CurrentUser | LocalMachine}]
      [-CertificateStoreName <StoreName> {AddressBook | AuthRoot | CertificateAuthority
          | Disallowed | My | Root | TrustedPeople | TrustedPublisher}]
      [-ClientCertificateThumbprint <string>]
      [-EncryptionCertificateThumbprint <string>]
      [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


In der Regel sind die einzigen Parameter angegeben, um dieses Cmdlet **RequestForUpdateTicketId**an.

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe


Dieses Cmdlet gibt ein Microsoft.Phone.PartnerServices.Cmdlets.RequestForUpdate-Objekt, das die folgenden Felder enthält.

<span id="Status"></span><span id="status"></span><span id="STATUS"></span>**Status**  
Hierbei handelt es sich um den Fortschritt der RFU Übermittlung. Im folgenden werden die Elemente im Feld Status.

-   **ErrorCode**. Dies ist der Fehlercode des Fehlers, der aufgetreten ist.

-   **ErrorMessage**. Dieses Webpart enthält messaged im Zusammenhang mit der fehlerhaften RFU Übermittlung.

-   **Status**. Dieses Webpart enthält den Status der Status der aktuellen RFU-Übermittlung. Die folgende Liste enthält die Zustände.

    -   **InProcessOnTrack**. Die Übermittlung RFU ist derzeit in Arbeit.

    -   **InProcessFailure**. Der RFU-Übermittlung mit einem Fehler abgeschlossen; der Benutzer hat jedoch weiterhin die Option zum Wiederholen.

    -   **CompletedFailure**. Die RFU Übermittlung abgeschlossen mit einem Fehler und die Benutzer haben nicht wiederholen.

    -   **CompletedSuccess**. Die Übermittlung RFU ist ohne Probleme abgeschlossen.

    -   **FailedToRetrieveStatus**. Dies bedeutet, dass die Status Berechnung fehlgeschlagen ist. Die ErrorMessage ist in diesem Fall "ist ein Fehler beim Abrufen des Status RFU aufgetreten. Vom OEM ist keine Aktion erforderlich. Microsoft wird das Problem dadurch verursacht, die untersucht werden."

## <a name="span-idexceptionsspanspan-idexceptionsspanspan-idexceptionsspanexceptions"></a><span id="Exceptions"></span><span id="exceptions"></span><span id="EXCEPTIONS"></span>Ausnahmen


Die folgenden Ausnahmen sind für ihre Fehlerszenarien der entsprechenden ausgelöst.

<span id="FaultException_ArgumentFaultDetail_"></span><span id="faultexception_argumentfaultdetail_"></span><span id="FAULTEXCEPTION_ARGUMENTFAULTDETAIL_"></span>**FaultException&lt;ArgumentFaultDetail&gt;**  
-   Die ID eines ungültigen Tickets wurde bereitgestellt. Ticket-ID wurde entweder null oder leer.

<span id="FaultException_InvalidOperationFaultDetail_"></span><span id="faultexception_invalidoperationfaultdetail_"></span><span id="FAULTEXCEPTION_INVALIDOPERATIONFAULTDETAIL_"></span>**FaultException&lt;InvalidOperationFaultDetail&gt;**  
-   Die ID eines ungültigen Tickets wurde bereitgestellt. Ticket-ID ist nicht im Dienst definiert.

-   Der authentifizierte Benutzer ist nicht der Besitzer der Firmware-Übermittlung.

-   Ticket-ID ist ein Ticket Erneutes Senden.

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Szenarien


### <a name="span-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanspan-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanspan-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanretrieve-the-status-of-a-successfully-processed-request-for-update"></a><span id="Retrieve_the_status_of_a_successfully_processed_request_for_update"></span><span id="retrieve_the_status_of_a_successfully_processed_request_for_update"></span><span id="RETRIEVE_THE_STATUS_OF_A_SUCCESSFULLY_PROCESSED_REQUEST_FOR_UPDATE"></span>Abrufen des Status einer erfolgreich verarbeitet Anforderung für update

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   Eine Anforderung für die Aktualisierung wurde erfolgreich übermittelt.

-   Die Anforderung für Ticket-Updatenummer ist verfügbar.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Den Status des Updates abrufen und das Ergebnis-Objekt in einem PowerShell-Variablen mit dem Namen $result speichern:

``` syntax
PS> $result = Get-RequestForUpdate -RequestForUpdateTicketId TKT-SIGN-TEST-FO03ST-1
```

Zeigen Sie die Ergebnisse in der Konsole an:

``` syntax
PS> $result | Format-List

Ticket             : TKT-SIGN-TEST-FO03ST-1
RfuType            : Trial
IsApproved         : False
CreatedOn          : 7/18/2013 5:22:44 PM
ModifiedOn         : 7/18/2013 5:22:45 PM
FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles            :
Attachments        :
Operations         : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOpera
                     tion}
ExtensionData      : System.Runtime.Serialization.ExtensionDataObjectFile    
```

Der Pings Status in der Konsole angezeigt:

``` syntax
PS> $result.Status

## StatusErrorCodeErrorMessageExtensionData

InProcessOnTrack    System.Runtime.Serializati... 
```

### <a name="span-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanspan-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanspan-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanattempt-to-retrieve-the-status-for-an-rfu-when-the-ticket-does-not-exist"></a><span id="Attempt_to_retrieve_the_status_for_an_RFU_when_the_ticket_does_not_exist"></span><span id="attempt_to_retrieve_the_status_for_an_rfu_when_the_ticket_does_not_exist"></span><span id="ATTEMPT_TO_RETRIEVE_THE_STATUS_FOR_AN_RFU_WHEN_THE_TICKET_DOES_NOT_EXIST"></span>Versuchen Sie, den Status für ein RFU abrufen, wenn das Ticket nicht vorhanden ist

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   OEM versucht, eine RFU Ticket-Nummer abzurufen, die nicht vorhanden ist.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Versuchen Sie, die signierte Einreichung für ein Ticket abzurufen, die noch verarbeitet wird:

``` syntax
PS> $result = Get-RequestForUpdate –RequestForUpdateTicketId TKT-SIGN-TEST-NONONO
```

``` syntax
Get-RequestForUpdate : An error has ocurred.  The request could not be
processed because operation is not valid for current state of service.
Details: The specified RequestForUpdate ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: 994c438c-a6e1-44eb-8f06-2cbfa6c097bb.
At line:1 char:11
+ $result = Get-RequestForUpdate -RequestForUpdateTicketId TKT-SIGN-TEST-NONONO
+           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-RequestForUpdate], Ti
   cketDoesNotExistException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Ticke
   tDoesNotExistException,Microsoft.Phone.PartnerServices.Cmdlets.GetRequestF
  orUpdateCommand            
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>Hilfedokumentation von PowerShell


Es folgt der Hilfedokumentation für das **Get-RequestForUpdate** -Cmdlet von Windows PowerShell.

``` syntax
PS C:\Windows\system32> get-help get-requestforupdate -full

NAME
    Get-RequestForUpdate

SYNOPSIS
    Gets the status of a current request for update.

SYNTAX
    Get-RequestForUpdate [-RequestForUpdateTicketId] <String> [-ServiceUri
    <Uri>] [-ServiceAccessControlNamespace <String>]
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName
    <StoreName>] [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]


DESCRIPTION
    Gets the status of a current request for update. The request could be for
    a MicrosoftOemMixed or MicrosoftAKOnly update.


PARAMETERS
    -RequestForUpdateTicketId <String>
        The request for update ticket id.

        Required?                    true
        Position?                    2
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

        Provides detailed information of the request for update (RFU).



NOTES




    --------------  Example 1 --------------

    C:\PS>Get-RequestForUpdate -RequestForUpdateTicketId TKT-RFU-PROD-ABCD56-1


    Gets the status for a given RequestForUpdateTicketId



    Ticket             : TKT-RFU-PROD-ABCD56-1
                RfuType            : RetailServicing
                IsApproved         : False
                CreatedOn          : 6/29/2013 7:44:07 AM
                ModifiedOn         : 6/29/2013 7:44:08 AM
                FirmwareSubmission :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles            :
                Attachments        :
                Operations         :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData      :
    System.Runtime.Serialization.ExtensionDataObject




RELATED LINKS



PS C:\Windows\system32>NAME
    Get-RequestForUpdate

SYNOPSIS
    Gets the status of a current request for update.

SYNTAX
    Get-RequestForUpdate [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] 
    [-CertificateStoreLocation <StoreLocation>] 
    [-CertificateStoreName <StoreName>] 
    [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>]
    [<CommonParameters>]

DESCRIPTION
    Gets the status of a current request for update.


PARAMETERS
    -RequestForUpdateTicketId <String>
        The request for update ticket id.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -ServiceUri <Uri>
        The service URI. The default value for this parameter is read from the configuration file. 

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreLocation <StoreLocation>
        The certificate store location. The default value for this parameter is read from the configuration file.
        
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreName <StoreName>
        The certificate store name. The default value for this parameter is read from the configuration file. 

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ClientCertificateThumbprint <String>
        The client certificate thumbprint. The default value for this parameter is read from the configuration file.
        
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -EncryptionCertificateThumbprint <String>
        The encryption certificate thumbprint. The default value for this parameter is read from the configuration
        file. 
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/p/?linkid=113216).

INPUTS



OUTPUTS
    RequestForUpdate

        Provides detailed information about the request for update (RFU).



NOTES




    --------------  Example 1 --------------

    C:\PS>Get-RequestForUpdate -RequestForUpdateTicketId TKT-RFU-PROD-ABCD56-1


    Gets the status for a given RequestForUpdateTicketId.



    Ticket             : TKT-RFU-PROD-ABCD56-1
    RfuType            : RetailServicing
    IsApproved         : False
    CreatedOn          : 6/29/2013 7:44:07 AM
    ModifiedOn         : 6/29/2013 7:44:08 AM
    FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
    Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
    Bundles            :
    Attachments        :
    Operations         : 
{Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
    Status             : Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
    ExtensionData      : System.Runtime.Serialization.ExtensionDataObject




RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** None

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Senden Sie ein update](submit-an-update.md)

 

 






