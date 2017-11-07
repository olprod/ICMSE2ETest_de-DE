---
title: EnterpriseDesktopAppManagement CSP
description: Dienstanbieter EnterpriseDesktopAppManagement Konfiguration wird verwendet, um Enterprise-Desktopanwendung Management Aufgaben wie das Abfragen von installierten unternehmensanwendungen, behandeln Applikationen installieren oder Entfernen von Anwendungen.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2BFF7491-BB01-41BA-9A22-AB209EE59FC5
ms.openlocfilehash: 2672eb2a8dd5344ab5a69fa6262e185f2cf8a1de
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisedesktopappmanagement-csp"></a>EnterpriseDesktopAppManagement CSP


Der Dienstanbieter für EnterpriseDesktopAppManagement Konfiguration wird verwendet, um Enterprise-Desktopanwendung Management Aufgaben wie das Abfragen von installierten unternehmensanwendungen, behandeln Installieren von Anwendungen oder Anwendungen zu entfernen.

Anwendungsinstallationen können einige Zeit in Anspruch nehmen, daher sie erfolgt asynchron. Wenn der Befehl Exec abgeschlossen ist, kann der Client eine generische Warnung an den Verwaltungsserver mit dem Status senden, ob es sich bei einem Fehler oder Erfolg ist. Ein SyncML Beispiel finden Sie unter [Warnung (Beispiel)](#alert-example).

Das folgende Diagramm zeigt die EnterpriseDesktopAppManagement CSP im Strukturformat dar.

![Enterprisedesktopappmanagement csp](images/provisioning-csp-enterprisedesktopappmanagement.png)

<a href="" id="--vendor-msft-enterprisedesktopappmanagement"></a>**./Vendor/MSFT/EnterpriseDesktopAppManagement**  
Der Stammknoten für den Dienstanbieter für EnterpriseDesktopAppManagement-Konfiguration.

<a href="" id="msi"></a>**MSI-DATEI**  
Knoten für alle Einstellungen.

<a href="" id="msi-productid"></a>**MSI / ***_ProductID_**  
Der MSI-Produktcode für die Anwendung.

<a href="" id="msi-productid-version"></a>* *MSI /*ProductID*/Version**  
Versionsnummer. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="msi-productid-name"></a>* *MSI /*ProductID*/Name**  
Der Name der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="msi-productid-publisher"></a>* *MSI /*ProductID*/Publisher**  
Herausgeber der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="msi-productid-installpath"></a>* *MSI /*ProductID*/InstallPath**  
Installationspfad der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist abrufen.

<a href="" id="msi-productid-installdate"></a>* *MSI /*ProductID*/InstallDate**  
Installationsdatum der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="msi-productid-downloadinstall"></a>* *MSI /*ProductID*/DownloadInstall**  
Führt den Download und die Installation der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgänge sind Execute, und erhalten.

<a href="" id="msi-productid-status"></a>* *MSI /*ProductID*/Status**  
Status der Anwendung. Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

| Status                    | Wert |
|---------------------------|-------|
| Initialisiert               | 10    |
| Download wird ausgeführt.      | 20    |
| Ausstehende Download "Wiederholen"    | 25    |
| Fehler beim Download           | 30    |
| Download abgeschlossen        | 40    |
| Ausstehende Benutzersitzung      | 48    |
| Erzwingung In Bearbeitung   | 50    |
| Ausstehende Erzwingung "Wiederholen" | 55    |
| Erzwingung fehlgeschlagen        | 60    |
| Erzwingung abgeschlossen     | 70    |

 

<a href="" id="msi-productid-lasterror"></a>* *MSI /*ProductID*/LastError**  
Der letzte Fehlercode während der Installation der Anwendung. Dies wird in der Regel als ein HRESULT-Format gespeichert. Je nachdem, was bei der Fehler aufgetreten ist kann dies das Ergebnis der Ausführung von MSIExec.exe oder das Ergebnis der Fehlermeldung aus einer API, die nicht erfolgreich sein.

Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

<a href="" id="msi-productid-lasterrordesc"></a>* *MSI /*ProductID*/LastErrorDesc**  
Beschreibung des letzte Code enthält. Der Wert LastErrorDesc wird für den Wert der Abgleichs LastError gesucht. Manchmal kann es keine LastErrorDesc zurückgegeben.

Werttyp ist Zeichenfolge. Unterstützte Vorgang ist Get.

## <a name="examples"></a>Beispiele


**SyncML Anforderung CSP-Versionsinformationen**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement?prop=Type</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

In der folgenden Tabelle werden die Felder im vorherigen Beispiel beschrieben:

| Name   | Beschreibung                                                                                                                   |
|--------|-------------------------------------------------------------------------------------------------------------------------------|
| Erhalten    | Auszuführende Operation. Get-Operation ist eine Anforderung Informationen zurückgeben.                                              |
| CmdID  | Eingabewert verwendet, um die Anforderung zu verweisen. Antworten werden dieser Wert enthalten die Anfrage und-Antwort abgleichen verwendet werden kann. |
| LocURI | Pfad zu Win32 CSP Befehlsprozessor.                                                                                          |

 

**SyncML MSI-Vorgänge für die Anwendung Deinstallation ausführen**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Delete>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D</LocURI>
        </Target>
      </Item>
    </Delete>
    <Final/>
  </SyncBody>
</SyncML>
```

In der folgenden Tabelle werden die Felder im vorherigen Beispiel beschrieben:

| Name   | Beschreibung                                                                                                                                                                                                         |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Löschen | Auszuführende Operation. Der Löschvorgang ist eine Anforderung an den Knoten CSP zu löschen, der die angegebene installiert MSI-Anwendung darstellt und, ausführen und Deinstallieren der Anwendung im Rahmen des Prozesses. |
| CmdID  | Eingabewert verwendet, um die Anforderung zu verweisen. Antworten werden dieser Wert enthalten die Anfrage und-Antwort abgleichen verwendet werden kann.                                                                                       |
| LocURI | Pfad zu Win32 CSP Befehlsprozessor, einschließlich der Produkt-ID (in diesem Beispiel 1803A630-3C38-4D2B-9B9A-0CB37243539C)-Eigenschaft enthält Escapezeichen für XML-Formatierung.                                                          |

 

**SyncML MSI-Operationen für die Erstellung von Statusberichten**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

In der folgenden Tabelle werden die Felder im vorherigen Beispiel beschrieben:

| Name   | Beschreibung                                                                                                                                                |
|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Erhalten    | Auszuführende Operation. Get-Operation ist eine Anforderung an den Bericht, dass der Status der angegebenen MSI Anwendung installiert.                                 |
| CmdID  | Eingabewert verwendet, um die Anforderung zu verweisen. Antworten werden dieser Wert enthalten die Anfrage und-Antwort abgleichen verwendet werden kann.                              |
| LocURI | Pfad zu Win32 CSP Befehlsprozessor, einschließlich der Produkt-ID (in diesem Beispiel 1803A630-3C38-4D2B-9B9A-0CB37243539C)-Eigenschaft enthält Escapezeichen für XML-Formatierung. |

 

**SyncML MSI-Installationsvorgänge für eine Anwendung gezielt an einen bestimmten Benutzer auf dem Gerät ausführen. Der Befehl hinzufügen ist erforderlich, um den Befehl Exec Länderkürzel.**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Add>
      <CmdID>1</CmdID>
      <Item>
        <Target>
        <LocURI>./User/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C384D2B-9B9A-0CB37243539C%7D/DownloadInstall</LocURI>
        </Target>
      </Item>
    </Add>
    <Exec>
      <CmdID>6</CmdID>
      <Item>
        <Target>
          <LocURI>./User/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D/DownloadInstall</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">xml</Format>
          <Type xmlns="syncml:metinf">text/plain</Type>
        </Meta>
        <Data>
          <MsiInstallJob id="{9BD4F7CD-880A-40B5-B74C-1BEECB51E596}">
            <Product Version="1.0.0">
              <Download>
                <ContentURLList>
                  <ContentURL>
                    http://bcl-w2k12r2-vm/testapps/msi/reboot/reboot.msi
                  </ContentURL>
                  <ContentURL>https://dp2.com/packages/myApp.msi</ContentURL>
                </ContentURLList>
              </Download>
              <Validation>                
<FileHash>134D8F1F7C3C036DC3DCDA9F97515C8C7951DB154B73365C9C22962BD23E3EB3</FileHash>
              </Validation>
              <Enforcement>
                <CommandLine>/quiet</CommandLine>
                <TimeOut>5</TimeOut>
                <RetryCount>3</RetryCount>
                <RetryInterval>5</RetryInterval>
              </Enforcement>
            </Product>
          </MsiInstallJob>
        </Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

In der folgenden Tabelle werden die Felder im vorherigen Beispiel beschrieben:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Add</td>
<td>Dies ist erforderlich, vor dem Befehl Exec.
<ul>
<li>CmdID - Eingabewert verwendet, um die Anforderung zu verweisen. Antworten enthält dieser Wert, der verwendet werden kann, die Anforderung und Antwort übereinstimmen.</li>
<li>LocURI - Pfad zu Win32 CSP Befehlsprozessor, einschließlich der Produkt-ID (in diesem Beispiel 1803A630-3C38-4D2B-9B9A-0CB37243539C)-Eigenschaft enthält Escapezeichen für XML-Formatierung.</li>
</ul></td>
</tr>
<tr class="even">
<td>EXEC</td>
<td>Der Knoten Exec umfasst die Parameter und Eigenschaften zum Suchen, herunterladen, überprüfen und Ausführen der Produktinstallation benötigt.
<ul>
<li>CmdID - Eingabewert verwendet, um die Anforderung zu verweisen. Antworten werden dieser Wert enthalten die Anfrage und-Antwort abgleichen verwendet werden kann.</li>
<li>LocURI - Pfad zu Win32 CSP Befehlsprozessor, einschließlich der Produkt-ID (in diesem Beispiel 1803A630-3C38-4D2B-9B9A-0CB37243539C)-Eigenschaft enthält Escapezeichen für XML-Formatierung.</li>
<li>Daten - Daten der Knoten enthält eine eingebettete XML-DATEI vom Typ "MsiInstallJob"</li>
<li>MsiInstallJob - enthält alle Informationen für die erfolgreiche Download, Validierung und Ausführung der MSI-Installation erforderlich (siehe Abschnitt am Ende dieses Dokuments ausführliche für dieses Objekt eingebettete Daten).</li>
</ul></td>
</tr>
</tbody>
</table>

 

> **Hinweis**  Status des Auftrags MSI-Informationen werden mit standard OMA DM Benachrichtigungsmechanismus gemeldet. Der Status gemeldet wird dargestellt, HRESULT gemäß Definition im MSIEXEC Thema auf der Microsoft TechNet unter standard MSIEXEC Rückgabecodes unter <https://technet.microsoft.com/library/cc759262(v=ws.10).aspx>.

 

**SyncML zum Ausführen der MSI-Installationsvorgänge für eine Anwendung, die auf die für alle Benutzer auf dem Gerät (pro Gerät Installation)**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Add>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>./Device /Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B6F7CB29F-1319-4816-B345-0856916EB801%7D/DownloadInstall
          </LocURI>
      </Target>
    </Item>
  </Add>
    <Exec>
      <CmdID>67890</CmdID>
      <Item>
        <Target>
          <LocURI>./Device /Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B6F7CB29F-1319-4816-B345-0856916EB801%7D/DownloadInstall</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">xml</Format>
          <Type xmlns="syncml:metinf">text/plain</Type>
        </Meta>
        <Data>
          <MsiInstallJob id="{9BD4F7CD-880A-40B5-B74C-1BEECB51E596}">
            <Product Version="1.0.0">
              <Download>
                <ContentURLList>
                  <ContentURL>http://bcl-w2k12r2-vm/testapps/msi/Orca/Orca.msi</ContentURL>
                  <ContentURL>https://dp2.com/packages/myApp.msi</ContentURL>
                </ContentURLList>
              </Download>
              <Validation>
                <FileHash>4525065777EF18B9444ABF71DD4B48E5F64F4F0E1E029995FB8DA441CDE4296E</FileHash>
              </Validation>
              <Enforcement>
                <CommandLine>/quiet</CommandLine>
                <TimeOut>5</TimeOut>
                <RetryCount>3</RetryCount>
                <RetryInterval>5</RetryInterval>
              </Enforcement>
            </Product>
          </MsiInstallJob>
        </Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

MsiInstallJob in der folgenden Tabelle werden die Schemaelemente beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>MsiInstallJob</td>
<td>Stammelement
<p>&quot;Attribut: &quot;-Id: die ID der Anwendung installiert wird</p></td>
</tr>
<tr class="even">
<td>Produkt</td>
<td>untergeordnetes Element des MsiInstallJob
<p>Attribut: "Version" – Zeichenfolgendarstellung der Version der Anwendung</p></td>
</tr>
<tr class="odd">
<td>Download</td>
<td>untergeordnetes Element des Produkts. Container für Download-Konfigurationsinformationen.</td>
</tr>
<tr class="even">
<td>ContentURLList</td>
<td>untergeordnetes Element des Downloads. Liste der 1 oder mehrere Herunterladen von Bildern URL Locator in Form von ContentURL Elemente enthält.</td>
</tr>
<tr class="odd">
<td>ContentURL</td>
<td>Speicherort Inhalte sollten hier heruntergeladen werden. Muss eine Eigenschaft formatiert URL an, zeigt die. MSI-Datei.</td>
</tr>
<tr class="even">
<td>Überprüfung</td>
<td>Enthält Informationen zum Überprüfen der Echtheit konkurrieren. • FileHash – SHA256-Hash-Wert der Inhalt der Datei</td>
</tr>
<tr class="odd">
<td>FileHash</td>
<td>SHA256-Hash-Wert der Inhalt der Datei</td>
</tr>
<tr class="even">
<td>Erzwingung</td>
<td>Beim Installieren dieser MSI zu verwendende Eigenschaften für die Softwareinstallation</td>
</tr>
<tr class="odd">
<td>CommandLine</td>
<td>Befehlszeilenoptionen für die beim Aufruf von MSIEXEC.exe verwendet werden</td>
</tr>
<tr class="even">
<td>Timeout</td>
<td>Zeitspanne in Minuten an, denen der Installationsvorgang werden, bevor Sie das Installationsprogramm ausgeführt kann betrachtet die Installation möglicherweise ist ein Fehler aufgetreten und der Installationsvorgang nicht mehr überwacht.</td>
</tr>
<tr class="odd">
<td>RetryCount</td>
<td>Fehler bei die Anzahl der Häufigkeit, mit die der herunterladen und installieren-Vorgang wird wiederholt werden, bevor die Installation als gekennzeichnet wird.</td>
</tr>
<tr class="even">
<td>RetryInterval</td>
<td>Dauer in Minuten zwischen Retry Vorgänge.</td>
</tr>
</tbody>
</table>

 

Es folgt ein Beispiel für eine häufige Antwort auf eine Anforderung

``` syntax
<?xml version="1.0" encoding="utf-16"?>
<SyncML>
  <SyncHdr />
  <SyncBody>
    <Status>
      <CmdID>12345</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>0</CmdRef>
      <Cmd>SyncHdr</Cmd>
      <Data>200</Data>
    </Status>
    <Status>
      <CmdID>67890</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>1</CmdRef>
      <Cmd>Add</Cmd>
      <Data>200</Data>
    </Status>
    <Final />
  </SyncBody>
</SyncML>
```

## <a name="how-to-determine-which-installation-context-to-use-for-an-msi-package"></a>Gewusst wie: bestimmen, welche Installation Kontext für ein MSI-Paket verwenden


In den folgenden Tabellen gezeigt wie app Zielgruppenadressierung und MSI-Paket-Typ (pro Benutzer, pro Computer oder Dualmodus) im-Client installiert werden.

Für Intune Standalone-Umgebung bestimmt das MSI-Paket Ausführungskontexts MSI-DATEI.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ziel</th>
<th>MSI pro Benutzer</th>
<th>MSI pro Computer</th>
<th>Dualmodus MSI-DATEI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User</td>
<td>Installieren Sie den MSI-pro Benutzer
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
<td>Installieren Sie das MSI pro Gerät
<p>LocURI enthält ein Präfix Gerät wie z. b. / Gerät</p></td>
<td>Installieren Sie den MSI-pro Benutzer
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
</tr>
<tr class="even">
<td>System</td>
<td>Installieren Sie den MSI-pro Benutzer
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
<td>Installieren Sie das MSI-pro Gerät
<p>LocURI enthält ein Präfix Gerät wie z. b. / Gerät</p></td>
<td>Installieren Sie den MSI-pro Benutzer
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
</tr>
</tbody>
</table>

 

In der folgenden Tabelle gilt für SCCM-hybridumgebung.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ziel</th>
<th>MSI pro Benutzer</th>
<th>MSI-DATEI pro Computer</th>
<th>Dualmodus MSI-DATEI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User</td>
<td>Installieren des MSI-pro Benutzers
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
<td>Installieren Sie das MSI pro Gerät
<p>LocURI enthält ein Präfix Gerät wie z. b. / Gerät</p></td>
<td>Installieren Sie den MSI-pro Benutzer
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
</tr>
<tr class="even">
<td>System</td>
<td>Installieren des MSI-pro Benutzers
<p>LocURI enthält ein Benutzerpräfix wie z. b. / Benutzer</p></td>
<td>Installieren Sie das MSI pro Gerät
<p>LocURI enthält ein Präfix Gerät wie z. b. / Gerät</p></td>
<td>Installieren Sie den MSI-System Kontext
<p>LocURI enthält ein Präfix Gerät wie z. b. / Gerät</p></td>
</tr>
</tbody>
</table>

 

## <a name="how-to-determine-the-package-type-from-the-msi-package"></a>Gewusst wie: bestimmen den Pakettyp aus dem MSI-Paket


-   ALLUSERS = ""-Pakettyp pro Benutzer
-   ALLUSERS = 1 - Pakettyp pro Computer
-   ALLUSERS = 2, MSIINSTALLPERUSER = 1 - dual-Modus Pakettyp

Eigenschaften können im jeweiligen Paket angegeben, über die Befehlszeile übergeben, durch eine Transformation geändert oder über eine Benutzeroberfläche (häufiger) ausgewählt werden.

Es folgt eine Liste von verweisen:

-   [Mithilfe von Windows Installer](https://technet.microsoft.com/library/cc782896.aspx)
-   [Erstellen von einem einzelnen Paket bereit für pro-Benutzer- oder maschinenbasierte Installation Kontext in Windows 7](http://blogs.msdn.com/b/windows_installer_team/archive/2009/09/02/authoring-a-single-package-for-per-user-or-per-machine-installation-context-in-windows-7.aspx)
-   SyncML Darstellung-Protokoll Entwurfsversion 1.3 27 August 2009 (OMA-TS-SyncML\_RepPro V1\_3-20090827-D)

## <a name="alert-example"></a>Warnung (Beispiel)


``` syntax
<Alert>
       <CmdID>4</CmdID>
       <Data>1224</Data>
       <Item>
          <Source>
             <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/{AF9257BA-6BBD-4624-AA9B-0182D50292C3}/DownloadInstall</LocURI>
          </Source>
          <Meta>
             <Type xmlns="syncml:metinf">Reversed-Domain-Name:com.microsoft.mdm.win32csp_install</Type>
             <Format xmlns="syncml:metinf">int</Format>
             <Mark xmlns="syncml:metinf">informational</Mark>
          </Meta>
          <Data>0</Data>
       </Item>
</Alert>
```

 

 






