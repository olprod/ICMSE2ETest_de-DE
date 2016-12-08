---
title: Abfragen von Anbietern
description: Abfragen von Anbietern
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: abe58e3b-4050-4d42-ad71-a0c702492f8d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 37b1a0b475fe745ecbf08e6963db2d5c0ad80777
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="querying-providers"></a>Abfragen von Anbietern


Zeigt Trace und Anbieter Abfragen Optionen.

``` syntax
xperf {-providers [options] | -loggers | -boottrace | -profint | -profiles | -profileswithdetails | -profilesessions | -profileproviders | -profileloggers}
```

## <a name="parameters"></a>Parameter


<a href="" id="-providers-options----"></a>**-Anbietern***\[Optionen...\]*  
Fragen Sie alle bekannten/installiert und registriert Anbieter als sowie alle bekannten Kernel Flags und Gruppen ab. Weitere Informationen hierzu finden Sie unter [Anbieter](providers-wpa.md).

<a href="" id="-loggers"></a>**-Protokollierungsmodule**  
Alle aktiven protokollierungssitzungen Abfragen.

<a href="" id="-boottrace"></a>**Boottrace-**  
Abfragen der Startkonfiguration Trace an.

<a href="" id="-profint"></a>**Profint-**  
Fragen Sie im aktuellen Profil Intervall ab.

<a href="" id="-profiles-profilefilename---profilename-"></a>**-Profile** *{ProfileFileName | Profilname}*  
Fragen Sie in *ProfileFileName* oder *Profilname*definierten Profilnamen ab. Wenn keine Parameter angegeben werden, eine Abfrage die Namen der integrierten Profile.

<a href="" id="-profileswithdetails-profilefilename---profilename-"></a>**-profileswithdetails** *{ProfileFileName | Profilname}*  
Abfrage des Profils den Namen in definierten *ProfileFileName* oder detaillierte Eigenschaften im *Profilname*. Wenn keine Parameter angegeben werden, eine Abfrage die Namen der integrierten Profile.

<a href="" id="-profilesessions-profilefilename---sessionname-"></a>**-profilesessions** *{ProfileFileName | Sitzungsname}*  
Fragen Sie ab, die in *ProfileFileName* oder *Sitzungsname*definierten Namen der Benutzerprofildienst-Sitzung. Wenn keine Parameter angegeben werden, Fragen Sie ab, die Namen der integrierten Profil Sitzungen.

<a href="" id="-profileproviders-profilefilename---providername-"></a>**-profileproviders** *{ProfileFileName | ProviderName}*  
Fragen Sie in *ProfileFileName* oder *ProviderName*definierten Namen der Profile an ab. Wenn keine Parameter angegeben werden, Fragen Sie ab, die Namen der integrierten Profilanbieter.

<a href="" id="-profileloggersprofilename"></a>**-profileloggers** *Profilname*  
Abfrageprotokollierung Sitzungen in *Profilname*angegeben.

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







