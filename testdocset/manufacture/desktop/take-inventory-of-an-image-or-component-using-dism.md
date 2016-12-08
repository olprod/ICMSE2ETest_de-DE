---
author: Justinha
Description: Bestandsaufnahme eines Bilds oder mithilfe von DISM-Komponente
ms.assetid: cab41da0-3155-4170-8377-b6335de47a38
MSHAttr: PreferredLib:/library/windows/hardware
title: Bestandsaufnahme eines Bilds oder mithilfe von DISM-Komponente
ms.openlocfilehash: aa3beecb7ca8089202e33b4ac2854d2784795b4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="take-inventory-of-an-image-or-component-using-dism"></a>Bestandsaufnahme eines Bilds oder mithilfe von DISM-Komponente


Sie können eine Inventur der Bestimmung der Treiber, Pakete, übernehmen und andere Dateien und Einstellungen sind in einem Windows-Abbild enthalten. Verwenden Sie hierzu Deployment Image Servicing and Management (DISM) – Wartung Befehle aus.

Sie müssen ein offline-Abbild aus einer WIM oder VHD-Datei bereitstellen, bevor Sie Inventur der oder Dienst ein bestimmtes Windows-Abbild nutzen können. Weitere Informationen finden Sie unter [Mount und eine DISM mithilfe eines Windows Bild ändern](mount-and-modify-a-windows-image-using-dism.md).

In diesem Abschnitt:

