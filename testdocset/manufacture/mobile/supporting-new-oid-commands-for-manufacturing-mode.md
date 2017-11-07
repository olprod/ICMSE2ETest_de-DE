---
author: kpacquer
Description: "Unterstützung für neue OID Befehle für Fertigung-Modus"
ms.assetid: 0ebb9581-043e-47f8-84c9-6fa97c0900cc
MSHAttr: PreferredLib:/library/windows/hardware
title: "Unterstützung für neue OID Befehle für Fertigung-Modus"
ms.openlocfilehash: 6b54c5ec5aacae5a18a9ec480d1f6a5e9d665c83
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-new-oid-commands-for-manufacturing-mode"></a>Unterstützung für neue OID Befehle für Fertigung-Modus


Bei Ausführung im Modus Fertigung müssen Miniporttreiber Wi-Fi-Unterstützung für die folgenden neuen OID Befehle hinzufügen. Der Treiber sollten sicherstellen, dass das Gerät aktuell im Modus vor dem Aufrufen von einen der folgenden Befehle Fertigung ist. Weitere Informationen finden Sie unter [Determine Wenn MMOS ausgeführt wird](determine-if-mmos-is-running.md). Einige der in der API angegebenen Parameter können IHV-spezifischen sein.

## <a name="span-idoiddot11manufacturingtestspanspan-idoiddot11manufacturingtestspanoiddot11manufacturingtest"></a><span id="OID_DOT11_MANUFACTURING_TEST"></span><span id="oid_dot11_manufacturing_test"></span>OID\_DOT11\_MANUFACTURING\_TEST


