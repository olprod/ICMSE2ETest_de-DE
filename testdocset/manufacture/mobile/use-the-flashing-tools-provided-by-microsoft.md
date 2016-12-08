---
title: Verwenden Sie die blinkende von Microsoft bereitgestellten tools
description: Verwenden Sie die blinkende von Microsoft bereitgestellten tools
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: deb8960a-18b0-447d-ba6d-5611def266c0
ms.openlocfilehash: 9ab519b802b4a35907605a97fcd573f2fb588b58
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-flashing-tools-provided-by-microsoft"></a>Verwenden Sie die blinkende von Microsoft bereitgestellten tools


Microsoft stellt ein Toolset für blinkende für Geräte bereit. Dieses Tool enthält ffutool.exe ein Befehlszeilentool, das auf dem Entwicklungscomputer ausgeführt wird und ffuloader.efi, ein Gerät clientseitigen UEFI blinkendes Anwendung. In diesem Thema wird beschrieben, wie Ihr Gerät einrichten und Entwicklungscomputer dieses Tools, und Verwendung erläutert.

**Wichtige**  
-   In Windows 1607 Version 10, wird ffutool.exe von dem Assessment and Deployment Kit (ADK) installiert. In früheren Versionen von Windows 10 wird ffutool.exe von der Windows Driver Kit (WDK), Enterprise WDK (EWDK) oder Windows Hardware Lab Kit (HLK) installiert.

-   Gerät-Side UEFI blinkende Anwendung von Microsoft wird automatisch in alle Bilder enthalten. Diese Anwendung muss auf allen Geräten für den Einzelhandel enthalten sein.

-   Für blinkende Geräte während der Herstellung können OEMs eigene blinkende Tools mithilfe der Informationen in [Developing benutzerdefinierte OEM blinkende Tools](developing-custom-oem-flashing-tools.md) oder mithilfe von ffutool.exe erstellen. Wenn Sie Ihr Bild blinkt Ffutool verwenden, kann es langsamer als andere blinkende Tools sein.

 

## <a name="a-href-idinitialdevicesidesetupainitial-device-side-setup"></a><a href="" id="initialdevicesidesetup"></a>Gerät-Side ersteinrichtung


Führen Sie zur Vorbereitung eines Geräts blinken mithilfe eines Windows 10 Mobile Abbilds die folgenden Schritte aus:

1.  Mithilfe von Tools des Herstellers SoC einer UEFI auf jedem Gerät erhalten möchten, die aktualisiert werden muss. Geräte müssen startbaren mindestens auf die UEFI für blinken zu sein.

    In der Regel erfolgt dies mit dem eMMC Software Downloader. Diese UEFI sollte die gleichen UEFI sein, die in Gerätebilder enthalten ist.

2.  Nach einem startbaren UEFI vorhanden ist, müssen die blinkende Anwendung (ffuloader.efi) und Unterstützung für einfache e/a-Treiber (efisimpleio.dll) das Gerät hinzugefügt und beim Start ausgeführt werden. Führen Sie hierzu das Übernehmen ffubinaries.bat Skript ein, während das Gerät mit dem Entwicklungscomputer verbunden ist. Alle diese Dateien stehen zur Verfügung, des Kits in %ProgramFiles(x86)%\\Windows Kits\\10\\Tools\\Bin\\i386.

    Das Skript übernehmen ffubinaries.bat ffuloader.efi und efisimpleio.dll in den Stamm des Verzeichnisses ESP auf dem Gerät kopiert und die Konfigurationsdatenbank Boot auf Boot sofort blinkende Modus Hingehen festgelegt. Dieses Skript erfordert bcdedit.exe im Pfad.

**Hinweis**  
Diese Schritte müssen nur einmal auf jedem Gerät ausgeführt werden. Nachdem Sie diese Schritte ausgeführt werden, werden Sie können verschiedene Bilder auf das Gerät flash

 

## <a name="a-href-idhostsidesetupahost-side-setup"></a><a href="" id="hostsidesetup"></a>Host-Side-setup


Blinken auf der Hostseite erfolgt über eine Verbindung mit WinUSB den Treiber Microsoft Universal USB-Gerät eingerichtet. Standardmäßig in Windows 8 und höher sind die erforderlichen Treiber enthalten.

In Windows 7 können die erforderlichen Treiber von Windows Update installiert werden. So konfigurieren Sie einen Computer Windows 7, um die erforderlichen Treiber zu installieren:

1.  Klicken Sie auf Start.

