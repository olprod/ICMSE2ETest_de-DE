---
author: Justinha
Description: "Bestimmen der tatsächlichen Größe des Ordners WinSxS"
ms.assetid: 059afbeb-3911-4e50-9ba5-ffd4fe6f38a4
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bestimmen der tatsächlichen Größe des Ordners WinSxS"
ms.openlocfilehash: e2990f62177a028034a9b5d1eb1d73f23107664f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="determine-the-actual-size-of-the-winsxs-folder"></a>Bestimmen der tatsächlichen Größe des Ordners WinSxS


Warum ist der Ordner WinSxS so groß? Die Antwort auf diese häufig gestellte Frage ist, dass der Komponente Store (Ordner WinSxS) alle Komponenten enthält, dass schließen ein Windows ermöglicht das System ausgeführt werden. Diese Komponenten werden zum Ausführen eines Rollbacks problematisch Änderungen gespeichert oder reparieren eine Datei, die beschädigt ist. Weitere Informationen zu den Komponentenspeicher finden Sie unter [Verwalten der Komponente Store](manage-the-component-store.md). Informationen zum Löschen von Dateien im Ordner WinSxS finden Sie unter [Clean Up the WinSxS Ordner](clean-up-the-winsxs-folder.md).

Für Dateien des Betriebssystems kann angezeigt werden, dass mehr als eine Kopie der gleichen Version einer Datei wird unter dem Betriebssystem mehr als zentral gespeichert, aber in der Regel nur eine echte Kopie der Datei vorhanden ist. Die übrigen Exemplare werden nur "projiziert" die harte Verknüpfung aus dem Komponentenspeicher. Eine *feste Verbindung* ist ein File System-Objekt, das zwei Dateien, die an den gleichen Speicherort auf dem Datenträger verweisen kann. Einige Tools, wie die Datei-Explorer, bestimmen Sie die Größe der Verzeichnisse ohne Berücksichtigung, dass die darin enthaltenen Dateien möglicherweise schwer verknüpft. Dies möglicherweise führen Sie glauben, dass der Ordner WinSxS mehr Speicherplatz belegt, als es tatsächlich ist.

**Warnung**  
Einige wichtige Systemdateien befinden sich nur im Ordner "WinSxS". Löschen von Dateien aus dem Ordner WinSxS oder löschen den gesamten Ordner WinSxS möglicherweise stark Ihr System beschädigt werden, damit Ihr PC möglicherweise nicht starten, und es nicht möglich machen, aktualisieren.

 

Eine neue Option wurde das Tool DISM für Windows 8.1 um festzustellen, wie viel Speicherplatz der WinSxS hinzugefügt really Ordner verwendet.

**Analysieren der Größe des Speichers Komponente (Ordner WinSxS)**

