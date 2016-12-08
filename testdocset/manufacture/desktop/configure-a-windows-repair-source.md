---
author: Justinha
Description: Konfigurieren einer Windows-Reparatur-Quelle
ms.assetid: 00c879d8-5c56-4e96-9c44-df0c2fc4371d
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren einer Windows-Reparatur-Quelle
ms.openlocfilehash: 2a463563e4e38a03b3d34b86216846393422db19
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-a-windows-repair-source"></a>Konfigurieren einer Windows-Reparatur-Quelle


Gruppenrichtlinien können Sie eine Windows reparieren Bildquelle zur Verwendung in Ihrem Netzwerk angeben. Die Quelle reparieren kann zum Wiederherstellen von Windows-Features oder zum Reparieren eines beschädigten Windows-Abbilds verwendet werden.

Features bei Bedarf können Sie eine optionale Funktion aus einem Windows®-Abbild entfernen und dann wiederhergestellt werden weiter unten. Sie können optionale Features deaktivieren und Entfernen von Dateien, die diese Funktionen über ein Windows-Abbild mithilfe der Tools Deployment Image Servicing and Management (DISM) zugeordnet. Wenn Sie das **Argument/Entfernen** mit der Option **DISM/Disable-Feature** , das Manifesten-Dateien für das Feature oder die Serverrolle verwenden, werden in das Bild verwaltet. Allerdings werden alle anderen Dateien für das Feature entfernt. Dadurch können Sie auf Speichern, herunterzuladen und bereitzustellen, da kleinere Bilder heruntergeladen ohne verlieren Features. Wenn das Abbild bereitgestellt wurde, können Benutzer das Feature auf ihren Computern mithilfe von Features bei Bedarf zum Abrufen der erforderlichen Dateien aus der Quelle reparieren können Sie jederzeit aktivieren. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren von Windows Features mithilfe von DISM](enable-or-disable-windows-features-using-dism.md).

Automatische Beschädigung Reparatur enthält Dateien, um Windows zu reparieren, wenn das Betriebssystem beschädigt ist. Benutzer können auch verwenden eine angegebenen Reparatur-Quelle in Ihrem Netzwerk oder Windows Update die Quelldateien abrufen, die zum Aktivieren eines Features oder zum Reparieren eines Windows-Abbilds erforderlich sind. Weitere Informationen finden Sie unter [Reparieren einer Windows-Abbild](repair-a-windows-image.md).

In diesem Abschnitt:

