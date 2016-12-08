---
title: DiagnosticLog CSP
description: DiagnosticLog CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F76E0056-3ACD-48B2-BEA1-1048C96571C3
ms.openlocfilehash: 5059164463f66d871a009dc26d506f6d7b99e5f0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diagnosticlog-csp"></a>DiagnosticLog CSP


Der DiagnosticLog Konfigurationsdienstanbieter (CSP) wird zum Generieren und Sammeln von Diagnoseinformationen vom Gerät verwendet: Event Tracing for Windows (ETW) Protokolldateien und aktuelle MDM Zustand des Geräts konfiguriert.

DiagnosticLog CSP unterstützt den folgenden Typ der Protokollierung von Ereignis:

-   Collection-basierter Protokollierung
-   Channel-basierter Protokollierung

### <a name="collector-based-tracing"></a>Collection-basierter Protokollierung

Diese Art von Ereignis Tracing sammelt Ereignisdaten gleichzeitig aus einer Sammlung von registrierten ETW-Anbieter.

Ein Ereignissammlung ist ein Container der registrierten ETW-Anbieter. Benutzer können hinzufügen oder Löschen einen Collector Knoten und registrieren oder Aufheben der Registrierung mehrere Anbieter in diese Sammlung.

Die ***CollectorName*** muss innerhalb der CSP eindeutig sein und muss einen gültigen Ereignisnamen Kanal oder eine GUID-Anbieter nicht.

DiagnosticLog CSP eine Protokolldatei für jeden Knoten Collector verwaltet und die Protokolldatei wird überschrieben, wenn Sie ein Befehl zum Starten erneut auf demselben Knoten Collector ausgelöst wird.

Für jeden Knoten Collector kann der Benutzer:

-   Starten Sie oder beenden Sie die Sitzung mit allen registrierten und aktiviert Anbietern
-   Sitzungsstatus Abfrage
-   Änderung Trace Log Dateimodus
-   Änderung Trace maximale Größe der Protokolldatei

Die Konfigurationen melden Dateimodus und maximale Größe der Protokolldatei wird nicht wirksam während Ablaufverfolgungssitzung ausgeführt wird. Diese werden angewendet, wenn Benutzer die aktuelle Sitzung beendet und dann erneut für diese Sammlung gestartet.

Für jeden registrierten Anbieter in dieser Collector kann der Benutzer:

-   Geben Sie Schlüsselwörter ein, um Ereignisse von diesem Anbieter filtern
-   Ändern Sie Ablaufverfolgungsebene zum Filtern von Ereignissen von diesem Anbieter
-   Aktivieren Sie oder deaktivieren Sie des Anbieters in die Ablaufverfolgungssitzung

Die Änderungen auf **Status**, **Schlüsselwörter** und **TraceLevel** wirkt sich unmittelbar während Ablaufverfolgungssitzung ausgeführt wird.

> **Hinweis**  Microsoft-WindowsPhone-Enterprise-Diagnose-Anbieter (GUID - 3da494e4-0fe2-415C-b895-fb5265c5c83b) verfügt über die erforderlichen Debug-Ressourcendateien integrierten Windows-Betriebssystem, wodurch die Protokolldateien auf dem Remotecomputer decodiert werden können. Eine beliebige andere Protokolle möglicherweise nicht die erforderlichen zum Decodieren Debugressourcen.

 

### <a name="channel-based-tracing"></a>Channel-basierter Protokollierung

Der Typ des Ereignisses Tracing exportiert Ereignisdaten aus einem bestimmten Kanal. Dies ist nur auf dem Desktop unterstützt.

Benutzer können hinzufügen oder Löschen einen DDE-Kanal-Knoten mithilfe der vollständige Name, beispielsweise Microsoft-Windows-AppModel-Laufzeit/Admin.

DiagnosticLog CSP pflegt eine Protokolldatei für jeden Knoten DDE-Kanal und die Protokolldatei wird überschrieben, wenn Sie ein Befehl zum Starten erneut auf demselben DDE-Kanal Knoten ausgelöst wird.

Für jeden Knoten DDE-Kanal kann der Benutzer:

-   Exportieren von DDE-Kanal Ereignisdaten in einer Protokolldatei (EVTX)
-   Aktivieren Sie oder deaktivieren Sie den Kanal aus Ereignisprotokolldienst zulassen oder verweigern Ereignisdaten in den DDE-Kanal geschrieben wird
-   Angeben einer XPath-Abfrage zum Filtern von Ereignissen beim Exportieren der Daten der DDE-Kanal-Ereignis

