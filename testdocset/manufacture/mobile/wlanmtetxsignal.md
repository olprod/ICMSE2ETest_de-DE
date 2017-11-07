---
author: kpacquer
Description: WlanMTETxSignal
ms.assetid: 02a91cb8-de7b-4b96-aa41-7dab33a8d02e
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTETxSignal
ms.openlocfilehash: 5ed45add3a07f1c78f6a8e75e4aacc498b46cf39
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtetxsignal"></a>WlanMTETxSignal


Fordert den Treiber ein Signal am angegebenen Band und DDE-Kanal übertragen.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
DWORD WlanMTETxSignal(
    __in    HANDLE      hAdapter,
    __in    BOOLEAN     bEnable,
    __in    BOOLEAN     bOpenLoop,
    __in    DOT11_BAND  Dot11Band,
    __in    ULONG       uChannel,
    __in    LONG        SetPowerLevel,
    __out   LONG        *pADCPowerLevel
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameter


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[in\] das Handle für den Adapter Wi-Fi durch Aufrufen von [WlanMTEOpenHandle](wlanmteopenhandle.md)abgerufen.

<span id="bEnable"></span><span id="benable"></span><span id="BENABLE"></span>*bAktivieren*  
\[in\] Wenn ein Wert festgelegt ist, die Übertragung aktiviert ist. Andernfalls wird Übermittlung an der angegebenen Band und Channel deaktiviert.

<span id="bOpenLoop"></span><span id="bopenloop"></span><span id="BOPENLOOP"></span>*bOpenLoop*  
\[in\] auf **True**festgelegt, der Treiber muss eine offene Schleife Stromversorgung verwenden und Signal Rückgabewert im *pADCPowerLevel* -Parameter. Wenn dieser Parameter festgelegt ist und die Hardware keine offene Schleife Überwachung der Stromversorgung unterstützt, ein **FEHLER\_NICHT\_UNTERSTÜTZTE** Ausnahme wird zurückgegeben.

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
\[in\] den DDE-Kanal, der das Signal ist übertragen werden. Der Bereich Channel hängt von der Band und PHY-Typen unterstützt.

<span id="SetPowerLevel"></span><span id="setpowerlevel"></span><span id="SETPOWERLEVEL"></span>*SetPowerLevel*  
\[in\] die Power-Ebene der übertragenen Signal in dBm.

<span id="pADCPowerLevel"></span><span id="padcpowerlevel"></span><span id="PADCPOWERLEVEL"></span>*pADCPowerLevel*  
\[Out, optional\] die aktuellen Ebene Signal erkannt, um die Antenne als UNFORMATIERTEN Wert zurückgegeben. Die Auslegung dieses Werts wird von unabhängigen Hardwarehersteller implementiert. Diese Rückgabeparameter ist gültig, wenn *bOpenLoop* **True** ist und die Hardware wird unterstützt.

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
<td align="left"><p>Zurückgegeben, wenn der Parameter <em>Dot11Band</em> oder <em>uChannel</em> NULL ist, oder wenn <em>bOpenLoop</em> vorhanden ist, aber <em>pADCPowerLevel</em> ist NULL.</p></td>
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

 

 






