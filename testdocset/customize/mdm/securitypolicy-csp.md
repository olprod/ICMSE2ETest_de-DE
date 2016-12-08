---
title: SecurityPolicy CSP
description: SecurityPolicy CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6014f8fe-f91b-49f3-a357-bdf625545bc9
ms.openlocfilehash: 0c833a80761ed4f7fc645848e599d64b8cf5c54d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="securitypolicy-csp"></a>SecurityPolicy CSP


Der Dienstanbieter für SecurityPolicy Konfiguration wird so konfigurieren Sie Einstellungen für Sicherheitsrichtlinien für WAP Push OMA-Clientbereitstellung, OMA DM, Dienst Angabe (SI), Dienst laden (SL) und MMS verwendet.

>  **Hinweis**   Dieses Dienstanbieters Konfiguration erfordert die ID\_CAP\_CSP\_FOUNDATION und ID\_CAP\_GERÄT\_MANAGEMENT\_SICHERHEIT\_RICHTLINIEN Funktionen, die über ein Netzwerk Konfiguration Anwendung zugegriffen werden.

 

Für den CSP SecurityPolicy nicht den Replace-Befehl verwendet werden, wenn der Knoten bereits vorhanden ist.

Das folgende Diagramm veranschaulicht das SecurityPolicy Configuration Service Provider Management-Objekts im Strukturformat von OMA DM sowohl OMA-Clientbereitstellung verwendet.

![SecurityPolicy Csp (dm, cp)](images/provisioning-csp-securitypolicy-dmandcp.png)

<a href="" id="policyid"></a>***PolicyID***  
Definiert die Sicherheits-ID Richtlinie als Dezimalwert.

Die folgenden Sicherheitsrichtlinien werden unterstützt.

