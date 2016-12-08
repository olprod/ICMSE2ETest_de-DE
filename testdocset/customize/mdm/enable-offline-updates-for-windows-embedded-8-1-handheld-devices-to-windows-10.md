---
title: "Aktivieren von offline-Upgrades auf Windows-10 für Windows Embedded 8.1 Handheld-Geräte"
description: "Wie alle Windows-Geräte verwenden Windows 10 Mobile Geräte Microsoft Update standardmäßig zum Herunterladen von Updates über das Internet."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ED3DAF80-847C-462B-BDB1-486577906772
ms.openlocfilehash: 77559e511ef23bea0bba71c8a5910b189a67e0f8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-offline-upgrades-to-windows-10-for-windows-embedded-81-handheld-devices"></a>Aktivieren von offline-Upgrades auf Windows-10 für Windows Embedded 8.1 Handheld-Geräte


Wie alle Windows-Geräte verwenden Windows 10 Mobile Geräte Microsoft Update standardmäßig zum Herunterladen von Updates über das Internet. Jedoch in einigen Umgebungen Enterprise Geräte für den Internetzugriff zum Abrufen von Updates möglicherweise nicht. Aufgrund von Netzwerk-Einschränkungen oder anderen Unternehmensrichtlinien müssen ihre Updates Geräte von einem internen Speicherort heruntergeladen werden. In diesem Dokument wird beschrieben, wie offline Updates von System Center Configuration Manager zu aktivieren.

Hier ist eine Tabelle mit Aktualisierungspfad auf Windows 10 Mobile.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Starten Sie SKU</th>
<th>Upgrade auf 10 Windows Mobile</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Mobile 6.5</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Windows Phone 8</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Windows Phone 8.1</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>

 
Zum Konfigurieren des MDM Dienstanbieters und aktivieren die mobilen Geräte zum Herunterladen von Updates von einem vordefinierten internen Speicherort IT muss Administrator oder zuständigen Administrator eine Reihe von manuellen und automatisierten Schritte ausführen.

Es folgt die Gliederung des Prozesses:

1.  Vorbereiten eines neuen Geräts, das an das Internet auf die endgültige Updatepakete herunterladen eine Verbindung herstellen kann. 
2.  Nach dem Herunterladen von Updates und bevor Sie auf die Schaltfläche installieren, rufen Sie eine XML-Datei auf dem Gerät, das alle Metadaten für jede Updatepaket enthält ab.
3.  Überprüfen Sie den Statuscode in der XML-Datei.
4.  Überprüfen Sie die Registrierung Abhängigkeiten.
5.  Mithilfe eines Skripts, das wir bereitstellen, Analysieren der XML-Datei zum Extrahieren von download-URLs für die Update-Pakete.
6.  Laden Sie die Update-Paketen verwenden des Downloads URLs.
7.  Platzieren Sie heruntergeladenen Pakete auf einer internen Freigabe, die Geräte zugegriffen werden kann, die Sie aktualisieren.
8.  Erstellen Sie zwei zusätzliche XML-Dateien, die bestimmte Updates für den download zu definieren und die einzelnen Standorte aus der die Updates herunterladen und auf das Produktionsgerät bereitstellen.
9.  Starten des Aktualisierungsvorgangs ein Gerät.

Als Teil des Aktualisierungsvorgangs führt Windows Daten Migrators um Vordergrund konfigurierten Einstellungen und Daten auf dem Gerät angezeigt. Beispielsweise wenn das Gerät mit einem Wartungszeit oder andere Richtlinie Update in Windows Embedded 8.1 Handheld konfiguriert wurde, werden diese Einstellungen automatisch auf Windows 10 als Teil des Aktualisierungsvorgangs migriert. Wenn dem Endgerät für zugewiesenen Zugriffsrechten Sperrfunktionen konfiguriert wurde, wird Klicken Sie dann diese Konfiguration auch auf Windows-10 als Teil des Aktualisierungsvorgangs migriert. Dazu gehören ProductId & AumId Konvertierung für alle internen apps (einschließlich Buttonremapping apps).

Beachten Sie, dass die Migrators übernehmen der folgenden unwichtig:

