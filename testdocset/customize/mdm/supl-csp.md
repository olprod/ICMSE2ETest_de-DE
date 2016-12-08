---
title: SUPL CSP
description: SUPL CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: afad0120-1126-4fc5-8e7a-64b9f2a5eae1
ms.openlocfilehash: a85e780952fadc4edbf73265d019fb1d5a0a992a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supl-csp"></a>SUPL CSP


SUPL Konfigurationsdienstanbieter wird verwendet, um den Client Speicherort konfigurieren, wie in der folgenden Tabelle dargestellt.

<table>
<colgroup>
<col width="20%" />
<col width="40%" />
<col width="40%" />
</colgroup>
<thead>
<tr class="header">
<th>Suchdienst</th>
<th>SUPL</th>
<th>V2 UPL</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Verbindungstyp</p></td>
<td><p>Alle Verbindungen als CDMA</p></td>
<td><p>CDMA</p></td>
</tr>
<tr class="even">
<td><p>Configuration</p></td>
<td><ul>
<li><p>Die Einstellungen, die an den Treiber GNSS so konfigurieren Sie das Verhalten SUPL gelegt werden müssen:</p>
<ul>
<li><p>Die Adresse des Servers Home SUPL (H-SLP).</p></li>
<li><p>H-SLP Serverzertifikat.</p></li>
<li><p>Positionierung-Methode.</p></li>
<li><p>Die Version des Protokolls standardmäßig verwendet.</p></li>
</ul></li>
<li><p>MCC/MNC-Wert-Paaren, die verwendet werden, an welche Networks UUIC ermittelt das SUPL-Konto.</p></li>
</ul></td>
<td><ul>
<li><p>Adresse des Servers – eines mobilen Positionierung Center für nicht vertrauenswürdigen Modus.</p></li>
<li><p>Die Positionierung-Methode wird von den MPC für nicht vertrauenswürdigen Modus verwendet.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

Die SUPL oder V2 UPL Verbindung wird neu konfiguriert werden, jedes Mal, wenn das Gerät neu gestartet wird, wird eine neue UICC eingefügt oder neue Einstellungen werden mithilfe von OMA-Clientbereitstellung, OMA DM, bereitgestellt oder TestTools. Das Gerät im roaming-Modus ist, umstellen, Mobile Station eigenständigen Modus, in dem nur die integrierten – Microsoft Speicherort Komponenten verwendet werden.

Das folgende Diagramm veranschaulicht das SUPL Configuration Service Provider Management-Objekts im Strukturformat von OMA DM und OMA-Clientbereitstellung verwendet.

> **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION-Funktion aus einer Anwendung der Netzwerk-Konfiguration zugegriffen werden.

 

![Supl Csp (dm, cp)](images/provisioning-csp-supl-dmandcp.png)



<a href="" id="supl1"></a>**SUPL1**  
Für SUPL erforderlich. Definiert das Konto für den Knoten (SUPL aktiviert Terminal ist FESTGELEGT). Nur ein SUPL Konto wird zu einem bestimmten Zeitpunkt unterstützt.

<a href="" id="appid"></a>**AppID**  
Erforderlich. Die AppID für SUPL wird automatisch festgelegt, um `"ap0004"`. Dies ist eine nur-Lese-Wert.

<a href="" id="addr"></a>**Adresse**  
Optional Gibt die Adresse des Servers Home SUPL Speicherort Plattform (H SLP) für nicht-Proxy-Modus. Der Wert ist eine Serveradresse als einen vollqualifizierten Domänennamen und den Port angegeben als ganze Zahl, mit dem Format *Server*: *Port*.

Wenn dieser Wert nicht angegeben ist, leitet das Gerät die H SLP Adresse aus der IMSI gemäß Definition im Standard SUPL ab. Um automatische Generierung der H SLP Adresse basierend auf den IMSI zu verwenden, muss die Länge MNC ordnungsgemäß auf die UICC festgelegt werden. Im Allgemeinen, beträgt dieser Wert 2 oder 3.