2.  Typ **Geräteeinstellungen-Installation**.

3.  Wählen Sie **Ja, dies automatisch (empfohlen)**.

4.  Klicken Sie auf **Änderungen zu speichern**.

## <a name="a-href-idflashingprocedureaflashing-procedure"></a><a href="" id="flashingprocedure"></a>Prozedur blinken


Nachdem das Gerät und Host-Setup abgeschlossen ist, führen Sie die folgenden Schritte aus, um ein Gerät flash:

1.  Starten Sie das Gerät in der FFU Download-Modus, während er auf den Hostcomputer verbunden ist. Sie haben verschiedene Möglichkeiten, um das Gerät in der FFU Download-Modus während des Startvorgangs zu erzwingen:

    -   Schließen Sie das Paket Microsoft.BCD.Lab.spkg in Ihr Bild durch Angeben der optionalen Funktion **LABIMAGE** beim Generieren des Test Bilds ein Wenn dieses Paket im Testbild enthalten ist, wird das Gerät automatisch den FFU Download-Modus, wenn es gestartet wird. Weitere Informationen zum Umwandeln eines Bildes finden Sie unter [Erstellen eines Telefon-Abbilds ImgGen.cmd verwenden](building-a-phone-image-using-imggencmd.md).

    -   Um das Gerät manuell in den FFU Download-Modus erzwingen, drücken Sie und halten Sie, um das Gerät zu starten und klicken Sie dann sofort drücken und halten die Lautstärke Schaltfläche nach oben. Diese Option ist verfügbar, nachdem eine anfängliche FFU hat auf das Gerät aktualisiert wurde.

2.  Führen Sie an der Befehlszeile ein Bild blinkt ffutool.exe. Dieses Programm ist in %ProgramFiles(x86)%\\Windows Kits\\10\\Tools\\Bin\\i386. Es folgt ein Beispiel für die Verwendung.

    ``` syntax
    ffutool -flash <FFU file>
    ```

    In der folgenden Tabelle werden die Befehlszeilenparameter für ffutool.exe beschrieben.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Parameter</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>-flash</strong> <em>FFU-Datei</em></p></td>
    <td><p>Gibt den Pfad zur Datei FFU, die an das Gerät blinken soll.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>-Überspringen</strong></p></td>
    <td><p>Für Geräte, die enthalten die optionale <strong>LABIMAGE</strong> -Funktion in der FFU Download-Modus automatisch starten, startet dieser Parameter das Hauptfenster Betriebssystem (wird übersprungen des FFU Download-Modus).</p></td>
    </tr>
    </tbody>
    </table>

     

Sie können mehrere Geräte zu einem Zeitpunkt mithilfe von ffutool.exe blinken. Zu diesem Zweck sicher, dass alle Geräte vor dem Ausführen ffutool.exe herstellen. Darüber hinaus wird empfohlen, dass Sie eine USB-Karte, die einen dedizierten Root-Hub pro Port enthält verwenden, sodass ein Problem blinkt ein Gerät nicht auf allen Geräten auswirkt.

**Hinweis**  
Blinkendes Geschwindigkeit verschlechtert, wie Sie Geräte hinzufügen.

 

## <a name="a-href-idvalidatingplatformidavalidations-performed-by-the-microsoft-flashing-tool"></a><a href="" id="validatingplatformid"></a>Überprüfungen, die durch das blinkende Tool von Microsoft durchgeführt


Vor der Schwelle blinkt, führt die blinkende Anwendung UEFI Gerät-Side von Microsoft bereitgestellten die folgenden Überprüfungen im Bild:

-   Die Anwendung überprüft die Bild-Signaturen gegen die Plattform Schlüssel (PK) und die Microsoft Windows Phone Produktion PCA 2012-Zertifikat (für den Einzelhandel Bilder) oder Microsoft Test-Stammzertifizierungsstelle Zertifikat (für nicht-Verkaufsversion Bilder).

-   Die Anwendung überprüft die Hashes von jeder Ausschnitt von Daten in das Bild für die Tabelle des weiteren von der Katalogdatei signiert.

-   Die Anwendung wird überprüft, dass das Bild die aktuellen Geräteplattform unterstützt. Um diese Überprüfung durchführen, vergleicht die Anwendung mehrere Werte in die Struktur der SMBIOS System mit den entsprechenden Werten in das Gerät Plattform-Paket. Diese Prüfungen dazu beitragen, stellen Sie sicher, dass ein Bild zu einem bestimmten Gerät zugeordnet werden kann, nur, wenn es für das entsprechende Geräteplattform entwickelt wurde. Weitere Informationen über diese Prüfungen finden Sie weiter unten.

