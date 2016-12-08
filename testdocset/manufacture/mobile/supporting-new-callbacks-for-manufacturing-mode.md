---
author: kpacquer
Description: "Unterstützung für neue Rückrufe für Fertigung-Modus"
ms.assetid: c94468fa-4581-4d51-9e48-e751d070db28
MSHAttr: PreferredLib:/library/windows/hardware
title: "Unterstützung für neue Rückrufe für Fertigung-Modus"
ms.openlocfilehash: 69c656c35fb1deb36951e80e9baa7dfa2901372f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-new-callbacks-for-manufacturing-mode"></a>Unterstützung für neue Rückrufe für Manufacturing Modus


Bei Ausführung im Modus Fertigung müssen Wi-Fi-Miniporttreiber Unterstützung für die folgenden neuen Rückruf hinzufügen.

## <a name="span-idndisstatusdot11manufacturingcallbackspanspan-idndisstatusdot11manufacturingcallbackspanndisstatusdot11manufacturingcallback"></a><span id="NDIS_STATUS_DOT11_MANUFACTURING_CALLBACK"></span><span id="ndis_status_dot11_manufacturing_callback"></span>NDIS\_STATUS\_DOT11\_MANUFACTURING\_RÜCKRUF


Die **NDIS\_STATUS\_DOT11\_MANUFACTURING\_RÜCKRUF** Rückruf wird verwendet, um für bestimmte Anforderungen Abschlussstatus anzugeben. Hier wird die Datenstruktur für diesen Rückruf festgelegt.

``` syntax
typedef enum _DOT11_MANUFACTURING_CALLBACK_TYPE {
    dot11_manufacturing_callback_unknown = 0,
    dot11_manufacturing_callback_self_test_complete = 1,
    dot11_manufacturing_callback_sleep_complete = 2,
    dot11_manufacturing_callback_IHV_start = 0x80000000,
    dot11_manufacturing_callback_IHV_end = 0xffffffff
} DOT11_MANUFACTURING_CALLBACK_TYPE, * PDOT11_MANUFACTURING_CALLBACK_TYPE;

typedef struct DOT11_MANUFACTURING_CALLBACK_PARAMETERS {
#define DOT11_MANUFACTURING_CALLBACK_REVISION_1  1
    NDIS_OBJECT_HEADER                Header;
    DOT11_MANUFACTURING_CALLBACK_TYPE dot11ManufacturingCallbackType;
    ULONG                             uStatus;
    PVOID                             pvContext;
} DOT11_MANUFACTURING_CALLBACK_PARAMETERS, * PDOT11_MANUFACTURING_CALLBACK_PARAMETERS;
```

<span id="dot11_manufacturing_callback_self_test_complete"></span><span id="DOT11_MANUFACTURING_CALLBACK_SELF_TEST_COMPLETE"></span>**Dot11\_Fertigung\_Rückruf\_self\_testen\_abgeschlossen**  
**dot11\_Fertigung\_Rückruf\_self\_testen\_vollständige** wird durch den Treiber, wenn eine angeforderte aufgerufen Selbsttest abgeschlossen ist, indem der Treiber. In diesem Rückruf muss im Kontext Selbsttest Anforderung als auch das Ergebnis Selbsttest zurückgeben. Der Treiber ruft dann die **OID\_DOT11\_FERTIGUNG\_TESTEN** OID mit der **dot11\_Fertigung\_testen\_self\_Abfrage\_Ergebnis** Befehl aus, um das detaillierte Ergebnis des Tests zu erhalten.

<span id="dot11_manufacturing_callback_sleep_complete"></span><span id="DOT11_MANUFACTURING_CALLBACK_SLEEP_COMPLETE"></span>**Dot11\_Fertigung\_Rückruf\_dem Standbymodus\_abgeschlossen**  
**dot11\_Fertigung\_Rückruf\_dem Standbymodus\_vollständige** wird aufgerufen, wenn ein angeforderte Ruhezustand-Befehl von der Treiber ausgeführt wird. Dieser Rückruf muss Zurückgeben des Kontexts für die Anforderung dem Standbymodus sowie den Status gibt an, ob Erfolg oder Fehler. Dieser Rückruf wird auch beim die Anwendung eine Anforderung an den Treiber aus dem Ruhezustand reaktivieren sendet vom Treiber aufgerufen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






