---
author: kpacquer
Description: WlanMTEQueryADC
ms.assetid: 59b02678-f928-4b9e-837b-9c148aaedcfc
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQueryADC
ms.openlocfilehash: cff140553e837a5ee6d1309dd946b2543d53dab1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequeryadc"></a>WlanMTEQueryADC


Fordert den Wert des übermittelten Signals bei der über eine offene Schleife ausgeführt.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTEQueryADC(
    __in    HANDLE      hAdapter,
    __in    DOT11_BAND  Band,
    __in    ULONG       uChannel,
    __out   LONG        *pADCPowerLevel
    );
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="Band"></span><span id="band"></span><span id="BAND"></span>*Band*  
\[in\] das Band auf dem das Signal ist, erkannt werden. Die Werte des Parameters *Dot11Band* werden definiert, durch die DOT11\_BAND Enum, siehe unten:

``` syntax
typedef enum DOT11_BAND {
        dot11_band_2p4g = 1,
        dot11_band_4p9g,
        dot11_band_5g
    } DOT11_BAND, * PDOT11_BAND;
```

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[in\] den DDE-Kanal auf dem das Signal übertragen werden. Der Kanalbereich DDE-, hängt von der Band und PHY-Typen unterstützt.

<span id="pADCPowerLevel"></span><span id="padcpowerlevel"></span><span id="PADCPOWERLEVEL"></span>*pADCPowerLevel*  
\[Skalieren\] der aktuellen Audiosignals unter Antenne erkannt als UNFORMATIERTEN Wert zurückgegeben. Die Interpretation der dieser Wert wird von unabhängigen Hardwarehersteller implementiert werden. Dieser Parameter gilt nur, wenn das Gerät offene Schleife Power unterstützt und derzeit eines Signals in der Schleife öffnen Übertragung ist.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>Dot11Band</em>, <em>uChannel</em>oder <em>pADCPowerLevel</em> NULL ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das Handle <em>hAdapter</em> ungültig ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>Zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen des Vorgangs reserviert werden kann.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise


Wenn offene Schleife Power nicht unterstützt wird, kann der Treiber zurückgegebenen **FEHLER\_NICHT\_UNTERSTÜTZTE**.

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Rückgabewert


Wenn die Funktion erfolgreich ist, wird der Rückgabewert ist FEHLER\_ERFOLG.

Wenn die Funktion fehlschlägt, ist der Rückgabewert eines Fehlercodes System. Die folgende Tabelle listet eines die Fehlercodes, die zurückgegeben werden können.

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
<td align="left"><p>Die Zugriffsnummer <em>hAdapter</em> ist ungültig.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>Ist nicht genügend Arbeitsspeicher zum Ausführen der Funktion reservieren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