Für OMA DM Wenn das Format für diesen Knoten falsch ist der Eintrag wird ignoriert und wird ein Fehler zurückgegeben werden, aber der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter.

<a href="" id="version"></a>**Version**  
Optional Bestimmt die Version des Protokolls SUPL verwenden. Für SUPL 1.0, legen Sie diesen Wert auf `1`. Für SUPL 2.0, legen Sie diesen Wert auf `2`. Der Standardwert ist 1.

<a href="" id="mccmncpairs"></a>**MCCMNCPairs**  
Erforderlich. Listen Sie aller die MCC-MNC-Paare im Besitz des Mobilfunkbetreiber auf. Diese Liste wird verwendet, um sicherzustellen, dass die UICC das Netzwerk entspricht und SUPL verwendet werden. Wenn die UICC und das Netzwerk nicht übereinstimmen, wird das Gerät verwendet den Speicherort Standarddienst und SUPL wird nicht verwendet.

Dieser Wert ist eine Zeichenfolge mit dem Format "(X1,Y1)(X2,Y2)... (Xn, Yn) ", in dem `X` ist eine MCC und `Y` ein MNC ist.

Für OMA DM Wenn das Format für diesen Knoten falsch ist der Eintrag wird ignoriert und wird ein Fehler zurückgegeben werden, aber der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter.

<a href="" id="highaccpositioningmethod"></a>**HighAccPositioningMethod**  
Optional Gibt die Positionierung-Methode, die der SUPL-Client für mobile stammt Position Anforderungen verwendet wird. Der Wert kann eine der folgenden ganzen Zahlen sein:

<table>
<colgroup>
<col width="15%" />
<col width="85%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Keine: Das Gerät wird standardmäßig verwendet Positionierung-Methode. In diesem Modus standardmäßig erhält die GNSS Unterstützung (Zeit Einfügung, grob Position Einfügung und Ephemeris Daten) aus dem Microsoft Positionierung-Dienst.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Mobile Station persönlicher: Das Gerät kontaktiert den H-SLP-Server, um eine Position zu erhalten. Die H-SLP ist die Berechnung der Position und an das Gerät zurückgegeben.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Mobile Station basiert: Ruft das Gerät vom Server H SLP Speicherort Beihilfe Daten (Almanach, Ephemeris Daten, Zeit und grob Ausgangsposition des Geräts) und das Gerät verwendet diese Informationen helfen GPS ein Update zu erhalten. Alle Position Berechnungen erfolgen im Gerät.</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Mobile Station eigenständige: Das Gerät ruft Unterstützung nach Bedarf aus der Speicherort von Microsoft.</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>OTDOA</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>AFLT</p></td>
</tr>
</tbody>
</table>

 

Der Standardwert ist 0. Die Standardmethode in Windows-Geräten bietet qualitativ hochwertige GNSS Positionierung für mobile stammt Position Anfragen ohne Laden des Mobilfunkbetreibers Netzwerk- oder Diensten unterstützt.

> **Wichtig**   Die Positionierung Mobile Station unterstützt, OTDOA und AFLT-Methoden müssen nur für Testzwecke konfiguriert werden.

 

Für OMA DM Wenn das Format für diesen Knoten falsch ist der Eintrag ignoriert und wird ein Fehler zurückgegeben; der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter

<a href="" id="locmasterswitchdependencynii"></a>**LocMasterSwitchDependencyNII**  
Optional Boolean-Wert. Gibt an, ob die Umschaltfläche Speicherort auf dem Bildschirm **Speicherort** in den **Einstellungen** auch zum Verwalten von SUPL Netzwerk initiierte Anforderungen für Speicherort (NI) verwendet wird. Wenn Sie der Wert auf 0 festgelegt ist, ist das Verhalten NI unabhängig von der aktuellen Position Umschaltfläche festlegen. Wenn der Wert auf 1 festgelegt ist, folgt das NI Verhalten der aktuellen Position Umschaltfläche festlegen aus. Der Standardwert ist 1.