-   3. Partei apps durch OEMs bereitgestellt
-   Veraltete 1st Party-apps, z. B. Bing News
-   Veraltete Systemprogramm Einstellungen wie Microsoft.Game, Microsoft.IE

Im Falle einer Enterprise zurücksetzen werden diese Einstellungen migrierten automatisch beibehalten.

Nach unten Reisen nach das Upgrade auf Windows 10 abgeschlossen ist, wenn Sie sich entschließen, schieben nach unten eine neue wehlockdown.xml, müssen Sie die folgenden Schritte ausführen, um sicherzustellen, dass die aktualisierten Einstellungen über ein Enterprise Zurücksetzen beibehalten werden:

1.  Löschen der TPK\*Ppkg und eine neue Ppkg mit der neuen Konfiguration zum permanenten Ordner weitergeben.
2.  Weitergeben einer neuen Ppkg mit der neuen Konfiguration mit einer höheren Priorität. Beachten Sie, dass in ICD Besitzer = Microsoft Rang = 0 ist die niedrigste Priorität; und umgekehrt. Mit diesem Schritt werden die alten zugewiesenen Zugriffsrechten Sperrfunktionen Konfiguration überschrieben.

**Anforderungen:**

-   Das Testgerät muss die andere Produktion Geräte identisch sein, die die Updates erhalten haben.
-   Das Testgerät muss mit System Center Configuration Manager registriert sein.
-   Das Gerät kann mit dem Internet verbinden.
-   Das Gerät muss auf eine SD-Karte mit mindestens 0,5 GB freiem Speicherplatz verfügen.
-   Stellen Sie sicher, dass die Einstellungsapp und PhoneUpdate Applet über Access zugewiesen verfügbar sind.

Im folgende Diagramm ist eine Übersicht über den Prozess.

![Aktualisierungsverfahren Sie für Windows embedded 8.1-Geräten](images/windowsembedded-update.png)

## <a name="step-1-prepare-a-test-device-to-download-updates-from-microsoft-update"></a>Schritt 1: Vorbereiten eines neuen Geräts zum Herunterladen von Updates von Microsoft Update


Definieren der Basislinie für das Update, das für andere Geräte angewendet wird. Verwenden Sie ein Gerät, das das letzte Bild als das Testgerät ausgeführt wird.

Lösen Sie das Gerät so nach Updates entweder manuell oder mithilfe von System Center Configuration Manager.

**Manuell**

1.  Wechseln Sie zu **Einstellungen für** das Gerät &gt; **Telefon Updates** &gt; **nach Updates suchen**.
2.  Synchronisieren Sie das Gerät. Wechseln Sie zu **Einstellungen** &gt; **Jahrestag** &gt; **registrierte** und klicken Sie auf das Aktualisierungssymbol klicken. Wiederholen Sie nach Bedarf.
3.  Führen Sie die aufforderungen, um die Updates herunterladen, aber drücken Sie nicht die Schaltfläche installieren.

> **Hinweis**  Es ist ein Fehler in allen Betriebssystemversionen bis zu GDR2, wo der CSP nicht zugewiesenen Wert festgelegt. Es ist nicht möglich, ändern, oder legen Sie dies bis GDR2 auf dem Gerät bereitgestellt wird.


**Mithilfe von System Center Configuration Manager**

1.  Lösen Sie eine Überprüfung des Testgeräts Remote durch die Bereitstellung einer Trigger Scan Basiskonfiguration aus.

    ![Gerät Scan mit sccm](images/windowsembedded-update2.png)

2.  Legen Sie den Wert dieses OMA-URIs durch an den Einstellungen dieses Elements Konfiguration durchsuchen und Auswählen der neu erstellten Trigger Scan Einstellungen aus dem vorherigen Schritt.

    ![Gerät Scan mit sccm](images/windowsembedded-update3.png)

3.  Stellen Sie sicher, dass der Wert, der für diesen URI angegeben ist größer als der Wert für die Geräte und die Remediate nicht konformer wann Regeln unterstützen die Option aktiviert ist. Bei der ersten jeder Wert, der größer als 0 funktionsfähig ist, ist jedoch für nachfolgende Konfigurationen, stellen Sie sicher, dass Sie einen inkrementierten Wert angeben.

    ![Gerät Scan mit sccm](images/windowsembedded-update4.png)

