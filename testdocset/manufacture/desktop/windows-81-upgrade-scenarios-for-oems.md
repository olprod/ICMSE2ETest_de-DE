---
author: Justinha
Description: Windows 8.1 Upgradeszenarien OEMs
ms.assetid: 92f0ef1c-06e0-4f9b-8009-9567ae1bfaac
MSHAttr: PreferredLib:/library/windows/hardware
title: Upgradeszenarien OEMs Windows 8.1
ms.openlocfilehash: 05721f74166e679270f4e214bedde551be701714
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-81-upgrade-scenarios-for-oems"></a>Windows 8.1 Upgradeszenarien OEMs


Die Aktualisierung von Windows 8.1 behält die Mehrzahl der OEM-Anpassungen, einschließlich OEM-branding, apps, Hilfe und Support-Informationen, Treiber und OEM Store-Auflistungen. Erleben Sie einige OEM-Lösungen, einschließlich einer benutzerdefinierte Hilfe und Support oder benutzerdefinierte Lösung möglicherweise nicht über das Upgrade beibehalten werden. Testen Sie, um potenzielle Probleme für Ihre Kunden zu verringern, die End-to-End-Aktualisierungsvorgang.

Die Windows 8.1 kann aus dem Windows Store oder auf einem Datenträger installiert werden.

Upgrade-Optionen für Windows 8.1 umfassen:

-   **Vollständige Aktualisierung** behält bei apps, Benutzerdaten, Benutzerkonten und PC-Einstellungen.

-   **Nur Daten** behält Benutzerkonten und Daten, jedoch nicht beibehalten, OS Einstellungen oder desktop-Anwendung installiert. Treibern, die entscheidend für die Installation (Speicher- und Treiber) sind, werden in die neue Installation migriert.

-   **Installieren Sie** speichern keine Daten oder Windows-Konfigurationen.

Alle persönlichen Dateien und Windows-Dateien und Verzeichnisse, in einen Ordner Windows.old verschoben werden, und nach Abschluss des Setups Windows zugegriffen werden können. Persönliche Dateien bleiben im Windows.old. Windows-Dateien aus der vorherigen Installation werden nach einem Zeitraum entfernt.

Die unterstützten Optionen für das Upgrade sind:

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Frühere OS</th>
<th align="left">Ausführen eines vollständigen Upgrades</th>
<th align="left">Nur Daten</th>
<th align="left">Neuinstallation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8 (aus dem Windows Store)</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows RT (aus dem Windows Store)</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8 (von Medien)</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows 7 (von Medien)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
</tbody>
</table>

 

Windows 8.1 Installationen zur Aktualisierung von Windows Vista und Windows XP werden nicht unterstützt.

## <a name="span-idrollbackspanspan-idrollbackspansystem-rollback-log-files"></a><span id="ROLLBACK"></span><span id="rollback"></span>System Rollback-Protokolldateien


Rollback auf die vorherige Installation tritt auf, wenn die Windows-Aktualisierung ein Fehler auftritt. Probleme zu beheben, indem Sie die Protokolldateien ansehen (*&lt;Laufwerk&gt;*$Windows. ~ BT\\Quellen\\Panther und Quellen\\Rollback, wobei * &lt;Laufwerk&gt; * ist der Stamm des Laufwerks, auf dem Windows installiert ist).

**Warnung**  
Das Bild Push-Button zurückgesetzt wird nicht mehr auf Windows RT Geräten verfügbar sein, bei einem System Rollback.

 

## <a name="span-idlowdiskspanspan-idlowdiskspanlow-disk-space"></a><span id="LOWDISK"></span><span id="lowdisk"></span>Nicht genügend Speicherplatz


Windows 8.1 kann mit begrenztem Speicherplatz auf Computern installiert werden. Die Fenster Upgradeprozess komprimiert die vorherige Windows-Installation und löscht große Zwischenspeichern von Dateien.

## <a name="span-idwinrespanspan-idwinrespanspan-idwinrespanwindows-re"></a><span id="WinRE"></span><span id="winre"></span><span id="WINRE"></span>Windows RE