[Abrufen von Informationen für Windows-Bild](#getwiminformatio)

[Abrufen von Informationen mit Windows PE](#getwindowspeinformation)

[Abrufen von Treiberinformationen](#getdriverinformation)

[Get-Pakets und Featureinformationen](#getpackageinformation)

[Abrufen von App-Paket (.appx) – Wartung Informationen](#getapppackage)

[Abrufen von internationalen Einstellungen und Sprachen](#getinternationalsettingslang)

[Abrufen von Informationen für Windows-Edition](#getwindowseditioninformation)

[Lesen von Anwendungsinformationen Patch](#getapplicationinformation)

## <a name="span-idgetwiminformatiospanspan-idgetwiminformatiospanspan-idgetwiminformatiospanget-windows-image-information"></a><span id="GetWIMInformatio"></span><span id="getwiminformatio"></span><span id="GETWIMINFORMATIO"></span>Abrufen von Informationen für Windows-Bild


Bild-Befehlen können Sie die Informationen zu einem bestimmten Windows-Abbild in einer WIM-Datei oder virtual Hard Disk (VHD)-Datei, zu der Bilder in einer bestimmten WIM oder VHD-Datei, und bereitgestellten WIM- oder VHD-Dateien aufgelistet. Diese Informationen helfen Ihnen Mount-Speicherorte zu identifizieren, image-Namen oder Überprüfen Sie die Architektur des Bilds, das Sie bereitstellen werden.

Sie können Informationen über alle Bilder in einer WIM- oder VHD-Datei mithilfe der **/Get-ImageInfo** – Wartung Befehl DISM sammeln. Sie können auch Informationen zu einem bestimmten Abbild in einer WIM- oder VHD-Datei wie Betriebssystem, Architektur und Einstellungen, durch Angeben der Name oder die Indexnummer des Bilds sammeln. Um das Bild in eine VHD-Datei angeben, müssen **Sie/Index: 1** verwenden.

Sie können die Bilder, die derzeit bereitgestellten identifizieren, auf dem Computer, und können Sie Informationen zu den bereitgestellten Abbild wie Lese-/Schreibberechtigungen, Bereitstellungsort, Pfad der bereitgestellten Datei und Index des bereitgestellten Abbilds mithilfe der **/Get-MountedImageInfo** – Wartung Befehl Liste.

Weitere Informationen zu verfügbaren DISM Bild Befehlen finden Sie unter [DISM - Deployment Image Servicing und technische Referenz für Windows Verwaltung](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

**An Liste Bilder, die in einer WIM- oder VHD-Datei enthalten sind**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Um Informationen zu alle Bilder in einer WIM- oder VHD-Datei, an der Eingabeaufforderung mit erhöhten Rechten Typ aufzulisten:

    ``` syntax
    Dism /Get-ImageInfo /imagefile:C:\test\images\install.wim
    ```

    Bei Verwendung mit **der/Index** oder **Name** Optionen, ausführlichere Informationen zu wird das angegebene Bild angezeigt. Um das Bild in eine VHD-Datei anzugeben, verwenden Sie `/Index:1`.

Der generierte Bericht enthält die folgenden Informationen.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Index</p></td>
<td align="left"><p>Der Indexwert des Bilds in der WIM- oder VHD-Datei.</p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="even">
<td align="left"><p>Name</p></td>
<td align="left"><p>Der Windows-Edition-Name des Bilds in der WIM- oder VHD-Datei.</p></td>
<td align="left"><p>Windows 8 Pro</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Beschreibung</p></td>
<td align="left"><p>Die Beschreibung des Bilds in der WIM- oder VHD-Datei.</p></td>
<td align="left"><p>Windows 8 Pro</p></td>
</tr>
<tr class="even">
<td align="left"><p>Größe</p></td>
<td align="left"><p>Die Größe des Bilds.</p></td>
<td align="left"><p>8,045,951,502 bytes</p></td>
</tr>
</tbody>
</table>

 

**So Listen Sie bereitgestellte Abbilder**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Geben Sie an der Eingabeaufforderung mit erhöhten Rechten:

    ``` syntax
    Dism /Get-MountedImageInfo 
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Mount-Dir</p></td>
<td align="left"><p>Der Speicherort, in dem das Abbild bereitgestellt wird.</p></td>
<td align="left"><p><strong>C:\Test\Mount</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Bilddatei</p></td>
<td align="left"><p>Der vollständige Pfad zur WIM- oder VHD-Datei.</p></td>
<td align="left"><p><strong>C:\Test\Images\install.wim</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bildindex</p></td>
<td align="left"><p>Die Indexnummer des bereitgestellten Abbilds, das in WIM oder VHD-Datei eingeschlossen wird.</p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="even">
<td align="left"><p>Eingebundene Lese-/Schreibzugriff</p></td>
<td align="left"><p><strong>Ja,</strong> , wenn das bereitgestellte Abbild für Lese- und Schreibzugriff oder <strong>No</strong> zulässt, wenn das bereitgestellte Abbild nur schreibgeschützten Zugriff zulässt.</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Status</p></td>
<td align="left"><p>Der Bereitstellungsstatus des Bilds. Die folgenden: möglichen Werte</p>
<p><strong>Okay.</strong> Das Bild wird bereitgestellt. Keine Probleme vorliegen.</p>
<p><strong>Erneute Bereitstellung erforderlich.</strong> Das Bild muss bereitgestellt werden. Dies kann durch einen Neustart das Hostsystem, wenn das Abbild bereitgestellt ist, verursacht werden.</p>
<p><strong>Ungültig. </strong>: das Bild wird in einem ungültigen Zustand. Möglicherweise müssen Sie auf das Bild <strong>/Cleanup-Mountpoints</strong> verwenden.</p></td>
<td align="left"><p>OK</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetwindowspeinformationspanspan-idgetwindowspeinformationspanspan-idgetwindowspeinformationspanget-windows-pe-information"></a><span id="GetWindowsPEInformation"></span><span id="getwindowspeinformation"></span><span id="GETWINDOWSPEINFORMATION"></span>Abrufen von Informationen mit Windows PE


Sie können ein Bild Windows Vorinstallation Environment (Windows PE) zur Wartung auf die gleiche Weise wie, die Sie alle Windows-Abbild würden bereitstellen. Es bestehen auch Windows PE-Befehle, die speziell für ein Windows PE-Abbild Wartung. Diese Befehle können auf Einstellungen für die Liste Windows PE wie Onlinetreiberinstallation, Zielpfad und Profilinformationen verwendet werden. Weitere Informationen zu Windows PE zum Warten Befehle in DISM finden Sie unter [DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md).

**So Listen Sie alle Einstellungen im bereitgestellten Windows PE-Abbild.**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Um Informationen zu alle für die Windows PE im bereitgestellten Windows PE-Abbild, an der Eingabeaufforderung mit erhöhten Rechten Typ aufzulisten:

    ``` syntax
    Dism /image:C:\test\offline /Get-PESettings
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Profil</p></td>
<td align="left"><p>Meldet, ob Windows PE Profil aktiviert oder deaktiviert ist.</p></td>
<td align="left"><p>Deaktiviert</p></td>
</tr>
<tr class="even">
<td align="left"><p>Scratch-Speicher</p></td>
<td align="left"><p>Der Betrag beschreibbaren verfügbaren Speicherplatz auf dem Systemdatenträger Windows PE, wenn im Ramdisk-Modus gestartet.</p></td>
<td align="left"><p>32MB</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Zielpfad</p></td>
<td align="left"><p>Der Pfad zum Stammverzeichnis des Windows PE-Abbild beim Starten.</p></td>
<td align="left"><p>X:\</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetdriverinformationspanspan-idgetdriverinformationspanspan-idgetdriverinformationspanget-driver-information"></a><span id="GetDriverInformation"></span><span id="getdriverinformation"></span><span id="GETDRIVERINFORMATION"></span>Abrufen von Treiberinformationen


Die Befehle zum Warten von Treiber können zum Aufzählen der Treiberpakete im Driver Store basierend auf deren INF-Dateien verwendet werden. **Die/Get** -Befehle können Sie grundlegende Informationen zu Drittanbieter-Treiberpakete oder alle Treiberpakete im Offlinemodus Bild anzeigen. Wenn Sie ein offline-Abbild oder einem ausgeführten Betriebssystem zeigen, können Sie bestimmen, welche Treiberpakete werden im Bild und Abrufen von Informationen zu den Treiber.

Sie können Anzeigen detaillierter Informationen zu einer bestimmten installierten INF-Datei oder eine, die noch nicht installiert ist. Die installierten Treiber im Driver Store werden Oem0.inf, Oem1.inf usw. heißen.

Weitere Informationen zu verfügbaren DISM Treiber – Wartung Befehlen finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-driver-servicing-command-line-options-s14.md).

**So Listen Sie Treiberpakete in die offline-Abbild**

1.  Klicken Sie auf **Start**, und geben Sie **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Verwenden Sie eine der folgenden Befehle, um die Listeninformationen zu allen Treiber Pakete in einem bereitgestellten offline Windows-Abbild:

    ``` syntax
    Dism /image:C:\test\offline /Get-Drivers
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Drivers /all
    ```

    Geben Sie für ein ausgeführtes Betriebssystem einen der folgenden Befehle ein:

    ``` syntax
    Dism /online /Get-Drivers
    ```

    ``` syntax
    Dism /online /Get-Drivers /all
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Veröffentlichte Name</p></td>
<td align="left"><p>Der Name des Treiberpakets nach Driver Store hinzugefügt wird.</p></td>
<td align="left"><p>Oem0.inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>Ursprünglicher Dateiname</p></td>
<td align="left"><p>Der ursprüngliche INF-Dateiname des Treiberpakets wird.</p></td>
<td align="left"><p>Toaster.inf</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Inbox</p></td>
<td align="left"><p><strong>Ja</strong> für einen Standardtreiber (Posteingang Treiber) oder auf <strong>Nein</strong> für Drittanbieter-Treiberpakete.</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Klassenname</p></td>
<td align="left"><p>Der Anzeigenamen der Geräteklasse der Treiber gehört.</p></td>
<td align="left"><p>Printer</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Name des Anbieters</p></td>
<td align="left"><p>Der Anbieter oder die digitale Signatur für das Paket.</p></td>
<td align="left"><p>Microsoft</p></td>
</tr>
<tr class="even">
<td align="left"><p>Date</p></td>
<td align="left"><p>Das Datum der Treiber zugeordnet ist, wie er in der INF-Datei angegeben wird. Das Datum wird für Ihr Gebietsschema entsprechend formatiert werden.</p></td>
<td align="left"><p>10/31/2006</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>Die Versionsnummer, die in der INF-Richtlinie angegeben ist.</p></td>
<td align="left"><p>6.1.6801.0</p></td>
</tr>
</tbody>
</table>

 

**So rufen Sie Informationen zu einem bestimmten Treiber**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen zu einem bestimmten Treiberpaket im Windows-Abbild offline aufgelistet. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-DriverInfo /driver:oem1.inf
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird Folgendes ein:

    ``` syntax
    Dism /online /Get-DriverInfo /driver:oem1.inf
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Veröffentlichte Name</p></td>
<td align="left"><p>Der Name des Treiberpakets nach Driver Store hinzugefügt wird.</p></td>
<td align="left"><p>Oem0.inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>Pfad-Treiber Store</p></td>
<td align="left"><p>Der Pfad zum Speicherort Treiber. Wenn der Treiber installiert ist, wird der Pfad zu den Treiberspeicher aufgeführt. Wenn der Treiber noch nicht installiert ist, wird der Pfad zu der Treiber auf dem Host Wartung aufgeführt.</p></td>
<td align="left"><p><strong>E:\Images\Mount_depset\Windows\System32\DriverStore\FileRepository\Fasttx2k.inf_x86_neutral_0328f62e\Fasttx2k.inf</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Klassenname</p></td>
<td align="left"><p>Der Anzeigenamen der Geräteklasse der Treiber gehört.</p></td>
<td align="left"><p>Printer</p></td>
</tr>
<tr class="even">
<td align="left"><p>Beschreibung der Klasse</p></td>
<td align="left"><p>Die Beschreibung der Geräteklasse der Treiber gehört.</p></td>
<td align="left"><p>Drucker</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Die Klassen-GUID</p></td>
<td align="left"><p>Die GUID der Geräteklasse, der der Treiber ein Mitglied ist.</p></td>
<td align="left"><p><strong>{4D36E97B-E325-11CE-BFC1-08002BE10318}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Date</p></td>
<td align="left"><p>Das Datum der Treiber zugeordnet, wie er in der INF-Datei angegeben wird. Das Datum wird entsprechend für Ihr Gebietsschema formatiert werden.</p></td>
<td align="left"><p>8/6/2003</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>Die Treiberversionsnummer, die in der INF-Richtlinie angegeben ist.</p></td>
<td align="left"><p>1.0.1.37</p></td>
</tr>
<tr class="even">
<td align="left"><p>Start erforderlich</p></td>
<td align="left"><p><strong>Ja,</strong> ist der Treiber Boot kritischen oder auf <strong>Nein,</strong> Falls noch nicht.</p></td>
<td align="left"><p><strong>Nein</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Treiber für Architektur</p></td>
<td align="left"><p>Die Architektur des Bilds an, die auf dem er installiert ist. Wenn der Treiber noch nicht installiert ist, wird das Feld wiederholt für jede unterstützte Betriebssystemarchitektur gemeldet.</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="even">
<td align="left"><p>Hersteller</p></td>
<td align="left"><p>Der Hersteller des unterstützten Geräts.</p></td>
<td align="left"><p>AdventureWorks</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Beschreibung</p></td>
<td align="left"><p>Eine Beschreibung des unterstützten Geräts.</p></td>
<td align="left"><p><strong>Windows XP Adventure Works 376 Domänencontroller</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Architektur</p></td>
<td align="left"><p>Die Architektur des Treibers.</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hardware-ID</p></td>
<td align="left"><p>Die Hardware-ID des unterstützten Geräts.</p></td>
<td align="left"><p><strong>ABC_3376</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Dienstname</p></td>
<td align="left"><p>Der Dienstname des Treibers.</p></td>
<td align="left"><p><strong>C1232k</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Kompatible IDs</p></td>
<td align="left"><p>Alternative Plug & Play (Plug & Play-) IDs für das Gerät, wenn eine zutrifft.</p></td>
<td align="left"><p><strong>* 12ABC</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Ausschluss-IDs</p></td>
<td align="left"><p>Plug & Play-IDs, die nicht mit das Gerät eine trifft zu übereinstimmt.</p></td>
<td align="left"><p><strong>* A_123</strong></p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
Wenn Sie einen Treiber, die noch nicht installiert ist zeigen, wird der Bericht etwas unterschiedlich sein.

 

## <a name="span-idgetpackageinformationspanspan-idgetpackageinformationspanspan-idgetpackageinformationspanget-package-and-feature-information"></a><span id="GetPackageInformation"></span><span id="getpackageinformation"></span><span id="GETPACKAGEINFORMATION"></span>Get-Pakets und Featureinformationen


Betriebssystem zum Warten von Paketen Befehlen können Sie Informationen zum Windows-Pakete abzurufen. DISM und Befehle zum Warten von Paketen können auch Informationen zum Windows-Features, offline oder für eine ausgeführte Windows-Installation abzurufen.

Die **Option/PackagePath** können Sie angeben einer CAB-Datei oder einen Ordner, in dem die CAB-Datei extrahiert werden. Sie können diesen Befehl um Paketinformationen für MSU-Dateien zu erhalten. Alternativ können **Sie/Get-Packages** zum Suchen des Namens eines Pakets verwenden und verwenden Sie dann den Namen des Pakets **angeben/PackageName** .

Sie können ausführliche Informationen zu einem Feature anzeigen. Sie müssen die **Option/FeatureName** mit dem **Befehl/Get** verwenden. Verwenden Sie die **Option/Get-Features** , um den Namen des Features im Bild zu suchen. Komponentennamen Groß-/Kleinschreibung Wenn Sie ein Windows-Abbild als Windows 8 bedienen.

Finden Sie weitere Informationen zum Betriebssystem-Paket-Befehle zum Warten in DISM verfügbaren [DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md).

**So Listen Sie alle Pakete des Abbilds**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen zu allen im Windows-Abbild offline-Pakete aufgelistet, geben Sie den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-Packages
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-Packages
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Paketidentität</p></td>
<td align="left"><p>Der Name des Pakets gemäß Angabe im Bild wird angezeigt.</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Bundesland</p></td>
<td align="left"><p>Der aktuelle Status des Pakets. Als:</p>
<p><strong>Installiert.</strong> Das Paket wird installiert.</p>
<p><strong>Installation steht.</strong> Das Paket wird installiert, jedoch ist ein Neustart für die Durchführung die ausstehenden online Aktionen erforderlich.</p>
<p><strong>Bereitgestellt.</strong> Das Paket ist für die Installation bereitgestellt.</p></td>
<td align="left"><p><strong>Installiert</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Versionstyp</p></td>
<td align="left"><p>Der Typ des Pakets. Als:</p>
<p><strong>Feature Pack.</strong> Ein Feature des Windows-Betriebssystem.</p>
<p><strong>Sprachpaket.</strong> Ein Sprachpaket für Windows-Betriebssystem oder Language Interface Pack (LIP).</p>
<p><strong>Foundation.</strong> Zentrale Betriebssystemkomponenten einschließlich optionaler Features.</p></td>
<td align="left"><p>Feature Pack</p></td>
</tr>
<tr class="even">
<td align="left"><p>Installieren Sie</p></td>
<td align="left"><p>UTC-Datum und Uhrzeit, wann die Installation erfolgt ist. Wenn das Paket noch nicht installiert ist, wird das Installieren von Time-Feld leer.</p></td>
<td align="left"><p>8/18/2008 7:58:00 UHR</p></td>
</tr>
</tbody>
</table>

 

**So führen Sie Informationen zu einem bestimmten Paket**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen zu einem bestimmten Paket im Offlinemodus Windows-Abbild, geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-PackageInfo /PackagePath:C:\packages\package.cab
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    Geben Sie für ein ausgeführtes Betriebssystem einen der folgenden Befehle ein:

    ``` syntax
    Dism /online /Get-PackageInfo /PackagePath:C:\packages\package.cab
    ```

    ``` syntax
    Dism /online /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Paketidentität</p></td>
<td align="left"><p>Der Name des Pakets gemäß Angabe im Bild wird angezeigt.</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Zutreffend</p></td>
<td align="left"><p>Gibt an, wenn das Paket auf das Bild angewendet wird.</p></td>
<td align="left"><p><strong>Nein</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Copyright</p></td>
<td align="left"><p>Copyright-Informationen für das Paket.</p></td>
<td align="left"><p>Copyright © Microsoft Corporation. Alle Rechte vorbehalten.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Firma</p></td>
<td align="left"><p>Das Unternehmen, das das Paket bereitgestellt, sofern verfügbar.</p></td>
<td align="left"><p>Microsoft Corporation</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Zeitpunkt der Erstellung</p></td>
<td align="left"><p>Datum und Uhrzeit der Erstellung des Pakets, sofern verfügbar.</p></td>
<td align="left"><p>8/18/2008 7:58:00 UHR</p></td>
</tr>
<tr class="even">
<td align="left"><p>Beschreibung</p></td>
<td align="left"><p>Eine kurze Beschreibung des Pakets.</p></td>
<td align="left"><p>Fehlerbehebung für KB300106</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Client installieren</p></td>
<td align="left"><p>Der Clienttool, das die Installation des Pakets.</p></td>
<td align="left"><p>DISM Paket-Manager-Anbieter</p></td>
</tr>
<tr class="even">
<td align="left"><p>Installieren Sie Paketname</p></td>
<td align="left"><p>Der Name des installierten MUM-Datei.</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0.mum</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Installieren Sie</p></td>
<td align="left"><p>Das Datum und die Zeit, die das Paket installiert wurde. Wenn das Paket noch nicht installiert ist, wird das <strong>Installieren von Time</strong> -Feld leer.</p></td>
<td align="left"><p>8/18/2008 7:58:00 UHR</p></td>
</tr>
<tr class="even">
<td align="left"><p>Zuletzt aktualisiert</p></td>
<td align="left"><p>Das Datum, die das Paket, das sofern verfügbar Aktualisierungszeitpunkt an.</p></td>
<td align="left"><p>8/18/2008 7:58:00 UHR</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Name</p></td>
<td align="left"><p>Der Anzeigename des Pakets, lokalisiert, sofern verfügbar.</p>
<p>Im allgemeinen &quot;Standard&quot; für alle Pakete zum Warten angezeigt wird.</p></td>
<td align="left"><p>ActiveX®-Installationsdienst</p></td>
</tr>
<tr class="even">
<td align="left"><p>Produktname</p></td>
<td align="left"><p>Der Name des Produkts, die das Paket gehört, sofern verfügbar.</p></td>
<td align="left"><p><strong>Microsoft Windows-NetFx3-OC-Paket</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Version des Produkts</p></td>
<td align="left"><p>Die Version des Produkts, die das Paket gehört, sofern verfügbar.</p></td>
<td align="left"><p>123.01.0000</p></td>
</tr>
<tr class="even">
<td align="left"><p>Freigabe</p></td>
<td align="left"><p>Der Typ des Pakets. Als:</p>
<p><strong>Feature Pack.</strong> Ein Feature des Windows-Betriebssystem.</p>
<p><strong>Sprachpaket.</strong> Ein Sprachpaket für Windows-Betriebssystem oder Language Interface Pack (LIP).</p>
<p><strong>Foundation.</strong> Zentrale Betriebssystemkomponenten einschließlich optionaler Features.</p></td>
<td align="left"><p>Feature Pack</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Neustart erforderlich</p></td>
<td align="left"><p>Gibt an, ob ein Neustart erforderlich ist, bei der Installation oder Deinstallation des Pakets online.</p></td>
<td align="left"><p>Mögliche</p></td>
</tr>
<tr class="even">
<td align="left"><p>Supportinformationen</p></td>
<td align="left"><p>Informationsquellen für Support, sofern verfügbar.</p></td>
<td align="left"><p>http://support.Microsoft.com/?kbid=300106</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bundesland</p></td>
<td align="left"><p>Gibt an, ob das Paket in das Betriebssystem installiert ist. Die folgenden: möglichen Werte</p>
<p><strong>Nicht vorhanden.</strong> Das Paket wird nicht installiert.</p>
<p><strong>Installiert.</strong> Das Paket wird installiert.</p>
<p><strong>Installation steht.</strong> Das Paket installiert werden, jedoch ist ein Neustart zum Abschließen ausstehender online Aktionen erforderlich.</p>
<p><strong>Bereitgestellt.</strong> Das Paket wird für die Installation bereitgestellt.</p></td>
<td align="left"><p>Installiert</p></td>
</tr>
<tr class="even">
<td align="left"><p>Vollständig offline werden können</p></td>
<td align="left"><p><strong>Ja.</strong> Das Paket kann offline installiert werden, ohne das Abbild zu starten.</p>
<p><strong>Nein.</strong> Sie müssen in das Bild starten, um die Installation dieses Pakets abzuschließen.</p>
<p><strong>Nicht festgelegt.</strong> Möglicherweise müssen Sie die Installation dieses Pakets in das Bild, um die vollständige zu starten. Viele Pakete können offline vollständig installiert werden. Wenn Sie versuchen, ein Paket offline zu installieren und ein Neustart erforderlich ist, wird sie in der Protokolldatei gemeldet. Sie können den Status eines Pakets mit dem Befehl Get-PackageInfo überprüfen.</p>
<p>Dieses Feld gilt nur für Windows 8, Windows Server® 2012 und Windows-Vorinstallation Environment (Windows PE) 4.0 Ziel Bildern.</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Benutzerdefinierte Eigenschaften</p></td>
<td align="left"><p>Eine Liste der benutzerdefinierten Eigenschaften in der Manifestdatei des Pakets definiert. Wenn keine benutzerdefinierten Eigenschaften vorhanden sind, werden (keine benutzerdefinierten Eigenschaften gefunden) angezeigt.</p></td>
<td align="left"><p>Abhängigkeit: Language Pack</p></td>
</tr>
<tr class="even">
<td align="left"><p>Features für das Paket auflisten</p></td>
<td align="left"><p>Eine Liste der Features, in dem Paket.</p>
<p>Wenn kein Feature im Paket vorhanden ist, wird die Paketidentität gefolgt von (keine Features für dieses Paket gefunden) angezeigt.</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0 (keine Features für dieses Paket gefunden)</strong></p></td>
</tr>
</tbody>
</table>

 

**So Listen Sie alle Features im Bild**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen zu den Features im Offlinemodus Windows-Abbild, geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-Features
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Features /PackagePath:C:\packages\package.cab
    ```

    Geben Sie für ein ausgeführtes Betriebssystem einen der folgenden Befehle ein:

    ``` syntax
    Dism /online /Get-Features
    ```

    ``` syntax
    Dism /online /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    ``` syntax
    Dism /online /Get-Features /PackagePath:C:\packages\package.cab
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Featurename</p></td>
<td align="left"><p>Der Name des Features gemäß Angabe im Bild wird angezeigt.</p></td>
<td align="left"><p><strong>Windows enthaltene Spiele</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Bundesland</p></td>
<td align="left"><p>Der aktuelle Status des Features. Die folgenden: möglichen Werte</p>
<ul>
<li><p><strong>Aktiviert.</strong> Das Feature aktiviert ist.</p></li>
<li><p><strong>Deaktiviert.</strong> Das Feature ist deaktiviert.</p></li>
<li><p><strong>Ausstehende zu aktivieren.</strong> Das Feature ist aktiviert, jedoch ist ein Neustart zum Abschließen ausstehender online Aktionen erforderlich.</p></li>
<li><p><strong>Deaktivierung steht aus.</strong> Das Feature erfordert einen Neustart zum Abschließen ausstehender online Aktionen jedoch deaktiviert sein.</p></li>
<li><p><strong>Entfernt Nutzlast deaktiviert.</strong> Das Feature ist deaktiviert, und der Nutzlast wurde entfernt. Nur die Paket-Metadaten ist im Bild vorhanden. Nutzlast wiederhergestellt werden kann und das Feature kann bei Bedarf aktiviert werden, nachdem das Bild bereitgestellt wird. Weitere Informationen zu Features bei Bedarf finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md).</p></li>
</ul></td>
<td align="left"><p><strong>Deaktiviert</strong></p></td>
</tr>
</tbody>
</table>

 

**So führen Sie Informationen über ein bestimmtes feature**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen über ein bestimmtes Feature im Offlinemodus Windows-Abbild, geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-FeatureInfo /FeatureName:LocalPack-GB /PackageName:Microsoft-Windows-LocalPack-GB-Package~6595b6144ccf1df~x86~~1.0.0.0
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:Hearts 
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Featurename</p></td>
<td align="left"><p>Name des Features.</p></td>
<td align="left"><p><strong>Windows enthaltene Spiele</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Anzeigename</p></td>
<td align="left"><p>Der Name des Features gemäß Angabe in der Benutzeroberfläche angezeigt wird.</p></td>
<td align="left"><p><strong>Spiele</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Beschreibung</p></td>
<td align="left"><p>Eine kurze Beschreibung des Features.</p></td>
<td align="left"><p>Standardmäßig enthaltene Spiele.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Neustart erforderlich</p></td>
<td align="left"><p>Gibt an, ob ein Neustart erforderlich ist, wenn Sie aktivieren oder Deaktivieren dieses Feature.</p></td>
<td align="left"><p><strong>Ja</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bundesland</p></td>
<td align="left"><p>Der aktuelle Status des Features. Die folgenden: möglichen Werte</p>
<p><strong>Aktiviert.</strong> Das Feature aktiviert ist.</p>
<p><strong>Deaktiviert.</strong> Das Feature ist deaktiviert.</p>
<p><strong>Aktivierung steht aus.</strong> Das Feature ist aktiviert, jedoch ist ein Neustart zum Abschließen ausstehender online Aktionen erforderlich.</p>
<p><strong>Deaktivierung steht aus.</strong> Das Feature erfordert einen Neustart zum Abschließen ausstehender online Aktionen jedoch deaktiviert sein.</p>
<p><strong>Deaktivierte mit Nutzlast entfernt.</strong> Das Feature ist deaktiviert, und seine Nutzlast wurde entfernt. Nur die Paket-Metadaten ist im Bild vorhanden. Nutzlast wiederhergestellt werden kann und das Feature kann bei Bedarf aktiviert werden, nachdem das Bild bereitgestellt wird. Weitere Informationen zu Features bei Bedarf finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](configure-a-windows-repair-source.md).</p></td>
<td align="left"><p><strong>Deaktiviert</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Benutzerdefinierte Eigenschaften</p></td>
<td align="left"><p>Eine Liste der benutzerdefinierten Eigenschaften in der Manifestdatei des Pakets definiert. Wenn keine benutzerdefinierten Eigenschaften vorhanden sind, werden (keine benutzerdefinierten Eigenschaften gefunden) angezeigt.</p></td>
<td align="left"><p>Abhängigkeit: Language Pack</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetapppackagespanspan-idgetapppackagespanspan-idgetapppackagespanget-app-package-appx-servicing-information"></a><span id="GetAppPackage"></span><span id="getapppackage"></span><span id="GETAPPPACKAGE"></span>Abrufen von App-Paket (.appx) – Wartung Informationen


Sie können das app-Paket (.appx) – Wartung Befehle verwenden, um die bereitgestellte apps in einem Windows-Abbild aufzulisten. Bereitgestellte apps werden für jede Benutzerprofil registriert werden, die für die Windows-Abbild erstellt wird.

Weitere Informationen zum app-Paket – Wartung DISM verfügbaren Befehlen finden Sie unter [DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md).

**So Listen Sie bereitgestellte apps im Windows-Abbild**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Um bereitgestellte apps in einer bereitgestellten offline Windows-Abbild aufzulisten, geben Sie Folgendes ein:

    ``` syntax
    Dism /image:c:\test\offline /Get-ProvisionedAppxPackages
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird Folgendes ein:

    ``` syntax
    Dism /online /Get-ProvisionedAppxPackages
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DisplayName</p></td>
<td align="left"><p>Der Name der app.</p></td>
<td align="left"><p>Fabrikam.Sample.CS</p></td>
</tr>
<tr class="even">
<td align="left"><p>Version</p></td>
<td align="left"><p>Die Versionsnummer des app-Pakets.</p></td>
<td align="left"><p>1.0.0.0</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Architektur</p></td>
<td align="left"><p>Die Architektur der app.</p></td>
<td align="left"><p>neutral</p></td>
</tr>
<tr class="even">
<td align="left"><p>ResourceID</p></td>
<td align="left"><p>Weitere Informationen finden Sie unter [App Packen Glossary](http://go.microsoft.com/fwlink/p/?linkid=252145).</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Paketname</p></td>
<td align="left"><p>Der vollständige Name des app-Pakets.</p></td>
<td align="left"><p>Fabrikam.Sample.CS_1.0.0.0_neutral_s9y1p3hwd5qda</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetinternationalsettingslangspanspan-idgetinternationalsettingslangspanspan-idgetinternationalsettingslangspanget-international-settings-and-languages"></a><span id="GetInternationalSettingsLang"></span><span id="getinternationalsettingslang"></span><span id="GETINTERNATIONALSETTINGSLANG"></span>Abrufen von internationalen Einstellungen und Sprachen


Die internationale Wartung Befehle können zum vorhandene internationale Einstellungen in Windows und Windows PE Bilder Abfragen verwendet werden. Weitere Informationen zum Betriebssystem Befehle zum Warten von Paketen in DISM, verfügbaren finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

**Wichtige**  
Internationale Wartung Befehle kann nicht auf einem Windows Vista oder Windows Server 2008-Abbild verwendet werden.

 

Verwenden Sie die Option **/ online** zum Anzeigen von Informationen zu den internationalen Einstellungen und Sprachen im Betriebssystem ausgeführt wird. Verwendung **/image:** &lt; *Pfad\_auf\_offline\_Bild\_Verzeichnis* &gt; zum Anzeigen von Informationen zu internationalen Einstellungen und Sprachen im Offlinemodus Bild. Bei Verwendung mit den **Optionen/Image** und **/distribution** werden Informationen zu den internationalen Einstellungen und Sprachen in der Verteilung angezeigt.

**So Listen Sie alle internationalen Einstellungen und Sprachen**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen zu allen internationalen Einstellungen im Offlinemodus Windows-Abbild, geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-Intl
    ```

    ``` syntax
    Dism /image:C:\test\offline /distribution:C:\windows_distribution\langpacks /Get-Intl
    ```

    Geben Sie für ein ausgeführtes Betriebssystem den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-Intl
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Standardsystem Benutzeroberflächensprache</p></td>
<td align="left"><p>Die Sprache, die derzeit als Standardsystem-Benutzeroberflächensprache festgelegt ist.</p></td>
<td align="left"><p><strong>En-US</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Standardgebietsschema des Systems</p></td>
<td align="left"><p>Die Sprache für nicht-Unicode-Programme (auch als Systemgebietsschema bezeichnet) sowie Schriftart.</p></td>
<td align="left"><p><strong>En-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Standard-Zeitzone</p></td>
<td align="left"><p>Die Zeitzone, die derzeit als Standard festgelegt wird.</p></td>
<td align="left"><p>Pazifik Normalzeit</p></td>
</tr>
<tr class="even">
<td align="left"><p>Benutzergebietsschema für Standardbenutzer</p></td>
<td align="left"><p>Die &quot;Standards und Formate&quot; Sprache (auch als Gebietsschema des Benutzers bezeichnet), die für den Standardbenutzer festgelegt ist.</p></td>
<td align="left"><p><strong>En-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Location</p></td>
<td align="left"><p>Der geografische Standort, die derzeit für das Betriebssystem festgelegt ist. Weitere Informationen zu geografischen Standorten finden Sie unter [Tabelle geografischen Standorten](http://go.microsoft.com/fwlink/?LinkId=131360).</p></td>
<td align="left"><p>USA</p></td>
</tr>
<tr class="even">
<td align="left"><p>Active-Tastaturen</p></td>
<td align="left"><p>Die Wert-Paar für die aktive Tastatur. Im Beispiel bereitgestellt 0409 ist die Sprachen-ID und 00000409 ist der Tastatur-Bezeichner.</p></td>
<td align="left"><p><strong>: 0409: 00000409</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Standardtastaturen</p></td>
<td align="left"><p>Die Wert-Paar für die Standardtastatur. Im Beispiel bereitgestellt 0409 ist die Sprachen-ID und 00000409 ist der Tastatur-Bezeichner.</p></td>
<td align="left"><p><strong>: 0409: 00000409</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Installierte Sprache(n)</p></td>
<td align="left"><p>Eine Liste mit allen installierten Language Packs.</p></td>
<td align="left"><p><strong>En-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Typ</p></td>
<td align="left"><p>Der Typ der einzelnen Language Pack installiert. Weitere Informationen finden Sie unter [Hinzufügen von Language Packs auf Windows](add-language-packs-to-windows.md).</p></td>
<td align="left"><p><strong>En-US</strong></p>
<p>Typ: Vollständig lokalisierte Sprache</p>
<p><strong></strong>Ar-SA</p>
<p>Typ: Teilweise lokalisierte Sprache, MUI-Typ</p>
<p>Fallback Sprachen <strong>En-US</strong>, <strong>fr-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Verteilung Sprachen</p></td>
<td align="left"><p>Eine Liste der Sprachen, die in der Verteilung Freigabe verfügbar sind.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Diese Liste enthält den Namen des Ordners in der Freigabe der Verteilung. Die Sprache der tatsächlichen LP.cab-Datei im Ordner wird nicht überprüft. Beispielsweise ist der Pfad für die Verteilung... \Langpacks\bg-BG\Lp.cab, wird der Wert der bg-BG als die Sprache, in die Verteilung Freigabe gemeldet, auch wenn die LP.cab-Datei nicht die richtigen CAB-Datei für bg-BG ist.</p>
</div>
<div>
 
</div></td>
<td align="left"><p>Die Standardsprache in die Verteilung ist: <strong>ja-JP</strong></p>
<p>Die verfügbaren Sprachen in der Verteilung sind: <strong>bg-BG</strong>, <strong>nl-NL</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bedeutung der mehrstufigen Keyboard-Treiber</p></td>
<td align="left"><p>Eine Liste der Tastaturtreiber für japanische oder koreanische Tastaturen, falls installiert sind.</p></td>
<td align="left"><p>Japanische Tastatur (106/109 Tasten)</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetwindowseditioninformationspanspan-idgetwindowseditioninformationspanspan-idgetwindowseditioninformationspanget-windows-edition-information"></a><span id="GetWindowsEditionInformation"></span><span id="getwindowseditioninformation"></span><span id="GETWINDOWSEDITIONINFORMATION"></span>Abrufen von Informationen zu Windows Edition


Die Befehle zum Warten von Edition können Sie um Informationen zu erhalten, welche Editionen von Windows für das Upgrade verfügbar sind.

Zieleditionen sind die Editionen von Windows, die Sie zum Aktualisieren können. Sie können Informationen über die aktuelle Version oder die Zieledition von Schwelle Windows offline oder einem ausgeführten Betriebssystem anzeigen.

Weitere Informationen zu Windows Edition – Wartung DISM verfügbaren Befehlen finden Sie unter [Befehlszeilenoptionen DISM Windows Edition – Wartung](dism-windows-edition-servicing-command-line-options.md).

**Abrufen von Informationen zu den aktuellen Windows-Editionen**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen über die aktuelle Version des offline Windows-Abbilds auflisten, geben Sie den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-CurrentEdition
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-CurrentEdition
    ```

**Abrufen von Informationen zu Zieleditionen von Windows**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen über die Zieledition des Windows-Abbilds offline auflisten, geben Sie den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-TargetEditions
    ```

    Geben Sie für ein Betriebssystem ausgeführt wird den folgenden Befehl ein:

    ``` syntax
    Dism /online /Get-TargetEditions
    ```

## <a name="span-idgetapplicationinformationspanspan-idgetapplicationinformationspanspan-idgetapplicationinformationspanget-application-patch-information"></a><span id="GetApplicationInformation"></span><span id="getapplicationinformation"></span><span id="GETAPPLICATIONINFORMATION"></span>Lesen von Anwendungsinformationen Patch


Befehlszeilenoptionen zum Warten Anwendung kann auf eine offline-Abbild verwendet werden, so überprüfen Sie die Verfügbarkeit der Microsoft® Windows® Installer Anwendungspatches (MSP-Dateien) und zum Abfragen der offline-Abbild Informationen zur installierten Anwendungen der Windows Installer (MSI-Dateien) und Anwendung patches (MSP-Dateien).

Sie können ausführliche Informationen zu installierten MSP-Patches gefiltert nach Patch und Anwendung anzeigen. Wenn die Option **Patchcode** angegeben wird, wird detaillierte Informationen für alle Windows Installer-Anwendung angezeigt, die auf der Patch angewendet wird. Wenn die **Option/ProductCode** angegeben wird, werden Informationen zu allen MSP-Patches in der angegebenen Anwendung angezeigt.

Wenn die Optionen **Patchcode** **und/ProductCode** sowohl angegebenen, Informationen sind werden angezeigt, nur, wenn der angegebene Patch auf die angegebene Windows Installer-Anwendung angewendet wird. Wenn die Optionen **Patchcode** **und/ProductCode** nicht angegeben wurden, alle Windows Installer-Pakete installiert, und MSP-Patches angezeigt werden.

Weitere Informationen zur Anwendung – Wartung DISM verfügbaren Befehlen finden Sie unter [DISM Anwendung – Wartung Command-Line Options](dism-application-servicing-command-line-options.md).

**So führen Sie Informationen zu installierten MSP-patches**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen zu der MSP-Patches Geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /PatchCode:{B0B9997C-GUID-GUID-GUID-74D866BBDFFF}
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /PatchCode:{B0B9997C-GUID-GUID-GUID-74D866BBDFFF} /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Patch-Code</p></td>
<td align="left"><p>Eine GUID zum Identifizieren eines bestimmten Windows Installer-Pakets. Paketcodes ordnet eine MSI-Datei zusammen mit einer Anwendung oder eines Produkts und kann auch für die Überprüfung des Quellen verwendet werden.</p></td>
<td align="left"><p><strong>{8ACD2816-595D-48AA-A43B-3523CAA4F692}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Produktcode</p></td>
<td align="left"><p>Eine GUID, die den Prinzipal Identifikation einer Anwendung oder das Produkt ist.</p></td>
<td align="left"><p>{7764DEFC-C5D1-413C-8428-2AA903BF6DAA}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>PatchName</p></td>
<td align="left"><p>Der registrierte Anzeigename für den Patch. Für Patches, die nicht die <strong>DisplayName</strong> -Eigenschaft in der Tabelle MsiPatchMetadata enthalten, ist der zurückgegebene Anzeigename eine leere Zeichenfolge.</p></td>
<td align="left"><p>QFE9 - nicht entfernbar</p></td>
</tr>
<tr class="even">
<td align="left"><p>Patch-Status</p></td>
<td align="left"><p>1, wenn dieser Patch derzeit auf das Produkt angewendet wird.</p>
<p>2 Wenn diesen Patch durch einen anderen Patch abgelöst wurde.</p>
<p>4, wenn dieser Patch aufgrund eines anderen Patches veraltet vorgenommen wurden.</p></td>
<td align="left"><p>1 (wird angewendet)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Patch deinstalliert werden</p></td>
<td align="left"><p>1, wenn der Patch wie möglich aus dem Produkt deinstallieren markiert ist. Das Installationsprogramm in diesem Fall kann die Deinstallation weiterhin blockieren, wenn dieses Patch durch einen anderen Patch erforderlich ist, die nicht deinstalliert werden kann. Andernfalls wird 0 gemeldet.</p></td>
<td align="left"><p>0</p></td>
</tr>
<tr class="even">
<td align="left"><p>Link zur Hilfe</p></td>
<td align="left"><p>Informationsquellen für Support, sofern verfügbar.</p></td>
<td align="left"><p>http://www.Microsoft.com</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Transformationen</p></td>
<td align="left"><p>Der Satz von Patch-Transformationen für das Produkt nach der letzten Patchinstallation angewendet. Dieser Wert möglicherweise nicht für pro Benutzer nicht verwaltete Anwendungen zur Verfügung, wenn der Benutzer nicht am Computer angemeldet ist.</p></td>
<td align="left"><p><strong>: App1RTMToApp1QFE9;: #App1RTMToApp1QFE9</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Lokale Paket</p></td>
<td align="left"><p>Der Speicherort der lokalen Cache Patchdatei, die durch das Produkt verwendet wird.</p></td>
<td align="left"><p><strong>C:\Windows\Installer\132f5c.msp</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Installieren von Datum</p></td>
<td align="left"><p>Das Datum, an dem Produkt der Patch angewendet wurde.</p></td>
<td align="left"><p>20080912</p></td>
</tr>
</tbody>
</table>

 

**So führen Sie Informationen zu MSP-Patches zu einer Anwendung angewendet**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  So führen Sie Informationen zu der MSP-Patches Geben Sie einen der folgenden Befehle:

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatches
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatches /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Patch-Code</p></td>
<td align="left"><p>Eine GUID zum Identifizieren eines bestimmten Windows Installer-Pakets. Paketcodes ordnet eine MSI-Datei zusammen mit einer Anwendung oder eines Produkts und kann auch für die Überprüfung des Quellen verwendet werden.</p></td>
<td align="left"><p><strong>{8ACD2816-595D-48AA-A43B-3523CAA4F692}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Produktcode</p></td>
<td align="left"><p>Eine GUID, die den Prinzipal Identifikation einer Anwendung oder das Produkt ist.</p></td>
<td align="left"><p><strong>{7764DEFC-C5D1-413C-8428-2AA903BF6DAA}</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>PatchName</p></td>
<td align="left"><p>Der registrierte Anzeigename für den Patch. Für Patches, die nicht die <strong>DisplayName</strong> -Eigenschaft in der Tabelle MsiPatchMetadata enthalten, ist der zurückgegebene Anzeigename eine leere Zeichenfolge.</p></td>
<td align="left"><p>QFE9 - nicht entfernbar</p></td>
</tr>
</tbody>
</table>

 

**So führen Sie Informationen zu allen Windows Installer-Anwendungen**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen zu den MSP-Patches auflisten, geben Sie den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-Apps
    ```

Der Bericht generiert werden die Produktcode und Produktname für Anwendungen, die in die offline-Abbild installiert sind. Beispiel:

Produktcode: **{DB935363-5A68-47AF-A55A-CFC90F2E83BC}**

Produktname: MsiTestApplication2

**So führen Sie Informationen zu einer bestimmten Windows Installer-Anwendung**

1.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste, **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

2.  Informationen zu den MSP-Patches auflisten, geben Sie den folgenden Befehl ein:

    ``` syntax
    Dism /image:C:\test\offline /Get-AppInfo /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

Der Bericht generiert umfasst die folgende Informationen:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feld</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Produktcode</p></td>
<td align="left"><p>Eine GUID, die den Prinzipal Identifikation einer Anwendung oder das Produkt ist.</p></td>
<td align="left"><p><strong>{DB935363-5A68-47AF-A55A-CFC90F2E83BC}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Produktname</p></td>
<td align="left"><p>Der Name der Anwendung.</p></td>
<td align="left"><p>MsiTestApplication2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Produkt-Status</p></td>
<td align="left"><p>Den Installationsstatus für das Produkt, bei der Initialisierung.</p>
<p>-1, wenn das Produkt weder angekündigt noch installiert ist.</p>
<p>1, wenn das Produkt ist angekündigt, jedoch nicht installiert.</p>
<p>2 Wenn für einen anderen Benutzer das Produkt installiert ist.</p>
<p>5, wenn für den aktuellen Benutzer das Produkt installiert ist.</p></td>
<td align="left"><p>5 (installiert)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Package Code</p></td>
<td align="left"><p>Eine GUID zum Identifizieren eines bestimmten Windows Installer-Pakets. Paketcodes ordnet eine MSI-Datei zusammen mit einer Anwendung oder eines Produkts und kann auch für die Überprüfung des Quellen verwendet werden.</p></td>
<td align="left"><p><strong>{C67CA1AE-6074-4810-BD74-F6BBB609744A}</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Version des Produkts</p></td>
<td align="left"><p>Die Version des Produkts im Zeichenfolgenformat.</p></td>
<td align="left"><p>1.0.0</p></td>
</tr>
<tr class="even">
<td align="left"><p>Assignment-Typ</p></td>
<td align="left"><p>0, wenn das Produkt angekündigt ist oder pro Benutzer installiert.</p>
<p>1, wenn das Produkt angekündigt ist oder für alle Benutzer pro Computer installiert.</p></td>
<td align="left"><p>1 (pro Computer)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Herausgeber</p></td>
<td align="left"><p>Der Name des Herstellers des Produkts.</p></td>
<td align="left"><p>Microsoft MSI-Test</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sprache</p></td>
<td align="left"><p>Der decimal Bezeichner für die Produktsprache.</p></td>
<td align="left"><p>1033</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Installieren der Quelle</p></td>
<td align="left"><p>Das Verzeichnis, das die Quell-CAB-Datei oder der Quelle Dateistruktur des Installationspakets enthält.</p></td>
<td align="left"><p><strong>E:\Testpkg\App2_RTM\</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Paketname</p></td>
<td align="left"><p>Der Name der ursprünglichen Installationspaket.</p></td>
<td align="left"><p>MsiTestApplication2.msi</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Link zur Hilfe</p></td>
<td align="left"><p>Informationsquellen für Support, sofern verfügbar.</p></td>
<td align="left"><p>http://www.Microsoft.com/Management</p></td>
</tr>
<tr class="even">
<td align="left"><p>Transformationen</p></td>
<td align="left"><p>Der Satz von Patch-Transformationen durch die letzte Patchinstallation auf das Produkt angewendet. Dieser Wert möglicherweise nicht für pro Benutzer nicht verwaltete Anwendungen zur Verfügung, wenn der Benutzer nicht am Computer angemeldet ist.</p></td>
<td align="left"><p><strong>C:\Windows\Installer\{BDB20E90-3ACD-450B-BBDE-61E39687C6B1} \ACBlueT02.mst</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Lokale Paket</p></td>
<td align="left"><p>Die Position des lokal zwischengespeicherten Pakets.</p></td>
<td align="left"><p><strong>C:\Windows\Installer\132f3b.msi</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>Installieren von Datum</p></td>
<td align="left"><p>Das Datum, an das die Anwendung installiert wurde.</p></td>
<td align="left"><p><strong>20080912</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Ein Windows-Abbild mithilfe von DISM Service](service-a-windows-image-using-dism.md)

[Ein Windows PE-Abbild mit DISM-Service](service-a-windows-pe-image-with-dism.md)

[Deployment Image Servicing and Management (DISM) bewährte Methoden](deployment-image-servicing-and-management--dism--best-practices.md)

 

 