<table>
<colgroup>
<col width="15%" />
<col width="25%" />
<col width="55%" />
</colgroup>
<thead>
<tr class="header">
<th>PolicyID</th>
<th>Richtlinienname</th>
<th>Beschreibung der Richtlinie</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>4104</p>
<p>Hex: 1008</p></td>
<td><p>TPS-Richtlinie</p></td>
<td><p>Diese Einstellung gibt an, ob Mobilfunkbetreibern die Bereitstellung Server vertrauenswürdige (TPS) SECROLE_OPERATOR_TPS Rolle zugewiesen werden können.</p>
<p>Standardwert: 1</p>
<p>Unterstützte Werte:</p>
<p>0: der TPS rollenzuweisung ist deaktiviert.</p>
<p>1: die rollenzuweisung TPS ist aktiviert und kann Mobilfunkbetreibern zugewiesen werden.</p></td>
</tr>
<tr class="even">
<td><p>4105</p>
<p>Hex: 1009</p></td>
<td><p>Nachricht Authentifizierungsrichtlinie "Wiederholen"</p></td>
<td><p>Diese Einstellung gibt die maximale Anzahl der Häufigkeit, mit die der Benutzer versucht, eine Wireless Application Protocol (WAP) PIN signierten Nachricht authentifizieren berechtigt ist.</p>
<p>Standardwert: 3</p>
<p>Mögliche Werte: 0 bis 256.</p></td>
</tr>
<tr class="odd">
<td><p>4108</p>
<p>Hex: 100 c</p></td>
<td><p>Dienst beim Laden der Richtlinie</p></td>
<td><p>Diese Einstellung gibt an, ob SL Nachrichten akzeptiert werden, durch die Sicherheitsrollen, die SL Nachrichten akzeptieren können angeben. Eine Nachricht SL downloads neue Dienste oder XML-Bereitstellungsdatei an das Gerät.</p>
<p>Standardwert: 256 (SECROLE_KNOWN_PPG)</p>
<p>Unterstützte Werte: SECROLE_ANY_PUSH_SOURCE, SECROLE_KNOWN_PPG</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>4109</p>
<p>Hex: 100 d</p></td>
<td><p>-Angabe Richtlinie</p></td>
<td><p>Diese Einstellung gibt an, ob SI Nachrichten akzeptiert werden, durch die Sicherheitsrollen, die SI Nachrichten akzeptieren können angeben. Eine SI-Nachricht wird an das Gerät gesendet, um Benutzer von neuen Dienste, dienstaktualisierungen und provisioning Services zu informieren.</p>
<p>Standardwert: 256 (SECROLE_KNOWN_PPG)</p>
<p>Unterstützte Werte: SECROLE_ANY_PUSH_SOURCE, SECROLE_KNOWN_PPG</p></td>
</tr>
<tr class="odd">
<td><p>4111</p>
<p>Hex: 100f</p></td>
<td><p>OTA Provisioning Policy</p></td>
<td><p>Diese Einstellung bestimmt, ob die PIN OMA-Clientbereitstellung signierte Nachrichten verarbeitet werden. Diese Richtlinie Wert gibt eine Rollenmaske an. Wenn eine Nachricht mindestens eines der folgenden Rollen in der Rollenmaske enthält, wird die Nachricht verarbeitet. Um ordnungsgemäß signierte OMA-Clientbereitstellung sicherzustellen werden Nachrichten akzeptiert, vom Client Konfiguration, alle Rollen, die in 4141, festgelegt werden Richtlinien 4142 und 4143 auch in dieser Richtlinie festgelegt werden müssen. Beispielsweise muss Richtlinie 4111 damit sichergestellt ist ordnungsgemäß signierte USERNETWPIN signiert OMA-Clientbereitstellung Nachrichten vom Gerät, akzeptiert werden Wenn Richtlinie 4143 auf 4096 (SECROLE_ANY_PUSH_SOURCE) für ein Gerät Netzbetreiber nicht gesperrte festgelegt ist, auch die Rolle SECROLE_ANY_PUSH_SOURCE festgelegt haben.</p>
<p>Standardwert: 384 (SECROLE_OPERATOR_TPS | SECROLE_KNOWN_PPG)</p>
<p>Unterstützte Werte: SECROLE_KNOWN_PPG, SECROLE_ANY_PUSH_SOURCE, SECROLE_OPERATOR_TPS</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>4113</p>
<p>Hex: 1011</p></td>
<td><p>WSP-Push-Richtlinie</p></td>
<td><p>Diese Einstellung gibt an, ob Benachrichtigungen aus dem WAP-Stapel Wireless Sitzung Protocol (WSP) weitergeleitet werden.</p>
<p>Standardwert: 1</p>
<p>Unterstützte Werte:</p>
<p>0: der WSP-Benachrichtigungen routing ist nicht zulässig.</p>
<p>1: routing von WSP Benachrichtigungen zulässig ist.</p></td>
</tr>
<tr class="odd">
<td><p>4132</p>
<p>Hex: 1024</p></td>
<td><p>PIN Netzwerk angemeldet OTA Provision Nachricht Prompt Benutzerrichtlinie</p></td>
<td><p>Diese Richtlinie gibt an, ob das Gerät eine Benutzeroberfläche, um die Bestätigung des Benutzers abzurufen, bevor eine reine Netzwerk Pin Verarbeitung OTA Provisioning Nachricht signiert auffordern. Wenn auffordern, hat der Benutzer die Möglichkeit, die Bereitstellung OTA-Nachricht verwerfen.</p>
<p>Standardwert: 0</p>
<p>Unterstützte Werte:</p>
<p>0: das Gerät fordert eine Benutzeroberfläche Bestätigung des Benutzers abrufen, wenn es sich bei die Bereitstellung OTA WAP-Nachricht ausschließlich mit Pin Netzwerk angemeldet ist.</p>
<p>1: keine Aufforderung des Benutzers vorhanden ist.</p></td>
</tr>
<tr class="even">
<td><p>4141</p>
<p>Hex: 102d</p></td>
<td><p>OMA CP NETWPIN Richtlinie</p></td>
<td><p>Diese Einstellung bestimmt, ob die OMA Netzwerk angemeldet PIN Meldung akzeptiert werden. Maske-Rolle die Nachricht und die Richtlinie Rollenmaske werden mithilfe des AND-Operators kombiniert. Wenn das Ergebnis ungleich NULL ist, wird die Nachricht akzeptiert.</p>
<p>Standardwert: 0</p>
<p>Unterstützte Werte: SECROLE_KNOWN_PPG, SECROLE_ANY_PUSH_SOURCE, SECROLE_OPERATOR_TPS</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>4142</p>
<p>Hex: 102e</p></td>
<td><p>OMA CP USERPIN Richtlinie</p></td>
<td><p>Diese Einstellung bestimmt, ob die OMA Benutzer PIN oder Benutzer MAC signierte Nachricht akzeptiert werden. Maske-Rolle die Nachricht und die Richtlinie Rollenmaske werden mithilfe des AND-Operators kombiniert. Wenn das Ergebnis ungleich NULL ist, wird die Nachricht akzeptiert.</p>
<p>Standardwert: 256</p>
<p>Unterstützte Werte: SECROLE_OPERATOR_TPS, SECROLE_ANY_PUSH_SOURCE, SECROLE_KNOWN_PPG</p></td>
</tr>
<tr class="even">
<td><p>4143</p>
<p>Hex: 102f</p></td>
<td><p>OMA CP USERNETWPIN Richtlinie</p></td>
<td><p>Diese Einstellung bestimmt, ob die OMA Benutzer Netzwerk PIN signierte Nachricht akzeptiert werden. Maske-Rolle die Nachricht und die Richtlinie Rollenmaske werden mithilfe des AND-Operators kombiniert. Wenn das Ergebnis ungleich NULL ist, wird die Nachricht akzeptiert.</p>
<p>Standardwert: 256</p>
<p>Unterstützte Werte: SECROLE_KNOWN_PPG, SECROLE_ANY_PUSH_SOURCE, SECROLE_OPERATOR_TPS</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>4144</p>
<p>Hex: 1030</p></td>
<td><p>Richtlinie für MMS-Nachrichten</p></td>
<td><p>Diese Einstellung bestimmt, ob MMS-Nachrichten verarbeitet werden. Diese Richtlinie Wert gibt eine Rollenmaske an. Wenn eine Nachricht mindestens eine der Rollen in der Rollenmaske enthält, wird die Nachricht verarbeitet.</p>
<p>Standardwert: 256 (SECROLE_KNOWN_PPG)</p>
<p>Unterstützte Werte: SECROLE_KNOWN_PPG, SECROLE_ANY_PUSH_SOURCE</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Sicherheitsrollen zulassen oder Einschränken des Zugriffs auf Ressourcen-Geräte. Die Sicherheitsrolle basiert auf der Nachricht Ursprung und wie die Nachricht signiert ist. Sie können mehrere Rollen zu einer Nachricht im XML-Dokument in Sicherheit Richtlinie zuweisen, durch die Kombination der decimal Werte der Rollen, die Sie zuweisen möchten. Beispielsweise, um sowohl die SECROLE zuweisen\_BEKANNTE\_PPG und SECROLE\_OPERATOR\_TPS Rollen, verwenden Sie den Dezimalwert 384 (256 + 128).

