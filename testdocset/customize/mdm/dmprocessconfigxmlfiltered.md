---
title: DMProcessConfigXMLFiltered-Funktion
description: Telefoneinstellungen konfiguriert mithilfe von OMA Client Provisioning XML.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
Search.Refinement.TopicID: "184"
ms.assetid: 31D79901-6206-454C-AE78-9B85A3B3487F
keywords: DMProcessConfigXMLFiltered-Funktion
topic_type: apiref
api_name: DMProcessConfigXMLFiltered
api_location: dmprocessxmlfiltered.dll
api_type: DllExport
ms.openlocfilehash: fdb73fa49b41e4b1f49982906574370f118b7913
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dmprocessconfigxmlfiltered-function"></a>DMProcessConfigXMLFiltered-Funktion

> **Wichtige**  
Die Verwendung dieser Funktion für automatische Datenkonfiguration (ADC) ist in Windows Phone 8.1 veraltet. Weitere Informationen zu den neuen Prozess für die Bereitstellung einer Konfiguration finden Sie unter [Konfiguration von Diensten](https://msdn.microsoft.com/en-us/library/windows/hardware/dn757424) . Diese Funktion ist jedoch weiterhin unterstützt, für andere OEM verwendet.


Konfiguriert die telefoneinstellungen mithilfe von OMA Client Provisioning XML. Die Verwendung dieser Funktion ist auf den folgenden Szenarien streng begrenzt.

-   Hinzufügen von dynamischen Anmeldeinformationen für die Bereitstellung von OMA-Client.

-   Fertigung Test Applications. Diese Anwendungen und der unterstützenden Treiber müssen aus den Telefonen entfernt werden, bevor sie verkauft werden.

Microsoft empfiehlt, dass diese Funktion nicht verwendet wird, so konfigurieren Sie die folgenden Arten von Einstellungen.

-   Sicherheitseinstellungen, die mithilfe von CertificateStore SecurityPolicy und RemoteWipe, konfiguriert werden, es sei denn, sie mit der OMA DM oder OMA-Clientbereitstellung Sicherheitsrichtlinien verknüpft sind.

-   Nicht-Mobilfunk datenverbindungseinstellungen (beispielsweise Hotspot-Einstellungen).

-   File Systemdateien und Registrierungseinträge, es sei denn, sie verwendet werden OMA DM berücksichtigt Management Mobilfunkbetreiber datenverbindungseinstellungen oder manufacturing Tests.

-   E-Mail-Einstellungen.

> **Hinweis**  Die **DMProcessConfigXMLFiltered** -Funktion verfügt über vollständigen Funktionalität in Windows 10 Mobile und Windows Phone 8.1 besitzt eine nur-Lese-Funktionalität in Windows 10 Desktop

 

<a name="syntax"></a>Syntax
------

```C++
HRESULT STDAPICALLTYPE DMProcessConfigXMLFiltered(
         LPCWSTR pszXmlIn,
   const WCHAR   **rgszAllowedCspNode,
   const DWORD   dwNumAllowedCspNodes,
         BSTR    *pbstrXmlOut
);
```

<a name="parameters"></a>Parameter
----------

*pszXmlIn*
<ul style="list-style-type:none">
<li>\[in\] die Null terminierte – XML-Eingabe Puffer mit den Konfigurationsdaten. Der Parameter enthält den XML-CODE, die so konfigurieren Sie das Telefon verwendet werden. **DMProcessConfigXMLFiltered** akzeptiert nur OMA Client Provisioning XML (auch als WAP provisioning bezeichnet). Es akzeptiert keine OMA DM SyncML XML (auch bekannt als SyncML).</li>
</ul>
<br>

*rgszAllowedCspNode*
<ul style="list-style-type:none">
<li>\[in\] Array von **WCHAR\* ** anzugeben, dass die Konfiguration Service Provider Knoten aufgerufen werden dürfen.</li>
</ul>
<br>

*dwNumAllowedCspNodes*
<ul style="list-style-type:none">
<li>\[in\] Anzahl der Elemente in *RgszAllowedCspNode*übergeben.</li>
</ul>
<br> 

*pbstrXmlOut*
<ul style="list-style-type:none">
<li>\[Skalieren\] resultierenden Null – terminierte XML von Konfiguration. Der Aufrufer **DMProcessConfigXMLFiltered** ist für die Bereinigung des Ausgabepuffers, die der Parameter *PbstrXmlOut* verweist verantwortlich. Verwenden Sie [**SysFreeString**](https://msdn.microsoft.com/library/windows/hardware/ms221481) , um den Arbeitsspeicher freizugeben.</li>
</ul>
<br>

Wenn **DMProcessConfigXMLFiltered** ein Dokuments abruft, enthält der *PbstrXmlOut* die XML-Ausgabe der Bereitstellung Vorgänge (in Form einer Zeichenfolge). Wenn **DMProcessConfigXMLFiltered** einen Fehler zurückgibt, enthält XML-Ausgabe häufig "Fehlerknoten", um anzugeben, welche Elemente des Originals XML ist fehlgeschlagen. Wenn Eingabedokuments enthält keine Abfragen und erfolgreich verarbeitet wird, sollte das Ausgabedokument des Eingabedokuments ähneln. In einigen Fällen Fehler wird keine Ausgabe zurückgegeben.

<a name="return-value"></a>Rückgabewert
------------

Gibt den standard **HRESULT** -Wert **S\_OK** um Erfolg anzuzeigen. Die folgende Tabelle zeigt die zusätzlichen Fehlercodes, die möglicherweise zurückgegeben werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rückgabecode</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_OBJECTBUSY</strong></p></td>
<td style="vertical-align:top"><p>Der Konfigurations-Verwaltungsdienst wird derzeit ausgeführt.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>CONFIG_E_ENTRYNOTFOUND</strong></p></td>
<td style="vertical-align:top"><p>Es wurde kein Metabase-Eintrag gefunden.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_CSPEXCEPTION</strong></p></td>
<td style="vertical-align:top"><p>In einer Konfiguration-Dienstanbieter ist eine Ausnahme aufgetreten.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>CONFIG_E_TRANSACTIONINGFAILURE</strong></p></td>
<td style="vertical-align:top"><p>Ein Konfigurationsdienstanbieter konnte nicht ordnungsgemäß Rollback. Die betroffenen Einstellungen möglicherweise in einem unbekannten Zustand.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_BAD_XML</strong></p></td>
<td style="vertical-align:top"><p>Die XML-Eingabe ist ungültig oder falsch formatiert.</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Hinweise
-------

Die Verarbeitung des XML-ist transaktional; Dient zum Abrufen des gesamten Dokuments erfolgreich verarbeitet oder keine Einstellungen verarbeitet werden. Die Funktion **DMProcessConfigXMLFiltered** verarbeitet daher nur eine XML-Konfiguration Anforderung zu einem Zeitpunkt.

Die Verwendung der **DMProcessConfigXMLFiltered** hängt von der Konfiguration-Dienstanbieter, die verwendet werden. Wenn beispielsweise die Eingabe .provxml die folgenden zwei Einstellungen enthält:

``` XML
<wap-provisioningdoc>
    <characteristic type="NAPDEF">
        <characteristic type="Internet" mwid="1">
            <parm name="NAME" value="Contoso Internet APN"/>
            <parm name="BEARER" value="GSM-GPRS"/>
            <parm name="NAP-ADDRESS" value="wap.contoso"/>
            <parm name="NAP-ADDRTYPE" value="APN"/>
            <parm name="INTERNET" value="1"/>
        </characteristic>
    </characteristic>
    <characteristic type="BrowserFavorite">
        <characteristic type="Contoso">
            <parm name="URL" value="http://www.contoso.com"/>
        </characteristic>
    </characteristic>
</wap-provisioningdoc>
```

Klicken Sie dann müssten der zweite Parameter im Aufruf **DMProcessConfigXMLFiltered** die folgende Definition haben.

``` C++
LPCWSTR rgszAllowedCspNodes[] =
{
    L"NAPDEF",
    L"BrowserFavorite"
};
```

Dieses Array von Konfiguration Dienstnamen Anbieter gibt an, welche Inhalte .provxml vorhanden sein sollten. Wenn die Provxml enthält "EMAIL2" Bereitstellung jedoch *RgszAllowedCspNodes* enthält keine EMAIL2, Fehler bei der **DMProcessConfigXMLFiltered** ein **E\_ACCESSDENIED** Fehlercode.

Im folgenden Codebeispiel wird veranschaulicht, wie dieses Array in übergeben wird. Hinweis: Diese *SzProvxmlContent* nicht den vollständigen XML-Inhalt der Kürze halber angezeigt wird. Bei der tatsächlichen Verwendung der "..." würde die vollständige oben gezeigten XML-Zeichenfolge enthalten.

``` C++
WCHAR szProvxmlContent[] = L"<wap-provisioningdoc>...</wap-provisioningdoc>"; 
BSTR bstr = NULL;

HRESULT hr = DMProcessConfigXMLFiltered(
                szProvxmlContent,
                rgszAllowedCspNodes,
                _countof(rgszAllowedCspNodes),
                &bstr
                );

/* check error */

if ( bstr != NULL )
{
    SysFreeString( bstr );
    bstr = NULL;
}
```

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Minimale unterstützte Clients</p></td>
<td style="vertical-align:top"><p>Keine unterstützt</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Minimal unterstützte server</p></td>
<td style="vertical-align:top"><p>Keine unterstützt</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Minimale unterstützte Telefon</p></td>
<td style="vertical-align:top"><p>Windows Phone 8.1</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Kopfzeile</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.h</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Bibliothek</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.lib</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DLL-DATEI</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.dll</p></td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>Siehe auch

[**SysFreeString**](https://msdn.microsoft.com/library/windows/hardware/ms221481)

 






