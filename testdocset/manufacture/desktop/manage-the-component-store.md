---
author: Justinha
Description: Verwalten der Komponente Store
ms.assetid: 97e222b5-67cf-4d05-a010-de3e5518cb60
MSHAttr: PreferredLib:/library/windows/hardware
title: Verwalten der Komponente Store
ms.openlocfilehash: 1b4c2a490e49c1d19110c03da545fd14b99a294e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manage-the-component-store"></a>Verwalten der Komponente Store


"Warum WinSxS so groß ist?" hat von vielen Benutzern von Windows aufgefordert wurden. Während diese Frage wurde in Blogbeiträgen erläuterten in diesem Thema wechselt in den etwas Weitere Details über die Konzepte hinter der Komponente Store (insbesondere in den Ordner WinSxS) und anschließend Links zu Themen, in denen Hervorheben von Methoden, um die Größe des Ordners WinSxS besser zu verwalten.

Die Antwort ist, dass der Ordner WinSxS nicht so groß wie er auf den ersten Blick erscheint, da die Berechnung der Größe umfassen können, dass Windows-Binärdateien an anderer Stelle befindet sich wodurch Ordner WinSxS scheinbar größer als eigentlich ist.

## <a name="span-idthewindowscomponentstoreandwinsxsfolderspanspan-idthewindowscomponentstoreandwinsxsfolderspanspan-idthewindowscomponentstoreandwinsxsfolderspanthe-windows-component-store-and-winsxs-folder"></a><span id="The_Windows_component_store_and_WinSxS_folder"></span><span id="the_windows_component_store_and_winsxs_folder"></span><span id="THE_WINDOWS_COMPONENT_STORE_AND_WINSXS_FOLDER"></span>Den Windows-Komponentenspeicher und die Ordner WinSxS


Ordner WinSxS befindet sich im Windows-Ordner, beispielsweise **c:\\Windows\\WinSxS**. Es ist der Speicherort für die Windows-Komponente Store-Dateien. Die Komponente Windows Store wird verwendet, um die Funktionen für die Anpassung erforderlich ist, und Aktualisieren von Windows unterstützt. Es folgen einige Beispiele wie die Windows-Komponenten Store Dateien verwendet werden:

-   So installieren Sie neue Komponentenversionen mithilfe von Windows Update. Dadurch wird Systeme sicher und auf dem neuesten Stand.

-   Aktivieren oder Deaktivieren des Windows-Features.

-   Hinzufügen von Rollen oder Features mit dem Server-Manager.

-   Verschieben von Systemen zwischen verschiedenen Editionen von Windows.

-   Wiederherstellung von Fehlern Beschädigung oder boot

-   Deinstallieren von problematisch updates

-   Ausführen von Programmen, die Verwendung von Side-by-Side-Assemblys

Die Komponente Windows Store wurde erstmalig in Windows XP zur Unterstützung von nebeneinander Assemblys eingeführt. Beginnend in Windows Vista, wurde der Komponentenspeicher erweitert, um nachzuverfolgen und zu service alle Komponenten, die das Betriebssystem bilden. Diese unterschiedlichen Betriebssystemkomponenten nachverfolgen Objekte wie Dateien, Verzeichnisse, Registrierungsschlüssel und Diensten. Bestimmte Versionen von Komponenten werden in Pakete dann zusammengefasst. Pakete werden von Windows Update und DISM zum Aktualisieren von Windows verwendet. Komponenten und Pakete, die in einer Windows-Installation verwendet werden durch die Komponente Windows Store verarbeitet. Bestimmen der Größe der Windows Store-Komponente ist kompliziert, dass viele der Dateien aus Verzeichnissen außerhalb Windows Store-Komponente mithilfe der sogenannten *Festplatte verknüpfen*von Windows verwendet werden. In solchen Fällen werden die Dateien von einer Komponentenversion innerhalb und außerhalb der Komponente Windows Store angezeigt. Mithilfe von *schwerer verknüpfen* kann Windows angezeigt werden, um mehrere Kopien der gleichen Datei beizubehalten, ohne dass tatsächlich den hinzugefügten Speicherplatz für mehrere Kopien.

## <a name="span-idhardlinksspanspan-idhardlinksspanspan-idhardlinksspanhard-links"></a><span id="Hard_links"></span><span id="hard_links"></span><span id="HARD_LINKS"></span>Feste links