-   Öffnen Sie ein Befehlsfenster mit erhöhten Rechten und Typ:

    ``` syntax
    Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
    ```

    **Hinweis**  
    Die Option **/AnalyzeComponentStore** nicht unter Windows 8 und früher erkannt.

     

    Die zurückgegebenen Informationen sind:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Title</th>
    <th align="left">Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Windows-Explorer angezeigte Größe der Komponente Store</p></td>
    <td align="left"><p>Dies Wert die Größe des Ordners WinSxS, wenn von Windows Explorer berechnet. Dieser Wert nicht die Verwendung von festen Links innerhalb des Ordners WinSxS berücksichtigt werden.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Tatsächliche Größe der Komponente Store</p></td>
    <td align="left"><p>Feste Links innerhalb des Ordners WinSxS berücksichtigt diesen Wert. Es wird nicht Dateien aus, die mit Windows gemeinsam mithilfe von feste Links verwendet werden.</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Gemeinsam mit Windows</p></td>
    <td align="left"><p>Dieser Wert stellt bereit, die Größe der Dateien, die harte sind verknüpft, sodass sie sowohl im Komponentenspeicher und an anderen Standorten (für den normalen Betrieb von Windows) angezeigt werden. Dies ist in der tatsächlichen Größe enthalten, jedoch sollten nicht als Teil der Komponente Store Aufwand betrachtet werden.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Sicherungen und deaktivierten Funktionen</p></td>
    <td align="left"><p>Dies ist die Größe der Komponenten, die auf Fehler im neuere Komponenten reagieren oder die Option zum Aktivieren von mehr Funktionen bereitstellen aufbewahrt werden. Darüber hinaus die Größe der Komponente Store Metadaten und Side-by-Side-Komponenten.</p>
    <p>Dies ist in der tatsächlichen Größe enthalten und ist Teil der Komponente Store Aufwand.</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Cache und temporäre Daten</p></td>
    <td align="left"><p>Dies ist die Größe der Dateien, die intern von der Komponente Store um zu beschleunigen Wartungsvorgänge Komponente verwendet werden. Dies ist in der tatsächlichen Größe enthalten und ist Teil der Komponente Store Aufwand.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Datum der letzten Bereinigung</p></td>
    <td align="left"><p>Dies ist das Datum der zuletzt abgeschlossenen Komponente Store Bereinigung.</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>Anzahl der zurückforderbar Pakete</p></td>
    <td align="left"><p>Dies ist die Anzahl der ersetzte Pakete auf dem System dieser Komponente Cleanup entfernen kann.</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>Komponente Store Cleanup empfohlen</p></td>
    <td align="left"><p>Dies ist eine Komponente Store Cleanup Empfehlung. Bereinigung wird empfohlen, beim Ausführen eines Cleanup-Prozess die Größe der Komponente Store Aufwand verringern kann.</p></td>
    </tr>
    </tbody>
    </table>

     

    Basierend auf dieser Analyse des Verarbeitungsaufwands zum Ordner WinSxS können durch die Summe von Sicherungen bestimmen und Features mit dem Cache und temporäre Datengröße deaktiviert.

    Beispiel für die Ausgabe:

    ``` syntax
    C:\>dism /online /cleanup-image /analyzecomponentstore

    Deployment Image Servicing and Management tool
    Version: 6.3.XXXX.0

    Image Version: 6.3.XXXX.0

    [==========================100.0%==========================]

    Component Store (WinSxS) information:

    Windows Explorer Reported Size of Component Store : 4.98 GB

    Actual Size of Component Store : 4.88 GB

        Shared with Windows : 4.38 GB
        Backups and Disabled Features : 506.90 MB
        Cache and Temporary Data : 279.52 KB

    Date of Last Cleanup : 2013-06-10 23:32:22

    Number of Reclaimable Packages : 0
    Component Store Cleanup Recommended : No

    The operation completed successfully.
    ```

    In diesem Beispiel Ordner WinSxS scheint 4.98 GB sein, aber der tatsächliche Aufwand (die Summe der Größe von Sicherungen und deaktivierten Funktionen und die Größe des Cache und temporäre Daten) beträgt 786.42 MB.

**Bestimmen Sie, ob Sie die Komponente Store (Ordner WinSxS) basierend auf den Analyseergebnissen bereinigen sollten**

1.  Öffnen Sie ein Befehlsfenster mit erhöhten Rechten und Typ:

    ``` syntax
    Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
    ```

2.  Falls Cleanup empfohlen wird gehen Sie dann in der zugehörigen Thema [Clean Up the Ordner WinSxS](clean-up-the-winsxs-folder.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Verwalten der Komponente Store](manage-the-component-store.md)

[Bereinigen des Ordners WinSxS](clean-up-the-winsxs-folder.md)

[Wo ist mein Space? (Blogbeitrag)](http://blogs.technet.com/b/askcore/archive/2013/03/01/where-did-my-space-go.aspx)

[Warten Änderungen in Windows 8.1/Server 2012 R2](http://blogs.technet.com/b/joscon/archive/2013/07/29/servicing-changes-in-windows-8-1-server-2012r2.aspx)

[NTFS-Metadateien Blogbeitrag](http://blogs.technet.com/b/askcore/archive/2009/12/30/ntfs-metafiles.aspx)

[Zum Erstellen und Bearbeiten von NTFS-Verknüpfung verweist.](http://support.microsoft.com/kb/205524)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

 

 






