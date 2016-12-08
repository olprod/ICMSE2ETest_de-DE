---
author: Justinha
Description: "Drucktaste zurücksetzen häufig gestellte Fragen (FAQ)"
ms.assetid: 80a313e3-6c2e-4768-9fec-78dd2876f024
MSHAttr: PreferredLib:/library/windows/hardware
title: "Drucktaste zurücksetzen häufig gestellte Fragen (FAQ)"
ms.openlocfilehash: abfe8a173bf415aa1648048652767e0d3e96008b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="push-button-reset-frequently-asked-questions-faq"></a>Drucktaste zurücksetzen häufig gestellte Fragen (FAQ)


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Frage</th>
<th align="left">Antwort</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Ist erforderlich für einen Benutzer Fenster RE Drucktaste zurücksetzen Features ausführen?</td>
<td align="left">Ja. Um ein Feature Drucktaste zurücksetzen ausgeführt werden soll, müssen Sie Windows RE-Boot-Abbild (Winre.wim) zur Verfügung stellen, auf der lokalen Festplatte und registrieren den Speicherort mithilfe des Tools Reagentc. Sie können die Standardeinstellung Winre.wim (verfügbar unter C:\Windows\System32\Recovery) oder ein benutzerdefiniertes Winre.wim Bild verwenden. Wenn Windows RE auf der lokalen Festplatte nicht aktiviert ist, müssen Benutzer Windows RE von Medien Drucktaste zurücksetzen Features Zugriff auf starten.</td>
</tr>
<tr class="even">
<td align="left">Was ist Compact OS?</td>
<td align="left">Compact OS ist eine Auflistung von Features, die zulassen Windows 10 mit Speicherkapazität so niedrig wie 16 GB auf PCs bereitgestellt werden. Die zwei primären Technologien umfassen:
<ul>
<li>Komprimierung der Common Language Runtime-Systemdateien</li>
<li>Single instancing von installierten Anpassungen mit dem Anpassungen Paket von Drucktaste zurücksetzen Features verwendet</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left">Wann sollte ich Compact OS werden verwendet?</td>
<td align="left">Sowohl die Komprimierung des Systems Dateien und Single instancing von Anpassungen ähnliche Merkmale aufweisen wie die Technologie WIMBoot aus Windows 8.1. Während Compact OS auf alle Hardwarekonfigurationen unterstützt wird, empfiehlt es sich nur auf Computern mit Flash-basierte Speicher verwendet werden.</td>
</tr>
<tr class="even">
<td align="left">Wie weiß ich, wenn das Betriebssystem komprimiert werden?</td>
<td align="left">Compact.exe kann den aktuellen Komprimierungsstatus Abfragen verwendet werden.</td>
</tr>
<tr class="odd">
<td align="left">Wie kann ich feststellen, wenn eine .ppkg Einzelinstanz-ist?</td>
<td align="left">Führen Sie Fsutil.exe, und geben Sie das Laufwerk, auf dem die .ppkg gespeichert ist. Beispiel: <code>fsutil.exe wim enumwims c:</code></td>
</tr>
<tr class="even">
<td align="left">Gibt es Formatierungen Anforderungen für die Datei ResetConfig.xml?</td>
<td align="left">Ja. Immer UTF-8-Codierung verwendet, und verwenden Sie keine Unicode- oder ANSI. Fügen Sie die folgende Deklaration hinzu, in der Datei ResetConfig.xml und in anderen XML-Dateien: <code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;</code>.</td>
</tr>
<tr class="odd">
<td align="left">Welche Arten von Wechseldatenträgern für Hersteller erstellt Wiederherstellungsmedien unterstützt werden?</td>
<td align="left">DVDs oder USB-Laufwerke können als Wiederherstellungsmedien verwendet werden. Beachten Sie, dass Drucktaste zurücksetzen Features erfordert alle Recovery-Ressourcen auf dem gleichen Mediums befinden.</td>
</tr>
<tr class="even">
<td align="left">Werden recimg.exe wird in Windows 10 unterstützt?</td>
<td align="left">Keine recimg.exe ist in Windows 10 veraltet.</td>
</tr>
<tr class="odd">
<td align="left">Werden Drucktaste Zurücksetzen wird unter Windows Server unterstützt?</td>
<td align="left">Nein, wird diese Funktionalität auf Windows Server 2016 – Technische Vorschau nicht unterstützt.</td>
</tr>
<tr class="even">
<td align="left">Benutzerdefinierte Recovery Solutions (d. h. nicht Drucktaste Reset) können die Bereitstellung Pakete mit Windows ICD oder des USMT ScanState-Tool erstellt wiederhergestellt werden.</td>
<td align="left">Bereitstellung Pakete kann nur durch Drucktaste zurücksetzen oder Bereitstellung Medien erstellt mithilfe von Windows Imaging und Konfiguration Designer (ICD) angewendet werden. Anwendung dieser Pakete von benutzerdefinierten Recovery Solutions wird nicht unterstützt.</td>
</tr>
<tr class="odd">
<td align="left">Wenn das Bereitstellung Paket erstellt mithilfe ist des ScanState dieses Tool größer als 4GB, lässt das Hilfsprogramm "Erstellen einer Wiederherstellungslaufwerk" Kunden USB Wiederherstellungsmedien erstellen?</td>
<td align="left">Ja, wird das Dienstprogramm <strong>Erstellen einer Wiederherstellungslaufwerk</strong> provisioning Paket zu unterteilen aufgeteilt, bevor sie in das USB-Gerät kopiert. Während der Wiederherstellung werden die Teile in der ursprünglichen Bereitstellung Paket zusammengesetzt werden.</td>
</tr>
<tr class="even">
<td align="left">Vorinstalliert ich habe OS Updates auf dem PC, wie können Sie sicherstellen, dass sie während der Wiederherstellung wiederhergestellt werden?</td>
<td align="left">Des DISM.exe /Cleanup-Image Befehl mit den Optionen /StartComponentCleanup und /ResetBase markiert alle OS Updates als Permanent. Permanente Updates werden immer während der Wiederherstellung wiederhergestellt.</td>
</tr>
<tr class="odd">
<td align="left">Wie kann ich feststellen, wenn die Option /ResetBase zuletzt ausgeführt wurde?</td>
<td align="left"><p>Überprüfen des <strong>LastResetBase_UTC</strong> Registrierungseintrags unter dem Registrierungspfad:</p>
<p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component basierend – Wartung</p></td>
</tr>
<tr class="even">
<td align="left">Mir Dateien, beibehalten/wiederhergestellt bei Ihrem PC und Refresh PC ausgeführt werden zurückgesetzt werden müssen, aber ich möchte nicht zu erfassen ScanState verwenden. Dabei sollte ich diese Dateien zu platzieren?</td>
<td align="left">Alle Inhalte unter C:\Recovery\OEM bleiben unverändert Zurücksetzen des Computers und den PC zu aktualisieren. Jedoch darauf hinzuweisen, dass dieser Inhalt auch auf den Datenträger des USB-Wiederherstellung gesichert werden werden, wenn mit dem Erstellen einer Wiederherstellung Laufwerk Dienstprogramm.</td>
</tr>
<tr class="odd">
<td align="left">Ich kann der Aktualisierung Ihrer PC-Option in Einstellungen oder Windows RE mehr nicht finden. Wo ist das Feature?</td>
<td align="left">Beide Aktualisieren der PC und Ihrem PC sind nun Teil der gleichen Benutzer auftreten, unter der Option Zurücksetzen dieser PC auf Einstellungen und in Windows RE zurücksetzen. Wenn Sie diese PC-Erfahrung zurücksetzen starten, sehen Sie zusätzliche Optionen:
<ul>
<li><strong>Meine Dateien behalten</strong> – dies initiiert das Aktualisieren Ihrer PC-Feature.</li>
<li><strong>Entfernen Sie alles</strong> – dies initiiert das Zurücksetzen Ihrer PC-Feature.</li>
<li><strong>Wiederherstellen von Factory Einstellungen</strong> – auf PCs aus Windows 8/8.1 aktualisiert diese Factory Wiederherstellung mit der vorhandenen Recovery Image initiiert.</li>
</ul></td>
</tr>
<tr class="even">
<td align="left">Sollte ich die Option /drivers angeben, wenn Sie ScanState mit Anpassungen erfassen?</td>
<td align="left">Die Option /drivers ist nicht erforderlich, wenn provisioning erstellten Pakets ist für Drucktaste zurücksetzen Features verwendet werden soll. Drucktaste zurücksetzen Features beibehalten der Treiber die bereits installiert sind, leicht nicht erforderlich, die Factory vorinstalliert Treiber erneut anwenden. Hinweis: Treiber Applets außerhalb des Treiberpakets INF-Datei installiert werden mithilfe ScanStates /apps Option erfasst.</td>
</tr>
<tr class="odd">
<td align="left">Wie viel Speicherplatz ist erforderlich, in der Reihenfolge für die Aktualisierung Ihrer PC-Funktion erfolgreich ausgeführt?</td>
<td align="left">Wenn Sie die installierten Anpassungen in verweisen auf die Anpassungen Paket mit ScanState erstellt Datei Zeiger konvertiert haben, ist der erforderliche Speicherplatz: 4GB + Size_of_ppkg * 0,2
<p>Andernfalls ist der erforderliche Speicherplatz: 4GB + Size_of_ppkg * 2</p></td>
</tr>
<tr class="even">
<td align="left">Muss ich die Größe des GPT von 128 MB auf 16 MB basierend auf den aktualisierten Partition Layout Empfehlungen zu reduzieren?</td>
<td align="left">Nein. 128 MB MSR-Partitionen unterstützt weiterhin Windows. Jedoch ist auf PCs mit begrenzter Speicherkapazität, einem GPT 16 MB empfohlen, für Endbenutzer als möglichst viel Speicherplatz ein.</td>
</tr>
<tr class="odd">
<td align="left">Ist es, dass alle bekanntes Problem bei der Verwendung von Ihrem PC, um PCs auf Factory Bedingung zurückzusetzen, nach dem durchgehen Factory Floor testen zurücksetzen?</td>
<td align="left">PBR Features nicht gedacht sind auf Factory Etagen verwendet werden, besteht keine technische Einschränkung die verhindert, es dass. Behalten Sie jedoch Folgendes beachten bei Verwendung von Ihrem PC zurücksetzen unter werksseitige:
<ul>
<li>Wenn die Factory Floor Tests Windows aktivieren enthält, wird zurücksetzen PC die Einheit an einem nicht aktivierten Zustand nicht zurückgesetzt.</li>
<li>Vorinstalliertes RDX Inhalt werden entfernt</li>
<li>Wenn die Einheit nicht für mehrere Tage nach der Validierung Factory jedoch bleibt eingeschaltet zurückgesetzt wird, werden die vorinstallierten Sprachen außer während OOBE ausgewählt während der Wartung entfernt werden</li>
<li>Endbenutzer können sehen, erklären Sie, dass eine Einheit für die Protokolle PBR unter C:\Windows\Logs\PBR Schlüsseltokens während Factory zurückgesetzt wurde</li>
</ul></td>
</tr>
</tbody>
</table>

 

 

 





