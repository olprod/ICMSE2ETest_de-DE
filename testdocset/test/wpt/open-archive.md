---
title: "Öffnen Sie ein Archiv in WPA"
description: "Wie Spuren in einer Archivdatei öffnen, zusammengeführt werden und die zusammengeführten Spuren komprimieren."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0f9ebec0c9859f60cf16447527ab41bd1ae7ba9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="open-an-archive-in-wpa"></a>Öffnen Sie ein Archiv in WPA

WPA kann öffnen ETL-Dateien, die in der ZIP-Dateien enthalten sind und CAB-Dateien, zwei gängige Archivformate. Ein Dialogfeld in WPA **Laden von Zip/Cab**, ermöglicht durchsuchen Dateien in einem Archiv und Konfigurieren von Optionen für die Extrahierung von ETL-Dateien aus dem Archiv.

In diesem Thema:
- [Öffnen ein Archiv in WPA](#opening)
- [Elemente und **Laden von Zip/Cab** -Optionen](#options)
- [Zusammenführen von ablaufverfolgungen im WPA](#merging)

## <a name="a-href-idopeningaopening-an-archive"></a><a href="" id="opening"></a>Öffnen ein Archiv

Sie können mithilfe von **Load aus Zip/Cab** öffnen **Datei&nbsp;>&nbsp;öffnen** nach einer Datei, wie bei jeder anderen Datei suchen, die WPA öffnen können. Wenn Sie eine Zip oder Cab-Datei auswählen, wird WPA automatisch **Laden von Zip/CAB-Datei**geöffnet. 

Bei Verwendung der im Menü rich **Datei&nbsp;>&nbsp;Open** ermöglicht es Ihnen, rufen direkt **Laden von Zip/CAB-Datei** durch Klicken auf **Öffnen** unter **Archiv öffnen** Wenn **Navigieren** ausgewählt wird.

![Archiv-Befehl im Menü rich in WPA öffnen.](images/wpa-rich-menu-open-archive.png)


## <a name="a-href-idoptionsaelements-and-options-in-load-from-zipcab"></a><a href="" id="options"></a>Elemente und **Laden von Zip/Cab** -Optionen

Die folgende Abbildung zeigt das Dialogfeld **Laden von Zip/Cab** .

![Das Dialogfeld Archiv öffnen in WPA.](images/open-archive.png)

In der folgenden Tabelle werden die Elemente und **Laden von Zip/Cab** -Optionen beschrieben.

| Dialogfeld-element | Beschreibung |
|---|---|
| **Archiv&nbsp;Datei** | Der Pfad und Dateiname der Name der Archivdatei. |
| **Wählen Sie&nbsp;Ablaufverfolgungen** | Eine Liste der Dateien in den ausgewählten Archivdatei, einschließlich geschachtelter Verzeichnisse. |
| **Extrahieren Sie&nbsp;um** | Der Pfad zu der Sie die ETL-Dateien zu extrahieren möchten. Angeben eines Speicherorts ist optional. Wenn Sie keinen Pfad angeben, werden die ETL-Dateien in einen temporären Ordner extrahiert und gelöscht, nachdem Sie WPA schließen. |
| **Zusammenführen von&nbsp;ausgewählte&nbsp;Dateien&nbsp;um** | Geben Sie einen Pfad und Namen WPA die extrahierten ETL-Dateien in einer einzigen ETL-Datei zusammengeführt werden. Dies ist gleichbedeutend mit **Xperf**&nbsp;**-Merge**. |
| **Komprimieren&nbsp;zusammengeführt&nbsp;Trace** | Wählen Sie diese Option WPA Komprimieren der zusammengeführte Datei haben. Dies ist gleichbedeutend mit dem **-Komprimieren** Option mit **Xperf**verwendet&nbsp;**-Merge**. |
| **Open&nbsp;Ablaufverfolgungen&nbsp;in&nbsp;einzelne&nbsp;Sitzung** | Wählen Sie diese Option, um mehrere Spuren zusammen zu analysieren, ohne in eine neue Verfolgung zusammenführen. Diese Option ist andernfalls die gleichen Einschränkungen wie zusammenführen. |

## <a name="a-href-idmergingamerging-traces-in-wpa"></a><a href="" id="merging"></a>Zusammenführen von ablaufverfolgungen im WPA

Wenn Sie ETL-Dateien aus dem Archiv extrahieren, Sie können auch WPA **Xperf**entspricht einer einzelnen Trace, die Spuren zusammengeführt haben&nbsp;**-Merge**. Wenn Sie nicht die Spuren Zusammenführen auswählen, werden alle Spuren in das Archiv ausgewählten geöffnet, aber WPA berücksichtigt werden separate Spuren aus. 

Wie bei Xperf, sind das Zusammenführen von Spuren Einschränkungen. Im Allgemeinen muss auf dem gleichen Computer und erfasst werden, während die gleichen Zeit, ohne neu zu starten.

