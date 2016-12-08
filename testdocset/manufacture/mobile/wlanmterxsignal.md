---
author: kpacquer
Description: WlanMTERxSignal
ms.assetid: eb475d1a-0692-44de-aada-1c8c85f2f500
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTERxSignal
ms.openlocfilehash: cd03290bc97866e0583a90aed28446a92361fb18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmterxsignal"></a>WlanMTERxSignal


Abfragen von Informationen zum empfangene Signal zu einem bestimmten Band und DDE-Kanal.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTERxSignal(
    __in    HANDLE      hAdapter,
    __out   BOOLEAN     *pbEnabled,
    __in    DOT11_BAND  Dot11Band,
    __in    ULONG       uChannel,
    __out   LONG        *pPowerLevel
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="pbEnabled"></span><span id="pbenabled"></span><span id="PBENABLED"></span>*pbEnabled*  
\[Skalieren\] **true,** Wenn der Treiber ein Signal an der angegebenen Band und Kanal erkannt. **False,** Wenn kein Signal erkannt wurde.

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[in\] das Band auf dem das Signal ist, erkannt werden. Die Werte des Parameters *Dot11Band* werden definiert, durch die DOT11\_BAND Enum, siehe unten:

``` syntax
typedef enum DOT11_BAND {
        dot11_band_2p4g = 1,
        dot11_band_4p9g,
        dot11_band_5g
    } DOT11_BAND, * PDOT11_BAND;
```

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[in\] den DDE-Kanal, der das Signal ist erkannt werden. DDE-Kanal Range Dependa auf Band ist und auf die unterstützten PHY-Typen.

<span id="pPowerLevel"></span><span id="ppowerlevel"></span><span id="PPOWERLEVEL"></span>*pPowerLevel*  
\[Skalieren\] die Power Ebene des empfangenen Signals an den Antenne zurückgegeben RSSI gemessen in dBm erkannt. Dies ist nur gültig, wenn *bAktiviert* auf **True**festgelegt ist.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>PbEnabled</em>, <em>Dot11Band</em>, <em>uChannel</em>oder <em>pPowerLevel</em> NULL ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>Zurückgegeben, wenn das durch den Parameter <em>hAdapter</em> angegebenen Adapter Handle ungültig ist.</p></td>
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


[Wi-Fi Fertigung-API](wi-fi-manufacturing-api.md)

 

 