Die folgenden Sicherheitsrollen werden unterstützt.

<table>
<colgroup>
<col width="15%" />
<col width="25%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Sicherheitsrolle</th>
<th>Dezimalwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SECROLE_OPERATOR_TPS</p></td>
<td><p>128</p></td>
<td><p>Vertrauenswürdige Server Bereitstellung.</p>
<p>Zugewiesene WAP-Nachrichten, die einen Push-Initiator stammen, die authentifiziert (SECROLE_PPG_AUTH) von einem vertrauenswürdigen Push Proxy Gateway (SECROLE_TRUSTED_PPG), und, in dem der URI des vertrauenswürdigen Provisioning Server (TPS) auf dem Gerät die URI Uniform Resource Identifier () von der Initiator Push entspricht.</p>
<p>Mobilfunkbetreiber kann bestimmen, ob diese Rolle und der Rolle SECROLE_OPERATOR die gleichen Berechtigungen erforderlich sind.</p></td>
</tr>
<tr class="even">
<td><p>SECROLE_KNOWN_PPG</p></td>
<td><p>256</p></td>
<td><p>Bekannte Pushbenachrichtigungs-Proxy-Gateway.</p>
<p>Nachrichten, die dieser Rolle darauf hinzuweisen, dass das Gerät die Adresse der Push-Proxy-Gateway bekannt ist.</p></td>
</tr>
<tr class="odd">
<td><p>SECROLE_ANY_PUSH_SOURCE</p></td>
<td><p>4096</p></td>
<td><p>Verschieben Sie Router.</p>
<p>Nachrichten vom Router Push werden diese Rolle zugewiesen werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="oma-client-provisioning-examples"></a>Beispiele für OMA-Clientbereitstellung


Festlegen der Codezugriffssicherheits-Richtlinie:

``` syntax
<wap-provisioningdoc>
    <characteristic type="SecurityPolicy">
        <parm name="4141" value="0"/>
    </characteristic>
<wap-provisioningdoc>
```

Abfragen von Codezugriffssicherheits-Richtlinie:

``` syntax
<wap-provisioningdoc>
    <characteristic type="SecurityPolicy">
        <parm-query name="4141"/>
    </characteristic>
<wap-provisioningdoc>
```

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Festlegen der Codezugriffssicherheits-Richtlinie:

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
    <SyncHdr>
    …
    </SyncHdr>
    <SyncBody>
        <Replace>
            <CmdID>1</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/SecurityPolicy/4141</LocURI></Target>
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

Abfragen von Codezugriffssicherheits-Richtlinie:

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
    <SyncHdr>
    …
    </SyncHdr>
    <SyncBody>
        <Get>
            <CmdID>1</CmdID>
            <Item>
            <Target><LocURI>./Vendor/MSFT/SecurityPolicy/4141</LocURI></Target> 
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

## <a name="microsoft-custom-elements"></a>Microsoft benutzerdefinierter Elemente


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
<td><p>Parameter-Abfragen</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>noparm</p></td>
<td><p>Ja. Wenn dies wird verwendet, und klicken Sie dann die Richtlinie wird standardmäßig auf 0 festgelegt (die restriktivsten entspricht der Richtlinienwerte).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