Dieser Wert verwaltet die Einstellungen für SUPL und v2 UPL. Wenn ein Gerät für SUPL und V2 UPL konfiguriert ist, und diese Werte unterscheiden, wird die Einstellung SUPL immer verwendet werden.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Speicherort Umschaltfläche festlegen</th>
<th>LocMasterSwitchDependencyNII-Einstellung</th>
<th>Die anforderungsverarbeitung NI zulässig</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ein</p></td>
<td><p>0</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Ein</p></td>
<td><p>1</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Aus</p></td>
<td><p>0</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Aus</p></td>
<td><p>1</p></td>
<td><p>Nein (es sei denn, PrivacyOverride festgelegt ist)</p></td>
</tr>
</tbody>
</table>

 

Die folgenden Anforderungen Anwendung schlägt fehl, wenn die Umschaltfläche Speicherort auf deaktiviert festgelegt ist und dieser Wert auf 1 festgelegt ist:

-   `noNotificationNoVerification`

-   `notificationOnly`

-   `notificationAndVerficationAllowedNA`

-   `notificationAndVerficationDeniedNA`

Jedoch wenn `privacyOverride` festgelegt ist in der Nachricht der Ort zurückgegeben werden.

Wenn die Umschaltfläche Speicherort auf deaktiviert festgelegt ist, und dieser Wert auf 0 festgelegt ist, verhindert die Umschaltfläche Speicherort nicht SUPL Netzwerk initiierte Anforderungen aus arbeiten.

Für OMA DM das Format für diesen Knoten falsche werden der Eintrag ignoriert und wird ein Fehler zurückgegeben werden, aber der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter.

<a href="" id="nidefaulttimeout"></a>**NIDefaultTimeout**  
Optional Zeit in Sekunden an, denen die Anforderung Netzwerk initiierte Speicherort für den Benutzer beim Warten auf eine Antwort und vor dem Ausführen der Standardaktion angezeigt wird. Der Standardwert ist 30 Sekunden. Es wird ein Wert zwischen 20 und 60 Sekunden empfohlen.

Dieser Wert verwaltet die Einstellungen für SUPL und v2 UPL. Wenn ein Gerät für SUPL und V2 UPL konfiguriert ist, und diese Werte unterscheiden, wird die Einstellung SUPL immer verwendet werden.

<a href="" id="serveraccessinterval"></a>**ServerAccessInterval**  
Optional Ganzzahl Definiert die minimale Zeitspanne in Sekunden zwischen mobile stammt Anforderungen an den Server gesendet werden, um zu verhindern, Überlastung des Mobilfunkbetreibers Netzwerk an. Der Standardwert ist 60.

<a href="" id="rootcertificate"></a>**RootCertificate**  
Erforderlich. Gibt das Stammzertifikat für den Server H SLP an. Windows unterstützt keinen nicht sicheren Modus. Wenn dieser Knoten nicht angegeben ist, der Konfigurationsdienstanbieter schlägt fehl; möglicherweise keinen bestimmten Fehler zurück

<a href="" id="rootcertificate-name"></a>**RootCertificate/Name**  
Gibt den Namen des Stammzertifikats H SLP als Zeichenfolge in das Format *Name*CER.

<a href="" id="rootcertificate-data"></a>**RootCertificate-Daten**  
Die Base64-codiertes Blob des Stammzertifikats H SLP.

<a href="" id="rootcertificate2-name"></a>**RootCertificate2/Name**  
Gibt den Namen des Stammzertifikats H SLP als Zeichenfolge in das Format *Name*CER.

<a href="" id="rootcertificate2-data"></a>**RootCertificate2-Daten**  
Die base-64-codiertes Blob des Stammzertifikats H SLP.

<a href="" id="rootcertificate3-name"></a>**RootCertificate3/Name**  
Gibt den Namen des Stammzertifikats H SLP als Zeichenfolge in das Format *Name*CER.

<a href="" id="rootcertificate3-data"></a>**RootCertificate3-Daten**  
Die base-64-codiertes Blob des Stammzertifikats H SLP.

