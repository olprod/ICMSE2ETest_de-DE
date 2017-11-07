---
author: kpacquer
Description: 'Windows PE: Identifizieren Sie Laufwerkbuchstaben mit einem Skript'
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Identifizieren Sie Laufwerkbuchstaben mit einem Skript'
ms.openlocfilehash: 83a508c8406ce390e5452190a6120a9dbd76c999
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-identify-drive-letters-with-a-script"></a>Windows PE: Identifizieren Sie Laufwerkbuchstaben mit einem Skript

Zuweisung von Windows PE Laufwerkbuchstaben ändern jedes Mal gestartet wird, und ändern können, je nachdem, welche Hardware erkannt wird. 

Ein Skript können um zu ermitteln, die welche Laufwerkbuchstaben also durch Suchen nach einer Datei oder eines Ordners.

Dieses Beispielskript sucht nach ein Laufwerk, einen Ordner namens Bilder verwendet, und weist diese eine Systemvariable: IMAGESDRIVE %. 

``` syntax
@echo Find a drive that has a folder titled Images.
@for %%a in (C D E F G H I J K L M N O P Q R S T U V W X Y Z) do @if exist %%a:\Images\ set IMAGESDRIVE=%%a
@echo The Images folder is on drive: %IMAGESDRIVE%
@dir %IMAGESDRIVE%:\Images /w
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>Verwandte Themen

[Windows PE für Windows 10](winpe-intro.md)

[Wpeinit und Startnet.cmd: Verwenden von Skripts zum Starten des Windows PE](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md) 

[Windows PE: Installieren auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md) 