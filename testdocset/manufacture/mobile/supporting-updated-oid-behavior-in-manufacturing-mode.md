---
author: kpacquer
Description: "Unterstützung von aktualisierten OID Verhalten in Fertigung-Modus"
ms.assetid: 1ae614a7-fbf9-4c3b-834e-d62d7f7ab352
MSHAttr: PreferredLib:/library/windows/hardware
title: "Unterstützung von aktualisierten OID Verhalten in Fertigung-Modus"
ms.openlocfilehash: 35d980a65afcf99fec7c858afda7d32975d5bf14
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-updated-oid-behavior-in-manufacturing-mode"></a>Unterstützung von aktualisierten OID Verhalten in Fertigung-Modus


Bei Ausführung im Modus Fertigung müssen Wi-Fi-Miniporttreiber Unterstützung für die folgenden aktualisierten OIDs hinzufügen.

## <a name="span-idoiddot11operationmodecapabilityspanspan-idoiddot11operationmodecapabilityspanoiddot11operationmodecapability"></a><span id="OID_DOT11_OPERATION_MODE_CAPABILITY"></span><span id="oid_dot11_operation_mode_capability"></span>OID\_DOT11\_VORGANG\_MODUS\_FUNKTION


Die **OID\_DOT11\_VORGANG\_MODUS\_FUNKTION** Befehl wird aufgerufen, im Abfragemodus, um die Liste der vom Treiber unterstützt Betriebsmodi zurück. Mit diesem Befehl fungiert als bereits dokumentierte, aber -Treiber müssen jetzt einen neue Vorgang im Modus unterstützt **DOT11\_VORGANG\_MODUS\_FERTIGUNG**, also dem Kontext in der Fertigungsvorgänge ausgeführt werden. Die vollständige Dokumentation dieser OID, finden Sie unter [OID\_DOT11\_VORGANG\_MODUS\_FUNKTION](http://msdn.microsoft.com/library/ff569396.aspx) auf MSDN.

``` syntax
#define DOT11_OPERATION_MODE_UNKNOWN            0x00000000
#define DOT11_OPERATION_MODE_STATION            0x00000001
#define DOT11_OPERATION_MODE_AP                 0x00000002
#define DOT11_OPERATION_MODE_EXTENSIBLE_STATION 0x00000004
#define DOT11_OPERATION_MODE_EXTENSIBLE_AP      0x00000008
#define DOT11_OPERATION_MODE_WFD_DEVICE         0x00000010
#define DOT11_OPERATION_MODE_WFD_GROUP_OWNER    0x00000020
#define DOT11_OPERATION_MODE_WFD_CLIENT         0x00000040
#define DOT11_OPERATION_MODE_MANUFACTURING      0x40000000
#define DOT11_OPERATION_MODE_NETWORK_MONITOR    0x80000000

typedef struct _DOT11_OPERATION_MODE_CAPABILITY {
    ULONG uReserved;
    ULONG uMajorVersion;
    ULONG uMinorVersion;
    ULONG uNumOfTXBuffers;
    ULONG uNumOfRXBuffers;
    ULONG uOpModeCapability;
} DOT11_OPERATION_MODE_CAPABILITY, * PDOT11_OPERATION_MODE_CAPABILITY;
```

## <a name="span-idoiddot11currentoperationmodespanspan-idoiddot11currentoperationmodespanoiddot11currentoperationmode"></a><span id="OID_DOT11_CURRENT_OPERATION_MODE"></span><span id="oid_dot11_current_operation_mode"></span>OID\_DOT11\_AKTUELLEN\_VORGANG\_MODUS


Die **OID\_DOT11\_AKTUELLEN\_VORGANG\_MODUS** Befehl kann im Satz oder Abfrage Modus konfigurieren oder Zurückgeben des Treibers aktuellen Operation Modus aufgerufen werden.

Mit diesem Befehl fungiert als bereits dokumentierte, aber der Treiber ist jetzt erforderlich, um die Unterstützung der **DOT11\_VORGANG\_MODUS\_MANUFACTURING** Vorgang Modus. Die vollständige Dokumentation dieser OID, finden Sie unter [OID\_DOT11\_AKTUELLEN\_VORGANG\_MODUS](https://msdn.microsoft.com/library/windows/hardware/ff569132) auf MSDN.

``` syntax
typedef struct _DOT11_CURRENT_OPERATION_MODE {
    ULONG uReserved;
    ULONG uCurrentOpMode;
} DOT11_CURRENT_OPERATION_MODE, * PDOT11_CURRENT_OPERATION_MODE; 
```

<span id="uCurrentOpMode"></span><span id="ucurrentopmode"></span><span id="UCURRENTOPMODE"></span>*uCurrentOpMode*  
\[in\] gibt den Treiber Vorgang Modus festgelegt werden soll. Dieser Parameter dient auch als einen Platzhalter für den Treiber zurückzugebenden den Vorgang-Modus im Abfragemodus aufgerufen. Wenn der Treiber den angeforderten Vorgang Modus nicht unterstützt, sollte er zurückgeben **NDIS\_STATUS\_FEHLERHAFTE\_VERSION**.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






