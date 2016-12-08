---
title: Erstellen eines benutzerdefinierten Aufzeichnung-Profils
description: Erstellen eines benutzerdefinierten Aufzeichnung-Profils
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4f33a662-0883-48b2-aa50-eb2dffc244d9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c0c11cbdeccc7b438355c7797d3b6afe8721dcaa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="author-a-custom-recording-profile"></a>Erstellen eines benutzerdefinierten Aufzeichnung-Profils


Dieses Verfahren beschreibt, wie ein benutzerdefinierter Aufzeichnung Profil in Windows Performance Aufzeichnung (WPR) zu erstellen. Sie können benutzerdefinierte Profile in eine XML-Datei erstellen, die die Erweiterung .wprp hat. sind die verfügbaren finden Sie unter [Aufzeichnung Profil XML-Referenz](recording-profile-xml-reference.md) für die vollständige Referenz und Schema Informationen. verfügbaren finden Sie unter [Authoring Aufzeichnung Profile](authoring-recording-profiles.md) Ausführlichere Informationen zum Erstellen der Aufzeichnung Profile sind.

**So erstellen Sie eine benutzerdefinierte Aufzeichnung Profil**

1.  Erstellen Sie eine neue XML-Datei in einem XML-Editor.

2.  Geben Sie Collector Definitionen. Weitere Informationen finden Sie unter [1. Collector Definitionen](1-collector-definitions.md).

3.  Geben Sie die System- und Ereignis Anbieter Definitionen. Weitere Informationen finden Sie unter [2. System- und Ereignis Anbieter Definitionen](2-system-and-event-provider-definitions.md).

4.  Geben Sie ein Profildefinitionen. Weitere Informationen finden Sie unter [3. Definitionen Profile](3-profile-definitions.md).

    **Hinweis**  
    Wenn das benutzerdefinierte Profil zu beenden, und führen Sie wieder, wenn einige Anbieter nicht gestartet werden soll, legen Sie das **Strict** -Attribut auf "True". Weitere Informationen zu dieser Option finden Sie unter [Strict Anbieter](strict-providers.md).

     

5.  Speichern Sie die Datei mit der Erweiterung .wprp.

Sie können definieren, abgeleitete Kollektoren, Anbieter und Profile, die von einer Basisversion erben, die Sie zuvor in der gleichen Datei oder in einer anderen Datei definieren. Weitere Informationen zu dieser Option finden Sie unter [Vererbung](inheritance.md).

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien WPR](windows-performance-recorder-common-scenarios.md)

 

 







