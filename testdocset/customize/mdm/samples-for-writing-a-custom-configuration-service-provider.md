---
title: "Beispiele für das Schreiben eines benutzerdefinierten Konfiguration-Dienstanbieters"
description: "Beispiele für das Schreiben eines benutzerdefinierten Konfiguration-Dienstanbieters"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ccda4d62-7ce1-483b-912f-25d50c974270
ms.openlocfilehash: 6b7b0cd2eed047ece5e7312aa0e2e354308495cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="samples-for-writing-a-custom-configuration-service-provider"></a>Beispiele für das Schreiben eines benutzerdefinierten Konfiguration-Dienstanbieters

Im folgenden Beispiel wird veranschaulicht, wie für eine duale SIM Phone Chip Karte Bezeichner (ICCID) und International Mobile Abonnenten Identität (IMSI) abgerufen.

## <a name="retrieving-iccid-and-imsi-for-a-dual-sim-phone"></a>Abrufen von ICCID und IMSI für eine duale SIM phone

Im folgende Beispiel wird die Implementierung der [IConfigServiceProvider2::ConfigManagerNotification](iconfigserviceprovider2configmanagernotification.md) -Methode verwendet. Es zunächst das IConfigSession2-Objekt abgerufen und fragt dann der ICCID mit der IConfigSession2::GetSessionVariable-Methode. Ersetzen Sie zum Abrufen der IMSI L "ICCID" mit L "IMSI".

``` syntax
case CFGMGR_NOTIFICATION_SETSESSIONOBJ:
    if (NULL != lpParam)
    {
        m_pSession = reinterpret_cast<IConfigSession2*>(lpParam);
        m_pSession->AddRef();
    }

    bstrContext = SysAllocString(L"ICCID");
    if (NULL == bstrContext)
    {
    hr = E_OUTOFMEMORY;
    goto Error;
    }

    hr = m_pSession->GetSessionVariable(bstrContext, &varValue);
    if (FAILED(hr))
    {
        goto Error;
    }
    break;
```

 