<a href="" id="v2upl1"></a>**V2UPL1**  
Erforderlich für V2 UPL für CDMA. Gibt die kontoeinstellungen für Ebene Benutzerstandort und IS-801 für CDMA an. Nur ein Konto wird zu einem bestimmten Zeitpunkt unterstützt.

<a href="" id="mpc"></a>**MPC**  
Optional Die Adresse des mobilen Positionierung Mittelpunkts (MPC), in der Format- *IP-Adresse*: *Portnummer*. Dieser Parameter ist erforderlich, nicht vertrauenswürdigen Modus des Vorgangs und der PDE-Parameter muss leer sein.

<a href="" id="pde"></a>**PDE**  
Optional Die Adresse der die Position Bestimmung Entität (PDE) in der Format- *IP-Adresse*: *Portnummer*. Dieser Parameter muss leer sein, nicht vertrauenswürdigen Modus des Vorgangs.

<a href="" id="positioningmethod-mr"></a>**PositioningMethod\_MR**  
Optional Gibt die Positionierung-Methode, die der SUPL-Client für mobile stammt Position Anforderungen verwendet wird. Der Wert kann eine der folgenden ganzen Zahlen sein:

<table>
<colgroup>
<col width="15%" />
<col width="85%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Keine: Das Gerät wird standardmäßig verwendet Positionierung-Methode. In diesem Modus standardmäßig erhält die GNSS Unterstützung (Zeit Einfügung, grob Position Einfügung und Ephemeris Daten) aus dem Microsoft Positionierung-Dienst.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Mobile Station persönlicher: Das Gerät kontaktiert den H-SLP-Server, um eine Position zu erhalten. Die H-SLP ist die Berechnung der Position und an das Gerät zurückgegeben.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Mobile Station basiert: Ruft das Gerät vom Server H SLP Speicherort Beihilfe Daten (Almanach, Ephemeris Daten, Zeit und grob Ausgangsposition des Geräts) und das Gerät verwendet diese Informationen helfen GPS ein Update zu erhalten. Alle Position Berechnungen erfolgen im Gerät.</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>Mobile Station eigenständige: Das Gerät ruft Unterstützung nach Bedarf aus der Speicherort von Microsoft.</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>AFLT</p></td>
</tr>
</tbody>
</table>

 

Der Standardwert ist 0. Die Standardmethode bietet hohe Qualität GNSS Positionierung für mobile stammt Position Anfragen ohne Laden des Mobilfunkbetreibers Netzwerk- oder Diensten unterstützt.

>  **Wichtig**   Mobile Station unterstützt und AFLT Positionierung Methoden muss nur für Testzwecke konfiguriert werden.

 

Für OMA DM Wenn das Format für diesen Knoten falsch ist der Eintrag wird ignoriert und wird ein Fehler zurückgegeben werden, aber der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter.

<a href="" id="locmasterswitchdependencynii"></a>**LocMasterSwitchDependencyNII**  
Optional Boolean-Wert. Gibt an, ob die Umschaltfläche Speicherort auf dem Bildschirm **Speicherort** in den **Einstellungen** auch zum Verwalten von Netzwerk-initiierte Anforderungen für Speicherort verwendet wird. Wenn Sie der Wert auf 0 festgelegt ist, ist das Verhalten NI unabhängig von der aktuellen Position Umschaltfläche festlegen. Wenn der Wert auf 1 festgelegt ist, folgt das NI Verhalten der aktuellen Position Umschaltfläche festlegen aus. Dieser Wert muss für CDMA-Geräte auf 1 festgelegt werden. Der Standardwert ist 1.

Dieser Wert verwaltet die Einstellungen für SUPL und v2 UPL. Wenn ein Gerät für SUPL und V2 UPL konfiguriert ist, und diese Werte unterscheiden, wird die Einstellung SUPL immer verwendet werden.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Speicherort Umschaltfläche festlegen</th>
<th>LocMasterSwitchDependencyNII-Einstellung</th>
<th>Die anforderungsverarbeitung NI zulässig</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ein</p></td>
<td><p>0</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Ein</p></td>
<td><p>1</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Aus</p></td>
<td><p>0</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Aus</p></td>
<td><p>1</p></td>
<td><p>Nein (es sei denn, PrivacyOverride festgelegt ist)</p></td>
</tr>
</tbody>
</table>

 

