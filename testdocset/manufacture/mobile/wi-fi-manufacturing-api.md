---
author: kpacquer
Description: Wi-Fi Manufacturing API
ms.assetid: 014c7111-cb2f-43a9-a0d0-4b097261493e
MSHAttr: PreferredLib:/library/windows/hardware
title: Wi-Fi Manufacturing API
ms.openlocfilehash: 1b4ba91982b7039067871f6245a5491cc58a603d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wi-fi-manufacturing-api"></a>Wi-Fi Manufacturing API


Im Rahmen des Fertigungsprozesses führen Sie Tests aus, um sicherzustellen, dass die Komponenten integrierte, funktionsfähige und kalibriertes richtig sind, und sie alle Auflagen erfüllen.

In diesem Abschnitt dokumentierten API-Mitglieder sind für unabhängigen Hardwareanbietern zum Schreiben von Anwendungen für den Wi-Fi-Chipsatz Tests definierten Schnittstellen. Diese API-Satz erfordert, dass der Treiber OID Spezifikation der Wi-Fi-Treiber entsprechen.

Diese API Test muss nur im Modus Fertigung verwendet werden. Weitere Informationen finden Sie unter [Determine Wenn MMOS ausgeführt wird](determine-if-mmos-is-running.md).

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_this_section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


Die folgenden Schnittstellen sind für diese API definiert.

<span id="WlanMTEEnumAdapters"></span><span id="wlanmteenumadapters"></span><span id="WLANMTEENUMADAPTERS"></span>[WlanMTEEnumAdapters](wlanmteenumadapters.md)  
Gibt die Liste der Adapter, die von den Wi-Fi-Stapel erkannt werden.

<span id="WlanMTEOpenHandle"></span><span id="wlanmteopenhandle"></span><span id="WLANMTEOPENHANDLE"></span>[WlanMTEOpenHandle](wlanmteopenhandle.md)  
Öffnet einen Handle für den Treiber basierend auf der angegebenen GUID-Schnittstelle, und gibt das Handle für den Anrufer zurück.

<span id="WlanMTECloseHandle"></span><span id="wlanmteclosehandle"></span><span id="WLANMTECLOSEHANDLE"></span>[WlanMTECloseHandle](wlanmteclosehandle.md)  
Schließt einen Handle für den Treiber [WlanMTEOpenHandle](wlanmteopenhandle.md)zuvor geöffnet haben.

<span id="WlanMTERegisterCallbackHandler"></span><span id="wlanmteregistercallbackhandler"></span><span id="WLANMTEREGISTERCALLBACKHANDLER"></span>[WlanMTERegisterCallbackHandler](wlanmteregistercallbackhandler.md)  
Registriert einen Ereignishandler, der aufgerufen wird, wenn der Treiber einen Rückruf für eine Fertigung-Funktion aufruft Ereignis.

<span id="WlanMTEDeRegisterCallbackHandler"></span><span id="wlanmtederegistercallbackhandler"></span><span id="WLANMTEDEREGISTERCALLBACKHANDLER"></span>[WlanMTEDeRegisterCallbackHandler](wlanmtederegistercallbackhandler.md)  
Hebt die Registrierung auf einen Rückrufhandler, damit es nicht mehr aufgerufen wird, tritt ein Ereignis Fertigung-bezogenen Funktionen bereitgestellt.

<span id="WlanMTEGetVendorInfo"></span><span id="wlanmtegetvendorinfo"></span><span id="WLANMTEGETVENDORINFO"></span>[WlanMTEGetVendorInfo](wlanmtegetvendorinfo.md)  
Herstellerspezifische Informationen anfordert, wie die Herstellerklassen-ID und die Beschreibung der Hersteller.

<span id="WlanMTEResetAdapter"></span><span id="wlanmteresetadapter"></span><span id="WLANMTERESETADAPTER"></span>[WlanMTEResetAdapter](wlanmteresetadapter.md)  
Setzt den Wi-Fi-Adapter.

<span id="WlanMTEQueryMacAddress"></span><span id="wlanmtequerymacaddress"></span><span id="WLANMTEQUERYMACADDRESS"></span>[WlanMTEQueryMacAddress](wlanmtequerymacaddress.md)  
Fragt die MAC-Adresse von der Wi-Fi-Adapter.

<span id="WlanMTEQueryPhyTypes"></span><span id="wlanmtequeryphytypes"></span><span id="WLANMTEQUERYPHYTYPES"></span>[WlanMTEQueryPhyTypes](wlanmtequeryphytypes.md)  
Fragt die Liste der 802.11 PHY-Typen für den Adapter konfiguriert.

<span id="WlanMTEStartSelfTest"></span><span id="wlanmtestartselftest"></span><span id="WLANMTESTARTSELFTEST"></span>[WlanMTEStartSelfTest](wlanmtestartselftest.md)  
Beginnt, Self ein vordefinierten Satz von getestet.

<span id="WlanMTEQuerySelfTestResult"></span><span id="wlanmtequeryselftestresult"></span><span id="WLANMTEQUERYSELFTESTRESULT"></span>[WlanMTEQuerySelfTestResult](wlanmtequeryselftestresult.md)  
Fragt den Treiber für die Ergebnisse eines zuvor angeforderten self-test.

<span id="WlanMTERxSignal"></span><span id="wlanmterxsignal"></span><span id="WLANMTERXSIGNAL"></span>[WlanMTERxSignal](wlanmterxsignal.md)  
Abfragen von Informationen zum empfangene Signal an einem DDE-Kanal zu einer bestimmten Band.

<span id="WlanMTETxSignal"></span><span id="wlanmtetxsignal"></span><span id="WLANMTETXSIGNAL"></span>[WlanMTETxSignal](wlanmtetxsignal.md)  
Fordert den Treiber ein Signal am angegebenen Band und DDE-Kanal übertragen.

<span id="WlanMTEQueryADC"></span><span id="wlanmtequeryadc"></span><span id="WLANMTEQUERYADC"></span>[WlanMTEQueryADC](wlanmtequeryadc.md)  
Fordert den Wert des übertragenen Signals beim über eine offene Schleife ausgeführt.

<span id="WlanMTESetData"></span><span id="wlanmtesetdata"></span><span id="WLANMTESETDATA"></span>[WlanMTESetData](wlanmtesetdata.md)  
Fordert, dass der Treiber Daten in einer angegebenen Position und Offset von diesem Speicherort schreiben.

<span id="WlanMTEQueryData"></span><span id="wlanmtequerydata"></span><span id="WLANMTEQUERYDATA"></span>[WlanMTEQueryData](wlanmtequerydata.md)  
Fragt den Treiber für Daten an einen bestimmten Standort und Offset von diesem Standort.

<span id="WlanMTESleep"></span><span id="wlanmtesleep"></span><span id="WLANMTESLEEP"></span>[WlanMTESleep](wlanmtesleep.md)  
Anforderungen, die der Treiber So wechseln in den Energiesparmodus für ein angegebenes Zeitintervall oder auf unbestimmte Zeit, bis der Normalzustand-Anforderung gesendet wird.

<span id="WlanMTEAwake"></span><span id="wlanmteawake"></span><span id="WLANMTEAWAKE"></span>[WlanMTEAwake](wlanmteawake.md)  
Anforderungen, die aus der aktuellen Zustand reaktivieren der Treiber.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






