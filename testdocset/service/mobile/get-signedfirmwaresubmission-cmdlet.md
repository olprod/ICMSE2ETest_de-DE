---
author: kpacquer
Description: Get-SignedFirmwareSubmission-cmdlet
ms.assetid: 911d3704-0508-4aae-8236-59cfd380867b
MSHAttr: PreferredLib:/library/windows/hardware
title: Cmdlet &quot;Get-SignedFirmwareSubmission&quot;
ms.openlocfilehash: ec94ca2379643afdd80024bf3575b272ba82998d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-signedfirmwaresubmission-cmdlet"></a>Cmdlet "Get-SignedFirmwareSubmission"


Die Code signiert Firmware kann nach dem erfolgreichen Senden an Microsoft abgerufen werden. Wenn die Übermittlung erfolgreich ist, erhält der OEM Ticket-Nummer. Verwenden Sie das Cmdlet **Get-SignedFirmwareSubmission** , um die signierten Einreichung für die Code Sign Ticket-Nummer abzurufen.

Es folgt die Syntax für das Cmdlet **Get-SignedFirmwareSubmission** .

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
NAME
     Get-SignedFirmwareSubmission
SYNTAX
     Get-SignedFirmwareSubmission
      [-TicketId] <string>
      [[-DownloadDirectory] <string>]
      [-ServiceUri <uri>]
      [-CertificateStoreLocation <StoreLocation> {CurrentUser | LocalMachine}]
      [-CertificateStoreName <StoreName> {AddressBook | AuthRoot | CertificateAuthority
         | Disallowed | My | Root | TrustedPeople | TrustedPublisher}]
      [-ClientCertificateThumbprint <string>]
      [-EncryptionCertificateThumbprint <string>]
      [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


Normalerweise sind die einzigen Parameter, die für dieses Cmdlet angegeben sind **TicketId** und **DownloadDirectory**.

Das Cmdlet Ruft die Standardwerte für den Rest der Parameter aus einer Konfigurationsdatei. Standardmäßig ist dieser Konfigurationsdatei vom Installationsprogramm am platziert: %ProgramFiles(x86)%\\Microsoft\\WP Aufnahme Client\\Module\\Microsoft.Phone.PartnerServices.Client\\ Microsoft.Phone.PartnerServices.Client.dll.config

Die Config-Datei im Abschnitt dieses Dokuments ist eine Beispieldatei für Config bereitgestellt.

Wenn die nicht erforderliche Parameter explizit in der Befehlszeile angegeben werden, überschreiben diese Werte die Standardwerte festgelegt, die in der Konfigurationsdatei gespeichert sind.

Zur Unterstützung der Windows PowerShell Scripts zur Automatisierung das Cmdlet gibt ein Objekt vom Typ `Microsoft.Phone.PartnerServices.SignedFirmwareSubmission`:

``` syntax
TypeName: Microsoft.Phone.PartnerServices.SignedFirmwareSubmission

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
File        Property   System.IO.FileInfo File {get;set;}
FirmwareSubmissionTicketId    Property   string TicketId {get;set;}
```

Mit diesem Objekt kann bearbeitet werden, mithilfe von Windows PowerShell oder in der Befehlszeile angezeigt. Die folgenden Abschnitte beschreiben allgemeine Verwendungsszenarien und häufig auftretenden Fehlern zum Abrufen von Übermittlungen signiert.

**Hinweis**  
Viele dieser Befehle werden hier in mehreren Zeilen dargestellt, jedoch in Windows PowerShell in einer einzelnen Zeile eingegeben werden müssen.

 

## <a name="span-idexceptionsspanspan-idexceptionsspanspan-idexceptionsspanexceptions"></a><span id="Exceptions"></span><span id="exceptions"></span><span id="EXCEPTIONS"></span>Ausnahmen


Die folgenden Ausnahmen sind für ihre Fehlerszenarien der entsprechenden ausgelöst.

<span id="FaultException_ArgumentFaultDetail_"></span><span id="faultexception_argumentfaultdetail_"></span><span id="FAULTEXCEPTION_ARGUMENTFAULTDETAIL_"></span>**FaultException&lt;ArgumentFaultDetail&gt;**  
-   Die ID eines ungültigen Tickets wurde bereitgestellt. Ticket-ID wurde entweder null oder leer.

<span id="FaultException_InvalidOperationFaultDetail_"></span><span id="faultexception_invalidoperationfaultdetail_"></span><span id="FAULTEXCEPTION_INVALIDOPERATIONFAULTDETAIL_"></span>**FaultException&lt;InvalidOperationFaultDetail&gt;**  
-   Die ID eines ungültigen Tickets wurde bereitgestellt.

-   Ticket-ID ist nicht im Dienst definiert.

-   Der authentifizierte Benutzer ist nicht der Besitzer der Firmware-Übermittlung.

-   Ticket-ID ist ein Ticket Erneutes Senden.

-   Signieren von Code wird noch ausgeführt.

-   Signieren von Code steht zum manuellen Eingriff von Microsoft. Keine OEM-Aktion durchführen.

-   Signieren von Code ist fehlgeschlagen.

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Szenarien


### <a name="span-idretrieveasuccessfullysignedsubmissionspanspan-idretrieveasuccessfullysignedsubmissionspanspan-idretrieveasuccessfullysignedsubmissionspanretrieve-a-successfully-signed-submission"></a><span id="Retrieve_a_successfully_signed_submission"></span><span id="retrieve_a_successfully_signed_submission"></span><span id="RETRIEVE_A_SUCCESSFULLY_SIGNED_SUBMISSION"></span>Abrufen einer erfolgreich signierten Übermittlung

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   Eine Anforderung Firmware wurde zum Signieren von Code erfolgreich übermittelt.

-   Ticket Übermittlung, das von der Firmware Anforderung zurückgegeben wird, ist verfügbar.

-   ERFOLG e-Mail-Benachrichtigung, die gibt an, dass die Firmware Übermittlung erfolgreich signiert wurde wurde vom OEM empfangen.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Abrufen der signierten Übermittlung ein Ticket, und speichern Sie das Ergebnisobjekt in einer Windows PowerShell-Variablen:

``` syntax
PS> $result = Get-SignedFirmwareSubmission –FirmwareSubmissionTicketId TKT-SIGN-TEST-BTUADL 
-DownloadDirectory C:\temp
```

Zeigen Sie die Ergebnisse in der Konsole an:

``` syntax
PS> $result | Format-List

TicketId : TKT-SIGN-TEST-BTUADL
File     : c:\temp\OemTest.TKT-SIGN-TEST-BTUADL.zip
```

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanspan-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanspan-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanattempt-to-retrieve-a-signed-firmware-submission-before-completion"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_before_completion"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_before_completion"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_BEFORE_COMPLETION"></span>Beim Abrufen einer signierten Firmware Übermittlung vor dem Abschluss

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   Eine Anforderung Firmware wurde erfolgreich zum Signieren von Code übermittelt.

-   Das Übermittlung Ticket, das von der Firmware-Anforderung zurückgegeben wird, ist verfügbar.

-   Der Signiervorgang Firmware-Code wird ausgeführt. D. h., das Ticket wurde ausgestellt, aber eine ERFOLG-e-Mail wurde nicht empfangen.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Versuchen Sie, die signierte Einreichung für ein Ticket abzurufen, die noch verarbeitet wird:

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId TKT-SIGN-TEST-XD252Y 
-DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has occurred.  The request could not be processed because the operation is not
valid for the current state of service.
Details: Unable to retrieve the specified firmware submission. Reason: Code signing is still in progress.
Reason: FirmwareSubmissionIsInProgress.
Correlation: 4ab98c1a-df9c-40a9-ac6a-f9b1e9d42e87.
At line:1 char:1
+ Get-SignedFirmwareSubmission TKT-SIGN-TEST-06TV0O c:\temp -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmission], FirmwareSubmissionInProgressExcept
   ion
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException,Microso
   ft.Phone.PartnerServices.Cmdlets.GetSignedFirmwareSubmissionCommand            
