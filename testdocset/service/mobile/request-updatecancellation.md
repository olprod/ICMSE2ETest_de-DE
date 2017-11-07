---
author: kpacquer
Description: Anforderung-UpdateCancellation-cmdlet
ms.assetid: a01ab740-d6a2-4c9e-bfb6-ee3fabb3799a
MSHAttr: PreferredLib:/library/windows/hardware
title: Anforderung-UpdateCancellation-cmdlet
ms.openlocfilehash: b151e57bf0dd69809618137d3d3def7d76928270
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idrequest-updatecancellationspanrequest-updatecancellation-cmdlet"></a><span id="request-updatecancellation"></span>Anforderung-UpdateCancellation-cmdlet


Anzufordern Sie einen Abbruch des einer Firmware Übermittlung Anforderung mit dem Cmdlet **Anforderung UpdateCancellation** .

Sie können entweder OEM/mixed Updates, die über das [Cmdlet New-RequestForUpdate](new-requestforupdate-cmdlet.md)gesendet Abbrechen. Sie können nicht abbrechen eine Anforderung für das Update (RFU) gesendet, um Microsoft Update nach der Live Versand genehmigt wurde.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
    Request-UpdateCancellation [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>] 
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName 
    <StoreName>] [-ClientCertificateThumbprint <String>] 
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


In der Regel ist der einzige Parameter, der in diesem Cmdlet angegeben wird der Firmware Übermittlung Ticket-ID.

``` syntax
Request-UpdateCancellation -RequestForUpdateTicketId 
    TKT-RFU-PROD-ABCD56-1
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>Hilfedokumentation von PowerShell


Es folgt der Hilfedokumentation für das **New-FirmwareSubmission** -Cmdlet von Windows PowerShell.

``` syntax
NAME
    Request-UpdateCancellation
    
SYNOPSIS
    Requests cancellation for the specified ticket.
    
SYNTAX
    Request-UpdateCancellation [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>] 
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName 
    <StoreName>] [-ClientCertificateThumbprint <String>] 
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]
    
    
DESCRIPTION
    Requests cancellation for the specified update request. The request could 
    be for a MicrosoftOemMixed or MicrosoftAKOnly update.
    

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
    
        
        
    
     
    
NOTES
    
    
        
    
    --------------  Example 1 --------------
    
    C:\PS>Request-UpdateCancellation -RequestForUpdateTicketId 
    TKT-RFU-PROD-ABCD56-1
    
    
    Requests cancellation for a given RequestForUpdateTicketId
    
    
    
    
    
    
RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** None

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übermitteln von Binärdateien retail signiert sein](https://msdn.microsoft.com/library/windows/hardware/dn789223)

[Neue RequestForUpdate-cmdlet](new-requestforupdate-cmdlet.md)

[Neue RequestForMicrosoftUpdate-cmdlet](new-requestformicrosoftupdate-cmdlet.md)

 

 