4.  Grundlage für die Konfiguration für TriggerScan erstellen und bereitstellen. Es wird empfohlen, dass diese Basiskonfiguration bereitgestellt werden, nachdem der Grundlinie für gesteuert Updates auf das Gerät (auf dem Gerät über eine Gerät Sync-Sitzung werden die entsprechenden Dateien bereitgestellt) angewendet wurde.
5.  Folgen Sie den Anweisungen für das Herunterladen von Updates, jedoch keine installieren Sie die Updates auf dem Gerät.


## <a name="a-href-idstep2astep-2-retrieve-the-device-update-report-xml-from-the-device"></a><a href="" id="step2"></a>Schritt 2: Abrufen von Device Update Report XML vom Gerät

Nach Updates werden heruntergeladen (jedoch nicht auf dem Gerät installiert), generiert der Prozess eine XML-Datei, die enthält Informationen zu den Paketen, dass es heruntergeladen. Sie müssen diese XML-Datei abrufen.

Es gibt zwei Methoden, um diese Datei vom Gerät abrufen. ein Pre-GDR1 und eine Post-GDR1.

**Pre-GDR1: Analysieren Sie ein Compliance-Protokoll vom Gerät in Configuration Manager**

1.  Erstellen Sie ein Konfigurationselement über Configuration Manager die Registrierung Eintrag ./Vendor/MSFT/EnterpriseExt/DeviceUpdate/ApprovedUpdatesXml einsehen.

    > **Hinweis**  In System Center Configuration Manager möglicherweise einen Fehler zu den Datei Grenzwert überschreiten, bei Verwendung von ApprovedUpdatesXml angezeigt. Der Prozess schließt jedoch weiterhin, auch wenn die Datei groß ist.

    Wenn die XML-Datei größer ist als 32 KB können Sie auch ./Vendor/MSFT/FileSystem/&lt;*Filename*&gt;.
2.  Einen Basisplan für diese Konfiguration-Element mit einem "Platzhalterwert" (beispielsweise Zzz) festgelegt, und stellen Sie sicher, dass Sie nicht warten.

    Der Wert der simulierte ist nicht festgelegt werden. Es wird nur für den Vergleich verwendet.
3.  Nach den Bericht, den XML an das Gerät gesendet wird, zeigt die System Center Configuration Manager ein Compliance-Protokoll, das die Informationen enthält. Das Protokoll kann großer Datenmengen enthalten.
4.  Analysieren Sie dieses Protokoll für den Bericht von XML-Inhalten.

