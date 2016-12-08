---
title: CTraceMergeProperties
description: CTraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d7991df7-574a-4b48-9e2c-a76bb5da1cd3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5a4bd87e49dcd19aa08efc7e7ae108c57717210c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ctracemergeproperties"></a>CTraceMergeProperties


Stellt die Richtlinien, die angewendet werden, wenn die Bibliothek die Ereignis-ablaufverfolgungsprotokolldateien (ETL) für Event Tracing for Windows (ETW) Sitzungen zusammenführt, das zuvor mit die Profile gestartet wurden. Die [ITraceMergeProperties](itracemergeproperties.md) und die [IParsingErrorInfo](iparsingerrorinfo.md) -Schnittstellen implementiert. Der Client instanziiert eine neue Instanz für alle Seriendruck-Eigenschaften, die für die Zusammenführung der ETL-Dateien anwenden muss. Wenn der Client die Eigenschaften des XML-Seriendruck geladen wird, überprüft die Instanz für das Schema. Wenn die Überprüfung fehlschlägt, wird die Instanz speichert die Fehlerinformationen und gibt einen Fehlercode zurück. Im Falle eines Fehlers der Client erhält einen Schnittstellenzeiger zum **IParsingErrorInfo** und ruft die Fehlerinformationen ab.

## <a name="syntax"></a>Syntax


``` syntax
{
  [default] interface ITraceMergeProperties;
  interface IParsingErrorInfo;
};
```

## <a name="related-topics"></a>Verwandte Themen


[Klassen](classes.md)

 

 







