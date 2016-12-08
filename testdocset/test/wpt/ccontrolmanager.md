---
title: CControlManager
description: CControlManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1952f739-e610-4bc3-938f-8ffad3875aec
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d434adb9481268b5aa57e208c2f2de33914bf1b4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ccontrolmanager"></a>CControlManager


Stellt den-Manager, der eine Benutzerprofildienst-Auflistung ausgeführt wird. Die Klasse implementiert die [IControlManager](icontrolmanager.md), [IOnOffTransitionManager](ionofftransitionmanager.md), [IControlErrorInfo](icontrolerrorinfo.md)und [IEnumControlWarningInfo](ienumcontrolwarninginfo.md) Schnittstellen. Führen Sie Profile instanziiert der Client eine Instanz der Klasse. Die Bibliothek behält nur eine einzelne statische Instanz des Managers. Wenn der Client versucht, mehrere Male instanziieren, gibt die Bibliothek die ursprüngliche Instanz und erhöht den Referenzzähler.

## <a name="syntax"></a>Syntax


``` syntax
{
  [default] interface IControlManager;
  interface IOnOffTransitionManager;
  interface IControlErrorInfo;
  interface IEnumControlWarningInfo;
};
```

## <a name="related-topics"></a>Verwandte Themen


[Klassen](classes.md)

 

 







