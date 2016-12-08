---
author: kpacquer
Description: Diese Funktion wird von der Firmware UEFI Startmodus und optional Profilname abgerufen.
ms.assetid: 389dab4d-9f74-4c33-9d02-9b6510581fd8
MSHAttr: PreferredLib:/library/windows/hardware
title: EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. GetBootModeInfo
ms.openlocfilehash: 9510b932ebb239b3d61be02b6a1744ac36669641
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="efibootmodemgmtprotocolgetbootmodeinfo"></a>EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. GetBootModeInfo


Diese Funktion wird verwendet, um die Startmodus und optional Profilname von der Firmware UEFI abzurufen.

``` syntax
typedef EFI_STATUS
(EFIAPI *EFI_GET_BOOT_MODE_INFO)(
    IN  struct _EFI_BOOT_MODE_MGMT_PROTOCOL *This,
    OUT EFI_OS_BOOT_MODE                    *BootMode,
    IN OUT UINT32                           *ProfileNameElements,
    OUT CHAR16                              *ProfileName
    );
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="This"></span><span id="this"></span><span id="THIS"></span>*Dies*  
\[in\] ein Zeiger auf die **EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL** Instanz.

<span id="BootMode"></span><span id="bootmode"></span><span id="BOOTMODE"></span>*Bootmodus*  
\[Skalieren\] einen Zeiger auf die-Aufzählung, die den Startmodus des Geräts enthält.

<span id="ProfileNameElements"></span><span id="profilenameelements"></span><span id="PROFILENAMEELEMENTS"></span>*ProfileNameElements*  
\[in\] \[,\] einen Zeiger auf einen UINT32-Wert, der die Anzahl der Zeichen im Namen Profils empfängt.

<span id="ProfileName"></span><span id="profilename"></span><span id="PROFILENAME"></span>*Profilname*  
\[Skalieren\] einen Zeiger auf den Namen des aktuellen Profils.

## <a name="span-idreturnvaluesspanspan-idreturnvaluesspanspan-idreturnvaluesspanreturn-values"></a><span id="Return_values"></span><span id="return_values"></span><span id="RETURN_VALUES"></span>Rückgabewerte


Gibt einen der folgenden Statuscodes zurück:

| Rückgabecode             | Beschreibung                                                      |
|-------------------------|------------------------------------------------------------------|
| EFI\_ERFOLG            | Erfolg                                                          |
| EFI\_NICHT\_FOUND         | Die Daten der Boot-Modus wurde nicht gefunden.                                |
| EFI\_VOLUME\_ist BESCHÄDIGT  | Eine Partition erforderlichen Speicher ist nicht initialisiert oder ist beschädigt. |
| EFI\_UNGÜLTIGE\_PARAM     | Es wurde ein ungültiger Parameter an die Funktion übergeben.                 |
| EFI\_PUFFER\_TOO\_KLEINE | Nicht genügend Speicherplatz in den bereitgestellten Puffer.                         |

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** Vom Benutzer generiert

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Boot Modus Management UEFI-Protokoll](boot-mode-management-uefi-protocol.md)

 

 






