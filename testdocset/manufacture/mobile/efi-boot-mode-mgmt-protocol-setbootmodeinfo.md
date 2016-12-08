---
author: kpacquer
Description: Diese Funktion liefert eine Startmodus und optional Profilname der Firmware bei nachfolgenden Starts zu verwenden.
ms.assetid: b4cc9267-0237-41eb-bce3-ced8247c42b5
MSHAttr: PreferredLib:/library/windows/hardware
title: EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. SetBootModeInfo
ms.openlocfilehash: b596df16a9137a2970fddbb1d1539817485cdbc5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="efibootmodemgmtprotocolsetbootmodeinfo"></a>EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. SetBootModeInfo


Diese Funktion liefert eine Startmodus und optional Profilname der Firmware bei nachfolgenden Starts zu verwenden.

``` syntax
typedef EFI_STATUS
(EFIAPI *EFI_SET_BOOT_MODE_INFO)(
    IN  struct _EFI_BOOT_MODE_MGMT_PROTOCOL *This,
    IN EFI_OS_BOOT_MODE                    *BootMode,
    IN UINT32                           *ProfileNameElements OPTIONAL,
    IN CHAR16                              *ProfileName OPTIONAL
    );
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="This"></span><span id="this"></span><span id="THIS"></span>*Dies*  
\[in\] ein Zeiger auf die **EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL** Instanz.

<span id="BootMode"></span><span id="bootmode"></span><span id="BOOTMODE"></span>*Bootmodus*  
\[in\] einen Zeiger auf die-Aufzählung, die den Startmodus des Geräts enthält.

<span id="ProfileNameElements"></span><span id="profilenameelements"></span><span id="PROFILENAMEELEMENTS"></span>*ProfileNameElements*  
\[in\] einen Zeiger auf einen UINT32-Wert, der die Anzahl der Zeichen im Profilnamen festgelegt.

<span id="ProfileName"></span><span id="profilename"></span><span id="PROFILENAME"></span>*Profilname*  
\[in\] einen Zeiger auf den Namen des Profils Boot-Modus festlegen.

## <a name="span-idreturnvaluesspanspan-idreturnvaluesspanspan-idreturnvaluesspanreturn-values"></a><span id="Return_values"></span><span id="return_values"></span><span id="RETURN_VALUES"></span>Rückgabewerte


Gibt einen der folgenden Statuscodes zurück:

| Rückgabecode            | Beschreibung                                                      |
|------------------------|------------------------------------------------------------------|
| EFI\_ERFOLG           | Erfolg                                                          |
| EFI\_NICHT\_FOUND        | Die Daten der Boot-Modus wurde nicht gefunden.                                |
| EFI\_VOLUME\_ist BESCHÄDIGT | Eine Partition erforderlichen Speicher ist nicht initialisiert oder ist beschädigt. |
| EFI\_UNGÜLTIGE\_PARAM    | Es wurde ein ungültiger Parameter an die Funktion übergeben.                 |
| EFI\_FEHLERHAFTE\_PUFFER\_GRÖßE | Die Zeichenfolge Profilname ist zu lang.                         |

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** Vom Benutzer generiert

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Boot Modus Management UEFI-Protokoll](boot-mode-management-uefi-protocol.md)

 

 






