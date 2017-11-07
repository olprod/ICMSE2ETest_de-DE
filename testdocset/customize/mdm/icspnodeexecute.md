---
title: "ICSPNode ausführen"
description: "ICSPNode ausführen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5916e7b7-256d-49fd-82b6-db0547a215ec
ms.openlocfilehash: d8a21a2cc6ac824a6d1cb0c714b8cb40320fb507
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeexecute"></a>ICSPNode::Execute

Diese Methode führt eine Aufgabe auf einer intern ungeachtet Konfiguration Service Provider Knoten durch übergeben in den angegebenen Benutzerdaten und ein Ergebnis zurückgibt. Die genaue Bedeutung des **Ausführen** und ob es auch unterstützt wird, hängt von den Zweck des Knotens ab. Beispielsweise sollte **Execute** aufgerufen wird, auf einen Knoten, der eine Datei darstellt wahrscheinlich **ShellExecute** die Datei während der Aufruf **Execute** auf einen Registrierungsknoten im Allgemeinen nicht sinnvoll.

## <a name="syntax"></a>Syntax

``` syntax
HRESULT Execute([in] VARIANT varUserData);
```

## <a name="parameters"></a>Parameter

<a href="" id="varuserdata"></a>*varUserData*  
&nbsp;&nbsp;&nbsp;&nbsp;Daten in die Ausführung übergeben.

## <a name="return-value"></a>Rückgabewert

Der Wert S\_OK gibt an, dass der Vorgang für den Knoten erfolgreich ausgeführt wurde. E\_NOTIMPL zurückgegeben werden soll, wenn diese Methode nicht implementiert ist.

## <a name="remarks"></a>Hinweise

Diese Methode unterstützt extern – ungeachtet Knoten nicht.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** None

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 




