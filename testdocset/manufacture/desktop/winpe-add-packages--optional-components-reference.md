---
author: Justinha
Description: "Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)"
ms.assetid: 67aa9c25-9fab-4970-8aa5-65f904969e8e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)"
ms.openlocfilehash: ea77090f9d579bc951e1a3dda30ab7f540b7328e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-add-packages-optional-components-reference"></a>Windows PE: Hinzufügen von Paketen (optionalen Komponenten Reference (engl.)


Windows PE (Windows PE) Featurepakete, auch bekannt als optionale Komponenten hinzugefügt.

**Sprachen**: bei der Installation von einzelnen optionalen Komponenten müssen Sie installieren Sie zunächst die optionale Komponente sprachneutrale und installieren Sie dann die Liste der sprachspezifischen optionale Komponente. Die erforderlichen Sprachressourcen muss die gleiche Version als der sprachneutralen Ressourcen. Sprachressourcen befinden sich in einem Ordner mit dem gleichen Namen wie die Sprache, die im Verzeichnis der optionalen Komponenten installiert ist.

## <a name="span-idbkmk1spanspan-idbkmk1spanadding-optional-components"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>Hinzufügen von optionalen Komponenten


Optionale Komponenten sind in Windows Assessment and Deployment Kit (Windows ADK), in das Laufwerk C: enthalten\\Program Files\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Vorinstallation Umgebung\\amd64\\Windows PE\_OCs\\ Ordner.

**Abrufen von Windows Assessment and Deployment Kit mit Windows PE-tools**