Eine feste Verbindung ist ein File System-Objekt dem zwei Dateien an den gleichen Speicherort auf dem Datenträger verweisen kann. Dies bedeutet, dass mehr als eine Datei auf dieselben Daten verweisen und Änderungen für diese Daten in einer Datei in den anderen Dateien übernommen werden. Dies erschwert die Konzepte der Größe des Verzeichnisses angezeigt, entsprechend dem folgenden Beispiel:

1.  Verzeichnis A hat drei Dateien: 1.txt, 2.txt und 3. Txt

2.  Verzeichnis B besteht aus einer Datei: 4. Txt

3.  Dateien 1. Txt 2.Klicken Txt schwer miteinander verknüpft und sind 1MB an Daten enthalten.

4.  Dateien 3. Txt 4. Txt auch schwer miteinander verknüpft und sind 2MB der Daten enthalten.

![feste Links-Beispiel](images/dep-adk-winb-dism-winsxs-hardlinks.jpg)

In diesem Beispiel finden Sie unter, feste Links mehrere Dateien zum Verweisen auf die gleiche Gruppe von Daten zu aktivieren.

Was ist nun der Größe des Directory ein?

Die Antwort hängt Sie Directory A: verwenden möchten

1.  Wenn Sie die Dateien aus dem Verzeichnis A gelesen wird die Größe aller Dateien, die gelesen werden die Summe der einzelnen Dateigröße. In diesem Beispiel wird die 4 MB sein.

2.  Wenn Sie alle Dateien aus dem Verzeichnis ein an einen neuen Speicherort kopieren, wird die Menge der Daten kopiert die Summe der Festplatte alle Daten aus den Dateien verknüpft. In diesem Beispiel wird die 3 MB sein.

3.  Wenn Sie versuchen, um Speicherplatz freizugeben, durch die ein Verzeichnis löschen, werden nur eine Reduzierung der Größe für die Dateien angezeigt, die harte verknüpft, nur von Directory A sind. In diesem Beispiel Beträge diese an eine Einsparung von 1 MB.

Back auf die Frage wie viel Speicherplatz wird von der Komponente Windows Store und insbesondere die Ordner WinSxS verwendet. Die dritte Antwort in das Verzeichnis eines Beispiels entspricht am ehesten wie viel zusätzlicher Speicherplatz verwendet wird. Festplatte für den Rest des Systems verknüpfte Dateien sind für Systemvorgänge erforderlich, sodass nicht gezählt sollten und Dateien Festplatten mit mehreren Speicherorten im Komponentenspeicher verknüpft sollte nur die Größe auf einem Datenträger gezählt werden.

## <a name="span-idmanagingthewindowscomponentstorespanspan-idmanagingthewindowscomponentstorespanspan-idmanagingthewindowscomponentstorespanmanaging-the-windows-component-store"></a><span id="Managing_the_Windows_Component_Store"></span><span id="managing_the_windows_component_store"></span><span id="MANAGING_THE_WINDOWS_COMPONENT_STORE"></span>Verwalten von Windows Store-Komponente


Neue Features in Windows 8.1 und Windows Server 2012 R2 können Sie um die Komponente Windows Store zu verwalten:

[Bestimmen Sie die tatsächliche Größe des Ordners WinSxS](determine-the-actual-size-of-the-winsxs-folder.md)

[Bereinigen des Ordners WinSxS](clean-up-the-winsxs-folder.md)

[Verringern Sie die Größe des Speichers Komponente in einem Offline-Windows-Bild](reduce-the-size-of-the-component-store-in-an-offline-windows-image.md)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Wo ist mein Space? (Blogbeitrag)](http://blogs.technet.com/b/askcore/archive/2013/03/01/where-did-my-space-go.aspx)

[Weitere auf feste links](http://blogs.technet.com/b/joscon/archive/2011/08/26/more-on-hard-links.aspx)

[NTFS-Metadateien Blogbeitrag](http://blogs.technet.com/b/askcore/archive/2009/12/30/ntfs-metafiles.aspx)

[Zeigt, wie Sie zum Erstellen und Bearbeiten von NTFS-Verknüpfung](http://support.microsoft.com/kb/205524)

 

 






