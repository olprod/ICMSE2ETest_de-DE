---
author: kpacquer
Description: "Sie können bestimmen, ob das Gerät im Modus Manufacturing oder nicht mithilfe einer im Kernelmodus oder Benutzermodus API ist."
ms.assetid: fc888a9a-a004-4689-9972-a40b4d5ba50c
MSHAttr: PreferredLib:/library/windows/hardware
title: Erkennen Manufacturing Modus
ms.openlocfilehash: f4607ffafca8fbd79b499637cd4795bcb8e50ca8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="detect-manufacturing-mode"></a>Erkennen Manufacturing Modus


Sie können bestimmen, ob das Gerät im Modus Manufacturing oder nicht mithilfe einer im Kernelmodus oder Benutzermodus API ist.

Im Kernelmodus wurde eine neue API in wdm.h definiert:

``` syntax
_IRQL_requires_max_(APC_LEVEL)
NTKERNELAPI
BOOLEAN
ExIsManufacturingModeEnabled (
    VOID
    );
```

Es folgt ein Beispiel, wie Sie es verwenden können:

``` syntax
BOOLEAN ManufacturingModeEnabled = FALSE;

NTSTATUS
DriverEntry(
    PDRIVER_OBJECT DriverObject,
    PUNICODE_STRING RegistryPath
    )
{
...
    ManufacturingModeEnabled = ExIsManufacturingModeEnabled();
...
}

NTSTATUS
DoManufacturingOperation(
    VOID
    )
{
    if (ManufacturingModeEnabled == FALSE) {
        return STATUS_NOT_SUPPORTED;
    }
...
    return STATUS_SUCCESS;
}
```

Im Benutzermodus wird die API in sysinfoapi.h definiert:

``` syntax
WINBASEAPI
BOOL
WINAPI
GetOsManufacturingMode(
    _Out_ PBOOL pbEnabled
    );
```

Es folgt ein Beispiel, wie Sie es verwenden können:

``` syntax
DWORD
DoManufacturingOperation(
    VOID
    )
{
    DWORD Error = ERROR_SUCCESS;
    BOOL ManufacturingModeEnabled = FALSE;

    if (!GetOsManufacturingMode(&ManufacturingModeEnabled)) {
        Error = GetLastError();
    }

    if ((Error != ERROR_SUCCESS) ||
        (ManufacturingModeEnabled == FALSE)) {
        return ERROR_NOT_SUPPORTED;
    }
...
    return ERROR_SUCCESS;
}
```

 

 





