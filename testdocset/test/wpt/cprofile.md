---
title: CProfile
description: CProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 046b4559-0408-4766-8bb5-d50a695138b9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b275d536918f15bfdadb4e380744a9a096f5dbc2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cprofile"></a>CProfile


Stellt ein **Profile** -Objekt, und enthält Daten zur Event Tracing for Windows (ETW) Sitzungen und Anbietern zu konfigurieren. Diese Klasse implementiert die [IProfile](iprofile.md) und [IParsingErrorInfo](iparsingerrorinfo.md) Schnittstellen. Der Client instanziiert eine neue Instanz für alle Profile, die ausgeführt werden muss. Wenn das Profil des Clients geladen wird, überprüft die Instanz für das Schema. Wenn die Überprüfung fehlschlägt, wird die Instanz speichert die Fehlerinformationen und gibt einen Fehlercode aus. Im Falle eines Fehlers der Client empfängt einen Schnittstellenzeiger auf **IParsingErrorInfo** und ruft die Fehlerinformationen ab.

## <a name="syntax"></a>Syntax


``` syntax
{
  [default] interface IProfile;
  interface IParsingErrorInfo;
};
```

## <a name="related-topics"></a>Verwandte Themen


[Klassen](classes.md)

 

 







