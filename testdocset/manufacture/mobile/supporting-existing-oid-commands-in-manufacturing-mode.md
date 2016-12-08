---
author: kpacquer
Description: "Unterstützung von vorhandenen OID Befehlen in Manufacturing Modus"
ms.assetid: 8b26ab8e-00b8-4f4c-a7c5-8fca4c5b1e3f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Unterstützung von vorhandenen OID Befehlen in Manufacturing Modus"
ms.openlocfilehash: 0faf01e3e7b1ecb551c043bf2fa569c3b4fac91d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-existing-oid-commands-in-manufacturing-mode"></a>Unterstützung von vorhandenen OID Befehle in Fertigung-Modus


Bei Ausführung im Modus Fertigung müssen Miniporttreiber Wi-Fi-Unterstützung für die folgenden vorhandenen OIDs hinzufügen.

## <a name="span-idoidgensupportedguidsspanspan-idoidgensupportedguidsspanoidgensupportedguids"></a><span id="OID_GEN_SUPPORTED_GUIDS"></span><span id="oid_gen_supported_guids"></span>OID\_GEN\_UNTERSTÜTZTE\_GUIDS


Die **OID\_GEN\_UNTERSTÜTZTE\_GUIDS** Befehl wird aufgerufen, im Abfragemodus, um den Satz der unterstützten GUIDS zurückzugeben. Eine ausführliche Dokumentation finden Sie unter [OID\_GEN\_UNTERSTÜTZTE\_GUIDS](http://msdn.microsoft.com/library/ff569641.aspx) auf MSDN.

**Hinweis**  
Diese OID wird normalerweise aus Gründen der Kompatibilität aufgerufen. Der Treiber kann, falls gewünscht ignoriert werden sollen, und zurückgeben **NDIS\_STATUS\_NICHT\_UNTERSTÜTZTE** stattdessen.

 

## <a name="span-idoidgenvendoridspanspan-idoidgenvendoridspanoidgenvendorid"></a><span id="OID_GEN_VENDOR_ID"></span><span id="oid_gen_vendor_id"></span>OID\_GEN\_HERSTELLER\_ID


Die **OID\_GEN\_HERSTELLER\_ID** Befehl wird aufgerufen, im Abfragemodus, um die 3-Byte-IEEE registriert Hersteller Rückgabecode gefolgt von einem einzelnen Byte vom Hersteller, die einer bestimmten Netzwerkkarte identifiziert zugewiesen Eine ausführliche Dokumentation finden Sie unter [OID\_GEN\_HERSTELLER\_ID](http://msdn.microsoft.com/library/ff569651.aspx) auf MSDN.

## <a name="span-idoidgenvendordescriptionspanspan-idoidgenvendordescriptionspanoidgenvendordescription"></a><span id="OID_GEN_VENDOR_DESCRIPTION"></span><span id="oid_gen_vendor_description"></span>OID\_GEN\_HERSTELLER\_BESCHREIBUNG


Die **OID\_GEN\_HERSTELLER\_BESCHREIBUNG** Befehl wird aufgerufen, im Abfragemodus eine mit NULL endende Zeichenfolge zurückgegeben, die die NIC im ANSI-Format beschreibt. Eine ausführliche Dokumentation finden Sie unter [OID\_GEN\_HERSTELLER\_BESCHREIBUNG](http://msdn.microsoft.com/library/ff569649.aspx) auf MSDN.

## <a name="span-idoidgencurrentlookaheadspanspan-idoidgencurrentlookaheadspanoidgencurrentlookahead"></a><span id="OID_GEN_CURRENT_LOOKAHEAD"></span><span id="oid_gen_current_lookahead"></span>OID\_GEN\_AKTUELLEN\_LOOKAHEAD


Die **OID\_GEN\_AKTUELLEN\_LOOKAHEAD** Befehl wird aufgerufen, in Set-Modus, um die Anzahl von Bytes der empfangenen Paketdaten an den Protokolltreiber gesendet werden sollen. Eine ausführliche Dokumentation finden Sie unter [OID\_GEN\_AKTUELLEN\_LOOKAHEAD](http://msdn.microsoft.com/library/ff569574.aspx) auf MSDN.

**Hinweis**  
Diese OID wird normalerweise aus Gründen der Kompatibilität aufgerufen. Der Treiber, falls gewünscht ignoriert werden sollen, und zurückgeben kann **NDIS\_STATUS\_NICHT\_UNTERSTÜTZTE** stattdessen.

 

## <a name="span-idoidpmaddwolpatternspanspan-idoidpmaddwolpatternspanoidpmaddwolpattern"></a><span id="OID_PM_ADD_WOL_PATTERN"></span><span id="oid_pm_add_wol_pattern"></span>OID\_PM\_HINZUFÜGEN\_WOL\_MUSTER


Die **OID\_PM\_HINZUFÜGEN\_WOL\_MUSTER** Befehl wird aufgerufen, in Set-Modus, um das Muster WOL angeben. Eine ausführliche Dokumentation finden Sie unter [OID\_PM\_HINZUFÜGEN\_WOL\_MUSTER](http://msdn.microsoft.com/library/ff569764.aspx) auf MSDN.

**Hinweis**  
Diese OID wird normalerweise aus Gründen der Kompatibilität aufgerufen werden. Der Treiber kann, falls gewünscht ignoriert werden sollen, und zurückgeben **NDIS\_STATUS\_NICHT\_UNTERSTÜTZTE** stattdessen.

 

## <a name="span-idoiddot11resetrequestspanspan-idoiddot11resetrequestspanoiddot11resetrequest"></a><span id="OID_DOT11_RESET_REQUEST"></span><span id="oid_dot11_reset_request"></span>OID\_DOT11\_ZURÜCKSETZEN\_ANFORDERN


Die **OID\_DOT11\_ZURÜCKSETZEN\_ANFORDERN** Befehl wird im Abfragemodus zurückzugebenden vom Treiber verwendete IEEE-MAC-Adresse bezeichnet. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_ZURÜCKSETZEN\_ANFORDERN](http://msdn.microsoft.com/library/ff569409.aspx) auf MSDN.

## <a name="span-idoiddot11currentaddressspanspan-idoiddot11currentaddressspanoiddot11currentaddress"></a><span id="OID_DOT11_CURRENT_ADDRESS"></span><span id="oid_dot11_current_address"></span>OID\_DOT11\_AKTUELLEN\_ADRESSE


Die **OID\_DOT11\_AKTUELLEN\_ADRESSE** Befehl wird aufgerufen, im Abfragemodus verwendete vom Treiber IEEE-MAC-Adresse zurückgegeben. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_AKTUELLEN\_ADRESSE](http://msdn.microsoft.com/library/ff569125.aspx) auf MSDN.

## <a name="span-idoiddot11supportedphytypesspanspan-idoiddot11supportedphytypesspanoiddot11supportedphytypes"></a><span id="OID_DOT11_SUPPORTED_PHY_TYPES"></span><span id="oid_dot11_supported_phy_types"></span>OID\_DOT11\_UNTERSTÜTZTE\_PHY\_TYPEN


Die **OID\_DOT11\_UNTERSTÜTZTE\_PHY\_TYPEN** Befehl wird aufgerufen, im Abfragemodus zum Anfordern der Liste der PHY-Typen, die von der 802.11 Station unterstützt. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_UNTERSTÜTZTE\_PHY\_TYPEN](http://msdn.microsoft.com/library/ff569426.aspx) auf MSDN.

## <a name="span-idoiddot11currentphyidspanspan-idoiddot11currentphyidspanoiddot11currentphyid"></a><span id="OID_DOT11_CURRENT_PHY_ID"></span><span id="oid_dot11_current_phy_id"></span>OID\_DOT11\_AKTUELLEN\_PHY\_ID


Die **OID\_DOT11\_AKTUELLEN\_PHY\_ID** Befehl heißt in Set-Modus festlegen die aktuelle PHY-ID. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_AKTUELLEN\_PHY\_ID](http://msdn.microsoft.com/library/ff569135.aspx) auf MSDN.

## <a name="span-idoiddot11hardwarephystatespanspan-idoiddot11hardwarephystatespanoiddot11hardwarephystate"></a><span id="OID_DOT11_HARDWARE_PHY_STATE"></span><span id="oid_dot11_hardware_phy_state"></span>OID\_DOT11\_HARDWARE\_PHY\_ZUSTAND


Die **OID\_DOT11\_HARDWARE\_PHY\_ZUSTAND** Befehl heißt im Abfragemodus, um die PHY Power Status zurückzugeben. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_HARDWARE\_PHY\_ZUSTAND](http://msdn.microsoft.com/library/ff569370.aspx) auf MSDN.

## <a name="span-idoiddot11nicpowerstatespanspan-idoiddot11nicpowerstatespanoiddot11nicpowerstate"></a><span id="OID_DOT11_NIC_POWER_STATE"></span><span id="oid_dot11_nic_power_state"></span>OID\_DOT11\_NIC\_POWER\_ZUSTAND


Die **OID\_DOT11\_NIC\_POWER\_ZUSTAND** Befehl heißt im Abfragemodus, um die NIC Power Status zurückzugeben. Eine ausführliche Dokumentation finden Sie unter [OID\_DOT11\_NIC\_POWER\_ZUSTAND](http://msdn.microsoft.com/library/ff569392.aspx) auf MSDN.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Wi-Fi manufacturing Unterstützung für Tests der OID-Schnittstelle](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