-   [Wählen Sie eine Quelle reparieren](#bkmk-specify)

-   [Festlegen von Gruppenrichtlinien](#bkmk-setgpo)

-   [Verwalten einer Quelle reparieren](#bkmk-maintain)

## <a name="span-idbkmkspecifyspanspan-idbkmkspecifyspanspan-idbkmkspecifyspanchoose-a-repair-source"></a><span id="BKMK_Specify"></span><span id="bkmk_specify"></span><span id="BKMK_SPECIFY"></span>Wählen Sie eine Quelle reparieren


Windows Update können Sie die Dateien bereitstellen, die zum Wiederherstellen eines Windows-Features oder Reparieren einer beschädigten Betriebssystem erforderlich sind. Sie können auch Gruppenrichtlinien zum Sammeln der erforderlichen Dateien von einem Speicherort im Netzwerk konfigurieren. Mehrere Speicherorte für Datenquellen können in der Gruppenrichtlinie angegeben werden.

**Mit Windows Update wiederherstellen optionale Features und reparieren die Windows-Bilder**

1.  Windows Update wird standardmäßig verwendet werden, wenn er durch die Richtlinieneinstellungen auf dem Computer zulässig ist.

2.  Wenn Sie Windows Update als primäre oder backup für Dateien, die Wiederherstellung optionale Features oder Reparatur von Windows-Abbilder verwendet werden, verwenden möchten, sollten Sie sicherstellen, dass die Firewall für die Gewährung des Zugriffs auf Windows Update konfiguriert ist.

**Mit einem Speicherort im Netzwerk wiederherstellen optionale Features und reparieren die Windows-Bilder**

1.  Sie können ein bereitgestelltes Windows-Abbild aus einer WIM-Datei als Quelle verwenden, Wiederherstellen optionale Features und Reparieren einer beschädigten Betriebssystem. Beispielsweise c:\\testen\\binden\\Windows. Weitere Informationen zum Erfassen einer Windows-Abbild als WIM-Datei finden Sie unter [Capture Bilder der Festplatte Partitionen mithilfe von DISM](capture-images-of-hard-disk-partitions-using-dism.md).

2.  Sie können eine ausgeführte Windows-Installation als Quelle optionale Features wiederherstellen durch Freigabe c:\\Windows-Ordner in Ihrem Netzwerk.

3.  Sie können einen Windows-Side-by-Side-Ordner von einer Netzwerkfreigabe oder aus einem Wechselmedium, wie der Windows-DVD als Quelle für die Dateien verwenden. Beispielsweise z:\\Quellen\\SxS.

4.  Eine Windows WIM-Datei auf einer Netzwerkfreigabe können als Quelle Sie optionale Features wiederherstellen. Geben Sie den Index des Windows-Abbilds in der WIM-Datei, die Sie verwenden möchten, und Sie verwenden, müssen ein `Wim:` Präfix im Pfad zu diesem Dateiformat zu identifizieren. Geben Sie in eine Datei namens contoso.wim Index 3 angeben möchten, zum Beispiel: Wim:\\\\Netzwerks\\Bilder\\contoso.wim:3.

## <a name="span-idbkmksetgpospanspan-idbkmksetgpospanspan-idbkmksetgpospanset-group-policy"></a><span id="BKMK_SetGPO"></span><span id="bkmk_setgpo"></span><span id="BKMK_SETGPO"></span>Festlegen von Gruppenrichtlinien


Gruppenrichtlinien können Sie angeben, wann Windows Update oder einem Speicherort im Netzwerk als Quelle reparieren für Features bei Bedarf und automatischer Beschädigung Reparatur verwendet werden sollen.

**So konfigurieren Sie Gruppenrichtlinien für Feature bei Bedarf**

1.  Öffnen Sie den Gruppenrichtlinien-Editor. Beispielsweise auf einen Computer mit Windows-10 aus dem Bildschirm **Start** , geben Sie **Gruppenrichtlinien bearbeiten**, und wählen Sie dann auf **Bearbeiten von Gruppenrichtlinien** , um die Gruppenrichtlinien-Editor zu öffnen.

2.  Klicken Sie auf **Computerkonfiguration**, klicken Sie auf **Administrative Vorlagen**, klicken Sie auf **System**, und doppelklicken Sie dann auf die Einstellung **Einstellungen für optionale Komponenteninstallation und Komponente reparieren angeben** .

3.  Wählen Sie die Einstellungen, die Sie für Features bei Bedarf verwenden möchten.

## <a name="span-idbkmkmaintainspanspan-idbkmkmaintainspanspan-idbkmkmaintainspanmaintaining-a-repair-source"></a><span id="BKMK_Maintain"></span><span id="bkmk_maintain"></span><span id="BKMK_MAINTAIN"></span>Verwalten von einer Quelle reparieren


Wenn Sie Windows Update nicht verwenden als Quelle reparieren für Features bei Bedarf und automatischer Beschädigung reparieren, sollten Sie die folgenden Richtlinien für die Verwaltung einer Quelle reparieren.

### <a name="span-idservicingupdatesspanspan-idservicingupdatesspanspan-idservicingupdatesspanservicing-updates"></a><span id="Servicing_updates"></span><span id="servicing_updates"></span><span id="SERVICING_UPDATES"></span>Wartung von updates

Einer beliebigen Quelle reparieren sollten mit den neuesten Dienstupdates aktuellen beibehalten. Wenn Sie ein Bild aus einer WIM-Datei für Features bei Bedarf verwenden, können Sie das Tool DISM auf das Bild-service verwenden. Weitere Informationen finden Sie unter [Mount und eine DISM mithilfe eines Windows Bild ändern](mount-and-modify-a-windows-image-using-dism.md). Wenn Sie eine online Windows-Installation auf Ihrem lokalen Netzwerk als Bild Reparatur shared verwenden, sollten Sie sicherstellen, dass der Computer Zugriff auf Windows Update hat.

### <a name="span-idmultilingualimagesspanspan-idmultilingualimagesspanspan-idmultilingualimagesspanmultilingual-images"></a><span id="Multilingual_images"></span><span id="multilingual_images"></span><span id="MULTILINGUAL_IMAGES"></span>Mehrsprachige Abbilder

Sie müssen alle relevanten Language Packs bei Ihrer Reparatur Quelldateien für die Gebietsschemas enthalten, die das Bild unterstützt. Die Installation schlägt fehl, wenn Sie versuchen, ein Feature, ohne alle Komponenten Lokalisierung wiederherzustellen, die für dieses Feature die Windows-Installation erforderlich sind.

Sie können zusätzliche Language Packs installieren, nachdem ein Feature wiederhergestellt wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[Aktivieren Sie oder deaktivieren Sie des Windows-Features mithilfe von DISM](enable-or-disable-windows-features-using-dism.md)

[Reparieren eines Windows-Abbilds](repair-a-windows-image.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

 

 