```

Dieser Status wird durch die zurückgegebene Grund "Code signing noch ausgeführt wird" angezeigt.

Wenn ein benutzerdefiniertes Powershellskript verwendet wird, können sie eine Ausnahme (Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException) abfangen programmiert werden. Diese Ausnahme kann untersucht werden, um festzustellen, ob die Übermittlung abgeschlossen wurde. Das folgende Codebeispiel veranschaulicht, wie die Fehlerinformationen aus dem Objekt zurückgegebene Ergebnis zu extrahieren.

``` syntax
      $result = ''
        try {
            $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId "TKT-SIGN-TEST-17Y8M5" -DownloadDirectory c:\MyFirmwareSubmissions
        }
        catch [Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException] {
            write-host "Error Message" + $_.Exception.Message
            write-host "Error Detail" + $_.Exception.Detail
            
            #exit or take other action since we've detected a failure
            exit 1
        } 
```

Eine Schleife kann zum Warten (mindestens 30 Minuten), und versuchen Sie erneut zu ermitteln, ob die Übermittlung abgeschlossen wurde erstellt werden. Es wird dringend empfohlen, dass solche eine Abruf Formatvorlage mit Intervallen von weniger als 30 Minuten zur Vermeidung einer Überlastung des Update-Servers nicht aufgerufen werden muss.

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanattempt-to-retrieve-a-signed-firmware-submission-when-the-request-has-failed"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_when_the_request_has_failed"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_when_the_request_has_failed"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_WHEN_THE_REQUEST_HAS_FAILED"></span>Beim Abrufen einer signierten Firmware-Übermittlung, wenn die Anforderung ein Fehler aufgetreten ist

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   Eine Anforderung Firmware wurde erfolgreich zum Signieren von Code übermittelt.

-   Das Übermittlung Ticket, das von der Firmware Anforderung zurückgegeben wird ist verfügbar.

-   Der Signiervorgang Firmware-Code ist dauerhaft fehlgeschlagen. D. h., wurde eine Benachrichtigung über e-Mail vom OEM für Ticket empfangen.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

Versuchen Sie, die signierte Einreichung für ein Ticket abzurufen, die dauerhaft ein Fehler aufgetreten ist:

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId TKT-SIGN-TEST-TUKJGG -DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has occurred.  The request could not be
processed because the operation is not valid for the current state of service.
Details: Unable to retrieve the specified firmware submission. Reason: Code
signing has failed.
Reason: FirmwareSubmissionHasFailed.
Correlation: 67a645af-19b7-468d-9f7a-4a3fd341a15e.
At line:1 char:11
+ $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
TKT-SIGN-TEST ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmiss
   ion], FirmwareSubmissionFailedException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Firmw
   areSubmissionFailedException,Microsoft.Phone.PartnerServices.Cmdlets.GetSi
  gnedFirmwareSubmissionCommand
```

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanattempt-to-retrieve-a-signed-firmware-submission-when-the-ticket-does-not-exist"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_when_the_ticket_does_not_exist"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_when_the_ticket_does_not_exist"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_WHEN_THE_TICKET_DOES_NOT_EXIST"></span>Beim Abrufen einer signierten Firmware-Übermittlung, wenn das Ticket nicht vorhanden ist

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>Szenario erforderlichen Komponenten

