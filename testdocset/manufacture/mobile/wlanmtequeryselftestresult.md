---
author: kpacquer
Description: WlanMTEQuerySelfTestResult
ms.assetid: 7c728c46-7adb-4b1c-8b0e-85eb58ddd026
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQuerySelfTestResult
ms.openlocfilehash: 8c87cebcb9e53e4b907b4ed27b096f434a5beeda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequeryselftestresult"></a>WlanMTEQuerySelfTestResult


Fragt den Treiber für die Ergebnisse eines zuvor angeforderten self-test.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEQuerySelfTestResult(
    __in                            HANDLE                              hAdapter,
    __in                            DOT11_MANUFACTURING_SELF_TEST_TYPE  eTestType,
    __in                            ULONG                               uTestID,
    __in                            PVOID                               pvContext,
    __out                           BOOLEAN                             *pbResult,
    __out                           ULONG                               *puPinFailedBitMask,
    __out                           ULONG                               *puBytesWrittenOut,
    __in                            ULONG                               uOutBufLen,
    __out_bcount_opt(uOutBufLen)    PUCHAR                              pucOutBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="eTestType"></span><span id="etesttype"></span><span id="ETESTTYPE"></span>*eTestType*  
\[in\] der Typ der Selbsttest angeforderten. Die Werte der *eTestType* definieren, indem der DOT11\_MANUFACTURING\_SELF\_TEST\_TYP-Enumeration, siehe unten:

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
\[in\] des Kontexts, der in der ursprünglichen Anforderung Selbsttest angegeben wurde.

<span id="pbResult"></span><span id="pbresult"></span><span id="PBRESULT"></span>*pbResult*  
\[Skalieren\] das letzte Ergebnis des Selbsttest. **True** Wenn übergeben, **False** , wenn Fehler aufgetreten ist.

<span id="puPinFailedBitMask"></span><span id="pupinfailedbitmask"></span><span id="PUPINFAILEDBITMASK"></span>*puPinFailedBitMask*  
\[Skalieren\] die Bitmaske für Adapter Stifte, die den Test als nicht erfolgreich.

<span id="puBytesWrittenOut"></span><span id="pubyteswrittenout"></span><span id="PUBYTESWRITTENOUT"></span>*puBytesWrittenOut*  
\[Skalieren\] die Anzahl von Bytes des optionalen Daten aus den Ergebnissen Selbsttest zurückgegeben.

<span id="uOutBufLen"></span><span id="uoutbuflen"></span><span id="UOUTBUFLEN"></span>*uOutBufLen*  
\[in\] die Länge des Puffers für zusätzliche Informationen zur Selbsttest zurückgeben.

<span id="pucOutBuffer"></span><span id="pucoutbuffer"></span><span id="PUCOUTBUFFER"></span>*pucOutBuffer*  
\[Skalieren\] Puffer Länge * \*PuBytesWrittenOut* , zusätzliche Informationen zu den Selbsttest bereitstellt. Der Wert der * \*PuBytesWrittenOut* muss kleiner oder gleich dem Wert der *uOutBufLen*.

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Muss die Anwendung erhalten haben eine **dot11\_Fertigung\_Rückruf\_self\_testen\_vollständige** Rückruf, bevor Sie diesen Befehl aufrufen. Sie sollten auch die gleiche Bereitstellen in Reihenfolge zu erzielen das Ergebnis für die entsprechenden Selbsttest Anforderung anzufordern Context-Wert, der in der ursprünglichen Selbsttest verwendet wurde.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. Die folgende Tabelle enthält die Fehlercodes, die möglicherweise zurückgegeben werden.

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
<td align="left"><p>Zurückgegeben, wenn die <em>PbResult</em>, <em>PuPinFailedBitMask</em>oder <em>PuBytesWrittenOut</em> -Parameter NULL ist oder wenn der durch den <em>eTestType</em> -Parameter angegebenen Testtyp ungültig ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das Handle <em>hAdapter</em> ungültig ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>Zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen des Vorgangs zugewiesen werden konnte.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






