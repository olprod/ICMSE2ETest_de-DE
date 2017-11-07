---
author: kpacquer
Description: Initialize-FirmwareSubmission-cmdlet
ms.assetid: f941c3e5-dea6-444b-aebe-41ca07b24377
MSHAttr: PreferredLib:/library/windows/hardware
title: Initialize-FirmwareSubmission-cmdlet
ms.openlocfilehash: 993a7d88c700c9a8e95598c4a77ff530d36adcd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="initialize-firmwaresubmission-cmdlet"></a>Initialize-FirmwareSubmission-cmdlet


Verwenden Sie dieses Standalone-Cmdlet, um einer Firmware Übermittlung vorzubereiten. Dieses Cmdlet kombiniert die Firmware Übermittlung in einer Zip-Datei auf dem lokalen Computer und kommuniziert nicht mit Partnerdienste.

Verwenden Sie dieses Cmdlet nach [dem Cmdlet New-FirmwareSubmission](new-firmwaresubmission-cmdlet.md) die Zip-Datei hochladen, die die Firmware Übermittlung enthält. Dieses Cmdlet bietet nur ein .NET File-Objekt als Ausgabe. Um die Zip-Datei zu senden, die über dieses Cmdlet erstellt wird, verwenden Sie das Cmdlet " **New-FirmwareSubmission** ".

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten


Erstellen Sie ein Paket mit ImgGen.cmd ein. Dadurch wird mehrere Dateien, einschließlich einer UpdateHistory.xml-Datei und eine für die Zielgruppenadressierung Package-Datei, mit dem Namen im folgenden Format erstellt, in dem &lt;OEM&gt; ist der Name des OEM und &lt;Gerät&gt; ist der Name des Geräts:

&lt;OEM&gt;. &lt;Gerät&gt;. Customizations.MainOS.spkg