Eine Windows 8.1-Version von Windows RE wird installiert, damit das Betriebssystem repariert werden kann. Starten Sie während des Upgrades kritische und input Gerät, das das neue Windows RE-Abbild Treiber hinzugefügt werden.

Windows RE wird wie folgt installiert:

1.  Die vorhandene Windows RE-Partition wird auf Windows-RW verwendet.

2.  Windows RE-Partition wird auf Windows 8-PCs mit einer OEM-konfiguriert Windows RE-Partition beibehalten. Eine neue Windows RE-Partition wird durch die Windows-Partition verkleinern erstellt.

3.  Die vorhandene Windows RE-Partition wird mit einer generischen Windows RE-Partition auf Windows 8 PCs verwendet.

**Vorsicht**  
OEM-Anpassungen der vorhandenen Windows RE-Abbild werden nicht in die neue Windows RE-Abbild migriert.

 

## <a name="span-idrecpbrspanspan-idrecpbrspanrecovery-image-for-push-button-reset"></a><span id="RECPBR"></span><span id="recpbr"></span>Recovery-Bild für die Schaltfläche Zurücksetzen


Das Bild Schaltfläche Zurücksetzen wird basierend auf der folgenden Implementierung aktualisiert:

Vor dem Upgrade nach dem Upgrade Plattform **lokale Recovery Bild Verfügbarkeit**

**Upgrademethode**

**Image-Wiederherstellung**

**Wiederherstellung Image-partition**

X64, x86

Lokale Recovery Bild ist verfügbar

Medien oder Windows Store

Vorhandenes Bild von Windows 8-Wiederherstellung

Vorhandene Partition ist nicht veränderten

X64, x86

Lokale Recovery Bild ist nicht verfügbar

Medien oder Windows Store

Keine

Keine

Windows RT

Lokale Recovery Bild ist verfügbar

Windows Store

Neue Windows 8.1 Recovery-Bild

Vorhandene Partition wird wieder verwendet.

Windows RT

Lokale Recovery Bild ist nicht verfügbar

Windows Store

Keine

Keine

 

Das Bild wird auf Windows RT-PCs mit einem vorhandenen Wiederherstellungsabbild durch Windows 8.1 Image-Wiederherstellung ersetzt. Die folgenden Anpassungen werden migriert des Bilds Windows 8.1 Recovery einschließlich:

-   Speichern von Anpassungen und Lizenzen für vorinstallierte Windows Store-apps

-   Treiber kompatibel mit Windows 8.1

-   OEM-Supportinformationen

Das Wiederherstellungsabbild bleibt auf Windows 8 PCs an einem vorhandenen Recovery Bild.

Wenn das vorherige Betriebssystem eine vorhandene besitzt werden Wiederherstellung Image-Partition, keine Wiederherstellungsabbild oder Partitionen erstellt.

## <a name="span-iddriversspanspan-iddriversspandrivers"></a><span id="DRIVERS"></span><span id="drivers"></span>Treiber


Vollständige Aktualisierung in Szenarien, die folgenden Treiber Typen werden migriert:

-   Kompatible Treiber

-   Von einem OEM oder Endbenutzer installiert Treiber von Drittanbietern

-   Treiber, die für die Installation von entscheidender Bedeutung sind werden Windows PE als auch für das Betriebssystem in allen Upgradeszenarien migriert.

Die folgenden Treiber werden nicht migriert:

-   In-Box-Treiber von Drittanbietern wie Druckertreiber, werden nicht migriert werden, weil das neue Betriebssystem in der Regel Weitere auf dem neuesten Stand Treiber enthält.

-   Software Filtertreiber werden nicht migriert, mit Ausnahme von Antivirus Treiber oder durch eine INF-Datei installiert Treiber zu filtern.

Netzwerk- und Wi-Fi-Treiber werden auf Neuinstallationen und nur Daten Upgradeszenarien migriert.

Alle migrierten Treiber befinden sich im Treiberrepository und Windows automatisch installiert Treiber während der Plug & Play-basierend auf den Kriterien in [Wie Windows Rangfolgen-Treiber](http://go.microsoft.com/fwlink/?LinkId=294347)definiert.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Windows-Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md)

 

 






