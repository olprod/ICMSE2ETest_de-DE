---
title: Struktur der OMA DM Dateien zur Bereitstellung
description: Struktur der OMA DM Dateien zur Bereitstellung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7bd3ef57-c76c-459b-b63f-c5a333ddc2bc
ms.openlocfilehash: e4d8c4baf6d1fd9217af02d064a3e1fda482bb59
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="structure-of-oma-dm-provisioning-files"></a>Struktur der OMA DM Dateien zur Bereitstellung

OMA DM Befehle werden zwischen dem Server und dem Client-Gerät in Nachrichten übertragen. Eine Nachricht kann einen oder mehrere Befehle enthalten. Eine Liste der unterstützten Befehle finden Sie unter der Tabelle in [der OMA DM-Protokoll unterstützen](oma-dm-protocol-support.md).

Eine Nachricht DM ist ein XML-Dokument. Die Struktur und den Inhalt des Dokuments wird im Protokoll OMA DM Darstellung definiert (OMA-SyncML-DevInfo-DTD-V1\_1\_2-20030505-D.dtd) von der [OMA Website](http://go.microsoft.com/fwlink/p/?LinkId=526900)verfügbar.

Jede Nachricht besteht aus einer Kopfzeile, durch das SyncHdr-Element angegeben und Nachrichtentext, durch das SyncBody-Element angegeben.

Die folgende Tabelle enthält die OMA DM-Versionen, die unterstützt werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Version</th>
<th>Format</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OMA DM Version 1.1.2</p></td>
<td><p><code>&lt;SyncML xmlns='SYNCML:SYNCML1.1'&gt;</code></p>
<p><code>&lt;/SyncML&gt;</code></p></td>
</tr>
<tr class="even">
<td><p>OMA DM Version 1.2</p></td>
<td><p><code>&lt;SyncML xmlns='SYNCML:SYNCML1.2'&gt;</code></p>
<p><code>&lt;/SyncML&gt;</code></p></td>
</tr>
</tbody>
</table>

 

## <a name="file-format"></a>Dateiformat

Das folgende Beispiel zeigt die allgemeine Struktur des XML-Dokuments durch den Server mithilfe von OMA DM Version 1.2.1 nur zur Veranschaulichung gesendet. Die ersten XML-Paketen zwischen Client und Server ausgetauscht konnte zusätzliche XML-Tags enthalten. Eine ausführliche Beschreibung und Beispiele für diese Pakete finden Sie in der Spezifikation [OMA Gerät Management Protocol 1.2.1 (engl.)](http://go.microsoft.com/fwlink/p/?LinkId=526902) .

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncHdr>
      <VerDTD>1.2</VerDTD>
      <VerProto>DM/1.2</VerProto>
      <SessionID>1</SessionID>
      <MsgID>1</MsgID>
      <Target>
         <LocURI>{unique device ID}</LocURI>
      </Target>
      <Source>
         <LocURI>https://www.contoso.com/mgmt-server</LocURI>
      </Source>
   </SyncHdr>
   <SyncBody>
      <!-- query a device OS system version -->
      <Get>
         <CmdID>2</CmdID>
         <Item>
            <Target>
               <LocURI>./DevDetail/SwV</LocURI>
            </Target>
         </Item>
      </Get>
      <!-- Update device policy -->
      
      <Final />
   </SyncBody>
</SyncML>
```

## <a name="synchdr-element"></a>SyncHdr-element

SyncHdr umfasst die folgende Informationen:

-   Dokumentieren Sie Type Definition (DTD) und das Protokoll Versionsnummern

-   Bezeichner Sitzung und Nachricht. Jede Nachricht in der gleichen Sitzung DM benötigen eine unterschiedliche MsgID.

-   Nachricht Quell- und Zielserver Uniform Resource Identifiers (URIs)

-   Anmeldeinformationen für die Authentifizierung

Diese Informationen werden, vom Client-Gerät verwendet, um die Sitzung DM ordnungsgemäß zu verwalten.


**Codebeispiel**

Im folgenden Codebeispiel wird der Kopfzeile Komponente einer DM Nachricht. In diesem Fall wird der OMA DM Version 1.2 lediglich als Beispiel verwendet.

> **Hinweis**   Die &lt;LocURI&gt; Wert des Knotens für die &lt;Quelle&gt; Element in der SyncHdr des Pakets DM Gerät generierte sollte der Wert der identisch sein. / DevInfo/DevID. Weitere Informationen zu DevID finden Sie unter [DevInfo Konfiguration-Dienstanbieter](devinfo-csp.md).

 

``` syntax
<SyncHdr>
   <VerDTD>1.2</VerDTD>
   <VerProto>DM/1.2</VerProto>
   <SessionID>1</SessionID>
   <MsgID>1</MsgID>
   <Target>
      <LocURI>{unique device ID}</LocURI>
   </Target>
   <Source>
      <LocURI>https://www.contoso.com/mgmt-server</LocURI>
   </Source>
</SyncHdr>
```

## <a name="syncbody-element"></a>SyncBody-element

SyncBody enthält eine oder mehrere DM-Befehle. Die SyncBody kann mehrere DM Befehle enthalten. Jeder Befehl muss auf einen anderen CmdID-Wert aufweisen.

**Codebeispiel**

Das folgende Beispiel zeigt die Komponente Textkörper einer Nachricht DM. In diesem Beispiel SyncBody enthält nur ein Befehl und abrufen. Dies wird angegeben, indem die &lt;endgültigen /&gt; Tag, das tritt auf, unmittelbar nach dem Abbruch Tag für den Befehl Get.

``` syntax
<SyncBody>
   <!-- query device OS software version -->
   <Get>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>./DevDetail/SwV</LocURI>
         </Target>
      </Item>
   </Get>
   <Final />
</SyncBody>
```

Bei Verwendung von SyncML für die Bereitstellung von OMA DM kann eine LocURI in SyncBody haben eine "." als den Segmentnamen einer gültigen nur in das erste Segment. Jedoch ein "." ist kein gültiger Segmentname für die anderen Segmente. Beispielsweise die folgenden LocURI ist ungültig, da das Segment Name des siebten Segments ist ein ".".

```
<LocURI>./Vendor/MSFT/Registry/HKLM/Security/./Test</LocURI>
```

## <a name="update-device-settings-example"></a>Update Device Einstellungen-Beispiel

Der Befehl Ersetzen wird verwendet, um eine Einstellung für die Geräte zu aktualisieren.

Im folgenden Beispiel wird veranschaulicht, wie den Replace-Befehl verwenden, um eine Einstellung für die Geräte zu aktualisieren.

``` syntax
<SyncHdr>
   <VerDTD>1.2</VerDTD>
   <VerProto>DM/1.2</VerProto>
   <SessionID>1</SessionID>
   <MsgID>1</MsgID>
   <Target>
      <LocURI>{unique device ID}</LocURI>
   </Target>
   <Source>
      <LocURI>https://www.contoso.com/mgmt-server</LocURI>
   </Source>
</SyncHdr>
<SyncBody>
   <!-- update device setting -->
   <Replace>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>./Vendor/MSFT/PolicyManager/My/DeviceLock/MinDevicePasswordLength</LocURI>
         </Target>
         <Meta>
            <Type xmlns="syncml:metinf">text/plain</Type>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>6</Data>
      </Item>
   </Replace>
   <Final />
</SyncBody>
```

 