-   Installieren Sie [Windows Assessment and Deployment Kit (Windows ADK) technische Referenz](http://go.microsoft.com/fwlink/p/?LinkId=526803), einschließlich des Windows PE-Features.

**Erstellen einer Gruppe von 32-Bit oder 64-Bit-Windows PE-Dateien**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Kopieren Sie Sie in den **Bereitstellungstools und Imaging-Umgebung**Windows PE-Dateien für die PCs, die Sie starten möchten.

    -   Die 64-Bit-Version kann UEFI 64-Bit- und 64-Bit-BIOS PCs gestartet werden.

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   Die 32-Bit-Version kann 32-Bit-UEFI, BIOS-32-Bit- und 64-Bit-BIOS-PCs gestartet werden.

        ``` syntax
        copype x86 C:\WinPE_x86
        ```

**Stellen Sie das Windows PE Boot-Abbild**

-   Stellen Sie das Windows PE-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

**Hinzufügen von optionalen Komponenten (Pakete oder CAB-Dateien)**

1.  Fügen Sie die optionale Komponente Windows PE hinzu. Wenn optionale Komponenten hinzufügen möchten, müssen Sie die optionale Komponente und der zugeordneten Sprachpakete hinzufügen.

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-HTA.cab"  

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"
    ```

    **Wichtige**  
    Einige optionalen Komponenten müssen die erforderlichen Komponenten, die in der Reihenfolge installiert werden müssen. Finden Sie auf dieser Seite in der Liste der optionalen Komponenten.

     

2.  Stellen Sie sicher, dass die optionale Komponente Teil des Bilds ist:

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

    Überprüfen der resultierenden Liste der Pakete, und stellen Sie sicher, dass die Liste die optionale Komponente und die zugehörigen Language Pack enthält.

**Fügen Sie weitere Sprachen hinzu, um Bilder, die optionale Komponenten enthalten**

1.  Die optionalen Komponenten im Windows PE-Abbild aufgelistet:

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

2.  Überprüfen der resultierenden Liste der Pakete, und fügen Sie die entsprechenden Language Packs für jedes Paket im Bild, einschließlich des Basis Windows PE-Language Packs.

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

    WHERE... Windows PE\_OCs\\fr-fr\\lp.cab stellt das base Windows PE-Language Pack.

3.  Wenn Sie Language Packs für Japan, Korea oder China hinzufügen, fügen Sie die Schriftart-Pakete für diese Sprachen hinzu. Es folgt ein Beispiel für Japan:

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Font Support-JA-JP.cab"
    ```

4.  Stellen Sie sicher, dass die Language Packs Teil des Bilds sind:

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

    Überprüfen die resultierende Liste der Pakete, und überprüfen Sie, ob die für die einzelnen optionalen Komponenten, einschließlich der Basis Windows PE-Image, dass eine entsprechende Sprachpaket vorhanden ist.

5.  Ändern Sie die regionalen Einstellungen in der Sprache, die Sie verwenden möchten:

    ``` syntax
    Dism /Set-AllIntl:en-US /Image:"C:\WinPE_amd64\mount"
    ```

    Klicken Sie in Windows PE Sprachen verwenden, um `wpeutil setmuilanguage`.

**Heben Sie die Bereitstellung des Windows PE-Abbilds und Erstellen von Medien**

1.  Hängen Sie das Windows PE-Abbild.

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  Erstellen von startbaren Medien, wie ein USB-Laufwerk.

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  Die Medien zu starten. Windows PE wird automatisch gestartet. Nachdem das Windows PE-Fenster angezeigt wird, wird der Befehl Wpeinit automatisch ausgeführt. Dies kann einige Minuten dauern. Überprüfen Sie Ihre Anpassungen.

## <a name="span-idbkmkbspanspan-idbkmkbspanlist-of-optional-components"></a><span id="bkmk_b"></span><span id="BKMK_B"></span>Liste der optionalen Komponenten


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Komponentenname Bereich/Optional</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Datenbank/Windows PE-MDAC</p></td>
<td align="left"><p>Windows PE MDAC unterstützt Microsoft® Open Database Connectivity (ODBC), OLE DB und Microsoft ActiveX® Data Objects (ADO). Diese Sammlung von Technologien bietet Zugriff auf verschiedene Datenquellen wie Microsoft SQL Server®. Beispielsweise kann diesen Zugriff Abfragen für Microsoft SQL Server-Installationen, die ADO-Objekte enthalten. Sie können eine dynamische Antwortdatei aus eindeutigen Systeminformationen erstellen. Sie können auf ähnliche Weise Erstellen datengesteuerter Client- oder Anwendungen, die Integration von Informationen aus einer Vielzahl von Datenquellen, beide relationale (SQL Server) und nicht-relationaler.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Management/Windows PE-FMAPI Datei</p></td>
<td align="left"><p>Windows PE-FMAPI bietet Zugriff auf Windows PE Datei Management API (FMAPI) zum Ermitteln und Wiederherstellen von Dateien aus unverschlüsselte Volumes gelöscht. Das FMAPI bietet auch die Möglichkeit, eine Schlüsseldatei mit Kennwort oder Wiederherstellung für die Suche und die Wiederherstellung der gelöschten Dateien von Windows BitLocker Drive Encryption verschlüsselt Volumes verwenden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Schriftarten/Windows PE-Schriftarten-Legacy</p></td>
<td align="left"><p>Windows PE-Schriftarten-Legacy enthält 32 Schriftartendateien für verschiedene Sprachen/Schreiben von Skripts. Einige dieser Schriftarten werden nicht mehr als Benutzeroberfläche Schriftarten verwendet. Beispielsweise Skripts wie Bangla, Devanagari, Gujarati, Gurmukhi, Kannada, Malayalam, Odia, Tamil, Telugu und Singhalesisch Mangal Latha, Vrinda, Gautami, Kalinga, Artika, Raavi, Shruti und Tunga behandelt wurden, jedoch in Windows 8, sie alle unter unified Nirmala UI, eine einzige, Pan-Indian Schriftart wurden. Die folgende Liste enthält die Schriftarten und Sprachen in diese optionale Komponente enthalten:</p>
<ul>
<li><p>estre.ttf Estrangelo Edessa (Syrisch)</p></li>
<li><p>mvboli.ttf Metaverse Boli (Thaana)</p></li>
<li><p>Khmer KhmerUI.ttf-Benutzeroberfläche (UI Khmer)</p></li>
<li><p>Khmer KhmerUIB.ttf-UI fett (Khmer UI)</p></li>
<li><p>Laoui.ttf Laotisch UI (Laotisch)</p></li>
<li><p>Laouib.ttf Laotisch Benutzeroberfläche fett (Laotisch)</p></li>
<li><p>daunpenh.ttf DaunPenh (Khmer)</p></li>
<li><p>moolbor.ttf MoolBoran (Khmer)</p></li>
<li><p>dokchamp.ttf DokChampa (Laotisch)</p></li>
<li><p>Himalaya.ttf Microsoft Himalaya (Tibetisch)</p></li>
<li><p>monbaiti.ttf Mongolisch (Mongolisch) Baiti</p></li>
<li><p>MSYI.ttf Microsoft Yi Baiti (Yi Silben)</p></li>
<li><p>nyala.ttf Nyala (Äthiopien)</p></li>
<li><p>Sylfaen.ttf Sylfaen (Armenisch &amp; Georgisch)</p></li>
<li><p>euphemia.ttf Euphemia (Unified Aboriginal Kanadische)</p></li>
<li><p>plantc.ttf Plantagenet Cherokee (Cherokee)</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Schriftarten/Unterstützung für Windows PE Schriftarten-JA-JP</p></td>
<td align="left"><p>Windows PE-Schriftart Support-JA-JP enthält zwei japanische Schriftartfamilien, die als TrueType-Auflistung (TTC) Dateien vorliegen. MS Gothic ist die Windows japanische User Interface Schriftart in Versionen von Windows vor Windows Vista. MS Gothic enthält einen großen Zeichensatz und eingebettete Bitmaps lesbar Rendern in kleinen Größen sicherzustellen. Meiryo, eine Schriftart, die in Windows Vista, eingeführt wurde wurde speziell für die Verwendung in einer Umgebung mit Microsoft ClearType® Rendering entwickelt. Meiryo enthält keinen eingebetteten Bitmaps. Stattdessen nutzt Meiryo Hinweise Anweisungen zum Erzeugen lesbar Zeichen in kleinen Größen. Das Modul enthält darüber hinaus zwei japanische Bitmap-Schriftarten, App932.fon und Vga932.fon. Das Modul enthält außerdem eine Bitmap-only TrueType-Schriftart, Jpn_font.ttf. Diese Schriftart wird auf Bildschirmen Boot verwendet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Schriftarten/Unterstützung für Windows PE Schriftarten-KO-KR</p></td>
<td align="left"><p>Windows PE-Schriftart Support-KO-KR enthält drei zentrale Koreanisch Schriftartfamilien: Gulim geändert, Batang und Malgun Gothic. Gulim geändert wird die ältere Benutzeroberflächenschriftart und als TTC-Datei enthält, Gulim geändert, GulimChe, Dotum und DotumChe. Batang ist der Vorversion Textschrift und ist auch ein TTC Datei, Batang, BatangChe, GungSuh und GungSuhChe enthält. Malgun Gothic, eine Schriftart, die in Windows Vista, eingeführt wurde, wurde speziell für die Verwendung in einer Umgebung mit ClearType Rendering entwickelt. Malgun Gothic enthält keinen eingebetteten Bitmaps und Hinweise zum Erzeugen lesbar Zeichen in kleinen Größen Anweisungen angewiesen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Schriftarten/Unterstützung für Windows PE Schriftarten-ZH-CN</p></td>
<td align="left"><p>Windows PE-Schriftart Support-ZH-CN enthält zwei Chinesisch Schriftartfamilien, die als TTC Dateien vorliegen. Simsun ist die vereinfachtem Chinesisch Benutzer Schnittstelle Schriftart in Windows-Versionen vor Windows Vista. Simsun enthält eingebetteten Bitmaps um lesbar Rendering in kleinen Größen sicherzustellen. Die anderen TTC Schriftart ist MingLiu. MingLiu eingebettetem Bitmaps und bietet Unterstützung für die Hongkong zusätzliche Zeichen festgelegt (HKSCS). YaHei, eine Schriftart, die in Windows Vista, eingeführt wurde wurde speziell für die Verwendung in einer Umgebung mit ClearType Rendering entwickelt. YaHei enthält keinen eingebetteten Bitmaps. YaHei nutzt für Schriftarthinweise Anweisungen zum Erzeugen lesbar Zeichen in kleinen Größen. Das Modul enthält darüber hinaus eine Bitmap-only TrueType-Schriftart, Chs_boot.ttf. Diese Schriftart wird auf Bildschirmen Boot verwendet werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Schriftarten/Unterstützung für Windows PE Schriftarten-ZH-HK</p><p> und </p>
<p>Windows PE-Schriftart Support-ZH-TW</p></td>
<td align="left"><p>Hongkong und Taiwan optionalen Komponenten enthalten zwei Chinesisch Schriftartfamilien, die als TTC Dateien vorliegen. Simsun ist die vereinfachtem Chinesisch Benutzer Schnittstelle Schriftart in Windows-Versionen vor Windows Vista. Simsun enthält eingebetteten Bitmaps um lesbar Rendering in kleinen Größen sicherzustellen. MingLiu eingebettetem Bitmaps und bietet Unterstützung für die HKSCS. JhengHei, eine Schriftart, die in Windows Vista, eingeführt wurde wurde speziell für die Verwendung in einer Umgebung mit ClearType Rendering entwickelt. JhengHei enthält keinen eingebetteten Bitmaps. JhengHei nutzt für Schriftarthinweise Anweisungen zum Erzeugen lesbar Zeichen in kleinen Größen. Das Modul enthält darüber hinaus eine Bitmap-only TrueType-Schriftart, Cht_boot.ttf. Diese Schriftart wird auf Bildschirmen Boot verwendet.</p></td>
</tr>
<tr class="even">
<td align="left"><p>HTML/Windows PE-HTA</p></td>
<td align="left"><p>Windows PE-HTA bietet Unterstützung für HTML-Anwendung (HTA) GUI-Anwendungen durch die Windows Internet Explorer® Skriptmodul und HTML-Dienste erstellen. Diese Anwendungen sind vertrauenswürdig und Anzeigen von Menüs, Symbole, Symbolleisten und Titelinformationen, die Sie erstellen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft .NET/Windows PE-NetFX</p></td>
<td align="left"><p>Windows PE NetFX enthält eine Teilmenge der .NET Framework 4.5, das für Clientanwendungen entwickelt wurde.</p>
<p>Nicht alle Windows-Binärdateien in Windows PE vorhanden sind und werden daher nicht alle Windows-APIs vorhanden oder verwendbar. Aufgrund der begrenzten API-Satz, haben die folgenden Features von .NET Framework keine oder Funktionalität in Windows PE verringert:</p>
<ul>
<li><p>Windows Presentation Foundation (WPF)</p></li>
<li><p>Windows-Runtime</p></li>
<li><p>.NET Framework-Fusion-APIs</p></li>
<li><p>Steuerelement-Bibliothek für Windows-ereignisprotokollierung</p></li>
<li><p>.NET Framework-COM-Interoperabilität</p></li>
<li><p>.NET Framework Kryptografie-Modell</p></li>
</ul>
<p><strong>Abhängigkeiten</strong>: Installieren Sie <strong>Windows PE WMI</strong> vor der Installation von <strong>Windows PE NetFX</strong>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Netzwerk/Windows PE-Dot3Svc</p></td>
<td align="left"><p>Fügt die Unterstützung für IEEE 802.X Authentifizierungsprotokoll in verkabelten Netzwerken. Weitere Informationen finden Sie unter [Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Netzwerk/Windows PE-PPPoE</p></td>
<td align="left"><p>Windows PE PPPoE ermöglicht Point-Protokoll über Ethernet (PPPoE) zu erstellen, verbinden, trennen und Löschen von PPPoE-Verbindungen aus Windows PE verwenden. PPPoE ist ein Netzwerkprotokoll zum Kapseln von PPP-Protokoll () Rahmen innerhalb von Ethernet-Rahmen. PPPoE ermöglicht Windows-Benutzer auf ihren Computern Remote zum Internet herstellen. Mithilfe von PPPoE können Benutzer praktisch von einem Computer zu einem anderen über ein Ethernetnetzwerk herstellen eine Verbindung zwischen den Computern einwählen. Diese Verbindung können die Computer transport-Datenpaketen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Netzwerk/Windows PE-RNDIS</p></td>
<td align="left"><p>Windows PE-RNDIS enthält Remote Network Driver Interface Specification (Remote NDIS)-Support. Windows PE-RNDIS ermöglicht die Netzwerkunterstützung für Geräte, die die Spezifikation Remote NDIS über USB zu implementieren. Remote NDIS definiert eine Reihe von unabhängigen Bus-Nachricht und eine Beschreibung der Funktionsweise dieser Nachricht Satz über verschiedene e/a-Bus an. Aus diesem Grund müssen Hardwareanbietern kein NDIS-Miniporttreiber schreiben. Da diese Schnittstelle Remote NDIS standardisiert ist, kann eine Gruppe von Host-Treiber eine beliebige Anzahl von Bus angeschlossenes Netzwerkgeräte unterstützen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Netzwerk/Windows PE-WDS-Tools</p></td>
<td align="left"><p>Windows PE-WDS-Tools umfasst APIs So aktivieren Sie das Image Capture-Tool und multicast Szenarios, in dem einen benutzerdefinierten Windows-Bereitstellungsdienst-Client umfasst. Es muss installiert sein, wenn Sie beabsichtigen, der Windows-Bereitstellungsdienst-Client auf einer benutzerdefinierten Windows PE-Abbild ausgeführt.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Netzwerk/Windows PE-WLAN-Paket</p></td>
<td align="left"><p>Windows PE-WLAN-Paket wird von Windows Recovery Environment (Windows RE) verwendet. Dieses Paket ist in der Datei Basis winre.wim enthalten.</p>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell/Windows PE-PlatformID</p></td>
<td align="left"><p>Windows PE-PlatformID enthält Windows PowerShell-Cmdlets zum Abrufen der Plattformbezeichner des physischen Computers. </p>
<p><strong>Abhängigkeiten</strong>: Installieren von <strong>Windows PE WMI</strong> und <strong>Windows PE-SecureStartup</strong> vor der Installation von <strong>Windows PE-PlatformID</strong>.</p>
<p>Um das Windows PowerShell-Cmdlet verwenden, um die Plattform-ID abrufen, wird <strong>Windows PE-PowerShell</strong> -Paket installieren müssen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PowerShell/Windows PE-PowerShell</p></td>
<td align="left"><p>Windows PE-PowerShell enthält Windows PowerShell-basierten Diagnose mithilfe von Windows-Verwaltungsinstrumentation (WMI) während der Herstellung die Hardware Abfragen zu vereinfachen. Sie können Windows PowerShell-basierte Bereitstellung und Verwaltung Windows PE-basierten erstellen. Zusätzlich zur Bereitstellung können Sie Windows PowerShell für Wiederherstellungsszenarien verwenden. Kunden können in Windows RE starten, und klicken Sie dann Windows PowerShell-Skripts verwenden, um Probleme zu beheben. Kunden können nicht nur die Toolsets, die in Windows PE ausgeführt. In ähnlicher Weise können Sie skriptgesteuerte offlinelösungen zum Wiederherstellen von einigen Computers aus Nein Boot Szenarien erstellen.</p>
<p>Windows PE-PowerShell weist die folgenden bekannten Einschränkungen:</p>
<ul>
<li><p>Windows PowerShell-Remoting wird nicht unterstützt. Alle Cmdlets aufgeführt, die Remoting-Funktionalität aufweisen, gibt einen Fehler zurück.</p></li>
<li><p>Die Windows PowerShell Integrated Scripting Environment (ISE) wird nicht unterstützt.</p></li>
<li><p>Windows PowerShell 2.0 wird nicht unterstützt.</p></li>
</ul>
<p><strong>Abhängigkeiten</strong>: Installieren Sie <strong>Windows PE WMI</strong> &gt; <strong>Windows PE NetFX</strong> &gt; <strong>Windows PE-Skripts</strong> vor der Installation von <strong>Windows PE-PowerShell</strong>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell/Windows PE-DismCmdlets</p></td>
<td align="left"><p>Windows PE-DismCmdlets enthält das DISM PowerShell Modul an, das Cmdlets zum Verwalten und Warten von Windows-Abbildern enthält.</p>
<p>Weitere Informationen finden Sie unter [Windows PowerShell-Cmdlets Bereitstellung Imaging – Wartung Management (DISM)](http://go.microsoft.com/fwlink/p/?linkid=290822).</p>
<p><strong>Abhängigkeiten</strong>: Installieren Sie <strong>Windows PE WMI</strong> &gt; <strong>Windows PE NetFX</strong> &gt; <strong>Windows PE Scripting</strong> &gt; <strong>Windows PE-PowerShell</strong> vor der Installation von <strong>Windows PE-DismCmdlets</strong>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PowerShell/Windows PE-SecureBootCmdlets</p></td>
<td align="left"><p>Windows PE SecureBootCmdlets enthält den PowerShell-Cmdlets zum Verwalten von Umgebungsvariablen UEFI (Unified Extensible Firmware Interface) für das Secure starten.</p>
<p><strong>Abhängigkeiten</strong>: Installieren Sie <strong>Windows PE WMI</strong> &gt; <strong>Windows PE NetFX</strong> &gt; <strong>Windows PE Scripting</strong> &gt; <strong>Windows PE-PowerShell</strong> vor der Installation von <strong>Windows PE-SecureBootCmdlets</strong>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell/Windows PE-StorageWMI</p></td>
<td align="left"><p>Windows PE-StorageWMI enthält PowerShell-Cmdlets für die Speicherverwaltung. Diese Cmdlets verwenden der Windows-Speicher-Management-API (SMAPI) zum Verwalten von lokalen Speichers, wie Datenträger, Partition und Volume-Objekten. Oder diese Cmdlets verwenden, die Windows SMAPI zusammen mit Array Speicherverwaltung mithilfe eines Storage Management. Windows PE-StorageWMI enthält auch Internet SCSI (iSCSI) Initiator-Cmdlets für die Verbindung von einem Hostcomputer oder Server mit virtuellen Festplatten auf externe iSCSI-basierte Speicherarrays über einen Ethernet-Netzwerkadapter oder iSCSI-Host Bus Adapter (HBA).</p>
<p><strong>Abhängigkeiten</strong>: Installieren Sie <strong>Windows PE WMI</strong> &gt; <strong>Windows PE NetFX</strong> &gt; <strong>Windows PE Scripting</strong> &gt; <strong>Windows PE-PowerShell</strong> vor der Installation von <strong>Windows PE-StorageWMI</strong>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Wiederherstellung/Windows PE-Rejuv</p></td>
<td align="left"><p>Windows PE-Rejuv wird von Windows Recovery Environment (Windows RE) verwendet. Dieses Paket ist in der Datei Basis winre.wim enthalten.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Wiederherstellung/Windows PE-SRT</p></td>
<td align="left"><p>Windows PE SRT wird von Windows RE verwendet. Dieses Paket ist in der Datei Basis winre.wim enthalten.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Wiederherstellung/Windows PE-WinReCfg</p></td>
<td align="left"><p>Windows PE WinReCfg enthält das Tool Winrecfg.exe, und es ermöglicht die folgenden Szenarien:</p>
<ul>
<li><p>Starten von X86-basierten Windows PE so konfigurieren Sie Windows RE-Einstellungen auf Schwelle offline X64-basierten Betriebssystem.</p></li>
<li><p>Starten von X64-basierten Windows PE auf ein Bild offline X86-basierten Betriebssystem Windows RE-Einstellungen konfigurieren.</p></li>
</ul>
</tr>
<tr class="odd">
<td align="left"><p>Scripting/Windows PE-Skripts</p></td>
<td align="left"><p>Windows PE-Skript enthält eine mehrsprachige Skripting-Umgebung, ideal für die Automatisierung von System Administration Aufgaben wie Batchverarbeitung-Datei. Skripts, die in der Umgebung Windows Script Host (WSH) ausgeführt können anrufen WSH-Objekte und andere COM-basierte Technologien, die unterstützt Automatisierung WMI, die Windows-Subsysteme zu verwalten, die zentrale Verwaltungsaufgaben für viele System befinden.</p>
<p><strong>Abhängigkeiten</strong>: Install Windows PE Scripting, stellen Sie sicher, die vollständige scripting-Funktionen ist verfügbar, wenn Sie Windows PE NetFX und Windows PE HTA verwenden. Die Installationsreihenfolge ist nicht relevant.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Scripting/Windows PE-WMI</p></td>
<td align="left"><p>Windows PE WMI enthält eine Teilmenge der Anbieter (Windows Management Instrumentation, WMI), die minimale Systemdiagnose zu ermöglichen. WMI ist die Infrastruktur für die von Verwaltungsdaten und Vorgänge auf Windows-Betriebssystemen. Sie können die WMI-Skripts oder Anwendungen zum Automatisieren administrativer Aufgaben auf Remotecomputern schreiben. Darüber hinaus stellt WMI Management Daten an andere Teile des Betriebssystems und Produkte.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Setup/Windows PE-LegacySetup</p></td>
<td align="left"><p>Windows PE-LegacySetup enthält alle Dateien aus dem Ordner \Sources auf Windows Media an. Fügen Sie diese optionale Komponente, wenn Sie Setup oder auf den Ordner \Sources auf die Windows Media-service. Sie müssen diese optionale Komponente zusammen mit die optionale Komponente für das Setup Feature hinzufügen. Um eine neue Datei Boot.wim Mediums hinzuzufügen, fügen Sie das übergeordnete Windows PE-Setup aus, entweder der untergeordneten Elemente (Windows PE-Setup-Client oder Windows PE-Setup-Server) und optional Media-Komponenten. Media Setup ist erforderlich, um die Installation von Windows Server 2008 R2 unterstützt.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Setup/Windows PE-Setup</p></td>
<td align="left"><p>Windows PE-Setup wird das übergeordnete Objekt des Windows PE-Setup-Client und Windows PE-Setup-Server. Sie enthält alle Setupdateien aus dem Ordner \Sources, die auf dem Client und dem Server gemeinsam sind.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Setup/Windows PE-Setup-Client</p></td>
<td align="left"><p>Windows PE-Setup-Client enthält die Client-branding-Dateien für die übergeordnete Windows PE-Setup optionale Komponente.</p>
<p><strong>Abhängigkeiten</strong>: Installieren von <strong>Windows PE-Setup</strong> vor der Installation von <strong>Windows PE-Setup-Client</strong>.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Setup/Windows PE-Setup-Server</p></td>
<td align="left"><p>Windows PE-Setup-Server enthält die Server branding-Dateien für die übergeordnete Windows PE-Setup optionale Komponente.</p>
<p><strong>Abhängigkeiten</strong>: <strong>Windows PE-Setup</strong> vor der Installation von <strong>Windows PE-Setup-Server</strong>zu installieren.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Starten/Windows PE-SecureStartup</p></td>
<td align="left"><p>Windows PE-SecureStartup ermöglicht die Bereitstellung und Verwaltung von BitLocker- und das Modul TPM (Trusted Platform). Sie umfasst BitLocker-Befehlszeilentools, BitLocker WMI Management Bibliotheken, TPM-Treiber, TPM Base Services (TB), <strong>Win32_TPM</strong> -Klasse, die BitLocker-entsperren-Assistenten und BitLocker UI-Bibliotheken. TPM-Treiber bietet eine bessere Unterstützung für BitLocker- und TPM in dieser Umgebung vor dem Start stattfindende.</p>
<p><strong>Abhängigkeiten</strong>: <strong>Windows PE WMI</strong> vor der Installation von <strong>Windows PE-SecureStartup</strong>zu installieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Speicher/Windows PE-EnhancedStorage</p></td>
<td align="left"><p>Windows PE-EnhancedStorage ermöglicht Windows ermitteln können, zusätzliche Funktionalität für Speichergeräten wie verschlüsselte Laufwerke und Implementierungen, die Trusted Computing Group (TCG) und IEEE 1667 zusammengesetzt (&quot;Standardprotokoll für die Authentifizierung in Host Anlagen der vorübergehende Speichergeräten&quot;) Spezifikationen. Diese optionale Komponente ermöglicht Windows diese Speichergeräten systemintern BitLocker mit verwalten.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idwindowsreoptionalcomponentsspanspan-idwindowsreoptionalcomponentsspanspan-idwindowsreoptionalcomponentsspanwindows-re-optional-components"></a><span id="Windows_RE_optional_components"></span><span id="windows_re_optional_components"></span><span id="WINDOWS_RE_OPTIONAL_COMPONENTS"></span>Windows RE optionalen Komponenten


Die standardmäßigen Windows RE-Abbild enthält die folgenden integrierten optionalen Komponenten:

-   Windows PE-EnhancedStorage

-   Windows PE-Rejuv

-   Windows PE für das Skripting

-   Windows PE-SecureStartup

-   Windows PE-Setup

-   Windows PE SRT

-   Windows PE-WDS-Tools

-   Windows PE WMI

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Windows PE: Optimieren der Leistung und das Bild zu reduzieren](winpe-optimize.md)

[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

 

 






