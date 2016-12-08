---
title: WPR Schnellstart
description: Schneller Einstieg in WPR
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bb93222f-a938-45a9-8fd7-0a1eb254537c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 67c403094110d8cd858a7c36812600670662fc3d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpr-quick-start"></a>Schneller Einstieg in WPR


In diesem Artikel wird die Features, die in der Windows Performance Aufzeichnung (WPR)-Benutzeroberfläche (UI) zur Verfügung stehen.

**Hinweis**  
Sie können auch WPR über die Befehlszeile ausführen. Informationen zu dieser Option finden Sie unter [WPR Command-Line Options](http://go.microsoft.com/fwlink/p/?linkid=223233).

 

**Inhalt dieses Artikels:**

-   [Aufzeichnung mithilfe der WPR Standardeinstellungen](#default)

-   [Aufzeichnung Profile verwenden](#profiles)

-   [Verwenden die Leistung Szenarien](#perf)

-   [Mithilfe von Detailstufen](#detail)

-   [Verwenden der Protokollierungsmodus](#logmode)

## <a name="a-href-iddefaultarecording-by-using-the-wpr-default-settings"></a><a href="" id="default"></a>Mithilfe der Standardeinstellungen für WPR aufzeichnen


Klicken Sie auf **der Startseite** auf **Windows Performance Aufzeichnung** der WPR UI zu öffnen. Klicken Sie in WPR auf **Starten** , um die Systemleistung zu erfassen, indem Sie mit den Standardeinstellungen aus dem **allgemeinen** Profil.

Weitere Informationen zu diesem Feature finden Sie unter [Starten eine Aufzeichnung](http://go.microsoft.com/fwlink/?LinkId=249060) und [Aufzeichnung für die Diagnose für grundlegende System](http://go.microsoft.com/fwlink/?LinkId=249061).

## <a name="a-href-idprofilesausing-recording-profiles"></a><a href="" id="profiles"></a>Aufzeichnung Profile verwenden


WPR Aufzeichnung Profile enthalten alle Informationen, die erforderlich sind, um die Leistung für ein bestimmtes Szenario Aufzeichnung aktivieren. Sie können mehrere Profile in einer einzigen Aufzeichnung einschließen.

Allgemeine Informationen zu WPR-Profilen finden Sie unter [Aufzeichnung Profile](http://go.microsoft.com/fwlink/?LinkId=249062).

WPR bietet eine Vielzahl von integrierten Aufzeichnung Profile, die in Gruppen nach Funktion sortiert werden. Weitere Informationen zu integrierten WPR-Profilen finden Sie unter [integrierte Aufzeichnung](http://go.microsoft.com/fwlink/?LinkId=249063) und [Integrierten Profile auswählen](http://go.microsoft.com/fwlink/?LinkId=249064).

Sie können außerdem erstellen und Datensätze von Ereignissen benutzerdefinierten Profile (.wprp-Dateien) hinzugefügt. Weitere Informationen zu benutzerdefinierten Profilen finden Sie unter [Authoring Aufzeichnung Profile](http://go.microsoft.com/fwlink/p/?linkid=223238) und [Hinzufügen oder Entfernen eines benutzerdefinierten Profils Aufzeichnung](http://go.microsoft.com/fwlink/?LinkId=249068).

## <a name="a-href-idperfausing-performance-scenarios"></a><a href="" id="perf"></a>Verwenden die Leistung Szenarien


Leistung Szenarien können Sie häufige Szenarien wie ein-/ausschalten Übergänge oder Heap Analyse aufzeichnen. Sie können nur ein Szenario für eine Aufzeichnung auswählen. Weitere Informationen zur Leistung Szenarien finden Sie unter [WPR Szenarien](http://go.microsoft.com/fwlink/p/?linkid=223244) und [Ändern Sie das Szenario Leistung](http://go.microsoft.com/fwlink/?LinkId=249066).

## <a name="a-href-iddetailausing-detail-levels"></a><a href="" id="detail"></a>Mithilfe von Detailstufen


Sie können eine Detailebene für jede Aufzeichnung auswählen. Die verfügbaren Ebenen sind **hell** und **Verbose**. Die Detailebene **Licht** wird hauptsächlich für Timing-Aufzeichnungen. Die Detailstufe **Verbose** enthält detaillierte Informationen, die Sie für die Analyse benötigen. Weitere Informationen zu Detail Ebenen finden Sie unter [Detailstufe](http://go.microsoft.com/fwlink/?LinkId=249070) und [Ändern Sie die Detailebene](http://go.microsoft.com/fwlink/?LinkId=249069).

## <a name="a-href-idlogmodeaselecting-a-logging-mode"></a><a href="" id="logmode"></a>Auswahl eines Protokollierungsmodus


WPR kann Ereignisse protokolliert, in eine sequenzielle Datei oder in zirkulären Puffer im Arbeitsspeicher. Protokollierung in eine Datei wird für kurze Spuren verwendet, wenn Sie wissen, wann die Ereignisse, die Sie verfolgen möchten auf Sie zukommt. Arbeitsspeicher der Protokollierung wird für kontinuierliche Tracing verwendet, wenn Ereignisse protokolliert, die zu einem beliebigen Zeitpunkt auftreten können sollen. Allgemeine Szenarien können beide Arten von Protokollierung. Ein-/ausschalten Übergänge nur können Datei Protokollierung jedoch.

Weitere Informationen zur Protokollierung Modi finden Sie unter [Logging-Modus](http://go.microsoft.com/fwlink/?LinkId=249071) und [Ändern der Protokollierungsmodus](http://go.microsoft.com/fwlink/?LinkId=249072).

## <a name="related-topics"></a>Verwandte Themen


[Einführung in WPR](introduction-to-wpr.md)

[WPR-Features](http://go.microsoft.com/fwlink/p/?linkid=223236)

[WPR Vorgehensweisen](http://go.microsoft.com/fwlink/p/?linkid=223237)

[WPR (engl.)](http://go.microsoft.com/fwlink/p/?linkid=223245)

 

 