### <a name="device-platform-validation-checks"></a>Gerät-Plattform validierungsüberprüfungen

Um zu überprüfen, dass das Bild die aktuellen Geräteplattform vor blinken unterstützt, führt die Anwendung die folgenden Aufgaben:

1.  Aus dem Gerät Plattform-Paket in das Bild, das aktualisiert wird, wird die Zeichenfolge **DevicePlatformID** abgerufen. Weitere Informationen zu dieser Zeichenfolge finden Sie unter [Festlegen von Geräteinformationen-Plattform](set-device-platform-information.md).

2.  Wenn die Zeichenfolge das Format *Hersteller*aufweist. - *Familie*. *Produktname*. *Version* und alle vier Werte in der Zeichenfolge Übereinstimmung die entsprechenden *Hersteller*, *Familie*, *Produktname*und *Version* SMBIOS Werte auf dem Gerät, die Plattform Validierung erfolgreich ist und die blinkende Vorgang fortgesetzt wird.

3.  Wenn die Zeichenfolge das Format *Hersteller*verfügt. - *Familie*. *Produktname* und alle drei Werte in der Zeichenfolge Übereinstimmung die entsprechenden *Hersteller*, *Familienangehörige*und *Produktname* SMBIOS Werte auf dem Gerät, die Plattform Validierung erfolgreich ist und die blinkende Vorgang fortgesetzt wird.

4.  Sie andernfalls die Plattform Überprüfung fehlschlägt, und das Bild blinkt nicht auf das Gerät.

In einem nicht-Einzelhandel-Abbild OEMs die Gerät Plattform Validierung blinken durch Hinzufügen von DEAKTIVIEREN deaktivieren\_FFU\_PLAT\_ID\_KONTROLLKÄSTCHEN Feature zur OEMInput-Datei, die zum Generieren des Bilds verwendet wird.

**Wichtige**  
Die Gerät Plattform Validierung blinken muss im Einzelhandel Bilder nicht deaktiviert werden.

 

## <a name="ffu-tool-error-codes"></a>FFU Tool-Fehlercodes


Wenn Sie das Tool FFU verwenden ein Bilds auf Ihrem Gerät blinkt, möglicherweise ein Fehler auftritt, wie unten dargestellt.

``` syntax
Error: Failed to flash with device error { 0x18, 0x0, 0x0, 0x2, 0xa, 0x5 }
```

Die erste Hexadezimalzahl ist ein Ereigniscode, der den Typ des blinkende Fehler angibt. Die folgende Tabelle enthält eine Beschreibung des Tools FFU blinken Fehler.

**Häufige Fehler**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlercode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0xC</p></td>
<td><p>Beim Anwenden des Abbilds auf dem Datenträger, konnte ein Lesevorgang alle in der aktuellen Daten Deskriptor angegebenen Blöcke zurückgeben.</p>
<p>Dieser Fehler wird normalerweise durch einen beschädigten Bild verursachen. Das Bild wird normalerweise müssen neu erstellt werden. Weitere Informationen finden Sie unter [Erstellen von ein Telefon-Bild mithilfe eines ImgGen.cmd](building-a-phone-image-using-imggencmd.md).</p></td>
</tr>
<tr class="even">
<td><p>0 x 18</p></td>
<td><p>Während initialisieren Hash überprüft, Fehler bei einem Katalog Signatur Kontrollkästchen.</p>
<p>Wenn dieser Fehler auftritt, wird es in der Regel in Bezug auf signierenden des Bilds. Weitere Informationen finden Sie unter [Signieren einer vollständigen flash aktualisierungsabbild (FFU)](sign-a-full-flash-update--ffu--image.md).</p></td>
</tr>
<tr class="odd">
<td><p>0x1C</p></td>
<td><p>Eine oder mehrere Write Deskriptoren finden Sie unter Speicherorte ungültigen Datenträger.</p>
<p>Dieser Fehler weist normalerweise, dass das Bild für ein Telefon mit mehr Speicherplatz als das aktuelle Telefon tatsächlich hat erstellt wurde. Suchen Sie das richtige Bild oder aktualisieren Sie das Bild, das Ihnen durch Reduzierung der in OEMDevicePlatform.xml angegebenen MinSectorCount. Weitere Informationen finden Sie unter [Festlegen von Geräteinformationen-Plattform](set-device-platform-information.md).</p></td>
</tr>
</tbody>
</table>

 