Um das gleiche Bild für mehrere OEMs oder Geräte zu verwenden, fügen Sie eine für die Zielgruppenadressierung Datei (PhoneMetadataDeviceTargetingInfo.xml). Weitere Informationen finden Sie unter [DeviceInfo](https://msdn.microsoft.com/library/windows/hardware/mt138322).

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


Im folgenden werden die Parameter für dieses Cmdlet.

<span id="-UpdateHistoryPath__required_"></span><span id="-updatehistorypath__required_"></span><span id="-UPDATEHISTORYPATH__REQUIRED_"></span>*-UpdateHistoryPath (erforderlich)*  
Eine Zeichenfolgenpfad zur Datei UpdateHistory.

<span id="-OemInputPath__required_"></span><span id="-oeminputpath__required_"></span><span id="-OEMINPUTPATH__REQUIRED_"></span>*-OemInputPath (erforderlich)*  
Eine Zeichenfolgenpfad zur Datei OEMInput.xml.

<span id="-TypeOfSubmission__required_"></span><span id="-typeofsubmission__required_"></span><span id="-TYPEOFSUBMISSION__REQUIRED_"></span>*-TypeOfSubmission (erforderlich)*  
Der Typ Übermittlung. Der Typ muss es sich um **Bild**, **FfuCatalog**oder **PartialImage**sein.

<span id="-OutputFilePath__required_"></span><span id="-outputfilepath__required_"></span><span id="-OUTPUTFILEPATH__REQUIRED_"></span>*-OutputFilePath (erforderlich)*  
Ein String-Pfad in der resultierenden Ausgabe Zip-Datei. Wenn dieser Parameter keinen vollständigen Pfad enthält, wird die Ausgabedatei im aktuellen Arbeitsverzeichnis gespeichert.

<span id="-TypeOfProduct"></span><span id="-typeofproduct"></span><span id="-TYPEOFPRODUCT"></span>*-TypeOfProduct*  
Ein optionaler Parameter, der das Zielprodukt Firmware-Übermittlung angibt. Das Produkt muss eine der WindowsPhoneBlue, WindowsPhoneThreshold und WindowsIoTCoreThreshold sein. Der Standardwert lautet WindowsPhoneBlue an.

**Hinweis**  Product-Werte möglicherweise hinzugefügt oder in regelmäßigen Abständen entfernt werden.

 

<span id="-SignedRemovalPackageFolder"></span><span id="-signedremovalpackagefolder"></span><span id="-SIGNEDREMOVALPACKAGEFOLDER"></span>*-SignedRemovalPackageFolder*  
Ein Zeichenfolgenpfad zu einem Ordner, die Entfernung enthält Pakete (mit der Endung .spkr Dateierweiterungen), ein Bild hinzugefügt werden soll.

<span id="-PackagesToRemoveFolder"></span><span id="-packagestoremovefolder"></span><span id="-PACKAGESTOREMOVEFOLDER"></span>*-PackagesToRemoveFolder*  
Ein String Pfad in einen Ordner, der Pakete (mit der Endung .spkg Dateierweiterungen) enthält, die zum Erstellen von Paketen entfernen, auf das Bild verwendet wird.

<span id="-Baseline"></span><span id="-baseline"></span><span id="-BASELINE"></span>*-Baseline*  
Deklarieren einer Firmware Übermittlung einen Basisplan sein, damit sie für den Einzelhandel Wartung (über Anforderung für Update (RFU)) verwendet werden kann. Geplante Übermittlungen müssen Windows-Paket Standardkonfiguration kompatibel sein. Weitere Informationen finden Sie unter [Anforderungen für den Einzelhandel Bilder Windows Standard Packen Konfiguration (WSPC)](https://msdn.microsoft.com/library/dn756781).

Dieses Kennzeichen können nicht mit **– TypeOfSubmission FfuCatalog** oder **– TypeOfSubmission PartialImage**verwendet werden.

Dieses Kennzeichen können nicht außerdem mit **– SignedRemovalPackageFolder** oder **– PackagesToRemoveFolder**verwendet werden.

<span id="-NonWspcCompliant"></span><span id="-nonwspccompliant"></span><span id="-NONWSPCCOMPLIANT"></span>*-NonWspcCompliant*  
Dieser Parameter ist veraltet. Es wurde ursprünglich verwendet, um anzugeben, dass die Übermittlung vorgesehen war, nicht kompatibel mit der Windows Phone Standard Paket Konfiguration (WSPC) sein. Das Modell WSPC geändert hat und dieses Flag wird nicht mehr verwendet.

Weitere Informationen zu WSPC Anforderungen finden Sie unter [Windows Standard Packaging-Konfiguration (WSPC) Anforderungen für den Einzelhandel Bilder](https://msdn.microsoft.com/library/dn756781).

<span id="-FfuPath"></span><span id="-ffupath"></span><span id="-FFUPATH"></span>*-FfuPath*  
Vollständiger Pfad zu einer FFU Datei, die mit dem FFU Katalog zu sendenden angemeldet sein. Fügen Sie diesen Parameter beim Angeben von **– TypeOfSubmission FfuCatalog**.

<span id="-PartialImageDirectory"></span><span id="-partialimagedirectory"></span><span id="-PARTIALIMAGEDIRECTORY"></span>*-PartialImageDirectory*  
Vollständiger Pfad zur ein Verzeichnis, das eine partielle Bild enthält, das nur SPKG Dateien besteht. Fügen Sie diesen Parameter beim **– TypeOfSubmission PartialImage**angeben.

## <a name="span-idsamplewindowspowershellscriptsspanspan-idsamplewindowspowershellscriptsspanspan-idsamplewindowspowershellscriptsspansample-windows-powershell-scripts"></a><span id="Sample_Windows_PowerShell_scripts"></span><span id="sample_windows_powershell_scripts"></span><span id="SAMPLE_WINDOWS_POWERSHELL_SCRIPTS"></span>Windows PowerShell-Skriptbeispiele


Zum Senden von eines Katalogs FFU signiert werden, kann das folgenden Windows PowerShell-Skript verwendet werden.

``` syntax
Initialize-FirmwareSubmission -TypeOfSubmission FfuCatalog –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –FfuPath [path]
```

Das folgende Windows PowerShell-Skript kann verwendet werden, eine partielle Bild zur Darstellung der signierenden übermitteln.

``` syntax
Initialize-FirmwareSubmission -TypeOfSubmission PartialImage –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –PartialImageDirectoy [path]
```

Das folgende Windows PowerShell-Skript zum Lesen von Gültigkeitsfehlern in der Pipeline Ausgabe dieses Cmdlets verwendet werden kann, auf dem \[Pfad\] wird mit den jeweiligen absoluten Dateipfad ersetzt.

``` syntax
try 
{
Initialize-FirmwareSubmission -TypeOfSubmission Image –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –SignedRemovalPackageFolder [path] –PackagesToRemoveFolder [path]
}
catch 
{
# Assuming exception is a validation error
Write-Host $_.Exception.ValidationErrorLog
}
```

## <a name="span-iderrorsspanspan-iderrorsspanspan-iderrorsspanerrors"></a><span id="Errors"></span><span id="errors"></span><span id="ERRORS"></span>Fehler


Wenn die Übermittlung Zip ordnungsgemäß erstellt nicht zur Verfügung, gibt dieses Cmdlet von Windows Powershell eine leere Zeichenfolge zurück. Wenn die Übermittlung Zip wird erstellt, aber Validierungsfehler aufgetreten sind, werden diese Fehler im Fehlerprotokoll in der Übermittlung Zip erfasst.

In Windows Phone 8.1, wurde ein Paket für die Zielgruppenadressierung erforderlich (&lt;OEM&gt;.&lt; Gerät&gt;. Customizations.MainOS.spkg). Wenn dieses Paket nicht enthalten ist, wird eine Ausnahme ausgelöst.

## <a name="span-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanhelp-documentation-from-windows-powershell"></a><span id="Help_documentation_from_Windows_PowerShell"></span><span id="help_documentation_from_windows_powershell"></span><span id="HELP_DOCUMENTATION_FROM_WINDOWS_POWERSHELL"></span>Hilfedokumentation von Windows PowerShell


``` syntax
NAME
    Initialize-FirmwareSubmission

SYNOPSIS


SYNTAX
Initialize-FirmwareSubmission [[-TypeOfProduct] <String>] [[-TypeOfSubmission] <String>] [-UpdateHistoryPath]
    <String> [-OemInputPath] <String> -OutputFilePath <String> [-SignedRemovalPackageFolder <String>]
    [-PackagesToRemoveFolder <String>] [-Baseline] -FfuPath -PartialImageDirectory [<CommonParameters>]]


DESCRIPTION
    This cmdlet is used to prepare a submission .zip for code signing,
    including packages to be signed and related metadata. This cmdlet only
    works on an x86 instance of PowerShell.


PARAMETERS
    -TypeOfProduct <String>
        An optional parameter that specifies the target product of the
        firmware submission. The product must be one of WindowsPhoneBlue and
        WindowsPhoneThreshold. Default is WindowsPhoneBlue.

        Required?                    false
        Position?                    0
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TypeOfSubmission <String>
        Acceptable values are Image, PartialImage, and FfuCatalog.
        Mandatory parameters for Image submission are: UpdateHistoryPath,
        OemInputPath, and OutputFilePath. If you forget a mandatory parameter,
        the cmdlet will prompt you for it.

        Required?                    false
        Position?                    1
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -UpdateHistoryPath <String>
        Full path to UpdateHistory.xml file.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OemInputPath <String>
        Full path to OEMInput.xml file.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OutputFilePath <String>
        Full path to directory which will contain output .zip file.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SignedRemovalPackageFolder <String>
        Full path to directory containing spkrs available to include in
        submission .zip.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -PackagesToRemoveFolder <String>
        Full path to directory containing spkgs for which spkrs need to be
        generated and submitted.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -Baseline
        Indicates that the submission should be marked as baseline, which make this submission eligible for retail
        servicing updates.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -FfuPath <String>
        Full path to an FFU file that contains the FFU catalog to be submitted
        for code signing.  This parameter is only used for a FfuCatalog
        submission.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -PartialImageDirectory <String>
        Full path to a directory containing a partial image that consists of
        only SPKG files.  This parameter is only used for a PartialImage
        submission.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
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
    .NET FileInfo object.

        .NET FileInfo object contains submission .zip ready to submit for code
        signing.

NOTES
    --------------  Non-baseline image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue -TypeOfSubmission Image -UpdateHistoryPath
    c:\input -OemInputPath c:\input -OutputFilePath c:\output





    --------------  Baseline image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneThreshold -TypeOfSubmission Image
    -UpdateHistoryPath c:\input -OemInputPath c:\input -OutputFilePath c:\output -baseline





    --------------  FFU catalog submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneThreshold
            -TypeOfSubmission FfuCatalog -UpdateHistoryPath c:\input -OemInputPath
            c:\input -OutputFilePath c:\output -FfuPath c:\input\flash.ffu




    --------------  Partial image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue
            -TypeOfSubmission PartialImage -UpdateHistoryPath c:\input -OemInputPath
            c:\input -OutputFilePath c:\output -PartialImageDirectory c:\input\spkg




    --------------  Print usage text example.  --------------

    PS C:\> Initialize-FirmwareSubmission


RELATED LINKS
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Anforderungen für den Einzelhandel Bilder Windows Standard Packen Konfiguration (WSPC)](https://msdn.microsoft.com/library/dn756781)

[Neue FirmwareSubmission cmdlet](new-firmwaresubmission-cmdlet.md)

[Übermitteln von Binärdateien retail signiert sein](https://msdn.microsoft.com/library/windows/hardware/dn789223)

 

 