-   OEM versucht, eine Zahl Ticket abzurufen, die nicht vorhanden ist.

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>Beispiel-Verwendung mit erwartete Ausgabe

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId bad_ticket_number -DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has ocurred.  The request could not be
processed because the operation is not valid for the current state of service.
Details: The specified FirmwareSubmission ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: fd8bb041-fe0f-46ea-9b89-ccf91a57178c.
At line:1 char:11
+ $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
TKT-SIGN-TEST ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmiss
   ion], TicketDoesNotExistException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Ticke
   tDoesNotExistException,Microsoft.Phone.PartnerServices.Cmdlets.GetSignedFi
  rmwareSubmissionCommand
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>Hilfedokumentation von PowerShell


Es folgt der Hilfedokumentation für das Cmdlet **Get-SignedFirmwareSubmission** von Windows PowerShell.

``` syntax
NAME
    Get-SignedFirmwareSubmission

SYNOPSIS
    Gets a signed firmware submission for a given firmware submission ticket.

SYNTAX
    Get-SignedFirmwareSubmission [-FirmwareSubmissionTicketId] <String>
    [[-DownloadDirectory] <String>] [-ServiceUri <Uri>]
    [-ServiceAccessControlNamespace <String>] [-CertificateStoreLocation
    <StoreLocation>] [-CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint
    <String>] [<CommonParameters>]


DESCRIPTION
    Downloads a signed firmware submission for a given ticket id.

            The download can only be performed after a new firmware submission
    has been created and uploaded with the OemSubmit tool or WP Ingestion
    Client and the uploaded files have been signed by Microsoft. Otherwise it
    will throw an error.


PARAMETERS
    -FirmwareSubmissionTicketId <String>
        Firmware-Submission ticket. Must be a valid ticket.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -DownloadDirectory <String>
        The download directory for the signed firmware-submission. Must be a
        full path to the download directory.

                    A default value can be defined in the configuration file.

        Required?                    false
        Position?                    3
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
        parameter is read from the configuration file. Should only be modified
        if instructed by the system administrator or Microsoft

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
    SignedFirmwareSubmission

        Contains information about the downloaded file and the firmware
        submission ticket related to the signing.

NOTES
    --------------  Example 1 --------------

    C:\PS>Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCDEF -DownloadDirectory
    C:\SignedFirmwareSubmissionDownloads | Format-List


    Successful download of a signed firmware-submission read for download.

                The ticket id is TKT-SIGN-PROD-ABCDEF and the zip-file is
    downloaded to directory C:\SignedFirmwareSubmissionDownloads.



    FirmwareSubmissionTicketId : TKT-SIGN-PROD-ABCDEF
                File     :
    c:\SignedFirmwareSubmissionDownloads\OemTest.TKT-SIGN-PROD-ABCDEF.zip

RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** None

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übermitteln von Binärdateien retail signiert sein](https://msdn.microsoft.com/library/windows/hardware/dn789223)

 

 