OID\_DOT11\_MANUFACTURING\_heißt TEST als Anforderung Methode in der Treiber ein bestimmtes Tests ausführen. Diese OID sollte niemals während des normalen Betriebs verwendet werden.

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST {
    DOT11_MANUFACTURING_TEST_TYPE dot11ManufacturingTestType;
    ULONG uBufferLength;
    UCHAR ucBuffer[1];
} DOT11_MANUFACTURING_TEST, * PDOT11_MANUFACTURING_TEST;
```

<span id="dot11ManufacturingTestType"></span><span id="dot11manufacturingtesttype"></span><span id="DOT11MANUFACTURINGTESTTYPE"></span>*dot11ManufacturingTestType*  
\[in\] gibt den Fertigung Test ausgeführt werden soll. Der Datentyp für diesen Member ist einer der Werte von den **DOT11\_MANUFACTURING\_TEST\_TYPE** Enumeration.

Die DOT11 manufacturing Test Typ-Enumeration wird wie folgt definiert:

``` syntax
typedef enum _DOT11_MANUFACTURING_TEST_TYPE {
    dot11_manufacturing_test_unknown = 0,
    dot11_manufacturing_test_self_start = 1,
    dot11_manufacturing_test_self_query_result = 2,
    dot11_manufacturing_test_rx = 3,
    dot11_manufacturing_test_tx = 4,
    dot11_manufacturing_test_set_data = 5,
    dot11_manufacturing_test_query_data = 6,
    dot11_manufacturing_test_sleep = 7,
    dot11_manufacturing_test_awake = 8,
    dot11_manufacturing_test_IHV_start = 0x80000000,
    dot11_manufacturing_test_IHV_end = 0xffffffff
} DOT11_MANUFACTURING_TEST_TYPE, * PDOT11_MANUFACTURING_TEST_TYPE;
```

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[in\] die Länge in Bytes, der die **DOT11\_MANUFACTURING\_TESTEN** Struktur und zusätzlichen Daten speziell für den Test am Ende angefügt.

<span id="ucBuffer"></span><span id="ucbuffer"></span><span id="UCBUFFER"></span>*ucBuffer*  
\[in\] den Puffer mit optionalen Daten gemäß der **dot11DiagnosticsTestType** Member.

## <a name="span-iddot11manufacturingtestselfstartspanspan-iddot11manufacturingtestselfstartspandot11manufacturingtestselfstart"></a><span id="dot11_manufacturing_test_self_start"></span><span id="DOT11_MANUFACTURING_TEST_SELF_START"></span>Dot11\_Fertigung\_testen\_self\_starten


Die **dot11\_Fertigung\_testen\_self\_starten** Befehl wird aufgerufen, um den Treiber zum Testen der WLAN-IC-Konnektivität, FEM IC-Konnektivität oder der WLAN-BT Koexistenz Schnittstelle anfordern.

**DOT11\_DIAGNOSTIC\_SELF\_TEST\_BT\_KOEXISTENZ** gilt nur, wenn der WLAN- und Bluetooth-Chips in separaten ICs befinden. Werden auf dem gleichen Modul bei diesem Test wird nicht unterstützt und sollte der Miniport zurückgeben **NDIS\_STATUS\_NICHT\_UNTERSTÜTZTE**.

Wenn aufgerufen, der Treiber sollte die angeforderte Tests ausführen im Sinne der **DOT11\_MANUFACTURING\_SELF\_TEST\_FESTLEGEN\_PARAMS** strukturieren und Erfolg zurückgeben, wenn die Tests gestartet wurden. Nach Abschluss des, ob die Tests wurden erfolgreich abgeschlossen oder fehlgeschlagen ist, sollte der Treiber den Status mithilfe von angeben die **NDIS\_STATUS\_DOT11\_FERTIGUNG\_RÜCKRUF** Rückrufhandler mit der *dot11ManufacturingCallbackType* legen Sie auf **dot11\_Fertigung\_Rückruf\_self\_testen\_abgeschlossen** und den Status, beschreibt das Ergebnis des Tests. Der Treiber ruft dann die **OID\_DOT11\_FERTIGUNG\_TESTEN** Oid mit der **dot11\_Fertigung\_testen\_self\_Abfrage\_Ergebnis** Befehl aus, um den detaillierten Ergebnis des Tests Abfragen.

``` syntax
typedef struct _DOT11_MANUFACTURING_SELF_TEST_SET_PARAMS {
    DOT11_MANUFACTURING_SELF_TEST_TYPE SelfTestType;
    ULONG uTestID;
    ULONG uPinBitMask;
    PVOID pvContext;
    ULONG uBufferLength;
    UCHAR ucBufferIn[1];
} DOT11_MANUFACTURING_SELF_TEST_SET_PARAMS, *PDOT11_MANUFACTURING_SELF_TEST_SET_PARAMS;
```

<span id="SelfTestType"></span><span id="selftesttype"></span><span id="SELFTESTTYPE"></span>*SelfTestType*  
\[in\] gibt den Typ der Selbsttest vom Treiber ausgeführt werden. Der Datentyp für dieses Element ist das **DOT11\_MANUFACTURING\_SELF\_TEST\_TYP** Enumeration mit einem der folgenden Werte:

<span id="DOT11_MANUFACTURING_SELF_TEST_INTERFACE"></span><span id="dot11_manufacturing_self_test_interface"></span>**DOT11\_MANUFACTURING\_SELF\_TEST\_SCHNITTSTELLE**  
-   Steuerung und Daten WLAN-Schnittstelle

-   Uhr-Anforderung

-   Dem Standbymodus Takt

-   Interrupt und Power angeben Zeilen

-   Alle zugehörigen Verbindungen

<span id="DOT11_MANUFACTURING_SELF_TEST_RF_INTERFACE"></span><span id="dot11_manufacturing_self_test_rf_interface"></span>**DOT11\_MANUFACTURING\_SELF\_TEST\_RF\_SCHNITTSTELLE**  
-   -Steuerelement und RF FEM-IC-Schnittstelle

-   FEM Stromversorgung

-   Übertragen Signal Loopback Pfad von TX Schnittstelle RX-Schnittstelle und überprüft werden.

<span id="DOT11_MANUFACTURING_SELF_TEST_BT_COEXISTENCE"></span><span id="dot11_manufacturing_self_test_bt_coexistence"></span>**DOT11\_MANUFACTURING\_SELF\_TEST\_BT\_KOEXISTENZ**  
-   Festlegen von Zeile Zustände von Bluetooth-Seite und Lesen von Zeile Zustände von WLAN-Seite

-   Überprüfen Sie jeden Pin-Status

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[in\] ID des Tests ausgeführt werden.

<span id="uPinBitMask"></span><span id="upinbitmask"></span><span id="UPINBITMASK"></span>*uPinBitMask*  
\[in\] Bitmaske für die Pins auf getestet werden soll.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in\] Context-Wert an die Anwendung zurückgegeben werden soll, mithilfe von **dot11\_Fertigung\_Rückruf\_self\_testen\_vollständige Rückruf** Wenn der Treiber die Tests abgeschlossen hat.

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[in optionalen\] die Länge des Puffers mit weiteren Eingaben für den Selbsttest.

<span id="ucBufferIn"></span><span id="ucbufferin"></span><span id="UCBUFFERIN"></span>*ucBufferIn*  
\[in optionalen\] der Puffer, zusätzliche Eingaben für den Selbsttest enthält.

## <a name="span-iddot11manufacturingtestselfqueryresultspanspan-iddot11manufacturingtestselfqueryresultspandot11manufacturingtestselfqueryresult"></a><span id="dot11_manufacturing_test_self_query_result"></span><span id="DOT11_MANUFACTURING_TEST_SELF_QUERY_RESULT"></span>Dot11\_Fertigung\_testen\_self\_Abfrage\_Ergebnis


Dieser Befehl ruft die Ergebnisse einer zuvor angeforderten Selbsttest ab. Sollte nur aufgerufen werden, wenn der Treiber angegeben hat, dass der Selbsttest abgeschlossen mithilfe der **NDIS\_STATUS\_DOT11\_MANUFACTURING\_RÜCKRUF** mit der *dot11ManufacturingCallbackType* , legen Sie auf **dot11\_manufacturing\_Rückruf\_self\_testen\_abgeschlossen** sowie den Status, die das Ergebnis des Tests beschreibt.

``` syntax
typedef struct _DOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS {
    DOT11_MANUFACTURING_SELF_TEST_TYPE SelfTestType;
    ULONG uTestID;
    BOOLEAN bResult;                    // PASS/FAIL
    ULONG uPinFailedBitMask;            // Detected PIN faults
    PVOID pvContext;
    ULONG uBytesWrittenOut;
    UCHAR ucBufferOut[1];               // Additional output from self-test (optional)
} DOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS, *PDOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS;
```

<span id="SelfTestType"></span><span id="selftesttype"></span><span id="SELFTESTTYPE"></span>*SelfTestType*  
\[in\] gibt den Typ der self-test, dessen Ergebnis abgefragt wird. Der Datentyp für dieses Element ist das **DOT11\_MANUFACTURING\_SELF\_TEST\_TYP** Enumeration.

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[in\] ID des Tests ausgeführt werden.

<span id="bResult"></span><span id="bresult"></span><span id="BRESULT"></span>*bResult*  
\[Skalieren\] das Ergebnis des Tests. **True,** Wenn der Test erfolgreich war, **False** , wenn es nicht erfolgreich.

<span id="uPinFailedBitMask"></span><span id="upinfailedbitmask"></span><span id="UPINFAILEDBITMASK"></span>*uPinFailedBitMask*  
\[Skalieren\] die Bitmaske einer PIN Cachefehler erkannt.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in\] Kontext verwendet, wenn der Treiber angegeben, dass die Tests abgeschlossen wurden.

<span id="uBytesWrittenOut"></span><span id="ubyteswrittenout"></span><span id="UBYTESWRITTENOUT"></span>*uBytesWrittenOut*  
\[Skalieren\] die Länge des Puffers, die keine zusätzliche zurückgegebene Ausgabe aus der Selbsttest enthält.

<span id="ucBufferOut"></span><span id="ucbufferout"></span><span id="UCBUFFEROUT"></span>*ucBufferOut*  
\[eingehend, ausgehend, optional\] Puffer der Länge *uBytesWrittenOut* aus, die zusätzliche Ausgabe aus der Selbsttest enthält.

## <a name="span-iddot11manufacturingtestrxspanspan-iddot11manufacturingtestrxspandot11manufacturingtestrx"></a><span id="dot11_manufacturing_test_rx"></span><span id="DOT11_MANUFACTURING_TEST_RX"></span>Dot11\_Fertigung\_testen\_Rx


Die **dot11\_Fertigung\_testen\_Rx** nur-Lese-Befehl getestet und überprüft, ob Verbindungen zwischen den Antenne Port und WLAN-IC-vorhanden ist.

Um diese Verbindungen zu testen, generiert ein Signalgenerator eine nicht moduliert Netzbetreiber Welle (Unternehmen oder Arbeitsgruppe) mit einer bestimmten Häufigkeit und Stromversorgung, die gemessen und vom Gerät unter Test (DUT) zurückgegeben wird. Wenn die Band und/oder Channel Einstellung inkonsistent sind, und klicken Sie dann der Treiber gibt **STATUS\_UNGÜLTIGE\_PARAMETER**.

``` syntax
typedef struct _DOT11_MANUFACTURING_FUNCTIONAL_TEST_RX {
    BOOLEAN bEnabled;
    DOT11_BAND Dot11Band;
    ULONG uChannel;
    LONG  PowerLevel;
} DOT11_MANUFACTURING_FUNCTIONAL_TEST_RX, * PDOT11_MANUFACTURING_FUNCTIONAL_TEST_RX;
```

<span id="bEnabled"></span><span id="benabled"></span><span id="BENABLED"></span>*bAktiviert*  
\[Skalieren\] **true,** Wenn der Treiber ein Signal am angegebenen Band und Kanal erkannt. **False,** Wenn kein Signal erkannt wurde.

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[in\] das Band auf dem das Signal ist, erkannt werden.

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[in\] den DDE-Kanal, der das Signal ist erkannt werden. Der Bereich Channel hängt von der Band und unterstützt Blatt.

<span id="PowerLevel"></span><span id="powerlevel"></span><span id="POWERLEVEL"></span>*PowerLevel*  
\[Skalieren\] die Power-Ebene des empfangenen Signals an die Antenne zurückgegeben, wie die RSSI in dBm gemessen erkannt. Dies ist nur gültig, wenn *bAktiviert* auf **True**festgelegt ist.

## <a name="span-iddot11manufacturingtesttxspanspan-iddot11manufacturingtesttxspandot11manufacturingtesttx"></a><span id="dot11_manufacturing_test_tx"></span><span id="DOT11_MANUFACTURING_TEST_TX"></span>Dot11\_Fertigung\_testen\_tx


Die **dot11\_Fertigung\_testen\_tx** lesegeschützte Befehl überprüft die Verbindung zwischen dem Chipsatz und die FEM-Ausgabe.

Um diesen Test durchführen, ein Signal Analyzer physisch auf den Port Antenne verbunden ist und die DUT zum Übertragen von einem Unternehmen mit bestimmten Band, DDE-Kanal und Power-Einstellungen auf Poolebene oder Arbeitsgruppe angefordert wird. Der Treiber misst eigene ADC Lesen für die übertragenen Signal auch und an die Anwendung zurückgegeben.

``` syntax
typedef struct _DOT11_MANUFACTURING_FUNCTIONAL_TEST_TX {
    BOOLEAN bEnable;
    BOOLEAN bOpenLoop;
    DOT11_BAND Dot11Band;
    ULONG uChannel;
    ULONG uSetPowerLevel;
    LONG  ADCPowerLevel;
} DOT11_MANUFACTURING_FUNCTIONAL_TEST_TX, * PDOT11_MANUFACTURING_FUNCTIONAL_TEST_TX;
```

<span id="bEnable"></span><span id="benable"></span><span id="BENABLE"></span>*bAktivieren*  
\[in\] festgelegt, diesen Befehl Übertragung aktiviert. Wenn nicht festgelegt wurden, Übermittlung an der angegebenen Band und Channel deaktiviert sind.

<span id="bOpenLoop"></span><span id="bopenloop"></span><span id="BOPENLOOP"></span>*bOpenLoop*  
\[in\] Wenn auf **true**festgelegt ist, gibt dieser Parameter an, dass der Treiber eine offene Schleife Stromversorgung verwenden und den Wert lesen Signal in *ADCPowerLevel*zurückgegeben angefordert wird. Wenn es sich bei Festlegung auf **"false"**, der Treiber eine offene Schleife Stromversorgung nicht verwendet wird.

Wenn dieser Wert festgelegt ist und die Hardware keine offene Schleife Überwachung der Stromversorgung unterstützt, gibt der Treiber **NDIS\_STATUS\_NICHT\_UNTERSTÜTZTE**.

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[in\] das Band auf dem ist das Signal übertragen werden.

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[in\] den DDE-Kanal, der das Signal ist übertragen werden. Der Bereich Channel hängt von der Band und unterstützt Blatt.

<span id="uSetPowerLevel"></span><span id="usetpowerlevel"></span><span id="USETPOWERLEVEL"></span>*uSetPowerLevel*  
\[in\] die Power-Ebene des übertragenen Signals. Dies wird als Prozentsatz der maximalen Energie-Ebene zurückgegeben.

<span id="ADCPowerLevel"></span><span id="adcpowerlevel"></span><span id="ADCPOWERLEVEL"></span>*ADCPowerLevel*  
\[Out, optional\] die aktuellen Ebene Signal erkannt, um die Antenne als UNFORMATIERTEN Wert zurückgegeben. Die Auslegung dieses Werts wird durch unabhängigen Hardwarehersteller angegeben.

Dies muss festgelegt werden, wenn *bOpenLoop* **True** ist und die Hardware wird unterstützt.

## <a name="span-iddot11manufacturingtestsetdataspanspan-iddot11manufacturingtestsetdataspandot11manufacturingtestsetdata"></a><span id="dot11_manufacturing_test_set_data"></span><span id="DOT11_MANUFACTURING_TEST_SET_DATA"></span>Dot11\_Fertigung\_testen\_festgelegt\_Daten


Die **dot11\_Fertigung\_testen\_festlegen\_Daten** lesegeschützte Befehl wird die Anwendung zum Schreiben von Daten an einer bestimmten Position.

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_SET_DATA {
    ULONG uKey;
    ULONG uOffset;
    ULONG uBufferLength;
    UCHAR ucBufferIn[1];
} DOT11_MANUFACTURING_TEST_SET_DATA, * PDOT11_MANUFACTURING_TEST_SET_DATA;
```

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[in\] der Schlüssel ist IHV bestimmte und kann einen Verweis auf ein bestimmtes Register oder einen Eintrag aus einer benannten Tabelle sein.

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[in\] den Offset innerhalb der Daten.

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[in\] die Anzahl von Datenbytes im Puffer zusätzliche Testdaten enthalten sein soll.