Weitere Informationen zur Verwendung von DiagnosticLog zum Erfassen von Protokollen Remote von einem PC oder Mobilgerät finden Sie unter [MDM Diagnostizieren von Fehlern in Windows 10](diagnose-mdm-failures-in-windows-10.md).

Es folgen die Links zu den DDFs:

-   [DiagnosticLog CSP Version 1.2](diagnosticlog-ddf.md#version-1-2)
-   [DiagnosticLog CSP Version 1.3](diagnosticlog-ddf.md#version-1-3)

Das folgende Diagramm zeigt den DiagnosticLog Konfiguration-Dienstanbieter im Strukturformat dar.

![Diagnosticlog Csp Diagramm](images/provisioning-csp-diagnosticlog.png)

<a href="" id="--vendor-msft-diagnosticlog"></a>**./Vendor/MSFT/DiagnosticLog**  
Der Stammknoten für den Dienstanbieter für DiagnosticLog-Konfiguration.

Die folgenden Schritte beschreiben den Prozess zum Erfassen von Diagnosen mithilfe dieser CSP.

1.  Geben Sie eine *CollectorName* für den Container der Ziel-ETW-Anbieter.
2.  (Optional) Protokollierung und melden Sie Parameter der Datei mithilfe der folgenden Optionen:

    -   **TraceLogFileMode**
    -   **LogFileSizeLimitMB**

    Jede dieser werden weiter unten in diesem Thema beschrieben.

3.  Geben Sie einen oder mehrere Ziel-ETW-Anbieter an, durch Bereitstellen der *Felder ProviderGUID* zum Hinzufügen von EtwLog-Kollektoren*Vorgang/CollectorName*/Providers/*"ProviderGUID"*.
4.  (Optional) Protokollierung und melden Sie Parameter der Datei mithilfe der folgenden Optionen:

    -   **TraceLevel**
    -   **Schlüsselwörter**

    Jede dieser werden weiter unten in diesem Thema beschrieben.

5.  Starten der Protokollierung mit **TraceControl** EXECUTE-Befehl "START"
6.  Führen Sie Aktionen auf dem Zielcomputer, die Aktivität in den Protokolldateien generiert.
7.  Beenden der Protokollierung mit **TraceControl** EXECUTE Befehl "BEENDEN"
8.  Sammeln Sie die Protokolldatei befindet sich der `%temp%` Ordner mit der in [einer Protokolldatei lesen](#reading-a-log-file) beschriebenen Methode

<a href="" id="etwlog"></a>**EtwLog**  
Knoten, das Fehler Tracing für Windows-Ereignisprotokoll enthalten soll.

Der unterstützte Vorgang ist abrufen.

<a href="" id="etwlog-collectors"></a>**EtwLog-Kollektoren**  
Inneren Knoten interior dynamischen untergeordneten Knoten für aktiven Anbieter enthalten.

Der unterstützte Vorgang ist abrufen.

<a href="" id="etwlog-collectors-collectorname"></a>**EtwLog-Kollektoren / ***_CollectorName_**  
Dynamische Knoten zur Darstellung des aktiven Collector Konfiguration.

Unterstützte Vorgänge sind hinzufügen, löschen, und erhalten möchten.

Fügen Sie eine Sammlung hinzu

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Add>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

Löschen einer Sammlung

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Delete>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement</LocURI>
                </Target>
            </Item>
        </Delete>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-collectors-collectorname-tracestatus"></a>* *EtwLog-Kollektoren/*CollectorName*/TraceStatus**  
Gibt an, ob der aktuelle Status der Protokollierung ausgeführt wird.

Der Datentyp ist eine ganze Zahl.

Der unterstützte Vorgang ist Get.

In der folgenden Tabelle sind die möglichen Werte:

| Wert | Beschreibung |
|-------|-------------|
| 0     | Beendet     |
| 1     | Schritte     |

 

<a href="" id="etwlog-collectors-collectorname-tracelogfilemode"></a>* *EtwLog/Kollektoren/*CollectorName*/TraceLogFileMode**  
Gibt den Dateimodus Protokollierung melden Sie sich an.

Der Datentyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Tabelle sind die möglichen Werte aufgeführt:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EVENT_TRACE_FILE_MODE_SEQUENTIAL (0 X 00000001)</p></td>
<td><p>Sequenziell Ereignisse in einer Protokolldatei geschrieben werden; beendet, wenn die Datei die maximale Größe erreicht.</p></td>
</tr>
<tr class="even">
<td><p>EVENT_TRACE_FILE_MODE_CIRCULAR (0 X 00000002)</p></td>
<td><p>Ereignisse in einer Protokolldatei geschrieben. Nachdem die Datei die maximale Größe erreicht, werden die ältesten Ereignisse mit eingehenden Ereignisse ersetzt.</p></td>
</tr>
</tbody>
</table>

 

<a href="" id="etwlog-collectors-collectorname-tracecontrol"></a>* *EtwLog/Kollektoren/*CollectorName*/TraceControl**  
Gibt die Protokollierung und den Zustand des Berichts-Aktion.

Der Datentyp ist eine Zeichenfolge.

In der folgenden Tabelle sind die möglichen Werte aufgeführt:

| Wert | Beschreibung        |
|-------|--------------------|
| STARTEN | Starten Sie melden Sie sich Protokollierung. |
| BEENDEN  | Melden Sie sich Protokollierung stoppen   |

 

Der unterstützte Vorgang ist ausführen.

Nachdem Sie eine Aufgabe Protokollierung hinzugefügt haben, können Sie eine Verfolgung durch Ausführen eines Befehls Ausführen auf diesem Knoten mit dem Wert START starten.

Einen Execute-Befehl ausführen, um die Ablaufverfolgung beenden möchten, auf diesem Knoten mit dem Wert BEENDEN.

Starten von Ablaufverfolgungsprotokollen für die Sammlung

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/TraceControl</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>START</Data>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

Collector Trace Protokollierung beenden

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/TraceControl</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>STOP</Data>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-collectors-collectorname-logfilesizelimitmb"></a>* *EtwLog-Kollektoren/*CollectorName*/LogFileSizeLimitMB**  
Die maximale Größe der Protokolldatei, festgelegt in MB.

Der Datentyp ist eine ganze Zahl.

Gültige Werte sind 1 und 2048. Der Standardwert ist 4.

Unterstützte Vorgänge sind Get und ersetzen.

<a href="" id="etwlog-collectors-collectorname-providers"></a>* *EtwLog-Kollektoren/*CollectorName*/Providers**  
Inneren Knoten interior dynamischen untergeordneten Knoten für aktiven Anbieter enthalten.

Der unterstützte Vorgang ist abrufen.

<a href="" id="etwlog-collectors-collectorname-providers-providerguid"></a>* *EtwLog-Kollektoren/*CollectorName*/Anbieter / ***_"ProviderGUID"_**  
Dynamische Knoten zur Darstellung des aktiven Anbieterkonfiguration pro Anbieter-GUID.

> **Hinweis**  Microsoft-WindowsPhone-Enterprise-Diagnose-Anbieter (GUID - 3da494e4-0fe2-415C-b895-fb5265c5c83b) verfügt über die erforderlichen Debug-Ressourcendateien integrierten Windows-Betriebssystem, wodurch die Protokolldateien auf dem Remotecomputer decodiert werden können. Eine beliebige andere Protokolle möglicherweise nicht die erforderlichen zum Decodieren Debugressourcen.

 

Unterstützte Vorgänge sind hinzufügen, löschen, und erhalten möchten.

Hinzufügen eines Dienstanbieters

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Add>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

Löschen eines Providers

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Delete>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b</LocURI>
                </Target>
            </Item>
        </Delete>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-collectors-collectorname-providers-provderguid-tracelevel"></a>**EtwLog-Kollektoren/* CollectorName*/Providers/*ProvderGUID*/TraceLevel**  
Gibt die Detailebene im Ablaufverfolgungsprotokoll.

Der Datentyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Tabelle sind die möglichen Werte aufgeführt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1 – TRACE_LEVEL_CRITICAL</p></td>
<td><p>Ungewöhnliche beenden oder Beendigung Ereignisse</p></td>
</tr>
<tr class="even">
<td><p>2 – TRACE_LEVEL_ERROR</p></td>
<td><p>Schwerwiegender Fehlerereignisse</p></td>
</tr>
<tr class="odd">
<td><p>3 – TRACE_LEVEL_WARNING</p></td>
<td><p>Warnereignisse wie Zuweisung mit Fehlern</p></td>
</tr>
<tr class="even">
<td><p>4 – TRACE_LEVEL_INFORMATION</p></td>
<td><p>Nicht-Fehler Ereignisse wie Eingangs- oder Ausgangsanimationen</p></td>
</tr>
<tr class="odd">
<td><p>5 – TRACE_LEVEL_VERBOSE</p></td>
<td><p>Ausführliche Informationen</p></td>
</tr>
</tbody>
</table>

 

Legen Sie Provider **TraceLevel**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b/TraceLevel</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-collectors-collectorname-providers-provderguid-keywords"></a>**EtwLog/Kollektoren/* CollectorName*/Providers/*ProvderGUID*/Keywords**  
Gibt die Anbieter-Schlüsselwörter, die als MatchAnyKeyword für diesen Anbieter verwendet werden.

der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get und ersetzen.

Standardwert ist 0, d. h., kein Keyword.

Provider **Schlüsselwörter** abrufen

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b/Keywords
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Final/> 
  </SyncBody>
</SyncML>
```

Legen Sie Provider **Schlüsselwörter**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>4</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b/Keywords
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>12345678FFFFFFFF</Data>
      </Item>
    </Replace>
    <Final/> 
  </SyncBody>
</SyncML>
```

<a href="" id="etwlog-collectors-collectorname-providers-provderguid-state"></a>**EtwLog-Kollektoren/* CollectorName*/Providers/*ProvderGUID*/State**  
Gibt an, ob dieses Anbieters in die Ablaufverfolgungssitzung aktiviert ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgänge sind Get und ersetzen. Diese Änderung wird während der aktiven Ablaufverfolgungssitzung effektiv sein.

In der folgenden Tabelle werden die möglichen Werte aufgelistet. Standardwert ist TRUE.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TRUE</p></td>
<td><p>Anbieter ist in die Ablaufverfolgungssitzung aktiviert.</p></td>
</tr>
<tr class="even">
<td><p>FALSE</p></td>
<td><p>Anbieter ist in die Ablaufverfolgungssitzung deaktiviert.</p></td>
</tr>
</tbody>
</table>

 

Legen Sie Provider **Zustand**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/DeviceManagement/Providers/3da494e4-0fe2-415C-b895-fb5265c5c83b/State</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">bool</Format>
                </Meta>
                <Data>false</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-channels"></a>**EtwLog-Kanäle**  
Interior-Knoten, interior dynamischen untergeordneten Knoten registrierten Kanäle enthalten.

Der unterstützte Vorgang ist abrufen.

<a href="" id="etwlog-channels-channelname"></a>**EtwLog-Kanäle / ***_ChannelName_**  
Dynamische Knoten zur Darstellung von eines registrierten Kanals. Der Knotenname muss ein gültiger Windows-Ereignisprotokoll Channel Name, beispielsweise "Microsoft-Client-Lizenzierung-Plattform % 2FAdmin" sein.

Unterstützte Vorgänge sind hinzufügen, löschen, und erhalten möchten.

Hinzufügen eines Kanals

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Add>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

Löschen eines Kanals

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Delete>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin</LocURI>
                </Target>
            </Item>
        </Delete>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-channels-channelname-export"></a>* *EtwLog-Kanäle/*ChannelName*/Export**  
Knoten, der den Befehl zum Exportieren von DDE-Kanal Ereignisdaten in die Protokolldatei zu lösen.

Der unterstützte Vorgang ist ausführen.

Exportieren von Daten von DDE-Kanal-Ereignis

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin/Export</LocURI>
                </Target>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-channels-channelname-filter"></a>* *EtwLog-Kanäle/*ChannelName*/Filter**  
Gibt die XPath-Abfragezeichenfolge zum Filtern der Ereignisse beim Exportieren.

Der Datentyp ist eine Zeichenfolge.

Unterstützte Vorgänge sind Get und ersetzen.

Standardwert ist die leere Zeichenfolge.

Abrufen von DDE-Kanal **Filter**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin/Filter</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="etwlog-channels-channelname-state"></a>* *EtwLog-Kanäle/*ChannelName*/State**  
Gibt an, ob der Kanal aktiviert oder deaktiviert ist.

Der Datentyp ist ein boolescher Wert.

Unterstützte Vorgänge sind Get und ersetzen.

In der folgenden Tabelle sind die möglichen Werte aufgeführt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TRUE</p></td>
<td><p>DDE-Kanal ist aktiviert.</p></td>
</tr>
<tr class="even">
<td><p>FALSE</p></td>
<td><p>DDE-Kanal ist deaktiviert.</p></td>
</tr>
</tbody>
</table>

 

Abrufen von DDE-Kanal **Zustand**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin/State</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

Set-Kanal **Zustand**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Client-Licensing-Platform%2FAdmin/State</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">bool</Format>
                </Meta>
                <Data>false</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="devicestatedata"></a>**DeviceStateData**  
In Version 1.3 CSP in Windows 10, Version 1607 hinzugefügt. Knoten für alle Arten von Gerät Zustandsdaten, die verfügbar gemacht werden.

<a href="" id="devicestatedata-mdmconfiguration"></a>**DeviceStateData/MdmConfiguration**  
In Version 1.3 CSP in Windows 10, Version 1607 hinzugefügt. Löst das Gerät Management Zustandsdaten mit SNAP einrasten.

Der unterstützte Wert ist ausführen.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Exec>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/DiagnosticLog/DeviceStateData/MdmConfiguration</LocURI>
        </Target>
        <Meta>
           <Format xmlns="syncml:metinf">chr</Format>
        </Meta>
        <Data>SNAP</Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="filedownload"></a>**FileDownload**  
Der Knoten, der untergeordnete Knoten für Log File Transport Protokolle und die entsprechenden Aktionen enthalten.

<a href="" id="filedownload-dmchannel"></a>**FileDownload/DMChannel**  
Knoten untergeordnete Knoten mithilfe der DDE-Kanal DM für Transportprotokoll enthalten.

<a href="" id="filedownload-dmchannel-filecontext"></a>**FileDownload/DMChannel / ***_FileContext_**  
Dynamische interior Knoten, die pro stellt melden Kontext.

<a href="" id="filedownload-dmchannel-filecontext-blocksizekb"></a>* *FileDownload/DMChannel/*FileContext*/BlockSizeKB**  
Legt das Protokoll lesen Puffers in KB.

Der Datentyp ist eine ganze Zahl.

Gültige Werte sind 1-16. Der Standardwert ist 4.

Unterstützte Vorgänge sind Get und ersetzen.

**BlockSizeKB** festlegen

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockSizeKB</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

Abrufen von **BlockSizeKB**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockSizeKB</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="filedownload-dmchannel-filecontext-blockcount"></a>* *FileDownload/DMChannel/*FileContext*/BlockCount**  
Stellt die Anzahl der insgesamt Lese-Block für die Protokolldatei.

Der Datentyp ist eine ganze Zahl.

Der einzige unterstützte Vorgang ist Get.

Abrufen von **BlockCount**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockCount</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="filedownload-dmchannel-filecontext-blockindextoread"></a>* *FileDownload/DMChannel/*FileContext*/BlockIndexToRead**  
Stellt die Startposition Lese-Block.

Der Datentyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get und ersetzen.

**BlockIndexToRead** auf 0 festgelegt

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockIndexToRead</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>0</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

**BlockIndexToRead** wird auf 1 festgelegt.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockIndexToRead</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="filedownload-dmchannel-filecontext-blockdata"></a>* *FileDownload/DMChannel/*FileContext*/BlockData**  
Der Datentyp ist Base64 an.

Der einzige unterstützte Vorgang ist Get.

Abrufen von **BlockData**

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel/DeviceManagement/BlockData</LocURI>
                </Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

<a href="" id="filedownload-dmchannel-filecontext-datablocks"></a>* *FileDownload/DMChannel/*FileContext*/DataBlocks**  
Der Knoten für den Zugriffsschutz die ausgewählte Protokoll an den Server DM übertragen.

<a href="" id="filedownload-dmchannel-filecontext-datablocks-blocknumber"></a>* *FileDownload/DMChannel/*FileContext*/DataBlocks / ***_BlockNumber_**  
Der Datentyp ist Base64.

Der einzige unterstützte Vorgang ist Get.

## <a name="reading-a-log-file"></a>Lesen einer Protokolldatei


1.  Auflisten der Protokolldatei unter **./Vendor/MSFT/DiagnosticLog/FileDownload/DMChannel**
2.  Wählen Sie eine Protokolldatei im Resultset (Aufzählung)
3.  Festlegen Sie **BlockSizeKB** pro Server DM Nutzlast Einschränkung.
4.  Abrufen von **BlockCount** insgesamt lesen Anforderung bestimmen
5.  Set **BlockIndexToRead** lesen Anfangspunkt nicht initialisiert werden
6.  Rufen Sie **BlockData** für Upload Protokoll blockieren
7.  **BlockIndexToRead** erhöhen
8.  Wiederholen Sie Schritt 5 bis 7, bis **BlockIndexToRead == (BlockIndexToRead – 1)**

 

 






