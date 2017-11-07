---
author: kpacquer
Description: WlanMTEStartSelfTest
ms.assetid: 6c583601-3d26-4a4a-b225-11c2b54ea59b
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEStartSelfTest
ms.openlocfilehash: e63c684a7fb1f1379b775a3aae05a32ed9022207
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtestartselftest"></a>WlanMTEStartSelfTest


Beginnt, Self ein vordefinierten Satz von getestet.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEStartSelfTest(
    __in                        HANDLE                              hAdapter,
    __in                        DOT11_MANUFACTURING_SELF_TEST_TYPE  eTestType,
    __in                        ULONG                               uTestID,
    __in                        PVOID                               pvContext,
    __in                        ULONG                               uPinBitMask,
    __in                        ULONG                               uInBufLen,
    __in_bcount_opt(uInBufLen)  PUCHAR                              pucInBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="eTestType"></span><span id="etesttype"></span><span id="ETESTTYPE"></span>*eTestType*  
\[in\] der Typ der Selbsttest angeforderten. Die Werte der *eTestType* definieren, indem die DOT11\_MANUFACTURING\_SELF\_TEST\_TYP-Aufzählung; siehe unten:

``` syntax
typedef enum DOT11_MANUFACTURING_SELF_TEST_TYPE {
        DOT11_MANUFACTURING_SELF_TEST_TYPE_INTERFACE = 1,
        DOT11_MANUFACTURING_SELF_TEST_TYPE_RF_INTERFACE,
        DOT11_MANUFACTURING_SELF_TEST_TYPE_BT_COEXISTENCE
    } DOT11_MANUFACTURING_SELF_TEST_TYPE, * PDOT11_MANUFACTURING_SELF_TEST_TYPE;
```

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[in\] die ID für den Selbsttest angefordert.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in\] im Kontext, die dieser Anforderung in den Rückruf und in der nachfolgenden Ergebnisabfrage eindeutig identifiziert.

<span id="uPinBitMask"></span><span id="upinbitmask"></span><span id="UPINBITMASK"></span>*uPinBitMask*  
\[in\] die Bitmaske für Adapter Pins auf getestet werden soll.

<span id="uInBufLen"></span><span id="uinbuflen"></span><span id="UINBUFLEN"></span>*uInBufLen*  
\[in\] die Länge des Puffers für zusätzliche Informationen zu den Selbsttest übergeben.

<span id="pucInBuffer"></span><span id="pucinbuffer"></span><span id="PUCINBUFFER"></span>*pucInBuffer*  
\[in\] Puffer, die zusätzliche Informationen zu den Selbsttest enthalten soll.

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Nach Abschluss der Selbsttest, die Anwendung Rückrufhandler wird aufgerufen, wenn eine registriert wurde, mit der **dot11ManufacturingCallbackType** legen Sie auf **dot11\_Fertigung\_Rückruf\_self\_testen\_vollständige**, und das Ergebnis der Selbsttest enthalten ist.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. In der folgenden Tabelle sind die Fehlercodes, die möglicherweise zurückgegeben werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Fehlercode</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ZUSÄTZLICH</p></td>
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>uInBufLen</em> vorhanden ist, aber der Parameter <em>PucInBuffer</em> NULL ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das durch den <em>hAdapter</em> -Parameter angegebenen Adapter Handle ungültig ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>Zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen des Vorgangs reserviert werden kann.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Manufacturing API](wi-fi-manufacturing-api.md)

 

 