Die folgenden Anforderungen Anwendung schlägt fehl, wenn die Umschaltfläche Speicherort auf deaktiviert festgelegt ist und dieser Wert auf 1 festgelegt ist:

-   `noNotificationNoVerification`

-   `notificationOnly`

-   `notificationAndVerficationAllowedNA`

-   `notificationAndVerficationDeniedNA`

Jedoch wenn `privacyOverride` festgelegt ist in der Nachricht der Ort zurückgegeben werden.

Wenn die Umschaltfläche Speicherort auf deaktiviert festgelegt ist, und dieser Wert auf 0 festgelegt ist, verhindert die Umschaltfläche Speicherort nicht SUPL Netzwerk initiierte Anforderungen aus arbeiten.

Für OMA DM Wenn das Format für diesen Knoten falsch ist der Eintrag wird ignoriert und wird ein Fehler zurückgegeben werden, aber der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Parameter.

<a href="" id="applicationtypeindicator-mr"></a>**ApplicationTypeIndicator\_MR**  
Erforderlich. Dieser Wert muss immer auf festgelegt werden `00000011`.

<a href="" id="nidefaulttimeout"></a>**NIDefaultTimeout**  
Optional Zeit in Sekunden an, denen die Anforderung Netzwerk initiierte Speicherort für den Benutzer beim Warten auf eine Antwort und vor dem Ausführen der Standardaktion angezeigt wird. Der Standardwert ist 30 Sekunden. Es wird ein Wert zwischen 20 und 60 Sekunden empfohlen.

Dieser Wert verwaltet die Einstellungen für SUPL und v2 UPL. Wenn ein Gerät für SUPL und V2 UPL konfiguriert ist, und diese Werte unterscheiden, wird die Einstellung SUPL immer verwendet werden.

<a href="" id="serveraccessinterval"></a>**ServerAccessInterval**  
Optional Ganzzahl Definiert die minimale Zeitspanne in Sekunden zwischen mobile stammt Anforderungen an den Server gesendet werden, um zu verhindern, Überlastung des Mobilfunkbetreibers Netzwerk an. Der Standardwert ist 60.

## <a name="unsupported-nodes"></a>Nicht unterstützte Knoten


Die folgenden optionalen Knoten werden nicht auf Windows-Geräten unterstützt.

-   ProviderID

-   Name

-   PrefConRef

-   ToConRef

-   ToConRef /&lt;X&gt;

-   ToConRef /&lt;X&gt;/ConRef

-   AddrType

Wenn die Anwendung Konfiguration versucht, festlegen, löschen oder Abfragen diese Knoten, wird eine Antwort, die angibt, dass dieser Knoten nicht implementiert ist über OMA DM zurückgegeben. In OMA-Clientbereitstellung die Anforderung an diese Knotensatz ignoriert, und der Konfigurationsdienstanbieter weiterhin verarbeitet den Rest der Knoten.

Wenn ein Mobilfunkbetreiber erfordert die Kommunikation mit den H-SLP über eine bestimmte Verbindung statt eine standardmäßige Mobilfunk Verbindung erfolgen soll, muss dies mithilfe von konfiguriert werden die [CM\_CellularEntries Konfigurationsdienstanbieter](cm-cellularentries-csp.md) und die [CM\_ProxyEntries Konfigurationsdienstanbieter](cm-proxyentries-csp.md) H SLP-Server mit der erforderlichen Verbindung zuordnen.

## <a name="oma-client-provisioning-examples"></a>Beispiele für OMA-Clientbereitstellung