<span id="ucBufferIn"></span><span id="ucbufferin"></span><span id="UCBUFFERIN"></span>ucBufferIn  
\[in\] der Puffer, die zusätzliche Testdaten der Länge *uBufferLength*enthält.

## <a name="span-iddot11manufacturingtestquerydataspanspan-iddot11manufacturingtestquerydataspandot11manufacturingtestquerydata"></a><span id="dot11_manufacturing_test_query_data"></span><span id="DOT11_MANUFACTURING_TEST_QUERY_DATA"></span>Dot11\_Fertigung\_testen\_Abfrage\_Daten


Die **dot11\_Fertigung\_testen\_Abfrage\_Daten** Befehl wird die Anwendung zum Lesen von Daten an einer bestimmten Position.

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_QUERY_DATA {
    ULONG uKey;
    ULONG uOffset;
    ULONG uBufferLength;
    ULONG uBytesRead;
    UCHAR ucBufferOut[1];
} DOT11_MANUFACTURING_TEST_QUERY_DATA, * PDOT11_MANUFACTURING_TEST_QUERY_DATA;
```

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[in\] der Schlüssel ist IHV bestimmte und kann einen Verweis auf einem bestimmten Register oder einen Eintrag aus einer benannten Tabelle sein.

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[in\] den Offset innerhalb der Daten.

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[in\] die Anzahl von Datenbytes im Puffer gelesen werden sollen.

<span id="uBytesRead"></span><span id="ubytesread"></span><span id="UBYTESREAD"></span>uBytesRead  
\[Skalieren\] lesen Sie die tatsächliche Anzahl von Datenbytes vom Treiber.

<span id="ucBufferOut"></span><span id="ucbufferout"></span><span id="UCBUFFEROUT"></span>ucBufferOut  
\[Skalieren\] die vom Treiber gelesenen Daten enthält.

## <a name="span-iddot11manufacturingtestsleepspanspan-iddot11manufacturingtestsleepspandot11manufacturingtestsleep"></a><span id="dot11_manufacturing_test_sleep"></span><span id="DOT11_MANUFACTURING_TEST_SLEEP"></span>Dot11\_Fertigung\_testen\_dem Standbymodus


Die **dot11\_Fertigung\_testen\_dem Standbymodus** Befehl weist den Wi-Fi-Chipsatz So wechseln in den niedrigsten Power-Zustand für entweder einen angegebenen Zeitraum oder unbegrenzt.

Für diesen Test alle Sender deaktiviert werden soll, und der Wi-Fi-Chipsatz abgeschaltet werden sollte. Der Test überprüft, dass Wi-Fi Energiesparmodus eingeben kann, die innerhalb der angegebenen Grenzwerte, die aktuelle Auslastung ist und es ist keine aktuelle gezeichnet wird, wenn Wi-Fi deaktiviert ist.

Der Treiber kann werden aktiviert aus dem Ruhezustand können Sie jederzeit mithilfe der **dot11\_Fertigung\_testen\_Normalzustand** Befehl. Wenn das Standbymodus Timeout auf −1 festgelegt ist, der Treiber sollte den Energiesparmodus versetzt wird auf unbestimmte Zeit, sofern Sie nicht aufgefordert werden, mithilfe von reaktivieren **dot11\_Fertigung\_testen\_Normalzustand**. Beim Reaktivieren des der Treiber entweder aufgrund der Timeout ablaufen oder als Ergebnis der Normalzustand Befehl angeben den Normalzustand Status mithilfe der **NDIS\_STATUS\_DOT11\_FERTIGUNG\_RÜCKRUF** Rückrufhandler mit der *dot11ManufacturingCallbackType* legen Sie auf **dot11\_Fertigung\_Rückruf\_dem Standbymodus\_vollständige**.

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_SLEEP {
    ULONG uSleepTime;
    PVOID pvContext;
} DOT11_MANUFACTURING_TEST_SLEEP, * PDOT11_MANUFACTURING_TEST_SLEEP;
```

