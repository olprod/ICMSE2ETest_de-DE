---
title: Exporter (engl.)
description: Exporter (engl.)
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3b6b8ff1-b1c6-4117-a44a-010629b6b981
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a75dc624a3c325e11d157cb57aeb7e338d198007
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exporter"></a>Exporter (engl.)


Die WPA Exporter (engl.) ist ein Befehlszeilentool, das WPA-Funktionen für automatisierte Analyse Szenarien bereitstellt. Durch die Batchverarbeitung von Befehlen WPA Exporter (engl.) zusammen, können Sie Trace-Analyse für viel größerem Umfang als über die Benutzeroberfläche ausführen.

Das WPA Exporter (engl.) können Sie Tabellen aus einer einzelnen Trace und Profil gefiltert optional an einem bestimmten zeitlichen in einer (durch Trennzeichen getrennte Werte) CSV-Datei exportieren. Diese Zeiträume können durch eine der folgenden definiert werden:

-   Numerische Zeitstempelwerte

-   Benannte Markierungen

-   [Interessante Bereiche](regions-of-interest.md)

Wenn Sie keinen Zeitraum angeben, werden die Daten aus der gesamte Trace Dauer exportiert.

Tabellen können nicht aktuell von [Marktanteilen Analyseansichten](comparative-analysis-views.md)exportiert werden.

## <a name="syntax"></a>Syntax


Um die WPA Exporter (engl.) verwenden, müssen Sie eine vorhandene Ablaufverfolgungsdatei zusammen mit einem Profil angeben.

`wpaexporter.exe [-i] traceFile.etl -profile profile.wpaProfile [-delimiter <char>] [-prefix <prefix>] [-outputfolder <folder>] [-range <start> <end>] [-marks <M1> <M2>] [-regionsxml <manifest> ...] [-region <region_name>] [-symbols] [-tti] [-h | /?]`

## <a name="parameters"></a>Parameter


<a href="" id="--i--tracefile-etl"></a>*\[i -\] traceFile.etl*  
Eine Trace-Datei, die zu exportierenden Daten enthält. Die `–i` Flag ist optional.

<a href="" id="-profile"></a>*-Profil*  
Ein WPA-Profil (.wpaProfile) mit den Tabellen zu exportieren.

<a href="" id="-delimiter"></a>*-Trennzeichen*  
(Optional) Das Zeichen, das als Trennzeichen zwischen Werten in den CSV verwenden. Der Standardtrennlinie handelt es sich um ein Komma.

<a href="" id="-prefix"></a>*-Präfix*  
(Optional) Eine Zeichenfolge, die Ausgabedateinamen voran.

<a href="" id="-outputfolder"></a>*-outputfolder*  
(Optional) Der Ordner, in dem in den Tabellen exportiert werden sollen.

<a href="" id="-range"></a>*-Bereichs*  
(Optional) Die Zeit Zeitspanne aus &lt;starten&gt; auf &lt;End&gt;, exportiert werden sollen. Die Standardeinstellung ist Nanosekunden, jedoch können Sie auch angeben, Sekunden (s), Millisekunden (ms) oder Mikrosekunden (USA).

**Beispiele:**`1s`, `100ms`,`500us`

<a href="" id="-marks"></a>*-Verwenden*  
(Optional) Der Bereich exportiert werden sollen, wie durch zwei benannte Markierungen angegeben.

<a href="" id="-regionsxml"></a>*-regionsxml*  
(Optional) Eine oder mehrere manifest Dateien, die interessante Bereiche enthalten, sind. Sie können dieses Flag ohne Angeben der `–region` Flag für die gesamte Tabelle **Regionen interessante** exportieren.

**Beispiel:**`-regionsxml regionsxml1.xml regionsxml2.xml`

<a href="" id="-region"></a>*-Region*  
(Optional) Der Name einer bestimmten Region in der Verfolgung. Verwenden Sie dieses Flag zum Exportieren von Daten nur für die Dauer des Bereichs. Wenn Sie dieses Flag verwenden, müssen Sie auch mindestens einer Regionen der Manifestdatei Zinsen angeben.

<a href="" id="-symbols"></a>*-Symbole*  
(Optional) Enthalten Sie dieses Kennzeichen, um das Laden des Symbols aktivieren.

<a href="" id="-tti"></a>*-tti*  
(Optional) Verarbeiten Sie Trace auch bei Zeit Inversions.

## <a name="remarks"></a>Hinweise


Die Ausgabedateinamen werden automatisch generiert basierend auf der Tabelle und die vordefinierten Namen. Der Benutzer kann optional ein Präfix angeben (`-prefix`) und dem Verzeichnis (`-outputfolder`).

## <a name="related-topics"></a>Verwandte Themen


[WPA-Features](wpa-features.md)

[Profile anzeigen](view-profiles.md)

 

 