Hinzufügen von neuen Konfigurationsinformationen für einen Server H SLP für SUPL. Werte in Kursivschrift müssen mit der richtigen Einstellungen für das Netzwerk Mobilfunkbetreiber ersetzt werden. Ein gültiges binäres Blob muss für den Stamm Zertifikat Datenwert eingeschlossen werden.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<wap-provisioningdoc>
  <characteristic type="SUPL">
    <characteristic type="SUPL1">
      <parm name="Addr" value="supl.abc.def.example.com: 7777" />
      <characteristic type="Ext">
      <characteristic type="Microsoft">
      <characteristic type="RootCertificate">
        <parm name="Name" value="certName.cer" />
        <parm name="Data" value="" datatype="binary"/>
      </characteristic>
         <parm name="MCCMNCPairs" value="(111,000)(222,111)(333,333)(444,222)" />
         <parm name="HighAccPositioningMethod" datatype="integer" value="0" />
         <parm name="LocMasterSwitchDependencyNII" datatype="integer" value="1" />
      </characteristic>
      </characteristic>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
```

Hinzufügen von demselben Gerät eine SUPL und ein V2 UPL Konto. Werte in Kursivschrift müssen mit der richtigen Einstellungen für das Netzwerk Mobilfunkbetreiber ersetzt werden. Ein gültiges binäres Blob muss für den Stamm Zertifikat Datenwert eingeschlossen werden.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<wap-provisioningdoc>
  <characteristic type="SUPL">
    <characteristic type="V2UPL1">
      <parm name="MPC" value="192.0.2.1:7777" />
      <parm name="PDE" value="192.0.2.1:7778" />
      <parm name="PositioningMethod_MR" datatype="integer" value="1" />
    </characteristic>
    <characteristic type="SUPL1">
      <parm name="Addr" value="supl.abc.def.example.com:7777" />
      <characteristic type="Ext">
      <characteristic type="Microsoft">
      <characteristic type="RootCertificate">
        <parm name="Name" value="certName.cer" />
        <parm name="Data" value="" datatype="binary"/>
      </characteristic>
         <parm name="MCCMNCPairs" value="(111,000)(222,111)(333,333)(444,222)" />
         <parm name="HighAccPositioningMethod" datatype="integer" value="2" />
         <parm name="LocMasterSwitchDependencyNII" datatype="integer" value="1" />
      </characteristic>
      </characteristic>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
```

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Hinzufügen eines Kontos SUPL zu einem Gerät. Werte in Kursivschrift müssen mit der richtigen Einstellungen für das Netzwerk Mobilfunkbetreiber ersetzt werden. Ein gültiges binäres Blob muss für den Stamm Zertifikat Datenwert eingeschlossen werden.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
    <SyncBody>
        <Add>
            <CmdID>Add FQDN</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Addr</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>supl.abc.def.example.com:2222</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>Add MCCMNC</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Ext/Microsoft/MCCMNCPairs</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>(111,000)(222,111)(333,333)(444,222)</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>Add HighAccPositioningMethod</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Ext/Microsoft/HighAccPositioningMethod</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>2</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>Add LocMasterSWDepend</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Ext/Microsoft/LocMasterSwitchDependencyNII</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>Add Cert name</CmdID>

            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Ext/Microsoft/RootCertificate/Name</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>certName.cer</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>Add Cert data - 200</CmdID>

            <Item>
                <Target><LocURI>./Vendor/MSFT/SUPL/SUPL1/Ext/Microsoft/RootCertificate/Data</LocURI></Target>
                <Meta>
                <Format xmlns="syncml:metinf">b64</Format>
                </Meta>
                <Data></Data>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierte Elemente


In der folgenden Tabelle werden die benutzerdefinierten Microsoft-Elemente, die dieser Konfigurationsdienstanbieter für OMA-Clientbereitstellung unterstützt veranschaulicht.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elemente</th>
<th>Verfügbar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Parameter-Abfrage</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Merkmal-Abfrage</p></td>
<td><p>Ja</p>
<p>Rekursive Abfrage: Nein</p>
<p>Abfragen auf oberster Ebene Ebene: Nein</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