Eine schrittweise Anleitung finden Sie unter [Gewusst wie: Abrufen von einem Gerät Update-Bericht mithilfe von System Center Configuration Manager-Protokolle](#how-to-retrieve-a-device-update-report-using-system-center-configuration-manager-logs).

**POST-GDR1: Abrufen der Bericht-Xml-Datei mit einer SD-Karte**

1.  Erstellen Sie ein Konfigurationselement mithilfe von Configuration Manager einen Registrierungswert für ./Vendor/MSFT/EnterpriseExt/DeviceUpdate/CopyUpdateReportToSDCard festgelegt.
2.  Der Wert, den Sie für diesen Artikel Konfiguration definieren wird durch den relativen Pfad zur SD-Karte einschließlich der Dateiname der XML-Datei definiert (beispielsweise SDCardRoot\\Update\\DUReport.xml).
3.  Entfernen Sie die SD-Karte vom Gerät zu, und kopieren Sie die XML-Datei mit dem PC.

## <a name="step-3-check-the-status-code-in-the-xml-file"></a>Schritt 3: Überprüfen Sie den Statuscode in der XML-Datei
Stellen Sie sicher, dass der Statuscode 0000-0000 (Erfolg) festgelegt ist.

## <a name="step-4-check-for-registry-dependencies"></a>Schritt 4: Überprüfen Sie für die Registrierung Abhängigkeiten
Abhängigkeiten Registrierung in der XML-Datei zu entfernen.

## <a name="step-5-extract-download-urls-from-the-report-xml"></a>Schritt 5: Extract herunterladen URLs aus dem XML-Bericht

Verwenden Sie das [Beispiel PowerShell-Skript](#example-powershell-script) , um die heruntergeladene Datei extrahieren von die URLs aus der XML-Datei oder manuell zu analysieren.

## <a name="step-6-retrieve-update-packages-using-download-urls"></a>Schritt 6: Abrufen Updatepakete von download-URLs

Verwenden Sie ein Skript oder manuell Updatepaket für jede auf einem PC oder einer internen Freigabe.

## <a name="step-7-place-the-update-packages-on-an-accessible-share"></a>Schritt 7: Setzen Sie die Update-Pakete eine Freigabe für zugegriffen werden

Legen Sie alle Updatepakete in einer internen Freigabe, die an alle Geräte zugegriffen werden kann, die diese Updates benötigen. Sicherstellen Sie, dass die interne Freigabe Unternehmensebene erfüllen mehrere Geräte die Updates zur gleichen Zeit zugreifen möchte.

## <a name="step-8-create-two-xml-files-for-production-devices-to-select-updates-and-download-locations"></a>Schritt 8: Erstellen von zwei XML-Dateien für Produktion Geräte auswählen Updates und download-Adressen

Hier sind die beiden Dateien.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Begriff</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DUControlledUpdates.xml</strong></p></td>
<td><p>Dies ist die gleiche Datei wie der Bericht, wie Sie, DEN XML in Schritt2 mit einem anderen Namen abgerufen. Diese Datei weist dem Gerät bestimmte Updatepakete heruntergeladen. Zum Beispiel finden Sie in Anhang</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>DUCustomContentUris.xml</strong></p></td>
<td><p>Diese Datei ordnet die Updatepakete in DUControlledUpdates.xml den internen freigegebenen Speicherort.</p></td>
</tr>
</tbody>
</table>

 

Schritte [zum Bereitstellen von Updates gesteuerte](#how-to-deploy-controlled-updates)eine exemplarische Vorgehensweise. Stellen Sie sicher, dass die Trigger Scan Basiskonfiguration noch NICHT bereitgestellt wurde.

<a href="" id="deploy-controlled-updates"></a>
### <a name="how-to-deploy-controlled-updates"></a>Gewusst wie: Bereitstellen von gesteuerte updates

Dieser Prozess besteht aus drei Teilen:

-   Erstellen eines Configuration-Elements für DUControlledUpdates.xml
-   Erstellen eines Configuration-Elements für DUCustomContentURIs.xml
-   Erstellen Sie ein Konfigurationselement genehmigten Updates.

<a href="" id="create-ducontrolledupdates"></a>
**Erstellen eines Configuration-Elements für DUControlledUpdates.xml**

1.  Erstellen eines Configuration-Elements an. Klicken Sie im Fenster **Einstellungen durchsuchen** wählen Sie **Device-Datei** als Filter aus, und klicken Sie dann auf **auswählen**.

    ![eingebettete geräteaktualisierung](images/windowsembedded-update18.png)

2.  Navigieren Sie zu der DUControlledUpdates.xml an, die über das Testgerät erstellt wurde und geben Sie dieser Dateipfad aus, und nennen Sie auf dem Gerät als `NonPersistent\DUControlledUpdates.xml`.

    ![eingebettete geräteaktualisierung](images/windowsembedded-update19.png)

3.  Aktivieren Sie das Kontrollkästchen **nicht konformer Remediate-Einstellungen**.
4.  Klicken Sie auf **OK**.

<a href="" id="create-ducustomcontent"></a>
**Erstellen eines Configuration-Elements für DUCustomContentURIs.xml**

1.  Erstellen eines Configuration-Elements, und geben Sie diesen Dateipfad, und nennen Sie das Gerät als`NonPersistent\DUCustomContentURIs.xml`
2.  Aktivieren Sie das Kontrollkästchen **nicht konformer Remediate-Einstellungen**.

    ![Embedded-Gerät unsuccessfully Written](images/windowsembedded-update21.png)

3.  Klicken Sie auf **OK**.

<a href="" id="create-config-baseline"></a>
**Erstellen Sie eine Basiskonfiguration für genehmigter updates**

1.  Erstellen Sie ein Konfigurationselement Baseline, und geben sie einen Namen (beispielsweise ControlledUpdates).
2.  Fügen Sie die Konfigurationselemente DUControlledUpdates und DUCustomContentURIs hinzu, und klicken Sie dann auf **OK**.

    ![Embedded-Gerät unsuccessfully Written](images/windowsembedded-update22.png)

3.  Bereitstellen der Basiskonfiguration an das entsprechende Gerät oder Gerät-Auflistung.

    ![Embedded-Gerät unsuccessfully Written](images/windowsembedded-update23.png)

4.  Klicken Sie auf **OK**.

## <a name="step-7-trigger-the-other-devices-to-scan-download-and-install-updates"></a>Schritt 7: Lösen Sie aus, die andere Geräte, um zu überprüfen, herunterladen und Installieren von updates

Nun, die andere "Produktion" oder "speicherintern" Geräte die erforderliche Informationen zum Herunterladen von Updates von einer internen Freigabe haben, sind die Geräte für Updates bereit.

### <a name="use-this-process-for-unmanaged-devices"></a>Verwenden Sie dieses Verfahren für nicht verwalteten Geräten

Wenn die Richtlinie zur Aktualisierung des Geräts, nicht verwaltete oder von System Center Configuration Manager eingeschränkt kann ein Prozess zur Aktualisierung auf dem Gerät in einer der folgenden Methoden gestartet werden:

-   Eine regelmäßige Überprüfung, bei der das Gerät automatisch führt gestartet.
-   Manuell über **Einstellungen** initiiert - &gt; **Telefon Update**  - &gt; **nach Updates suchen**.

### <a name="use-this-process-for-managed-devices"></a>Verwenden Sie dieses Verfahren für verwalteten Geräten

Wenn die Richtlinie zur Aktualisierung des Geräts verwaltet oder durch MDM eingeschränkt ist, kann ein Prozess zur Aktualisierung auf dem Gerät auf eine der folgenden Arten ausgelöst werden:

-   Lösen Sie das Gerät zum Suchen nach Updates über System Center Configuration Manager.

    Stellen Sie sicher, dass die Überprüfung Trigger wurde erfolgreich ausgeführt, und entfernen Sie die Trigger Scan Basiskonfiguration.

    > **Hinweis**  Stellen Sie sicher, dass die Richtlinie PhoneUpdateRestriction auf einen anderen Wert 0 (null) festgelegt ist, um sicherzustellen, dass das Gerät kein automatisches Scannen nicht ausgeführt wird.


-   Lösen Sie das Gerät, die als Teil eines Wartungsfensters von der IT-Administrator in System Center Configuration Manager definierten überprüft.

Nach Abschluss die Installation des Updates können IT-Admin der DUReport generiert in die Produktion Geräte um zu ermitteln, ob das Gerät erfolgreich die Liste der Updates installiert. Wenn das Gerät nicht, werden die Fehlercodes in der DUReport.xml bereitgestellt. Um den Bericht Gerät aktualisieren von einem Gerät abzurufen, führen Sie dieselben Schritte in [Schritt2](#step2)definiert.

<a href="" id="example-script"></a>
## <a name="example-powershell-script"></a>Beispiel-PowerShell-Skript

``` syntax
param (
# [Parameter (Mandatory=$true, HelpMessage="Input File")]
        [String]$inputFile,

# [Parameter (Mandatory=$true, HelpMessage="Download Cache Location")]
        [String]$downloadCache,

# [Parameter (Mandatory=$true, HelpMessage="Local Cache URL")]
        [String]$localCacheURL
       )

#DownloadFiles Function
function DownloadFiles($inputFile, $downloadCache, $localCacheURL)
{
    $customContentURIFileCreationError = "Not able to create Custom Content URI File"
#Read the Input File
    $report = [xml](Get-Content $inputFile)
    
# this is where the document will be saved
    $customContentURLFile = "$downloadCache\DUCustomContentUris.xml"
    New-Item -Path $customContentURLFile -ItemType File -force -ErrorAction SilentlyContinue -ErrorVariable NewItemError > $null
    if ($NewItemError -ne "")
    {
       PrintMessageAndExit $customContentURIFileCreationError
    }

# get an XMLTextWriter to create the XML
    $XmlWriter = New-Object System.XMl.XmlTextWriter($customContentURLFile,$Null)

# choose a pretty formatting:
    $xmlWriter.Formatting = 'Indented'
    $xmlWriter.Indentation = 1
    $XmlWriter.IndentChar = "`t"
 
# write the header
    $xmlWriter.WriteStartDocument()
    $xmlWriter.WriteStartElement('CustomContentUrls')
    foreach ($update in $report.UpdateData.coreUpdateMetadata.updateSet.update)
    {
        if (!$update.destinationFilePath -or !$update.contentUrl) 
        {
            continue;
        }

        $destFilePath = $update.destinationFilePath.Trim();
        $contentUrl = $update.contentUrl.Trim();

        Write-Host "Pre-Processing Line: $destFilePath#$contentUrl"
        if (($destFilePath -ne "") -and ($destFilePath.Contains("\")) -and ($contentUrl -ne "") -and ($contentUrl.Contains("/")) )
        {
            $isBundle = $update.isBundle
            $revisionId = $update.revisionId
            $updateId = $update.updateId
            $revisionNum = $update.revisionNum

            $fileName = $destFilePath.Substring($destFilePath.LastIndexOf("\") + 1);
#Write-Host "Processing Line: $destFilePath#$contentUrl"
            if ($fileName -ne "")
            {
                $destination = $downloadCache + "\" + $fileName;
                Try
                {
                    $wc = New-Object System.Net.WebClient
                    $wc.DownloadFile($contentUrl, $destination)
                    Write-Host "Successfull Download: $contentUrl#$destination";

                    $XmlWriter.WriteStartElement('contentUrl')
                    $XmlWriter.WriteAttributeString('isBundle', $isBundle)
                    $XmlWriter.WriteAttributeString('revisionId', $revisionId)
                    $XmlWriter.WriteAttributeString('updateId', $updateId)
                    $XmlWriter.WriteAttributeString('revisionNum', $revisionNum)
                    $XmlWriter.WriteRaw($localCacheURL + $fileName)
                    $xmlWriter.WriteEndElement()
                }
                Catch [ArgumentNullException]
                {
                    Write-Host "Content URL is null";
                }
                Catch [WebException]
                {
                    Write-Host "Invalid Content URL: $contentUrl";
                }
                Catch 
                {
                    Write-Host "Exception in Download: $contentUrl";
                }
            }
            else
            {
                Write-Host "Ignored Input Line: $contentUrl"
            }
        }
        else
        {
            Write-Host "Ignored Input Line: $contentUrl"
        }
    }

# close the "CustomContentUrls" node
    $xmlWriter.WriteEndElement()
 
# finalize the document
    $xmlWriter.WriteEndDocument()
    $xmlWriter.Flush()
    $xmlWriter.Close()

    Write-Host "Successfully Created Custom Content URL File: $customContentURLFile"
}

#PrintMessage Function
function PrintMessageAndExit($ErrorMessage)
{
    Write-Host $ErrorMessage
    exit 1
}

#PrintMessage Function
function PrintUsageAndExit()
{
    Write-Host "Usage: Download.ps1 -inputFile <InputFilePath> -downloadCache <CachePath> -localCacheURL <URL>"
    exit 1
}

if (($inputFile -eq "") -or ($downloadCache -eq "") -or ($localCacheURL -eq ""))
{
    PrintUsageAndExit
}
if (!$localCacheURL.EndsWith("/")) 
{
    $localCacheURL = $localCacheURL + "/";
}
$inputFileErrorString = "Input File does not exist";
$downloadCacheErrorString = "Download Cache does not exist";
$downloadCacheAddError = "Access Denied in creating the Download Cache Folder";
$downloadCacheRemoveError = "Not able to delete files from Download Cache"
$downloadCacheClearWarningString = "Download Cache not empty. Do you want to Clear";

#Check if Input File Exist
$inputFileExists = Test-Path $inputFile;
if(!$inputFileExists) 
{
    PrintMessageAndExit($inputFileErrorString)
}

#Check if Download Cache Exist
$downloadCacheExists = Test-Path $downloadCache;
if(!$downloadCacheExists)
{
    PrintMessageAndExit($downloadCacheErrorString)
}

$downloadCacheFileCount = (Get-ChildItem $downloadCache).Length;
if ($downloadCacheFileCount -ne 0)
{
#Clear the directory
    Remove-Item $downloadCache -Recurse -Force -Confirm -ErrorVariable RemoveItemError -ErrorAction SilentlyContinue > $null
    if ($RemoveItemError -ne "")
    {
        PrintMessageAndExit $downloadCacheRemoveError
    }

    $childItem = Get-ChildItem $downloadCache -ErrorAction SilentlyContinue > $null
    $downloadCacheFileCount = ($childItem).Length;
    if ($downloadCacheFileCount -ne 0)
    {
        PrintMessageAndExit $downloadCacheRemoveError
    }

#Create a new directory
    New-Item -Path $downloadCache -ItemType Directory -ErrorAction SilentlyContinue -ErrorVariable NewItemError > $null
    if ($NewItemError -ne "")
    {
       PrintMessageAndExit $downloadCacheAddError
    }
}

DownloadFiles $inputFile $downloadCache $localCacheURL
```

<a href="" id="how-to-retrieve"></a>
## <a name="how-to-retrieve-a-device-update-report-using-system-center-configuration-manager-logs"></a>Gewusst wie: Abrufen von einem Gerät Update-Bericht mithilfe von System Center Configuration Manager-Protokolle

Verwenden Sie dieses Verfahren für Pre-GDR1 Geräte.

**Für Pre-GDR1 Geräte**

1.  Lösen Sie eine Überprüfung Gerät aus. Wechseln Sie zu **Einstellungen**  - &gt; **Phone Update**  - &gt; **nach Updates suchen**.

    Da die DUReport Einstellungen nicht behoben haben, sollten Sie eine Nichteinhaltung sehen.
2.  In System Center Configuration Manager unter **Ressourcen und Compliance** &gt; **Kompatibilitätseinstellungen**mit der rechten Maustaste auf die **Konfiguration von Elementen**.
3.  Wählen Sie **Configuration-Element erstellen**.

    ![Geräte-Update mit sccm](images/windowsembedded-update5.png)
4.  Geben Sie einen Dateinamen (beispielsweise GetDUReport), und wählen Sie dann **Mobile-Gerät**.
5.  Überprüfen Sie auf der Seite **Einstellungen für mobiles Gerät** das **Zusätzliche Einstellungen konfigurieren, die nicht in der Standardgruppe Einstellungen sind**, und klicken Sie auf **Weiter**.

    ![Geräte-Update mit sccm](images/windowsembedded-update6.png)
6.  Klicken Sie auf der Seite **Zusätzliche Einstellungen** auf **Hinzufügen**.

    ![Geräte-Update mit sccm](images/windowsembedded-update7.png)
7.  Klicken Sie auf der Seite **Einstellungen navigieren** auf **Einstellung erstellen**.

    ![Geräte-update](images/windowsembedded-update8.png)
8.  Geben Sie einen eindeutigen **Namen**ein. Wählen Sie für den **Typ der Einstellung** **OMA-URI** , und wählen Sie für den **Datentyp** **Zeichenfolge**.
9.  Geben Sie in das Textfeld **OMA URI** `./Vendor/MSFT/EnterpriseExt/DeviceUpdate/UpdatesResultXml`, klicken Sie dann auf **OK**.

    ![Update des mobilen Geräts](images/windowsembedded-update9.png)
10. Klicken Sie auf der Seite **Einstellungen wechseln Sie** auf **Schließen**.
11. Überprüfen Sie auf der Seite des **Assistenten zum Erstellen eines Configuration-Element** **Alle Windows Embedded 8.1 Handheld** als die unterstützte Plattform, und klicken Sie dann auf **Weiter**.

    ![eingebettete geräteaktualisierung](images/windowsembedded-update10.png)
12. Schließen Sie die Seite des **Assistenten zum Erstellen eines Configuration-Element** .
13. Mit der rechten Maustaste auf den neu erstellen Konfiguration Artikel, und wählen Sie dann auf die Registerkarte **Kompatibilitätsregeln** .
14. Klicken Sie auf die Einstellung der neu erstellten mobiles Gerät (beispielsweise DUReport), und klicken Sie dann auf **auswählen**.
15. Geben Sie einem Platzhalterwert (beispielsweise Zzz), die sich von der auf dem Gerät unterscheidet.

    ![eingebettetes geräteaktualisierung](images/windowsembedded-update11.png)
16. Deaktivieren Sie Remediation, indem die Option **Remediate nicht konformer Regeln beim unterstützt** deaktivieren.
17. Klicken Sie auf **OK** , um die Seite Regel bearbeiten zu schließen.
18. Erstellen Sie eine neue Basiskonfiguration. Klicken Sie unter **Ressourcen und Compliance** &gt; **Kompatibilitätseinstellungen**, mit der rechten Maustaste auf **Den Basislinien Konfiguration**.
19. Wählen Sie **Configuration-Element erstellen**.

    ![eingebettetes geräteaktualisierung](images/windowsembedded-update12.png)
20. Geben Sie einen Basisplan Namen (beispielsweise RetrieveDUReport).
21. Fügen Sie das Konfigurationselement, das Sie gerade erstellt haben. Wählen Sie **Hinzufügen** aus, und wählen Sie dann das Menüelement-Konfiguration, das Sie gerade erstellt, (beispielsweise DUReport haben).

    ![eingebettetes geräteaktualisierung](images/windowsembedded-update13.png)
22. Klicken Sie auf **OK**und dann auf **OK** , um die Grundlage für die Konfiguration abzuschließen.
23. Bereitstellen der neu erstellten Basiskonfiguration auf das gewünschte Gerät-Auflistung an. Mit der rechten Maustaste auf die Grundlage für die Konfiguration, die Sie erstellt haben und die select **Bereitstellen**.

    ![eingebettetes geräteaktualisierung](images/windowsembedded-update14.png)
24. Aktivieren Sie das Kontrollkästchen **Remediate nicht konformer Regeln beim unterstützt**.
25. Wählen Sie das gewünschte Gerät-Auflistung aus, und legen Sie den Zeitplan.

    ![Geräte-update](images/windowsembedded-update15.png)
26. Wählen Sie zum Anzeigen der Inhalts DUReport der entsprechenden bereitstellungs für die Konfiguration Saseline, die Sie erstellt haben. Mit der rechten Maustaste auf die Bereitstellung, und wählen Sie **Status anzeigen**.
27. Klicken Sie auf **Ausführen Zusammenfassung** , und klicken Sie dann auf **Aktualisieren**. Klicken Sie auf der Registerkarte nicht konformer sollte die Test-Geräte aufgeführt sein.
28. **Postendetails**klicken Sie unter mit der rechten Maustaste auf das Testgerät aus, und wählen Sie dann **Im Modus Details**.

    ![Geräte-update](images/windowsembedded-update16.png)
29. In der Registerkarte nicht konformer sehen Sie die DUReport Sie können nicht den Inhalt von hier aus abrufen.

    ![Geräte-update](images/windowsembedded-update17.png)
30. Öffnen Sie zum Abrufen der DUReport ein Explorer-Fenster auf C:\\Program Files\\SMS\_CCM\\SMS\_DM.log.
31. Suchen Sie in der Protokolldatei vom unteren für "./Vendor/MSFT/EnterpriseExt/DeviceUpdate/UpdatesResultXml" RuleExression = "Equals Zzz" Zzz, in dem der Wert der simulierte ist. Direkt über die Informationen für UpdateData kopieren und mithilfe dieser Informationen die DUControlledUpdates.xml erstellen.

 