<span id="uSleepTime"></span><span id="usleeptime"></span><span id="USLEEPTIME"></span>*uSleepTime*  
\[in\] die Zeitdauer in Millisekunden Ruhezustand des Treibers. Wenn der Treiber Ruhezustand bis mithilfe von aktiviert auf −1 festgelegt eingibt, die **dot11\_Fertigung\_testen\_Normalzustand** Befehl.

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[in\] Kontext verwendet, wenn der Treiber mithilfe der Test Abschlusszustand an die Anwendung zurückgibt **dot11\_Fertigung\_Rückruf\_dem Standbymodus\_vollständige**.

## <a name="span-iddot11manufacturingtestawakespanspan-iddot11manufacturingtestawakespandot11manufacturingtestawake"></a><span id="dot11_manufacturing_test_awake"></span><span id="DOT11_MANUFACTURING_TEST_AWAKE"></span>Dot11\_Fertigung\_testen\_Normalzustand


Die **dot11\_Fertigung\_testen\_Normalzustand** Befehl bewirkt, dass den Wi-Fi-Chipsatz zu startenden aus den niedrigsten Power-Zustand. Gibt der Treiber **STATUS\_UNGÜLTIGE\_PARAMETER** Wenn dieser Befehl gesendet wird, wenn der Chipsatz bereits länger aktiviert ist.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