**Weiteren Fehlern**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlercode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0 x 8</p></td>
<td><p>Ein ungültiger binary manifest Header wurde bei der Vorbereitung des Geräts blinken gelesen.</p></td>
</tr>
<tr class="even">
<td><p>0 x 9</p></td>
<td><p>Die Anwendung konnte nicht genügend Speicher zum Kopieren der Datenträger schreiben Deskriptor-Tabelle zugeordnet werden.</p></td>
</tr>
<tr class="odd">
<td><p>0xb</p></td>
<td><p>Konnte nicht vor dem Schreiben von Daten, die blinkende Anwendung alle Datenträger schreiben-Deskriptoren gelesen werden.</p></td>
</tr>
<tr class="even">
<td><p>0xD</p></td>
<td><p>Beim Anwenden des Abbilds auf dem Datenträger, konnte kein Schreibvorgang blockieren.</p></td>
</tr>
<tr class="odd">
<td><p>0xE zurückgeliefert</p></td>
<td><p>Ein Paket von der Anwendung blinkende gelesen, eine ungültige Prüfsumme enthalten sind.</p></td>
</tr>
<tr class="even">
<td><p>0xF</p></td>
<td><p>Beim Vorbereiten des Abbilds blinkt, war die blinkende Anwendung die vollständige Sicherheit Kopfzeile konnte nicht gelesen.</p></td>
</tr>
<tr class="odd">
<td><p>0 x 10</p></td>
<td><p>Beim Vorbereiten des Abbilds blinkt, lesen Sie die blinkende Anwendung eine ungültige Sicherheit Kopfzeile.</p></td>
</tr>
<tr class="even">
<td><p>0x11</p></td>
<td><p>Beim Vorbereiten des Abbilds blinkt, konnte die blinkende Anwendung die erwartete den Abstand nach dem Sicherheitsheader lesen.</p></td>
</tr>
<tr class="odd">
<td><p>0 x 12</p></td>
<td><p>Beim Vorbereiten des Abbilds blinkt, lesen Sie die blinkende Anwendung eine ungültige Bild-Kopfzeile.</p></td>
</tr>
<tr class="even">
<td><p>0 x 13</p></td>
<td><p>Beim Vorbereiten des Abbilds blinkt, konnte die blinkende Anwendung die erwartete Anzahl von Leerstellen nach dem Bildheader zu lesen.</p></td>
</tr>
<tr class="odd">
<td><p>0 x 14</p></td>
<td><p>Beim Vorbereiten des Abbilds auf dem Datenträger anwenden, konnte nicht den Block Flasher Puffer genügend Bytes im Stream blinkt sicher.</p></td>
</tr>
<tr class="even">
<td><p>0x15</p></td>
<td><p>Beim Anwenden des Abbilds auf dem Datenträger, erreicht das Blockieren Flasher Ende des Datenstroms unerwartet. Dies gibt an, dass ein Bild nicht korrekt erstellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p>0 x 16</p></td>
<td><p>Die Plattform-ID in das Bild angegebenen entspricht nicht die ID des Geräts, die blinken soll.</p></td>
</tr>
<tr class="even">
<td><p>0 x 17</p></td>
<td><p>Beim Lesen von Bilddaten, konnte nicht in eine Hash-Prüfung.</p></td>
</tr>
<tr class="odd">
<td><p>0x1A</p></td>
<td><p>Fehler beim Abrufen von eines Handles für das UEFI Firmware der Aufhebung der Synchronisierung-Ereignis.</p></td>
</tr>
<tr class="even">
<td><p>0x1B</p></td>
<td><p>Fehler beim Abfragen der Startkonfigurationsdaten für die Plattform-ID Kontrollkästchen Einstellungen.</p></td>
</tr>
<tr class="odd">
<td><p>0x1D</p></td>
<td><p>Das Bild hat keinen zurücksetzen Schutz aktiviert, oder ein nicht unterstütztes zurücksetzen Schutz Bild wurde verwendet.</p></td>
</tr>
<tr class="even">
<td><p>0 x 20</p></td>
<td><p>Das Bild kann nicht auf einem Wechselmedium aktualisiert werden.</p></td>
</tr>
<tr class="odd">
<td><p>0 x 21</p></td>
<td><p>Kann keine optimierte blinkende-Methode verwenden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Erstellen und blinkende](building-and-flashing-images.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Use%20the%20flashing%20tools%20provided%20by%20Microsoft%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





